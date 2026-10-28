## 01 基本信息
- **标题**: BindVAE: Dirichlet variational autoencoders for de novo motif discovery from accessible chromatin
- **作者与单位**: Kshirsagar, Meghana; Yuan, Han; Ferres, Juan Lavista; Leslie, Christina（单位未提供）
- **期刊/预印本平台**: Genome Biology
- **年份**: 2022-08-16
- **论文类型**: 方法学（Method）
- **领域**: 调控基因组学；计算生物学；机器学习
- **关键词**: 染色质可及性；转录因子；从头基序发现；变分自编码器；Dirichlet分布
- **DOI/arXiv 号**: 10.1186/s13059-022-02723-w
- **代码**: 未提供
- **数据**: GM12878 ATAC-seq (GEO GSE477531)、A549 ATAC-seq (ENCODE ENCFF548PSN2)、HT-SELEX (Jolma et al. 2013; Yang et al. 2017)、CAP-SELEX (Jolma et al. 2015)、ChIP-seq (ENCODE GM12878)、RNA-seq (ENCODE)
- **阅读日期**: 未提供
- **在该课题方向中的位置**: 本文属于「蛋白质-DNA互作 × 深度学习」方向，聚焦于从染色质可及性数据（ATAC-seq）中无监督地从头发现TF结合基序。与常见的监督式深度模型（如DeepSEA、Basset）不同，BindVAE采用Dirichlet变分自编码器，将每个可及峰分解为多个TF结合信号的混合，直接学习可解释的k-mer分布作为基序表示。该方法为TF–DNA结合机制研究提供了一种无需已知基序库或ChIP-seq标签的从头发现途径，并可迁移至其他物种或细胞类型的可及性数据。

## 02 一句话总结
本文提出BindVAE，一种以Dirichlet分布为先验的变分自编码器，将ATAC-seq峰中k-mer计数分解为多个潜在主题（对应TF结合信号），通过HT-SELEX探针投影将潜在维度映射到具体TF，从而在无需已知基序库的情况下从头发现TF结合基序及协同结合信号。

## 03 研究问题
- **具体问题**: 如何从染色质可及性数据（ATAC-seq peaks）中无监督地、从头地发现转录因子的DNA结合基序，并进一步识别TF间的协同结合关系？
- **为什么重要**: ATAC-seq数据广泛可得（覆盖多种细胞类型、物种、疾病状态），但其中编码的TF结合信号是多种TF信号的混合。传统方法依赖已知基序库（如HOMER、MEME）进行富集分析，无法发现新基序；监督式深度模型（如DeepSEA、Basset）虽能预测可及性，但解释性差，特征归因不稳定且难以跨细胞类型泛化。从头发现基序是解析细胞类型特异性调控网络的关键步骤。
- **现有方法不足**:
  - PWMs基序库方法受限于已知基序的覆盖度，无法发现新基序或细胞类型特异性结合信号。
  - 监督式深度模型（DeepSEA、Basset）需要标签，且解释性差，特征归因（如DeepLIFT）在大输入窗口上不稳定，难以跨细胞类型泛化。
  - 传统无监督方法（如HOMER、MEME）对复杂混合信号（多个TF共占一个峰）的分解能力有限。
- **精确的"Can ... ?"研究问题**: Can an unsupervised Dirichlet variational autoencoder, trained on k-mer counts from ATAC-seq peaks, learn latent dimensions that correspond to interpretable TF binding motifs, and can these dimensions be mapped to specific TFs using HT-SELEX probe projections?

## 04 背景与发展脉络
- **阶段一：PWMs基序库匹配**（如FIMO、HOMER、MEME）
  - 优点：简单、快速、可解释性强。
  - 局限：受限于已知基序库的覆盖度，无法发现新基序；对复杂混合信号分解能力有限。
- **阶段二：k-mer监督式机器学习**（如gkm-SVM、SeqGL）
  - 优点：无需已知基序库，可捕捉更复杂的序列特征。
  - 局限：SeqGL需要标签（可及vs不可及），gkm-SVM解释性有限。
- **阶段三：深度监督模型**（如DeepSEA、Basset、DanQ、Basenji）
  - 优点：预测精度高，可捕捉长程特征。
  - 局限：解释性差，特征归因不稳定，需要大量标签数据，跨细胞类型泛化能力有限。
- **阶段四：无监督生成模型**（本文BindVAE）
  - 主张位置：利用VAE的生成框架，以Dirichlet先验强制潜在维度非负且和为1（类似主题模型），使每个潜在维度对应一个k-mer分布（即基序），实现可解释的从头基序发现。该方法无需标签，可扩展至任意细胞类型，且天然支持多TF信号分解。
- **脉络说明**: 该脉络基于本文引言与讨论部分的叙述整理，标注为「仅本文框架」，未经外部系统核验。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 已知基序库覆盖不足 | 传统方法（HOMER、MEME）只能发现库中已有的基序，无法发现新基序 | 基序库构建依赖已有的实验数据（如SELEX、ChIP-seq），对新TF或细胞类型特异性结合信号覆盖有限 | 引言部分：传统方法"confounded by the problem of redundant or missing motifs" |
| 监督模型解释性差 | DeepSEA、Basset等模型预测准确但难以提取可解释的基序信息 | 特征归因方法（如DeepLIFT）在大输入窗口上不稳定，且模型学习的是判别性特征而非生成性基序 | 引言部分：监督模型"interpretation requires attribution of the learned parameters to the output labels—which is often not a robust process" |
| 跨细胞类型泛化困难 | 监督模型在一个细胞类型上训练后难以迁移至其他细胞类型 | 模型可能学习到细胞类型特异的非TF相关特征 | 引言部分：监督模型"do not generalize across cell types" |
| 混合信号分解困难 | 一个可及峰中可能包含多个TF的结合位点，传统方法难以分解 | 可及峰是多个TF共同占据的区域，信号是混合的 | 引言部分：可及峰中"dozens of TFs occupy overlapping subsets of these peaks" |
| 从头基序发现能力不足 | 现有无监督方法（如HOMER）依赖差异富集，对低丰度TF信号不敏感 | 当TF结合位点只出现在少数峰中时，富集分析统计功效不足 | 引言部分：de novo motif discovery "can be underpowered when the sequence signal is complex" |

## 06 核心思想
1. **表面方法**: 构建一个Dirichlet变分自编码器，输入为ATAC-seq峰中k-mer（8-mer，含通配符）的计数向量，通过编码器映射到100维潜在空间，解码器从潜在表示重建k-mer计数。潜在向量服从Dirichlet先验，每个维度对应一个"主题"（k-mer分布）。训练后，用HT-SELEX探针投影到潜在空间，将每个维度映射到具体TF。

2. **核心洞察**: 
   - 将TF结合基序建模为k-mer上的多项分布（即"主题"），与主题模型（如LDA）思想一致，但用VAE框架实现，可扩展至大规模数据。
   - Dirichlet先验天然适合"混合成员"建模：每个峰是多个TF信号的混合，潜在向量各分量非负且和为1，对应各TF信号的占比。
   - 通过HT-SELEX探针投影，将无监督学习的潜在维度与具体TF关联，弥合了"数据驱动"与"生物学验证"之间的鸿沟。

3. **可能的普适教训** [Analysis]: 
   - 无监督生成模型（如VAE）可以作为一种"可解释的降维"工具，将高维序列特征分解为有生物学意义的组件，而无需监督标签。
   - 将外部实验数据（如HT-SELEX）作为"探针"来注释无监督模型的潜在空间，是一种通用的模型解释策略，可迁移至其他组学数据（如ChIP-seq、甲基化）的潜在表示分析。

## 07 方法总览
- **输入**: ATAC-seq峰（200bp窗口，以峰 summit 为中心）的k-mer计数向量。k-mer长度为8，允许最多2个连续通配符，词汇表大小D=112,800。
- **输出**: 
  1. 每个峰的100维潜在表示（Dirichlet分布参数）。
  2. 每个潜在维度的k-mer分布（解码器权重θ），可视为基序。
  3. 潜在维度到TF的映射（通过HT-SELEX探针投影）。
- **模块**:
  1. 编码器：3层全连接网络（每层300隐藏单元），将k-mer计数向量映射到Dirichlet分布参数α。
  2. 潜在层：从Dirichlet(α)采样得到z（100维）。
  3. 解码器：将z映射回k-mer分布（通过softmax），重建输入。
- **训练**: 优化ELBO（证据下界），使用Adam优化器（学习率3e-4），batch size=128，最多300,000步。使用隐式重参数化梯度（Figurnov et al. 2018）处理Dirichlet采样。
- **反馈回路**: 无显式反馈回路；训练完成后，用HT-SELEX探针做推断（前向传播），得到探针的潜在表示，通过富集分析将维度映射到TF。
- **假设**: 
  - 每个可及峰是多个TF结合信号的混合，混合比例由潜在向量z表示。
  - k-mer计数（含通配符）足以捕捉TF结合特异性。
  - HT-SELEX探针的潜在表示能反映TF的结合偏好。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| k-mer特征提取 | 将DNA序列转换为k-mer计数向量 | 将序列信息转化为固定维度的数值表示，便于神经网络处理 | 输入：200bp DNA序列；输出：D=112,800维计数向量 | Methods节"Vocabulary or input space" | 移除后模型无法处理序列输入；使用其他特征（如one-hot）会失去k-mer的语义信息 |
| 编码器（3层MLP） | 将k-mer计数映射到Dirichlet分布参数 | 实现从高维输入到低维潜在空间的非线性压缩 | 输入：k-mer计数向量；输出：100维Dirichlet参数α | Methods节"Layers" | 移除后无法获得潜在表示；减少层数可能降低表示能力 |
| Dirichlet潜在层 | 从Dirichlet(α)采样得到z | 强制潜在向量非负且和为1，使各维度可解释为"混合比例" | 输入：α；输出：z∈R^100 | Methods节"Variational autoencoders"；图1a | 替换为高斯先验会失去"混合成员"解释性 |
| 解码器（softmax） | 从z重建k-mer分布 | 将潜在表示映射回k-mer空间，实现生成式建模 | 输入：z；输出：D维k-mer概率分布 | Methods节"Variational autoencoders"；图1a | 移除后无法重建输入，模型退化为纯编码器 |
| HT-SELEX探针投影 | 将TF的SELEX探针投影到潜在空间，映射维度到TF | 为无监督学习的潜在维度提供生物学注释 | 输入：SELEX探针k-mer计数；输出：每个维度的富集p值 | Results节"Mapping the TFs to dimensions"；Algorithm 1 | 移除后潜在维度无法与具体TF关联，模型仅能发现"模式"而非"TF基序" |
| 协同结合分析 | 用CAP-SELEX探针检测潜在维度中的协同结合信号 | 验证模型能否捕获TF对协同结合这一生物学现象 | 输入：CAP-SELEX探针；输出：协同结合TF对列表 | Results节"Cooperative binding signals in GM78"；图3a-c | 移除后模型仅能发现单个TF基序，无法研究TF-TF协同互作 |

## 09 关键公式符号
1. **ELBO（证据下界）**:
   \[
   \log p_\theta(\mathbf{x}) \geq \sum_{i=1}^{N} \mathbb{E}_{q_\phi(z_i|x_i)}[\log p_\theta(x_i|z_i)] - KL(q_\phi(z_i|x_i) \| p(z_i))
   \]
   - \(x\): 输入k-mer计数向量
   - \(z\): 潜在变量（100维）
   - \(p_\theta(x|z)\): 解码器（似然函数），建模为多项分布
   - \(q_\phi(z|x)\): 编码器（变分后验），建模为Dirichlet分布
   - \(p(z)\): 先验分布，Dirichlet(α)
   - \(KL\): KL散度

2. **Dirichlet先验**:
   \[
   z_i \sim \text{Dirichlet}(\alpha)
   \]
   - \(z_i\): 第i个输入的潜在表示
   - \(\alpha\): Dirichlet分布参数（标量，所有维度共享）

3. **解码器参数**:
   \[
   \theta \in \mathbb{R}^{M \times D}, \quad M=100, D=112,800
   \]
   - \(\theta\): 解码器权重矩阵，第m行是第m个主题的k-mer分布

4. **潜在得分（Latent score）**:
   \[
   z_{ik} = \text{第i个峰在第k个主题上的得分}
   \]
   - 用于计算"可及性得分"：\(\sum_{i \in \text{all peaks}} z_{im}\)（图3d）

## 10 实验设计与证据链
- **数据集**:
  - GM12878 ATAC-seq: GEO GSE477531，76,218个可重复峰
  - A549 ATAC-seq: ENCODE ENCFF548PSN2
  - 其他细胞类型: 小鼠CD8 T细胞、人类CD8 T细胞、人类naive B细胞（男/女供体）
  - HT-SELEX: Jolma et al. 2018 (296 TFs, 325 experiments)
  - CAP-SELEX: Jolma et al. 2020 (TF对协同结合)
  - ChIP-seq: ENCODE GM12878, 82个实验（11个TF有足够重叠）
  - RNA-seq: ENCODE (GM78: ENCFF906LSJ, ENCFF630BDD; A549: ENCFF203NNS; T细胞: ENCSR336VTK4)
- **指标**: 精度（Precision）、召回率（Recall）、F1分数（用于TF检索评估）；p值（Mann-Whitney U检验，用于维度-TF映射）
- **基线**: HOMER、MEME、GADEM（与BindVAE比较）；BindVAE+Tomtom（替换映射算法）
- **评测协议**: 以RNA-seq定义的表达TF为金标准，评估各方法检索到的TF中表达TF的比例

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|------------------|------|
| 基序发现（图1c） | BindVAE能从ATAC-seq中从头发现TF基序 | 与CIS-BP数据库比对 | 发现多个已知TF基序（如RUNX3、CTCF等），平均基序宽度7.4bp | BindVAE发现的k-mer模式与已知TF结合位点一致 | 未与所有已知TF基序系统比较；未评估新基序的生物学功能 | Results节"BindVAE learns diverse k-mer binding patterns" |
| TF检索（表S4） | BindVAE在检索表达TF方面优于基线 | 与HOMER、MEME、GADEM比较 | BindVAE精度更高，但召回率和F1较低；BindVAE+Tomtom召回率和F1更高 | BindVAE发现的基序更精确但覆盖度有限；Tomtom映射可提高召回率 | 精度-召回率权衡的具体原因未深入分析 | Results节"Comparison with de novo motif discovery methods"；表S4 |
| 协同结合（图3a-c） | BindVAE能捕获TF对协同结合信号 | 用CAP-SELEX探针验证 | 发现MYBL1-MAX、FOXJ3-TBX21等协同结合对，p值显著（如2e-62） | BindVAE能学习协同结合基序 | 协同结合信号的生物学功能未验证 | Results节"Cooperative binding signals in GM78" |
| 细胞类型特异性（图3d） | BindVAE发现的TF具有细胞类型特异性 | GM78 vs A549 | 两细胞类型中TF可及性得分不同，GO富集显示细胞类型特异生物学过程 | BindVAE能捕获细胞类型特异的TF结合模式 | 未与ChIP-seq直接比较验证 | Results节"Accessibility patterns in different and similar cell types" |
| ChIP-seq验证（图4a-b） | BindVAE的潜在表示能区分不同TF的ChIP-seq峰 | 投影ChIP-seq峰到潜在空间 | UMAP显示不同TF的峰形成不同簇 | BindVAE的潜在表示具有生物学意义 | 仅定性展示，无定量指标 | Results节"Projecting ChIP-seq peaks into the latent space" |
| 重复性（表S6） | BindVAE结果在不同训练运行间稳定 | 5次重复训练 | 可及性得分标准差较小 | BindVAE训练稳定 | 未评估不同超参数下的稳定性 | Results节"Accessibility patterns in different and similar cell types" |

## 11 结论正确解读
- **任务范围**: 本文任务是从ATAC-seq峰中无监督发现TF结合基序，并映射到具体TF。该任务限定于"可及染色质区域"内的序列信号，不涉及不可及区域的TF结合预测。
- **Oracle/真值输入**: 无监督训练不使用任何标签；TF映射使用HT-SELEX体外结合数据作为"探针"，ChIP-seq仅用于验证。HT-SELEX数据本身是体外实验，可能不完全反映体内结合情况。
- **端到端状态**: 方法端到端可运行（从ATAC-seq峰到TF基序），但TF映射步骤依赖外部HT-SELEX数据，并非完全从头。
- **算力成本**: 单GPU训练4-5小时（300,000步），推断50,000个样本约1分钟。成本适中，可扩展。
- **历史数据依赖**: 依赖ATAC-seq峰的质量和数量；HT-SELEX数据覆盖的TF集合有限（296个），未覆盖的TF无法被映射。
- **模型依赖**: 结果依赖k-mer长度（8）、通配符数量（2）、潜在维度数（M=100）、Dirichlet先验α等超参数。作者未系统评估所有超参数的影响。
- **最难情形**: 长基序（>10bp）被拆分到多个维度；旁系同源TF因基序相似难以区分；低表达或低可及性TF的信号可能被噪声淹没。
- **群体/领域边界**: 方法在人类细胞系（GM78、A549）和部分免疫细胞中验证；未在疾病样本、其他物种或单细胞数据中系统评估。
- **不确定性**: 作者承认训练存在随机性（5次重复实验），但未提供置信区间或统计检验。

**有边界的复述**: BindVAE能够在ATAC-seq峰中无监督地发现与已知TF基序一致的k-mer模式，并通过HT-SELEX探针映射到具体TF；在精度上优于HOMER等传统方法，但召回率较低；能捕获细胞类型特异性和协同结合信号。这些结论仅限于测试的细胞类型和HT-SELEX覆盖的TF集合。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 长基序拆分 | 长基序（如CTCF）被拆分到多个潜在维度 | 使用更长k-mer或增加通配符 | Results节"Motifs discovered de novo by our model" |
| 旁系同源TF难以区分 | 基序相似的TF家族成员映射到同一维度 | 结合更精细的SELEX数据或表达信息 | Results节"Mapping the TFs to dimensions" |
| 召回率较低 | 相比HOMER，BindVAE发现的TF数量较少 | 使用Tomtom替代Algorithm 1可提高召回率 | Results节"Comparison with de novo motif discovery methods" |
| 依赖HT-SELEX数据 | TF映射受限于SELEX实验覆盖的TF集合 | 扩展SELEX数据覆盖范围 | Results节"Mapping the TFs to dimensions" |
| 未利用可及性定量信息 | 模型仅使用峰内k-mer计数，未使用峰的强度/可及性水平 | 将可及性水平作为输入特征 | 讨论部分 |
| 未建模TF-TF互作 | 协同结合分析依赖外部CAP-SELEX数据，模型本身不直接学习互作 | 扩展模型以直接学习TF对联合分布 | 讨论部分 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| 精度-召回率权衡未深入分析 | Algorithm 1可能偏向高置信度但覆盖度低的映射；Tomtom提高召回率但可能引入假阳性 | 影响方法在实际应用中的可用性 | 系统变化p值阈值，绘制PR曲线 | 表S4 |
| 基序宽度偏短（平均7.4bp） | 8-mer+通配符表示可能无法捕捉长基序或结构化基序（如锌指蛋白的间隔基序） | 长基序TF（如CTCF、ZNF家族）在调控中重要 | 与CIS-BP中长基序TF的检出率比较 | 图1c |
| 未与监督式深度模型（如DeepSEA）比较 | 监督模型在预测任务上可能更优，BindVAE的优势仅在无监督场景 | 需明确方法适用场景 | 在相同数据集上比较基序发现质量 | 讨论部分 |
| 协同结合分析依赖CAP-SELEX | CAP-SELEX数据本身有限，可能遗漏真实存在的协同结合对 | 协同结合是调控重要机制，需更全面验证 | 用ChIP-seq共定位数据交叉验证 | 图3a-c |
| 未评估单细胞数据 | scATAC-seq数据噪声更大、峰更稀疏，方法可能不适用 | 单细胞数据是当前调控基因组学重要方向 | 在scATAC-seq数据上测试 | 未提供 |
| 未与其他无监督方法（如LDA、NMF）比较 | 主题模型方法可能更简单且效果相当 | 需证明VAE框架的增量价值 | 与LDA/NMF在相同数据上比较 | 未提供 |

## 14 学到什么
**Agent 提炼的知识候选**:
1. **Dirichlet先验作为"混合成员"建模工具**: 在TF–DNA互作研究中，一个可及峰往往包含多个TF的结合信号。Dirichlet分布天然适合建模"混合比例"，可迁移至其他需要分解混合信号的场景（如ChIP-seq峰中多个TF共占、增强子中多个TF协同）。
2. **外部数据作为"探针"注释潜在空间**: 用HT-SELEX体外结合数据投影到无监督模型的潜在空间，为每个维度赋予生物学注释。这一策略可推广至其他无监督组学模型（如scRNA-seq的VAE潜在空间用已知标记基因注释）。
3. **k-mer+通配符的序列表示**: 使用8-mer（含通配符）而非one-hot编码，在保持计算可行性的同时捕捉序列简并性。该表示可迁移至其他序列模型（如预测TF结合位点的CNN）。
4. **无监督方法作为监督方法的补充**: BindVAE无需标签即可发现基序，适用于缺乏ChIP-seq数据的细胞类型或物种。在课题中，可将其作为"基序发现"的第一步，再用监督方法精炼。
5. **协同结合信号的检测**: 通过CAP-SELEX探针投影，BindVAE能发现TF对协同结合基序。这提示在TF–DNA互作研究中，不仅关注单个TF，还应关注TF对或TF组合的联合结合模式。

## 15 与已有知识连接
- **与主题模型（LDA）的关联**: BindVAE的"主题-词语"结构与LDA类似，但用VAE替代了吉布斯采样，可扩展至更大数据集。LDA在文本建模中的"文档-主题-词语"层次对应BindVAE的"峰-主题-k-mer"层次。
- **与gkm-SVM的关联**: 本文k-mer+通配符表示与gkm-SVM的gapped k-mer特征一致，但BindVAE将其用于生成模型而非判别模型。
- **与DeepSEA/Basset的关联**: 这些监督模型预测可及性/调控功能，BindVAE则无监督学习可及性峰内的序列结构。两者互补：BindVAE可提供可解释的基序，DeepSEA可提供预测能力。
- **与HT-SELEX/CAP-SELEX实验的关联**: 本文依赖这些体外实验数据作为验证和映射工具。在课题中，可考虑使用更新的SELEX数据集（如Methyl-SELEX、ChIP-exo）扩展TF覆盖范围。
- **与TF–DNA结合机制研究的关联**: 本文发现的基序和协同结合信号可直接用于构建TF结合模型（如PWM、CNN评分器），或与结构预测（如AlphaFold、RoseTTAFold）结合，研究TF如何识别其结合位点。

## 16 研究想法
**Agent 生成的研究候选**:

1. **候选名称**: BindVAE-3D：将Dirichlet VAE与结构预测结合的TF–DNA协同结合建模
   - **来源局限/观察**: BindVAE能发现协同结合基序，但无法解释TF如何物理互作并结合DNA。
   - **核心假设**: 协同结合基序的空间排列（间距、方向）与TF-TF物理互作界面相关。
   - **初步方法**: 用BindVAE发现协同结合基序对，提取基序间距和方向；用AlphaFold预测TF-TF复合物结构；关联基序几何特征与结构互作界面。
   - **验证方式**: 与已知TF-TF共晶体结构比较；用突变实验验证预测的互作界面。
   - **创新状态**: unverified

2. **候选名称**: scBindVAE：面向单细胞ATAC-seq的稀疏Dirichlet VAE
   - **来源局限/观察**: BindVAE在bulk ATAC-seq上验证，但scATAC-seq数据更稀疏、噪声更大，且细胞异质性需要建模。
   - **核心假设**: 在单细胞水平引入细胞类型标签作为条件变量，可提高基序发现的灵敏度和细胞类型特异性。
   - **初步方法**: 在BindVAE基础上引入条件VAE（CVAE）框架，以细胞类型为条件；使用稀疏化技术处理dropout；在scATAC-seq数据上评估基序发现质量。
   - **验证方式**: 与bulk ATAC-seq结果比较；用已知细胞类型标记TF验证。
   - **创新状态**: unverified

3. **候选名称**: BindVAE-Express：整合可及性与表达数据的TF活性推断
   - **来源局限/观察**: BindVAE仅使用序列信息，未利用可及性水平和基因表达数据。
   - **核心假设**: 将ATAC-seq峰的强度（可及性水平）和下游基因表达作为额外输入，可更准确推断TF活性。
   - **初步方法**: 扩展BindVAE为多模态VAE，同时输入k-mer计数、峰强度和靶基因表达；在潜在空间中引入TF活性得分。
   - **验证方式**: 与TF表达数据比较；用TF敲低/过表达实验验证。
   - **创新状态**: unverified

4. **候选名称**: BindVAE-MotifDB：从ATAC-seq中构建细胞类型特异性TF基序数据库
   - **来源局限/观察**: BindVAE发现的基序与CIS-BF一致，但未系统构建数据库。
   - **核心假设**: 在多种细胞类型上训练BindVAE，可构建覆盖更广、细胞类型特异的TF基序数据库。
   - **初步方法**: 在ENCODE的多个细胞类型ATAC-seq数据上训练BindVAE，统一映射到TF；构建数据库并评估覆盖度和特异性。
   - **验证方式**: 与CIS-BP、JASPAR数据库比较；用ChIP-seq数据验证。
   - **创新状态**: unverified

5. **候选名称**: BindVAE-Phys：将物理模拟（MD/对接）与BindVAE基序结合的TF结合自由能预测
   - **来源局限/观察**: BindVAE提供基序但无法预测结合强度。
   - **核心假设**: BindVAE基序可作为MD模拟的初始结合位点，提高结合自由能预测精度。
   - **初步方法**: 用BindVAE基序定位TF结合位点；用MD模拟或分子对接计算结合自由能；与实验结合亲和力数据比较。
   - **验证方式**: 与SPR/ITC实验数据比较；用已知突变体验证。
   - **创新状态**: unverified