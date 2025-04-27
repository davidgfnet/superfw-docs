+++
title = "Emulators"
weight = 370
description = """
How to install and use emulators for GBA using SuperFW.
"""
+++

SuperFW supports certain console emulators for the GBA. In fact, it ships a
built-in copy of Jagoomba Color so that it can load and play GameBoy
and GameBoy Color ROMs out of the box.

For other emulators it is necessary to download and install them in the SD
card.

### Compatible emulators

Platform            | Emulator            | ROM file  | Website
--------------------|---------------------|-----------|--------------------------------------
Nintendo NES        | PocketNES           | `.nes`    | [dwedit.org/gba/pocketnes.php](https://www.dwedit.org/gba/pocketnes.php)
SG-1000             | SMS Advance         | `.sg`     | [archive.org/details/smsadvance-25-bin](https://archive.org/details/smsadvance-25-bin)
Sega Master System  | SMS Advance / DrSMS | `.sms`    | [www.webpersona.com/drsms](https://www.webpersona.com/drsms/)
Game Gear           | SMS Advance / DrSMS | `.gg`     |
NeoGeo Pocket Color | NGPGBA              | `.ngc`    | [github.com/FluBBaOfWard/NGPGBA](https://github.com/FluBBaOfWard/NGPGBA)
Watara Supervision  | WasabiGBA           | `.sv`     | [github.com/FluBBaOfWard/WasabiGBA](https://github.com/FluBBaOfWard/WasabiGBA)
Game Boy (Color)    | Goomba(Color)       | `.gb/gbc` | [dwedit.org/gba/goombacolor.php](https://www.dwedit.org/gba/goombacolor.php)

### Installation

Installing the emulators is as simple as downloading the release binary
(a .gba ROM file) and copying it to the `.superfw/emulators/` directory.
The files must have the right name so they can be found by SuperFW, namely:

Emulator      | File            | Download link                                      | Mirror
--------------|-----------------|----------------------------------------------------|----------------------------------------
PocketNES     | pocketnes.gba   | https://www.dwedit.org/gba/pocketnes.php           |
SMS Advance   | smsadvance.gba  | https://archive.org/download/smsadvance-25-bin ⚠️  | [v2.5 patched](/downloads/smsadvance-2.5-sc-patched.gba)
DrSMS         | drsms.gba       | https://www.webpersona.com/drsms/downloads.html ⚠️ | [v6.0 patched](/downloads/drsms-6.0-sc-patched.gba)
NGPGBA        | ngpgba.gba      | https://github.com/FluBBaOfWard/NGPGBA/releases    |
WasabiGBA     | wasabigba.gba   | https://github.com/FluBBaOfWard/WasabiGBA/releases |
Goomba        | gbc-emu.gba     | https://www.dwedit.org/gba/goombacolor.php         |

{{< tip "warning" >}}

Emulators must be compatible with Supercard. Some of them, like SMS Advance and
DrSMS are not compatible out of the box and they much be patched. You can download
patched versions from the mirror links in the above table.

{{< /tip >}}

If the emulator binary is not properly installed you might see an error message
when launching a ROM.

![Error message caused by a missing emulator binary](/images/screenshots/menu-load-emu-rom.png)

{{< tip "note" >}}

Note that there's no need to install Goomba (or any fork, GoombaColor, JagoombaColor ...)
to play GB/GBC games, SuperFW has a built-in JagoombaColor copy. However you are free
to install your favourite emulator/fork and it will take preference over the
built-in emulator.

{{< /tip >}}

### Playing ROMs

To use any of the emulators, simply browse the desired ROM (as you do with GBA ROMs)
and press _A_ to load it. SuperFW will load the emulator binary as well as the ROM
and launch it.

Most GBA emulators assume that the cartridge has SRAM storage, for the purposes of
storing savegames as well as savestates (if/whenever they are supported). SuperFW
will write the SRAM contents to a `.sav` file on reboot, to preserve its contents.


