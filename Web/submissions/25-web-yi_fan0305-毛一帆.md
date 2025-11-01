# 工具

## Hackbar 安装：

先下载谷歌浏览器，随后找到 Hackbar 的 [github 官网](https://github.com/0140454/hackbar/releases/tag/v1.2.8)，找到适合谷歌浏览器的压缩包 HackBar-chrome.zip，将压缩包解压进一个文件夹，随后点击谷歌浏览器“管理扩展”中“加载未打包扩展程序”，找到文件夹，将插件安装到谷歌中。

![](https://images.cnblogs.com/cnblogs_com/blogs/752184/galleries/2478477/t_251018155819_%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-18%20234943.png)

## Burp Suit 安装：

首先到 [PortSwigger](https://portswigger.net/) 官网，此外还要下载 Java ，之后找到合适自己版本的 Burp Suit Community （毕竟免费）下载即可。

![](https://images.cnblogs.com/cnblogs_com/blogs/752184/galleries/2478477/t_251018160325_%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-19%20000314.png)

## VM ware 虚拟机：

到 [官网](https://www.broadcom.com/) ，注册账号，之后在 products 中找到 VMware Products，点击 Fusion and Workstation，然后点击 download now，在 my downloads 中搜索 VMware Workstation Pro，之后继续点击，然后找打适合自己系统配置的虚拟机，之后下载即可。

![](https://images.cnblogs.com/cnblogs_com/blogs/752184/galleries/2478477/t_251019004603_%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-19%20084533.png)

随后，在 VM 虚拟机上，新建新的虚拟机，选择典型配置，安装镜像文件，输入用户名和密码，寻找位置，随后一步一步安装即可。

![](https://images.cnblogs.com/cnblogs_com/blogs/752184/galleries/2478477/t_251019012546_%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-19%20092539.png)

# Write Up

## view_source wp

X老师让小宁同学查看一个网页的源代码，但小宁同学发现鼠标右键好像不管用了。

获取在线场景，发看到 FLAG is not here，我们打开 F12，会发现，flag 就在里面。

![](https://images.cnblogs.com/cnblogs_com/blogs/752184/galleries/2478477/t_251019013608_%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-19%20093242.png)

## get_post wp

X老师告诉小宁同学HTTP通常使用两种请求方法，你知道是哪两种吗？

获取在线场景，发现 请用GET方式提交一个名为a,值为1的变量，在网址栏后面加上 `?a=1`，之后会跳转到一个网页，要求我们请再以POST方式随便提交一个名为b,值为2的变量，这时 F12，用我们的 hackbar，将网址输入，点开 Use POST method，在 Body 输入 `b=2`，点击 EXECUTE，然后就得到 flag 了。

![](https://cdn.luogu.com.cn/upload/image_hosting/7z3e68js.png?x-oss-process=image/resize,m_lfit,h_170,w_225)

# Linux

## Linux 系统安装

找到 [下载网站](https://ubuntu.com/download) ，找到 Mirrors ，找到中国的一个镜像网站，这里我找的是清华大学的镜像网，点击 "https://mirrors.tuna.tsinghua.edu.cn/ubuntu-releases/" ，随后寻找适合自己的版本下载，我选择的是 ubuntu-24.04.3-desktop-amd64.iso

## Linux 学习笔记

Shell 命令行

### 命令格式 

```
command parameters（命令 参数）  
```

### 长短参数

```
单个参数：ls -a（a 是英文 all 的缩写，表示“全部”）  
多个参数：ls -al（全部文件 + 列表形式展示）  
单个长参数：ls --all  
多个长参数：ls --reverse --all  
长短混合参数：ls --all -l  
```

长参数用 `--`，短参数用 `-`

### 快捷方式

`Ctrl + Alt + T`：打开 Shell

`Ctrl + R`：查找前面用过的命令，输入命令的一部分字符，会自动匹配，如果不是我们想要的命令，可重复该命令，再次匹配，找到命令后，`Enter` 直接执行，`Ctrl + E` 将命令输入到当前行。

`Ctrl + L`：清除屏幕，光标回到最左上角。

`Ctrl + C`：终止当前在执行的命令。

`Ctrl + U`：从当前位置剪切到行首（不包括当前位置）。

`Ctrl + Y`：从当前位置剪切到行尾（包括当前位置）。

`Ctrl + W`：剪切当前位置左侧的**单词**，这里指连续的英文字母。

`Ctrl + Y`：粘贴 `Ctrl + U/Y/W` 剪切的内容。

`Ctrl + A`：将光标放到该行最前面。

`Ctrl + E`：将光标放到改行最后面

`Ctrl + D`：关闭 Shell

### 查看路径

`pwd`：显示当前目录路径。

`which + 命令`：查看命令的可执行文件所在地。

### 浏览目录

`ls`：列出文件和目录。

#### 常见参数：
- `-a`：显示所有文件和目录，包括隐藏文件和目录。
- `-l`：显示详细列表。
- `-h`：适合人类阅读的，目前看到是效果是让文件大小更加明显可读（转化为K）。
- `-t`：按文件最后一次修改时间排序。
- `-i`：显示文件内容标识，即 `inode`。
（inode 存储的是文件的元信息，而不是文件的实际内容。可以把它理解为文件的"身份证"。）

### 切换目录

`cd`：表示切换目录。
