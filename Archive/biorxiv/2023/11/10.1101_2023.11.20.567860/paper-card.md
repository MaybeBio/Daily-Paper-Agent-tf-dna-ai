## 01 基本信息

- **标题**：DNA-binding factor footprints and enhancer RNAs identify functional non-coding genetic variants
- **作者**：Simon C Biddie; Giovanna Weykopf; Elizabeth F. Hird; Elizabeth T. Friman; Wendy A Bickmore
- **单位**：未提供（根据作者信息推测为 MRC Human Genetics Unit，University of Edinburgh 相关机构，但原文未明确标注）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2023
- **论文类型**：预印本（研究论文）
- **领域**：功能基因组学 / 调控基因组学 / 复杂疾病遗传学
- **关键词**：GWAS、非编码变异、DNase footprints、enhancer RNA、molQTL、变异优先级排序
- **DOI/arXiv 号**：10.1101/2023.11.20.567860
- **代码**：https://github.com/sbiddie/FINDER（合并数据集）；https://github.com/efriman/PeakPredict（随机森林分类工具）
- **数据**：>50,000 个数据集，>2,000 个 biosources；来源详见 Supplementary table 1
- **阅读日期**：未提供

**在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**：本文属于**功能基因组学与调控基因组学**范畴，核心关注**转录因子（TF）在基因组上的结合足迹（footprints）**与**增强子RNA（eRNA）**作为功能性非编码变异的标记。该文不直接使用深度学习或分子动力学模拟，而是基于**大规模实验数据的整合分析**（DNase-seq、ATAC-seq、ChIP-seq、eRNA），通过**统计评估（precision/recall）**和**机器学习（随机森林+SHAP）**来验证「TF结合足迹 + eRNA」这一组合标记对功能性变异的预测能力。对本课题（TF–DNA结合机制 × AI/物理模拟）而言，该文提供了**「如何用实验衍生的TF结合证据来标注功能性变异」**的基准框架，可作为AI预测模型的特征工程参考和验证基准。

---

## 02 一句话总结

本文系统评估了六种活性调控元件标记（ATAC-seq、H3K27ac、DNase footprints、eRNA、ChIP-seq等）对功能性非编码变异的预测能力，发现**DNase footprints与eRNA的组合**具有最高的精确率（precision），并以此构建了FINDER框架，可将GWAS候选变异集大幅缩减（如白细胞计数性状约缩减30倍），同时保留生物学相关的基因和通路。

---

## 03 研究问题

**具体问题**：在GWAS关联区域中，如何从成百上千个连锁不平衡（LD）的候选变异中识别出真正具有功能（影响调控元件活性）的因果非编码变异？

**为什么重要**：
- 绝大多数GWAS变异位于非编码区，功能注释困难
- 现有基于活性调控元件标记（如ATAC-seq、H3K27ac）的优先级排序方法精确率低
- 功能变异的识别是理解复杂疾病机制和药物靶点发现的前提

**现有方法为何不足**：
- ATAC-seq和H3K27ac标记覆盖范围大（宽峰），特异性低，导致大量假阳性
- 现有方法未充分利用「TF直接结合」和「增强子转录活性」这两个更接近功能机制的信号
- 机器学习方法（如deep learning）对常见变异效果差，且缺乏可解释性

**精确的「Can ... ?」研究问题**：
**Can the combination of DNase footprints and enhancer RNAs, as markers of active regulatory elements, identify functional non-coding genetic variants with higher precision than existing markers (e.g., ATAC-seq, H3K27ac) alone?**

---

## 04 背景与发展脉络

*注：以下脉络基于本文框架整理，部分外部引用来自原文引文，标注为「经外部核验」或「仅本文框架」。*

**阶段一：GWAS时代的功能变异注释困境**
- GWAS发现了大量与复杂性状/疾病相关的非编码变异（Maurano et al., 2012）
- 但LD结构使得因果变异难以定位
- 代表性方法：基于LD的精细定位（fine mapping）

**阶段二：基于染色质状态的注释方法**
- 利用ATAC-seq、DNase-seq、H3K27ac ChIP-seq等标记活性调控元件
- 代表性工作：ENCODE、Roadmap Epigenomics
- 局限：这些标记覆盖范围大，特异性不足，无法精确到单个变异（Gasperini et al., 2017; Chen et al., 2023）

**阶段三：TF结合与功能证据的整合**
- DNase footprints可反映TF在DNA上的直接结合（Vierstra et al., 2020）
- eRNA是活性增强子的标志（Hou and Krause, 2021）
- molQTL（分子数量性状位点）提供等位基因特异性的功能证据（Abramov et al., 2021; van Arensbergen et al., 2019）
- 本文主张：**将DNase footprints与eRNA结合，作为高精确率的功能变异标记**

**阶段四：机器学习辅助变异优先级排序**
- 已有方法：deep learning（如DeepSEA、Enformer）、基于注释的回归模型
- 局限：对常见变异预测效果差（Wang et al., 2022; Tabarini et al., 2022）
- 本文的补充：使用随机森林+SHAP验证footprints和eRNA的特征重要性

**本文主张的位置**：在「实验衍生的TF结合证据（footprints）+ 增强子活性证据（eRNA）」这一交叉点上，提出一个**简单、可解释、高精确率**的变异优先级排序框架，不依赖复杂的深度学习模型，而是基于**功能机制**的标记组合。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| GWAS变异功能注释困难 | 绝大多数GWAS变异位于非编码区，难以判断功能 | 非编码区缺乏直接的功能读出；LD结构使因果变异难以分离 | Introduction 第1段 |
| 现有活性标记精确率低 | ATAC-seq和H3K27ac标记的变异集过大，包含大量非功能变异 | 这些标记反映的是开放的染色质区域或宽泛的组蛋白修饰，而非具体的TF结合事件；覆盖范围大（宽峰） | Results 图3A-B；Discussion 第1段 |
| 现有方法无法精确到单变异 | 宽峰标记无法区分同一调控区域内多个候选变异的功能差异 | ATAC-seq峰和H3K27ac峰通常跨越数百bp至数kb，包含多个变异 | Results 图3A；Discussion 第1段 |
| 机器学习方法对常见变异效果差 | deep learning等方法对常见变异的预测精确率低 | 训练数据偏差、缺乏功能机制约束、特征选择不当 | Introduction 第3段（引用Wang et al., 2022; Tabarini et al., 2022） |
| 细胞类型特异性问题 | 功能变异的作用具有细胞类型特异性，但GWAS难以指示相关细胞类型 | 不同细胞类型的调控元件活性差异大；跨细胞类型合并标记会稀释信号 | Results 图5D；Discussion 第3段 |
| eRNA数据覆盖不足 | eRNA数据库的biosource数量最少，可能遗漏组织特异性增强子 | eRNA检测（如PRO-seq）成本高，现有数据主要来自基础条件 | Discussion 第3段；Results 图1A |

---

## 06 核心思想

### 1) 表面方法

系统收集六种活性调控元件标记（DNase footprints、eRNA、ATAC-seq、H3K27ac、DHS、ChIP-seq），将所有biosource合并为「细胞/组织类型不可知」的master file，然后与GWAS目录变异和三种molQTL（bQTL、raQTL、caQTL）基准集进行交集分析，计算每种标记（及组合）的精确率（precision）。最终确定DNase footprints + eRNA为最优组合，构建FINDER框架。

### 2) 核心洞察

**「直接功能证据」优于「间接活性标记」**：
- DNase footprints反映的是TF在DNA上的**直接结合足迹**（约20-40bp），比ATAC-seq（数百bp宽峰）更精确地定位到TF结合位点
- eRNA反映的是**增强子的实际转录活性**，比H3K27ac（组蛋白修饰）更接近增强子的功能状态
- 两者结合 = **「TF确实结合了」+「增强子确实在转录」**，这是比「染色质开放」或「组蛋白修饰」更强的功能证据

**「细胞类型不可知」策略的合理性**：
- 由于不知道GWAS变异在哪种细胞类型中起作用，将所有biosource合并可以最大化捕获可能性
- 虽然会引入噪声，但footprints和eRNA的高特异性弥补了这一点

### 3) 可能的普适教训 [Analysis]

- **特征选择的机制驱动优于数据驱动**：与其堆砌大量表观遗传标记，不如选择直接反映功能机制的标记（TF结合 + 转录活性）
- **精确率与召回率的权衡**：高精确率（低假阳性）对于实验验证优先排序更为重要，即使牺牲召回率
- **「合并所有细胞类型」的实用主义**：在不知道相关细胞类型时，合并策略虽然粗糙但有效，且后续可通过细胞类型富集分析（如FORGE2）来推断相关细胞类型

---

## 07 方法总览

**输入**：
- 六种活性调控元件标记的基因组坐标（BED格式）：
  1. DNase footprints（ENCODE, Vierstra et al., 2020）
  2. eRNA（PINTS portal, Yao et al., 2022）
  3. ATAC-seq（GTRD, Kolmykov et al., 2021）
  4. H3K27ac ChIP-seq（GTRD, dbInDel）
  5. DHS（ENCODE, Meuleman et al., 2020）
  6. ChIP-seq（GTRD，956个DNA结合因子）
- GWAS目录变异（p < 1×10⁻⁵，>180K非冗余变异）
- 三种molQTL基准集：bQTL（Abramov et al., 2021）、raQTL（van Arensbergen et al., 2019）、caQTL（Vierstra et al., 2020; Zheng et al., 2020）

**输出**：
- 每种标记及55种组合的精确率（precision）评分
- FINDER框架：DNase footprints + eRNA组合的变异优先级排序
- 应用示例：白细胞计数性状、哮喘性状的变异优先级排序

**模块**：
1. **数据整合模块**：合并所有biosource的每种标记，生成master file
2. **变异交集模块**：GWAS变异与标记的bedtools交集
3. **精确率计算模块**：以molQTL为真阳性集，计算precision
4. **机器学习验证模块**：随机森林分类器 + SHAP值（PeakPredict包）
5. **应用模块**：FINDER应用于具体性状（白细胞计数、哮喘）

**训练**：
- 随机森林分类器：以molQTL为标签，六种标记重叠为特征，平衡采样
- 非传统「训练-测试」框架，主要是统计评估和特征重要性分析

**工具**：
- bedtools（merge, intersect）
- PeakPredict（https://github.com/efriman/PeakPredict）
- scikit-learn（随机森林）
- SHAP
- FORGE2（细胞类型富集分析）
- GREAT（GO分析）
- FABIAN-variant（TF motif结合预测）
- HOMER（基因组注释）
- UCSC LiftOver（基因组版本转换）

**反馈回路**：无显式反馈回路；主要是单向的「标记→交集→精确率评估」流程。

**假设**：
- molQTL变异代表真实的功能变异（真阳性集）
- 细胞类型不可知策略可接受（合并所有biosource）
- 变异与标记的基因组重叠（≥1bp）足以判定共定位

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| **数据整合模块** | 合并所有biosource的每种标记，生成master file | 细胞类型不可知策略需要最大化覆盖；单一biosource数据量不足 | 输入：各标记的BED文件；输出：合并后的master BED | Results 图1A-B；Methods "Data sources" | 预期影响：移除后无法覆盖所有可能的调控元件，精确率下降 [预期效应] |
| **变异交集模块** | 计算GWAS变异与标记的重叠 | 确定候选变异是否落在活性调控元件内 | 输入：GWAS变异、标记master file；输出：交集变异列表 | Methods "Intersections of features" | 预期影响：移除后无法进行任何优先级排序 [预期效应] |
| **精确率计算模块** | 以molQTL为真阳性集计算precision | 量化每种标记/组合的预测能力 | 输入：交集变异、molQTL；输出：precision值 | Results 图3A-B；Methods "Confusion matrix calculations" | 预期影响：移除后无法比较不同标记的优劣 [预期效应] |
| **机器学习验证模块** | 随机森林+SHAP验证特征重要性 | 独立验证footprints和eRNA的预测价值 | 输入：六种标记重叠特征、molQTL标签；输出：SHAP值、预测AUC | Results 图3C；Methods "Random forest classification" | 实测影响：SHAP确认footprints和eRNA为top特征；移除后失去独立验证 [实测消融效应] |
| **FINDER应用模块** | 将footprints+eRNA组合应用于具体性状 | 展示框架的实际效用 | 输入：GWAS性状变异；输出：优先级排序的候选变异 | Results 图5A-F；Table 1 | 预期影响：移除后无法展示实际应用价值 [预期效应] |
| **细胞类型富集分析模块** | FORGE2分析优先级变异的细胞类型富集 | 推断功能变异的相关细胞类型 | 输入：优先级变异；输出：富集的细胞类型 | Results 图5D | 预期影响：移除后无法推断相关细胞类型 [预期效应] |

---

## 09 关键公式符号

**1. Precision（精确率/阳性预测值）**

\[
\text{Precision} = \frac{TP}{TP + FP}
\]

- TP（True Positives）：与标记重叠且与molQTL共定位的GWAS变异数
- FP（False Positives）：与标记重叠但**不**与molQTL共定位的GWAS变异数

**用途**：评估每种标记/组合识别功能性变异的能力。来源：Methods "Confusion matrix calculations"。

**2. Z-score标准化**

\[
Z = \frac{x - \mu}{\sigma}
\]

- x：特定标记组合的precision值
- μ：所有组合precision值的均值
- σ：所有组合precision值的标准差

**用途**：跨不同molQTL基准集比较precision值（因为不同molQTL的precision绝对值范围差异大，如bQTL为7.5-55.46%，raQTL为0.42-3.53%）。来源：Results 图3A。

**3. Fold change（相对随机变异的富集倍数）**

\[
\text{Fold change} = \frac{\text{Precision}_{\text{标记组合}}}{\text{Precision}_{\text{随机SNV}}}
\]

**用途**：评估标记组合相对于随机SNV的富集程度。例如，footprints+eRNA组合的fold change为13.89，而ATAC-seq仅为1.12-1.44。来源：Results 图3B。

**4. SHAP值（Shapley Additive Explanations）**

\[
\phi_i = \sum_{S \subseteq F \setminus \{i\}} \frac{|S|!(|F|-|S|-1)!}{|F|!} [f_{S \cup \{i\}}(x_{S \cup \{i\}}) - f_S(x_S)]
\]

- F：所有特征的集合
- S：不包含特征i的特征子集
- f_S：仅使用子集S训练模型的预测值

**用途**：量化每个标记对随机森林分类器预测的贡献。来源：Methods "Random forest classification"；Results 图3C。

---

## 10 实验设计与证据链

### 数据集/群体

| 数据集 | 规模 | 来源 |
|--------|------|------|
| GWAS目录变异 | >180K非冗余变异（p < 1×10⁻⁵） | NHGRI-EBI GWAS catalog V1.0.2 |
| DNase footprints | ENCODE（Vierstra et al., 2020） | 外部 |
| eRNA | PINTS portal（Yao et al., 2022） | 外部 |
| ATAC-seq | GTRD（Kolmykov et al., 2021） | 外部 |
| H3K27ac | GTRD + dbInDel | 外部 |
| ChIP-seq | GTRD（956个DNA结合因子） | 外部 |
| bQTL | AD ASTRA（Abramov et al., 2021） | 外部 |
| raQTL | van Arensbergen et al., 2019（K562, HepG2） | 外部 |
| caQTL | ENCODE + QTLbase（Vierstra et al., 2020; Zheng et al., 2020） | 外部 |
| 随机SNV | >660M（MAF ≥ 1%），随机抽取~180K | dbSNP build 151 |
| 罕见病变异 | 210个非冗余变异 | Smedley et al., 2016 |

### 指标

- **Precision（精确率）**：主要指标
- **Recall（召回率）**：在罕见病变异分析中报告
- **Fold change**：相对于随机SNV的富集
- **SHAP值**：特征重要性

### 基线

- 随机SNV（~180K随机抽取）
- 单一标记（ATAC-seq、H3K27ac、DHS、ChIP-seq、footprints、eRNA各自单独）
- GWAS目录本身（fold change 8.24）

### 评测协议

1. 将所有标记按biosource合并为master file
2. 计算GWAS变异与每种标记/组合的重叠
3. 以molQTL为真阳性集，计算precision
4. 对随机SNV重复100次抽样，计算平均fold change
5. 随机森林分类器验证特征重要性
6. 应用于具体性状（白细胞计数、哮喘）展示实用性
7. 用罕见病变异集进行独立验证

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|-------------------|------|
| 六种标记单独及组合的precision比较 | footprints+eRNA组合具有最高precision | 55种组合 vs 单一标记；以三种molQTL为基准 | footprints+eRNA组合在bQTL、raQTL、caQTL中均达到最高precision（Z-score聚类为最高簇） | footprints和eRNA是功能变异的最强预测标记 | 未报告具体precision数值（仅Z-score聚类图） | Results 图3A |
| 随机SNV fold change | footprints+eRNA组合显著富集功能变异 | 100次随机SNV抽样 | footprints+eRNA组合fold change = 13.89；footprints单独 = 7.37；eRNA单独 = 8.09；ATAC-seq = 1.12-1.44 | footprints+eRNA组合远超随机和单一标记 | 未报告置信区间 | Results 图3B |
| 随机森林+SHAP | footprints和eRNA是预测molQTL的最重要特征 | 六种标记作为特征 | SHAP值显示footprints和eRNA为top正向特征 | 独立机器学习方法验证了统计结果 | 未报告模型AUC | Results 图3C |
| DHS中心性分析 | DHS核心区域比扩展区域有更高precision | DHS core vs ±25/50/100bp | DHS core precision约为1.5倍，扩展至100bp不增加 | TF结合位点（footprints）的中心位置更关键 | 未报告具体数值 | Results 图4A-B |
| 罕见病变异验证 | footprints+eRNA组合对罕见功能变异同样有效 | 210个罕见病变异 vs 随机SNP | footprints+eRNA组合precision = 0.65，recall = 0.25；ATAC-seq和H3K27ac precision低但recall高 | 组合标记对罕见变异同样具有高精确率 | 样本量小（210个变异） | Results 图4C-D |
| 白细胞计数性状应用 | FINDER可缩减候选变异集 | ~10K变异缩减至~300 | 约30倍缩减，GO分析显示生物学功能保留 | FINDER可有效应用于GWAS后续分析 | 未进行实验验证 | Results 图5A-C；Table 1 |
| 哮喘性状LD分析 | FINDER可从LD变异中识别功能变异 | 92个LD变异缩减至1个 | rs10173081被识别为候选功能变异，位于髓系开放染色质，影响TF结合 | FINDER可辅助精细定位 | 未进行功能实验验证 | Results 图6A-D |

---

## 11 结论正确解读

**任务范围**：本文的任务是**变异优先级排序**（variant prioritisation），即从GWAS关联变异中识别可能具有功能的候选变异，**不是**因果推断或功能验证。

**oracle/真值输入**：本文使用molQTL（bQTL、raQTL、caQTL）作为「真阳性」基准。这些molQTL本身来自实验数据（等位基因特异性TF结合、报告基因活性、染色质可及性），但molQTL并不等同于因果变异——它们只是与分子表型相关的变异。

**端到端状态**：FINDER框架是**端到端可用的**，从GWAS变异输入到优先级排序输出，但输出的是「候选功能变异」，需要后续实验验证。

**算力成本**：低。主要计算为bedtools交集和precision计算，无需GPU或深度学习训练。

**历史数据依赖**：高度依赖公开数据库（ENCODE、GTRD、PINTS等）的**数据完整性和质量**。eRNA数据覆盖最少（biosource数量最少），可能影响结果的全面性。

**模型依赖**：随机森林仅用于验证特征重要性，不是核心方法。核心方法是简单的集合交集+precision计算。

**最难情形**：
- 细胞类型特异性功能变异（合并策略可能稀释信号）
- 非TF结合机制的功能变异（如影响RNA剪接、3D基因组结构的变异）
- eRNA数据缺失的组织/条件

**群体/领域边界**：本文分析基于人类基因组数据（hg38），主要适用于人类复杂疾病/性状的GWAS变异。对非人类物种或非SNV变异（如indel、结构变异）的适用性未验证。

**不确定性**：
- precision值依赖于molQTL基准集的质量和覆盖度
- 细胞类型不可知策略可能引入假阳性（变异在某种细胞类型中位于footprint内，但在相关细胞类型中并非如此）
- 未报告置信区间或统计显著性检验

**有边界的复述**：在人类基因组中，以现有公开数据为基础，DNase footprints与eRNA的组合标记可以将GWAS候选变异集缩减约30倍，同时保持约55%的基因保留率（以GO分析衡量），其精确率显著高于ATAC-seq或H3K27ac单独使用。该框架适用于常见变异和罕见变异的优先级排序，但需要后续功能实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 低召回率 | footprints+eRNA组合虽然精确率高，但召回率低，导致大量假阴性 | 未明确提及 | Results 图4D（precision 0.65, recall 0.25） |
| eRNA数据覆盖不足 | eRNA数据库的biosource数量最少，可能遗漏组织特异性增强子 | 需要在与GWAS性状相关的细胞类型和条件下进行eRNA profiling（如PRO-seq） | Discussion 第3段 |
| 细胞类型不可知策略的局限 | 合并所有biosource可能引入与性状无关的细胞类型信号 | 利用FORGE2等工具推断相关细胞类型 | Results 图5D；Discussion 第3段 |
| 动态TF结合的遗漏 | DNase footprints反映的是稳态结合，可能遗漏快速交换的TF | 改进footprint检测方法（如酶切偏差校正） | Discussion 第3段（引用Calviello et al., 2019） |
| 未进行功能实验验证 | 识别的候选变异未通过实验（如CRISPR、报告基因）验证 | 未明确提及 | 全文未提及功能验证实验 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| molQTL作为真阳性基准的循环性问题 | molQTL本身来自与标记类似的实验（如DNase-seq的bQTL），用bQTL验证footprints可能高估precision | 如果基准集与预测特征来自同一实验类型，存在循环验证风险 | 使用独立的功能实验数据（如CRISPR验证、eQTL）作为基准重新计算precision | Methods "Data sources"；bQTL来自ChIP-seq的等位基因特异性结合 |
| 合并所有biosource可能掩盖细胞类型特异性信号 | 某些变异可能在特定细胞类型中功能显著，但合并后信号被稀释 | 功能变异具有细胞类型特异性，合并策略可能丢失关键信息 | 按细胞类型分层分析，比较precision差异 | Results 图1A显示biosource重叠度低 |
| 未报告统计显著性 | precision差异未进行统计检验（如bootstrap、Fisher精确检验） | 无法判断footprints+eRNA的优势是否显著 | 对precision差异进行bootstrap置信区间估计 | Results 图3A-B仅展示Z-score聚类 |
| 随机森林模型未报告AUC | 仅报告SHAP值，未报告模型整体性能 | 无法评估模型的实际预测能力 | 计算ROC-AUC、PR-AUC | Methods "Random forest classification" |
| 罕见病变异集规模小（210个） | 样本量小，precision估计的置信区间宽 | 结论的稳健性存疑 | 使用更大规模的ClinVar或HGMD变异集验证 | Results 图4C-D |
| 「功能变异」的定义依赖molQTL | molQTL反映的是分子表型（如TF结合、染色质可及性），不一定是因果变异 | 高precision可能只是高「分子活性」而非高「因果性」 | 使用孟德尔随机化或共定位分析验证因果性 | Discussion 未讨论因果性问题 |
| 未与其他预测工具（如CADD、Eigen、DeepSEA）进行系统比较 | 仅与单一标记比较，未与现有综合预测工具对比 | 无法评估FINDER相对于现有方法的增量价值 | 在相同基准集上比较FINDER与CADD、Eigen、DeepSEA等的precision | 全文未提及与现有工具的系统比较 |

---

## 14 学到什么

**Agent 提炼的知识候选**

| 知识 | 描述 | 可迁移性（面向TF–DNA结合 × AI/物理模拟） |
|------|------|------------------------------------------|
| **「直接功能证据」优于「间接活性标记」** | DNase footprints（TF直接结合）和eRNA（增强子转录活性）比ATAC-seq（开放染色质）和H3K27ac（组蛋白修饰）具有更高的功能变异预测精确率 | 在设计AI预测模型时，应优先使用反映TF直接结合的feature（如footprint、ChIP-exo、甲基化敏感footprint），而非宽泛的染色质可及性特征 |
| **「细胞类型不可知」合并策略** | 在不知道相关细胞类型时，合并所有biosource的标记可以最大化覆盖，且不显著降低精确率 | 在构建TF–DNA结合预测模型时，可考虑跨细胞类型合并训练数据，但需注意细胞类型特异性结合模式的丢失 |
| **精确率-召回率的权衡** | footprints+eRNA组合precision高但recall低（0.25），适合实验验证优先级排序 | 在AI辅助的变异优先级排序中，应根据下游实验成本选择precision-optimal或recall-optimal的阈值 |
| **TF motif + footprint的联合分析** | 通过FABIAN-variant预测TF motif破坏，结合footprint和eRNA证据，可识别具体受影响的TF（如ETS家族） | 可将「motif破坏预测 + footprint证据 + eRNA证据」整合为多模态特征，用于TF–DNA结合亲和力预测模型的输入 |
| **SHAP值用于特征重要性验证** | 随机森林+SHAP可独立验证哪些标记对功能变异预测最重要 | 在AI模型设计中，SHAP值可用于特征筛选和模型可解释性分析，帮助识别哪些实验衍生的TF结合特征最具预测力 |
| **LD分析 + 功能标记的联合策略** | 从LD变异集中，通过footprint+eRNA标记将92个变异缩减至1个候选 | 在物理模拟（如MD）或结构预测中，可先用footprint+eRNA标记筛选候选变异，再进行高成本的构象变化模拟，降低计算负担 |
| **eRNA作为增强子活性的功能读出** | eRNA的存在表明增强子处于活跃转录状态，是比组蛋白修饰更接近功能的标记 | 在预测TF–DNA结合的功能后果时，可将eRNA作为「增强子活性」的标签，用于监督学习或验证 |

---

## 15 与已有知识连接

| 连接对象 | 关系 | 说明 |
|----------|------|------|
| **ENCODE项目**（Dunham et al., 2012） | 数据来源 | 本文的DNase footprints和DHS数据来自ENCODE统一处理的结果 |
| **Vierstra et al., 2020**（Nature Genetics） | 数据来源+方法基础 | DNase footprints的生成方法；该文也展示了footprint在功能变异预测中的应用 |
| **Meuleman et al., 2020**（Nature） | 数据来源 | 共识DHS参考图谱，本文的DHS数据来源 |
| **van Arensbergen et al., 2019**（Nature Biotechnology） | 基准集来源 | 大规模MPRA（raQTL）数据，本文用作真阳性基准之一 |
| **Abramov et al., 2021**（AD ASTRA） | 基准集来源 | 等位基因特异性TF结合QTL（bQTL）数据库 |
| **GTRD**（Kolmykov et al., 2021） | 数据来源 | ChIP-seq和ATAC-seq数据的统一处理数据库 |
| **PINTS**（Yao et al., 2022） | 数据来源 | eRNA数据库，本文的eRNA数据来源 |
| **FABIAN-variant**（Steinhaus et al., 2022） | 工具 | 用于预测TF motif破坏，本文用于分析候选变异对TF结合的影响 |
| **FORGE2**（Breeze et al., 2022） | 工具 | 用于细胞类型特异性DHS富集分析 |
| **Gasperini et al., 2017**（Nature Genetics） | 对比/批评对象 | 该文显示基于染色质特征的变异优先级排序效果有限，本文回应了这一挑战 |
| **Wang et al., 2022**（Nature Reviews Genetics） | 对比/批评对象 | 综述了基于深度学习的非编码变异预测方法，本文指出这些方法对常见变异效果差 |
| **Nasser et al., 2021**（Nature Genetics） | 相关方法 | 使用ABC模型整合染色质状态和增强子-启动子连接预测功能变异，与本文思路互补 |
| **Sollis et al., 2023**（GWAS Catalog） | 数据来源 | GWAS目录数据，本文的GWAS变异来源 |

---

## 16 研究想法

**Agent 生成的研究候选**

### 候选1：基于footprint+eRNA的深度学习特征增强模型

- **名称**：FINDER-Deep：融合footprint与eRNA的深度预测模型
- **来源局限/观察**：本文证明footprints+eRNA具有高precision，但未使用深度学习；现有深度模型（如DeepSEA）未充分利用footprint和eRNA特征
- **核心假设**：将DNase footprint和eRNA作为附加特征通道输入深度学习模型，可提高功能变异预测的precision，同时保持较高recall
- **增量**：在现有模型基础上增加footprint和eRNA特征通道，而非从头训练
- **初步方法**：以DeepSEA或Enformer为骨干，在输入层增加footprint和eRNA的二进制/连续值轨道；在molQTL基准集上比较有无footprint/eRNA通道的precision-recall
- **验证方式**：使用独立的功能实验数据（如CRISPR验证、eQTL）作为测试集
- **创新状态**：unverified

### 候选2：TF结合动力学与功能变异的关系

- **名称**：结合驻留时间（residence time）作为功能变异预测因子
- **来源局限/观察**：本文提到footprint质量与TF驻留时间相关（Discussion引用Sung et al., 2014），快速交换的TF可能产生弱footprint，但本文未深入探讨
- **核心假设**：TF在DNA上的驻留时间（而非仅结合与否）是功能变异预测的更强指标；变异对驻留时间的影响可通过分子动力学（MD）模拟预测
- **增量**：将MD模拟的TF–DNA结合自由能变化与footprint强度结合，构建「结合动力学评分」
- **初步方法**：选择已知footprint的TF–DNA复合物，对变异位点进行MD模拟（如数百ns），计算结合自由能变化（MM-PBSA/GBSA）；与footprint强度变化关联
- **验证方式**：使用已发表的TF结合亲和力实验数据（如HT-SELEX、PBM）验证
- **创新状态**：unverified

### 候选3：细胞类型特异性功能变异预测

- **名称**：Cell-type-aware FINDER：整合单细胞footprint与eRNA的变异优先级排序
- **来源局限/观察**：本文采用细胞类型不可知策略，但承认可能稀释细胞类型特异性信号；eRNA数据覆盖不足是主要局限
- **核心假设**：在特定细胞类型中，footprint+eRNA标记的precision高于合并策略
- **增量**：使用单细胞ATAC-seq（scATAC-seq）和单细胞RNA-seq推断的eRNA活性，构建细胞类型特异性的footprint+eRNA图谱
- **初步方法**：从scATAC-seq数据中推断footprint（如使用TOBIAS或HINT-ATAC），从scRNA-seq中推断eRNA活性；在已知细胞类型特异性功能的GWAS性状（如免疫细胞相关性状）上验证
- **验证方式**：使用细胞类型特异性eQTL或CaQTL数据验证
- **创新状态**：unverified

### 候选4：物理模拟与footprint的交叉验证

- **名称**：MD-guided footprint interpretation：用分子动力学解释footprint强度差异
- **来源局限/观察**：本文使用footprint作为TF结合的代理，但footprint强度受多种因素影响（酶切偏好、TF驻留时间、协同结合），物理机制不明确
- **核心假设**：MD模拟可以解释为什么某些TF产生强footprint而另一些产生弱footprint，从而改进footprint的解读
- **增量**：将MD模拟的TF–DNA结合构象动态与footprint模式关联
- **初步方法**：选择多个TF–DNA复合物（已知footprint质量差异），进行MD模拟，分析DNA主沟/副沟的几何变化、TF–DNA氢键网络、水分子介导的相互作用；与footprint强度关联
- **验证方式**：使用footprint深度测序数据（如DNase-seq、MNase-seq）验证
- **创新状态**：unverified

### 候选5：eRNA与TF协同结合的因果模型

- **名称**：eRNA-TF协同模型：eRNA转录与TF结合的双向因果关系
- **来源局限/观察**：本文使用eRNA作为增强子活性的标记，但eRNA与TF结合的关系是双向的——TF结合驱动eRNA转录，eRNA也可能影响TF结合（通过改变染色质结构）
- **核心假设**：eRNA的存在不仅标记增强子活性，还可能通过R-loop形成或组蛋白修饰影响TF结合稳定性
- **增量**：构建eRNA-TF结合的因果模型，区分「TF结合→eRNA」和「eRNA→TF结合」两个方向
- **初步方法**：使用eRNA敲低/过表达实验数据，结合footprint分析，构建因果推断模型（如Mendelian randomization或instrumental variable分析）
- **验证方式**：使用CRISPR干扰（CRISPRi）靶向eRNA位点，检测footprint变化
- **创新状态**：unverified