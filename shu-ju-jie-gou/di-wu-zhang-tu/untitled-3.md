# 5-6-图的应用-最短路径

> 两个顶点之间带权路径长度最短的路径为最短路径。

### 1-dijkstra带权图单源最短路径

```c
s[] : 标记已经完成的顶点。所有值初始化为0。源点下标的值为1。
dist[] : 记录从源点v0到其他各顶点当前的最短路径长度。 
数组中的值初始化为源点到各个顶点边的权值，即dist[i]=arcs[0][i];。
path[] : 记录从最短路径中顶点的前驱顶点，即path[i]为v到vi最短路径上vi 的前驱顶点。
```

* 数组中的值初始化: 
* 若源点v0到该顶点vi有一条有向边\(无向边\)，则另path\[i\]=0; 
* 否则path\[i\]=-1;

步骤：

带权图单源最短路径

* 初始化数组，并集合S初始为{0};
* 从顶点集合V-S中选出vj，满足dist\[j\]=Min{dist\[i\]\| vi∈V-S}，vj 就是当前求得的最短路径的终点，并另S∪{j};
* 修改此时从 v0 出发到集合V-S上任一顶点 vk 最短路径的长度: 若dist\[ j\]+arcs\[ j\]\[k\]&lt;dist\[k\] 则令dis\[k\]=dist\[ j\]+arcs\[ j\]\[k\]; path\[k\]=j;
* 重复2\)、3\)操作n-1次，直到S中包含全部顶点;
* 
![](../../.gitbook/assets/image%20%2862%29.png)

![](../../.gitbook/assets/image%20%28174%29.png)



不适合负数的权值

### Floyd算法

![](../../.gitbook/assets/image%20%28350%29.png)

![](../../.gitbook/assets/image%20%2887%29.png)



```c
void Floyd(Graph G){
    int A[G.vexnum][G.vexnum];
    for(int i=0;i<G.vexnum,i++){
        for(int j=0;j<G.vexnum;j++){
            A[i][j]=G.Edge[i][j];
        }
    }
    for(int k=0;k<G.vexnum;k++){
        for(int i=0;i<G.vexnum,i++){
            for(int j=0;j<G.vexnum;j++){
                if(A[i][j]>A[i][k]+A[k][j])
                    A[i][j]=A[i][k]+A[k][j];
            }
        }
    }
}
```



