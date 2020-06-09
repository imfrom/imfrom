---
title: "Pamac Gui Wps Office Curl 22 The Requested URL Returned Error 416"
date: 2020-03-05T00:10:05-05:00
draft: true
---

On a recent [WPS](https://www.wps.com/linux) upgrade through pamac gui, there was a somewhat inconvenient `curl: (22) The requested URL returned error: 416 `  error which I wasn't ready for,  at the time it happened.

All the updates had gone through any major problem, but this seemed to go on.

I had no issues elsewhere and with another system in which the updates went through without any setback there seemed to be no issues either.

Even after updating the **mirrorlist**, I was still facing the same problem.

A quick google search led me to, among the most relevant results, a post that was entitled <a href="https://forum.manjaro.org/t/wps-office-failure-while-downloading/112800/3" target="_blank"> wps-office: failure while downloading </a>  that was brought up by the manjaro distro users to the devs - the latter group  is after all,  the one behind the <a href="https://gitlab.manjaro.org/applications/pamac" target="_blank"> development of the pamac graphical interface program </a> - in which some folks pointed out the possibility of a network problem. Unlike the op issue, mine had primarily to do with an upgrade of the wps suite, and not an installation or reinstall. And also, just  as another user stated on the same forum, I had made sure that the network paralleled culprit wasn't preventing the upgrade of wps from happening.

Since wps office is provided by AUR which is the largest unofficial repository package t Arch Linux, the best course of action was to reset the upgrade through the pamac program itself.






