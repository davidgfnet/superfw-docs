+++
title = "Cheats"
weight = 340
description = """
How to load and use cheat codes in SuperFW.
"""
+++

SuperFW supports cheat codes that can be enabled and disabled while playing.
At the moment only Code Breaker cheats are supported, and only a subset of
them. Using cheat codes might also result in some slowdowns in the gameplay,
since they are usually executed once per frame taking some CPU cycles.

### Install cheats

Cheat codes are shipped in text files (.cht files) and placed under the
`.superfw/cheats` directory in the SD card. The cheat files are named after
the game code and version.

You might download SuperFW compatible cheats ready to use from the
[SuperFW cheat repository](https://github.com/davidgfnet/superfw-cheats/releases)

### Using cheat codes

In order to use cheats, ensure that they are enabled in the _Settings_ menu.
You will need to ensure that you enabled the _In-game menu_ when launching
your ROM.

When playing the ROM, press the key combo to trigger the _In-game menu_
(whatever key combo you configured, the default is _L_ + _R_ + _Start_).
You can now navigate to the _Cheats_ menu (if the option is disabled it
means that no cheats could be loaded, either not found or disabled).

![Cheats UI in the In-game menu](/images/screenshots/igm-cheats-example.png)

For each cheat code, you will see a title or description and you can
press _A_ button to enable or disable it. Codes are active until you
disable them, so make sure to disable codes once you don't need them any more.

{{< tip "warning" >}}

## Warning

Using cheat codes (particularly cheat codes of questionable quality)
can crash your game, corrupt your saves or cause weird undesired behaviour.
This is due to the fact that cheat codes can read and write any memory
address.

This can happen if you use cheat codes for the wrong game (some games
have regional differences and ROMs can be very different across versions).

{{< /tip >}}
