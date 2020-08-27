# 基本操作
进入一个文件： vim 文件名
打开多个文件 vim file1 file2
使用:bn :bp 来进行文件切换

## vim的模式
普通模式
写入模式 - i
命令模式 - :

## vim的各种插入
(逻辑)对于插入类操作，大写表示相反的方向。
i - insert I - 行首insert
a - append A - 行尾append
o - 上插 O - 下插
p - 下(后)粘 P - 上(前)粘

## vim的导航
基本用法：<N><motion>
(逻辑)在vim中移动光标是一个很频繁的需求，因此它就在你的右手。这样很方便。
jk - 上下 hl - 左右
jk就在食指和中指，hl就在jk的左右。

(助记)up和down
Ctrl + u 向上翻半页
Ctrl + d 向下翻半页

(注)这里的单词是真的单词。标点符号也算单词。一坨中文字不能识别为词语所以算单词。
w(ord) 后一个单词的第一个字母
e(nd) 该单词的末尾，再按一次到下一个单词的末尾
b(ack) 向前一个单词

(逻辑)WEB。大写的按上下文元素移动的命令是指按空格(或空白字符)分割。

0 表开始，则到行首
^ 突起的小山包，到行首非空字符
$ 美元，尽头是美元

% 匹配括号移动(助记：百分号就像一个8被/隔开。这两个o本来是一对，所以用它来查找匹配的括号当然合适啦。)

* 匹配下一个当前光标所在的单词。（助记：*是通配符嘛。）
# 匹配上一个... （助记：音乐中#代表升号。）

## vim的搜索
/? 向前或向后搜索
nN查看上一个或下一个搜索结果
可以noremap n nzz 方便把结果放到中间，因为这样眼睛就可以始终盯着屏幕中间。

vim中有leader键，相当于键盘上的win键
自定义leader键：let mapleader=" "

将搜索后显示的高亮取消:nohlsearch  (no height line search)

将leader回车变为取消高亮的方法
leader在map中用<LEADER>表示
noremap <LEADER><CR> :nohlsearch<CR>

## 普通模式下的搜索
基本用法：<N><action><motion>
f - find
=========
向前搜索第一个出现的字母
f + 要最开始出现的字母的位置
df? 删到
F 向前搜索

t - to
=======
f相同但光标落在前一个字符
T 向前搜索

## vim的操作
操作逻辑：<operation><motion> 由操作加动作构成，非常符合逻辑。

d - delete：删除(剪切)
==================
dl 往左边删除。

c - change 改写
=====================
?cw 改?个词
?cb 改?上一个词
?cl 改?个字符

s - 改写一个字符
================
S改写这一行

r - replace
===========
替换一个字符
R - 进入替换模式

v - 可视模式
==========
可以执行一些普通的操作
V - 行可视
在行可视下输入:normal <operation> 可以在每行执行指令
<C-Q/V>可以进入块

<C-V><motion>[I/A$]<char>
在多行中插入同样的文字。可用于注释。
如果是在行尾统一插入，则需要插入$。

<C-V> 也可以用于插入多行一样的文字，这样你就不用复制了。

## 区域选择
基本用法：<action><N>[a/i]<object>
object 可以是字符或者(w(ord)、W(ord)、s(entence)、p(aragraph))
i - in 
======
ciw 如果你在词中间，change in word
ci" 改写""中的东西删除并进入写入模式
yi" 同理
di" 同理

a - ... 
=====
助记：插入时i和a是一对，这里的a可以理解为all
和i一样，但顺带选中指定的object。word是会删除后面顺带的一个空格，在你的单词是在句尾而且还多一个空格可能会有用。

y - 复制
==========

快速浏览
zz == z. 放到中间

:split 上下分屏
:vsplit 左右分屏

## 简单文字处理
~ 所在光标大小写切换，光标移动到下一个。可以和数字联动。
gU gu 也可以达到同样效果，但不是切换而是更具体了。后面跟motion。

<C-A> 数字增加1。是整个数字。如果所在光标不是数字则，会往后找。

<C-N><C-P>简单的自动补全。

<N>J 将下面一行连起来，行首的多遇空格会变成一个空格。

< > 左右缩进，后接motion

= 自动缩进，后接motion。(常用gg=G)

## 宏
q<char> 记录宏
@<char> 调用宏
@@ 调用上个宏？

============================配置文件相关===============================
更改配色
=======
:color <tab>

snazzy 配色，github上
let g:SnazzyTransparent = 1 让你的vim透明

## vim改键
noremap a b

## 更方便的vim保存
map s :w<CR>
map Q :q<CR>

加载配置文件 :source $MYVIMRC
打开语法高亮 :syntax on 
显示普通行号 :set nu
显示相对行号 :set relativenumber
下面两个有
显示搜索高亮 :hlsearch
启用边输边高亮 :incsearch
搜索忽略大小写 :set ignorecase
搜索智能大小写 :set smartcase

在当前行显示一条线 :set cursorline
显示自动换行 :set wrap # 自带
显示在命令模式下按了什么键，一般在右下角 :set showcmd
底行命令tab自动补全 :set wildmenu # 自带

