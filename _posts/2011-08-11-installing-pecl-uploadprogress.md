--- 
layout: post
title: installing PECL uploadprogress
category: tech
tags: 
- drupal
- uploadprogress
- linux
- ubuntu
---
why do this: <http://drupal.org/node/793262>

OS: ubuntu-10.04.3-server

Install the PHP developer package for the version of PHP you're using. For example, in case of php5 run:

	$ sudo apt-get install php5-dev php-pear

Configure uploadprogress extension to php

	$sudo vi /etc/php5/apache2/conf.d/uploadprogress.ini

add this line:

	extension=uploadprogress.so

Install the PECL uploadprogress library:

	$ sudo pecl install uploadprogress

Restart apache:

	$ sudo service apache2 restart

Ref:  
<http://drupal.org/node/793262>
