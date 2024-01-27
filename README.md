# init-mac

作为一名程序员，最趁手的“兵器”那还得是 MBP，有了一台新的 MBP 之后，肯定是要安装一大堆软件或工具的，把电脑装扮成自己喜欢的样子。

正好最近入手了一台新电脑，把安装软件的过程记录下来，下次再需要装环境直接按这个文章来就行了。

### Homebrew

Homebrew 是 Mac 的包管理器，仅需执行相应的命令就能下载安装需要的软件包，可以省掉自己去下载、解压、拖拽（安装）等繁琐的步骤。

官方地址：<https://brew.sh/>

安装命令：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

但是，使用这个命令大概率是会报错的：

```bash
curl: (7) Failed to connect to raw.githubusercontent.com port 443: Connection refused
```

所以，这里提供一个替代方案，使用国内的源进行安装：

```bash
/usr/bin/ruby -e "$(curl -fsSL https://cdn.jsdelivr.net/gh/ineo6/homebrew-install/install)"
```

### 终端

对于 Mac 用户来说，iTerm2 和 oh-my-zsh 就是两大神器。把 iTerm2 和 oh-my-zsh 配置好，不仅可以给自己打造一个舒适的开发环境，养养眼，还能大大的提升效率。

**iTerm2：**

官方地址：<https://iterm2.com/>

直接下载安装就可以了。

**oh-my-zsh：**

官方地址：<https://ohmyz.sh/>

两个安装命令：

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

```bash
sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

当然了，大概率也是会失败的。这里再提供两个国内的源：

```bash
sh -c "$(curl -fsSL https://gitee.com/mirrors/oh-my-zsh/raw/master/tools/install.sh)"
```

```bash
sh -c "$(wget -O- https://gitee.com/pocmon/mirrors/raw/master/tools/install.sh)"
```

可以使用如下命令查看系统有哪些 shell：

```bash
cat /etc/shells
```

使用 `echo $SHELL` 查看系统当前使用的 shell。

如果想切换的话，可以使用命令：

```bash
chsh -s /bin/zsh
```

接下来就可以来给终端美容了，更换自己喜欢的主题，可以到下面地址来选择：

> <https://github.com/ohmyzsh/ohmyzsh/wiki/themes>

本地主题在这个目录下：`~/.oh-my-zsh/themes`。

然后还有两个比较重要的插件：

先进入到插件目录：

```bash
cd ~/.oh-my-zsh/custom/plugins/
```

1、命令补全 zsh-autosuggestion：

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions
```

2、语法高亮：zsh-syntax-highlighting

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
```

### 配置 vim

直接分享给大家我的 vimrc 配置文件：

```bash
" 显示行号
set number
" 显示标尺
set ruler
" 历史纪录
set history=1000
" 输入的命令显示出来，看的清楚些
set showcmd
" 状态行显示的内容
set statusline=%F%m%r%h%w\ [FORMAT=%{&ff}]\ [TYPE=%Y]\ [POS=%l,%v][%p%%]\ %{strftime(\"%d/%m/%y\ -\ %H:%M\")}
" 启动显示状态行1，总是显示状态行2
set laststatus=2
" 语法高亮显示
syntax on
set fileencodings=utf-8,gb2312,gbk,cp936,latin-1
set fileencoding=utf-8
set termencoding=utf-8
set fileformat=unix
set encoding=utf-8
" 配色方案
colorscheme desert
" 指定配色方案是256色
set t_Co=256

set wildmenu

" 去掉有关vi一致性模式，避免以前版本的一些bug和局限，解决backspace不能使用的问题
set nocompatible
set backspace=indent,eol,start
set backspace=2

" 启用自动对齐功能，把上一行的对齐格式应用到下一行
set autoindent

" 依据上面的格式，智能的选择对齐方式，对于类似C语言编写很有用处
set smartindent

" vim禁用自动备份
set nobackup
set nowritebackup
set noswapfile

" 用空格代替tab
set expandtab

" 设置显示制表符的空格字符个数,改进tab缩进值，默认为8，现改为4
set tabstop=4

" 统一缩进为4，方便在开启了et后使用退格(backspace)键，每次退格将删除X个空格
set softtabstop=4

" 设定自动缩进为4个字符，程序中自动缩进所使用的空白长度
set shiftwidth=4

" 设置帮助文件为中文(需要安装vimcdoc文档)
set helplang=cn

" 显示匹配的括号
set showmatch

" 文件缩进及tab个数
au FileType html,python,vim,javascript setl shiftwidth=4
au FileType html,python,vim,javascript setl tabstop=4
au FileType java,php setl shiftwidth=4
au FileType java,php setl tabstop=4
" 高亮搜索的字符串
set hlsearch

" 检测文件的类型
filetype on
filetype plugin on
filetype indent on

" C风格缩进
set cindent
set completeopt=longest,menu

" 功能设置

" 去掉输入错误提示声音
set noeb
" 自动保存
set autowrite
" 突出显示当前行 
set cursorline
" 突出显示当前列
set cursorcolumn
"设置光标样式为竖线vertical bar
" Change cursor shape between insert and normal mode in iTerm2.app
"if $TERM_PROGRAM =~ "iTerm"
let &t_SI = "\<Esc>]50;CursorShape=1\x7" " Vertical bar in insert mode
let &t_EI = "\<Esc>]50;CursorShape=0\x7" " Block in normal mode
"endif
" 共享剪贴板
set clipboard+=unnamed
" 文件被改动时自动载入
set autoread
" 顶部底部保持3行距离
set scrolloff=3
```

### 字体

安装一个我很喜欢的一个字体 Fira Code，好看，而且也很适合用来写代码。

> <https://github.com/tonsky/FiraCode>

### VS Code

配置信息：

```json
{
    "editor.fontFamily": "Fira Code",
    "editor.fontLigatures": true,
    "editor.fontSize": 14,
    "workbench.startupEditor": "none"
}
```

### 安装 GO

直接从官网下载安装包安装即可。

修改配置：

```bash
# 启用 Go Modules 功能
go env -w GO111MODULE=on

# 配置 GOPROXY 环境变量，以下三选一

# 1. 七牛 CDN
go env -w  GOPROXY=https://goproxy.cn,direct

# 2. 阿里云
go env -w GOPROXY=https://mirrors.aliyun.com/goproxy/,direct

# 3. 官方
go env -w  GOPROXY=https://goproxy.io,direct
```

### 数据库客户端 dbeaver

官方地址：https://dbeaver.io/

### 开发环境

使用 Docker 搭建基本的开发环境，包括 MySQL 和 Redis 等。

这里推荐一个开源项目 gonivinck，只需要一条命令，就可以启动常用的开发环境容器。

项目地址：https://github.com/nivin-studio/gonivinck