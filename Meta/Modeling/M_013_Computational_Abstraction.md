# M-030 · Computational Abstractions（计算抽象）

> 本文档用于界定「计算模型允许什么样的计算形态」。
> 这些抽象不等于算法，也不等于语言语法，
> 而是算法赖以成立的语义基础。

---

## 0. 定位说明（Positioning）

- 计算抽象 ≠ 算法
- 计算抽象 ≠ 控制结构（for / while）
- 计算抽象 ⊂ 计算模型（Computational Model）

关系层级：

问题  
→ 数学 / 逻辑模型  
→ **计算抽象（本文件）**  
→ 算法（有限、可执行、可评估）  
→ 实现 / 控制结构  
→ 机器执行

---

## 1. A 类：计算的定义方式（How computation is defined）

这些抽象回答：**计算在语义上是如何被定义的**

### 1.1 递归（Recursion）
- 自相似定义
- 通过更小子问题定义整体
- 数学基础：不动点（fixpoint）

说明：
- 递归是计算抽象
- 不是算法
- 不依赖具体执行机制（栈只是常见实现）

---

### 1.2 迭代（Iteration）
- 状态序列的逐步推进
- 抽象形式：
  s₀ → s₁ → s₂ → … → sₙ
- 强调“状态演化”，而非控制流

说明：
- 迭代 ≠ 循环
- 循环是实现层控制结构

---

### 1.3 不动点（Fixpoint）
- 定义：f(x) = x
- 计算语义：反复应用直到稳定
- 是递归与循环的统一数学基础

典型应用：
- 递归函数
- 数据流分析
- 程序语义（denotational semantics）

---

## 2. B 类：计算的执行与展开方式（How computation proceeds）

这些抽象决定：**计算如何被展开与调度**

---

### 2.1 求值策略（Evaluation Strategy）
- eager / lazy
- call-by-value
- call-by-name
- call-by-need

影响：
- 终止性
- 性能
- 是否支持无限结构

---

### 2.2 顺序 vs 并发（Sequential vs Concurrent）
- 单一执行路径
- 多个计算同时存在
- 交错执行语义

注意：
- 这是计算模型层差异
- 不是“是否用多线程 API”

---

### 2.3 非确定性（Nondeterminism）
- 一步可能有多个合法后继
- 不等于随机

典型模型：
- NFA
- 逻辑编程
- 搜索空间的抽象定义

---

## 3. C 类：上下文与信息能力（Context & Information）

这些抽象决定：**计算能“记住”什么**

---

### 3.1 状态（State）
- 有状态 / 无状态
- 显式状态 / 隐式状态
- 全局 / 局部状态

模型示例：
- FSM
- ASM
- 状态转移系统

---

### 3.2 作用域与绑定（Scope / Binding）
- 静态作用域
- 动态作用域
- 环境（environment）

这是计算语义问题，而非语法糖。

---

### 3.3 Continuation（续延）
- 当前计算“剩余部分”的显式表示
- 抽象了“接下来做什么”

统一解释：
- return
- exception
- coroutine
- backtracking

---

## 4. D 类：扩展计算语义（Extended computation）

这些抽象扩展了“可计算”的概念边界。

---

### 4.1 并行 / 分布（Parallel / Distributed）
- 同步 / 异步
- 消息传递
- 无共享状态

---

### 4.2 概率计算（Probabilistic Computation）
- 概率转移
- 随机选择
- 马尔可夫过程

---

### 4.3 近似 / Anytime 计算
- 允许不完全结果
- 可中断
- 资源受限下逐步改进

---

## 5. 判定法则（Classification Rule）

判断一个概念是否属于“计算抽象”，问：

> 它是在定义「计算可以长什么样」，  
> 还是在定义「具体怎么算」？

- 前者 → 计算抽象
- 后者 → 算法或实现

---

## 6. 总结性陈述（Key Statement）

> 计算抽象定义了“什么样的计算是可能的”，  
> 算法只是其中在有限资源下的一个具体实例。

---

## 7. Forward References
