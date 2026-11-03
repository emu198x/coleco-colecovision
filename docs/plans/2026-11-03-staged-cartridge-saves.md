# Preserve cartridges staged before firmware loading

Engineering-frontier correction of emu198x/emu198x#2186. The user approved the
batch after the Spectrum board work. The family lives in this repository and
is consumed by the umbrella through its published runtime crate.

1. Reproduce accepted cartridge loss on both NTSC/PAL profiles, with two
   distinct synthetic cartridges. Preserve complete original v5 specimens and
   the exact reproducer before changing production code.
2. Agree an explicit snapshot v6 policy with a v5 reader. V6 carries an optional
   staged cartridge only when no live machine owns it. V5 live machines retain
   their own cartridge bytes; v5 empty saves read as empty because absent bytes
   cannot be recovered. Do not apply new-media validation to existing saves.
3. Update snapshot encode/decode and the runtime's internal restored-media
   installation. Validate the full envelope before mutation, retain old fixture
   bytes and exact hardware continuation, and reject contradictory new payloads.
4. Test two staged images, absent/staged-empty distinctions, BIOS installation
   and CPU-visible cartridge execution, dirty restore targets, source-byte
   immutability, legacy readers, running-machine reset/replay and atomic errors.
5. Run fmt, all-target Clippy and workspace tests; push/merge through normal CI.
   Publish the runtime fix before the umbrella consumes it. Record the exact
   published version/package identity; use no local registry override.
6. Retain reviewed heads and evidence in verified recovery archives, then remove
   the task worktree/cache/processes. Leave the primary checkout unchanged.

The user approved v6 with explicit v5 readers on 2026-11-03. Task workspace:
/private/tmp/198x-coleco-staged-state. Shared task evidence/build cache:
/private/tmp/198x-runtime-state-evidence and /private/tmp/198x-runtime-state-target.

## Verified implementation

Version 6 stores a borrowed staged image only while the live machine is absent.
Decode checks version, complete payload, board/profile identity and exclusive
cartridge ownership before installing anything. The v5 reader uses the explicit
old layout. Low-level saved media, including an explicitly empty image, retain
their original admission semantics. No Rust API or dependency changes.

Both regions and two BIOS-executed cartridges survive blank and dirty targets
(eight cases). Original v5 empty captures clear stale BIOS/media without inventing
missing bytes. Existing frozen v5 live machines retain exact hardware, native
video, audio and final state; comparison normalizes only the new envelope version
and absent staging field. Contradictory/truncated/future payloads reject atomically.
Dropping staged bytes deliberately makes the execution regression fail; restored
positive suites and all-target Clippy pass. All original specimen hashes match.
