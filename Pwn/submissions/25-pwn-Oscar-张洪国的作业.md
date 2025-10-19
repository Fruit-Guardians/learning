第一题：了解了Linux中基本的命令，如nc ls cat flag等

![](https://cdn.nlark.com/yuque/0/2025/png/61871836/1760846963646-ef193585-715a-46cd-be76-ddc52d1256ee.png)

![](https://cdn.nlark.com/yuque/0/2025/png/61871836/1760846962640-46aea4e0-d60a-4b1b-ae68-684f77bb22e0.png)



第二题： 先使用IDA反汇编，并从代码中获取到密码为7038329

接着在虚拟机中nc连接靶机，输入密码，获得flag![](https://cdn.nlark.com/yuque/0/2025/png/61871836/1760846964055-3591600b-03d2-4fcb-b625-882c2b2a6d38.png)![](https://cdn.nlark.com/yuque/0/2025/png/61871836/1760846964232-051b600a-edb1-464e-9576-be1038da3998.png)

![](https://cdn.nlark.com/yuque/0/2025/png/61871836/1760846963341-9795ae9f-217b-4e96-855d-54d6bbe16a4a.png)



第三题：先使用IDA反汇编，再查看fun函数逻辑

这里使用了ai，知道了代码的需求，即在一小时内输入，再学习了管道自动化在CTF中的应用

最后在虚拟机中得到flag

![](https://cdn.nlark.com/yuque/0/2025/png/61871836/1760846964286-3757d1f0-a615-46e9-b296-cc2f1e3018b2.png)![](https://cdn.nlark.com/yuque/0/2025/png/61871836/1760846964462-7ec56b81-4d89-435f-9b5e-4c12ef57b1f2.png)![](https://cdn.nlark.com/yuque/0/2025/png/61871836/1760846963271-1e4d8ca6-b324-4018-a8b2-fe8771eb2c5c.png)![](https://cdn.nlark.com/yuque/0/2025/png/61871836/1760846964591-2c958fd9-5448-4f8d-ba2f-1eadd1a6b7f5.png)![](https://cdn.nlark.com/yuque/0/2025/png/61871836/1760846965281-33ca9cc0-7786-420b-bfdf-6c5f4afc1c2f.png)

