---
layout: 
title: "Pacman Unable to Lock Database"
date: 2019-09-15T23:35:41-04:00
draft: true
---

On a recent pacman upgrade, I encountered the error:

```
:: Synchronizing package databases...
error: failed to update core (unable to lock database)
error: failed to update extra (unable to lock database)
error: failed to update community (unable to lock database)
error: failed to synchronize all databases
```

the solution everytime is to remove the `db.lck` from the `/var/lib/` directory and restart pacman.

```
rm /var/lib/db.lck
pacman -Syyu
```

