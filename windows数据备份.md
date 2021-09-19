# windows数据备份

## Drive SnapShot

不用启动盘，可以直接在系统下运行备份及还原，速度还很快。

能pe下运行

> Drive SnapShot 再也不用了，曾经备份了，同时也ghost备份了，偶然一次机器崩溃了，突然想用Drive SnapShot 恢复，结果死活蓝屏不行，幸亏当时ghost还备份了一份，再也不用了。以前也测试过失败，还支持热备份什么的，简直是扯淡。

你这肯定只是个例，我备份了没有1000也有800机器了，没有遇到过类似问题。同推Drive Snapshot。

强烈推荐Drive Snapshot和DISM++组合使用

driver snapshot早期有个毛病，<u>目标磁盘必须要大于备份的源盘；</u>
否则恢复过程正常，但系统就是死活起不起来. 当年就是这个导致评估阶段就否决了这个备份还原方案.

我也一度用 Drive Snapshot，如果我没记错当时还是我在推荐 CCF 推荐的，单个执行文件远超 Ghost 的备份速度。几年使用下来基本没什么问题，顶多遇到在线还原卡圈的情况，转到 PE 还原也就没问题了。

Drive SnapShot还是推荐这个，只备份系统盘，数据啥的反正不在只放一个地方的。

## Macrium Reflect

免费版本就够用了

最后选择了 Macrium Reflect，百来 M 体积，界面友好，很快能上手，备份速度飞快（默认使用 Direct IO，30 多 G 3分钟不到），也能自建 PE 恢复环境。最关键的是恢复后那个什么 地平线4 终于不用重装了！

唯一缺点就是不像 ATI 那样有人做单文件的 PE 版本，所以系统完全不能启动时，必须用它的 ISO 启动来还原。

我装过这个Macrium Reflect, 它学win10一样, 强迫你升级它的

至于在PE里用, 我用它生成的winpe iso, 提取出一个执行文件, 然后放到任何pe都可以用了.

我把 ISO 里面的 WIM 文件解开，就有个 macrium 目录，提取后在 WePE 2.1 下运行还是提示缺文件。看起来是 WePE 精简得比较厉害，缺 esent.dll 和 winhttp.dll ，补全就可以启动了。

但是有个问题，就是启动时 loading network 过程会卡几分钟，应该是 WePE 完全精简掉了网络功能，而我也不知道怎么去掉这个 Macrium Reflect 启动时不检测网络。其它 PE 不太清楚。

压缩包 19M 不到，也可以在正常系统作为绿色版使用，没有上面所说的卡 loading 问题 ，只支持 Windows 10 x64.

## vhd安装系统

差分一下vhd文件就是备份了，硬盘占用也小。
win7企业版和旗舰版，win10全系列都支持。

[详细](https://www.jianshu.com/p/62ee081df1e5)

## DISM++

DISM++备份系统为WIM，然后以WIMBOOT还原系统，再用SNAPSHOT备份即可

Dism++ 类 WIM 备份速度太慢

## ghost

还可以，不过恢复了还要修复一下引导

还原后win10会自己重装驱动, 没有的驱动进系统后用驱动精灵

可以配合DISM++

## ATI (Acronis True Image)

太庞大

## 自带的备份和还原

这个自带的很多人都没有听说更不会用（还原）

## 参考

[【讨论】win10的系统盘用什么软件备份？ - 第 2 页 - 精品技术论坛](https://bbs.et8.net/bbs/showthread.php?t=1388010&page=2)

