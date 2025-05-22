# 📱 flutter_app CI/CD Boilerplate

This project is a simple, ready-to-use boilerplate for setting up **CI/CD** with Flutter.  
The main purpose of this repo is to demonstrate how to automate building and releasing **APK**, **AAB**, and **iOS** apps using **GitHub Actions**.

---

## 🚀 Features

- Quick CI/CD setup for Flutter
- Automatic APK and AAB builds for Android
- Automatic iOS builds (requires macOS and Xcode)
- Supports obfuscation and debug symbols for better security and debugging
- Ready to use with GitHub Actions

---

---

## 📦 Output Formats

| Format | Path |
|--------|------|
| APK | `build/app/outputs/flutter-apk/flutter_app-*.apk` |
| AAB | `build/app/outputs/bundle/release/app-release.aab` |
| iOS | `build/ios/iphoneos/Runner.app` or exported IPA |
| Debug Symbols | `build/app/outputs/symbols/` |




---

## 📌 Usage Note

To use this CI/CD setup, simply add the workflow files from the `.github/workflows/` folder to your own repository,  
then trigger or monitor the workflows from the **Actions** tab in GitHub.  
The build outputs (APKs, AABs, debug symbol files, etc.) will be automatically uploaded to the **Releases** section on GitHub.

---

---

## 🛠 Build Instructions (Manual)

Make sure you have Flutter installed. Then run:

### 🔹 Get dependencies:
```bash
flutter pub get
```

### 🔹 Build APK:
```bash
flutter build apk --release --obfuscate --split-debug-info=build/symbols --split-per-abi
```

### 🔹 Build AAB:
```bash
flutter build appbundle --release --obfuscate --split-debug-info=build/symbols
```

### 🔹 Build iOS:
```bash
flutter build ios --release --obfuscate --split-debug-info=build/symbols
```

> Note: For iOS builds, macOS and Xcode are required.

---

## ⚙️ CI/CD Setup (GitHub Actions)

This repo contains ready-to-use GitHub Actions workflows for:

- `android-apk.yml`: Builds & uploads per-ABI APKs to release
- `android-aab.yml`: Builds & uploads AAB to release
- `ios-build.yml`: Builds iOS release (manual export)

Each workflow uses:
- `--obfuscate` for Dart code protection
- `--split-debug-info` for crash diagnostics

See `.github/workflows/` directory.

---


## ⚠️ Important

To enable GitHub Actions to upload your build artifacts (APKs, AABs, etc.) to releases,  
you **must** enable **Write** permission for GitHub Actions in your repository settings.  
Otherwise, the upload step will fail due to insufficient permissions.

---

## 📦 Release Example

Each GitHub Release includes:

- ✅ Signed APKs (per ABI)
- ✅ AAB bundle
- ✅ Debug symbols (uploaded as artifacts)

---

## 🧑‍💻 Developer Notes

- Requires Java 17 (configured via `actions/setup-java`)
- Uses Kotlin 1.9+
- Gradle 8.4+ and desugar_jdk_libs 2.1.4 are used for full Java 8+ compatibility

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---



> Maintained with ❤️ by [YourName or Organization]
