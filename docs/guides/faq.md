---
title: FAQ
---

# FAQ

Some questions that come up a lot. If something's actually broken, the [Troubleshooting](troubleshooting.md) page might be more help.

#### How do I soft-reset or quit back to the menu?

With nds-bootstrap, press `L` + `Down` + `SELECT` in game. You can change this combo with `Settings` > `System settings` > `Menu Hotkey`, or [set your own](settings.md#custom-hotkey). More in-game controls are on the [nds-bootstrap controls page](https://wiki.ds-homebrew.com/nds-bootstrap/controls).
#### Should I use Pico-Loader or nds-bootstrap?

If you're on a flashcart that Pico-Loader supports, or a DSpico, give Pico-Loader a go. It's also the only option for `.ndz` files. If your cart isn't supported by Pico-Loader, use nds-bootstrap. On a DSi or 3DS SD card it's nds-bootstrap only.

You don't have to pick just one. Install both and you can switch loaders for an individual game in its [per-game settings](using.md#per-game-settings), which is handy if one game works better with the other loader.

#### What flashcarts does this work with?

Pretty much any flashcart that can run homebrew, either through its own kernel or using one of the autoboot files that come with AKMenu-Next. If you're not autobooting, some carts (like the Games n' Music, or some Slot-2 carts booted into NDS mode) might need `BOOT.NDS` DLDI patched first.

Pico-Loader only works on [certain flashcarts](https://github.com/LNH-team/pico-loader#supported-platforms), but nds-bootstrap will work on anything that runs homebrew.

#### Can I run DSiWare on AKMenu-Next?

Yes, on these setups:

- A modded DSi or 3DS running AKMenu-Next from the console's SD card
- A DSpico plugged into a DSi or 3DS

Normal flashcarts can't run DSiWare since they run in DS mode, and the DS and DS Lite don't have the hardware for it at all. See [Running DSiWare](dsiware.md) for how to set it up.

#### Can I use this alongside TWiLight Menu++?

Yep. The main thing is not to overwrite the `BOOT.NDS` that TWiLight Menu++ uses.

- **DSi:** skip copying `BOOT.NDS` and launch `akmenu-next.dsi` from Unlaunch or TWiLight Menu++ instead.
- **3DS:** skip copying `BOOT.NDS`. You launch AKMenu-Next from the home menu anyway.
- **Flashcart:** rename AKMenu-Next's `BOOT.NDS` to something else (like `akmenu-next.nds`) and launch it from your kernel or from TWiLight.

Both menus use nds-bootstrap from the same `_nds` folder, so you only need it installed once. Both can use a `saves` folder next to your ROMs too, so your saves should carry across as long as the `Save extension` and `Use 'saves' folder` settings match how TWiLight has them.

#### How can I use a nightly build of nds-bootstrap?

Put `nds-bootstrap-nightly.nds` in your `_nds` folder (next to `nds-bootstrap-release.nds`), then go to `Settings` > `Game loader settings` and set `nds-bootstrap version` to `nightly`. You can also just use nightly for one game, from its [per-game settings](using.md#per-game-settings). There's more detail on the [updating page](updating.md#updating-nds-bootstrap).

#### What games are compatible?

Most retail games should work with the latest nds-bootstrap or Pico-Loader. ROM hacks, translations and randomisers might be hit or miss.

AKMenu-Next just hands the game to the loader, so game compatibility problems should be reported to the loader instead:

- [nds-bootstrap issue tracker](https://github.com/DS-Homebrew/nds-bootstrap/issues)
- [Pico-Loader issue tracker](https://github.com/LNH-team/pico-loader/issues)

Homebrew works too. On a DSi or 3DS, some homebrew only runs properly from a flashcart. If something doesn't load, try setting `Homebrew Loader` to `nds-bootstrap-hb` in `Settings` > `Game loader settings`.

#### Where are my saves?

By default (Flashcart, DSi and 3DS editions) they're in a `saves` folder next to the ROM, e.g. `Games/saves/Mario.sav`. The DSpico edition puts them right next to the ROM, e.g. `Games/Mario.sav`. You can change both of these, see [Saves](using.md#saves).

#### Can I have more than one save for a game?

Yes, every game has four save slots. Press `Y` on a game, `Y` again for its settings, and change `Choose Save Slot` in the `Features` tab. See [Save slots](using.md#save-slots).

#### Can I play GBA games?

On a DS or DS Lite with an EZ-Flash 3-in-1 (or compatible) expansion pack, yes, `.gba` files from your SD card can be loaded onto it. You can also boot a real GBA cart (or Slot-2 flashcart) from the `Slot 2 Card` entry.

On a DSi or 3DS there's no GBA slot, but you can set up a GBA emulator (like GBARunner3) as a [plugin](plugins.md) so `.gba` files open in it.

#### Can I use my old Acekard / Wood themes?

Yes! Drop them into `_nds/akmenunext/ui/` and pick them from `START` > `Themes`. See [Themes](themes.md).

#### Can I change the language?

Go to `Settings` > `System settings` > `Language`. Right now AKMenu-Next comes with English, French, German, Italian, Spanish, Russian, Japanese, and Simplified and Traditional Chinese. If you'd like to help translate, the language files are in the [AKMenu-Next repo](https://github.com/coderkei/akmenu-next/tree/main/language).

The `Language Override` setting in `Game loader settings` is something different: it changes which language *games* start in, not the menu.

#### I have a question not listed here

Ask it in the [AKMenu-Next GBAtemp thread](https://gbatemp.net/threads/ds-i-3ds-akmenu-next-wood-frontend-for-nds-bootstrap-pico-loader.665743/). If you want to report a bug or request a feature, please open an issue on the [AKMenu-Next issue tracker](https://github.com/coderkei/akmenu-next/issues).
