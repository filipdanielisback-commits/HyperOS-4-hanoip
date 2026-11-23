# XotoLoader

## Concept

XotoLoader is a proposed custom startup-menu experience for the HyperOS 4 hanoip project. It is a visual and interaction concept, **not a replacement bootloader**. The Motorola boot chain and original bootloader should remain intact unless a future, separately reviewed engineering plan establishes a safe and necessary reason to change them.

## Proposed screen

- Branding: the project owner's supplied XotoLoader logo.
- Background: black.
- Text: white, with restrained orange highlights matching the logo.
- Device target: Motorola Moto G60, `XT2135-2`, codename `hanoip`.
- Project version label: XotoLoader v1.0.

## Menu options

1. **Start HyperOS 4** — continue the normal startup path into the installed operating system.
2. **Restart device** — request a normal device restart.

## Proposed interaction

- Volume keys: move the selection, if the eventual platform and hardware support this input at the chosen startup stage.
- Power key: activate the selected item, if supported and safely implemented.
- Default selection: Start HyperOS 4.
- The menu should not offer destructive actions such as wiping data or modifying partitions.

The exact key handling and whether this menu can appear before Android starts are **engineering questions**, not confirmed capabilities. They depend on the Moto G60 boot architecture and the chosen implementation layer.

## Startup timing and visual sequence

The initial design idea is to show the original Motorola startup animation, then the XotoLoader branding and menu, followed by HyperOS 4 after the user selects Start HyperOS 4.

A fixed 15-second delay is only a visual proposal. It must not be implemented as an assumption that Android has already booted or that a bootloader can be launched after the Android boot animation. A true pre-OS menu must run at an appropriate early-boot stage; an interface running inside Android is only an ordinary application or system UI and cannot act as a bootloader.

## Safety and project status

- Status: concept / specification only.
- No XotoLoader executable, boot image, bootloader modification, or working menu has been created or tested.
- Preserve the stock bootloader and a recoverable stock-firmware path.
- Any future implementation requires device-specific architecture research, review, and testing on a non-essential test device. Boot-chain changes can make a device unbootable.
- Do not describe XotoLoader as a real bootloader unless it actually implements bootloader functionality and that functionality has been independently verified.

## Acceptance criteria for a future prototype

- Displays the supplied XotoLoader branding clearly.
- Offers exactly the two initial choices: Start HyperOS 4 and Restart device.
- Has a clear selection indicator and accessible navigation.
- Starts the intended OS only after a valid selection, with a safe documented default/fallback.
- Restart performs a normal restart and does not erase user data.
- Does not overwrite or replace the Motorola bootloader.
- Is tested and documented before being described as working.
