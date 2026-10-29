# JoshTapApp

Android NFC-driven audio player project, with Play, Library and Cards tabs.

## Build

Requires JDK 17, Android SDK 35 and a configured Android SDK location.

```bash
./gradlew :app:assembleDebug
adb install -r app/build/outputs/apk/debug/app-debug.apk
```

## Current source inventory (reviewed 29 October 2026)

The repository contains Kotlin implementations for Room entities/DAO, audio playback through Media3, NFC reading/writing, backup, onboarding and optional Firebase cloud features. It also contains local unit tests and Android instrumentation tests. **Presence of source files is not evidence that every workflow works on a real phone.**

The Android CI workflow builds a debug APK on JDK 17 but explicitly **skips unit tests** and does not run instrumentation. The latest observed `main` workflow was successful on 21 September 2026; that means the debug build passed, not that NFC playback, permissions, backup/restore, cloud login or device compatibility were verified.

## Verification still required

1. Run `./gradlew :app:testDebugUnitTest` and review failures.
2. Install the APK on a supported NFC-enabled Android phone and complete onboarding.
3. Import audio, assign it to a card, scan a tag, play/pause/skip, and check foreground/background playback.
4. Verify backup, restore, persistence after app restart and permission-denial handling.
5. Test airplane mode and optional Firebase configuration without leaking credentials.
6. Run instrumented tests on a device/emulator; inspect logcat and test accessibility.

This is an **Android application**, not a website. Browser playtesting cannot substitute for a real Android NFC/device test.

Earlier `docs/COMPLETION_PROOF.md` records a historical scaffold milestone and an old repository URL. It is not proof of current end-to-end operation.
