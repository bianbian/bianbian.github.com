--- 
layout: post
tags: 
- Raspberry Pi
type: post
meta: 
  _edit_last: "1"
  _syntaxhighlighter_encoded: "1"
published: true
status: publish
title: !binary |
  5pu05pS5bGludXjnlKjmiLflkI0=

---
raspbian系统是img形式的,这就意味着所有人装完系统后里面都是同样的东西.包括用户名,密码,密钥etc.

安全起见,这些东西都需要更新一下.密码和密钥比较简单.这里记录一下更改用户名.

因为默认用户pi已经加入了很多group,新建用户,再加入group的做法比较麻烦,所以采取重命名pi用户的办法.

主要涉及三个文件
<ul>
	<li>/etc/passwd 记录了用户名,uid,home,shell等信息.建议使用sudo vipw命令.找到pi开头的行,把pi改成newuser,/home/pi改成/home/newuser,并重命名相应目录.</li>
	<li>/etc/shadow 记录用户密码.建议使用sudo vipw -s命令.把pi行的pi改成newuser.</li>
	<li>/etc/group 记录组信息.建议使用sudo vigr命令.里面记录了pi已经加入了好多组,还有一个pi组,把这些pi都替换成newuser.</li>
</ul>
重新登录就可以了.

以上是手动更改文件的做法,以下是正规做法(未测试):
[bash]usermod -l username pi
usermod -md /home/newuser newuser
groupmod -n newuser pi[/bash]