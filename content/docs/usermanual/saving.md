+++
title = "Saving your game"
weight = 330
description = """
Explains what kinds of savegames exist, how supercard handles them and what kinds of limitations and workarounds exist.
"""
+++

Many GBA games allow some sort of progress saving (even though around 500
games were released without any kind of memory and might employ other
techniques, such as password-based progress saving). These games use some
sort of memory storage (also called _cart backup_ in GBA jargon) to save
progress data. This storage is mostly emulated in Supercard to ensure the
cart can be cheaply built.

### Save memory types

There are several memory types and each game will only use one. They all
have different pros and cons, so game manufacturers picked them based on
the game needs.

#### SRAM / FRAM

This saving mechanism was very popular in the GameBoy / GB Color era. The
cart has an SRAM/FRAM chip that hols all the saved data. For SRAM chips,
the cart requires a coin battery, since SRAM is a volatile memory type. It
usually holds 32KiB of data.

Supercard is equiped with this memory type, so any games using this saving
mechanism will work out of the box without any kind of patching / hacking.
The downside of this memory type is that we need to write back its content
into the SD card, so it can hold data for more than one ROM (ie. if you
switch games by loading a different ROM).

Supercard will try to save a copy of the SRAM contents on reboot, so it
is a good idea to check your battery (otherwise you might lose your data).

#### EEPROM

Electrically erasable programmable read-only memory (EEPROM) is a memory
type that is rather slow, holds small amounts of data, but is not volatile
and will hold its contents even without a battery. It comes in two sizes
for most GBA games: 512 bytes or 8KiB.

Supercard doesn't have an EEPROM, so we emulate it by patching the ROM
before launching it. The patches can _convert_ this memory type into
SRAM (so they work on Supercard), or directly write the data into the
SD card (so called _DirectSaving_ mode).

#### Flash

Flash memory is very well known and commonly used these days. GBA games
typically ship 64KiB of flash, with notable exceptions (like Pokemon)
that use 128KiB. The GBA is not capable of addressing more than 64KiB,
so these games use a trick called _banking_. This memory is slower than
SRAM but can hold the data without any battery (just like a thumb drive).

Since Supercard also doesn't have any backup flash storage, we need to
emulate this using SRAM. We do this using patching.

### Saving mechanisms

In general we can use patching to convert Flash/EEPROM games into SRAM.
This is what the original Supercard firmware does (using its Windows
patcher tool). This approach works well for most games but has a few
caveats. For Flash/EEPROM games it is also possible a new mechanims
called _DirectSaving_ that was developed specifically for SuperFW. This
new system doesn't use any SRAM and reads and writes data directly to the
SD card.

#### Using SRAM as storage

This will simply use the Supercard built-in SRAM memory as savegame
storage. Any EEPROM/Flash games will be patched and _converted_ to use this
memory. There's a few pros and cons of this approach:

 - It works with most games (SRAM, Flash, EEPROM)
 - Requires a reboot to write the savegame to the SD card (or using the in-game menu to save).
 - Might require a working battery if saving on reboot.

This save type is only recommended for SRAM-based games. Ensure you reboot
your device when you are done playing to write your progress to the SD card.

![Chosing SRAM save type in the ROM launch pop up](/images/screenshots/menu-load-save-sram.png)

![Boot save message](/images/screenshots/reboot-save-msg.png)

When using the [In-game menu]({{< ref "docs/usermanual/igm.md" >}}) you can access
the _Save to SD card_ menu to immediately flush your SRAM to the SD card. There's
even an option to _Save and quit to firmware_ which will just save and immediately
reboot to the SuperFW menu. Should you want to *not* save your game (ie. you made
some sort of mistake, etc.) you can use the _Back to menu (skip save)_ option under
the _Reset_ menu. This option simply resets back to SuperFW but skips saving on
reboot.

![In-game menu savegame screen for SRAM-based saves](/images/screenshots/igm-save-sram.png)

##### Manually handling save games

When using SRAM as saving mechanism you can manage your savegames in a completely
manual way: no automatic loading nor saving. This allows you to load a `.sav`
from the SuperFW menu so the next ROM you launch uses that save data. Likewise
you will be able to manually write the SRAM data after you finish playing into
any `.sav` file.

To use this method, ensure that you choose _SRAM_ as save type and _Manual_
as both load and save mechanisms. SuperFW won't load nor store any SRAM data.

![Manual SRAM handling](/images/screenshots/igm-save-sram-manual.png)

You can also choose from a bunch of possibilities. For savegame load you can
specify:

 - Load: It loads the `.sav` file into SRAM before launching the ROM.
 - Clear: Will clear the SRAM, simulating a fresh new cartridge. It won't delete
   nor mangle the `.sav` file.
 - Manual: Does nothing at all. Assumes that the SRAM contents are manually managed
   by the user.

For saving your savegame you can choose between:

 - On reboot: Programs a file in the SD card (`.superfw/pending-save.txt` to be precise)
   and will save the SRAM contents during the next boot.
 - Manual: Does nothing. You are supposed to save your SRAM data manually.

In order to load or save the SRAM contents from/to a save file, you can use the
file browsers and locate the `.sav` file. Pressing _A_ on it will open the
savegame operation menu.

![Savefile management menu](/images/screenshots/sav-file-menu.png)

 - Write SRAM to sav, dumps the current SRAM contents to the .sav file.
 - Load sav to SRAM, performs the opposite and loads the savefile to SRAM.
 - Clear/Erase sav, will overwrite the savefile with an empty save file.


#### Using _DirectSaving_

The recommended save mechanism for Flash/EEPROM games. It will directly access
the SD card to read and write data. It saves your progress automatically just
like with an original cart. In general it is the simplest and safest method:

 - Reads and writes like a real cart.
 - Doesn't matter whether the Supercard has a working battery.
 - Doesn't require rebooting or manually saving.
 - Might be slightly slower than real carts.

![Direct Saving selected in the ROM loading menu](/images/screenshots/menu-load-save-ds.png)

This mechanism is not available if the game you are playing is an SRAM-based
game. You will need to [use SRAM]({{< ref "#using-sram-as-storage" >}}) saving
mechanism for these games. Also note that, since the loading/saving process is
completely automated you won't be able to use any advanced saving options like
the In-game menu or any kind of manual save management.


### Save game backups

Since things can go wrong sometimes (bad SD card, you drop your device, batteries
run out...) and we don't want you losing your precious save game file, SuperFW
has a backup mechanism.

![Backup count setting](/images/screenshots/menu-settings-backup.png)

In the _Settings menu_ you might specify a backup count greater than zero (setting
it to zero disables it altogether) to use this feature. SuperFW will keep a number
of savegame files as backup. For instance, when using 2 backups you might end up with
the following files: `mysave.sav`, `mysave.1.sav`, `mysave.2.sav`. The latest and
most recent save file is always the `.sav` file, and the previous copies are named
`.1`, `.2`, etc. When a new file is created, files are renamed and the oldest copy
(in this example `mysave.3.sav`) is deleted.




