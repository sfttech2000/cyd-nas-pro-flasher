# CYD-NAS Pro web installer

Installs CYD-NAS Pro on an ESP32-2432S028 (CYD) from a browser over USB: computers with Chrome or
Edge (Web Serial), Android phones with Chrome and an OTG cable (WebUSB, small CH340 driver).

firmware/boot.bin goes to 0x0 and firmware/app.bin to 0xe000, so the settings (NVS 0x9000-0xDFFF,
including the unlock key) are kept; "erase" wipes the whole chip first. Installs go through this
page only (no one-file image), so each one is counted.

The Pro firmware is locked per board: it shows a machine code (NAS-<chip id>) and runs once an
unlock key from the shop is entered on its web page. The free version is CYD-NAS Lite at
https://sfttech2000.github.io/cyd-nas-flasher/.

Binaries come from `pio run -e cyd` and `python scripts/make_flasher_bins.py <this repo>/firmware`
in the CYD-NAS project (drop full.bin). Screenshots in img/ were captured from the device over USB
(`scripts/screenshot.py`).

Uses esptool-js 0.6.1 (Apache-2.0), vendored in mobile/esptool-js/ with its licence.
Made by tee & claude.
