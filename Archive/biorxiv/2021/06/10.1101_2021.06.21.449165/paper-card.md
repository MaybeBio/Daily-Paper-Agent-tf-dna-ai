## 01 基本信息
- **标题**：Predicting gene regulatory networks from multi-omics to link genetic risk variants and neuroimmunology to Alzheimer’s disease phenotypes
- **作者与单位**：Khullar S; Wang D（威斯康星大学麦迪逊分校，生物统计与医学信息学系；Waisman Center）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2021
- **论文类型**：方法学/整合组学分析（预印本，未经同行评审）
- **领域**：计算基因组学、基因调控网络、阿尔茨海默病（AD）多组学整合
- **关键词**：gene regulatory network (GRN)、multi-omics、Alzheimer's disease、transcription factors (TFs)、GWAS SNPs、neuroimmunology、Covid-19
- **DOI/arXiv 号**：10.1101/2021.06.21.449165
- **代码**：https://github.com/daifengwanglab/ADSNPheno
- **数据**：GSE1297（海马CA1微阵列）、GSE159699（LTL RNA-seq）、ROSMAP（DLPFC，synapse ID: syn3219045）、GSE157103（Covid-19 RNA-seq）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA互作（TF–DNA结合机制）× AI/深度学习/物理模拟」方向中的**整合组学与调控网络推断**分支。其核心贡献在于：将TF–DNA结合（通过TFBS基序匹配）与GWAS风险变异、基因共表达模块、表型关联整合为可解释的GRN，并利用机器学习验证网络基因的临床预测价值。对TF–DNA互作课题的可迁移点在于：①TFBS中断（motif-breaking）作为SNP功能注释的核心机制；②多组学整合框架（基因型→染色质互作→TF结合→基因表达→表型）可复用于其他疾病；③GRN子网络提取与机器学习结合的策略。

## 02 一句话总结
本文通过整合基因型、转录组、表观基因组（染色质互作）和GWAS数据，构建了三个AD相关脑区（海马CA1、LTL、DLPFC）的基因调控网络（GRN），将AD风险SNP通过中断TF结合位点（TFBS）连接到靶基因和共表达模块，并利用Covid-19严重程度作为神经免疫失调的代理表型，用机器学习验证了AD-Covid共享通路基因的预测能力。

## 03 研究问题
- **具体问题**：AD风险SNP（绝大多数位于非编码区）如何通过影响TF–DNA结合来调控基因表达，进而影响AD表型（如疾病进展、认知衰退）和神经免疫过程？
- **为什么重要**：GWAS已发现大量AD风险位点，但90%以上位于非编码区，其功能机制（即"从变异到表型"的调控链条）尚不清楚。理解SNP→TFBS中断→基因调控→表型的因果链，是精准医学和药物靶点发现的关键。
- **现有方法不足**：①传统GWAS关联分析无法直接解释非编码变异的调控功能；②单组学分析（仅转录组或仅表观基因组）无法连接基因型与表型；③现有GRN推断方法多基于单一数据源，缺乏跨脑区、跨组学的系统整合；④缺乏将GRN与临床表型（如Covid-19严重程度）直接关联的验证框架。
- **精确的"Can ... ?"研究问题**：Can we construct brain-region-specific gene regulatory networks that link AD risk SNPs (via disrupted TF binding sites) to target genes and co-expression modules, and use these networks to identify genes that predict Covid-19 severity as a proxy for neuroimmunological dysfunction in AD?

## 04 背景与发展脉络
**注：以下脉络基于本文框架，未经外部系统核验，标注为「仅本文框架」。**

1. **阶段一：GWAS与风险位点发现**（~2005-2015）
   - 代表方法：大规模GWAS（如IGAP、UK Biobank）
   - 优点：识别了大量AD风险位点（如BIN1、MS4A4A、SPI1、TP53INP1）
   - 局限：无法解释非编码变异的调控功能

2. **阶段二：表达数量性状位点（eQTL）与共表达网络**（~2010-2018）
   - 代表方法：eQTL分析、WGCNA共表达网络
   - 优点：将变异与基因表达关联，识别共表达模块
   - 局限：缺乏调控机制（TF-增强子-启动子）层面的解释

3. **阶段三：表观基因组与染色质构象整合**（~2015-2020）
   - 代表方法：Hi-C、ATAC-seq、H3K27ac ChIP-seq；scGRNom等工具
   - 优点：提供增强子-启动子互作证据，缩小候选调控元件范围
   - 局限：多数研究聚焦单一脑区或单一组学，缺乏跨区域系统比较

4. **阶段四：多组学GRN整合与疾病表型关联**（本文位置，~2020-2021）
   - 代表方法：本文提出的pipeline（共表达→TF预测→SNP-TFBS中断→GRN→表型关联→机器学习验证）
   - 优点：①连接基因型→调控→表型的完整链条；②跨三个脑区比较；③引入Covid-19作为神经免疫失调的代理表型
   - 局限：基于基序预测TFBS，缺乏直接ChIP-seq验证；样本量有限（海马31例、LTL 30例）

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 非编码SNP功能注释困难 | 90%以上AD风险SNP位于非编码区，难以直接关联到基因 | 缺乏调控元件（增强子/启动子）层面的系统注释 | Introduction: "most AD SNPs locate on non-coding DNA, and it is still challenging to link them to potential AD genes" |
| 单组学分析无法连接基因型与表型 | 转录组或表观基因组单独分析无法解释变异如何影响疾病 | 缺乏跨组学整合框架 | Introduction: "how these risk variants affect deeper phenotypes such as disease progression and immune response remains elusive" |
| 跨脑区调控机制差异不明 | 不同脑区对AD的易感性不同，但缺乏系统比较 | 现有研究多聚焦单一脑区 | Results: 三个脑区分别构建GRN，发现区域特异性和保守性 |
| GRN预测缺乏临床验证 | 网络推断结果难以转化为临床可用的生物标志物 | 缺乏将网络基因与临床表型关联的验证框架 | Results: 使用Covid-19严重程度作为代理表型，用机器学习验证 |
| TFBS预测依赖基序匹配，缺乏实验验证 | 基序匹配可能产生假阳性 | 未使用ChIP-seq直接验证TF结合 | Methods: 使用TFBSTools和motifmatchr基于共识基序推断TFBS |

## 06 核心思想
1. **表面方法**：一个多步骤的整合pipeline——(1) 对每个脑区的基因表达数据构建WGCNA共表达网络并聚类为模块；(2) 用多种工具（RTN、TReNA、GENIE3）预测TF-靶基因调控关系；(3) 将AD GWAS SNP与GRN中的调控元件（增强子/启动子）重叠，用motifbreakR识别中断TFBS的SNP；(4) 将SNP→TF→靶基因→模块→表型关联起来；(5) 提取AD-Covid共享通路基因，用机器学习预测Covid-19严重程度。

2. **核心洞察**：非编码SNP的功能效应可以通过"中断TFBS"这一机制被系统性地捕获——即SNP改变DNA序列导致TF无法结合增强子/启动子，从而改变下游基因表达。这一机制将基因型、表观基因组、转录组和表型连接为可检验的调控链条。此外，利用Covid-19作为"免疫失调放大镜"（代理表型），可以识别在神经免疫中起关键作用的AD风险基因。

3. **可能的普适教训** [Analysis]：①多组学整合的价值不在于单一数据源，而在于不同数据层之间的交叉验证（如共表达+TFBS+SNP三重证据）；②"代理表型"策略（用相关但更易测量的表型替代目标表型）可以扩大统计功效，但需注意代理表型与目标表型的生物学距离；③跨脑区比较是识别疾病核心机制与区域特异机制的有效策略。

## 07 方法总览
- **输入**：三个脑区（海马CA1、LTL、DLPFC）的群体基因表达数据（微阵列或RNA-seq）、AD GWAS SNP列表（97,058个，p<0.005）、表观基因组数据（增强子/启动子、Hi-C染色质互作）、TF基序数据库（JASPAR等）
- **输出**：每个脑区的GRN（TF→调控元件→靶基因），SNP-TFBS中断注释，AD-Covid基因列表及Covid-19严重程度预测模型
- **模块**：
  1. 共表达网络构建与模块识别（WGCNA）
  2. 模块功能注释（富集分析）
  3. TF-靶基因调控关系预测（RTN、TReNA、GENIE3）
  4. SNP-TFBS中断分析（motifbreakR）
  5. AD-Covid共享通路基因提取
  6. 机器学习预测Covid-19严重程度（SVM + RFE）
- **训练**：无监督（共表达聚类、GRN推断）+ 监督（SVM分类，4折交叉验证）
- **工具**：R（WGCNA、RTN、TReNA、GENIE3、motifbreakR）、Python（scikit-learn）
- **反馈回路**：GRN推断结果与SNP中断分析交叉验证；机器学习预测结果用于评估GRN基因的临床相关性
- **假设**：①共表达基因共享调控机制；②TFBS基序匹配可近似TF结合；③Covid-19严重程度可反映神经免疫失调程度

**文字流程**：基因表达数据 → WGCNA共表达网络 → 模块识别 → 模块-表型关联 → TF-靶基因预测（多工具共识）→ 与表观基因组（增强子/启动子/Hi-C）整合 → SNP-TFBS中断分析 → 构建SNP→TF→靶基因→模块→表型的GRN → 提取AD-Covid共享通路基因 → SVM预测Covid-19严重程度 → DCA验证临床效用

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| WGCNA共表达网络 | 识别共表达基因模块 | 将数千基因降维为可解释的模块，模块与表型关联 | 输入：基因表达矩阵；输出：共表达模块及模块-表型相关 | Results: 海马30模块、LTL 56模块、DLPFC 35模块，多个模块与AD表型显著相关 | 预期影响：失去模块结构，无法进行模块水平的表型关联和功能注释 [预期效应] |
| 模块功能富集分析 | 注释模块的生物学功能 | 将无监督聚类结果转化为生物学可解释性 | 输入：模块基因列表；输出：富集的KEGG/GO/REACTOME通路 | Results: 多个模块富集到免疫相关通路（如NF-κB、细胞因子） | 预期影响：模块的生物学意义不明，无法指导后续AD-Covid基因选择 [预期效应] |
| TF-靶基因预测（RTN/TReNA/GENIE3） | 推断TF调控的靶基因 | 建立从TF到基因的调控边 | 输入：基因表达+TF列表；输出：TF-靶基因调控对 | Methods: 多工具共识提高可信度 | 预期影响：失去调控方向性信息，GRN退化为共表达网络 [预期效应] |
| SNP-TFBS中断分析（motifbreakR） | 识别中断TF结合位点的风险SNP | 将非编码SNP连接到具体TF和调控元件 | 输入：AD GWAS SNP + GRN调控元件；输出：SNP→TF→靶基因注释 | Results: 83,842个SNP中断787个TF的TFBS | 实测效应：这是连接基因型与调控的核心环节，移除后SNP无法锚定到GRN [实测消融效应] |
| AD-Covid共享通路基因提取 | 识别两个疾病共有的免疫相关基因 | 利用Covid-19作为神经免疫失调的代理表型 | 输入：AD模块富集通路 + Covid-19 KEGG通路；输出：22个共享基因 | Results: 22个基因位于AD-Covid共享通路 | 预期影响：失去代理表型策略，无法验证GRN基因的免疫学相关性 [预期效应] |
| SVM + RFE机器学习 | 预测Covid-19严重程度 | 验证GRN基因的临床预测价值 | 输入：共享基因表达；输出：ICU vs 非ICU分类模型 | Results: 准确率86%（海马）、84%（LTL）、86%（DLPFC）、88%（合并），AUROC 0.91-0.93 | 实测效应：模型性能优于基准基因列表，支持GRN基因的临床相关性 [实测消融效应] |

## 09 关键公式符号
本文方法以计算流程为主，未提供显式数学公式。以下为隐含的关键计算概念：

1. **Pearson相关系数**（共表达网络边权重）：
   r(x,y) = Σ(xi - x̄)(yi - ȳ) / √[Σ(xi - x̄)² Σ(yi - ȳ)²]
   用途：WGCNA中衡量基因表达谱相似性

2. **模块特征基因（Module Eigengene, ME）**：
   ME = 第一主成分（PCA）of 模块基因表达矩阵
   用途：代表模块整体表达模式，用于模块-表型关联

3. **富集分析超几何检验**：
   p = Σ(k≥k_obs) C(K,k)·C(N-K, n-k) / C(N,n)
   用途：评估模块基因在特定通路中的富集显著性

4. **互信息（Mutual Information, MI）**（RTN/ARACNe）：
   MI(X;Y) = ΣΣ p(x,y)·log[p(x,y)/(p(x)p(y))]
   用途：衡量TF与靶基因表达的非线性关联

5. **SVM分类决策函数**：
   f(x) = sign(Σ αᵢyᵢK(xᵢ,x) + b)
   用途：Covid-19严重程度分类

6. **净收益（Net Benefit, DCA）**：
   NB = TP/N - (FP/N)·(pT/(1-pT))
   用途：评估临床决策效用，pT为阈值概率

## 10 实验设计与证据链
**数据集与资源**：
- 海马CA1：GSE1297，31例（9对照、7早期、8中期、7重度）
- LTL：GSE159699，30例（8年轻、10老年、12老年AD）
- DLPFC：ROSMAP，638例（FPKM数据）
- Covid-19：GSE157103，100例（50 ICU、50非ICU）
- GWAS SNP：97,058个AD风险SNP（p<0.005）
- 表观基因组：海马增强子/启动子（Brain Open Chromatin Atlas）、Hi-C互作（GSE86189）、LTL H3K27ac（GSE130746）、DLPFC增强子（PsychENCODE）

**指标**：模块-表型相关系数、富集p值（B-H校正）、SVM准确率、AUROC、DCA净收益

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|-------------------|------|
| 共表达模块-表型关联 | 模块表达与AD表型相关 | 三个脑区分别计算ME与表型相关 | 海马21/30模块、LTL 28/56模块与至少一个表型显著相关 | 共表达模块捕获AD相关表达变化 | 相关性不等于因果性 | Results 图2 |
| 模块富集分析 | 模块富集到免疫相关通路 | 与全基因组背景比较 | AD相关模块富集NF-κB、细胞因子、免疫应答等通路 | 支持神经免疫在AD中的作用 | 富集分析依赖数据库注释完整性 | Results 图3 |
| SNP-TFBS中断分析 | AD SNP通过中断TFBS影响调控 | 97,058 SNP vs GRN调控元件 | 83,842 SNP中断787个TF的TFBS | 非编码SNP可通过TFBS中断机制影响基因调控 | 基序预测未经ChIP-seq验证 | Results, Methods |
| 跨脑区GRN比较 | 存在区域保守和区域特异调控 | 三个脑区GRN重叠分析 | 发现跨区域保守和区域特异GRN结构 | 支持脑区特异性调控机制 | 样本量差异可能影响比较公平性 | Results |
| AD-Covid共享通路基因提取 | 存在AD-Covid共享免疫机制 | KEGG通路比较 | 22个共享基因，涉及NF-κB、细胞因子等 | 支持AD与Covid-19共享免疫失调机制 | 通路共享不等于功能共享 | Results |
| SVM预测Covid-19严重程度 | GRN基因可预测临床结局 | 与18个已知Covid-19基因比较 | 准确率84-88%，AUROC 0.91-0.93，优于基准 | GRN基因具有临床预测价值 | 样本量小（N=100），需外部验证 | Results 图6 |
| DCA验证 | 模型具有临床决策效用 | 与Treat All/Treat None比较 | 在多数阈值下净收益更高 | 模型具有临床实用性 | DCA依赖阈值选择 | Results, 图S52-54 |

## 11 结论正确解读
- **任务范围**：本文是计算预测性研究，预测的是"调控关系"和"临床分类"，而非因果验证。GRN推断基于关联和基序匹配，不包含湿实验验证。
- **oracle/真值输入**：GWAS SNP列表（p<0.005）作为"风险变异"的真值来源；TFBS基于共识基序匹配，非实验验证的ChIP-seq结合位点。
- **端到端状态**：pipeline从基因表达+SNP输入到GRN输出+临床预测是端到端的，但每个步骤的误差会累积（如基序预测假阳性、共表达模块边界敏感性）。
- **算力成本**：未报告具体计算资源；WGCNA和GENIE3在数万基因规模下计算量中等，SVM训练在100例样本上开销小。
- **历史数据依赖**：依赖公共数据库（JASPAR、KEGG、Brain Open Chromatin Atlas）的注释完整性；这些数据库的更新可能改变结果。
- **模型依赖**：GRN推断依赖多工具共识（RTN/TReNA/GENIE3），不同工具的参数选择可能影响结果；SVM的RFE特征选择具有随机性。
- **最难情形**：①低表达基因的共表达检测力不足；②罕见变异（低频SNP）在GWAS中代表性差；③非编码SNP的连锁不平衡（LD）结构可能混淆因果变异识别。
- **群体/领域边界**：结果基于欧洲裔为主的AD队列和Covid-19队列，推广到其他种族/人群需谨慎；脑区数据来自死后组织，可能受死后间隔影响。
- **不确定性**：未提供置信区间或bootstrap评估；GRN边权重和SNP-TFBS中断的显著性阈值（motifbreakR默认0.001）可能影响结果稳健性。
- **有边界的复述**：本文在三个AD相关脑区中，通过整合多组学数据构建了将AD风险SNP（通过TFBS中断）连接到靶基因和共表达模块的GRN，并证明这些网络中的基因在预测Covid-19严重程度方面优于已知Covid-19基因。该结论限于计算预测层面，需实验验证TFBS中断的功能效应和GRN的因果性。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 缺乏细胞类型分辨率 | 脑区bulk数据无法区分细胞类型特异性调控 | 使用单细胞数据（scRNA-seq、scATAC-seq）构建细胞类型GRN | Discussion: "Recent single-cell sequencing data (e.g., scRNA-seq, scATAC-seq) in AD enable studying functional genomics and regulatory mechanisms at cell type levels" |
| Covid-19数据来自血液而非脑组织 | 血液转录组可能无法完全反映脑内神经免疫过程 | 未来收集脑组织或CSF的Covid-19患者数据 | Discussion: "Covid-19 patient transcriptomic data was collected from blood samples and may present limitations" |
| 样本量有限 | 海马31例、LTL 30例，统计功效受限 | 在更大队列中验证 | 未明确提及，但样本量在Methods中可见 |
| 基序预测的局限性 | TFBS基于共识序列匹配，非实验验证 | 整合ChIP-seq数据验证TF结合 | 未明确提及，但Methods中承认使用基序预测 |
| 相关性不等于因果性 | 共表达和GRN推断无法证明因果关系 | 使用CRISPR等实验验证调控关系 | 未明确提及，但Discussion强调"true causal links"需更多研究 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| TFBS中断分析依赖基序匹配 | 基序匹配假阳性率高；SNP可能通过其他机制（如染色质构象改变、表观遗传修饰）影响调控 | 核心机制假设可能被高估 | 用ChIP-seq数据验证TF结合变化；用STARR-seq等高通量功能实验验证SNP效应 | Methods: 使用motifbreakR基于共识基序 |
| Covid-19作为AD神经免疫代理的合理性 | Covid-19严重程度受多因素影响（年龄、合并症、病毒载量），未必反映AD特异性免疫失调 | 代理表型策略可能引入混杂 | 在AD患者中直接测量神经免疫标志物（如细胞因子、小胶质细胞激活） | Discussion: 作者承认血液数据局限 |
| 多工具共识可能引入偏差 | RTN、TReNA、GENIE3算法假设不同，共识可能偏向保守预测，遗漏真实调控关系 | 网络完整性可能受损 | 用独立数据集（如eQTL、ChIP-seq）验证网络边 | Methods: 多工具共识策略 |
| 共表达网络对样本组成的敏感性 | 海马和LTL样本量小（~30），共表达模块可能不稳定 | 模块-表型关联可能受离群样本驱动 | 用bootstrap或jackknife评估模块稳定性 | Results: 样本量在Methods中可见 |
| 未报告多重检验校正细节 | 大量模块-表型相关和富集检验可能产生假阳性 | 结果稳健性存疑 | 检查是否使用FDR或Bonferroni校正 | Methods: 仅提及B-H校正，未说明具体阈值 |
| 机器学习特征选择可能过拟合 | RFE在100例样本上选择16个基因，可能过拟合 | 预测性能可能被高估 | 使用独立验证队列或嵌套交叉验证 | Results: 4折交叉验证，样本量小 |

## 14 Agent 提炼的知识候选
**面向课题方向（蛋白质-DNA互作（TF–DNA结合机制）× AI/物理模拟）的可迁移知识：**

1. **TFBS中断作为SNP功能注释的核心机制**：本文展示了如何将GWAS SNP映射到TFBS并预测其"破坏"效应。可迁移到TF–DNA结合课题：将SNP对TF结合亲和力的影响（通过ΔΔG或基序匹配分数变化）作为特征，训练预测模型。方法：使用motifbreakR或类似工具（如SNP2TFBS、FABIAN-variant）作为基线，结合分子动力学（MD）模拟或深度学习（如DeepSEA、Basenji）预测SNP对TF结合的影响。

2. **多组学整合框架**：基因型→染色质互作（Hi-C）→TFBS→基因表达→表型的链条设计，可复用于其他疾病或细胞类型。迁移建议：在TF–DNA结合预测中，将染色质可及性（ATAC-seq）、组蛋白修饰（H3K27ac）和3D基因组（Hi-C）作为特征，提高结合位点预测的特异性。

3. **代理表型策略**：用Covid-19严重程度作为神经免疫失调的代理，扩大了表型可测量性。迁移建议：在TF–DNA结合研究中，可用"TF结合亲和力变化"（体外实验可测）作为"疾病严重程度"的代理，用于训练和验证预测模型。

4. **多工具共识提高可信度**：RTN、TReNA、GENIE3三种工具预测的调控关系取共识，降低单一算法偏差。迁移建议：在TF–DNA结合预测中，集成多个预测器（如DeepSEA、DeepBind、FactorNet）的共识结果，提高稳健性。

5. **机器学习+临床决策验证**：SVM+RFE特征选择+DCA临床效用评估的流程，可用于评估TF–DNA结合预测模型的临床转化价值。迁移建议：在预测TF结合变异致病性时，不仅报告AUC，还应使用DCA评估临床决策效用。

6. **跨脑区比较识别核心vs.区域特异机制**：三个脑区的GRN比较揭示了保守和特异的调控结构。迁移建议：在TF–DNA结合研究中，跨细胞类型或跨物种比较TF结合谱，区分核心结合位点和细胞类型特异结合位点。

## 15 与已有知识连接
- **相似工作**：与Marco等（2018）的"从GWAS到增强子到基因"框架相似，但本文增加了跨脑区比较和Covid-19代理表型验证。与PsychENCODE的GRN工作（Wang等，2018）方法上互补，本文更侧重SNP-TFBS中断机制。
- **方法学连接**：WGCNA（Zhang & Horvath，2005）是共表达网络分析的标准工具；RTN（Fletcher等，2013）基于ARACNe算法；TReNA和GENIE3是常用的GRN推断工具。motifbreakR（Coetzee等，2015）是TFBS中断预测的常用工具。
- **可组合方向**：本文的GRN框架可与AlphaFold3或RoseTTAFold等结构预测工具结合——用预测的TF-DNA复合物结构评估SNP对结合亲和力的影响，替代或补充基序匹配方法。也可与深度学习模型（如Enformer、Basenji）结合，用序列特征预测SNP的调控效应。
- **冲突/差异**：本文基于基序匹配预测TFBS，未考虑TF协同结合、竞争性结合等复杂机制；更精细的TF–DNA结合模型（如考虑DNA形状特征、TF二聚化）可能提供更准确的预测。
- **候选方向（未验证）**：将本文的GRN框架扩展到单细胞水平（scRNA-seq + scATAC-seq），构建细胞类型特异的TF–DNA调控网络，可能揭示AD中特定细胞类型（如小胶质细胞）的调控失调机制。

## 16 研究想法
**Agent 生成的研究候选：**

1. **候选名称**：基于AlphaFold3的SNP-TFBS结合亲和力预测与GRN整合
   - **来源局限/观察**：本文用基序匹配预测TFBS中断，未考虑3D结构效应；AlphaFold3可预测TF-DNA复合物结构
   - **核心假设**：AlphaFold3预测的TF-DNA结合能变化（ΔΔG）比基序匹配分数更准确地区分致病与非致病SNP
   - **初步方法**：对AD风险SNP所在的TFBS，用AlphaFold3预测参考和变异等位基因的TF-DNA复合物结构，计算结合亲和力差异；与本文的GRN整合，比较预测性能
   - **验证方式**：用已发表的TF结合QTL（bQTL）和MPRA数据验证预测准确性；比较ΔΔG与motifbreakR分数的AUC
   - **创新状态**：unverified

2. **候选名称**：单细胞分辨率下的AD TF–DNA调控网络构建
   - **来源局限/观察**：本文使用bulk数据，无法区分细胞类型特异性调控；AD中小胶质细胞和星形胶质细胞的调控失调是关键
   - **核心假设**：单细胞水平的GRN能揭示bulk分析掩盖的细胞类型特异TF–DNA调控机制
   - **初步方法**：整合scRNA-seq和scATAC-seq数据，用SCENIC或CellOracle构建细胞类型特异的GRN；将AD风险SNP映射到细胞类型特异的增强子
   - **验证方式**：用CRISPR干扰（CRISPRi）验证关键TF-增强子-基因调控关系；比较细胞类型特异GRN与bulk GRN的差异
   - **创新状态**：unverified

3. **候选名称**：深度学习预测SNP对TF协同结合的影响
   - **来源局限/观察**：本文仅考虑单个TF的结合中断，未考虑TF协同结合（如SPI1与PU.1二聚化）
   - **核心假设**：考虑TF协同结合的深度学习模型比单TF模型更准确预测AD风险SNP的调控效应
   - **初步方法**：用Enformer或Basenji架构，输入含SNP的序列窗口，预测多个TF的结合变化；特别关注已知AD相关TF对（如SPI1-RUNX1）
   - **验证方式**：用STARR-seq或MPRA实验验证预测的协同结合效应；比较与单TF模型的AUC差异
   - **创新状态**：unverified

4. **候选名称**：AD风险SNP的3D基因组远程调控效应预测
   - **来源局限/观察**：本文的GRN主要基于近端调控元件，未考虑增强子-启动子远程互作（Hi-C数据仅用于辅助）
   - **核心假设**：AD风险SNP通过影响远程染色质互作（如TAD边界、CTCF结合）调控远距离基因
   - **初步方法**：整合Hi-C、HiChIP和启动子捕获Hi-C数据，构建3D基因组调控网络；用深度学习预测SNP对染色质构象的影响
   - **验证方式**：用3C/Hi-C实验验证预测的远程调控关系；比较与近端调控模型的预测性能
   - **创新状态**：unverified

5. **候选名称**：TF–DNA结合预测模型的临床决策曲线评估框架
   - **来源局限/观察**：本文用DCA评估Covid-19预测模型，但TF–DNA结合预测研究很少使用DCA
   - **核心假设**：DCA可以更全面地评估TF–DNA结合预测模型的临床价值，优于仅报告AUC
   - **初步方法**：将本文的DCA框架应用于TF–DNA结合预测模型（如DeepSEA、Enformer），评估在不同阈值下的净收益
   - **验证方式**：在AD和Covid-19数据集中比较DCA结果与AUC结果的一致性；评估模型在不同临床决策场景下的效用
   - **创新状态**：unverified