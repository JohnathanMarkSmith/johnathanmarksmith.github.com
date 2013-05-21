---
layout: post
title: "How to clone a local Git Repository"
description: "How to clone a local Git Repository"
categories: [ Github, Git, Git Interview Question ]
tags: [ Github, Git, Git Interview Question ]
comments: false
---

I get asked a good number of times "How do I clone a local Git Repository?". So do make it easy I am going to pust it on my blog site so I can just follow the link to in.  are you ready??

This worked for me:

{% highlight bash %}

git clone file:////<host>/<share>/<path>

{% endhighlight %}

For example, if your main machine has the IP 192.168.10.51 and the computer name main, and it has a share named code which itself is a git repository, the both of the following commands should work equally:


{% highlight bash %}

git clone file:////main/code
git clone file:////192.168.10.51/code


{% endhighlight %}

If the git repository is in a subdirectory, simply append the path.


You can see the full list of <a href="/git-interview-questions.html">Git Interview Questions Here</a>

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}
