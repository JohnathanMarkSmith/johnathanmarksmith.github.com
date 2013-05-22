---
layout: post
title: "How To Install Gitolite on Linux"
description: "How To Install Gitolite on Linux"
categories: [ Git, Gitolite, Linux ]
tags: [ Git, Gitolite, Linux ]
comments: false
---

### Why Gitolite

Git by itself does not do any access control -- it relies on the transport medium to do authentication ("who are you?"), and on OS file permissions to do authorisation ("what are you allowed to do?").

Git also comes with a program called "git-shell" which can act as a restricted login shell if you don't want users getting a proper shell. Using this and judicious use of Unix groups, you can allow some people read-only access while others get read-write access, etc. This is probably sufficient if your needs are simple and don't change too often.

However, gitolite does this much better, and offers many more features

Gitolite is useful in any server that is going to host multiple git repositories, each with many developers, where "anyone can do anything to any repo" is not a good idea....

Giteolite will let you pick which developers have access to which repositories and which branches and more.... Gitolite, Gitolite, Gitolite it will save you!!!


### How To Install Gitolite on Linux

Login in as root

now you have to create the git(make it git or gitolite) account

{% highlight bash %}
    useradd git
    passwd git
{% endhighlight %}

Now login as git or gitolite

You need to copy your SSH public key (a file called ~/.ssh/id_rsa.pub) from your workstation, renaming it to yourname.pub (we'll use jsmith.pub in our examples).

From my workstations

{% highlight bash %}
   scp ~/.ssh/id_rsa.pub git@REGAN:/home/git/jsmith.pub 
{% endhighlight %}

Now run the following commands from the git account

{% highlight bash %}
   git clone git://github.com/sitaramc/gitolite
   mkdir bin
   gitolite/install -ln
   gitolite setup -pk jsmith.pub
{% endhighlight %}

### Now for Testing

From your workstation enter the following command

{% highlight bash %}
   ssh git@REGAN info
{% endhighlight %}

your output should look something like this

{% highlight bash %}
   hello jsmith, this is git@regan running gitolite3 v3.5.1-4-g2f48a3e on git 1.8.2.3

    R W		gitolite-admin
    R W		testing
{% endhighlight %}

### Time To Be a Gitolite Admin

From your workstation enter the following command

{% highlight bash %}
   git clone git@<server>:gitolite-admin
   cd gitolite-admin
{% endhighlight %}

That is everything you have gitolite all setup and ready to go.


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

{% include JB/setup %}
