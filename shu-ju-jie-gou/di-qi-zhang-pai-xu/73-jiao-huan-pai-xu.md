# 7-3-交换排序\*

## 1-1-冒泡排序

> 基本思想：

```c
void BubbleSort(ElemType A[],int n){
    for(int i=0;i<n;i++){
        bool flag = false;
        for(int j=n-1;j>1;j--){
            if(A[j-1].key>A[j].key){
                swap(A[j-1],A[j]);
                flag=true;
            }
            if(flag==flase)
                return;
        }
    }
}
```

一次冒泡会将一个元素放到他的最终位置上

## 1-2-快排

>

```c
int Partition(ElemType A[],int low,int high){
    ElemType pivot = A[low];
    while(low<high){
        while(low<high&&A[high]>=pivot)
            high--;
        A[low]=A[high];
        while(low<high&&A[low]<=pivot)
            low++;
        A[high]=A[low];
    }
    A[low]=pivot;
    return low;
}
```

O\(high-low+1\)不稳定，

最好

平均时间复杂度为O\(nlog2n\)

空间复杂度O\(log2n\)

最坏的时间复杂度为O\(n2\)

空间复杂度O\(n\)

