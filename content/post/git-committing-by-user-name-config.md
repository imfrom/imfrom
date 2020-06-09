+++
title = "Git Committing by User Name Config"
date = "2017-11-16T13:01:35-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>I recently had to set up again the local branches through git.</p>

<p>An error that was not uncommon came up on the screen:</p>

<pre><code> *** Please tell me who you are.

 Run

   git config --global user.email "you@example.com"
   git config --global user.name "Your Name"

 to set your account's default identity.
 Omit --global to set the identity only in this repository.
</code></pre>

<p>This time around it was done through configuring a <code>user.name</code> and a <code>user.email</code> on git itself.</p>

<p>It came to memory that the last time I was setting it up on a different system by pulling the sources from the remote branch, this configuration was never used.</p>

<p>An answer on stackoverflow reminded me that this was indeed the case the last time I had done it. See <a href="https://stackoverflow.com/a/17713604" target="_blank"> instead of doing a git pull you can do a git fetch</a></p>

<pre><code> git fetch
 git reset --hard origin/master
</code></pre>

<p>Even if the error from <code>git</code> with the <strong>please tell me who you are</strong> comes up after an ssh key is granted, as it was posted on this other thread entitled <em>Git-please tell me who you are error when using ssh key</em>, the best alternative is to specify the <code>--global</code> option from <code>git</code> as it posted at <a href="https://stackoverflow.com/a/42335651" target="_blank"> run git config –global user.email - git config –global user.name</a></p>

<p>Of course, if the option to have a <code>--global</code> configuration is not desirable, then the removal of this <code>.gitconfig</code> file may be accomplished through <strong>git</strong> again by issuing <code>git config --global --unset-all user.name</code> and <code>git config --global --unset-all user.email</code> from the terminal.</p>

<p>On the website that aims at answering questions about the ubuntu distributiion, there are more examples with this purpose. See for example <a href="https://askubuntu.com/questions/206449/" target="_blank"> git config global file - remove settings</a></p>

<p>The most important part about it lies on the command <strong>–unset-all</strong>, even though the <a href="https://stackoverflow.com//a/282550" target="_blank">  answer</a> which pointed at it was not the accepted solution in this case.</p>

<p>For more details about the config-file for <strong>git</strong> it is recommended to read the manual <strong>man git-config</strong> for more details.</p>
