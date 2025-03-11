+++
title = "In-game menu"
weight = 330
description = """
How to enable and use the in-game menu.
"""
+++

SuperFW features an _In-game menu_ (_IGM_ for short) that can be triggered
during game play. This menu features some options such as reset, saving game,
cheats, etc.

The menu is not available for every game and can mess up the game (particularly
the graphics) when used, it really depends on the game and when it is used.

### Configuration

In the _Settings_ menu it is possible to configure the key combo used to
trigger the menu. It is also possible to configure the default loading
behaviour so that the _IGM_ is enabled or disabled by default, in the
ROM loader menu.

![IGM trigger key settings](/images/screenshots/menu-settings-igm-hotkey.png)

Some games, particularly those big ones (32MiB ROMs), won't support the
_IGM_ and the option won't be selectable in the ROM loader menu. The menu
requires around 1MiB of _free ROM space_, which is something that 32MiB ROMs
don't usually have.

### Usage

During gameplay you might press the aforementioned key combo to trigger
the _IGM_. A menu will be displayed with a bunch of options, navigate them
similarly to the main menu.

![In-game menu main screen screenshot](/images/screenshots/igm-main.png)

#### Reset

It is possible to reset the current game, but also to reset and go back to the
SuperFW main menu (_reset to firmware_). Note that resetting to firmware will
load whatever firmware is flashed and configured in your Supercard. Should you
launch SuperFW from another firmware (perhaps the official firmware) you will
go back to this firmware and not SuperFW.

![IGM reset submenu](/images/screenshots/igm-reset-menu.png)

When the currently loaded game uses SRAM saves and if you have choosen to
automatically save the game on reboot, reseting back to firmware will trigger
a save game. If you wished to avoid this, you can select the _skip save_ option.
This option will skip save on reset, but still allow you to manually save once
in the main menu if you wish so (ie. using [manual saving]({{< ref "saving.md#manually-handling-save-games" >}}).

#### Save game

This menu is only available if the save type is configured as _SRAM_. You can
write the current SRAM save game (useful to ensure you do not lose progress
if you have a bad battery). If you configured SuperFW to create save backups
you can save doing so or just ovewriting the last save file (and not backing
it up).

![In-game menu savegame screen for SRAM-based saves](/images/screenshots/igm-save-sram.png)

A convenient option also exists to save and return to firmware. This option
will save your _SRAM_ and reboot to the main menu, skipping the save-on-reboot.

#### Savestates

This submenu allows for savestate loading and saving. Savestates can be used
to capture a snapshot of a running game to restore it later. For more details
on how to use this, please check the [Savestates manual]({{< ref "savestates.md" >}}).

#### RTC menu

On games that support RTC, this allows you to configure the date and time.
Please note that there is no hardware clock support. The time won't advance
on its own, if you want to simulate the passage of time, you will have to update
the RTC clock value manually (ideally periodically).

#### Cheats

This submenu controls cheat codes, please check the
[documentation on Cheats]({{< ref "/docs/usermanual/cheats.md" >}}) for more information.
The menu entry is disabled if cheats were not enabled or no cheats were loaded.

### Caveats and known issues

The _IGM_ can be used to save the current game to the SD card. However, when
used alongside with [Direct Saving]({{< ref "/docs/usermanual/saving/#using-_directsaving_" >}}),
the menu won't be able to perform any saving operations. In that case saving
is handled automatically from/to the SD card and the _IGM_ cannot interfere
with the process.

![In-game menu warning screen during DirectSave](/images/screenshots/igm-warn-save.png)

If the _IGM_ key combo is triggered during a _Direct Saving_ read/write
operation you will be greeted with a message and won't be able to use the
menu until the operation is completed. Please avoid using the _IGM_ when
the game is loading or saving (saving points are usually obvious, but loading
is usually not transparent to the user, so you might encounter this warning
during cut scenes, loading screens or black/white transition screens).

The menu might have disabled options and submenus. This is normal depending
on the game loaded and the configuration selected (save type, cheats available, etc).

