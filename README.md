# GyroLock V11 — Gyro XYZ Smooth & Retry Fix

This version returns to gyro XYZ stabilization; it does not use FFmpeg `deshake`.

## Changes from V9
- Reduces the nested FFmpeg trajectory expression from 120 to 48 key points to lower the chance of expression/parser failures on Android.
- Uses a softer dead-band, slower gyro low-pass filtering, a longer 1.6-second centered path smoothing window, and a moderate 0.72 correction gain to reduce visible jitter during slow pans.
- Keeps 30 FPS output and the MPEG-4 encoder path without the unsupported `-preset` option.
- **Keeps the original recorded clip available after a stabilization failure.** The button becomes `COBA STABILKAN LAGI`, so the user can retry without recording the clip again.
- Clears the pending original only after a processed output has been successfully published.

## Build APK on GitHub
1. Upload the contents of this ZIP to the root of your GitHub repository.
2. Open **Actions** and run **Build GyroLock APK** (or push to `main`/`master`).
3. Download `GyroLock-debug-apk` from the completed workflow's Artifacts.

## Notes
- This is gyro-driven software stabilization, not optical stabilization. Results depend on sensor alignment, recording timing, lens characteristics, and motion.
- This source archive was checked for ZIP integrity. It was not compiled in this environment because Gradle is unavailable here; build it in GitHub Actions and test with a short clip first.
