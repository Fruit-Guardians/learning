## 工具

### hackbar插件

在浏览器扩展里面搜索添加即可，使用时右键选择“检查”

![1760578728255](https://gitee.com/yu-xiangshuo/image-library/raw/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-16%20093844.png)

### bp

寻找压缩包，进行破解

![1760579426413](https://gitee.com/yu-xiangshuo/image-library/raw/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-16%20095017.png)

设置代理：在火狐浏览器搜索foxyproxy，添加后设置代理![1760579827984](https://gitee.com/yu-xiangshuo/image-library/raw/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-16%20095640.png)



![屏幕截图 2025-10-16 095230](https://gitee.com/yu-xiangshuo/image-library/raw/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-16%20095230.png)

## writeup

### 攻防世界view_source

禁用右键可以使用F12，或者CTRL+u等方法查看源代码寻找flag![1760580391104](https://gitee.com/yu-xiangshuo/image-library/raw/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-16%20100344.png)

攻防世界get_post

先使用URL后面拼接？a=1提交变量然后打开 hackbar提交b=2![1760580713114](https://gitee.com/yu-xiangshuo/image-library/raw/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-16%20101141.png)

### 脚本

![1760580940961](https://gitee.com/yu-xiangshuo/image-library/raw/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-16%20101538.png)![1760580959238](https://gitee.com/yu-xiangshuo/image-library/raw/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-16%20101432.png)

## linux

#### 搭建环境

下载VMware，获取kali镜像。创建虚拟机安装 kali![1760582953041](https://gitee.com/yu-xiangshuo/image-library/raw/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-16%20104908.png)

#### Linux笔记

##### 一、文件与目录操作（核心高频）

1. **ls**：列出目录内容，查看文件/文件夹
   - `ls`：默认列出当前目录可见文件
   - `ls -l`：显示详细信息（权限、大小、修改时间等）
   - `ls -a`：显示隐藏文件（以“.”开头的文件）
   - `ls /目标路径`：查看指定目录内容，如`ls /home`
2. **cd**：切换工作目录，移动操作位置
   - `cd 目标路径`：切换到指定目录，如`cd /usr/local`
   - `cd ..`：回到上一级目录
   - `cd ~`：快速切换到当前用户的家目录
   - `cd -`：回到上一次所在的目录
3. **pwd**：显示当前所在目录的完整路径，避免“迷路”
   - 直接输入`pwd`即可，无额外参数
4. **mkdir**：创建新目录
   - `mkdir 目录名`：创建单个目录，如`mkdir test`
   - `mkdir -p 多级目录`：递归创建嵌套目录，如`mkdir -p a/b/c`
5. **rm**：删除文件/目录（慎用，删除后难恢复）
   - `rm 文件名`：删除单个文件，如`rm file.txt`
   - `rm -r 目录名`：删除目录及内部所有内容，如`rm -r test`
   - `rm -f 文件名`：强制删除，不弹出确认提示
   - `rm -rf 目录名`：强制删除目录，高危命令，确认后再执行
6. **cp**：复制文件/目录
   - `cp 源文件 目标位置`：复制文件，如`cp file1.txt /home`
   - `cp -r 源目录 目标位置`：复制目录及内容，如`cp -r test /usr`
7. **mv**：移动文件/目录，或重命名
   - `mv 源文件 新文件名`：重命名，如`mv file1.txt file2.txt`
   - `mv 源文件/目录 目标路径`：移动，如`mv file.txt /home/test`
8. **touch**：创建空文件，或更新文件时间戳
   - `touch 文件名`：创建空文件，如`touch new.txt`
9. **cat**：查看文件内容（适合短文件）
   - `cat 文件名`：直接显示全部内容，如`cat file.txt`
   - `cat -n 文件名`：显示内容并标注行号
10. **文本编辑**：修改文件内容
    - `nano 文件名`：简单编辑器，上手快，如`nano file.txt`（Ctrl+O保存，Ctrl+X退出）
    - `vim 文件名`：功能强，需简单学习（按`i`进入编辑模式，按`Esc`后输入`:wq`保存退出）

##### 二、系统信息与管理（查看状态）

1. **uname**：查看系统内核与版本信息
   - `uname -a`：显示完整系统信息（内核版本、主机名、架构等）
   - `uname -r`：仅显示内核版本
2. **df**：查看磁盘空间使用情况
   - `df -h`：以“GB/MB”等易读格式显示，如`df -h`
3. **free**：查看内存使用情况
   - `free -h`：以易读格式显示内存（总内存、已用、空闲）
4. **top/htop**：查看进程动态（实时监控）
   - `top`：默认实时显示进程，按`q`退出
   - `htop`：界面更友好（部分系统需先安装：`sudo apt install htop`）
5. **ps**：查看当前运行的进程
   - `ps aux`：显示所有进程的详细信息
   - `ps aux | grep 关键词`：筛选特定进程，如`ps aux | grep ssh`
6. **kill**：终止指定进程
   - `kill 进程ID`：正常终止进程，如`kill 1234`（进程ID可通过`ps`查看）
   - `kill -9 进程ID`：强制终止无响应进程
7. **sudo**：以管理员（root）权限执行命令
   - `sudo 目标命令`：如`sudo apt update`，执行时需输入当前用户密码

##### 三、权限管理（控制访问）

1. **chmod**：修改文件/目录的权限（r=读、w=写、x=执行）
   - 数字权限：`chmod 755 文件名`（所有者rwx，其他用户rx）
   - 符号权限：`chmod +x 脚本名`（给所有用户添加执行权限，如`chmod +x run.sh`）
2. **chown**：修改文件/目录的所有者和所属组
   - `chown 用户名:组名 文件名`：如`chown user:group file.txt`

##### 四、网络操作（连接与测试）

1. **ping**：测试网络连通性
   - `ping 目标IP/域名`：如`ping www.baidu.com`（按`Ctrl+C`停止）
2. **查看网络接口**：了解IP、网卡信息
   - `ifconfig`：旧版命令，部分系统可用
   - `ip addr`：新版命令，显示所有网卡的IP、MAC等信息
3. **netstat**：查看网络连接与端口
   - `netstat -tuln`：显示所有正在监听的端口（t=TCP，u=UDP，l=监听，n=数字显示）

##### 五、软件包管理

1. **apt**：安装、卸载、更新软件
   - `sudo apt update`：更新软件源列表（获取最新软件版本信息）
   - `sudo apt install 软件名`：安装软件，如`sudo apt install firefox`
   - `sudo apt remove 软件名`：卸载软件，如`sudo apt remove firefox`
   - `sudo apt upgrade`：升级已安装的所有软件

## 其他学习笔记

### http协议

超文本传输协议，用于在客户端与服务器间传输超文本（包含超链接的文本，允许用户从当前内容直接跳转到其他内容）的应用层协议。

#### 特点：

本身不记录客户端的历史请求信息，每次请求都是独立的。

每次请求/响应后客户端与服务器立刻断开联系

请求/响应内容均是明文传输，因此敏感场景通常使用https协议

#### url结构：

url：用户发送请求时，用于定位目标资源的地址标签

一个完整的http的url包括六个部分，部分可选但是顺序固定。如：[https://www.example.com:8080/path?query=123#fragment](https://www.example.com:8080/path?query=123#fragment)

1. **协议**（必须）：`https`，指定通信规则（也可以是`http`）。
2. **域名**（必须）：`www.example.com`，服务器的网络地址标识，用来找到对应服务器。
3. **端口**：`8080`，**<u>默认端口`http`为 80，`https`为 443</u>**，可省略，用来连接服务器的指定服务。
4. **路径**（必须）：`/path`，指定服务器上的资源位置。
5. **查询参数**：`?query=123`，向服务器传递额外信息，格式为 “键 = 值”。
6. **锚点**：`#fragment`，用于定位页面内的具体位置，不会发送到服务器。

#### http请求报文：

请求行：包含请求方法、URL、HTTP 版本，例如`GET /index.html HTTP/1.1`。

请求头：键值对形式的附加信息，常见字段如下：

- `Host`：指定服务器域名，如`Host: www.example.com`。
- `User-Agent`：标识客户端（浏览器 / 设备）信息，如`Mozilla/5.0 (Windows NT 10.0; Win64; x64) Chrome/118.0.0.0`。
- `Content-Type`：请求体的格式，如`application/json`（JSON 格式）、`application/x-www-form-urlencoded`（表单格式）。

请求体：可选，仅在需要向服务器提交数据时存在（如 POST 请求），存放表单数据、JSON 字符串等。

#### 常见请求方法：

| 方法   | 作用                                               | 是否有请求体                     |
| ------ | -------------------------------------------------- | -------------------------------- |
| GET    | 获取服务器资源（如浏览页面、查询数据）             | 无（数据通过 URL 查询参数传递）  |
| POST   | 向服务器提交数据（如提交表单、上传文件）           | 有（数据存放在请求体中，更安全） |
| PUT    | 全量更新服务器资源（如更新用户信息）               | 有                               |
| DELETE | 删除服务器资源（如删除一条记录）                   | 无                               |
| HEAD   | 仅获取响应头，不返回响应体（用于检查资源是否存在） | 无                               |

#### 响应报文：

**状态行**：包含 HTTP 版本、状态码、状态描述，例如`HTTP/1.1 200 OK`。

响应头：服务器返回的附加信息，常见字段如下：

- `Content-Type`：响应体的格式，如`text/html`（HTML 页面）、`image/jpeg`（图片）。
- `Content-Length`：响应体的字节大小。
- `Set-Cookie`：服务器向客户端设置 Cookie，用于记录状态。

**响应体**：服务器返回的实际数据，如 HTML 代码、JSON 数据、图片二进制流等。

#### 常见状态码：

1开头：请求已经接收，继续处理（100）

2开头：请求正常处理完成（200 OK     204 No Content成功但是无响应体）

3开头：需要进一步操作才能获取资源

4开头：客户端错误，请求存在错误，服务器无法处理（400 请求参数错误	401 未登录	403 权限不足	404 资源不存在）

5开头：服务器错误

#### 更安全的https：

http+SSL/TLS,通过加密保护数据传输安全

| 对比维度   | HTTP                                                 | HTTPS                                                        |
| ---------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| 端口       | 默认用 80 端口，URL 里可省略（比如`http://xxx.com`） | 默认用 443 端口，URL 里可省略（比如`https://xxx.com`）       |
| 安全性     | 数据明文传输，像寄明信片，中间可能被偷看、篡改       | 数据加密传输，像寄带锁的快递，只有收件方（服务器）能解开     |
| 速度       | 不用额外加密解密，首次打开略快一点                   | 首次连接要 “握手” 验证加密（类似互相确认身份），会慢一点点，后续访问速度差不多 |
| 证书       | 不需要任何证书，随便建个网站就能用                   | 必须有 SSL 证书（可申请免费的，比如 Let's Encrypt），没有证书浏览器会提示 “不安全” |
| 浏览器提示 | 地址栏一般没特殊标识，部分浏览器会标 “不安全”        | 地址栏会显示小锁图标，点锁能看到证书信息，证明网站是真的     |
