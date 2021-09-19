# Trello

免费版本都能做些什么?

- Unlimited cards
- Unlimited members
- Up to 10 boards // 目前我只用一个就好.
- 1 Power-Up per board
- Unlimited storage (10MB/file) // 这个不错.
- 50 automated command runs per month
- Unlimited activity log
- Assignee and due dates
- iOS and Android mobile apps
- 2-factor authentication

## 概念

Workspace > Board > List > Cards

## 常用操作

- 删除: 要想删除cards, 先要archive, 然后在archived cards中删除, 没有批量作业, 相对来说在桌面操作更方便.
- 移动命令: 右键card, 使用move, 其中可以选择目标 board / list / 位置, 位置在这里挺重要.  [via](https://webapps.stackexchange.com/questions/95769/trello-to-quickly-move-a-card-to-top-of-another-list)

## 常用快捷键

### board中操作

- board选择菜单: `b`
- 切换当前board的菜单: `w`
- 搜索: `/`
- 过滤显示: `f`
  - 快速过滤和自己有关的card: `q`, 手机端只能通过 filter: @来定义
    - ==设置card和自己关联==: `space` (这个实在是应该常用)
  - 清除过滤设置: `x`
- 定位cards: 上下左右, 或者`j`, `k` (上下)
- 移动card: `,`和 `.`是向左右方向移动, 并且排列在其他list的尾部; 要想移动到头部, 使用shift组合键.
- 拷贝/移动: `ctrl+c`, `ctrl+x`, `ctrl+v`, 操作paste的时候, 如果在已有的card上, 那么就paste到这个card里面, 成为一个附件. 有点儿嵌套的意思, 不知道有什么作用. 值得注意的是, 这样的拷贝/剪切是原card的分身. 

### 新建card

- 在当前选择的card后面增加新card: `n`
- 自动完成members, 只在comments中起作用: `@`
- 自动完成labal, 新建card的时候: `#`
- 自动设置位置, 新建card的时候: `^2`, `^top`, `^bottom`, `^listname`

### 操作card

- 快速编辑title: `e`

- 完整编辑title: `t`

- archive card: `c`

- 设置时间: `d`

- 增加检查框: `-` 

- 关闭/取消: `esc`

- 保存修改: `ctrl+enter`

- 打开card: `enter`

- 增加label: `l`

  - 1-0数字分别代表固定颜色的label

     | Key  | Label Color |
     | ---- | ----------- |
     | 1    | Green       |
     | 2    | Yellow      |
     | 3    | Orange      |
     | 4    | Red         |
     | 5    | Purple      |
     | 6    | Blue        |
     | 7    | Sky         |
     | 8    | Lime        |
     | 9    | Pink        |
     | 0    | Black       |

  - `;` 切换label的文字显示.

- 增加/减少member: `m`

- 设定检测提醒: `s`

### 系统

- undo / redo: `z`, `shift+z`
- repeat action: `r`
- 打开快捷方式帮助: `?`

## 格式

> Markdown does **not work in card titles**, and not all syntax will display when using the Trello mobile app.

支持markdown, 但标题没有任何格式.  [via](https://help.trello.com/article/821-using-markdown-in-trello)

## 不足

- Trello不能自动萃取url的title?
- 不能多行title, 除非是拷贝进来多行.
- title是url无法点击访问该url, url只能在des中可以自动链接(markdown)
- 没有可以下载安装的windows 10的版本, 只能通过microsoft store安装. 







