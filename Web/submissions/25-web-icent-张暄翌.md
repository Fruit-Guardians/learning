# 工具

## HackBar

下载**Firefox**火狐浏览器，点击右上角的**拓展**  
点击**管理拓展**，搜索**HackBar**  
下载名为**HackBar**的组件

## BurpStuite

通过学长分享的网址https://www.52pojie.cn/forum.php?mod=viewthread&tid=2005151&highlight=burpsuite  
用**123云盘**提取并解压了分享的BurpStuite文件  
> 分享的文件自带*jdk*  
> 文件中有*注册机*，可以获取*密钥*与*Activation Response*

打开**BurpStuite**,输入密钥，点击**手动激活**  
输入获取的**Activation Response**完成激活

## AI

选择了豆包、Deepseek等较为主流的AI软件

# Linux

## VMware 虚拟机

去**broadcom**官网 https://www.broadcom.com/ 注册一个账户  
注册完成后自动跳转至**Home**界面，点击上方的**Product**  
跳转至**Product**界面，再点击上方的**Product**  
找到**VMware Products**，再点击**Fusion and Workstation**  
点击**downlode now**自动跳转至**my downlodes**  
找到**VMware Workstation Pro**下载适合自己系统的**虚拟机**  

## 配置Linux环境

进入下载网站**Downlode**https://ubuntu.com/download  
找到**Mirror**，选择一个中国的镜像网站  
> 我选择了https://mirrors.tuna.tsinghua.edu.cn/ubuntu-releases/

下载一个适合的版本
> 我选择的版本是*Ubuntu 24.04 LTS*
>> 安装了*uhuntu-24.04.3-desktop-amd64.iso*

将安装的文件提供给**VMware 虚拟机**  
输入用户名和密码，按照说明点击即可

# 攻防世界习题

## view_source

进入网站,发现显示"Flag is not here"  
发现如题目所说右键无法使用  
打开Burpsutie,进入*代理*,进入*拦截*,打开*内嵌浏览器*  
在这个浏览器上登入刚刚的网址,返回Burpsutie,进入*HTTP历史记录*
找到 http://61.147.171.103:57307 这一条  
查看它的响应,发现第27行的 <!-- Cyberpeace{B564E7137974CB362A3F90F305EA5045} -->  
找到了flag,结束

![攻防世界1](https://img2024.cnblogs.com/blog/3722679/202511/3722679-20251101213110594-868170877.png)

## get_post
进入网站,发现显示"请用GET方式提交一个名为a,值为1的变量"  
打开Burpsutie,也用*内嵌浏览器*登入该网站  
打开拦截，再次发送GET请求,发现请求被成功拦截了  
更改GET,在*GET /*后写上"?a=1",放行  
查看网站,发现多了一条"请再以POST方式随便提交一个名为b,值为2的变量"
在*HTTP历史记录*中找到刚刚的请求,点击右键,点击*发送到Repeater*  
将"GET"改成"POST",并加上请求头"Content-Type: application/x-www-form-urlencoded"  
在请求体添加"b=2",点击发送  
查看它的响应，发现出现Cyberpeace{77968C8A7FC568EF10D4AD9475F8F103}  
找到了flag，结束

![攻防世界2](https://img2024.cnblogs.com/blog/3722679/202511/3722679-20251101213124369-1640589783.png)

# AI编写python脚本

将"写一个python脚本，要求找到一个值经过md5加密后的前6位是15af95"的要求提交给deepseek  
deepseek的结果 
 
import hashlib
import itertools
import string
import time

def find_md5_with_prefix(target_prefix, max_length=8, charset=None):
    """
    寻找MD5哈希值前6位为指定前缀的字符串
    
    参数:
    target_prefix (str): 目标MD5前缀（6位十六进制）
    max_length (int): 搜索的最大字符串长度
    charset (str): 使用的字符集，默认为数字+小写字母
    """
    if charset is None:
        charset = string.digits + string.ascii_lowercase
    
    target_prefix = target_prefix.lower()
    attempts = 0
    start_time = time.time()
    
    print(f"开始搜索MD5前缀为 '{target_prefix}' 的字符串...")
    print(f"字符集: {charset}")
    print(f"最大长度: {max_length}")
    print("-" * 50)
    
    # 尝试不同长度的字符串
    for length in range(1, max_length + 1):
        print(f"正在尝试长度为 {length} 的字符串...")
        
        # 生成所有可能的组合
        for combo in itertools.product(charset, repeat=length):
            text = ''.join(combo)
            attempts += 1
            
            # 计算MD5
            md5_hash = hashlib.md5(text.encode('utf-8')).hexdigest()
            
            # 检查前缀
            if md5_hash[:6] == target_prefix:
                end_time = time.time()
                elapsed = end_time - start_time
                
                print("\n" + "=" * 50)
                print("🎉 找到匹配的字符串!")
                print(f"原始字符串: {text}")
                print(f"MD5哈希值: {md5_hash}")
                print(f"尝试次数: {attempts:,}")
                print(f"耗时: {elapsed:.2f} 秒")
                print(f"速度: {attempts/elapsed:,.0f} 次/秒")
                print("=" * 50)
                return text, md5_hash
            
            # 每100万次显示进度
            if attempts % 1000000 == 0:
                print(f"  已尝试 {attempts:,} 次组合...")
    
    print(f"\n在长度 {max_length} 内未找到匹配的字符串")
    return None, None

def brute_force_specific_charset():
    """使用特定字符集进行暴力破解"""
    target_prefix = "15af95"
    
    # 方法1: 先尝试纯数字
    print("方法1: 尝试纯数字")
    result, md5_hash = find_md5_with_prefix(target_prefix, max_length=8, charset=string.digits)
    
    if result is None:
        # 方法2: 尝试数字+小写字母
        print("\n方法2: 尝试数字+小写字母")
        result, md5_hash = find_md5_with_prefix(target_prefix, max_length=6, 
                                              charset=string.digits + string.ascii_lowercase)
    
    if result is None:
        # 方法3: 尝试所有可打印字符
        print("\n方法3: 尝试所有可打印字符")
        result, md5_hash = find_md5_with_prefix(target_prefix, max_length=5, 
                                              charset=string.printable[:-5])  # 排除一些特殊字符
    
    return result, md5_hash

def verify_solution(text, expected_prefix):
    """验证找到的解决方案"""
    if text:
        md5_hash = hashlib.md5(text.encode('utf-8')).hexdigest()
        print(f"\n验证结果:")
        print(f"输入: {text}")
        print(f"MD5: {md5_hash}")
        print(f"前6位: {md5_hash[:6]}")
        print(f"匹配目标: {expected_prefix}")
        print(f"验证: {'✅ 成功' if md5_hash[:6] == expected_prefix else '❌ 失败'}")
        return md5_hash[:6] == expected_prefix
    return False

if __name__ == "__main__":
    target_prefix = "15af95"
    
    print("MD5前缀碰撞搜索工具")
    print("目标: 找到MD5前6位为 '15af95' 的字符串")
    print("=" * 60)
    
    # 执行搜索
    result, md5_hash = brute_force_specific_charset()
    
    # 验证结果
    if result:
        verify_solution(result, target_prefix)
        
        # 保存结果到文件
        with open("md5_solution.txt", "w") as f:
            f.write(f"目标前缀: {target_prefix}\n")
            f.write(f"找到的字符串: {result}\n")
            f.write(f"完整MD5: {md5_hash}\n")
        print(f"\n结果已保存到 'md5_solution.txt'")
    else:
        print("\n❌ 未找到解决方案，请尝试:")
        print("   - 增加 max_length 参数")
        print("   - 扩大字符集范围")
        print("   - 使用更强大的计算资源")

# 笔记

## Linux基础命令

### 快捷键
CTRL + R:用于**查找**使用过的命令  
Ctrl + L:清除屏幕，并将当前行移到屏幕**顶部**  
Ctrl + C:**中止**正在执行的命令  
Ctrl + U:从光标位置剪切到**行首**  
Ctrl + K:从光标位置剪切到**行尾**  
Ctrl + W:剪切光标**左侧的一个单词**  
Ctrl + Y:粘贴  
Ctrl + A:将光标移至命令行**开头**  
Ctrl + E:将光标移至命令行**结尾**  
Ctrl + D:关闭Shell(对话框)  

### 文件的组织

/:表示根目录 
> 根目录有且只有一个

bin:表示二进制文件  
> binary(二进制的)的缩写
> bin目录包含了会被所有用户使用的可执行程序  

boot:包含与Linux启动密切相关的文件  
dev:表示设备  
> device(设备)的缩写
> dev里的子目录，每一个都对应一个外设(比如光盘驱动器文件)

etc:包含系统的配置文件  
home:用户的私人目录
> 类似Windous的"我的文档"

lib:表示库，包含被程序调用的文件  
> library(资料库)的缩写

media:表示媒体，可以访问外设中的内容  
>如USB盘，SD卡等可移动的外设

mut:表示挂载
> mount(镶嵌)的缩写
> 类似media，一般表示临时挂载的一些装置

opt:表示可选的应用软件包
> optional application software package(可选应用软件包)的缩写
> 用于安装第三方软件与插件

root:超集用户*root*的家目录
sbin:表示系统二进制文件
> System binary(系统二进制)的缩写
> 包含系统级的重要可执行程序

srv:表示服务
> service(服务)的缩写
> 包含网络服务启动后所需要取用的数据

mp:表示临时的
> temporary(临时的)的缩写
> 普通用户和程序存放临时文件的地方

usr:表示Unix操作系统软件资源
> Unix Software Resource(Unix软件资源)的缩写
> usr 目录是最大的目录之一，安装了大部分用户要调用的程序

var:表示动态的
> variable(动态的)的缩写
> 通常包含程序的数据(如 log 文件)

### 命令

#### 查看路径

pwd:显示当前目录的路径  
which:查看命令的可执行命令所在的文件  
> Linux的每一条命令实质上也对应着一个可执行程序
>> 在终端输入命令按下回车时,就执行了对应的程序
>>> which命令本身对应的程序也在Linux中

#### 浏览和切换目录
ls:列出文件和目录
> 是Linux最常用的命令之一
>>常用参数
>>> -a:显示所有文件和目录(包括隐藏)
>>> -l:显示详细列表
>>> -h:适合人类阅读的
>>> -t:令文件按最近一次修改时间排序
>>> -i:显示文件的 inode (文件内容的标识)

cd:切换目录
> change directory(切换目录)的缩写
>> cd /:跳转到根目录
>> cd ~:跳转到家目录
>> cd ..:跳转到上级目录
>> cd ./home:跳转到当前目录的home目录下
>> cd /home/lion:跳转到根目录下的home名录下的lion目录
>> cd:不添加任何参数，也是回到家目录
>>> 输入cd /ho
>>>> **单击***tab*会自动补全路径
>>>> **双击***tab*会列出所有可能的目录列表

du:列举目录大小信息
> 常用参数
>> -h:适合人类阅读的
>> -a:同时列举出目录下文件的大小信息
>> -s:只显示总计大小,不显示具体信息

#### 浏览和创建文件

cat:一次性显示文件所有内容
> 更适合查看小文件
>> 常用参数
>>> -n:显示行号

less:分页显示文件内容
> 更适合查看大文件
>> 快捷操作
>>> 空格键：前进一页(一个屏幕)
>>> b键:后退一页
>>> 回车键:前进一行
>>> y键:后退一行
>>> ↑键与↓键:回退或前进一行
>>> d键:前进半页
>>> u键:后退半页
>>> q键:停止读取文件,中止 less 命令
>>> =键:显示当前内容是文件的第几行到第几行以及一些其他关于本页内容的详细信息
>>> h键:显示帮助文档
>>> /键:进入搜索(查找)模式
>>>> 按n键跳转至下一个结果,N跳转至上一个结果

head:显示文件开头的几行(默认是10行)
> -n:指定行数，如 head cloud-init.log -n 2 就是两行

tail:显示文件结尾的几行(默认是10行)
> -n:指定行数，如 tail cloud-init.log -n 2 就是两行
> -f:每过一秒检查一次文件是否有更新内容
>> 可以用 -s 参数指定间隔时间,如 tail -f -s 4 xxx.log 就是每过4秒

touch:创建一个文件
mkdir:创建一个目录
> -p递归的创建目录结构 mkdir -p one/two/three

#### 文件的复制和移动

cp:拷贝文件和目录
> -r递归的拷贝,常用来拷贝一整个目录
> 例子 cp file file_copy (file是目标文件,file_copy是拷贝出来的文件)

mv:移动/重命名文件和目录
> 用法和cp相似

## http协议

## php基础语法
