---
layout: post
title: "How to install Jekyll on Linux Mint"
description: "How to install Jekyll on Linux Mint"
categories: [ Linux, Mint, LinuxMint, Jekyll ]
tags: [ Linux, Mint, LinuxMint, Jekyll ]
comments: false 
---

I found using Jekyll for websites and blogging is great but sometimes its not so easy getting your OS up and running with it.  Linux Mint makes it very easy to work with.  All you have to do is install ruby, rake, jekyll, nodejs and you are all ready to blog, So OS's dont make it easy to get everything install but with Linux Mint it is very easy all you have to do is following the 3 commands below.

{% highlight bash %}
sudo apt-get install ruby ruby-dev make rake
sudo gem install jekyll --no-rdoc --no-ri
sudo apt-get install nodejs 
{% endhighlight %}

After doing the install you are all ready to start to use jekyll on Linux Mint.


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}
