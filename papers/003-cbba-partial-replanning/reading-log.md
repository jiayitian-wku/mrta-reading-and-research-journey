# Reading Log

## 2026-08-16 — Introduction | First-round Reading

### What I Read｜今日阅读

今天开始对《Partial Replanning for Decentralized Dynamic Task Allocation》
进行第一轮研读。

今天阅读了 Abstract 和 Introduction 的前半部分，目前停在
Introduction 第三段中途，第三段尚未读完。

### What I Understood｜我的理解

- Decentralized 并不是“任务分散”，而是不存在统一的中央控制器，
  机器人之间通过通信和协调完成任务分配。

- Dynamic Task Allocation 指任务并非在系统开始前全部已知，
  而是可能在机器人执行已有任务的过程中动态出现。

- 本文主要研究的问题是：当多机器人团队已经形成任务分配方案后，
  又出现新的任务时，如何及时调整已有方案。

- CBBA 是本文使用的基础去中心化任务分配算法。

- CBBA-PR 在 CBBA 基础上加入 Partial Replanning，使新任务出现时
  不必完全推翻原有任务分配。

### Questions / Corrections｜问题与理解修正

今天修正了一个理解：

之前一度把 CBBA-PR 和“去中心化动态任务分配问题”混在一起。
现在理解为：

**去中心化动态任务分配是研究问题，CBBA-PR 是作者提出的一种解决方法。**

目前仍未解决的问题：

1. online 在本文语境下具体意味着什么？
2. CBBA-PR 如何决定哪些已有任务需要被 reset？
3. 作者用什么指标衡量 convergence、solution quality 和协调代价？

这些问题暂时保留，等阅读后续对应章节时再回答。

### Next Step｜下一步

从 Introduction 第三段当前停下的位置继续。

先完整理解第三段，再判断这一段在整个 Introduction 的论证结构中
承担什么作用，不提前深入算法细节。
