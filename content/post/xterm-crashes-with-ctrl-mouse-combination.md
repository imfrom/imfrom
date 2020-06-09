---
layout: 
title: "Xterm Crashes With Ctrl Mouse Combination"
date: 2019-03-05T23:33:24-05:00
draft: true
---

It seemed as if there's some sort of conflict by bringing up the menu on the xterm terminal.

<kbd>Ctrl</kbd>+ 🖱 (rightmouse) is usually the way that one would bring the
menu, but every time this was done, **xterm** was crashing. 

After going over some of the **xorg-fonts-*** packages, I noticed that some of
them were not installed for the X system. 

Among them,  **xorg-fonts-misc** was not installed. I
proceeded to install it and the menu was brought up
successfully again by the <kbd>ctrl</kbd> rightmouse
🖱combination.

A bug report was properly sent out to address this issue. I don't recall from having this issue before, and/or when it even first appeared.

