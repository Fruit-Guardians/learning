#一,工具

<font style="color:#3370ff;">1.</font>**Hackbar**

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761209378382-1518aaa0-3236-4dbd-8deb-c40be26d7bdb.png)

2.**Burp Suite**

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761209337128-5d617d0d-05c5-408e-adca-b83f3899d89a.png)

**3.ai:ChatGPT,DeepSeek,豆包**

**4.f12**

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761209465758-0bef3436-5fcd-4306-a123-035affaa4638.png)

**#二,题目**

**1.**![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761209485455-fb2fee65-6d90-4f01-9d83-4b238c78ee74.png)

f12按一下就有flag

2.![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761209531129-ca66d3a1-8ece-485f-8419-f3af87edd9a3.png)![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761209538303-82bb2d0c-966f-427f-a5be-fd4fdc82dfc2.png)

看不懂,问ai:get的格式为/?参数=...

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761209713509-eafa1407-23bc-4ee2-af5c-0ce54c2995d4.png)![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761209713493-6aeb314e-6073-417c-b69d-414d0aedd9d2.png)

post方式查了一下要用javascript语法,没学过,直接复制粘贴ai写的了,得到flag

3.交给chatgpt:![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761209991042-49fbc6f9-62e8-4e20-9407-01d561e006aa.png)

代码如下:

`import hashlib



target_prefix = "15af95"



i = 0

while True:

    s = str(i).encode()  # 将数字转为字节

    md5_hash = hashlib.md5(s).hexdigest()  # 计算MD5

    if md5_hash.startswith(target_prefix):

        print(f"找到匹配值: {i}")

        print(f"MD5哈希: {md5_hash}")

        break

    i += 1

`

#三,Linux环境

1.环境搭建(之前下好了)

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761210186249-05b099c7-baee-402a-bee5-8ee611fd6d49.png)

2.基础命令学习

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761212098432-eba3a371-2663-4b4a-ac77-b56e59135864.png)

听网课

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1761212100898-f1f07577-ba85-41eb-ad54-ad2bf5b9002a.png)

菜鸟教程网



