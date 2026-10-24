# Dreamer Studio 2.0

**A portable Windows toolkit for the FlashForge Dreamer 3D printer.**

Dreamer Studio integrates firmware management, Cura configuration and local Wi-Fi printing in a single Windows x64 executable. Python is not required on the target PC.

> **Hardware-specific software.** Built for FlashForge Dreamer. Firmware flashing can render hardware inoperable if interrupted or used with incompatible devices. Check the printer model and prepare recovery options before proceeding.

## Features

- Install a customized Marlin 2.0.9.7 firmware build with Russian-language UI and a Wi-Fi menu.
- Restore the original FlashForge V2.15 firmware or included recovery images.
- Build a customized stock firmware image with selected menu and heating options.
- Automatically install a printer configuration for **Ultimaker Cura 5.13**.
- Use the integrated, **local-only** Cura HTTP-to-TCP bridge for the Dreamer's original Wi-Fi module (USR-C322).
- Transfer G-code to a FAT32 SD card with integrity checks before printing.
- Export included firmware images, Cura profiles, Marlin sources and offline documentation.

## Compatibility and requirements

| Item | Requirement |
| --- | --- |
| Printer | FlashForge Dreamer (other models are not supported) |
| Computer | Windows x64 |
| Firmware flashing | Compatible Dreamer USB bootloader driver |
| Cura integration | Cura 5.13 installed and launched at least once |
| Network printing | Compatible Marlin build, working printer Wi-Fi, FAT32 SD card |
| Printing profile | Left extruder T1 / ABS starting configuration; tune for your machine |

Cura and USB drivers **are not included** in the executable.

## Quick start

1. Download `DreamerStudio.exe` from [Releases](../../releases) **once a release has been published**.
2. Connect **one** FlashForge Dreamer by USB and close FlashPrint or other software using the connection.
3. Use **Install Marlin** only if you intend to replace the existing firmware. Follow the on-screen restart instructions and **never disconnect power while flashing**.
4. Launch Cura 5.13 once and close it; select **Install Cura profile** in Dreamer Studio.
5. On the printer, configure Wi-Fi and read its assigned IPv4 address.
6. Enter that address in Dreamer Studio, start the Wi-Fi bridge, and verify connectivity.
7. Insert a FAT32 SD card, open Cura, select the Dreamer printer and use **Print over network**.

For complete instructions, see the [Russian offline manual](docs/Dreamer-Studio-Manual-RU.html) or [README in Russian](README_RU.md).

## How network printing works

Cura connects to the local bridge on `127.0.0.1:18899`. The bridge communicates with the printer on `<printer-ip>:8899`. No cloud service is used. A complete G-code file is written to `/PIHCURA.GCO` on the printer's SD card and verified before printing begins. The bridge must be launched again after restarting the PC.

## Dual extruders

The Cura definition includes **T0 (right)** and **T1 (left)**. The provided tested starting configuration uses **T1 only**. Simply enabling T0 does not make dual-material printing safe or correctly configured; start/end G-code, tool changes, offsets and temperatures require individual testing.

## Test status and limitations

On one physical Dreamer, firmware installation, USB and Wi-Fi communication, SD card mounting, CRC rejection, and successful upload of a diagnostic file were verified. The diagnostic file completed without motion, extrusion or heating. **A full printed part using the latest Marlin update has not yet been validated.** Clean Windows systems without existing drivers, additional Wi-Fi hardware revisions, changing Wi-Fi credentials on real hardware and some recovery paths remain unverified.

## Downloads and source code

**This repository package currently contains documentation and GitHub metadata only.** The application executable and complete project sources must be added separately before announcing a software release. Do not present the repository as containing downloadable software until those files have been uploaded.

The embedded firmware is based on [moonglow/FlashForge_Marlin](https://github.com/moonglow/FlashForge_Marlin) and Marlin 2.0.9.7. If you distribute firmware binaries, provide the corresponding complete source code and license notices under the applicable GPL-3.0 terms. Review licenses of all other bundled components before publishing. See [LICENSES.md](LICENSES.md).

## Issues and contributions

Bug reports, improvement ideas and pull requests are welcome. Please include your printer variant, firmware/build version, Windows and Cura versions, what happened, and sanitized logs. **Never publish Wi-Fi passwords or other secrets.**
