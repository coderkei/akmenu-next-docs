---
title: Themes
---

### AKMenu-Next Themes

AKMenu-Next is compatible with Wood R4 and AKAIO themes (also known as AKMenu themes as all three menus are based upon AKMenu). To install themes, please see the below steps:

#### Install AKMenu-Next Themes

1. Visit the [Wood R4/AKMenu Theme Repository](https://themes.flashcarts.net/akmenu/).
1. Find a theme you wish to install and download it.
1. Open/Extract the .7z archive. You can use [7-Zip](https://7-zip.org/) to do this.
1. Inside the 7z archive, you will find a folder with the theme's name. Copy this folder to `_nds/akmenunext/ui` folder on your SD Card.
1. Place the SD card back into your flashcart or console, and boot into AKMenu-Next.
1. Press the `START` key to open the AKMenu-Next start menu popup, then select `Settings`.
1. Set the theme to the name of the theme you downloaded, then press A to save, and A again to restart.

!!! warning
    Please ensure that your theme is not a folder inside a folder!

    For example if your theme is called "HatsuneMiku", ensure that the path is `_nds/akmenunext/ui/HatsuneMiku` and not `_nds/akmenunext/ui/HatsuneMiku/HatsuneMiku`

    If you do not check for this, you will end up with a broken AKMenu-Next installation after selecting the theme and will need to reinstall AKMenu-Next, or edit `_nds/akmenunext/globasettings.ini` to set back one of the default themes (such as "zelda").