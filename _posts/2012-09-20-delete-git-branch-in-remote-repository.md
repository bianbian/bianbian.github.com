---
layout: post
title: delete git branch in remote repository
category: tech
tags: linux, git
---
Command `git push <remote> :<name>` can used for deleting a branch in remote repository from git V1.5.0.  
But from git v1.7.0, this behaviour is [refused by default](https://github.com/gitster/git/blob/master/Documentation/RelNotes/1.7.0.txt).  
Command `git push origin --delete branch` is used instead with git 1.7.0+
> "git push" learned "git push origin --delete branch", a syntactic sugar for "git push origin :branch".

Ref:  
  [How do I delete a Git branch both locally and in Github?](http://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-both-locally-and-in-github)
