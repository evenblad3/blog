---
title: "Optimize Your Windows Computer"
date: 2025-10-05
author: "Chris Bradley"
tags: [windows, optimization, speed, performance, low-end, tech, microsoft, bloatware, bloat, debloat]
description: "Optimizing Windows and making the computer more performant."
readtime: "2min"
---

# Optimize Your Windows Computer
Ever wondered why your Windows computer runs like a tortoise? Does a tortoise run? Of course not!
Thats why I am here to show you how to make your computer run as fast as it could. If you have a broke ass computer, don't worry I've gotchu too :D

## Deleting Apps
No, before you wonder why you gonna delete some apps even though you are using everything, there are still some apps you have to delete especially *if you're using some low-end hardware*. Things like Whatsapp desktop, YouTube or Instagram shortcut, etc can be used on web browsers. Come on, if you really want to speed up your computer you really have to do it. This way **you can save some space** in your computer's secondary storage. There's a lot of tweaks you can do in web browsers to speed them up and I'll show you how to do it soon now. [If you're the "jump the gun" person, here you go.](#optimizing-webbrowsers)

## Disabling Startup Programs
If you use Adobe products, its going to decrease a **LOT** of performance. Its a spyware shit too. Go to `msconfig` -> startup or Task Manager -> startup, disable all apps that doesn't need auto start ability.

## Disabling Animations
If you disable animations, you're going to boost your computer's performance. Search for `Adjust the apperance and performance of Windows` -> Visual Effects -> Adjust for best performance, and check `Smooth edges of screen fonts` if you don't want pixelated text.

## Cache Files
Delete them one or two months once. This is typically necessary for people who involve in heavy usage or have low end hardware. Just don't delete them too often like everyday that's overkill and can sometimes reduce the speed of calculating certain operations. The following directories contain cache files:
- `%AppData%\Local\<Browser>\Cache` (Or go to your browser settings and clear browsing data)
- `%temp%` (`C:\Users\%username%\AppData\Local\Temp`)
- `prefetch` (`C:\Windows\Prefetch`)

## Optimizing Webbrowsers
### Chrome
Do these:
*  Turn off background activity, its just wasting your computer's energy and spying on you.
   ```
   Continue running background apps when Google Chrome is closed
   ```
*  Turn on `Energy saver`
* Do **not** use Chrome, seriously.

### Firefox
1. Install [uBlock Origin](https://ublockorigin.com/), prevents most of the ads and popups, saves resources.

2. Go to `about:config` and set the following values
**WARNING**: Before proceeding beware that these are experimental settings so use it at your own risk ⚠️
   ```
   browser.cache.memory.capacity: -1 # automanage
   browser.sessionstore.interval: 300000 # 5min
   network.prefetch-next: false # Disable prefetching
   gfx.webrender.all: false # For weaker or no GPUs
   image.mem.decode_bytes_at_a_time: 4096
   media.hardware-video-decoding.force-enabled: false
   ```
