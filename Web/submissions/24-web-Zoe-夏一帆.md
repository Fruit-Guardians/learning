第一题：
import hashlib

def verify_md5_prefix(input_string, target_prefix="15af95"):
    md5_hash = hashlib.md5(input_string.encode()).hexdigest()
    matches = md5_hash.startswith(target_prefix)
    print(f"字符串：{input_string}")
    print(f"MD5哈希：{md5_hash}")
    print(f"前6位：{md5_hash[:6]}")
    print(f"匹配目标 '{target_prefix}'：{matches}")
    return matches

if __name__ == "__main__":
    test_str = "Hello AI Python"
    verify_md5_prefix(test_str)

图片：  ![7adf3a78fc7fa0a3597d10a471a2db69](https://github.com/user-attachments/assets/084f0d81-16b7-4fa5-b477-c92380f7718f)
