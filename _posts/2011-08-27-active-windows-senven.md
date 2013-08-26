--- 
layout: post
title: 刷BIOS激活Win7
category: tech
tags: 
- windows 7
- bios
- oem
---
要激活Windows 7,靠淘宝上卖KEY的是不靠谱的,要激活要么从正规渠道买KEY,要么再想办法.

办法就是用OEM Licence.

## 原理

OEM Licence的原理就是在MS许可的机器上装MS许可的OS(SLP: Microsoft Software Licensing and Protection)  
许可的信息是存在BIOS的某个东西,叫做SLIC: Software Licensing Description Table, 里面有公钥啊母钥啊之类的东西.  
许可的OS里也有个东西,Certificate和 KEY,里面有母钥啊公钥啊之类的东西,和BIOS里的信息配对.  
有了这两样东西,就可以用上OEM Licence的Win7啦~

OS里的这两样东西比较好搞,找到这两个文件,然后导入到系统里就OK了.

第一样东西相对来说比较难搞,需要自己制作BIOS,然后再刷BIOS.刷BIOS有风险,万一失败,电脑就变砖了,要去找客服.

下面说下我是怎么做的:

## 1.首先看下自己电脑BIOS的厂商,开机的时候能看到,我的是Phoenix  

## 2.下载BIOS厂牌相应的工具,不同厂牌的BIOS制作工具是不一样的

<http://www.box.net/shared/270l4iyhigu995l7857o>

* phoenixtool190.zip制作BIOS的工具
* RwV1.4.7.rar制作BIOS的时候,需要一个跟你系统有关的RW文件,用这个工具来生成RW文件.
* SLIC 2.1 BINS 1-31-2011.7z这里面有BIOS里要的SLIC(里面有公钥母钥等等东西),OS里要的母钥公钥.:D
* SLIC_ToolKit_V3.2.rar验证BIOS里SLIC版本,要2.1版才能激活win7(v1用来激活XP,v2用来激活Vista)

都解压&amp;安装.

## 3.先用SLIC_ToolKit看一下你的SLIC版本,如果你的是2.1版,那恭喜你,你不用刷BIOS啦!直接跳过这步!

如果不是2.1,那么恭喜你,你要刷BIOS!

![SLIC ToolKit](http://img.bianbian.me/blog/201108/slic_toolkit.png)

先制作有SLIC V2.1的BIOS

从Acer网站上下载BIOS,解压,在DOS文件夹里有个JE40D111.wph,就是它了.(还有Winflash32,Winflash64文件夹,这两个里面的BIOS都被分装在exe文件里了,咱不管他)

![Acer BIOS](http://img.bianbian.me/blog/201108/acer_bios.png)

打开RW-Everything,制作RW文件

![RW-Everything](http://img.bianbian.me/blog/201108/rw.png)

点那个钮保存rw文件

打开PhoenixTool

![PhoenixTool](http://img.bianbian.me/blog/201108/phoenixTool.png)

Original BIOS那里选择刚才的JE40D111.wph文件  
RW file选择刚才制作的rw文件  
SLIC File选择 SLIC 2.1 BINSACER2.1 BIN &amp; 2.1 CertificateAcer\[ACRSYS-ACRPRDCT-ANNI\]2.1.BIN  
点击Go按钮,包含SLIC2.1的BIOS文件就制作好啦.  
文件存在跟JE40D111.wph相同目录下,文件名是JE40D111_SLIC.wph.

我们把原来的JE40D111.wph改为另外的名字,把JE40D111_SLIC.wph改名为JE40D111.wph

## 4.刷BIOS

要在DOS下刷BIOS,相对比较安全.windows下的cmd是不行的..  
如果你没有dos,那么用usboot-v1.70这个工具,找个U盘做一个  
到dos里,执行Acer bios文件夹里的bios.bat,过一会,bios就刷好了

## 5.重启,进入windows7.

以管理员身份运行cmd.exe

	slmgr.vbs -ilc "磁盘位置SLIC 2.1 BINSACER2.1 BIN & 2.1 Certificate~Certificate~ACER-ACRSYS-2.1.XRM-MS"

提示证书导入成功  
到这里找到对应你电脑品牌,你OS版本的KEY  
<http://forums.mydigitallife.info/showthread.php?t=10370>  
然后在cmd里运行

	slmgr.vbs -ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX

提示KEY导入成功  
好了,windows7 OEM被激活了,快到电脑属性里面看看吧:-)  
累死我了,吃饭去...
