---
title: "Cannot Convert String Helvetica Medium to Type Fontstruct"
date: 2020-12-20T08:30:13-05:00
draft: true
---

This could very well qualify among one of the most pesky annoyingly error messages that one could ever come across, under the X window system. Of course there are many other errors that are certainly more problematic, but the aformentioned warning is one that requires, as I'm doing now, to write a few words about it. 

In the past, by simply installing any of the `xorg-fonts-75dpi` and/or `xorg-fonts-100dpi` packages, would have gotten this issue resolved. 
 
One could further consult similar posts under the Arch forum that inquired about this problem. See <a href="https://bbs.archlinux.org/viewtopic.php?id=21713" target=_blank>missing helvetica font</a> or also <a href="https://bbs.archlinux.org/viewtopic.php?id=189463" target="_blank">Fonts: cannot convert string… to type Fontstruct</a>, or even albeit unrelated — since this issue at this other site, was concerned under another program perhaps — on the linuxquestions forum entitled <a href="https://www.linuxquestions.org/questions/linux-software-2/error-message-regarding-fonts-in-grace-943919/" target="_blank"> Error message regarding fonts in grace</a> 

But this time around, there must have been some sort of update that most likely has breaking up the way that a non error, and consequentially working without a warning of any kind would come up under the X system. 

Invoking `xlsfonts | grep helvetica` was not returning anything for that matter, and restarting the system a great number of times failed for not showing the error/warning and 'fixing' the underlying issue either. 

The only way to circumvent it this time around, was by installing the `adobe-base-14-fonts` from the AUR repositories. Something that, as I already said, never had to be include it, to have the error/warning not coming up.

Further resources about this package may be found at https://aur.archlinux.org/packages/adobe-base-14-fonts/
