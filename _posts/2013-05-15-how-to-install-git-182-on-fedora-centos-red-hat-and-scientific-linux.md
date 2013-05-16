---
layout: post
title: "How to install Git 1.8.2 on Fedora, CentOS, Red Hat and Scientific Linux"
description: "How to install Git 1.8.2 on Fedora, CentOS, Red Hat and Scientific Linux"
categories: [ Linux, Git, Programming ]
tags: [ Linux, Git, Programming ]
comments: false
---
I always like to use YUM for installing software on Fedora, CentOS, Red Hat and Scientific Linux but someone times the RPM only have old versions of the software I need!

Just Like Git... I need Git 1.8 for something (you dont need the details).  

So I had to download the source for Git, Do a make and then install it and all this will only take about 15 mins... are you ready?

### Time To Download, Make and Install Git

To download, make and install Git all you have to do is enter the following commands in a console that your have root access in

{% highlight bash %}

yum install gettext-devel expat-devel curl-devel zlib-devel openssl-devel
cd /usr/local/src
wget https://www.kernel.org/pub/software/scm/git/git-1.8.2.3.tar.gz
tar xzvf git-1.8.2.3.tar.gz
cd git-1.8.2.3
make prefix=/usr/local all
make prefix=/usr/local install

{% endhighlight %}

After the above is done you should check the version, type in the following command

    git --version

Your output should look something like this:

    git version 1.8.2.3

### Your Identity, Tell Git Who You Are

You need to tell git who you are, the following commands will setup your name and email address:

    config --global user.name "John Doe"
    config --global user.email johndoe@example.com




That's it, your done!



If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>
{% include JB/setup %}
