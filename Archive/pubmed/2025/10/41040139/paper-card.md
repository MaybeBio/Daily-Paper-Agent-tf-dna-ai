## 01 基本信息
- **标题**：The nascent transcriptome delineates the regulatory landscape in human health and disease
- **作者**：Shah, Sagar R; Chen, You; Leung, Alden K; Navarro, Priscila V Castilho; Paramo, Mauricio I; Gupta, Juhi; Gurumurthy, Aishwarya; Fite, Rebuma F; Weimer, Annika K; Cochran, Anna; Wang, Austin; Du, Qian; Mohyeldin, Ahmed M; Egli, Dieter; Kundaje, Anshul; Creusot, Remi J; Ryan, Russell J H; Snyder, Michael P; Clark, Andrew G; Lis, John T; Yu, Haiyuan
- **单位**：Cornell University（Yu、Lis、Clark 等实验室）；Stanford University（Snyder）；Columbia University（Egli）等（部分作者单位未在摘要中列出，以原文为准）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2025
- **论文类型**：预印本（研究论文）
- **领域**：基因组学、转录调控、调控基因组学
- **关键词**：nascent transcriptome, PRO-cap, transcriptional regulatory elements (TREs), enhancer, promoter, transcription initiation, GWAS, eQTL, deep learning, ProCapNet
- **DOI/arXiv 号**：10.1101/2025.09.24.676871
- **代码**：https://github.com/haiyuan-yu-lab/TRE_landscape
- **数据**：ENCODE portal（accession codes 见 Supplementary Table 1）；UCSC trackhub：https://genome.ucsc.edu/s/cybluetree/TRE%20hub
- **阅读日期**：2025-10-03（以检索日期为准）
- **在课题方向中的位置**：本文提供全组织/细胞类型覆盖的、基于转录起始（PRO-cap）的活性调控元件图谱，并整合 ProCapNet 深度学习模型进行序列-功能解析与变异效应预测。对「TF–DNA 结合机制 × AI」方向，本文提供了：(1) 大规模活性增强子/启动子的转录起始信号作为 TF 结合功能读出的训练标签；(2) 基于深度学习的序列-转录起始建模框架（ProCapNet + DeepSHAP + TF-MoDISco），可直接迁移到 TF–DNA 结合特异性与变异效应预测任务；(3) 组织特异性 TF 基序-表达关联分析范式。

## 02 一句话总结
本文用优化的 PRO-cap 协议在 215 个人类样本中绘制了碱基分辨率、跨组织/疾病状态的活性调控元件（TREs）图谱，证明转录起始信号可精准标记功能性增强子/启动子，并整合 ProCapNet 深度学习模型与统计精细定位，实现组织特异性变异-功能预测与疾病机制解析。

## 03 研究问题
- **具体问题**：能否用 RNA 聚合酶 II（Pol II）转录起始信号（而非仅染色质状态）系统性地定义人类多种正常组织与疾病状态下的活性转录调控元件（TREs），并解析其序列决定因素与疾病关联？
- **为什么重要**：现有调控元件注释（如 ENCODE cCRE）主要基于染色质可及性与组蛋白修饰，但这些表观遗传标记无法直接区分「活性」与「 poised/沉默」元件，且对短寿命 eRNA 的检测灵敏度不足。转录起始是 TRE 活性的直接功能读出，但缺乏跨组织、疾病状态的大规模高分辨率图谱。
- **现有方法不足**：(1) 表观遗传注释（ATAC-seq、H3K27ac）不能直接反映转录活性；(2) CAGE-seq 主要捕获稳定 RNA，对不稳定 eRNA 灵敏度低；(3) 缺乏碱基分辨率、可区分双向/单向起始的跨组织图谱；(4) 缺乏将转录起始信号与深度学习序列模型、GWAS/eQTL 精细定位整合的系统框架。
- **精确研究问题（Can...?）**：Can transcription initiation detected by PRO-cap at base-pair resolution across diverse human tissues and disease states delineate a functionally enriched set of active TREs that (a) outperform epigenomic annotations in predicting enhancer activity, (b) reveal tissue-specific sequence determinants via deep learning, and (c) enable context-dependent prioritization of disease-associated noncoding variants?

## 04 背景与发展脉络
*（标注：以下脉络为「经外部核验」的领域共识，结合本文框架整理）*

1. **表观遗传注释时代（ENCODE cCRE, Roadmap）**：用 DNase-seq/ATAC-seq 可及性 + H3K27ac/H3K4me1 组蛋白修饰定义候选调控元件。局限：不能区分活性/poised 状态，无法直接反映转录输出。
2. **转录起始图谱时代（CAGE, FANTOM）**：FANTOM 用 CAGE-seq 捕获 5' 帽化 RNA 定义启动子/增强子。局限：主要捕获稳定 RNA，对短寿命 eRNA 灵敏度不足，且无法区分 Pol II 暂停位点。
3. **run-on 测序技术（GRO-seq, PRO-seq, PRO-cap）**：直接捕获 Pol II 延伸中的新生 RNA，实现碱基分辨率转录起始/暂停定位。PRO-cap 通过 5' 帽化 RNA 富集，特异检测转录起始位点（TSSs）。
4. **深度学习序列模型（Basenji, Enformer, ProCapNet）**：用卷积/Transformer 架构从 DNA 序列预测功能基因组信号。ProCapNet 专门建模 PRO-cap 转录起始 profile，可解释序列-转录起始规则。
5. **本文位置**：将 PRO-cap 从细胞系扩展到 215 个人类样本（含原代组织、疾病模型），构建跨组织活性 TRE 图谱，并整合 ProCapNet + DeepSHAP + TF-MoDISco + S-LDSC/TORUS，形成「转录起始定义元件 → 序列规则解析 → 变异效应预测 → 疾病机制」的完整框架。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 表观遗传标记不能直接反映 TRE 活性 | ATAC-seq/H3K27ac 标记的元件中仅部分有转录活性；poised 增强子被误判 | 染色质可及性与组蛋白修饰是「许可性」标记，不直接等于 Pol II 招募与起始 | Results 图 2a：PRO-cap 与 cCRE 重叠分析显示大量 cCRE 无转录起始信号；Discussion 第 1 段 |
| CAGE-seq 对不稳定 eRNA 灵敏度不足 | 大量增强子转录本在 CAGE 中缺失 | CAGE 捕获稳态 RNA，eRNA 半衰期极短，被快速降解 | Introduction 第 2 段；Results「PRO-cap recapitulates...」节：PRO-cap 检出远多于 CAGE 的远端 TREs |
| 缺乏跨组织/疾病状态的活性 TRE 图谱 | 现有图谱多为细胞系或单一组织 | 原代组织样本处理困难，PRO-cap 通量低 | Results 图 1a：215 样本覆盖多器官与疾病状态 |
| 变异-功能解读缺乏组织特异性 | GWAS 变异富集在非编码区，但无法确定其作用的组织与元件 | 需要组织分辨的活性元件注释作为「功能锚点」 | Results 图 3a：S-LDSC 显示组织特异性 TRE 富集模式 |
| 序列-转录起始规则不明确 | 无法从序列预测哪些元件有转录活性、TSS 如何定位 | 缺乏碱基分辨率、跨组织的训练数据 | Results 图 4a：ProCapNet 跨 16 个组织训练，DeepSHAP 解析基序贡献 |

## 06 核心思想
1. **表面方法**：优化 PRO-cap 协议（缩短至 ~10 小时、低至 1-2 百万细胞），在 215 个人类样本（正常组织、干细胞分化、疾病模型）中绘制碱基分辨率转录起始图谱；用 PINTS 峰值检测定义 TREs；训练 ProCapNet 深度学习模型；整合 S-LDSC、TORUS、精细定位进行变异-功能分析。
2. **核心洞察**：转录起始本身（而非染色质状态）是 TRE 活性的最直接功能读出。PRO-cap 检出的 TREs 在增强子活性、进化保守性、疾病变异富集方面均优于表观遗传注释；碱基分辨率揭示 TSS 定位、双向/单向起始、暂停位点等表观遗传方法无法提供的调控信息。
3. **可能的普适教训 [Analysis]**：功能读出（如转录起始）比状态标记（如染色质可及性）更能定义「活性」元件；将高分辨率功能数据与可解释深度学习结合，可系统解析序列-功能规则并迁移到变异效应预测；组织分辨的活性元件图谱是连接 GWAS 变异与疾病机制的关键桥梁。

## 07 方法总览
- **输入**：215 个人类样本（正常组织、iPSC/ESC 分化谱系、疾病模型如 T1D 患者 T 细胞、白血病/淋巴瘤细胞系、转移癌活检）；匹配的 DNase-seq/ATAC-seq 数据（用于 ProCapNet 训练）。
- **输出**：(1) 715,296 个 union TREs（含分类：启动子/近端/远端增强子；双向/单向起始）；(2) 组织特异性 TRE 集；(3) ProCapNet 模型（16 个组织/细胞类型）；(4) 变异效应预测（eQTL/GWAS 精细定位）。
- **核心模块**：PRO-cap 实验 → 数据预处理（fastp、STAR、UMI 去重）→ PINTS 峰值检测 → union TRE 定义与分类 → 定量（DESeq2 归一化）→ 特异性评分 → ProCapNet 训练（序列 → 转录起始 profile）→ DeepSHAP 基序解析 → TF-MoDISco 基序聚类 → S-LDSC/TORUS 变异富集 → 精细定位与功能验证（CRISPRi、报告基因）。
- **反馈回路**：ProCapNet 预测 → 变异效应排序 → CRISPRi 实验验证（MYC 位点）→ 验证结果支持模型预测的组织特异性。
- **文字流程**：从多样本 PRO-cap 实验获得碱基分辨率转录起始信号 → PINTS 识别峰值并合并为 union TREs → 按位置/方向性分类 → 计算组织特异性 → 用 ProCapNet 学习序列-起始规则 → DeepSHAP 提取关键 TF 基序 → 将 TRE 注释与 GWAS/eQTL 整合，用 S-LDSC 评估组织特异性富集 → 对候选因果变异进行 in silico 突变效应预测 → 用 CRISPRi 和报告基因实验验证关键位点（如 MYC 3' 增强子、IL2RB 内含子增强子）。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 优化的 PRO-cap 协议 | 从少量细胞/组织捕获 Pol II 暂停的 5' 帽化新生 RNA | 原代组织样本量有限，需高灵敏度、低输入 | 输入：1-2 百万细胞/组织；输出：碱基分辨率转录起始信号 | Results 图 1a；Methods「Sample collection...」节 | 无法覆盖原代组织，图谱局限于细胞系 |
| PINTS 峰值检测 | 从 PRO-cap 信号中识别转录起始位点（TSSs） | 需要客观、可重复的峰值定义 | 输入：比对后的 PRO-cap reads；输出：峰值/TRE 坐标 | Methods「Data preprocessing」节；引用 PINTS 原始文献 | 峰值定义偏差将影响所有下游分析 |
| union TRE 定义与分类 | 跨样本合并元件，按位置/方向性分类 | 需统一注释以进行跨组织比较 | 输入：各样本峰值；输出：715,296 union TREs（启动子/增强子；双向/单向） | Results 图 1a；Extended Data 图 1b | 无法进行跨样本比较与 meta 分析 |
| ProCapNet 深度学习模型 | 从 DNA 序列预测转录起始 profile（count + profile 任务） | 解析序列-起始规则，预测变异效应 | 输入：1kb 序列 + 匹配染色质可及性；输出：预测的起始 profile | Results 图 4a；Methods「ProCapNet models...」节 | 无法进行序列-功能解析与变异效应预测 |
| DeepSHAP + TF-MoDISco | 解释模型预测，提取关键 TF 基序 | 将黑箱模型转化为可解释的调控语法 | 输入：ProCapNet 模型 + 序列；输出：基序贡献分数、TF 基序聚类 | Results 图 4a；Methods「ProCapNet models...」节 | 无法识别组织特异性 TF 语法 |
| S-LDSC / TORUS | 评估 TRE 注释对性状遗传力的富集 | 连接调控元件与复杂性状 | 输入：TRE 注释 + GWAS summary statistics；输出：富集分数/τc | Results 图 3a、3d；Extended Data 图 6 | 无法建立 TRE 与疾病/性状的因果关联 |
| CRISPRi 筛选与报告基因 | 实验验证 TRE 功能与变异效应 | 验证计算预测的因果性 | 输入：sgRNA 文库 + 细胞系；输出：MYC 表达变化 | Results 图 1g；Extended Data 图 5b,c | 无法确认 TRE 的功能必要性 |

## 09 关键公式符号
*（本文为基因组学/实验为主，公式较少，以下为方法中涉及的定量公式）*

1. **特异性分数（Specificity score）**：
   \[
   S_e = 1 - \frac{H_e}{\log_2 N}
   \]
   其中 \( H_e = -\sum_t p_{t|e} \log_2 p_{t|e} \)，\( p_{t|e} = q_{e,t} / \sum_t q_{e,t} \)，\( q_{e,t} \) 为元件 e 在组织 t 中的平均归一化表达，N 为组织类型数。S=0 表示 ubiquitous，S=1 表示完全组织特异。

2. **方向性指数（Directionality Index, DI）**：
   \[
   DI = \frac{\text{plus\_count} - \text{minus\_count}}{\text{plus\_count} + \text{minus\_count}}
   \]
   衡量双向起始元件中正负链转录的平衡程度。

3. **变异效应（ProCapNet in silico 突变）**：
   \[
   \text{log}_2\text{FC} = \log_2\left(\frac{\text{predicted\_count}_{\text{alt}}}{\text{predicted\_count}_{\text{ref}}}\right)
   \]
   用于量化 SNP 对转录起始活性的预测影响。

4. **S-LDSC 富集分数**：
   \[
   \text{Enrichment} = \frac{\text{Prop. heritability} / \text{Prop. SNPs}}{\text{Prop. heritability} / \text{Prop. SNPs}}
   \]
   标准分层 LD 分数回归框架（引用 Finucane et al. 2015）。

## 10 实验设计与证据链
- **数据集**：215 个人类样本（正常组织、iPSC/ESC 分化、T1D 患者 T 细胞、白血病/淋巴瘤细胞系、转移癌活检）；中位去重 reads 2960 万；多数样本 ≥2 技术重复（中位基因组范围相关性 0.902）。
- **指标**：PRO-cap 信号定量、TRE 分类（启动子/增强子）、特异性分数、进化保守性（phastCons/phyloP）、S-LDSC 富集、eQTL 重叠、CRISPRi 功能验证。
- **基线/对照**：ENCODE cCRE 注释、FANTOM CAGE-seq 注释、ATAC-seq/DNase-seq 峰值、H3K27ac ChIP-seq。
- **评测协议**：交叉验证（ProCapNet 留出染色体）、与实验验证的 VISTA 增强子比较、CRISPRi 扰动后 MYC 表达变化。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| PRO-cap 图谱构建 | 转录起始可跨组织/疾病状态系统检测 | 215 样本，多组织/疾病 | 715,296 union TREs；组织聚类清晰 | 转录起始是跨状态的活性 TRE 通用标记 | 未覆盖所有细胞类型/发育阶段 | Results 图 1a；Extended Data 图 1 |
| 与表观遗传注释比较 | PRO-cap 提供表观遗传标记之外的信息 | PRO-cap vs ATAC/H3K27ac/cCRE | 大量 cCRE 无转录起始；PRO-cap 检出更多远端 TRE | 转录起始是活性增强子的更精确标记 | 表观遗传标记仍可标记 poised 元件 | Results 图 2a |
| VISTA 增强子验证 | PRO-cap 信号与体内增强子活性一致 | PRO-cap vs VISTA 转基因增强子 | VISTA 阳性增强子 PRO-cap 信号显著更高 | 转录起始预测增强子活性 | VISTA 仅覆盖胚胎组织 | Results 图 1e |
| ProCapNet 训练与解释 | 序列可预测转录起始，且可解析 TF 基序 | 16 组织/细胞类型，交叉验证 | 高预测性能；识别已知 TF 基序（如 SP、ETS、CREB） | 序列编码转录起始规则 | 模型仅捕捉局部序列效应 | Results 图 4a；Supplementary 图 6 |
| S-LDSC 组织特异性富集 | TRE 注释捕获组织特异性遗传力 | 176 GWAS traits vs 组织 TRE | 组织匹配的 TRE 显著富集 | TRE 是连接变异与组织的功能锚点 | 富集不等于因果 | Results 图 3a、3d |
| CRISPRi MYC 位点 | TRE 模块功能必要性与选择性 | 5 种细胞系，sgRNA 靶向 TRE 模块 | 模块特异性敲低 MYC | TRE 模块具有选择性功能 | 仅验证 MYC 位点 | Results 图 1g；Extended Data 图 5 |
| rs6426833 报告基因 | 变异改变增强子活性 | 参考 vs 替代等位基因，Caco-2/HCT116 | 替代等位基因活性更高 | 变异具有功能效应 | 仅一个变异，体外实验 | Results 图 3b,c |

## 11 结论正确解读
- **任务范围**：本文是描述性图谱 + 计算建模 + 靶向验证，非全基因组功能筛选。结论限于「转录起始可标记活性 TRE」及「ProCapNet 可预测序列-起始关系」。
- **oracle/真值输入**：ProCapNet 训练使用 PRO-cap 信号作为标签，染色质可及性作为辅助输入；变异效应预测是计算推断，未经全基因组实验验证。
- **端到端状态**：从样本到 TRE 图谱的流程是端到端的；但「变异 → 疾病」链条仅展示了个案验证（rs6426833、MYC 位点），非系统验证。
- **算力成本**：ProCapNet 为中等规模 CNN，训练成本可承受；S-LDSC/TORUS 为轻量统计计算。
- **历史数据依赖**：依赖 ENCODE/GENCODE/GTEx 注释；TRE 分类基于 GENCODE v37 转录本。
- **模型依赖**：ProCapNet 仅建模局部序列（1kb 窗口），不包含远端调控信息；DeepSHAP 归因是近似。
- **最难情形**：单向起始的远端增强子、低表达组织、异质性样本（如肿瘤活检）的 TRE 检测。
- **群体/领域边界**：样本以欧洲裔为主（GTEx 来源）；疾病覆盖有限（T1D、血液肿瘤、转移癌），未覆盖所有疾病类型。
- **不确定性**：TRE 与靶基因连接基于最近基因/共表达推断，未系统验证 3D 互作；pause 位点变异效应未深入探讨。
- **有边界的复述**：在 215 个人类样本中，PRO-cap 检出的转录起始信号可定义一组功能富集、进化保守、组织特异的活性 TREs；ProCapNet 能从序列预测这些信号并解析 TF 基序贡献；该框架可优先排序组织特异性非编码变异，但因果验证仍需实验。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 样本覆盖有限 | 未覆盖所有细胞类型、发育阶段、疾病状态 | 扩展至更多组织/疾病队列 | Discussion 第 2 段 |
| ProCapNet 仅建模局部序列 | 1kb 窗口无法捕捉远端调控元件效应 | 整合 3D 基因组、更长上下文 | Discussion 第 3 段 |
| 变异效应预测未经全基因组验证 | 仅个案验证（rs6426833、MYC） | 大规模 CRISPR 筛选、报告基因 | Discussion 第 4 段 |
| 单向 TRE 分析受限 | 单向起始可能包含噪声，分析集中于双向 TRE | 改进单向 TRE 检测与验证 | Results「...restricted to divergent TREs」节 |
| 靶基因连接推断 | 基于最近基因/共表达，未验证 3D 互作 | 整合 Hi-C、eQTL 共定位 | Discussion 第 5 段 |
| 疾病样本异质性 | 肿瘤活检样本细胞组成复杂 | 单细胞分辨率 PRO-cap | Discussion 第 6 段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| PRO-cap 信号与增强子活性的关联基于 VISTA 胚胎数据 | VISTA 仅覆盖胚胎组织，可能不反映成人增强子活性；报告基因 assay 与内源染色质环境不同 | 若 PRO-cap 在成人组织中误分类增强子，下游变异解读将受影响 | 在成人组织中进行 CRISPR 干扰或报告基因验证随机抽样 | Results 图 1e；Methods「VISTA...」节 |
| ProCapNet 训练数据包含染色质可及性作为输入 | 模型可能主要依赖可及性而非序列基序，削弱「序列-功能」解释 | 若模型依赖可及性，则无法用于无可及性数据的场景（如变异预测） | 消融实验：仅用序列训练，比较性能 | Methods「ProCapNet models...」节 |
| S-LDSC 富集分析使用组织匹配的 TRE 注释 | 组织间样本量不均（如脑样本多、胰腺少）可能引入偏差 | 富集结果可能反映样本量而非生物学 | 进行样本量匹配的置换检验 | Results 图 3a；Methods「Heritability partition...」节 |
| 双向 TRE 分析限制 | 单向 TRE 可能包含大量真实增强子，排除后可能丢失重要调控信息 | 单向增强子在发育/疾病中可能具有独特功能 | 对单向 TRE 进行独立验证（如 CRISPR） | Results「...restricted to divergent TREs」节 |
| 靶基因连接基于最近基因 | 增强子可调控远距离基因，最近基因推断可能错误 | 错误的靶基因连接会导致通路分析偏差 | 整合 Hi-C、eQTL 共定位、CRISPR 验证 | Methods「Pathway enrichment...」节 |
| 疾病样本（转移癌）与正常样本的批次效应 | 肿瘤样本处理流程可能不同于正常组织 | 批次效应可能混淆组织特异性信号 | 进行批次校正、重复验证 | Methods「Sample collection...」节 |

## 14 学到什么
*（Agent 提炼的知识候选，面向「TF–DNA 互作 × AI/物理模拟」课题）*

1. **转录起始作为 TF 结合的功能读出**：PRO-cap 信号可直接标记「活性」TF 结合位点（增强子/启动子），比染色质可及性更接近 TF 功能输出。可迁移：在 TF–DNA 结合预测任务中，用 PRO-cap 信号作为训练标签或过滤条件，减少「结合但不功能」的假阳性。
2. **ProCapNet 架构可迁移**：CNN 建模序列 → 转录起始 profile（count + profile 双任务）的框架，可直接迁移到 TF–DNA 结合特异性预测。关键设计：以可及性为辅助输入、以起始位点为中心的多任务输出。
3. **DeepSHAP + TF-MoDISco 的基序解析流程**：从深度学习模型提取碱基贡献分数 → 聚类为基序 → 与已知 TF 基序比对。可迁移：用于解析 TF 结合位点的序列语法（如基序间距、方向、协同性）。
4. **组织特异性基序-表达关联分析**：将组织限制性 TF 基序与 GTEx TF 表达关联，推断「基序- TF 表达」共同决定组织特异性调控。可迁移：在 TF–DNA 结合模型中引入 TF 表达作为上下文特征。
5. **变异效应预测的「功能锚点」策略**：用组织匹配的活性 TRE 注释作为 S-LDSC/TORUS 的注释集，显著提升 GWAS 富集信号。可迁移：在 TF–DNA 结合变异预测中，优先考虑位于活性 TRE 内的变异。
6. **双向/单向起始分类**：双向起始是增强子的稳健特征，单向起始可能代表不同调控逻辑。可迁移：在 TF 结合位点分类中引入方向性特征。
7. **CRISPRi 验证的靶向策略**：对计算预测的 TRE 模块进行 CRISPRi 筛选，验证功能必要性与选择性。可迁移：作为 TF–DNA 结合预测的实验验证范式。

## 15 与已有知识连接
- **ENCODE cCRE / Roadmap 表观遗传注释**：本文 PRO-cap TRE 与 cCRE 的比较（Results 图 2a）直接衔接 ENCODE 框架，显示转录起始可细化 cCRE 的活性状态。
- **FANTOM CAGE-seq**：本文与 FANTOM 的比较显示 PRO-cap 对远端增强子灵敏度更高，与已知 CAGE 对不稳定 eRNA 灵敏度有限的共识一致。
- **ProCapNet 原始论文**（Kundaje 实验室）：本文扩展了 ProCapNet 的应用范围（从细胞系到多组织/疾病），并整合了 S-LDSC/TORUS。
- **DeepSHAP / TF-MoDISco**：可解释 AI 在基因组学中的标准工具，本文展示了其在多组织场景下的应用。
- **S-LDSC / TORUS**：分层 LD 分数回归和贝叶斯 eQTL 富集方法，本文将其应用于组织特异性 TRE 注释。
- **VISTA Enhancer Browser**：体内增强子验证的金标准，本文用于验证 PRO-cap 信号的功能相关性。
- **CRISPRi 筛选**：与 ENCODE 4 的调控元件功能验证策略一致。
- **与课题方向的连接**：本文的「转录起始 → 活性元件 → TF 基序 → 变异效应」框架，为 TF–DNA 结合机制研究提供了「功能活性」维度的标注数据；ProCapNet 的序列建模方法可直接迁移到 TF 结合特异性预测；组织特异性基序-表达关联分析为理解 TF 协同性提供了新视角。

## 16 研究想法
*（Agent 生成的研究候选，面向「TF–DNA 互作 × AI/物理模拟」课题）*

1. **候选名称**：TF–DNA 结合特异性的「转录起始感知」预测模型
   - **来源局限/观察**：现有 TF 结合预测（如 DeepSEA、Basenji）主要基于染色质状态或 ChIP-seq，未充分利用转录起始信号作为功能读出。
   - **核心假设**：将 PRO-cap 信号作为辅助任务或标签，可提升 TF 结合位点预测的特异性（区分「结合且功能」与「结合但不功能」）。
   - **初步方法**：在 ProCapNet 架构基础上，增加 TF 结合预测头；用 ENCODE 3/4 的 ChIP-seq 和本文 PRO-cap 数据联合训练；比较有无 PRO-cap 辅助的性能差异。
   - **验证方式**：在独立数据集（如 GTEx eQTL、GWAS 精细定位）上评估预测位点的功能富集。
   - **创新状态**：unverified

2. **候选名称**：组织特异性 TF 协同基序的深度学习解析
   - **来源局限/观察**：本文发现组织特异性 TRE 富集特定 TF 基序，但未系统解析基序间的协同/拮抗关系。
   - **核心假设**：组织特异性转录起始由「基序组合 + TF 表达」共同决定，可通过深度学习注意力机制解析。
   - **初步方法**：用 ProCapNet 的 DeepSHAP 分数构建基序共现网络；结合 GTEx TF 表达，识别组织特异的 TF-TF 协同模块。
   - **验证方式**：在 CRISPRi 数据中验证预测的协同 TF 对。
   - **创新状态**：unverified

3. **候选名称**：变异效应预测的「活性增强子」优先化策略
   - **来源局限/观察**：GWAS 变异富集在活性 TRE 内，但现有预测工具未充分利用组织匹配的活性注释。
   - **核心假设**：将 PRO-cap 检出的组织特异性活性 TRE 作为先验，可提升非编码变异的功能预测精度。
   - **初步方法**：将本文 TRE 注释整合到现有变异效应预测流程（如 CADD、Eigen、Enformer）；比较有/无 TRE 先验的 AUC。
   - **验证方式**：在 176 GWAS traits 上评估富集提升。
   - **创新状态**：unverified

4. **候选名称**：TF 结合与转录起始的物理模拟耦合框架
   - **来源局限/观察**：本文为纯实验+统计建模，未涉及 TF–DNA 结合的物理机制（如构象变化、暂停位点选择）。
   - **核心假设**：将 MD 模拟的 TF–DNA 结合自由能特征与 ProCapNet 的序列特征融合，可提升对转录起始位点选择的预测。
   - **初步方法**：对关键 TF（如 SP、ETS）进行 MD 模拟，提取结合构象特征；作为额外特征输入 ProCapNet。
   - **验证方式**：在本文 PRO-cap 数据上比较融合模型的预测性能。
   - **创新状态**：unverified

5. **候选名称**：疾病相关 TF 调控程序的跨组织比较
   - **来源局限/观察**：本文展示了 T1D 患者 T 细胞中 TRE 活性改变，但未系统比较疾病状态下的 TF 调控程序。
   - **核心假设**：疾病状态下的 TRE 活性改变由特定 TF 模块驱动，可通过差异分析识别。
   - **初步方法**：对 T1D、白血病、转移癌样本进行差异 TRE 分析；结合 TF 基序富集和表达数据，识别疾病特异 TF 模块。
   - **验证方式**：在独立疾病队列中验证。
   - **创新状态**：unverified