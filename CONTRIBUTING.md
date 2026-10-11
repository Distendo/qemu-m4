# Contributing to qemu-m4

qemu-m4 is an experimental QEMU research fork. Contributions should improve
reproducibility, technical accuracy, test coverage, or platform emulation.

## Before starting

1. Read the [QEMU contribution guide](https://www.qemu.org/contribute/).
2. Read `docs/IMAC_M4_ROADMAP.md` and `docs/RESEARCH_LOG.md`.
3. Search existing code and tests before creating a parallel implementation.
4. For hardware claims, provide a public source or reproducible experiment.

## Change expectations

- Keep patches focused and explain the guest-visible behavior being added.
- Include tests for new behavior where feasible.
- Record build and test commands, including host architecture and configuration.
- Document incomplete functionality and known limitations.
- Do not describe code as compatible or verified without test evidence.
- Do not commit proprietary firmware, OS images, keys, credentials, or secrets.
- Follow QEMU's existing style, subsystem patterns, and licensing requirements.

## Suggested change description

- **Problem:** What guest-visible behavior is missing or incorrect?
- **Evidence:** What source or experiment establishes the expected behavior?
- **Implementation:** What changed and why?
- **Tests:** Exact commands and results.
- **Limitations:** What remains unsupported?
