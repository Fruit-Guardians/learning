#攻防世界
  ##view_source
  <img width="1327" height="1195" alt="e5a205d2deeb654bb6d0011058fb4514" src="https://github.com/user-attachments/assets/3a1b1b7c-35d6-426a-a4f4-e67a73f73f88" />
  <img width="1612" height="382" alt="6ad14be13e7af5c61241bc17eb4baa62" src="https://github.com/user-attachments/assets/c1347d17-772f-4224-97eb-be34d3b5fef7" />
  使用f12查看源码
  ##get_post
  <img width="1327" height="1207" alt="1c22749948d44e1a993aeef1ea394a9c" src="https://github.com/user-attachments/assets/8650acdb-c602-45ac-b70b-e337ca7341c8" />
  <img width="1205" height="901" alt="bb0f4167bc2ef027366de54d4c3c2783" src="https://github.com/user-attachments/assets/72732411-8608-4bee-9733-638d31a47451" />
#python脚本
import hashlib
import random
import string

def find_md5_prefix(target_prefix, length_range=(4, 10)):
    target_len = len(target_prefix)
    char_set = string.ascii_letters + string.digits
    count = 0
    while True:
        str_length = random.randint(*length_range)
        random_str = ''.join(random.choice(char_set) for _ in range(str_length))
        md5_hash = hashlib.md5(random_str.encode('utf-8')).hexdigest()
        if md5_hash.startswith(target_prefix):
            return random_str, md5_hash
        count += 1
        if count % 1000000 == 0:
            print(f"已尝试 {count:,} 次，仍未找到匹配字符串...")

if __name__ == "__main__":
    TARGET_PREFIX = "15af95"
    print(f"开始查找 MD5 前 6 位为 {TARGET_PREFIX} 的字符串...")
    try:
        result_str, result_md5 = find_md5_prefix(TARGET_PREFIX)
        print(f"\n找到匹配结果！")
        print(f"原始字符串：{result_str}")
        print(f"MD5 哈希：{result_md5}")
        print(f"验证前缀：{result_md5[:6]}（与目标 {TARGET_PREFIX} 一致）")
    except KeyboardInterrupt:
        print("\n程序被用户中断")
#Yakit安装
  <img width="2559" height="1527" alt="image" src="https://github.com/user-attachments/assets/0892a878-0c5c-444c-84bd-339696af2ed6" />
#Linux搭建
  安装VMware虚拟器
  <img width="1935" height="1115" alt="dfa5b7731760c75af1726629fa2bc334" src="https://github.com/user-attachments/assets/31a765ed-5e2b-41bd-8d35-fd866a1b6526" />
  安装Linux系统
  <img width="2559" height="1501" alt="e9021145473cd57a1c047b7b90dbfc2a" src="https://github.com/user-attachments/assets/f21ae193-3237-4d37-8ebf-b7d9cd5bc038" />
#Linux学习笔记
  pwd ：显示当前工作目录的绝对路径（类似Windows的“查看当前位置”）。

  ls ：列出当前目录下的文件/文件夹，常用参数：

  ls -l （缩写 ll ）：详细列出，含权限、大小、修改时间等。

  ls -a ：显示隐藏文件（以 . 开头的文件）。

  ls -lh ：以人类可读格式（KB/MB）显示文件大小。

  cd [路径] ：切换目录，常用场景：

  cd .. ：返回上一级目录。

  cd ~ ：切换到当前用户的主目录（如 /home/ubuntu ）。

  cd / ：切换到根目录。

  mkdir [目录名] ：创建文件夹， mkdir -p 目录1/目录2 创建多级目录。

  touch [文件名] ：创建空文件（如 touch test.txt ）。

  rm [文件/目录] ：删除，常用参数：

  rm -f ：强制删除（忽略不存在的文件，不提示）。

  rm -r ：递归删除目录及内部所有内容（如 rm -r testdir ）。

  rm -rf ：强制递归删除（慎用！避免误删系统文件）。
 
  cp [源文件] [目标路径] ：复制文件/目录， cp -r 源目录 目标目录 复制目录。

  mv [源文件] [目标路径] ：移动文件/目录，也可用于重命名（如 mv old.txt new.txt ）。

  cat [文件名] ：查看文件全部内容（适合小文件）。

  more [文件名] ：分页查看大文件（按空格翻页， q 退出）。

  less [文件名] ：更灵活的分页查看（支持上下键滚动， /关键词 搜索）。

  head -n [数字] 文件名 ：查看文件前N行（默认前10行）。

  tail -n [数字] 文件名 ：查看文件后N行（如 tail -n 5 log.txt ）， tail -f 文件名 实时监控文件更新
