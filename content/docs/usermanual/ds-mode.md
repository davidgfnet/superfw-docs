+++
title = "DS mode"
weight = 380
description = """
How to use Supercard and SuperFW in DS mode to play DS homebrew.
"""
+++

SuperFW has (limited) support for DS mode. That means you might use SuperFW to
play DS games on your NDS device. SuperFW is capable of launching an NDS
homebrew file located as `/BOOT.NDS` in the SD card and patching it with
the necessary _DLDI_ automatically. This enables many homebrew/game launchers.

Although we would recommend the usage of a Slot-1 cartridge these days (since
they are ubiquitous and very cheap) you can use your Slot-2 Supercard as well.
You will need a Passme/Passcard or a similar Slot-1 cartridge (or use some
patched firmware like [FlashMe](https://wiki.gbatemp.net/wiki/FlashMe)).

### Homebrew/Launcher setup

Since SuperFW acts as a mere NDS homebrew launcher, you will need to
install some software in your SD card. Here we list a few launchers that
work well and are useful. This list is merely informative and not exhaustive!

Launcher            | Purpose                 | Website
--------------------|-------------------------|--------------------------------------
TWiLight Menu++     | Homebrew/Games launcher | [github.com/DS-Homebrew/TWiLightMenu](https://github.com/DS-Homebrew/TWiLightMenu)
akmenu-next         | Homebrew/Games launcher | [github.com/coderkei/akmenu-next/](https://github.com/coderkei/akmenu-next)
GodMode9i           | Homebrew launcher/Tools | [github.com/DS-Homebrew/GodMode9i](https://github.com/DS-Homebrew/GodMode9i)
Homebrew Menu       | Homebrew launcher       | [devkitpro.org/wiki/Homebrew\_Menu](https://devkitpro.org/wiki/Homebrew_Menu)

In most cases the installation consists in downloading the `.nds` file and
renaming it to `BOOT.NDS` (and placing it at the root of the SD card).

In the case of TwilightMenu++/akmenu-next please use the _Flashcard_ variant and unzip the
release into the SD card. Only the `BOOT.NDS` file and the `_nds` directory are
actually needed for a successful installation on SuperFW.

### Usage

For users using a Passme/Passcard just boot your DS device and choose the DS game.
You should see the SuperFW logo in the upper screen and, after a few seconds, it should
load your Homebrew launcher of choice. In case of an error, you should see an
error message on the screen (see [boot error codes]({{< ref "/docs/usermanual/troubleshooting/#boot-error-codes" >}})).

If you use FlashMe, you might need to boot your DS pressing some sort of key
to force booting from Slot-2 (ie. Select or Select+Start depending on the version
or whether you have a Slot-1 cartridge also inserted). You should see the
SuperFW logo as well while it loads the launcher.

If the launcher does not load correctly or complains about the SD card format
or initialization, make sure that you are using the correct SD format. While
SuperFW supports exFAT/FAT32/FAT16 it could be that the launcher you are loading
has a much more limited support for these filesystems.


