## 01 基本信息

- **标题**：An apicomplexan-specific foundation model improves prediction of regulatory genomic signals in Plasmodium falciparum
- **作者**：Brown AS; Yang J; Llinás M; Mahony S
- **单位**：未提供（作者隶属机构未在摘要中列出）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（方法学 + 实证研究）
- **领域**：基因组学 / 调控基因组学 / 深度学习 / 疟原虫表观基因组学
- **关键词**：foundation model, self-supervised pretraining, Plasmodium falciparum, transcription factor binding, chromatin accessibility, histone modifications, chromatin states, GPN, fine-tuning
- **DOI/arXiv 号**：10.64898/2026.11.12.766050
- **代码**：未提供（TPCAV 代码在 GitHub: https://github.com/seqcode/TPCAV，但本文模型代码未明确提供）
- **数据**：455 个顶复门（apicomplexan）基因组组装（NCBI）；ChIP-seq、ATAC-seq 数据来源见 Methods 节
- **阅读日期**：2026-11-16（预印本发布日期）
- **在课题方向中的位置**：本文直接聚焦 TF–DNA 结合机制，在数据稀缺的小基因组（P. falciparum，23 Mbp，80.6% A/T）中，通过自监督预训练（masked nucleotide reconstruction）获得序列表征，再微调（fine-tune）预测 TF 结合位点、染色质可及性、组蛋白修饰和染色质状态。属于「蛋白质-DNA 互作 × 深度学习」方向，核心贡献是验证了**系统发育相关的预训练数据**（而非通用大模型）在低数据调控预测任务中的价值，并系统比较了不同微调策略（LPFT、全冻结、低学习率、无冻结）对 TF 结合预测的影响。

---

## 02 一句话总结

在数据稀缺的 P. falciparum 基因组中，用 455 个顶复门基因组组装进行 masked-nucleotide 自监督预训练的 GPN 模型，经 LPFT 微调后，在预测 TF 结合位点、染色质可及性、组蛋白修饰和染色质状态等调控信号上优于无预训练模型和人类基因组预训练的 DNABERT，且收益集中在少于 3,000 个训练样本的低数据场景。

---

## 03 研究问题

- **具体问题**：在数据稀缺的小基因组（P. falciparum）中，自监督预训练（foundation model）是否能为下游调控基因组学预测任务带来实际收益？收益在什么条件下最大？
- **为什么重要**：现有 foundation model 的争论集中在数据丰富的人类基因组上，任务特定模型（task-specific models）常可匹敌或超越预训练模型。但小基因组（如寄生虫）缺乏大规模标注数据，预训练可能是唯一可行的路径。P. falciparum 是疟疾病原体，其基因调控机制与致病性密切相关，且其基因组具有极端 A/T 偏倚（80.6%），对跨物种迁移构成独特挑战。
- **现有方法不足**：
  - 人类基因组预训练模型（如 DNABERT）在 A/T 极端偏倚的顶复门基因组上迁移差（图 2A，DNABERT 中位正确碱基概率 ~0.37，接近 shuffled 对照）。
  - 任务特定模型在小样本下无法学到足够的调控语法（regulatory grammar）。
  - 已有 foundation model 研究多聚焦于大基因组，未系统评估小基因组 + 低标注数据场景。
- **精确的「Can ... ?」问题**：Can self-supervised pretraining on phylogenetically relevant (apicomplexan) genomes improve downstream prediction of regulatory genomic signals in P. falciparum, and does the benefit depend on labeled data availability and fine-tuning strategy?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 与 Discussion 的引用，属于「经外部核验」的领域发展框架（引用文献均为已发表工作）。

1. **早期 CNN 调控预测（2015–2018）**：DeepSEA（J. Zhou & Troyanskaya, 2015）、Basenji（Kelley et al., 2018）证明短 DNA 窗口足以预测染色质特征和非编码变异效应。局限：需要大量标注数据，跨物种泛化差。
2. **长程模型（2021–2026）**：Enformer（Avsec et al., 2021, 2026）引入长序列建模，提升复杂长程调控任务性能。局限：训练数据需求更大，主要面向人类/哺乳动物。
3. **基因组 foundation models（2023–2026）**：DNABERT-2（Z. Zhou et al., 2024）、Evo 2（Brixi et al., 2026）、GPN（Benegas et al., 2023）等通过自监督预训练学习序列表征。GPN 最初在植物基因组上验证。争议：在数据丰富场景下，预训练收益不明确（Z. Tang et al., 2025；Feng et al., 2025；Mupparapu et al., 2025；You et al., 2025）。
4. **小基因组 / 寄生虫调控预测**：已有工作（如 Karollus et al., 2024）尝试在小型真核基因组上使用 foundation model，但缺乏系统评估。
5. **本文位置**：首次在顶复门（apicomplexan）范围内训练**类群特异（clade-specific）** foundation model，系统比较预训练 vs. 无预训练、不同微调策略，并明确给出收益边界（<3,000 训练样本）。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 标注数据稀缺 | P. falciparum 的 TF ChIP-seq 数据集小（n = 198 至 10,310 峰） | 寄生虫难以体外培养、ChIP 实验通量低 | Results 图 6A；Methods Datasets 节 |
| 跨物种迁移差 | 人类预训练 DNABERT 在 P. falciparum 上重建性能接近 shuffled 对照 | 极端 A/T 偏倚（80.6%）与人类基因组差异大；调控语法不同 | Results 图 2A |
| 预训练收益不确定 | 数据丰富时预训练收益趋近于零 | 任务特定模型可从足够标注中自行学到特征 | Results 图 6A；Discussion 节 |
| 微调策略敏感 | 标准端到端微调（None Frozen）在低数据下反而有害 | 大梯度更新覆盖（overwrite）预训练表征（feature distortion, Kumar et al., 2022） | Results 图 5；Discussion 节 |
| 重复序列干扰 | 高可重建区域含 poly-T 等低复杂度基序 | 重复序列本身具有高可预测性，非调控信号 | Results 图 4（RM#2 poly-T motif） |
| 长程调控信息缺失 | GPN 感受野有限，无法建模远距离调控 | 架构限制（25 层 CNN，kernel size 9） | Discussion 节（作者提及架构局限） |

---

## 06 核心思想

### 1) 表面方法
- 用 455 个顶复门基因组组装（含 P. falciparum 近缘种）训练 GPN，任务为 masked nucleotide reconstruction（随机遮蔽 ~15% 碱基，预测被遮蔽碱基）。
- 将预训练模型的核心（25 层 dilated CNN）作为特征提取器，替换输出层为分类头，用 ChIP-seq / ATAC-seq 峰标注微调，预测二分类（结合/不结合）。
- 系统比较 4 种微调策略：无冻结（None Frozen）、LPFT（先冻结后解冻）、全冻结（Full Frozen）、低核心学习率（Lower Core Learning Rate）。
- 用 TPCAV（concept attribution）检验模型内部是否编码已知 TF 基序概念。

### 2) 核心洞察
- **系统发育相关性 > 模型规模**：在顶复门内预训练（即使数据量远小于人类基因组）比在人类基因组上预训练（DNABERT）迁移效果好得多。预训练数据的**类群匹配**比模型大小更重要。
- **预训练收益是条件性的**：收益集中在 <3,000 训练样本的低数据场景；数据充足时收益消失。这调和了「预训练有用」与「任务特定模型可匹敌」两种对立观点。
- **微调策略决定收益是否兑现**：在低数据下，标准端到端微调（None Frozen）会破坏预训练表征（feature distortion），LPFT 是安全默认。
- **浅层即足够**：截断到前 8 层 CNN 即可获得大部分预训练收益，说明 TF 结合预测本质上是局部基序识别问题。

### 3) 可能的普适教训 [Analysis]
- 对 TF–DNA 结合预测而言，**基序是局部特征**，因此浅层网络足够；深层网络学到的长程特征对结合预测贡献有限，甚至可能过拟合。
- 预训练的价值在于**提供先验的序列语法**（包括编码约束、重复结构、基序共现），而非直接提供基序位置。这解释了为何预训练在低数据下帮助大、在高数据下帮助小。
- 对数据稀缺的非模式生物（如寄生虫、病原体），**类群特异预训练**应成为默认策略，而非直接使用人类/通用模型。

---

## 07 方法总览

- **输入**：DNA 序列（512 bp 窗口，one-hot 编码 A/C/G/T/N）
- **输出**：
  - 预训练阶段：每个遮蔽位置的碱基概率分布（4 类）
  - 微调阶段：序列级二分类 logit（结合/不结合）
- **模块**：
  1. GPN 核心：25 层 dilated CNN（kernel size 9，dilation 倍增），残差连接 + LayerNorm
  2. 预训练头：线性投影到 4 类碱基词汇表
  3. 分类头：全局平均池化 → dropout(0.1) → 线性(512→512) → GELU → dropout(0.1) → 线性(512→2)
- **训练**：
  - 预训练：AdamW，lr=1e-4，weight decay=0.01，cosine schedule，1000 warmup steps，batch size 512，fp16 混合精度
  - 微调：分类头 lr=1e-5，核心（若解冻）lr=1e-6，20,000 步
- **数据划分**：P. falciparum 3D7 的 chr13 为验证集，chr14 为测试集（最大染色体）；训练时排除与 chr13/14 同源的序列（通过 Minimap2 比对生成 blacklist）
- **工具**：PyTorch 2.5.1，HuggingFace wrappers，Minimap2 (v2.28)，SAMtools (v1.21)，bedtools (v2.31.1)，deepTools (v3.5.1)，XSTREME (MEME Suite v5.5.1)，STAMP (v2.0)，TPCAV (v0.10.3)
- **流程**：
  1. 收集 455 个顶复门组装，构建 blacklist 排除与 chr13/14 同源序列
  2. 预训练 GPN（masked nucleotide reconstruction），评估重建性能
  3. 对每个下游任务（TF 结合、ATAC、组蛋白修饰、染色质状态），构建正负样本集
  4. 用 4 种微调策略训练分类器，在 chr14 上评估 AUPRC
  5. 用 TPCAV 检验模型内部是否编码已知 TF 基序概念
  6. 与 DNABERT（人类预训练）和 MalariaSED-like 模型比较

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Masked nucleotide reconstruction 预训练 | 学习顶复门基因组序列的统计规律（编码约束、重复结构、基序共现） | 在无标注数据上注入序列先验 | 输入：512 bp 序列（~15% 碱基遮蔽）；输出：遮蔽位点碱基概率 | Results 图 2A：预训练模型重建性能显著优于 shuffled 对照 | 预期：低数据任务性能下降（图 6A 中 <3,000 样本场景收益最大） |
| 25 层 dilated CNN 核心 | 提取多尺度序列特征 | 捕获局部基序和中等范围序列上下文 | 输入：512 bp one-hot；输出：512 维特征图 | Results 图 7：截断到 8 层即达大部分性能 | 预期：移除深层对 TF 结合预测影响小（[Analysis] 因基序是局部特征） |
| 分类头（池化 + MLP） | 将序列级特征映射为二分类 logit | 将预训练表征适配到具体调控任务 | 输入：512 维池化向量；输出：2 类 logit | Results 图 5-6 | 预期：无分类头则无法做下游预测 |
| LPFT 微调策略 | 先冻结核心训练分类头，再以低学习率解冻核心 | 避免早期大梯度覆盖预训练表征 | 输入：预训练核心 + 随机分类头；输出：训练好的分类器 | Results 图 5：LPFT 在低数据下最优 | 预期：换成 None Frozen 在低数据下性能下降（图 5，AUPRC 0.12 vs 0.23） |
| Blacklist 构建（Minimap2 比对） | 排除与测试染色体同源的训练序列 | 防止数据泄漏，保证测试集评估公正 | 输入：训练组装 + chr13/14；输出：blacklist BED | Methods 节 | 预期：移除后测试性能虚高（[Analysis] 同源序列泄漏） |
| TPCAV concept attribution | 检验模型内部是否编码已知 TF 基序概念 | 提供机制性证据，说明预训练学到了调控特征 | 输入：模型中间层激活 + 概念/非概念序列；输出：F-score | Results 图 4；Supplemental 图 4：预训练模型 F-score 0.94 vs shuffled 0.78 | 预期：移除后无法验证模型是否真正编码基序概念 |

---

## 09 关键公式符号

本文为深度学习方法学论文，核心公式为 masked reconstruction 的交叉熵损失和分类任务的交叉熵损失，作者未给出显式数学公式。以下为基于方法描述的标准公式化表达（[Analysis] 标注）：

**1. Masked reconstruction 损失**（预训练阶段）：
\[
\mathcal{L}_{\text{recon}} = -\frac{1}{|\mathcal{M}|} \sum_{i \in \mathcal{M}} \log p(x_i | x_{\backslash \mathcal{M}})
\]
- \( \mathcal{M} \)：被遮蔽的碱基位置集合（~15% 的 512 bp 窗口）
- \( x_i \)：位置 \( i \) 的真实碱基
- \( p(x_i | x_{\backslash \mathcal{M}}) \)：模型在给定未遮蔽序列条件下对位置 \( i \) 的预测概率

**2. 分类损失**（微调阶段）：
\[
\mathcal{L}_{\text{cls}} = -\frac{1}{N} \sum_{j=1}^{N} \left[ y_j \log \hat{y}_j + (1 - y_j) \log(1 - \hat{y}_j) \right]
\]
- \( y_j \in \{0, 1\} \)：第 \( j \) 个序列窗口的标签（结合/不结合）
- \( \hat{y}_j \)：模型预测的结合概率

**3. AUPRC**（评估指标）：
\[
\text{AUPRC} = \int_0^1 \text{Precision}(\text{Recall}) \, d(\text{Recall})
\]
- Precision = TP / (TP + FP)，Recall = TP / (TP + FN)
- 对类别不平衡数据比 AUROC 更敏感

**4. 微调策略中的学习率调度**（LPFT）：
\[
\text{lr}_{\text{core}} = \begin{cases} 0 & \text{前 50\% 训练步} \\ 1 \times 10^{-6} & \text{后 50\% 训练步} \end{cases}
\]
\[
\text{lr}_{\text{head}} = 1 \times 10^{-5} \quad \text{全程}
\]

---

## 10 实验设计与证据链

### 数据集与设置
- **预训练数据**：455 个顶复门基因组组装（NCBI），涵盖 Plasmodium、Toxoplasma、Cryptosporidium、Babesia、Theileria 等属
- **测试物种**：P. falciparum 3D7（chr14 为测试集，chr13 为验证集）
- **下游任务**：
  - 14 个 ApiAP2 TF 的 ChIP-seq 结合位点预测（n = 198 至 10,310 训练峰）
  - 4 个 ATAC-seq 时间点（10/20/30/40 hpi）染色质可及性预测（n = 470 至 1,596）
  - 4 个组蛋白修饰 ChIP-seq（H3K18me1, H3K4me1, H3K4me3, H3K9ac；n = 2,003 至 3,730）
  - 10 个染色质状态（Brown et al., 2026 的 11 态模型，排除 quiescent 态；n = 2,720 至 14,357）
- **指标**：AUPRC（测试集 chr14）
- **基线**：无预训练（随机初始化）、DNABERT（人类基因组预训练）、MalariaSED-like 模型（无预训练 CNN-LSTM）
- **微调策略**：None Frozen、LPFT、Full Frozen、Lower Core LR
- **随机种子**：3 个（11, 22, 33），报告均值

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| 预训练模型重建性能 | 顶复门预训练能学到序列规律 | 4 个 GPN 模型 vs shuffled 对照 vs DNABERT | 全基因组预训练模型正确碱基概率中位数最高；DNABERT 接近 shuffled 对照（~0.37） | 类群匹配的预训练数据比通用预训练更有效 | 不能说明预训练学到了调控功能（仅统计规律） | Results 图 2A |
| 区域分层重建 | 重建性能在功能区域有差异 | 按基因组注释分层（外显子、内含子、UTR、TSS、基因间区） | 内含子重建最可靠（25-32% 高置信正确碱基）；TSS 和 UTR 区域提升有限 | 预训练捕获了剪接/编码约束，但调控区域结构更复杂 | 不能说明高重建 = 调控重要性 | Results 图 2B |
| TF 结合位点重建 | 重建置信度在 TF 结合位点升高 | PfAP2-G2 结合位点（含 motif）vs 随机区域 | 结合位点重建置信度显著高于随机区域 | 预训练模型隐式编码了 TF 结合位点的序列特征 | 不能说明模型能直接预测结合（需微调验证） | Results 图 3 |
| 微调策略比较（PfAP2-I, n=198） | LPFT 在低数据下最优 | 4 种微调策略 vs 无预训练 | LPFT AUPRC=0.23；None Frozen=0.12（低于无预训练 0.18）；Full Frozen=0.19；Lower LR=0.20 | 低数据下标准微调破坏预训练表征；LPFT 是安全默认 | 单一数据集，不能推广到所有低数据任务 | Results 图 5 |
| 微调策略比较（PfHP1, n=2,931） | 中等数据下策略差异缩小 | 同上 | 所有预训练策略 AUPRC 0.65-0.67，无预训练 0.45 | 预训练收益在中等数据下仍显著 | 策略间差异不显著 | Results 图 5 |
| 14 个 TF 全面板 | 预训练收益与数据量负相关 | 预训练 LPFT vs 无预训练，按 n 分层 | 中位 AUPRC 提升 0.09；<3,000 样本提升 0.11；>3,000 样本提升 ≈0 | 预训练收益集中在低数据场景 | 不能说明预训练在数据丰富时有害（仅无益） | Results 图 6A |
| ATAC-seq 预测 | 预训练提升染色质可及性预测 | 4 个时间点，预训练 vs 无预训练 | 中位 AUPRC 提升 0.13（0.09-0.19） | 预训练对开放染色质预测有稳定收益 | 时间点间差异未做显著性检验 | Results 图 6B |
| 组蛋白修饰预测 | 预训练对组蛋白修饰预测收益较小 | 4 个修饰，预训练 vs 无预训练 | 中位 AUPRC 提升 0.03（0.004-0.053） | 组蛋白修饰预测受限于数据量而非序列特征 | H3K18me1 几乎不可预测（AUPRC≈0.1） | Results 图 6C |
| 染色质状态预测 | 预训练提升特定状态预测 | 10 个状态，预训练 vs 无预训练 | 中位 AUPRC 提升 0.04；状态 7（HP1）提升 0.15 | 预训练对异染色质相关状态收益最大 | 状态间差异未做多重检验校正 | Results 图 6D |
| 截断实验 | 浅层即足够 | 2/4/8/16/25 层，6 个 TF | 8 层达峰值性能；更深层无显著提升 | TF 结合预测是局部问题，浅层特征足够 | 其他任务（如长程调控）可能不同 | Results 图 7 |
| TPCAV 概念归因 | 预训练模型编码 TF 基序概念 | 45 个已知 TF 基序 vs 非基序序列 | 预训练模型 F-score 0.94 vs shuffled 0.78 | 预训练内部表征确实编码了 TF 基序特征 | 概念归因是间接证据，不等同于因果 | Results 图 4；Supplemental 图 4 |
| 与 MalariaSED-like 比较 | 预训练优于任务特定架构 | 16 个因子，预训练 GPN vs MalariaSED-like | 预训练 GPN 在 10/16 因子上显著更优，4 个相当 | 预训练表征优于从头训练的任务特定模型 | 未比较计算成本 | Supplemental 图 5 |

---

## 11 结论正确解读

- **任务范围**：本文评估的是**局部序列特征**（512 bp 窗口）对调控信号预测的贡献。结论不适用于需要长程（>10 kb）调控信息的任务。
- **Oracle/真值输入**：ChIP-seq 峰和 ATAC-seq 峰作为监督标签，存在实验噪声和抗体特异性偏差；峰定义（MACS2 q < 0.001）影响正负样本划分。
- **端到端状态**：预训练 + 微调是端到端可训练的，但预训练阶段仅使用序列（无任何功能注释），微调阶段使用峰标注。TPCAV 分析是事后解释，不参与训练。
- **算力成本**：预训练 200 万步（2M steps），具体 GPU 时数未报告；微调 20,000 步。截断实验表明实际部署可用 8 层模型降低成本。
- **历史数据依赖**：预训练数据来自 NCBI 现有组装（截至 2026 年），组装质量参差；P. falciparum 3D7 参考基因组为单一菌株。
- **模型依赖**：结论基于 GPN（CNN）架构，不必然推广到 Transformer 架构（如 Evo 2、DNABERT-2）。作者明确讨论 GPN 的归纳偏置（局部感受野）可能恰好适合 TF 结合预测。
- **最难情形**：H3K18me1（着丝粒富集、与基因表达弱相关）几乎不可预测（AUPRC≈0.1），说明某些组蛋白修饰的基因组分布不由局部序列决定。
- **群体/领域边界**：结论限于顶复门（apicomplexan），跨门迁移（如到动质体、真菌）未验证。作者在 Discussion 中推测类群特异预训练可能泛化到其他数据稀缺分支，但无直接证据。
- **有边界的复述**：在顶复门基因组范围内，用 455 个组装预训练的 GNN 模型，在 <3,000 标注样本的调控预测任务上，经 LPFT 微调可稳定提升 AUPRC（中位 +0.09~0.11）；数据充足时收益消失；人类预训练模型（DNABERT）在此场景下无收益。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 单一测试物种 | 所有下游任务仅在 P. falciparum 上评估 | 扩展到 Toxoplasma、Cryptosporidium 等其他顶复门物种 | Discussion 节 |
| 架构局限 | GPN 感受野有限，无法建模长程调控 | 使用更 expressive 的模型核心或更宽感受野 | Discussion 节 |
| 数据量代理指标粗糙 | 用 ChIP-seq 峰数量作为数据量代理，未考虑峰质量差异 | 更精细的数据量度量 | Discussion 节 |
| 预训练数据偏差 | 455 个组装中 Plasmodium 占比可能过高，影响跨属迁移 | 平衡各属数据量 | Discussion 节 |
| 未验证跨门迁移 | 结论可能不适用于顶复门以外的基因组 | 在其他数据稀缺分支（如动质体）测试 | Discussion 节 |
| H3K18me1 预测失败 | 该修饰几乎不可从局部序列预测 | 需整合其他特征（如三维基因组） | Results 图 6C；Discussion 节 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 预训练收益与数据量负相关，但未做因果验证 | 可能是任务难度差异而非数据量驱动（如 PfAP2-G2 和 PfAP2-G5 峰多但基序简单） | 若收益由任务难度驱动，则「<3,000 样本」的阈值不可迁移 | 控制任务难度（如合成数据集）后改变样本量 | Results 图 6A |
| DNABERT 比较可能不公平 | DNABERT 未在顶复门数据上微调重建；且 DNABERT 的 tokenizer（3-mer）在 A/T 富集区效率低 | 若比较不公平，则「类群特异 > 通用」结论被夸大 | 在顶复门数据上继续预训练 DNABERT 再比较 | Results 图 2A |
| 截断实验仅报告 6 个 TF | 样本量小，且未报告方差 | 无法判断 8 层 vs 25 层差异是否显著 | 扩展到全部 14 个 TF，报告置信区间 | Results 图 7 |
| TPCAV 概念归因的 F-score 0.94 可能虚高 | 概念序列含 12 个 motif 插入，远高于自然密度；线性分类器可能利用插入伪影 | 若归因虚高，则「模型编码 TF 基序」的证据被夸大 | 使用自然序列中的 motif 实例（非人工插入）重做 | Supplemental 图 4 |
| 未报告预训练计算成本 | 200 万步训练的具体 GPU 时数缺失 | 若预训练成本过高，实际部署价值存疑 | 报告 FLOPs 或 GPU 时数 | Methods 节 |
| 微调策略比较仅在 2 个数据集上 | PfAP2-I（n=198）和 PfHP1（n=2,931）不能代表所有低数据场景 | 策略推荐（LPFT）可能过拟合到这两个数据集 | 在更多低数据任务上验证 | Results 图 5 |
| 未讨论峰定义对结果的影响 | MACS2 q < 0.001 的峰集可能包含大量间接结合事件 | 若峰集噪声大，预训练收益可能被低估 | 用不同 q 阈值或 IDR 峰集重做 | Methods Datasets 节 |
| 预训练数据包含 P. falciparum 自身组装 | 测试物种（P. falciparum）的序列可能已出现在预训练数据中 | 若存在泄漏，预训练收益被高估 | 排除 P. falciparum 后重新预训练 | Methods 节（blacklist 仅排除 chr13/14 同源，未排除整个物种） |

---

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题。

1. **类群特异预训练是低数据调控预测的默认策略**：当目标物种缺乏大规模 ChIP-seq 标注时，用同纲/同门物种的基因组序列做 masked reconstruction 预训练，比使用人类/通用模型更有效。迁移到本课题：对非模式生物的 TF–DNA 结合预测，应优先收集系统发育近缘物种的基因组序列做预训练，而非依赖人类基因组预训练模型。

2. **LPFT 是低数据微调的安全默认**：标准端到端微调在 <3,000 样本时破坏预训练表征（feature distortion）。LPFT（先冻结核心训练分类头，再低学习率解冻）在低数据下最优。迁移到本课题：任何 TF–DNA 结合预测模型的微调，在样本不足时应采用 LPFT 而非全量微调。

3. **浅层特征对 TF 结合预测足够**：截断到前 8 层 CNN 即达峰值性能。TF 结合本质是局部基序识别问题，深层网络学到的长程特征对结合预测贡献有限。迁移到本课题：设计 TF–DNA 结合预测模型时，不必追求超深网络；应关注感受野与基序长度的匹配。

4. **重建置信度可作为无标注调控元件发现先验**：模型对 PfAP2-G2 结合位点周围序列的重建置信度显著高于随机区域，且不依赖 motif 中心。迁移到本课题：masked reconstruction 模型的重建置信度可作为候选 TF 结合区域的先验，用于引导 ChIP-seq 实验设计或作为无监督特征。

5. **重复序列是调控预测的混淆因素**：高可重建区域含 poly-T 等低复杂度基序，模型可能利用重复性而非调控功能。迁移到本课题：在 TF–DNA 结合预测中，应区分「序列可预测性」与「调控功能」，可用 shuffled 对照或重复序列掩码来解耦。

6. **预训练收益的边界条件**：收益集中在 <3,000 训练样本；数据充足时收益消失。迁移到本课题：评估预训练价值时，必须报告数据量-收益曲线，而非单一数据点；否则结论不可迁移。

7. **TPCAV 概念归因是验证模型编码 TF 基序的有效工具**：通过线性分类器在中间层激活上分离概念/非概念序列，可检验模型是否真正学到基序特征。迁移到本课题：对任何 TF–DNA 结合预测模型，可用 TPCAV 检验模型内部表征是否编码已知 TF 基序，作为机制性验证。

8. **系统发育距离是预训练迁移效果的关键变量**：DNABERT（人类预训练）在 P. falciparum 上几乎无迁移，而顶复门内预训练效果显著。迁移到本课题：预训练数据的选择应基于系统发育距离而非数据量；对 TF–DNA 结合预测，同门物种的 100 个基因组可能比跨门物种的 10,000 个基因组更有价值。

---

## 15 与已有知识连接

- **GPN 架构**：Benegas et al. (2023) 提出，最初在植物基因组上验证。本文将其扩展到顶复门，验证了架构的跨类群适用性。连接：GPN 的 dilated CNN 设计（kernel size 9，倍增 dilation）与 TF 基序的局部性匹配。
- **Feature distortion 现象**：Kumar et al. (2022) 在计算机视觉中提出，本文在基因组领域验证。连接：LPFT 策略的普适性。
- **Foundation model 争议**：Z. Tang et al. (2025)、Feng et al. (2025)、Mupparapu et al. (2025)、You et al. (2025) 在人类基因组上质疑预训练价值。本文提供小基因组视角的调和证据。
- **植物中的类群特异预训练**：Lv et al. (2026) 在 Poaceae/Brassicaceae 内验证家族级模型迁移更好；Zhai et al. (2026) 的 PlantCAD2 在被子植物上优于通用模型。本文与之一致，支持「系统发育匹配 > 模型规模」的普适规律。
- **P. falciparum 调控基因组学**：Brown et al. (2026) 的 11 态染色质模型、Shang et al. (2022) 的 ApiAP2 ChIP-seq、Campbell et al. (2010) 的 ApiAP2 PBM 基序数据库。本文直接使用这些资源作为下游任务和验证基准。
- **MalariaSED**：Wang et al. (2023) 的 CNN-LSTM 架构，本文作为无预训练基线。连接：任务特定架构 vs 预训练表征的对比。
- **TPCAV**：J. Yang & Mahony (2026) 的 concept attribution 框架，本文用于验证模型内部表征。连接：可迁移到其他 TF–DNA 结合模型的可解释性分析。
- **[Analysis] 候选方向**：本文的「重建置信度作为调控元件先验」思路，与无监督调控元件预测（如 gapped k-mer SVM、conservation-based 方法）可结合；「类群特异预训练」策略可推广到其他数据稀缺病原体（如锥虫、利什曼原虫）。

---

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题。

### 候选 1：类群特异预训练 + 物理模拟特征融合的 TF–DNA 结合预测
- **来源局限/观察**：本文证明序列预训练在低数据下有效，但未整合物理化学特征（如 DNA 形状、静电势）。TF–DNA 结合不仅由序列基序决定，还受 DNA 结构（minor groove width, propeller twist）影响。
- **核心假设**：将 masked reconstruction 预训练表征与 DNA 形状特征（DNAshape 或 MD 模拟导出的结构特征）融合，可在低数据下进一步提升 TF–DNA 结合预测精度。
- **初步方法**：在本文 GPN 预训练模型基础上，增加 DNA 形状特征通道（如 5-mer 形状编码），微调时同时优化序列和形状特征。比较融合 vs 纯序列 vs 纯形状。
- **验证方式**：在 P. falciparum 的 14 个 ApiAP2 TF 数据集上评估 AUPRC；与本文结果直接对比。
- **创新状态**：unverified

### 候选 2：重建置信度作为 TF 结合位点的无监督先验，引导 ChIP-seq 实验设计
- **来源局限/观察**：本文发现重建置信度在 PfAP2-G2 结合位点升高，但未系统评估其作为全基因组先验的精度。
- **核心假设**：masked reconstruction 模型的重建置信度可作为 TF 结合区域的排序先验，在无 ChIP-seq 数据的情况下优先选择候选区域进行实验验证。
- **初步方法**：计算全基因组重建置信度，与已知 TF 结合位点（如 PfAP2-G2、PfAP2-I）重叠率评估；与 motif 扫描（FIMO）比较；构建「重建置信度 + motif 共定位」的集成先验。
- **验证方式**：在 P. falciparum 的 ChIP-seq 数据集上评估 top-k 召回率；与随机、motif-only、conservation-only 基线比较。
- **创新状态**：unverified

### 候选 3：跨顶复门物种的 TF–DNA 结合模型迁移（zero-shot 与 few-shot）
- **来源局限/观察**：本文仅在下游任务中使用 P. falciparum 数据，未测试预训练模型对其他顶复门物种（如 Toxoplasma gondii、Cryptosporidium parvum）的迁移。
- **核心假设**：顶复门共享的调控语法（如 ApiAP2 基序的保守性）使预训练表征可跨物种迁移，few-shot 微调即可达到较好性能。
- **初步方法**：用本文预训练模型，在 Toxoplasma 或 Cryptosporidium 的 ChIP-seq 数据上做 zero-shot 和 few-shot 评估；比较与从头训练模型的差距。
- **验证方式**：跨物种 AUPRC 评估；分析迁移性能与系统发育距离的关系。
- **创新状态**：unverified

### 候选 4：TF–DNA 结合预测中的「序列可预测性」与「功能重要性」解耦
- **来源局限/观察**：本文发现高重建置信度区域含重复序列（poly-T），提示「可预测性」≠「调控功能」。但未系统解耦。
- **核心假设**：通过对比「重建置信度」与「功能重要性」（如 ChIP-seq 峰、eQTL、保守性），可区分序列的统计规律性与调控功能，从而改进调控元件预测。
- **初步方法**：对 P. falciparum 基因组计算重建置信度、保守性、ChIP-seq 峰重叠率；用三维散点图或条件概率分析三者关系；构建「高置信度 + 高保守性 + 非重复」的调控元件候选集。
- **验证方式**：候选集与已知调控元件的重叠率；与本文 motif discovery 结果比较。
- **创新状态**：unverified

### 候选 5：预训练表征 + MD 模拟的 TF–DNA 结合机制解析
- **来源局限/观察**：本文用 TPCAV 证明预训练模型编码 TF 基序概念，但未解析具体结合机制（如构象变化、水介导相互作用）。
- **核心假设**：预训练模型的高重建置信度区域对应 MD 模拟中 DNA 构象柔性较低（或结合自由能较高）的区域，即序列统计规律与物理结合机制存在对应。
- **初步方法**：选取 PfAP2-G2 结合位点，用 MD 模拟（如 GROMACS + parmbsc1 力场）计算 DNA 构象 ensemble；比较重建置信度与构象熵、minor groove width 的相关性。
- **验证方式**：Pearson/Spearman 相关性；与随机区域对照。
- **创新状态**：unverified

### 候选 6：小基因组 foundation model 的「最小数据需求」标定
- **来源局限/观察**：本文给出 <3,000 样本的收益边界，但未系统扫描不同预训练数据量、不同下游任务类型下的收益曲线。
- **核心假设**：存在一个「预训练数据量阈值」，超过后收益饱和；该阈值与基因组大小、A/T 含量、调控复杂度相关。
- **初步方法**：用不同数量的顶复门组装（50/100/200/455）预训练 GPN，在固定下游任务上评估 AUPRC；拟合收益-数据量曲线。
- **验证方式**：曲线拐点分析；与人类基因组（ENCODE 数据）的收益曲线对比。
- **创新状态**：unverified