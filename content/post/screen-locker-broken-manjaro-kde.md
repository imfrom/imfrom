+++
title = "Screen Locker Broken Manjaro Kde"
date = "2017-12-09T13:58:20-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>While updating a fresh installation of Manjaro KDE, the screen locked.
Apparently the default settings for the system, enabled this behavior without
further ado.</p>

<p>As a result of this problem, the surprising part came afterward when the updates that were being downloaded, suddenly crashed the system. This led to the nonetheless bothersome problem of <code>modules.devname not found</code> error followed by the no more troublesome error <code>you are now being dropped into an emergency shell</code> and <code>sh can't access tty; job control turned off</code>.</p>

<p>I didn’t have at the time a live media to access the system. Although I knew the that the sudden crashing during the download of updates , was one of the problems underlying the <code>modules.devname not found</code> error.</p>

<p>A quick google searched returned  <a href="https://unix.stackexchange.com/questions/355689/manjaro-fails-to-boot-modules-devname-not-found-then-unknown-disk-uuid-error" target="_blank">Manjaro fails to boot, modules.devname not found</a> a result which provided an answer that pointed to access the system with Manjaro’s own <code>mhwd-chroot</code> command to access the emergency shell. See <a href="https://wiki.manjaro.org/index.php/Restore_the_GRUB_Bootloader#Chroot_into_your_existing_Manjaro_Installation" target="_blank">Chroot into your existing Manjaro Installation</a></p>

<p><img src="/images/mhwd-chroot-steps.png" alt=""></p>

<p>And as the already mentioned answer on the unix.stackexchange.com site suggested, it was necessary to reload the image again.</p>

<p><img src="/images/chroot-answer-mkinitcpio.png" alt=""></p>
