# Algorithm Design Mental Model v0.1  
（算法设计通用心智模型）

---

## 0. 核心定义

算法的本质不是代码，而是：

在状态空间中寻找满足目标的路径


完整路径：

Problem
→ Solution Space
→ State Space
→ Search Strategy
→ Optimization
→ Algorithm
→ Program


---

# 1. Problem（问题）

任何算法从“问题定义”开始。

问题必须被明确为：

- 输入是什么
- 输出是什么
- 约束是什么
- 目标是什么

### 问题类型

| 类型 | 示例 |
|---|---|
| 判定问题 | 是否存在路径 |
| 构造问题 | 给出解 |
| 优化问题 | 最短路径 |
| 计数问题 | 方案数 |
| 搜索问题 | 找满足条件的元素 |

---

# 2. Solution Space（解空间）

解空间 = 所有可能答案的集合。

例如：

| 问题 | 解空间 |
|---|---|
| 排序 | 所有排列 |
| 组合 | 所有子集 |
| 路径 | 所有可能路径 |
| 参数优化 | 所有参数组合 |

解空间通常：

- 极大
- 不可直接遍历

因此必须转化为可搜索结构。

---

# 3. State Space（状态空间）

关键步骤：

> 把“解”拆成“生成解的过程”

状态 = 部分解（partial solution）

### 状态设计方式

| 解问题 | 状态表示 |
|---|---|
| 排列 | prefix |
| 子集 | 已选元素 |
| 路径 | 当前节点 |
| 动态规划 | 子问题 |
| 图问题 | (node, visited) |
| 搜索问题 | 搜索节点 |

本质关系：

解空间 = 终点集合
状态空间 = 通向终点的图


---

# 4. Search Strategy（搜索策略）

在状态空间中移动。

## 基本搜索方法

### DFS

- 深度优先探索
- 常用于回溯与组合问题

### BFS

- 层级扩展
- 常用于最短路径

### Backtracking

- 带剪枝的 DFS

### Dynamic Programming

- 状态复用
- 子问题重叠

### Greedy

- 局部最优策略

### Heuristic / A*

- 启发式搜索
- 预测最优路径

---

# 5. Optimization（优化）

算法设计的核心能力。

优化方向：

## 5.1 减少状态数量

- 剪枝
- memo
- 状态压缩

## 5.2 减少搜索路径

- greedy
- branch and bound

## 5.3 降低单步成本

- 数据结构优化
- 预处理
- 数学变换

## 5.4 复杂度控制

- 时间复杂度
- 空间复杂度
- 平均 vs 最坏

---

# 6. 数据结构的角色

状态空间 = 数据结构
搜索路径 = 算法


### 常见映射

| 问题 | 数据结构 |
|---|---|
| 顺序问题 | array / list |
| 查找问题 | hash |
| 层级问题 | tree |
| 关系问题 | graph |
| 区间问题 | segment tree |
| 优先问题 | heap |
| 组合问题 | recursion tree |

一句话总结：

> 数据结构决定算法上限。

---

# 7. 算法的统一形式

所有算法本质：

Graph traversal + state representation


包括：

- DFS
- BFS
- DP
- A*
- 强化学习

甚至：

- 机器学习
- 推荐系统
- 控制系统

本质都是：

在状态空间中找最优路径


---

# 8. 示例：Three Sum

### Problem

寻找三数之和为 0 的组合。

### Solution space

所有三元组组合：

C(n,3)


### State space

(i, j)


第三个数由双指针推导。

### Search

- 排序
- 固定一个元素
- 双指针扫描

### Optimization

- 排序
- 去重
- 双指针降低复杂度

---

# 9. 示例：动态规划问题

### Problem

最短路径 / 最优值问题

### State

dp[i]


### Search

状态转移：

dp[i] = f(dp[i-1], dp[i-2], ...)


### Optimization

- memo
- 滚动数组
- 状态压缩

---

# 10. 算法设计最难的一步

不是搜索。

而是：

state representation


状态建错会导致：

- DP 无法建模
- 剪枝失效
- 复杂度爆炸

高手与初学者的差距就在这里。

---

# 11. 算法层级结构（认知进阶）

Level 0 — 代码技巧
Level 1 — 算法模板（DFS / DP / Greedy）
Level 2 — 状态空间设计
Level 3 — 解空间建模
Level 4 — 问题抽象能力（数学建模）
Level 5 — 系统级建模（AI / 控制 / 仿真）


---

# 12. 与 AI / 强化学习 的统一

强化学习模型：

state
action
reward
policy


本质：

状态空间 + 路径优化


AI 并不是全新范式，而是：

> 更复杂的搜索 + 统计优化

---

# 13. 核心结论

> 算法设计 = 如何把“解空间”转化为“可搜索的状态空间”

不是代码技巧问题，而是：

空间建模能力


---

# 14. v0.2 演化方向

下一版将加入：

## A. 解空间分类学

- 离散空间
- 连续空间
- 组合空间
- 概率空间

## B. 状态空间设计模式库

- prefix
- sliding window
- graph state
- DP state

## C. 搜索策略选择图谱

- DFS vs BFS vs DP vs A*

## D. 剪枝理论

- admissible heuristic
- dominance pruning

## E. 从算法 → AI → 系统设计统一建模

Optimization
Planning
Learning
Control


---

# 最终总结

算法不是技巧
算法是“空间 + 路径”的设计


核心能力：

> 状态空间建模能力