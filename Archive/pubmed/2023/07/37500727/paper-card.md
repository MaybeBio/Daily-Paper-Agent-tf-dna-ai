## 01 基本信息

- **标题**：Integrated single-cell chromatin and transcriptomic analyses of human scalp identify gene-regulatory programs and critical cell types for hair and skin diseases
- **作者与单位**：Ober-Reynolds, Benjamin; Wang, Chen; Ko, Justin M; Rios, Eon J; Aasi, Sumaira Z; Davis, Mark M; Oro, Anthony E; Greenleaf, William J（斯坦福大学等，具体单位未在摘要中逐一列出）
- **期刊/预印本平台**：Nature Genetics
- **年份**：2023
- **论文类型**：研究论文（Research Article）
- **领域**：单细胞基因组学、基因调控、皮肤/毛发疾病遗传学
- **关键词**：scRNA-seq、scATAC-seq、enhancer-gene links、GWAS、androgenetic alopecia、eczema、转录因子、染色质可及性
- **DOI/arXiv 号**：10.1038/s41588-023-01445-4
- **代码**：https://github.com/GreenleafLab/scScalpChromatin
- **数据**：GEO accession GSE212450；交互式数据浏览器：http://shiny.scscalpchromatin.su.domains/shiny_scalp/
- **阅读日期**：未提供
- **在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**：本文不直接研究TF-DNA结合的物理/结构机制，而是利用单细胞多组学数据（scRNA+scATAC）推断**顺式调控元件（enhancer）与靶基因的关联**，并通过**gkm-SVM机器学习模型**预测SNP对染色质可及性（即TF结合位点功能）的影响。其核心贡献在于：(1) 提供了一套从单细胞ATAC数据推断**enhancer-gene regulatory network**的完整流程；(2) 展示了如何将**序列级机器学习模型（gkm-SVM）** 应用于疾病相关非编码变体的功能优先级排序。对TF-DNA互作课题的可迁移点在于：**peak-to-gene linkage推断方法**、**TF motif活性（chromVAR）与靶基因关联的分析框架**、以及**gkm-SVM在预测TF结合破坏方面的应用**。

---

## 02 一句话总结

本文通过匹配的人头皮 scRNA-seq 和 scATAC-seq 数据，在多分辨率聚类水平上推断 enhancer-gene 关联（比先前方法多识别 50–100% 的关联），发现高调控基因（HRGs）的表达由多个可加性 enhancer 模块驱动，并利用 LD 回归和 gkm-SVM 机器学习模型将 AGA、湿疹等疾病的 GWAS 信号优先定位于特定细胞类型（如真皮乳头细胞）和候选功能 SNP。

---

## 03 研究问题

- **具体问题**：人类头皮中哪些细胞类型和基因调控程序（enhancer-gene 网络）驱动毛发和皮肤疾病的遗传风险？具体而言，非编码 GWAS 变异如何通过影响细胞类型特异的染色质可及性和 TF 结合来致病？
- **为什么重要**：绝大多数皮肤/毛发疾病 GWAS 变异位于非编码区，其功能解读需要细胞类型特异的调控元件图谱。此前缺乏匹配的单细胞转录组+染色质可及性数据，且缺乏跨细胞分辨率的 enhancer-gene 关联推断。
- **现有方法不足**：
  - 先前单细胞皮肤研究多聚焦单一谱系或未保留完整毛囊结构；
  - 标准 peak-to-gene 关联仅在单一分辨率（全数据集）上进行，遗漏亚型特异的调控关系；
  - 仅用 nearest-gene 或静态 peak 重叠来注释 GWAS 变异，缺乏对 TF 结合破坏的定量预测。
- **精确研究问题（Can...?）**：Can integrated single-cell chromatin and transcriptomic profiling of human scalp, combined with machine learning models of sequence-to-accessibility, identify cell types, enhancer-gene links, and candidate causal SNPs underlying hair and skin disease GWAS loci?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架及摘要中引用的代表性工作，部分为「仅本文框架」的叙述。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|----------|
| 批量组织/细胞系调控图谱 | ENCODE、Roadmap、Fantom5 | 覆盖广、深度高 | 缺乏细胞类型分辨率，无法解析复杂组织（如毛囊） | 本文用单细胞分辨率替代批量 |
| 单细胞转录组皮肤图谱 | 多项 scRNA-seq 皮肤研究（如 Cheng et al., 2018; Solé-Boldo et al., 2020） | 鉴定细胞类型和状态 | 缺乏染色质可及性信息，无法连接非编码变异 | 本文同时提供 scRNA+scATAC |
| 单细胞 ATAC 皮肤图谱 | 少数 scATAC 皮肤研究 | 提供调控元件信息 | 缺乏匹配转录组，难以推断 enhancer-gene 功能关联 | 本文匹配同一批样本的 scRNA+scATAC |
| 多组学整合与 peak-to-gene 关联 | ArchR、Seurat CCA 整合、 Cicero | 可推断 enhancer-gene 关联 | 通常在单一分辨率进行，遗漏亚型特异调控 | 本文在多个分辨率（全数据集+亚聚类）上重复推断，增加 50–100% 关联 |
| 非编码变异功能预测 | CADD、GWAS LD 回归、ABC model | 可优先排序变异 | 缺乏细胞类型特异性或缺乏序列级预测 | 本文用 LDSC + 细胞类型特异 peak + gkm-SVM 序列模型 |
| 序列级机器学习预测调控 | gkm-SVM、DeepSEA、Enformer | 可预测变异对 TF 结合/染色质的影响 | 需要大量训练数据，且解释性有限 | 本文用 gkm-SVM + GkmExplain 预测 SNP 对细胞类型特异可及性的影响 |

**本文主张的位置**：在单细胞多组学整合、多分辨率 enhancer-gene 推断、以及序列级机器学习变异优先级排序三个层面同时推进，并以疾病 GWAS 为验证场景。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单细胞皮肤研究缺乏匹配的多组学数据 | 已有 scRNA 或 scATAC 研究多为单一模态 | 技术成本和样本处理难度高 | 本文首次提供匹配的 scRNA+scATAC 人头皮图谱（Results 图 1A,B） |
| 标准 peak-to-gene 关联在单一分辨率进行 | 亚型特异的 enhancer-gene 关联被遗漏 | 全数据集聚类掩盖了亚型特异的调控程序 | 多分辨率推断新增 79,386 个关联（Results 图 2A, Extended Data 图 5A） |
| 高调控基因（HRGs）的调控机制不明 | 部分基因关联大量 enhancer，但表达调控机制不清 | 缺乏跨细胞类型的 enhancer 模块分析 | HRGs 的 enhancer 呈模块化使用，总可及性与表达相关（Results 图 2E–I, Extended Data 图 5F） |
| GWAS 变异功能解读缺乏细胞类型分辨率 | 非编码变异难以映射到具体细胞类型 | 缺乏细胞类型特异的调控元件图谱 | LDSC 显示 AGA 信号富集于真皮乳头细胞 peak（Results 图 5A） |
| 非编码 SNP 的效应预测缺乏序列级模型 | 仅用 peak 重叠无法判断 SNP 是否破坏 TF 结合 | 需要细胞类型特异的序列-可及性模型 | gkm-SVM 模型预测 SNP 对可及性的影响，识别 47/19/19 个高置信 SNP（Results 图 6, Table S29） |
| 真皮乳头细胞数量稀少难以分析 | 标准聚类难以分离 DP 细胞 | DP 细胞在头皮中占比极低 | 通过亚聚类和 marker 基因（HHIP, WNT5A, PTCH1）鉴定 DP（Results 图 3, Extended Data 图 3） |

---

## 06 核心思想

### 1) 表面方法

- 生成匹配的人头皮 scRNA-seq（54,288 细胞）和 scATAC-seq（45,896 细胞）数据；
- 在多个分辨率（全数据集 + 5 大谱系亚聚类）上分别进行 peak-to-gene 关联推断，合并为 consensus 关联集；
- 定义高调控基因（HRGs），分析其 enhancer 模块化使用与表达的关系；
- 用 LDSC 将皮肤/毛发疾病 GWAS 信号映射到细胞类型特异 peak；
- 用 gkm-SVM 训练细胞类型特异的序列-可及性模型，预测 SNP 对可及性的影响，结合 peak-to-gene 关联和 eQTL 证据优先排序候选 SNP。

### 2) 核心洞察

- **多分辨率推断增强调控网络分辨率**：在亚聚类水平上重复 peak-to-gene 推断，能捕获全数据集分析遗漏的亚型特异调控关系，且新增关联与全数据集关联同样可靠（保守性、ABC 模型验证）。
- **增强子模块化加性模型**：HRGs 的多个 enhancer 在不同细胞类型中以不同组合被使用，总可及性（而非单一 enhancer）与表达水平相关，支持增强子加性模型。
- **细胞类型特异调控元件是连接 GWAS 与疾病机制的关键**：AGA 信号在 DP 细胞中富集，而湿疹信号在 T 细胞中富集，提示不同疾病的驱动细胞类型不同。
- **序列级模型可预测 SNP 的功能效应**：gkm-SVM 不仅能预测可及性，还能通过 GkmExplain 归因分数定位 SNP 破坏的具体 TF 结合基序。

### 3) 可能的普适教训 [Analysis]

- 单细胞调控图谱的价值不仅在于细胞类型注释，更在于**跨分辨率的调控关系推断**——同一数据在不同聚类粒度下能回答不同层次的问题。
- 增强子对基因表达的贡献可能是**可加性**的，这为从 ATAC 数据定量预测表达提供了简化假设。
- 将**无监督聚类 → 调控推断 → 遗传学注释 → 序列模型**串联，是从多组学数据到可检验因果假设的通用范式。

---

## 07 方法总览

- **输入**：
  - 人头皮组织（健康对照、斑秃患者）的匹配 scRNA-seq 和 scATAC-seq 数据；
  - 外部 GWAS 汇总统计（AGA、湿疹、发色等）；
  - 外部 ABC model 预测（131 组织/细胞类型）用于验证；
  - 外部 TF 扰动/敲低数据（如 TP63、KLF4）用于验证调控靶点。

- **输出**：
  - 头皮细胞类型图谱（42 个 scRNA 聚类、38 个 scATAC 聚类）；
  - Consensus peak-to-gene 关联集（146,088 个）；
  - HRG 列表（1,739 个）及其 enhancer 模块；
  - 细胞类型特异的疾病 GWAS 富集结果；
  - 优先排序的候选功能 SNP 列表（AGA 47 个、湿疹 19 个、发色 19 个）。

- **主要模块**：
  1. 数据生成与质控（10x Genomics 平台）；
  2. 迭代 LSI 降维与聚类（scRNA 和 scATAC 分别进行）；
  3. CCA 整合 scRNA 与 scATAC；
  4. Peak-to-gene 关联推断（多分辨率）；
  5. HRG 鉴定与 enhancer 模块分析；
  6. chromVAR TF motif 活性分析；
  7. LDSC 细胞类型富集分析；
  8. gkm-SVM 训练与 GkmExplain SNP 效应预测；
  9. 多证据整合的 SNP 优先级排序。

- **训练**：
  - gkm-SVM：每个细胞类型聚类一个模型，正样本为该聚类特异的可及 peak 序列，负样本为 GC 匹配的不可及序列；10 折交叉验证评估。
  - 无监督聚类：迭代 LSI + Seurat/ArchR 标准流程。

- **反馈回路**：
  - 预测的 TF 调控靶点用外部 TF 扰动数据（TP63、KLF4）验证；
  - 预测的 SNP 效应与已知 eQTL 交叉验证。

- **假设**：
  - Peak-to-gene 关联反映增强子-启动子功能关系；
  - 序列可及性主要由 TF 结合驱动（gkm-SVM 的隐含假设）；
  - 增强子对表达的贡献近似可加。

- **文字流程**：
  - 组织解离 → 单细胞文库制备 → 测序 → 比对 → QC → 聚类 → 注释 → 整合 → peak 鉴定 → 多分辨率 peak-to-gene 关联 → HRG 分析 → chromVAR → LDSC → gkm-SVM 训练 → SNP 效应预测 → 多证据整合 → 候选 SNP 列表。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 多分辨率 peak-to-gene 关联 | 在全数据集和亚聚类水平分别推断 enhancer-gene 关联 | 亚型特异的调控关系在全数据集分析中被稀释 | 输入：scRNA/scATAC 整合数据；输出：146,088 consensus 关联 | 新增关联与全数据集关联同样保守（Extended Data 图 5C），且更可能被 ABC 模型验证（Extended Data 图 5D） | 预期减少 50–100% 的关联数量，丢失亚型特异调控信息（作者明确主张） |
| HRG 鉴定与 enhancer 模块分析 | 识别关联 enhancer 数量异常多的基因，分析其模块化使用 | 揭示核心谱系基因的多增强子调控策略 | 输入：consensus 关联集；输出：1,739 个 HRG 及模块 | HRGs 富集已知 super-enhancer 基因（图 2D）；模块化使用与细胞类型特异表达相关（图 2F–I） | 无法识别多增强子调控的谱系关键基因 |
| chromVAR TF motif 活性 | 量化每个细胞中 TF motif 的可及性偏差 | 连接染色质可及性与 TF 活性 | 输入：peak 矩阵 + motif 注释；输出：motif 偏差 z-score | 识别了角蛋白细胞分化中的已知 TF（图 3C, Extended Data 图 6E） | 无法推断 TF 调控靶点 |
| LDSC 细胞类型富集 | 将 GWAS 信号映射到细胞类型特异 peak | 确定疾病驱动细胞类型 | 输入：GWAS 汇总统计 + 细胞类型 peak；输出：富集分数 | AGA 信号富集于 DP 细胞（图 5A） | 无法确定疾病相关细胞类型 |
| gkm-SVM 序列模型 | 预测序列可及性，评估 SNP 效应 | 从序列层面预测非编码变异功能 | 输入：peak 序列 + 标签；输出：可及性预测 + GkmExplain 归因 | 高预测性能（Extended Data 图 10A–D）；预测的 SNP 与 eQTL 一致（图 6E） | 无法从序列预测 SNP 功能效应 |
| GkmExplain SNP 效应评分 | 计算 SNP 对可及性的影响 | 优先排序候选因果 SNP | 输入：参考/替代等位基因序列；输出：delta score + prominence score | 识别出 47/19/19 个高置信 SNP（Table S29） | 无法从候选 SNP 中筛选功能变异 |

---

## 09 关键公式符号

本文核心定量方法中，明确给出的公式有限。以下为文中明确描述或可直接推导的关键公式：

**1. Linkage Score（调控靶点评分）**

文中明确给出：

$$LS_g = \sum_{k=1}^{n} R_k^2 \cdot MS_k$$

- $LS_g$：基因 $g$ 的 linkage score
- $n$：与基因 $g$ 关联的 peak 数量
- $R_k$：第 $k$ 个 peak 与基因 $g$ 的 Pearson 相关系数（peak-to-gene 关联强度）
- $MS_k$：第 $k$ 个 peak 中 TF motif 的匹配得分

**用途**：综合 peak-to-gene 关联强度和 motif 匹配置信度，识别特定 TF 的潜在调控靶基因。

**2. chromVAR 偏差 z-score（隐含）**

文中使用 chromVAR 计算 motif 偏差，其核心公式（来自原始 chromVAR 论文，非本文推导）：

$$z_{ij} = \frac{x_{ij} - \mu_{ij}}{\sigma_{ij}}$$

- $x_{ij}$：细胞 $j$ 中 motif $i$ 的期望可及性
- $\mu_{ij}, \sigma_{ij}$：基于 GC 含量匹配背景的期望和标准差

**用途**：量化每个细胞中 TF motif 的可及性富集程度。

**3. gkm-SVM 核函数（隐含）**

文中使用 LS-GKM 包的 wgkmrbf 核（t=5, l=11, k=7, d=3, M=50, H=50），具体核函数形式见原始 gkm-SVM 文献，本文未展开。

**4. GkmExplain delta score（隐含）**

$$\Delta = \sum_{i \in \text{central 50bp}} (Importance_i^{alt} - Importance_i^{ref})$$

- 对每个 SNP，计算参考/替代等位基因序列的 GkmExplain 归因分数之差，取中心 50bp 之和。

**用途**：量化 SNP 对预测可及性的影响方向和大小。

---

## 10 实验设计与证据链

### 数据集与资源

| 资源 | 规模/描述 |
|------|-----------|
| 人头皮样本 | 健康对照（C_PB, n=3; C_SD, n=7）、斑秃患者（AA, n=5） |
| scRNA-seq | 54,288 细胞，42 个聚类 |
| scATAC-seq | 45,896 细胞，38 个聚类 |
| Peak 总数 | 589,294 union peaks |
| Peak-to-gene 关联 | 146,088 consensus 关联 |
| GWAS 数据 | AGA、湿疹、发色等（来源：UK Biobank、GWAS catalog） |
| 验证数据 | ABC model（131 组织/细胞类型）、TP63 突变 RNA-seq、KLF4 敲低 RNA-seq |

### 实验与证据链表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 多分辨率 peak-to-gene 关联 | 亚聚类分析能发现更多可靠的 enhancer-gene 关联 | 全数据集 vs 亚聚类数据集 | 新增 79,386 个关联（50–100% 增加） | 多分辨率方法显著增加调控网络覆盖 | 新增关联的生物学功能需实验验证 | Results 图 2A, Extended Data 图 5A |
| 关联保守性验证 | 新增关联与已知调控关系一致 | 关联 peak vs 非关联 peak 的保守性 | 新增关联保守性显著高于非关联 peak | 新增关联具有进化保守性 | 保守性不等于功能验证 | Extended Data 图 5C |
| ABC model 验证 | 新增关联与独立预测的 enhancer-gene 关系一致 | 本文关联 vs ABC 预测 | 新增关联显著富集 ABC 预测 | 多分辨率关联与独立方法一致 | ABC 本身是计算预测，非实验验证 | Extended Data 图 5D |
| HRG 与 super-enhancer 重叠 | HRGs 富集已知 super-enhancer 基因 | HRGs vs 非 HRGs | 显著富集 | HRGs 代表多增强子调控的基因 | super-enhancer 定义本身有争议 | Results 图 2D |
| 增强子模块与表达关系 | 总可及性预测表达水平 | 高表达 vs 低表达细胞类型的总可及性 | 正相关 | 支持增强子加性模型 | 相关性不等于因果性 | Results 图 2F–I, Extended Data 图 5F |
| LDSC 细胞类型富集 | AGA 风险变异富集于 DP 细胞 | AGA vs 其他 trait × 所有细胞类型 | AGA 最强富集于 DP | DP 是 AGA 的关键驱动细胞 | 富集不等于因果 | Results 图 5A |
| TP63 靶点验证 | 预测的 TP63 靶点在 TP63 突变中下调 | 预测靶点 vs 非靶点 | 显著富集下调基因（OR=1.95） | 预测的 TP63 靶点具有功能相关性 | 仅一个 TF 验证 | Results 图 3I |
| KLF4 靶点验证 | 预测的 KLF4 靶点在 KLF4 敲低中下调 | 预测靶点 vs 非靶点 | 显著富集下调基因（OR=1.87） | 预测的 KLF4 靶点具有功能相关性 | 仅一个 TF 验证 | Results 图 3K |
| gkm-SVM 性能 | 模型可准确预测细胞类型特异可及性 | 10 折交叉验证 | 高 AUROC/AUPRC | 序列模型可捕捉细胞类型特异的调控语法 | 预测性能不等于因果效应 | Extended Data 图 10A–D |
| SNP 优先级排序 | 高置信 SNP 与 eQTL 一致 | 高置信 SNP vs 随机 SNP | 显著富集 eQTL | 预测的 SNP 具有调控功能证据 | eQTL 本身受 LD 混淆 | Results 图 6E |

---

## 11 结论正确解读

- **任务范围**：本文的结论限于**人头皮组织**的细胞类型和调控元件图谱，以及**AGA、湿疹、发色**三个 trait 的遗传信号富集分析。结论不直接推广到其他组织或疾病。
- **enhancer-gene 关联是计算推断**：peak-to-gene 关联基于相关性，不证明物理增强子-启动子互作，也不证明因果关系。作者明确表示需要实验验证。
- **HRG 增强子加性模型**：支持加性模型，但不排除存在非加性（协同/冗余）效应的 enhancer。加性模型是统计层面的近似。
- **LDSC 富集是遗传信号层面的结论**：AGA 信号富集于 DP 细胞开放染色质，说明 DP 细胞中的调控元件富集 AGA 风险位点，但不证明 DP 细胞是 AGA 的唯一或首要驱动者。
- **gkm-SVM 预测的是可及性，不是 TF 结合**：模型预测 SNP 对染色质可及性的影响，间接推断对 TF 结合的破坏。GkmExplain 归因分数是模型解释，不是实验验证的 TF 结合变化。
- **SNP 优先级排序是假设生成**：47/19/19 个 SNP 是候选，需要功能实验（如报告基因、CRISPR 编辑）验证。
- **斑秃（AA）样本的结论有限**：AA 样本中未发现独特的 T 细胞亚群或差异 peak，可能是统计功效不足或样本量限制，不能排除 AA 中存在 T 细胞亚群特异的调控变化。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 样本量有限 | AA 样本 n=5，DP 细胞数量稀少，无法训练 DP 特异的 gkm-SVM 模型 | 未来增加样本量或富集 DP 细胞 | Results 图 6, Methods 节 |
| enhancer-gene 关联为计算推断 | 基于相关性，非物理互作验证 | 需要实验验证（如 CRISPR、Hi-C） | Discussion 节 |
| gkm-SVM 无法覆盖所有细胞类型 | 仅训练了细胞数足够的聚类（28/38） | 未来在更多细胞类型中训练模型 | Methods 节 |
| 无法识别 AA 特异的 T 细胞调控变化 | 未发现 AA 与对照 T 细胞间的显著差异 peak | 可能需要更大样本量或更精细的亚群分析 | Results 图 4, Discussion 节 |
| SNP 效应预测缺乏实验验证 | 高置信 SNP 仅与 eQTL 一致，未做功能实验 | 需要报告基因、CRISPR 等实验验证 | Discussion 节 |
| 部分 enhancer-gene 关联可能受连锁不平衡影响 | 未明确讨论 | 未提供 | 未提供 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 多分辨率 peak-to-gene 关联的 50–100% 增量可能部分来自统计功效差异 | 亚聚类样本量更小，相关性估计更不稳定，可能产生更多假阳性关联 | 如果新增关联多为假阳性，则 HRG 分析和下游 SNP 注释的可靠性受影响 | 用独立数据（如其他皮肤 scATAC 数据）重复关联推断，或对新增关联进行实验验证 | Results 图 2A, Extended Data 图 5A |
| HRG 的 enhancer 加性模型基于相关性，未排除 enhancer 冗余或协同效应 | 加性模型可能过度简化真实调控逻辑 | 如果存在强协同效应，基于加性模型的表达预测会失真 | 用 CRISPR 干扰逐个/组合删除 enhancer，测量表达变化 | Results 图 2F–I |
| gkm-SVM 的 delta score 仅反映模型预测变化，不直接测量 TF 结合 | 模型可能学到的是序列特征与可及性的相关性，而非因果 TF 结合 | 如果模型学到的是间接特征，SNP 效应预测可能误导 | 用 SNP 所在位点的体外 TF 结合实验（EMSA、SELEX）验证 | Results 图 6, Methods 节 |
| LDSC 富集分析使用 peak 集合而非单个 peak，可能掩盖 peak 内的功能异质性 | 一个 peak 内可能包含多个 TF 结合位点，仅部分受 SNP 影响 | 如果 peak 内功能位点未被区分，SNP 优先级排序可能遗漏关键变异 | 对 peak 内 SNP 进行更精细的序列分析（如 motif 破坏评分） | Results 图 5, Methods 节 |
| 斑秃样本中未发现 T 细胞差异，可能是样本量不足而非真实阴性 | n=5 的 AA 样本可能无法检测到效应量较小的差异 | 如果存在但未检测到，可能遗漏 AA 的关键免疫机制 | 增加 AA 样本量，或使用更敏感的差异分析方法 | Results 图 4, Discussion 节 |
| 训练 gkm-SVM 时正负样本的选取可能引入偏差 | 负样本为 GC 匹配的随机基因组区域，可能包含未被检测到的可及区域 | 如果负样本包含真实可及区域，模型会低估序列特征 | 使用独立 ATAC 数据验证负样本的不可及性 | Methods 节 |

---

## 14 学到什么

> 以下为面向「蛋白质-DNA互作（TF–DNA结合机制）× AI/物理模拟」课题的可迁移知识。

### 概念层面

1. **增强子模块化加性模型**：一个基因的表达可能由多个 enhancer 的可加性贡献决定。对于 TF–DNA 互作研究，这意味着单个 TF 结合位点的功能效应需要在多个 enhancer 的背景下评估，而非孤立看待。
2. **多分辨率调控推断**：同一数据在不同聚类粒度下能揭示不同层次的调控关系。TF–DNA 互作研究可借鉴此思路：在粗粒度（细胞类型）和细粒度（细胞状态/亚群）下分别分析 TF 结合模式，可能发现不同的调控逻辑。
3. **细胞类型特异的调控元件是连接遗传变异与疾病的桥梁**：TF 结合位点的功能重要性是细胞类型依赖的。研究 TF–DNA 互作时，应优先关注疾病相关细胞类型中的结合事件。

### 方法层面

4. **chromVAR 的 TF motif 活性分析**：通过 motif 在可及染色质中的富集程度推断 TF 活性，是连接 ATAC-seq 与 TF 结合的有效工具。可迁移到其他组织或疾病场景。
5. **Linkage Score 整合策略**：将 peak-to-gene 关联强度与 motif 匹配置信度相乘，综合排序 TF 的潜在靶基因。这一思路可推广到其他「结合位点→靶基因」的推断场景。
6. **gkm-SVM + GkmExplain 的 SNP 效应预测**：用序列核 SVM 学习细胞类型特异的可及性模式，再用归因方法定位 SNP 对可及性的影响。这是从序列直接预测 TF 结合破坏的轻量级替代方案（相比深度学习），且可解释性更好。
7. **多证据整合的 SNP 优先级排序**：将 peak 重叠、peak-to-gene 关联、序列模型预测、eQTL 证据结合，逐步过滤候选 SNP。这一流程可迁移到任何非编码变异功能解读任务。

### 实验设计层面

8. **外部数据验证计算推断**：用 ABC model、TF 扰动数据、eQTL 等独立资源验证计算预测，是增强结论可信度的有效策略。
9. **多分辨率验证**：在多个聚类水平上重复关键分析，检验结论的稳健性。

---

## 15 与已有知识连接

- **与单细胞多组学整合方法的关系**：本文使用 CCA 整合 scRNA 和 scATAC，与 Seurat v4 的加权最近邻（WNN）方法互补。WNN 可同时利用 RNA 和 ATAC 模态进行联合聚类，而本文的 CCA 整合主要用于 peak-to-gene 关联推断。
- **与 enhancer-gene 预测工具的关系**：本文的 peak-to-gene 关联方法与 ABC model（Activity-by-Contact）互补。ABC 基于增强子活性和三维接触频率，本文基于单细胞共变异。两者一致性验证（Extended Data 图 5D）增强了可信度。
- **与 TF 结合预测工具的关系**：gkm-SVM 是 DeepSEA、Enformer 等深度学习模型的轻量级替代。相比深度学习，gkm-SVM 在小样本场景下更稳定，且 GkmExplain 提供了逐碱基归因，与 TF-MoDISco 等 motif 发现工具互补。
- **与 GWAS 功能解读的关系**：本文的「细胞类型特异 peak + LDSC + 序列模型」流程与 sc-linker、scGRNom 等工具思路一致，但本文增加了 gkm-SVM 序列层面的预测，提供了更精细的 SNP 效应估计。
- **与 TF–DNA 互作结构预测的关系**：本文未涉及 AlphaFold、MD 模拟等结构方法，但其「SNP 破坏 TF 结合 motif」的预测可作为结构生物学研究的输入——预测破坏结合的 SNP 可用于后续 MD 模拟或结合实验验证。
- **与课题方向的衔接**：本文提供的 enhancer-gene 调控网络和候选 SNP 列表，可作为 TF–DNA 互作研究的「候选结合位点库」。例如，AGA 相关的 DP 细胞 enhancer 中的 TF 结合位点，可进一步用 ChIP-seq、CUT&Tag 或结构预测方法验证。

---

## 16 研究想法

> 以下为面向「蛋白质-DNA互作（TF–DNA结合机制）× AI/物理模拟」课题的研究候选。

### 候选 1：基于 gkm-SVM 的 TF 结合特异性跨细胞类型迁移学习

- **来源观察**：本文为每个细胞类型独立训练 gkm-SVM，但未利用细胞类型间的共享调控语法。
- **核心假设**：不同细胞类型的 TF 结合规则共享底层序列语法，迁移学习可提升稀有细胞类型（如 DP）的预测性能。
- **方法**：用多任务学习或元学习框架，在细胞类型间共享 gkm-SVM 的低层特征，同时保留细胞类型特异的输出层。
- **验证**：在本文的 28 个聚类上比较单任务 vs 多任务 gkm-SVM 的 AUROC/AUPRC，特别关注细胞数较少的聚类。
- **创新状态**：unverified

### 候选 2：将 GkmExplain 归因分数与 TF 结构信息结合，预测 SNP 对结合亲和力的定量影响

- **来源观察**：本文用 GkmExplain 预测 SNP 对可及性的影响，但未量化对 TF 结合亲和力的影响。
- **核心假设**：GkmExplain 归因分数与 TF–DNA 结合亲和力变化（ΔΔG）相关，可作为一种轻量级替代 MD 模拟的预测器。
- **方法**：收集已有 TF–DNA 结合亲和力数据（如 SELEX、HT-SELEX、PBMs），计算 SNP 的 GkmExplain delta score，与实验测得的 ΔΔG 回归，评估预测能力。
- **验证**：在独立数据集上测试；对高影响 SNP 用 MD 模拟或 EMSA 实验验证。
- **创新状态**：unverified

### 候选 3：多分辨率 peak-to-gene 关联与 TF 共结合分析，推断增强子模块的组合编码规则

- **来源观察**：本文发现 HRGs 的 enhancer 呈模块化使用，但未分析模块内 TF 的组合模式。
- **核心假设**：同一 enhancer 模块内的 TF 结合位点存在组合编码规则（如协同、互斥），且这些规则在不同细胞类型间保守或分化。
- **方法**：对每个 HRG 的 enhancer 模块进行 TF motif 共富集分析，构建 TF–TF 共结合网络；比较不同细胞类型间的网络差异。
- **验证**：用外部 ChIP-seq 数据验证预测的 TF 共结合；用 CRISPR 干扰验证模块内 TF 的功能依赖性。
- **创新状态**：unverified

### 候选 4：将本文的 enhancer-gene 关联与 AlphaFold 结构预测结合，解析疾病相关 SNP 的分子机制

- **来源观察**：本文识别了 AGA 和湿疹的高置信 SNP，但未解析其分子机制。
- **核心假设**：部分疾病相关 SNP 通过改变 TF 结合位点的三维结构（而非仅序列）影响结合。
- **方法**：对高置信 SNP 所在的 enhancer 区域，用 AlphaFold 或 RoseTTAFold 预测 TF–DNA 复合物结构，比较参考/替代等位基因的结合能差异。
- **验证**：对预测高影响的 SNP 用表面等离子共振（SPR）或电泳迁移率变动分析（EMSA）验证结合亲和力变化。
- **创新状态**：unverified

### 候选 5：基于单细胞 ATAC 的 TF 结合动力学建模，预测增强子模块的时序激活

- **来源观察**：本文提供了静态的 enhancer-gene 关联，但未分析增强子激活的时序动态。
- **核心假设**：在细胞分化轨迹上，enhancer 模块的激活顺序由 TF 结合位点的亲和力层级决定。
- **方法**：利用本文的角蛋白细胞分化轨迹数据，对每个 enhancer 模块计算 chromVAR motif 活性的时序变化，构建 TF–enhancer 激活层级模型。
- **验证**：用分化时间序列的 ATAC-seq 或 ChIP-seq 数据验证预测的激活顺序。
- **创新状态**：unverified

### 候选 6：将 gkm-SVM 预测的 SNP 效应与 eQTL 共定位分析结合，构建疾病因果变异的精细定位流程

- **来源观察**：本文的 SNP 优先级排序已整合 eQTL，但未做共定位分析。
- **核心假设**：同时满足「预测破坏可及性」和「与 eQTL 共定位」的 SNP 更可能是因果变异。
- **方法**：对 AGA 和湿疹的 47/19 个 SNP，进行共定位分析（coloc、SMR），结合 gkm-SVM delta score 构建综合评分。
- **验证**：用 CRISPR 编辑验证 top SNP 对基因表达的影响。
- **创新状态**：unverified