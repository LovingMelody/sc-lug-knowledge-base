# Welcome, Space Penguins!

This wiki is a collection of information on how to run Star Citizen on Linux, as well as our tips and tricks!

🐧 Join us! https://robertsspaceindustries.com/orgs/LUG  

🗨 Discord: https://discord.gg/meCFYPj  
😎 Matrix space: https://matrix.to/#/#SCLUG:matrix.org  

## Contents
* [Quick-Start Guide](Quick-Start-Guide)
* [Manual Installation](Manual-Installation)
* [Troubleshooting](Troubleshooting)
* [Performance Tuning](Performance-Tuning)
* [Tips and Tricks](Tips-and-Tricks)
* [Sticks, Throttles, & Pedals](Sticks,-Throttles,-&-Pedals)

## News

#### Game Updates

> (Oct 24, 2023) **Installer Error Code 256**  
> - Inspect install log for failed winetricks downloads or sha256 mismatch and note the URL of the files being downloaded and its destination in winetricks' cache
> - Download each file manually to its destination in winetricks' cache
> - Use winetricks to ensure that the prefix is set to Win10 mode
> - Proceed with lug-helper installer

> (Mar 11, 2023) **3.18 Mouse/Cursor Issues**  
> - The 3.18 update caused mouse and view snapping issues for most Penguins using Wayland. We recommend installing Gamescope as a workaround or using Xorg.
> - **Note for Nvidia users:** Gamescope may not work on your hardware. See this [known issue report](https://github.com/ValveSoftware/gamescope/issues/526).
> - A possible fix to get Gamescope working on Nvidia: `Right click the game->Configure->System options->Game execution->Environment variables` then find or create `__GL_THREADED_OPTIMIZATIONS` in the left column and change/set it to `0` in the right column.
> - After installing Gamescope, enable it in Lutris: `Right click the game->Configure->System options->Gamescope->Enable Gamescope`. Then, set `Output Resolution` to your monitor's native resolution, ie `1920x1080`.
> - If you're using a version of gamescope newer than **3.11.51**, an additional Gamescope setting is required. Set `Relative Mouse Mode` to on
> - Other Gamescope settings that may be required depending on your system: `Window Mode` set to `Fullscreen` if it doesn't launch fullscreen, `-g` in `Custom Settings` to grab keyboard
> - Depending on your system, `Prefer System Libraries` may need to be enabled or disabled in Lutris
> - If this doesn't work, you will need to switch to Xorg instead of Wayland.

> (Jan 27, 2023) **RSI Launcher v1.6.2 JavaScript error**  
>
> Special configuration is needed in Lutris or you will receive a JavaScript error. See [CIG's announcement in Spectrum](https://robertsspaceindustries.com/spectrum/community/SC/forum/1/thread/upcoming-launcher-update-for-linux-users/5693728  )
>
> **Solution 1:**
> - **After the launcher updates,** all Penguins must configure the following:
>   - `Right click the game->Configure->Game options` add `--no-sandbox` to the Arguments
>   - In `System options`, make sure Advanced options is on then enable `CLI mode`
>
> **Solution 2:**
> - **If this does not fix the problem**, revert the above changes and install the latest GloriousEggroll runner, available in our Helper

> (Jan 27, 2023) **Fresh installs fail to create needed directories**
> - This has been resolved in the latest version of our [Helper](https://github.com/starcitizen-lug/lug-helper/releases) for new installs.
> - For existing or manual installs, run the following command to create the necessary directory structure for both the LIVE and PTU environments. Adjust the wine prefix path if installing to a non-default location:  
> ```
> mkdir -p "/home/$USER/Games/star-citizen/drive_c/Program Files/Roberts Space Industries/StarCitizen/"{LIVE,PTU}
> ```


#### General News
> (Nov 11, 2023) **Failed to Initialize Dependencies**
> - If you are on a rolling release distro and using Gamescope, you may receive this error due to a bug in Gamescope v3.12.7. See [this Github issue](https://github.com/ValveSoftware/gamescope/issues/984) for more info.
> - To fix: Install the git release of Gamescope or downgrade to 3.12.5 until the fix is released to stable.

> (May 8, 2023) **Wine 8**
> - Wine 8.x runners may not be compatible with prefixes created by previous Wine 7.x runners. If you experience inexplicable frame drops, crashes, or other issues after switching to an 8.x runner, try re-creating your wine prefix. You may copy out the `data.p4k` file beforehand to avoid a complete game redownload.

#### Nvidia News
> (Dec 12, 2023) **Graphical artifacts from previous frames on 545 drivers**
> - If you are experiencing previous frames appearing on your screen, downgrade to the latest 535 drivers
> - Latest affected driver tested: 545.29.06
> - Latest 535 driver test: 535.146.02

> (Oct 9, 2023) **Crash when taking shield damage in-game***
> - There is a shield rendering bug that causes the game to crash. It seems to affect 1000 series cards.
> - There is currently no known workaround other than switching cards. We recommend AMD.

> (Aug 10, 2023) **Driver v535.98 may break vulkan, steam, and/or everything**
> - If you are affected by this, downgrade to v535.86 to fix.

> (Jan 27, 2023) **Required DXVK version**
> - DXVK 2.1 may resolve issues Penguins had with previous versions of DXVK and may perform better without async.
> - For DXVK 2.0 and prior, Penguins with RTX cards should use [gnusenpai DXVK v1.10.1 or later](https://github.com/gnusenpai/dxvk/releases) to fix the `corrupted size vs. prev_size` error/crash. Can be installed manually or from the LUG helper.

> (Nov 17, 2022) **DXVK 2.0**
> - DXVK 2.0 changes the way shaders are handled on some Nvidia cards and may provide better performance than async (see the [release notes](https://github.com/doitsujin/dxvk/releases/tag/v2.0)). If you have worse performance on 2.0, remove the the `DXVK_ASYNC=1` environment variable.
> - DXVK 2.0 requires Nvidia driver **v510.47.03** or later, but **v520.56.06** or later is recommended.


#### Easy Anti-Cheat

> (March 24, 2023) **GlorousEggroll Runners**
> - GE runners since Wine-GE-Proton7-41 include an EAC workaround by default for Star Citizen. It will be enabled automatically for new installs. To enable it for existing installs, see our EAC workaround [wiki section](Tips-and-Tricks#easy-anti-cheat-workaround).

> (Feb 12, 2022) **Easy Anti-Cheat is live.**
> - CIG is aware of the problem but there is still no ETA. There are currently no consequences that we are aware of for using the workaround, but CIG has suggested that eventually people will be kicked for tripping EAC. To apply the workaround, use the [LUG Helper](https://github.com/starcitizen-lug/lug-helper).
