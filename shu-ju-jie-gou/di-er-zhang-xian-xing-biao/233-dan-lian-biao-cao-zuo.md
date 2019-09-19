# 2-3-3-单链表操作

## 1.1. 按序号查找

* 在单链表中从第一个结点出发，顺指针next域逐个往下搜索，直到找到第i个结点为止
* 否则返回最后一个结点指针域NULL

![](../../.gitbook/assets/image%20%28293%29.png)

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
//感觉这个代码是有点问题的，因为没判断L头节点是否为空，
//while的判断有问题，如果没有到达i的时候节点p就是NULL的时候
//返回的是最后一个节点的地址，而没有返回NULL
```

## 1.2.按值查找结点

```c
LNode *LocateElem(LinkList L,ElemType e){         
    LNode *p=L->next; 
    while(p!=NULL&&p->data!=e) //从第1个结点开始查找data域为e的结点 
        p=p->next;
    return p;
}
//没有判断头节点是否为NULL
//如果p为NULL，返回的就是尾节点，并没有判断是否为我们所要查找的值e
```

![](../../.gitbook/assets/image%20%28187%29.png)

## 1.3.插入

> 插入操作是将值为x的新结点插入到单链表的第i个位置上。先检查插 入位置的合法性，然后找到待插入位置的前驱结点，即第i−1个结 点，再在其后插入新结点。

算法思路:

* 1.取指向插入位置的前驱结点的指针        1⃣️p=GetElem\(L,i-1\); 
* 2.令新结点\*s的指针域指向\*p的后继结点2⃣️s-&gt;next=p-&gt;next; 
* 3.令结点\*p的指针域指向新插入的结点\*s3⃣️p-&gt;next=s;

```cpp
//以下代码手撸的，真实情况下，需要调试
Lnode * InsertElem(LinkList L,Lnode *s,int i){
    if (i==0){
        s->next = L;
        return s;
    }
    if (p=GetElem(L,i-1)!=NULL){ 
        s->next = p->next;
        p->next = s;
        return L;
    }
    else{
        return NULL;
    }
}
```

## 1.4.删除

* 删除操作是将单链表的第i个结点删除。先检查删除位置的合法性，然后查找表中第i−1个结点，即被删结点的前驱结点，再将其删除。

算法思路:

* 1.取指向删除位置的前驱结点的指针          1⃣️ p=GetElem\(L,i-1\);
* 2.取指向删除位置的指针                               2⃣️q=p-&gt;next;
* 3.p指向结点的后继指向被删除结点的后继3⃣️p-&gt;next=q-&gt;next
* 4.释放删除结点a1                                           4⃣️free\(q\);

![](../../.gitbook/assets/image%20%28281%29.png)



```cpp
Lnode * DeleteElem(LinkList L,int i){
    if (i==0){
        L = L->next;
        return L;
    }
    if (p=GetElem(L,i-1)!=NULL){ 
        q = p->next;
        p->next=q->next;
        free(q);
    }
    else{
        return NULL;
    }
}
```

