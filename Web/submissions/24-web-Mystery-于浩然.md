#工具
##Hackbar
<img width="1213" height="242" alt="屏幕截图 2025-10-28 234328" src="https://github.com/user-attachments/assets/f8ac7602-b3d5-4df0-a5fd-86bfb2802a32" />
##Burp Suite
<img width="1315" height="960" alt="屏幕截图 2025-10-28 234522" src="https://github.com/user-attachments/assets/6819bda6-dadd-4bc8-b735-eedaef2efe76" />
##AI
<img width="688" height="1214" alt="屏幕截图 2025-10-28 230713" src="https://github.com/user-attachments/assets/e8678540-70fc-4f2e-b2b0-adf94554bda0" />
#题目
##view_source
**直接F12即可**
<img width="2560" height="1600" alt="屏幕截图 2025-10-28 231111" src="https://github.com/user-attachments/assets/4b8f3cd3-7fa0-46d0-a059-10faaa8f8c54" />
##get_post
**在网址后加”？a=1“，回车，获得b=2，在post data中输入b=2，然后execute**
<img width="2559" height="1599" alt="屏幕截图 2025-10-28 233249" src="https://github.com/user-attachments/assets/497a3ec4-f2b9-4d57-a1e5-f08790ea6826" />
##robots
**在网址后面加上”/robots.txt“，获得Disallow，并替换robots.txt**
<img width="1002" height="236" alt="屏幕截图 2025-10-29 000301" src="https://github.com/user-attachments/assets/610bcf3f-945f-4b45-acaf-fbaba26288db" />
<img width="1093" height="173" alt="屏幕截图 2025-10-29 000321" src="https://github.com/user-attachments/assets/84b6f332-e15e-4be7-9eed-adacca51b83f" />
##用ai写一个python脚本，要求找到一个值经过md5加密后的前6位是15af95
```
import hashlib
import random
import string
def find_md5_target(prefix: str = "15af95", length_range: tuple = (6, 12)) -> str:
    chars = string.ascii_letters + string.digits  # 候选字符集（字母+数字）
    count = 0  # 计数，方便查看执行进度
    while True:
        # 生成随机长度的字符串
        str_len = random.randint(*length_range)
        random_str = ''.join(random.choice(chars) for _ in range(str_len))
        # MD5加密（小写）
        md5_result = hashlib.md5(random_str.encode()).hexdigest()
        count += 1
        if count % 100000 == 0:
            print(f"已尝试 {count:,} 次，仍在查找...")
        # 校验前6位是否匹配
        if md5_result.startswith(prefix):
            print(f"\n找到目标！")
            print(f"原始字符串：{random_str}")
            print(f"MD5值：{md5_result}")
            return random_str
# 执行查找（可能需要几秒到几分钟，取决于运气）
if __name__ == "__main__":
    find_md5_target()
```
<img width="831" height="232" alt="屏幕截图 2025-10-29 002459" src="https://github.com/user-attachments/assets/087eeddf-c2bf-466d-85a2-9eef3e6390b5" />
#虚拟机
##VMware
<img width="1475" height="970" alt="屏幕截图 2025-10-29 000528" src="https://github.com/user-attachments/assets/2a4643be-a2f6-4110-89b8-d5effbd8ba66" />
##Kali Linux
<img width="1474" height="976" alt="屏幕截图 2025-10-29 000644" src="https://github.com/user-attachments/assets/fb2a60be-7fdd-4956-a57f-b6f066b0b189" />
#Linux指令
-Ctrl + R ：用于查找使用过的命令（history命令用于列出之前使用过的所有命令，然后输入!命令加上编号 (!2) 就可以直接执行该历史命令）
-Ctrl + L：清除屏幕并将当前行移到页面顶部
-Ctrl + C：中止当前正在执行的命令
-Ctrl + U：从光标位置剪切到行首
-Ctrl + K：从光标位置剪切到行尾
-Ctrl + W：剪切光标左侧的一个单词
-Ctrl + Y：粘贴Ctrl + U | K | Y剪切的命令
-Ctrl + A：光标跳到命令行的开头
-Ctrl + E：光标跳到命令行的结尾；
-Ctrl + D：关闭Shell会话
-pwd:显示当前目录的路径  
-ls:列出文件和目录，它是Linux最常用的命令之一
-du:列举目录大小信息
 -【常用参数】
 -h 适合人类阅读的；
 -a同时列举出目录下文件的大小信息；
 -s只显示总计大小，不显示具体信息。
 -a显示所有文件和目录包括隐藏的
 -l显示详细列表
 -h适合人类阅读的
 -t按文件最近一次修改时间排序
 -i显示文件的inode（inode是文件内容的标识）
-cd / --> 跳转到根目录  
-cd ~ --> 跳转到家目录  
-cd .. --> 跳转到上级目录  
-cd ./home --> 跳转到当前目录的home目录下  
-cd /home/lion --> 跳转到根目录下的home目录下的lion目录  
-cd --> 不添加任何参数，也是回到家目录  
-du:列举目录大小信息。
 -【常用参数】
 -h 适合人类阅读的；
 -a同时列举出目录下文件的大小信息；
 -s只显示总计大小，不显示具体信息。
-cat：一次性显示文件所有内容，更适合查看小的文件。  
-n显示行号。  
-空格键：前进一页（一个屏幕）；
-b 键：后退一页；
-回车键：前进一行；
-y 键：后退一行；
-上下键：回退或前进一行；
-d 键：前进半页；
-u 键：后退半页；
-q 键：停止读取文件，中止less命令；
-= 键：显示当前页面的内容是文件中的第几行到第几行以及一些其它关于本页内容的详细信息；
-h 键：显示帮助文档；
-/ 键：进入搜索模式后，按 n 键跳到一个符合项目，按 N 键跳到上一个符合项目，同时也可以输入正则表达式匹配。
-tail：显示文件的结尾几行（默认是 10 行）  
 -【参数】
 -n指定行数tail cloud-init.log -n 2
 -f会每过 1 秒检查下文件是否有更新内容，也可以用 -s 参数指定间隔时间tail -f -s 4 xxx.log
-touch：创建一个文件  
-mkdir：创建一个目录  
 -【常用参数】
 -p递归的创建目录结构mkdir -p one/two/three
-cp：拷贝文件和目录-r递归的拷贝，常用来拷贝一整个目录mv：移动（重命名）文件或目录，与 cp 命令用法相似。  
-rm：删除文件和目录，由于 Linux 下没有回收站，一旦删除非常难恢复，因此需要谨慎操作
 -【常用参数】
 -i向用户确认是否删除；
 -f文件强制删除；
 -r递归删除文件夹，著名的删除操作 rm -rf。
-ln：英文 Link 的缩写，表示创建链接。  
