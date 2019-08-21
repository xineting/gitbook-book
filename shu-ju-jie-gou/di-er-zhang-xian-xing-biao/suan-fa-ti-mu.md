# 顺序表-算法题目

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

10-循环左移

将n\(n&gt;1\)个整数存放到一位数组R里。试设计一个在时间和空间两方面都尽可能高效的算法，将R中保存的序列循环左移p个位置。

```c
void Reverse(int R[],int left,int right){
    int i,tmp;
    for(i=0;i<(right-left+1)/2;i++){
        tmp = R[left+i];
        R[left+i]=R[right-i];
        R[right-i]=tmp;
    }
}
void Converse(int R[],int p){
    Reverse(R,0,p-1);
    Reverse(R,p,n-1);
    Reverse(R,0,n-1);
}
```

11-一个长度为L\(L&gt;=1\)的升序序列S，处在第 \[L/2\]个位置的数称为S的中位数。例如，若序列S1={11,13,15,17,19}，则S1的中位数是15，两个序列的中位数是含它们所有元素的升序序列的中位数。例如s2={2,4,6,8,20}。则S1和S2的中位数是11.现在有两个等长升序序列A和B，试设计一个在时间和空间两方面都尽可能高效的算法，找出两个序列A和B的中位数。

> 我个人觉得这个题写出来这种思路，如果不是巨佬或者出题人，一般都很难写的全面，很容易细节上出错，不过如果可以把思路写出来，应该可以得一大半分数了，所以，一定要把算法写的清楚，如果写不出来，就遍历，时间复杂度为O\(n\)，问题也不是很大。

```c
int M_search(int A[],int B[],int n){
    int s1=0,d1=n-1,m1,s2=0,d2=n-1,m2;
    while(s1!=d1||s2!=d2){
        m1=(s1+d1)/2;
        m2=(s2+d2)/2;
        if(A[m1]==B[m2]){
            return A[m1];
        }
        if(A[m1]<B[m2]){
            if((s1+d1)%2==0){
                s1=m1;
                d2=m2;
            }
            else{
                s1=m1+1;
                d2=m2;
            }
        }
        if(A[m1]>B[m2]){
            if((s2+d2)%2==0){
                d1=m1;
                s2=m2;
            }
            else{
                d1=m1;
                s2=m2+1;
            }
        }
    }
    return A[s1]<B[s2]?A[s1]:B[s2];
}
```



12-已知一个整数序列A=\(a0,a1,a2,a3,..,an-1\),其中0&lt;=ai&lt;n\(0&lt;=i&lt;n\)。若存在ap1=ap2=...=apm=x且m》n/2（0&lt;=pk&lt;n,1&lt;=k&lt;=m）,则称x为A的主元素。例如（0,5,5,3,5,7,5,5）,则称5为主元素，假设A中的n个元素保存在一个一位数组中，请设计一个高效的算法，找出A的主元素，输出A的出元素，若没有，则输出-1。

> 对于统考算法题，花费大量时间思考最优解法是得不偿失的。

```c
int Majority(int A[],int n){
  int i,c,count=1;
  c=A[0];
  for (i=1;i<n;i++){
    if(A[i]==c)
      count++;
    else
      if(count>0)
        count--;
      else{
        c=A[i];
        count=1;
      }
  }
  if(count>0){
    for(i=count=0;i<n;i++){
      if(A[i]==c)
        count++
    }
    if(count>n/2)return c;
    else return -1;
  }
}
```

