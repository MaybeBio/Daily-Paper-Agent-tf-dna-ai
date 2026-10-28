## 01 基本信息

- **标题**：Deep learning approaches for noncoding variant prioritization in neurodegenerative diseases
- **作者与单位**：Lan, Alexander Y; Corces, M Ryan（Gladstone Institutes，美国加州旧金山）
- **期刊/预印本平台**：Frontiers in Aging Neuroscience
- **年份**：2022-12-06
- **论文类型**：综述（Review）
- **领域**：神经退行性疾病基因组学 × 深度学习（非编码变异优先级排序）
- **关键词**：deep learning, noncoding variant prioritization, neurodegenerative diseases, Alzheimer's disease, transcription factor binding, chromatin accessibility, gene expression, 3D chromatin interaction
- **DOI/arXiv 号**：10.3389/fnagi.2022.1027224
- **代码**：未提供
- **数据**：未提供（综述性论文，无原始数据）
- **阅读日期**：2026-05-13（按当前日期）
- **在该课题方向中的位置**：本文是连接「TF–DNA 结合机制」与「深度学习变异效应预测」的桥梁性综述。核心逻辑链为：非编码变异 → 影响 TF 结合（cis-regulatory code）→ 改变染色质状态/基因表达 → 导致神经退行性疾病。文中系统梳理了从 DeepBind/DeepSEA/Basset 到 Basenji/Enformer/Akita/Orca 的模型谱系，并重点讨论了 TF 结合 motif 的发现、细胞类型特异性建模、以及变异效应预测的验证策略，对「TF–DNA 互作 × AI」课题提供了完整的方法论地图。

---

## 02 一句话总结

本文系统综述了深度学习在神经退行性疾病非编码变异优先级排序中的应用，核心逻辑是：以 DNA 序列为输入，通过 CNN/Transformer 等架构学习 TF 结合、染色质可及性、基因表达和 3D 染色质互作等调控特征，利用等位基因差异评分（如 ISM）预测非编码变异的调控功能影响，从而从 GWAS 关联位点中筛选候选因果变异。

---

## 03 研究问题

- **具体问题**：如何从 GWAS 鉴定的大量非编码风险变异中，优先排序并识别真正具有调控功能（影响 TF 结合、染色质状态、基因表达）的因果变异？
- **为什么重要**：>90% 的 GWAS 变异位于非编码区，功能注释困难；AD 等神经退行性疾病遗传度（60–80%）高，但因果变异和机制不清，阻碍了药物靶点发现和患者分层。
- **现有方法不足**：
  - 传统 ML 依赖手工特征工程，耗时且特征选择敏感；
  - 连锁不平衡使 GWAS 关联变异难以区分因果与非因果；
  - 非编码变异的功能效应缺乏「遗传密码」级别的理解；
  - 脑组织细胞类型高度异质，需要细胞类型特异性的建模。
- **精确的「Can ... ?」问题**：Can deep learning models trained on DNA sequence predict the functional impact of noncoding variants on TF binding and gene regulation in disease-relevant brain cell types, thereby prioritizing causal variants from GWAS loci in neurodegenerative diseases?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注「仅本文框架」；部分模型信息经外部知识核验。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文主张的位置 |
|------|-----------|------|------|---------------|
| 前深度学习时代 | gkm-SVM + deltaSVM | 可解释、计算高效、能捕捉 gapped k-mer 特征 | 手工特征、无法捕捉长程依赖、扩展性有限 | 作为 DL 的基线对照 |
| 早期 CNN（2015-2016） | DeepBind、DeepSEA、Basset | 首次证明 CNN 可从序列预测 TF 结合/染色质特征；DeepSEA 多任务学习 919 个特征 | 输入长度短（≤1kb）、输出为二值/粗粒度、缺乏定量分辨率 | 奠定「序列→调控特征」范式 |
| 长程+定量模型（2018-2022） | Basenji/Basenji2、BPNet、Sei | Basenji 输入~131kb、128bp 分辨率定量预测；BPNet 碱基分辨率；Sei 4kb 输入、21,907 个 cis-regulatory 谱 | 计算成本高、训练数据需求大 | 代表当前 SOTA 的序列→调控建模 |
| Transformer 时代（2021-） | Enformer、DNABERT | Enformer 注意力机制实现~100kb 长程互作建模；DNABERT 预训练+微调范式 | 计算资源需求极高、可解释性挑战 | 未来方向，尚未在神经退行性疾病中充分应用 |
| 3D 染色质建模 | Akita、DeepC、Orca | 从序列直接预测 Hi-C 接触图；Orca 多分辨率（4kb-1Mb） | 需要大量 Hi-C 数据、变异效应验证困难 | 补充 TF 结合模型无法捕捉的远程调控信息 |

**本文主张的位置**：DL 方法已从「预测 TF 结合」扩展到「预测基因表达、3D 染色质互作」等多层次调控特征，但在神经退行性疾病中的应用仍处于早期阶段，需要结合细胞类型特异性数据和功能验证。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 非编码变异功能注释困难 | >90% GWAS 变异位于非编码区，难以直接推断功能 | 缺乏对 cis-regulatory code 的完整理解；非编码变异效应通常微弱且依赖细胞类型/状态 | Introduction 第 2-3 段 |
| 连锁不平衡（LD）干扰因果变异识别 | 同一 LD block 内多个变异统计上不可区分 | 等位基因共分离导致无法仅凭统计关联确定因果变异 | Introduction 第 2 段；Noncoding variant prediction 节 |
| 传统 ML 特征工程瓶颈 | 手工特征选择耗时、敏感、难以泛化 | 基因组数据高维复杂，先验知识不完整 | Introduction 第 4 段 |
| 细胞类型特异性不足 | 脑组织异质性高，全组织数据掩盖细胞类型特异效应 | 不同细胞类型（神经元、小胶质细胞等）调控景观差异大 | Genomic applications 节「细胞类型特异性」段落 |
| 数据稀缺 | 特定脑细胞类型的 TF 结合/染色质数据有限 | 难以获得足够数量的高质量 ChIP-seq/ATAC-seq 数据 | Current limitations 节 |
| 模型可解释性不足 | DL「黑箱」问题限制生物学机制提取 | 多层非线性变换使特征归因困难 | Model interpretability 节 |
| 功能验证瓶颈 | DL 预测的变异缺乏高通量实验验证手段 | 单变异验证成本高、通量低；MPRA 缺乏正确基因组背景 | Discussion 节 |

---

## 06 核心思想

### 1) 表面方法
- 综述了从早期 CNN（DeepBind、DeepSEA、Basset）到现代架构（Basenji、Enformer、BPNet、Sei、Akita、DeepC、Orca）的深度学习模型谱系
- 核心流程：one-hot 编码 DNA 序列 → CNN/Transformer 特征提取 → 预测调控特征（TF 结合、染色质可及性、基因表达、3D 互作）→ ISM/梯度方法计算变异效应评分 → 变异优先级排序
- 在神经退行性疾病中的应用：gkm-SVM 用于 AD/PD 脑细胞类型 ATAC-seq 分析；DeepSEA/SpliceAI 用于 AD GWAS 变异功能注释

### 2) 核心洞察
- **序列即调控密码**：DNA 序列本身编码了足够的调控信息，DL 模型可以从序列直接预测多种调控特征，无需手工特征
- **等位基因差异评分**：通过比较参考/替代等位基因的预测差异来评估变异功能效应，将「预测」转化为「变异优先级排序」
- **细胞类型特异性是关键**：神经退行性疾病的调控效应高度依赖细胞类型，需要匹配的细胞类型数据训练模型
- **多层次建模互补**：TF 结合、染色质可及性、基因表达、3D 互作是不同层次的调控信息，组合使用可提高变异排序准确性

### 3) 可能的普适教训 [Analysis]
- **模型架构选择应匹配生物学问题的尺度**：短程 TF 结合用短输入 CNN 即可，长程增强子-启动子互作需要 Transformer 或 dilated CNN——这提示在 TF–DNA 互作研究中，应根据目标互作的距离尺度选择模型
- **训练数据的「匹配性」比模型复杂度更重要**：DeepMEL2 的成功关键在于使用匹配的黑色素瘤细胞系数据，而非更复杂的架构——对 TF–DNA 互作研究，应优先获取目标细胞类型/状态的 ChIP-seq/ATAC-seq 数据
- **可解释性方法应与模型同步设计**：BPNet 的碱基分辨率输出 + DeepLIFT 归因是「可解释性优先」的设计范例，而非事后补救

---

## 07 方法总览

- **输入**：one-hot 编码的 DNA 序列（长度从 101bp 到 1Mb 不等，取决于模型）
- **输出**：调控特征预测——TF 结合概率/强度、染色质可及性、基因表达水平、组蛋白修饰、3D 染色质互作概率等
- **核心模块**：
  1. 嵌入层：one-hot 编码或 k-mer tokenization（DNABERT）
  2. 特征提取层：CNN（卷积+池化）、dilated CNN（Basenji）、Transformer 注意力层（Enformer）、CNN+双向 LSTM（DeepMEL2）
  3. 预测头：全连接层 + 适当的激活函数（sigmoid 用于二分类、线性用于定量预测）
  4. 多任务头：共享 trunk + 独立输出分支（DeepSEA、Basenji）
- **训练**：监督学习，以实验数据（ChIP-seq peaks、ATAC-seq 信号、RNA-seq 表达等）为标签；损失函数为二值交叉熵（分类）或 Poisson/MSE（定量）
- **变异效应评分**：ISM（分别输入参考/替代等位基因序列，比较预测差异）、saliency maps、DeepLIFT/DeepSHAP 归因
- **验证**：QTL 重现（eQTL、caQTL、sQTL）、MPRA 数据、CRISPR 实验
- **反馈回路**：模型预测 → 功能验证 → 改进训练数据/模型

**文字流程**：
1. 从 GWAS 获得风险位点 → 提取 LD block 内所有候选变异
2. 对每个变异，构建参考/替代等位基因的 DNA 序列（通常以变异为中心 ± 数百 bp）
3. 输入训练好的 DL 模型，获得两种等位基因的调控特征预测
4. 计算预测差异（如 Δbinding score），作为变异功能效应评分
5. 结合其他注释（如染色质状态、eQTL 共定位）进行优先级排序
6. 对 top 变异进行实验验证（MPRA、CRISPR、报告基因等）

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| One-hot 编码 | 将 DNA 序列转为数值矩阵 | DL 模型需要数值输入；保留碱基位置信息 | 输入：DNA 序列字符串；输出：4×N 二值矩阵 | Methods/Deep learning 节 | 无法直接使用序列信息，模型不可训练 |
| 卷积层（motif 检测） | 扫描序列中的局部模式，相当于学习 TF binding motif | TF 结合具有短程序列特异性，卷积核可视为 motif 检测器 | 输入：one-hot 矩阵；输出：特征图 | DeepBind/DeepSEA 的 kernel 分析与 PWMs 匹配（Genomic applications 节） | 模型失去局部序列模式识别能力，TF 结合预测性能大幅下降 |
| Dilated 卷积（Basenji） | 扩大感受野，捕捉长程调控信息 | 增强子-启动子互作可达数十 kb，需要长程上下文 | 输入：~131kb 序列；输出：128bp 分辨率预测 | Basenji 优于 Basset 的长程预测表现（Genomic applications 节） | 无法捕捉 >1kb 的远程调控信息，变异效应预测精度下降 |
| 多任务学习头 | 同时预测多个细胞类型/多个调控特征 | 共享特征提取，提高数据效率；捕捉跨细胞类型共享的调控规则 | 输入：共享 trunk 特征；输出：多任务预测 | DeepSEA 919 任务、Basenji 多细胞类型预测（Genomic applications 节） | 单任务模型在小样本细胞类型上性能下降，泛化能力减弱 |
| Transformer 注意力层（Enformer） | 计算序列任意位置间的依赖关系 | 远程调控互作不依赖线性距离，注意力机制直接建模全局依赖 | 输入：序列嵌入；输出：注意力加权特征 | Enformer 在 eQTL 和 MPRA 变异预测上优于 Basenji2（Genomic applications 节） | 长程互作建模能力下降，增强子-启动子关联预测受损 |
| ISM 变异效应评分 | 通过等位基因替换计算预测差异 | 将模型从「预测器」转化为「变异效应评估器」 | 输入：参考/替代等位基因序列；输出：Δ预测值 | 多个模型使用 ISM 进行变异优先级排序（Noncoding variant prediction 节） | 无法评估变异功能效应，模型仅能预测而不能排序 |
| DeepLIFT/DeepSHAP 归因 | 计算每个碱基对预测的贡献 | 识别关键碱基和 motif，提高可解释性 | 输入：序列+模型；输出：碱基级重要性分数 | BPNet 使用 DeepLIFT 发现 motif 语法（Model interpretability 节） | 模型可解释性下降，难以从预测回溯到生物学机制 |

> 注：以上「移除后的影响」多为预期效应（基于模型设计逻辑），非原文实测消融数据。原文未提供系统性消融实验结果。

---

## 09 关键公式符号

本文为综述，未给出具体模型公式。以下为文中隐含的核心概念公式化表达：

**1. 序列预测模型的一般形式：**
$$y = f_{\theta}(X_{onehot})$$

- $X_{onehot} \in \{0,1\}^{4 \times L}$：one-hot 编码的 DNA 序列，L 为序列长度
- $f_{\theta}$：深度神经网络（CNN/Transformer），θ 为可学习参数
- $y$：调控特征预测（TF 结合概率、染色质可及性分数等）

**2. ISM 变异效应评分：**
$$\Delta_{ISM} = f_{\theta}(X_{alt}) - f_{\theta}(X_{ref})$$

- $X_{ref}$：参考等位基因序列
- $X_{alt}$：替代等位基因序列（仅变异位点碱基不同）
- $\Delta_{ISM}$：变异导致的预测调控特征变化，正值表示增强结合/可及性，负值表示减弱

**3. 多任务学习损失函数（概念性）：**
$$\mathcal{L} = \sum_{t=1}^{T} w_t \cdot \mathcal{L}_t(y_t, \hat{y}_t)$$

- $T$：任务数（如不同细胞类型或不同调控特征）
- $w_t$：任务权重
- $\mathcal{L}_t$：第 t 个任务的损失（如 BCE 或 Poisson loss）

**4. 梯度归因（saliency）：**
$$S_i = \left| \frac{\partial y}{\partial X_i} \right|$$

- $S_i$：第 i 个碱基位置的重要性分数
- 用于识别对预测贡献最大的序列位置

---

## 10 实验设计与证据链

> 本文为综述，无原始实验。以下为文中引用的代表性研究及其验证策略。

**数据集/群体**：
- 文中提及的数据资源：ENCODE、Roadmap Epigenomics、Human Cell Atlas、Allen Brain Atlas 等公共数据库（Current limitations 节）
- AD 相关 GWAS 数据：文中提及 Bellenguez et al. 2022、de Rojas et al. 2021、Wightman et al. 2021 等近期 AD GWAS（Introduction 节）
- 脑细胞类型数据：snATAC-seq 24 个聚类（Corces et al. 2020，AD/PD 研究）

**指标**：
- 分类任务：AUROC、AUPRC
- 回归任务：Pearson/Spearman 相关系数
- 变异效应验证：eQTL 重现率、MPRA 一致性

**基线**：
- gkm-SVM（deltaSVM）作为传统 ML 基线
- 各模型与 DeepSEA/Basset 等早期 DL 模型对比

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-----------------|------|
| DeepBind 预测 TF 结合 | CNN 可从序列预测 TF-RNA 结合 | 与 gkm-SVM 等非 DL 方法对比 | 在多个 ChIP-seq 数据集上优于非 DL 方法 | CNN 能有效学习 TF 结合特异性 | 未证明在神经退行性疾病变异上的适用性 | Genomic applications 节 |
| DeepSEA 多任务预测 | 多任务学习可同时预测 919 个调控特征 | 单任务 vs 多任务 | 多任务提升泛化性能 | 共享特征提取有利于小样本任务 | 未直接验证疾病变异 | Genomic applications 节 |
| Basenji 长程预测 | dilated CNN 可捕捉长程调控信息 | 与 Basset（短输入）对比 | 在长程调控预测上优于 Basset | 长输入+ dilated 卷积可建模远程互作 | 未在神经退行性疾病中验证 | Genomic applications 节 |
| Enformer 注意力建模 | Transformer 可提升远程调控预测 | 与 Basenji2 对比 | 在 eQTL 和 MPRA 变异预测上优于 Basenji2 | 注意力机制优于固定感受野的 CNN | 计算成本高，难以广泛应用 | Genomic applications 节 |
| gkm-SVM 用于 AD/PD snATAC-seq | ML 可识别脑细胞类型特异的功能变异 | 24 个 snATAC-seq 聚类 | 识别出细胞类型特异的调控变异 | 细胞类型特异性建模对神经退行性疾病重要 | gkm-SVM 性能可能不如 DL | Genomic applications 节 |
| DeepSEA/SpliceAI 用于 AD GWAS | DL 评分可辅助 AD 变异优先级排序 | 与仅统计关联对比 | 识别出影响 TF 结合/剪接的候选变异 | DL 评分可补充统计关联分析 | 缺乏系统性实验验证 | Noncoding variant prediction 节 |

---

## 11 结论正确解读

- **任务范围**：本文是综述，不提出新模型，而是系统梳理 DL 在非编码变异优先级排序中的方法论。结论是「DL 方法在该任务中具有巨大潜力，但应用仍处于早期阶段」。
- **oracle/真值输入**：文中讨论的模型均以实验数据（ChIP-seq、ATAC-seq、RNA-seq 等）为监督信号，变异效应通过 ISM 等事后方法计算，而非直接训练于变异标签。
- **端到端状态**：当前流程并非端到端——GWAS 先筛选位点 → DL 模型评分 → 实验验证，各步骤独立。
- **算力成本**：文中指出 Enformer 等大模型计算成本高（Current limitations 节），但未给出具体数值。
- **历史数据依赖**：模型性能依赖训练数据的细胞类型/状态匹配度；神经退行性疾病中匹配数据稀缺。
- **最难情形**：罕见变异（缺乏统计功效）、非编码区域功能未知、细胞类型特异性效应、多变异协同效应。
- **群体/领域边界**：结论主要基于 AD 研究，对其他神经退行性疾病（PD、ALS）的适用性为推断性。
- **不确定性**：DL 预测的变异效应缺乏系统性功能验证；模型预测与真实调控机制之间的因果关系未确立。

**有边界的复述**：在 2022 年时间点，深度学习模型（CNN/Transformer）已能在多种细胞类型中从 DNA 序列预测 TF 结合、染色质可及性和基因表达等调控特征，并通过等位基因差异评分辅助非编码变异优先级排序；在 AD 研究中，这些方法已初步应用于 GWAS 位点的功能注释，但受限于数据稀缺、验证不足和计算成本，尚未成为标准流程。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 数据稀缺 | 特定脑细胞类型的调控数据不足，限制模型训练 | 利用单细胞测序技术（snATAC-seq、snRNA-seq）生成更多细胞类型特异数据 | Current limitations 节 |
| 数据划分不当 | 训练/测试集划分不当可能导致性能高估 | 采用严格的染色体划分策略 | Current limitations 节 |
| 功能验证不足 | DL 预测缺乏系统性实验验证 | 结合 MPRA、CRISPR 等高通量验证方法 | Discussion 节 |
| 罕见变异处理困难 | 罕见变异缺乏统计功效，DL 难以学习 | 结合家族研究和功能实验 | Discussion 节 |
| 计算成本高 | 大模型（如 Enformer）训练和推理成本高 | 开发更高效的模型架构和推理方法 | Current limitations 节 |
| 可解释性挑战 | DL「黑箱」限制生物学机制提取 | 改进归因方法，结合 motif 分析 | Model interpretability 节 |
| 多组学整合不足 | 单一模型难以整合多种数据类型 | 开发多模态、多任务学习框架 | Future directions 节 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 综述偏向 CNN 架构，对 Transformer 讨论相对有限 | 截至 2022 年，Transformer 在基因组学的应用刚起步；但 Enformer 已展示优势 | 可能低估 Transformer 在长程调控建模中的潜力 | 追踪 2022 年后文献，比较 CNN vs Transformer 在相同基准上的表现 | Genomic applications 节对 Enformer 的讨论篇幅有限 |
| 对「预测差异 = 功能效应」的假设未充分质疑 | ISM 分数高并不必然意味着生物学功能改变；预测差异可能来自模型伪影 | 变异优先级排序的可靠性取决于该假设的成立 | 系统比较 ISM 分数与实验验证（MPRA、CRISPR）的一致性 | Noncoding variant prediction 节 |
| 对 gkm-SVM 与 DL 的比较不够系统 | 文中提到 DL 优于 gkm-SVM，但未讨论具体任务和数据集差异 | 不同任务上传统方法可能仍有竞争力 | 在统一基准上系统比较 gkm-SVM vs DL | Genomic applications 节 |
| 对细胞类型特异性的讨论停留在概念层面 | 未深入讨论如何选择/整合细胞类型数据，以及细胞类型间调控差异的程度 | 细胞类型特异性是神经退行性疾病研究的关键 | 比较全组织 vs 单细胞类型训练的模型在变异预测上的差异 | Genomic applications 节「细胞类型特异性」段落 |
| 对模型验证策略的讨论不够深入 | 仅提及 QTL 和 MPRA 验证，未讨论验证的局限性和偏差 | 验证方法的选择直接影响结论可靠性 | 分析不同验证策略（eQTL vs MPRA vs CRISPR）的一致性和互补性 | Noncoding variant prediction 节 |
| 对「罕见变异」的讨论过于简略 | 仅提及统计功效问题，未讨论 DL 在罕见变异上的特殊挑战 | 罕见变异是神经退行性疾病的重要研究方向 | 评估 DL 模型在常见 vs 罕见变异上的预测性能差异 | Discussion 节 |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **「序列 → 调控特征 → 变异效应」的三层范式**：这是 TF–DNA 互作 × AI 研究的核心方法论框架。可迁移到本课题：先训练序列→TF 结合模型，再通过等位基因替换计算变异效应，最后用实验验证。

2. **多任务学习是应对细胞类型异质性的有效策略**：共享 trunk + 多任务头的设计（DeepSEA、Basenji）可同时预测多种细胞类型的调控特征，提高数据效率。对 TF–DNA 互作研究，可同时预测多种 TF 的结合谱，捕捉 TF 间的协同/竞争关系。

3. **输入长度与模型架构的匹配原则**：短程 TF 结合（~100bp）用简单 CNN 即可；长程调控（>10kb）需要 dilated CNN 或 Transformer。这提示在设计 TF–DNA 互作模型时，应根据目标互作的距离尺度选择架构。

4. **可解释性方法应与模型设计同步**：BPNet 的碱基分辨率输出 + DeepLIFT 归因是「可解释性优先」的设计范例。对 TF–DNA 互作研究，碱基级归因可直接揭示 TF 结合 motif 和关键碱基，是连接预测与机制的关键桥梁。

5. **训练数据的「匹配性」比模型复杂度更重要**：DeepMEL2 的成功关键在于使用匹配的黑色素瘤细胞系数据。对 TF–DNA 互作研究，应优先获取目标细胞类型/状态的 ChIP-seq 数据，而非依赖通用模型。

6. **ISM 是变异效应评估的通用工具**：通过比较参考/替代等位基因的预测差异，将模型从「预测器」转化为「变异评估器」。可迁移到 TF–DNA 互作研究：评估 SNP 对 TF 结合的影响，预测疾病相关变异的调控功能。

7. **3D 染色质互作是 TF–DNA 结合的重要补充维度**：Akita/DeepC/Orca 从序列预测 Hi-C 接触图，提示 TF 结合效应可能通过染色质构象变化传递。可探索将 TF 结合模型与 3D 基因组模型串联，实现更完整的调控效应预测。

8. **验证策略的层次性**：QTL（统计关联）→ MPRA（体外功能）→ CRISPR/单碱基编辑（体内功能），验证强度递增。TF–DNA 互作研究应建立类似的层次化验证体系。

---

## 15 与已有知识连接

- **DeepBind (Alipanahi et al., 2015)**：CNN 预测 TF 结合的先驱工作，本文作为早期实现详细介绍。与本课题直接相关——TF–DNA 结合预测的奠基性方法。
- **DeepSEA (Zhou & Troyanskaya, 2015)**：多任务 CNN 预测 919 个调控特征，本文重点讨论。其「序列→染色质特征→变异效应」范式是 TF–DNA 互作 × AI 的核心框架。
- **Basset (Kelley et al., 2016)**：CNN 预测染色质可及性，本文作为早期三篇奠基工作之一。可迁移到 TF 结合位点的可及性预测。
- **Basenji (Kelley et al., 2018)**：dilated CNN 实现长程调控预测，本文重点讨论。对 TF–DNA 互作研究，提供了捕捉远程增强子-启动子互作的方法。
- **Enformer (Avsec et al., 2021a)**：Transformer 架构实现 100kb 长程调控预测，本文作为 SOTA 讨论。代表 TF–DNA 互作建模的前沿方向。
- **BPNet (Avsec et al., 2021b)**：碱基分辨率 TF 结合预测 + DeepLIFT 归因，本文重点讨论。对 TF–DNA 互作研究提供了 motif 发现和碱基级归因的范例。
- **gkm-SVM/deltaSVM (Lee et al., 2015)**：传统 ML 基线，本文用于对比。在 TF–DNA 互作研究中仍可作为轻量级基线。
- **Corces et al. (2020)**：snATAC-seq 用于 AD/PD 脑细胞类型调控景观分析，本文引用。提供了神经退行性疾病中 TF–DNA 互作的细胞类型特异性数据资源。
- **Schwartzentruber et al. (2021)**：AD GWAS 变异 meta 分析，使用 DeepSEA 等功能评分。展示了 TF–DNA 互作模型在疾病变异优先级排序中的实际应用。
- **ENCODE/Roadmap Epigenomics**：本文提及的公共数据资源，是训练 TF–DNA 互作模型的主要数据来源。
- **JASPAR 数据库**：本文提及用于初始化 DeepMEL2 卷积核的 TF motif 数据库，是 TF–DNA 互作研究的核心参考资源。

---

## 16 研究想法

> **Agent 生成的研究候选**

### 候选 1：神经退行性疾病脑细胞类型特异的 TF–DNA 结合预测模型
- **名称**：BrainCell-TFBind
- **来源局限/观察**：现有 TF 结合预测模型（DeepSEA、Basenji）主要基于通用细胞系数据，缺乏神经退行性疾病相关脑细胞类型（小胶质细胞、星形胶质细胞等）的特异性建模
- **核心假设**：脑细胞类型特异的 TF 结合模型能比通用模型更准确地预测 AD/PD 相关非编码变异的调控效应
- **增量**：利用 snATAC-seq/snRNA-seq 数据训练细胞类型特异的 TF 结合模型，并与通用模型对比变异预测性能
- **初步方法**：收集 AD/PD 脑组织 snATAC-seq 数据 → 按细胞类型聚类 → 训练多任务 CNN（共享 trunk + 细胞类型特异头）→ 用 ISM 计算 AD GWAS 变异的细胞类型特异效应评分 → 与已知功能变异验证
- **验证方式**：与 eQTL 共定位、MPRA 实验数据对比；评估细胞类型特异评分是否优于通用评分
- **创新状态**：unverified

### 候选 2：TF–DNA 结合 motif 的碱基分辨率归因与变异效应解释
- **名称**：MotifAttrib
- **来源局限/观察**：BPNet 展示了碱基分辨率 TF 结合预测的可行性，但未在神经退行性疾病变异中系统应用；现有变异优先级排序多使用粗粒度评分，缺乏 motif 级别的解释
- **核心假设**：碱基分辨率归因能揭示 AD 相关非编码变异如何通过破坏/创建 TF 结合 motif 来影响调控功能
- **增量**：将 BPNet 类模型应用于神经退行性疾病相关细胞类型，建立「变异 → motif 破坏 → 结合改变 → 疾病风险」的完整解释链
- **初步方法**：训练碱基分辨率 TF 结合模型 → 对 AD/PD GWAS 变异进行 DeepLIFT/DeepSHAP 归因 → 聚类变异效应模式 → 与已知 TF motif（JASPAR）匹配 → 优先排序候选变异
- **验证方式**：与电泳迁移率变动分析（EMSA）或报告基因实验对比；评估归因识别的 motif 是否与实验验证一致
- **创新状态**：unverified

### 候选 3：整合 TF 结合与 3D 染色质互作的变异效应级联预测
- **名称**：TF-3D-Cascade
- **来源局限/观察**：现有模型分别预测 TF 结合和 3D 染色质互作，未建模「TF 结合改变 → 染色质构象改变 → 基因表达改变」的级联效应
- **核心假设**：级联建模能捕捉单独 TF 结合模型无法预测的远程调控效应，提高变异优先级排序的准确性
- **增量**：将 TF 结合预测（BPNet 类）与 3D 基因组预测（Akita 类）串联，实现从序列变异到染色质构象变化的端到端预测
- **初步方法**：训练 TF 结合模型 → 将预测的 TF 结合变化作为 3D 基因组模型的输入特征 → 预测变异对染色质互作的影响 → 关联基因表达变化 → 在 AD 相关位点验证
- **验证方式**：与 Hi-C 数据中 AD 相关位点的染色质互作变化对比；与 eQTL 数据交叉验证
- **创新状态**：unverified

### 候选 4：基于物理模拟的 TF–DNA 结合变异效应验证框架
- **名称**：TFBind-MD-Validate
- **来源局限/观察**：DL 预测的 TF 结合变异效应缺乏物理层面的验证；分子动力学（MD）模拟可提供结合自由能的直接计算，但计算成本高
- **核心假设**：DL 预测的高效应变异在 MD 模拟中表现出显著的结合自由能变化，两者结合可提高变异优先级排序的可信度
- **增量**：建立 DL 预测 → MD 验证的两阶段变异筛选流程，兼顾通量与精度
- **初步方法**：用 DL 模型（如 DeepSEA）初筛 AD 相关变异 → 对 top 变异进行 MD 模拟（如 GROMACS/AMBER）计算 TF–DNA 结合自由能变化 → 与 DL 预测对比 → 建立一致性评分
- **验证方式**：与实验结合亲和力数据（如蛋白微阵列、表面等离子共振）对比；评估 DL+MD 联合评分的预测精度
- **创新状态**：unverified

### 候选 5：基于 Transformer 的 TF–DNA 结合长程上下文建模
- **名称**：TF-Transformer-LongRange
- **来源局限/观察**：现有 TF 结合模型（BPNet）输入长度有限（~1kb），无法捕捉远程调控元件对 TF 结合的间接影响；Enformer 虽支持长输入但未针对 TF 结合优化
- **核心假设**：Transformer 架构能有效整合长程序列上下文，提高 TF 结合预测的准确性，特别是对受远程调控影响的位点
- **增量**：设计针对 TF–DNA 结合任务优化的 Transformer 架构，支持 >10kb 输入，并保持碱基分辨率输出
- **初步方法**：基于 Enformer 架构，调整输出层为碱基分辨率 TF 结合预测 → 在 ENCODE 和脑细胞类型 ChIP-seq 数据上训练 → 与 BPNet 对比长程调控位点的预测性能 → 评估 AD 变异效应
- **验证方式**：在已知受远程调控影响的 TF 结合位点上测试；与 Hi-C 数据交叉验证
- **创新状态**：unverified