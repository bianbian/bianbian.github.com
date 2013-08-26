--- 
layout: post
title: 搶到淘寶二級域名
category: tech
tags: 
- linux
- bash
- taobao
- domain
---
自從痛失.org域名以來,對域名的事情很是在意. 這次是淘寶的二級域名.

觀察了一下,這域名已經換過一次主人了, 讓我看到一絲希望. 先前的使用者不知道為什麼原因不用了, 現在是另一家店, 經營不善, 好評率是70%, 這種情況基本沒法在淘寶經營下去的. 呵呵.

而域名釋放狀態下, 訪問這域名的話, 會302到另外一個頁面去; 正常情況下是200.

於是寫了個腳本做監測, 如果遇到302, 就給自己手機發郵件, 手機會有短信提示.

	#!/bin/sh
	url="http://ooxx.taobao.com"

	response_code=`curl -o /dev/null -s -w %{response_code} $url`

	if [ "$response_code" -eq "200" ]; then
	    echo "ooxx.taobao.com works fine~"
	elif [ "$response_code" -eq "302" ]; then
	    echo "ooxx.taobao.com is available!"
	    echo "Plz check taobao.com for detail" | mail -s "ooxx.taobao.com is available!" "13900008888@139.com"
	else
	    echo "There's some problem with ooxx.taobao.com!"
	    echo "Plz check taobao.com for detail" | mail -s "There's some problem with ooxx.taobao.com!" "13900008888@139.com"
	fi

昨天晚上, 從廚房回來, 看到手機在閃, 看了一下, 是域名監測短信! 趕緊上淘寶看了一下, 這域名釋放出來了!

麻利的, 登錄, 搶占! hiahia:D
