# 4-3-2-二叉树的遍历2

## 线索二叉树

### 线索化

* 若无左子树，则将左指针指向前驱结点
* 若无右子树，则将右指针指向后续结点

![](../../.gitbook/assets/image%20%2813%29.png)

![](../../.gitbook/assets/image%20%28111%29.png)

![](../../.gitbook/assets/image%20%2834%29.png)

![](../../.gitbook/assets/image%20%2881%29.png)

```c
typedef struct ThreadNode{
    ElemType data;
    struct ThreadNode *lchild,*rchild;
    int ltag,rtag;
}ThreadNode,*ThreadTree;
```

### 中序线索二叉树

* 前驱结点：若左指针为线索，则其指向结点为前驱结点，若左指针为左孩子，则其左子树的最右侧结点为前驱结点。
* 后驱结点若右指针为线索，则将其指向结点为后驱结点，若右指针为右孩子，则其右子树的最左侧结点为为其前驱结点。

通过中序遍历对二叉树线索化的递归算法如下

```c
void InThread (ThreadTree &p,ThreadTree &pre){//第一开始传入的pre为NULL
    if(p!=NULL){
        InThread(p->lchild,pre);//一直寻找p的左下子树结点
        if(p->lchild==NULL){
            p->lchild = pre;
            p->ltag=1;
        }//对左下结点的操作，把他们的左指针指向pre
        if(pre!=NULL&&pre->rchild==NULL){
            pre->rchild=p;
            pre->rtag=1;
        }//对分支结点的操作，把左下结点的pre指向中间结点
        pre=p;
        InThread(p->rchild,pre);
    }
}//跳出循环时pre指针为最右结点
```

![](../../.gitbook/assets/image%20%28111%29.png)

```cpp
void CreateThread(ThreadTree T){
    ThreadTree pre=NULL;
    if(T!=NULL){
        InThread(T,pre);
        pre->rchild=NULL;//处理最后一个结点
        pre->rtag=1;
    }
}
```

### 中序线索二叉树的遍历

* 寻找遍历过程中第一个结点，即p为根的情况的左下结点！

```c
ThreadNode *Firstnode(ThreadNode *p){
    while(p->ltag==0) p=p->lchild;
    return p;
}
```

* 寻找p的下一个结点

```c
ThreadNode *Nextnode(ThreadNode *p){
    if(p->rtag==0) return FirstNode(p->rchild);
    else return p->rchild;
}
```

* 遍历

```csharp
void InOrder(ThreadNode *T){
    for(ThreadNode *p=FirstNode(T);p!=NULL;p=NextNode(p))
        visit(p);
}
```

