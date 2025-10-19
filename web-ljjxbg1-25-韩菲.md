<font style="color:#DF2A3F;">1.view_source</font>

![](https://cdn.nlark.com/yuque/0/2025/png/61875695/1760873184424-a479e5b8-27aa-497a-a239-9a83d83a1f97.png)

共三种途径

1.ctrl u

2.在网址前加view_source:

3.f12



<font style="color:#DF2A3F;">2.get-post</font>

<font style="color:#000000;">在网址后直接加/？a=1进行put得到</font>![](https://cdn.nlark.com/yuque/0/2025/png/61875695/1760874944893-dbf36877-ad05-415b-b7eb-a4c10fb93d50.png)

<font style="color:#000000;">利用hackbar进行post</font>

<font style="color:#000000;"></font>

<font style="color:#000000;">3.</font><font style="color:rgb(31, 35, 40);">python脚本</font>

<h1 id="df9efa0c">Python脚本：寻找MD5哈希前6位为"15af95"的值</h1>
```plain
python

下载
复制
运行



import hashlib
import itertools
import string
import time

def find_md5_with_prefix(target_prefix, max_length=8):
    """
    寻找一个字符串，其MD5哈希值的前6位与目标前缀匹配
    
    参数:
        target_prefix (str): 目标MD5前缀(6个十六进制字符)
        max_length (int): 尝试的最大字符串长度
    
    返回:
        str: 第一个匹配的字符串，如果没有找到则返回None
    """
    chars = string.printable  # 所有可打印ASCII字符
    start_time = time.time()
    attempts = 0
    
    print(f"开始搜索MD5前缀为'{target_prefix}'的字符串...")
    
    for length in range(1, max_length + 1):
        print(f"正在尝试长度为{length}的字符串...")
        for candidate in itertools.product(chars, repeat=length):
            candidate_str = ''.join(candidate)
            md5_hash = hashlib.md5(candidate_str.encode('utf-8')).hexdigest()
            attempts += 1
            
            if md5_hash.startswith(target_prefix):
                end_time = time.time()
                elapsed = end_time - start_time
                print(f"\n找到匹配的字符串!")
                print(f"字符串: {candidate_str}")
                print(f"MD5哈希: {md5_hash}")
                print(f"尝试次数: {attempts}")
                print(f"耗时: {elapsed:.2f}秒")
                return candidate_str
                
            # 每100万次尝试打印一次进度
            if attempts % 1000000 == 0:
                print(f"已尝试 {attempts} 次组合...")
    
    print("\n在指定长度范围内未找到匹配的字符串。")
    return None

if __name__ == "__main__":
    target_prefix = "15af95"
    result = find_md5_with_prefix(target_prefix)
    
    if result:
        print(f"\n成功找到字符串: '{result}'，其MD5哈希前6位为'{target_prefix}'")
    else:
        print("\n未找到符合条件的字符串。")
```

<h2 id="754bd722">脚本说明</h2>
1. **1.****功能**：这个脚本会尝试所有可能的字符串组合，直到找到一个字符串，其MD5哈希值的前6位是"15af95"。
2. **2.****工作原理**：
    - •使用itertools.product生成所有可能的字符串组合
    - •对每个字符串计算MD5哈希值
    - •检查哈希值是否以目标前缀开头
    - •找到匹配项后立即返回
3. **3.****注意事项**：
    - •这是一个暴力破解方法，可能需要很长时间才能找到结果
    - •默认最大字符串长度为8，可以根据需要调整
    - •脚本会定期打印进度信息
4. **4.****优化建议**：
    - •如果需要更快的速度，可以考虑使用多线程/多进程
    - •可以限制字符集以减少搜索空间
    - •对于更长的前缀，可能需要更高效的算法

运行此脚本时，请耐心等待，因为找到匹配项可能需要相当长的时间





**工具**

1.浏览器自带工作台

f12唤起即可

2.hackbar

在Firefox中下载老版本hackbar

3.ai

豆包 ds



这周进群比较晚，准备时间比较仓促，下面两天会跟进linux的尝试



  


