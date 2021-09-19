# markdown

不是因为写东西多畅快，我向来都是用鼠标去按按钮。。而是因为markdown文件本质上就是txt，都在自己手上，存储方便，同步方便，不容易悲剧，极端情况文件损坏也能看到没损坏的内容，最多是损坏的部分是乱码而已。但是因为我的markdown笔记带本地图片所以同步后手机端其实体验很不美好，所以我基本不在手机上改动，重要的笔记都导出成html放网盘里方便在手机里看。

放在本地虽说安全但是使用不便，真是好纠结啊。目前还是图床一份本地备份的方式，虽说麻烦了一点但是数据还是更加重要的。

android 编辑器

- 纯纯写作

- **epsilon notes**

  大型markdown文件的迅速和不卡顿

  渲染的时候不会出现什么奇怪的问题。

- **markor**
  目前我使用的, 觉得不错.

- ia writer

- 易写

- Jotterpad

- NoteHighlight 

- dropbox+typora

- vnote

# syntax 

heading
------

```
This is an H1 
============= 

This is an H2 
-------------
```

Any number of underlining `=`’s or `-`’s will work.

```
# This is an H1 
## This is an H2 
###### This is an H6
```


Blockquotes
=========

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet, 
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus. 
>  Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus. 
>    > Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse 
> id sem consectetuer libero luctus adipiscing.

> This is the first level of quoting. 
>
> > > This is nested blockquote.

Blockquotes can contain other Markdown elements, including headers, lists, and code blocks:

Lists
====

* Red 
* Green 
* Blue

+ Red 
+ Green 
+ Blue

- Red 
- Green 
- Blue

1. Bird 
2. McHale 
3. Parish

1. Bird 
1. McHale 
1. Parish

3. Bird 
1. McHale 
8. Parish

Each subsequent paragraph in a list item must be indented by either 4 spaces or one tab:

1. This is a list item with two paragraphs. Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus. Donec sit amet nisl. Aliquam semper ipsum sit amet velit.

To put a blockquote within a list item, the blockquote’s `>`

1. This is a list item with two paragraphs. Lorem ipsum dolor sit amet, 
2. > consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus. Donec sit amet nisl. Aliquam semper ipsum sit amet velit.

delimiters need to be indented:

you can backslash-escape the period:

1986\. What a great season.

Code Blocks
=========

One level of indentation — 4 spaces or 1 tab — is removed from each line of the code block.

Regular Markdown syntax is not processed within code blocks.

Horizontal Rules
============

* * *
***
*****
- - -
----------------------------------------

Links
====

This is [an example](http://example.com/ "Title") inline link.

See my [About](markdown syntax.md) page for details. 

reference style link
--------------------

This is [an example][id] reference-style link.

[id]: http://example.com/ "Optional Title Here"

Link definition names may consist of letters, numbers, spaces, and punctuation

they are _not_ case sensitive.

The _implicit link name_ shortcut allows you to omit the name of the link, in which case the link text itself is used as the name.

[Google][]

[Google]: http://google.com/

Link definitions can be placed anywhere in your Markdown document. I tend to put them **immediately after each paragraph in which they’re used**, but if you want, you can put them all at the end of your document, sort of like footnotes.

Automatic Links
-----------------

<http://example.com/>

<address@example.com>



## Anchor

```
Take me to [contact](#contact_form)
```

```
<a id="contact_form"></a>
```

Emphasis
=======

Markdown treats asterisks (`*`) and underscores (`_`) as indicators of emphasis.

Text wrapped with one `*` or `_` will be wrapped with an HTML `<em>` tag; double `*`’s or `_`’s will be wrapped with an HTML `<strong>`

can backslash escape it:

\*this text is surrounded by literal asterisks\*

Code
====

Use the `printf()` function. 

you can use multiple backticks as the opening and closing delimiters:

``There is a literal backtick (`) here.``

Images
=====

![Alt text](assets/testing.png) 
![Alt text](assets/testing.png "Optional title")

Reference-style image syntax looks like this:

![Alt text][id]

[id]: url/to/image "Optional title attribute"

comments
========

[syntax - Comments in Markdown - Stack Overflow](https://stackoverflow.com/questions/4823468/comments-in-markdown)

- 仅自己可见, 在输出后用户不可见. 直接加reference, 而不要引用.

[comment]: <> "This is a comment, it will not be included"
[comment]: <> "in  the output file unless you use it in"
[comment]: <> "a reference style link."

- 或者, 也不要引用.

[//]: <> "This is also a comment."

- 更好的兼容性, 避免<>被解释: ✔️

[//]: # "This may be the most platform independent comment"

- 当然, 比较传统的可以用html注释, 这样输出html是可以看到的.

	`<!-- coment -->`

- 对于github来说, 可以这样: 

	[](Comment text goes here)
	
	他会生成一个锚点:
	
	`<a href="Comment%20text%20goes%20here"></a>`