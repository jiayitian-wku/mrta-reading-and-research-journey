# MRTA 论文研读与研究记录

本仓库用于持续记录我对 **Multi-Robot Task Allocation（MRTA，多机器人任务分配）** 的论文研读与研究过程。

这里不仅保存最终的论文总结，也会保留阅读过程中形成的手写笔记、理解变化、问题、修正以及不同论文之间的联系。

我的目标不是简单整理论文内容，而是逐步建立自己对 MRTA 的完整理解，并为后续科研与论文工作形成可追溯的研究记录。

## 当前研读论文

### 1. A formal analysis and taxonomy of task allocation in multi-robot systems

主要用于建立 MRTA 的基础理论框架，包括：

- Utility
- ST / MT
- SR / MR
- IA / TA
- MRTA taxonomy
- Optimal Assignment Problem
- Hungarian / Auction / Greedy
- 不同 MRTA 方法的计算、通信与解质量比较

**状态：正在完成多轮研读与总结。**

### 2. SOLD!: Auction Methods for Multirobot Coordination

重点理解 auction-based task allocation，以及 MURDOCH 中任务发布、竞价、分配和重新分配的过程。

**状态：待系统研读。**

### 3. Partial Replanning for Decentralized Dynamic Task Allocation

重点理解 decentralized dynamic task allocation，以及 CBBA / CBBA-PR 中的局部重规划机制。
本文主要分析的是在去中心化的动态任务分配中，如何通过局部重规划快速应对新任务的出现。


**状态：正在完成多轮研读与总结。**

## 仓库结构

### `papers/`

分别保存三篇论文的独立研读记录。

每篇论文主要包含：

- `README.md`：当前对该论文形成的总体理解
- `reading-log.md`：真实的研读过程、问题与理解变化
- PDF：阶段性的手写研读与总结材料

### `cross-paper/comparison.md`

用于在三篇论文研读完成后进行横向比较，整理它们之间的研究脉络、方法差异、假设、局限以及可能进一步研究的问题。

## 记录原则

- 以中文记录自己的理解和研究过程
- 保留重要 technical terms 和 paper titles 的英文原文
- 不追求一次性得到“正确答案”
- 保留理解变化、错误修正和研究问题
- 优先记录真正能够反映思考过程的内容，而不是机械摘抄论文

---

> 这是一个持续更新的 MRTA 学习与研究仓库。
