工具安装过程​
￼
1.
Hackbar安装：先下载谷歌浏览器，然后从https://github.com/0140454/hackbar/releases中下载扩展程序并开启开发者模式然后在其中打开下载好的文件就行​
​
​
￼
￼
￼
￼
￼
￼
​
2.
Burp Suite安装：首先下载java jdk环境，再从https://portswigger.net/官网上下载最新版本，最后从网上获取破解包和注册机就行​
​
￼
￼
￼
￼
￼
￼
​
3.
Linux系统安装：先从VMware虚拟机官网下载VMware虚拟机，然后从https://ubuntu.com/download中下载ubuntu的镜像文件，再从虚拟机中建立系统用下载好的镜像文件​
​
￼
￼
￼
￼
￼
￼
​
￼
linux基础命令的学习笔记：​
￼
1.
command ：命令名，相应功能的英文单词或单词的缩写 ​
2.
• [-options] ：选项，可用来对命令进行控制，也可以省略 ​
3.
• parameter ：传给命令的参数，可以是 零个、一个 或者 多个​
4.
is:查看当前文件夹下的内容​
5.
pwd:查看当前所在文件夹​
6.
cd:切换文件夹​
7.
touch:如果文件不存在，新建文件​
8.
mkdir:创建目录​
9.
rm:删除指定文件​
10.
clear:清屏​
快捷方式​
￼
Ctrl + Alt + T：打开 Shell​
Ctrl + R：查找前面用过的命令，输入命令的一部分字符，会自动匹配，如果不是我们想要的命令，可重复该命令，再次匹配，找到命令后，Enter 直接执行，Ctrl + E 将命令输入到当前行。​
Ctrl + L：清除屏幕，光标回到最左上角。​
Ctrl + C：终止当前在执行的命令。​
Ctrl + U：从当前位置剪切到行首（不包括当前位置）。​
Ctrl + Y：从当前位置剪切到行尾（包括当前位置）。​
Ctrl + W：剪切当前位置左侧的**单词**，这里指连续的英文字母。​
Ctrl + Y：粘贴 Ctrl + U/Y/W 剪切的内容。​
Ctrl + A：将光标放到该行最前面。​
Ctrl + E：将光标放到改行最后面​
Ctrl + D：关闭 Shell​
常见参数​
￼
-a：显示所有文件和目录，包括隐藏文件和目录。​
-l：显示详细列表。​
-h：适合人类阅读的，目前看到是效果是让文件大小更加明显可读（转化为K）。​
-t：按文件最后一次修改时间排序。​
-i：显示文件内容标识，即 inode。（inode 存储的是文件的元信息，而不是文件的实际内容。可以把它理解为文件的"身份证"。​
AI脚本​
￼
import hashlib​
import itertools​
​
def find_md5_with_prefix(prefix, charset="abcdefghijklmnopqrstuvwxyz0123456789", max_length=6):​    
"""​    
穷举指定字符集中的字符串，查找MD5哈希前6位匹配给定前缀的字符串。​    
:param prefix: 目标MD5前缀（6位十六进制字符串）​    
:param charset: 字符串字符集，默认为小写字母和数字​    
:param max_length: 最大字符串长度，默认为6​    
:return: 匹配的字符串，如果未找到则返回None​    
"""​    
for length in range(1, max_length + 1):​        
for candidate in itertools.product(charset, repeat=length):​            
candidate_str = ''.join(candidate)​            
md5_hash = hashlib.md5(candidate_str.encode()).hexdigest()​            
if md5_hash[:6] == prefix:​                
return candidate_str​    
return None​
​
if name == "__main__":​    
target_prefix = "15af95"​    
result = find_md5_with_prefix(target_prefix)​    
if result:​        
print(f"找到字符串: {result}")​    
else:​        
print("未找到匹配的字符串，尝试扩大字符集或增加最大长度。")
