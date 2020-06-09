---
layout: 
title: "Clamav Freshclam Update Definitions"
date: 2018-08-28T01:29:48-05:00
draft: true
---

as the <a href="https://wiki.archlinux.org/index.php/ClamAV" target="_blank">ClamAV arch linux wiki</a> states, **ClamAV** is:

>Clam AntiVirus is an open source (GPL) anti-virus toolkit for UNIX. It provides a number of utilities including a flexible and scalable multi-threaded daemon, a command line scanner and advanced tool for automatic database updates. Because ClamAV's main use is on file/mail servers for Windows desktops, it primarily detects Windows viruses and malware with its built-in signatures.

In order to update the definitions correctly is important to run first 

     freshclam

which should then start the update 


     ClamAV update process started at Tue Aug 28 01:16:43 2018
     Downloading main.cvd [100%]
     main.cvd updated (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
     Downloading daily.cvd [100%]
     daily.cvd updated (version: 24880, sigs: 2066436, f-level: 63, builder: neo)
     Downloading bytecode.cvd [100%]
     bytecode.cvd updated (version: 327, sigs: 91, f-level: 63, builder: neo)
     Database updated (6632776 signatures) from database.clamav.net (IP: )

But then an error came up saying that:

     WARNING: Clamd was NOT notified: Can't connect to clamd through /run/clamav/clamd.ctl: No such file or directory


which left me unsure what could have been the issue.

Googling about it returned among many of the results, some as in <a href="https://www.linuxquestions.org/questions/linux-server-73/can%27t-connect-to-unix-socket-var-run-clamav-clamd-ctl-connection-refused-856847/" target="_blank">Can't connect to Unix socket /var/run//clamav/clamd.ctl</a>, which dealt with the issue.

The error here in which it dealt with **clamd.ctl** and not with **clamd.sock connect ()** as it was posted on the entry entitled <a href="https://wiki.archlinux.org/index.php/ClamAV#Error:_Clamd_was_NOT_notified" target="_blank">Error Clamd was not notified</a>.

But after running 

      freshclam

I had already forgotten to start/enable `clamav-freshclam.service` as outlined on the Wiki <a href="https://wiki.archlinux.org/index.php/ClamAV#Updating_database" target="_blank">ClamAV updating database</a>

so

     systemctl start clamav-freshclam.service
     systemctl enable clamav-freshclam.service

Which returned:

`Created symlink /etc/systemd/system/multi-user.target.wants/clamav-freshclam.service → /usr/lib/systemd/system/clamav-freshclam.service.` 

Later on by calling the status of that service with

     systemctl status clamav-freshclam.service

returned 

     Aug 28 01:23:43  systemd[1]: Started ClamAV virus database upda>
     Aug 28 01:23:43  freshclam[]: ClamAV update process started>
     Aug 28 01:23:43  freshclam[]: main.cvd is up to date (versi>
     Aug 28 01:23:43  freshclam[]: daily.cvd is up to date (vers>
     Aug 28 01:23:43  freshclam[]: bytecode.cvd is up to date


But whether it would be necessary to enable it every time it restarts, it's something that I will deal with later on. I only needed it this time around to check some files, and that was the purpose of running it in the first place.
