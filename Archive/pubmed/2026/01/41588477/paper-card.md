## 01 基本信息

- **标题**：Aligned cross-modal integration and regulatory heterogeneity characterization of single-cell multiomic data with deep contrastive learning
- **作者**：Cheng, Yue; Su, Yanchi; Fan, Yi; Yang, Yuning; Chen, Xingjian; Wong, Ka-Chun; Li, Xiangtao
- **单位**：未提供（基于作者信息推测可能为中国高校/研究机构，但原文未明确）
- **期刊/平台**：Genome Medicine
- **年份**：2026-01-27
- **论文类型**：方法学（Method）论文，提出新深度学习框架
- **领域**：单细胞多组学（scMulti-omics）数据整合与聚类分析
- **关键词**：单细胞多组学、对比学习、跨模态整合、调控异质性、聚类分析
- **DOI/arXiv 号**：10.1186/s13073-025-01586-7
- **代码**：未提供（原文提及"Code and reproducible workflows are openly available"，但未给出具体链接）
- **数据**：多个公开数据集，包括10X Genomics的pbmc 10x public、multiome bmmc、human brain 3k、pbmc 10k，SNARE-seq数据，CITE-seq数据（inhouse、GSE128639、spleen lymph），以及DLPFC snMulti-omics数据集（105,332 nuclei，来自AD患者和对照）
- **阅读日期**：2026-05-13
- **在课题方向中的位置**：本文属于"AI/深度学习 × 单细胞多组学"方向，聚焦于跨模态（RNA+ATAC/ADT）数据整合与聚类。与"TF–DNA结合机制"的关联在于：通过整合染色质可及性（ATAC）与基因表达数据，识别细胞类型特异的peak-gene关联和cis-regulatory elements（CREs），并进一步通过motif富集分析推断转录因子（如ELF1）在特定细胞类型（如Microglia）中的调控作用。该方法为从单细胞多组学数据中解析TF–DNA结合位点与基因调控网络提供了计算框架，可迁移至TF–DNA互作机制研究。

---

## 02 一句话总结

本文提出scMDCF，一个基于对比学习的单细胞多组学整合框架，通过跨模态对比学习模块（最大化互信息+信息熵正则化）和自优化深度嵌入聚类模块，在RNA+ATAC和RNA+ADT数据上实现优于现有方法的聚类性能，并成功识别细胞类型特异的peak-gene关联、cis-regulatory elements及候选转录因子（如Microglia中的ELF1）。

---

## 03 研究问题

- **具体问题**：如何有效整合单细胞多组学数据（如RNA+ATAC、RNA+ADT），在消除批次效应的同时保留生物学异质性，并从中提取可解释的调控信息（如peak-gene关联、CREs、转录因子调控）？
- **为什么重要**：单细胞多组学技术可同时测量同一细胞的多种模态（转录组、染色质可及性、表面蛋白），但不同模态间存在尺度、稀疏性和生物学差异，整合不当会丢失关键生物学变异或引入噪声。传统方法（如线性整合、简单拼接）难以捕捉跨模态的非线性关系和模态特异性信息。
- **现有方法不足**：
  - 统计方法（BREM-SC、MOFA+）假设模态间正相关或特定分布，无法处理负相关或复杂非线性关系；
  - 相似性矩阵融合方法（CiteFuse、Seurat V4）采用线性融合策略，可能扭曲数据固有的非线性流形结构；
  - 深度生成方法（GLUE、MultiVI、Cobolt、totalVI）依赖先验知识图或特定概率假设，且多为"黑盒"，缺乏可解释性；
  - 多数方法在类别不平衡（如稀有细胞群）时表现不佳。
- **精确研究问题**：Can a contrastive learning-based framework with cross-modality mutual information maximization and information entropy regularization effectively integrate scMulti-omics data while preserving both shared and modality-specific biological information, thereby improving clustering accuracy and enabling the identification of cell-type-specific regulatory elements and transcription factor biomarkers?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注为「仅本文框架」，未经外部系统核验。

- **第一阶段：统计方法**（BREM-SC、MOFA+）
  - 代表：BREM-SC（贝叶斯随机效应混合模型）、MOFA+（贝叶斯因子分析）
  - 优点：可解释性强，有统计保证
  - 局限：假设模态间正相关或特定分布，无法处理非线性关系；扩展性有限

- **第二阶段：相似性矩阵融合**（CiteFuse、Seurat V4）
  - 代表：CiteFuse（相似性网络融合）、Seurat V4（加权最近邻）
  - 优点：无需分布假设，计算相对简单
  - 局限：线性融合策略可能扭曲非线性流形结构；对高维稀疏数据敏感

- **第三阶段：深度生成模型**（GLUE、MultiVI、Cobolt、totalVI、scMDC）
  - 代表：GLUE（图引导VAE）、MultiVI（概率VAE）、Cobolt（层次贝叶斯VAE）、totalVI（CITE-seq专用VAE）、scMDC（多模态自编码器）
  - 优点：可扩展性强，能处理高维数据
  - 局限：依赖先验知识图或特定概率假设；多为"黑盒"，缺乏可解释性；部分方法对批次效应处理不足

- **第四阶段（本文位置）：对比学习+自优化聚类**
  - scMDCF：跨模态对比学习（互信息最大化+信息熵正则化）+ 自优化深度嵌入聚类
  - 创新点：无需负采样、无需先验知识图；通过信息熵保留模态特异性信息；自动估计聚类数；计算效率高
  - 与TF–DNA互作课题的关联：通过整合ATAC（染色质可及性）与RNA（基因表达），识别peak-gene关联和CREs，进而通过motif富集推断TF调控，为从单细胞数据中解析TF–DNA结合机制提供新工具

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 模态间尺度与分布差异 | RNA、ATAC、ADT数据维度、稀疏性、分布差异大，直接拼接效果差 | 不同组学技术测量不同生物学层面，噪声模型不同 | Methods "Data processing"节；Results 图2 |
| 模态间关系复杂（可能负相关） | 传统方法假设模态正相关，无法处理负相关或非线性关系 | 基因表达与染色质可及性并非简单正相关，存在反馈调控等复杂机制 | Background节对BREM-SC、MOFA+局限的讨论 |
| 批次效应 | 不同实验批次、组织来源导致数据偏移 | 技术差异（测序深度、平台）和生物学变异混杂 | Results 图3c（spleen lymph两批次整合）；Additional File 1: Fig. S8 |
| 稀有细胞群难以识别 | 少数细胞群（如Microglia仅占3%）被大群体掩盖 | 类别不平衡导致聚类偏向多数类 | Results 图8a；Discussion节 |
| 现有深度方法"黑盒"、缺乏可解释性 | 难以从模型中提取生物学意义 | 纯生成模型或判别模型不关注特征可解释性 | Background节对GLUE、MultiVi等的讨论 |
| 聚类数需预先指定 | 多数方法需要用户提供聚类数k | 无监督场景下k未知 | Methods "Self-optimizing multimodal deep embedded clustering"节 |
| 计算效率低 | 大规模数据（>10万细胞）下部分方法无法扩展 | 模型复杂度高或需全量数据训练 | Results 图S6（运行时间对比） |

---

## 06 核心思想

### 1) 表面方法
scMDCF是一个端到端的深度学习框架，包含三个核心模块：
- **多组学信息编码器**：分别对RNA和ATAC/ADT数据使用独立的编码器（多层全连接+BN+ReLU），提取模态特定特征；
- **跨模态对比学习模块**：通过最大化两个模态特征之间的互信息（使用InfoNCE的变体，但无需负采样），同时最大化各模态的信息熵，以保留模态特异性信息；
- **跨模态特征融合模块**：将对比学习后的特征拼接，通过非线性融合网络映射到公共低维空间；
- **自优化深度嵌入聚类模块**：使用KL散度对齐软分配与目标分布，自动优化聚类。

### 2) 核心洞察
- **对比学习优于拼接或生成式整合**：通过最大化互信息而非简单拼接，能更好地捕捉跨模态的共享信息，同时避免模态间尺度差异的干扰；
- **信息熵正则化保留异质性**：单纯最大化互信息可能导致模态特异性信息丢失，通过最大化信息熵可防止表示坍缩，保留每个模态的独特生物学特征；
- **自优化聚类避免人为指定k**：通过KL散度自举方式自动确定聚类数，适应无标注数据场景。

### 3) 可能的普适教训 [Analysis]
- 在整合异质数据源时，"共享+特有"的分离策略（对比学习捕捉共享、熵正则化保留特有）比单纯追求一致性更有效；
- 无监督聚类中，通过分布对齐（KL散度）而非固定k值，可提高对稀有群体的识别能力；
- 可解释性可通过下游分析（如motif富集、peak-gene关联）而非模型本身实现，这为"黑盒"模型提供了生物学验证路径。

---

## 07 方法总览

- **输入**：预处理后的单细胞多组学数据矩阵，包括RNA表达矩阵（X_omic1，n×m）和ATAC/ADT矩阵（X_omic2，n×p），其中n为细胞数，m为基因数，p为peak数或ADT数
- **输出**：细胞的低维公共表示（Z，n×z）及聚类标签
- **模块**：
  1. 多组学信息编码器（RNA编码器、ATAC/ADT编码器）
  2. 跨模态对比学习模块（互信息最大化+信息熵正则化）
  3. 跨模态特征融合模块（非线性融合网络）
  4. 自优化深度嵌入聚类模块（KL散度）
  5. 多组学重建解码器（分别重建各模态）
- **训练**：
  - 预训练阶段：优化重建损失 + 对比学习损失（γ=0.1）
  - 聚类阶段：优化KL散度损失 + 重建损失 + 对比学习损失（η=0.1, β=10, μ=5）
- **工具**：PyTorch（推测，原文未明确）；Seurat、ArchR、Signac、Monocle3、CellChat用于下游分析
- **反馈回路**：聚类结果通过KL散度反馈到编码器，迭代优化表示
- **假设**：不同模态来自同一细胞，存在共享的生物学信息；模态特异性信息可通过熵正则化保留

**文字流程**：
1. 预处理各模态数据，选择高变基因/peak
2. 分别通过RNA编码器和ATAC/ADT编码器提取模态特定特征
3. 跨模态对比学习模块计算互信息损失和信息熵损失，优化编码器
4. 将两个模态的特征拼接，通过非线性融合网络得到公共表示Z
5. 在Z上应用自优化聚类（KL散度），迭代更新聚类中心和编码器
6. 通过解码器重建各模态数据，确保信息不丢失
7. 输出聚类标签和低维表示，供下游分析（如peak-gene关联、motif富集）

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 多组学信息编码器 | 分别提取RNA和ATAC/ADT的模态特定特征 | 不同模态数据分布差异大，需独立编码 | 输入：预处理矩阵；输出：模态特定嵌入 | Methods节；Results 图2（聚类性能） | [预期] 直接拼接原始数据会导致尺度差异主导表示，聚类性能下降 |
| 跨模态对比学习模块 | 最大化两个模态特征间的互信息，同时最大化信息熵 | 捕捉跨模态共享信息，同时保留模态特异性 | 输入：两个模态的嵌入；输出：对比损失+熵损失 | Methods节；Results 图4g（消融实验） | [实测] 移除后聚类性能下降（图4g），表明对比学习对整合至关重要 |
| 跨模态特征融合模块 | 将模态特定特征拼接并映射到公共低维空间 | 融合共享和特有信息，得到统一表示 | 输入：拼接特征；输出：公共表示Z | Methods节；Results 图2c（UMAP） | [预期] 移除后无法获得统一表示，下游分析（如peak-gene关联）无法进行 |
| 自优化深度嵌入聚类 | 通过KL散度自动确定聚类数并优化聚类 | 避免人为指定k，适应无标注数据 | 输入：公共表示Z；输出：聚类标签 | Methods节；Results 图8a（AD数据聚类） | [预期] 移除后需人为指定k，可能遗漏稀有群体（如Microglia） |
| 多组学重建解码器 | 从公共表示重建各模态数据 | 确保公共表示保留足够信息 | 输入：公共表示Z；输出：重建的模态矩阵 | Methods节；预训练损失定义 | [预期] 移除后表示可能丢失模态特有信息，影响下游分析 |
| 信息熵正则化 | 最大化各模态嵌入的信息熵 | 防止表示坍缩，保留模态特异性 | 输入：模态嵌入；输出：熵损失 | Methods节；Results 图4e（λ参数分析） | [预期] 移除后表示可能坍缩到少数模式，丢失异质性 |

---

## 09 关键公式符号

1. **编码器变换**（每个堆叠块）：
   Z_omic1 = φ(φ(X_omic1 W_omic1 + b_omic1))
   - Z_omic1：RNA模态的潜在表示（n×d）
   - X_omic1：预处理后的RNA表达矩阵（n×m）
   - W_omic1：权重矩阵（m×d）
   - b_omic1：偏置
   - φ：ReLU激活函数
   - φ：BatchNorm1d归一化
   - 用途：RNA模态特征提取
   - 来源：Methods "Multi-omics informed encoder"节，公式(1)

2. **对称编码器**（ATAC/ADT）：
   Z_omic2 = φ(φ(X_omic2 W_omic2 + b_omic2))
   - 符号含义同上，对应ATAC或ADT模态
   - 来源：Methods节，公式(3)

3. **互信息**（对比学习目标）：
   I(Z_omic1, Z_omic2) = Σ Σ P(z_omic1, z_omic2) log[P(z_omic1, z_omic2) / (P(z_omic1)P(z_omic2))]
   - I：互信息
   - P(z_omic1, z_omic2)：联合概率分布
   - P(z_omic1)、P(z_omic2)：边缘概率分布
   - 用途：衡量两个模态共享的信息量，最大化以捕捉跨模态一致性
   - 来源：Methods "Cross-modality contrastive learning"节，公式(4)

4. **信息熵**：
   H(Z_omic) = -Σ P(z_omic) log P(z_omic)
   - H：信息熵
   - 用途：最大化以保留模态特异性信息，防止表示坍缩
   - 来源：Methods "Cross-modality contrastive learning"节，公式(6)-(7)

5. **对比学习损失**：
   L_cl = -Σ [I(Z_omic1, Z_omic2) + α(H(Z_omic1) + H(Z_omic2))]
   - α：平衡参数
   - 用途：联合优化互信息和信息熵
   - 来源：Methods节，公式(8)

6. **重建损失**（MSE）：
   L_rec^omic = MSE(X_omic, X_hat_omic) = (1/n) Σ (X_omic - X_hat_omic)²
   - X_hat_omic：重建的模态矩阵
   - 用途：确保公共表示保留足够信息
   - 来源：Methods "Multi-omics reconstruction decoder"节，公式(10)-(11)

7. **KL散度聚类损失**：
   L_kl = KL(P||Q) = Σ Σ p_ij log(p_ij / q_ij)
   - q_ij：软分配（学生t分布）
   - p_ij：目标分布（q_ij的平方归一化）
   - 用途：自优化聚类
   - 来源：Methods "Self-optimizing multimodal deep embedded clustering"节，公式(12)-(14)

8. **总损失**：
   L_total = η L_rec^omic1 + β L_rec^omic2 + μ L_cl + L_kl
   - η=0.1, β=10, μ=5
   - 用途：联合优化所有模块
   - 来源：Methods "Joint optimization"节，公式(16)

---

## 10 实验设计与证据链

### 数据集与规模
| 数据集 | 模态 | 规模 | 用途 |
|--------|------|------|------|
| pbmc 10x public | RNA+ATAC | 未明确 | 聚类基准测试 |
| multiome bmmc | RNA+ATAC | 未明确 | 聚类基准测试 |
| human brain 3k | RNA+ATAC | 未明确 | 聚类基准测试 |
| pbmc 10k | RNA+ATAC | 未明确 | 聚类基准测试 |
| inhouse | RNA+ADT | 1,372细胞 | CITE-seq聚类 |
| GSE128639 | RNA+ADT | 30,672细胞 | CITE-seq聚类（人骨髓） |
| spleen lymph | RNA+ADT | 16,282细胞（两批次） | CITE-seq聚类+批次效应 |
| DLPFC snMulti-omics | RNA+ATAC | 105,332 nuclei | AD疾病应用 |
| Sanger数据集 | RNA+ATAC | 647,366细胞（用于运行时间测试） | 可扩展性测试 |

### 指标
- 聚类：NMI、ARI、AMI、V-measure、Homogeneity（有标注数据）
- 无标注数据：ASW、DB、CH指数
- 批次效应：iLISI、cLISI、batchKL

### 基线方法
- 多组学：scMDC、GLUE、MultiVI、Cobolt、Seurat-V4 WNN、MOFA+、scMoMA、FigR
- 单组学RNA：scDeepCluster、scziDesk
- 单组学ATAC：SCALE

### 实验表格
| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 4个RNA+ATAC数据集聚类 | scMDCF优于现有多组学方法 | 与10种方法对比，5个指标 | scMDCF在多数指标上最优 | 对比学习整合优于拼接或生成式方法 | 未报告统计显著性检验 | Results 图2a |
| 3个CITE-seq数据集聚类 | scMDCF在RNA+ADT上同样有效 | 与6种方法对比 | scMDCF在多数指标上最优 | 方法可泛化至不同组学组合 | 未报告统计显著性检验 | Results 图3a |
| spleen lymph批次效应 | scMDCF能有效消除批次效应 | iLISI、cLISI、batchKL | scMDCF在iLISI上最优 | 对比学习有助于批次整合 | 未报告cLISI和batchKL的具体数值 | Results 图3c；Additional File 1: Fig. S8 |
| 运行时间对比 | scMDCF计算效率高 | 647,366细胞，逐步增加 | scMDCF运行时间最短 | 适合大规模数据 | 未报告具体时间数值 | Additional File 1: Fig. S6 |
| 消融实验（移除对比学习模块） | 对比学习模块对性能至关重要 | 有/无对比学习模块 | 移除后聚类性能下降 | 对比学习是核心组件 | 未报告具体下降幅度 | Results 图4g |
| 消融实验（移除融合模块） | 融合模块对性能有贡献 | 有/无融合模块 | 移除后性能下降 | 融合模块必要 | 未报告具体下降幅度 | Results 图4g |
| 超参数分析（λ、损失权重、基因数） | 模型对超参数敏感度 | 不同λ、权重方案、基因数 | 找到最优配置 | 模型可调优 | 未报告所有组合结果 | Results 图4a-e |
| SNARE-seq peak-gene关联 | scMDCF能识别有意义的peak-gene关联 | 与已知marker基因/peak对比 | 识别出细胞类型特异的peak-gene关联 | 整合分析可揭示调控关系 | 未与实验验证数据对比 | Results 图5 |
| AD数据稀有群体识别 | scMDCF能识别稀有细胞群 | 与Seurat不同分辨率对比 | 识别出Microglia（3%）和Endothelial（0.24%） | 自优化聚类优于固定分辨率 | 未报告其他方法是否也能识别 | Results 图8a；Additional File 1: Fig. S21-27 |
| ELF1 motif富集 | scMDCF能推断TF调控 | motif富集分析 | ELF1在Microglia中显著富集 | 识别出候选TF biomarker | 未进行实验验证 | Results 图8c-e |

---

## 11 结论正确解读

- **任务范围**：本文聚焦于单细胞多组学数据的**无监督聚类**和**整合表示学习**，而非监督分类或回归任务。结论仅适用于无标注场景下的细胞类型识别。
- **oracle/真值输入**：聚类评估使用了数据集的真实细胞类型标签（如pbmc 10x public等），但模型本身不依赖标签训练。AD数据集的细胞类型注释基于marker基因/peak。
- **端到端状态**：scMDCF是端到端训练的，但下游分析（peak-gene关联、motif富集）依赖外部工具（ArchR、Signac），并非模型直接输出。
- **算力成本**：原文未报告训练时间、GPU型号等具体算力信息。仅报告了运行时间对比（图S6），显示scMDCF在647,366细胞规模下运行时间最短，但未给出绝对数值。
- **历史数据依赖**：模型依赖预处理步骤（标准化、高变基因/peak选择），不同预处理可能影响结果。消融实验（图S9）显示标准化方案对性能有影响。
- **模型依赖**：结果依赖于超参数选择（λ、损失权重、基因数等），最优配置通过网格搜索确定，但未报告搜索范围。
- **最难情形**：从结果看，scMDCF在稀有细胞群（Microglia 3%、Endothelial 0.24%）识别上表现突出，但这是否在所有数据集上成立未验证。批次效应处理在spleen lymph数据集上有效，但仅测试了两批次场景。
- **群体/领域边界**：结论基于血液（PBMC、骨髓）和脑组织（DLPFC）数据，是否适用于其他组织类型（如肿瘤、肠道）未验证。方法针对RNA+ATAC和RNA+ADT两种组合，其他模态组合（如RNA+甲基化）未测试。
- **不确定性**：ELF1作为AD相关Microglia转录因子biomarker的结论是**计算预测**，未经实验验证（如ChIP-seq、siRNA敲低等）。peak-gene关联基于相关性，不证明因果关系。

**有边界的复述**：scMDCF在测试的4个RNA+ATAC和3个RNA+ADT数据集上，在无监督聚类任务中优于现有方法，并能从整合表示中识别细胞类型特异的peak-gene关联和候选TF（如ELF1），但这些发现需要实验验证。

---

## 12 作者自认局限

在提供的材料中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限）：
- 原文在Discussion节提到"Future enhancements of scMDCF are planned to accommodate emerging multi-omics data types"，暗示当前版本可能不直接支持所有多组学数据类型。
- 原文未明确讨论方法对数据质量、dropout率、模态缺失等实际问题的鲁棒性。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 聚类性能提升幅度未报告具体数值 | 原文仅以图表展示，未给出NMI/ARI等指标的绝对数值和标准差 | 无法评估提升是否具有实际意义 | 查阅原文图表数据或补充材料 | Results 图2a、3a |
| 未报告统计显著性检验 | 多次实验、多种方法对比，但未说明差异是否显著 | 性能差异可能来自随机性 | 要求作者提供重复实验的统计检验结果 | Results 图2a、3a |
| 消融实验仅报告"移除后下降" | 未报告下降的具体幅度和统计显著性 | 无法判断各模块的相对贡献 | 查阅图4g的详细数据 | Results 图4g |
| ELF1结论基于计算预测 | 未进行实验验证（如ChIP-seq、qPCR、免疫组化） | 计算预测可能为假阳性 | 设计实验验证ELF1在AD Microglia中的表达和功能 | Results 图8c-e |
| peak-gene关联基于相关性 | 相关性不等于因果关系，可能存在混杂因素 | 调控关系的推断可能不准确 | 使用CRISPR干扰或报告基因实验验证 | Results 图5 |
| 数据集规模未明确报告 | 多个数据集仅给出细胞数（如1,372、16,282、105,332），但未报告peak数、基因数、稀疏度等 | 影响方法适用性评估 | 查阅补充材料 | Methods "Data processing"节 |
| 未与其他最新深度学习方法（如scDART、scMoMaT的改进版）对比 | 对比方法可能未覆盖最新进展 | 性能优势可能被高估 | 补充与最新方法的对比实验 | Results 图2a、3a |
| 批次效应评估仅用spleen lymph两批次数据 | 单数据集、两批次场景不足以证明通用性 | 批次效应处理能力可能被高估 | 在多批次、多组织数据集上验证 | Results 图3c |
| 运行时间对比未报告具体数值 | 仅以图展示，无法评估绝对效率 | 实际应用中的计算成本不明确 | 查阅图S6数据 | Additional File 1: Fig. S6 |
| 未讨论方法对dropout率、模态缺失的鲁棒性 | 单细胞数据常存在高dropout和模态缺失 | 实际数据中的表现可能下降 | 设计模拟实验或使用含缺失模态的数据集测试 | 全文未提及 |

---

## 14 与已有知识连接

- **对比学习在单细胞领域的应用**：本文的跨模态对比学习与**scDART**（对比学习+图注意力）、**scMoMaT**（矩阵分解）等方法同属单细胞多组学整合方向，但本文创新性地将互信息最大化与信息熵正则化结合，避免了负采样需求。
- **与TF–DNA互作研究的连接**：本文通过整合ATAC-seq（染色质可及性）与RNA-seq（基因表达）识别peak-gene关联和CREs，这与**SCENIC**（基于motif的基因调控网络推断）、**cisTopic**（主题模型识别CREs）等方法互补。本文的聚类结果可作为这些下游分析的前置步骤。
- **与转录因子结合机制研究的连接**：本文在AD数据中识别出ELF1作为Microglia候选TF biomarker，ELF1属于ETS转录因子家族，已知参与免疫调控。这一发现与**TF–DNA结合机制**研究（如ChIP-seq、SELEX、HT-SELEX）可形成"计算预测→实验验证"的闭环。
- **与深度学习架构的连接**：本文的编码器-解码器架构与**autoencoder**家族（如scVI、scVAE）一脉相承，但通过对比学习增强了跨模态对齐能力，与**CLIP**（跨模态对比学习）思想类似。
- **与批次效应处理的连接**：本文的批次效应处理与**Harmony**、**BBKNN**等经典方法不同，后者基于图或概率模型，本文通过对比学习隐式对齐批次。
- **可迁移至TF–DNA互作课题**：
  1. **跨模态整合策略**：可将scMDCF的对比学习框架迁移至"蛋白质序列（氨基酸）↔ DNA序列（核苷酸）"的跨模态对齐，用于预测TF–DNA结合特异性；
  2. **peak-gene关联方法**：本文的peak-gene关联分析流程（ArchR + Signac）可直接用于TF–DNA互作研究中的cis-regulatory element注释；
  3. **motif富集流程**：本文的motif富集分析（JASPAR + chromVAR）是TF–DNA结合机制研究的标准工具，可复用；
  4. **稀有群体识别**：本文对稀有细胞群（Microglia）的识别能力提示，在TF–DNA互作研究中可关注稀有细胞类型特异的TF调控。

---

## 15 与已有知识连接（续）

- **与AlphaFold/Rosetta等结构预测工具的连接**：本文未涉及蛋白质结构预测，但其识别出的TF（如ELF1）可作为结构预测的输入，用于研究TF–DNA结合的结构基础。
- **与分子动力学（MD）模拟的连接**：本文的TF–peak关联预测可作为MD模拟的初始候选体系，验证TF–DNA结合的动态过程。
- **与ChIP-seq等实验数据的连接**：本文的预测结果（如ELF1 motif富集）可与公共ChIP-seq数据库（ENCODE、Cistrome）交叉验证，增强结论可信度。
- **与单细胞ATAC-seq分析工具（如SnapATAC、ArchR）的连接**：本文的预处理和peak-gene关联流程与这些工具兼容，可无缝集成。

---

## 16 研究想法

### 候选1：基于对比学习的TF–DNA结合特异性预测
- **名称**：ContrastiveTF-DNA
- **来源局限/观察**：scMDCF证明对比学习能有效整合RNA和ATAC模态；TF–DNA结合预测通常依赖序列特征（如PWM、CNN），但缺乏跨模态（蛋白质结构+DNA序列）整合
- **核心假设**：通过对比学习对齐TF蛋白质序列/结构嵌入与DNA序列嵌入，可捕捉TF–DNA结合的共享模式，提高结合位点预测精度
- **初步方法**：将TF氨基酸序列和DNA序列分别编码，使用对比学习最大化正样本对（已知结合的TF-DNA对）的互信息，同时用信息熵正则化保留TF和DNA的特异性特征
- **验证方式**：在公共数据集（ENCODE ChIP-seq、HT-SELEX）上评估AUC、PRC，与现有方法（DeepBind、DeepSEA）对比
- **创新状态**：unverified

### 候选2：单细胞多组学数据中的TF调控网络推断增强
- **名称**：scMDCF-GRN
- **来源局限/观察**：scMDCF能识别细胞类型特异的peak-gene关联和TF motif，但未构建完整的基因调控网络（GRN）
- **核心假设**：将scMDCF的聚类结果和peak-gene关联作为先验，可提高GRN推断的准确性，特别是对稀有细胞类型
- **初步方法**：在scMDCF聚类基础上，结合TF motif富集和peak-gene关联，使用回归或互信息方法构建细胞类型特异的GRN，并与SCENIC对比
- **验证方式**：在已知调控关系的基因集上评估AUROC，或与实验验证的调控关系对比
- **创新状态**：unverified

### 候选3：TF–DNA结合机制中的"共享+特有"特征分离
- **名称**：TF-DNA-Separation
- **来源局限/观察**：scMDCF的核心思想是"共享+特有"分离（对比学习捕捉共享、熵正则化保留特有）；TF–DNA结合中，不同TF家族可能有共享的结合机制（如螺旋-转角-螺旋结构域）和特有的结合偏好（如特定碱基接触）
- **核心假设**：将TF–DNA结合特征分解为共享（家族水平）和特有（TF水平）两部分，可提高结合特异性预测的可解释性和精度
- **初步方法**：设计双分支网络，一个分支学习TF家族共享的DNA结合模式，另一个分支学习TF特异的结合偏好，通过对比学习+熵正则化联合优化
- **验证方式**：在TF–DNA结合数据集上评估预测精度，并可视化共享/特有特征对应的序列motif
- **创新状态**：unverified

### 候选4：从单细胞ATAC-seq数据推断TF结合动态
- **名称**：scATAC-TFDynamics
- **来源局限/观察**：scMDCF在AD数据中识别出Microglia特异的ELF1 motif，提示单细胞染色质可及性数据可反映TF结合的细胞类型特异性
- **核心假设**：通过整合单细胞ATAC-seq的peak可及性和TF motif信息，可推断TF结合活性的动态变化（如疾病状态下的变化）
- **初步方法**：在scMDCF聚类基础上，计算每个细胞类型中TF motif的可及性得分，结合伪时间分析（Monocle3）推断TF结合活性的动态轨迹
- **验证方式**：与已知的AD相关TF调控变化对比，或使用独立数据集验证
- **创新状态**：unverified

### 候选5：跨模态对比学习用于TF–DNA共结合预测
- **名称**：CoBindingCL
- **来源局限/观察**：scMDCF的跨模态对比学习可整合不同组学数据；TF–DNA共结合（多个TF协同结合同一调控区域）是基因调控的重要机制
- **核心假设**：通过对比学习对齐多个TF的序列特征和DNA序列特征，可预测TF共结合位点
- **初步方法**：将多个TF的序列嵌入和DNA序列嵌入作为多模态输入，使用对比学习最大化共结合位点的跨模态一致性
- **验证方式**：在共结合ChIP-seq数据集上评估预测精度
- **创新状态**：unverified