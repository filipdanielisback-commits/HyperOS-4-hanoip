# Porting status

**Overall state: Research only — no working port exists in this repository.**

Last reviewed: 2026-11-23

## Milestones

- [x] Create project repository and initial documentation
- [ ] Confirm exact Moto G60 model / regional SKU
- [ ] Establish stock firmware and device baseline
- [ ] Identify a legitimate, compatible HyperOS 4 donor build
- [ ] Verify donor build version, device origin, Android base, and provenance
- [ ] Review license and redistribution restrictions for every component
- [ ] Map hardware-dependent components and compatibility gaps
- [ ] Define a safe, reproducible build and test plan
- [ ] Perform controlled testing on a non-essential test device
- [ ] Validate boot, display, touch, audio, Wi-Fi, Bluetooth, mobile network, cameras, sensors, charging, encryption, and stability
- [ ] Publish verified results and limitations

## Evidence rules

Use these labels in issues and pull requests:

- **Verified** — supported by reproducible logs, source code, or reliable documentation.
- **Observed** — seen in a test, but not yet independently reproduced.
- **Hypothesis** — plausible explanation that still needs testing.
- **Unknown** — no reliable evidence yet.
- **Blocked** — work cannot proceed until a dependency or permission is resolved.

A screenshot of a themed interface alone does not prove that the underlying operating system is a genuine HyperOS system port.

## Current known blockers

1. Exact Moto G60 variant and stock firmware baseline are unknown.
2. The HyperOS 4 donor build shown in the Tecno LH8n video has not been independently inspected.
3. Compatibility between the donor system and Moto G60 hardware has not been established.
4. Redistribution permissions for proprietary firmware components have not been reviewed.
