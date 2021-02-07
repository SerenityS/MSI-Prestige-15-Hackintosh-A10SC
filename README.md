# MSI Prestige 15 Hackintosh
This project uses OpenCore to boot the EFI instance of MSI Prestige 15 16G 512GB FullHD notebook. The OpenCore version is 0.6.6, which is compatible with Big Sur (11.1.x).

## Hardware driver description
| Type               | Model                                 | Remarks                   |
| ------------------ | ------------------------------------- | ------------------------- |
| Model              | MSI Prestige 15 A10SC                 |                           |
| CPU                | Intel i7-10710U                       |                           |
| IGPU               | Intel Graphics UHD 620                |                           |
| DGPU               | Nvidia GTX1650 Max-Q                  | **cannot be driven, SSDT is disabled**  |
| Display            | Sharp SHP14A1 15.6'     |                           |
| RAM                | Samsung DDR4 2666MHz 16GB x2          |                           |
| SSD1               | Western Digital SN730 512GB           |                           |
| SSD2               | Sabrent 2280 Rocket Q 2TB             | add-on                    |
| Audio              | Reltek ALC298                         |                           |
| Wireless           | Intel AX201 WIFI 6.                   |                           |
| Bluetooth          | Intel AX201 BT5.1                     |                           |
| Card Reader        | Realtek RTS5250 PCI-E                 | **cannot be driven**      |
| Fingerprint Reader | Synaptics WBDI                        | **cannot be driven**      |

- BIOS version: E16S3IMS.108

## prompt
- Turn off secure boot in the BIOS.
- Turn off CFG Lock in the BIOS (you need to enter the hidden menu, in the BIOS, first hold down ALT + right CTRL + right SHIFT, then press (FN) F2 to open the hidden menu), this item is in the Advanced->power of the hidden menu & Performance ->CPU-Power Management Control ->CPU lock Configuration ->CFG lock part.
- This example includes Clover and OC two boot, BOOTx64.efi in the Boot folder is OC (because OC must be booted from here); when adding OC and Clover to the EFI startup item, select /EFI as the boot file of OC /Boot/BOOTx64.efi, and Clover chooses /EFI/Clover/CLOVERX64.efi.
- Please regenerate the serial number, motherboard serial number, SmUUID and other information in config.plist by yourself. If Clover and OC need to be used together, then make sure that the information of the two is the same. ** Remember not to overwrite these information when upgrading config **.
- The AX201 network card needs to be connected by HeliPort in Apps, please unzip it and drag it into Apps for consumption!

## Additional fix
The earphone has a noise problem. Use ComboJack for optional switching. The terminal enters Attach/ComboJack/ and executes ./install.sh to install.
The sound card external amplifier under OC may have a silent startup or wake-up silent problem. If there is often no sound, you can try to install JackFix to solve the sound card restart problem. The terminal enters OC-Attach/JackFix/ and executes sudo ./install.command to install (the sound card node has been modified) .
The above two repairs require the VertStub.kext driver, Clover and OC have been added, and you must restart after installation.

## Untested components
Thunderbolt 3, Type-C port and video output is normal (HDMI and TB3 monitor), no other TB3 device on hand, unable to test

## Known issues
The bluetooth doesn't work.
The touchpad may occasionally fail (caused by the keyboard driver to prevent accidental touch, it can be restored by pressing Win+Prtscr twice)

The problem of Bluetooth loss is not visible in Windows after it is lost. It can be solved by shutting down and unplugging the power and then letting it stand for a few seconds and then turning it on again (hardware problem, normal power on and off will not occur)

## reference
- https://github.com/hla63/Msi-modern-15-Hackintosh
- https://github.com/KerKerOgh/MSI-Prestige-15-Hackintosh
- https://github.com/daliansky/XiaoXinPro-13-hackintosh
- https://github.com/daliansky/OC-little
- https://dortania.github.io/OpenCore-Install-Guide/

## drive
- https://github.com/acidanthera/OpenCorePkg
- https://github.com/acidanthera/Lilu
- https://github.com/acidanthera/VirtualSMC
- https://github.com/acidanthera/AppleALC
- https://github.com/acidanthera/WhateverGreen
- https://github.com/acidanthera/AirportBrcmFixup
- https://github.com/acidanthera/BrcmPatchRAM
- https://github.com/acidanthera/VoodooPS2
- https://github.com/VoodooI2C/VoodooI2C
- https://github.com/acidanthera/HibernationFixup
- https://github.com/OpenIntelWireless/itlwm
- https://github.com/OpenIntelWireless/IntelBluetoothFirmware
- https://github.com/1hbb/OpenIntelWireless-Factory
- https://github.com/al3xtjames/NoTouchID
- https://github.com/acidanthera/CPUFriend
- https://github.com/acidanthera/NVMeFix
- https://github.com/hackintosh-stuff/ComboJack
- https://github.com/fewtarius/jackfix
