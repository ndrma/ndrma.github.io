---
title: 'linux_things'
date: 2024-04-16T20:23:26+01:00
draft: false
ShowReadingTime: true
ShowToc: true
summary: ""
hipfile: hip/01_Spiral.hiplc

cover:
    image: /blog/images/mint.jpg
    alt: "Cover Photo"
    caption: ""
    relative: true
tags: ["linux","vfx"]
categories: ["linux", "notes"]
---
While using linux for vfx work I've had to do some general maintenance stuff, wrote the steps so that I understand the process better myself. I use linux mint btw.

### ⬛️  Moving /home (and some partitioning that was needed)
<br />

This guide is the source of what I did: https://forums.linuxmint.com/viewtopic.php?p=2192189#p2192189
It's written by a well respected member of the linux mint forums (rene, thank you), it's really solid.

The guide being solid is no substitute to having backups and timeshifts, so do those.
Using [pika](https://gitlab.gnome.org/World/pika-backup) lately and really liking it.
<br />
<br />
* restart (or shutdown+power up again) and don't login
* at the login screen `Ctrl+Alt+F1` to bring up the console
* login as root, or use *sudo* before the commands
* run ```mount /dev/nameofyourdisk /mnt```
* run ```df``` to check if the correct partition is mounted
* copy your home directory with ```rsycn -av /home/ /mnt/``` (this will take some time, and a lot of weirdness on the screen if your home is quite big also make sure before you run this that it's the correct drive with the correct mount)
* after this finishes run ```rm -r /home```
* then run ```mkdir /home```
* alternatively you can do ```mv /home /home.old && mkdir /home```
* do a ```blkid``` to find your partition's UUID, note it down and
* run ```nano /etc/fstab``` add a line with ```UUID (code)   /home     ext4    defaults   0   2```
* ```umount /mnt && mount /home``` (no output here is success)
* ```df``` to verify mount
* ```exit``` the console
* ```Ctrl+Alt+F7``` to return to the graphical login

<br />
In my case the mounting went weird (and the editing of the fstab part) because it kept erroring out because home remained mounted. I rebooted, started from a live Mint image, edited the fstab and rebooted and the system worked!

### ⚫️  Creating the partition on the disk that is both filesystem and /home currently.
<br />
In my case, I had a whole nvme, where I'd thrown everything in (assigning /home to a separate partition is easier to do during the initial format)

so in order to partition you can't do it on a live system (and Gparted live PLEASE NO)

* rebooted with a Mint installation media
* started Gparted
* found out I need to remove quite a few files from the current /home so that I could reduce it to a reasonable number (can't partition lower than the current occupied space)
* offloaded files
* restarted the process and created a partition I labelled home, ext4 like my file system
* label helped with identifying it at the ```blkid``` list.
* waited for the whole thing to finish and started the process above
<br />

**Good luck!**


### links
* https://easylinuxtipsproject.blogspot.com/p/1.html

