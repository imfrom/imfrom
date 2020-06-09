---
layout: 
title: "Kakoune Matching Pairs"
date: 2019-02-15T03:18:37-05:00
draft: true
---


When I tried to delve further into the issue of highlighters
that were used on kakoune, I was more interested on the
options akin to the ones provided and which have been
implemented on vim or neovim, such as e.g. showmatch,
matchpairs.

On vim this is something that could be easily
obtained by having for example a `set showmatch` on the
initialization file, but on kakoune, and although <a
href="https://github.com/mawww/kakoune/issues/1192">this
issue on github</a> seemed to
point in the right direction, and the <a
href="https://github.com/mawww/kakoune/issues/1192#issuecomment-277494934">accompanying
comment</a> further specified that by having it [the function
show_matching] called out by a hook directly from the configuration
file, it still wouldn't quite load the `add-highlighter` onto the
buffer. 

Perhaps and one of the feasible explanations is that at the
time this issue came up, other changes may have been further
implemented from the developing side, thus preventing from
having this function working as I would have thought, and in
what seemed to be almost a basic functionality.


      hook global WinCreate .* %{
      	addhl show_matching
      }

Without having the above on the config file, I was able to
see from the buffer that the `add-highlighter` option would
come up without a problem, followed by `path/name` and ending
up with `type` and `type params` to be specified accordingly.

Furthermore, calling out both `addhl` with either `global` or
`window` or `buffer` seemed to work fine for `show_matching`
to highlight the opening and closing delimiters. On the
buffer that is, but I needed to have the changes applied
globally and soon after restarting the editor. The settings
needed to be called out directly from the **kakrc** file.

All in all, and after changing the values around to have
`add-highlighter` instead of `addhl` (although I couldn't
think of a valid reason), and further adding to the snippet
some values such as a `buffer` right after `addhl` instead,
I noticed all of it wouldn't add up. The hook had already
specified it as such.

The only thing left was to have `addhl` directly on the
initialization file without invoking a hook.

And that's exactly what I did

     addhl global\ show-matching 

The opening and closing pairs would highlight accordingly.







