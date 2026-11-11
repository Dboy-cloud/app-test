# Base App (Flutter: Android + iOS + Windows)

A simple notes app: add and delete notes, saved on the device.
One codebase in `lib/main.dart` builds for all three platforms.

## Option A: no installs (GitHub builds it for you)
1. Create a free GitHub account and a new repository.
2. Upload everything in this folder (keep the `.github` folder).
3. Open the repo's **Actions** tab. The "Build all platforms" workflow runs
   automatically. When it finishes, download the results under "Artifacts":
   - `android-apk` -> installable .apk
   - `windows-app` -> Windows app folder (run base_app.exe)
   - `ios-unsigned` -> iOS build (unsigned, see below)

## Option B: build on your own computer
1. Install Flutter: https://docs.flutter.dev/get-started/install
2. In an empty location run:
      flutter create --platforms=android,ios,windows --project-name base_app base_app
3. Copy this folder's `lib/`, `test/`, `pubspec.yaml`, `analysis_options.yaml`
   over the new `base_app` folder.
4. Run:
      cd base_app
      flutter pub get
      flutter run                 # runs on a connected device/emulator
      flutter build apk --release # Android .apk
      flutter build windows       # Windows (on a Windows PC)
      flutter build ios           # iOS (needs a Mac + Xcode)

## Before publishing
- Android (Play Store): create a signing keystore and build an app bundle:
  `flutter build appbundle`.
- iOS (App Store): needs an Apple Developer account and code signing. Use a Mac,
  or a cloud service such as Codemagic.
- Windows (Microsoft Store): package as MSIX (`dart run msix:create` with the
  `msix` package) or distribute the folder directly.
- Change the app name and ID (e.g. `com.yourname.yourapp`) before publishing.
