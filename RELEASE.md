# Release Checklist

## Required checks

Run from the repository root with the lockfile-installed dependencies:

```bash
npm test -- --runInBand
npm run typecheck
```

This repository has no `build` script in `package.json`; do not treat a missing script as a passed build. Validate Android packaging on an approved Android device or CI runner with the declared React Native/Expo toolchain. The on-device ExecuTorch dependency is a sibling workspace and must have generated `lib/module` and `lib/typescript` outputs before Deft's typecheck can resolve it.

## Device and privacy checks

1. Verify the app remains usable in local/Ollama or on-device mode without cloud keys.
2. Review cloud-fallback and provider changes to ensure they remain explicitly opt-in and keys are never logged or committed.
3. Test accessibility permissions, background/overlay permissions, watchdog pause/stop behavior, and model-download failure/recovery on a real device when relevant.
4. Inspect `git diff --check`, changed environment files, generated bundles, and Android native configuration before release.

Keep model files and user conversation/history data out of Git. Release only the reviewed commit and retain a known-good APK/build for rollback.
