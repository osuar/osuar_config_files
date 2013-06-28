
## General tips

In general, keep a working snapshot (or ten) of the system around in the form
of a disk image. You never know. It would be good to automate this to take
periodic backups.


## The ODROID won't boot kernel v3.8!

The new kernel (as opposed to v3.6) requires a new bootloader, as described by
mdrjr here: http://forum.odroid.com/viewtopic.php?f=23&t=1213. Follow his link
for instructions on how to install the new bootloader.


## Curl error

If this happens:

	curl error: Peer certificate cannot be authenticated with given CA certificates

Set your date correctly (i.e., not Jan 1, 2000) manually using date or
automatically using ntpdate.


## I'm trying to create an image of the SD card using dd, but it's huge!

One way in which to decrease the size of the image you create is by squeezing
the partitions down to a minimum size (e.g., using gparted) and doing something
like this:

	dd if=/dev/sdd of=sd.img bs=1024 count=$[3766*1024]

This will take an SD card at /dev/sdd and create an image file named sd.img in
the current directory with a block size of 1 MB and a total size of 3.68 GB
(3766\*1024\*1024 bytes = 3.68 GB, see?).

<!--
vim: ft=markdown
-->

