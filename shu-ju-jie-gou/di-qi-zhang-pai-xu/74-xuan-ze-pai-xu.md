---
description: sad
---

# 7-4-选择排序\*

## 1-1-直接选择排序

> 基本思想

```c
void SelectSort(ElemType A[],int n){
    for(int i=0;i<n-1;i++){
        int min=i;
        for(int j=i+1;j<n;j++){
            if(A[j]<A[min]){
                min=j;
            }
        }
        if(min!=i){
            swap(A[i],A[min]);
        }
    }
}
```

不稳定，顺链

## 1-2-堆排序

> 基本思想

小根堆

大根堆

堆的初始化

```c
void BuildMaxHeap(ElemType A[], int len){
    for(int i=len-/2;i>0;i--){
        AdjustDown(A,i,len);
    }
}

void AdjustDown(ElemType A[], int k, int len){
    A[0]=A[k];
    for(int i=2*k;i<len;i++){
        if(i<len&&A[i]<A[i+1])
            i++;
        else{
            A[k]=A[i];
            k=j;
        }
    }
    A[k]=A[0];
}
```

不稳定，顺序存储（链式存储）

O\(nlogn\)

O\(1\)

堆的插入

```c
void AdjustUp(){

}
```



