+++
title = "Firmware update"
weight = 210
description = """
Explains how to flash a new update to the internal flash memory.
"""
+++

{{< tip "warning" >}}

## Warning

Updating the firmware has similar risks to a fresh install. Ensure you charge your device and don't drop it while flashing. You might always use a DS device to recover from a bad flash though!

{{< /tip >}}

## Installing a new release

You can update (or downgrade) your SuperFW at any time. Certain releases could result in incompatiblity issues with games, patches and savestates, ensure you read the release notes! Downgrading to beta releases is not recommended nor supported.

To update just follow the same steps as a fresh install:

  - Boot SuperFW as you usually do.
  - Navigate (using the _L_/_R_ shoulder buttons) to the _Info_ menu.
  - Press the key combo _Down_ + _B_ + _Start_, you will see the message _Flashing is enabled_ at the bottom.
  - Navigate back to the _File browser_ menu and locate the `.fw` file. Press the _A_ button to open it.
  - You should see the firmware image version you are about to update to. Ensure it is the intended one.
  - Proceed to flash with the key combo _L_ + _R_ + _Up_.

Ensure this process *is not interrupted* or the flash will be corrupted. It can take up to a couple of minutes to complete, should the process fail, you might try again. Once flashed, we recommend to restart your device immediately.

SuperFW might complain if you are attempting to flash the incorrect variant (ie. upgrading a Lite cart with an SD firmware).
Do not rely on this feature, always double check that you are using the right version.


## Flashing on DS

You might update your SuperFW firmware using the [DS flash tool](https://github.com/davidgfnet/superfw-nds-flasher-tool/releases), check the [Firmware flashing](flash.md) instructions.


## Downgrading / Restoring original firmware

If you made a backup before flashing SuperFW, you can restore it at any time.
If you don't have a proper backup, you might find a copy of the english firmware
on [archive.org](https://archive.org/details/supercard_ofw_185).

#### Downgrade process

Similarly to upgrading/installing your SuperFW you might use a GBA or an NDS.
Just rename the firmware to something like `original.fw` and proceed like a
regular upgrade. After a reboot you should boot into the original firmware.

Please note that the original firmware does not support SDHC cards nor exFAT,
so don't be surprised if you see an error screen after the reboot.

#### Downgrade issues

SuperFW might complain with a message like "Bad FW variant". This means that you are either using the wrong
image or that you are downgrading to an older version. Versions 0.18 and older do not support variant checks
and downgrade will always fail. The fix is easy: just boot the version you want to flash (you will need to
rename the firmware file to `superfw.gba`) and then flash it.

