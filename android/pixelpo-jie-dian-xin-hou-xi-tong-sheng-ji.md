---
description: Pixel破解电信后系统升级
---

# Pixel破解电信后系统升级

## Pixel破解电信后系统升级

 注意，此法可适合升级版本,N to N或O，或者O to O.  
 不能O to N 降级，会卡Google 动画不开机的。  
 1.下载最新的的Android版本线刷包  
[ https://developers.google.cn/android/images\#sailfish](https://developers.google.cn/android/images#sailfish)  
 2.解压线刷包，并将我补丁包\[url=\]Flash-nomodem-nowipe.zip\[/url\]解压到同一个目录；  
 3. 对于非OPP3版的factory Image，需要将Flash all的版本名信息合并到我flash-nomodem-nowipe.bat，OPP3可以跳过这步  
 4. 双击运行flash-nomodem-nowipe.bat  
 ![DIR.png](http://attachments.gfan.net.cn/forum/201706/26/194747r4lqfzdilrvd3ry3.png.thumb.jpg)  
 其实原理很简单：  
 就是改掉Factory Image里面的Flashall.bat线刷脚本，  
 1 屏蔽FlashAll.bat里面，flash radio...，避免破解modem被覆盖  
 2 删掉FlashAll.bat里面，flash update其中的-w字样，避免破解记录被覆盖  
 3 删掉image包里面Android.txt的自检要求  
 4 删掉image包里面userdata.img，避免破解记录被覆盖  
 必要时， image包里面modem.img也删了。  
 然后运行修改好的bat好了。  
 运行flash-nomodem-nowipe.bat，自动完成步骤3，4并刷机  
 有经验的可以对比flash-all.bat.txt原文差异，按此来改其他刷机包。  
 ![Diff.png](http://attachments.gfan.net.cn/forum/201706/26/1947468qot9tr86a666qa9.png.thumb.jpg)

## Refs

[\[实用教程\] Pixel电信4G破解完成-之后的系统升级，不丢电信破解线刷](http://bbs.gfan.com/android-9165559-1-1.html)

