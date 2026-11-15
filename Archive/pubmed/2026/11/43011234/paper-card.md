## 01 基本信息

- **标题**：scMINA: an interpretable workflow for paired scRNA-scATAC multiome integration and regulatory prioritization
- **作者与单位**：Zhang, Shuwen; Hu, Hongru; Wang, Xue; Xiong, Chengjie; Kanekiyo, Takahisa; Asmann, Yan W; Ren, Yingxue（Mayo Clinic 等，具体单位未提供）
- **期刊/预印本平台**：NAR Genomics and Bioinformatics
- **年份**：2026
- **论文类型**：方法学/工作流（Workflow）论文
- **领域**：单细胞多组学（scRNA-seq + scATAC-seq）整合与调控优先排序
- **关键词**：single-cell multiomics, scRNA-seq, scATAC-seq, integration, interpretable AI, regulatory network, Alzheimer's disease
- **DOI/arXiv 号**：10.1093/nargen/lqag140
- **代码**：https://github.com/ShuwenZhangswz/scMINA；10.5281/zenodo.19582768
- **数据**：SEA-AD 数据集（Synapse ID: syn29879329；CELL x GENE 门户）
- **阅读日期**：未提供
- **该文在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × AI/深度学习」方向中的**调控网络推断与可解释性**子方向。它不直接预测 TF-DNA 三维结构或结合亲和力，而是通过整合 scRNA-seq 与 scATAC-seq 多组学数据，利用可解释 AI（XAI）方法优先排序候选基因和转录因子（TF），为 TF-DNA 调控关系提供**数据驱动的候选优先级**。其核心贡献在于将深度学习嵌入表示与特征归因方法（Integrated Gradients、Path-Explainer）结合，弥合了"黑盒模型"与"生物学可解释性"之间的鸿沟，可作为 TF-DNA 结合机制研究中候选调控因子的**上游筛选工具**。

## 02 一句话总结

本文提出了一个模块化、可解释的单细胞多组学分析工作流 scMINA，通过基准测试选定 scPair 作为默认整合方法，将 scRNA-seq 与 scATAC-seq 数据整合为统一细胞状态嵌入，并利用 Integrated Gradients 和 Path-Explainer 两种 XAI 特征归因方法，在 SEA-AD 阿尔茨海默病数据集上优先排序了与疾病相关胶质细胞状态相关的候选基因和转录因子。

## 03 研究问题

- **具体问题**：如何从配对的单细胞多组学数据（scRNA-seq + scATAC-seq）中，在保持可解释性的前提下，优先排序与疾病相关的候选基因和转录因子？
- **为什么重要**：单细胞多组学技术能同时捕获转录组和表观基因组信息，为解析复杂疾病中的基因调控机制提供了前所未有的机会。然而，多组学数据整合和下游调控推断缺乏标准化工作流，且深度学习方法虽然性能优越但可解释性差，限制了其生物学应用。
- **现有方法不足**：
  - MOFA+ 等矩阵分解方法可解释但仅能捕捉线性关系，且整合偏向 RNA 模态，未充分利用染色质可及性信息；
  - MultiVI 等深度生成模型能建模非线性关系，但嵌入表示难以直接解释；
  - 现有方法缺乏系统性的基准测试来指导用户选择适合特定数据集的整合策略；
  - 下游调控推断（如 FigR）与整合步骤脱节，缺乏从整合嵌入到调控优先排序的端到端工作流。
- **精确的 "Can ... ?" 研究问题**：Can an interpretable workflow that couples multimodal integration with XAI-based feature attribution robustly prioritize disease-associated genes and transcription factors from paired scRNA-seq and scATAC-seq data?

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注为「仅本文框架」，未经外部系统核验。

1. **单细胞多组学技术兴起**：scRNA-seq 提供转录组信息，scATAC-seq 提供染色质可及性信息，配对测量（如 10x Multiome）使同一细胞的转录组和表观基因组可联合分析。
2. **第一代整合方法——矩阵分解**：MOFA/MOFA+ 将多模态数据分解为共享和特异因子，可解释性强，但仅能捕捉线性关系，且难以扩展到全特征集。
3. **第二代整合方法——深度生成模型**：MultiVI 等基于变分自编码器（VAE）的方法能建模非线性关系，灵活处理缺失模态，但嵌入表示缺乏直接生物学解释。
4. **监督式跨模态映射**：scPair 通过配对训练直接建立 scRNA-seq 与 scATAC-seq 之间的映射关系，在跨模态预测任务中表现优异，但尚未被系统整合到完整分析工作流中。
5. **可解释 AI（XAI）的引入**：Integrated Gradients 和 Path-Explainer 等特征归因方法可量化输入特征对模型输出的贡献，为深度学习嵌入提供生物学层面的解释。
6. **调控网络推断**：FigR 等基于相关性的方法通过基因表达与染色质可及性的关联推断 TF-靶基因调控关系，但依赖预先定义的细胞类型注释。
7. **本文主张的位置**：scMINA 将上述进展整合为一个端到端、模块化的工作流，首次系统性地将整合方法基准测试、XAI 特征归因和调控网络推断耦合，为多组学数据提供从整合到调控优先排序的完整解决方案。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 多组学整合方法选择困难 | 不同整合方法在不同数据集上表现差异大，缺乏统一指导 | 各方法基于不同假设（线性 vs 非线性、无监督 vs 监督），适用场景不同 | Results "Benchmarking single cell multiomics integration methods" 节 |
| 深度嵌入缺乏可解释性 | MultiVI 等深度模型的嵌入表示难以直接映射到生物学机制 | 深度学习的分布式表示不天然对应生物学概念 | Introduction 节："embeddings derived from deep learning models can be more difficult to interpret directly" |
| MOFA+ 整合偏向 RNA 模态 | MOFA+ 的整合结果主要反映转录组信息，染色质可及性信息利用不足 | 矩阵分解方法对高维稀疏的 ATAC 数据拟合能力有限 | Results 图 2b："its integration was biased toward RNA and led to underutilization of chromatin accessibility information" |
| 跨模态预测能力不足 | MOFA+ 无法进行模态间预测（如从 ATAC 预测 RNA） | 矩阵分解方法缺乏显式的跨模态映射机制 | Results "Cross-modal alignment and prediction" 部分 |
| 调控推断与整合脱节 | 现有流程中整合和调控推断是分离的步骤，缺乏统一框架 | 缺乏将整合嵌入直接用于调控优先排序的标准化接口 | Discussion 节："a central innovation of scMINA is its combination of advanced integration strategies with multiple layers of downstream analysis" |
| 基因优先排序缺乏多方法交叉验证 | 单一方法（如仅 DORC 或仅 XAI）可能产生偏差 | 不同方法捕捉不同维度的信号，单一方法可能遗漏关键信息 | Results "Explainable AI-based signature discovery" 节：XAI 与 DORC 的交叉验证 |

## 06 核心思想

### 1) 表面方法

scMINA 是一个模块化工作流，包含以下步骤：
- **数据预处理**：统一峰值调用（MACS2）、质量控制、特征过滤
- **整合方法基准测试**：系统比较 scPair、MultiVI、MOFA+ 三种整合方法
- **默认整合**：选定 scPair 作为默认整合方法，学习联合嵌入
- **下游分析**：三个并行分支——(a) 常规差异表达/可及性分析（Seurat/Signac）；(b) 基于相关性的调控推断（FigR，DORC 分析）；(c) 基于 XAI 的特征归因（Integrated Gradients + Path-Explainer）
- **交叉验证**：将 XAI 归因结果与 DORC 分析结果交叉，识别高置信度候选基因

### 2) 核心洞察

- **监督式整合优于无监督整合**：scPair 通过配对训练显式建模 RNA-ATAC 映射关系，在跨模态预测和细胞状态分辨上优于无监督方法（MultiVI）和线性方法（MOFA+）。
- **可解释性可以"事后"实现**：与其设计 inherently interpretable 的模型（如 MOFA+），不如在强大的黑盒模型（scPair）上应用 XAI 特征归因，在保持性能的同时获得生物学解释。
- **多方法交叉验证增强置信度**：XAI 归因（捕捉模型决策依据）与 DORC 分析（捕捉统计相关性）是互补的信号源，二者交叉可识别更可靠的候选调控因子。
- **模块化设计是关键**：工作流允许用户根据数据特征和分析目标替换整合方法、归因方法或调控推断工具，适应不同场景。

### 3) 可能的普适教训 [Analysis]

- **"先整合，后归因"范式**：对于 TF-DNA 互作研究，可以先训练高性能的跨模态模型（如将染色质可及性映射到基因表达），再用 XAI 方法识别关键调控元件，这比直接设计可解释模型更灵活。
- **多证据源交叉验证**：在 TF-DNA 结合机制研究中，计算预测（如 XAI 归因）与统计推断（如 DORC 相关性）的结合可以增强候选因子的可信度，类似地也可与结构预测（如 AlphaFold）或分子动力学模拟结果交叉验证。
- **基准测试应成为标准实践**：在将 AI 方法应用于 TF-DNA 互作预测时，应系统比较不同方法在目标数据集上的表现，而非默认选择最流行的方法。

## 07 方法总览

- **输入**：配对的 scRNA-seq 和 scATAC-seq 计数矩阵（同一细胞），以及可选的细胞注释信息
- **输出**：(1) 整合后的细胞状态嵌入；(2) 细胞类型/亚型注释；(3) 差异表达基因列表；(4) DORC 基因列表；(5) XAI 高归因基因列表；(6) TF-DORC 调控网络；(7) 交叉验证的候选基因/转录因子优先排序表
- **模块**：
  1. 数据预处理模块（统一峰值调用、QC、特征选择）
  2. 整合模块（scPair 默认，可替换为 MultiVI/MOFA+）
  3. 聚类与注释模块（Seurat 流程）
  4. 差异分析模块（MAST）
  5. 调控推断模块（FigR/DORC）
  6. XAI 归因模块（Integrated Gradients + Path-Explainer）
  7. 交叉验证与优先排序模块
- **训练**：scPair 使用配对数据监督训练，损失函数包含 RNA 重建和 ATAC 重建项；MultiVI 使用 VAE 无监督训练；MOFA+ 使用变分贝叶斯分解
- **工具**：Nextflow DSL2（工作流管理）、Conda（环境管理）、Seurat v5.0.0、Signac、FigR、Captum、PAUSE
- **反馈回路**：XAI 归因结果可反馈至聚类注释，优化细胞状态定义；DORC 分析结果可指导后续实验验证
- **假设**：基因表达与染色质可及性之间存在可学习的映射关系；高归因特征对应生物学上重要的调控元件；DORC 与 XAI 的交叉验证可提高候选基因可靠性

**文字流程**：原始数据 → Cell Ranger ARC 处理 → 统一峰值调用（MACS2）→ QC 过滤 → scPair 整合训练 → 嵌入提取 → Seurat 聚类/注释 → 分支1：差异表达分析 → 分支2：FigR DORC 分析 → 分支3：XAI 归因（IG + Path-Explainer）→ 交叉验证 → 候选基因/转录因子优先排序

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 统一峰值调用 | 跨样本 harmonize 染色质可及性特征空间 | 不同样本的 peaks 不重叠，需统一特征集 | 输入：各样本 peaks；输出：统一 peak 集 | Methods "Dataset description" 节 | 预期影响：无法进行跨样本比较 [预期效应] |
| scPair 整合 | 监督式学习 RNA-ATAC 跨模态映射，生成联合嵌入 | 提供比无监督方法更准确的细胞状态表示 | 输入：RNA 计数 + ATAC 二元矩阵；输出：30 维嵌入 | Results 图 2a-c：scPair 在多数指标上排名最高 | 预期影响：细胞状态分辨率下降，跨模态预测能力减弱 [预期效应] |
| 聚类与注释 | 识别细胞类型和亚型 | 下游分析需要细胞类型级别的比较 | 输入：嵌入；输出：聚类标签 + 注释 | Results 图 3a-b | 预期影响：无法进行细胞类型特异性分析 [预期效应] |
| 差异表达分析 | 识别 AD vs 对照的差异表达基因 | 常规转录组层面的疾病关联分析 | 输入：RNA 矩阵 + 注释；输出：DEG 列表 | Results 图 3d-f | 预期影响：失去转录组层面的疾病信号 [预期效应] |
| FigR DORC 分析 | 推断基因表达与染色质可及性的相关性，定义调控域 | 识别潜在的顺式调控元件 | 输入：RNA + ATAC 矩阵；输出：DORC 基因列表 | Results 图 4e-f | 预期影响：失去基于相关性的调控推断信号 [预期效应] |
| XAI 归因（IG + Path-Explainer） | 量化输入特征对模型输出的贡献 | 将黑盒模型转化为可解释的生物学信号 | 输入：scPair 模型 + 嵌入；输出：特征归因分数 | Results 图 5a-f | 预期影响：失去模型层面的特征重要性信号 [预期效应] |
| 交叉验证与优先排序 | 整合 DORC 和 XAI 结果，识别高置信度候选 | 单一方法可能有偏差，交叉验证提高可靠性 | 输入：DORC 列表 + XAI 归因分数；输出：优先排序表 | Results 图 5c-d：如 NCK2, DOCK4, SYNDIG1, GLDN 在两种方法中均高排名 | 预期影响：候选基因列表可能包含更多假阳性 [预期效应] |

## 09 关键公式符号

本文为工作流论文，核心方法（scPair、FigR、Integrated Gradients）的详细公式在原始文献中，本文未给出完整数学推导。以下为文中涉及的关键概念：

1. **scPair 损失函数**（概念性，来自原始文献 [12]）：
   - 包含 RNA 重建损失、ATAC 重建损失和跨模态映射损失
   - 本文未给出具体公式，仅描述为"supervised learning approach that links chromatin accessibility and gene expression end to end"

2. **Integrated Gradients**（概念性，来自 [15]）：
   - 沿从基线到输入的路径积分梯度，量化特征贡献
   - 本文未给出公式，仅描述为"gradient-based approaches"

3. **DORC 评分**（概念性，来自 FigR [14]）：
   - 基于基因表达与峰可及性的相关性
   - 本文未给出具体公式

4. **评估指标**（文中使用）：
   - ARI (Adjusted Rand Index)：聚类准确度
   - NMI (Normalized Mutual Information)：聚类一致性
   - ASW (Average Silhouette Width)：细胞类型分离度
   - cLISI (Cell-specific Local Inverse Simpson's Index)：细胞类型纯度
   - batchASW / iLISI：批次混合度
   - FOSCTTM (Fraction of Samples Closer than True Match)：跨模态对齐质量
   - PCC / SCC：跨模态预测相关性
   - auROC / 1-BCE：ATAC 预测准确度

> 注：具体公式数值未在文中给出，以上为概念性描述。

## 10 实验设计与证据链

**数据集/群体**：
- SEA-AD（Seattle Alzheimer's Disease Brain Cell Atlas）MTG 区域多组学数据
- 初始：98,601 细胞（16 正常供体）+ 52,755 细胞（12 痴呆供体）
- 基准测试子集：4 个供体（2 正常 + 2 痴呆），32,291 细胞
- 全量分析：26 个供体（排除 2 个低胶质细胞计数供体），25,054 胶质细胞

**指标**：ARI、NMI、ASW、cLISI、batchASW、iLISI、FOSCTTM、PCC、SCC、auROC、1-BCE

**基线/对比方法**：MOFA+、MultiVI（与 scPair 对比）

**预算/资源**：未提供

**骨干/仪器**：未提供（计算平台信息未给出）

**oracle 输入**：细胞类型注释（用于评估聚类准确度）

**评测协议**：
1. 在 4 供体子集上基准测试三种整合方法
2. 用多种指标评估聚类质量、批次混合、跨模态预测
3. 选定 scPair 后，在全量 26 供体胶质细胞数据上应用
4. 进行亚聚类、差异表达、DORC 分析、XAI 归因
5. 交叉验证 XAI 与 DORC 结果

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 整合方法基准测试 | scPair 在整合质量上优于 MultiVI 和 MOFA+ | 3 方法 × 4 供体子集 | scPair 在多数指标上排名最高 | scPair 适合作为默认整合方法 | 未在所有可能的数据集上验证 | Results 图 2a-c |
| 模态平衡性评估 | MOFA+ 整合偏向 RNA 模态 | 比较各方法的模态贡献 | MOFA+ 偏向 RNA，scPair/MultiVI 更平衡 | 矩阵分解方法可能忽略 ATAC 信息 | 未量化模态偏差的具体程度 | Results 图 2b |
| 跨模态预测 | scPair 能准确预测缺失模态 | scPair vs MultiVI 的 FOSCTTM、PCC/SCC、auROC/1-BCE | scPair 优于 MultiVI | scPair 具有更强的跨模态映射能力 | 预测准确度的生物学意义未验证 | Results 图 2c |
| 胶质细胞亚聚类 | scRNA-scATAC 整合能分辨胶质细胞亚型 | 26 供体胶质细胞 | 识别出 11 个微胶质亚群、13 个星形胶质亚群 | 整合嵌入保留细胞异质性 | 亚群的生物学功能未验证 | Results 图 3a, 4a, 4c |
| AD 差异表达 | 胶质细胞在 AD 中有转录组改变 | AD vs 对照，各胶质细胞类型 | 各类型均鉴定出 DEGs | 胶质细胞参与 AD 病理 | DEGs 的因果关系未验证 | Results 图 3d-f |
| DORC 分析 | 存在与基因表达耦合的可及性调控域 | FigR 框架 | 鉴定出 DORC 基因（微胶质 56 个，星形胶质 164 个） | 存在候选顺式调控元件 | DORC 的功能验证未进行 | Results 图 4e-f |
| XAI 归因 | 可识别对细胞状态区分贡献最大的基因 | IG + Path-Explainer | 鉴定出高归因基因，部分与 DORC 重叠 | XAI 可提供与统计推断互补的信号 | 归因基因的因果作用未验证 | Results 图 5a-f |
| XAI-DORC 交叉验证 | 交叉验证可提高候选基因置信度 | 两种方法结果取交集 | 如 NCK2, DOCK4, SYNDIG1, GLDN 在微胶质中交叉验证 | 多方法交叉可增强候选可靠性 | 交叉验证的灵敏度/特异性未量化 | Results 图 5c-d |

## 11 结论正确解读

- **任务范围**：本文是**计算方法开发与演示**，而非生物学发现验证。其输出是候选基因/转录因子的**优先排序**，而非因果调控关系的证明。
- **oracle/真值输入**：细胞类型注释用于评估聚类质量；DORC 和 XAI 结果均无实验验证作为真值。
- **端到端状态**：工作流是端到端的（从原始数据到候选基因列表），但生物学验证（如 CRISPR 干扰、报告基因实验）未包含在内。
- **算力成本**：未报告训练时间、GPU 需求等计算资源信息。
- **历史数据依赖**：结果依赖于 SEA-AD 数据集的质量和注释准确性；不同数据集上表现可能不同。
- **模型依赖**：默认整合方法为 scPair，其性能在基准测试中优于 MultiVI 和 MOFA+，但这一结论仅限于测试的 4 供体子集。
- **最难情形**：稀疏的 ATAC 数据、罕见细胞类型、批次效应严重的数据集可能挑战工作流的稳健性。
- **群体/领域边界**：结果基于脑组织（MTG 区域）胶质细胞，推广到其他组织或细胞类型需谨慎。
- **不确定性**：XAI 归因分数和 DORC 相关性均不能证明因果关系；候选基因需要实验验证。
- **有边界的复述**：scMINA 在 SEA-AD 脑组织胶质细胞多组学数据上，通过 scPair 整合和 XAI 归因，能够优先排序与 AD 相关的候选基因和转录因子，其中部分候选基因与 DORC 分析结果交叉验证，但这些候选的因果作用尚未经实验证实。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 生物学验证缺失 | 候选基因和转录因子未经实验验证 | 需要扰动实验和体内研究确认因果作用 | Discussion 节："their causal regulatory roles in these microglial states remain to be established experimentally" |
| 泛化性未验证 | 仅在 SEA-AD 数据集上演示 | 需在更多疾病背景和多组学数据集上评估 | Discussion 节："evaluation across additional disease contexts and multiome datasets will be valuable" |
| 计算证据非因果 | XAI 归因和 DORC 相关性是计算证据 | 需要独立实验验证 | Discussion 节："these findings should be interpreted as candidate regulatory associations rather than evidence of causal regulation" |
| 利益冲突 | 共同作者 Hu Hongru 是 scPair 的开发者 | 未提及 | Conflict of interest 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 基准测试仅在 4 个供体上进行 | 样本量小，可能无法代表数据异质性；scPair 的优势可能不具普适性 | 默认方法的选择基于有限证据，可能不适用于其他数据集 | 在更多样化的数据集上重复基准测试 | Results "Benchmarking" 节 |
| scPair 开发者是共同作者 | 存在潜在的利益冲突，可能影响方法选择和结果解读 | 默认方法的选择应尽可能客观 | 由独立团队进行第三方基准测试 | Conflict of interest 节 |
| XAI 归因与 DORC 的交叉验证缺乏定量指标 | 未报告交叉验证的灵敏度、特异性或富集显著性 | 无法评估交叉验证策略的实际增益 | 计算交叉验证的统计显著性（如超几何检验） | Results 图 5 |
| 未与其他 XAI 方法比较 | 仅使用 IG 和 Path-Explainer，未与 SHAP、LIME 等比较 | 无法确定所选 XAI 方法是否最优 | 系统比较多种 XAI 方法 | Methods "Explainable AI" 节 |
| 未报告计算资源消耗 | 深度学习模型训练成本未知 | 影响方法的可及性和可扩展性 | 报告训练时间、GPU 型号和内存使用 | 全文未提供 |
| 生物学发现的验证深度有限 | 候选基因虽有文献支持，但未进行功能实验 | 计算预测的生物学意义需要实验确认 | 进行 CRISPR 干扰或报告基因实验 | Discussion 节 |
| 未讨论 scPair 的失败模式 | 未说明 scPair 在哪些条件下可能失效 | 用户可能在不适用场景下使用 scPair | 在合成数据或极端稀疏数据上测试 | 全文未提供 |

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质-DNA 互作（TF-DNA 结合机制）× AI/物理模拟」课题方向。

1. **可解释 AI 作为 TF-DNA 调控候选的筛选工具**：scMINA 展示了将 XAI 特征归因（IG、Path-Explainer）应用于深度学习嵌入，以识别对细胞状态区分贡献最大的基因/调控元件的可行性。在 TF-DNA 结合机制研究中，可训练一个将染色质可及性映射到基因表达的模型，然后用 XAI 识别关键调控位点，作为分子动力学模拟或结构预测的候选输入。

2. **多方法交叉验证范式**：scMINA 将 XAI 归因与 DORC 相关性分析交叉，识别高置信度候选。这一范式可迁移到 TF-DNA 互作研究：将结构预测（如 AlphaFold3）、分子动力学模拟（如结合自由能计算）与序列基序分析（如 PWM 扫描）的结果交叉验证，可提高候选 TF 结合位点的可靠性。

3. **监督式跨模态映射优于无监督整合**：scMINA 的基准测试表明，监督式方法（scPair）在跨模态预测上优于无监督方法（MultiVI）和线性方法（MOFA+）。在 TF-DNA 结合预测中，若有配对数据（如 ChIP-seq + RNA-seq），监督式方法可能优于纯无监督的表示学习方法。

4. **模块化工作流设计**：scMINA 的模块化架构（整合、聚类、差异分析、调控推断、XAI 归因可独立替换）是一个值得借鉴的设计模式。在 TF-DNA 互作研究中，可将序列编码、结构预测、动力学模拟、实验验证设计为可替换模块，便于基准测试和优化。

5. **基准测试应成为标准实践**：scMINA 通过系统基准测试选择整合方法，而非默认选择最流行方法。在 TF-DNA 结合预测中，应系统比较不同方法（如基于序列的 CNN、基于结构的 AlphaFold、基于物理的 MD）在目标数据集上的表现。

6. **XAI 归因的生物学验证缺口**：scMINA 的候选基因未经实验验证，这提醒我们在 TF-DNA 互作研究中，计算预测必须与实验验证闭环，否则只能作为假设生成工具。

7. **批次效应和模态平衡的重要性**：scMINA 指出 MOFA+ 的整合偏向 RNA 模态，提示在 TF-DNA 互作研究中，多模态数据（序列、结构、表观遗传修饰）的整合需注意模态平衡，避免某一模态主导结果。

8. **可解释性可以"事后"实现**：scMINA 展示了在强大黑盒模型上应用 XAI 归因的可行性。在 TF-DNA 结合预测中，不必牺牲模型性能换取可解释性，可以在高性能模型上事后应用归因方法。

## 15 与已有知识连接

1. **scPair**（Hu et al., 原始文献 [12]）：scMINA 的默认整合方法，监督式跨模态映射模型。可进一步阅读其原始论文了解模型架构和训练细节。

2. **MultiVI**（Ashuach et al., 原始文献 [11]）：基于 VAE 的无监督多模态整合方法，scMINA 的对比方法之一。

3. **MOFA+**（Argelaguet et al., 原始文献 [9, 10]）：矩阵分解类整合方法，scMINA 的对比方法之一，可解释但仅捕捉线性关系。

4. **FigR**（Kartha et al., 原始文献 [14]）：基于相关性的调控网络推断框架，scMINA 用于 DORC 分析和 TF-DORC 网络构建。与 TF-DNA 互作研究直接相关，可迁移到其他多组学数据。

5. **Integrated Gradients**（Sundararajan et al., 原始文献 [15]）：梯度-based 特征归因方法，scMINA 用于解释 scPair 嵌入。可迁移到 TF-DNA 结合模型的解释。

6. **Path-Explainer**（原始文献 [28]）：基于路径积分的归因方法，与 IG 互补。

7. **SEA-AD 数据集**（原始文献 [16]）：阿尔茨海默病脑细胞图谱，包含多组学数据，可作为 TF-DNA 互作研究的验证数据源。

8. **Harmony**（原始文献 [21]）：批次校正方法，scMINA 用于整合后的批次效应移除。

9. **MAST**（原始文献，Seurat 中实现）：差异表达分析方法，scMINA 用于 DEG 鉴定。

10. **scMINA 与 TF-DNA 互作研究的连接**：本文的 DORC 分析直接涉及染色质可及性与基因表达的关联，其识别的候选调控元件可作为 TF 结合位点预测的输入。XAI 归因方法可迁移到 TF-DNA 结合模型的解释。工作流的模块化设计模式可借鉴到 TF-DNA 互作分析管线的构建。

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质-DNA 互作（TF-DNA 结合机制）× AI/物理模拟」课题方向。

### 候选 1：基于 XAI 归因的 TF 结合位点优先排序框架
- **名称**：XAI-TFBS Prioritizer
- **来源局限/观察**：scMINA 展示了 XAI 归因在单细胞多组学中识别关键调控元件的可行性，但未将其与 TF 结合位点预测或结构验证结合。
- **核心假设**：将 XAI 归因（如 IG）应用于染色质可及性-基因表达映射模型，可优先排序对细胞状态区分贡献最大的染色质区域，这些区域富集功能性 TF 结合位点。
- **初步方法**：训练 scRNA-scATAC 整合模型 → 对每个 peak 计算 IG 归因分数 → 将高归因 peak 与已知 TF 基序（如 JASPAR）扫描结果交叉 → 用 ChIP-seq 数据验证富集。
- **验证方式**：在 SEA-AD 或 ENCODE 数据上评估高归因 peak 中 TF 基序的富集显著性；与随机 peak 集比较。
- **创新状态**：unverified

### 候选 2：多方法交叉验证的 TF-DNA 结合预测管线
- **名称**：Cross-Validated TF-DNA Binding Predictor
- **来源局限/观察**：scMINA 的交叉验证策略（XAI + DORC）提高了候选基因置信度，但 TF-DNA 结合预测领域缺乏类似的多方法交叉验证框架。
- **核心假设**：将序列基序分析、结构预测（AlphaFold3）、分子动力学模拟（结合自由能）和 XAI 归因四种方法的结果交叉，可显著提高 TF-DNA 结合预测的精度。
- **初步方法**：对候选 TF-peak 对，分别计算 PWM 匹配分数、AlphaFold3 预测的结合界面、MD 模拟的结合自由能、以及 XAI 归因分数；将四种分数整合为综合评分。
- **验证方式**：在 ChIP-seq 数据集上评估综合评分的 AUC，与单一方法比较。
- **创新状态**：unverified

### 候选 3：模态平衡感知的 TF 调控网络推断
- **名称**：Modality-Balanced Regulatory Network Inference
- **来源局限/观察**：scMINA 指出 MOFA+ 的整合偏向 RNA 模态，提示多模态整合中的模态不平衡问题可能影响下游调控推断。
- **核心假设**：在多模态整合中显式控制模态权重，可改善 TF 调控网络的推断准确性。
- **初步方法**：在 scMINA 框架中引入模态平衡正则化项，比较不同模态权重下 DORC 推断的稳定性。
- **验证方式**：在模拟数据和真实数据上评估调控网络推断的准确性和稳健性。
- **创新状态**：unverified

### 候选 4：TF-DNA 结合动力学的 XAI 增强分子动力学模拟
- **名称**：XAI-Enhanced MD for TF-DNA Binding
- **来源局限/观察**：scMINA 的 XAI 归因识别了关键调控元件，但未与物理模拟结合；TF-DNA 结合机制研究中 MD 模拟计算成本高，需要优先选择候选体系。
- **核心假设**：XAI 归因分数可作为 MD 模拟的初始候选筛选器，优先模拟高归因 TF-peak 对，提高计算资源利用效率。
- **初步方法**：用 scMINA 类工作流识别高归因 TF-peak 对 → 对 top 候选进行 MD 模拟 → 比较结合自由能与 XAI 分数的相关性。
- **验证方式**：在已知结构的 TF-DNA 复合物上验证 XAI 分数与实验结合亲和力的相关性。
- **创新状态**：unverified

### 候选 5：疾病相关 TF 调控程序的跨细胞类型比较
- **名称**：Cross-Cell-Type TF Regulatory Program Comparison
- **来源局限/观察**：scMINA 在胶质细胞中识别了 AD 相关的候选 TF，但未进行跨细胞类型的系统比较。
- **核心假设**：AD 相关的 TF 调控程序在不同胶质细胞类型中具有共享和特异的核心调控模块。
- **初步方法**：应用 scMINA 工作流到微胶质、星形胶质、少突胶质和 OPC，比较各细胞类型的 DORC 和 XAI 归因结果，识别共享和特异的 TF 调控模块。
- **验证方式**：用公开的 AD 相关 GWAS 数据验证优先 TF 的遗传富集。
- **创新状态**：unverified