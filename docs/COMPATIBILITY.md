# Compatibility investigation

This document tracks the technical questions that must be answered before claiming compatibility.

## Donor build

The project has a user-provided YouTube Short titled “HyperOS 4 ported from Xiaomi 17T Pro to TECNO LH8n” as a research lead:

https://www.youtube.com/shorts/HX4AFNP6IrQ

The video title is a claim, not independent proof of the donor package contents, framework provenance, or functionality. The exact donor build, release identifier, Android base, firmware package, and modifications remain **unverified**.

## Compatibility areas to investigate

| Area | Questions | Status |
|---|---|---|
| Android framework | Which framework and system services are required by the donor build? | Unknown |
| Kernel / boot image | Can the target's supported kernel and boot configuration satisfy system requirements? | Unknown |
| Vendor / HAL | Which Moto-specific hardware interfaces are needed? | Unknown |
| Graphics | Are the graphics stack and display interfaces compatible? | Unknown |
| Radio / telephony | Are modem and vendor interfaces compatible with the target firmware? | Unknown |
| Camera | Are compatible camera HALs and libraries available? | Unknown |
| Audio | Are audio policy and hardware interfaces compatible? | Unknown |
| Biometrics / sensors | Are target-specific services and permissions available? | Unknown |
| Partitions / dynamic partitions | Do image sizes and partition expectations fit the target? | Unknown |
| Encryption / boot verification | What security and data-encryption constraints apply? | Unknown |

## Important distinction

A successful boot animation or launcher screenshot is not enough to establish a usable port. Compatibility must be tested feature by feature and documented with reproducible evidence.
