--- 
layout: post
title: change the boot up resloution of ubuntu
category: tech
tags: 
- linux
- ubuntu
---
## 1. edit grub config file

	sudo vi /etc/default/grub

change this line

	#GRUB_GFXMODE=640×480

to your own resloution, such as

	GRUB_GFXMODE=1366x768

## 2. edit another grub config file

	sudo vi /etc/grub.d/00_header

after this line:

	set gfxmode=${GRUB_GFXMODE}

add a line:
	set gfxpayload=keep

## 3. update grub

	sudo update-grub

