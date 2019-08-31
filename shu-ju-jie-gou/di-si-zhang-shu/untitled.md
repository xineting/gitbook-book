# 4-2-2-二叉树的存储结构

## 顺序存储

> 二叉树的顺序存储结构就是用一组地址连续的存储单元依次自上而下、自左至右存储完全 二叉树上的结点元素。

![](../../.gitbook/assets/image%20%2823%29.png)

## 链式存储

```c
typedef struct BiTNode{
    ElemType data; //数据域
    struct BiTNode *lchild,*rchild; //指向该结点的左、右孩子指针 
}BiTNode,*BiTree; 
//二叉树结点结构
```

![](../../.gitbook/assets/image%20%28107%29.png)

含有n个结点的二叉链表中，有n+1个空链域。即2n-（n-1）。



* 这种结构的链表由于有两个指针，所以叫二叉链表。
* 另外还可以增加指针指向该结点的双亲结点，那这时三个指针的链表就叫三叉链表。

