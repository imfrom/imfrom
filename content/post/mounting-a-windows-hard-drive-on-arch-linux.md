+++
title = "Mounting a Windows Hard Drive on Arch Linux"
date = "2017-11-24T13:40:27-05:00"
draft = true
tags = []
topics = []
description = ""
+++

<p>After following some of the advice on <a href="https://wiki.archlinux.org/index.php/NTFS-3G">ntfs-3g arch linux</a> entry which described the procedure to mount a windows system:</p>

<p>A <code>lsblk -f</code> call on the filesystem returned:</p>

<pre><code> sdb                                                         
 ├─sdb1 vfat   SYSTEM   
 ├─sdb2 ntfs   Recovery 
 ├─sdb3                 
 ├─sdb4 ntfs   OS       
 └─sdb5 ntfs   Restore  
</code></pre>

<p>I was after <strong>sdb4</strong> in this case. So I invoked on the command line:</p>

<pre><code> $ ntfs-3g /dev/sdb4 /mnt/fat/
</code></pre>

<p>Which returned the message:</p>

<pre><code> Unprivileged user can not mount NTFS block devices using the external FUSE
 library. Either mount the volume as root, or rebuild NTFS-3G with integrated
 FUSE support and make it setuid root. Please see more information at
 http://tuxera.com/community/ntfs-3g-faq/#unprivileged
</code></pre>

<p>So with sudo privileges I invoked it again, but this time around the more precise error message that <em>Input/output error NTFS is inconsistent</em> was returned on the terminal. The entire message was as follows:</p>

<pre><code> ntfs_attr_pread_i: ntfs_pread failed: Input/output error
 Failed to read of MFT, mft=391080 count=1 br=-1: Input/output error
 Falling back to read-only mount because the NTFS partition is in an
 unsafe state. Please resume and shutdown Windows fully (no hibernation
 or fast restarting.)
 ntfs_attr_pread_i: ntfs_pread failed: Input/output error
 Failed to read NTFS $Bitmap: Input/output error
 NTFS is either inconsistent, or there is a hardware fault, or it's a
 SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
 then reboot into Windows twice. The usage of the /f parameter is very
 important! If the device is a SoftRAID/FakeRAID then first activate
 it
</code></pre>

<p>If I were to invoke it with <code>mount</code> instead of <code>ntfs-3g</code>, then it would have mounted it without a setback</p>

<pre><code> $ sudo mount -t ntfs-3g /dev/sdb4 /mnt/fat
</code></pre>

<p>successfully mounted it and I was able to access the files on that hard drive.</p>
