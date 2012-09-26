--- 
layout: post
title: change hostname of ubuntu
category: tech
tags: 
- linux
- ubuntu
---
## Change hostname, take effect immediately, got lost after reboot

	$sudo hostname newhostname

## Change hostname,  take effect after reboot

	$sudo vi /etc/hostname

change to:

newhostname

## Avoid "unable to resolve host xxx" error

	$sudo vi /etc/hosts

add a line:

	127.0.1.1 newhostname
