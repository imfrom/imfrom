---
title: "Wps Office Spanish Dictionary"
date: 2019-12-30T22:51:32-05:00
draft: true
---

I've installed many text formatting processors over the years, or as they are simply abbreviated with the acronyms WYSIWYG...

Although many users prefer the advantages provided by a cloud stored-word processing program such as the one provided by Google, I tend to steer away from it mainly because of response time within the application. 

But I'm not oblivious either to the fact that the versioning control system as it was implemented by Google, is surely a breakthrough innovation among these programs, which needless to say, many of these other programs - including the one provided by Microsoft - at least the one provided for local installation  - has failed to develop such a feature.

For this simple implementation alone I consider it an advantage over any desktop solution.

But when it comes to locally installed programs,  I've tried to consider the pros and cons and one way or another I've always tried to install - as I said earlier - the one with the overall best response time...

For this reason alone - notwithstanding the license under which the program is developed and which its devs and maintainers have put it in use, and which I always encourage to go over some its terms to clarify any further ambiguity,  and also without disregarding either the proprietary background of the company Kingsoft Office, which is the one that came up with the product,  [wps office for linux](https://www.wps.com/linux) provides almost exactly,  what a vendor such as the program that Microsoft has been able to successfully come up with over the years: a whole suite of spreadsheet, word processor, and presentation programs.

As it's usually the case whenever I'm using this program, I've always toggled back and forth between languages and the dictionaries in use, and even though is no less true that one could easily go directly to whatever pre-compiled version the distribution has put together for the user, to have it installed on the machine nonetheless -- along with the language pack for it -- , is not clearly documented. And to make this issue less straightforward than what it ought to be, the devs have modified or for a better usage of the word - have diverged over the years  as to where the destination directories for these dictionaries are to be placed under. 

For example, at one given point in time, the company provided the download link for the language of choice by making it  available by simply clicking  directly on their website, but for one reason or another I've recently found that the link was no longer accessible.

As I've said before, the distro would most likely have the language pack of choice available for the system.

But I personally didn't want to go this route this time around neither, and wanted instead,  to install the language pack so the program would identify it.

The destination for the dictionaries is not under `.local` but rather over at 

```
/usr/lib/office6/
```

therein another subdirectory under `dicts` aptly entitled `spellcheck/` which further shows the default language directory - which is normally **en_US** in this case, is the folder from which the program would first look up any relevant file to be loaded.

The language pack dictionary for wps-office namely provides three (3) files with the suffixes: 

* *.dic
* *.aff
* *.conf
 
All of these files must be copied over to a newly created directory under the same subdirectory `dicts/spellcheck` as it was outlined earlier.

Make sure the directory for which these other language files are to be put under, is   either copied in its entirety - the whole directory with all the aforementioned files - or that the directory in question is indeed created from scratch... There's no other way around this issue, as long as wps-office identifies and recognizes multiple dictionaries to be loaded up as soon as the program starts. 

The filenames for all the dictionaries - whether these are from the packaged **en_US**, or **en_GB**, or **es_ES**, or **es_MX** etc all have identical names, thus:

* main.dic
* main.aff
* dict.conf

comprise the ~~file~~ directory list....

That's why I - without trying to sound pedantic - brought up the reason as by which one must be careful,  not to simply copy over just the additional files for the other language to be used, as this could potentially **overwrite** the rest.

The other option would be by trying to **rename** the files -- from say a hunspell installation -- to `main.aff`, `main.dic`, and modifiy the contents of the file `dict.conf` respectively to the preferred  language in question.

