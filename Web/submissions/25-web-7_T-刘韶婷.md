# 工具 
## Hackbar
![屏幕截图 2025-10-18 202133.png](https://77-tt-1383238072.cos.ap-guangzhou.myqcloud.com/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-18%20202133.png)

## Burp Suite
汉化
![屏幕截图 2025-10-18 220105.png](https://77-tt-1383238072.cos.ap-guangzhou.myqcloud.com/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-18%20220105.png)
原版
![屏幕截图 2025-10-18 220249.png](https://77-tt-1383238072.cos.ap-guangzhou.myqcloud.com/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-18%20220249.png)

# Linux
## 环境搭建
![屏幕截图 2025-10-19 034320.png](https://77-tt-1383238072.cos.ap-guangzhou.myqcloud.com/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-19%20034320.png)

## 基础知识
### 文件和目录操作
Is: 列出目录内容
cd:切换目录
pwd:显示当前目录路径
mkdir:创建新目录
rm:删除文件或目录
cp:复制文件或目录
mv:移动或重命名文件
touch:创建空文件或更新文件时间
cat: 查看文件内容
### 系统信息与监控
ps:查看进程
top:实时查看系统资源
df:查看磁盘使用情况
du: 查看目录大小
网络管理与诊断
ping: 测试网络连接状态
ifconfig:查看网络信息
### 权限管理
chmod:修改文件权限
chown: 更改文件拥有者
### 其他实用工具
grep: 搜索文本
find:查找文件
man: 查看命令手册
clear:清空终端屏幕
alias:创建命令别名
history: 显示命令历史
date:显示/设置系统时间
In:创建文件链接。
uname:显示系统信息
which: 查找命令路径。
# 题目
## 脚本
```python
import hashlib 
import multiprocessing 
from functools import partial 

def check_range(prefix, start, end): 
    """检查[start, end)范围内的数值，返回符合条件的结果""" 
    for num in range(start, end): 
        # 直接对字节流计算MD5（减少字符串转换开销） 
        md5_hash = hashlib.md5(str(num).encode()).hexdigest() 
        if md5_hash.startswith(prefix): 
            return num, md5_hash 
    return None 
    
def find_md5_prefix_fast(prefix, processes=4): 
    """多进程并行查找符合条件的数值""" 
    # 每个进程处理的数值范围步长（可根据实际情况调整） 
    step = 1000000 
    manager = multiprocessing.Manager() 
    result_queue = manager.Queue() # 用于进程间传递结果 
    
    # 启动多进程 
    workers = [] 
    def worker_func(start): 
        res = check_range(prefix, start, start + step) 
        if res: 
            result_queue.put(res) 
            
    # 动态分配任务（循环生成新的数值范围，直到找到结果） 
    current_start = 0 
    while True: 
        # 确保进程数不超过设定值 
        while len(workers) < processes: 
            p = multiprocessing.Process( 
                target=worker_func, 
                args=(current_start,) 
            ) 
            p.start()
            workers.append(p) 
            current_start += step 
            
            # 检查是否有进程找到结果 
            if not result_queue.empty(): 
                # 终止所有进程 
                for p in workers: 
                    p.terminate() 
                return result_queue.get()
                 
            # 清理已完成的进程 
            workers = [p for p in workers 
            
if p.is_alive()] if __name__ == "__main__": 
    target_prefix = "15af95" 
    print(f"多进程查找MD5前6位为 {target_prefix} 的值...") 
    # 进程数建议设为CPU核心数（如8核设为8） 
    result_num, result_md5 = find_md5_prefix_fast(target_prefix, processes=8) 
    print(f"找到符合条件的值：{result_num}") 
    print(f"MD5值：{result_md5}")
```
## Writeup
### robots
访问`http://111.198.29.45:33982/robots.txt`发现`f1ag_1s_h3re.php`
访问`http://111.198.29.45:33982/f1ag_1s_h3re.php`得到flag
![屏幕截图 2025-10-19 012559.png](https://77-tt-1383238072.cos.ap-guangzhou.myqcloud.com/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-19%20012559.png)

### view_source
F12
![屏幕截图 2025-10-19 011957.png](https://77-tt-1383238072.cos.ap-guangzhou.myqcloud.com/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-19%20011957.png)
### get_post
![屏幕截图 2025-10-19 021654.png](https://77-tt-1383238072.cos.ap-guangzhou.myqcloud.com/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-19%20021654.png)
