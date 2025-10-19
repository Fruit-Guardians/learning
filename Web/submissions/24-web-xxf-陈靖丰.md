## 1.F12+HackBar
![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760768896651-65ecb755-e219-4628-abab-870b20c6efe2.png)

## 2.Burpsuit
设置8080端口代理和证书

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760769103275-7ceda89c-f5d2-46a5-8273-b763ecdeee61.png)

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760769129886-b8bf5887-9c01-4b94-8745-c8a2598c37a8.png)

成功抓包

## 3.AI
deepseek和豆包

## 4.攻防世界
**view_source**

**1.**![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760769416324-4bcca5ae-aa24-4b8d-990a-6d3147102446.png)

F12用看前端代码，找到flag



get_post

1.![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760769545782-c95fb500-406f-44c2-ae5a-a3719e903a61.png)

利用hackbar按照要求，get和post请求完成传参，并获取flag

**robots**

**1.一般有关于robots协议的都先从robots.txt进入**

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760769896003-c5412363-7717-4626-96ee-8460b1edfae3.png)

观察看到明显的flag所在的php文件中

访问得到

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760769953015-7c23749a-d136-4f31-a2c2-dd23841e8e0a.png)

## Linux学习以及环境搭建
这里我用的是虚拟机VM，以及系统kali

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760770117598-052c67e2-728d-4803-bc25-7447520a935f.png)

因为之前大搭建过直接展示成品图，大概步骤就是创建，然后找ISO镜像，再调其他系统配置就可以了



# Linux基础命令学习
`cd /`进入根目录

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760860594965-0f3b9474-4883-4081-beb2-14c2e7ca9720.png)

`cd /home`进入根目录下的home目录

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760860699045-d7087955-f849-4a35-9c9e-233260d2039b.png)

`cd ../`切回上一级（当前目录下的所在的上一级）

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760860739200-47650a59-7d6f-4bf7-b8f3-1c5f40ce81a5.png)

`cd -`切换到上一个命令打开的目录

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760860893052-4d29d6e8-50e4-4b47-9faa-fdb062b767c8.png)

`ls`查看当前目录下的所有目录和文件

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760861030306-df959a44-1d2d-468a-98d9-ed09eed069b6.png)

`ls -a`和ls作用一样，但多了隐藏文件

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760861088578-c8d7d8bb-4a22-4803-b03a-c1c8627cfe27.png)

`ls /dir（文件名或目录）`查看指定目录或文件夹下的所有目录或文件

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760861280304-9af22d31-bd5f-47c7-bf67-67be51fc5267.png) 

`vim 文件名` 进入文档后，需要编辑按i或者o，想要存储先按esc，再输入:wq，即编辑完保存文件

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760861527301-ba50ac06-8694-4aa4-903f-14c0c443841c.png)

![](https://cdn.nlark.com/yuque/0/2025/png/54970229/1760861671660-d7d62d96-07cf-422f-912d-dcaba947382f.png)

