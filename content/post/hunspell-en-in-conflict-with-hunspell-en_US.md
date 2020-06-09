---
layout: 
title: "Hunspell-en in Conflict With Hunspell en_US"
date: 2018-08-16T23:56:45-05:00
draft: true
---

On a different machine running the latest updates from Arch, pacman would give the error (and rightly so) that `hunspell-en and hunspell-en_US are in conflict` and `could not satisfy dependencies` followed by `removing hunspell-en breaks dependency hunspell-en required by **antergos-common-meta**`.

This was of course never a problem on the other machine in which **antergos-common-meta** was removed a while back. For the simple reason that the update related to anything **hunspell** was in this particular case only for **hunspell-en_US** as well as **hunspell-es_any** but not for, and this is important to note: **hunspell-en**. The latter includes all English dictionaries for US, UK, etc.

So the question is how to resolve this impeding conflict during the updates? Simply by skipping the package on pacman during the updates, or simply by deselecting the packages that belong to *hunspell-en* on pamac (the gui version for pacman) for which the conflict exists in the first place.

     pacman -Su IgnorePkg=hunspell-en_US

See <a href="https://wiki.archlinux.org/index.php/Pacman#Skip_package_from_being_upgraded" target="_blank">Skip package from being upgraded</a> on the Arch Wiki.

By removing **antergos-common-meta** the first time around on this particular
as I had done a few weeks ago on the other machine, made no difference. And
that's the reason as to why the above is recommended. That is, by skipping the
packages in question that belong to **hunspell-en_US** for example first, and
then by proceeding with the updates normally seems to be the most reasonable
method. 

Once this is done, the next step would be to remove **hunspell-en** which would also remove **antergos-common-meta** by which the latter package relies on.

Finally, the next step would be in installing the libraries for **hunspell-en_US**, or **hunspell-en_GB**, or **hunspell-en_AU** or **hunspell-en_CA**.

Apparently, in the latest installation ISO image, this issue with **hunspell** and its dependencies has not been removed from the repositories that the installation media uses for the initial process. Which better explains as to why on the other machine which had the most recent Antergos installation, this problem was still present, whereas with the other machine in which I had removed **antergos-common-meta** which removed **hunspell-en** - the one that bundles all dictionaries for the English language - was never experienced.

