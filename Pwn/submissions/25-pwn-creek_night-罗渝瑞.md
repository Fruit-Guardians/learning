<h1 id="mfYNd">P1</h1>
![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760794354094-bd84b470-5f07-474b-93d4-e9dc8499b738.png)

拿到第一道题后无从下手，经过一番搜索后决定先用ida将附件打开

发现报了

The processor type 'metapc' is not included in the installed version of IDA. Please check our web site for information about ordering additional processor modules.

的错

经查证是安装路径中带有中文，于是重装了ida

顺利打开附件

![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760794874844-54f6e7d3-f5cd-496b-94fb-da71d68c309b.png)

随后在打开view-open subviews-Strings

![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760794942650-d25b2dda-d1f8-4bc9-ae95-03e4778bf304.png)

在/bin/sh中找到command选中按x

<font style="color:rgb(77, 77, 77);">发现/bin/sh的Address在main函数里</font>

<font style="color:rgb(77, 77, 77);">选中main函数进行反编译</font>

![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760795227211-f07e6192-b0bb-4dd6-9b14-5f6b14c49292.png)

<font style="color:rgb(77, 77, 77);">发现main函数只有一个system函数，直接调用了/bin/sh</font>

<font style="color:rgb(77, 77, 77);">所以直接用nc连接到靶机即可获取权限</font>

![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760795444903-20c96c58-7047-477c-8406-e2eeee84a083.png)

使用ls指令，发现flag就在里面

![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760795631504-c72caf1f-8770-42e5-9e76-328e53d79e0e.png)

<font style="color:rgb(77, 77, 77);">使用cat flag得到flag</font>

![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760795718023-f6b4f094-ea52-4bf4-9ef1-1e54a832c162.png)

<h1 id="RrNBT">P2</h1>
![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760795956577-b05b65ff-c26d-498a-aecc-d03093363108.png)

有了第一道题的经验，先在ida对附件进行逆向得到

![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760796219159-7aa0cdf1-2fee-4cd2-ae32-193a0586624b.png)

非常轻松的得到了密码7038329

连接到靶机之后输入密码然后cat flag

![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760796475748-0a442912-4ab7-4a80-ac59-0b3958c6c756.png)

<h1 id="jqrl0">P3</h1>
![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760799254324-6cc2aa37-67ea-48d1-a8eb-9ef19946b5f6.png)

先进行IDA分析

同第二题的步骤可以找到func

![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760799668259-c903e184-7b57-43fe-9a18-e38dd3167d14.png)

函数逻辑大概是当你输入一个大于0的v2，函数循环且v1自增，v1小于0时就可获得flag

初看有些荒谬，但仔细思考便可发现v1为int16类型，范围为<font style="color:rgb(143,149,158);">-32768-32767</font>所以只需持续输入v2直至v1溢出为负数即可

查询得到linux中确实存在这么一个功能的命令，即yes命令，在学习后写出如下命令

yes 1 | nc 47.94.110.224 30749

运行后成功获得flag

![](https://cdn.nlark.com/yuque/0/2025/png/61847283/1760801062750-0c1f2b81-97b5-401e-8794-10ee7e5d7717.png)

