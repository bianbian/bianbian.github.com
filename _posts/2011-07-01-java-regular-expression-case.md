--- 
layout: post
title: Java Regular Expression Case
category: tech
tags: 
- Java
- Regular Expression
---
## Check if a string is number

	public boolean isNumeric(String str) {
		Pattern pattern = Pattern.compile("[0-9]*");
		Matcher isNum = pattern.matcher(str);
		return isNum.matches();
	}
