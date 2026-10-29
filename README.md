# 罗大仙大战开屏广告 — Android prototype

A conservative Android AccessibilityService prototype that attempts to click visible, actionable nodes whose labels clearly indicate an ad skip action.

## Build APK without installing Android Studio
This repository includes a GitHub Actions workflow that builds a debug APK in the cloud.

1. Create a GitHub repository and upload the contents of this project (the `cleanstart` folder contents, not the ZIP itself).
2. Open the repository's **Actions** tab.
3. Select **Build Android APK** / **Build Android APK** workflow.
4. Click **Run workflow** and wait for it to finish.
5. Open the completed run and download the artifact named `luodaxian-battle-opening-ads-apk`.
6. Extract the downloaded artifact ZIP to get `app-debug.apk`.

The workflow uses Java 17, Gradle 8.9, Android SDK Platform 35, and Android Build Tools 35.0.0.

## Requirements for local build
- JDK 17
- Android SDK Platform 35
- Android Gradle Plugin 8.7.3 / Kotlin 2.0.21

## Local build
Run `gradle assembleDebug` from the project root after installing the requirements above.

## Current prototype limitations
- It only clicks clear text labels such as “跳过广告”, “跳过”, “skip ad”, “skip”, and “关闭广告”.
- It does not perform coordinate taps, dismiss generic “X” buttons, or handle image-only controls.
- It cannot guarantee that all ads are skipped. Some apps use inaccessible/custom-rendered ad UI.
- Shake-to-open ads are not fully blocked in this version. Preventing those requires app-specific behavior and may not be possible through Accessibility alone.
- The service runs only after the user explicitly enables it in Android Settings.

## Privacy
This prototype has no INTERNET permission and does not upload screen contents. Accessibility access is powerful; enable it only if you understand and trust the app.
