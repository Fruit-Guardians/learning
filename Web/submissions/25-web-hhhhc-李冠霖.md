[2025-web-hhhhc-李冠霖.md](https://github.com/user-attachments/files/23165813/2025-web-hhhhc-.md)
#25-web-hhhhc-#

##工具##

​	###F12###



![b6a509ab7d14b2605570ee4813f71bc8](C:\Users\li130\Desktop\b6a509ab7d14b2605570ee4813f71bc8.png)

​	###Hackbar###

![e4f76257e33c9a9f55eec31038a7a408](D:\QQ\Tencent Files\2752033760\nt_qq\nt_data\Pic\2025-10\Ori\e4f76257e33c9a9f55eec31038a7a408.png)

​	###Burpsuite###

​		还没太摸索明白

![7b58fbe7e0cbf7a817d79754bb44b30a](D:\QQ\Tencent Files\2752033760\nt_qq\nt_data\Pic\2025-10\Ori\7b58fbe7e0cbf7a817d79754bb44b30a.png)

​	###AI###

​		我直接用的deep seek（

#题目#

###view_source###

​		<!-- Cyberpeace{B564E7137974CB362A3F90F305EA5045} -->（感谢学长指导）

###get_post###

		1. GET

核心用途： 用于获取或请求数据。

特点：

· 参数在 URL 中： 所有要发送给服务器的数据（参数）都会附加在 URL 之后，格式为 ?key1=value1&key2=value2。
  · 例如：https://www.example.com/search?q=keyword&category=books
· 可见性： 由于参数在 URL 中，所以对用户是可见的，并且可以被浏览器历史记录、书签保存。
· 长度限制： URL 有长度限制（因浏览器和服务器而异），所以不能发送大量数据。
· 安全性： 安全性较低，因为参数直接暴露在 URL 中，不适合传输密码、信用卡号等敏感信息。
· 幂等性： GET 请求是幂等的，意味着多次执行相同的 GET 请求，效果与执行一次是相同的。它不应该改变服务器状态（例如，它只用于查询，而不用于删除或修改）。
· 可缓存： GET 请求可以被浏览器缓存。

典型应用场景：

· 在浏览器地址栏输入网址访问网页。
· 点击网页链接。
· 使用搜索引擎进行搜索。

---

2. POST

核心用途： 用于提交或发送数据给服务器，通常会导致服务器状态的改变（如更新数据、创建新资源）。

特点：

· 参数在请求体中： 要发送的数据放在 HTTP 请求的 Body（主体） 部分，不会显示在 URL 中。
· 可见性： 对用户不可见，更安全（但并非绝对安全，仍需使用 HTTPS 加密）。
· 长度限制： 理论上没有长度限制，可以发送大量数据，如图片、文件等。
· 安全性： 相对 GET 更安全，因为数据不在 URL 中直接暴露。
· 非幂等性： POST 请求是非幂等的，意味着多次提交相同的 POST 请求可能会产生不同的结果（例如，多次提交一个订单会创建多个订单）。
· 不可缓存： 默认情况下，POST 请求不会被浏览器缓存。

典型应用场景：

· 用户登录（提交用户名和密码）。
· 发表博客评论、发布微博。
· 上传文件。
· 网上购物提交订单。

---

总结对比表

特性 GET POST
核心目的 获取数据 提交数据
参数位置 URL 的查询字符串中 HTTP 请求的 Body 中
数据可见性 可见（在URL中） 不可见（在Body中）
数据长度 有限制（受URL长度限制） 理论上无限制
安全性 较低（数据暴露在URL中） 相对较高（但并非绝对安全）
幂等性 是（多次请求结果相同） 否（多次请求可能产生不同结果）
缓存 可被浏览器缓存 默认不缓存
历史记录 参数保留在浏览器历史中 参数不会保留在历史中
书签 可被收藏为书签 无法直接收藏带有数据的书签

其他常见 HTTP 方法

除了 GET 和 POST，HTTP 协议还定义了其他一些重要的方法，特别是在 RESTful API 设计中非常常用：

· PUT： 用于更新服务器上的已有资源（全部更新）。
· PATCH： 用于对资源进行部分更新。
· DELETE： 用于删除服务器上的指定资源。

简单来说，记住 GET 是拿，POST 是给，就掌握了 HTTP 请求方法的核心基础。

###脚本###

import hashlib
import itertools
import string
import time

def find_md5_with_prefix(target_prefix, max_length=8, charset=None):
    """
    寻找MD5哈希值前6位为指定前缀的原始值
    
    参数:
    target_prefix: 目标MD5前缀（6位十六进制）
    max_length: 最大搜索长度
    charset: 字符集，默认为数字和小写字母
    """
    if charset is None:
        charset = string.digits + string.ascii_lowercase
    
    target_prefix = target_prefix.lower()
    print(f"开始搜索MD5前6位为 '{target_prefix}' 的值...")
    print(f"字符集: {charset}")
    print(f"最大长度: {max_length}")
    print("-" * 50)
    
    start_time = time.time()
    attempts = 0
    
    # 尝试不同长度的字符串
    for length in range(1, max_length + 1):
        print(f"正在尝试长度为 {length} 的字符串...")
        
        # 生成所有可能的组合
        for combination in itertools.product(charset, repeat=length):
            original_value = ''.join(combination)
            attempts += 1
            
            # 计算MD5哈希值
            md5_hash = hashlib.md5(original_value.encode()).hexdigest()
            
            # 检查前6位是否匹配
            if md5_hash[:6] == target_prefix:
                end_time = time.time()
                elapsed_time = end_time - start_time
                
                print("\n" + "=" * 50)
                print("找到符合条件的值！")
                print(f"原始值: {original_value}")
                print(f"MD5哈希: {md5_hash}")
                print(f"尝试次数: {attempts}")
                print(f"耗时: {elapsed_time:.2f} 秒")
                print("=" * 50)
                return original_value, md5_hash
            
            # 每100万次显示进度
            if attempts % 1000000 == 0:
                print(f"  已尝试 {attempts} 次组合...")
    
    end_time = time.time()
    elapsed_time = end_time - start_time
    print(f"\n在长度为1-{max_length}的字符串中未找到符合条件的值")
    print(f"总尝试次数: {attempts}")
    print(f"总耗时: {elapsed_time:.2f} 秒")
    return None, None

def find_specific_length(target_prefix, length, charset=None):
    """
    在指定长度的字符串中搜索
    """
    if charset is None:
        charset = string.digits + string.ascii_lowercase
    
    target_prefix = target_prefix.lower()
    print(f"在长度为{length}的字符串中搜索MD5前6位为'{target_prefix}'的值...")
    
    start_time = time.time()
    attempts = 0
    
    for combination in itertools.product(charset, repeat=length):
        original_value = ''.join(combination)
        attempts += 1
        
        md5_hash = hashlib.md5(original_value.encode()).hexdigest()
        
        if md5_hash[:6] == target_prefix:
            end_time = time.time()
            elapsed_time = end_time - start_time
            
            print("\n" + "=" * 50)
            print("找到符合条件的值！")
            print(f"原始值: {original_value}")
            print(f"MD5哈希: {md5_hash}")
            print(f"尝试次数: {attempts}")
            print(f"耗时: {elapsed_time:.2f} 秒")
            print("=" * 50)
            return original_value, md5_hash
    
    end_time = time.time()
    elapsed_time = end_time - start_time
    print(f"在长度为{length}的字符串中未找到符合条件的值")
    print(f"尝试次数: {attempts}")
    print(f"耗时: {elapsed_time:.2f} 秒")
    return None, None

if __name__ == "__main__":
    # 方法1: 全面搜索（从短到长）
    print("方法1: 全面搜索")
    original, md5_hash = find_md5_with_prefix("15af95", max_length=6)
    
    if original is None:
        print("\n" + "=" * 50)
        print("开始扩展搜索范围...")
        print("=" * 50)
        
        # 方法2: 重点搜索较长的字符串
        for length in [7, 8]:
            original, md5_hash = find_specific_length("15af95", length)
            if original is not None:
                break
    
    # 如果还没找到，可以尝试扩展字符集
    if original is None:
        print("\n" + "=" * 50)
        print("尝试扩展字符集（包含大写字母和特殊字符）...")
        print("=" * 50)
        
        extended_charset = string.digits + string.ascii_letters + "!@#$%^&*()_+-=[]{}|;:,.<>?"
        original, md5_hash = find_specific_length("15af95", 6, extended_charset)

##linux搭建##

​	1.先找AI看看怎么整![image-20251027212018791](C:\Users\li130\AppData\Roaming\Typora\typora-user-images\image-20251027212018791.png)

​	2.根据方法下载virtualbox以及linux对应镜像文件

​	3.进行对应配置

![image-20251027212328790](C:\Users\li130\AppData\Roaming\Typora\typora-user-images\image-20251027212328790.png)

![image-20251027212448088](C:\Users\li130\AppData\Roaming\Typora\typora-user-images\image-20251027212448088.png)
