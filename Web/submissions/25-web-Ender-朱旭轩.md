###工具###

---

##1.浏览器开发者工具F12##
<img width="2560" height="1600" alt="屏幕截图 2025-10-15 202909" src="https://github.com/user-attachments/assets/3d8571d9-c2ac-456f-996c-c4e69ea482bf" />
##2.HackBar##
<img width="2560" height="1528" alt="屏幕截图 2025-10-19 154418" src="https://github.com/user-attachments/assets/0637c247-8f4f-45d6-8b40-5cc2b0e44f2d" />
##3.Burp Suit##
还不太明白用法（这全英文给我干不会了）
<img width="2378" height="1339" alt="屏幕截图 2025-10-19 154549" src="https://github.com/user-attachments/assets/8554b6a7-558c-421a-8ead-d1cd02f5cf28" />
##4.AI##
这个夸克很好用，直接可以在原页面开小窗问，很顺手
<img width="2560" height="1600" alt="屏幕截图 2025-10-19 124152" src="https://github.com/user-attachments/assets/a15fa98c-2046-4967-9d59-ad669f64ff7b" />

---

###基础题目练习###

---

##view_source##
最简单的一个，直接f12查看源代码（应该是这样吧）
<img width="2560" height="1600" alt="屏幕截图 2025-10-19 123840" src="https://github.com/user-attachments/assets/704674c3-071e-4301-9b29-450b6c34aeb2" />
##get_post##
嗯对，如图所示
<img width="2560" height="1600" alt="屏幕截图 2025-10-19 132741" src="https://github.com/user-attachments/assets/7ac808c2-a531-4ea3-8064-326e1d48baa8" />
##用ai写一个python脚本，要求找到一个值经过md5加密后的前6位是15af95##
直接交给夸克了

---

import hashlib

def find_md5_prefix(prefix):
    counter = 0
    while True:
        # 将计数器转换为字符串并进行MD5哈希计算
        hash_object = hashlib.md5(str(counter).encode())
        md5_hash = hash_object.hexdigest()
        
        # 检查哈希值的前六位是否匹配给定的前缀
        if md5_hash.startswith(prefix):
            return counter, md5_hash
        
        counter += 1

# 要查找的前缀
prefix = "15af95"
result_counter, result_hash = find_md5_prefix(prefix)

print(f"找到符合条件的字符串: {result_counter}")
print(f"其MD5哈希值为: {result_hash}")
结果如下

<img width="2560" height="1600" alt="屏幕截图 2025-10-19 155734" src="https://github.com/user-attachments/assets/53697e9e-c4cf-4814-9bb6-674afcc684c9" />
##robots##
据夸克查询可得：Robots协议（也称为爬虫协议或机器人协议）是一种网站与网络爬虫之间的约定，用于指导爬虫哪些页面可以抓取，哪些页面不可以抓取。它的核心是一个名为robots.txt的文本文件，通常放置在网站的根目录下。通过该文件，网站管理员可以控制爬虫的访问行为，从而保护网站的隐私、优化服务器性能，并引导爬虫抓取重要内容。
嗯（原来还有这种东西），直接HackBar访问robots.txt文件，结果如下图
<img width="2560" height="1600" alt="屏幕截图 2025-10-19 133402" src="https://github.com/user-attachments/assets/d4fa5f14-00f4-49c6-91fe-ce4606037d63" />
###Linux基础###

---

##搭建##
直接从网上资源下载Ubantu，然后下载VMware虚拟机，看着挺官方，但是需要钱激活
听说w11自带虚拟机，还听说VMware从应用商城可以直接下，不要钱，晚点再折腾修改，，，
已严肃学习Linux基础知识qwq
