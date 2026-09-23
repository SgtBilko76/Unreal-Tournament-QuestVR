# Unreal Tournament VR — a Meta Quest & PICO port of UT99

A standalone VR port of **Unreal Tournament (UT99)** for Meta Quest 2 / Pro / 3 / 3S (developed
and tested on Quest 3) and, experimentally, PICO 4 / Neo 3 — built on [Surreal Engine](https://github.com/dpjudas/SurrealEngine),
a from-scratch reimplementation of Unreal Engine 1, with an OpenXR/Vulkan stereo renderer.

The same engine also runs Unreal Gold in VR — see the sister repository
[Unreal-Gold-QuestVR](https://github.com/SgtBilko76/Unreal-Gold-QuestVR); both apps install side
by side. More PortRoyale ports at [portroyale.online](https://portroyale.online).

This repository contains **no copyrighted game content** — only engine code. You provide your
own copy of the game (see below for a free, legal source).

## Features

* Native OpenXR rendering (72 Hz, per-eye asymmetric projection), snap turning, stick locomotion
* Weapons held in and aimed with the right controller, with a controller-ray crosshair —
  including UT's dual Enforcers (second pistol in the left hand)
* Sniper rifle zoom shown as a scope screen above the gun, aimed with the hand
* Redeemer guided shell steered with the right controller
* World-anchored curved menu panel operated by pointing and clicking with the controller
* VR comfort: no view bob, no double-tap dodge; recenter on the Meta / Home button
* Save settings and botmatch play; deathmatch and botmatches work well
* Installs side by side with [Unreal Gold VR](https://github.com/SgtBilko76/Unreal-Gold-QuestVR) (separate app and data folder)
* Experimental PICO 4 / Neo 3 support — one APK for both makes, **untested on PICO hardware**;
  reports are very welcome

## Getting the game (legal, free)

Unreal Tournament is available for free from OldUnreal:

**https://www.oldunreal.com/downloads/unrealtournament/full-game-installers/**

Run the installer on a PC (Linux/macOS installers are on OldUnreal's GitHub releases, linked
from that page). The installer patches the game to the current OldUnreal 469 version — this
port detects and runs it (tested with 469e); the original 436 also works.

## Installing on the headset

1. Install the APK from the [Releases](../../releases) page (sideload with `adb install -r` or
   [SideQuest](https://sidequestvr.com/setup-howto); developer mode required). SideQuest is a
   Quest tool — on PICO, sideload with adb.
2. Copy the game folders to `/sdcard/SurrealEngineUT/` on the headset so you have:

       /sdcard/SurrealEngineUT/System   Maps   Textures   Sounds   Music   Help

   e.g. `adb push "C:\Games\UnrealTournament\System" /sdcard/SurrealEngineUT/System` — and so on
   for each folder. Leave out your PC's `UnrealTournament.ini` / `User.ini`; the app keeps its
   own settings.
3. Launch **Unreal Tournament VR** from the Unknown Sources section of the library and grant "All files access"
   when asked.

## Controls

| Input | Action |
| --- | --- |
| Left stick | Move (direction follows snap-turns) |
| Right stick left/right | Snap-turn 45° |
| Right stick up/down | Next / previous weapon |
| Right trigger | Fire (aimed where the crosshair on the gun's ray sits) |
| Right grip | Alt-fire |
| Right A | Enter — activate selected inventory item |
| Right B | F2 key |
| Left trigger | Jump |
| Left X | ] — select next inventory item |
| Left grip (hold) | Crouch |
| Left Y | Scoreboard |
| Left menu button | Open / close the game menu |
| Meta / Home button long-press | Recenter |
| Sniper zoom | Scope screen above the gun; aim with the hand |
| Redeemer guided shell | Steered with the right controller |

## Known limitations (engine)

* Bot AI is only partially implemented in Surreal Engine.
* No dynamic lighting; some movers/semisolid brushes behave oddly.
* No networking/multiplayer.
* PICO support is brand new and untested on hardware.

## Building

See [Docs/AndroidBeta.md](Docs/AndroidBeta.md) for the Quest APK packaging, and
[Docs/Building.md](Docs/Building.md) for desktop builds. In short: Android SDK + NDK 27,
Gradle 8.x, `gradle assembleRelease` in `Projects/Android`.

## Credits and license

* [Surreal Engine](https://github.com/dpjudas/SurrealEngine) by dpjudas and contributors — the
  Unreal Engine 1 reimplementation this port is built on. See [LICENSE.md](LICENSE.md).
* VR/OpenXR approach inspired by [Team Beef](https://www.patreon.com/teambeef)'s Quest ports.
* Unreal Tournament is a trademark of Epic Games, Inc. This project is not affiliated with
  Epic Games. No game content is distributed here.
