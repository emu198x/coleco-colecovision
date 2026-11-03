# coleco-colecovision

> Read [`PRINCIPLES.md`](PRINCIPLES.md) first. [`MANIFESTO.md`](MANIFESTO.md) is why the project exists.

The ColecoVision family: its shared wiring, the NTSC and PAL boards, and the headless runtime. It moved out of
[emu198x/emu198x](https://github.com/emu198x/emu198x) with its history under that
repository's [workspace-shape decision](https://github.com/emu198x/emu198x/blob/main/knowledge/decisions/workspace-shape.md),
and is published so machines and siblings take it from crates.io.

## Binding rules

Emu198x's [RULES.md](https://github.com/emu198x/emu198x/blob/main/RULES.md)
requires cycle-accurate CPUs at their evidence-backed native granularity,
and accurate hardware signals and timing. Preserve bus ownership, contention,
DMA, interrupt ordering, held signal values and access side effects.

Bus traits, callbacks, read/write methods and public pin fields are permitted
when they preserve that behaviour. The blanket interface-shape ban was retired
on 2026-10-28; see the
[current bus-interface decision](https://github.com/emu198x/emu198x/blob/main/knowledge/decisions/cpu-bus-interface.md).
An interface shape alone neither proves accuracy nor justifies a rewrite.

## Working here

- Rust pinned in `rust-toolchain.toml`. Before pushing: `cargo fmt --all --check`,
  `cargo clippy --workspace --all-targets -- -D warnings`, `cargo test --workspace`.
- Hardware facts cite the umbrella's `reference/` and `syntheses/`, never another
  emulator's code.
- Land work through pull requests, rebase-merged. Every commit subject and PR
  title is a conventional commit; `feat`, `fix`, `perf` and `revert` earn a release.
- A change to the public API is a change for every machine that uses it. Say what
  an existing caller has to do.
