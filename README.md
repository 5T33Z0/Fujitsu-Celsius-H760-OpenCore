[![OpenCore](https://img.shields.io/badge/OpenCore-1.0.5-cyan.svg)](https://github.com/acidanthera/OpenCorePkg/releases/latest) ![MacOS](https://img.shields.io/badge/macOS-Sonoma+-purple.svg) [![release](https://img.shields.io/badge/Download-latest-success.svg)](https://github.com/5T33Z0/Fujitsu-Celsius-H760-OpenCore/releases/latest)

# Fujitsu Celsius H760 OpenCore

## About
OpenCore EFI folder for running macOS Sonoma or newer on the Fujitsu H760 Workstation Laptop. This is a 3.000+ $ Laptop I saved from ending as e-Waste. As far as I can tell, this is the first and only Hackintosh EFI folder for this Celsius Model which is not really surprising given the original price tag of this machine. 

The initial EFI was created with OpCore Simplify and then tweaked and modified to ensure maximum compatibility.

## Specs

| **Component** | Description |
|:-------------:|:-----------|
| **Model**     | [Fujitsu Celsius H760](https://www.fujitsu.com/hk/products/computing/pc/workstations/celsius-h760/) (Workstation Laptop) |
| **Year**      | 2016 |
| **Chipset**   | QM170 |
| **BIOS**      | 1.35 (2023-01-23) |
| **CPU**       | [Intel Core i7-6820HQ](https://www.intel.com/content/www/us/en/products/sku/88970/intel-core-i76820hq-processor-8m-cache-up-to-3-60-ghz/specifications.html) (Skylake) |
| **Graphics**  | **iGPU**: Intel HD 530 (spoofed as Kaby Lake)<br>**GPU**: NVIDIA Quadro M2000M (not working in macOS) |
| **Audio**     | Realtek ALC25 (ALC-Layout: 3) |
| **Networking**| **Wi-Fi**: Intel Wireless-AC 8260 (Dual Band)<br>**LAN**: Intel I219-LM (1 Gbps)<br>**WWAN**: SIM Card Slot |
| **Storage**   | Samsung CM871a SSD (512 GB) |
| **RAM**       | 16 GB DDR4 SK Hynix (2133 MHz) |
| **SD Card Reader** | Realtek RTS524A PCIE |

**More Details**: [FUJITSU Workstation CELSIUS H760 Data Sheet](https://objects.icecat.biz/objects/mmo_33216273_1477032094_9991_3759.pdf)

## What's working

- [X] Video (iGPU)
- [x] Audio (including Volume Controls)
- [x] External Display. (Only works, if the dGPU is *not* disabled – although it is driven by the iGPU…)
- [x] Touchpad (ELAN)
- [x] Wi-Fi and Bluetooth (Root Patches required)
- [x] Ethernet
- [x] Battery Status Indicator
- [X] SD Card Reader
- [x] Sleep

## Not working/Todo…
- [ ] Keyboard Shortcut Mappings (currently, only Volume buttons work)
- [ ] Waking Screen without additional Keyboard inputs
- [ ] Brightness Controls. These only work if the dGPU is disabled. But then the external display doesn't work…
- [ ] dGPU (NVIDIA Quatro M200M) – I doubt that this will ever work. Maybe, if I could trigger Webdriver Patches in OCLP…

*to be continued…*
