---
title: "Pamac Runs Post Install Hooks but Fails to Install New Updates"
date: 2018-07-18T21:31:56-05:00
draft: true
---

The GUI version of **pacman** which runs under Antergos
installed the scheduled updates as expected.

But as soon as new updates were found it just failed to
install them.

In this case, after running the post installation hooks, it
found a new update for one of the programs. But this time
however, it failed to even initialized the transaction. 

Although it could have been relatively simple to circumvent
the problem by seeing through **pacman** itself what the error
was, but just closing the **pamac** application, seemed all
that was needed to have the problem fixed.

Soon after, the GUI version **pamac** had no further issues
to install the updates accordingly.

Perhaps this is is just a reminder not to fully rely on
**pamac** and used the main package manager for any Arch
based distribution.



