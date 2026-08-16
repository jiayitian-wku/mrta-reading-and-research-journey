# Partial Replanning for Decentralized Dynamic Task Allocation

## Paper Information

* **Authors:** Noam Buckman, Han-Lim Choi, Jonathan P. How
* **Year:** 2019
* **Venue:** AIAA SciTech 2019 Forum
* **Paper Link:** [AIAA](https://arc.aiaa.org/doi/10.2514/6.2019-0915)

## Why This Paper Matters

这篇论文研究去中心化的动态任务分配问题，将抽象的MRTA概念落实到一个具体算法——CBBA with Partial Replanning（CBBA-PR）。

它关注的核心问题是：当机器人团队已经形成任务分配方案，而新任务又在运行过程中出现时，如何避免把所有已有任务全部重新分配，同时兼顾响应速度、团队协调、通信负担和任务分配质量。

## My Current Understanding

以下内容是我在第一轮研读中的阶段性理解，之后会根据正文继续修正。

* **Decentralized Task Allocation：** 任务分配所需的计算、通信和决策由机器人团队共同承担，而不是全部依赖中央规划器。
* **Static Task Allocation：** 在任务分配开始之前，所有任务都已经确定和已知。
* **Dynamic Task Allocation：** 新任务会在任务分配或任务执行过程中继续出现，机器人团队需要及时调整已有方案。
* **CBBA：** 一种面向静态任务分配的去中心化算法。
* **CBBA-PR：** 作者在CBBA基础上加入Partial Replanning，使算法能够处理动态出现的新任务。
* **Partial Replanning：** 新任务出现后，只重新规划已有任务分配的一部分，而不是重新分配全部任务。

因此，去中心化动态任务分配是论文研究的问题类别，而CBBA-PR是作者为解决这一问题提出的一种具体算法。

根据摘要，作者声称CBBA-PR能够在多无人机仿真实验中实现更快的收敛，并改善任务分配方案的质量。该结论仍需在后续Results部分结合实验设置和评价指标进行核查。

## Key Concepts & Algorithms

* Multi-Robot Task Allocation（MRTA）
* Decentralized Task Allocation
* Static vs. Dynamic Task Allocation
* Consensus-Based Bundle Algorithm（CBBA）
* CBBA with Partial Replanning（CBBA-PR）
* Peer-to-Peer Communication
* Convergence
* Conflict-Free Allocation
* Robustness
* Scalability

## Current Status

* **Reading Stage:** Round 1 — Overall Framework Reading
* 已完成标题和Abstract的第一轮研读。
* 已完成Introduction第1段和第2段。
* 当前正在阅读Introduction第3段，梳理已有的集中式动态任务处理方法。
* 目前重点是理解论文的研究场景、已有方法局限和CBBA-PR的提出动机，暂不深入公式与算法证明。

### Open Questions

1. `online`在动态任务分配中具体对应哪些新任务出现方式？
2. CBBA-PR如何决定重置哪些任务以及重置多少任务？
3. 论文使用什么指标衡量任务分配方案的质量？
4. CBBA-PR如何在收敛速度与更充分的团队协调之间进行权衡？

## Next Step

1. 继续完成Introduction第3段，区分两类已有集中式方法及其共同局限。
2. 阅读Introduction中关于已有去中心化方法的讨论。
3. 确认作者提出CBBA-PR的具体研究缺口和主要贡献。
4. 完成Introduction后，再进入Section II，学习动态任务分配的问题定义和CBBA基础。
