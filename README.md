# The Homebrew Channel Plus

This repository contains the public release of the source code for
The Homebrew Channel Plus.

# Improvements
Possible improvements and fixes!

## Bugfixes (High Priority)

* **Real Wii testing**
  * Verify behavior on actual Wii hardware (not just Dolphin). I meaaaan it should work but it is slightly different code, so it is worth testing.
  * Fix timing, IOS permissions, USB initialization, etc. (if any)

<!--* **NAND save & theme bugs**
  * Ensure themes and save data work properly when launched as a channel with correct identity.-->

* **SD/USB handling**
  * Handle missing or corrupt SD/USB devices gracefully.
  * Support hot-swapping if possible.

* **Stability**
  * Audit for memory leaks, and rare crashes.

## Quality of Life and New Features (Medium Rare ~~Steak~~)

* **UI overhaul**
  * Modern grid/list view, better scaling for icons/text.

<!-- * **Sorting & filtering**
  * Alphabetical, last used, categories (games, emulators, tools). -->

* **Search bar**
  * Quickly find an app if there are dozens installed.

<!--* **Per-app settings**
  * Override video mode, language, or aspect ratio per app.-->

* **Theme engine refresh**
  * Easier to install/preview themes, community theme packs, like a store.
<!-- theme resources: https://wiibrew.org/wiki/Homebrew_Channel/Themes -->

* **Faster boot**
  * Optimize shit like directory scanning and startup routines.

* **Auto Updater**.
  * Just as the title says!

## New Features

* **Network booting**
  * Launch homebrew over Wi-Fi (HTTP/SMB/NFS).

* **Auto-updater / repo browser**
  * Have a app store to download or update apps from within HBC, just like the [Homebrew Browser](https://oscwii.org/library/app/homebrew_browser).

* **Wii U vWii support**
  * Graceful handling if run under Wii U’s vWii mode, like is there any issues?

* **Plugin system**
  * Sidebar widgets (system info, FPS counter, quick tools).

* **Safe Mode**
  * If a theme or sidebar widget crashes HBC, revert to defaults automatically.

* **More Animations and transitions**
  * CUSTOMISABLE ANIMATIONS AND TRANSITIONSSSSS!!!!!! (theme options)
  
## Integration with outside sources
* **Companion desktop tool** (Linux/Windows/macOS) to manage SD/USB contents.
* **Cloud sync** (experimental) for saves/configs/apps via SMB/NFS.
* **Notifications** for something... I don't know what though, but it would have a popup at the top.

Included portions:

* The Homebrew Channel Plus
* Reload stub
* Banner
* PyWii (includes Alameda for banner creation)
* WiiPAX (LZMA executable packer)

Not included:

* Installer (wtf is even the installer)

Note that the code in this repository differs from the source code used to build
the official version of The Homebrew Channel, which includes additional
protection features (i.e. we had to add reverse-DRM to stop scammers from
selling it).

This code is released with no warranty, and hasn't even been tested on a real
Wii, only under Dolphin (yes, this release runs under Dolphin).

## Build instructions

You need **devkitPPC** and **libogc** installed, and the **DEVKITPRO**/**DEVKITPPC** environment
variables correctly set. Use the latest available versions. Make sure you have
**libogc**/**libfat**, and also install the following 3rd party libraries:

* `zlib`
* `libpng`
* `mxml`
* `freetype`

You can obtain binaries of those with
[devkitPro pacman](https://devkitpro.org/wiki/devkitPro_pacman). Simply use

    sudo (dkp-)pacman -S ppc-zlib ppc-libpng ppc-mxml ppc-freetype

Additionally, you'll need the following packages on your host machine:

* `pycryptodomex` (for `PyWii`)
* `libpng headers` (`libpng-dev`)
* `gettext`
* `sox`

The build process has only been tested on Linux. You're on your own if you
want to try building this on OSX or Windows.

You'll need the Wii common key installed as `~/.wii/common-key`.

First run '`make`' in wiipax, then '`make`' in channel. You'll find a .wad file
that you can install or directly run with Dolphin under
channel/title/channel_retail.wad. You'll also find executable binaries under
channel/channelapp, but be advised that the NAND save file / theme storage
features won't work properly if HBC isn't launched as a channel with its
correct title identity/permissions.

## License

Unless otherwise noted in an individual file header, all source code in this
repository is released under the terms of the GNU General Public License,
version 2 or later. The full text of the license can be found in the COPYING
file.
