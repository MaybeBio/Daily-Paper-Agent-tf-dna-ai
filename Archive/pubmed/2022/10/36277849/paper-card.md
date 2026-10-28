## 01 基本信息

- **标题**: Single-cell multiome of the human retina and deep learning nominate causal variants in complex eye diseases
- **作者与单位**: Wang, Sean K; Nair, Surag; Li, Rui; Kraft, Katerina; Pampari, Anusri; Patel, Anusri; Kang, Joyce B; Luong, Christy; Kundaje, Anshul; Chang, Howard Y（斯坦福大学，Howard Y. Chang 为通讯作者）
- **期刊/预印本平台**: Cell Genomics
- **年份**: 2022-10-25
- **论文类型**: 研究论文（Research Article）
- **领域**: 单细胞多组学、基因组学、深度学习、复杂眼病遗传学
- **关键词**: single-cell multiome, scRNA-seq, scATAC-seq, HiChIP, eQTL, deep learning, BPNet, GWAS, retina, causal variants
- **DOI/arXiv 号**: 10.1016/j.xgen.2022.100164
- **代码**: BPNet 模型训练代码：https://doi.org/10.5281/zenodo.6796067；scRNA/scATAC 分析代码：https://doi.org/10.5281/zenodo.6795162
- **数据**: GEO: GSE196235；可视化网站：https://eyemultiome.su.domains/；BPNet 模型：https://doi.org/10.5281/zenodo.6330053
- **阅读日期**: 未提供
- **在该课题方向中的位置**: 本文是「单细胞多组学 × 深度学习 × 复杂疾病遗传学」交叉方向的代表性工作。对于「蛋白质-DNA 互作（TF–DNA 结合机制）× AI」课题，本文的核心可迁移价值在于：(1) 将 base-resolution 深度学习模型（BPNet）应用于细胞类型特异的染色质可及性数据，预测 SNP 对 TF 结合的影响；(2) 展示了如何将深度学习预测与实验数据（HiChIP、eQTL）整合，形成从变异到靶基因的完整证据链；(3) 提供了细胞类型分辨率的 TF 基序富集与足迹分析流程，可直接迁移到其他组织或细胞类型的 TF–DNA 结合研究。

## 02 一句话总结

本文构建了成人视网膜的单细胞多组学图谱（>50,000 细胞，13 种细胞类型），整合 HiChIP 增强子连接组、eQTL 数据和基于 BPNet 架构的 base-resolution 深度学习模型，从 7,034 个非编码 SNP 中筛选出 23 个高效应 SNP，并预测其通过改变细胞类型特异的 TF 结合（如 LHX2、NEUROD4）来影响靶基因表达，从而在特定视网膜细胞类型中发挥致病作用。

## 03 研究问题

- **具体问题**: 复杂眼病（AMD、青光眼、糖尿病视网膜病变、近视、黄斑毛细血管扩张症2型）GWAS 鉴定出的非编码 SNP 如何在特定视网膜细胞类型中发挥功能？它们影响哪些靶基因、通过何种分子机制（特别是 TF 结合的改变）？
- **为什么重要**: 复杂眼病 GWAS 已发现数百个关联位点，但绝大多数位于非编码区，功能解读困难。理解这些变异的细胞类型特异性和分子机制，是连接遗传关联与疾病病理的关键步骤，也是开发细胞类型靶向治疗的基础。
- **现有方法不足**: (1) 传统 bulk 组织分析无法解析细胞类型特异性的调控机制；(2) 仅用「最近基因」注释 SNP 靶基因不准确（本文显示 44.3% 的预测靶基因不同于线性基因组上的最近基因）；(3) 单纯依赖染色质可及性重叠无法区分功能性 SNP 与乘客 SNP；(4) 缺乏对 SNP 如何影响 TF 结合的机制性预测。
- **精确的「Can ... ?」研究问题**: Can integration of single-cell multiome (scRNA-seq + scATAC-seq) with HiChIP, eQTL, and base-resolution deep learning models nominate causal noncoding variants and their cell-type-specific target genes and TF-binding mechanisms in complex eye diseases?

## 04 背景与发展脉络

**注：以下脉络基于本文框架及文中引用的代表性工作，部分经外部核验（标注）。**

1. **GWAS 非编码变异功能解读的早期尝试**（2010s 初-中）: 主要依赖 LD 扩展、基因组注释重叠（如 ENCODE）和 eQTL 分析。代表性方法包括 GREGOR、fGWAS 等。局限：缺乏细胞类型分辨率，无法区分因果变异与 LD 代理变异。
2. **单细胞 ATAC-seq 应用于复杂疾病**（2018-2021）: 如 Corces et al. (2020, Nat Genet) 构建了人类免疫细胞的 scATAC-seq 图谱并用于自身免疫病变异解读。局限：缺乏同一细胞的转录组信息，难以建立可及性-表达的直接关联。
3. **单细胞多组学技术（10x Multiome）**（2020-2021）: 同一细胞同时获得转录组和染色质可及性，使得 peak-to-gene 关联预测成为可能。代表性工作包括 Granja et al. (2021, Nat Genet) 的 ArchR 框架。
4. **增强子-启动子互作图谱（HiChIP）**（2016-2021）: 如 Mumbach et al. (2016, Nat Methods) 开发 HiChIP 技术，用于在特定组蛋白修饰（如 H3K27ac）背景下鉴定 3D 基因组互作。局限：bulk 水平，缺乏细胞类型分辨率。
5. **Base-resolution 深度学习模型预测调控变异**（2018-2021）: 如 BPNet (Avsec et al., 2021, Nat Genet) 最初用于 ChIP-seq 的 base-resolution 预测，可解释性分析可鉴定 TF 基序及其协同作用。Enformer (Avsec et al., 2021, Nat Methods) 等模型进一步扩展了序列-表达预测。局限：多数模型在 bulk 或细胞系数据上训练，缺乏原代组织的细胞类型特异性。
6. **本文位置**: 首次将上述四类资源（单细胞多组学、HiChIP、eQTL、BPNet 深度学习）整合于同一组织（成人视网膜），形成从「变异→细胞类型→调控元件→TF 结合→靶基因」的完整功能注释管线。其创新点在于：(a) 成人原代组织的单细胞多组学图谱；(b) 将 BPNet 从 ChIP-seq 迁移到 scATAC-seq 的细胞类型特异训练；(c) 多证据整合的 SNP 优先级排序框架。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 非编码 SNP 功能解读困难 | 96.5% 的疾病相关 SNP 位于非编码区，无法直接通过编码效应解释 | GWAS 关联位点多为调控变异，需细胞类型特异的调控注释 | Results 节 "The vast majority (96.5%) of these SNPs localized to noncoding regions" |
| 缺乏细胞类型分辨率 | 传统 bulk 组织分析无法确定变异在哪种细胞类型中起作用 | 视网膜由多种功能特化的细胞类型组成，不同疾病可能涉及不同细胞类型 | Results 节 图 4B 显示 SNP 在不同细胞类型中的可及性分布差异显著 |
| 最近基因注释不准确 | 44.3% 的预测靶基因不同于线性基因组上的最近基因 | 增强子可通过 3D 染色质互作调控远距离基因 | Results 节 "For nearly half (44.3%) of these peaks, our predictions differed from the nearest gene" |
| 难以区分功能性 SNP 与乘客 SNP | 仅凭染色质可及性重叠无法确定 SNP 是否具有调控效应 | 需要功能预测（如深度学习）和实验验证（如 HiChIP、eQTL）的多重证据 | Results 节 图 6B 显示高效应 SNP 比例远低于随机 SNP |
| 缺乏对 TF 结合影响的机制性预测 | 传统方法无法预测 SNP 如何改变 TF 结合 | 需要 base-resolution 模型和基序分析 | Results 节 图 6C 展示 SNP 对 TF 基序的破坏/创建 |
| 稀有细胞类型覆盖不足 | 微胶质细胞和星形胶质细胞仅占 0.4% 的细胞 | 稀有细胞类型在疾病中可能具有重要作用，但难以捕获足够数量 | Results 节 "rarer cell types, such as astrocytes and microglia, which each constituted only 0.4% of profiled cells" |

## 06 核心思想

### 1) 表面方法

构建成人视网膜单细胞多组学图谱（10x Multiome 平台，8 个供体，51,645 个细胞），鉴定 13 种细胞类型。收集 1,331 个 GWAS index SNP（5 种眼病），LD 扩展至 7,034 个非编码 SNP。将 SNP 映射到细胞类型特异的 scATAC-seq peak 上，结合三种正交证据进行优先级排序：(a) peak-to-gene 共可及性关联（预测靶基因）；(b) H3K27ac HiChIP 3D 互作（验证靶基因）；(c) 基于 BPNet 架构的细胞类型特异深度学习模型（预测 SNP 对染色质可及性的影响）。最终鉴定出 23 个高效应 SNP，并对其中的代表性 SNP 进行 TF 基序层面的机制解析。

### 2) 核心洞察

- **细胞类型特异性是解读非编码变异的关键维度**：同一 SNP 在不同细胞类型中的可及性、靶基因和 TF 结合效应可能完全不同。例如 rs1532278 在 13 种细胞类型中的 9 种可及，但深度学习预测其功能效应仅限于 Müller 胶质细胞，因为该细胞类型特异表达识别其所在基序的 TF（推测为 LHX2）。
- **多证据整合优于单一证据**：peak 可及性、3D 互作、eQTL 和深度学习预测各自有局限，但交叉验证可显著提高 SNP 优先级排序的可信度。23 个高效应 SNP 中，许多同时满足多个标准。
- **深度学习模型可提供机制性假设**：BPNet 不仅能预测 SNP 的效应大小，还能通过基序分析揭示 SNP 破坏/创建了哪个 TF 的结合位点，从而将「关联变异」转化为「分子机制假说」。例如 rs1874459 被预测创建了一个新的 bHLH 基序，该基序可能被 NEUROD4 识别。

### 3) 可能的普适教训 [Analysis]

- **单细胞多组学 + 深度学习的组合是解读非编码变异的强大范式**：这一框架不限于视网膜或眼病，可迁移到任何具有单细胞多组学数据的组织/疾病。对于 TF–DNA 结合研究，这意味着「细胞类型特异的 TF 结合图谱」可以通过 scATAC-seq + 深度学习模型来系统性地构建，而非依赖逐个 TF 的 ChIP-seq。
- **「可及性 ≠ 功能」**：本文的一个重要方法论贡献是展示了如何从「SNP 在可及染色质中」这一静态观察，推进到「SNP 改变可及性」这一动态预测。这提醒 TF–DNA 结合研究：基序的存在或可及性并不等于实际结合，需要功能验证。
- **细胞类型特异的 TF 表达是连接变异与功能的桥梁**：本文通过将 SNP 的预测效应与细胞类型特异的 TF 表达谱结合，提出了「细胞类型特异 TF 决定 SNP 功能」的模型。这一思路可推广到其他复杂疾病。

## 07 方法总览

- **输入**: (1) 8 个成人视网膜样本（4 个供体）的 10x Multiome 数据（scRNA-seq + scATAC-seq）；(2) 5 种眼病的 1,331 个 GWAS index SNP；(3) 公开的 HiChIP 数据（H3K27ac）；(4) 公开的视网膜 eQTL 数据（EyeGEx）
- **输出**: (1) 13 种视网膜细胞类型的转录组和染色质可及性图谱；(2) 7,034 个非编码 SNP 的细胞类型特异性注释；(3) 23 个高效应 SNP 列表及其预测靶基因、TF 结合机制
- **主要模块**:
  1. **单细胞多组学数据处理**: Cell Ranger ARC 生成 count matrix → ArchR 进行 QC、聚类、细胞类型注释
  2. **Peak calling 与细胞类型特异 peak 鉴定**: MACS2 在每种细胞类型的 pseudo-bulk 数据上 calling peak
  3. **SNP 注释**: 将 LD 扩展后的 SNP 映射到 peak 上，记录细胞类型特异性
  4. **Peak-to-gene 关联**: ArchR 的 getPeak2GeneLinks 函数，基于同一细胞的 RNA 和 ATAC 共变
  5. **HiChIP 互作分析**: HiC-Pro 处理 → HiCCUPS calling loops → 与 SNP 所在 peak 重叠
  6. **eQTL 分析**: 查询 EyeGEx 数据库，记录 SNP-基因关联
  7. **BPNet 深度学习**: 每种细胞类型训练独立的 BPNet 模型（输入 2,114 bp 序列，预测 1,000 bp 窗口内的 ATAC 可及性 profile 和 counts），对 SNP 进行 in silico 突变分析（参考 vs 交替等位基因）
  8. **高效应 SNP 鉴定**: 满足 |log2 fold change| > 0.5 且 FDR < 0.01 的 SNP 被定义为高效应
  9. **TF 基序分析**: 对高效应 SNP 所在区域进行基序破坏/创建分析，结合细胞类型特异的 TF 表达
- **训练**: BPNet 模型，5-fold 交叉验证，每折独立训练；损失函数为 profile 的 multinomial negative log-likelihood + counts 的 MSE
- **反馈回路**: 深度学习预测结果反馈到 SNP 优先级排序，与 HiChIP、eQTL 结果交叉验证
- **假设**: (1) 染色质可及性的改变可反映调控效应；(2) 细胞类型特异的可及性 peak 是调控变异的功能载体；(3) BPNet 模型在 scATAC-seq 数据上的预测可迁移到 SNP 效应评估

**文字流程**: 视网膜样本 → 10x Multiome 文库制备 → 测序 → Cell Ranger ARC 处理 → ArchR QC/聚类/注释 → 13 种细胞类型 → 每种细胞类型 calling peaks → 收集 GWAS SNP → LD 扩展 → SNP-peak 重叠 → 三种正交分析（peak-to-gene、HiChIP、eQTL）→ BPNet 训练与 SNP 评分 → 高效应 SNP 鉴定 → TF 基序与表达分析 → 机制假说

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 单细胞多组学图谱构建 | 同时获取转录组和染色质可及性 | 建立 peak-to-gene 关联需要同一细胞的两种模态 | 输入：10x Multiome 原始数据；输出：13 种细胞类型的 RNA/ATAC 矩阵 | Results 图 1B-D 显示清晰的细胞类型分离和 marker 基因表达 | 预期影响：无法进行 peak-to-gene 关联分析，SNP 靶基因预测只能依赖最近基因或 HiChIP（实测影响未提供） |
| 细胞类型特异的 peak calling | 鉴定每种细胞类型的调控元件 | 不同细胞类型的调控景观不同 | 输入：pseudo-bulk ATAC 数据；输出：每种细胞类型的 peak 集合（共 620,386 个） | Results 图 2A-C 显示 peak 的细胞类型特异性和供体间一致性 | 预期影响：SNP 的细胞类型注释丢失，无法区分 SNP 在哪种细胞中可能具有功能 |
| SNP-LD 扩展与 peak 重叠 | 将 GWAS index SNP 扩展至 LD 代理 SNP，并映射到调控元件 | 单个 index SNP 不足以代表整个风险位点 | 输入：1,331 个 index SNP；输出：7,034 个非编码 SNP，其中 1,152 个与 peak 重叠 | Results 图 4A-B 显示 SNP 在不同细胞类型中的分布 | 预期影响：遗漏 LD 代理 SNP 中的功能性变异 |
| Peak-to-gene 关联预测 | 预测每个 peak 的靶基因 | 非编码 SNP 可能调控远距离基因 | 输入：RNA/ATAC 共变数据；输出：peak-gene 关联对 | Results 图 4C-D 显示 199,055 个 peak 有预测靶基因，44.3% 不同于最近基因 | 预期影响：靶基因预测严重依赖基因组距离，可能遗漏远程调控关系 |
| HiChIP 增强子连接组 | 提供 3D 基因组互作证据 | 验证 peak-to-gene 预测的物理基础 | 输入：H3K27ac HiChIP 数据；输出：9,670 个 loops | Results 图 5A 显示 >95% loop anchors 与 scATAC peak 重叠 | 预期影响：缺乏 3D 互作验证，SNP-靶基因关联的物理基础不明确 |
| eQTL 分析 | 提供 SNP-基因表达的统计关联 | 独立于染色质数据的验证 | 输入：EyeGEx 数据库；输出：SNP-基因关联 | Results 图 5B-D 显示 596 个 SNP 有显著 eQTL | 预期影响：缺乏表达层面的统计支持 |
| BPNet 深度学习模型 | 预测 SNP 对染色质可及性的影响 | 提供 base-resolution 的功能预测 | 输入：2,114 bp 序列（参考/交替等位基因）；输出：预测的可及性变化 | Results 图 6B 显示高效应 SNP 比例显著高于随机背景（2.0% vs 0.2%） | 预期影响：无法区分功能性 SNP 与乘客 SNP，优先级排序能力大幅下降 |
| TF 基序与足迹分析 | 预测 SNP 影响的 TF 结合 | 将 SNP 效应转化为分子机制 | 输入：高效应 SNP 区域序列 + 细胞类型 TF 表达；输出：候选 TF | Results 图 6E-G 显示 LHX2 和 NEUROD4 的细胞类型特异表达模式 | 预期影响：机制假说缺失，SNP 功能解读停留在「改变可及性」层面 |

## 09 关键公式符号

本文核心公式来自 BPNet 模型的损失函数（引用自 Avsec et al., 2021, Nat Genet，原文未给出完整公式，以下为 BPNet 原始论文中的定义）：

**BPNet 损失函数**:
$$L = L_{profile} + \lambda \cdot L_{counts}$$

其中：
- $L_{profile}$ = multinomial negative log-likelihood (MNLL)，衡量预测的 base-resolution 可及性 profile 与观测 profile 的差异
- $L_{counts}$ = mean squared error (MSE)，衡量预测的总 counts 与观测 counts 的差异
- $\lambda$ = 相对权重，本文设为 0.1 × mean total counts per region

**SNP 效应评分**:
$$\Delta = \log_2(\text{predicted counts}_{\text{alt}} / \text{predicted counts}_{\text{ref}})$$

其中：
- $\text{predicted counts}_{\text{ref}}$ = 参考等位基因序列的预测 counts
- $\text{predicted counts}_{\text{alt}}$ = 交替等位基因序列的预测 counts

**显著性检验**: 对每个 SNP 的 $\Delta$ 进行 one-sided Poisson test，以预测的参考等位基因 counts 为率参数，检验交替等位基因 counts 是否显著偏离。P 值通过 Fisher's method 跨细胞类型合并，并进行 Benjamini-Hochberg FDR 校正。

**LD 扩展标准**: $R^2 > 0.9$（基于 1000 Genomes Project Phase 3 基因型）

**peak-to-gene 关联阈值**: 相关性 > 0.3（ArchR getPeak2GeneLinks 默认参数）

## 10 实验设计与证据链

### 数据集与资源
- **单细胞多组学数据**: 8 个成人视网膜（4 个供体），10x Multiome 平台，51,645 个细胞，13 种细胞类型
- **GWAS SNP**: 1,331 个 index SNP（AMD、青光眼、DR、近视、MacTel），来自 NHGRI-EBI GWAS Catalog
- **LD 扩展后 SNP**: 7,034 个非编码 SNP
- **HiChIP**: H3K27ac，2 个生物学重复
- **eQTL**: EyeGEx 数据库（bulk 视网膜）
- **BPNet 模型**: 每种细胞类型 5-fold，共 65 个模型
- **背景 SNP**: 9,984 个随机非编码 SNP（GC 含量匹配）

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 单细胞多组学图谱构建 | 成人视网膜可被分为 13 种细胞类型 | 与已发表 scRNA-seq 数据比较 | 22 个 cluster 归为 13 种细胞类型，marker 基因表达正确 | 图谱质量可靠，可用于下游分析 | 未验证细胞亚型的存在 | Results 图 1B-D |
| scATAC peak 与 bulk ATAC 重叠 | 单细胞 ATAC 可复现 bulk 结果 | 与已发表 bulk ATAC 数据比较 | >90% bulk peak 被 scATAC peak 覆盖 | 单细胞 ATAC 数据质量高 | 未比较 peak 强度，仅比较存在性 | Results 图 2B |
| SNP-peak 重叠分析 | 眼病 SNP 富集于特定细胞类型的调控元件 | 5 种眼病 × 13 种细胞类型 | 不同眼病 SNP 富集于不同细胞类型（如 AMD 富集于微胶质细胞） | 细胞类型特异性是解读眼病 SNP 的关键 | 未进行统计显著性检验（如置换检验） | Results 图 4B |
| Peak-to-gene 关联 | 可预测 SNP 的靶基因 | 相关性 > 0.3 | 199,055 个 peak 有预测靶基因 | 提供了靶基因预测资源 | 未实验验证预测的靶基因 | Results 图 4C-D |
| HiChIP 验证 | 3D 互作支持 peak-to-gene 预测 | 与 peak-to-gene 预测重叠 | 多个 SNP 的预测靶基因得到 HiChIP loop 支持 | 3D 互作增强靶基因预测可信度 | 未对全部预测进行验证 | Results 图 5A |
| eQTL 验证 | SNP 与基因表达相关 | EyeGEx 数据库 | 多个 SNP 有显著 eQTL | 表达层面的统计支持 | eQTL 为 bulk 数据，缺乏细胞类型分辨率 | Results 图 5B-D |
| BPNet 高效应 SNP 鉴定 | 深度学习可识别功能性 SNP | 高效应 SNP vs 随机背景 SNP | 23 个高效应 SNP（2.0%），显著高于随机背景（0.2%） | 深度学习可有效富集功能性 SNP | 未实验验证 23 个 SNP 的功能 | Results 图 6B |
| TF 基序分析 | 高效应 SNP 通过改变 TF 结合发挥作用 | 参考 vs 交替等位基因的基序匹配 | rs1532278 破坏 Müller 胶质细胞中的同源异型域 TF 基序；rs1874459 创建 bHLH 基序 | 提供了 SNP→TF 结合的机制假说 | 未通过实验（如电泳迁移率变动分析）验证 TF 结合变化 | Results 图 6C-G |

## 11 结论正确解读

- **任务范围**: 本文的任务是「非编码 SNP 的功能注释与优先级排序」，而非「因果变异的最终实验验证」。23 个高效应 SNP 是「预测」结果，需要实验验证。
- **oracle/真值输入**: 本文使用了多个外部数据源作为验证，包括已发表的 bulk ATAC-seq、EyeGEx eQTL 数据库、已发表的视网膜 scRNA-seq 数据。这些数据本身可能存在偏差（如 bulk eQTL 缺乏细胞类型分辨率）。
- **端到端状态**: 本文的流程是「数据生成 → 计算分析 → 预测」，未包含湿实验验证环节。因此，从 SNP 到疾病机制的完整链条尚未闭合。
- **算力成本**: 未提供具体算力信息。BPNet 模型训练需要 GPU 资源，但具体成本未披露。
- **历史数据依赖**: 依赖 1000 Genomes Project Phase 3 的 LD 结构、EyeGEx 的 eQTL 数据、已发表的 bulk ATAC-seq 数据。这些数据的质量直接影响本文结论。
- **模型依赖**: BPNet 模型在 scATAC-seq 数据上的表现可能不如其在 ChIP-seq 数据上的表现（scATAC 的 noise 水平更高），但本文未提供模型性能的详细评估（如 AUROC、AUPRC）。
- **最难情形**: 稀有细胞类型（微胶质细胞、星形胶质细胞，各占 0.4%）的 peak calling 和模型训练可能不够稳健。作者在 Limitations 中承认了这一点。
- **群体/领域边界**: 样本来自 4 个供体（8 只眼），均为无眼病史的个体。结论可能不适用于其他种族/族裔群体或其他年龄段。视网膜的细胞类型组成和调控景观可能因年龄、疾病状态而异。
- **不确定性**: 23 个高效应 SNP 的效应量（|log2 fold change| > 0.5）是相对较大的预测效应，但未提供置信区间。对于效应量较小的 SNP，模型可能无法可靠检测。

**有边界的复述**: 本文在 4 个无眼病史供体的成人视网膜中，通过单细胞多组学、HiChIP、eQTL 和 BPNet 深度学习的整合分析，预测了 23 个与 5 种复杂眼病相关的非编码 SNP 可能通过改变特定细胞类型中的 TF 结合来影响靶基因表达。这些预测需要实验验证，且结论的推广受限于样本量、供体多样性和计算模型的固有局限。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 稀有细胞类型覆盖不足 | 微胶质细胞和星形胶质细胞仅占 0.4% 的细胞，可能无法充分解析其调控景观 | 扩展图谱，纳入更多供体和细胞 | Limitations 节 |
| 缺乏功能实验验证 | 高效应 SNP 的预测未通过实验验证 | 在细胞或动物模型中验证 SNP 功能 | Limitations 节 |
| 其他眼部组织未覆盖 | 视网膜以外的眼部组织（如视网膜色素上皮、脉络膜、小梁网）可能也是疾病相关 SNP 的功能位点 | 对其他眼部组织进行类似的多组学分析 | Limitations 节 |
| 供体数量有限 | 仅 4 个供体，可能无法充分代表人群多样性 | 增加供体数量，纳入不同种族/族裔 | Limitations 节 |
| 深度学习模型的局限性 | BPNet 模型可能无法捕捉所有功能性 SNP 的效应 | 改进模型架构，整合更多功能基因组数据 | Limitations 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| BPNet 模型在 scATAC-seq 上的适用性未充分验证 | BPNet 最初为 ChIP-seq 设计，scATAC 的 noise 水平更高、信号更稀疏，模型性能可能下降 | 如果模型在 scATAC 上性能不佳，高效应 SNP 的鉴定可能不可靠 | 在已发表的 ChIP-seq 数据上验证模型性能，或使用独立的 scATAC 数据集进行交叉验证 | Methods 节 "Deep learning model training"；Avsec et al., 2021 |
| 高效应 SNP 的阈值选择缺乏敏感性分析 | |log2 fold change| > 0.5 且 FDR < 0.01 的阈值是任意的，不同的阈值可能产生不同的 SNP 列表 | 阈值选择直接影响最终结果 | 进行阈值敏感性分析，评估不同阈值下 SNP 列表的稳定性 | Results 节 "SNP scoring with BPNet" |
| Peak-to-gene 关联的因果方向不明确 | 相关性 > 0.3 的阈值可能包含大量假阳性，且相关性不等于因果性 | 如果 peak-to-gene 预测不准确，靶基因注释可能错误 | 使用 CRISPR 干扰/激活实验验证 peak-gene 功能连接 | Results 节 "Predicted target genes" |
| eQTL 数据为 bulk 水平，缺乏细胞类型分辨率 | EyeGEx 的 bulk eQTL 可能掩盖细胞类型特异性的调控效应 | 本文强调细胞类型特异性，但 eQTL 验证缺乏这一维度 | 使用单细胞 eQTL 数据（如 scRNA-seq eQTL）进行验证 | Results 节 "eQTL analysis" |
| 未报告模型性能指标 | 未提供 BPNet 模型在训练/验证集上的 AUROC、AUPRC 等指标 | 无法评估模型预测的可靠性 | 补充模型性能评估 | Methods 节 "Deep learning model training" |
| 23 个高效应 SNP 的效应量可能被高估 | 模型可能对训练数据过拟合，导致 SNP 效应预测偏大 | 过拟合会导致假阳性高效应 SNP | 使用独立的验证集（如其他视网膜 ATAC 数据）进行外部验证 | Results 节 图 6B |
| 未讨论 SNP 的等位基因特异性效应 | 模型预测的是参考 vs 交替等位基因的差异，但未验证杂合子中是否存在等位基因特异性可及性 | 等位基因特异性可及性是 SNP 功能的重要证据 | 在杂合子供体中检测等位基因特异性 ATAC 信号 | Results 节 "SNP scoring with BPNet" |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **细胞类型特异的深度学习模型训练策略**：本文为每种细胞类型独立训练 BPNet 模型，而非训练一个混合模型。这一策略对于 TF–DNA 结合研究有直接借鉴意义——不同细胞类型中同一 TF 的结合偏好可能不同，独立建模可捕捉这种特异性。可迁移到「预测细胞类型特异的 TF 结合位点」任务。

2. **多证据整合的变异优先级排序框架**：本文的「peak 可及性 + peak-to-gene 关联 + HiChIP 3D 互作 + eQTL + 深度学习预测」五重证据整合框架，可迁移到任何「非编码变异功能注释」任务。对于 TF–DNA 结合研究，这意味着评估一个变异是否影响 TF 结合时，不应仅依赖基序预测，而应整合染色质状态、3D 互作和表达关联。

3. **Base-resolution 突变效应预测方法**：本文使用 BPNet 对 SNP 进行 in silico 突变分析，比较参考/交替等位基因的预测可及性。这一方法可直接迁移到 TF–DNA 结合预测——对 TF 结合位点内的 SNP 进行同样的突变分析，预测其对 TF 结合亲和力的影响。

4. **「可及性变化 + 基序破坏/创建」的机制推断流程**：本文通过将 SNP 效应与基序分析结合，提出了「SNP 通过破坏/创建 TF 基序来改变可及性」的机制假说。这一流程可迁移到 TF–DNA 结合研究，用于从「SNP 改变可及性」推进到「SNP 改变特定 TF 的结合」。

5. **细胞类型特异 TF 表达作为功能解读的桥梁**：本文通过将 SNP 的预测效应与细胞类型特异的 TF 表达结合，提出了「细胞类型特异 TF 决定 SNP 功能」的模型。这一思路可迁移到其他组织——在解读非编码变异时，应优先考虑在相关细胞类型中高表达的 TF。

6. **单细胞多组学数据的 peak-to-gene 关联方法**：ArchR 的 getPeak2GeneLinks 方法利用同一细胞的 RNA 和 ATAC 共变来预测 peak 的靶基因。这一方法可迁移到 TF–DNA 结合研究——当 TF 结合位点与基因表达关联时，可利用共变信息推断调控关系。

7. **「高效应 SNP」的操作性定义**：本文定义了「高效应 SNP」的量化标准（|log2 fold change| > 0.5，FDR < 0.01），这一标准可迁移到其他深度学习预测任务，用于筛选值得实验验证的候选变异。

## 15 与已有知识连接

- **BPNet 架构**：本文使用的 BPNet 模型源自 Avsec et al. (2021, Nat Genet) 的 ChIP-seq base-resolution 预测工作。BPNet 的核心创新在于使用 multinomial loss 预测 base-resolution 的 profile，并通过 in silico 突变分析鉴定关键碱基。本文将其从 ChIP-seq 迁移到 scATAC-seq，扩展了其应用范围。

- **单细胞多组学分析框架**：本文的分析流程（Cell Ranger ARC → ArchR）与 Granja et al. (2021, Nat Genet) 的 ArchR 框架一致。ArchR 的 peak-to-gene 关联方法（getPeak2GeneLinks）是本文靶基因预测的核心工具。

- **非编码变异功能解读的经典工作**：本文与以下工作形成互补：(1) ENCODE 项目的调控元件注释；(2) Roadmap Epigenomics 的表观遗传图谱；(3) Finucane et al. (2015, Nat Genet) 的 LD score regression 框架（用于细胞类型富集分析）；(4) 视网膜 scRNA-seq 的早期工作（如 Lukowski et al. 2019, EMBO J）。本文的独特贡献在于将单细胞多组学与深度学习结合，实现了「变异→细胞类型→TF→靶基因」的端到端预测。

- **复杂眼病遗传学**：本文涉及的 5 种眼病（AMD、青光眼、DR、近视、MacTel）均有大量 GWAS 研究。本文的 SNP 列表来自 NHGRI-EBI GWAS Catalog，与 Fritsche et al. (2016, Nat Genet) 的 AMD GWAS、Choquet et al. (2020, Nat Genet) 的近视 GWAS 等工作直接相关。

- **TF–DNA 结合预测的深度学习**：本文的 BPNet 方法属于「序列→染色质可及性」的监督学习范式，与 DeepSEA (Zhou & Troyanskaya, 2015, Nat Methods)、Basenji (Kelley et al., 2018, PLoS Comput Biol) 等模型同属一个技术谱系。对于 TF–DNA 结合研究，本文展示了如何将这类模型从「预测可及性」扩展到「预测 SNP 效应」。

- **可迁移的候选方向** [Analysis]：本文的框架可迁移到以下方向：(1) 其他组织的单细胞多组学 + 深度学习变异解读；(2) 将 BPNet 从 ATAC 扩展到 TF 特异性 ChIP-seq 的联合建模；(3) 整合单细胞 TF 表达数据与深度学习预测，构建「细胞类型 × TF × 变异」的三维功能图谱；(4) 将本文的「高效应 SNP」定义与 CRISPR 筛选（如 CRISPRi/a）结合，实现高通量功能验证。

## 16 研究想法

**Agent 生成的研究候选**：

### 候选 1：细胞类型特异的 TF–DNA 结合预测模型（TF-BPNet）
- **名称**: Cell-type-specific TF binding prediction via multi-task BPNet
- **来源局限/观察**: 本文为每种细胞类型独立训练 BPNet，但未利用 TF 表达信息。不同细胞类型中同一 TF 的表达水平差异巨大，可能影响其结合。
- **核心假设**: 将 TF 表达作为条件输入，可提高 TF 结合预测的细胞类型特异性。
- **增量**: 在 BPNet 架构中引入 TF 表达作为条件变量（如 FiLM 层），实现「一个模型预测多种细胞类型的 TF 结合」。
- **初步方法**: 使用本文的视网膜 scATAC-seq 数据 + TF 表达矩阵，训练条件 BPNet；比较与独立训练模型的性能。
- **验证方式**: 使用已发表的 TF ChIP-seq 数据（如 ENCODE）进行交叉验证；比较 SNP 效应预测的准确性。
- **创新状态**: unverified

### 候选 2：从「高效应 SNP」到「TF 结合改变」的因果推断框架
- **名称**: Causal inference of TF binding disruption from deep learning predictions
- **来源局限/观察**: 本文预测了 SNP 对可及性的影响，但未验证 SNP 是否真的改变了 TF 结合。基序破坏/创建分析是间接证据。
- **核心假设**: 深度学习预测的「高效应 SNP」中，有一部分通过改变 TF 结合来发挥功能，且这些 SNP 可以通过等位基因特异性分析来识别。
- **增量**: 将深度学习预测与等位基因特异性 ATAC-seq（如杂合子供体）结合，构建「预测→验证」的闭环。
- **初步方法**: 在杂合子供体中检测高效应 SNP 的等位基因特异性可及性；使用 CRISPR 干扰验证 TF 结合。
- **验证方式**: 等位基因特异性 ATAC 信号与深度学习预测的一致性；CRISPR 实验的功能验证。
- **创新状态**: unverified

### 候选 3：跨组织的「变异-TF-靶基因」图谱构建
- **名称**: Cross-tissue variant-TF-target gene atlas for complex diseases
- **来源局限/观察**: 本文仅覆盖视网膜。许多复杂疾病的 SNP 在多个组织中具有功能，但细胞类型特异性的 TF 结合图谱缺乏跨组织比较。
- **核心假设**: 同一 SNP 在不同组织中的功能可能不同，取决于该组织中表达的 TF 和染色质状态。
- **增量**: 将本文的框架扩展到多个组织（如脑、心脏、免疫组织），构建跨组织的「变异-TF-靶基因」图谱。
- **初步方法**: 整合多个组织的单细胞多组学数据（如 Human Cell Atlas），训练跨组织的 BPNet 模型。
- **验证方式**: 跨组织 eQTL 数据验证；组织特异性疾病关联的富集分析。
- **创新状态**: unverified

### 候选 4：TF 协同结合的深度学习建模
- **名称**: Modeling TF cooperativity in variant effect prediction
- **来源局限/观察**: 本文的 BPNet 模型预测的是染色质可及性，而非 TF 结合本身。TF 协同结合（如 pioneer factor 与 partner TF）在基因调控中至关重要，但未在模型中得到显式建模。
- **核心假设**: 在 BPNet 中引入 TF 基序共现信息，可提高对 SNP 效应的预测精度，特别是对位于 TF 结合簇中的 SNP。
- **增量**: 在 BPNet 的贡献分析中，显式建模 TF 基序的协同效应（如 pairwise interaction terms）。
- **初步方法**: 使用本文的视网膜数据，对高效应 SNP 进行 TF 基序共现分析；扩展 BPNet 的贡献归因方法。
- **验证方式**: 与已知的 TF 协同结合数据（如 ChIP-seq 共结合）比较；实验验证预测的协同效应。
- **创新状态**: unverified

### 候选 5：深度学习预测与分子动力学模拟的整合
- **名称**: Integrating deep learning variant effect prediction with molecular dynamics simulations of TF-DNA binding
- **来源局限/观察**: 本文的深度学习模型预测 SNP 对可及性的影响，但无法提供原子层面的机制解释。对于位于 TF 结合位点内的 SNP，分子动力学（MD）模拟可以提供结合亲和力变化的直接证据。
- **核心假设**: 深度学习预测的「高效应 SNP」中，位于 TF 结合位点内的 SNP 会导致 TF-DNA 结合亲和力的显著变化，且这种变化可以通过 MD 模拟量化。
- **增量**: 将深度学习（序列→可及性）与 MD（序列→结合自由能）结合，形成「宏观可及性 + 微观结合亲和力」的多尺度预测框架。
- **初步方法**: 选择 23 个高效应 SNP 中位于 TF 基序内的 SNP，使用 MD 模拟（如 AMBER 或 GROMACS）计算 TF-DNA 结合自由能变化；与深度学习预测的效应量比较。
- **验证方式**: MD 模拟的结合自由能变化与深度学习预测的效应量相关性；实验验证（如表面等离子体共振或荧光各向异性）。
- **创新状态**: unverified