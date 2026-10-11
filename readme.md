# qemu-m4

**Apple M4 / iMac M4 emulation research in QEMU**

qemu-m4 is an experimental project to investigate and implement the hardware
models needed to emulate an Apple M4-based iMac in QEMU.

The long-term goal is to build an increasingly accurate virtual platform for
Apple Silicon M4 hardware. This includes CPU behavior, SoC devices, boot
infrastructure, and the peripherals required by a guest operating system.

  Warning

   This project is at the initial research and planning stage. It does not
   currently claim to emulate an Apple M4, boot macOS, or reproduce a complete
   iMac. Hardware behavior must be implemented and validated before those
   capabilities can be claimed.

Project goals
-------------

- Investigate what existing QEMU ARM/AArch64 infrastructure can be reused.
- Research publicly documented Apple Silicon architecture and boot requirements.
- Develop a testable plan for an M4-compatible CPU and machine model.
- Incrementally implement and test platform components.
- Document unsupported features, assumptions, and reproducible results.
- Keep changes maintainable against upstream QEMU.

Non-goals
---------

- Claiming that a generic ARM virtual machine is an Apple M4.
- Claiming macOS compatibility without reproducible boot evidence.
- Treating undocumented hardware behavior as known fact.
- Distributing Apple firmware, macOS images, keys, or other proprietary assets.

Status
------

**Current phase: repository setup and feasibility research.**

No custom M4 machine model or complete M4 hardware implementation is claimed
at this stage. See ``docs/IMAC_M4_ROADMAP.md`` for the proposed milestones.

Getting the source
------------------

Clone this repository:

.. code-block:: console

   git clone https://github.com/Distendo/qemu-m4.git
   cd qemu-m4

This repository follows the upstream QEMU source tree. Consult the official
QEMU documentation for current build dependencies and build instructions:

- QEMU documentation: https://www.qemu.org/docs/master/
- Building QEMU: https://www.qemu.org/docs/master/devel/build-system.html
- ARM system emulation: https://www.qemu.org/docs/master/system/target-arm.html
- QEMU contribution guide: https://www.qemu.org/contribute/

Until an M4-specific machine is implemented, use only existing QEMU machine
types documented for your selected target. There is no supported ``imac-m4``
machine type yet.

Development principles
----------------------

1. **Evidence first.** Link hardware claims to public documentation, source
   code, or reproducible experiments.
2. **Incremental implementation.** Make each component independently testable.
3. **No false compatibility claims.** Clearly distinguish implemented,
   partially implemented, researched, and unknown features.
4. **Upstream awareness.** Prefer existing QEMU abstractions and follow the
   project's coding and testing conventions.
5. **Reproducibility.** Record host architecture, build configuration, test
   commands, and results.
6. **Respect proprietary assets.** Users must obtain operating-system images
   and firmware through lawful channels.

Roadmap
-------

See ``docs/IMAC_M4_ROADMAP.md`` for the research and implementation plan.

Contributing
------------

Early contributions are welcome in areas such as architecture research,
documentation, test design, and analysis of existing QEMU ARM system support.

Before proposing implementation changes, read the QEMU contribution guide and
the relevant subsystem documentation. Every hardware feature should include
tests or a clearly documented reason why automated testing is not yet possible.

Project identity
----------------

qemu-m4 is an independent community research project associated with
**WhoSaidImpossible?** It is not affiliated with or endorsed by Apple Inc. or
the QEMU project.

Apple, iMac, macOS, and M4 are trademarks of Apple Inc. QEMU is a trademark
of its respective owners. This project's name describes its research goal,
not an assertion of Apple affiliation or complete compatibility.

The repository's inherited QEMU license and copyright notices remain
applicable. See the existing license and copyright files in the source tree.
