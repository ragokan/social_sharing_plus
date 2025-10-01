# Repository Guidelines

## Project Structure & Module Organization
Core Flutter plugin code lives in `lib/`, with platform channels under `lib/src/`. Native iOS and Android implementations sit in `ios/` and `android/` respectively. The `example/` app demonstrates integration and is the fastest way to validate changes end-to-end. Tests for the Dart layer live in `test/`, and documentation assets reside at the repository root.

## Build, Test, and Development Commands
Run `flutter pub get` in the repo root (and inside `example/`) to fetch dependencies. Use `flutter test` to execute the Dart test suite, and `flutter analyze` to surface lint violations. To validate on-device behavior, `cd example && flutter run` launches the sample app with your local plugin changes.

## Coding Style & Naming Conventions
Follow Flutter's default two-space indentation and prefer descriptive camelCase for identifiers. Public APIs should use clear, action-oriented names that mirror platform intent (e.g., `shareToLinkedIn`). Before committing, format Dart code with `dart format .` and resolve lint feedback reported through `flutter analyze`, which reads rules from `analysis_options.yaml` (extends `flutter_lints`).

## Testing Guidelines
Add or update unit tests in `test/` to cover new behaviors, mocking platform interfaces where needed. Name test files after the Dart unit under test (e.g., `social_sharing_plus_test.dart`) and keep test descriptions behavior-focused. For feature work, run `flutter test --coverage` to verify meaningful coverage and inspect `coverage/lcov.info` when adjusting thresholds or integrating with CI.

## Commit & Pull Request Guidelines
Commit messages should be concise and imperative (e.g., `fix: handle missing LinkedIn app`), matching the existing history's mix of conventional and descriptive prefixes. Every pull request needs a focused summary, bulletproof reproduction steps or example usage, linked issues when applicable, and screenshots or screen recordings for UI-facing updates. Confirm that tests and `flutter analyze` pass locally before requesting review.

## Security & Configuration Tips
Avoid checking secrets or API tokens into the repository; prefer environment variables within the `example/` app. When debugging platform code, keep platform-specific configuration files (`Info.plist`, `AndroidManifest.xml`) scoped to the example app to prevent leaking production keys.
