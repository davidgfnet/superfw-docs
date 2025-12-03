+++
title = "Firmware flashing"
weight = 200
description = """
Explains how to flash the firmware to the internal flash memory.
"""
+++

{{< tip "warning" >}}

## Warning

Installing the SuperFW firmware on the internal flash will erase the original firmware.
Create a backup if you want to be able to restore it later. You have been warned!

The process can be performed both on a GBA or a DS device. When using a GBA
there's a small risk that the flashing process fails or is interrupted causing
the cart to brick. In that case, the cart might not boot anymore (you now have a
nice paperweight). This can be easily recovered using a DS console and a Slot-1 flashcart.

{{< /tip >}}

## No installation

You might use SuperFW without installing it. Just launch it from any other homebrew / menu / firmware of your choice and use it.

{{< tip >}}
This approach is called _chainloading_ and has several disadvantages: you
might not be able to use exFAT and/or SDHC depending on the installed
firmware. SuperFW supports old and new cards, low and high capacity, as
well as modern filesystems like exFAT with proper Unicode support.
{{< /tip >}}

## Flashing on GBA (or DS in GBA mode)

You can flash SuperFW using the original firmware and/or any other custom
firmware like SCFW. As long as the firmware is capable of launching homebrew
you can launch SuperFW and use it to flash itself.

#### Prerequisites

You will need the following:

  - GBA or DS device
  - Supercard cart
  - An non-HC SD card (those older low capacity cards, SDHC cards are not supported by the original firmware!)
  - The firmware (check the [download page]({{< ref "/docs/download/download.md" >}}))

#### Identify your cartridge

If you are unsure what kind of Supercard cartridge you have, please read carefully.

 - If the device has the word "rumble" on the label, this is incompatible with SuperFW.
 - If it's an NDS-lite sized cart, it's the "Lite" variant (be careful not to confuse it with a Lite Rumble!)
 - If it uses Compact Flash carts, it's a SuperCard CF, incompatible with SuperFW.
 - Otherwise (that is, no Rumble, no CF, and no Lite) it's a Supercard SD (either full size SD, or MiniSD or MicroSD).

  You can check the following image to better identify your cart.
  Compatible carts are displayed in green, incompatible ones in red.
  (Click to enlarge)

  [![Supercard cart collection](/images/cart_overview_thumb.jpg)](/images/cart_overview.jpg)

{{< tip "warning" >}}

Flashing the wrong firmware will brick your cart. Make sure to use the right one
and, in doubt, test the firmware before flashing it.
You can always use an NDS console to unbrick any flash cart.

{{< /tip >}}


#### Preparation

The SD card must be formated using FAT16 or FAT32 (exFAT is *not* compatible with the original firmware). Download the `superfw-sd.fw` (if you have a Supercard SD) or `superfw-lite.fw` (if you have a Supercard Lite) file and place it in the SD card. Create a copy of this file and rename it to `superfw.gba`.

#### Install

  - Boot the Supercard firmware and load the `superfw.gba` ROM. It will boot SuperFW.
  - (Optional) Backup your current firmware using the _Tools_ menu. Select _Flash backup_ and backup the `.superfw/flash_backup-*.bin` file to your PC.
  - Navigate (using the _L_/_R_ shoulder buttons) to the _Info_ menu (the rightmost one).
  - Press the key combo _Down_ + _B_ + _Start_, you will see the message _Flashing is enabled_ at the bottom.
  - Navigate back to the _File browser_ menu and locate the `superfw-sd.fw`/`superfw-lite.fw` file. Press the _A_ button to open it.
  - You will see a pop up menu, proceed to flash with the key combo _L_ + _R_ + _Up_.

It is very important that this process *is not interrupted* or the flash will be corrupted. It can take up to a couple of minutes to complete, you will see the info message updated on each flashing step (_Checking_, _Erasing_, _Flashing_, _Verifying_). Should the process fail, you might try again. Once flashed, shutdown and restart your device, it should boot SuperFW.


## Flashing on DS

You can use a DS device to flash the firmware to the Supercard by using the Slot 2. This method is very safe and can unbrick any cart, since the flasher tool is loaded via Slot 1 (DS cart).

#### Prerequisites

You will need the following:

  - DS device
  - Supercard cart
  - A Slot-1 cartridge (any cheap DS cart will do, like any R4 clone/derivative)
  - An SD card (any card that works on your Slot-1 cart, you don't need an SD card for the Supercard for this operation)
  - The firmware (check the [download page]({{< ref "/docs/download/download.md" >}}))
  - The DS flash tool ([download the latest release](https://github.com/davidgfnet/superfw-nds-flasher-tool/releases))

#### Preparation

Copy both the SuperFW firmware file (`superfw-sd.fw` or `superfw-lite.fw`) and the DS flash tool (`superfw-flasher.nds`) to the SD card. Insert it in your Slot-1 cartridge. Load both carts in their respective slots and boot your DS in DS-mode.

⚠️ Please ensure that you have a *compatible cart* and you are flashing *the correct firmware*.

#### Install

  - Boot the `superfw-flasher.nds` flash tool using your Slot-1 cart.
  - Select the correct flash cart type (ie. Lite, SD, etc).
  - (Optional) Backup your current/original firmware. Use the _Dump flash_ option. Backup `sc_flash_dump.bin` to your PC.
  - Use the _Write flash_ option and locate the SuperFW image `superfw-sd.fw`/`superfw-lite.fw`. Select it using _A_ button.
  - Press the key combo _L_ + _R_ + _A_ to start flashing. Do not interrupt this process!

You might reboot into GBA mode to verifiy that the new firmware is now working.

## Flashing back to the official firmware

We recommend making a backup before installing SuperFW so you can always go back.

Check [the downgrade notes]({{< ref "/docs/install/upgrade/#downgrading--restoring-original-firmware" >}})
for guidance on downgrading/restoring.

