---
layout: post
title: "How to install Maven on Fedora, CentOS, Red Hat and Scientific Linux"
description: "How to install Maven on Fedora, CentOS, Red Hat and Scientific Linux"
categories: [ Linux, Java, Maven ]
tags: [ Linux, Java, Maven ]
comments: false
---

If you are using Fedora, CentOS, Red Hat or Scientific Linux sometimes yum does not have the package for the product you would like to install and Maven is one of them at the time of me writing this blog.

I am going to show you how I install Maven on Fedora, CentOS, Red Hat or Scientific Linux you can do it the same way or find a better way.

### Download Maven and untar it.

The first thing we need to do is to download the Maven tar file and untar it to a shared location on the workstation

{% highlight bash %}
wget http://mirrors.gigenet.com/apache/maven/maven-3/3.0.5/binaries/apache-maven-3.0.5-bin.tar.gz
su -c "tar -zxvf apache-maven-3.0.4-bin.tar.gz -C /opt/" 
{% endhighlight %}

### Setup the Maven Environment Variables in shared profile.

The next step is to setup the Maven environment variables in a shared profile so all users on the system will get them import at login time.

{% highlight bash %}
su -c "vi /etc/profile.d/maven.sh"

# Add the following lines to maven.sh
export M2_HOME=/opt/apache-maven-3.0.5
export M2=$M2_HOME/bin
PATH=$M2:$PATH 
{% endhighlight %}

### Now test your install of Maven.

Logout of the system and then log back into it. Enter the following command:

{% highlight bash %}
[jsmith@regan ~]$ mvn -version 
{% endhighlight %}

If you did everything right your output should look something like the one below:

{% highlight bash %}
Apache Maven 3.0.5 (r01de14724cdef164cd33c7c8c2fe155faf9602da; 2013-02-19 08:51:28-0500)
Maven home: /opt/apache-maven-3.0.5
Java version: 1.7.0_19, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-1.7.0-openjdk-1.7.0.19/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "2.6.32-358.2.1.el6.i686", arch: "i386", family: "unix"
{% endhighlight %}

Now that's it. have fun with maven. 

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>




{% include JB/setup %}
