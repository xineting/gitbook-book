# 7-5-归并排序和基数排序\*

## 1-归并排序

二路归并排序

1-合并两个有序线性表

```c
ElemType *B=(ElemType *)malloc ((n+1)*sizeof(ElemType));
void Merge(ElemType A[],int low,int mid,int high){

}
```

2-归并排序

```c
void MergeSort(ElemType A[],int low,int high){
    if(low<high){
        int mid = (low+high)/2;
        MergeSort(A,low,mid);
        MergeSort(A,mid+1,high);
        Merge(A,low,mid,high);
    }
}
```

O\(nlogn\)

空间复杂度O\(n\)

稳定

适合顺序存储，链式存储

## 2-基数排序

> 借助

n表示元素个数

r表示位数的取值范围

d位数

时间复杂度O\(d\(n+r\)\)

空间复杂度O\(r\)

稳定，不基于比较





