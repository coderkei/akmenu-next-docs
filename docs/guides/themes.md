---
title: Themes
---

=== "Installing Themes"

    AKMenu-Next supports Acekard/AKAIO themes, Wood R4 themes, and themes made for AKMenu-Next.

    1. Open the [Wood R4/AKMenu Theme Repository](https://themes.flashcarts.net/akmenu/) and download a theme.
    2. Open the `.7z` archive with an extractor such as [7-Zip](https://7-zip.org/).
    3. Copy the theme folder from the archive to `_nds/akmenunext/ui` on your SD card.
    4. Put the SD card back in your flashcart or console and start AKMenu-Next.
    5. Press `START`, choose **Settings**, and select the theme you installed.
    6. Press **A** to save, then press **A** again to restart with the theme.

    !!! warning "Check the folder path"
        The theme folder must sit directly inside `_nds/akmenunext/ui`. For example, a theme named `HatsuneMiku` should be at:

        ```text
        _nds/akmenunext/ui/HatsuneMiku
        ```

        Do not leave it nested in a second folder such as `_nds/akmenunext/ui/HatsuneMiku/HatsuneMiku`. Selecting a nested theme can break the menu installation. If that happens, reinstall AKMenu-Next or edit `_nds/akmenunext/globasettings.ini` to select a default theme such as `zelda`.

=== "Creating Themes"

    ## Theme folder and image format

    Themes live under `_nds/akmenunext/ui`. Each theme's folder contains its artwork and settings. An installable theme needs its bitmap assets and a `uisettings.ini` with a `[global settings]` section. A `custom.ini` file is optional.

    Theme bitmap assets must be 16-bit BMPs in **X1 R5 G5 B5 (RGB 5:5:5)** format. In GIMP, choose **16 bit (X1 R5 G5 B5)** in the BMP export options.

    ## Configuration basics

    `uisettings.ini` controls interface colors, positions, sizes, and features such as covers. Optional `custom.ini` settings add items to the upper screen, including the DS username, date, custom text, and custom picture.

    Both files use INI format: a section name in square brackets followed by `key = value` lines. Put settings in the section for the feature they control. Coordinates and sizes are in screen pixels; color values use the DS packed 15-bit format (for example, `0x7fff` is white). Omitted settings use built-in defaults.

    This excerpt from Blue Skies' `uisettings.ini` sets interface and file-list colors, then positions and shows the clock:

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

    A setting only applies inside its section. For example, `x` and `y` under `[big clock]` position the clock; under `[date]`, they position the date. Set `show = 0` to hide an item and `show = 1` to display it where supported.

    ## UI colors and scroll indicators

    In `[global settings]`, these color keys control scroll indicators in scrollable settings, theme lists, Help, and About windows:

    | Key | Controls |
    | --- | --- |
    | `spinBoxNormalColor` | Chevron for a direction that cannot scroll farther |
    | `spinBoxTextColor` | Chevron for a direction that can scroll, and the scrollbar thumb where shown |
    | `spinBoxFrameColor` | Scrollbar outline beside the chevrons |

    ```ini
    [global settings]
    spinBoxNormalColor = 0x001f
    spinBoxTextColor = 0x7fff
    spinBoxFrameColor = 0x4210
    ```

    ## Clock and calendar

    Configure these sections in `uisettings.ini`:

    * `[big clock]`: `x`, `y`, and `show`.
    * `[am pm]`: `x`, `y`, `color`, and `show` for the AM/PM label in 12-hour mode.
    * `[calendar year]` and `[calendar month]`: `x`, `y`, and `show`.
    * `[calendar dayx]`: `x`, `y`, and `show` for a compact day number.
    * `[calendar day]`: `x`, `y`, `dw`, `dh`, `highlightColor`, and `show` for the month grid.

    Set the relevant `show` values to `0` if the design removes the calendar or needs that space clear. You can use a `[date]` overlay in `custom.ini` instead.

    ## Standard text and pictures (`custom.ini`)

    The standard text layer draws over the theme's upper-screen background. Colors use DS 15-bit values, and `show` is `0` or `1`.

    The `[user name]` section displays the username saved in DS system settings:

    ```ini
    [user name]
    x = 60
    y = 173
    color = 0x7fff
    show = 1
    ```

    The `[custom text]` section accepts `text`, `x`, `y`, `w`, `h`, `color`, and `show`. The `[custom picture]` section accepts `file`, `x`, `y`, and `show`.

    ## Date and time (`custom.ini`)

    The `[date]` section displays the system date. With `font = 0`, it uses standard text and does not require calendar number graphics:

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

    Supported `format` values are:

    | Value | Example |
    | --- | --- |
    | `DD/MM/YYYY` | `09/11/2026` |
    | `MM/DD/YYYY` | `11/09/2026` |
    | `YYYY/MM/DD` | `2026/11/09` |

    Set `showTime = 0` to hide the time. Otherwise, the time follows the DS clock's 12-hour setting: it uses a 12-hour style such as `11:45 PM` when enabled, or a 24-hour style such as `23:45` when disabled.

    Set `font = 1` to draw the date using digit sprites from `calendar/date_numbers.bmp`. The bitmap must be **9 pixels wide by 140 pixels high**, with ten 9-by-14 sprites stacked vertically in order from `0` to `9`. The selected `format` still determines the day, month, and year order. The bitmap does not draw slashes; a 9-pixel gap separates each field so the background can show the slash. Bitmap dates do not display the time, even if `showTime = 1`.

    ## Game covers

    AKMenu-Next can show a BMP cover on the top screen for `.nds`, `.dsi`, `.srl`, and `.ids` games. Put `.bmp` covers at the SD card root in `_nds/covers_code/` or `_nds/covers_name/`. AKMenu-Next first looks for a four-character game code, then for the ROM's filename without its final extension.

    To enable covers for a theme, add a `[cover]` section to its `uisettings.ini`:

    ```ini
    [cover]
    x = 140
    y = 44
    darken = 0
    fade = 0
    ```

    `x` and `y` position the cover. If either is omitted, the cover is centered on that axis. `darken` dims the whole top screen behind the cover (`0` is normal; `100` is black). `fade` makes the cover transparent (`0` is opaque; `100` is invisible). Both default to `0`. A theme without a `[cover]` section does not display covers. **Interface settings → Game covers** can disable or enable covers for themes that support them.

    If a cover BMP has four or more entirely black or transparent columns along its right edge, those columns are clipped. Some images from Pico-Cover use this convention.

    ## Theme music (`bgm.wav`)

    Add a `bgm.wav` to the theme folder alongside its images, for example `_nds/akmenunext/ui/blue skies/bgm.wav`. AKMenu-Next plays the track in a loop while the menu is open. **Interface settings → Theme music** controls playback.

    Use uncompressed RIFF/WAVE PCM audio in **16-bit signed, 22,050 Hz, mono** format. Audacity and FFmpeg can export audio in this format.
