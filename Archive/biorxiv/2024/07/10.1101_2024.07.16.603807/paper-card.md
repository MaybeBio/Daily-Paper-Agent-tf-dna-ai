## 01 基本信息

- **标题**：PAX proteins in silico prediction in Lissachatina fulica
- **作者与单位**：Dominova IN; Golovneva K; Korshunova N; Zhukov VV（单位：Immanuel Kant Baltic Federal University，俄罗斯）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2024
- **论文类型**：计算/生物信息学预测研究（未提供实验验证）
- **领域**：比较基因组学、转录因子（TF）家族鉴定、蛋白质结构预测、分子对接
- **关键词**：PAX proteins; Lissachatina fulica; Paired box domain; molecular docking; HADDOCK; AlphaFold2
- **DOI/arXiv 号**：10.1101/2024.07.16.603807
- **代码**：未提供
- **数据**：GigaDB 数据库（http://gigadb.org/dataset/100647）；NCBI Protein 数据库；补充材料 Table S1、S2
- **阅读日期**：2025年（未提供具体日期）
- **在该课题方向中的位置**：本文属于「蛋白质-DNA互作 × AI/物理模拟」方向中的**TF家族鉴定与DNA结合能力预测**子类。核心方法链为：同源搜索（HMMER）→ 结构预测（AlphaFold2）→ DNA-蛋白对接（HADDOCK）→ 系统发育分析。对TF–DNA结合机制课题的可迁移价值在于：展示了**无实验数据条件下，利用计算管线对新型物种TF家族进行从头鉴定与DNA结合能力评估**的完整流程，尤其是HADDOCK对接评分与Z-score在评估TF-DNA亲和力中的应用。

---

## 02 一句话总结

本文通过HMMER同源搜索在非洲大蜗牛 *Lissachatina fulica* 基因组中预测出8个含Paired box结构域的PAX家族蛋白，利用AlphaFold2预测其3D结构，并通过HADDOCK分子对接比较其与DNA的结合能力，结合系统发育分析将其归入5个PAX亚家族（I、III、IV、β、Pox-Neuro），为后续研究该物种PAX蛋白在再生中的功能提供序列基础。

---

## 03 研究问题

- **具体问题**：*Lissachatina fulica*（非洲大蜗牛）基因组中是否存在编码PAX家族转录因子的基因？这些基因的蛋白产物是否具有DNA结合能力？它们属于哪些PAX亚家族？
- **为什么重要**：*L. fulica* 具有再生眼触角的能力，而PAX蛋白（尤其是PAX6）在眼发育中起关键作用。但该物种缺乏注释基因组，无法直接获取PAX蛋白序列，阻碍了对其再生分子机制的探索。
- **现有方法为何不足**：*L. fulica* 基因组未注释，无法直接通过关键词搜索获取PAX蛋白；仅依赖BLAST可能遗漏低相似度序列；缺乏结构层面的验证手段来确认预测序列的DNA结合功能。
- **精确的"Can ... ?"问题**：Can we identify PAX family transcription factors in the unannotated genome of *Lissachatina fulica* through homology-based search, and can their DNA-binding capability be computationally validated via molecular docking?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及参考文献构建，属于「经外部核验」的领域发展概述。

1. **PAX基因家族的发现与命名（1980s-1990s）**：PAX基因因"paired box"而得名，该结构域最初在果蝇 *paired (Prd)* 和 *gooseberry (Gsb)* 基因之间发现（Bopp et al.）。后续被证实编码序列特异性DNA结合活性（Underhill 2012）。
2. **PAX结构域的结构解析（2000s）**：PAX蛋白的Paired box结构域被解析为128个氨基酸的双亚结构域（N端PAI + C端RED），形成三螺旋折叠，C端含HTH基序，PAI含β-turn和β-wing，均参与DNA结合（Underhill 2000; Apuzzo et al. 2004）。
3. **PAX亚家族分类体系建立（1990s-2000s）**：基于结构域组成和功能，PAX蛋白被分为4个常见亚家族（I-IV），后补充无脊椎动物特有的Pox-Neuro和PAX-β亚家族（Mansouri et al. 1999; Friedrich 2015; Schmerer et al. 2009）。
4. **软体动物PAX蛋白研究（2010s-2020s）**：Navet et al. (2017) 对软体动物PAX蛋白进行系统分析，发现Lophotrochozoa中PAX2/5/8缺乏homeodomain，Gastropoda缺乏octapeptide等谱系特异性特征。
5. **计算结构预测与对接技术成熟（2020s）**：AlphaFold2（2021）实现高精度单体结构预测；HADDOCK等对接工具支持信息驱动的蛋白-DNA复合物建模。本文首次将这些技术系统应用于软体动物PAX蛋白的从头鉴定。

**本文主张的位置**：在无注释基因组背景下，整合同源搜索、结构预测和分子对接三种计算手段，建立从序列到DNA结合能力的完整预测管线，填补 *L. fulica* PAX蛋白研究的空白。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 基因组未注释 | 无法直接获取PAX蛋白序列 | *L. fulica* 缺乏注释基因组 | Introduction: "lack of an annotated genome for L. fulica" |
| 同源搜索可能遗漏 | 仅靠BLAST可能无法识别低相似度PAX序列 | PAX蛋白在不同物种间序列差异大，尤其无脊椎动物存在谱系特异性结构变异 | Methods: 使用HMMER+HMM profile而非仅BLAST |
| 序列鉴定不等于功能验证 | 仅确认Paired box结构域存在不足以证明DNA结合能力 | 部分预测序列含不完整结构域（如仅PAI或仅RED），需结构水平验证 | Results: 发现Afu004298仅含PAI，Afu016671/672含部分PAI |
| 亚家族归属不确定 | 序列特征与多个亚家族重叠 | PAX蛋白结构域组合多样，存在中间类型 | Results: Afu015865和Afu004298在系统发育树上位于亚家族I和II之间 |
| 缺乏实验验证手段 | 无法通过湿实验确认预测蛋白的功能 | 该物种缺乏遗传操作工具，且本研究为纯计算分析 | Discussion: 提出后续需通过转录本搜索和表达分析验证 |

---

## 06 核心思想

### 1) 表面方法

一条四步计算管线：(1) 从NCBI收集3个软体动物纲（腹足纲、头足纲、双壳纲）的91条已知PAX/Paired box蛋白序列，构建多序列比对并生成HMM profile；(2) 用HMMER的hmmsearch在 *L. fulica* 预测蛋白组（GigaDB）中搜索候选序列（E-value < 10⁻⁵）；(3) 对候选序列进行结构域注释（InterProScan）、二级结构预测（RaptorX-Property）和3D结构预测（AlphaFold2）；(4) 用HADDOCK 2.4将候选蛋白的Paired box结构域与B-DNA（PDB: 1BNA）对接，以已知Paired box结构域（PDB: 1PDN）为阳性对照，比较结合能、Z-score和RMSD。

### 2) 核心洞察

- **结构域完整性是功能预测的关键**：并非所有含Paired box同源序列的蛋白都具有完整的DNA结合能力。作者通过结构域注释发现部分候选序列仅含PAI亚结构域（如Afu004298）或部分PAI（如Afu016671/672），提示这些蛋白可能具有不同的DNA结合特性或功能。
- **多证据交叉验证**：单一方法（如仅系统发育或仅结构域搜索）不足以确定亚家族归属。本文综合结构域组成、系统发育位置、特征基序（如octapeptide、homeodomain）和对接结果，对每个候选蛋白进行多维度判定。
- **对接评分可区分结合亲和力**：HADDOCK的Z-score和RMSD提供了相对定量的DNA结合能力比较。Afu004298（仅含PAI）的Z-score（-2.3）优于完整Paired box结构域对照（-2.1），提示PAI亚结构域本身可能足以介导DNA结合，与文献中PAI是DNA结合主要亚结构域的观点一致。

### 3) 可能的普适教训 [Analysis]

- **对未注释基因组的TF鉴定，HMM profile优于简单BLAST**：HMM能捕获远程同源关系，尤其适用于结构域序列保守但全长序列差异大的TF家族。
- **结构预测与对接可作为TF-DNA结合能力的功能代理**：在缺乏湿实验条件时，AlphaFold2+HADDOCK管线可提供中等通量的功能预测，但需注意对接评分的解读应结合结构域组成分析。
- **谱系特异性结构变异是TF分类的陷阱**：软体动物PAX蛋白存在亚家族特异性结构域缺失（如Lophotrochozoa的PAX2/5/8无homeodomain），跨物种TF鉴定时需考虑谱系特异性特征，不能简单套用脊椎动物分类标准。

---

## 07 方法总览

- **输入**：
  - 91条软体动物PAX/Paired box蛋白序列（NCBI Protein，来自Cephalopoda、Gastropoda、Bivalvia）
  - *L. fulica* 预测蛋白组（GigaDB, Guo et al. 2019）
  - B-DNA结构（PDB ID: 1BNA）
  - Paired box结构域晶体结构（PDB ID: 1PDN，去DNA后作为对照）
- **输出**：
  - 8个*L. fulica* PAX候选蛋白序列及其亚家族注释
  - 每个候选蛋白的3D结构模型（AlphaFold2）
  - 候选蛋白Paired box结构域与DNA的对接评分（HADDOCK score、Z-score、RMSD等）
- **模块**：
  1. 数据收集与过滤（NCBI Protein检索，排除PREDICTED/LOW QUALITY/hypothetical）
  2. 多序列比对（Clustal Omega + MUSCLE，100次迭代）
  3. HMM profile构建与搜索（HMMER 3.4, hmmsearch, E-value < 10⁻⁵）
  4. 结构域注释（InterProScan）
  5. 二级结构预测（RaptorX-Property）
  6. 3D结构预测（AlphaFold2 Colab + MMseqs2）
  7. DNA-蛋白对接（HADDOCK 2.4，仅用Paired box结构域区域）
  8. 系统发育分析（MEGA X, ML + LG+F模型, 1000 bootstrap）
  9. BLAST验证（对NCBI refseq_protein数据库）
- **训练**：无监督/无训练过程；HMM profile基于已有序列比对构建，AlphaFold2为预训练模型
- **反馈回路**：系统发育结果与结构域注释相互印证；对接结果与结构域完整性关联分析
- **文字流程**：收集已知PAX序列 → 多序列比对 → 构建HMM profile → 在*L. fulica*蛋白组中搜索 → 候选序列经InterProScan验证Paired box结构域 → AlphaFold2预测3D结构 → 提取Paired box结构域区域与B-DNA进行HADDOCK对接 → 以1PDN为对照比较结合能力 → 结合结构域组成、系统发育和BLAST结果确定亚家族归属

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| HMM profile构建与搜索（HMMER） | 在*L. fulica*蛋白组中识别PAX同源序列 | 仅靠BLAST可能遗漏远程同源序列；HMM能捕获结构域级保守性 | 输入：91条已知PAX蛋白比对；输出：10条候选序列（E<10⁻⁵） | Methods: "HMMER software...hmmsearch algorithm" | 预期影响：可能遗漏低相似度PAX序列，或引入更多假阳性（需后续结构域验证） |
| 结构域注释（InterProScan） | 确认候选序列含Paired box结构域 | 排除假阳性；区分完整/部分结构域 | 输入：10条候选序列；输出：8条含Paired box的序列 | Results: "two sequences...were found not to belong to the PAX protein family" | 实测效应：排除2条仅含homeodomain的序列（Afu015311, Afu004437） |
| 3D结构预测（AlphaFold2） | 生成候选蛋白的三维结构模型 | 为对接提供结构输入；评估结构可靠性 | 输入：8条候选序列；输出：5个模型/序列，按pLDDT排序 | Methods: "AlphaFold2 Colab...pLDDT reliability index" | 预期影响：无法评估预测结构的构象多样性对对接结果的影响 |
| DNA-蛋白对接（HADDOCK 2.4） | 评估Paired box结构域与DNA的结合能力 | 提供功能验证的计算证据 | 输入：候选蛋白Paired box结构域 + B-DNA（1BNA）；输出：HADDOCK score、Z-score、RMSD | Results: Table 2 | 实测效应：Afu004298（仅PAI）Z-score最高（-2.3），提示PAI足以结合DNA |
| 系统发育分析（MEGA X） | 确定候选序列的亚家族归属 | 结构域组成不足以唯一确定亚家族 | 输入：候选序列+已知PAX序列；输出：ML树 | Results: Fig. 3 | 预期影响：无法区分近期基因复制与直系同源关系 |
| BLAST验证 | 交叉验证系统发育结果 | 系统发育树可能受长枝吸引等伪影影响 | 输入：候选序列 vs NCBI refseq_protein；输出：相似性百分比 | Results: Table 3 | 实测效应：BLAST与系统发育结果不完全一致（如Afu015865/Afu004298） |

---

## 09 关键公式符号

本文未提供明确的数学公式。涉及的关键计算指标如下：

- **E-value（HMMER）**：hmmsearch输出的期望值，表示随机匹配到该得分的期望次数。阈值设为10⁻⁵。
- **HADDOCK score**：HADDOCK的加权评分函数，综合范德华能、静电能、约束能、溶剂化能等项（具体权重未在文中给出）：
  \[
  \text{HADDOCK score} = w_1 E_{\text{vdw}} + w_2 E_{\text{elec}} + w_3 E_{\text{air}} + w_4 E_{\text{solv}} + \ldots
  \]
  其中 \( E_{\text{air}} \) 为ambiguous interaction restraints（AIR）违反能。文中报告了score、Z-score、RMSD、静电能、范德华能、约束能等指标（Table 2）。
- **Z-score**：HADDOCK cluster的Z-score，定义为该cluster平均得分与所有cluster平均得分的偏差除以标准差，越负表示结合越强。
- **pLDDT（AlphaFold2）**：per-residue predicted local Distance Difference Test，0-100分，衡量每个残基的预测置信度。
- **RMSD**：均方根偏差，用于评估对接模型与参考结构的偏差。

---

## 10 实验设计与证据链

### 数据集/群体/规模
- **已知PAX序列集**：91条（Gastropoda 29条，Cephalopoda 9条，Bivalvia 53条），来自NCBI Protein数据库
- **目标蛋白组**：*L. fulica* 预测蛋白组（GigaDB, Guo et al. 2019），具体规模未提供
- **候选序列**：10条（HMMER预测）→ 8条（结构域验证后）
- **阳性对照**：Paired box结构域晶体结构（PDB ID: 1PDN，去除DNA后）
- **DNA底物**：B-DNA（PDB ID: 1BNA）
- **系统发育分析**：5个软体动物纲的PAX序列（Gastropoda, Cephalopoda, Bivalvia, Aplacophora, Polyplacophora）

### 指标
- HMMER E-value
- InterProScan结构域注释
- HADDOCK score、Z-score、RMSD、静电能、范德华能、约束能
- 系统发育树拓扑（ML, LG+F模型, 1000 bootstrap）
- BLAST identity百分比

### 评测协议
- 无独立测试集；通过阳性对照（1PDN）的对接结果作为参考基准
- 系统发育分析采用多物种序列集，bootstrap支持率评估分支可靠性

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| HMMER搜索 | *L. fulica* 基因组含PAX同源序列 | 91条已知PAX序列构建的HMM profile vs *L. fulica* 蛋白组 | 10条候选序列（E<10⁻⁵） | *L. fulica* 基因组编码PAX同源蛋白 | 不能证明这些序列具有功能 | Results: Table 1 |
| InterProScan结构域验证 | 候选序列含Paired box结构域 | 10条候选 vs InterPro数据库 | 8条含Paired box；2条仅含homeodomain | 8条序列属于PAX家族 | 不能确定结构域是否完整/功能 | Results: "two sequences...not belong to PAX" |
| HADDOCK对接 | 候选Paired box结构域能结合DNA | 8条候选 + 1PDN对照 vs B-DNA（1BNA） | 所有候选均有对接信号；Afu004298 Z-score最高（-2.3） | 候选蛋白具有DNA结合潜力 | 对接评分不能等同于体内亲和力；未做突变验证 | Results: Table 2 |
| 系统发育分析 | 候选序列可归入已知PAX亚家族 | 候选序列 + 5纲软体动物PAX序列 | 8条序列分属5个亚家族（I, III, IV, β, Pox-Neuro） | *L. fulica* PAX蛋白覆盖多个亚家族 | 部分分支bootstrap支持率未报告；Afu015865/Afu004298位置不确定 | Results: Fig. 3 |
| BLAST验证 | 系统发育结果可被序列相似性支持 | 候选 vs NCBI refseq_protein | 与系统发育结果部分一致 | 交叉验证了部分归属 | BLAST与系统发育结果存在不一致（如Afu015865/Afu004298） | Results: Table 3 |

---

## 11 结论正确解读

- **任务范围**：本研究是**纯计算预测**，不包含任何湿实验验证（如RT-PCR、EMSA、ChIP-seq等）。所有结论均为"预测"性质。
- **oracle/真值输入**：无真值标签。阳性对照为已知Paired box结构域（1PDN）的DNA结合能力，但该对照仅用于对接评分的相对比较，不构成对候选蛋白功能的直接验证。
- **端到端状态**：管线从基因组序列到功能预测是端到端的，但每个环节的误差会累积。HMMER搜索可能遗漏或误报；AlphaFold2对无同源模板的序列预测可靠性有限；HADDOCK对接评分与体内结合亲和力的相关性未经校准。
- **算力成本**：未报告。AlphaFold2和HADDOCK均为计算密集型工具，但本文未提供运行时间或资源需求。
- **历史数据依赖**：高度依赖NCBI中已有软体动物PAX序列的注释质量。若已知序列集存在错误注释或采样偏差，会影响HMM profile的准确性。
- **模型依赖**：结果依赖于HMMER、AlphaFold2、HADDOCK三个工具的默认/选定参数。不同版本或参数可能导致不同结果。
- **最难情形**：部分候选序列含不完整Paired box结构域（如Afu004298仅含PAI，Afu016671/672含部分PAI），这些序列的DNA结合能力预测不确定性最高。
- **群体/领域边界**：结论仅适用于 *L. fulica* 的预测蛋白组，外推到其他软体动物或物种需谨慎。PAX亚家族分类基于现有软体动物序列，可能随新序列加入而改变。
- **不确定性**：作者未提供置信区间或不确定性量化。系统发育树的bootstrap值未完整报告。

**有边界的复述**：在 *L. fulica* 预测蛋白组中，存在8个含Paired box结构域的序列，计算分析提示它们可能属于5个PAX亚家族，且其Paired box结构域在体外对接模拟中显示出DNA结合潜力，其中Afu004298（仅含PAI亚结构域）的预测结合能力最强。这些预测需通过转录本验证和功能实验确认。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 缺乏实验验证 | 所有预测均为计算分析，未进行湿实验确认 | 后续需搜索*L. fulica*不同发育阶段的转录本，确认这些基因的表达 | Discussion: "the further stage of studying the identified sequences...will involve searching for transcripts" |
| 基因组未注释的限制 | 预测基于GigaDB的预测蛋白组，可能不完整或有错误 | 未明确提及 | Introduction: "lack of an annotated genome for L. fulica" |
| PAX-β和Pox-Neuro亚家族数据有限 | 软体动物中Pox-Neuro仅有一个已知序列，限制系统发育分析 | 未明确提及 | Discussion: "only one amino acid sequence of Pox-Neuro is known for molluscs" |
| 部分序列结构域不完整 | Afu004298仅含PAI，Afu016671/672含部分PAI，功能预测不确定性高 | 未明确提及 | Results: "a few sequences were found to contain partial Paired box domain" |
| BLAST与系统发育结果不一致 | 部分序列的BLAST最佳匹配与系统发育归属不符 | 未明确提及 | Results: Table 3 vs Fig. 3 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| HMMER搜索的灵敏度未报告 | 未提供搜索的假阳性/假阴性率；E-value阈值10⁻⁵可能过严或过松 | 影响候选序列的完整性和可靠性 | 可用已知PAX序列做jackknife测试，或与BLAST结果对比召回率 | Methods: 未提供搜索统计 |
| HADDOCK对接未设置阴性对照 | 仅用1PDN作为阳性对照，未用非DNA结合蛋白或突变体作为阴性对照 | 无法判断对接评分的特异性 | 加入已知非DNA结合蛋白（如GFP）作为阴性对照 | Results: Table 2 |
| 对接仅用Paired box结构域而非全长蛋白 | 全长蛋白中其他结构域可能影响DNA结合特异性或亲和力 | 可能高估或低估实际结合能力 | 对全长蛋白进行对接，或至少包含连接区域 | Methods: "Only the Paired box domain sequence was considered for docking" |
| 系统发育分析中PAX-β和Pox-Neuro的采样不足 | Pox-Neuro仅1条已知序列，PAX-β可能缺乏外群 | 亚家族归属可能不稳定 | 增加更多软体动物物种的PAX序列，或使用不同的建树方法 | Discussion: "only one amino acid sequence of Pox-Neuro is known" |
| 未报告AlphaFold2模型的pLDDT分数分布 | 低pLDDT区域的结构不可靠，但未说明哪些区域用于对接 | 对接结果可能基于不可靠的结构区域 | 报告每个模型各结构域的pLDDT分数，排除低置信度区域 | Methods: 仅提及"highest pLDDT index" |
| 未讨论PAX蛋白的异构体/剪接变体 | 预测蛋白组可能不包含所有剪接变体 | 可能遗漏功能重要的PAX异构体 | 与转录组数据比对，确认剪接变体 | 未提供 |
| 缺乏与其他软体动物PAX预测的定量比较 | 未与已发表的软体动物PAX蛋白预测做系统比较 | 无法评估预测的准确性和新颖性 | 与Navet et al. 2017等已发表数据做序列相似性和结构域组成比较 | Discussion: 仅定性引用 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **HMM profile是未注释基因组中TF家族鉴定的首选工具**：相比BLAST，HMM能捕获结构域级远程同源性，适用于PAX这类结构域保守但全长序列差异大的TF家族。可迁移到其他TF家族（如Homeobox、bHLH、Zinc finger）的从头鉴定。
2. **结构域完整性分析应作为TF鉴定的必要步骤**：本文发现部分候选序列仅含部分Paired box结构域（如仅PAI），这直接影响功能预测。在TF–DNA结合机制研究中，应区分完整/部分DNA结合结构域，避免将非典型序列误判为功能TF。
3. **HADDOCK对接可作为TF-DNA结合能力的计算筛选工具**：通过比较Z-score和RMSD，可在无实验数据时对候选TF的DNA结合能力进行相对排序。但需注意：(a) 设置阴性对照；(b) 仅用DNA结合结构域对接可能丢失全长蛋白的调控信息；(c) 对接评分与体内亲和力的相关性需校准。
4. **多证据交叉验证是TF亚家族分类的稳健策略**：本文综合结构域组成、特征基序、系统发育和BLAST结果，而非依赖单一方法。对TF–DNA互作研究，建议至少结合序列相似性、结构域组成和系统发育三个维度。
5. **谱系特异性结构变异是跨物种TF注释的陷阱**：软体动物PAX蛋白存在亚家族特异性结构域缺失（如Lophotrochozoa的PAX2/5/8无homeodomain），提示在非模式生物中注释TF时，不能简单套用模式生物的域组成规则。
6. **AlphaFold2结构预测与对接的管线可迁移**：本文展示了"序列→结构→功能"的计算管线，可推广到其他TF家族与DNA的互作预测，但需注意AlphaFold2对无同源模板序列的预测置信度评估。
7. **PAX蛋白亚家族分类需考虑"部分结构域"中间类型**：Afu004298仅含PAI但具有强DNA结合预测，提示PAI亚结构域本身可能足以介导DNA结合。这与TF–DNA结合机制研究中"最小DNA结合单元"的确定直接相关。

---

## 15 与已有知识连接

1. **PAX结构域结构与DNA结合机制（Underhill 2000; Apuzzo et al. 2004）**：本文引用的经典文献确立了Paired box结构域的双亚结构域（PAI/RED）三螺旋折叠模型。本文的预测结果与该模型一致——含完整PAI+RED的序列（如Afu015865）预测结合能力较强，而仅含部分结构域的序列（如Afu004298）结合模式可能不同。可进一步用分子动力学（MD）模拟验证PAI单独结合DNA的构象变化。

2. **软体动物PAX蛋白谱系特异性特征（Navet et al. 2017）**：Navet等发现Lophotrochozoa的PAX2/5/8缺乏homeodomain、Gastropoda缺乏octapeptide。本文结果与之一致，并进一步发现*L. fulica* PAX蛋白存在部分Paired box结构域缺失的变异。这提示TF结构域的获得/缺失在软体动物中可能比脊椎动物更频繁。

3. **PAX6与眼发育（Yoshida et al. 2014）**：头足类PAX6通过可变剪接产生多种异构体参与眼发育。本文预测的Afu013869（PAX6）缺乏homeodomain但保留octapeptide，与头足类PAX6变异体类似。这为研究*L. fulica*眼再生中PAX6的异构体功能提供了候选序列。

4. **HADDOCK在蛋白-DNA对接中的应用（Van Zundert et al. 2016）**：HADDOCK是信息驱动的对接工具，本文将其应用于TF-DNA结合能力评估。与更严格的MD模拟（如GROMACS、AMBER）相比，HADDOCK计算成本低但精度有限。后续可对高分候选（如Afu004298）进行MD模拟验证结合稳定性。

5. **AlphaFold2在TF结构预测中的应用（Mirdita et al. 2022）**：本文使用ColabFold（AlphaFold2+MMseqs2）进行结构预测。AlphaFold2对单体结构预测精度高，但对蛋白-DNA复合物的预测能力有限，因此本文仅用其生成单体结构，再通过对接研究DNA结合。这与当前领域"AlphaFold2预测单体+对接研究互作"的主流范式一致。

6. **PAX-β亚家族（Schmerer et al. 2009; Franke et al. 2015）**：PAX-β是Lophotrochozoa特有的PAX亚家族，功能尚不明确。本文预测的Afu023584属于PAX-β，且BLAST匹配到Mucin-5AC（与Navet et al. 2017的发现一致），提示PAX-β可能与其他蛋白存在序列相似性混淆，需谨慎注释。

7. ***L. fulica* 基因组资源（Guo et al. 2019）**：本文使用的蛋白组来自Guo等发表的基因组文章，该资源为后续研究提供了基础。但预测蛋白组的质量直接影响本文结果，建议后续用转录组数据验证这些预测基因的表达。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选1：基于MD模拟的PAX亚家族DNA结合特异性比较
- **名称**：PAX亚家族DNA结合特异性的分子动力学比较研究
- **来源局限/观察**：本文仅用HADDOCK对接评估了*L. fulica* PAX蛋白与通用B-DNA的结合能力，未考虑序列特异性。HADDOCK的Z-score提供了相对亲和力排序，但无法揭示不同PAX亚家族对DNA序列的偏好性。
- **核心假设**：不同PAX亚家族（I/III/IV/β/Pox-Neuro）的Paired box结构域对DNA序列具有不同的结合偏好，且这种偏好可通过MD模拟的相互作用能量分解来量化。
- **初步方法**：(1) 选取本文预测的8个*L. fulica* PAX蛋白及已知晶体结构（如PAX6-DNA复合物PDB: 6PAX）作为参考；(2) 使用HADDOCK或NPDock将各Paired box结构域与不同DNA序列（如TAAT、CGAT等已知PAX结合基序）对接；(3) 对高评分复合物进行显式溶剂MD模拟（AMBER或GROMACS，100-500ns）；(4) 计算MM/PBSA结合自由能及残基能量分解，比较各亚家族的DNA结合界面。
- **验证方式**：与已知PAX蛋白-DNA共晶结构比对；如可能，用EMSA实验验证预测的序列偏好。
- **创新状态**：unverified

### 候选2：部分Paired box结构域蛋白的功能意义
- **名称**：仅含PAI亚结构域的PAX蛋白：*L. fulica* Afu004298的DNA结合机制与功能启示
- **来源局限/观察**：本文发现Afu004298仅含PAI亚结构域，但HADDOCK预测其DNA结合能力最强（Z-score = -2.3）。这与"完整Paired box结构域是DNA结合所必需"的传统观点矛盾。
- **核心假设**：PAI亚结构域本身足以介导序列特异性DNA结合，且其结合模式可能与完整Paired box结构域不同（如更依赖β-wing与DNA小沟的接触）。
- **初步方法**：(1) 对Afu004298的PAI结构域进行MD模拟（apo和DNA结合态）；(2) 与完整Paired box结构域（如Afu015865）的DNA结合模式进行对比；(3) 分析PAI结构域与DNA的氢键网络和疏水接触；(4) 搜索其他物种中仅含PAI的PAX类似蛋白，评估其进化分布。
- **验证方式**：如能获得重组蛋白，用EMSA或表面等离子共振（SPR）验证PAI结构域的DNA结合能力。
- **创新状态**：unverified

### 候选3：PAX蛋白在*L. fulica*眼再生中的表达动态
- **名称**：*L. fulica* 眼触角再生过程中PAX基因表达动态的计算预测与验证
- **来源局限/观察**：本文仅预测了PAX蛋白序列，未涉及其表达模式。作者在讨论中明确提出下一步需搜索转录本。
- **核心假设**：*L. fulica* 眼触角再生过程中，不同PAX亚家族基因（尤其是PAX6对应基因Afu013869）呈现时序性表达变化，且与神经发生和眼形态发生的已知通路相关。
- **初步方法**：(1) 从GigaDB或SRA获取*L. fulica*不同发育阶段/再生时间点的转录组数据；(2) 用本文预测的8个PAX序列作为查询，进行转录本组装和定量；(3) 分析PAX基因在再生过程中的表达动态；(4) 与已发表的软体动物PAX表达数据（如*Haliotis*、*Lymnaea*）比较。
- **验证方式**：原位杂交（ISH）或定量RT-PCR验证关键时间点的表达。
- **创新状态**：unverified

### 候选4：PAX蛋白-DNA结合的计算-实验联合验证框架
- **名称**：从序列预测到结合验证：软体动物TF-DNA互作的计算-实验联合框架
- **来源局限/观察**：本文的纯计算管线缺乏实验验证，且未提供可重复使用的代码或数据集。
- **核心假设**：通过整合HMMER（同源搜索）、AlphaFold2（结构预测）、HADDOCK（对接）和有限的实验验证（如EMSA），可以建立适用于非模式生物TF-DNA互作研究的标准化流程。
- **初步方法**：(1) 将本文的8个PAX蛋白作为测试集；(2) 对每个蛋白进行HADDOCK对接，选择评分最高的DNA复合物；(3) 用荧光各向异性或EMSA验证2-3个代表性蛋白的DNA结合；(4) 将实验数据与计算评分关联，建立校准模型；(5) 发布可复现的流程（如Snakemake/CWL工作流）。
- **验证方式**：实验数据与计算预测的一致性；流程在另一个非模式物种（如*Biomphalaria glabrata*）上的可迁移性。
- **创新状态**：unverified

### 候选5：PAX蛋白结构域组合的进化分析
- **名称**：软体动物PAX蛋白结构域组合的进化动态：部分结构域缺失的适应意义
- **来源局限/观察**：本文发现*L. fulica* PAX蛋白存在多种结构域组合变异（如仅PAI、PAI+部分homeodomain等），但未进行进化分析。
- **核心假设**：软体动物PAX蛋白的结构域组合变异是谱系特异性适应，可能与特定发育过程（如神经发生、再生）的功能分化相关。
- **初步方法**：(1) 从NCBI/Ensembl收集更多软体动物（腹足纲、头足纲、双壳纲、多板纲）的PAX蛋白序列；(2) 注释各序列的结构域组成；(3) 构建结构域组合的进化网络；(4) 分析结构域缺失/获得与物种生态位、发育模式的相关性。
- **验证方式**：与已发表的软体动物系统发育树整合，检验结构域变异的系统发育信号。
- **创新状态**：unverified