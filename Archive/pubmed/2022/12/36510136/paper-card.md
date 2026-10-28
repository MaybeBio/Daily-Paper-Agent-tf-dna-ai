## 01 基本信息
- **标题**: DeepTSS: multi-branch convolutional neural network for transcription start site identification from CAGE data
- **作者与单位**: Grigoriadis, Dimitris; Perdikopanis, Nikos; Georgakilas, Georgios K; Hatzigeorgiou, Artemis G（希腊雅典大学 Diana 实验室，具体单位未提供）
- **期刊/预印本平台**: BMC Bioinformatics（Volume 23, Supplement 2）
- **年份**: 2022-12-13
- **论文类型**: 方法学（Method）文章
- **领域**: 基因组学 / 转录起始位点（TSS）识别 / 深度学习
- **关键词**: CAGE, TSS, Deep learning, Convolutional neural network, Genomic signal processing, Promoter
- **DOI/arXiv 号**: 10.1186/s12859-022-04945-y
- **代码**: https://github.com/DianaLaboratory/DeepTSS
- **数据**: FANTOM5 CAGE 数据（H9 训练，K562 测试）、ENCODE ChIP-Seq（Pol II、H3K4me3、TFBS）、Ensembl v98 基因注释、UCSC phyloP 100-way 保守性评分
- **阅读日期**: 未提供
- **在该方向中的位置**: 本文属于「TF–DNA 互作 × 深度学习」方向中的**转录起始位点（TSS）识别**子任务。TSS 是 TF 结合调控基因表达的**直接下游事件**，本文的多分支 CNN 架构（分别处理序列、GSP 信号、结构特征、保守性）为整合多源特征进行**调控元件功能预测**提供了可迁移的架构范式，与 TF–DNA 结合位点预测任务高度相关。

## 02 一句话总结
本文提出 DeepTSS——一个多分支卷积神经网络，将 CAGE 峰周围的 DNA 序列（one-hot）、基因组信号处理（GSP）特征、DNA 结构特征（bendability、propeller twist）和进化保守性（phyloP）分别输入四个独立卷积分支，在 H9 细胞上训练，用于从 CAGE 数据中区分真实转录起始事件与转录/技术噪声，在 K562 细胞上达到 98% 精确率和 96% 灵敏度，优于 ADAPT-CAGE、TOMETOOLS、CAGER、RECLU、PARACLU 和 iTiSS。

## 03 研究问题
- **具体问题**: CAGE 数据中大量峰（peak）并非真实转录起始事件，而是转录副产物（如剪接中间体、随机 5' 加帽）或技术噪声。如何从 CAGE 峰中准确识别真正的 TSS？
- **为什么重要**: TSS 注释是启动子/增强子表征、基因调控网络解析的基础。CAGE 噪声若未去除，将导致下游分析（如差异启动子使用、增强子 RNA 鉴定）产生系统性偏差。
- **现有方法不足**: 已有方法分为两类——(1) 统计方法（CAGER、RECLU、PARACLU）依赖跨重复样本的峰可重复性，无法处理单样本或低深度数据；(2) 机器学习方法（TOMETOOLS、ADAPT-CAGE）依赖人工特征工程，需要领域专家知识且可能引入主观偏差；iTiSS 需要多数据集联合分析，适用场景受限。
- **精确研究问题 (Can...?)**: Can a multi-branch convolutional neural network that integrates raw DNA sequence, genomic signal processing features, structural DNA features, and evolutionary conservation outperform existing feature-engineered ML methods in distinguishing true TSS-associated CAGE peaks from noise?

## 04 背景与发展脉络
*（注：以下脉络基于本文框架整理，标注「仅本文框架」；未做外部文献系统核验）*

1. **CAGE 技术成熟期（2003–2015）**: CAGE 成为 5' 端转录本定量的金标准，FANTOM 联盟大规模生产数据。**局限**: 噪声问题逐渐暴露。
2. **统计去噪方法（2015–2018）**: CAGER、RECLU、PARACLU 通过跨重复峰可重复性统计过滤噪声。**局限**: 依赖重复样本，单样本失效。
3. **特征工程 + 传统 ML（2018–2021）**: TOMETOOLS（GMM + 随机森林）、ADAPT-CAGE（堆叠模块化 ML，整合结构特征与启动子 motif）。**局限**: 特征工程成本高，可能遗漏关键模式。
4. **深度学习进入调控基因组学（2018–至今）**: CNN 在序列功能预测中展现优势（如 DeepSEA、Basenji 等，本文未直接引用但属同一范式）。**本文位置**: 首次将 GSP 特征、结构特征、保守性评分与 raw sequence 以多分支 CNN 方式融合用于 TSS 识别，是「DL + 多源特征融合」在 CAGE 去噪中的代表工作。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| CAGE 峰包含大量非 TSS 噪声 | 基因内部（内含子/外显子）出现大量 CAGE 峰，与真实启动子峰混淆 | 转录副产物（剪接中间体）、随机 5' 加帽、技术伪迹 | Fig. 1（RAB7A 基因座示例）；Background 节引用文献 [3–5] |
| 统计去噪方法依赖重复样本 | 单样本或重复少的实验无法有效去噪 | 可重复性统计需要跨样本信息 | Background 节对 CAGER/RECLU/PARACLU 的描述 |
| 特征工程方法需要专家知识 | 特征选择主观、可能遗漏关键判别模式 | 人工特征难以覆盖所有生物学信号维度 | Discussion 节对 ADAPT-CAGE 局限性的讨论 |
| 现有方法缺乏单核苷酸分辨率 | 峰级预测无法精确定位 TSS 位置 | 部分方法基于峰聚类而非逐碱基判别 | Results 节对 DeepTSS 单核苷酸分辨率的强调 |

## 06 核心思想

**1) 表面方法**:
DeepTSS 是一个四分支 CNN 架构。每个 CAGE 峰以其代表位置（peak representative，即 5' 标签覆盖最多的碱基）为中心，提取 600 bp 窗口，生成四类特征：① one-hot 编码的 DNA 序列；② GSP 特征（Z-Curve、DNA-walk、paired numeric、tetrahedron 表示）；③ 结构特征（bendability、propeller twist）；④ phyloP 保守性评分。四类特征分别输入四个独立卷积分支（各 2 层卷积），输出拼接后进入全连接层，最终以 sigmoid 输出二分类概率。

**2) 核心洞察**:
- **多源特征互补性**: 不同特征捕捉 TSS 的不同生物学属性——序列编码捕捉 motif 模式，GSP 捕捉 DNA 物理化学周期性，结构特征捕捉启动子区域的可弯曲性/螺旋扭转特性，保守性捕捉进化约束。四者互补，单一特征不足以充分区分真实 TSS 与噪声。
- **分支式架构优于特征拼接**: 将不同特征类型分别输入独立卷积分支，允许网络为每种特征学习专属的局部模式提取器，而非在输入层强制混合异质特征。
- **数据增强策略**: 通过将窗口在峰代表位置上下游 ±100 bp 内以 25 bp 步长滑动，生成 7 个额外训练样本，迫使模型对峰代表位置定位偏差具有鲁棒性。

**3) 可能的普适教训 [Analysis]**:
- 对于 TF–DNA 结合位点预测，本文的多分支架构提示：**不同特征类型（序列 motif、结构可及性、进化保守性、表观遗传信号）应分别建模再融合**，而非简单拼接为单一输入向量。
- 窗口滑动增强是一种轻量级、有效的**位置鲁棒性训练策略**，可迁移到任何以峰/位点为中心的预测任务。

## 07 方法总览

**输入**: 
- CAGE 峰代表位置（用户提供 bam 文件或 bed 文件）
- 参考基因组序列（fasta）
- phyloP 保守性评分（bigWig，可选）

**输出**: 每个 CAGE 峰的二分类概率（真实 TSS vs 噪声）

**模块**:
1. **预处理模块**: 从 bam/bed 提取峰代表位置；过滤低表达峰（默认 TPM ≥ 1）；按距离（默认 50 bp）合并邻近峰
2. **特征提取模块**: 对每个峰代表位置提取 600 bp 窗口，计算四类特征（one-hot 序列、GSP 信号、结构特征、保守性）
3. **多分支 CNN 模块**: 四个独立卷积分支（各 2 层卷积 + leaky ReLU + batch norm），输出拼接
4. **分类模块**: 3 层全连接（120/60/25 节点）+ sigmoid 输出

**训练**:
- 训练数据: H9 细胞 CAGE 峰（N=38,439）
- 正样本: 与 Ensembl 蛋白编码基因 TSS 注释重叠（±1 kb）且同时富集 H3K4me3 和 Pol II 的峰（N=11,304）
- 负样本: 不重叠任何表观标记和 TSS 注释的基因间区峰（N=11,579）
- 排除: 启动子近端（TSS ±1 kb 至 ±10 kb 区域）的峰，避免模糊样本
- 优化器: Adam，学习率 0.001，batch size 256，dropout 0.2，early stopping（patience=10），60 epochs
- 数据增强: 窗口滑动（±100 bp，25 bp 步长，7 个额外样本）

**评测协议**:
- 测试数据: K562 细胞（与训练细胞系 H9 不同，测试跨细胞系泛化能力）
- 基准 1: 蛋白编码基因注释（TSS ±500 bp 为正区域，±50 kb 为负区域）
- 基准 2: ChromHMM 染色质状态（活性转录 vs 弱/抑制转录）
- 基准 3: 实验数据（H3K4me3、TF ChIP-Seq 富集）
- 对比方法: ADAPT-CAGE、TOMETOOLS、CAGER、RECLU、PARACLU、iTiSS

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 峰代表位置识别 | 在 CAGE 峰内定位 5' 标签覆盖最多的碱基 | 提供单核苷酸分辨率的预测锚点 | 输入: CAGE 峰区间；输出: 单碱基位置 | Methods "Overview of DeepTSS" 节 | 预期影响: 失去单核苷酸分辨率，退化为峰级预测 [Analysis] |
| 多分支特征输入 | 将四类特征分别输入独立卷积分支 | 允许网络为异质特征学习专属模式 | 输入: 600 bp 窗口的四类特征；输出: 各分支特征图 | Fig. 2c；Results 图 3a 显示全特征模型最优 | 实测: 图 3a 显示仅用序列+GSP（Sequence-DiS-TSS）性能低于全特征模型；移除结构或保守性分支预期降低性能 [Analysis] |
| 卷积层（每分支 2 层） | 提取局部序列模式 | CNN 可自动学习 motif 级特征，无需人工设计 | 输入: 特征向量；输出: 抽象特征图 | Methods "Network architecture" 节 | 预期影响: 减少卷积层数会降低模式提取能力 [Analysis] |
| 特征拼接 + 全连接层 | 融合多分支特征并分类 | 整合异质特征进行最终判别 | 输入: 拼接特征；输出: sigmoid 概率 | Methods "Network architecture" 节 | 预期影响: 移除拼接层则无法融合多源信息 [Analysis] |
| 窗口滑动数据增强 | 生成位置偏移的训练样本 | 提高对峰代表位置定位误差的鲁棒性 | 输入: 原始窗口；输出: 7 个偏移窗口 | Methods "DeepTSS training" 节 | 预期影响: 移除后模型对代表位置偏差敏感，泛化下降 [Analysis] |

## 09 关键公式符号

本文未提供显式数学公式。核心操作可形式化描述如下（基于 Methods 节文字重建，非原文公式）：

- **峰代表位置**: \( r = \arg\max_i c_i \)，其中 \( c_i \) 为峰内第 \( i \) 个碱基的 5' 标签覆盖数
- **窗口特征提取**: 对每个峰代表位置 \( r \)，提取窗口 \( [r-300, r+300] \)（600 bp）
- **one-hot 编码**: \( X_{seq} \in \{0,1\}^{600 \times 4} \)
- **GSP 特征**: \( X_{GSP} \in \mathbb{R}^{600 \times d_1} \)（Z-Curve 3 维、DNA-walk 1 维、paired numeric 1 维、tetrahedron 3 维）
- **结构特征**: \( X_{struct} \in \mathbb{R}^{600 \times 2} \)（bendability、propeller twist）
- **保守性**: \( X_{cons} \in \mathbb{R}^{600} \)（phyloPhast 评分）
- **模型输出**: \( \hat{y} = \sigma(f_{dense}([h_1; h_2; h_3; h_4])) \)，其中 \( h_i = f_{conv_i}(X_i) \)，\( \sigma \) 为 sigmoid
- **损失函数**: 二元交叉熵 \( L = -\frac{1}{N}\sum [y \log \hat{y} + (1-y)\log(1-\hat{y})] \)

## 10 实验设计与证据链

**数据集/群体**:
- 训练: H9 细胞 CAGE 峰（N=38,439），正样本 11,304，负样本 11,579
- 测试: K562 细胞 CAGE 峰（N=75,127，其中正样本 32,310，负样本 42,817）
- 注释数据: Ensembl v98 蛋白编码基因 TSS、ENCODE Pol II/H3K4me3 ChIP-Seq、ENCODE 161 TF 的 ChIP-Seq（91 细胞类型）、ChromHMM 染色质状态分割

**指标**: 精确率（Precision）、灵敏度（Sensitivity）、准确率（Accuracy）、TP/FP 数量

**评测协议**:
- 基准 1: 蛋白编码基因注释（TSS ±500 bp 正区域，±50 kb 负区域）
- 基准 2: ChromHMM 活性转录 vs 弱/抑制转录状态
- 基准 3: TF ChIP-Seq 和 H3K4me3 峰重叠率
- 跨细胞系测试（H9 训练 → K562 测试）

**基线**: ADAPT-CAGE、TOMETOOLS、CAGER、RECLU、PARACLU、iTiSS

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 基准 1: 蛋白编码基因注释 | DeepTSS 优于现有方法 | 所有算法默认参数，K562 细胞 | DeepTSS: 精确率 0.98，灵敏度 0.96，准确率 95.4%；ADAPT-CAGE: 0.97/0.94；TOMETOOLS: 0.96/0.86；CAGER: 0.97/0.78；PARACLU: 0.97/0.60；RECLU: 0.93/0.79；iTiSS: 0.72/0.01 | DeepTSS 在精确率和灵敏度上均最优 | 未报告统计显著性检验；单细胞系测试 | Table 1；Results 节 |
| 基准 2: ChromHMM 染色质状态 | DeepTSS 预测富集于活性转录区域 | 阳性预测与 ChromHMM 活性转录状态重叠率 | DeepTSS: 96.66% 活性，3.33% 弱/抑制；ADAPT-CAGE: 95.90%/4.09%；TOMETOOLS: 92.59%/7.40%；CAGER: 84.62%/15.37%；iTiSS: 41.58%/58.41% | DeepTSS 预测与活性染色质高度一致 | 未报告阴性预测的染色质状态分布 | Table 2；Fig. 5a, b |
| 基准 3: 实验数据（TF/H3K4me3） | DeepTSS 预测富集 TF 结合和 H3K4me3 | 阳性预测与 TF ChIP-Seq 和 H3K4me3 峰重叠率 | DeepTSS: 98.27% TF，92.04% H3K4me3；ADAPT-CAGE: 97.72%/91.12%；TOMETOOLS: 95.46%/88.12%；CAGER: 87.67%/81.11% | DeepTSS 预测与功能实验证据高度一致 | 重叠率非独立验证，因训练正样本部分基于 H3K4me3/Pol II 定义 | Table 2；Fig. 5c, d |
| 消融分析: 特征组合 | 全特征模型最优 | 不同特征组合的 DeepTSS 变体 | 全特征（序列+GSP+结构+保守性）最优；序列+GSP（Sequence-DiS-TSS）次之 | 多特征融合提升性能 | 未逐一报告每个特征移除的独立消融 | Fig. 3a |
| 跨细胞系泛化 | H9 训练的模型可泛化到 K562 | 训练 H9，测试 K562 | 达到 98% 精确率/96% 灵敏度 | 模型具有跨细胞系泛化能力 | 仅测试一个目标细胞系 | Results 节 |

## 11 结论正确解读

- **任务范围**: 本文解决的是 CAGE 峰的二分类问题（真实 TSS vs 噪声），而非从头预测基因组上的 TSS 位置。输入必须是已检测到的 CAGE 峰。
- **Oracle/真值输入**: 训练标签部分依赖外部注释（Ensembl TSS、H3K4me3/Pol II ChIP-Seq），这意味着正样本定义隐含了「真实 TSS 应具有活性染色质标记」的假设。这可能导致对不依赖 H3K4me3/Pol II 的 TSS（如某些组织特异性或低活性启动子）存在系统性偏差。
- **端到端状态**: 不是端到端系统——需要预先的 CAGE 峰检测步骤（峰聚类、代表位置识别），DeepTSS 仅负责峰分类。
- **算力成本**: 未报告训练时间或硬件需求；推理时间约 4 分钟/40,000 峰（CPU），相对轻量。
- **历史数据依赖**: 训练数据仅来自 H9 细胞，测试仅 K562 细胞。对更多细胞类型、疾病状态或非人类物种的泛化能力未验证。
- **最难情况**: 位于启动子近端（TSS ±1 kb 至 ±10 kb）的峰被完全排除在训练外，意味着模型对「启动子附近但非真实 TSS」的判别能力未知。
- **有边界的复述**: DeepTSS 在 H9 训练、K562 测试的条件下，对 CAGE 峰的二分类（真实 TSS vs 噪声）达到 98% 精确率/96% 灵敏度，优于 6 种现有方法；其优势来源于多分支架构对序列、GSP、结构、保守性四类特征的融合利用。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 特征工程仍存在 | 虽然无需手动特征选择，但 GSP 和结构特征的类型是预先定义的 | 未明确提及 | Discussion 节（隐含） |
| 训练数据单一 | 仅在 H9 细胞上训练 | 未明确提及 | Methods "DeepTSS training" 节（隐含） |
| 依赖外部注释 | 正样本定义依赖 Ensembl TSS 和 ChIP-Seq 数据 | 未明确提及 | Methods "DeepTSS training" 节（隐含） |
| 未报告统计显著性 | 与基线方法的差异未进行统计检验 | 未明确提及 | Results 节（隐含） |

*注: 作者在原文中未设独立的「Limitations」章节，以上为从 Methods 和 Discussion 节推断的隐含局限，非作者明确表述。*

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 正样本定义依赖 H3K4me3/Pol II 共定位 | 可能排除不依赖这些标记的 TSS（如 paused promoter 或低活性 TSS），导致模型对这类 TSS 判别力不足 | 若模型用于全基因组 TSS 注释，可能系统性漏检特定类型启动子 | 用独立 TSS 数据集（如 CAGE 转录起始簇 + 无 ChIP-Seq 过滤）重新评估 | Methods "DeepTSS training" 节 |
| 跨细胞系测试仅 H9→K562 | 两个细胞系均为永生系，且可能共享部分调控程序；不能代表原代细胞或跨组织泛化 | 实际应用中需处理多种细胞类型 | 在多个原代细胞/组织 CAGE 数据上测试 | Results 节 |
| 与 ADAPT-CAGE 的差异较小（精确率 0.98 vs 0.97） | 实际增益可能有限，尤其在考虑计算成本后 | 需要评估增量价值是否值得额外复杂度 | 报告置信区间和效应量 | Table 1 |
| 窗口滑动增强可能引入标签噪声 | 偏移窗口可能包含非 TSS 区域却被标记为阳性，可能降低模型特异性 | 增强策略的收益与噪声代价需权衡 | 对比有无增强的模型在精确率上的差异 | Methods "DeepTSS training" 节 |
| 未报告模型在不同 TSS 形态（sharp vs broad）上的分层性能 | TSS 形态差异可能影响特征重要性 | 不同启动子类型可能需要不同特征 | 按 TSS 形态分层评估 | 未提供 |

## 14 学到什么
*（Agent 提炼的知识候选）*

1. **多分支架构处理异质特征**: DeepTSS 的核心可迁移设计——将序列、信号、结构、保守性等异质特征分别输入独立卷积分支，再融合。对于 TF–DNA 结合位点预测，可类比设计：序列 motif 分支 + DNA 结构（shape）分支 + 进化保守性分支 + 表观遗传（如 DNase-seq、ATAC-seq）分支，避免在输入层强制混合不同尺度和语义的特征。

2. **GSP 特征作为序列的补充表示**: 将 DNA 序列转换为 Z-Curve、DNA-walk 等数值信号，可捕捉序列的全局物理化学周期性，这些信息在 one-hot 编码中不易被 CNN 直接提取。TF–DNA 结合预测中可尝试将 DNA shape（如 minor groove width、roll、helix twist）以类似方式作为独立分支输入。

3. **窗口滑动增强提升位置鲁棒性**: 通过在峰代表位置上下游滑动窗口生成训练样本，迫使模型对位置偏差不敏感。TF–DNA 结合预测中，ChIP-seq 峰的中心定位常存在 ±50 bp 偏差，此策略可直接迁移。

4. **跨细胞系训练/测试协议**: 在一种细胞类型上训练、另一种上测试，是评估模型泛化能力的有效协议。TF–DNA 结合预测中，不同细胞类型的 TF 结合谱差异大，此协议可检验模型是否学到通用结合规则而非细胞类型特异过拟合。

5. **多维度评测基准**: 本文使用注释（Ensembl TSS）、表观遗传状态（ChromHMM）、实验数据（ChIP-Seq）三重基准评测，比单一指标更全面。TF–DNA 结合预测可类比：序列 motif 富集、染色质可及性、表达相关性等多维度验证。

6. **特征融合的消融分析**: 通过比较不同特征组合的模型性能（Fig. 3a），系统评估各特征贡献。TF–DNA 结合预测中应报告每种特征（序列、结构、保守性、表观）的独立贡献和交互效应。

## 15 与已有知识连接

- **与 TF–DNA 结合预测的关系**: TSS 是 TF 结合的直接功能后果，DeepTSS 识别的真实 TSS 区域可作为 TF 结合位点预测的**正样本来源**或**候选区域筛选**。其多分支架构与 DeepSEA（序列-only CNN）、Basenji（序列+表观）等形成对比，展示了多源特征融合的替代方案。
- **与 DNA shape 预测的联系**: DeepTSS 使用的 bendability 和 propeller twist 特征与 TF–DNA 结合中的 DNA shape 读取（如 Zhou et al. 2013 的 DNAshape 方法）高度相关。可迁移思路：将 DNA shape 特征作为独立分支与序列分支并行，可能提升 TF 结合特异性预测。
- **与进化保守性特征的联系**: phyloP 保守性在 TF 结合预测中已被广泛使用（如 motif conservation 评分），DeepTSS 将其作为独立输入分支的做法提示：保守性信息可与序列信息互补，而非简单相乘或相加。
- **与 CAGE 在调控基因组学中应用的联系**: FANTOM5 的 CAGE 数据已被用于增强子 RNA（eRNA）鉴定和启动子-增强子互作研究。DeepTSS 的去噪能力可提升这些下游分析的质量。
- **与深度学习架构演进的联系**: 多分支 CNN 架构与「多模态学习」范式一致，与同时期工作如 Enformer（序列+表观多任务）形成互补——DeepTSS 展示了在**特征层面**而非**任务层面**的多模态融合。

## 16 研究想法
*（Agent 生成的研究候选）*

1. **候选名称**: TF-DNAshape-MultiBranch——将 DeepTSS 多分支架构迁移到 TF 结合位点预测
   - **来源局限/观察**: DeepTSS 证明多分支融合（序列+GSP+结构+保守性）优于单一特征；TF 结合预测中 DNA shape 已被证明重要但常以手工特征或简单拼接方式使用
   - **核心假设**: 将 DNA shape 特征（minor groove width、roll、helix twist、propeller twist）作为独立 CNN 分支与序列 one-hot 分支并行，可提升 TF 结合位点预测的精确率
   - **初步方法**: 在 ENCODE ChIP-seq 数据集上，对每个 TF 构建四分支 CNN（序列、DNA shape、保守性、染色质可及性），与单序列 CNN 和特征拼接 CNN 对比
   - **验证方式**: 跨细胞系测试（训练 GM12878，测试 K562）；与 DNAshape 传统方法对比；消融分析各分支贡献
   - **创新状态**: unverified

2. **候选名称**: TSS-TF-Joint——联合建模 TSS 识别与 TF 结合的多任务学习
   - **来源局限/观察**: DeepTSS 仅做 TSS 二分类，未利用 TF 结合信息；TF 结合预测通常独立于 TSS 注释
   - **核心假设**: TSS 识别和 TF 结合预测是相关任务，多任务学习可互相正则化，提升两者性能
   - **初步方法**: 共享底层序列编码器，分别输出 TSS 概率和 TF 结合概率；在 FANTOM5 CAGE + ENCODE ChIP-seq 联合数据上训练
   - **验证方式**: 对比单任务模型；检验 TSS 预测是否受益于 TF 结合信息（反之亦然）
   - **创新状态**: unverified

3. **候选名称**: DeepTSS-Interpret——基于注意力机制的可解释 TSS 预测
   - **来源局限/观察**: DeepTSS 使用标准 CNN，缺乏对预测依据的定位能力；TSS 预测的生物学可解释性对下游实验验证至关重要
   - **核心假设**: 在 DeepTSS 架构中引入注意力层或使用可解释性工具（如 DeepLIFT、Integrated Gradients），可定位决定 TSS 判别的关键序列 motif 和结构特征
   - **初步方法**: 在 DeepTSS 卷积层后添加注意力机制；对预测结果进行归因分析，提取关键 motif 并与已知 TF 结合 motif 比对
   - **验证方式**: 归因分析发现的 motif 是否富集已知 TF 结合位点；注意力权重是否集中在启动子核心区域
   - **创新状态**: unverified

4. **候选名称**: Cross-Species-TSS——跨物种 TSS 预测的迁移学习
   - **来源局限/观察**: DeepTSS 仅使用人类数据训练和测试；TSS 机制在哺乳动物中保守，但物种特异差异未知
   - **核心假设**: 人类训练的 DeepTSS 可迁移到小鼠等模式生物，且通过少量物种特异数据微调可进一步提升
   - **初步方法**: 使用 FANTOM5 小鼠 CAGE 数据测试人类训练模型；比较零样本迁移 vs 微调迁移
   - **验证方式**: 跨物种精确率/灵敏度对比；分析物种特异特征（如 GC 含量差异）对性能的影响
   - **创新状态**: unverified

5. **候选名称**: TSS-Noise-Robust——面向低质量 CAGE 数据的鲁棒 TSS 识别
   - **来源局限/观察**: DeepTSS 训练数据来自高质量 H9 样本；实际应用中 CAGE 数据质量参差不齐
   - **核心假设**: 通过对抗训练或噪声注入，可提升模型对低深度、高噪声 CAGE 数据的鲁棒性
   - **初步方法**: 在训练中注入模拟噪声（随机标签偏移、低覆盖度采样）；在低质量 CAGE 样本上测试
   - **验证方式**: 对比标准训练 vs 鲁棒训练的模型在低质量数据上的性能下降幅度
   - **创新状态**: unverified