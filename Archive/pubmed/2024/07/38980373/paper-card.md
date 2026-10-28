## 01 基本信息

- **标题**：DeepGRNCS: deep learning-based framework for jointly inferring gene regulatory networks across cell subpopulations
- **作者**：Lei, Yahui; Huang, Xiao-Tai; Guo, Xingli; Hang Katie Chan, Kei; Gao, Lin
- **单位**：未提供（根据作者信息推测为中国高校/研究机构，具体单位未在摘要中列出）
- **期刊/平台**：Briefings in Bioinformatics
- **年份**：2024
- **论文类型**：方法学（Method）论文
- **领域**：计算生物学 / 基因调控网络推断 / 单细胞转录组学 / 深度学习
- **关键词**：gene regulatory network (GRN); scRNA-seq; deep learning; cell subpopulations; transcription factors (TFs)
- **DOI/arXiv 号**：10.1093/bib/bbae334
- **代码**：https://github.com/Nastume777/DeepGRNCS
- **数据**：模拟数据（JEGN、BoolEE 生成）；真实数据（BEELINE 六个数据集；NSCLC 患者 scRNA-seq 数据，http://lungcancer.chenlulab.com）
- **阅读日期**：未提供
- **在「蛋白质-DNA 互作 × AI/物理模拟」方向中的位置**：该文属于「TF–DNA 结合机制」下游的 GRN 推断任务，核心假设是 TF 表达可预测靶基因表达（即 TF 调控靶基因）。方法为深度学习（前馈神经网络），不涉及物理模拟或结构预测。其可迁移价值在于：① 将 TF 作为调控因子显式建模；② 跨细胞亚群联合推断 GRN 的思路可迁移到 TF–DNA 结合位点预测或 TF 活性推断任务中。

---

## 02 一句话总结

DeepGRNCS 提出一个基于深度前馈神经网络的框架，利用多个细胞亚群的 scRNA-seq 数据联合推断亚群特异的基因调控网络（GRN），通过逐一"敲除"每个 TF 并比较预训练模型预测靶基因表达的误差变化来量化 TF–靶基因调控权重，在模拟和真实数据集上优于现有方法。

---

## 03 研究问题

- **具体问题**：如何从 scRNA-seq 数据中联合推断多个细胞亚群各自的 GRN，同时利用亚群间的共享信息？
- **为什么重要**：组织中存在多种细胞亚群，每个亚群有独特的调控网络。单独推断每个亚群的 GRN 会忽略亚群间的相似性，而将所有细胞合并推断又会掩盖亚群特异性调控。准确推断亚群特异 GRN 有助于理解细胞分化、疾病异质性（如肿瘤）的调控机制。
- **现有方法不足**：
  - 传统方法（相关性、互信息、贝叶斯网络、回归等）多针对单一 GRN，忽略细胞亚群结构；
  - 联合图模型方法（如 JEGN、SRMDG、NETI2）假设数据服从高斯分布，而 scRNA-seq 数据通常不符合该假设；
  - 现有深度学习方法（如 DeepSEM）未显式利用 TF 作为调控因子的生物学先验，也未利用亚群间共享信息。
- **精确研究问题（Can...?）**：Can a deep learning framework that jointly leverages expression data from multiple cell subpopulations and explicitly models TF-to-target-gene regulation outperform existing single-GRN and joint-GRN inference methods on simulated and real scRNA-seq data?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论，属于「仅本文框架」的梳理，未经外部系统核验。

| 阶段 | 代表性方法 | 优点 | 局限 |
|------|-----------|------|------|
| 第一代：统计关联 | 相关性分析、互信息（PIDC）、贝叶斯网络 | 计算简单、可解释 | 无法捕捉非线性调控、噪声敏感、忽略方向性 |
| 第二代：回归/方程 | GENIE3、GRNBoost2、SINCERITIES、SOCDE | 可处理非线性、部分方法利用拟时序 | 多为单 GRN 推断，忽略亚群结构；SINCERITIES/SOCDE 依赖拟时序信息 |
| 第三代：联合图模型 | JEGN、SRMDG、NETI2 | 同时推断多个亚群 GRN，利用共享信息 | 假设高斯分布，与 scRNA-seq 数据分布不符；未区分 TF 与靶基因 |
| 第四代：深度学习 | DeepSEM、CNNC | 可拟合复杂非线性关系 | DeepSEM 未利用亚群共享信息；CNNC 需构造概率矩阵、计算量大 |
| **本文位置** | **DeepGRNCS** | **联合多亚群 + 显式 TF 先验 + 无先验信息** | **需亚群标签；需足够细胞数；逐基因训练模型计算开销大** |

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 忽略细胞亚群异质性 | 单一 GRN 无法反映不同亚群的特异调控 | scRNA-seq 数据天然包含多种细胞类型/状态，各亚群调控网络不同 | Introduction 第 3 段："Tissues consist of various cell types, resulting in diverse cell subpopulations... each subpopulation characterized by unique GRNs" |
| 独立推断亚群 GRN 丢失共享信息 | 每个亚群单独推断时样本量不足、噪声大 | 亚群间存在共享调控机制，独立推断未利用这些信息 | Introduction 第 3 段："these methods may miss shared information within data from the same source when inferring GRNs for each cell subpopulation independently" |
| 高斯分布假设不成立 | 联合图模型方法（JEGN 等）在 scRNA-seq 上表现不佳 | scRNA-seq 数据通常服从负二项分布，而非高斯分布 | Introduction 第 3 段："these methods assume that data follow a Gaussian distribution, which is not always accurate because scRNA-seq data typically follow a negative binomial distribution" |
| 忽略 TF 的生物学角色 | 所有基因被平等对待，未利用 TF 作为调控因子的先验 | 真实调控网络中 TF 是主要调控者，靶基因是被调控者 | Introduction 第 3 段："these methods assume that all nodes have an equal probability of being connected, overlooking the fact that transcription factors (TFs) typically regulate other genes or TFs in real gene networks" |
| 深度模型输入信息损失 | SIGNET 使用二值化输入，丢失表达量信息 | 二值化无法区分表达水平差异 | Introduction 第 4 段："we used the raw expression data of TFs as input data, thereby preserving a higher amount of feature information than the deep model" |

---

## 06 核心思想

### 1) 表面方法

DeepGRNCS 是一个三阶段框架：
- **预处理**：将 scRNA-seq 数据按细胞亚群划分，TF 表达作为输入（原始值），靶基因表达经 log 归一化 + 等宽离散化后作为分类标签；
- **训练**：对每个靶基因训练一个深度前馈神经网络，网络由"主网络"（primary subpopulation 数据）和"配对网络"（其他亚群数据）组成，联合预测靶基因表达；
- **推断**：逐一将每个 TF 的表达置零（模拟敲除），用预训练模型重新预测靶基因表达，计算误差变化率作为调控权重，构建 GRN。

### 2) 核心洞察

- **跨亚群联合建模**：不同亚群共享部分调控机制，通过"主网络 + 配对网络"结构同时利用目标亚群和其他亚群的数据，既保留亚群特异性又利用共享信息；
- **TF 先验**：显式将 TF 作为输入特征、靶基因作为输出，符合"TF 调控靶基因"的生物学方向性；
- **无先验的因果推断**：通过 in silico 敲除（将 TF 表达置零）模拟扰动实验，避免依赖已知调控关系或网络拓扑先验；
- **原始表达量优于二值化**：保留 TF 表达的连续值信息，比 SIGNET 的二值化输入包含更多调控信息。

### 3) 可能的普适教训 [Analysis]

- **"扰动后预测误差"作为关联度量**：这一思路可迁移到 TF–DNA 结合预测——例如训练模型预测 TF 结合后靶基因表达变化，再通过 in silico 突变 TF 结合位点来评估结合贡献；
- **多任务/多条件联合建模**：在 TF–DNA 互作预测中，不同细胞类型/条件的 ChIP-seq 数据可类比为不同亚群，联合建模可提升泛化能力；
- **生物学先验约束网络结构**：将"TF 调控靶基因"的方向性先验嵌入模型架构（而非仅作为后处理），可减少搜索空间、提升可解释性。

---

## 07 方法总览

- **输入**：scRNA-seq 表达矩阵（细胞 × 基因），细胞亚群标签；TF 列表（需预先指定）
- **输出**：每个细胞亚群的 GRN（TF–靶基因调控权重矩阵）
- **模块**：
  1. 数据预处理模块（log 归一化、等宽离散化）
  2. 深度预测网络（Network Main + Network Pair）
  3. 调控权重计算模块（in silico 敲除 + Z-score 标准化）
- **训练**：对每个靶基因独立训练一个网络；损失函数为交叉熵；优化器为 Adam；隐藏层 8 节点 + ReLU + 归一化
- **工具**：PyTorch，GPU 加速
- **反馈回路**：无显式反馈回路（非迭代优化）
- **假设**：
  1. TF 表达可预测靶基因表达（存在调控关系）；
  2. 不同亚群间存在共享调控机制；
  3. 将 TF 表达置零可模拟其功能缺失；
  4. 需要预先知道哪些基因是 TF。

**文字流程**：
1. 输入 scRNA-seq 矩阵和亚群标签 → 2. 将基因分为 TF 和靶基因 → 3. 对每个靶基因 g：用主亚群 TF 表达训练 Network Main，用其他亚群 TF 表达训练 Network Pair → 4. 训练完成后，逐一将每个 TF 表达置零，重新预测靶基因 g 的表达 → 5. 计算预测误差变化率（公式 3）→ 6. 用 Z-score 标准化得到调控权重（公式 4）→ 7. 重复步骤 3-6 得到所有靶基因的调控权重 → 8. 构建每个亚群的 GRN。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 数据预处理（等宽离散化） | 将靶基因连续表达值转为离散标签 | 将回归问题转为分类问题，适配交叉熵损失 | 输入：靶基因表达向量；输出：离散标签 | Methods "Data preprocessing" 节 | [预期] 移除后需改用回归损失，可能影响训练稳定性；离散化可能丢失部分定量信息 |
| Network Main | 从主亚群 TF 表达预测靶基因表达 | 学习主亚群特异的调控关系 | 输入：主亚群 TF 表达矩阵；输出：靶基因表达预测 | Methods "The deep neural network" 节；图 1A | [预期] 移除后模型无法学习亚群特异调控 |
| Network Pair | 从其他亚群 TF 表达辅助预测主亚群靶基因 | 利用亚群间共享调控信息提升预测精度 | 输入：其他亚群 TF 表达矩阵；输出：靶基因表达预测 | Methods "The deep neural network" 节；图 1A | [预期] 移除后退化为单亚群模型，丢失共享信息（作者在 Introduction 中强调这是与单亚群方法的关键区别） |
| In silico 敲除 + 误差计算 | 逐一将 TF 置零，比较预测误差 | 量化每个 TF 对靶基因的调控贡献 | 输入：预训练模型 + 修改后的 TF 矩阵；输出：误差变化率 | Methods "Prediction of the relationship between genes" 节；图 1B | [预期] 移除后无法计算调控权重，无法构建 GRN |
| Z-score 标准化 | 将误差率标准化为可比权重 | 不同靶基因的误差率量纲不同，需标准化 | 输入：误差率向量；输出：标准化权重 | Methods 公式 4 | [预期] 移除后不同基因间权重不可直接比较 |

---

## 09 关键公式符号

| 公式 | 符号含义 | 用途 | 直觉 | 来源 |
|------|----------|------|------|------|
| 公式 1（预处理）：M_g,c 经 log 归一化 + 等宽离散化 | M_g,c：基因 g 在细胞 c 中的表达值；C_k：亚群 k 的细胞数 | 将连续表达值转为离散标签 | 通过 log 压缩动态范围，等宽分箱将连续值映射为整数类别 | Methods "Data preprocessing" 节 |
| 公式 2（预测）：X_g = f(TF 表达) | X_g：基因 g 的表达向量；f：深度网络学到的非线性函数 | 建模 TF 表达到靶基因表达的映射 | 深度网络拟合未知非线性调控函数 | Methods "The deep neural network" 节 |
| 公式 3（误差率）：err_h,g = 1 - acc_h,g | acc_h,g：敲除 TF h 后模型预测基因 g 的准确率 | 量化 TF h 对基因 g 的调控强度 | 若 TF h 调控 g，敲除后预测准确率下降，误差率升高 | Methods "Prediction of the relationship between genes" 节 |
| 公式 4（Z-score）：Weight_h,g = (err_h,g - mean(err_g)) / σ(err_g) | err_g：所有 TF 对基因 g 的误差率向量；mean/σ：均值和标准差 | 标准化误差率得到可比权重 | 将误差率转为标准分数，便于跨基因比较 | Methods "Prediction of the relationship between genes" 节 |

---

## 10 实验设计与证据链

### 数据集与设置

| 数据集 | 类型 | 规模 | 用途 |
|--------|------|------|------|
| 模拟数据（JEGN 生成） | 50 基因、4 亚群 | 每亚群 1000 细胞 | 与联合图模型方法对比 |
| 模拟数据（JEGN 生成） | 100 基因、4 亚群 | 每亚群 2000 细胞 | 与联合图模型方法对比 |
| 模拟数据（BoolODE 生成） | BF/BFC/TF 网络 | 每网络 3 亚群、每亚群 1000 细胞 | 与单 GRN 推断方法对比 |
| 真实数据（BEELINE） | hESC, hHEP, mDC, mHSC-E, mHSC-GM, mHSC-L | 见表 1（原文） | 与单 GRN 推断方法对比 |
| 真实数据（NSCLC） | LUAD AT2 细胞、LUSC 基底细胞 | 见表 2（原文） | 生物学应用验证 |

### 指标
- AUROC（area under the receiver operating characteristic curve）
- AUPRC（area under the precision-recall curve）
- EPR（early precision ratio）
- F1-score

### 基线方法
- 联合图模型：JEGN、SRMDG、NETI2、DKGN
- 单 GRN 推断：PIDC、GENIE3、SINCERITIES、SOCDE、DeepSEM、GRNBoost2、MI

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| 模拟数据（JEGN）对比 | DeepGRNCS 优于联合图模型方法 | 50/100 基因、4 亚群；对比 JEGN/SRMDG/NETI2/DKGN | AUROC 平均高 2.8%，AUPRC 平均高 1.3%（vs 次优 SRMDG） | DeepGRNCS 在模拟数据上优于联合图模型方法 | 提升幅度有限，且仅在特定模拟设置下验证 | Results 图 2A-B |
| 模拟数据（BoolODE）对比 | DeepGRNCS 优于单 GRN 方法 | BF/BFC/TF 网络；对比 PIDC/GENIE3/SINCERITIES/SOCDE | AUROC 高 1.8-2.5%，AUPRC 高 25.8-27.6%（vs 次优） | DeepGRNCS 利用亚群共享信息优于单 GRN 方法 | 模拟网络结构可能与真实调控有差异 | Results 图 2C-D |
| 真实数据（BEELINE）对比 | DeepGRNCS 在真实数据上优于基线 | 6 个数据集；对比 DeepSEM/MI/GRNBoost2/GENIE3/DKGN | AUPRC 平均高 25.5%（vs 次优）；mHSC-GM 数据集上低于 DKGN 3.8% | DeepGRNCS 在多数真实数据集上表现最佳 | 在个别数据集上并非最优 | Results 图 2E-F |
| 亚群数量影响 | 增加亚群数量提升性能 | 模拟数据；1/2/3/4 亚群 | 3 亚群时最优，AUROC/AUPRC 提升 1.4%/7.2%（vs 1 亚群） | 适度增加亚群可提升推断精度 | 亚群过多可能引入噪声 | Results 图 3A |
| 离散化方法对比 | 等宽离散化优于其他方法 | 模拟数据；等宽 vs 等频 vs K-means | 等宽离散化 AUROC 高 2.8%（vs 次优） | 等宽离散化更适合该任务 | 仅在一个模拟设置下验证 | Results 图 3B |
| NSCLC 应用 | DeepGRNCS 能识别疾病相关关键基因 | LUAD AT2 恶性/非恶性；LUSC 早/晚期基底细胞 | 识别出 ELF3、HOPX、SOX4 等已知 LUAD 相关基因；晚期基底细胞基因与 DNA 修复、EMT 相关 | DeepGRNCS 推断的 GRN 具有生物学意义 | 未与实验验证（如 ChIP-seq、敲除实验）直接对比 | Results 图 4-5 |

---

## 11 结论正确解读

- **任务范围**：该文解决的是 GRN 推断问题，即从 scRNA-seq 表达数据中推断 TF–靶基因的调控关系。**不是** TF–DNA 结合位点预测，**不是** 三维结构建模，**不是** 物理模拟。
- **输入要求**：需要预先知道细胞亚群标签和 TF 列表。若亚群标签未知或 TF 列表不完整，方法无法直接使用。
- **真值/基准**：模拟数据的真值来自 JEGN 和 BoolODE 生成的已知网络；真实数据使用 BEELINE 提供的 ChIP-seq 衍生网络作为 ground truth。这意味着评估依赖于 ChIP-seq 数据的质量与覆盖度。
- **端到端状态**：方法端到端可运行（输入表达矩阵 → 输出 GRN），但需要亚群标签作为额外输入。
- **算力成本**：对每个靶基因需单独训练一个深度网络，基因数增加时计算开销线性增长。作者在讨论中承认此局限。
- **数据依赖**：需要足够细胞数（模拟中每亚群 1000-2000 细胞）；当细胞数少于基因数时性能显著下降（图 S2）。
- **最难场景**：细胞数少、基因数多、亚群数量过多或过少时性能下降。
- **边界复述**：DeepGRNCS 在模拟和真实 scRNA-seq 数据上，对"给定亚群标签和 TF 列表、细胞数充足"的 GRN 推断任务，优于所对比的基线方法；但其优势在个别数据集（如 mHSC-GM）上不成立，且未在蛋白质-DNA 结合机制层面提供直接验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 需要亚群分类信息 | 方法要求预先知道细胞亚群标签 | 未明确提及 | Discussion 第 1 段（"The method requires the categorization information of cellular subpopulations"） |
| 需要大量细胞样本 | 细胞数过少时训练不充分，影响精度 | 期待 scRNA-seq 技术进步提供大规模数据 | Discussion 第 1 段（"DeepGRNCS needs a large number of cell samples to train the deep model"） |
| 逐基因训练计算开销大 | 基因数增加导致运行时间线性增长 | 建议聚焦生物学显著基因或差异表达基因 | Discussion 第 2 段（"An increase in the number of genes leads to an increase in the runtime"） |
| 敲除策略可能混淆直接与间接调控 | 逐一敲除 TF 可能无法区分直接和间接调控关系 | 需更好的模型可解释性分析方法 | Discussion 第 2 段（"might obscure direct and indirect regulatory relationships"） |
| 深度模型缺乏可解释性 | 模型内部机制不透明 | 探索自编码器等替代模型 | Discussion 第 2 段（"many deep models lack transparency"） |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 模拟数据中 TF/靶基因区分是预设的 | 模拟数据已知哪些基因是 TF，真实数据中 TF 列表可能不完整 | 若 TF 列表不完整，推断的 GRN 会遗漏关键调控边 | 在 TF 列表随机删减的情况下测试性能下降程度 | Methods "Datasets" 节 |
| 敲除策略将 TF 表达置零可能不反映真实生物学 | 真实调控中 TF 活性受翻译后修饰、核定位等影响，mRNA 表达量不等于 TF 活性 | 若表达量不能代表 TF 活性，则"表达预测"的前提不成立 | 与 TF 蛋白丰度或 ChIP-seq 结合强度数据对比 | Methods "Prediction of the relationship between genes" 节 |
| 与基线方法对比的公平性 | DeepGRNCS 使用了亚群标签和 TF 先验，而部分基线方法（如 PIDC、GENIE3）未使用这些信息 | 性能提升可能部分来自额外信息而非方法本身 | 在相同输入条件下对比（如给基线方法也提供亚群标签） | Results 图 2 |
| 真实数据评估依赖 ChIP-seq ground truth | ChIP-seq 网络本身有噪声和不完整性，可能偏向某些方法 | 评估基准的偏差可能影响结论可靠性 | 使用多种 ground truth（如 CRISPR 筛选、eQTL）交叉验证 | Results "real datasets" 节 |
| 未报告计算时间/资源消耗 | 逐基因训练深度网络的计算成本未量化 | 实际应用中基因数可达数万，计算可行性存疑 | 报告不同基因数下的运行时间和 GPU 需求 | 全文未提供 |
| 未与其他深度 GRN 方法（如 GraphSAGE-based、GNN-based）对比 | 仅对比了传统方法和 DeepSEM | 无法判断在深度学习方法中的相对位置 | 增加与 GNN、Transformer-based GRN 方法的对比 | Results 图 2 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **TF 先验嵌入架构**：将"TF 调控靶基因"的方向性先验直接嵌入网络输入输出设计（TF 为输入特征、靶基因为预测目标），而非作为后处理约束。可迁移到 TF–DNA 结合预测：以 TF 表达 + DNA 序列特征为输入，预测结合位点或结合强度。

2. **In silico 扰动作为关联度量**：通过逐一移除输入特征并观察预测误差变化来量化特征重要性，是一种无需梯度/注意力权重的归因方法。可迁移到 TF–DNA 结合机制研究：对 DNA 序列的每个位置或 motif 进行 in silico 突变，观察结合预测变化，识别关键碱基。

3. **跨条件联合建模**：利用多个细胞亚群/条件的共享信息提升单条件预测精度，通过"主网络 + 辅助网络"结构实现。可迁移到 TF–DNA 结合预测：不同细胞类型的 ChIP-seq 数据可联合建模，共享 TF 结合 motif 信息，提升低质量数据条件下的预测。

4. **离散化将回归转分类**：将连续表达值离散化为类别标签，使问题适配分类损失函数。可迁移到结合强度预测：将连续 ChIP-seq 信号离散化为"强/弱/无结合"类别，简化学习目标。

5. **无先验的调控推断流程**：整个推断过程不依赖已知调控关系、基因注释或网络拓扑，仅依赖表达数据和 TF 列表。可迁移到新物种/新细胞类型的 TF–DNA 结合预测，减少对先验知识的依赖。

6. **Z-score 标准化跨基因比较**：对每个靶基因的误差率向量做 Z-score 标准化，使不同基因的调控权重可比。可迁移到多 TF 结合强度比较：对不同 TF 的结合分数做标准化，便于跨 TF 比较。

---

## 15 与已有知识连接

- **与 SIGNER 的关系**：本文明确受 SIGNER 启发（Introduction 第 4 段），但改进在于：① 使用原始表达而非二值化输入；② 联合多亚群数据。SIGNER 是单 GRN 推断方法，DeepGRNCS 是其多亚群扩展。
- **与联合图模型（JEGN、SRGMG、NETI2）的关系**：这些方法用高斯图模型联合估计多个网络，本文用深度学习替代图模型，避免高斯假设。
- **与 BEELINE 基准的关系**：BEELINE 是 GRN 推断领域公认的基准框架，本文使用其模拟和真实数据集及评估协议，结果可与该领域大量方法直接对比。
- **与 TF–DNA 结合机制的联系**：本文的"TF 表达预测靶基因表达"假设隐含了 TF–DNA 结合 → 转录调控的因果链。其推断出的 GRN 边可视为 TF–DNA 结合的功能性下游证据，可与 ChIP-seq 结合位点数据互补。
- **与深度学习可解释性的联系**：本文的 in silico 敲除策略与特征归因方法（如 permutation importance、occlusion analysis）思想一致，可视为一种模型无关的可解释性工具。
- **[Analysis] 候选连接**：本文的跨亚群联合建模思路与多任务学习、元学习在生物信息学中的应用相关；其"扰动→预测误差"策略与 CRISPR 干扰筛选的 in silico 版本类似，可探索与实验扰动数据的结合。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：TF–DNA 结合位点预测的跨细胞类型联合建模
- **名称**：CrossCell-TFBind
- **来源局限/观察**：DeepGRNCS 证明跨亚群联合建模可提升 GRN 推断精度；类似地，不同细胞类型的 ChIP-seq 数据存在共享的 TF 结合 motif，但现有模型多为单细胞类型训练。
- **核心假设**：跨细胞类型联合训练可提升 TF 结合位点预测，尤其在 ChIP-seq 数据稀疏的细胞类型中。
- **增量**：将 DeepGRNCS 的"主网络 + 配对网络"结构迁移到序列-结合预测任务，以 DNA 序列 + 染色质可及性为输入，预测 TF 结合。
- **初步方法**：对每个 TF，主网络处理目标细胞类型序列，辅助网络处理其他细胞类型序列，联合预测结合概率。
- **验证方式**：ENCODE 多细胞类型 ChIP-seq 数据，留一细胞类型交叉验证。
- **创新状态**：unverified

### 候选 2：基于 in silico 序列扰动的 TF–DNA 结合 motif 发现
- **名称**：InSilicoMut-Footprint
- **来源局限/观察**：DeepGRNCS 用 in silico 基因敲除识别调控边；类似地，对 DNA 序列进行 in silico 点突变可识别对 TF 结合关键的碱基位置。
- **核心假设**：对预训练结合预测模型做系统性序列扰动，可恢复已知 TF 结合 motif，并发现新 motif。
- **增量**：将"特征扰动→预测变化"从基因表达域迁移到序列域，提供一种无需梯度/注意力的 motif 发现方法。
- **初步方法**：对每个序列位置逐一突变，计算预测结合分数变化，构建"突变敏感性谱"，聚类识别 motif。
- **验证方式**：与 MEME、DeepBind 等 motif 发现工具对比，用已知 motif 数据库（JASPAR）评估。
- **创新状态**：unverified

### 候选 3：TF 表达与 DNA 序列特征的融合模型用于结合强度预测
- **名称**：TFExpr-SeqBind
- **来源局限/观察**：DeepGRNCS 仅用 TF 表达预测靶基因表达，未利用 DNA 序列信息；而 TF–DNA 结合同时受 TF 丰度和序列亲和力影响。
- **核心假设**：融合 TF 表达水平和 DNA 序列特征可提升结合强度预测精度，优于仅用序列或仅用表达。
- **增量**：将 DeepGRNCS 的表达驱动框架与序列-based 结合预测模型（如 DeepBind、BPNet）结合。
- **初步方法**：双编码器架构——序列编码器提取 motif 特征，表达编码器提取 TF 丰度特征，融合后预测结合强度。
- **验证方式**：同一细胞类型中 ChIP-seq 信号与 TF 表达 + 序列的联合预测，与单模态模型对比。
- **创新状态**：unverified

### 候选 4：亚群特异 TF 调控网络的差异分析框架
- **名称**：DiffSubNet
- **来源局限/观察**：DeepGRNCS 输出每个亚群的 GRN，但未提供亚群间网络差异的统计检验方法。
- **核心假设**：亚群间 GRN 边的权重差异可量化，且差异显著的边对应关键细胞状态转换调控因子。
- **增量**：在 DeepGRNCS 输出上增加差异网络分析模块，识别亚群特异调控边。
- **初步方法**：对每个 TF–靶基因边，比较不同亚群的权重分布（bootstrap 或贝叶斯方法），计算差异显著性。
- **验证方式**：在 NSCLC 数据上验证差异边是否富集已知癌症相关通路。
- **创新状态**：unverified

### 候选 5：将物理模拟（MD/对接）与 DeepGRNCS 推断的调控边整合
- **名称**：GRN-MD-Integrator
- **来源局限/观察**：DeepGRNCS 推断的调控边缺乏物理层面的验证；TF–DNA 结合机制可通过 MD 模拟或结构预测验证。
- **核心假设**：对 DeepGRNCS 推断的高权重 TF–靶基因边，若 TF 与靶基因启动子区域存在物理结合可能性（通过 MD/对接评估），则边的可信度更高。
- **增量**：将统计推断（DeepGRNCS）与物理模拟（MD/对接）结合，形成"统计-物理"双重验证框架。
- **初步方法**：对高权重边，提取 TF 结构（AlphaFold）与靶基因启动子序列，用 MD 模拟或分子对接评估结合自由能，作为边的物理可信度评分。
- **验证方式**：在已知 TF–DNA 复合物结构数据上验证评分有效性，再应用于 DeepGRNCS 输出。
- **创新状态**：unverified