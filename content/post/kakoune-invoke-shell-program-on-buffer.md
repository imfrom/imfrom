---
title: "Kakoune Invoke Shell Program on Buffer"
date: 2019-02-05T03:47:40-04:00
draft: true
---

<!--# Kakoune Invoke Shell Program on Buffer {#kakoune-invoke-shell-program-on-buffer .post-title}

[Feb 5, 2019]{.post-date}
-->

I seldom use the text editor kakoune. But many of the features that I have
found with vim or neovim for that matter in the past, have finally been
implemented on this editor.

It is, however, one of the best modal editors currently in development
and I encourage anyone who may be interested on the modality of these
sort of editors, to try it out.

I wanted to see how well this editor handled key mappings to invoke a
command from within the shell.

The map keys doc which can be found at
[mapping.ascii](https://github.com/mawww/kakoune/blob/master/doc/pages/mapping.asciidoc)
specifies that `map [switches] <scope> <mode> <key> <keys>` would be the
recomme nded way to map a key to the desired parameter.

Further googling about this issue, led me to a post at [how to execute
shell commands with the current
filename](https://discuss.kakoune.com/t/how-to-execute-shell-commands-with-the-current-file-name/)
in which a user asked for a similar configuration on the kakrc
initialization file to invoke a command within the shell for the current
buffer.

But unfortunately the suggested recommendation for a latex file in this
case, would not work.

At the very least, the WinSetOption variable must have a normal mode to
which the key is mapped to.

So the correct way to map the key would be

     map global normal <c-x> ':w<ret> $ latex $kak_buffile'

In that case, **ctrl** and **x** are bound to save the file and invoke
the shell command.

If other options are needed then specify it accordingly

**References**

[kakoune
mapping](https://github.com/mawww/kakoune/blob/master/doc/pages/mapping.asciidoc)

[Kakoune normal mode
commands](https://github.com/mawww/kakoune/wiki/Normal-mode-commands)
:::
:::
:::

