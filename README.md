# playage notes

This repository is a loose collection of notes; as they become more precise, the repo will be more organised.

## Parts

A multiplayer client needs a bunch of features. Ideally they would be modular so that things can be swapped out, like the game being used or the matchmaking method:

 - Being able to start the game given player addresses and game parameters
 - Matchmaking, a process that produces player addresses and game parameters
 - A mod loader, primarily for UserPatch, WololoKingdoms and small trees
 - Game patches (UP / WK)
 - A mod repository
 - A spectator server

### Starting the game

I'll just start with a [DPRun](https://github.com/playage/dprun) module probably lol

### Matchmaking

For PlayAge I want this to be decentralised to the farthest possible extent, but we could start with a simpler matchmaking API that uses a central server.

### Mod loader

For other stuff, a DLL can be injected when the game boots. Different game types can be started with `GAME=UPMODNAME` flag, for 'full conversion' like mods.

Graphic mods and such can be loaded in by a DLL fairly easily.
Custom language strings from multiple mods can be loaded using aoc-language-ini.

Random maps and scenarios could just be downloaded into the game folder, but it might also be nice to have a separate entry in the random maps list on the game setup screen for that stuff. Then when starting a game, the DLL mods could auto-install the mod containing those maps, bypassing AoC's slow builtin file sharing.

### Game patches

UserPatch can be installed programmatically with some command line flags. The `-i` flag does a UI-less installation. `-f` can be used to set config fields. 1 to enable, 0 to disable.

```
SetupAoC.exe -i -f:1010101010101010
```

WololoKingdoms can be installed programmatically with https://github.com/AoE2CommunityGitHub/WololoKingdoms/pull/23.

### Mod repository

Just a way to download a tarball, probably.

For PlayAge, this could maybe be based on Dat, which has updates. datrs is not ready yet though.

### Spectator server

Not sure yet, should use libp2p relaying quite extensively I think so the host doesn't have to send out a million packets every move
