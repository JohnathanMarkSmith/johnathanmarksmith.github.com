---
layout: post
title: "How to load MySQL Database from Command Line in Linux"
description: "How to load MySQL Database from Command Line in Linux"
categories: [ MySQL, Linux, Database ]
tags: [ MySQL, Linux, Database ]
comments: false
I been getting asked, How can I load my MySQL database from the command line? 

So I am going to make this quick and easy...

First cd in the folder where your sql file is, for this demo I am using a file called "backup.mysql". Then use the following command

{% highlight bash %}
mysql --user root --password regandb < backup.mysql
{% endhighlight %}

MySQL will prompt you for a password then your mysql will be loaded depending on how big your backup/file is it may take some time. You could add a -f flag if your database is very big, it will prevent it from stopping if there is error. 


---
{% include JB/setup %}
