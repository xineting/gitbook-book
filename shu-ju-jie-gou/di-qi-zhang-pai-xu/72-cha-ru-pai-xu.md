# 7-2-插入排序\*

## 1-1直接插入排序

每次将一个待排序的直接插入已知数列中

```c
void InsettSort(ElemType A[],int n){
    int i,j;
    for(i=2;i<=n;i++){
        A[0]=A[i];
        for(j=i-1;A[0].key<A[j];j--){
            A[j+1]=A[j];
        A[j+1]=A[0];
        }
    }
}
```

稳定O\(n2\)

## 1-2-折半插入排序

```c
void BInsertSort(ElemType A[],int n){
    int i,j;
    int low,high,mid;
    for(i=2;i<=n;i++){
        low=1;high=i-1;
        while(low<=high){
            mid=(low+high)/2;
            if(A[mid]-key>A[0].key)
                high=mid-1;
            else
                low=mid+1;
        }
        for(j=1;j>=high+1;j--){
            A[j+1]=A[j];  
        }
        A[high+1]=A[0];
    }
}
```



稳定O\(n2\)，顺序存储。

## 1-3-希尔排序

> 缩小增量排序

```c
void ShellSort(ElemType A[],int n){
    for(int dk=n/2;dk>=1;dk=dk/2)
        for(int i=dk+1;i<=n;i++){
            if(A[i].key<A[i-dk].key){
                A[0]=A[i];
                for(int j=i-dk;j>0&&A[0].key<A[j].key;j-=dk)
                    A[j+dk]=A[j];
                A[j+dk]=A[0];
            }
        }
}
```

O\(n2\)不稳定，顺序存储

