---
title: Updating AKMenu-Next
---

# Updating AKMenu-Next

AKMenu-Next, nds-bootstrap and Pico-Loader are all separate projects, so they're updated separately too. You don't have to update them all at once.

You can check what you've currently got by pressing `START` and choosing `About`. It shows your AKMenu-Next version and the versions of any loaders it can find.

The latest versions and changelogs are here:

- [AKMenu-Next releases](https://github.com/coderkei/akmenu-next/releases/latest)
- [nds-bootstrap releases](https://github.com/DS-Homebrew/nds-bootstrap/releases/latest)
- [Pico-Loader releases](https://github.com/LNH-team/pico-loader/releases/latest)

!!! warning "Mac users: Merge, don't Replace"

    When macOS asks what to do with an existing folder, always pick **Merge**. **Replace** deletes the whole old folder first, which takes your themes, plugins, cheats and settings with it.

!!! tip "Your settings are safe"

    Updating won't reset your settings, favourites or recently played list. AKMenu-Next ships its defaults as `-init.ini` files and only uses them if you don't already have a real one, so overwriting is fine.

## Updating AKMenu-Next

=== "Flashcart"

    1. Download the latest release of [AKMenu-Next Flashcart Edition](https://github.com/coderkei/akmenu-next/releases/latest/download/akmenu-next-flashcart.zip).

    1. Extract the downloaded `akmenu-next-flashcart.zip` file with [7-Zip](https://www.7-zip.org/).

    1. Copy the following files/folders to the root of your SD card:

        - `_nds` folder
        - `BOOT.NDS` (or whatever you renamed it to)

    1. Overwrite the existing files when asked.

    You don't need to copy the `_pico` folder or the autoboot files again, those don't change between AKMenu-Next versions.

=== "DSpico"

    1. Download the latest release of [AKMenu-Next DSpico Edition](https://github.com/coderkei/akmenu-next/releases/latest/download/akmenu-next-pico.zip).

    1. Extract the downloaded `akmenu-next-pico.zip` file with [7-Zip](https://www.7-zip.org/).

    1. Copy the following files/folders to the root of your SD card:

        - `_nds` folder
        - `BOOT.NDS`
        - `_picoboot.nds` (only if you autoboot AKMenu-Next)

    1. Overwrite the existing files when asked.

=== "Nintendo DSi"

    1. Download the latest release of [AKMenu-Next DSi Edition](https://github.com/coderkei/akmenu-next/releases/latest/download/akmenu-next-dsi.zip).

    1. Extract the downloaded `akmenu-next-dsi.zip` file with [7-Zip](https://www.7-zip.org/).

    1. Copy the following files/folders to the root of your SD card:

        - `_nds` folder
        - `akmenu-next.dsi`
        - `BOOT.NDS` (skip this if you use TWiLight Menu++)
        - `title` folder (only if you have AKMenu-Next installed as a HiyaCFW app)

    1. Overwrite the existing files when asked.

=== "Nintendo 3DS"

    1. Download the latest release of [AKMenu-Next 3DS Edition](https://github.com/coderkei/akmenu-next/releases/latest/download/akmenu-next-3ds.zip).

    1. Extract the downloaded `akmenu-next-3ds.zip` file with [7-Zip](https://www.7-zip.org/).

    1. Copy the following files/folders to the root of your SD card:

        - `_nds` folder
        - `akmenu-next.cia`
        - `BOOT.NDS` (skip this if you use TWiLight Menu++)

    1. Overwrite the existing files when asked.

    1. Install `akmenu-next.cia` with FBI again. You might need to restart your 3DS before the new version shows up.

## Updating nds-bootstrap

1. Download the latest release of [nds-bootstrap](https://github.com/DS-Homebrew/nds-bootstrap/releases/latest/download/nds-bootstrap.zip).

1. Extract the downloaded `nds-bootstrap.zip` file with [7-Zip](https://www.7-zip.org/).

1. Copy the *contents* of the zip into the `_nds` folder on your SD card, overwriting the old files.

!!! tip "Using nightlies"

    Want to try a nightly build? These come straight from nds-bootstrap's GitHub Actions now:

    1. Go to the [nds-bootstrap Actions page](https://github.com/DS-Homebrew/nds-bootstrap/actions/workflows/build.yml?query=branch%3Amaster+is%3Asuccess) and click the newest successful run.
    1. Scroll down to **Artifacts** and download `build`. You'll need to be signed in to GitHub for the download to show up.
    1. Extract the zip, then extract the `nds-bootstrap.7z` inside it with [7-Zip](https://www.7-zip.org/).
    1. Copy `nds-bootstrap-nightly.nds` into your `_nds` folder, next to the release version.

    Then set `nds-bootstrap version` to `nightly` in `Settings` > `Game loader settings`. You can keep both and flip between them, or just use the nightly for one game from its [per-game settings](using.md#per-game-settings).

## Updating Pico-Loader

1. Download the latest release of [Pico-Loader](https://github.com/LNH-team/pico-loader/releases/latest). Pick the one that matches your flashcart, same as when you installed it. If you're not sure, check the [Supported Platforms table](https://github.com/LNH-team/pico-loader#supported-platforms). DSpico users want `Pico_Loader_DSPICO.zip`.

1. Extract the downloaded zip with [7-Zip](https://www.7-zip.org/).

1. Copy the *contents* of the zip into the `_pico` folder on your SD card, overwriting the old files.
