## 01 基本信息
- **标题**：Unsupervised domain adaptation methods for cross-species transfer of regulatory code signals
- **作者与单位**：Latyshev, Pavel; Pavlov, Fedor; Herbert, Alan; Poptsova, Maria（单位未在提供材料中明确列出，部分作者隶属俄罗斯国立研究大学高等经济学院，依据计算资源声明推断）
- **期刊/预印本平台**：Frontiers in Big Data
- **年份**：2023-04-18
- **论文类型**：实证基准研究（benchmark study）
- **领域**：计算基因组学 / 深度学习 / 迁移学习（Unsupervised Domain Adaptation）
- **关键词**：domain adaptation, transfer learning, regulatory code, transcription factor binding sites, histone marks, cross-species prediction, deep learning
- **DOI/arXiv 号**：10.3389/fdata.2023.1140663
- **代码**：https://github.com/pavellatko/dna-domain-adaptation
- **数据**：ChIP-atlas（https://chip-atlas.org）；人类基因组 hg38、小鼠基因组 mm10（UCSC）
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文直接针对「跨物种 TF–DNA 结合位点与组蛋白修饰信号的预测」任务，系统比较了 9 种无监督域适应（UDA）方法在人类↔小鼠 ChIP-seq 数据上的迁移效果。属于「蛋白质–DNA 互作 × 深度学习 × 迁移学习」交叉方向，核心关注点是：当目标物种缺乏标注数据时，如何利用源物种的调控信号知识进行有效迁移。对 TF–DNA 结合机制研究者的价值在于：提供了跨物种调控代码迁移的系统性基准，并揭示了非对抗性方法（MCC、DAN）在此任务上的优势。

## 02 一句话总结
本文以人类和小鼠的 ChIP-seq 数据（4 个转录因子、10 个组蛋白修饰，共 71 个实验集）为基准，训练混合 CNN+LSTM 模型，系统比较 9 种无监督域适应方法在跨物种调控信号预测中的表现，发现非对抗性方法 MCC（Minimum Class Confusion）和 DAN（Deep Adaptation Network）显著优于对抗性方法（DANN、ADDA、CDAN、MCD），且跨物种直接预测（无域适应）对 TF 结合位点比对组蛋白修饰更有效。

## 03 研究问题
- **具体问题**：当目标物种（如小鼠）缺乏实验标注数据时，能否利用源物种（如人类）的 ChIP-seq 数据，通过无监督域适应方法有效预测目标物种的转录因子结合位点（TFBS）和组蛋白修饰（HM）信号？
- **为什么重要**：ChIP-seq 实验成本高、耗时，且许多物种缺乏实验数据。若能实现可靠的跨物种调控信号迁移，将极大扩展调控基因组学的覆盖范围，并为进化保守性研究提供计算手段。
- **现有方法不足**：此前跨物种预测多依赖直接应用源模型（baseline），未系统利用目标物种的无标注序列信息进行域适应；且已有 UDA 方法多在图像数据上验证，其在基因组序列数据（高噪声、高维度、物种特异重复元件干扰）上的适用性未知。
- **精确研究问题（Can 形式）**：Can unsupervised domain adaptation methods, trained on labeled ChIP-seq data from one species (human or mouse), significantly improve the prediction of transcription factor binding sites and histone mark signals in another species (mouse or human) compared to direct application of the source model without adaptation?

## 04 背景与发展脉络
*注：以下脉络基于本文框架及引用文献，部分经外部核验，标注如下。*

1. **早期跨物种调控预测（无迁移学习）**：直接训练源物种模型并应用于目标物种。代表工作如 Chen et al. (2018) 用 SVM 和 CNN 做跨物种增强子预测，发现存在进化保守信号。局限：未利用目标物种无标注数据，性能受物种间序列差异限制。
2. **域适应方法在计算机视觉中的发展**：从对抗性方法（DANN, Ganin et al., 2015; CDAN, Long et al., 2018）到非对抗性方法（DAN, Long et al., 2015; JAN, Long et al., 2017; MCC, Jin et al., 2020），均在图像基准（Office-31, VisDA-2017）上验证。局限：图像数据与基因组序列数据分布特性差异大。
3. **域适应在基因组学中的初步应用**：Cochran et al. (2022) 将 DANN 用于跨物种 TF 结合预测，验证了可行性，但仅测试单一对抗性方法，且未系统比较多种 UDA 架构。
4. **本文位置**：首次系统性地将 9 种 UDA 方法（涵盖对抗性、非对抗性、统计匹配三类）应用于跨物种调控代码迁移，使用真实 ChIP-seq 数据（而非模拟数据），提供大规模基准（1,420 个模型），并揭示非对抗性方法在此任务上的优势。

*脉络核验状态*：本文框架内引用完整；Chen et al. (2018) 与 Cochran et al. (2022) 为外部文献，经本文引用确认存在，但未独立核验其具体结果。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 实验数据稀缺 | 多数物种缺乏 ChIP-seq 实验数据，实验成本高 | NGS 实验昂贵，无法覆盖所有物种和组织类型 | Abstract："experiments are still expensive and are not available for many species of interest" |
| 直接跨物种预测性能有限 | 源模型直接应用于目标物种时，性能受物种间序列差异影响 | 物种间存在序列差异、物种特异重复元件（如人类 Alu、小鼠 B1）引入噪声 | Discussion："even without additional filtering for obvious species-specific sequences such as human Alu and mouse B1 transposons" |
| 现有 UDA 方法未在基因组数据上验证 | 9 种 UDA 方法均源自图像领域，其在基因组序列上的表现未知 | 图像与序列数据分布特性差异大，基因组数据噪声高、维度高 | Introduction："It is of interest to test applicability of those methods to experimental molecular biology data sets that are incomplete, noisy, and subject to other biases" |
| 对抗性方法训练不稳定 | DANN、ADDA 在多数实验中未优于 baseline | 对抗性训练在噪声数据上易不稳定，判别器与特征提取器的博弈难以收敛 | Results 图 5："Two other adversarial models—DANN and ADDA—did not perform better than the baseline model for most of the experiments" |
| 组蛋白修饰信号稀疏 | 部分 HM（如 H3K36me1、H3K23ac）信号稀疏，单组织数据不足 | 稀疏信号导致训练数据不足，模型难以学习有效特征 | Results 2.3："combined approach works better for sparse HM signals (for example, H3K36me1 and H3K23ac)" |

## 06 核心思想
1. **表面方法**：构建混合 CNN+LSTM 模型作为特征提取器，在源物种（人类或小鼠）的 ChIP-seq 数据上训练分类器，然后使用 9 种不同的 UDA 方法，利用目标物种的无标注序列数据对模型进行域适应微调，最后在目标物种的标注数据上评估性能。
2. **核心洞察**：跨物种调控代码迁移中，**非对抗性方法（MCC、DAN）显著优于对抗性方法**。作者认为，基因组序列数据的高噪声和物种特异重复元件使得对抗性训练的判别器难以稳定学习域不变特征，而基于统计匹配（MCC 的最小类混淆、DAN 的最大均值差异）的方法更鲁棒。此外，TFBS 比 HM 更适合跨物种迁移，反映了 TF 结合序列的进化保守性更强。
3. **可能的普适教训** [Analysis]：在生物序列数据上，域适应方法的选择不应直接照搬图像领域的经验。对抗性方法在图像上表现优异，但在高噪声、高维度的基因组数据上可能失效；统计匹配方法（如 MCC）因其简单性和鲁棒性反而更适用。这提示：**方法选择应基于数据特性而非领域惯例**。

## 07 方法总览
- **输入**：源物种（人类 hg38 或小鼠 mm10）的 ChIP-seq 峰区序列（±500 bp，共 1 kb），one-hot 编码为 4×1000 二进制矩阵；目标物种的无标注序列数据（随机采样，大小为目标样本的 2 倍）。
- **输出**：目标物种基因组上 TFBS 或 HM 位置的二分类预测（峰 vs. 非峰）。
- **特征提取器**：混合 CNN+LSTM 网络。CNN 层：1D 卷积（256 个 kernel，size=20）+ ReLU + MaxPooling（size=15）+ Dropout；随后接双向 LSTM（hidden size=128）。
- **域适应模块**：9 种 UDA 方法，分为三类：
  - 对抗性：DANN、ADNA、CDAN、MCD
  - 非对抗性（统计匹配）：DAN、JAN、MDD、AFN
  - 非对抗性（熵最小化）：MCC
- **训练流程**：
  1. 在源物种标注数据上训练 baseline 模型（CNN+LSTM 分类器）。
  2. 对每个 UDA 方法，使用源物种标注数据 + 目标物种无标注数据，按各方法的目标函数进行域适应训练。
  3. 在目标物种的标注数据上评估（accuracy、PR AUC、ROC AUC）。
- **反馈回路**：无显式主动学习或迭代优化回路；UDA 训练为一次性域适应过程。
- **假设**：源物种和目标物种的调控代码共享进化保守的序列特征；目标物种的无标注序列足以提供域分布信息。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CNN 层 | 提取局部序列 motif 特征 | 捕获 TF 结合位点的短序列模式 | 输入：4×1000 one-hot 矩阵；输出：特征图 | Results 图 3；作者称混合架构优于单 CNN 或单 LSTM | 预期降低 motif 检测能力 [Analysis]；作者未做消融实验 |
| 双向 LSTM 层 | 捕获序列长程依赖和上下文信息 | TF 结合位点可能受远端序列上下文影响 | 输入：CNN 特征图；输出：隐状态序列 | Results 图 3；作者称混合架构优于单 LSTM | 预期降低对长程序列依赖的建模能力 [Analysis]；作者未做消融实验 |
| 分类器 | 输出峰/非峰二分类预测 | 完成下游预测任务 | 输入：LSTM 隐状态；输出：二分类概率 | Results 图 4 | 无法完成预测任务 |
| 域适应模块（9 种 UDA） | 对齐源/目标域特征分布 | 减少跨物种分布偏移，提升目标域泛化 | 输入：源/目标特征表示；输出：域适应后的特征 | Results 图 5：MCC、DAN 显著优于 baseline | 移除后退化为 baseline 直接预测，性能下降（MCC 最高提升 29%） |
| 负样本生成 | 随机采样基因组序列作为负类 | 提供分类训练所需的负样本 | 输入：目标基因组序列；输出：随机序列集 | Methods 5.2 | 负样本质量影响分类性能 [Analysis]；作者未系统评估负样本选择策略 |

## 09 关键公式符号
本文未提供显式数学公式。核心方法涉及的关键概念（基于引用文献，非本文推导）：
- **DAN**：MK-MMD（Multiple Kernel Maximum Mean Discrepancy），度量源/目标域特征分布距离，公式为 MMD² = ‖E_s[φ(x_s)] − E_t[φ(x_t)]‖²_H，其中 φ 为核映射，H 为 RKHS。
- **MCC**：最小类混淆损失，基于目标域预测概率矩阵 P 的类混淆矩阵，最小化 ‖P^T P‖_F（Frobenius 范数），鼓励目标域预测的类间低混淆。
- **对抗性方法（DANN/CDAN）**：min-max 博弈，判别器损失 L_d = −E[log D(f(x_s))] − E[log(1 − D(f(x_t)))]，特征提取器最小化 −L_d。
- **用途**：这些公式定义了各 UDA 方法的优化目标，是方法比较的核心。
- **来源**：Methods 5.4 引用 github.com/thuml/Transfer-Learning-Library 实现，未在本文中显式列出公式。

## 10 实验设计与证据链
- **数据集**：ChIP-atlas 数据库，人类（hg38）和小鼠（mm10）基因组；4 个 TF（CTCF、RAD21、SPI1、TBX21）和 10 个 HM（H2B、H3K23ac、H3K36ac、H3K36me1、H3K79me1、H3K27ac、H3K4me1、H3K4me2、H3K4me3、H3K9me3）；组织类型包括血液、肾脏、肺、肝、乳腺、前列腺、胰腺、神经组织、干细胞；共 71 个实验集（59 个 HM + 12 个 TF）。
- **规模**：每个实验集样本量约 40,000 个峰区段（范围 50,000 ± 12,500）；负样本为随机基因组序列。
- **指标**：accuracy、PR AUC、ROC AUC。
- **基线**：无域适应的源模型直接预测（baseline）。
- **评测协议**：人类→小鼠和小鼠→人类两个方向的迁移实验；每个 UDA 方法在相同数据上运行；共 1,420 个模型（1 baseline + 9 UDA × 71 实验集 × 2 方向）。
- **计算资源**：俄罗斯国立研究大学高等经济学院超算集群。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 9 种 UDA 方法 vs baseline（TF） | UDA 方法能提升跨物种 TFBS 预测 | 4 个 TF，人类↔小鼠双向 | MCC、DAN 显著优于 baseline；CDAN 第三；DANN、ADDA 多数未优于 baseline | 非对抗性方法在 TFBS 迁移中更有效 | 未证明 UDA 对所有 TF 均有效；未报告各 TF 的详细数值 | Results 图 4B、图 5 |
| 9 种 UDA 方法 vs baseline（HM） | UDA 方法能提升跨物种 HM 预测 | 10 个 HM，人类↔小鼠双向 | MCC 为绝对最优；DAN 次之；对抗性方法表现不稳定 | MCC 对 HM 迁移同样有效 | 未报告各 HM 的详细数值；未分析 HM 类型间差异 | Results 图 4A、图 5 |
| 组织特异性 vs 合并预测 | 合并稀疏 HM 信号可提升训练效果 | 稀疏 HM（H3K36me1、H3K23ac）合并 vs. 单组织 | 合并方法对稀疏 HM 更有效 | 合并数据可缓解稀疏信号问题 | 未量化合并带来的具体增益 | Results 2.3 |
| 模型架构比较（CNN vs LSTM vs CNN+LSTM） | 混合架构优于单一架构 | H3K27ac 和 TBX21 上比较 | CNN+LSTM 优于单 CNN 或单 LSTM | 混合架构更适合序列特征提取 | 仅两个数据集上验证，泛化性未知 | Results 图 8 |
| 稳定性测试（5 次重复） | UDA 方法性能稳定 | 2 个 HM + 2 个 TF 上 5 次运行 | 性能稳定 | UDA 方法在该数据上可重复 | 未报告方差数值 | Methods 5.4、Supplementary Table 3 |

## 11 结论正确解读
- **任务范围**：本文结论仅适用于人类↔小鼠之间的跨物种调控信号迁移，且限于 4 个 TF 和 10 个 HM。不能外推至更远缘物种（如人类↔鱼、人类↔果蝇）。
- **oracle/真值输入**：使用 ChIP-seq 峰区作为正标签，随机基因组序列作为负标签。ChIP-seq 本身存在噪声和抗体特异性偏差，标签并非绝对真值。
- **端到端状态**：方法为端到端深度学习，但依赖预定义的峰区（±500 bp）作为输入窗口，未探索可变窗口或全基因组扫描。
- **算力成本**：未报告训练时间或资源消耗；仅提及使用超算集群。
- **历史数据依赖**：依赖 ChIP-atlas 数据库的公共数据，数据质量受原始实验影响。
- **模型依赖**：所有 UDA 方法共享同一 CNN+LSTM 特征提取器，结论可能受该架构限制；其他架构（如 Transformer）下 UDA 方法排名可能不同 [Analysis]。
- **最难情形**：对抗性方法（DANN、ADDA）在多数实验中失败，提示高噪声数据下对抗训练的不稳定性；小鼠→人类方向的迁移效果未单独报告，可能比人类→小鼠更具挑战性 [Analysis]。
- **有边界的复述**：在人类和小鼠的 ChIP-seq 数据上，使用 CNN+LSTM 架构时，非对抗性 UDA 方法（MCC、DAN）能显著提升跨物种 TF 结合位点和组蛋白修饰信号的预测性能，而对抗性方法（DANN、ADDA）多数情况下无增益或负增益。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 物种范围有限 | 仅测试了人类和小鼠两个物种 | 计划在进化上更远缘的物种上测试 UDA 方法 | Discussion："we plan to extend testing of DA methods on evolutionary more divergent species to understand the limits of cross-species regulatory code transfer" |
| 未过滤物种特异重复元件 | 未对人类 Alu 和小鼠 B1 转座子进行过滤 | 未明确提及，但暗示未来可加入过滤步骤 | Discussion："even without additional filtering for obvious species-specific sequences such as human Alu and mouse B1 transposons" |
| 计算成本高 | 未报告具体训练时间，但提及计算密集 | 未明确提及 | Methods 6：仅描述使用超算集群 |
| 数据噪声与偏差 | ChIP-seq 数据本身存在噪声和实验偏差 | 未明确提及 | Abstract："incomplete, noisy and susceptible to analytic bias" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|----------------------|----------|----------|------|
| 未报告各 TF/HM 的详细数值 | 仅展示汇总图和排名，无法判断方法性能是否因 TF/HM 类型而异 | 不同 TF 的 DNA 结合特异性差异大，可能影响迁移难度 | 要求作者提供 Supplementary Table 1 的逐项数值分析 | Results 图 4-7 仅展示汇总 |
| 未分析方向不对称性 | 人类→小鼠 vs 小鼠→人类的结果可能不同，但未单独讨论 | 参考基因组质量、注释完整性差异可能影响迁移方向 | 分别报告两个方向的性能并统计检验 | Results 图 5 仅展示合并结果 |
| 未评估负样本选择策略 | 随机采样序列作为负类可能引入偏差（如 GC 含量、重复区域） | 负样本质量直接影响分类器学习 | 对比不同负样本生成策略（如匹配 GC 含量、排除重复区域） | Methods 5.2 仅描述随机采样 |
| 未与其他迁移学习范式比较 | 仅比较 UDA 方法，未与微调（fine-tuning）、多任务学习等比较 | UDA 可能不是最优迁移策略 | 增加微调、多任务学习等基线 | 未在文中提及 |
| 未报告模型不确定性 | 仅报告点估计指标，无置信区间 | 数据噪声大，性能差异可能不显著 | 报告多次运行的方差或置信区间 | Methods 5.4 仅提及稳定性，未报告数值 |
| 未讨论物种间序列同源性影响 | 人类和小鼠是近缘物种，序列保守性高，迁移相对容易 | 远缘物种迁移可能完全失败 | 在更远缘物种对（如人类↔斑马鱼）上测试 | Discussion 提及未来计划，但未在当前实验中验证 |

## 14 学到什么
**Agent 提炼的知识候选**

1. **非对抗性 UDA 方法在基因组序列数据上更优**：MCC 和 DAN 显著优于对抗性方法（DANN、ADDA）。迁移到 TF–DNA 结合研究：当目标物种缺乏 ChIP-seq 数据时，优先选择基于统计匹配或熵最小化的域适应方法，而非对抗性方法。
2. **TF 结合位点比组蛋白修饰更适合跨物种迁移**：TFBS 的跨物种预测效果优于 HM，反映 TF 结合序列的进化保守性更强。迁移到 TF–DNA 结合机制研究：TF 结合 motif 的保守性可作为跨物种功能预测的优先目标。
3. **混合 CNN+LSTM 架构适用于序列特征提取**：CNN 捕获局部 motif，LSTM 捕获长程依赖。迁移到 TF–DNA 结合研究：可借鉴此架构设计 TF 结合位点预测模型，或将其作为域适应方法的特征提取器。
4. **合并稀疏信号可提升训练效果**：对稀疏 HM 信号，合并不同组织数据优于单组织训练。迁移到 TF–DNA 结合研究：对低丰度 TF 或稀有细胞类型的 ChIP-seq 数据，可考虑合并不同条件或组织的数据增强训练。
5. **域适应可量化跨物种调控代码的保守性**：UDA 性能提升幅度可作为物种间调控代码相似性的度量。迁移到 TF–DNA 结合机制研究：通过比较不同 TF 的域适应增益，可推断哪些 TF 的结合机制在进化上更保守。
6. **基准测试框架可复用**：1,420 个模型的系统比较框架（baseline + 9 UDA × 多数据集 × 双向迁移）可作为跨物种调控预测的标准评测协议。

## 15 与已有知识连接
- **Chen et al. (2018)**：跨物种增强子预测，使用 SVM 和 CNN，发现进化保守信号。本文扩展了该方法至域适应框架，并系统比较多种 UDA 方法。
- **Cochran et al. (2022)**：将 DANN 用于跨物种 TF 结合预测。本文验证了 DANN 在此任务上效果有限，并发现非对抗性方法更优，是对该工作的直接扩展和修正。
- **Ganin et al. (2015)**：DANN 原始论文，对抗性域适应的奠基工作。本文在基因组数据上检验了其适用性。
- **Long et al. (2015, 2017)**：DAN 和 JAN 的原始论文，基于 MMD 的统计匹配方法。本文验证了 DAN 在基因组数据上的有效性。
- **Jin et al. (2020)**：MCC 原始论文，基于最小类混淆的熵最小化方法。本文发现 MCC 是跨物种调控迁移的最优方法。
- **Jiang et al. (2022)**：域适应方法综述，本文引用了其分类框架（对抗性、非对抗性、重建性）。
- **Encode 项目 (Luo et al., 2020)**：提供 ChIP-seq 数据资源，本文数据来源之一。
- **ChIP-atlas (Zou et al., 2022)**：本文主要数据来源，提供跨物种 ChIP-seq 数据。
- **与 TF–DNA 结合机制研究的连接**：本文的域适应框架可用于预测未研究物种的 TF 结合位点，为 DNA 结合 motif 的进化保守性研究提供计算工具。结合结构预测（如 AlphaFold）或分子动力学模拟，可进一步验证域适应识别的保守 motif 是否对应保守的三维结合模式。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：基于 MCC 域适应的远缘物种 TF 结合位点预测
   - **来源局限/观察**：本文仅测试人类↔小鼠（近缘物种），远缘物种（如人类↔斑马鱼、人类↔果蝇）的迁移效果未知。
   - **核心假设**：MCC 域适应在远缘物种间仍能有效迁移 TF 结合信号，但增益随进化距离增加而下降。
   - **初步方法**：在人类↔斑马鱼、人类↔果蝇的 ChIP-seq 数据上复现本文框架，比较 MCC、DAN 与 baseline 的性能。
   - **验证方式**：ROC AUC、PR AUC 对比；分析增益与物种进化距离的相关性。
   - **创新状态**：unverified

2. **候选名称**：域适应增益作为 TF 结合保守性的量化指标
   - **来源局限/观察**：本文发现不同 TF 的域适应增益不同，但未系统分析。
   - **核心假设**：域适应增益与 TF 结合 motif 的进化保守性正相关，可作为保守性的量化指标。
   - **初步方法**：对多个 TF 计算 MCC 域适应增益，与已知的 motif 保守性评分（如 phyloP、保守性打分）进行相关性分析。
   - **验证方式**：Spearman 相关性检验；在独立数据集上验证预测能力。
   - **创新状态**：unverified

3. **候选名称**：结合域适应与结构预测的跨物种 TF–DNA 结合机制解析
   - **来源局限/观察**：本文仅使用序列信息，未利用三维结构信息。
   - **核心假设**：域适应识别的保守序列特征对应保守的三维结合模式，可通过结构预测（AlphaFold）和分子动力学模拟验证。
   - **初步方法**：对域适应识别的高增益 TF，预测其与 DNA 复合物结构，比较跨物种的结构保守性。
   - **验证方式**：结构比对 RMSD、结合自由能计算。
   - **创新状态**：unverified

4. **候选名称**：对抗性域适应在基因组数据上失效的机制分析
   - **来源局限/观察**：本文发现 DANN、ADDA 在多数实验中未优于 baseline，但未解释原因。
   - **核心假设**：基因组序列的高噪声和类别不平衡导致对抗训练不稳定，判别器过拟合源域特征。
   - **初步方法**：可视化特征分布（t-SNE）、分析判别器损失曲线，对比 MCC 与 DANN 的训练动态。
   - **验证方式**：特征分布重叠度、训练收敛性指标。
   - **创新状态**：unverified

5. **候选名称**：基于 MCC 正则化的多任务跨物种调控预测框架
   - **来源局限/观察**：本文仅测试单任务迁移，未利用多任务学习。
   - **核心假设**：将 MCC 作为正则化项加入多任务学习框架，可同时提升多个 TF/HM 的跨物种预测性能。
   - **初步方法**：构建多任务 CNN+LSTM 模型，共享特征提取器，各任务独立分类头，MCC 损失作用于共享特征。
   - **验证方式**：多任务 vs 单任务性能对比；计算资源效率分析。
   - **创新状态**：unverified