## 01 基本信息

- **标题**：Machine Learning Prediction of Non-Coding Variant Impact in Human Retinal cis-Regulatory Elements
- **作者与单位**：VandenBosch, Leah S; Luu, Kelsey; Timms, Andrew E; Challam, Shriya; Wu, Yue; Lee, Aaron Y; Cherry, Timothy J（单位未在提供材料中列出）
- **期刊/预印本平台**：Translational Vision Science & Technology
- **年份**：2022
- **论文类型**：原创研究（方法学 + 应用）
- **领域**：计算基因组学 / 调控基因组学 / 眼科遗传学
- **关键词**：机器学习、GKM-SVM、deltaSVM、视网膜、cis-regulatory elements、非编码变异、ATAC-seq、转录因子结合基序
- **DOI/arXiv 号**：10.1167/tvst.11.4.16
- **代码**：未提供（提及使用 LS-GKM 工具包，但未提供自定义代码仓库）
- **数据**：ATAC-seq 数据已存入 UCSC Genome Browser track hub（https://tinyurl.com/CherryLab-EyeBrowser）；VISIONS 数据库（http://genome.ucsc.edu/s/CherryLab/VISIONS_TrackHub）
- **阅读日期**：未提供
- **在「蛋白质-DNA 互作 × AI/物理模拟」方向中的位置**：本文属于「TF–DNA 结合机制 × 机器学习」交叉方向，具体为利用 GKM-SVM（一种基于序列 k-mer 特征的核方法）从 ATAC-seq 定义的开放染色质区域（推定 CRE）中学习序列语法，并通过 deltaSVM 框架预测单核苷酸变异对 TF–DNA 结合潜力的影响。该方法不依赖 3D 结构或物理模拟，而是纯序列驱动的统计学习，属于该方向中「序列-功能映射」类方法，与 DeepSEA、Enformer 等深度学习模型同属一个范式家族，但采用更轻量的核方法。

---

## 02 一句话总结

本文利用成人视网膜 ATAC-seq 数据定义推定 cis-regulatory elements（CREs），训练 GKM-SVM 分类器区分视网膜 CRE 与基因组背景序列，并通过 deltaSVM 框架对 3,773 个 hold-out CRE 中所有可能的单核苷酸变异进行功能影响评分，发现负向评分变异富集于高保守位点、TF 结合基序核心序列及 CRE 中心区域，且与小鼠视紫红质启动子 MPRA 数据呈正相关（Pearson r = 0.506）。

---

## 03 研究问题

- **具体问题**：如何系统性地、高通量地预测人类视网膜 cis-regulatory elements 中非编码单核苷酸变异的功能影响？
- **为什么重要**：约半数视网膜疾病病例无法用编码区变异解释，提示非编码调控变异可能致病；但调控变异的解读缺乏系统性工具，GWAS 和 eQTL 分析在复杂组织中的分辨率有限。
- **现有方法不足**：
  - 实验方法（如 MPRA）通量有限、成本高，难以覆盖全基因组所有潜在调控位点；
  - 已有的计算工具多基于通用基因组模型，缺乏组织特异性（视网膜）训练数据；
  - 传统序列保守性分析（如 phyloP）无法提供变异影响的定量预测，且对组织特异性增强子不敏感。
- **精确研究问题（Can...?）**：Can a GKM-SVM model trained on adult human retinal ATAC-seq-defined cis-regulatory elements accurately predict the functional impact of single nucleotide variants, as validated by phylogenetic conservation, TF motif disruption, allele frequency, and independent MPRA data?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 及引用文献，属于「经外部核验」的领域发展框架。

1. **阶段一：非编码变异与疾病关联的发现**（~2010s 前）
   - 代表性方法：GWAS、eQTL、单病例候选变异分析
   - 优点：建立了非编码变异与疾病的关联证据
   - 局限：关联不等于功能；无法区分 driver 与 passenger 变异；组织特异性差

2. **阶段二：实验性功能验证**（~2010s）
   - 代表性方法：MPRA、STARR-seq、CRISPR 编辑
   - 优点：直接测量变异对表达的影响
   - 局限：通量有限、成本高、难以覆盖所有候选变异

3. **阶段三：序列-功能预测模型**（~2015s 至今）
   - 代表性方法：DeepSEA、Basenji/Enformer、GKM-SVM/deltaSVM
   - 优点：可对全基因组所有变异进行评分；训练后可快速推断
   - 局限：依赖训练数据的组织/细胞类型特异性；对远端调控机制建模有限；解释性弱于基序分析

4. **阶段四：组织特异性调控变异解读**（本文位置）
   - 本文主张：利用成人视网膜 ATAC-seq 定义组织特异性 CRE 集，训练 GKM-SVM，生成 deltaSVM 评分数据库（VISIONS），实现视网膜非编码变异的系统解读
   - 与已有工作的区别：此前 GKM-SVM/deltaSVM 已应用于小鼠视网膜增强子（Kwasnieski 等），但本文首次将其扩展至人类视网膜全基因组 CRE 集，并构建公开查询资源

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 非编码变异功能解读困难 | 约半数视网膜疾病病例无法用编码变异解释 | 非编码基因组庞大且功能注释不完整；CRE 功能具有高度组织特异性 | Introduction 第 1 段（"as many as half of all cases cannot be explained by variants in protein-coding genes alone"） |
| 实验验证通量不足 | MPRA 等实验方法只能覆盖有限区域 | 实验成本高、周期长，难以全基因组覆盖 | Introduction 第 2 段（"Identifying and investigating all potential regulatory regions and putative variants is a monumental task"） |
| 已有计算工具缺乏组织特异性 | 通用模型对视网膜 CRE 的预测精度有限 | 不同组织的染色质状态和 TF 结合模式差异显著 | Introduction 第 3 段（"approaches such as a gapped k-mer support vector machine (GKM-SVM) can effectively predict... in the context of specific mouse retinal enhancers"） |
| 变异影响的定量评分缺失 | 保守性分析只能给出二元/连续保守分数，无法直接预测功能后果 | 保守性 ≠ 功能；增强子序列可容忍一定变异而不影响功能 | Results 图 3B（保守性与 deltaSVM 相关性分析） |
| 基序破坏的精细定位困难 | 需要知道变异具体破坏哪个 TF 基序的哪个关键碱基 | 基序内不同位置的容忍度不同，需要碱基分辨率分析 | Results 图 4C（单碱基分辨率 deltaSVM 分析） |

---

## 06 核心思想

### 1) 表面方法

- 用成人视网膜 ATAC-seq 峰定义推定 CRE（阳性集），用基因组背景序列（GC-matched、非重叠）作为阴性集；
- 训练 GKM-SVM 分类器（L=11, k=7, d=3, C=1, t=2, e=0.005），学习区分视网膜 CRE 与背景的序列特征；
- 对 hold-out 集中的每个 CRE 进行全碱基饱和突变，用 deltaSVM 计算每个 SNV 的预测功能影响分数；
- 将 deltaSVM 分数与等位基因频率（gnomAD）、系统发育保守性（phyloP）、TF 基序位置及独立 MPRA 数据交叉验证。

### 2) 核心洞察

- **序列语法可学习**：GKM-SVM 能够从 ATAC-seq 定义的开放染色质区域中提取有生物学意义的序列特征（即 TF 结合基序的序列偏好），无需显式提供基序注释；
- **deltaSVM 分数具有生物学效度**：负向评分变异（预测破坏 CRE 功能）在进化保守位点富集、在 TF 基序核心序列集中、在 CRE 中心区域富集，且与实验测得的表达变化相关；
- **组织特异性是关键**：视网膜训练的模型对视网膜 CRE 的评分显著高于其他组织来源的 CRE，说明模型捕捉了视网膜特异的调控语法。

### 3) 可能的普适教训 [Analysis]

- **轻量核方法在中小规模数据上可媲美深度学习**：GKM-SVM 在 ~15k 训练样本上达到 AUC 0.95，说明对于序列分类任务，特征工程（gapped k-mer）加核方法在数据量有限时是高效选择；
- **ATAC-seq 作为 CRE 代理标记的可行性**：开放染色质区域虽不等同于增强子，但作为训练标签足以学习到有功能的序列特征；
- **变异评分的验证策略可迁移**：将预测分数与多重独立证据（保守性、等位基因频率、基序位置、实验数据）交叉验证，是建立计算预测可信度的通用范式。

---

## 07 方法总览

- **输入**：
  - 阳性集：18,866 个成人视网膜 ATAC-seq 峰（8 个生物学重复，IDR 处理），峰 summit ±150 bp 共 301 bp 序列；
  - 阴性集：1,000,000 个随机基因组区域（GC-matched、与阳性集无重叠）；
  - 外部验证数据：RPE、初级视觉皮层（PVC）、肺成纤维细胞 ATAC-seq；小鼠视紫红质启动子 MPRA 数据（Kwasnieski 等）。
- **输出**：
  - 训练好的 GKM-SVM 分类器；
  - 3,773 个 hold-out CRE 中所有可能 SNV 的 deltaSVM 分数；
  - VISIONS 数据库（39,437 个推定 CRE 的变异评分），可在 UCSC Genome Browser 查询。
- **模块**：
  1. 数据预处理（ATAC-seq 峰调用、阴性集生成、GC 匹配）；
  2. GKM-SVM 训练与五折交叉验证；
  3. 序列词汇表构建（所有 2,097,152 个非冗余 11-mer 打分）；
  4. deltaSVM 变异评分（饱和突变 + 词汇表差值）；
  5. 多维度验证（等位基因频率、保守性、基序分析、MPRA 对比）。
- **训练**：GKM-SVM（LS-GKM 包），超参数 L=11, k=7, d=3, C=1, t=2, e=0.005（引自 Shigaki 等 2019）。
- **反馈回路**：无显式迭代反馈；模型训练后固定，用于评分和验证。
- **假设**：
  - ATAC-seq 峰区域代表功能性 CRE；
  - 序列本身（而非染色质状态或 3D 结构）足以预测 CRE 功能；
  - deltaSVM 分数线性反映变异对 CRE 功能的破坏程度。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ATAC-seq 峰调用与 CRE 定义 | 从 8 个视网膜重复中鉴定高置信开放染色质区域 | 提供组织特异的阳性训练集 | 输入：原始 ATAC-seq reads；输出：18,866 个 301-bp 推定 CRE | Methods "Input Data Sources"；IDR 流程保证重复性 | 若移除，模型无组织特异性训练数据，退化为通用模型 |
| 阴性集生成（GC-matched） | 生成与阳性集 GC 含量匹配的非重叠基因组背景序列 | 防止 GC 偏好作为混淆变量 | 输入：阳性集坐标、参考基因组；输出：1M 个 301-bp 阴性序列 | Methods "Input Data Sources"；oPOSSUM GC 匹配 | 若移除，模型可能学习 GC 含量而非序列语法 |
| GKM-SVM 训练 | 学习区分 CRE 与背景的序列特征 | 核心分类器 | 输入：正/负序列集；输出：训练好的 SVM 模型 | Results 图 2A-B（AUC=0.951/0.956） | 若移除，无法生成序列词汇表或变异评分 |
| 11-mer 词汇表构建 | 对所有可能的 11-mer 序列打分 | 为 deltaSVM 提供参考分数 | 输入：训练好的 SVM；输出：2,097,152 个 11-mer 分数 | Methods "Vocabulary and Sequence Scoring" | 若移除，无法计算变异前后分数差 |
| deltaSVM 变异评分 | 计算每个 SNV 对序列分数的影响 | 核心输出 | 输入：参考/变异 11-mer 分数；输出：每个 SNV 的 deltaSVM 分数 | Methods "Variant Impact Scoring"；Results 图 3-5 | 若移除，无法生成变异优先级排序 |
| 多维度验证 | 与等位基因频率、保守性、基序、MPRA 对比 | 建立预测分数的生物学效度 | 输入：deltaSVM 分数 + 外部数据；输出：相关性/富集分析 | Results 图 3-5 | 若移除，预测分数缺乏独立验证，临床解读可信度不足 |
| VISIONS 数据库 | 将评分扩展到 39,437 个 CRE 并公开 | 提供社区资源 | 输入：扩展 CRE 集 + 训练好的模型；输出：UCSC track hub | Results "VISIONS" 部分 | 若移除，方法不可复现，社区无法使用 |

---

## 09 关键公式符号

本文未提供显式数学公式。核心计算逻辑如下：

1. **GKM-SVM 分类决策**（标准 SVM 形式，未在文中显式给出但为方法基础）：
   - 决策函数：f(x) = sign(Σᵢ αᵢ yᵢ K(xᵢ, x) + b)
   - 其中 K 为 gapped k-mer 核，衡量序列 x 与支持向量 xᵢ 在 gapped k-mer 特征空间中的相似度
   - 符号：αᵢ = 支持向量系数；yᵢ = 标签（+1 CRE / -1 背景）；b = 偏置

2. **deltaSVM 变异分数**（核心评分逻辑）：
   - deltaSVM(ref→var) = Σ_{k-mer containing var} score(k-mer_var) − Σ_{k-mer containing ref} score(k-mer_ref)
   - 即：变异位点所在窗口内所有 11-mer 的分数变化总和
   - 负值表示变异使序列更不像 CRE（预测破坏功能）

3. **五折交叉验证**：数据随机分为 5 份，每份轮流作为验证集，其余 4 份训练，报告平均 AUC。

4. **统计检验**：Kruskal–Wallis χ² 检验 + 配对 Wilcoxon 秩和检验（Bonferroni 校正）用于组间比较；Pearson 相关系数用于 deltaSVM 与 MPRA 表达的相关性。

---

## 10 实验设计与证据链

### 数据集/群体/规模/指标/基线/预算/评测协议

- **训练集**：~15k 视网膜 CRE（80% 的 18,866 个 ATAC-seq 峰）+ 等量 GC-matched 阴性序列
- **Hold-out 测试集**：3,773 个视网膜 CRE（20%），用于 deltaSVM 评分和验证
- **外部数据集**：RPE、PVC、肺成纤维细胞 ATAC-seq（用于组织特异性检验）；小鼠 RhoCRE3 启动子 MPRA 数据（Kwasnieski 等 2016）
- **主要指标**：AUC（ROC 和 PR）、Pearson 相关系数、富集分析（基序、保守性）
- **基线/对照**：shuffled-label 模型（随机打乱正负标签）
- **评测协议**：五折交叉验证（分类器）；deltaSVM 分数与外部数据的相关性/富集分析

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| 五折交叉验证 | 模型能区分视网膜 CRE 与背景序列 | 原始模型 vs shuffled-label 模型 | AUC=0.951（ROC），AUC=0.956（PR）；shuffled 模型接近随机 | 模型学到了真实的序列特征 | 未报告精确的 shuffled AUC 数值 | Results 图 2A-B |
| 组织特异性评分 | 模型对视网膜 CRE 评分高于非视网膜 CRE | 视网膜 vs RPE vs PVC vs 成纤维细胞 ATAC-seq 峰 | 视网膜峰平均分最高，RPE 次之，PVC/成纤维细胞最低（P < 2e-16） | 模型具有组织特异性 | 未报告各组织具体分数分布 | Results 图 2C |
| 等位基因频率分析 | 高 deltaSVM 负分变异在人群中更稀有 | deltaSVM 分数 vs gnomAD 等位基因频率 | 极端负分变异等位基因频率更低 | 预测破坏性变异受净化选择 | 未报告具体相关系数 | Results 图 3A |
| 保守性分析 | 负分变异位于高保守位点 | deltaSVM 分数 vs phyloP 分数 | 最负分 bin 平均 phyloP = 0.456；中性 bin = 0.119；正分 bin = 0.101（P < 2e-16） | 预测破坏性变异富集于保守序列 | 保守性为间接证据，非功能验证 | Results 图 3B |
| 基序破坏分析 | 负分变异富集于 TF 基序核心 | deltaSVM 分数 vs HOCOMOCO 基序位置 | 负分变异显著富集于基序核心序列；单碱基分辨率显示基序内关键位置 deltaSVM 更负 | 模型识别到 TF 结合基序的关键碱基 | 未对所有基序逐一验证 | Results 图 4A-C |
| MPRA 对比 | deltaSVM 分数与实验表达变化相关 | 小鼠 RhoCRE3 启动子饱和突变 MPRA vs deltaSVM 预测 | Pearson r = 0.506 | 预测分数与实验功能测量正相关 | 仅一个 CRE 验证；跨物种；r 中等强度 | Results 图 5 |

---

## 11 结论正确解读

- **任务范围**：本文仅预测 SNV 对 CRE 序列"像不像调控元件"的影响，不直接预测对基因表达的影响幅度，也不涉及染色质 3D 结构、表观遗传修饰状态或 TF 浓度等动态因素。
- **Oracle/真值输入**：训练标签为 ATAC-seq 峰（开放染色质），这是 CRE 的代理标记而非功能验证；MPRA 验证仅覆盖一个 CRE（小鼠 RhoCRE3），且为跨物种验证。
- **端到端状态**：非端到端。模型输出的是序列分类分数和变异 delta 分数，不包含从变异到疾病表型的完整因果链。
- **算力成本**：GKM-SVM 为轻量方法，训练成本远低于深度学习模型；但全基因组饱和突变评分需要预计算 11-mer 词汇表，一次性成本较高。
- **历史数据依赖**：模型依赖 ATAC-seq 数据的质量、组织来源（成人视网膜）、以及参考基因组版本（hg38）。
- **模型依赖**：结果依赖于 GKM-SVM 超参数选择（L=11, k=7, d=3 等），这些参数引自先前研究，未在本文中进行系统调优。
- **最难情况**：模型对远离 ATAC-seq 峰中心的远端增强子、或依赖染色质互作的调控机制可能不敏感；对非经典 TF 结合模式（如间接结合、协同结合）的建模能力有限。
- **群体/领域边界**：模型仅针对视网膜组织；对其他组织或细胞类型的适用性未验证。跨物种验证仅在小鼠一个 CRE 上进行。
- **不确定性**：未报告 deltaSVM 分数的置信区间或预测不确定性估计；未进行独立队列验证。

**有边界的复述**：本文证明，在成人视网膜 ATAC-seq 数据上训练的 GKM-SVM 模型能够以高准确率区分推定 CRE 与基因组背景，其 deltaSVM 变异评分与进化保守性、等位基因频率、TF 基序位置及一个独立 MPRA 数据集显著相关，可作为视网膜非编码变异功能优先排序的计算工具，但其直接临床解读能力尚未建立。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 模型基于 ATAC-seq 代理标记 | ATAC-seq 峰代表开放染色质，不等同于功能验证的增强子 | 整合更多功能数据（如 ChIP-seq、Hi-C）以精确定义 CRE | Discussion 第 1 段 |
| 跨物种验证有限 | 仅使用小鼠 RhoCRE3 一个 CRE 的 MPRA 数据 | 在更多人类 CRE 上进行 MPRA 或 CRISPR 验证 | Discussion 第 2 段 |
| 未整合单细胞数据 | 模型基于 bulk ATAC-seq，无法区分细胞类型特异性 | 整合单细胞 ATAC-seq 数据以提高分辨率 | Discussion 第 3 段 |
| 变异评分缺乏直接疾病关联 | 未在患者队列中验证评分与疾病表型的关联 | 与临床遗传学数据整合，评估诊断率提升 | Discussion 第 4 段 |
| 模型可解释性有限 | GKM-SVM 的 gapped k-mer 特征难以直接映射到生物学机制 | 结合基序分析提高可解释性 | Discussion 第 5 段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| AUC 0.95 可能高估泛化能力 | 训练和测试集来自同一批 ATAC-seq 数据（随机 80/20 分割），可能存在数据泄漏或过度拟合 | 真实应用场景是预测新变异/新 CRE，而非同分布数据 | 使用独立视网膜 ATAC-seq 数据集（如不同个体/不同实验室）进行外部验证 | Methods "Input Data Sources" 未提及跨数据集验证 |
| 阴性集为随机基因组区域 | 随机区域可能包含未注释的增强子或其他功能元件，导致阴性集污染 | 分类器可能学到的是"已知 vs 未知"而非"增强子 vs 非增强子" | 使用实验验证的非增强子区域（如沉默染色质）作为阴性对照 | Methods "Input Data Sources" 仅描述为"randomly selected" |
| MPRA 验证仅一个 CRE | 单一 CRE 的相关性（r=0.506）可能不代表普遍规律 | 无法排除该 CRE 的特殊性 | 在多个独立 CRE 上重复 MPRA 验证 | Results 图 5 仅展示 RhoCRE3 |
| 跨物种验证的适用性 | 人类模型直接评分小鼠序列，物种间 TF 结合偏好差异可能影响结果 | 正相关可能部分由保守序列驱动，而非模型特异性 | 使用人类同源 CRE 的 MPRA 数据验证 | Results 图 5 使用小鼠序列 |
| 未与深度学习方法比较 | 未报告与 DeepSEA、Enformer 等模型的性能对比 | 无法判断 GKM-SVM 是否是最优选择 | 在相同数据集上运行多种方法并比较 AUC 和 deltaSVM 相关性 | 全文未提及深度学习基线 |
| 等位基因频率分析可能受连锁不平衡影响 | 低频变异可能因连锁而非直接功能选择 | 净化选择的推断可能被 LD 结构混淆 | 使用条件分析或独立变异集验证 | Results 图 3A 未控制 LD |
| 基序分析依赖数据库完整性 | HOCOMOCO 数据库可能未覆盖所有视网膜相关 TF | 模型可能遗漏未知 TF 基序 | 使用 de novo 基序发现方法交叉验证 | Methods "Transcription Factor Motif Analysis" 仅使用已知数据库 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **GKM-SVM + deltaSVM 是轻量级、可迁移的变异效应预测框架**：
   - 可迁移性：该框架不依赖深度学习基础设施，训练成本低，适合中小规模实验室复现；
   - 迁移到本课题：对于 TF–DNA 结合机制研究，可用该框架对任意物种/组织的 ATAC-seq（或 DNase-seq）数据训练组织特异性 CRE 模型，生成变异优先级评分，辅助设计湿实验验证。

2. **ATAC-seq 峰作为 CRE 训练标签的可行性**：
   - 核心洞察：开放染色质区域虽非功能验证，但足以训练出能识别 TF 基序的模型；
   - 迁移到本课题：在缺乏 ChIP-seq 数据的情况下，ATAC-seq 可作为 TF 结合位点预测的替代训练信号，尤其适用于稀有细胞类型或难以进行 ChIP 的组织。

3. **多维度验证策略是建立预测可信度的关键**：
   - 方法：将预测分数与等位基因频率、保守性、基序位置、独立实验数据四重交叉验证；
   - 迁移到本课题：任何 AI 预测的 TF–DNA 结合效应都应至少与两个独立证据源交叉验证，避免单一验证源的偏差。

4. **deltaSVM 分数分布可揭示 CRE 内部功能结构**：
   - 核心发现：负分变异在 CRE 中心呈双峰分布，对应 TF 基序富集区；
   - 迁移到本课题：该分析模式可用于定位 TF 结合热点区域，指导后续突变扫描实验的位点选择。

5. **组织特异性是调控变异解读的核心维度**：
   - 方法：通过对比视网膜 vs 非视网膜 CRE 评分，验证模型组织特异性；
   - 迁移到本课题：在构建 TF–DNA 结合预测模型时，应明确标注训练数据的组织来源，并测试跨组织泛化能力。

6. **deltaSVM 可跨物种应用**：
   - 发现：人类模型能有效评分小鼠序列并与实验数据相关；
   - 迁移到本课题：在模式生物（小鼠、斑马鱼等）中验证人类 TF 结合预测时，该框架可能提供跨物种可迁移的基线。

---

## 15 与已有知识连接

- **GKM-SVM 方法源头**：该方法由 Beer 实验室开发（Lee et al., 2011; Ghandi et al., 2014），已成功应用于多种调控基因组学任务。本文将其扩展至人类视网膜组织，属于方法在新组织类型上的应用。
- **deltaSVM 框架**：由 Lee et al. (2015) 提出，用于预测调控变异效应。本文遵循该框架，但训练数据为视网膜特异性 ATAC-seq，而非通用 DNase-seq 或 ChIP-seq。
- **与 DeepSEA/Enformer 的关系**：这些深度学习方法同样预测非编码变异效应，但使用多任务学习整合多种细胞类型的调控信号。本文的 GKM-SVM 方法在单组织场景下达到 AUC 0.95，提示轻量方法在组织特异性任务中仍有竞争力。
- **与视网膜调控基因组学的连接**：本文引用了先前在小鼠视网膜增强子上的 GKM-SVM 工作（Kwasnieski et al., 2016），并扩展至人类。与 Cherry 实验室先前发表的视网膜 ATAC-seq 数据（Cherry et al., 2020）直接相关。
- **与 MPRA 验证的连接**：Kwasnieski et al. (2016) 的 RhoCRE3 数据是本文跨物种验证的锚点，该数据也是视网膜增强子功能研究的经典资源。
- **与临床基因组学的连接**：本文的 VISIONS 数据库可作为视网膜疾病非编码变异的注释资源，与 ClinVar、gnomAD 等数据库互补。
- **[Analysis] 与结构预测方法的潜在连接**：本文方法不涉及 3D 结构，但 TF 基序分析结果（如 OTX2 的 TAATCC 核心）可与 AlphaFold 等结构预测工具结合，探索基序破坏如何影响 TF–DNA 物理结合。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

1. **候选一：多组织 GKM-SVM 集成模型用于跨组织调控变异优先级排序**
   - 来源局限/观察：本文仅训练视网膜模型，未探索多组织联合建模；
   - 核心假设：多组织联合训练可提高单组织预测精度（通过共享序列语法），同时保留组织特异性特征；
   - 初步方法：在 ENCODE 多组织 ATAC-seq 数据上训练多任务 GKM-SVM 或分层模型，比较单组织 vs 多组织模型的 AUC 和 deltaSVM 与 MPRA 的相关性；
   - 验证方式：使用 GTEx eQTL 和已发表 MPRA 数据作为独立验证；
   - 创新状态：unverified。

2. **候选二：将 deltaSVM 分数与 AlphaFold 预测的 TF–DNA 结合结构变化关联**
   - 来源局限/观察：本文 deltaSVM 分数与基序破坏相关，但未涉及物理结合机制；
   - 核心假设：deltaSVM 负分变异对应的氨基酸（蛋白侧）或碱基（DNA 侧）变化会导致 AlphaFold 预测的 TF–DNA 结合界面能量或构象变化；
   - 初步方法：选取 OTX2/CRX 等视网膜 TF，对基序内所有 SNV 进行 AlphaFold 或分子对接模拟，比较 deltaSVM 分数与预测结合能变化的相关性；
   - 验证方式：若相关性显著，则 deltaSVM 可作为结构预测的快速预筛选工具；
   - 创新状态：unverified。

3. **候选三：单细胞 ATAC-seq 驱动的细胞类型特异性 CRE 变异评分**
   - 来源局限/观察：本文使用 bulk ATAC-seq，无法区分视网膜细胞类型（如视杆、视锥、双极细胞等）；
   - 核心假设：细胞类型特异性 CRE 模型能更精确地预测与特定细胞类型相关疾病的变异；
   - 初步方法：利用已发表的人视网膜 scATAC-seq 数据，按细胞类型聚类后分别训练 GKM-SVM，比较细胞类型特异性模型与 bulk 模型的变异评分差异；
   - 验证方式：使用已知视网膜疾病基因的调控变异进行富集分析；
   - 创新状态：unverified。

4. **候选四：将 deltaSVM 分数整合到 CRISPR 筛选设计中的位点选择**
   - 来源局限/观察：本文仅提供预测分数，未展示其在实验设计中的实用性；
   - 核心假设：deltaSVM 分数可优先排序 CRISPR 突变筛选的靶向位点，提高筛选效率；
   - 初步方法：在视网膜类器官或细胞系中，选取 deltaSVM 分数分布不同的位点进行 CRISPR 饱和突变，比较预测分数与实验功能效应的 ROC；
   - 验证方式：若 AUC > 0.8，则 deltaSVM 可作为 CRISPR 筛选的预筛选工具；
   - 创新状态：unverified。

5. **候选五：跨物种保守性加权 deltaSVM 评分提升致病变异识别**
   - 来源局限/观察：本文仅使用 phyloP 作为验证指标，未将其整合到评分中；
   - 核心假设：将 deltaSVM 分数与跨物种保守性加权结合，可提升致病变异的识别精度（因为保守位点的破坏更可能致病）；
   - 初步方法：构建 deltaSVM × phyloP 复合评分，在视网膜疾病患者队列中比较复合评分与单一评分的诊断率；
   - 验证方式：使用 ClinVar 和文献报道的视网膜疾病致病变异进行回顾性验证；
   - 创新状态：unverified。