---
layout: article
title: Reinstall GRUB Bootloader
description: >
    Official directions to Reinstall Grub Bootloader.
keywords:
    - Support
    - Grub
    - Bootloader
    - Refresh
    - Reinstall
    - System76
---


GRUB is the Ubuntu bootloader. It takes care of getting the operating system started up. It is also responsible for allowing the user to select between multiple operating systems at boot. Sometimes, GRUB can begin acting funny, and it may not let you boot into Ubuntu to fix the problem.

### Important Note About GRUB Updates!

If you need to configure grub-pc (for example, after an update), installing grub to all devices will break GRUB. You will need to install to /dev/sda (_not_ /dev/sda1) **only**. Installing everywhere **will** break the bootloader.

## 1. Create an Ubuntu Live Disk

Create an Installation USB Drive  | Create an Installation DVD
--------------------------------- | ---------------------------
[Using Ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu) | [Using Ubuntu](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-ubuntu)
[Using Windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) | [Using Windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
<small>OS X can't make a System76-compatible USB Drive</small>| [Using OS X](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-mac-osx)

## 2. Reinstall GRUB Bootloader

Once you have the disk made, reboot your system. You'll need to tell the computer to boot from the Live Disk. When you see the System76 logo on the screen: 

Laptops  | Desktops
-------- | --------
Hold F7 or F1 | Hold F8 or F10

Open a terminal  (search _Terminal_ from the Ubuntu dash or press <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>) and run the following commands:

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
grub-install --force /dev/sda
```

After this, reboot your computer, removing the disk when prompted, and Ubuntu should boot.

### Common Errors

Often, the fourth command (`sudo cp /etc/resolv.conf /mnt/etc/resolv.conf`) will return an error, stating that the file does not exist. This is not an issue, and you can proceed. Alternatively, connecting to the internet from the LiveCD should create this file.

If the chroot command returns with the error "chroot: cannot run command `/bin/bash': Exec format error", this probably indicates that the Ubuntu Install CD is not compatible with that of the installed system.

For example, the error is most frequently seen when trying to chroot to a 64-bit system (eg. amd64) from a 32-bit Install CD (eg. x86).

The solution is to use an Install CD which is using the same architecture as the installed system (i.e. 32-bit Install CD for 32-bit targets / 64-bit Install CD for 64-bit targets). 
