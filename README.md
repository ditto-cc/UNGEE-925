# 一、绪论（背就完了）

## 1、 数据结构

1. 数据 
2. 数据元素
3. 数据项（**最小**单位）
4. 数据对象（集合)
5. 数据结构
6. 数据的**逻辑**结构（**线性**、**非线性**）
7. 数据的**物理**结构（**顺序**存储方法、**链式**存储方法、**索引**存储方法、**散列**存储方法）
8. ADT抽象数据类型（数据对象、数据关系、基本操作）

## 2、 算法

1. 算法**特性**：1) 有穷性  2) 确定性  3) 输入  4) 输出  5) 可行性
2. 算法设计**目标**：1) 正确性  2) 可读性  3) 健壮性  4) 高效率与低存储量需求

# 二、线性表（最基础，常考）

## 1、概念和结构体定义

1. 逻辑特性 ：只有一表头，只有一表尾，**表头无前驱，表尾无后继**，其他一前驱和后继
2. 存储结构：

> 顺序表： **连续空间 随机访问** 

>
> ```c
> typedef struct SqList {
>         DataType data[MAXSIZE];
>         int length;
> } SqList;					//顺序表
> ```

> 链表：**动态分配 不支持随机访问** （包括单链表、双链表、循环单/双链表、静态链表(用一维数组表示)）

> ```c
> typedef struct ListNode {
>        DataType data;
>        ListNode *next;		
> } ListNode;					//单链表
> 
> typedef struct DListNode {
>        DataType data;
>        DListNode *prior, *next;
> } DListNode;				//双链表
> 
> ```
>  
> |      | 顺序表 | 链表 |
> | ---- | ------ | ---- |
> | 插入 | O(n)   | O(1) |
> | 查找 | O(n)   | O(n) |
> | 删除 | O(n)   | O(n) |
>

## 2、基本操作（基础，常考）
1. 顺序表
	- 添加、删除操时计算顺序表中元素的移动次数
2. 链表
	- 链表的**头插法**和**尾插法**代码实现（读写算法题可能都会有）
	- 单、双链表元素插入操作（选择题）
	- 单、双循环链表判断是否为空（选择填空）

# 三、栈、队列★★★★★

## 1、概念（基础）
1. 栈
	- 定义：一端操作，栈顶栈底
	- 特点：**先进后出**（后进先出）**FILO**
	- 存储结构：顺序栈、链栈
	- 数学性质：出栈序列总数N=C (n, 2n) / (n + 1)

2. 队列
	- 定义：一端入队，一端出队，队头队尾
	- 特点：**先入先出**（后入后出）**FIFO**
	- 存储结构：顺序队、链队

## 2、应用（算法题很少实现栈和队列，一般直接使用接口）
1. 栈
	- 括号匹配（没考过）
	- 表达式计算（逆波兰表达式求值，没考过；中缀表达式->前、后缀表达式）
	- **树的先序和后序遍历，图的深度优先遍历**代码实现（非递归实现）
	- 共享栈：两个栈共享一个顺序表，栈底在两端，栈顶相遇时（```top1 == top2```）溢出

2. 队列
	- 循环队列（顺序队列）
		- 目的：解决假溢出
		- 队列元素个数：A[0...M]数组 元素个数=**```(rear- front + M) % M```**
		- 判断队列为空：**```front == rear```**
		- 判断队列满：**```front == (rear + 1) % M```**
		- 出队：**```front = (front + 1) % M```**
		- **树的层次遍历、图的广度优先遍历**代码实现
	- 链队列（非重点）
		
- 判断空：**```Q.front == NULL || Q.rear == NULL```**
		
	- 双端队列（选择题，可能的输出序列）
		
		> 输入受限：一端入，两端出
		> 输出受限：两端入，一端出


# 四、串（每年必考）

## 1、定义（背）
1. 串：0或多个字符组成的有限序列（例如："abc"）
2. 空串：0个元素的串（例如：""）
3. 模式匹配：求某子串的定位操作```index(string s, string t)```（**注：下标从1开始**）
4. 求子串：```substr(string s, int pos, int len)```**（注：下标从1开始）**

## 2、KMP （掌握方法属于白给的题）
> **next nextval 数组求法（填空、选择必考★★★★★）**


# 五、数组、矩阵与广义表（常考）

## 1、数组（套路题）
- 一维数组：(a1, a2, a3,...)
- 二维数组：[(a1, a2, a3), (a1, a2, a3),...]一维数组的一维数组
> **行、列优先计算存储地址**（选择填空，几乎必考，看清是行还是列优先和起始下标）

## 2、矩阵（选填居多，算法题少见，需要重视）

1. 特殊矩阵压缩
	- **对称矩阵**：压缩在一维数组，计算下标（必考，看清下标起始位置（0或1）和上或下三角存储）不用背公式
	- 三角阵（上或下三角元素值相同）：没考过，和对称矩阵压缩类似，将上或下三角的元素存储在一维数组最后
	- 对角矩阵
2. 稀疏矩阵顺序存储
	- **三元组表示法**（重点，考过画表，画转置之后的结果）**考过一次快速转置算法题，比较刁钻**
	- 伪地址法（非重点，映射到一维，需要2N空间，N为非0元素个数，A[i][j] -> B[n(i - 1) + j]
3. 稀疏矩阵链式存储（图的表示法）
	- 邻接表（图那一章的重点）
	- 十字链表（考过，要会画图，写代码几率不大，但是不难）

## 3、广义表（属于白给的题:)）
1. 举几个例子就行了
	- A = ()  空表 长=0 深=1
	- B = (d, e) B的元素全是原子 长=2 深=1
	- C = (b, (c, d)) C有两个元素，原子b和广义表（c, d) 长=2 深=2
	- D = (B, C) D有两个元素 长=2 深=3 注：B，C为其它广义表的引用
	- E = (a, E) E有两个元素，a和E本身 长=2 深=∞
2. **长度 = 最上层元素个数 + 1**
3. **深度 = 括号的最大层数**
4. **Head 表头函数**：取出广义表中第一个元素
5. **Tail 表尾函数**：除第一个元素外，**剩下的元素构成的表**（注：得到的是一个**表**）
	
> 例如： A=(a, b)  Tail(A) = ((b)); B=(a) Tail(B) = ()

6. **画图题**（头尾链表存储结构）
	- 原子节点（标记域0、数据域）
	- 广义表节点（标记域1、头指针域、尾指针域）
	
	  > 标记域用来区分两种节点


# 六、树与二叉树★★★★★

## 1、概念（必须理解，基础，否则影响算法题理解）
> 由唯一的根和若干棵互不相交的子树构成，每一个子树又是一棵树，节点数为0时树为空树
1. 节点的度：节点拥有的子树（分支）数量
2. 树的度：树中节点度的最大值
3. 叶子节点（终端节点）：度为0
4. 非终端节点（分支节点）：度不为0
5. 孩子：某节点的子树的根节点
6. 双亲：与孩子相对应
7. 兄弟：同一个双亲的孩子之间互为兄弟
8. 祖先：从根到某节点的路径上所有节点
9. 子孙：以某节点为根的子树中所有节点
10. 层次：根为第一层，根的孩子为第二层，依此类推
11. 树的高度（深度）：节点的最大层次
12. 堂兄弟：双亲在同一层的节点
13. 有序树：树中节点的子树从左到右有次序
14. 无序树：树中节点的子树从左到右无次序
15. 丰满树：理想平衡树，除最底层外，其它层都是满的
16. 森林：若干课不相交的树的集合

## 2、树的存储结构
1. 顺序（双亲存储结构）kruskal算法
2. 链式
	- 孩子存储结构（图的邻接表存储结构）
	- 孩子兄弟存储结构（森林、树和二叉树转化）

## 3、二叉树（重点）
> 每个节点最多有两个子树，左右不可以颠倒
1. 满二叉树：所有分支节点都有两个孩子（层数为h 的满二叉树节点数= 2^h - 1）
2. 完全二叉树：最后一层的节点集中在最左侧，其他层是满的
3. 性质：
	- **N0 = N2 + 1 (推导：N0 + N1 + N2 = N1 + 2 * N2 + 1，节点数=分支树 + 1，可以推广到所有树)**
	- 高度为h的二叉树最多有2^h - 1个节点
	- 第i层最多有 2^(i - 1)个节点
	- **n个节点最多组成C(n, 2n) / (n - 1)种不同的二叉树**
	- **n个节点深度=└log2 n┘ + 1 = ┌log2 （n + 1）┐** 
	- 按层次给二叉树节点编号（堆排序）
		- 从1开始：第i号节点的双亲编号=i/2，左孩子=i*2，右孩子=i*2 + 1
		- 从0开始：第i号节点的双亲编号=(i-1)/2=┌i/2┐- 1，左孩子=i*2 + 1，右孩子=i*2 + 2

4. 存储结构：
	- 顺序存储：**最适合完全二叉树**，否则浪费空间
	
	- 链式存储：节点包含左指针域lchild、右指针域rchild和数据域data
		```c
		typedef struct BTNode {
		    DataType data;	// 数据类型可自行修改
		    struct BTNode *lchild, *rchild;
		} BTNode;
		```
	
5. **二叉树遍历**
	
	- 先序遍历：
	
	  ```c
	  void preorder(struct BTNode *root) {
	      if (!root)
	          return;
	      Visit(root->data);
	      preOrder(root->lchild);
	      preOrder(root->rchild);
	  }
	  
	  //非递归先序遍历
	  void preOrderNR(struct BTNode *root) {
	      if (!root)
	          return;
	      struct BTNode S[maxSize];
	      int top = -1;
	      //栈和队列的实现和操作比较简单，如果栈和队列的实现不是核心算法
	      //算法题应该可以直接接口：InitStack Push Pop StackEmpty
	      //简化代码，避免出错
	      S[++top] = root;
	      struct BTNode *p;
	      while (top > -1) {
	          p = S[top--];
	          //Visit是访问节点函数，按题意更改
	          Visit(p->data);
	          //先右后左
	          if (p->rchild)
	              S[++top] = p->rchild;
	          if (p->lchild)
	              S[++top] = p->lchild;
	      }
	  }
	  ```
	
	- 中序遍历：
	
	  ```c
	  //递归中序遍历
	  void inOrder(struct BTNode *root) {
	      if (!root)
	          return;
	      inOrder(root->lchild);
	      Visit(root->data);
	      inOrder(root->rchild);
	  }
	  
	  //非递归中序遍历
	  void inOrderNR(struct BTNode *root) {
	      if (!root)
	          return;
	      InitStack(S);
	      struct BTNode *p = root;
	      while (p && !StackEmpty(S)) {
	          if (p) {
	              Push(S, p);
	              p = p->lchild;
	          } else {
	              Pop(S, p);
	              Visit(p->data);
	              p = p->right;
	          }
	      }
	  }
	  ```
	
	- 后序遍历：
	
	  ```c
	  //递归后序遍历
	  void postOrder(struct BTNode *root) {
	      if (!root)
	          return;
	      postOrder(root->lchild);
	      postOrder(root->rchild);
	      Visit(p->data);
	  }
	  
	  //非递归后序遍历
	  //逆后序遍历序列=先序遍历过程中左右子树遍历顺序交换得到的序列
	  void postOrderNR(struct BTNode *root) {
	      if (!root)
	          return;
	      InitStack(S1);
	      InitStack(S2);
	      Push(S1, root);
	      struct BTNode *p;
	      while (!StackEmpty(S1)) {
	          Pop(S1, p);
	          Push(S2, p);
	          //先左后右
	          if (p->lchild)
	              Push(S1, p->lchild);
	          if (p->rchild)
	              Push(S1, p->rchild);
	      }
	      while (!StackEmpty(S2)) {
	          Pop(S2, p);
	          Visit(p->data);
	      }
	  }
	  ```
	
	- 层次遍历：
	
	  ```c
	  void levelOrder(struct BTNode *root) {
	      if (!root)
	          return;
	      InitQueue(Q);
	      Enqueue(Q, root);
	      struct BTNode *p;
	      while (!QueueEmpty(Q)) {
	          Dequeue(Q, p);
	          Visit(p->data);
	          if (p->lchild)
	              Enqueue(Q, p->lchild);
	          if (p->rchild)
	              Enqueue(Q, p->rchild);
	      }
	  }
	  ```
	
6. **线索二叉树**
```c
typedef enum PointerTag {Link, Thread}	
//Link代表指向左右孩子，Thread代表指向前驱或后继

typedef struct BiThrNode {
    DataType data;
    int ltag, rtag;
    struct BiThrNode *lchild, *rchild;
} BiThrNode;
```

> **画图题**：给出二叉树，可以画出线索化后的树
> 
> **代码填空**：考过中序线索二叉树的遍历，重点看一下中序线索化的代码p134
> 
> **算法题**（难点，之前没考过）：插入节点后，维持线索化，有可能考算法题。模拟题常有，相对较难

7. **森林、树、二叉树转化**
	
	- 树-->二叉树
		1) 将同一节点的各孩子连起来
		2) 将每个节点的分支从左往右，除第一个外，其余都剪掉
		3) 调整二叉树
	- 二叉树-->树（树-->二叉树的逆过程）
	- 森林-->二叉树
		1) 先将森林的各个树转化为二叉树
		2) 将第二棵树作为第一棵树的右子树，将第三棵树作为第二棵树的右子树，依此类推
	- 二叉树-->森林（森林-->二叉树的逆过程）

8. 树和森林的遍历（**易错点**）
	- 树的遍历
		- 先序遍历：先访问根节点，再先序遍历子树
		- 后序遍历：先遍历根节点的每一棵子树，再访问根节点
	- **森林的先序遍历序列**是对应**二叉树的先序遍历序列**
	- **森林的后序遍历序列**是对应**二叉树的中序遍历序列**

9. 二叉排序树、平衡二叉树（看排序那一章）

10. 赫夫曼树、赫夫曼编码（**画图**）
	- 赫夫曼树：**最优二叉树**，带权路径长度最短
        - 路径：从树中一个节点到另一个节点的分支构成的路线
        - 路径长度：路径上的分支数目
        - 树的路径长度：根到每个节点的路径长度之和
        - 带权路径长度：节点具有权值，从该节点到根的路径长度乘节点权值
        - 树的带权路径长度**(WPL)**（考过计算WPL的算法题）：**叶子节点的带权路径长度之和**
	- 赫夫曼编码：由赫夫曼树根节点到叶子节点的路径写出叶子节点的赫夫曼编码，左0右1（左1右0），不唯一
		- 任一字符的编码串（到根的路径）都不是另一个字符的前缀（到根的路径）
		- 产生的是**最短前缀码**

	> **注：赫夫曼树可以是多叉树**

# 七、图★★★★★

## 1、基本概念（基础，必须理解）

1. 图：由节点的有穷集合V和边的集合E
2. 有向图、无向图：边有无方向
3. 弧：含箭头一端是弧头，另一头是弧，例如<v1, v2>
4. 顶点的度、入度和出度
	- 度： 与某顶点相关的边数
	- 入度：有向图中指向节点的边的数量
	- 出度：有向图中由某节点发出的边数
5. 有向完全图、无向完全图
	- **有向完全图：n个顶点有n(n-1)条边**
	- **无向完全图：n个顶点有n(n-1)/2条边**
	
6. 路径和路径长度：相邻顶点的序偶构成的序列，路径长度指路径边的数量

7. 简单路径：**顶点不重复**出现的路径

8. 回路：路径中第一个顶点和最后一个顶点相同的路径

9. 联通、连通图和连通分量
	- 联通：Vi到Vj有路径
	- 连通图：任意两个顶点都联通
	- 连通分量：图中的**极大连通子图**（添加任一个顶点之后不连通）

10. 强连通图、强连通分量
	- 强连通图：任意两个顶点互有路径
	- 强连通分量：图中的**极大强连通子图**（添加任一个顶点之后不强连通）

11. 权和网：带权图

## 2、图的存储结构（算法题常考）

1. 邻接矩阵（顺序存储）

   > 稠密图常用，存储空间**只与顶点个数相关**
```c
typedef struct VNode {
    int no;
    char info;
}VNode;

typedef struct MGraph {
    float edges[MAXSIZE][MAXSIZE];
    int vexnum, edgenum;
    VNode vex[MAXSIZE];
}
```

2. 邻接表（链式存储）

   > 稀疏图常用，存储**与顶点个数和边数都有关**
```c
typedef struct ArcNode {
	int adjvex;
    int weight;
    struct ArcNode *nextarc;
}

typedef struct VNode {
    VertexType data;
    struct ArcNode *firstarc;
}VNode, AdjList[MAXSIZE];

typedef struct AdjGraph {
    struct AdjList adjList;
    int vexnum, arcnum;
	int kind;
} AdjGraph;
```



3. 邻接多重表：**无向图特有**的存储结构（相当于把无向图邻接表的边节点合成一个双向边节点）

4. 十字链表：**有向图特有**的存储结构（相当于邻接表+逆邻接表）

## 3、图的遍历（必考）
- 深度优先遍历

  ```c
  //递归实现
  void DFS(struct AGraph *G, int *visited, int v) {
      if (visited[v])
          return;
  	struct VNode vex = G->adjList[v];
      Visit(vex.data);
      visited[v] = 1;
      struct ArcNode *arc = vex.firstarc;
      while (arc) {
          DFS(G, visited, arc->adjvex);
          arc = arc->nextarc;
      }
  }
  void DFSTraverse(struct AGraph *G, int v) {
      int visited[maxSize] = {0};
      DFS(G, visited, v);
  }
  
  //非递归实现
  void DFSTraverseNR(AdjGraph *G, int v) {
      int visited[maxSize] = {0};
      InitStack(S);
      Push(S, v);
      int p;
      while (!StackEmpty(S)) {
          Pop(S, &p);
          struct VNode vex = G->adjList[p];
          Visit(vex->data);
          visited[p] = 1;
          struct ArcNode *arc = vex.firstarc;
          while (arc) {
              if (visited[arc->arjvex] == 0)
              	Push(S, arc->adjvex);
              arc = arc->nextarc;
          }
      }
  }
  ```

- 广度优先遍历

  ```c
  void BFSTraverse(struct AdjGraph *G, int v) {
      int visited[maxSize] = {0};
      InitQueue(Q);
      EnQueue(Q, v);
      int p;
      while (!QueueEmpty(Q)) {
          DeQueue(Q, &p);
          struct VNode *vex = G->adjList[p];
          Visit(vex->data);
          visited[p] = 1;
          struct ArcNode *arc = vex->firstarc;
          while(arc) {
              if (visited[arc->vex] == 0)
                  EnQueue(Q, arc->adjvex);
              arc = arc->nextarc;
          }
      }
  }
  ```

## 4、最小生成树（常考）
- **Prim**(可能考算法题)

  > 时间复杂度为 **O(n^2)**，适用于**稠密图**
  >
  > 要会画表，从起始点开始，在候选边中找最小代价边（套路题，做几道就会了）

```c
void MST_Prim(struct MGraph *G, int v0, int &sum) {
    int lowcost[maxSize], vset[maxSize];
    int v = v0;
    for (int i = 0; i < G->vexnum; i++) {
        lowcost[i] = G->edges[v][i];
        vset[i] = 0;
    }
    
    vset[v] = 1;
    sum = 0;
    for (int i = 0;i < G->vexnum - 1;i++) {
        int min = INF;
        int k;
        for ( int j = 0; j < G->vexnum; j++) {
            if (vset[j] == 0 && lowcost[j] < min) {
                min = lowcost[j];
                k = j;
            }
        }
        vset[k] = 1;
        v = k;
        sum += min;
        for (int j = 0; j < G->vexnum;j++) {
            if (G->edges[v][j] < lowcost[j] && vset[j] == 0)
                lowcost[j] = G->edges[v][j];
        }
    }
}
```

- Kruskal

  > 时间复杂度为**O(ElogE)**（和边的排序算法相关），适用于**稀疏图**
  >
  > 手工找最小生成树最好方法，用到**并查集**检查添加边后是否出现回路

## 5、最短路径（常考）
- **迪杰斯特拉**

  > 时间复杂度**O(n^2)**，计算**单源最短路径，不能带负权边**

  ```c
  //dist[]存放顶点v到其余顶点最短的路径长度，path[]存放v到各顶点的最短路径
  void Dijkstra(struct MGraph *G, int v, int dist[], int path[]) {
  	int vset[maxSize];
  	for (int i = 0; i < G->vexnum;i++) {
  		dist[i] = G->edges[v][i];
  		vset[i] = 0;
  		if (G->edges[v][i] < INF)
              path[i] = v;
          else
              path[i] = -1;
  	}
      vset[v] = 1;
      path[v] = -1;
      
      for (int i = 0; i < G->vexnum;i++) {
          int min = INF;
          int k;
          for (intj = 0; j < G->vexnum;j++) {
              if (vset[j] == 0 && dist[j] < min) {
                  k = j;
                  min = dist[j];
              }
          }
          vset[k] = 1;
          for (int j = 0; j < G->vexnum; j++) {
              if (vset[j] == 0 && dist[k] + G->edges[k][j] < dist[j]) {
                  dist[j] = dist[k] + g->edges[k][j];
                  path[j] = k;
              }
          }
      }
  }
  ```

- 弗洛依德算法

  > 时间复杂度**O(n^3)**，图中**不允许有负权环**

  ```c
  void Floyd(struct MGraph *G, int path[][]) {
  	int A[maxSize][maxSize];
      for (int i = 0; i < G->vexnum; i++) {
          for (int j = 0; j < g->vexnum; j++) {
              A[i][j] = g->edges[i][j];
              path[i][j] = -1;
          }
      }
      
      for (int k = 0; k < G->vexnum;k++) {
          for (int i = 0; i < G->vexnum; i++) {
              for (int j = 0; j < vexnum; j++) {
                  if (A[i][j] > A[i][k] + A[k][j]) {
                      A[i][j] = A[i][k] + A[k][j];
                      path[i][j] = k;
                  }
              }
          }
      }
  }
  ```

  

## 6、拓扑排序（常考，求关键路径的第一步）
- AOV网

  > 活动在顶点上的网
  >
  > **有向无环图**
  >
  > 定点表示活动，边无权值，边代表活动先后关系

- 拓扑排序

  > 1）找到入度为零的起始点入栈
  >
  > 2）弹出入度为零的起始点，将其邻接点的入度减一，如果邻接点入度变为0则压入栈中
  >
  > 3）所有点均访问到则拓扑排序成功
  ```C
  int topSort(struct AGraph *G) {
      int stack[maxSize];
      int top = -1, n = 0;
      int indegree[maxSize];
      for (int i = 0; i < G->vexnum; i++) {
          struct ArcNode *p = G->adjList[i].firstarc;
          while (p) {
              indegree[i] ++;
              p = p->nextarc;
          }
      }
      
      for (int i = 0; i < G->vexnum; i++) {
          if (indegree[i] == 0)
              stack[++top] = i;
      }
      
      while (top > -1) {
          int v = stack[top--];
          n++;
          struct VNode vex = G->adjList[v];
          Visit(vex->data);
          struct ArcNode *arc = vex.firstarc;
          while (arc) {
              if ((--indegree[arc->adjvex]) == 0)
                  stack[++top] = arc->adjvex;
              arc = arc->nextarc;
          }
      }
      return G->vexnum == n;
  }
  ```

## 7、关键路径（常考，画表）
- AOE网

  > 活动在边上的网
  >
  > **有向无环图**
  >
  > **顶点代表事件**，**边表示活动**，边有权值 ，边代表活动持续时间

- 关键路径

  > **源点**：入度为0的点
  >
  > **汇点**：出度为0的点
  >
  > 关键路径：从**源点到汇点**所有路径中的**最长路径**
  >
  > 1) 先进行拓扑排序
  >
  > 2) 按拓扑排列顺序，计算顶点最早发生时间(ve(k)=**max**{ve(j) + <j, k>}，j为k的前驱顶点，可能有多个)
  >
  > 3) 按逆拓扑排序顺序，计算顶点最迟发生时间(vl(k)=**min**{vl(j) - <k, j>}，j为k的后继顶点，可能有多个)
  >
  > 4) 计算边最早发生时间e（与发出该边的顶点的最早发生时间ve相同）
  >
  > 5) 计算边最迟发生时间l（以该活动结束的顶点最迟发生时间vl - 边的权值）
  >
  > 6) 整理数据成一张表，**e和l相等的边即为关键活动**，组成的从源点到汇点的**最长路径**即为关键路径


# 八、排序★★★★★

## 1、 排序概念和稳定性（概念，理解）

- 排序：将原本无序的序列重新排列成有序的序列

- **稳定性**：排序序列中有两个或两个以上相同的关键字时，排序前和排序后的相对位置不变则稳定，变化则不稳定

## 2、排序算法
1. 插入类
   - 直接插入排序
   
     > 最少比较次数：**n-1**
     >
     > 最多比较次数：**(n + 2) * (n - 1) / 2**（加上哨兵）
     >
     > 时间复杂度：**O(n^2)**
     >
     > 空间复杂度：**O(1)**
     >
     > **稳定**
   
   ```c
   //不带哨兵
   void InsertionSort(int data[], int n) {
       for (int i = 1; i < n; i++) {
           int e = data[i];
           int j = i;
           for (; j > 0 && data[j - 1] > e; j--) {
               data[j] = data[j - 1];
           }
           data[j] = e;
       }
   }
   
   
   //严薇敏书上的
   void InertSort(struct SqList &L) {
       for (i = 2; i <= L.length; i++) {
           if (LT(L.r[i].key, L.r[i - 1].key)) {
               L.r[0] = L.r[i];
               L.r[i] = L.r[i - 1];
               for (j = i - 2; LT(L.r[0], L.r[j]); j--) 
                   L.r[j + 1] = L.r[j];
               L.r[j + 1] = L.r[0];
           }
       }
   }
   ```
   
   - 折半插入排序
   
     > 相比直接插入排序，减少了比较次数
     >
     > 时间复杂度：**O(n^2)**
     >
     > 空间复杂度：**O(1)**
   ```c
   //严书上
   void BInsertSort(struct SqList &L) {
       for (i = 2; i < = L.length; i++) {
           L.r[0] = L.r[i];
           low = 1; high = i - 1;
           while (low < high) {
               m = (low + high) / 2;
               if (LT(L.r[0].key, L.r[m].key))
                   high = m - 1;
               else
                   low = m + 1;
           }
           for (j = i - 1;j >= high + 1;j-)
               L.r[j + 1] = L.r[j];
           L.r[high + 1] = L.r[0];
       }
   }
   ```
   - 希尔排序
   
     > 时间复杂度：**O(n^(3/2))**
     >
     > 空间复杂度：**O(1)**
     >
     > **不稳定**
   ```c
   //严书上,L.r[0]是暂存单元，不是哨兵
   void ShellInsert(struct SqList &L, int dk) {
       for (i = dk + 1; i < L.length; i++) {
           if (LT(L.r[i].key, L.r[i - dk])) {
               L.r[0] = L.r[i];
               for (j = i - dk; j > 0; j -= dk)
                   L.r[j + dk] = L.r[j];
               L.r[j + dk] = L.r[0];
           }
       }
   }
   
   void ShellSort(struct SqList &L, int dlta[], int t) {
       for (i = 0; i < t; i++) {
           ShellInsert(L, dlta[i]);
       }
   }
   ```
   
2. 交换类
   - 冒泡排序
     
     > 时间复杂度**O(n^2)**
     >
     > 空间复杂度：**O(1)**
     >
     > **稳定**
   
   ```c
   void swap(int data[], int i, int j) {
       int temp = data[i];
       data[i] = data[j];
       data[j] = temp;
   }
   
   void BubbleSort(int data[], int n) {
       bool change = false;
       for (int i = n - 1; i >= 0; i --) {
           change = false;
           for (int j = 0; j < i; j++) {
               if (data[j] > data[j + 1]) {
                   swap(data, j, j + 1);
                   change = true;
               }
           }
           if (!change)
               return;
       }
   }
   ```
   
   - 快速排序
   
     > 时间复杂度：**O(nlogn)**
     >
     > 空间复杂度：**O(nlogn)**
     >
     > **不稳定**
   
   ```c
   int Partition(int data[], int left, int right) {
       if (left >= right)
           return;
       int piv = data[left];
       int i = left, j = right;
       while (i < j) {
           while (i < j && data[j] >= piv) j--;
           data[i] = data[j];
           while (i < j && data[i] <= piv) i++;
           data[j] = data[i];
       }
       data[i] = piv;
   	
       return i;
   }
   
   void QSort(int data[], int low, int high) {
       if (low <= high)
           return;
       int piv = Partition(data, low, high);
       QSort(data, 0, piv - 1);
       QSort(data, piv + 1, high);
   }
   
   void QuickSort(int data[], int n) {
       QSort(data, 0, -1);
   }
   ```
   
3. 选择类
   - 简单选择排序
   
     > 时间复杂度：**O(n^2)**
     >
     > 空间复杂度：**O(1)**
     >
     > **不稳定**
   
   ```c
   void swap(int data[], int i, int j) {
       int temp = data[i];
       data[i] = data[j];
       data[j] = temp;
   }
   
   void SelectSort(int data[], int n) {
       for (int i = 0; i < n; i ++) {
           int min = i;
           for (int j = i; j < n; j++) {
               if (data[j] < data[min]) {
                   min = j;
               }
           }
           swap(data, i, min);
       }
   }
   ```
   
   - 堆排序（去年刚考过算法题）
   
     > 时间复杂度：**O(nlogn)**
     >
     > 空间复杂度：**O(1)**
     >
     > **不稳定**
   
     ```c
     void swap(int data[], int a, int b) {
         int temp = data[a];
         data[a] = data[b];
         data[b] = temp;
     }
     
     void siftDown(int data[], int i, int end) {
         while (2 * i <= end) {
             int child = 2 * i;
             if (child + 1 <= end && data[child + 1] > data[child])
                 child ++;
     
             if (data[child] < data[i]) {
             	break;
             }
             swap(data, i, child);
             i = child;
         }
     }
     
     void HeapSort(int data[], int n) {
         int i = n / 2;
     
         for ( ;i > 0; i--) {
             siftDown(data, i, n);
         }
     
         for (i = n; i > 1; i--) {
             swap(data, 1, i);
             siftDown(data, 1, n - i);
         }
     }
     ```
   
     
   
4. 二路归并排序（几乎没出过算法题）

   > 时间复杂度：**O(nlogn)**
   >
   > 空间复杂度：**O(n)**

   ```c
   void Merge(int data[], int left, int mid, int right) {
   	//辅助空间
       int temp[right - left + 1];
       int n = right - left + 1;
   
       int i = left, j = mid + 1;
       
       //归并操作，将两个有序序列归并到辅助空间中
       int k = 0;
       while (k < n) {
           if (i > mid)
               temp[k] = data[j++];
           else if (j > right)
               temp[k] = data[i++];
           else if (data[i] < data[j])
               temp[k] = data[i++];
           else
               temp[k] = data[j++];
           k++;
       }
   
       for (i = left; i <= right; i++) {
           data[i] = temp[i - left];
       }
   }
   
   void MergeSort(int data[], int left, int right) {
       if (left >= right)
           return;
   
       int mid = left + (right - left) / 2;
       MergeSort(data, left, mid);
       MergeSort(data, mid + 1, right);
       Merge(data, left, mid, right);
   }
   
   void MergeSort(int data[], int n) {
       MergeSort(data, 0, n - 1);
   }
   ```

   

5. 基数排序

   > 不需要比较关键字
   >
   > 时间复杂度：**O(d * (n + rd))**
   >
   > 空间复杂度：**O(r* d)**
## 4、外部排序（期末考试有，真题没见过，需要看一看）
## 5、时间复杂度、空间复杂度和稳定性总结（必考）

| 排序方法 | 平均时间复杂度  | 最坏时间复杂度  | 最好时间复杂度  | 空间复杂度 | 稳定性 |
| -------- | --------------- | --------------- | --------------- | ---------- | ------ |
| 插入选择 | O(n^2)          | O(n^2)          | O(n)            | O(1)       | 稳定   |
| 希尔排序 | O(n^1.3)        | O(n^2)          | O(n)            | O(1)       | 不稳定 |
| 选择排序 | O(n^2)          | O(n^2)          | O(n^2)          | O(1)       | 不稳定 |
| 堆排序   | O(nlogn)        | O(nlogn)        | O(nlogn)        | O(1)       | 不稳定 |
| 冒泡排序 | O(n^2)          | O(n^2)          | O(n)            | O(1)       | 稳定   |
| 快速排序 | O(nlogn)        | O(n^2)          | O(nlogn)        | O(nlogn)   | 不稳定 |
| 归并排序 | O(nlogn)        | O(nlogn)        | O(nlogn)        | O(n)       | 稳定   |
| 基数排序 | O(d * (n + rd)) | O(d * (n + rd)) | O(d * (n + rd)) | O(rd)      | 稳定   |





# 九、查找★★★★★

## 1、 概念、顺序查找法和折半查找法

1. 查找

   > 给定一个值K，在n个记录的表中找出关键字k的记录

2. 平均查找长度（平均比较次数）ASL

   > 衡量查找算法优劣的标准
   >
   > **ASL1**:查找成功的平均查找长度
   >
   > **ASL2**:查找失败的平均查找长度

3. 顺序查找

   > ASL1 = (n + 1) / 2
   >
   > ASL2 = n

4. 折半查找

   > 画出折半查找的判定树，计算ASL

   ```c
   int BSearch(int data[], int n, int k) {
   	int low = 0, high = n - 1, mid;
       while (low <= high) {
           mid = low + (low + high) / 2;
           if (data[mid] == k)
               return mid;
           else if (data[mid] < k)
               low = mid + 1;
           else
               high = mid - 1;
       }
       return -1;
   }
   ```
   
5. 分块查找

   > 先二分查找索引块
   >
   > 再顺序查找块内元素

## 2、二叉排序树和二叉平衡树（必考，平衡化旋转操作）

1. 二叉排序树

   > 二叉树，且任一结点或是空树，或满足
   >
   > 左子树所有非空结点键值**小于**根节点键值
   >
   > 右子树所有非空结点键值**大于**根节点键值

2. 平衡二叉树

   > 平衡二叉树，且任一结点左子树高度与右子树高度差**绝对值不超过1**
   >
   > **四种调整方式(重点)**：LL, RR, LR, RL

## 3、B-树和B+树（理解，常考）

1. M阶B-树
    - **根节点至少有两个分支，1个关键字**
    
    - **非根非叶节点最少有┌m / 2┐个分支，┌m / 2┐ - 1 个关键字**
    
    - **有n个分支的节点有n - 1个关键字，均不相同，按递增排列**
    
    - **叶节点在同一层，为空指针，表示查找失败**
    
	> **支持随机索引，不支持顺序索引**
    > 
    > **注：插入删除时，节点分裂，合并要会画图**（考过）

2. M阶B+树
	- **有n个分支的节点有n个关键字**
	- **根节点关键字个数：2 <= n <= m**
	- **非根节点外，其他节点关键字个数：┌m / 2┐ <= n <= m**
	- **叶子节点包含信息，分支节点只起到索引作用，所有叶子节点连成一个链表**

## 4、散列表（必考）
1. 散列表
	> 根据关键字和指定HASH函数计算出在表中的位置
	>
	> **AVL与装填因子直接相关**（关键字个数和表长度的比值）
	>
	> **AVL计算(重点)**
2. 建立方法和解决冲突的方法
	- 建立方法
        - 直接定址法
        	
        	> H(key) = a * key + b
        - 数字分析法
        - 平方取中法
        - 除数留余法

        	> H(key) = key mod p

	- 解决冲突的方法
		- 开放定址法
			
   > +1, +2, +3, ......
			
		- 平方探查法
     	
		  > +1^2, -1^2, +2^2, -2^2, ......
   	  
   	- 链地址法
   