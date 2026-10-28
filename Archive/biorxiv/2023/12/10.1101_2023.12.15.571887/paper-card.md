## 01 基本信息

- **标题**：Benchmarking DNA binding affinity models using allele-specific transcription factor binding data
- **作者**：Xiaoting Li; Lucas A. N. Melo; Harmen J. Bussemaker
- **单位**：Columbia University（Bussemaker Lab，作者单位未在摘要中明确列出，根据通讯作者及实验室推断，未提供）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2023-12-15
- **论文类型**：方法学/基准评测研究（含新软件工具）
- **领域**：计算生物学；转录因子-DNA结合；机器学习；功能基因组学
- **关键词**：allele-specific binding (ASB)；sequence-to-affinity model；ProBound；PyProBound；CTCF；ChIP-seq；beta-binomial；motif discovery
- **DOI/ID**：10.1101/2023.12.15.571887
- **代码**：https://github.com/BussemakerLab/AlleleSpecificBinding；https://github.com/BussemakerLab/PyProBound
- **数据**：AlleleDB（1000 Genomes 变异目录）；ENCODE ChIP-seq（ENCLB048DBS, ENCLB581JXH）；SRA ChIP-exo/CUT&Tag（SRR6736398, SRR6736390, SRR8435051, SRR8754587）；MotifCentral 模型
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦 TF–DNA 结合机制，提出基于等位基因特异性结合（ASB）数据的序列-亲和力模型基准评测框架，属于「AI/深度学习 × TF–DNA 结合」方向中的模型评估与可解释性方法，核心贡献在于：(1) 基于过离散二项分布的似然函数用于全基因组聚合评估；(2) PyProBound 工具（PyTorch 实现，可处理变长序列）；(3) 显式建模 DNA 片段化序列偏好以消除 ChIP-seq 系统性偏差。

## 02 一句话总结

本文提出一个基于 beta-binomial 分布的似然函数框架，利用全基因组杂合 SNP 位点的等位基因特异性 ChIP-seq 计数，对多种 TF–DNA 序列-亲和力模型（如 ProBound/MotifCentral、JASPAR、HOCOMOCO）的预测能力进行无阈值、无峰值调用的定量基准评测，并开发了 PyProBound 工具以支持从 ChIP-seq/ChIP-exo/CUT&Tag 数据中直接学习结合模型（含片段化偏差建模），同时将该似然函数扩展用于从头基序发现。

## 03 研究问题

- **具体问题**：如何在不依赖单个位点统计显著性的情况下，全基因组尺度定量评估序列-亲和力模型预测 TF 结合变异效应的能力？
- **为什么重要**：现有 ASB 检测方法（如 AlleleDB 的 beta-binomial 检验）仅在单个 SNP 水平上判断是否存在等位基因不平衡，统计功效有限，尤其对低覆盖度位点无法做出判断；而预测 SNV 对 TF 结合的影响是理解非编码变异致病机制的关键。
- **现有方法不足**：(1) 基于 motif 匹配的简单打分（如 JASPAR）缺乏定量亲和力信息；(2) 基于峰值调用的方法（peak calling）引入阈值偏差；(3) 缺乏统一的、可跨模型比较的度量标准；(4) 体外模型（如 SELEX）与体内结合环境存在差异，缺乏系统性验证手段。
- **精确研究问题**：Can a genome-wide beta-binomial likelihood function, applied to allele-specific ChIP-seq counts, provide an unbiased and statistically powerful metric for benchmarking and comparing sequence-to-affinity models of TF–DNA binding?

## 04 背景与发展脉络

**脉络标注**：以下脉络基于本文引用及作者叙述，属「经外部核验」部分（引用文献 [1]-[25] 均为已发表工作），但脉络组织方式为本文框架。

1. **阶段一：体外高通量结合实验（SELEX 等）**
   - 代表性方法：HT-SELEX [12]、SMiLE-seq [15]
   - 优点：可大规模、定量刻画 TF 固有结合偏好
   - 局限：缺乏体内染色质环境信息（共因子、可及性、甲基化等）

2. **阶段二：体内结合实验（ChIP-seq 等）**
   - 代表性方法：ChIP-seq [13]、ChIP-exo [16]、CUT&Tag [17]
   - 优点：反映真实细胞环境下的 TF 占据
   - 局限：分辨率有限、存在片段化偏差、难以直接推断序列-亲和力关系

3. **阶段三：计算模型构建**
   - 代表性方法：ProBound [18]（生物物理可解释的机器学习框架）、DeepBind [20]、JASPAR [19]、HOCOMOCO [21]
   - 优点：可从数据中学习序列-亲和力映射
   - 局限：模型质量缺乏统一评测标准；体外模型与体内数据存在差距

4. **阶段四：等位基因特异性分析（本文位置）**
   - 代表性方法：AlleleDB [5]（beta-binomial 检验）
   - 本文主张：将 beta-binomial 从「检验工具」转化为「评测度量」，聚合全基因组证据，无需单点显著；同时扩展 PyProBound 以处理变长序列和片段化偏差，实现从体内数据直接学习模型。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单点 ASB 检测统计功效不足 | 大多数 TF 仅有极少 SNP 达到显著 ASB 阈值；如 CTCF 有 2,231 个 ASB SNP，但 PU.1 和 EBF1 分别仅 387 和 189 个 | ChIP-seq 覆盖度有限，单点检验需要大量读数才能达到显著性 | Results 节 "Prediction of CTCF allele-specific binding events"；Methods "Collection of Allele-Specific Binding SNVs" |
| 缺乏跨模型统一评测标准 | 不同来源的 motif 模型（JASPAR、HOCOMOCO、ProBound）难以直接比较预测能力 | 各模型输出尺度不同，缺乏统一的定量度量 | Results 节 "A metric for binding affinity model quality" |
| ChIP-seq 片段化存在序列偏好 | 初始 PyProBound 模型在片段末端显示强位置偏差 | DNA 超声破碎的序列依赖性未被显式建模 | Results 节 "Taking DNA fragmentation bias into account"；Supplemental Figure S4B |
| 体外模型与体内结合存在差距 | SELEX 模型预测 ASB 方向正确但可能不够精确 | 体外缺乏染色质环境、共因子、竞争性结合 | Results 节 "Prediction of CTCF allele-specific binding events"；Discussion 节 |
| 峰值调用引入阈值偏差 | 传统 peak calling 依赖显著性阈值，丢失弱信号 | 阈值选择影响下游分析 | Results 节 "A metric for binding affinity model quality"（隐含，作者主张无阈值方法） |

## 06 核心思想

### 1) 表面方法
- 构建 beta-binomial 似然函数，以 SNP 位点的等位基因 ChIP-seq 计数为数据，以序列-亲和力模型预测的等位基因亲和力比值为预测变量，全基因组聚合评估模型解释力。
- 开发 PyProBound（PyTorch 实现），支持变长序列输入，显式建模 DNA 片段化序列偏好，从 ChIP-seq/ChIP-exo/CUT&Tag 数据中直接学习 TF 结合模型。
- 将同一似然函数用于从头基序发现（优化基序参数以最大化 beta-binomial 似然）。

### 2) 核心洞察
- **等位基因特异性作为天然内参**：杂合 SNP 位点的两个等位基因处于完全相同的染色质环境（同一细胞、同一可及性、同一共因子环境），因此等位基因计数差异直接反映序列本身对结合的影响，天然控制了所有反式因素和局部染色质状态。
- **聚合而非单点检验**：将似然函数在全基因组所有可及 SNP 上聚合，即使单个位点不显著，也能通过大量位点的联合信号评估模型质量。
- **片段化偏差是 ChIP-seq 建模的系统性混淆因素**：若不显式建模，会污染学习到的结合模型。

### 3) 可能的普适教训 [Analysis]
- 在 TF–DNA 结合建模中，利用「同一环境下的等位基因对比」是一种强大的自然实验设计，可推广到其他功能基因组学数据（如 ATAC-seq、甲基化）的模型评测。
- 任何基于 ChIP-seq 的 TF 结合模型都应考虑片段化序列偏好，否则可能学到片段化伪影而非真实结合偏好。
- 将统计检验框架转化为模型评测度量（likelihood-based benchmarking）是一种可迁移的方法论思路。

## 07 方法总览

- **输入**：
  - 等位基因 ChIP-seq 计数（参考/替代等位基因读数）来自 AlleleDB
  - 序列-亲和力模型（MotifCentral/ProBound、JASPAR、HOCOMOCO）
  - 基因组序列（hg19，含 SNP 侧翼 ±29 bp）
  - 原始 ChIP-seq/ChIP-exo/CUT&Tag FASTQ（用于 PyProBound 训练）
- **输出**：
  - 各模型的 beta-binomial 似然值（用于基准比较）
  - PyProBound 训练的 TF 结合模型（含片段化偏差模型）
  - 从头发现的基序（ASB-derived motif）
- **模块**：
  1. ASB 数据收集与预处理（AlleleDB 下载、SNP 筛选）
  2. 序列-亲和力打分（滑动窗口求和，覆盖所有结合偏移）
  3. Beta-binomial 似然函数（含过离散参数 ρ 和背景结合常数 C 的估计）
  4. PyProBound 训练（变长序列、多模块乘积模型、L-BFGS 优化）
  5. 从头基序发现（优化基序参数以最大化 beta-binomial 似然）
- **训练**：
  - PyProBound 使用 L-BFGS 优化，损失函数基于片段计数的负对数似然
  - 正则化：L2（λ = 10⁻⁶ 用于体内模型，λ = 10⁻⁴ 用于 ASB 衍生模型）+ 指数屏障
  - 无显式训练/验证集划分描述（未提供）
- **反馈回路**：无显式主动学习或迭代闭环；模型评估与训练相对独立
- **文字流程**：
  1. 从 AlleleDB 获取等位基因 ChIP-seq 计数及 SNP 位点
  2. 对每个 SNP，以参考/替代等位基因的侧翼序列计算各模型的累积结合亲和力
  3. 以 beta-binomial 似然函数评估模型预测与观测等位基因计数的吻合度
  4. 对多个模型（SELEX 来源、体内来源、公共数据库来源）进行系统比较
  5. 使用 PyProBound 从 ChIP-seq/ChIP-exo/CUT&Tag 原始数据学习新模型（含片段化偏差建模）
  6. 将 beta-binomial 似然函数嵌入 PyProBound 优化目标，实现从头基序发现

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Beta-binomial 似然函数 | 全基因组聚合评估模型预测等位基因不平衡的能力 | 单点检验功效不足，需要聚合信号 | 输入：等位基因计数、预测亲和力比值；输出：似然值 | Results 图 3A；MotifCentral 模型 LL 显著优于对照（p < 10⁻⁸） | 移除后无法进行跨模型定量比较（预期影响） |
| 滑动窗口累积亲和力计算 | 将 TF 结合模型映射到 SNP 位点的等位基因特异性打分 | TF 可在多个偏移/方向结合，需累积所有可能结合模式 | 输入：SNP 侧翼序列、模型；输出：每个等位基因的累积亲和力 | Results 图 1B；Supplemental Figure S2 显示包含所有偏移的重要性 | 仅用单一偏移会丢失结合信息，降低预测能力（预期影响） |
| PyProBound 变长序列支持 | 直接分析 paired-end ChIP-seq 片段（变长） | 原始 ProBound 无法处理变长序列，限制体内数据应用 | 输入：FASTQ/片段序列；输出：结合模型参数 | Results 节 "Taking DNA fragmentation bias into account" | 无法利用 paired-end 数据，需截断/延伸导致信息损失（预期影响） |
| 片段化偏差建模 | 显式学习 DNA 片段化序列偏好 | ChIP-seq 片段化存在序列依赖性，混淆结合模型 | 输入：片段末端序列；输出：片段化偏好模型 | Supplemental Figure S4B-D；建模后位置偏差消失且预测性能提升 | 不建模则学到片段化伪影，模型质量下降（实测：LL = –3.2086 vs –3.1995，p < 10⁻⁸） |
| 从头基序发现（ASB-driven） | 直接从等位基因计数中学习基序 | 验证 ASB 信号确实由 TF 结合序列偏好驱动 | 输入：等位基因计数、侧翼序列；输出：基序参数 | Results 图 5；与 MotifCentral 模型 Pearson r = 0.94 | 无法独立验证 ASB 的序列来源（预期影响） |
| 引导/重采样评估 | 评估模型间似然差异的统计显著性 | 需要判断模型差异是否显著 | 输入：SNP 集合；输出：bootstrap 分布 | Results 图 3A；Wilcoxon test p < 10⁻⁸ | 无法判断模型差异的统计显著性（预期影响） |

## 09 关键公式符号

**1. Beta-binomial 似然函数（核心评测指标）**

文中未给出完整公式，但根据描述可重构：

\[
L(\rho, C) = \prod_{i} \frac{B(y_i + \alpha_i, n_i - y_i + \beta_i)}{B(\alpha_i, \beta_i)}
\]

其中：
- \( y_i \)：SNP i 的参考等位基因读数
- \( n_i \)：SNP i 的总读数
- \( \alpha_i = p_i(1-\rho)/\rho \)，\( \beta_i = (1-p_i)(1-\rho)/\rho \)
- \( p_i \)：参考等位基因的期望比例，由模型预测的亲和力比值决定
- \( \rho \)：过离散参数（over-dispersion）
- \( C \)：背景结合常数（非特异性结合）

**2. 累积亲和力计算**

\[
A_{ref} = \sum_{k} \frac{K_{seq_k}^{ref}}{1 + K_{seq_k}^{ref}}, \quad A_{alt} = \sum_{k} \frac{K_{seq_k}^{alt}}{1 + K_{seq_k}^{alt}}
\]

其中 \( K_{seq} \) 为模型预测的相对亲和力，k 遍历所有可能的结合偏移/方向。

**3. PyProBound 片段计数模型**

\[
f_{i,r} = \alpha_{NS} + \sum_{m} \sum_{k} \frac{K_{m,seq_{i,k}}}{1 + K_{m,seq_{i,k}}}
\]

其中：
- \( f_{i,r} \)：片段 i 在轮次 r 的相对浓度
- \( \alpha_{NS} \)：非特异性结合项
- \( m \)：结合模式索引
- \( K_{m,seq} \)：模式 m 对序列 seq 的相对亲和力

**4. 损失函数（PyProBound 优化目标）**

\[
\mathcal{L} = -\sum_{i,r} k_{i,r} \log f_{i,r} + \lambda \sum_{\theta} \theta^2 + \text{exponential barrier}
\]

其中 \( k_{i,r} \) 为观测计数，λ 为 L2 正则化系数，exponential barrier 防止数值错误。

**来源**：Methods 节 "Beta-binomial model of genome-wide allelic effects on the binding affinity"、"In vivo binding data analysis with PyProBound"、"PyProBound regularization"。

## 10 实验设计与证据链

**数据集与规模**：
- ASB 数据：AlleleDB（1000 Genomes 变异目录），CTCF 2,231 个 ASB SNP + 44,422 个对照 SNP；PU.1（SPI1）387 个 ASB SNP；EBF1 189 个 ASB SNP
- 体外模型：MotifCentral（ProBound 训练的 HT-SELEX 模型）
- 公共数据库模型：JASPAR、HOCOMOCO
- 体内数据：ENCODE CTCF ChIP-seq（ENCLB048DBS, ENCLB581JXH）；SRA ChIP-exo（SRR6736398, SRR6736390）和 CUT&Tag（SRR8435051, SRR8754587）
- 基因组：hg19

**指标**：
- Beta-binomial 对数似然（LL）
- 过离散参数 ρ 的估计
- 与对照（等位基因等概率）模型的似然比

**评测协议**：
- 对每个 SNP，计算参考/替代等位基因的累积亲和力比值
- 以该比值作为 beta-binomial 模型的预测变量
- Bootstrap（1000 次）评估 LL 差异的统计显著性

**表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| MotifCentral 模型预测 CTCF ASB 方向 | 体外模型能预测体内等位基因结合偏好 | 预测亲和力差异 vs. 观测等位基因计数；覆盖 1,000 倍亲和力范围 | 预测方向与观测一致 | ProBound 体外模型具有体内预测能力 | 不能证明模型在所有亲和力范围内均最优 | Results 图 2 |
| Beta-binomial LL 比较（CTCF） | 模型显著优于等概率对照 | MotifCentral vs. 固定 p=0.5 对照 | LL = –3.2356 vs. –3.2021（p < 10⁻⁸） | 模型具有显著预测能力 | 差异绝对值较小，需注意效应量 | Results 图 3A |
| 过离散参数比较 | 模型解释部分等位基因变异 | ρ 估计值比较 | 模型 ρ 显著低于对照 | 模型解释了部分等位基因计数变异 | 仍有大量未解释变异 | Results 图 3A |
| PU.1 和 EBF1 验证 | 框架可推广至其他 TF | MotifCentral 模型 vs. 对照 | 趋势一致但信号较弱 | 框架具有通用性 | 低 ASB SNP 数限制统计功效 | Supplemental Figure S1, S3 |
| PyProBound 片段化建模 vs 截断 | 显式片段化建模提升模型质量 | 片段化建模 vs 200bp 截断 | 片段化建模 LL 更优（–3.1995 vs –3.2086，p < 10⁻⁸） | 片段化偏差是重要混淆因素 | 未比较其他截断策略 | Results 图 4；Supplemental Figure S4 |
| CUT&Tag 模型 vs ChIP-seq 模型 | 不同体内 assay 的模型质量差异 | CUT&Tag vs ChIP-seq vs ChIP-exo 来源模型 | CUT&Tag 模型表现最佳 | CUT&Tag 可能具有更低的序列偏好噪声 | 仅针对 CTCF，需更多 TF 验证 | Results 图 4 |
| ASB 从头基序发现 | 等位基因计数可直接学习基序 | 优化基序参数最大化 beta-binomial LL | 与 MotifCentral 模型高度一致（Pearson r = 0.94） | ASB 信号确实由 TF 结合序列偏好驱动 | 仅验证 CTCF 一个 TF | Results 图 5 |

## 11 结论正确解读

- **任务范围**：本文仅针对 TF–DNA 结合中的等位基因特异性效应预测，不涉及全基因组结合位点预测、染色质可及性建模或共因子效应。
- **Oracle/真值输入**：等位基因 ChIP-seq 计数来自 AlleleDB，该数据库基于 14 个个体的组织样本，其 ASB 标注本身依赖 beta-binomial 检验，存在一定误标注率。
- **端到端状态**：非端到端。流程为「已有模型 → 预测亲和力 → 似然评估」，模型训练与评估分离；PyProBound 训练虽从原始数据出发，但评估仍依赖独立 ASB 数据。
- **算力成本**：未提供具体训练时间或硬件需求。
- **历史数据依赖**：依赖 AlleleDB 的 1000 Genomes 变异注释和 ChIP-seq 数据；模型质量受限于这些数据的覆盖度和质量。
- **模型依赖**：所有评估基于现有序列-亲和力模型（ProBound、JASPAR、HOCOMOCO），不涉及深度学习端到端模型（如 DeepBind 虽被引用但未纳入基准比较）。
- **最难情形**：低亲和力位点、低覆盖度 SNP、非 CTCF 的 TF（ASB SNP 数量少时统计功效不足）。
- **群体/领域边界**：仅人类数据；仅 3 个 TF（CTCF、PU.1、EBF1）；仅评估 SNP 效应，不涉及插入缺失或结构变异。
- **不确定性**：bootstrap 提供了 LL 差异的统计显著性，但未报告效应量置信区间；ρ 和 C 的估计不确定性未充分讨论。

**有边界的复述**：本文证明，在 CTCF 的 2,231 个 ASB SNP 上，ProBound 体外模型预测的等位基因亲和力差异与观测的 ChIP-seq 等位基因计数显著一致（p < 10⁻⁸），且该似然框架可推广至 PU.1 和 EBF1；同时，显式建模 DNA 片段化序列偏好可提升从 ChIP-seq 学习的模型质量，且 ASB 数据可直接用于从头基序发现（与独立模型 Pearson r = 0.94）。这些结论仅限于人类 CTCF、PU.1、EBF1 三个 TF 及 AlleleDB 数据范围。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 单点 ASB 检测统计功效不足 | 大多数 TF 仅有极少 SNP 达到显著 ASB 阈值 | 使用聚合似然框架替代单点检验 | Results 节 "A metric for binding affinity model quality" |
| 体外模型与体内环境差异 | SELEX 模型可能未完全反映体内共因子效应 | 从体内数据（ChIP-seq/CUT&Tag）直接学习模型 | Discussion 节 |
| 片段化偏差的复杂性 | 简单截断无法消除片段化偏好 | 显式建模片段化序列偏好 | Results 节 "Taking DNA fragmentation bias into account" |
| 仅关注直接结合效应 | 未考虑间接结合、染色质可及性变异 | 未来可扩展至更复杂模型 | Discussion 节（隐含） |
| 基准数据有限 | 仅 3 个 TF 有足够 ASB SNP 进行验证 | 需要更多 TF 和细胞类型的 ASB 数据 | Discussion 节（隐含） |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 基准仅覆盖 3 个 TF | CTCF、PU.1、EBF1 可能不代表所有 TF 的结合模式（如锌指蛋白、bHLH 等） | 框架的通用性未充分验证 | 在更多 TF 类型上重复分析 | Results 节仅列出 3 个 TF |
| 依赖 AlleleDB 的 ASB 标注 | AlleleDB 的 beta-binomial 检验本身可能有误标注，且仅覆盖 14 个个体 | 标注质量直接影响基准结果 | 使用独立 ASB 数据集（如 ADASTRA）交叉验证 | Methods "Collection of Allele-Specific Binding SNVs" |
| 未与深度学习模型（如 DeepBind）直接比较 | 文中引用 DeepBind 但未纳入基准 | 无法判断 ProBound 类模型与深度学习方法在 ASB 预测上的相对优劣 | 将 DeepBind、BPNet 等模型纳入同一似然框架比较 | 文中仅比较 ProBound、JASPAR、HOCOMOCO |
| 累积亲和力计算未考虑共因子 | 仅使用单一 TF 模型，未建模共因子协同效应 | 真实结合可能涉及多个 TF 协同 | 引入多 TF 联合模型 | Methods 节描述仅单一模型 |
| 片段化偏差建模的验证有限 | 仅通过 LL 提升和位置偏差消失来验证，未直接验证片段化模型本身 | 片段化模型可能过度拟合 | 使用独立片段化数据（如 sonication 对照）验证 | Supplemental Figure S4 |
| 从头基序发现仅验证 CTCF | 单一 TF 的验证不足以证明方法通用性 | 方法可能对某些 TF 类型失效 | 在多个 TF 的 ASB 数据上重复 | Results 图 5 |
| 未报告计算成本 | PyProBound 训练时间和资源需求未说明 | 影响方法实用性评估 | 补充性能基准 | 未提供 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **等位基因特异性作为内参的设计范式**：利用杂合 SNP 位点两个等位基因处于相同染色质环境的特性，天然控制反式因素。可迁移到本课题：在评估 TF–DNA 结合模型时，优先使用等位基因特异性数据（如 AlleleDB、个人基因组 ChIP-seq）而非仅用 peak 强度或 motif 匹配。

2. **Beta-binomial 似然作为模型评测指标**：将统计检验框架转化为连续、可比较的模型质量度量，避免阈值依赖。可迁移到本课题：在比较不同 TF–DNA 结合预测模型（如 MD 模拟 vs. 深度学习 vs. 位置权重矩阵）时，可构建统一的似然基准框架。

3. **片段化偏差的显式建模**：ChIP-seq 数据中 DNA 片段化存在序列偏好，若不建模会污染结合模型。可迁移到本课题：任何基于 ChIP-seq 的 TF 结合模型训练或评估都应考虑片段化偏差，可借鉴 PyProBound 的多模块乘积模型设计。

4. **体外-体内模型差距的系统评估**：SELEX 模型在预测体内 ASB 时表现良好但非最优，体内数据训练的模型（尤其 CUT-CUT&Tag）更优。可迁移到本课题：在构建 TF–DNA 结合模型时，应明确标注训练数据来源（体外 vs. 体内），并优先使用体内数据或进行域适应。

5. **从头基序发现的似然优化**：将 beta-binomial 似然嵌入基序参数优化，可直接从等位基因计数中学习结合偏好。可迁移到本课题：当缺乏传统 ChIP-seq peak 数据时，可利用等位基因计数进行无监督/弱监督的基序发现。

6. **滑动窗口累积亲和力计算**：考虑所有可能的结合偏移和方向，而非仅最优匹配位置。可迁移到本课题：在计算 SNP 效应时，应累积所有偏移的贡献，而非仅取最大得分。

## 15 与已有知识连接

- **ProBound 原始框架**：本文的 PyProBound 是对 Rube et al. (2022) [18] 的 ProBound 的 PyTorch 重实现，核心算法（多轮 SELEX 建模、生物物理可解释参数）保持一致，但扩展了变长序列支持。可参考原始 ProBound 论文了解算法细节。
- **AlleleDB**：Chen et al. (2016) [5] 的等位基因特异性结合数据库，本文使用其 beta-binomial 模型作为基础，但将其从「检验工具」转化为「评测度量」。
- **ASB 与疾病变异关联**：本文引用的 GWAS 研究 [2,3] 表明非编码变异通过影响 TF 结合导致表型变异，本文的基准框架可直接用于评估此类预测的可靠性。
- **DeepBind**：Alipanahi et al. (2015) [20] 的深度学习 TF 结合预测模型，本文引用但未纳入基准比较，可作为后续扩展方向。
- **HT-SELEX 与 MotifCentral**：本文使用 MotifCentral 中 ProBound 训练的体外模型，与 Jolma et al. (2013) [12] 的 HT-SELEX 数据直接相关。
- **CUT&Tag 技术**：Kaya-Okur et al. (2019) [17] 的低背景体内结合检测方法，本文发现其训练的模型优于 ChIP-seq 模型，提示该技术可能具有更低的序列偏好噪声。
- **候选方向 [Analysis]**：本文的似然框架可扩展至：(1) 深度学习模型（如 BPNet、DeepSEA）的基准评测；(2) 与 MD 模拟预测的结合自由能变化（ΔΔG）进行比较；(3) 多 TF 协同结合模型评估。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：基于等位基因似然的深度学习 TF–DNA 结合模型基准平台
   - **来源局限/观察**：本文仅比较了 ProBound、JASPAR、HOCOMOCO，未纳入深度学习模型（如 DeepBind、BPNet）
   - **核心假设**：深度学习模型在 ASB 预测上可能优于传统 motif 模型，但需统一基准验证
   - **增量**：将 beta-binomial 似然框架扩展至深度学习模型，提供标准化评测协议
   - **初步方法**：在相同 ASB 数据集上，对多个深度学习模型进行似然评估，并与 ProBound 比较
   - **验证方式**：使用多个 TF 的 ASB 数据，bootstrap 评估 LL 差异显著性
   - **创新状态**：unverified

2. **候选名称**：MD 模拟预测的 SNP 效应与等位基因 ChIP-seq 数据的系统比较
   - **来源局限/观察**：本文仅使用序列-亲和力模型，未涉及物理模拟方法
   - **核心假设**：MD 或对接方法预测的 ΔΔG 与等位基因计数存在定量关联
   - **增量**：将物理模拟预测纳入同一似然框架，实现 AI 与物理方法的直接比较
   - **初步方法**：对 CTCF 的 ASB SNP 子集进行 MD 模拟或结构预测，计算 ΔΔG，与 beta-binomial 似然关联
   - **验证方式**：比较 MD 预测与序列模型的似然值，评估增量预测能力
   - **创新状态**：unverified

3. **候选名称**：考虑共因子协同的等位基因结合预测模型
   - **来源局限/观察**：本文仅使用单一 TF 模型，未考虑共因子效应；作者在讨论中提及共因子可能解释部分未解释变异
   - **核心假设**：引入共因子 motif 或染色质状态特征可提升 ASB 预测能力
   - **增量**：在 beta-binomial 框架中引入多 TF 联合结合项
   - **初步方法**：在 CTCF 位点附近扫描共因子 motif，作为协变量加入似然模型
   - **验证方式**：比较含/不含共因子项的模型 LL
   - **创新状态**：unverified

4. **候选名称**：基于 ASB 数据的细胞类型特异性 TF 结合模型训练
   - **来源局限/观察**：AlleleDB 数据来自 14 个个体的多种组织，但本文未利用细胞类型信息
   - **核心假设**：细胞类型特异的 ASB 模式可训练出更精确的组织特异结合模型
   - **增量**：利用 AlleleDB 的组织标签，训练细胞类型特异的 PyProBound 模型
   - **初步方法**：按组织分层训练模型，比较各组织模型的差异和预测能力
   - **验证方式**：交叉验证 LL 和组织特异性 motif 差异
   - **创新状态**：unverified

5. **候选名称**：ASB 驱动的从头基序发现扩展到多 TF 协同 motif
   - **来源局限/观察**：本文验证了单 TF 基序的从头发现（Pearson r = 0.94），但未探索多 TF 协同 motif
   - **核心假设**：ASB 数据可同时学习多个 TF 的协同结合模式
   - **增量**：扩展 PyProBound 以支持多 motif 联合优化
   - **初步方法**：在 CTCF 的 ASB 位点附近同时优化 CTCF 和候选共因子 motif
   - **验证方式**：与已知共因子 motif 数据库比对，评估新发现 motif 的生物学意义
   - **创新状态**：unverified