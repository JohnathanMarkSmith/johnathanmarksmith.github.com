---
layout: post
title: "How to install grails on a linux machine"
description: "How to install grails on a linux machine"
categories: [ Linux, Mint, LinuxMint, Grails  ]
tags: [ Linux, Mint, LinuxMint, Grails  ]
comments: false 
---

In this post I am going to show you a quick and easy way to install grails 2.2.2 on a linux machine.  You can install grails many ways but I like to do it this way so its install and running under my profile.

The first thing we are going to do is to download and unzip grails

{% highlight bash %}
wget http://dist.springframework.org.s3.amazonaws.com/release/GRAILS/grails-2.2.2.zip
unzip grails-2.2.2.zip
{% endhighlight %}


Now that we have it all ready to use (downloaded and unzip) we need to setup the environment variables.  Add the following environment variables to your .bashrc (I assume you are using bash as your shell)  

{% highlight bash %}
export GRAILS_HOME=/home/jxsmith/grails-2.2.2
export JAVA_HOME=/usr/lib/jvm/java-6-openjdk-amd64
export PATH=$PATH:$JAVA_HOME/bin:$GRAILS_HOME/bin
{% endhighlight %}

Now logout of your profile and running the following command (you should see the version number)

{% highlight bash %}
grails -version
{% endhighlight %}

If you see the version number your all done and its ready to use.



If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>
{% include JB/setup %}
