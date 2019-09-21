# 题目

【2012年计算机联考真题】

某计算机存储器按字节编址，采用小端方式存放数据，假定编译器规定int和short型长度分别为32位和16位，并且数据按边界对齐存储，其C语言程序段如下：

```text
struct{
    int a;
    char b;
    short c;
}record;
record.a=273;
```

若record变量的首地址为0xC008，则地址0xC008中的内容及record.c的地址分别为（ ）

```text
A . 0x00  0xC00D
B . 0x00  0xC00E
C . 0x11  0xC00D
D . 0x11  0xC00E
【答案】 D
```

【解析】

首先要了解record的首地址存放的即是record.a的内容，a=273=0x00000111，小端存储，先存放小的那一端，所以存放的是0x11。然后要了解边界对齐，即对于存放某长度为m字节的数据，存放地址需在m字节的整数倍存放，结构体整体的大小是最大成员长度的整数倍。

| 地址 | 0xC008 | 0xC009 | 0xC00A | 0xC00B |
| :--- | :--- | :--- | :--- | :--- |
| 内容 | record.a\(0x11\) | record.a\(0x01\) | record.a\(0x00\) | record.a\(0x00\) |
| 地址 | 0xC00C | 0xC00D | 0xC00E | 0xC00F |
| 内容 | record.b | - | record.c | record.c |

0xC00D本来该存放record.c，但是0xC00D是奇数，不是2字节（short的长度）的整数倍，所以里面为空。

如果我们把题改成

```text
struct{
    char a;
    int b;
    short c;
}record;
record.a=273;
```

 record的首地址依旧是0xC008，这时候上面的表格就变成这样了

| 地址 | 0xC008 | 0xC009 | 0xC00A | 0xC00B |
| :--- | :--- | :--- | :--- | :--- |
| 内容 | record.a | - | - | - |
| 地址 | 0xC00C | 0xC00D | 0xC00E | 0xC00F |
| 内容 | record.b\(0x11\) | record.b\(0x01\) | record.b\(0x00\) | record.b\(0x00\) |
| 地址 | 0xC010 | 0xC011 | 0xC012 | 0xC013 |
| 内容 | record.c | record.c | - | - |

此时record占字节总数为12个字节，为最大字节成员（int）的整数倍。

0xC00C是int字节长度（sizeof\(int\)=4）的整数倍。

