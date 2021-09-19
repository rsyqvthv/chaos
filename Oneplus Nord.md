# 安装 Magisk

## 准备

- 首先连接线用原装的.
- 打开developer模式
- [Releases · topjohnwu/Magisk](https://github.com/topjohnwu/Magisk/releases)
	- 下载magisk和magisk manager

## 确认A/B盘和system_as_root

- 确认是否a/b盘和系统为根

A/B partitions.
If your device is A/B, then your device is also certainly using system-as-root.

`adb shell getprop ro.build.ab_update`

- 如果不是a/b盘, 需要确认是否系统为根

whether you are using system-as-root on a non-A/B device, use a terminal to check with this command:

`adb shell getprop ro.build.system_root_image`

- 如果不是系统为根, 那么无法使用magisk.

what's system-as-root? [via](https://twitter.com/topjohnwu/status/1174392826278248448), [via](https://source.android.com/devices/bootloader/system-as-root)


## oem unlock

- developer options > allow oem unlock
- remove pin lock etc.
- reboot to fast boot
- `fastboot oem unlock` and accept. **wipe user data**


## 不刷入recovery的方式安装


- download twrp [via](https://forum.xda-developers.com/oneplus-nord/development/recovery-unofficial-twrp-oneplus-nord-t4142149)
- `fastboot boot TWRP.img`

其他安装方式: 

> [Installation | Magisk](https://topjohnwu.github.io/Magisk/install.html)

## Magisk OTA 升级

[OTA Upgrade Guides | Magisk](https://topjohnwu.github.io/Magisk/ota.html)

- 在magisk manager中, uninstall magisk, 不要重启
- 安装更新, 不要重启.
- 在magisk manager中安装magisk, 到另外一个盘.
- 重启.

 #question 遇到问题, 侦测到bootlock unlocked, 然后就只能完全升级.


# 安装 busy box
[[Help] Installing Busybox : Magisk](https://www.reddit.com/r/Magisk/comments/6pv0oe/help_installing_busybox/)

- 在magisk中安装 busybox for Android

# hosts

[[Magisk][Module][Deprecated] Unified Hosts Adblocker](https://forum.xda-developers.com/apps/magisk/magisk-unified-hosts-adblocker-t3559019)

- 简单的说就是使用adaway.

这里我遇到了启动非常慢的问题.
开始以为是hosts改变的原因, 后来发现是luckypatcher相关

卸载patched playstore重启, 然后再安装patched playstore就好了.


