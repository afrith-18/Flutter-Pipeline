# Flutter-Pipeline
🔥 Flutter CI template with GitHub Actions — clean code, fast builds, reliable delivery.
A minimal, production-ready GitHub → Flutter pipeline template.

Use this repository as a starter for Flutter apps to get:
- deterministic CI checks (format, analyze, tests)
- build artifact generation (APK / AAB)
- artifact upload for QA distribution
- Dependabot + secrets-friendly deployment hooks

## What's included
- `.github/workflows/flutter-ci.yml` — CI pipeline (analyze, tests, build, upload)
- `dev-setup.sh` — local bootstrap script
- `CONTRIBUTING.md` — PR & review guidance
- `fastlane/Fastfile` — example Android deploy (optional)

## Prerequisites
- Flutter app (this repo assumes standard structure with `pubspec.yaml` & `lib/`)
- GitHub repo with **Actions** enabled
- GitHub Secrets configured (see "Secrets" below)

## Recommended GitHub Secrets
- `FLUTTER_VERSION` (optional: e.g. `3.10.5`)
- `ANDROID_KEYSTORE_BASE64` (base64 of your keystore file) — optional for release signing in CI
- `KEYSTORE_PASSWORD`, `KEY_ALIAS`, `KEY_PASSWORD` — optional
- `FIREBASE_TOKEN` — optional (upload to Firebase App Distribution)
- `FASTLANE_USER`, `FASTLANE_PASSWORD` — optional for Play deploy

> Note: For iOS builds you need macOS runners (self-hosted or GitHub-hosted macos-latest) and Apple signing secrets. This starter focuses on Android / CI basics.

---

## Quick start

1. Create a GitHub repo and push your Flutter project (or fork this starter).
2. Add recommended secrets (Settings → Secrets → Actions).
3. Copy `.github/workflows/flutter-ci.yml` into your repo.
4. Open a PR — CI will run static checks and tests automatically.

---

## How the CI works (high-level)
On PR:
- Checkout, set up Flutter
- Cache pub packages
- Run `flutter format` check
- Run `flutter analyze`
- Run `flutter test` (unit + widget tests)
- Build debug APK and upload as artifact for QA

On push to `main`:
- Run the above checks
- Build Release AAB (if signing secrets are present)
- Optionally upload to Firebase App Distribution or drive deployment via Fastlane

---

## Contributing
See [CONTRIBUTING.md](./CONTRIBUTING.md) for PR templates and guidelines.

---

## License
MIT
