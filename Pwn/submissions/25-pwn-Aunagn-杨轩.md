第一题:

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760771970186-b2d3100b-4db1-4f79-9c7c-36d8e2f054cc.png)![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760772029026-c7782988-6a9e-418b-ae06-ba7854e64d7f.png)![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760772041105-5a53ca02-61f4-4330-9e00-b8fa9c3a37d7.png)

先了解了一下nc,ls,cat命令作用

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760771820786-e65a80cd-557b-45e0-9b91-69a72c02def7.png)

然后打开Linux虚拟机终端依次输入,得到flag

第二题:

把附件拖进ida窗口里,然后tab反汇编成c语言格式,找到密码之后进入Linux虚拟机终端,nc一下,然后输入刚才找到的密码,回车,cat flag就得到了flag

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760772469094-dfd2802e-5339-4019-a5ff-23154b11c2cc.png)

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760772167648-a0c1cd8f-239c-4c7a-b00b-25c799226073.png)

第三题:

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760772945170-0868211e-43b9-44b9-af3b-3af51ad4ccaf.png)

还是先把附件拖入ida

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760772955935-d1815d55-983c-4c46-bf01-141a1fe607be.png)

然后tab反汇编

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760772961903-c5aa0bef-002d-452c-90d2-5b1520f9384b.png)

双击func看到函数内容,看不太懂,问ai:![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760773185465-fc600527-4eec-4a4d-b99e-fcd231c82a9a.png)![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760773220888-1f262c6c-e47c-4a38-8edb-c3bbb5a300f7.png)

得到解题方法,查找"yes"命令和"管道"的用法:![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760773481481-2f573f1b-b83a-453f-8592-a64bf25d42f2.png)![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760773481407-cfe2dd62-cab4-4f20-8caf-2e3923bf06a6.png)

![](https://cdn.nlark.com/yuque/0/2025/png/61844100/1760772968889-79c4013a-6c18-41f8-940e-7866a530facc.png)

然后打开Linux终端,输入yes 1 | nc 47.95.4.104,就能得到flag

