---
layout: page
title: "Git Interview Questions"
description: "Git Interview Questions"
---

## Git Interview Questions

I really like working with Git and but I really dont like going on interviews and getting asked questions on it.. As developers we really dont have to know EVERYTHING but hard but we should know how to find the anwsers.


## How do I clone a local Git Repository?

This worked for me:

{% highlight bash %}

git clone file:////<host>/<share>/<path>

{% endhighlight %}

For example, if your main machine has the IP 192.168.10.51 and the computer name main, and it has a share named code which itself is a git repository, the both of the following commands should work equally:


{% highlight bash %}

git clone file:////main/code
git clone file:////192.168.10.51/code


{% endhighlight %}

## How do you share a local Git repository?

     git daemon --export-all --base-path=$(pwd)



If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

{% include JB/setup %}
