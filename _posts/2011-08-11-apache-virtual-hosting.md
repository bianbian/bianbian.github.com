--- 
layout: post
title: apache virtual hosting
category: tech
tags: 
- apache
- ubuntu
---
Environment: ubuntu-10.04.3-server, apache2

my domain config:

A Record: `aws->ip`  
C NAME  : `www->aws`  
have a site on apache2

by default, you can access the site through www, aws, ip. Since www is the domain I want to use, I want to disable the aws and ip way, or redirect them to www.

so I use NameVirtualHost and RedirectMatch to do that:

make www site a NameVirtualHost, add another NameVirtualHost and make it as primary server, redirect all request on this virtual host to www.

	<VirtualHost>
		*:80
		# Redirect all requests other than known host to blog.bianbian.me
		RedirectMatch 301 (.*)$ http://blog.bianbian.me$1
	</VirtualHost>
