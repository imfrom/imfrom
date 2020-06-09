+++
title = "Npm Warn Saveerror Enonent During Uninstall"
date = "2017-11-08T13:44:21-05:00"
draft = true
tags = []
topics = []
description = ""
+++

 <p>I recently tried a few utility programs through <strong>npm</strong> javascript manager. For further info see <a href="https://en.wikipedia.org/wiki/Npm_(software)" target="_blank">Npm package manager</a> on Wikipedia.</p>

<p>But after trying them, I noticed that the output compilation was not what I had expected.</p>

<p>Usually, or so it seems, that by default the programs end up on <code>/usr/lib/node_modules</code>.</p>

<p>I kept one of the programs which I found it handy and very convenient. But I just wanted to remove the rest from the system.</p>

<p>But lo and behold. The removal outcome for the programs was not what I had expected either.</p>

<p><strong>npm</strong> threw errors even with sudo privileges.</p>

<pre><code> npm WARN enoent ENOENT: no such file or directory, open 'package.json'
 npm WARN c No description
 npm WARN c No repository field.
 npm WARN c No README data
 npm WARN c No license field.
</code></pre>

<p>The problem was easily resolved by issuing the flag <code>-g</code> (get) for a successful uninstall. So that was <code>npm uninstall &lt;name&gt; -g</code>.</p>

<p>Later I checked on <code>/usr/lib/node_modules</code>, to make sure the program was no longer on the system.</p>
