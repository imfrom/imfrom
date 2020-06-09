+++
title = "Antergos Grub Selection"
date = "2018-01-20T08:38:47-05:00"
draft = true
tags = ["antergos", "grub"]
topics = []
description = ""
+++

During the installation of Antergos, there was an option to install the Linux LTS kernel along with the default latest stable version.

Even though it was installed appropriately, the option to select the other kernel, could not be seen from the Grub selection window.

this is even after running the usual `mkinitcpio -p <linux kernel>` that loads the modules and other dependencies accordingly.

It’s good to remember that Grub configuration file though, resides on the /boot/default directory.

With sudo privileges, access the file at /boot/default/grub first.

Therein, and lying at the bottom of the configuration file, one can find the:

     # Uncomment to make GRUB remember the last selection. This requires to
     # set 'GRUB_DEFAULT=saved' above.
     #GRUB_SAVEDEFAULT="true"

One could uncomment the GRUB_SAVEDEFAULT="true" so the grub configuration file ‘remembers’ the selection.

Furthermore, and right on the top of the file the default chosen selection can be specified by modifying the value of 0:

 # GRUB boot loader configuration

 GRUB_DEFAULT=0
To a 2 or 3 for the desired kernel. Which in my case, and if the LTS kernel is to be loaded instead, matched the kernel itself and the fallback for it.

By going this route, it no longer is necessary in specifying during the system startup, the desired kernel that one chooses to be loaded.

Remember after making any changes to grub, to update the configuration file by running:

grub-mkconfig -o /boot/grub/grub.cfg

For more info about this, visit the wiki:

<p><a href="https://wiki.archlinux.org/index.php/GRUB/Tips_and_tricks" target="_blank">GRUB/Tips and tricks</a></p>
