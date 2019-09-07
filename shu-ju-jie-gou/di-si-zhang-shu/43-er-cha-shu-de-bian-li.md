# 4-3-1-二叉树的遍历

按某条搜索路径访问树中的每个结点，树的每个结点被访问一次，而且只访问一次。

![](../../.gitbook/assets/image%20%2821%29.png)

## 1-先序遍历

### 递归算法

若二叉树非空

* 访问根结点
* 先序遍历左子树
* 先序遍历右子树

### 

```c
void PreOrder(BitTree T){
    if(T!=NULL){
        visit(T);
        PreOrder(T->lchild);
        PreOrder(T->rchild);
    }
}
```

时间复杂度O\(N\)

### 非递归算法

* 初始时依次扫描根结点的左侧结点，并将它们一一进栈；
* 出栈一个结点，访问他；
* 扫描该孩子的右结点并将其进栈；
* 依次扫描右孩子的左侧结点并一一进栈；
* 反复该过程，直到判空为止。

```c
void InOrder2(BitTree T){
    InitStack(S);
    BitTree p =T;
    while(p||!IsEmpty(s)){
        if(p){
            Push(S,p);
            p=p->lchild;
        }
        else{
            Pop(S,p);
            visit(p);
            p=p->rchild;
        }
    }
}
```

## 2-中序遍历



若二叉树非空



* 中序遍历左子树
* 访问根结点
* 中序遍历右子树

```c
void InOrder(BitTree T){
    if(T!=NULL){
        InOrder(T->lchild);
        visit(T);
        InOrder(T->rchild);
    }
}
```

## 3-后序遍历



```c
void PostOrder(){
    if(T!=NULL){
        PostOrder(T->lchild);
        PostOrder(T->rchild);
        visit(T);
    }
}
```

## 4-层次遍历

借助队列

* 初始时将根入队，并访问根结点，然后出队；
* 若有左子树，则将左子树的根入队；
* 若有右子树，则将右子树的根入队；
* 然后出队，访问该结点；
* 反复过程直到队列为空。

![](../../.gitbook/assets/image%20%286%29.png)



## 5-由遍历序列构造二叉树

![](../../.gitbook/assets/image%20%28198%29.png)



### 由先序遍历和中序遍历构造二叉树的过程

* 在先序遍历中，第一个结点是跟结点
* 根结点将中序遍历序列划分为两部分
* 在先序中确定两部分的结点，并且两部分的结点分别为左子树的根和右子树的根。
* 在子树中递归重复该过程，便能确定一颗二叉树。
* * 
![](../../.gitbook/assets/image%20%2891%29.png)



