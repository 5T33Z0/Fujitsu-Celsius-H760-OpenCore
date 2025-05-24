[![OpenCore](https://img.shields.io/badge/OpenCore-1.0.5-cyan.svg)](https://github.com/acidanthera/OpenCorePkg/releases/latest) ![MacOS](https://img.shields.io/badge/macOS-Sonoma+-purple.svg) [![release](https://img.shields.io/badge/Download-latest-success.svg)](https://github.com/5T33Z0/Fujitsu-Celsius-H760-OpenCore/releases/latest)

# Fujitsu Celsius H760 OpenCore

## About
OpenCore EFI folder for running macOS Sonoma or newer on the Fujitsu H760 Workstation Laptop. This is a 3.000+ $ Laptop I saved from ending as e-Waste. As far as I can tell, this is the first and only Hackintosh EFI folder for this Celsius Model which is not really surprising given the original price tag of this machine. 

The initial EFI was created with OpCore Simplify and then tweaked and modified to ensure maximum compatibility.

## Specs

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-baqh{text-align:center;vertical-align:top}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-7btt{border-color:inherit;font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-uzvj{border-color:inherit;font-weight:bold;text-align:center;vertical-align:middle}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg"><thead>
  <tr>
    <th class="tg-c3ow"><span style="font-weight:700;font-style:normal;text-decoration:none">Component</span></th>
    <th class="tg-0pky"><span style="font-weight:bold">Description</span></th>
  </tr></thead>
<tbody>
  <tr>
    <td class="tg-7btt">Model</td>
    <td class="tg-0pky"><a href="https://www.fujitsu.com/hk/products/computing/pc/workstations/celsius-h760/" target="_blank" rel="noopener noreferrer">Fujitsu Celsius H760</a> (Workstation Laptop)</td>
  </tr>
  <tr>
    <td class="tg-7btt">Year</td>
    <td class="tg-0pky">2016</td>
  </tr>
  <tr>
    <td class="tg-7btt"><span style="font-style:normal;text-decoration:none">Chipset</span></td>
    <td class="tg-0pky">QM170</td>
  </tr>
  <tr>
    <td class="tg-7btt"><span style="font-style:normal;text-decoration:none">BIOS</span></td>
    <td class="tg-0pky">1.35 (2023-01-23)</td>
  </tr>
  <tr>
    <td class="tg-7btt">CPU</td>
    <td class="tg-0pky"><a href="https://www.intel.com/content/www/us/en/products/sku/88970/intel-core-i76820hq-processor-8m-cache-up-to-3-60-ghz/specifications.html" target="_blank" rel="noopener noreferrer">Intel Core i7-6820HQ</a> (Skylake)</td>
  </tr>
  <tr>
    <td class="tg-uzvj" rowspan="2"><span style="font-style:normal;text-decoration:none">Graphics</span></td>
    <td class="tg-0pky"><span style="font-weight:bold">iGU</span>: Intel HD 530 (spoofed as Kaby Lake)</td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-weight:bold">GPU</span>: NVIDIA Quadro M2000M (not working in macOS)</td>
  </tr>
  <tr>
    <td class="tg-baqh"><span style="font-weight:bold">Audio</span></td>
    <td class="tg-0lax">Realtek ALC25 (ALC-Layout: 3)</td>
  </tr>
  <tr>
    <td class="tg-uzvj" rowspan="3"><span style="font-style:normal;text-decoration:none">Networking</span></td>
    <td class="tg-0pky"><span style="font-weight:bold">Wi-Fi</span>: Intel Wireless-AC 8260 (Dual Band)</td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-weight:bold">LAN</span>: Intel I219-LM (1 Gbps)</td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-weight:bold">WWAN</span>: SIM Card Slot</td>
  </tr>
  <tr>
    <td class="tg-7btt">Storage</td>
    <td class="tg-0pky">Samsung CM871a SSD (512 GB)</td>
  </tr>
  <tr>
    <td class="tg-7btt"><span style="font-style:normal;text-decoration:none">RAM</span></td>
    <td class="tg-0pky">16 GB DDR4 SK Hynix (2133 Mhz)</td>
  </tr>
  <tr>
    <td class="tg-c3ow"><span style="font-weight:bold">SD Card Reader</span></td>
    <td class="tg-0pky">Realtek RTS524A PCIE</td>
  </tr>
</tbody></table>

**More Details**: [FUJITSU Workstation CELSIUS H760 Data Sheet](https://objects.icecat.biz/objects/mmo_33216273_1477032094_9991_3759.pdf)

## What's working

- [X] Video (iGPU)
- [x] Audio (including Volume Controls)
- [x] External Display. (Only works, if the dGPU is *not* disabled – although it is driven by the iGPU…)
- [x] Touchpad (ELAN)
- [x] Wi-Fi and Bluetooth (Root Patches required)
- [x] Ethernet
- [x] Battery Status Indicator
- [X] SD Card Reader (no kext required)
- [x] Sleep

## Not working/Todo…
- [ ] Keyboard Shortcut Mappings (currently, only Volume buttons work)
- [ ] Waking Screen without additional Keyboard inputs
- [ ] Brightness Controls. These only work if the dGPU is disabled. But then the external display doesn't work…
- [ ] dGPU (NVIDIA Quatro M200M) – I doubt that this will ever work. Maybe, if I could trigger Webdriver Patches in OCLP…

*to be continued…*

## 📜 License

This repository is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)** license.

**This means**:

- ✅ You may use, share, and adapt this configuration for **personal and non-commercial use**
- ❌ You **may not use it for commercial purposes**
- 🔗 License text: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)

If you use or modify this configuration, please include attribution:

`Original: https://github.com/5T33Z0/Fujitsu_Celsius_H760_OpenCore`
