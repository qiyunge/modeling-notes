面试向 · 20 个必杀算法结构清单

（LeetCode Cookbook × Algorithm Design 的交汇点）

我不是按「题型」分，而是按**“结构可判定性”分——这正好是你能在面试中说得出口、站得住**的那种解释。

I. 单调性与可判定性（Binary / Two Pointers / Sliding Window）
1️⃣ 二分搜索（Binary Search）

结构条件

判定函数 f(x) 是单调的（T → F 或 F → T）

模板信号

“最小/最大满足条件的 x”

“第一个/最后一个…”

一句话解释（面试用）

我把问题转成一个单调判定函数，在解空间上做二分。

2️⃣ 双指针（Two Pointers）

结构条件

序列有顺序性

移动一侧不会破坏另一侧的最优性

模板信号

有序数组

和/距离/覆盖区间

一句话解释

两个指针分别维护左右边界，整体复杂度从 O(n²) 降为 O(n)。

3️⃣ 滑动窗口（Sliding Window）

结构条件

连续子区间

窗口内状态可增量维护

模板信号

substring / subarray

“最长/最短满足条件”

一句话解释

用窗口维护区间状态，右扩左缩保证线性复杂度。

II. 栈与局部约束结构
4️⃣ 单调栈（Monotonic Stack）

结构条件

需要“最近的更大/更小”

局部顺序约束

模板信号

next greater

histogram

temperature

一句话解释

栈中保持单调性，用来快速定位最近的违约元素。

5️⃣ 栈模拟递归 / 表达式

结构条件

隐式递归 / 嵌套结构

模板信号

括号

DFS 转迭代

表达式求值

一句话解释

栈显式维护递归调用状态。

III. 哈希 × 频率 × 状态压缩
6️⃣ 哈希表（Hash Map）

结构条件

快速查找

频率 / 映射关系

模板信号

two sum

counting

prefix sum

一句话解释

用哈希表换时间，降低查找复杂度。

7️⃣ 前缀和（Prefix Sum）

结构条件

区间查询

可减性

模板信号

subarray sum

区间和

一句话解释

把区间问题转成两个前缀的差。

IV. 动态规划（DP）——这是面试里最重要的一类
8️⃣ 一维 DP

结构条件

最优子结构

状态可线性递推

模板信号

max subarray

climb stairs

一句话解释

当前最优解由前一个状态决定。

9️⃣ 二维 DP

结构条件

状态 = (i, j)

局部决策影响全局

模板信号

LCS

edit distance

一句话解释

用二维状态表示子问题之间的转移关系。

🔟 背包问题（Knapsack）

结构条件

选择 / 不选择

资源受限

模板信号

capacity

weight / value

一句话解释

对每个元素做选择决策，状态表示当前资源占用。

1️⃣1️⃣ 区间 DP

结构条件

区间分治

最优合并顺序

模板信号

burst balloons

matrix chain

一句话解释

枚举最后一次合并点，划分子区间。

V. 图论（面试常考，但要克制）
1️⃣2️⃣ BFS / DFS

结构条件

可达性

状态图

模板信号

maze

connected components

一句话解释

把问题建成图，搜索可达状态。

1️⃣3️⃣ 拓扑排序

结构条件

有向无环图（DAG）

依赖关系

模板信号

course schedule

dependency

一句话解释

在 DAG 上按依赖顺序线性化节点。

1️⃣4️⃣ 最短路径（Dijkstra）

结构条件

非负权

贪心可行

模板信号

weighted graph

shortest path

一句话解释

每一步选择当前最小未确定距离的节点。

VI. 贪心算法（最容易翻车，但面试官爱）
1️⃣5️⃣ 贪心（Greedy）

结构条件

局部最优 ⇒ 全局最优

模板信号

interval scheduling

activity selection

一句话解释

通过交换论证，局部最优选择是安全的。

（⚠️ 面试里不要求你完整证明，但要敢说“交换论证”）

VII. 分治与选择
1️⃣6️⃣ 分治（Divide & Conquer）

结构条件

子问题独立

合并可行

模板信号

merge sort

quick sort

一句话解释

拆成规模更小的同类问题，再合并结果。

1️⃣7️⃣ 快速选择（Quickselect）

结构条件

排名问题

不需要全排序

模板信号

kth largest

一句话解释

利用 partition，把期望复杂度降到 O(n)。

VIII. 并查集与区间结构
1️⃣8️⃣ 并查集（Union-Find）

结构条件

动态连通性

合并与查询

模板信号

islands

components

一句话解释

用路径压缩和按秩合并维护集合关系。

1️⃣9️⃣ 堆（Heap / Priority Queue）

结构条件

动态最值

模板信号

top-k

streaming

一句话解释

用堆维护当前最优候选集合。

IX. 进阶（可选，但能拉开差距）
2️⃣0️⃣ 位运算 / 状态压缩

结构条件

状态数小

子集枚举

模板信号

subset

bitmask dp

一句话解释

用二进制表示状态，压缩搜索空间。

你现在该怎么用这份清单（非常关键）
面试训练时，你只做三件事：

做题时：
👉 先判断「属于哪一个结构编号」

写完代码后：
👉 用一句话给自己复述结构解释

面试中：
👉 只说“结构判断 + 算法选择”，不要展开哲学