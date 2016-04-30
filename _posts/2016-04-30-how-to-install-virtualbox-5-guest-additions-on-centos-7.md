---
layout: post
title: "How to install VirtualBox 5 Guest Additions on CentOS 7"
description: "How to install VirtualBox 5 Guest Additions on CentOS 7"
categories: [ Linux, VirtualBox, CentOS 7, How-To ]
tags: [ Linux, VirtualBox, CentOS 7, How-To  ]
comments: false 
---

So last night I had to upgate to VirtualBox 5 due to installing the new MAC os.  After installing VirutalBox5 I wanted to setup my guest linux which I like to use CentOS 7. 

I did the basic install of CentOS7 but then wanted to add the VirtualBox Guest Additions but I was going so many errors. After doing some research and playing around I found all the packages that you need to have installed on CentOS7 before trying to install the VirtualBox Guest Addition.

In this post I am going to show you a quick and easy way to install everything you need.

Just run the following commands:

{% highlight bash %}
sudo yum install kernel-devel-3.10.0-327.el7.x86_64
sudo yum install kernel-devel
sudo yum install gcc*
sudo yum install epel-release
{% endhighlight %}


Now that we have everything we need to do the VirtualBox Guest install you should not have any issues..



If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>
{% include JB/setup %}
