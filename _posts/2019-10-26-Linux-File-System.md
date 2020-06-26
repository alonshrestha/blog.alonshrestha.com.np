---
title: "Linux File System Hierarchy"
layout: post
author: alonshrestha
categories:
- Linux
- Ubuntu
- CentOS
- Files
- System
- Hierarchy
- Types
image: assets/images/blog/2019-10-26/1.png
featured: true
---

All the files on the [Linux](https://stechalon.com/category/linux){:target= "_blank"} are organized into a single inverted tree directory which is also known as [file system hierarchy](https://stechalon.com/linux-file-system-explained/){:target= "_blank"}. The file system handles your data on the storage, which allows the system to know and use it at the beginning and end of the operation. By default, Linux has organized directories which is similar to almost all Linux file system. In this article, we will know about different types of Linux file systems and the Linux file system hierarchy.

> **Table Of Content**

* TOC
{:toc}



# Linux File System Types

Linux provides different types of file system formats for partitioning the disk which is listed below. Each has its own merits of the use.

|File System  | Explanation  |
|---|---|
| **Ext:** |  A basic file system having lot of limitation and no longer in use. |
| **Ext2:** |  Upgrade version of Ext which allows 2 TB of data and not in use anymore.  |
| **Ext3:** |  Upgrade of Ext2. Does not support file recovery and disk snapshots. |
| **Ext4:** | Upgrade of Ext3. Allows large file of data upto 16TB with significant speed. |
| **XFS** |  Default file system in RHEL 7. Allows data upto 500 TB |
| **BtrFS** | New file system not yet supported but will be include in later updates.|
| **NTFS** |  Not Supported on RHEL |
| **VFAT** |  Equivalent to the FAT32. Useful to use on USB thumb drive. |




# Linux File System Hierarchy

In the [Linux file system hierarchy](https://stechalon.com/linux-file-system-explained/#1-linux-file-system-hierarchy){:target= "_blank"}, the root of the tree is said to be on the top of the hierarchy,  and the branches of directories and subdirectories  as shown in the below image. 



![](/assets/images/blog/2019-10-26/img1.png)

You can try in your machine `ls -l /` to see this directories as shown below.

{% highlight ruby %}

[alon@localhost ~]$ ls -l /
total 36
lrwxrwxrwx.   1 root root    7 Jul 11 09:02 bin -> usr/bin
dr-xr-xr-x.   5 root root 4096 Sep 12 15:22 boot
drwxr-xr-x.   3 root root 4096 Jul 11 08:51 data
drwxr-xr-x.  19 root root 3120 Sep 25 17:14 dev
drwxr-xr-x.  82 root root 8192 Sep 25 17:14 etc
drwxr-xr-x.   3 root root   17 Apr 11  2018 home
lrwxrwxrwx.   1 root root    7 Jul 11 09:02 lib -> usr/lib
lrwxrwxrwx.   1 root root    9 Jul 11 09:02 lib64 -> usr/lib64
drwxr-xr-x.   2 root root    6 Apr 11  2018 media
drwxr-xr-x.   2 root root    6 Apr 11  2018 mnt
drwxr-xr-x.   5 root root   76 Sep 23 14:36 opt
dr-xr-xr-x. 115 root root    0 Sep 25 17:14 proc
dr-xr-x---.   7 root root 4096 Sep 23 15:24 root
drwxr-xr-x.  26 root root  740 Oct 29 18:06 run
lrwxrwxrwx.   1 root root    8 Jul 11 09:02 sbin -> usr/sbin
drwxr-xr-x.   2 root root    6 Apr 11  2018 srv
dr-xr-xr-x.  13 root root    0 Sep 25 17:14 sys
drwxrwxrwt.   9 root root 4096 Oct 29 04:50 tmp
drwxr-xr-x.  13 root root 4096 Jul 11 09:03 usr
drwxr-xr-x.  21 root root 4096 Jul 22 14:05 var

{% endhighlight %}

Form the above sketch you can see `->` symbol pointing multiple directories in  `/usr/` directory.  This indicates that the directories  `bin` , `lib` , `lib64` and `sbin` are the [symbolic links](https://blog.alonshrestha.com.np/Understanding-Hard-and-Soft-Links-In-Linux/){: target="_blank"} from `/usr/`.

Table below describes the directories

|Directory  | Explanation  |
|---|---|
| **/** |  Know as `root` directory where file system tree starts. |
| **/bin** |  Contains `binaries files` of the application or program that can be run. Essential during boot. |
| **/boot** | Contains all the files and directories that are need to `boot` the Linux kernel. |
| **/dev** | Contains device files that allows to access `physical devices`. Many of these file are generated at boot time. Essential during boot. |
| **/etc** | Know as `every thing to configure`. Contains the configuration files that are used by the application and services. |
| **/home** | This drectory is used for local user `home directory`.|
| **/lib, /lib64** |  Contains the shared libraries that are used by the application in `/boot`  `/sbin` and `bin`   |
| **/media** |  Contains the files of the `external storage`. |
| **/mnt** |  Contains files that allows for `mounting` the devices. |
| **/opt** |  This is used to install `optional package` not from the Linux distribution repositories .|
| **/sbin** |  Similar to `/bin`. Contains all the binaries that superuser needs. |
| **/srv** |  Directory that may be used for data by services like `HTTP`, `NFS` and `TCP`. |
| **/run** |  System application use this directory for storing temporary file for their own need. |
| **/tmp** |  This directory contains `temporary files` which gets `deleted` while system boot without waring. |
| **/usr** | Contains subdirectories including programs, libraries, documentation etc. for all user-related programs. This is not needed for boot. |
| **/var** |  Contains `system log` files which size changes dynamically. |
| **/root** |  Home directory of `root user`. |
| **/proc** |  Contains files that give information about `kernel and CPU`.  |
| **/sys** | Similar to `/proc` that contains information about the connected devices from your computer.   |
| **/lost+found** | Files that are saved during `system failures`.  |

{% include summaryCallout.html heading= "Summary" content= "In this article, you learned the concept of Linux file system types and hierarchy. Please feel free to write me if need any help." %}