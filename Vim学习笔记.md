# Vim学习笔记

## 一、vim简介

1、vim是linux和unix下使用最多的编辑器

2、只要用服务器，vim是必备技能

3、后端和运维工程师必须掌握的编辑器

4、可以纯键盘编码，提高编辑效率

## 二、vim的四种模式

### 1、插入模式（Insert）

通过a\i\o或者A\I\O进入

A:在改行的最后面进行插入

a：在当前字母后进行插入

I:在改行的最前面进行插入

i:在当前字母的前面进行插入

O：在当前行的上面进行插入

o:在当前行的下面进行插入

### 2、正常模式（normal）

进入vim的模式

### 3、命令行模式（command）

：wq 保存退出

：vs 竖分屏

：sp 横分屏

### 4、视窗模式（visual）

v:单选

V:行选

ctrl+v:与hjkl建结合使用，块状选取

## 三、Vim的常用技巧

### 1、insert模式下快速删除

`ctrl+h`:快速删除一个字母

`ctrl+w`:快速删除一个单词

`ctrl+u`:快速删除当前行

注：以上命令在终端中也可以使用

在终端中，

`ctrl+a`:到命令行**首部**

`ctrl+e`:到命令行**尾部**

`ctrl+b`:**前移**一个字符

`ctrl+f`:**后移**一个字符

### 2、如何快速切换Insert和normal模式

`ctrl+[`:从insert切换到normal模式==Esc

`gi`：从normal模式快速回到insert最后一次编辑的位置

## 四、Vim的快速移动

### 1、hjkl多练多用，摆脱上下左右建

### 2、实用移动

​	**1、w/W**

​		w:移动到下一个单词词首

​		W:移动到下一个以空格分隔的单词词首

​	**2、e/E**

​		e:移动到下一个单词的词尾

​		E:移动到下一个以空格分隔的单词词尾

​	**3、b/B**

​		b：移动到上一个单词的词首

​		B：移动到上一个以空格分隔的单词的词首

### 3、行间搜索移动

​	**f{char}:**在一行中快速搜索一个字符，并跳转到它。

​		；下一个匹配

​		，上一个匹配

​	**F{char}：**反向搜索

​	**t{char}:**跳转到想要查找字符的前一个字符

### 4、vim水平移动

​	**$:快速到行尾**

​	**0：快速到行首**

​	^:快速到行首的非空白字符

​	g_:快速到行尾的非空白字符

### 5、垂直移动

（）：在句子间移动

​	{}：在在段落中移动

### 6、vim页面移动

​	**gg/G：** 文章首行/尾行

​	`ctrl+o`	快速返回到上次编辑的行

​	**H/M/L**	屏幕的头部/中部/尾部

​	`ctrl+u` 下一页 

​	`ctrl+f` 上一页

​	zz:将光标至于屏幕中部

## 五、Vim的快速修改

### 1、r/R（replace）

​	r：替换一个字符

​	R：替换多个字符

### 2、s/S（substitue）

​	s:删除当前字符并进入插入模式   4s(删除4个字符)

​	S:删除当前行并进入插入模式

### 3、c/C(change)

​	c：ct"-->删除到“

​	C：删除整行进行操作

## 六、Vim的查询

### 1、格式

​		/name

​		set hls：设置高亮

​		set incsearch:设置增量搜索

### 2、n/N

​		跳到下一个/上一个

### 3、*/#

​		进行当前单词的前向或者后向的匹配

## 七、Vim如何搜索替换

## 1、格式

`：[range] 	s/{pattern}/{string}/[falgs]`

flag:

​	**g:globle**全局范围

​	**c:confirm:**表示请求确认

​	**n:**只计数，不替换

## 2、示例

：% 	s/name/good/g

:10,20	s/like/nameg

：%		s/like//n

精确匹配：% s/**\\<stop\\>**/name/g

## 八、vim多文件操作

## 1、Buffer\windows\tab

**buffer：**打开的一个文件的缓冲区

**windows:**buffer可视化的分割区域

**tab：**可以组织窗口为一个工作区

## 2、如何实现在buffer间切换

`ls：`列出当前所有的缓冲区

`bn:n`代表数字，跳转到指定的缓冲区

`:bpre 	:bnext	:bfirst	:blast`的用法

## 3、window窗口的划分和跳转

`:sp`	水平划分窗口

`:vs`	竖直划分窗口

`ctrl +w+whjkl`：实现窗口的切换

`ctrl +w+HJKL：实现窗口的移动

`ctrl+=`:使所有的窗口等高等宽

## 4、tab标签页

`:tabnew filename`	在新的标签页中打开文件

`gt`:跳到上一个标签页

`gT`:跳到下一个标签页

## 九、vim中的文本对象

vim中的文本对象是指一个单词或者一个句子或则一个段落

如何使用文本对象

`[number]<command>[text object]`

number表示数字

command表示命令d\c\y

text object:要操作的文本对象

`yiw\ci(\ci"`个自的含义是什么？

## 十、vim中复制和粘贴

复制粘贴 y/p

剪切粘贴 d/p

V选择要复制的内容，然后用p粘贴

解决粘贴出现排版的问题

**:set past**

**然后再粘贴**

**：set nopast**

**"{register}**:寄存器、a-z均可使用

:reg	查看寄存器

## 十一、vim的宏

了解即可

用q+寄存器开始录制，使用q结束录制

思考：如何快速再每行首部添加同一个字符

十二、vim补全大法

`ctrl+n ctrl+p`:单词补全

`ctrl+x ctrl+f`:文件名补全

`r! echo %:`快速得到当前文件名

`：r! echo %:p`：快速得到绝对路径

## 十二、vim配色

：colorscheme 当前主题颜色

：colorscheme ctrl+d 显示所有配色

：colorscheme 配色名	修改配色

## 十三、vim映射

**映射**：把一个操作，映射到另一个操作上去

**基本映射**：normal模式下的映射

​	`map - x`:用-号代替删除键x

​	`map <c-d> dd`:使用ctrl+d执行dd删除一行

**其他模式的映射**：

​	`nmap`:normal下的映射

​	`imap`:insert下的映射

​	`vmap`:visual下的映射

**如何避免递归映射：**采用非递归映射

​	nnoremap\inoremap\vnoremap

**如何写vimscript:**《本方法学vimscript》

## 十四、vim插件

**安装插件管理器：**Plug-in

https://github.com/junegunn/vim-plug

**常用插件**

``Plug 'mhinz/vim-startify'`
 `Plug 'preservim/nerdtree'`
 `Plug 'kien/ctrlp.vim'` 
 `Plug 'vim-airline/vim-airline'`
 `Plug 'vim-airline/vim-airline-themes'` 
 `Plug 'Yggdroot/indentLine'`
 `Plug 'w0ng/vim-hybrid'`
 `Plug 'altercation/solarized'`

## **持续更新！**