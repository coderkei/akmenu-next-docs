---
title: Troubleshooting
---

# Troubleshooting

Something not working? Have a look through the errors below. If yours isn't here, the [FAQ](faq.md) might help, or you can ask in the [GBAtemp thread](https://gbatemp.net/threads/ds-i-3ds-akmenu-next-wood-frontend-for-nds-bootstrap-pico-loader.665743/).

!!! tip "Check the About screen first"

    Press `START` and choose `About`. It tells you which version of AKMenu-Next you're on, whether it thinks it's running from a flashcart, DSpico or SD card, and which versions of nds-bootstrap and Pico-Loader it can find. If a loader says `N/A`, AKMenu-Next can't see it, which explains a lot of problems on its own.

## Errors when AKMenu-Next starts

#### "AKMenu-Next system files are missing or corrupted"

AKMenu-Next couldn't find its own files. It needs at least `_nds/akmenunext/` and `_nds/akmenunext/launcher.nds` on the root of your SD card.

- Make sure you copied the whole `_nds` folder from the download, and that it's on the root of the card, not inside another folder.
- If it was working before, your SD card might be on its way out. Back up your saves and [test your SD card](https://www.flashcarts.net/microsd-fakes#testing-a-microsd-card) with **H2testw** or **F3**. Fake and failing cards are honestly the most common cause of this.
- Then reinstall AKMenu-Next from the [install guide](akmenu-next.md).

#### "AKMenu-Next cannot launch: no valid themes are installed"

There aren't any themes AKMenu-Next can use in `_nds/akmenunext/ui`.

- Check there's at least one theme folder in there, with a `uisettings.ini` file directly inside it (not in another folder inside it, see the [themes page](themes.md#installing-a-theme)).
- If you deleted the bundled themes, copy them back from the download.
- If your themes are definitely there, the files might be corrupted. Same as above, test your SD card.

#### "The selected theme is missing or corrupt"

The theme you had picked is broken or gone, so AKMenu-Next switched to another one. You can carry on using the menu as normal. If you want your old theme back, reinstall it and pick it again from `START` > `Themes`.

#### White screen, black screen, or it freezes on boot

- If you're on a flashcart, make sure your kernel is actually able to launch homebrew, and try launching `BOOT.NDS` from the kernel menu instead of autobooting.
- If AKMenu-Next can't see your SD card, `BOOT.NDS` might need to be DLDI patched for your cart.
- If you have `Autorun Last ROM` turned on, the problem might be the game, not the menu. Hold `B` while AKMenu-Next starts to skip autorun.
- Try a different theme by editing `uiName` in `_nds/akmenunext/globalsettings.ini` to `Blue Skies`.

## Errors when launching a game

#### "Loader not found"

AKMenu-Next can't find the files for the loader it's trying to use. The message tells you which file it was looking for.

| Loader | It needs |
| --- | --- |
| nds-bootstrap | `_nds/nds-bootstrap-release.nds` |
| nds-bootstrap (nightly) | `_nds/nds-bootstrap-nightly.nds` |
| nds-bootstrap-hb (homebrew & plugins) | `_nds/nds-bootstrap-hb-release.nds` |
| Pico-Loader | `_pico/picoLoader7.bin` and `_pico/picoLoader9.bin` |

Either install the missing loader (see the [install guide](akmenu-next.md)), or switch to one you do have in `Settings` > `Game loader settings`. Don't forget to check the game's own [per-game settings](using.md#per-game-settings) too, it might be set to a different loader or to nightly.

If it's a plugin file you're launching, the missing file might be the emulator itself. Check the `path` in the plugin's INI.

#### "INI error: ndsbs.ini is missing from _nds/akmenunext or is corrupt"

AKMenu-Next needs `_nds/akmenunext/ndsbs.ini` to launch nds-bootstrap. Copy it back over from a fresh download of AKMenu-Next (it's called `ndsbs-init.ini` in the download, which works fine, AKMenu-Next will rename it on the next boot).

#### "There is not enough space on the disk"

AKMenu-Next couldn't create the save file for the game. Saves can be up to a few MB (and some games, like WarioWare D.I.Y., need 32MB), so make sure you've got a decent amount of free space. Keeping at least 50MB free is a good idea, as nds-bootstrap and Pico-Loader need some room for their own files too.

If you've got loads of free space and still see this, the SD card might be read-only, corrupted, or failing. Run a disk check on it and [test the card](https://www.flashcarts.net/microsd-fakes#testing-a-microsd-card).

#### It shows "Initializing nds-bootstrap" and then a message about first-time setup

That's normal! The first time you use nds-bootstrap it has to create a big file (`_nds/pagefile.sys`). Just press `OK` and wait, it only happens once.

#### "DSiWare launch requires a ROM on the DSi SD card and DSi mode"

You tried to launch DSiWare through nds-bootstrap from somewhere that doesn't support it. Through nds-bootstrap, DSiWare has to be on the *console's* SD card (the `DSi SD` entry). If you're on a DSpico, either set the game to use Pico-Loader, or move it to the console's SD card. See [Running DSiWare](dsiware.md).

#### "Could not create the DSiWare save files on the SD card"

Same as the "not enough space" error above, but for DSiWare's `.pub`/`.prv` saves. Check your free space and that the card isn't read-only.

#### "An error occurred", "Data abort", "Failed to load arm9" or similar

Errors like these come from the game loader, not AKMenu-Next. A few things worth trying first:

- Update your loader to the latest version (see [Updating](updating.md)).
- Try the other loader, if you have both. You can do this for just that one game.
- If you're on nds-bootstrap, try turning `DS-Only Mode` or `TWL CPU Speed` on or off for that game.
- Turn cheats off for that game.
- Make sure the ROM itself isn't a bad dump.

If none of that helps, report it to the loader you're using:

- [nds-bootstrap issue tracker](https://github.com/DS-Homebrew/nds-bootstrap/issues)
- [Pico-Loader issue tracker](https://github.com/LNH-team/pico-loader/issues)

!!! tip "Getting a log from nds-bootstrap"

    If you create an empty file called `debug.txt` in your `_nds` folder, AKMenu-Next turns on nds-bootstrap's logging and debug mode. This can be really helpful to attach to a bug report. Delete the file again when you're done, as it slows things down.

## Other problems

#### My game started with a blank save / my save is gone

AKMenu-Next looks for saves based on your `Save extension` and `Use 'saves' folder` settings. If they don't match where your saves actually are, it'll make a new blank save instead. Check [where saves go](using.md#saves), move your save to the right place, and make sure the game's [save slot](using.md#save-slots) is set to default (and that `Save Slot Override` is off).

#### My game doesn't save properly

Try setting the save type manually. Press `Y` on the game, then `Y` again, and change `Select a save type`. If you're not sure what it should be, look the game up in a save type list, or ask in the GBAtemp thread.

#### Cheats aren't showing up

- Make sure `usrcheat.dat` is at `_nds/akmenunext/cheats/usrcheat.dat`. If AKMenu-Next can't find it, the `Cheats` button won't show at all.
- If the button's there but nothing comes up, your database doesn't have that game (or that version of it). Try a newer database.
- Cheats aren't available for homebrew.

#### Cheats aren't working in game

- Make sure `Cheat in Game(AR)` is on, either globally in `Other Settings` or in the game's per-game settings.
- Make sure you saved your cheat selection with `X`.
- If you're using Pico-Loader, update it. Older versions don't support cheats.

#### My ROM hack or translation has a blank/generic icon

Its banner checksum is probably wrong. Turn on `Ignore CRC16 Errors` in `Other Settings` and the proper icon should show.

#### A file type I have a plugin for doesn't show up

- Make sure the INI is directly in `_nds/akmenunext/plugins/` and named after the extension (e.g. `gbc.ini`).
- Restart AKMenu-Next, plugins are only loaded at startup.
- Check the INI has at least a `path` (or `dsipath`/`ntrpath`), otherwise it's ignored.
- Check your `Set file list type` isn't doing anything odd, or press `L` + `SELECT` to show all files.

#### Game covers aren't showing

- Make sure you're using a theme that supports covers (it'll be listed under "Game Cover Themes").
- Check `Game covers` is turned on in `Interface settings`.
- Check the cover's name and location, see [game covers](themes.md#game-covers). Press `Y` on the game to double check its game code.
- Make sure the cover is a normal BMP and not too big.

#### No theme music

- Not every theme has music.
- Check `Theme music` is turned on in `Interface settings`.
- If it's your own theme, check the format of your music files, see [theme music](themes.md#theme-music).

#### Can't see the DSi SD card on my DSpico

The `DSi SD` entry only shows up when the DSpico is running in DSi mode on a DSi or 3DS, and there's an SD card in the console itself.
