## 01 基本信息

- **标题**：EpiZoo: a DNA sequence-aware foundation model for cross-species single-cell epigenomics
- **作者与单位**：Keyi Li; Xiaoyang Chen; Qun Jiang; Zian Wang; Hairong Lv; Rui Jiang（单位未提供）
- **期刊/预印本平台**：bioRxiv
- **年份**：2026
- **论文类型**：预印本（方法学/基础模型）
- **领域**：单细胞表观基因组学 × 基础模型（foundation model）
- **关键词**：single-cell epigenomics, foundation model, DNA sequence, cross-species, scATAC-seq, mixture-of-experts, regulatory genomics
- **DOI/arXiv 号**：10.64898/2026.09.24.754017
- **代码**：未提供
- **数据**：Omni-scATAC corpus（约 2090 万细胞，多物种，人工整理）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「蛋白质-DNA 互作 × AI」方向中的**序列-表观组联合建模**分支。虽不直接预测 TF–DNA 结合，但其核心设计——将 DNA 序列编码的调控信息（含 TF 结合 motif 信号）与染色质可及性（chromatin accessibility）整合进统一模型——为 TF–DNA 结合机制研究提供了可迁移的序列感知架构与跨物种比较框架。

## 02 一句话总结

EpiZoo 将多物种单细胞表观基因组谱（scATAC-seq）转换为整合 DNA 序列调控信息的"细胞句子"，通过 mixture-of-experts transformer（26 亿参数）在约 2090 万细胞上预训练，在特征提取、细胞类型注释、数据填补等任务上达到 SOTA，并支持跨物种调控保守性分析与突变优先级排序。

## 03 研究问题

- **具体问题**：现有单细胞表观基因组基础模型受限于单一物种（依赖基因组坐标对齐），且未充分利用 DNA 序列中编码的调控信息（如 TF 结合 motif），无法实现跨物种的调控程序学习与比较。
- **为什么重要**：跨物种单细胞表观图谱（如灵长类进化研究）需要统一框架来比较调控元件的保守性与分化；同时，DNA 序列中的调控信息（TF motif、染色质状态）是理解基因调控机制的关键，现有模型将其忽略。
- **现有方法不足**：坐标依赖导致无法跨物种迁移；纯表观特征（如 peak 矩阵）缺乏序列上下文，难以解释调控机制；缺乏大规模多物种预训练语料。
- **精确研究问题（Can...?）**：Can a DNA sequence-aware foundation model pretrained on multi-species single-cell epigenomic atlases learn universal regulatory programs that generalize across species and support downstream tasks including annotation, imputation, mutation prioritization, and cross-species regulatory comparison?

## 04 背景与发展脉络

*注：以下脉络基于本文框架，未经外部核验。*

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|----------|
| 早期 scATAC 分析 | peak calling + 差异可及性 | 简单、可解释 | 无法跨细胞整合、缺乏序列上下文 | — |
| 单细胞基础模型（同物种） | scBERT, scGPT 等（RNA）；scATAC 专用模型 | 捕获细胞异质性 | 坐标依赖、单物种、忽略 DNA 序列 | 被超越 |
| 序列模型（DNA 语言模型） | Enformer, Borzoi 等 | 直接从序列预测调控 | 非单细胞、无细胞类型粒度 | 被整合 |
| 跨物种表观模型 | 少数多物种 scATAC 模型 | 跨物种比较 | 未显式编码序列调控信息 | 被超越 |
| **本文** | **EpiZoo** | **序列感知 + 多物种 + 单细胞粒度 + MoE 扩展** | — | **当前 SOTA** |

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 坐标依赖 | 模型无法跨物种迁移 | 现有模型以基因组坐标（如 peak 位置）为锚点，不同物种坐标不可比 | 摘要："current models remain largely confined to individual species by genomic coordinate dependence" |
| 序列信息缺失 | 模型无法利用 DNA 编码的调控信息 | 现有模型仅用表观特征（如可及性矩阵），忽略序列中的 TF motif 与调控元件 | 摘要："overlook regulatory information encoded in DNA sequences" |
| 跨物种语料缺乏 | 无法学习通用调控程序 | 缺乏大规模多物种单细胞表观组预训练数据 | 作者人工构建 Omni-scATAC corpus（约 2090 万细胞） |
| 模型容量不足 | 难以捕获全谱系细胞多样性 | 现有模型参数量有限，无法覆盖多物种、多细胞类型 | EpiZoo 采用 26 亿参数 MoE 架构 |

## 06 核心思想

1. **表面方法**：将单细胞表观基因组谱（scATAC-seq）转换为"细胞句子"（cell sentences），每个句子整合三类信息——DNA 序列编码的调控信息、序列无关的表观基因组上下文、基于可及性的重要性权重；用 mixture-of-experts transformer 预训练。

2. **核心洞察**：DNA 序列本身携带跨物种保守的调控密码（如 TF 结合 motif），将其与表观可及性联合建模，可让模型学到物种间共享的调控程序（regulatory programs），从而突破坐标依赖，实现跨物种泛化。

3. **可能的普适教训 [Analysis]**：在单细胞表观组学中，"序列"是连接物种间调控机制的天然桥梁——即使基因组坐标不保守，序列层面的调控逻辑（motif、语法）仍可迁移。这提示 TF–DNA 结合研究：将序列特征作为跨物种先验，可增强模型的可迁移性与机制可解释性。

## 07 方法总览

- **输入**：多物种单细胞 scATAC-seq 谱（peak × cell 矩阵）+ 对应基因组 DNA 序列
- **输出**：细胞嵌入（cell embeddings）、可及性预测、细胞类型注释、突变优先级分数
- **核心模块**：
  1. 细胞句子构建器（cell sentence constructor）：将表观谱 + 序列信息编码为 token 序列
  2. Mixture-of-Experts (MoE) Transformer：26 亿参数，稀疏激活
  3. 预训练任务：masked cell sentence modeling（推测，具体任务未提供）
- **训练**：在 Omni-scATAC corpus（约 2090 万细胞，多物种）上预训练
- **工具**：未提供具体框架
- **反馈回路**：预训练 → 下游任务微调/零样本评估 → 跨物种比较分析
- **文字流程**：多物种 scATAC 谱 → 提取 peak 可及性 + 对应 DNA 序列 → 构建细胞句子（整合序列调控信息、表观上下文、可及性权重）→ MoE Transformer 编码 → 预训练学习跨物种调控程序 → 下游任务（注释、填补、突变优先级、跨物种比较）

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 细胞句子构建器 | 将表观谱 + 序列信息转换为统一 token 序列 | 统一异构输入，使模型可处理多物种数据 | 输入：scATAC 谱 + DNA 序列；输出：cell sentence tokens | 摘要："converts ... into compact cell sentences" | 预期影响 [Analysis]：移除后模型退化为纯表观模型，丧失跨物种迁移能力 |
| DNA 序列编码模块 | 提取序列中的调控信息（如 TF motif） | 提供跨物种保守的调控先验 | 输入：peak 区域 DNA 序列；输出：序列嵌入 | 摘要："integrate DNA-encoded regulatory information" | 预期影响 [Analysis]：移除后无法支持"从序列预测可及性"与跨物种比较 |
| 可及性重要性权重 | 加权不同 peak 对细胞状态的贡献 | 区分功能性 peak 与噪声 | 输入：可及性值；输出：权重 | 摘要："accessibility-based importance" | 预期影响 [Analysis]：移除后可能降低细胞嵌入的生物学分辨率 |
| MoE Transformer | 大规模参数下高效编码细胞句子 | 捕获全谱系细胞多样性 | 输入：cell sentence；输出：细胞嵌入 | 摘要："mixture-of-experts transformer ... 2.6 billion parameters" | 预期影响 [Analysis]：移除 MoE 后参数量下降，可能降低表达力 |
| 预训练任务 | 学习跨物种调控程序 | 无监督学习通用调控表示 | 输入：masked cell sentences；输出：重建 | 摘要："pretrained on ... Omni-scATAC corpus" | 预期影响 [Analysis]：移除后模型无跨物种先验，下游性能下降 |

*注：以上"预期影响"均为 [Analysis] 推断，原文未提供消融实验。*

## 09 关键公式符号

不适用。原文为预印本摘要，未提供具体公式。核心概念（cell sentence、MoE、可及性权重）以文字描述为主，无数学形式化。

## 10 实验设计与证据链

- **数据集**：Omni-scATAC corpus（约 2090 万细胞，多物种，人工整理，用于预训练）；外部数据集（排除在预训练之外，用于评估）
- **指标**：未提供具体指标（如 F1、AUC、准确率等）
- **基线**：未提供具体基线模型名称
- **预算/骨干/仪器**：未提供
- **oracle 输入**：未提供
- **评测协议**：在外部数据集上评估特征提取、细胞类型注释、数据填补；跨物种泛化评估；灵长类进化调控保守性/分化分析；癌症体细胞突变优先级排序；从 DNA 序列预测细胞类型特异性染色质可及性

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 特征提取 | 细胞嵌入质量 | 外部数据集，SOTA 对比 | 达到 SOTA | 细胞嵌入捕获跨物种调控信息 | 未提供具体指标，无法量化优势幅度 | 摘要 |
| 细胞类型注释 | 注释准确性 | 外部数据集，SOTA 对比 | 达到 SOTA | 序列感知提升注释泛化 | 未提供跨物种注释的具体物种数 | 摘要 |
| 数据填补 | 缺失数据恢复 | 外部数据集，SOTA 对比 | 达到 SOTA | 模型理解表观-序列关系 | 未提供填补的生物学验证 | 摘要 |
| 跨物种泛化 | 进化远物种扩展 | 未提供具体物种 | 支持扩展 | 序列感知架构支持跨物种 | 未提供零样本 vs 微调对比 | 摘要 |
| 灵长类调控比较 | 保守性/分化分析 | 灵长类进化数据 | 支持分析 | 可比较调控保守与分化 | 未提供具体保守性量化指标 | 摘要 |
| 突变优先级排序 | 癌症突变功能影响 | 癌症数据，上下文感知 | 支持排序 | 序列+表观上下文提升突变优先级 | 未提供与现有突变预测工具的对比 | 摘要 |
| 序列→可及性预测 | 从 DNA 预测染色质状态 | 跨基因组区域与物种 | 支持预测 | 模型学到序列-可及性映射 | 未提供预测精度与 Enformer 等对比 | 摘要 |

## 11 结论正确解读

- **任务范围**：本文结论限于单细胞表观基因组学（scATAC-seq）的基础模型预训练与下游任务，不涉及 TF–DNA 结合的直接预测或机制解析。
- **oracle/真值输入**：预训练数据为人工整理的 Omni-scATAC corpus，标注（如细胞类型）来源未说明；下游任务的真值标签（如突变致病性）未说明。
- **端到端状态**：模型端到端预训练 + 下游微调/评估，但具体训练细节（损失函数、微调策略）未提供。
- **算力成本**：未提供训练成本、GPU 数量、训练时间。
- **历史数据依赖**：依赖 scATAC-seq 数据质量与 peak calling 流程；跨物种比较依赖物种基因组注释质量。
- **模型依赖**：MoE 架构、tokenization 策略、序列编码方式均未公开细节，复现性受限。
- **最难情形**：进化距离远的物种（如非哺乳类）的调控比较、罕见细胞类型的注释、非编码突变的功能预测。
- **群体/领域边界**：结论适用于有 scATAC-seq 数据的物种；不适用于无参考基因组的物种；未涉及蛋白质结构或直接 TF 结合动力学。
- **不确定性**：未提供置信区间、统计检验细节或误差分析。
- **有边界的复述**：EpiZoo 在约 2090 万细胞的多物种 scATAC 数据上预训练，通过整合 DNA 序列信息实现跨物种单细胞表观组下游任务的 SOTA 性能，并支持调控保守性分析与突变优先级排序；但具体性能指标、消融实验、训练细节未在摘要中披露，需全文验证。

## 12 作者自认局限

在提供的材料（摘要）中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限，[Analysis] 推断）：
- 依赖 scATAC-seq 数据质量与 peak calling 流程
- 跨物种比较受限于基因组注释质量
- 模型规模（26 亿参数）可能带来部署成本
- 未披露与现有序列模型（如 Enformer）的直接对比

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| "SOTA" 声明缺乏具体指标 | 摘要未提供数值，可能优势幅度有限或仅在特定任务 | 无法评估实际增益 | 查阅全文实验部分，对比具体 F1/AUC 等 | 摘要仅定性描述 |
| 未披露基线模型 | 可能对比了较弱基线 | 影响 SOTA 声明的可信度 | 检查全文基线选择 | 摘要未列基线 |
| 序列信息整合方式未详述 | 可能仅用 motif 计数而非全序列编码 | 影响机制可解释性 | 查阅方法部分 tokenization 细节 | 摘要仅提"DNA-encoded regulatory information" |
| 跨物种泛化未量化 | 未说明测试物种数量与进化距离 | 无法判断泛化边界 | 查阅全文物种列表与零样本结果 | 摘要仅提"evolutionarily diverse species" |
| 突变优先级排序缺乏基准对比 | 未与 ClinVar、CADD 等现有工具对比 | 实际临床价值未知 | 查阅全文对比实验 | 摘要仅提"context-aware prioritization" |
| 未提供消融实验 | 无法确认各模块（序列、权重、MoE）的独立贡献 | 核心设计 claim 缺乏证据 | 查阅全文消融表 | 摘要未提消融 |
| 预训练语料构建标准未披露 | 人工整理可能引入选择偏差 | 影响模型泛化 | 查阅数据筛选标准 | 摘要仅提"manually curated" |

## 14 学到什么

**Agent 提炼的知识候选**

1. **序列感知的跨物种建模策略**：将 DNA 序列信息（含 TF 结合 motif 信号）与表观可及性联合编码，可突破坐标依赖，实现跨物种调控程序学习。→ 迁移到 TF–DNA 结合：可在多物种 TF 结合数据上构建序列感知模型，利用序列保守性增强结合预测的泛化性。

2. **"细胞句子"（cell sentence）概念**：将高维表观谱转换为紧凑的 token 序列，使 transformer 可直接处理。→ 迁移：可将 TF–DNA 结合事件（如 ChIP-seq peaks + 序列）编码为"结合句子"，用语言模型范式建模结合语法（binding grammar）。

3. **MoE 架构用于大规模单细胞模型**：26 亿参数 MoE 在保持高效推理的同时扩展模型容量。→ 迁移：TF–DNA 结合预测模型可借鉴 MoE 设计，对不同细胞类型/物种使用不同 expert，提升多任务泛化。

4. **可及性重要性加权**：以可及性作为 peak 重要性的先验权重。→ 迁移：在 TF–DNA 结合预测中，可用染色质可及性作为特征重要性先验，增强模型对功能位点的关注。

5. **跨物种调控保守性/分化分析框架**：利用统一模型比较灵长类调控元件。→ 迁移：可用于比较 TF 结合位点在物种间的保守性，识别 lineage-specific binding events。

6. **从序列预测细胞类型特异性可及性**：模型支持"序列 → 可及性"的预测。→ 迁移：类似地可构建"序列 → TF 结合"预测模型，用于非测序物种或变异效应预测。

## 15 与已有知识连接

- **Avsec et al. (2021) Enformer**：从序列预测表观信号（含可及性），EpiZoo 的"序列→可及性"预测可视为 Enformer 思路在单细胞层面的扩展，但 EpiZoo 额外整合了细胞状态上下文。
- **scGPT / scBERT**：单细胞 RNA 基础模型，EpiZoo 将其范式迁移到表观组学，并引入序列感知。
- **Zhou & Troyanskaya (2015) DeepSEA**：从序列预测染色质特征，EpiZoo 的突变优先级排序与其目标类似，但 EpiZoo 是单细胞分辨率且跨物种。
- **TF–DNA 结合预测（如 DeepBind, DeepSEA, BPNet）**：EpiZoo 的序列编码模块与这些方法共享 motif 识别逻辑，但其创新在于将序列信息与单细胞表观状态联合建模。
- **跨物种调控比较（如 Zoonomia）**：EpiZoo 提供了一种基于基础模型的替代框架，无需多序列比对即可比较调控程序。
- **候选方向 [Analysis]**：EpiZoo 的架构可直接扩展为"TF–DNA 结合基础模型"——将 ChIP-seq 或 HT-SELEX 数据编码为结合句子，预训练后预测未见 TF 或物种的结合特异性。

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：TF-BindZoo：基于 EpiZoo 架构的跨物种 TF–DNA 结合基础模型
   - **来源局限/观察**：EpiZoo 虽序列感知，但未直接建模 TF–DNA 结合事件；现有 TF 结合预测模型多为单物种、单 TF，缺乏跨物种泛化。
   - **核心假设**：将 TF 结合事件（peak + 序列 + 细胞上下文）编码为"结合句子"，预训练后可泛化到未见 TF 与物种。
   - **增量**：在 EpiZoo 的 cell sentence 基础上引入 TF 身份 token，构建 binding-aware 预训练任务。
   - **初步方法**：收集多物种 ChIP-seq 数据，构建 TF–peak–序列三元组；用 MoE transformer 预训练 masked binding prediction；下游任务包括未见 TF 结合预测、跨物种结合保守性分析。
   - **验证方式**：在留出物种/TF 上评估 AUC；与 DeepBind、BPNet 对比；验证跨物种零样本性能。
   - **创新状态**：unverified

2. **候选名称**：序列-表观联合的 TF 结合 motif 可解释性分析
   - **来源局限/观察**：EpiZoo 声称整合"DNA-encoded regulatory information"，但未提供 motif 层面的可解释性分析。
   - **核心假设**：EpiZoo 的注意力权重可揭示细胞类型特异的 TF motif 重要性。
   - **增量**：对 EpiZoo 进行注意力分析，提取 cell-type-specific motif 重要性图谱。
   - **初步方法**：用 in-silico mutagenesis 或 attention scoring 识别关键 motif；与已知 TF motif 数据库（JASPAR）比对。
   - **验证方式**：与 ChIP-seq 验证的 TF 结合位点重叠率；与已知细胞类型 marker TF 一致性。
   - **创新状态**：unverified

3. **候选名称**：EpiZoo 用于非编码变异对 TF 结合影响的单细胞分辨率预测
   - **来源局限/观察**：EpiZoo 支持突变优先级排序，但未专门针对 TF 结合破坏效应。
   - **核心假设**：EpiZoo 的序列感知表示可预测 SNP 对 TF 结合亲和力的影响，且具有细胞类型特异性。
   - **增量**：在 EpiZoo 基础上增加 delta-binding score 预测头。
   - **初步方法**：用 eQTL 或 sQTL 数据中已知的 allele-specific binding 事件微调；评估在 GWAS 变异上的富集。
   - **验证方式**：与 DeepSEA、Enformer 的变异效应预测对比；实验验证（如 MPRA）。
   - **创新状态**：unverified

4. **候选名称**：跨物种 TF 结合语法（binding grammar）的解析
   - **来源局限/观察**：EpiZoo 的 cell sentence 范式暗示序列组合语法，但未显式建模 TF 协同结合（co-binding）。
   - **核心假设**：Transformer 的 attention 可捕获 TF 间的协同结合模式，且这些模式在物种间保守。
   - **增量**：分析 EpiZoo attention 中 TF motif 对的共现模式，构建跨物种 binding grammar。
   - **初步方法**：提取 attention 权重，聚类 TF motif 对；比较不同物种的共现网络。
   - **验证方式**：与已知 TF 协同结合数据库（如 ENCODE co-binding）比对；用 CRISPR 干扰验证预测的协同关系。
   - **创新状态**：unverified