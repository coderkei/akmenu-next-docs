---
title: Running DSiWare On AKMenu-Next
---

### DSpico with AKMenu-Next (DSpico only)

!!! note

    This requires a DSpico and only works if your DSpico is booted on a DSi or 3DS. It will not load DSiWare on the Original DS or DS Lite.

1. You need to acquire a copy of the DSi NAND files. If you have a DSi with HiyaCFW, you can copy the files from your DSi's SD card for this. If you do not have HiyaCFW, you can use GodMode9i booted on your DSpico to copy the files needed from the `nand:/` drive on it. GodMode9i offers a Copy & Paste functionality to do this.

1. From your DSi NAND files, copy the below folders & files to the DSpico SD card:

    - `photo`
    - `shared1`
    - `shared2`
    - `sys`
    - A copy of the Nintendo DS ARM7 BIOS Dump inside the `_pico` folder named as `biosnds7.rom`. (You may need to rename it to this). [Follow this guide](https://wiki.ds-homebrew.com/ds-index/ds-bios-firmware-dump) for obtaining a BIOS dump.

1. Boot up AKMenu-Next and ensure that the `Game Loader` inside the settings is set to `Pico-Loader` and that you have your DSpico booted on a DSi or 3DS.

1. After doing the above, Add your DSiWare with the `.nds` file extension. You can now run DSiWare on your DSpico!

!!! note

    If your DSiWare dump is a file with no file extension, you can change the filename and add `.nds` to the end to get AKMenu-Next to pick it up.