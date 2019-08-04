# 2-3-3-单链表操作

## 1.1. 按序号查找

* 在单链表中从第一个结点出发，顺指针next域逐个往下搜索，直到找到第i个结点为止
* 否则返回最后一个结点指针域NULL

![](../../.gitbook/assets/image%20%2860%29.png)

```cpp
LNode * GetElem(LinkList L,int i){ 
    int j=1;                        //计数，初始为1
    LNode *p=L->next;               //第一个节点的值赋给p
    if(i==0) return L; 
    if(i<1) return NULL; 
    while(p&&j<i){                  //从第1个节点开始查找，查找到第i个节点
        p=p->next;
        j++;
    }
    return p;
}
```

## 1.2.按值查找结点

```c
LNode *LocateElem(LinkList L,ElemType e){         
    LNode *p=L->next; 
    while(p!=NULL&&p->data!=e) //从第1个结点开始查找data域为e的结点 
        p=p->next;
    return p;
}
```

![](../../.gitbook/assets/image%20%2834%29.png)



