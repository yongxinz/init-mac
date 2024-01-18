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
