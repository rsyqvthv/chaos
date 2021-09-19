首先遇到的问题是链接usb手机没有反应.

先下载了oneplus one的driver, [Download OnePlus USB Drivers For All Models | Root My Device](https://rootmydevice.com/usb-drivers/download-oneplus-usb-drivers/)

查毒有一些问题? [VirusTotal](https://www.virustotal.com/gui/file/01cef3f06745d6f505c254eba4e1fe79821f922028613da1d4a4a7e3d230aaa8/detection) 

- This is the official usb driver for oneplus 3 phone, downloaded from oneplus website…

- 但还是冒险尝试安装.
- 但是安装的时候等待了非常长的时间.
- 仔细看到下面是2015年的driver, 是不是太老旧? 
- 取消倒是挺快.

所以只好冒险尝试通过xplore将文件考到手机中然后操作.

在拷贝的过程里, 我看到了很多地方提及了安装Media Feature Pack for N and KN versions of Windows 10, 但我记得我已经安装过, 不过我试试再安装一次.

- [Download Media Feature Pack for N and KN versions of Windows 10 from Official Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=48231) 同时下载86和64版.
- x86 的顺利安装了
- x64的居然说不适合我的电脑.

后来尝试将usb线插到电脑背后, 居然就可以了.

> 在连接线不通的情况下, 除了更新driver, 还可以换个插口.

- 也不知道是机身usb不行
- 还是刚安装的x86 media pack起作用了.

通过连线将rom拷贝到手机中, 超级快.

尝试在twrp中使用adb sideload, 结果提示: `this pack for oneplus, this is a 'A0001'`

后来找到专门讨论这个事情的帖子, 将oos 9 安装到oneplus one中, [OxygenOS 2.1.4 for the OnePlus One - OnePlus Community](https://forums.oneplus.com/threads/oxygenos-2-1-4-for-the-oneplus-one.425544/)

- 搞了几下不知道是不是bootload unlock了, 
- 使用`fastboot oem device-info`来检查一下, 显示`Device unlocked: true`, 原来早期版本的oneplus并没有那么丑陋的启动unlocked提示.
- 按照指引并未启动到原生recovery中, 幸好系统还可以进去.
- 从系统的高级启动菜单中进入recovery成功.
- 然后先清除data和cache
- 再选择本地安装.
- 之后重启就可以了.

启动画面不是通常的白点红圈. 感觉有些诡异. 但最终还是进入系统了. 

> 学到了一个东西, 刷oneplus官方的rom, 还是要用原生的recovery, 而不能使用twrp, 会造成很严重的后果. 

但最后还有个疑问, bootlock锁上了吗?

- 进入系统激活高级启动菜单后
- 进入bootload mode
- `fastboot oem device-info` 显示bootload是解开的状态
- 使用命令`fastboot oem lock`
- 成功锁住.
