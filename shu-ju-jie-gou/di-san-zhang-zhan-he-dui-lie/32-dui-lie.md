# 3-2-队列

![](../../.gitbook/assets/image%20%2817%29.png)

队头\(Front\):允许删除的一端，又称为队首。 队尾\(Rear\): 允许插入的一端先进入队列的元素必然先离开队列， 即先进先出\(First In First Out\)简称FIFO

用数组来实现队列，可以将队首放在数组下标为0的位置。不要求从数组首位开始存储队列。也就是说队首不一定要在数组下标为0的位置。那如何表示队首呢?

```text
#define MaxSize 50 typedef struct{
ElemType data[MaxSize];
int front，rear; } SqQueue;
//定义队列中元素的最大个数
//存放队列元素//队头指针和
```

把数组“掰弯”，形成一个环。Rear指针到了下标为4的位置还能继续指回 到下标为0的地方。这样首尾相连的顺序存储的队列就叫循环队列

入队:rear=\(rear+1\)%MaxSize出队:front=\(front+1\)%MaxSize此时出现了新的问题，rear和front指针值相同，我们说过空队列时front等于rear，现在队列满了 也是front等于rear，那如何分辨队列是空还是满呢?方法一:设置标志位flag，当flag=0且rear等于front时为队列空，当flag=1且rear等于front时为队列满。方法二:我们把front=rear仅作为队空的判定条件。当队列满的时候，令数组中仍 然保留一个空余单元。我们认为这种情况就是队列满了。

我们把front=rear仅作为队空的判定条件。当队列满的时候，令数组中仍 然保留一个空余单元。我们认为这种情况就是队列满了





```text
那么栈满时，有什么等量关系?
```

\(rear+1\)%Maxsize==front

队列中元素个数:

\(rear-front+MaxSize\)% MaxSize

```text
 bool EnQueue(SqQueue &Q,ElemType x){ if((Q.rear+1)%MaxSize==Q.front) return false; //队满 Q.data[Q.rear]=x;
Q.rear=(Q.rear+1)%MaxSize;
true; }
```

```text
 bool DeQueue(SqQueue &Q,ElemType &x){ if(Q.rear==Q.front) return false;
//队空，报错
}


```



链式队列![page5image55472320](blob:https://app.gitbook.com/5b8226ea-8afc-4f6f-aba9-c00540ef1395)![page5image55475440](blob:https://app.gitbook.com/b4595737-fb7e-4a3e-a6c1-fd94d844d7ab)![page5image55472944](blob:https://app.gitbook.com/32788b34-5b71-48e9-8620-74ad79b52e25)![page5image55468576](blob:https://app.gitbook.com/b0f524b0-2721-4d86-b5ed-78d2b8e3fa63)![page5image55473776](blob:https://app.gitbook.com/3ab39b26-941f-4d20-b4b5-225c6ecaf5d4)![page5image55459840](blob:https://app.gitbook.com/61e458f8-a3b2-40d7-9371-50511fe12389)![page5image55469200](blob:https://app.gitbook.com/6755f749-1163-457b-a1e7-0d50b202372a)![page5image55469824](blob:https://app.gitbook.com/a66ec363-098e-482c-8371-632f5ef0cd75)![page5image55474192](blob:https://app.gitbook.com/3295bf00-98fb-401c-a848-7e6e2e665576)![page5image55462544](blob:https://app.gitbook.com/73f5d8be-d53e-4785-8982-ba79f8e80f9b)![page5image55472736](blob:https://app.gitbook.com/2743b888-587a-484d-b9fd-c3ef5f52a76e)![page5image55474816](blob:https://app.gitbook.com/fe54bab3-1611-42e3-85a6-c398dda5aa20)![page5image61639680](blob:https://app.gitbook.com/061c19ca-4146-45d5-9e5a-1008c5f5d30e)![page5image61639872](blob:https://app.gitbook.com/8409fdd4-5927-47d3-bc43-736498735cca)![page5image61640064](blob:https://app.gitbook.com/2b590a0b-145f-465b-99fc-2f6c76e76cbd)![page5image61640256](blob:https://app.gitbook.com/191eef7a-879b-4b6d-b78b-1089d191e5d6)![page5image61640448](blob:https://app.gitbook.com/bb8796e1-c769-46c1-ab21-90e6215200e5)![page5image61640640](blob:https://app.gitbook.com/9fd572ba-f07e-43f0-8868-c6ac74d2907d)![page5image61640832](blob:https://app.gitbook.com/0e32d244-bdfb-4c5c-8dc5-9438e7c73762)![page5image61641024](blob:https://app.gitbook.com/adb4e5b1-216a-4a96-af73-b21244fd00a5)![page5image61641216](blob:https://app.gitbook.com/855fd42b-75c5-4d18-aed8-ce9194938fb3)![page5image61641408](blob:https://app.gitbook.com/28df7b0e-580b-4769-93c1-13ba299b2196)![page5image61641600](blob:https://app.gitbook.com/a7cc21db-0b13-4c8d-98ba-eafc8e0a18ba)![page5image61641792](blob:https://app.gitbook.com/2b1e3f48-c3d3-4744-8a97-dca125156ea0)![page5image55466912](blob:https://app.gitbook.com/61c21913-ace7-493d-9da6-da9fa6d8154a)

1.入 队:

2.出队:

队列的链式存储结构，其实就是线性表的单链表，只不过需要加点限制，只能表尾插入元素，表头删除元素。为了方便操作，我们分别设置队头指针和队尾指针，队头指针指向头结点，队尾指针指向尾结点

![](../../.gitbook/assets/image%20%2850%29.png)







```text
typedef struct{ //链式队列结点 ElemType data;
struct LinkNode *next; }LinkNode;
typedef struct{ //链式队列 LinkNode*front,*rear; //队头和队尾指针
}LinkQueue;
```



1.入队:我们知道队列只能从队尾插入元素，队头删除元素。于是入队就是在队尾指针进行插入结点操作。链 队的插入操作和单链表的插入操作是一致的\`\`\`

```text
 void EnQueue(LinkQueue &Q，ElemType x){ s=(LinkNode *)malloc(sizeof(LinkNode)); s->data=x;
s->next=NULL;
Q.rear->next=s;
Q.rear=s; }

```

![](../../.gitbook/assets/image%20%2862%29.png)

2.出队:出队就是头结点的后继结点出队，然后将头结点的后继改为它后面的结点。



```text
bool DeQueue(LinkQueue &Q,ElemType &x){ if(Q.front==Q.rear) return false; //空队 p=Q.front->next;
x=p->data;
Q.front->next=p->next;
if(Q.rear==p) Q.rear=Q.front;
free(p);
return true; }
```

