+++
title = "Gigabyte Motherboard Fails to Load Live Cd but Succeeds With Flash Drive"
date = "2017-04-08T13:10:35-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>I can’t say whether some of the systems that NUC Intel produces, face the same problems while loading a LiveCD/LiveDVD iso image via an external drive, as the manufacturer Gigabyte currently does. The latter manufacturer gave me the proverbial run for the money when I wanted to install an image that was burned on a DVD and had been successfully installed on an old system.</p>

<p>Not only I tried to load two (2) different images that proved to have been installed without issues and worked correctly on two (2) separate old Dell systems, but it seemed that even after specifying the external DVD/Writer on the first prioritized boot order of the BIOS, the motherboard was simply unable to identify it.</p>

<p>I can’t attest whether the BIOS for that particular model is used across similar boards, although is unlikely, but what I can guarantee is that after several attempts, including and not limited to one instance, in which the board seemed to boot in the desired order, in the end was a total disaster: even a warning came up - something that had to do with a missing file from the installation burned DVD image- which appeared on the screen, and would not let me continue.<br>
I wondered at that point whether the motherboard BIOS was clearly identifying the external DVD writer.</p>

<p>A quick search on Google confirmed it. The motherboard would identify the external DVD only sparingly and inconsistently.</p>

<p>I had an HDD preloaded with an operating system. And had no problems whatsoever to load it directly. But connecting an HDD with a preloaded OS would miss the point altogether. How about if the HDD had no OS preconfigured on it. Then it would become a problem.</p>

<p>Another Google search returned different scenarios which were not applicable to my situation.
One user pointed out that by disconnecting and connecting the external DVD right after powering on the motherboard resolved his issue.</p>

<p>Someone on the Anandtech forums - I remember this website from years before, it published some if not the best reviews about SDDs on the marked - briefly spoke about it. This time around someone on the forum, a subdomain of Anandtech, responded that one reason he/she likes to read the posts is too help him/her determine what motherboard <em>not</em> to buy. Another user rightfully expressed his dissatisfaction with this particular brand’s issue on modern times.</p>

<p>A post on a blog from blogspot pointed out that the solution in his/her case was to tweak with the USB connection. Other responses that followed had to do with the failure on the users’ part, in properly identifying the boot order for the device. But this was not the problem I was having. If anything, I noticed - like I wrote earlier - the inconsistency of the board’s BIOS in simply recognizing the connection. Whereas sometimes it would show right after powering the system, other times it would not show up at all. <a href="#blogspot"><sup id="blogref">1</sup></a></p>

<p>Disabling <strong>AHCI</strong> mode in favor of <strong>Legacy</strong> or <strong>IDE</strong> like a user pointed out on Anandtech did not resolve it either. And much less by changing the preloaded configuration for <strong>CSM</strong>. At one point, the system could not even access the BIOS at all, and it became unresponsive. Only after unplugging the cable from the external DVD writer, the BIOS utility would actually show up. This last inconsistent behavior I noticed it by messing with different settings like the ones I mentioned earlier, in which I was faced with the same problem. The only way to access the BIOS was by unplugging the cable. <a href="#anand"><sup id="anandref">2</sup></a></p>

<p>Up to that point I stopped looking and reading for viable solutions altogether. Nothing I tried seemed to work, even though I could plug in an HDD with a preloaded OS. The GB-BXBT run fine or without major problems on a preloaded OS, and yet I was unable to load a live CD/DVD and install it from there.</p>

<p>I noticed that the problem with the USB for the BIOS settings for example, was supposedly patched years ago. And the latest updates for the BIOS on that particular system occurred a year or two before the manufacturer shipped the system to resellers.</p>

<p>How the external DVD writer would appear and disappear at times while turning on the motherboard was simply beyond me. I was unable to confirm nonetheless the same findings than the user at blogspot.</p>

<p>At that moment I realized I could no longer waste any more time in trying to install the Live CD/DVD from the DVD writer onto the HDD. Luckily I had an old USB drive lying around that I could use for testing purposes.</p>

<p>For years I had installed from Live CD/DVDs onto the majority of the systems. It seemed, this was no longer possible.</p>

<p>I tried to use the simplest method to have a portable OS on a flash drive that could - hopefully install onto the HDD.</p>

<p>According to the Arch Wiki <a href="#dd"><sup id="ddref">3</sup></a> the command line could come handy for this purpose:</p>

<p>On the terminal</p>

<pre><code>$ dd bs=4M if=/path/to/archlinux.iso of=/dev/sdx status=progress &amp;&amp; sync
</code></pre>

<p>It took a few minutes for the process to finish but in the end I could no longer complain.</p>

<p>Had to press the <code>DEL</code> key one more time to access the BIOS. Then just like before, went to specify the boot order that the board should recognize first. The boot sequence showed the HDD on the first spot, followed by the flash drive I had recently copied the image to. Rebooted the system and finally the Manjaro installer loaded without an issue.</p>

<p>The installation finished without problems. Later I removed the flash drive. Rebooted the system without having to go into the BIOS again., and successfully the fresh installation of Manjaro with the XFCE environment was running updates as usual.</p>

<p><strong>References</strong></p>

<p><a name="blogspot"></a><a href="http://chromasoft.blogspot.com/2010/10/solving-dreaded-gigabyte-wont-boot-from.html" target="_blank">solving <em>gigabyte wont boot from USB</em></a><a href="#blogref">&crarr;</a></p>

<p><a name="anand"></a><a href="https://forums.anandtech.com/threads/dreaded-wont-boot-from-cd-problem-gigabyte-mb-stumped-and-in-need-of-help.2400256" target="_blank">Anandtech - Won’t boot from CD Gigabyte at Anandtech</a>  <a href="#anandref">&crarr;</a></p>

<p><a href="https://wiki.archlinux.org/index.php/USB_flash_installation_media#Using_dd" target="_blank">USB Flash installation media at Arch Wiki</a></p>

<p><a name="dd"></a><a href="https://wiki.archlinux.org/index.php/USB_flash_installation_media#In_GNU.2FLinux" target="_blank">USB Installation in GNU/Linux</a><a href="#ddref"> ↩︎</a></p>

