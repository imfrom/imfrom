+++
title = "Firefox Problem With Xclip"
date = "2017-05-20T13:58:18-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>I’ve used both vim and neovim editors. The latter is just the newest implementation with out of the box pre-configurations.</p>

<p>As expected, whenever I was trying to use the copy paste command tool such as <code>xclip</code>, both vim and neovim produced the newlines on the X window system across different applications.</p>

<p>But when I set out to write an email on Gmail from Alphabet Inc., using a copy paste command tool such as <a href="https://github.com/astrand/xclip" target="_blank">xclip</a>, the process was to no avail: newlines were not being displayed on Gmail’s interface.</p>

<p>The closest match was a 2016 <a href="https://github.com/neovim/neovim/issues/4501" target="_blank">Yanking to clipboard does not preserve newlines (when pasting to some applications</a> issue that was opened but was eventually closed because the user decided to have <code>xsel</code> take care of the problem for him/her.</p>

<p>But that post raised more questions than answers.</p>

<p>There was a reference on that thread about seeing a post on
unix.stackexchange.com: <a href="https://unix.stackexchange.com/questions/164074/pasting-in-thunderbird-turns-line-breaks-into-spaces" target="_blank">pasting-in-thunderbird-turns-line-breaks-into-spaces</a></p>

<p>After reading the link provided, I recall having come across the same post hours earlier when I was trying to find out more about the issue. A Google search with keywords including but not limited to <strong>xclip</strong> or <strong>newlines</strong>, or <strong>gmail</strong> or <strong>firefox</strong> would return as one of the first results, that specific post which appeared on the stackexchange network before any other post and more relevant results would showed up. Perhaps even those that were more important queries on the web were relegated, but I guess that’s an entirely different issue.</p>

<p>The answer that was accepted on the stackexchange network for that particular question did nothing to resolve the problem, and I guess it wasn’t until I came across the outstanding bugs on Firefox as I will show later, that the buried comment by a user name Volker Siegel was more relevant than I thought:</p>

<blockquote>
<p>Wow. I indeed was using html. Turning this off solved the problem. What could
be an explanation for that? – user2820379 Apr 28 ‘15 at 8:18</p>

<p>Explanation? “Thunderbird, a software that has evolved over more than a decade
to follow changes in protocols and UI expectations. Under these circumstances,
it is inevitable that the structure degrades - know as bit rot. In this
context, it is hard to introduce a new feature in conflict with the current
state, when solving the conflict is infeasible. A new UI feature like HTML
editing may need to be sneaked in between rotten skeletons of old protocol
layers. It will work nicely, but as a result, you will find the configuration
of the new feature down between these old rotten sediments.” – Volker Siegel
Apr 28 ‘15 at 15:30</p>
</blockquote>

<p>I wanted to get at the reasoning behind this fiasco and whether to blame neovim or gmail for it.
On vim: pasting worked under the Gmail’s interface, whereas with neovim the process just failed: newlines turned into whitespace.</p>

<p>The bug is one of those outstanding and hence unresolved that for years has plagued the Firefox browser and its counterpart such as Firebird:</p>

<p><img src="/images/firefox_bug_newlines.png" alt="Paste in content editable div from xclip removes newlines"></p>

<p><a href="https://bugzilla.mozilla.org/show_bug.cgi?id=1049785" target="_blank">Paste in contentEditable div from xclip removes newlines</a></p>

<p>The above post made a reference to <a href="https://productforums.google.com/forum/#!msg/gmail/aV8bdPFiR24/3Owwd9rSaD0J" target="_blank">Gmail ignoring newlines on Copy/Paste</a> and the unhelpful answer of a user did nothing to pinpoint at the problem:</p>

<p><img src="/images/gmail_ignoring_newlines_copypaste.png" alt="gmail ignoring newlines"></p>

<p>The ludicrous implementation of <code>\r</code> before <code>\n</code> is just nonsense.</p>

<p>And it also does not matter whether <code>printf</code> was used instead or a simple <code>echo</code>:</p>

<pre><code> $ echo -e 'una prueba\npara ver' | xclip -sel c 
</code></pre>

<p>or</p>

<pre><code> $ echo $'una prueba\npara ver' | xclip -sel c 
</code></pre>

<p>With <code>xsel</code> the flags are entirely different. But this clearly showed that Firefox is still trying to catch up with it. Gmail is not the problem. If it were I’d be more than happy to denote it. One could verify it by using a different email service such as Outlook from Microsoft for example.</p>

<p>A quick search related to Firefox turned out many more issues than what was originally intended, such as <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=1174452" target="_blank">Copying text with the style “white-space: pre;” does not preserve white space (spaces, tabs, newlines)</a></p>

<p>On the above thread, an <a href="https://bug1174452.bmoattachments.org/attachment.cgi?id=8646518" target="_blank">attachment</a> provided can also be verified with <code>xclip</code>. It does not work under Firefox.</p>

<p>Another <a href="https://kb.iu.edu/d/bdkf">bug 116083</a> is still on the database for the Indiana University.</p>

<p><strong>References</strong></p>

<p><a href="https://specifications.freedesktop.org/clipboards-spec/clipboards-latest.txt" target="_blank">Clipboard specifications from freedesktop.org</a></p>
