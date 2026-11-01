## 01 基本信息

- **标题**：DeepCNet: A multimodal deep learning model for predicting cell type-specific gene expression and promoter-enhancer interactions from single-cell multiome data
- **作者与单位**：Jin, Weijia; Zhao, Fengdi; Ma, Xin; Lu, Qing; Esser, Karyn A; Sun, Ramon C; Chen, Li（单位未在摘要中提供）
- **期刊/预印本平台**：Research Square（预印本）
- **年份**：2026-10-25
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：计算基因组学；单细胞多组学；基因调控；深度学习
- **关键词**：promoter-enhancer interactions; single-cell multiome; deep learning; gene expression prediction; TF-GRN
- **DOI/arXiv 号**：10.21203/rs.3.rs-8716015/v1
- **代码**：未提供
- **数据**：PBMC scMultiome（10X Genomics）；AD 单细胞多组学数据（Broad Institute）；ChIA-PET（ENCODE）；sn-m3C-seq；AD 研究 Hi-C 数据；CRISPR-K562（ENCODE）；CRISPRi-Ast（AstroREG）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× 深度学习」方向，核心贡献在于从单细胞多组学数据中推断细胞类型特异的启动子-增强子（PE）互作，并进一步构建 TF–基因调控网络（TF-GRN）。与纯序列模型（如 Enformer、ExPecto）不同，DeepCNet 显式建模 PE 互作并支持跨条件差异分析，为 TF–DNA 结合机制研究提供了从序列 + 染色质可及性到调控网络推断的端到端框架。

---

## 02 一句话总结

DeepCNet 是一个多模态深度学习框架，整合 DNA 序列特征、染色质可及性和细胞类型关系，从单细胞多组学数据中预测细胞类型特异基因表达并推断启动子-增强子互作，进而构建 TF–基因调控网络；在血液和脑组织两个数据集上，其表达预测准确性和 PE 互作推断与正交染色质互作及 CRISPR 扰动数据的一致性均优于现有方法。

---

## 03 研究问题

- **具体问题**：如何从单细胞多组学数据（同一细胞中同时测量 RNA 表达和染色质可及性）中，实现细胞类型特异的基因表达预测，并同时推断启动子-增强子（PE）互作及构建 TF–基因调控网络（TF-GRN）？
- **为什么重要**：非编码 DNA 如何决定细胞类型特异的基因表达是基因组学核心问题。PE 互作是基因调控的关键机制，而 TF–DNA 结合是 PE 互作的分子基础。单细胞多组学提供了在同一细胞中同时观察表达和调控元件的独特机会，但现有方法多聚焦于表达预测精度，缺乏对调控互作的可解释推断。
- **现有方法不足**：
  - ExPecto、Enformer 等基于 bulk 数据开发，未利用单细胞分辨率的细胞类型异质性；
  - seq2cells 虽面向单细胞，但主要强调表达预测，未系统推断 PE 互作；
  - EPInformer 可推断 PE 互作，但未显式建模细胞类型关系，也未支持跨条件（如疾病 vs 对照）的差异互作分析。
- **精确研究问题（Can...?）**：Can a multimodal deep learning framework that integrates DNA sequence, chromatin accessibility, and cell type relationships from single-cell multiome data simultaneously predict cell type-specific gene expression and infer cell type-specific promoter-enhancer interactions that are consistent with orthogonal experimental data?

---

## 04 背景与发展脉络

> 注：此脉络基于本文摘要与引文的框架整理，标注为「仅本文框架」，未经外部系统核验。

1. **第一代：序列到功能的 bulk 模型**
   - 代表：ExPecto（±20 kb 序列 → 染色质特征 → 表达）、Enformer（196 kb 序列 → 多任务基因组轨道预测）
   - 优点：利用大规模 bulk 数据（ENCODE、Roadmap）训练，泛化能力强
   - 局限：无法捕捉单细胞水平的细胞类型异质性；PE 互作推断非核心目标

2. **第二代：单细胞扩展**
   - 代表：seq2cells（基于 Enformer 迁移学习，预测单细胞/细胞类型表达）
   - 优点：利用单细胞 RNA-seq 数据，实现细胞类型分辨
   - 局限：主要优化表达预测精度，调控互作推断能力有限

3. **第三代：显式 PE 互作建模**
   - 代表：EPInformer（Transformer 架构，整合序列 + 表观信号 + 染色质互作）
   - 优点：可推断 PE 互作，支持下游调控分析
   - 局限：未显式建模细胞类型间关系；不支持跨条件差异分析

4. **本文主张的位置**：DeepCNet 作为第四代，在单细胞多组学框架下同时实现：(i) 利用预训练序列模型提取高效特征；(ii) 通过跨细胞类型自编码器建模细胞类型关系；(iii) 通过注意力机制显式推断 PE 互作；(iv) 扩展至双条件（疾病 vs 对照）差异 PE 互作与 TF-GRN 重连分析。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有方法忽视细胞类型关系 | 各细胞类型独立建模，无法借用相关信息 | 未显式建模细胞类型间层次/谱系关系 | Results 图 2：DeepCNet 在稀有细胞类型（如 Tregs）上表现更优；Methods「Cross cell-type autoencoder」节 |
| 表达预测精度与调控推断脱节 | 高精度预测模型不提供可解释的 PE 互作 | 多数模型以预测精度为唯一优化目标 | Introduction：现有方法「emphasize predictive accuracy rather than regulatory inference」 |
| 单细胞数据稀疏性 | 单细胞水平表达和可及性噪声大，直接建模困难 | 细胞类型水平聚合降低稀疏性，但损失单细胞异质性 | Methods「Single cell multiome data」节：细胞类型水平聚合后建模 |
| 跨条件差异调控推断缺失 | 疾病 vs 对照的 PE 互作变化难以系统识别 | 现有模型不支持双条件联合建模 | Results 图 5：DeepCNet-D 引入条件特异注意力参数 |
| 序列特征可解释性差 | 端到端序列模型难以定位关键调控元件 | 预训练模型嵌入缺乏直接序列级解释 | Discussion：作者承认「learned sequence representations are less directly interpretable in terms of specific regulatory sequence features」 |

---

## 06 核心思想

### 1) 表面方法

DeepCNet 是一个多模态深度学习框架，包含两个变体：
- **DeepCNet-S**（单条件）：输入为基因启动子及附近（±100 kb）ATAC 峰（候选增强子）的 DNA 序列 + 染色质可及性 + 峰到 TSS 距离，通过预训练 ExPecto 提取序列特征，经特征投影、融合、多头注意力（MHA）编码器推断 PE 互作，最终预测细胞类型特异基因表达。
- **DeepCNet-D**（双条件）：扩展 DeepCNet-S，共享序列特征和 MHA 架构，但引入条件特异可学习参数，联合建模两个条件（如 AD vs 对照），输出条件特异的 PE 注意力分数，其差值即为差异 PE 互作。

### 2) 核心洞察

- **PE 互作是表达预测与调控推断的统一中间表示**：通过注意力机制显式建模启动子-增强子关系，既提升表达预测（利用增强子信息），又提供可解释的调控推断输出。
- **细胞类型关系可通过自编码器隐式编码**：跨细胞类型自编码器学习基因嵌入，使相关细胞类型共享信息，特别有利于稀有细胞类型的预测。
- **条件差异可通过注意力偏置参数化**：在共享 MHA 编码器中引入条件特异偏置项，使模型在保持共享调控架构的同时捕捉条件特异的 PE 变化，避免独立训练两个模型带来的噪声。

### 3) 可能的普适教训 [Analysis]

- **中间表示设计决定模型的可解释性与下游可用性**：将「互作」作为显式中间变量，而非仅作为预测的副产品，是连接预测任务与生物学推断的关键设计选择。
- **共享架构 + 条件特异参数** 是平衡统计功效与条件特异性的有效策略，可迁移至其他双条件/多条件调控比较场景。
- **预训练模型 + 轻量微调** 在数据量有限的单细胞场景中具有明显优势，但需注意预训练嵌入的可解释性瓶颈。

---

## 07 方法总览

- **输入**：
  - 基因启动子序列（±1 kb TSS）
  - 启动子附近 ±100 kb 内的 ATAC 峰（候选增强子）序列（最多 60 个峰，统一长度 2 kb）
  - 每个峰的染色质可及性（ATAC 计数）
  - 峰到 TSS 的距离
  - 细胞类型信息（用于跨细胞类型自编码器）
  - （DeepCNet-D 额外输入：条件标签，如 AD/对照）

- **输出**：
  - 细胞类型特异基因表达预测值（连续值）
  - PE 互作注意力分数（每个启动子-峰对）
  - （DeepCNet-D 额外输出：条件特异 PE 分数及差异分数 ΔAPE）

- **模块**：
  1. 序列编码器（预训练 ExPecto → 特征投影：2×1D 卷积，64 维）
  2. 跨细胞类型自编码器（生成基因嵌入，32 维）
  3. 特征融合（序列特征 + ATAC 特征 + 基因嵌入）
  4. MHA 编码器（3 层 Transformer 块，8 头注意力，64 维）
  5. 表达预测头（全连接层 128→128→1）
  6. （DeepCNet-D）条件特异注意力偏置参数

- **训练**：
  - 损失函数：Smooth L1 Loss（表达预测）
  - 优化器：AdamW，学习率 5×10⁻⁴，权重衰减 1×10⁻⁶
  - 早停：patience = 5 epochs，最大 30 epochs
  - 参数量：约 0.32M
  - 验证策略：12 折交叉染色体验证（chromosomes 划分训练/验证/测试）

- **文字流程**：
  1. 对每个基因，提取启动子序列和附近 ATAC 峰序列，通过预训练 ExPecto 生成序列嵌入
  2. 将序列嵌入与 ATAC 可及性、峰距 TSS 距离拼接，经特征融合块处理
  3. 跨细胞类型自编码器从单细胞 ATAC 数据学习基因嵌入，与序列特征拼接
  4. MHA 编码器对启动子-峰对进行注意力建模，输出 PE 注意力分数
  5. 启动子上下文嵌入（注意力加权）与基因嵌入拼接，经全连接层预测表达
  6. （DeepCNet-D）两个条件共享序列特征，但注意力偏置不同，输出条件特异 PE 分数

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 序列编码器（预训练 ExPecto） | 从 DNA 序列提取高维调控特征 | 序列是调控信息的根本载体；预训练模型提供跨细胞类型的泛化特征 | 输入：启动子/峰序列（one-hot）；输出：2002 维特征 → 投影至 64 维 | Results 图 2：完整模型性能最优；Ablation「w/zero sequence embedding」 | **实测**：移除后表达预测性能大幅下降（Ablation 图 S2），说明序列信息是核心输入 |
| 跨细胞类型自编码器 | 学习基因嵌入，编码细胞类型关系 | 使相关细胞类型共享信息，提升稀有细胞类型预测 | 输入：单细胞 ATAC 基因活性；输出：32 维基因嵌入 | Results 图 2：Tregs（稀有类型）预测优于基线；Ablation「w/o gene embedding」 | **实测**：移除后 PBMC 数据集性能显著下降（Ablation 图 S2），MFC 数据集影响较小 |
| MHA 编码器（注意力掩码） | 建模启动子-峰互作，输出 PE 分数 | 显式建模 PE 互作是调控推断的核心；注意力权重可解释 | 输入：64 维特征矩阵（启动子+峰）；输出：PE 注意力分数 + 上下文嵌入 | Results 图 3：PE 推断与 ChIA-PET 和 CRISPR 数据一致性高 | **预期**：移除后 PE 推断不可用，表达预测可能下降（因失去增强子信息整合） |
| 条件特异注意力偏置（DeepCNet-D） | 捕捉两条件间的 PE 互作差异 | 使模型能识别疾病相关的调控变化 | 输入：共享 MHA 输出 + 条件标签；输出：条件特异 PE 分数 | Results 图 5：DeepCNet-D 在 AD 数据上识别出差