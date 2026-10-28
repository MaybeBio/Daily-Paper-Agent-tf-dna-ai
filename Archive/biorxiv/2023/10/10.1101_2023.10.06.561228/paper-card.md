## 01 基本信息

- **标题**：Joint sequence & chromatin neural networks characterize the differential abilities of Forkhead transcription factors to engage inaccessible chromatin
- **作者**：Arora S; Yang J; Akiyama T; James DQ; Morrissey A; Blanda TR; Badjatia N; Lai WK; Ko MS; Pugh BF; Mahony S
- **单位**：未提供（根据致谢推测为 Penn State University 相关机构）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2023
- **论文类型**：预印本（研究论文）
- **领域**：计算生物学 / 转录因子-DNA 互作 / 染色质生物学 / 深度学习
- **关键词**：Forkhead 转录因子、pioneer factor、染色质可及性、卷积神经网络、特征归因、ChIP-exo
- **DOI/ID**：10.1101/2023.10.06.561228
- **代码**：https://github.com/seqcode/iFox-mES
- **数据**：GEO GSE244411
- **阅读日期**：未提供
- **在该方向中的位置**：本文聚焦于 TF–DNA 结合机制中「pioneer factor 能力差异」这一核心问题，采用 CNN 联合建模 DNA 序列与染色质特征，并通过特征归因技术解释模型预测。该方法为「TF–DNA 互作 × 深度学习」方向提供了可迁移的联合建模框架，尤其适用于比较同家族 TF 在染色质可及性差异下的结合行为。

## 02 一句话总结

本文通过在相同染色质背景下（小鼠胚胎干细胞）过表达五个 Forkhead 家族 TF，利用联合 DNA 序列与染色质特征的 CNN 模型，证明 Fox TF 之间的差异结合模式由「序列偏好差异」与「对不可及染色质的结合能力差异」共同决定，且不同 Fox 亚家族在 pioneer 能力上存在显著梯度。

## 03 研究问题

- **具体问题**：在相同染色质环境下，序列偏好相似的 Forkhead 家族 TF 为何会结合不同的基因组位点？其 pioneer 能力（结合不可及染色质的能力）是否存在系统性差异？
- **为什么重要**：Pioneer factor 是发育和重编程过程中的关键调控因子，但「pioneer 能力」常被当作二元属性（有/无），缺乏定量比较框架。理解同家族 TF 间 pioneer 能力的梯度对预测 TF 在特定细胞类型中的功能至关重要。
- **现有方法不足**：传统方法（如 motif 富集、ChIP-seq 峰重叠）难以分离序列偏好与染色质偏好的贡献；体外实验（如 cis-bp）无法反映染色质环境的影响；单一 TF 研究缺乏同家族比较的系统性。
- **精确研究问题**：Can a joint sequence + chromatin neural network model, combined with feature attribution, quantitatively decompose the relative contributions of intrinsic sequence preference and preexisting chromatin environment to the differential DNA-binding activities of paralogous Forkhead TFs?

## 04 背景与发展脉络

（注：以下脉络为「经外部核验」的领域发展概述，结合本文引用与领域常识）

1. **Pioneer factor 概念确立期**（~2010s）：FoxA 被鉴定为最早发现的 pioneer factor 之一，能在不开放染色质的情况下结合核小体 DNA（Cirillo et al., 2002）。关键发现：Forkhead 结构域与连接组蛋白 H1 结构相似，提示其能结合核小体。
2. **ChIP-exo 高分辨率时代**（~2014-2018）：Pugh 实验室开发 ChIP-exo，实现 TF 结合位点的单碱基分辨率定位，可区分直接结合与间接结合模式。
3. **深度学习应用于 TF 结合预测**（~2015-2020）：DeepBind、DeepSEA、BPNet 等模型证明 CNN 可从序列预测 TF 结合；但多数模型仅用序列，忽略染色质环境。
4. **序列+染色质联合建模**（~2018-2023）：少数工作开始整合 DNase/ATAC 信号与序列（如 Basenji、Enformer），但多用于预测而非解释 TF 间差异。
5. **本文位置**：首次将「序列+染色质」联合 CNN 应用于同家族 TF 的系统比较，并用特征归因技术将模型预测分解为序列贡献与染色质贡献，为「pioneer 能力」提供可量化的计算框架。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 同家族 TF 结合位点差异难以解释 | FoxA1、FoxC1、FoxG1、FoxL2、FoxP3 在相同细胞中结合不同位点 | 序列偏好差异 + 染色质偏好差异共同作用，但传统方法无法分离两者 | Results 图 2A-B；Discussion |
| Pioneer 能力缺乏定量比较 | 文献常将 TF 简单分为 pioneer/non-pioneer | 缺乏在相同染色质背景下系统比较多个 TF 的实验设计 | Introduction；Discussion |
| 序列 motif 相似但结合不同 | cis-bp 数据库显示五个 Fox TF 体外 motif 相似，但体内结合位点差异大 | 体外实验无法反映染色质环境的影响；体内结合受染色质状态调控 | Results 图 1A-D；Discussion |
| 序列-only 模型预测能力不足 | 仅用序列的 CNN 无法捕捉 Fox TF 的差异结合模式 | 序列信息不足以解释染色质依赖性结合 | Results 图 4B-C |
| 特征归因解释困难 | 深度学习模型预测准确但难以解释 | 需要将模型预测分解为序列与染色质各自的贡献 | Methods：CNN feature attribution；Results 图 5-6 |

## 06 核心思想

**1) 表面方法**：
- 在 mES 细胞中过表达五个 Fox TF（FoxA1, FoxC1, FoxG1, FoxL2, FoxP3），24h 后进行 ChIP-exo、ATAC-seq、RNA-seq
- 训练 CNN 模型，输入为 DNA 序列（one-hot）+ 预存染色质特征（ATAC-seq、组蛋白修饰、MNase-seq 等），预测 ChIP-exo 读数
- 使用 DeepLiftShap 进行特征归因，将预测分解为序列贡献与染色质贡献

**2) 核心洞察**：
- Fox TF 的差异结合由「序列偏好差异」与「染色质偏好差异」两个正交轴共同决定
- 不同 Fox TF 对预存染色质状态的「亲和力」存在梯度：FoxA1 > FoxC1/FoxL2 > FoxG1/FoxP3（从高到低 pioneer 能力）
- 序列-only 模型无法捕捉差异，说明染色质信息是解释 Fox TF 差异结合的必要条件
- 特征归因可在单碱基/单特征水平揭示「为什么这个位点被这个 TF 结合而不被另一个结合」

**3) 可能的普适教训** [Analysis]：
- 同家族 TF 的「pioneer 能力」不应被视为二元属性，而应视为连续谱系
- 联合建模 + 特征归因是解析「序列 vs 环境」贡献的通用框架，可迁移至其他 TF 家族（如 Sox、GATA 等）
- 在相同细胞背景中过表达多个同家族 TF 是比较 TF 内在特性的高效实验设计

## 07 方法总览

- **输入**：
  - DNA 序列：500bp 窗口，one-hot 编码，形状 (4, 500)
  - 染色质特征：10 种 mES 预存染色质信号（ATAC-seq、H3K4me1/2/3、H3K27ac、H3K9me3、H3K36me3、H3K79me2、H3K122ac、高/低浓度 MNase-seq），z-score 标准化，形状 (#tracks, 500)
  - 联合输入：拼接为 (4 + #tracks, 500) 数组
- **输出**：预测该区域 ChIP-exo 读数（log 变换）
- **模型架构**：VGG 启发的卷积塔
  - 第一层：1D 卷积，n 个滤波器，kernel size 25，stride 1
  - 中间层：4 层 1D 卷积塔，kernel size w，stride 2，滤波器数逐层增加
  - 降维层：1 个滤波器，kernel size 1，stride 1
  - 全连接层：k 层，每层 f 个输出特征
- **训练**：
  - 损失函数：MSE
  - 优化器：AdamW（lr, betas=[0.9, 0.999], weight_decay=0.01）
  - 学习率调度：ExponentialLR（gamma）
  - 超参数调优：Asynchronous HyperBand（Ray），每个 Fox TF 单独调优
  - 早停：validation loss 不改善即停止
- **特征归因**：DeepLiftShap（Captum 实现），DNA 背景为二核苷酸 shuffling（10 次），染色质背景为零数组
- **流程**：
  1. ChIP-exo 数据 → peak calling（ChExMix）→ 定义正样本
  2. 随机采样负样本（排除 peak 和 blacklist 区域）
  3. 训练序列-only 和序列+染色质两种 CNN
  4. 比较两种模型在预测和差异结合上的表现
  5. 对序列+染色质模型进行特征归因，分解序列与染色质贡献
  6. 结合 ATAC-seq 时间序列（0h vs 24h）评估各 TF 的染色质开放能力

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ChExMix peak calling | 从 ChIP-exo 数据中鉴定结合位点及结合模式 | 提供高分辨率结合位点定义，区分直接/间接结合 | 输入：ChIP-exo BAM；输出：peak 及 binding subtype | Methods：ChIP-exo data processing | 移除后无法定义正样本，模型无法训练 |
| 序列-only CNN | 仅用 DNA 序列预测 TF 结合 | 作为基线，评估序列信息的解释力 | 输入：(4, 500) one-hot；输出：ChIP-exo 读数 | Results 图 4B-C | 预期：无法捕捉 Fox TF 差异结合（已证实） |
| 序列+染色质 CNN | 联合序列与预存染色质特征预测结合 | 核心模型，捕捉染色质对 TF 结合的调控 | 输入：(4+#tracks, 500)；输出：ChIP-exo 读数 | Results 图 4B-C | 预期：显著提升预测能力，尤其对染色质依赖性 TF |
| DeepLiftShap 特征归因 | 将模型预测分解为序列与染色质贡献 | 解释模型「为什么」预测该位点被结合 | 输入：训练好的 CNN + 输入样本；输出：各特征的贡献分数 | Results 图 5-6；Methods：CNN feature attribution | 移除后无法区分序列 vs 染色质贡献，核心结论无法得出 |
| TF-MoDISco | 从序列归因中提取 motif | 将序列贡献转化为可解释的 motif 模式 | 输入：DeepLiftShap 序列分数；输出：motif 矩阵 | Results 图 S11 | 移除后序列层面的解释力下降 |
| 差异结合分析 + K-means 聚类 | 将结合位点按 TF 偏好分组 | 定义「TF 偏好簇」用于后续分析 | 输入：各 TF ChIP-exo 信号；输出：8 个结合簇 | Results 图 2B | 移除后无法定义「差异结合」的表型 |
| ATAC-seq 时间序列 | 评估 TF 结合后的染色质开放能力 | 区分「结合不可及染色质」与「开放染色质」两个能力 | 输入：0h/24h ATAC-seq；输出：可及性变化 | Results 图 7 | 移除后无法评估 pioneer 功能后果 |

## 09 关键公式符号

本文为深度学习应用型论文，无新推导的数学公式。核心概念性「公式」如下：

1. **联合输入表示**：
   \( X = [X_{seq}; X_{chrom}] \)
   其中 \( X_{seq} \in \mathbb{R}^{4 \times 500} \) 为 one-hot DNA 编码，\( X_{chrom} \in \mathbb{R}^{C \times 500} \) 为 C 种染色质特征的 z-score 标准化信号，\( [;] \) 表示通道维度拼接。

2. **预测目标**：
   \( \hat{y} = f_{CNN}(X) \)，\( y = \log(\text{ChIP-exo read count} + 1) \)

3. **损失函数**：
   \( \mathcal{L} = \frac{1}{N} \sum_{i=1}^{N} (\hat{y}_i - y_i)^2 \)（MSE）

4. **DeepLiftShap 归因**：
   \( \phi_i = \sum_{j} \frac{\partial f}{\partial x_i} \cdot (x_i - x_i^{ref}) \) 的 DeepLift 变体，其中 \( x_i^{ref} \) 为参考输入（DNA 为二核苷酸 shuffling，染色质为零向量）。

## 10 实验设计与证据链

**数据集与资源**：
- 细胞系：小鼠胚胎干细胞（mES），五个 Fox TF 诱导过表达系 + 对照
- ChIP-exo：每个 TF 2 个生物学重复，24h 时间点；FoxA1 另有 0h/48h 时间点
- ATAC-seq：0h（预存）和 24h（TF 表达后）
- RNA-seq：0h 和 24h，每个条件 2 个重复
- 外部数据：mES 组蛋白修饰 ChIP-seq、MNase-seq（来自已发表数据，Table S2/S3）
- 训练/验证/测试：染色体级别划分（chr11 验证，chr2/chr17 测试）

**指标**：
- 模型预测性能：Pearson 相关系数（预测 vs 实际 ChIP-exo 读数）
- 差异结合：edgeR（fold>1.5, q<0.05）
- 归因分析：序列贡献分数 vs 染色质贡献分数

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| ChIP-exo peak calling | Fox TF 在 mES 中结合不同位点 | 5 个 TF 两两比较 | 结合位点重叠率低，各 TF 有独特结合簇 | Fox TF 在相同染色质环境下结合不同位点 | 无法区分序列 vs 染色质贡献 | Results 图 1C-D, 2A-B |
| Motif 分析（ChExMix + MEME） | 序列偏好差异部分解释结合差异 | 各 TF 结合位点的 motif 比较 | FoxA1 偏好完整 TGTTTAC；其他 TF 偏好 TGTTT 变体 | 序列偏好存在差异 | motif 差异不足以完全解释结合差异 | Results 图 1C-D, 2B |
| 序列-only CNN | 序列信息能否预测 Fox TF 结合 | 5 个 TF 的序列-only 模型 | 预测性能中等，无法捕捉差异结合模式 | 序列信息部分预测结合 | 序列不足以解释差异 | Results 图 4B-C |
| 序列+染色质 CNN | 染色质信息是否提升预测 | 同 TF 的序列-only vs 序列+染色质 | 染色质特征显著提升预测，尤其对 FoxG1/FoxP3 | 染色质环境是 Fox TF 结合的重要决定因素 | 无法确定因果方向（预存 vs 诱导） | Results 图 4B-C |
| 特征归因（DeepLiftShap） | 序列 vs 染色质贡献可分解 | 各 TF 的归因分数比较 | FoxA1 序列贡献高；FoxG1/FoxP3 染色质贡献高 | Fox TF 在「序列依赖 vs 染色质依赖」轴上存在梯度 | 归因分数为相关性而非因果性 | Results 图 5 |
| 单点归因示例 | 归因可解释单点结合差异 | 3 个代表性位点 | 展示序列/染色质贡献如何决定 TF 特异性 | 归因可提供机制性解释 | 示例数量有限 | Results 图 6 |
| ATAC-seq 时间序列 | TF 结合后是否开放染色质 | 0h vs 24h ATAC 信号 | FoxA1 显著增加可及性；FoxG1/FoxP3 几乎无变化 | FoxA1 具有 pioneer 活性，FoxG1/FoxP3 缺乏 | 24h 时间点可能不足以捕捉慢速染色质重塑 | Results 图 7 |
| RNA-seq 差异表达 | TF 表达的功能后果 | 各 TF vs 对照 | 各 TF 驱动不同表达程序 | 差异结合转化为差异表达 | 未直接验证 pioneer 活性与表达变化的因果关系 | Results 图 8 |

## 11 结论正确解读

- **任务范围**：本文结论仅限于五个 Fox TF 在 mES 细胞中的过表达行为，不直接推广到内源表达水平或其他细胞类型。
- **oracle/真值输入**：ChIP-exo 信号作为结合活性的真值；ATAC-seq/组蛋白修饰为「预存」染色质状态（0h 数据），但部分染色质特征可能受 TF 表达影响（24h 数据用于验证）。
- **端到端状态**：CNN 模型为预测模型，非生成模型；特征归因提供解释但非因果验证。
- **算力成本**：未提供具体训练时间/资源消耗，仅提及使用 2 张 NVIDIA P100 GPU。
- **历史数据依赖**：模型依赖 mES 细胞的预存染色质状态，该状态本身是细胞类型特异的。
- **模型依赖**：CNN 架构和超参数为每个 TF 单独调优，可能引入 TF 间不可比性（作者未讨论此点）。
- **最难情况**：FoxL2 和 FoxC1 结合位点位于「静止」染色质，但缺乏已知 pioneer 机制解释；模型能预测但机制不明。
- **群体/领域边界**：结论限于 Forkhead 家族，不推广至所有 TF 家族。
- **不确定性**：ChIP-exo 信号受抗体效率、过表达水平影响；未提供 peak calling 的 FDR 阈值细节。

**有边界的复述**：在 mES 细胞中过表达五个 Forkhead 家族 TF 后，其基因组结合位点的差异由序列偏好差异和对预存染色质状态的亲和力差异共同决定；FoxA1 具有最强的不可及染色质结合能力，FoxG1/FoxP3 最弱，FoxC1/FoxL2 居中。联合序列+染色质 CNN 可捕捉这一差异，而序列-only 模型不能。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 过表达系统的人工性 | TF 在非内源水平表达，可能改变结合行为 | 未明确提及 | Discussion（隐含） |
| 单一时间点（24h） | 可能错过早期结合事件或晚期染色质重塑 | 未明确提及 | Methods：Choosing ChIP-exo time-point |
| 无法完全排除间接结合 | ChIP-exo 捕获的是交联后的 DNA-蛋白互作，可能包含间接结合 | 未明确提及 | Discussion（隐含） |
| 归因方法的相关性而非因果性 | DeepLiftShap 分数反映模型依赖，不直接证明生物学因果 | 未明确提及 | Methods：CNN feature attribution（隐含） |
| 仅五个 Fox TF | 结论不覆盖全部 Forkhead 家族 | 未明确提及 | Introduction（隐含） |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| 过表达水平未标准化 | 不同 TF 的蛋白表达量可能不同，导致结合位点数量差异被误解为内在偏好差异 | 核心结论（pioneer 能力梯度）可能受表达水平混淆 | 用 Western blot 或定量质谱验证各 TF 表达量；或使用表达量归一化的结合分析 | Methods：未提及表达量验证 |
| 「预存」染色质状态的定义 | 0h 染色质数据来自未表达 TF 的 mES 细胞，但过表达本身可能在 24h 内改变染色质 | 模型可能捕捉的是 TF 诱导的染色质变化而非「预存」状态 | 使用更早时间点（如 6h）的染色质数据，或使用不结合 DNA 的突变体作为对照 | Results 图 7 使用 24h ATAC 数据 |
| CNN 超参数逐 TF 调优 | 不同 TF 使用不同超参数，模型容量可能不同，导致比较不公平 | 「序列 vs 染色质贡献」的 TF 间比较可能反映模型差异而非生物学差异 | 使用固定超参数进行敏感性分析；或报告超参数搜索空间 | Methods：Table 2 |
| 归因方法的选择 | DeepLiftShap 仅为多种归因方法之一，不同方法可能给出不同结论 | 核心解释（序列 vs 染色质贡献）可能依赖归因方法 | 使用 Integrated Gradients、SHAP 等替代方法交叉验证 | Methods：仅使用 DeepLiftShap |
| 未报告负对照 | 未展示不相关 TF（如非 Forkhead 家族）的模型表现 | 无法排除模型只是捕捉了通用染色质可及性信号 | 训练一个非 Forkhead TF 的对照模型 | Results 中未提及 |
| 差异结合分析依赖聚类 | K=10 的选择主观（作者承认），不同 K 值可能改变簇的定义和后续结论 | 簇定义影响所有下游分析 | 进行 K 值敏感性分析 | Methods：K 值选择描述 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **联合建模框架**：将 DNA 序列（one-hot）与染色质特征（z-score 信号）在通道维度拼接后输入 CNN，是解析「序列 vs 环境」贡献的通用架构。可迁移至其他 TF 家族（如 Sox、GATA、bHLH）的差异结合分析。

2. **特征归因作为解释工具**：DeepLiftShap 可将 CNN 预测分解为序列贡献和染色质贡献，在单碱基/单特征水平解释「为什么这个位点被 TF A 结合而不被 TF B 结合」。此方法可推广至任何「序列+上下文」联合建模任务。

3. **同家族多 TF 比较实验设计**：在相同细胞背景中过表达多个同家族 TF，配合 ChIP-exo 高分辨率定位，是系统比较 TF 内在特性的高效策略。可迁移至其他 pioneer factor 候选家族。

4. **Pioneer 能力梯度概念**：pioneer 能力不是二元属性，而是连续谱系。这一概念框架可用于重新审视已有 pioneer factor 列表，并指导预测新 pioneer factor。

5. **序列-only 模型的局限**：当 TF 结合高度依赖染色质环境时，序列-only 模型无法捕捉差异结合。这提示在 TF 结合预测任务中，应优先考虑联合建模而非纯序列模型。

6. **ATAC-seq 时间序列作为功能验证**：通过比较 TF 结合前后的染色质可及性变化，可区分「结合不可及染色质」与「开放染色质」两个能力维度。此设计可迁移至其他候选 pioneer factor 的功能验证。

## 15 与已有知识连接

- **Cirillo et al. (2002)**：FoxA 与连接组蛋白 H1 的结构相似性，是 FoxA pioneer 能力的结构基础。本文扩展了这一概念，显示并非所有 Forkhead 家族成员都具备同等 pioneer 能力。
- **Soufi et al. (2015)**：pioneer factor 在重编程中的角色。本文提供了定量比较 pioneer 能力的方法，可补充该领域对 pioneer 能力差异的定量理解。
- **DeepBind / DeepSEA (2015)**：CNN 用于 TF 结合预测的开创性工作。本文在此基础上加入染色质特征通道，并引入归因解释，是「可解释深度学习」在 TF 结合领域的应用。
- **BPNet (Avsec et al., 2021)**：使用归因方法解释 TF 结合预测。本文与 BPNet 类似，但聚焦于多 TF 比较而非单 TF 精细建模。
- **ChromHMM (Ernst & Kellis, 2012)**：染色质状态注释。本文使用 ChromHMM 定义「活性」与「静止」染色质区域，作为分析 TF 染色质偏好的基础。
- **ChExMix (Yamada et al., 2019)**：ChIP-exo 数据分析工具，本文用于 peak calling 和结合模式鉴定。
- **SeqUnwinder**：k-mer 判别性 motif 发现工具，本文用于补充 motif 分析。
- **候选连接方向**：本文的「序列+染色质」联合建模框架可迁移至其他 TF 家族；归因方法可推广至「突变效应预测」或「TF 协同结合」分析；pioneer 能力梯度概念可与单细胞 ATAC-seq 数据结合，预测细胞类型特异的 pioneer 活性。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：Pioneer 能力预测器（PioneerScore）
   - **来源局限/观察**：本文仅比较了 5 个 Fox TF，且依赖过表达系统。缺乏可推广的 pioneer 能力定量预测工具。
   - **核心假设**：TF 的 pioneer 能力可由其 DNA 结合结构域的结构特征（如与 H1 的相似性、正电荷分布）和染色质互作界面预测。
   - **初步方法**：收集已发表的 pioneer/non-pioneer TF 标注，提取结构特征和序列特征，训练分类器或回归模型；用本文的 Fox TF 数据作为验证集。
   - **验证方式**：在独立细胞类型和 TF 家族中验证预测准确性；与实验测定的染色质开放能力比较。
   - **创新状态**：unverified

2. **候选名称**：单细胞 pioneer 活性图谱（scPioneerAtlas）
   - **来源局限/观察**：本文使用 bulk ChIP-exo 和 ATAC-seq，无法解析细胞异质性。Pioneer 活性可能在细胞亚群中差异显著。
   - **核心假设**：单细胞 ATAC-seq 数据中，TF 的 pioneer 活性可通过其结合位点的染色质可及性变化推断。
   - **初步方法**：利用 scATAC-seq 数据，对每个细胞亚群计算 TF motif 可及性得分；结合本文的 Fox TF 梯度作为先验，推断其他 TF 的 pioneer 活性。
   - **验证方式**：与已知 pioneer factor 的细胞类型特异性比较；用 CRISPR 干扰验证预测的 pioneer TF 功能。
   - **创新状态**：unverified

3. **候选名称**：序列-染色质互作归因的因果验证（CausalAttrib）
   - **来源局限/观察**：本文的归因分析为相关性，未进行实验验证。归因分数是否反映真实因果机制未知。
   - **核心假设**：对 CNN 归因分数最高的序列/染色质特征进行突变或扰动，应导致 TF 结合的可预测变化。
   - **初步方法**：选择 FoxA1 和 FoxG1 的若干结合位点，对归因分数高的序列区域进行点突变，用报告基因或体外结合实验验证结合变化；对染色质特征（如 H3K4me1）进行酶学扰动。
   - **验证方式**：突变/扰动后的结合变化与归因分数预测方向一致。
   - **创新状态**：unverified

4. **候选名称**：跨细胞类型的 TF 结合泛化模型（CrossCellTF）
   - **来源局限/观察**：本文模型在 mES 细胞中训练，未测试跨细胞类型的泛化能力。TF 的染色质偏好可能随细胞类型变化。
   - **核心假设**：在一种细胞类型中训练的「序列+染色质」联合模型，可迁移至其他细胞类型，且归因分析可揭示细胞类型特异的染色质依赖。
   - **初步方法**：在 mES 中训练模型，在 ESC 分化衍生物或其他细胞类型（如成纤维细胞）中测试；比较归因分数的变化。
   - **验证方式**：跨细胞类型的预测性能；归因分数变化与已知细胞类型特异染色质状态一致。
   - **创新状态**：unverified

5. **候选名称**：Forkhead 结构域-核小体互作的分子模拟
   - **来源局限/观察**：本文从基因组层面分析 pioneer 能力差异，但缺乏分子机制解释。FoxA1 与 FoxG1 的 pioneer 能力差异是否源于结构域-核小体互作的原子级差异？
   - **核心假设**：Forkhead 结构域与核小体 DNA 的结合自由能差异可解释 pioneer 能力梯度。
   - **初步方法**：用 MD 模拟或增强采样方法计算 FoxA1/FoxG1/FoxL2 等与核小体 DNA 的结合自由能；分析关键残基的相互作用网络。
   - **验证方式**：模拟预测的结合自由能与实验测定的 pioneer 能力排序一致；突变关键残基后实验验证。
   - **创新状态**：unverified