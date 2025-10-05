# NetHunter Kernel for Redmi 5A (riva)

## Short Description
Kali NetHunter-compatible kernel for the Redmi 5A (codename: riva). This project is a NetHunter port built from crDroid's Android 14 kernel sources and includes drivers, injection/monitor support for many external Wi-Fi adapters, HID support, SDR, Bluetooth, and a number of NetHunter-related patches.

## IMPORTANT — Read First ⚠️
- **Do not flash this unless you know what you're doing.** Flashing kernels can brick your device. Proceed at your own risk.
- Install crDroid Android 14 (riva) first. This kernel is built to work with crDroid Android 14 only. See crDroid downloads and installation instructions: [crDroid Downloads](https://crdroid.net/rova/10) and [Installation Guide](https://crdroid.net/rova/10/install).
- You will need OrangeFox recovery (or another compatible custom recovery) to flash crDroid and this kernel zip. Boot into recovery and flash from there.
- crDroid ships with KernelSU by default, but that version may be outdated. Use Magisk 28.0 to root the device for best compatibility (recommended).
- If external Wi-Fi adapters do not show up automatically, install the wireless-firmware Magisk module (available in the Releases).

## Downloads / Releases
Look in the [Releases](https://github.com/ShorterKing/Nethunter-Kernel-Redmi5A-Riva/releases) section for:
- `crdroid14_riva_NetHunter.zip` — Kernel zip that you flash via recovery.
- `wireless-firmware-magisk.zip` — Magisk module with firmware for external adapters.

## Quick Install (Recommended Workflow)
1. Install OrangeFox recovery on your device.
2. Install crDroid Android 14 (riva) following crDroid’s official install guide: [crDroid Installation Guide](https://crdroid.net/rova/10/install). (Flash crDroid first, reboot to recovery if instructed.)
3. Boot into OrangeFox (recovery).
4. From recovery, flash `crdroid14_riva_NetHunter.zip` (from Releases).
5. Reboot device.
6. Root with Magisk 28.0 (install Magisk through recovery or the Magisk app).
7. If external adapters are not detected, flash the wireless-firmware Magisk module (provided in this repo’s Releases or `magisk-modules/`). Reboot.
8. Verify NetHunter functions (Wi-Fi injection, monitor mode, HID devices, etc.).

## Features / What’s Included
This kernel includes (but is not limited to):
- Added RTL88xxAU drivers (support for many Realtek USB Wi-Fi adapters)
- Wi-Fi injection support for external adapters (aircrack-ng style injection)
- Monitor mode for supported adapters
- HID support — broad compatibility with HID devices and keyboards
- HID injection and support for many HID devices
- SDR support (where hardware allows)
- Bluetooth drivers support for a variety of chipsets
- DVB support
- USB mass storage support & improved OTG support (USB 2.0 / 3.0)
- System V IPC enabled as applicable
- Added drivers: Realtek, Ralink, Mediatek, Atmel, ath9k, ADMtek, ath ar9170, Broadcom, VMware VMXNET3 ethernet driver, and more
- HCIUSB support for Broadcom / Realtek / Atheros / Intel / Qualcomm / Marvell adapters
- Mouse and gamepad support (classic PC analog joysticks & many USB gamepads)
- ADC ladder and touch controller support (ADP5588/87/85/89, Atmel AT42 series, etc.)
- HD Audio PCI support with initialization patch loading and multiple codec support (Realtek, Analog Devices, VIA, IDT/Sigmatel)
- All ramdisk compression methods supported (where applicable)
- Default governor: (set to governor — customize in kernel config or via init scripts)
- RFCOMM & RFCOMM TTY support
- Added HID-keyboard support and other HID keyboard compatibility
- Other NetHunter-related patches included to improve tool compatibility
- One more thing if HID does not work please run this command as root 
- mknod --mode=666 /dev/hidg0 c 240 0 && mknod --mode=666 /dev/hidg1 c 240 1 && dmesg | grep hidg

If you rely on a specific external adapter, check its chipset and confirm driver support in this kernel.

## Files in This Repository
- `crdroid14_riva_NetHunter.zip` — Kernel flashable zip (Releases)
- `wireless-firmware.zip` — Magisk module to add extra firmware for external adapters
- `README.md` — This file
- `COPYING` — License file

## Credits
- Original kernel sources: Iusmac / crDroid (Android 14, riva) — [crDroid](https://crdroid.net/rova/10)
- NetHunter port & packaging: ShorterKing (this repo)
- Drivers & patches integrated from various upstream drivers and projects — see kernel `Documentation/` and `COPYING` for details.

## License
This repository is distributed under the GNU General Public License v3.0 (GPLv3) as chosen by the repository maintainer.

**Note:** The Linux kernel itself is traditionally distributed under the GPLv2, and portions of kernel code may be GPLv2-only. Make sure you understand the licensing implications if you plan to relicense or redistribute modified kernel code; keep original `COPYING` and upstream license notices intact and follow the terms of the upstream license(s).

## Support / Reporting Issues
- Open an Issue here on [GitHub](https://github.com/ShorterKing/Nethunter-Kernel-Redmi5A-Riva/issues) and include: device model, crDroid build version, kernel zip version, steps to reproduce, dmesg logs (if available), and the exact external adapter chipset (if relevant).
- Provide logs and exact commands/screenshots where possible.

## Changelog (High Level)
- **v1.0** — Initial NetHunter port from crDroid Android 14; added RTL88xxAU, Wi-Fi injection, HID, SDR, Bluetooth, DVB, numerous drivers & NetHunter patches.


## Final Notes
- Keep crDroid updated separately — if upstream crDroid releases security patches, you will need to rebase/merge them into this kernel to keep it secure and stable.
- If you want this project to be recognized as a fork of crDroid or to submit upstream patches, consider forking the original crDroid repo and maintaining a branch there (or submitting PRs) so your work can be merged upstream.
