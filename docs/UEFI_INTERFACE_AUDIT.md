# XotoLoader UEFI interface audit

**Status: Preliminary public-source audit. No device-side testing has been performed.**

## Objective

Assess whether the stock Moto G60 / hanoip boot environment is documented well enough to support a native EFI application such as a future XotoLoader menu.

## Evidence collected

### A. Public bootloader-variable report

A public Moto G60 (XT2135-2) forum post reproduces output from `fastboot getvar all` including:

- `kernel: uefi`
- `version-bootloader: MBM-3.0-hanoip_retail-c29b299de0-211118`
- `product: hanoip`

This is useful device-specific evidence that the bootloader identifies its kernel/environment as UEFI. It is a third-party user report, not Motorola firmware documentation, and it does not expose the UEFI System Table or prove that arbitrary third-party EFI applications can be launched.

Source: [4PDA Moto G60 report](https://4pda.to/forum/index.php?showtopic=1035942).

A separate public bootloader log includes a `git:uefisecapp` version field and A/B slot information. This corroborates that a component named uefisecapp exists in the firmware ecosystem, but does not document its application interfaces.

Source: [GSM-Forum Moto G60 bootloader log](https://forum.gsmhosting.com/vbb/f898/moto-g60-flashing-failed-need-help-3244373/).

### B. Hanoip Android device tree

The public hanoip device tree's `BoardConfig.mk` documents an ARM64 Android target, Android boot image header v3, device-tree inclusion, and AVB build configuration. It is an Android build configuration, not a specification of the pre-OS firmware interfaces.

Source: [hanoip BoardConfig.mk](https://github.com/motorola-sm6150-devs/device_motorola_hanoip/blob/514e0261a117a0c7e7fa3cc3cd44f80819b0b779/BoardConfig.mk).

The same tree's `gpt-utils/gpt-utils.h` lists a partition called `uefisecapp`. A partition name alone does not prove standard EFI application loading support.

Source: [hanoip gpt-utils.h](https://github.com/motorola-sm6150-devs/device_motorola_hanoip/blob/514e0261a117a0c7e7fa3cc3cd44f80819b0b779/gpt-utils/gpt-utils.h).

## Interfaces a native EFI app would need

At minimum, a real EFI application expects a firmware-provided EFI system table and the relevant Boot Services. A useful menu also needs a way to draw to the display and receive input. Android's Generic Bootloader documentation lists required UEFI interfaces for its own use, including Block I/O, RNG, memory allocation, text output, and Android-specific protocols for AVB and boot control.

Sources:
- [Android GBL overview](https://source.android.com/docs/core/architecture/bootloader/generic-bootloader)
- [Android GBL deployment requirements](https://source.android.com/docs/core/architecture/bootloader/generic-bootloader/gbl-dev)

GBL's requirements are not a checklist that can be assumed to exist on hanoip. They illustrate why the word "UEFI" in a bootloader variable is not enough to establish compatibility.

## Compatibility matrix

| Question | Evidence | Result |
|---|---|---|
| Does a public hanoip bootloader report say `kernel: uefi`? | Third-party fastboot output for XT2135-2 | Reported |
| Is there a bootloader named MBM-3.0-hanoip? | Same output | Reported |
| Is a `uefisecapp` component referenced? | Public device-tree code and third-party log | Yes |
| Is an EFI System Table available to a third-party app? | No inspected source documents it | Unknown |
| Are EFI Boot Services and required protocols available? | No inspected source documents them | Unknown |
| Can a custom `.efi` application be loaded by stock firmware? | No verified evidence | Unknown |
| Can XotoLoader safely present a pre-OS menu today? | Not demonstrated | No prototype |

## Conclusion

The evidence supports a narrower statement than "the Moto G60 is fully UEFI-app compatible":

**The Moto G60 bootloader reports a UEFI kernel/environment, and its firmware ecosystem references a uefisecapp component. Public evidence reviewed so far does not establish that the stock firmware exposes a general-purpose EFI application environment or supports launching third-party EFI programs.**

## Next research milestone

Seek device-specific technical documentation or source that describes the MBM/ABL handoff and explicitly confirms the EFI application entry environment and protocols available on hanoip. Until that evidence exists, keep XotoLoader as a design/specification project and do not build or install experimental boot firmware.

No instructions in this document authorize modifying boot-critical partitions. Keep the original Motorola boot chain intact; boot-chain experiments can make the phone unbootable and may erase data.
