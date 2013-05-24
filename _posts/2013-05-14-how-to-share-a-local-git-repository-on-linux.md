---
layout: post
title: "How to share a local git repository on linux"
description: "How to share a local git repository on linux"
categories: [ Linux, Git, Git Interview Question ]
tags: [ Linux, Git, Git Interview Question ]
comments: false
---

Sometimes you will find the need to share a local git repository with some of your co-workers without putting the reposiotry on a server.

### There are five possibilities to set up a repository for pull from

You have a number of ways to share your lcoal git repository with others.

*   Local filesystem: git clone /path/to/repo or git clone file://path/to/repo. Least work if you have networked filesystem, but not very efficient use of network. 

*   HTTP protocols: git clone http://example.com/repo. You need any web server, and you also need to run (perhaps automatically, from a hook) git-update-server-info to generate information required for fetching/pulling via "dumb" protocols.

*   SSH: git clone ssh://example.com/srv/git/repo or git clone example.com:/srv/git/repo. You need to setup SSH server (SSH daemon), and have SSH installed on client (e.g. PuTTY on MS Windows).

*   git protocol: git clone git://example.com/repo. You need to run git-daemon on server; see documentation for details (you can run it as standalone process only for fetching, not necessary run as service). git-daemon is a part of git.

*   bundle: You generate bundle on server using git-bundle command, transfer it to a client machine in any way (even via USB), and clone using git clone file.bndl (if clone does not work, you can do "git init", "git remote add" and "git fetch").

### How do I share my local git repository

I like to share my local git repository but using the git-daemon. First I move to the folder that has all my repo's in it and then I issue the following commands:

    git daemon --export-all --base-path=$(pwd)

Now to clone the shared repository, use

    git clone git://HOSTNAME/ REPOSITORY_NAME
    # e.g., git clone git://my-machine/ test-project


That was easy right?

<object width="560" height="315"><param name="movie" value="http://www.youtube.com/v/fCWVg6cmXyY?hl=en_US&amp;version=3"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/fCWVg6cmXyY?hl=en_US&amp;version=3" type="application/x-shockwave-flash" width="560" height="315" allowscriptaccess="always" allowfullscreen="true"></embed></object>


You can see the full list of <a href="/git-interview-questions.html">Git Interview Questions Here</a>


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

{% include JB/setup %}
