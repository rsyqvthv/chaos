# 资源

[Issues](https://github.com/typora/typora-issues/issues) · typora/typora-issues 问题提交

# 设置

Open and edit `conf.user.json` from opened “File Explore”. If there’s no such file, create one.

# incoming

自定义上传代码的[方法](https://support.typora.io/Upload-Image/#custom):

if you write a tool upload-image.sh, then you can input [some path]/upload-image.sh in the command filed. Typora will call [some path]/upload-image.sh "image-path-1" "image-path-2" to upload two images located in image-path-1 and image-path-2. Then the command may return something like:

```
Upload Success:
http://remote-image-1.png
http://remote-image-2.png
```

Then Typora will get the two remote image url from the output, and replace the original local images used in the Markdown document.

You can use ${filename} and ${filepath} in your custom commands, they will be replace as the current markdown file name and current file path. For “untitled” files that have not been saved on your disk, they will be empty strings.

---

Typora will put recent used folders/files on the jump list of Typora, you could pin frequently used file/folder and access them quickly from task bar.

需要开启windows的历史记录功能. 如果像我一样关闭了这个功能, 就没有显示了.

