+++
title = "Manjaro Kde Plasma Dolphin Mtp Cant Open File"
date = "2017-12-16T13:26:25-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p><strong>MTP</strong> implementation runs on most desktop environments without a problem. Except on KDE where it has had several problems in identifying and initializing a simple file from any of the devices that have been connected to the system, mainly through the USB port.</p>

<p>It’s really a shame that although Plasma KDE fairly supports Bluetooth protocol better than the rest of other desktop environments, it largely fails with both gwenview and its default Dolphin manager to open up files directly.</p>

<p>I have tried in a great many occasions to slither out many of these KDE errors by falsely attributing it to my lack of knowledge on its usage. But I can’t deny any longer that the system either works or it doesn’t. And one should no longer have to wait who-knows-how-long-and-when, before updates smother out its deficiencies.</p>

Yes, I have tried to look up for the issue elsewhere such as as in <a href="https://bbs.archlinux.org/viewtopic.php?id=177028" target="_blank">mtp mount issues in KDE/Dolphin</a>, but many of the suggestions have not worked so far. 

<p>Whereas with KDE, to my amazement - because at this point of its developmental phase, one would think that it should perform better and not worse - the problems all range from mild to critical, while <strong>xfce</strong> on the other hand, these unexpected malfunctions and sudden out-of-the-blue crashes do occur but at a lesser degree, and when one of these errors undermines the stability, the errors do not necessarily affect the overall functionality.</p>

<p>I experienced and spoke at somewhat length about a <a href="https://imfrom.github.io/post/manjaro-kde-plasma-error-unknown-application-folder/">manjaro kde error unknown application</a> post.</p>

<p>In the wake of recent Bluetooth vulnerabilities that have happened,<a href="#blue"><sup id="blueref">1</sup></a>  and the history behind it in which several authors have researched the issue,<a href="#tech"><sup id="techref">2</sup></a> it makes no sense to have a whole interface that handles this protocol better than most environments and yet fails when the to-be-expected approach to handle it differently or by using the right terminology, handling it without bluetooth at all in light of everything that has happened with it, by going directly through the use of the mtp protocol that is supposed to take care of it. Notice that mtp is supported without a major flaw in <strong>xfce</strong>, <strong>Gnome</strong>, and others.</p>

<p>For further reading about <strong>MTP</strong>, is advisable to visit the formidable wiki from Arch Linux at <a href="https://wiki.archlinux.org/index.php/MTP" target="_blank">MTP</a></p>

<p>It turns out that kio-extras is a dependency of Kde’s dolphin file manager, which apparently is partly responsible for the <code>failed to initlialize</code> error, but whichever is to be blamed in this regard, matters for as long as the user finds the KDE environment worthy to be used. In my case perhaps, the same opinion that for so long I’ve had of the software, has notably changed amid these recent problems: first with the <a href="https://imfrom.github.io/post/manjaro-kde-plasma-error-unknown-application-folder/">manjaro kde error unknown application instance as highlighted earlier</a>, and now with the bluetooth problem.</p>

<p>Perhaps is worthy to revisit this desktop environment, but for now, it is in my opinion that there are better options out there from which to choose from, before having to put up with the inconsistencies and failures that have rendered the systems I have been running lately, useless in more than one occasion.</p>

<p><strong>References</strong></p>

<p><a href="https://mobile.slashdot.org/story/17/09/12/2030213/blueborne-vulnerabilities-impact-over-5-billion-bluetooth-enabled-devices" target="_blank">Blueborne vulnerabilities impact devices</a><a name="blue"></a><a href="#blueref">_↩︎</a></p>


<p> Technical papers that include Bluetooth vulnerabilities are as follow <a href="http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.258.7253&rep=rep1&type=pdf" target="_blank">Security Risks in Bluetooth Devices</a>, and <a href="https://pdfs.semanticscholar.org/8872/521819c79505ac20e5da8dd14f8c41eb3f07.pdf" target="_blank">Bluetooth security threats and solutions</a><a name="tech"></a><a href="#techref"> &#8617;</a></p>

