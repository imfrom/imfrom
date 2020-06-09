---
title: "Error Bash Completion No Such File or Directory"
date: 2020-06-09T02:59:45-04:00
draft: true
---
I wouldn't know where to look —- I certainly can browse the <a href="https://packages.debian.org/buster/bash-completion" target="_blank">repo</a> from Debian reposotiry — or where bash completion is usually installed on Debian-based distributions. It's been a while since I have used these kind of systems. But after all, this is irrelevant. Even as popular as it may,  not everyione uses it.

A quick glance at the files that comprise this program, one could see that aside from the `usr` folder, bash completion is also installed under `etc` and `bin` accordingly.

Bash completion allows to fill in the rest of the commands or variables that follow fora gitven executable.

See <a href="https://wiki.archlinux.org/index.php/Bash#Tab_completion" target="_blank">Bash autocompletion</a> for more details about its chock features' versatility. 

In the case of Arch, the installation does not create — unlike on Debian — the folder `bash_completion` under `etc`. And I don't think this may have been an oversight from the Arch team, but perhaps due to safety reasons,  this was something that was never considered in the first place.

Other programs have had no issue by correctly including on the script the means to have it install appropriately. But it's my opinion — and anyone is more than welcome to disagree with me here — that many a great number of programs have not chosen to do so or failed altogether in this regard. Hugo for example is one of them. See for example the <a href="https://github.com/gohugoio/hugo/pull/1088" target="_blank"> destination directory</a> when this feature was added. See the commit <a href="https://github.com/gohugoio/hugo/pull/1088/commits/ccdf544f73dda2ff2dd8bf0407a77e21084c59e8">here.</a>

To resolve this issue, the most viable solution is to manually add the folder, to where this error stems from, or else the message`Error: bash_completion.d: hugo.sh no such file or directory` will disallow the `autocomplete` which was added to the binaries of this  program, to come into effect. 


