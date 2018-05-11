# Vim常用命令：

## 移动光标

1. 移动到行尾"$"，移动到行首"0"(数字)，移动到行首第一个字符处"^"

2. 移动到段首"{"，移动到段尾"}"

3. 移动到下一个词"w"，移动到上一个词"b"

4. 移动到文档开始"gg"，移动到文档结束"G"

5. 跳到第n行"ngg" 或 "nG" 或 ":n"

6. 移动光标到屏幕顶端"H"，移动到屏幕中间"M"，移动到底部"L"

7. 移动到上次编辑文件的位置 "`"

## 编辑操作

1. 光标后插入"a", 行尾插入"A"

2. 后插一行插入"o"，前插一行插入"O"

3. 删除字符插入"s"， 删除正行插入"S"

4. 光标前插入"i"，行首插入"I"

5. 删除一行"dd"，删除后进入插入模式"cc"或者"S"

6. 删除一个单词"dw"，删除一个单词进入插入模式"cw"

7. 删除一个字符"x"或者"dl"，删除一个字符进入插入模式"s"或者"cl"

8. 粘贴"p"，交换两个字符"xp"

9. 交换两行"ddp"

10. 复制"y"，复制一行"yy"

11. 拷贝当前行 "yy"或者"Y"

12. 撤销"u"，重做"ctrl + r"

13. 删除到行尾可以使用"D"或"C"

14. 删除当前字符 "x"

15. ">>"缩进所有选择的代码

16. "<<" 反缩进所有选择的代码

17. 合并两行" J"

18. 若不想保存文件，而重新打开":e!"

19. 若想打开新文件 ":e filename"，然后使用"ctrl + ^"进行文件切换

## Vim常用设置（`.vimrc`）

``` javascript

打开语法高亮
syntax on

使用配色方案
colorscheme desert

打开文件类型检测功能
filetype on

不同文件类型采用不同缩进
filetype indent on

允许使用插件
filetype plugin on
filetype plugin indent on

关闭vi模式
set nocp

与windows共享剪贴板
set clipboard+=unnamed

取消VI兼容，VI键盘模式不易用
set nocompatible

显示行号, 或set number
set nu

历史命令保存行数
set history=100

当文件被外部改变时自动读取
set autoread

取消自动备份及产生swp文件
set nobackup
set nowb
set noswapfile

允许使用鼠标点击定位
set mouse=a

允许区域选择
set selection=exclusive
set selectmode=mouse,key

高亮光标所在行
set cursorline

取消光标闪烁
set novisualbell

总是显示状态行
set laststatus=2

状态栏显示当前执行的命令
set showcmd

标尺功能，显示当前光标所在行列号
set ruler

设置命令行高度为3
set cmdheight=3

粘贴时保持格式
set paste

高亮显示匹配的括号
set showmatch

在搜索的时候忽略大小写
set ignorecase
 
高亮被搜索的句子
set hlsearch
 
在搜索时，输入的词句的逐字符高亮（类似firefox的搜索）
set incsearch

继承前一行的缩进方式，特别适用于多行注释
set autoindent

为C程序提供自动缩进
set smartindent

使用C样式的缩进
set cindent

制表符为4
set tabstop=4

统一缩进为4
set softtabstop=4
set shiftwidth=4

允许使用退格键，或set backspace=2
set backspace=eol,start,indent
set whichwrap+=<,>,h,l

取消换行
set nowrap

在被分割的窗口间显示空白，便于阅读
set fillchars=vert:\ ,stl:\ ,stlnc:\

光标移动到buffer的顶部和底部时保持3行距离, 或set so=3
set scrolloff=3

```

## 参考文献（从如下文献中摘录）

[Vim配置](https://blog.csdn.net/g_brightboy/article/details/14229139)

[Vim编辑快捷键总结](https://www.jianshu.com/p/6f13474d36ac)
