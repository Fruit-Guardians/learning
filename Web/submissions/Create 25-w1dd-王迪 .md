####插件
<img width="1241" height="553" alt="image" src="https://github.com/user-attachments/assets/21af1bbb-c741-4cd6-be1a-fe920507df5d" />
####攻防世界
题一Ctrl+U获取源代码
题二网址后加a=1然后hack bar拓展输入b=2执行
####AI生成
pathon
import hashlib
import random
import string
from threading import Thread
from queue import Queue

# 目标前缀和结果存储队列
TARGET_PREFIX = "15af95"
result_queue = Queue()
stop_flag = False  # 找到结果后终止所有线程

def generate_random_str(length=10):
    """生成随机字符串（包含字母+数字）"""
    return ''.join(random.choices(string.ascii_letters + string.digits, k=length))

def md5_check():
    """循环生成并验证MD5前缀"""
    global stop_flag
    while not stop_flag:
        # 生成随机字符串（可调整length参数改变长度）
        random_str = generate_random_str(length=12)
        # MD5加密（转小写，确保前缀匹配格式）
        md5_hash = hashlib.md5(random_str.encode()).hexdigest().lower()
        # 验证前6位是否匹配
        if md5_hash.startswith(TARGET_PREFIX):
            stop_flag = True
            result_queue.put((random_str, md5_hash))
            break

if __name__ == "__main__":
    print(f"开始查找MD5前6位为{TARGET_PREFIX}的值...")
    print("（按Ctrl+C可终止程序）")
    
    # 创建多线程（线程数可根据CPU核心数调整，建议4-8个）
    thread_count = 6
    threads = []
    for _ in range(thread_count):
        t = Thread(target=md5_check)
        t.daemon = True  # 主线程退出时子线程自动退出
        t.start()
        threads.append(t)
    
    # 等待结果或用户终止
    try:
        while not stop_flag:
            if not result_queue.empty():
                original, md5_val = result_queue.get()
                print(f"\n找到匹配值！")
                print(f"原始字符串：{original}")
                print(f"MD5加密后：{md5_val}")
                break
        # 等待所有线程结束
        for t in threads:
            t.join()
    except KeyboardInterrupt:
        print("\n程序已手动终止")
####linux
<img width="2129" height="1109" alt="2BQ@44`K2~54T$FIKY%XGPT" src="https://github.com/user-attachments/assets/28226938-5bc4-466d-b8dc-92d0a23b07bb" />
####markdown语法
Markdown 语法速查表（可直接保存使用）
 
一、标题（1-6级）
 
语法 效果 
 # 一级标题  # 一级标题 
 ## 二级标题  ## 二级标题 
 ### 三级标题  ### 三级标题 
 #### 四级标题  #### 四级标题 
 ##### 五级标题  ##### 五级标题 
 ###### 六级标题  ###### 六级标题 
 
注：# 后必须加空格，6个#为最低级标题
 
二、文本样式
 
功能 语法 效果 
加粗  **加粗内容**  /  __加粗内容__  加粗内容 
斜体  *斜体内容*  /  _斜体内容_  斜体内容  
加粗斜体  ***加粗斜体***  加粗斜体 
删除线  ~~删除线内容~~  删除线内容 
引用  > 引用内容  > 引用内容 
嵌套引用  > 一级引用\n>> 二级引用  > 一级引用 >> 二级引用 
 
三、列表
 
1. 无序列表
 
语法 效果 
 - 列表项1  - 列表项1 
 * 列表项2  * 列表项2 
 + 列表项3  + 列表项3 
 - 父项\n  - 子项 （缩进2空格/Tab） - 父项   - 子项 
 
2. 有序列表
 
语法 效果 
 1. 步骤1  1. 步骤1 
 2. 步骤2\n  1. 子步骤2.1  2. 步骤2   1. 子步骤2.1 
 
注：数字后必须加.和空格，序号不影响渲染结果
 
3. 任务列表
 
语法 效果 
 - [x] 已完成任务  - [x] 已完成任务 
 - [ ] 未完成任务  - [ ] 未完成任务 
 
注：中括号内x为小写，空格不可省略
 
四、链接与图片
 
类型 语法 示例 
普通链接  [链接文本](地址 "可选描述")  GitHub 
锚点链接（跳转到标题）  [跳转文本](#标题名)  跳转到一级标题 
网络图片  ![描述](图片地址 "可选标题")  示例图 
本地图片  ![描述](本地路径)  本地图 
 
五、代码块
 
类型 语法 示例 
行内代码  `代码内容`   print("Hello")  
多行代码块（带语法高亮）  语言类型\n代码\n   python\ndef func():\n    print("Markdown")\n  
 
六、表格
 
语法 效果 
` 表头1 
 
注：:--- 左对齐，:---: 居中，---: 右对齐，- 数量至少1个
 
七、其他常用语法
 
功能 语法 效果 
分割线  ---  /  ***  /  ___  --- 
脚注  文本[^1]\n\n[^1]: 脚注内容  文本^1 
换行 行尾加2个空格 + 回车 换行效果 
转义字符  \特殊字符 （如#、*） # 不会被解析为标题




