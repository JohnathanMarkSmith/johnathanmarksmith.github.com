---
layout: post
title: "How to see the number of commits your developers made in your Git repository"
description: "How to see the number of commits your developers made in your Git repository"
categories: [ Linux, Git]
tags: [ Linux, Git ]
comments: false
---

It looks like everyone is starting to use Git for version control and I get asked from managers "How can I check who is commiting work and doing all the work?"

The best way to see who is commiting work to your Git repository is easy.  Just go into one of your Git repositories and type the following:

{% highlight bash %}
git shortlog -s -n -e --all
{% endhighlight %}

and your output should look like:

{% highlight bash %}
    33	Johnathan Smith <johnathan.smith@uftwf.org>
    21	Jade <plusjade@gmail.com>
    10	Johnathan Smith <johnathansmith1969@gmail.com>
    10	Yuya Saito <studiomohawk@gmail.com>
     4	Andrea Schiavini <andrea.schiavini@gmail.com>
     3	Anton Vattay <3martini@gmail.com>
     2	Abhijeet Kumar <abhijeet.kumar.ak@gmail.com>
     2	David Joos <david.joos@gmail.com>
     2	Laura Cabrera <lzcabrera@gmail.com>
     2	jayraj <jogjayr@gmail.com>
     1	Adam Kerney <adam.w.kerney@gmail.com>
     1	Alessio Caiazza <nolith@abisso.org>
     1	Alistair Hutchison <github@alistairh.co.uk>
     1	Andrew Kraut <akraut@gmail.com>
     1	Brandon Philips <brandon@ifup.org>
     1	Darren Jeacocke <dazonic@me.com>
     1	Hong Xu <xuhdev@gmail.com>
     1	Ian Li <i@techotaku.net>
     1	James Fleeting <twofivethreetwo@gmail.com>
     1	Jeff Kuchta <jkuchta@gmail.com>
     1	Jesse Chan-Norris <jcn@pith.org>
     1	Kori Roys <kori@koriroys.com>
     1	Liu Lantao <liulantao@gmail.com>
     1	Loren Sands-Ramshaw <lorensr@gmail.com>
     1	Lukas Knuth <mr.luke.187@googlemail.com>
     1	Marko Bauhardt <marko.bauhardt@googlemail.com>
     1	Martijn Pieters <mj@zopatista.com>
     1	Matt Swanson <mdswanson@sep.com>
     1	Michael-Keith Bernard <mkbernard.dev@gmail.com>
     1	Pradeep Nayak <pradeep1288@gmail.com>
     1	Simon Starr <simon@starr.cx>
     1	Stephen Ball <sdball@gmail.com>
     1	Tommaso Visconti <tommaso.visconti@gmail.com>
     1	Victor Widell <victor@topmost.se>
     1	christine <piroko@gmail.com>
{% endhighlight %}

This will show you who is doing all the work..... 

Now that's it. have fun with Git. 

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>



{% include JB/setup %}
