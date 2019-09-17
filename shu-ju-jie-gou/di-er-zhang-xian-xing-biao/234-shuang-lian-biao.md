# 2-3-4-双链表

## 1-1-与单链表的区别

* 单链表
*   ```c
  typedef struct LNode{ //定义单链表结点类型 
      ElemType data; //数据域
      struct LNode *next;//指针域
  }LNode, *LinkList;
  ```

* 双链表
*   ```c
  typedef struct DNode{ //定义单链表结点类型 
      ElemType data; //数据域
      struct LNode *prior,*next;//前驱和后继指针
  }DNode, *DLinkList;
  ```

* 
## 1-2-插入

1.插入:\(方法不唯一\)

* s-&gt;next=p-&gt;next;
* p-&gt;next-&gt;prior=s;
* s-&gt;prior=p
* p-&gt;next=s;

![](../../.gitbook/assets/image%20%2891%29.png)

## 1-3-删除

2.删除:

* p-&gt;next=q-&gt;next;
* q-&gt;next-&gt;prior=p;
* free\(q\);

![](../../.gitbook/assets/image%20%2812%29.png)

