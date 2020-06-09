---
layout: 
title: "Error While Reinstalling All Previously Deployed Packages of Context User"
date: 2018-11-26T01:25:37-05:00
draft: true
---

I still don't know whether there was an old installation of Libreoffice sitting somewhere on the system. But a new fresh installation not only failed to start up but it also returned the message error `Error while reinstalling all previously deployed packages of context user`.

Looking up Google didn't help in finding some sort of recent info about this issue. 

I also had a `warning: failed to load path from javadlx` which was obviously only a warning but nonetheless troublesome and problematic considering that this was just a fresh installation of Libreoffice.

Further looking up this issue through Google led me to the forum of Arch in which a user mentioned the possibility of permission problems with the installation. The user also queried Google to find more about this issue:

>Googling about the error showed some chances of being a permission problem with ~/.openoffice.org2. But I don't have that directory in my system, but ~/.config/.libreoffice. I would suggest you check the permissions on this directory. Mine are 766. <a href="#javadlx"><sup id="javadlxref">1</sup></a>

but there was nothing out of the norm with the permissions set on the directory. But from his post it reminded me that usually the path that is set by xdg is under the **xdg** directory. Then again, the environment variable for it had been set correctly.

I decided to go ahead and back up the `.config/libreoffice/4` directory where some of the other files for libreoffice laid at. 

Then I moved that directory with all the files to another location, following by calling out `libreoffice` which seemed to resolve the issue.

One of the first hits provided by Google after my first inquiry, were from the forums at the libreoffice website itself, in which one of the threads that also dealt with this issue had mentioned the same workaround that I had just used. See more at <a href="https://forum.openoffice.org/en/forum/viewtopic.php?f=101&t=83995" target="_blank">LO5.0 Fatal Error cannot be started</a>.<a href="#oocontextuser"><sup id="oocontextuserref">2</sup></a>

Further queries that would shed more light about this problem, took me to a previous probable bug that was reported to the <a href="https://bugs.documentfoundation.org/show_bug.cgi?id=64606" target="_blank">documentfoundation.org</a> website. This report was opened on 2013 and closed right after around 2014. <a href="#docfoundation"><sup id="docfoundationref">3</sup></a>

Why that bug report at the documentfoundation.org website was marked as closed shortly after it was reported, is simply beyond me.

The report occurred under version 5 whereas in my case, it was under version 6. And the problem is still there.


**References**

1- <a name="javadlx"></a><a href="https://bbs.archlinux.org/viewtopic.php?pid=1003045#p1003045" target="_blank">Permission problem with Libreoffice - Arch linux forums</a><a href="#javadlxref">&crarr;</a>

2- <a name="oocontextuser"></a> <a href="https://forum.openoffice.org/en/forum/viewtopic.php?f=101&t=83995" target="_blank">LO5.0 Fatal error cannot be started</a> <a href="#oocontextuserref">&crarr;</a>

3- <a name="docfoundation"></a> <a href="https://bugs.documentfoundation.org/show_bug.cgi?id=64606" target="_blank">bug filed with documentfoundation.org</a><a href="#docfoundationref">&crarr;</a>



