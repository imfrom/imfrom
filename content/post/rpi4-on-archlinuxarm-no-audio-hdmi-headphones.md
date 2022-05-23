---
title: "Rpi4 on Arch Linux Arm No Audio Headphones resolved with snd_bcm2835_enable_headphones=1"
date: 2022-05-22T22:58:21-04:00
draft: true
---

According to the recommendations the block of code should be in one
line:

```
snd_bcm2835.enable_headphones=1
snd_bcm2835.enable_hdmi=1
snd_bcm2835.enable_compat_alsa=0
```

Rpi4 has had trouble for a while now, especially running
under Arch Linux with the sound output from the headphones
jack source. I've usually read a great many threads
dealing with this issue before. Unfortunately, many of the
solutions/recommendations/suggestions haven't resolved the problem.

Other distros have dealt successfully with this issue before. But
whether it has been casued for some given reason or another,
in the case of ArchlinuxArm this has been an outstanding issue
in a great many number of occasions.

The configuration files and particular model and versions for the
rpi4 as it has been outlined on many of the threads, are not quite
that different from mine, and yet the issue was not resolved.

I've read about this:

https://archlinuxarm.org/forum/viewtopic.php?f=65&t=15090&start=0

therein, another specific thread dealing with this issue was opened
which followed over here:

https://archlinuxarm.org/forum/viewtopic.php?f=65&t=15128&p=65808#p65816

This thread [sound on rpi model
4b](https://archlinuxarm.org/forum/viewtopic.php?f=65&t=15070) was
for example, specifically opened to collect more information about
some of the back then outstanding issues with the rpi4 model b.

The above also links to
[Re: fresh rpi4b install with linux-raspberrypi](https://archlinuxarm.org/forum/viewtopic.php?f=65&t=15128&p=65808#p65816)
which as one might guessed by going over it, it deals with
installing another kernel tailored to this particular sound problem.

Some of the posted code may not apply to the particular model, but
as the author clearly specified, many of these settings might differ
considerably from one's setup.

```
arm_64bit=1
enable_gic=1
dtparam=i2c_arm=on
dtoverlay=i2c-rtc,ds3231
dtparam=audio=on
dtoverlay=disable-wifi
dtoverlay=disable-bt
disable_overscan=0
```

From there, another thread entitled [alsa - device not
found](https://archlinuxarm.org/forum/viewtopic.php?f=60&t=15056&p=65576&hilit=alsa#p65576)
was posted

In it, there were some specific packages that must be installed such
as (at the time of writing):

```
alsa-firmware 1.2.4-2
alsa-lib 1.2.4-3
alsa-plugins 1:1.2.2-2
alsa-topology-conf 1.2.4-2
alsa-ucm-conf 1.2.4-2
alsa-utils 1.2.4-2
```

In addition to these, the author also linked
another thread [Re:No usb detected on rpi4 with
aarch64](https://archlinuxarm.org/forum/viewtopic.php?f=65&t=14734&start=50#p65549)
which it also suggested to have the package **mpg123** installed
as well.

```
# dtoverlay=vc4-kms-v3d
dtparam=audio=on
hdmi_force_hotplug=1
over_voltage=6
arm_freq=2000
```

One must always remember that this may have been the settings for that 
particular setup. `dtoverlay=` for example was commented out.

But by now one must realize, that the most widely accepted
configuration has been  so far `dtparam=audio=on`. It has been
brought up for many use cases before.

Of course. All of the above is assuming that another kernel,
that of **linux-raspberrypi4** would be installed to take care
of this issue.

At Reddit for example, this has been also the accepted suggestion.

<a href="https://www.reddit.com/r/archlinuxarm/comments/obxh8i/need_help_with_sound_on_raspberry_pi_4/"
 target="_blank">Need help with sound on rpi4</a>

as one of the users said: _I use the linux-raspberrypi4
 kernel. Installed pulseaudio, ran it and everything worked
 perfectly. Don't remember doing anything else other than selecting
 the correct output device._

Unfortunately, about a year ago or more when I installed arch linux
arm on this particular model, I tried, albeit unsuccessfully to
resolve this issue with this aforementioned kernel
**linux-raspberrypi4**. It didn't work. No sound was ever coming out
of the headphones.

Another user who opened a similar topic outlining the
problematic sound with rpi4 under Arch [rpi4b: no audio device
found](https://archlinuxarm.org/forum/viewtopic.php?f=60&t=14641)
in his case, the culprit seemed to stem from a permission issue
with the file in question. Not in mine. I had also checked file
permissions, but it was not causing the misdetection identifying
the port.

Other posts such as this one for example
at reddit with the title [Rpi4 running armv7
archlinux , audio does not work through the onboard 3.5mm audio
jack](https://www.reddit.com/r/archlinuxarm/comments/ou1ej4/rpi4_running_armv7_archlinux_audio_does_not_work/)
barely provided any insight at all.

Back to archlinuxarm.org there were other threads related with the
underlying issue.

This one simply titled [Re: No
sound](https://archlinuxarm.org/forum/viewtopic.php?f=9&t=12408)
it specified to have

```
dtparam=audio=on
```
and
```
hdmi_drive=2
```

one of the users specified that: *Without hdmi_drive=2 you should
get sound from the jack on the rpi.* , or by commenting it out.
This was also specified before.

Of course. This is not the first time the fellow users over at
archlinuxarm.org have had to deal with it.

In this thread with the title
[Analog Audio not working in rpi4](https://archlinuxarm.org/forum/viewtopic.php?f=60&t=15470)

    I am not getting audio from 3.5 mm audio jack in my raspberry
    pi 4. I have done a clean install of arch. I have installed
    pulseaudio, alsa-utils still iam not getting the audio.


I had also done the same, but to no avail.

the recommendaton for the op was, as in
this reply [Re: analog audio not working in
rpi4](https://archlinuxarm.org/forum/viewtopic.php?f=60&o  i it=15470#p670)


```
dtoverlay=upstream-pi4
```

This didn't work either.

There were also a couple of suggestions or likely solutions to
this issue with the rpi4, archlinuxarm and sound  that ranged from
the aforementioned websites dedicated to the arch linux arm wiki,
as well as in the stackexchange network.

This one from archlinuxarm.org was titled: [Rpi4 No
Sound](https://archlinuxarm.org/forum/viewtopic.php?f=67&t=15352)
in which an error was preventing the user from running a script such
as `amixer -q cset numid=3 1`

This one for example was also dealing the same issue of sound on
te rpi4 and arch linux arm, and
`amixer cset numid` command  to execute

The question on the stackexchange network
with the rpi, was [No Audio Output on 3.5mm
Jack](https://raspberrypi.stackexchange.com/questions/13499/no-audio-output-on-3-5mm-jack)

thes user wrote that

      I have tried turning up the sound in alsamixer as well as
      running modprobe snd_bcm2835. I have also tried to play
      the files with aplay rather than ncmpcpp with no luck.

one of the respondents (who also got the accepted answer for this
sort of problem) said to have

```
amixer cset numid=3 1
```

He was quoted as saying on the answer that

       The last number is the audio output with 1 being the 3.5
       jack, 2 being HDMI and 0 being auto.

one must remember that the latter was, by the looks of it, posted as
an acceptable answer to this particular problem before the
question/answer came up from archlinuxarm.org.

```
modprobe snd_bcm2835
```

as well as `aplay -L` were implemented accordingly by this user in
an effort to figure out what the problem might be with the sound and
the rpi4 model.

https://raspberrypi.stackexchange.com/questions/13499/no-audio-output-on-3-5mm-jack

But more inquiries and suggestions may be further found with
Google about this troublesome behavior. It certainly is one of
the pressing outstanding issues with this awesome distribution
and the model of the rpi4 in question

The **Arch Linux Arm wiki**, (which I'll copy and paste) for
example, states, in regards to the audio:

# Raspberry Pi
 
## Audio

alsa-utils should supply the needed programs to use onboard sound. Default volume can be adjusted using alsamixer.

A key change with Linux kernel version 4.4.x for ARM related to ALSA and to the needed sound module: in order to use tools such as alsamixer with the current kernel, users must modify /boot/config.txt to contain the following line:

```
dtparam=audio=on
```
### Caveats for Audio

To force audio over HDMI, add this to /boot/config.txt:

```
hdmi_drive=2
```
If you experience distortion using the 3.5mm analogue output:

```
audio_pwm_mode=2
```
![wiki](/images/archlinuxarmrpi4wiki.png)


Source: https://archlinuxarm.org/wiki/Raspberry_Pi


What worked in my case were a few lines on the configuration file
that I personally never thought that were going to resolve the sound
issue.

```
snd_bcm2835.enable_headphones=1
snd_bcm2835.enable_hdmi=1
snd_bcm2835.enable_compat_alsa=0
```

![answer-snd-2835](/images/answer-sound-raspberry-pi-forum.png)

Re: Pi4 - No hdmi audio
Tue Jan 21, 2020 9:23 am

     HDMI audio should work in both ports, but there may be some config
     you can do to make it better.
     
     Add this to the end of the line in cmdline.txt file in /boot
     (all must be on the same line)
     
     snd_bcm2835.enable_headphones=1 snd_bcm2835.enable_hdmi=1
     snd_bcm2835.enable_compat_alsa=0


