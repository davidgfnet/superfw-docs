+++
title = "Troubleshooting"
weight = 390
description = """
Common issues and how to solve them.
"""
+++

Supercards are of questionable quality and are known to have some issues
and suffer from known hardware issues. Please ensure you test your cart
(i.e. battery is healthy) and are aware of its limitations.

### Known issues

This is a non-exhaustive list of known issues that might not have a fix:

 - General slowness while playing for some games. See the explanation
   [below]({{< ref "#slowness-while-playing" >}})
 - Non-working games: ie. NES Classics / Famicom Mini collection.
 - Gameboy/Color game issues: These games use an emulator, see the
   [full explanation](#game-boy--color-rom-issues).
 - The In-game menu doesn't work properly or is not available for some
   games. This is unfortunately the case for some games.

Some issues can be fixed or improved on a game-by-game basis, however
do not file bugs for known issues. There's usually an open bug for it
already.

### ROM issues

#### Boot issues (white/black screen)

Supercard has slow memory and requires certain patches to work with this
memory type. If these patches are not correctly generated, the game will
most likely crash with a white or black screen, usually during boot.

Ensure you are using the correct patches (for commercial games use the
_Built-in database_). The patches are auto-generated, so it is possible
that they contain bugs.

#### Slowness while playing

Since Supercard has a slow cart memory, some games designed for faster
carts might suffer from slowness. This cannot usually be fixed. However
some games can suffer from additional slowdowns when using the _In-game menu_.
You can try disabling it and checking if this improves the game speed.

#### Corrupted ROMs and random glitches

SuperFW does not validate ROM checksums (nor SD card checksums) when loading
files from the SD card. This is done on purpose, since doing so would
be painfully slow. In some cases the loaded ROM could not work, have glitches,
etc. If this only happens occasionally it might be that your cart is not
properly inserted, or the slot is dirty. It can also be due to low-quality
SD cards, check if another card works better. Some GBA models are known to
have issues even with the original firmware (usually the SP or NDS devices
work better).

#### Game boy / Color ROM issues

Using a GBA cartridge it is not possible to play GB/C games. SuperFW uses
an emulator (jagoombacolor) to play these games. Any issues with particular
games are most likely an emulator issue. You can try using a better emulator
or purchase a Gameboy/Color cartridge (only works on GBA, won't work in NDS).

### Save game issues

There are several issues that can affect your ability to save games. Ensure
you check which kind of saving type you are using before troubleshooting.

#### Bad cart battery

If you use _SRAM_ games (or _SRAM_ saving type in general) you might need
to have a working battery. This is necessary if you save on reboot.

You can verify your battery in the _Tools_ menu and running a battery test.
Run the test and follow the instructions.

If your battery is dead, you won't be able to save on reboot. You can instead
use _Direct Saving_ with games that allow it. For _SRAM_ games you can select
_Manual_ as saving method and then use the [In-game menu]({{< ref "/docs/usermanual/igm.md" >}}) 
to manually save the game while playing.

#### Corrupted save game

Some games might complain about corrupted games while loading. This could be
caused by a corrupted save (that is, saving corrupted your game for some reason)
or due to an issue loading the save game. You can test whether your save file is
corrupt by loading it in your PC and using an emulator.

Make sure that you select the _Load_ option in the _Savegame load_ option in the
_Savegame options_ menu, when loading a game. If the option is not available, it
means that SuperFW was not able to find a save game (`.sav` file). Ensure that
the file is in the right directory (can be configured in the _Settings_ menu).

If your save games are corrupted, you will need to identify why that happens. If
you use _Direct Saving_ it is possible that your SD card is not having a good time,
that happens with low quality or older cards. Please test another card to ensure
this is not a bad card.

Corrupted SRAM save games can happen for many reasons: bad cart battery (see above),
using SRAM with games that require 128KiB flash (use _Direct Saving_ for these),
a corrupted SRAM chip (you can check yours in the _Tools_ menu, etc.

### SD card issues

Some SD cards are known to cause issues, usually cards of questionable quality.
It is also common to encounter issues related to filesystem corruption and
format. We encourage users to back up their savegames and other valuable files
periodically, since SD card corruption happens unfortunately more frequently
than with hard drives.

#### Boot error codes

During boot the SD card partition will be mounted and accessed. If this process
fails an error will be displayed.

*Fatal SD card init err*

Error name             | Number | Description
-----------------------|--------|---------------------------------------------------
`SD_ERR_NO_STARTUP`    |   1    | SD card failed reset sequence. Damaged SD card?
`SD_ERR_BAD_IDENT`     |   2    | Card identification failed. Incompatible SD card?
`SD_ERR_BAD_INIT`      |   3    | Failed initialization sequence (CID/RCA registers).
`SD_ERR_BAD_CAP`       |   4    | Could not read card capabilities (CSD register).
`SD_ERR_BAD_MODEXCH`   |   5    | Could not change SD card mode.
`SD_ERR_BAD_BUSSEL`    |   6    | Failed to configure the SD card.

*Cannot mount FATfs*

Error name             | Number | Description
-----------------------|--------|---------------------------------------------------
`FR_DISK_ERR`          |   1    | There was an SD read error (or timeout).
`FR_NOT_READY`         |   3    | SD card was not found.
`FR_NO_FILESYSTEM`     |  13    | Could not find a valid filesystem in the card.

*Cannot load BOOT.NDS*

Error name             | Number | Description
-----------------------|--------|---------------------------------------------------
`ERR_FILE_ACCESS`      |   1    | Could not open/read the NDS file.
`ERR_NDS_TOO_BIG`      |   2    | NDS sections exceed the RAM size or the loader capabilities.
`ERR_NDS_BAD_ADDRS`    |   3    | The NDS load addresses are invalid.
`ERR_NDS_BAD_ENTRYP`   |   4    | The NDS entrypoints are invalid.
`ERR_NDS_BADHEADER`    |   5    | The NDS header is invalid.

