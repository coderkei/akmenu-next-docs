---
title: Using the Menu
---

# Using the Menu

This page goes over the day-to-day stuff: getting around, launching things, saves, cheats and so on. For a rundown of every option in the settings menu, see [Settings](settings.md).

## Controls

### File browser

| Button | What it does |
| --- | --- |
| `D-Pad Up/Down` | Move through the list |
| `D-Pad Left/Right` | Jump up/down a page |
| `A` | Open a folder or launch the selected file |
| `B` | Go back to the parent folder |
| `L` (tap) | Also goes back to the parent folder |
| `X` | Jump to Favourites |
| `Y` | File info for the selected file (this is where per-game settings live) |
| `START` | Open the start menu |
| `SELECT` | Cycle through file list styles |
| `R` | Change screen brightness (DS / DS Lite only) |
| `L` + `Y` | Open settings |
| `L` + `X` | Open the cheat list for the selected game |
| `L` + `SELECT` | Temporarily show all files, not just games |

The touch screen works too, you can tap on items, the `START` button and the folder-up button.

!!! tip

    Can't remember all that? Press `START` and choose `Help` to see the main ones on screen.

### In game

Once a game is running, the controls belong to the loader, not AKMenu-Next. With nds-bootstrap the default soft-reset combo is `L` + `Down` + `SELECT`, which takes you back to AKMenu-Next. You can change this with the `Menu Hotkey` setting (see [Settings](settings.md#system-settings)). The full list of nds-bootstrap controls is on the [nds-bootstrap controls page](https://wiki.ds-homebrew.com/nds-bootstrap/controls).
## The start menu

Press `START` (or tap the button in the corner) to open it.

| Option | What it does |
| --- | --- |
| Set favourite | Add the selected file to Favourites |
| Remove favourite | Remove the selected file from Favourites |
| File Info | Same as pressing `Y` |
| Themes | Pick a different theme (see [Themes](themes.md)) |
| Tools | Settings for an EZ-Flash 3-in-1 expansion pack, if you have one in Slot-2 |
| Settings | The main settings menu |
| Help | A quick list of controls |
| About | Your AKMenu-Next version, what mode it's running in, and which loaders it found |

The `About` screen is really handy when something isn't working. It tells you if AKMenu-Next can actually see nds-bootstrap and Pico-Loader, and which versions they are.

## Favourites and Recently Played

**Favourites** is a shortcut list you build yourself. Highlight a game, press `START` and choose `Set favourite`. You can get to the list from the top level of the browser, or press `X` from anywhere.

**Recently Played** keeps track of the last 10 games you launched, newest first. Homebrew isn't added to it, but DS games, DSiWare and plugin files are.

## File list styles

Press `SELECT` to flip between the four styles, or set one permanently in `Settings` > `Interface settings` > `Filelist style`.

| Style | Looks like |
| --- | --- |
| Old school | Plain text list, no icons |
| Modern | Big icons with the file name |
| Internal | Big icons with the game's real title from its banner |
| Small Icons | Smaller icons so you can fit more on screen |

If you'd like the list sorted by something other than file name, have a look at `Sort by` under `File system settings`. You can sort by game title or by date too.

## Launching games

Just highlight a game and press `A`. Here's what AKMenu-Next recognises out of the box:

| Extension | What it is | Launched with |
| --- | --- | --- |
| `.nds` | DS games and homebrew | Your selected game loader (or homebrew loader for homebrew) |
| `.dsi`, `.srl`, `.ids` | DSi-enhanced / DSiWare / other DS ROM dumps | Your selected game loader |
| `.ndz` | Compressed DS ROMs | Always Pico-Loader |
| `.gba` | GBA ROMs | EZ-Flash 3-in-1 if one is inserted, otherwise a `gba` plugin if you have one |

Anything else needs a [plugin](plugins.md), or you can press `L` + `SELECT` to see every file.

### Autorun

If you turn on `Autorun Last ROM` (in `Other Settings`), AKMenu-Next will launch the last game you played straight away when it starts up. Hold `B` while AKMenu-Next is booting if you want to skip it and get to the menu.

## Per-game settings

Highlight a game, press `Y` to open its file info, then press `Y` again (the `Settings` button) to get its per-game settings. Anything set to `default` just follows the global setting from the main settings menu.

There are two tabs. Use `L`/`R` to switch between them.

**Compatibility**

| Option | What it does |
| --- | --- |
| Select a save type | Force a specific save size. Leave on `unknown/auto` unless a game isn't saving properly |
| Game Loader | Use Pico-Loader or nds-bootstrap for just this game (flashcart & DSpico only) |
| nds-bootstrap version | Release or nightly, for this game only |
| DS-Only Mode | Run this game in DS mode instead of DSi mode |
| TWL CPU Speed | Run this game at the DSi's faster CPU speed |
| Card Read DMA | Turn nds-bootstrap's card read DMA on or off for this game |
| DSiWare booter | Only shows up for DSiWare. Use nds-bootstrap or Unlaunch for this title |

The nds-bootstrap options only show up when the game is actually going to use nds-bootstrap. If you change `Game Loader` to nds-bootstrap, save, then open the settings again and they'll appear.

**Features**

| Option | What it does |
| --- | --- |
| Cheat in Game (AR) | Enable or disable cheats for this game, or follow the global setting |
| Choose Save Slot | Which save slot to use (see [save slots](#save-slots) below) |
| Show icon | How the game's icon is drawn: transparent, as is, or how the DS firmware would show it |

Per-game settings are stored in `_nds/akmenunext/gamedata.bin`, so if you ever want to wipe them all at once, delete that file.

## Saves

AKMenu-Next creates the save file for you the first time you launch a game, so there's nothing to set up. If there isn't enough free space on the card for the save, you'll get a "not enough space" error instead of the game booting.

Where the save goes depends on two settings in `File system settings`:

| Use 'saves' folder | Save extension | Save for `Games/Mario.nds` ends up at |
| --- | --- | --- |
| Yes | `.sav` | `Games/saves/Mario.sav` |
| Yes | `.nds.sav` | `Games/saves/Mario.nds.sav` |
| No | `.sav` | `Games/Mario.sav` |
| No | `.nds.sav` | `Games/Mario.nds.sav` |

The Flashcart, DSi and 3DS editions use a `saves` folder by default. The DSpico edition puts saves next to the ROM by default.

!!! tip "Coming from another menu?"

    If your existing saves are somewhere else (for example, TWiLight Menu++ also uses a `saves` folder, but some kernels put `.sav` files next to the ROM), either move them to match, or change these two settings to match where your saves already are. Do this **before** launching the game, otherwise AKMenu-Next will make a fresh blank save.

### Save slots

Each game can have up to four separate saves. Slot "default" is the normal save file, and slots 1 to 3 add a number before the extension:

```text
Mario.sav     <- default slot
Mario.1.sav   <- slot 1
Mario.2.sav   <- slot 2
Mario.3.sav   <- slot 3
```

Pick a slot from the game's [per-game settings](#per-game-settings). Slots that already have a save file are marked with a `*`. There's also a global `Save Slot Override` in `Other Settings` which forces every game onto the same slot, handy if you're sharing the console with someone.

### DSiWare saves

DSiWare uses `.pub` and `.prv` save files instead of `.sav`. These are made automatically too. See [Running DSiWare](dsiware.md#saves) for details.

## Cheats

1. Make sure you've got a `usrcheat.dat` in `_nds/akmenunext/cheats/` (see the install guide for where to get one).

1. Go to `Settings` > `Other Settings` and turn `Cheat in Game(AR)` on. This is the global switch.

1. Highlight a game and press `L` + `X`, or press `Y` and then `X` (`Cheats`). You'll get the list of cheats for that game.

1. In the cheat list:

    | Button | What it does |
    | --- | --- |
    | `A` | Tick or untick a cheat (or open a folder of cheats) |
    | `Y` | Show the description for the selected cheat |
    | `L` | Untick everything |
    | `Left`/`Right` | Jump between cheat folders |
    | `X` | Save your selection |
    | `B` | Back out without saving |

1. Launch the game as normal. Your ticked cheats will be applied.

If you want cheats on for one game but off everywhere else, leave the global switch off and set `Cheat in Game(AR)` to `on` in that game's per-game settings.

Cheats work with both nds-bootstrap and Pico-Loader (make sure your Pico-Loader is up to date, older versions didn't support them). If the `Cheats` button doesn't show up in the file info window at all, AKMenu-Next can't find `usrcheat.dat`. If the button is there but nothing opens, that game probably just isn't in your cheat database.

!!! note

    Cheats aren't available for homebrew. Some cheats in the database can crash games or corrupt saves, so if a game starts misbehaving, try it with cheats off.

## Slot-1 and Slot-2

- **Slot 1 Card** (DSi & 3DS SD card versions only) boots whatever game card is in the console's cartridge slot.
- **Slot 2 Card** (DS & DS Lite) boots whatever's in the GBA slot. Depending on the `Slot-2 mode` setting it'll ask whether to start it in GBA mode or NDS mode, or just do one of them. If nothing is inserted you'll get a message saying so.

If you have an EZ-Flash 3-in-1 (or compatible) expansion pack inserted, `.gba` files on your SD card can be loaded into it. Press `Y` on a GBA ROM for the `to NOR` and `to RAM` buttons, and use `Tools` in the start menu for its rumble and memory settings. GBA ROMs bigger than 32MB aren't supported.
