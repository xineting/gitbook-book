# 队列-算法题目

2-Q是一个队列，S是一个空栈，实现队列中元素逆置的算法

```c
void Reverse(Queue &Q,Stack &S){
    while(!EmptyQueue(Q)){
        elemtype x;
        DeQueue(Q,x);
        Push(S,x);
    }
    while(!EmptyStack(S)){
        elemtype x;
        pop(S,x);
        EnQueue(Q,x);
    }
}
```

