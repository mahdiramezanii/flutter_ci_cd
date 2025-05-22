# 📱 flutter_app

A modern, cross-platform Flutter application built with Firebase, notifications, and clean architecture.  
This app is ready for production with CI/CD support for APK, AAB, and iOS builds.

---

## 🚀 Features

- 🔥 Firebase integration (auth, messaging, etc.)
- 🛎 Local notifications via `flutter_local_notifications`
- 🔐 Obfuscation for secure builds
- 📦 CI/CD GitHub Actions for APK, AAB, and iOS
- 📁 Debug symbols for crash reporting
- 🧱 Split-per-ABI builds to reduce APK size

---

## 📦 Output Formats

| Format | Path |
|--------|------|
| APK | `build/app/outputs/flutter-apk/flutter_app-*.apk` |
| AAB | `build/app/outputs/bundle/release/app-release.aab` |
| iOS Archive | `build/ios/iphoneos/Runner.app` (or exported IPA) |
| Debug Symbols | `build/app/outputs/symbols/` |

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

> Maintained with ❤️ by [Mahdi Ramezani]
