# Case Study – Maximum Flow through the Algorithm Paradigm Tree
# 案例：最大流问题的算法范式演化全过程

> 目标：  
> 用一个经典问题，完整走一遍  
> **DP ❌ → Greedy ❌ → 结构分析 → 图模型 → Residual Network ✅**

---

## 0. 问题定义（起点）

给定一个有向网络：
- 边有容量
- 有源点 s 和汇点 t
- 每条边流量 ≤ 容量
- 中间节点满足流守恒

目标：
> 最大化从 s 到 t 的总流量

---

## 1. 第一反应：动态规划（DP）❌

### 尝试思路
- 把问题拆成子问题：
  - 从 s 到某个中间点 v 的最大流
  - 再从 v 到 t
- 或按“路径数量 / 节点子集”定义状态

### 为什么失败（关键）

#### 1️⃣ 强全局耦合
- 一条路径用了容量
- 会直接影响 **所有其他路径的可行性**

#### 2️⃣ 没有自然的子问题边界
- “前一段流”与“后一段流”无法独立
- 状态必须记住整个剩余网络

#### 3️⃣ 状态爆炸
- DP 状态 ≈ 所有可能的容量分布
- 不可行

📌 结论：
> 最大流 **不具备自然的 DP 结构**

---

## 2. 回退尝试：贪心算法（Greedy as Probe）❌

### 最自然的贪心想法

#### Greedy v1
> 每次找一条 s → t 的路径，  
> 尽量多送流（瓶颈容量）

### 表面上看起来合理
- 每一步都“送最多”
- 似乎在逼近最优

### 但它会失败（核心）

#### 失败现象
- 早期选了一条“看起来不错”的路径
- 却：
  - 占用了关键边
  - 阻断了后续更优组合

#### 关键洞察
> 问题不是“送得不够多”，  
> 而是 **早期选择不可撤销**

📌 这是一个**极其重要的信号**：
- Greedy 失败不是随机的
- 失败来自：**需要回退 / 修正**

---

## 3. 失败分析 → 结构洞察（关键跃迁）

### Greedy 暴露出的结构问题

#### 1️⃣ 决策需要可撤销
- 之前送的流，未来可能要“收回”

#### 2️⃣ 网络不是静态的
- 每送一单位流
- 网络结构就发生变化

#### 3️⃣ 需要表示“反向可能性”
- 如果我后悔了
- 能不能把流“退回去”？

📌 这一步不是算法，而是 **建模升级**

---

## 4. 建模升级：Residual Network（残量网络）✅

### 核心思想（非常重要）

> **不要只看“还能送多少”  
> 还要看“能不能撤回”**

---

### 残量网络的构造

对每条边 (u → v, capacity = c, flow = f)：

- 正向边：  
  - 剩余容量 = c − f
- 反向边：  
  - 容量 = f（表示“可撤回”）

📌 反向边不是物理边  
📌 它是“修正自由度”的数学表达

---

## 5. 新问题表述（关键转化）

原问题：
> 最大化流量

被转化为：
> 在残量网络中，  
> **不断寻找从 s 到 t 的增广路径**

每次：
1. 找一条 s → t 的路径
2. 取瓶颈容量 Δ
3. 沿路径增广（正向加，反向减）
4. 更新残量网络

---

## 6. 为什么这个结构能保证正确性？

### 不变量（Invariant）

- 任意时刻：
  - 当前流是可行流
  - 残量网络准确描述“所有可能的修正”

### 终止条件
- 当残量网络中 **不存在 s → t 路径**
- ⇒ 当前流已无法再改进

---

## 7. 理论闭环：Max-Flow Min-Cut

### 关键定理
> 当不存在增广路径时，  
> 当前流 = 某个 s–t 割的容量

也就是说：
- 上界 = 下界
- 全局最优已达成

📌 这是结构性最优，不是枚举得到的

---

## 8. 算法范式回顾（非常重要）

### 我们实际走过的路径

| 阶段 | 结果 | 得到的信息 |
|----|----|----|
| DP | ❌ | 问题全局耦合 |
| Greedy | ❌ | 需要回退机制 |
| 失败分析 | ✅ | 结构暴露 |
| 图模型 | ✅ | 网络流 |
| 残量网络 | ✅ | 修正自由度 |
| 增广路径 | ✅ | 算法成立 |

---

## 9. 方法论总结（精华）

> **最大流算法不是“设计出来的”  
> 而是“被 Greedy 的失败逼出来的”**

真正的创新点不是：
- Ford–Fulkerson 的实现细节

而是：
- **Residual Network 这一建模升级**

---

## 10. 可迁移的通用经验

### 当你遇到类似问题时，问自己：

1. 决策是否需要可撤销？
2. 是否存在“反向自由度”？
3. 问题是否本质是：
   - 资源流动
   - 全局约束
   - 结构不变量？

👉 如果是：
→ 考虑 **Flow / Matching / Cut**

---

## 一句话终极总结

> **DP 失败告诉你“问题不局部”  
> Greedy 失败告诉你“问题不单向”  
> 残量网络告诉你“问题是结构性的”**

# State Taxonomy v0.1 — Data Structure Perspective
（状态分类学｜数据结构视角）

属于：CMS（Computational Modeling System）
层级：L2 State Representation

目标：

建立最底层能力：

看到问题 → 先识别“状态承载结构”


而不是：

看到问题 → 想算法


---

# 0. 核心思想

state 不是抽象概念。

state 一定“寄生”在某种结构上：

| state 的宿主 | 计算结构 |
|---|---|
| array | sequential state |
| string | ordered state |
| tree | hierarchical state |
| graph | relational state |
| set/subset | combinatorial state |
| grid | spatial state |
| heap | priority state |

算法其实是：

在结构上的状态移动方式


---

# 1. Array State（顺序状态）

最基础状态结构。

state 表现：

index
pointer
window
prefix


---

## 1.1 常见问题类型

| 问题 | 状态 |
|---|---|
| 扫描 | i |
| pair | (l, r) |
| prefix sum | prefix[i] |
| sliding window | (l, r, stats) |

---

## 1.2 对应算法族

| state 类型 | 算法 |
|---|---|
| index 单调 | linear scan |
| pair 单调 | two pointers |
| window | sliding window |
| prefix 可复用 | prefix sum |
| 局部最优 | greedy |

---

## 1.3 本质

array = 线性状态空间

state(i) → state(i+1)


---

# 2. Tree State（层级状态）

树的本质：

parent → children


state 表现：

node
subtree
depth
path


---

## 2.1 常见问题

| 类型 | 例 |
|---|---|
| 遍历 | inorder/preorder |
| 深度 | height |
| 路径 | root→leaf |
| 子结构 | subtree |

---

## 2.2 算法族

| state | 算法 |
|---|---|
| node | DFS |
| level | BFS |
| subtree | DP on tree |
| ancestor | LCA |

---

## 2.3 本质

tree = 分支状态空间

state(node)
→ children states


---

# 3. Graph State（关系状态）

图表示：

nodes + edges


state 表现：

node
(node, visited)
(node, cost)


---

## 3.1 常见问题

| 类型 | 算法 |
|---|---|
| reachability | BFS / DFS |
| shortest path | Dijkstra |
| connectivity | union-find |
| cycle | DFS |

---

## 3.2 状态结构

graph traversal = state transitions


---

# 4. Grid State（空间状态）

二维 / 三维空间。

state：

(x, y)
(x, y, direction)


---

## 4.1 常见问题

- flood fill
- shortest path
- islands
- BFS on grid

---

## 4.2 本质

grid = 特殊 graph

node = cell
edge = adjacency


---

# 5. Set / Subset State（组合状态）

状态表示：

subset
visited
bitmask


---

## 5.1 问题类型

| 类型 | 算法 |
|---|---|
| 全组合 | backtracking |
| 状态压缩 | bitmask DP |
| 子集最优 | subset DP |

---

## 5.2 本质

subset space = 指数状态空间

---

# 6. Heap State（优先级状态）

state：

top element
priority ordering


---

## 6.1 问题类型

- top k
- streaming
- scheduling
- greedy

---

# 7. Interval State（区间状态）

state：

[l, r]


---

## 7.1 算法

- interval DP
- sweep line
- segment tree

---

# 8. 数据结构视角的统一图

Array → Sequential state
Tree → Hierarchical state
Graph → Relational state
Grid → Spatial state
Subset → Combinatorial state
Heap → Priority state
Interval → Range state


---

# 9. 关键能力：识别“state 的宿主”

看到题第一步不是：

> 用 BFS 还是 DP？

而是：

state 承载在什么结构上？


这是算法选择的源头。

---

# 10. 数据结构 → 算法映射（核心速查）

| 结构 | 状态 | 算法 |
|---|---|---|
| array | index | scan / two pointers |
| array | window | sliding window |
| array | prefix | prefix sum |
| tree | node | DFS |
| tree | subtree | DP |
| graph | node | BFS |
| graph | weighted | Dijkstra |
| subset | bitmask | DP |
| grid | cell | BFS |
| heap | priority | greedy |

---

# 11. CMS 中的位置

L2 State representation


决定：

- transition 结构
- 算法族
- complexity 上限

---

# 12. 下一步（核心引擎）

进入：

# State Taxonomy v0.2 — Information Structure Perspective

从：

数据结构

升级到：

信息结构


分类：

- positional state
- resource state
- constraint state
- belief state
- probabilistic state

这一步完成后：

你会从“算法思维”

直接进入：

> AI / decision system 思维

---

# 最终总结

算法不是从算法开始
算法从 state 的宿主开始


结构决定状态。

状态决定算法。
下一步我们要跨过一个非常关键的门槛：

从“数据结构上的 state”

升级到：

信息结构上的 state（真正 AI 层）
这一步是：

algorithm → modeling

modeling → intelligence

的分界线。