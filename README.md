[![OpenCore](https://img.shields.io/badge/OpenCore-1.0.5-cyan.svg)](https://github.com/acidanthera/OpenCorePkg/releases/latest) ![MacOS](https://img.shields.io/badge/macOS-Sonoma+-purple.svg) [![release](https://img.shields.io/badge/Download-latest-success.svg)](https://github.com/5T33Z0/Fujitsu-Celsius-H760-OpenCore/releases/latest)

# Fujitsu Celsius H760 OpenCore

## About
OpenCore EFI folder for running macOS Sonoma or newer on the Fujitsu H760 Workstation Laptop. This is a 3.000+ $ workstation laptop I saved from ending as E-Waste. As far as I can tell, this is the first and only OpenCore config for this Celsius Model which is not really surprising given the original price tag of this machine. 

The initial EFI was created with OpCore Simplify and then tweaked and modified to improve compatibility. Installing macOS worked immediately. But getting the iGPU and acceleration to work was rather challenging. It took some time to figure out that output of the iGPU to the DisplayPort is hard-wired through the Nvidia M2000M GPU which has to stay enabled in order to work. This affects brightness controls as well as sleep mode (check &rarr; [Observations](#observations) for details). Further research and tests are required.

## Specs

| **Component** | Description |
|--------------:|:-----------|
| **Model**     | [Fujitsu Celsius H760](https://www.fujitsu.com/hk/products/computing/pc/workstations/celsius-h760/) (Workstation Laptop) |
| **Year**      | 2016 |
| **Chipset**   | QM170 |
| **BIOS**      | 1.35 (2023-01-23) |
| **CPU**       | [Intel Core i7-6820HQ](https://www.intel.com/content/www/us/en/products/sku/88970/intel-core-i76820hq-processor-8m-cache-up-to-3-60-ghz/specifications.html) (Skylake) |
| **Graphics**  | **iGPU**: Intel HD 530 (spoofed as Kaby Lake)<br>**GPU**: NVIDIA Quadro M2000M (not working in macOS) |
| **Audio**     | Realtek ALC255 (ALC-Layout: 3) |
| **Networking**| **Wi-Fi**: Intel Wireless-AC 8260 (Dual Band)<br>**LAN**: Intel I219-LM (1 Gbps)<br>**WWAN**: SIM Card Slot |
| **Storage**   | Samsung CM871a SSD (512 GB) |
| **RAM**       | 16 GB DDR4 SK Hynix (2133 MHz) |
| **SD Card Reader** | Realtek RTS524A PCIE |

**More Details**: [FUJITSU Workstation CELSIUS H760 Data Sheet](https://objects.icecat.biz/objects/mmo_33216273_1477032094_9991_3759.pdf)

## What's working

- [X] Graphic Acceleration (iGPU). Only works if Nvidia Optimus is enabled in BIOS
- [x] External Display via DisplayPort (it's hard-wired through the dGPU, so Nvidia Optimus has to be enabled)
- [x] Audio (including Volume Controls)
- [x] Touchpad (ELAN via PS/2)
- [x] Integrated Camera
- [x] Ethernet
- [x] Wi-Fi and Bluetooth (root patching with OCLP required)
- [x] Battery Status Indicator
- [X] SD Card Reader

## Not working/Todo…
- [ ] dGPU (NVIDIA Quadro M2000M)
- [ ] Sleep: Black-Screen-on-Wake issue if dGPU is enabled
- [ ] Keyboard Shortcut Mappings (currently, only Audio Volume shortcuts are working)
- [ ] Brightness Controls only work if the dGPU is disabled. But then the external display doesn't work.

## BIOS Settings

Change the following options to run macOS:

- **Advanced**
	- **Boot configuration**
		- Fast Boot: Disabled
		- CSM: Disabled
	- **Video Features**
		- NVIDIA Optimus Technology: Enabled
	- **USB Features**
		- Legacy USB Support: Enabled
		- XHCI Controller Setting: Enabled
- **Security**
	- **Secure Boot Configuration**
		- Secure Boot Option: Disabled 	    

## Observations

### Intel HD 530 iGPU Configuration
I attempted to apply a Skylake framebuffer patch for the Intel HD 530 iGPU, followed by OpenCore Legacy Patcher (OCLP) 2.4.0 root patches to enable graphics acceleration in macOS Sonoma.

- **Result**: Root patches were applied successfully, but the Window Server would crash immediately after logging in, kicking me back to the login-screen.
- **Solution**: Reverting root patches and spoofing a Kaby Lake framebuffer instead, so proper graphics acceleration is working

### Nvidia Quadro M2000M and Optimus Configuration

The Celsius H760 uses Nvidia Optimus, where the external display ports (e.g., DisplayPort) are physically routed through the Nvidia Quadro M2000M dGPU, even when the Intel HD 530 iGPU drives the display.

- **Observation**: Applying OCLP root patches for the Quadro M2000M results in a critical issue: The root patches brick macOS, preventing the system from booting, even in Safe Mode.
- **Solution**: Keep the Nvidia Optimus GPU option _enabled_ in the BIOS and avoid applying OCLP root patches for the dGPU. This allows the Intel HD 530 iGPU to drive the external display via the DisplayPort, routed through the Quadro M2000M.
- **Recommendation**: Do not apply OCLP root patches for the Nvidia Quadro M2000M. Otherwise the system becomes unbootable – even in Safe Mode. Ensure Optimus remains enabled in the BIOS to support external displays.

### Related issues: Brightness Control and Sleep Functionality

- **Issues**: The combination of iGPU spoofing (Kaby Lake framebuffer) and the DisplayPort routing through the Nvidia Quadro M2000M causes additional issues:
  - **Brightness Shortcut Keys**: Brightness adjustment keys do not work currently.
  - **Sleep Mode**: The system fails to enter sleep properly. The screen turns black, but the backlight remains on, and the display does not wake, requiring a hard restart.
  - **Possible Cause**: The interaction between the spoofed iGPU configuration and the dGPU’s role in display routing may conflict with macOS’s power management and display control.
