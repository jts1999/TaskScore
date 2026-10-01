# TaskScore iOS cloud-build setup

This package is prepared for Capacitor 8 and Codemagic so the iOS build can be produced in the cloud without owning a Mac.

## What is already prepared
- TaskScore V5 Plus Preview is in `www/`.
- Capacitor app name: `TaskScore`.
- Provisional bundle identifier: `com.taskscore.productivity`.
- `ios-cloud-check` workflow builds an unsigned simulator app and requires no Apple credentials.
- `ios-testflight` workflow creates a signed IPA and sends it to TestFlight after Apple credentials are connected.

## Before the TestFlight workflow
1. Put this project in a Git repository (GitHub, GitLab or Bitbucket works with Codemagic).
2. Add that repository to Codemagic.
3. Run `TaskScore iOS - Cloud Build Check` first. This verifies that the app compiles on Codemagic's Mac without requiring signing.
4. Join the Apple Developer Program and create the TaskScore app in App Store Connect.
5. Confirm the final bundle identifier. If you change it from `com.taskscore.productivity`, update BOTH `capacitor.config.json` and the `bundle_identifier` in `codemagic.yaml` before the signed build.
6. In Codemagic, add an App Store Connect integration named exactly `codemagic` (or rename the integration entry in `codemagic.yaml` to match the name you choose).
7. Start the `TaskScore iOS - TestFlight` workflow. Codemagic will generate the iOS project, sign it, build the IPA and upload it to TestFlight.

## Important
The Plus screen is still a preview. No subscription/payment, account, cloud backup or sync backend is connected yet.

The iOS project folder is generated during each cloud build and is intentionally not stored in this ZIP.
