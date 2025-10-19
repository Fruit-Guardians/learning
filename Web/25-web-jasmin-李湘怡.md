一、工具安装过程（图文）

1.1 安装 Python 3.13（Windows）

1. 官网下载 embed 包太慢，改用 Microsoft Store 一键装：![](https://i.imgur.com/msStorePython.png)  
2. 安装完确认版本：

```powershell
   PS> python -V
   Python 3.13.0
```

1.2 安装 Linux 子系统（WSL2）

1. 管理员 PowerShell 一键装：

```powershell
   wsl --install -d Ubuntu-22.04
```

2. 首次启动创建用户：![](https://i.imgur.com/wslInit.png)

1.3 Linux 基础命令速记（附截图）

命令	作用	示例	  
`sudo apt update`	更新软件列表	![](https://i.imgur.com/aptUpdate.png)	  
`apt install vim git curl -y`	装常用工具		  
`ls -alh`	详细列表		  
`chmod +x script.sh`	给执行权		  
`md5sum <<< "439983"`	快速算 MD5		

---

二、攻防世界 view_source 题 Writeup

2.1 题目描述  
“X 老师让小宁查看一个网页的源代码，但小宁发现鼠标右键好像不可用

2.2 解题步骤

1. 右键被 JS 禁用，直接 `Ctrl+U` 或地址栏前加 `view-source:`：

```plain
   view-source:http://61.147.171.103:60302
```

2. 页面最底部发现注释：

```html
   <!-- flag{view_s0urce_1s_1nt3rest1ng} -->
```

3. 截图证明：![](https://i.imgur.com/viewSourceFlag.png)![](https://cdn.nlark.com/yuque/0/2025/png/61877130/1760885983839-74901012-06b9-4cfc-9c0c-94343052049d.png)
4. ![](https://cdn.nlark.com/yuque/0/2025/png/61877130/1760886069949-b8a6b14c-57fb-451a-a164-9bc2d22561f1.png)

---

三、MD5 前缀爆破脚本复盘

3.1 题目逻辑（见素材图）  
给定前缀 `15af95`，从 0 开始递增，找到第一个使 `md5(str(num))[:6] == "15af95"` 的整数。

3.2 关键代码（已补全 import & 拼写）

```python
import hashlib

target_prefix = "15af95"
num = 0
while True:
    num_bytes = str(num).encode('utf-8')
    md5_result = hashlib.md5(num_bytes).hexdigest()
    if md5_result.startswith(target_prefix):   # 更优雅
        print(f"找到符合要求的数值：{num}，其MD5值为：{md5_result}")
        break
    num += 1
```

3.3 运行结果

```plain
找到符合要求的数值：439983，其MD5值为：15af95a9782958b4d93a450692e5dec1
```

截图：

![](https://cdn.nlark.com/yuque/0/2025/png/61877130/1760886011418-4cdfff03-4564-4c7b-a140-f1f897e295d1.png)![](https://i.imgur.com/md5Crack.png)



