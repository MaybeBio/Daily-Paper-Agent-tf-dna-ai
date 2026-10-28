## 01 基本信息

- **标题**：SOX2 can associate with chromatin directly by binding to DNA or indirectly via association with other chromatin-bound proteins
- **作者**：Briana D. Ormsbee Golden; Kabhilan Mohan; Ethan P Metz; Phillip J Wilder; Jimmie Persinger; Soumi Basu; Daisy V. Gonzalez; Tahir H. Tahirov; Donald W. Coulter; Sandipan Brahma; Angie Rizzino
- **单位**：未提供（根据作者信息推测为美国内布拉斯加大学医学中心（UNMC）相关机构，但原文未明确列出单位列表）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（研究论文）
- **领域**：转录因子（SOX2）与染色质互作机制；转录调控；表观基因组学
- **关键词**：SOX2、DNA结合突变体、piggyback机制、ChIP-seq、ATAC-seq、CUT&RUN、AP-1、FRA1
- **DOI/ID**：10.64898/2026.09.02.748901
- **代码**：未提供
- **数据**：GEO（GSE293810, GSE293863, GSE316530, GSE316791, GSE344670）
- **阅读日期**：2026-09-03（根据预印本日期推断）
- **在该课题方向中的位置**：本文直接聚焦TF–DNA互作机制，通过构建SOX2 DNA结合域点突变体（G76P），系统比较野生型与突变体在全基因组范围内的染色质结合模式、转录组效应及染色质可及性变化，提出并验证了TF可通过"piggyback"（搭便车）机制间接结合染色质的新观点。该文为理解TF–DNA直接结合与间接结合（通过蛋白-蛋白互作）的相对贡献提供了重要范式，对AI/深度学习预测TF结合位点及物理模拟TF–DNA互作的研究具有重要参考价值——提示仅基于DNA序列基序的预测模型可能遗漏大量功能性结合事件。

## 02 一句话总结

通过构建SOX2 DNA结合域点突变体SOX2(G76P)，结合ChIP-seq、ATAC-seq、RNA-seq和CUT&RUN等多组学分析，证明SOX2不仅能通过其DBD直接结合SOX基序，还能通过与其他染色质结合蛋白（如AP-1/FRA1复合物）的蛋白-蛋白互作以"piggyback"机制间接结合染色质，且两种结合模式调控不同的基因网络。

## 03 研究问题

- **具体问题**：SOX2的基因靶点选择性是否仅由其DNA结合域（DBD）决定？当DBD无法直接结合DNA时，SOX2是否仍能通过其他机制（如蛋白-蛋白互作）与染色质结合并调控基因表达？
- **为什么重要**：SOX2是干细胞多能性和多种癌症（如小细胞肺癌、神经内分泌前列腺癌、髓母细胞瘤）中的关键转录因子。传统观点认为TF通过直接结合DNA基序发挥功能，但越来越多的证据表明TF的IDR和蛋白-蛋白互作也参与靶点选择。理解SOX2的完整染色质结合机制对癌症治疗和干细胞生物学至关重要。
- **现有方法为何不足**：大多数TF结合位点预测工具（如基于ChIP-seq的motif分析）默认TF必须直接结合DNA基序，忽略了TF通过蛋白-蛋白互作间接结合染色质的可能性。这可能导致对TF功能网络的系统性误判。
- **精确的"Can ... ?"研究问题**：Can a SOX2 DNA-binding mutant (SOX2(G76P)) still associate with chromatin and regulate gene expression through indirect mechanisms (e.g., piggyback via other chromatin-bound proteins), and if so, does this indirect association target different gene networks than direct DNA binding?

## 04 背景与发展脉络

**注：以下脉络基于本文框架及引用文献，部分经外部核验。**

1. **TF–DNA直接结合范式（经典模型）**：转录因子通过其DBD识别并结合特定DNA基序（如SOX家族的AACAAT基序），招募共调控因子和染色质重塑复合物（如SWI/SNF）调控基因表达。代表工作：Gubbay et al. 1990; Sinclair et al. 1990（SOX/SRY发现）；Reményi et al. 2003（SOX2 DBD晶体结构）。
2. **IDR在TF功能中的作用（近年进展）**：TF的IDR（如反式激活域）虽不直接结合DNA，但介导蛋白-蛋白互作，参与转录调控。代表工作：Wright and Dyson 1999；Brodsky et al. 2020；Jonas et al. 2025；Abidi et al. 2026。
3. **TF间接结合染色质（"piggyback"机制）的先例**：核受体（如糖皮质激素受体、雌激素受体）已被证明可通过蛋白-蛋白互作（tethering）间接结合AP-1等位点。代表工作：Jakacka et al. 2001；Carroll et al. 2006；Miranda et al. 2013。
4. **SOX2功能研究**：SOX2在胚胎干细胞、神经发育和多种癌症中的功能已被广泛研究，但其靶点选择机制（特别是DBD之外区域的贡献）尚不清楚。本文首次系统比较SOX2与SOX2(G76P)的全基因组结合模式。
5. **本文主张的位置**：在经典直接结合模型与新兴IDR功能研究之间架起桥梁，证明SOX2同时采用直接结合和间接结合两种模式，且间接结合（piggyback）可独立于DBD驱动转录组重编程。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| TF靶点选择机制认知不完整 | 传统模型认为TF必须直接结合DNA基序才能调控基因 | 忽略了TF的IDR和蛋白-蛋白互作对靶点选择的贡献 | Introduction部分：指出"selection of gene targets by SOX2 is not solely determined by its DNA binding domain" |
| ChIP-seq无法区分直接与间接结合 | ChIP-seq检测到的TF-染色质互作可能包含间接结合事件，但常规分析默认所有峰均为直接结合 | 交联可捕获间接互作，但缺乏区分方法 | Discussion部分：CUT&RUN与ChIP-seq结果对比显示方法学差异 |
| 预测模型可能遗漏功能性结合事件 | 基于DNA基序的TF结合位点预测工具无法识别无基序的功能性结合位点 | 预测模型仅考虑DNA序列特征，忽略蛋白-蛋白互作 | Results部分：SOX2(G76P)结合的位点缺乏SOX基序但富含AP-1基序 |
| SOX2高表达癌症的治疗靶点选择 | SOX2在多种癌症中高表达，但靶向其DBD可能不足以完全抑制其功能 | SOX2可通过间接机制维持部分功能 | Introduction部分：SOX2在20多种癌症中高表达 |
| CUT&RUN可能漏检间接结合 | CUT&RUN对间接结合的检测灵敏度低于ChIP-seq | CUT&RUN依赖抗体-蛋白复合物与DNA的邻近性，间接结合距离较远 | Results部分：SOX2(G76P)在CUT&RUN中信号弱但ChIP-seq信号强 |

## 06 核心思想

**1) 表面方法**：
构建SOX2 DBD点突变体SOX2(G76P)（第76位甘氨酸→脯氨酸，破坏DBD第二α螺旋），在髓母细胞瘤细胞系ON S76中建立多西环素诱导表达系统，系统比较SOX2与SOX2(G76P)在以下层面的差异：
- 体外DNA结合能力（EMSA）
- 细胞增殖效应（MTT）
- 转录组变化（RNA-seq）
- 全基因组染色质结合（ChIP-seq）
- 染色质可及性（ATAC-seq）
- 染色质结合模式（CUT&RUN）

**2) 核心洞察**：
SOX2的基因靶点选择性不仅由DBD决定。SOX2(G76P)虽无法直接结合DNA，但仍能通过与其他染色质结合蛋白（特别是AP-1/FRA1复合物）的蛋白-蛋白互作，以"piggyback"机制间接结合染色质，并驱动与SOX2完全不同的转录组重编程。此外，野生型SOX2本身也通过该机制结合一部分缺乏SOX基序的位点。

**3) 可能的普适教训 [Analysis]**：
- TF的DBD并非其功能的唯一决定因素；IDR介导的蛋白-蛋白互作可独立驱动TF的染色质结合和转录调控。
- ChIP-seq与CUT&RUN的结果差异可作为区分直接与间接结合的实验策略。
- 基于DNA基序的TF结合预测模型需要整合蛋白-蛋白互作信息才能全面捕捉TF的功能靶点。

## 07 方法总览

- **输入**：SOX2野生型与G76P突变体（小鼠G78P/人G76P）、ON S76髓母细胞瘤细胞系、多西环素诱导系统
- **输出**：全基因组TF结合谱（ChIP-seq）、染色质可及性谱（ATAC-seq）、转录组谱（RNA-seq）、染色质结合模式（CUT&RUN）、细胞增殖数据
- **模块**：
  1. 定点突变与质粒构建（QuikChange方法）
  2. 慢病毒生产与细胞系建立
  3. EMSA（体外DNA结合验证）
  4. MTT（细胞增殖）
  5. RNA-seq（转录组）
  6. ChIP-seq（全基因组结合）
  7. ATAC-seq（染色质可及性）
  8. CUT&RUN（结合模式验证）
  9. 生物信息学分析（DiffBind、Homer motif分析、deepTools可视化）
- **训练**：不适用（非机器学习方法）
- **工具**：DiffBind、Homer、deepTools、R/tidyverse、ChIPseeker
- **反馈回路**：EMSA验证突变体DNA结合能力丧失→RNA-seq/ChIP-seq/ATAC-seq/CUT&RUN多组学交叉验证→motif分析揭示结合位点特征
- **文字流程**：首先通过定点突变构建SOX2(G76P)并验证其体外DNA结合能力丧失（EMSA）→建立诱导表达细胞系并确认其抑制增殖效应→进行RNA-seq比较转录组差异→ChIP-seq比较全基因组结合位点→ATAC-seq比较染色质可及性变化→CUT&RUN验证结合模式差异→motif分析揭示间接结合位点的序列特征→整合多组学数据得出结论。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| SOX2(G76P)点突变体 | 破坏DBD第二α螺旋，消除直接DNA结合能力 | 区分直接结合与间接结合的贡献 | 输入：野生型SOX2序列；输出：G76P突变体 | EMSA显示突变体无法形成DNA-蛋白复合物（Supplemental Fig. S1B） | 无法区分直接与间接结合机制 |
| 诱导表达细胞系（i-SOX2(G76P)-ON S76） | 可控地表达突变体蛋白 | 避免组成性表达的适应性变化 | 输入：慢病毒载体；输出：多西环素诱导细胞系 | 剂量依赖性抑制增殖（Fig. 1A, B） | 无法在相同遗传背景下比较SOX2与突变体效应 |
| ChIP-seq | 全基因组TF结合位点检测 | 比较SOX2与突变体的染色质结合谱 | 输入：交联染色质+SOX2抗体；输出：结合峰 | 突变体结合大量非SOX基序位点（Fig. 2） | 无法获得全基因组结合信息 |
| ATAC-seq | 染色质可及性检测 | 评估TF对染色质开放状态的影响 | 输入：转座酶处理细胞核；输出：可及性峰 | SOX2大幅增加可及性，突变体仅小幅增加（Fig. 3） | 无法评估TF对染色质结构的影响 |
| CUT&RUN | 高分辨率TF结合位点检测 | 对比ChIP-seq，区分直接与间接结合 | 输入：细胞核+SOX2抗体+MNase；输出：结合峰 | 突变体在CUT&RUN中信号弱（Fig. 8） | 无法验证结合模式的拓扑差异 |
| Motif分析（Homer） | 识别结合位点富集的DNA序列基序 | 确定直接与间接结合的序列特征 | 输入：ChIP-seq峰；输出：富集基序 | 突变体峰富集AP-1/FRA1基序而非SOX基序（Fig. 2C） | 无法区分直接与间接结合的序列特征 |
| RNA-seq | 全转录组表达分析 | 比较SOX2与突变体的转录调控效应 | 输入：总RNA；输出：差异表达基因 | 两者调控大量不同基因（Fig. 1C） | 无法评估功能后果 |

## 09 关键公式符号

**不适用**。本文为实验生物学研究，未使用数学公式或统计模型。核心分析为ChIP-seq/ATAC-seq/CUT&RUN的峰检测和motif富集分析，使用现有工具（DiffBind、Homer）的默认统计方法，未在文中给出具体公式。

## 10 实验设计与证据链

**数据集/群体**：
- 细胞系：ON S76（人髓母细胞瘤细胞系）
- 293T细胞（用于EMSA的瞬时转染）
- 条件：对照（无Dox）vs Dox诱导（SOX2或SOX2(G76P)表达）
- 生物学重复：ChIP-seq、ATAC-seq、RNA-seq各2个重复（文中提及"Two replicates of each condition were generated"）

**指标**：
- 细胞增殖（MTT assay）
- 差异表达基因数（RNA-seq）
- ChIP-seq峰数及motif富集
- ATAC-seq可及性峰数
- CUT&RUN峰数

**基线**：未处理（无Dox）的i-SOX2-ON S76和i-SOX2(G76P)-ON S76细胞

**预算**：未提供

**骨干/仪器**：Illumina NovaSeq 6000（RNA-seq）；ChIP-seq/ATAC-seq/CUT&RUN测序平台未明确说明

**oracle输入**：不适用（非计算方法）

**评测协议**：差异峰/差异基因通过DiffBind/DEseq2等标准流程分析；motif富集通过Homer findMotifsGenome

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| EMSA | SOX2(G78P)无法直接结合DNA | 野生型SOX2 vs G78P突变体，含SOX基序的DNA探针 | 突变体无特异性DNA-蛋白复合物 | G76P突变破坏DBD直接DNA结合能力 | 未检测突变体是否保留部分弱结合 | Supplemental Fig. S1B |
| 细胞增殖（MTT） | SOX2(G76P)具有生物学活性 | Dox诱导 vs 对照 | 剂量依赖性抑制增殖（~40%） | 突变体虽不能直接结合DNA但仍具功能 | 未比较SOX2与突变体的抑制程度差异 | Fig. 1A, B |
| RNA-seq | SOX2与SOX2(G76P)调控不同基因 | Dox诱导SOX2 vs Dox诱导SOX2(G76P) | 仅568个基因共同上调，699个共同下调 | 两者调控大量不同基因网络 | 未验证差异基因的蛋白水平变化 | Fig. 1C |
| ChIP-seq | SOX2与SOX2(G76P)结合不同基因组位点 | Dox诱导SOX2 vs Dox诱导SOX2(G76P) | 突变体结合位点缺乏SOX基序，富集AP-1/FRA1基序 | SOX2(G76P)通过非直接DNA结合机制结合染色质 | 未进行基序突变验证 | Fig. 2 |
| ATAC-seq | SOX2增加染色质可及性，突变体不能 | Dox诱导SOX2 vs Dox诱导SOX2(G76P) | SOX2增加~33%可及性峰，突变体仅~2.5% | 直接DNA结合是染色质开放的主要驱动力 | 未检测突变体是否通过其他机制影响染色质 | Fig. 3 |
| CUT&RUN | SOX2与SOX2(G76P)结合模式拓扑不同 | Dox诱导SOX2 vs Dox诱导SOX2(G76P) | 突变体CUT&RUN信号弱 | 突变体与DNA距离较远，支持间接结合 | 未进行蛋白-蛋白互作实验直接验证 | Fig. 8 |
| ChIP-seq峰重叠分析 | SOX2与SOX2(G76P)共享部分结合位点 | Dox诱导SOX2 vs Dox诱导SOX2(G76P) | 共享位点缺乏SOX基序但含AP-1基序 | 野生型SOX2也通过间接机制结合部分位点 | 未验证共享位点的功能重要性 | Fig. 7 |

## 11 结论正确解读

- **任务范围**：本文仅在一个细胞系（ON S76髓母细胞瘤）中研究了SOX2及其DNA结合突变体SOX2(G76P)的染色质结合和转录调控效应。结论不能直接推广到其他细胞类型或SOX家族其他成员。
- **oracle/真值输入**：不适用（非计算方法）。
- **端到端状态**：研究为描述性多组学分析，未进行功能验证实验（如报告基因实验、蛋白-蛋白互作实验如Co-IP）来直接证明SOX2(G76P)与AP-1/FRA1的物理互作。
- **算力成本**：不适用。
- **历史数据依赖**：依赖已发表的FRA1 ChIP-seq数据（来自HCT116和MDA-MB-231细胞系），这些数据来自不同细胞类型，可能不完全代表ON S76中的情况。
- **模型依赖**：不适用。
- **最难情形**：SOX2(G76P)在CUT&RUN中信号弱，但ChIP-seq信号强，这种差异被解释为间接结合的证据，但无法完全排除抗体特异性或交联效率差异的替代解释。
- **群体/领域边界**：研究仅限于SOX2在髓母细胞瘤中的行为；SOX2在其他癌症或正常发育中的间接结合机制可能不同。
- **不确定性**：作者未提供SOX2(G76P)与AP-1/FRA1直接物理互作的生化证据；间接结合的分子机制（具体互作蛋白、互作域）尚不明确。

**有边界的复述**：在ON S76髓母细胞瘤细胞中，SOX2(G76P)（DBD突变体）虽不能直接结合DNA，但仍能结合染色质并驱动转录组重编程，其结合位点富集AP-1/FRA1基序而非SOX基序，提示SOX2可通过与其他染色质结合蛋白的间接互作（piggyback机制）调控基因表达。该结论仅限于此细胞系和此突变体，且未提供直接蛋白-蛋白互作证据。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未直接验证蛋白-蛋白互作 | 作者推断SOX2(G76P)通过与其他蛋白（如AP-1）互作间接结合染色质，但未进行Co-IP或类似实验直接证明 | 未明确提及 | Discussion部分："we believe indirect chromatin association at some gene loci is far more likely"（措辞为推测性） |
| 非直接结合位点的功能验证不足 | 未通过报告基因或基因编辑实验验证SOX2(G76P)间接结合位点的功能重要性 | 未明确提及 | Discussion部分 |
| CUT&RUN可能漏检间接结合 | 作者承认CUT&RUN对间接结合的检测可能不敏感 | 未明确提及 | Discussion部分："CUT&RUN may fail to adequately detect transcription factors that associate with chromatin indirectly" |
| 单一细胞系 | 仅在ON S76髓母细胞瘤细胞中验证 | 未明确提及 | 全文 |
| 未鉴定具体互作蛋白 | 作者提出SOX2(G76P)可能与FRA1/AP-1等互作，但未鉴定具体蛋白复合物 | 未明确提及 | Discussion部分 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| SOX2(G76P)的"间接结合"结论主要基于ChIP-seq与CUT&RUN的差异 | ChIP-seq与CUT&RUN的差异可能源于技术因素（如抗体差异、交联效率、MNase消化偏好），而非真实的结合模式差异 | 如果差异是技术性的，则"piggyback"结论可能被高估 | 使用相同抗体进行两种实验；使用不同交联剂（如DSG+甲醛）验证；进行SPR或EMSA验证突变体是否完全无DNA结合 | Results Fig. 2 vs Fig. 8 |
| 未进行蛋白-蛋白互作的直接生化验证 | "piggyback"机制的核心假设是SOX2(G76P)与其他DNA结合蛋白互作，但未提供Co-IP、pull-down或邻近标记（BioID/APEX）证据 | 直接互作证据是"piggyback"结论的关键支撑 | 进行内源性Co-IP；使用BioID或TurboID标记SOX2(G76P)鉴定互作蛋白组 | Discussion部分 |
| 共享位点（Fig. 7）的解读可能过度 | 作者认为SOX2和SOX2(G76P)共享的位点证明野生型SOX2也通过间接机制结合，但共享位点也可能是ChIP-seq的假阳性或抗体交叉反应 | 如果共享位点是技术假象，则"SOX2本身也使用piggyback"的结论不成立 | 对共享位点进行独立验证（如CUT&RUN重复、qPCR）；使用不同SOX2抗体重复实验 | Results Fig. 7 |
| 未比较SOX2与SOX2(G76P)的蛋白表达水平 | 如果突变体蛋白表达水平远高于野生型，可能解释其较强的转录组效应 | 表达水平差异可能混淆功能比较 | 进行定量Western blot或质谱定量比较两种蛋白水平 | Methods节未提及表达水平比较 |
| 未进行时间序列分析 | 转录组和染色质结合分析仅在单一时间点（48h）进行，可能遗漏早期或晚期效应 | 时间动态可区分直接与间接效应 | 进行0h、6h、12h、24h、48h多时间点采样 | Methods节 |
| 未验证SOX2(G76P)是否影响内源性SOX2的功能 | 突变体可能与内源性SOX2竞争互作蛋白，产生显性负效应 | 如果存在显性负效应，观察到的表型可能不反映SOX2(G76P)的独立功能 | 敲低内源性SOX2后表达突变体；或使用SOX2-null细胞系 | 未提及 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **TF功能不限于直接DNA结合**：SOX2(G76P)虽不能直接结合DNA，但仍能通过蛋白-蛋白互作结合染色质并驱动转录组重编程。这提示在构建TF调控网络时，不能仅依赖DNA基序预测，需整合蛋白-蛋白互作信息。

2. **ChIP-seq与CUT&RUN的差异可作为直接/间接结合的判别工具**：直接结合（DBD-DNA）在CUT&RUN中信号强，而间接结合（蛋白-蛋白介导）在CUT&RUN中信号弱但ChIP-seq信号强。这一方法学策略可迁移到其他TF的研究中。

3. **TF突变体策略是解析DBD贡献的有效手段**：通过单点突变（G76P）破坏DBD结构而非完全敲除蛋白，可保留蛋白-蛋白互作能力，从而区分直接与间接结合的贡献。此策略可推广到其他含DBD的TF。

4. **AP-1/FRA1是SOX2间接结合的重要中介**：SOX2(G76P)结合位点富集AP-1基序，且与FRA1 ChIP-seq峰重叠，提示SOX2可能通过FRA1/AP-1复合物间接结合染色质。这为理解SOX2与其他TF的协同调控提供了新线索。

5. **对AI预测模型的启示**：现有TF结合位点预测模型（如基于CNN的DeepSEA、基于Transformer的Enformer）主要基于DNA序列特征，无法预测不依赖DNA基序的间接结合事件。未来模型可整合蛋白-蛋白互作网络和共结合TF信息，以提高预测准确性。

6. **对物理模拟的启示**：TF-DNA互作的分子动力学模拟通常聚焦于DBD-DNA直接互作，但本文提示需考虑TF通过其他蛋白介导的间接DNA结合模式，这扩展了模拟的体系范围。

7. **实验设计范式**：多组学交叉验证（ChIP-seq + ATAC-seq + RNA-seq + CUT&RUN）是解析TF多重功能的高效策略，可系统揭示TF的直接与间接靶点。

## 15 与已有知识连接

- **SOX2 DBD结构**：Reményi et al. 2003解析了SOX2 DBD与DNA的共晶结构，本文的G76P突变正是基于该结构设计的（第76位甘氨酸位于第二α螺旋，该螺旋直接插入DNA小沟）。可连接至PDB结构（如1GT0等SOX2-DNA复合物结构）。
- **TF间接结合先例**：核受体的"tethering"机制（Jakacka et al. 2001；Carroll et al. 2006；Miranda et al. 2013）为本文的"piggyback"概念提供了先例。SOX2可能采用类似的蛋白-蛋白互作介导的染色质结合模式。
- **SOX2 pioneer factor功能**：Soufi et al. 2015报道SOX2作为先锋因子可直接结合核小体DNA并开放染色质。本文的ATAC-seq结果（SOX2增加~33%可及性）与此一致，但SOX2(G76P)仅增加~2.5%，提示直接DNA结合是染色质开放的主要机制。
- **IDR在TF靶点选择中的作用**：Brodsky et al. 2020、Jonas et al. 2025、Abidi et al. 2026等近期研究表明TF的IDR可驱动靶点特异性。本文的SOX2(G76P)保留了IDR，其间接结合能力可能由IDR介导。
- **CUT&RUN技术**：Skene and Henikoff 2017开发了CUT&RUN技术，本文利用该技术区分直接与间接结合，展示了CUT&RUN在TF-染色质互作研究中的新应用。
- **SOX2-OT正反馈环**：本文发现SOX2上调SOX2-OT，而SOX2-OT可上调SOX2表达（Askarian-Amiri et al. 2014），提示SOX2存在正反馈调控环。
- **与AI预测工具的关系**：现有工具如DeepSEA（Zhou and Troyanskaya 2015）、Enformer（Avsec et al. 2021）主要基于DNA序列预测TF结合，本文结果提示这些工具可能系统性遗漏间接结合事件，未来模型需整合蛋白-蛋白互作特征。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：基于蛋白-蛋白互作信息的TF结合位点预测模型
   - **来源局限/观察**：现有TF结合预测模型仅基于DNA序列，无法预测SOX2(G76P)这类不依赖DBD-DNA直接结合的间接结合事件
   - **核心假设**：整合蛋白-蛋白互作网络和共结合TF的ChIP-seq数据可显著提高TF结合位点预测的召回率
   - **初步方法**：构建多模态深度学习模型，输入为DNA序列+目标TF的蛋白-蛋白互作网络特征+共结合TF的ChIP-seq峰信号，输出为TF结合概率；在SOX2及其他已知存在间接结合机制的TF（如核受体）上验证
   - **验证方式**：与现有工具（DeepSEA、Enformer）在独立ChIP-seq数据集上比较AUROC/AUPRC；重点评估无基序结合位点的预测能力
   - **创新状态**：unverified

2. **候选名称**：TF直接/间接结合模式的分子动力学判别方法
   - **来源局限/观察**：本文通过ChIP-seq/CUT&RUN差异推断间接结合，但缺乏原子级结构证据
   - **核心假设**：TF-染色质复合物的结构特征（如DBD-DNA接触面积、蛋白-蛋白界面）可用于判别直接与间接结合模式
   - **初步方法**：对SOX2和SOX2(G76P)与核小体/AP-1复合物进行粗粒化MD模拟，比较结合自由能、接触面积和构象动力学差异；开发基于结构特征的分类器
   - **验证方式**：与本文ChIP-seq/CUT&RUN数据交叉验证；在已知直接/间接结合的TF对（如核受体-AP-1）上测试
   - **创新状态**：unverified

3. **候选名称**：SOX2间接结合位点的功能验证与保守性分析
   - **来源局限/观察**：本文未对SOX2(G76P)间接结合位点进行功能验证，且仅在单一细胞系中研究
   - **核心假设**：SOX2间接结合位点在多种细胞类型中保守，且对SOX2驱动的转录程序具有功能重要性
   - **初步方法**：在多种SOX2高表达癌症细胞系（小细胞肺癌、胶质母细胞瘤）中重复ChIP-seq/ATAC-seq；对间接结合位点进行CRISPR干扰（CRISPRi）验证功能；跨物种保守性分析
   - **验证方式**：间接结合位点扰动后目标基因表达变化；保守性评分与功能重要性相关性
   - **创新状态**：unverified

4. **候选名称**：SOX2 IDR介导间接结合的机制解析
   - **来源局限/观察**：本文未鉴定SOX2(G76P)间接结合的具体互作蛋白，也未明确IDR的贡献
   - **核心假设**：SOX2的C端IDR（含反式激活域）通过与AP-1/FRA1等TF的直接互作介导间接染色质结合
   - **初步方法**：构建SOX2 IDR截短突变体；进行Co-IP/MS鉴定互作蛋白组；使用BioID邻近标记在活细胞中捕获瞬时互作；AlphaFold-Multimer预测SOX2 IDR与FRA1的互作界面
   - **验证方式**：IDR截短后间接结合位点丢失；互作蛋白组与ChIP-seq峰重叠分析
   - **创新状态**：unverified

5. **候选名称**：基于图神经网络的TF协同结合预测
   - **来源局限/观察**：SOX2(G76P)的间接结合位点富集AP-1基序，提示TF-TF协同结合是间接结合的重要机制
   - **核心假设**：TF-TF协同结合模式可通过图神经网络从蛋白-蛋白互作网络和共结合数据中学习
   - **初步方法**：构建TF-基因调控图，节点为TF和基因，边为ChIP-seq共结合和蛋白-蛋白互作；使用GNN预测TF在特定基因座的结合模式（直接/间接/协同）
   - **验证方式**：在独立数据集上验证预测准确性；与本文SOX2/SOX2(G76P)数据对比
   - **创新状态**：unverified