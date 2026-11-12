# Cascadia Falling

A custom map and mission for [Nuclear Option](https://store.steampowered.com/app/2168680/Nuclear_Option/),
work in progress.

**Map:** a 400 km box of the Pacific Northwest, Vancouver to Yakima, built from real elevation, land cover
and OpenStreetMap data: sixteen airfields laid out as they really are, seventeen FOBs, seven helipads, three
naval bases, eight mountain radar sites and four nuclear silo fields. Loads through BatongMaster's
[NOCustomMaps](https://github.com/BatongMaster/NOCustomMaps) plugin.

**Mission:** PALA attacks Puget Sound from the Pacific and the straits of Juan de Fuca and Georgia; BDF
defends from Tacoma. PvP, both sides can be joined. A 7.5-hour war (the clock runs at 10x): PALA's carrier
and surface groups start far out at sea and the first reach Port Townsend after about two hours, while air
raids, heli-lifts, landings and columns work the flanks. Every BDF site is a PALA objective. BDF wins by
holding JBLM, Fort Lewis FOB, the Port of Tacoma and the Narrows until T+450, or by sinking all five PALA
Hyperions and then destroying the PALA Strategic HQ that appears on Texada Island.

## Prerequisites

1. **BepInEx 5** (the Nuclear Option Mod Manager installs it for you).
2. **NOCustomMaps 1.4.2 or newer** (the 1.4.0 build stopped working with the 2026-10-30 game update, 0.34.6).
3. **The Cascadia map**, build key `cm.cascadia.d7766d89`. The host and every player need the same build.

**Hosts using Wing Command:** set `AiSharpTurns = false` in `BepInEx\config\com.marci.wingcommand.cfg` before
you host. With it on, most AI take-offs end in a crash (in our tests 58 of 183 AI take-offs crashed within
a minute with it on, 0 of 67 with it off).

## Optional and recommended mods

| Mod | Who needs it | What it does | Download |
|---|---|---|---|
| NOAIFlightFix | recommended, host only | keeps the AI's climb-outs after take-off and its dives toward low targets in check | [releases](https://github.com/netmaster296/NOAIFlightFix/releases) |
| NOLakeIndex | recommended, everyone | a fast lake and river lookup for NOCustomMaps, for a better frame rate on this map | [releases](https://github.com/netmaster296/NOLakeIndex/releases) |
| NOAirbaseLightsFix | optional | keeps the donor airbase's runway lights off on custom maps | [releases](https://github.com/netmaster296/NOAirbaseLightsFix/releases) |
| NOCloudDeck | optional, visual and local only | a Pacific Northwest rain day: cloud deck, rain and haze | [releases](https://github.com/netmaster296/NOCloudDeck/releases) |
| NOGridLetters | optional | makes the grid readable on a map with 40 rows (rows past Z read A*, B*..., zoomed-in columns read 12-3) | [releases](https://github.com/netmaster296/NOGridLetters/releases) |

Each is a DLL for `BepInEx\plugins\`, or install them with the Nuclear Option Mod Manager where they are listed.

NOCloudDeck is optional, but in PvP its users see much less far than players without it (in this weather about
5-12 km under the cloud and 0.5 km inside it, against about 50 km in stock), so agree on it before a PvP match.

## Install

**Easiest:** in the [Nuclear Option Mod Manager](https://github.com/Combat787/NuclearOptionModManager)
search for "Cascadia Falling" and install it; it pulls in NOCustomMaps and NOGridLetters and installs the map
(about 1.6 GB). Then subscribe to the
[Cascadia Falling mission on the Steam Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=3825716792);
it appears in the game's mission list under Workshop and updates itself.

**By hand:**

1. Download `cascadia-0.1.1.zip` from the [latest release](https://github.com/netmaster296/CascadiaFalling/releases)
   and put `cascadia-0.1.1.nomapz` into `BepInEx\plugins\NOCustomMaps\maps\` in your game folder
   (`CustomMaps\` under `%USERPROFILE%\AppData\LocalLow\Shockfront\NuclearOption\` works too).
2. Subscribe to the [Workshop mission](https://steamcommunity.com/sharedfiles/filedetails/?id=3825716792), or
   copy this repository's `Missions\Cascadia Falling` folder to
   `%USERPROFILE%\AppData\LocalLow\Shockfront\NuclearOption\Missions\`.
3. Optional: the mods above, each DLL into `BepInEx\plugins\`.
4. Start the game and pick Cascadia Falling. The first minute is slow while the map streams in.

The `.nomapz` is the map bundle compressed in NOCustomMaps' own packed form; the plugin reads it directly and
the map key is unchanged. Delete any earlier Cascadia build you may have (`cm.cascadia.982e4baa`, `ad4b5110`,
`bbcd790f`, `12f4e54d`, `2546c698`): the game cannot tell them apart by name. Keep only `cascadia-0.1.1.nomapz`
(`cm.cascadia.d7766d89`).

## Update 0.1.2 (mission only)

The map is unchanged: still `cascadia-0.1.1.nomapz`, build `cm.cascadia.d7766d89`. Only the mission file changed.

- The BDF Annex kept at the Port of Tacoma now lies bow into the wind. It was moored with the wind behind its
  deck, so its COIN and EW1 left the bow too slow and several fell into the bay. BDF's COIN and EW1 should now
  launch from JBLM first.
- PALA escorts no longer wait in the path of their own carriers and destroyers (a Hyperion ran down its own
  patrol boat), and BDF ships no longer stack up on one picket station.
- BDF's rally points at the Port of Tacoma moved from the waterfront to dry ground in the city, so transport
  helicopters there no longer hunt for a landing spot over Commencement Bay.
- The Hood Canal picket starts north of the Hood Canal Bridge (a corvette sailing under it hit the deck and sank).
- One CFB Comox shelter whose fighters often failed to get airborne (6 of 28 in our playtests) is gone.
- Column vehicles that started partly buried on a mountain road (a PALA tank never moved) now start on the ground.
- The Tacoma Narrows vehicle depot is gone: in every recorded session its SAM vehicles jammed at the one road
  junction off the Narrows plateau. BDF's other depots still supply vehicles.
- Host notes in the mission description and the in-game briefing, with a PvP warning about NOCloudDeck.

## What is here

- `Missions/Cascadia Falling/`: the mission as the game saves it (also on the Steam Workshop).
- `workshop/`: the Workshop page text and preview image.
- Releases: the packed map.

The map and mission are generated by a build pipeline (elevation, land cover and OpenStreetMap data through a
Unity bundle builder and a Python mission builder) that is not in this repository.

## Credits and licences

Map data: © OpenStreetMap contributors ([ODbL](https://www.openstreetmap.org/copyright)); ESA WorldCover 2021
([CC BY 4.0](https://esa-worldcover.org/)); USGS 3DEP, NRCan CDEM and NOAA elevation via Mapzen Terrarium
tiles. Map loader: NOCustomMaps by BatongMaster. The mission file and the plugin code are MIT (see LICENSE);
the map data keep their own licences above. Not affiliated with Shockfront Studios.
