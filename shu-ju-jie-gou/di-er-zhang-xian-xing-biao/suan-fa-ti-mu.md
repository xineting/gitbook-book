# 算法题目

9-线性表\(a1,a2,a3,...an\)中元素递增有序且按顺组存储在计算机内。要求设计一算法完成用最少时间在表中查找数值为e的元素。若找到将其和后继元素位置相交换，若找不到，则插入使表中元素仍递增有序。

```cpp
void SearchInsert(SqList &l,ElemType e){    
    int low=0,high=l.length-1,mid;
    while(low<=high){
        mid = (low+high)/2;
        if(l.data[mid]==e) break;
        else if(l.data[mid]>e) low = mid+1;
        else high = mid-1;
    }
    if(l.data[mid]==e&&mid!=n-1){
        ElemType tmp;
        tmp = l.data[mid];
        l.data[mid] = l.data[mid+1];
        l.data[mid+1] = tmp;
    }
    if(low>high){
        for(int i = l.length-1;i>high;i--){
            l.data[i+1]=l.data[i];
        }
        l.data[low]=e;
    }
}
```

