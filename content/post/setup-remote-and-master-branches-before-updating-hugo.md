+++
title = "Setup Remote and Master Branches Before Updating Hugo"
date = "2017-08-18T14:00:51-05:00"
draft = true
tags = []
topics = []
description = ""
+++

<p>A while ago, I had to set remote and master branches on a different machine.</p>

<p>The methods included setting it up through the <code>git pull</code> command. By going tis route, both the master and remote branches were consequently set and configured without a major inconvenience.</p>

<p>Recently, although I tried to replicate the same method above, I faced problems that included among many other errors, the infamous <code>error: src refspec master does not match any. error: failed to push some refs to 'origin</code></p>

<p>I wasn’t going to go through the poor method of setting up a new site and copy-paste among other files, the <code>posts</code> folder, the <code>theme</code>, the <code>config</code> files, and any other modification I had previously committed.</p>

<p>The site was being generated without a mishap, so I knew it had to do with the no less complicated <code>git</code>, since some of the errors, like the above, were clearly describing that <code>origin</code> did not match the one from the remote.</p>

<p>the necessary steps are as follow:</p>

<p>1-Remove with <code>git</code> all leftovers from the <code>public</code> folder with <code>git rm -rf public</code></p>

<p>2-Remove the <code>public</code> folder itself with <code>rm -rf.</code></p>

<p>3-Add the static site as a submodule to the master with <code>git submodule add -b master &lt;git@github.com:&lt;USERNAME&gt;/&lt;USERNAME&gt;.github.io.git public&gt;.</code></p>

<p>And that should be more than enough to have it working in no time. Push your changes and update it accordingly.</p>
