---
layout: post
title: "How to install MariaDB on CentOS7"
description: "How to install MariaDB on CentOS7"
categories: [ Linux, MariaDB, MySQL, CentOS7, RHEL7]
tags: [ Linux, MariaDB, MySQL, CentOS7, RHEL7 ]
comments: false
---

Centos 7 comes with MariaDB instead of MySQL. MariaDB is a open source equivalent to MySQL and I am going to show you how to install it right now. 

If you must have MySQL you need to add the mysql-community repo by using the following command

{% highlight bash %}
sudo rpm -Uvh http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm
{% endhighlight %}

and then you can install MySQL like you normally...

Now let me show you how to install MariaDB on CentOS7. The first step is to install the MariaDB server and client

{% highlight bash %}
sudo yum -y install mariadb-server mariadb
{% endhighlight %}

After running the above command we need to start the MariaDB server and enable it in systemd

{% highlight bash %}
sudo systemctl start mariadb.service
sudo systemctl enable mariadb.service
{% endhighlight %}

Now that MariaDB server is enable and running you need to run the install script. Run the following command and anwser the questions

{% highlight bash %}
sudo mysql_secure_installation
{% endhighlight %}

Now that you did everything you are all done... you can now login to the MariaDB server by using the client command

{% highlight bash %}
mysql
{% endhighlight %}


Now that's it. have fun with MariaDB on CentOS7.

<object width="640" height="480"><param name="movie" value="//www.youtube-nocookie.com/v/ZTxYgPahmUU?hl=en_US&amp;version=3"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="//www.youtube-nocookie.com/v/ZTxYgPahmUU?hl=en_US&amp;version=3" type="application/x-shockwave-flash" width="640" height="480" allowscriptaccess="always" allowfullscreen="true"></embed></object>


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>
{% include JB/setup %}
