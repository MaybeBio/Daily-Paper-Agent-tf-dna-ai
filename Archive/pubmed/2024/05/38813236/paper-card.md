## 01 基本信息
- **标题**：The upregulation and transcriptional regulatory mechanisms of Extra spindle pole bodies like 1 in bladder cancer: An immunohistochemistry and high-throughput screening Evaluation
- **作者与单位**：Zhang, Wei; Liang, Zi-Qian; He, Rong-Quan; Huang, Zhi-Guang; Wang, Xiao-Min; Wei, Mao-Yan; Su, Hui-Ling; Liu, Zhi-Su; Zheng, Yi-Sheng; Huang, Wan-Ying; Zhang, Han-Jie; Dang, Yi-Wu; Li, Sheng-Hua; Cheng, Ji-Wen; Chen, Gang; He, Juan（广西医科大学第一附属医院等，具体单位未提供）
- **期刊/预印本平台**：Heliyon
- **年份**：2024-05-30
- **论文类型**：多组学整合研究（含IHC验证、scRNA-seq、表观遗传学分析、药物敏感性预测）
- **领域**：膀胱癌（BC）肿瘤分子生物学；ESPL1基因表达调控
- **关键词**：ESPL1；膀胱癌；转录调控；表观遗传；miR-299-5p；免疫微环境；药物敏感性
- **DOI/arXiv 号**：10.1016/j.heliyon.2024.e31192
- **代码**：未提供
- **数据**：GEO、ArrayExpress、TCGA公共数据；in-house IHC样本（n=202）；Depmap Portal CRISPR数据
- **阅读日期**：未提供
- **在「蛋白质-DNA互作(聚焦TF–DNA结合机制) × AI方法/物理模拟」方向中的位置**：本文属于**表观遗传调控机制解析**类研究，利用ChIP-seq、ATAC-seq、Hi-C等实验数据鉴定ESPL1上游转录因子（H2AZ、IRF5、HIF1A）及增强子-启动子环状互作，属于**基于实验数据的TF–DNA结合位点与染色质构象分析**，未涉及AI/深度学习或物理模拟方法，但提供了TF–DNA结合与染色质三维互作整合分析的范例。

## 02 一句话总结
通过整合多中心mRNA数据（n=1391）、in-house IHC验证（n=202）、scRNA-seq、ChIP-seq/ATAC-seq/Hi-C表观遗传分析及药物敏感性预测，证明ESPL1在膀胱癌中显著上调，其转录受上游TF（H2AZ、IRF5、HIF1A）结合及增强子-启动子染色质环调控，且与免疫浸润、化疗药物敏感性相关。

## 03 研究问题
- **具体问题**：ESPL1在膀胱癌中的表达水平如何？其转录上调的表观遗传调控机制是什么？ESPL1表达与肿瘤微环境、药物敏感性有何关联？
- **为什么重要**：膀胱癌异质性强、复发率高，需新的诊断标志物和治疗靶点。ESPL1作为分离酶（separase）核心组分，在多种肿瘤中高表达，但其在膀胱癌中的表达调控机制尚不明确。
- **现有方法不足**：既往研究（如Chen et al.）仅基于小样本（n=246）报道ESPL1在膀胱癌中高表达，缺乏蛋白水平验证、细胞类型定位、上游调控机制解析及临床相关性分析。
- **精确的"Can ... ?"研究问题**：Can integrating multi-centre transcriptomic data, in-house IHC validation, scRNA-seq, and epigenetic profiling (ChIP-seq/ATAC-seq/Hi-C) reveal the expression pattern and transcriptional regulatory mechanisms of ESPL1 in bladder cancer?

## 04 背景与发展脉络
- **阶段一：ESPL1功能研究**（2010s-2020s）：ESPL1作为分离酶，在姐妹染色单体分离中起关键作用。多项研究报道其在肝癌、肺癌、卵巢癌等中高表达并与预后相关（Song et al., Liu et al., Gui et al.）。
- **阶段二：膀胱癌中ESPL1初步探索**（2020s）：Chen et al. 基于小样本（n=246）报道ESPL1在膀胱癌中高表达，但未深入机制。
- **阶段三：多组学整合与表观遗传调控解析**（本文，2024）：利用大规模公共数据（n=1391）、in-house IHC（n=202）、scRNA-seq、ChIP-seq/ATAC-seq/Hi-C，首次系统解析ESPL1在膀胱癌中的表达特征、细胞定位、上游TF调控及染色质三维互作机制。
- **本文主张的位置**：在ESPL1肿瘤研究脉络中，本文是首个针对膀胱癌进行**多维度表观遗传调控机制**解析的研究，填补了ESPL1上游调控机制的空白。
- **脉络标注**：仅本文框架（基于本文引言与讨论的梳理）。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 样本量不足 | 既往膀胱癌ESPL1研究仅纳入246例样本 | 单一中心、缺乏多中心数据整合 | Introduction: "included only a small number of samples (n = 246)" |
| 缺乏蛋白水平验证 | 既往研究仅基于mRNA数据 | 未进行in-house实验验证 | Introduction: "in-house samples were not included for experimental validation" |
| 调控机制不明 | ESPL1高表达的转录调控机制完全未知 | 未利用表观遗传学手段解析上游调控 | Introduction: "there was neither an in-depth exploration of the potential regulatory mechanisms of ESPL1 expression" |
| 缺乏细胞类型定位 | 不清楚ESPL1在膀胱癌中由何种细胞表达 | 未进行单细胞水平分析 | Introduction: "nor a comprehensive analysis at the cellular level" |
| 上游miRNA未鉴定 | ESPL1的miRNA调控网络未知 | 未进行miRNA预测与验证 | Introduction: "the roles that these factors potentially play in the upstream regulation of ESPL1 have not been clarified" |

## 06 核心思想
1. **表面方法**：整合多中心转录组数据（19个mRNA数据集合并为11个队列）进行ESPL1表达差异分析；用in-house组织芯片（n=202）进行IHC蛋白验证；用scRNA-seq（GSE176249）定位细胞类型；用ChIP-seq/ATAC-seq/Hi-C解析表观遗传调控；用Depmap CRISPR数据评估基因依赖性；用分子对接预测药物结合；用4种miRNA预测工具鉴定上游miRNA。
2. **核心洞察**：ESPL1在膀胱癌中的高表达并非孤立事件，而是由**多层次调控网络**共同驱动——上游TF（H2AZ、IRF5、HIF1A）结合启动子区域、增强子-启动子染色质环（含超级增强子）激活转录、以及miR-299-5p的负调控缺失。该网络同时与肿瘤免疫微环境重塑和化疗药物敏感性相关。
3. **可能的普适教训** [Analysis]：对于肿瘤中异常高表达的基因，仅验证表达差异远远不够；**整合表观遗传（TF结合、染色质构象）与非编码RNA调控**可系统揭示其转录上调的驱动机制，这一思路可迁移至其他肿瘤相关基因的调控研究。

## 07 方法总览
- **输入**：多中心mRNA表达数据（n=1391）、in-house组织样本（n=202）、scRNA-seq数据（GSE176249）、ChIP-seq/ATAC-seq/Hi-C公共数据、Depmap CRISPR筛选数据、药物敏感性数据（GDSC）、miRNA表达数据（n=6625血样+n=537组织）
- **输出**：ESPL1表达差异结论、蛋白水平验证、细胞类型定位、上游TF鉴定、染色质环互作图谱、药物敏感性关联、miRNA调控网络
- **模块**：① 数据整合与差异表达分析（limma+SVA批次校正）→ ② IHC蛋白验证 → ③ scRNA-seq细胞定位 → ④ 表观遗传调控解析（ChIP-seq TF结合、ATAC-seq染色质开放性、Hi-C染色质环）→ ⑤ 功能依赖性分析（Depmap CRISPR）→ ⑥ 药物敏感性预测（oncoPredict）→ ⑦ miRNA预测与调控网络构建
- **训练**：不涉及传统模型训练；使用统计检验（t检验、ANOVA、Wilcoxon秩和检验）和随机效应模型计算SMD
- **反馈回路**：mRNA差异→IHC验证→scRNA-seq定位→表观遗传机制→药物关联→miRNA网络，各模块间形成证据链闭环
- **文字流程**：先通过多中心mRNA数据确认ESPL1上调→用IHC在蛋白水平验证→用scRNA-seq确定表达细胞类型→用ChIP-seq/ATAC-seq/Hi-C解析上游TF和染色质环调控→用CRISPR数据确认功能依赖性→预测药物敏感性→最后预测并验证miR-299-5p为上游负调控因子。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 多中心mRNA差异分析 | 确认ESPL1在BC中mRNA水平上调 | 提供大规模统计证据 | 输入：19个mRNA数据集；输出：SMD=0.75, 95%CI [0.09,1.40] | Results 图2A-B | 失去核心表达差异证据 |
| IHC蛋白验证 | 在蛋白水平验证ESPL1上调 | mRNA≠蛋白，需独立验证 | 输入：202例组织芯片；输出：肿瘤组显著高表达（p<0.0001），AUC=0.97 | Results 图3C-D | 无法确认蛋白水平变化 |
| scRNA-seq细胞定位 | 确定ESPL1表达细胞类型 | 明确肿瘤细胞vs基质细胞表达 | 输入：GSE176249；输出：ESPL1主要在BC上皮细胞表达 | Results 图6C-D | 无法区分细胞来源 |
| ChIP-seq TF鉴定 | 识别ESPL1上游TF | 解析转录调控机制 | 输入：Cistrome DB ChIP-seq数据；输出：H2AZ、IRF5、HIF1A结合ESPL1 TSS | Results 图8 | 失去TF调控证据 |
| ATAC-seq染色质开放性 | 确认ESPL1 TSS区域染色质开放 | 验证TF可及性 | 输入：ATAC-seq数据；输出：TSS区域开放 | Results 图8 | 无法确认调控区域可及性 |
| Hi-C/ChIA-PET染色质环 | 鉴定增强子-启动子互作 | 解析三维基因组调控 | 输入：HT-1376 ChIA-PET数据；输出：启动子-超级增强子/典型增强子环 | Results 图8 | 失去远程调控证据 |
| Depmap CRISPR依赖性 | 评估ESPL1功能重要性 | 确认ESPL1对癌细胞生存的必要性 | 输入：Depmap CRISPR数据；输出：ESPL1为多个癌细胞系依赖基因 | Results 图9A | 失去功能重要性证据 |
| 药物敏感性预测 | 关联ESPL1表达与药物反应 | 探索治疗意义 | 输入：GDSC药物数据；输出：高ESPL1与紫杉醇/吉西他滨IC50相关 | Results 图9B | 失去临床转化线索 |
| miRNA预测与验证 | 鉴定ESPL1上游miRNA | 完善调控网络 | 输入：4种miRNA预测工具；输出：miR-299-5p为候选，BC中下调 | Results 图9D-G, 图10 | 失去非编码RNA调控维度 |

## 09 关键公式符号
- **SMD（标准化均数差）**：SMD = (μ_treatment - μ_control) / σ_pooled，用于合并多队列效应量。文中SMD=0.75，95%CI [0.09, 1.40]（Methods 统计部分）。
- **I²统计量**：I² = (Q - df) / Q × 100%，用于量化队列间异质性。文中I²=88%（Results 图2B），提示队列间异质性高，故采用随机效应模型。
- **AUC（曲线下面积）**：用于评估ESPL1区分BC与正常组织的诊断效能，AUC=0.97 [0.95-0.99]（Results 图3D）。
- **IC50**：半数抑制浓度，用于药物敏感性分析（Results 图9B）。
- **Pearson相关系数r**：r ≥ 0.6且p<0.05定义为ESPL1正共表达基因（Methods 通路富集部分）。
- **分子对接结合能**：以kcal/mol表示，ESPL1-紫杉醇为-10.0 kcal/mol，ESPL1-吉西他滨为-6.8 kcal/mol（Results 图9C）。

## 10 实验设计与证据链
- **数据集/群体**：19个mRNA数据集（合并为11个队列，n=1391：1183 BC + 208非癌）；in-house组织芯片（n=202：175 BC + 27对照）；scRNA-seq（GSE176249，5201个细胞，9种细胞类型）；血样miRNA数据（n=6625）；组织miRNA数据（n=537）；Depmap CRISPR（n=1095细胞系）
- **指标**：mRNA表达差异（SMD）、IHC评分、AUC、IC50、免疫细胞浸润分数、相关性r值
- **基线/对照**：非癌组织/正常样本作为对照；ESPL1高/低表达组比较
- **评测协议**：随机效应模型计算合并SMD；Egger检验评估发表偏倚；ROC/sROC评估诊断效能；免疫浸润用CIBERSORT、TIMER、ESTIMATE三种算法交叉验证

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| 多中心mRNA差异分析 | ESPL1在BC中mRNA上调 | 11个队列，BC vs 非癌 | SMD=0.75 [0.09,1.40]，7/11队列显著 | ESPL1 mRNA在BC中上调 | 异质性高（I²=88%），部分队列不显著 | Results 图2A-B |
| IHC蛋白验证 | ESPL1蛋白在BC中高表达 | 175 BC vs 27对照 | 肿瘤组显著高表达，p<0.0001 | 蛋白水平验证mRNA结果 | 未做生存分析 | Results 图3C-D |
| ROC分析 | ESPL1可区分BC与正常 | IHC评分 | AUC=0.97 [0.95-0.99] | ESPL1有强诊断潜力 | 未与临床分期关联 | Results 图3D |
| scRNA-seq定位 | ESPL1在BC上皮细胞表达 | 9种细胞类型 | 上皮细胞中高表达 | 肿瘤细胞内在表达 | 未做肿瘤异质性亚群分析 | Results 图6C-D |
| 通路富集 | ESPL1共表达基因富集于细胞周期 | GO/KEGG/Reactome | 细胞周期、DNA复制通路富集 | ESPL1参与细胞周期调控 | 未做功能实验验证 | Results 图4 |
| ChIP-seq TF结合 | H2AZ/IRF5/HIF1A结合ESPL1 TSS | Cistrome DB数据 | 三个TF均有结合峰 | 三个TF可能调控ESPL1转录 | 未在BC细胞系中验证 | Results 图8 |
| ATAC-seq开放性 | ESPL1 TSS区域染色质开放 | ATAC-seq峰 | TSS区域有开放峰 | 调控区域可及 | 未做动态染色质分析 | Results 图8 |
| Hi-C/ChIA-PET环 | 启动子-增强子环存在 | HT-1376 ChIA-PET | 启动子与SE/TE有环 | 远程增强子可能调控ESPL1 | 未在BC原代细胞验证 | Results 图8 |
| CRISPR依赖性 | ESPL1是癌细胞必需基因 | Depmap 1095细胞系 | Chronos score<-1 | ESPL1对癌细胞增殖必要 | 未做BC特异性验证 | Results 图9A |
| 药物敏感性 | ESPL1表达与药物IC50相关 | 高vs低表达组 | 紫杉醇IC50升高（p=0.016），吉西他滨IC50降低（p=0.0012） | ESPL1影响化疗敏感性 | 未做体外药物实验 | Results 图9B |
| 分子对接 | ESPL1与药物直接结合 | 紫杉醇/吉西他滨 | 结合能-10.0/-6.8 kcal/mol | 可能存在直接物理互作 | 未做结合动力学验证 | Results 图9C |
| miRNA预测与验证 | miR-299-5p为ESPL1上游抑制因子 | 4种预测工具+表达验证 | 26个候选miRNA，miR-299-5p在BC中下调且与ESPL1负相关（r=-0.12, p=0.01） | miR-299-5p可能负调控ESPL1 | 未做荧光素酶报告实验 | Results 图9D-G, 图10 |

## 11 结论正确解读
- **任务范围**：本研究是**描述性/相关性**研究，而非因果性功能研究。所有结论均基于公共数据库挖掘、生信分析和IHC验证，未进行细胞或动物水平的功能实验。
- **oracle/真值输入**：ESPL1表达数据来自公共数据库（GEO/TCGA）和in-house IHC；TF结合和染色质环数据来自Cistrome DB和公共ChIA-PET/Hi-C数据，非本研究自行产生的实验数据。
- **端到端状态**：非端到端。各分析模块独立进行，未形成统一的预测模型或验证闭环。
- **算力成本**：未提供具体算力信息；分析以统计和生信工具为主，计算成本较低。
- **历史数据依赖**：高度依赖公共数据库的样本质量和注释准确性；不同平台、不同批次的合并可能引入偏倚（I²=88%提示高异质性）。
- **模型依赖**：不涉及机器学习模型；统计方法依赖随机效应模型假设。
- **最难情形**：对于ESPL1表达不显著升高的BC亚型（4/11队列未达显著），本研究的结论可能不适用。
- **群体/领域边界**：结论仅适用于膀胱癌；ESPL1在其他肿瘤中的调控机制可能不同。
- **不确定性**：TF结合和染色质环数据来自非BC细胞系（HT-1376为膀胱癌细胞系，但ChIA-PET数据来源未明确说明）；miRNA调控仅基于预测和相关性，缺乏实验验证。
- **有边界的复述**：在膀胱癌中，ESPL1在mRNA和蛋白水平均显著上调，主要表达于上皮肿瘤细胞；其转录可能受H2AZ、IRF5、HIF1A三个TF结合启动子及增强子-启动子染色质环调控；ESPL1高表达与免疫细胞浸润改变和紫杉醇/吉西他滨敏感性变化相关；miR-299-5p在BC中下调，可能为ESPL1上游负调控因子。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 缺乏功能实验 | 未进行in vitro/in vivo实验验证ESPL1的生物学功能 | "in vivo and in vitro assays must be developed to examine the biological function of ESPL1" | Discussion 末段 |
| 表观遗传机制需进一步验证 | ChIP-seq/ATAC-seq/Hi-C数据来自公共数据库，非本研究自行产生 | "more in-house high-throughput technologies are required for further studies to validate the potential epigenetic regulatory mechanisms" | Discussion 末段 |
| 预测性结论 | miRNA调控和药物敏感性均为预测性结果 | 未明确提出具体验证方案 | Discussion 末段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 高异质性（I²=88%） | 合并SMD可能受少数极端队列驱动；随机效应模型虽已校正，但结论稳健性存疑 | 影响ESPL1上调结论的普适性 | 逐队列留一法敏感性分析；按平台/种族分层分析 | Results 图2B |
| ChIP-seq数据来源非BC特异性 | Cistrome DB中H2AZ/IRF5/HIF1A的ChIP-seq数据可能来自其他细胞类型，不能直接外推至BC | TF结合具有细胞类型特异性，可能高估或误判调控关系 | 在BC细胞系中重新进行ChIP-seq验证 | Results 图8 |
| 染色质环数据单一细胞系 | HT-1376 ChIA-PET数据仅代表一个膀胱癌细胞系，无法反映BC异质性 | 增强子-启动子互作具有细胞特异性 | 在多个BC细胞系中验证Hi-C/ChIA-PET | Results 图8 |
| miRNA仅预测未验证 | 4种工具预测的26个miRNA未进行实验验证；miR-299-5p与ESPL1的负相关r=-0.12极弱 | 相关性弱可能无生物学意义；预测工具假阳性率高 | 荧光素酶报告实验；miRNA mimic/inhibitor功能实验 | Results 图9D-G |
| 药物敏感性为计算预测 | oncoPredict基于表达谱预测IC50，未考虑药物代谢、肿瘤微环境等实际因素 | 临床转化价值有限 | 体外药物敏感性实验（IC50测定） | Results 图9B |
| 分子对接未验证 | 对接结合能仅为计算预测，未进行结合动力学或细胞实验验证 | 直接物理互作证据不足 | SPR/ITC等生物物理方法验证 | Results 图9C |
| 免疫浸润分析未与临床结局关联 | 仅报告了免疫细胞浸润差异，未分析其与生存、治疗反应的关系 | 免疫相关结论的临床意义不明 | 生存分析；免疫治疗队列验证 | Results 图5 |
| 缺乏多变量校正 | 临床特征关联分析（表2）未校正混杂因素（如分期、分级、吸烟史） | 可能产生虚假关联 | 多因素logistic/Cox回归 | Table 2 |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **多组学整合策略**：从mRNA差异→蛋白验证→单细胞定位→表观遗传机制→功能依赖性→药物关联→miRNA调控的**七步递进框架**，可迁移至其他肿瘤中异常表达基因的系统性解析。
2. **TF–DNA结合与染色质构象联合分析**：ChIP-seq（TF结合）+ ATAC-seq（染色质开放性）+ Hi-C/ChIA-PET（远程互作）三者联用，可系统揭示基因转录调控的**空间机制**。对本课题（TF–DNA结合机制）的启示：仅鉴定TF结合位点不够，需结合染色质开放性（可及性）和三维构象（增强子-启动子环）判断功能性结合。
3. **超级增强子（SE）概念**：ESPL1启动子与上游SE形成环，提示**SE驱动的癌基因表达**是肿瘤中基因上调的重要模式。可迁移至TF–DNA互作研究：关注SE区域内的TF结合位点富集。
4. **miRNA-TF-靶基因调控网络**：构建TF–靶基因–miRNA三方网络（图9E），展示**多层转录调控**的复杂性。对本课题启示：TF–DNA结合并非孤立事件，需考虑miRNA介导的靶基因mRNA降解对TF-靶基因关系的间接影响。
5. **药物敏感性预测与分子对接**：oncoPredict（基于表达谱）+ AutoDock/QuickVina（分子对接）的组合，为从表达数据到药物反应预测提供了计算流程。对本课题启示：TF–DNA结合小分子抑制剂的设计可参考此对接流程。
6. **免疫微环境关联分析**：ESPL1表达与免疫细胞浸润相关，提示**癌基因表达与免疫逃逸**的潜在联系。对本课题启示：TF–DNA结合调控的靶基因可能参与免疫调节，值得在互作研究中纳入免疫相关表型。

## 15 与已有知识连接
- **ESPL1功能背景**：ESPL1编码分离酶（separase），在姐妹染色单体分离中切割黏连蛋白亚基SCC1（Rad21）。本文讨论中引用了Song et al.（肝癌）、Liu et al.（肺腺癌）、Gui et al.（卵巢癌）等研究，可连接至PubMed中这些文献。
- **TF–DNA结合机制**：本文鉴定的TF（H2AZ、IRF5、HIF1A）中，HIF1A是低氧诱导因子，在肿瘤中广泛研究；IRF5是干扰素调节因子，参与免疫调控。可连接至JASPAR、TRANSFAC等TF结合位点数据库。
- **染色质三维结构**：本文使用的ChIA-PET技术（Chromatin Interaction Analysis by Paired-End Tag Sequencing）和Hi-C技术，可连接至ENCODE、4D Nucleome等计划的数据资源。
- **膀胱癌分子分型**：本文未涉及，但可连接至TCGA膀胱癌分子分型研究（如basal/luminal亚型）。
- **miRNA调控网络**：miR-299-5p位于14q32.31的DLK1-DIO3印记区域，该区域在多种肿瘤中异常甲基化。可连接至miRBase、TargetScan等数据库。
- **方法学连接**：limma、SVA、clusterProfiler、Seurat、CIBERSORT等工具均为生信分析标准工具，可连接至Bioconductor/R生态。
- **可迁移方向** [Analysis]：本文的**表观遗传调控解析框架**（TF ChIP-seq + ATAC-seq + 染色质环）可直接迁移至其他TF–DNA互作研究；**miRNA-TF-靶基因网络构建**方法可扩展至更复杂的调控网络分析。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：基于深度学习预测TF–DNA结合与染色质环协同调控
   - **来源局限/观察**：本文仅用实验数据展示TF结合与染色质环共存，未建立预测模型
   - **核心假设**：TF结合位点、染色质开放性、增强子-启动子环三者存在可学习的协同模式
   - **初步方法**：以ENCODE/4D Nucleome数据为训练集，构建多模态深度学习模型（如Transformer+图神经网络），输入DNA序列+ATAC-seq峰+Hi-C矩阵，输出TF–DNA结合概率及增强子-启动子互作概率
   - **验证方式**：在膀胱癌ChIP-seq/Hi-C数据上验证；与现有工具（如DeepSEA、Basenji）比较AUC
   - **创新状态**：unverified

2. **候选名称**：HIF1A–ESPL1轴在膀胱癌低氧微环境中的调控机制
   - **来源局限/观察**：本文鉴定HIF1A为ESPL1上游TF，但未探讨低氧条件对ESPL1表达的影响
   - **核心假设**：低氧通过HIF1A直接结合ESPL1启动子/增强子区域上调ESPL1表达，促进肿瘤增殖
   - **初步方法**：膀胱癌细胞系低氧培养（1% O2）→ qPCR/WB检测ESPL1表达；HIF1A siRNA敲低验证；ChIP-qPCR验证HIF1A结合
   - **验证方式**：双荧光素酶报告实验；低氧条件下细胞增殖/凋亡表型
   - **创新状态**：unverified

3. **候选名称**：基于分子动力学模拟的ESPL1-紫杉醇/吉西他滨结合机制解析
   - **来源局限/观察**：本文仅用分子对接预测结合能，未进行动力学验证
   - **核心假设**：ESPL1与紫杉醇/吉西他滨的结合在动力学上稳定，且结合位点具有药物设计价值
   - **初步方法**：以ESPL1晶体结构（PDB: 7NJ1）为受体，进行100ns级分子动力学模拟（AMBER/GROMACS），计算结合自由能（MM-PBSA/MM-GBSA），鉴定关键残基
   - **验证方式**：与对接结果比较；突变关键残基后重复模拟；表面等离子共振（SPR）实验验证
   - **创新状态**：unverified

4. **候选名称**：基于图神经网络的TF–miRNA–靶基因调控网络推断
   - **来源局限/观察**：本文构建的TF–ESPL1–miR-299-5p网络仅基于预测工具，未系统化
   - **核心假设**：图神经网络可从多组学数据中学习TF–miRNA–靶基因的调控关系
   - **初步方法**：以TCGA-BLCA数据构建异质图（节点：TF、miRNA、mRNA；边：ChIP-seq结合、miRNA靶向预测、表达相关性），训练图注意力网络（GAT）预测调控关系
   - **验证方式**：留出法验证；与现有数据库（如miRTarBase、TRRUST）比较
   - **创新状态**：unverified

5. **候选名称**：ESPL1超级增强子-启动子环的3D基因组预测模型
   - **来源局限/观察**：本文发现ESPL1启动子与SE形成环，但未预测其他癌症中类似模式
   - **核心假设**：SE-启动子环的形成具有序列特征，可被机器学习模型预测
   - **初步方法**：以CTCF/cohesin ChIP-seq、H3K27ac/H3K4me3组蛋白修饰、序列motif为特征，训练随机森林/XGBoost预测SE-启动子互作
   - **验证方式**：在独立Hi-C数据集上验证；与现有预测工具（如CTCF-IP、PIRCh）比较
   - **创新状态**：unverified