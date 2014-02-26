---
layout: post
title: "How I use Git with my projects"
description: "How I use Git with my projects"
categories: [ Git ]
tags: [ Git ]
---

This post is a copy of the guide I give to new programmers on my project.  This is only a guide on how I like to work with git and my project. You may have a better way.  If you like this guide just change ProjectX to your project name and you can use it

# Using Git with ProjectX

This document is going to give you the basic commands you need to develop code for the ProjectX product using git SCM.


# Overview of the branches in the central repository
At the core, the development model is greatly inspired by existing models out there. The central repo holds two main branches with an infinite lifetime:

* master
* develop

The master branch at origin should be familiar to every Git user. Parallel to the master branch, another branch exists called develop.

We consider origin/master to be the main branch where the source code of HEAD always reflects a production-ready state.
We consider origin/develop to be the main branch where the source code of HEAD always reflects a state with the latest delivered development changes for the next release. Some would call this the “integration branch”. This is where any automatic nightly builds are built from. 

When the source code in the develop branch reaches a stable point and is ready to be released, all of the changes should be merged back into master somehow and then tagged with a release number. How this is done in detail will be discussed further on.

Therefore, each time when changes are merged back into master, this is a new production release by definition. We tend to be very strict at this, so that theoretically, we could use a Git hook script to automatically build and roll-out our software to our production servers every time there was a commit on master.

## The different types of branches we may use are:
* Feature / Fix branches
* Release branches
* Hotfix branches

Each of these branches have a specific purpose and are bound to strict rules as to which branches may be their originating branch and which branches must be their merge targets. We will walk through them in a minute.

By no means are these branches “special” from a technical perspective. The branch types are categorized by how we use them. They are of course plain old Git branches.

# Getting ProjectX from the central repository

Once your git admin has give you access to the ProjectX repository all your have to do to clone

the repository is type the following command:
	$ git clone ssh://git@<server>/ProjectX
	
Before you keep reading please keep in mind that no one should merge code into the master branch but the lead developer on the project...


# Feature / Fix branches

* May branch off from: develop
* Must merge back into: develop
* Branch naming convention: anything except master, develop, release-*, or hotfix-*

Feature branches (or sometimes called topic branches) are used to develop new features for the upcoming or a distant future release. When starting development of a feature or fix, the target release in which this feature will be incorporated may well be unknown at that point. The essence of a feature branch is that it exists as long as the feature is in development, but will eventually be merged back into develop (to definitely add the new feature to the upcoming release) or discarded (in case of a disappointing experiment).

Feature branches typically exist in developer repos only, not in origin.

If you are working on an issue you should name the branch the same as the TIMS ticket so we know what bug this branch addressed.

# Creating a feature / fix branch

When starting work on a new feature or fix, branch off from the develop branch.
	$ git checkout -b myfeature develop

# Incorporating a finished feature / fix on develop

Finished features may be merged into the develop branch definitely add them to the upcoming
release once QA has tested it and has signed off:

	$ git checkout develop
	$ git merge --no-ff myfeature

	$ git branch -d myfeature
	Deleted branch myfeature (was 05e9557)
	
NEVER PUSH YOUR CODE TO THE CENTRAL REPOSITORY UNTIL QA SIGNED OFF AND TESTED YOUR CHANGE!!!!!!

	$ git push origin develop
	

The --no-ff flag causes the merge to always create a new commit object, even if the merge could be performed with a fast-forward.

This avoids losing information about the historical existence of a feature branch and groups together all commits that together added the feature.

In the latter case, it is impossible to see from the Git history which of the commit objects together have implemented a feature—you would have to manually read all the log messages.

Reverting a whole feature (i.e. a group of commits), is a true headache in the latter situation, whereas it is easily done if the --no-ff flag was used.

Yes, it will create a few more (empty) commit objects, but the gain is much bigger that that cost. Unfortunately, I have not found a way to make --no-ff the default behaviour of git merge yet, but it really should be.


# Release branches

* May branch off from: develop
* Must merge back into: develop and master
* Branch naming convention: release-v*

Release branches support preparation of a new production release. They allow for last-minute dotting of i’s and crossing t’s. Furthermore, they allow for minor bug fixes and preparing metadata for a release (version number, build dates, etc.). By doing all of this work on a release branch, the develop branch is cleared to receive features for the next big release.

The key moment to branch off a new release branch from develop is when develop (almost) reflects the desired state of the new release. At least all features that are targeted for the release-to-be-built must be merged in to develop at this point in time. All features targeted at future releases may not—they must wait until after the release branch is branched off.

It is exactly at the start of a release branch that the upcoming release gets assigned a version number—not any earlier. Up until that moment, the develop branch reflected changes for the “next release”, but it is unclear whether that “next release” will eventually become 0.3 or 1.0, until the release branch is started. That decision is made on the start of the release branch and is carried out by the project’s rules on version number bumping.

# Creating a release branch

Release branches are created from the develop branch. For example, say version 1.1.5 is the current production release and we have a big release coming up. The state of develop is ready for the “next release” and we have decided that this will become version 1.2 (rather than 1.1.6 or 2.0). So we branch off and give the release branch a name reflecting the new version number:
	
	$ git checkout -b release-v1.2 develop
	Switched to a new branch "release-v1.2"
	
Modify some files?

	$ git commit -a -m "Bumped version number to 1.2"
	[release-1.2 74d9424] Bumped version number to 1.2
	1 files changed, 1 insertions(+), 1 deletions(-)

After creating a new branch and switching to it, we bump the version number. Here we make some changes to some files in the working copy to reflect the new version. (This can of course be a manual change—the point being that some files change.) ?

This new branch may exist there for a while, until the release may be rolled out definitely. During that time, bug fixes may be applied in this branch (rather than on the develop branch). Adding large new features here is strictly prohibited. They must be merged into develop, and therefore, wait for the next big release.

# Finishing a release branch

When the state of the release branch is ready to become a real release, some actions need to be carried out. First, the release branch is merged into master (since every commit on master is a new release by definition, remember). Next, that commit on master must be tagged for easy future reference to this historical version. Finally, the changes made on the release branch need to be merged back into develop, so that future releases also contain these bug fixes.

The first two steps in Git:

	$ git checkout master
	Switched to branch 'master'

	$ git merge --no-ff release-v1.2
	Merge made by recursive.

	$ git tag -a v1.2

The release is now done, and tagged for future reference.

To keep the changes made in the release branch, we need to merge those back into develop,
though. In Git:

	$ git checkout develop
	Switched to branch 'develop'

	$ git merge --no-ff release-v1.2
	Merge made by recursive.

This step may well lead to a merge conflict (probably even, since we have changed the version number). If so, fix it and commit.

Now we are really done and the release branch may be removed, since we don’t need it any more:

	$ git branch -d release-v1.2
	Deleted branch release-v1.2 (was ff452fe).

	
# Hotfix branches

* May branch off from: master
* Must merge back into: develop and master(only lead developer)
* Branch naming convention: hotfix-*

Hotfix branches are very much like release branches in that they are also meant to prepare for a new production release, albeit unplanned. They arise from the necessity to act immediately upon an undesired state of a live production version. When a critical bug in a production version must be resolved immediately, a hotfix branch may be branched off from the corresponding tag on the master branch that marks the production version.

The essence is that work of team members (on the develop branch) can continue, while another person is preparing a quick production fix.

TRY TO NEVER DO A HOTFIX.

# Creating the hotfix branch
Hotfix branches are created from the master branch. For example, say version 1.2 is the current production release running live and causing troubles due to a severe bug. But changes on develop are yet unstable. We may then branch off a hotfix branch and start fixing the problem:

	$ git checkout -b hotfix-1.2.1 master
	Switched to a new branch "hotfix-1.2.1"

	$ ./bump-version.sh 1.2.1
	Files modified successfully, version bumped to 1.2.1.

	$ git commit -a -m "Bumped version number to 1.2.1"

	[hotfix-1.2.1 41e61bb] Bumped version number to 1.2.1
	1 files changed, 1 insertions(+), 1 deletions(-)

Don’t forget to bump the version number after branching off!

Then, fix the bug and commit the fix in one or more separate commits.

	$ git commit -m "Fixed severe production problem"
	[hotfix-1.2.1 abbe5d6] Fixed severe production problem
	5 files changed, 32 insertions(+), 17 deletions(-)

# Finishing a hotfix branch

## THIS SHOULD BE DONE BY LEAD DEVELOPER ONLY!

When finished, the bugfix needs to be merged back into master, but also needs to be merged back into develop, in order to safeguard that the bugfix is included in the next release as well. This is completely similar to how release branches are finished.

First, update master and tag the release.
	$ git checkout master
	Switched to branch 'master'
	
	$ git merge --no-ff hotfix-1.2.1
	Merge made by recursive.
	
	$ git tag -a v1.2.1

Next, include the bugfix in develop, too:

	$ git checkout develop
	Switched to branch 'develop'
	
	$ git merge --no-ff hotfix-1.2.1
	Merge made by recursive.

	The one exception to the rule here is that, when a release branch currently exists, the hotfix changes need to be merged into that release branch, instead of develop. Back-merging the bugfix into the release branch will eventually result in the bugfix being merged into develop too, when the release branch is finished. (If work in develop immediately requires this bugfix and cannot wait for the release branch to be finished, you may safely merge the bugfix into develop now already as well.)

Finally, remove the temporary branch:

	$ git branch -d hotfix-1.2.1
	Deleted branch hotfix-1.2.1 (was abbe5d6).

## NEVER PUSH YOUR CODE TO THE CENTRAL REPOSITORYUNTIL QA SIGNED OFF AND TESTED YOUR CHANGE!!!!!!

	$ git push origin develop

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


Thanks, Johnathan Mark Smith
{% include JB/setup %}
