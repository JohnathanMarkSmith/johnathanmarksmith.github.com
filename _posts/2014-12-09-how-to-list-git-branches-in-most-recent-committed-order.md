---
layout: post
title: "How to list Git branches in most recent committed order"
description: "How to list Git branches in most recent committed order"
categories: [ Git, Github,  ]
tags: [ Git, Github,  ]
comments: false 
---

I been getting asked a lot on how to find the most updated branch in Git.   Below I am going to show you 3 commands that will help you.

### Lets Get To The Commands

This first command is only going to show you the commits and the order of them

{% highlight bash %}
$ git for-each-ref --sort=-committerdate refs/heads/
4afeb5072c9667b4aef6d5c4fe17ae686b83fbd8 commit refs/heads/master
{% endhighlight %}

This command is better it will show you the branch, date of commit and author

{% highlight bash %}
$ git for-each-ref --sort=-committerdate refs/heads/ --format='%(refname) %(committerdate) %(authorname)' | sed 's/refs\/heads\///g'
master Thu Oct 2 08:56:32 2014 -0700 Johnathan Mark Smith
{% endhighlight %}


Now for the command I like the best, This one will show you the date, author and then the branch

{% highlight bash %}
$ git for-each-ref --sort=-committerdate refs/heads/ --format='%(committerdate:short) %(authorname) %(refname:short)'
2014-10-02 Johnathan Mark Smith master
{% endhighlight %}


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

{% include JB/setup %}
