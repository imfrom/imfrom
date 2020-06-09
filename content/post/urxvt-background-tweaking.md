+++
title = "Urxvt Background Tweaking"
date = "2017-08-18T14:05:19-05:00"
draft = true
tags = ["urxvt", "rxvt"]
topics = []
description = ""
+++
<p>I’ve never bothered with <a href="https://wiki.archlinux.org/index.php/rxvt-unicode" target="_blank">urxvt</a> in the past. Perhaps was the way that dealt with the default glyph, which discouraged me from using it.</p>

<p>Later I found that the above was easily answered here at <a href="https://unix.stackexchange.com/questions/81746/how-can-i-get-better-looking-fonts-in-my-term" target="_blank">how can I get better looking fonts in my terminal (urxvt)</a></p>

<p>Nonetheless, the simple fact that I had to modify it directly on <code>.Xresources</code>, stopped me from doing all the necessary modifications to accomplish it.</p>

<p>Then I also found the excellent script <a href="https://github.com/majutsushi/urxvt-font-size" target="_blank">urxvt-font-size</a> which allows changing the font size on the fly.</p>

<p>The one problem I faced with this magnificent terminal was the handling of the background color.</p>

<p>Ignorant I was of the fact that although <code>.Xresources</code> is the responsible source to change the background, one must specify it, and not expect to interpret the default values of <code>xterm</code>, a different terminal.</p>

<p>It wasn’t until a post which was replying to a thread opened on the Arch\Linux forums entitled <a href="https://bbs.archlinux.org/viewtopic.php?pid=957150#p957150" target="_blank">rxvt-unicode font color too dark</a> which pretty much condensed what I was after, and made me feel more stupid afterward.</p>

<p><img src="/images/2017-08-18-karol-answer.png" alt=""></p>

