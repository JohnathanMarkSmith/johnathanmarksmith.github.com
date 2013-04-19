---
layout: post
title: "How to install Apache2 and PHP on Fedora, CentOS, Red Hat and Scientific Linux"
description: "How to install Apache2 and PHP on Fedora, CentOS, Red Hat and Scientific Linux"
categories: [ Linux, Apache, PHP ]
tags: [ Linux, Apache, PHP ]
comments: false
---

If you are using Fedora, CentOS, Red Hat or Scientific Linux I am going to show you the basic install of Apache2 and PHP using yum.

### Install Apache2.

To install Apache2 just enter the following command:
{% highlight bash %}
yum install httpd
{% endhighlight %}

### Install PHP

To install PHP just enter the following command:
{% highlight bash %}
yum install php
{% endhighlight %}

### Start up Apache2

The following command is going to setup Apache and set it up to start everytime your workstation or server books.
{% highlight bash %}
chkconfig --level 2345 httpd on; service httpd start
{% endhighlight %}

### Test Your Install

Now its time to test your install of Apache2 and PHP, To Do this we are going to make a small PHP file and run in from your brower.

The following command will create and index.php file with the PHPInfo command in it:
{% highlight bash %}
 sudo echo “<?php phpinfo(); ?>” > /var/www/html/index.php
{% endhighlight %}

Now launch your browser to http://127.0.0.1 or http://localhost if anything was done righ your output should look like the one below:


<div style="text-align: center">
<img src="/images/php.jpg" alt="Install Apache2 and PHP with Johnathan Mark Smith">
</div>


Now that's it. have fun with Apache2 and PHP. 

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>



{% include JB/setup %}
