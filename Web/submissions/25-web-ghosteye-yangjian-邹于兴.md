## 工具
1.F12，不管  

2.hackbar  

![hackbar](https://github.com/ghosteye-yangjian/image-hosting/blob/96aba531a90f54fdbdc21ab83095d86771a6a481/%E8%81%94%E6%83%B3%E6%88%AA%E5%9B%BE_20251125112830.png)  

3.Burp Suite，kali里面有，后续打算在本机上再搞一个  

![Burp Suite](https://github.com/ghosteye-yangjian/image-hosting/blob/96aba531a90f54fdbdc21ab83095d86771a6a481/%E8%81%94%E6%83%B3%E6%88%AA%E5%9B%BE_20251125105424.png)  

4.AI,deepseek,豆包......略  

import hashlib
import time

def find_md5_prefix(target_prefix: str) -> tuple[str, str, float]:
    """
    暴力破解找到 MD5 加密后前 n 位与目标前缀匹配的原始值
    :param target_prefix: 目标 MD5 前缀（十六进制字符串）
    :return: (原始值, 完整 MD5 值, 耗时)
    """
    if not target_prefix.islower() or len(target_prefix) < 1:
        raise ValueError("目标前缀需为小写十六进制字符串（0-9、a-f）")
    
    target_len = len(target_prefix)
    counter = 0  # 计数器（作为原始候选值）
    start_time = time.time()
    
    while True:
        # 将计数器转为字符串（原始值），UTF-8 编码后计算 MD5
        original = str(counter)
        md5_hash = hashlib.md5(original.encode("utf-8")).hexdigest()
        
        # 匹配前 target_len 位
        if md5_hash[:target_len] == target_prefix:
            end_time = time.time()
            return original, md5_hash, end_time - start_time
        
        counter += 1
        # 每 100 万次输出进度（可选）
        if counter % 1000000 == 0:
            print(f"已尝试 {counter:,} 个值，耗时 {time.time() - start_time:.2f}s")

# 目标：MD5 前六位为 15af95
target = "15af95"
try:
    original_val, md5_val, cost_time = find_md5_prefix(target)
    print(f"找到匹配值！")
    print(f"原始值：{original_val}")
    print(f"完整 MD5：{md5_val}")
    print(f"耗时：{cost_time:.2f}s")
except KeyboardInterrupt:
    print("\n程序被手动终止")

## FLAG
1.摁一下F12  

![yiti](https://github.com/ghosteye-yangjian/image-hosting/blob/cc21bd345114a33df55f06d6d49731a86aebeb33/%E8%81%94%E6%83%B3%E6%88%AA%E5%9B%BE_20251125094334.png)

2.GET就网址后面直接加上?a=1,POST用的Hackbar  

![erti](https://github.com/ghosteye-yangjian/image-hosting/blob/cc21bd345114a33df55f06d6d49731a86aebeb33/%E8%81%94%E6%83%B3%E6%88%AA%E5%9B%BE_20251125102736.png)

## 虚拟机及Linux系统搭建 

我搭了一个CentOS 7和一个kali Linux并对两者有了一些基础的了解，kali的图前面放过，这里就不放了

![CentOS 7](https://github.com/ghosteye-yangjian/image-hosting/blob/cc21bd345114a33df55f06d6d49731a86aebeb33/%E8%81%94%E6%83%B3%E6%88%AA%E5%9B%BE_20251125105254.png)

 
