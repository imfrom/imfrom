---
title: "Guake Module Not Found Pbr — no module named pbr"
date: 2021-10-27T04:08:20-04:00
draft: true
---

As I decided to run slackware current rather than 14.2, as I had done before, there were perhaps a couple of packages that although were not officially supported, had to be manually configured and compiled again. 

Among these packages was the drop-down terminal **guake**. Unlike **yakuake**, which is normally configured without a major setback, running 14.2 required at one point to have vte3 installed, as well as pbr.

The latter one however, proved to be a chore.

The error `error: invalid command 'bdist_wininst'` kept coming up without further info. A quick googling around this problem led me to actually nowhere, since one of the comments mentioned about removing support for **wininst** but this [https://github.com/pypa/setuptools/issues/857#issuecomment-273274212](comment) dated as far back as 2017.

Another error that showed up — no matter what I did to circumvent it during the installation of guake — was the most infamous of all:

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

## Some notes with python3.9 and/or python3 that may be in conflict with sbopkg

I think this part is utterly important as well

First, and just as it was clarified before with the use of say, either `python -m pip install guake` or `python3 -m pip install guake` respectively. one must remember, as long as **sbopkg** is the preferential method to install **guake**, to either remove any of these packages.

Usually `pip` will install it under `.local/` variables and place the executable under the same directory

If one were to invoke (as I had done before) plain `pip uinstall guake` 

Then, it will only return, That is

```
.local/bin/guake
.local/bin/guake-toggle
.local/lib/python3.9/site-packages/guake-3.8.5.dist-info/*
.local/lib/python3.9/site-packages/guake/*
Proceed (Y/n)? n

```

Whkereas for example, running python on the other hand, with the correct **python -m pip uninstall guake**

will include most subdirectories under `.local/` 

```
Found existing installation: guake 3.7.0
Uninstalling guake-3.7.0:
  Would remove:
    .local/bin/guake
    .local/bin/guake-toggle
    .local/lib64/python2.7/site-packages/guake-3.7.0.dist-info/*
    .local/lib64/python2.7/site-packages/guake/*
    .local/share/guake/po/LINGUAS
    .local/share/guake/po/ca.mo
    .local/share/guake/po/ca.po
    .local/share/guake/po/cs.mo
    .local/share/guake/po/cs.po
    .local/share/guake/po/de.mo
    .local/share/guake/po/de.po
    .local/share/guake/po/el.mo
    .local/share/guake/po/el.po
    .local/share/guake/po/es.mo
    .local/share/guake/po/es.po
    .local/share/guake/po/fa.mo
    .local/share/guake/po/fa.po
    .local/share/guake/po/fr.mo
    .local/share/guake/po/fr.po
    .local/share/guake/po/gl.mo
    .local/share/guake/po/gl.po
    .local/share/guake/po/guake.pot
    .local/share/guake/po/hr.mo
    .local/share/guake/po/hr.po
    .local/share/guake/po/hu.mo
    .local/share/guake/po/hu.po
    .local/share/guake/po/id.mo
    .local/share/guake/po/id.po
    .local/share/guake/po/it.mo
    .local/share/guake/po/it.po
    .local/share/guake/po/ja.mo
    .local/share/guake/po/ja.po
    .local/share/guake/po/ko.mo
    .local/share/guake/po/ko.po
    .local/share/guake/po/nb.mo
    .local/share/guake/po/nb.po
    .local/share/guake/po/nl.mo
    .local/share/guake/po/nl.po
    .local/share/guake/po/pa.mo
    .local/share/guake/po/pa.po
    .local/share/guake/po/pl.mo
    .local/share/guake/po/pl.po
    .local/share/guake/po/pt_BR.mo
    .local/share/guake/po/pt_BR.po
    .local/share/guake/po/ru.mo
    .local/share/guake/po/ru.po
    .local/share/guake/po/sv.mo
    .local/share/guake/po/sv.po
    .local/share/guake/po/tr.mo
    .local/share/guake/po/tr.po
```

The package **pbr** is also available on both **sbopkg** as well as through pip as well

What I have done in the past is to download and build throgh **sbopkg** just in case, there have been prior upgrades.

This is after downloading and building again:

```
Installing guake-toggle script to /tmp/SBo/package-guake/usr/bin

Slackware package maker, version 3.14159265.

Searching for symbolic links:

No symbolic links were found, so we won't make an installation script.
You can make your own later in ./install/doinst.sh and rebuild the
package if you like.

This next step is optional - you can set the directories in your package
to some sane permissions. If any of the directories in your package have
special permissions, then DO NOT reset them here!

Would you like to reset all directory permissions to 755 (drwxr-xr-x) and
directory ownerships to root.root ([y]es, [n]o)? n

Creating Slackware package:  /tmp/sbopkg.OElwoH/sbopkg-sbooutputdir/guake-3.7.0-x86_64-1ponce.tgz

./
install/
install/doinst.sh
install/slack-desc
usr/
usr/bin/
usr/bin/guake
usr/bin/guake-toggle
usr/doc/
usr/doc/guake-3.7.0/
usr/doc/guake-3.7.0/COPYING
usr/doc/guake-3.7.0/NEWS.rst
usr/doc/guake-3.7.0/README.rst
usr/doc/guake-3.7.0/guake.SlackBuild
usr/lib64/
usr/lib64/python3.9/
usr/lib64/python3.9/site-packages/
usr/lib64/python3.9/site-packages/guake/
usr/lib64/python3.9/site-packages/guake-3.7.0-py3.9.egg-info/
usr/lib64/python3.9/site-packages/guake-3.7.0-py3.9.egg-info/PKG-INFO
usr/lib64/python3.9/site-packages/guake-3.7.0-py3.9.egg-info/SOURCES.txt
usr/lib64/python3.9/site-packages/guake-3.7.0-py3.9.egg-info/dependency_links.txt
usr/lib64/python3.9/site-packages/guake-3.7.0-py3.9.egg-info/entry_points.txt
usr/lib64/python3.9/site-packages/guake-3.7.0-py3.9.egg-info/not-zip-safe
usr/lib64/python3.9/site-packages/guake-3.7.0-py3.9.egg-info/pbr.json
usr/lib64/python3.9/site-packages/guake-3.7.0-py3.9.egg-info/requires.txt
usr/lib64/python3.9/site-packages/guake-3.7.0-py3.9.egg-info/top_level.txt
usr/lib64/python3.9/site-packages/guake/__init__.py
usr/lib64/python3.9/site-packages/guake/__pycache__/
usr/lib64/python3.9/site-packages/guake/__pycache__/__init__.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/__init__.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/about.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/about.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/boxes.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/boxes.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/callbacks.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/callbacks.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/common.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/common.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/customcommands.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/customcommands.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/dbusiface.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/dbusiface.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/dialogs.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/dialogs.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/globals.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/globals.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/gsettings.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/gsettings.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/guake_app.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/guake_app.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/guake_logging.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/guake_logging.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/guake_toggle.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/guake_toggle.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/keybindings.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/keybindings.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/main.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/main.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/menus.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/menus.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/notebook.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/notebook.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/notifier.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/notifier.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/palettes.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/palettes.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/paths.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/paths.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/prefs.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/prefs.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/settings.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/settings.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/simplegladeapp.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/simplegladeapp.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/split_utils.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/split_utils.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/support.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/support.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/terminal.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/terminal.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/theme.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/theme.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/utils.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/__pycache__/utils.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/about.py
usr/lib64/python3.9/site-packages/guake/boxes.py
usr/lib64/python3.9/site-packages/guake/callbacks.py
usr/lib64/python3.9/site-packages/guake/common.py
usr/lib64/python3.9/site-packages/guake/customcommands.py
usr/lib64/python3.9/site-packages/guake/data/
usr/lib64/python3.9/site-packages/guake/data/__init__.py
usr/lib64/python3.9/site-packages/guake/data/__pycache__/
usr/lib64/python3.9/site-packages/guake/data/__pycache__/__init__.cpython-39.opt-1.pyc
usr/lib64/python3.9/site-packages/guake/data/__pycache__/__init__.cpython-39.pyc
usr/lib64/python3.9/site-packages/guake/data/about.glade
usr/lib64/python3.9/site-packages/guake/data/autostart-guake.desktop
usr/lib64/python3.9/site-packages/guake/data/guake-prefs.template.desktop
usr/lib64/python3.9/site-packages/guake/data/guake.appdata.xml
usr/lib64/python3.9/site-packages/guake/data/guake.glade
usr/lib64/python3.9/site-packages/guake/data/guake.template.desktop
usr/lib64/python3.9/site-packages/guake/data/org.guake.gschema.xml
usr/lib64/python3.9/site-packages/guake/data/pixmaps/
usr/lib64/python3.9/site-packages/guake/data/pixmaps/add_tab.png
usr/lib64/python3.9/site-packages/guake/data/pixmaps/guake-128.png
usr/lib64/python3.9/site-packages/guake/data/pixmaps/guake-48.png
usr/lib64/python3.9/site-packages/guake/data/pixmaps/guake-64.png
usr/lib64/python3.9/site-packages/guake/data/pixmaps/guake-notification.png
usr/lib64/python3.9/site-packages/guake/data/pixmaps/guake-tray.png
usr/lib64/python3.9/site-packages/guake/data/pixmaps/guake-tray.svg
usr/lib64/python3.9/site-packages/guake/data/pixmaps/guake.png
usr/lib64/python3.9/site-packages/guake/data/pixmaps/intro-large.jpg
usr/lib64/python3.9/site-packages/guake/data/pixmaps/intro-medium.jpg
usr/lib64/python3.9/site-packages/guake/data/pixmaps/intro-small.jpg
usr/lib64/python3.9/site-packages/guake/data/pixmaps/quick-open-python-exception.png
usr/lib64/python3.9/site-packages/guake/data/pixmaps/quick-open-selection.png
usr/lib64/python3.9/site-packages/guake/data/pixmaps/quick-open.png
usr/lib64/python3.9/site-packages/guake/data/pixmaps/screenshot-fullscreen.jpg
usr/lib64/python3.9/site-packages/guake/data/pixmaps/screenshot-small.jpg
usr/lib64/python3.9/site-packages/guake/data/prefs.glade
usr/lib64/python3.9/site-packages/guake/data/search.glade
usr/lib64/python3.9/site-packages/guake/dbusiface.py
usr/lib64/python3.9/site-packages/guake/dialogs.py
usr/lib64/python3.9/site-packages/guake/globals.py
usr/lib64/python3.9/site-packages/guake/gsettings.py
usr/lib64/python3.9/site-packages/guake/guake_app.py
usr/lib64/python3.9/site-packages/guake/guake_logging.py
usr/lib64/python3.9/site-packages/guake/guake_toggle.py
usr/lib64/python3.9/site-packages/guake/keybindings.py
usr/lib64/python3.9/site-packages/guake/main.py
usr/lib64/python3.9/site-packages/guake/menus.py
usr/lib64/python3.9/site-packages/guake/notebook.py
usr/lib64/python3.9/site-packages/guake/notifier.py
usr/lib64/python3.9/site-packages/guake/palettes.py
usr/lib64/python3.9/site-packages/guake/paths.py
usr/lib64/python3.9/site-packages/guake/prefs.py
usr/lib64/python3.9/site-packages/guake/settings.py
usr/lib64/python3.9/site-packages/guake/simplegladeapp.py
usr/lib64/python3.9/site-packages/guake/split_utils.py
usr/lib64/python3.9/site-packages/guake/support.py
usr/lib64/python3.9/site-packages/guake/terminal.py
usr/lib64/python3.9/site-packages/guake/theme.py
usr/lib64/python3.9/site-packages/guake/utils.py
usr/share/
usr/share/applications/
usr/share/applications/guake-prefs.desktop
usr/share/applications/guake.desktop
usr/share/glib-2.0/
usr/share/glib-2.0/schemas/
usr/share/glib-2.0/schemas/org.guake.gschema.xml
usr/share/guake/
usr/share/guake/about.glade
usr/share/guake/autostart-guake.desktop
usr/share/guake/guake.glade
usr/share/guake/pixmaps/
usr/share/guake/pixmaps/add_tab.png
usr/share/guake/pixmaps/guake-128.png
usr/share/guake/pixmaps/guake-48.png
usr/share/guake/pixmaps/guake-64.png
usr/share/guake/pixmaps/guake-notification.png
usr/share/guake/pixmaps/guake-tray.png
usr/share/guake/pixmaps/guake-tray.svg
usr/share/guake/pixmaps/guake.png
usr/share/guake/pixmaps/quick-open-python-exception.png
usr/share/guake/pixmaps/quick-open-selection.png
usr/share/guake/pixmaps/quick-open.png
usr/share/guake/prefs.glade
usr/share/guake/search.glade
usr/share/locale/
usr/share/locale/ca/
usr/share/locale/ca/LC_MESSAGES/
usr/share/locale/ca/LC_MESSAGES/guake.mo
usr/share/locale/cs/
usr/share/locale/cs/LC_MESSAGES/
usr/share/locale/cs/LC_MESSAGES/guake.mo
usr/share/locale/de/
usr/share/locale/de/LC_MESSAGES/
usr/share/locale/de/LC_MESSAGES/guake.mo
usr/share/locale/el/
usr/share/locale/el/LC_MESSAGES/
usr/share/locale/el/LC_MESSAGES/guake.mo
usr/share/locale/es/
usr/share/locale/es/LC_MESSAGES/
usr/share/locale/es/LC_MESSAGES/guake.mo
usr/share/locale/fa/
usr/share/locale/fa/LC_MESSAGES/
usr/share/locale/fa/LC_MESSAGES/guake.mo
usr/share/locale/fr/
usr/share/locale/fr/LC_MESSAGES/
usr/share/locale/fr/LC_MESSAGES/guake.mo
usr/share/locale/gl/
usr/share/locale/gl/LC_MESSAGES/
usr/share/locale/gl/LC_MESSAGES/guake.mo
usr/share/locale/hr/
usr/share/locale/hr/LC_MESSAGES/
usr/share/locale/hr/LC_MESSAGES/guake.mo
usr/share/locale/hu/
usr/share/locale/hu/LC_MESSAGES/
usr/share/locale/hu/LC_MESSAGES/guake.mo
usr/share/locale/id/
usr/share/locale/id/LC_MESSAGES/
usr/share/locale/id/LC_MESSAGES/guake.mo
usr/share/locale/it/
usr/share/locale/it/LC_MESSAGES/
usr/share/locale/it/LC_MESSAGES/guake.mo
usr/share/locale/ja/
usr/share/locale/ja/LC_MESSAGES/
usr/share/locale/ja/LC_MESSAGES/guake.mo
usr/share/locale/ko/
usr/share/locale/ko/LC_MESSAGES/
usr/share/locale/ko/LC_MESSAGES/guake.mo
usr/share/locale/nb/
usr/share/locale/nb/LC_MESSAGES/
usr/share/locale/nb/LC_MESSAGES/guake.mo
usr/share/locale/nl/
usr/share/locale/nl/LC_MESSAGES/
usr/share/locale/nl/LC_MESSAGES/guake.mo
usr/share/locale/pa/
usr/share/locale/pa/LC_MESSAGES/
usr/share/locale/pa/LC_MESSAGES/guake.mo
usr/share/locale/pl/
usr/share/locale/pl/LC_MESSAGES/
usr/share/locale/pl/LC_MESSAGES/guake.mo
usr/share/locale/pt_BR/
usr/share/locale/pt_BR/LC_MESSAGES/
usr/share/locale/pt_BR/LC_MESSAGES/guake.mo
usr/share/locale/ru/
usr/share/locale/ru/LC_MESSAGES/
usr/share/locale/ru/LC_MESSAGES/guake.mo
usr/share/locale/sv/
usr/share/locale/sv/LC_MESSAGES/
usr/share/locale/sv/LC_MESSAGES/guake.mo
usr/share/locale/tr/
usr/share/locale/tr/LC_MESSAGES/
usr/share/locale/tr/LC_MESSAGES/guake.mo
```








