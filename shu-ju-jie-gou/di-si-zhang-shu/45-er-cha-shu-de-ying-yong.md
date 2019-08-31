# 4-5-二叉树的应用\*

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

![](../../.gitbook/assets/image%20%28171%29.png)

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

![](../../.gitbook/assets/image%20%28156%29.png)

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

![](../../.gitbook/assets/image%20%2835%29.png)

#### LL平衡螺旋（右单螺旋）

> 在结点A的左孩子的左子树上插入了新结点

* 调整方法：右旋操作：将A的左孩子B代替A，将A结点称为B的右孩子，
* B的原右子树作为A的左子树。

![](../../.gitbook/assets/image%20%2869%29.png)

#### 

#### RR平衡旋转

> 在结点A的右子树的右孩子上插入了新结点

* 调整方法：右旋操作：将A的左孩子B代替A，将A结点称为B的右孩子，
* B的原右子树作为A的左子树。

![](../../.gitbook/assets/image%20%2824%29.png)

![](../../.gitbook/assets/image%20%28114%29.png)

![](../../.gitbook/assets/image%20%2894%29.png)

![](../../.gitbook/assets/image%20%28153%29.png)

## 哈夫曼树

### 带权路径长度

### 哈夫曼树的构造算法

### 哈夫曼树的重要性质

## 哈夫曼编码

