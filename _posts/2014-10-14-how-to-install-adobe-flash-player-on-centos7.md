---
layout: post
title: "How to install Adobe Flash Player on CentOS7"
description: "How to install Adobe Flash Player on CentOS7"
categories: [ Linux, Flash, CentOS7, RHEL7]
tags: [ Linux, Flash, CentOS7, RHEL7 ]
comments: false
---

In this post I am going to show you how to install the Adobe Flash player on CentOS7 and RHEL7.

Adobe provided yum repository that contains RPM packages of Adobe Linux Software. 

You use yum command to install either 32 or 64 bit flash player on a CentOS7 Linux operating system.



### Adding Adobe repository to Yum and Insall
To add the adobe repository to Yum you have to enter the following command.

{% highlight bash %}
rpm -ivh http://linuxdownload.adobe.com/adobe-release/adobe-release-x86_64-1.0-1.noarch.rpm
{% endhighlight %}

After you add the repositor to yum you need to run the install command to now install the flash-plugin

{% highlight bash %}
yum install flash-plugin
{% endhighlight %}

Now that everything is installed you need to test it!

Open Firefox and type the following URL:

{% highlight bash %}
about:plugins
{% endhighlight %}


Now that's it. have fun with Flash on CentOS7 now.


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}
