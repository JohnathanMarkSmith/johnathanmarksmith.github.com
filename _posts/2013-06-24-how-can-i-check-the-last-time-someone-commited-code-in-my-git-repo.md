---
layout: post
title: "How can I check the last time someone commited code in my git repo"
description: "How can I check the last time someone commited code in my git repo"
categories: [ Git, Gitub, Linux ]
tags: [ Git, Github, Linux ]
comments: false
---

I get requested a lot from the manngers to see that last time someone has commited work into the git repo and I have found a quick and easy way.


Just run the following command and it will tell you the last time someone commited work and the number of commited the user did.

        jsmith@regan ~> git shortlog -sne |awk '{print $1,$2,$3,system("git log -n1 --format=%cd --author=" $2)}'
        Thu Jun 13 08:14:49 2013 -0400
        17 Johnathan Smith 0


As you can see from the above example 'Johnathan Smith' has commited 17 units of work and the last time was Thu Jun 13 08:14:49 2013.


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

{% include JB/setup %}
