---
layout: post
title: "How to Reset Git Branch to Origin Version"
description: "How to Reset Git Branch to Origin Version"
categories: [ Linux, Git, Git Interview Question ]
tags: [ Linux, Git, Git Interview Question ]
comments: false
---
I get asked a lot from the developers "how do I reset a branch in Git", This is very easy to do if you did not pushed the branch to the origin yet.  You can reset the branch to the upstream branch by using the following commands.

{% highlight bash %}
git checkout thebranch
git reset --hard origin/thebranch
{% endhighlight %}

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>
{% include JB/setup %}
