---
layout: post
title: "How to disable firewalld on CentOS7 and RHEL7 By Johnathan Mark Smith"
description: "How to disable firewalld on CentOS7 and RHEL7 By Johnathan Mark Smith"
categories: [ Linux, Firewalld, CentOS7, RHEL7 ]
tags: [ Linux, Firewalld, CentOS7, RHEL7 ]
comments: false
---

CentOS7 and RHEL7 use Firewalld which is a bit complicated so I am going to show you how to disable it.

### How to stop and disable firewalld

The following two commands will first disable firewalld and then stop it.

{% highlight bash %}
sudo systemctl mask firewalld
sudo systemctl stop firewalld
{% endhighlight %}

Thats it so you box now has NO firewalld running.. you should maybe think about iptables.


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

{% include JB/setup %}
