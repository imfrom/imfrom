---
layout: 
title: "Could Not Satisfy Dependencies Hunspell Antergos Common Meta"
date: 2018-07-18T00:12:54-05:00
---
It seems as if **antergos-common-meta** has been removed
from some of the repositories.

In the latest updates by using pamac or even pacman returned
the *could not satisfy dependency* error that was required
in this case for the hunspell Spanish dictionary **hunspell-es**.

![](/images/Screenshot_2018-07-17_23-51-16.png)

Thus by removing **antergos-common-meta** or whatever was left
of it, resolved the problem, it seems that the Antergos
community haven't been able to resolve some of these issues
that keep coming up every now and then with the
distribution.

A Google search about this problem returned, among the
results some posts like <a
href="https://forum.antergos.com/topic/10303/cant-solve-dependencies-hunspell"
target="_blank">can't solve dependencies hunspell</a> which
summarised the same error message. 

Unlike other occasions, I didn't read about this particular issue this time, The reason for not following up on it is due to the fact that a few days ago a dependency problem had appeared about a `..libso.2` (I can't remember the name of the file, this time around), but it was a file that needed to be removed before successfully continuing with the updates.

Hopefully the Antergos developers will be able to correct some
of these inconsistencies in an otherwise great distribution
that is based on Arch, before a greater share of users who are
fond of Arch, not only migrate to it, but fully adopt it as
the main OS in their systems. 

Until then some of these errors and dependency satisfaction
from the packages would have to be resolved manually by the
end-users on their own.

