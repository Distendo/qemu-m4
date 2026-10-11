# iMac M4 emulation roadmap

This document tracks a research and implementation plan for adding an Apple
M4-based iMac platform to QEMU. It is a plan, not a claim that these features
already work.

## Status vocabulary

- **Unknown** — not yet researched.
- **Researching** — evidence is being collected.
- **Designed** — an implementation plan has been reviewed.
- **In progress** — code exists but is not yet considered complete.
- **Implemented** — code is merged into this fork.
- **Verified** — reproducible tests demonstrate the stated behavior.

Do not mark a feature implemented or verified without evidence.

## Milestone 0 — establish a baseline

- [ ] Record the upstream QEMU commit this fork starts from.
- [ ] Build an unmodified baseline on a documented host.
- [ ] Record host OS, architecture, compiler, Meson, Ninja, and configuration.
- [ ] Identify existing ARM/AArch64 machine models and Apple-related code.
- [ ] Inspect `vmapple` and document what it does and does not model.
- [ ] Enable a repeatable test workflow before adding hardware code.

**Exit criteria:** baseline build and relevant tests are reproducible.

## Milestone 1 — architecture and feasibility research

- [ ] Collect public documentation for Apple Silicon and the M4 family.
- [ ] Separate public facts, experimentally observed behavior, and unknowns.
- [ ] Investigate CPU core configuration and architectural feature reporting.
- [ ] Research memory map, interrupt topology, timers, and boot handoff.
- [ ] Research firmware requirements and device-tree or equivalent platform data.
- [ ] Record evidence and confidence for every hardware assumption.

**Exit criteria:** a cited feasibility report with explicit unknowns and risks.

## Milestone 2 — define the emulation boundary

Decide which target is being built, because these are different projects:

1. **CPU model:** instruction execution and CPU-visible architectural behavior.
2. **SoC/platform model:** CPU plus memory map, interrupts, timers, and devices.
3. **Complete iMac model:** platform plus storage, USB, display, input, networking,
   firmware, and other required peripherals.

- [ ] Choose the first narrow milestone.
- [ ] Define guest-visible behavior and acceptance tests.
- [ ] Identify components that can reuse existing QEMU devices.
- [ ] Document what cannot be emulated accurately with available evidence.

## Milestone 3 — minimal machine skeleton

- [ ] Design a machine type only after documenting the required platform model.
- [ ] Add the smallest useful machine implementation following QEMU conventions.
- [ ] Add memory regions and interrupt/timer wiring based on verified evidence.
- [ ] Add trace points and diagnostic logging.
- [ ] Add unit or integration tests for each new component.
- [ ] Ensure unsupported operations fail clearly instead of silently pretending
  to work.

**Exit criteria:** a deterministic test guest can exercise the implemented
machine skeleton. This does not imply macOS boot support.

## Milestone 4 — boot path

- [ ] Determine the lawful and technically supported firmware strategy.
- [ ] Implement a documented boot handoff for a minimal test payload.
- [ ] Verify CPU entry state, memory layout, interrupts, and console output.
- [ ] Add regression tests for the boot path.

**Exit criteria:** a minimal test payload boots reproducibly with logs and tests.

## Milestone 5 — peripheral expansion

For each device, document its guest-visible interface and test coverage.

- [ ] Storage and block devices
- [ ] USB controller and input devices
- [ ] Display and graphics path
- [ ] Networking
- [ ] Audio
- [ ] Power management and shutdown/reboot behavior
- [ ] Other devices shown to be necessary by evidence

Prefer existing QEMU device models when their interfaces match the researched
hardware. Do not invent device compatibility to make the checklist look full.

## Milestone 6 — operating-system compatibility

- [ ] Establish a lawful test-image and firmware workflow.
- [ ] Document the required boot chain and platform services.
- [ ] Capture complete logs for each attempt.
- [ ] Triage failures by CPU, firmware, interrupt, device, or OS assumptions.
- [ ] Publish only compatibility claims supported by repeatable results.

macOS booting is a research goal, not a current capability claim.

## Engineering gates

Before merging hardware changes:

- [ ] Code follows local QEMU style and build conventions.
- [ ] Relevant tests pass; new behavior has regression coverage.
- [ ] Public sources or experiments support hardware assumptions.
- [ ] Limitations and unsupported behavior are documented.
- [ ] No proprietary firmware, operating-system image, key, or secret is committed.
- [ ] The change does not misrepresent a generic ARM VM as an M4 emulator.

## Initial research references

- QEMU documentation: https://www.qemu.org/docs/master/
- QEMU ARM system emulation: https://www.qemu.org/docs/master/system/target-arm.html
- QEMU build system: https://www.qemu.org/docs/master/devel/build-system.html
- QEMU contribution guide: https://www.qemu.org/contribute/
- QEMU source mirror: https://github.com/qemu/qemu

Keep a dated research log in `docs/RESEARCH_LOG.md`; cite the exact source or
reproduction steps for each meaningful claim.
