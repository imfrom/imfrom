---
title: "Kakoune Macros Recording and Replay"
date: 2019-02-06T03:28:11-04:00
draft: true
---

One of the features for which I personally would have a use for, would
be macros recording and playback.

To read about this on the doc page for **kakoune**, `:doc keys macros`
might give you an idea that by default **Q** starts or ends macro
recording, while **q** replays it.

the `<esc>` key also ends the macro recording.

See [Kakoune
Macros](https://github.com/mawww/kakoune/blob/master/doc/pages/keys.asciidoc#macros)

But further description for the macros recording and playback, is not
provided on the doc page for **Kakoune**.

The author advises to consult the `:doc registers` for further info.

As the doc states

> Registers are named lists of text -instead of simply text- in order to
> interact well with multiselection. They are used for various purposes,
> like storing the last yanked text, or the captured groups associated
> with the selections.

And about interacting with it:

> `<c-r><c>` when in insert mode or in a prompt, insert the value stored
> in the c register (single character)

> `"<c>` in normal mode, select the register (single character)

But unlike **vim** in which a macro is replayed by preceding the
register with the macro **@**, on **kakoune**, the double quote along
with register `<key>` must precede the macro key, which in this case is
`q` that\'s bound to the default register **@**

Ignorant of this fact, mixed with the confusion that stemmed primarily
from the habit of using a workflow from **vim**, disallowed me to fully
comprehend that in order to replay the macro, the register (whatever
this one may be) must supersede the double quote `"`, followed in the
end by the default register `q` which in turn, fully replays the
specified macro.

After going over it, this may simply seem to have been just an oversight
on my part since such an obvious step to record and replay the macro, is
evident, but considering I\'ve been used to **vim**, it was not at all
clear at first, what the steps may have been, mainly in order to replay
the macro on Normal mode. On **Insert** and **Prompt** mode, however,
the documentation provided all the details.

So to record the macro

     " <key> Q <esc> 

And to replay the macro

     " <key> q 

**References**

[Kakoune
Macros](https://github.com/mawww/kakoune/blob/master/doc/pages/keys.asciidoc#macros)

[Kakoune
registers](https://github.com/mawww/kakoune/blob/master/doc/pages/registers.asciidoc)

**Other useful links**

[A vim user\'s comparison between vim and
kakoune](https://www.reddit.com/r/vim/comments/5icmak/a_vim_users_comparisation_between_kakoune_and_vim/)
:::
:::
:::

