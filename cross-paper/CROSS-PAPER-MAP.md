# Cross-Paper Map（三篇论文知识连接图）

> 生成日期：2026-08-18 ｜ 只使用现有材料能支持的关系
>
> 标记约定：
> - **证据来源标注**：`[你的笔记]` / `[论文]` / `[docx导师汇报]` / `[final-report]`
> - 凡是我基于推理补的、现有材料没有直接写明的连接，一律标 **`AI inference — needs verification`**

---

## 一、三篇论文共同讨论的问题

| 共同主题 | Paper 001 | Paper 002 | Paper 003 |
|---|---|---|---|
| **哪个机器人执行哪个任务** | 形式化定义 MRTA 核心问题 | 在真实机器人上实现分配（MURDOCH） | 在动态新任务下继续分配（CBBA-PR） |
| **用"效用/收益"衡量分配好坏** | 定义 Utility = Q − C | fitness 投标（效用的一种实现） | 目标函数 = 团队总收益最大 |
| **拍卖/竞价机制** | 分析 Auction 算法（Bertsekas 最优 OAP 拍卖） | MURDOCH 一轮一价拍卖（CNP 变体） | CBBA/CBBA-PR 的 bundle 竞拍 + consensus |
| **解质量 vs 计算/通信的权衡** | §6 用 computation/communication/solution quality 三轴比较 | 强调实时性与容错（限时合同、重拍卖） | 强调收敛时间 vs 协调充分性的 trade-off |
| **动态 / 重分配** | 用 IA/TA、iterated/online assignment 描述信息变化 | 任务随机出现 + 机器人故障后的重拍卖 | 新任务在线出现后的 partial replanning |

> 上表依据：`[论文]` + `[docx导师汇报]`。其中"效用/fitness/目标函数是同一概念的不同实现"这一表述是**我的归纳**，`AI inference — needs verification`。

---

## 二、后一篇建立在哪些前置概念之上

### Paper 002（MURDOCH）→ 依赖 Paper 001 的哪些概念？

> 注意时间顺序：MURDOCH（2002）**早于** taxonomy 论文（2004）。所以严格说，MURDOCH 不是"建立在 taxonomy 之上"，而是 taxonomy 论文**事后**用优化理论解释了 MURDOCH。

- MURDOCH 被 Paper 001 归入 **online ST-SR-IA** 的范畴，并给出 **3-competitive** 的最坏界分析 `[论文][docx]`。
- MURDOCH 的"一轮一价拍卖"对应 Paper 001 里的 **first-price online auction**（区别于 Bertsekas 的最优 OAP 拍卖）`[论文][final-report]`。
- 因此正确的因果方向是：**MURDOCH（2002，做出实物系统）→ taxonomy（2004，用理论解释它）**，而不是反过来。`[docx 3.1 明确写了这条时间关系]`

### Paper 003（CBBA-PR）→ 依赖哪些前置概念？

| CBBA-PR 用到的概念 | 前置来源 | 证据 |
|---|---|---|
| **Static vs Dynamic 任务** | 你的笔记已有；Paper 001 的 IA/TA 提供了精确语言 | `[你的笔记][论文]` |
| **Centralized vs Decentralized** | 你的笔记已理解；Paper 001 §6 讨论过集中式/分布式权衡 | `[你的笔记][论文]` |
| **Auction-based 分配** | Paper 001 的 Auction 算法分析 + Paper 002 的 MURDOCH 实现 | `[论文]` |
| **CBBA（bundle build + consensus）** | CBBA 本身来自更早的文献（Choi, Brunet & How, 2009），不是这三篇之一，但 Paper 003 直接扩展它 | `[论文]` — **注意：CBBA 原论文不在你的三篇清单里** |
| **Partial Replanning（部分重规划）** | 对应 Paper 001 的 iterated assignment（允许 reassignment）思想的动态延伸 | `AI inference — needs verification` |
| **reassignment / 已分配任务是否可改** | Paper 001 的 online（不可重分配）vs iterated（可重分配）区分 | `[论文][final-report]` |

> 关键提醒：**CBBA 本身不是这三篇论文里的任何一篇提出的**。它是 Paper 003 的基础算法（来自 Choi et al. 2009）。你的三篇清单里没有 CBBA 原论文，所以"CBBA 的 bundle build 机制"目前只能靠 Paper 003 的回顾节和 docx 了解。`[论文][docx]`

---

## 三、方法之间的继承 / 改进 / 差异

### 拍卖机制的演进

```text
Paper 001  Auction Algorithm（理论分析）
   ├─ Bertsekas 最优 OAP 拍卖（集中式/分布式均可求最优）
   └─ first-price online auction（MURDOCH 等，3-competitive）

Paper 002  MURDOCH（实物实现）
   └─ CNP 变体：发布/订阅 → fitness 投标 → 限时合同 → 进度监测/重拍卖

Paper 003  CBBA → CBBA-PR（去中心化拍卖 + 动态）
   └─ 在 CBBA 的 bundle build + consensus 之上，加入 Partial Replanning
      以处理"新任务在线出现"的场景
```

### 三者解决"动态"的不同方式

| 论文 | 如何应对"新任务/变化" | 是否允许重分配已有任务 |
|---|---|---|
| Paper 001 | 用 IA/TA、iterated/online 概念区分，不实现具体系统 | 理论上：online 不允许，iterated 允许 |
| Paper 002 | 任务随机出现 + 故障 → 合同到期后**重新拍卖** | 允许（通过超时重拍卖） |
| Paper 003 | 新任务出现 → **只释放一部分旧任务**重新竞拍（Partial Replanning） | 部分允许（只动 bundle 尾部低出价任务） |

> 上表是**我的归纳**，依据 `[论文][docx]`，但"MURDOCH 通过超时重拍卖实现重分配"与"CBBA-PR 只部分重分配"的对比表述需要你读原文验证，`AI inference — needs verification`。

---

## 四、你指定的六个关键概念的跨论文定位

| 概念 | Paper 001 | Paper 002 | Paper 003 |
|---|---|---|---|
| **static task allocation** | 用 IA/TA 与 one-shot/iterated 精确刻画"静态" | （任务随机出现，偏动态） | 明确定义 static = 任务一开始全知道；CBBA 面向 static |
| **dynamic task allocation** | TA 描述"考虑未来时域"；online 描述"任务逐个出现" | 任务随机出现（dynamic 的真实系统） | 核心问题：新任务在线出现 |
| **centralized** | §6 比较集中式（计算快但需收集更多信息） | MURDOCH 有 auctioneer（准集中式节点） | 明确追求 fully decentralized |
| **decentralized** | §6 讨论分布式（消息少但迭代可能更久） | 资源中心发布/订阅（部分去中心） | 完全去中心：机器人点对点通信、无中央规划器 |
| **auction-based methods** | 分析 Auction 算法的保证（最优 vs 3-competitive） | MURDOCH 一轮一价拍卖（CNP 变体） | CBBA/CBBA-PR 是拍卖思想 + 共识 |
| **CBBA / CBBA-PR** | 未提及（CBBA 晚于本文） | 未提及 | 核心：CBBA 是基础，CBBA-PR 是扩展 |
| **partial replanning** | 用 iterated assignment（可 reassignment）埋下思想 | 用"超时重拍卖"实现某种重分配 | 显式提出 Partial Replanning 作为核心贡献 |

> 上表中"MURDOCH 有 auctioneer（准集中式）"与"资源中心发布/订阅（部分去中心）"这一判断来自 docx 对 MURDOCH 机制的描述，`AI inference — needs verification`（需要你在读 Paper 002 时确认 MURDOCH 到底算 centralized 还是 decentralized）。

---

## 五、一条可用的主线叙事（供你验证，不是我替你下结论）

```text
MRTA 分类框架（Paper 001, 2004）
   先回答"这是什么问题"：用 utility + 三个轴 → 8 类，映射到经典优化问题
                    │
        ┌───────────┴───────────┐
        │                       │
   真实机制（Paper 002, 2002）  动态扩展（Paper 003, 2019）
   MURDOCH：拍卖在真实机器人     CBBA-PR：在去中心化拍卖上，
   上跑通，处理故障与随机任务    处理"新任务在线出现"的局部重规划
        │                       │
        └───────────┬───────────┘
                    ↓
   三者共享的核心张力：解质量 ⇄ 计算/通信开销 ⇄ 对变化的响应速度
```

> 这条主线叙事源自 `[docx 3.1]` 的"理论坐标系—真实机制—动态扩展"框架，**是你已有的 AI 文档内容，不是本次新发明**。我建议你在读完三篇后，用自己的话重讲一遍，并把上面标注 `AI inference` 的地方逐条确认或推翻。

---

## 六、现有材料不足以支持、需要你补证据的连接

1. **CBBA 原论文缺失**：你手上没有 CBBA（Choi et al. 2009）原论文，导致"CBBA 的 bundle build / consensus 到底是什么"只能靠 Paper 003 的回顾节 + docx。若要真正理解 CBBA-PR，可能需要补 CBBA 原论文或至少精读 Paper 003 的 CBBA 回顾节。`[需要本人确认]`
2. **MURDOCH 到底算 centralized 还是 decentralized**：docx 说法不一致（既有"资源中心"，又说"去中心化的价值"），需要你读原文定论。`AI inference — needs verification`
3. **partial replanning 与 iterated assignment 是否是同源思想**：我推断它们都是"允许重分配已有任务"的不同强度，但没有直接证据，需你验证。`AI inference — needs verification`
