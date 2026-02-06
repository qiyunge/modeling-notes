# State Representation Pattern Library v0.1
（状态空间设计模式库）

> 核心原则：
> 算法能力 = 状态建模能力

所有算法问题，本质都是：



在状态空间中寻找满足目标的路径


---

# 1. 状态空间设计的四个原型

所有算法状态，本质只有四类。

## 1.1 Prefix 型（构造型）

状态表示：



state = 已构造的一部分解


典型问题：

- 排列
- 组合
- 子集
- backtracking
- N 皇后

例：



path = [1,3,5]


本质：

> 从空解逐步扩展

---

## 1.2 Position 型（指针型）

状态表示：



state = 当前处理的位置


典型问题：

- 双指针
- 滑动窗口
- 字符串处理
- 数组扫描

例：



left = 3
right = 10


本质：

> 在序列上移动

---

## 1.3 Graph 型（关系型）

状态表示：



state = 当前节点 + 已访问


典型问题：

- 图搜索
- BFS / DFS
- 最短路径
- A*

例：



(node, visited)


本质：

> 在关系结构中移动

---

## 1.4 DP 型（子问题型）

状态表示：



state = 子问题


典型问题：

- 背包
- 最长子序列
- 编辑距离
- 最优路径

例：



dp[i][j]


本质：

> 解被拆成可复用子解

---

# 2. LeetCode 题目的本质

所有题本质是这些模式的组合。

| 模式 | 代表算法 |
|---|---|
| Prefix | 回溯 |
| Position | 双指针 / 滑动窗口 |
| Graph | BFS / DFS |
| DP | 动态规划 |

复杂题：



= 多模式组合


例如：

- DP + Graph
- Sliding window + Hash
- Backtracking + Pruning

---

# 3. 状态设计流程（核心方法）

遇到问题，不要先想算法。

## Step 1 — 解是什么？

输出类型：

- 数值
- 集合
- 路径
- 序列
- 结构

---

## Step 2 — 解是如何生成的？

得到：



state


---

## Step 3 — state 需要记录哪些信息？

常见字段：

| 信息 | 用途 |
|---|---|
| index | 扫描位置 |
| visited | 防重复 |
| prefix | 构造解 |
| sum | 约束 |
| count | 统计 |
| dp value | 子解 |

---

## Step 4 — state 如何转移？



state → next state


算法在这里诞生。

---

# 4. 状态设计模板（面试必备）

## 4.1 双指针模板



state = (left, right)

while left < right:
if condition:
left += 1
else:
right -= 1


适用：

- 排序数组
- two sum
- 容器盛水

---

## 4.2 滑动窗口模板



state = window[left:right]

while right < n:
expand window
while invalid:
shrink window


维护：

- sum
- count
- hashmap

适用：

- substring
- frequency
- 最长子串

---

## 4.3 回溯模板



def dfs(path):
if 满足条件:
记录解
return

for choice in choices:
    做选择
    dfs(path)
    撤销选择


适用：

- 组合
- 排列
- 子集

---

## 4.4 BFS 模板



queue = [start]
visited = set()

while queue:
node = queue.pop(0)
for neighbor in node:
if not visited:
queue.append(neighbor)


适用：

- 最短路径
- 层级遍历

---

## 4.5 DP 模板



dp[i][j] = 状态定义

for 状态顺序:
dp[i][j] = 状态转移方程


适用：

- 最值问题
- 可复用子问题

---

# 5. 高手 vs 初学者

普通人：

> 这题用什么算法？

高手：



解空间是什么
↓
状态是什么
↓
状态如何转移
↓
才选算法


---

# 6. 状态最小化（核心技能）

state 记录太多：



→ 状态爆炸


state 记录太少：



→ 无法判断


这是算法设计最难的地方。

---

# 7. 状态压缩

当 state 太大：

使用：

- bitmask
- rolling array
- 编码

例：



visited → bitmask


---

# 8. 算法统一视角



所有算法 = 状态图上的路径搜索


例如：

- DFS = 深度遍历状态图
- BFS = 最短路径
- DP = DAG 上的路径优化
- Greedy = 单路径启发
- RL = 动态策略搜索

---

# 9. 与 AI 的统一

强化学习：



state
action
reward
policy


等价：



状态空间 + 搜索路径优化


---

# 10. 核心结论

> 算法设计 = 把“解空间”转化为“可搜索的状态空间”

不是代码问题。

是：



空间建模能力


---

# 11. v0.2 演化方向

下一版本将加入：

## A. 解空间分类学

- 离散
- 连续
- 组合
- 概率

## B. 状态设计错误学

- state 过多
- state 缺信息
- 转移错误
- 剪枝失效

## C. 搜索策略选择图

- DFS vs BFS vs DP vs Greedy vs A*

## D. 剪枝理论

- admissible heuristic
- dominance pruning

## E. 算法 → AI → 决策系统统一



Optimization
Planning
Learning
Control


---

# 12. 一句话总结



算法不是技巧
算法是“空间 + 路径”的设计


状态空间建模能力：

= 算法水平上限