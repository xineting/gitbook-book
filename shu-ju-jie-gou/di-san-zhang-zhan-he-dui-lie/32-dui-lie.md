# 3-2-队列

![](../../.gitbook/assets/image%20%2863%29.png)

* 队头\(Front\):允许删除的一端，又称为队首。
* 队尾\(Rear\): 允许插入的一端
* 先进入队列的元素必然先离开队列， 即先进先出\(First In First Out\)简称FIFO

## 顺序队列

> 用数组来实现队列，可以将队首放在数组下标为0的位置。  
> 不要求从数组首位开始存储队列。也就是说队首不一定要在数组下标为0的位置。那如何表示队首呢?

```c
#define MaxSize 50 //定义队列中元素的最大个数
    typedef struct{
    ElemType data[MaxSize];//存放队列元素
    int front，rear;//队头指针和队尾指针 
} SqQueue; 
```

## 循环队列

> 把数组“掰弯”，形成一个环。  
> Rear指针到了下标为4的位置还能继续指回 到下标为0的地方。  
> 这样首尾相连的顺序存储的队列就叫循环队列

* 入队:rear=\(rear+1\)%MaxSize
* 出队:front=\(front+1\)%MaxSize

> 此时出现了新的问题，rear和front指针值相同，我们说过空队列时front等于rear，现在队列满了 也是front等于rear，那如何分辨队列是空还是满呢?



* 方法一:设置标志位flag，当flag=0且rear等于front时为队列空，当flag=1且rear等于front时为队列满。
* 方法二:我们把front=rear仅作为队空的判定条件。当队列满的时候，令数组中仍 然保留一个空余单元。我们认为这种情况就是队列满了。
* 我们把front=rear仅作为队空的判定条件。当队列满的时候，令数组中仍 然保留一个空余单元。我们认为这种情况就是队列满了
* \(rear+1\)%Maxsize==front

队列中元素个数:

* \(rear-front+MaxSize\)% MaxSize



* 入队

```c
bool EnQueue(SqQueue &Q,ElemType x){
    if((Q.rear+1)%MaxSize==Q.front) 
        return false; //队满 
    Q.data[Q.rear]=x;
    Q.rear=(Q.rear+1)%MaxSize;
    return true; 
}
```

* 出队

```c
bool DeQueue(SqQueue &Q,ElemType &x){ 
    if(Q.rear==Q.front) 
        return false;//队空，报错
    x = Q.data[front];
    Q.front=(Q.front+1)%MaxSize;
    return true;
}
```

## 链式存储结构

> 队列的链式存储结构，其实就是线性表的单链表，只不过需要加点限制，只能表尾插入元素，表头删除元素。为了方便操作，我们分别设置队头指针和队尾指针，队头指针指向头结点，队尾指针指向尾结点

![](../../.gitbook/assets/image%20%28172%29.png)

```c
typedef struct{ //链式队列结点 
    ElemType data;
    struct LinkNode *next; 
}LinkNode;
typedef struct{ //链式队列 
    LinkNode*front,*rear; //队头和队尾指针
}LinkQueue;
```

* 入队:我们知道队列只能从队尾插入元素，队头删除元素。于是入队就是在队尾指针进行插入结点操作。链队的插入操作和单链表的插入操作是一致的

```c
EnQueue(LinkQueue &Q，ElemType x){ 
    s=(LinkNode *)malloc(sizeof(LinkNode)); 
    s->data=x;
    s->next=NULL;
    Q.rear->next=s;
    Q.rear=s; 
}
```

![](../../.gitbook/assets/image%20%28200%29.png)

* 出队:出队就是头结点的后继结点出队，然后将头结点的后继改为它后面的结点。

```c
bool DeQueue(LinkQueue &Q,ElemType &x){ 
    if(Q.front==Q.rear) 
        return false; //空队 
    p=Q.front->next;
    x=p->data;
    Q.front->next=p->next;
    if(Q.rear==p) 
        Q.rear=Q.front;
    free(p);
    return true; 
}
```

