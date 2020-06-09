---
layout: 
title: "Kakoune Invoke Shell Program on Buffer"
date: 2019-02-05T02:19:58-05:00
draft: true
--- 

I seldom use the text editor
kakoune. Many of the features that I
have found with vim or neovim for that
matter in the past, have finally been
implemented on this editor.

It is, however, one of the best modal
editors currently in development and I
encourage anyone who may be interested on
the modality of these sort of editors,
to try it out.

I wanted to see how well this editor
handled key mappings to invoke a command
from within the shell.

The map keys doc which can be found at <a
href="https://github.com/mawww/kakoune/blob/master/doc/pages/mapping.asciidoc"
target="_blank">mapping.ascii</a>
specifies that `map [switches] <scope>
<mode> <key> <keys>` would be the recomme
nded way to map a key to the desired
parameter.

Further googling about this issue, led me
to a post at <a
href="https://discuss.kakoune.com/t/how-to-execute-shell-commands-with-the-current-file-name/"
target="_blank">how
to execute shell commands with the current
filename</a> in which a user asked for a
similar configuration on the kakrc
initialization file to invoke a command
within the shell for the current buffer. 

But unfortunately the suggested
recommendation for a latex file in this
case, would not work.

At the very least, the WinSetOption
variable must have a normal mode to which
the key is mapped to.

So the correct way to  map the key would be


     map global normal <c-x> ':w<ret> $ latex $kak_buffile'

In that case, **ctrl** and **x** are bound
to save the file and invoke the shell
command.

If other options are needed then specify
it accordingly


**References**

<a href="https://github.com/mawww/kakoune/blob/master/doc/pages/mapping.asciidoc"
target="_blank">kakoune mapping</a>

<a
href="https://github.com/mawww/kakoune/wiki/Normal-mode-commands"
target="_blank">Kakoune normal mode
commands</a>

