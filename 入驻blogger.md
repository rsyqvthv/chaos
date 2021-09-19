## 简要步骤

- 首先加入custom domain, 以防将来的变化
- 然后选择个简单的theme
- ~~最后联通stackedit, 这样可以使用markdown写作.~~ 
- ~~发布的时候使用simplehtml,~~
- ~~在file properties定义常用的参数.~~
- ~~同步stackedit和google, 保存编辑.~~ 
- 改用typora, 注意title使用h3或者以下的.
- copy html code, 粘贴到blogger就好. 
- 图片上传到blogger中.
- favicon需要一些时间才能更新上去

## 发布时

- ~~如何在stackedit中定义permalink? (似乎不能) google自动的permalink自动加入日期很讨厌.~~
- 每篇文章定义permalink, 文章更新后需要revert to draft后再修改日期, 但这样需要在blogger后台定义一个跳转, 将旧的url跳转到新的url上. 说实在的, blogger的这个自动加时间的url对seo不友好. 但可以通过新文引旧闻的方法进行弥补, 也更像blog吧.

## 备份

- 备份样式. blogger > themes > 下拉小三角 > backup (restore也在这里.)
- 备份内容. blogger > settings > manage blog > backup content

## blogger设置

- layout有一些有趣的设置

- themes > custom > 左边advanced > 下拉菜单中最后一个 add css, 我加入了如下:

  ```css
  .post-body blockquote {
      background: #f9f9f9;
      border-left: 10px solid #ccc;
      margin: 1.5em 10px;
      padding: 0.5em 10px;
      quotes: "\201C""\201D""\2018""\2019";
      font-size: inherit;
      text-align: inherit;
  }
  .post-body blockquote:before {
      color: #ccc;
      content: open-quote;
      font-size: 4em;
      line-height: 0.1em;
      margin-right: 0.25em;
      vertical-align: -0.4em;
  }
  /*.post-body blockquote p {
      display: inline;
  }*/
  .post-body pre > code {
      background: #f4f4f4;
      border: 1px solid #ddd;
      border-left: 3px solid #f36d33;
      color: #666;
      page-break-inside: avoid;
      font-family: monospace;
      font-size: x-small;
      line-height: 1.6;
      margin-bottom: 1.6em;
      max-width: 100%;
      overflow: auto;
      padding: 1em 1.5em;
      display: block;
      word-wrap: break-word;
  }
  .post-body *:not(pre)>code {
      color: #242729;
      background-color: #e4e6e8;
      padding: 2px 4px;
      border-radius: 3px;
      font-size: small;
  }
  .post-body li > input ~ p {
      display: inline;
      margin-left: .5em;
  }
  .post-body figure table,td,th{
      border: 1px solid black;
      border-collapse: collapse;
      padding: 10px;
      text-align: left;
  }
  .post-body figure tr:nth-child(even) {
      background-color: #f2f2f2;
  }
  .post-body mark {
      background-color: #b8ef79;
      color: black;
      padding: 2px 4px;
      border-radius: 3px;
  }
  .post-body a:visited, .post-body a:link {
      display: inline;
      background-image: -webkit-gradient(linear,left top,right top,color-stop(100%,#f9ed43),color-stop(0,#fff));
      background-image: -webkit-linear-gradient(left,#f9ed43 100%,#fff 0);
      background-image: linear-gradient(to right,#f9ed43 100%,#fff 0);
      background-position: 0 80%;
      background-repeat: repeat-x;
      background-size: 100% 23%;
      color: inherit;
  }
  .post-body a:hover {
      background-position-y: 0;
      background-size: 100% 87%;
  }
  .post h3.post-title {
      font-size: 3em;
  }
  .post-body:not(.container) {
      padding-top: 5em;
  }
  .post-body h1 {
      font-size: 2em;
      margin-top: 4em;
      text-align-last: center;
  }
  .post-body h2 {
      font-size: 2em;
      margin-top: 2em;
  }
  .post-body h3 {
      font-size: 1em;
      text-decoration: underline;
  }
  .post-body h4 {
      font-size: 1em;
      text-decoration: underline dashed;
      
  }
  .post-body h5 {
      font-size: 1em;
      text-decoration: underline wavy red;
  }
  .post-body h6 {
      font-size: 1em;
      text-decoration: underline wavy green;
  }
  ```

## 问题有待解决

- 自动加入[toc]