# 1-4-操作系统的运行机制



![](../../.gitbook/assets/image%20%28211%29.png)

## 1-内核态 v.s. 用户态

CPU 有两种状态，

“内核态”和“用户态” 

* 处于内核态时，说明此时正在运行的是内核程序，此时可以执行特权指令 
* 处于用户态时，说明此时正在运行的是应用程序，此时只能执行非特权指令

拓展:CPU 中有一个寄存器叫 程序状态字寄存器\(PSW\)，其中有个二进制位，1表示 “内核态”，0表示“用户态” 

别名:内核态=核心态=管态;用户态=目态

内核态-&gt;用户态:执行一条特权指令——修改PSW的标志位为“用户态”，这个动作意味着操作系统 将主动让出CPU使用权。

用户态-&gt;内核态:由“中断”引发，硬件自动完成变态过程，触发中断信号意味着操作系统将强行夺 回CPU的使用权。

除了非法使用特权指令之外，还有很多事件会触发中断信号。一个共性是，但凡需要操作系统介入的地方，都会触发中断信号。

## 2-中断和异常

![](../../.gitbook/assets/image%20%2827%29.png)

“中断”是让操作系统内核夺回CPU使用权的唯一途径，如果没有“中断”机制，那么一旦应用程序上CPU运行，CPU就会一直运行这个应用程序

![](../../.gitbook/assets/image%20%2840%29.png)

### 2-1-内中断

例如特权指令

有时候应用程序想请求操作系统内核的服务，此时会执行一条特殊的指令——陷入指令，该指 令会引发一个内部中断信号

### 2-2-外中断

时钟中断——由时钟部件发来的中断信号

![](../../.gitbook/assets/image%20%28286%29.png)

![](../../.gitbook/assets/image%20%28368%29.png)

![](../../.gitbook/assets/image%20%28189%29.png)
