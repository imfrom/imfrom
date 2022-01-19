---
title: "Setup Network Printer Ip Address Port Number"
date: 2018-08-10T01:31:19-05:00
draft: true
---

Setting up a network printer seems not only problematic on Arch based systems, but also on Windows.

The latter also gave me the proverbial run for the money.

Even after I thought that the network printer had be configured correctly, errors such as `there was a problem processing document` after printing a test page, or simply the error stating that `the printer may not be connected` assured me that the network printer was not being correctly identified.

**C**ommon **U**nix **P**rinting **S**ervices or as its acronym that is better known for: CUPS, is without a doubt, the most reliable method to set up any printer, and especially those that depend upon a network to operate accordingly.

It was not the first time setting up a network printer through CUPS, but
contrary to the first time around when the printer was successfully configured
on the system, in which the ip address had to be specified, and the connection
port number of the socket was automatically picked up by CUPS, this time around
however, specifying the ip address by itself made no difference with further
configuration. 

The printer was still not recognized.

I scoured Google for any relevant results that would help me troubleshoot the problem, but none of the results seemed to provide a definitive answer.

The Arch Linux Forums was one of the first indicators that this issue was beyond a driver problem and rather a misconfiguration with the network printer.

On the thread entitled _Printer setting cant find wireless printer_, a <a href="https://bbs.archlinux.org/viewtopic.php?pid=1605184#p1605184" target="_blank">reply provided</a> gave a couple of hints as to where to begin to troubleshot the problem.

>Your post is much too vague. What does your wireless printer advertise? You should be able to add it using its IP address in the CUPS interface like this: http://192.168.1.3. You need to replace 192.168.1.3 by the IP of your printer and http:// could be socket:// lpd:// or something else... Maybe you also have to specify a port number like this: http://192.168.1.3:9100. If you can setup the printer in another OS (for example Windows); you might be able to find these by examining the properties of the printer.

The problem with Windows however, is that Windows itself does not provide a simple port configuration method that would have allowed me to see the ip address and the port that was currently in use.

This time around CUPS had already specified the ip address and the connection for the socket. But everything else for even the location had already been noted. Furthermore, I double checked it against the settings for the wireless configuration of the printer. Not solely relying on whatever configuration the display showed but also by printing out right from the printer the specifics of the configuration.

When I ventured out to get a glimpse through a Windows system that would allow me to double check the settings, I encountered though, an unforeseen `An error occurred during port configuration. This operation is not supported` which prevented me any further from finding out about the ip address and port number configuration.

![](/images/windows-port-error-configuration.png)

This however, was not expected.

On this question that was brought up on the stackexchange network, the user asked <a href="https://unix.stackexchange.com/questions/140009/list-all-network-printers-including-ones-not-installed" target="_blank">to list all network printers (including ones not installed)</a> and although it hinted that the program **lpstat** with the flag `-a` was one that would undertake the task, as the user pointed out, this would not apply to those printers that have not been installed. 

Another command that would certainly come handy is `lpinfo -v` but more than what it provided was therefore needed.

On another thread entitled <a href="https://superuser.com/questions/662418/how-do-i-get-the-name-of-a-network-printer" target="_blank">linux - how do you get the name of a network printer</a> one of the comments said that:

>When I run the nmap command it never seems to complete.

https://superuser.com/questions/662418/how-do-i-get-the-name-of-a-network-printer#comment836711_662485

which pretty much matches many of the issues that I have encountered with the program.

The only workaround with this pervasive problem of a printer that depends solely on the network, is through some sort of initial setup performed namely through a Windows system that would point it out. Unlike Linux with its **C**ommon **U**nix **P**rinting **S**ervices in which by just confirming the correct ip address and port numbers of the printer are under , is more than enough to identify it accordingly.  Until then, and just like a user on the Arch Forums said:

>The problem here is that the criteria ("Network Printer") is something that only makes sense to humans. Computer programs aren't going to have a clear sense of that idea. You might try doing a network sweep for IP addresses that successfully connect on the JetDirect port (tcp/9100). The list is still likely to be incomplete in the case of non-JetDirect printers such as desktop printers shared over SMB. – Bratchley Jun 30 '14 at 18:16

**References**

<a href="https://unix.stackexchange.com/questions/140009/list-all-network-printers-including-ones-not-installed#comment226003_140009" target="_blank">unix.stackexchange.com/questions/140009/list-all-network-printers-including-ones-not-installed#comment226003_140009</a>

<a href="https://www.uvm.edu/cosmolab/om/brother/html/nug/chapter2.html" target=_blank"> 2 Configuring your printer for a networt</a>

