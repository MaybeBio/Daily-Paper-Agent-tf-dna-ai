## 01 基本信息

- **标题**：The potential of AI models to identify regulatory variants underlying cattle traits
- **作者**：Zhao R; Owen R; Marr M; Jayaraman S; Chue Hong N; Talenti A; Hassan M; Prendergast J
- **单位**：未提供（根据基金信息推测与 University of Edinburgh / CTLGH 相关）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2024-08-06
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：调控基因组学 × 机器学习；物种比较（人 vs 牛）
- **关键词**：regulatory variants, cattle, machine learning, eQTL, MPRA, conservation, Enformer, variant prioritization
- **DOI/arXiv 号**：10.1101/2024.08.01.606140
- **代码**：https://github.com/evotools/nf-VarAnno ；https://github.com/evotools/functional-variant-prediction
- **数据**：https://doi.org/10.5281/zenodo.13342541（牛保守性分数）；https://doi.org/10.5281/zenodo.14901001（牛模型）
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文聚焦 **TF–DNA 结合机制** 的间接层面——通过整合序列保守性、染色质状态、TF motif 距离等特征，用梯度提升树（CatBoost）预测调控变异。其核心价值在于：(1) 首次为牛生成 PhyloP/PhastCons 保守性分数；(2) 系统比较了人类与牛模型在 eQTL 与 MPRA 数据上的性能差异；(3) 评估了 Enformer 深度学习特征对调控变异预测的增量贡献（结论为增量极小）。对 TF–DNA 结合机制研究而言，本文提供了「哪些特征对跨物种调控变异预测最重要」的实证证据，以及「训练数据质量（eQTL vs MPRA）比模型复杂度更关键」的洞见。

---

## 02 一句话总结

本文开发了一个物种无关的变异注释流程（nf-VarAnno），首次为牛生成 PhyloP/PhastCons 保守性分数，并训练 CatBoost 模型预测调控变异；在人类数据上达到 AUROC 0.86、牛 0.73，但发现 Enformer 深度特征几乎不提升性能，且人类与牛的性能差距主要源于牛训练集（eQTL）质量不足而非特征缺失。

---

## 03 研究问题

- **具体问题**：能否用机器学习模型在牛基因组中预测调控变异？哪些数据与特征对跨物种（人→牛）迁移最重要？
- **为什么重要**：牛等家畜的调控变异注释远落后于人类；若能准确预测调控变异，可改进育种值（gEBV）计算和功能变异优先排序，对畜牧业有直接经济效益。
- **现有方法不足**：人类模型（GWAVA, DeepSEA, Enformer, CADD）依赖人类特有的海量染色质数据；牛缺乏保守性分数、染色质数据稀少，且现有工具多为人类中心设计，难以直接迁移。
- **精确研究问题（Can...?）**：Can a species-agnostic variant annotation framework, trained on common features available for both human and cattle, achieve comparable performance in predicting regulatory variants across species, and can deep learning features (Enformer) or additional chromatin data close the performance gap?

---

## 04 背景与发展脉络

> 注：此脉络基于本文 Introduction 与 Discussion 的叙述，属「仅本文框架」，未经外部系统核验。

| 阶段 | 代表方法 | 优点 | 局限 |
|------|----------|------|------|
| 早期功能预测 | GWAVA (Ritchie 2014) | 首次用随机森林整合多类注释 | 依赖 HGMD 变异，人类中心 |
| 深度学习时代 | DeepSEA (Zhou & Troyanskaya 2015) | CNN 从序列预测染色质，端到端 | 需大量人类染色质数据训练 |
| 大规模预训练 | Sei (Chen 2022), Enformer (Avsec 2021) | 覆盖数千染色质谱，泛化强 | 人类中心；对单碱基效应分辨率有限 |
| 物种迁移尝试 | 本文 nf-VarAnno | 物种无关注释 + 保守性分数生成 | 牛训练数据质量仍为瓶颈 |

**本文主张的位置**：填补「人类模型 → 家畜应用」的空白，强调**训练数据质量**（gold-standard regulatory variant sets）比**模型复杂度**更关键，并首次为牛提供可复用的保守性分数资源。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 牛缺乏保守性分数 | PhyloP/PhastCons 仅人类可用 | 多序列比对未包含牛或未计算 | Results 节「Novel variant annotation pipeline」；作者首次用 Cactus 241-way 比对计算 |
| 牛染色质数据稀少 | 仅 95 个牛染色质特征 vs 人类 1,554 个 | 牛表观基因组计划规模有限 | Methods 节「Variant annotation pipeline」 |
| eQTL 训练集质量差 | 牛 eQTL 模型 AUROC 0.73 < 人类 0.86 | 牛 eQTL 来自 RNA-seq 变异调用，LD 强、样本异质 | Results 图 4A；Discussion 节 |
| 跨物种迁移困难 | 人类预训练模型直接用于牛效果差 | 序列保守性、motif 距离等特征需物种特异化 | Results 节「Human omics data does not improve cattle models」 |
| Enformer 特征增量极小 | 加入 5,313 个 Enformer 特征后 AUROC 仅 +0.01 | 深度学习模型对单碱基调控效应分辨率有限 | Results 图 5A；Discussion 节引用 Huang 2023 |
| 变异优先排序的 LD 干扰 | GWAS 峰内难以定位因果变异 | 牛群体 LD 强，eQTL 精细定位困难 | Introduction 节 |

---

## 06 核心思想

**1) 表面方法**：构建 nf-VarAnno 流程，整合五类注释（保守性、位置属性、VEP、序列上下文、Enformer 预测），用 CatBoost 训练二分类模型区分调控/非调控变异。

**2) 核心洞察**：
- **特征可迁移性**：人类与牛调控变异共享大量特征规律（如保守性、motif 距离），因此「常见特征集」足以跨物种建模。
- **数据质量 > 模型复杂度**：牛 eQTL 与人类 eQTL 的性能差距（0.73 vs 0.86）在改用 MPRA 数据后大幅缩小（牛 ~0.81），说明差距主要来自训练标签质量而非特征不足。
- **深度学习特征的边际价值有限**：Enformer 的 5,313 维预测特征对分类性能几乎无提升，提示传统注释已捕获大部分可学习信号。

**3) 可能的普适教训 [Analysis]**：在调控变异预测中，「训练标签的准确性」与「特征的可迁移性」比「模型架构的先进性」更值得投入资源。对 TF–DNA 结合机制研究而言，这意味着：与其追求更复杂的深度学习模型，不如优先构建高质量、跨物种可比的调控变异标注集（如 MPRA 数据）。

---

## 07 方法总览

- **输入**：人类/牛 SNP 集合（调控变异 + 匹配背景变异），每条变异附带基因组坐标、等位基因、参考基因组版本。
- **注释流程（nf-VarAnno）**：
  1. 保守性：人类用 UCSC PhyloP/PhastCons（100-way/30-way）；牛用 Cactus 241-way 比对计算（首次）
  2. 位置属性：到 TSS、CpG 岛、染色质区域的距离
  3. VEP 注释：变异后果、基因上下文
  4. 序列上下文：5-mer 侧翼序列（one-hot 编码）
  5. Enformer 预测：5,313 个功能基因组信号差异分数
- **模型**：CatBoost（梯度提升树），四模型比较（RF, CatBoost, XGBoost, SVM），CatBoost 因性能/效率胜出
- **训练/评估**：染色体级别留出（leave-out chromosomes）防数据泄漏；指标 AUROC、PR、F1
- **输出**：每个变异的调控概率分数，用于 GWAS 位点优先排序
- **反馈回路**：无显式主动学习；但通过 SHAP 分析迭代特征理解
- **假设**：调控变异与背景变异在注释特征上可区分；人类与牛共享部分调控编码规律

**文字流程**：变异集 → nf-VarAnno 注释 → 特征编码（one-hot + 数值）→ CatBoost 训练（染色体留出交叉验证）→ 模型评估 → SHAP 解释 → 应用于 GWAS 变异优先排序 → 富集分析验证

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 保守性分数生成（牛） | 计算 PhyloP/PhastCons | 牛无现成保守性分数；保守性是调控变异最强预测因子之一 | 输入：Cactus 241-way 比对；输出：牛全基因组保守性分数 | Results 节；Supplementary Fig. 1 显示编码区富集 | 预期大幅降低牛模型性能（保守性在人类模型中为 top 特征）[预期效应] |
| 位置属性计算 | 到 TSS/CpG/染色质距离 | 调控变异富集于启动子、增强子附近 | 输入：变异坐标 + 注释文件；输出：距离特征 | Results 图 2C-H 显示跨物种相似富集模式 | 预期中等性能下降 [预期效应] |
| Enformer 特征 | 5,313 维序列预测差异分数 | 探索深度学习特征能否替代实验染色质数据 | 输入：±196kb 序列；输出：参考/替代等位基因预测差异 | Results 图 5A：加入后 AUROC 仅 +0.01 | 实测影响极小（+0.01），移除几乎无损失 [实测效应] |
| CatBoost 分类器 | 区分调控/背景变异 | 梯度提升树处理混合类型特征高效 | 输入：编码后特征矩阵；输出：调控概率 | Results 图 3A：人类 AUROC 0.86 | 换用 RF 性能接近（0.82），SVM 明显差（0.64）[实测效应] |
| 染色体留出评估 | 防数据泄漏 | 同染色体变异高度相关，随机分割会高估性能 | 输入：染色体分组；输出：独立测试集性能 | Methods 节「Regulatory variant modelling」 | 若改为随机分割，性能可能虚高 [预期效应] |
| SHAP 解释 | 特征重要性排序 | 理解模型决策，指导特征工程 | 输入：训练模型 + 特征矩阵；输出：SHAP 值 | Results 图 3B：距离 TSS、保守性为 top 特征 | 移除后不影响性能，但丧失可解释性 [预期效应] |

---

## 09 关键公式符号

本文未使用显式数学公式。核心概念性「公式」为：

- **调控概率**：P(regulatory | x) = CatBoost(x)，其中 x 为特征向量
- **Enformer 差异分数**：Δ = Enformer(seq_ref) − Enformer(seq_alt)，对 5,313 个输出通道分别计算
- **保守性分数**：PhyloP = −log10(p-value of accelerated substitution rate)；PhastCons = posterior probability of conserved state（标准定义，未在文中重述）

---

## 10 实验设计与证据链

**数据集与规模**：
- 人类：GTEx CaVEMaN 精细定位调控变异 45,987（高置信度，因果概率 >0.5）；背景变异匹配 MAF
- 牛：FarmGTEx eQTL 79,215 个顺式调控变异；牛 SuRE MPRA 66,501 个 raQTL
- 人类 SuRE MPRA：K562 18,717 SNP；HepG2 13,838 SNP
- 人类 GWAS：28,918 个 credible set 变异（Open Targets Genetics）
- 牛 GWAS：4 个性状（体重、体高、体况评分、产奶量），变异数见表 2
- 人类孟德尔病调控变异：345 个（ClinVar 相关）

**指标**：AUROC、PR-AUC、F1、富集倍数（enrichment ratio）

**基线/对比**：
- 人类模型 vs 牛模型（同特征集）
- 人类模型 vs CADD（TraitGym 基准）
- 含/不含 Enformer 特征
- 含/不含牛染色质特征

**评测协议**：染色体留出（leave-out chromosomes）；10 次重复随机背景采样

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 人类高置信度模型 | 特征集可预测人类调控变异 | CatBoost vs RF/XGBoost/SVM | AUROC 0.86 (CatBoost) | 特征集有效 | 不能说明牛模型同样有效 | Results 图 3A |
| 牛 eQTL 模型 | 同特征集可预测牛调控变异 | 牛 vs 人类（同特征） | 牛 AUROC 0.73 < 人类 0.86 | 跨物种可行但存在差距 | 差距原因未定（数据 vs 特征） | Results 图 4A |
| 牛 MPRA 模型 | 训练标签质量影响性能 | 牛 eQTL vs 牛 MPRA | MPRA 模型 ~0.81 | 标签质量是关键因素 | 不能排除特征差异贡献 | Results 图 7 |
| 加入 Enformer 特征 | 深度学习特征提升性能 | 有/无 Enformer 特征 | 人类 +0.01，牛无提升 | Enformer 增量极小 | 不能推广到所有深度学习模型 | Results 图 5A |
| 加入牛染色质特征 | 额外染色质数据提升性能 | 有/无 95 个牛染色质特征 | 无显著提升 | 常见特征已足够 | 不能排除更高质量染色质数据有效 | Results 图 4A；Supplementary Fig. 8 |
| 人类模型迁移到牛 | 人类模型可直接用于牛 | 人类模型 vs 牛模型（牛数据测试） | 人类模型 AUROC 0.67-0.68 < 牛模型 0.73 | 物种特异模型更优 | 不能说明迁移完全无效 | Results 节「Human omics data does not improve cattle models」 |
| GWAS 富集分析 | 模型可富集因果变异 | 牛 4 性状 + 人类 83 性状 | 最高 18 倍富集（牛产奶量） | 模型可用于变异优先排序 | 富集不等于因果验证 | Results 图 8-9；表 2 |
| GC 基因座案例 | 模型可定位已知增强子 | 预测分数 vs 已知功能变异 | 最高分变异位于增强子区域 | 模型可识别已知调控元件 | 单案例，需更多验证 | Results 图 10 |

---

## 11 结论正确解读

- **任务范围**：本文预测的是「变异是否具有调控效应」（regulatory vs non-regulatory），而非「变异如何改变 TF 结合亲和力」或「调控效应的方向/幅度」。对 TF–DNA 结合机制研究，本文提供的是**候选调控变异的优先排序工具**，而非结合机制解释。
- **Oracle/真值输入**：训练标签来自 eQTL 精细定位（CaVEMaN 因果概率）和 MPRA 实验，均为统计推断或体外实验，非体内功能验证。
- **端到端状态**：非端到端。模型依赖预计算注释（保守性、染色质距离等），不直接从序列预测。
- **算力成本**：CatBoost 训练成本低；Enformer 推理需 GPU 但单变异成本可控。
- **历史数据依赖**：依赖 GTEx/FarmGTEx 的 eQTL 定义，受样本量、组织覆盖、变异检测方法影响。
- **模型依赖**：仅测试了树模型（RF/CatBoost/XGBoost/SVM），未测试深度序列模型（除 Enformer 特征外）。
- **最难情形**：远端增强子变异、非编码 RNA 区域、结构变异附近的 SNP。
- **群体/领域边界**：牛（Bos taurus）与人类；其他家畜（猪、鸡）未验证。
- **不确定性**：牛 eQTL 模型 AUROC 0.73 的误差范围未报告；MPRA 模型性能基于未发表数据（「unpublished」）。

**有边界的复述**：本文开发的框架可在人类（AUROC 0.86）和牛（AUROC 0.73）中有效区分 eQTL 定义的调控变异与背景变异，并在牛 MPRA 数据上达到 ~0.81；该性能主要来自保守性、位置、motif 距离等传统特征，Enformer 深度特征增量极小；模型可对 GWAS 变异实现最高 18 倍富集，但牛模型性能受限于训练标签质量。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 牛训练数据质量不足 | 牛 eQTL 模型性能低于人类；eQTL 来自 RNA-seq 变异调用，LD 强 | 生成更高质量的金标准调控变异集（如更大规模 MPRA、全基因组测序） | Discussion 节 |
| 牛染色质数据有限 | 仅 95 个特征，且加入后无性能提升 | 需要更多牛组织/细胞类型的表观基因组数据 | Discussion 节 |
| 跨物种迁移效果有限 | 人类模型直接用于牛效果差（AUROC 0.67-0.68） | 物种特异模型优于迁移模型 | Results 节「Human omics data does not improve cattle models」 |
| Enformer 特征未充分利用 | 仅用差异分数，未微调模型 | 未来可探索微调或端到端训练 | Discussion 节 |
| 牛 MPRA 数据未发表 | 66,501 个 raQTL 来自「unpublished」数据 | 待同行评审与公开 | Results 节「Model performance in predicting human and cattle MPRA regulatory variants」 |
| 未验证其他家畜 | 仅牛与人类 | 扩展到猪、鸡等物种 | Discussion 节 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 牛 eQTL 模型性能差距归因于「标签质量」 | 也可能因牛基因组注释不完整、保守性分数计算基于旧组装（Btau_5.0.1） | 若归因错误，未来资源投入方向会偏差 | 用相同特征集训练人类模型但随机降质标签，模拟牛标签质量，比较性能下降幅度 | Results 图 4A；Discussion 节 |
| Enformer 特征无增量 | 可能因 CatBoost 无法有效利用高维相关特征，而非 Enformer 本身无信息 | 若为模型-特征交互问题，换用深度学习分类器可能不同 | 用简单线性模型或 MLP 测试 Enformer 特征增量 | Results 图 5A |
| 染色体留出策略 | 仅留出 1-2 条染色体测试，可能低估性能（若测试染色体有特殊结构） | 影响模型泛化性结论 | 多种留出策略（随机、多染色体）对比 | Methods 节「Regulatory variant modelling」 |
| 背景变异选择 | 仅匹配 MAF，未匹配 LD 结构、基因密度等 | 可能引入选择偏差，高估区分度 | 用更严格匹配（如 LD 代理、功能注释密度）重复实验 | Methods 节「Genotype datasets」 |
| GC 基因座案例 | 单案例展示，且「最高分变异位于增强子」可能是巧合 | 案例研究不能证明模型因果定位能力 | 系统评估多个已知增强子-表型关联位点 | Results 图 10 |
| 富集分析未校正多重检验 | 4 性状 × 多模型 × 多阈值，可能产生假阳性富集 | 影响「模型有效」结论的稳健性 | 报告 FDR 校正后富集显著性 | Results 图 8-9；表 2 |
| 牛保守性分数基于 Btau_5.0.1 | 旧组装可能遗漏结构变异、错误定位 | 影响所有依赖保守性特征的结论 | 用 BosTau9 直接计算保守性分数对比 | Methods 节「Variant annotation pipeline」 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **跨物种特征迁移的可行性**：保守性、motif 距离、位置属性等「通用调控特征」可在人类与牛之间迁移，无需物种特异的大规模染色质数据。→ 对 TF–DNA 结合研究：可优先构建跨物种共享的特征集，而非依赖单一物种的表观数据。

2. **训练标签质量 > 模型复杂度**：牛 eQTL 模型（0.73）与牛 MPRA 模型（~0.81）的性能差异，说明「金标准标签」比「更复杂模型」更能提升预测。→ 对 TF–DNA 结合研究：投入资源生成高质量结合实验数据（如 MPRA、STARR-seq）比优化模型架构更有效。

3. **深度学习特征（Enformer）的边际价值有限**：在传统注释基础上，5,313 维 Enformer 特征仅带来 +0.01 AUROC。→ 对 TF–DNA 结合研究：若已有保守性、motif 距离等特征，引入大规模预训练模型（如 Enformer、DNABERT）前应做成本-收益评估。

4. **染色体留出评估的必要性**：同染色体变异高度相关，随机分割会高估性能。→ 对 TF–DNA 结合研究：评估结合位点预测模型时，应按染色体/区域划分训练测试集，避免数据泄漏。

5. **SHAP 可解释性分析的价值**：通过 SHAP 识别 top 特征（保守性、距离 TSS），可指导特征工程和生物学假设生成。→ 对 TF–DNA 结合研究：用 SHAP 分析可揭示哪些序列特征（如 motif 强度、GC 含量）对结合预测贡献最大。

6. **保守性分数的物种特异性生成**：牛 PhyloP/PhastCons 首次可用 Cactus 241-way 比对计算，且可有效迁移到 BosTau9。→ 对 TF–DNA 结合研究：对非模式物种，可参考此流程生成保守性特征，无需依赖人类中心数据库。

7. **eQTL 与 MPRA 的互补性**：eQTL 反映体内调控效应但受 LD 干扰；MPRA 提供等位基因特异性效应但脱离染色质环境。两者联合可提高训练标签质量。→ 对 TF–DNA 结合研究：结合体内（eQTL）与体外（MPRA）数据可构建更稳健的训练集。

---

## 15 与已有知识连接

- **GWAVA (Ritchie et al., 2014)**：本文与 GWAVA 同属「特征工程 + 传统 ML」路线，但 GWAVA 仅限人类，本文扩展至牛并新增保守性分数。
- **DeepSEA (Zhou & Troyanskaya, 2015)**：DeepSEA 用 CNN 从序列预测染色质，本文用预计算染色质距离特征，两者互补；本文结果显示传统特征已接近深度学习特征上限。
- **Enformer (Avsec et al., 2021)**：本文直接使用 Enformer 输出作为特征，发现增量极小，与 Huang et al. (2023) 的批评一致——深度学习模型对单碱基调控效应分辨率有限。
- **CADD (Schubach et al., 2024)**：本文在 TraitGym 基准上与 CADD 对比（~0.67 vs ~0.69），显示轻量模型可接近重型集成方法。
- **FarmGTEx (Liu et al., 2022)**：本文使用 FarmGTEx 牛 eQTL 数据作为训练标签，是该方法在牛中的直接应用。
- **Xiang et al. (2019, 2021, 2023)**：FAETH 分数相关工作，本文与其共享「保守性 + 调控注释」思路，但用 ML 替代线性加权。
- **GPN-MSA (Benegas et al., 2025)**：本文对比了 DNA 语言模型（GPN-MSA ~0.66），显示传统特征模型（~0.67）与之相当。
- **候选方向 [Analysis]**：本文未使用 AlphaFold 等结构预测工具；对 TF–DNA 结合机制研究，可探索将结构特征（如 AlphaFold3 预测的 TF-DNA 结合界面）与本文的调控变异特征融合。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

**候选 1：基于结构感知的跨物种调控变异预测**
- **来源局限/观察**：本文特征集不含蛋白质结构信息；TF–DNA 结合机制中，变异对结合亲和力的影响取决于三维结构。
- **核心假设**：将 AlphaFold3 或 RoseTTAFoldNA 预测的 TF-DNA 结合界面残基接触信息作为特征，可提升调控变异预测性能，尤其在远端增强子区域。
- **增量**：在本文 nf-VarAnno 基础上增加结构特征通道，比较 AUROC 提升。
- **初步方法**：对候选变异所在 TF 结合位点，用结构预测工具生成复合物模型，提取界面距离、氢键变化等特征，与现有特征拼接训练 CatBoost。
- **验证方式**：在牛 MPRA 数据上比较有/无结构特征的 AUROC；在已知 TF 结合位点突变数据集上验证。
- **创新状态**：unverified

**候选 2：利用 MPRA 数据微调 DNA 语言模型用于牛调控变异**
- **来源局限/观察**：本文发现 Enformer 特征增量极小，但未尝试微调；且牛缺乏预训练 DNA 语言模型。
- **核心假设**：在牛 MPRA 数据上微调人类预训练 DNA 语言模型（如 Nucleotide Transformer），可捕获牛特异调控语法。
- **增量**：相比本文的「冻结特征」策略，微调可能释放深度学习模型潜力。
- **初步方法**：用牛 MPRA 阳性/阴性变异对预训练模型进行对比微调，输出变异效应分数，与 CatBoost 集成。
- **验证方式**：牛 eQTL 留出染色体测试；与本文 CatBoost 基线对比。
- **创新状态**：unverified

**候选 3：TF-motif 距离特征的精细化——基于位置权重矩阵（PWM）的亲和力变化评分**
- **来源局限/观察**：本文仅用「到最近 motif 的距离」作为特征，未利用 motif 序列本身的变化。
- **核心假设**：对变异位点计算参考/替代等位基因的 PWM 得分差异（ΔPWM），可提供比距离更精细的 TF 结合信息。
- **增量**：在本文特征集中加入 ΔPWM 特征，测试对近端调控变异（<1kb TSS）的预测提升。
- **初步方法**：用 HOMER 或 CIS-BP 的 PWM 库，对每个变异计算 ΔPWM，作为新特征加入 CatBoost。
- **验证方式**：在牛 MPRA 数据上比较有/无 ΔPWM 特征的 AUROC；分层分析近端 vs 远端变异。
- **创新状态**：partially checked（PWM 方法成熟，但未在本文框架中测试）

**候选 4：调控变异预测与 gEBV 育种的端到端集成**
- **来源局限/观察**：本文仅验证了富集能力，未评估对育种值预测的实际增益。
- **核心假设**：将调控变异预测分数作为权重纳入 gEBV 计算，可提高经济性状基因组预测准确性。
- **增量**：从「变异分类」到「育种应用」的闭环验证。
- **初步方法**：用本文模型对牛 50K 芯片 SNP 打分，将分数作为先验权重引入 BayesR 或 BayesRC 模型，比较 gEBV 预测准确性（如相关性、MSE）。
- **验证方式**：交叉验证；与未加权基线对比。
- **创新状态**：unverified

**候选 5：跨物种（人-牛-猪）调控变异预测的统一框架**
- **来源局限/观察**：本文仅比较了人与牛，未测试其他家畜。
- **核心假设**：调控密码在哺乳动物中高度保守，统一框架可同时提升多物种预测。
- **增量**：扩展 nf-VarAnno 至猪、羊，验证特征可迁移性边界。
- **初步方法**：对猪/羊生成保守性分数（基于现有比对），用牛模型直接测试，再用少量本地数据微调。
- **验证方式**：各物种 MPRA/eQTL 数据独立测试。
- **创新状态**：unverified