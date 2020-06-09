+++
title = "Network Has Been Disconnected Manjaro Kde Xfce"
date = "2017-12-01T13:41:54-05:00"
draft = true
tags = []
topics = []
description = ""
+++

<p>For some unknown reason, I was getting the message <code>network has been disconnected</code> even on connections that have been previously used.</p>

<p>Contrary to the post entitled <strong>NetworkManager doesn’t automatically ask for a password for new network</strong>, see <a href="https://bbs.archlinux.org/viewtopic.php?id=142066" target="_blank">see this post on bbs.archlinux.org</a> in my case the connection was used many times before.</p>

<p>The dependency problem that has plagued this bug seemed to make a comeback on a most of Manjaro desktop environments.</p>

<p>Installing, or better put, reinstalling it with</p>

<pre><code> yaourt -S gnome-keyring
</code></pre>

<p>seemed to resolve the issue.</p>

<p>The same problem hasn’t been experienced on Antergos distribution.</p>
