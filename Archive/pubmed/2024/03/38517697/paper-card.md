## 01 基本信息
- **标题**：Comparative analysis of models in predicting the effects of SNPs on TF-DNA binding using large-scale in vitro and in vivo data
- **作者**：Han, Dongmei; Li, Yurun; Wang, Linxiao; Liang, Xuan; Miao, Yuanyuan; Li, Wenran; Wang, Sijia; Wang, Zhen
- **单位**：未提供（根据基金信息推测为中国机构）
- **期刊/平台**：Briefings in Bioinformatics
- **年份**：2024
- **论文类型**：基准评测/比较分析研究（Benchmarking study）
- **领域**：计算生物学；调控基因组学；TF–DNA 结合变异效应预测
- **关键词**：SNP；TF–DNA binding；in vitro；in vivo；model comparison；deep learning；PWM
- **DOI/arXiv**：10.1093/bib/bbae110
- **代码**：https://github.com/hdm2020/benchmark
- **数据**：https://doi.org/10.6084/m9.figshare.24961908
- **阅读日期**：未提供
- **在课题方向中的位置**：本文是 TF–DNA 结合变异效应预测模型的系统性基准评测，覆盖 PWM、传统机器学习（SVM/OLS）与深度学习（CNN）三大类方法，并同时使用大规模体外（SNP-SELEX）与体内（ASB）数据进行验证。对于本课题（TF–DNA 结合机制 × AI/物理模拟），本文提供了模型选型依据、训练数据影响分析、TF 类别的可预测性差异等关键参考，是方法评估与选择的重要基准文献。

## 02 一句话总结
本文利用大规模体外（SNP-SELEX，407 TFs）和体内（ASB，380 TFs）数据，系统比较了 14 种基于 PWM、SVM、OLS 和深度神经网络的 SNP 对 TF–DNA 结合效应预测模型，发现体外预测中 kmer/gkm 机器学习方法（deltaSVM_HT-SELEX、QBiC-Pred）最优，体内预测中基于 ChIP-seq 训练的深度多任务模型（DeepSEA、Sei、Enformer）相对更优，且预测性能与 TF 的 DBD 类别和进化保守性相关。

## 03 研究问题
- **具体问题**：不同计算模型（PWM、传统机器学习、深度学习）在预测 SNP 对 TF–DNA 结合影响时的性能差异如何？这些模型在体外（SNP-SELEX）与体内（ASB）数据上的表现是否一致？
- **为什么重要**：非编码变异是复杂性状相关变异的主体，而 TF–DNA 结合破坏是其重要功能机制。准确预测 SNP 对 TF 结合的影响对于解析 GWAS 信号、理解疾病机制至关重要。然而，已有模型缺乏系统性、大规模、跨体外/体内的公平比较。
- **现有方法不足**：已有评测（如 Wagih et al. 2018）覆盖模型数量有限（5种）、TF 数量少（101个），且未同时使用大规模体外与体内数据进行交叉验证；不同模型训练数据（体外 vs 体内）与评测数据不匹配的问题未被系统研究。
- **精确研究问题**：Can a unified benchmark using large-scale in vitro (SNP-SELEX) and in vivo (ASB) data reveal consistent model rankings for SNP effect prediction on TF–DNA binding across different TF classes and data regimes?

## 04 背景与发展脉络
*注：此脉络基于本文框架及引用文献，部分经外部核验。*

1. **PWM 时代**：PWM 是经典 TF 结合 motif 表示方法，假设各位置独立。代表工具：atSNP、motifbreakR、tRap、FABIAN-variant。优点：简单、可解释；局限：忽略位置间依赖性和侧翼序列影响。
2. **kmer/gkm 机器学习时代**：利用 k-mer 或 gapped k-mer 特征 + SVM/线性模型，代表：deltaSVM（基于 HT-SELEX 或 ChIP-seq 训练）、QBiC-Pred（基于 HT-SELEX 的 OLS 模型）。优点：能捕捉序列依赖性和侧翼效应；局限：特征工程依赖、泛化性有限。
3. **深度学习时代**：CNN 自动学习序列特征，代表：DeepBind、DeepSEA、Beluga、DeepFun、Sei、Enformer。优点：多任务学习、捕捉复杂模式、体内数据表现好；局限：黑箱、数据需求大、体外数据训练时优势不明显。
4. **基准评测演进**：Wagih et al. (2018) 首次系统比较 5 种模型于 ASB 数据；Yan et al. (2021) 用 SNP-SELEX 验证 deltaSVM 优于 ΔPWM；本文（2024）将规模扩展至 14 模型 × 407/380 TFs × 体外/体内双基准，并首次系统分析 TF 属性（DBD 类别、进化保守性）对可预测性的影响。

**本文主张的位置**：目前最大规模的 TF–DNA 结合 SNP 效应预测模型基准评测，首次同时覆盖体外/体内数据、四大类模型、TF 属性分析。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 模型评测规模不足 | 已有评测仅覆盖少量模型和 TF | 数据获取困难、计算成本高 | Introduction 引用 Wagih et al. 仅 5 模型、101 TFs |
| 体外/体内性能脱节 | 体外最优模型（deltaSVM_HT-SELEX）在体内并非最优 | 体内结合受染色质状态、共因子等非序列因素影响 | Results 图 2 vs 图 3 对比 |
| 训练数据与评测数据不匹配 | 用 ChIP-seq 训练的模型在体外评测中表现不佳 | 体内数据包含间接结合和非序列信号，与体外纯序列测定不一致 | Results 图 2D：deltaSVM_HT-SELEX vs deltaSVM_ChIP-seq 比较 |
| TF 类别可预测性差异大 | C2H2 锌指类 TF 预测准确率显著低于 bZIP 类 | C2H2 锌指 motif 多样性高、结合模式复杂、进化上较新 | Results 图 4A、4C |
| 无 motif 信息的 TF 难以预测 | 缺乏已知 motif 的 TF 在体内数据中预测性能差 | 模型依赖 motif 先验知识，无 motif 时无法有效建模 | Results 图 4D |
| 细胞类型特异性未被充分建模 | 多细胞类型训练的模型在特定细胞类型中性能波动大 | 不同细胞类型中 TF 结合谱差异大，通用模型难以捕捉 | Results 图 3F：Sei/Enformer 跨细胞类型 SD 较高 |

## 06 核心思想
1. **表面方法**：收集 14 种已发表的 SNP→TF 结合效应预测模型，统一在 SNP-SELEX（体外）和 ASB（体内）两个大规模数据集上计算 AUROC/AUPRC，进行系统比较；并进一步分析 TF 属性（DBD 类别、进化保守性、表达特异性、互作数、PTM 数）与预测性能的关系。
2. **核心洞察**：
   - 模型性能高度依赖评测数据来源：体外数据上 kmer/gkm 方法最优，体内数据上深度多任务模型最优。不存在"万能模型"。
   - 训练数据与评测数据的匹配性比模型架构更重要：用体外数据训练的模型在体外评测中占优，用体内数据训练的模型在体内评测中占优。
   - TF 的内在属性（DBD 类别、进化年龄）是预测性能的重要决定因素，且这种影响在体外/体内数据中部分一致（bZIP 均好，C2H2 均差）。
3. **可能的普适教训** [Analysis]：对于 TF–DNA 结合预测任务，模型选择应首先考虑目标应用场景（体外 vs 体内），而非盲目追求"最先进"架构；同时，TF 类别差异提示需要开发类别特异的建模策略，而非一刀切的通用模型。

## 07 方法总览
- **输入**：SNP 的参考/替代等位基因序列（40 bp 窗口，SNP 居中）；TF 标识符
- **输出**：每个 SNP-TF 对的结合差异分数（如 deltaSVM score、ΔPWM score、深度学习 log-ratio 等）
- **模型类别**：
  1. PWM-based（4种）：atSNP、motifbreakR、tRap、FABIAN-variant
  2. kmer/gkm-based（3种）：deltaSVM_HT-SELEX、deltaSVM_ChIP-seq、QBiC-Pred
  3. DNN-based（7种）：DeepBind_HT-SELEX、DeepBind_ChIP-seq、DeepSEA、Beluga、DeepFun、Sei、Enformer
- **评测数据**：
  - 体外：SNP-SELEX（407 TFs，~15,000 SNPs，~32,000 阳性 SNP-TF 对）
  - 体内：ASB（380 TFs，>3M SNPs，~100,000 阳性 SNP-TF 对）
- **指标**：AUROC（主指标）、AUPRC、Spearman 相关系数
- **TF 属性分析**：DBD 类别（TFClass）、进化保守性（7 级）、表达特异性/水平、TF-TF/TcoF 互作数、PTM 数
- **流程**：数据收集与清洗 → 统一正负样本定义 → 各模型独立预测 → 按 TF 计算 AUROC → 模型间配对 Wilcoxon 检验 → TF 属性分层分析 → 回归模型校正批次效应

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| SNP-SELEX 数据预处理 | 定义体外结合差异阳性/阴性样本 | 提供体外基准真值 | 输入：原始 SNP-SELEX 数据；输出：正负样本集 | Methods "SNP-SELEX data collection" | 无法进行体外评测 |
| ASB 数据预处理 | 定义体内等位基因特异性结合样本 | 提供体内基准真值 | 输入：ADASTRA v5.1.2；输出：正负样本集 | Methods "ASB data collection" | 无法进行体内评测 |
| 模型预测层 | 14 种模型独立预测 SNP 效应 | 比较不同算法/训练数据组合 | 输入：序列+TF；输出：结合差异分数 | Table 1 | 无法进行模型比较 |
| 性能评估层 | 按 TF 计算 AUROC/AUPRC | 统一度量标准 | 输入：预测分数+标签；输出：各 TF 的 AUROC | Methods "Evaluation metrics" | 无法量化模型优劣 |
| TF 属性注释层 | 关联 TF 的 DBD、保守性、表达等属性 | 解释性能差异来源 | 输入：TF 列表；输出：属性注释 | Methods "Annotations of TFs" | 无法进行 TF 属性分析 |
| 统计分析层 | 配对 Wilcoxon 检验、回归模型 | 确定差异显著性、校正混杂因素 | 输入：AUROC 矩阵+属性；输出：统计检验结果 | Results 图 2-5 | 无法得出可靠结论 |

## 09 关键公式符号
本文主要使用 AUROC/AUPRC 作为评估指标，未引入新的数学模型。核心概念：

- **AUROC**：Area Under the Receiver Operating Characteristic Curve，衡量模型区分正负样本的能力，0.5=随机，1.0=完美。
- **AUPRC**：Area Under the Precision-Recall Curve，对类别不平衡更敏感。
- **ΔES**（ASD 数据）：allelic effect size difference = es_mean_ref − es_mean_alt，用于量化等位基因特异性结合差异。
- **PBS**（SNP-SELEX 数据）：P-value of binding score，衡量等位基因间结合差异的显著性。
- **Spearman 相关系数**：用于评估预测分数与实验测量值之间的单调相关性。

## 10 实验设计与证据链
- **数据集**：
  - SNP-SELEX：407 TFs，~15,000 SNPs（First Batch: 90,035 SNPs/270 TFs；Novel Batch: 66,329 SNPs/487 TFs）
  - ASDASTRA v5.1.2：380 TFs，>3M SNPs，~100,000 阳性 SNP-TF 对
- **指标**：AUROC（主）、AUPRC、Spearman ρ
- **基线**：各模型互为基线，无外部随机基线
- **评测协议**：每个 TF 独立计算 AUROC（≥20 阳性样本），模型间配对 Wilcoxon 检验

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 体外数据模型比较 | kmer/gkm 方法优于 PWM 和 DNN | 14 模型在 SNP-SELEX First Batch 上比较 | deltaSVM_HT-SELEX 中位 AUROC=0.968，QBiC-Pred=0.932，显著高于其他 | 体外数据上 kmer/gkm 方法最优 | 不能说明 kmer/gkm 在体内也最优 | Results 图 2A |
| 体外数据 Novel Batch 验证 | 上述结论的稳健性 | 14 模型在 Novel Batch 上比较 | 性能普遍下降，但 deltaSVM_HT-SELEX 和 QBiC-Pred 仍领先 | kmer/gkm 优势在独立体外数据中可重复 | Novel Batch 中绝对性能有限 | Results 图 2B |
| 体内数据模型比较 | DNN 多任务模型优于其他 | 14 模型在 ASDASTRA 上比较 | DeepSEA、Enformer 中位 AUROC>0.6，PWM 方法接近随机 | 体内数据上 DNN 多任务模型最优 | 不能说明 DNN 在体外也最优 | Results 图 3A |
| 训练数据影响分析 | 训练数据来源决定评测表现 | deltaSVM_HT-SELEX vs deltaSVM_ChIP-seq；DeepBind_HT-SELEX vs DeepBind_ChIP-seq | 体外评测中 HT-SELEX 训练版本更优；体内评测中 ChIP-seq 训练版本更优 | 训练-评测数据匹配性比架构更重要 | 不能排除架构差异的贡献 | Results 图 2D、3D |
| DBD 类别分析 | bZIP 可预测性高，C2H2 低 | 9 个 DBD 类别的 AUROC 比较 | bZIP ΔAUROC=+0.042，Homeodomain=+0.051，Tryptophan cluster=+0.068；C2H2=−0.065，HMG=−0.079，NR-C4=−0.053 | TF 类别显著影响可预测性 | 因果机制未确定 | Results 图 4A、4C |
| 进化保守性分析 | 古老 TF 预测更准 | 7 级保守性比较 | WGD 阶段 TF 显著优于 KRAB 扩张阶段（差=0.114） | 进化保守性与可预测性正相关 | 相关性不等于因果 | Results 图 4B |
| 表达/互作/PTM 分析 | 高表达、少互作、少 PTM 的 TF 预测更准 | 三分位分组比较 | 高表达组 AUROC 更高；互作和 PTM 多的 TF 性能差 | 非序列因素影响体内可预测性 | 样本量有限，需更多验证 | Results 图 5C-F |

## 11 结论正确解读
- **任务范围**：仅评估 SNP 对 TF–DNA 结合的**效应预测**（结合强度变化），不涉及 SNP 对基因表达、表观遗传状态的直接预测。
- **oracle/真值输入**：SNP-SELEX 和 ASDASTRA 数据本身存在实验噪声和偏差；ASDASTRA 为 meta-analysis 结果，可能放大或掩盖某些信号。
- **端到端状态**：所有模型均为"序列→结合分数"的静态预测，未考虑细胞类型特异性动态结合、染色质状态等。
- **算力成本**：未报告各模型训练/推理的具体计算成本，无法评估效率-性能权衡。
- **历史数据依赖**：模型训练数据（如 ENCODE ChIP-seq）与评测数据（ASDASTRA）存在重叠，可能高估体内性能。
- **最难情形**：C2H2 锌指类 TF、缺乏 motif 信息的 TF、位于启动子/CpG 岛的 SNP 是预测难点。
- **群体/领域边界**：主要基于人类 TF 数据；其他物种、非 TF 蛋白的 DNA 结合预测不在范围内。
- **不确定性**：AUROC 差异的效应量普遍较小（中位数差异 0.05-0.1），实际应用中的增益可能有限。

**有边界的复述**：在人类 TF 的 SNP 结合效应预测任务中，不存在跨体外/体内均最优的单一模型；kmer/gkm 方法（deltaSVM_HT-SELEX、QBiC-Pred）适用于体外纯序列效应预测，深度多任务模型（DeepSEA、Sei、Enformer）适用于体内复杂环境预测；TF 的 DBD 类别和进化年龄是预测性能的稳定决定因素。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 评测数据覆盖有限 | 仅覆盖 694 个 TF（约 40% 人类 TF） | 扩展至更多 TF 和细胞类型 | Discussion |
| 体内数据噪声 | ASDASTRA meta-analysis 可能引入偏差 | 使用更高质量、标准化的体内数据 | Discussion |
| 未纳入 base-resolution 模型 | BPNet 等单碱基分辨率模型因 TF 覆盖有限未纳入 | 未来纳入更多新型模型 | Methods "Overview of state-of-the-art models" |
| 非序列因素未建模 | 模型仅基于序列，未整合表观遗传、3D 基因组等 | 开发多模态整合模型 | Discussion |
| 缺乏因果验证 | 预测性能不等于生物学因果性 | 结合 CRISPR 等实验验证 | Discussion |

**作者提及的相关约束**（非正式局限）：模型选择时需考虑计算资源；部分模型仅支持特定基因组版本（hg19 vs hg38），需坐标转换。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 正负样本定义依赖 P-value 阈值 | 不同阈值可能改变模型排名 | 评测结论对阈值敏感则稳健性存疑 | 在不同 P-value 阈值下重复分析 | Methods "Definition of positive and negative samples" |
| 模型选择存在"家族偏差" | 14 模型中 7 个为 DNN，但 DNN 内部差异大 | 可能掩盖 DNN 架构间的显著差异 | 按 DNN 子类型（CNN vs Transformer）分层分析 | Table 1 |
| 训练数据与评测数据重叠 | 部分模型（如 DeepSEA）训练数据含 ENCODE，评测数据 ASDASTRA 也基于 ENCODE | 体内性能可能被高估 | 使用完全独立的体内数据集（如 CUT&Tag）验证 | Discussion 提及 CUT&Tag 但未实施 |
| TF 属性分析为观察性 | DBD 类别与性能的关联可能受其他混杂因素（如 motif 质量）影响 | 因果推断需谨慎 | 控制 motif 信息量后重新分析 | Results 图 4 |
| 未报告置信区间 | 部分统计检验仅报告 P 值，未提供效应量 CI | 无法评估差异的实际意义 | 补充 bootstrap CI | Results 图 2-5 |
| 计算成本未报告 | 不同模型的计算需求差异大 | 实际选型需考虑资源约束 | 补充推理时间、GPU 小时数 | 未提供 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **评测数据选择决定结论**：TF–DNA 结合预测模型的性能排名高度依赖评测数据来源（体外 vs 体内）。本课题中，若目标是解析体内调控机制，应优先选择在体内数据上验证过的模型（如 DeepSEA、Enformer）；若目标是纯序列结合机制研究，kmer/gkm 方法更合适。
2. **训练-评测数据匹配原则**：模型训练数据与目标应用场景的一致性比模型架构选择更重要。本课题开发新模型时，应明确目标场景并选择匹配的训练数据。
3. **TF 类别分层评估**：不同 DBD 类别的 TF 可预测性差异显著（bZIP 好、C2H2 差）。本课题在评估模型或设计实验时，应按 TF 类别分层报告性能，避免"平均性能"掩盖关键差异。
4. **进化保守性作为先验**：进化上古老的 TF（WGD 阶段）预测更准，提示可将其保守性作为模型特征或先验知识。
5. **非序列因素的重要性**：体内预测性能受 TF 表达、互作、PTM 等非序列因素影响。本课题若构建体内结合预测模型，应考虑整合这些特征。
6. **无 motif TF 的挑战**：缺乏已知 motif 的 TF 预测性能差，提示需要开发不依赖 motif 先验的建模策略（如直接从序列学习）。
7. **基准评测方法学**：大规模、多模型、双数据源（体外+体内）的评测框架可迁移至其他 TF–DNA 结合预测任务（如预测 TF 结合位点、解析结合机制）。

## 15 与已有知识连接
- **Wagih et al. (2018)**：本文扩展了其 5 模型 × 101 TFs 的 ASDASTRA 评测至 14 模型 × 380 TFs，结论一致（深度学习方法优于 PWM），但进一步发现 kmer/gkm 在体外数据上更优。
- **Yan et al. (2021)**：本文验证了其 deltaSVM 优于 ΔPWM 的结论，并扩展至更多模型和 TF。
- **DeepSEA/Enformer 系列**：本文确认了这些模型在体内数据上的优势，但指出其在体外数据上并非最优，挑战了"深度学习=最佳"的普遍认知。
- **TF 类别与可预测性**：与 Zhou & Troyanskaya (2015) 关于 TF motif 复杂性的观察一致，C2H2 锌指因 motif 多样性高而难以预测。
- **本课题方向**：本文为 TF–DNA 结合机制研究提供了"模型-数据-场景"匹配的实用指南；其 TF 属性分析框架可迁移至物理模拟（MD）中，用于选择可模拟的 TF 体系。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF 类别感知的混合预测模型
   - **来源局限/观察**：本文发现不同 TF 类别（bZIP vs C2H2）可预测性差异大，单一模型难以兼顾。
   - **核心假设**：将 TF 的 DBD 类别作为条件输入，训练类别条件化的深度学习模型，可提升整体预测性能。
   - **初步方法**：在现有 CNN 架构（如 DeepSEA）中加入 DBD 类别 embedding 作为辅助输入；或在损失函数中加入类别感知的权重。
   - **验证方式**：在本文公开的 SNP-SELEX 和 ASDASTRA 基准上比较类别条件模型与通用模型的 AUROC。
   - **创新状态**：unverified

2. **候选名称**：体外-体内迁移学习框架
   - **来源局限/观察**：体外和体内数据性能脱节，但两者存在正相关（Supplementary Figure S4C）。
   - **核心假设**：利用体外数据（大规模、低噪声）预训练，再用体内数据（小规模、高噪声）微调，可兼顾两者优势。
   - **初步方法**：先在 SNP-SELEX 数据上预训练 CNN，再在 ASDASTRA 数据上微调；比较与直接训练的性能差异。
   - **验证方式**：在本文基准上比较迁移学习 vs 直接训练的 AUROC，并分析不同微调策略（全量微调 vs 冻结底层）。
   - **创新状态**：unverified

3. **候选名称**：进化保守性引导的 TF 结合预测
   - **来源局限/观察**：进化上古老的 TF 预测更准，提示保守性包含有用先验。
   - **核心假设**：将 TF 的进化保守性分数作为特征或正则化项，可提升低保守性 TF 的预测性能。
   - **初步方法**：从 TF 家族系统发育树提取保守性分数，作为辅助特征输入模型；或对低保守性 TF 使用更强的正则化。
   - **验证方式**：在本文基准上按保守性分层比较 AUROC，检验是否缩小了高/低保守性 TF 的性能差距。
   - **创新状态**：unverified

4. **候选名称**：非序列特征增强的体内结合预测
   - **来源局限/观察**：体内预测性能受 TF 表达、互作、PTM 等非序列因素影响。
   - **核心假设**：将 TF 表达水平、互作网络、PTM 状态等特征与序列特征融合，可提升体内 SNP 效应预测。
   - **初步方法**：构建多模态模型，序列分支（CNN）+ 属性分支（MLP），在 ASDASTRA 上训练。
   - **验证方式**：与纯序列模型比较 AUROC，并做消融实验分析各非序列特征的贡献。
   - **创新状态**：unverified

5. **候选名称**：无 motif TF 的 de novo 结合预测
   - **来源局限/观察**：缺乏已知 motif 的 TF 预测性能差，是当前模型的主要短板。
   - **核心假设**：利用蛋白质结构预测（如 AlphaFold）或 DBD 序列相似性，为无 motif TF 生成伪 motif 或结构先验。
   - **初步方法**：对无 motif TF，用 AlphaFold 预测 DBD 结构，与 DNA 做对接模拟生成候选结合模式，再输入预测模型。
   - **验证方式**：在本文基准中筛选无 motif TF 子集，比较结构先验增强 vs 纯序列模型的 AUROC。
   - **创新状态**：unverified

6. **候选名称**：物理模拟与机器学习融合的 SNP 效应预测
   - **来源局限/观察**：本文模型均为纯序列方法，未利用物理化学信息；MD/对接模拟可提供结合自由能变化。
   - **核心假设**：将 MD 模拟计算的结合自由能变化（ΔΔG）作为特征或约束，可提升 SNP 效应预测精度，尤其对机制性理解。
   - **初步方法**：对 SNP 所在位点做短时 MD 模拟，提取 ΔΔG 和构象变化特征，与序列特征融合训练。
   - **验证方式**：在本文基准的子集（如 50 个 TF）上比较融合物理特征 vs 纯序列模型的 AUROC，并分析物理特征对错误预测的修正能力。
   - **创新状态**：unverified