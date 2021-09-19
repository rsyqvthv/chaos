# Google Pixel 5 使用

## 问题汇总

- 按键有些难按, 相比oneplus系列来说. 但好处是不容易误碰.
- [Google Pixel 5 | XDA Developers Forums](https://forum.xda-developers.com/c/google-pixel-5.11335/)
- [如何识别pixel的外观](https://support.google.com/pixelphone/answer/7157629?hl=en-GB)
- [了解pixel 5 的设备型号model](https://www.wesolveall.com/how-to-identify-your-google-pixel-phone-model), 盒子上和机身背面写的: GTT9Q, 属于：主要在*英国*、欧盟、加拿大、澳大利亚、*台湾*和新加坡发售，不支持 mmWave [via](https://zhuanlan.zhihu.com/p/328468270)
- build number: RQ2A.210405.005
- [Google提供的镜像](https://developers.google.com/android/images#redfin): 查询RQ2A和pixel 5 的交集
- 手机升级, 备份都需要将手机锁屏取消, 切记.
- 在root后, 回复数据的期间, 发现一些google软件无法使用了, 比如相机和录音. photos也产生了诡异的退出. 于是只好重新reset再来一次.

## Google提供的数据转移

- reset后, 尝试使用copy data, 从旧手机中copy数据使用了不到10分钟, 之后是getting your phone ready, 大概2分总左右.
- 其实上面的步骤只是转移了call logs 和 accounts, 以及程序列表, 在所谓的数据转移完成后, 会有一个从市场安装程序的过程, 这些程序并没有以前的数据, 都需要重新设置. 而那些不再市场的app都不会安装.

## 配置adb环境

> [免 root 玩转 Android 设备：如何从零开始使用 adb - 少数派](https://sspai.com/post/57427)

## 解锁bootloader

好处: Pixel 设备不会因为解锁 Bootloader 或 root 操作丢失保修资格，也不会因此失去 Widevine L1 数字版权认证而无法观看 Netflix 高清视频，相反，保证拥有一个已解锁状态的 Bootloader 甚至可以方便我们在设备变砖的情况下自行刷入工厂镜像进行修复。

为 Pixel 5 解锁 Bootloader 的方法很简单：

1. 在手机开机状态下，启用开发者选项 并勾选「允许 USB 调试」和「允许 OEM 解锁」，后者需要联网才能开启
2. 然后将手机通过数据线连接至电脑，保证 ADB 环境配置正确 的前提下，启动电脑端的命令行窗口
3. 在命令行窗口中输入 `adb reboot bootloader` 并回车执行，等待手机重启至 Bootloader 界面。注意，在此期间手机上会出现 USB 调试权限申请弹窗，记得及时授予
4. 手机处在 Bootloader 界面后，继续在电脑端命令行窗口中输入 `fastboot flashing unlock`并回车执行，此时手机端会出现解锁确认画面
5. 使用手机音量按键将屏幕选项切换至「解锁」，然后点击电源键确认
6. 等待手机开机

## Root

到底是原生还是第三方rom? 由于pixel还算是新机, 在配套工具还不完善且对第三方rom不了解的时候, 先停留在stock rom上吧. 

## 安装magisk

>  [No.3 使用 Magisk root 设备](https://zhuanlan.zhihu.com/p/328468270)

- 下载最新版的rom, [Google提供的镜像](https://developers.google.com/android/images#redfin): 查询RQ2A和pixel 5 的交集. 

- 解压image-redfin-rq2a.210405.005.zip中的boot.img

- 将这个文件存入手机中:
  `adb push boot.img "/sdcard/download/"`

- 下载最新的 Canary 版本 [Magisk Manager](https://raw.githubusercontent.com/topjohnwu/magisk_files/canary/app-debug.apk)

- 使用adb命令安装他

  `adb install app-debug.apk`
  
- 打开 Magisk Manager，保证手机已经能够连接到 Wi-Fi 网络（不建议此时插入国内 SIM 卡），依次选则 Magisk 一栏中的 **Install > Select and Patch a File**

- 找到我们放入手机存储中的 **boot.img** 文件并执行破解，破解完成会在 Download 目录下生成一个名为 **magisk_patched.img** 的文件，此时可以退出 Magisk Manager

- 将magisk_patched.img其传输至电脑备用

- `adb reboot bootloader` 

- 在命令行工具中输入 `fastboot boot`（有空格），**先不要回车**，把上面的 **magisk_patched.img** 文件直接拖入命令行窗口，然后回车执行，手机会自动开机 (数据不会丢失)

- 开机后我们就已经拥有临时的 Magisk 框架和 Magisk root 了，保险起见，这里依然建议大家在开机后打开 Magisk Manger 并手动执行一次安装。安装方式选择 **Install > Direct Install (Recommanded)** 就好，安装完成后再重启一次即可。

- 这里我遇到了触屏没有反应的情况, If your phone is frozen with the screen on, hold down the power button for about 30 seconds to restart. [via](https://support.google.com/pixelphone/answer/6377386?hl=en-GB), 硬重启解决.

> 延伸阅读: 
>
> [Magisk - The Magic Mask for Android | XDA Developers Forums](https://forum.xda-developers.com/t/magisk-the-magic-mask-for-android.3473445/)
>
> [Magisk and MagiskHide Installation and Troubleshooting](https://didgeridoohan.com/magisk/HomePage)
>
> [Issues · topjohnwu/Magisk](https://github.com/topjohnwu/Magisk/issues)

### GSF ID 注册(未进行)

> [应用商店里搜不到 Netflix？你可能遗漏了这一步 | 一日一技 - 少数派](https://sspai.com/post/55536)

GSF 是 *Google* Service Framework 的缩写，每台 Android 设备在连接到 *Google* Play 服务的同时都会获得一个与当前系统和 *Google* 账号配套的 GSF ID。**这个 ID 是我们手动解锁 Play 保护机制认证的关键**，获取它的方式有两种。

如果你有一定的玩机经验，在保证设备开启 USB 调试且电脑端环境配置正确的前提下，可以连接手机到电脑然后通过以下命令获取 GSF ID：

```
adb root
adb shell 'sqlite3 /data/data/com.google.android.gsf/databases/gservices.db "select * from main where name = \"android_id\";"'
```

### Magisk Hide

- 打开 Magisk Manager，点击主界面右上角的齿轮图标进入设置界面，然后找到并开启 MagiskHide 功能
- 随后在「超级用户」界面（Magisk 主界面下方第二个「盾牌」图标）顶部就会出现 MagiskHide 功能入口
- 进入 MagiskHide 界面后，点击右下角的放大镜图标进入索引
- 这里我们先勾选上 Show system apps 选项，然后分别找到 Google Play Store、Google Play services 和 Google Services framework 并勾选右侧的开关进行隐藏.
- 注意点开折叠将所有的子项全部勾选.
- 完成后退出 Magisk Manager，清除 Play 应用商店的数据后重启手机即可（你也可以在清除数据后进行一次 GSF ID 注册）。

### 在Magisk中修复SafetyNet硬件认证的完整指南

> [How to Fix SafetyNet Hardware Attestation (Universal SafetyNet Fix)](https://www.thecustomdroid.com/fix-safetynet-hardware-attestation-guide/)

启用MagiskHide并通过基本证明. 

- 首先为“ **Google** Play服务”下列出的所有服务打开MagiskHide 。
- 完成上述操作后，请在Magisk Manager中按“检查SafetyNet”，并验证您的设备已通过基本认证。
- 果您的设备运行的是自定义ROM，并且无法通过基本的SafetyNet认证，则可能需要切换到另一个ROM。

确保设备通过基本认证后，下一步就是在其上安装Universal SafetyNet Fix模块。

- 首先，从[Github官方*发布*页面](https://github.com/kdrag0n/safetynet-fix/releases)直接将最新版本的Universal SafetyNet Fix Magisk模块直接下载到您的设备上。
- 下载完成后，启动Magisk Manager应用程序，然后转到“模块”部分（底部导航栏中的最后一个图标）。按“从存储安装”按钮打开文件选择窗口。然后浏览设备存储并选择模块的ZIP文件（例如，*safetynet-fix-v1.1.1.zip*）。
- Magisk Manager将立即开始在您的设备上安装Universal SafetyNet Fix模块。安装成功后，请按屏幕底部的“重新启动”按钮。
- 该模块以“一劳永逸”的方式工作，因此您无需进行任何配置。重新启动后，请在Magisk Manager应用程序中重新检查SafetyNet。
- 之后测试通过.

如果显示evalType是basic, 但仍然没有通过cts认证, 那么可能需要安装MagiskHide Props Config. [详情这里](https://www.thecustomdroid.com/fix-safetynet-hardware-attestation-guide/#step-3-install-magiskhide-props-config-to-pass-cts-profile-if-required).

## 解决xposed问题

在上面初步通过了SafetyNet后, 只要升级了camera之类的系统程序, SafetyNet认证立刻失效, 且这些升级的系统程序都无法使用.

在[这里](https://didgeridoohan.com/magisk/MagiskHide)提到了xposed会暴露magisk, 当删除了EdXposed的扩展后, 这些系统程序就可以使用了. 





## 升级时保留数据

如果你想保留数据，可以在运行 flash-all.bat 前对其进行编辑，

>  编辑方法参考 [这篇文章](https://sspai.com/post/40545) 中「修改 flash-all 脚本」一节
>
> [谷歌Pixel系列手机每月更新无痛刷机技巧 - 知乎](https://zhuanlan.zhihu.com/p/65145687)

下载完整版镜像后, 解压其中的flash-all.bat文件. 

去掉 -w 参数. 

到末尾 `fastboot -w update image-xxxx-xxxxxxx.zip` 一处，将其修改为 `fastboot update image-xxxx-xxxxxxx.zip`，保存后的刷机脚本即为保留数据进行镜像刷写的升级脚本。

## 备份旧数据

首先, 关闭旧手机的网络, 只保留电话功能以防工作需要.

尝试使用 `adb pull "/sdcard/" .` 速度挺快, 但是遇到了[一个错误就整个停止了](https://android.stackexchange.com/questions/226573/adb-pull-stops-after-first-error).  

而且adb pull没有[文件标记](https://android.stackexchange.com/questions/40459/how-to-pull-only-newer-files-with-adb-pull-android-sdk-utility), 所以也无法只拷贝新的文件.

一些基于adb的建议:

- 压缩成一个tar文件后传输, 避免命名和路径的问题. `adb shell tar c sdcard > sdcard_backup.tar`, 但也有说tar在运行中有错误也不停止, 也没有进度, 让人很惶恐.
- [adebar](https://github.com/IzzySoft/Adebar) > [updated](https://codeberg.org/izzy/Adebar), based on Bash and Adb
- [adb-sync](https://github.com/google/adb-sync)
- [AdbSync](http://www.temblast.com/adbsync.htm), Win32 utility for syncing files to and from an Android device. [via](https://github.com/google/adb-sync/issues/44)
- [[GUIDE] Full Phone Backup without Unlock or Root | XDA Developers Forums](https://forum.xda-developers.com/t/guide-full-phone-backup-without-unlock-or-root.1420351/), 这里使用了`adb backup`, 进行全盘备份. [中文版本](https://www.jianshu.com/p/092c7c46866d), 注意: 这个命令并不是通用的，经我测试，可用率不是很高. 

所以只有使用笨办法, 使用windows拷贝. 他总是先要计算一下文件数量, 然后再拷贝, 速度像是成倍.

备份calllogs用这个: [SMS Backup & Restore - Apps on Google Play](https://play.google.com/store/apps/details?id=com.riteshsahu.SMSBackupRestore)

## 软件调教

### 调教pixel launcher

默认的launcher可调节的地方非常少, 尤其是那个search bar不能取消, 让人很难过. xda出品了 [Pixel Tweaks for Pixel 5 with Color Picker | XDA Developers Forums](https://forum.xda-developers.com/t/april-5-2021-pixel-tweaks-for-pixel-5-with-color-picker.4184067/), 用起来有些复杂.

### lucky patcher

[How to disable signature verification to install unsigned APK (Rooted device/VMOS) (Lucky Patcher)](https://www.andnixsh.com/2020/01/how-to-install-unsigned-apk-root-method.html)

### clip stack

需要adb执行三条代码: 

```
adb -d shell appops set com.catchingnow.tinyclipboardmanager SYSTEM_ALERT_WINDOW allow;
adb -d shell pm grant com.catchingnow.tinyclipboardmanager android.permission.READ_LOGS;
adb shell am force-stop com.catchingnow.tinyclipboardmanager;
```

### join

需要adb执行4条代码来访问clipboard

```
adb -d shell appops set com.joaomgcd.join SYSTEM_ALERT_WINDOW allow
adb shell pm grant com.joaomgcd.join android.permission.WRITE_SECURE_SETTINGS
adb shell pm grant com.joaomgcd.join android.permission.READ_LOGS
adb shell am force-stop com.joaomgcd.join
```





