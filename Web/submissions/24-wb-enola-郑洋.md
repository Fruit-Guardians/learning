# *工具*

## 1 .Hackbar

直接在chrome应用扩展里搜索下载即可

![](24-wb-enola-郑洋.assets/屏幕截图 2025-10-17 183501-1760843334407-2.png)

## 2.burp suite

首先，配置Java环境，前往官网下载即可，下载好后进行验证

![image-20251019111003751](24-wb-enola-郑洋.assets/image-20251019111003751.png)

然后前往burp suite官网，根据自己的需要下载适合的版本，我下载的是社区版

![](24-wb-enola-郑洋.assets/屏幕截图 2025-10-18 162631.png)

下载好后，打开exe文件，一直点到工具页面，然后进行端口和证书的配置。

打开burp suite的proxy页面，点击add，加上127.0.0.1：8080

![](24-wb-enola-郑洋.assets/屏幕截图 2025-10-19 111625.png)

接着打开chrome浏览器，下载switchyomega插件，打开插件，点击新建情景模式

![image-20251019112055339](24-wb-enola-郑洋.assets/image-20251019112055339.png)

设置成如图选项后，接下来便开始证书的设置

先在地址栏输入127.0.0.1：8080，下载证书文件

![屏幕截图 2025-10-18 173714](24-wb-enola-郑洋.assets/屏幕截图 2025-10-18 173714.png)

然后在浏览器里打开设置，找到证书选项，导入刚刚下载好的证书cer文件，证书设置完成

![屏幕截图 2025-10-18 174337](24-wb-enola-郑洋.assets/屏幕截图 2025-10-18 174337.png)

最终burpsuite设置完成。

# *Linux*

## 1.Linux环境的搭建

我是在VMware上搭建了Ubuntu系统，之前进行了搭建，在此便不在展示细节。

点击vm文件，新建虚拟机，然后导入下载好的镜像文件即可

![image-20251019112840950](24-wb-enola-郑洋.assets/image-20251019112840950.png)

然后进行网络的设置，我设置的桥接，最终Ubuntu系统便搭建完成，接下来进行汉化和汉字输入法的加入即可，最终结果如下

![image-20251019113607086](24-wb-enola-郑洋.assets/image-20251019113607086.png)

## 2.linux知识学习

`ssh root@xxx`这条命令，必须要在`Shell`中才能执行

*Bash`是目前最常用的`Shell`。MacOS 中的默认`Shell`就是 `Bash*

root：表示用户名；

iZm5e8dsxce9ufaic7hi3uZ：表示主机名；

~：表示目前所在目录为家目录，其中root用户的家目录是 /root普通用户的家目录在 /home 下；

#：指示你所具有的权限（root用户为# ，普通用户为$ ）。

执行whoami命令可以查看当前用户名；

执行hostname命令可以查看当前主机名；

# *作业*

## **1.view -source**

点开地址，按F12即可找出

![屏幕截图 2025-10-18 223725](24-wb-enola-郑洋.assets/屏幕截图 2025-10-18 223725.png)

## 2.get-post

暂时没做出来，我下载的hackbar好像有点问题，和网上教程里的不太一样，在捣鼓捣鼓

## 3.robots

先点进地址，发现什么都没有

![image-20251019114343793](24-wb-enola-郑洋.assets/image-20251019114343793.png)

然后访问txt文件，找到flag地址

![image-20251019114418395](24-wb-enola-郑洋.assets/image-20251019114418395.png)

然后输入地址，便可得到flag

![image-20251019114516317](24-wb-enola-郑洋.assets/image-20251019114516317.png)

## 3.用ai写一个python脚本，要求找到一个值经过md5加密后的前6位是`15af95`

我用的deepseek，他给出了三种方法：

### 1.暴力破解

import hashlib
import time

def find_md5_collision():
    target_prefix = "15af95"
    print(f"正在寻找MD5哈希前6位为 '{target_prefix}' 的值...")
    

    start_time = time.time()
    counter = 0
    
    # 从0开始尝试数字
    for i in range(0, 10**10):  # 最多尝试100亿次
        test_string = str(i)
        md5_hash = hashlib.md5(test_string.encode()).hexdigest()
        
        if md5_hash.startswith(target_prefix):
            end_time = time.time()
            print(f"\n找到匹配的值！")
            print(f"原始值: {test_string}")
            print(f"MD5哈希: {md5_hash}")
            print(f"尝试次数: {counter}")
            print(f"耗时: {end_time - start_time:.2f} 秒")
            return test_string, md5_hash
        
        counter += 1
        if counter % 1000000 == 0:  # 每100万次显示进度
            print(f"已尝试 {counter} 次...")
    
    print("在限制范围内未找到匹配的值")
    return None

if __name__ == "__main__":
    find_md5_collision()

## 2.随机字符串

import hashlib
import random
import string
import time

def find_md5_collision_random():
    target_prefix = "15af95"
    print(f"正在寻找MD5哈希前6位为 '{target_prefix}' 的值...")
    
    start_time = time.time()
    counter = 0
    
    while True:
        # 生成长度1-20的随机字符串
        length = random.randint(1, 20)
        test_string = ''.join(random.choices(
            string.ascii_letters + string.digits + string.punctuation, 
            k=length
        ))
        
        md5_hash = hashlib.md5(test_string.encode()).hexdigest()
        
        if md5_hash.startswith(target_prefix):
            end_time = time.time()
            print(f"\n找到匹配的值！")
            print(f"原始值: {test_string}")
            print(f"MD5哈希: {md5_hash}")
            print(f"尝试次数: {counter}")
            print(f"耗时: {end_time - start_time:.2f} 秒")
            return test_string, md5_hash
        
        counter += 1
        if counter % 100000 == 0:  # 每10万次显示进度
            print(f"已尝试 {counter} 次...")

if __name__ == "__main__":
    find_md5_collision_random()

### 3.多线程加速

import hashlib
import threading
import time

def worker(thread_id, start_num, end_num, target_prefix, result):
    """工作线程函数"""
    for i in range(start_num, end_num):
        test_string = str(i)
        md5_hash = hashlib.md5(test_string.encode()).hexdigest()
        
        if md5_hash.startswith(target_prefix):
            result.append((test_string, md5_hash))
            return

def find_md5_collision_multithreaded():
    target_prefix = "15af95"
    num_threads = 8
    range_size = 10**8  # 每个线程处理1亿个数字
    
    print(f"使用 {num_threads} 个线程寻找MD5哈希前6位为 '{target_prefix}' 的值...")
    
    start_time = time.time()
    threads = []
    result = []
    
    # 创建并启动线程
    for i in range(num_threads):
        start_num = i * range_size
        end_num = (i + 1) * range_size
        thread = threading.Thread(
            target=worker, 
            args=(i, start_num, end_num, target_prefix, result)
        )
        threads.append(thread)
        thread.start()
    
    # 等待所有线程完成
    for thread in threads:
        thread.join()
    
    if result:
        end_time = time.time()
        test_string, md5_hash = result[0]
        print(f"\n找到匹配的值！")
        print(f"原始值: {test_string}")
        print(f"MD5哈希: {md5_hash}")
        print(f"耗时: {end_time - start_time:.2f} 秒")
        return test_string, md5_hash
    else:
        print("在指定范围内未找到匹配的值")
        return None

if __name__ == "__main__":
    find_md5_collision_multithreaded()