pandas 的四种“合并/对齐”操作：统一模型

先给一个总纲（这是核心）：

pandas 的所有“合并类操作”，本质都在做两件事之一：
① 关系扩展（row-space 变化）
② 坐标对齐（axis alignment）

一、四兄弟的“数学位置”
操作	本质	对齐依据	行空间变化	类比
merge	关系代数 JOIN	列值	✅ 经常变化	SQL JOIN
join	索引对齐	index	❌ 通常不变	特征补充
concat	轴拼接	axis	✅ 直接叠加	向量/矩阵拼接
align	显式坐标对齐	index/columns	❌（仅重排/补 NaN）	坐标系统一
二、concat：“我不管语义，只拼”
核心语义

不做匹配

只沿某个轴 堆叠

是否对齐 index/columns，取决于 axis

pd.concat([df1, df2], axis=0)  # 行拼接
pd.concat([df1, df2], axis=1)  # 列拼接

示例：axis=0（行拼）
pd.concat([df1, df2])


行数 = df1 + df2

index 可能重复

不关心主键、不关心关系

👉 这是“物理拼接”，不是“逻辑 join”

示例：axis=1（列拼）
pd.concat([df1, df2], axis=1)


会按 index 对齐

不匹配的 index → NaN

👉 axis=1 时，它开始有点像 join，但仍然没有“关系”概念

使用建议

批量堆数据（日志、分块读取）

列并排拼接（你确认 index 已经对齐）

不要用它模拟 SQL join

三、align：最“数学化”的 API（但很少人用）
核心语义

把两个对象投影到同一个坐标系

left2, right2 = left.align(right, join="outer")


不合并数据

只做：

index/columns 对齐

重排

补 NaN

示例
a = pd.Series([1,2], index=["x","y"])
b = pd.Series([10], index=["y"])

a2, b2 = a.align(b, join="outer")


结果：

a2: x=1, y=2
b2: x=NaN, y=10

什么时候用 align？

你要做 向量化运算

不想在心里默默假设 index 对齐

想 显式 表达“统一坐标系”

a2, b2 = a.align(b)
c = a2 + b2


👉 这是 最干净的数学写法

四、回到 merge vs join：为什么 pandas 要分成两个 API？

这是设计哲学问题。

pandas 认为世界有两种数据观：
1️⃣ 表（relation）

行 = 记录

列 = 属性

主键 / 外键

行数变化是“业务事实”

➡ 用 merge

2️⃣ 带坐标的数据（labeled array）

index = 坐标轴

行是“在某个坐标下的观测”

你是在“补信息”，不是“造新记录”

➡ 用 join / align / axis=1 concat

五、一个“绝对不要混淆”的判断题（面试级）

如果你的操作允许产生“重复行”，那它就不应该是 join，而应该是 merge

反过来也成立：

如果你不能解释为什么会多出行，那你就不该用 merge

六、在 pandas 3.0 + CoW 下的再定性（工程视角）
操作	CoW 影响
merge	本来就 copy-heavy，CoW 几乎无感
join	读时共享，写时分离（CoW 很有价值）
concat	axis=0 重建；axis=1 可能共享
align	纯对齐，copy 最少

👉 分析型代码：join / align
👉 数据工程/ETL：merge

七、终极速查口诀（你可以直接记这个）

merge：我在建“关系”

join：我在补“特征”

concat：我在“堆东西”

align：我在“统一坐标系”