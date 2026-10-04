# Lifelines: Android build

This folder is everything GitHub needs to build the Android app file (.aab) that Google Play takes.
Nothing here needs Android Studio.

## One-time setup
1. Create a **private** GitHub repository and upload everything in this folder (including the hidden `.github` folder).
2. In the repo go to **Actions → Make upload key (run once) → Run workflow**.
   When it finishes, download the artifact `KEEP-PRIVATE-upload-key`. Keep it safe: it is your signing key.
3. In the repo go to **Settings → Secrets and variables → Actions → New repository secret** and add:
   - `KEYSTORE_B64`: the text inside `keystore_b64.txt`
   - `KEYSTORE_PASSWORD`, `KEY_PASSWORD`, `KEY_ALIAS`: the three values inside `secrets.txt`

## Every release
1. Replace `www/index.html` with the newest `lifelines.html` from the game build.
2. **Actions → Build Android app → Run workflow**. When it finishes, download `lifelines-release-aab`.
3. Upload that `.aab` in Google Play Console.

## Google Play Console products (must match exactly)
One-time products ("Managed products"), all type **non-consumable / one-time**:
- `lifelines_energy`: Max energy 1,000
- `lifelines_cash`: Start with $10 million
- `lifelines_god`: God mode
