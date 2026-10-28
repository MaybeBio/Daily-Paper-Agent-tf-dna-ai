## 01 基本信息

- **标题**：An atlas of TF driven gene programs across human cells
- **作者**：Pett JP; Prete M; Pham D; England N; Yuan H; Prigmore E; Tuck L; Oszlanczi A; To K; Xu C; Suo C; Dann E; He P; Kedlian V; Kanemaru K; Cranley J; Yang L; Elmentaite R; Oliver AJ; Cujba A; Cakir B; Murray S; Mahbubani KT; Saeb-Parsy K; Gambardella L; Haniffa M; Nawijn MC; Teichmann SA; Meyer KB
- **单位**：未提供（根据作者列表推测涉及Wellcome Sanger Institute、剑桥大学等，但原文未明确列出）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2025
- **论文类型**：资源型/方法型研究（构建数据库资源并展示应用）
- **领域**：单细胞基因组学、基因调控网络、转录因子调控
- **关键词**：transcription factors, regulons, single cell, Human Cell Atlas, gene regulatory networks, enhancer-GRN, GWAS
- **DOI/arXiv 号**：10.1101/2025.05.30.657075
- **代码**：https://github.com/Teichlab/cellregulondb
- **数据**：ArrayExpress E-MTAB-14583；processed data 可通过 CELLxGENE 获取；数据库网站 https://www.cellregulondb.org
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文属于「蛋白质-DNA互作（TF–DNA结合机制）× AI/深度学习/物理模拟」方向中的**数据资源与调控网络推断**类别。它不直接预测TF-DNA三维结合结构，而是利用大规模单细胞转录组数据，通过共表达+motif富集（pySCENIC）推断细胞类型特异的TF→靶基因调控程序（regulons），并进一步整合ATAC-seq数据构建增强子-基因调控网络（eGRN）。对本课题的可迁移价值在于：提供了TF调控程序的系统化资源、TF-靶基因关系的细胞类型特异性注释，以及将GWAS风险变异映射到调控网络的完整分析流程。

---

## 02 一句话总结

本文利用约500万个人类单细胞转录组数据，通过pySCENIC流程推断出覆盖15个器官系统、500余种细胞类型的约70万个细胞类型/组织特异的TF-靶基因调控程序（regulons），构建了CellRegulon数据库，并进一步整合新生成的人肺多组学（RNA+ATAC）数据扩展为增强子-基因调控网络（eGRN），用于将GWAS疾病风险变异映射到特定细胞类型和TF调控模块。

---

## 03 研究问题

- **具体问题**：如何在单细胞分辨率下，系统性地绘制人类多种组织中转录因子（TF）驱动的基因调控程序（regulons），并利用这些程序解析细胞类型特异的调控逻辑、疾病相关细胞类型及风险基因模块？
- **为什么重要**：TF通过组合方式调控基因表达决定细胞命运，但TF的调控具有高度细胞类型特异性。传统bulk组织分析掩盖了这种异质性，而单细胞数据的大规模积累使得在单细胞水平绘制调控图谱成为可能。理解TF-靶基因关系是解析发育、稳态和疾病中基因调控机制的基础。
- **现有方法不足**：
  - ChIP-seq虽能直接鉴定TF结合位点，但难以扩展到大量TF和原代细胞类型；
  - 传统共表达网络缺乏因果性和TF结合证据；
  - 已有单细胞调控网络推断方法（如SCENIC）多局限于单一组织或少量细胞类型，缺乏跨组织的系统比较；
  - 缺乏将调控网络与GWAS风险变异系统关联的标准化流程。
- **精确研究问题（Can...?）**：Can we construct a comprehensive, cell-type-resolved atlas of TF-driven gene regulatory programs across human tissues from existing single-cell data, and can this atlas link disease-associated genetic variants to specific cell types and TF modules?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架及作者引用，部分经外部核验标注。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|----------|
| 早期TF靶基因鉴定 | ChIP-seq、ChIP-chip | 直接、可靠 | 通量低、细胞类型覆盖有限、难以扩展到大量TF | 本文不依赖ChIP-seq，而是基于计算推断 |
| 基序扫描 | FIMO、PWM匹配 | 可扩展 | 假阳性高、缺乏细胞类型上下文 | 本文在共表达基础上叠加motif富集 |
| 共表达网络 | WGCNA | 可扩展、无需TF结合数据 | 缺乏方向性、因果关系不明 | 本文采用SCENIC的共表达+motif双重过滤 |
| 调控网络推断 | SCENIC/pySCENIC | 结合共表达与motif，推断regulons | 早期版本缺乏跨组织系统应用 | 本文核心方法，扩展至15个器官系统 |
| 增强子-基因网络 | SCENIC+ | 整合ATAC-seq，纳入增强子调控 | 需要配对多组学数据 | 本文用新生成的人肺多组学数据扩展 |
| 疾病变异映射 | sc-linker、snp2cell | 将GWAS变异与细胞类型关联 | 依赖网络质量 | 本文采用snp2cell在eGRN上传播风险信号 |

**本文主张的位置**：在SCENIC/pySCENIC框架基础上，首次构建覆盖整个人体的、细胞类型分辨率的TF调控程序图谱，并展示其在疾病变异映射中的价值。作者主张大规模数据整合可提高regulon推断的稳健性和细胞类型特异性（Results 图4e-g）。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单细胞数据稀疏性 | 单细胞转录组存在大量dropout，直接计算共表达噪声大 | 每个细胞检测到的基因数有限，技术噪声高 | Methods "Computation of regulons"：使用mini-metacells（10-15细胞）缓解稀疏性 |
| 跨组织数据整合困难 | 不同数据集批次效应强、注释体系不统一 | 各研究使用不同平台、不同注释标准 | Methods：优先选择已整合的、注释协调的大规模图谱，手动映射到Cell Ontology ID |
| 共表达≠因果关系 | 共表达可能反映间接调控或下游效应 | mRNA共表达无法区分直接/间接调控 | 方法上叠加motif富集过滤，但作者承认仍是预测（Discussion） |
| 计算资源需求大 | 全基因组范围TF-靶基因推断计算量大 | 需对每个谱系分别运行GRNBoost2 | Methods：按谱系/细胞区室拆分计算 |
| 调控网络推断的可重复性低 | 不同方法/运行间网络重叠度低 | 基因互作空间巨大，数据覆盖有限 | Results 图4b-g：比较eReg与crReg，显示数据量增大可提高稳健性 |
| 疾病变异到细胞类型的映射不确定 | GWAS变异多在非编码区，难以确定作用细胞类型 | 连锁不平衡、增强子-基因对应关系不明确 | 采用snp2cell网络传播方法，但结果仍是预测（Discussion） |

---

## 06 核心思想

### 1) 表面方法

- 收集14个器官系统的公开单细胞RNA-seq数据集（约500万细胞），按谱系/细胞区室拆分；
- 使用pySCENIC流程：GRNBoost2推断TF-靶基因共表达模块 → cisTarget进行motif富集验证 → 得到细胞类型特异的regulons；
- 对每个regulon按细胞类型和组织进行差异表达过滤，保留活跃调控程序；
- 新生成人肺10x多组学（RNA+ATAC）数据，用SCENIC+扩展为eGRN；
- 使用snp2cell将GWAS风险变异映射到eGRN，识别疾病相关细胞类型和TF模块。

### 2) 核心洞察

- **数据规模即优势**：跨组织、跨数据集的数万至数百万细胞整合，可覆盖远多于单一研究的细胞类型和状态，使regulon推断更全面、更稳健（图4b-g显示crReg优于仅基于单数据集的eReg）。
- **细胞类型特异性是调控的核心维度**：TF的靶基因集合随细胞类型变化，regulon的"活性"（是否在特定细胞类型中差异表达）比TF表达本身更能反映调控功能。
- **调控网络可作为GWAS变异的"解释层"**：将风险变异映射到eGRN后，可通过网络传播识别富集的细胞类型和TF模块，将静态的遗传关联转化为动态的调控假设。

### 3) 可能的普适教训 [Analysis]

- 大规模公共数据整合的价值不仅在于"更多数据"，更在于覆盖更广的生物学状态空间——这对任何需要细胞类型分辨率的研究（包括TF-DNA结合机制研究）都适用。
- 计算推断的调控关系应视为"可检验假设"而非"结论"，需要与实验验证（如ChIP-seq、CRISPR扰动）结合。
- 将调控网络与遗传变异关联是连接"机制"与"疾病"的高效桥梁，这一思路可迁移到其他复杂性状研究。

---

## 07 方法总览

- **输入**：
  - 公开单细胞RNA-seq数据（14个器官系统，约500万细胞）
  - 新生成的人肺10x多组学数据（RNA+ATAC，5个供体、5个肺部位，>37,000细胞）
  - TF基序数据库（cisTarget内置）
  - 公开GWAS summary statistics（儿童期哮喘、IPF、COPD）
- **输出**：
  - CellRegulon数据库：约70万个regulons，覆盖约1300个TF、500余种细胞类型
  - 人肺eGRN：TF→增强子→基因调控网络
  - 疾病风险评分：每个细胞类型和TF的疾病关联评分
- **模块**：
  1. 数据收集与预处理（QC、doublet去除、批次整合）
  2. 谱系/细胞区室划分
  3. pySCENIC regulon推断（GRNBoost2 + cisTarget）
  4. 差异表达过滤（保留活跃regulons）
  5. SCENIC+ eGRN构建（人肺多组学）
  6. snp2cell GWAS风险传播
- **训练**：GRNBoost2（梯度提升机）在每谱系内训练，预测每个基因的表达由哪些TF调控
- **工具**：pySCENIC、SCENIC+、Scanpy、ArchR、Harmony、snp2cell、cisTopic、cisTarget
- **反馈回路**：无显式闭环反馈；regulon推断为单次前向流程
- **假设**：
  - 共表达+motif富集可近似TF-靶基因调控关系
  - 细胞类型注释准确且可跨数据集映射
  - GWAS风险变异可通过增强子-基因连接映射到调控网络

**文字流程**：
收集公开scRNA-seq数据 → 按谱系拆分 → 每谱系内用GRNBoost2基于共表达推断TF→靶基因调控模块 → 用cisTarget检查靶基因启动子中TF基序富集 → 形成候选regulons → 对每个regulon在细胞类型水平做差异表达分析，保留活跃regulons → 构建CellRegulon数据库 → 新生成人肺多组学数据 → 用SCENIC+推断eGRN → 将GWAS变异映射到eGRN → 用snp2cell传播风险信号 → 识别疾病相关细胞类型和TF模块。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 数据整合与谱系划分 | 将14个器官系统的scRNA-seq数据按谱系/细胞区室分组 | 不同谱系调控逻辑差异大，需分别建模；整合扩大覆盖 | 输入：多个scRNA-seq数据集；输出：谱系特异的表达矩阵 | Methods "Computation of regulons" | 预期影响：移除后无法跨组织比较，regulon覆盖度大幅下降 [预期效应] |
| mini-metacell聚合 | 将10-15个细胞聚合成metacell | 缓解单细胞稀疏性，提高共表达计算信噪比 | 输入：单细胞表达矩阵；输出：metacell表达矩阵 | Methods "Computation of regulons" | 预期影响：共表达推断噪声增大，regulon质量下降 [预期效应] |
| GRNBoost2共表达推断 | 基于梯度提升机推断TF→靶基因调控关系 | 核心调控关系推断引擎 | 输入：metacell表达矩阵；输出：TF-靶基因权重矩阵 | Methods "Computation of regulons" | 实测影响：未单独消融；但图4b-g显示数据量增大（crReg vs eReg）显著提高TF预测精度 [实测效应] |
| cisTarget motif富集 | 验证靶基因启动子中TF结合基序是否富集 | 过滤纯共表达噪声，增加调控关系的因果证据 | 输入：TF-靶基因对+基因组序列；输出：通过motif验证的regulons | Methods "Computation of regulons" | 预期影响：移除后假阳性大幅增加，regulon特异性下降 [预期效应] |
| 差异表达过滤 | 保留在特定细胞类型中活跃的regulons | 区分"存在"的调控程序与"活跃"的调控程序 | 输入：全regulons+细胞类型注释；输出：活跃regulons | Methods "Computation of regulons" | 预期影响：移除后无法区分细胞类型特异的调控活性 [预期效应] |
| SCENIC+ eGRN构建 | 整合ATAC-seq数据，将增强子纳入调控网络 | 增强子变异是疾病风险的主要载体，需纳入网络 | 输入：人肺多组学RNA+ATAC；输出：TF→增强子→基因eGRN | Results 图4a；Methods "eRegulon analysis" | 预期影响：移除后无法将非编码变异映射到调控网络 [预期效应] |
| snp2cell风险传播 | 将GWAS变异信号在网络中传播，识别疾病相关细胞类型和TF | 将静态遗传关联转化为细胞类型特异的调控假设 | 输入：GWAS summary statistics + eGRN；输出：细胞类型/TF/基因的风险评分 | Results 图5a-e；Methods "GWAS association analysis" | 预期影响：移除后无法从调控网络中获得疾病机制假设 [预期效应] |

---

## 09 关键公式符号

本文为资源型论文，核心方法（GRNBoost2、cisTarget、snp2cell）均为已有工具，原文未给出具体数学公式。以下为方法中隐含的关键概念：

1. **Regulon活性评分（AUCell）**：
   - 对每个细胞，计算其基因表达排名中regulon靶基因集的富集分数（AUC值）
   - 符号：AUC（Area Under the Curve）
   - 用途：量化单个细胞中特定regulon的活性
   - 来源：SCENIC框架标准方法（Methods "eRegulon analysis"提及AUCell）

2. **Regulon特异性评分（RSS, Regulon Specificity Score）**：
   - 用于衡量regulon在特定细胞类型中的特异性
   - 基于Jensen-Shannon散度计算
   - 用途：识别细胞类型特异的TF调控程序
   - 来源：Results 图4e提及RSS

3. **Jaccard系数**：
   - J(A,B) = |A∩B| / |A∪B|
   - 用途：衡量两个regulon靶基因集合的重叠程度，用于regulon聚类和嵌入
   - 来源：Methods "Regulon analysis"

4. **GWAS风险传播（snp2cell）**：
   - 基于贝叶斯框架将SNP-level关联信号聚合到基因、增强子、TF层面
   - 具体公式未在原文给出，引用自snp2cell原始文献
   - 来源：Methods "GWAS association analysis"

---

## 10 实验设计与证据链

### 数据集与资源

| 资源 | 规模/内容 | 用途 |
|------|-----------|------|
| 公开scRNA-seq数据集 | 14个器官系统，约500万细胞 | CellRegulon构建 |
| 新生成人肺多组学 | 5个供体、5个肺部位，>37,000细胞（RNA+ATAC） | eGRN构建 |
| 儿童期哮喘GWAS | 公开summary statistics | 疾病关联分析 |
| IPF GWAS | 公开summary statistics | 疾病关联分析 |
| COPD GWAS | 公开summary statistics | 疾病关联分析 |
| 文献挖掘TF列表 | 64个naive B细胞相关TF（半自动文本挖掘） | 验证B细胞regulon |

### 指标

- Regulon特异性评分（RSS）
- TF活性相关性（图4c）
- 精确率-召回率（图4g，B细胞TF验证）
- 疾病风险富集分数（snp2cell输出）

### 基线/对比

- eReg（仅基于人肺多组学数据推断的regulons） vs crReg（基于CellRegulon大规模数据推断的regulons）

### 实验列表

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| Regulon空间嵌入（图1a） | regulon整体结构反映细胞类型组织 | 约70万regulons的UMAP嵌入 | 呈球形分布，细胞类型聚类 | regulon空间具有结构性和细胞类型组织 | 未证明该结构反映因果关系 | Results 图1a |
| TF分布统计（图1b-d） | TF可分为特异性和普遍性两类 | 按出现细胞类型数量分类 | 多数TF特异，少数普遍；普遍TF靶基因更多 | TF调控具有广谱和特异两种模式 | 未证明功能重要性差异 | Results 图1b-d |
| B细胞分化轨迹（图2a-b） | regulon可重建B细胞分化顺序 | 无监督嵌入 vs 已知分化顺序 | 嵌入顺序与已知分化一致 | regulon捕获分化相关调控变化 | 未证明因果关系 | Results 图2a-b |
| B细胞TF验证（图4g） | CellRegulon可恢复已知B细胞TF | crReg vs eReg，64个文献TF | crReg精确率-召回率优于eReg | 大规模数据整合提高regulon推断精度 | 未在多种细胞类型中系统验证 | Results 图4g |
| 疾病GWAS映射（图5a-e） | eGRN可将疾病风险映射到细胞类型 | 儿童期哮喘、IPF、COPD | 识别出已知相关细胞类型（如哮喘-上皮/免疫） | eGRN可重现已知疾病-细胞类型关联 | 未证明新发现的因果性 | Results 图5a-e |
| 哮喘风险模块（图4l-m） | 识别哮喘相关TF模块 | 网络传播+富集分析 | 富集到FOSL1、BHLHE40等 | 提示角质化/损伤修复通路参与哮喘 | 未实验验证 | Results 图4l-m |

---

## 11 结论正确解读

- **任务范围**：本文构建的是**计算预测的**TF-靶基因调控程序图谱，而非实验验证的TF-DNA结合事件。regulon推断基于共表达+motif富集，反映的是"可能受该TF调控的基因集合"，不等同于直接物理结合。
- **oracle/真值输入**：无实验真值；B细胞TF验证使用文献挖掘的64个已知TF作为近似金标准，但该列表本身可能不完整且有偏。
- **端到端状态**：从原始数据到数据库的流程是端到端的，但从regulon到疾病机制的推断是假设生成性的，未经过实验验证。
- **算力成本**：原文未报告具体算力需求，但pySCENIC在数百万细胞规模上运行需要较大计算资源。
- **历史数据依赖**：完全依赖公开scRNA-seq数据，数据质量、批次效应和注释准确性直接影响结果。
- **模型依赖**：结果高度依赖pySCENIC/SCENIC+流程的参数选择和motif数据库完整性。
- **最难情况**：对罕见细胞类型或低表达TF的regulon推断可能不可靠；跨数据集的批次效应可能引入假关联。
- **群体/领域边界**：仅覆盖健康成人及胎儿组织，未包含疾病状态组织（除GWAS映射外）；主要适用于人类。
- **不确定性**：regulon预测的假阳性率未系统评估；GWAS映射结果受LD结构和增强子-基因连接质量影响。

**有边界的复述**：CellRegulon是一个基于约500万健康人类细胞转录组数据计算推断的TF-靶基因调控程序数据库，可有效恢复已知的细胞类型-疾病关联和B细胞分化调控逻辑，但其调控关系预测和疾病机制推断均需实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 预测性质 | 所有regulon均为计算预测，需实验验证 | 建议结合实验方法验证关键预测 | Discussion |
| 定量细节缺失 | 未捕获TF间协同性、相对贡献、动力学参数和靶基因降解速率 | 可提取子集进行更详细的数学建模 | Discussion |
| 数据覆盖偏差 | 主要基于健康组织，疾病状态覆盖有限 | 未来可整合更多疾病状态数据 | Discussion |
| 方法依赖 | 使用pySCENIC梯度提升机，可能受限于方法假设 | 期待更先进的机器学习方法（如神经网络）用于未来版本 | Discussion |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| B细胞TF验证仅使用文献挖掘列表 | 该列表可能偏向已知/研究充分的TF，存在确认偏倚 | 高估了CellRegulon在发现新TF方面的能力 | 使用独立实验数据（如CRISPR筛选、ChIP-seq）进行盲测 | Results 图4g |
| crReg优于eReg的比较可能受数据量混淆 | 两者差异不仅在于数据量，还在于数据来源和预处理流程 | 无法确定"数据量"是唯一优势因素 | 控制数据来源，仅改变数据量进行消融 | Results 图4b-g |
| GWAS映射依赖增强子-基因连接质量 | 共开放染色质推断的连接可能存在大量假阳性 | 影响疾病相关细胞类型和TF识别的可靠性 | 与Hi-C、eQTL等独立数据交叉验证 | Methods "GWAS association analysis" |
| 角质化/损伤修复通路与哮喘的关联 | 可能是继发效应而非因果驱动 | 影响对疾病机制的理解 | 在动物模型或类器官中进行功能实验 | Results 图4l-m |
| 未报告regulon推断的假阳性率 | 缺乏对预测精度的全局评估 | 用户无法判断数据库的整体可靠性 | 使用ChIP-seq、CUT&RUN等实验数据系统评估 | 全文未提供 |
| 细胞类型注释依赖原始数据 | 不同数据集的注释标准不一致，可能引入错误 | 影响所有下游分析的准确性 | 使用独立标记基因进行注释一致性检验 | Methods "Cell type annotation" |

---

## 14 学到什么

> 以下为面向「蛋白质-DNA互作（TF–DNA结合机制）× AI/物理模拟」课题的可迁移知识。

### 概念层面

1. **Regulon作为调控单元**：将TF-靶基因关系组织为"regulon"（一个TF及其受调控的靶基因集合），比单基因或单TF分析更系统。本课题研究TF-DNA结合时，可将regulon作为先验约束，缩小候选靶基因范围。
2. **细胞类型特异性是核心维度**：同一TF在不同细胞类型中靶基因集合不同。TF-DNA结合机制研究应明确细胞类型背景，避免将一种细胞中的结合模式泛化。
3. **共表达+motif双重过滤**：仅靠共表达噪声大，仅靠motif假阳性高，两者结合是计算推断TF-靶基因关系的有效策略。可迁移到AI模型的特征工程。

### 方法层面

4. **大规模数据整合策略**：跨数据集整合时，按谱系/细胞区室拆分建模而非全局建模，可兼顾数据量和生物学差异。本课题若需训练TF结合预测模型，可参考此策略构建训练集。
5. **Mini-metacell聚合**：将10-15个细胞聚合为metacell可缓解稀疏性，提高共表达计算信噪比。对单细胞ATAC-seq的TF footprint分析同样适用。
6. **GWAS→调控网络→细胞类型的映射流程**：snp2cell的网络传播方法将遗传变异与调控网络结合，识别疾病相关细胞类型和TF模块。本课题研究TF-DNA结合变异（如TFBS突变）时，此流程可直接复用。
7. **RSS（Regulon特异性评分）**：量化regulon在细胞类型中的特异性，可用于筛选细胞类型特异的TF调控程序，也可作为AI模型的特征。

### 工具层面

8. **pySCENIC/SCENIC+流程**：成熟的regulon推断工具链，支持RNA和ATAC多组学整合。本课题可将其作为TF-靶基因关系预测的基线方法。
9. **CellRegulonDB资源**：可直接查询特定TF在特定细胞类型中的靶基因集合，作为TF-DNA结合研究的先验知识库。
10. **snp2cell**：将GWAS变异映射到调控网络的工具，适用于TFBS变异的功能注释。

### 对TF-DNA结合机制研究的迁移建议

- 将CellRegulon的regulon作为TF-DNA结合预测模型的**监督信号**：如果一个基因是某TF的regulon靶基因，则其启动子/增强子区域更可能包含该TF的结合位点。
- 利用CellRegulon的细胞类型特异性信息，构建**细胞类型条件化的TF结合预测模型**。
- 将GWAS风险变异映射到TF结合位点，结合CellRegulon的regulon信息，可优先筛选疾病相关的TF-DNA结合变异。

---

## 15 与已有知识连接

- **SCENIC框架**（Aibar et al., 2017, Nature Methods）：本文使用的pySCENIC是该方法的Python实现。SCENIC首次提出"共表达+motif富集"的regulon推断范式，本文将其扩展至跨组织大规模应用。
- **SCENIC+**（González-Blas et al., 2023, Nature Methods）：在SCENIC基础上整合增强子信息，本文使用该方法构建人肺eGRN。
- **Human Cell Atlas**（Regev et al., 2017, eLife）：本文数据主要来源于HCA项目，HCA的标准化注释体系使跨数据集整合成为可能。
- **snp2cell**（Ashuach et al., 2023, Nature Genetics）：本文使用的GWAS风险映射工具，将遗传变异通过调控网络传播到细胞类型。
- **TF-DNA结合机制研究**：本文的regulon推断基于motif富集，与TFBS预测（如JASPAR、CIS-BP数据库）直接相关。本课题若研究TF-DNA结合的三维结构或动力学，可将regulon作为功能验证的候选集合。
- **深度学习在基因调控中的应用**：本文Discussion提到未来可用神经网络改进regulon推断，这与本课题的AI方法方向一致。Enformer、Basenji等模型可预测序列变异对基因表达的影响，与本文的GWAS映射互补。
- **3D基因组与增强子-启动子互作**：本文的eGRN基于共开放染色质推断增强子-基因连接，与Hi-C、Micro-C等3D基因组数据互补。本课题研究TF-DNA结合时，可结合3D基因组数据理解TF结合位点的空间上下文。

---

## 16 研究想法

> 以下为面向「蛋白质-DNA互作（TF–DNA结合机制）× AI/物理模拟」课题的研究候选。

### 候选1：基于CellRegulon先验的TF-DNA结合预测模型

- **名称**：Regulon-Guided TFBS Prediction
- **来源局限/观察**：现有TFBS预测模型（如基于CNN的DeepSEA、Basenji）缺乏细胞类型特异性，且训练数据多来自ChIP-seq，覆盖TF有限。CellRegulon提供了约1300个TF在500+细胞类型中的靶基因集合，可作为弱监督信号。
- **核心假设**：如果一个基因是某TF的regulon靶基因，其调控区域（启动子+增强子）更可能包含该TF的功能性结合位点。
- **初步方法**：以CellRegulon的regulon靶基因集合为正样本，以非靶基因的调控区域为负样本，训练细胞类型条件化的TFBS预测模型。输入为DNA序列+细胞类型embedding，输出为TF结合概率。可结合ATAC-seq峰信息限定候选增强子区域。
- **验证方式**：使用独立ChIP-seq数据（如ENCODE、Cistrome）评估预测精度；比较加入CellRegulon先验前后的AUC提升。
- **创新状态**：unverified

### 候选2：TF-DNA结合变异的细胞类型特异性功能注释

- **名称**：Cell-Type-Aware TFBS Variant Prioritization
- **来源局限/观察**：GWAS变异多在非编码区，现有注释工具（如RegulomeDB、FunSeq2）缺乏细胞类型分辨率。本文展示了CellRegulon+GWAS映射的可行性，但未系统评估TFBS变异。
- **核心假设**：同一TFBS变异在不同细胞类型中的功能影响不同，取决于该细胞类型中TF的regulon活性。
- **初步方法**：对每个GWAS风险位点，提取其所在增强子的TF结合位点，结合CellRegulon的regulon活性评分，计算"变异影响分数"= TF结合破坏概率 × 该细胞类型中TF的regulon活性。在哮喘、COPD、IPF等疾病中验证。
- **验证方式**：与eQTL数据交叉验证；在相关细胞类型中进行CRISPR扰动实验。
- **创新状态**：unverified

### 候选3：TF-DNA结合动力学的多组学整合建模

- **名称**：Multi-Omics TF-DNA Binding Dynamics Model
- **来源局限/观察**：本文的eGRN是静态网络，未考虑TF-DNA结合的动力学（如结合强度、解离速率）。本课题若结合分子动力学（MD）模拟，可预测TF-DNA结合的结构基础。
- **核心假设**：CellRegulon中TF-靶基因关系的强度（共表达相关系数、motif保守性）与TF-DNA结合的物理化学性质（结合自由能、氢键数）相关。
- **初步方法**：选取CellRegulon中高置信度TF-靶基因对，提取TF的DNA结合域结构（来自AlphaFold或PDB），对TF-DNA复合物进行MD模拟，计算结合自由能。将模拟结果与regulon强度关联，训练一个"序列→结构→调控强度"的端到端模型。
- **验证方式**：与实验测定的TF-DNA结合亲和力数据（如HT-SELEX、PBMs）比较。
- **创新状态**：unverified

### 候选4：细胞类型转换中的TF调控程序动态模拟

- **名称**：TF Regulatory Program Dynamics in Cell Fate Transitions
- **来源局限/观察**：本文展示了B细胞分化中regulon的动态变化（图2），但未建模调控程序切换的机制。本课题可结合物理模拟（如Waddington景观）理解TF如何驱动细胞状态转换。
- **核心假设**：细胞命运转换由少数关键TF的regulon活性切换驱动，这些TF的DNA结合亲和力变化是转换的物理基础。
- **初步方法**：利用CellRegulon的B细胞分化轨迹数据，识别关键转换TF。对这些TF的DNA结合域进行MD模拟，比较不同分化阶段靶基因启动子的结合亲和力差异。构建"TF结合亲和力→regulon活性→细胞状态"的动力学模型。
- **验证方式**：在体外分化系统中进行TF扰动实验，验证预测的关键转换TF。
- **创新状态**：unverified

### 候选5：基于图神经网络的跨细胞类型调控程序迁移学习

- **名称**：Graph Neural Network for Cross-Cell-Type Regulatory Program Transfer
- **来源局限/观察**：CellRegulon覆盖500+细胞类型，但不同细胞类型的数据量极不均衡。图神经网络可建模TF-TF、TF-基因、基因-基因的多层关系，实现知识迁移。
- **核心假设**：细胞类型间的调控程序具有可迁移的共享结构，图神经网络可捕捉这种结构。
- **初步方法**：构建异构图（节点=TF、基因、增强子；边=regulon关系、共表达、motif匹配），以CellRegulon为训练数据，使用图神经网络学习细胞类型特异的TF调控程序表示。对低数据量细胞类型进行零样本预测。
- **验证方式**：在留出细胞类型上评估regulon预测精度；与pySCENIC基线比较。
- **创新状态**：unverified