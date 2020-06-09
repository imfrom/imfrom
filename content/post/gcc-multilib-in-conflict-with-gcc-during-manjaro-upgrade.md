+++
title = "Gcc Multilib in Conflict With Gcc During Manjaro Upgrade"
date = "2017-06-08T04:04:38-05:00"
draft = true
tags = []
topics = []
description = ""
+++

  <p>During the latest Manjaro upgrade, a conflict of packages already installed on the system, was preventing to proceed with the upgrade.</p>

<p>A quick search on Google returned among the results, a post which had recently been opened on the archlinux forum with the title <a href="https://bbs.archlinux.org/viewtopic.php?id=226723" target="_blank">conflict with gcc-libs and gcc-libs-multilib</a></p>

<p>Even though the conflict of packages on my system, was not the same conflict than the ones reported on the archlinux forum such as with the package gcc-fortran, it was clear as a user suggested:</p>

<blockquote>
<p>gcc-*-multilib is all or nothing.</p>
</blockquote>

<p>On my system, querying the database for <code>gcc</code> with <code>pacman -Qs gcc</code> returned:</p>

<p><img src="/images/2017-06-08-gcc-gcc-multilib-conflict.png" alt=""></p>

<p>I was missing <strong>gcc-libs</strong>, while <strong>gcc-libs-multilib</strong> was installed instead.</p>

<p>A quick <code>pacman -Ss gcc</code> query - see <a href="https://wiki.archlinux.org/index.php/pacman#Querying_package_databases" target="_blank">archlinux wiki - Querying package databases</a> would show the <strong>gcc-multilib</strong> and its accompanying files for the package <strong>gcc-libs-multilib</strong>:</p>

<p><img src="/images/2017-06-08-gcc-multilib-gcc-libs-multilib.png" alt=""></p>

<p>What I ended up doing to avoid the conflict and proceed with the upgrade as scheduled, was to remove the old version of <strong>gcc</strong> - 6.8 if I’m not mistaken now, although I can always check the revision history for the exact number of the package I had at the time - and reinstall <strong>gcc</strong>. I figured to do that, since for one, I had to install the newest version for the compiler anyways, and once done with the system upgrade, then the package <strong>gcc</strong> would be reinstalled.</p>

<p>A final <code>pacman -Qs gcc</code> would return:</p>

<p><img src="/images/2017-06-08-pacman-qs-gcc.png" alt=""></p>
