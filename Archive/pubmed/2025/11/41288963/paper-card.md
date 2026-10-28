## 01 基本信息

- **标题**：scRegulate: single-cell regulatory-embedded variational inference of transcription factor activity from gene expression
- **作者**：Zandigohar, Mehrdad; Rehman, Jalees; Dai, Yang
- **单位**：未提供（根据作者信息推测为 University of Illinois Chicago 相关机构，但原文未明确标注）
- **期刊/平台**：Bioinformatics (Oxford, England)
- **年份**：2025
- **论文类型**：方法学（Method）论文
- **领域**：计算生物学 / 单细胞转录组学 / 转录因子活性推断 / 基因调控网络推断
- **关键词**：转录因子活性、单细胞RNA测序、变分推断、基因调控网络、生成模型
- **DOI/ID**：10.1093/bioinformatics/btaf638
- **代码**：https://github.com/YDaiLab/scRegulate
- **数据**：所有数据集公开可用，详见原文引用；归档版本：https://doi.org/10.5281/zenodo.17139420
- **阅读日期**：2026-04-23（基于当前对话日期）
- **在该方向中的位置**：本文属于「蛋白质-DNA互作（聚焦TF–DNA结合机制）× AI/深度学习」方向中的**TF活性推断**子领域。与纯统计方法（如decoupleR）、基于motif的方法（如SCENIC）和贝叶斯因子模型（如BITFAM）不同，本文提出将先验TF-靶基因关系嵌入VAE架构，在非线性生成模型中联合推断TF活性和细胞类型特异的GRN。该文不直接建模TF-DNA物理结合（如motif扫描或ChIP-seq），而是通过基因表达数据反推TF调控活性，属于该方向的**下游推断**环节。

---

## 02 一句话总结

本文提出scRegulate——一个将先验TF-靶基因关系嵌入VAE架构的生成式深度学习框架，通过动态松弛先验约束、结合变分推断，从scRNA-seq数据中推断细胞特异的TF活性和细胞类型特异的加权GRN，在聚类、GRN推断和Perturb-seq验证中优于现有基线方法。

---

## 03 研究问题

- **具体问题**：如何从单细胞转录组数据中准确推断转录因子（TF）活性，并同时重建细胞类型特异的基因调控网络（GRN）？
- **为什么重要**：TF是细胞身份和功能的核心驱动因子，其活性失调与多种疾病相关。scRNA-seq提供了单细胞水平的转录组快照，但mRNA表达量并不直接等于TF蛋白活性（受翻译后修饰、核定位、竞争性结合等因素影响），因此需要计算方法从表达数据中反推TF活性。
- **现有方法不足**：
  - 统计方法（如decoupleR）依赖线性假设，无法捕捉非线性调控动态；
  - motif富集方法（如SCENIC）依赖静态motif数据库，在注释不完善的物种或条件下准确性受限；
  - 贝叶斯因子模型（如BITFAM）假设线性关系，且计算开销大；
  - 多组学方法（如SCENIC+、CellOracle、BIOTIC）需要额外的染色质可及性数据（ATAC-seq），并非所有scRNA-seq数据集都具备。
- **精确的"Can ... ?"问题**：Can a variational autoencoder with embedded prior TF-target gene constraints, progressively relaxed during training, infer cell-type-specific TF activities and GRNs from scRNA-seq data more accurately and efficiently than existing statistical, motif-based, and linear Bayesian methods?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文Introduction的叙述框架，标注为「仅本文框架」；外部核验部分另行标注。

**阶段一：基于先验知识的快速统计方法**
- 代表：decoupleR（Badia-i-Mompel et al. 2022）
- 方法：将先验TF-靶基因网络与表达矩阵结合，通过线性模型（ULM）或集成方法估计TF活性
- 优点：速度快、实现简单
- 局限：线性假设，无法捕捉非线性调控；不推断新调控关系

**阶段二：基于motif富集的共表达网络方法**
- 代表：SCENIC（Aibar et al. 2017）
- 方法：先通过共表达识别TF-靶基因模块（regulon），再用motif富集剪枝
- 优点：不依赖预先给定的TF-靶基因数据库，可发现新调控关系
- 局限：依赖静态motif数据库进行剪枝，在注释不完善的系统中准确性受限；regulon定义基于共表达，可能混淆直接与间接调控

**阶段三：贝叶斯因子模型**
- 代表：BITFAM（Gao et al. 2021）
- 方法：概率矩阵分解，将表达矩阵分解为TF活性矩阵×TF-靶基因权重矩阵
- 优点：利用ChIP-seq先验数据，可推断加权GRN
- 局限：线性假设限制了对复杂非线性转录动力学的捕捉能力

**阶段四：多组学整合方法**
- 代表：SCENIC+（Bravo González-Blas et al. 2023）、CellOracle（Kamimoto et al. 2023）、BIOTIC（Cao et al. 2024）
- 方法：整合染色质可及性数据（ATAC-seq）与转录组
- 优点：提供更准确的TF-靶基因关系
- 局限：需要额外的ATAC-seq数据，不适用于仅有scRNA-seq的数据集；数据整合带来额外复杂性

**阶段五（本文位置）：生成式深度学习 + 先验嵌入**
- 代表：scRegulate
- 方法：将先验TF-靶基因关系嵌入VAE解码器权重初始化，训练中动态松弛先验约束，允许数据驱动地修正和发现新调控关系
- 定位：填补"仅scRNA-seq数据"条件下非线性、可扩展、可解释的TF活性推断空白

**[Analysis] 外部核验**：上述脉络中，decoupleR、SCENIC、BITFAM、SCENIC+、CellOracle、BIOTIC均为该领域公认的代表性方法，其基本特征描述与文献一致。本文的定位（生成模型+先验嵌入）在该领域具有新颖性，但VAE用于scRNA-seq分析本身已有先例（如scVI、scVAE等），本文的创新点在于将GRN先验显式嵌入解码器结构。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有方法依赖静态先验 | SCENIC依赖motif数据库剪枝，在注释不完善的系统中准确性受限 | 静态数据库无法捕捉组织/细胞类型特异的调控关系 | Introduction第2段："its dependence on static motif databases for pruning may limit its accuracy when inferring TF regulon activity in poorly annotated systems" |
| 线性假设限制表达捕捉 | BITFAM等贝叶斯因子模型假设线性关系 | 转录调控本质上是非线性过程（协同、竞争、反馈） | Introduction第2段："the reliance on linear assumptions may still limit their ability to capture the complex non-linear transcriptional dynamics" |
| 多组学数据需求 | SCENIC+、CellOracle、BIOTIC需要ATAC-seq数据 | 这些方法通过染色质可及性增强TF-靶基因预测 | Introduction第3段："they require high-quality enhancer annotations or complementary ATAC-seq chromatin data, which are not always available" |
| 先验与数据冲突 | 静态先验可能包含错误或过时的调控关系 | 数据库注释不完整或存在组织特异性差异 | Methods 2.3.3：动态松弛机制（mask factor m(t)从1→0）允许新调控关系出现 |
| 可解释性与发现能力的权衡 | 纯数据驱动方法（如标准VAE）缺乏生物学可解释性 | 隐空间维度不对应已知生物学实体 | Methods 2.1：将TF节点显式嵌入VAE结构，使隐变量对应TF活性 |
| 计算效率 | BITFAM等MCMC方法在大规模数据上计算开销大 | 概率推断的采样过程耗时 | Results 3.1 图2E：scRegulate在运行时间上优于SCENIC和BITFAM |

---

## 06 核心思想

### 1) 表面方法

scRegulate是一个三阶段VAE框架：
- **阶段一（先验初始化）**：用先验GRN（默认CollecTRI）初始化解码器中连接TF活性层到输出层的权重，强制初始网络尊重已知TF-靶基因关系；
- **阶段二（动态推断）**：训练过程中通过mask factor m(t)从1逐渐衰减到0，逐步松弛先验约束，允许数据驱动地修正和发现新的TF-靶基因关系；
- **阶段三（细胞类型特化微调）**：在全局训练基础上，对每个细胞类型（或聚类）单独微调GRN权重和TF活性，获得细胞类型特异的调控网络。

### 2) 核心洞察

- **先验作为初始化而非硬约束**：与SCENIC等将先验作为固定剪枝标准不同，scRegulate将先验作为起点，通过动态松弛允许数据修正先验中的错误或发现新关系。这解决了"静态先验在动态生物学中的不适应性"问题。
- **TF活性作为VAE隐变量**：将TF活性定义为VAE隐空间中的节点激活值（ReLU），使隐变量具有明确的生物学对应，兼顾了深度学习的表达能力和传统TF活性推断的可解释性。
- **细胞类型特异的GRN**：通过微调阶段，每个细胞类型获得独立的GRN，捕捉调控网络的上下文依赖性——这是全局GRN方法无法提供的分辨率。

### 3) 可能的普适教训 [Analysis]

- **先验知识的"软嵌入"策略**：在深度学习模型中，先验知识不应作为硬约束（硬编码权重不可变），而应作为初始化或正则化项，在训练中逐步放松。这种"先验引导+数据修正"的范式可迁移到其他生物信息学推断任务（如通路活性推断、突变效应预测）。
- **隐空间的可解释性设计**：通过将隐变量与生物学实体（如TF）对齐，可以在不牺牲深度学习表达能力的前提下获得可解释的表示。这对蛋白质-DNA互作研究中的表示学习有启发意义。
- **细胞类型特化的必要性**：全局模型可能掩盖细胞类型特异的调控差异，分阶段（全局→局部）的训练策略值得在其他单细胞分析任务中借鉴。

---

## 07 方法总览

- **输入**：
  - scRNA-seq表达矩阵（经Scanpy预处理：过滤低质量细胞、选择高变基因、log归一化）
  - 可选先验GRN（默认CollecTRI，包含1186个TF的带符号TF-基因互作）
- **输出**：
  - 每个细胞的TF活性向量（非负值，ReLU激活）
  - 加权GRN矩阵（正/负/零值，表示TF对靶基因的激活/抑制/无调控）
  - 细胞类型特异的GRN（微调后）
- **模型架构**：
  - VAE：编码器（1-3层全连接+ReLU）将表达谱映射到隐空间（μ, σ）；解码器（1-2层）先推断TF活性，再通过可训练的GRN权重矩阵重建基因表达
  - 重参数化技巧用于采样隐变量
- **训练**：
  - 损失函数 = ELBO + GRN正则化项（L1稀疏惩罚）
  - 优化器：Adam，自适应学习率调度器（基于验证损失）
  - 数据划分：85%训练 / 15%验证
  - 全局种子42确保可复现性
- **关键机制**：
  - 先验初始化：解码器权重初始化为先验GRN
  - 动态松弛：mask factor m(t)从1线性衰减到0，控制先验约束的强度
  - α调度：从α_start到α_max逐步增加，控制先验驱动估计（ULM）到数据驱动推断的过渡
- **下游分析**：
  - 基于TF活性的细胞聚类（Leiden算法）
  - 差异活性TF识别（Wilcoxon秩和检验）
  - TF-靶基因功能富集分析（GO）
  - TF-TF共调控网络构建（余弦相似度）
- **流程**：表达矩阵 → 预处理 → VAE训练（先验初始化→动态松弛→全局收敛）→ 细胞类型微调 → 输出TF活性+GRN → 下游分析

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 先验GRN初始化 | 将CollecTRI等先验知识嵌入解码器初始权重 | 提供生物学先验，引导模型从合理的调控假设出发，避免纯数据驱动的任意初始化 | 输入：先验GRN矩阵；输出：初始化解码器权重 | Methods 2.1, 2.3.2；Results 3.2中CollecTRI初始化优于随机初始化 | 预期影响：失去先验引导，模型可能收敛到生物学上不合理的局部最优，尤其在数据稀疏时（[Analysis] 原文未做此消融实验，属预期推断） |
| 动态松弛机制（mask factor m(t)） | 训练中逐步从1衰减到0，控制先验约束强度 | 允许数据修正先验中的错误或发现新调控关系，避免先验成为硬性限制 | 输入：训练轮次t；输出：mask值m(t)∈[0,1] | Methods 2.3.3公式(5)-(6) | 预期影响：若m(t)恒为1（先验硬约束），模型无法发现新调控关系；若恒为0（无先验），退化为标准VAE，失去生物学引导（[Analysis] 原文未做此消融实验） |
| α调度（先验→数据过渡） | 控制ULM先验估计与数据驱动解码器估计的混合比例 | 训练初期依赖先验稳定收敛，后期让数据主导发现新模式 | 输入：训练轮次t；输出：α∈[0,α_max] | Methods 2.3.2公式(3)-(4) | 预期影响：α调度不当可能导致训练不稳定或先验过度主导（[Analysis] 原文未做此消融实验） |
| 编码器（1-3层全连接+ReLU） | 将基因表达谱映射到隐空间参数（μ, σ） | 降维并捕捉非线性表达模式 | 输入：基因表达向量x；输出：隐变量分布参数(μ, σ) | Methods 2.3.1 | 预期影响：移除后无法进行变分推断，模型退化为确定性自编码器，丧失不确定性估计能力 |
| 解码器（1-2层全连接+ReLU） | 从隐变量（TF活性）重建基因表达 | 建立TF活性到基因表达的生成映射 | 输入：隐变量z；输出：TF活性估计ê^TF，再经GRN权重W重建基因表达x̂ | Methods 2.3.1公式(1)-(2) | 预期影响：移除后无法重建表达，模型无法学习生成过程 |
| GRN权重矩阵W（可训练） | 定义TF-靶基因互作的强度和方向 | 输出加权GRN，实现调控网络的推断 | 输入：TF活性向量；输出：基因表达预测 | Methods 2.3.1公式(2)；Results 3.2 GRN基准测试 | 实测消融：在GRouNdGAN基准上，移除先验初始化后AUPRC显著下降（Results 3.2） |
| L1稀疏正则化 | 对GRN权重施加稀疏惩罚 | 减少弱调控关系的噪声，提高GRN可解释性 | 输入：GRN权重矩阵W；输出：正则化损失项 | Methods 2.3.3公式(4) | 预期影响：移除后GRN可能包含大量弱连接，降低推断精度（[Analysis] 原文未做此消融实验） |
| 细胞类型特化微调 | 对每个细胞类型单独优化GRN和TF活性 | 捕捉细胞类型特异的调控网络，提供全局模型无法达到的分辨率 | 输入：全局训练后的模型+细胞类型标签；输出：细胞类型特异的GRN和TF活性 | Methods 2.1阶段三；Results 3.4 PBMC案例 | 预期影响：移除后只能获得全局GRN，无法区分细胞类型特异的调控差异（[Analysis] 原文未做此消融实验） |

---

## 09 关键公式符号

> 注：原文公式以文字描述为主，以下基于Methods 2.3节内容整理，具体编号为原文编号。

**1. 编码器（变分后验近似）**：
q_φ(z|x) = N(z; μ_φ(x), σ_φ(x))

- z：隐变量（潜在表示）
- x：输入基因表达向量
- φ：编码器网络参数
- μ_φ(x), σ_φ(x)：编码器输出的均值和标准差

**2. 重参数化技巧**：
z = μ + σ ⊙ ε, ε ~ N(0, I)

- ε：标准正态随机变量
- ⊙：逐元素乘法

**3. 解码器（TF活性推断）**：
ê^TF = p_θ(z) （解码器将隐变量映射到TF活性空间）

- ê^TF：推断的TF活性向量
- θ：解码器网络参数

**4. 基因表达重建**：
x̂ = W · ê^TF

- x̂：重建的基因表达向量
- W：GRN权重矩阵（TF×基因）
- 该式定义了TF活性到基因表达的线性映射，是GRN推断的核心

**5. 先验-数据混合（α调度）**：
ê^TF = (1-α) · ê^TF_ULM + α · p_θ(e^TF|z)

- ê^TF_ULM：基于先验GRN的ULM估计（初始化为先验驱动）
- α ∈ [0, α_max]：混合系数，随训练从α_start增加到α_max
- 该式平衡先验知识与数据驱动推断

**6. α更新规则**：
α_{t+1} = α_t + Δα（当α_t < α_max时）

- t：训练迭代次数
- Δα：步长超参数

**7. GRN稀疏正则化**：
L_reg = γ Σ_j ||w_{.,j}||_1

- γ：正则化系数（线性调度）
- w_{.,j}：GRN权重矩阵中第j列（基因j的所有TF调控权重）
- L1范数促进稀疏性

**8. 先验掩码更新**：
W_updated = m(t) · W_prior + (1-m(t)) · W_learned

- m(t)：掩码因子，从1线性衰减到0
- W_prior：先验GRN权重
- W_learned：数据驱动的学习权重
- 该式实现先验约束的动态松弛

**9. 总损失函数**：
L_total = ELBO + L_reg

- ELBO：证据下界（变分推断标准目标）
- L_reg：GRN稀疏正则化项

---

## 10 实验设计与证据链

### 数据集与资源

| 数据集 | 类型 | 规模/内容 | 用途 |
|--------|------|-----------|------|
| Tabula Muris（heart, lung, brain） | 小鼠单细胞转录组 | 多组织、多细胞类型 | TF活性聚类评估 |
| PBMC | 人外周血单核细胞 | 8种免疫细胞类型 | TF活性聚类评估 |
| 人类中颞回（MTG） | 人脑单细胞转录组 | 多种神经元/胶质细胞类型 | TF活性聚类评估 |
| GRouNdGAN模拟数据（Dahlin, PBMC, Tumor） | 合成单细胞数据 | 已知ground truth GRN | GRN推断精度评估 |
| Perturb-seq（CRISPRi） | 扰动实验数据 | 10个TF的双敲低 | TF活性推断验证 |
| 人类PBMC 3k | 真实单细胞数据 | 健康供体外周血 | 案例研究 |

### 基线方法

pySCENIC、BITFAM、decoupleR、BIOTIC、CellOracle（5种代表性方法）

### 评估指标

- 聚类：ARI（Adjusted Rand Index）、NMI（Normalized Mutual Information）、macro F1、AUC
- GRN推断：AUROC、AUPRC
- 扰动验证：TF活性log2 fold change（LFC）方向与显著性

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| TF活性聚类（PBMC） | scRegulate的TF活性表示能准确区分细胞类型 | 与SCENIC、decoupleR、BIOTIC对比 | ARI=0.814±0.042, NMI=0.821±0.021, F1=0.868±0.118, AUC=0.930±0.058，显著优于对比方法（Wilcoxon, P<.01） | scRegulate的TF活性捕获细胞异质性优于现有方法 | 未在更多组织类型上验证泛化性 | Results 3.1, 图2A |
| TF活性聚类（lung, heart, brain） | scRegulate在多种组织上保持优势 | 与SCENIC、decoupleR、BIOTIC对比 | AUC: lung=0.948±0.033, heart=0.992±0.002, brain=0.953±0.015 | scRegulate跨组织泛化性良好 | 未与CellOracle、BITFAM在这些数据集上对比 | Results 3.1, 图2A |
| 缺失值鲁棒性（MTG） | scRegulate对dropout鲁棒 | 随机遮蔽10%和30%表达值 | scRegulate保持高聚类性能，对比方法显著下降（P<.01） | scRegulate对数据稀疏性鲁棒 | 未测试更高缺失率 | Results 3.1, 图2B-C |
| 可扩展性 | scRegulate随数据规模扩展 | 不同数据集大小 | scRegulate保持高F1分数 | scRegulate可扩展至大规模数据 | 未提供具体时间-规模曲线 | Results 3.1, 图2D |
| 计算效率 | scRegulate运行时间优于基线 | 与SCENIC、BITFAM对比 | scRegulate显著快于SCENIC和BITFAM | scRegulate计算高效 | 未与decoupleR、CellOracle、BIOTIC对比运行时间 | Results 3.1, 图2E |
| GRN推断（GRouNdGAN） | scRegulate在合成数据上GRN重建精度高 | 与SCENIC、CellOracle、BITFAM对比 | 在Dahlin、PBMC、Tumor数据集上AUROC/AUPRC均最优（如PBMC: AUPRC=0.946, AUROC=0.703） | scRegulate在受控条件下GRN推断优于基线 | 合成数据与真实调控网络存在差距 | Results 3.2, 图3A |
| GRN推断（mESC） | scRegulate在真实数据上GRN重建精度高 | 与pySCENIC对比 | AUROC和AUPRC均优于pySCENIC | scRegulate在真实数据上GRN推断优于基线 | 仅与pySCENIC对比，未与其他方法对比 | Results 3.2, 图5 |
| Perturb-seq验证 | scRegulate能正确推断敲低TF的活性下降 | CRISPRi双敲低10个TF | 所有测试TF均显示显著负LFC（范围-0.19至-0.61），ELK1（LFC=-0.61, P=2.37×10⁻¹¹）和EGR1（LFC=-0.57, P=7.12×10⁻⁶）最强 | scRegulate的TF活性与实验扰动一致 | 仅验证了敲低方向，未验证敲低幅度与蛋白水平的相关性 | Results 3.3, 图3B |
| 与基线在Perturb-seq上的对比 | scRegulate在扰动检测上优于基线 | 与SCENIC、decoupleR、BITFAM对比 | SCENIC和decoupleR未能检测ELK1的显著抑制（P>.7），BITFAM错误推断为激活（LFC=0.18, P=.0068） | scRegulate在扰动检测上更准确 | 仅对比了ELK1一个TF的详细结果 | Results 3.3 |
| PBMC案例研究 | scRegulate识别已知细胞类型特异TF | 8种免疫细胞类型 | 识别出PAX5（B细胞）、GATA3/BATF（CD4 T细胞）、RUNX3/EOMES/STAT4/STAT5A/TBX21（CD8 T细胞）、ID2/EOMES/TBX21（NK细胞）、SPI1/CEBPB/CEBPE（髓系）等已知谱系决定TF | scRegulate的TF活性具有生物学有效性 | 未进行新调控关系的实验验证 | Results 3.4, 图4 |
| 先验GRN依赖性 | scRegulate性能受先验GRN质量影响 | 使用不同先验GRN（CollecTRI vs 随机/其他） | CollecTRI初始化表现最佳（图10） | 先验GRN质量影响性能 | 未系统评估不同先验来源的梯度效应 | Results 3.4, 图10 |

---

## 11 结论正确解读

### 任务范围
- 本文解决的是**从scRNA-seq数据推断TF活性和GRN**的计算问题，不涉及TF-DNA物理结合的分子机制建模（如motif扫描、ChIP-seq峰分析、分子动力学模拟）。
- 输入仅为基因表达矩阵+先验GRN，不利用染色质可及性、DNA序列或表观遗传数据。

### 有边界的结论复述
1. **在聚类任务上**：scRegulate的TF活性表示在PBMC、肺、心脏、脑四个数据集上，以ARI/NMI/F1/AUC为指标，优于或持平于SCENIC、decoupleR、BIOTIC（Wilcoxon检验P<.01）。
2. **在GRN推断任务上**：在GRouNdGAN合成数据（Dahlin、PBMC、Tumor）和mESC真实数据上，scRegulate的AUROC/AUPRC优于SCENIC、CellOracle、BITFAM。
3. **在扰动验证任务上**：在CRISPRi Perturb-seq数据上，scRegulate正确推断出10个敲低TF的活性下降（LFC范围-0.19至-0.61），而SCENIC和decoupleR对ELK1敲低不敏感，BITFAM方向错误。
4. **在生物学有效性上**：PBMC案例中识别的细胞类型特异TF与已知谱系决定因子一致。

### 不能得出的结论
- 不能得出scRegulate在所有数据集和条件下都优于所有方法的结论——对比的基线方法有限，且未在所有数据集上对比所有方法。
- 不能得出scRegulate发现的"新"TF-靶基因关系具有生物学真实性的结论——未进行湿实验验证。
- 不能得出scRegulate适用于无先验GRN的物种或条件的结论——先验GRN是模型的重要组成部分。
- 不能得出TF活性推断等同于TF蛋白活性测量的结论——推断的是转录调控活性，与蛋白丰度、DNA结合 occupancy 不等价。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 性能依赖先验GRN质量 | 使用不同先验GRN（CollecTRI vs 其他）时性能有差异（图10） | 可通过整合motif分析或ATAC-seq数据增强先验GRN | Discussion："scRegulate's performance depends on the networks used for establishing prior knowledge" |
| 未建模其他调控层 | 仅关注TF调控，未纳入染色质可及性、DNA甲基化、非编码RNA等 | 未来可扩展整合多组学数据 | Discussion："Other regulators, including chromatin remodelers and non-coding RNAs, also contribute to transcriptional regulation" |
| 未显式建模DNA motif/可及性 | 模型不直接利用DNA序列信息或染色质状态 | 未来可纳入DNA-guided特征 | Discussion："Future extensions could incorporate DNA-guided features" |
| 需要超参数调优 | 特定数据集可能需要调整α调度、网络深度等超参数 | 未提供自动超参数搜索策略 | Discussion："Further hyperparameter tuning may be required in certain datasets" |
| 基准测试的局限性 | 合成数据（GRouNdGAN）与真实调控网络存在差距；真实数据缺乏gold standard | 需要更多实验验证的调控网络作为基准 | Discussion："true regulatory networks are rarely known, especially in higher eukaryotes" |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 先验GRN（CollecTRI）与测试数据的重叠 | 如果测试数据中的TF-靶基因关系大量存在于CollecTRI中，性能优势可能部分来自先验信息的"泄漏"而非模型的学习能力 | 影响对模型核心贡献的评估 | 使用去除CollecTRI中已知关系的"干净"测试集，或与无先验的VAE变体对比 | Methods 2.3.2-2.3.3；Results 3.2 |
| 与基线方法的公平性 | 不同方法使用不同的先验资源（SCENIC用motif数据库，BITFAM用ChIP-seq，scRegulate用CollecTRI），比较可能不完全公平 | 影响结论"优于现有方法"的强度 | 统一先验资源，或评估各方法在其最优配置下的表现 | Methods 2.4；Results 3.2 |
| 细胞类型特化微调可能过拟合 | 微调阶段在每个细胞类型上单独优化，如果某些细胞类型样本量小，可能过拟合 | 影响GRN推断的泛化性 | 在小样本细胞类型上评估微调前后的稳定性，或使用交叉验证 | Methods 2.1阶段三；Results 3.4 |
| 未报告不确定性量化 | VAE提供隐变量的分布，但论文未展示TF活性估计的不确定性如何用于下游分析 | 不确定性信息是VAE相对确定性方法的优势 | 展示TF活性估计的置信区间及其对下游结论的影响 | Methods 2.3.1；Results |
| 与TF-DNA物理结合证据的脱节 | 推断的TF活性未与ChIP-seq、motif扫描或DNA结合实验交叉验证 | 对"TF活性"的生物学有效性需要多角度验证 | 将推断的TF活性与同一细胞类型的ChIP-seq信号或ATAC-seq footprint比较 | Results 3.3-3.4 |
| 未与其他深度学习方法对比 | 对比的基线主要是统计/线性方法，未与近期基于深度学习的TF活性推断方法（如基于图神经网络或Transformer的方法）对比 | 影响对"深度学习框架"优势的评估 | 增加与近期深度学习方法的对比实验 | Results 3.2；Introduction |
| 合成数据基准的局限性 | GRouNdGAN模拟数据基于特定生成模型，可能无法完全反映真实调控网络的复杂性 | 影响GRN推断结论的推广性 | 在更多独立实验验证的GRN数据集上评估 | Results 3.2；Discussion |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

### 概念层面
1. **先验的"软嵌入"优于"硬约束"**：scRegulate将先验GRN作为初始化而非固定约束，通过mask factor动态松弛。这一思想可迁移到TF-DNA结合预测任务——例如，将已知的motif位置权重矩阵（PWM）作为神经网络初始化的先验，而非硬编码过滤条件，允许模型在训练中修正motif模型。
2. **TF活性与GRN的联合推断**：TF活性和GRN是相互依赖的——TF活性决定靶基因表达，而靶基因表达又反映TF活性。scRegulate在统一框架中联合优化两者，避免了分步推断的误差累积。这对TF-DNA互作研究有启发：结合DNA序列特征和基因表达数据联合建模，可能比单独建模更准确。
3. **细胞类型特异的调控网络**：全局GRN掩盖了细胞类型特异的调控差异。scRegulate的微调阶段提供了"全局初始化+局部特化"的范式，适用于研究不同细胞类型中同一TF的不同调控行为。

### 方法层面
4. **VAE用于调控推断的可行性**：VAE不仅能用于数据降维和生成，还能通过设计解码器结构（将隐变量映射到TF活性，再经GRN权重映射到基因表达）实现生物学可解释的推断。这一架构设计可迁移到其他调控推断任务。
5. **动态调度策略**：α调度（先验→数据）和mask调度（约束→自由）是平衡先验知识与数据驱动学习的有效手段。在TF-DNA结合预测中，可类似地设计"先验约束强度随训练递减"的策略。
6. **多基准评估框架**：scRegulate的评估策略（聚类+GRN重建+扰动验证+生物学案例）为TF活性推断方法提供了可复用的评估模板。

### 对TF-DNA互作课题的迁移建议
7. **将scRegulate的TF活性作为特征**：在蛋白质-DNA互作研究中，scRegulate推断的TF活性可作为下游预测模型（如TF结合位点预测、增强子-启动子互作预测）的输入特征，补充序列特征和染色质特征。
8. **先验GRN的构建**：scRegulate使用CollecTRI作为先验，但也可使用基于motif扫描或ChIP-seq的先验GRN。在缺乏实验数据的物种中，可考虑用TF-DNA结合预测模型（如DeepSEA、Enformer）生成的预测互作作为先验。
9. **与物理模拟的结合**：scRegulate推断的细胞类型特异GRN可为分子动力学（MD）模拟或对接研究提供候选TF-靶基因对，缩小需要高成本物理模拟的搜索空间。

---

## 15 与已有知识连接

### 可核验的外部文献连接
1. **scVI / VAE在单细胞中的应用**：scRegulate基于VAE架构，与scVI（Lopez et al. 2018, Nature Methods）和scANVI等单细胞VAE方法一脉相承，但scRegulate的贡献在于将GRN先验嵌入解码器结构，而非仅用于数据去噪或批次校正。
2. **SCENIC / pySCENIC**（Aibar et al. 2017, Nature Methods）：SCENIC通过共表达+motif富集推断regulon活性，是TF活性推断的经典方法。scRegulate在多个基准上与其对比，并声称在非线性建模和细胞类型特异性方面更优。
3. **BITFAM**（Gao et al. 2021, Nature Communications）：基于贝叶斯因子分解的TF活性推断方法，利用ChIP-seq先验。scRegulate与其对比，指出其线性假设的限制。
4. **decoupleR**（Badia-i-Mompel et al. 2022, Bioinformatics）：基于先验网络的快速统计方法，scRegulate与其对比，强调非线性建模的优势。
5. **CollecTRI**（Müller-Dott et al. 2023, Nucleic Acids Research）：scRegulate使用的默认先验GRN数据库，包含1186个TF的带符号互作。
6. **GRouNdGAN**（Zinati et al. 2024）：用于生成具有已知ground truth GRN的单细胞数据，scRegulate使用其作为GRN推断的基准。
7. **Perturb-seq / CRISPRi**（Dixit et al. 2016, Cell）：scRegulate使用Perturb-seq数据验证TF活性推断的准确性。

### 与用户课题方向的连接
8. **TF-DNA结合机制**：scRegulate不直接建模TF-DNA物理结合，但其推断的TF活性反映了TF在细胞中的调控输出，可作为TF-DNA结合功能后果的度量。结合DNA序列特征（如motif）和染色质状态（如ATAC-seq），可构建"序列→结合→活性→表达"的完整调控链条。
9. **AI/深度学习在TF-DNA互作中的应用**：scRegulate展示了如何将生物学先验嵌入深度学习架构。类似地，TF-DNA结合预测模型（如DeepSEA、Basenji、Enformer）可考虑将scRegulate推断的TF活性作为辅助任务或特征，实现多任务学习。
10. **物理模拟（MD/对接）**：scRegulate推断的细胞类型特异GRN可为MD模拟提供生物学相关的候选TF-靶基因对，减少盲目搜索。同时，MD模拟计算的结合自由能可作为scRegulate推断GRN权重的物理约束或验证。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选1：TF-DNA序列特征与scRegulate TF活性的多模态融合预测
- **名称**：SeqActTF：序列-活性融合的TF结合预测框架
- **来源局限/观察**：scRegulate仅使用基因表达数据推断TF活性，未利用DNA序列信息；而现有TF-DNA结合预测模型（如DeepSEA）仅使用序列特征，未考虑细胞状态依赖的TF活性。
- **核心假设**：将DNA序列特征（motif、保守性、染色质可及性）与scRegulate推断的细胞类型特异TF活性融合，可提高TF结合位点预测的准确性和细胞类型特异性。
- **初步方法**：构建双通道神经网络——序列通道（CNN/Transformer编码DNA序列）和活性通道（scRegulate输出的TF活性向量），在中间层融合后预测TF结合概率。在ENCODE ChIP-seq数据和单细胞ATAC-seq数据上验证。
- **验证方式**：与DeepSEA、Basenji等序列-only模型对比AUPRC；评估在不同细胞类型间的迁移性能。
- **创新状态**：unverified

### 候选2：将MD模拟结合自由能作为GRN权重的物理约束
- **名称**：PhysReg：物理约束的GRN推断
- **来源局限/观察**：scRegulate的GRN权重完全由表达数据驱动，缺乏物理化学约束；TF-DNA结合强度（由MD模拟或对接计算）是GRN权重的天然先验。
- **核心假设**：将MD模拟计算的TF-DNA结合自由能作为GRN权重的正则化项，可提高GRN推断的物理合理性和跨条件泛化能力。
- **初步方法**：对关键TF-靶基因对进行MD模拟或分子对接，计算结合自由能ΔG；将ΔG作为先验约束加入scRegulate的损失函数（如权重初始化或正则化项）；在Perturb-seq和GRouNdGAN数据上对比有无物理约束的性能。
- **验证方式**：GRN推断AUPRC提升；预测的TF-靶基因互作与ChIP-seq实验数据的一致性。
- **创新状态**：unverified

### 候选3：基于scRegulate TF活性的细胞类型特异TF-TF协同调控网络分析
- **名称**：CoopReg：TF协同调控模块识别
- **来源局限/观察**：scRegulate输出细胞类型特异的TF活性和GRN，但未系统分析TF-TF协同调控关系；TF常以复合物形式协同结合DNA。
- **核心假设**：在特定细胞类型中，协同调控的TF对在活性上表现出显著相关性，且其共靶基因富集于特定生物学通路。
- **初步方法**：利用scRegulate推断的细胞类型特异TF活性矩阵，计算TF-TF活性相关性网络；结合GRN权重识别共靶基因模块；对模块进行GO/KEGG富集分析；与已知蛋白-蛋白互作数据库（如STRING）交叉验证。
- **验证方式**：识别的TF-TF协同模块与已知调控复合物（如AP-1、NF-κB）的一致性；模块的细胞类型特异性。
- **创新状态**：unverified

### 候选4：scRegulate的扰动响应预测扩展
- **名称**：PerturbAct：基于scRegulate的TF敲低/过表达响应预测
- **来源局限/观察**：scRegulate在Perturb-seq数据上验证了TF敲低后活性下降，但未利用模型预测未实验的扰动响应。
- **核心假设**：scRegulate学习到的生成模型可用于预测任意TF扰动后的基因表达变化和GRN重布线。
- **初步方法**：在scRegulate训练完成后，通过干预隐空间中的TF活性节点（如设为零或倍增），用解码器预测基因表达变化；与已知Perturb-seq数据对比验证；扩展至预测组合扰动。
- **验证方式**：预测的差异表达基因与实验Perturb-seq数据的一致性（如top-k重叠率、相关性）。
- **创新状态**：unverified

### 候选5：整合scATAC-seq的TF-DNA结合先验增强scRegulate
- **名称**：ActiBind：染色质可及性引导的TF活性推断
- **来源局限/观察**：scRegulate仅使用表达数据，未利用染色质可及性信息；TF-DNA结合需要开放的染色质区域，scATAC-seq提供了这一信息。
- **核心假设**：将scATAC-seq推断的TF结合足迹（footprint）作为先验约束，可提高scRegulate在复杂组织中的TF活性推断准确性。
- **初步方法**：从scATAC-seq数据中计算TF footprint得分；将footprint得分整合到scRegulate的先验GRN初始化或正则化项中；在同时具有scRNA-seq和scATAC-seq的多组学数据集上验证。
- **验证方式**：与仅使用表达数据的scRegulate对比聚类和GRN推断性能；与SCENIC+对比。
- **创新状态**：unverified