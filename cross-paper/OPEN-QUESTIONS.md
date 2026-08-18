# Open Questions Tracker（开放问题追踪）

> 生成日期：2026-08-18 ｜ 只整理、不代答
>
> 规则：
> - 每个问题标注 **来源 Paper / 来源 Section / 当前理解 / 尚未解决 / 建议何时解决**
> - 我**不会**替你回答这些问题，只帮你定位它们在笔记中的位置和解决时机
> - "来源 Section" 能确认的才写，不能确认的写 `未能确认`

---

## 一、Concept（概念类）

### Q1 「online 具体表示什么？」
- **来源 Paper**：Paper 003（CBBA-PR）
- **来源 Section**：Abstract（摘要）
- **当前理解**：你已区分 static（任务一开始全知道）vs dynamic（执行中冒出新任务）；但"online"作为独立概念的定义还没自己写清。
- **尚未解决**：online assignment 与 dynamic task arrival、与 IA/TA 的精确关系。
- **建议何时解决**：读到 Paper 003 Section III（作者分析现有动态处理方法）时顺带解决；也可回看 Paper 001 的 "online assignment" 定义对照。

### Q2 「convex score function / continuous decision variables 是什么含义？」
- **来源 Paper**：Paper 003
- **来源 Section**：Introduction 第 4 段（Ref.[9] 的局限）
- **当前理解**：你不懂这两个数学名词，AI 曾提示"第一轮不需要掌握"。
- **尚未解决**：这两个术语的数学定义，以及为什么它限制了 Ref.[9] 的适用问题类型。
- **建议何时解决**：**暂时搁置**。它们是引言里为引出 CBBA 的陪衬，不是主线；等读完 CBBA-PR 算法、有时间再回头补，不要现在卡住。

### Q3 「task scores independent（任务评分相互独立）的含义，以及为什么它是个限制？」
- **来源 Paper**：Paper 003
- **来源 Section**：Introduction 第 4 段（Ref.[10]/[11] 的缺陷）
- **当前理解**：你已初步理解"做任务 A 的价值不应因为还做了任务 B 而变"，但对"为什么现实中不成立、以及它如何限制算法"还模糊。
- **尚未解决**：这个"独立性假设"和 Paper 001 里的"interrelated utilities / task constraints"是不是同一个东西？
- **建议何时解决**：读到 CBBA 的 bundle build（任务价值会因已接任务而变）时，这个假设的反面会自然出现，届时再回看。

### Q4 「adaptive memory / genetic algorithm 这类算法是什么？」
- **来源 Paper**：Paper 003
- **来源 Section**：Introduction 第 3 段
- **当前理解**：你问"这类算法是什么"，AI 纠正为"它们是 centralized dynamic 方法的具体例子，不是 CBBA-PR 的组成部分"。
- **尚未解决**：这两个算法本身的机制（但对你当前目标不重要）。
- **建议何时解决**：**无需专门解决**。你只需知道它们是"集中式动态方法的例子"即可，深挖它们会重蹈 Hungarian 的覆辙。

### Q5 IA / TA 的精确含义，以及 IA 是否等于 static？
- **来源 Paper**：Paper 001
- **来源 Section**：taxonomy 定义（§3 附近）
- **当前理解**：你能列出 IA/TA，但 final-report 指出你曾把"IA = 当前时刻分配"误读成"IA = 静态、不能动态重复"。
- **尚未解决**：IA 下仍可有 iterated / online / 随信息变化的反复分配；TA 是显式规划未来时域。这层区别你还没用自己的话讲清。
- **建议何时解决**：读 Paper 003 的 Section II（问题定义区分 static/dynamic）时回看 Paper 001 的 IA/TA，做一次对照笔记。

---

## 二、Algorithm（算法类）

### Q6 「被重置的部分任务如何确定？」（你原文的 Q2）
- **来源 Paper**：Paper 003
- **来源 Section**：Abstract（你标注"留待 Section IV"）
- **当前理解**：尚未读到；你只知道"Partial Replanning = 只重规划一部分"，但不知道"哪一部分、怎么选"。
- **尚未解决**：释放哪些任务、按什么规则选（bundle 尾部低出价任务？n_reset 怎么定？）。
- **建议何时解决**：**这是 Paper 003 的核心**，读到 Section IV（CBBA-PR 机制）时重点解决。

### Q7 Full Reset / No Reset / Local Partial / Team Partial Reset 四种方式的区别与收敛复杂度
- **来源 Paper**：Paper 003
- **来源 Section**：未能确认（docx 提到，论文正文 Section IV/V 应有）
- **当前理解**：docx 里写了（O(nₜD) vs O(D) vs O(n_reset·D)），但这是 AI 补写，你还没读到。
- **尚未解决**：四种方式的机制、通信轮次、解质量权衡；Local 与 Team 的区别。
- **建议何时解决**：读 Section IV/V 时，**用自己的话**重新整理一遍（不要把 docx 当成自己的理解）。

### Q8 CBBA 的 bundle build 与 consensus 机制；bundle ≠ path 的含义
- **来源 Paper**：Paper 003
- **来源 Section**：未能确认（论文 §II 的 CBBA 介绍）
- **当前理解**：docx 写了定义，你还没读到。
- **尚未解决**：bundle（竞拍加入顺序）与 path（实际执行顺序）为什么不同、为什么释放任务必须按 bundle 尾部。
- **建议何时解决**：读 Section II 的 CBBA 回顾时解决；这是理解 CBBA-PR 的前置。

### Q9 Hungarian 手算细节是否还需要继续投入？
- **来源 Paper**：Paper 001
- **来源 Section**：§5.1（你自己 reading-log 里的反思）
- **当前理解**：你自己已判断"投入超过重要程度"，应转向主线。
- **尚未解决**：这不算未解决问题，而是"已决定停止"的事项，列在此提醒你不再回头。
- **建议何时解决**：**不再继续**。若以后做复现实验再调用，不需要现在补。

---

## 三、Mathematical formulation（数学公式类）

### Q10 目标函数（总收益最大化）的完整数学形式
- **来源 Paper**：Paper 003
- **来源 Section**：Section II-A Problem Statement（你 08-18 刚读到，笔记里贴了公式截图但还没拆解）
- **当前理解**：你写"目标 = 让整个团队总任务收益尽量大"，但公式里的变量、约束还没逐项拆。
- **尚未解决**：公式里的符号含义、约束条件（如每个任务/机器人容量限制）。
- **建议何时解决**：下次精读 Section II-A 时，把每个符号标出来，用自己的话重写公式含义。

### Q11 competitive factor 的 α-competitive 数学定义
- **来源 Paper**：Paper 001
- **来源 Section**：§5.1 附近（final-report 有引用）
- **当前理解**：docx 给了定义（"最坏情况不低于最优的 1/α"），但你自己没推导过。
- **尚未解决**：为什么 2-competitive = 至少最优的一半；为什么 online 无重分配下 3-competitive 是最佳可能。
- **建议何时解决**：写 Paper 001 的最终文字版总结时，用一个小例子（如你曾找的 Greedy 次优反例）验证一遍。

---

## 四、Paper relationship（论文关系类）

### Q12 三篇论文如何连成一条研究主线？
- **来源 Paper**：全部三篇
- **来源 Section**：—
- **当前理解**：docx 的 3.1 节写了"理论坐标系—真实机制—动态扩展"，但这是 AI 补写。
- **尚未解决**：你是否**用自己的话**能讲清这条主线（而不是复述 docx）。
- **建议何时解决**：读完 Paper 002 + Paper 003 后，回到本文件夹的 `CROSS-PAPER-MAP.md` 亲自核对并补写自己的版本。

### Q13 MURDOCH 与 Paper 001 taxonomy 的对应关系
- **来源 Paper**：Paper 002 ↔ Paper 001
- **来源 Section**：—
- **当前理解**：docx 说"MURDOCH 是 online ST-SR-IA 的真实系统实例"，你还没独立验证。
- **尚未解决**：MURDOCH 到底落在 taxonomy 的哪一类、哪个 variant（online / iterated / IA）。
- **建议何时解决**：读 Paper 002 时，明确把它放进 Paper 001 的分类坐标系里。

---

## 五、Experimental result（实验结果类）

### Q14 「任务分配方案的质量」用什么指标衡量？（你原文的疑问）
- **来源 Paper**：Paper 003
- **来源 Section**：Abstract（你标注"留待 Section V"）
- **当前理解**：尚未读到。
- **尚未解决**：CBBA-PR 实验用了什么评价指标（团队总分？收敛轮次？消息量？）。
- **建议何时解决**：读 Section V 实验结果时解决，并记录具体指标与比较对象。

### Q15 MURDOCH 实验数据（49 个任务、3791 条消息、3 小时等）是否可信、如何解读？
- **来源 Paper**：Paper 002
- **来源 Section**：未能确认（实验结果节）
- **当前理解**：docx 列了数字，但你没读过原文实验。
- **尚未解决**：这些数字的实验设置、评价指标、失效模式。
- **建议何时解决**：读 Paper 002 实验节时，对照原文核实（不要直接引用 docx 的数字）。

---

## 六、Research direction（研究方向类）

以下研究问题来自 Paper 001 的 `final-research-report.md`（AI 协助提炼），属于"可做的后续方向"，不是你现在必须做的：

| 编号 | 研究问题 | 现状 | 建议 |
|---|---|---|---|
| RQ1 | utility landscape 结构如何影响 Greedy 与 Hungarian 的效用差距？ | 有设计、未执行 | 可作为最小复现实验，**暂缓** |
| RQ2 | 通信丢包/延迟如何影响 auction 一致性与解质量？ | 未展开 | **暂缓** |
| RQ3 | 新任务出现时，全量重分配 vs partial replanning 如何权衡？ | 未展开 | **优先级最高**，直接连接 Paper 003，读完 CBBA-PR 后可做 |
| RQ4 | precedence/resource constraints 加入后 taxonomy 哪里失效？ | 未展开 | **暂缓** |

---

## 快速索引：哪些问题"现在就该解决" vs "暂时搁置"

- **现在就该解决（主线）**：Q6（被重置任务如何确定）、Q8（bundle build/consensus、bundle≠path）、Q10（目标函数公式）、Q14（质量指标）、Q7（四种 Reset 区别）—— 都在 Paper 003 的 Section II/IV/V，是你当前正在读的路径上。
- **读 Paper 002 时解决**：Q13、Q15、Q12（补全跨论文）。
- **暂时搁置**：Q2（convex function）、Q4（adaptive memory/genetic）、Q9（Hungarian 手算）、RQ1/RQ2/RQ4（研究方向）。
- **需要回看 Paper 001 解决**：Q5（IA/TA）、Q11（competitive factor）。
