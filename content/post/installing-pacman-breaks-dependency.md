---
layout: 
title: "Installing Pacman Breaks Dependency"
date: 2018-05-29T06:34:49-04:00
---

Running one of the usual updates from the pamac gui package, returned 

     pamac: installing pacman (5.1.0-1) breaks dependency ‘pacman<5.1

I noticed that any package on the list with a dependency must be
unchecked before continuing.

Later I checked the antergos forum to see if there was any solution.

![](/images/pacman-cant-install-breaks-dependency.png)

The suggested workaround was to run 

     pacman -Syyu -d  --nodeps

The following commit apparently introduced the issue in the first
place:

https://git.archlinux.org/svntogit/packages.git/commit/?id=e9272fcb3289f875b1a14222fb17f9185274107f
