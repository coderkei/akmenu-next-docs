---
title: Themes
---

# Themes

AKMenu-Next has an upgraded theme system. On top of everything classic themes could do, AKMenu-Next themes can have game covers, background music, their own file icons, and extra top-screen bits like the date and your DS username.

It can use three kinds of themes:

- AKMenu-Next themes, with all the extras above
- Acekard / AKAIO themes
- Wood R4 themes

Acekard and Wood themes work as they are, and you can add the new features to them yourself (see Creating Themes).

A few themes come with AKMenu-Next already (Blue Skies, Starlight and DSpico, each with a "Game Covers" version), and there are loads more online.

=== "Installing Themes"

    ## Installing a theme

    1. Download a theme:
        - For themes made for AKMenu-Next, have a look at the [AKMenu-Next theme repository](https://themes.flashcarts.net/aknext/).
        - For older Acekard/AKAIO/Wood R4 themes, try the [Wood R4/AKMenu theme repository](https://themes.flashcarts.net/akmenu/).
    2. Open the `.7z` archive with an extractor such as [7-Zip](https://7-zip.org/).
    3. Copy the theme's folder from the archive into `_nds/akmenunext/ui/` on your SD card.
    4. Put the SD card back in your flashcart or console and start AKMenu-Next.
    5. Press `START` and choose `Themes`.
    6. Highlight the theme you just installed and press `A` to pick it, then press `X` (`OK`).
    7. Say `Yes` when it asks to restart, and AKMenu-Next will reload with your new theme.

    ### The theme picker

    Themes are split into two groups: **Standard Themes** and **Game Cover Themes** (the ones that can show box art, see [game covers](#game-covers) below). Press `Right` on a group to open it and `Left` to close it. `B` backs out without changing anything.

    !!! warning "Check the folder path"

        The theme's folder has to sit directly inside `_nds/akmenunext/ui`. For example, a theme called `HatsuneMiku` should end up like this:

        ```text
        _nds/akmenunext/ui/HatsuneMiku/uisettings.ini
        ```

        A really common mistake is ending up with it nested one level too deep, like `_nds/akmenunext/ui/HatsuneMiku/HatsuneMiku/`, which happens when the archive has a folder inside a folder. A theme like that won't show up in the picker at all. Move the inner folder up a level and it'll appear.

    !!! note "If a theme is broken"

        If the theme you're using goes missing or turns out to be broken, AKMenu-Next will tell you and switch to another valid theme (Blue Skies if it can) so you're not left with a menu that won't boot. If you've got no valid themes at all, you'll get a message telling you to add one to `_nds/akmenunext/ui`.

    ## Game covers

    If you're using a theme that supports covers, AKMenu-Next can show a picture of the box art on the top screen when you highlight a game. The bundled "Game Covers" themes all support this.

    You'll need to get the cover images yourself and put them on your SD card. Covers are `.bmp` files, named either after the game's 4-letter game code or the ROM's file name. AKMenu-Next looks in these places, in this order:

    **DS games** (`.nds`, `.ndz`, `.dsi`, `.srl`, `.ids`)

    1. `_nds/covers_code/` using the game code, e.g. `_nds/covers_code/ASME.bmp`
    1. `_nds/covers_name/` using the file name, e.g. `_nds/covers_name/Super Mario 64 DS.bmp`
    1. `_pico/covers/nds/` using the game code (where Pico-Launcher keeps its covers)

    **GBA games** (`.gba`)

    1. `_nds/covers_code/`, then `_nds/covers_name/`, then `_pico/covers/gba/`, trying both the game code and the file name in each.

    The file name is the ROM's name without its extension, so `Super Mario 64 DS.nds` looks for `Super Mario 64 DS.bmp`. You can find a game's code by pressing `Y` on it in AKMenu-Next.

    If you already have covers set up for Pico-Launcher, AKMenu-Next will just use them, no need to copy anything.

    !!! tip "Cover image tips"

        - Any normal uncompressed `.bmp` works (16, 24 or 32-bit, or paletted). 32-bit BMPs can have transparency.
        - Keep them small. Anything bigger than 256×192 gets cropped, and files over 1MB or 1024 pixels in either direction are skipped.
        - Some covers (including a lot from Pico-Cover) have a strip of black or transparent padding on the right. If there are 4 or more empty columns on the right edge, AKMenu-Next trims them off for you.

    You can turn covers off with `Settings` > `Interface settings` > `Game covers`.

    ## Theme music

    Some themes come with background music. You can turn it off with `Settings` > `Interface settings` > `Theme music`.

=== "Creating Themes"

    Use [AKTheme Studio](https://coderkei.github.io/akmenu-next-theme-editor/) to create custom themes for AKMenu-Next.

    If you want to edit the theme files by hand, start by copying one of the bundled themes and changing things bit by bit.

    ## What's in a theme

    A theme is just a folder inside `_nds/akmenunext/ui/`. The folder name is the theme name that shows up in the picker. At minimum it needs a `uisettings.ini` with a `[global settings]` section, plus its images.

    Here's what a full theme folder looks like:

    ```text
    MyTheme/
    ├── uisettings.ini      <- colours, positions, and features (required)
    ├── custom.ini          <- extra top-screen bits like username and date (optional)
    ├── upper_screen.bmp    <- top screen background (256×192)
    ├── lower_screen.bmp    <- bottom screen background (256×192)
    ├── title_left.bmp      ┐
    ├── title_bg.bmp        ├ window title bars
    ├── title_right.bmp     ┘
    ├── btn2.bmp, btn3.bmp, btn4.bmp   <- buttons of different widths
    ├── spin_btn_left.bmp, spin_btn_right.bmp
    ├── brightness.bmp      <- brightness button
    ├── folder_up.bmp       <- folder up button
    ├── menu_bg.bmp         <- start menu background
    ├── card_icon_blue.bmp  <- little SD activity icon (max 32×32)
    ├── progress_wnd.bmp, progress_bar.bmp
    ├── calendar/
    │   ├── clock_numbers.bmp, clock_colon.bmp
    │   ├── day_numbers.bmp, year_numbers.bmp
    │   └── date_numbers.bmp (optional, see the date section below)
    ├── icons/              <- optional theme-specific file icons
    └── bgm.wav / bgm.bcstm <- optional music
    ```

    The two screen backgrounds have to be exactly 256×192, and nothing can be bigger than the screen (number strips can be up to 10 screens tall).

    ### Image format

    All theme images must be 16-bit BMPs in **X1 R5 G5 B5** format (also called RGB 5:5:5). That's what the DS draws natively. In GIMP, when you export as BMP, open the advanced options and choose **16 bit (X1 R5 G5 B5)**.

    Pure black (`#000000`) pixels are treated as transparent. If you actually want black, use a very dark grey like `#080808` instead.

    ### Theme icons

    Put DS banner `.bin` files in your theme's `icons/` folder to give it its own folder, save, favourites (and so on) icons. They use the same file names as the ones in `_nds/akmenunext/icons/`, so copy that folder into your theme and edit from there. Any icon your theme doesn't include falls back to the global one.

    Players can ignore theme icons with `Settings` > `Interface settings` > `Icon source`.

    ## Config files

    `uisettings.ini` controls the interface: colours, where things go, how big they are, and whether features like covers are switched on. `custom.ini` is optional and adds extra things to the top screen, like the DS username, the date, your own text, or a picture.

    Both are normal INI files: a section name in square brackets, then `key = value` lines under it. Positions and sizes are in pixels. Anything you leave out just uses the built-in default.

    A setting only applies to the section it's in, so `x` and `y` under `[big clock]` move the clock, while `x` and `y` under `[date]` move the date. Most sections also have `show = 1` (visible) or `show = 0` (hidden).

    Here's a chunk of Blue Skies' `uisettings.ini` as an example:

    ```ini
    [global settings]
    formBodyColor = 0x5e06
    formTextColor = 0x7fff
    spinBoxNormalColor = 0x7fff
    spinBoxTextColor = 0x4d80
    spinBoxFrameColor = 0x35ad

    [main list]
    textColor = 0x2d6b
    selectionBarColor1 = 0x20e2
    selectionBarColor2 = 0x1482
    selectionBarOpacity = 100

    [big clock]
    x = 6
    y = 94
    show = 1
    ```

    ### Colours

    Colours are written as DS 15-bit values in hex. Each of red, green and blue goes from 0 to 31, and they're packed together like this:

    ```text
    colour = red + (green × 32) + (blue × 1024)
    ```

    A few to get you going:

    | Colour | Value |
    | --- | --- |
    | White | `0x7fff` |
    | Black | `0x0000` |
    | Red | `0x001f` |
    | Green | `0x03e0` |
    | Blue | `0x7c00` |
    | Mid grey | `0x4210` |

    If you've got a normal 0–255 colour from an image editor, divide each channel by 8 (and round down) to get the 0–31 value.

    ### Scroll indicators

    These keys in `[global settings]` colour the little scroll arrows and bars you see in the settings, theme list, Help and About windows:

    | Key | Controls |
    | --- | --- |
    | `spinBoxNormalColor` | The arrow for a direction you can't scroll any further in |
    | `spinBoxTextColor` | The arrow for a direction you *can* scroll in, plus the scrollbar thumb |
    | `spinBoxFrameColor` | The outline of the scrollbar |

    ```ini
    [global settings]
    spinBoxNormalColor = 0x001f
    spinBoxTextColor = 0x7fff
    spinBoxFrameColor = 0x4210
    ```

    ### Clock and calendar

    These all go in `uisettings.ini`:

    | Section | Keys | What it is |
    | --- | --- | --- |
    | `[big clock]` | `x`, `y`, `show` | The big clock, drawn using `calendar/clock_numbers.bmp` |
    | `[am pm]` | `x`, `y`, `color`, `show` | AM/PM label, only shown when the 12-hour clock is on |
    | `[calendar year]` | `x`, `y`, `show` | The year |
    | `[calendar month]` | `x`, `y`, `show` | The month |
    | `[calendar dayx]` | `x`, `y`, `show` | A small day number |
    | `[calendar day]` | `x`, `y`, `dw`, `dh`, `highlightColor`, `show` | The month grid. `dw`/`dh` are the size of each day cell |

    If your design doesn't have room for the calendar, set the `show` values to `0` and use a `[date]` in `custom.ini` instead.

    ## Extra top-screen bits (`custom.ini`)

    Everything in `custom.ini` is drawn on top of `upper_screen.bmp`.

    ### Username

    Shows the name from the console's system settings:

    ```ini
    [user name]
    x = 60
    y = 173
    color = 0x7fff
    show = 1
    ```

    ### Your own text and picture

    `[custom text]` takes `text`, `x`, `y`, `w`, `h`, `color` and `show`.

    `[custom picture]` takes `file`, `x`, `y` and `show`. `file` is the full path to the BMP from the root of the SD card, e.g. `/_nds/akmenunext/ui/MyTheme/avatar.bmp`. It has to be a small image, the file can't be bigger than 10KB (roughly 64×64).

    ### Date and time

    `[date]` shows the current date, and the time if you want it. With `font = 0` it uses normal text, so you don't need any extra graphics:

    ```ini
    [date]
    x = 8
    y = 148
    color = 0x7fff
    show = 1
    format = DD/MM/YYYY
    showTime = 1
    font = 0
    ```

    The `format` can be:

    | Value | Example |
    | --- | --- |
    | `DD/MM/YYYY` | `09/11/2026` |
    | `MM/DD/YYYY` | `11/09/2026` |
    | `YYYY/MM/DD` | `2026/11/09` |

    `showTime = 0` hides the time. Otherwise it follows the player's `12-hour clock` setting, so it shows either `23:45` or `11:45 PM`.

    #### Using your own digits

    Set `font = 1` to draw the date with your own number graphics from `calendar/date_numbers.bmp` instead:

    - The image must be **9 pixels wide and 140 pixels tall**: ten 9×14 digits stacked on top of each other, `0` at the top down to `9` at the bottom.
    - The slashes aren't drawn. Instead there's a 9 pixel gap between each part, so you can put slashes (or dots, or whatever you like) into your background image.
    - `format` still decides the order of day, month and year.
    - The time isn't shown in this mode, even with `showTime = 1`.

    ## Supporting game covers

    To make your theme show covers, add a `[cover]` section to its `uisettings.ini`. Themes without one never show covers, and they'll be listed under Standard Themes instead of Game Cover Themes.

    ```ini
    [cover]
    x = 140
    y = 44
    darken = 0
    fade = 0
    ```

    | Key | What it does |
    | --- | --- |
    | `x`, `y` | Where the cover's top left corner goes. Leave one out to centre the cover on that axis. |
    | `darken` | Darken the whole top screen behind the cover, from `0` (normal) to `100` (black). Nice for making covers pop on a busy background. |
    | `fade` | Make the cover see-through, from `0` (solid) to `100` (invisible). |

    Most people make two versions of their theme, one with covers and one without, since covers usually need space on the top screen that the calendar would otherwise use.

    ## Theme music

    Put music files straight in the theme folder, next to the images. AKMenu-Next looks for:

    - `bgm.bcstm` and `bgm1.bcstm` up to `bgm9.bcstm`
    - `bgm.wav` and `bgm1.wav` up to `bgm9.wav`

    So that's up to 20 songs per theme. Each time the music starts, one is picked at random and looped. If a file can't be played, it's skipped and another one is picked.

    ### BCSTM (recommended)

    BCSTM is the 3DS music format, and it's the better choice: the files are much smaller than WAV, and it supports loop points, so a song can have an intro that plays once and then loop the rest.

    - DSP-ADPCM, mono or stereo, up to 48,000 Hz. 32,000 Hz is a good choice, since the DS outputs at about 32.7 kHz anyway, so going higher just wastes space.
    - Loop points saved in the file are used.
    - Wii U `.bfstm` files won't work.
    - Tools like [VGAudio](https://github.com/Thealexbarney/VGAudio), [LoopingAudioConverter](https://github.com/libertyernie/LoopingAudioConverter) or [μ-wave](https://kazuki-4ys.github.io/web_apps/mu-wave/) (which runs in your browser) can make them.

    ### WAV

    - Uncompressed RIFF/WAVE PCM, 16-bit signed, mono or stereo. 22,050 Hz mono keeps the size down.
    - Always loops from the very start.
    - Audacity or FFmpeg can export this. For example, with FFmpeg:

        ```bash
        ffmpeg -i song.mp3 -ac 1 -ar 22050 -c:a pcm_s16le bgm.wav
        ```

    !!! note

        If you're sharing your theme, please only include music you're allowed to share, and credit it (the bundled themes include a `Music Attribution.txt` for this). AI-generated art and music aren't accepted for themes submitted to the AKMenu-Next repo.
