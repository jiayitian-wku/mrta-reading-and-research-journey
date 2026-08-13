## 2026-08-13 — First-pass review and re-entry

### What I Read

第一轮阅读时，我先整体了解了这篇论文的结构、研究问题和主要内容，并在第一份手写笔记的最后两页对整体思路进行了整理。

第二轮阅读开始按照重要程度进一步细读。我重点学习了 utility、MRTA taxonomy，以及论文中的部分算法和问题类型，并尝试理解论文的主要结论和可能进一步研究的问题。

### What I Understood

经过前两轮阅读，我逐渐意识到，论文研读不是把所有出现的概念和算法都研究到很深，而是首先需要抓住作者真正想解决的问题，以及各部分内容在整篇论文中的作用。

目前我已经对 utility、ST/MT、SR/MR、IA/TA 等基本概念，以及部分 assignment algorithms 有了一定理解。

### Questions / Corrections

回看第二轮阅读过程，我发现自己的一个明显问题是阅读深度分配不均。

例如在 ST-SR-IA 部分，我花了较多时间深入研究 Hungarian Algorithm，并进行了多次手算和算法细节学习。虽然这些内容帮助我理解了 assignment problem，但投入的时间超过了它在整篇论文中的重要程度。

这导致我对部分算法细节理解较深，但对论文整体 taxonomy、Section 6 的比较分析、Section 7 的边界，以及论文整体贡献和局限的理解还不够完整。

因此，我需要从“遇到一个知识点就深入研究”转向“先理解论文主线，再决定哪些知识值得深入”。

### Next Step

第三轮阅读将以完成整篇论文的核心理解为目标，重点回答：

- 为什么作者需要建立 MRTA taxonomy？
- ST/MT、SR/MR、IA/TA 三个轴如何形成 8 类 MRTA 问题？
- 各类 MRTA 问题大致对应哪些经典优化问题？
- Section 6 为什么从 computation、communication 和 solution quality 三个维度比较现有方法？
- Section 7 说明 taxonomy 无法覆盖哪些问题？
- 这篇论文的主要贡献、假设、局限是什么？
- 从这些局限中可以进一步提出哪些研究问题？
