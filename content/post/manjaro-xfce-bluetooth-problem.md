+++
title = "Manjaro Xfce Bluetooth Problem"
date = "2017-09-29T13:32:01-05:00"
draft = true
tags = []
topics = []
description = ""
+++
 <p>Bluetooth recognition - at least on Manjaro Xfce - has been erratic and inconsistent.</p>

<p>For no clear reason the LTS kernel and even a newer kernel have identified the hardware, while it has failed to do so in a great many occasions.</p>

<p>Many of the tweaks included reinstalling <code>bluez</code>, <code>bluez-firmware</code>, <code>bluez-libs</code>, <code>bluez-tools</code>, and <code>bluez-utils</code>.</p>

<p>Back to the drawing room and back again.</p>

<p>The bluetooth adapters were not being recognized however. And after logging out and back into the session, and even after <code>sudo /sbin/shutdown -r now</code>, nothing seemed to work.</p>

<p>The following day - to my surprise - I booted the system and it picked the bluetooth adapters without a problem.</p>

<p>It reminded me of a comment on the manjaro forum thread entitled <a href="https://forum.manjaro.org/t/bluetooth-adapters-app-not-opening-bluetooth-manager-bluez-failed/4367/19" target="_blank">Bluetooth adapters app not opening Bluetooth Manager</a> in which one of the participants said:</p>

<blockquote>
<p>Bluetooth support in Linux is always troublesome, even in Windows, smartphone, etc. So yeah, I think staying away from bluetooth related hardwares if you want a trouble free experience. Wireless hardwares nowadays are going towards a dedicated receiver way to handle wireless connection and that’s a better approach. Just my two cents <a href="https://imfrom.github.io/post/manjaro-xfce-bluetooth-problem/#blueref"><sup id="blueref">1</sup></a></p>
</blockquote>

<p>I have to agree with him on that regard.</p>

<p>On the other hand, the desktop environment <strong>KDE</strong> hasn’t - I ran it for a short while and perhaps my feedback is worthless of consideration on that regard - given me the same problems than the current configuration under <strong>xfce</strong>.</p>

<p>But I never thought that the problems would persist even after the installation of a newer kernel. That is perhaps the main reason which has been drifting me away from <strong>xfce</strong> until further notice.</p>

<p>And while <strong>KDE</strong>-fanboys have come up with the slogan that <em>it grows on you</em>, <strong>xfce</strong> is perhaps a more GNU/Linux-centric configurable environment than the former. I still enjoy tweaking with its features even though its less polished than Plasma <strong>KDE</strong>. There is no question about this. <strong>KDE</strong> aims at the latest hardware, while <strong>xfce</strong> focuses on the rest. I’ve never tried to benchmark its memory and CPU consumption, but I’m almost certain it fairs much better than <strong>KDE</strong>.</p>

<p>Whether <strong>xfce</strong> will be a daily desktop environment driver running the main programs on which my workflow depends upon, it’s a question of time and how well it will handle them without a major setback.</p>

Further oversights around Bluetooth vulnerabilities include technical papers such as <a href="http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.258.7253&rep=rep1&type=pdf" target="_blank">Security Risks in Bluetooth Devices</a>, <a href="https://pdfs.semanticscholar.org/8872/521819c79505ac20e5da8dd14f8c41eb3f07.pdf" target="_blank">Bluetooth security threats and solutions</a>

Even recent articles from <a
href="https://mobile.slashdot.org/story/17/09/12/2030213/blueborne-vulnerabilities-impact-over-5-billion-bluetooth-enabled-devices"
target="_blank">Slashdot - BlueBorne Vulnerabilities Impact Over 5 Billion
Bluetooth-Enabled Devices</a> have gone on at length about it. The following
paper - although unreliable since it looks more than a pamphlet from a company
that advertises its products under the pretension of providing unparalleled
protection - serves to confirm that regardless of its merit [this paper itsel]
is worth considering the possible risks could arise as a result from the
operations of bluetooth devices.

<p><strong>References</strong></p>

<p><a href="https://forum.manjaro.org/t/bluetooth-adapters-app-not-opening-bluetooth-manager-bluez-failed/4367/19" target="_blank">bluetooth adapters not opening bluetooth-manager-bluez-failed</a><a href="#blueref">_↩︎</a></p>
