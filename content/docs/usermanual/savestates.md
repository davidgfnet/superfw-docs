+++
title = "Savestates"
weight = 345
description = """
Details on what are savestates, how to use them and their limitations.
"""
+++

Savestates are snapshots of a running game. This is a very common feature
available in emulation so that users can save an exact state / point in time
of a given game and restore it later. This is very useful to practice levels
since you can skip parts of the game or restart at a much advantageous point.

The implementation that SuperFW uses has many limitations and, for some games,
might be unusable or plagued with issues, bugs and game corruption. The main
reason for this is that it is impossible to properly capture the state of
a running game on the GBA. There are several registers which are hidden (ie.
write only registers, shadow registers, implicit states, etc.) and cannot be
saved or properly restored. For this reason savestates can be considered
unreliable and only usable on a game-by-game basis.

### Savestate types

SuperFW offers savestates through its In-Game menu (_IGM_). When entering the
_IGM_ you will see the _Savestates_ option in the menu, which leads to a submenu
that allows users to create, delete and restore savestates.

There are two types of savestates:

 - In-memory savestate: It is stored in the Supercard SD-RAM and is
   _deleted_ on reboot / power loss. These are usually quick to create
   and restore and the available number of slots might depend on the
   amount of free SDRAM memory for a given game.
 - Persistent savestate: This types of states are loaded and written
   from/to SD card. They can be created and used at a much later point
   even after a device power off cycle. They are slow to create and restore
   but can be preserved across reboots. They are not limited to the
   amount of free memory available in the system.

Any in-memory savestate can be copied over another persistent savestate so
that it can be stored persistenly and be usable long-term.

### Savestate usage

The basic operations with savestates are loading and saving. Saving a savestate
will dump the current savestate (ie. game snapshot) into the desired memory
or disk slot. Loading does the opposite, loads the savestate to the current
ongoing game. Loading does not inmediately resume game play, but rather prepare
for it.

![Savestate menu](/images/screenshots/igm-savestates.png)

Savestates are not perfect due to the nature of the GBA hardware. Some registers
are unreadable (write-only) which results in incomplete savestates. It is common
to get freezes or some other game-breaking artifacts when restoring a savestate.
To minimize the risk we recommend to restore savestates in similiar settings
where they were taken. That is, when restoring a savestate try to get as close
as possible to the original scenario where the state was created. For instance:
restoring a savestate in the game title screen is much more likely to fail compared
to restoring it in the same level it was created.




