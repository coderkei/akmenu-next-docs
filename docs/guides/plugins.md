---
title: Plugins
---

### AKMenu-Next Plugins

Plugins allow AKMenu-Next to be extended to launch other filetypes including Emulator ROMs and Videos.

=== "Installing Plugins"

    1. Visit the [AKMenu-Next Plugins Page](https://github.com/coderkei/akmenu-next-plugins/releases/latest) and download the plugin you want.

    1. Extract the contents of the plugin download to your computer.

    1. Ensure that the plugin download contains an `_nds` folder. Copy the `_nds` folder and any other folders or files next to it and paste it to the root of your SD card. You may be asked to replace files. If you are on Windows, click `Replace the file in the destination`. If you are on MacOS, click `Merge` and not `Replace` otherwise the existing `_nds` folder will be deleted.

    1. Files that have an extension supported in the plugin will now show in the AKMenu-Next file browser and can be launched

=== "Making Plugins"

    #### Plugin INI

    - AKMenu-Next plugins come as `{Extension}.ini` files which must be loacated in `_nds/akmenunext/plugins` and use the below format:

    ```
    [plugin]
    path=path/to/nds/here.nds
    argv=1
    bootstrap=0
    ```

    - `path` = Path to the `.nds` file that will be launched with the plugin. This file can be located anywhere but the advised location is `_nds/akmenunext/plugins/app`.
    - `argv` = Sets whether the filepath of the file launched is passed to the NDS file specified.
    - `bootstrap` = Sets whether the path of the plugin is launched with nds-bootstap-hb.nds. This is used for the DSi SD card and is ignored if the user is on a flashcart.

    #### Icons

    - Icons are located in `_nds/akmenunext/plugins/icons` and are standard Nintendo DS banner files. They should be named as `{Extension}.bin` so that they are loaded when the accompanying extension is loaded. If the icon is missed or invalid, AKMenu-Next will fallback to the default placeholder icon for that extension.