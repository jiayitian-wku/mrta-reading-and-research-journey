# MRTA Paper Reading & Research Notes

本仓库用于持续记录我对Multi-Robot Task Allocation（MRTA，多机器人任务分配）的论文研读与研究过程。

我的目标不是简单整理论文内容，而是逐步建立对MRTA的系统理解，并保留从初步判断、产生疑问、修正理解，到后续算法分析与实验验证的完整研究轨迹。

## Research Goals

* 建立MRTA的基础概念与分类框架。
* 理解不同任务分配算法的适用场景、基本机制与局限。
* 比较算法在计算、通信、收敛速度和任务分配质量等方面的差异。
* 将阅读过程中产生的问题、误解、修正和阶段性结论持续记录下来。
* 为后续研究问题、算法复现和论文工作打下基础。

## Current Reading Progress

> 说明：`papers/`目录中的编号沿用最初建仓时的顺序。当前实际研读顺序为：001 → 003 → 002。

### 1. A Formal Analysis and Taxonomy of Task Allocation in Multi-Robot Systems

这篇论文用于建立MRTA的基础理论框架，主要涉及：

* Utility
* ST / MT
* SR / MR
* IA / TA
* MRTA Taxonomy
* Optimal Assignment Problem
* Hungarian / Auction / Greedy
* 不同MRTA方法在计算、通信和解质量等方面的比较

**Status:** 阶段性完成。已完成多轮研读、理解修正与综合总结。

### 2. Partial Replanning for Decentralized Dynamic Task Allocation

这是当前正在研读的论文，重点理解：

* Decentralized Task Allocation
* Static vs. Dynamic Task Allocation
* Consensus-Based Bundle Algorithm（CBBA）
* CBBA with Partial Replanning（CBBA-PR）
* Partial Replanning
* Convergence与Conflict-Free Allocation
* 响应速度、团队协调、通信负担和解质量之间的权衡

当前的初步理解是：这篇论文研究去中心化的动态任务分配问题，并提出CBBA-PR，使机器人团队在新任务动态出现时，只重新规划已有任务分配的一部分，而不是完全重新求解所有任务。

**Status:** Round 1进行中。已完成标题、Abstract以及Introduction前两段的第一轮研读，当前正在分析Introduction中已有动态任务处理方法及其局限。

### 3. SOLD!: Auction Methods for Multirobot Coordination

这篇论文将重点用于理解：

* Auction-Based Task Allocation
* 任务发布、竞价、获胜者确定与任务分配
* 多机器人协调中的市场机制
* MURDOCH系统
* 任务重新分配与动态协调

**Status:** 尚未开始系统研读。

## Current Research Focus

当前重点是完成《Partial Replanning for Decentralized Dynamic Task Allocation》的第一轮框架阅读，并逐步回答以下问题：

1. 论文处理的具体任务场景是什么？
2. 新任务出现后，原有CBBA存在什么问题？
3. 作者为什么提出CBBA-PR？
4. Partial Replanning具体重新规划什么？
5. 新方法如何在收敛速度与团队协调之间进行权衡？
6. 作者如何通过实验评价收敛速度和任务分配质量？

## Reading Workflow

### Round 1: Initial Understanding

* 阅读论文整体结构。
* 记录自己的初始理解和判断。
* 标记不理解的术语、句子和算法问题。
* 暂时不深入推导公式或证明。

### Round 2: Verification and Correction

* 根据正文证据回答第一轮问题。
* 修正不准确或过于简单的理解。
* 判断论文真正重要的贡献、机制和局限。
* 保留“初始理解→修正理解”的变化过程。

### Later Research Stages

* 比较三篇论文之间的联系。
* 梳理关键算法和评价指标。
* 进行必要的算法复现或实验验证。
* 形成跨论文的阶段性研究结论。

## Repository Structure

| Path                                   | Purpose            |
| -------------------------------------- | ------------------ |
| `papers/001-formal-analysis-taxonomy/` | MRTA基础理论与分类框架      |
| `papers/002-sold-auction-methods/`     | 拍卖式多机器人协调方法        |
| `papers/003-cbba-partial-replanning/`  | 去中心化动态任务分配与CBBA-PR |
| `cross-paper/`                         | 跨论文概念、方法和问题比较      |
| `reading-log.md`                       | 仓库整体研读进度与阶段记录      |

每篇论文目录主要保留：

* `README.md`：论文信息、当前理解、关键概念和进度。
* `reading-log.md`：逐轮阅读记录、问题、修正和阶段性结论。

## Next Step

1. 完成当前论文Introduction的第一轮研读。
2. 梳理集中式与去中心化动态任务分配方法的区别。
3. 进入Section II，理解动态任务分配的问题定义与CBBA基础。
4. 在Section IV中回答“局部重规划具体重置哪些任务”的问题。
5. 在Section V中核查论文如何评价收敛速度与任务分配质量。

---

**Last Updated:** 2026-08-16
