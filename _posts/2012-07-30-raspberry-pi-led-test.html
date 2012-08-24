--- 
layout: post
tags: 
- IT
- Raspberry Pi
- test
type: post
meta: 
  _wp_old_slug: rpi-led-test
  _edit_last: "1"
  _syntaxhighlighter_encoded: "1"
published: true
status: publish
title: !binary |
  5qCR6I6T5rS+bGVk5a6e6aqM

---
其实还搞不太了解pi的gpio的电气特性,只知道gpio是直接跟BCM芯片连接,目前有多种语言能控制GPIO.
GPIO电压是3V3,拿来做个LED实验应该木问题.

所需器材:
<ul>
	<li>rpi一只(必须的啦~)</li>
	<li>面包板</li>
	<li>发光二极管一只</li>
	<li>220R电阻一只</li>
	<li>杜邦线若干</li>
</ul>

思路:控制GPIO电压高低(3V3或0),就能点亮LED啦,保险起见,加个电阻限流.
电路图:
<img src="http://img.bianbian.me/blog/201207/ledtest.png" alt="电路图" />

搞起来~
下载最新的python gpio驱动,http://code.google.com/p/raspberry-gpio-python/downloads/list
选择python-rpi.gpio_0.3.1a-1_armhf.deb
安装:[bash]dpkg -i python-rpi.gpio_0.3.1a-1_armhf.deb[/bash]

python程序 testled.py:
[python]import RPi.GPIO as GPIO
import time

# 这一步是必须的哟,应该是从0.3版本添加的新特性
GPIO.setmode(GPIO.BOARD)
GPIO.setup(11, GPIO.OUT)

while True :
  print &quot;set output low&quot;
  GPIO.output(11, GPIO.LOW)
  time.sleep(1)
  print &quot;set output high&quot;
  GPIO.output(11, GPIO.HIGH)
  time.sleep(1)
[/python]
跑起来:[bash]sudo python testled.py[/bash]

效果:
<img src="http://img.bianbian.me/blog/201207/rpi-and-breadboard.png" alt="rpi和面包板" />
<img src="http://img.bianbian.me/blog/201207/breadboard.png" alt="面包板接线" />
