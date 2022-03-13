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
- OpenCore 0.7.5

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

- The NVIDIA GPU is disabled in macOS, only integrated graphics are available (unfixable).

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

See [https://dortania.github.io/OpenCore-Install-Guide/config.plist/kaby-lake.html#intel-bios-settings](here) for the full list.
