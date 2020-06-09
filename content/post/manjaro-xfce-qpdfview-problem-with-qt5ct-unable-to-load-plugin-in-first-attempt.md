+++
title = "Manjaro Xfce Qpdfview Problem With Qt5ct Unable to Load Plugin in First Attempt"
date = "2017-10-19T03:52:43-05:00"
draft = true
tags = []
topics = []
description = ""
+++

<p>I currently have two (2) identical - or that’s what it seemed like - <strong>xfce</strong> environments on two (2) different hardware systems.</p>

<p>I always keep at hand a list of viewers and if there is any problem removing those to be found unnecessarily large or extremely light to the point of rendering them useless, I tend to check the Arch Wiki at <a href="https://wiki.archlinux.org/index.php/list_of_applications" target="_blank">List of Applications</a> for a refresher on what’s available at the moment.</p>

<p>I’ve always found useful, more or less two (2), or three (3) of them, among them, with a quick copy-paste from the Arch Wiki:</p>

<p>gv — Graphical user interface for the Ghostscript interpreter that allows to view and navigate through PostScript and PDF documents.</p>

<p>ePDFView — Free lightweight PDF document viewer using the Poppler and GTK+ libraries. Development stopped.</p>

<p>qpdfview — Tabbed document viewer. It uses Poppler for PDF support, libspectre for PS support, DjVuLibre for DjVu support, CUPS for printing support and the Qt toolkit for its interface.</p>

<p>The latter, strangely enough, was behaving differently on one of the <strong>manjaro xfce</strong> systems.</p>

<p>A quick google search turned pretty much nothing, related to this issue I was having: namely, the adjustment and consequent resizing for the Settings Window.</p>

<p><img src="/images/manjaro-xfce-qpdfview-settings-box-wrong.png" width="680px" height="450px;"></p>

<p>As you can see from the image above, I was unable to get to the bottom of the window whereto I could’ve specified <strong>to cancel</strong> or <strong>apply</strong> the changes to take effect via a GUI. What use is a GUI if one can’t access the main settings of the program?</p>

<p>This took me to the wrong path in trying to modify the settings upon which the <strong>Dialog box</strong> depended on.</p>

<p>The settings for <code>qpdfview.conf</code> were found right under the <code>.conf/qpdfview/</code> directory.</p>

<p>To no avail I tried to change the settings for the</p>

<pre><code> settingsDialogSize=@Size(488 803)
</code></pre>

<p>on the <strong>qpdfview.conf</strong> file, but every single time I did so, even after changing the above size to other feasible settings, the settings window loaded the default and preconfigured values for it, rendering any change I had made earlier such as modifying the values for that <strong>settingsDialogSize</strong> onto the configuration file,  obsolete.</p>

<p>Then I gave up tweaking around with the <code>qpdfview.conf</code> file. Even after removing this file, removing <strong>qpdfview</strong> along with all poppler libraries from the system, reinstalling the program again, logging out of the system, and restarting, and logging right back in, the problem still persisted.</p>

<p>The settings window remained, remained useless for the most part - and from a GUI’s perspective.</p>

<p>Of course I could have just pressed the <strong>carriage</strong> return key on the keyboard to apply the changes, or for that matter the <strong>escape</strong> key to discard any changes, but this was just besides the point, since it defeated the purpose of having GUI applications running. I needed it to be operational.</p>

<p>I tried another venue.</p>

<p>I noticed that every single time that the program <strong>qpdfview</strong> was invoked from the command line, several errors appeared, including the most significant of the lot:</p>

<pre><code> qt5ct: using qt5ct plugin
 qt5ct: D-Bus global menu: no
 Could not load plug-in in first attempt: ""
 "The shared library was not found."
</code></pre>

<p>the second of these messages was self-explanatory. The libraries upon which qpdfview relied upon, were not recognizing or finding the plugin.</p>

<p>A quick search on google later regarding <strong>qt5ct</strong> did not provide a satisfactory explanation behind the <strong>qpdfview</strong> problem.</p>

<p>I read some of the visual methods in adjusting the settings for <strong>qt</strong> on <a href="https://www.pcsuggest.com/qt5ct-change-qt5-application-style/" target="_blank">Change Qt5 application style with qt5ct</a></p>

<p>So I started <strong>qt5ct</strong>, and I noticed that the default settings for the window was to have <strong>gtk2</strong> as the style to be loaded.</p>

<p>Then right after I had changed it to one of the other values, I had high expectations that the changes would improve the dimensions of the dialog box settings for <strong>qpdfview</strong>. But I was wrong. It made everything worse off.</p>

<p>I finally had to tweak around with the problem directly through the <code>qt5ct.conf</code> file by changing the style field. Only then the problem with <strong>qpdfview</strong> was resolved.</p>

<pre><code> [Appearance]
 color_scheme_path=
 custom_palette=true
 icon_theme=Vertex-Maia
 style=gtk2
</code></pre>

<p>The style value was modified to <strong>Breeze</strong>, I saved the file and exited.</p>

<p>The <strong>qt5ct.conf</strong> file should have on the Appearance the following:</p>

<pre><code> [Appearance]
 color_scheme_path=
 custom_palette=true
 icon_theme=Vertex-Maia
 style=Breeze
</code></pre>

<p>Right after making the changes - not even a logout was required - <strong>qpdfview</strong> dialog box dimensions were working and definitely manageable. The only glitch - if it may be rightfully called as such - was an apparent back-to-back unwanted behavior in which the whole window for the settings, was not clearly visible, but one quick maximizing drag-around-movement maneuver, fixed the annoyance once and for all.</p>

<p><img src="/images/qpdfview-correct-settings-dialog-box-1.png" width="680" height="450"></p>

