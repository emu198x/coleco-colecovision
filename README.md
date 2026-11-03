# coleco-colecovision

The ColecoVision family: its shared wiring, the NTSC and PAL boards, and the headless runtime.

| Crate | Registry |
|---|---|
| [`emu198x-common-coleco-colecovision`](crates/emu198x-common-coleco-colecovision) | [crates.io](https://crates.io/crates/emu198x-common-coleco-colecovision) |
| [`emu198x-machine-coleco-colecovision-ntsc`](crates/emu198x-machine-coleco-colecovision-ntsc) | [crates.io](https://crates.io/crates/emu198x-machine-coleco-colecovision-ntsc) |
| [`emu198x-machine-coleco-colecovision-pal`](crates/emu198x-machine-coleco-colecovision-pal) | [crates.io](https://crates.io/crates/emu198x-machine-coleco-colecovision-pal) |
| [`emu198x-runtime-coleco-colecovision`](crates/emu198x-runtime-coleco-colecovision) | [crates.io](https://crates.io/crates/emu198x-runtime-coleco-colecovision) |

Part of [Emu198x](https://github.com/emu198x/emu198x), a family of
cycle-accurate retro-computing emulators. Used by the Emu198x ColecoVision binary and the browser fleet. The first system family to move (pilot).

Each crate is versioned on its own and bumps only when it changes. Releases go
through release-plz: merging its release pull request tags the crate and
publishes it.

Licensed GPL-2.0-or-later.
