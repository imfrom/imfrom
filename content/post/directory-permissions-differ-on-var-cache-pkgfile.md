---
title: "Directory Permissions Differ on Var Cache Pkgfile"
date: 2018-08-06T02:49:21-05:00
draft: true
---

During the last updates through pacman the following message came up:

     warning: directory permissions differ on /var/cache/pkgfile/
     filesystem: 775  package: 755

But to first understand why this came up in the first place is good to know that `pkgfile` is a tool for searching files in the official repos. <a href="https://wiki.archlinux.org/index.php/Pkgfile" target="_blank">pkgfile - ArchLinux wiki</a>

It should be noted that the question as to why the **pkgfile** differs for the file system hierarchy and the package itself has come up before.

This <a href="https://github.com/falconindy/pkgfile/issues/25" target="_blank">issue</a> on Github dealt with it.

In the thread, one of the users reported whether it was necessary for **pkgfile** to create the directory if it doesn't exist. 

Of course this is not the case here, but upon closer look on the pacman log it could be seen that **pkgconf** had just been upgraded

     upgraded pkgconf (1.5.2-1 -> 1.5.3-1)
     warning: directory permissions differ on /var/cache/pkgfile/
     filesystem: 775  package: 755

Which suggests that right after the updates it didn't recreate it.

On the other hand **pkgconf** is according to the manual pages:

     pkgconf is a program which helps to configure compiler and
     linker flags for development libraries.  This allows build
     systems to detect other dependencies and use them with the
     system toolchain.

see for example what the aforementioned <a href="Github https://github.com/falconindy/pkgfile/issues/25#issuecomment-227413406" target="_blank"> issue on Github</a> said about it.

And a quick Google search would return among many of the results, the following: 

https://bbs.archlinux.org/viewtopic.php?pid=317732#p317732

As well as

<a href="https://bbs.archlinux.org/viewtopic.php?id=223190" target="_blank">this one</a> which in turn redirected to <a href="https://bbs.archlinux.org/viewtopic.php?id=218133" target="_blank">this one</a>

With due credit to where credit is due, the following post from the Manjaro community explicitly said that it was a warning and not an error itself.

>xabbu 2018-06-10 21:39:39 UTC #4
>directory permissions differ on ...
>
>This message is a warning and not an error. This is normally not a problem. It just says that the permissions of a folder in a package differ form the permissions of that folder on your system.
>
>Normally this will not result in a problem, however you should change the permissions to the package defaults to avoid future problems. This message is shown every time you update this package if the permissions don’t match.
>
>In your specific case, at the moment only root and members of the group locate have access to the mlocate folder. With the change to 755 everybody can access and read the content of that folder. This don’t necessary mean everybody has also read access to the files in that folder.
>
>Why the package folder contains different permissions than your system folder can have several reasons. Often it is because the upstream source have changed permissions. Sometimes a developer does this on purpose. But sometimes this happens by mistake and is changed back with the next release. Also the Maintainer can change the permissions of files and folder in the build process.
>And of course the user sometimes changes the permissions of a file or folder and forget about or does it to fix a problem.
>
>Also please note (@jochen82 @farverio ), if you have a problem with something else start a new thread with your problem to get help with that.
>

On another thread on the same Manjaro forums this came up: 

>fhdk 2018-05-07 10:34:00 UTC #4
> rrrsssttt:
>directory permissions differ on /var/lib/samba/private/ 
>filesystem: 755 package: 700
> bill_t:
>It means that the permissions of this directory must be set to 755 (or drwxr-xr-x).
>
>Actually it means the opposite.
>
>The filesystem is 755 when the package expects it to be 700.
>
>So the right thing to do is to set permissions as the package expects it to be.
>
>sudo chmod 700 /var/lib/samba/private/
> rrrsssttt:
>I want to clarify that I don’t believe I have ever touched that folder (I may have installed apps that have touched it, but I consciously never have)
>
>You don’t need to. It is probably a fix since the folder mentioned is named private and as such is a folder that samba uses for stuff like certificates, keys, private keys, and so on.
>
>Such folder is only accessible for the system service running samba and the service will presumably refuse to run if permissions is wrong.
>
>Try that with your .gnupg folder or the .ssh folder. If permissions is world readable you will get complaints from application and some even refuses to run unless only accessible by owner aka chmod 700 ~/.ssh -R as an example.

see <a href="https://forum.manjaro.org/t/i-got-a-warning-after-running-the-latest-round-of-updates-im-confused-what-to-do-next/46651" target="_blank">I get a warning after running the latest round of updates</a>

As the user on the Manjaro Forum pointed out when he/she said:

>Actually it means the opposite

Changing the directory permissions of the package in question in the file system with a `chmod 755` would be the best course of action for this package permission issue.

I think that the reason why it occurs in the first place, is due to the fact that the tool **pkgfile** must have administrative privileges during installation/upgrade in order to continue. That is, writing, reading and executing. But once the update has finished it no longer is necessary to keep the same permissions than before. The package no longer needs to have access to the home of the user in question.



