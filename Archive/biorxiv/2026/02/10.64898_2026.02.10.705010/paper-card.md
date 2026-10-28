## 01 基本信息

- **标题**：Distinct DNA-binding syntax and chromatin remodeling capacities of bHLH transcription factors in cell differentiation, reprogramming and cancer
- **作者与单位**：Xabier de Martin; Joel Martínez-Miralles; Serafima Beletskaya; Adrià Navarro; Jan Izquierdo; Baldomero Oliva; Gabriel Santpere（单位未在材料中明确列出，部分作者隶属西班牙巴塞罗那自治大学遗传学博士项目）
- **期刊/预印本平台**：bioRxiv
- **年份**：2026-02-11
- **论文类型**：预印本（研究论文）
- **领域**：转录因子（bHLH家族）DNA结合机制、染色质重塑、细胞分化与重编程、癌症
- **关键词**：bHLH、E-box、ChIP-seq、染色质可及性、DNA甲基化、核小体、pioneer factor、MYC、TWIST
- **DOI/arXiv 号**：10.64898/2026.02.10.705010
- **代码**：https://github.com/SantpereLab/bHLH_Induction
- **数据**：ChIP-ATLAS（74个ChIP-seq数据集）、GEO（ATAC-seq、RNA-seq、甲基化数据，具体编号见补充表S1-S6）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「TF–DNA结合机制 × 多组学整合 + 结构建模」方向，聚焦bHLH家族E-box变体的DNA结合语法（motif syntax）与染色质可及性/核小体占位的关系，提出E-box亲和力依赖的pioneer活性模型，并揭示DNA甲基化驱动的MYC增强子入侵机制。对TF–DNA互作课题的可迁移价值在于：建立了从ChIP-seq峰值、motif变体、染色质状态到转录输出的系统性分析框架，并引入AlphaFold3+ModCRE的结构模拟方法评估核小体结合能力。

## 02 一句话总结

本文通过整合74个bHLH诱导ChIP-seq实验与匹配的染色质可及性、甲基化、转录组数据，结合AlphaFold3结构预测和ModCRE核小体建模，发现CAT-和CAG-preferring bHLH因子通过高亲和力E-box变体（如CAT-CAT、CAT-CAG）结合并重塑关闭染色质，而CAC-preferring因子（MYC、HEY）主要限于开放染色质，且DNA甲基化将MYC从CAC-CAC重定向至CAT-CAC以实现增强子入侵。

## 03 研究问题

- **具体问题**：bHLH转录因子家族内部，不同亚类（CAT-/CAG-/CAC-preferring）的DNA结合语法（E-box变体选择、motif密度、间距）如何决定其结合关闭染色质（pioneer活性）和重塑染色质的能力？DNA甲基化如何影响这一过程？
- **为什么重要**：bHLH因子是细胞命运决定、重编程和癌症的核心调控因子，但此前缺乏跨因子的系统性比较，无法解释为何某些bHLH（如NEUROD2、ASCL1）具有pioneer活性而另一些（如MYC）没有。
- **现有方法不足**：已有研究多为单个因子的案例分析，缺乏统一的E-box变体分辨率分析框架；对核小体相互作用的评估缺乏结构层面的验证；DNA甲基化对bHLH结合的影响未被系统研究。
- **精确研究问题**：Can the E-box variant syntax (type, density, spacing) of bHLH transcription factors predict their capacity to engage and remodel closed chromatin, and does CpG methylation redirect CAC-preferring factors toward non-canonical E-box variants?

## 04 背景与发展脉络

*注：以下脉络基于本文框架及其引用的文献，部分经外部核验。*

1. **bHLH家族与E-box分类**（经外部核验）：bHLH因子以二聚体形式结合CANNTG E-box，根据中心二核苷酸分为CAT、CAG、CAC等亚类。经典工作（如Murre et al. 1989）确立了bHLH-DNA结合的基本框架。
2. **pioneer factor概念**（经外部核验）：pioneer因子能在关闭染色质上结合并启动重塑，如OCT4、SOX2、FOXA等。bHLH家族中NEUROD2、ASCL1被报道具有pioneer活性，但机制不清。
3. **E-box变体与染色质状态关联**（本文框架）：本文作者前期工作（de Martin et al.）提出NEUROD2通过CAT-CAT/CAT-CAG结合关闭染色质；Casey et al. (2018) 报道ASCL1/MYOD1在ESC中通过CAG-CAC结合关闭染色质。
4. **核小体结合的结构约束**（经外部核验）：核小体DNA的周期性弯曲（~10bp螺旋周期）影响TF结合位点的可及性；α-螺旋长度被认为影响TF与核小体表面的空间冲突。
5. **DNA甲基化与TF结合**（经外部核验）：CpG甲基化可阻碍或促进TF结合，但bHLH家族中此效应未被系统研究。
6. **本文主张的位置**：首次在bHLH全家族尺度上统一E-box变体语法、染色质可及性、甲基化、核小体结构建模和转录输出，提出「E-box亲和力依赖的pioneer模型」，并挑战「α-螺旋长度决定pioneer活性」的既有假说。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 缺乏跨bHLH因子的统一比较框架 | 各研究使用不同细胞类型、不同motif分析工具，难以横向比较 | 缺乏统一的E-box变体分辨率分析流程和标准化数据整合 | Results "Collection of bHLH ChIP-seq data"；补充表S5显示仅3/74实验进行了E-box变体与染色质状态关联分析 |
| pioneer活性机制不清 | 同为bHLH，NEUROD2有pioneer活性而MYC没有，原因不明 | 既有模型归因于α-螺旋长度，但本文数据显示螺旋长度与核小体结合能力无一致关联 | Results "bHLH interaction with nucleosomes"；图4B-C |
| DNA甲基化对bHLH结合的影响被忽视 | 甲基化数据未与ChIP-seq整合分析 | 缺乏跨组学数据整合方法 | Results "bHLH interaction with methylated DNA"；图3A-B |
| 核小体结合能力缺乏结构验证 | 仅凭ChIP-seq无法区分直接核小体结合与染色质开放后的次级结合 | 缺乏高分辨率核小体结构建模工具的应用 | Methods "ModCRE"；图4C |
| E-box变体与转录输出的因果关系不明 | 观察到变体偏好差异，但未连接至基因表达变化 | 缺乏motif变体→染色质重塑→转录激活的端到端分析 | Results "Relationship between motif architecture and transcriptional activation"；图5B |

## 06 核心思想

1. **表面方法**：整合74个bHLH诱导ChIP-seq数据集，以E-box变体（10种中心二核苷酸组合）为基本分析单元，结合匹配的ATAC-seq/H3K27ac（染色质可及性）、WGBS（甲基化）、RNA-seq（转录输出），并引入AlphaFold3结构预测和ModCRE核小体建模。

2. **核心洞察**：
   - bHLH因子的pioneer活性由其**偏好E-box变体的内在亲和力**决定，而非α-螺旋长度。高亲和力变体（如CAT-CAT对NEUROD2）允许在关闭染色质上竞争性结合；低亲和力变体（如CAC-CAC对MYC）不足以克服核小体屏障。
   - **DNA甲基化是E-box变体选择的开关**：CpG甲基化阻断CAC-CAC（含CpG）的识别，迫使MYC转向CAT-CAC（不含CpG），从而在高度甲基化的增强子区域实现入侵。
   - **E-box密度和间距**（如TWIST的5bp周期）是协同结合和关闭染色质入侵的附加语法层。

3. **可能的普适教训** [Analysis]：
   - TF结合特异性的研究不应止步于consensus motif，而应细化到**变体分辨率（variant-resolution）**，因为不同变体可能对应完全不同的染色质结合模式。
   - Pioneer活性的评估需要**结构层面的核小体冲突分析**（如ModCRE），而非仅凭ChIP-seq的染色质可及性关联。
   - 表观遗传修饰（甲基化）可以**重编程TF的motif偏好**，这为理解癌症中TF靶标重塑提供了新机制。

## 07 方法总览

- **输入**：74个bHLH诱导ChIP-seq数据集（17个因子，来自ChIP-ATLAS）；匹配的ATAC-seq/H3K27ac（染色质可及性）、WGBS（甲基化）、RNA-seq（转录组）；HT-SELEX/methyl-SELEX体外结合数据；AlphaFold3预测的bHLH二聚体结构。
- **输出**：每个因子的E-box变体偏好谱、染色质可及性关联、甲基化效应、核小体结合模式、转录激活能力、跨因子聚类关系。
- **模块**：数据收集与QC → motif变体分析 → 染色质可及性分层 → 甲基化整合 → 核小体距离分析 → 结构建模（AlphaFold3+ModCRE）→ 转录组关联 → 跨研究整合。
- **训练**：无监督学习（聚类、回归），无端到端深度学习模型。
- **工具**：ChIP-ATLAS、bwa-mem、samtools、deepTools、bedtools、MACS2、DESeq2、Limma、clusterProfiler、AlphaFold3、ModCRE、liftOver。
- **反馈回路**：无显式反馈回路；分析为流水线式。
- **假设**：ChIP-seq峰值中E-box的中心富集反映直接结合；pre-induction染色质可及性代表结合前状态；AlphaFold3结构可用于核小体冲突评估。

**文字流程**：从ChIP-ATLAS检索并筛选诱导实验 → 对每个实验的peak集进行E-box变体扫描和中心性评估 → 获取匹配的pre-induction染色质可及性数据，将peak按可及性四分位分层 → 对每个peak计算CpG甲基化水平 → 使用核小体定位图计算peak到核小体dyad的距离分布 → 用AlphaFold3预测bHLH二聚体结构，ModCRE评估与核小体的空间冲突 → 对每个实验计算motif变体富集与染色质可及性/重塑的回归关系 → 整合RNA-seq数据评估转录激活 → 跨实验聚类和功能注释。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| E-box变体扫描与中心性分析 | 识别peak中10种E-box变体的分布和中心富集 | 区分真实结合位点与背景；变体分辨率是核心创新 | 输入：peak序列；输出：变体频率、中心性得分 | Results 图1A、图S2 | 无法区分变体偏好，回到consensus motif水平，丢失关键信息 |
| 染色质可及性分层 | 将peak按pre-induction可及性分为四分位 | 定义「关闭染色质结合」的操作性标准 | 输入：ATAC-seq/H3K27ac信号；输出：peak分层标签 | Results 图2A | 无法评估pioneer活性 |
| 甲基化整合分析 | 计算peak内CpG甲基化水平并与E-box变体关联 | 揭示甲基化对变体选择的调控 | 输入：WGBS数据；输出：甲基化-E-box变体关联矩阵 | Results 图3A-B、图S5 | 无法解释MYC增强子入侵机制 |
| 核小体距离分析 | 计算peak到核小体dyad的距离分布 | 区分dyad结合与linker结合模式 | 输入：核小体定位图；输出：距离分布曲线 | Results 图4A | 无法评估核小体结合模式 |
| AlphaFold3+ModCRE结构建模 | 预测bHLH二聚体结构并评估核小体结合冲突 | 提供结构层面的pioneer活性解释 | 输入：蛋白序列；输出：核小体结合可行性评分 | Results 图4B-C、Methods "ModCRE" | 无法区分螺旋长度效应，回到经验性假说 |
| 多变量回归（motif→染色质/转录） | 同时评估10种E-box变体对染色质可及性和转录激活的贡献 | 分离各变体的独立效应 | 输入：变体富集矩阵+表型矩阵；输出：回归系数 | Results 图5A-B、图S7 | 无法建立变体与功能的定量关联 |
| 跨研究聚类与功能注释 | 按E-box偏好和染色质行为对17个因子聚类 | 识别亚类共性 | 输入：各因子特征矩阵；输出：聚类树、GO注释 | Results 图5C、图S8 | 无法泛化到家族层面 |

**消融效应区分**：文中未进行显式消融实验；「移除后影响」为基于分析逻辑的预期效应 [Analysis]。

## 09 关键公式符号

本文核心分析为统计回归框架，无复杂数学公式。关键概念如下：

- **E-box变体**：CANNTG，其中NN为10种可能的二核苷酸组合（AA, AC, AG, AT, CA, CC, CG, GA, GC, GG，排除GT/TG等非回文组合）。符号：E_NN。
- **中心性得分（Centrality score）**：基于E-box到peak summit距离分布的K-S检验统计量。符号：D_KS。用途：衡量变体是否在peak中心富集。直觉：真实结合位点应集中在summit附近。
- **Motif富集指数（Motif enrichment index）**：log[(count_peak+1)/(count_flanking+1)]。用途：衡量变体在peak内相对侧翼的富集程度。直觉：正值表示peak内富集。
- **多变量线性回归**：log(accessibility_change) ~ Σ β_i × E_i_enrichment + covariates。用途：分离各E-box变体对染色质可及性变化的独立贡献。符号：β_i为变体i的回归系数。
- **核小体距离**：peak summit到最近核小体dyad的距离（bp）。用途：评估结合位点相对核小体的位置偏好。
- **ModCRE冲突阈值**：4Å接触距离标准，允许最多2个空间冲突。用途：判断TF二聚体能否在核小体表面结合。

## 10 实验设计与证据链

- **数据集**：74个ChIP-seq实验（17个bHLH因子）；匹配的ATAC-seq/H3K27ac（21个实验有pre/post数据）；WGBS（27个实验）；RNA-seq（21个实验）；HT-SELEX/methyl-SELEX（来自Yin et al. 2017）；核小体定位图（mESC，Voong et al.）。
- **指标**：E-box中心性（K-S p值）、motif富集指数、染色质可及性四分位、甲基化百分比、核小体距离分布、表达log2 fold change。
- **基线**：peak侧翼区域的E-box频率作为背景；均匀分布作为中心性零假设。
- **评测协议**：无独立测试集；采用跨实验一致性检验和与体外SELEX数据的交叉验证。

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| E-box变体中心性分析 | 不同bHLH亚类偏好不同E-box变体 | 74个实验，10种变体中心性比较 | CAT-preferring因子富集CAT-CAT/CAT-CAG；CAC-preferring富集CAC-CAC | 变体偏好是亚类特异性的 | 未证明变体偏好是细胞类型无关的 | Results 图1A、图S2 |
| 染色质可及性分层 | CAT/CAG-preferring因子能结合关闭染色质 | 按pre-induction可及性四分位比较peak分布 | CAT/CAG因子在低可及性区域有显著peak富集；CAC因子主要在高可及性区域 | pioneer活性是CAT/CAG亚类共性 | 未直接测量核小体占位变化 | Results 图2A |
| 甲基化-E-box关联 | 甲基化重定向MYC至CAT-CAC | 高甲基化vs低甲基化区域的E-box变体分布 | 高甲基化区域CAC-CAC减少、CAT-CAC增加 | 甲基化驱动MYC变体转换 | 未证明因果关系（仅相关性） | Results 图3A-B |
| 核小体距离分析 | bHLH因子偏好核小体侧翼/linker | peak到dyad距离分布 | 多数因子在dyad处有耗尽、在linker处富集 | 结合发生在核小体侧翼 | 未区分主动核小体结合与被动linker偏好 | Results 图4A |
| AlphaFold3+ModCRE | 螺旋长度不决定核小体结合能力 | 15个因子结构预测，比较螺旋长度与核小体结合评分 | 螺旋长度与核小体结合能力无一致关联 | 挑战螺旋长度假说 | 结构预测精度有限，需实验验证 | Results 图4B-C |
| 回归分析（motif→染色质重塑） | E-box变体富集预测染色质可及性变化 | 21个实验，pre/post ATAC-seq | CAT-CAT/CAT-CAG富集与可及性增加正相关 | 高亲和力变体驱动重塑 | 未排除其他因子（如共调控因子）的贡献 | Results 图5A、图S7 |
| 回归分析（motif→转录激活） | E-box变体富集预测基因表达变化 | 21个实验，RNA-seq | 高亲和力变体与靶基因激活正相关 | 变体语法连接至转录输出 | 未区分直接与间接转录效应 | Results 图5B |
| 跨实验聚类 | 因子按E-box语法聚类为功能亚类 | 17个因子，基于变体偏好和染色质行为 | 聚类与已知功能（神经、肌肉、癌基因）一致 | 语法决定功能 | 聚类受数据量不平衡影响 | Results 图5C |

## 11 结论正确解读

- **任务范围**：本文仅覆盖bHLH家族17个因子在诱导过表达条件下的结合行为，不涵盖内源表达水平、其他TF家族、体内发育过程。
- **oracle/真值输入**：ChIP-seq peak作为结合事件的真值；pre-induction ATAC-seq作为染色质状态的代理；SELEX数据作为体外亲和力参考。这些均为间接测量。
- **端到端状态**：非端到端；分析为模块化流水线，各步骤独立验证。
- **算力成本**：未报告；AlphaFold3预测和ModCRE建模为计算密集型，但未提供具体资源需求。
- **历史数据依赖**：依赖ChIP-ATLAS中第三方数据，各实验的抗体质量、过表达水平、细胞类型存在异质性。
- **模型依赖**：回归模型假设E-box变体效应为线性可加，未考虑非线性交互。
- **最难情形**：低ChIP-seq信噪比的实验（如HEY因子）可能低估其真实结合能力；高度甲基化的关闭染色质区域难以用现有ATAC-seq准确测量。
- **群体/领域边界**：结论限于培养细胞中的诱导过表达系统，不直接推广至体内生理条件。
- **不确定性**：甲基化驱动的变体转换主要基于相关性和体外SELEX，缺乏体内因果验证；核小体结合的结构预测未经过实验突变验证。

**有边界的复述**：在培养细胞诱导过表达系统中，bHLH因子的E-box变体偏好（而非α-螺旋长度）预测其结合关闭染色质的能力；DNA甲基化可重编程CAC-preferring因子的变体选择，但这一机制在体内的普遍性尚待验证。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 诱导过表达的非生理条件 | 过表达可能产生非生理性结合 | 未来需在生理表达水平下验证 | Discussion "Interpreting bHLH activity under induced conditions" |
| 缺乏体内因果验证 | 甲基化驱动的变体转换主要基于相关性和体外数据 | 需体内实验验证 | Discussion "A methylation-driven model explaining MYC enhancer invasion" |
| 数据异质性 | 74个实验来自不同实验室、不同细胞类型 | 需标准化数据生成 | Methods "ChIP-seq peaks QC" |
| 结构预测精度有限 | AlphaFold3预测未经过实验验证 | 需晶体结构或突变实验验证 | Methods "ModCRE" |
| 未覆盖全部bHLH家族 | 仅17个因子，未包含所有bHLH成员 | 需扩展至更多因子 | Results "Collection of bHLH ChIP-seq data" |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 「E-box亲和力决定pioneer活性」可能混淆相关与因果 | 高亲和力变体在关闭染色质上的富集可能反映的是结合后的染色质开放，而非结合前的能力 | 核心机制主张，影响pioneer因子设计 | 使用时间序列ChIP-seq（结合后0-2h）区分初始结合与次级结合 | Results 图2A仅显示稳态peak分布 |
| 甲基化驱动的变体转换缺乏直接证据 | 高甲基化区域的CAT-CAC富集可能由其他因素（如染色质状态、其他TF竞争）驱动 | 癌症中MYC靶标重塑的机制解释 | 体外核小体+甲基化DNA结合实验；CRISPR编辑CpG位点 | Results 图3A-B为相关性分析 |
| 核小体距离分析未区分主动与被动结合 | 所有TF都可能在linker区域富集，不一定是主动核小体结合 | 影响pioneer活性的定义 | 与随机背景模型比较；使用核小体竞争实验 | Results 图4A缺乏对照 |
| AlphaFold3+ModCRE的结论可能受结构预测误差影响 | 螺旋长度与核小体结合无关联可能反映预测精度不足而非真实生物学 | 挑战既有模型需更强证据 | 使用实验结构（X-ray/cryo-EM）验证；突变螺旋长度进行功能实验 | Methods "ModCRE"未报告预测置信度 |
| 回归模型未考虑共调控因子 | bHLH常与E蛋白等形成异源二聚体，不同二聚体组合可能改变变体偏好 | 变体语法可能不是因子内在属性 | 纳入二聚体伴侣表达水平作为协变量 | Results 图5A-B仅使用单一因子ChIP-seq |
| 跨实验整合可能引入批次效应 | 不同实验室的ChIP-seq、ATAC-seq协议差异可能影响peak调用和可及性测量 | 影响跨因子比较的效度 | 使用批次校正方法（如ComBat）；仅用同一实验室数据验证 | Methods未提及批次校正 |

## 14 学到什么

**Agent 提炼的知识候选**

1. **变体分辨率分析框架**：将TF motif分析从consensus水平细化到变体水平（如E-box的10种NN组合），可揭示亚类特异的结合语法。迁移到TF–DNA课题：对任意TF家族，应系统枚举所有可能的motif变体，而非仅使用PWM consensus。
2. **多组学整合策略**：ChIP-seq + pre-induction染色质可及性 + 甲基化 + RNA-seq的四层整合，可分离「结合偏好」与「功能输出」。迁移：研究TF–DNA互作时，应同时获取结合位点的表观遗传上下文，而非孤立分析peak。
3. **结构模拟评估核小体冲突**：AlphaFold3预测TF结构 + ModCRE核小体建模，可在无实验结构的情况下评估TF的核小体结合可行性。迁移：对缺乏实验结构的TF-DNA复合物，可用此流程预测pioneer潜力。
4. **甲基化作为motif选择开关**：CpG甲基化可阻断含CpG的motif（如CACGTG）并重定向至非CpG变体（如CATGTG）。迁移：在癌症或发育场景中，DNA甲基化状态应作为TF结合预测的关键特征。
5. **E-box间距语法**：TWIST的5bp间距对应核小体DNA的螺旋周期，提示TF二聚体/四聚体的协同结合模式。迁移：分析TF结合位点时应考虑位点间距的周期性，而非仅单点富集。
6. **pioneer活性的操作化定义**：用「pre-induction低可及性区域的peak富集」作为pioneer活性的可量化指标，避免模糊的定性描述。迁移：可复用于其他TF的pioneer能力评估。
7. **跨因子聚类揭示功能亚类**：基于E-box偏好和染色质行为的聚类与已知功能一致，提示TF的DNA结合语法可预测其生物学角色。迁移：对新TF，可通过结合语法聚类预测其功能类别。

## 15 与已有知识连接

- **Murre et al. (1989)**：bHLH-DNA结合的基础框架，本文在此基础上细化了E-box变体语法。
- **Casey et al. (2018)**：ASCL1/MYOD1在ESC中的pioneer活性研究，本文将其扩展至全家族比较。
- **de Martin et al.（作者前期工作）**：NEUROD2的CAT-CAT/CAT-CAG结合模式，本文验证并推广至其他CAT-preferring因子。
- **Yin et al. (2017)**：HT-SELEX/methyl-SELEX数据，本文用于验证甲基化对E-box结合的影响。
- **Voong et al. (2016)**：化学核小体定位图，本文用于分析TF结合位点与核小体的空间关系。
- **Vierstra et al. (2020)**：TF motif archetype数据库，本文用于排除非E-box motif的共富集。
- **AlphaFold3 (Abramson et al. 2024)**：结构预测工具，本文用于bHLH二聚体建模。
- **ModCLIP/ModCRE (Oliva实验室)**：核小体结合建模工具，本文用于评估TF-核小体空间冲突。
- **候选连接方向**：与「TF–DNA结合动力学」（如SMAD、p53的变体偏好）比较；与「 pioneer factor设计」（如dCas9-pioneer融合）结合；与「癌症增强子重编程」领域（如MYC在多种癌症中的增强子入侵）交叉。

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：E-box变体语法预测bHLH pioneer活性的深度学习模型
   - **来源局限/观察**：本文的回归框架为线性模型，无法捕捉变体间的非线性交互（如间距×密度×甲基化）。
   - **核心假设**：基于CNN或Transformer的序列模型，以E-box变体、间距、侧翼序列、甲基化状态为输入，可更准确预测TF的染色质重塑能力。
   - **初步方法**：以本文74个ChIP-seq数据集为训练数据，构建多任务模型同时预测peak可及性变化和转录激活；引入注意力机制识别关键间距模式。
   - **验证方式**：留一因子交叉验证；与本文线性回归比较AUC；在独立bHLH ChIP-seq数据上测试。
   - **创新状态**：unverified

2. **候选名称**：DNA甲基化驱动的TF motif重编程——泛癌分析
   - **来源局限/观察**：本文揭示MYC在甲基化下从CAC-CAC转向CAT-CAC，但仅涉及少数因子和细胞类型。
   - **核心假设**：在泛癌中，启动子/增强子甲基化状态系统性重编程多种TF的motif偏好，形成「甲基化- TF靶标重塑」网络。
   - **初步方法**：整合TCGA甲基化、ATAC-seq、ChIP-seq数据，对50+ TF计算甲基化依赖的motif偏好变化；聚类识别共享重编程模式。
   - **验证方式**：体外甲基化SELEX验证；CRISPR甲基化编辑后ChIP-seq验证。
   - **创新状态**：partially checked（本文已提供初步证据）

3. **候选名称**：核小体结合能力的结构预测——从bHLH扩展到全TF家族
   - **来源局限/观察**：本文用AlphaFold3+ModCLIP评估15个bHLH因子，但未与其他TF家族比较。
   - **核心假设**：TF的DNA结合域结构特征（螺旋长度、柔性、电荷分布）可预测其核小体结合能力，且此预测力跨家族泛化。
   - **初步方法**：对C2H2锌指、homeodomain、FOX等家族各10+因子，用AlphaFold3预测结构，ModCLIP评估核小体结合，与实验pioneer活性数据比较。
   - **验证方式**：与已知pioneer因子列表（如OCT4、SOX2、FOXA1）比较；体外核小体结合实验验证。
   - **创新状态**：unverified

4. **候选名称**：TF–DNA结合动力学的分子动力学模拟——E-box变体偏好机制
   - **来源局限/观察**：本文的E-box变体偏好来自ChIP-seq统计，缺乏原子层面的机制解释。
   - **核心假设**：不同E-box变体与bHLH二聚体的结合自由能差异（尤其是中心二核苷酸与关键残基的氢键/疏水相互作用）决定变体偏好。
   - **初步方法**：选取NEUROD2、MYC、TWIST1各3个E-box变体，进行μs级MD模拟，计算结合自由能（MM-PBSA/ABFE），分析构象变化。
   - **验证方式**：与本文ChIP-seq变体偏好排序比较；表面等离子共振（SPR）实验验证结合亲和力。
   - **创新状态**：unverified

5. **候选名称**：TF–DNA互作的「语法-功能」映射——跨细胞类型的泛化性检验
   - **来源局限/观察**：本文结论主要基于培养细胞诱导系统，未检验在体内不同细胞类型中的泛化性。
   - **核心假设**：E-box变体语法是TF的内在属性，但染色质重塑能力受细胞类型特异性共因子调节。
   - **初步方法**：收集体内（组织/类器官）bHLH ChIP-seq数据，比较变体偏好与培养细胞的一致性；分析共结合因子对重塑能力的影响。
   - **验证方式**：跨数据集一致性检验；共因子敲低后ChIP-seq表型变化。
   - **创新状态**：unverified