+++
title = "Manjaro Kde Plasma Error Unknown Application Folder"
date = "2017-12-14T13:28:52-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>It’s apparently a foolish idea to login as root from a file manager on Plasma KDE.</p>

<p>This was exactly what caused a number of problems, and among them, most notably, that I could not get past the login screen.</p>

<p>Of course, little did it matter that I installed any of the other display managers available and removed the current in use from the command line. I was still unable to get past the login screen.</p>

<p>In other words, it wasn’t just the usual <code>login failed</code> which indicates the wrong username and/or password. This was exactly the opposite, as after inputting the password for the system, since <code>login automatically</code> was disabled, the screen would fall back as if it loading the kernel again, and then without further ado, back into the login screen.</p>

<p>This feedback loop process was endless. I couldn’t but scourge on Google for some sort of information regarding the issue.</p>

<p>One of the first queries to Google was with the terms <strong>plasma kde fails to startx</strong>, although I knew that the last element of the query was not the most accurate. For one, because the <strong>X server</strong> was somehow running, or else how could I have a login screen in the first place. But almost unsurprisingly, the first result from Google was from the Arch Linux forum entitled <a href="https://bbs.archlinux.org/viewtopic.php?id=193286" target="_blank">Cannot start plasma 5</a>.</p>

<p>I tried to follow one of the recommendations and modify the last line to</p>

<pre><code> exec startkde
</code></pre>

<p><img src="/images/change-xinitrc-for-kde-plasma-login.png" alt=""></p>

<p>but it made no difference.</p>

<p>Perhaps on other desktop environments the change on <strong>.xinitrc</strong> was a success, but at least on Manjaro Plasma KDE, all of it was failing and I was not able to get past the login screen.</p>

<p>For example, the suggestion to modify the <strong>.xinitrc</strong> on the <strong>xfce</strong> desktop environment have proven to succeed without any major problem.</p>

<p>See for example <a href="https://bbs.archlinux.org/viewtopic.php?id=147721" target="_blank">Can’t get past the login screen</a>, where modifying the <code>.xinitrc</code> was more than enough to get it started.</p>

<p><img src="/images/change-xinitrc-for-xfce-login.png" alt=""></p>

<p>At this point it was futile to modify any further the <strong>.xinitrc</strong> initialization file when moments before I had restarted the system, an error related to Plasma KDE had popped up on the screen:</p>

<p><img src="/images/plasma-error-window.png" width="500"></p>

<p>A couple more errors from the main file manager Dolphin showed for example the following:</p>

<p><img src="/images/user-xbel-kde-plasma.png" width="500"></p>

<p>And also</p>

<p><img src="/images/kio_applicationsrc-error.png" width="500"></p>

<p>At this point, after the infamous error with the <strong>kio_applicationsrc</strong>, I very well knew that the culprit of it all occurred when trying to login as root to Plasma from the Dolphin file manager.</p>

<p>Later on, after giving up the have Manjaro KDE running on the system, I found a few posts that spoke about logging in as root on the Plasma environment.</p>

<p>On the same post that for example was highlighted earlier, there is useful information as why running as root as KDE is altogether discouraged:</p>

<p><img src="/images/dont-run-as-root-on-kde.png" alt=""></p>

