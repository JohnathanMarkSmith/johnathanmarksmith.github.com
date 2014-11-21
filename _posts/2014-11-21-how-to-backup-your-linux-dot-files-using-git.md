---
layout: post
title: "How to backup your linux dot files using Git"
description: "How to backup your linux dot files using Git"
categories: [ Linux, Mint, Git, Github, Backup ]
tags: [ Linux, Mint, Git, Github, Backup ]
comments: false 
---

As you may or may not know that I love working on a Linux OS and I also love working with Git so why not use them both in a blog post??  

What can I do with Linux and Git that I have not seen anywhere else?  

I got it! How about how to backup your Linux dot files like ".bash_profile" using Git and putting them on github so If I move to a new Linux workstation I can just do a pull of all my files..

### Clone My Project to Start

so the first thing we are going to do is to clone my dot files project and move them into a folder called dotfiles

{% highlight bash %}
cd ~/Documents
mkdir dotfiles
git clone git@github.com:JohnathanMarkSmith/mintdotfiles.git
cp mintdotfiles/* dotfiles
{% endhighlight %}

No after you do that you should copy all your dot files into the same folder

{% highlight bash %}
cp ~/.bash_profile ~/Documents/dotfiles/bash_profle
cp ~/.bashrc ~/Documents/dotfiles/bashrc
cp ~/.gitconfig ~/Documents/dotfiles/gitconfig
cp ~/.gitignore ~/Documents/dotfiles/gitignore
cp ~/.vimrc ~/Documents/dotfiles/vimrc
{% endhighlight %}

No lets change the file rights and run the scripte

{% highlight bash %}
cd ~/Documents/dotfiles
chmod +x makesymlinks.sh
./makesymlinks.sh
{% endhighlight %}

Now you need to go into github or bitbucket and create a new repository, once you created one on the server you then use the following commands to setup your local repository and push it to the server

{% highlight bash %}

git init
git add --all
git commit -am "first time load"
git remote add origin ssh://newhost.com/usr/local/gitroot/myproject.git
git push -u origin master
{% endhighlight %}


No you have a backup of all your dot linux files and you can all ways update your backup.


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}