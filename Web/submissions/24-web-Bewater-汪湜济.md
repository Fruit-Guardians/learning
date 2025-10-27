+ 工具

Hackbar

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761576365242-b00bfbcd-0745-455c-a0cd-ff53ef3a2226.png)

Burp Suite

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761576399448-6b542f2a-6173-4be7-b0c0-bcf9aea2a2ab.png)

+ 题目



view_source

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761576484486-be46e10f-75fa-43d9-a135-0b0478bb25ac.png)

直接按F12易得



get_post

第一步直接在URL后加？a=2即可

第二步新建一个文本文档，然后写入如下指令![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761576610312-043cf2f5-cc1f-4936-ac43-36db86601dda.png)

将该文本文档另存为HTML文件后点开它，再点击发送post请求即可

（该步骤还可以直接在burpsuite中进行）

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761576686646-12b8ccf9-94fe-49e7-af2e-3c29f10d9d7f.png)



robots

在URL后直接加上/robots.txt易得![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761576777356-d3c269f4-4bcc-47e7-b894-9b65645b618e.png)

再根据提示（flag……）把该段文字直接写在URL后/f1ag_1s_h3re.php即可得到flag

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761576895975-85653047-7588-4cd8-b5ee-279c4c351c3f.png)





+ Linux

下载

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761577221484-4906ca10-3aa2-426f-b613-62e51654951a.png)

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761577223173-1d7e2dc7-6246-468d-8df0-c2806b278a72.png)

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761577224798-ca879124-0b6a-42fe-809b-08e222ea2deb.png)

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761577226723-ad8f0e6e-67a7-4f5a-84cb-966243b89944.png)

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761577228457-4c554e6d-bc0a-4a23-9b62-6d791a78dbe7.png)

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761577230090-f46f3132-2975-4dae-85d1-977a93b6f1b3.png)

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761577231806-98d4478a-1e64-426e-939a-21c0dcc368d8.png)

![](https://cdn.nlark.com/yuque/0/2025/png/55526765/1761577234307-1a5d2f9c-991f-42ae-adaa-b63a3438dd33.png)

初始账号密码都是kali

ctrl+shift+t 打开终端

输入一下指令

sudo apt update（检查更新）

apt list --upgradable（列出清单）

sudo apt upgrade -y（更新并确认）

sudo apt dist-upgrade（深度更新）

sudo apt autoremove（删除安装包）



关于kali的一些命令这里就从略了，笔者已经用了一段时间的kali系统了。



