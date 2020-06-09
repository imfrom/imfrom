+++
title = "Antergos Keyboard Selection During Installation"
date = "2018-01-27T08:49:17-05:00"
draft = true
tags = ["antergos"]
topics = []
description = ""
+++

<p>One of the drawbacks during the installation of <a href="https://antergos.com" target="_blank">Antergos Linux</a> was in identifying the keyboard layout option that was previously selected during the media installation.</p>

<p>As a result only the default variant was being used after installing the system.</p>

<p>I was able to identify the problem by going to the X window system xorg configuration file <code>/etc/X11/xorg.d/00-keyboard.conf</code> and noticing that the <strong>XkbLayout</strong> variant was not being properly identified as originally intended.</p>

<p>In my case, only one of the options had been specified correctly on the <code>00-keyboard.conf</code> file.</p>

<p>What I found odd, is that on another system, which is by the way, running the same xfce environment from Antergos, the same problem was not encountered. On the other system, only one (1) variant was used, and it had correctly identified the layout twice, but on the system which after installing the Antergos media, loaded the incorrect values, two (2) variants were set accordingly, but only one (1) layout option was identified. In my case <strong>us</strong> had been been identified once, whereas with the former no issues pertaining to this problem occurred in the first place.</p>

<p>As the wiki <a href="https://wiki.archlinux.org/index.php/Keyboard_configuration_in_Xorg#Using_X_configuration_files" target="_blank">Using X configuration files wiki</a> recommends, not to modify any of the settings manually, but let instead <strong>localectl</strong> handle it. <a href="#sample"><sup id="sampleref">1</sup></a></p>

<p><img src="https://imfrom.github.io/images/localectl-usage.png" alt="" /></p>

<p>Of course, it comes handy when there is even an example that illustrates the process by using the correct parameters. For something like:</p>

<p><img src="https://imfrom.github.io/images/00-keyboard-sample.png" alt="" /></p>

<p>Then something like the following <a href="#localectl"><sup id="localectlref">2</sup></a>, based on the previous example, suffices:</p>

<p><img src="https://imfrom.github.io/images/localectl-sample-usage.png" alt="" /></p>

<p>Set the values as deemed applicable to the desired customization.</p>

<h2 id="references">References</h2>

<ol>
<li><p><a name="sample"><a href="https://wiki.archlinux.org/index.php/Keyboard_configuration_in_Xorg#Using_X_configuration_files" target="_blank">Using X Configuration files 00-keyboard.conf</a></a><a href="#sampleref"> &#x21A9;&#xFE0E;</a></p></li>

<li><p><a name="localectl"><a href="https://wiki.archlinux.org/index.php/Keyboard_configuration_in_Xorg#Using_localectl" target="_blank">Using localectl</a></a><a href="#localectlref"> &#x21A9;&#xFE0E;</a></p></li>
</ol>

