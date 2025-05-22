🚧 WORK in PROGRESS

[![OpenCore](https://img.shields.io/badge/OpenCore-1.0.5-cyan.svg)](https://github.com/acidanthera/OpenCorePkg/releases/latest) ![MacOS](https://img.shields.io/badge/macOS-Sonoma+-purple.svg) [![release](https://img.shields.io/badge/Download-latest-success.svg)]()

# Fujitsu Celsius H760 OpenCore

## About
OpenCore EFI folder for running macOS Sonoma or newer on the Fujitsu H760 Workstation Laptop. This is a 3.000+ $ Laptop I saved from ending as e-Waste. As far as I can tell this is the first and only Hackintosh EFI folder for this system which is not really surprising giving the original price point of this machine. The upload will be located under "Releases" once I am done with configuring, testing and documentation!

## Specs

Component | Description
----------|------------
**Model**     | [FUJITSU CELSIUS H760](https://www.fujitsu.com/hk/products/computing/pc/workstations/celsius-h760/)
**Released**  | 2016
**Chipset**   | QM170
**BIOS**      | 1.35 (2023-01-23)
**CPU**       | [Intel Core i7-6820HQ](https://www.intel.com/content/www/us/en/products/sku/88970/intel-core-i76820hq-processor-8m-cache-up-to-3-60-ghz/specifications.html) (Skylake)
**Graphics**: <ul><li>iGPU <li> dGPU | <br><ul><li>Intel HD Graphics 530 (spoofed as Kabylake) <li> NVIDIA Quadro M2000M (not working in macOS)
**Networking**: <ul><li> WiFi <li>LAN<li>WAN| <br><ul><li>Intel Wireless-AC 8260 (Dual Band) <li>Intel I219-LM (1 Gbps) <li> SIM Card Slot
**Storage**  | Samsung CM871a SSD (512 GB)
**RAM** | 16 GB DDR4 SK Hynix (2133 Mhz)
**SD Card Reader** | Realtek PCIE CardReader
…


## What's working

- [x] iGPU (incuding. Brightness Controls)
- [x] Audio (including Volume Controls)
- [x] LAN
- [x] WiFi/BT (requires patching with OCLP in Post-Install)
- [x] Touchpad (ELAN)
- [x] Battery Status Indicator
- [X] SD Card Reader

### Todo
- [ ] Modifying Framebufffer Patch for attaching external Displays
- [ ] Keyboard Shortcuts Mappings
- [ ] Waking Screen without additional Keyboard inputs
- [ ] USB Port Mapping

…

*to be continued…*

## 📜 License

This repository is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)** license.

**This means**:

- ✅ You may use, share, and adapt this configuration for **personal and non-commercial use**
- ❌ You **may not use it for commercial purposes**
- 🔗 License text: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)

If you use or modify this configuration, please include attribution:

`Original: https://github.com/5T33Z0/Fujitsu_Celsius_H760_OpenCore`
