---
layout: 
title: "Pacman Gtk Doc File Exists in Filesystem"
date: 2019-11-23T01:10:01-05:00
draft: true
---

It was odd that seemingly identical pamac installations loaded onto very similarly configured machines,  were somehow behaving differently on a great many occasions. 

Both pamac versions had been downloaded and configured and compiled apparently via the same procedure. Both systems also had been configured not much that different from one another. But on one of the systems, pamac would eventually return an error during the same updates. 

Pamac would simply hang, egregiously stuck at either:

      checking inter-dependencies
      
or during

      checking inter-conflicts
      
Of course, I could have just  dismissed all these errors and be happily content to just get rid of this nonsense by removing pamac altogether and start afresh from the official package manager, but I would have never been happy by either settling these problems through such trivialities, as long as another system, on which the very same package was installed, was not showing the same behavior.

Had it given me a problematic workaround at the very least - on the other system that is,  which was working flawlessly nonetheless, -there would have been no doubt that I wouldn't have even considered this extraneous interface to start off with, and would have gone  instead through pacman directly. Or I could have taken further steps and try to at least, file a bug report as the <a href="https://wiki.archlinux.org/index.php/Pacman#%22Failed_to_commit_transaction_(conflicting_files)%22_error" target="_blank">Arch Wiki suggests</a>. But I always liked the design idea behind this graphical interfaced package provided with its updates' notifications, which unlike pacman that would have required to manually tweak checking for these updates. 

But as it's usually the case, pacman was downright correct by identifying as closely as possible the culprit by which the system itself held `files already in filesystem`. This was clearly the case with the package **gtk-doc**, and somehow this conflict had to be resolved.

But what I don't know, and it's my mistake since I didn't venture out - either at the time when it first occurred -, and much less now, because it'd be a wildly-guessing why would this be the case, that even when two systems configured alike which in turn held the same package revisions,  were somehow behaving disparagingly different.

I was not able to remove it [gtk-doc], by invoking pacman alone - as there was another error that disallowed me to do so. And I was simply sloppy back then, as I'm perhaps now to single out and summarize each of the problems that had I encountered during the installation for the new version of pamac, and to to have kept  working errors' copies handy, as this would have provided a somewhat more acceptable idea where the problem lied at.

I did however, tried to stay as far away as possible from manually  removing  each of the files installed by the package [gtk-doc], but unfortunately after many unsuccessful attempts to install another pamac version, this predictable painstaking process, that of having to go and remove each file owned by the package,  seemed to be the only inevitable method to circumvent this problem.

After going through each subsequent step during removal and by successfully reinstalling the same package over again, pamac has been working - so far - without a glitch. If it stays as such, is yet to be determined. I could no longer assure it... but it gives me pause and comfort in knowing that `checking inter-dependencies` or `checking file-conflcts` rolling hangs haven't returned to this annoyingly halting process.
