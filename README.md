# IOST_TPS
---
## 背景
IOST采用POB共识机制，17个超级节点，0.5秒出一个块(2 BPS）,现对其进行TPS性能测试
---
## 官方资料
[私链搭建方法教程](https://developers.iost.io/docs/en/1-getting-started/Overview.html)

---
## 测试环境
```
节点程序运行在扫链服务器ubuntu容器内，配置如下：
Docker version 18.06.1-ce, build e68fc7a
root@298e90390d9a:/# cat /proc/version
Linux version 4.4.0-93-generic (buildd@lcy01-28) (gcc version 4.8.4 (Ubuntu 4.8.4-		2ubuntu1~14.04.3) ) #116~14.04.1-Ubuntu SMP Mon Aug 14 16:07:05 UTC 2017
```

---
## 测试步骤
### 1.通过官方SDK对交易进行离线签名
### 2.通过RPC接口sendTx 广播交易进行转账
### 3.多线程脚本模拟多用户广播交易
### 4.通过接口getBlockByNumber扫描每个测试区块中包含的交易笔数除以出块间隔时间得到TPS

---
## 测试结果
### 1.测试结果数据
#### 测试程序运行5 mins后取其中100s 稳定输出的log记录如下，计算出平均值为854
```
 GetBlockByNumber ,height=219074, contain transaction num= 716 ,TPS=1432 
 GetBlockByNumber ,height=219075, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219076, contain transaction num= 422 ,TPS=844 
 GetBlockByNumber ,height=219077, contain transaction num= 844 ,TPS=1688 
 GetBlockByNumber ,height=219078, contain transaction num= 45 ,TPS=90 
 GetBlockByNumber ,height=219079, contain transaction num= 82 ,TPS=164 
 GetBlockByNumber ,height=219080, contain transaction num= 610 ,TPS=1220 
 GetBlockByNumber ,height=219081, contain transaction num= 514 ,TPS=1028 
 GetBlockByNumber ,height=219082, contain transaction num= 622 ,TPS=1244 
 GetBlockByNumber ,height=219083, contain transaction num= 758 ,TPS=1516 
 GetBlockByNumber ,height=219084, contain transaction num= 91 ,TPS=182 
 GetBlockByNumber ,height=219085, contain transaction num= 59 ,TPS=118 
 GetBlockByNumber ,height=219086, contain transaction num= 793 ,TPS=1586 
 GetBlockByNumber ,height=219087, contain transaction num= 658 ,TPS=1316 
 GetBlockByNumber ,height=219088, contain transaction num= 776 ,TPS=1552 
 GetBlockByNumber ,height=219089, contain transaction num= 584 ,TPS=1168 
 GetBlockByNumber ,height=219090, contain transaction num= 70 ,TPS=140 
 GetBlockByNumber ,height=219091, contain transaction num= 100 ,TPS=200 
 GetBlockByNumber ,height=219092, contain transaction num= 688 ,TPS=1376 
 GetBlockByNumber ,height=219093, contain transaction num= 546 ,TPS=1092 
 GetBlockByNumber ,height=219094, contain transaction num= 460 ,TPS=920 
 GetBlockByNumber ,height=219095, contain transaction num= 325 ,TPS=650 
 GetBlockByNumber ,height=219096, contain transaction num= 80 ,TPS=160 
 GetBlockByNumber ,height=219097, contain transaction num= 70 ,TPS=140 
 GetBlockByNumber ,height=219098, contain transaction num= 134 ,TPS=268 
 GetBlockByNumber ,height=219099, contain transaction num= 387 ,TPS=774 
 GetBlockByNumber ,height=219100, contain transaction num= 268 ,TPS=536 
 GetBlockByNumber ,height=219101, contain transaction num= 315 ,TPS=630 
 GetBlockByNumber ,height=219102, contain transaction num= 20 ,TPS=40 
 GetBlockByNumber ,height=219103, contain transaction num= 46 ,TPS=92 
 GetBlockByNumber ,height=219104, contain transaction num= 249 ,TPS=498 
 GetBlockByNumber ,height=219105, contain transaction num= 254 ,TPS=508 
 GetBlockByNumber ,height=219106, contain transaction num= 660 ,TPS=1320 
 GetBlockByNumber ,height=219107, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219108, contain transaction num= 145 ,TPS=290 
 GetBlockByNumber ,height=219109, contain transaction num= 135 ,TPS=270 
 GetBlockByNumber ,height=219110, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219111, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219112, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219113, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219114, contain transaction num= 93 ,TPS=186 
 GetBlockByNumber ,height=219115, contain transaction num= 113 ,TPS=226 
 GetBlockByNumber ,height=219116, contain transaction num= 643 ,TPS=1286 
 GetBlockByNumber ,height=219117, contain transaction num= 745 ,TPS=1490 
 GetBlockByNumber ,height=219118, contain transaction num= 570 ,TPS=1140 
 GetBlockByNumber ,height=219119, contain transaction num= 771 ,TPS=1542 
 GetBlockByNumber ,height=219120, contain transaction num= 139 ,TPS=278 
 GetBlockByNumber ,height=219121, contain transaction num= 72 ,TPS=144 
 GetBlockByNumber ,height=219122, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219123, contain transaction num= 340 ,TPS=680 
 GetBlockByNumber ,height=219124, contain transaction num= 235 ,TPS=470 
 GetBlockByNumber ,height=219125, contain transaction num= 625 ,TPS=1250 
 GetBlockByNumber ,height=219126, contain transaction num= 77 ,TPS=154 
 GetBlockByNumber ,height=219127, contain transaction num= 74 ,TPS=148 
 GetBlockByNumber ,height=219128, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219129, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219130, contain transaction num= 847 ,TPS=1694 
 GetBlockByNumber ,height=219131, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219132, contain transaction num= 68 ,TPS=136 
 GetBlockByNumber ,height=219133, contain transaction num= 153 ,TPS=306 
 GetBlockByNumber ,height=219134, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219135, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219136, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219137, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219138, contain transaction num= 137 ,TPS=274 
 GetBlockByNumber ,height=219139, contain transaction num= 123 ,TPS=246 
 GetBlockByNumber ,height=219140, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219141, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219142, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219143, contain transaction num= 689 ,TPS=1378 
 GetBlockByNumber ,height=219144, contain transaction num= 1 ,TPS=2 
 GetBlockByNumber ,height=219145, contain transaction num= 2 ,TPS=4 
 GetBlockByNumber ,height=219146, contain transaction num= 57 ,TPS=114 
 GetBlockByNumber ,height=219147, contain transaction num= 22 ,TPS=44 
 GetBlockByNumber ,height=219148, contain transaction num= 35 ,TPS=70 
 GetBlockByNumber ,height=219149, contain transaction num= 10 ,TPS=20 
 GetBlockByNumber ,height=219150, contain transaction num= 1 ,TPS=2 
 GetBlockByNumber ,height=219151, contain transaction num= 1 ,TPS=2 
 GetBlockByNumber ,height=219152, contain transaction num= 1 ,TPS=2 
 GetBlockByNumber ,height=219153, contain transaction num= 1 ,TPS=2 
 GetBlockByNumber ,height=219154, contain transaction num= 307 ,TPS=614 
 GetBlockByNumber ,height=219155, contain transaction num= 536 ,TPS=1072 
 GetBlockByNumber ,height=219156, contain transaction num= 28 ,TPS=56 
 GetBlockByNumber ,height=219157, contain transaction num= 73 ,TPS=146 
 GetBlockByNumber ,height=219158, contain transaction num= 651 ,TPS=1302 
 GetBlockByNumber ,height=219159, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219160, contain transaction num= 583 ,TPS=1166 
 GetBlockByNumber ,height=219161, contain transaction num= 441 ,TPS=882 
 GetBlockByNumber ,height=219162, contain transaction num= 11 ,TPS=22 
 GetBlockByNumber ,height=219163, contain transaction num= 75 ,TPS=150 
 GetBlockByNumber ,height=219164, contain transaction num= 308 ,TPS=616 
 GetBlockByNumber ,height=219165, contain transaction num= 253 ,TPS=506 
 GetBlockByNumber ,height=219166, contain transaction num= 182 ,TPS=364 
 GetBlockByNumber ,height=219167, contain transaction num= 201 ,TPS=402 
 GetBlockByNumber ,height=219168, contain transaction num= 60 ,TPS=120 
 GetBlockByNumber ,height=219169, contain transaction num= 49 ,TPS=98 
 GetBlockByNumber ,height=219170, contain transaction num= 285 ,TPS=570 
 GetBlockByNumber ,height=219171, contain transaction num= 174 ,TPS=348 
 GetBlockByNumber ,height=219172, contain transaction num= 148 ,TPS=296 
 GetBlockByNumber ,height=219173, contain transaction num= 162 ,TPS=324 
 GetBlockByNumber ,height=219174, contain transaction num= 16 ,TPS=32 
 GetBlockByNumber ,height=219175, contain transaction num= 57 ,TPS=114 
 GetBlockByNumber ,height=219176, contain transaction num= 282 ,TPS=564 
 GetBlockByNumber ,height=219177, contain transaction num= 331 ,TPS=662 
 GetBlockByNumber ,height=219178, contain transaction num= 271 ,TPS=542 
 GetBlockByNumber ,height=219179, contain transaction num= 160 ,TPS=320 
 GetBlockByNumber ,height=219180, contain transaction num= 17 ,TPS=34 
 GetBlockByNumber ,height=219181, contain transaction num= 46 ,TPS=92 
 GetBlockByNumber ,height=219182, contain transaction num= 432 ,TPS=864 
 GetBlockByNumber ,height=219183, contain transaction num= 732 ,TPS=1464 
 GetBlockByNumber ,height=219184, contain transaction num= 854 ,TPS=1708 
 GetBlockByNumber ,height=219185, contain transaction num= 412 ,TPS=824 
 GetBlockByNumber ,height=219186, contain transaction num= 122 ,TPS=244 
 GetBlockByNumber ,height=219187, contain transaction num= 91 ,TPS=182 
 GetBlockByNumber ,height=219188, contain transaction num= 772 ,TPS=1544 
 GetBlockByNumber ,height=219189, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219190, contain transaction num= 531 ,TPS=1062 
 GetBlockByNumber ,height=219191, contain transaction num= 850 ,TPS=1700 
 GetBlockByNumber ,height=219192, contain transaction num= 140 ,TPS=280 
 GetBlockByNumber ,height=219193, contain transaction num= 124 ,TPS=248 
 GetBlockByNumber ,height=219194, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219195, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219196, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219197, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219198, contain transaction num= 139 ,TPS=278 
 GetBlockByNumber ,height=219199, contain transaction num= 112 ,TPS=224 
 GetBlockByNumber ,height=219200, contain transaction num= 764 ,TPS=1528 
 GetBlockByNumber ,height=219201, contain transaction num= 1 ,TPS=2 
 GetBlockByNumber ,height=219202, contain transaction num= 1 ,TPS=2 
 GetBlockByNumber ,height=219203, contain transaction num= 11 ,TPS=22 
 GetBlockByNumber ,height=219204, contain transaction num= 83 ,TPS=166 
 GetBlockByNumber ,height=219205, contain transaction num= 104 ,TPS=208 
 GetBlockByNumber ,height=219206, contain transaction num= 761 ,TPS=1522 
 GetBlockByNumber ,height=219207, contain transaction num= 674 ,TPS=1348 
 GetBlockByNumber ,height=219208, contain transaction num= 668 ,TPS=1336 
 GetBlockByNumber ,height=219209, contain transaction num= 618 ,TPS=1236 
 GetBlockByNumber ,height=219210, contain transaction num= 84 ,TPS=168 
 GetBlockByNumber ,height=219211, contain transaction num= 26 ,TPS=52 
 GetBlockByNumber ,height=219212, contain transaction num= 526 ,TPS=1052 
 GetBlockByNumber ,height=219213, contain transaction num= 636 ,TPS=1272 
 GetBlockByNumber ,height=219214, contain transaction num= 570 ,TPS=1140 
 GetBlockByNumber ,height=219215, contain transaction num= 609 ,TPS=1218 
 GetBlockByNumber ,height=219216, contain transaction num= 142 ,TPS=284 
 GetBlockByNumber ,height=219217, contain transaction num= 44 ,TPS=88 
 GetBlockByNumber ,height=219218, contain transaction num= 248 ,TPS=496 
 GetBlockByNumber ,height=219219, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219220, contain transaction num= 571 ,TPS=1142 
 GetBlockByNumber ,height=219221, contain transaction num= 704 ,TPS=1408 
 GetBlockByNumber ,height=219222, contain transaction num= 51 ,TPS=102 
 GetBlockByNumber ,height=219223, contain transaction num= 111 ,TPS=222 
 GetBlockByNumber ,height=219224, contain transaction num= 247 ,TPS=494 
 GetBlockByNumber ,height=219225, contain transaction num= 400 ,TPS=800 
 GetBlockByNumber ,height=219226, contain transaction num= 775 ,TPS=1550 
 GetBlockByNumber ,height=219227, contain transaction num= 392 ,TPS=784 
 GetBlockByNumber ,height=219228, contain transaction num= 129 ,TPS=258 
 GetBlockByNumber ,height=219229, contain transaction num= 89 ,TPS=178 
 GetBlockByNumber ,height=219230, contain transaction num= 238 ,TPS=476 
 GetBlockByNumber ,height=219231, contain transaction num= 228 ,TPS=456 
 GetBlockByNumber ,height=219232, contain transaction num= 340 ,TPS=680 
 GetBlockByNumber ,height=219233, contain transaction num= 209 ,TPS=418 
 GetBlockByNumber ,height=219234, contain transaction num= 11 ,TPS=22 
 GetBlockByNumber ,height=219235, contain transaction num= 70 ,TPS=140 
 GetBlockByNumber ,height=219236, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219237, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219238, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219239, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219240, contain transaction num= 137 ,TPS=274 
 GetBlockByNumber ,height=219241, contain transaction num= 76 ,TPS=152 
 GetBlockByNumber ,height=219242, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219243, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219244, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219245, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219246, contain transaction num= 120 ,TPS=240 
 GetBlockByNumber ,height=219247, contain transaction num= 131 ,TPS=262 
 GetBlockByNumber ,height=219248, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219249, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219250, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219251, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219252, contain transaction num= 51 ,TPS=102 
 GetBlockByNumber ,height=219253, contain transaction num= 1 ,TPS=2 
 GetBlockByNumber ,height=219254, contain transaction num= 641 ,TPS=1282 
 GetBlockByNumber ,height=219255, contain transaction num= 567 ,TPS=1134 
 GetBlockByNumber ,height=219256, contain transaction num= 728 ,TPS=1456 
 GetBlockByNumber ,height=219257, contain transaction num= 516 ,TPS=1032 
 GetBlockByNumber ,height=219258, contain transaction num= 94 ,TPS=188 
 GetBlockByNumber ,height=219259, contain transaction num= 65 ,TPS=130 
 GetBlockByNumber ,height=219260, contain transaction num= 432 ,TPS=864 
 GetBlockByNumber ,height=219261, contain transaction num= 810 ,TPS=1620 
 GetBlockByNumber ,height=219262, contain transaction num= 663 ,TPS=1326 
 GetBlockByNumber ,height=219263, contain transaction num= 636 ,TPS=1272 
 GetBlockByNumber ,height=219264, contain transaction num= 105 ,TPS=210 
 GetBlockByNumber ,height=219265, contain transaction num= 109 ,TPS=218 
 GetBlockByNumber ,height=219266, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219267, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219268, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219269, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219270, contain transaction num= 187 ,TPS=374 
 GetBlockByNumber ,height=219271, contain transaction num= 213 ,TPS=426 
 GetBlockByNumber ,height=219272, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219273, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219274, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219275, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219276, contain transaction num= 184 ,TPS=368 
 GetBlockByNumber ,height=219277, contain transaction num= 181 ,TPS=362 
 GetBlockByNumber ,height=219278, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219279, contain transaction num= 857 ,TPS=1714 
 GetBlockByNumber ,height=219280, contain transaction num= 681 ,TPS=1362 
 GetBlockByNumber over,sum_time=103 s ,average_txs=427, average_TPS=854 
```
#### 峰值= 1714





