---
layout: 
title: "Reply to Email With Mutt on Xfce"
date: 2019-02-01T01:35:59-05:00
draft: true
---

After looking at various ways to reply to an email address through mutt along with the terminal of choice, the <a href="https://docs.xfce.org/xfce/exo/preferred-applications" target="_blank">xfce docs website</a> did not provide me with all the needed details in this case.

I knew that by going to **Preferred Applications** one would have to further specify the corresponding commands under the **Mail Reader** application. But although it did pointed this out by running

    $ exo-open --launch TerminalEmulator mutt

on the terminal, this, however, does not work. The terminal of choice will not open accordingly.

Further queries about this problem led me to a post from the Northern Virginia Linux Users Group.

On this <a href="http://www.firemountain.net/pipermail/novalug/2013-January/033997.html" target="_blank">post</a>, one of the users pointed out that by launching, say, **xterm** with the **-e** option, this would be more than enough to open the file in question. 

     exo-open --launch 'xterm -e'

But this is wrong, since **TerminalEmulator** needs to be specified.

On another <a href="http://www.firemountain.net/pipermail/novalug/2013-January/034003.html" target="_blank">post</a> closely related under the same thread, another user specified that the **--launch** option needed a "category." It wouldn't be difficult to find out what the category he was referring to, may be. In this case, even the already mentioned link from <a href="http://www.firemountain.net/pipermail/novalug/2013-January/033997.html" target="_blank">xfce docs</a> had already pointed out.

The man page for <a href="https://jlk.fjfi.cvut.cz/arch/manpages/man/xterm.1" target="_blank">xterm</a> says about the **-e** option that it will

     -e program [ arguments ... ]
     This option specifies the program (and its command line arguments) to be run in the xterm window. It also sets the window title and icon name to be the basename of the program being executed if neither -T nor -n are given on the command line.

To wrap it all up, quotes `'` are indeed needed to call out the preferred terminal - which in my case is xterm - and finally bring out the mail reader. The option **-e** is needed as well, along with the path to the mutt configuration file.

     exo-open --launch TerminalEmulator 'xterm mutt -f /path/to/configuration/file "%s"'

or if one is using neomutt, change the **-f** option accordingly to **-F**.


     exo-open --launch TerminalEmulator 'xterm neomutt -F /path/to/configuration/file "%s"'


