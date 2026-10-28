## 01 基本信息

- **标题**：Inferring binding specificities of human transcription factors with the wisdom of crowds
- **作者**：Nikita Gryzunov; Dmitry Penzar; Vasilii Kamenets; Valery Vyaltsev; Ivan Kozin; Irina A. Eliseeva; Vladimir Nozdrin; Ilya E. Vorontsov; Sergey Bushuev; Vadim Strekalovskikh; Arsenii Zinkevich; Gregory Andrews; Matwej Bedarew; Ido Blass; Dmitry Frolov; Iuliia Lariushina; Jill Moore; Yaron Orenstein; German Roev; Danil Salimov; Noam Shimshoviz; Ido Tziony; Zhiping Weng; IBIS Consortium; GRECO-BIT/Codebook Consortium; Philipp Bucher; Bart Deplancke; Oriol Fornes; Jan Grau; Ivo Grosse; Arttu Jolma; Fedor A. Kolpakov; Vsevolod J. Hughes; Ivan V. Kulakovskiy
- **单位**：涉及多机构（包括 University of Toronto、EPFL、Vavilov Institute of General Genetics、Martin Luther University Halle-Wittenberg 等，具体对应关系见正文作者列表）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2025
- **论文类型**：社区挑战赛（benchmarking challenge）结果报告 + 方法学评估
- **领域**：计算生物学 / 调控基因组学 / TF–DNA 结合特异性建模
- **关键词**：transcription factor, DNA motif, binding specificity, PWM, deep learning, benchmarking, community challenge
- **DOI/arXiv 号**：10.1101/2025.11.16.688692
- **代码**：bibis 包（https://github.com/autosome-ru/ibis-challenge）；postibis（https://github.com/autosome-ru/postibis）；IBIS-rSNP（https://github.com/autosome-ru/IBIS-rSNP）
- **数据**：Zenodo（https://doi.org/10.5281/zenodo.14174161；https://doi.org/10.5281/zenodo.14176443）
- **阅读日期**：2026-05-13（按当前日期）
- **在该方向中的位置**：本文是 TF–DNA 结合特异性建模领域迄今最大规模的开放社区基准测试（challenge），系统比较了 PWM 与各类 advanced approaches（以 CNN 类深度学习为主）在跨平台（A2G/G2A）与平台内（WET）预测任务上的表现。它为该领域提供了标准化的数据划分、评测协议和可复现的基准框架，是评估 AI 方法（尤其深度学习）在 TF–DNA 互作建模中真实泛化能力的关键参考。

## 02 一句话总结

本文通过组织 IBIS 社区挑战赛，利用 40 个人类转录因子的多平台实验数据（ChIP-seq、HT-SELEX、SMiLE-seq、PBM 等），在严格隔离的测试集上系统比较了 PWM 与各类深度学习模型的 TF–DNA 结合特异性预测性能，发现精心设计的 CNN 类模型在跨平台泛化上仅以有限幅度优于 PWM，且许多深度学习方案在跨实验泛化中失败。

## 03 研究问题

- **具体问题**：在跨平台（从人工序列到基因组序列，或反之）和平台内场景下，哪种 TF–DNA 结合特异性建模方法（PWM vs. 深度学习等 advanced approaches）表现最好？深度学习模型是否真的显著优于传统 PWM？
- **为什么重要**：TF–DNA 结合特异性模型是调控基因组学的基础工具，广泛应用于调控变异效应预测、增强子/启动子注释等。此前缺乏大规模、公平、跨平台的系统比较，导致社区对"先进方法是否真的更优"缺乏定量认识。
- **现有方法不足**：以往的基准测试规模有限、数据来源单一（常为同一平台）、缺乏统一的评测协议，且常由方法开发者自行评测，存在选择偏差。
- **精确研究问题（Can...?）**：Can deep learning models trained on one type of TF–DNA binding assay (e.g., HT-SELEX) generalize to predict binding in another assay type (e.g., ChIP-seq) better than position weight matrices, when evaluated on previously unseen human transcription factors with rigorous cross-platform benchmarking?

## 04 背景与发展脉络

- **阶段一：PWM 时代（~1980s–2000s）**：以 position weight matrix 为核心表示，假设各位置核苷酸独立贡献。代表工具：MEME、HOMER、RSAT、SeSiMCMC 等。优点：简单、可解释、计算高效；局限：无法建模位置间依赖（如二核苷酸偏好、高阶互作）。
- **阶段二：高级表示与机器学习（~2010s–）**：引入 Markov 模型、贝叶斯模型、k-mer 特征、支持向量机等，试图超越 PWM 的独立性假设。代表：BaMM、k-mer-based 方法。优点：可捕获部分依赖；局限：仍受特征工程限制，泛化能力提升有限。
- **阶段三：深度学习（~2015–）**：CNN、RNN、Transformer 等架构直接学习序列到结合强度的映射。代表：DeepBind、LegNet、Malinois 等。优点：可自动学习复杂特征；局限：易过拟合、可解释性差、跨平台泛化未经验证。
- **阶段四：社区挑战赛与系统基准（本文，2024–2025）**：IBIS 是首个大规模、多平台、严格隔离测试集的开放挑战，将 PWM 与深度学习等 advanced approaches 置于同一评测框架下。本文主张：深度学习有优势但幅度有限，且高度依赖设计质量；PWM 仍是强基线。
- **脉络说明**：以上脉络基于本文 Introduction 和 Discussion 的叙述框架，属于「经外部核验」的领域共识（PWM 历史地位、深度学习兴起等均有广泛文献支持），但具体阶段划分和代表性方法选择为本文框架。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 缺乏公平的跨平台基准 | 以往评测多在同一平台内进行，或由方法开发者自行评测 | 数据分散、协议不统一、缺乏社区协作 | Introduction 第 2–3 段；"benchmarking studies remained sporadic and usually were focused on synthetic data, data from one experimental platform" |
| 深度学习易过拟合平台特异特征 | 许多深度学习方案在跨平台（A2G/G2A）中表现远差于平台内（WET） | 模型容量大，易学习训练平台的实验偏差而非真实结合特异性 | Results "Triple-A models outperform PWMs" 节；"many deep learning–based approaches failed substantially in cross-experiment validation" |
| PWM 的独立性假设被高估为瓶颈 | 传统观点认为 PWM 无法建模位置依赖，但实际表现仍具竞争力 | 多数 TF 的结合位点可能确实以独立贡献为主，高阶依赖贡献有限 | Results 节；"position weight matrices displayed a surprisingly strong performance out of the box" |
| 评测指标单一化风险 | 单一指标（如 AUROC）可能掩盖模型在特定任务上的差异 | 不同任务（分类 vs 排序 vs 变异效应）需要不同指标 | Methods "Benchmarking protocols" 节；使用 AUROC、AUPRC、Kendall τ 等多种指标 |
| 信息泄漏风险 | 训练与测试数据若重叠或共享序列特征，会虚高评估结果 | 序列数据天然存在同源性和重复性 | Methods "Ensuring fair play and fair evaluation" 节；染色体级别 holdout、去重处理 |
| 变异效应预测与结合预测脱节 | 结合预测好的模型未必能准确预测 SNP 效应 | 变异效应涉及等位基因间微小差异，对模型精度和分辨率要求更高 | Results "rSNP" 节；"better TFBS prediction did not necessarily improve recognition of regulatory variant effects" |

## 06 核心思想

1. **表面方法**：组织开放社区挑战赛（IBIS），提供统一的训练数据（40 个人类 TF、5 种实验平台）、预先公布的评测协议和隐藏测试集，邀请全球团队提交 PWM 和 advanced approaches（AAA）模型，并用多种指标（AUROC、AUPRC、Kendall τ）在跨平台（A2G/G2A）和平台内（WET）场景下进行盲评。

2. **核心洞察**：
   - 深度学习的优势是真实的但有限：最佳 AAA 模型在跨平台任务中一致优于 PWM，但幅度不大（"limited margin"），且仅在"精心设计"时成立。
   - PWM 的竞争力远超预期：作为最简单的模型家族，PWM 在多数场景下仍是强基线，说明 TF 结合特异性可能主要由独立位置贡献主导。
   - 跨平台泛化是深度学习的真正考验：许多 AAA 模型在 WET 中表现优异但在 A2G/G2A 中崩溃，说明它们学到了平台特异偏差而非通用结合规则。
   - 内部基准选择（internal benchmarking）是成功的关键：获胜团队并非使用了最复杂的架构，而是通过系统性的内部验证选择了最稳健的模型配置。

3. **可能的普适教训** [Analysis]：
   - 在生物序列建模中，"更复杂的模型"不等于"更好的泛化"；跨实验/跨平台的验证是检验模型是否学到真实生物学信号的关键。
   - 社区挑战赛（crowd-sourced benchmarking）是解决方法评估偏差的有效机制，尤其适合数据分散、方法多样的领域。
   - 简单基线（如 PWM）应始终作为新方法的对照，否则无法判断复杂模型的增量价值。

## 07 方法总览

- **输入**：40 个人类 TF 的多平台实验数据，包括 ChIP-seq（CHS）、HT-SELEX（HTS）、基因组 HT-SELEX（GHTS）、SMiLE-seq（SMS）、蛋白结合微阵列（PBM，含 ME 和 HK 两种设计）。训练数据为部分平台/实验的序列及结合标签，测试数据为其他平台/实验的序列。
- **输出**：对测试序列的 TF 结合预测分数（用于排序/分类），以及（对 AAA 模型）对 rSNP 等位基因效应的预测。
- **模块**：
  1. **数据预处理模块**：统一处理各平台原始数据（PBM 归一化、ChIP-seq/GHTS 的 peak calling、HT-SELEX/SMiLE-seq 的 read 处理），生成标准化的训练/测试集。
  2. **PWM 基线模块**：使用多种经典 motif discovery 工具（MEME、STREME、RSAT、HOMER、SeSiMCMC 等）从训练数据构建 PWM，并用两种扫描方式（sum-occupancy 和 best-hit）评分。
  3. **AAA 模型模块**：参赛团队提交的各类 advanced approaches，以 CNN 类深度学习为主，也包括混合架构（CNN-RNN）、集成模型等。
  4. **评测模块**：对每个模型在多个基准（A2G、G2A、WET）上计算 AUROC、AUPRC、Kendall τ 等指标，并通过层次化 rank aggregation 得到最终排名。
  5. **rSNP 效应评测模块**：使用 ChIP-seq/GHTS 中检测到的等位基因特异性结合位点，评估模型对 SNP 效应的预测能力。
- **训练**：各参赛团队自行设计训练流程（数据增强、超参数选择、集成策略等），但必须仅使用提供的训练数据。
- **反馈回路**：Leaderboard 阶段（公开、小规模测试集）允许团队迭代优化；Final 阶段（隐藏测试集）为一次性盲评。
- **假设**：模型应仅从 DNA 序列预测结合特异性，不依赖额外基因组注释（如染色质可及性、保守性等）。

**文字流程**：组织者收集并预处理多平台实验数据 → 划分训练/测试集（按染色体和平台隔离）→ 公开 Leaderboard 阶段供团队迭代 → 团队提交最终模型（PWM 或 AAA）→ 组织者统一评测（A2G/G2A/WET 多基准）→ 层次化 rank aggregation 确定排名 → 额外进行 rSNP 效应评测 → 汇总分析各模型家族的表现模式。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 数据预处理与标准化 | 将 5 种实验平台的原始数据统一为可训练的序列-标签格式 | 各平台数据格式、偏差、噪声特性差异大，需统一处理才能公平比较 | 输入：原始实验数据（FASTQ、BED、PBM 强度等）；输出：标准化的训练/测试序列集 | Methods "Experimental data preprocessing" 节 | 移除后各团队需自行处理数据，引入额外变量，降低可比性 |
| 多基准评测协议 | 在 A2G、G2A、WET 三种场景下用多种指标评测模型 | 单一场景/指标无法全面反映模型泛化能力 | 输入：模型预测分数 + 测试集标签；输出：AUROC、AUPRC、Kendall τ 等指标 | Methods "IBIS benchmarking protocols" 节 | 移除后无法区分"平台内过拟合"与"真实泛化能力" |
| 层次化 rank aggregation | 将多个指标、多个 TF 的排名综合为团队最终排名 | 不同指标和 TF 间表现可能不一致，需稳健的聚合策略 | 输入：各指标下的排名；输出：综合排名 | Methods "Ranking strategy" 节 | 移除后排名将依赖单一指标，易受异常值影响 |
| PWM 扫描模块（sum-occupancy / best-hit） | 用 PWM 对测试序列进行两种方式的评分 | 评估 PWM 在不同扫描策略下的表现，作为 AAA 的基线 | 输入：PWM + 测试序列；输出：序列分数 | Results "PWM scanning" 节；Supplementary Figure SF7 | 移除后无法量化 AAA 相对 PWM 的增量 |
| rSNP 效应评测模块 | 评估模型对等位基因特异性结合变化的预测能力 | 这是 TF 结合模型的重要实际应用场景，且对模型精度要求更高 | 输入：rSNP 位点序列（Ref/Alt）+ 模型预测；输出：concordance curve 的 AUC | Results "rSNP" 节；Figure 3 | 移除后无法检验模型在"微小序列变化"上的分辨率 |
| 内部基准选择（团队侧） | 各团队在 Leaderboard 上迭代优化模型选择 | 帮助团队避免过拟合 Final 测试集，选择泛化更好的配置 | 输入：Leaderboard 测试集反馈；输出：最终提交的模型配置 | Results "IBIS Solutions and Winners" 节 | 移除后团队可能直接过拟合 Final 测试集，评估失真 |

## 09 实验设计与证据链

- **数据集**：40 个人类 TF，5 种实验平台（CHS、HTS、GHTS、SMS、PBM），共 372 个实验。训练/测试按染色体隔离（奇/偶染色体）和平台隔离划分。
- **指标**：AUROC、AUPRC（分类）、Kendall τ_b（HT-SELEX 排序）、concordance curve AUC（rSNP）。
- **基线**：MEX1 集合（从 IBIS 训练数据用多种工具构建的最佳 PWM），以及 consensus 序列基线。
- **参赛规模**：Leaderboard 阶段 28 队、1905 次提交；Final 阶段 19 队。
- **评测流程**：Final 阶段每队限一次提交，AAA 和 PWM 分别排名，再通过层次化 rank aggregation 综合。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 主基准（A2G/G2A） | AAA 是否优于 PWM | 19 队 AAA vs. PWM 提交 vs. MEX1 基线 | 最佳 AAA 一致优于 PWM 和 MEX1，但幅度有限 | 深度学习有真实但有限的跨平台优势 | 不能说明所有 AAA 都优于 PWM；不能说明优势在所有 TF/平台中一致 | Results "Triple-A models outperform PWMs" 节；Figure 2 |
| WET 基准 | 平台内预测表现 | 同平台训练/测试 | 多数 AAA 在 WET 中表现优异 | 深度学习能很好拟合平台内模式 | WET 表现不能预测跨平台泛化 | Supplementary Figure SF3 |
| 跨平台对比（A2G vs. G2A） | 泛化方向是否对称 | 从人工到基因组 vs. 从基因组到人工 | 两个方向表现模式不同，A2G 更具挑战性 | 数据分布差异影响泛化难度 | 不能确定具体哪个因素导致不对称 | Figure 2 |
| rSNP 效应预测 | 结合预测好是否意味着变异效应预测好 | 各模型对 rSNP 的 concordance | 最佳 AAA 在 rSNP 上未显著优于 PWM | 结合预测与变异效应预测是不同能力 | 不能排除某些模型在特定 TF 上表现好 | Results "rSNP" 节；Figure 3 |
| 后挑战评估（post-challenge） | 额外深度学习架构的表现 | 多种公开架构（LegNet 变体、DNA 语言模型等） | 多数后挑战模型未超过最佳参赛 AAA；语言模型表现差 | 架构选择和数据策略比模型家族更重要 | 不能排除未来语言模型改进后表现提升 | Results "Post-challenge" 节；Figure 4 |
| 消融分析（LegNet 变体） | 架构微调的影响 | LegNet-Pure vs. LegNet-Max vs. LegNet-WE 等 | 微调（如 pooling 替换）显著影响泛化 | 小架构改动可大幅改变泛化能力 | 不能确定最优架构的通用原则 | Results "Post-challenge" 节；Supplementary Figure SF9 |

## 11 结论正确解读

- **任务范围**：本文评测的是"从序列预测 TF 结合特异性"这一任务，涵盖跨平台（A2G/G2A）和平台内（WET）两种泛化场景。不涉及 TF 结合位点的基因组注释、染色质状态整合等更复杂任务。
- **oracle/真值输入**：测试标签来自实验数据（ChIP-seq peaks、HT-SELEX/SMiLE-seq reads、PBM 强度），但经过统一预处理和匿名化。模型仅接收序列输入，不接收实验元数据。
- **端到端状态**：AAA 模型是端到端训练的（序列→预测分数），PWM 则需先进行 motif discovery 再扫描，属于两阶段流程。
- **算力成本**：本文未报告各模型的训练/推理成本，但指出深度学习模型需要更多计算资源。语言模型（DNABERT2、NT、GENA-LM）因参数量大，训练成本显著更高。
- **历史数据依赖**：训练数据来自 Codebook 项目，覆盖 40 个 TF，但 TF 选择偏向已知有明确结合基序的因子；对无明确基序或结合依赖辅助因子的 TF，结论可能不适用。
- **模型依赖**：结论基于 19 个参赛团队的提交和若干后挑战模型，不能覆盖所有可能的深度学习架构。
- **最难情形**：跨平台泛化（尤其 A2G）是最难场景；短基序 TF（如 CG 结合因子）和结合位点高度简并的 TF 对模型挑战最大。
- **群体/领域边界**：结论仅适用于人类 TF；对其它物种、非 TF 的 DNA 结合蛋白（如染色质重塑因子）、或 RNA 结合蛋白不适用。
- **不确定性**：排名在 1000 次随机子采样中保持稳定（Figure 1），但个体 TF 间的表现差异大，部分 TF 上 AAA 与 PWM 无显著差异。

**有边界的复述**：在 IBIS 挑战赛的设定下（40 个人类 TF、5 种实验平台、严格隔离的测试集），精心设计的 CNN 类深度学习模型在跨平台泛化上一致但有限地优于 PWM；PWM 仍是强基线；深度学习模型的成功高度依赖内部验证和架构微调，而非模型家族本身。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 数据覆盖有限 | 仅 40 个 TF，且偏向已知基序的因子 | 扩展到更多 TF 和物种 | Discussion 第 2 段 |
| 平台间差异大 | 不同实验平台测得的结合偏好存在差异，影响跨平台评估 | 开发更统一的实验协议 | Discussion 第 3 段 |
| rSNP 预测困难 | 所有模型在 rSNP 效应预测上表现有限 | 需要包含突变效应的训练数据 | Results "rSNP" 节 |
| 语言模型表现差 | DNA 语言模型在微调后仍远低于监督模型 | 探索更好的微调策略或架构 | Results "Post-challenge" 节 |
| 无法完全排除信息泄漏 | 尽管设计了染色体隔离，但序列同源性可能仍导致泄漏 | 更严格的序列去重和同源性过滤 | Methods "Ensuring fair play" 节 |
| 参赛者策略差异 | 团队的计算资源、经验差异可能影响结果 | 提供更标准化的计算环境 | Discussion 第 4 段 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 参赛团队的自选择偏差 | 参赛者可能只提交在其内部验证中表现好的模型，导致 AAA 的平均表现被高估 | 影响对"深度学习 vs. PWM"整体结论的解读 | 对比所有提交（含 Leaderboard 阶段）与 Final 提交的表现差异 | Results "Leaderboard" 节 |
| 测试集 TF 与训练集 TF 的相似性 | 部分 TF 属于同一家族，可能共享基序特征，降低跨 TF 泛化难度 | 影响结论的普适性 | 按 TF 家族分层分析表现 | Table 1；Supplementary Table ST1 |
| 指标选择偏向 | AUROC/AUPRC 对类别不平衡敏感，可能不反映实际应用中的排序质量 | 影响对模型实用价值的判断 | 增加 NDCG、召回率@k 等指标 | Methods "Benchmarking protocols" 节 |
| 后挑战模型的训练数据可能包含测试信息 | 后挑战模型使用了与参赛者相同的训练数据，但可能通过公开的 TF 基序数据库间接引入测试 TF 信息 | 影响后挑战评估的公平性 | 检查训练数据与公开数据库的重叠 | Results "Post-challenge" 节 |
| 未报告计算成本 | 深度学习模型的训练成本可能远超 PWM，但未在评估中体现 | 影响实际部署决策 | 记录各模型的训练时间和资源消耗 | 未提供 |
| 单一数据来源（Codebook） | 所有数据来自同一项目，可能存在系统性实验偏差 | 影响结论的外部效度 | 用独立数据集（如 ENCODE）进行交叉验证 | Introduction 第 2 段 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **跨平台基准设计**：本文的 A2G/G2A 划分策略（训练和测试使用不同实验平台）是评估模型泛化能力的有效设计，可直接迁移到 TF–DNA 互作建模的其它任务（如预测突变效应、预测细胞类型特异性结合）。
2. **PWM 作为强基线**：在开发新的深度学习模型时，应始终将 PWM（或类似简单模型）作为基线，并报告相对提升幅度。本文表明，提升可能远小于预期。
3. **内部验证的重要性**：获胜团队的成功并非来自复杂架构，而是来自系统的内部基准选择。这提示在 TF–DNA 建模中，数据划分策略和模型选择流程可能比架构创新更重要。
4. **rSNP 预测的挑战**：结合预测与变异效应预测是两种能力，前者好不代表后者好。这提示在开发用于调控变异解读的模型时，需要专门的训练目标和评测协议。
5. **模型集成与数据增强**：虽然本文未详细披露，但多个获胜团队使用了集成策略和反向互补增强，这可能是提升泛化的有效手段。
6. **语言模型的局限**：DNA 语言模型在 TF 结合预测上表现不佳，提示预训练策略可能不适合短序列、高信噪比任务，或需要不同的微调方法。

## 15 与已有知识的连接

- **相似工作**：本文与 DREAM 挑战赛系列（如 DREAM-ENCODE、Random Promoter DREAM Challenge 2022）在方法论上高度相似，均采用社区挑战赛+统一评测的模式。本文的层次化 rank aggregation 策略直接借鉴了 DREAM-ENCODE 的流程。
- **互补工作**：Codex 等大规模 TF 结合数据资源（如 ENCODE、Factorbook）提供了本文所用数据的来源背景；本文的基准测试结果可视为对这些数据资源建模方法的系统评估。
- **冲突观点**：本文发现 DNA 语言模型表现不佳，与部分文献声称的预训练模型在调控任务上的优势相矛盾。这提示语言模型的优势可能局限于特定任务或需要更大规模的数据。
- **可迁移方法**：bibis 包的数据预处理和评测流程可直接用于其它物种或其它类型的 DNA-蛋白质互作建模；A2G/G2A 的跨平台评估思路可迁移到 RNA-蛋白质互作、染色质可及性预测等领域。
- **理论框架**：本文的"内部基准选择"概念与机器学习中的模型选择理论一致，但强调了在生物数据中跨域验证的特殊重要性。

## 16 研究想法

**Agent 生成的研究候选**：

1. **名称**：跨物种 TF 结合特异性迁移学习基准
   - **来源局限/观察**：IBIS 仅覆盖人类 TF，跨物种泛化未测试
   - **核心假设**：在人类 TF 上预训练的深度学习模型可迁移到小鼠、果蝇等物种的 TF 结合预测，但迁移效果因 TF 家族保守性而异
   - **增量**：扩展 IBIS 评测框架到多物种，建立跨物种迁移学习的标准基准
   - **初步方法**：使用 IBIS 数据预训练 CNN，在其它物种的 ChIP-seq/HT-SELEX 数据上微调或零样本测试
   - **验证方式**：与物种特异的 PWM 基线比较，报告跨物种 AUROC/AUPRC
   - **创新状态**：unverified

2. **名称**：结合位点内 SNP 效应的细粒度评测协议
   - **来源局限/观察**：IBIS 的 rSNP 评测显示所有模型表现有限，但未深入分析失败模式
   - **核心假设**：现有模型在 SNP 效应预测上的局限源于训练目标（分类）与任务需求（微小差异排序）不匹配
   - **增量**：设计专门的训练目标（如对比学习、排序损失）和评测指标（如 concordance 的置信区间）
   - **初步方法**：在 IBIS 数据上训练多任务模型（同时预测结合强度和等位基因效应），在 rSNP 数据集上评测
   - **验证方式**：与 IBIS 最佳模型比较 concordance AUC，并分析 SNP 类型（转换/颠换、基序核心/侧翼）的差异
   - **创新状态**：unverified

3. **名称**：基于结构信息的 TF 结合特异性增强
   - **来源局限/观察**：IBIS 限制参赛者仅使用序列信息，但结构信息（如 AlphaFold 预测的 TF 结构）可能提供互补信号
   - **核心假设**：将 TF 蛋白结构特征（如 DNA 结合域的理化性质）与序列特征结合，可提升跨平台泛化
   - **增量**：首次系统评估结构信息在 TF 结合特异性建模中的增量价值
   - **初步方法**：提取 TF 的 AlphaFold 结构特征，与 CNN 序列特征融合，在 IBIS 基准上评测
   - **验证方式**：与 IBIS 最佳序列模型比较，控制计算成本
   - **创新状态**：unverified

4. **名称**：TF 结合基序的层次化表示学习
   - **来源局限/观察**：IBIS 显示 CNN 优于 PWM 但幅度有限，提示现有深度模型可能未充分利用基序的层次结构
   - **核心假设**：显式建模基序的层次结构（单体→二聚体→复合体）可提升模型的可解释性和泛化
   - **增量**：提出可解释的层次化 CNN 架构，在 IBIS 基准上同时评测性能和可解释性
   - **初步方法**：设计多尺度卷积模块，每个尺度对应不同的基序层级，用注意力机制融合
   - **验证方式**：与 IBIS 最佳模型比较，并用 motif 发现任务验证学习到的表示
   - **创新状态**：unverified

5. **名称**：低资源 TF 的结合特异性预测
   - **来源局限/观察**：IBIS 中部分 TF 训练数据有限，模型表现差异大
   - **核心假设**：利用 TF 家族内的基序相似性，通过元学习或参数共享提升低资源 TF 的预测
   - **增量**：建立低资源 TF 预测的专门基准，评估数据增强和迁移策略
   - **初步方法**：在 IBIS 数据上训练元学习模型（如 MAML），在低资源 TF 上测试
   - **验证方式**：与单 TF 训练的 CNN 比较，报告低资源 TF 的 AUPRC
   - **创新状态**：unverified