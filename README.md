# Gym Library – Android app

This folder is a complete Android Studio project. It wraps the Gym Library web app
(`app/src/main/assets/index.html`) in a full-screen app with its own icon.
Everything runs offline except the Google Fonts (it falls back to system fonts) and
the "Ask Claude" box, which is hidden in the app.

## Option A – Build it on GitHub (nothing to install)

1. Go to https://github.com/new
2. **Repository name:** `gym-library-android` → choose **Private** → click **Create repository**.
3. On the new repo page, click **uploading an existing file**.
4. Unzip `GymLibrary-Android.zip` on your PC, open the `GymLibrary-Android` folder,
   select **everything inside it** (including the `.github` and `gradle` folders) and drag it onto the page.
   - Windows hides nothing here, but if `.github` is missing, turn on **View → Show → Hidden items** in File Explorer.
5. Click **Commit changes**.
6. Click the **Actions** tab. The **Build APK** run starts automatically (about 3–5 minutes).
   If it doesn’t, click **Build APK** → **Run workflow** → **Run workflow**.
7. When it shows a green tick, click the run → scroll to **Artifacts** → click **GymLibrary-apk** to download a zip.
8. Unzip it to get **app-debug.apk**.

## Option B – Build it in Android Studio

1. Install Android Studio from https://developer.android.com/studio (accept the default SDK setup).
2. **File → Open…** → select the `GymLibrary-Android` folder → **OK** → **Trust Project**.
3. Wait for the Gradle sync to finish (bottom status bar; the first time downloads ~1 GB).
4. **Build → Build App Bundle(s) / APK(s) → Build APK(s)**.
5. When the popup says *APK(s) generated successfully*, click **locate**.
   The file is `app/build/outputs/apk/debug/app-debug.apk`.

## Install on your phone

1. Copy `app-debug.apk` to the phone (USB, Google Drive, or email it to yourself).
2. Tap the file in **Files** / **Downloads**.
3. If prompted, tap **Settings** → turn on **Allow from this source** → go back → **Install**.
4. If Play Protect warns about an unknown developer, tap **More details → Install anyway**
   (expected for a personally built app).

## Updating the app later

- Replace `app/src/main/assets/index.html` with a newer copy of the web app.
- Increase `versionCode` (e.g. 1 → 2) and `versionName` in `app/build.gradle.kts`.
- Rebuild. Installing the new APK over the old one keeps your training log,
  **as long as it is built with the same signing key** (the same GitHub repo / same PC).
  Use **Log → Copy backup** before updating, just in case.

## Notes

- This builds a **debug** APK, signed with a debug key. That’s fine for your own phone.
  To publish on Google Play you’d need a release build signed with your own upload key
  (**Build → Generate Signed App Bundle / APK** in Android Studio).
- Package name: `com.gymlibrary.app` (change `applicationId` in `app/build.gradle.kts` if you want your own).
- Minimum Android version: 8.0 (API 26). Target: Android 15 (API 35).
