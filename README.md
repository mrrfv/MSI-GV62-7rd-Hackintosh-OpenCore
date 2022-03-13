# MSI GV62 7rd Hackintosh

An EFI that lets you run macOS Monterey on your MSI GV62 7rd gaming laptop!

**Warning!** This repository is intended for experienced users. You will get very limited support if you don't know what you're doing.

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

- WiFi and Bluetooth
- Sound (speakers not tested, headphones work without any patches)
- Touchpad and built-in keyboard
- Camera
- Integrated graphics (macOS doesn't support NVIDIA graphics cards - if you play games on your laptop, consider dual-booting).
- USB (installer only boots from USB 2.0)
- HiDPI after using [one-key-hidpi](https://github.com/xzhih/one-key-hidpi)
- FileVault

## What doesn't work (and limitations)

- The NVIDIA GPU is disabled in macOS, only integrated graphics are available (unfixable). To help conserve battery, it's automatically disabled when you're on macOS.
- External monitors (VGA, DisplayPort not tested)
- If you're dual-booting macOS with Windows, and your Windows installation is encrypted with VeraCrypt, choosing Windows using the OpenCore picker won't do anything, and you'll need to use your BIOS' boot menu.
- The built-in microphone doesn't work, and headphones might not work if they're plugged in when macOS is booting. This might be fixable by using different layout-id's, so TBD.

## Untested

- Apple services (iCloud, iTunes, App Store, etc)

## Installation

### BIOS Settings (required!)

First, unlock advanced BIOS settings by pressing right shift + right Ctrl + left alt + f2.
Enable the following settings (you need to find them):

- DVMT Pre-Allocated(iGPU Memory): 64MB
- FN Key Swap
- Above 4G decoding

Disable the following settings:

- Fast Boot (optional)
- VT-d
- Secure Boot

See [here](https://dortania.github.io/OpenCore-Install-Guide/config.plist/kaby-lake.html#intel-bios-settings) for the full list.

### Create a bootable USB

See [this guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) to create a bootable USB. Instead of putting the unconfigured OpenCore EFI folder to the USB drive, use the one from this repository.

### Boot!

Hold F11 while your laptop starts, and choose your USB drive. Boot the macOS recovery, change the language, open the Disk Utility, format the drive you want to install macOS on as APFS and install. You're done!

See Dortania's [OpenCore Post-Install guide](https://dortania.github.io/OpenCore-Post-Install/) to finish your installation.
