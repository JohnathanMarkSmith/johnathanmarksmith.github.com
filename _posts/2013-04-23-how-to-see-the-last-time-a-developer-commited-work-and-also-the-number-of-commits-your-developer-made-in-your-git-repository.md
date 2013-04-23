---
layout: post
title: "How to see the last time a developer commited work and also the number of commits your developer made in your Git repository"
description: "How to see the last time a developer commited work and also the number of commits your developer made in your Git repository"
categories: [ Linux, Git]
tags: [ Linux, Git ]
comments: false
---

How would you like to check-up on your developers and see that last time your developers commited work to your Git repository.  I do this all the time to check on the developers on my projects. 

The best way to see who is commiting work to your Git repository and the last time is easy.  Just go into one of your Git repositories and type the following:

{% highlight bash %}
git shortlog -sne |awk '{print $1,$2,$3,system("git log -n1 --format=%cd --author=" $2)}'
{% endhighlight %}

and your output should look like:

{% highlight bash %}
Wed Apr 10 11:35:41 2013 -0400
3 Johnathan Smith 0
{% endhighlight %}

This will show you who is doing all the work and the last time work was commited..... 

Now that's it. have fun with Git. 

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>



{% include JB/setup %}
