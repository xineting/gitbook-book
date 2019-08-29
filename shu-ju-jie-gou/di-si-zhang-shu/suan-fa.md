# 算法

已知一棵二叉树按顺序存储结构进行存储，设计一个算法，求编号为i和j的两个结点的最近的祖先结点的值。

```c
ElemType Comm_Ancestor(SqlTree T,int i,int j){
    if(T[i]!='#'&&T[j]!='#'){
        while(i!=j){
            if(i>j)
                i/=2;
            else
                j/=2;
        }
        return T[i];
    }
}
```

