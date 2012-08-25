--- 
layout: post
tags: 
- IT
- Raspberry Pi
type: post
meta: 
  _edit_last: "1"
  _syntaxhighlighter_encoded: "1"
published: true
status: publish
title: samba on respbian
---
安装samba
[bash]sudo apt-get install samba samba-common-bin[/bash]
我们需要的smbpasswd命令,不是一个单独的安装包,它包含在samba-common-bin这个包里.

修改samba配置文件:
[bash]sudo vi /etc/samba/smb.conf[/bash]

把[text]# security = user[/text]前面的#去掉,改成[text]security = user[/text] 用配置文件里面的话:"security = user" is always a good idea.
再在这一行下面加一行:[text]client ntlmv2 auth = yes[/text] samba默认用NTLMv1验证,而win7是用NTLMv2验证,不加这行win7连不上samba.
在配置文件最后面加上要共享的目录:
[text]
[public]
    comment = Public Storage
    path = /home/shares/public
    valid users = @users
    force group = users
    create mask = 0660
    directory mask = 0771
    read only = no[/text]

添加samba用户
[bash]sudo smbpasswd -a username[/bash]
会让你输入两次密码,输进去就好啦.

重启samba:
[bash]sudo /etc/init.d/samba restart[/bash]
经验证[bash]sudo /etc/init.d/samba reload[/bash]是不行的.没仔细研究为神马.

在win7中打开\\raspberrypi-ip\public,输入刚才创建的用户/密码,就能看到共享的内容了:)
