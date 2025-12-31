+++
title = "Patches"
weight = 350
description = """
How patches work, why they are needed and how to generate and use them.
"""
+++

Supercard requires ROM patching to work. This involves modifying the original ROM
(this is done during ROM load, the ROMs are not modified on the SD card) to make
it work properly on the Supercard cartridge.

Other higher quality flashcarts might not require any patching (or less amount
of patching) since they contain certain hardware parts that emulate the original
GBA cart much better. Unfortunately this is not possible with Supercards and patching
is a requirement (except perhaps for Homebrew games).

Patch types
-----------

There's several patching processes that SuperFW does to GBA ROMs:

 - *WaitCNT patching* (also known as white-screen patching): These patches are required
   to make games work, due to the fact that Supercards ship slow memory. Faster
   games will fail without them (usually with a white screen during boot).
 - *Save patches*: Some games require patching their save functions so they can work.
   Supercard only supports SRAM-based games, so any other games need to be _converted_
   using these patches. See [save types]({{< ref "/docs/usermanual/saving/#save-memory-types" >}})
   if you want to learn more.
 - *IRQ handler* patches: These patches enable the [in-game menu]({{< ref "/docs/usermanual/igm/" >}})
   by modifying the game to display the menu when a key combo is pressed. These are optional
   and only really used when said menu is enabled.
 - *RTC* patches: Only used for a handful of games that require RTC emulation.

All these patches are generated and used toghether. When we talk about _patches_
we refer to a mixture of these types of patches.

Using and loading patches
-------------------------

Patches are needed to load a ROM in Supercard. On the original official Supercard
firmware no patching is performed at all and it relies on the user generating patches
on a computer using a specific software. This is not necessary in SuperFW (most of
the time). SuperFW supports the following patching approaches:

 - Patch database: a built-in database that contains patches for most GBA commercial
   games (official releases and such). The default patching method and by far the
   easiest one to use.
 - PatchEngine: a patch generator that runs on your GBA. It will process a ROM and
   generate patches for it. You only need to do this once, the patches are saved for
   later. Quite slow but useful if your game is not in the aforementioned database.
 - No patching: This option is provided to run Homebrew. Most homebrew software is
   capable of running on Supercard without any kind of patching.

When using the patch database, the loader UI will show whether the ROM has been found
in the database as well as some game information. The patches are indexed by game ID
and version, which could be ambiguous in some cases. This is particularly true for ROM
hacks and homebrew based on commercial games (ie. Pokemon Hacks/Homebrew).

{{< tip "warning" >}}

### Playing ROM hacks and/or forks

When playing derived games (non official forks or romhacks) SuperFW will
attempt to use the "official" patches, which doesn't work most of the time.
If the ROM hack is a full build (like may Pokemon romhacks) it is very likely
it won't work. For these games you should _generate new patches_. See below.

{{< /tip >}}


Patch generation
----------------

It is possible to generate your own patches (recommended when playing a non-official game)
by using the built-in PatchEngine or the web-based patch generator.

The built-in PatchEngine is quite slow and not very capable. It is fine for most
homebrew games, simple ROM hacks (ie. translations) or if your ROM is not in the
database. Run the patch generator and it will produce a patch file under the
 `/.superfw/patches` directory so that it can be reused in the future.

![Patch engine option in the ROM load menu](/images/screenshots/menu-load-patchengine.png)

Patches can also be generated using the web-based patch generator tool, which is
highly recommended. See the section below for more information.

Web-based patch generation tool
-------------------------------

You can generate patches (ie. for homebrew or ROM hacks) using the
[web-based patch generator tool](https://patchtool.superfw.davidgf.net/), which produces
higher quality patches (albeit not perfect).

To use it, simply pick the GBA ROM you want to process and press the button. It can
take some significant amount of time (up to 5 minutes, depending on the game and PC).
The tool will generate a `.patch` file you can download and place, as usual, in the
`/.superfw/patches` directory or next to the ROM file (must have the same name but
the `.patch` extension).

#### Using symbol (.sym) files

Some homebrew developers might provide a symbol file (a text file that has a `.sym`
extension usually) along with the ROM, that can be used to generate high quality patches
for SuperFW. You might need to ask around, since these files are not usually
distributed. Also note that these files are different for every ROM version
or revision (ie. you cannot use the sym file from another game or version).

To use this file, check out the _Advanced_ button where you can also load a sym
file along with the ROM, and click Generate.


