---
title: Plugins
---

# Plugins

Plugins let AKMenu-Next open file types it doesn't understand on its own. A plugin just tells AKMenu-Next "when someone opens a `.gbc` file, start this emulator and pass it the file". It's how you get things like Game Boy, NES or SNES ROMs, or videos, showing up in your file list and launching with one press of `A`.

=== "Installing Plugins"

    1. Go to the [AKMenu-Next Plugins page](https://github.com/coderkei/akmenu-next-plugins/releases/latest) and download the plugin(s) you want.

    1. Extract the download on your computer.

    1. Inside you should find an `_nds` folder (and maybe some other files or folders next to it). Copy all of it to the root of your SD card.

        - On **Windows**, if it asks about replacing files, choose `Replace the file in the destination`.
        - On **macOS**, choose `Merge`, **not** `Replace`. Replace will wipe your existing `_nds` folder, AKMenu-Next and all.

    1. Put the SD card back and start AKMenu-Next. Files with the plugin's extension will now show up in the file browser and can be launched like anything else.

    !!! note

        Plugins are loaded when AKMenu-Next starts up, so if you add one while the menu's running, restart it before the new files show up.

    !!! tip "GBA files and the EZ-Flash 3-in-1"

        If you've got a `gba` plugin installed *and* an EZ-Flash 3-in-1 in Slot-2, `.gba` files will go to the 3-in-1 instead of the plugin. Take the 3-in-1 out if you want to use the plugin.

=== "Making Plugins"

    #### The plugin INI

    Each plugin is a single `.ini` file in `_nds/akmenunext/plugins/`. The file name is the extension it handles, so `gbc.ini` handles `.gbc` files, `nes.ini` handles `.nes` files and so on. Extensions aren't case sensitive.

    Here's what one looks like:

    ```ini
    [plugin]
    path=app/myemulator.nds
    argv=1
    bootstrap=0
    hbargv=0
    ```

    And here's every key you can use:

    | Key | Default | What it does |
    | --- | --- | --- |
    | `path` | (none) | The `.nds` file to launch. This is the fallback if `dsipath`/`ntrpath` aren't set. |
    | `dsipath` | (none) | Use this `.nds` instead when AKMenu-Next is running in DSi mode (DSi/3DS SD card, or a DSpico in a DSi/3DS). |
    | `ntrpath` | (none) | Use this `.nds` instead when AKMenu-Next is running in DS mode (flashcarts, or anything on a DS/DS Lite). |
    | `argv` | `0` | Set to `1` to pass the selected file's path to the emulator. Almost every emulator needs this. |
    | `bootstrap` | `0` | Set to `1` to launch the plugin through nds-bootstrap-hb. This only kicks in on a DSi/3DS SD card, it's ignored on flashcarts. |
    | `hbargv` | `0` | Set to `1` to also pass the file through nds-bootstrap-hb's `HOMEBREW_ARG` setting. Only used when the plugin is actually going through nds-bootstrap-hb. |
    | `extension` | file name | Override the extension, if you want the INI to be called something different from the extension it handles. |

    You need at least one of `path`, `dsipath` or `ntrpath`, otherwise the plugin is skipped. If you set `dsipath` but no `path`, the plugin only works in DSi mode (and the same the other way round with `ntrpath`). You'll get an error if you try to open the file in the other mode.

    `dsipath` and `ntrpath` are handy for emulators that have separate DS and DSi builds, or if one version just runs better on one kind of setup.

    !!! warning

        Don't put `//` comments on the end of lines like you might see in some examples. Everything after the `=` is read as the value, so `argv=1 // passes the file` won't do what you want. If you want notes in your INI, put them on their own line starting with `;` or `//`.

    #### Where paths point to

    Paths in a plugin INI can be written a few ways:

    | Written as | Points to |
    | --- | --- |
    | `app/emu.nds` | Relative to the plugins folder, so `_nds/akmenunext/plugins/app/emu.nds` |
    | `_nds/emu.nds` | From the root of the SD card |
    | `/apps/emu.nds` | From the root of the SD card |
    | `fat:/apps/emu.nds` or `sd:/apps/emu.nds` | That exact drive and path |

    The usual place to keep the emulator itself is `_nds/akmenunext/plugins/app/`, which is what the official plugins do. That way your `path` can just be `app/emu.nds`.

    #### How plugins are launched

    Plugins are treated as homebrew, so they follow your `Homebrew Loader` setting (in `Settings` > `Game loader settings`):

    - **AKMenu-Next** (the default): the emulator is booted directly.
    - **nds-bootstrap-hb**: the emulator is booted through nds-bootstrap-hb.
    - **Pico-Loader**: the emulator is booted through Pico-Loader.

    The one exception is `bootstrap=1`. On a DSi or 3DS SD card, that forces nds-bootstrap-hb for that plugin no matter what your `Homebrew Loader` is set to. This is for emulators that were really made for flashcarts and only work properly from the DSi SD through nds-bootstrap-hb.

    If you'd rather your own `Homebrew Loader` setting always wins, turn on `Override plugin defaults` in `Other Settings`.

    #### Plugin icons

    To give your file type an icon, put a standard Nintendo DS banner file in `_nds/akmenunext/plugins/icons/`, named after the extension, e.g. `gbc.bin` for `.gbc` files. If there isn't one, the files get the default "unknown file" icon.

    Banner files are the same format as the banner inside a `.nds` file. You can pull one out of an existing `.nds` with tools like `ndstool` (`ndstool -x game.nds -t banner.bin`).

    #### Per-file banners

    Want a specific file to have its own icon? Put a DS banner file in the same folder as it, named the file's **full** name with `.bin` on the end:

    ```text
    Pokemon Crystal.gbc
    Pokemon Crystal.gbc.bin   <- icon for that one file
    Mario.nds
    Mario.nds.bin             <- replaces Mario's built-in icon
    ```

    A per-file banner wins over everything else: the ROM's own icon, and the plugin's extension icon. It works for any file the browser is showing, so as long as the file type is covered by a plugin (or you're showing all files), it'll use it.

    #### Example: a Game Boy plugin

    Say you've got a Game Boy emulator called `gbemu.nds` that accepts a ROM path through argv, and you want `.gb` and `.gbc` files to open in it.

    1. Put `gbemu.nds` in `_nds/akmenunext/plugins/app/`.

    1. Make `_nds/akmenunext/plugins/gb.ini`:

        ```ini
        [plugin]
        path=app/gbemu.nds
        argv=1
        ```

    1. Make a copy of it called `gbc.ini` (each extension needs its own INI).

    1. Optionally, add `gb.bin` and `gbc.bin` icons to `_nds/akmenunext/plugins/icons/`.

    1. Restart AKMenu-Next and your Game Boy ROMs will show up.

    If you make something you think other people would like, consider sharing it on the [GBAtemp thread](https://gbatemp.net/threads/ds-i-3ds-akmenu-next-wood-frontend-for-nds-bootstrap-pico-loader.665743/)!
