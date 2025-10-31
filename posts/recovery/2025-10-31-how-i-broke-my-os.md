---
title: "How I Broke My OS"
date: 2025-10-31
author: "Chris Bradley"
tags: [os recovery, windows, grub, linux, boot, cmos]
description: "How I broke my OS and how I recovered it."
readtime: "3min"
---

# How I Broke My OS
For the past month, I've broken my Windows several time just because I wanted to try different Linux distros. But thankfully, I was able to recover and it was a complete nightmare to recover it. I've sat weeks to fix and even had to face some hardware issues. Let's take a look how I recovered my OS and made my laptop boot again normally.

## Problem #1, Installing Arch Linux
### The Problem
If I remember well, I've been sitting in front of my laptop like for 6 hours straight just for the installation to break lmao and after several times I installed it without any Desktop Environment with a **wrong** password 😭
Even worse, my Lenovo laptop didn't respond to BIOS keys. It went straight into Arch and yes, I still had my Windows files but I couldn't boot into BIOS settings or Windows.
### The Fix
Thankfully, I had another laptop which my friend gave me to optimize. I plugged out the hard drive from my laptop, connected it with a SATA to USB cable to the other laptop. Only after finding my Windows partition there, I calmed down a bit. After several times of installing systemd and GRUB bootloader, I came into a conclusion that Arch wasn't for me. After wiping the Arch partion, I was able to boot into my Windows but had the error:
```
Your PC couldn't start properly.
After multiple tries, fhd operating system on your PC failed to start.
Error code: 0xc0000001
```
Back to the second laptop's Windows, found out my Basic Windows Parition was marked as `RAW` which means the there is no file system or the parition is corrupted.
This is where I was able to successfully boot into windows. I did **NOT** format the raw partition which will erase my years of work. Instead what I did was ran the `CHKDSK` utility and FINALLY fixed it by doing so.
```bash
chkdsk D: /f
```
But still I haven't fixed my BIOS keys issue.

## Problem #2, With Lubuntu
### The Problem
Installed Lubuntu everything was fine except it didn't install GRUB. Went into the GRUB folder `/etc/default/grub`, edited the  grub config file by setting `GRUB_DEFAULT=3`which instead of going into Lubuntu it went into `memtest86+` and I had no way of booting into Lubuntu. This time I had another laptop which my homie gave me, which had Debian I installed. Tried several ways to fix it and lost the motivatation to even have Linux on my laptop.
### The Fix
I wiped the Lubuntu partition, after several hours I fixed the second laptop's Windows installed Rufus (had to do new fresh installation unfortunately), created a bootable Windows stick. Then it was later fixed with `bcdedit` which was a common EFI parition problem.
```bash
bootrec /fixmbr
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd
```
These commands fixed my boot problems.

## Problem #3, BIOS Keys Fix
I am not sure what the problem was, but after ripping the laptop apart and cleaning them all, I found that a part of my Flat Flex Cable was bent which made it disconnect often by not sitting in position properly and led to power issues I had recently. It caused the laptop to turn of randomly and it was cleaned and had to carefully place them in position. Then I removed the CMOS battery, waited like 10-15 minutes, plugged all of them in and it works like charm till now.

## What I Learned
I went through a lot of shit which could be avoided by a lot of ways. So what you guys need to have:
* A **bootable USB** with the version of **YOUR** Windows PC flashed with **[Rufus](https://rufus.ie/en)** and not Ventoy.
* An extra laptop, just has to work.
* A SATA cable. Its really a life saver.
* A bootable Linux USB, optional but  recommended.

Sometimes a better way to learn tech is by breaking stuff, but always have a backup of your data lol
