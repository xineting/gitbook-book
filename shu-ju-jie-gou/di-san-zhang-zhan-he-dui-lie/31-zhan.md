# 3-1-栈

* 栈：只允许在一端进行插入或删除操作的线性表
* 栈顶:栈中允许进行插入和删除的那一端
* 栈底：固定的，不允许进行插入和删除的另一端。



## 1-顺序栈

```c
#define MaxSize 50 //定义栈中元素的最大个数 
typedef struct{
    Elemtype data[MaxSize]; //存放栈中元素 
    int top;
} SqStack;
```

> Top值不能超过MaxSize
>
> 空栈的判定条件通常定为top==-1，满栈的判定条件通常为top==MaxSize-1，栈中数据元素个数为top+1

* 判断栈空

```c
bool StackEmpty(SqStack S){
    if(s.top==-1)
        return true;
    else 
        return false;
}
```

* 入栈

```c
bool Push(SqStack &S ，ElemType x){
    if(S.top==MaxSize-1)
        return false;
    S.data[++S.top]=x; 
    return true;
}
```

* 出栈

```c
bool Pop(SqStack &S，ElemType &x){ 
    if(S.top==-1)
        return false;
    x=S.data[S.top--]; 
    return true;
}
```

### 共享栈

> 顺序栈的存储空间大小需要事先开辟好，很多时候对每个栈各自单独开辟存储空间的利用率不如将 各个栈的存储空间共享

```c
#define MaxSize 100 //定义栈中元素的最大个数 
typedef struct{
    Elemtype data[MaxSize]; //存放栈中元素
    int top1; //栈1栈顶指针 
    int top2; //栈2栈顶指针
} SqDoubleStack;//顺序共享栈的简写
```

* 入栈

```c
bool Push(SqDoubleStack &S ，ElemType x，int stackNum){
    if(S.top1+1==s.top2)
        return false; //栈满
    if(stackNum==1)
        S.data[++S.top1]=x; //栈1有元素进栈 
    else if(stackNum==2) 
        S.data[--S.top2]=x; //栈2有元素进栈
    return true;
}
```

![](../../.gitbook/assets/image%20%28164%29.png)

## 2-链式栈

```c
typedef struct SNode{
    Elemtype data; //存放栈中元素
    struct SNode *next ; //栈顶指针
} SNode，*SLink 

typedef struct LinkStack{
    SLink top;
    int count; 
}LinkStack
```



> 1.链栈一般不存在栈满的情况。  
> 2.空栈的判定条件通常定为top==NULL;



```c
bool Push(LinkStack *S, ElemType x){
    SLink p=(SLink)malloc(sizeof(SNode)); 
    p->data=x;
    p->next=S->top;
    S->top=p;
    S->count++;
    return true;
}
```



```c
bool Pop(LinkStack *S, ElemType&x){
    if(S->top==NULL) 
        return false;
    x=S->top->data;
    Slink p=S->top;
    S->top=S->top->next; 
    free(p);
    S->count--;
    return true;
}
```

![](../../.gitbook/assets/image%20%28103%29.png)

