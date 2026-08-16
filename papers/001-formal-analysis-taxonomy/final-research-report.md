# 论文 001 最终研究报告：A Formal Analysis and Taxonomy of Task Allocation in Multi-Robot Systems

**系统整理 · 理解审计 · 后续研究接口**

- 研究者：田佳一
- 报告日期：2026-08-16
- 用途：个人科研档案、GitHub 阶段性成果与导师交流

> **最终判定：** 第一篇论文的基础研读阶段可以正式结束。你已经掌握论文主线；在采用本报告列出的修正后，可以把精力转向下一篇论文，而不必继续陷在 Hungarian Algorithm 的手算细节中。

---
## English Summary

This paper provides a formal framework and taxonomy for Multi-Robot Task Allocation (MRTA), helping organize different task-allocation problems according to the capabilities of robots, the requirements of tasks, and the temporal characteristics of assignment.

The most important result of my reading was not learning a single allocation algorithm, but developing a structured way to distinguish different MRTA problems. In particular, the ST/MT, SR/MR, and IA/TA dimensions provide a useful conceptual framework for understanding why different task-allocation settings require different solution methods.

During the reading process, I also corrected several early misunderstandings. I initially focused too heavily on individual algorithms such as the Hungarian algorithm and auction-based methods. After revisiting the purpose of the paper, I realized that these algorithms are examples within a broader taxonomy rather than the central contribution of the paper.

This paper therefore serves as the conceptual foundation for my subsequent reading. I will use its taxonomy as a reference when studying more specific decentralized and dynamic task-allocation methods, including CBBA and CBBA with Partial Replanning (CBBA-PR).

---

## 中文完整研究报告


## 1. 研究对象、材料与核验方法

### 1.1 论文信息

| 字段 | 内容 |
| --- | --- |
| 题目 | A Formal Analysis and Taxonomy of Task Allocation in Multi-Robot Systems |
| 作者 | Brian P. Gerkey；Maja J. Matarić |
| 发表 | The International Journal of Robotics Research, 23(9), 939-954, 2004 |
| DOI | 10.1177/0278364904045564 |
| 论文类型 | MRTA 的形式化分析与问题分类框架；不是单一新算法论文，也不是系统综述 |

论文要解决的核心不是“哪一种算法最好”，而是先把多机器人任务分配问题说清楚：给定机器人、任务和可比较的效用估计，怎样描述问题结构、识别对应的经典优化问题，并据此分析或选择求解方法。[P §1-§2]

### 1.2 本报告使用的证据

| 证据代号 | 材料 | 本报告如何使用 |
| --- | --- | --- |
| P | 论文作者版全文（18 页） | 核对定义、公式、复杂度、架构比较、局限与未来方向 |
| N1 | 001-formal-analysis-taxonomy-handwritten-compressed.pdf（18 页） | 识别第一/二轮逐页批注、算法手算、问题与初步结论 |
| N2 | 001-formal-analysis-taxonomy-third-pass-.pdf（2 页） | 核对第三轮整篇综合、三个轴、Section 6-8 与未来问题 |
| G | GitHub README、reading-log 与提交历史 | 还原 8 月 12-16 日的理解变化和当前仓库缺口 |

> **证据边界：** 凡是论文明确提出的内容，本报告用 [P §章节] 标识；凡是来自你的笔记或 GitHub 记录，则用 [N1/N2/G] 标识；本报告新增的研究建议会明确写成“建议”或“可验证问题”，不会伪装成论文结论。

### 1.3 你的阅读轨迹

| 时间 | 记录动作 | 反映出的理解变化 |
| --- | --- | --- |
| 2026-08-12 | 建立三篇 MRTA 论文的仓库结构 | 从零散阅读转向连续保存研究过程 |
| 2026-08-13 | 上传 18 页批注；补写 reading-log | 完成逐页理解，并发现自己在 Hungarian 细节上投入过多 |
| 2026-08-13 | 上传 2 页第三轮综合 | 开始从整篇论文视角回答 taxonomy、Section 6、局限和贡献 |
| 2026-08-16 | 仓库主页标记第一篇“阶段性完成” | 主线已形成，但尚缺一份最终、可核查的系统报告 |

这一轨迹是有价值的：它保留了“先深入局部算法 - 发现失衡 - 回到论文主线 - 形成综合框架”的真实修正过程。比只上传一份漂亮摘要更能说明你的科研学习能力。[G reading-log；Git history]

## 2. 最终判定：是否已经真正读完

> **结论：** 可以正式结束第一篇论文的基础研读阶段，但应以本报告中的修正版作为最终认知版本。你已经理解“论文在做什么”；当前缺口主要是术语精确性、适用条件和证据边界，不是主线缺失。

| 层级 | 判定 | 理由 |
| --- | --- | --- |
| 研究问题与主线 | 通过 | 能说明 MRTA 核心问题、为什么需要 taxonomy，以及 taxonomy 与算法的区别 |
| 三个轴与八类 | 基本通过 | 八类能够列出；但轴名称和“2×2×2”表达需修正，IA/TA 仍需更精确 |
| 算法关系 | 需修正后通过 | Hungarian、Greedy、Auction 已接触，但“拍卖=分布式=最优”的适用范围曾被混在一起 |
| Section 6 证据 | 待深化 | 知道三个比较维度，但尚未完整保留六种架构的精确表格与分析假设 |
| 局限与未来问题 | 基本通过 | 抓住 interrelated utilities 与 task constraints；需把论文原始未来方向与个人扩展分开 |
| 科研复现 | 尚未完成 | 论文阅读可以关闭；算法小实验可作为后续研究，而不是补读论文的前置条件 |

换句话说，你现在不是“没读懂”，而是从入门理解迈向学术表达时，需要把几个容易口语化的概念收紧。完成这一步后，继续反复手算 Hungarian 的边际收益很低。

## 3. 整篇论文的逻辑链

1. 现实背景：MRTA 架构很多，但长期以 proof-of-concept 为主，缺乏共同的形式化分析语言。
1. 统一目标：用 robot-task utility 把执行质量与资源成本压缩成可比较的标量。
1. 形式工具：借用运筹学、网络流、调度与组合优化，把 MRTA 问题映射为已有问题。
1. 分类框架：以 ST/MT、SR/MR、IA/TA 三个二元轴形成 2×2×2=8 类问题。
1. 实证式分析：把六种既有 ST-SR-IA 架构映射到 iterated/online assignment，比较计算、通信和解质量。
1. 边界与未来：承认相互关联效用、任务约束和领域结构未被充分刻画，提出用 utility landscape 收紧预测。

> **一句话主旨：** 这篇论文的真正贡献，是把“各种机器人分配方法看起来各说各话”的局面，转换成“先识别问题类别，再利用成熟优化理论分析求解”的共同框架。

## 4. P/A/M/E/L/Q 系统整理

| 维度 | 系统结论 |
| --- | --- |
| P - Problem | MRTA 缺少可比较、可预测、可指导设计的理论基础；核心问题是哪个/哪些机器人执行哪个/哪些任务。 |
| A - Assumptions | 任务原则上相互独立；效用可压缩为统一标量；效用估计虽有噪声但可比较；研究聚焦 intentional cooperation 与任务分配层。 |
| M - Method | 定义 utility；引入 subset system、matroid、competitive factor；建立 8 类 taxonomy；映射到 OAP、调度、SPP、SCP 等；分析六种架构。 |
| E - Evidence | 形式化问题归约与复杂度结果；已有理论保证；六种已在实体或仿真机器人上验证过的架构的统一分析；另有 Hungarian 运行时间小基准。 |
| L - Limitations | 不覆盖 interrelated utilities 和 task constraints；Section 6 依赖理想化通信与计算假设；competitive factor 是粗糙的最坏情况界。 |
| Q - Questions | 不同 utility landscape 下 Greedy 与最优算法差距多大？不可靠通信与动态任务出现会怎样改变解质量、收敛和重规划？ |

### 4.1 论文究竟有没有做“仿真”

这篇论文的主要证据不是作者新做的一套多机器人仿真实验。作者分析的六种架构此前分别在 physical robots 或 simulated robots 上被验证过；本论文做的是形式化映射与理论比较。[P §6]

作者自己新增的计算实验很有限：用 ANSI C 实现 Hungarian method，在随机、对称、均匀效用的 assignment problem 上测运行时间；当时的 Pentium III 700 MHz 对几十规模问题小于 1 ms，对 300×300 问题小于 1 s。[P §5.1] 这只能证明该方法在所测规模下计算上可行，不能证明它在所有真实 MRTA 环境中整体最好。

## 5. 核心概念的精确版本

### 5.1 MRTA 与 task

论文把 task 定义为实现系统总体目标所需、且原则上可独立于其他子目标完成的 subgoal。它既可以是离散任务，也可以是连续任务。[P §1.1] 因此，本文 taxonomy 的“任务”不是随意切分的动作片段，而是带有强独立性假设的分配单元。

> **必须记住：** 本文分类的是 MRTA problem，不是 robot architecture。Centralized/decentralized、broadcast/unicast、homogeneous/heterogeneous 都不是本文三个 taxonomy 轴。

### 5.2 Utility：不是简单写成 Q-C 就结束

机器人 R 对任务 T 的效用同时依赖机器人与任务。Q(R,T) 表示预计执行质量，C(R,T) 表示预计资源成本。论文采用非负效用：

$$ U(R,T) = Q(R,T) - C(R,T), if R can execute T and Q(R,T) > C(R,T); otherwise U(R,T) = 0. $$

*成本可包含时间、距离、能耗等；质量与成本必须先映射到可比较的统一尺度。[P §3]*

- 效用是估计，不是真实世界的全知值；传感器噪声、环境变化和模型误差会进入估计。
- 论文中的“optimal”是相对于系统可用信息的并集而言的最优，不等于对未知真实世界的绝对最优。
- 效用估计器可以很复杂，但最终必须输出一个可排序的标量。
- 遗漏却会影响真实表现的因素构成 externalities；这正是 taxonomy 边界的重要来源。

### 5.3 Greedy、matroid 与 competitive factor

canonical Greedy 的逻辑是：按效用从高到低检查候选元素，只要加入后仍可行就接受。若可行集合构成 matroid，Greedy 对任意权重都能给出最优解；OAP 并不是 matroid，所以 Greedy 不保证最优。[P §4；§5.1.1]

论文用 α-competitive 表示最坏情况保证：算法结果至少为最优解的 1/α。因而 2-competitive 表示至少有最优值的一半，而不是“比最优差 2%”或“误差为 2”。

## 6. 三个轴与八类问题

### 6.1 三个轴的正确名称

| 轴 | 二元取值 | 准确含义 | 最常见误解 |
| --- | --- | --- | --- |
| 机器人并发任务能力 | ST / MT | ST：每个机器人同一时刻至多执行一个任务；MT：至少有些机器人可同时执行多个任务 | 不是机器人一生只能做一个/多个任务 |
| 任务所需机器人数量 | SR / MR | SR：每个任务恰需一个机器人；MR：至少有些任务需要多个机器人合作 | 不是笼统的 robot capability 轴 |
| 分配时间视野 | IA / TA | IA：现有信息只支持立即分配，不规划未来；TA：已知未来任务集合或任务到达模型，可形成时域计划 | IA 不等于 static，TA 也不只是“任务多” |

> **你笔记中的直接错误：** 第三轮笔记写了“3×2×2=8”。正确表达是：三个维度，每个维度有两个取值，所以组合数为 2×2×2=8。

### 6.2 八类问题与经典优化映射

| 类别 | 直观场景 | 经典问题映射 | 复杂度/结论 | 论文给出的求解方向 |
| --- | --- | --- | --- | --- |
| ST-SR-IA | 一台机器人当前至多做一项；每项只需一台；立即分配 | Optimal Assignment Problem (OAP) | 多项式可解 | Hungarian：最优；Bertsekas auction：满足条件时最优；Greedy：2-competitive |
| ST-SR-TA | 每台机器人形成串行任务计划 | R || Σ wj Cj 调度 | strongly NP-hard | 初始最优分配 + online Greedy 近似；或市场式交换任务 |
| ST-MR-IA | 为当前任务即时组成互斥机器人联盟 | 最大效用 Set Partitioning Problem (SPP) | strongly NP-hard | SPP 启发式；剪枝可行 coalition-task 组合；可并行化 |
| ST-MR-TA | 既要组队又要安排执行时间 | coalition formation + multiprocessor task scheduling | strongly NP-hard；质量难界定 | 忽略时间后迭代 ST-MR-IA；或 leader-based 动态组队与排程 |
| MT-SR-IA | 机器人可并发做多个单机器人任务 | 与 ST-MR-IA 等价：交换 robots/tasks 的角色 | strongly NP-hard | 沿用 SPP 分析与算法 |
| MT-SR-TA | 机器人可并发，且需要未来排程 | 与 ST-MR-TA 等价 | strongly NP-hard | 沿用 coalition + scheduling 的分析 |
| MT-MR-IA | 机器人和任务两侧都允许多对多、集合可重叠 | minimum-cost Set Covering Problem (SCP) | strongly NP-hard | Chvátal 或 Bar-Yehuda/Even 启发式；可行子集越受限越有希望 |
| MT-MR-TA | 多对多并发合作并加入时间计划 | MPTmMPMn || Σ wj Cj | strongly NP-hard；作者当时不知道可用近似 | 论文只给出形式化刻画，没有成熟处方 |

这张表的意义不是要求你背完整调度符号，而是看出结构趋势：一旦加入多机器人协作、并发执行或时间扩展，问题往往从可多项式求解的 OAP 快速进入 strongly NP-hard。taxonomy 因此不仅是命名表，也在提示问题难度和可借用的理论工具。

### 6.3 IA、online、iterated、TA 的关系

| 概念 | 任务信息与重分配 | 是否规划未来 | 典型例子 |
| --- | --- | --- | --- |
| one-shot IA | 当前任务一次性给出并分配 | 否 | 单次 OAP |
| iterated IA | 随着新传感信息反复重算当前分配，可允许 reassignment | 否；每轮仍只看当前 | BLE、动态角色分配 |
| online assignment | 任务逐个出现；已分配机器人不可重分配 | 没有任务到达模型 | MURDOCH |
| TA | 知道任务集合或到达模型，形成跨时间 schedule | 是 | ST-SR-TA 调度 |

> **对下一篇 CBBA-PR 最重要的接口：** dynamic task arrival 并不会自动等于 TA。关键要看算法是否显式规划未来时域、是否允许重分配、任务何时被揭示，以及已有分配如何被修正。

## 7. 四类常被混淆的求解方法

| 方法 | 在本文中的角色 | 保证与适用条件 | 不要误写成 |
| --- | --- | --- | --- |
| Hungarian method | 典型 centralized OAP solver | 完整效用矩阵下给 ST-SR-IA 最优解；论文写 O(m n²)，方阵时 O(n³) | 所有 MRTA 类别的通用最优算法 |
| Bertsekas auction | distributed optimal OAP method | 合适 bidding increment、价格更新和终止条件下求 OAP 最优/近最优 | 任何拍卖架构都必然最优 |
| canonical Greedy | 多种架构背后的共同分配逻辑 | OAP 上 2-competitive；不保证全局最优 | 局部最优一定等于全局最优 |
| online Greedy / Farthest Neighbor | 任务逐个出现且不可重分配时的分配 | 3-competitive；在无到达模型、无重分配条件下是最佳可能最坏界 | 与一次性 Greedy 使用同一保证 |

> **Auction 是一个算法家族：** 论文同时讨论“用于 OAP 的最优 auction algorithm”和“MURDOCH 等 first-price online auction”。前者的最优性不能自动转移给后者。拍卖也不天然意味着没有中央节点；实现可以有 auctioneer、broker 或分布式价格更新。

### 7.1 Centralized 与 distributed 的真实权衡

论文在 ST-SR-IA 中指出：集中式方法通常计算更快，但要收集更多效用信息；分布式 auction 往往消息更少，却可能因迭代竞价和网络时延需要更久。[P §5.1] 这是特定通信模型下的分析，不是“集中式永远通信大、分布式永远通信小”的普遍定律。

论文甚至判断，在当时的小到中型系统（文中举 n<200）且广播可用时，centralized assignment 可能更合适。这一判断依赖 2004 年硬件与通信假设，今天引用时应写成论文语境中的结论。

## 8. Section 6：六种架构的精确比较

### 8.1 比较对象并不是八类问题

Section 6 只选择了六种解决 ST-SR-IA 及其 iterated/online variants 的架构。它的目的不是逐一比较八类 taxonomy，而是证明：不同论文用不同术语描述的架构，映射到相同 optimization problem 后，会显示出共同的算法结构。[P §6]

### 8.2 三个评价维度与隐藏假设

| 维度 | 论文的具体操作化 | 分析假设/未计入项 |
| --- | --- | --- |
| Computation | 每个机器人执行主导操作（通常是 utility 计算/比较）的次数，按 m 个机器人、n 个任务计 | 假设负载均匀并行；不计 utility 计算本身的真实耗时 |
| Communication | 全网 inter-robot messages 总数 | 假设完美共享广播、消息都很小且大小近似；不计丢包与多数时延细节 |
| Solution quality | 将架构映射到 assignment algorithm 后，用 competitive factor 给出最坏情况界 | 不是平均表现；不能说明所有领域中的实际效果 |

> **你第三轮笔记需要收紧：** 你写的“收敛速度、稳定性、通信延迟”等指标很有研究价值，但它们不是 Section 6 三项指标的原始、完整定义。应标成你对比较框架的扩展，而不是论文已经量化的内容。

### 8.3 Iterated assignment 架构（论文 Table 1）

| 架构 | 每轮计算 | 每轮通信 | 解质量 |
| --- | --- | --- | --- |
| ALLIANCE | O(mn) | O(m) | at least 2-competitive |
| BLE | O(mn) | O(mn) | 2-competitive |
| M+ | O(mn) | O(mn) | 2-competitive |

ALLIANCE 的较低通信量来自机器人内部对其他机器人 fitness 的建模，相当于分散了 utility 计算；这并不表示它整体成本一定更低，因为论文的表没有把内部建模开销完整算入。

### 8.4 Online assignment 架构（论文 Table 2）

| 架构 | 每项任务的计算 | 每项任务通信 | 解质量 |
| --- | --- | --- | --- |
| MURDOCH | O(1)/bidder；O(m)/auctioneer | O(m) | 3-competitive |
| Dias & Stentz first-price auctions | O(1)/bidder；O(m)/auctioneer | O(m) | at least 3-competitive |
| Chaimowicz et al. dynamic role assignment | O(1)/bidder；O(m)/auctioneer | O(m) | at least 3-competitive |

三者在这套粗粒度分析中计算与通信几乎相同；允许 reassignment 的后两者可能优于不允许 reassignment 的 MURDOCH。论文借此说明，架构表面差异很大，但底层常共享 Greedy 或 first-price allocation 逻辑。

## 9. 逐项理解漏洞审计

| 你的记录 | 判定 | 漏洞在哪里 | 最终修正版 |
| --- | --- | --- | --- |
| MRTA 是给多个机器人和任务做分配，使整体效用最大 | 正确 | 需补充任务独立与效用可比较假设 | 在给定可用信息和效用模型下，选择可行 robot-task allocation 以最大化系统总效用 |
| Utility = Q-C | 需修正 | 漏掉能力条件、Q>C 和非负截断 | 能执行且 Q>C 时为 Q-C，否则为 0；optimal 只相对可用信息 |
| 三个轴写成 SPACE / ROBOT CAPABILITY / ALLOCATION TIME | 需修正 | 前两个轴名称会误导 | 机器人并发任务能力；任务所需机器人数量；分配时间视野 |
| 3×2×2=8 | 直接错误 | 算式不成立 | 三个二元轴：2×2×2=8 |
| IA 是当前时刻的任务分配 | 部分正确 | 容易误以为 IA=静态、不能动态重复 | IA 不规划未来；仍可 iterated 或 online，甚至随信息变化反复分配 |
| ALLIANCE、M+、MURDOCH、CBBA 放在八类问题附近 | 需修正 | architecture/algorithm 与 problem class 混在一起；CBBA 不在本文 | 先给场景分类，再判断某架构解决哪一类/哪一 variant；本文 Section 6 聚焦 ST-SR-IA |
| Auction 可用分布式方式得到最优分配 | 条件性正确 | 容易把 Bertsekas OAP auction 的保证推广给所有拍卖 | 区分 optimal OAP auction 与 first-price online auction；后者如 MURDOCH 为 3-competitive |
| Hungarian 适合集中式，需要完整效用矩阵 | 正确 | 复杂度应按论文写清；结论只针对 OAP | 一般 O(m n²)，方阵 O(n³)；给 ST-SR-IA 最优解 |
| Section 6 比计算、通信、解质量 | 正确但不完整 | 尚未记录六种架构精确表格与假设 | 保留 Tables 1-2 数值，并注明 broadcast、消息大小、并行计算等假设 |
| 未来处理更动态、更不确定、更大规模 MRTA | 个人推论 | 不是论文最明确的 future work 原句 | 论文明确提出刻画 domain-specific utility landscape，并据此预测 Greedy 与最优算法表现 |
| 论文通过仿真证明算法效果 | 需避免 | 本文没有统一新仿真对比 | 主要证据是形式化映射、理论界和架构分析；仅有 Hungarian 运行时间基准 |

### 9.1 最值得肯定的三点

- 你已经主动纠正“taxonomy 是分类框架，Hungarian/Auction/Greedy 是求解方法”的层级关系，这是真正理解论文结构的标志。[G README]
- 你用具体效用矩阵找到了 Greedy 可能次优的反例，也能解释 2-competitive 和 3-competitive 的直观含义。[N1 p.17]
- 你识别了论文未处理的 interrelated utilities 与 task constraints，并开始把通信限制、动态任务和重分配连接到下一篇论文。[N1 p.16；N2 p.2]

### 9.2 当前 GitHub 记录的真实缺口

- papers/001.../README.md 已写“阶段性完成”，但 reading-log.md 仍停留在第三轮开始之前，没有记录第三轮回答和最终修正。
- cross-paper/comparison.md 仍为空，尚未把 A Formal 与 CBBA-PR 的 static/dynamic、centralized/decentralized、reassignment 等关系填入。
- 仓库中有高价值手写证据，却缺少一份可搜索、可引用、可给老师快速浏览的文字版最终结论。

> **建议的仓库动作：** 把本报告的 Markdown 版放入 papers/001-formal-analysis-taxonomy/final-research-report.md；在 reading-log.md 追加“Final synthesis and corrections”；随后只需在 cross-paper 表中补第一篇对应列，不必继续重写旧笔记。

## 10. 论文贡献、假设与局限

### 10.1 四项主要贡献

1. 提出一个 domain-independent 的 MRTA problem taxonomy，使不同场景有共同描述语言。
1. 把八类问题与 OAP、scheduling、SPP、SCP 等成熟理论连接起来，揭示复杂度并提供候选算法。
1. 用 computation、communication、solution quality 的统一维度分析六种既有架构，暴露其底层相似性。
1. 为从经验式 proof-of-concept 走向可解释、可比较、可预测的 MRTA 研究提供起点，而不是宣称给出最终穷尽框架。

### 10.2 核心假设

- 任务独立：没有先后、同步、共享资源等 task constraints。
- 效用可标量化并跨候选方案比较；系统可获得足够的 robot-task utility estimates。
- 研究 intentional cooperation；任务执行内部如何实现不由 taxonomy 规定。
- Section 6 假设并行计算、完美共享广播、小且近似同尺寸的消息。

### 10.3 局限

| 局限 | 为什么重要 | 论文给出的线索 |
| --- | --- | --- |
| Interrelated utilities | 某任务效用会随同一机器人或其他机器人承担的任务而变，例如路径顺序、拥堵、物理干扰 | MTSP、dynamic MTSP、factored POMDP、learning |
| Task constraints | 任务之间可能有 precedence、parallel execution、resource constraints | 调度理论；dynamic constraint satisfaction |
| Coarse worst-case bounds | competitive factor 可能与真实平均表现差很多 | 加入领域结构以收紧预测 |
| Utility model sensitivity | 若距离、时间、能耗、风险等遗漏，所谓最优只是错误模型内最优 | 研究 utility landscape 与 externalities |

### 10.4 论文真正明确的 future direction

作者最明确的未来方向，是研究真实 MRTA 中 utility matrix 的结构。局部传感可能产生强烈两极化的 utility landscape；全局距离信息可能产生平滑衰减。若能对这些 landscape 分类，就能预测 Greedy 在典型问题中会多接近最优，并决定是否值得支付更高的最优求解成本。[P §8]

## 11. 从第一篇论文自然生长出的研究问题

| 研究问题 | 与本文的连接 | 可测变量 | 与你后续论文的接口 |
| --- | --- | --- | --- |
| RQ1：utility landscape 结构如何影响 Greedy 与 Hungarian 的效用差距？ | 直接承接 §8 future work | 最优比值、运行时间、矩阵稀疏度/平滑度 | 建立算法评价基线 |
| RQ2：通信丢包、延迟和频率限制如何影响 auction 的一致性与解质量？ | 补足 §6 理想通信假设 | 消息数、收敛轮次、冲突率、效用 | 连接 decentralized allocation |
| RQ3：新任务出现时，全量重分配与 partial replanning 的代价如何权衡？ | 从 online/iterated IA 继续推进 | 响应时间、被扰动任务数、总效用、通信 | 直接连接 CBBA-PR |
| RQ4：加入 precedence/resource constraints 后，三轴 taxonomy 哪些地方失效？ | 承接 §7.2 | 可行率、调度长度、求解复杂度 | 连接更完整的 MRTA taxonomy |

> **当前优先级：** 对你现在最合适的是先带着 RQ3 进入 CBBA-PR 阅读；RQ1 可作为后续最小复现实验。RQ2 和 RQ4 暂时作为研究问题保留，不需要现在同时展开。

## 12. 最小复现实验设计（尚未完成，不冒充论文证据）

如果之后需要把“读懂”推进到“有可验证产出”，可以做一个纯软件、Mac 可完成的小实验。它不是关闭第一篇阅读的必需项，也不涉及硬件。

1. 生成三类 utility matrices：随机、局部稀疏/两极化、随距离平滑衰减。
1. 同一矩阵分别运行 Hungarian 与 Greedy；另建立任务逐个出现且不可重分配的 online Greedy。
1. 记录 total utility、Greedy/optimal ratio、运行时间，以及一个明确声明为 proxy 的消息量估计。
1. 改变机器人/任务规模和 utility 结构，观察最坏界与典型表现是否相差很大。
1. 把失败案例、随机种子、代码和图表放入 experiments/001-assignment-baseline/，不要只上传最好结果。

| 完成标准 | 最低要求 |
| --- | --- |
| 可复现 | 固定随机种子、记录依赖与运行命令 |
| 可比较 | 同一输入、同一效用定义、至少 3 种规模 |
| 可解释 | 说明 Greedy 何时失败，不只给平均数 |
| 不夸大 | 消息量若未真实模拟网络，必须写 communication proxy |

## 13. 可直接向老师讲的 90 秒版本

> 这篇论文针对 MRTA 研究长期偏经验、缺少统一理论的问题，提出了一个与具体任务和架构无关的分类框架。作者先用 utility 表示机器人执行任务的预计质量减去成本，再从三个二元维度描述问题：机器人能否并发执行多个任务、一个任务是否需要多个机器人，以及分配是否包含未来时间规划，因此形成 2×2×2 共八类问题。论文进一步把这些类别映射到 Optimal Assignment、Scheduling、Set Partitioning 和 Set Covering 等经典优化问题，从而判断哪些问题可精确求解、哪些是 strongly NP-hard。Section 6 并没有比较完整八类，而是把六种 ST-SR-IA 架构统一放到计算量、通信量和解质量三个维度下分析，发现许多表面不同的架构底层都接近 Greedy 或 first-price allocation。它的局限是默认任务和效用基本独立，也采用较理想的通信假设。对我后续最重要的启发是：先识别问题结构，再讨论算法；同时要研究动态任务出现和重分配怎样影响通信、响应速度与总效用。

## 14. 最终关闭清单

| 检查项 | 状态 | 关闭标准 |
| --- | --- | --- |
| 能讲清论文研究问题 | 完成 | 不把论文说成单一算法论文 |
| 能准确解释三个轴 | 修正后完成 | 使用 2×2×2=8；不用 SPACE/robot capability 误命名 |
| 能区分 taxonomy 与 algorithms | 完成 | 先问题分类，后求解方法 |
| 能区分 Hungarian、optimal auction、online auction、Greedy | 修正后完成 | 不给所有拍卖方法套用最优保证 |
| 能说明 Section 6 的范围和假设 | 本报告已补齐 | 六种 ST-SR-IA 架构；保留两张精确比较表 |
| 能说明论文证据 | 本报告已补齐 | 理论映射为主；不是统一新仿真实验 |
| 能说明局限和 future work | 完成 | interrelated utilities、task constraints、utility landscape |
| GitHub 有最终文字版 | 待你上传 | 添加本报告 Markdown；reading-log 追加最终节点 |

> **最终决定：** 在把本报告的修正作为最终版本后，第一篇论文可以正式关闭。下一步不是继续补更多算法细节，而是进入 CBBA-PR，并持续用“问题类别 - 假设 - 方法 - 证据 - 权衡 - 局限”的框架阅读。

## 附录 A：引用键与材料位置

| 引用键 | 位置 |
| --- | --- |
| P | Gerkey & Matarić (2004) 作者版全文；报告按论文 section 标注 |
| N1 | papers/001-formal-analysis-taxonomy/001-formal-analysis-taxonomy-handwritten-compressed.pdf |
| N2 | papers/001-formal-analysis-taxonomy/001-formal-analysis-taxonomy-third-pass-.pdf |
| G README | papers/001-formal-analysis-taxonomy/README.md |
| G reading-log | papers/001-formal-analysis-taxonomy/reading-log.md |
| Git history | 仓库 main 分支，核验至 commit 446524f（2026-08-16） |

## 附录 B：来源链接

- [论文 DOI / 期刊页面](https://doi.org/10.1177/0278364904045564)
- [论文作者版 PDF](https://robotics.stanford.edu/~gerkey/research/final_papers/mrta-taxonomy.pdf)
- [你的 MRTA GitHub 仓库](https://github.com/jiayitian-wku/mrta-reading-and-research-journey)

建议引用格式：Gerkey, B. P., & Matarić, M. J. (2004). A formal analysis and taxonomy of task allocation in multi-robot systems. The International Journal of Robotics Research, 23(9), 939-954. https://doi.org/10.1177/0278364904045564
