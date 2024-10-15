---
date: 2024-06-24
---
#通信

- 波特率指每秒发送出多少个符号Symbol。
- 波特率Baud Rate和比特率 Bit Rate经常会被搞混，区分的方式为前者是传码率，后者是传信率。计算方式为：比特率 = 波特率 \* （# of bits per Symbol)。这样，如果每个Symbol只能是0或1，那么只需要1bit来表示，那么此时波特率和比特率是一样的。但如果Symbol有8个level，那就需要3bit来表示，这时比特率的数字就是波特率的3倍。

这个问题可以参考https://blog.csdn.net/xiang\_shao344/article/details/51440357

另外波特(Baud)实际本身就指频率，但一般人们还是会冗余的加上“率”字，所以大多数情况下我们还是称其为波特率或者Baud Rate。
