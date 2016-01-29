---
title: Eliminating Two Windows Boot Options
author: Tim
layout: post
redirect_from: /2005/01/23/eliminating-two-windows-boot-options/
category:  Perplexed
tags:
  - boot options
  - grub
  - linux
  - solutions
  - windows
---
I tried a few different ways of setting up my laptop, and I ended up installing Windows on partition 3 once and then temporarily removing the partitions and installing it on partition 0. After that I resized the partition and installed Linux and Grub as the bootloader. I thought that everthing was straightforward, but I somehow ended up with a boot screen showing both options. So I did a bit of digging and found [this page][1] that talked about the basics of the boot screens. Simply deleting the reference to partition 3 made my Windows boot directly without the need to make a selection after my Grub choice.

 [1]: http://www.softwaretipsandtricks.com/forum/showthread.php?t=11551
