---
title: "Sed and Awk to Print Ranges"
date: 2019-12-27T00:47:09-05:00
draft: true
---


`sed` and `awk` are very powerful tools that would yield results unlike anything else in *Nix.

Although one could certainly create constructs within say a bash script that would give it further fuel, it comes handy to have it as it's always the case: available,  for even other menial tasks.

Printing a given range of lines would undoubtedly come practical during those times when simply displaying them directly by invoking the manual is proven not to be the most straightforward method.

So for this purpose both `sed` and `awk` serve me well.

If I were to invoke with `sed` a certain range of lines to print say from the XParseGeometry manual or from any other file on the system, filtering it out gives - as the proverbial saying goes - power for the money.

Yes, it helps to have the entire `man` pages on the terminal, but it wouldn't filter out the results as I have wanted it to. One may try by using `grep` but I wasn't interested this time around to use it.

So

```
man XParseGeometry | awk 'NR==20,NR==40' 
```


would hence return:

```

       display   Specifies the connection to the X server.

       fheight
       fwidth    Specify the font height and width in  pixels  (increment
                 size).

       parsestring
                 Specifies the string you want to parse.

       screen    Specifies the screen.

       width_return
       height_return
                 Return the width and height determined.

       xadder
       yadder    Specify  additional  interior padding needed in the win‐
                 dow.

       x_return
```

returned what I was after..


With `sed` things are perhps easier, and a great many users recommend to go this route for simple tasks such as the one I usually encounter.

on the terminal 

```
man XParseGeometry | sed -n '20,40'p
```

would rightly return:

```

       display   Specifies the connection to the X server.

       fheight
       fwidth    Specify the font height and width in  pixels  (increment
                 size).

       parsestring
                 Specifies the string you want to parse.

       screen    Specifies the screen.

       width_return
       height_return
                 Return the width and height determined.

       xadder
       yadder    Specify  additional  interior padding needed in the win‐
                 dow.

       x_return
```

which gives me exactly what I was after....


Of course, the magic of Unix doesn't stop there. One could further delve into even more  commands to give both `sed` and `awk` an unimaginable power for pattern searching without having to entirely `grep` it...

Having other simple tasks such as looking up particular pattern on a given file, is much more easier which could print out the results satisfactorily....

for a given file `x`

```
sed -n '2,4'p <filename>
```

and through `awk` a simple

```
awk 'NR==<range>,NR==<range>' <filename>
``` 

should suffice.



**Further reading** 

https://www.grymoire.com/Unix/Sed.html

https://www.grymoire.com/Unix/Awk.html





