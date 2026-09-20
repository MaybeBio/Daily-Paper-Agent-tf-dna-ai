## 01 基本信息

- **标题**：Genomic foundation model-derived disruption profiling links somatic mutations to cancer biology and clinical outcomes
- **作者**：Nayak A; Lee T; Agarwal V; Georgakopoulos-Soares I
- **单位**：未提供（medRxiv 预印本未列出完整单位信息）
- **期刊/平台**：medRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：癌症基因组学 × 基因组基础模型（genomic foundation models）
- **关键词**：somatic mutations, disruption profiling, AlphaGenome, AlphaMissense, cancer genomics, regulatory effects, survival
- **DOI/ID**：10.64898/2026.09.15.26363174
- **代码**：未提供
- **数据**：TCGA（dbGaP phs000178.v11.p8）、TCGA-CDR、IntOGen、POG570、Cancer hotspots v2（均在 Data Availability 中列出）
- **阅读日期**：2026-09-16（按预印本日期推断）
- **在该课题方向中的位置**：本文属于「基因组基础模型（sequence-to-function models）应用于癌症体细胞突变功能解读」方向。与「蛋白质-DNA 互作（TF–DNA 结合机制）× AI」课题的直接关联在于：本文使用 AlphaGenome 预测的**转录因子结合（transcription factor binding）**和**染色质可及性（chromatin accessibility）**作为 disruption 模态之一，并发现染色质可及性 disruption 与生存关联最强——这为 TF–DNA 结合扰动如何影响癌症表型提供了大规模、跨癌种的证据。方法上，其「aggregate variant-level predictions to patient-gene profiles」的框架可迁移到 TF–DNA 结合扰动的患者级聚合分析。

---

## 02 一句话总结

本文使用 AlphaGenome 和 AlphaMissense 两个序列到功能模型，对 TCGA 33 种癌症类型 8,800 名患者的体细胞突变进行蛋白层面和调控层面的 disruption 预测，并将变异级预测聚合为患者-基因 disruption profiles，发现这些 profiles 反映组织来源、癌症类型和微卫星不稳定状态，且在缺乏热点突变的患者中，调控 disruption（尤其染色质可及性）与总生存期相关。

---

## 03 研究问题

- **具体问题**：体细胞突变是否可以通过累积产生**部分性、基因水平的 disruption**（而非传统的二元驱动/非驱动分类），并且这种 disruption 是否具有生物学和临床后果？
- **为什么重要**：传统癌症基因组学聚焦于单个突变（尤其是热点突变和驱动突变），忽略了大量非热点突变可能通过调控元件（如 TF 结合位点、染色质可及性区域）产生累积效应。如果这种「连续、多维」的 disruption 观点成立，将改变癌症基因优先排序和患者分层的方式。
- **现有方法为何不足**：传统方法依赖 recurrence 或功能实验注释来识别驱动基因，无法量化非热点突变的调控效应；且缺乏从 DNA 序列直接预测多种分子表型（蛋白功能、染色质、TF 结合、剪接）的整合框架。
- **精确研究问题（Can...?）**：Can genomic foundation model-derived disruption profiles, aggregated from variant-level sequence-to-function predictions, capture biologically and clinically meaningful gene-level perturbation beyond discrete driver mutations in cancer?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架及该领域已知发展，标注「经外部核验」的部分为领域共识。

1. **阶段一：单变异功能注释（约 2015–2020）**
   - 代表方法：PolyPhen-2、SIFT、CADD、ClinVar 注释
   - 优点：可扩展、计算快
   - 局限：主要针对蛋白编码效应，缺乏调控层面预测；对非编码突变覆盖弱
   - 经外部核验

2. **阶段二：序列到功能深度学习模型（约 2021–2024）**
   - 代表方法：Enformer、Basenji、AlphaMissense
   - 优点：直接从 DNA 序列预测表达、染色质状态、TF 结合、剪接等
   - 局限：多为单模态预测，缺乏跨模态整合；变异级预测未系统聚合到患者/基因水平
   - 经外部核验

3. **阶段三：基因组基础模型（约 2024–2026）**
   - 代表方法：AlphaGenome（本文使用）、Evo、Nucleotide Transformer
   - 优点：多模态、可迁移、可同时预测蛋白和调控效应
   - 局限：预印本阶段，验证尚不充分
   - 经外部核验（AlphaGenome 本身为本文所用，其发布细节未提供）

4. **本文主张的位置**：首次将 AlphaGenome + AlphaMissense 的变异级预测**系统聚合为患者-基因 disruption profiles**，并验证其与癌症类型、微卫星状态和生存的关联——即从「变异中心」转向「基因水平连续 disruption」视角。
   - 仅本文框架

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单变异视角忽略累积效应 | 癌症基因组学聚焦单个突变，忽略多个突变在基因水平的累积 disruption | 传统驱动基因概念是离散的（driver/non-driver），缺乏连续度量 | Abstract: "Cancer genomics has concentrated on individual mutations, overlooking whether somatic mutations can accumulate to produce partial, gene-level disruption" |
| 非热点突变功能解读缺失 | 非热点突变在大多数癌种中表现出更大的调控效应，但传统方法无法量化 | 现有注释工具主要覆盖蛋白编码效应，调控预测能力有限 | Abstract: "non-hotspot mutations exhibited larger regulatory effects across most cancer types" |
| 多模态 disruption 缺乏整合框架 | 转录、染色质、TF 结合、剪接等 disruption 分散在不同模型中，未统一 | 缺乏将变异级预测聚合为患者-基因水平 profiles 的方法 | Abstract: "aggregated the variant-level predictions to construct patient-gene disruption profiles capturing transcriptional activity, chromatin accessibility, transcription factor binding, and splicing" |
| 驱动基因之外的临床信号被忽略 | 缺乏热点突变的患者中仍存在与生存相关的 disruption 信号 | 传统分析仅关注 recurrent hotspot mutations，忽略非热点突变的累积效应 | Abstract: "Among patients lacking recurrent hotspot mutations in a given cancer gene, higher predicted disruption was associated with overall survival" |

---

## 06 核心思想

### 1) 表面方法
使用两个预训练基因组基础模型（AlphaGenome、AlphaMissense）对 TCGA 体细胞突变进行变异级 disruption 预测，覆盖蛋白功能、转录活性、染色质可及性、TF 结合和剪接五个模态；然后将变异级预测按患者-基因聚合为 disruption profiles，并与临床表型（癌症类型、微卫星状态、生存）关联。

### 2) 核心洞察
体细胞突变对基因的扰动是**连续、多维**的：热点突变富集于强蛋白效应，而非热点突变通过调控模态（尤其染色质可及性和 TF 结合）产生广泛但较弱的 disruption。这些调控 disruption 在缺乏经典驱动突变的患者中仍携带临床预后信息——即「基因被部分扰动」本身就是一个有意义的生物学状态。

### 3) 可能的普适教训 [Analysis]
- **聚合层级决定生物学可解释性**：变异级预测 → 基因级聚合 → 患者级关联，这种「从局部到整体」的聚合策略是连接序列模型输出与临床表型的通用范式，可迁移到 TF–DNA 结合扰动的患者级分析。
- **多模态互补优于单模态**：蛋白效应和调控效应在不同突变类型中分布不同，单一模态会遗漏信号。对 TF–DNA 结合研究而言，同时考虑结合位点突变对 TF 结合的直接影响和下游染色质/表达变化是必要的。
- **「无驱动突变」不等于「无功能后果」**：在缺乏经典驱动事件的患者中寻找弱但累积的信号，是精准医学中扩大可靶向人群的潜在路径。

---

## 07 方法总览

- **输入**：TCGA 体细胞突变数据（8,800 患者，33 癌种）；参考基因组序列
- **输出**：患者-基因 disruption profiles（5 个模态：蛋白功能、转录活性、染色质可及性、TF 结合、剪接）；与癌症类型、MSI 状态、生存的关联
- **模块**：
  1. 变异级 disruption 预测（AlphaGenome + AlphaMissense）
  2. 模态特异性聚合（variant → gene → patient）
  3. 临床关联分析（癌症类型、MSI、生存）
- **训练**：未提供（使用预训练模型，未见微调描述）
- **工具**：AlphaGenome、AlphaMissense
- **反馈回路**：未提供（未见迭代优化或验证回路描述）
- **假设**：序列到功能模型的预测值可近似反映体内真实的分子 disruption 效应；不同模态的 disruption 可加性地聚合为基因水平度量

**文字流程**：
1. 从 TCGA 获取体细胞突变和临床数据
2. 对每个变异，使用 AlphaGenome 预测调控模态 disruption（转录、染色质、TF 结合、剪接），使用 AlphaMissense 预测蛋白功能 disruption
3. 将变异级预测按基因聚合，再按患者聚合，构建患者-基因 disruption profiles
4. 分析 profiles 与癌症类型、组织来源、MSI 状态的关系
5. 在缺乏热点突变的患者中检验 disruption 与总生存期的关联
6. 在独立治疗注释队列（POG570）中验证基因水平 disruption 与治疗亚组生存的关联

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 变异级 disruption 预测（AlphaGenome） | 从 DNA 序列预测调控模态 disruption（转录、染色质、TF 结合、剪接） | 非热点突变的调控效应无法用传统注释工具量化 | 输入：突变序列上下文；输出：各调控模态的 disruption 分数 | Abstract: "non-hotspot mutations exhibited larger regulatory effects across most cancer types" | 预期影响：失去所有调控模态信息，仅剩蛋白效应，无法捕捉非热点突变的累积信号 [Analysis：预期效应，未提供消融实验] |
| 变异级 disruption 预测（AlphaMissense） | 预测错义突变的蛋白功能影响 | 热点突变主要富集于蛋白效应，需要蛋白层面的量化 | 输入：错义突变；输出：蛋白功能 disruption 分数 | Abstract: "recurrent hotspot mutations showed substantially larger predicted protein-level effects" | 预期影响：失去热点突变的蛋白效应区分度 [Analysis：预期效应] |
| 患者-基因聚合 | 将变异级预测聚合为基因水平、患者水平的 disruption profiles | 检验「累积 disruption」假说需要基因/患者级度量 | 输入：变异级 disruption 分数；输出：患者-基因 disruption profiles | Abstract: "aggregated the variant-level predictions to construct patient-gene disruption profiles" | 预期影响：无法从单变异视角检验累积效应假说 [Analysis：预期效应] |
| 临床关联分析 | 关联 disruption profiles 与癌症类型、MSI、生存 | 验证 disruption 的生物学和临床相关性 | 输入：disruption profiles + 临床数据；输出：关联统计 | Abstract: "reflected tissue of origin, cancer type, and microsatellite-instability status"; "associated with overall survival" | 预期影响：失去临床验证，仅剩计算预测 [Analysis：预期效应] |
| 独立队列验证（POG570） | 在治疗注释队列中验证 disruption-生存关联 | 检验泛化性，避免 TCGA 特异性 | 输入：POG570 突变 + 治疗数据；输出：治疗亚组生存关联 | Abstract: "In an independent treatment-annotated cohort, gene-level disruption was also associated with survival within treatment-defined subgroups" | 预期影响：泛化性存疑 [Analysis：预期效应] |

---

## 09 关键公式符号

不适用。本文为应用型研究，摘要中未提供具体公式或数学定义。disruption 分数的具体计算方式、聚合方法（求和/平均/加权）在摘要中未描述，需查阅全文 Methods 部分。

---

## 10 实验设计与证据链

- **数据集**：TCGA（8,800 患者，33 癌种）；TCGA-CDR（生存数据）；POG570（独立治疗注释队列）；IntOGen（驱动基因）；Cancer hotspots v2（热点突变）
- **指标**：未在摘要中明确列出（推测包括关联显著性、风险比等，需查阅全文）
- **基线**：未在摘要中明确列出（推测包括仅热点突变分析、TMB 等，需查阅全文）
- **预算/算力**：未提供
- **骨干/仪器**：AlphaGenome、AlphaMissense（均为预训练模型）
- **oracle 输入**：不适用（无人工标注的 disruption 真值；模型预测本身作为度量）
- **评测协议**：未在摘要中详细描述

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 热点 vs 非热点突变的 disruption 比较 | 热点突变富集于蛋白效应，非热点突变富集于调控效应 | 热点突变 vs 非热点突变，跨癌种比较 | 热点突变蛋白效应更大；非热点突变调控效应更大 | 不同突变类型在不同模态中分布不同 | 未证明因果关系；未证明调控 disruption 的功能后果 | Abstract |
| Disruption profiles 与癌症类型/组织来源/MSI 关联 | Disruption profiles 携带生物学信息 | 跨癌种比较；MSI 状态分层 | Profiles 反映组织来源、癌症类型和 MSI 状态 | Disruption profiles 具有生物学相关性 | 未证明独立于 TMB 的增量信息量（摘要仅称「retaining information beyond TMB」） | Abstract |
| 缺乏热点突变患者中的 disruption-生存关联 | 非热点 disruption 具有临床预后价值 | 无热点突变的患者亚组；OS 关联 | 较高 disruption 与较差 OS 相关（染色质可及性最强） | 调控 disruption 在无经典驱动事件时仍有预后意义 | 未证明因果关系；未证明独立于其他临床变量 | Abstract |
| POG570 独立队列验证 | Disruption-生存关联可泛化 | 治疗亚组分层 | 基因水平 disruption 与治疗亚组生存相关 | 泛化性初步支持 | 未提供效应量；未提供多变量校正信息 | Abstract |

---

## 11 结论正确解读

- **任务范围**：本文仅针对体细胞突变（非胚系）；仅覆盖 TCGA 和 POG570 队列；仅使用两个特定模型（AlphaGenome、AlphaMissense）的预测，未与其他模型系统比较。
- **oracle/真值输入**：无实验验证的 disruption 真值；所有 disruption 度量来自模型预测，模型准确度直接影响结论可靠性。
- **端到端状态**：从突变 → 模型预测 → 聚合 → 临床关联的完整流程已实现，但未达到「模型预测可直接指导临床决策」的程度。
- **算力成本**：未提供。
- **历史数据依赖**：依赖 TCGA 的历史突变 calling 和临床注释；依赖模型训练时的参考基因组版本和训练数据分布。
- **模型依赖**：结论完全依赖 AlphaGenome 和 AlphaMissense 的预测质量；若模型对调控变异的预测存在系统性偏差，则所有下游结论受影响。
- **最难情形**：非编码突变、剪接区域突变、低频突变的 disruption 预测可靠性可能较低；罕见癌种样本量小，统计功效有限。
- **群体/领域边界**：仅限癌症体细胞突变；不适用于胚系变异解读、非癌症疾病、非人类物种。
- **有边界的复述**：在 TCGA 33 癌种和 POG570 队列中，基于 AlphaGenome 和 AlphaMissense 预测聚合得到的患者-基因 disruption profiles 与癌症类型、MSI 状态和生存期存在统计关联，且这种关联在缺乏热点突变的患者中仍然存在；但这些关联的因果性和独立预测价值（超越 TMB 及其他临床变量）尚需进一步验证。

---

## 12 作者自认局限

在提供的材料（摘要 + 声明）中未发现作者明确承认的局限。作者仅提供了数据可用性声明和利益冲突声明。

**作者提及的相关约束**（非正式局限）：
- 数据可用性声明中提及 TCGA 数据为受控访问（dbGaP），需申请审批——这构成可重复性方面的实际约束。
- 未提供代码可用性声明，可能暗示代码未公开。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| Disruption 度量完全依赖模型预测，无实验验证 | AlphaGenome/AlphaMissense 的预测可能偏离真实分子效应；调控 disruption 的预测尤其缺乏大规模实验基准 | 若模型预测有偏，所有下游临床关联可能反映模型偏差而非真实生物学 | 使用独立实验数据（如 MPRA、STARR-seq、ChIP-seq 验证的 TF 结合变异）对 disruption 分数进行校准；比较不同模型（Enformer、Basenji）的预测一致性 | Abstract 未提及任何实验验证；仅称「predicted disruption」 |
| 「Retaining information beyond TMB」的表述模糊 | 摘要未说明增量信息量的大小、统计显著性、或是否经多变量校正 | 若增量信息量很小或经校正后消失，临床意义有限 | 查阅全文的多变量 Cox 模型、C-index 或 AUC 增量；要求报告校正 TMB、分期、年龄后的独立贡献 | Abstract: "retaining information beyond tumor mutational burden"——未提供效应量 |
| 缺乏热点突变患者中的生存关联可能受混杂因素影响 | 高 disruption 可能与总突变负荷、基因组不稳定性或特定突变 signature 相关，而非 disruption 本身 | 若关联由混杂驱动，则「disruption」不是因果变量 | 匹配 TMB 后的亚组分析；突变 signature 校正；孟德尔随机化或共突变网络分析 | Abstract 仅称「Among patients lacking recurrent hotspot mutations」——未提及 TMB 匹配 |
| 聚合方法未描述 | 变异级 disruption 如何聚合为基因/患者水平（求和？平均？最大？加权？）直接影响结果 | 不同聚合策略可能产生不同结论；缺乏敏感性分析则结果稳健性存疑 | 查阅 Methods 的聚合公式；要求多种聚合策略的敏感性分析 | 摘要未提供聚合细节 |
| 独立队列验证（POG570）的细节不足 | 未说明 POG570 中验证的是哪些基因、哪些模态、效应量大小 | 若验证仅限特定亚组或特定基因，泛化性有限 | 查阅全文的 POG570 分析细节；要求报告与 TCGA 一致的模态和基因集合 | Abstract 仅一句提及 POG570 |
| 与「TF–DNA 结合机制」的关联深度有限 | 摘要仅将 TF 结合作为 disruption 模态之一，未深入分析具体 TF 或结合 motif 的机制 | 对 TF–DNA 互作领域而言，需要知道哪些 TF 的结合扰动最相关、是否富集于特定 motif 或结合位点特征 | 查阅全文是否有 TF 特异性分析、motif 富集、结合位点位置效应分析 | 摘要未提及具体 TF 或 motif 层面的分析 |

---

## 14 Agent 提炼的知识候选

> 以下为可迁移到「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题方向的知识点：

1. **变异级 → 基因级 → 患者级的聚合框架**：本文的核心方法论贡献在于将单变异预测聚合为更高层级的 profiles。对 TF–DNA 结合研究，可将「单个 TF 结合位点突变的影响」聚合为「基因启动子/增强子区域的综合 TF 结合 disruption score」，再关联到表达变化或表型。迁移方式：定义 TF 结合 disruption = Σ(位点突变 × 该位点对基因表达的贡献权重)。

2. **多模态 disruption 的互补性**：本文发现蛋白效应和调控效应在不同突变类型中分布不同（热点 vs 非热点）。对 TF–DNA 研究，这意味着「TF 结合 disruption」和「下游表达 disruption」应同时考虑，单一模态会遗漏信号。迁移方式：同时计算 TF 结合 motif 突变的影响和预测的基因表达变化，构建联合 disruption 指标。

3. **「无驱动突变 ≠ 无功能后果」的临床视角**：本文在缺乏热点突变的患者中发现 disruption-生存关联。对 TF–DNA 研究，这意味着在缺乏经典驱动 TF 突变（如 MYC 扩增、TP53 突变）的肿瘤中，TF 结合位点的散在突变可能通过累积效应影响基因调控网络。迁移方式：在「TF 野生型」肿瘤中专门分析 cis-regulatory 元件的突变负荷与预后关联。

4. **染色质可及性作为最稳健的 disruption 模态**：本文发现染色质可及性 disruption 与生存关联最强。对 TF–DNA 研究，这提示染色质可及性变化可能是 TF 结合扰动的下游整合指标，比单个 TF 结合预测更稳健。迁移方式：将 TF 结合位点突变的影响映射到染色质可及性变化，而非仅停留在结合亲和力预测。

5. **基础模型直接用于临床关联的范式**：本文展示了「预训练基因组模型 → 患者级聚合 → 临床关联」的完整流程。对 TF–DNA 研究，可借鉴此流程：使用 AlphaGenome 或类似模型预测 TF 结合 disruption → 聚合为患者级 TF 调控 disruption score → 关联到癌症亚型、治疗反应或生存。

---

## 15 与已有知识连接

- **AlphaMissense（经外部核验）**：Cheng et al., Science 2023。本文将其用于蛋白水平 disruption 预测。该模型基于 AlphaFold 的蛋白结构上下文，对错义突变进行致病性预测。在 TF–DNA 研究中，AlphaMissense 可用于预测 TF 蛋白自身突变对其 DNA 结合域功能的影响。
- **Enformer / Basenji（经外部核验）**：Avsec et al., Nat. Methods 2021；Kelley et al., PLOS Comp. Biol. 2018。序列到表达/染色质预测的经典模型。本文使用的 AlphaGenome 属于此类模型的后续发展。对 TF–DNA 研究，这些模型可直接预测 TF 结合位点突变对染色质状态和表达的影响。
- **TCGA PanCanAtlas（经外部核验）**：本文的主要数据来源。该资源已被广泛用于癌症基因组-表型关联研究，包括 TF 调控网络在癌症中的扰动分析。
- **Cancer hotspots v2（经外部核验）**：Chang et al., Nat. Biotechnol. 2018。本文用于区分热点/非热点突变。在 TF–DNA 研究中，可用于区分 TF 基因自身的热点突变与 cis-regulatory 元件的散在突变。
- **POG570（经外部核验）**：基因组学指导的精准肿瘤治疗队列。本文用作独立验证队列。对 TF–DNA 研究，该队列的治疗注释可用于分析 TF 调控 disruption 与治疗反应的关系。
- **与「TF–DNA 结合机制 × AI」课题的关联**：本文的「TF 结合 disruption」模态直接涉及 TF–DNA 结合扰动，但其分析停留在「预测分数」层面，未深入结合 motif 序列特征、结合亲和力变化或结构机制。这为课题提供了「从预测到机制」的延伸空间：可将 AlphaGenome 的 TF 结合 disruption 预测与分子动力学模拟或结构预测结合，解释「为什么」某些突变破坏 TF 结合。

---

## 16 Agent 生成的研究候选

> 以下为基于本文可延伸的研究方向，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题：

### 候选 1：TF 结合 disruption 的机制解析——从预测分数到结构解释
- **名称**：Mechanistic interpretation of TF-binding disruption via structure-aware modeling
- **来源局限/观察**：本文仅报告 TF 结合 disruption 的预测分数，未解释「为什么」某些突变破坏 TF 结合；预测分数缺乏结构层面的验证
- **核心假设**：AlphaGenome 预测的高 TF 结合 disruption 突变富集于 TF–DNA 结合界面的关键接触残基/碱基，且可通过 MD 模拟或结构预测验证
- **增量方法**：将 AlphaGenome 的 TF 结合 disruption 预测与 AlphaFold3/分子对接/MD 模拟结合，对高 disruption 突变进行结构层面的机制验证；构建「序列预测 → 结构验证」的两步流水线
- **验证方式**：使用 ChIP-seq 验证的 TF 结合变异数据集，比较结构特征（接触距离、氢键变化、结合自由能 ΔΔG）能否区分高/低 disruption 突变
- **创新状态**：unverified

### 候选 2：TF 结合 disruption 的 motif 序列特征分析
- **名称**：Sequence motif determinants of TF-binding disruption in cancer genomes
- **来源局限/观察**：本文未分析 TF 结合 disruption 是否富集于特定 TF 的 motif 或特定位置的碱基替换
- **核心假设**：高 disruption 突变非随机分布，而是富集于 motif 的保守位置（如核心识别序列），且不同 TF 家族对突变位置的敏感性不同
- **增量方法**：对本文识别的 TF 结合 disruption 突变进行 motif 位置偏好分析（position-specific disruption profiles），结合 PWM 和 position weight matrix 计算预期 vs 观察的 disruption 分布
- **验证方式**：使用体外结合实验（如 HT-SELEX、PBMs）数据验证 motif 位置敏感性的预测
- **创新状态**：unverified

### 候选 3：TF 结合 disruption 与染色质可及性 disruption 的因果链建模
- **名称**：Causal chain modeling from TF-binding disruption to chromatin accessibility changes
- **来源局限/观察**：本文发现染色质可及性 disruption 与生存关联最强，但未分析 TF 结合 disruption 是否通过染色质可及性变化介导生存影响
- **核心假设**：TF 结合 disruption → 染色质可及性改变 → 基因表达变化 → 临床结局，构成因果链；TF 结合 disruption 对生存的影响部分由染色质可及性介导
- **增量方法**：使用中介分析（mediation analysis）或结构方程模型，检验 TF 结合 disruption 对生存的效应是否由染色质可及性 disruption 介导；结合 ATAC-seq 数据验证
- **验证方式**：在 TCGA 和独立队列中重复中介分析；使用孟德尔随机化（如 cis-MR）加强因果推断
- **创新状态**：unverified

### 候选 4：TF 结合 disruption 作为治疗反应生物标志物
- **名称**：TF-binding disruption profiles as predictive biomarkers for targeted therapy
- **来源局限/观察**：本文在 POG570 中验证了 disruption-生存关联，但未分析特定治疗亚组中哪些 TF 结合 disruption 最具预测价值
- **核心假设**：特定 TF 通路（如 p53、MYC、ER 信号）的结合 disruption 可预测对应靶向治疗的反应
- **增量方法**：在治疗注释队列中，按 TF 通路分层分析 disruption profiles 与治疗反应的关系；构建 TF 通路特异性 disruption signature
- **验证方式**：在 POG570 及其他治疗注释队列（如 MSK-IMPACT）中验证；与已知生物标志物（如 TMB、MSI）比较增量预测价值
- **创新状态**：unverified

### 候选 5：TF 结合 disruption 的跨物种保守性分析
- **名称**：Evolutionary conservation of TF-binding disruption effects
- **来源局限/观察**：本文未分析 disruption 效应的进化保守性；若高 disruption 位点在进化上保守，则其功能重要性更强
- **核心假设**：高 disruption 的 TF 结合位点在物种间保守性更高，且保守性可增强 disruption 预测的可信度
- **增量方法**：使用 phyloP/phastCons 或跨物种比对，计算 TF 结合位点的保守性分数，与 disruption 分数联合建模
- **验证方式**：比较保守 vs 非保守位点的 disruption 分数分布；在独立数据集中验证保守性加权的 disruption 分数是否改善临床关联
- **创新状态**：unverified