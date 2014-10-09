---
layout: post
title: "How to install Apache2 on CentOS7"
description: "How to install Apache2 on CentOS7"
categories: [ Linux, Apache2, CentOS7 ]
tags: [ Linux, Apache2, CentOS7 ]
comments: false
---

CentOS 7 ships with Apache 2.4 so it is directly avaliable as a CentOS 7 package. So we can install it just like this

{% highlight bash %}
sudo yum install httpd
{% endhighlight %}

By default apache should be installed, if not then install it as shown above

### Configure your system to start Apache on boot

Now lets configure your system to start apache on boot

{% highlight bash %}
sudo systemctl start httpd.service
sudo systemctl enable httpd.service
{% endhighlight %}


Now direct your browser to http://127.0.0.1 and you should see the apache2 home page

Now that's it. have fun with Apache2.


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>
{% include JB/setup %}
