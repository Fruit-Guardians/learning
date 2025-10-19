P1

看起来很简单，实则也简单

（主要飞书中介绍只要nc ls cat就可解题）

先用nc连接靶机地址，接ls查看文件，最后cat flag就OK了 

![](https://cdn.nlark.com/yuque/0/2025/png/61872857/1760851083357-3d1ca429-29b1-4b59-b9a0-46806395c207.png)

P2

提到了有关ida的知识，那么我们下载文件并将文件用ida打开，双击点开main函数，tap查看具体内容

![](https://cdn.nlark.com/yuque/0/2025/png/61872857/1760851100211-60859e7c-2476-41bd-b2e9-5c40112ecf4e.png)

易观察到if语句，得知7038329为正确密码

进入虚拟机输入再cat flag即可得到正确答案

![](https://cdn.nlark.com/yuque/0/2025/png/61872857/1760851111192-987cf032-dcc5-4bee-9161-e85beef1fe09.png)

p3

同理先进行ida分析

![](https://cdn.nlark.com/yuque/0/2025/png/61872857/1760851121928-7ae3667c-2c2e-42b6-b72d-90a81268006f.png)

需要一定的语言知识

输入数为v2，每次输入，vi加1并进行判断v1是否小于0，使v1小于0（目的），但初始v1为0。

此处需要了解整数溢出相关知识

可知当数为32768时为-32768

即我们需要不断循环

使用linux内置yes命令

![](https://cdn.nlark.com/yuque/0/2025/png/61872857/1760851136177-9e0e49c5-dfd1-4dfb-b827-b3814d5c8f56.png)

or deepseek神力

![](https://cdn.nlark.com/yuque/0/2025/png/61872857/1760851146798-3d7331b3-108a-4db3-b713-b8e6d1d3c138.png)



