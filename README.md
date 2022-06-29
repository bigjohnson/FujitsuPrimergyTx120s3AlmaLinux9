# FujitsuPrimergyTx120s3AlmaLinux9
Note on Alma Linux 9 installation on **Fujitsu Primergy TX120 S3** server.

## Graphics card

The video card resolution is not detectable by installer linux kernel, during installation, and installed linux kernel, at the installation end.

You need add

`vga=791`

at the end of installer kernel parameters, you can edit it pressing tab key at the bootloader installer menu.

After installation you cannot use the video, you must have ssh access to the server an as root add the

`vga=791`

in file

`/etc/default/grub`

on the

`GRUB_CMDLINE_LINUX="vga=791"`

parameter end, and reinstall bootloader

`grub2-mkconfig -o $(sudo readlink -f /etc/grub2.cfg)`

## ServerView Raid Manager

Download the ServerView_RAID installer for Red Hat 8 el8.x86_64 

**ServerView RAID Manager installation package for Linux Red Hat EL8**

from

https://support.ts.fujitsu.com/prim_supportcd/SVSSoftware/html/ServerViewRaid_e.html

if you find the EL9 version you can try it, actually there is only EL8

install the init scripts

`dnf install initscripts`

install the pciutils

`dnf install pciutils`

then you can install the ServerView Raid Manager

`rpm -Uvh ServerView_RAID-7.9-1.el8.x86_64.rpm`

reboot, then you can access the Raid Manager from localhost at the url

https://127.0.0.1:3173/svraid

you can forward the port in ssh and connect it from remote client.
