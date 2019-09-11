# 4-5-树的应用

## 并查集

> 一种简单的几何表示，通常用双亲表示法作为并查集的存储结构。  
> 通常用数组元素的下标代替元素名，用跟结点的下标代表子集合名，根结点的双亲结点为负数。

支持三种操作：

**Union\(S,Root1,Root2\):**把集合S中子集Root2合并入Root1中，要求Root1和Root2互不相交，否则不执行合并。  
**Find\(S,x\):**查找集合S中单元素x所在子集合，并返回该子集合的名字。  
**Initial\(S\):**将集合每一个元素都初始化为只有一个单元素的子集合。

![](../../.gitbook/assets/image%20%28101%29.png)

并查集的结构定义

```c
#define SIZE 100
int UFSets[SIZE];
```

初始化操作

```text
void Initial(int S[]){
    for(int i=0;i<size;i++){
        s[i]=-1;
    }   
}
```

Find操作

```c
int Find(int S[],int x){
    while(S[x]>=0){
        x=S[x];
    }
    return x;
}
```

Union操作

```c
void Union(int S[],int Root1,int Root2){
    S[Root2]=Root1;
}
```



