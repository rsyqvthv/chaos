# 使用Turbo net做portble

参考: [Turbo Studio - YouTube](https://www.youtube.com/watch?v=GA03qdYSlRY)

直接前后take snapshot, 然后自动对比系统变化. 需要注意的是:

- filesystem中, 新建的目录是实心的. windows之类的目录可以删除.
- 非实心的目录中也会有文件, 比如桌面快捷方式等, 需要遍历删除.
- 注册表也酌情删除

# 隔离模式 isolation mode

[Virtualize Your Applications with Turbo Studio - Turbo.net](https://turbo.net/studio)

- full：容器完全与系统隔离, 数据只在沙箱内交换.
- write copy: 容器可以访问主机设备上的值。如果产生冲突, 则虚拟值优先. 但所有的写入都在沙箱里面.
- merge: 容器可以访问主机设备上的值。如果产生冲突, 则虚拟值优先. 但所有的写入都写入系统.
- hide: 对容器来说这些值将不可访问. 此种模式会导致容器失败.

之后选择startup file选择启动程序. 默认会使用它的图表和metadata. 

在setting中设置sandbox, location中使用@APPDIR@来表示程序目录. via, 没有找到更多, 似乎还有: @DESKTOP@, @APPDATA@ [via](https://www-c.turbo.net/docs/studio/working-with-turbo-studio/container-settings#container-settings)

最后选择project type是exe, 点击build即可.