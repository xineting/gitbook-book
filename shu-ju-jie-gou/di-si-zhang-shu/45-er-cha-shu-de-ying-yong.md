# 4-5-二叉树的应用

## 二叉排序树

> 简称BST,也称二叉查找树

二叉查找树或者是一棵空树，或者是有以下特性的非空二叉树：

* 若左子树非空，则左子树上所有结点关键字值均小于根结点的关键字值。
* 若右子树非空，则右子树上所有结点关键字值均大于根结点的关键字值。
* 左右子树本身也是一棵二叉排序树。

中序遍历结果递增

### 二叉排序树的查找

```c
BSTNode *BST_Search(BiTree T,ElemType key,BSTNode *&p){
//查找函数返回指向关键字值为key的结点指针，若不存在，返回NULL
    p=NULL;
    while(T!=NULL&&key!=T->data){
        p=T;
        if(key<T->data) T=T->lchild;
        else T=T->rchild;
    }
    return T;
}
```

### 二叉排序树的插入

```c
int BST_Insert(BiTree &T,KeyType k){
    if(T==NULL){
        T=(BiTree)malloc(sizeof(BSTNode));
        T->data=k;
        T->lchild=T->rchild=NULL;
        return 1;
    }
    else if(k==T->data){
        return 0;
    }
    else if(l>T->data){
        return BST_Insert(T->rchild);
    }
    else{
        return BST_Insert(T->lchild);
    }
}
```

### 二叉排序树的构造

```c
void Create_BST(BiTree &T,KeyType str[],int n){
    T=NULL;
    for(int i=0;i<n;i++){
        BST_Insert(T,str[i]);
    }
}
```

### 二叉排序树的删除

* 若被删的是叶子
* 若被删除的只有一棵子树，则让子树代替氟结点的子树
* 若被删除的有两棵子树，则让z的中序序列的直接后继（或直接前驱）代替z，并删去直接后继（直接前驱）结点。



删除并插入，得到的二叉排序树是否相同

* 可能相同，也可能不同

### 查找效率\(ASL\)

![](../../.gitbook/assets/image%20%28286%29.png)

## 平衡二叉树（AVL树）

> 任意结点的平衡因子不超过1
>
> 平衡因子：右子树高度-左子树高度

高度为h的最小平衡二叉树的结点数Nh

N\[1\]=1;

N\[2\]=2;

N\[3\]=N\[1\]+N\[2\]+1

……

N\[h\]=N\[h-1\]+N\[h-2\]+1



### 平衡二叉树的判断

![](../../.gitbook/assets/image%20%28263%29.png)

```c
void Judge_AVL(BiTree &bt,int &balance,int &h){
    int bl=0,br=0,hl=0,hr=0;
    if(bt==NULL){
        h=0;
        balance=1;
    }
    else if(bt->lchild==NULL&&bt->rchild==NULL){
        h=1;
        balance=1;
    }
    else{
        Judge_AVL(bt->lchild,bl,hl);
        Judge_AVL(bt->rchild,br,hr);
        h=hl>hr?hl+1:hr+1;
        if (abs(hl-hr)>2&&bl==1&&br==1)
            balance=1;
        else
            balance=0;
    }
}
```

### 平衡二叉树的插入

先插入，再调整

![](../../.gitbook/assets/image%20%2861%29.png)

#### LL平衡螺旋（右单螺旋）

> 在结点A的左孩子的左子树上插入了新结点

* 调整方法：右旋操作：将A的左孩子B代替A，将A结点称为B的右孩子，
* B的原右子树作为A的左子树。

![](../../.gitbook/assets/image%20%28124%29.png)

#### 

#### RR平衡旋转（左单螺旋）

> 在结点A的右子树的右孩子上插入了新结点

* 调整方法：左旋操作：将A的右孩子B代替A，将A结点称为B的左孩子，
* B的原左子树作为A的右子树。

![](../../.gitbook/assets/image%20%2843%29.png)

例子：

![](../../.gitbook/assets/image%20%28162%29.png)

#### LR平衡旋转

> 在结点A的左结点的右子树插入了新结点，

* 先左旋后右旋操作

![](../../.gitbook/assets/image%20%28259%29.png)

#### RL平衡旋转（原理相同）

* 先右旋后左旋。

例子

![](../../.gitbook/assets/image%20%28202%29.png)



## 哈夫曼树

* 带权路径长度：路径上所经过边的个数
* 权：结点被赋予的数值
* 树的带权路径长度（WPL）：树中所有叶结点的带权路径长度之和称为该树的带权路径长度

在含有N个带权叶子结点的二叉树中，其中带权路径长度WPL最小的二叉树称为哈夫曼树，也称最优二叉树。

### 哈夫曼树的构造算法

> 给定N个权值分别为w1,w2,w3,w4...wn的结点。通过哈夫曼算法可以构造出最优二叉树，算法的描述如下：

1. 将这N个结点分别作为N棵仅含一个结点的二叉树，构成森林F。
2. 构造一个新结点，并从F中选取两棵根结点权值最小的树作为新结点的左、右子树，并且将新结点的权置为左右子树上根结点的权值之和。
3. 从F中删除刚才选出的那两棵树，同时将得到的树加入F中。
4. 重复2）和3），直至F中只剩下一棵树为止。

### 哈夫曼树的重要性质

1. 每个初始结点都会成为叶结点，双支结点都为新生成的结点
2. 权值越大离根结点越近，反正权值越小离根结点越远
3. 哈夫曼树中没有结点的度为1
4. n个叶子结点的哈夫曼树的结点总数为2n-1，其中度为2的结点数为n-1.

![](../../.gitbook/assets/image%20%2887%29.png)

## 哈夫曼编码

![](../../.gitbook/assets/image%20%2816%29.png)

* 前缀编码：如果没有一个编码是另一个编码的前缀，则称这样的编码为前缀编码。如0、101、100是前缀编码。

利用哈夫曼算法构造哈夫曼树，权值为每个字母出现的次数。

![](../../.gitbook/assets/image%20%28114%29.png)

