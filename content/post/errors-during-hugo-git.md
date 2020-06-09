+++
title = "Errors During Hugo Git"
date = "2017-12-13T15:56:07-05:00"
draft = true
tags = []
topics = []
description = ""
+++

<p>During the last setup of <a href="https://gohugo.io/" target="_blank">Hugo</a>, I was faced again with the sometimes difficult handling of submodules. This was of course after the corresponding configuration for the <code>user.name</code> and <code>user.email</code> had already been set accordingly.</p>

<p>The next error which dealt with the git submodule was that it already existed in the index. Which made me look it up on Google.</p>

<p>Among the first results that came up after my query, was the following from the stackoverflow site at the StackExchange Network, entitled <a href="https://stackoverflow.com/questions/12898278/" target="_blank">Issue with adding common code as git submodule: “already exists in the index”</a></p>

<p>The answer that has been widely accepted included as a solution having to invoke the <code>git rm --cached projectfolder</code> on the tree of the folder.</p>

<p>After issuing it:</p>

<pre><code> $ git rm --cached .git/public 
 fatal: pathspec '.git/public' did not match any files
</code></pre>

<p>Which clearly led me nowhere, I noticed that further implementing correctly the command would require a few more steps.</p>

<p>The command <code>git push origin master</code> indicated that origin did not appear to be a git repository.</p>

<pre><code> $ git push origin master
 fatal: 'origin' does not appear to be a git repository
 fatal: Could not read from remote repository.
</code></pre>

<p>It was only after I invoked the <code>git rm -rf public</code> which seemed to fix the problem:</p>

<pre><code> $ git rm -rf public/
 Migrating git directory of 'public' from
 '/public/.git' to
 '/.git/modules/public'
 rm 'public'
</code></pre>

<p>This seemed to at least tell me that the <code>public</code> folder had been removed. So apparently the <code>--cached</code> flag did nothing in this regard.</p>

<p>Next, by using the <code>&lt;tab&gt;</code> key for autocompletion, right after the directories, I invoked <code>git rm -rf .git/modules</code>, which showed the number of possibilities as shown below:</p>

<pre><code> $ git rm -rf .git/modules/
 about                        index.html
 config.toml                  index.xml
 config.yaml                  js
 content                      page
 "content                     post
 css                          "post
 deploy.sh                    sitemap.xml
 .gitmodules                  static
 google4417fd3500b3c667.html  "static
 images                       tags
 "images                      themes
 img                          topics
</code></pre>

<p>Then again, I completed the <code>git rm -rf</code> with the corresponding <code>public</code> folder:</p>

<pre><code> $ git rm -rf .git/modules/public/
 fatal: pathspec '.git/modules/public/' did not match any files
</code></pre>

<p>Which unfortunately again, came back with the <strong>fatal: pathspec</strong> error from before.</p>

<p>What worked, was to have the option <code>--cached</code>, to be implemented right after <code>git rm</code> only recursively with the <strong>.gitmodules</strong>.</p>

<p>So that was</p>

<pre><code> $ git rm --cached .git
 .git/        .gitmodules  
</code></pre>

<p>Which finally after tab completion:</p>

<pre><code> $ git rm --cached .gitmodules 
 rm '.gitmodules'
</code></pre>

<p>So it seems the <code>git rm --cached</code> worked with the <strong>.gitmodules</strong>, but it did not succeed with the <strong>.git/modules/public</strong> directory.</p>

<p>It was only after I invoked the Unix command <code>rm -rf</code> under the <strong>.git</strong> directory, that the problem was finally resolved.</p>

<pre><code> $ rm -rf .git/modules/public/
</code></pre>

<p>After it, the submodule was added again with the</p>

<pre><code> git submodule add -b master &lt;name of static repository&gt; public
</code></pre>

<p>As shown below:</p>

<pre><code> $ git submodule add -b master https://github.com/&lt;username&gt;/&lt;static repository&gt; public
 Cloning into '/public'...
 remote: Counting objects: 2075, done.
 remote: Compressing objects: 100% (91/91), done.
 remote: Total 2075 (delta 74), reused 114 (delta 31), pack-reused 1907
 Receiving objects: 100% (2075/2075), 4.06 MiB | 2.17 MiB/s, done.
 Resolving deltas: 100% (1247/1247), done.

 $ 
</code></pre>

<p>The step-by-step instructions by simply issuing <code>rm -rf public</code> as the <a href="https://gohugo.io/hosting-and-deployment/hosting-on-github/" target="_blank">tutorial to have Hugo running on Github</a> suggested, did not work in this case, for the simple reason that the <strong>git repository</strong> was cloned during the initial setup.</p>

<p>The <strong>.git/modules/public</strong> already existed as a result. So it had to be removed by issuing <strong>rm -rf .git/modules/public</strong> before setting up again the submodule remote repository.</p>

<p><img src="/images/hugo-step-by-step-instructions.png" alt=""></p>

