# 链式表-算法题目

1.设计一个递归算法，删除不带头结点的单链表L中所有值为X的结点

```c
void Del_X_3(Linklist &L,ElemType x){
    //递归实现在单链表L中删除值为x的结点
    Lnode *p;
    if(L==NULL){
        return;
    }
    if(L->data==x){
        p=L;
        L=L->next;
        free(p);
        Del_X_3(L,x);
    }
    else{
        Del_X_3(L->next,x);
    }
}
```

5.试编写算法将带头节点的单链表就地逆置，所谓“就地”是指辅助空间复杂度O\(1\)

```c
LinkList Reverse_1(LinkList L){
    Lnode *p,*r;
    p=L->next;
    L->next=NULL;
    while(p!=NULL){
        r=p->next;
        p->next=L->next;
        L->next=p;
        p=r;
    }
    return L;
}
```

* 
8. 给定两个单链表，编写算法找出两个链表的公共结点!

```c
LinkList Search_1st_Common(LinkList L1,LinkList L2){
    int len1=length(L1);
    int len2=length(L2);
    LinkList longList,shortList;
    if(len1>len2){
        longList=L1->next;
        shortList=L2->next;
        dist=len1-len2;
    }
    else{
        longList=L2->next;
        shortList=L1->next;
        dist=len2-len1;
    }
    while(dist--){
        longList=longList->next;
    }
    while(longList!=NULL){
        if(longLost==shortList){
            return longList;
        }
        else{
            longList=longList->next;
            shortList=shortList->next;
        }
    }
    return NULL;
}
```

11.设C={a1,b1,a2,b2.......an,bn}为线性表，采用带头结点的hc单链表存放，设计一个就地算法，将其拆分为两个线性表使A={a1,a2,...an},B={bn,bn-1,...,b1}。

```c
LinkList DisCreat_2(LinkList &A){
    LinkList B=(LinkList)malloc(sizeof(LNode));
    B->next=NULL;
    Lnode *p=A->next,*q;
    Lnode *ra=A;
    while(p!=NULL){
        ra->next=p;
        ra=p;
        p=p->next;
        q=p->next;
        p->next=B->next;
        B->next=p;
        p=q
    }
    ra->next=NULL;
    return B;
}
```



13. 假设有两个按元素值递增次序排序的线性表，均以单链表形式存储。请编写算法将这两个单链表归并为一个按元素值递减排序的单链表，**并要求利用原来两个单链表的结点存放归并后的单链表。带头结点。**

```c
void MergeList(LinkList &La,LinkList &Lb){
    LNode *r,*pa=La->next,*pb=Lb->next;
    La->next=NULL;
    while(pa&&pb){
        if(pa->data<=pb->data){
            r=pa->next;
            pa->next=La->next;
            La->next=pa;
            pa=r;
        }
        else{
            r=pb->next;
            pb->next=La->next;
            L->next=pb;
            pb=r;
        }
    }
    if(pa){
        pb=pa;
    }
    while(pb){
        r=pb->next;
        pb->next=La->next;
        L->next=pb;
        pb=r;
    }
    free(Lb);//这个头结点可以一开始就free掉
}
```

14-设A和B是两个单链表，（带头结点），其中元素递增有序，设计一个算从A和B中公共元素产生单链表C，要求不破坏A和B的结点。

```c
void Get_Common(LinkList A,LinkList B){
    Lnode *p=A->next;
    Lnode *q=B->next;
    Lnode *r,*s;
    LinkList C=(LinkList)malloc(sizeof(Lnode));
    r=C;
    while(p&&q){
        if(p->data==q->data){
            s=(Lnode*)malloc(sizeof(Lnode));
            s->data=p->data;
            r->next=s;
            r=s;
            p=p->next;
            q=q->nexr;
        }
        else if(p->data>q->data){
            q=q->next;
        }
        else{
            p=p->next;
        }            
    }
    r->next=NULL;
    return C;
}
```

17-设计一个算法判断带头结点的循环双链表是否对称

```c
bool Symetry(DlinkList L){
    Dnode *p=L->next,*q=L->prior;
    while(p->data==q->data)
        if(p==q||p->next==q) 
            return true;
        else{
            p=p->next;
            q=q->prior;
        }
    return false;
}
```

19-设带有头结点的循环单链表，其结点值为正整数，设计一个算法，反复找出单链表中结点值最小的结点并输出，然后删除该结点，直到链表为空，再删除头结点

```c
void Del_All(LinkList &L){
    Lnode *p,*pre,*minp,*minpre;
    while(L->next!=L){
        pre=L;
        minpre=L;
        p=L->next;
        minp=L->next;
        while(p!=L){
            if(p->data<minp->data){
                minp=p
                minpre=pre;
            }
            pre=p;
            p=p->next;
        }
        printf("%d\n",minp->data);
        minpre->next=minp->next;
        free(minp);
    }
}
```

