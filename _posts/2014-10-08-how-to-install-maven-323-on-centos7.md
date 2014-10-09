---
layout: post
title: "How to install Maven 3.2.3 on CentOS7"
description: "How to install Maven 3.2.3 on CentOS7"
categories: [ Linux, CentOS7, Java, Maven, Programming, Project Management]
tags: [ Linux, CentOS7, Java, Maven, Programming, Project Management ]
comments: false
---


If you are using Fedora, CentOS, Red Hat or Scientific Linux sometimes yum does not have the package for the product you would like to install and Maven is one of them at the time of me writing this blog.  So lets do the install on CentOS7.

I am going to show you how I install Maven 3.2.3 on Fedora, CentOS, Red Hat or Scientific Linux you can do it the same way or find a better way.

### Download Maven and untar it.

The first thing we need to do is to download the Maven tar file and untar it to a shared location on the workstation

{% highlight bash %}
wget http://mirrors.gigenet.com/apache/maven/maven-3/3.2.3/binaries/apache-maven-3.2.3-bin.tar.gz
su -c "tar -zxvf apache-maven-3.2.3-bin.tar.gz -C /usr/local“ 
cd /usr/local
sudo ln -s apache-maven-3.2.3 maven
{% endhighlight %}

### Setup the Maven Environment Variables in shared profile.

The next step is to setup the Maven environment variables in a shared profile so all users on the system will get them import at login time.

{% highlight bash %}
su -c "vi /etc/profile.d/maven.sh"

# Add the following lines to maven.sh
export M2_HOME=/usr/local/maven
export M2=$M2_HOME/bin
PATH=$M2:$PATH 
{% endhighlight %}

### Now test your install of Maven.

Logout of the system and then log back into it. Enter the following command:

{% highlight bash %}
[jsmith@regan ~]$ mvn -version 
{% endhighlight %}



Now that's it. have fun with maven.


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>



{% include JB/setup %}
