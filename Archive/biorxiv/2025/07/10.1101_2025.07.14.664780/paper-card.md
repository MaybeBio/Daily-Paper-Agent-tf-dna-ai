## 01 基本信息

- **标题**：Harnessing DNA Foundation Models for Cross-Species Transcription Factor Binding Site Prediction in Plant Genomes
- **作者**：Maryam Haghani; Krishna Vamsi Dhulipalla; Song Li
- **单位**：未提供（根据作者信息推测为美国高校，具体单位未在摘要中列出）
- **期刊/平台**：bioRxiv（预印本）；脚注说明修订版已被 *Proceedings of Machine Learning Research*（PMLR）接收
- **年份**：2025（预印本发布日期 2025-07-18）
- **论文类型**：方法评估/基准测试（benchmarking）研究
- **领域**：植物基因组学 × 深度学习（DNA foundation models）
- **关键词**：TFBS prediction, DNA foundation models, DNABERT-2, AgroNT, HyenaDNA, DAP-seq, cross-species generalization, Arabidopsis thaliana, Sisymbrium irio
- **DOI/arXiv**：10.1101/2025.07.14.664780
- **代码**：https://github.com/Maryam-Haghani/TFBS
- **数据**：https://zenodo.org/records/17229680（DOI: 10.5281/zenodo.17229680）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「TF–DNA 结合机制 × AI 方法」方向中的**跨物种泛化能力评估**子方向。它不提出新的结合机制假设，而是系统比较三种预训练 DNA foundation models（DNABERT-2、AgroNT、HyenaDNA）在植物 TFBS 预测任务上相对于专用模型（DeepBind、BERT-TFBS）和 motif 方法（MEME/FIMO）的性能与效率，并验证跨物种迁移的可行性。对 TF–DNA 互作课题的贡献在于：提供了 foundation model 在植物 TFBS 预测中的系统基准，并揭示了参数高效微调（仅更新 <0.6% 参数）即可达到接近全量微调性能的关键发现。

---

## 02 一句话总结

本文在拟南芥（*Arabidopsis thaliana*）和播娘蒿（*Sisymbrium irio*）的 AREB/ABF 家族 DAP-seq 数据上，通过三种评测协议（跨染色体、跨数据集、跨物种）系统比较了三种 DNA foundation models（DNABERT-2、AgroNT、HyenaDNA）与专用基线（DeepBind、BERT-TFBS、MEME/FIMO）的 TFBS 预测性能，发现 HyenaDNA 在保持接近最优精度的同时训练速度快 100 倍以上，且仅微调 <0.6% 参数即可达到接近全量微调的性能。

---

## 03 研究问题

- **具体问题**：预训练的 DNA foundation models 能否在植物 TFBS 预测任务上超越专用深度学习方法（DeepBind、BERT-TFBS）和 motif 方法（MEME/FIMO），并且能否实现跨物种泛化？
- **为什么重要**：实验方法（ChIP-seq、DAP-seq）劳动密集、成本高、物种特异，缺乏可扩展性。若 foundation models 能跨物种准确预测 TFBS，则可填补缺乏实验数据的物种的调控注释空白，对理解植物基因调控网络和抗逆育种有直接价值。
- **现有方法不足**：① 传统 motif 方法（MEME/FIMO）仅捕捉线性 motif 特征，无法学习复杂序列依赖；② 专用深度学习模型（DeepBind、BERT-TFBS）在单一物种上训练，跨物种泛化能力未经验证；③ 尚无研究系统比较多种 foundation models 在植物 TFBS 预测上的表现。
- **精确的 "Can ... ?" 问题**：Can pretrained DNA foundation models (DNABERT-2, AgroNT, HyenaDNA) achieve superior or comparable TFBS prediction accuracy relative to specialized baselines (DeepBind, BERT-TFBS, MEME/FIMO) on plant DAP-seq data, while generalizing across species and maintaining computational efficiency?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与参考文献构建，标注为「经外部核验」的部分仅指本文引用的文献信息，脉络组织为本文框架。

**阶段一：实验方法（ChIP-seq / DAP-seq）**
- 代表性方法：ChIP-seq [1]、DAP-seq [2]
- 优点：直接测量 TF–DNA 结合，提供体内/体外结合位点
- 局限：劳动密集、成本高、物种特异、难以扩展到全基因组规模

**阶段二：传统计算预测（motif 方法）**
- 代表性方法：MEME [8]（motif discovery）、FIMO [9]（motif scanning）
- 优点：可解释性强，基于 PWM 模型
- 局限：仅捕捉线性 motif 特征，无法学习序列上下文依赖和非线性互作

**阶段三：专用深度学习模型**
- 代表性方法：DeepBind [10]（CNN）、BERT-TFBS [11]（DNABERT-2 + CNN + CBAM）
- 优点：自动学习序列特征，无需人工设计特征
- 局限：通常在单一物种/单一 TF 上训练，跨物种泛化能力有限；需要大量标注数据

**阶段四：DNA foundation models（本文位置）**
- 代表性方法：DNABERT-2 [4]（BERT 架构，135 物种预训练）、AgroNT [5]（RoBERTa 架构，48 植物物种预训练）、HyenaDNA [6]（Hyena 算子，单核苷酸分辨率，长序列建模）
- 优点：大规模预训练捕获跨物种序列模式，可微调适应下游任务
- 本文主张的位置：首次系统评估多种 foundation models 在植物 TFBS 预测上的性能与跨物种泛化能力，并揭示 HyenaDNA 在精度-效率平衡上的优势

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 实验方法不可扩展 | ChIP-seq/DAP-seq 劳动密集、成本高、物种特异 | 实验流程复杂，需要物种特异抗体/条件 | Introduction 第 1 段 |
| 传统 motif 方法性能有限 | MEME/FIMO 在跨物种任务中 MCC 显著低于深度模型（0.720 vs. 0.426 跨物种方向） | PWM 仅捕捉线性 motif，无法学习复杂序列依赖 | Results 3.3 节 |
| 专用深度模型泛化不足 | DeepBind 在跨数据集任务中精度低于 foundation models | 在单一数据集上训练，缺乏跨物种预训练知识 | Results 3.2 节、图 2(a) |
| foundation models 计算成本高 | AgroNT 训练需 >38,000s，推理最长 977s | 模型参数量大（1B），全量微调代价高 | Results 3.3 节、表 S8 |
| 缺乏系统基准 | 此前无研究比较多种 foundation models 在植物 TFBS 上的表现 | 植物领域 foundation model 应用滞后于动物/人类 | Introduction 第 2 段 |

---

## 06 核心思想

**1) 表面方法**：
- 将三种预训练 DNA foundation models（DNABERT-2、AgroNT、HyenaDNA）作为特征提取器，在其顶部附加一个两层分类头（2 个神经元），在 DAP-seq 正/负样本上全量微调。
- 与三种基线比较：motif 方法（MEME+FIMO）、DeepBind（CNN）、BERT-TFBS（DNABERT-2 + CNN + CBAM）。
- 在三种评测协议下评估：跨染色体（leave-one-chromosome-out）、跨数据集（Malley2016→Sun2022）、跨物种（*A. thaliana* ↔ *S. irio*）。

**2) 核心洞察**：
- **HyenaDNA 的精度-效率最优平衡**：HyenaDNA 在三种协议下均达到接近最优精度（与 AgroNT 无显著差异），但训练速度快 ~130 倍、推理快 ~50 倍。其单核苷酸分辨率 tokenization 和 Hyena 算子（隐式长程卷积）使其在长序列（265bp）上比基于 k-mer 的模型更高效。
- **参数高效微调的有效性**：仅更新 embedding 层和分类头（<0.6% 参数）即可达到接近全量微调的性能，说明 foundation model 的预训练表示已捕获足够的序列特征，下游任务只需轻量适配。
- **跨物种泛化的机制基础**：AREB/ABF 的 DNA 结合偏好在不同 Brassicaceae 物种间高度保守（引用 Sun et al. 2022 的 PWM 比较和 swap-DAP 实验），这为跨物种迁移提供了生物学基础。

**3) 可能的普适教训** [Analysis]：
- 对于 TF–DNA 互作预测任务，**预训练表示的质量比模型架构的复杂度更重要**——轻量分类头 + 冻结 backbone 即可达到高精度，提示该领域应更多关注预训练策略而非任务特定架构设计。
- **跨物种泛化能力与 TF 结合位点的进化保守性直接相关**——当目标 TF 的 DNA 结合域在物种间保守时，跨物种迁移效果显著；这提示在扩展其他 TF 家族时，应优先选择结合域保守的 TF。
- **评测协议的设计决定了结论的适用范围**——三种协议（跨染色体、跨数据集、跨物种）分别测试了不同层面的泛化能力，这种多维度评测框架值得在 TF–DNA 互作预测研究中推广。

---

## 07 方法总览

- **输入**：DNA 序列（正样本为 DAP-seq 峰序列，负样本为随机打乱的 dinucleotide-preserving 序列），长度标准化至 201bp（跨数据集）或 265bp（跨染色体/跨物种）
- **输出**：二分类概率（TFBS vs. non-TFBS）
- **模型架构**：
  - Foundation models：DNABERT-2（12 层 BERT，768 维）、AgroNT（40 层 RoBERTa，1500 维，1B 参数）、HyenaDNA（Hyena 算子，单核苷酸 token）
  - 分类头：2 神经元全连接层，接在最终 token 表示的均值池化后
- **训练**：二分类交叉熵损失，AdamW 优化器，early stopping（10 epochs 无验证集改进即停止），保留最低验证损失的 checkpoint
- **基线**：MEME（motif discovery，5 个 de novo motifs）+ FIMO（motif scanning）；DeepBind（4 层 CNN）；BERT-TFBS（DNABERT-2 + CNN + CBAM）
- **评测协议**：
  1. 跨染色体：leave-one-chromosome-out，5 折，25 次运行（5 染色体 × 5 seeds）
  2. 跨数据集：Malley2016 训练 → Sun2022 测试（去重后 14,294 样本）
  3. 跨物种：*A. thaliana* 训练 → *S. irio* 测试，反之亦然（24,932 总样本）
- **指标**：Accuracy (ACC)、F1、Matthews Correlation Coefficient (MCC)、ROC-AUC、PR-AUC
- **统计检验**：ANOVA + Tukey's HSD（显著性水平 0.05）
- **反馈回路**：无显式反馈回路（非主动学习或迭代优化框架）
- **流程**：数据预处理（长度标准化、负样本生成）→ 模型微调 → 三种协议评测 → 统计比较 → 消融研究（HyenaDNA 参数冻结策略）

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 预训练 foundation model backbone | 提取 DNA 序列的上下文表示 | 捕获跨物种的序列模式，提供比随机初始化更好的特征 | 输入：DNA 序列；输出：token 级 embedding | Results 3.1-3.3：foundation models 整体优于 DeepBind 和 motif 基线 | 预期影响：移除后模型退化为随机初始化网络，性能大幅下降（[Analysis] 基于迁移学习常识，非本文实测） |
| 分类头（2 神经元全连接层） | 将序列表示映射为二分类概率 | 将预训练表示适配到 TFBS 分类任务 | 输入：均值池化后的序列 embedding；输出：TFBS/non-TFBS 概率 | Results 3.4：仅更新此头（<0.1% 参数）即可达到接近全量微调性能 | 预期影响：移除后模型无法输出分类结果 |
| 均值池化层 | 将变长 token 序列压缩为固定维度向量 | 适配分类头需要固定维度输入 | 输入：token embeddings；输出：768/1500 维向量 | Methods 2.2 节描述 | 预期影响：替换为其他池化策略（如 CLS token）可能影响性能（[Analysis] 未在本文测试） |
| 负样本生成（dinucleotide-preserving shuffling） | 生成平衡的负样本集 | 维持类别平衡，控制序列组成偏差 | 输入：正样本序列；输出：等量负样本 | Methods 2.1 节 | 预期影响：移除后类别不平衡导致模型偏向多数类（[Analysis] 基于分类常识） |
| 长度标准化（padding/trimming） | 统一序列长度至 201/265bp | 适配模型输入要求 | 输入：变长序列；输出：固定长度序列 | Methods 2.1 节 | 预期影响：过短 padding 可能引入噪声，过长 trimming 可能丢失边界信息（[Analysis] 未在本文测试） |
| HyenaDNA 参数冻结策略（Backbone.layers） | 仅更新 embedding + 分类头 | 降低计算和内存开销 | 输入：冻结 backbone 的模型；输出：微调后的模型 | Results 3.4、表 2a-2c：性能与全量微调几乎一致 | 实测影响：全量微调（None）与 Backbone.layers 性能几乎一致，但计算成本更高 |

---

## 09 关键公式符号

本文为实证基准测试研究，未提出新的数学模型或公式。核心方法为标准的二分类交叉熵损失和 AdamW 优化，无需要特殊符号化的公式。评测指标为标准定义：

- **Accuracy (ACC)** = (TP + TN) / (TP + TN + FP + FN)
- **F1 score** = 2 × Precision × Recall / (Precision + Recall)
- **MCC** = (TP×TN − FP×FN) / √[(TP+FP)(TP+FN)(TN+FP)(TN+FN)]
- **ROC-AUC / PR-AUC**：基于阈值扫描的曲线下面积

> 注：以上公式为通用定义，本文未显式列出公式，但指标名称与标准定义一致。

---

## 10 实验设计与证据链

**数据集与规模**：
- *A. thaliana* AREB/ABF1-4 DAP-seq 峰：14,374 个正样本（Sun2022）
- *S. irio* AREB/ABF1-4 DAP-seq 峰：10,558 个正样本（Sun2022）
- *A. thaliana* AREB/ABF2 DAP-seq 峰（Malley2016）：用于跨数据集训练
- 负样本：dinucleotide-preserving shuffling 生成，数量与正样本等量
- 序列长度：标准化至 201bp（跨数据集）或 265bp（跨染色体/跨物种）

**指标**：ACC、F1、MCC、ROC-AUC、PR-AUC

**基线**：MEME+FIMO（motif）、DeepBind（CNN）、BERT-TFBS（DNABERT-2+CNN+CBAM）

**评测协议**：跨染色体（5 折）、跨数据集（Malley2016→Sun2022）、跨物种（双向）

**统计检验**：ANOVA + Tukey's HSD（α=0.05）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-------------------|------|
| 跨染色体评测 | foundation models 能否在未见染色体上泛化 | 6 模型 × 5 折 × 5 seeds | 未提供具体数值（摘要仅提及整体趋势） | foundation models 整体优于 motif 基线 | 无法判断具体模型间差异 | Results 3.1、表 1、图 S1 |
| 跨数据集评测 | 模型能否跨实验批次泛化 | Malley2016 训练 → Sun2022 测试 | 神经模型间无显著差异（ACC/F1/MCC），但均优于 motif 基线；motif 的 ROC-AUC/PR-AUC 显著更低 | foundation models 和专用深度模型均能跨数据集泛化；motif 方法泛化能力有限 | 无法判断 foundation models 是否优于 DeepBind | Results 3.2、图 2(a)、表 S7 |
| 跨物种评测 | 模型能否跨物种泛化 | *A. thaliana* ↔ *S. irio* 双向 | 深度模型均良好泛化；motif 基线 MCC 仅 0.426（*A. thaliana*→*S. irio*）；AgroNet 精度略高但训练 >38,000s；HyenaDNA 训练 ~100× 快于 AgroNet | 深度模型跨物种泛化能力强；HyenaDNA 精度-效率最优 | 无法判断 HyenaDNA 是否在统计上显著优于其他深度模型（仅"comparable"） | Results 3.3、图 3、表 S8 |
| HyenaDNA 消融 | 参数冻结策略是否影响性能 | 全量微调 vs. 仅 embedding+分类头 vs. 仅分类头 | Backbone.layers 与全量微调性能几乎一致 | 参数高效微调有效，<0.6% 参数即可 | 无法判断更激进的冻结策略（仅分类头）在更大数据集上的表现 | Results 3.4、表 2a-2c、表 S9 |

---

## 11 结论正确解读

- **任务范围**：本文仅针对 AREB/ABF 转录因子家族在两种 Brassicaceae 物种上的 TFBS 预测，不涵盖其他 TF 家族或其他植物科属。
- **oracle/真值输入**：DAP-seq 峰被作为 ground truth 正样本，负样本由 dinucleotide-preserving shuffling 生成——这意味着模型学到的是"与真实峰序列不同的序列"而非"不结合的序列"，负样本质量依赖打乱策略的有效性。
- **端到端状态**：模型为端到端训练（序列 → 分类），但依赖预训练 foundation model 的表示质量。
- **算力成本**：HyenaDNA 训练 ~302s/213s（跨物种），AgroNet >38,000s，差异 >100 倍。但未报告推理时的 GPU 型号和 batch size 等细节。
- **历史数据依赖**：模型依赖 DAP-seq 实验数据，实验条件（如组织、处理）可能影响峰的定义和模型泛化。
- **模型依赖**：结论基于三种特定 foundation models（DNABERT-2、AgroNet、HyenaDNA），不代表所有 foundation models 均表现相同。
- **最难情形**：跨物种从 *S. irio* 训练 → *A. thaliana* 测试时，motif 基线 MCC 仅 0.426，说明小规模训练数据下 motif 方法严重退化；深度模型在此情形下仍保持良好性能。
- **群体/领域边界**：结论限于 Brassicaceae 科内、ABF 家族 TF；扩展到远缘物种或其他 TF 家族需进一步验证。
- **不确定性**：未报告置信区间或方差分析之外的效应量；跨物种结果可能受物种间序列相似性影响，而非模型本身的泛化能力。

**有边界的复述**：在 AREB/ABF 家族 DAP-seq 数据上，预训练 DNA foundation models（尤其是 HyenaDNA）在跨染色体、跨数据集和跨物种三种评测协议下均达到与专用深度模型相当或更优的预测精度，同时训练效率提升 1-2 个数量级；且仅微调 <0.6% 参数即可保持接近全量微调的性能。该结论适用于 Brassicaceae 科内、结合位点高度保守的 TF 家族。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 数据覆盖有限 | 仅 AREB/ABF 家族、两种 Brassicaceae 物种 | 扩展到更多 TF 家族和物种；利用即将到来的 multi-DAP-seq 数据 | Conclusion 第 2 段 |
| 缺乏 TF 特异性信息 | 当前模型未编码 TF 身份，无法区分不同 TF 的结合偏好 | 开发 TF-aware 模型，实现跨 TF 知识迁移 | Conclusion 第 2 段 |
| 未整合可解释性方法 | 未使用解释工具分析模型关注的序列特征 | 整合解释方法，支持从模式物种到未表征物种的调控知识迁移 | Conclusion 第 2 段 |
| 下游应用未验证 | 模型尚未用于推断未实验物种的 TFBS | 开发可推断未执行 DAP-seq 实验物种峰值的模型 | Conclusion 第 2 段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 负样本生成方式可能过于简单 | dinucleotide-preserving shuffling 仅保持二核苷酸组成，可能无法模拟真实的非结合序列（如染色质可及性差异、GC 含量偏差） | 若负样本与真实非结合序列差异过大，模型精度可能被高估 | 使用基因组随机区域或 DNase-seq 可及性区域作为负样本，比较模型性能变化 | Methods 2.1 节 |
| 跨物种泛化可能由序列相似性驱动而非语义理解 | *A. thaliana* 和 *S. irio* 同属 Brassicaceae，基因组序列相似性高；模型可能仅学习保守 motif 而非深层调控逻辑 | 若泛化仅来自序列相似性，则扩展到远缘物种时性能可能急剧下降 | 在更远缘物种（如单子叶植物）上测试，或分析模型关注的序列特征是否与已知 motif 一致 | Results 3.3 节 |
| "comparable" 的统计含义不明确 | 摘要和结果中使用 "comparable" 描述 HyenaDNA 与 AgroNet 的精度差异，但未报告效应量和置信区间 | 无法判断 HyenaDNA 是否在统计上显著劣于 AgroNet（尽管效率优势明显） | 检查补充材料中的完整统计检验结果（Tukey's HSD 分组字母） | Results 3.3 节 |
| 消融研究仅针对 HyenaDNA | 未对其他 foundation models 进行参数冻结消融，无法判断该结论是否可推广 | 若参数高效微调仅对 HyenaDNA 有效，则其普适性存疑 | 对 DNABERT-2 和 AgroNet 进行相同的冻结策略消融 | Results 3.4 节 |
| 未报告模型在不同 TF 上的分项性能 | AREB/ABF1-4 可能具有不同的结合偏好和 motif 复杂度，聚合指标可能掩盖个别 TF 上的失败 | 若模型在某个 TF 上表现差，聚合指标会掩盖该问题 | 按 TF 分别报告性能指标，检查是否存在显著差异 | Results 3.1-3.3 节 |
| 效率比较未标准化硬件条件 | 训练时间比较未报告 GPU 型号、batch size、序列长度等细节 | 不同硬件条件下的时间比较可能不公平 | 在相同硬件和超参数下重新运行所有模型，报告标准化时间 | Results 3.1-3.3 节 |

---

## 14 学到什么

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题的可迁移知识。

**Agent 提炼的知识候选**：

1. **预训练表示的可迁移性**：DNA foundation models 在跨物种 TFBS 预测中表现优异，说明预训练阶段捕获的序列模式具有跨物种普适性。可迁移到 TF–DNA 互作机制研究：使用 foundation model 的 embedding 作为特征，分析 TF 结合位点的序列决定因素，而非仅依赖 PWM motif。

2. **参数高效微调策略**：仅更新 <0.6% 参数（embedding + 分类头）即可达到接近全量微调性能。可迁移到物理模拟/结构预测任务：在 MD 模拟或 docking 评分函数中，使用预训练表示 + 轻量适配层，避免大规模重训练。

3. **多维度评测协议设计**：跨染色体（基因组位置泛化）、跨数据集（实验批次泛化）、跨物种（进化泛化）三种协议分别测试不同层面的泛化能力。可迁移到 TF–DNA 结合预测模型评估：不应仅在同分布测试集上评估，应设计多层次的泛化测试。

4. **dinucleotide-preserving shuffling 作为负样本生成策略**：保持二核苷酸组成的同时破坏 motif 结构，比完全随机打乱更严格。可迁移到 TF–DNA 结合数据增强：在训练数据有限时，用此策略生成更真实的负样本。

5. **结合位点保守性与跨物种迁移的关系**：AREB/ABF 结合位点在 Brassicaceae 内高度保守，是跨物种迁移成功的生物学基础。可迁移到 TF–DNA 互作机制研究：在评估跨物种预测前，先分析目标 TF 的 DNA 结合域序列保守性，作为可行性的先验判断。

6. **效率-精度权衡的系统评估**：HyenaDNA 的单核苷酸分辨率 tokenization 在长序列上比 k-mer 方法更高效。可迁移到 TF–DNA 结合机制建模：对于长调控区域（增强子、启动子），选择支持长序列的模型架构（如 Hyena、Mamba）而非标准 Transformer。

7. **轻量分类头的设计**：在 foundation model 顶部仅加 2 神经元分类头即可完成二分类任务。可迁移到 TF–DNA 结合强度预测：将分类头替换为回归头，即可预测结合亲和力，无需设计复杂任务特定架构。

---

## 15 与已有知识连接

- **DNABERT-2 [4]**：基于 BERT 架构的 DNA foundation model，在 135 个物种基因组上预训练。本文将其作为 backbone 之一，验证了其在植物 TFBS 预测中的有效性。与课题关联：DNABERT-2 的 embedding 可用于分析 TF 结合位点的序列上下文特征。

- **AgroNT [5]**：基于 RoBERTa 架构的植物基因组 foundation model，48 个植物物种预训练，1B 参数。本文发现其精度最高但计算成本极大。与课题关联：植物特异的预训练模型可能捕获更多植物调控特征，但需权衡计算成本。

- **HyenaDNA [6]**：基于 Hyena 算子的 decoder-only 模型，支持单核苷酸分辨率长序列建模。本文发现其在精度-效率平衡上最优。与课题关联：Hyena 算子的隐式长程卷积可能更适合捕获 TF 结合的远端调控元件。

- **DeepBind [10]**：CNN 架构的 DNA/RNA 结合位点预测器，是深度学习方法在 TFBS 预测中的经典工作。本文将其作为专用基线。与课题关联：CNN 方法在短序列上有效，但缺乏长程依赖建模能力。

- **BERT-TFBS [11]**：结合 DNABERT-2 + CNN + CBAM 的混合架构，专门用于 TFBS 预测。本文将其作为强基线。与课题关联：CBAM 注意力机制可迁移到 TF–DNA 结合机制分析，用于识别关键序列位置。

- **MEME [8] / FIMO [9]**：motif discovery 和 scanning 的经典工具。本文将其作为传统基线。与课题关联：PWM 模型的可解释性仍是深度学习方法的重要对照，可用于验证深度学习模型学到的 motif 是否与已知 motif 一致。

- **Sun et al. 2022 [7]**：提供了 AREB/ABF 家族在四种 Brassicaceae 物种的 DAP-seq 数据，并证明结合位点跨物种保守。本文的数据基础。与课题关联：该数据集可用于 TF–DNA 结合机制的比较基因组学分析。

- **Alley et al. (Plant Cistrome Database) [2]**：DAP-seq 技术的开发与数据积累。与课题关联：DAP-seq 是植物 TF–DNA 互作研究的重要实验手段，本文验证了计算模型可补充实验覆盖不足。

- **迁移方向**：本文的评测框架（跨染色体/跨数据集/跨物种）可迁移到 TF–DNA 结合机制研究中的模型评估；参数高效微调策略可迁移到基于结构预测（如 AlphaFold）的 TF–DNA 复合物建模；dinucleotide-preserving shuffling 可迁移到结合数据增强。

---

## 16 研究想法

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题的研究候选。

**Agent 生成的研究候选**：

1. **TF-aware 跨物种 TFBS 预测模型**
   - 来源局限/观察：本文模型未编码 TF 身份，无法区分不同 TF 的结合偏好；作者在结论中明确提到开发 TF-aware 模型是未来方向。
   - 核心假设：将 TF 的 DNA 结合域序列或 embedding 作为条件输入，可提升模型在未见 TF 上的泛化能力。
   - 初步方法：在 foundation model 顶部引入 cross-attention 机制，将 TF 蛋白序列的 embedding 与 DNA 序列 embedding 进行交互；训练时使用多 TF 的 DAP-seq 数据。
   - 验证方式：在 held-out TF 上测试零样本或少样本泛化能力，与本文的 TF-agnostic 模型比较。
   - 创新状态：unverified

2. **结合位点保守性引导的跨物种迁移学习**
   - 来源局限/观察：本文跨物种成功可能依赖 AREB/ABF 结合位点的高保守性；对结合位点分歧大的 TF 家族，迁移效果未知。
   - 核心假设：利用系统发育距离或结合位点保守性度量作为迁移学习的权重，可提升远缘物种间的预测性能。
   - 初步方法：计算目标物种与源物种的 TF 结合位点 PWM 相似度，作为迁移学习的样本权重或正则化项；在多个 TF 家族上验证。
   - 验证方式：比较保守性加权迁移与朴素迁移在远缘物种上的性能差异。
   - 创新状态：unverified

3. **Foundation model embedding 与物理模拟的混合评分函数**
   - 来源局限/观察：本文 foundation model 在序列层面预测 TFBS 精度高，但未涉及三维结构；TF–DNA 结合机制研究需要结构层面的理解。
   - 核心假设：将 foundation model 的序列 embedding 与 MD 模拟或 docking 的结构特征（如结合自由能、接触面积）融合，可提升 TF–DNA 结合亲和力预测精度。
   - 初步方法：对已知 TF–DNA 复合物结构，提取 foundation model 的序列 embedding 和 MD 模拟的结构特征，训练多模态回归模型预测结合亲和力。
   - 验证方式：在公开的 TF–DNA 结合亲和力数据集（如 SELEX、PBMs）上比较混合模型与单一模态模型的性能。
   - 创新状态：unverified

4. **参数高效微调在 TF–DNA 结构预测中的应用**
   - 来源局限/观察：本文发现仅微调 <0.6% 参数即可达到接近全量微调性能，提示预训练表示的高质量。
   - 核心假设：在 TF–DNA 复合物结构预测任务中，冻结预训练模型 backbone、仅微调轻量适配层，可达到与全量微调相当的性能，同时大幅降低计算成本。
   - 初步方法：在 AlphaFold 或 RoseTTAFold 的 TF–DNA 复合物预测中，冻结大部分参数，仅微调少数适配层（如 LoRA），比较与全量微调的性能差异。
   - 验证方式：在 TF–DNA 复合物结构预测基准（如 PDB 中的 TF–DNA 复合物）上比较不同微调策略。
   - 创新状态：unverified

5. **长序列建模在增强子-启动子互作预测中的应用**
   - 来源局限/观察：HyenaDNA 支持长序列（1M tokens）建模，本文仅用于短序列（265bp）TFBS 预测，未发挥其长序列优势。
   - 核心假设：使用 HyenaDNA 对增强子-启动子区域的长序列进行建模，可捕获远端调控元件对 TF 结合的影响，提升 TFBS 预测精度。
   - 初步方法：将增强子-启动子区域（~10kb）作为输入，使用 HyenaDNA 提取特征，预测中间区域的 TF 结合位点。
   - 验证方式：在植物增强子-启动子互作数据集上比较长序列模型与短序列模型的 TFBS 预测性能。
   - 创新状态：unverified

6. **可解释性分析：foundation model 关注的序列特征与已知 TF motif 的对比**
   - 来源局限/观察：本文未使用解释方法分析模型决策依据，无法判断模型是否学到生物学上合理的特征。
   - 核心假设：foundation model 在 TFBS 预测中关注的序列位置与已知 TF motif 显著重叠，且能发现新的 motif 变体。
   - 初步方法：使用 attention 可视化或 SHAP 值分析模型关注的序列位置，与已知 AREB/ABF motif 比对；对模型发现的新 motif 进行实验验证。
   - 验证方式：计算模型关注区域与已知 motif 位置的重叠率；对新颖 motif 进行 EMSA 或 DAP-seq 验证。
   - 创新状态：unverified