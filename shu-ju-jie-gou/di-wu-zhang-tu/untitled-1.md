# 5-2-图的存储结构

## 1-邻接矩阵

* 结点数为n的图G = \(V, E\)的邻接矩阵A是n×n的。 
* 将G的顶点编号为 v1,v2,...,vn \(数组下标\)
* 若&lt; vi , v j &gt;∈E，则A\[i\]\[ j\]=1，否则A\[i\]\[ j\]=0。

![](../../.gitbook/assets/image%20%28142%29.png)

例子：

* 有向图

![](../../.gitbook/assets/image%20%28129%29.png)

对角线为0.

* 无向图

![](../../.gitbook/assets/image%20%28205%29.png)

关于对角对称



* A^n的含义

![](../../.gitbook/assets/image%20%28158%29.png)

![](../../.gitbook/assets/image%20%2867%29.png)

## 2-邻接表法

> 为每一个顶点建立一个单链表存放它相邻的边

顶点表  
采用顺序存储，每个数组元素存放顶点的数据和边表的头指针

边表（出边表）  
采用链式存储，单链表中存放于一个顶点相邻的所有边，一个链表结点表示一条从该结点到链表结点顶点的边。

![](../../.gitbook/assets/image%20%28148%29.png)



![](../../.gitbook/assets/image%20%28237%29.png)

## 3-基本操作

![](../../.gitbook/assets/image%20%28141%29.png)

![](../../.gitbook/assets/image%20%2865%29.png)

![](../../.gitbook/assets/image%20%28108%29.png)

![](../../.gitbook/assets/image%20%2821%29.png)

* InsertVertex\(G, x\) 在图G中插入顶点x
* DeleteVertex\(G, x\)，从图G中删除顶点x
* AddEdge\(G, x, y\)，若无向边\(x, y\)或者有向边&lt;x, y&gt;不存在，则向图G中添加该边
* RemoveEdge\(G, x, y\)，若无向边\(x, y\)或者有向边&lt;x, y&gt;存在，则在图G中删除该边
* FirstNeighbor\(G, x\)或图不存在x，则返回-1。
* NextNeighbor\(G, x\) 假设图G中顶点y是顶点x的一个邻接点，返回除y之外顶点x的下一 个邻接点的顶点号，若y是x的最后一个邻接点，则返回-1。
* 
![](../../.gitbook/assets/image%20%28199%29.png)

## 4-十字链表

> 有向图的一种链式存储结构

![](../../.gitbook/assets/image%20%28213%29.png)

![](../../.gitbook/assets/image%20%28190%29.png)

```c
#define MaxVertexNum 100
typedef struct ArcNode{
    int tailvex,headvex;
    struct ArcNode *hlink,*tlink;
    //InfoType info;
}ArcNode;
typedef struct VNode{
    VertexType data;
    ArcNode *firstin,*firstout;
}VNode;
typedef struct {
    VNode xlist[MaxVertexNum];
    int vexnum,arcnum;
}
```

## 5-邻接多重表

> 无向图的一种链式存储结构

![](../../.gitbook/assets/image%20%28236%29.png)

```c
#define MaxVertexNum 100
typedef struct ArcNode{
    int ivex,jvex;
    ArchNode *ilink,*jlink;
    //InfoType info
    //bool Mark
}
typedef struct VNode{
    VertexType data;
    ArcNode *firstedge;
}VNode;
typedef struct{
    VNode adjmulist[MaxVertexNum];
    int vexnum,arcnum;
}AMLGraph
```

