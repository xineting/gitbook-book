# 4-3-2-二叉树的遍历2

## 线索二叉树

### 线索化

* 若无左子树，则将左指针指向前驱结点
* 若无右子树，则将右指针指向后续结点

![](../../.gitbook/assets/image%20%2811%29.png)

![](../../.gitbook/assets/image%20%2899%29.png)

![](../../.gitbook/assets/image%20%2830%29.png)

![](../../.gitbook/assets/image%20%2870%29.png)

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

```text

```

```text

```



### 中序线索二叉树的遍历

```text

```

```text

```

