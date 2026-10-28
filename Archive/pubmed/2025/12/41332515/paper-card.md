## 01 基本信息

- **标题**：Inferring binding specificities of human transcription factors with the wisdom of crowds
- **作者**：Gryzunov, Nikita; Penzar, Dmitry; Kamenets, Vasilii; Vyaltsev, Valery; Kozin, Ivan; Eliseeva, Irina A; Nozdrin, Vladimir; Vorontsov, Ilya E; Bushuev, Sergey; Strekalovskikh, Vadim; Zinkevich, Arsenii; Andrews, Gregory; Bedarew, Matwej; Blass, Ido; Frolov, Dmitry; Lariushina, Iulia; Moore, Jill; Orenstein, Yaron; Roev, German; Salimov, Danil; Shimshoviz, Noam; Tziony, Ido; Weng, Zhiping; Bucher, Philipp; Deplancke, Bart; Fornes, Oriol; Grau, Jan; Grosse, Ivo; Jolma, Arttu; Kolpakov, Fedor A; Makeev, Vsevolod J; Hughes, Timothy R; Kulakovskiy, Ivan V
- **单位**：未提供（作者来自多个机构，包括俄罗斯、加拿大、以色列、瑞士、德国等地的研究团队）
- **期刊/预印本平台**：bioRxiv : the preprint server for biology
- **年份**：2025
- **论文类型**：预印本（社区挑战赛结果报告）
- **领域**：计算生物学 / 转录因子结合特异性建模 / 基准测试
- **关键词**：转录因子、DNA基序、位置权重矩阵、深度学习、社区挑战、基准测试
- **DOI/arXiv 号**：10.1101/2025.11.16.688692
- **代码**：https://github.com/autosome-ru/ibis-challenge；https://github.com/autosome-ru/postibis；https://github.com/autosome-ru/IBIS-rSNP
- **数据**：Zenodo（https://zenodo.org，DOI 未提供具体编号）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文是「蛋白质-DNA互作（聚焦TF–DNA结合机制）× AI/深度学习」方向中最重要的社区基准测试之一。它系统比较了PWM与深度学习模型在跨平台（人工序列→基因组序列）泛化能力上的差异，为TF–DNA结合特异性建模提供了标准化的数据、评测协议和基线。对课题的启示在于：深度学习模型在跨平台迁移中优于PWM，但优势有限；PWM在合理选择后仍具竞争力；rSNP效应预测是独立于基序预测的挑战性任务。

## 02 一句话总结

本文通过组织IBIS社区挑战赛，利用40个人类转录因子的5种实验平台数据，系统比较了PWM与任意高级方法（主要是深度学习）在跨平台TF–DNA结合特异性预测上的表现，发现精心设计的CNN模型整体优于PWM但优势有限，且PWM在合理选择后仍具竞争力。

## 03 研究问题

- **具体问题**：在跨平台（人工序列→基因组序列，或反之）的TF–DNA结合特异性预测任务中，深度学习模型是否显著优于传统PWM？如何公平、无信息泄漏地评测不同模型？
- **为什么重要**：TF–DNA结合特异性预测是调控基因组学的核心任务。PWM是经典模型，但假设位点内核苷酸独立贡献；深度学习模型理论上可捕获依赖关系，但其实际增益在跨平台泛化场景中缺乏系统评估。此外，已有基准测试常局限于单一平台或合成数据，缺乏多平台、多TF的公平比较。
- **现有方法不足**：已有基准测试（如ENCODE-DREAM）数据单一、评测协议不统一；PWM构建方法多样但缺乏系统比较；深度学习模型容易过拟合平台特异性伪影；缺乏跨平台迁移的标准化评测。
- **精确研究问题**：Can properly designed deep learning models consistently outperform position weight matrices in cross-platform prediction of human TF–DNA binding specificities, when evaluated on unseen experimental platforms with rigorous anti-leakage protocols?

## 04 背景与发展脉络

**脉络说明**：以下脉络基于本文引言和讨论的叙述，属于「仅本文框架」，未经外部系统核验。

1. **PWM时代（~1980s-2010s）**：PWM是经典TF结合特异性模型，假设位点内各位置独立贡献。代表性工具包括MEME、STREME、RSAT、HOMER、SeSiMCMC、ChIPMunk等。优点：简单、可解释、计算高效；局限：无法捕获核苷酸间的依赖关系。
2. **高级模型探索（~2010s-2020s）**：随着深度学习兴起，CNN、RNN等被用于TF–DNA结合预测。代表性工作包括DeepBind、DeepSEA等。优点：可捕获序列依赖；局限：容易过拟合、可解释性差、跨平台泛化能力未系统验证。
3. **社区挑战赛（~2010s-至今）**：DREAM和CAGI挑战赛证明了社区基准测试在公平评测中的价值。ENCODE-DREAM挑战赛是TF–DNA结合预测的重要先例，但数据来源单一。
4. **IBIS挑战赛（本文，2024）**：首次利用多平台（5种实验）、多TF（40个）的未公开数据，设计严格的防泄漏协议，系统比较PWM与任意高级方法。本文主张的位置：填补了跨平台泛化评测的空白，提供了标准化基准和工具（bibis）。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 信息泄漏 | 模型在训练时接触测试数据分布，导致评测虚高 | 实验数据平台间存在重叠（如同一TF的ChIP-Seq和HT-SELEX数据可能共享序列特征）；训练/测试划分不当 | Methods "General rules of IBIS" 节；"Ensuring fair play and fair evaluation" 节 |
| 平台特异性伪影 | 模型在训练平台上表现好，但跨平台泛化差 | 不同实验平台（ChIP-Seq vs HT-SELEX vs PBM）检测到的结合位点分布、亲和力范围不同；模型过拟合平台特有偏差 | Results "Triple-A models outperform PWMs, but by a limited margin" 节；Discussion 节 |
| 深度学习过拟合 | 许多深度学习模型在跨平台评测中表现差 | 模型容量大、训练数据有限（每个TF的位点数量有限）、缺乏正则化 | Results 图2；Discussion 节 |
| PWM选择困难 | 不同PWM构建工具差异大，选择不当影响性能 | 各工具对数据预处理、背景模型、伪计数等处理不同 | Results "IBIS Solutions and Winners" 节；Table 2 |
| rSNP效应预测困难 | 基序预测好的模型在rSNP效应预测中不一定好 | rSNP效应涉及等位基因间微小差异，需要定量预测而非分类；模型对单核苷酸变化的敏感性不足 | Results "Better TFBS prediction does not necessarily improve recognition of regulatory variant effects" 节；图3 |
| 评测指标不统一 | 不同研究使用不同指标，难以横向比较 | 分类任务（AUROC/AUPRC）与回归任务（Kendall τ）并存；负样本构建方式多样 | Methods "Ranking Strategy" 节；"Benchmarking on HT-SELEX reads" 节 |

## 06 核心思想

1. **表面方法**：组织一个开放社区挑战赛（IBIS），提供多平台、多TF的未公开实验数据，设计严格的防泄漏训练/测试划分，用统一的评测协议（多种指标、多种负样本构建方式）比较PWM与任意高级方法（AAA）的表现。

2. **核心洞察**：
   - 跨平台泛化是评测TF结合特异性模型的试金石。模型若只学到平台特异性伪影，在跨平台测试中会失败。
   - 精心设计的CNN（如带dilation的TCN、Mobile Inverted Bottleneck）可以胜过PWM，但优势有限且需要大量工程调优。
   - PWM在合理选择（内部基准测试）后仍具竞争力，说明简单模型+好的选择策略可以接近复杂模型。
   - 基序预测性能与rSNP效应预测性能不完全相关，后者是独立挑战。

3. **可能的普适教训** [Analysis]：
   - 社区挑战赛+严格防泄漏协议是评测机器学习模型泛化能力的有效机制，可迁移到其他TF–DNA互作预测任务（如预测突变效应、预测协同结合等）。
   - 深度学习模型的优势在于捕获复杂序列特征，但需要匹配的评测任务来体现；在简单分类任务上，传统方法可能已接近上限。
   - 内部基准测试（在训练数据上比较多种候选模型）是提升最终性能的关键步骤，这一策略可迁移到任何TF–DNA建模任务。

## 07 方法总览

- **输入**：40个人类TF的多平台实验数据，包括：
  - ChIP-Seq (CHS)：基因组结合峰
  - 基因组HT-SELEX (GHTS)：基因组DNA片段的体外结合选择
  - HT-SELEX (HTS)：人工随机序列的体外结合选择
  - SMiLE-Seq (SMS)：人工序列的定量结合谱
  - 蛋白结合微阵列 (PBM)：两种设计（ME训练、HK测试）
- **输出**：每个TF的结合特异性模型（PWM或AAA），输出对测试序列的结合预测分数
- **模块**：
  1. 数据预处理：统一格式、GC匹配负样本构建、训练/测试划分（染色体级别防泄漏）
  2. 模型提交：参赛者提交PWM（最多4个/TF）或AAA（任意模型）
  3. 评测：多种指标（AUROC、AUPRC、Kendall τ）、多种负样本类型（shades、aliens、random）
  4. 排名：分层排名聚合（DREAM-ENCODE方法）
  5. 后挑战评测：rSNP等位基因效应预测
- **训练**：参赛者使用提供的训练数据自行训练模型；组织者用统一协议评测
- **反馈回路**：Leaderboard阶段（公开，5+5 TF）→ Final阶段（隐藏，30 TF）
- **工具**：bibis Python包（数据预处理+评测）；PWMEval（PWM扫描）
- **假设**：结合特异性可从序列预测；跨平台泛化反映模型捕获真实结合特异性的能力

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 数据预处理与防泄漏划分 | 统一多平台数据格式，按染色体划分训练/测试 | 防止信息泄漏，保证评测公平 | 输入：原始实验数据；输出：训练/测试集 | Methods "Experimental data preprocessing" 节 | 移除后评测结果不可信（预期） |
| 多指标评测协议 | 对每个TF、每个模型计算多种性能指标 | 单一指标可能偏袒特定模型类型 | 输入：模型预测分数+真实标签；输出：AUROC/AUPRC/Kendall τ | Methods "IBIS benchmarking protocols" 节 | 移除后无法全面比较模型（预期） |
| 分层排名聚合 | 将多个指标、多个负样本类型的排名合并为最终排名 | 公平比较不同模型在不同任务上的综合表现 | 输入：各指标排名；输出：最终排名 | Methods "Ranking Strategy" 节 | 移除后排名不稳定（预期） |
| PWM扫描（PWMEval） | 用PWM对测试序列打分 | 统一PWM评测方式 | 输入：PWM+序列；输出：结合分数 | Methods "General notes on position matrices" 节 | 移除后PWM评测不一致（预期） |
| rSNP效应评测 | 预测等位基因特异性结合 | 测试模型在单核苷酸变异上的定量预测能力 | 输入：rSNP位点序列；输出：等位基因偏好 | Results "Better TFBS prediction does not necessarily improve recognition of regulatory variant effects" 节；图3 | 移除后无法评估模型在变异效应预测上的表现（预期） |
| 后挑战深度学习模型 | 组织者用统一方案训练多种深度学习模型 | 补充参赛者未覆盖的模型类型，验证结论稳健性 | 输入：训练数据；输出：模型预测 | Methods "Post-challenge deep learning models" 节 | 移除后结论仅基于参赛者模型（预期） |

## 09 关键公式符号

本文主要使用评测指标公式，无新提出的数学模型。关键公式如下：

1. **位置权重矩阵（PWM）转换**：
   - 位置频率矩阵（PFM）加伪计数后转换为对数几率（log-odds）：
   - log2([PFM + 0.00001] / 0.25)
   - 符号：PFM为位置频率矩阵，0.00001为伪计数，0.25为均匀背景频率（4种核苷酸）
   - 用途：将PFM转换为可打分的PWM
   - 来源：Methods "General notes on position matrices" 节

2. **PWM扫描的两种模式**：
   - **Best-hit**：取序列中最高得分的子串作为预测分数
   - **Sum-occupancy**：计算序列中所有子串得分的总和（基于位置频率矩阵）
   - 符号：无特定公式，但两种模式在评测中分别计算
   - 用途：评估PWM对整条序列的预测
   - 来源：Methods "General notes on position matrices" 节

3. **评测指标**：
   - AUROC（Area Under the Receiver Operating Characteristic curve）
   - AUPRC（Area Under the Precision-Recall Curve）
   - Kendall's τb（用于HT-SELEX回归任务，允许并列排名）
   - 符号：τb为Kendall秩相关系数
   - 用途：量化模型预测与真实标签的一致性
   - 来源：Methods "IBIS benchmarking protocols" 节

4. **排名聚合**：
   - 排名分数 = −log(r/(N+1))，其中r为某指标上的排名，N为总方案数
   - 符号：r为排名，N为方案总数
   - 用途：将多个指标的排名合并为综合排名
   - 来源：Methods "Ranking Strategy" 节

## 09 关键公式符号

本文主要使用评测指标公式，无新提出的数学模型。关键公式如下：

1. **位置权重矩阵（PWM）转换**：
   - 位置频率矩阵（PFM）加伪计数后转换为对数几率（log-odds）：
   - log2([PFM + 0.00001] / 0.25)
   - 符号：PFM为位置频率矩阵，0.00001为伪计数，0.25为均匀背景频率（4种核苷酸）
   - 用途：将PFM转换为可打分的PWM
   - 来源：Methods "General notes on position matrices" 节

2. **PWM扫描的两种模式**：
   - **Best-hit**：取序列中最高得分的子串作为预测分数
   - **Sum-occupancy**：计算序列中所有子串得分的总和（基于位置频率矩阵）
   - 符号：无特定公式，但两种模式在评测中分别计算
   - 用途：评估PWM对整条序列的预测
   - 来源：Methods "General notes on position matrices" 节

3. **评测指标**：
   - AUROC（Area Under the Receiver Operating Characteristic curve）
   - AUPRC（Area Under the Precision-Recall Curve）
   - Kendall's τb（用于HT-SELEX回归任务，允许并列排名）
   - 符号：τb为Kendall秩相关系数
   - 用途：量化模型预测与真实标签的一致性
   - 来源：Methods "IBIS benchmarking protocols" 节

4. **排名聚合**：
   - 排名分数 = −log(r/(N+1))，其中r为某指标上的排名，N为总方案数
   - 符号：r为排名，N为方案总数
   - 用途：将多个指标的排名合并为综合排名
   - 来源：Methods "Ranking Strategy" 节

## 10 实验设计与证据链

**数据集与规模**：
- 40个人类TF，5种实验平台（CHS、GHTS、HTS、SMS、PBM）
- 每个TF有3-5种平台数据
- 训练/测试划分：Leaderboard阶段5+5 TF（公开），Final阶段30 TF（隐藏）
- 测试数据：每个TF的每个平台有独立的测试集
- 负样本类型：shades（峰附近区域）、aliens（非相关蛋白的峰）、random（随机基因组区域，GC匹配）

**指标**：AUROC、AUPRC（分类任务）；Kendall's τb（HT-SELEX回归任务）

**基线**：MEX1（从IBIS训练数据用多种工具构建的PWM集合，每个TF选最佳PWM）

**评测协议**：
- PWM：组织者用PWMEval统一扫描，两种模式（best-hit、sum-occupancy）
- AAA：参赛者提交预测分数，组织者统一评测

**主要实验**：

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|----------------|------|
| Final阶段排名 | 深度学习模型是否优于PWM | 19个参赛团队，4个主要学科（A2G-AAA、G2A-AAA、A2G-PWM、G2A-PWM） | 最佳AAA（CNN类）在A2G和G2A中均优于最佳PWM | 精心设计的CNN可跨平台泛化并优于PWM | 优势有限，且需要大量工程调优 | Results "IBIS Solutions and Winners" 节；图1-2 |
| PWM vs AAA定量比较 | AAA相对PWM的增益大小 | 归一化性能分数（相对MEX1的log2-odds） | 最佳AAA比最佳PWM高约0.1-0.2 log2-odds单位 | AAA有增益但幅度有限 | 增益是否对所有TF一致不明确 | Results 图2 |
| rSNP效应预测 | 基序预测好的模型是否rSNP预测也好 | 参赛者模型预测rSNP等位基因偏好 | 排名与主基准不完全一致；PWM在rSNP任务中表现相对较好 | rSNP预测是独立任务，需要专门优化 | 最佳rSNP模型的类型不明确 | Results "Better TFBS prediction does not necessarily improve recognition of regulatory variant effects" 节；图3 |
| 后挑战模型比较 | 多种深度学习架构的相对表现 | LegNet变体、Malinois、DNA语言模型（DNABERT-2、GENA-LM、Nucleotide Transformer） | LegNet-Max和LegNet-WE最佳；DNA语言模型表现差 | 小型CNN在有限数据上优于大型预训练模型 | 语言模型在更大数据或不同任务上可能表现不同 | Results "Deeper exploration of the Triple-A models" 节；图4 |
| 消融：PWM初始化 | 将PWM嵌入CNN是否提升性能 | LegNet-PWM、LegNet-PWM-Stem vs LegNet-Max | 无显著提升 | PWM先验不帮助CNN | 可能因CNN已能学习PWM信息 | Results 图4；Supplementary Figure S9 |

## 11 结论正确解读

- **任务范围**：本文评测的是**跨平台**TF–DNA结合特异性预测，即模型在一种或多种实验平台数据上训练，在未见的平台数据上测试。这不直接等同于基因组上的全基因组结合位点预测（后者还涉及染色质可及性、共因子等）。
- **Oracle/真值输入**：训练数据来自5种实验平台，每种平台有其固有偏差（如PBM偏向高亲和力、ChIP-Seq受抗体和染色质环境影响）。模型被要求从序列预测结合，不提供基因组上下文信息。
- **端到端状态**：本文是**模型评测**，不是端到端预测流水线。参赛者模型仅输出序列结合分数，不涉及基因组注释、变异注释等下游任务。
- **算力成本**：未提供具体算力数据。但后挑战模型训练使用统一方案，DNA语言模型（500M参数）训练成本显著高于小型CNN。
- **历史数据依赖**：评测数据来自Codebook联盟，是未公开的新数据，避免了参赛者预先见过测试数据的风险。
- **模型依赖**：结论基于2024年参赛者提交的模型。深度学习领域进展迅速，未来模型可能表现更好。
- **最难情形**：跨平台泛化（A2G和G2A）是最难的任务，许多深度学习模型在此失败；rSNP效应预测是另一个难点，与主基准排名不一致。
- **群体/领域边界**：仅涉及人类TF，且40个TF覆盖13个结构家族，但并非所有TF家族都有代表。结论可能不适用于非人类物种或特殊TF家族。
- **不确定性**：排名稳定性分析（1000次随机子采样）显示前两名稳定，但第三名及以后存在波动。

**有边界的复述**：在40个人类TF、5种实验平台的评测中，精心设计的CNN模型在跨平台泛化上优于传统PWM，但优势幅度有限（约0.1-0.2 log2-odds单位）；PWM在合理选择后仍具竞争力；rSNP效应预测是独立于基序预测的挑战性任务。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 数据覆盖有限 | 仅40个人类TF，虽覆盖13个结构家族，但未覆盖所有TF家族 | 扩展到更多TF和物种 | Discussion 节 |
| 平台偏差 | 不同实验平台检测到的结合位点分布不同，跨平台评测可能低估某些模型 | 开发更鲁棒的跨平台归一化方法 | Discussion 节 |
| rSNP预测困难 | 所有模型在rSNP效应预测中表现有限，与主基准排名不一致 | 开发专门针对等位基因效应的评测和模型 | Discussion 节 |
| 深度学习模型过拟合 | 许多深度学习模型在跨平台评测中失败，即使训练时表现好 | 需要更好的正则化和数据增强策略 | Discussion 节 |
| 语言模型表现差 | DNA语言模型在TF结合预测上表现不佳 | 需要针对调控序列的专门预训练策略 | Discussion 节 |
| 评测指标局限 | 主要依赖分类指标（AUROC/AUPRC），可能未完全反映定量预测能力 | 开发更全面的定量评测指标 | Discussion 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 参赛者动机差异 | 不同团队投入资源不同，排名可能反映工程投入而非算法本质 | 影响结论"深度学习优于PWM"的普适性 | 分析参赛者方案复杂度与性能的关系 | Results 表2-3 |
| 评测协议偏向 | 评测指标和负样本构建方式可能偏向特定模型类型 | 影响公平性 | 用不同指标和负样本重新排名 | Methods "IBIS benchmarking protocols" 节 |
| 后挑战模型选择 | 组织者选择的后挑战模型可能不代表最优深度学习方案 | 影响"深度学习上限"的估计 | 测试更多架构和超参数 | Methods "Post-challenge deep learning models" 节 |
| 数据预处理差异 | 不同平台数据质量、深度不同，可能影响跨平台评测 | 影响结论的稳健性 | 按平台分层分析性能 | Table 1 |
| 缺乏基序质量分析 | 未系统比较模型学到的基序与已知基序的一致性 | 影响对模型可解释性的判断 | 用Tomtom等工具比较模型基序与已知基序 | 未提供 |
| 未分析序列特征 | 未分析模型是否捕获了PWM无法捕获的序列特征（如二核苷酸偏好） | 影响对深度学习优势来源的理解 | 用特征重要性分析工具（如DeepSHAP）分析模型 | 未提供 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **跨平台评测是TF–DNA模型的试金石**：在单一平台上训练和测试的模型可能过拟合平台特异性伪影。本课题（TF–DNA结合机制×AI）应优先采用跨平台评测协议，至少包含一个未参与训练的实验平台作为测试集。

2. **PWM仍是强基线**：精心选择的PWM（通过内部基准测试）在跨平台任务中仅略逊于最佳深度学习模型。在开发新模型时，应始终与PWM基线比较，并报告相对增益。

3. **CNN架构的实用设计**：最佳方案（LegNet-Max、LegNet-WE）的改进点包括：不同卷积核大小（3,6,9,12）、全局最大池化替代平均池化、窗口化SE块。这些设计可迁移到其他TF–DNA结合预测任务。

4. **数据增强策略**：反向互补序列增强是标准做法，几乎所有顶级方案都采用。在TF–DNA建模中应默认使用。

5. **rSNP效应预测是独立任务**：基序预测性能与rSNP效应预测性能不完全相关。如果课题涉及变异效应预测，需要专门优化模型对单核苷酸变化的敏感性，而非仅优化基序预测。

6. **防泄漏协议设计**：染色体级别的训练/测试划分是防止信息泄漏的关键。在构建TF–DNA数据集时，应避免同一序列区域出现在训练和测试集中。

7. **集成方法的价值**：多个顶级方案使用模型集成（如不同初始化、不同架构的集成）来提升性能。在TF–DNA预测中，集成是简单有效的性能提升手段。

8. **DNA语言模型的当前局限**：在TF结合预测任务上，DNA语言模型（DNABERT-2、GENA-T、Nucleotide Transformer）表现不如小型CNN。这提示在有限数据场景下，小型专用模型可能优于大型预训练模型。

## 15 与已有知识连接

- **ENCODE-DREAM挑战赛**：本文的排名聚合方法直接借鉴了ENCODE-DREAM挑战赛（文中引用），是TF–DNA结合预测领域的前一次大规模社区评测。本文的贡献在于多平台、多TF、严格防泄漏的设计。
- **Codebook Motif Explorer (MEX)**：本文的MEX1基线直接来自作者团队之前的Codebook工作（文中引用11），该工作系统比较了PWM构建工具。
- **DeepBind/DeepSEA**：深度学习在TF–DNA结合预测中的经典工作，本文的CNN方案可视为这些工作的延续和系统比较。
- **ZMotif**：本文获胜方案使用的CNN基序发现工具（文中引用31），可迁移到其他基序发现任务。
- **PERFECTOS-APE**：用于rSNP效应预测的PWM工具（文中引用36），是PWM在变异效应预测中的代表。
- **DNA语言模型（DNABERT-2、GENA-LM、Nucleotide Transformer）**：本文系统评测了这些模型在TF结合预测上的表现，结果与文献中关于语言模型在调控任务上表现不佳的报道一致。
- **与课题方向的连接**：本文为TF–DNA结合机制研究提供了标准化的数据资源（40个TF、5种平台）和评测工具（bibis），可直接用于验证新模型。其"跨平台泛化"思想可迁移到其他蛋白质-DNA互作预测任务（如预测结构域-基序互作）。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：跨平台TF–DNA结合预测的物理信息增强CNN
   - **来源局限/观察**：本文显示纯序列CNN在跨平台泛化中优势有限，且未利用DNA结构特征（如形状、弯曲性）。
   - **核心假设**：将DNA形状特征（如minor groove width、propeller twist）作为CNN的辅助输入，可提升跨平台泛化能力，尤其在PWM表现差的TF上。
   - **初步方法**：在LegNet-Max基础上，增加DNA形状特征通道；在IBIS数据上评测A2G和G2A性能。
   - **验证方式**：与本文最佳方案比较，按TF家族分层分析增益来源。
   - **创新状态**：unverified

2. **候选名称**：TF–DNA结合特异性的混合PWM-深度学习模型
   - **来源局限/观察**：本文显示PWM在合理选择后仍具竞争力，且rSNP预测中PWM表现相对好。
   - **核心假设**：将PWM作为深度学习模型的先验（如初始化第一层卷积核），可结合PWM的可解释性和深度学习的灵活性。
   - **初步方法**：用MEX1 PWM初始化CNN第一层，微调时允许学习偏离PWM的依赖关系；在IBIS数据上评测。
   - **验证方式**：与纯CNN和纯PWM比较，分析学到的卷积核与PWM的差异。
   - **创新状态**：partially checked（本文测试了PWM初始化但未深入分析）

3. **候选名称**：rSNP效应预测的等位基因感知训练策略
   - **来源局限/观察**：本文显示基序预测好的模型在rSNP预测中不一定好，提示需要专门优化。
   - **核心假设**：在训练时加入等位基因对（reference vs alternative）的对比损失，可提升模型对单核苷酸变化的敏感性。
   - **初步方法**：在IBIS训练数据上，构造等位基因对作为训练样本，使用对比学习或排序损失；在rSNP评测集上验证。
   - **验证方式**：与本文rSNP评测结果比较，分析不同TF家族的表现。
   - **创新状态**：unverified

4. **候选名称**：TF–DNA结合特异性的多任务学习框架
   - **来源局限/观察**：本文显示不同平台数据有系统差异，但未利用多平台数据训练单一模型。
   - **核心假设**：多任务学习（每个平台作为任务）可让模型学习平台无关的结合特异性表征。
   - **初步方法**：在LegNet-Max基础上，增加平台分类辅助任务或使用对抗训练去除平台信息；在IBIS数据上评测。
   - **验证方式**：与单平台训练模型比较，分析跨平台泛化能力。
   - **创新状态**：unverified

5. **候选名称**：TF–DNA结合预测的主动学习策略
   - **来源局限/观察**：本文显示某些TF的训练数据有限，导致模型过拟合。
   - **核心假设**：主动学习（选择信息量最大的序列进行实验验证）可高效提升低数据TF的模型性能。
   - **初步方法**：在IBIS训练数据上模拟主动学习循环，用不确定性采样选择新训练样本；比较不同采样策略。
   - **验证方式**：模拟实验，比较主动学习与随机采样的性能差异。
   - **创新状态**：unverified