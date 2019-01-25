# playage notes

This repository is a loose collection of notes; as they become more precise, the repo will be more organised.

## Parts

A multiplayer client needs a bunch of features. Ideally they would be modular so that things can be swapped out, like the game being used or the matchmaking method:

 - Being able to start the game given player addresses and game parameters
 - Matchmaking, a process that produces player addresses and game parameters
 - A mod loader, primarily for UserPatch, WololoKingdoms and small trees
 - A mod repository
 - A spectator server

## Starting the game

I'll just start with a [DPRun](https://github.com/playage/dprun) module probably lol

## Matchmaking

For PlayAge I want this to be decentralised to the farthest possible extent, but we could start with a simpler matchmaking API that uses a central server.

## Mod loader

UserPatch has a CLI that can somehow be used without the UI.
WololoKingdoms can be installed programmatically with https://github.com/AoE2CommunityGitHub/WololoKingdoms/pull/23.

For other stuff, a DLL can be injected when the game boots.

## Mod repository

Just a way to download a tarball, probably.

For PlayAge, this could maybe be based on Dat, which has updates. datrs is not ready yet though.

## Spectator server

Not sure yet, should use libp2p relaying quite extensively I think so the host doesn't have to send out a million packets every move
