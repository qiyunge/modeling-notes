# M-031 · Mapping ADT to Computational Models
# ADT 向计算模型的映射

> 本文档回答一个核心问题：
> **抽象数据类型（ADT）如何从“纯语义对象”，
> 映射为计算模型中“可执行的状态转移系统”？**

---

## 0. 定位说明（Positioning）

- ADT ≠ 算法
- ADT ≠ 数据结构实现
- ADT 是 **值 + 操作 + 约束** 的语义规范
- 计算模型提供 **状态、状态转移、可执行性**

**ADT 只有在映射到计算模型之后，才具备“运行”的意义。**

---

## 1. 为什么 ADT 必须映射到计算模型

### 1.1 ADT 的本体特征

ADT 定义的是：

- 值域（Value Domain）
- 操作（Operations）
- 不变量（Invariants）
- 等价关系（Equivalence）

ADT 本身：

- 不包含时间
- 不包含执行顺序
- 不包含资源概念
- 不包含状态转移机制

👉 **ADT 是纯语义对象，不能直接执行**

---

### 1.2 计算模型提供什么

计算模型（TM / RAM / ASM / λ）提供：

- 状态（State）
- 状态转移（Transition）
- 有限步骤（Finite execution）
- 可执行语义（Operational semantics）

👉 **ADT 必须“落入”计算模型，才能成为可执行系统**

---

## 2. ADT → 计算模型的三类映射（核心结构）

ADT 映射到计算模型，本质上包含三类映射：
ADT
├─ 表示映射（Representation）
├─ 操作映射（Operation）
└─ 约束映射（Invariant）
---

## 3. 表示映射（Representation Mapping）

### 定义

> **将 ADT 的“值”，映射为计算模型中的“状态表示”**

---

### 抽象层（ADT）

```text
Stack<T>
Value:
  finite sequence of T


⸻

计算模型层（示例）

可能的表示映射包括：
	•	数组 + 索引
	•	链表 + 指针
	•	持久化树结构
	•	多个子结构的组合

State = (array, top_index)
State = (array, top_index)
关键特性
	•	同一个 ADT 可以有多个表示映射
	•	表示映射决定：
	•	空间结构
	•	基本操作代价
	•	可用的状态不变量

⸻

核心问题

ADT 的“值”在计算模型中长什么样？

⸻

4. 操作映射（Operation Mapping）

定义

将 ADT 的操作，映射为计算模型中的“状态转移规则”
抽象层（ADT）
push : Stack × T → Stack
语义上表示：

返回一个新的栈值
计算模型层

必须选择一种执行语义：
	•	原地修改（mutable）
	•	复制返回新结构（immutable）
	•	半持久化（persistent）
    (state, input) → state'

关键特性
	•	操作映射引入“执行步骤”
	•	操作映射决定：
	•	时间复杂度
	•	是否可并发
	•	是否可回滚

⸻

核心问题

ADT 的操作如何变成“可执行的状态转移”？

⸻

5. 约束映射（Invariant Mapping）

定义

将 ADT 的不变量，映射为计算模型中的约束机制
Invariant:
  size ≥ 0

  计算模型层

不变量可通过多种方式保证：
	•	表示结构本身不可破坏
	•	类型系统约束
	•	构造器保证
	•	运行时检查
	•	静态验证

⸻

显式 vs 隐式不变量
	•	显式：每次操作检查
	•	隐式：表示方式保证“不可能破坏”

⸻

核心问题

ADT 的语义正确性在执行过程中如何被保证？
6. 完整示例：Queue ADT

6.1 ADT 定义
Queue<T>

Operations:
  enqueue : Queue × T → Queue
  dequeue : Queue → (T, Queue)

Invariant:
  FIFO order
  6.2 映射方案 A：数组 + head / tail
	•	表示映射：数组 + 两个索引
	•	操作映射：索引更新
	•	不变量映射：模运算 + 边界检查

特征：
	•	时间高效
	•	空间固定
6.3 映射方案 B：两个栈
	•	表示映射：Stack_in + Stack_out
	•	操作映射：
	•	enqueue → push Stack_in
	•	dequeue → pop Stack_out（必要时倒栈）
	•	不变量映射：通过操作组合保证 FIFO

特征：
	•	同一个 ADT
	•	完全不同的计算结构

⸻

7. ADT 映射与算法的关系

关键区分
	•	ADT 映射 ≠ 算法
	•	ADT 映射定义：
	•	状态空间
	•	原语操作
	•	算法定义：
	•	状态转移的策略与顺序
关系描述

ADT 决定“能做什么动作”，
算法决定“按什么策略做这些动作”。
8. ADT 映射在整体建模体系中的位置
问题 / 需求
↓
数学 / 逻辑模型
↓
ADT（值 + 操作 + 不变量）
↓
ADT → 计算模型映射
↓
算法（搜索 / DP / 贪心）
↓
实现（递归 / 迭代 / 控制结构）
↓
机器执行

9. 判定清单（Checklist）

在设计或审视一个 ADT 时，必须回答：
	1.	值是如何映射为状态的？
	2.	操作如何成为状态转移？
	3.	不变量在哪里、如何被保证？

若三问均清晰，则该 ADT 已成功落入计算模型。
10. 总结性陈述（Key Statement）

ADT 映射到计算模型，
本质是将“值的语义”
转化为“状态与状态转移的语义”
