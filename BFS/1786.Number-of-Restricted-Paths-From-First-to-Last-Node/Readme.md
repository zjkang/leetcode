### 1786.Number-of-Restricted-Paths-From-First-to-Last-Node

题意描述：我们认为节点n是海平面，把distanceToLastNode(x)理解为节点x到节点n的海拔高度。我们需要找一条从节点1到节点n的路径，其中依次经过的每个点的“海拔”都是递减的。问这样的路径有多少条。

首先，这是一个single source, non-negative weight的图论问题，我们会用Dijkstra算法很容易地计算出每个节点距离节点n的最短路径距离，也就是“海拔”。

然后我们从节点1开始，用DFS来统计到达节点n的路径数目。注意，我们每次从当前节点a往后进行分支搜索的时候，根据题目要求，我们只会选择海拔相对a更低的节点递归下去，而不是选择所有的相邻节点。另外，考虑到图的结构很可能错综复杂，所以记忆化是必须的。

另外想提的一点是，DFS的过程中我们并不需要使用visited来去重。这是因为我们在递归的过程中永远遵循“水往低处流”的规则，所以不可能会在DFS的过程中遇到任何已经访问过的节点。
