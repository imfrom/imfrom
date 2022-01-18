---
title: "Slackware Startx Blank Screen Without Imobiledeviceglue"
date: 2022-01-18T03:07:36-05:00
draft: true
---

Blank screen kde plasma wayland on Slackware was the issue this time.

I had tried to run level 3 on slackware current kde plasma by invoking, as I had done before, `startx` on the system. 

And with the most current slackware as of this writing, and after successfully upgrading the system, I was still unable to do so.

Some post dating back to 2019 https://www.linuxquestions.org/questions/slackware-14/slackware-current-kde5-startx-failed-4175662813/  pointed to do an upgrade. Of which I had done. So this suggestion led nowhere.

After checking many of the issues as described on linuxquestions which resembled some of the behavior such as logging in through level 4 on sddm as this one pointed out https://www.linuxquestions.org/questions/slackware-14/blank-screen-on-startx-for-kde-at-kernel-5-10-4-a-4175687833/page2.html

I couldn't help but noticed that not only I was unable to log in through sddm but also a message that read the following:

```
The current theme can not be loaded due to the errors below, please select another theme:

file:///usr/share/sddm/themes/Breeze/Main.qml:14:1:plugin cannot be loaded for module "org.kde.plasma.core" cannot load library /usr/lib64/qt5/qml/org/kde/plasma/core" libcorebindingsplugin.so (libimobiledevice-glue-1.0.so.0 cannot open shared object file: No such file or directory)
```

This of course served no discernible help at all, as Google quickly confirmed, a search for `bindingsplugin.so` returned unrelated results while recently, as of today, a search on Google for <libcorebindingsplugin.so slackware> pointed out that the solution for the problem would be to `slackpkg install-new`. But for as long as I have updated the system on Slackware, with the kernel and packages, I have always foregone from invoking, even though is technically correct after a system upgrade, such command as `slackpkg install-new`.

By the time I read that suggestion, which was just now as of this writing and  which was posted only a few days ago, I had already found, perhaps not as elegant, a solution to invoke `startx` successfully.

Somehow while invoking **kwin_wayland** though `startkwayland` I noticed, unlike before, that was returning the error: `/usr/bin/kwin_wayland: error while loading shared libraries: libimobiledevice-glue-1.0.so.0: cannot open shared object file: No such file or directory` which quickly identified the culprit.

Somehow the file for this shared library  was not installed. Perhaps the file was not using the same repo as the repo that was being used during  the system upgrade. 

After installing it with `slackpkg install imobiledevice-glue` kde plasma was successfully loaded with `startx`.




