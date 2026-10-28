## 01 基本信息

- **标题**: De novo distillation of thermodynamic affinity from deep learning regulatory sequence models of in vivo protein-DNA binding
- **作者与单位**: Alexandari, Amr M; Horton, Connor A; Shrikumar, Avanti; Shah, Nilay; Weilert, Melanie; Pufall, Miles A; Fordyce, Polly M; Kundaje, Anshul（单位未在摘要中提供）
- **期刊/平台**: bioRxiv (preprint server for biology)
- **年份**: 2023
- **论文类型**: 预印本（方法学/计算生物学）
- **领域**: 计算生物学；转录因子-DNA结合；深度学习；热力学亲和力
- **关键词**: Transcription factors, protein-DNA binding, deep learning, thermodynamic affinity, in vivo binding, regulatory genomics
- **DOI/ID**: 10.1101/2023.05.11.540401
- **代码**: https://github.com/kundajelab/affinity_distillation
- **数据**: GEO:GSE207001（ChIP-nexus）；Zenodo: https://zenodo.org/record/6762262（GR MITOMI）
- **阅读日期**: 未提供
- **在课题方向中的位置**: 本文提出了一种从深度学习模型（BPNet）中提取热力学亲和力的方法（Affinity Distillation），通过in silico marginalization技术，将in vivo ChIP数据训练的模型转化为可预测体外热力学亲和力的工具。该方法直接连接了深度学习预测与TF-DNA结合的热力学机制，为理解TF-DNA结合机制提供了新的计算框架，属于「蛋白质-DNA互作 × 深度学习」交叉方向的重要方法学进展。

## 02 一句话总结

本文提出Affinity Distillation（AD）方法，通过将序列插入随机背景并利用BPNet深度学习模型的count head进行in silico marginalization，从in vivo ChIP数据训练的模型中提取热力学亲和力，在多种酵母和人类TF上以优于传统motif方法（Weeder、STREME、MoDISco）的精度预测了体外测量的相对结合自由能（ΔΔG）。

## 03 研究问题

- **具体问题**: 能否从in vivo蛋白-DNA结合数据训练的深度学习模型中提取出定量的热力学亲和力信息？
- **为什么重要**: TF-DNA结合的热力学亲和力是理解基因调控的基础，但in vivo结合数据受多种上下文因素影响，难以直接提取纯热力学信息。传统motif方法无法捕捉非加性效应和上下文依赖，而深度学习模型虽能准确预测in vivo结合，但缺乏物理解释。
- **现有方法不足**: 
  - 传统motif方法（PWM等）是加性模型，无法捕捉非加性（epistatic）效应
  - 体外实验（如MITOMI、BET-seq）通量有限，无法覆盖所有序列
  - 深度学习模型虽预测准确，但被视为"黑箱"，无法提取定量热力学参数
- **精确研究问题**: Can thermodynamic affinities be distilled de novo from deep learning models trained on in vivo protein-DNA binding data, with accuracy comparable to or exceeding traditional motif-based methods?

## 04 背景与发展脉络

**注：此脉络基于本文框架，未经外部系统核验。**

1. **阶段一：PWM/motif模型时代**
   - 代表方法：PWM、位置权重矩阵
   - 优点：简单、可解释、计算高效
   - 局限：线性加性假设，无法捕捉非加性效应和上下文依赖

2. **阶段二：体外高通量实验**
   - 代表方法：MITOMI、BET-seq、gcPBM、SELEX-seq
   - 优点：提供定量热力学数据
   - 局限：通量有限，无法覆盖全部序列空间

3. **阶段三：深度学习预测模型**
   - 代表方法：DeepBind、DeepSEA、BPNet、Enformer
   - 优点：预测精度高，能捕捉复杂序列语法
   - 局限：缺乏物理解释，无法直接提取热力学参数

4. **阶段四：深度学习+热力学桥接（本文位置）**
   - 代表方法：Affinity Distillation
   - 核心创新：通过in silico marginalization从深度学习模型中提取热力学亲和力
   - 优势：结合深度学习的预测能力和热力学的可解释性

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| in vivo结合数据与体外亲和力脱节 | 原始ChIP-seq/ChIP-nexus计数与体外测量相关性差（r=0.18-0.31） | 上下文因素（染色质状态、协同因子、竞争）干扰纯热力学信号 | Results 图6A；Results 图3E |
| 传统motif方法无法捕捉非加性效应 | 多突变组合的效应不等于单突变效应之和 | PWM等加性模型假设位点独立贡献 | Results 图5O |
| 深度学习模型缺乏物理解释 | 预测准确但无法提取热力学参数 | 模型参数与热力学量之间无直接对应关系 | Discussion 第1段 |
| 体外实验通量有限 | 无法覆盖所有可能的序列变异 | 实验成本和时间限制 | Discussion 第2段 |
| 多突变效应预测困难 | 加性模型在远离共识序列时误差增大 | 非特异性结合和构象变化等非线性效应 | Results 图5O |

## 06 核心思想

### 1) 表面方法
Affinity Distillation（AD）是一种从训练好的深度学习模型（BPNet）中提取热力学亲和力的后处理方法。具体步骤包括：(1) 将目标序列插入数百个随机生成的背景序列中；(2) 用训练好的BPNet模型预测这些序列的count输出；(3) 计算插入序列与无插入背景之间的平均log count比（Δlog(counts)），作为该序列的热力学亲和力评分。

### 2) 核心洞察
[Analysis] 本文的核心洞察在于：虽然深度学习模型是在in vivo数据上训练的，包含了上下文效应，但通过将目标序列插入大量随机背景并进行marginalization（平均化），可以有效地"消除"上下文效应，提取出序列内在的热力学贡献。这类似于统计力学中的系综平均——通过平均化消除环境干扰，提取本征性质。

### 3) 可能的普适教训
[Analysis] 这一方法展示了深度学习模型可以隐式学习到热力学级别的信息，即使训练数据是in vivo的复杂上下文。这提示我们：深度学习模型可能比我们想象的更接近底层物理规律，关键在于找到合适的"解码"方法。对于TF-DNA互作研究，这意味着in vivo数据中蕴含的热力学信息可以通过适当的计算策略被提取出来。

## 07 方法总览

- **输入**: 目标DNA序列（任意长度，通常为包含TF结合位点的序列）
- **输出**: 热力学亲和力评分（Δlog(counts)），可校准为ΔΔG值
- **核心模块**:
  1. BPNet模型训练（in vivo ChIP数据）
  2. In silico marginalization（随机背景插入+预测+平均）
  3. 校准（线性回归将marginalization score映射到ΔΔG）
- **训练**: BPNet模型在ChIP-seq/ChIP-nexus数据上训练，使用标准BPNet架构（卷积层+空洞卷积+dilated layers）
- **工具**: Keras (TensorFlow backend)；DeepSHAP用于模型解释
- **反馈回路**: 无显式反馈回路；模型训练完成后固定，AD作为后处理步骤
- **假设**: (1) BPNet模型能准确预测in vivo结合；(2) 随机背景的marginalization能消除上下文效应；(3) count head的输出与热力学亲和力存在单调关系

**文字流程**:
1. 收集in vivo ChIP数据（ChIP-seq或ChIP-nexus）
2. 训练BPNet模型预测结合profile和count
3. 对目标序列，生成≥100个随机背景（通过dinucleotide shuffling从held-out genomic peaks生成）
4. 将目标序列插入每个背景的中心位置
5. 用训练好的BPNet预测插入序列和纯背景的count
6. 计算Δlog(counts) = mean(log(count_insert) - log(count_background))
7. （可选）用少量体外测量数据校准Δlog(counts)到ΔΔG

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| BPNet模型 | 预测in vivo TF结合profile和count | 提供序列到结合的映射函数 | 输入：one-hot DNA序列；输出：count预测+profile预测 | Results 图1C-D | 无法进行AD；模型精度直接影响AD质量 |
| In silico marginalization | 消除上下文效应，提取序列本征贡献 | 将in vivo模型转化为热力学预测器 | 输入：目标序列+随机背景；输出：Δlog(counts) | Results 图1E-F | 无法消除上下文效应，预测精度下降 |
| 随机背景生成 | 提供多样化的序列上下文 | 确保marginalization的有效性 | 输入：held-out genomic peaks；输出：随机背景序列 | Methods "Affinity Distillation"节 | 背景多样性不足可能导致偏差 |
| 校准模块 | 将marginalization score映射到ΔΔG | 将相对评分转化为绝对能量 | 输入：marginalization scores + 体外测量值；输出：校准函数 | Results 图1G | 无法获得绝对能量值，但相对排序仍有效 |
| DeepSHAP解释 | 识别模型关注的序列特征 | 验证模型学习到生物学相关特征 | 输入：模型+序列；输出：贡献度分数 | Results 图1C | 无法验证模型学到的特征是否合理 |

**消融效应说明**: 文中未提供系统消融实验，但图4D显示marginalization背景数量影响动态范围。预期移除随机背景生成会导致AD退化为直接使用模型预测，无法消除上下文效应。

## 09 关键公式符号

**1. Marginalization score（核心公式）**:

$$\Delta \log(\text{counts}) = \frac{1}{N} \sum_{i=1}^{N} \left[ \log(\hat{y}(s_i + x)) - \log(\hat{y}(s_i)) \right]$$

- $\hat{y}$: BPNet模型的count head输出
- $s_i$: 第i个随机背景序列
- $x$: 目标插入序列
- $N$: 背景数量（≥100）

**2. 校准公式**:

$$\Delta\Delta G = \alpha \cdot \Delta \log(\text{counts}) + \beta$$

- $\alpha, \beta$: 线性回归参数，通过最小二乘拟合得到

**3. Langmuir等温线（用于体外实验拟合）**:

$$R = \frac{R_{max} \cdot [DNA]}{K_d + [DNA]}$$

- $R$: 结合比例
- $R_{max}$: 饱和结合值
- $[DNA]$: DNA浓度
- $K_d$: 解离常数

## 10 实验设计与证据链

**数据集与规模**:
- 酵母：Pho4（PB-exo 5686个区域，ChIP-nexus 1621个区域）、Cbf1（PB-exo 1057个区域，ChIP-nexus 1174个区域）
- 人类：GR（ChIP-seq 17203个区域）、MAX（HeLa-S3 20438个区域）、Myc（HeLa-S3 16391个区域，K562 17318个区域）、GABPA（HepG2 6129个区域，肝组织9543个区域）、E2F1（MCF7 19373个区域）
- 体外验证：BET-seq（酵母，约10^6序列）、MITOMI（人类GR，188序列）、gcPBM（人类TF，最多30000探针）

**指标**: Pearson相关系数(r)、均方根误差(RMSE, kcal/mol)

**评测协议**: 训练BPNet模型→AD提取marginalization scores→校准→与体外测量比较

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| PB-exo酵母TF测试 | AD能从in vitro数据训练的模型提取亲和力 | AD vs 原始PB-exo计数 vs motif方法 | Pho4: r=-0.91 (AD) vs r=-0.73 (原始)；Cbf1: r=-0.74 (AD) vs r=-0.61 (原始) | AD显著提升与体外测量的相关性 | 未证明AD适用于所有TF类型 | Results 图1E-F |
| 全序列空间泛化 | AD能预测未见过的序列 | 所有10^6 BET-seq序列 | Pho4: r=0.89；Cbf1: r=0.77 | AD具有良好的泛化能力 | 未测试更远距离的序列变异 | Results 图1F |
| 校准到绝对能量 | AD分数可校准为ΔΔG | 线性回归校准 | RMSE=0.204 (Pho4), 0.409 (Cbf1) kcal/mol | AD可提供定量能量预测 | 校准需要少量体外数据 | Results 图1G |
| 人类GR测试 | AD适用于人类TF | GR ChIP-seq vs MITOMI | r=0.95, RMSE=0.414 kcal/mol | AD跨物种适用 | 仅测试了一个人类TF | Results 图5K |
| 多人类TF测试 | AD广泛适用 | 6个TF，gcPBM验证 | r=0.66-0.86 | AD在多种TF上有效 | 不同TF间性能差异大 | Results 图6 |
| 非加性效应捕捉 | AD能学习epistatic效应 | 成对突变 vs 加性预测 | AD准确预测非加性效应 | AD超越加性模型 | 未系统量化epistasis程度 | Results 图5O |
| 与motif方法比较 | AD优于传统方法 | AD vs Weeder/STREME/MoDISco | AD在所有测试中RMSE最低 | AD是当前最优方法 | 未测试所有可能的motif方法 | Results 图1H-I, 5L |

## 11 结论正确解读

- **任务范围**: 本文方法适用于从in vivo ChIP数据训练的深度学习模型中提取热力学亲和力，适用于多种TF类型（bHLH、ETS、E2F、核受体）
- **oracle/真值输入**: 体外测量数据（BET-seq、MITIOMI、gcPBM）作为校准和验证的真值
- **端到端状态**: 非端到端；需要先训练BPNet模型，再进行AD后处理，最后用少量体外数据校准
- **算力成本**: 未明确报告；BPNet训练为GPU密集型，AD本身计算开销较低
- **历史数据依赖**: 依赖in vivo ChIP数据（ChIP-seq/ChIP-nexus）和少量体外测量数据
- **模型依赖**: 依赖BPNet架构；其他架构可能不适用
- **最难情形**: 低亲和力位点、非共识序列、需要捕捉非加性效应的场景
- **群体/领域边界**: 适用于有足够in vivo ChIP数据和少量体外校准数据的TF；不适用于无ChIP数据的TF
- **不确定性**: 校准需要少量体外数据；不同TF间性能差异大（r=0.66-0.95）

**有边界的复述**: AD方法能够从in vivo ChIP数据训练的BPNet模型中提取与体外热力学测量高度相关的亲和力评分，在测试的酵母和人类TF上优于传统motif方法，但需要少量体外数据校准以获得绝对能量值，且性能因TF而异。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 校准需要体外数据 | 需要少量体外测量数据（<1000个）进行校准 | 未明确提及 | Results 图1G |
| 不同TF性能差异 | r范围0.66-0.95，部分TF表现不佳 | 未明确提及 | Results 图6 |
| 酵母基因组中STR预测困难 | 酵母STR短且稀少，导致预测性能下降 | 数据增强策略 | Results 图4E-F |
| 未测试所有TF类型 | 仅测试了bHLH、ETS、E2F、核受体 | 未明确提及 | Results 图6 |
| 依赖BPNet架构 | 方法基于BPNet，其他架构可能不适用 | 未明确提及 | Methods "Model architecture"节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| 校准数据量小 | 使用<1000个体外测量值校准，可能不足以捕捉所有序列空间 | 校准质量直接影响绝对能量预测精度 | 增加校准数据量，测试性能是否持续提升 | Results 图1G |
| 背景生成策略 | 使用dinucleotide shuffling生成背景，可能无法完全模拟基因组上下文 | 背景多样性不足可能导致marginalization不充分 | 比较不同背景生成策略（如基因组随机采样、进化保守序列） | Methods "Affinity Distillation"节 |
| 线性校准假设 | 假设marginalization score与ΔΔG呈线性关系 | 实际关系可能非线性，影响绝对能量预测 | 测试非线性校准函数（如多项式、sigmoid） | Results 图1G |
| 未报告置信区间 | 未提供预测不确定性的估计 | 实际应用中需要知道预测可靠性 | 使用bootstrap或贝叶斯方法估计不确定性 | 全文未提及 |
| 与体外实验的差异 | 体外实验条件（如MITIOMI）与in vivo环境差异大 | 校准可能引入系统性偏差 | 使用多种体外实验交叉验证 | Results 图5 |
| 非加性效应的机制解释 | 未解释AD如何捕捉非加性效应 | 理解机制有助于改进方法 | 分析AD预测的epistatic模式与已知蛋白-DNA相互作用机制的关系 | Results 图5O |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **In silico marginalization技术**: 通过将目标序列插入大量随机背景并平均化预测，可以从上下文相关的模型中提取序列本征贡献。这一方法可迁移到其他TF-DNA结合预测任务，如从in vivo数据中提取纯热力学参数。

2. **深度学习模型隐含热力学信息**: 本文证明in vivo训练的深度学习模型隐式编码了热力学级别的信息。这提示在TF-DNA互作研究中，深度学习模型不仅是预测工具，还可能作为"虚拟实验平台"来探索序列-亲和力关系。

3. **校准策略**: 使用少量体外测量数据（<1000个）校准深度学习输出到绝对能量空间，这一策略可推广到其他需要定量预测的场景。

4. **非加性效应的捕捉**: AD方法能捕捉传统motif方法无法处理的非加性效应，这对于理解TF结合位点中的协同/拮抗突变具有重要意义。

5. **跨物种适用性**: 方法在酵母和人类TF上均有效，表明其具有跨物种的通用性，可应用于不同模式生物的TF-DNA互作研究。

6. **实验设计启示**: 本文的验证策略（in vivo训练→in vitro验证）为计算方法的验证提供了范式，即使用正交实验数据验证计算预测。

## 15 与已有知识连接

- **BPNet架构**: 本文使用BPNet（Avsec et al., 2021, Nature Genetics），该模型最初用于预测ChIP-nexus和ChIP-seq的base-resolution binding profiles。本文扩展了BPNet的应用范围，从预测到热力学参数提取。

- **DeepSHAP/DeepLIFT**: 使用DeepSHAP（Lundberg & Lee, 2017; Shrikumar et al., 2017）进行模型解释，这是深度学习可解释性的标准工具。

- **PWM/motif模型**: 本文与经典PWM模型形成对比，展示了深度学习模型在捕捉非加性效应方面的优势。PWM模型是TF-DNA结合预测的经典方法（Stormo, 2000）。

- **体外实验技术**: 本文使用BET-seq（Le et al., 2018）、MITIOMI（Maerkl & Quake, 2007）、gcPBM（Bulyk et al., 2001）等体外实验数据作为验证基准。

- **热力学模型**: 本文与TF-DNA结合的热力学模型（如Berg & von Hippel, 1987）相关，提供了一种从数据中提取热力学参数的新途径。

- **[Analysis] 可迁移方向**: 本文方法可迁移到其他蛋白质-DNA互作预测任务，如预测突变对结合亲和力的影响、设计高亲和力TF变体、理解TF家族成员间的差异结合特异性等。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**: 基于AD的TF结合位点突变效应预测平台
   - **来源局限/观察**: AD能预测序列变异对结合亲和力的影响，但未系统评估其在预测致病突变（如GWAS变异）中的表现
   - **核心假设**: AD预测的ΔΔG能准确预测致病性非编码变异对TF结合的影响
   - **初步方法**: 收集ClinVar/GWAS中位于TF结合位点的变异，用AD预测ΔΔG变化，与实验测量和致病性注释比较
   - **验证方式**: 与MPRA（Massively Parallel Reporter Assay）数据比较
   - **创新状态**: unverified

2. **候选名称**: 多TF协同结合的AD扩展
   - **来源局限/观察**: 当前AD仅处理单个TF的结合，未考虑多个TF的协同/竞争结合
   - **核心假设**: 通过修改marginalization策略，可以提取TF-TF协同结合的热力学参数
   - **初步方法**: 在背景序列中同时插入两个TF的结合位点，分析AD预测的协同效应
   - **验证方式**: 与已知的TF-TF协同结合实验数据比较
   - **创新状态**: unverified

3. **候选名称**: AD与分子动力学模拟的交叉验证
   - **来源局限/观察**: AD预测的热力学亲和力缺乏原子级别的机制解释
   - **核心假设**: AD预测的高/低亲和力序列在MD模拟中表现出相应的结合自由能差异
   - **初步方法**: 选择AD预测的极端亲和力序列，进行MD模拟计算结合自由能（如MM-PBSA），比较两种方法的一致性
   - **验证方式**: 两种方法的一致性分析
   - **创新状态**: unverified

4. **候选名称**: 基于AD的TF结合特异性重设计
   - **来源局限/观察**: AD能捕捉TF的精细结合特异性，但未用于蛋白工程
   - **核心假设**: 通过AD预测的亲和力景观，可以设计具有新结合特异性的TF变体
   - **初步方法**: 用AD预测TF突变体的结合特异性变化，筛选具有新特异性的变体，实验验证
   - **验证方式**: 体外结合实验（如EMSA、MITIOMI）
   - **创新状态**: unverified

5. **候选名称**: AD在染色质上下文中的扩展
   - **来源局限/观察**: 当前AD通过marginalization消除上下文效应，但未利用上下文信息
   - **核心假设**: 通过分析不同上下文中的AD预测差异，可以量化染色质状态对TF结合的影响
   - **初步方法**: 在不同染色质状态（开放/关闭）的细胞中训练BPNet，比较AD预测的差异
   - **验证方式**: 与ATAC-seq和ChIP-seq数据比较
   - **创新状态**: unverified