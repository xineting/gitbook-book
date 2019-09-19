# 4-1-2-树的存储结构

## 顺序存储结构

```c
typedef struct TNode{
    ElemType data;
    int parent;
}TNode;

typedef struct {
    TNode nodes[MaxSize]; //结点数组 
    int n;                //树的双亲表示结构
}Tree;
```

```c
typedef char ElemType; 
typedef struct CNode{
    int child;           //该孩子在表头数组的下标
    struct CNode *next;  //指向该结点的下一个孩子结点
}CNode，*Child;

typedef struct {
    Elemtype data;   //结点数据域 
    Child firstchild;//指向该结点的第一个孩子结点
}TNode;           //孩子结点数据类型
 
#define Maxsize 100 
typedef struct {
    TNode nodes[Maxsize];//结点数据域 
    int n;               //树中结点个数 
}Tree;                   
```

![](../../.gitbook/assets/image%20%28238%29.png)



