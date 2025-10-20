## 工具
开发者工具
![开发者工具](https://github.com/user-attachments/assets/5d9db756-505b-4384-9f72-0f270ec6db00)

## 搭建Linux环境
![搭建Linux环境](https://github.com/user-attachments/assets/8fbdfc0b-cfaa-441f-8cde-be4284a38678)

## 用ai写一个python脚本，要求找到一个值经过md5加密后的前6位是15af95
''import hashlib

def find_md5_prefix(target_prefix):
    # 从0开始递增尝试
    num = 0
    while True:
        # 将数字转换为字符串（可根据需求修改为其他类型的输入）
        input_str = str(num)
        # 计算MD5哈希（需先编码为字节）
        md5_hash = hashlib.md5(input_str.encode('utf-8')).hexdigest()
        # 检查前6位是否匹配目标前缀
        if md5_hash.startswith(target_prefix):
            return input_str, md5_hash
        # 每100万次打印一次进度，避免程序看起来"卡住"
        if num % 1000000 == 0:
            print(f"已尝试 {num} 个值...")
        num += 1

if __name__ == "__main__":
    target = "15af95"
    print(f"正在寻找MD5前6位为 {target} 的值...")
    result_str, result_hash = find_md5_prefix(target)
    print(f"找到匹配的值：{result_str}")
    print(f"其MD5哈希为：{result_hash}")''
