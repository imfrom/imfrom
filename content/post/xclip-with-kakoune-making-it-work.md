---
layout: 
title: "Xclip With Kakoune Making It Work"
date: 2019-03-25T00:01:13-04:00
draft: true
---
 
One of the pressing issues with Kakoune is the implementation
of `xclip` to use the clipboard selections.

As the <a href="https://github.com/mawww/kakoune/wiki/Registers---Clipboard/" target="_blank">Kakoune Registers -- Clipboard Wiki</a> states it: 

>Notice that <a href="https://github.com/mawww/kakoune/issues/2325" target="_blank">xclip will not work using this example</a>

This was one of the reasons why I wanted to delve further into this issue.

Anyhow, I'll copy-paste the various sections from the <a href="https://github.com/mawww/kakoune/wiki/Registers---Clipboard/" target="_blank">Kakoune Registers - Clipboard Wiki</a> that show a better overview of the steps to follow by adding the snippets into the initialization file, while using `xsel`. Then I will tweak around with the `xclip` features by using the three clipboards that `xclip` uses, namely, `p` (primary), `sec` (secondary), and finally `clip` for the clipboard.

Those are the options available by the use of `xclip`.

### Using the System Clipboard
You can use kakoune with [system clipboard tools](https://wiki.archlinux.org/index.php/Clipboard) like `xsel`, `xclip` or `pbcopy`/`pbpaste` 

### To yank (copy)
`<a-|> xsel --input --clipboard <ret>`

`<a-|>` pipes each selection through the given external filter program and ignore its output.

You may want to use the following hook to automate the dialog with the system clipboard, on each `y`, `d` or `c` operations:

```
      hook global NormalKey y|d|c %{ nop %sh{
              printf %s "$kak_main_reg_dquote" | xsel --input --clipboard
      }}
      
```

### To paste

`! xsel --output --clipboard <ret>`

`!` inserts program output before selection while `<a-!>` inserts program output after selection.

Therefore you can add the following mappings:

### Paste before
`map global user P '!xsel --output --clipboard<ret>'`

### Paste after
`map global user p '<a-!>xsel --output --clipboard<ret>'`

### How to use it now
* y/d - yank/delete using internal clipboard AND system clipboard at once
* p   - paste from internal clipboard
* <,p> - paste after from system clipboard (, is default for user mode)
* <,P> - paste before from system clipboard (, is default for user mode)

## How to make it work with Xclip instead.

As I've found out, and as the issue clearly showed, this is not
currently possible by using Xclip under Kakoune, except of course by mapping
a key to Normal mode and then calling out `xclip`.

As the [freedesktop.org](https://specifications.freedesktop.org/clipboards-spec/clipboards-latest.txt)  website states it, this is not a task
that can be easily done as long as different clients have different methods that make use of these `clipboard` features. 

quoting from the [clipboards specifications freedesktop](https://specifications.freedesktop.org/clipboards-spec/clipboards-latest.txt)

>There are two historical interpretations of the ICCCM:

> a) use PRIMARY for mouse selection, middle mouse button paste, and
>    explicit cut/copy/paste menu items (Qt 2, GNU Emacs 20)
>
> b) use CLIPBOARD for the Windows-style cut/copy/paste menu items;
>    use PRIMARY for the currently-selected text, even if it isn't
>    explicitly copied, and for middle-mouse-click (Netscape, Mozilla,
>    XEmacs, some GTK+ apps)

>No one ever does anything interesting with SECONDARY as far as I can
>tell.

>The current consensus is that interpretation b) is correct. Qt 3 and
>GNU Emacs 21 will use interpretation b), changing the behavior of
>previous versions.

And it follows with:

>In addition, the ICCCM has a thing called "cut buffers" which most
>clients no longer support.
>
>There are two historical interpretations of the ICCCM:
>
> a) use PRIMARY for mouse selection, middle mouse button paste, and
>    explicit cut/copy/paste menu items (Qt 2, GNU Emacs 20)
>
> b) use CLIPBOARD for the Windows-style cut/copy/paste menu items;
>    use PRIMARY for the currently-selected text, even if it isn't
>    explicitly copied, and for middle-mouse-click (Netscape, Mozilla,
>    XEmacs, some GTK+ apps)

And it summarizes it among many points with the following:


>The correct behavior can be summarized as follows: CLIPBOARD works
>just like the clipboard on Mac or Windows; it only changes on explicit
>cut/copy. PRIMARY is an "easter egg" for expert users, regular users
>can just ignore it; it's normally pastable only via
>middle-mouse-click.

So the best course of action, since `xclip` is known to be
working fine under [vim](https://vim.org) or
[neovim](https://neovim.org), would be to map say in this
case, the `Y` key for yanking out operations, and the `P` key
for pasting the selection.

Of course, if other operations such as `delete` or `change`
as Kakoune currently employs, need to be mapped, I believe
that the keys can be assigned their own combinations.

We normally use the `clipboard` rather than the `primary` or
`secondary` X selections:

## To yank with Xclip

     map global normal <Y> ' $ xclip -select clip '

## To paste with Xclip

And to paste

     map global normal P '<!> xclip -select clip -o'


## Freeing register `"` on Kakoune and yanking with p

The above mapping of both the `Y` or `P` key registers,
do not restrain the operations by which `y` that records the
operation to register `"`  or `p` that pastes it.

There's no possible way to do it with the otherwise rest of
the `clipboards` options that `xclip` uses, without further
noticing that the register `y` that is used for normal
yanking operations under Kakoune, wouldn't work as expected.
And neither by pastting that same register `"`.

...

**Other references**

<a href="https://unix.stackexchange.com/questions/22494/copy-file-to-xclip-and-paste-to-firefox" target="_blanK">unix stackexchange -- copy file to xclip and paste on firefox</a>
