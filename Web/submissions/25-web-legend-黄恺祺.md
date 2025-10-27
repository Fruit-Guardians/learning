## 工具
### 1.浏览器开发者工具F12(浏览器自带无需安装)
![这是图片](https://youke1.picui.cn/s1/2025/10/26/68fe369827833.png "Magic Gardens")
### 2.Hackbar安装
在火狐中找到附加组件管理器,搜索本组件并进入安装.
![这是图片](https://youke1.picui.cn/s1/2025/10/26/68fe37cae91e4.png "Magic Gardens")
![这是图片](https://youke1.picui.cn/s1/2025/10/26/68fe387e408ca.png "Magic Gardens")
### 3.Burp Suite安装
这是安装和破解的完成图
![这是图片](https://youke1.picui.cn/s1/2025/10/26/68fe456315937.png "Magic Gardens")
### 4.AI使用
详见下文 AI写脚本
### 5.攻防世界
第一题 F12获取即可
![这是图片](https://youke1.picui.cn/s1/2025/10/26/68fe3c58db256.png "Magic Gardens")
第二题 
先在url中添加相应的参数
![这是图片](https://youke1.picui.cn/s1/2025/10/27/68fe472a7a61a.png "Magic Gardens")
再使用开发者工具-HackBar输入地址与参数,点execute即可
![这是图片](https://youke1.picui.cn/s1/2025/10/27/68fe481c2215a.png "Magic Gardens")
### 6.AI写脚本
![这是图片](https://youke1.picui.cn/s1/2025/10/26/68fe3e6171208.png "Magic Gardens")
![这是图片](https://youke1.picui.cn/s1/2025/10/26/68fe3f1c876d8.png "Magic Gardens")
## Linux
到官网上注册账号 下载并安装相应的VWware虚拟机软件
![这是图片](https://youke1.picui.cn/s1/2025/10/27/68ff5b88b37e9.png "Magic Gardens")
确保虚拟网卡的正常安装
![这是图片](https://youke1.picui.cn/s1/2025/10/27/68ff5c54da570.png "Magic Gardens")
在阿里云镜像站完成CentOS的安装
![这是图片](https://youke1.picui.cn/s1/2025/10/27/68ff5d4d9017a.png "Magic Gardens")
打开VWware,创建新的虚拟机,并提供正确的映像文件,点击下一步
![这是图片](https://youke1.picui.cn/s1/2025/10/27/68ff718aa5c12.png "Magic Gardens")
稍等片刻 则进入了系统
![这是图片](https://youke1.picui.cn/s1/2025/10/27/68ff75a0004af.png "Magic Gardens")
下载并安装FinalShell以便远程连接系统
![这是图片](https://youke1.picui.cn/s1/2025/10/27/68ff781974958.png "Magic Gardens")
## Linux基本命令
# 一 Lunix目录结构
无盘符概念 只有一个根目录/ 所有文件都在其下.
注意:Lunix系统中用/表示层级关系而非\.
/doc1/doc2/doc3.exe(第一个/表示根目录,后面的则表示层次关系)
相当于D:\doc1\doc2\doc3.exe

# 二 基本Linux命令
学习Linux，本质上是学习在命令行下熟练使用Linux的各类命令.
命令行：即Linux终端（Terminal)，是一种命令提示符页面。以纯“字符”的形式操作系统，可以使用各种字符化命
令对系统发出操作指令。
命令：即Linux程序。一个命令就是一个Linux的程序。命令没有图形化页面，可以在命令行（终端中）提供字符化的反
馈。

命令的通用格式:
command <-options> <parameter>
command 命令本身
option 可选非必填 命令的一些选项,用于控制命令的行为细节
parameter 命令的参数 多为命令的指向目标等

1. 列出文件:ls命令
ls 无选项 无参数:以平铺形式，列出当前工作目录(默认是home目录/home/用户名)的内容.
1s [-а -l -h] [Linux路径]
当使用参数时，ls命令的参数表示：指定一个Linux路径，列出指定路径的内容.
使用选项时:
-a 列出全部文件 包括隐藏文件(以.开头的文件等等)和文件夹
-l 以列表（竖向排列）的形式展示内容，并展示更多信息 权限 用户组 大小 创建的时间等
-al/-a -l/-la 同时包含-a与-l 顺序可以任意组合
-h 必须与/l搭配使用-lh,以易于阅读的形式列出文件大小K/M/G

2. 切换与查看工作目录:cd-pwd命令
cd 切换工作目录
cd [Linux路径] 无需选项 只有参数 不写参数时自动切换至home目录
pwd 查看当前的工作目录.

3.相对路径 绝对路径和特殊路径符
cd /home/itheima/Desktop 绝对路径写法 以根目录为起点 路径描述以/开头
cd Desktop 相对路径写法 [!!以当前目录(工作目录)为起点!!] 可以不包含工作目录 路径描述不一定以/开头
特殊路径符:
.表示当前目录，比如cd./Desktop表示切换到当前目录下的Desktop目录内，和cd Desktop效果一致
..表示上一级目录，比如：cd..即可切换到上一级目录，cd../..切换到上二级的目录
~表示HOME目录，比如：cd~即可切换到HOME目录或cd~/Desktop，切换到HOME内的Desktop目录

4. 创建新目录:mkdir命令
mkdir [-p] [Linux路径] (在工作目录/当前目录下)创建新的目录(文件夹)
路径必填 可相对可绝对可特殊
-p选填 表示自动创建不存在的父目录 适用于创建连续多层级的目录
即mkdir -p ~/doc1/doc2/doc3...若doc1到3都不存在 用-p可直接创建一条链!
注意：创建文件夹需要修改权限，请确保操作均在HOME目录内，不要在HOME外操作
涉及到权限问题，HOME外无法成功!

5. 文件操作:touch(创建)、cat(查看)、more(查看)命令
touch [路径] 创建文件
touch doc1/doc2.txt 表示在doc1下创建doc2文件,类型为txt.
文件路径依旧可绝对可相对.
如何区分文件夹和文件?
用ls -l查看前缀 前缀为d则为文件夹 为-则为文件.
cat [路径] 查看文件(若为txt文件会直接显示至下方)
more [路径] 在查看文件的基础上支持翻页.

6. 文件操作: cp(复制)、mv(移动或者改名)、rm命令(删除)
cp [-r] [参数1] [参数2] 复制
参数1表示被复制的文件或文件夹 复制文件夹时添加-r 表示递归.
参数2表示复制到的路径(这些路径都要带你复制的文件本身的名字/重命名后的名字 即cp doc1 doc2/doc3 将doc1以doc3为命名复制至doc2目录中.)
mv [参数1] [参数2] 移动或改名
参数1表示被移动的文件或文件夹
参数2表示移动到的路径(这里就不需要带本身名字了) 如果参数2不是路径而是文件名 文件名又不存在(即排除相对路径) 
则视为将该文件改名至参数2的名称.
rm [-r -f] [参数1] [参数2] ...... [参数n]删除
参数可为无数个 因此可以一次删除多个文件或文件夹
与cp一样 -r选项代表删除文件夹
-f则为强制删除(管理员用户在删除时会被提示信息 加了-f就不会提示了)
rm 命令支持通配符* 用于做模糊匹配.：
test*，表示匹配任何以test开头的内容
*test，表示匹配任何以test结尾的内容
*test*，表示匹配任何包含test的内容
(可以通过su-root，并输入密码123456（和普通用户默认一样）临时切换到root用户体验
通过输入exit命令，退回普通用户，这样就能看到删除时的提示信息了)

7. 查找命令:which find
通过which命令，查看所使用的一系列命令的程序文件存放在哪里
which [要查找的命令] 即可.
通过find指令，搜索指定的文件
按文件名查找:
find [起始路径] -name(表示以文件名查找) [文件名]
注:按文件名查找也可以将文件名改成带通配符的文件名,做模糊匹配
按文件大小查找:
find [起始路径] -size(按大小查找) [+或- n数字[kMG]]
+-表示大于小于
nkMG表示数字+单位,注意k小写,MG大写
例如:find / -size +1G 查找根目录下大于1G的文件
