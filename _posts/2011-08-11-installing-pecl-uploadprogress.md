--- 
layout: post
tags: 
- apache
- drupal
- IT
- php
- ubuntu
- uploadprogress
type: post
meta: 
  tagazine-media: a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";s:1:"0";s:6:"author";s:7:"2280877";s:7:"blog_id";s:7:"2203254";s:9:"mod_stamp";s:19:"2011-08-11 13:43:53";}
  jabber_published: "1313068582"
  _wpas_done_twitter: "1"
published: true
status: publish
title: Installing PECL uploadprogress
---
why do this: <a href="http://drupal.org/node/793262">http://drupal.org/node/793264</a>
OS: ubuntu-10.04.3-server

Install the PHP developer package for the version of PHP you're using. For example, in case of php5 run:
$ sudo apt-get install php5-dev php-pear

Configure uploadprogress extension to php
$sudo vi /etc/php5/apache2/conf.d/uploadprogress.ini
extension=uploadprogress.so

Install the PECL uploadprogress library:
$ sudo pecl install uploadprogress

Restart apache:
$ sudo service apache2 restart

Ref:<a href="http://drupal.org/node/793262">http://drupal.org/node/793262</a>
