---
layout: 
title: "Arch Linux Javaws No Such File or Directory"
date: 2019-10-10T00:58:13-04:00
draft: true
---

Trying to get `javaws` to work without a glitch on one of the systems it was tested under, proved to be a chore. 

The executable file was not being recognized in this case, which consequently led me to believe, that during the installation of the program, the path somehow had not been set by the libraries that'd normally take care of it.

All the libraries for which `javaws` depended upon and for which it was being tested even under a different system seemed to have been installed. This included, **jdk8-openjdk..** and its counterparts.

Apparently, during the installation, the path that had been set for `javaws` had been incorrectly identified.  

The error read as follows:

``` 
/usr/bin/javaws line 197: no such file or directory.

```

Upon further inspection of the line in question, is hard to pinpoint whether therein lied the problem or not...

Upon going ahead and after opening the `javaws` executable, I noticed that the path had been incorrectly set indeed by either some of the libraries during the initialization.... It was pointing out to a different location **rather** than where the files for the java environment were located instead. 
 
Modifying the file in question and instructing it to open up without further ado, seemed to resolve the problem. Thus `java=/location/of/java/default/` worked without a problem.
