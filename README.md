# Family Health Platform

An offline-first family health, nutrition, fitness, and smart-kitchen application for Android and iOS.

**Current state:** project foundation only. No production-ready application or release is available yet.

## Principles
- Designed for family members across age groups, with age-appropriate safeguards.
- Local-first data storage and privacy-conscious defaults.
- Core functionality does not depend on a cloud service or language model.
- Health calculations are deterministic, documented, and separated from generative AI.
- Optional AI is intended to run on-device only.
- No advertising or behavioral tracking is planned.

## Repository purpose
This is the public, selectively curated release repository. It is not a mirror of the private development repository. Internal project memory, private planning, sensitive test data, and unreviewed history must never be published here.

## Safety
This software is not a medical device and does not diagnose or treat disease, prescribe medication, or replace qualified professionals. Features involving minors require age-appropriate safeguards and guardian involvement. Adult weight and calorie rules must not be applied to children or teenagers.

## Project status
Specifications and architecture are being developed privately before implementation. No commercial product name, logo, or open-source license has been approved. Do not assume permission to reuse, redistribute, or modify this repository until a license is explicitly added.

## Languages
The intended product and project documentation support Arabic and English.


## Private Android verification

This public repository contains a manually triggered CI workflow only; it does not mirror or contain the private application source.

- Workflow: `.github/workflows/private-android-ci.yml`
- It checks out the selected revision of `zigzag4you/wellness-platform-dev` using a read-only token stored as the Actions secret `PRIVATE_REPO_READ_TOKEN`.
- It runs Kotlin unit tests, Android lint, a debug APK assembly, and emulator instrumentation tests on standard GitHub-hosted Ubuntu runners.
- The APK, source tree, and build outputs are not uploaded or published. The runner is ephemeral.
- The workflow is manual-only (`workflow_dispatch`) to avoid exposing a private-repository credential to untrusted pull-request or push workflows.

### One-time setup

Create a fine-grained personal access token restricted to the private repository `wellness-platform-dev`, with **Contents: Read-only** permission, then add it to this public repository under **Settings → Secrets and variables → Actions** with the exact name `PRIVATE_REPO_READ_TOKEN`. Do not paste the token into issues, files, commits, or chat.

Then open **Actions → Private Android source verification → Run workflow**, choose `main` (or an exact commit SHA), and run it. Workflow logs and the verification summary are public; they contain the source revision and step results, not the application source or APK.
