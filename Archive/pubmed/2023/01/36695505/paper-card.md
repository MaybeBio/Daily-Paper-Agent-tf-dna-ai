## 01 基本信息

- **标题**：Computational approaches to understand transcription regulation in development
- **作者与单位**：van der Sande, Maarten; Frolich, Siebren; van Heeringen, Simon J.（荷兰 Radboud University，van Heeringen 实验室）
- **期刊/预印本平台**：Biochemical Society Transactions
- **年份**：2023
- **论文类型**：综述（Review）
- **领域**：基因调控网络（GRN）推断；发育生物学；计算生物学
- **关键词**：gene regulatory networks (GRNs)、multi-omics、single-cell sequencing、neural networks、transcription factors (TFs)、cis-regulatory elements (CREs)
- **DOI/arXiv 号**：10.1042/BST20210145
- **代码**：未提供
- **数据**：未提供（综述，无原始数据）
- **阅读日期**：未提供
- **在「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法/物理模拟」方向中的位置**：本文是综述，聚焦于从基因表达数据推断 TF→靶基因调控关系的计算方法，涵盖多组学整合、单细胞测序和神经网络三大方向。与 TF–DNA 结合机制的直接关系在于：TF 结合 CRE（增强子/启动子）是 GRN 的核心环节，文中讨论了如何利用染色质可及性（ATAC-seq）、TF 基序（motif）评分、足迹分析（footprinting）等来推断 TF 在 DNA 上的结合，进而构建调控网络。本文不涉及物理模拟（MD/对接）或结构预测，属于 AI/统计建模路线。

---

## 02 一句话总结

本文综述了从基因表达数据推断基因调控网络（GRN）的计算方法，指出传统共表达网络基于相关性而非因果性，主张通过多组学整合、单细胞测序和神经网络三大方向提升 GRN 推断的准确性和因果性，最终目标是准确建模 TF 与靶基因之间的调控关系。

---

## 03 研究问题

- **具体问题**：如何从基因组规模的基因表达数据中准确推断 TF 与靶基因之间的调控关系（即 GRN），以理解发育过程中的转录调控？
- **为什么重要**：发育由转录调控驱动，TF 结合 CRE 调控靶基因表达是核心机制。准确的 GRN 模型能产生可检验的假设，帮助理解细胞命运决定和疾病中的调控失调。
- **现有方法为何不足**：
  - 传统共表达网络（如 WGCNA、ARACNE）基于相关性而非因果性，产生大量假阳性/假阴性。
  - 仅用基因表达单一模态，缺乏染色质状态、TF 结合等直接证据。
  - 批量测序（bulk）混合了多种细胞类型，掩盖了细胞类型特异的调控。
  - 线性/加性模型无法捕捉 TF 之间的非线性、乘法效应。
- **精确的「Can ... ?」研究问题**：Can integrating multi-omics data, single-cell resolution, and flexible neural network models significantly improve the accuracy and causality of GRN inference compared to traditional co-expression approaches?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架，未做外部核验。

1. **概念奠基期（1969–2000s）**：Britten & Davidson 于 1969 年提出 GRN 概念，后在海胆胚胎中实验验证。GRN 作为理解发育调控的抽象工具。
2. **共表达网络时代（2000s–2010s）**：微阵列和 RNA-seq 的出现使全基因组表达测量成为可能。WGCNA、ARACNE 等工具基于表达相关性/互信息推断基因间关系。**局限**：相关性≠因果性，网络精度低。
3. **多组学整合（2010s–至今）**：将染色质可及性（ATAC-seq/DNase-seq）、组蛋白修饰（H3K27ac、H3K4me1/3）、染色质构象（Hi-C）等与表达数据结合，用 TF 基序和足迹分析推断 TF 在增强子上的结合，增加因果约束。
4. **单细胞时代（2015s–至今）**：scRNA-seq 和 scATAC-seq 提供细胞类型特异的调控信号，支持伪时间轨迹推断和细胞类型特异的 GRN。
5. **神经网络时代（2018s–至今）**：ANN/DNN 作为灵活的非线性模型，可自动学习复杂调控关系，在基因组学中已有成功应用（如 DeepSEA、Basenji 等预测染色质状态和变异效应）。

**本文主张的位置**：处于第 3–5 阶段的交汇点，主张 GRN 推断应走向「单细胞多组学 + 神经网络」的融合范式。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 共表达网络缺乏因果性 | 推断的调控关系多为相关性，无法区分直接/间接调控 | 表达相关性不等于调控因果性；基因间共享调控因子会产生虚假相关 | Introduction 段：「these inferred networks are inaccurate and mostly based on correlative rather than causative interactions」 |
| 单一模态信息不足 | 仅用表达数据无法确定 TF 是否真正结合 DNA | 调控发生在染色质层面，表达是下游结果；TF 结合受染色质状态影响 | Multi-omics 节：「By incorporating TF binding at enhancers, regulatory networks can be constrained by direct, causal relationships」 |
| 批量测序掩盖细胞异质性 | 混合信号无法区分细胞类型特异的调控 | 组织由多种细胞类型组成，bulk 信号是平均结果 | Single cell 节：「bulk gene expression studies measure the whole transcriptome as a compound signal of all the different cells」 |
| 单细胞数据稀疏且统计假设被破坏 | 低覆盖度导致低表达基因关系难以检测；细胞非独立样本 | 每个细胞仅测到数千转录本；细胞来自同一遗传和环境影响，非独立重复 | Single cell 节：「cells are repeated measures...breaks most statistical assumptions」 |
| 线性/加性模型表达力不足 | 无法捕捉 TF 间的非线性、乘法效应 | 基因调控本质上是非线性、组合性的 | Neural networks 节：「gene-gene relationships are more complex and for example can include multiplicative effects」 |
| 神经网络可解释性差 | 模型预测准确但难以理解内部逻辑 | 深度网络的黑箱特性 | Neural networks 节：「the persistent misconception that ANNs only function as a black box」 |
| 基准评测不统一 | 各方法报告自身精度高但缺乏独立对比 | 缺乏标准化基准和统一指标 | Neural networks 节：「without independent benchmark studies it is hard to verify these results」 |

---

## 06 核心思想

### 1) 表面方法
综述三大技术路线：
- **多组学整合**：将表达数据与染色质可及性（ATAC-seq/DNase-seq）、组蛋白修饰（H3K27ac、H3K4me1/3）、染色质构象（Hi-C）等结合，用 TF 基序评分和足迹分析推断 TF 在增强子上的结合，以约束网络拓扑。
- **单细胞测序**：利用 scRNA-seq/scATAC-seq 获得细胞类型特异的调控信号，通过伪时间推断和细胞聚类（pseudobulk/meta-cells）构建细胞类型特异的 GRN。
- **神经网络**：用 ANN/DNN 作为灵活的非线性模型，自动学习基因间的复杂调控关系，可处理多模态输入。

### 2) 核心洞察
- **因果性需要多模态约束**：仅靠表达数据无法区分相关与因果，需要染色质可及性、TF 结合等直接证据来约束网络结构。
- **单细胞分辨率是必要的**：发育调控是细胞类型特异的，bulk 信号丢失了关键信息。
- **神经网络的灵活性是双刃剑**：能拟合任意非线性关系，但需要足够数据量，且可解释性差；多组学约束可以缓解欠定问题（curse of dimensionality）。
- **未来方向是三者融合**：单细胞多组学数据 + 神经网络模型，用多模态数据约束网络结构，用神经网络捕捉非线性。

### 3) 可能的普适教训 [Analysis]
- **「用直接证据约束间接推断」**：在 TF–DNA 结合预测中，如果只有表达数据，应尽量引入染色质可及性、基序、足迹等直接结合证据作为先验或约束，而非仅依赖表达相关性。
- **「分辨率决定可推断性」**：在蛋白质-DNA 互作研究中，单细胞/空间分辨率能揭示 bulk 中隐藏的细胞类型特异结合模式，这对 TF 结合的组织特异性研究有直接借鉴意义。
- **「模型复杂度需与数据量匹配」**：神经网络虽强大，但在小样本（如罕见发育阶段）下容易过拟合；正则化、dropout 和多模态约束是必要的。

---

## 07 方法总览

本文为综述，无单一方法实现。以下为文中描述的 GRN 推断通用流程：

- **输入**：
  - 基因表达数据（bulk RNA-seq 或 scRNA-seq）
  - 染色质可及性数据（ATAC-seq/DNase-seq）
  - 组蛋白修饰数据（H3K27ac、H3K4me1/3）
  - 染色质构象数据（Hi-C，可选）
  - TF 基序信息（motif 位置权重矩阵）
- **输出**：TF→靶基因的调控网络（有向图），或细胞类型特异的 GRN
- **模块**：
  1. 数据预处理与归一化
  2. 细胞聚类/伪时间推断（单细胞）
  3. 增强子/启动子注释与活性量化
  4. TF 结合位点预测（基序扫描 + 足迹分析 + 可及性整合）
  5. 增强子-启动子连接（距离、共可及性、Hi-C）
  6. 调控关系推断（回归、互信息、贝叶斯、神经网络）
  7. 网络修剪与验证
- **训练**：取决于具体方法；神经网络需大量样本，用 GPU 加速
- **反馈回路**：预测的调控关系可通过实验（如 TF 敲低/过表达）验证，验证结果可反馈优化模型
- **假设**：TF 结合 CRE 是调控的主要机制；可及性反映调控潜力；表达变化反映调控结果

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 多组学数据整合 | 将表达与染色质状态结合 | 表达单独不足以确定因果调控；染色质状态提供 TF 结合的直接证据 | 输入：表达+可及性+组蛋白修饰；输出：约束后的候选调控关系 | Multi-omics 节：「By incorporating TF binding at enhancers, regulatory networks can be constrained by direct, causal relationships」 | [预期] 移除后回到纯共表达，假阳性增加，因果性丧失 |
| TF 结合位点预测（基序+足迹） | 确定 TF 在 CRE 上的潜在结合位置 | TF 结合是调控的直接事件；基序提供序列特异性信息 | 输入：DNA 序列+可及性；输出：TF 结合概率/足迹 | Multi-omics 节：「combine TF binding probabilities derived from TF motif scores with DNA accessibility」 | [预期] 移除后无法确定 TF 是否直接结合，网络缺乏机制锚点 |
| 增强子-启动子连接 | 将远端增强子与靶基因关联 | 增强子可远程调控基因；错误连接导致错误靶基因分配 | 输入：增强子活性+基因位置+Hi-C；输出：增强子-基因配对 | Multi-omics 节：「enhancer-promoter interactions allow for the inference of directed GRNs」 | [预期] 移除后使用最近基因启发式，错误率显著上升（文中引用 [106,107] 指出最近基因启发式常不正确） |
| 单细胞聚类/pseudobulk | 获得细胞类型特异的表达信号 | 发育组织异质性强，bulk 信号是混合平均 | 输入：scRNA-seq 计数矩阵；输出：细胞类型/聚类后的表达谱 | Single cell 节：「clustering related cells, called pseudobulk or meta-cells...still yields cell-type specific signals」 | [预期] 移除后丢失细胞类型特异性，无法构建 context-specific GRN |
| 伪时间推断 | 排序细胞沿发育轨迹 | 发育是动态过程，需要时间信息推断因果 | 输入：scRNA-seq；输出：细胞伪时间排序 | Single cell 节：「order cells by their inferred temporal ordering...infer the gene-gene relations on this pseudotime」 | [预期] 移除后无法区分调控的时序方向 |
| 神经网络模型 | 学习非线性调控关系 | 基因调控含乘法/非线性效应，线性模型不足 | 输入：多模态特征；输出：预测的调控关系/表达 | Neural networks 节：「ANNs can approximate any continuous relationship in the data [157,158]」 | [预期] 移除后回到线性/加性模型，无法捕捉非线性交互 |
| 正则化/dropout | 约束模型复杂度 | 高维小样本下模型欠定 | 输入：模型参数；输出：约束后的模型 | Discussion 节：「regularization [174] and dropout [175] constrain the problem」 | [预期] 移除后过拟合风险显著增加 |

---

## 09 关键公式符号

本文为综述，未提供具体公式。文中提及的数学概念包括：

- **互信息（Mutual Information）**：ARACNE 等工具用于衡量基因表达之间的非线性关联，公式为 \( I(X;Y) = \sum_{x,y} p(x,y) \log \frac{p(x,y)}{p(x)p(y)} \)。用途：识别共表达基因对。来源：Introduction 节提及 ARACNE [42]。
- **贝叶斯回归（Bayesian ridge regression）**：用于 scRNA-seq 和 scATAC-seq 的整合推断。来源：Single cell 节提及 [124–126]。
- **偏微分方程/常微分方程（ODE）**：用于伪时间轨迹上的调控推断。来源：Single cell 节提及 [133,134]。
- **马尔可夫过程**：用于建模转录爆发（transcriptional bursting）和降解动力学。来源：Single cell 节提及 [142]。

> 注：以上公式为文中提及方法的数学基础，非本文作者推导。

---

## 10 实验设计与证据链

本文为综述，无原始实验。以下为文中引用的关键证据和基准：

- **数据集/群体**：文中提及的基准包括 DREAM challenges [164,184] 和 BEELINE platform [144]，均包含预定义数据集和质量指标。
- **规模**：未提供具体数字。
- **指标**：未提供具体指标定义。
- **基线**：传统共表达方法（WGCNA [41]、ARACNE [42]）作为对比基线。
- **预算**：未提供。
- **骨干/仪器**：未提供。
- **Oracle 输入**：不适用（综述）。
- **评测协议**：文中指出「只有通过标准化基准、在相同条件下比较，才能公平评估 GRN 推断方法」（Discussion 节）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| 多组学 vs 单组学 GRN 推断 | 多组学整合优于纯表达推断 | 表达+染色质 vs 纯表达 | 文中引用 [98,110,111] 显示多组学方法显著提升准确率 | 多组学约束可过滤假阳性、增加因果性 | 未提供具体数值，无法量化提升幅度 | Multi-omics 节 |
| 单细胞 vs bulk GRN 推断 | 单细胞数据提供细胞类型特异信号 | scRNA-seq vs bulk | 文中承认多数单细胞方法「未能显示对 bulk 方法的一致改进」[117,143,144] | 单细胞数据有原理优势但实践尚未兑现 | 不能断言单细胞方法普遍优于 bulk | Single cell 节 |
| 神经网络 vs 传统方法 | ANN 能捕捉非线性调控 | ANN vs 回归/互信息 | 各 ANN 方法报告更高精度，但缺乏独立基准验证 | ANN 有表达力优势 | 无法确认是否真正优于传统方法 | Neural networks 节 |
| 足迹分析 | 从可及性数据推断 TF 结合 | 足迹 vs 基序扫描 | 足迹可检测动态结合，但受酶切偏好影响 [87–89] | 足迹提供结合的直接证据 | 对动态结合 TF 检测不完整 | Multi-omics 节 |

---

## 11 结论正确解读

- **任务范围**：本文讨论的是从基因表达（及辅助染色质数据）推断 TF→靶基因调控关系的计算方法，不涉及 TF–DNA 结合的物理/结构层面（如分子动力学、对接、结构预测）。
- **Oracle/真值输入**：文中未讨论使用 ChIP-seq 等实验结合数据作为训练标签或验证基准的具体方案，仅提及 ChIP-seq 作为理想但不可扩展的实验手段。
- **端到端状态**：文中描述的 GRN 推断流程并非端到端——各模块（TF 结合预测、增强子-启动子连接、调控推断）相对独立，未形成统一的可训练管线。
- **算力成本**：文中仅提及神经网络需 GPU 加速，未提供具体算力需求。
- **历史数据依赖**：GRN 推断依赖已注释的 TF 基序数据库和参考基因组注释，跨物种泛化能力有限（文中提及 [66] 指出跨物种泛化问题）。
- **最难情形**：发育过程中 TF 结合是动态的、细胞类型特异的，且增强子-启动子远程互作复杂，这些是当前方法最难处理的场景。
- **群体/领域边界**：结论主要针对发育生物学中的 GRN 推断，对疾病中的调控失调推断可能部分适用但未直接讨论。
- **不确定性**：作者明确承认单细胞 GRN 方法尚未兑现理论优势，神经网络方法的优越性缺乏独立基准验证。

**有边界的复述**：在发育生物学背景下，从表达数据推断 GRN 的传统共表达方法因缺乏因果性而精度有限；通过整合染色质可及性等多组学数据、利用单细胞分辨率、并采用神经网络等灵活模型，有望提升 GRN 推断质量，但当前证据尚不足以断言某一方法全面胜出，需依赖标准化基准（如 DREAM、BEELINE）进行公平比较。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 单细胞 GRN 方法未兑现理论优势 | 多数单细胞方法「seemingly barely any better than purely random models」 | 需要更多工作证明其实际价值 | Single cell 节：「many fail to show consistent improvement over methods that were developed for bulk data, and are seemingly barely any better than purely random models [117,143,144]」 |
| 计算扩展性问题 | 单细胞方法「take several days to weeks to finish」 | 需要更高效的算法和实现 | Single cell 节：「the added complexity and number of cells leads to computational scaling issues」 |
| 神经网络可解释性差 | 难以理解模型内部学习到的调控逻辑 | 需要可解释性方法 | Neural networks 节：「understanding how ANNs work is...much harder」 |
| 神经网络优越性缺乏独立验证 | 各方法自报精度高但无统一基准 | 需要标准化基准（DREAM、BEELINE） | Neural networks 节：「without independent benchmark studies it is hard to verify these results」 |
| 多组学增加欠定风险 | 更多模态使网络更复杂，欠定问题加剧 | 用多模态数据「prune」可能的调控关系，减少自由度 | Discussion 节：「most multi-omics approaches use the new modalities to prune the possible TF-target gene relations, which actually reduces the degrees of freedom」 |
| 机制性模型实用性不足 | 转录爆发等机制模型理论上好但实践价值未证明 | 需要更多工作证明其实用性 | Single cell 节：「more work is needed to prove their practical usefulness」 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 综述对「多组学优于单组学」的结论主要依赖引用而非系统比较 | 引用的研究可能使用不同数据集和指标，直接比较有偏 | GRN 推断领域的核心争议是「增加模态是否真的提升精度」 | 在 DREAM/BEELINE 基准上系统比较单模态 vs 多模态方法 | Multi-omics 节引用 [98,110,111] |
| 作者对神经网络的乐观预期缺乏实证支持 | 文中承认无独立基准验证，且单细胞方法表现不佳 | 神经网络可能只是在小样本下过拟合，而非真正学到调控逻辑 | 在标准基准上比较 ANN 与传统方法，控制数据量和计算预算 | Neural networks 节 |
| 「pseudobulk 解决重复测量问题」的论述不完整 | 聚类本身引入主观性，且 pseudobulk 仍非独立样本 | 统计有效性是 GRN 推断可信度的基础 | 比较 pseudobulk 与混合模型在不同聚类参数下的表现 | Single cell 节 |
| 足迹分析的局限被轻描淡写 | 文中承认酶切偏好问题，但未讨论替代方案（如 ChIP-seq 的不可扩展性 vs 计算预测的不确定性） | TF 结合预测的准确性直接决定 GRN 质量 | 在已知 ChIP-seq 数据上评估足迹分析 vs 基序打分的精度 | Multi-omics 节 |
| 综述未讨论物理模拟/结构预测路线 | 分子动力学、AlphaFold 等结构方法可能为 TF 结合提供正交证据 | 对 TF–DNA 互作研究而言，序列+表达方法缺少结构层面的机制约束 | 探索将结构预测与 GRN 推断结合的混合方法 | 全文未提及 |
| 「最终走向单细胞多组学 ANN」的预测缺乏时间表和里程碑 | 技术成熟度、数据积累、算力成本均未讨论 | 领域发展需要可检验的阶段性目标 | 设定 3–5 年内的可量化基准目标 | Discussion 节 |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **多模态约束是提升因果性的关键**：在 TF–DNA 结合预测中，仅用表达数据（或仅用序列）是不够的。本文的核心主张——用染色质可及性、组蛋白修饰、3D 基因组等直接证据约束调控关系——可直接迁移到 TF 结合位点预测：将 ATAC-seq 可及性、DNase 足迹、H3K27ac 等作为特征或先验，可显著减少仅靠基序扫描的假阳性。

2. **单细胞分辨率揭示 context-specific 调控**：TF 结合是细胞类型特异的。在 TF–DNA 互作研究中，应尽量使用单细胞多组学数据（scATAC-seq + scRNA-seq）而非 bulk，以捕捉发育过程中 TF 结合的动态变化。pseudobulk 策略是处理稀疏数据的实用手段。

3. **神经网络的「无假设」特性适合捕捉非线性 TF 互作**：TF 之间的协同/拮抗作用往往是非线性的（如乘法效应）。ANN 无需预设交互形式，可自动学习这些复杂关系。但需注意：小样本下容易过拟合，正则化、dropout 和多模态约束是必要的。

4. **基准评测是领域痛点**：GRN 推断方法「自报精度高但缺乏独立验证」的问题在 TF 结合预测中同样存在。使用标准化基准（如 DREAM、BEELINE）和模拟数据（已知 ground truth）是验证方法的必要步骤。

5. **增强子-启动子连接是 TF–DNA 互作的关键下游环节**：TF 结合增强子后如何影响靶基因表达，取决于增强子-启动子互作。Activity-by-Contact 模型（结合距离和增强子活性）优于最近基因启发式，这一思路可迁移到 TF 靶基因分配问题。

6. **转录爆发（transcriptional bursting）是单细胞数据的重要特征**：单细胞表达数据中的噪声部分来自转录的随机爆发。将这一机制纳入模型（如马尔可夫过程）可能提升 GRN 推断的准确性，也提示在 TF–DNA 结合研究中需考虑转录噪声的影响。

7. **跨物种泛化是挑战**：TF 结合模型在一个物种上训练后未必能迁移到另一物种。开发跨物种泛化的方法（如利用保守基序、共线性信息）是未来方向。

---

## 15 与已有知识连接

- **与 WGCNA/ARACNE 的对比**：本文明确指出传统共表达工具（WGCNA [41]、ARACNE [42]）基于相关性而非因果性，这是 GRN 推断领域的经典批评。读者若熟悉这些工具，可理解本文主张的「多组学约束」是对其根本缺陷的回应。
- **与 DREAM/BEELINE 基准的联系**：DREAM challenges [164,184] 和 BEELINE platform [144] 是 GRN 推断领域的标准基准，读者可参考这些基准的设计（模拟数据+实验数据混合）来设计 TF 结合预测的评测方案。
- **与 DeepSEA/Basenji 等深度学习模型的联系**：文中提及的「用序列预测染色质状态」的神经网络模型（[150,151] 等）与 DeepSEA、Basenji 等经典工作一脉相承。这些模型证明 CNN 能从序列预测功能基因组学输出，是 TF 结合预测的重要基线。
- **与 AlphaFold 等结构预测的联系**：本文未讨论结构方法，但读者可将结构预测（如 AlphaFold3、RoseTTAFold 等预测蛋白质-DNA 复合物结构）与本文的统计推断方法视为互补：结构方法提供物理结合机制，统计方法提供调控网络层面的功能关联。
- **与单细胞轨迹推断工具的联系**：文中提及的伪时间推断（Monocle、Slingshot 等）是单细胞分析的标准工具，读者可将其与 TF 结合动态分析结合，研究发育过程中 TF 活性的时序变化。
- **与 Activity-by-Contact 模型的联系**：文中引用的 ABC 模型 [109] 是增强子-靶基因分配的重要方法，读者可将其与 TF 结合数据结合，构建「TF→增强子→靶基因」的完整调控链。

---

## 16 研究想法

> **Agent 生成的研究候选**

### 候选 1：基于单细胞多组学的 TF 结合动态推断框架
- **名称**：scTF-Binding：单细胞分辨率下的 TF 结合位点动态推断
- **来源局限/观察**：本文指出单细胞 GRN 方法尚未兑现理论优势，且 TF 结合是动态、细胞类型特异的。现有 TF 结合预测大多基于 bulk 数据或静态序列特征。
- **核心假设**：整合 scATAC-seq 可及性、scRNA-seq 表达和 TF 基序信息，可以在单细胞水平推断 TF 结合活性的动态变化，且优于 bulk 方法。
- **初步方法**：对 scATAC-seq 进行足迹分析（考虑酶切偏好校正），结合 TF 基序评分和 scRNA-seq 共表达，用变分自编码器或图神经网络学习细胞类型特异的 TF 结合概率。
- **验证方式**：在已知 TF 结合数据的细胞系（如 ENCODE）上模拟单细胞数据，比较 scTF-Binding 与 bulk 方法的 AUC；在发育系统（如胚胎干细胞分化）中验证预测的 TF 结合动态是否与已知调控事件一致。
- **创新状态**：unverified

### 候选 2：多模态约束的神经网络 GRN 推断
- **名称**：MultiGRN：多模态数据约束的图神经网络 GRN 推断
- **来源局限/观察**：本文指出多组学整合可提升 GRN 精度，但缺乏统一框架；神经网络可捕捉非线性但易过拟合。
- **核心假设**：将染色质可及性、组蛋白修饰、增强子-启动子连接作为图神经网络的边约束，可以显著减少 GRN 推断的假阳性，同时保留非线性表达能力。
- **初步方法**：构建异质图（TF、增强子、基因），节点特征来自多组学数据，边权重由 ABC 模型和共可及性初始化；用图注意力网络学习边存在概率，用正则化和 dropout 控制过拟合。
- **验证方式**：在 DREAM/BEELINE 基准上比较 MultiGRN 与现有方法；在已知调控网络中评估边预测的 precision/recall。
- **创新状态**：unverified

### 候选 3：TF 结合预测与结构信息的混合模型
- **名称**：StructTF：融合 AlphaFold3 结构预测与序列特征的 TF 结合位点预测
- **来源局限/观察**：本文完全未讨论结构方法，但 TF–DNA 结合本质上受物理化学机制控制。序列基序方法忽略 3D 结构约束。
- **核心假设**：AlphaFold3 等结构预测工具提供的 TF-DNA 复合物结构信息，可以作为先验约束，提升 TF 结合位点预测的精度，尤其是在基序模糊的区域。
- **初步方法**：对候选 TF-DNA 复合物进行结构预测，提取界面残基接触信息作为特征；与序列基序、可及性特征融合，训练梯度提升或深度学习分类器。
- **验证方式**：在 ChIP-seq 数据集上比较 StructTF 与仅用序列/可及性特征的基线；在结构已知的 TF 家族中验证预测的界面残基是否与实验结构一致。
- **创新状态**：unverified

### 候选 4：转录爆发机制启发的单细胞 GRN 推断
- **名称**：BurstGRN：考虑转录爆发的单细胞 GRN 推断模型
- **来源局限/观察**：本文提及转录爆发是单细胞表达数据的重要特征，但现有 GRN 推断方法多假设高斯噪声，忽略爆发动力学。
- **核心假设**：将转录爆发（马尔可夫过程）纳入 GRN 推断模型，可以更准确地估计 TF 对靶基因的调控强度，尤其是在低表达基因上。
- **初步方法**：用两状态马尔可夫模型描述基因的活跃/沉默状态，将 TF 浓度作为状态转换速率的协变量；用 MCMC 或变分推断估计参数。
- **验证方式**：在已知爆发参数的基因上模拟数据，比较 BurstGRN 与高斯假设方法的参数估计误差；在真实 scRNA-seq 数据上验证推断的调控关系是否与 ChIP-seq 一致。
- **创新状态**：unverified

### 候选 5：跨物种 TF 结合泛化基准
- **名称**：CrossTF-Bench：跨物种 TF 结合预测的标准化基准
- **来源局限/观察**：本文指出跨物种泛化是挑战 [66]，但缺乏标准化基准来量化这一问题。
- **核心假设**：通过构建跨物种的 TF 结合基准，可以系统评估现有方法的泛化能力，并指导开发更鲁棒的模型。
- **初步方法**：收集人类、小鼠、斑马鱼、果蝇的 TF 结合数据（ChIP-seq、DAP-seq），统一处理流程；定义跨物种迁移任务（训练集/测试集来自不同物种）；评估序列基序、深度学习、结构预测等方法的迁移性能。
- **验证方式**：报告各方法在跨物种任务上的 AUC、PR-AUC；分析影响迁移的因素（序列保守性、TF 家族、染色质状态）。
- **创新状态**：unverified