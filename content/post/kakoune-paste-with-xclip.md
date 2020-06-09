---
layout: 
title: "Kakoune Paste With Xclip"
date: 2019-02-03T12:44:11-05:00
draft: true
---

The <a href="https://github.com/mawww/kakoune/wiki/Registers---Clipboard"
target="_blank">kakoune wiki on github</a>
goes at length on some of the steps to
to follow in order to paste with the system clipboard

It says to in order to paste before with
**xsel** to

     map global user p '<a-!>xsel --output --clipboard<ret>'
     
     
But in the case of  **xclip** for example,
and by reading the man pages of **xclip** 


     -selection
              specify which X selection to use, options are "primary" to
              use XA_PRIMARY (default), "secondary" for XA_SECONDARY  or
              "clipboard" for XA_CLIPBOARD

and

     
     -o, -out
              print the selection to standard out (generally for  piping
              to a file or program)
              
              
So in order to paste with the system
clipboard by using **xclip** instead,
`clipboard` from **xsel** would have to
be replaced with `selection` from
**xclip**, so something in the lines of 

~~map global normal p '<a-!>xclip -o -s<ret>'~~
      
But rather something like

       map global user p '<a-!>xclip -o -s <ret>'
       
       map global user P '!xclip -o -s <ret>'
       
would suffice.
      
## Updates

I've since stopped using the above since the way that
`xclip` uses many of the
`clipboards` do not seem to behave as expected under
Kakoune. 

`xclip` works without a setback under <a
href="https://www.vim.org" target="_blank">vim</a> or even <a
href="https://neovim.io" target="_blank">neovim</a>, and it
was this that led me to make `xclip` work under Kakoune. 

See the [xclip with kakoune -- making it
work](../xclip-with-kakoune-making-it-work/) for further info.
      




