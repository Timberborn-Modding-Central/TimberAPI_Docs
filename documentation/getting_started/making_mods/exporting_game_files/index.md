---
title: Exporting Game Files
permalink: /making_mods/exporting_game_files/
nav_order: 0
layout: page
has_toc: true
parent: Making Mods
---
# Exporting Game Files
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Prerequisites
- Installed Unity Editor
- Downloaded GUI version from: [https://github.com/AssetRipper/AssetRipper/releases](https://github.com/AssetRipper/AssetRipper/releases)   
    **Known working version: 0.2.1.1**
- Folder where it can Export files to.
    -   Note it will replace/remove all files in the folder!
- Separate Unity project for AssetRipper.    

## Instruction:  
1. Open Asset ripper  
1. Change Setting of Script Export format to **DLL Export without Renaming.**  
![Asset Ripper](/assets/images/assetripper/assetripper.png)
1. Select Open File and Select Timberborn.exe   
![Open File](/assets/images/assetripper/open_file.png)
1. Select Export All and select the folder where to Export files.  
![Export Files](/assets/images/assetripper/export_all.png)
1. Open Exported files when export is done.  
1. go to /Timberborn/ExportedProject and Rename Asset folder to Timberborn.  
1. Open renamed folder and Select MonoScript folder and delete it.
    - Can stop here if you just want to look at text files.  
1. Copy Renamed folder to Unity Projects Asset folder. 
1. Start Unity Editor.
    - it may crash or freeze with so many files to import then force close the editor.  
1. Open Thunderkit settings.  
![Thunderkit](/assets/images/assetripper/thunderkit.png)  
1. Open tab ThunderKit Settings and press Import.  
![Thunderkit](/assets/images/assetripper/thunderkit_import.png)  
1. Find model you want to check.
