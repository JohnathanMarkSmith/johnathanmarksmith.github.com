---
layout: post
title: "Quick Fix for Git SSL Certificates Problem"
description: "Quick Fix for Git SSL Certificates Problem"
categories: [ Git, SSL ]
tags: [ Git, SSL ]
comments: false
---

I get asked sometimes a number of times per day do I have a quick fix for the Git SSL Certificates Problem that shows up if you dont have the certificate installed on your workstation the right way.

Solution #1 – The super-easy but bad solution, but it works!!

Simply use the git global preferences to turn off SSL  verification:

{% highlight bash %}
git config --global http.sslVerify false
{% endhighlight %}

The downside is? Well what is the point in using https if you have turned off SSL verification… This solution is not recommended as it leaves you vulnerable to man-in-the-middle attacks, but it is a quick fix and it works. So if you are not going to a repo over the internet then this is a quick fixed that is fine.

<object width="640" height="480"><param name="movie" value="//www.youtube.com/v/x5IbMiATtA8?hl=en_US&amp;version=3"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="//www.youtube.com/v/x5IbMiATtA8?hl=en_US&amp;version=3" type="application/x-shockwave-flash" width="640" height="480" allowscriptaccess="always" allowfullscreen="true"></embed></object>

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}
