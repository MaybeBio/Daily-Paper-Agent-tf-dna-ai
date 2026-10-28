## 01 基本信息
- **标题**：Towards a comprehensive regulatory map of Mammalian Genomes
- **作者**：Goncalves, Tassia Mangetti; Stewart, Casey L; Baxley, Samantha D; Xu, Jason; Li, Daofeng; Gabel, Harrison W; Wang, Ting; Avraham, Oshri; Zhao, Guoyan
- **单位**：未提供（据致谢推测含 Washington University School of Medicine, WUSTL）
- **期刊/平台**：Research Square（预印本）
- **年份**：2023-10-16
- **论文类型**：方法学 + 基因组注释资源论文
- **领域**：基因组学、基因调控、顺式调控模块（CRM）预测
- **关键词**：Cis-regulatory modules (CRMs)、CRM预测、哺乳动物基因组、转录因子结合位点（TFBS）、无训练数据算法
- **DOI/ID**：10.21203/rs.3.rs-3294408/v1
- **代码**：未提供（数据可视化于 WashU Epigenome Browser，链接见 Data availability）
- **数据**：WashU Epigenome Browser 会话链接（Human: hg38-s.json；Mouse: mm10-s.json）
- **阅读日期**：2025-01-27（按当前日期）
- **在该课题方向中的位置**：本文属于「蛋白质-DNA互作 × 计算方法」中的**无训练数据（training data-free）的CRM/TFBS聚类预测**方向。与TF–DNA结合机制的直接关联在于：其预测单元是TFBS富集区（CRM），核心输入是序列保守性和TFBS基序密度，而非实验测定的结合亲和力或结构信息。对TF–DNA课题的可迁移点在于：①提供了一种不依赖已知CRM标注的、基于序列特征的调控元件预测框架；②其CRM-TF-靶基因关联分析（无监督聚类 + 通路富集）可作为TF结合位点功能注释的参考流程。

## 02 一句话总结
本文开发了无训练数据的算法 MrMOD，仅以哺乳动物基因组序列（人和小鼠）为输入，通过系统发育足迹法（PhyloNet）鉴定保守TFBS基序并聚类为高分辨率CRM（平均<220 bp），用21套正交实验数据集验证其高灵敏度与富集度，并展示其可指导转基因报告实验设计。

## 03 研究问题
- **具体问题**：哺乳动物基因组中顺式调控模块（CRM）缺乏类似基因模型的固定参考注释（reference CRM models），导致不同实验、不同peak calling程序产生的调控元件位置和边界不一致，难以跨条件比较。
- **为什么重要**：CRM控制基因表达的时空特异性，其变异与癌症、神经发育疾病等密切相关；缺乏固定参考模型阻碍了调控基因组学的系统比较和功能解析。
- **现有方法不足**：①实验方法（报告基因、ChIP-seq、ATAC-seq等）只能采样部分细胞/组织/条件，无法覆盖全部时空状态；②计算方法的三大类（比较基因组学、基序依赖、基序盲）均需训练数据或先验知识，且大多依赖特定组织/细胞类型的表观遗传数据。
- **精确研究问题（Can...?）**：Can we predict a comprehensive, position-fixed set of cis-regulatory modules in mammalian genomes using only genomic sequences, without any training data or tissue-specific epigenetic information, and achieve high accuracy validated by orthogonal experimental datasets?

## 04 背景与发展脉络
*（注：以下脉络基于本文框架，未做外部系统核验，标注为「仅本文框架」）*

1. **实验定义CRM阶段**：经典报告基因实验（如VISTA Enhancer Browser）定义了少量高置信增强子，但通量低、覆盖有限。
2. **高通量表观基因组阶段**：ChIP-seq、DNase-seq、ATAC-seq、STARR-seq、MPRA等产生海量候选调控元件，但依赖peak calling，不同程序/参数/批次间peak边界不一致，且只能反映采样时的细胞状态。
3. **计算预测阶段**：
   - 比较基因组学方法：依赖序列保守性，无法发现新进化CRM；
   - 基序依赖方法：需已知TF基序库，且基序聚类阈值难定；
   - 基序盲方法：需已知CRM作为训练集，受限于已有标注的覆盖度。
4. **本文主张的位置**：提出「无训练数据 + 仅序列输入 + 固定位置输出」的第三类方案——MrMOD，将CRM预测从「依赖实验数据的归纳」转向「基于序列内在特征的演绎」，输出类似基因模型的固定参考CRM（refCRM）。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 缺乏固定CRM参考模型 | 不同peak calling程序/参数产生不同peak位置和长度；跨实验比较困难 | 实验方法依赖peak calling，无类似基因模型的固定参考 | Background 第2段；Discussion 第2段 |
| 实验方法覆盖不全 | 无法采样所有细胞类型、发育阶段、刺激条件 | 试剂、起始材料、技术限制 | Background 第2段 |
| 计算预测依赖训练数据 | 多数方法需已知CRM、TF基序或表观遗传数据作为输入 | 已知标注有限，限制预测范围 | Background 第3段 |
| 保守性方法漏检新CRM | 比较基因组学无法发现物种特异或新进化的CRM | 功能序列不一定保守 | Background 第3段 |
| CRM边界不精确 | 实验定义的CRM通常较大（如VISTA平均>2 kb），难以定位最小功能单元 | 报告基因片段包含多个功能元件 | Results 图7；Discussion 第3段 |

## 06 核心思想
1. **表面方法**：两阶段流程——先用PhyloNet在哺乳动物三基因组（人、小鼠、大鼠）中系统发育足迹法鉴定保守TFBS基序（5,143个非冗余PWM），再用CERMOD算法基于基序密度Z-score聚类预测CRM。
2. **核心洞察**：CRM的本质是TFBS的局部富集，而TFBS的保守性可以通过多序列比对和系统发育足迹法从序列本身提取，无需任何实验标注。因此，可以用「序列内在特征」替代「实验训练数据」，实现全基因组、无偏、固定位置的CRM预测。
3. **可能的普适教训 [Analysis]**：①「固定参考模型」思维——如同基因模型之于RNA-seq，调控元件也需要类似参考坐标系才能实现跨实验可比性；②「无训练数据」策略在标注稀缺的基因组区域（如非编码区）具有独特优势，但代价是预测精度受限于基序数据库质量和保守性假设；③将预测结果作为「先验」指导实验设计（如CRM亚片段选择），可显著缩小实验搜索空间。

## 07 方法总览
- **输入**：人（hg38）、小鼠（mm10）基因组序列；小鼠为锚定基因组；大鼠序列用于三物种比较。
- **输出**：全基因组CRM预测（CRMfull，人约607万、小鼠约555万）；每个CRM有固定基因组坐标、长度（平均~216 bp）、Z-score。
- **模块**：
  1. 直系同源基因鉴定（BioMart）
  2. 启动子上游5 kb间区序列提取
  3. PhyloNet系统发育足迹法 → 保守TFBS基序（PWM）
  4. 基序去冗余（ALLR统计）→ 5,143个非冗余PWM
  5. CERMOD算法 → 基于基序密度Z-score的CRM预测
  6. 对照区域生成（CTRL：非CRM区域，匹配长度分布）
  7. 多数据集验证（21套正交数据）
  8. 无监督聚类（Seurat）→ CRM功能注释
- **文字流程**：提取三物种直系同源基因上游5 kb序列 → PhyloNet鉴定保守基序 → 去冗余得5,143 PWM → CERMOD扫描全基因组，计算每个位置的基序密度Z-score，Z>2.33（p<0.01单尾）的峰延伸至Z=0边界，合并为CRM → 生成匹配的CTRL对照 → 用ExpCRMs、VISTA、ENCODE cCREs、Cistrome、ATAC-seq、scATAC-seq等21套数据计算灵敏度与OR → 对小鼠chr17 CRM做TFBS扫描 + Seurat聚类 + 通路富集。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| PhyloNet基序发现 | 鉴定三物种保守的TFBS基序 | 提供无训练数据的TFBS先验 | 输入：三物种直系同源上游序列；输出：5,143个非冗余PWM | Results 第1段；Methods | 移除后无基序输入，CRM预测无法进行（核心依赖） |
| 基序去冗余（ALLR） | 合并高度相似的PWM | 避免同一TF的多个相似基序重复计数 | 输入：PhyloNet原始基序；输出：去冗余后5,143 PWM | Methods | 不去冗余会高估基序密度，导致CRM边界偏移 [预期效应] |
| CERMOD CRM预测 | 基于基序密度Z-score聚类 | 将离散TFBS聚合成模块级调控单元 | 输入：PWM + 基因组序列；输出：CRMfull（固定坐标） | Results 图1C-D | 移除后无CRM输出（核心模块） |
| CTRL对照生成 | 生成匹配的非CRM对照区域 | 公平评估预测灵敏度与OR | 输入：非CRM基因组区域；输出：CTRL集 | Results 图2；Methods | 无对照则无法计算OR，验证不成立 |
| 多数据集验证 | 用21套正交数据计算灵敏度/OR | 证明预测的普适性和准确性 | 输入：CRMfull + 外部数据集；输出：灵敏度、OR、p值 | Results 图4；Tables 2-3 | 移除后预测准确性无法量化 |
| Seurat无监督聚类 | 基于TFBS组成对CRM分群 | 功能注释CRM，关联TF与靶基因 | 输入：chr17 CRM的TFBS丰度矩阵；输出：43个CRM簇 | Results 图5-6 | 移除后CRM缺乏功能注释，无法关联TF-靶基因 |
| 转基因报告实验 | 验证CRM亚片段功能 | 证明预测可指导实验设计 | 输入：hs52及其亚片段；输出：表达模式 | Results 图7 | 移除后缺乏体内功能验证（非核心计算模块） |

## 09 关键公式符号
*（注：原文未给出显式数学公式，以下为方法中隐含的统计量）*

1. **Z-score（基序密度显著性）**：
   - 符号：Z
   - 含义：某基因组位置周围基序密度相对于全基因组期望的偏离程度
   - 公式（隐含）：Z = (观测基序数 − 期望基序数) / 标准差
   - 阈值：Z > 2.33（对应p < 0.01，单尾）
   - 用途：判定CRM峰；来源：Methods「Whole-genome-wide CRM identification」

2. **ALLR（Average Log Likelihood Ratio）**：
   - 符号：ALLR
   - 含义：两个PWM矩阵相似性的统计量
   - 用途：基序去冗余、与已知数据库（TRANSFAC/CIS-BP）比对
   - 阈值：ALLR > 6.57 且 OLAP > 68.1% 判定为冗余
   - 来源：Methods「Comparison with transcription factor PWMs」

3. **OLAP（Overlap score）**：
   - 符号：OLAP
   - 含义：两个PWM比对区域的重叠百分比
   - 用途：与ALLR联合判定基序冗余
   - 来源：Methods

4. **超几何检验（Hypergeometric test）**：
   - 用途：PWM关联基因集与ChIP-Atlas TF靶基因集富集显著性
   - 阈值：FDR校正p < 0.05
   - 来源：Results 第1段；Methods

## 10 实验设计与证据链
- **数据集/群体**：
  - 基因组：人（hg38）、小鼠（mm10）、大鼠（用于三物种比较）
  - 验证数据（21套）：ExpCRMs（文献人工收集，小鼠97个、人60个）、VISTA Enhancer Browser（小鼠634、人998）、ENCODE cCREs、Cistrome Data Browser（ATAC-seq、DNase-seq、ChIP-seq H3K27ac/H3K4me1/H3K4me3）、ATAC-seq Atlas（小鼠）、scATAC-seq（小鼠脑、人45组织）
  - 分析区域：小鼠chr17（聚类分析）
- **指标**：灵敏度（sensitivity）、OR（odds ratio）、p值（卡方检验）、基因组覆盖率
- **基线/对照**：CTRL区域（非CRM、匹配长度分布与基因组特征分布）
- **预算/资源**：未提供（计算资源未说明）
- **骨干/仪器**：未提供（计算平台未说明）
- **oracle输入**：无（无监督预测，验证时使用实验数据作为金标准）
- **评测协议**：CRM与实验数据重叠（1bp或50%重叠阈值）；OR = (CRM∩实验)/(CTRL∩实验) 的比值

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| PWM与已知数据库比对 | PhyloNet基序代表真实TFBS | 与TRANSFAC、CIS-BP比对 | 16.3%与TRANSFAC、42.8%与CIS-BP相似 | 多数基序为已知TFBS | 58%基序未匹配已知数据库，可能为新基序或噪声 | Results 表1 |
| PWM关联基因与ChIP-Atlas富集 | PWM关联基因是TF真实靶基因 | 超几何检验，FDR<0.05 | 637个（12.4%）PWM显著富集 | 部分PWM对应真实TF-靶基因关系 | 87.6%未显著富集，可能因ChIP-Atlas覆盖不全 | Results 第1段 |
| CRM vs CTRL 对ExpCRMs的灵敏度 | CRM富集实验验证的调控序列 | 1bp/50%重叠，OR计算 | 小鼠OR=10.51（1bp）、8.40（50%）；人OR=5.23（1bp）、4.67（50%） | CRM显著富集已知功能调控序列 | 灵敏度非100%，部分CRM可能无功能或实验未覆盖 | Results 图4G-H；Tables 2-3 |
| CRM vs CTRL 对VISTA增强子的灵敏度 | CRM富集体内验证增强子 | 同上 | 小鼠OR=5.94-10.24；人OR=6.02-8.21 | CRM富集体内验证增强子 | VISTA增强子较大，可能含非功能序列 | Results 图4G-H；Tables 2-3 |
| CRM vs CTRL 对表观遗传peak的灵敏度 | CRM富集表观遗传标记 | 19套数据（ENCODE cCREs、Cistrome、ATAC等） | 所有数据集OR>1，多数p<2.2e-16 | CRM富集多种表观遗传调控信号 | ENCODE cCREs在50%重叠时OR=0.97（人），可能因cCREs分辨率高 | Results 图4G-H；Tables 2-3 |
| chr17 CRM无监督聚类 | CRM可按TFBS组成功能分群 | Seurat聚类，43簇 | 各簇富集不同通路（如C17富集神经发育、癌症） | CRM簇对应不同调控功能 | 仅基于序列组成，未验证簇内CRM共调控 | Results 图5-6 |
| hs52亚克隆转基因实验 | CRM预测可指导实验设计 | 鸡胚电穿孔 | hs52.2和hs52.3驱动更受限表达 | 预测的CRM亚片段具有功能特异性 | 仅验证1个增强子，样本量小 | Results 图7 |

## 11 结论正确解读
- **任务范围**：本文任务是「预测」CRM，而非「验证」CRM功能。预测基于序列保守性和TFBS密度，不涉及TF-DNA结合的物理化学机制（如结合亲和力、构象变化）。
- **oracle/真值输入**：验证阶段使用了实验数据（ExpCRMs、VISTA、表观遗传peak）作为金标准，但预测阶段完全无监督。
- **端到端状态**：预测→验证→实验指导的完整流程已跑通，但验证覆盖度有限（仅157个文献CRM + 1个增强子亚克隆实验）。
- **算力成本**：未报告。
- **历史数据依赖**：依赖基因组序列比对（人/鼠/大鼠）和已知PWM数据库（CIS-BP/TRANSFAC），不依赖表观遗传训练数据。
- **模型依赖**：依赖PhyloNet和CERMOD两个已有算法，MrMOD本身是流程整合而非新算法。
- **最难情形**：非保守CRM（物种特异调控元件）无法被PhyloNet发现；短CRM（<63 bp）可能漏检；高重复序列区域的CRM预测不可靠。
- **群体/领域边界**：仅适用于哺乳动物（人、小鼠、大鼠）；不适用于非哺乳动物或病毒基因组。
- **不确定性**：CRM边界由Z-score阈值决定，不同阈值会产生不同结果；预测的CRM中可能包含大量假阳性（非功能序列）。
- **有边界的复述**：MrMOD能在无训练数据条件下，以约42%基因组覆盖率预测哺乳动物CRM，其预测在已知实验数据上显著富集（OR 1.2-10.5），并能指导增强子亚克隆实验，但预测的CRM集合尚未经过系统体内功能验证，不能视为最终的功能调控元件注释。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 预测CRM的假阳性 | 部分预测CRM可能无功能 | 需要更多实验验证 | Discussion 第3段（"biological validation is essential"） |
| 实验验证覆盖有限 | 仅1个增强子亚克隆实验 | 未明确 | Results 图7 |
| 保守性依赖 | 无法检测非保守CRM | 未明确 | Background 第3段（暗示比较基因组学局限） |
| 分析限于chr17 | 聚类分析仅在小鼠chr17进行 | 扩展到全基因组 | Results 第3段（"narrowed our analysis to the smaller mouse chromosome 17"） |
| 数据资源有限 | 文献CRM数量少（157个） | 未明确 | Results 第2段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|----------------------|----------|----------|------|
| 验证数据集中于启动子近端区域（上游5 kb） | CRM预测可能偏向启动子近端调控，遗漏远端增强子 | 远端增强子在发育调控中至关重要 | 用STARR-seq或MPRA在全基因组范围（含远端）验证CRM | Methods「Intergenic region sequences of up to 5 kb」 |
| 42%基因组覆盖率过高 | 可能包含大量假阳性；「非功能区域」定义模糊 | 过高的覆盖率降低实用性 | 用随机区域作为对照计算假阳性率；用CRISPR干扰验证随机抽样CRM | Results 图1C |
| 无训练数据既是优点也是风险 | 缺乏实验数据约束可能导致预测偏离真实调控逻辑 | 训练数据可提供功能先验 | 与监督学习方法（如EnhancerFinder）在相同验证集上比较 | Background 第3段 |
| 基序来源依赖CIS-BP/TRANSFAC | 已知基序库覆盖不全，可能漏检新型TF结合模式 | TF-DNA结合特异性远未被完全表征 | 整合de novo motif发现（如HOMER） | Methods「Comparison with transcription factor PWMs」 |
| 聚类分析仅用TFBS组成，未考虑序列上下文 | 同一TFBS在不同染色质环境下功能可能不同 | 调控逻辑依赖染色质状态 | 整合染色质可及性（ATAC）、组蛋白修饰数据到聚类特征 | Results 第3段 |
| 未与现有CRM数据库（如ENCODE cCREs）做系统比较 | 无法评估相对已有资源的增量价值 | 实用性需与现有资源对比 | 计算与cCREs、FANTOM5 enhancers的Jaccard重叠 | Results 图4（仅OR，无重叠率） |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **「固定参考模型」思维（可迁移）**：如同基因模型之于RNA-seq，TF–DNA结合研究也需要「固定参考结合位点」坐标系。可将MrMOD的refCRM概念迁移为「refTFBS」——为每个TF提供全基因组固定的、无训练数据依赖的结合位点参考集，使不同ChIP-seq、SELEX、MPRA实验可跨条件直接比较。

2. **无训练数据预测策略（可迁移）**：在TF–DNA结合数据稀缺的物种或细胞类型中，可借鉴「系统发育足迹法 + 基序密度聚类」的流程，仅用多序列比对和已知PWM数据库预测候选结合区域，作为实验筛选的起点。

3. **CTRL对照设计（可迁移）**：生成与预测区域长度分布、基因组特征分布完全匹配的阴性对照，是公平评估预测精度的关键。该设计可直接迁移到TF结合位点预测模型的评估中。

4. **多源正交验证框架（可迁移）**：用文献CRM、VISTA、表观遗传peak、scATAC等多层次数据交叉验证，比单一数据集验证更稳健。对TF–DNA研究，可类似地用ChIP-seq、HT-SELEX、甲基化干扰、MPRA等多维度数据验证预测的结合位点。

5. **预测指导实验设计（可迁移）**：用预测CRM亚分割大型实验增强子（如VISTA hs52），可定位最小功能单元。对TF–DNA研究，可用预测的亚结合位点设计突变实验，精确定位关键核苷酸。

6. **无监督聚类功能注释（可迁移）**：基于TFBS组成对CRM聚类，可发现共调控模块。对TF–DNA研究，可对全基因组TF结合谱做类似聚类，发现协同结合的TF组合。

## 15 与已有知识连接
- **与ENCODE项目的关系**：本文的cCREs验证数据来自ENCODE，但MrMOD预测不依赖ENCODE数据，两者是正交关系。ENCODE cCREs在50%重叠时OR=0.97（人），提示MrMOD与ENCODE定义的调控元件存在差异，可能反映两种方法捕捉不同调控特征。
- **与CIS-BP数据库的关系**：CIS-BP（Weirauch et al., 2014, Cell）提供TF结合偏好PWM，本文使用CIS-BP进行基序比对和TFBS扫描，是TF–DNA结合特异性知识库的直接应用。
- **与PhyloNet的关系**：PhyloNet（Zhang et al., 2013, NAR）是系统发育足迹法工具，本文将其用于哺乳动物保守基序发现，是该方法的规模化应用。
- **与CERMOD的关系**：CERMOD（Goncalves et al., 2015, NAR）是本文作者前期开发的CRM预测算法，本文将其从单物种扩展到哺乳动物全基因组。
- **与VISTA Enhancer Browser的关系**：VISTA（Visel et al., 2007, Nat Genet）是转基因增强子验证数据库，本文使用其作为金标准之一，并展示预测可指导VISTA增强子的亚分割。
- **与单细胞ATAC-seq的关系**：本文使用小鼠脑和人类组织的scATAC-seq数据验证，连接了群体细胞调控元件与单细胞染色质可及性。
- **与TF–DNA结合机制研究的关联 [Analysis]**：本文不涉及结合亲和力、结合动力学或结构机制，但其「TFBS聚类→CRM」的层次化视角提示：TF–DNA结合研究不应仅关注单一位点，而应关注位点簇（CRM）层面的协同调控逻辑。这一视角与「增强子-启动子互作」「TF协同结合」等研究方向互补。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA结合位点的「固定参考坐标系」构建
   - **来源局限/观察**：ChIP-seq peak calling在不同实验间不可比；缺乏类似基因模型的固定TFBS参考。
   - **核心假设**：基于系统发育足迹法 + PWM密度聚类，可为每个TF构建全基因组固定的候选结合位点参考集（refTFBS），其精度可通过多实验数据验证。
   - **初步方法**：借鉴MrMOD流程，将PhyloNet基序发现 + CERMOD聚类应用于单个TF的已知PWM，输出全基因组refTFBS；用ChIP-seq、HT-SELEX、MPRA数据计算灵敏度与OR。
   - **验证方式**：与现有TFBS数据库（如JASPAR、ENCODE ChIP-seq）比较重叠率；用CRISPR突变验证随机抽样位点。
   - **创新状态**：unverified（需验证可行性）

2. **候选名称**：CRM-TF-靶基因三层调控网络的无监督解析
   - **来源局限/观察**：MrPOST仅在小鼠chr17做了聚类分析，且未系统验证TF-CRM-靶基因关系。
   - **核心假设**：基于TFBS组成的CRM聚类可揭示协同TF组合，且聚类内CRM的靶基因共享生物学通路。
   - **初步方法**：将MrPOST聚类扩展到全基因组；对每簇CRM做TFBS富集分析（如HOMER）；用Hi-C数据连接CRM与靶基因；对靶基因做通路富集。
   - **验证方式**：与已知TF协同结合文献比较；用CRISPR干扰验证簇内CRM对靶基因表达的影响。
   - **创新状态**：unverified（部分基于本文chr17结果外推）

3. **候选名称**：预测CRM指导的增强子亚分割与最小功能单元定位
   - **来源局限/观察**：本文仅验证了1个VISTA增强子（hs52）的亚分割。
   - **核心假设**：预测CRM边界可精确定位增强子内的最小功能单元，且这些单元对应特定TFBS组合。
   - **初步方法**：选取多个VISTA增强子，用MrPOST预测亚CRM；对每个亚CRM做转基因报告实验；比较亚CRM与全长增强子的表达模式。
   - **验证方式**：统计亚CRM驱动表达的特异性与全长增强子的一致性；突变关键TFBS验证功能。
   - **创新状态**：unverified（需扩大样本量）

4. **候选名称**：跨物种CRM保守性与TF–DNA结合共进化分析
   - **来源局限/观察**：MrPOST基于人/鼠/大鼠保守性，但未分析CRM的跨物种保守程度与TFBS turnover。
   - **核心假设**：保守CRM中的TFBS组合在哺乳动物中稳定，而物种特异CRM中的TFBS反映新进化调控。
   - **初步方法**：比较人/鼠CRM的直系同源区域；分析TFBS gain/loss；关联TFBS turnover与靶基因表达差异。
   - **验证方式**：与已知TFBS进化研究比较；用报告基因验证物种特异CRM的活性。
   - **创新状态**：unverified（需跨物种数据）

5. **候选名称**：无训练数据CRM预测与表观遗传数据的互补性分析
   - **来源局限/观察**：MrPOST与ENCODE cCREs在50%重叠时OR=0.97（人），提示两种方法捕捉不同调控特征。
   - **核心假设**：序列保守性预测的CRM与表观遗传定义的调控元件互补，两者交集和差集分别对应不同调控机制。
   - **初步方法**：对MrPOST CRM与cCREs做四象限分析（交集/差集）；比较各象限的序列特征、TFBS组成、靶基因功能。
   - **验证方式**：用STARR-seq或MPRA验证各象限的增强子活性。
   - **创新状态**：unverified（基于本文OR=0.97的观察）