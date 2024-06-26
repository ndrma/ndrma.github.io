---
title: 'Unreal+houdini+linux'
date: 2024-04-16T22:31:58+01:00
draft: false
ShowReadingTime: true
ShowToc: true
summary: ""
hipfile: hip/01_Spiral.hiplc

cover:
    image: /blog/images/unreal_engine.png
    alt: "Cover Photo"
    caption: ""
    relative: true
tags: ["UE5","Unreal","linux","vfx","houdini"]
categories: ["houdini", "Unreal", "snippets","linux", "notes"]
---
### ⬛️  links and before we begin

1. https://github.com/EpicGames/UnrealEngine?tab=readme-ov-file#getting-up-and-running
2. https://www.sidefx.com/forum/topic/61839/?page=1#post-404735
3. https://www.youtube.com/watch?v=TOpdnwBxEq4 (unlisted video, for UE4, but helpful stuff, sourcing houdini environment (the most useful part) at around 27:40)
4. during houdini installation, choose the plugins you'll want / need, otherwise install those now for the version you're on (a lot of the time, the most recent bleeding edge version won't play well with compiling alongside UE)
5. https://www.youtube.com/watch?v=600RgBneV_A (newer video, Manjaro base, UE5.1)

### ⬛️  First things
<br />

* make the directory for UE5 and switch to it
* ``` git clone git@github.com:EpicGames/UnrealEngine.git ```
* now in the UE5 directory ```./Setup.sh```
* then find the plugin for unreal at ```/opt/sidefx/houdini_engine``` (you need to plugin that corresponds to the current version of houdini in the system, if you remove that version it will break the integration)
* get the ```HoudiniEngine``` folder and copy it in the ```Plugins/Runtime``` folder of UE5
* **NOW** it is important to initialize the houdini environment before the next step so that when the make files are generated it knows what to look for
```
cd /opt/hfsX
source houdini_setup
The Houdini 20.0.653 environment has been initialized.
```
* back in the top directory ``` ./GenerateProjectFiles.sh``` \[With the environment initialized you shouldn't get any errors at the generate script\]
* ```make``` (it shouldn't require sudo)
* a lot of the times there might be some error in the UE make that just reks all of it. That's 99% the houdini engine plugin. 1st try removing it from the directory and recompiling, it should go faster and without errors.
* Then is the troubleshooting, have to find a houdini version that UE5 agrees with and wants to compile. So off you go!
* after compiling has finished, and all has gone well, need shortcuts for rofi now


### ⬛️  regarding updates and changes

soon(TM)
