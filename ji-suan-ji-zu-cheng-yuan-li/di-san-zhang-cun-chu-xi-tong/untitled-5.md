# 3-4-主存储器和CPU

## 1-简单模型



![](blob:https://app.gitbook.com/1835facb-d776-4d60-b76f-b5e96b2ee6cd)

连接原理

![](blob:https://app.gitbook.com/f6a8001d-c43e-47f9-a6a2-c2b19e62bc24)

## 2-主存地址分配

![](../../.gitbook/assets/image%20%28104%29.png)

![](../../.gitbook/assets/image%20%28305%29.png)

## 3-主存与cpu的连接例题

```text
设CPU有16根地址线，8根数据线，并用MREQ作为访存控制信号(低电平有效)，用WR作为读/写控制
信号(高电平为读，低电平为写)。现有下列存储芯片:1K×4位RAM，4K×8位 RAM，8K×8位RAM，
2K×8位ROM，4K×8位ROM，8K×8位ROM及74LS138译码器和各种门电路。画 出CPU与存储器的连
接图，要求: 

1- 主存地址空间分配:6000H~67FFH为系统程序区;6800H~6BFFH为用户程序区。
2- 合理选用上述存储芯片，说明各选几片? 
3- 详细画出存储芯片的片选逻辑图。
```

```text
系统程序区用ROM，用户程序区用RAM
1. 确认地址线、数据线，选择存储芯片 
数据线:CPU数据线8根,存储器位数应扩展为8位
地址分配:6000H~67FFH  67FFH – 6000H + 1 = 800H，
2K   ROM地址线11根    ->用1片2K×8位ROM 
6800H~6BFFH=6BFFH–6800H+1=400H，1K 
用2片1K×4位RAM，位扩展 ->RAM地址线10根
```

![](../../.gitbook/assets/image%20%28350%29.png)

## 4-主存容量的扩展

### 4-1-位扩展

![](../../.gitbook/assets/image%20%28250%29.png)

### 4-2-字拓展

![](../../.gitbook/assets/image%20%28224%29.png)

![](../../.gitbook/assets/image%20%28319%29.png)

![](../../.gitbook/assets/image%20%28132%29.png)

#### 4-3-字位同时扩展

![](../../.gitbook/assets/image%20%28239%29.png)

