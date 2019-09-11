# 2-3-2-链式存储的操作

## 1. 单链表的操作

### 1.1.头插法建立单链表: 

* 建立新的结点分配内存空间，将新结点插入到当前链表的表头

![](../../.gitbook/assets/image%20%28101%29.png)

```c
LinkList CreatList1(LinkList &L){ 
   LNode *s;                             //辅助指针
   int x; 
   L=(LinkList)malloc(sizeof(LNode));    //创建头结点
   L->next=NULL;                         //初始为空链表
   scanf(”%d”,&x);                       //输入结点的值 
   while(x!=9999){                       //输入9999表示结束
      s=(LNode*)malloc(sizeof(LNode));   //创建新结点
      s->data=x;                        
      s->next=L->next;
      L->next=s;                         //将新结点插入表中，L为头指针
      scanf(”%d”,&x);                    //读入下一个结点值
      }
      return L;
  }
```

头插法建立单链表，读入数据的顺序与生成的链表中元素的顺序是相反的



### 1.2.尾插法建立单链表:

* 建立新的结点分配内存空间，将新结点插入到当前链表的表尾,需要增加一个指向表尾元素的尾指针

![](../../.gitbook/assets/image%20%28220%29.png)

```cpp
LinkList CreatList2(LinkList &L){ 
    int x;
    L=(LinkList)malloc(sizeof(LNode)); 
    LNode *s, *r=L;
    scanf(”%d”,&x);                        //输入结点的值
    while(x!=9999){                        //输入9999表示结束
        s=(LNode *)malloc(sizeof(LNode));  //r为表尾指针 指向表尾
        s->data=x;
        r->next=s;
        r=s;                               //r指向新的表尾结点
        scanf(”%d”,&x);
    } 
    r->next=NULL;                         //尾结点指针置空
    return L;
}
```

![](../../.gitbook/assets/image%20%2841%29.png)





尾插法建立单链表，读入数据的顺序与 生成的链表中元素 的顺序是相同的

