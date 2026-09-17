# JoshTapApp — Beautiful Code Standard Audit

**Audit date:** 17 September 2026  
**Repository tier:** Critical / relied-upon  
**Standard:** The Beautiful Code Standard

## Overall finding

JoshTapApp has a healthy Android/Kotlin structure with ViewModels, repositories, backup/database code, Android instrumentation tests and a build workflow. It is substantially closer to the Beautiful Code Standard than a repo with no automated evidence.

The main gap is that CI explicitly builds with unit tests skipped and then states that instrumentation is omitted. That means the repository contains useful behavioural tests that are not part of the release evidence.

## What is already good

- Android application code is separated into focused classes rather than one monolithic file.
- Database and onboarding instrumentation tests exist.
- CI performs a reproducible debug build on pushes and pull requests.
- Kotlin/Android project conventions make the entry points and platform boundaries familiar.
- Backup and persistence concerns appear separated into dedicated code rather than hidden inside UI classes.

## Main gaps

- **Reality first:** current CI uses `assembleDebug` and explicitly skips unit/instrumentation tests. A green workflow therefore proves compilation, not behaviour.
- **Tests:** existing Android tests should be run automatically where practical; add JVM unit tests for logic that does not need an emulator.
- **Data safety:** database and backup/restore paths deserve especially strong regression coverage because failures can lose or corrupt user state.
- **Repository neatness:** large prompt/history documents such as `Prompts 1 to 13 - TapApp.txt` are development history rather than runtime source. Keep them only if they remain genuinely useful; otherwise Git already remembers their history.
- **Security:** add dependency and secret scanning appropriate to Android/Gradle projects.
- **Smoke testing:** the critical user journey should be exercised on an emulator/device: launch → onboarding if needed → choose/use a card/audio item → persist/reopen.

## Priorities

1. Stop describing compile-only CI as sufficient behavioural evidence: run `test` tasks and the existing instrumentation suite in CI, or clearly separate build and device-test jobs.
2. Add regression tests around database writes, migrations, backup and restore.
3. Add one emulator smoke test for the main real-user flow.
4. Add dependency/security and secret scanning.
5. Remove or relocate stale prompt-history artefacts if they no longer help maintain the product.
6. Use CRAP, CC and coverage as ratchets/signals after the test pipeline is trustworthy, not as substitutes for it.

## Bottom line

The codebase already has good testing ingredients. The next step is simple: **make CI actually run the tests the repository already contains.**
