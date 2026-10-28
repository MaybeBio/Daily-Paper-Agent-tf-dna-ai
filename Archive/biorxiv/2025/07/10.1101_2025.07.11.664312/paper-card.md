## 01 基本信息

- **标题**：PromoterAtlas: decoding regulatory sequences across Gammaproteobacteria using a transformer model
- **作者**：Coppens L; Ledesma-Amaro R
- **单位**：未提供（作者信息未在材料中给出）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2025
- **论文类型**：预印本（方法学 + 工具开发）
- **领域**：细菌调控基因组学 × Transformer 深度学习
- **关键词**：promoter prediction, transformer, Gammaproteobacteria, sigma factor, regulatory sequence, genome annotation
- **DOI/arXiv 号**：10.1101/2025.07.11.664312
- **代码**：https://github.com/LucasCoppens/PromoterAtlas
- **数据**：https://huggingface.co/datasets/LCoppens/PromoterAtlas-data
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文聚焦细菌（Gammaproteobacteria）启动子及 σ 因子结合位点的识别与全基因组注释，属于「TF–DNA 互作 × 深度学习」方向。与真核 TF–DNA 结合机制研究相比，本文的可迁移点在于：(1) 用无监督掩码预训练规避标注数据稀缺问题；(2) 用嵌入空间分析揭示跨物种的调控元件进化关系；(3) 用分割头实现全基因组注释。其方法框架（预训练 + 微调 + 嵌入分析）可直接迁移到真核 TF–DNA 结合位点预测任务。

---

## 02 一句话总结

本文构建了一个 180 万参数的 Transformer 模型（PromoterAtlas），在 3371 种 Gammaproteobacteria 的约 900 万条启动子上游 200 nt 序列上做掩码预训练，通过分割头实现五种 σ 因子启动子的全基因组注释，并证明其嵌入可预测转录/翻译水平且编码跨物种的 σ 因子进化关系。

---

## 03 研究问题

- **具体问题**：能否用一个跨物种训练的 Transformer 模型，实现 Gammaproteobacteria 全基因组范围的启动子注释（含 σ 因子类型区分），并利用其嵌入预测基因表达水平？
- **为什么重要**：细菌启动子预测长期受限于小数据集、单物种训练、二分类框架（仅判断"是/否启动子"而非全面注释），导致新测序基因组的调控景观注释困难。
- **现有方法不足**：
  - 依赖实验验证的启动子标注，数据量小；
  - 多为单物种（尤其 E. coli）训练，跨物种泛化差；
  - 仅做二分类，无法区分 σ 因子类型，也无法提供全基因组注释。
- **精确研究问题（Can...?）**：Can a transformer model pre-trained on unlabeled upstream sequences across 3,371 gammaproteobacterial species enable accurate whole-genome promoter annotation with σ factor specificity and cross-species expression prediction?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 的叙述，标注为「仅本文框架」，未经外部核验。

1. **通用基因组 Transformer 时代**：Enformer、Nucleotide Transformer、Evo 2、DNABert-2 等大规模模型展示了 DNA 序列建模能力；蛋白领域 ESM-2/ESMFold 证明纯序列模型可预测结构。
2. **细菌启动子预测的传统方法**：PWM → HMM → SVM → CNN → RNN → Transformer。深度学习方法在精度上未显著超越传统方法，受限于：
   - 标注数据稀缺；
   - 单物种训练；
   - 二分类而非全面注释。
3. **本文主张的位置**：用无监督掩码预训练 + 跨物种数据 + 分割头，构建首个面向 Gammaproteobacteria 的端到端全基因组启动子注释工具，并展示嵌入的多功能性（表达预测、进化关系编码）。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 标注数据稀缺 | 实验验证的启动子数量有限，模型训练数据不足 | 启动子实验验证成本高、覆盖度低 | Introduction 节："scarcity of experimentally validated promoters creates a bottleneck in training data" |
| 单物种训练限制泛化 | 多数模型仅在 E. coli 上训练，跨物种表现差 | 单物种数据无法覆盖调控元件的多样性 | Introduction 节："models are often trained on data limited to single species, most often Escherichia coli, limiting both dataset size and model generalisability" |
| 二分类框架信息量低 | 仅判断"是否启动子"，无法区分 σ 因子类型 | 缺乏全面注释框架 | Introduction 节："existing approaches typically focus on classifying isolated sequences rather than providing a comprehensive annotation framework" |
| 全基因组注释缺失 | 新测序基因组无法快速获得调控注释 | 缺乏端到端工具 | Introduction 节："automated whole-genome promoter annotation an unresolved challenge" |
| 传统方法精度瓶颈 | 深度学习方法未显著超越 PWM/HMM | 数据与框架限制而非模型能力 | Introduction 节："Deep learning approaches have struggled to improve prediction accuracy over traditional methods" |

---

## 06 核心思想

### 1) 表面方法

- 构建 1.8M 参数 Transformer（DNATransformer 架构），在 3371 种 Gammaproteobacteria 的约 900 万条 200 nt 上游序列上做掩码 token 预测预训练。
- 在预训练模型上训练分割头，实现五种 σ 因子（σ70/σ38, σ54, σ32, σ28, σ24）启动子的全基因组注释。
- 用冻结的预训练嵌入 + 预测头做转录/翻译水平回归。

### 2) 核心洞察

- **无监督预训练规避标注瓶颈**：利用基因组中天然存在的大量未标注上游序列，让模型自行发现调控模式，不依赖实验标注。
- **跨物种数据提供进化信号**：Gammaproteobacteria 内 σ 因子核心启动子结构保守，跨物种训练既扩大数据量又保留核心机制。
- **嵌入空间编码功能与进化信息**：深层嵌入按 σ 因子身份聚类（而非物种），说明模型学到了调控元件的进化保守性；嵌入还可直接用于表达预测，说明其编码了定量调控信息。

### 3) 可能的普适教训 [Analysis]

- 对 TF–DNA 互作研究：当实验标注稀缺时，跨物种/跨细胞类型的无监督预训练是可行的替代路径，前提是目标结合机制在进化上保守。
- 嵌入空间分析（如 UMAP 聚类）可作为模型"是否学到生物学结构"的诊断工具，而不只依赖下游任务精度。
- 分割头设计（而非分类头）使模型天然适配全基因组扫描任务，这一思路可迁移到真核 TF 结合位点的全基因组注释。

---

## 07 方法总览

- **输入**：200 nt 的 DNA 序列（基因上游区域），one-hot 编码为 4 通道。
- **输出**：
  - 预训练：掩码位置的核苷酸概率分布（4 类）；
  - 分割头：每个位置的 12 类标注（无特征、各 σ 因子的 −10/−35 motif 等）；
  - 表达预测头：归一化转录水平或蛋白表达水平（标量回归）。
- **模块**：
  1. 线性编码器（4 → 128 维）；
  2. 8 个 DNATransformer 块（双卷积 + rotary attention + FFN，各有残差连接）；
  3. 线性解码器（128 → 4 维，用于预训练）；
  4. 分割头（3 层 1D 卷积，kernel size 10，输出 12 类）；
  5. 表达预测头（2 层 1D 卷积 + 2 层全连接）。
- **训练**：
  - 预训练：掩码 20 个随机位置（10%），交叉熵损失，AdamW，batch size 1024，初始 LR 1e-3，264 epochs（约 5 天，单张 A100）；
  - 分割头：交叉熵损失，Adam，LR 1e-5，batch size 5，early stopping patience 10；
  - 表达预测：AdamW，LR 1e-5，batch size 32，MSE 损失，early stopping patience 10。
- **数据**：NCBI 基因组数据库，3371 种 Gammaproteobacteria，约 900 万条 200 nt 上游序列；训练:验证 = 9:1。
- **反馈回路**：无显式主动学习或迭代优化回路；预训练 → 微调为单向流程。
- **假设**：上游 200 nt 区域富集启动子及调控元件；Gammaproteobacteria 内 σ 因子核心启动子结构保守。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 线性编码器 | 将 one-hot 4 维投影到 128 维隐藏空间 | 降低维度、学习核苷酸嵌入 | 输入：200×4 one-hot；输出：200×128 | Methods 节描述 | 预期：模型无法训练（维度不匹配）[预期效应] |
| 双卷积层（kernel size 3） | 捕获局部序列模式（如 motif 短片段） | DNA 调控元件多为 6-10 bp 的短保守 motif，卷积适合局部模式 | 输入：200×128；输出：200×128 | Methods 节："double convolution with window size 3" | 预期：丧失局部 motif 识别能力，预训练损失上升 [预期效应] |
| Rotary attention 层 | 建模长程依赖（如 −10 与 −35 box 间的间隔关系） | 启动子功能依赖 motif 间的间距与相对位置 | 输入：200×128；输出：200×128 | Methods 节："rotary attention layer... encodes relative positions" | 预期：无法建模 motif 间距约束，σ 因子区分能力下降 [预期效应] |
| 线性解码器 | 将隐藏表示映射回 4 维核苷酸概率 | 实现掩码 token 预测的预训练目标 | 输入：200×128；输出：200×4 | Methods 节 | 预期：预训练无法进行 [预期效应] |
| 分割头（3 层 1D 卷积） | 将嵌入转为逐位置 12 类标注 | 实现全基因组启动子注释 | 输入：200×128 嵌入；输出：200×12 概率 | Methods 节；Results 图 3 | 未提供消融实验；预期：移除后无法输出注释 [预期效应] |
| 表达预测头 | 从嵌入回归转录/翻译水平 | 验证嵌入编码定量调控信息 | 输入：池化嵌入；输出：标量 | Results 图 5 | 未提供消融实验；预期：移除后丧失表达预测能力 [预期效应] |
| 预训练 + 冻结微调策略 | 先无监督学习通用序列特征，再冻结 backbone 训练任务头 | 规避标注数据稀缺，防止过拟合 | 预训练权重 → 冻结 → 任务头训练 | Methods 节 | 预期：若解冻微调可能提升任务精度但增加过拟合风险 [预期效应] |

---

## 09 关键公式符号

本文未提供显式的数学公式。以下为从方法描述中可推断的必要符号：

- **掩码预训练损失**（交叉熵，仅掩码位置）：
  \[
  \mathcal{L}_{\text{MLM}} = -\frac{1}{M} \sum_{i \in \mathcal{M}} \log p(x_i | x_{\backslash \mathcal{M}})
  \]
  其中 \(\mathcal{M}\) 为掩码位置集合，\(M = |\mathcal{M}|\)，\(x_i\) 为位置 \(i\) 的真实核苷酸，\(p\) 为模型预测概率。

- **分割头损失**（逐位置交叉熵）：
  \[
  \mathcal{L}_{\text{seg}} = -\frac{1}{L} \sum_{i=1}^{L} \log p(y_i | \mathbf{h}_i)
  \]
  其中 \(L = 200\) 为序列长度，\(y_i \in \{1, \dots, 12\}\) 为位置 \(i\) 的标注类别，\(\mathbf{h}_i\) 为 backbone 在位置 \(i\) 的隐藏表示。

- **表达预测损失**（MSE）：
  \[
  \mathcal{L}_{\text{expr}} = \frac{1}{N} \sum_{j=1}^{N} (\hat{e}_j - e_j)^2
  \]
  其中 \(\hat{e}_j\) 为预测表达值，\(e_j\) 为真实值。

- **Rotary position embedding**（旋转位置编码）：对 query/key 向量按频率旋转，使 attention 对相对位置敏感。具体公式未在文中给出，可参考 RoPE 原论文（未在本文引用列表中确认）。

---

## 10 实验设计与证据链

### 数据集与评测协议

| 项目 | 详情 |
|------|------|
| 预训练数据 | NCBI 基因组数据库，3371 种 Gammaproteobacteria，约 900 万条 200 nt 上游序列 |
| 预训练/验证划分 | 9:1 |
| 分割头训练数据 | 318 条人工标注序列（147 σ70/σ38, 50 σ54, 76 σ32, 27 σ28, 18 σ24） |
| 分割头验证 | 留出 20% 作为验证集 |
| 转录预测数据 | Lafleur et al. (2022)：5,392 条；Hossain et al. (2020)：4,350 条；Urtecho et al. (2019)：10,898 条；Yu et al. (2021)：1,494 条 |
| 转录预测评测 | 80% 训练 / 10% 验证 / 10% 测试，Pearson 相关系数 |
| 蛋白表达预测数据 | Kosuri et al. (2013)，含启动子+RBS 序列及蛋白表达测量 |
| 蛋白表达预测评测 | 8:1:1 划分，Pearson 相关系数 |
| 全基因组注释验证 | E. coli ChIP-seq 数据（Cho et al., 2014）；GO 富集分析 |
| 硬件 | 单张 NVIDIA A100（预训练约 5 天） |

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 预训练收敛与泛化 | 无监督掩码预训练可在跨物种数据上收敛 | 训练/验证损失对比 | 训练 264 epochs 收敛，验证损失良好（具体数值未提供） | 模型能学习跨物种的序列模式 | 无法判断是否达到 SOTA 预训练性能 | Results 节；图 S1 |
| 全基因组启动子注释（E. coli） | 分割头能识别真实启动子 | 与 ChIP-seq 数据比对 | 多数预测启动子落在 ChIP-seq 峰内；σ32 预测 13 个全部验证（100% 准确率） | 注释工具具有较高精度 | 未提供全基因组 precision/recall 曲线；样本量小 | Results 图 3B |
| 与现有工具对比 | PromoterAtlas 优于 SAPPHIRE 和 ProPr | 同一 ChIP-seq 验证标准 | PromoterAtlas 验证率 70%；SAPPHIRE 58%；ProPr 62%；naive baseline 56% | PromoterAtlas 精度更高 | 未提供统计显著性检验；naive baseline 本身 56% 说明 ChIP-seq 验证标准宽松 | Results 图 3B |
| 跨物种注释 | 模型能注释非 E. coli 物种 | 对 P. aeruginosa, L. pneumophila 等注释 | 各物种注释数量不同（206-615 个启动子） | 工具可跨物种使用 | 无独立实验验证这些预测 | Results 图 3C |
| GO 富集分析 | 预测启动子下游基因功能与 σ 因子已知角色一致 | 各 σ 因子下游基因 GO 富集 | σ70→基础转录/翻译；σ54→鞭毛/氮利用；σ32→热激/蛋白折叠；σ28→趋化/鞭毛；σ24→应激 | 注释具有生物学意义 | GO 分析基于注释基因功能，非直接实验验证 | Results 图 3D |
| 嵌入空间 UMAP 分析 | 深层嵌入按 σ 因子聚类 | 不同层（block 1, 3, 5, 7）嵌入对比 | 浅层按 GC 含量聚类；深层按 σ 因子聚类 | 模型学到 σ 因子的进化保守性 | 未量化聚类纯度；样本量有限 | Results 图 4 |
| 转录水平预测 | 嵌入编码定量调控信息 | PromoterAtlas 嵌入 vs 直接 one-hot 卷积 | PromoterAtlas 模型在 4 个数据集上均优于简单卷积（具体数值未提供） | 预训练嵌入提升表达预测 | 未与 SOTA 表达预测工具（如 PromoterCalculator）做系统对比 | Results 图 5B |
| 蛋白表达预测 | 嵌入可预测翻译水平 | Kosuri et al. (2013) 数据 | Pearson r = 0.79 | 嵌入捕获转录+翻译调控信息 | 低于 Kosuri 的 ANOVA 模型（r = 0.82）；未做显著性检验 | Results；图 S6 |

---

## 11 结论正确解读

- **任务范围**：本文的"启动子注释"限定于 Gammaproteobacteria 纲内，且仅覆盖五种 σ 因子（σ70/σ38, σ54, σ32, σ28, σ24）。不适用于其他细菌门类或古菌。
- **Oracle/真值输入**：分割头训练数据为人工基于 logit 图标注的 318 条序列，标注标准是"明显可识别的 motif"，存在主观性和选择偏差。ChIP-seq 验证仅针对 E. coli。
- **端到端状态**：全基因组注释流程是端到端的（输入 GenBank → 输出注释），但分割头训练依赖人工标注，并非完全自动化。
- **算力成本**：预训练约 5 天（单张 A100），对一般实验室可复现，但不算轻量。
- **历史数据依赖**：预训练数据来自 NCBI 已注释基因组，依赖基因组注释质量；表达预测数据全部来自 E. coli，跨物种表达预测能力未验证。
- **最难情形**：非 E. coli 物种的启动子注释缺乏独立实验验证；σ70/σ38 与 σ38 的区分困难（作者将其合并为一类）；低表达基因的启动子可能因 motif 不明显而漏检。
- **不确定性**：验证率 70% 可能低估实际性能（ChIP-seq 条件依赖性），但也可能高估（人工标注偏差 + 小样本）。
- **有边界的复述**：PromoterAtlas 是一个在 Gammaproteobacteria 跨物种数据上预训练的 Transformer 模型，能够以较高精度注释五种 σ 因子的启动子，其嵌入可预测 E. coli 中的表达水平，且深层嵌入按 σ 因子身份聚类。这些结论仅限于 Gammaproteobacteria 纲，且表达预测的跨物种泛化尚未验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 训练数据缺乏实验验证 | 预训练数据为未标注的上游序列，分割头训练数据仅 318 条人工标注序列 | 纳入更多实验验证数据以提升模型性能 | Discussion 节："further refinement with additional experimental data" |
| 保守的注释策略 | 仅标注"明显可识别的 motif"，可能漏检弱启动子 | 用更多数据扩展可识别 motif 的范围 | Discussion 节："focus only on the most clearly recognisable regulatory patterns" |
| 表达预测限于 E. coli | 训练和验证数据均来自 E. coli | 扩展到非模式生物的标准化表达数据集 | Discussion 节："comprehensive cross-species validation of expression prediction capabilities remains challenging due to the scarcity of standardised expression datasets for non-model organisms" |
| 模型为早期版本 | 作者称当前工作是"early step" | 纳入更多实验数据、扩展其他细菌类群、开发更复杂的调控元件工程工具 | Discussion 节："the current work represents an early step" |

**作者提及的相关约束**（非正式局限）：
- σ70 与 σ38 的 motif 过于相似，无法在分割任务中区分，故合并为一类（Results 节）。
- 预训练数据中 Pseudomonas 物种占比高，可能影响对其他属的识别精度（Results 图 1C 相关讨论）。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 分割头训练数据仅 318 条且为人工标注 | 标注标准是"logit 图中明显可识别的 motif"，存在主观性；模型可能只学会识别高置信度 motif，而非全部功能启动子 | 若标注有偏，则全基因组注释的召回率被高估 | 用独立实验验证的启动子集合（如 RegulonDB）做全基因组 recall 评估 | Results 节：训练数据描述 |
| ChIP-seq 验证仅针对 E. coli 且样本量小（σ32 仅 13 个） | 验证集太小，无法估计真实精度；naive baseline 56% 说明 ChIP-seq 重叠标准本身宽松 | 70% 验证率可能不具统计显著性 | 扩大验证集，计算 95% CI；与 naive baseline 做统计检验 | Results 图 3B |
| 与 SAPPHIRE/ProPr 对比仅用 ChIP-seq 重叠率 | 未比较其他指标（如 motif 保守性、表达预测相关性）；未报告这些工具在相同数据上的运行时间或易用性 | 无法判断整体优劣 | 在多个物种、多个 σ 因子上做系统 benchmark | Results 图 3B |
| 表达预测仅与简单 CNN 对比 | 未与 PromoterCalculator 等专用工具做直接对比（仅提及"on par or higher"但未给出数值） | 无法确认"state-of-the-art"声明 | 在同一测试集上直接对比 PromoterCalculator、SAPPHIRE 等 | Results 图 5B |
| UMAP 聚类分析为定性观察 | 未量化聚类纯度或与 σ 因子注释的互信息；浅层按 GC 聚类可能只是序列组成的统计效应 | "编码进化关系"的 claim 缺乏定量支持 | 计算聚类纯度、Silhouette score；与随机嵌入对比 | Results 图 4 |
| 预训练数据中 Pseudomonas 占比高 | 模型可能对 Pseudomonas 过拟合，其他属的启动子识别精度可能更低 | 跨物种泛化声明需要分物种评估 | 按属分层报告注释精度 | Results 图 1C |
| 未提供消融实验 | 无法判断双卷积、rotary attention、预训练策略各组件对最终性能的贡献 | 架构选择的合理性未经验证 | 对 backbone 各组件做消融 | 全文未提及消融 |
| 未与其他预训练 DNA 模型（如 Nucleotide Transformer）对比 | 无法判断 1.8M 参数的小模型是否优于通用大模型 | 模型规模与任务特化之间的权衡未知 | 在同一下游任务上对比 Nucleotide Transformer 等 | 全文未提及此类对比 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **无监督预训练规避标注瓶颈（可直接迁移）**
   - 概念：用未标注的基因组上游序列做掩码预测，让模型自行发现调控 motif，不依赖实验标注。
   - 迁移到 TF–DNA 互作：真核 TF 结合位点的实验标注同样稀缺，可对目标物种/类群的启动子或开放染色质区域做掩码预训练，再在下游任务微调。

2. **跨物种训练利用进化保守性（可直接迁移）**
   - 概念：同一进化支内 TF 结合机制保守，跨物种训练既扩大数据量又保留核心机制。
   - 迁移到 TF–DNA 互作：对同一 TF 家族在不同物种中的结合位点做联合建模，可提升低资源物种的预测能力。

3. **分割头设计适配全基因组注释（可直接迁移）**
   - 概念：用逐位置多分类（而非序列级二分类）实现全基因组扫描，输出"无特征 / motif 类型"标注。
   - 迁移到 TF–DNA 互作：可对全基因组做逐位置 TF 结合位点注释，输出"无结合 / 结合 motif 类型"。

4. **嵌入空间分析作为模型诊断工具（可直接迁移）**
   - 概念：用 UMAP 等可视化嵌入，检查模型是否按生物学类别（如 σ 因子）而非技术因素（如物种 GC 含量）聚类。
   - 迁移到 TF–DNA 互作：检查 TF 嵌入是否按家族/结构域聚类，可诊断模型是否学到功能相关的表示。

5. **分层特征组织（浅层→深层）的观察（需验证）**
   - 概念：浅层嵌入按序列组成（GC 含量）组织，深层嵌入按功能类别（σ 因子）组织。
   - 迁移到 TF–DNA 互作：可检验真核 TF 模型中是否也存在类似的分层组织，指导选择哪层嵌入做下游任务。

6. **保守的标注策略保证精度但牺牲召回（设计权衡）**
   - 概念：只标注"明显可识别的 motif"以保精度，代价是漏检弱启动子。
   - 迁移到 TF–DNA 互作：在构建训练集时，可先用高置信度 motif 保证精度，再用半监督或主动学习扩展覆盖。

7. **表达预测作为嵌入质量的定量验证（可直接迁移）**
   - 概念：用嵌入预测转录/翻译水平，作为"嵌入是否编码功能信息"的定量指标。
   - 迁移到 TF–DNA 互作：可用 TF 嵌入预测下游基因表达变化，验证嵌入是否捕获了 TF 的调控效应。

---

## 15 与已有知识连接

- **Avsec et al. (2021) Enformer**：本文引用的通用基因组 Transformer 代表，证明注意力机制可建模长程调控相互作用。PromoterAtlas 的 rotary attention 可视为对 Enformer 架构的轻量化替代，适合细菌基因组（基因间距短，200 nt 窗口足够）。
- **Benegas et al. (2025) / Brixi et al. (2025) / Dalla-Torre et al. (2024) Evo 2 / Nucleotide Transformer**：大规模基因组基础模型。PromoterAtlas 的定位是"小而专"——1.8M 参数 vs 这些模型的数十亿参数，但聚焦单一细菌纲，训练数据更集中。
- **Cho et al. (2014) E. coli σ factor ChIP-seq**：本文验证注释工具的核心外部数据。该数据集也是其他启动子预测工具（如 SAPPHIRE）的常用 benchmark。
- **SAPPHIRE (2024) 和 ProPr (2024)**：现有细菌启动子预测工具，本文直接对比对象。SAPPHIRE 为混合架构（CNN + LSTM），ProPr 为概率模型，本文的 Transformer + 分割头框架在 σ 因子覆盖范围上更广。
- **LaFleur et al. (2022), Hossain et al. (2020), Urtecho et al. (2019), Yu et al. (2021)**：大规模启动子活性测量数据集，本文用于表达预测任务的训练/评估。这些数据集也是合成启动子设计领域的常用 benchmark。
- **Kosuri et al. (2013)**：组合启动子文库的经典工作，本文用于蛋白表达预测验证。该数据集的"启动子+RBS 组合"设计对合成生物学有直接参考价值。
- **RoPE（Rotary Position Embedding）**：本文 attention 层采用的位置编码方法，由 Su et al. (2024) 提出。相比绝对位置编码，RoPE 更适合建模 motif 间相对距离——这对启动子中 −10/−35 box 间距约束的建模尤为重要。
- **候选方向（未在本文验证）**：本文方法可迁移到真核 TF–DNA 互作，但需注意：(1) 真核启动子更复杂（增强子、绝缘子等远距离元件），200 nt 窗口可能不足；(2) 真核 TF 结合位点更分散、更依赖染色质状态，需整合表观基因组特征。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：跨物种预训练的真核 TF–DNA 结合位点注释模型
- **来源局限/观察**：PromoterAtlas 的成功依赖 Gammaproteobacteria 内 σ 因子启动子结构的进化保守性。真核 TF 结合位点同样存在家族内的保守性（如 bZIP、C2H2 锌指），但缺乏跨物种的系统性预训练。
- **核心假设**：在多个真核物种的启动子/开放染色质区域上做掩码预训练，可学到 TF 结合位点的保守表示，提升低资源物种的 TF 结合位点预测。
- **初步方法**：收集 ENCODE、modENCODE 等多物种的 ATAC-seq/启动子区域，构建 500-1000 nt 窗口数据集，用 PromoterAtlas 的 DNATransformer 架构预训练，再用 ChIP-seq 数据微调分割头。
- **验证方式**：在未见过的物种上测试注释精度；与单物种训练的基线对比。
- **创新状态**：unverified

### 候选 2：σ 因子嵌入空间的定量分析
- **来源局限/观察**：PromoterAtlas 的 UMAP 分析显示深层嵌入按 σ 因子聚类，但仅为定性观察，未量化。
- **核心假设**：嵌入空间中的几何距离与 σ 因子的进化距离或结合位点相似性相关。
- **初步方法**：计算各 σ 因子嵌入簇的 Silhouette score、簇间距离；与 σ 因子蛋白序列的系统发育距离做相关分析。
- **验证方式**：Mantel test 检验嵌入距离与进化距离的相关性。
- **创新状态**：unverified

### 候选 3：基于嵌入的启动子强度预测与设计
- **来源局限/观察**：PromoterAtlas 嵌入可预测表达水平（r = 0.79），但仅用简单回归头。
- **核心假设**：嵌入空间中的方向性移动对应启动子强度的系统性变化，可用于启动子设计。
- **初步方法**：在嵌入空间中插值/移动，生成变异启动子序列，用表达预测头筛选高表达候选。
- **验证方式**：合成生物学实验验证 top 候选启动子的表达强度。
- **创新状态**：unverified

### 候选 4：结合物理模拟的 σ 因子–启动子结合机制解析
- **来源局限/观察**：PromoterAtlas 识别了 σ 因子结合位点，但未解释结合的分子机制（如 −10/−35 box 的间距如何影响 σ 因子识别）。
- **核心假设**：将 PromoterAtlas 的序列嵌入与分子动力学（MD）模拟结合，可揭示 σ 因子识别不同启动子 motif 的结构基础。
- **初步方法**：选取 PromoterAtlas 高置信度预测的各类 σ 因子启动子，用 AlphaFold3 预测 σ 因子-DNA 复合物结构，再用 MD 模拟验证结合稳定性。
- **验证方式**：MD 模拟的结合自由能与 PromoterAtlas 的预测置信度是否相关。
- **创新状态**：unverified

### 候选 5：合成启动子文库的主动学习设计
- **来源局限/观察**：PromoterAtlas 采用保守标注策略（仅高置信度 motif），可能漏检弱启动子。
- **核心假设**：用主动学习迭代选择"模型不确定但可能功能"的序列进行实验验证，可扩展训练集覆盖并提升弱启动子识别。
- **初步方法**：用 PromoterAtlas 嵌入 + 不确定性采样，从大规模基因组序列中挑选候选启动子，实验验证后加入训练集。
- **验证方式**：多轮主动学习后，模型在弱启动子上的召回率是否提升。
- **创新状态**：unverified