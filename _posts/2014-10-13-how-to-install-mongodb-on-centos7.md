---
layout: post
title: "How to install MongoDB server on CentOS7 and RHEL7"
description: "How to install MongoDB server on CentOS7  and RHEL7"
categories: [ Linux, MongoDB, CentOS7, RHEL7]
tags: [ Linux, MongoDB, CentOS7, RHEL7 ]
comments: false
---

So I am going to show you how to install MongoDB on CentOS7 and RHEL7 today.

First thing we need to do is to add the MongoDB repo to yum.


### Adding MongoDB repo to Yum

{% highlight bash %}
vim /etc/yum.repos.d/mongodb.repo
{% endhighlight %}

Next insert the following lines into the repo file you just created.

{% highlight bash %}
[mongodb]
name=MongoDB repo
baseurl=http://downloads-distro.mongodb.org/repo/redhat/os/x86_64/
gpgcheck=0
enabled=1
{% endhighlight %}

After you saved the file with the repo information you will need to install the MongoDB packages using yum.


### Installing MongoDB packages

{% highlight bash %}
yum install mongodb-org
{% endhighlight %}

Now that you have MongoDB packages installed you will need to start the MongoDB service using systemd.

### Starting MongoDB Server
{% highlight bash %}
sudo systemctl start mongod.service
{% endhighlight %}
 
Now lets check to see if MongoDB is running and also open up the firewall so we can access it.

### Checking to see if mongoDB is running


{% highlight bash %}
ps -ef  |  grep   mongo
{% endhighlight %}

### Opening up the ports on the firewall


{% highlight bash %}
sudo firewall-cmd --zone=public --add-port=27017/tcp --permanent
sudo firewall-cmd --reload
{% endhighlight %}

 

Now that's it. have fun with MongoDB.



If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>
{% include JB/setup %}