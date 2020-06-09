---
layout: 
title: "Closetag Vim on Markdown Filetype"
date: 2018-12-17T00:43:33-05:00
draft: true
---

I coudln't help but noticing that the closetag plugin script for vim wasn't working on any of the markdown files that had been previously edited.

The markdown files in question were of the abbreviated form `md` and not `markdown`.

It did work without a problem on any newly-created file and whether these files were of the form or had the extension `md` or `markdown`.

The README file of **closetag** specifies that in order for the plugin to work, it should be further specified as such on the initialization file with something such as:

     let g:closetag_filenames = "*.html, *.xhtml, *.phtml"

etcetera. <a href="#closetagreadme"><sup id="closetagreadmeref">1</sup></a>

At one given point I recall having `*.md`, which was more than enough for the **closetag** plugin to work without a problem, even with previously edited files.

This time around however, only having `*.md` did not remedy the problem.

Having `*.markdown` on the vim initialization file was necessary for the
**closetag** plugin to work with previously edited markdown files that held a
suffix `.md` extension


     let g:closetag_filenames = "*.md, *.mardown"


**References**

<a name="closetagreadme"></a><a href="https://github.com/alvan/vim-closetag/blob/master/README.md#options" target="blank">README file for closetag</a><a href="#closetagreadmeref">&crarr; </a>
