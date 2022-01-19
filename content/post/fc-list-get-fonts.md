---
title: "Fc-List Get Fonts"
date: 2019-12-23T22:53:32-05:00
draft: true
---


It's always nice to have a 'cheat sheet' summary of all sorts Unix to remember certain programs 

I usually have `Lua` looking this up for me through `otf` and `ttf` fonts, but it's been a while since I went this route.

`fontconfig `takes care of all font-related 


<a href="https://www.freedesktop.org/wiki/Software/fontconfig/" target="_blank">fontconfig</a> takes care -- as the freedesktop.org website states to 

* discover new fonts when installed automatically, removing a common source of configuration problems.

* perform font name substitution, so that appropriate alternative fonts can be selected if fonts are missing.
identify the set of fonts required to completely cover a set of languages.

* have GUI configuration tools built as it uses an XML-based configuration file (though with autodiscovery, we believe this need is minimized).
efficiently and quickly find the fonts you need among the set of fonts you have installed, even if you have installed thousands of fonts, while minimzing memory usage.
*  be used in concert with the X Render Extension and FreeType to implement high quality, anti-aliased and subpixel rendered text on a display.

But it does not provide any searching mechanism to look up a particular font on the system. Or at the very least not one that I'm aware of anyway..

On the other hand, `fc-list` does list the fonts available on the system...

The only caveat is that if I were to try to get the family name of the glyph in question, `fc-list` does provide it, but I would need to further `grep` it in order to not get a bunch of results.

`fc-list` is simply put:

```
FC-LIST(1)                                                     FC-LIST(1)

NAME
       fc-list - list available fonts

SYNOPSIS
       fc-list  [  -vVh ] [ --verbose ] [ -f format | --format format ] [
       -q | --quiet ] [ --version ] [ --help ]
           [ pattern  [ element ... ]  ]

DESCRIPTION
       fc-list lists fonts and styles available on the system for  appli‐
       cations  using  fontconfig.   If  any elements are specified, only
       those are printed.  Otherwise family and style are printed, unless
       verbose output is requested.
```

a printing mechanism to list the fonts on the system.

`grep` [ing] the font itself through the program, filters out the family name of the font as well - and whether these are otf or ttf.

