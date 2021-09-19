# 关于Magisk的问题

## [Magisk 是如何工作的？](https://sspai.com/post/53043)

Xposed 通过劫持 Android 系统的 zygote 进程来加载自定义功能，这就像是半路截杀，在应用运行之前就已经将我们需要的自定义内容强加在了系统进程当中。

Magisk 则另辟蹊径，通过挂载一个与系统文件相隔离的文件系统来加载自定义内容，所有改动在那个世界（Magisk 分区）里发生，在必要的时候却又可以被认为是（从系统分区的角度而言）没有发生过。

得益于独特的挂载机制，使用 Magisk 时我们可以有针对性地隐藏 root，甚至暂时隐藏 Magisk 本身。

![img](D:\documents\markdown\magisk\xposed diagram.png)

挂载系统的存在，也让 Magisk 拥有了多样的模块化生态系统。既然用了「开外挂」的实现方式，那不妨就多挂载一些额外的东西，字体、音效、驱动……甚至 Xposed 本身。

## 如何正确的安装 Magisk

> 所谓正确就是要建立原版boot.img的备份, 只有这样才能在ota升级后不用重新安装magisk

- 在电脑上配置好驱动和fastboot
- 并解开 Bootloader 锁 [via](https://oneplus.gadgethacks.com/how-to/unlock-bootloader-your-oneplus-6-0185473/)

如果你的设备有来自 [TWRP](https://twrp.me/Devices/) 的官方支持，只需在打开 USB 调试后将手机与电脑相连，然后打开电脑端的命令行窗口：

1. 执行 `adb reboot bootloader` 进入 Bootloader 界面
2. 执行 `fastboot boot TWRP.img` 进入临时 TWRP
3. 在 TWRP 中刷入你下载的 Magisk 安装包, 在安装的时候会看到他备份了boot image.

没有官方 TWRP 支持的设备安装 Magisk 的步骤要稍微复杂一些：

1. 从你的刷机包中提取当前固件的 **boot.img** 文件，将它传入到安装了 Magisk Manager 的手机中
2. 进入 Magisk Manager —— 安装（install）—— install —— 修补 boot 镜像文件
3. 然后选择传入的 boot.img 文件进行生成，并将生成后的 Patchedboot.img （姑且这么命名） 传输到电脑上。
4. 打开命令行窗口
5. 执行 `adb reboot bootloader` 进入 Bootloader 界面
6. 执行 `fastboot boot Patchedboot.img` 来加载生成后的 boot 分区文件获取**临时 root**
7. 此时进入系统，你会发现你已经成功安装了 Magisk（如果显示没有安装则为获取失败，请检查操作过程重新尝试），但这还不够，我们还得进入 Magisk Manager，选择安装（install）——install——Direct Install（直接安装）才能将临时 root 转换为永久 root。

这样做不光安装了magisk, 而且还备份了原始的boot.img. 为将来无缝安装ota做好了准备.

![09072020-064252](D:\documents\markdown\magisk\09072020-064252.png)

[三星](https://topjohnwu.github.io/Magisk/install.html#samsung-system-as-root)、[华为](https://topjohnwu.github.io/Magisk/install.html#huawei)等特殊机型的 Magisk 安装方法参见 Magisk 官方帮助文档。

安装完 Magisk 后，我们就可以通过 TWRP 或者 Magisk Manager 刷入获取到的模块了。模块的获取方式可以是 Magisk Manager 自带的模块仓库，也可以是其他第三方论坛（如酷安、XDA 等）。

## 卸载

卸载 Magisk 最为彻底的方式就是在 Magisk Manager 中点击「卸载」、「完全卸载」，应用会自动下载刷完 uninstall.zip 卸载包、自动卸载它自己、自动重启。如果你无法进入系统，在 TWRP 中手动刷入 uninstall.zip 卸载包即可。

## root

身兼 root 工具的 Magisk，在这方面的功能可以说是稳扎稳打。用户不必要过度操心，直接使用 Magisk Manager 中的默认设置就能用得舒心。

## 隐藏 root 

> 为什么安装了magisk后, ota升级还能发现我的系统已经root了? 不是magisk是systemless吗?

### SafetyNet 安全性测试

先进入 Magisk Manager 检测是否通过了谷歌服务中的 SafetyNet 安全性测试。

想要通过 SafetyNet 测试，最好使用原厂系统，或者是值得信赖的第三方 ROM 正式版（也就是 Official Builds），以减少不必要的麻烦。

如果是 basic integrity 这一项没有通过认证，那说明你遇到了大麻烦：试着开启「Magisk 核心功能模式」或者卸载所有模块，如果还是没有通过，那么你可能需要换一个系统或者第三方 ROM 了。

如果是 ctsProfile 这一项没有通过，那说明你的 ROM 没有通过其兼容性测试，一些 beta 版本或者国内厂商的 ROM 可能出现这种问题。这时我们下载使用 [MagiskHide Props Config](https://forum.xda-developers.com/apps/magisk/module-magiskhide-props-config-t3789228) 这个模块往往能够解决问题。

### Magisk Hide 

确保 SafetyNet 检测无虞后，我们才能开始「蒙眼」行动，即对指定的某些 App 隐藏 Magisk 的存在。

至于对哪些应用进行 Magisk Hide，这个就要看每个读者的具体需要了。一般来说，Google Play 服务和商店是必须的，但也请注意这条来自开发者的注意事项：如无必要，不要随意在 Magisk Hide 列表添加 App 而造成滥用（Do not abuse MagiskHide!）。

如果你还不放心，还可以去 Magisk Manager 的设置中打开「隐藏 Magisk Manager」。此时 Magisk Manager 将会进行一次重新安装，以便打乱软件包名来躲过对 Magisk Manager 的检测。

## 模块

> 模块只是简易了玩机操作的实践，但并没有将它无害化，该翻车的操作还是会翻车，
>
> 玩机千万条，数据第一条；模块不规范，机主两行泪。

### Magisk Manager

在模块仓库中点击下载，便会自动开始下载、刷入的步骤，刷入完成后你可以选择关闭或者是直接重启生效。模块更新也是一样的步骤。

### 手动

XDA 还有专门的 Magisk 板块，国内的酷安等交流地也有不少活跃制作模块的开发者。

但如果你是手动下载的模块 .zip 包，一切都需要手动。进入模块菜单项，点击下方的加号图标进入文件目录选取目标模块 .zip 包，即可开始模块的刷入或是更新。

### 卸载

在能够进入 Magisk Manager 的情况下，停用某个模块只需要把相应模块的钩子取消掉即可，如果你还想删掉这个模块，一并点击垃圾桶图标删除。停用和卸载都需要重启生效。

可是如果「翻车」进不了系统，那该如何停用和卸载问题模块呢？

- 无论是提前安装好，还是翻车后进入 TWRP 安装，你都需要用到 Magisk Manager for Recovery Mode 模块（仓库中搜索 mm 即可）。翻车后进入 TWRP 中的终端输入使用指令即可开始管理模块，[详见该模块的使用说明](#Magisk Manager for Recovery Mode)
- 部分模块可以以「同样的模块包，再刷入一次便是卸载」的方式对应进行停用卸载。
- 痛定思痛，进入 TWRP 刷入 Magisk 的卸载包，卸载一整个 Magisk。
- 没有 TWRP，保留数据刷写当前系统的完整包。

### [bootloop问题](https://iamernie8199.blogspot.com/2019/03/android-90-pie-root-xposed.html)

安装模组就有一定的机率会遇到Bootloop之类的问题

1. 除了用Uninstaller解除安装之外还有一些解决方法
2.  [Core Only Mode](https://forum.xda-developers.com/apps/magisk/module-core-mode-bootloop-solver-modules-t3817366)  能让框架暂时回归核心功能模式(不会载入任何模组)
3. [Magisk Manager for Recovery Mode](https://forum.xda-developers.com/apps/magisk/module-tool-magisk-manager-recovery-mode-t3693165)  能在TWRP下禁用模组

## 升级

每当 Magisk 进行版本更迭的时候，用户就会在 Manager 收到更新推送，一般是先更新 Magisk Manager，再由其来更新 Magisk 本体。

Magisk 也具有稳定版、beta 测试版和 Canary 金丝雀版三个版本，都是由开发者官方推出，用户可以根据自己的经验和需要选择对应的版本。

## [无痛升级ota](https://sspai.com/post/53075)

对移动平台操作系统而言，OTA 更新也许是最为常见也最为方便的系统升级方式，一次没有太多功能更新的月度安全补丁推送也许只需要下载几十兆大小的更新包，与之形成对比的则是以 GB 为单位计算的全量工厂镜像。

得益于 systemless 特性，能够无痛 OTA 更新也是 Magisk 的一大优点。

### A/B系统

A/B 系统分区是 Google 在 Android 7.0 时代引入的新机制，顾名思义，采用这个机制的设备拥有 A、B 两套系统分区，用户数据则能够在这两套系统分区之间共用。这种分区机制带来的最大好处，在于让无缝系统更新（seemless updates）成为了可能. 此外，采用 A/B 系统分区的设备在遭遇 OTA 事故时，还能在系统启动失败后自动切换回更新前能够正常工作的系统分区。

A/B 分区同样也是安装了 Magisk 状态下进行无痛 OTA 系统更新的前提条件，

### 何确定自己的设备支持A/B分区

使用adb

1. 运行 CMD 命令行工具或终端
2. 执行 adb shell 指令，此处应返回 设备代号:/$
3. 随后执行 `getprop ro.build.ab_update` 指令
4. 返回结果为 true 则表示你的设备采用了 A/B 系统分区。

当然，你也可以通过 [Treble Check](https://play.google.com/store/apps/details?id=com.kevintresuelo.treble) 这款小应用来检测 Project Treble 和 A/B 系统分区的兼容性，这款工具无需 root，下载安装后直接运行即可看到结果。

另外的方法[via](https://www.jianshu.com/p/0f4cc2896a09)

根据Magisk官方安装手册，建议要开启了 A/B 系统更新，可以确保不会刷成砖。

```
adb shell getprop ro.build.ab_update
adb shell getprop ro.build.system_root_image
```

确保这两个返回的都是true，代表开启了A/B 更新并使用了system_root_image分区布局

### 准备

由于 A/B 分区在系统更新过程中几乎不会对用户造成打扰，一些 OEM 厂商也顺势将 OTA 更新做成了一个可以在**后台自动完成**的任务。

但问题在于，伴随着自动完成 OTA 更新后系统分区的切换，我们在更新前借助 Magisk 获取的 root 权限和已经安装过的 Magisk 模块都会一一**失效**。

我们需要做如下准备:

- 找到并关闭自动系统更新选项。这个选项位于开发者选项的第一部分设置当中，因此还算好找。

- 然后，在厂商发布系统更新或确认能检测到 OTA 更新后，点击进入 Magisk Manager 应用，找到位于主界面的「卸载 Magisk」选项，然后点击「还原原厂镜像」。

- 注意，如果你在此时遇到了 `stock backup does not exist` 这样的提示，则表明 Magisk 未能在安装时成功创建 boot 分区的备份（自然也就无法还原原厂镜像），此时建议使用我们在[ 第一篇 ](https://sspai.com/post/53043)文章中提到的 boot 镜像修补法来重新安装 Magisk，这样就能保证原厂镜像得到正确备份了。

  

### 更新ota的流程

> 和第一步操作不同的是，自动系统更新选项我们建议保持长期关闭，**还原原厂镜像操作在每次进行 OTA 更新操作前都要执行**。

- OTA 更新流程结束后

- 无视系统的重启提示.

- 直接打开 Magisk Manager 应用，找到「安装」选项，然后在点击后的弹出菜单中选择「安装到未使用的槽位（Install to Inactive Slot）」。

- 随后，Magisk 就会在已经顺利进行过 OTA 更新的另一系统分区中进行安装。

- 安装完成后直接点击安装界面右下角的「重启」按钮，即可重启到既保留了 Magisk，又应用了 OTA 更新的另一系统分区了。



## [xposed ](https://iamernie8199.blogspot.com/2019/03/android-90-pie-root-xposed.html)

就结论而言我比较推荐edxposed

- 在Magisk管理器中刷入[Riru核心](https://github.com/RikkaApps/Riru/releases/download/v15/magisk-riru-core-v15.zip)
- 在Magisk管理器中刷入[EdXposed](https://github.com/ElderDrivers/EdXposed/releases/download/v0.2.9.9_b2/magisk-EdXposed-v0.2.9.9_beta2-release.zip), YAHFA is stable.
- 重启后安装[EdXposed管理器](https://github.com/ElderDrivers/EdXposed/releases/download/v0.2.9.9_b1/EdXposedInstaller_v2.2.0-release.apk)
- 打开之后确定是否成功安装
- 没意外会看到以下画面

![bloggersstand](D:\documents\markdown\magisk\Screenshot_20190301-173815.png)

[延伸阅读](https://iamernie8199.blogspot.com/search/label/Xposed)

## lucky patcher

magisk如何配合lucky patcher实现payment bypass?

[Disable signature check using Core Patch app to install unsigned APK (Xposed/EdXposed) (Root)](https://www.andnixsh.com/2020/02/disable-signature-check-using-core.html) 这里提到了lucky patcher系统隐藏的不足, 已经隐藏自身的一些局限. 

i have Magisk and Systemless Xposed and modded play store installed.

Does lucky patcher support Android 10? [yes](https://www.reddit.com/r/luckypatcher/comments/ejueew/does_lucky_patcher_support_android_10/)

[You need to install Xposed using Magisk Manager](https://www.reddit.com/r/luckypatcher/comments/gn6589/disable_apk_signature_verification_doesnt_apply/)

- First install the Riru - Core module, since that's the foundation for the Xposed module, 
- then install Riru - EdXposed. 
  - [Yes, I have Riru Core and Riru EdXposed (YAHFA and SandHook) mudules](https://www.reddit.com/r/luckypatcher/comments/giu523/lp_module/)
  - Do you know what's the difference between the YAHFA and Sandhook modules? YAHFA is more stable (it's been in development longer than Sandhook) while Sandhook is faster.
- Reboot, 
- and there should be an app called EdXposed on your phone. Open it, open the menu, and click on "Modules." There should be a module for Lucky Patcher; toggle it on and reboot. 
- All the patches in "Patch for Android" will automatically be enabled upon rebooting if you have done all the steps correctly---you shouldn't have to do it manually.
- Opened lucky patcher and under "Toolbox" menu>>Xposed Settings, enable "Support patch for InApp and LVL emulation".It says failed at first but works nevertheless. 

