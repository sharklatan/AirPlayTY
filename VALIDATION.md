# Validation — 2026-11-19

- Built independently from the copied template layout using tools/build.py. No local source project, YouTube APK or private signing key is required to build the bundle.
- Morphe Desktop 2.2.0 / Patcher 2.4.0 loads the generated bundle and lists exactly one named patch, Sharklatan AirPlay, scoped to app.morphe.android.youtube 21.30.216.
- Actual unsigned patch run completed successfully on the preserved Morphe-generated 21.30.216 APK. That copyrighted test input and its output are not distributed.
- The matching direct APK adaptation was installed separately during development; its initial onResume register reuse failure was fixed by attaching at method entry. User reported playback working. This does not certify all AirPlay receivers or independently establish every end-to-end behavior of the public bundle.
- GitHub Actions publication cannot be tested until the owner uploads this folder to a repository. The workflow derives the Add to Morphe link and download URL from GITHUB_REPOSITORY; no owner name is assumed.
- Previous ReVanced 20.40.45 baseline is preserved in the original project; it was not changed by this repository.

Current limit: second pass over a previously Morphe-patched APK. One-pass integration with the original com.google.android.youtube APK is not implemented in this release.
