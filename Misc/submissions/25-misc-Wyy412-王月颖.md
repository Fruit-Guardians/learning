[Week1]好玩的维吉尼亚解题思路：
将附件里的内容粘贴到https://www.guballa.de/vigenere-solver的Input里，在Result的末尾有flag。 

[Week1]ez_docx解题思路：
打开附件，按ctrl+F搜索flag,可得部分flag{I_be1ieve_y0u_Can_
再利用工具bandzip解压，找到文件我也是一段flag哦，得到另一部分flag    flnd_+h3m}
经过推断得flag。

[Week1]ez_LSB解题思路：
下载附件，用https://www.aperisolve.com/打开，搜索flag即可得到。

[Week1]ez_dase解题思路:
判断编码类型为base91，利用base91在线解码工具可解出flag.
[Week1]编码的答案解题思路：
1  <img width="1944" height="1271" alt="屏幕截图 2025-10-19 144755" src="https://github.com/user-attachments/assets/b82e14ef-0b77-4c10-b14b-24d7a59e0035" />
根据Ascll码可以推断出flag。
2<img width="1758" height="1465" alt="屏幕截图 2025-10-19 145914" src="https://github.com/user-attachments/assets/442f8dc0-a3cb-4eaa-90f6-123517e0078d" />
每8个转为一个ASCLL字符，可得flag。
3<img width="1680" height="1358" alt="屏幕截图 2025-10-19 150301" src="https://github.com/user-attachments/assets/01a8a653-170b-4aa2-8836-58109e4a8c3f" />
这个是典型的Base64编码，直接用在线工具解码得flag。
4.<img width="1711" height="1398" alt="屏幕截图 2025-10-19 150558" src="https://github.com/user-attachments/assets/1b0399f6-fada-4e04-a03a-3afa28d2c727" />
这个是ROT13加密，对每个字母进行ROT13转换，非字母不变，可得到flag。
5.<img width="1798" height="1484" alt="屏幕截图 2025-10-19 151012" src="https://github.com/user-attachments/assets/1449324f-7f8e-4557-8fde-69394a02308b" />
这是摩尔斯电码，对照标准摩尔斯电码表可推算出flag。
6.<img width="1878" height="1473" alt="屏幕截图 2025-10-19 151350" src="https://github.com/user-attachments/assets/23b81743-9b89-4716-beab-513d23e42094" />
这是栅栏密码，根据在线工具解码得到flag。

最终你会得到flag<img width="1652" height="1351" alt="屏幕截图 2025-10-19 151806" src="https://github.com/user-attachments/assets/763236ae-ccf4-448f-8571-c05b434b560f" />





