---
layout: 
title: "Pamac Error While Loading Shared Libraries Libalpm"
date: 2019-11-01T02:37:53-04:00
draft: true
---


[Libalpm](https://www.archlinux.org/pacman/libalpm.3.html) is the library for package management of Arch.

I found it funny that in case of any bugs the team says

> Bugs? You must be kidding; there are no bugs in this software. But if we happen to be wrong, submit a bug report.

But they're right. When it comes to package management handling, Arch offers unlike any other one out there, the quirks and perks that not even a propietary  coding scheme such as Homebrew, Fink, Macports from OSX Cocoa could even think to come close during its best moments. This is not to illegitimize whatever accomplishments have been put together by these teams, but it's still disparately sub-par compared to what Arch has offered.


During the last kernel update there was a problem with  pamac though

Firing it up from the terminal was simply returning an

```
error while loading shared libraries: libalpm.so.11: cannot open shared object file: No such file or directory
```

Which considering how lazy I've become over the years, and even more so after reading articles a few years ago such as [Is Google making us stupid](https://en.wikipedia.org/wiki/Is_Google_Making_Us_Stupid%3F) by Atlantic technology writer Nicholas Carr, I couldn't wait to gobble it up or try to leave it up to Google to offer the best match to this undesired behavior I was getting.

The first query by the algorithms of Google returned an issue over at <a href="https://github.com/Jguer/yay/issues/1087" target="_blank">yay: error while loading shared libraries: libalpm.so.11: cannot open shared object file: No such file or directory </a>

But thinking about it again, the issue pertained mostly to <a href="https://aur.archlinux.org/packages/yay/" target="_blank"> aur.archlinux.org/packages/yay/</a> which I've never installed. Perhaps I had done it years earlier on another different system, but not on the current machines I've been running.

The second queried result though, took me to <a href="https://rtfm.co.ua/en/arch-linux-package-query-error-while-loading-shared-libraries-libalpm-so-11-2/" target="_blank"> Arch Linux: package-query: error while loading shared libraries: libalpm.so.11</a>, but as soon as I read about making a symbolic link, which the author of article rightfully pointed out that although it could be done,  is not recommended and just plain wrong to go that route.. 

The other solution from the same article, involved reinstalling <a href="https://aur.archlinux.org/packages/package-query/" target="_blank"> aur package query</a>, but then again, I didn't even have package-query on that particular system.... and unfortunaetly reinstalling pamac didn't resolve the issue as he had stated it.

Downloading the newest version and configuring it later on did the trick...

Somehow it seemed that during the latest upgrade, the installation of  pamac, which occured during the same kernel upgrade and which it was done  by the interface itself did not go as planned.... 


This had to be done again not only with `makepkg` but with a newer version, in order to have it running again.

