## 01 基本信息

- **标题**: NetREm: Network Regression Embeddings reveal cell-type transcription factor coordination for gene regulation
- **作者与单位**: Khullar, Saniya; Huang, Xiang; Ramesh, Raghu; Svaren, John; Wang, Daifeng（单位未在摘要中提供）
- **期刊/预印本平台**: Bioinformatics Advances
- **年份**: 2025-04-22
- **论文类型**: 方法学（计算生物学工具开发与验证）
- **领域**: 计算基因组学；基因调控网络推断；单细胞转录组学
- **关键词**: 转录因子协调（TF coordination）；网络正则化回归（network-regularized regression）；单细胞RNA测序（scRNA-seq）；基因调控网络（GRN）；细胞类型特异性
- **DOI/arXiv 号**: 10.1093/bioadv/vbae206
- **代码**: https://github.com/SaniyaKhullar/NetREm
- **数据**: 未提供统一数据仓库链接，数据在文章及在线补充材料中
- **阅读日期**: 未提供
- **在课题方向中的位置**: 本文属于「蛋白质-DNA互作（聚焦TF–DNA结合机制）× AI/深度学习」方向中的**图正则化回归方法**分支。其核心创新在于将TF-TF蛋白-蛋白相互作用（PPI）网络作为先验知识，通过网络正则化约束，从单细胞基因表达数据中推断细胞类型特异的TF-TF协调关系及其对靶基因（TG）的调控。该方法不直接建模TF-DNA结合，而是通过表达调控间接推断TF间的功能协调，可作为TF-DNA结合机制研究的互补视角。

## 02 一句话总结

本文提出NetREm方法，利用TF间的蛋白-蛋白相互作用（PPI）网络作为正则化先验，通过SVD变换将单细胞基因表达数据映射到嵌入空间，再用Lasso回归推断细胞类型特异的TF-TF协调关系（B）和TF-TG调控网络，并在人类、小鼠、酵母及施万细胞和阿尔茨海默病数据中验证其有效性。

## 03 研究问题

- **具体问题**: 如何从单细胞基因表达数据中推断细胞类型特异的TF-TF协调关系及其对靶基因（TG）的调控？现有方法忽略了TF间已知的PPI网络结构，导致无法捕捉TF间的功能协调。
- **为什么重要**: TF通常以组合方式协同或拮抗地调控靶基因，这种协调关系是理解细胞类型特异的基因调控程序的关键。然而，大多数GRN推断工具仅基于表达相关性，忽略了TF-TF间的物理或功能相互作用这一重要先验知识。
- **现有方法不足**: 现有GRN推断工具（如SCENIC、GRNBoost2、PIDC等）主要基于共表达、互信息或回归，但往往：(1) 忽略TF-TF PPI网络结构；(2) 无法区分协同与拮抗关系；(3) 在M≪N的高维稀疏单细胞数据中不稳定。
- **精确研究问题**: Can a network-regularized regression framework that incorporates TF-TF PPI priors reveal cell-type-specific TF coordination (both cooperative and antagonistic) for target gene regulation from single-cell gene expression data?

## 04 背景与发展脉络

*注：此脉络基于本文框架整理，未经外部系统核验。*

1. **经典GRN推断方法**：基于相关性（Pearson）、互信息（PIDC）、回归（GENIE3）、布尔网络等，主要利用表达数据的统计模式，但忽略先验生物学知识。
2. **基于 motif 的方法**：如SCENIC，利用TF motif 结合位点信息推断调控子（regulons），但受限于 motif 数据库覆盖度，约10%的TF缺乏motif数据，且无法捕捉间接调控。
3. **网络正则化回归**：Li & Li (2008) 提出网络约束正则化回归，将基因网络作为先验融入回归模型，但未应用于TF-TF协调推断。
4. **单细胞GRN推断**：scRNA-seq技术推动细胞类型特异的GRN推断，但数据稀疏性和噪声仍是挑战。
5. **本文位置**：NetREm将PPI网络作为正则化先验，通过SVD构造嵌入空间，将网络正则化回归转化为标准Lasso问题，同时输出TF-TG调控关系和TF-TF协调关系（B），填补了现有方法在显式建模TF协调方面的空白。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有GRN工具忽略TF-TF PPI先验 | SCENIC等仅基于motif和共表达，无法利用已知PPI信息 | 传统方法未将PPI网络结构融入推断过程 | Introduction: "these SOTA tools often overlook the interdependent TF-TF PPI networks (PPINs) that are crucial for TG regulation" |
| 无法区分协同与拮抗协调 | 现有方法仅给出正/负相关，缺乏对TF间协调性质的系统推断 | 缺乏对TF-TF关系的显式建模 | Results 3.2: NetREm输出带符号的B分数，区分协同（正）与拮抗（负） |
| 高维稀疏数据下推断不稳定 | M≪N时，传统回归方法易过拟合 | 单细胞数据维度高、噪声大 | Methods 2.1: "If M≪N, then X suffers from the curse of dimensionality" |
| 弱motif信号TF被遗漏 | 如TEAD1在SCENIC中被遗漏 | 仅依赖motif匹配强度，弱信号TF被过滤 | Discussion: "SCENIC identifies many TFs... but overlooks TEAD1" |
| 缺乏细胞类型特异的PPI注释 | 现有PPI数据库是全局的，缺乏细胞类型分辨率 | PPI数据库构建技术限制 | Methods 2.1: "most PPINs are global and organism-specific, lacking cell-type and tissue specificity" |

## 06 核心思想

1. **表面方法**: NetREm将TF-TF PPI网络作为图正则化先验，融入弹性网络回归框架。对每个TG，以候选TF表达为特征、TG表达为响应，求解网络正则化回归问题。通过SVD将问题转化为标准Lasso，得到TF-TG系数c*，并基于嵌入构造TF-TF协调分数B。

2. **核心洞察**: TF间的PPI网络（直接和/或间接相互作用）编码了TF协调的先验知识。通过图拉普拉斯正则化，模型倾向于选择在PPI网络中紧密连接的TF组（grouped selection），从而：(a) 识别出功能相关的TF模块；(b) 利用PPI信息弥补表达数据中弱相关但生物学重要的TF-TG关系；(c) 通过系数符号推断协同/拮抗关系。

3. **可能的普适教训** [Analysis]: 将先验生物网络（如PPI）作为正则化约束，而非仅作为事后验证，可以显著提升从高维噪声数据中推断调控关系的能力。这一思想可迁移到TF-DNA结合机制研究：例如，将ChIP-seq共结合信息或3D基因组相互作用作为正则化先验，改进TF结合位点预测或增强子-启动子配对推断。

## 07 方法总览

- **输入**: (1) 单细胞基因表达矩阵 X∈R^{M×N}（M个细胞，N个候选TF）；(2) 靶基因表达向量 y∈R^M；(3) TF-TF PPI网络 W0（来自STRINGdb等，加权、无向）；(4) 可选：先验GRN（TF-RE-TG候选链接）
- **输出**: (1) TF-TG调控网络（系数c*，正=激活，负=抑制）；(2) TG特异的TF-TF协调网络B（-100~100，正=协同，负=拮抗）；(3) 细胞类型特异的整体TF-TF协调网络B̄
- **模块**:
  1. 数据预处理：标准化表达数据（z-score）
  2. PPI网络预处理：子集化至候选TF，添加缺失边权重η=0.01，构造图拉普拉斯
  3. 网络正则化回归：求解式(1)的优化问题
  4. SVD变换：将问题转化为标准Lasso（式4），计算嵌入X̃和ỹ
  5. Lasso求解：使用LassoCV选择最优α
  6. 输出生成：c* → TF-TG网络；B = f(X̃, c*) → TF-TF协调网络
- **训练**: 对每个TG独立求解；使用70%训练/30%测试（A1, A11-12）；超参数β（网络正则化强度）和α（稀疏性）需调优
- **工具**: Python, scikit-learn (LassoCV, ElasticNetCV等), STRINGdb
- **反馈回路**: 无显式反馈回路；但输出B可注释已知PPI，发现新PPI候选
- **假设**: (1) TF表达水平可作为其蛋白活性的代理；(2) PPI网络权重反映TF间功能协调的先验概率；(3) 线性模型足以捕捉TF-TG调控关系；(4) 细胞类型内TF协调关系相对稳定

**文字流程**: 输入表达矩阵和PPI网络 → 对每个TG，标准化数据 → 构建图拉普拉斯正则化项 → 求解网络正则化回归（式1）→ 通过SVD构造嵌入X̃, ỹ（式3）→ 用LassoCV求解标准Lasso（式4）→ 得到c* → 构建TF-TG网络 → 计算B分数 → 聚合所有TG的B得到B̄网络 → 输出细胞类型特异的调控和协调网络。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| PPI网络预处理 | 将全局PPI子集化至候选TF，添加缺失边权重η | 使PPI网络与候选TF集合匹配，保证图拉普拉斯正定性 | 输入：全局PPI W0；输出：全连接加权PPI W | Methods 2.1: "adds an artificial weight 0<η<w_min0 for missing pairwise edges" | 移除后图拉普拉斯可能不连通，正则化失效 [预期] |
| 网络正则化回归（式1） | 联合优化数据拟合、稀疏性和网络平滑性 | 核心创新：将PPI先验融入回归 | 输入：X, y, W；输出：c* | Methods 2.1 式(1) | 退化为弹性网络，失去PPI先验信息 [预期] |
| SVD变换 | 将网络正则化问题转化为标准Lasso | 利用现有高效Lasso求解器 | 输入：E = X^TX/M + βA；输出：X̃, ỹ | Methods 2.1 式(2)-(4) | 无法使用标准Lasso工具，需自定义优化器 [预期] |
| Lasso求解（LassoCV） | 求解稀疏系数c* | 选择最优α，平衡稀疏性和拟合 | 输入：X̃, ỹ；输出：c* | Methods 2.1: "solved using standard Lasso or LassoCV" | 无稀疏性，所有TF都被保留，模型不可解释 [预期] |
| TF-TF协调分数B计算 | 从嵌入和c*推断TF间协调关系 | 核心输出：量化TF间协同/拮抗 | 输入：X̃, c*；输出：B矩阵(-100~100) | Results 3.2: "B scores predict the potential behavior among TFs" | 无法推断TF协调，仅能获得TF-TG关系 [预期] |
| 先验GRN整合（A11-12） | 利用多组学数据构建候选TF列表 | 提高生物学相关性，减少搜索空间 | 输入：scATAC-seq, motif, 3D基因组；输出：TG特异候选TF | Methods 2.2: "derive prior GRNs using multi-omics data" | 候选TF过多，计算量大且假阳性增加 [预期] |

## 09 关键公式符号

**式(1) 网络正则化回归目标函数**：
c* = argmin_c f(c) = (1/(2M))‖y - Xc‖² + α‖c‖₁ + (β/2)ΣᵢΣⱼ wᵢⱼ(cᵢ/√dᵢ - cⱼ/√dⱼ)²

- c ∈ R^N：TF系数向量，表示各TF对TG的调控强度（正=激活，负=抑制）
- X ∈ R^{M×N}：标准化TF表达矩阵
- y ∈ R^M：标准化TG表达向量
- M：细胞数；N：候选TF数
- α ≥ 0：L1稀疏性正则化参数（Lasso）
- β > 0：网络正则化强度参数
- wᵢⱼ：TF i和j间的PPI权重（0<w≤1）
- dᵢ = Σₖ wᵢₖ：TF i的度（连通性）
- 第一项：数据拟合；第二项：稀疏性；第三项：网络平滑性（相连TF的系数应相似）

**式(3) SVD变换**：
(1/N)X̃^T X̃ = (1/M)X^T X + βA
(1/N)ỹ^T X̃ = (1/M)y^T X

- A = D^T(W⊙V)D：图拉普拉斯相关矩阵
- V = N·I - 11^T：常数矩阵
- D = diag(1/√d)：度归一化矩阵
- X̃ ∈ R^{N×N}：嵌入后的特征矩阵
- ỹ ∈ R^N：嵌入后的响应向量

**式(4) 等价Lasso问题**：
c* = argmin_c f̃(c) = (1/(2N))‖ỹ - X̃c‖² + α‖c‖₁

**B分数计算**：
Bᵢⱼ = 100 · Bᵢⱼ⁰ / max|B⁰|，其中 Bᵢⱼ⁰ = cos(X̃ᵢ, X̃ⱼ) · Cᵢⱼ

- Cᵢⱼ = sign(cᵢ·cⱼ)：若cᵢ和cⱼ同号则Cᵢⱼ=1（协同），异号则Cᵢⱼ=-1（拮抗）
- cos(X̃ᵢ, X̃ⱼ)：嵌入空间中TF i和j的余弦相似度
- B ∈ [-100, 100]，正值=协同，负值=拮抗

## 10 实验设计与证据链

- **数据集/群体**: 12个应用（A1-A12），覆盖3个物种：
  - 人类：hESCs（A1模拟）、HSCs（A2）、hPSCs（A5）、PBMCs 9亚型（A7）、施万细胞（A8, A11）、CNS 4细胞类型（A9）、62免疫亚型（A10）、AD 8细胞类型（A12）
  - 小鼠：mESCs（A3）、mDCs（A4）
  - 酵母：YCs（A6，11条件×12基因型）
- **规模**: 未提供统一细胞数；A1模拟100/1000细胞；A12基于80,660单核转录组（Mathys et al. 2019）
- **指标**: MSE（回归）、精确率/召回率/F1（TF-TG链接）、AUPR、AUC（分类）、JS（Jaccard相似性）、超几何检验（富集分析）
- **基线/对比方法**: 4种基准回归模型（Linear Regression, ElasticNetCV, LassoCV, RidgeCV）、GRN工具（SCENIC, GRNBoost2, RTN, RTNduals等）
- **骨干/仪器**: 未提供（计算平台未说明）
- **Oracle输入**: 模拟数据使用已知ground truth GRN（A1）；真实数据使用STRINGdb PPI、motif数据库、scATAC-seq peak-to-gene链接
- **评测协议**: 70%训练/30%测试（A1, A11-12）；交叉验证（A10 RF模型）；与gold standard GRN比较

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|-------------------|------|
| 模拟数据（A1） | NetREm能恢复已知TF-TG链接 | 6个数据集（3噪声×2细胞数），对比4种BRMs | NetREm精确率最高，TF2/TF4系数显著高于BRMs | 网络正则化能识别弱相关但生物学重要的TF | 未与所有SOTA GRN工具全面比较 | Results 3.2, Fig 2, Supp Fig S2 |
| HSCs（A2） | NetREm发现已知TF-TG关系 | 与gold standard比较 | 识别出ATF2等关键TF的调控 | PPI先验提高调控推断准确性 | 未提供定量FDR控制 | Results 3.3, Supp Table S8 |
| 施万细胞（A8, A11） | NetREm识别mSC/nmSC特异协调 | 有/无先验GRN对比 | 发现EGR2为mSC特异TF，POU3F1-EGR2协同（B̄=99.14） | 细胞类型特异的TF协调可被推断 | 未与RTNduals在B̄上定量比较 | Results 3.4-3.5, Fig 4-5 |
| AD vs Control（A12） | 疾病状态改变TF协调 | 8细胞类型，AD vs Control | 发现IRF7-STAT3在AD中从拮抗转为协同 | 疾病相关TF协调变化可被检测 | 未进行多重检验校正的严格讨论 | Results 3.6, Fig 6 |
| 与RTNduals比较 | NetREm优于RTNduals | 13个人类contexts | 10/13 contexts中NetREm有效链接比例显著更高 | PPI先验+回归优于纯表达方法 | 未报告计算时间对比 | Results 3.3, Fig 3B, Supp Table S21 |
| PPI网络鲁棒性 | NetREm对PPI输入变化稳健 | 13种不同PPI输入 | 输出B̄网络平均Spearman ρ=0.32，结果稳定 | 对PPI先验噪声具有鲁棒性 | 未测试极端PPI缺失情况 | Results 3.3, Supp Fig S14 |

## 11 结论正确解读

- **任务范围**: 本文解决的是从基因表达数据推断TF-TG调控关系和TF-TF协调关系，而非直接建模TF-DNA物理结合。NetREm的"调控"是功能层面的推断，不等同于ChIP-seq验证的物理结合。
- **Oracle/真值输入**: 模拟数据使用ground truth GRN；真实数据使用STRINGdb PPI、motif预测、scATAC-seq peak-to-gene链接作为先验。这些先验本身可能包含噪声和偏差。
- **端到端状态**: NetREm是端到端的计算流程，但依赖外部PPI数据库和可选先验GRN。输出需要实验验证。
- **算力成本**: 未报告具体计算时间；对每个TG独立求解Lasso，计算复杂度与TG数线性相关。
- **历史数据依赖**: 依赖STRINGdb等数据库的PPI注释，这些注释可能偏向研究充分的蛋白。
- **模型依赖**: 线性模型假设TF对TG的调控是加性的，无法捕捉非线性调控或剂量效应。
- **最难情况**: 低表达TF、缺乏PPI注释的TF、以及M≪N的高维场景。
- **群体/领域边界**: 验证集中在人类、小鼠、酵母；施万细胞和AD数据来自特定数据集，可能不适用于其他组织或物种。
- **不确定性**: 未提供置信区间或贝叶斯框架；B分数的统计显著性仅通过置换检验/超几何检验部分评估。

**有边界的复述**: NetREm在模拟和真实数据中，能够利用PPI先验从单细胞表达数据中推断出细胞类型特异的TF-TF协调关系（协同/拮抗）和TF-TG调控链接，其性能在多个指标上优于传统回归方法，并能发现SCENIC等工具遗漏的TF（如TEAD1）。然而，这些推断是功能层面的，需要实验验证，且依赖PPI数据库的覆盖度和准确性。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| PPI网络缺乏细胞类型特异性 | 当前使用全局PPI，无法反映细胞类型特异的蛋白相互作用 | 期待未来有更精细的细胞类型/组织特异性PPI数据 | Discussion: "most PPINs are global and organism-specific, lacking cell-type and tissue specificity" |
| 线性模型假设 | 假设TF对TG的调控是线性的 | 可考虑非线性降维方法 | Discussion: "we can incorporate nonlinear dimensionality reduction into NetREm" |
| 未考虑同源二聚化 | 模型未显式处理TF同源二聚体（如TF-TF自身相互作用） | 未来可扩展模型以处理同源二聚化 | Discussion: "we may see if any of our N* final TFs for a given TG form homodimers" |
| 依赖先验GRN质量 | A11-12中先验GRN来自多组学数据，可能包含噪声 | 未明确说明 | 未提供 |
| 计算效率 | 对每个TG独立求解，大规模应用时计算量较大 | 未明确说明 | 未提供 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| B分数的符号（协同/拮抗）仅由c*的符号决定 | 两个TF可能通过不同机制（如竞争同一结合位点 vs 协同招募）对同一TG产生相同符号的系数，但协调性质可能不同 | 过度简化TF协调的生物学复杂性 | 与ChIP-seq共结合数据或突变实验比较B符号与物理结合模式 | Results 3.2: "C_ij = sign(c_i, c_j)" |
| 模拟数据中PPI权重与ground truth高度相关 | 模拟数据可能高估了PPI先验的效用 | 真实数据中PPI噪声可能降低NetREm优势 | 在PPI权重中加入噪声扰动，测试NetREm性能下降曲线 | Results 3.2: 模拟使用已知ground truth |
| 与RTNduals的比较仅使用"有效链接比例" | 未报告召回率或FDR，可能高估NetREm优势 | 需要更全面的性能评估 | 计算并报告AUPR、召回率、FDR等指标 | Results 3.3, Fig 3B |
| 未与深度学习GRN方法（如DeepSEM、GRNBoost2+）比较 | 深度学习可能捕捉非线性调控关系 | 需要明确NetREm在方法谱系中的定位 | 在相同数据集上运行多种GRN方法进行基准测试 | 未提供 |
| 施万细胞和AD分析中缺乏独立实验验证 | 仅依赖已有ChIP-seq/eQTL数据，未进行新实验验证 | 预测的生物学意义需要实验确认 | 对Top预测进行CRISPR干扰或报告基因实验 | Results 3.4-3.6 |
| 未讨论B分数的统计不确定性 | B̄是点估计，缺乏置信区间 | 用户可能过度解读B̄的精确值 | 使用bootstrap或贝叶斯方法估计B̄的不确定性 | 未提供 |

## 14 与已有知识连接

- **网络正则化回归**: 本文直接扩展了Li & Li (2008)的图约束正则化方法，将其应用于TF-TF协调推断。可连接至graph-regularized regression、network Lasso等文献。
- **GRN推断工具谱系**: 与SCENIG (Aibar et al. 2017)、GRNBoost2 (Moerman et al. 2019)、PIDC (Chan et al. 2017)、Inferelator (Greenfield et al. 2013)等方法形成对比。本文强调PPI先验的独特价值。
- **TF协同与增强子-启动子互作**: 本文的TF-TF协调概念与增强子-启动子环化（如Hi-C、HiChIP数据）和TF共结合（ChIP-seq共定位）研究相关。可连接至转录调控的"增强子-启动子"模型。
- **单细胞多组学整合**: 本文整合scRNA-seq和scATAC-seq，与近年来的多组学GRN推断趋势一致（如SCENIC+、CellOracle）。
- **PPI网络数据库**: 使用STRINGdb (Szklarczyk et al. 2023)，可连接至HIPPIE、hu.MAP、BioGRID等资源。
- **疾病相关调控网络**: 本文的AD分析可连接至神经退行性疾病中TF调控失调的研究（如APOE、TREM2相关调控网络）。
- **与TF-DNA结合机制的直接关联** [Analysis]: 本文的TF-TF协调推断可作为TF-DNA结合研究的**功能验证层**。例如，预测的协同TF对可优先进行ChIP-seq共结合验证或电泳迁移率变动分析（EMSA）；预测的拮抗对可提示竞争性结合机制。此外，本文的PPI先验思想可迁移至**TF结合位点预测**：将TF-TF PPI作为图正则化约束，改进基于序列的TF结合预测模型。

## 15 与已有知识连接（续）

- **方法可迁移性**: NetREm的SVD+网络正则化框架可迁移至其他"特征间存在已知网络结构"的回归问题，如eQTL定位中的SNP-SNP互作、微生物组数据中的物种互作。
- **与物理模拟的潜在结合** [Analysis]: NetREm预测的TF-TF协调关系可为分子动力学（MD）模拟或蛋白-蛋白对接提供候选TF对。例如，预测的高协同TF对可进行蛋白-蛋白对接模拟，验证其物理互作可能性；预测的拮抗对可模拟竞争性DNA结合。
- **与深度学习方法的互补** [Analysis]: 深度学习GRN方法（如图神经网络）可捕捉非线性关系，但缺乏可解释性。NetREm的线性+网络正则化框架提供可解释的系数和B分数，可作为深度学习模型的解释工具或特征工程层。

## 16 研究想法

### 候选1: TF-TF协调引导的TF结合位点预测增强
- **名称**: TFCoop-Bind
- **来源局限/观察**: NetREm预测的TF-TF协调关系未被用于改进TF结合位点预测；现有结合位点预测主要基于序列motif，忽略TF间协同。
- **核心假设**: 在NetREm预测的高协同TF对中，其结合位点在增强子/启动子区域更可能共定位。
- **初步方法**: 将NetREm的B̄分数作为图正则化约束，输入到基于CNN或Transformer的TF结合位点预测模型；或在预测后处理中，对高协同TF对的共结合位点进行重加权。
- **验证方式**: 使用ChIP-seq共结合数据（如ENCODE）验证预测的协同TF对是否显著共定位；比较加入B̄先验前后的AUPR。
- **创新状态**: unverified

### 候选2: 细胞类型特异的TF-TF协调网络与3D基因组整合
- **名称**: 3D-TFCoop
- **来源局限/观察**: NetREm的B̄网络是细胞类型特异的，但未与3D基因组数据（Hi-C、HiChIP）整合；增强子-启动子互作是TF协调的物理基础之一。
- **核心假设**: 高B̄的TF对更可能通过染色质环化共同调控靶基因。
- **初步方法**: 将NetREm的B̄网络与Hi-C数据中的染色质环锚点重叠分析；构建TF-TF-增强子-启动子四维网络，识别细胞类型特异的调控模块。
- **验证方式**: 使用CRISPR干扰（CRISPRi）破坏预测的染色质环，检测靶基因表达变化；比较NetREm预测的协调TF对在环化区域中的富集程度。
- **创新状态**: unverified

### 候选3: 疾病风险SNP对TF-TF协调的扰动分析
- **名称**: SNP-TFCoop
- **来源局限/观察**: NetREm在AD中识别了疾病相关的TF协调变化，但未系统分析风险SNP如何通过改变TF结合影响TF-TF协调。
- **核心假设**: 疾病风险SNP通过改变TF结合位点，破坏或增强TF-TF协调关系，从而影响靶基因表达。
- **初步方法**: 将AD风险SNP映射到NetREm预测的TF结合区域；分析SNP是否位于高B̄ TF对的结合位点；构建SNP-TF-TF-TG调控路径。
- **验证方式**: 使用报告基因实验验证SNP对TF结合和协调的影响；比较风险SNP与非风险SNP在TF-TF协调网络中的位置。
- **创新状态**: unverified

### 候选4: NetREm与分子动力学模拟的交叉验证
- **名称**: MD-TFCoop
- **来源局限/观察**: NetREm的TF-TF协调是功能推断，缺乏物理互作证据；MD模拟可提供TF-TF或TF-DNA物理互作的原子级细节。
- **核心假设**: NetREm预测的高协同TF对具有物理互作倾向（如结合界面互补性）。
- **初步方法**: 选取NetREm预测的高协同和拮抗TF对，进行蛋白-蛋白对接（如HADDOCK、ClusPro）和短时MD模拟；比较预测的协调性质与物理互作能量。
- **验证方式**: 计算预测协同TF对的结合自由能与随机TF对的差异；使用突变实验验证关键界面残基。
- **创新状态**: unverified

### 候选5: 基于NetREm的TF-TF协调动态模型
- **名称**: TFCoop-Dyn
- **来源局限/观察**: NetREm是静态的，未建模TF-TF协调随细胞状态或时间的变化。
- **核心假设**: TF-TF协调关系是动态的，随细胞分化或疾病进展而重连。
- **初步方法**: 将NetREm应用于时间序列单细胞数据（如分化轨迹），构建动态B̄网络；使用图神经网络或动态贝叶斯网络建模协调关系的演变。
- **验证方式**: 使用谱系追踪或药物扰动实验验证预测的动态协调变化；比较动态模型与静态模型的预测准确性。
- **创新状态**: unverified