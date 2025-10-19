web-24-felix

# 工具

## Hackber

![](https://raw.githubusercontent.com/felix-zjh/TuChuang/main/img/1760786985599-29.png)

## **Burp Suite** 

![](https://raw.githubusercontent.com/felix-zjh/TuChuang/main/img/1760786985600-30.png)

# 题目

## **view_source**

F12直接可以找到flag

![](https://raw.githubusercontent.com/felix-zjh/TuChuang/main/img/1760786985600-31.png)

## **get_post**

第一步直接在网址后面加上/?a=1回车即可

第二部先用Burpsuite拦截到该请求信息，让后转到重放器，将get改为post，再将请求体格式更改，最后传递参数发送即可得到flag

![](https://raw.githubusercontent.com/felix-zjh/TuChuang/main/img/1760786985600-32.png)

## robots

robots.txt是一种文本文件，**用于告知搜索引擎爬虫哪些页面可以被抓取、哪些页面不应被抓取**

直接get找到不应被抓取的页面

![](https://raw.githubusercontent.com/felix-zjh/TuChuang/main/img/1760786985600-33.png)

再次get就得到了flag

![](https://raw.githubusercontent.com/felix-zjh/TuChuang/main/img/1760786985600-34.png)

## AI编写的程序

使用多线程加速

```
import hashlib
import threading
import time

class MD5Finder:
    def __init__(self, prefix):
        self.prefix = prefix.lower()
        self.found = False
        self.result = None
        self.counter = 0
        self.lock = threading.Lock()
        self.start_time = time.time()
    
    def worker(self, start, step):
        """工作线程函数"""
        current = start
        while not self.found:
            test_str = str(current)
            md5_hash = hashlib.md5(test_str.encode()).hexdigest()
            
            if md5_hash[:6] == self.prefix:
                with self.lock:
                    if not self.found:  # 双重检查防止重复
                        self.found = True
                        self.result = (test_str, md5_hash)
                        return
            
            # 更新计数器
            if current % 1000 == 0:
                with self.lock:
                    self.counter += 1000
            
            current += step
    
    def find(self, num_threads=4):
        """使用多线程查找"""
        print(f"使用 {num_threads} 个线程寻找MD5前6位为 '{self.prefix}' 的值...")
        
        threads = []
        for i in range(num_threads):
            thread = threading.Thread(target=self.worker, args=(i, num_threads))
            threads.append(thread)
            thread.start()
        
        # 显示进度
        last_count = 0
        while not self.found:
            time.sleep(1)
            current_count = self.counter
            elapsed = time.time() - self.start_time
            rate = (current_count - last_count) / 1.0  # 每秒速度
            last_count = current_count
            
            print(f"已尝试: {current_count} 次, 速度: {rate:.0f} 次/秒", end='\r')
        
        # 等待所有线程结束
        for thread in threads:
            thread.join()
        
        if self.result:
            elapsed = time.time() - self.start_time
            print(f"\n找到匹配项！")
            print(f"原值: {self.result[0]}")
            print(f"MD5哈希: {self.result[1]}")
            print(f"耗时: {elapsed:.2f} 秒")
            print(f"尝试次数: {self.counter}")
            return self.result

# 使用方法
if __name__ == "__main__":
    finder = MD5Finder("15af95")
    result = finder.find(num_threads=8)  # 使用8个线程
```





# Linux

## 环境搭建

用VMware虚拟机搭建的，更新了源，配置了共享文件夹

![](https://raw.githubusercontent.com/felix-zjh/TuChuang/main/img/1760786985600-35.png)

## 基础知识

### **快捷方式**

命令或参数仅需输入前几位就可以用 Tab 键补全；

Ctrl + R ：用于查找使用过的命令（history命令用于列出之前使用过的所有命令，然后输入!命令加上编号 (!2) 就可以直接执行该历史命令）；

Ctrl + L：清除屏幕并将当前行移到页面顶部；

Ctrl + C：中止当前正在执行的命令；

Ctrl + U：从光标位置剪切到行首；

Ctrl + K：从光标位置剪切到行尾；

Ctrl + W：剪切光标左侧的一个单词；

Ctrl + Y：粘贴Ctrl + U | K | Y剪切的命令；

Ctrl + A：光标跳到命令行的开头；

Ctrl + E：光标跳到命令行的结尾；

Ctrl + D：关闭Shell会话；

### **查看路径、**

**pwd**:显示当前目录的路径

**which**：查看命令的可执行文件所在路径

### **浏览和切换目录**

**ls**:列出文件和目录，它是`Linux`最常用的命令之一。

【**常用参数**】

`-a`显示所有文件和目录包括隐藏的

`-l`显示详细列表

`-h`适合人类阅读的

`-t`按文件最近一次修改时间排序

`-i`显示文件的`inode`（`inode`是文件内容的标识）

**cd**：`cd`是英语 `change directory`的缩写，表示切换目录

cd / --> 跳转到根目录  

cd ~ --> 跳转到家目录  

cd .. --> 跳转到上级目录  

cd ./home --> 跳转到当前目录的home目录下  

cd /home/lion --> 跳转到根目录下的home目录下的lion目录  

cd --> 不添加任何参数，也是回到家目录

[**注意**] 输入 `cd /ho`单次 `tab`键会自动补全路径 + 两次 `tab`键会列出所有可能的目录列表

**du**:列举目录大小信息。

【**常用参数**】

`-h` 适合人类阅读的；

`-a`同时列举出目录下文件的大小信息；

`-s`只显示总计大小，不显示具体信息。

### **浏览和创建文件**

**cat**：一次性显示文件所有内容，更适合查看小的文件。

【**常用参数**】

`-n`显示行号。

**less**：分页显示文件内容，更适合查看大的文件。

【快捷操作】

空格键：前进一页（一个屏幕）；

b 键：后退一页；

回车键：前进一行；

y 键：后退一行；

上下键：回退或前进一行；

d 键：前进半页；

u 键：后退半页；

q 键：停止读取文件，中止less命令；

= 键：显示当前页面的内容是文件中的第几行到第几行以及一些其它关于本页内容的详细信息；

h 键：显示帮助文档；

/ 键：进入搜索模式后，按 n 键跳到一个符合项目，按 N 键跳到上一个符合项目，同时也可以输入正则表达式匹配。

**head**：显示文件的开头几行（默认是 10 行

【**参数**】

```
-n` 指定行数`head cloud-init.log -n 2
```

**tail**：显示文件的结尾几行（默认是 10 行

【**参数**】

```
-n`指定行数`tail cloud-init.log -n 2
-f`会每过 1 秒检查下文件是否有更新内容，也可以用 -s 参数指定间隔时间`tail -f -s 4 xxx.log
```

**touch**：创建一个文件

**mkdir**：创建一个目录

【**常用参数**】

```
-p`递归的创建目录结构`mkdir -p one/two/three
```

### **文件的复制和移动**

**cp**：拷贝文件和目录

【用法】

cp file file_copy --> file 是目标文件，file_copy 是拷贝出来的文件  

cp file one --> 把 file 文件拷贝到 one 目录下，并且文件名依然为 file  

cp file one/file_copy --> 把 file 文件拷贝到 one 目录下，文件名为file_copy  

cp *.txt folder --> 把当前目录下所有 txt 文件拷贝到 folder 目录下 

【**常用参数**】

`-r`递归的拷贝，常用来拷贝一整个目录

mv：移动（重命名）文件或目录，与 cp 命令用法相似。

【用法】

mv file one --> 将 file 文件移动到 one 目录下  

mv new_folder one --> 将 new_folder 文件夹移动到one目录下  

mv *.txt folder --> 把当前目录下所有 txt 文件移动到 folder 目录下  

mv file new_file --> file 文件重命名为 new_file 

### **文件的删除和链接**

**rm**：删除文件和目录，由于 Linux 下没有回收站，一旦删除非常难恢复，因此需要谨慎操作

【用法】

rm new_file  --> 删除 new_file 文件  

rm f1 f2 f3  --> 同时删除 f1 f2 f3 3个文件  

【常用参数】

`-i`向用户确认是否删除；

`-f`文件强制删除；

```
-r`递归删除文件夹，著名的删除操作 `rm -rf
```

**ln**：英文 Link 的缩写，表示创建链接

### 组群和用户

**userdel**:删除用户

**su**：切换用户

**groups**：查看用户所在群组

**usermod**：用于修改用户的账户

usermod：用于修改用户的账户。

【常用参数】

-l对用户重命名。需要注意的是 /home中的用户家目录的名字不会改变，需要手动修改。

-g修改用户所在的群组，例如 usermod -g friends lion 修改 lion 用户的群组为 friends 。

-G一次性让用户添加多个群组，例如 usermod -G friends,foo,bar lion 。

-a -G会让你离开原先的群组，如果你不想这样做的话，就得再添加 -a参数，意味着 append 追加的意思。

**chgrp**：用于修改文件的群组

**chown**：改变文件的所有者，需要 root 身份才能运行

【用法】

chown lion file.txt --> 把其它用户创建的file.txt转让给lion用户  

chown lion:bar file.txt --> 把file.txt的用户改为lion，群组改为bar

【**常用参数**】

- `-R`可以递归地修改文件访问权限，例如`chmod -R 777 /home/lion`

### 文件权限

**chmod**：修改访问权限

【**常用参数**】

- `-R`可以递归地修改文件访问权限，例如`chmod -R 777 /home/lion`

drwxr-xr-x表示文件或目录的权限。

【解读】

d ：表示目录，就是说这是一个目录，普通文件是 - ，链接是 l 。

r ：read表示文件可读。

w ：write表示文件可写，一般有写的权限，就有删除的权限。

x ：execute表示文件可执行。

-：表示没有相应权限

用字母来分配权限

u：user 的缩写，用户的意思，表示所有者。

G ：group 的缩写，群组的意思，表示群组用户。

o ：other 的缩写，其它的意思，表示其它用户。

a ：all 的缩写，所有的意思，表示所有用户。

\+ ：加号，表示添加权限。

\- ：减号，表示去除权限

= ：等于号，表示分配权限。

例：chmod u+rx file --> 文件file的所有者增加读和运行的权限

### **查找文件**

**locate**：搜索包含关键字的所有文件和目录。后接需要查找的文件名，也可以用正则表达式

**find**：用于查找文件，它会去遍历你的实际硬盘进行查找，而且它允许我们对每个找到的文件进行后续操作

【用法】

find <何处> <何物> <做什么> 

[**注意**] find 命令只会查找完全符合 “何物” 字符串的文件，而 locate 会查找所有包含关键字的文件

### 网络相关

- `ping`：测试与目标主机的网络连接。
- `ifconfig` / `ip addr`：查看和配置网络接口信息（现代系统推荐使用 `ip` 命令）。
- `ssh`：远程登录到另一台 Linux 主机。
  - `ssh username@host_ip`