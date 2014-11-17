---
layout: post
title: "How to Enable SSH on Mint"
description: ""
categories: [ Linux, Mint, LinuxMint, SSH ]
tags: [ Linux, Mint, LinuxMint, SSH ]
comments: false 
---

I been getting a number of emails from people that do not know how to enable SSH on Linux Mint systems, so I decided to make this post.

To enable SSH (secure shell) on Linux Mint all you have to do is install the SSH package which is openssh-server

{% highlight bash %}
sudo apt-get update
sudo apt-get install openssh-server
{% endhighlight %}

After doing the install you can test that it works by connecting to the localhost 

{% highlight bash %}
ssh 127.0.0.1
{% endhighlight %}


<object width="640" height="480"><param name="movie" value="//www.youtube.com/v/z4Ci9NX_ej8?version=3&amp;hl=en_US"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="//www.youtube.com/v/z4Ci9NX_ej8?version=3&amp;hl=en_US" type="application/x-shockwave-flash" width="640" height="480" allowscriptaccess="always" allowfullscreen="true"></embed></object>



If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}
