---
layout: 
title: "Sddm Wayland Timezone Differs From Locale"
date: 2018-11-02T02:16:00-04:00
draft: true
---

A slowdown on my hardware had recently made me to reconsider another display manager that would presumably improve the boot time of my system. But even after installing it, I could not see any discernible difference between these display greeters. Perhaps I had noticed it before a year or so ago when I tried it out and went ahead and enabled it on an older system. This time around though, my expectations fell short.

After installing <a href="https://wiki.archlinux.org/index.php/SDDM#Configuration_GUI" target="_blank">SDDM</a>, I called out systemd to disable <a href="https://wiki.archlinux.org/index.php/LightDM" target="_blank">LightDM</a> with

     sytemctl disable lightdm.service 

followed by the enabling of the newly installed display manager with

     systemctl enable sddm.service

But it wasn't clear at first, but just after rebooting the system - although at this point my faulty memory is not helping me remember whether it was a reboot or by logging out of the system, that I noticed that the timezone differed from that of the desktop environment.

Perhaps it was SDDM Wayland that got it right this time around and not the DE XFCE according to the locale currently in use. The timezone that SDDM picked up and hence the entry that was returned after calling out 'timedatectl' were the same. The reasoning behind this assumption is that by calling out the `timedatectl status` as the <a href="https://wiki.archlinux.org/index.php/System_time#Time_zone" target="_blank">Arch Wiki suggested</a>, returned indeed what was expected, albeit wrongly set at one point by me, but nonetheless correct.

     datetimectl status

matched SDDM clock settings. The timezone had been incorrectly set at one point.

Modifying the timezone accordingly seemed to have resolved the issue with:

    timedatectl set-timezone Zone/SubZone

All in all, some of the <a href="https://bbs.archlinux.org/viewtopic.php?id=207550" target="_blank">posts from Arch Forums</a> that were queried via Google, were slightly off topic. Some of these <a href="https://bbs.archlinux.org/viewtopic.php?id=112137" target="_blank">posts</a> for example dealt primarily with clock twelve and twenty four hour clock settings, whereas in my case it the underlying cause was primarily due with the timezone set incorrectly.

Further posts that came up for XFCE were also from the long-standing threads at **linuxquestions.org**, a site that has been around perhaps longer than any other out there related to GNU/Linux in general. This time around the <a href="https://www.linuxquestions.org/questions/linux-software-2/adjusting-the-clock-in-xfce-4175528816/" target="_blank">user was running AntiX</a>  and not systemd. The `timedatectl` is part of the latter in this case, so the suggestions aimed at `hwclock` or setting it also through `date` instead.

I've found that is relatively easy to mess up the time settings on the system as this question from stackexchange pointed out. See for example <a href="https://unix.stackexchange.com/questions/60772/i-messed-up-my-system-clock-in-arch-linux" target="_blank">I messed up my system clock in Arch Linux</a>.

Other questions that dealt with XFCE and not necessarily with SDDM, pretty much coincided with the `timedatectl` command. Like for example the following question that was also on **stackexchange** <a href="https://unix.stackexchange.com/questions/296776/how-can-i-easily-change-my-time-zone-in-arch-xfce" target="_blank">How can I easily change my time-zone in Arch/Xfce</a> that I came across only later and after resolving it first in my end.

And still, the best way and proven methodology I know of, and one which deals with the time/date issue on an Arch Linux system is by the aforementioned method outlined above. Credit where the credit is due, because all the credit goes to the **Arch Wiki** for making it accessible without having to read through an entire manual to resolve an outstanding problem as simple as a timezone. Although I have to acknowledge that reading `man` pages is the optimal and thorough alternative to get a deep understanding of an entire system. Nothing comes close as the latter!

**References**

<a href="https://wiki.archlinux.org/index.php/System_time#Time_zone" target="_blnak">System Time Arch Wiki</a>


