---
title: Settings
---

# Settings

Open the settings with `START` > `Settings`, or press `L` + `Y` from the file browser.

Getting around the settings menu:

- `L` / `R` switch between tabs
- `Up` / `Down` pick an option
- `Left` / `Right` change it
- `A` saves (it'll ask you to confirm)
- `B` backs out without saving anything

Some options only show up on certain setups. For example, `Game Loader` only appears on flashcarts and the DSpico, since the DSi and 3DS versions only use nds-bootstrap. If you can't see something listed here, that's probably why.

All of these get saved to `_nds/akmenunext/globalsettings.ini`.

## System settings

| Option | Choices | What it does |
| --- | --- | --- |
| Language | Any installed language | Press `A` on it to choose the menu language. AKMenu-Next restarts to apply it. |
| Menu Hotkey | `L-↓-SELECT`, `L-R-START`, `L-R-SELECT`, `L-R-A-B-↓`, `L-R-B-Y-↓`, `L-R-A-B-X-Y`, Custom | The button combo nds-bootstrap uses to soft-reset back to AKMenu-Next while you're in a game. See [custom hotkeys](#custom-hotkey) below. |
| Slot-2 mode | ask, gba, nds | What happens when you open `Slot 2 Card`. `ask` gives you a choice each time. |

### Custom hotkey

If none of the preset combos suit you, set `Menu Hotkey` to `Custom` and put your own combo in `_nds/akmenunext/ndsbs.ini`:

```ini
[ndsbs]
hotkey=284
```

The value is a hex number made by adding together the buttons you want:

| Button | Value | | Button | Value |
| --- | --- | --- | --- | --- |
| A | `1` | | Right | `10` |
| B | `2` | | Left | `20` |
| SELECT | `4` | | Up | `40` |
| START | `8` | | Down | `80` |
| R | `100` | | X | `400` |
| L | `200` | | Y | `800` |

So `L` + `Down` + `SELECT` is `200` + `80` + `4` = `284`. Remember it's hex, so `L` + `R` + `START` is `200` + `100` + `8` = `308`. If `hotkey=` is left empty, nds-bootstrap just uses its own default.

!!! warning

    Don't delete `ndsbs.ini`, even if you never use a custom hotkey. nds-bootstrap won't launch without it and you'll get an "INI error" message.

## Interface settings

| Option | Choices | What it does |
| --- | --- | --- |
| Filelist style | Old school, Modern, Internal, Small Icons | How the file list looks. You can also cycle through these with `SELECT`. See [file list styles](using.md#file-list-styles). |
| Scrolling speed | Fast, Medium, Slow | How fast the list scrolls when you hold a direction. |
| Icon source | Theme Icons, Global Icons, Built-in icons | Where folder, save and other file icons come from. `Theme Icons` uses the theme's own `icons` folder first, then falls back to `_nds/akmenunext/icons`. `Global Icons` skips the theme and uses `_nds/akmenunext/icons`. `Built-in icons` ignores both. |
| Animation | on, off | Animated game icons and other little bits of motion. |
| 12-hour clock | on, off | Show the clock as 11:45 PM instead of 23:45. |
| Game covers | on, off | Show box art on the top screen, if your theme supports it. See [game covers](themes.md#game-covers). |
| Theme music | on, off | Play the theme's background music, if it has any. |

## File system settings

| Option | Choices | What it does |
| --- | --- | --- |
| Set file list type | NDS, NDS + SAV, ALL | Which files show up in the browser. `NDS` shows games, GBA ROMs and anything you have a plugin for. `NDS + SAV` adds save files. `ALL` shows everything. |
| Show hidden files | on, off | Show files and folders that have the hidden attribute set. |
| Save extension | `.nds.sav`, `.sav` | Whether saves are named `Game.sav` or `Game.nds.sav`. |
| Use 'saves' folder | yes, no | Put saves in a `saves` folder next to the ROM instead of right beside it. |
| Sort by | Name, Game Title, Date Asc, Date Desc | How files are ordered in each folder. |

Have a look at [Saves](using.md#saves) for a table of where save files end up with each combination.

!!! warning

    Changing `Save extension` or `Use 'saves' folder` doesn't move your existing saves. If you change either of them, move your save files to match, or your games will start from a fresh save.

## Game loader settings

| Option | Choices | What it does |
| --- | --- | --- |
| Game Loader | nds-bootstrap, Pico-Loader | Which loader runs your DS games. Flashcart & DSpico only. |
| nds-bootstrap version | release, nightly | Which nds-bootstrap build to use. Nightly needs `_nds/nds-bootstrap-nightly.nds`. |
| DS-Only Mode | on, off | Run games in DS mode, even on a DSi or 3DS. Can help with games that misbehave in DSi mode. |
| TWL CPU Speed | on, off | Run DS games at the DSi's faster CPU speed. Can reduce lag in some games, but break others. DSi & 3DS only. |
| Card Read DMA | Auto, on, off | nds-bootstrap's card read DMA. Leave it on `Auto` unless you've been told a specific game needs it changed. |
| Language Override | System, Japanese, English, French, German, Italian, Spanish, Chinese, Korean | Make games start in a different language than your console is set to. Only works for games that actually include that language. |
| DS Phat Colors | on, off | Mimic the slightly different colours of the original DS screen. DSi mode only. |
| DSiWare booter | nds-bootstrap, Unlaunch | What to launch DSiWare with on a DSi. `Unlaunch` also works if you have Astronaut installed instead. See [Running DSiWare](dsiware.md). DSi mode only. |
| Homebrew Loader | AKMenu-Next, nds-bootstrap-hb, Pico-Loader | What to launch homebrew with. See below. |

Most of these settings are only for nds-bootstrap. If you're using Pico-Loader they won't make a difference.

### Homebrew Loader

- **AKMenu-Next** (the default) boots homebrew directly. This is what you want most of the time.
- **nds-bootstrap-hb** runs homebrew through nds-bootstrap's homebrew build. Useful on a DSi or 3DS SD card for homebrew that was only ever meant to run from a flashcart and won't work otherwise. Needs `_nds/nds-bootstrap-hb-release.nds`.
- **Pico-Loader** runs homebrew through Pico-Loader instead. Needs Pico-Loader in `_pico`.

## Other Settings

| Option | Choices | What it does |
| --- | --- | --- |
| Ignore CRC16 Errors | on, off | Some ROM hacks and translations have a broken checksum on their icon, so they show a generic icon. Turn this on to show the icon anyway. |
| Cheat in Game(AR) | on, off | The global switch for cheats. Games can override this in their [per-game settings](using.md#per-game-settings). |
| Save Slot Override | off, 0, 1, 2, 3 | Force every game onto the same [save slot](using.md#save-slots). `0` is the default slot. |
| Autorun Last ROM | on, off | Launch the last game you played as soon as AKMenu-Next starts. Hold `B` while booting to skip it. |
| Override plugin defaults | on, off | Always use your `Homebrew Loader` setting for plugins, even if the plugin asks for nds-bootstrap-hb. See [Plugins](plugins.md#how-plugins-are-launched). |

## Resetting your settings

If you've got yourself into a mess, you can put everything back to default:

1. Delete `_nds/akmenunext/globalsettings.ini`.
1. Copy `_nds/akmenunext/globalsettings-init.ini` from a fresh download of AKMenu-Next (the same edition you're using) into `_nds/akmenunext` on your SD card.
1. Boot AKMenu-Next. It'll pick up the fresh settings and ask you for your language again.

If you skip step 2 it still works, but you'll get AKMenu-Next's built-in defaults rather than the ones tuned for your edition.

There are a few other files in `_nds/akmenunext` you can delete to reset other things:

| File | What it holds |
| --- | --- |
| `favorites.ini` | Your favourites |
| `recent.ini` | Recently Played |
| `lastsave.ini` | The last game you played (used by autorun and to remember your folder) |
| `gamedata.bin` | Per-game settings and save types |
| `backlight.ini` | Screen brightness |
