## 01 基本信息

- **标题**：EpiXFormer: a cross-attention neural network for predicting cell type-specific transcription factor binding sites
- **作者**：Peng, Yonglin; Liu, Xinhua; Wu, Jun; Lin, Sang; Zhan, Shengxuan; Li, Hua; Wang, Ju; Zhao, Xiaodong
- **单位**：未提供（根据基金信息推测为中国机构，具体单位未在摘要中列出）
- **期刊/平台**：Briefings in Bioinformatics
- **年份**：2026（在线日期 2026-01-13）
- **论文类型**：方法学/算法研究
- **领域**：计算生物学、调控基因组学、深度学习
- **关键词**：transcription factor binding sites; cell type-specific; cross-attention; epigenomics; deep learning
- **DOI/arXiv**：10.1093/bib/bbaf721
- **代码**：https://github.com/Zer0o0/epixformer
- **数据**：ENCODE（accession 见 Supplemental Table S6）；GSE167979、GSE147716（hESC）；GSE90895（MEF/ESC/pre-iPSC）；GSE132440、GSE216090（PDAC）
- **阅读日期**：2026-05-13（基于当前日期）
- **在课题方向中的位置**：该文属于「TF–DNA 结合机制 × 深度学习」方向，聚焦于利用 cross-attention 架构整合 DNA 序列与表观基因组信息（组蛋白修饰、染色质可及性）进行细胞类型特异的 TF 结合位点预测，并探索模型可解释性（注意力权重、motif 提取）以揭示 TF 结合的调控机制。

---

## 02 一句话总结

EpiXFormer 通过 cross-attention 机制将 DNA 序列（CNN 提取特征）与 40 kb 窗口内的 7 种表观基因组信号（token 化）进行跨模态融合，在 199 个 DBP-细胞类型组合上实现了高精度（平均 AUROC 0.9905）的细胞类型特异 TF 结合位点预测，并利用注意力权重和 motif 分析揭示了近端/远端表观信息对 TF 结合的不同贡献及共结合因子。

---

## 03 研究问题

- **具体问题**：如何利用 DNA 序列和表观基因组信息，准确预测特定细胞类型中转录因子（TF）和 DNA 结合蛋白（DBP）的结合位点？
- **为什么重要**：TF 结合是基因调控的核心事件，其细胞类型特异性决定了细胞身份和功能。实验方法（ChIP-seq）成本高、通量低，无法覆盖所有 TF-细胞类型组合，计算预测是必要补充。
- **现有方法不足**：
  - 纯序列方法（如 DeepBind）无法区分不同细胞类型的结合差异；
  - 已有整合表观信息的方法（如 FactorNet、Leopard、maxATAC）多采用简单拼接或复杂架构，可解释性差，难以揭示表观信息如何影响 TF 结合；
  - 多数方法未显式建模近端与远端表观信息的差异化贡献。
- **精确研究问题**：Can a cross-attention-based neural network that explicitly models the interaction between DNA sequence and proximal/distal epigenomic context achieve accurate and interpretable cell type-specific TF binding site prediction?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言和讨论的叙述，属于「仅本文框架」，未经外部系统核验。

| 阶段 | 代表方法 | 优点 | 局限 | 本文位置 |
|------|----------|------|------|----------|
| 序列基方法 | DeepBind (CNN)、FIMO (motif 扫描) | 可解释（motif）、计算快 | 无法区分细胞类型 | 作为基线对比 |
| 序列+可及性 | Leopard、maxATAC | 引入细胞类型信息 | 特征简单拼接、可解释性弱 | 作为 SOTA 对比 |
| 多模态整合 | FactorNet、DeepGRN | 整合多种表观信号 | 架构复杂、难以提取生物学洞察 | 本文改进对象 |
| 注意力机制 | Transformer 架构 | 可建模长程依赖、注意力可解释 | 直接应用于基因组数据需适配 | 本文核心创新 |

**本文主张的位置**：EpiXFormer 通过 cross-attention 在保持简单架构的同时，实现了高精度和可解释性，填补了「高性能 vs 可解释」的空白。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 细胞类型特异性缺失 | 纯序列方法无法区分不同细胞类型的 TF 结合 | 序列本身不携带细胞类型信息 | Results 图 2C-D：EpiXFormer 优于 DeepBind/FIMO |
| 多模态特征整合方式粗糙 | 已有方法简单拼接序列和表观特征，性能受限 | 未建模两种模态间的交互关系 | Results 图 2F：EpiXFormer 优于 FactorNet/DeepGRN/Leopard/maxATAC |
| 可解释性不足 | 复杂架构难以提取生物学机制 | 特征融合方式不透明 | Discussion：现有方法「hinders interpretability」 |
| 远端表观信息利用不充分 | 多数方法仅关注局部区域 | 未显式建模远端调控 | Results 图 4A：注意力权重显示 40 kb 窗口内远端贡献 |
| 非序列特异 DBP 预测困难 | ns-DBP 缺乏明确 motif，预测难度大 | 结合依赖蛋白-蛋白互作而非直接 DNA 识别 | Results 图 2B：EpiXFormer 对 ns-DBP 仍达高 AUROC |

---

## 06 核心思想

### 1) 表面方法
构建一个 Transformer 编码器-解码器架构：CNN 提取 DNA 序列特征作为 query，表观基因组信号（7 种，40 kb 窗口，200 bp bin）经嵌入后作为 key/value，通过 cross-attention 融合两种模态，最终经全连接层输出结合概率。

### 2) 核心洞察
- **表观信息作为「上下文」**：将 40 kb 表观信号类比为 NLP 中的「句子上下文」，DNA 序列是「查询」，通过 cross-attention 让序列特征主动「查询」相关表观信号，而非简单拼接。
- **近端 vs 远端差异化贡献**：注意力权重分析显示，TF 结合主要受 ~10 kb 内近端表观信号影响（5 kb 上下游），但远端也有非零贡献，且不同 TF 的贡献距离模式不同。
- **共结合因子检测**：通过 motif 分析，模型不仅能恢复已知 TF motif，还能检测到共结合蛋白的 motif（如 RAD21/SMC3 检测到 CTCF motif），提示模型隐式学习了蛋白-蛋白互作。

### 3) 可能的普适教训 [Analysis]
- **跨模态 attention 优于特征拼接**：当两种输入模态具有不同语义层级时（序列是「实体」，表观是「上下文」），cross-attention 比 concatenation 更自然地建模二者关系。
- **可解释性设计应内置于架构而非事后分析**：cross-attention 权重天然提供「哪些表观信号影响了该位置的结合决策」的逐位置归因。
- **ns-DBP 的预测可通过「共结合因子」间接实现**：即使 DBP 本身无 motif，其结合位点可通过其互作蛋白的 motif 特征被识别。

---

## 07 方法总览

- **输入**：
  - DNA 序列：200 bp，one-hot 编码为 200×4 矩阵
  - 表观信息：7 种（ATAC, H3K27ac, H3K27me3, H3K36me3, H3K4me1, H3K4me3, H3K9me3），40 kb 窗口（±20 kb），200 bp bin → 200×7 状态矩阵，缺失标记为 'x'
- **输出**：结合概率（sigmoid）
- **架构**：
  - CNN 层：处理 DNA 序列，提取局部序列特征
  - Encoder：multi-head self-attention + feed-forward，处理表观 token 序列
  - Decoder：cross-attention（query 来自 CNN 序列特征，key/value 来自 encoder 的表观表示）
  - 全连接层：输出预测
- **训练**：
  - 每个 DBP-细胞类型对训练独立模型（base-model）
  - 正样本：ChIP-seq peak 中心 ±200 bp
  - 负样本：随机基因组区域 + FIMO 扫描（P=0.0001）非 peak 区域
  - 训练/测试比：80%/20%
- **工具**：TensorFlow（推测，未明确）、NeuronMotif（motif 提取）、Tomtom（motif 比对）、GREAT/DAVID（功能富集）
- **反馈回路**：无显式主动学习或迭代优化；模型为单次训练+推理

**文字流程**：
1. 对每个 DBP-细胞对，收集 ChIP-seq peak 作为正样本，生成负样本
2. 对每个样本，提取 200 bp DNA 序列和 40 kb 表观信号
3. 序列经 CNN 提取特征，表观信号经嵌入+self-attention 编码
4. Cross-attention 融合两种特征
5. 全连接层输出结合概率，二分类交叉熵训练
6. 推理时提取注意力权重和 CNN motif 进行生物学解释

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CNN 序列编码层 | 提取 DNA 序列局部 motif 特征 | 序列是 TF 结合的基础决定因素 | 输入：200×4 one-hot；输出：序列特征向量 | Results 图 5A-B：恢复已知 TF motif | 预期：失去序列特征，性能大幅下降（未做消融） |
| 表观 token 嵌入 | 将 7 种表观信号组合编码为 token | 表观信息是细胞类型特异性的主要来源 | 输入：200×7 状态矩阵；输出：200 个 token 嵌入 | Results 图 2C-D：加入表观信息后优于纯序列方法 | 预期：失去细胞类型特异性，退化为序列方法（未做消融） |
| Encoder (self-attention) | 建模表观信号间的长程依赖 | 远端表观信号可能协同影响 TF 结合 | 输入：token 嵌入；输出：上下文增强的表观表示 | Results 图 4A：注意力显示远端贡献 | 预期：失去远端信息整合能力（未做消融） |
| Cross-attention | 让序列特征「查询」相关表观信号 | 核心创新：显式建模序列-表观互作 | 输入：序列特征 (query) + 表观表示 (key/value)；输出：融合特征 | Results 图 4A-D：注意力权重有生物学意义 | 预期：退化为简单拼接，性能下降（未做消融） |
| 全连接输出层 | 二分类预测 | 将融合特征映射为结合概率 | 输入：融合特征；输出：概率 | Results 图 2A-B：高 AUROC | 预期：无法输出预测（trivial） |
| 半模型 (semi-model) | 使用部分表观信息训练 | 评估不同表观信号的贡献 | 输入：序列+部分表观；输出：预测 | Results 图 2G-J：ATAC 模型最接近 base | 预期：信息缺失时性能下降（实测） |

---

## 09 关键公式符号

本文为方法学论文，但摘要和正文中未给出明确的数学公式。以下为从方法描述中可推断的关键概念：

- **One-hot 编码**：DNA 序列 S ∈ {A, C, G, T}^200 → X ∈ ℝ^(200×4)，X[i,j] = 1 若第 i 位为第 j 种核苷酸
- **表观状态矩阵**：E ∈ {0, 1, x}^(200×7)，E[i,j] 表示第 i 个 200 bp bin 中第 j 种表观信号是否存在（1/0）或缺失（x）
- **Token 化**：每个 bin 的 7 维状态组合映射为词汇表中的一个 token（词汇表大小 3^7 = 2187）
- **Cross-attention**：Attention(Q, K, V) = softmax(QK^T / √d_k) V，其中 Q 来自 CNN 序列特征，K/V 来自 encoder 的表观表示
- **损失函数**：二元交叉熵 L = -[y·log(ŷ) + (1-y)·log(1-ŷ)]
- **评估指标**：AUROC, AUPRC, Accuracy, Recall, Precision, F1, MCC

> 注：具体公式细节未在提供的材料中给出，以上为基于方法描述的合理推断。

---

## 10 实验设计与证据链

### 数据集与设置
- **数据来源**：ENCODE 数据库（215 个 DBP-细胞类型组合初筛，199 个用于训练）
- **细胞系**：GM12878, HCT116, HepG2, IMR-90, K562, MCF-7, SK-N-SH（7 种）
- **DBP 数量**：43 种（其中 32 种为序列特异 TF，11 种为非序列特异 DBP）
- **正样本**：ChIP-seq peak 中心 ±200 bp
- **负样本**：随机非结合区域 + FIMO 扫描（P=0.0001）非 peak 区域
- **训练/测试**：80/20 随机划分
- **表观特征**：7 种（ATAC, H3K27ac, H3K27me3, H3K36me3, H3K4me1, H3K4me3, H3K9me3）
- **基线**：DeepBind、FIMO、FactorNet、DeepGRN、Leopard、maxATAC
- **外部验证**：hESC（GSE167979, GSE147716）、MEF/ESC/pre-iPSC（GSE90895）、PDAC（GSE132440, GSE216090）

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| base-model 性能 | EpiXFormer 能高精度预测 TF 结合 | 32 个 TF 的 199 个 DBP-细胞对 | 平均 AUROC 0.9905 [0.9649–0.9983] | 模型在多种 TF 和细胞系中表现优异 | 未与所有可能基线全面对比 | Results 图 2A |
| ns-DBP 性能 | EpiXFormer 能预测无 motif 的 DBP | 11 个 ns-DBP | 平均 AUROC 0.9904 [0.9577–0.9986] | 表观信息可补偿序列 motif 缺失 | 未解释 ns-DBP 结合的具体机制 | Results 图 2B |
| 与序列方法对比 | 表观信息提升预测 | EpiXFormer vs DeepBind/FIMO | EpiXFormer AUROC 更高 | 表观信息对 TF 结合预测有增量贡献 | 未报告具体提升幅度 | Results 图 2C-D |
| 与 SOTA 对比 | EpiXFormer 优于现有方法 | EpiXFormer vs FactorNet/DeepGRN/Leopard/maxATAC | EpiXFormer AUPRC 更高 | 跨模态 attention 优于特征拼接 | 未报告统计显著性检验 | Results 图 2F |
| 半模型消融 | 不同表观信号的贡献 | base vs ATAC-only vs 其他单信号 | ATAC 模型最接近 base | 染色质可及性是最重要的表观特征 | 未测试所有信号组合 | Results 图 2G-J |
| 细胞类型特异性 | 预测位点具有细胞类型特异性 | 5 个细胞系的 EP300 预测 | 各细胞系独立聚类，Jaccard 指数组内高、组间低 | 模型捕获了细胞类型特异的结合模式 | 未与随机期望比较 | Results 图 3A-B |
| 功能富集 | 预测位点具有生物学意义 | EP300 预测位点的 GREAT 分析 | 富集到细胞身份相关 GO 项 | 预测位点具有功能相关性 | 未做多重检验校正说明 | Results 图 3C |
| motif 恢复 | 模型学到已知 motif | NeuronMotif 提取 vs JASPAR | 恢复已知 TF motif | 模型学到了序列特征 | 未报告 motif 匹配的定量指标 | Results 图 5A-B |
| 共结合因子检测 | 模型能检测共结合蛋白 | RAD21/SMC3 模型 | 检测到 CTCF motif | 模型隐式学习蛋白-蛋白互作 | 未系统验证所有共结合关系 | Results 图 5C |
| 先锋因子推断 | 模型能识别先锋因子 | BRG1/BAF155 模型 | 检测到 POU5F1::SOX2 motif | 模型可用于先锋因子发现 | 未实验验证 | Results 图 5D |
| 跨细胞类型泛化 | 模型可预测未见细胞类型 | 训练集外细胞类型预测 | 高 AUROC（0.99+） | 模型泛化能力强 | 未测试远缘细胞类型 | Results 图 6A-B |
| 跨物种应用 | 模型可应用于小鼠 | 小鼠 MEF/ESC/pre-iPSC | 预测 MYC 结合位点 | 模型跨物种可用 | 未与小鼠 ChIP-seq 定量比较 | Results 图 6C-F |

---

## 11 结论正确解读

- **任务范围**：该模型预测的是「给定 DBP 和细胞类型，某 200 bp 区域是否被结合」的二分类问题，而非预测结合强度或亲和力。
- **Oracle/真值输入**：训练使用 ChIP-seq peak 作为 gold standard，但 ChIP-seq 本身有抗体质量、峰 calling 参数等噪声。
- **端到端状态**：模型是端到端训练的（序列+表观 → 预测），但表观数据需预先处理为 200 bp bin 状态。
- **算力成本**：每个 DBP-细胞对训练独立模型，199 个模型的总训练成本未报告。
- **历史数据依赖**：模型依赖 ENCODE 已产生的 ChIP-seq 和表观数据，对新 TF 或新细胞类型需重新训练或迁移。
- **最难情况**：ns-DBP（无 motif）的预测虽然 AUROC 高，但机制解释依赖共结合因子，可能不适用于无已知互作蛋白的 DBP。
- **边界**：模型在 7 个细胞系、43 个 DBP 上验证，外推到其他细胞类型或物种需谨慎；跨细胞类型预测虽表现好，但训练数据本身来自多个细胞系。
- **不确定性**：未报告预测置信区间或不确定性估计；注意力权重解释为「影响」是相关性而非因果性。

**有边界的复述**：EpiXFormer 在 ENCODE 来源的 7 个细胞系、43 个 DBP 上，利用 DNA 序列和 7 种表观信号，通过 cross-attention 融合实现了高精度的细胞类型特异 TF 结合位点预测，并提供了注意力权重和 motif 分析作为解释工具，但其泛化范围限于训练数据覆盖的细胞类型和 DBP 种类。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 覆盖 TF 数量有限 | 仅应用于 32 个 TF | 扩展至更多 TF | Discussion |
| 表观数据依赖 | 需要目标细胞类型的表观数据 | 探索数据缺失场景下的预测 | Discussion |
| 半模型性能下降 | 仅用部分表观信号时性能降低 | 优化半模型设计 | Results 图 2G-J |
| 未覆盖所有 DBP 类型 | 主要验证了序列特异 TF 和部分 ns-DBP | 扩展至更多 ns-DBP 和染色质调控因子 | Discussion |
| 跨细胞类型预测的机制解释有限 | 注意力权重解释为相关性而非因果 | 结合实验验证 | Discussion |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 高 AUROC 可能部分来自数据泄漏 | 训练和测试集随机划分，但同一细胞系的 peak 可能高度相似 | 若存在泄漏，性能被高估 | 按染色体划分训练/测试，或使用独立细胞系验证 | Methods：80/20 随机划分 |
| 与基线对比不全面 | 未与最新深度学习方法（如 Enformer、Basenji）对比 | 无法判断是否真正 SOTA | 在相同数据上运行公开基线 | Results 图 2F |
| 注意力权重解释缺乏因果验证 | 注意力高权重区域未必是功能必需区域 | 影响生物学结论可靠性 | 对高注意力区域进行 CRISPR 干扰或突变实验 | Results 图 4A-D |
| ns-DBP 的高性能可能依赖共结合因子 motif | 若共结合因子在不同细胞类型中表达不同，模型可能失效 | 影响 ns-DBP 预测的泛化性 | 在共结合因子敲除或低表达细胞中测试 | Results 图 5C |
| 半模型比较未控制变量 | 不同半模型可能使用不同数量的输入信号 | 无法公平比较各表观信号的贡献 | 统一输入信号数量，逐一替换 | Results 图 2G-J |
| 未报告模型不确定性 | 预测无置信区间，难以判断可靠性 | 影响实际应用中的决策 | 添加 MC-dropout 或 ensemble 不确定性估计 | 未提供 |
| 跨细胞类型预测的评估标准模糊 | 未明确「未见细胞类型」的定义 | 影响泛化性结论的强度 | 明确留出法（leave-one-cell-line-out）协议 | Results 图 6 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **跨模态 attention 设计**：当输入包含「主特征」（DNA 序列）和「上下文特征」（表观信号）时，用主特征作为 query、上下文作为 key/value 的 cross-attention 比简单拼接更有效且可解释。可迁移到 TF–DNA 结合机制研究中，用于整合序列、结构、表观等多模态信息。

2. **表观信息的 token 化处理**：将 40 kb 窗口划分为 200 bp bin，每个 bin 的 7 种表观信号组合编码为 token（3^7=2187 词汇表），类似 NLP 处理方式。这种离散化方法可迁移到其他基因组特征编码任务。

3. **ns-DBP 的间接预测策略**：对无明确 motif 的 DNA 结合蛋白，通过检测其共结合蛋白的 motif 实现预测和解释。这一思路可迁移到研究间接 DNA 结合或蛋白复合物介导的结合机制。

4. **注意力权重作为「影响距离」的度量**：通过分析注意力权重随距离的衰减模式，可推断表观信息对 TF 结合的有效作用范围（本文发现 ~10 kb 近端主导）。该方法可迁移到研究增强子-启动子互作、染色质环等长程调控机制。

5. **先锋因子发现的计算途径**：通过建模 BRG1/BAF155（SWI/SNF 复合物）并结合 motif 分析检测 POU5F1::SOX2 motif，展示了从染色质重塑因子结合位点推断先锋因子的计算策略。

6. **半模型消融作为特征重要性评估**：通过训练仅含部分表观信号的半模型，可系统评估各表观特征对 TF 结合的相对贡献（ATAC > 组蛋白修饰）。此消融设计可迁移到其他多模态基因组预测任务。

7. **跨细胞类型训练策略**：训练一个模型用于多个细胞类型的预测，可揭示 TF 在不同细胞类型中的共享和特异结合模式，有助于构建细胞类型特异的基因调控网络（GRN）。

---

## 15 与已有知识连接

- **与 DeepBind (Alipanahi et al., 2015)**：DeepBind 仅用序列预测结合，EpiXFormer 在此基础上引入表观信息，解决了细胞类型特异性的缺失。二者可视为序列-only 与序列+上下文方法的对比。
- **与 BPNet (Avsec et al., 2021)**：BPNet 用序列预测 base-resolution 结合 profile，EpiXFormer 预测 200 bp 分辨率的二分类，但 EpiXFormer 的注意力权重分析类似于 BPNet 的 contribution score 归因。
- **与 FactorNet (Quang & Xie, 2019)**：FactorNet 也整合序列和表观信息，但采用复杂架构；EpiXFormer 的 cross-attention 更简洁且可解释性更强。
- **与 Enformer (Avsec et al., 2021)**：Enformer 使用 transformer 处理长程序列，EpiXFormer 的 cross-attention 可视为将 transformer 应用于多模态基因组数据的变体。
- **与 Pioneer Factor 研究 (Zaret & Carroll, 2011)**：本文的先锋因子推断方法（通过 SWI/SNF 结合位点检测 OCT4 motif）与实验上鉴定先锋因子的策略互补。
- **与 CTCF/cohesin 机制 (Phillips-Cremins et al., 2013)**：RAD21/SMC3 模型检测到 CTCF motif 的发现，与已知的 CTCF-cohesin 共定位现象一致，验证了模型可捕获已知的蛋白-蛋白互作。
- **与表观基因组调控机制 (Rivera & Ren, 2013)**：本文对近端 vs 远端表观信息贡献的区分，与增强子-启动子互作和染色质结构对 TF 结合的调控模型一致。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：基于 EpiXFormer 的 TF 结合亲和力预测扩展
- **来源局限/观察**：EpiXFormer 仅预测二分类结合/不结合，未利用 ChIP-seq 的峰强度或 read count 信息。
- **核心假设**：将回归头替代分类头，可预测结合强度（affinity），提供更细粒度的调控信息。
- **增量**：从定性到定量，可区分强/弱结合位点，对构建 GRN 更有价值。
- **初步方法**：修改输出层为回归，损失函数改为 MSE 或 Poisson loss，评估指标增加 Pearson 相关。
- **验证方式**：与 ChIP-seq read count 比较，或与体外结合实验（如 HT-SELEX）数据交叉验证。
- **创新状态**：unverified

### 候选 2：跨物种迁移学习用于先锋因子发现
- **来源局限/观察**：EpiXFormer 在人类细胞系上训练，但先锋因子在发育和重编程中跨物种保守。
- **核心假设**：预训练于人类数据的模型，通过微调可迁移到小鼠或其他物种，并识别保守的先锋因子。
- **增量**：扩展模型适用范围，提供跨物种的先锋因子预测工具。
- **初步方法**：使用人类数据预训练，小鼠数据微调，比较迁移学习 vs 从头训练的性能。
- **验证方式**：在小鼠胚胎发育数据中验证预测的先锋因子是否在已知的发育调控中起作用。
- **创新状态**：unverified

### 候选 3：注意力权重引导的增强子-启动子互作预测
- **来源局限/观察**：EpiXFormer 的注意力权重显示表观信号在 40 kb 窗口内对 TF 结合有贡献，但未显式建模互作方向。
- **核心假设**：注意力权重可重新解释为增强子-启动子互作的强度估计。
- **增量**：将 TF 结合预测扩展到 3D 基因组互作预测。
- **初步方法**：提取注意力权重矩阵，与 Hi-C 或 HiChIP 数据比较，训练一个轻量级映射模型。
- **验证方式**：在已知的增强子-启动子对（如 CRISPR-FlowFISH 验证）上评估。
- **创新状态**：unverified

### 候选 4：结合物理模拟的 TF-DNA 结合机制解释
- **来源局限/观察**：EpiXFormer 的 motif 分析仅提供序列层面的解释，未涉及 3D 结构层面的结合机制。
- **核心假设**：将 EpiXFormer 预测的高置信结合位点作为候选，用分子对接或 MD 模拟验证其结构可行性，可提供从序列到结构的完整解释。
- **增量**：连接深度学习预测与物理模拟，提供机制层面的验证。
- **初步方法**：选取 EpiXFormer 预测的 novel 结合位点，用 AlphaFold3 或 HDOCK 预测 TF-DNA 复合物结构，MD 模拟评估结合稳定性。
- **验证方式**：比较模拟预测的结合构象与已知晶体结构（如有），或设计突变实验验证关键接触残基。
- **创新状态**：unverified

### 候选 5：动态表观状态下的 TF 结合预测
- **来源局限/观察**：EpiXFormer 使用静态表观数据，但表观状态在细胞分化、疾病进展中是动态变化的。
- **核心假设**：引入时间序列表观数据，可预测 TF 结合位点的动态变化，揭示调控网络的重塑。
- **增量**：从静态预测到动态预测，适用于发育和疾病模型。
- **初步方法**：使用时序 ATAC/组蛋白数据作为输入，采用循环或时序注意力机制。
- **验证方式**：在分化时间序列数据（如造血分化）中验证预测的动态结合变化是否与已知调控事件一致。
- **创新状态**：unverified

### 候选 6：EpiXFormer 用于 SNP 调控效应预测
- **来源局限/观察**：EpiXFormer 可预测结合位点，但未直接评估遗传变异对结合的影响。
- **核心假设**：对 SNP 位点进行 in silico 突变，比较突变前后预测分数，可评估 SNP 的调控效应。
- **增量**：将模型应用于疾病相关 SNP 的功能注释，连接基因组变异与调控机制。
- **初步方法**：对 eQTL/GWAS SNP 进行等位基因特异性预测，与实验数据（如 MPRA、STARR-seq）比较。
- **验证方式**：在已知调控 SNP（如 rs6983267）上验证预测方向与实验一致。
- **创新状态**：unverified