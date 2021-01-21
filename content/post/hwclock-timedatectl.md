---
title: "Hwclock Timedatectl"
date: 2020-06-08T04:08:04-04:00
draft: true
---

Setting the time and date by invoking `hwclock --systohc` or by `hwclock --hctosys` should always be followed by `localtime` rather than say by `--utc` wich is the Universal Corrdinated Time.

On the other hand, if multiple systems are to be used, it may be useful to better have the hardware clock synchronized in UTC in case that time zone and DST Daylight Savings Time come into effect.

Omitting appending something as simple as `--localtime` would certainly display the UTC on multiple systems under any hardware.

In case of any trouble setting it up afterwards may resolve the issue

```
timedatectl set-timezone 
```
Alternatively, one may invoke:

```
hwclock --set --date 'mm/dd/yyyy 00:00:00'
hwclock --hctosys --localtime
```



