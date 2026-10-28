## 01 基本信息

- **标题**：Identifying the DNA methylation preference of transcription factors using ProtBERT and SVM
- **作者**：Li, Yanchao; Zou, Quan; Dai, Qi; Stalin, Antony; Luo, Ximei
- **单位**：未提供（作者所属机构未在摘要中列出）
- **期刊/平台**：PLoS Computational Biology
- **年份**：2025
- **论文类型**：方法学/计算生物学研究
- **领域**：蛋白质-DNA互作（转录因子-DNA结合机制）× 深度学习（ProtBERT）+ 传统机器学习（SVM）
- **关键词**：Transcription factors (TFs), DNA methylation, TFPM (TF-methylation-DNA preference), ProtBERT, SVM, RAAC, K-mer
- **DOI/arXiv**：10.1371/journal.pcbi.1012513
- **代码**：https://github.com/LiZaiyuan0619/RKmer-SVM4TFPM/
- **数据**：源自 Liu et al. [11] 的数据集（原始数据来自 Wang et al. [18] 和 Yin et al. [33]）；另含 1,639 个人类 TF 数据集（S2 Zip）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦于**转录因子（TF）是否偏好结合甲基化DNA（TFPM）**的二分类预测问题，属于「TF–DNA结合机制 × AI方法」方向。其核心贡献在于：① 用 ProtBERT 做 TF 识别；② 用 RAAC + K-mer + SVM 做 TFPM 识别，强调在**小数据集**下传统机器学习优于深度学习的可迁移思路。

---

## 02 一句话总结

本文提出一个两步计算框架：先用微调后的 ProtBERT 区分 TF 与非 TF，再用 RAAC（氨基酸约简分类）+ K-mer + SVM 区分 TFPM（偏好甲基化DNA的TF）与 TFPNM（偏好非甲基化DNA的TF），在人类独立测试集和跨物种小鼠数据集上均优于现有方法，并预测出 1,639 个人类 TF 中 top 20 的 TFPM 候选，其中多数属于 Krueppel C2H2-type Zinc-finger 家族。

---

## 03 研究问题

- **具体问题**：如何从蛋白质序列出发，计算性地识别哪些转录因子（TF）偏好结合甲基化DNA（即 TFPM），而非仅依赖实验手段？
- **为什么重要**：DNA 甲基化是重要的表观遗传修饰，TF 对甲基化DNA的偏好直接影响基因调控网络的理解。实验方法（如质谱、HT-SELEX）成本高、通量低，亟需计算预测方法。
- **现有方法不足**：已有方法（XGBoost、LSTM、CNN）在小规模、高同源性数据集上训练，泛化能力差，面对新物种或未见序列时性能下降明显。
- **精确研究问题**：Can a two-step pipeline combining ProtBERT (for TF classification) and RAAC + K-mer + SVM (for TFPM classification) achieve superior and generalizable performance compared to existing methods on both human and cross-species datasets?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与参考文献，标注为「经外部核验」的部分仅指本文引用的文献，未逐一外部验证。

| 阶段 | 代表方法 | 优点 | 局限 | 本文位置 |
|------|----------|------|------|----------|
| 实验方法 | 串联质谱、HT-SELEX | 高精度、直接测定 | 资源消耗大、通量低 | 本文旨在替代/补充 |
| 早期计算 | Liu et al. (2020) XGBoost + 二肽组成（DC） | 简单、可解释 | 特征表达有限，泛化差 | 本文对比基线之一 |
| 中期计算 | Li et al. (2022) Skip-gram + LSTM | 捕捉序列语义 | 小数据集易过拟合 | 本文对比基线之一 |
| 中期计算 | Nguyen et al. (2022) G-gap DC + SVM | 降维有效 | 仍依赖手工特征 | 本文对比基线之一 |
| 本文方法 | ProtBERT（TF识别）+ RAAC + K-mer + SVM（TFPM识别） | 两步解耦，兼顾大模型与小数据 | 依赖预训练模型，TFPM步骤仍为手工特征 | 本文主张 |

**本文主张的位置**：在 TF 识别任务上利用大规模预训练模型（ProtBERT）的优势；在 TFPM 识别任务上，因数据量小、类别差异微妙，选择 RAAC + K-mer + SVM 而非端到端深度学习，以避免过拟合。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 数据规模小 | TFPM 训练集仅 270 正样本、106 负样本 | 实验鉴定 TFPM 成本高，公共数据库有限 | Materials and methods, Datasets 节 |
| 类别差异微妙 | TFPM 与 TFPNM 序列相似度高，难以区分 | 甲基化偏好可能由局部序列特征决定，而非全局结构 | Results, TFPMs classification 节 |
| 现有方法泛化差 | 已有模型在新物种（小鼠）上性能下降 | 训练集高同源性、特征表达不足 | Introduction 节 |
| 深度学习过拟合 | 端到端大模型在小数据集上不稳定 | 模型参数量远超样本量，易学习噪声 | Results, TFPMs classification 节 |
| 特征维度爆炸 | K-mer 直接编码维度随 K 增大指数增长 | 20^K 种可能组合，稀疏且噪声大 | Results, TFPMs classification 节（K=1 最优） |

---

## 06 核心思想

### 1) 表面方法
- **第一步**：用 ProtBERT-BFD 微调，对 TF vs 非 TF 做二分类，取 CLS token 嵌入。
- **第二步**：对已识别的 TF，用 RAAC（Op=11 将 20 种氨基酸约简为 11 类）+ K-mer（K=1）编码，输入 SVM（RBF 核，C=0.01, gamma=1）做 TFPM vs TFPNM 二分类。

### 2) 核心洞察
- **任务解耦**：TF 识别与 TFPM 识别是两个难度不同的任务。前者数据量大、类别差异明显，适合大模型；后者数据量小、差异微妙，适合特征约简 + 传统分类器。
- **RAAC 的生物学意义**：将 20 种氨基酸按理化性质（电荷、疏水性等）聚类，K=1 时实际编码的是「简化残基类型频率」，这暗示**甲基化偏好可能与单残基水平的理化特征相关**，而非长程序列模式。
- **CLS token 优于池化**：在 ProtBERT 微调中，CLS token 嵌入比 mean/max pooling 更优，因其聚合了全局上下文信息。

### 3) 可能的普适教训 [Analysis]
- **模型选择应匹配数据规模**：不是所有任务都适合端到端深度学习；在小数据、细粒度分类场景下，特征工程 + 传统模型（SVM）可能更稳健。
- **预训练模型可作「粗筛器」**：大模型适合做粗粒度分类（如 TF vs 非TF），细粒度子类（如 TFPM vs TFPNM）可交给可解释的浅层模型。
- **氨基酸约简是降维利器**：RAAC 类方法在序列特征工程中仍有价值，尤其当数据量不足以支撑高维 one-hot 或 embedding 时。

---

## 07 方法总览

- **输入**：蛋白质氨基酸序列（TF 数据集 522 个 TF + 416 个非 TF；TFPM 数据集 270 TFPM + 106 TFPNM；独立测试集 69 TFPM + 37 TFPNM；跨物种小鼠 129 TFPM）
- **输出**：二分类标签（TF / 非TF；TFPM / TFPNM）
- **模块**：
  1. ProtBERT-BFD 微调（TF 分类）
  2. RAAC 氨基酸约简（Op=11）
  3. K-mer 频率编码（K=1）
  4. SVM 分类器（RBF 核）
- **训练**：5-fold cross-validation + 独立测试集；超参数网格搜索（RAAC op ∈ {5,8,9,11,13}，K ∈ {1,2,3,4,5}，SVM C 和 gamma）
- **工具**：Hugging Face Transformers API（ProtBERT 微调）；scikit-learn（SVM）
- **反馈回路**：无显式迭代反馈；两步流水线为前馈式
- **文字流程**：
  1. 输入蛋白质序列 → 2. ProtBERT 微调模型判断是否为 TF → 3. 若是 TF，则用 RAAC 将序列约简为 11 类符号 → 4. 统计 K=1 时各类符号频率 → 5. 输入 SVM 判断是否为 TFPM → 6. 输出预测标签

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ProtBERT-BFD 微调 | 区分 TF 与非 TF | TF 识别是 TFPM 预测的前置步骤，需高精度粗筛 | 输入：氨基酸序列（max_len=1000）；输出：TF/非TF 概率 | Results 表 4：Accuracy 93.87%, AUC 0.9801 | 预期：若移除，无法从任意蛋白中筛选候选 TF，流水线失效 |
| CLS token 嵌入 | 聚合全序列上下文特征 | 比 mean/max pooling 更优（表 2） | 输入：ProtBERT 输出；输出：1024 维向量 | Results 表 2：CLS 在 Accuracy/MCC/Specificity/F1 上均优于 mean/max pooling | 预期：改用 mean pooling 会降低 TF 分类性能（实测对比） |
| RAAC（Op=11） | 将 20 种氨基酸约简为 11 类 | 降低维度、减少噪声、保留理化性质信息 | 输入：原始氨基酸序列；输出：约简符号序列 | Results 表 3：Op=11 为最优分组方案 | 预期：移除后 K-mer 维度从 11 增至 20，稀疏性增加，SVM 性能下降 |
| K-mer 频率编码（K=1） | 统计简化残基类型频率 | 捕获单残基水平的理化特征分布 | 输入：RAAC 约简序列；输出：11 维频率向量 | Results：K=1 优于 K=2~5 | 预期：K>1 时维度增加但 AUC 下降（实测），移除则无特征输入 |
| SVM（RBF 核） | 区分 TFPM 与 TFPNM | 小数据下比深度学习更稳定 | 输入：11 维频率向量；输出：TFPM/TFPNM 标签 | Results 表 4：Accuracy 80.19%, AUC 0.8351；图 4：SVM 优于 XGBoost 和 RF | 预期：替换为神经网络可能过拟合（作者解释，未做消融） |

---

## 09 关键公式符号

本文未提供显式数学公式（如损失函数、核函数表达式等），仅提及以下概念：

- **二元交叉熵损失**（Binary Cross-Entropy Loss）：用于 ProtBERT 微调，公式在原文中提及但未编号：
  \[
  L = -\frac{1}{N}\sum_{i=1}^{N} [y_i \log(\hat{y}_i) + (1-y_i) \log(1-\hat{y}_i)]
  \]
  其中 \( y_i \) 为真实标签（0 或 1），\( \hat{y}_i \) 为预测概率。

- **SVM RBF 核**：\( K(x, x') = \exp(-\gamma \|x - x'\|^2) \)，文中未显式给出，但提及使用 RBF 核。

- **评估指标**：
  - Sensitivity = TP / (TP + FN)
  - Specificity = TN / (TN + FP)
  - Accuracy = (TP + TN) / (TP + TN + FP + FN)
  - MCC = (TP·TN - FP·FN) / √[(TP+FP)(TP+FN)(TN+FP)(TN+FN)]
  - AUC：ROC 曲线下面积

---

## 10 实验设计与证据链

### 数据集与评测协议
- **训练集**：416 TF + 416 非 TF（TF 分类）；270 TFPM + 106 TFPNM（TFPM 分类）
- **独立测试集**：106 TF + 106 非 TF（TF 分类）；69 TFPM + 37 TFPNM（TFPM 分类）
- **跨物种验证**：129 个小鼠 TFPM 序列
- **大规模预测**：1,639 个人类 TF（排除已知 522 个有偏好标签的 TF）
- **指标**：Sensitivity, Specificity, Accuracy, MCC, AUC
- **验证方式**：5-fold cross-validation + 独立测试集

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|-------------|-------------------|------|
| TF 分类 | ProtBERT 优于现有方法 | 对比 CTD_SAAC_DC+SVM [11], Tripeptide+LSTM [28], PSSM+CNN [30] | Accuracy 93.87%, Sensitivity 93.40%, Specificity 94.33%, MCC 0.8773, AUC 0.9801 | ProtBERT 在 TF 识别上全面领先 | 未在更大规模或更多物种上验证 | Results 表 4 |
| TFPM 分类 | RAAC+K-mer+SVM 优于现有方法 | 对比 XGBoost [11], LSTM [28], CNN [30] | Accuracy 80.19%, Sensitivity 86.95%, Specificity 67.57%, MCC 0.5568, AUC 0.8351 | 两步法在 TFPM 识别上最优 | 未与端到端 ProtBERT 直接对比 TFPM 任务 | Results 表 4 |
| 跨物种验证 | 模型泛化到小鼠 | 129 个小鼠 TFPM 序列 | 优于所有基线（具体数值未在摘要中给出） | 模型具有跨物种泛化能力 | 小鼠数据无明确负样本，验证不完整 | Results 表 5 |
| 大规模预测 | 预测 1,639 个人类 TF 的 TFPM 概率 | 无对比基线 | Top 20 中多数为 Krueppel C2H2-type Zinc-finger 家族 | 预测结果与已知生物学知识一致 | 无 wet-lab 验证 | Results 表 6 |
| 超参数选择 | K=1, Op=11 最优 | 网格搜索 K∈{1..5}, op∈{5,8,9,11,13} | K=1, Op=11 给出最高 AUC | 单残基理化特征足以区分 TFPM | 未测试其他 RAAC 分组方案 | Results 图 4A |
| 池化策略 | CLS 优于 mean/max pooling | 对比三种池化方式 | CLS 在 Accuracy/MCC/Specificity/F1 上均最优 | CLS 聚合全局上下文更有效 | 未在其他预训练模型上验证 | Results 表 2 |

---

## 11 结论正确解读

- **任务范围**：本文解决的是「给定蛋白质序列，判断是否为 TF」和「给定 TF 序列，判断是否偏好甲基化 DNA」两个二分类问题。**不涉及** TF 与 DNA 的具体结合位点预测、结合亲和力定量预测或三维结构建模。
- **Oracle/真值输入**：训练标签来自实验文献（Wang et al. [18], Yin et al. [33]），非计算预测。TFPM 标签基于实验观察到的甲基化偏好，但**未提供结合亲和力的定量阈值**。
- **端到端状态**：两步流水线是**非端到端**的——TF 分类用 ProtBERT，TFPM 分类用 SVM，两者独立训练，无联合优化。
- **算力成本**：ProtBERT 微调需要 GPU，但 TFPM 步骤（SVM）计算成本极低；整体流程对算力要求中等。
- **历史数据依赖**：训练数据来自 2019-2020 年左右的实验文献，可能遗漏近年新发现的 TFPM。
- **最难情形**：TFPM vs TFPNM 的区分（AUC 0.8351）显著低于 TF vs 非TF（AUC 0.9801），说明甲基化偏好预测仍是难点。
- **群体/领域边界**：模型主要基于人类数据训练，小鼠验证仅覆盖正样本（129 TFPM），**未验证小鼠负样本**，因此跨物种泛化结论需谨慎。
- **不确定性**：预测 1,639 个人类 TF 的 top 20 结果**未经 wet-lab 验证**，仅通过文献间接佐证（如 Krueppel C2H2 家族与甲基化偏好相关）。

**有边界的复述**：本文提出的两步法在人类独立测试集上优于现有方法，并在小鼠正样本上表现出一定泛化能力；但其 TFPM 预测精度仍有限（AUC ≈ 0.84），且大规模预测结果缺乏实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 数据集规模小 | TFPM 训练集仅 270 正样本、106 负样本 | 计划纳入新数据以扩展模型能力 | Materials and methods, Datasets 节 |
| 跨物种验证不完整 | 小鼠数据仅含正样本（129 TFPM），无负样本 | 未明确提及 | Results, Generalization 节 |
| 深度学习在小数据上不稳定 | ProtBERT 在 TFPM 任务上可能过拟合 | 采用 RAAC + SVM 替代 | Results, TFPMs classification 节 |
| 预测结果缺乏实验验证 | 1,639 个人类 TF 的 top 20 预测未 wet-lab 确认 | 未来研究将探索 Krueppel C2H2 家族与甲基化 DNA 的关系 | Conclusion 节 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| TFPM 任务未与端到端 ProtBERT 直接对比 | 作者声称 ProtBERT 会过拟合，但未提供实验证据 | 若端到端 ProtBERT 在 TFPM 上表现相当，则两步法的必要性存疑 | 在相同数据上微调 ProtBERT 做 TFPM 二分类，对比 AUC | Results 表 4 仅对比了传统方法 |
| 小鼠验证仅含正样本 | 无负样本意味着无法计算特异性或 MCC，泛化结论可能过于乐观 | 跨物种泛化是本文核心卖点之一，证据链不完整 | 收集小鼠 TFPNM 负样本，重新评估 | Results 表 5 |
| K=1 最优的解释不足 | 作者归因于单残基理化性质，但未做特征重要性分析 | 若 K=1 仅因维度低而避免过拟合，则生物学解释可能不成立 | 对 11 类简化残基做特征重要性排序，检查是否有特定残基类别主导 | Results, TFPMs classification 节 |
| 数据划分未说明序列相似性控制 | 若训练/测试集存在高序列相似性，性能可能被高估 | 序列相似性泄漏是蛋白质预测的常见陷阱 | 检查训练/测试集最大序列同一性，或用 CD-HIT 去冗余 | Materials and methods 未提及 |
| 未与 AlphaFold 或结构特征对比 | 甲基化偏好可能与三维结构相关，本文仅用序列特征 | 若结构特征能显著提升性能，则序列方法的边界需明确 | 对已知结构的 TF 提取结构特征，与序列特征对比 | 全文未提及结构信息 |
| 预测 top 20 的验证依赖文献间接证据 | Krueppel C2H2 家族与甲基化相关是已知知识，预测结果可能只是「重复已知」 | 模型的新颖发现能力未被证明 | 检查 top 20 中是否有此前未知的 TFPM 候选 | Results 表 6 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **任务分解策略**：将「TF 识别」与「TFPM 识别」拆分为两个独立任务，分别选择适合的模型（大模型 vs 传统 ML）。可迁移到 TF–DNA 结合机制研究：先粗筛（如预测是否结合 DNA），再细分类（如结合模式、甲基化偏好、辅因子依赖）。
2. **RAAC 氨基酸约简**：将 20 种氨基酸按理化性质聚类为 11 类，大幅降低特征维度。可迁移到其他 TF–DNA 互作预测任务，尤其是小样本场景（如特定 TF 家族的结合特异性预测）。
3. **CLS token 优于池化**：在蛋白质序列分类中，CLS token 嵌入比 mean/max pooling 更有效。可迁移到 TF 结合位点预测、DNA 结合域分类等任务。
4. **小数据下 SVM 的稳健性**：当样本量小（<500）且类别差异微妙时，SVM + 手工特征可能优于深度学习。可迁移到 TF 家族亚型分类、甲基化敏感 vs 不敏感 TF 的区分。
5. **跨物种验证的设计**：即使负样本缺失，正样本跨物种验证仍能提供一定泛化证据，但需明确标注其局限性。可迁移到其他物种的 TF–DNA 互作预测。
6. **K=1 的生物学启示**：单残基理化性质（电荷、疏水性）可能足以编码甲基化偏好信号，提示 TF 的甲基化敏感性可能由 DNA 结合域中少数关键残基决定。可迁移到突变分析（哪些残基突变会改变甲基化偏好）。

---

## 15 与已有知识连接

- **ProtBERT**：由 Elnaggar et al. (2021) 提出的蛋白质预训练语言模型，基于 BERT 架构，在 UniProt/TrEMBL 等大规模蛋白质序列上预训练。本文将其用于 TF 分类，与 ProtBERT 在蛋白质功能预测、亚细胞定位等任务上的应用一致。
- **RAAC（Reduced Amino Acid Alphabet）**：源自蛋白质序列分析中的氨基酸约简策略，如 Etchebest et al. 的 16 蛋白块（PB）聚类。本文使用 Op=11 方案，与蛋白质结构分类中的氨基酸理化聚类方法一致。
- **SVM + 序列特征**：与早期蛋白质功能预测工作（如 SVM + dipeptide composition）一致，Liu et al. (2020) 的 XGBoost 方法也是类似思路。
- **TF 甲基化偏好**：与已知的 Krueppel C2H2 锌指家族（如 Kaiso, ZBTB33）结合甲基化 CpG 的实验发现一致。该家族通过锌指基序识别甲基化 CpG，是 TF–DNA 互作中「甲基化阅读器」的代表。
- **与结构预测的关联**：本文未使用 AlphaFold 或 MD 模拟，但其预测的 TFPM 候选可作为结构生物学研究的输入（如对 top 候选做分子对接或 MD 模拟，验证甲基化 CpG 的结合模式）。
- **与 ChIP-seq / HT-SELEX 的互补**：本文方法可作为实验方法的计算预筛，缩小 wet-lab 验证范围。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：基于 RAAC 的 TF–DNA 结合位点偏好预测
- **名称**：RAAC-Kmer 用于 TF 结合基序预测
- **来源局限/观察**：本文证明 RAAC + K-mer 在 TFPM 分类上有效，但未扩展到结合位点（motif）预测
- **核心假设**：RAAC 约简后的残基频率可编码 TF 的 DNA 结合域偏好，进而预测其结合的 DNA motif
- **初步方法**：对 TF 的 DNA 结合域序列做 RAAC + K-mer 编码，训练模型预测其已知的 DNA 结合 motif（如从 CIS-BP 数据库获取）
- **验证方式**：与现有 motif 预测工具（如 DeepBind、DeepSEA）对比，在独立 TF 家族上测试
- **创新状态**：unverified

### 候选 2：将 ProtBERT 嵌入与 RAAC 特征融合用于 TFPM 预测
- **名称**：Hybrid ProtBERT-RAAC 特征融合
- **来源局限/观察**：本文在 TFPM 任务上未使用 ProtBERT 嵌入，仅用 RAAC + K-mer
- **核心假设**：ProtBERT 嵌入（全局语义）+ RAAC 特征（局部理化）融合可提升 TFPM 分类性能
- **初步方法**：提取 ProtBERT 的最后一层嵌入，与 RAAC + K-mer 特征拼接，输入 SVM 或轻量 MLP
- **验证方式**：在相同数据集上与本文方法对比，检查 AUC 是否提升
- **创新状态**：unverified

### 候选 3：TF 甲基化偏好的结构基础分析
- **名称**：TFPM 候选的分子对接与 MD 模拟验证
- **来源局限/观察**：本文预测的 top 20 TFPM 候选未经结构验证
- **核心假设**：TFPM 的 DNA 结合域与甲基化 CpG 的相互作用可通过分子对接和 MD 模拟区分于非甲基化 CpG
- **初步方法**：选取 top 候选 TF，用 AlphaFold 预测其 DNA 结合域结构，与甲基化/非甲基化 CpG DNA 做分子对接，再进行短时 MD 模拟比较结合自由能
- **验证方式**：与已知 TFPM（如 Kaiso）的晶体结构对比，检查预测的结合模式是否一致
- **创新状态**：unverified

### 候选 4：跨物种 TFPM 预测的负样本构建
- **名称**：跨物种 TFPM 泛化评估的负样本设计
- **来源局限/观察**：本文小鼠验证仅含正样本，无负样本
- **核心假设**：构建合适的小鼠 TFPNM 负样本可更严格评估模型跨物种泛化能力
- **初步方法**：从小鼠实验数据中收集明确不偏好甲基化 DNA 的 TF，构建负样本集，重新评估模型
- **验证方式**：对比有/无负样本时的 AUC、特异性变化
- **创新状态**：unverified

### 候选 5：TF 甲基化偏好与 DNA 序列上下文的关系
- **名称**：甲基化偏好 TF 的 DNA 序列上下文分析
- **来源局限/观察**：本文仅用蛋白质序列特征，未考虑 DNA 序列上下文
- **核心假设**：TFPM 的甲基化偏好可能依赖于其结合位点周围的 DNA 序列上下文（如 CpG 密度、侧翼序列）
- **初步方法**：对已知 TFPM 的结合位点做序列上下文分析（如 CpG 密度、GC 含量、侧翼 motif），训练模型预测甲基化偏好
- **验证方式**：与本文蛋白质序列特征模型对比，检查是否互补
- **创新状态**：unverified