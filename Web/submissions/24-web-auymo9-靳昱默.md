工具
##列表
1.F12
<img width="2559" height="1591" alt="image" src="https://github.com/user-attachments/assets/b0f84747-26e0-4342-9a17-46c09c094ee1" />
2.HackBar
<img width="2276" height="1155" alt="image" src="https://github.com/user-attachments/assets/7155cadc-3842-40c5-8500-dcaa25db9963" />
3.Burp Suite
<img width="2357" height="1335" alt="image" src="https://github.com/user-attachments/assets/2c5c34c0-30a3-46d9-b603-e734a55873f7" />


##题目
1.view_source
<img width="1067" height="802" alt="image" src="https://github.com/user-attachments/assets/a5ba73ab-f66b-4605-af37-352c6a46991a" />
2.get_post
<img width="2542" height="1203" alt="image" src="https://github.com/user-attachments/assets/926a6cff-e674-409d-9bf8-2315e165a03d" />
3.MD5
<img width="1557" height="1238" alt="image" src="https://github.com/user-attachments/assets/16968b11-7bd6-4328-98ff-a8527152de22" />

##环境搭建
<img width="2559" height="1400" alt="image" src="https://github.com/user-attachments/assets/72eef2ea-6133-465d-92e4-5b62b7eabb52" />


##Linux
1. 命令格式与查助资料
- 终端命令的通用格式：
command [-options] [parameter]
- 其中 -options 表示选项， parameter 表示传给命令的参数。
- 查阅命令帮助／手册：
  - command --help：简单帮助信息。
  - man command：调用其 manual 手册页，包含详细说明。
2. 为什么要学习常用 Linux 命令
- 早期 Linux 系统常无图形界面，操作几乎完全依赖命令行。
- 在职场中，服务器维护／远程管理多通过 SSH 等命令行方式完成。
- 虽然 Linux 下可用命令很多（200 +），但“常用”的只有十几条，掌握这些即能应对日常操作。
3. 文件和目录操作
查看目录内容
- ls：列出当前目录内容。
 常用选项：
  - -a：显示所有文件，包括隐藏文件（以 “.” 开头）。
  - -l：以长列表格式显示详细信息。
  - -h：配合 -l 以“人性化”方式显示文件大小。
- 通配符使用（在 ls 或其他命令中）：
  - *：匹配任意数目的字符。
  - ?：匹配任意一个字符。
  - []：匹配括号内的任一字符，如 [a-f] 匹配 a 至 f。
切换目录
- cd [目录]：切换当前工作目录。
 注意事项：
  - Linux 的文件／目录名称大小写敏感。
  - 相对路径：以当前目录为参照（路径不以 / 或 ~ 开头）
  - 绝对路径：以 /（根目录）或 ~（用户主目录）开头。
  - cd ~ 切换到当前用户家目录。
  - cd - 在最近两个工作目录之间来回切换。
创建与删除
- touch 文件名：如果文件不存在，则创建空文件；若存在，则更新其修改时间。
- mkdir 目录名：创建新目录。可加 -p 选项递归创建多级目录。
- rm 文件名：删除文件或目录。使用时需谨慎，因为删除后一般不可恢复。
  - 常用选项：-f 强制删除／忽略不存在的文件，-r 递归删除目录。
拷贝与移动
- cp 源 目标：复制文件或目录。若复制目录，需加 -r。
 常用选项：-i 在覆盖前询问。
- mv 源 目标：移动或重命名文件／目录。
 常用选项：-i 在覆盖前询问。
- tree [目录]：以树状图形式列出目录结构。选项 -d 只显示目录。
查看文件内容
- cat 文件名：一次性显示整个文件内容。适用于内容少的文件。
 常用选项：
  - -n：为所有输出行编号。
  - -b：仅对非空行编号。
- more 文件名／less 文件名：分页显示文件内容。比较适合内容多的文件。more 的操作键：空格滚下一屏，Enter滚一行，b回滚一屏，q退出。
- grep [选项] 模式 文件名：在文本文件中按照模式（可用正则表达式）进行搜索。
 常用选项：
  - -n：显示匹配行号。
  - -v：显示不匹配模式的行（反向匹配）。
  - -i：忽略大小写。
 示例：以 ^a 表示行首以 a 开头，ke$ 表示行尾以 ke 结束。
- 其他：如 echo 用于显示文本，重定向 >、>> 通过把输出写入／追加到文件，管道 | 把一个命令的输出传递给另一个命令。
4. 系统信息相关命令
时间和日期
- date：查看当前系统时间
- cal：显示日历，-y 可以查看整年日历
磁盘信息
- df -h：显示文件系统磁盘剩余空间，-h 以人性化方式显示（如 GB、MB）。
- du -h [目录]：显示该目录及其子目录／文件所占用的磁盘空间。
进程信息
- ps aux：查看当前系统上各用户／各终端的进程状态（包括详细信息）
 选项说明：
  - a：显示当前终端以外用户的进程。
  - u：以用户所属、CPU/内存使用等方式显示详细状态。
  - x：显示没有控制终端的进程。
- top：动态显示正在运行的进程，并根据 CPU／内存等排序。按 q 退出。
- kill [-9] PID：终止指定进程。-9 表示强制终止。建议只终止自己启动的进程，不要随意 kill root 启动或系统关键进程，以免造成系统不稳定。
5. 用户与权限管理
组管理
- groupadd 组名：新增组。
- groupdel 组名：删除组。
- cat /etc/group：查看系统中的组信息。
- chgrp -R 组名 文件/目录：递归修改文件／目录所属组。
用户管理
- 创建用户／删除用户／更改密码 等通常要用 sudo 执行。
- id 用户名：查看用户的 UID、GID 等信息。
- who：查看当前登录的所有用户。
- whoami：查看当前登录的是哪个用户。
- which 命令：显示该命令所在路径（可执行文件）。示例：which ls 输出 /bin/ls。
 提示：
  - /bin、/usr/bin：普通用户命令目录。
  - /sbin、/usr/sbin：系统管理员专用命令目录。
  - 注意：cd 是 shell 内置命令，不会显示具体路径。
- 切换用户：
  - su - 用户名：切换到指定用户，并切换目录到该用户的家目录（若有 “-”）。
  - exit：退出当前用户会话。
 注意：直接切换到 root (su 不带用户名) 不推荐，因为安全风险较高。
文件权限修改
- chown 用户 文件/目录：修改文件／目录的所有者为指定用户。
- chgrp -R 组名 文件/目录：递归修改所属组。
- chmod -R 模式 文件/目录：递归修改权限模式。示例：chmod -R 755 目录名。
6. 打包／压缩／软件安装
打包／解包
- tar 是 Linux 中常用的备份／打包工具。
 格式示例：
# 打包
tar -cvf 打包文件.tar 被打包的文件／路径...
# 解包
tar -xvf 打包文件.tar
- 选项说明：
  - c：创建档案（archive）
  - x：解开（extract）
  - v：显示过程（verbose）
  - f：指定档案文件名，f 之后必须是 .tar 文件名。
压缩／解压缩
- 使用 gzip（结合 tar -z）常见于 .tar.gz 格式：
# 压缩
tar -zcvf 打包文件.tar.gz 被压缩的文件／路径...
# 解压缩
tar -zxvf 打包文件.tar.gz
# 解压缩 + 指定目录
tar -zxvf 打包文件.tar.gz -C 目标路径
- 注意：-C 指定解压到某个目录，该目录必须已存在。
- 使用 bzip2（结合 tar -j）得到 .tar.bz2 格式：
# 压缩
tar -jcvf 打包文件.tar.bz2 被压缩的文件／路径...
# 解压缩
tar -jxvf 打包文件.tar.bz2

软件安装／卸载／更新（以 APT 为例）
- sudo apt install 软件包：安装软件。
- sudo apt remove 软件包：卸载软件。
- sudo apt upgrade：更新已安装的软件包。
7. 远程管理常用命令
关机／重启
- shutdown 命令用于关机或重启。常见示例：
# 立刻重启
shutdown -r now
# 立刻关机
shutdown now
# 在指定时间关机（如今天20:25）
shutdown 20:25
# 10 分钟后关机
shutdown +10
# 取消已设置的关机
shutdown -c
- 注意：如果不指定时间，默认 1 分钟后关机。
 在远程维护服务器时，一般建议重新启动系统而不是直接关机。
网络／远程登录与文件传输
- ifconfig：查看或配置当前机器网卡配置信息。
 示例：ifconfig | grep inet 查看 IP。
 注意：物理网卡通常命名如 ensXX。127.0.0.1 为本地回环地址。
- ping IP地址：测试本机与目标主机之间的网络连通性。越大延迟越慢。
 示例：ping 127.0.0.1 用于检测本地网络是否正常。
- ssh：远程登录。格式：
ssh [-p port] user@remote
- -p 指定端口（非默认 22 时需指定）。、
 注意：在 Windows 系统上可使用 PuTTY、XShell 等连接。
- scp：远程拷贝文件。格式类似于 ssh：
scp -P port 本地文件 user@remote:目标路径
scp -P port user@remote:远程文件 本地目标
- 若复制目录，加 -r。注意：指定端口时选项是大写 -P。
