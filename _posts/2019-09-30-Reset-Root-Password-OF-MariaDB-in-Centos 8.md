---
title: Reset MariaDB Root Password on CentOS 8
layout: post
author: alonshrestha
categories:
- Linux
- CentOS 8
- Mariadb
- mysql
- password
- reset
- tech
- tech tips
- Linux tips
image: assets/images/blog/2019-09-30/1.png
featured: true
---

[MariaDB](https://mariadb.org/){:target="_blank"} root user has full privileges to access every data in the databases. Being human, users sometimes make mistakes or forget the root password. In this article, you will learn how to reset the root password of MariaDB on [centOS 8](https://www.centos.org/){:target="blank"}.

{% include note.html content= "You must have root access on the server to reset mariadb root password." %}

> **Table Of Content**

* TOC
{:toc}

# Stop MariaDB Server
First you need to down your mariaDB server. For that use the command `sudo systemctl stop mariadb`.  

{%highlight ruby%}

[alon@localhost ~]$ sudo systemctl stop mariadb

{%endhighlight%}

# Start MariaDB Server with Safe Mode
Start mariadb server with safe mode using `mysqld_safe`. For that use the command `sudo mysqld_safe --skip-grant-tables &`.

{%highlight ruby%}
[alon@localhost ~]$ sudo mysqld_safe --skip-grant-tables &
{%endhighlight%}

After entering the above command, if you got `hang` as shown below, press `enter`.  This will redirect you again to command line.

{%highlight ruby%}

[root@localhost alon]# mysqld_safe --skip-grant-tables &
[1] 1892
[root@localhost alon]# 191116 17:21:13 mysqld_safe Logging to '/var/log/mariadb/mariadb.log'.
191116 17:21:13 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

{%endhighlight%}

{% include tip.html content= "Using --skip-grant-tables  runs the server without grants, which allows you to enter into the server without password and it is possible for user from other networks to connect to the server. " %}
# Login to MariaDB Server as Root
Now, you will be able  to login in mariaDB as `root` user. For that use the command `mysql -u root`.

{%highlight ruby%}

[alon@localhost ~]$ mysql -u root

{%endhighlight%}

You will be login to the mariadb server.  

{%highlight ruby%}

[alon@localhost ~]$ mysql -u root
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 2
Server version: 5.5.60-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>

{%endhighlight%}

# Change MariaDB Root Password
First change the database. For that use the command `use mysql;`.

{%highlight ruby%}
MariaDB [(none)]> use mysql;
{%endhighlight%}

After using the `mysql` database, update the password of root user. For that use the command `update user SET PASSWORD=PASSWORD("yourNewStrongPassword") WHERE USER='root';`.
{%highlight ruby%}
MariaDB [mysql]> update user SET PASSWORD=PASSWORD("yourNewStrongPassword") WHERE USER='root';
{%endhighlight%}
Flush Privileges using command `flush privileges;`
{%highlight ruby%}
MariaDB [mysql]> flush privileges;
{%endhighlight%}
Exit from mariadb.
{%highlight ruby%}
MariaDB [mysql]> exit
Bye
{%endhighlight%}

# Kill mysql and mysqld_safe processor
Find the pid value of `mysql` and `mysqld_safe` processor using command `ps aux | grep mysqld_safe` and `ps aux | grep mysql`.

{%highlight ruby%}
[alon@localhost ~]$ ps aux | grep mysqld_safe

root      1892  0.0  0.0 113312  1652 pts/0    S    17:21   0:00 /bin/sh /bin/mysqld_safe --skip-grant-tables
root      2062  0.0  0.2 239088  4160 pts/0    T    17:28   0:00 sudo mysqld_safe --skip-grant-tables
alon      2288  0.0  0.0 112708   988 pts/0    R+   17:56   0:00 grep --color=auto mysqld_safe
{%endhighlight%}

Now kill the processor using command `kill -9`

{%highlight ruby%}
[alon@localhost ~]$ sudo kill -9 1892

[alon@localhost ~]$ sudo kill -9 2062
[1]+  Killed                  sudo mysqld_safe --skip-grant-tables

{%endhighlight%}

# Restart MariaDB
Use the command `sudo systemctl stop mariadb` and `sudo systemctl stop mariadb`

{%highlight ruby%}
[alon@localhost ~]$ sudo systemctl stop mariadb
{%endhighlight%}
{%highlight ruby%}
[alon@localhost ~]$ sudo systemctl start mariadb
{%endhighlight%}

# Login to MariaDB 
Use Command `mysql -u root -p`.
{%highlight ruby%}
[alon@localhost ~]$ mysql -u root -p

Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 8
Server version: 5.5.60-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> exit
Bye

{%endhighlight%}


{% include summaryCallout.html heading= "Summary" content= "In this article, you learned how to reset MariaDB root password on centOS 8. Please feel free to write me if you need any help." %}