# 5-4-图的遍历-深度优先搜索

## 1-深度优先搜索DFS

* 首先访问起始顶点v; 
* 接着由v出发访问v的任意一个邻接且未被访问的邻接顶点 wi ; 
* 然后再访问与wi邻接且未被访问的任意顶点yi ; 
* 若wi 没有邻接且未被访问的顶点时，退回到它的上一层顶点 v ; 
* 重复上述过程，直到所有顶点被访问为止

```c
bool visit[MAX_TREE_SIZE];
void DFSTraverse(Graph G){
    for(int i=0;i<G.vexnum;i++){
        visited[i]=FALSE;  
    }
    for(int i=0;i<G.vexnum;i++){
        DFS(G,i);
    }
}
void DFS(Graph G,int v){
    visit(v);
    visited[v]=TRUE;
    for(w=FirstNeighbor(G,v);w>=0;w=NextNeighbor(G,v,w)){
        if(!visited[w]);
            DFS(G,w);
    }
}
```

![](../../.gitbook/assets/image%20%2859%29.png)

### 

### 深度优先生成树

在深度遍历过程中，我们可以得到一棵遍历树，称为深度优先生成树\(生成森林\)。

### 遍历与连通性问题

在无向图当中，在任意结点出发进行一次遍历\(调用一次 BFS或DFS\)，若能访问全部结点，说明该无向图是连通的。

在无向图中，调用遍历函数\(BFS或DFS\)的次数为连通分 量的个数。

