---
title: Manual Install
permalink: /using_mods/manual_install/
nav_order: 0
layout: page
has_toc: true
parent: Using Mods
---

# Manual Installation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


# Manual Installation (guide for Windows/Steam)
Source: [Installing BepInEx](https://docs.bepinex.dev/articles/user_guide/installation/index.html)
{: .fs-1 .mt-n5 .mb-0 }
All current mods for Timberborn use the framework [BepInEx](https://docs.bepinex.dev/index.html), which provides a great starting point for loading and interacting with the game!

1. Download the latest [BepInEx release](https://github.com/BepInEx/BepInEx/releases)
2. Move everything of step 1 to the local timberborn files.\
   ![My helpful screenshot](/assets/images/timberborn_local_files.png)
5. Open steam and run Timberborn

# Manual Installation (guide for Mac/Steam)
Source: [Installing BepInEx](https://docs.bepinex.dev/articles/user_guide/installation/index.html)
{: .fs-1 .mt-n5 .mb-0 }

All current mods for Timberborn use the framework [BepInEx](https://docs.bepinex.dev/index.html), which provides a great starting point for loading and interacting with the game!

1. Download the latest [BepInEx release](https://github.com/BepInEx/BepInEx/releases)
2. Move everything of step 1 to `~/Library/Application Support/Steam/steamapps/common/Timberborn`
3. Open `run_bepinex.sh` and edit it to have `executable_name="Timberborn.app"`
4. Open terminal, type `chmod +x <drag run_bepinex.sh to terminal>`
5. Open steam and set the Launch Options for Timberborn to: `"<copy the full path to the run_bepinex>" %command%` and run it.  
   example: `"/Users/<User>/Library/Application Support/Steam/steamapps/common/Timberborn/run_bepinex.sh" %command%`

# Installing mods
1. Download mods at [ThunderStore](https://timberborn.thunderstore.io/package/)
2. Locate to `~/Library/Application Support/Steam/steamapps/common/Timberborn/BepInEx/plugins`
3. \*Create a folder for each mod you downloaded (If the mod hasn't have one)
4. Move all files inside the downloaded mod to the newly created folder.  
   \*Optional step to prevent conflicts with other mods

**Note:** You likely need [TimberAPI](https://timberborn.thunderstore.io/package/Timberborn_Central/TimberAPI/)

