---
layout: post
title: "Installing LAMP (Linux, Apache, MySQL, PHP) stack on your Raspberry Pi"
description: "Installing LAMP (Linux, Apache, MySQL, PHP) stack on your Raspberry Pi"
categories: [ LAMP, Linux, Raspberry, Pi, Raspberry Pi, How-To ]
tags: [ LAMP, Linux, Raspberry, Pi, Raspberry Pi, How-To  ]
comments: false
---


Learn to set up a LAMP (Linux, Apache, MySQL, PHP) stack on your Raspberry Pi and configure it to work as a web server. 

What you will learn
By following this resource and setting up a web server and WordPress website you will learn how to:
 ◦ Install software on your Raspberry Pi
 ◦ Install and configure Apache, PHP, and MySQL to create a LAMP web server


Set up an Apache web server
{% highlight bash %}
sudo apt-get install apache2 -y
{% endhighlight %}


Install PHP

PHP is a preprocessor: it’s code that runs when the server receives a request for a web page via a web browser. It works out what needs to be shown on the page, and then sends that page to the browser. Unlike static HTML, PHP can show different content under different circumstances. Other languages are also capable of doing this, but since WordPress is written in PHP, that’s what we need to use this time. PHP is a very popular language on the web: huge projects like Facebook and Wikipedia are written in PHP.

Install the PHP package with the following command:
{% highlight bash %}
sudo apt-get install php -y
{% endhighlight %}


Install MySQL

MySQL (pronounced My Sequel or My S-Q-L) is a popular database engine. Like PHP, it’s widely used on web servers, which is why projects like WordPress use it, and why those projects are so popular.

Install the MySQL Server and PHP-MySQL packages by entering the following command into the terminal window:
{% highlight bash %}
sudo apt-get install mysql-server php-mysql -y
{% endhighlight %}


Now restart Apache:
{% highlight bash %}
sudo service apache2 restart
{% endhighlight %}


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>
{% include JB/setup %}

