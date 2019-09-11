# 5-7-图的应用-拓扑排序

### 有向无环图

> 不存在环的有向图，简称DAG图。

### AOV网:

> 若用一个DAG图表示一个工程，其顶点表示活动，用有向边&lt;vi,vj&gt;表示活动vi先于活动vj进行的传递关系，则将这钟DAG称为顶点表示活动网络，记为AOV网

### 拓扑排序 

> 对DAG所有顶点的一种排序，使若存在一条从顶点A 到顶点B的计路算径机基，础在排序程中序B语排言在A的数后据面结构。

### 算法

* 从DAG图中选择一个没有前驱的顶点并输出 
* 从图中删除该顶点和所有以它为起点的有向边
* 重复1、2直到当前的DAG图为空或当前图中不存在无前驱的顶点为止。
* 后一种情况说明图中有环。

![](../../.gitbook/assets/image%20%28214%29.png)

![](../../.gitbook/assets/image%20%28140%29.png)

![](../../.gitbook/assets/image%20%28239%29.png)



```c
bool TopologicalSort(Graph G){
    InitStack(S);
    for(int i=0;i<G.vexnum;i++)
        if(indegree[i]==0)
            push(S,i);
    int count=0;
    while(!isEmpty(S)){
        pop(S,i);
        print[count++]=i;
        for(p=G.Vertices[i],firstarc;p;p=p->nextarc){
            v=p->adjvex;
            if(!(--indegree[v]))
                push(S,v);
        }
    }
    if(count<G.vexnum)
        return false;
    else
        return true;
    
}
```

若邻接矩阵为三角矩阵，则存在拓扑排序;反之不一定成立。

![](../../.gitbook/assets/image%20%2832%29.png)

