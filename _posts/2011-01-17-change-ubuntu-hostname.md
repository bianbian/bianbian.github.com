--- 
layout: post
tags: 
- IT
- ubuntu
type: post
meta: 
  _wpas_skip_twitter: "1"
published: true
status: publish
title: change hostname of ubuntu
---
change hostname, take effect immediately, got lost after reboot

$sudo hostname newhostname

&nbsp;

Change hostname,  take effect after reboot

$sudo vi /etc/hostname

newhostname

&nbsp;

Avoid "unable to resolve host xxx" error

$sudo vi /etc/hosts

127.0.1.1 newhostname
