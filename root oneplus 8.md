很长时间没有折腾手机了, 折腾了一下午, 下面是精要.

# 基本概念

- unlock loader
- 然后找到和手机相同版本的firmware, 下载取出其中的boot.img
- 使用magisk manager patch这个boot.img
- 使用fastboot刷入patched boot.img

# 下载

- [android driver](https://download.highonandroid.com/file/Drivers/UniversalAdbDriverSetup.msi)
- [fastboot.zip](https://download.highonandroid.com/file/Tools/fastboot.zip)
- [Magisk Manager Canary 2020 APK](https://download.highonandroid.com/file/Tools/Magisk/Canary/MagiskManagerCanary2020.apk.html) (For Android 10)
- [Payload unpacker](https://download.highonandroid.com/file/Tools/Payload/payload_dumper-win64.zip.html)
- 检查手机的firmware版本, 到[这里](https://www.oneplus.com/uk/support/softwareupgrade/details?code=PM1586920535300)下载同样的版本, 确保数字部分是一样的.

# unlock loader

- 电脑上安装android driver
- 手机链接电脑, 选择file transfer
- 手机上激活developer模式
- 取消oem保护
- 电脑端打开cmd
- 进入fastboot目录, 输入`adb devices`, 手机中确定. 将adb和手机联通. 并再次输入该命令确认手机在adb的列表中.
- `adb reboot bootloader` 进入手机fastboot模式
- `fastboot oem unlock` 解锁bookloader
- 这时在手机上会有一些选项, 按照需要使用音量和电源键选取.
- 之后手机重置并重启. 出现unlock画面.
- 等手机重启后需要重新初步设置, 并再次打开developer模式, 为后面的操作做好准备.

# patch

- 将下载的firmware(很大)的zip包中的payload.bin取出来
- 放到Payload unpacker中的input目录, 然后运行exe, 等待boot字符过去即可关闭窗口.
- 从output取出boot.img
- 将boot.img和magisk.apk拷贝到手机的download目录中
- 安装magisk, 注意这时需要联网.
- 然后在magisk后面选择install, next, select and patch file, 之后选中boot.img即可
- 将patched_boot.img拷贝到电脑的fastboot目录.

# root

- 其实就是将patched_boot.img刷入手机.
- `adb devices`
- `adb reboot bootloader`
- `fastboot flash boot magisk_patched.img`看到两个okay就算成功了
- `fastboot reboot` 重启手机.
- 等手机重启后, 检查magisk, status是normal就确定已经root了.



# 参考

- [How to Root OnePlus 8/OnePlus 8 Pro or any other OnePlus on Android 10! ](https://www.youtube.com/watch?v=UVABAEGRgew) 这个 Max Lee 介绍的不错, 提供的软件也很细致, 只是缺了一个unlock loader的步骤, 让我费了很大劲.
- [How to Unlock and Root the OnePlus 8 Pro - Appuals.com](https://appuals.com/how-to-unlock-and-root-the-oneplus-8-pro/)
- [ RollBack package to Android 10](https://techibee.in/download-android-11-for-oneplus-8-and-oneplus-8-pro/) 如果手机中的firmware比官方的给的高, 那么就在这里下载rollback包. 留意Na/IN/EU字母的匹配.