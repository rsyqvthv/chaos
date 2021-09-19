# 如何安装Office

没想到安装Office居然在2021年成为了一件麻烦事儿, 真怀念Office 2007年, 只需要下载, 序列号, 选择组件的时候. 

话不多说, 下面是步骤. 

现在微软的安装包是没有组件选项的, 如果需要选定特定的组件, 那么就需要自己下载一个部署工具, 然后配置自己的组件配置, 最后使用部署工具按照这个配置下载和安装.

## 下载部署工具

部署工具: [Office - Microsoft Download Center](https://www.microsoft.com/en-us/download/office.aspx) 选择 Office Deployment Tool进行下载. 运行解压在一个目录中, 其中有一个setup.exe, 我们只需要这个. 

## 自定义配置

访问[Apps Admin Center](https://config.office.com/), 左下角的Create a new configuration, 进行配置.

- Products : Office Pro Plus 2019 Vol, 其他的都选择none
- Apps: 这里是重点, 选择需要的, 比如 Word, Excel和PowerPoint
- Language: 选择中文, 
- Installation: CDN+to user, upgrade选择全部卸载之前的版本.
- Licensing: Auto accepte EULA =  yes, 
- 剩下的随便.
- 最后右上角输出保存Configuration.xml文件即可. 

## 下载配置的安装文件

使用这个命令下载配置好的文件包 `setup.exe /download Configuration.xml` 等很久, 耐心点儿. 完事儿cmd窗口会自动关闭.

## 安装

使用这个命令安装 `setup.exe /configure Configuration.xml`

安装的时候的提示画面中会显示正在安装的组件的图标, 应该和之前配置的一样.

如此完成后, Office就结束了.

这个目录可以多次使用安装, 直接将安装命令存为cmd文件即可.

