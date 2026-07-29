<img src="logo.png" width="88" alt="BEQ">

# BEQ

Per-application equalizer for Windows. Different EQ curves for different
applications at the same time, applied inside the Windows audio engine with no
added latency.

**[Download the latest beta](../../releases/latest)** — Windows x64.

Binaries only; the source code is not published.

## What it does

- 10-band parametric equalizer, per application
- Live per-band spectrum for every source — and the bars are the controls:
  drag for gain, mouse wheel for Q, double-click to reset
- Streams are matched to the applications that produce them automatically
- Follows your default output device when you switch headphones or speakers
- Compact tray panel plus a full window with browser-style tabs
- Microphone tab: volume, EQ, noise gate, presets, monitoring, test recording
- Russian and English interface, global bypass hotkey, start with Windows
- Presets, configuration export and import
- Optional per-site equalizer in the browser through the bundled extension

## Install

Unpack the archive and run as administrator:

```
BEQ.exe --install
```

Then start `BEQ.exe`; it lives in the tray. To remove: `BEQ.exe --uninstall`.

## Known limitations

- The audio processing object is **unsigned by design**, so installing disables
  the Windows protected audio path. DRM-protected playback may stay silent in
  some applications.
- Only **WASAPI Shared** streams can be processed — WASAPI Exclusive, Kernel
  Streaming and ASIO bypass the audio engine.
- **Audio enhancements** must be enabled for the output device, otherwise
  Windows loads no processing objects at all.
- No automatic gain compensation: boosting bands can clip loud material.
- Site rules cannot work on DRM video or cross-origin media without CORS.

Status: beta. It changes system audio settings — read the notes in the release
before installing.
