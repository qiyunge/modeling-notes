一套内核，两种形态

同一个核心体系：

Algorithm Mental Model

Pattern Library

Error Book

分裂成两条输出：

         内核（Algorithm OS）
             │
     ┌───────┴────────┐
     │                │
 内化（能力）      外化（作品）
 A 路线            B 路线

A. 内化版本（你每天用的）

目标：

刷题更快
建模更准
工程更稳
面试更强


形式：

不发布

不讲究排版

高频使用

强调“反射速度”

内容形态：

① Decision checklist（做题前）
state?
transition?
constraint?
objective?

② Pattern reflex（看到就知道）
信号	反应
pair / sorted	two pointers
longest substring	sliding window
最少步数	BFS
子问题最优	DP
所有方案	backtracking
③ Error trigger（卡住就查）

state 太大？

信息不够？

转移不闭合？

constraint 太晚？

这个版本：

是“肌肉记忆”

不是文档。

B. 外化版本（对外展示）

目标：

证明你的算法思维能力
展示建模能力
连接 AI / Decision / Optimization


形式：

GitHub

Docusaurus

Blog

Portfolio

内容形态：

模块 1
Algorithm Design Mental Model

定位：

算法世界观

模块 2
State Representation Pattern Library

定位：

方法论

模块 3
State Design Error Book

定位：

实战经验

模块 4（关键）
Computational Modeling Notes

把算法延展到：

optimization

RL

decision systems

simulation

这一步会直接让你从：

“算法人”

变成：

“Decision systems / AI engineer”

关键点：内化 ≠ 外化

很多人会犯一个错误：

把“外化文档”当“学习工具”。

结果：

写得好看

但不会用

正确结构：

类型	用途
内化版	高频使用
外化版	低频展示
内核	不变
你现在真正要做的，不是继续写

而是完成：

「Algorithm OS v1.0」

结构：

Mental Model
Pattern Library
Error Book
↓
统一为操作系统


这个东西：

是你的算法核心认知

是你 AI 思维入口

是你 Decision Systems 的起点

接下来最关键的一步（决定成型）

不是继续写内容。

而是：

给它定“目录结构”

一旦目录定了：

所有新知识自动归位

所有题目自动归类

所有模型自动连接

这就是：

认知操作系统

我现在只问一个“结构级问题”：

这个体系，你更想把它当：

A. 算法学习系统
B. 建模系统（Algorithm → AI → Decision）
C. 职业核心系统（未来 5 年主线）

只能选一个“主身份”。

因为它会决定：

目录结构

内容深度

输出方式

项目方向

b

很好，你选 B. 建模系统（Algorithm → AI → Decision），
这其实直接把整个体系“升维”了。

它不再是：

刷题系统

算法学习笔记

而是：

Computational Modeling System

（计算建模操作系统）

这会成为你未来：

AI

决策系统

仿真

optimization

RL

的统一入口。

接下来我不会再把内容当“算法笔记”，而是当：

建模语言（modeling language）

来搭结构。

一、主身份确定后的变化

从现在开始，这套体系的定位变为：

Algorithm
不是目标
是建模工具


最终目标：

Modeling reality
→ computation
→ decision


这和：

Decision systems engineer

Simulation engineer

AI engineer

是同一条线。

二、整个系统正式命名

我们给它一个正式名字：

CMS v1.0

Computational Modeling System

它的核心不是“算法”，而是：

如何把现实问题转化为可计算模型。

三、CMS 的核心层级（最关键）

这是之后所有内容的“母目录”。

L0 Reality
L1 Problem formulation
L2 State representation
L3 Transition system
L4 Constraint system
L5 Objective system
L6 Computation strategy
L7 Decision / Policy


你会发现：

算法只在 L6

AI 在 L7

建模在 L1–L5

这才是真结构。

四、把你已有三篇笔记嵌进去
《Mental Model》

归位：

L2–L6

《Pattern Library》

归位：

L6

《Error Book》

归位：

L2–L6 debug layer

五、真正的核心将变成这三个模块
Module 1
Problem → Model

现实 → 数学/计算模型

Module 2
Model → Computation

状态 → 转移 → 算法

Module 3
Computation → Decision

优化 / RL / policy

这三个模块：

直接对应：

运筹学

控制理论

强化学习

决策系统

六、接下来系统的“第一块基石”

不是算法。

是：

Problem Formulation（问题建模）

也就是：

现实问题
↓
变量
↓
状态
↓
约束
↓
目标


这一块才是：

AI工程师

决策工程师

simulation engineer

真正的核心能力。

而大多数人一辈子没学到。

七、你现在进入的阶段

不是算法阶段。

是：

Modeling phase

这个阶段的人：

看问题第一反应：

这是什么系统
变量是什么
状态是什么
目标是什么


不是：

“用什么算法”。

八、下一步必须做的事（极关键）

建立：

Problem Formulation Handbook v0.1

内容：

如何把现实问题抽象为变量

如何识别 state

如何定义 constraint

如何设计 objective

如何判断 deterministic / stochastic

如何判断 discrete / continuous

这一步完成后：

你会开始用“建模语言”看世界。

不是算法语言。

我直接问一个决定接下来深度的问题：

你希望这个 Handbook 第一部分从哪类问题切入？

A. 算法题（离散）
B. 现实工程问题（资源 / 路径 / 调度）
C. AI问题（prediction / RL）
D. 仿真系统（system state / dynamics）

选一个，我们直接进入 CMS 的真正核心。

a

很好，从 A. 算法题（离散） 切入是最稳的路径。
因为：

离散问题边界清晰

状态可控

建模逻辑最纯

是 AI / 决策 / optimization 的“基础训练场”

下面是 CMS 的第一块核心基石文档。

# Problem Formulation Handbook v0.1 — Discrete Problems
（问题建模手册｜离散算法切入）

属于：CMS（Computational Modeling System）

目标：

把“做题”升级为：

Reality → Model → Computation → Decision

---

# 0. 核心理念

算法题 ≠ coding

算法题本质是：



现实问题的离散化模型


真正训练的是：

- 抽象能力
- 状态建模能力
- 约束表达能力
- 目标函数设计能力

---

# 1. Problem Formulation 的标准流程

任何问题统一建模为：



Problem
→ Variables
→ State
→ Constraints
→ Objective
→ Computation


---

# 2. Step 1 — Variables（变量识别）

第一件事不是写算法。

是识别：



系统中有哪些“可变化”的量？


变量分类：

| 类型 | 例子 |
|---|---|
| 位置变量 | i, j |
| 选择变量 | choose/not choose |
| 结构变量 | tree / graph |
| 数值变量 | sum / cost |
| 状态变量 | visited |

---

# 3. Step 2 — State（状态建模）

state 是：



某一时刻系统的完整描述


离散算法中最常见 state：

| 类型 | 表达 |
|---|---|
| index state | i |
| pointer state | (l, r) |
| subset state | visited |
| path state | path |
| DP state | dp[i][j] |
| graph state | node |

---

# 4. Step 3 — Constraints（约束）

约束定义：



哪些 state 是合法的？


约束来源：

- 问题条件
- 资源限制
- 不重复
- 容量限制

例：

- sum ≤ target
- node 未访问
- weight 不超过 capacity

---

# 5. Step 4 — Objective（目标）

算法问题必然有目标：

| 类型 | 例 |
|---|---|
| existence | 是否存在 |
| count | 多少种 |
| optimal | 最小/最大 |
| construct | 给出方案 |

目标决定算法族：

| 目标 | 算法 |
|---|---|
| existence | DFS/BFS |
| count | DP |
| optimal | DP / shortest path |
| construct | backtracking |

---

# 6. Step 5 — Transition（状态转移）

核心问题：



从 state 如何到 next state？


表达：



state + action → next state


例：

- i → i+1
- path + candidate
- node → neighbor
- dp[i] → dp[i+1]

---

# 7. Step 6 — Computation Strategy（算法）

现在才轮到算法。

根据：

- state
- constraints
- objective

选择：

| 状态结构 | 算法 |
|---|---|
| 序列扫描 | two pointer |
| 窗口 | sliding window |
| 子问题 | DP |
| 路径 | BFS |
| 构造 | DFS/backtracking |

---

# 8. 完整建模例子

## Example 1 — Two Sum

### Problem
找两数之和 = target

### Variables
- index i
- 数值 nums[i]

### State


i + seen_numbers


### Constraint
不能重复使用同一元素

### Objective
existence

### Transition


i → i+1


### Computation
hash lookup

---

## Example 2 — Longest Substring Without Repeating

### Variables
- 字符位置
- 字符频率

### State


(l, r, windowSet)


### Constraint
窗口内字符不重复

### Objective
max length

### Transition
扩张 r
必要时收缩 l

### Computation
sliding window

---

## Example 3 — Coin Change

### Variables
- 金额
- 硬币选择

### State


dp[i]


### Constraint
金额非负

### Objective
最少硬币数

### Transition


dp[i] = min(dp[i - coin] + 1)


### Computation
DP

---

# 9. 离散建模的四种基础问题原型

所有算法题本质属于：

## 9.1 Selection
选或不选

→ backtracking / DP

---

## 9.2 Ordering
顺序问题

→ two pointer / sliding window

---

## 9.3 Path
路径问题

→ BFS / DFS / shortest path

---

## 9.4 Allocation
资源分配

→ DP / greedy

---

# 10. 建模错误常见源头

| 错误 | 原因 |
|---|---|
| state 过大 | 存储过多 |
| state 不足 | 信息不够 |
| transition 错 | 漏路径 |
| constraint 晚 | 剪枝失败 |
| objective 不清 | 算法不收敛 |

---

# 11. 判断问题性质（关键）

在选算法前必须判断：

## Discrete vs Continuous

- 离散 → DP / search
- 连续 → optimization

## Deterministic vs Stochastic

- 确定 → algorithm
- 随机 → probability / RL

---

# 12. CMS 中的位置

这份手册属于：



L1 Problem formulation


它决定：

- 状态
- 约束
- 目标
- 算法

---

# 13. 下一步（v0.2）

将进入：

# State Taxonomy（状态分类学）

内容：

- prefix state
- positional state
- relational state
- resource state
- probabilistic state

这一步会让你：

看到题 → 直接识别 state 类型

---

# 终极总结

算法题不是算法训练。

是：



如何把现实离散系统
→ 转化为计算模型


掌握这一步：

- DP
- BFS
- Greedy

都会自然出现。


接下来我们要进入 CMS 的最核心模块：

State Taxonomy（状态分类学）

这是整个系统真正的“发动机”。

我先确认一个方向：

你希望分类从哪种角度开始？

A. 数据结构视角（array / graph / tree）
B. 信息结构视角（position / subset / path / resource）
C. 动力系统视角（state evolution / transition）
D. AI视角（belief / latent / policy state）

选一个，我们直接进入 CMS 的核心引擎。