--- 
layout: post
title: java regular expression sample
category: tech
tags: 
- java
- regular expression
- sample
---
## Check if a string is number

	public boolean isNumeric(String str) {
		Pattern pattern = Pattern.compile("[0-9]*");
		Matcher isNum = pattern.matcher(str);
		return isNum.matches();
	}
