# Device information: Motorola Moto G60

## Target identity

| Field | Value | Verification |
|---|---|---|
| Manufacturer | Motorola | Confirmed by Motorola documentation |
| Marketing name | moto g60 / moto g60 vision | Motorola identifies XT2135-2 as moto g60 vision |
| Model number | `XT2135-2` | Supplied by project owner; matches Motorola's EU declaration |
| Device codename | `hanoip` | Present in the matching firmware package name |
| RAM | 6 GB | Supplied by project owner; not independently measured |
| Current firmware | `S2RIS32.32-20-9-9-2-3` | Supplied by project owner; matching XT2135-2 RETEU firmware package is listed publicly |
| Region / channel | RETEU (Europe) is a strong match | Inferred from the matching firmware package name; confirm the phone's software channel |
| Android version | Android 12 for this firmware package | Firmware listing labels the package Android 12; confirm on handset |
| Storage capacity | Unknown | Not supplied |
| Current build fingerprint | Unknown | Not collected |

## Firmware identity

The reported build string matches the public package name:

`XT2135-2_HANOIP_RETEU_12_S2RIS32.32-20-9-9-2-3_subsidy-DEFAULT_regulatory-XT2135-2-EUROPE_cid50_CFC.xml.zip`

This is useful evidence for identifying the correct regional firmware family. It does **not** prove that the handset currently has every partition or component from that package, nor does it establish compatibility with a Xiaomi donor ROM.

## Required baseline before any porting work

Before device-specific engineering, confirm from the handset's Settings > About phone:
- Exact model number and software channel
- Android version and security patch level
- Full build number
- RAM and storage variant

Do not share IMEI, serial number, phone number, account identifiers, or other private device identifiers.

## Evidence and references

- [Motorola EU declaration of conformity for XT2135-2](https://en-gb.support.motorola.com/ci/fattach/get/79315385/1664922506/redirect/1/filename/XT2135-2_Moto%2BG60%2BVision%2BMC38C%2BRED%2BDoC.pdf) identifies XT2135-2 as moto g60.
- [Motorola support model list](https://en-gb.support.motorola.com/app/answers/detail/a_id/167829) lists XT2135-2 as moto g60 vision.
- [Motorola kernel source request for this exact firmware release](https://github.com/MotorolaMobilityLLC/kernel-msm/issues/574) references the XT2135-2 HANOIP RETEU S2RIS32.32-20-9-9-2-3 package.
- [Public firmware listing](https://romdevelopers.com/index.php?a=downloads&b=tags&tag=Moto+G60+Update) lists the matching package and identifies it as Android 12.

## Privacy note

Never commit IMEI, serial number, phone number, account identifiers, or unredacted diagnostic logs.
