+++
title = "Getting started"
weight = 320
description = """
Initial configuration and setup for a fresh SuperFW install.
"""
+++

After installing SuperFW there's a bunch of configuration and preparation
steps you can follow to get the most out of your Supercard. Follow this
guide to customize and setup your card for your needs.

### UI configuration

Using the _L_ and _R_ shoulder buttons you can switch between different
menus in the main UI. As a first step, navigate to the UI settings menu
and configure your preferred language, as well as UI color and text speed.
You can disable the _Recent ROMs_ if you don't wish to record nor display
the recently played ROMs.

![UI settings screenshot](/images/screenshots/menu-ui-settings.png)

### Preparing your SD card

SuperFW is relatively easy to use and requires no files on your SD card except
for the (original and unpatched) game ROMs. Simply ensure that you format your
SD card using _FAT16_, _FAT32_ or _exFAT_ and copy your files in any directory
you prefer. Any necessary output directories (usually under `.superfw/`) will
be automatically created when needed if you don't create them in advance.

Some features require adding some extra files to the SD card. You can add
[cheats]({{< ref "/docs/usermanual/cheats.md" >}}) and
[emulators]({{< ref "/docs/usermanual/emulators.md" >}}) by
downloading the necessary files and copying them to the appropriate directory
in the SD card. [Patches]({{< ref "/docs/usermanual/patches.md" >}}) can also
be manually added to the SD card, this might be useful if the built-in patches
or _PatchEngine_ are not good enough for certain games.

### Cartridge health test

It would be advisable to ensure that your Supercard cart is in good condition,
to avoid some of the most common pitfalls when using it. You can perform some
sanity tests by navigating to the _Tools_ menu. It is recommended to run an
SDRAM, SRAM and battery test. The first two should always pass without issue,
otherwise it means that the cart could be defective. The battery test can
fail if your battery is dry, see
[the troubleshooting manual entry]({{< ref "/docs/usermanual/troubleshooting.md#bad-cart-battery" >}})
for more information on this specific issue.

### Loading a ROM

The first menu (or the second, if you enabled the _Recent ROMs_ menu) is the ROM
browser. You can use it to find ROMs in the SD card. Once you have located the
desired ROM just select it with the _A_ button. The ROMs should have the `.gba`
extension to be recognized as GBA ROMs.

![Screenshot of the ROM browser](/images/screenshots/menu-rom-browser.png)

The ROM loader a loader menu will pop up. This provides information about the
ROM, as long as there's an entry for it in the _Built-in Database_. In general,
particularly if you play an official commercial game, you can just launch the game
right away with the default settings.

![ROM load pop-up dialog](/images/screenshots/menu-load-rom.png)

Using the shoulder buttons _L_ and _R_ you can move to the different loading
configuration submenus. These allow you to tweak things such as savegame
configuration, patching preferences and other advanced functions.

Once you are done playing, we recommend rebooting your device, to ensure
that any savegame is properly flushed to the SD card. This is only necessary
when the game uses _SRAM_ as save memory (as shown in the load menu).
In that case you might see a message during the next boot.

