---
description: Pixel破解电信
---

# Pixel破解电信

## 0. Notes
- 欧版 Bootloader 可以直接解锁，美版里V版不行，需要找奸商解锁。
- 其实只要 1）解锁 Bootloader，2）按照 ex. 刷入 modemst，就可以完成电信破解（已测试 Android 8.1）。
- 暂时不清楚 modemst 是否是各版本通用的。

## 1. 解锁 Bootloader
解锁教程：http://bbs.gfan.com/android-8404948-1-1.html

platform-tools 地址： https://dl.google.com/android/repository/platform-tools-latest-windows.zip

简述：开发者模式中开启 OEM 解锁后，重启手机进入 bootloader 模式，在电脑端运行 ```fastboot oem unlock```

## 2. 刷入 7.1.1 原厂镜像
原厂镜像(v7.1.1)地址： https://dl.google.com/dl/android/aosp/sailfish-nof27b-factory-5a8a6e11.zip

简述：
- 下载原厂镜像(v7.1.1)文件，解压后进入文件夹
- 手机进入 bootloader 模式
- 运行 flash-all.bat (Win) 刷入原厂镜像

## 3. 刷入修改版镜像文件，并刷入 Android 8.1 的 Radio(基带) & Modem
修改版镜像文件链接: https://pan.baidu.com/s/1nvvELIh 密码: 6bvk

原厂镜像(v8.1)地址：https://dl.google.com/dl/android/aosp/sailfish-opm1.171019.016-factory-8a6591cc.zip

简述：
- 下载修改版镜像文件
- 手机进入 bootloader 模式
- 刷入修改版ROM：```fastboot -w update image-sailfish-nof27b_root.zip```
- 下载原厂镜像(v8.1)文件，解压后进入文件夹
- 从```image-sailfish-opm1.171019.016.zip```中解压出```modem.img```
- 手机进入 bootloader 模式
- 刷入新版基带：```fastboot flash radio radio-sailfish-8996-130091-1710201747.img```
- 刷入新版Modem：```fastboot flash modem modem.img```

## 4. 开启 diag 并替换 carrier_policy.xml
carrier_policy.xml 链接: https://pan.baidu.com/s/1nvvELIh 密码: 6bvk

简述：
- 进入 shell ```adb shell```
- 开启 su (root 权限) ```su```
- 开启 diag ```setprop sys.usb.config diag,adb```
- 运行 QPST 的 EST Explorer
- 替换 /policyman 中的 carrier_policy.xml
- 重启手机确定 LTE 是否生效

## 5. 备份 modemst
简述：
- 进入 shell 后获取 root 权限：```adb shell``` & ```su```
- 备份 modemst
```
dd if=/dev/block/platform/soc/624000.ufshc/by-name/modemst1 of=/sdcard/modemst1.img
dd if=/dev/block/platform/soc/624000.ufshc/by-name/modemst2 of=/sdcard/modemst2.img
```
- 将 modemst1.img、modemst2.img 复制到本地

## 6. 刷入原厂ROM（v8.1）
Flash-nomodem-nowipe.zip：http://bbs.gfan.com/android-9165559-1-1.html

简述：
- 下载 Flash-nomodem-nowipe.zip 并解压在原厂镜像文件夹中（sailfish-opm1.171019.016）
- 解压最新版 platform-tools 到原厂镜像文件夹中
- 修改 flash-nomodem-nowipe.bat 如下并运行

```
@ECHO OFF
:: Copyright 2012 The Android Open Source Project
::
:: Licensed under the Apache License, Version 2.0 (the "License");
:: you may not use this file except in compliance with the License.
:: You may obtain a copy of the License at
::
::      http://www.apache.org/licenses/LICENSE-2.0
::
:: Unless required by applicable law or agreed to in writing, software
:: distributed under the License is distributed on an "AS IS" BASIS,
:: WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
:: See the License for the specific language governing permissions and
:: limitations under the License.

:: remove modem.img, userdata.img and blink requirement check
for %%a in (image*.zip) do 7z d %%a userdata.img
for %%a in (image*.zip) do 7z d %%a modem.img
for %%a in (image*.zip) do 7z u %%a android-info.txt

adb reboot bootloader
rename flash-all.bat flash-all.bat.save

PATH=%PATH%;"%SYSTEMROOT%\System32"
fastboot flash bootloader bootloader-sailfish-8996-012001-1711291800.img
fastboot reboot-bootloader
ping -n 5 127.0.0.1 >nul
::fastboot flash radio radio-sailfish-8996-130091-1710201747.img
::fastboot reboot-bootloader
::ping -n 5 127.0.0.1 >nul
fastboot update image-sailfish-opm1.171019.016.zip

echo Press any key to exit...
pause >nul
exit
```

- 之后系统会启动失败，根据提示来一发 factory data reset 就可以了

## ex. 恢复 modemst
```
fastboot flash modemst1 modemst1.img
fastboot flash modemst2 modemst2.img
```

## Note
- 其实这里就是刷入原厂的 bootloader 和 image，只不过删除了 image 中的 modem.img 和 userdata.img。
- 因为本流程使用了最新的基带，理论上不需要修改 android-info.txt。
- 据说不可以 factory reset，会掉 carrier_policy，不过我猜恢复一下 modemst 就可以复原。
- 备份 modemst 是因为有的人在 Android 8.1 下破解失效

# Refs

[coeusite/Pixel\_CT4G](https://gist.github.com/coeusite/86f6318c13c5bc15aef13345f1bb3ed4)

