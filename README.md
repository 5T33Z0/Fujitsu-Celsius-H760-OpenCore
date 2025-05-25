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
- [x] External Display. (Only works, if the dGPU is *not* disabled. It seems that the DisplayPort is hard-wired through the dGPU.)
- [x] Touchpad (ELAN)
- [x] Wi-Fi and Bluetooth (Root Patches required)
- [x] Ethernet
- [x] Battery Status Indicator
- [X] SD Card Reader

## Not working/Todo…
- [ ] Keyboard Shortcut Mappings (currently, only Volume buttons work)
- [ ] Waking Screen without additional Keyboard inputs
- [ ] Brightness Controls. These only work if the dGPU is disabled. But then the external display doesn't work…
- [ ] dGPU (NVIDIA Quatro M200M) – I doubt that this will ever work. Maybe, if I could trigger Webdriver Patches in OCLP…

## Observations

### Intel HD530, OCLP and iGPU spoofing
I've tried to use a Skylake Framebuffer Patch and then apply root patches with OCLP to re-enable the Intel HD530 in macOS Sonoma. The patches were applied but graphics acceleration was not working afterwards. So, spoofinfg a Kaby Lake Framebuffer Patch is the way to go with this system 

### NVIDIA Optimus
I've noticed that OpenCore Legacy Patcher can apply root patches for the Nvidia Quadro M2000M GPU, if the NVIDIA Optimus GPU Option in BIOS is _disabled_. Don't do this! You won't be able to boot into macOS – not even in Safe Mode! Instead, leave the Optimus option _enabled_ so that the DisplayPort can be used by the Intel HD530 iGPU to drive an external display! 

### Related issues
I think the combination of iGPU sppofing and the DisplayPort being physically routed through the Nvidia Quadro causes additional issues: Brightness Shortcut keys are not workingt. The system doesn't enter sleep properly, only the screen turns black while the backlight stays on and won't return to displaying a picture.
