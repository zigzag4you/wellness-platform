# Family Health Platform

An offline-first family health, nutrition, fitness, weight-management, and smart-kitchen application for **Android only**.

**Development status:** an early native Android implementation is under active development in a separate private repository. It currently includes Arabic RTL family-profile flows and encrypted measurement storage. The relational Room + SQLCipher foundation is present but is not yet verified or connected to the active UI. This is not a production-ready app and no release APK is published.

## Product direction
- Family-oriented support for children, teenagers, adults, and older adults.
- Native Android: Kotlin, Jetpack Compose, Android SDK, and Gradle. iOS, Flutter, and Dart are out of scope.
- Offline-first and local-only by default; the core app must not depend on cloud services.
- Optional AI is intended to run entirely on-device. AI does not perform clinical calculations.
- No advertising, behavioral tracking, or unnecessary network access.
- Health calculations must be deterministic, sourced, versioned, and tested.

## Privacy and safety
- Health data is intended to remain on the device and be encrypted at rest.
- The current implementation is incomplete; encryption, recovery, and security have not received final production approval.
- Use synthetic data only during development and testing.
- This software is not a medical device and does not diagnose or treat disease, prescribe medication, or replace qualified professionals.
- Children and teenagers require age-appropriate safeguards. Adult formulas and restrictive weight-loss or calorie targets must not be applied to minors.
- Pregnancy, breastfeeding, older age, and health conditions require appropriately scoped pathways and safeguards.

## Repository purpose and publication policy
This is the **public project and verification repository**, not a mirror of the private development repository. Application source, internal project memory, private planning, sensitive test data, credentials, and unreviewed history must not be published here. Public product/source releases require a separate review and explicit approval.

No commercial product name, logo, or open-source license has been approved. Do not assume permission to reuse, redistribute, or modify this repository until a license is explicitly added.

## Android source verification
The workflow at [`.github/workflows/private-android-ci.yml`](.github/workflows/private-android-ci.yml) checks out the private Android source using a fine-grained read-only token and runs verification on GitHub-hosted runners.

- Triggers: manual dispatch, plus a push limited to changes in the workflow file itself.
- Private source: `zigzag4you/wellness-platform-dev`.
- Required Actions secret: `PRIVATE_REPO_READ_TOKEN`, restricted to the private repository with **Contents: Read-only**.
- Checks: Gradle wrapper integrity, Kotlin unit tests, Android lint, debug APK assembly, and Android emulator instrumentation tests.
- The workflow does not upload or publish the private source, APK, or build outputs. Its logs and summaries are visible in this public repository and may identify the exact private source revision.
- This workflow is a verification mechanism, not a public application release.

### One-time setup
Create a fine-grained token restricted to `wellness-platform-dev` with **Contents: Read-only**, then add it to this repository under **Settings → Secrets and variables → Actions** using the exact name `PRIVATE_REPO_READ_TOKEN`. Never put the token in files, issues, commits, or chat.

Run it from **Actions → Private Android source verification → Run workflow**, selecting `main` or an exact source commit SHA.

## Languages
Project documentation is maintained in Arabic and English. The application UI is currently being developed with Arabic RTL support.
