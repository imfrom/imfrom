+++
title = "Gigabyte Computer Sleep Suspend Under Manjaro"
date = "2017-05-22T12:08:23-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>I had configured Manjaro under an old system and was never pressed with the issue of suspend on that old hardware.</p>

<p>When the Gigabyte computer was finally up and running, I noticed that the system was unable to suspend or sleep.</p>

<p>After failing to find a quick solution to the problem on the archlinux forums, I came across this post from the Manjaro site: <a href="https://forum.manjaro.org/t/manjaro-not-waking-from-suspend-or-sleep/492" target="_blank">Manjaro not waking from suspend or sleep</a> and I almost knew  - not right away - that the discussion was the underlying cause of the problems I was experiencing.</p>

<p>One of the users, by the handle of <em>artoo</em> offered to downgrade the kernel:</p>

<p><img src="/images/2017-05-22-artoo-downgrade-suggestion.png" alt=""></p>

<p>The kernel number and the year of the post were no longer relevant.</p>

<p>But instead of the solution offered by the user <strong>artoo</strong> in downgrading, I chose to upgrade instead, especially after the reply by another user who said that:</p>

<blockquote>
<p>Its likeley the problem with hooks in mkinitcpio.conf and users having to
manually mkinitcpio -p linux. Its a weekeley problem on irc and this fixes most
oftenly.</p>
</blockquote>

<p>And</p>

<blockquote>
<p>Its very likely I assumed the initramfs get rebuild one way or another.</p>
</blockquote>

<p><img src="/images/2017-05-22-ivan-reply-mkinitcpiio.png" alt=""></p>

<p>And the anecdote example almost a month later by another user in which he said that</p>

<blockquote>
<p>This time execution of mkinitcpio -p linux46 turns out to be sufficient</p>
</blockquote>

<p><img src="./Gigabyte computer sleep suspend under Manjaro · blog del tecnólogo_files/2017-05-22-fordprefect-suggestion-mkinitcpio.png" alt=""></p>
