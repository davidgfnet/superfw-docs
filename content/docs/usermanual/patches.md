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

Many ROM hacks and forks (like Pokemon homebrew and hacks) use the same Game ID
and version as the official release. This is an issue when using the Patch Database
which will load patches for the official release. For some ROM hacks this might be
fine (since they might not patch the base code but rather add more content) but
for modern forks this usually doesn't work at all (these games are built from
scratch using reversed source code and modern compilers).

When using ROM hacks we recommend to generate patches and *not* use the patch
database.

{{< /tip >}}


Patch generation
----------------

While it is possible to generate a _Patch Database_ yourself, we do not recommend it
since it is quite complex. In general, it is better to use patches for specific
games that require it, and use the built-in database for commercial games.

Patches for a specific ROM can be generated using the PatchEngine. The resulting
patch will be cached under the `/.superfw/patches` directory so that it can be
reused in the future.

![Patch engine option in the ROM load menu](/images/screenshots/menu-load-patchengine.png)

Patches might also be generated using the [web-based patch generator tool](https://patchtool.superfw.davidgf.net/)
and placed in the aforementioned cache directory or next to the ROM file
using the `.patch` extension.



