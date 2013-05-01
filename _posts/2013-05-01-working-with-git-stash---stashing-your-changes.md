---
layout: post
title: "Working with Git stash   Stashing Your Changes"
description: "Working with Git stash   Stashing Your Changes"
categories: [ Git, Programming ]
tags: [ Git, Programming ]
comments: false---

Stashing is a great way to pause what you’re currently working on and come back to it later. For example, if you working on that awesome, brand new feature but someone just found a bug that you need to fix. Add your changes to the index using

	git add .

Or add individual files to the index, your pick. Stash your changes away with:

	git stash

And boom! You’re back to your original working state. Got that bug fixed? Bring your work back with:

	git stash apply

You can also do multiple layers of stashes, so make sure to use

	git stash list

To check out all of your current ones. If you need to apply a stash from deeper in the stack, that’s easy too. Here’s how to apply the second stash you’ve got:

	git stash apply stash@{1}

You can also easily apply the top stash on the stack by using:

	git stash pop

A note with this command, it deletes that stash for good, while apply does not. You can manually delete stashes with:

	git stash drop <id>

Or delete all of the stored stashes with:

	git stash clear

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

{% include JB/setup %}
