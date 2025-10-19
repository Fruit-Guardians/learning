24-web-zero-周雯雯

<h1 id="ofiXl">系统搭建</h1>
<h3 id="x8TEH">Linux</h3>
![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760524208874-8f22279d-b7de-47d6-8b7d-d19573b9f240.png)

<h3 id="Stclx">Hack Bar</h3>
![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760792640206-3bf9aea4-7bb8-49fb-9adf-97f1be225f19.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760792618316-70a9b01a-f41a-42ed-8632-eb5a9828ce83.png)

<h3 id="aRxYc">Burp Suit![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760808371692-9957a60b-e694-4ac8-8e8e-4a28ba1b3658.png)</h3>
<h1 id="hExH6">Linux基础命令学习</h1>
<h2 id="bK6yQ">shell</h2>
+ 接收用户输入的命令，将命令送入操作系统执行，将结果返回给用户。
+ <font style="color:rgb(77, 77, 77);">脚本都通过 shell 的解释执行，而不通过编译。</font>
+ <font style="color:rgb(77, 77, 77);">终端命令格式： command [-options] [parameter]</font>
1. <font style="color:rgb(77, 77, 77);">变量</font>

![画板](https://cdn.nlark.com/yuque/0/2025/jpeg/52691782/1760532679262-aeab3fb7-3eea-4cc7-ad58-81b96f8fc0e6.jpeg)

2. 单引号与双引号的使用

| <font style="color:rgb(51, 51, 51);background-color:rgb(250, 252, 253);">单引号字符串的限制</font> | <font style="color:rgb(51, 51, 51);background-color:rgb(250, 252, 253);">双引号的优点：</font> |
| --- | --- |
| + <font style="color:rgb(51, 51, 51);background-color:rgb(250, 252, 253);">单引号里的任何字符都会原样输出，单引号字符串中的变量是无效的；</font> | + <font style="color:rgb(51, 51, 51);background-color:rgb(250, 252, 253);">双引号里可以有变量</font> |
| + <font style="color:rgb(51, 51, 51);background-color:rgb(250, 252, 253);">单引号字符串中不能出现单独一个的单引号（对单引号使用转义符后也不行），但可成对出现，作为字符串拼接使用。</font> | + <font style="color:rgb(51, 51, 51);background-color:rgb(250, 252, 253);">双引号里可以出现转义字符</font> |


<h2 id="b3Eid">Linux 快捷指令</h2>
+ <font style="color:rgb(77, 77, 77);">通过上下方向键 ↑ ↓ 来调取过往执行过的Linux命令；</font>
+ <font style="color:rgb(77, 77, 77);">命令或参数仅需输入前几位就可以用 Tab 键补全；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + R ：用于查找使用过的命令（history命令用于列出之前使用过的所有命令，然后输入!命令加上编号 (!2) 就可以直接执行该历史命令）；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + L：清除屏幕并将当前行移到页面顶部；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + C：中止当前正在执行的命令；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + U：从光标位置剪切到行首；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + K：从光标位置剪切到行尾；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + W：剪切光标左侧的一个单词；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + Y：粘贴Ctrl + U | K | Y剪切的命令；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + A：光标跳到命令行的开头；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + E：光标跳到命令行的结尾；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + D：关闭Shell会话；</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl +Shift + = ：放大字体</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + -：缩小字体</font>
+ <font style="color:rgb(77, 77, 77);">Ctrl + C：退出选择/中止命令</font>

<h2 id="Uj528">名称含义</h2>
| 缩写 | 含义 |  | 演示/备注 |
| :--- | :--- | --- | :--- |
| **<font style="color:rgb(77, 77, 77);">pwd</font>** | <font style="color:rgb(77, 77, 77);">显示当前目录的路径</font> |  | ![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760520214357-041a556c-82f9-433d-b670-e7acf846baee.png)<font style="color:rgb(77, 77, 77);"></font> |
| **<font style="color:rgb(77, 77, 77);">which</font>** | <font style="color:rgb(77, 77, 77);">查看命令的可执行文件所在路径</font> |  | ![](https://cdn.nlark.com/yuque/0/2025/jpeg/52691782/1760520247856-6b847850-250f-4a74-ac8e-927d9044c1aa.jpeg) |
| **<font style="color:rgb(77, 77, 77);">ls</font>**<br/> | <font style="color:rgba(0, 0, 0, 0.75);">列出文件和目录 </font> | <font style="color:rgb(77, 77, 77);">【</font>**<font style="color:rgb(77, 77, 77);">常用参数</font>**<font style="color:rgb(77, 77, 77);">】</font><br/>+ `<font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">-a</font>`<font style="color:rgba(0, 0, 0, 0.75);">显示所有文件和目录包括隐藏的</font><br/>+ `<font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">-l</font>`<font style="color:rgb(77, 77, 77);">显示详细列表</font><br/>+ `<font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">-h</font>`<font style="color:rgb(77, 77, 77);">适合人类阅读的</font><br/>+ `<font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">-t</font>`<font style="color:rgb(77, 77, 77);">按文件最近一次修改时间排序</font><br/>+ `<font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">-i</font>`<font style="color:rgb(77, 77, 77);">显示文件的</font>`<font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">inode</font>`<font style="color:rgb(77, 77, 77);">（</font>`<font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">inode</font>`<font style="color:rgb(77, 77, 77);">是文件内容的标识）</font> |  |
| **<font style="color:rgb(77, 77, 77);">cd</font>** | <font style="color:rgb(77, 77, 77);">切换目录</font><br/> | ```plain cd / --> 跳转到根目录   cd ~ --> 跳转到家目录   cd .. --> 跳转到上级目录   cd ./home --> 跳转到当前目录的home目录下   cd /home/lion --> 跳转到根目录下的home目录下的lion目录   cd --> 不添加任何参数，也是回到家目录   ```  | <font style="color:rgb(77, 77, 77);">相对路径 在输入路径时，最前面不是 / 或者 ~，表示相对 当前目录 所在的目录位置</font><br/><font style="color:rgba(0, 0, 0, 0.75);">   </font><font style="color:rgba(0, 0, 0, 0.75);">绝对路径 在输入路径时，最前面是 / 或者 ~，表示从 根目录/家目录 开始的具体目录位置</font> |
| **<font style="color:rgb(77, 77, 77);">touch</font>** | <font style="color:rgba(0, 0, 0, 0.75);">创建文件或修改文件时间   </font> | + <font style="color:rgba(0, 0, 0, 0.75);">如果文件 不存在，可以创建一个空白文件</font><br/>+ <font style="color:rgba(0, 0, 0, 0.75);">如果文件 已经存在，可以修改文件的末次修改日期</font> |  |
| **<font style="color:rgb(77, 77, 77);">mkdir</font>** | <font style="color:rgba(0, 0, 0, 0.75);">创建一个新的目录</font> |  |  |
| <h4 id="rm"><font style="color:rgb(79, 79, 79);">rm</font></h4> | <font style="color:rgba(0, 0, 0, 0.75);">删除文件或目录</font> | + <font style="color:rgba(0, 0, 0, 0.75);">-f: 强制删除</font><br/>+ <font style="color:rgba(0, 0, 0, 0.75);">-r: 递归地删除目录下的内容</font> | <font style="color:rgb(0, 0, 0);background-color:rgb(248, 248, 64);">删除后不能恢复</font><br/><font style="color:rgba(0, 0, 0, 0.75);">删除文件夹 时必须加 -r</font> |
| **<font style="color:rgb(77, 77, 77);">mv</font>** | <font style="color:rgba(0, 0, 0, 0.75);">移动文件与目录，或修改文件与目录的名称</font> | | <font style="color:rgb(0, 0, 0);background-color:rgb(248, 248, 64);"></font> |
| **<font style="color:rgb(77, 77, 77);">cat</font>**<font style="color:rgb(77, 77, 77);"></font> | <font style="color:rgb(77, 77, 77);">从第一行开始一次性显示文件所有内容，更适合查看小的文件。</font> |  |  |
| **<font style="color:rgb(77, 77, 77);">tac</font>** | <font style="color:rgba(0, 0, 0, 0.75);">从最后一行开始显示</font> | | <font style="color:rgb(0, 0, 0);background-color:rgb(248, 248, 64);"></font> |
| **<font style="color:rgb(77, 77, 77);">nl</font>** | <font style="color:rgba(0, 0, 0, 0.75);">连同行号显示</font> | | <font style="color:rgb(0, 0, 0);background-color:rgb(248, 248, 64);"></font> |
| **<font style="color:rgb(77, 77, 77);">more</font>** | <font style="color:rgb(51, 51, 51);background-color:rgb(250, 252, 253);"></font> | | <font style="color:rgb(0, 0, 0);background-color:rgb(248, 248, 64);"></font> |
| **<font style="color:rgb(77, 77, 77);">head</font>** | <font style="color:rgba(0, 0, 0, 0.75);">只看头几行</font> | | <font style="color:rgb(0, 0, 0);background-color:rgb(248, 248, 64);"></font> |
| **<font style="color:rgb(77, 77, 77);">tail</font>** | <font style="color:rgba(0, 0, 0, 0.75);">只看末尾几行</font> | | <font style="color:rgb(0, 0, 0);background-color:rgb(248, 248, 64);"></font> |
| **<font style="color:rgb(77, 77, 77);">less</font>** | <font style="color:rgb(77, 77, 77);">分页显示文件内容，更适合查看大的文件。</font> | + 空格键：前进一页（一个屏幕）；<br/>+ b 键：后退一页；<br/>+ 回车键：前进一行；<br/>+ y 键：后退一行；<br/>+ 上下键：回退或前进一行；<br/>+ d 键：前进半页；<br/>+ u 键：后退半页；<br/>+ q 键：停止读取文件，中止less命令；<br/>+ = 键：显示当前页面的内容是文件中的第几行到第几行以及一些其它关于本页内容的详细信息；<br/>+ h 键：显示帮助文档；<br/>+ / 键：进入搜索模式后，按 n 键跳到一个符合项目，按 N 键跳到上一个符合项目，同时也可以输入正则表达式匹配。 |  |




4. 其他命令

| 命令 | 功能 | |
| --- | --- | --- |
| **<font style="color:rgb(77, 77, 77);">find -name "*扩展名"</font>** | <font style="color:rgba(0, 0, 0, 0.75);">查找指定路径下扩展名是... 的文件，包括子目录</font> | |
| **<font style="color:rgb(77, 77, 77);">find -name "*1*"</font>** | <font style="color:rgba(0, 0, 0, 0.75);">搜索桌面目录下，文件名包含 1 的文件</font> | |
| **<font style="color:rgb(77, 77, 77);">find -name "1*"</font>** | <font style="color:rgba(0, 0, 0, 0.75);">搜索桌面目录下，以数字 1 开头的文件</font> | |
| <font style="color:rgb(0, 0, 0);background-color:rgb(250, 250, 250);"></font> | <font style="color:rgba(0, 0, 0, 0.75);"></font> | |
| <font style="color:rgb(0, 0, 0);background-color:rgb(250, 250, 250);"></font> | <font style="color:rgba(0, 0, 0, 0.75);"></font> | |




<h1 id="UbVaC">三、基础解题</h1>
<h3 id="iJS1I">view_source</h3>
+ <font style="color:rgba(0, 0, 0, 0.75);">获得管理员权限：Fn+F12/ctrl+shift+l 查看源代码：ctrl+u</font>

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760607238646-2c5cf620-042c-4d66-a360-e71631480ae5.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760614783196-f96a9350-cec5-42bb-947b-8a93bd011e6e.png)

<h3 id="tb4St">get_post</h3>
+ hackbar抓包

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760607610109-dfe811fd-5f51-4fe5-b033-3e0d0c18645f.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760607347372-1c601e84-f936-4227-8c3a-d9fefdcc4fed.png)

<h3 id="LqFi3">robots</h3>
+ "/robots.txt": 表示一个官方的对于爬虫的协议

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760608212349-5d337bd2-8af7-447a-95ce-a152bf6fd0cb.png)

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760607902619-8b89d35f-4017-457a-b94f-6e5309352b17.png)

<h3 id="wQIBt">backup(备份文件)</h3>
+ 备份文件的后缀名：.git/.svn/.swp/.bak等
+ 路径扫描：Kali -->

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760608534503-b97c0ed4-a4cb-4595-81a3-6820ab55aede.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760608563505-04e05620-883a-433f-b516-dd869218fadf.png)

<h3 id="yUXJj">cookie</h3>
![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760611878420-f693de8f-298a-4c7c-adb3-093953ee2ba8.png)

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760611853787-06d8e195-a1e5-400a-a695-6ed751d8dd73.png)

<h3 id="H5vI4">disabled_button</h3>
+ 前端修改，将disabled 转换为 enable
+ 可以用HB抓一下

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760612299706-c98f8e56-b916-400a-bec0-72f827b86196.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760612270462-f867d7e6-ae9a-4f22-9106-21965f153f46.png)

<h3 id="ONhAg">7.simple_is</h3>
+ <font style="color:rgb(39, 46, 59);">JS的理解，python脚本的编写(把ASCII码值转化为原始字符串后输出）</font>

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760690188513-14fe03df-3ae5-45c0-bb89-8fb7e7d24fe5.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760690203763-da0fef7c-5c41-4a3c-8a61-abfbb1ed9cf3.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760690152779-3b206a92-0e0c-47cd-9db3-fc513cd99581.png)

<h3 id="EU2wv">8.xff_referer（伪造请求头）</h3>
+ <font style="color:rgb(39, 46, 59);">xff：</font><font style="color:rgba(0, 0, 0, 0.75);">X-Forwarded-For（XFF）是用来识别通过HTTP代理或负载均衡方式连接到Web服务器的客户端最原始的IP地址的HTTP请求头字段。</font>
+ <font style="color:rgb(39, 46, 59);">HTTP Referer ：是一个 HTTP 请求头字段，用于标识请求资源的来源地址。它允许服务器识别用户访问的来源页面，这些信息可以用于分析、日志记录、优化缓存等。</font>

<font style="background-color:#F1A2AB;">为什么说我答案不正确</font>

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760613282348-d860af2a-2bc0-4001-976b-2d309063030e.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760613624069-76361ed9-d78b-46b2-b0ff-a94644684e73.png)

<h3 id="mS6lD">9.weak_auth</h3>
![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760699456452-73dc62e8-d0e5-4d2c-81f6-4d177b1742f5.png)

<h3 id="XhJrE">10.command_execution</h3>
![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760692972337-97e36cdf-7c60-46c1-b7b2-c90ece244cb9.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760692928427-6bfccfd2-bf22-4761-b076-2f33af828da3.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760693311973-21c85dd3-f826-45cd-92fe-2918614938e2.png)

<h3 id="i2yut">11.simple_php</h3>
![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760698366176-e44a58de-c13d-4795-887a-04afe7456650.png)![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760788232684-487f32c7-2b61-402c-b3e3-3cfee43a81fa.png)

<h1 id="zHT0F">四、python脚本</h1>
```plain
import hashlib
import time

def check_md5(input_str, target_prefix):
    """检查输入字符串的MD5哈希值前n位是否匹配目标前缀"""
    md5_hash = hashlib.md5(input_str.encode()).hexdigest()
    return md5_hash.startswith(target_prefix), md5_hash

def search_by_incremental(target_prefix, start=0, end=10000000):
    """通过递增数字搜索匹配的MD5哈希"""
    print(f"开始递增搜索MD5前{len(target_prefix)}位为'{target_prefix}'的数字...")
    print(f"搜索范围: {start} 到 {end}")
    
    start_time = time.time()
    
    for num in range(start, end):
        # 将数字转换为字符串
        num_str = str(num)
        
        # 检查MD5哈希
        is_match, md5_hash = check_md5(num_str, target_prefix)
        
        if is_match:
            elapsed_time = time.time() - start_time
            print(f"\n找到匹配!")
            print(f"数字: '{num_str}'")
            print(f"MD5哈希: {md5_hash}")
            print(f"前{len(target_prefix)}位: {md5_hash[:len(target_prefix)]}")
            print(f"搜索耗时: {elapsed_time:.2f} 秒")
            print(f"总共尝试了 {num - start + 1} 个数字")
            return num_str, md5_hash
        
        # 每100000次显示进度
        if (num + 1) % 100000 == 0:
            elapsed_time = time.time() - start_time
            print(f"已尝试 {num + 1} 个数字... (耗时: {elapsed_time:.2f} 秒)")
    
    elapsed_time = time.time() - start_time
    print(f"\n搜索完成")
    print(f"在 {start} 到 {end} 范围内未找到匹配")
    print(f"总共尝试了 {end - start} 个数字")
    print(f"搜索耗时: {elapsed_time:.2f} 秒")
    return None, None

def main():
    """主函数"""
    # 目标MD5前缀
    target_prefix = "15af95"
    
    print("=" * 60)
    print(f"MD5前缀查找器 - 递增数字搜索法")
    print(f"目标: 找到一个数字，其MD5哈希的前{len(target_prefix)}位为 '{target_prefix}'")
    print("=" * 60)
    
    # 开始搜索
    result, md5_hash = search_by_incremental(target_prefix, end=10000000)
    
    if result:
        print("\n✅ 搜索成功!")
        print(f"找到的数字: {result}")
        print(f"MD5哈希: {md5_hash}")
    else:
        print("\n❌ 搜索失败")
        print(f"在指定范围内未找到MD5前缀为 '{target_prefix}' 的数字")

if __name__ == "__main__":
    main()
```

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760809803858-654fdb27-477a-4cf8-a0a9-3215abd83d44.png)

<h1 id="JDXkh">五、http协议（<font style="color:rgba(0, 0, 0, 0.9);">超文本传输协议）</font></h1>
<h2 id="mM5eh">（一）概念</h2>
<font style="color:rgba(0, 0, 0, 0.9);">应用层协议，浏览器 ⇄ 服务器之间“对话”的母语，客户端发送请求报文，服务端回送响应报文。http支持传输各个类型的内容。</font>![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1754102782297-3096de77-b412-4f04-ada7-7e716454495d.png)

<h2 id="CfExp">（二）一次完整 HTTP 请求幕后流程</h2>
1. <font style="color:rgba(0, 0, 0, 0.9);">浏览器解析 URL → 拿到协议/域名/端口/路径</font>
2. <font style="color:rgba(0, 0, 0, 0.9);">DNS 解析 → 拿到 IP</font>
3. <font style="color:rgba(0, 0, 0, 0.9);">TCP 三次握手（80 端口）</font>
4. <font style="color:rgba(0, 0, 0, 0.9);">浏览器拼装请求报文发出去——纯文本</font>
5. <font style="color:rgba(0, 0, 0, 0.9);">服务器回“响应报文”</font>

<h2 id="R7zwO">（三）http请求与回应报文结构</h2>
![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1760790729312-5a27c198-5ef8-45f3-8a33-d003f7ce9f66.png)

1. 方法（未完待续）

| get | 一种获取的方法 |
| --- | --- |
| post | 偏向于传输提交数据的方法 |
| referrer | |


2. 状态码（未完待续）

| 2×× | 被正常处理 |  |
| --- | --- | --- |
| 3×× | 重定向，会让浏览器执行某些特别的处理 | 304：可以使用缓存的内容 |
| 4×× | 客户端错误 | 404：被服务器拒绝/找不到请求资源 |
| 5×× | 服务端错误 | 500：服务器内部发生错误或故障 |


3. 首部：<font style="color:rgba(0, 0, 0, 0.9);">由**字段名（Field Name）和字段值（Field Value）**组成；</font>`<font style="color:rgba(0, 0, 0, 0.9);">Field-Name: Field-Value</font>`

| 类型 | 描述 |
| --- | --- |
| **通用首部（General Headers）** | 请求和响应都可以使用，如 `Date`、`Connection`、`Cache-Control` |
| **请求首部（Request Headers）** | 仅出现在请求中，如 `User-Agent`、`Accept`、`Authorization` |
| **响应首部（Response Headers）** | 仅出现在响应中，如 `Server`、`Set-Cookie`、`Location` |
| **实体首部（Entity Headers）** | 描述消息体内容，如 `Content-Type`、`Content-Length`、`Last-Modified` |


4. 请求URL

![](https://cdn.nlark.com/yuque/0/2025/png/52691782/1754102456649-34f8bc96-a907-4425-8f06-0468995c2983.png)



<h2 id="FGK1p">（四）http 和 https 的区别</h2>
|  | HTTP | HTTPS (=HTTP+TLS) |
| --- | --- | --- |
| 端口 | 80 | 443 |
| 明文/密文 | 全程明文 | 先TLS握手再加密传输 |
| 证书 | 不需要 | 需CA签发证书（可白嫖Let’s Encrypt） |
| 性能 | 少一次握手 | TLS 1.3 仅多1-RTT，几乎无感 |
| SEO | 谷歌降权 | 优先索引 |
| 浏览器标识 | 灰色“不安全” | 小锁+绿色 |


