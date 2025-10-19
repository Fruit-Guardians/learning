工具
hackbar插件
** Firefox 浏览器**
1.打开 Firefox 浏览器
2.访问:https://addons.mozillaorg/en-US/firefox/addon/hackbar/
3.点击"Add to Firefox"
下载过程暂时遇到点瓶颈，所以还没有截图


Linux
环境搭载
![476b5b7f8644d55667befefa9d646d77](https://github.com/user-attachments/assets/9329fcce-e90d-46a9-a18f-6e6cbddf974b)


Linux笔记
一、Linux 目录结构
· /：根目录，一切的起点。
· /home：相当于 Windows 的 C:\Users\。每个用户都在这里有自己独立的文件夹。
· /root：系统管理员（root 用户）的家目录。
· /etc：存放系统配置文件。
· /bin, /usr/bin：存放普通用户可以使用的基本命令。
· /tmp：存放临时文件。

---

二、基本 Shell 命令（在终端中操作）

打开一个叫“终端”（Terminal）的软件。

1. 文件与目录操作

命令 全称/含义 示例与说明
pwd Print Working Directory pwd  显示你当前所在的目录路径。
ls List ls  ls -l （显示详细信息） ls -a （显示隐藏文件，以.开头的文件）
cd Change Directory cd /home/user  cd .. （返回上一级目录） cd 或 cd ~ （直接回家目录）
mkdir Make Directory mkdir my_folder  创建一个名为 my_folder 的新目录。
cp Copy cp file1.txt file2.txt  cp -r dir1 dir2 （复制目录需要 -r 参数）
mv Move mv old.txt new.txt （重命名） mv file1 /home/user/ （移动文件）
rm Remove rm file.txt  rm -r my_folder （删除目录需要 -r 参数） 警告：rm 删除后一般无法找回！
cat Concatenate cat file.txt  在终端中快速查看文件的全部内容。
less - less long_file.txt  分页查看长文件。按 q 退出，空格翻页。

2. 系统与权限管理

命令 全称/含义 示例与说明
sudo Super User Do sudo command  以管理员身份执行命令。系统会要求输入当前用户的密码。
chmod Change Mode chmod +x script.sh （给文件添加可执行权限） 用于改变文件权限。
ps Process Status ps aux  查看当前系统中正在运行的进程。
kill - kill 1234  结束进程ID为 1234 的进程。
man Manual man ls  查看 ls 命令的详细使用手册。

---

**三、包管理器（安装软件的利器）

不同的 Linux 发行版使用不同的包管理器来安装、更新和卸载软件。

系统 命令 功能
Ubuntu / Debian sudo apt update 更新软件源列表（必须首先执行）。
 sudo apt install package_name 安装软件包。
 sudo apt remove package_name 卸载软件包。
 sudo apt upgrade 升级所有已安装的软件包。
CentOS / RedHat sudo yum install package_name 安装软件包（旧版）。
 sudo dnf install package_name 安装软件包（新版）。

示例：在 Ubuntu 上安装 Vim 编辑器

```bash
sudo apt update
sudo apt install vim
```

---

**四、Vim 编辑器（最简单的使用）
1. 打开/创建文件：vim file.txt
2. 此时处于 普通模式，不能输入文字。按 i 键进入 插入模式。
3. 现在可以正常输入和编辑文本了。
4. 编辑完成后，按 Esc 键退出插入模式，回到普通模式。
5. 在普通模式下输入以下命令并回车：
   · :w - 保存文件。
   · :q - 退出 Vim。
   · :wq - 保存并退出。
   · :q! - 强制退出，不保存。

-------
writeup
打开链接地址
ctrl+U
找到<!-- cyberpeace{77eda6dca7e9ca4fb2e72a4d14fe2f50} -->

![1e3afb8a315c455408540d1f442fa41f](https://github.com/user-attachments/assets/4de4144d-3de0-4258-862c-f7dd3d392c40)

