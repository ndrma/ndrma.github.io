---
title: 'void setup from zero'
date: 2026-05-20T20:23:26+01:00
draft: false
ShowReadingTime: true
ShowToc: true
summary: ""
hipfile: hip/01_Spiral.hiplc

cover:
    image: /blog/images/jupiter.png
    alt: "Cover Photo"
    caption: ""
    relative: true
tags: ["linux","alt","dwm","void"]
categories: ["linux", "notes"]
---
Setting up an alternative, more open distribution, as well as an alternate desktop environment experiment.
Also checking to see how dwm and void and worst of all nvidia, will behave in a different setup.

Maybe a fallback, maybe not. 

### ⬛️  initial install
<br />

Alright so during the initial install from the base iso (extremely minimal) a couple of things of notice:

* ```EFI needs 1G, setup as EFI boot, vfat, MOUNT at /boot/efi```
* ```/ is required, ext4```
* ```/home can be separate, ext4```
<br />
If GRUB crashes at the end of the installation it's probably due to some mismatch in the initial installation where it doesn't see/find the steps it needs to install. If all is setup correctly (and secureboot etc hasn't messed something up) chroot and grub-install MIGHT be a solution.
<br />

### ⚫️  we have the user, the admin, and a tty
<br />
alright so here, after updates and **xbps** has been updated too we got the terminal and basically nothing besides bash.

before we get to dwm, need a few things:

* xinit, xorgminimal, xauth

 ```sudo xbps-install -S xorg-minimal xauth xinit```

* xorg fonts, and a video driver *to be updated with nvidia instructions (soon tm)*

 ```sudo xbps-install -S xorg-fonts font-misc-misc xf86-video-vesa```

After these, we got most stuff, time to get to the dwm things.
<br />
This dwm install is based through FAUN-Dev Community guide on medium, link at the end.

**Void packages (case sensitive):**

 ```
sudo xbps-install base-devel libX11-devel libXft-devel libXinerama-devel freetype-devel fontconfig-devel
 ```

**Might as well grab micro here:**

 ```
sudo xbps-install micro
 ```

**step 1: clone**
 ```
mkdir .suckless
cd .suckless
 ```
grab dwm (provisional until personal repo/config is up)
 ```
git clone https://git.suckless.org/dwm
git clone https://git.suckless.org/st
git clone https://git.suckless.org/dmenu
 ```

**step 2: compile**
 ```
cd .suckless
cd dwm
make
sudo make clean install
cd..
cd st
make
sudo make clean install
cd ..
cd dmenu
make
sudo make clean install`
cd
 ```
**step 3: starting**

If you’re using startx, simply add exec /usr/local/bin/dwm at the end of your .xinitrc file on Linux, or at the end of your .xsession file on OpenBSD.

 ```
touch ~/.xinitrc
echo "exec dwm" > ~/.xinitrc
 ```
startx should now get into dwm, shift+alt+enter: st terminal, shift+alt+q: exit dwm (provisional until customized)
**Good luck!**


### links
* https://archive.is/dD9qc
* www.suckless.org
* https://www.youtube.com/watch?v=l-f5KgibVfI penguin (good)
* https://www.youtube.com/watch?v=7l9AuRU9ax4&t=112s
