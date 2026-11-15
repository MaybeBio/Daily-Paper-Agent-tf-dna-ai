## 01 基本信息

- **标题**：SP1 tethers NR2F2 to drive atrial cardiomyocyte identity
- **作者**：Gergen, Payton N; Clark, Alexander P; Saucerman, Jeffrey J
- **单位**：未提供（根据作者姓名与领域推断为美国高校生物医学工程系，但原文未提供，不臆造）
- **期刊/平台**：bioRxiv : the preprint server for biology（预印本）
- **年份**：2026（预印本日期 2026-11-08）
- **论文类型**：预印本（研究论文）
- **领域**：心脏发育、基因调控网络（GRN）、转录因子（TF）互作、单细胞多组学
- **关键词**：NR2F2、SP1、atrial cardiomyocyte、gene regulatory network、single-cell RNA-seq、ATAC-seq、AlphaFold、iPSC 分化
- **DOI/arXiv 号**：10.64898/2026.10.19.760167
- **代码**：未提供
- **数据**：人类胎儿单细胞 RNA-seq 与 ATAC-seq 数据（具体数据集编号未提供）
- **阅读日期**：2026-11-08（按预印本日期计）
- **在「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」方向中的位置**：本文属于「GRN 推断 + 结构预测（AlphaFold）+ 实验验证」的交叉路径。其核心贡献在于：用 GRN 推断提出 TF–TF 协同（而非直接 TF–DNA 结合）假说，再用 AlphaFold 预测蛋白-蛋白 tethering（拴系）的物理机制，最后用实验（SP1 敲低、proximity ligation）验证。对 TF–DNA 互作课题的可迁移点：① 将「TF 直接结合靶基因」的默认假设扩展为「TF 通过 tethering 另一 TF 间接调控」；② 用 AlphaFold 预测 TF–TF 物理互作作为 GRN 推断的验证层；③ 用 ATAC-seq 与 promoter 注释两种约束对比来发现「非直接结合」的调控关系。

---

## 02 一句话总结

本文通过对比 ATAC-seq 约束与 promoter 注释约束的人类胎儿心房/心室心肌细胞 GRN，预测 NR2F2 并非直接结合心房基因启动子，而是通过物理拴系 SP1 间接驱动心房心肌细胞身份，并用 AlphaFold 预测、SP1 敲低实验和 proximity ligation 实验验证了这一机制。

---

## 03 研究问题

- **具体问题**：在人类胎儿心房心肌细胞中，已知的心房特化转录因子 NR2F2 究竟是通过直接结合靶基因启动子，还是通过与其他 TF（如 SP1）物理互作（tethering）来驱动心房基因表达？
- **为什么重要**：人类心脏发育的 GRN 与动物模型不同，且难以直接研究。理解 NR2F2 的精确作用机制对心脏发育生物学、先天性心脏病机制和 iPSC 心房分化方案优化都至关重要。
- **现有方法为何不足**：传统 GRN 推断通常基于 promoter 注释（即假定 TF 直接结合启动子），忽略了 TF 通过蛋白-蛋白互作间接调控靶基因的可能；而仅用 ATAC-seq 约束又可能引入大量开放染色质区域的非功能性结合位点。两种约束单独使用都无法区分「直接结合」与「tethering 间接调控」。
- **精确研究问题（Can...?）**：Can we distinguish direct TF–DNA binding from TF–TF tethering in driving atrial cardiomyocyte identity by comparing GRNs constrained by ATAC-seq vs. promoter annotations, and validate the predicted tethering biophysically and experimentally?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注「仅本文框架」；外部文献连接见第 15 节。

1. **阶段一：GRN 推断的早期方法（promoter 注释约束）**
   - 代表方法：基于已知 promoter 序列中的 TF 结合 motif 推断 TF–靶基因关系。
   - 优点：直接反映 TF–DNA 结合；计算简单。
   - 局限：忽略开放染色质状态；无法捕捉 TF 通过蛋白互作间接调控；motif 存在不等于功能结合。
   - 本文位置：作为对比基准之一。

2. **阶段二：整合染色质可及性（ATAC-seq 约束）**
   - 代表方法：用 ATAC-seq 峰限定候选调控区域，再在其中找 motif。
   - 优点：反映开放染色质状态，更接近功能调控环境。
   - 局限：开放区域中大量非功能性结合；仍无法区分直接结合与 tethering。
   - 本文位置：作为对比基准之二。

3. **阶段三：多组学 GRN 推断 + 结构预测验证（本文主张）**
   - 代表方法：同时构建 ATAC-seq 约束与 promoter 约束的 GRN，比较差异；用 AlphaFold 预测 TF–TF 物理互作；用实验验证。
   - 优点：能提出「非直接结合」的调控假说；结构预测提供物理机制层面的支持；实验验证闭环。
   - 局限：依赖 GRN 推断质量；AlphaFold 预测需实验确认；样本量有限。
   - 本文位置：本文即此阶段的代表工作。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 传统 GRN 推断无法区分直接结合与间接调控 | 仅用 promoter 注释约束时，NR2F2 被预测为直接调控心房基因；但 ATAC-seq 约束下该关系消失 | 作者解释：NR2F2 可能不直接结合 DNA，而是通过 tethering 另一 TF（SP1）间接调控；promoter 注释约束会错误地将这种间接关系归为直接结合 | Abstract；Results 中 GRN 对比部分（具体图号未提供） |
| 人类心脏 GRN 与动物模型差异大 | 动物模型中的心房调控知识无法直接迁移到人类 | 作者解释：人类胎儿心脏的调控网络具有物种特异性 | Abstract 第一句 |
| 开放染色质区域存在大量非功能性 TF 结合位点 | ATAC-seq 约束的 GRN 可能包含大量假阳性 | 作者解释：ATAC-seq 峰反映可及性而非功能性结合 | Abstract 中「comparing GRNs based on current and potential epigenetic state」的论述 |
| 单一组学数据无法验证 TF–TF 物理互作 | 仅靠 GRN 推断无法确认 NR2F2-SP1 是否真的物理互作 | 作者解释：需要结构预测（AlphaFold）和实验（proximity ligation）来验证 | Abstract 中 AlphaFold 与 proximity ligation 部分 |

---

## 06 核心思想

### 1) 表面方法
- 从人类胎儿心脏单细胞 RNA-seq 和 ATAC-seq 数据分别推断心房与心室心肌细胞的 GRN。
- 用两种约束（ATAC-seq 峰 vs. promoter 注释）分别构建 GRN，比较差异。
- 对预测的 NR2F2-SP1 关系用 AlphaFold 预测蛋白-蛋白互作，并用已有 ChIP-seq 数据交叉验证。
- 在人类 iPSC 来源的心房心肌细胞分化体系中做 SP1 敲低，验证功能必要性。
- 用 proximity ligation 实验验证 NR2F2 与 SP1 在细胞核内的物理互作。

### 2) 核心洞察
- **「TF 不直接结合 DNA，而是通过 tethering 另一 TF 来调控靶基因」** 这一机制在人类心房心肌细胞中可能比预想更普遍。
- **对比两种 GRN 约束（ATAC-seq vs. promoter）的差异** 可以系统性地发现「非直接结合」的调控关系——这是一种新的计算策略。
- NR2F2 作为经典心房特化因子，其功能可能依赖 SP1 作为「DNA 结合锚点」，而非自身直接结合 DNA。

### 3) 可能的普适教训 [Analysis]
- 在 TF–DNA 互作研究中，**「TF 在 motif 上出现」不等于「TF 直接结合该位点」**；TF 可能通过蛋白-蛋白互作被招募。
- **多约束 GRN 对比** 是一种低成本、可迁移的假说生成策略，适用于任何有 ATAC-seq 和转录组数据的体系。
- **AlphaFold 可作为 GRN 推断的物理验证层**，在实验前筛选高置信度的 TF–TF 互作候选。

---

## 07 方法总览

- **输入**：人类胎儿心脏单细胞 RNA-seq 数据、单细胞 ATAC-seq 数据；已有 ChIP-seq 数据（用于交叉验证）；人类 iPSC 心房心肌细胞分化体系。
- **输出**：心房 vs. 心室心肌细胞特异的 GRN；NR2F2-SP1 调控关系；SP1 功能必要性结论；NR2F2-SP1 物理互作证据。
- **模块**：
  1. 单细胞多组学数据处理与细胞类型注释（心房/心室心肌细胞）。
  2. GRN 推断（两种约束：ATAC-seq 峰 vs. promoter 注释）。
  3. 差异比较与候选调控关系筛选。
  4. AlphaFold 蛋白-蛋白互作预测。
  5. ChIP-seq 数据交叉验证。
  6. iPSC 心房分化 + SP1 敲低功能实验。
  7. Proximity ligation 物理互作验证。
- **训练**：未涉及传统机器学习训练；GRN 推断为统计/计算推断方法（具体算法未提供）。
- **反馈回路**：计算预测 → 结构预测 → 实验验证 → 修正模型。
- **假设**：① ATAC-seq 峰反映潜在调控区域；② promoter 注释反映直接结合 motif；③ 两种约束的差异可揭示 tethering 机制；④ AlphaFold 预测的互作界面具有生物学意义。

**文字流程**：
人类胎儿心脏单细胞 RNA-seq + ATAC-seq → 注释心房/心室心肌细胞 → 分别用 ATAC-seq 峰和 promoter 注释约束推断 GRN → 比较两种 GRN 差异，发现 NR2F2 在 ATAC-seq 约束下不直接调控心房基因 → 预测 NR2F2 通过 SP1 间接调控 → AlphaFold 预测 NR2F2-SP1 物理互作 → 与已有 ChIP-seq 数据比对 → 在 iPSC 心房分化中敲低 SP1 验证功能 → Proximity ligation 验证核内物理互作。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 单细胞多组学数据处理与细胞类型注释 | 区分心房/心室心肌细胞，获得细胞类型特异的基因表达与染色质可及性 | 需要细胞类型特异的 GRN 才能比较心房 vs. 心室调控差异 | 输入：scRNA-seq + scATAC-seq；输出：注释后的细胞群体 | Abstract 描述 | 预期影响：无法获得细胞类型特异的 GRN，无法进行心房 vs. 心室比较 [Analysis] |
| 双约束 GRN 推断（ATAC-seq vs. promoter） | 分别构建两种约束下的 GRN，比较差异 | 对比两种约束可揭示「非直接结合」的调控关系 | 输入：表达矩阵 + 染色质可及性/motif 注释；输出：两套 GRN 及差异列表 | Abstract 核心方法描述 | 实测影响：移除任一约束将无法发现 NR2F2-SP1 的间接调控关系（作者核心主张） |
| AlphaFold 蛋白-蛋白互作预测 | 预测 NR2F2 与 SP1 的物理互作界面 | 为 GRN 推断的间接调控假说提供物理机制层面的支持 | 输入：NR2F2、SP1 蛋白序列；输出：互作预测结构/置信度 | Abstract 明确提及 | 预期影响：缺少此层验证，NR2F2-SP1 关系仅停留在计算推断层面 [Analysis] |
| ChIP-seq 交叉验证 | 用已有 ChIP-seq 数据验证预测的 NR2F2-SP1 共定位 | 提供独立于本文数据的证据 | 输入：已有 ChIP-seq 数据；输出：共定位/结合证据 | Abstract 提及 | 预期影响：缺少独立数据支持，结论强度下降 [Analysis] |
| iPSC 心房分化 + SP1 敲低 | 功能验证 SP1 对心房心肌细胞身份的必要性 | 证明 SP1 不仅是计算预测，而是功能必需 | 输入：iPSC 心房分化体系 + SP1 敲低；输出：心房分化表型变化 | Abstract 明确提及 | 实测影响：SP1 敲低抑制心房分化（作者核心实验证据） |
| Proximity ligation 实验 | 验证 NR2F2 与 SP1 在细胞核内的物理互作 | 直接证明两个蛋白在空间上接近 | 输入：心房心肌细胞 + 抗体对；输出：邻近信号 | Abstract 明确提及 | 预期影响：缺少此实验，物理互作仅靠 AlphaFold 预测 [Analysis] |

---

## 09 关键公式符号

**不适用。** 本文为计算 GRN 推断 + 实验验证型研究，提供的摘要与正文中未包含可提取的数学公式。GRN 推断的具体统计算法（如相关性、回归或互信息方法）在提供的材料中未给出具体公式。

---

## 10 实验设计与证据链

- **数据集/群体**：人类胎儿心脏单细胞 RNA-seq 与 ATAC-seq 数据（具体样本量、胎龄、供体数未提供）；人类 iPSC 来源心房心肌细胞分化体系。
- **指标**：GRN 中 TF–靶基因关系的存在/缺失；心房 vs. 心室差异调控的 TF；SP1 敲低后心房分化标志物变化；proximity ligation 信号。
- **基线**：promoter 注释约束的 GRN（作为与 ATAC-seq 约束对比的基准）。
- **预算**：未提供。
- **骨干/仪器**：未提供（单细胞测序平台、iPSC 分化方案细节未提供）。
- **oracle 输入**：已有 ChIP-seq 数据（用于交叉验证 NR2F2-SP1 关系）。
- **评测协议**：计算预测 → 结构预测 → 独立数据交叉验证 → 功能实验 → 物理互作验证。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 双约束 GRN 推断与比较 | NR2F2 在 ATAC-seq 约束下不直接调控心房基因 | ATAC-seq 约束 vs. promoter 注释约束 | NR2F2 在 ATAC-seq 约束下不直接驱动心房基因 | NR2F2 可能通过间接机制（tethering）调控 | 不能仅凭 GRN 推断确认具体机制 | Abstract |
| AlphaFold 预测 NR2F2-SP1 互作 | NR2F2 与 SP1 存在物理 tethering | AlphaFold 预测 + 已有 ChIP-seq 数据 | 预测支持 NR2F2-SP1 物理互作 | 计算层面支持 tethering 假说 | AlphaFold 预测不等于体内真实互作 | Abstract |
| SP1 敲低实验 | SP1 是心房心肌细胞分化所必需 | 对照 vs. SP1 敲低 | SP1 敲低抑制心房分化 | SP1 功能上必要 | 不能证明 NR2F2 必须通过 SP1（可能有 SP1 独立功能） | Abstract |
| Proximity ligation | NR2F2 与 SP1 在核内物理接近 | 心房心肌细胞中检测 | 检测到 NR2F2-SP1 邻近信号 | 两蛋白在核内物理互作 | 不能证明互作发生在心房基因启动子处 | Abstract |

---

## 11 结论正确解读

- **任务范围**：本文结论限定于人类胎儿心房心肌细胞中 NR2F2 调控心房基因的机制；不推广到其他细胞类型或物种。
- **oracle/真值输入**：使用了已有 ChIP-seq 数据作为交叉验证，但该数据并非本文新产生；proximity ligation 为直接实验证据。
- **端到端状态**：计算推断 → 结构预测 → 实验验证的完整闭环已实现，但 SP1 敲低实验仅证明 SP1 必要性，未做 NR2F2 回补或 SP1 过表达挽救实验来证明「NR2F2 必须通过 SP1」。
- **算力成本**：未提供。
- **历史数据依赖**：依赖人类胎儿心脏单细胞数据质量与注释准确性；依赖已有 ChIP-seq 数据的可比性。
- **模型依赖**：GRN 推断结果依赖所用推断算法与阈值（具体算法未提供）；AlphaFold 预测依赖其训练分布。
- **最难情形**：区分「NR2F2 通过 SP1 tethering」与「NR2F2 直接结合但 motif 不在 ATAC-seq 峰内」两种可能；SP1 敲低可能影响全局转录而非仅心房基因。
- **群体/领域边界**：结论限于人类胎儿心房心肌细胞；iPSC 分化体系与胎儿心肌的相似性有限。
- **不确定性**：GRN 推断的统计不确定性未报告；AlphaFold 预测置信度未报告；SP1 敲低效率与脱靶效应未报告。

**有边界的复述**：在人类胎儿心房心肌细胞中，基于 ATAC-seq 约束的 GRN 推断提示 NR2F2 不直接结合心房基因启动子；AlphaFold 预测与 ChIP-seq 数据支持 NR2F2 与 SP1 存在物理互作；SP1 敲低抑制 iPSC 心房分化，proximity ligation 证实两蛋白核内共定位。这些证据共同支持「NR2F2 通过 SP1 tethering 驱动心房心肌细胞身份」的机制，但未排除 NR2F2 在其他位点直接结合 DNA 的可能性。

---

## 12 作者自认局限

在提供的材料（Abstract）中，作者明确承认的局限有限。以下为可识别内容：

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 人类心脏 GRN 复杂且难以解析 | 作者在开头指出人类心脏发育 GRN 复杂、难以 unravel，且与动物模型不同 | 未明确给出 | Abstract 第一句 |
| 未提供其他明确局限 | — | — | — |

**作者提及的相关约束**（非正式局限，[Analysis] 标注）：
- 本文为预印本，尚未经同行评审。
- SP1 敲低实验仅证明必要性，未做机制回补实验。
- GRN 推断的具体算法与参数未在摘要中提供，影响可复现性评估。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 双约束 GRN 对比的差异被解释为「tethering」 | 差异也可能来自 ATAC-seq 峰与 promoter 注释的覆盖范围不同、motif 扫描阈值差异、或数据噪声 | 如果差异来自技术因素而非生物学机制，则核心结论不成立 | 用模拟数据或置换检验评估两种约束差异的显著性；用独立数据集重复 | Abstract 方法描述 |
| AlphaFold 预测的 NR2F2-SP1 互作 | AlphaFold 预测的是静态结构，不能证明体内真实互作；预测的互作界面可能不具功能 | 结构预测是核心证据链的一环，若不可靠则证据链断裂 | 用突变体破坏预测界面后检测功能丧失；用 co-IP 或 FRET 验证体内互作 | Abstract |
| SP1 敲低抑制心房分化 | SP1 是广泛表达的通用 TF，敲低可能通过非 NR2F2 相关途径影响心肌分化 | 如果 SP1 的作用与 NR2F2 无关，则「NR2F2 通过 SP1」的结论不成立 | 做 NR2F2 敲低 + SP1 过表达挽救实验；检测 SP1 敲低后 NR2F2 靶基因的全局变化 | Abstract |
| Proximity ligation 证明核内共定位 | 共定位不等于功能互作；可能只是两个蛋白在核内同一区域但无直接互作 | 物理接近是 tethering 的必要条件但非充分条件 | 结合 ChIP-seq 检测 NR2F2 是否在 SP1 结合位点富集；做 Hi-C/3C 验证染色质构象 | Abstract |
| 样本量与人种多样性未报告 | 人类胎儿心脏样本的供体数量、胎龄、性别、人种背景未知 | 影响结论的普适性 | 查阅全文补充材料 | 未提供 |

---

## 14 Agent 提炼的知识候选

> 面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题的可迁移知识：

1. **「双约束 GRN 对比」策略**：同时用 ATAC-seq 峰和 promoter 注释两种约束构建 GRN，比较差异来发现「非直接结合」的调控关系。可迁移到任何 TF–DNA 互作研究：当某 TF 在 promoter 约束下预测为靶基因调控者、但在 ATAC-seq 约束下消失时，提示该 TF 可能通过 tethering 而非直接结合发挥作用。
2. **AlphaFold 作为 GRN 推断的物理验证层**：在计算推断出 TF–TF 协同关系后，用 AlphaFold 预测蛋白-蛋白互作界面，作为实验前的筛选工具。可迁移到 TF–DNA 课题：预测 TF 与辅因子、共调控因子的物理互作，缩小实验验证范围。
3. **「TF 不直接结合 DNA，而是通过 tethering 另一 TF」的机制模板**：这一机制可能普遍存在于细胞类型特化中。在 TF–DNA 互作研究中，当 ChIP-seq 显示某 TF 在靶基因处富集但 motif 分析不支持直接结合时，应考虑 tethering 假说。
4. **多层级验证闭环设计**：计算推断 → 结构预测 → 独立数据交叉验证 → 功能敲低 → 物理互作验证。这一验证链可迁移到任何 TF–DNA 互作机制研究，确保结论的稳健性。
5. **「当前 vs. 潜在表观遗传状态」的对比思路**：作者比较了基于当前染色质状态（ATAC-seq）与潜在结合能力（promoter motif）的 GRN，这种「现实 vs. 潜力」的对比可迁移到 TF–DNA 结合预测中，用于区分「有结合能力」与「实际结合」。

---

## 15 与已有知识连接

- **NR2F2（COUP-TFII）**：已知的心房特化转录因子，在心脏发育中保守。本文挑战了其「直接结合 DNA」的默认假设，提出其通过 SP1 tethering 发挥作用。与已有文献中 NR2F2 作为孤儿核受体的 DNA 结合特性研究形成对比。
- **SP1**：广泛表达的通用转录因子，已知参与多种基因的组成性表达调控。本文将其置于心房特化的核心位置，提示通用 TF 在细胞类型特化中的新角色。
- **GRN 推断方法**：与 SCENIC、PIDC、GENIE3 等单细胞 GRN 推断工具属于同一方法学家族；本文的独特贡献在于「双约束对比」策略。
- **AlphaFold 蛋白-蛋白互作预测**：与 AlphaFold-Multimer、AlphaFold3 等工具的应用场景一致，本文将其用于 TF–TF 互作验证。
- **TF tethering 机制**：在类固醇受体（如 GR、ER）研究中已有 tethering 机制的报道（如 GR 通过 tethering AP-1、NF-κB 调控炎症基因）。本文将这一机制扩展到心脏发育中的 NR2F2-SP1。
- **iPSC 心房分化**：与已知的心房/心室心肌细胞分化方案（如维甲酸调控）相关，本文为优化分化方案提供了新靶点（SP1）。
- **[Analysis] 候选方向**：本文的「双约束对比」策略可能适用于其他细胞类型特化研究，如心室 vs. 传导系统、窦房结 vs. 心房肌等。

---

## 16 Agent 生成的研究候选

> 以下为基于本文提出的研究候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题。

### 候选 1：系统筛查「tethering 型 TF」的计算框架
- **名称**：Tethering-TF Screener（TTS）
- **来源局限/观察**：本文用双约束 GRN 对比发现 NR2F2-SP1 tethering，但该策略依赖人工比较，未系统化。
- **核心假设**：在任意细胞类型中，若某 TF 在 promoter 约束 GRN 中预测调控大量靶基因、但在 ATAC-seq 约束 GRN 中消失，则该 TF 可能通过 tethering 而非直接结合发挥作用。
- **初步方法**：开发自动化流程，对任意 scRNA-seq + scATAC-seq 数据构建双约束 GRN，输出「tethering 候选 TF」列表；用 AlphaFold-Multimer 批量预测候选 TF 与已知 DNA 结合 TF 的互作。
- **验证方式**：在多个公开数据集（如心脏、肝脏、脑发育）中测试，用 ChIP-seq 和突变实验验证 top 候选。
- **创新状态**：unverified（本文仅展示了单个案例，未系统化）

### 候选 2：AlphaFold 预测的 TF–TF 互作界面突变验证
- **名称**：Interface-Mutant Functional Assay（IMFA）
- **来源局限/观察**：本文用 AlphaFold 预测 NR2F2-SP1 互作，但未做界面突变验证。
- **核心假设**：破坏 AlphaFold 预测的 NR2F2-SP1 互作界面将消除 NR2F2 对心房基因的调控，但不影响 SP1 的全局功能。
- **初步方法**：在 iPSC 心房分化体系中，用 CRISPR 引入 NR2F2 互作界面点突变，检测心房标志物表达和 NR2F2 靶基因变化。
- **验证方式**：比较突变体与野生型的转录组、ChIP-seq 和 proximity ligation 信号。
- **创新状态**：unverified

### 候选 3：TF–DNA 直接结合 vs. tethering 的机器学习分类器
- **名称**：Direct-vs-Tether Classifier（DvT）
- **来源局限/观察**：本文的核心发现依赖于「直接结合 vs. tethering」的区分，但缺乏可推广的判别工具。
- **核心假设**：TF 的 DNA 结合域特征、ChIP-seq 峰形、motif 富集强度、以及蛋白互作网络特征可共同区分「直接结合」与「tethering」两种模式。
- **初步方法**：收集已发表的 ChIP-seq 数据，标注直接结合与 tethering 事件；提取特征（motif 富集、峰宽、共结合 TF、蛋白结构域）；训练梯度提升或图神经网络分类器。
- **验证方式**：在留出数据集上评估 AUC；用本文 NR2F2-SP1 作为外部验证案例。
- **创新状态**：unverified

### 候选 4：MD 模拟验证 TF–TF tethering 的动态稳定性
- **名称**：Tethering Dynamics via MD（TetherMD）
- **来源局限/观察**：本文用 AlphaFold 预测静态结构，未评估 tethering 复合物的动态稳定性。
- **核心假设**：NR2F2-SP1 的 tethering 复合物在 MD 模拟中表现出稳定的结合界面，且该稳定性与功能相关性一致。
- **初步方法**：用 AlphaFold 预测的 NR2F2-SP1 复合物结构作为起点，进行 μs 级粗粒化或全原子 MD 模拟，计算结合自由能和界面残基接触图。
- **验证方式**：比较 MD 预测的稳定界面与突变实验的功能影响；与已知非功能互作对比。
- **创新状态**：unverified

### 候选 5：SP1 作为通用「tethering 锚点」的泛组织验证
- **名称**：SP1-Anchor Hypothesis Test（SAHT）
- **来源局限/观察**：本文发现 SP1 作为 NR2F2 的 DNA 结合锚点，但 SP1 是广泛表达的通用 TF，可能在其他组织中也有类似功能。
- **核心假设**：SP1 在多种细胞类型中作为「tethering 锚点」，帮助不直接结合 DNA 的 TF 调控靶基因。
- **初步方法**：在多个公开 scRNA-seq + scATAC-seq 数据集中，用双约束 GRN 对比筛查 SP1 相关的 tethering 候选；用 AlphaFold 批量预测。
- **验证方式**：选择 top 候选在对应细胞系中做 SP1 敲低 + 靶基因检测。
- **创新状态**：unverified