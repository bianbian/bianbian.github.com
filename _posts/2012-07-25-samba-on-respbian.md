--- 
layout: post
title: samba on respbian
category: tech
tags: 
- linux
- Raspberry Pi
---
## 安装samba

	sudo apt-get install samba samba-common-bin

我们需要的smbpasswd命令,不是一个单独的安装包,它包含在samba-common-bin这个包里.

## 修改samba配置文件:

	sudo vi /etc/samba/smb.conf

把`# security = user`前面的#去掉,改成`security = user` 用配置文件里面的话:"security = user" is always a good idea.  
再在这一行下面加一行:`client ntlmv2 auth = yes` samba默认用NTLMv1验证,而win7是用NTLMv2验证,不加这行win7连不上samba.
在配置文件最后面加上要共享的目录:

	[public]
	    comment = Public Storage
	    path = /home/shares/public
	    valid users = @users
	    force group = users
	    create mask = 0660
	    directory mask = 0771
	    read only = no

## 添加samba用户

	sudo smbpasswd -a username

会让你输入两次密码,输进去就好啦.

## 重启samba:

	sudo /etc/init.d/samba restart

经验证`sudo /etc/init.d/samba reload`是不行的.没仔细研究为神马.

在win7中打开\\raspberrypi-ip\public,输入刚才创建的用户/密码,就能看到共享的内容了:)
