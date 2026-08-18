# Research Log — Aug 17–18, 2026

**Paper 002:** *Partial Replanning for Decentralized Dynamic Task Allocation*

## 2026-08-17 — Problem Formulation

### 今日进度

继续研读 Paper 002，完成了 **Section 3.1 — Problem Formulation** 的主要内容。

这一部分开始正式进入论文的问题建模阶段。相比前面的 Introduction，这里不再只是介绍研究背景，而是开始用更正式的方式描述机器人、任务以及任务分配之间的关系。

### 今天形成的理解

我开始意识到，`Problem Formulation` 的作用并不是单纯列出数学符号和公式，而是在明确：

* 系统中有哪些 robots 和 tasks；
* 任务如何分配给机器人；
* 什么样的 allocation 是允许的；
* 后续算法到底需要解决什么问题。

这一部分相当于后面理解 CBBA 和 CBBA-PR 的基础。

以前看到数学建模部分时，我更容易把它理解成独立的公式；现在开始尝试把每一个公式重新对应到实际的 MRTA 问题中。

### 当前理解

目前可以把这一部分理解成：

`robots + tasks + allocation constraints + objective`

↓

形成论文后续动态任务分配算法所需要解决的问题。

---

## 2026-08-18 — Dynamic Task Allocation

### 今日进度

继续进入 **Section 3.2 — Dynamic Task Allocation**。

目前已经读到 **Section 3.2.2 — Auction Mechanism**，开始接触论文真正的算法机制。

### 今天最重要的理解变化

今天开始真正区分：

**Static Task Allocation**

和

**Dynamic Task Allocation**

之间的区别。

静态情况下，任务集合相对固定，可以根据已有信息完成一次任务分配。

但是在 dynamic environment 中，会不断出现新的任务或新的变化，因此机器人需要对原来的任务分配结果进行调整。

这里产生了一个核心问题：

> 当新的任务出现以后，是否需要把原来的任务分配全部推翻，然后重新计算？

如果每次都进行 complete replanning，虽然可以重新寻找新的分配方案，但也会带来额外的计算和通信成本。

因此，这篇论文开始引出：

**partial replanning（部分重规划）**

也就是只重新考虑其中一部分原有任务，而不是每次都完全重新规划。

### Auction Mechanism

今天已经开始进入 `auction mechanism`。

目前我的理解是，去中心化任务分配中，机器人并不是依赖一个中央系统统一决定所有任务，而是通过 bidding / auction 的方式进行协调。

现在我正在继续理解：

* robot 到底对什么进行 bid；
* bid 的值是如何决定的；
* 不同机器人之间交换什么信息；
* auction 最终如何形成一致的 task allocation。

这一部分还没有完全研读结束，因此目前先保留这些问题，后续继续补充。

---

## Current Understanding

目前我对整篇论文核心逻辑的理解逐渐形成：

`MRTA Problem`

↓

`Problem Formulation`

↓

`Dynamic Task Arrival`

↓

`Existing Allocation Needs Adjustment`

↓

`Decentralized Coordination`

↓

`Auction / Bidding Mechanism`

↓

`Partial Replanning`

↓

`CBBA-PR`

这两天最大的进展不是记住了更多算法名称，而是开始理解：

**为什么作者需要提出 partial replanning，以及它处于整个动态任务分配流程中的什么位置。**

---

## Questions to Continue

下一阶段继续重点解决：

1. Auction mechanism 中每个 robot 的 bidding 过程具体如何进行？
2. Robots 之间需要交换哪些信息？
3. 原始 CBBA 在 dynamic task arrival 后是如何处理任务的？
4. CBBA-PR 相比 CBBA 到底修改了哪一个关键步骤？
5. Partial replanning 中哪些任务被保留，哪些任务会被重新分配？
6. Partial replanning 如何在 solution quality、computation 和 communication cost 之间进行权衡？

## Next Step

继续完成 **Section 3.2.2 — Auction Mechanism**，暂时不急着记忆所有公式和算法步骤。

当前优先目标是先建立完整的算法逻辑：

**问题是什么 → 为什么需要动态重分配 → auction 如何完成分配 → 为什么需要 partial replanning → CBBA-PR 如何实现它。**
