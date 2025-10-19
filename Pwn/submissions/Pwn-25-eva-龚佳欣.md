解题wp

题目1：

开启靶机，下载test到文件，从文件里将其拖至ida查看附件内容，点击左侧的main函数出现下图

![](https://cdn.nlark.com/yuque/0/2025/png/61848370/1760864906279-fa5d51b5-9596-4962-ab63-a08bd8855d1a.png)

然后进入虚拟机终端，输入nc连接靶机，进入平台复制ip和端口，再输入ls查看目录内容

![](https://cdn.nlark.com/yuque/0/2025/png/61848370/1760803638522-c41fa91e-9b29-4800-b241-d03ce1ede251.png)

找到flag，输入cat flag即可获取flag内容，粘贴获取的flag内容然后submit，解题成功

![](https://cdn.nlark.com/yuque/0/2025/png/61848370/1760867344510-67706359-888c-43f3-a347-30fca5b93e2f.png)

题目2：同题目一，首先将door附件下载至文档，然后拖拽至ida查看得到密码7838329

![](https://cdn.nlark.com/yuque/0/2025/png/61848370/1760865156402-1bd416e2-efef-4265-86f7-cbcd08742490.png)由于不知名原因进不了比赛平台，只能打本地,所以直接进入虚拟机终端<font style="color:rgb(28, 31, 35);">，执行ls查看目录显示有door文件，然后执行./door,再输入在ida中得到的密码，本地环境看不到flag，但由提示可知流程已走通，测试成功。</font>

![](https://cdn.nlark.com/yuque/0/2025/png/61848370/1760866542692-02fd6fdb-2752-43c9-962c-d5b56893139d.png)

