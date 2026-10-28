## 01 基本信息
- **标题**: Natural variation in regulatory code revealed through Bayesian analysis of plant pan-genomes and pan-transcriptomes
- **作者与单位**: Wei Wei, Xing Wu, Chandler A Sutherland, Yuting Lin, China Lunde, Moises Exposito-Alonso, Ksenia Krasileva（加州大学伯克利分校等，具体单位未在摘要中详列）
- **期刊/预印本平台**: bioRxiv (preprint server for biology)
- **年份**: 2025（预印本发布于2025-11-24）
- **论文类型**: 预印本（方法学 + 应用研究）
- **领域**: 植物功能基因组学；cis-regulatory element (CRE) 鉴定；pan-genomics；pan-transcriptomics；Bayesian variable selection
- **关键词**: cis-regulatory elements (CREs); pan-genome; pan-transcriptome; k-mer; Bayesian variable selection; transcription factor binding motifs (TFBMs); structural variants (SVs); maize; soybean
- **DOI/arXiv 号**: 10.1101/2025.10.27.684862
- **代码**: https://github.com/xingwu2/K-PROB ; https://github.com/WeiWei-1112/K-RPOB-analysis-code-and-scripts.git
- **数据**: 处理数据见 Zenodo doi.org/10.5281/zenodo.17346377；原始数据来源见 Methods（MaizeGDB, Genome Warehouse PRJCA002030, PRJCA00936, GEO GSE165787, Zenodo 10.5281/zenodo.14991916）
- **阅读日期**: 2026-05-13（按当前日期）
- **在「蛋白质-DNA互作(聚焦TF–DNA结合机制) × AI方法/物理模拟」方向中的位置**: 本文属于「序列-表达关联」类方法，不依赖3D结构或物理模拟，而是利用群体内自然变异（pan-genome中的k-mer多态性）与表达变异做统计关联，以Bayesian variable selection识别功能性TF结合位点。其核心贡献在于：① 无需参考基因组，直接利用k-mer表征启动子序列多样性；② 通过跨基因共享的k-mer聚类增强统计功效；③ 以PIP和per-pangene效应过滤识别功能性CRE。对TF–DNA结合机制研究而言，本文提供了一种「从序列变异到功能位点」的互补路径，可与结构预测、ChIP-seq/DAP-seq、ATAC-seq等实验数据整合。

## 02 一句话总结
本文开发了K-PROB工具，利用pan-genome中启动子k-mer多态性与pan-transcriptome表达变异的Bayesian variable selection联合建模，在玉米和大豆中鉴定出富集已知TF结合基序的功能性cis-regulatory elements，并通过荧光素酶报告实验验证了其中6个位点的调控效应。

## 03 研究问题
- **具体问题**: 如何在物种内（intraspecific）群体水平上，从高度多态、富含结构变异的启动子区域中，系统鉴定控制基因表达变异的因果cis-regulatory elements (CREs)？
- **为什么重要**: CREs是基因表达调控的遗传基础，理解其自然变异对于作物性状工程和精准育种至关重要。传统方法（如eQTL mapping）依赖单一参考基因组和SNP标记，在结构变异丰富的区域（如NLR基因家族）无法有效定位因果变异。
- **现有方法不足**: ① 生化实验（ChIP-seq, DAP-seq, ATAC-seq）需要特定抗体或体外表达体系，且通常只在单一基因型中进行，无法覆盖群体内等位变异；② 传统eQTL依赖SNP，无法处理SVs和序列缺失；③ 跨物种保守性分析无法捕捉物种内快速演化的调控变异。
- **精确的「Can ... ?」研究问题**: Can a k-mer-based Bayesian variable selection model, applied to pan-genome promoter sequences and pan-transcriptome expression data, identify causal cis-regulatory elements within highly polymorphic promoter regions that are enriched for known transcription factor binding motifs and validated by reporter assays?

## 04 背景与发展脉络
*注：以下脉络基于本文引言及引用，属「经外部核验」的领域发展概述，但具体分期和代表性方法选择为本文框架。*

1. **实验性启动子删减 (Experimental promoter bashing)**：通过连续删除启动子片段并检测报告基因表达来定位CREs。优点：直接、功能明确；缺点：低通量、耗时，无法覆盖群体内等位变异。
2. **生化全基因组方法**：ChIP-seq（体内TF结合）、DAP-seq（体外TF结合）、ATAC-seq（染色质开放性）。优点：高通量、可鉴定全基因组范围TF结合位点；缺点：依赖单一参考基因型，无法捕捉群体内等位差异，且需要实验材料和特定TF试剂。
3. **比较基因组学/保守性分析**：跨物种比对鉴定保守非编码序列。优点：可发现功能重要的CREs；缺点：无法捕捉物种内快速演化的调控变异，且保守性不等于功能。
4. **eQTL mapping**：将表达变异与遗传标记（SNP）关联。优点：直接利用自然变异；缺点：依赖参考基因组、SNP标记无法覆盖SVs、单标记边际检验功效低、难以定位因果变异。
5. **k-mer-based pan-genome方法**：如PanKmer等，利用k-mer表征序列多样性，无需参考基因组比对。优点：可处理SVs和高度多态区域；缺点：此前主要用于序列比较，未与表达数据关联。
6. **本文位置 (K-PROB)**：首次将k-mer表征与Bayesian variable selection联合建模，在pan-genome尺度上关联启动子序列变异与表达变异，直接输出候选CRE序列（k-mer clusters），并整合per-pangene效应过滤和实验验证。其创新在于「k-mer作为等位变异单元」+「跨基因共享」+「因果优先化」三者的结合。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单参考基因组无法覆盖群体内启动子多态性 | 高度多态区域（如NLR基因启动子）在单一参考基因组中缺失或错配，导致变异不可见 | 结构变异（SVs）和插入/缺失在群体中普遍存在，单一参考无法代表所有等位 | Introduction: "CREs underlying rapid evolution of gene expression often overlap with structural variation in promoters, making them undetectable using single-reference genomes" |
| 传统eQTL依赖SNP标记，无法定位SV内部或附近的因果变异 | eQTL信号落在SV区域时，无法确定具体因果序列 | SNP标记与SV不完全连锁，且SV内部序列无法通过短读长比对到参考基因组 | Introduction: "eQTL approaches... rely on short-read sequencing, read mapping to a selected reference... limits the identification of causal regulatory variants in genomic regions rich in structural variation" |
| 生化方法（ChIP-seq/DAP-seq）仅覆盖单一基因型 | 无法评估等位特异性结合或群体内TF结合差异 | 实验通常在参考品种中进行，无法扩展到群体规模 | Introduction: "biochemical assays typically require high sequencing depth and specialized protocols, resulting in such datasets being available only in a few plant model species and only in a single reference genotype" |
| 序列保守性 ≠ 功能 | 保守非编码序列不一定是功能性CRE | 保守性反映净化选择，但功能CRE可能物种/群体特异 | Introduction: "sequence-based methods tend to lead to false discoveries because the presence of CRE sequence does not equal regulatory function" |
| 边际关联检验功效低 | 单变异-单表型关联无法检测多基因调控或效应较小的CRE | 每个CRE效应小，且多重检验负担重 | Introduction: "single-variable marginal regression methods commonly used in GWAS models" 被本文联合模型取代（Results 图2C） |

## 06 核心思想
1. **表面方法**：从pan-genome中提取每个基因启动子区域的k-mer（7-12 bp），聚类相似k-mer为簇，构建k-mer簇×基因的计数矩阵，与基因表达数据一起输入Bayesian variable selection回归模型，估计每个k-mer簇对表达的效应和后验包含概率（PIP），再通过per-pangene回归过滤出功能性位点，最后用荧光素酶报告实验验证。
2. **核心洞察**：
   - k-mer天然编码了等位变异（包括SNP、indel、SV边界），无需参考基因组比对，因此能捕获传统SNP方法遗漏的调控变异。
   - 跨基因共享的k-mer簇允许模型「借用」信息：一个TF结合基序在多个基因启动子中出现，其效应可被联合估计，从而提升统计功效。
   - Bayesian variable selection（类似Bayesian sparse linear mixed model）天然处理高维稀疏问题，输出PIP作为因果优先化指标，比边际检验更直接指向因果变异。
   - per-pangene效应过滤是关键步骤：全局显著的k-mer簇未必在每个基因中都功能，只有那些在特定基因中表现出显著效应的位点才是真正的功能性CRE。
3. **可能的普适教训 [Analysis]**：在高度多态、结构变异丰富的基因组区域，将「序列单元」从SNP升级为k-mer，并利用跨位点共享信息，是突破参考基因组局限、提升因果变异定位精度的有效策略。这一思路可迁移到任何「序列变异-表型」关联场景，包括TF–DNA结合特异性的群体水平分析。

## 07 方法总览
- **输入**：
  - Pan-genome序列（玉米26个自交系、大豆27个品系）及基因注释
  - 对应品系的RNA-seq表达数据（TPM）
  - 启动子区域定义（2 kb上游）
- **输出**：
  - 显著k-mer簇列表（FDR ≤ 0.1），含PIP、效应值
  - 功能性k-mer簇-基因对（per-pangene显著）
  - 候选CRE序列及其预测的调控方向（激活/抑制）
- **模块**：
  1. 启动子序列提取与k-mer枚举
  2. k-mer聚类（CD-HIT，允许1个错配）
  3. 计数矩阵构建（k-mer簇×基因）
  4. Bayesian variable selection回归（Gibbs采样）
  5. per-pangene效应过滤（线性回归）
  6. TF基序比对（PlantTFDB, DAP-seq基序）
  7. 实验验证（荧光素酶报告）
- **训练**：10折交叉验证选择k值（7-12 bp），以预测R²为指标
- **工具**：Python（K-PROB主程序）、CD-HIT、R（per-pangene过滤、统计检验）、FIMO/MEME/TOMTOM（基序分析）
- **反馈回路**：交叉验证指导k选择 → 模型输出 → 实验验证 → 结果反馈到模型解释
- **假设**：① 启动子序列变异是表达变异的主要cis因素；② k-mer簇可近似代表TF结合位点；③ 跨基因共享的k-mer簇具有一致的调控效应方向；④ 稳态表达水平可反映cis调控效应。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| k-mer枚举与聚类 | 将启动子序列分解为k-mer并聚类为簇 | 将序列变异转化为可统计的变量单元，聚类可捕获错配变体 | 输入：启动子FASTA；输出：k-mer簇集合 | Methods "k-mer enumeration and clustering" | 移除聚类则变量维度爆炸，统计功效大幅下降 [预期] |
| 计数矩阵构建 | 统计每个基因中每个k-mer簇的出现次数 | 将序列信息转化为回归模型的输入矩阵 | 输入：k-mer簇、基因启动子；输出：计数矩阵 | Methods "count matrix construction" | 移除则无法进行关联分析 [预期] |
| Bayesian variable selection回归 | 联合估计所有k-mer簇对表达的效应，输出PIP | 高维变量选择，优先化因果k-mer簇 | 输入：计数矩阵+表达+协变量；输出：PIP、效应值 | Results 图2C：多基因模型解释75%表达变异 vs 单基因组6% | 移除则退化为边际检验，功效显著降低 [实测：图2C对比] |
| per-pangene效应过滤 | 对每个k-mer簇-基因对做回归，保留显著对 | 全局显著的簇未必在每个基因中都功能，需定位具体功能性位点 | 输入：显著k-mer簇+表达；输出：功能性位点列表 | Results 图3A-B：过滤后效应量增大，与ATAC-seq重叠率提升 | 移除则无法区分功能性位点与非功能性出现 [预期] |
| TF基序比对 | 将显著k-mer簇与已知TF基序比对 | 验证识别的k-mer簇是否对应已知TF结合序列 | 输入：k-mer簇、PlantTFDB/DAP-seq基序；输出：基序匹配列表 | Results 图2D：匹配到C2H2、NLP、WOX等TF家族 | 移除则无法建立与已知TF的关联 [预期] |
| 实验验证（荧光素酶报告） | 在烟草叶片中验证k-mer的调控效应 | 提供因果性的直接实验证据 | 输入：野生型/突变型启动子构建；输出：荧光素酶活性差异 | Results 图4B-C：5/6位点验证显著 | 移除则缺乏因果证据，仅停留在关联层面 [预期] |

## 09 关键公式符号
**模型**：y = Cα + Xβ + ε

| 符号 | 含义 | 用途 |
|------|------|------|
| y | n维基因表达向量（n = 基因数） | 响应变量 |
| C | n × c 协变量矩阵 | 校正批次、组织等混杂因素 |
| α | c维协变量效应向量 | 协变量回归系数 |
| X | n × p k-mer簇计数矩阵（X_ij = 簇j在基因i启动子中的出现次数） | 核心预测变量 |
| β | p维k-mer簇效应向量 | 待估计的遗传效应 |
| ε | n维残差向量，ε ~ N(0, δ_e² I) | 噪声项 |

**先验分布**：
- β_i ~ (1-γ_i) N(0, δ_0²) + γ_i N(0, δ_1²)
- γ_i ~ Bernoulli(π)
- π ~ Beta(a_π, b_π)
- δ_1⁻² ~ Gamma(a_1, b_1)
- δ_e⁻² ~ Gamma(a_e, b_e)

| 符号 | 含义 |
|------|------|
| γ_i | 潜在指示变量：γ_i=1 表示第i个k-mer簇有较大效应（来自N(0,δ_1²)），γ_i=0 表示效应可忽略（来自N(0,δ_0²)） |
| δ_0² | 小方差（背景效应），设为 q × Var(y)/Σ_j Var(X_·j)，q默认0.05 |
| δ_1² | 大方差（真实效应） |
| π | 先验包含概率 |
| PIP_i | 后验包含概率 = E[γ_i \| y, C, X]，用于优先化因果k-mer簇 |

**用途**：PIP是核心输出指标，用于排序候选CRE；效应值β用于预测调控方向（正=激活，负=抑制）。

## 10 实验设计与证据链
**数据集与资源**：
- 玉米：26个自交系pan-genome（MaizeGDB NAM项目），8组织RNA-seq（Hufford et al. 2021）
- 大豆：27个品系（含Glycine soja）pan-genome（Genome Warehouse PRJCA002030），叶片RNA-seq（PRJCA00936）
- ATAC-seq：玉米26系（GEO GSE165787）
- DAP-seq：玉米B73系212个TF（Zenodo 10.5281/zenodo.14991916）
- 基序数据库：PlantTFDB

**指标**：预测R²（交叉验证）、PIP、FDR、富集倍数、荧光素酶活性比值

**评测协议**：10折交叉验证（按基因/品系/pan-gene三种划分方式）

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|-------------------|------|
| 高变异基因鉴定 | 启动子序列和表达高度变异的基因富集环境响应功能 | 顶部30% vs 底部30%变异基因的GO/Pfam富集 | NLR、GST、环境响应相关显著富集 | 高cis调控变异基因与适应相关 | 不能证明因果关系，仅相关性 | Results 图1B-C |
| k值选择 | k=11为最优 | k=7-12，10折CV预测R² | k=11时R²≈0.62（按基因划分） | k=11平衡了特异性与统计功效 | 最优k可能随物种/数据集变化 | Results 图2B |
| 多基因联合 vs 单基因模型 | 联合建模提升功效 | 多基因模型 vs 单基因模型 | 多基因解释75%表达变异，单基因仅6% | 跨基因共享信息显著提升统计功效 | 未比较其他多基因方法（如MTAG） | Results 图2C |
| 基序富集 | 显著k-mer簇富集已知TF基序 | 显著簇 vs 随机簇与PlantTFDB比对 | 1.4倍富集（p<0.001, 置换检验） | K-PROB识别序列具有TF结合特征 | 富集不等于直接结合 | Results 图2C |
| ATAC-seq重叠 | 功能性位点位于开放染色质 | 过滤后位点 vs 所有位点与ATAC-seq峰重叠 | 过滤后重叠率提升1.79倍（95%CI: 1.52-2.07） | 过滤策略富集功能性位点 | 开放染色质不等于功能 | Results 图3D |
| DAP-seq重叠 | 功能性位点与TF体外结合位点重叠 | 过滤后位点 vs 所有位点与DAP-seq峰重叠 | 过滤后重叠率提升3.19倍（95%CI: 2.55-3.84） | 功能性位点确实被TF结合 | DAP-seq为体外实验，体内结合需ChIP-seq验证 | Results 图3E |
| 荧光素酶报告实验 | 去除k-mer改变启动子活性 | 野生型 vs 突变型启动子（去除k-mer） | 5/6位点显示显著表达差异（1.5-2.3倍） | 识别的k-mer具有因果调控效应 | 异源系统（烟草）可能不完全反映玉米体内调控 | Results 图4B-C |

## 11 结论正确解读
- **任务范围**: 本文仅针对启动子区域（2 kb上游）的cis调控变异，不涉及增强子、绝缘子等远端调控元件；仅覆盖玉米26系和大豆27系，群体规模有限。
- **oracle/真值输入**: 无人工标注的「真值CRE」；以已知TF基序、ATAC-seq/DAP-seq重叠作为间接验证，以荧光素酶报告实验作为直接功能验证（但仅验证了6个位点）。
- **端到端状态**: 非端到端。K-PROB输出候选k-mer簇，需后续per-pangene过滤和实验验证才能确定功能性位点。
- **算力成本**: 未报告具体算力需求，但Bayesian MCMC采样在数万基因×数万k-mer簇规模下计算量较大。
- **历史数据依赖**: 依赖高质量的pan-genome组装和匹配的RNA-seq数据，数据质量直接影响结果。
- **模型依赖**: 线性加性模型，未考虑k-mer簇间的交互效应（如TF协同结合）；未考虑染色质状态、甲基化等表观遗传因素。
- **最难情形**: 效应量小、出现频率低的k-mer簇难以被检测；高度相似的k-mer簇可能被聚类合并，丢失精细分辨率。
- **群体/领域边界**: 仅适用于有pan-genome和pan-transcriptome的物种；结果可能受群体结构影响（未做群体结构校正的明确说明）。
- **不确定性**: PIP和效应值均为估计值，存在抽样误差；MCMC收敛性依赖诊断（Geweke检验），但未报告具体收敛指标。
- **有边界的复述**: K-PROB在玉米和大豆中，利用pan-genome启动子k-mer变异与稳态表达变异的联合Bayesian建模，能够鉴定出富集已知TF基序、与开放染色质和DAP-seq位点重叠、且经报告实验验证的候选CRE，其性能显著优于单基因模型，但该方法局限于启动子区域、线性加性效应假设和有限的群体规模。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 群体规模有限 | 仅26个玉米自交系和27个大豆品系 | 纳入更多品系以提升统计功效和分辨率 | Discussion: "this study used genomes from only ~25 maize or soybean accessions, but as high-quality pangenomic datasets continue to grow, incorporating more intraspecific genetic and transcriptional variation is expected to greatly enhance statistical power and resolution" |
| 固定k-mer长度 | 选择单一最优k值（7-12 bp） | 开发支持可变k-mer长度的方法 | Discussion: "more flexible methods that accommodate variable k-mer lengths could further improve the power to identify TF binding motifs of diverse sizes" |
| 仅考虑加性效应 | 未建模k-mer簇间交互（TF协同） | 引入交互项捕获TF-TF互作 | Discussion: "current model only considered the additive effects of each k-mer... Future extensions could include interaction terms to capture these biologically meaningful TF-TF interactions" |
| 稳态表达 | 仅使用稳态表达数据 | 扩展到诱导/胁迫条件下的动态表达 | Discussion: "focuses on steady-state gene expression in plants... population-level variation in stress-inducible expression remains poorly characterized" |
| 未利用功能注释先验 | 未整合ATAC-seq/DAP-seq等作为先验信息 | 将功能注释作为先验纳入模型 | Discussion: "can incorporate orthogonal biologically grounded functional annotations as prior information to further prioritize causal kmer cluster identification" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 启动子区域仅定义为2 kb上游 | 远端增强子、内含子调控元件被忽略，可能遗漏重要CRE | 植物中大量调控元件位于远端或基因内部 | 扩展窗口至5-10 kb或全基因区域，比较结果差异 | Methods: "2kb sequences upstream of annotated genes" |
| 表达数据为多组织混合或单一组织 | 组织特异性调控无法被检测 | TF结合具有组织特异性，混合信号可能稀释效应 | 使用单细胞或更多组织的配对数据 | Results: 玉米8组织、大豆仅叶片 |
| 聚类阈值和k值选择依赖交叉验证R² | R²最大化不一定对应生物学最优；可能过拟合特定数据集 | 影响最终k-mer簇的生物学解释性 | 在不同物种/数据集上验证k值选择的稳健性 | Results 图2B |
| 荧光素酶验证仅在烟草异源系统 | 玉米/大豆体内调控环境不同，结果可能不保守 | 异源结果不能完全代表内源调控 | 在玉米/大豆原生质体或稳定转化中验证 | Results 图4B-C |
| 未报告群体结构校正 | 群体分层可能导致假阳性关联 | 玉米和大豆均有明显群体结构 | 加入主成分或亲缘关系矩阵作为协变量 | Methods 未提及群体结构校正 |
| 与DAP-seq重叠分析仅用B73单基因型 | 其他基因型的TF结合可能不同 | 单基因型DAP-seq无法代表群体内结合变异 | 使用多基因型DAP-seq数据 | Results 图3E |
| 未比较与现有eQTL/基序扫描工具的性能 | 缺乏与标准方法的直接对比 | 无法评估K-PROB的增量优势 | 在相同数据上运行MatrixEQTL、SNP-based GWAS等对比 | Results 未提供方法对比 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **k-mer作为等位变异单元**：在TF–DNA结合研究中，k-mer（6-12 bp）天然匹配TF基序长度，可直接代表潜在结合位点。K-PROB证明，将k-mer作为关联分析的变异单元，可捕获SNP和SV层面的调控变异，无需参考基因组。**可迁移到**：任何物种的TF–DNA结合位点群体水平分析，尤其是结构变异丰富的NLR等快速演化基因家族。

2. **跨基因共享信息提升统计功效**：同一TF基序出现在多个基因启动子中，联合建模可「借用」信息，显著提升检测功效（多基因模型R²=75% vs 单基因6%）。**可迁移到**：TF–DNA结合特异性预测，可利用跨基因的共享基序信息训练更稳健的模型，尤其在训练数据有限时。

3. **Bayesian variable selection用于因果优先化**：PIP作为因果包含概率，比边际p值更直接指向因果变异，且天然处理高维稀疏问题。**可迁移到**：从ChIP-seq/DAP-seq峰内的大量候选SNP/k-mer中优先化功能性变异，或与深度学习模型结合作为特征选择层。

4. **per-pan-gene效应过滤策略**：全局显著→局部验证的两步策略，有效区分「普遍调控基序」与「基因特异性功能位点」。**可迁移到**：TF–DNA结合预测中，区分「基序存在」与「基序功能」两个层次，避免仅凭序列匹配产生假阳性。

5. **多组学整合验证框架**：序列变异（pan-genome）+ 表达变异（pan-transcriptome）+ 染色质状态（ATAC-seq）+ 体外结合（DAP-seq）+ 功能实验（荧光素酶）的多层证据链。**可迁移到**：TF–DNA互作研究，建立从「序列预测」到「功能验证」的完整流程。

6. **高变异基因的生物学意义**：启动子序列和表达高度变异的基因富集环境响应功能（NLR、GST等），提示cis调控变异是适应性进化的主要驱动。**可迁移到**：研究TF–DNA结合位点的进化动态，聚焦高变异启动子区域可能发现新的调控机制。

## 15 与已有知识连接
- **与eQTL mapping的关系**: 本文方法可视为「k-mer-based eQTL」，但不同于传统SNP-eQTL，它直接利用序列单元而非遗传标记，且采用联合模型而非边际检验。与GTEx等eQTL研究的发现一致：cis调控变异是表达变异的主要来源。
- **与TF基序数据库的关系**: 本文使用PlantTFDB作为验证资源，其识别的k-mer簇与已知基序的富集验证了方法有效性。与JASPAR、CIS-BP等数据库的整合可进一步扩展。
- **与深度学习序列模型的关系**: 本文的k-mer聚类可视为一种「可解释的特征工程」，与DeepCRE、PhytoExpr等端到端深度学习模型互补。深度模型擅长捕获复杂序列语法，但缺乏因果优先化能力；K-PROB的Bayesian框架可提供因果解释。
- **与3D基因组/染色质构象的关系**: 本文仅关注启动子序列，未涉及3D基因组结构。与Hi-C、HiChIP等数据整合可扩展至增强子-启动子互作层面的调控变异分析。
- **与结构预测/AI方法的关系**: 本文不涉及蛋白质结构，但其识别的TF–DNA结合位点可作为AlphaFold3、RoseTTAFold等结构预测工具的输入，用于预测TF突变对结合亲和力的影响。
- **与群体遗传学的关系**: 本文的高变异基因富集环境响应功能，与「cis调控变异是适应性进化的底物」这一经典假说一致（如NLR基因的快速进化），可连接到McDowell & Simon (2006)等植物免疫进化研究。
- **与CRISPR基因组编辑的关系**: 本文识别的功能性CRE可直接作为基因编辑靶点，用于启动子工程和性状改良，与Rodríguez-Leal et al. (2017)等启动子编辑研究直接相关。

## 16 研究想法
**Agent 生成的研究候选**：

1. **名称**: TF–DNA结合特异性的群体水平预测模型（Pan-TFBS）
   - **来源局限/观察**: K-PROB仅利用启动子序列变异，未整合TF蛋白序列变异；TF–DNA结合特异性受TF蛋白序列和DNA序列共同决定。
   - **核心假设**: 将TF蛋白序列变异（pan-proteome）与DNA k-mer变异联合建模，可提升TF–DNA结合位点的预测精度，并揭示共进化信号。
   - **初步方法**: 扩展K-PROB框架，将TF蛋白序列embedding（如ESM2）与DNA k-mer特征拼接，训练多模态Bayesian回归或深度学习模型。
   - **验证方式**: 使用DAP-seq多基因型数据、SELEX数据、已知致病/表型相关TF突变进行验证。
   - **创新状态**: unverified

2. **名称**: 结构感知的CRE因果变异优先化（StructK-PROB）
   - **来源局限/观察**: K-PROB的per-pan-gene过滤仅依赖统计关联，未利用3D结构信息；TF–DNA结合亲和力受空间结构影响。
   - **核心假设**: 将AlphaFold3预测的TF–DNA复合物结构特征（结合界面残基、氢键网络）作为先验，可提升因果CRE的识别精度。
   - **初步方法**: 对K-PROB显著k-mer簇对应的TF–DNA复合物进行结构预测，提取结构特征作为Bayesian模型的先验或后验过滤条件。
   - **验证方式**: 与现有ChIP-seq、MPRA数据比较，评估结构先验对精度和召回率的影响。
   - **创新状态**: unverified

3. **名称**: 诱导型启动子的动态cis调控变异图谱
   - **来源局限/观察**: K-PROB仅使用稳态表达数据，但环境响应基因（如NLR）的调控变异可能在诱导条件下才显现。
   - **核心假设**: 在胁迫诱导条件下的pan-transcriptome中，可鉴定出稳态条件下不可见的因果CRE变异。
   - **初步方法**: 收集多基因型、多胁迫条件的RNA-seq数据，扩展K-PROB模型为动态Bayesian模型（如时间序列或状态依赖）。
   - **验证方式**: 对鉴定出的诱导型CRE进行荧光素酶报告实验，比较诱导前后活性差异。
   - **创新状态**: unverified

4. **名称**: TF协同结合的k-mer簇互作模型
   - **来源局限/观察**: K-PROB仅考虑加性效应，未建模TF–TF协同结合；真实调控中多个TF常协同作用于同一启动子。
   - **核心假设**: k-mer簇间的交互项可捕获TF协同结合效应，提升表达预测精度。
   - **初步方法**: 在K-PROB的Bayesian框架中引入k-mer簇交互项（如成对或高阶交互），使用稀疏正则化控制复杂度。
   - **验证方式**: 与已知TF协同对（如NLP与bHLH）比较，验证交互项是否识别已知协同关系。
   - **创新状态**: unverified

5. **名称**: 跨物种cis调控变异的迁移学习框架
   - **来源局限/观察**: K-PROB在玉米和大豆中独立应用，未利用跨物种保守的调控信息。
   - **核心假设**: 跨物种迁移学习可提升低资源物种的CRE鉴定能力，尤其是缺乏pan-transcriptome的物种。
   - **初步方法**: 利用玉米和大豆的K-PROB结果作为源域，对目标物种（如高粱、小麦）进行迁移学习，共享k-mer簇特征。
   - **验证方式**: 在目标物种中进行DAP-seq或报告基因验证，比较迁移学习与从头训练的精度。
   - **创新状态**: unverified