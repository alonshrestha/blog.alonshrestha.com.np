---
title: Understanding links on Linux
layout: post
author: alonshrestha
categories:
- Linux
- Ubuntu
- Centos
- Links
- Soft Links
- Hard Links
image: assets/images/blog/2019-10-20/4.png

---

`Links` are assigned to file on Linux which works as `aliases`. There are two types of links on Linux `symbolic links` and `hard links`. In this article, we will learn how to use and manage links on Linux.

> **Table Of Content**

* TOC
{:toc}


> **Requirements**

* Must have basic knowledge about the organization of the `Linux file system`.
 
 
# Hard Links
On Linux, every file has an `inode`, and in the inode, administrative information is stored. Information like :

* Data block where the file content is stored
* Creation, access and modification date
* Permission 
* File owners 

are stored in the inode.  From the above information, one important information is not stored in the inode i.e the `name` of the file. Names are itself stored in the directory, and each filename knows which inode to address for further file information.

Simply understanding `hard links`, giving a name while creating a file, this name is called hard links. On Linux single file can have multiple hard links that enable you to access the file from multiple different locations.

Some of the restrictions applied to hard links are as follows:
* Hard links cannot be created to directories
* If the last name of the multiple aliases of the original file is removed, then the content is also removed.
* All the hard links should be on the same device. 

When you create multiple hard links of a file, there is no difference between the first hard link and the last hard link you have created. If the first hard link that exists is removed, then it does not impact other hard links.

# Symbolic Links
`Symbolic Links` are also known as `soft links`. This is more flexible than hard links. The advantages and disadvantage of symbolic links are:

**Advantages**
* This link directly to the name of the file rather than inode.
* They can link to file as well as directories on other devices.

**Disadvantage**
* When the original file is removed, the symbolic link becomes invalid and does't work any longer.

# Creating Links
For creating links on Linux `ln` command is used. If you want to create a symbolic link, use the `-s` option and then specify your source and target file or directory.

**Example for Symbolic Link**

Creating a soft link in the current directory
{% highlight ruby %}

[alon@localhost Documents]$ ln -s /etc/
[alon@localhost Documents]$ ls -l
total 0
lrwxrwxrwx. 1 alon alon 5 Oct 22 00:20 etc -> /etc/


{% endhighlight %}

Creating soft link in specified directory

{% highlight ruby %}

[alon@localhost Documents]$ ln -s /home/ /tmp/
[alon@localhost tmp]$ ls -l
total 0
lrwxrwxrwx. 1 alon alon  6 Oct 22 00:45 home -> /home/

# soft link to the /home is created on /tmp
{% endhighlight %}


**Example for Hard Link**

{% highlight ruby %}

[root@localhost Data]# ln /etc/hosts .
[root@localhost Data]# ls -l
total 4
-rw-r--r--. 3 root root 158 Jun  7  2013 hosts

{% endhighlight %}

{% include note.html content= " For creating hard links you must be the owner of that file." %}

# Removing Links
Removing links on Linux is a bit risky task to do. You might create an error working program or loses the data. Below shows the example of removing links.

{% highlight ruby %}
#create directory in your home directory

[alon@localhost ~]$ mkdir test

#copy /etc/hosts in test directory

[alon@localhost ~]$ cp /etc/hosts /home/alon/test/

#create soft link of test as link

[alon@localhost ~]$ ln -s test link

#remove link

[alon@localhost ~]$ rm link

{% endhighlight %}

{% include warning.html content= " Do not use -r or -f to remove link. You will lose the data from the original file." %}

{% highlight ruby %}
#creating link again

[alon@localhost ~]$ ln -s test link

#using -rf

[alon@localhost ~]$ rm -rf link/
[alon@localhost ~]$ ls -l
total 0
lrwxrwxrwx. 1 0 0 4 Oct 22 01:08 link -> test
drwxr-xr-x. 2 0 0 6 Oct 22 01:08 test

#you will still see the link exist, but your original directory test will be empty.

[alon@localhost ~]$ ls test/

{% endhighlight %}

{% include summaryCallout.html heading= "Summary" content= "In this articel, you learned how to manage and work with links on Linux. Please feel free to write me if need any help." %}

> **Reference**
>  > Red Hat® RHCSA™/RHCE® 7 Cert Guide: Red Hat Enterprise Linux 7 (EX200 and EX300) Sander van Vugt.