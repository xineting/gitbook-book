# 5-3-图的遍历-广度优先搜索

## 1-广度优先搜索

> 图的遍历:  
> 从图中某一顶点出发，按照某种搜索方法沿着图中的边对图中的 所有顶点访问一次且仅访问一次。

* 首先访问起始顶点v; 
* 接着由出发依次访问v的各个未被访问过的邻接顶点
* 然后依次访问w1，w2 ,...,wi 的所有未被访问过的邻接顶点; 
* 在从这些访问过的顶点出发，访问它们所有未被访问过的邻接顶点; 
* ......，以此类推;

队列+辅助标记数组

![](../../.gitbook/assets/image%20%2861%29.png)

```c
bool visit(MAX_TREE_SIZE);
void BFSTraverse(Graph G){
    for (int i=0;i<G.vexnum;++i)
        visited[i]=FALSE;       //初始化数组
    InitQueue(Q);               //初始化队列Q
    for(int i;i<G.vexnum;++i){
        if(!visited[i])
            BFS(G,i);//对非连通图进行BFS调用
    }
}

void BFS(Grapg G,int v){
    visit(v);
    visited[v]=TRUE;
    EnQueue(Q,v);
    while(!isEmpty(Q)){
        DeQueue(Q,v);
        for(w=FirstNeighbor(G,v);w>0;w=NextNeighbor(G,v,w))
            if(!visited[w]){
                visit(w);
                visited[w]=TRUE;
                Enqueue(Q,w);
            }
    }    
}
```

### 性能

空间复杂度O\(\|V\|\)

时间复杂度

* 邻接矩阵法O（\|V\|^2）
* 邻接表法O\(\|V\|+\|E\|\)

### 无权图单源最短路径问题

> 定义从顶点U到顶点V的最短路径d\(u,v\)为从u到v的任何路径中最少的边数；若没有同路，则d\(u,v\)=∞。

### 广度优先生成树

在广度遍历过程中，我们可以得到一棵遍历树，称为广度优先生成树\(生成森林\)。

邻接矩阵法的广度优先生成树唯一，邻接表法的不唯一



