---
layout: post
title: "How to install MySQL on Fedora, CentOS, Red Hat and Scientific Linux"
description: "How to install MySQL on Fedora, CentOS, Red Hat and Scientific Linux"
categories: [ Linux, MySQL ]
tags: [ Linux, MySQL ]
comments: false
---

If you are using Fedora, CentOS, Red Hat or Scientific Linux I am going to show you the basic install of MySQL using yum.

### Install MySQL Client and Server software

To install MySQL Client and Server enter the following commands:
{% highlight bash %}
[root@regan ~]# yum groupinstall "MySQL Database server"
[root@regan ~]# yum groupinstall "MySQL Database client"
{% endhighlight %}

### To install MySQL system tables and Setup MySQL to start on boot

To install the MySQL system tables and setup MySQL to start on boot you need to enter the following commands:
{% highlight bash %}
[root@regan ~]# /usr/bin/mysql_install_db --user=mysql
[root@regan ~]# chkconfig --level 2345 mysqld on; service mysqld start
{% endhighlight %}

### Set Admin Password

To set the admin password for the MySQL databse you need to  enter the following commands:
{% highlight bash %}
[root@regan ~]# /usr/bin/mysqladmin -u root password 'new-password'
[root@regan ~]# /usr/bin/mysqladmin -u root -h regan password 'new-password'
{% endhighlight %}

Now that's it. have fun with MySQL. 

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}
