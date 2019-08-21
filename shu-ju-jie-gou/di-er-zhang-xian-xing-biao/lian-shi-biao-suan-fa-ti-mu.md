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
8. 给定两个单链表，编写算法找出两个链表的公共结点

```text
LinkList Search_1st_Common(LinkList L1,LinkList L2){
    int len1=length(L1);
    int len2=length(L2);
    LinkList longList,shortList;
    if(len1>len2){
        longList=L1->next;
        
    }
}
```





