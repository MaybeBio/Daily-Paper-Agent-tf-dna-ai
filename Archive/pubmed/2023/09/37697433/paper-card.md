## 01 基本信息

- **标题**：Assessing base-resolution DNA mechanics on the genome scale
- **作者与单位**：Jiang, Wen-Jie; Hu, Congcong; Lai, Futing; Pang, Weixiong; Yi, Xinyao; Xu, Qianyi; Wang, Haojie; Zhou, Jialu; Zhu, Chunge; Kuang, Zeyu; Fan, Ruiqi; Shen, Jing; Zhou, Xiaorui; Wang, Yu-Juan; Wong, Catherine C L; Zheng, Xiaoqi; Wu, Hua-Jun（单位未在摘要中提供，推测包含北京大学等，具体未提供）
- **期刊/预印本平台**：Nucleic Acids Research
- **年份**：2023
- **论文类型**：方法学 + 基因组学应用研究
- **领域**：DNA力学（bendability）× 深度学习
- **关键词**：DNA bendability, loop-seq, deep learning, capsule network, transcription factor binding, chromatin regulation
- **DOI/arXiv 号**：10.1093/nar/gkad720
- **代码**：https://github.com/JiangWenJie-stack/DNABendNet；https://zenodo.org/record/8218189
- **数据**：https://zenodo.org/deposit/7699690 和 https://zenodo.org/deposit/7663786（307物种bendability profiles）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「DNA力学（bendability）× 深度学习预测」方向，直接服务于TF–DNA结合机制研究——通过预测DNA内在可弯曲性，揭示TF结合位点的力学特征（如CTCF、EBF1等），为理解TF如何通过DNA力学识别靶点提供基因组尺度的基础资源。与MD/对接等物理模拟方法互补，属于数据驱动的序列-力学映射模型。

---

## 02 一句话总结

本文提出深度神经网络BendNet，以酵母loop-seq实验数据为训练集，从DNA序列直接预测碱基分辨率的DNA可弯曲性（bendability），并将其应用于人类基因组，发现bendability与染色质状态、TF结合、复制时序及疾病风险区域相关，为TF–DNA互作研究提供了基因组尺度的力学特征图谱。

---

## 03 研究问题

- **具体问题**：如何在基因组尺度上获得碱基分辨率的DNA内在可弯曲性（bendability）？现有loop-seq实验通量不足以覆盖人类基因组（需数千次实验），且无法考虑个体间序列变异。
- **为什么重要**：DNA弯曲是蛋白质–DNA互作（包括TF结合、核小体定位、复制起始等）的核心物理前提。碱基分辨率的bendability图谱可帮助理解TF如何选择结合位点、核小体如何定位、以及力学特征如何影响基因调控。
- **现有方法不足**：loop-seq通量有限（每次约10万条50-bp片段），无法覆盖人类基因组；低通量方法（EMSA、smFRET）每次仅测单条片段；缺乏可推广的序列→力学预测模型。
- **精确研究问题（Can...?）**：Can a deep neural network trained on yeast loop-seq data predict base-resolution DNA bendability for arbitrary sequences from other species, and can such predictions reveal biologically meaningful associations with TF binding and chromatin regulation in the human genome?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论，属于「仅本文框架」，未经外部系统核验。

1. **早期低通量力学测量**：EMSA、smFRET等单分子/生化方法，可精确测量单条DNA片段的弯曲/环化能力，但通量极低，无法扩展至基因组尺度。
2. **高通量loop-seq**：结合smFRET与SELEX选择，一次实验可测量约10万条50-bp DNA双链体的环化率（bendability），但覆盖人类基因组仍需数千次实验，成本与时间不可行。
3. **序列-力学预测模型**：此前已有DNAcycP（基于卷积网络预测DNA cyclizability）和DeepBend等模型，但精度有限，且未系统评估跨物种泛化能力。
4. **本文位置**：BendNet在loop-seq数据上训练，采用胶囊网络（capsule network）提取序列特征，在酵母全基因组上达到碱基分辨率，并首次推广到人类基因组及307个物种，同时将bendability与TF结合、染色质状态、疾病变异关联，填补了「序列→力学→功能」链条中的预测环节。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| loop-seq通量不足以覆盖大基因组 | 人类基因组需数千次loop-seq实验 | 每次实验仅能测量约10万条50-bp片段，且需合成对应DNA双链体 | 引言第2段 |
| 个体间序列变异无法通过实验覆盖 | 参考基因组序列无法代表个体变异 | loop-seq需预先合成片段，无法覆盖所有SNV/indel | 引言第2段 |
| 现有预测模型精度不足 | DNAcycP、DeepBend等在独立测试集上表现不如BendNet | 模型架构或训练策略欠优 | Results 图1D、Supplementary Figure 1E-F |
| 碱基分辨率力学信息缺失 | 已有模型多为窗口级预测，无法定位单碱基贡献 | 模型设计未针对碱基级特征提取 | Results 图5F-H（in silico mutagenesis） |
| TF结合位点的力学特征未知 | 不同TF结合位点的bendability模式差异未被系统描述 | 缺乏基因组尺度的bendability图谱 | Results 图5A-E |

---

## 06 核心思想

### 1) 表面方法
- 训练一个端到端的深度回归模型BendNet，输入为50-bp DNA序列（one-hot编码），输出为标量bendability分数。
- 架构：卷积模块（多个卷积块，每块含3层卷积+dropout+batch norm）+ 胶囊模块（capsule层+dropout+batch norm）+ 全连接回归头。
- 训练数据：酵母loop-seq 264,860条片段（70/20/10划分）。
- 超参数优化：结构参数用控制变量法，非结构参数用遗传算法（50代×20个体）。

### 2) 核心洞察
- **序列局部特征决定力学**：卷积核可捕获k-mer级别的序列模式，胶囊层进一步编码特征间的层次关系，使模型能学习到「序列→弯曲性」的非线性映射。
- **跨物种泛化可行**：酵母训练的模型可直接预测人类、小鼠等物种的bendability，说明DNA力学编码在进化中保守。
- **bendability是功能相关特征**：人类基因组中bendability与核小体占据、TF结合、复制时序、GWAS变异频率显著相关，提示力学是调控的潜在决定因素。

### 3) 可能的普适教训 [Analysis]
- 对于TF–DNA互作研究：**序列的力学特征（而非仅序列基序）可能是TF选择结合位点的隐藏变量**。BendNet提供的碱基分辨率bendability可作为特征，与ChIP-seq、ATAC-seq等整合，提升结合位点预测精度。
- 对于AI×生物物理：**实验数据（loop-seq）与深度学习结合，可替代昂贵的大规模物理测量**，且模型可迁移至未测量物种/序列。
- 对于可解释性：in silico mutagenesis（逐碱基突变后预测bendability变化）提供了一种「力学敏感位点」的注释方法，可迁移至其他序列-功能预测任务。

---

## 07 方法总览

- **输入**：50-bp DNA序列（one-hot编码，4通道）。
- **输出**：标量bendability分数（连续值，范围与loop-seq测量一致）。
- **模型架构**：
  - 卷积模块：多个卷积块，每块含3层卷积（核大小递增）+ ReLU + dropout + batch norm。
  - 胶囊模块：胶囊层（无路由）+ dropout + batch norm。
  - 全连接层：输出1维回归分数。
  - 总参数量：287,442（285,484可训练）。
- **损失函数**：MSE。
- **优化器**：Adam。
- **训练策略**：200 epochs，取验证集MSE最小的模型。
- **超参数优化**：
  - 结构参数（卷积块数、胶囊类数/维度）：控制变量法。
  - 非结构参数（学习率、dropout率）：遗传算法，50代×20个体。
- **数据划分**：70%训练（185,402）、20%验证（52,972）、10%测试（26,486）。
- **独立验证**：额外训练一个模型，将酵母5号染色体loop-seq数据（82,404条）作为测试集。
- **外部验证**：EMSA（9个鸡CTCF位点）、E. coli cyclizability（56条）、人类（35条）、小鼠（>90,000条）。
- **反馈回路**：无显式主动学习；但模型预测结果用于下游生物学分析（TF结合、染色质状态等），形成「预测→验证→解释」的闭环。
- **假设**：DNA内在bendability主要由序列决定，且在不同物种间保守；loop-seq测量值可作为bendability的金标准。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 卷积模块 | 提取局部序列模式（k-mer特征） | DNA弯曲性由短程序列特征（如AA/TT二核苷酸）主导 | 输入：50×4 one-hot；输出：特征图 | Results 图1B-C（测试集R=0.793） | 预期显著降低预测精度（卷积是特征提取核心）[预期效应] |
| 胶囊模块 | 编码特征层次关系，增强泛化 | 捕获序列模式间的组合效应，提升跨物种迁移能力 | 输入：卷积特征图；输出：胶囊向量 | Results 图1D（优于DNAcycP/DeepBend） | 预期降低跨物种泛化能力（胶囊层对特征组合敏感）[预期效应] |
| 全连接回归头 | 将高维特征映射为标量bendability | 回归任务需要连续输出 | 输入：拼接胶囊向量；输出：标量 | Results 图1B-C | 预期无法输出连续值，模型失效 [预期效应] |
| 遗传算法超参优化 | 自动搜索最优非结构超参 | 手动调参难以覆盖高维空间 | 输入：超参空间；输出：最优超参 | Methods「Hyperparameter optimization approach」 | 预期模型精度下降（次优超参）[预期效应] |
| in silico mutagenesis | 逐碱基突变预测bendability变化 | 定位对力学贡献最大的碱基位点 | 输入：50-bp序列+单碱基突变；输出：Δbendability | Results 图5F-H | 无法提供碱基级力学注释 [预期效应] |

---

## 09 关键公式符号

本文未提供显式数学公式。核心隐式公式为：

- **回归目标**：\( \hat{y} = f_{\theta}(X) \)，其中 \( X \in \{0,1\}^{50 \times 4} \) 为one-hot编码序列，\( \theta \) 为网络参数，\( \hat{y} \) 为预测bendability。
- **损失函数**：\( \mathcal{L} = \frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2 \)（MSE）。
- **评估指标**：Pearson相关系数 \( R = \frac{\text{Cov}(y, \hat{y})}{\sigma_y \sigma_{\hat{y}}} \)。

来源：Methods「Model architecture」与Results 图1B-D。具体数值见原文。

---

## 10 实验设计与证据链

### 数据集与资源
- **训练/测试**：酵母loop-seq 264,860条（70/20/10划分）；独立测试：酵母5号染色体82,404条。
- **外部验证**：
  - 鸡CTCF位点EMSA：9条
  - E. coli cyclizability：56条
  - 人类：35条
  - 小鼠：>90,000条
- **人类基因组分析**：GM12878、K562、HepG2、A549细胞系的ChIP-seq（152个TF）、ATAC-seq、DNase-seq、MNase-seq、H3K4me3、H3K27ac、H3K79me2、POLR2A、复制时序数据。
- **物种资源**：307个物种基因组bendability profiles（分辨率10 bp）。
- **TF motif**：JASPAR数据库840个TF motifs。
- **指标**：Pearson R、Wilcoxon秩和检验、相关性分析。
- **硬件**：未提供具体GPU型号（提及GTX3090Ti用于模型比较）。

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| 主模型测试集预测 | BendNet可准确预测bendability | 与RF、SVR、AlexNet、VGG16、GoogleNet22、ResNet34、DNAcycP、DeepBend对比 | R=0.793（测试集） | BendNet优于所有对比模型 | 未证明在更复杂基因组（如人类）上同样最优 | Results 图1B-D |
| 独立染色体测试 | 模型可泛化至未见序列 | 5号染色体82,404条作为测试集 | R=0.757 | 模型具有泛化能力 | 未证明可跨物种泛化 | Supplementary Figure 1G-H |
| 外部低通量验证 | 预测与实验测量一致 | 鸡CTCF EMSA、E. coli、人类、小鼠数据 | R=0.773（E. coli）、0.654（人类）、0.762（小鼠） | 跨物种、跨实验方法一致 | 样本量小（9-56条），统计功效有限 | Results 图2B-D、Supplementary Figure 1I |
| TSS/TES bendability分析 | bendability在转录起始/终止位点降低 | 人类基因组TSS/TES ±500 bp | 观察到明显bendability低谷 | bendability与转录调控相关 | 未证明因果关系 | Results 图3A-B |
| 染色质状态关联 | bendability与染色质可及性相关 | 15种chromHMM染色质状态 | 活性状态bendability更高 | bendability是染色质状态的特征之一 | 未排除其他序列特征混杂 | Results 图3I |
| TF结合位点bendability | 不同TF结合位点力学特征不同 | 152个TF ChIP-seq峰 | 约2/3 TF结合位点bendability降低，1/3升高 | TF结合与DNA力学相关 | 未证明力学是TF选择的直接原因 | Results 图5A-B |
| in silico mutagenesis | 单碱基突变可改变bendability | 840个TF motifs，逐碱基突变 | 关键位点突变导致bendability显著变化 | 碱基分辨率力学注释可行 | 未与实验验证突变效应 | Results 图5F-H |
| 复制时序关联 | bendability与复制时序相关 | 3个细胞系复制时序数据 | 早期复制区域bendability更高 | bendability可能参与复制调控 | 未证明因果关系 | Results 图3G |
| eccDNA bendability | eccDNA序列更可弯曲 | 423,018条人类eccDNA vs 基因组背景 | eccDNA显著更bendable | 力学可能参与eccDNA形成 | 未证明力学是eccDNA成因 | Results 图6A |
| 跨物种bendability | 不同物种bendability有差异 | 307个物种基因组 | 鸟类最高，鱼类最低 | bendability在进化中变化 | 未与表型/功能直接关联 | Results 图6B-C |

---

## 11 结论正确解读

- **任务范围**：本文任务是「从序列预测DNA内在可弯曲性（bendability）」，而非直接预测TF结合或染色质状态。所有下游关联分析均为相关性发现，非因果验证。
- **oracle/真值输入**：训练标签为loop-seq实验测量值（酵母），该测量本身受实验条件（温度、盐浓度等）影响，反映的是体外内在弯曲性，非体内真实弯曲状态。
- **端到端状态**：BendNet是端到端的序列→bendability回归模型，但下游生物学结论（TF结合、染色质等）依赖外部数据整合，非端到端。
- **算力成本**：未提供具体训练时间/资源消耗；仅提及在GTX3090Ti上与其他模型对比。
- **历史数据依赖**：模型完全依赖酵母loop-seq数据，跨物种泛化依赖力学编码的进化保守性假设。
- **模型依赖**：预测精度受训练数据分布限制；人类基因组中bendability预测未经大规模实验直接验证（仅通过间接关联支持）。
- **最难情形**：跨物种（如人类）预测时，序列组成与酵母差异较大，模型可能对GC含量极端区域或重复序列预测不准。
- **群体/领域边界**：结论适用于「内在DNA弯曲性」这一物理属性，不涉及蛋白质诱导的弯曲、超螺旋等更复杂力学状态。
- **不确定性**：bendability与TF结合、染色质状态的关联为相关性，混杂因素（如序列基序、GC含量、DNA甲基化）未完全控制。

**有边界的复述**：BendNet能在酵母loop-seq数据上训练，以较高精度预测多种物种的DNA内在可弯曲性；在人类基因组中，预测的bendability与转录起始/终止位点、染色质状态、TF结合、复制时序及疾病相关变异存在统计显著关联，提示DNA力学可能是基因调控的潜在贡献因素，但因果关系未建立。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 基于体外数据训练 | 模型基于loop-seq体外测量，缺乏体内条件（如蛋白质结合、离子环境）信息 | 开发测量体内DNA力学的方法 | Discussion 末段 |
| 缺乏细胞类型/组织特异性 | 当前模型不包含细胞类型或组织特异性信息 | 结合条件信息（如细胞类型）改进模型 | Discussion 末段 |
| 仅覆盖bendability一种力学属性 | 未涉及DNA扭转、超螺旋、 torsional rigidity等 | 扩展至其他力学属性，多任务学习 | Discussion 末段 |
| 跨物种泛化依赖保守性假设 | 模型从酵母迁移至人类等物种，依赖力学编码保守 | 用更多物种实验数据验证 | Discussion 末段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|---------------------|----------|----------|------|
| 训练数据仅来自酵母 | 酵母与人类基因组序列组成差异大（GC含量、重复序列），模型可能对人类特异序列（如CpG岛、卫星DNA）预测不准 | 人类基因组应用是本文核心卖点，若泛化有偏则下游结论受影响 | 用人类loop-seq数据（如文中提到的小鼠数据）做更严格跨物种验证；或比较模型在人类高GC/重复区域的预测误差 | Methods「Training and evaluation data」 |
| 相关性≠因果 | bendability与TF结合、染色质状态的关联可能由GC含量、序列基序等混杂因素驱动 | 若力学非独立贡献，则「力学调控转录」的结论需弱化 | 在控制GC含量、基序密度后做偏相关分析；或用matched sequence pairs（仅bendability不同）做实验验证 | Results 图3-5 |
| in silico mutagenesis未实验验证 | 预测的Δbendability缺乏实验对照，可能高估单碱基效应 | 碱基级力学注释若不可靠，则下游应用受限 | 选取若干预测高影响位点，用EMSA或smFRET实验验证 | Results 图5F-H |
| 模型可解释性有限 | 卷积+胶囊网络虽能预测，但未提供序列特征与力学机制的直接映射 | 若无法解释「什么序列特征导致高bendability」，则对机制研究帮助有限 | 用注意力可视化或特征归因方法（如SHAP）分析模型 | Methods「Model architecture」 |
| 未与其他力学预测模型系统比较 | 仅与DNAcycP、DeepBend比较，未与更近期的模型（如基于Transformer的）对比 | 若存在更优模型，BendNet的「最优」结论需修正 | 在相同数据划分下与更多基线模型比较 | Results 图1D |
| 307物种bendability资源缺乏验证 | 跨物种预测未与实验数据对照，仅提供资源 | 资源若存在系统性偏差，用户可能得出错误结论 | 随机选取若干物种的若干区域，用低通量实验验证 | Results 图6B-C |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **序列→力学→功能的三层映射框架**：BendNet展示了「序列特征→DNA弯曲性→染色质/TF结合」的完整分析链。对于TF–DNA互作研究，可将bendability作为中间表型，连接序列变异与结合差异。
2. **跨物种迁移的可行性**：酵母训练的模型可直接用于人类，说明DNA力学编码在进化中保守。这提示：**TF结合位点的力学特征可能比序列基序更保守**，可用于跨物种TFBS预测。
3. **in silico mutagenesis作为力学敏感位点注释工具**：逐碱基突变预测Δbendability，可迁移至TF motif分析——识别对力学贡献大的位点，这些位点可能对TF结合亲和力影响最大。
4. **胶囊网络在序列回归任务中的优势**：相比纯CNN（DNAcycP），胶囊层可编码特征层次关系，提升泛化。对于TF–DNA结合预测，可尝试类似架构。
5. **bendability与TF结合的非单调关系**：约2/3 TF结合位点bendability降低，1/3升高（如CTCF、EBF1），提示不同TF对DNA力学需求不同。**可据此将TF分为「刚性结合型」和「柔性结合型」**，分别建模。
6. **GC含量是bendability的重要决定因素**：增强子区域bendability与GC含量强相关（R=0.431），提示在TFBS预测模型中，GC含量可作为bendability的代理特征。
7. **eccDNA的力学偏好**：eccDNA序列显著更bendable，提示DNA弯曲性可能参与环状DNA形成——对研究TF介导的染色质环化有参考价值。
8. **资源复用**：307物种bendability profiles和在线工具（http://www.dnabendnet.com/）可直接用于TF–DNA互作研究中的背景控制或特征提取。

---

## 15 与已有知识连接

- **与loop-seq原始研究**：本文直接基于Basu et al. (2021)的酵母loop-seq数据（参考文献7-8），是该方法论的深度学习扩展。
- **与DNAcycP**：DNAcycP（Li et al.）是此前基于CNN的cyclizability预测模型，BendNet在相同数据上表现更优，且首次实现碱基分辨率。
- **与DeepBend**：DeepBend是另一DNA弯曲性预测工具，BendNet在精度和速度上均超越。
- **与TF–DNA结合预测**：本文发现TF结合位点bendability模式与TF类型相关，可连接至DeepSEA、Basenji等序列-功能预测模型——bendability可作为额外特征通道。
- **与核小体定位研究**：bendability与核小体占据正相关，与Segal et al.的核小体序列偏好模型一致，可整合进核小体定位预测。
- **与3D基因组研究**：CTCF结合位点bendability升高，与CTCF介导的染色质环化（TAD边界）相关，可连接Hi-C数据分析。
- **与疾病基因组学**：bendability与GWAS SNP频率正相关，提示力学特征可能影响调控元件的功能——可连接eQTL/GWAS精细定位。
- **与MD模拟**：BendNet提供的是序列→弯曲性的统计映射，而MD模拟可提供原子级力学机制。两者可互补：BendNet筛选候选区域，MD验证具体构象变化。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选1：TF结合位点的力学特征分类器
- **名称**：TFBS-BendClass：基于bendability谱的TF结合模式分类
- **来源局限/观察**：本文发现不同TF结合位点bendability模式不同（刚性vs柔性），但未系统分类。
- **核心假设**：TF可根据其结合位点的DNA bendability特征分为若干功能类别，且这些类别与TF的结构域类型（如锌指、bZIP、homeodomain）相关。
- **初步方法**：提取840个TF motifs的bendability谱（中心±25 bp），用无监督聚类（如k-means或层次聚类）分类TF；再与TF结构域、结合亲和力数据关联。
- **验证方式**：用ChIP-seq峰验证分类的生物学一致性；用EMSA实验验证预测的力学差异。
- **创新状态**：unverified

### 候选2：bendability引导的TFBS预测增强
- **名称**：BendBoost：将bendability特征注入深度学习TFBS预测模型
- **来源局限/观察**：现有TFBS预测模型（如DeepSEA）仅用序列基序，未利用力学特征。
- **核心假设**：加入bendability作为辅助输入特征，可提升TFBS预测精度，尤其对基序不明显的TF。
- **初步方法**：在现有CNN/Transformer架构中，将BendNet输出的bendability profile作为额外通道与序列one-hot拼接；在ENCODE ChIP-seq数据上训练和评估。
- **验证方式**：与基线模型（仅序列）比较AUPRC；分层分析基序弱/强TF的增益。
- **创新状态**：unverified

### 候选3：疾病相关SNP的力学效应预测
- **名称**：BendVar：预测SNP对DNA bendability的影响及其功能后果
- **来源局限/观察**：本文发现bendability与GWAS SNP频率相关，但未分析具体SNP的力学效应。
- **核心假设**：位于调控区域的致病SNP可能通过改变局部DNA bendability影响TF结合，而非直接改变基序。
- **初步方法**：对GWAS LD区间内所有SNP，用BendNet预测参考/突变等位基因的bendability差异（Δbendability）；筛选Δbendability显著的SNP，与eQTL、ChIP-seq数据交叉验证。
- **验证方式**：用EMSA或报告基因实验验证候选SNP的力学-功能关联。
- **创新状态**：unverified

### 候选4：多任务学习扩展至其他DNA力学属性
- **名称**：MultiBend：同时预测bendability、twistability和stiffness的多任务模型
- **来源局限/观察**：本文仅覆盖bendability，作者在讨论中提及可扩展至其他力学属性。
- **核心假设**：不同力学属性共享底层序列特征，多任务学习可提升各任务精度。
- **初步方法**：在BendNet架构上增加多个输出头，分别预测bendability、twist、stiffness等；使用已有实验数据（如MNase、环化实验）作为训练标签。
- **验证方式**：比较单任务vs多任务在独立测试集上的精度；分析任务间共享表征的生物学意义。
- **创新状态**：unverified

### 候选5：bendability与3D基因组结构的关联分析
- **名称**：Bend3D：bendability对染色质环化锚点形成的贡献
- **来源局限/观察**：本文发现CTCF结合位点bendability升高，CTCF是TAD边界的关键因子。
- **核心假设**：高bendability区域更易形成染色质环化锚点，bendability可作为TAD边界预测的特征。
- **初步方法**：整合BendNet预测的人类基因组bendability与Hi-C数据，比较TAD边界/内部区域的bendability分布；构建包含bendability的TAD边界预测模型。
- **验证方式**：用独立细胞系Hi-C数据验证；用CRISPR编辑改变bendability后检测TAD结构变化。
- **创新状态**：unverified