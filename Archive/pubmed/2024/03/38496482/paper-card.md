## 01 基本信息
- **标题**: On the identification of differentially-active transcription factors from ATAC-seq data
- **作者与单位**: Gerbaldo, Felix Ezequiel; Sonder, Emanuel; Frei, Selina; Wang, Jiayi; Gapp, Katharina; Robinson, Mark D; Germain, Pierre-Luc（ETH Zurich 等，具体单位未提供）
- **期刊/预印本平台**: bioRxiv (preprint server for biology)
- **年份**: 2024-03-18
- **论文类型**: 方法基准评测（benchmark）研究
- **领域**: 计算表观基因组学 / 转录因子活性推断
- **关键词**: ATAC-seq, transcription factor activity, chromVAR, monaLisa, differential accessibility, motif
- **DOI/arXiv 号**: 10.1101/2024.03.06.583825
- **代码**: https://github.com/ETHZ-INS/DTFAB
- **数据**: 半模拟数据见 Zenodo: 10.5281/zenodo.10732704, 10.5281/zenodo.10781849, 10.5281/zenodo.10781759, 10.5281/zenodo.10781109；TRAFTAC 数据 GSE260504
- **阅读日期**: 未提供
- **在课题方向中的位置**: 本文系统评测了从 ATAC-seq 数据推断差异活性 TF 的多种计算方法（chromVAR、monaLisa、diffTF、VIPER、decoupleR、fGSEA、ATACseqTFEA 等），属于「TF–DNA 结合机制 × 计算方法」中的**方法评测与流程优化**类别。对课题的启示在于：如何从染色质可及性数据中可靠地推断 TF 结合活性的变化，以及不同方法在何种条件下表现优劣。

## 02 一句话总结
本文通过 curated 的真实数据集和半模拟数据，系统评测了多种从 ATAC-seq 推断差异活性 TF 的方法，发现经过调整的 chromVAR-limma 流程、monaLisa 以及 GC 平滑分位数归一化结合多元线性模型是三种最有前景的方法。

## 03 研究问题
- **具体问题**: 从 ATAC-seq 数据中识别差异活性转录因子（differentially-active TFs）的最佳方法是什么？
- **为什么重要**: TF 活性常受翻译后修饰调控，其 mRNA 表达不能反映活性变化。ATAC-seq 可提供全基因组染色质可及性信息，但如何从中可靠推断 TF 活性缺乏系统比较。
- **现有方法不足**: 存在多种方法（fold-change-based 和 sample-based 两大类），但从未被系统比较；方法间的假设、统计框架和适用条件差异大，用户缺乏选择依据。
- **精确研究问题**: "Can we identify which computational methods most reliably detect differentially-active TFs from ATAC-seq data, and what modifications improve their performance?"

## 04 背景与发展脉络
（标注：以下脉络基于本文 Introduction 和 Discussion 的框架，属「仅本文框架」）

1. **TF 活性测量的传统方法**：ChIP-seq 可直接测量 TF 结合，但耗时、一次只能测一个 TF、依赖高质量抗体。
2. **ATAC-seq 的出现**：作为简单、快速、低起始量的染色质可及性检测方法，可间接反映 TF 结合（TF 结合位点通常处于开放染色质区域）。
3. **基于 motif 的 TF 活性推断方法**：
   - **fold-change-based 家族**：对峰水平差异可及性（如 logFC）进行 motif 富集分析，代表方法包括 monaLisa、diffTF、fGSEA、MEIRLOP 等。
   - **sample-based 家族**：为每个样本计算每个 motif 的活性分数，再进行组间比较，代表方法包括 chromVAR、VIPER/msVIPER、decoupleR 等。
4. **本文主张的位置**：首次系统比较这两大类方法，并识别出关键改进点（如 chromVAR 的 limma 替代 t 检验、GC 平滑分位数归一化），同时引入半模拟框架以在受控条件下评估方法。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 缺乏 ground truth | 真实扰动数据中，敲低/激活一个 TF 会影响其互作因子和下游 TF，使"真阳性"难以定义 | TF 网络复杂，扰动一个 TF 会级联影响其他 TF 活性 | Discussion 首段 |
| 方法间缺乏系统比较 | 多种方法存在但从未被同时评估 | 方法来自不同领域（表观基因组学、转录组学），假设差异大 | Introduction 末段 |
| chromVAR 原生差异检验不佳 | `chromVAR::differentialDeviations` 表现差 | 原生 t 检验未利用 moderating 信息，对少量样本不稳定 | Results 图 1-2；"Improvements to chromVAR-based approaches" 节 |
| 技术变异干扰 | 样本间 GC 含量、片段长度分布差异影响 motif 活性推断 | ATAC-seq 存在已知的 GC 偏好和片段长度偏好 | "Technical variation" 半模拟节；Results 图 3 |
| motif 相似性导致多变量方法不稳定 | 高度相似的 motif 在多变量回归中获得不一致的系数 | 共线性问题：相似 motif 的峰集合高度重叠 | TRAFTAC 应用节（JUNB/FOS 例） |
| 无核小体片段过滤效果不稳定 | 仅用 NF 片段或 NF 峰并不一致地提升效果 | NF 片段对某些 TF 更信息丰富，但对其他 TF 可能丢失信号 | "Focusing on nucleosome-free peaks/fragments" 节 |

## 06 核心思想

**1) 表面方法**：
- 收集 8 个 curated 真实数据集（含已知 TF 扰动）和半模拟数据集
- 运行 10+ 种方法/变体，包括 chromVAR（原生及多种修改）、monaLisa（两种变体）、diffTF、VIPER/msVIPER、decoupleR（多种变体）、fGSEA、ATACseqTFEA、简单线性回归等
- 用 rank of true motif、网络分数、精确率/召回率等指标评估

**2) 核心洞察**：
- 针对染色质数据设计的方法（chromVAR、monaLisa）整体优于从转录组改造的方法（VIPER、decoupleR 等）
- chromVAR 的关键改进在于用 limma 替代原生 t 检验（利用经验贝叶斯方差 moderating）
- GC 平滑分位数归一化能显著提升非专门方法的表现，说明技术变异是主要干扰源
- 方法间的互补性有限，简单聚合不能带来一致提升

**3) 可能的普适教训** [Analysis]：
- 方法的统计框架（是否利用跨特征信息、是否处理技术协变量）比方法本身的"设计初衷"更重要
- 在缺乏 ground truth 的推断任务中，半模拟框架是验证方法的关键工具
- 对多变量方法，输入特征（motif 集合）的相似性结构需要显式处理

## 07 方法总览

**输入**：
- ATAC-seq 峰水平计数矩阵（样本 × 峰）
- 峰基因组坐标
- motif 位置权重矩阵（PWM）集合（HOCOMOCO）
- 峰与 motif 的匹配关系（FIMO 扫描）

**输出**：
- 每个 motif 的差异活性 p 值/排名（fold-change-based 方法）
- 每个样本 × motif 的活性分数 + 组间差异检验结果（sample-based 方法）

**主要模块**：
1. **数据预处理**：适配子去除（Trimmomatic）、比对（Bowtie2）、峰 calling（MACS2）、峰 resize（300bp）、计数（chromVAR::getCounts）
2. **Motif 处理**：HOCOMOCO motif 集合、FIMO 扫描、motif 聚类为 archetypes
3. **活性推断方法**：
   - chromVAR 变体：原生 differentialDeviations、deviations+limma、z-scores+limma、z-scores+limma+quantile 归一化
   - monaLisa：vsZero、vsOthers
   - diffTF（analytic mode）
   - fGSEA
   - ATACseqTFEA
   - VIPER/msVIPER
   - decoupleR（ulm、mlm、wsum、udt、consensus）
   - 简单线性回归（ulm binary/scores）
   - 正则化回归（lasso/ridge）
4. **评估模块**：rank of true motif、网络分数（基于 BioGRID 互作）、精确率/召回率

**训练/调优**：无监督方法无训练；limma 为经验贝叶斯框架，无需调优；半模拟用于验证而非训练

**反馈回路**：无显式反馈回路；方法为一次性推断

**文字流程**：
1. 对每个数据集，从原始数据（或已处理数据）生成峰计数矩阵
2. 用 FIMO 将 motif 匹配到峰上
3. 对 fold-change-based 方法：先做峰水平差异分析（edgeR），再对 logFC 排序的峰列表进行 motif 富集
4. 对 sample-based 方法：计算每样本每 motif 的活性分数（如 chromVAR deviation），再用 limma 做组间差异检验
5. 对每种方法输出 motif 排名，与 ground truth 比较

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| chromVAR deviation 计算 | 计算每样本每 motif 的偏差分数（可及性相对期望的偏离） | 提供 motif 活性的连续度量，校正峰长度和文库大小 | 输入：峰×样本计数、峰×motif 指示矩阵；输出：样本×motif deviation/z-score | Results 图 1-2 显示 chromVAR 变体整体最优 | 移除后失去 sample-based 框架的核心 |
| limma 差异检验（替代原生 t 检验） | 对 chromVAR 分数做经验贝叶斯 moderating 的差异检验 | 原生 t 检验在小样本下方差估计不稳 | 输入：样本×motif 分数矩阵、分组；输出：每 motif 的 p 值 | "chromVAR(z)>limma 显著优于 differentialDeviations"（Results 图 1-2） | 预期：差异检验功效下降，小样本下假阳性增加 [Analysis] |
| GC 平滑分位数归一化 | 在峰计数矩阵上按 GC 含量分箱做分位数归一化 | 校正样本间 GC 偏好差异 | 输入：峰×样本计数、峰 GC 含量；输出：归一化计数 | Results 图 3 显示多数方法受益 | 预期：GC 相关技术变异未被校正，非专门方法表现下降 [Analysis] |
| monaLisa 分箱富集 | 将峰按 logFC 分箱，检验 motif 在各箱的富集 | 提供 fold-change 与 motif 关联的非参数视图 | 输入：峰 logFC、峰 motif 匹配；输出：每 motif 每箱的富集 p 值 | Results 图 1-2 显示 monaLisa 为 top 方法之一 | 移除后失去 fold-change-based 框架的最佳代表 |
| motif archetype 聚类 | 将高度相似的 motif 合并为 archetype | 减少 motif 集合冗余，避免多变量方法共线性 | 输入：motif PWM 集合；输出：archetype 集合 | Methods "Clustering of motif models" 节 | 预期：多变量方法稳定性提升，但可能损失单个 motif 的分辨率 [Analysis] |
| 半模拟框架 | 从基线 ATAC-seq 数据中，按 ChIP-seq 峰位置引入可量化扰动 | 提供受控 ground truth，避免真实数据中 TF 网络干扰 | 输入：基线 ATAC-seq、ChIP-seq 峰、扰动参数；输出：半模拟数据集 | Methods "Semi-simulations" 节；Results 图 4 | 移除后无法区分方法在真实数据中的表现差异是源于方法本身还是 ground truth 模糊 |

## 09 关键公式符号

本文为基准评测研究，无新提出的数学模型。关键统计框架如下：

**chromVAR deviation**（已有方法，文中使用）：
- 对样本 j、motif k 的偏差分数：
  $d_{jk} = \frac{1}{n_k} \sum_{i \in S_k} \frac{x_{ij} - \hat{\mu}_{ij}}{\hat{\sigma}_{ij}}$
  其中 $x_{ij}$ 为峰 i 在样本 j 中的计数，$\hat{\mu}_{ij}$、$\hat{\sigma}_{ij}$ 为基于背景峰（GC 含量和平均可及性匹配）的期望和标准差，$S_k$ 为含 motif k 匹配的峰集合，$n_k$ 为该集合大小。

**limma 经验贝叶斯 moderating**（已有方法，文中应用）：
- 对每个 motif 的样本间差异，limma 通过跨 motif 合并方差信息来 moderating 方差估计：
  $\tilde{s}_g^2 = \frac{d_0 s_0^2 + d_g s_g^2}{d_0 + d_g}$
  其中 $s_g^2$ 为特征 g 的样本方差，$s_0^2$ 为先验方差，$d_0$、$d_g$ 为自由度。

**半模拟扰动**（文中设计）：
- 对峰 i 在扰动组中的期望计数：$n_{ij}^s = \min\{\lceil n_{ij}^0 \cdot FC_i \cdot p \rceil, n_{ij}^0\}$
  其中 $n_{ij}^0$ 为原始计数，$FC_i$ 为从参考 ChIP-seq 数据中匹配的 fold-change，$p \in \{0, 0.25, 0.5, 1, 3\}$ 为扰动强度。

**Simes p 值聚合**（用于 monaLisa 多箱 p 值）：
- $p_{Simes} = \min_k \left( \frac{m}{k} p_{(k)} \right)$
  其中 $p_{(k)}$ 为排序后的第 k 个 p 值，m 为箱数。

## 10 实验设计与证据链

**数据集**：
- 8 个 curated 真实数据集：包含 TF 激活（如 ESR1/2 配体处理、NR3C1 地塞米松处理）和抑制（如 CRISPRi 敲低 GATA1/2、RUNX1/2、KLF1、MYC）实验，每组 2-3 个生物学重复
- 半模拟数据集：以淋巴母细胞系 HG03442 的 6 个对照样本为基线，引入 4 个 TF（CTCF、CEBPB、MAZ、ZNF143）的单因子扰动，5 种扰动强度
- 技术变异模拟：改变 GC 含量和片段长度分布

**指标**：
- Rank of true motif（真 motif 的排名）
- 网络分数（Network score）：基于 BioGRID 物理互作网络，衡量 top k 中互作因子的富集
- 精确率/召回率（以 motif archetypes 中与真 motif 聚类的成员为阳性）

**基线**：chromVAR 原生 differentialDeviations 作为默认基线

**评测协议**：每个方法在每个数据集上运行，输出 motif 排名；对 sample-based 方法用 limma 做组间比较；对 fold-change-based 方法用 edgeR 计算峰 logFC 后输入各方法

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 真实数据集基准 | 不同方法在真实扰动数据中的表现 | 10+ 方法/变体 × 8 数据集 | chromVAR(z)>limma 和 monaLisa 排名最高；原生 differentialDeviations 表现差 | 针对染色质设计的方法优于转录组改造方法；limma 改进有效 | 数据集数量有限（8 个），TF 类型覆盖不全 | Results 图 1 |
| 半模拟验证 | 在受控条件下确认真实数据结果 | 4 TF × 5 扰动强度 × 方法 | 结果与真实数据一致；扰动强度增加时所有方法表现提升 | 真实数据结论在受控条件下可复现 | 半模拟假设"可及性变化反映结合变化"可能过于简化 | Results 图 4 |
| GC/FL 技术变异 | 技术变异对方法的影响 | 有/无 GC 平滑分位数归一化 | 多数方法受益于 GC 归一化；FL 变异影响较小 | GC 偏差是主要技术干扰源 | 未系统评估其他技术变异（如批次效应） | Results 图 3 |
| 网络分数 | 方法能否识别 TF 的互作网络成员 | 与 rank of true motif 对比 | 网络分数与 rank 大致一致 | 方法在识别直接靶标和互作因子方面表现一致 | 网络分数依赖 BioGRID 注释完整性 | Results 图 1 中栏 |
| 方法聚合 | 简单聚合能否提升表现 | 3 种 top 方法的 p 值聚合 | 无一致提升 | 方法间互补性有限 | 未测试更复杂的集成策略 | "Limited gain from simple method aggregation" 节 |
| NF 片段过滤 | 仅用无核小体片段是否提升 | 全片段 vs NF 片段 vs NF 峰 | 效果因数据集而异，无一致结论 | NF 过滤不是普适改进策略 | 未深入分析何种条件下 NF 过滤有益 | "Focusing on nucleosome-free peaks/fragments" 节 |
| TRAFTAC 应用 | top 方法在新数据上的表现 | chromVAR、monaLisa、GC>MLM>limma 在 NFkB 敲降数据上 | 检测到 NFkB 相关 motif 变化，但 AP-1（JUN/FOS）信号更强 | 方法可发现非预期的生物学信号（AP-1 与 NFkB 通路交叉） | 缺乏独立验证 AP-1 变化的实验 | Results 图 5 |

## 11 结论正确解读

- **任务范围**: 本文仅评估"从 ATAC-seq 数据推断差异活性 TF"这一任务，不涉及 TF 结合位点预测、motif 发现或 TF-TF 互作网络推断。
- **oracle/真值输入**: 真实数据集的"真值"是实验扰动的 TF，但作者承认由于 TF 网络效应，真值本身有模糊性；半模拟数据中真值是已知的，但基于"可及性变化反映结合变化"的假设。
- **端到端状态**: 评测覆盖从原始数据到最终 TF 排名的完整流程，但各方法内部参数未系统调优（除 chromVAR 背景迭代数外）。
- **算力成本**: 未报告详细算力需求；diffTF 运行时间最长（数小时/数据集），chromVAR 和 monaLisa 在合理时间内完成。
- **历史数据依赖**: 方法依赖 motif 数据库（HOCOMOCO）和参考基因组注释，不同版本可能影响结果。
- **模型依赖**: 半模拟依赖 ChIP-seq 数据作为扰动模板，ChIP-seq 质量影响模拟真实性。
- **最难情形**: 低扰动强度（p=0.25）、motif 与 ChIP-seq 峰匹配率低的 TF（如 CEBPB）、以及存在大量相似 motif 的家族（如 JUN/FOS）。
- **群体/领域边界**: 结论基于人类细胞系数据（HEK293、K562、淋巴母细胞等），对非人类物种或不同组织类型的外推需谨慎。
- **不确定性**: 方法排名在真实数据和半模拟间基本一致，但具体排名受数据集组成影响；p 值校准普遍不佳（FDR 高于名义水平）。

**有边界的复述**: 在本文测试的 8 个真实数据集和半模拟条件下，chromVAR（使用 limma 做差异检验、增加背景迭代至 2000 次）和 monaLisa（vsOthers 模式）是识别差异活性 TF 的最可靠方法；GC 平滑分位数归一化能提升多数方法的表现；但所有方法的绝对表现受扰动强度、motif 质量和技术变异的影响，且 p 值校准不完善。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| Ground truth 模糊性 | 真实扰动数据中，敲低/激活一个 TF 会影响互作因子和下游 TF，使"真阳性"难以定义 | 使用更精确的扰动系统（如快速降解系统）和更早的时间点 | Discussion 首段 |
| 数据集规模有限 | 仅 8 个真实数据集，每组 2-3 个样本 | 更大规模、更多样化的基准数据集 | Discussion "Summary" 节 |
| 半模拟假设简化 | 假设可及性变化与 TF 结合变化成正比，未考虑竞争性结合、协同结合等 | 更精细的模拟模型 | Methods "Semi-simulations" 节 |
| 未覆盖所有方法 | 未包含深度学习方法（如 BPNet、DeepSEA 等） | 将深度学习方法纳入未来基准 | Discussion 末段 |
| p 值校准不佳 | 多数方法的 FDR 高于名义水平 | 开发更好的校准方法 | Results 图 2A 相关讨论 |
| 技术变异覆盖不全 | 仅模拟了 GC 和片段长度变异，未覆盖批次效应、测序深度差异等 | 更全面的技术变异模拟 | Discussion "Technical variation" 相关 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 真实数据集的"真值"仅基于实验扰动，而非直接测量 TF 结合 | 扰动可能通过间接效应改变其他 TF 活性，使"真阳性"定义偏窄或偏宽 | 若真值定义有偏，方法排名可能反映的是"识别直接扰动效应"而非"识别 TF 活性变化" | 使用 ChIP-seq 或 CUT&RUN 直接测量扰动前后的 TF 结合变化作为更精确的真值 | Discussion 首段 |
| 半模拟中扰动仅施加于 ChIP-seq 峰区域，未模拟可及性变化的传播效应 | 真实生物学中，一个 TF 的活性变化会通过染色质状态改变影响远处位点 | 若模拟过于简化，方法在模拟中的表现可能高估其在真实数据中的表现 | 在模拟中加入间接效应（如异染色质扩散、增强子-启动子互作变化） | Methods "Semi-simulations" 节 |
| chromVAR 的改进（limma、2000 背景迭代）是在同一批数据集上评估的，存在过拟合风险 | 改进可能针对这些特定数据集的特征（如样本量、效应大小）而非普适 | 若改进过拟合，新数据集上的表现可能不如预期 | 在独立数据集上验证改进的泛化性 | Results 图 1-2 |
| 网络分数依赖 BioGRID 互作注释，注释偏差可能影响方法排名 | 某些 TF 的互作网络注释更完整，可能使这些 TF 的方法表现被高估 | 若注释偏差系统性地偏向某些方法，排名可能失真 | 使用不依赖注释的评估指标，或控制注释完整性 | Methods "Network score" 节 |
| 未报告方法间的统计检验（如方差分析、配对检验） | 方法排名的差异可能不显著 | 若无统计显著性，推荐"top 3"方法缺乏严格依据 | 在方法间进行配对检验或 Friedman 检验 | Results 图 1-2 |
| TRAFTAC 应用中 AP-1 信号强于 NFkB 被解释为"通路交叉"，但缺乏独立验证 | AP-1 信号可能反映 TNF-α 处理的直接效应而非 NFkB 敲降的间接效应 | 若解释错误，可能误导对方法特异性的理解 | 在无 TNF-α 刺激的 NFkB 敲降实验中验证 AP-1 变化 | Results 图 5 |

## 14 学到什么

### Agent 提炼的知识候选

1. **方法选择原则**: 对于 TF 活性推断任务，优先选择针对染色质数据设计的方法（chromVAR、monaLisa），而非从转录组改造的方法（VIPER、decoupleR）。**可迁移性**: 在课题中设计 TF–DNA 结合预测模型时，应优先考虑利用染色质可及性特征的模型架构。

2. **统计框架的重要性**: chromVAR 原生 t 检验被 limma 替代后表现显著提升，说明经验贝叶斯方差 moderating 在小样本（n=2-3/组）下至关重要。**可迁移性**: 在 TF 结合预测模型的训练中，对少量样本的方差估计应使用 moderating 方法。

3. **GC 归一化的必要性**: GC 平滑分位数归一化能提升多数方法表现，说明技术变异（GC 偏好）是 ATAC-seq 推断的主要干扰源。**可迁移性**: 在构建 TF–DNA 结合模型时，应将 GC 含量作为协变量或使用 GC 归一化预处理。

4. **半模拟验证框架**: 本文设计的半模拟流程（从真实数据出发，引入已知单因子扰动）是验证推断方法的有效工具。**可迁移性**: 在课题中，可设计类似的半模拟框架来验证 TF–DNA 结合预测模型，避免真实数据中 ground truth 模糊的问题。

5. **Motif 集合的冗余问题**: 高度相似的 motif 会干扰多变量方法（如 mlm、lasso），使用 motif archetypes（聚类后）可缓解。**可迁移性**: 在构建 TF–DNA 结合模型时，应对 motif 集合进行去冗余处理。

6. **多方法交叉验证**: 不同方法的结果不一致时（如 TRAFTAC 中 NFYA 的案例），应谨慎解释，可能需要结合多种方法的共识。**可迁移性**: 在课题中，对 TF 结合预测结果应使用多种方法交叉验证。

7. **p 值校准的普遍问题**: 多数方法的 p 值校准不佳，FDR 高于名义水平。**可迁移性**: 在报告 TF 结合预测的显著性时，应使用经验 FDR 或置换检验而非名义 p 值。

8. **NF 片段过滤的非普适性**: 仅用无核小体片段并非普适改进策略，效果因 TF 和数据集而异。**可迁移性**: 在课题中，不应默认 NF 片段优于全片段，需根据具体 TF 和生物学问题测试。

## 15 与已有知识连接

- **chromVAR** (Schep et al., 2017, Nature Methods): 本文的核心方法之一，原用于 scATAC-seq 的 motif 活性偏差分析。本文扩展了其在 bulk ATAC-seq 中的应用，并改进了差异检验步骤。
- **monaLisa** (Machlab et al., 2022, Nucleic Acids Research): 基于分箱富集的 motif 分析工具，本文验证了其在差异 TF 推断中的有效性。
- **diffTF** (Berest et al., 2019, Genome Biology): 基于 GC 分箱的差异 TF 活性推断方法，本文将其纳入基准。
- **VIPER/msVIPER** (Alvarez et al., 2016, Nature Genetics): 基于 regulon 的 master regulator 分析方法，本文测试了其从转录组改造到 ATAC-seq 的适用性。
- **decoupleR** (Badia-i-Mompel et al., 2022, Bioinformatics): 统一的生物活性推断框架，本文测试了其多种变体。
- **limma** (Ritchie et al., 2015, Nucleic Acids Research): 经验贝叶斯差异表达分析工具，本文将其应用于 chromVAR 分数和峰 logFC 的差异检验。
- **edgeR** (Robinson et al., 2010, Bioinformatics): 用于峰水平差异可及性分析，为 fold-change-based 方法提供输入。
- **TRAFTAC 技术** (Samelson et al., 2023, Nature Biotechnology): 本文应用该技术敲降 NFkB，展示了 top 方法在新数据上的表现。
- **HOCOMOCO** (Kulakovskiy et al., 2018, Nucleic Acids Research): motif 数据库，本文使用其 v10-11 版本。
- **ENCODE** (ENCODE Project Consortium, 2012): 提供 NR3C1 数据集和半模拟基线数据。

## 16 研究想法

### Agent 生成的研究候选

**候选 1: 基于深度学习的 TF 活性推断模型**
- **名称**: TF-ATAC-Deep: 端到端的差异 TF 活性预测模型
- **来源局限/观察**: 本文基准显示 chromVAR+limma 为最优，但 chromVAR 的偏差计算基于线性假设，无法捕捉非线性交互（如协同结合、核小体竞争）
- **核心假设**: 深度学习模型（如注意力机制）可以从 ATAC-seq 峰模式中学习更复杂的 TF 结合信号
- **初步方法**: 以峰×样本计数矩阵和 motif 匹配为输入，用 CNN/Transformer 编码峰模式，预测每样本每 motif 的活性分数；用本文的 8 个真实数据集和半模拟框架评估
- **验证方式**: 与 chromVAR+limma 和 monaLisa 在相同基准上比较 rank of true motif 和网络分数
- **创新状态**: unverified

**候选 2: 结合 TF–DNA 物理模拟的活性推断**
- **名称**: 基于结构信息的 TF 活性先验增强
- **来源局限/观察**: 本文指出 motif 质量（motif 与真实结合位点的匹配度）是影响方法表现的关键因素，但未利用结构信息
- **核心假设**: 将 TF 的 DNA 结合域结构信息（如来自 AlphaFold 或 PDB）编码为 motif 的先验权重，可提升弱 motif TF 的检测
- **初步方法**: 用 MD 模拟或结构比对计算 TF 与不同 DNA 序列的结合亲和力，作为 motif 匹配分数的校准；将校准后的分数输入 chromVAR 或 monaLisa
- **验证方式**: 在 CEBPB（motif 质量差）等困难 TF 上比较校准前后的检测能力
- **创新状态**: unverified

**候选 3: 单细胞 ATAC-seq 的差异 TF 活性推断**
- **名称**: scTF-ATAC: 单细胞水平的 TF 活性变化检测
- **来源局限/观察**: 本文提到 chromVAR 原生于 scATAC-seq，但基准仅用 bulk 数据；单细胞数据的稀疏性和 dropout 问题未在本文中评估
- **核心假设**: 单细胞数据中，基于插补或聚合的策略可提升 TF 活性推断的灵敏度
- **初步方法**: 在 scATAC-seq 数据上比较 chromVAR、monaLisa 和深度生成模型（如 scVI）的 TF 活性推断；评估不同插补策略的影响
- **验证方式**: 使用已知 TF 扰动的 scATAC-seq 数据集（如 CRISPR 筛选数据）验证
- **创新状态**: unverified

**候选 4: 多组学整合的 TF 活性推断**
- **名称**: MultiTF-ATAC: 整合 ATAC-seq 和 RNA-seq 的差异 TF 活性推断
- **来源局限/观察**: 本文仅用 ATAC-seq 数据，但 TF 活性变化常伴随靶基因表达变化，整合转录组信息可能提升推断精度
- **核心假设**: 将 TF 的靶基因表达变化作为先验，可约束 ATAC-seq 推断的搜索空间
- **初步方法**: 构建概率模型，联合建模 ATAC-seq 峰可及性和 RNA-seq 基因表达，推断 TF 活性后验分布
- **验证方式**: 在同时有 ATAC-seq 和 RNA-seq 的扰动数据集上评估
- **创新状态**: unverified

**候选 5: TF 活性推断的基准测试框架扩展**
- **名称**: TF-Bench-ATAC: 标准化 TF 活性推断基准
- **来源局限/观察**: 本文的基准框架（真实数据 + 半模拟）是领域内首次系统评测，但数据集数量有限，且未覆盖非模式物种
- **核心假设**: 更大规模、更多样化的基准可揭示方法在不同条件下的适用边界
- **初步方法**: 扩展本文框架，纳入更多物种（小鼠、斑马鱼）、更多扰动类型（化学抑制、突变）和更多技术（snATAC-seq、mCAB-seq）
- **验证方式**: 社区协作建立标准化基准，定期更新方法排名
- **创新状态**: unverified