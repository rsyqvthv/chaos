# 将markdown上传到github

参考[应该如何使用Github Pages? - 学习 Web 开发 | MDN](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/Using_Github_pages)

浏览器: 

- 在git中创建一个仓库, 如**chaos**
- 并创建一个**gh-pages**分支, 自动访问 index.html

windows: 

- 安装git, [Git - Downloads](https://git-scm.com/downloads)
- 在本地文件目录初始化git: `git init`
- 链接远端仓库: `git remote add origin https://github.com/chrisdavidmills/my-repository.git`
- 加入全部本地文件到仓库 `git add --all`
- 确认修改: `git commit -m 'adding file for first time'`
- 推送上传: `git puch -u origin master`

访问

- username.github.io/my-repository-name
- 实例: https://rsyqvthv.github.com/chaos

# 使用git

参考 [Git 原理入门 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2018/10/git-internals.html), [常用 Git 命令清单 - 阮一峰的网络日志](https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)

初始化. `git init` 理解为新建一个仓库

加载修改到暂存. `git add --all` / `git add .`

提交到仓库. `git commit -m 'comments'`, `git commit -a`

列出所有分支(包括远端的). `git branch -a`

增加一个远程仓库. `git remote add [shortname] [url]`

上传本地分支到远端分支. `git push [remote] [branch]`

## 如何忽略

参考 [.gitignore file - ignoring files in Git | Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/saving-changes/gitignore), [How to Use a .gitignore File | Pluralsight](https://www.pluralsight.com/guides/how-to-use-gitignore-file)

新建一个.gitignore的文件, 在其中一行忽略一个就好. !keep.file 是拒绝忽略的意思.

# 自动执行

参考

- [如何用github和typora打造自己的云笔记 - 哔哩哔哩](https://www.bilibili.com/read/cv2230341/)
- [自动将本地文件保存到GitHub - 掘金](https://juejin.im/post/5e1bcca0e51d454d94422551), 唯一的好处是多个伪同步.
- [请问如何写一个批处理自动打开 gitbash，然后自动执行一系列git命令（windows平台）？ - 知乎](https://www.zhihu.com/question/38962022)
- [Windows使用计划任务自动Git同步代码_alwaysl7的博客-CSDN博客_git 自动同步 windows](https://blog.csdn.net/alwaysl7/article/details/74561203?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-7.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-7.nonecase) << 这个我能理解

脚本 [via](https://blog.csdn.net/xuhang666/article/details/98052724?utm_medium=distribute.pc_relevant.none-task-blog-baidujs-1)

```
echo "Start submitting code to the local repository"
echo "The current directory is：%cd%"
git add *
echo;
 
echo "Commit the changes to the local repository"
set now=%date% %time%
echo %now%
git commit -m "%now%"
echo;
 
echo "Commit the changes to the remote git server"
git push origin master
echo;
 
echo "Batch execution complete!"
echo;
```

建立计划任务, task scheduler

- create basic task...
- 然后一步一步执行就好.
- 注意在执行程序的步骤中, **选择工作目录为当前目录**. 
- 如果想最小化窗口, 甚至 隐藏, 参考 [[minimize cmd window#powershell]]


# pandoc

> 利用pandoc将markdown转换为html

[How to Automatically Convert Markdown to HTML](https://zapier.com/blog/markdown-html-export/)

for more powerful converting tools, you can install [Pandoc](https://pandoc.org/installing.html) on your Windows, Mac, or Linux computer to convert Markdown text into the format you want from Terminal.

- 下载installer后直接解压, 无需安装.
- 配置系统路径
- 然后参考教程使用命令行即可.

帮助

- 参考安装目录中的Pandoc User's Guide.html
- 或者 [online](https://pandoc.org/getting-started.html) 帮助
- 命令参考 [Pandoc - Pandoc User’s Guide](https://pandoc.org/MANUAL.html)
- `pandoc --help`

基本的语法

- filter模式. 

直接在cmd中运行`pandoc`后, 进入编辑模式, 这种模式下编辑的东西, 在[ctrl+z]退出后会自动转换成html.

定义输入输出格式: `pandoc -f markdown -t html`, 默认的转换就是markdown to html

- 转换模式

`pandoc test1.md -f markdown -t html -s -o test1.html`

The `-s` option says to create a “standalone” file, with a header and footer, not just a fragment

#question: 批量输出如何维护链接?

# 在github中如何删除所有的commit历史

有时候为了隐私问题, 可能需要清除所有的commit历史. 那么步骤如下: 

首先保证你有git安装在本地, windows中我使用gitportable. 

打开gitbash, 进入本地的repo目录, 如: `/c/folder/repo/` 

建立一个独立的分支:

```bash
git checkout --orphan temp_branch
```

将所有的文件加入这个新的分支`temp`

```bash
git add -A
git commit -am "init commit"
```

删除master分支

```bash
git branch -D master
```

将当前的`temp`分支命名为`master`

```bash
   git branch -m master
```

提交修改到github

```bash
git push -f origin master
```

这时会提示什么认证窗口, 我选择取消. 之后github和本地的commit历史就全部清除了.



参考: 

- [Steps to clear out the history of a git/github repository](https://gist.github.com/stephenhardy/5470814)
- [git - how to delete all commit history in github? - Stack Overflow](https://stackoverflow.com/questions/13716658/how-to-delete-all-commit-history-in-github)
- [Git: "please tell me who you are" error - Stack Overflow](https://stackoverflow.com/questions/11656761/git-please-tell-me-who-you-are-error)
- [git-cheat-sheet-education](https://education.github.com/git-cheat-sheet-education.pdf)
- [How (and why!) to keep your Git commit history clean | GitLab](https://about.gitlab.com/blog/2018/06/07/keeping-git-commit-history-clean/)
- [Clean GIT history — a Step by Step Guide | by Catalina Turlea | Medium](https://medium.com/@catalinaturlea/clean-git-history-a-step-by-step-guide-eefc0ad8696d)
- [GitHub - Delete commits history with git commands](https://gist.github.com/heiswayi/350e2afda8cece810c0f6116dadbe651)
- [How to Delete Commit History in Github – TecAdmin](https://tecadmin.net/delete-commit-history-in-github/)

# 在同步中忽略一些文件


