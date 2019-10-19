---
title: Working With Compession And Archive Files In Linux
layout: post
author: alonshrestha
categories:
- Linux
- Compression
- Archive
---

Managing and working with file compression and archive is the most important file-related task in Linux. tar command is known as Tape ARchive which is used to create an archive of files in Linux. This command creates an archive without compression. For creating an archive file with compression, you need to use specific compression tools or need to specify an option that compresses the archive while it is created. In this article, we will learn how to manage and work with archives and compressed files. 

# Create Archive
To create an archive we use `tar -cf  Archive-file-name.tar  /file-you-want-to-archive`.  In below example an archive is created with the name `myFiles.tar` for directory  `/home/alon/Documents/`.

**Example:** 

{% highlight ruby %}

[alon@localhost ~]$ tar -cf myFiles.tar /home/alon/Documents/

{% endhighlight %}

if you want to see what is happening while running above command, use `-v` option.

{% highlight ruby %}

[alon@localhost ~]$ tar -cvf myFiles.tar /home/alon/Documents/
/home/alon/Documents/
/home/alon/Documents/passwd
/home/alon/Documents/newfile
/home/alon/Documents/oktest.tar
/home/alon/Documents/oktest.tar.bz2
/home/alon/Documents/linkedfile

{% endhighlight %}

{% include note.html content= " In -cvf option ( - ) was not being used in old version of tar." %}

# Add File in Existing Archive
While managing archives with tar,  there might be also a case to add a new file in the existing archive. For that, we use `-r` options. Syntax `tar -rvf  Archive-file-name.tar  /path-of/file-you-want-to-add-to-the-archive`. 

**Example:**

{% highlight ruby %}

[alon@localhost ~]$ tar -rvf myFiles.tar /etc/hosts
/etc/hosts

{% endhighlight %}

# Update Existing Archive

To update current existing archive file, we can use the `-u` options. Syntax `tar -uvf  Archive-file-name.tar `

**Example:**


{% highlight ruby %}

[alon@localhost ~]$ tar -uvf myFiles.tar

{% endhighlight %}

# Monitoring Archive

You can also view all the files for the archive before extracting. For that, use `-t` option. Sytntax `tar -tvf  Archive-file-name.tar `.

**Example**

{% highlight ruby %}

[alon@localhost ~]$ tar -tvf myFiles.tar
drwxr-xr-x alon/alon         0 2019-10-19 15:28 home/alon/Documents/
-rw-r--r-- alon/alon      2268 2019-10-19 15:27 home/alon/Documents/passwd
-rw-rw-r-- alon/alon         0 2019-10-19 15:27 home/alon/Documents/newfile
-rw-rw-r-- alon/alon    235520 2019-10-19 15:27 home/alon/Documents/oktest.tar
-rw-rw-r-- alon/alon     27291 2019-10-19 15:27 home/alon/Documents/oktest.tar.bz2
-rw-rw-r-- alon/alon         0 2019-10-19 15:27 home/alon/Documents/linkedfile
-rw-r--r-- alon/alon         0 2019-10-19 15:28 home/alon/Documents/hosts
-rw-r--r-- root/root         0 2019-10-05 21:29 etc/hosts

{% endhighlight %}

{% include tip.html content= "It's good practice to monitor your archive before extracting it." %}

# Extracting Archive
Now its time to extract the content of the archive. For that, use `-x` option. Syntax `tar -xvf Archive-file-name.tar`

**Example:**

{% highlight ruby %}

[alon@localhost ~]$ tar -xvf myFiles.tar
home/alon/Documents/
home/alon/Documents/passwd
home/alon/Documents/newfile
home/alon/Documents/oktest.tar
home/alon/Documents/oktest.tar.bz2
home/alon/Documents/linkedfile
home/alon/Documents/hosts
etc/hosts


{% endhighlight %}

The above command extract the content  of archive in the current directory. To specify your target directory where you want to extract the files. For that, use  `-C` option. Syntax `tar -xvf Archive-file-name.tar -C /your-path`

**Example:**

{% highlight ruby %}

[alon@localhost ~]$ tar -xvf myFiles.tar -C /tmp/
home/alon/Documents/
home/alon/Documents/passwd
home/alon/Documents/newfile
home/alon/Documents/oktest.tar
home/alon/Documents/oktest.tar.bz2
home/alon/Documents/linkedfile
home/alon/Documents/hosts
etc/hosts


{% endhighlight %}

|Options  |Use  |
|---|---|---|---|---|
| c  | Creates an archive. |
| v  | Shows verbose output while tar is working |
| f  |   Used to specify the name of the tar archive that is to be used. Without using this option, the default destination is STDIN for  -x  and STDOUT for  -c .     |
|   t  | Shows the contents of an archive |
|   z  | Compresses/decompresses the archive while creating it, by using gzip |
|   j  | Compresses/decompresses the archive by using bzip2 |
|   x  | Extracts an archive. |
|   u  | Updates an archive; only newer files will be written to the archive |
|   C  |  Changes the working directory before performing the command.  |
|   r  |  Appends files to an archive. |