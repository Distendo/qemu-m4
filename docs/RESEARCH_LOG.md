# Research log

Use this file to record findings that affect the emulator design.

## Entry template

### YYYY-MM-DD — short topic

- **Question:**
- **Finding:**
- **Evidence:** URL, source path and commit, or reproducible experiment.
- **Confidence:** high / medium / low
- **Unknowns:**
- **Implication for qemu-m4:**
- **Next action:**

---

## Initial questions

- Which parts of QEMU's existing ARM/AArch64 system emulation are reusable?
- What is the scope and limitation of the existing `vmapple` machine?
- What publicly documented information exists for the M4 CPU and platform?
- What boot chain and firmware assumptions are required for each target?
- What is the smallest meaningful test guest for the first machine milestone?
