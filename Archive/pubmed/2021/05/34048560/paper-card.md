## 01 基本信息

- **标题**：DeepFun: a deep learning sequence-based model to decipher non-coding variant effect in a tissue- and cell type-specific manner
- **作者**：Pei, Guangsheng; Hu, Ruifeng; Jia, Peilin; Zhao, Zhongming
- **单位**：Center for Precision Health, School of Biomedical Informatics, The University of Texas Health Science Center at Houston（据作者信息推断，原文未完整列出）
- **期刊/平台**：Nucleic Acids Research
- **年份**：2021
- **论文类型**：方法学 + Web 服务器工具论文
- **领域**：基因组学 / 非编码变异功能预测 / 深度学习
- **关键词**：非编码变异、深度学习、CNN、染色质特征、组织/细胞类型特异性
- **DOI/arXiv 号**：10.1093/nar/gkab429
- **代码**：https://github.com/bsml320/DeepFun
- **数据**：ENCODE 和 Roadmap Epigenomics 项目的 7879 个染色质特征样本（DNase-seq、组蛋白修饰 ChIP-seq、TF ChIP-seq）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 深度学习」方向，聚焦于通过 CNN 从 DNA 序列预测染色质可及性、组蛋白修饰和 TF 结合等染色质特征，进而评估非编码变异的组织/细胞类型特异性功能影响。与 TF–DNA 结合机制直接相关（TF 结合位点预测、motif 解析），但并非直接建模 TF–DNA 三维结构或物理相互作用，而是基于序列的调控功能预测。

## 02 一句话总结

本文构建了一个基于 CNN 的深度学习模型 DeepFun，利用 ENCODE 和 Roadmap 的 7879 个染色质特征（DNase-seq、组蛋白修饰、TF ChIP-seq）作为预测目标，通过比较参考/替代等位基因的预测活性差异（SAD 和 log-odds difference），在单碱基分辨率下评估非编码变异的组织/细胞类型特异性功能影响，并通过独立 GWAS 数据集验证了其有效性。

## 03 研究问题

- **具体问题**：如何从 DNA 序列出发，在单碱基分辨率下预测非编码变异的调控功能影响，并给出组织/细胞类型特异性的评估？
- **为什么重要**：超过 90% 的 GWAS 变异位于非编码区，这些变异可能通过影响染色质可及性、组蛋白修饰或 TF 结合来发挥致病作用。不同疾病的风险变异往往只在特定组织或细胞类型中起作用（如精神疾病变异富集于神经元调控区，阿尔茨海默病变异富集于小胶质细胞增强子），因此组织/细胞类型特异性的功能预测对理解疾病机制至关重要。
- **现有方法不足**：已有工具如 CADD、GWAVA、FunSeq2 等基于传统机器学习或保守性评分，缺乏组织/细胞类型特异性；深度学习方法如 DeepSEA、Basset 虽能预测染色质特征，但覆盖的组织/细胞类型数量有限（如 DeepSEA 仅 125 个 DNase 特征），可能遗漏仅在特定组织中起作用的变异。
- **精确研究问题**：Can a CNN model trained on comprehensive ENCODE/Roadmap chromatin profiles (1548 DNase, 1536 histone marks, 4795 TF binding) predict non-coding variant functional impact in a tissue- and cell type-specific manner, and can in silico saturated mutagenesis identify informative motifs around functional variants?

## 04 背景与发展脉络

> 注：以下脉络基于本文引用和描述，属于「经外部核验」的领域发展框架。

1. **传统非编码变异注释方法**：CADD（2014）、GWAVA（2014）、FunSeq2（2014）等，基于保守性、功能基因组注释和传统机器学习，缺乏组织特异性，且无法捕捉序列-染色质特征间的非线性关系。
2. **第一代深度学习染色质预测模型**：DeepBind（2015）首次用 CNN 预测 TF 结合；DeepSEA（2015）用 CNN 同时预测 DNase、TF 结合和组蛋白修饰，引入 SAD 概念；Basset（2016）用 CNN 预测 DNase 可及性，采用 1000 bp 窗口和峰值合并策略。
3. **扩展组织覆盖的模型**：ExPecto（2018）在 DeepSEA 基础上扩展到更多组织和细胞类型，并加入位置权重；Basenji（2018）引入多任务学习和更大窗口。
4. **本文位置**：DeepFun 在 Basset 架构基础上，将训练数据扩展到 7879 个染色质特征（远超 DeepSEA 的 919 个），覆盖 225 个组织/细胞类型，并集成 screen analysis 和 in silico saturated mutagenesis 两种分析功能，强调组织/细胞类型特异性的变异效应评估。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 非编码变异功能注释缺乏组织/细胞类型特异性 | 大多数现有工具给出全局性评分，无法反映变异在特定组织中的作用 | 训练数据覆盖的组织/细胞类型有限，如 DeepSEA 仅 125 个 DNase 特征 | Introduction 节：DeepSEA 模型仅有 125 个 DNA 可及性特征，可能遗漏仅在特定组织起作用的变异 |
| 变异效应预测精度受限于训练数据规模 | 小规模训练数据导致模型泛化能力不足 | 深度学习方法需要大量标注数据，而染色质特征数据分散在不同项目中 | Materials and Methods 节：DeepFun 整合 7879 个样本，覆盖 225 个组织/细胞类型 |
| 现有工具无法预测未见过的变异 | 多数模型依赖已知变异信息或保守性特征 | 基于序列的 CNN 模型可直接对任意序列变异进行预测 | Materials and Methods 节：模型不依赖具体变异信息，可预测 novel mutations 和 de novo mutations |
| 难以解析变异影响的 motif 机制 | 仅知道变异影响某个调控特征，但不知道影响哪个 TF 结合 motif | 需要饱和突变扫描来系统评估每个碱基的贡献 | Results 节：in silico saturated mutagenesis 分析可识别 NFE2 motif 及其侧翼区域 |

## 06 核心思想

### 1) 表面方法

构建两个 CNN 模型（Model A 和 Model B），以 1000 bp DNA 序列为输入，分别预测 3451 个（Model A：DNase + 组蛋白修饰 + CTCF）和 4428 个（Model B：其他 TF）染色质特征的活性概率。对每个变异，分别计算参考/替代等位基因的预测活性，用 SAD 和 log-odds difference 量化变异效应。

### 2) 核心洞察

- **组织/细胞类型特异性来自训练数据的广度**：通过整合 225 个组织/细胞类型的 7879 个染色质特征，模型能够区分变异在不同组织中的差异化效应，而非给出单一全局评分。
- **序列上下文决定调控效应**：CNN 的第一层卷积核可自动学习 motif 特征，变异对预测活性的影响反映了其对 TF 结合位点的破坏或增强。
- **饱和突变扫描可解析 motif 结构**：通过系统突变 200 bp 窗口内的每个碱基，可重建 TF 结合 motif 的位置和关键碱基，将变异效应与具体 TF 结合机制关联。

### 3) 可能的普适教训 [Analysis]

- 深度学习模型的「组织特异性」能力本质上取决于训练标签的覆盖广度，而非模型架构本身。这提示在 TF–DNA 结合预测中，收集更多细胞类型/条件的 ChIP-seq 数据比改进网络结构更直接有效。
- 将变异效应分解为「对每个染色质特征的预测活性差」而非单一评分，可提供更丰富的生物学解释维度，这一思路可迁移到 TF 结合预测中，区分变异对不同 TF 的影响。

## 07 方法总览

- **输入**：1000 bp DNA 序列（以变异位点为中心，各延伸 500 bp），人类基因组版本 hg19/GRCh37 或 hg38/GRCh38（后者自动 liftOver 转换）
- **输出**：
  - Screen analysis：每个变异在所有染色质特征上的 SAD 和 log-odds difference 值，以及最受影响的组织/细胞类型和染色质特征
  - In silico saturated mutagenesis：200 bp 窗口内每个碱基突变的 SAD 热图，显示 motif 位置和关键碱基
- **模型架构**：扩展版 Basset CNN，3 个卷积层 + 2 个全连接隐藏层 + sigmoid 输出层
- **训练数据**：ENCODE 和 Roadmap 的 7879 个染色质特征（1548 DNase-seq、1536 组蛋白修饰、4795 TF ChIP-seq），去冗余后 Model A 含 3451 个特征，Model B 含 4428 个特征
- **训练策略**：80% 训练、10% 验证、10% 测试；早停法（验证集 loss 连续 12 个 epoch 不下降则停止）；贝叶斯超参数优化
- **变异效应计算**：对每个变异，分别用参考/替代等位基因序列预测活性，计算 SAD = P(alt) − P(ref) 和 log-odds difference
- **反馈回路**：无显式反馈回路；模型为前馈预测，变异效应为事后计算
- **工具**：Python 3.6、Torch7、Apache + mod_wsgi、MySQL（任务管理）、Bootstrap 4 + jQuery（前端）

**文字流程**：用户提交变异列表 → 服务器校验格式和基因组版本 → 对每个变异提取 1000 bp 上下文序列 → 分别用参考/替代等位基因序列输入 CNN → 预测所有染色质特征活性 → 计算 SAD/log-odds difference → 生成汇总表和热图 → 用户下载结果。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 数据整合与预处理模块 | 从 ENCODE/Roadmap 下载 7879 个染色质特征，统一格式、去冗余、峰值合并 | 提供大规模、多组织/细胞类型的训练标签，是组织特异性预测的基础 | 输入：原始 ENCODE/Roadmap 峰调用文件；输出：统一格式的 1000 bp 峰值区间 | Methods 节：整合 1548 DNase、1536 组蛋白修饰、4795 TF 结合特征 | 移除后模型退化为小规模训练，组织覆盖度大幅下降，无法实现组织特异性预测（预期效应） |
| CNN 特征提取模块（卷积层） | 从 DNA 序列中自动学习 motif 和调控语法特征 | CNN 第一层可捕获序列 motif，后续层可组合高阶特征，是序列-功能映射的核心 | 输入：one-hot 编码的 1000 bp 序列；输出：高层特征向量 | Methods 节：采用 Basset 架构，3 个卷积层 | 移除后模型无法从序列提取有效特征，预测能力崩溃（预期效应） |
| 多任务输出层 | 同时预测数千个染色质特征的活性 | 多任务学习可共享序列特征，提高泛化能力，并支持组织特异性比较 | 输入：全连接层特征；输出：每个染色质特征的活性概率（0-1） | Methods 节：Model A 输出 3451 个特征，Model B 输出 4428 个特征 | 移除后需为每个特征单独训练模型，计算成本高且无法利用跨任务共享信息（预期效应） |
| SAD/log-odds 计算模块 | 量化变异对染色质特征活性的影响 | 将序列预测转化为变异效应评分，是变异功能注释的核心指标 | 输入：参考/替代等位基因的预测活性；输出：SAD 和 log-odds difference | Methods 节：SAD = P(alt) − P(ref)；log-odds difference 公式 | 移除后无法评估变异效应，工具退化为纯染色质特征预测器（预期效应） |
| Screen analysis 模块 | 批量扫描大量变异在所有染色质特征上的效应 | 支持 GWAS 变异优先排序，识别最可能具有调控功能的变异 | 输入：变异列表（≤3000 个）；输出：汇总统计表、SAD 热图 | Results 节：Figure 3D 展示输出页面 | 移除后用户需自行处理原始预测结果，使用门槛大幅提高（预期效应） |
| In silico saturated mutagenesis 模块 | 系统突变 200 bp 窗口内每个碱基，评估每个位置的效应 | 可解析变异周围的功能 motif 和关键碱基，将变异效应与 TF 结合机制关联 | 输入：单个变异 + 目标染色质特征；输出：SAD 热图、motif 位置估计 | Results 节：Figure 3F 展示 NFE2 motif 的饱和突变结果 | 移除后无法解析变异影响的 motif 机制，生物学解释能力下降（预期效应） |
| Web 服务器框架（MVC） | 提供用户友好的提交、监控、结果展示界面 | 降低使用门槛，支持非计算背景的研究者 | 输入：用户提交的变异文件；输出：结果页面和下载文件 | Methods 节：Web server construction 部分 | 移除后工具仅剩命令行版本，可及性大幅降低（预期效应） |

## 09 关键公式符号

1. **SAD (SNP Activity Difference)**：
   \[
   \text{SAD} = P(\text{alt}) - P(\text{ref})
   \]
   其中 \( P(\text{ref}) \) 和 \( P(\text{alt}) \) 分别为参考/替代等位基因序列的预测活性概率（可及性或结合概率）。SAD > 0 表示变异增强调控活性，SAD < 0 表示减弱。

2. **Log-odds difference**：
   \[
   \text{log-odds difference} = \log\left(\frac{P(\text{alt})}{1 - P(\text{alt})}\right) - \log\left(\frac{P(\text{ref})}{1 - P(\text{ref})}\right)
   \]
   将概率转换为 log-odds 空间，更符合线性叠加假设，适合比较效应大小。

3. **CNN 预测函数**（隐含）：
   \[
   P(y_i = 1 | x) = \sigma(W_L \cdot f_{L-1}(\cdots f_1(x) \cdots) + b_L)
   \]
   其中 \( x \) 为 one-hot 编码的 1000 bp 序列，\( f_l \) 为第 \( l \) 层卷积/全连接变换，\( \sigma \) 为 sigmoid 函数，\( y_i \) 为第 \( i \) 个染色质特征的活性标签。

4. **早停条件**（训练策略）：验证集 loss 在连续 12 个 epoch 内未下降则停止训练。

## 10 实验设计与证据链

### 数据集与评测协议

- **训练数据**：ENCODE 和 Roadmap 的 7879 个染色质特征（1548 DNase-seq、1536 组蛋白修饰、4795 TF ChIP-seq），覆盖 225 个组织/细胞类型；去冗余后 Model A 含 3451 个特征，Model B 含 4428 个特征
- **训练/验证/测试划分**：80%/10%/10%，按峰区间随机划分
- **评测指标**：AUROC（主指标）、AUPRC（辅助指标，因正负样本不平衡）
- **独立验证数据**：
  - ClinVar 变异（benign、pathogenic、uncertain significance）
  - ASD（自闭症谱系障碍）de novo 突变（SSC 队列）
  - 多种 GWAS 疾病/性状的显著关联变异（Figure 4A 和 Supplementary Table S1）

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 模型性能基准测试 | DeepFun 在染色质特征预测上达到较好 AUROC | 与 Basset 原始结果对比 | 所有 DNase-seq 特征的中位 AUROC 为 0.933，优于 Basset 的 0.895 | 更大规模训练数据提升了预测性能 | 未提供逐特征显著性检验，无法判断提升是否统计显著 | Methods 节 |
| AUPRC 评估 | 在不平衡数据上模型仍有区分能力 | 与随机分类器对比 | DNase-seq 中位 AUPRC 0.544 vs 随机 0.042；组蛋白修饰 0.354 vs 随机 0.025 | 模型预测显著优于随机 | AUPRC 绝对值仍偏低，对弱效应变异的检测能力有限 | Methods 节 |
| ClinVar 变异验证 | DeepFun 能区分致病性和良性变异 | 比较 pathogenic 与 benign 变异的 SAD 分布 | 致病性变异在相关组织中 SAD 显著更高（具体数值未在摘要中提供） | 模型能捕捉致病性非编码变异的功能影响 | 未提供效应量，无法评估临床实用性 | 引用文献 26 |
| ASD de novo 突变验证 | DeepFun 能识别 ASD 相关功能突变 | 比较 ASD de novo 突变与对照突变的 SAD | ASD 突变在脑相关染色质特征上 SAD 显著更高 | 模型能识别神经发育疾病相关变异 | 未提供独立复现数据 | 引用文献 26 |
| 组织特异性验证（Figure 4A） | DeepFun 能给出组织/细胞类型特异性的变异效应 | 多种疾病 GWAS 变异在不同组织中的 SAD 比较 | 免疫疾病变异在肠/结肠中 SAD 高；神经疾病变异在脑/脊髓中 SAD 高 | 模型预测与疾病相关组织一致 | 仅展示趋势，未提供统计检验 | Results 节 Figure 4A |
| 与 DeepSEA 对比 | DeepFun 的扩展特征集与 DeepSEA 结果一致 | 计算两模型 SAD 的 Pearson 相关系数 | CTCF: PCC=0.883 (p=2.2×10⁻¹⁶)；DNase: PCC=0.751 (p=1.46×10⁻¹⁰)；H3K4me3: PCC=0.490 (p=2.4×10⁻⁴) | 两模型预测高度一致，DeepFun 扩展特征集不引入系统性偏差 | 部分特征（如 H3K4me3）相关性中等，可能因特征数量差异 | Supplementary Figure S1 |
| In silico saturated mutagenesis 验证 | 饱和突变能解析 TF 结合 motif | 以 rs6426833（溃疡性结肠炎相关）在 NFE2 结合特征上的饱和突变为例 | 替代等位基因（A）序列的饱和突变热图与 NFE2 motif（TGACTCAGCA，CIS-BP 数据库）高度一致 | 饱和突变可准确识别 TF 结合 motif 和关键碱基 | 仅展示单个案例，未系统评估 | Results 节 Figure 4B |

## 11 结论正确解读

- **任务范围**：本文的结论仅限于「从 DNA 序列预测染色质特征活性（可及性、组蛋白修饰、TF 结合）」以及「基于预测活性差异评估非编码变异效应」。不涉及 TF–DNA 三维结构、结合动力学或直接物理相互作用。
- **oracle/真值输入**：训练标签来自 ENCODE/Roadmap 的 peak calling 结果（二值化），本质上是实验观测的近似。peak calling 本身存在假阳性和假阴性，模型预测上限受限于标签质量。
- **端到端状态**：模型是端到端的序列→特征预测，但变异效应评估（SAD）是事后计算，非模型直接输出。模型不直接预测「致病性」或「疾病风险」。
- **算力成本**：原文未提供训练时间、GPU 型号等具体算力信息（Not assessable）。Web 服务器为 CPU 推理，screen analysis 约 5 秒/变异，饱和突变约 20 分钟/变异。
- **历史数据依赖**：模型基于 hg19/GRCh37 坐标训练，hg38 输入需 liftOver 转换，可能引入坐标转换误差。模型仅覆盖染色体 1-22 和 X。
- **最难情形**：模型对弱效应变异（SAD 接近 0）、非峰区域变异、以及训练数据中未覆盖的组织/细胞类型的预测可靠性较低。AUPRC 绝对值偏低（0.354-0.544）表明在正样本稀少的情况下精确率有限。
- **群体/领域边界**：模型仅适用于人类基因组（hg19/hg38），不适用于其他物种。训练数据来自 ENCODE/Roadmap 覆盖的细胞系和组织，不代表所有生理或病理状态。
- **不确定性**：原文未提供预测置信区间或不确定性估计。SAD 的点估计无法反映预测噪声。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未考虑长程相互作用 | 模型仅使用 1000 bp 局部序列窗口，未整合 3D 染色质构象（如 Hi-C）数据 | 未来可整合 3D 基因组数据以改进预测 | Conclusion 节 |
| 二值化标签丢失定量信息 | peak calling 将连续的染色质信号二值化，忽略了信号强度差异 | 未来可探索整合定量信号的方法 | Conclusion 节 |
| 未考虑 motif 以外的调控机制 | 模型主要捕获序列 motif 信息，对非 motif 依赖的调控机制（如 DNA 甲基化、染色质状态协同）覆盖不足 | 未来可整合其他表观遗传数据 | Conclusion 节 |
| 训练数据覆盖有限 | 尽管覆盖 225 个组织/细胞类型，但仍有大量细胞类型和条件未覆盖 | 随 ENCODE 3 等项目的推进，持续扩充训练数据 | Conclusion 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 模型性能提升主要归因于训练数据规模，但未控制架构差异 | DeepFun 声称优于 Basset（AUROC 0.933 vs 0.895），但两者架构不完全相同，无法确定提升来自数据还是模型改动 | 若提升主要来自数据，则架构创新贡献有限；若来自架构，则需明确报告差异 | 在相同训练数据上对比 DeepFun 与 Basset 架构 | Methods 节：DeepFun 为「扩展版 Basset 模型」 |
| 组织特异性验证缺乏统计检验 | Figure 4A 仅展示疾病变异在相关组织中 SAD 更高的趋势，未提供显著性检验或效应量 | 无法判断组织特异性模式是否稳健，可能受样本量或混杂因素影响 | 对每个疾病-组织对进行置换检验或混合效应模型 | Results 节 Figure 4A |
| 与 DeepSEA 的对比仅用 PCC，未比较变异优先排序的实际效果 | PCC 高不代表 DeepFun 在变异功能预测任务上优于 DeepSEA | 用户关心的是变异排序的准确性，而非预测值的线性相关性 | 在相同 benchmark 数据集上比较两模型的 AUROC/AUPRC 或排序指标 | Supplementary Figure S1 |
| 饱和突变验证仅展示单个案例 | rs6426833/NFE2 案例可能经过挑选，不能代表整体性能 | 无法评估饱和突变分析在多样本中的可靠性和泛化性 | 在多个变异-特征组合上系统评估 motif 恢复率 | Results 节 Figure 4B |
| 未报告模型在非峰区域（阴性区域）的变异效应分布 | 模型对峰区域的变异可能过度敏感，对非峰区域的变异效应可能被低估 | 真实调控变异可能位于开放染色质边界或低信号区域 | 分析非峰区域变异的 SAD 分布，与随机突变比较 | 未提供 |
| Web 服务器任务队列限制（最多 5 个并行任务）可能影响大规模应用 | 对需要批量分析数万变异的研究者构成瓶颈 | 影响工具的实际可用性 | 测试大规模提交时的吞吐量和等待时间 | Methods 节：Web server construction 部分 |

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI/深度学习」课题方向。

1. **多任务学习框架可同时建模多种 TF 结合特征**：DeepFun 在同一 CNN 中同时预测数千个染色质特征，TF 之间共享底层序列特征提取器。这一思路可直接迁移到 TF–DNA 结合预测中：与其为每个 TF 单独训练模型，不如构建一个多任务模型同时预测多个 TF 的结合，利用 TF 间的共享调控语法提高泛化能力，尤其对 ChIP-seq 数据稀少的 TF 有益。

2. **SAD 框架是变异效应量化的简洁有效方案**：通过比较参考/替代等位基因的预测活性差异，将变异效应转化为连续评分。这一框架不依赖变异注释或保守性信息，可推广到任何序列预测模型。在 TF–DNA 结合研究中，可计算变异对特定 TF 结合预测的 SAD，用于优先排序可能破坏/增强 TF 结合的候选变异。

3. **训练数据广度决定组织特异性能力**：DeepFun 的组织特异性预测能力主要来自 225 个组织/细胞类型的训练标签覆盖，而非特殊架构设计。这提示在 TF–DNA 结合预测中，收集更多细胞类型/条件的 ChIP-seq 数据（如 ENCODE 3、Cistrome 等）比追求更复杂的模型架构更直接有效。

4. **饱和突变扫描可解析 motif 结构**：通过系统突变窗口内每个碱基并计算预测活性变化，可重建 TF 结合 motif 的位置和关键碱基。这一方法可迁移到 TF–DNA 结合机制研究中：对任意 TF 结合位点进行饱和突变扫描，可识别对结合至关重要的碱基位置，与体外结合实验（如 SELEX、EMSA）互补。

5. **二值化标签的局限与改进方向**：DeepFun 使用 peak calling 的二值化标签，丢失了定量信号强度信息。在 TF–DNA 结合预测中，若使用 ChIP-seq 的定量信号（如 fold enrichment）而非二值化 peak 标签，可能提高模型对结合强度差异的敏感度。

6. **Web 服务器设计模式**：MVC 架构 + 任务队列 + 邮件通知的设计模式，为计算密集型预测工具提供了可参考的用户交互范式。在构建 TF–DNA 结合预测工具时，可借鉴其「批量提交 + 异步处理 + 结果下载」的流程。

## 15 与已有知识连接

- **DeepSEA (Zhou & Troyanskaya, 2015)**：DeepFun 直接与 DeepSEA 对比（PCC 0.751-0.883），两者共享 SAD 概念和 CNN 架构思路。DeepSEA 是序列-染色质特征预测的开创性工作，DeepFun 的主要增量是训练数据规模和组织覆盖度。
- **Basset (Kelley et al., 2016)**：DeepFun 的架构直接基于 Basset，包括 1000 bp 窗口、peak 合并策略和 CNN 层设计。Basset 是 DNase 可及性预测的代表性工作。
- **ExPecto (Zhou et al., 2018)**：同样扩展了 DeepSEA 的组织覆盖度，但 DeepFun 更强调 Web 服务器可用性和变异优先排序功能。
- **ENCODE 和 Roadmap Epigenomics 项目**：DeepFun 的训练数据来源，这两个项目提供了大规模、多组织/细胞类型的染色质特征数据，是序列-调控功能预测模型的标准训练资源。
- **CIS-BP 数据库**：DeepFun 在饱和突变验证中使用 CIS-BP 的 NFE2 motif 作为参照，该数据库是 TF 结合 motif 的权威资源。
- **与本课题方向的连接**：在 TF–DNA 结合机制研究中，DeepFun 的框架可迁移为「TF 结合预测器」——用 ChIP-seq 数据训练 CNN 预测特定 TF 的结合，然后用 SAD 评估变异对结合的影响。其多任务学习思路也可用于同时建模多个 TF 的竞争性结合。但需注意，DeepFun 是纯序列模型，不包含 TF 的 DNA 结合域结构信息，对结合特异性的解释能力有限。

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI/深度学习」课题方向。

### 候选 1：TF–DNA 结合特异性的多任务 CNN 预测器
- **名称**：TF-MultiBind：a multi-task CNN for pan-TF binding specificity prediction
- **来源局限/观察**：DeepFun 的多任务框架证明共享序列特征可同时预测多种染色质特征，但未聚焦于 TF 结合特异性本身。现有 TF 结合预测模型（如 DeepBind）多为单 TF 模型，未充分利用 TF 间的共享调控语法。
- **核心假设**：多个 TF 的 DNA 结合偏好共享底层序列特征（如 DNA 形状、GC 含量、核小体定位倾向），多任务学习可提高数据稀缺 TF 的结合预测精度。
- **初步方法**：在 DeepFun/Basset 架构基础上，以 Cistrome 或 ENCODE 的 TF ChIP-seq 为训练标签，构建多任务 CNN；对每个 TF 引入嵌入向量作为任务条件；比较多任务与单任务模型的 AUPRC，尤其关注 ChIP-seq 数据量 < 100 的 TF。
- **验证方式**：在独立测试集上比较多任务与单任务模型的 AUPRC；用已知 motif 的 TF 验证模型是否学到正确的结合偏好；用饱和突变分析检验 motif 恢复率。
- **创新状态**：unverified（多任务 TF 结合预测已有部分工作，但系统评估数据稀缺 TF 的增益尚不充分）

### 候选 2：变异效应的 TF 特异性分解
- **名称**：TF-SAD：decomposing non-coding variant effects into TF-specific binding impacts
- **来源局限/观察**：DeepFun 的 SAD 是「对所有染色质特征的平均效应」，无法回答「某个变异具体影响哪个 TF 的结合」。在疾病机制研究中，需要知道变异破坏/增强的是哪个 TF 的 motif。
- **核心假设**：将 SAD 分解到单个 TF 层面，可更精确地预测变异的功能机制，且分解后的 TF 特异性 SAD 与 eQTL 或 GWAS 共定位信号更一致。
- **初步方法**：在 DeepFun 框架中，对每个 TF 特征单独计算 SAD；结合 motif 扫描（如 FIMO）和 CNN 的梯度归因（如 saliency map），将变异效应归因到具体 TF；用已知致病机制变异（如 rs1421085/ARID5B）验证。
- **验证方式**：在 ClinVar 和 GWAS 变异上比较 TF 特异性 SAD 与全局 SAD 的区分能力；用 CRISPR 验证实验或已发表的 MPRA（大规模平行报告基因分析）数据检验预测。
- **创新状态**：partially checked（TF 特异性变异效应预测已有部分工具如 motifbreakR，但基于深度学习的端到端分解尚不充分）

### 候选 3：结合物理模拟的 TF–DNA 结合预测
- **名称**：PhysBind：integrating CNN predictions with MD-derived DNA shape features for TF binding prediction
- **来源局限/观察**：DeepFun 等纯序列模型忽略了 DNA 的物理结构特征（如小沟宽度、螺旋参数），而这些特征已被证明影响 TF 结合特异性。MD 模拟可提供序列-结构关系，但计算成本高，难以全基因组应用。
- **核心假设**：将 MD 模拟或 DNA 形状预测工具（如 DNAshape）导出的结构特征作为 CNN 的附加输入，可提高 TF 结合预测精度，尤其在 TF 结合域结构已知的情况下。
- **初步方法**：对训练集中的 peak 序列，用 DNAshape 或短 MD 模拟提取 DNA 形状特征；将序列 one-hot 编码与形状特征拼接作为 CNN 输入；比较有无形状特征的模型性能；对预测差异大的位点进行 MD 验证。
- **验证方式**：在独立 ChIP-seq 测试集上比较 AUPRC；用已知晶体结构的 TF-DNA 复合物验证预测的结合位点与实验结构一致；分析形状特征对预测的贡献度。
- **创新状态**：unverified（DNA 形状特征已用于 TF 结合预测，但与深度学习结合的系统评估尚不充分）

### 候选 4：跨细胞类型的 TF 结合迁移学习
- **名称**：TF-Transfer：transfer learning for TF binding prediction across cell types
- **来源局限/观察**：DeepFun 覆盖 225 个细胞/组织类型，但许多 TF 在特定细胞类型中缺乏 ChIP-seq 数据。迁移学习可利用数据丰富的细胞类型辅助数据稀缺的细胞类型。
- **核心假设**：TF 结合的序列偏好在不同细胞类型间高度共享，细胞类型特异性主要来自染色质状态和辅助因子；迁移学习可有效利用这一结构。
- **初步方法**：在数据丰富的细胞类型上预训练 CNN，然后在目标细胞类型的少量 ChIP-seq 数据上微调；比较微调与从头训练的性能；引入域对抗训练以去除细胞类型偏差。
- **验证方式**：在留一细胞类型交叉验证中比较迁移学习与从头训练；用 CRISPR 验证或已发表的 ChIP-seq 数据检验。
- **创新状态**：partially checked（迁移学习已用于 TF 结合预测，但跨细胞类型的系统评估尚不充分）