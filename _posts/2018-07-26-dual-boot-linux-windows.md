---
layout: post
title: Dual Boot Your Laptop Windows and Linux
---

There are a lot of websites explaining how to dual boot your new laptop or a machine. I will go over what I did :bowtie:

## Introduction
I will consider that you have a new laptop with windows installed in it. Backup your windows on a usb so that you can start over if something goes wrong.
On Windows:
* Search "Create a Recovery Drive"
	* "Back up system files to the recovery drive" and hit enter.
	* Insert USB drive
	* Write on USB
	* Follow prompts on screen
	* Remove USB and keep it safe until dual boot is complete.

## Download Linux
I will post the steps here to install Fedora-Workstation flavored with __K Desktop Environment (KDE)__. While you are on the Windows system, use another USB drive to create a Fedora Live Stick. In order to do that, download [Rufus](https://rufus.akeo.ie/) and then download [Fedora Workstation](https://getfedora.org/en/workstation/download/). Once both are downloaded, run Rufus and create a bootable Fedora Live USB (Follow on-screen prompts after Rufus application opens). You are ready now to install!

## Install Linux
Reboot your machine and while its restarting, go to the Boot Menu (Press `F12` or `F10` depending on your computer). Disable 'secure boot' and enable 'USB Boot' and restart again (you can do `Ctrl`+`Alt`+`Del` to reboot). Before it loads Window OS, go to the Boot Loader and Select your USB (it may be named as Fedora now). Once it starts and shows the Desktop, choose to install on the hard drive and follow the prompts. Once the installation completes, safely remove the USB and restart your machine. Depending on your machine, you may have to go to the Boot Menu each time after restarting to select your OS.

Let me know if you have any further questions :email:

Have a great day!
