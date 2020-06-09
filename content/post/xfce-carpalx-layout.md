+++
title = "Xfce Carpalx Layout"
date = "2017-07-09T12:09:38-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>There are many ways to add the <a href="http://mkweb.bcgsc.ca/carpalx/" target="_blank">carpalx</a> layout to X window system on GNU/Linux.</p>

<p>The desktop environment Plasma KDE does not have that problem. One could easily add it from the <strong>Input Devices</strong> from the <strong>settings</strong> of the system.</p>

<p>If however, one is running <strong>Xfce</strong>, things are not as straightforward as one would like them to be.</p>

<p>At the bottom of this post, one can find the zip archive where the <em>carpax.xkb</em> file resides.</p>

<p>Unzip the contents and open up the README.txt to have an idea of what to copy. But there are two (2) things/caveats to remember.</p>

<p><strong>One shouldn’t modify the <em>symbols/us</em> file as it was suggested by the author</strong></p>

<p>and</p>

<p><strong>No need to follow Step 3 by loading the layout with setxkbmap carpalx. For one thing it will not load the default variant of the layout.</strong></p>

<p>I’m just posting the following as it currently appears on the README.txt file provided by the author.</p>

<h1 id="installation-instructions">INSTALLATION INSTRUCTIONS</h1>

<ol>
<li><p>Copy carpalx.xkb to your XKB symbols directory (path my differ slightly)</p>

<p>$ cp carpalx.xkb /usr/share/X11/xkb/symbols/carpalx</p></li>

<li><p>Add the following lines to /usr/share/X11/xkb/symbols.dir</p>

<p>-dp—– a——- carpalx(qgmlwb)
–p—– a——- carpalx(qgmlwy)
–p—– a——- carpalx(qfmlwy)
–p—– a——- carpalx(qwkrfy)
–p—– a——- carpalx(qwyrfm)
–p—– a——- carpalx(tnwmlc)</p></li>

<li><p>Now it should be possible to load the layouts with, e.g.</p>

<p>$ setxkbmap carpalx                            # defaults to QGMLWB
$ setxkbmap -layout carpalx -variant qwkrfy    # to select other variants</p></li>

<li><p>The following files should also be updated:</p>

<p>/usr/share/X11/xkb/rules/xorg.lst
/usr/share/X11/xkb/rules/xorg.xml</p></li>
</ol>

<h1 id="one-better-way-to-accomplish-it">One better way to accomplish it:</h1>

<h1 id="instructions-to-follow">Instructions to follow</h1>

<ol>
<li><p>Copy indeed carpalx.xkb to the XKB symbols directory with sudo privileges</p>

<p>$ cp carpalx.xkb /usr/share/X11/xkb/symbols/carpalx</p></li>

<li><p>Go to <strong>/usr/share/X11/xkb/rules</strong></p>

<p>$ cd /usr/share/X11/xkb/rules</p></li>

<li><p>Once there and with sudo privileges again open <strong>evdev.lst</strong>. Add it.</p></li>
</ol>

<p><img src="/images/edit-evdevlst.png" alt=""></p>

<ol>
<li>Edit the file <strong>edev.xml</strong> and add the variant to the list.</li>
</ol>

<p><img src="/images/edit-evdevxml.png" alt=""></p>

<ol>
<li>Go to <strong>Keyboard Settings</strong> of the <strong>xfce</strong> graphical environment and add it. It will show on the list as shown in the following image:</li>
</ol>

<p><img src="/images/xfce carpalx layout · blog del tecnólogo_files/add-carpalx.png" alt=""></p>

<ul>
<li>Downloadable zip files:</li>
</ul>

<p><a href="http://mkweb.bcgsc.ca/carpalx/distribution/carpalx-x11.zip">http://mkweb.bcgsc.ca/carpalx/distribution/carpalx-x11.zip</a></p>
