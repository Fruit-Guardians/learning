![IMG_20251019_150903](https://github.com/user-attachments/assets/77092735-1550-4a3a-a458-e67cf15ab989)工具
列表
1. 浏览器开发者工具F12。
<img width="824" height="1254" alt="屏幕截图 2025-10-18 222437" src="https://github.com/user-attachments/assets/10c10a93-3039-4e71-8b66-fd694cde20fc" />

2. Hackbar:   
、<img width="1093" height="497" alt="屏幕截图 2025-10-19 145839" src="https://github.com/user-attachments/assets/f14d72a8-c7d0-407a-9d26-6bea73e205e9" />

3. Burp Suit  / Yakit 
[图片]<img width="2381" height="1339" alt="屏幕截图 2025-10-18 233819" src="https://github.com/user-attachments/assets/da67b453-1995-4440-9790-3e468c836373" />

[图片]<img width="2373" height="1317" alt="屏幕截图 2025-10-18 233651" src="https://github.com/user-attachments/assets/351a1782-ad01-4f3b-89ca-23e84867ea4d" />


题目


- 攻防世界基础题单：view_source
[图片]<img width="1339" height="1211" alt="屏幕截图 2025-10-18 235222" src="https://github.com/user-attachments/assets/bf901997-ba55-4e35-b259-2e15e4a92204" />

- 攻防世界基础题单：get_post
[图片]<img width="2000" height="1095" alt="屏幕截图 2025-10-19 010159" src="https://github.com/user-attachments/assets/43eed4bc-948d-4d2e-a4ea-3b7830a7a526" />

- 用ai写一个python脚本，要求找到一个值经过md5加密后的前6位是15af95
[图片]<img width="1769" height="1007" alt="屏幕截图 2025-10-19 151818" src="https://github.com/user-attachments/assets/bfdce79c-f936-4fb5-9e0a-6797d63526a1" />


- 攻防世界基础题单：robots
- 先http://61.147.171.35:58583/robot.txt进入，发现flag在这，于是http://61.147.171.35:58583/f1ag_1s_h3re.php找到flag
[图片]<img width="651" height="90" alt="屏幕截图 2025-10-19 143533" src="https://github.com/user-attachments/assets/d5d90d0e-581f-4ab7-90bc-164095c03abe" />

Linux基础（重点）
[图片]<img width="1624" height="1263" alt="屏幕截图 2025-10-19 150039" src="https://github.com/user-attachments/assets/09bcf6fc-f112-489a-a215-a1686498ef9c" />


[图片]<img width="1522" height="1009" alt="屏幕截图 2025-10-18 215850" src="https://github.com/user-attachments/assets/4e4fc23d-31b8-47ad-9184-ecb6d8b9a31e" />

  学习笔记
[图片]![IMG_20251019_150903](https://github.com/user-attachments/assets/5f9bf3dd-31a6-41ca-9324-20249e7ed303)

[图片]![IMG_20251019_150906](https://github.com/user-attachments/assets/ef6cea76-d03b-4258-a2e4-60ef1ac1c49d)



[图片]![IMG_20251019_150911](https://github.com/user-attachments/assets/20037589-2211-4b7c-bd2a-e4e2ef63404a)

[图片]![IMG_20251019_150914](https://github.com/user-attachments/assets/26fb2852-77e9-4b50-a009-c8e1f88929b0)
![IMG_20251019_150919](https://github.com/user-attachments/assets/63fd4400-5a32-4977-b6da-9dcbe02ff198)



Linux入门核心笔记
 
一、Linux基础概念
 
- 操作系统（OS）：硬件之上的第一层软件，是硬件与其他软件的桥梁，核心作用是管理内存、设备等资源，控制程序运行。
- Linux内核 vs 发行版：
- 内核：Linus主导维护的系统核心，负责硬件抽象、多任务调度等底层功能，是真正意义上的“Linux”。
- 发行版：内核+常用软件的集成包（如RHEL、CentOS、Ubuntu、Deepin），日常使用的“Linux系统”均指发行版。
- Linux vs Windows核心优势：稳定高效、免费/低成本、漏洞少易修补、原生支持多用户多任务、权限管控更严格、硬件资源占用低。
 
二、核心操作：终端与Shell
 
1. Shell（命令行交互界面）
 
- 作用：作为用户与内核的“翻译官”，解释执行用户输入的命令，支持编写bash脚本实现自动化操作。
- 常用Shell：默认是 bash （MacOS也默认使用），查看当前Shell：
bash
  
echo $SHELL
 
 
查看系统所有Shell：
bash
  
cat /etc/shells
 
 
2. 终端连接远程服务器
 
通过SSH命令直接登录，格式：
 
bash
  
ssh 用户名@服务器IP  # 示例：ssh root@121.42.11.34
 
 
输入服务器对应用户的密码即可完成连接。
 
3. 命令行基础
 
- 提示符含义： [root@iZm5e8dsxce9ufaic7hi3uZ ~]# 
-  root ：当前登录用户名； iZm5e8dsxce9ufaic7hi3uZ ：主机名； ~ ：当前所在目录（root家目录是 /root ，普通用户是 /home/用户名 ）； # ：表示root权限（普通用户提示符为 $ ）。
- 命令格式： command 参数 ，支持短参数（ ls -a ）、长参数（ ls --all ）、混合参数（ ls --all -l ）。
- 必备快捷键：
- ↑↓：调取历史命令；Tab：自动补全命令/文件路径
- Ctrl+C：强制中止当前运行的命令；Ctrl+L：清屏
- Ctrl+D：关闭当前Shell会话
 
三、文件与目录管理
 
1. 目录结构（根目录 / 为起点）
 
-  /bin ：所有用户可执行的二进制命令文件（如 ls 、 cd ）
-  /etc ：系统核心配置文件目录（如网络、用户配置）
-  /home ：普通用户的家目录（每个用户独立文件夹）
-  /root ：root用户的家目录； /tmp ：临时文件存储目录（重启后清空）
-  /usr ：用户程序与资源目录； /var ：动态文件目录（如日志、数据库文件）
 
2. 核心命令表
 
功能 命令示例 关键参数/说明 
查看当前路径  pwd  直接执行，输出当前所在绝对路径 
列出文件/目录  ls   -a （显示隐藏文件）、 -l （详细列表）、 -h （人类可读大小） 
切换目录  cd 路径   cd / （切到根目录）、 cd ~ （切到家目录）、 cd .. （切到上级目录） 
查看文件内容  cat 文件名 （小文件）、 less 文件名 （大文件）  cat -n （显示行号）； less 中按 q 退出查看 
创建文件/目录  touch 文件名 、 mkdir 目录名   mkdir -p one/two/three （递归创建多级目录） 
复制文件/目录  cp 源路径 目标路径   cp -r 目录1 目录2 （递归复制整个目录） 
移动/重命名  mv 源路径 目标路径   mv file1 file2 （重命名）、 mv file /home （移动） 
删除文件/目录  rm 目标路径   -i （删除前确认）、 -f （强制删除）、 -r （递归删目录，如 rm -rf 目录 ） 
查看命令所在路径  which 命令  示例： which node  查看node命令的安装路径 
 
3. 链接（类似Windows快捷方式）
 
- 硬链接： ln 源文件 链接文件 
- 与源文件共享同一个 inode （文件唯一标识），内容完全同步；删除源文件不影响链接文件，仅支持普通文件。
- 软链接： ln -s 源文件/目录 链接文件 
- 类似快捷方式， inode 与源文件不同；删除源文件后链接失效，支持文件和目录。
 
四、用户与权限管理
 
1. 用户/群组操作（需root权限）
 
- 创建用户： useradd 用户名 ；设置用户密码： passwd 用户名 （输入时密码不显示）
- 删除用户： userdel 用户名 （仅删用户）、 userdel -r 用户名 （删用户+其家目录）
- 切换用户： su 用户名 （如 su root 切换到root）、 sudo 命令 （以root权限执行单条命令，如 sudo ls /root ）
- 群组管理：
- 创建群组： groupadd 群组名 ；删除群组： groupdel 群组名 
- 修改用户所属群组： usermod -g 群组名 用户名 
 
2. 文件权限
 
- 权限格式解读： drwxr-xr-x 
- 第一位：文件类型（ d =目录、 - =普通文件、 l =软链接）
- 后9位分3组（所有者、所属群组、其他用户），每组含 r （读，4）、 w （写，2）、 x （执行，1）
- 修改权限（chmod命令）：
- 数字方式： chmod 740 文件名 （7=4+2+1，所有者rwx；4=4，群组r；0=无权限，其他用户无访问权）
- 字母方式： chmod u+x 文件名 （给所有者加执行权）、 chmod g-r 文件名 （给群组删读权）
 
五、进阶技能
 
1. 进程管理
 
- 查看进程：
-  ps -ef ：查看系统所有进程（显示进程号、用户、命令等）
-  top ：动态刷新进程列表（按CPU/内存排序，按 q 退出）
- 结束进程： kill 进程号 （正常终止）、 kill -9 进程号 （强制终止，如 kill -9 956 ）
- 后台运行进程：命令后加 & （如 cp file1 file2 & ）； nohup 命令 （关闭终端后进程仍运行）
 
2. 网络配置
 
- 查看IP地址： ifconfig （需先安装net-tools工具： yum install net-tools ）
- SSH免密登录（步骤）：
1. 客户机生成密钥对：
bash
  
ssh-keygen  # 一路回车，生成~/.ssh/id_rsa（私钥）和id_rsa.pub（公钥）
 
2. 上传公钥到服务器：
bash
  
ssh-copy-id root@服务器IP  # 输入服务器密码后，公钥自动写入授权文件
 
3. 后续登录：直接 ssh 服务器IP ，无需输入密码。
 
3. Vim编辑器（核心模式）
 
Vim默认进入交互模式，需切换模式操作：
 
- 切换到插入模式：按 i （光标处插入）、 a （光标后插入）
- 切换到命令模式：按 : （底部出现冒号，可输入命令）
- 常用操作：
- 删除： dd （删除当前行）、 dw （删除当前单词）、 x （删除当前字符）
- 复制粘贴： yy （复制当前行）、 p （粘贴到光标后）
- 退出： :q （未修改时退出）、 :wq （保存并退出）、 :q! （强制退出不保存）
 
六、常用命令速查（按场景）
 
- 软件安装/卸载： yum install 软件名 （安装）、 yum remove 软件名 （卸载）
- 查找文件： find /var -name "syslog" （按文件名找）、 find /var -size +10M （找大于10M的文件）
- 文本搜索： grep "关键词" 文件名 （在文件中搜索匹配内容）
- 压缩/解压： tar -zcvf 压缩包.tar.gz 目录 （压缩）、 tar -zxvf 压缩包.tar.gz （解压）
- 系统关机/重启： halt （立即关机）、 reboot （立即重启）
