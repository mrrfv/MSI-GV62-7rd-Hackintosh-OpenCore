# MSI GV62 7rd Hackintosh

An EFI that lets you run macOS Monterey on your MSI GV62 7rd gaming laptop!

**Warning!** This repository is intended for experienced users. You will get very limited support if you don't know what you're doing. You're expected to be able to fix most issues you encounter with this EFI by yourself (contributions are still welcome).

**IMPORTANT:** Windows Defender in [maximum security mode](https://github.com/AndyFul/ConfigureDefender) detects OpenCore's core files as a "severe trojan". You'll have to press "allow on device".

## Hardware

- Display: 15.6" FHD (1920x1080), IPS
- Graphics: GeForce® GTX 1050 with 4GB GDDR5, Intel HD Graphics 5500
- BIOS: Aptio V
- RAM: DDR4 2400MHz, 2 Slots, up to 32GB
- WiFi: Intel WiFi
- Chipset: Intel® HM175
- CPU: Intel Core i5 7300HQ (Kaby Lake)

## Software

- macOS Monterey
- OpenCore 0.7.9

## What works

- Camera
- Sound and built-in mic - speakers not tested, headphones work without any patches.
- WiFi and Bluetooth - Ethernet untested, but should work.
- USB - the macOS installer only boots from USB 2.0
- Touchpad (see below) and built-in keyboard
- Integrated graphics - macOS doesn't support NVIDIA graphics cards - if you play games on your laptop, consider dual-booting.
- HiDPI after using [one-key-hidpi](https://github.com/xzhih/one-key-hidpi)
- FileVault

## What doesn't work (and limitations)

This is my personal bug tracker. I want to daily drive macOS on this laptop, so expect these issues to be fixed sooner or later.

- The NVIDIA GPU is disabled in macOS, only integrated graphics are available (unfixable). To help conserve battery, it's automatically disabled when you're on macOS.
- External monitors (VGA doesn't work, DisplayPort not tested).
- If you're dual-booting macOS with Windows, and your Windows installation is encrypted with VeraCrypt, choosing Windows using the OpenCore picker won't do anything, and you'll need to use your BIOS' boot menu.
- Shutting down while in macOS won't fully shut down the system. I have yet to find a cause for this, but it seems to also happen in Windows, so I suppose there's something wrong with the BIOS.
- Audio hasn't been fully tested.

## Untested

- Apple services (iCloud, iTunes, App Store, etc)

## Installation

### BIOS Settings (required!)

First, unlock advanced BIOS settings by pressing right shift + right Ctrl + left alt + f2.
Enable the following settings (you need to find them):

- DVMT Pre-Allocated: 64MB
- FN/Win Key Swap
- Above 4G decoding
- Intel SpeedShift

Disable the following settings:

- Fast Boot (optional)
- VT-d
- Secure Boot
- CSM
- CFG Lock

These options are the bare minimum in order to get macOS to boot. See [here](https://dortania.github.io/OpenCore-Install-Guide/config.plist/kaby-lake.html#intel-bios-settings) for the full list.

### Create a bootable USB

See [this guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) to create a bootable USB. Instead of putting the unconfigured OpenCore EFI folder to the USB drive, use the one from this repository.

### Boot!

Hold F11 while your laptop starts, and choose your USB drive. Boot the macOS recovery, change the language, open the Disk Utility, format the drive you want to install macOS on as APFS and install. You're done!

See Dortania's [OpenCore Post-Install guide](https://dortania.github.io/OpenCore-Post-Install/) to finish your installation.
