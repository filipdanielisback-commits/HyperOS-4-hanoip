# HyperOS-4-hanoip

Community research and development project investigating the feasibility of a **genuine Xiaomi HyperOS 4 system port** for the Motorola Moto G60 (device codename: `hanoip`).

> **Status: Research / not bootable.** This repository currently contains planning and documentation only. No port, installer, recovery package, or working build is available here.

## Project goals

- Determine whether a compatible HyperOS 4 donor firmware and its redistribution terms are available.
- Document the Moto G60 hardware, firmware baseline, partition layout, and existing device support.
- Study compatibility boundaries between Xiaomi system components and Motorola device-specific components.
- Track progress transparently, including what is verified, unknown, blocked, or tested.
- Publish original device-specific work and build documentation where licensing permits.

## What “real port” means here

The goal is to investigate using genuine HyperOS system components, not to present a launcher, icon pack, theme, or AOSP ROM with a HyperOS appearance as a system port. A successful port is **not established** until the system boots on the target device and its core functions are tested.

## Current status

| Area | Status |
|---|---|
| Repository and project documentation | In progress |
| Exact Moto G60 model / SKU confirmation | Not yet verified |
| Device firmware and partition baseline | Not documented yet |
| HyperOS 4 donor build provenance | Unverified |
| Licensing / redistribution review | Pending |
| Compatibility analysis | Not started |
| Build and boot testing | Not started |

See [PORTING_STATUS.md](docs/PORTING_STATUS.md) and [DEVICE_INFO.md](docs/DEVICE_INFO.md).

## Safety and testing notes

- Android firmware modification can permanently damage a device, erase data, or make it unusable. Research first; do not flash experimental images on a daily-use device.
- Keep a verified stock-firmware recovery path and independent backups before any future device testing.
- Never publish private keys, account tokens, device identifiers, personal data, or proprietary firmware dumps.
- Do not redistribute Xiaomi or Motorola proprietary files unless their applicable terms explicitly allow it. Link to lawful sources and document required extraction steps instead.
- Any future installation instructions must state the exact supported model, prerequisites, known risks, and recovery limitations.

## Repository layout

```text
.
├── README.md
├── CONTRIBUTING.md
├── LICENSE-STATUS.md
└── docs/
    ├── DEVICE_INFO.md
    ├── PORTING_STATUS.md
    └── COMPATIBILITY.md
```

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md). Contributions should include sources for technical claims and clearly distinguish measured facts from assumptions.

## Disclaimer

This is an independent community project and is not affiliated with, endorsed by, or supported by Xiaomi or Motorola. HyperOS and related marks belong to their respective owners. All trademarks and copyrights remain with their owners.
