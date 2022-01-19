---
title: "Guake Module Not Found Pbr — no module named pbr"
date: 2021-10-27T04:08:20-04:00
draft: true
---

As I decided to run slackware current rather than 14.2, as I had done before, there were perhaps a couple of packages that although were not officially supported, had to be manually configured and compiled again. 

Among these packages was the drop-down terminal **guake**. Unlike **yakuake**, which is normally configured without a major setback, running 14.2 required at one point to have vte3 installed, as well as pbr.

the latter one however, proved to be a chore.

The error `error: invalid command 'bdist_wininst'` kept coming up without further info. A quick googling around this problem led me to actually nowhere, since one of the comments mentioned about removing support for **wininst** but this [https://github.com/pypa/setuptools/issues/857#issuecomment-273274212](comment) dated as far back as 2017.  
Another error that showed up — no matter what I did to circumvent it during the installation of guake — was the most infamous of all. 

guake `ModuleNotFoundError: No module named 'pbr'`

And it made no difference whatsoever whether I had tried to install it to another path as the command `pip install --user guake` as the guake project suggested, or even a `pip3 install guake` as it had been previously suggested over at https://github.com/Guake/guake/issues/1328#. 

Resorting to an old fashioned method such as `python -m pip install guake` as it was outlined on the documentation https://docs.python.org/3/installing/index.html had also proved as useless as anything before it. So there was no easily discernible workaround, or so it seemed, to resolve the issue. 

Normally with `pip` the packages are installed under `$HOME/.local/bin` and even exporting the path made no difference either. 

What gives at this point? The only difference with the current slack were a number of a few packages such as python3 and pygobject among many, that had been upgraded accordingly.

I even went as far as installing `python3-setuptools` on the system, but this, too, resolved nothing. 

And when I tried to find all traces of guake on the system, it did showed up under both python-2 and python-3 dirs respectively. I still don't know whether this may have been one of the underlying causes for the `no module found pbr` message though.

I also downloded guake sources directly from github, and compiled it from thnere, to no further avail either.

I had decided to almost give up on the issue, but as a last resort there was the possibility — even though the chances were slim or so it seemed to successfully install guake and/or pbr.

I went ahead and read on https://sbopkg.org/ after going around on an older thread from 2011 https://www.linuxquestions.org/questions/slackware-14/how-can-i-search-for-unofficial-packages-in-slackware-%2Apackages-like-guake-terminal%2A-888155/ that mentioned it.

After the initial setup and further reading through <a href="https://docs.slackware.com/howtos:slackware_admin:building_packages_with_sbopkg" target="_blank"> documentation for sbopkg</a>,  the first search directly from the terminal returned a `no match found` which took me back to Google again to see what this was about.

Therein one of the most relevant links pointed out to https://www.linuxquestions.org/questions/slackware-14/sbopkg-and-installed-sbo-git-packages-not-appears-4175632613/

Changed to the suggested directory and everything seemed to check accordingly. I had specified the repo directly from sbopkg and synced it afterwards. The configuration file rightly noted the changes.

The first install of guake, however, returned the same error as before. I decided to go ahead and remove `removepkg`anything under /tmp/ with sudo privileges for both `pbr` and `guake`.

Surprisingly, it wasn't until I specified the current Sbo-git and searched the packages interface for both **pbr** and **guake** later on, that the guake compilation went through without further error messages.

Guake returned no errors afterwards. As a matter of fact, I'm writing all of this, hoverever relevant it may be, (and acknowledging failure for not providing a back log that would detail all error messages with both **pbr** and **guake** during these unfinished compilations) by using this fast drop-down terminal. Yakuake also provides a similar interface, and many users from the slackware community may point out, and rightly so, that it works even better than guake, minus the aggravation with unofficial packages such as guake under slackware.

But the bottom line here is: I can't recommend **Sbopkg** highly enough. Whatever the issue there was, with both `pbr` and `guake`, seemed to have been finally resolved. 

I only wished I had tried **sbopkg** sooner. 




