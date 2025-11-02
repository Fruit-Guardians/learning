[week1.md](https://github.com/user-attachments/files/23289186/week1.md)
# 工具

#### 一.浏览器开发者工具F12：

1.同时按下Esc和Fn键切换至F1-F12模式，按F12，进入开发者模式

2.直接点击右上角三点，在<更多工具>一栏中点击开发者工具(Google) 

![image-20251030215149256](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251030215149256.png)

#### 二.HackBar插件安装

1.在火狐浏览器的扩展与主题的插件中搜索"HackBar"

2.点击安装（安装截图）

![image-20251030215803928](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251030215803928.png)

![image-20251101082504918](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251101082504918.png)

#### 三.Burp Suite安装（暂时还没安装成功，先安装了Yak，安装完成后会补全笔记）

1.安装Burp Suite之前需要自行配置 JAVA JDK 的环境

#### 四.Yak安装

（官方网站下载：https://www.yaklang.com/）

![image-20251031004749464](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251031004749464.png)

#### 五.AI

(以下为AI编写的)

我来帮你写一个Python脚本来寻找MD5哈希前6位为"15af95"的值。这个脚本会尝试不同的输入值，直到找到匹配的。

```python
import hashlib
import itertools
import string
import time

def find_md5_with_prefix(target_prefix):
    """
    寻找MD5哈希前6位为指定前缀的值
    
    Args:
        target_prefix (str): 目标MD5前缀（6位十六进制）
    
    Returns:
        tuple: (找到的值, 对应的MD5哈希) 或 (None, None) 如果超时
    """
    target_prefix = target_prefix.lower()
    print(f"正在寻找MD5前6位为 '{target_prefix}' 的值...")
    
    # 尝试数字
    print("尝试数字...")
    for i in range(100000000):  # 尝试1亿个数字
        original = str(i)
        md5_hash = hashlib.md5(original.encode()).hexdigest()
        
        if md5_hash[:6] == target_prefix:
            return original, md5_hash
    
    # 如果数字没找到，尝试字母数字组合
    print("尝试字母数字组合...")
    chars = string.ascii_letters + string.digits
    
    # 先尝试短字符串
    for length in range(1, 6):
        for combo in itertools.product(chars, repeat=length):
            original = ''.join(combo)
            md5_hash = hashlib.md5(original.encode()).hexdigest()
            
            if md5_hash[:6] == target_prefix:
                return original, md5_hash
    
    return None, None

def find_md5_with_prefix_optimized(target_prefix, max_attempts=10000000):
    """
    优化版本的查找函数，使用更高效的搜索策略
    
    Args:
        target_prefix (str): 目标MD5前缀
        max_attempts (int): 最大尝试次数
    
    Returns:
        tuple: (找到的值, 对应的MD5哈希) 或 (None, None)
    """
    target_prefix = target_prefix.lower()
    print(f"正在寻找MD5前6位为 '{target_prefix}' 的值...")
    print(f"最大尝试次数: {max_attempts:,}")
    
    start_time = time.time()
    
    # 策略1: 尝试随机字符串（更高效）
    import random
    chars = string.ascii_letters + string.digits + string.punctuation
    
    for i in range(max_attempts):
        # 随机生成长度1-10的字符串
        length = random.randint(1, 10)
        original = ''.join(random.choices(chars, k=length))
        
        md5_hash = hashlib.md5(original.encode()).hexdigest()
        
        if md5_hash[:6] == target_prefix:
            end_time = time.time()
            print(f"找到结果！用时: {end_time - start_time:.2f} 秒")
            return original, md5_hash
        
        # 每10万次显示进度
        if i % 100000 == 0 and i > 0:
            print(f"已尝试 {i:,} 次...")
    
    end_time = time.time()
    print(f"在 {max_attempts:,} 次尝试后未找到结果，用时: {end_time - start_time:.2f} 秒")
    return None, None

def main():
    target_prefix = "15af95"
    
    print("MD5前缀碰撞查找器")
    print("=" * 50)
    
    # 使用优化版本
    original, md5_hash = find_md5_with_prefix_optimized(target_prefix, 100000000)
    
    if original and md5_hash:
        print("\n" + "=" * 50)
        print("🎉 找到匹配的值！")
        print(f"原始值: {original}")
        print(f"MD5哈希: {md5_hash}")
        print(f"验证: MD5前6位 = {md5_hash[:6]}")
    else:
        print("\n未找到匹配的值，请增加尝试次数或调整搜索策略")

if __name__ == "__main__":
    main()
```

另外，这里还有一个更简单的版本，专注于快速尝试：

```python
import hashlib
import random
import string

def simple_find_md5_prefix(target_prefix, max_tries=100000000):
    """
    简单版本的MD5前缀查找
    """
    chars = string.ascii_letters + string.digits + string.punctuation
    target_prefix = target_prefix.lower()
    
    for i in range(max_tries):
        # 生成随机字符串
        length = random.randint(1, 20)
        text = ''.join(random.choices(chars, k=length))
        
        md5_hash = hashlib.md5(text.encode()).hexdigest()
        
        if md5_hash.startswith(target_prefix):
            return text, md5_hash
            
        if i % 1000000 == 0 and i > 0:
            print(f"已尝试 {i} 次...")
    
    return None, None

# 使用简单版本
print("开始查找...")
result, hash_value = simple_find_md5_prefix("15af95")

if result:
    print(f"找到结果: '{result}'")
    print(f"MD5: {hash_value}")
else:
    print("在指定尝试次数内未找到结果")
```

说明：

1. 工作原理：脚本会生成随机字符串，计算其MD5哈希，检查前6位是否匹配"15af95"
2. 搜索策略：
   · 先尝试数字
   · 然后尝试短字符串
   · 最后使用随机字符串
3. 性能考虑：
   · 找到特定MD5前缀需要一定的计算量
   · 脚本包含进度显示，让你了解搜索进度
   · 可以调整最大尝试次数
4. 运行时间：由于MD5的特性，找到特定前缀可能需要几秒到几小时不等，取决于运气

运行这个脚本，它会持续尝试直到找到匹配的值或者达到最大尝试次数。找到后会显示原始值和完整的MD5哈希。

#### 六.搜索笔记

#####    1)WriteUp定义：一份详细记录解题过程的文档，包含

- 题目分析思路
- 解题步骤详解
- 使用工具和方法
- 最终答案（Flag）
- 经验总结

#####    2）Flag定义：是一段特殊的字符串，通常包含：

- 比赛中的目标或答案
- 隐藏在题目中的凭证
- 证明完成某个挑战的证据

#####       常见格式：flag{example_flag_123} ,   cyberpeace{md5_hash} 等

#####       Flag在Web题目中常见隐藏位置：

- HTML源代码注释中
- HTTP响应头中
- JavaScript代码里
- 数据库查询结果中
- Cookie或本地存储中

#### 七.攻防世界题目

#### 1.view_source

##### 题目信息

- 题目名称：view_source
- 方向：Web方向
- 思路：禁用右键，限制源代码查看，则需找到绕过限制查看源代码

##### 解题步骤

- 打开在线应用场景
- d使用Ctrl+U快捷键或用F12的Elements

![image-20251101003201788](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251101003201788.png)

![image-20251101003104385](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251101003104385.png)

##### 获取Flag

cyberpeace{252e5153bd51276480f4ef376c7781cc} 

##### 总结

使用者被禁用右键后仍可使用开发者工具或快捷键获取源代码，找到Flag



#### 2.get_post

##### 题目信息

- 题目名称：get_post
- 方向：Web方向
- 思路：先用GET方式提交名为a，值为1到达变量，提交请求，在获得新提示后进行POST请求

##### 解题步骤

- 在URL中提交参数a=1（？表示开始传递的参数）
- 页面中显示新提示：POST请求
- F12键打开开发者模式，进入HackBar
- 打开POST模式并在Body框（请求体）中输入b=2，并按下EXECUTE（执行键），即可获得Flag



![image-20251101013525064](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251101013525064.png)

##### 获取Flag:

Cyberpeace{77968C8A7FC568EF10D4AD9475F8F103}

##### 总结

- 关注GET和POST的请求方式和区别
- GET在URL处进行参数传递，POST在Body请求体中





# Linux基础

### 环境搭建

1.安装VMware

2.安装CentOS 7系统ISO

3.打开后选择创建新的虚拟机

![image-20251101091703030](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251101091703030.png)

![image-20251101104117430](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251101104117430.png)

4.创建完成

5.安装虚拟机

![image-20251101105415373](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251101105415373.png)

6.安装完成

![image-20251101110703530](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20251101110703530.png)

### 基础命令知识学习

#### 1.ls（列出目录内容）

- 功能：列出当前目录或指定目录中的文件和文件夹

- 常用选项：

  -l：以长格式显示文件和目录的详细信息，包括权限、所有者、大小

  -a：显示所有文件和目录，包括隐藏文件（以. 开头的文件）

  -h：以易读的格式显示文件大小（如K,M,G）

  -t：按修改时间顺序

- 示例：

  ls -lha        # 长格式+全部文件+人性化大小
  ls -lt         # 按时间排序
  ls /home       # 查看指定目录

#### 2.cd（切换目录）

- 功能：切换到指定目录

- 用法：

  cd目录途径：切换到指定路径的目录

  cd：切换到用户的主目录（/home/用户名）

  cd.. ：切换到当前目录的上一级目录

  cd-：切换到上一次所在的目录

  cd../..：向上移动两级目录

- 示例：

  cd /home/user/documents      # 切换到绝对路径
  cd documents         # 切换到当前目录下的documents文件夹
  cd ~       # 切换到用户主目录
  cd ..       # 返回上一级目录
  cd -        # 返回上一个访问的目录

#### 3.pwd(显示当前工作目录)

- 功能：显示当前所在的目录途径

#### 4.mkdir（创建目录）

- 功能：创建一个新的目录

- 常用选项： 

  -p：递归创建目录，如果父目录不存在，则会一并创建

  -m：设置目录的权限模式

- 示例：

  #创建单个目录     mkdir new_folder

  #递归创建多级目录     mkdir -p parent_folder/child_folder/grandchild

  #创建多个并列目录     mkdir dir1 dir2 dir3

  #创建目录并设置权限      mkdir -m 755 secure_folder

#### 5.cp（复制文件或目录）

- 功能：将文件或目录从一个位置复制到另一个位置

- 常用选项：

  -r：递归复制目录及内容

  -i：交互式复制，目标文件已存在时提示确认

  -a：归档模式，保留文件的权限、属性等

- 示例：

  1.基本文件复制：

     复制文件到指定目录   cp file.txt /home/user/documents

     复制文件并重命名    cp file.txt new_file.txt

     复制多个文件到目录   cp file1.txt file2.txt file3.txt /target/folder/

  2.目录复制：

     递归复制整个目录   cp -r folder /home/user/documents

     递归复制并显示过程   cp -rv source_folder /backup/

     保留所有属性复制目录  cp -a original_folder /backup/

  3.安全复制：

     交互式复制（覆盖前询问）  cp -i important_file.txt /backup/

     复制前先备份已存在文件    cp --backup=numbered file.txt /target/

  4.特殊用法：

     复制时保留所有元数据    cp -p source.txt destination.txt

     强制复制，覆盖已存在文件    cp -f file.txt /target/location/

     复制符号链接本身（而不是指向的文件） cp -P symlink.txt copy_of_symlink.txt

#### 6.cat（查看文件内容）

- 功能：将文件内容输出到终端

- 常用选项：

  -n：为所有输出行编号（包括空行）

  -b：为非空输出行编号（忽略空行）

  -A：显示所有内容，相当于-vET组合

  -E：在每行末尾显示一个$符号

  -T：将制表符显示为^l

  -s：将连续多个空行压缩为一个空行

  -v：显示除换行符和制表符以外的非打印字符

#### 7.find（查找文件或目录）

- 功能：在指定目录及子目录中查找符合条件的文件或目录

- 常用选项：

  -name：按文件名查找

  -type：按文件类型查找（-f:普通文件  ； -d：目录   ；  -l：符号链接）

  -mtime：按修改时间查找（-n：nt天以内修改的文件  ；  +n：n天以前修改的文件）

  -exec：对找到的文件执行指定的命令

  -perm：按文件权限查找

- 示例：

  find /home -name ".txt"
  find . -type d
  find . -mtime -1
  find . -size +10M
  find . -name ".tmp" -exec rm {} \;

#### 8.tar（归档和压缩文件）

- 功能：用于创建、解压和管理归档文件

- 常用选项：

  -c：创建归档文件

  -x：解压归档文件

  -z：使用gzip压缩

  -j：使用bzip压缩

  -v：显示详细信息

  -f：指定归档文件名

  -p：保留文件权限属性

- 示例：

  创建普通的 tar 归档（不压缩）tar -cvf archive.tar folder/

  创建 gzip 压缩的归档（最常用）tar -czvf archive.tar.gz folder/

  创建 bzip2 压缩的归档（压缩率更高）tar -cjvf archive.tar.bz2 folder/

  创建 xz 压缩的归档（压缩率最高）tar -cJvf archive.tar.xz folder/

  解压普通的 tar 归档   tar -xvf archive.tar 

  解压 gzip 压缩的归档   tar -xzvf archive.tar.gz

  解压 bzip2 压缩的归档   tar -xjvf archive.tar.bz2

  解压 xz 压缩的归档   tar -xJvf archive.tar.xz

  解压到指定目录  tar -xzvf archive.tar.gz -C /target/directory/

  向现有归档追加文件  tar -rvf archive.tar newfile.txt

  创建归档时排除某些文件   tar -czvf backup.tar.gz --exclude="*.tmp" folder/

  保留文件权限（常用于系统备份）  tar -czvpf system_backup.tar.gz /etc/



------

### 其他命令会继续学习，并及时补充至笔记!



