# Algorithm Mapping Strategies (Reference)

> This note is a reference scaffold, not a learning summary.
> It is used to analyze, compare, and design algorithms.

---

## Core Question

Given a fixed mathematical model and computational model,
how can the same problem be mapped into different executable algorithms?

---

## The 8 Mapping Dimensions

### 1. Structure Exploitation
- What mathematical structures are trusted?
- What is explicitly *not* trusted?

Typical signals:
- monotonicity
- optimal substructure
- symmetry

---

### 2. State Representation
- What is a state?
- Explicit vs implicit?
- Granularity?

---

### 3. Inference Ordering
- Expansion order?
- Global vs local priority?
- Deterministic vs adaptive?

---

### 4. Decision Reversibility
- Can decisions be rolled back?
- Is backtracking allowed?

---

### 5. Invariant Enforcement
- What must always hold?
- Structural vs explicit checking?

---

### 6. Failure Semantics
- What does failure mean?
- How is it exposed?

---

### 7. Correctness Commitment
- Optimal / feasible / approximate?
- Conditional vs unconditional?

---

### 8. Resource Trade-off
- Time vs space?
- Offline vs online?

---

## Compression View

These 8 dimensions can be compressed into 3 meta-choices:
- Structure Trust
- State Externalization
- Error Commitment

---

## Usage Checklist

When analyzing or designing an algorithm:
- Which dimensions are fixed by the problem?
- Which dimensions are design choices?
- Which choices are reversible?

---

## Notes

This document should be updated only when a *new mapping dimension* is discovered.
Do not expand it with examples unless necessary.

一、先确认你的判断（是对的，而且很关键）

你说：

资源使用方式，只是算法选择的其中一种策略
我们还可以根据数学结构的映射方式，采用不同算法
还有其他选择策略方式

这是完全正确的，而且可以正式表述为：

资源使用（时间/空间）只是“映射策略”的一个投影维度，
而不是算法差异的根源。

算法差异的根源在于：
👉 你如何把数学结构映射为可执行推理过程。

二、把“算法选择”提升为“映射策略空间”

现在我们可以给出一个完整、可操作的分类：

算法 = 数学结构 → 计算机模型 的一组映射决策的组合

资源使用，只是其中一维。

下面是完整的 8 个核心映射维度。

三、算法的 8 种核心“选择策略维度”
1️⃣ 结构利用策略（Structure Exploitation）

（最根本的一维）

利用哪些数学结构？

单调性？

最优子结构？

对称性？

凸性？

📌 例子：

Dijkstra 比 Bellman–Ford 多用“非负性”

A* 多用“可估计未来”

👉 这是算法分支产生的根源

2️⃣ 状态表示策略（State Representation）

（你前面已经完全抓住了）

状态是什么？

节点？

路径？

集合？

状态是显式还是隐式？

📌 例子：

DP：显式状态表

搜索：隐式生成

👉 不同表示 = 不同算法形态

3️⃣ 推理顺序策略（Inference Ordering）

先算谁？

是否全局排序？

是否允许回溯？

📌 例子：

DFS / BFS / Best-first

Dijkstra / A*

👉 顺序本身就是算法

4️⃣ 决策可逆性策略（Reversibility）

决策是否可回滚？

一旦选了，能不能改？

📌 例子：

贪心：不可逆

DP：可逆（通过状态）

搜索：完全可逆

👉 这直接决定：

是否需要保存历史

是否能剪枝

5️⃣ 不变量维护策略（Invariant Enforcement）

不变量如何被维护？

显式检查？

隐式保证？

结构性保证？

📌 例子：

Dijkstra：结构性保证最短

回溯：显式检查约束

👉 算法 = 不变量落实方式

6️⃣ 失败语义策略（Failure Semantics）

失败如何被表达？

抛错？

返回空？

近似结果？

📌 例子：

Bellman–Ford：可检测负环

启发式：可能给次优但“成功”

👉 不同算法，对“失败”的态度不同

7️⃣ 正确性承诺策略（Correctness Commitment）

必须最优？

可接受次优？

是否只保证可行？

📌 例子：

精确算法

近似算法

anytime algorithm

👉 数学模型定义“正确是什么”
👉 算法定义“你承诺到哪一步”

8️⃣ 资源使用策略（Resource Trade-off）

（你指出的这一维）

时间 ↔ 空间

预处理 ↔ 查询

离线 ↔ 在线

📌 例子：

DP：空间换时间

流式算法：时间换空间

👉 这是最“表层”的一维

四、一个非常重要的澄清（避免常见误解）

算法不是在“这些维度中选一个”，
而是在每个维度上同时作出一个选择。

所以：

Dijkstra ≠ “时间优化算法”

DP ≠ “空间换时间算法”

它们是一整组映射选择的组合点。

五、你现在可以得到的“总公式”

你现在完全可以这样表述（这是成熟版本）：

算法
= 状态映射
× 结构利用
× 推理顺序
× 决策可逆性
× 不变量维护
× 失败语义
× 正确性承诺
× 资源权衡


任何两个算法不同，
必然在至少一个维度上不同。

六、为什么这套视角“非常高级”

因为它直接推出几个非显然结论：

算法创新 = 新的映射组合

算法对比必须逐维对比

不存在“最优算法”，只有“最适映射”

算法设计是建模的继续，而不是实现阶段

七、给你一句“可以长期用”的总结句

资源使用只是算法映射策略的一个坐标轴，
真正决定算法差异的，是数学结构如何被翻译为推理与状态演化。

如果你愿意，下一步我可以帮你做一件非常“系统化”的事：

👉 把这 8 个维度，反向压缩成 3 个“元选择”
👉 那会变成一个真正可用于设计新算法的心智模型