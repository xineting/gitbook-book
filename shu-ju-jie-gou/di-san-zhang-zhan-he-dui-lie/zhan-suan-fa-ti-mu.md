# 栈-算法题目

5-设有两个顺序栈都采用顺序栈方式，并且共享一个存储区\[0,.....maxsize-1\],为了尽量利用空间，减少溢出的可能，可采用栈顶相向，迎面增长的存储方式，试设计s1,s2,有关的入栈和出栈的操作算法。

```c
#define elemtypr int 
#define maxsize 100
typedef struct {
    elemtype data[maxsize];
    int top[2];
}stk;
stk s;
```

```c
//入栈
int push(int i,elemtype x){
    if(i<0||i>2){
        printf("输入错误");
        return -1;
    }
    if (s.top[0]+1==s.top[1]){
        printf("栈已满");
    }
    switch(i):
        case 0:{
            s.data[++s.top[0]]=x;return 0;break;
        }
        case 1:{
            s.data[--s.top[1]]=x;return 0;break;
        }
}
```



```c
//出栈
int pop(int i,elemtype &x){
    if(i<0||i>2){
        printf("输入错误");
        return -1;
    }
    if ((i==0&&s.top[0]==-1)||(i==1&&s.top[1]==maxsize)){
        printf("空栈");
    }
    switch(i):
        case 0:{
            x=s.data[s.top[0]--];return 0;break;
        }
        case 1:{
            x=s.data[s.top[1]++];return 0;break;
        }
}
```

