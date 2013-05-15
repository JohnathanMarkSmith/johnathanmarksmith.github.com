---
layout: post
title: "Replacing MySQL with MariaDB on CentOS 6"
description: "Replacing MySQL with MariaDB on CentOS 6"
categories: [ Linux, MySQL, MariaDB ]
tags: [ Linux, MySQL, MariaDB ]
comments: false
---

Replacing MySQL with MariaDB on CentOS 6

MariaDB is a high performance drop-in replacement for MySQL, developed by some of the original authors of the MySQL project. This will walk you through uninstalling MySQL and then installing MariaDB from their repository using the YUM package manager.

### WARNING: YOU SHOULD ALWAYS MAKE A BACKUP OF ANY DATABASES BEFORE REMOVE MYSQL!!!

AND AGAIN..... WARNING: YOU SHOULD ALWAYS MAKE A BACKUP OF ANY DATABASES BEFORE REMOVE MYSQL!!!

### Stop MySQL

If you have MySQL installed and running its time to stop it by entering the following command:

    [root@regan ~]# service mysqld stop


### Removing MySQL

Now its time to kiss MySQL goodbye by using the following command:

    [root@regan ~]# yum remove mysql*

(The * is a wildcard, and tells YUM to remove all packages starting with the string "mysql".)



Now let's add MariaDBs repository. Create the file /etc/yum.repos.d/MariaDB.repo by opening it in your favorite editor. 
We will use vi here, but nano might be easier if you are new to Linux (yum install nano, then nano -w filepath).

    [root@regan ~]# vi /etc/yum.repos.d/MariaDB.repo

Within the file we insert the following:

    [mariadb]
    name = MariaDB
    baseurl = http://yum.mariadb.org/5.5/centos6-x86
    gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
    gpgcheck=1

You should note that the last part of the baseurl needs to match your CentOS version and arch. In my case this would need to be centos6-amd64, for a 64-bit install, but since x86 (32-bit) is more common I've left that in the example above.

Save the file and exit your editor. (In vi this is done by holding Shif and pressing : (colon), entering "wq" (without the quotes) for "write quit", and enter.) 

### Time to install MariaDB

To install the components using YUM use the following command:

    [root@regan ~]# yum install MariaDB-server MariaDB-client

### That Was Easy

Now that it is installed, let's start the MariaDB service:

    [root@regan ~]# service mysql start


You can see that the service is "mysql" NOT "mysqld" now.


### Time to Loadin and Seee

Let's try to connect, shall we?

    [root@regan ~]# mysql -u root -p

Enter your database root password when promted.

You should see something like this:

{% highlight bash %}
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 1
Server version: 5.5.30-MariaDB MariaDB Server

Copyright (c) 2000, 2013, Oracle, Monty Program Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> 
{% endhighlight %}

That was easy right?


<object width="560" height="315"><param name="movie" value="http://www.youtube.com/v/EZe140Gj1qA?version=3&amp;hl=en_US"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/EZe140Gj1qA?version=3&amp;hl=en_US" type="application/x-shockwave-flash" width="560" height="315" allowscriptaccess="always" allowfullscreen="true"></embed></object>


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}
