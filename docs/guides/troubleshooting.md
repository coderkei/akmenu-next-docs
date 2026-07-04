---
title: Troubleshooting
---

### AKMenu-Next Troubleshooting

If you encounter issues when using AKMenu-Next, please refer to the below information:

#### The menu loads with just a black screen and a cursor

 - You have an incompatible or improperly installed theme, or the `_nds` folder is missing. Try reinstalling the theme (you may need to edit the name of the theme to the correct folder name in `_nds/akmenunext/globalsettings.ini`) or reinstalling AKMenu-Next from the [Installing AKMenu-Next](../guides/akmenu-next.md) page.

#### The menu loads but the bottom screen has no icons or text

- An error occured trying to read from the SD card. This can sometimes occur by using the wrong version of AKMenu-Next (such as using the DSi version on the DSpico). Please ensure the SD card is fully working and that you have the correct version of AKMenu-Next installed.

#### I get "Loader not found" when trying to run games

- You don't have the files for the chosen loader installed, please switch to another loader in the settings, or install the corresponding loader's files. The guides for both compatible loaders (nds-bootstrap and Pico-Loader) are listed on the [Installing AKMenu-Next](../guides/akmenu-next.md) page.

#### I get a message telling me to reinstall AKMenu-Next

- Your installation of AKMenu-Next is corrupted or important configuration files are missing. This can sometimes be caused by a failing SD card as well. Please [test your SD card](https://www.flashcarts.net/microsd-fakes#testing-a-microsd-card) with **H2TestW** or **F3** and reinstall AKMenu-Next from the [Installing AKMenu-Next](../guides/akmenu-next.md) page.

#### I get a message telling me there is not enough space available when launching a game

- This occurs when there is not enough space available on the SD card to create a save file, or when the SD card unexpectedly becomes inaccessible. Please ensure you have at least 50MB free on your SD card when running games to account for the game's save file and any additional files created by nds-bootstrap or Pico-Launcher. If you have enough free space and are still seeing this error, there may be a problem with your SD card.

#### I get "An error occured", "Data abort" or "Failed to load arm9" or similar errors

- These errors come from the game loader you are using and you should seek assistance for the loader you are using:
- [nds-bootstrap issue tracker](https://github.com/DS-Homebrew/nds-bootstrap/issues)
- [Pico-Loader issue tracker](https://github.com/LNH-team/pico-loader/issues)

