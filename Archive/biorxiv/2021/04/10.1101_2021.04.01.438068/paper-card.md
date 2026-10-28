## 01 基本信息

- **标题**：Learning single-cell chromatin accessibility profiles using meta-analytic marker genes
- **作者与单位**：Kawaguchi RK; Tang Z; Fischer S; Rajesh C; Tripathy R; Koo PK; Gillis J（Cold Spring Harbor Laboratory；Gillis 现属 University of Toronto）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2021-04-03
- **论文类型**：方法学/基准评测研究（含深度学习应用）
- **领域**：单细胞表观基因组学（scATAC-seq）、细胞类型注释、调控基因组学
- **关键词**：scATAC-seq、meta-analytic marker genes、cell-type annotation、chromatin accessibility、deep learning、motif analysis
- **DOI/arXiv 号**：10.1101/2021.04.01.438068
- **代码**：https://github.com/carushi/Catactor
- **数据**：https://gillisweb.cshl.edu/Meta_scATAC/（Meta scATAC-seq server）
- **阅读日期**：未提供
- **在「蛋白质-DNA 互作 × AI/物理模拟」方向中的位置**：本文不直接研究 TF–DNA 结合机制，而是聚焦 scATAC-seq 数据的细胞类型注释。其核心贡献在于：(1) 提出 meta-analytic marker gene 集合（MetaMarkers 方法），证明冗余 marker 基因的简单聚合即可实现稳健的细胞类型分类；(2) 训练序列深度 CNN 预测细胞类型特异的染色质可及性，并通过 motif 分析（JASPAR 比对、TF-MoDISCo）识别细胞类型特异的 TF 结合基序。对 TF–DNA 结合课题的可迁移点在于：marker 基因选择策略可迁移至 TF 靶基因集构建；CNN 可及性预测与 motif 归因方法可直接用于 TF 结合位点发现。

---

## 02 一句话总结

本文通过系统比较 7 个小鼠脑 scATAC-seq 数据集，证明基于多数据集整合的冗余 meta-analytic marker 基因集（SF）的简单信号聚合即可实现与机器学习分类器相当或更优的细胞类型注释性能，并进一步训练序列 CNN 预测细胞类型特异染色质可及性，通过 motif 分析揭示细胞类型特异的 TF 结合基序。

---

## 03 研究问题

- **具体问题**：scATAC-seq 数据因高稀疏性（二倍体基因组仅 2 个拷贝）、跨数据集协议异质性（sci-ATAC-seq、snATAC-seq、Paired-seq 等）以及 dropout 问题，导致细胞类型注释困难。本文要解决的核心问题是：**如何从 scATAC-seq 数据中稳健、可重复地进行细胞类型注释，并进一步挖掘细胞类型特异的调控信息？**
- **为什么重要**：scATAC-seq 是识别顺式调控元件（增强子、TF 结合位点）的关键技术，但细胞类型注释的准确性直接决定下游调控分析的可靠性。脑组织包含数百种细胞类型，注释错误将导致调控元件归因错误。
- **现有方法不足**：(1) 基于聚类的方法（如 Seurat、BBSCAN）依赖数据集内部结构，跨数据集泛化差；(2) 监督学习方法需要高质量训练标签，且特征选择（单基因 vs. 全基因）对性能影响大；(3) 单基因 marker 易受 dropout 影响，缺乏稳健性；(4) 不同研究间 marker 基因定义不一致，缺乏统一标准。
- **精确研究问题（Can...?）**：Can meta-analytic marker gene sets（从多个 scRNA-seq 数据集中整合的冗余 marker 基因）enable robust and reproducible cell-type annotation of scATAC-seq data across heterogeneous protocols, and can sequence-based deep learning further extract cell-type-specific regulatory motifs from the annotated profiles?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注「仅本文框架」；涉及外部文献处标注「经外部核验」。

1. **scATAC-seq 技术发展（经外部核验）**：ATAC-seq 通过 Tn5 转座酶插入识别开放染色质区域 [2]；单细胞版本（sci-ATAC-seq、snATAC-seq、Paired-seq 等）实现单细胞分辨率可及性检测 [1, 12, 17, 18, 37, 38]。
2. **细胞类型注释方法演进（仅本文框架）**：
   - 早期：基于聚类 + 已知 marker 基因人工注释，依赖先验知识，跨数据集不可迁移。
   - 中期：监督学习（SVM、随机森林、逻辑回归）应用于基因活性矩阵，需训练标签，特征选择敏感。
   - 联合聚类方法（Seurat、BBKNN）：整合多数据集，但计算成本高，对协议差异敏感。
   - 本文主张：**marker 基因选择策略比分类算法更重要**——冗余、meta-analytic 的 marker 集合（SF）使简单聚合即可超越复杂模型。
3. **序列深度学习预测染色质可及性（经外部核验）**：Basset [24]、DeepSea [25] 等 CNN 架构已证明可从 DNA 序列预测可及性/调控活性。本文将其应用于细胞类型特异的 pseudo-bulk 可及性预测，并结合 TF-MoDISCo [31] 进行 motif 发现。
4. **MetaMarkers 方法（仅本文框架）**：基于多 scRNA-seq 数据集的共表达分析，扩展 marker 基因集合以包含共表达基因，增加冗余性，降低 dropout 影响。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| scATAC-seq 数据高稀疏性 | 单细胞可及性信号接近二元（0/1/2），单基因信息量低 | 二倍体基因组仅 2 个拷贝，技术 dropout 率高 | Results 2.2 节：单基因 AUROC 仅 0.5–0.6（Supplementary Fig. 4A） |
| 跨数据集协议异质性 | 不同研究（sci-ATAC-seq、snATAC-seq、Paired-seq）的细胞数、聚类数、注释粒度差异大 | 实验协议、测序深度、生物样本差异 | Results 2.1 节：7 个数据集聚类数从 9 到 36 不等（Fig. 1C-D） |
| 单基因 marker 不稳健 | 单个 marker 基因易因 dropout 丢失信号，跨数据集重现性差 | 技术噪声 + 基因表达随机性 | Results 2.3 节：单基因 AUROC 跨数据集 Spearman 相关性低（Supplementary Fig. 5） |
| 监督学习依赖训练标签 | 跨数据集训练时，标签定义不一致导致性能下降 | 不同研究对细胞类型的定义和粒度不同 | Results 2.6 节：RNA atlas 训练的性能低于 Consensus 训练（Fig. 4A） |
| 聚类粒度限制注释分辨率 | 聚类数少时无法区分亚型（如 Pvalb、Vip） | 聚类参数选择影响分辨率 | Results 2.1 节：部分数据集仅注释到 major type（IN/EX/NN） |
| 基因活性与转录组不完全对应 | 基因活性评分（gene activity score）与 RNA 表达存在偏差 | 可及性 ≠ 表达，增强子调控复杂 | Results 2.2 节：基因活性与 scRNA-seq 相关性有限（Supplementary Fig. 3A-D） |

---

## 06 核心思想

### 1) 表面方法
- 收集 7 个小鼠脑 scATAC-seq 数据集（含 BICCN、Cusanovich、Lareau、Chen、Zhu、Preissl 等），统一处理为基因活性矩阵。
- 构建 5 种 marker 基因集：SF（meta-analytic，含共表达基因）、CU（scATAC-seq 来源）、TA、TN（scRNA-seq 来源）、SC（SF 子集，大小与 CU 匹配）。
- 评估 3 类注释方法：raw signal aggregation（简单聚合）、ML classifiers（SVM、RF、Logistic、Alternate Lasso）、joint clustering（Seurat、BBKNN）。
- 用 BICCN 数据训练序列 CNN（Basset 类架构）预测细胞类型特异可及性，并用 TF-MoDISCo 进行 motif 发现。

### 2) 核心洞察
- **Marker 基因的冗余性比分类算法复杂度更重要**：SF 集合（包含共表达基因，冗余度高）使简单聚合方法达到或超过复杂 ML 分类器性能。
- **Meta-analytic 整合优于单一数据集来源**：从多个 scRNA-seq 数据集整合的 marker 集合跨数据集泛化能力更强。
- **特征选择（marker 基因选择）是决定注释性能的主导因素**，而非分类器选择或训练策略。
- **"净化"后的细胞类型特异 pseudo-bulk 可及性谱可有效训练 CNN**，且 motif 分析能揭示细胞类型特异的 TF 结合基序。

### 3) 可能的普适教训 [Analysis]
- 在稀疏高噪声的单细胞数据中，**增加特征冗余性**（通过共表达扩展）比增加模型复杂度更有效——这一原则可能适用于其他单细胞模态（如 scRNA-seq、scDNA methylation）。
- **跨数据集 meta-analytic 整合**是提高泛化能力的通用策略，尤其当单一数据集样本量有限时。
- 对 TF–DNA 结合课题的启示：**TF 靶基因集合的构建可借鉴 meta-analytic 思路**——从多个 ChIP-seq/perturbation 数据集中整合 TF 靶基因，增加冗余性以提高下游分析稳健性。

---

## 07 方法总览

- **输入**：
  - 7 个 scATAC-seq 数据集（BICCN、Cusanova、Lareau、Chen、Zhu、Preissl 等）的 read count 矩阵
  - 5 个 marker 基因集（SF、CU、TA、TN、SC）
  - BICCN scRNA-seq 数据（作为训练参考）
  - 参考基因组 GRCm38（mm10）
- **输出**：
  - 细胞类型注释（major type: IN/EX/NN；subtype: Sst、Pvalb、Sncg、Vip、Lamp5 等）
  - 细胞类型特异的 pseudo-bulk 可及性谱
  - CNN 预测的可及性谱及 motif 富集结果
- **模块**：
  1. 数据预处理：read count → 基因活性（TSS ± 10kb 聚合）
  2. Marker 基因集构建：MetaMarkers 方法（基于多 scRNA-seq 共表达分析）
  3. 注释方法：raw signal aggregation / ML classifiers / joint clustering
  4. 评估：AUROC、Spearman 相关
  5. CNN 训练：Basset 类架构，5kb 序列输入，多任务分类
  6. 可解释性：filter 可视化、saliency map、TF-MoDISCo motif 发现
- **训练**：
  - ML classifiers：scikit-learn 实现，SVM（rbf kernel, degree=3）、RF（n_estimators=100）、Logistic（C=1.0）、Alternate Lasso（top 5 predictors, weight 1/n）
  - CNN：mini-batch SGD（batch=100），Adam 优化，初始学习率 0.001，学习率衰减因子 0.3（验证集 Pearson 相关 7 轮无提升时），早停（25 轮无提升）
  - 数据划分：训练集（除 chr 1,3,5,7,9 外所有染色体）、验证集（chr 7,9；N=24,908）、测试集（chr 1,3,5；N=14,670）
- **反馈回路**：CNN 预测性能（AUPR）反馈至模型选择；motif 富集结果反馈至生物学验证
- **假设**：
  - 基因活性评分（TSS 附近 read 聚合）可近似反映基因调控状态
  - 共表达基因可作为 marker 的冗余扩展
  - 5kb 序列窗口足以捕获调控元件信息

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| MetaMarkers（SF 集合构建） | 从多 scRNA-seq 数据集中整合 marker 基因及其共表达伙伴 | 增加 marker 冗余性，降低 dropout 影响，提高跨数据集泛化 | 输入：6 个 scRNA-seq 数据集；输出：SF marker 集合 | Results 2.4 节：SF 在多数数据集上 AUROC 最高（Fig. 3B）；SF 与 SC 对比显示冗余性贡献（Fig. 3B-C） | **实测**：SF 替换为 SC（同大小非冗余）后 AUROC 显著下降（Fig. 3B-C）；**预期**：移除共表达扩展将导致稀疏数据下 marker 信号丢失 |
| 基因活性计算 | 将 read count 转换为基因水平活性分数 | scATAC-seq 原始信号稀疏，需聚合到基因水平 | 输入：read count 矩阵；输出：基因活性矩阵 | Methods 节：TSS ± 10kb 聚合 | **预期**：窗口过小会丢失远端调控信息，过大引入噪声 |
| Raw signal aggregation | 对 marker 基因活性求和/平均，直接预测细胞类型 | 无需训练数据，简单可解释 | 输入：基因活性矩阵 + marker 集；输出：细胞类型分数 | Results 2.4 节：SF + raw aggregation 达到 AUROC 0.8–0.9（Fig. 3B） | **实测**：在部分数据集上优于 ML 方法（Fig. 4A）；**预期**：移除将失去无监督基线 |
| ML classifiers | 监督学习分类器（SVM、RF、Logistic、Alternate Lasso） | 评估特征选择与分类器复杂度的相对贡献 | 输入：基因活性矩阵 + 标签；输出：细胞类型预测 | Results 2.6 节：Consensus 训练优于 RNA atlas 训练（Fig. 4A）；Alternate Lasso + SF 进入 top 10（Fig. 4B） | **实测**：分类器选择对性能影响小于 marker 集选择（Fig. 4A-D）；**预期**：移除将无法评估特征选择 vs. 模型复杂度 |
| Joint clustering（Seurat/BBKNN） | 整合多数据集进行联合聚类和标签迁移 | 评估无监督整合方法的性能 | 输入：多数据集基因活性矩阵；输出：联合聚类标签 | Results 2.6 节：BBKNN/Seurat 性能低于 raw aggregation + SF（Fig. 4A） | **实测**：在异质数据集上性能不稳定；**预期**：移除不影响主要结论 |
| CNN（Basset 类） | 从 DNA 序列预测细胞类型特异可及性 | 探索序列决定性的调控编码 | 输入：5kb DNA 序列；输出：多任务可及性预测 | Results 2.7 节：AUPR 0.539，优于 DeepSea 的 0.444（Fig. 5A） | **预期**：移除将失去序列-可及性关系建模能力 |
| TF-MoDISCo + saliency | 从 CNN 中提取 motif 并分析细胞类型特异性 | 将黑盒模型转化为可解释的 TF 结合信息 | 输入：CNN 梯度/激活；输出：motif 富集结果 | Results 2.7 节：识别出细胞类型特异的 motif 组合（Fig. 5F） | **预期**：移除将无法连接序列预测与 TF 结合机制 |

---

## 09 关键公式符号

本文方法以评测和流程为主，无核心数学公式。以下为隐含的评分/评估公式：

1. **基因活性评分**（Gene activity score）：
   \[
   G_i = \sum_{j \in \text{features within } \pm 10\text{kb of TSS}_i} c_j
   \]
   其中 \( c_j \) 为 feature \( j \) 的 read count，\( G_i \) 为基因 \( i \) 的活性分数。

2. **Jaccard index**（marker 集合与 cluster 特异基因重叠度）：
   \[
   J(M, C) = \frac{|M \cap C|}{|M \cup C|}
   \]
   其中 \( M \) 为 marker 基因集，\( C \) 为 cluster 特异基因集。

3. **AUROC**（Area Under the Receiver Operating Characteristic Curve）：用于评估细胞类型分类性能，基于真阳性率（TPR）与假阳性率（FPR）的积分。

4. **AUPR**（Area Under the Precision-Recall Curve）：用于评估 CNN 可及性预测性能，基于精确率（Precision）与召回率（Recall）的积分。

5. **Saliency map**（梯度归因）：
   \[
   S = \left| \frac{\partial y_c}{\partial x} \right|
   \]
   其中 \( y_c \) 为类别 \( c \) 的预测分数，\( x \) 为输入序列的 one-hot 编码。

---

## 10 实验设计与证据链

### 数据集与规模
- **7 个 scATAC-seq 数据集**：BICCN（sci-ATAC-seq，6,278 细胞，含 scRNA-seq 参考）、Cusanovich、Lareau、Chen（Paired-seq）、Zhu（Paired-seq）、Preissl 等。细胞数从数百到 110,000+ 不等。
- **5 个 marker 基因集**：SF（meta-analytic，~200 基因/类型）、CU（scATAC-seq 来源）、TA、TN（scRNA-seq 来源）、SC（SF 子集，大小与 CU 匹配）。
- **CNN 数据**：BICCN 数据，5kb 序列 bin，训练集 N=274,689，验证集 N=24,908（chr 7,9），测试集 N=14,670（chr 1,3,5）。

### 指标
- 细胞类型注释：AUROC（major type: IN/EX/NN；subtype: 5 种抑制性神经元）
- 跨数据集泛化：Spearman 相关系数（单基因 AUROC 跨数据集一致性）
- CNN 预测：AUPR（平均跨细胞类型）

### 评测协议
- 注释方法：raw signal aggregation、4 种 ML classifiers、2 种 joint clustering 方法
- 训练策略：Consensus（用其他 6 个数据集训练，测试第 7 个）、RNA atlas（用 BICCN scRNA-seq 训练）、RNA（用同一数据集的 scRNA-seq 训练）
- 消融：SF vs SC（控制 marker 数量）、不同 marker 集对比

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 单基因 AUROC 分布 | 单个基因预测能力有限 | 7 个数据集，IN/EX/NN 分类 | 多数基因 AUROC 0.5–0.6 | 单基因信息量低，需聚合 | 未测试所有基因组合 | Results 2.2 节，Fig. 2B |
| Marker 集 + raw aggregation 跨数据集 | SF 集合跨数据集稳健 | 5 种 marker 集 × 7 数据集 | SF 在多数数据集 AUROC 最高（0.8–0.9） | 冗余 marker 集合提高泛化 | 未在所有 subtype 上验证 | Results 2.4 节，Fig. 3B |
| SF vs SC（数量匹配） | 冗余性贡献 | SF（含共表达）vs SC（同大小非冗余） | SF 显著优于 SC | 共表达扩展增加冗余性，提升性能 | 未测试其他冗余策略 | Results 2.4 节，Fig. 3C |
| ML classifiers vs raw aggregation | 特征选择 vs 模型复杂度 | 4 种 ML × 5 marker 集 × 7 数据集 | raw aggregation + SF 进入 top 10；ML 未一致超越 | 特征选择（marker 集）比分类器更重要 | 未测试深度学习分类器 | Results 2.6 节，Fig. 4A-D |
| Consensus vs RNA atlas 训练 | 训练数据来源影响 | Consensus（scATAC-seq）vs RNA atlas（scRNA-seq） | Consensus 训练普遍更优 | 同模态训练数据更有效 | 未测试多模态联合训练 | Results 2.6 节，Fig. 4A |
| CNN 可及性预测 | 序列可预测细胞类型特异可及性 | Basset 类 CNN vs DeepSea | CNN AUPR 0.539 vs DeepSea 0.444 | 细胞类型特异可及性具有序列决定性 | 未与随机序列基线比较 | Results 2.7 节，Fig. 5A |
| TF-MoDISCo motif 发现 | CNN 可提取细胞类型特异 motif | 3 种抑制性神经元亚型（Lamp5、Vip、Sncg） | 识别共享和独特的 motif（NFIC、MYOG、DBP、FOSL1 等） | 序列预测可连接 TF 结合机制 | 未进行 wet-lab 验证 | Results 2.7 节，Fig. 5F |

---

## 11 结论正确解读

- **任务范围**：本文结论仅适用于小鼠脑组织的 scATAC-seq 细胞类型注释，以及基于 BICCN 数据训练的 CNN 可及性预测。不适用于其他物种、组织或非脑细胞类型。
- **oracle/真值输入**：细胞类型标签来自各数据集作者提供的注释（基于聚类 + marker 基因人工判断），非独立验证的 ground truth。CNN 训练标签来自 BICCN 的 pseudo-bulk 可及性（阈值 0.02 二值化）。
- **端到端状态**：本文的注释流程（marker 集 + raw aggregation）是端到端可用的；但 CNN 预测 + motif 分析是独立模块，未与注释流程形成闭环。
- **算力成本**：未报告具体训练时间或硬件需求。CNN 为 Basset 类架构，规模中等，预计单 GPU 可训练。
- **历史数据依赖**：SF marker 集基于 BICCN 的 6 个 scRNA-seq 数据集构建，存在对 BICCN 数据质量的依赖。跨数据集验证显示一定泛化能力，但未在非脑组织验证。
- **模型依赖**：CNN 仅用 BICCN 数据训练，未验证跨数据集预测性能。motif 发现依赖 JASPAR 数据库的完整性。
- **最难情形**：跨数据集注释时，协议差异大的数据集（如 Cusanovich、Zhu）性能下降明显；亚型分类（如 Pvalb）比 major type 分类更难。
- **群体/领域边界**：结论限于小鼠脑组织；人类或其他物种需重新构建 marker 集。
- **不确定性**：CNN 预测的 AUPR 0.539 表明仍有大量假阳性/假阴性；motif 富集未进行实验验证，存在假阳性风险。

**有边界的复述**：在小鼠脑组织的 7 个 scATAC-seq 数据集中，基于多数据集整合的冗余 marker 基因集（SF）的简单信号聚合，在 major type（IN/EX/NN）和部分亚型分类上达到或超过机器学习分类器的性能；基于 BICCN 数据训练的序列 CNN 可预测细胞类型特异可及性（AUPR 0.539），且 motif 分析能识别已知和潜在的细胞类型特异 TF 结合基序。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 基因活性与转录组不完全对应 | 基因活性评分忽略远端增强子调控，与 RNA 表达存在偏差 | 未明确提及 | Results 2.2 节（隐含） |
| 数据集异质性限制 | 部分数据集（如 Cusanovich、Zhu）与其他数据集相关性低，跨数据集泛化受限 | 未明确提及 | Results 2.3 节，Supplementary Fig. 5 |
| CNN motif 发现的局限性 | 36% filter 匹配已知 motif，大量 filter 无对应已知 motif；JASPAR 数据库不完整 | 未明确提及 | Results 2.7 节 |
| 亚型分类精度有限 | Pvalb 亚型 AUROC 较低（0.755），亚型间区分困难 | 未明确提及 | Results 2.5 节，Fig. 3D |
| 依赖已有注释 | 使用作者提供的注释作为真值，可能继承其错误 | 未明确提及 | Results 2.1 节（隐含） |
| 未进行实验验证 | motif 富集和 CNN 预测未通过 wet-lab 实验验证 | 未明确提及 | 全文（隐含） |

> 注：作者在 Discussion 中未设独立「Limitations」小节，以上为从全文提取的明确或隐含局限。作者明确承认的局限较少，主要集中于数据集异质性和 motif 匹配率。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| SF marker 集与测试数据集可能存在重叠 | SF 基于 BICCN scRNA-seq 构建，而 BICCN scATAC-seq 也用于测试，可能高估性能 | 若存在数据泄漏，跨数据集泛化结论不成立 | 检查 SF 构建所用 scRNA-seq 与测试 scATAC-seq 是否来自同一批细胞/样本；用完全独立的 marker 集重复实验 | Results 2.4 节：SF 在 BICCN 上性能最高 |
| raw aggregation 与 ML 性能对比可能受评估协议影响 | ML 分类器在 Consensus 训练时可能因标签不一致而性能下降，而非分类器本身能力不足 | 结论「简单方法优于复杂方法」可能过度泛化 | 用统一标签体系（如映射到公共本体）重新训练 ML；增加更多分类器（如 XGBoost、神经网络） | Results 2.6 节：ML 性能高度依赖训练数据 |
| CNN 输入为 5kb bin，可能丢失长程调控信息 | 增强子-启动子互作可跨越数百 kb，5kb 窗口可能不足以捕获 | 若 CNN 仅学习局部序列特征，其生物学解释力有限 | 测试不同窗口大小（如 1kb、10kb、100kb）对预测性能的影响；与 Hi-C 数据整合验证 | Methods 节：5kb bin 设计 |
| TF-MoDISCo 分析仅针对 3 种抑制性神经元亚型 | 结论可能不适用于兴奋性神经元或非神经元细胞 | 细胞类型特异的 TF 调控机制可能因类型而异 | 扩展至所有细胞类型，比较 motif 富集的异同 | Results 2.7 节：仅 Lamp5、Vip、Sncg |
| 未报告 CNN 的跨数据集泛化性能 | 仅用 BICCN 训练和测试，未在其他数据集验证 | 若 CNN 过拟合 BICCN，其通用性存疑 | 用其他 6 个数据集测试 CNN 预测性能 | Results 2.7 节：仅 BICCN 数据 |
| 基因活性计算使用固定 10kb 窗口 | 不同细胞类型的 TSS 附近可及性分布可能不同，固定窗口可能引入偏差 | 窗口选择影响所有下游分析 | 敏感性分析：测试不同窗口大小（5kb、20kb、50kb）对注释性能的影响 | Methods 节：TSS ± 10kb |
| 未与最新深度学习方法（如 scBERT、scGPT）对比 | 2021 年预印本，未包含后续 SOTA 方法 | 结论的时效性受限 | 与 2023-2025 年方法在相同基准上对比 | 全文：仅对比传统 ML 和 Seurat/BBKNN |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

### 概念层面
1. **冗余 marker 策略**：在稀疏高噪声的单细胞数据中，**特征冗余性比模型复杂度更重要**。通过共表达扩展 marker 集合，使简单聚合方法达到 SOTA 性能。→ 可迁移至 TF–DNA 互作：构建 TF 靶基因集合时，可纳入共表达/共调控基因以增加稳健性。
2. **Meta-analytic 整合**：从多个数据集整合 marker 比单一数据集更稳健。→ 可迁移至 TF 结合位点预测：整合多个 ChIP-seq 数据集（ENCODE、Cistrome）可提高位点预测的泛化能力。
3. **"净化" pseudo-bulk 策略**：通过稳健细胞类型注释获得"纯净"的细胞类型特异可及性谱，再用于下游建模。→ 可迁移至 TF–DNA 互作：从 scATAC-seq 中提取细胞类型特异的开放染色质区域，作为 TF 结合位点预测的训练数据。

### 方法层面
4. **简单基线的重要性**：raw signal aggregation 作为基线，可有效评估复杂模型的增量价值。→ 在 TF 结合预测中，应先建立简单基线（如 PWM 扫描、k-mer 频率），再评估深度学习模型的真实增益。
5. **特征选择主导性能**：在单细胞注释中，marker 基因选择对性能的影响大于分类器选择。→ 在 TF–DNA 结合预测中，特征工程（如 motif 特征、进化保守性、染色质状态）可能比模型架构更重要。
6. **CNN + 可解释性分析流程**：训练序列 CNN 后，用 saliency map + TF-MoDISCo 提取 motif，连接预测与生物学机制。→ 可直接迁移至 TF 结合位点预测：训练 CNN 后，用 attribution 方法识别关键序列基序，与已知 TF motif 比对验证。

### 实验设计层面
7. **跨数据集基准评测**：在 7 个异质数据集上系统评测，报告 AUROC 分布而非单一指标。→ 在 TF 结合预测中，应在多个细胞类型/组织的数据集上评测，避免单数据集过拟合。
8. **消融实验设计**：通过 SF vs SC（控制数量）分离冗余性贡献。→ 在模型设计中，通过控制变量法分离不同因素（如特征数量、模型容量）的贡献。

### 对 TF–DNA 互作课题的具体迁移建议
- **TF 靶基因集合构建**：采用 MetaMarkers 思路，从多个 scATAC-seq/scRNA-seq 数据集中整合 TF 靶基因及其共表达伙伴，提高下游富集分析的稳健性。
- **TF 结合位点预测**：使用细胞类型特异的 pseudo-bulk 可及性谱（经稳健注释）作为训练标签，结合序列 CNN 预测，并用 saliency + TF-MoDISCo 提取 motif。
- **基准评测**：在多个细胞类型/组织上评测 TF 结合预测模型，报告跨数据集泛化性能，而非单一数据集 AUC。

---

## 15 与已有知识连接

### 可验证的外部连接
1. **Basset [24]**：本文 CNN 架构基于 Basset，后者已证明可从 DNA 序列预测 DNase-seq 可及性。→ 连接 TF–DNA 互作：Basset 类模型可扩展为预测细胞类型特异的 TF 结合。
2. **DeepSea [25]**：本文对比 DeepSea 的 AUPR（0.444 vs 0.539）。DeepSea 是序列深度学习的开创性工作，预测染色质特征和剪接。→ 连接：TF 结合预测的序列深度学习基线。
3. **TF-MoDISco [31]**：本文使用 TF-MoDISco 从 CNN attribution map 中提取 motif。该工具已广泛用于 TF 结合 motif 发现。→ 连接：从深度学习模型中提取可解释的 TF 结合基序。
4. **JASPAR [27]**：本文使用 JASPAR 2020 脊椎动物数据库进行 motif 比对。→ 连接：TF 结合 motif 的权威数据库。
5. **Seurat [23] / BBKNN [22]**：本文对比的联合聚类方法，广泛用于单细胞数据整合。→ 连接：单细胞多模态整合的基线方法。
6. **MetaMarkers [15]**：本文引用的前期工作，提出从多 scRNA-seq 数据集整合 marker 基因的方法。→ 连接：marker 基因选择的 meta-analytic 框架。

### 与用户课题方向的连接
- **TF–DNA 结合机制 × AI**：本文的 CNN + attribution 流程（训练序列模型 → saliency map → TF-MoDISco → JASPAR 比对）是 TF 结合位点发现的完整范式，可直接迁移。
- **TF–DNA 结合机制 × 物理模拟**：本文未涉及 MD/对接，但其「细胞类型特异可及性」概念可指导物理模拟的体系选择——优先模拟在开放染色质区域中预测结合的 TF–DNA 复合物。
- **单细胞表观基因组 × TF 结合**：本文的「净化」pseudo-bulk 策略可产生高质量的细胞类型特异开放染色质图谱，为 TF 结合预测提供训练标签。

### 候选方向（需进一步验证）
- [Analysis] 将 MetaMarkers 的冗余策略应用于 TF 结合位点预测的特征工程（如整合多个 motif 数据库、共结合因子特征）。
- [Analysis] 将本文 CNN 的 attribution 结果与 MD 模拟结合：先用 CNN 预测候选 TF 结合位点，再用 MD 验证结合亲和力。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：Meta-TFBS——基于 meta-analytic 冗余策略的 TF 结合位点预测
- **名称**：Meta-TFBS
- **来源局限/观察**：本文证明冗余 marker 基因集合可显著提升 scATAC-seq 注释性能；类似地，TF 结合位点预测中，单一 ChIP-seq 数据集的噪声和偏差可能限制模型性能。
- **核心假设**：从多个 ChIP-seq 数据集（ENCODE、CISTROME）中整合 TF 结合位点及其共结合伙伴，构建冗余训练标签，可提升 TF 结合位点预测的泛化性能。
- **初步方法**：① 收集同一 TF 的多个 ChIP-seq 数据集；② 用 MetaMarkers 类似方法整合高置信度结合位点（含共结合因子位点）；③ 训练序列 CNN 预测整合后的结合位点；④ 与单数据集训练的模型对比跨细胞类型泛化性能。
- **验证方式**：在独立数据集（如 CISTROME 的未训练细胞系）上评测 AUC/PR；与 ENCODE 基准（如 ENCODE-DREAM challenge）对比。
- **创新状态**：unverified（需验证冗余策略在 TF 结合预测中的有效性）

### 候选 2：Cell-type-specific TF motif discovery via CNN attribution on purified scATAC-seq profiles
- **名称**：Purified-Motif
- **来源局限/观察**：本文通过稳健细胞类型注释获得"净化"的 pseudo-accesibility profiles，并用于 CNN 训练和 motif 发现；但 motif 分析仅针对 3 种抑制性神经元亚型，未系统比较所有细胞类型。
- **核心假设**：使用 Meta-Marker 注释的细胞类型特异可及性谱训练的 CNN，能比原始混合数据训练的 CNN 发现更多细胞类型特异的 TF motif。
- **初步方法**：① 用 SF marker 集注释 7 个数据集的细胞类型；② 构建细胞类型特异的 pseudo-bulk 可及性谱；③ 训练多任务 CNN 预测可及性；④ 用 saliency + TF-MoDISco 提取 motif，与 JASPAR 比对；⑤ 比较净化前后 motif 发现的差异。
- **验证方式**：motif 与已知细胞类型特异 TF 的重叠率；motif 在独立数据集（如 scRNA-seq 验证的 TF 表达）中的一致性。
- **创新状态**：partially checked（本文已展示初步结果，但未系统比较）

### 候选 3：Sequence-to-accessibility CNN with interpretable TF-binding priors
- **名称**：TF-Prior-CNN
- **来源局限/观察**：本文 CNN 为黑箱模型，仅通过事后 attribution 解释；若能将已知 TF motif 作为先验注入模型，可能提升可解释性和预测性能。
- **核心假设**：在 CNN 第一层注入已知 TF motif 作为初始化或正则化，可提升细胞类型特异可及性预测的准确性和可解释性。
- **初步方法**：① 从 JASPAR 获取细胞类型相关 TF 的 PWM；② 将 PWM 作为 CNN 第一层 filter 的初始化；③ 训练时加入 motif 正则化项（如 filter 与 PWM 的相似性约束）；④ 与随机初始化 CNN 对比预测性能和 motif 可解释性。
- **验证方式**：AUPR 对比；attribution map 与已知 motif 的匹配率；在独立数据集上的泛化性能。
- **创新状态**：unverified（需验证先验注入的增量价值）

### 候选 4：Cross-species TF-binding prediction via meta-analytic marker gene transfer
- **名称**：Cross-species-TF
- **来源局限/观察**：本文的 meta-analytic 策略基于小鼠数据，但 TF 结合机制在物种间保守；跨物种整合可能提升预测性能。
- **核心假设**：从小鼠 scATAC-seq 中识别的细胞类型特异可及性区域和 motif，可迁移至人类同源细胞类型，提升人类 TF 结合位点预测性能。
- **初步方法**：① 将小鼠 marker 基因映射至人类同源基因；② 用小鼠训练的 CNN 预测人类细胞类型特异可及性；③ 与人类数据训练的模型对比；④ 分析跨物种迁移失败的案例（如物种特异 TF）。
- **验证方式**：人类 scATAC-seq 数据上的 AUPR；与人类 ENCODE 数据的重叠率。
- **创新状态**：unverified（需验证跨物种迁移可行性）

### 候选 5：Integrating physical simulation with CNN-predicted accessibility for TF-DNA binding affinity prediction
- **名称**：CNN-MD-hybrid
- **来源局限/观察**：本文 CNN 预测可及性但未涉及结合亲和力；MD 模拟可提供结合自由能，但计算成本高。将 CNN 预测的可及性作为 MD 模拟的候选区域筛选器，可降低计算成本。
- **核心假设**：CNN 预测的高可及性区域富集真正的 TF 结合位点，MD 模拟在这些区域中可更高效地预测结合亲和力。
- **初步方法**：① 用本文 CNN 预测细胞类型特异的高可及性区域；② 在这些区域中运行 MD 模拟（如 GROMACS/AMBER）计算 TF-DNA 结合自由能；③ 与随机区域中的 MD 模拟对比；④ 验证结合自由能与实验数据（如 SELEX、HT-SELEX）的相关性。
- **验证方式**：结合自由能与实验亲和力的相关性；CNN 筛选的富集倍数。
- **创新状态**：unverified（需验证 CNN 筛选对 MD 模拟的加速和准确性提升）