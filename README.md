# Family Health Platform

An offline-first family health, nutrition, fitness, weight-management, and smart-kitchen application for **Android only**.

**Development status:** an early native Android implementation is under active development in a separate private repository. It currently includes Arabic RTL family-profile flows and encrypted profile/measurement storage using Android Keystore and AES-GCM. A Room + SQLCipher database foundation is present but has not yet been verified by a successful complete instrumentation run or connected to the active UI. This is not a production-ready app and no release APK is published.

## Product direction
- Family-oriented support for children, teenagers, adults, and older adults, with age-appropriate pathways.
- Native Android: Kotlin, Jetpack Compose, Android SDK, and Gradle. iOS, Flutter, and Dart are out of scope.
- Offline-first and local-only by default; the core app must not depend on cloud services.
- Optional AI is intended to run entirely on-device. AI does not perform clinical calculations.
- No advertising, behavioral tracking, or unnecessary network access.
- Health calculations must be deterministic, sourced, versioned, and tested.

## Privacy and safety
- Health data is intended to remain on-device and encrypted at rest.
- The current implementation is incomplete; encryption, recovery, and security have not received final production approval.
- Use synthetic data only during development and testing.
- This software is not a medical device and does not diagnose or treat disease, prescribe medication, or replace qualified professionals.
- Adult formulas and restrictive weight-loss/calorie targets must never be applied to children or teenagers.
- Pregnancy, breastfeeding, older age, and health conditions require distinct, appropriately reviewed pathways.
- Allergy and dietary-exclusion handling must fail safely when ingredient data is incomplete.

## Repository roles and publication policy
- `wellness-platform-dev` (private) is the development source of truth.
- This repository is public and selectively curated; it is not a mirror of the private repository.
- Never publish private source, project memory, internal notes, secrets, health data, sensitive test data, or unreviewed history here.
- No public application source release or APK publication is implied by this repository.
- No commercial product name, logo, visual identity, or open-source license has been approved. Do not assume permission to reuse, redistribute, or modify this repository until a license is explicitly added.

## Current implementation status
The private Android project has a native application shell, Arabic RTL family-profile flows, encrypted profile and measurement stores, and a preliminary Room + SQLCipher database foundation.

Encrypted JSON stores remain the active persistence path. Room/SQLCipher is not yet confirmed by a successful complete instrumentation run or connected to the UI. App lock, complete family permissions, verified encrypted backup/restore, health calculation engines, food/meal/activity modules, and on-device AI are not yet complete.

**No production-ready release is available. Use synthetic data only.** Verification results must be tied to an exact private source commit; a successful build alone does not mean the app is release-ready.

## Private Android verification
The workflow [`.github/workflows/private-android-ci.yml`](.github/workflows/private-android-ci.yml) checks out a selected revision of `zigzag4you/wellness-platform-dev` using the Actions secret `PRIVATE_REPO_READ_TOKEN`, restricted to read-only access.

It runs Gradle wrapper integrity checks, Kotlin unit tests, Android lint, debug APK assembly, and Android emulator instrumentation tests on standard GitHub-hosted runners.

- Triggers: manual dispatch, plus a push limited to changes in the workflow file itself on `main`.
- Configure the fine-grained token under **Settings → Secrets and variables → Actions** as `PRIVATE_REPO_READ_TOKEN`; never place the token in source, issues, logs, or chat.
- Select an exact source commit when reproducibility is required.
- The workflow does not upload the private source tree or APK; its runner is ephemeral.
- Public workflow logs and summaries may expose the tested source SHA and test outcomes, but not the private source or APK.

## Languages
Arabic and English documentation are maintained. The application UI is being developed with Arabic RTL support.
