## 01 基本信息

- **标题**：In-silico assessment of novel peptidomimetics inhibitor targeting STAT3 and STAT4 N-terminal domain dimerization: A comprehensive study using molecular docking, molecular dynamics simulation, and binding free energy analysis
- **作者**：Shree, Megha; Vaishnav, Jayanti; Gurudayal; Ampapathi, Ravi Sankar
- **单位**：未提供（根据通讯作者 Ampapathi, Ravi Sankar 推测可能为印度机构，但原文未提供）
- **期刊/平台**：Biochemical and Biophysical Research Communications (BBRC)
- **年份**：2024
- **论文类型**：计算/模拟研究（in-silico 研究）
- **领域**：蛋白质-蛋白质相互作用抑制；JAK-STAT 信号通路；肽模拟物设计
- **关键词**：STAT3；STAT4；N-terminal domain；peptidomimetics；molecular docking；molecular dynamics；MM/PBSA
- **DOI/arXiv 号**：10.1016/j.bbrc.2024.150584
- **代码**：未提供
- **数据**：未提供（PDB 结构来源未在摘要中说明）
- **阅读日期**：2025-01-15（基于当前日期）
- **在「蛋白质-DNA 互作(聚焦 TF–DNA 结合机制) × AI 方法/物理模拟」方向中的位置**：本文聚焦 STAT3/STAT4 的 N-terminal domain（NTD）二聚化界面，通过分子对接 + MD 模拟 + MM/PBSA 的经典物理模拟流程，设计 β³-氨基酸肽模拟物以阻断二聚化。与 TF–DNA 结合机制的直接关联在于：STAT 蛋白是信号依赖性转录因子，其 NTD 二聚化是 DNA 结合和转录激活的前提；本文通过阻断二聚化间接抑制 STAT 的 DNA 结合功能。方法上属于「物理模拟（对接 + MD）」而非 AI 方法，可作为 TF 二聚化界面抑制剂的经典计算流程参考。

---

## 02 一句话总结

本文通过分子对接、分子动力学模拟和 MM/PBSA 结合自由能计算，设计并评估了三种含 β³-氨基酸的肽模拟物（Peptide-A/B/C），证明其能结合 STAT3 和 STAT4 的 N-terminal domain 二聚化界面（interface II），从而有潜力阻断 STAT 二聚化和核转位。

---

## 03 研究问题

- **具体问题**：能否设计出靶向 STAT3 和 STAT4 N-terminal domain（NTD）二聚化界面的肽模拟物抑制剂，并通过计算手段验证其结合能力？
- **为什么重要**：JAK-STAT 通路失调与多种癌症相关；STAT 蛋白 NTD 的二聚化是 STAT 活化、核转位和 DNA 结合的关键步骤。靶向 NTD 二聚化界面可阻断 STAT 功能，是一种有别于传统 SH2 域或 DNA 结合域抑制的新策略。
- **现有方法为何不足**：传统抑制剂多靶向 STAT3 的 SH2 域或 DNA 结合域，但存在选择性差、细胞通透性低等问题；NTD 二聚化界面作为靶点尚未被充分开发，且缺乏系统的计算设计流程。
- **精确研究问题（Can...?）**：Can peptidomimetic foldamers containing β³-amino acids, designed to mimic interface II residues of STAT3/STAT4 NTD dimers, bind stably to the NTDs and disrupt dimerization, as assessed by docking, MD simulation, and MM/PBSA free energy calculations?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文摘要及该领域公开知识构建，标注为「经外部核验」的部分基于已知文献，其余为「仅本文框架」。

1. **JAK-STAT 通路与癌症**（经外部核验）：JAK-STAT 是细胞因子信号传导的核心通路，STAT3/STAT4 的异常激活与多种实体瘤和血液肿瘤相关。
2. **STAT 抑制剂发展**（经外部核验）：
   - 第一代：靶向 SH2 域的小分子（如 Stattic、S3I-201），但选择性差。
   - 第二代：靶向 DNA 结合域或 NTD 的肽类/肽模拟物，试图提高特异性。
3. **NTD 二聚化作为靶点**（经外部核验）：STAT 的 NTD（约 1-130 残基）介导非磷酸化 STAT 的二聚化（interface I 和 interface II），是 STAT 核转位和 DNA 结合的前提。靶向 NTD 二聚化可同时影响 STAT 的多种功能。
4. **肽模拟物与 β³-氨基酸**（经外部核验）：β³-氨基酸可形成稳定的折叠体（foldamer），比天然肽更抗蛋白酶降解，且可精确呈现侧链空间排列，适合模拟蛋白-蛋白相互作用（PPI）的热点残基。
5. **计算方法**（经外部核验）：分子对接（AutoDock/Vina 等）用于初筛；MD 模拟（AMBER/GROMACS）用于评估复合物稳定性；MM/PBSA 用于结合自由能估算。
6. **本文主张的位置**（仅本文框架）：将上述要素整合——以 interface II 为模板设计 β³-氨基酸肽模拟物，用对接 + MD + MM/PBSA 系统评估其与 STAT3/STAT4 NTD 的结合，属于「PPI 抑制剂计算设计」在 STAT 家族上的新应用。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| STAT 抑制剂选择性差 | 传统小分子多靶向 SH2 域，在 STAT 家族成员间保守性高，导致交叉反应 | 作者未在摘要中明确解释，但暗示 NTD 界面更具特异性 | 摘要提及「strategic targeting of the N-terminal domain of STATs has emerged as a promising tactic」 |
| NTD 二聚化界面难以成药 | 蛋白-蛋白相互作用界面平坦、疏水，传统小分子难以高亲和结合 | 作者采用肽模拟物（foldamer）来模拟界面残基，以克服 PPI 靶点的成药性挑战 | 摘要：「judiciously designed a series of peptidomimetics that encompass beta(3)-amino acids, bearing side chains that mimic the residues within interface II」 |
| 计算设计缺乏实验验证 | 仅靠对接打分不可靠，需 MD 和自由能计算确认 | 作者采用多级计算流程（对接 → MD → MM/PBSA）以增强可信度 | 摘要：「subsequently computing the binding free energy utilizing MM/PBSA calculations」 |
| STAT3 与 STAT4 的差异 | 两者 NTD 序列和结构有差异，需分别评估 | 作者同时评估了 STAT3 和 STAT4 两个靶点 | 摘要：「assessed the binding affinity of these designed peptidomimetics toward both the NTDs」 |

---

## 06 核心思想

### 1) 表面方法
设计含 β³-氨基酸的肽模拟物（Peptide-A/B/C），其侧链模拟 STAT3/STAT4 NTD 二聚体 interface II 的关键残基；通过分子对接评估结合模式，MD 模拟评估复合物稳定性，MM/PBSA 计算结合自由能。

### 2) 核心洞察
STAT 的 NTD 二聚化界面（interface II）包含一组可被肽模拟物「模仿」的热点残基；通过将天然界面残基的侧链移植到 β³-氨基酸骨架上，可以设计出能竞争性结合 NTD 并阻断二聚化的分子。β³-氨基酸的骨架刚性和侧链呈现能力使其比天然肽更适合作为 PPI 抑制剂支架。

### 3) 可能的普适教训 [Analysis]
- 对于 TF 二聚化界面（如 STAT、bZIP、bHLH 等），「界面残基模拟」策略可迁移：先解析二聚体结构，识别界面热点残基，再设计含非天然氨基酸的肽模拟物。
- 计算流程「对接 → MD → MM/PBSA」是 PPI 抑制剂评估的经典基线，但需注意：对接打分仅用于初筛，MD 稳定性 + 自由能计算才是关键判据。
- β³-氨基酸 foldamer 可作为「肽类抑制剂」的通用支架，尤其适合靶向平坦的蛋白-蛋白界面。

---

## 07 方法总览

- **输入**：
  - STAT3 和 STAT4 NTD 的三维结构（来源未在摘要中说明，推测为 PDB 晶体结构或同源建模）
  - interface II 的残基信息（用于设计肽模拟物）
  - 设计的肽模拟物序列（Peptide-A/B/C，含 β³-氨基酸）
- **输出**：
  - 肽模拟物与 STAT3/STAT4 NTD 的结合模式
  - 复合物的 MD 模拟轨迹和稳定性评估
  - MM/PBSA 结合自由能
- **模块**：
  1. 肽模拟物设计（基于 interface II 残基模拟）
  2. 分子对接（评估结合亲和力和结合模式）
  3. MD 模拟（评估复合物稳定性、构象变化）
  4. MM/PBSA 计算（量化结合自由能）
- **训练**：不适用（无机器学习/训练过程）
- **工具**：未在摘要中说明（推测为 AutoDock/Vina、AMBER/GROMACS、MM/PBSA 工具）
- **反馈回路**：无（一次性计算流程，无迭代优化）
- **假设**：
  - interface II 是 NTD 二聚化的关键界面
  - 肽模拟物能模拟 interface II 残基的侧链排列
  - 对接 + MD + MM/PBSA 能可靠评估结合亲和力
- **文字流程**：
  1. 从 STAT3/STAT4 NTD 二聚体结构中提取 interface II 残基
  2. 设计含 β³-氨基酸的肽模拟物，使侧链模拟 interface II 热点残基
  3. 将肽模拟物对接到 STAT3/STAT4 NTD 单体上
  4. 对最优对接复合物进行 MD 模拟（评估稳定性）
  5. 用 MM/PBSA 计算结合自由能
  6. 比较三种肽模拟物对 STAT3 和 STAT4 的结合差异

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 肽模拟物设计 | 基于 interface II 残基设计 β³-氨基酸 foldamer | 天然肽易降解，β³-氨基酸可提高稳定性并精确呈现侧链 | 输入：interface II 残基；输出：Peptide-A/B/C 序列 | 摘要：「judiciously designed a series of peptidomimetics that encompass beta(3)-amino acids」 | 预期影响：移除后无法获得候选抑制剂（预期效应，未实测） |
| 分子对接 | 评估肽模拟物与 NTD 的结合模式和亲和力 | 初筛候选分子，确定结合构象 | 输入：肽模拟物 + NTD 结构；输出：对接打分、结合构象 | 摘要：「Employing molecular docking techniques; we have assessed the binding affinity」 | 预期影响：移除后无法获得初始结合构象，MD 无起点（预期效应） |
| MD 模拟 | 评估复合物在生理条件下的稳定性和构象变化 | 对接结果可能为局部最优，MD 可验证动态稳定性 | 输入：对接复合物；输出：轨迹、RMSD/RMSF 等 | 摘要：「conducted an evaluation of the stability and conformational alterations within the docked complexes over an extensive Molecular Dynamics」 | 预期影响：移除后无法判断复合物是否动态稳定（预期效应） |
| MM/PBSA 计算 | 量化结合自由能 | 提供比对接打分更可靠的亲和力排序 | 输入：MD 轨迹；输出：ΔG_binding | 摘要：「subsequently computing the binding free energy utilizing MM/PBSA calculations」 | 预期影响：移除后缺乏定量亲和力指标（预期效应） |

> 注：摘要中未提供消融实验或模块级对比数据，所有影响均为「预期效应」而非「实测消融效应」。

---

## 09 关键公式符号

本文摘要中未提供具体公式。基于方法描述，MM/PBSA 计算涉及的标准公式如下（标注为 [Analysis] 基于领域通用知识，非原文提供）：

- **MM/PBSA 结合自由能**：
  ΔG_bind = ΔE_MM + ΔG_solv - TΔS
  - ΔE_MM = ΔE_int + ΔE_vdW + ΔE_ele（分子力学能量：内能、范德华、静电）
  - ΔG_solv = ΔG_PB + ΔG_SA（极性溶剂化能 + 非极性溶剂化能）
  - TΔS：熵贡献（通常用正态模分析或忽略）
  - **用途**：估算肽模拟物与 NTD 的结合亲和力
  - **来源**：未在原文中提供，[Analysis] 基于 MM/PBSA 领域标准方法

- **分子对接打分函数**：具体形式未提供（取决于所用软件，如 AutoDock Vina 的 ΔG = ...），原文未给出。

---

## 10 实验设计与证据链

- **数据集/群体**：STAT3 和 STAT4 的 NTD 结构（具体 PDB ID 未在摘要中提供）
- **规模**：3 种肽模拟物（Peptide-A/B/C）× 2 个靶点（STAT3/STAT4）
- **指标**：对接打分、MD 稳定性指标（RMSD/RMSF 等，未具体说明）、MM/PBSA 结合自由能
- **基线**：未在摘要中说明（无阳性对照或已知抑制剂对比）
- **预算**：不适用（计算研究）
- **骨干/仪器**：未提供（计算集群/软件未说明）
- **oracle 输入**：不适用（无实验验证）
- **评测协议**：未在摘要中详细说明

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| 分子对接 | 肽模拟物能结合 STAT3/STAT4 NTD | 三种肽模拟物 vs 两个靶点 | 摘要称「assessed the binding affinity」，未给出具体数值 | 肽模拟物与 NTD 有结合倾向 | 无法判断结合强度是否优于已知抑制剂 | 摘要 |
| MD 模拟 | 复合物在动态条件下稳定 | 对对接复合物进行长时间 MD | 摘要称「evaluation of the stability and conformational alterations」，未给出具体数据 | 复合物在 MD 时间尺度内保持稳定 | 无法判断是否达到实验级稳定性（μs 级） | 摘要 |
| MM/PBSA | 结合自由能支持有效结合 | 计算三种肽模拟物的 ΔG_bind | 摘要称「demonstrate that the peptidomimetic foldamers... exhibit a propensity to bind」，未给出数值 | 结合自由能有利于结合 | 无法判断自由能是否达到药物候选阈值 | 摘要 |

> 注：摘要中未提供任何具体数值（对接分数、RMSD、ΔG 值等），所有结果描述均为定性。

---

## 11 结论正确解读

- **任务范围**：仅限计算评估（in-silico），无实验验证（无 SPR、ITC、细胞实验等）。
- **oracle/真值输入**：无实验真值；结构来源未说明，可能影响结果可靠性。
- **端到端状态**：非端到端——仅完成计算筛选和评估，未进入湿实验验证阶段。
- **算力成本**：未提供（MD 模拟时长、计算资源未说明）。
- **历史数据依赖**：依赖 STAT3/STAT4 NTD 的已知结构（PDB），但具体结构未说明。
- **模型依赖**：结果依赖对接软件、力场、MD 模拟参数、MM/PBSA 方法的选择，这些均未在摘要中说明。
- **最难情形**：PPI 抑制剂的计算评估通常高估结合亲和力；MD 模拟时间尺度有限，无法捕捉构象重排的完整图景。
- **群体/领域边界**：结论仅适用于 STAT3/STAT4 NTD 二聚化界面的计算评估，不能推广到其他 STAT 家族成员或实验条件下的真实抑制效果。
- **不确定性**：摘要中未提供误差估计、重复实验或统计显著性分析。

**有边界的复述**：在计算模拟的框架下，三种含 β³-氨基酸的肽模拟物显示出与 STAT3/STAT4 NTD 结合的倾向，且 MD 模拟和 MM/PBSA 分析支持其结合稳定性；但该结论未经实验验证，且具体数值和参数未在摘要中披露。

---

## 12 作者自认局限

在提供的摘要中，作者未明确列出局限性。摘要仅以「underscore the potential of these meticulously designed peptidomimetics as potential candidates meriting further exploration」结尾，暗示需要进一步研究，但未具体说明局限。

**作者提及的相关约束**（非正式局限）：
- 摘要中「meriting further exploration in the realm of cancer prevention and management」暗示当前结果仅为初步计算发现，需进一步验证。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 摘要中无任何具体数值（对接分数、RMSD、ΔG） | 可能选择性报告定性结论，或数值不显著 | 无法独立评估结合亲和力的强度 | 查阅全文获取具体数值和误差范围 | 摘要全文 |
| 未说明 STAT3/STAT4 NTD 结构的来源 | 若使用同源建模结构，可能引入构象偏差 | 结构质量直接影响对接和 MD 结果可靠性 | 核对 PDB ID 和结构分辨率 | 摘要未提供 |
| 未提及阳性对照或已知抑制剂对比 | 无法判断肽模拟物是否优于现有抑制剂 | 缺乏基准使「potential」claim 缺乏参照 | 与已知 STAT3 抑制剂（如 Stattic）进行对接和 MD 对比 | 摘要未提供 |
| 未说明 MD 模拟时长和力场 | 短模拟（<100 ns）可能不足以评估结合稳定性 | 模拟时长影响结论可靠性 | 查阅 Methods 获取模拟参数 | 摘要未提供 |
| 未讨论 β³-氨基酸肽模拟物的细胞通透性和代谢稳定性 | 即使计算结合良好，细胞实验可能失败 | PPI 抑制剂需同时满足结合亲和力和类药性 | 进行 ADMET 预测或实验评估 | 摘要未提供 |
| 仅评估 NTD 二聚化界面，未考虑 STAT 其他功能域（SH2、DBD） | 阻断 NTD 二聚化可能不足以完全抑制 STAT 功能 | STAT 功能是多域协同的，单一界面抑制可能不充分 | 设计多靶点策略或联合抑制 | [Analysis] 基于 STAT 结构-功能知识 |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **界面残基模拟策略（可迁移）**：本文的核心思路——从二聚体结构中提取 interface 热点残基，用非天然氨基酸（β³-氨基酸）模拟其侧链排列——可直接迁移到 TF–DNA 结合机制研究。例如，对于 bZIP 或 bHLH 类 TF 的二聚化界面，可设计类似的肽模拟物阻断二聚化，从而间接抑制 DNA 结合。
2. **计算流程「对接 → MD → MM/PBSA」作为 PPI 抑制剂评估基线**：该流程是 TF 二聚化界面抑制剂计算评估的经典范式。迁移到 TF–DNA 互作课题时，可将「对接靶点」从蛋白-蛋白界面改为蛋白-DNA 界面，或评估 TF 二聚化对 DNA 结合的影响。
3. **β³-氨基酸 foldamer 作为 PPI 抑制剂支架**：β³-氨基酸的骨架刚性和蛋白酶抗性使其成为 PPI 抑制剂的优选支架。在 TF 二聚化界面抑制剂设计中，可借鉴此策略提高候选物的代谢稳定性。
4. **多靶点评估（STAT3 和 STAT4 并行）**：本文同时评估了 STAT3 和 STAT4 两个同源靶点，可迁移到 TF 家族（如 AP-1 家族成员）的选择性抑制剂设计——评估候选物对家族内不同成员的选择性。
5. **MM/PBSA 作为亲和力排序工具**：在缺乏实验数据时，MM/PBSA 可用于候选物排序。迁移到 TF–DNA 互作课题时，可用于评估突变对 TF-DNA 结合自由能的影响。

---

## 15 与已有知识连接

- **STAT 结构与功能**（经外部核验）：STAT 蛋白包含 NTD、coiled-coil 域、DNA 结合域、SH2 域和转录激活域。NTD 介导的二聚化是 STAT 核转位和 DNA 结合的前提（参考文献：Darnell, 1997; Levy & Darnell, 2002）。
- **PPI 抑制剂设计**（经外部核验）：β³-氨基酸 foldamer 已被用于多种 PPI 靶点（如 p53-MDM2、Bcl-2 家族）的抑制剂设计（参考文献：Gellman, 1998; Horne & Gellman, 2008）。
- **TF 二聚化与 DNA 结合**（经外部核验）：bZIP（如 AP-1、CREB）和 bHLH（如 Myc-Max）类 TF 的二聚化是 DNA 结合的前提，二聚化界面抑制剂可间接调控基因表达（参考文献：Grigoryan & Keating, 2008）。
- **计算方法在 TF-DNA 互作中的应用**（经外部核验）：分子对接和 MD 模拟已广泛用于 TF-DNA 结合机制研究（如 protein-DNA docking、MM/PBSA 计算 TF-DNA 结合自由能）。
- **与本文的关联**：本文虽聚焦 STAT 蛋白（信号依赖性 TF），但其「阻断二聚化 → 抑制 DNA 结合」的逻辑与 bZIP/bHLH 类 TF 的调控机制高度相似，方法可迁移。

---

## 16 研究想法

> **Agent 生成的研究候选**

### 候选 1：基于界面残基模拟的 bZIP 类 TF 二聚化抑制剂设计
- **名称**：bZIP-dimer-breaker peptidomimetics
- **来源局限/观察**：本文对 STAT3/STAT4 NTD 的界面残基模拟策略可迁移到 bZIP 类 TF（如 c-Jun/c-Fos、CREB），其亮氨酸拉链二聚化界面已有大量结构数据。
- **核心假设**：设计含 β³-氨基酸的肽模拟物模拟 bZIP 二聚化界面的热点残基，可竞争性结合单体并阻断二聚化，从而抑制 DNA 结合。
- **相对本文的增量**：将靶点从 STAT 扩展到 bZIP 家族；可结合深度学习（如 AlphaFold 或 proteinMPNN）优化肽模拟物序列。
- **初步方法**：解析 bZIP 二聚体结构 → 识别界面热点残基 → 设计 β³-氨基酸肽模拟物 → 对接 + MD + MM/PBSA 评估 → 与已知 bZIP 抑制剂对比。
- **验证方式**：计算结合自由能 + 与实验已知的 bZIP 抑制剂（如有）对比；后续可进行 SPR/ITC 实验验证。
- **创新状态**：unverified（方法迁移，但具体靶点应用未验证）

### 候选 2：TF-DNA 结合界面 vs 二聚化界面的选择性抑制策略
- **名称**：Dual-interface targeting for TF inhibition
- **来源局限/观察**：本文仅靶向 NTD 二聚化界面，未考虑 TF 的 DNA 结合域。对于某些 TF，直接阻断 DNA 结合可能更有效。
- **核心假设**：对同一 TF，比较「二聚化界面抑制剂」和「DNA 结合界面抑制剂」的效果差异，可指导抑制剂设计策略选择。
- **相对本文的增量**：扩展为双界面比较研究；可引入深度学习打分函数（如 DeepDock 或 graph neural network-based scoring）提高对接精度。
- **初步方法**：对目标 TF（如 STAT3 或 p53），分别设计二聚化界面和 DNA 结合界面的肽模拟物/小分子 → 对接 + MD + MM/PBSA → 比较结合自由能和特异性。
- **验证方式**：计算比较 + 实验验证（EMSA 检测 DNA 结合抑制，共免疫沉淀检测二聚化抑制）。
- **创新状态**：unverified

### 候选 3：深度学习增强的肽模拟物序列优化
- **名称**：DL-enhanced peptidomimetic design for TF dimerization interfaces
- **来源局限/观察**：本文的肽模拟物设计依赖人工选择 interface 残基，未使用生成模型。深度学习（如 proteinMPNN、DiffAb）可自动生成高亲和力肽序列。
- **核心假设**：用深度学习生成模型优化 β³-氨基酸肽模拟物序列，可提高与 STAT3/STAT4 NTD 的结合亲和力，优于人工设计。
- **相对本文的增量**：引入 AI 方法替代人工设计；可同时优化序列和侧链修饰。
- **初步方法**：收集 STAT3/STAT4 NTD 结构 → 用 proteinMPNN 或类似模型生成候选肽序列 → 筛选含 β³-氨基酸的变体 → 对接 + MD + MM/PBSA 评估 → 与本文 Peptide-A/B/C 对比。
- **验证方式**：计算对比 + 实验验证（如荧光偏振或 SPR）。
- **创新状态**：unverified（AI 方法在 PPI 抑制剂设计已有先例，但针对 STAT NTD 的具体应用未验证）

### 候选 4：MD 模拟揭示 TF 二聚化动态对 DNA 结合的影响
- **名称**：Conformational dynamics of TF dimerization and DNA binding
- **来源局限/观察**：本文仅评估了肽模拟物与 NTD 的结合，未研究二聚化动态如何影响 DNA 结合。MD 模拟可揭示这一机制。
- **核心假设**：TF 二聚化的构象动态（如 interface 开合）直接影响 DNA 结合亲和力；阻断二聚化可间接改变 DNA 结合动力学。
- **相对本文的增量**：从静态结合评估扩展到动态机制研究；可结合增强采样方法（如 metadynamics）或 Markov state models。
- **初步方法**：对 STAT3/STAT4 NTD 二聚体进行长时间 MD 模拟 → 分析 interface 动态 → 与 DNA 结合域进行对接 → 比较二聚化状态 vs 单体状态的 DNA 结合能力。
- **验证方式**：计算分析 + 与实验突变数据对比（如 interface 突变体的 DNA 结合活性）。
- **创新状态**：unverified

### 候选 5：MM/PBSA 与深度学习打分函数的系统比较
- **名称**：Benchmarking MM/PBSA vs DL scoring for TF dimerization inhibitors
- **来源局限/观察**：本文依赖 MM/PBSA，但该方法对 PPI 抑制剂的预测精度有限。深度学习打分函数（如 DeepAffinity、GNINA）可能更优。
- **核心假设**：在 STAT3/STAT4 NTD-肽模拟物体系上，深度学习打分函数的排序能力优于 MM/PBSA。
- **相对本文的增量**：方法学比较，为 TF 二聚化抑制剂计算评估提供更优工具。
- **初步方法**：用本文的肽模拟物体系作为测试集 → 分别用 MM/PBSA 和多种 DL 打分函数评估 → 比较排序一致性和与实验数据的相关性。
- **验证方式**：计算对比 + 与已知实验结合数据（如有）对比。
- **创新状态**：unverified（DL 打分函数在蛋白-配体体系已有验证，但在 TF 二聚化界面抑制剂上未系统比较）