---
title: Wildcards in Linux with Examples
layout: post
author: alonshrestha
categories:
- Linux
- Shell
- Command
- Tech
- tech tips
- wildcards
- important
- text editor
- Linux tips
image: assets/images/blog/2019-11-01/1.png
---

`Wildcards` make your workflow a lot easier when you are working with files. Wildcards are the character that allows you to `search` any class of characters in `shell command` in Linux or other operating systems. This increases your efficiency of search. There are different types of wildcards which are described below.

|Wildcards  | Explanation  |
|---|---|
| * |  Search for ultimate number of characters. |
| ? |  Search for specific character that can be any. |
| [ ] | Search for the range of character that is specified between the square brackets. |


> **Table Of Content**

* TOC
{:toc}



# An Asterisk ( * )
Command used `ls -l /etc/sudo*`
The below examle shows all  the matched files of string appearing after `sudo` from `/etc` directory.

**Example**

{%highlight ruby%}

[alon@localhost ~]$ ls -l /etc/sudo*
-rw-r-----. 1 root root 1786 Oct 30  2018 /etc/sudo.conf
-r--r-----. 1 root root 4328 Oct 30  2018 /etc/sudoers
-rw-r-----. 1 root root 3181 Oct 30  2018 /etc/sudo-ldap.conf

{%endhighlight%}

# Question Mark ( ? )
Command used `ls /etc/rc?.d`
The below example show all the matched files beginning  wiht the string `rc` followed by any single character and end with `.d`.

**Example for Single Character**

{%highlight ruby%}

[alon@localhost ~]$ ls /etc/rc?.d
/etc/rc0.d:
K50netconsole  K90network

/etc/rc1.d:
K50netconsole  K90network

/etc/rc2.d:
K50netconsole  S10network

/etc/rc3.d:
K50netconsole  S10network

/etc/rc4.d:
K50netconsole  S10network

/etc/rc5.d:
K50netconsole  S10network

/etc/rc6.d:
K50netconsole  K90network

{%endhighlight%}


**Example for Multiple Character**

Command used `ls /etc/r??.d`. 
The below example show all the matched files beginning  wiht the string `r` followed by any double character and end with `.d`. 

{%highlight ruby%}
[alon@localhost ~]$ ls /etc/r??.d
/etc/rc0.d:
K50netconsole  K90network

/etc/rc1.d:
K50netconsole  K90network

/etc/rc2.d:
K50netconsole  S10network

/etc/rc3.d:
K50netconsole  S10network

/etc/rc4.d:
K50netconsole  S10network

/etc/rc5.d:
K50netconsole  S10network

/etc/rc6.d:
K50netconsole  K90network

{%endhighlight%}
# Bracket ( [ ] )
Command used  `ls- l /etc/[w-y]*`
The below example shows all the matched files starting with the range of `w-y`.

{%highlight ruby%}

[alon@localhost var]$ ls- l /etc/[w-y]*
-rw-r--r--. 1 root root 4479 May 16 02:46 /etc/wgetrc
-rw-r--r--. 1 root root  970 Nov  5  2018 /etc/yum.conf

/etc/wpa_supplicant:
total 4
-rw-------. 1 root root 67 Oct 31  2018 wpa_supplicant.conf

/etc/X11:
total 0
drwxr-xr-x. 2 root root  6 Apr 11  2018 applnk
drwxr-xr-x. 2 root root  6 Apr 11  2018 fontpath.d
drwxr-xr-x. 2 root root 29 Jul 31 14:00 xorg.conf.d

/etc/xdg:
total 0
drwxr-xr-x. 2 root root  6 Apr 11  2018 autostart
drwxr-xr-x. 2 root root 17 Aug 13 09:49 systemd

/etc/xinetd.d:
total 0

/etc/yum:
total 12
drwxr-xr-x. 2 root root    6 Nov  5  2018 fssnap.d
drwxr-xr-x. 2 root root   52 Nov  5  2018 pluginconf.d
drwxr-xr-x. 2 root root   25 Aug 13 09:49 protected.d
drwxr-xr-x. 2 root root   35 Jul 11 09:06 vars
-rw-r--r--. 1 root root  444 Nov  5  2018 version-groups.conf
-rw-r--r--. 1 root root 2603 Aug  8 17:42 yum-cron.conf
-rw-r--r--. 1 root root 2565 Aug  8 17:42 yum-cron-hourly.conf

/etc/yum.repos.d:
total 96

{%endhighlight%}

{% include summaryCallout.html heading= "Summary" content= "In this article, you learned about the wildcards and its use on Linux. Please feel free to write me if need any help." %}