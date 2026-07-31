<img src="logo.png" width="88" alt="BEQ">

# BEQ

Per-application equalizer and effects for Windows. Different curves — and
different effects — for different applications at the same time, applied inside
the Windows audio engine with no added latency.

**[Download the latest build](../../releases/latest)** — Windows x64.

Binaries only; the source code is not published.

## What it does

- 10-band parametric equalizer, applied per application
- Effects behind the equalizer, also per application: bass, compressor,
  chorus, delay, reverb, stereo width
- Presets carry both the curve and the effects, so a sound you liked can be
  saved and reused
- Live per-band spectrum for every source — and the bars are the controls:
  drag for gain, mouse wheel for Q, double-click to reset, Ctrl+Z to undo
- Streams are matched to the applications that produce them automatically
- Follows your default output device when you switch headphones or speakers
- Compact panel: application icons that light up with the sound and radiate a
  wave in its rhythm; click an icon to switch that application's processing
- Microphone tab: volume, EQ, noise gate, presets, monitoring, test recording
- **Check the sound** — one click tells you whether the processing actually
  reaches the speakers for a given application, instead of guessing
- Russian and English interface, global bypass hotkey, start with Windows
- Optional per-site equalizer in the browser through the bundled extension

## Install

Windows 10 (2004 or newer) or Windows 11, x64. Administrator rights required.

1. Unpack the archive anywhere.
2. Run as administrator: `BEQ.exe --install`
3. Start `BEQ.exe`.

The installer registers the audio processing object, attaches it to your
current output device and restarts the Windows audio service — sound stops for
a second. To remove everything: `BEQ.exe --uninstall`.

Windows SmartScreen will warn about an unknown publisher: the binaries are not
code-signed. "More info" → "Run anyway".

## Known limitations

- **Applications that use the low-latency ("raw") output path cannot be
  processed at all.** Windows applies no stream effects to such playback, and
  many games use it. The equalizer has no way in; "Check the sound" reports it
  honestly instead of pretending. Ordinary applications — browsers, players,
  messengers — are processed normally.
- The processing object is **unsigned by design**, so the installer disables the
  Windows protected audio path. DRM-protected playback may stay silent in some
  applications.
- Only **WASAPI Shared** streams can be processed — WASAPI Exclusive, Kernel
  Streaming and ASIO bypass the audio engine.
- **Audio enhancements** must be enabled for the output device, otherwise
  Windows loads no processing objects at all. The Status section detects this
  and offers a one-click fix.
- Microphone processing normally affects monitoring and the test recording
  only; pushing it into other applications requires an effect slot that many
  microphones do not offer.
- No automatic gain compensation: boosting bands can clip loud material, and
  the mixer warns when a curve peaks above 0 dB.
- Site rules cannot work on DRM video or cross-origin media without CORS.

Beta. It changes system audio settings — read the release notes before
installing.
