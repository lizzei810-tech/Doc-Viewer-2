# Doc Viewer - Android project

A WebView app that opens `app/src/main/assets/doc-viewer.html`, the PDF / PowerPoint / Word viewer.

## Build the APK without installing anything (GitHub)

GitHub builds the APK for you on its own computers.

1. Create a free account at github.com and create a new **empty** repository (name it `DocViewer`).
2. Unzip `DocViewer.zip`, open the `DocViewer` folder, and upload its **contents** (not the folder itself) to the repository. Drag the files into the GitHub upload page, or use "Add file → Upload files".
3. Open the **Actions** tab. The "Build APK" workflow starts automatically. Wait for the green tick (a few minutes).
4. Open the finished run and download **DocViewer-debug** from the "Artifacts" section. It is a zip that contains `app-debug.apk`.
5. Copy the APK to your phone and install it, allowing installs from this source when Android asks.

If the workflow fails, open the red run, copy the error text, and send it to the assistant.

## Build the APK on your computer (Android Studio)

1. Install **Android Studio** (it includes the Android SDK and Java).
2. In Android Studio choose **Open** and select this `DocViewer` folder.
3. Wait for **Gradle sync** to finish. The first sync downloads several hundred MB, so it can take a while.
4. Go to **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
5. When the message appears, click **locate**. The file is `app/build/outputs/apk/debug/app-debug.apk`.
6. Copy the APK to your phone, open it, and allow installs from this source when Android asks.

Or from a terminal inside this folder:

- macOS / Linux: `./gradlew assembleDebug`
- Windows: `gradlew.bat assembleDebug`

The APK is written to the same `app/build/outputs/apk/debug/` folder.

## Notes

- **Internet on the phone:** pdf.js, JSZip and Google Fonts load from the internet. To work fully offline, download `pdf.min.js`, `pdf.worker.min.js` and `jszip.min.js`, put them in `app/src/main/assets/`, and change the three script/worker URLs in `doc-viewer.html` to those file names.
- **Package name:** `com.hardwarefixer.docviewer`. Change `namespace` and `applicationId` in `app/build.gradle` to use a different one.
- **Sharing with others:** build a signed release APK with **Build → Generate Signed App Bundle / APK**, using your own keystore.
- **Not built yet:** this project was prepared without the Android SDK, so the first build on your computer is the real test. If it reports errors, send them to me and I'll fix them.
