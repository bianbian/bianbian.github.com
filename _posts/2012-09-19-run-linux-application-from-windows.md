---
layout: post
title: run linux application from windows
category: tech
tags:
- linux
- X11
---
Environment:

	debian 6  
	windows xp

I have a linux without desktop installed (gnome, kde, etc.), but I need run GUI application on this linux machine, from my windows workstation! How to to that?

Most linux use X window system for GUI display, so does debian. X uses a client-server moduel through network. linux applications running on linux are client, your workstation(keyboard, mouse, screen) are the server - they provide service to applications.

So all we need are:

* X server
* client
* connection between X server and client

## X server
Most \*nix shiped with X server, there are many X server implementations for windows too. Such as [xming(oos)](http://sourceforge.net/projects/xming/) and x-win32(commerical).  
I choose xming.  
Download and install xming. start Xming by just click the Xming icon.
## client
Applications I'd like to run are already installed on linux machine.
## connection between X server and client
putty is a widely used ssh client on windows, it can be used to forward X Widnow System application over your ssh connection.

![putty config X11](http://img.bianbian.me/blog/201209/putty-config-x11.png)  

after login to your linux, check if X forward works fine.  

	bianbian@server:~$ echo $DISPLAY
	localhost:10.0

If this works, just run the application from shell! :)  

![xterm running from windows](http://img.bianbian.me/blog/201209/xterm-running-from-windows.png)

But if it doesn't work...  
check if ``X11Forwarding yes`` specified in ``/etc/ssh/sshd_config`` and if xauth application installed on linux.. fix problems and restart sshd if necessary, re-ssh to linux and make sure the ``DISPLAY`` variable is set properly.

Ref:

* [Using X11 forwarding in SSH](http://the.earth.li/~sgtatham/putty/0.62/htmldoc/Chapter3.html#using-x-forwarding)
* [How to forward X over SSH from Ubuntu machine?](http://unix.stackexchange.com/questions/12755/how-to-forward-x-over-ssh-from-ubuntu-machine)
