解题wp
题目1(test)
先启动靶机，nc +ip+端口，连接到靶机，再用ls显示其目录，在目录中直接找到“flag”,用cat flag 读取flag里的‘flag’，得到flag{5e72edcd-1e99-4a5d-816c-b88b72b0306b}，返回平台，输入flag，正确！


<img width="361" height="447" alt="image" src="https://github.com/user-attachments/assets/5805ace1-2522-4610-9495-bc8e20652d69" />


题目2(pwn's door)
1.启动靶机，下载文件，nc访问靶机，发现要一个密码打开'door',要寻找密码，输错后提示用IDA解决，
2.导入door到IDA前，先判断*86还是*64格式，重起一个指令框，checksec door,找到door的格式是amd64
3.在IDA中打开door,选main函数，TAB，打开C格式，发现if ( n7038329 == 7038329 )条件语句，密码是7038329
4.返回密码输入窗口，输入密码7038329，输入cat flag,得到flag:flag{20a95d18-50c0-4288-9637-f26117057ee1}
5.返回平台，输入flag，正确！

阻碍：关于对door的checksec door 报错：
duck@duck-VVP:~$ checksec door
usage: pwn checksec [-h] [--file [elf ...]] [elf ...]
pwn checksec: error: argument elf: can't open 'door': [Errno 2] No such file or directory: 'door'
解决：地址不精确，checksec 桌面/door正确打开【哈哈】

<img width="530" height="376" alt="image" src="https://github.com/user-attachments/assets/c1d29d2d-9c99-4046-be05-b8d4613e8a38" />
<img width="990" height="688" alt="image" src="https://github.com/user-attachments/assets/1611e12e-825c-446e-9c29-d0e133b04866" />
<img width="695" height="334" alt="image" src="https://github.com/user-attachments/assets/b2725585-be2c-4976-b9b1-8d9f5360d521" />




题目3(INTbug)
1.启动靶机，下载文件，nc访问靶机，输入返回‘You can only input positive number!’输入ls无效，准备IDA
2.判断INTbug为*86or*64格式，另起指令框，精确地址后checksec INTbug,得其为64位
3.IDA打开INTbug，选main函数，TAB，打开C格式，有fuc未知函数，打开fuc,运算逻辑：2字节v1=0与4字节v2=0，循环：输入v2，v2<=0会跳出，当v1自增<0是输出flag，2字节int最大32767，当执行32768次循环后数据溢出得到负值
4.输入32768次v2费时，执行脚本循环执行32768次，编写循环脚本，运行(python INTbug.py)
未完待续


<img width="1437" height="756" alt="image" src="https://github.com/user-attachments/assets/4bff5889-78aa-4d5b-962c-616f71fe7a30" />
<img width="1007" height="316" alt="image" src="https://github.com/user-attachments/assets/dc6eec71-a6b8-4cc2-be29-4432f8a1bd6d" />
<img width="753" height="693" alt="image" src="https://github.com/user-attachments/assets/b24d89f8-197a-4f10-8ab1-c2c1342f1cd4" />
<img width="753" height="693" alt="image" src="https://github.com/user-attachments/assets/796ccb1f-b4bb-4826-b0e7-3337140c5f16" />



学习：虚拟机脚本创建：vim (name).py
