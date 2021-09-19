# 块元素

## 标题

之前使用h3开头, 现在还是觉得使用h1开头, 加上custom css.

# title1

title1 相应的文字

## title2

title1 相应的文字

### title3

title1 相应的文字

#### title4

title1 相应的文字

##### title5

title1 相应的文字

###### title6

title1 相应的文字

## 段落

A paragraph is simply one or more consecutive lines of text. In markdown source code, paragraphs are separated by two or more blank lines. In Typora, you only need one blank line (press `Return` once) to create a new paragraph.

Press `Shift` + `Return` to create a single line break. 
Most other markdown parsers will ignore single line breaks, 
so in order to make other markdown parsers recognize your line break, 
you can leave two spaces at the end of the line, or insert `<br/>`.

## 引用块

> This is a blockquote with two paragraphs. This is first paragraph.
>
> This is second pragraph. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.



> This is another blockquote with one paragraph. There is three empty line to seperate two blockquote.

## 列表

*   Red
*   Green
*   Blue



1.  Red
2.  Green
3.  Blue

## 任务列表

- [ ] a task list item

- [ ] list syntax required

- [ ] normal **formatting**, @mentions, #1234 refs

- [ ] incomplete

- [x] completed

## 代码块

Here's an example:

```
function test() {
  console.log("notice the blank line before this function?");
}
```

## 表格

| First Header | Second Header |
| ------------ | ------------- |
| Content Cell | Content Cell  |
| Content Cell | Content Cell  |
| Content Cell | Content Cell  |
| Content Cell | Content Cell  |

## 脚注

You can create footnotes like this[^footnote].

[^footnote]: Here is the *text* of the **footnote**.

## Horizontal Rules

------

# Span 元素

## 链接

This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.

## 内部链接 @question

**You can set the href to headers**, which will create a bookmark that allow you to jump to that section after clicking. For example:

Command(on Windows: Ctrl) + Click [This link](#代码块) will jump to header `Block Elements`. To see how to write that, please move cursor or click that link with `⌘` key pressed to expand the element into markdown source.

## 引用链接

This is [an example][id] reference-style link.

[id]: http://example.com/	"Optional Title Here"

或者一个省略版

[Google][]
And then define the link:

[Google]: http://google.com/

## URLs

Typora allows you to insert URLs as links, wrapped by `<`brackets`>`.

`<i@typora.io>` becomes <i@typora.io>.

Typora will also automatically link standard URLs. e.g: www.google.com.

## 图片

![Alt text](https://www.w3schools.com/images/compatible_chrome.gif "Optional title")

## Emphasis 斜体

Markdown treats asterisks (`*`) and underscores (`_`) as indicators of emphasis. Text wrapped with one `*` or `_` will be wrapped with an HTML `<em>` tag. E.g:

*single asterisks*

_single underscores_

## Strong 加重

**double asterisks**

__double underscores__

## Code代码

Use the `printf()` function.

## Strikethrough 删除线

~~Mistaken text.~~

## 下划线

`<u>Underline</u>` becomes <u>Underline</u>.

## Emoji :smile: 表情

Input emoji with syntax `:smile:`.

## Highlight 高亮

==highlight==

# HTML

直接使用html+style属性: <span style="color:red">this text is red</span>

## 嵌入 Contents

<iframe width="560" height="315" src="https://www.youtube.com/embed/OqU5z1ZkN90" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 视频

You can use the `<video>` HTML tag to embed videos. For example:

```
<video src="xxx.mp4" />
```



