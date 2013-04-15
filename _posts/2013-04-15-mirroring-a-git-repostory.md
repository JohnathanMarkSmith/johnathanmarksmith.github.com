---
layout: post
title: "Mirroring a Git repostory"
description: ""
categories: [Git, Programming, GitHub]
tags: [Git, Programming, Github]
comments: false
---

The firm I recently stated working at just moved to Git and I am the only resource then knows Git. I get asked so many times a day on how to mirror a git repostory.

From the birds eyes very its very easy:

git clone --mirror git@git.com:project project

cd project

git remote add github git@github.com:username/project.git


In cron Job

cd /pathto/project && git fetch -q && git push -q --mirror github


Thats how easy it is to mirror a Git Project on to GitHub

{% include JB/setup %}
