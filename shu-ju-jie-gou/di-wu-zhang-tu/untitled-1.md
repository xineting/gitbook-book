# 5-2-图的存储结构

## 1-邻接矩阵

* 结点数为n的图G = \(V, E\)的邻接矩阵A是n×n的。 
* 将G的顶点编号为 v1,v2,...,vn \(数组下标\)
* 若&lt; vi , v j &gt;∈E，则A\[i\]\[ j\]=1，否则A\[i\]\[ j\]=0。

![](../../.gitbook/assets/image%20%28105%29.png)

例子：

* 有向图

![](../../.gitbook/assets/image%20%2894%29.png)

对角线为0.

* 无向图

![](../../.gitbook/assets/image%20%28151%29.png)

关于对角对称



* A^n的含义

![](../../.gitbook/assets/image%20%28117%29.png)



