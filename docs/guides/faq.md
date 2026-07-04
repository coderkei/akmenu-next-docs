---
title: FAQ
---

### AKMenu-Next FAQ

Please see below for frequently asked questions about AKMenu-Next.

#### How do I soft-reset or quit back to the menu

- Use the nds-bootstrap button combination of L + Down + Select or change it in Settings -> Menu Hotkey.​ More controls can be found on the nds-bootstrap controls page. Pico-Loader currently does not support soft-reset.​

#### What flashcarts does this work with?

- This should work on any flashcart that can load homebrew, either via it's kernel, or via one of the provided autoboot files. If not autobooting, some flashcarts such as the Games N Music or some Slot 2 carts booted into NDS mode may require you to DLDI patch BOOT.NDS first.​
​
#### Can I run DSiWare on AKMenu-Next?

- DSiWare is supported on the DSpico cart when running on a DSi or 3DS with the Game Loader set to Pico-Loader. You must have the required DSi files for this to run, the instructions for this are available above in the main links.​

- Due to the complexity of adding TWiLight Menu++'s DSiWare implementation for it into the existing akmenu4 code. Please use TWiLight Menu++ to run DSiWare if you are not on a DSpico.​
​
#### Can I use this alongside TWiLight Menu++ on a DSi or 3DS?

- On a 3DS or a DSi system you must take care to not overwrite the existing BOOT.NDS file required by TWiLight Menu++.​ If you plan to use both on a DSi, copy only the akmenu-next.dsi file and launch that via Unlaunch or TWiLight Menu++. This is explained in the guide. On a 3DS, omit copying the BOOT.NDS file.​
​
- Likewise the same applies to a flashcart should you wish to use both, where you should rename the included BOOT.NDS to something else and launch it with the existing kernel you are using.​
​
#### How can I use a nightly build of nds-bootstrap on AKMenu-Next?

- Put a copy of nds-bootstrap-nightly.nds inside the _nds folder. Then go into the settings and under the File system settings section, set nds-bootstrap version to nightly.​
​
#### What games are compatible?

- Typically most retail games should compatible in the latest version of nds-bootstrap and Pico-Loader. Compatibility with rom-hacks, translations and randomizers are not guaranteed.​
​
- Any issues with game compatibility should be submitted on the [nds-bootstrap issue tracker](https://github.com/DS-Homebrew/nds-bootstrap/issues) or the [Pico-Loader issue tracker.](https://github.com/LNH-team/pico-loader/issues)

- Homebrew is supported as well, although homebrew compatibility may be limited on DSi and 3DS systems due to some homebrew only running correctly on flashcarts, on those systems you may opt to use the "nds-bootstrap" option in the "Homebrew Loader" for any homebrew that doesn't load with the default loader.​

#### I have a question not listed here

- Please submit your question to the [AKMenu-Next GBATemp Thread](https://gbatemp.net/threads/ds-i-3ds-akmenu-next-wood-frontend-for-nds-bootstrap-pico-loader.665743/) or if you wish to report a bug, issue or feature request, please open a request on the [AKMenu-Next Issue Tracker.](https://github.com/coderkei/akmenu-next/issues)

