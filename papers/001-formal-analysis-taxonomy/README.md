# A formal analysis and taxonomy of task allocation in multi-robot systems

## 论文信息

- **作者：** Brian P. Gerkey, Maja J. Matarić
- **年份：** 2004
- **期刊：** The International Journal of Robotics Research
- **研究主题：** Multi-Robot Task Allocation（MRTA，多机器人任务分配）

## 为什么研读这篇论文

这篇论文是我系统学习 MRTA 的第一篇论文。

它并不是只提出一种具体的任务分配算法，而是尝试建立一个统一的理论框架，对不同类型的 MRTA 问题进行分类，并将它们与已有的运筹学和组合优化问题联系起来。

对我来说，这篇论文主要承担“建立 MRTA 整体知识框架”的作用，也是继续研读后续 auction-based task allocation 和 decentralized dynamic task allocation 论文的基础。

## 我的当前理解

MRTA 最核心的问题可以概括为：

> **Which robot(s) should execute which task(s)?**  
> 哪个（或哪些）机器人应该执行哪个（或哪些）任务？

论文首先通过 **Utility（效用）** 对机器人执行任务的收益和成本进行统一描述。

随后作者提出三个分类维度：

- **ST / MT**：机器人能同时执行一个任务还是多个任务
- **SR / MR**：一个任务需要一个机器人还是多个机器人合作
- **IA / TA**：只考虑当前时刻的任务分配，还是需要考虑时间和未来任务

三个二元维度组合后形成 **8 类 MRTA 问题**。

论文进一步把这些 MRTA 问题与 Optimal Assignment Problem、Set Partitioning、Set Covering、Scheduling 等经典优化问题联系起来，并分析不同任务分配方法之间的关系。

在 Section 6 中，作者主要从三个维度比较已有的 MRTA 方法：

1. **Computation Requirements**
2. **Communication Requirements**
3. **Solution Quality**

经过几轮研读后，我逐渐理解到：

**Taxonomy 是用于描述、分类和比较 MRTA 问题的框架，而 Hungarian Algorithm、Auction Algorithm、Greedy Algorithm 等属于解决具体任务分配问题的方法。**

## 核心概念与算法

目前重点接触和学习的内容包括：

- Multi-Robot Task Allocation（MRTA）
- Utility
- ST / MT
- SR / MR
- IA / TA
- Optimal Assignment Problem（OAP）
- Hungarian Algorithm
- Auction Algorithm
- Greedy Algorithm
- Iterated Assignment
- Online Assignment
- Time-Extended Assignment
- Competitive Factor
- Set Partitioning Problem
- Set Covering Problem

## 当前进度

目前已经完成多轮研读。

第一阶段主要进行了逐页阅读、概念理解和算法学习，并形成了第一份手写研读笔记。

在后续复盘中，我发现自己曾经在 Hungarian Algorithm 等局部算法细节上投入过多时间，而对论文整体结构和核心研究逻辑关注不足。

因此，在后续研读中，我开始重新从整篇论文的角度梳理：

- 为什么需要建立 MRTA taxonomy
- 三个分类轴如何形成 8 类问题
- 各类问题与经典优化问题之间的关系
- Section 6 如何比较已有方法
- Taxonomy 的适用范围和局限
- 论文的主要贡献与未来研究方向

## 下一步

- 进一步巩固 8 类 MRTA 问题之间的区别
- 完善对 Section 6 比较框架的理解
- 总结论文的核心假设、贡献与局限
- 尝试脱离原文完整讲述这篇论文的研究逻辑
- 在此基础上继续研读下一篇 MRTA 论文
- 我会持续更新我的阅读笔记整体呈现我多轮研读论文的过程
