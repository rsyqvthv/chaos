# 使用de4dot解除混淆

访问:

[0xd4d/de4dot: .NET deobfuscator and unpacker.](https://github.com/0xd4d/de4dot) 下载 [Actions · 0xd4d/de4dot](https://github.com/0xd4d/de4dot/actions)

使用: 

Drag and drop the file(s) onto de4dot.exe and wait a few seconds.

结果:

> de4dot v3.1.41592.3405
>
> Detected **Spices.Net** (va.exe)
> Cleaning va.exe
> Renaming all obfuscated symbols
> Saving va-cleaned.exe

# 使用dnSpy查看

访问:

[0xd4d/dnSpy: .NET debugger and assembly editor](https://github.com/0xd4d/dnSpy), 下载 [Releases · 0xd4d/dnSpy](https://github.com/0xd4d/dnSpy/releases)

使用:

- 先判断32/64, 我只知道自己的系统是64的, vegasaur安装在program files目录, 判断就是64位吧.
- 将需要调试的dll拖拽进来打开. 
- 之后就傻眼了, 
  - 参考了一些教程, 但他们都能通过一些关键字进行搜索定位破解位置, 而vegasaur的关键字即便是解除混淆后, 也是乱码的(如下). 我搜索days这样的字仍然没有有效的返回. 
  
    > Resources.ResourceManager.GetString("櫋誛盚㡋ᦙ덬캽豽㐑脶蜾湙ઢ愌鑑싹頭畜렮螧馕핣ᱜꙂ뒉", Resources.cultureInfo_0);
  
    
  
  - 而且它是使用一个lic文件 (在`c:\Program Files\Vegasaur\3.0`中) 来检测是否注册的, 尝试查找这个地址中的各个片段, 都没有结果.
  
  - 单看左侧的那些命令函数也不得要领, 不知如何下手. 我的程序背景太弱, 这条路子恐怕我没有太多的可行性. 呼呼.
- 待续...

# 延长试用期

- 待续...