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


Alternatively, if there's any problem with the above, the
https://wiki.archlinux.org/title/System_time#Troubleshooting

## Troubleshooting

Clock shows a value that is neither UTC nor local time

This might be caused by a number of reasons. For example, if your hardware clock is running on local time, but timedatectl is set to assume it is in UTC, the result would be that your timezone's offset to UTC effectively gets applied twice, resulting in wrong values for your local time and UTC.

To force your clock to the correct time, and to also write the correct UTC to your hardware clock, follow these steps:

* Setup ntpd (enabling it as a service is not necessary).

* Set your time zone correctly.

* Run ntpd -qg to manually synchronize your clock with the network, ignoring large deviations between local UTC and network UTC.

* Run hwclock --systohc to write the current software UTC time to the hardware clock.
