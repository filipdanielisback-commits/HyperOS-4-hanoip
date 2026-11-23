# EFI / UEFI feasibility research for XotoLoader

**Status: Unverified — research only. No EFI application or firmware has been built or tested for hanoip.**

## Research question

Can XotoLoader run as a native EFI application in the Motorola Moto G60 (XT2135-2, codename `hanoip`) boot environment, without replacing the stock Motorola boot firmware?

## Findings from public sources

### 1. The available hanoip Android device tree

The public [Motorola hanoip device tree](https://github.com/motorola-sm6150-devs/device_motorola_hanoip) is an Android device tree for the Moto G40 Fusion / Moto G60.

Its `BoardConfig.mk` identifies:
- `TARGET_BOARD_PLATFORM := sm6150`
- `TARGET_BOOTLOADER_BOARD_NAME := hanoip`
- ARM64 as the primary target architecture
- Android boot image header version 3
- DTB inclusion in the boot image
- Android Verified Boot (AVB) build configuration

These are useful Android build and boot-image details. They do **not** demonstrate that the stock firmware exposes a general-purpose UEFI environment to third-party EFI applications.

Source: [hanoip BoardConfig.mk](https://github.com/motorola-sm6150-devs/device_motorola_hanoip/blob/514e0261a117a0c7e7fa3cc3cd44f80819b0b779/BoardConfig.mk).

### 2. UEFI-related partition references

The same repository's `gpt-utils/gpt-utils.h` contains the GPT signature string `EFI PART` and lists a partition named `uefisecapp`.

These are UEFI/GPT-related names, but neither one proves that the phone provides the UEFI Boot Services, Runtime Services, or protocols required to launch an arbitrary `.efi` program. GPT is a partition-table format; a partition name is not an EFI application interface.

Source: [hanoip gpt-utils.h](https://github.com/motorola-sm6150-devs/device_motorola_hanoip/blob/514e0261a117a0c7e7fa3cc3cd44f80819b0b779/gpt-utils/gpt-utils.h).

### 3. Android Generic Bootloader requirements

Android's official Generic Bootloader (GBL) documentation says that deployment requires UEFI-compliant boot firmware and required UEFI protocols. It also requires Android Verified Boot support, handling of normal/recovery/fastboot modes, slot selection and dynamic partition support, and the ability to provide OEM-specific kernel command line, device tree, and bootconfig data.

Sources:
- [Android GBL overview](https://source.android.com/docs/core/architecture/bootloader/generic-bootloader)
- [Android GBL deployment requirements](https://source.android.com/docs/core/architecture/bootloader/generic-bootloader/gbl-dev)

This documentation describes what GBL needs; it does not certify the Moto G60 firmware as GBL-compatible.

## Important correction

A previous project discussion described the Moto G60 as already using UEFI internally. The evidence collected so far is not sufficient to establish that claim. Firmware identifiers such as Motorola's MBM bootloader version, GPT metadata, or a partition named `uefisecapp` must not be treated as proof that a standard UEFI application environment is available.

The accurate current conclusion is:

**The Moto G60 has UEFI-related artifacts in its Android/firmware ecosystem, but native EFI application support on its stock boot firmware remains unverified.**

## XotoLoader implementation options

1. **Native pre-OS EFI application:** Only viable if the stock boot firmware actually exposes the necessary UEFI application-loading environment and protocols. This has not been established.
2. **Android-stage startup interface:** A menu implemented after Android starts is technically a different kind of feature. It cannot directly choose the kernel before Android boots and should not be presented as a bootloader.
3. **Custom boot firmware:** Replacing or modifying the Motorola boot chain is a separate, high-risk research project and is not the current plan.

The preferred direction is to investigate option 1 while preserving the stock boot chain. If that cannot be verified, reconsider the design rather than attempting to replace firmware.

## Evidence still needed

- Reliable documentation of the exact XT2135-2 / hanoip boot stages and firmware interfaces.
- Confirmation of whether the stock firmware implements the UEFI System Table and relevant Boot Services.
- Confirmation of which UEFI protocols, if any, are exposed to a third-party EFI application.
- Verified information about firmware image formats, signing/authentication policy, and supported boot paths.
- A safe, non-destructive way to validate compatibility without writing to boot-critical storage.

No test should involve flashing an experimental bootloader or EFI image to the phone. Firmware and boot-chain changes can make a device unbootable and may erase data.

## Current assessment

| Question | Assessment |
|---|---|
| Is the device ARM64? | Yes, in the public Android device tree |
| Does the device tree configure Android boot images and AVB? | Yes |
| Are there UEFI/GPT-related references in public source? | Yes |
| Does this prove standard UEFI application support? | No |
| Can XotoLoader currently be built as a working EFI app for hanoip? | Not established |
| Should the stock Motorola boot chain be replaced now? | No |
