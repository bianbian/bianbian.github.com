---
layout: post
title: delete git branch in remote repository
category: tech
tags: linux, git
---
How to deleting a git branch in remote repository?

In git v1.5.x and 1.6.x:

    git push <remote> :<name>

In git v1.7.0+:

	git push origin --delete branch

Ref:  

* [How do I delete a Git branch both locally and in Github?](http://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-both-locally-and-in-github)
* ["git push" learned "git push origin --delete branch", a syntactic sugar for "git push origin :branch"](https://github.com/gitster/git/blob/master/Documentation/RelNotes/1.7.0.txt)
