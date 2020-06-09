+++
title = "Git in Six Hundred Words by Mary Rose Cook"
date = "2016-08-03T14:45:04-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>Imagine you have a directory called <code>alpha</code>. It contains a file called <code>number.txt</code> that contains the text <code>first</code>.</p>

<p>You run <code>git init</code> to set up <code>alpha</code> as a Git repository.</p>

<p>You run <code>git add number.txt</code> to add <code>number.txt</code> to the index. The index is a list of all the files that Git is keeping track of. It maps filenames to the content of the files. It now has the mapping <code>number.txt -&gt; first</code>. Running the add command has also added a blob object containing <code>first</code> to the Git object database.</p>

<div class="main __reader_view_article_wrap_4270907014602854__">
      <p>(This essay is a companion piece to <a href="http://gitlet.maryrosecook.com/">Gitlet</a>, my implementation of Git in JavaScript.)</p>

<p>Imagine you have a directory called <code>alpha</code>. It contains a file called <code>number.txt</code> that contains the text <code>first</code>.</p>

<p>You run <code>git init</code> to set up <code>alpha</code> as a Git repository.</p>

<p>You run <code>git add number.txt</code> to add <code>number.txt</code> to the index. The index is a list of all the files that Git is keeping track of. It maps filenames to the content of the files. It now has the mapping <code>number.txt -&gt; first</code>. Running the add command has also added a blob object containing <code>first</code> to the Git object database.</p>

<p>You run <code>git commit -m first</code>. This does three things. First, it creates a tree object in the objects database. This object represents the list of items in the top level of the alpha directory. This object has a pointer to the <code>first</code> blob object that was created when you ran <code>git add</code>. Second, it creates a commit object that represents the version of the repository that you have just committed. This includes a pointer to the tree object. Third, it points the master branch at the new commit object.</p>

<p>You run <code>git clone . ../beta</code>. This creates a new directory called <code>beta</code>. It initializes it as a Git repository. It copies the objects in the alpha objects database to the beta objects database. It points the master branch on beta at the commit object that the master branch points at on the alpha repository. It sets the index on beta to mirror the content of the first commit. It updates your files - <code>number.txt</code> - to mirror the index.</p>

<p>You move to the beta repository. You change the content of <code>number.txt</code> to <code>second</code>. You run <code>git add number.txt</code> and <code>git commit -m second</code>. The commit object that is created has a pointer to its parent, the first commit. The commit command points the master branch at the second commit.</p>

<p>You move back to the alpha repository. You run <code>git remote add beta ../beta</code>. This sets the beta repository as a remote repository.</p>

<p>You run <code>git pull beta master</code>.</p>

<p>Under the covers, this runs <code>git fetch beta master</code>. This finds the objects for the second commit and copies them from the beta repository to the alpha repository. It points alpha’s record of beta’s master at the second commit object. It updates <code>FETCH_HEAD</code> to show that the master branch was fetched from the beta repository.</p>

<p>Under the covers, the pull command runs <code>git merge FETCH_HEAD</code>. This reads <code>FETCH_HEAD</code>, which shows that the master branch on the beta repository was the most recently fetched branch. It gets the commit object that alpha’s record of beta’s master is pointing at. This is the second commit. The master branch on alpha is pointing at the first commit, which is the ancestor of the second commit. This means that, to complete the merge, the merge command can just point the master branch at the second commit. The merge command updates the index to mirror the contents of the second commit. It updates the working copy to mirror the index.</p>

<p>You run <code>git branch red</code>. This creates a branch called <code>red</code> that points at the second commit object.</p>

<p>You run <code>git checkout red</code>. Before the checkout, <code>HEAD</code> pointed at the master branch. It now points at the red branch. This makes the red branch the current branch.</p>

<p>You set the content of <code>number.txt</code> to <code>third</code>, run <code>git add numbers.txt</code> and run <code>git commit -m third</code>.</p>

<p>You run <code>git push beta red</code>. This finds the objects for the third commit and copies them from the alpha repository to the beta repository. It points the red branch on the beta repository at the third commit object, and that’s it.</p>

<p>(If you would like to learn about the internals of Git in detail, you can read my essay, <a href="https://maryrosecook.com/blog/post/git-from-the-inside-out">Git from the inside out</a>.)</p>
