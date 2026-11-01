## 01 基本信息
- 标题：Cross-task benchmarking reveals variable transferability of deep learning models across molecular quantitative trait loci
- 作者与单位：Chen, Sihan; Wang, Xiaoyu; Peleg, Anton Y; Xu, Shuting; Li, Fuyi; Webb, Geoffrey I; Song, Jiangning（具体单位未在提供材料中列出；通讯与监督为 J.S., G.W., F.L.）
- 期刊/预印本平台：Briefings in Bioinformatics
- 年份：2026-10-30（按提供日期）
- 论文类型：基准评测 / 方法比较研究（benchmarking），含下游疾病变异优先级应用
- 领域：基因组学 × 深度学习；非编码变异功能解读；xQTL 预测
- 关键词：未提供（摘要与正文未列关键词列表）
- DOI/arXiv 号：10.1093/bib/bbag599
- 代码：https://github.com/SihanChen-bioinfo/xQTL-ModelBenchmarking
- 数据：GTEx v10 与既往发表数据集（apaQTL、bQTL、caQTL、clQTL、eQTL、hQTL、miQTL、pQTL、sQTL）；1000 Genomes Project 作为负对照来源；GWAS Catalog CAD-SNPs（2492 个，MONDO_0005090）
- 阅读日期：未提供
- 在「蛋白质–DNA 互作(聚焦 TF–DNA 结合机制) × AI/物理模拟」方向中的位置：本文不直接研究 TF–DNA 结合的结构/物理机制，也不使用 MD/对接/结构预测；但其评测对象之一为 bQTL（transcription factor binding QTL），且核心议题是「预训练调控序列表征能否跨分子表型迁移」。对本课题的可迁移价值在于：(1) 提供 TF 结合相关变异（bQTL）在序列模型下的可预测性证据与难度分层；(2) 提供「长程上下文 vs 局部序列」的表征能力对比结论，可类比到 TF 结合位点预测与 TF–DNA 亲和力建模；(3) 提供类别不平衡、下游分类器选择、负对照构造等评测协议，可直接迁移到 TF–DNA 结合预测的基准设计。

## 02 一句话总结
该研究用统一的预处理与评测流程，把六个代表性调控变异预测模型（GWAVA、DeepSEA、ExPecto、Enformer、Borzoi、AlphaGenome）的预训练特征接到 XGBoost 等分类器上，在九类 xQTL 上做跨任务评测，发现 eQTL 上普遍表现良好但跨表型迁移性差异很大（caQTL/bQTL/hQTL 易预测，clQTL/miQTL 难），长程表征的基础模型（AlphaGenome、Borzoi）更稳健，并据此在 CAD GWAS 位点上给出 337 个共识候选 caQTL。

## 03 研究问题
- 具体问题：以 eQTL 为中心训练/设计的深度学习调控变异预测模型，其预训练调控特征能否迁移到其他分子表型（xQTL）？迁移性由什么因素决定？
- 为什么重要：>90% 复杂性状相关变异位于非编码区，实验鉴定 xQTL 成本高、依赖组织/细胞类型与大队列；若模型只能预测 eQTL，则无法系统解读非编码变异的调控机制。
- 现有方法为何不足：早期方法（GWAVA）依赖人工注释、受注释可得性限制且不直接从序列学习；序列模型（DeepSEA、ExPecto）多限于短序列上下文，难以捕捉长程调控互作；计算工作过度集中于 eQTL，对其他调控表型泛化性有限。
- 精确研究问题（Can ... ?）：Can pretrained regulatory features from eQTL-centric sequence- and annotation-based models transfer across diverse xQTL classes, and which model/representation properties predict successful transfer?（依据 Introduction 与 Abstract 归纳）

## 04 背景与发展脉络
（该脉络为「仅本文框架」，即按本文 Introduction 的叙述整理；未做外部文献核验）
- 阶段 1：注释驱动方法。代表：GWAVA。优点：利用 curated functional annotations，生物学信息直接。局限：受注释可得性约束，不直接从 DNA 序列学习，难捕捉上下文依赖与长程效应。
- 阶段 2：短上下文序列模型。代表：DeepSEA、ExPecto。优点：直接从原始 DNA 序列学习多种调控活性，便于 eQTL 解读。局限：多限于短序列上下文，难捕捉长程调控互作。
- 阶段 3：基因组基础模型（长程上下文）。代表：Enformer、Borzoi、AlphaGenome。优点：自监督建模长程依赖，统一框架同时捕捉局部序列决定因素与远端调控互作。局限（本文指出）：计算与模型规模成本高、依赖大规模预训练数据；且本文未纳入 Caduceus、HyenaDNA、Nucleotide Transformer 等另一类基因组语言模型范式。
- 本文主张的位置：不做新模型，而是做跨任务基准，主张「迁移性存在显著差异」，并把长程表征与下游非线性分类器视为提升迁移性的关键因素。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 非编码变异功能难解读 | >90% 复杂性状相关变异位于非编码区，远离蛋白编码序列 | 传统基于蛋白的注释策略不适用 | Introduction |
| xQTL 实验鉴定成本高 | 需大队列、组织/细胞类型特异分子谱、大规模高通量功能实验 | 成本高、劳动密集；调控效应高度依赖上下文 | Introduction |
| 计算工作过度偏向 eQTL | 对其他调控表型泛化性有限 | 领域关注点集中于 eQTL | Introduction |
| 短上下文模型能力受限 | 难捕捉长程调控互作 | 模型仅建模短序列上下文 | Introduction |
| 跨表型迁移性未知 | 各模型在非 eQTL 表型上表现差异大 | 作者解释：不同分子表型与当前染色质特征的「直接相关程度」不同；预训练数据组织/细胞类型匹配度不同 | Results「Cross-xQTL prediction performance」；Discussion |
| 类别不平衡下指标虚高 | AUROC 相对稳定，但 AUPRC/F1/MCC 随负对照比例升高显著下降 | 功能变异在真实基因组中稀疏 | Results「Factors influencing cross-xQTL prediction performance」图 5 |
| 特征维度差异可能混淆比较 | 六个模型产生的调控表征维度不同 | 作者承认：为保留各模型原意表征而未统一维度 | Discussion（作者自述为 potential confounding factor） |

## 06 核心思想
1) 表面方法：固定一套统一预处理与评测流程（染色体划分训练/测试、统一负对照采样、统一分类器与阈值），把六个已有模型的变异级染色质特征抽出，训练 XGBoost/RF/线性分类器，在九类 xQTL 上横向比较 AUROC/AUPRC/F1/MCC/Brier，并做特征重要性组织富集与不平衡敏感性分析。
2) 核心洞察：模型迁移性不是「有/无」，而是随分子表型呈梯度——与染色质活性直接相关的表型（caQTL、bQTL、hQTL）易从现有表征中学到，而高阶/转录后表型（clQTL、miQTL）难；长程上下文表征比局部序列表征更稳健，且调控特征间存在显著非线性交互（线性分类器接近随机）。
3) 可能的普适教训 [Analysis]：在调控基因组学中，「预训练目标与下游表型的表征对齐程度」可能比模型规模更能预测迁移成功；评测时应同时报告阈值无关（AUROC/AUPRC）与阈值相关（F1/MCC）指标，因为不平衡会系统性夸大前者。

## 07 方法总览
- 输入：各 xQTL 数据集的正样本变异（显著 xQTL）与负对照变异（1000 Genomes 随机采样，1:10 为主，另有 1:5、1:1；并构造严格匹配负对照：距 xQTL ≥500 kb、排除已知 xQTL、匹配 MAF 差 <0.05 与基因组上下文注释）；MAF ≥0.01 保留。
- 输出：每个模型在每个 xQTL 上的变异级预测概率与二分类；性能指标；特征重要性排序与组织富集；CAD 候选 caQTL 列表。
- 模块：数据收集与处理 → 六个模型特征提取（GWAVA、DeepSEA、ExPecto、Enformer、Borzoi、AlphaGenome）→ 下游分类器训练（XGBoost 为主，RF/L1/Enet 对照）→ 评测（AUROC/AUPRC/F1/MCC/Brier、MAF 分布、效应量相关）→ 特征重要性 + 组织注释 + 置换检验/FDR → CAD 应用（共识预测 + 富集 + 等位特异 DNase-seq 差异）。
- 训练：染色体划分训练/测试（测试约 20% 变异）；训练集内 5 折交叉验证做超参优化；固定随机种子 seed=0（另做 seed=42、68 稳健性）。
- 工具：XGBoost、Random Forest、L1、Elastic Net；g:Profiler；GENCODE v38 (Ensembl release 104)。
- 反馈回路：无显式迭代反馈回路（非端到端训练，特征固定）。
- 假设：各模型输出的变异级染色质特征可作为可比的调控表征；统一分类器与阈值可保证公平比较；负对照采样策略不主导结论（由敏感性分析检验）。
- 文字流程：收集九类 xQTL 与负对照 → 按染色体划分 → 对每个模型抽取变异级特征 → 训练 XGBoost（含超参搜索）→ 在独立测试染色体上计算指标 → 特征重要性映射到组织并做置换检验 → 用表现最好的 AlphaGenome/Borzoi 对 CAD-SNPs 打分并取共识 → 富集分析与等位特异 DNase-seq 验证。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 统一预处理与评测流程 | 保证跨模型公平比较 | 各模型架构与特征表示不同 | 输入：xQTL 变异集；输出：统一训练/测试划分与指标 | Fig. 1；Materials and methods「Framework for cross-xQTL prediction」 | 预期：比较不可比（未实测消融） |
| 六个模型特征提取 | 提供变异级调控表征 | 评测对象 | 输入：DNA 序列/注释；输出：变异级染色质特征 | Table S2（统计摘要，正文引用） | 预期：无特征则无法评测 |
| 下游分类器（XGBoost 为主） | 将特征映射为 xQTL 概率 | 特征本身非分类器 | 输入：特征；输出：概率与二分类 | Fig. 4、Fig. S8、Table S6 | 实测消融效应：线性模型（L1/Enet）在多个 xQTL 上 AUROC 接近 0.5、MCC 接近 0，尤其对 DeepSEA/ExPecto/Enformer 特征；RF 略低于 XGBoost 但 Brier 更优（除 eQTL、pQTL） |
| 负对照采样（1:10/1:5/1:1 + 严格匹配集） | 构造二分类任务并检验不平衡影响 | 真实功能变异稀疏 | 输入：1000 Genomes；输出：负对照集 | Fig. 5、Fig. S7、Fig. S9、Table S7 | 实测：AUPRC 随负对照比例升高显著下降，AUROC 相对稳定；严格匹配负对照下主要趋势复现 |
| 特征重要性 + 组织富集 | 解释模型依赖何种信号 | 连接表征与表型可预测性 | 输入：XGBoost gain；输出：top 10% 特征的组织富集与经验 P 值/FDR | Fig. 2D/E、Fig. S1/S2/S5/S6；Materials and methods「Analysis of feature importance」 | 预期：失去机制解释力（未做移除消融） |
| CAD 共识优先级 | 展示下游应用价值 | 验证模型实用性与生物学相关性 | 输入：2492 CAD-SNPs；输出：337 个共识候选 caQTL | Fig. 6、Fig. S10–S12 | 预期：无共识策略则候选数更多、假阳性风险更高（未做消融） |

## 09 关键公式符号
- F1 与 MCC：正文给出定义式（Materials and methods「Model performance evaluation」），其中 TP、TN、FP、FN 分别为真阳性、真阴性、假阳性、假阴性。用途：阈值相关二分类性能（阈值固定 0.5）。直觉：MCC 在类别不平衡下比 F1 更能反映整体一致性。
- Brier score：$BS = \frac{1}{N}\sum_{i}(f_i - y_i)^2$，其中 $f_i$ 为变异 $i$ 的预测概率，$y_i \in \{0,1\}$ 为真实标签，$N$ 为变异数。用途：衡量概率校准质量，越低越好。来源指针：Materials and methods「Model performance evaluation」。
- Pearson 相关系数（PCC）：用于效应量与预测概率的相关（Results 图 2F、图 3B/C），以及 AlphaGenome 与 Borzoi 打分一致性（Fig. S10，PCC=0.807，Spearman=0.746）。具体公式未在提供材料中展开。
- Cohen's κ：用于两模型二分类一致性（κ=0.6673），公式未在提供材料中展开。
- 注：F1 与 MCC 的完整展开式在提供的文本中被公式排版截断，未提供可核验的完整表达式。

## 10 实验设计与证据链
数据集/群体与规模：
- eQTL：14,811 个 whole-blood eQTL（GTEx v10）。
- 九类 xQTL：apaQTL（whole blood）、bQTL（HCASMC）、caQTL（HCASMC）、clQTL（HCASMC）、eQTL（whole blood）、hQTL（LCL）、miQTL（whole blood）、pQTL（whole blood）、sQTL（whole blood）。
- 负对照：1:10 为主，另 1:5、1:1；严格匹配集（≥500 kb、排除已知 xQTL、MAF 差 <0.05、上下文注释匹配）。
- CAD-SNPs：2492 个（GWAS Catalog，MONDO_0005090）。
- 指标：AUROC、AUPRC、F1、MCC、Brier；MAF 分布一致性；效应量–概率 PCC。
- 基线：六个模型互为基线；分类器层面 XGBoost vs RF vs L1 vs Enet。
- 预算/骨干/仪器：未提供（无计算预算、GPU 时长等报告）。
- oracle 输入：无 oracle 输入；标签来自实验鉴定的 xQTL。
- 评测协议：染色体划分，测试约 20% 变异；训练集内 5 折交叉验证调参；固定阈值 0.5（另做 MCC 最优阈值敏感性）；固定 seed=0（另做 42、68）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| eQTL 预测 | 各模型在 eQTL 上的基本能力 | 六模型，1:10 不平衡 | AlphaGenome 最佳（AUROC=0.810, AUPRC=0.389, F1=0.343, MCC=0.292）；Borzoi 0.804、Enformer 0.799；GWAVA 0.775；ExPecto 0.724；DeepSEA 0.688 | 基础模型在 eQTL 上领先 | 不能说明其在所有表型上领先 | Fig. 2、Table 1 |
| 跨 xQTL 预测 | 迁移性是否因表型而异 | 九类 xQTL × 六模型 | caQTL/bQTL/hQTL 高（caQTL AlphaGenome AUROC=0.954, AUPRC=0.757）；clQTL/miQTL 低（一般 AUROC<0.71，MCC 低）；apaQTL/pQTL/sQTL 居中（pQTL Borzoi AUROC=0.794, AUPRC=0.442） | 存在跨表型可预测性梯度 | 不能说明低表现表型不可预测，只说明当前特征不足 | Fig. 3、Fig. S3、Table 1 |
| 分类器选择 | 下游分类器是否影响性能 | XGBoost vs RF vs L1 vs Enet | XGBoost 最佳（caQTL AUROC=0.894–0.954, AUPRC=0.652–0.757）；RF 略低（0.887–0.946 / 0.598–0.733）；线性模型常接近随机 | 调控特征含强非线性交互 | 不能说明线性模型在所有特征上都无效 | Fig. 4、Fig. S8、Table S6 |
| 类别不平衡 | 不平衡如何影响指标 | 1:1、1:5、1:10 | AUROC 相对稳定；AUPRC 显著下降（AlphaGenome caQTL AUPRC 从 0.954@1:1 降至 0.757@1:10，AUROC 仍 >0.95） | AUROC 可能高估真实效用 | 不能说明模型排序能力丧失 | Fig. 5、Fig. S9、Table S7 |
| 负对照敏感性 | 结论是否依赖负对照构造 | 严格匹配负对照 | 主要趋势复现（caQTL 高、clQTL/miQTL 低） | 结论对负对照选择稳健 | 不能排除其他未测混杂 | Fig. S7 |
| 随机种子 | 结论是否依赖初始化 | seed=0/42/68 | AUROC SD 0.00012–0.00735；AUPRC SD 0.00004–0.01106 | 对随机初始化稳健 | 不涉及模型权重随机性（特征固定） | Table S3 |
| 染色体划分 | 结论是否依赖测试染色体 | 统一测试染色体 2、12、14、19、21 | 与原始划分基本一致，仅微小差异 | 对染色体组成稳健 | 未覆盖全部染色体组合 | Table S4 |
| 阈值选择 | 固定阈值是否影响结论 | 固定 0.5 vs 训练集 MCC 最优阈值 | F1/MCC 变化，AUROC/AUPRC 基本不变，总体模式一致 | 阈值相关指标需谨慎解读 | 不改变排序结论 | Table S5 |
| CAD 应用 | 模型能否优先级化疾病变异 | AlphaGenome + Borzoi 共识 | Borzoi 503、AlphaGenome 422 候选；共识 337（11 已报道 + 326 新）；PCC=0.807、Spearman=0.746、一致率 89.92%、κ=0.6673；214 基因富集于胆固醇代谢（FDR=5.32×10⁻⁹）、动脉粥样硬化（FDR=8.57×10⁻⁹）等；共识候选等位特异 DNase-seq 差异显著大于非 caQTL | 基础模型可用于疾病变异优先级化 | 不能建立因果性（作者明确需 fine-mapping/colocalization/正交实验） | Fig. 6、Fig. S10–S12 |

## 11 结论正确解读
- 任务范围：本文是「跨任务基准评测」，不是新模型；结论边界限于所评测的六模型、九类 xQTL、所采用的负对照与分类器。
- oracle/真值输入：无 oracle 输入；标签为实验鉴定的 xQTL，因此性能上限受标签质量与覆盖度限制。
- 端到端状态：非端到端——模型特征固定，仅下游分类器训练；因此结论反映「表征 + 分类器」联合表现，不能单独归因于模型架构。
- 算力成本：未报告；作者在 Discussion 中仅定性指出基础模型受模型规模、计算需求与预训练数据依赖约束。
- 历史数据依赖：依赖 GTEx v10 与既往发表数据集；组织/细胞类型覆盖有限（如 bQTL/caQTL/clQTL 来自 HCASMC，hQTL 来自 LCL）。
- 模型依赖：结论依赖六个特定模型；作者明确未纳入 Caduceus、HyenaDNA、Nucleotide Transformer 等基因组语言模型范式。
- 最难情形：clQTL 与 miQTL（AUROC 一般 <0.71，MCC 低）；高类别不平衡下的 AUPRC/F1/MCC。
- 群体/领域边界：CAD 应用基于 GWAS Catalog 的 CAD-SNPs，富集结果支持心血管/脂质相关过程，但作者明确因果性未建立。
- 不确定性：特征维度差异被作者列为潜在混杂；预训练数据与目标组织匹配度的影响为定性推断。
- 有边界的复述：在本文评测的六模型与九类 xQTL 范围内，跨表型迁移性差异显著，长程表征的基础模型在多数表型与不平衡条件下更稳健，但 clQTL/miQTL 仍难预测，CAD 候选仅为优先级化假设而非因果结论。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 特征维度差异可能混淆比较 | 六个模型产生的调控表征维度不同，且为保留原意未统一 | 未明确给出具体方案，仅作为潜在混杂因素提出 | Discussion |
| 未纳入新兴基因组语言模型 | Caduceus、HyenaDNA、Nucleotide Transformer 未评测，属不同建模范式 | Future extensions should incorporate these emerging models | Discussion |
| 基础模型计算成本 | 模型规模、计算需求、对大规模预训练数据的依赖可能限制实际应用 | 选型时需考虑计算需求 | Discussion |
| CAD 候选因果性未建立 | 共识预测仅为候选 | 需 fine-mapping、colocalization 或正交功能实验 | Results「Identification of novel CAD-associated caQTLs」 |

作者提及的相关约束（非正式局限）：预训练数据与目标组织/细胞类型的匹配度可能影响性能（Discussion 引用既往研究 [43]）；模型架构与训练目标差异、预训练数据集差异也可能贡献于观察到的性能差异（Discussion）。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 特征维度未统一，可能使「基础模型更优」部分来自维度优势 | 高维特征给树模型更多分裂机会，未必反映表征质量 | 直接影响「长程表征更可迁移」这一核心结论的归因 | 对特征做统一降维（如 PCA 到相同维度）或维度匹配的对照实验 | Discussion 作者自述；Table S2 |
| 下游分类器固定为 XGBoost 为主，模型比较实为「表征+分类器」联合比较 | 不同表征可能适配不同分类器，最优组合可能改变排名 | 影响模型选型建议的普适性 | 对每个模型做分类器网格搜索并报告各自最优 | Fig. 4、Fig. S8、Table S6 |
| 负对照为随机采样（主分析），可能引入基因组上下文混杂 | 严格匹配集虽复现趋势，但主分析结论仍可能受上下文分布影响 | 影响 AUROC/AUPRC 的绝对水平与跨表型可比性 | 全面采用严格匹配负对照重跑主分析并比较排名 | Fig. S7；Materials and methods |
| 组织/细胞类型不匹配（如 hQTL 来自 LCL，bQTL/caQTL/clQTL 来自 HCASMC） | 性能差异可能部分来自预训练数据与目标组织的匹配度，而非表型本身的可学习性 | 影响「表型难度梯度」的机制解释 | 在同一组织/细胞类型内构造多类 xQTL 做对照 | Discussion；Materials and methods |
| 效应量–概率正相关被解读为「捕捉生物学定量信息」 | 也可能反映效应量大的变异更易被任何特征区分（如更靠近调控元件） | 影响对模型输出语义的解读 | 控制基因组上下文/注释后做偏相关分析 | Fig. 2F、Fig. 3B/C |
| CAD 共识策略提高精度但可能降低召回 | 两模型共享相似预训练偏差，共识可能系统性遗漏某类真 caQTL | 影响候选列表的完整性 | 引入第三类正交证据（如 MPRA、fine-mapping）评估遗漏 | Fig. 6B、Fig. S10 |
| 固定阈值 0.5 在不平衡下不最优 | 虽做了 MCC 最优阈值敏感性，但主分析仍用 0.5 | 影响 F1/MCC 的绝对解读 | 主分析即采用训练集调优阈值 | Table S5 |

## 14 学到什么
### Agent 提炼的知识候选
- 可迁移概念 1：跨任务迁移性梯度。与染色质活性直接相关的表型（caQTL、bQTL、hQTL）比高阶/转录后表型（clQTL、miQTL）更易从现有序列表征中学到。迁移到本课题：TF–DNA 结合（bQTL）属于「易预测」端，说明现有序列模型已能较好捕捉 TF 结合的序列决定因素；但 TF 结合的细胞类型特异性与协同结合可能仍未被充分表征，可作为改进方向。
- 可迁移概念 2：长程上下文 vs 局部序列。长程表征模型（Enformer/Borzoi/AlphaGenome）在跨表型与不平衡下更稳健。迁移到本课题：TF 结合常涉及远端增强子–启动子互作与染色质环化，提示 TF–DNA 结合建模应显式引入长程上下文（如 Hi-C/染色质环特征或长窗口序列模型）。
- 可迁移方法 1：统一评测协议。染色体划分 + 固定负对照采样 + 多指标（AUROC/AUPRC/F1/MCC/Brier）+ 多随机种子 + 多阈值敏感性。迁移到本课题：可直接用于 TF 结合位点预测或 TF–DNA 亲和力模型的基准设计，尤其应报告不平衡下的 AUPRC。
- 可迁移方法 2：严格匹配负对照。距正样本 ≥500 kb、排除已知位点、匹配 MAF 与基因组上下文注释。迁移到本课题：TF 结合预测的负对照常为随机序列或 shuffled 序列，可能高估性能；建议采用匹配 GC 含量、染色质状态、可及性的负对照。
- 可迁移方法 3：特征重要性 + 组织富集 + 置换检验/FDR。迁移到本课题：可用于检验 TF 结合模型是否真正依赖 TF motif 或染色质可及性信号，而非伪特征。
- 可迁移方法 4：共识优先级化。两模型打分相关（PCC=0.807）且一致率 89.92% 时取交集。迁移到本课题：可用于整合结构预测（如 AlphaFold3 类核酸–蛋白复合物预测）与序列模型（如 Borzoi）的 TF 结合候选。
- 可迁移实验设计：类别不平衡梯度（1:1/1:5/1:10）作为标准敏感性分析。迁移到本课题：TF 结合位点在基因组中同样稀疏，应报告不平衡梯度下的性能。
- 可迁移公式/指标：Brier score 用于概率校准；MCC 用于不平衡下的二分类；PCC 用于效应量–概率一致性。迁移到本课题：TF–DNA 结合亲和力预测可同时报告校准与排序指标。

## 15 与已有知识连接
- 相似工作（本文引用）：Enformer [21]、Borzoi [20]、AlphaGenome [25] 在 eQTL 预测上的优势与既往工作一致（Discussion 明确「Consistent with prior work」）。
- 组合方向：本文的「长程表征 + 非线性分类器」组合，可与本课题的物理模拟（MD/对接）或结构预测（TF–DNA 复合物）组合，形成「序列表征 + 结构/能量特征」的混合模型（[Analysis] 候选方向，未在本文中验证）。
- 冲突/张力：GWAVA 仅用人工注释却在多个 xQTL 上优于 DeepSEA 和 ExPecto（Results、Discussion），提示「生物学先验注释」在数据有限时仍具竞争力，与「端到端序列学习必然更优」的直觉存在张力。
- 可迁移领域：基因组语言模型（Caduceus、HyenaDNA、Nucleotide Transformer）被作者列为未评测的替代范式（Discussion），可作为本课题在 TF–DNA 结合建模上的候选骨干。
- 外部可核验文献（本文引用编号，具体内容未在提供材料中展开）：[1] GTEx、[17] GWAVA、[18] DeepSEA、[19] ExPecto、[20] Borzoi、[21] Enformer、[23] Nucleotide Transformer、[25] AlphaGenome、[30] HCASMC bQTL/caQTL/clQTL 来源、[31] hQTL、[32] miQTL、[33] pQTL、[34] 1000 Genomes、[35] g:Profiler、[36] GENCODE v38、[43] 组织匹配度相关研究、[44] Caduceus、[45] HyenaDNA。
- 用户已有知识连接：若用户熟悉 TF–DNA 结合的 motif 建模或 MD 自由能计算，本文提供的「跨表型迁移性梯度」与「不平衡下 AUPRC 下降」可直接作为评测设计的对照基线。

## 16 研究想法
### Agent 生成的研究候选
1. 名称：TF–DNA 结合预测的跨任务迁移性基准（TF-xQTL-Bench）
   - 来源局限/观察：本文发现 bQTL 属易预测端，但未细分 TF 家族、未区分直接/间接结合、未纳入结构信息。
   - 核心假设：TF 结合的可预测性在 TF 家族间差异显著，且与 TF 的 DNA 结合结构域类型（如 zinc finger、bHLH、homeodomain）相关。
   - 相对本文的增量：把 bQTL 从单一类别细分为 TF 家族/结构域层级，并加入结构预测或 MD 衍生特征。
   - 初步方法：用本文统一流程，在 bQTL 上按 TF 家族分层评测六个模型；加入 AlphaFold3 类 TF–DNA 复合物预测特征。
   - 验证方式：分层 AUROC/AUPRC 比较；与 motif 注释富集对照。
   - 可能的失败模式：bQTL 数据量不足以支撑家族分层；结构预测特征与序列特征高度共线。
   - 创新状态：unverified。
2. 名称：长程上下文对 TF 结合预测的增益消融
   - 来源局限/观察：本文显示长程模型更稳健，但未做「上下文长度」的受控消融。
   - 核心假设：TF 结合预测的增益主要来自远端增强子–启动子互作信息，而非单纯更大感受野。
   - 相对本文的增量：在固定模型架构下系统改变输入窗口长度，并加入染色质环（clQTL 类）特征。
   - 初步方法：对 Borzoi/Enformer 类模型做窗口长度梯度实验；用 clQTL 特征作为附加输入。
   - 验证方式：窗口长度 vs 性能曲线；加入/移除 clQTL 特征的消融。
   - 可能的失败模式：窗口长度与计算成本耦合，难以分离；clQTL 本身预测性能低（本文 AUROC<0.71），可能无增益。
   - 创新状态：unverified。
3. 名称：匹配负对照下的 TF 结合预测性能重估
   - 来源局限/观察：本文主分析用随机负对照，严格匹配集仅作敏感性分析；TF 结合预测领域常用 shuffled 序列。
   - 核心假设：采用匹配染色质状态与 GC 含量的负对照后，TF 结合预测性能会显著下降，且模型排名可能改变。
   - 相对本文的增量：把严格匹配负对照提升为主分析，并扩展到 TF 结合任务。
   - 初步方法：构造匹配可及性（DNase）、组蛋白修饰、GC 的负对照，重跑本文流程。
   - 验证方式：与随机负对照结果对比；报告 AUPRC 下降幅度与排名变化。
   - 可能的失败模式：匹配过严导致正负样本几乎不可分，性能趋近随机，失去区分度。
   - 创新状态：partially checked（本文 Fig. S7 已做类似敏感性分析，但未针对 TF 结合细分）。
4. 名称：序列模型 + 物理模拟的 TF–DNA 结合混合打分
   - 来源局限/观察：本文纯序列/注释模型，未涉及物理模拟；本课题关注 MD/对接/结构预测。
   - 核心假设：序列模型捕捉上下文依赖，MD/对接捕捉结合自由能与构象变化，二者互补可提升变异效应预测。
   - 相对本文的增量：在本文评测框架上增加物理模拟衍生特征（如结合自由能变化 ΔΔG、氢键数变化）。
   - 初步方法：对 bQTL 变异做 TF–DNA 复合物结构建模与短程 MD，提取能量特征，与 Borzoi/AlphaGenome 特征拼接训练 XGBoost。
   - 验证方式：与纯序列特征基线比较 AUPRC/MCC；做特征重要性分析。
   - 可能的失败模式：MD 通量不足以覆盖大量变异；结构预测对非编码变异不敏感；计算成本过高。
   - 创新状态：unverified。
5. 名称：不平衡感知的 TF 结合变异优先级化阈值策略
   - 来源局限/观察：本文显示固定阈值 0.5 在不平衡下不优，AUPRC 随负对照比例下降。
   - 核心假设：在真实基因组稀疏场景下，基于训练集 MCC 或 F1 最优阈值 + 校准（如 isotonic/Platt）可提升 TF 结合变异优先级化的实用性。
   - 相对本文的增量：把阈值优化与概率校准作为主分析，而非敏感性分析。
   - 初步方法：在 bQTL 上比较固定阈值、MCC 最优阈值、校准后阈值；报告 precision@k。
   - 验证方式：precision@k、召回@固定精度；与本文 Table S5 类似但针对 TF 结合。
   - 可能的失败模式：校准在小数据集上过拟合；precision@k 对 k 选择敏感。
   - 创新状态：partially checked（本文 Table S5 已做阈值敏感性，但未做校准与 precision@k）。