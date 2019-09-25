# 6-2-顺序,折半,分块查找

## 1-顺序查找

> 又称线性查找，主要用于在线性表中进行查找。

对无序线性表进行顺序查找，查找失败时要遍历整个线性表

```c
typedef struct{
    ElemType *elem;
    int TableLen;
}SSTable;
int Search_Seq(SStable St,ElemType key){
    St.elem[0]=key;
    for(int i=St.TableLen;St.elem[i]!=key;i--){
        return i;
    }
}
```

对关键字有序线性表进行顺序查找，查找失败时不一定要遍历整个线性表

![](../../.gitbook/assets/image%20%28183%29.png)

![](../../.gitbook/assets/image%20%28239%29.png)

## 2-折半查找

> 又称二分查找，仅适用于有序的顺序表

 **算法思想**

* 首先将给定值key与表中中间位置元素的关键字比较， 若相等，则返回该元素的位置; 若不等，则在前半部分或者是后半部分进行查找。
* 查找序列升序时， 若key小于中间元素，则查找前半部分; 若key大于中间元素，则查找后半部分。
* 重复该过程，直到找到查找的元素为止;或查找失败。

```c
int Binary_Search(SeqList L,ElemType key){
    int low = 0, high=L.TableLen-1 ,mid;
    while(low<=high){
        mid = (low+high)/2;
        if(L.elem[mid]==key)
            return mid;
        else if(L,emem[mid]>key)
            high = mid-1;
        else
            low = mid+1;
    }
}
```

折半查找的时间复杂度为O\( log2n\)

## 3-分块查找

> 又称索引顺序查找，它吸取了顺序查找和折半查找各自的优点， 既有动态结构，又适于快速查找。

![](../../.gitbook/assets/image%20%28238%29.png)

* 将查找表分为若干子块。块内的元素可以无序，但块间是有序的，对于所有块有第i块的最大关键字小于第i+1块的所 有记录的关键字。
* 建立索引表，索引表中的每个元素含有各块的最大关键字和各块中的第一个元素的地址，索引表按关键字有序排列。
* 
![](../../.gitbook/assets/image%20%2849%29.png)

![](../../.gitbook/assets/image%20%28211%29.png)

