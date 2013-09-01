---
layout: post
title: 用Magic Number判断文件类型
category: tech
tags: file type, unicode
---
Magic Number是指文件头部的几个字节，通常用十六进制表示，可用来判断文件类型。比如Java class文件的CAFEBABE，linux shell script的“shebang”（#!, 23 21)。

UTF-16，UTF-32编码文件的BOM，也可以作为Magic Number，用来判断文件编码。UTF-8编码的文件不一定包含BOM，不能用这种办法判断。

各种Unicode编码的BOM如下表：

<table class="compat-table">
  <tr>
    <th>Bytes</th>
    <th>Encoding Form</th>
  </tr>
  <tr>
    <td>00 00 FE FF</td>
    <td>UTF-32, big-endian</td>
  </tr>
  <tr>
    <td>FF FE 00 00</td>
    <td>UTF-32, little-endian</td>
  </tr>
  <tr>
    <td>FE FF</td>
    <td>UTF-16, big-endian</td>
  </tr>
  <tr>
    <td>FF FE</td>
    <td>UTF-16, little-endian</td>
  </tr>
  <tr>
    <td>EF BB BF</td>
    <td>UTF-8</td>
  </tr>
</table>

在程序中，只要读取文件头部几个字节，转换成十六进制，然后跟已知的Magic Number比较，就可以知道文件类型了。

顺便贴个Java字节转十六进制的代码：

{% gist 6250138 %}

参考：
- [File format](http://en.wikipedia.org/wiki/File_format)
- [Magic number]
- [UTF-8, UTF-16, UTF-32 & BOM](http://www.unicode.org/faq/utf_bom.html#BOM)

[Magic number]: http://en.wikipedia.org/wiki/Magic_number_(programming)

