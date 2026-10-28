## 01 基本信息

- **标题**：Sequence-Based Prioritization of Promoter Regulatory Variants in Colorectal Cancer Using a DNA Foundation Model
- **作者**：Sripal Vajinepalli; Aashna Saraf; Sayane Shome
- **单位**：未提供
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（方法学/计算生物学）
- **领域**：癌症基因组学 × 非编码调控变异 × DNA foundation model
- **关键词**：结直肠癌（CRC）、启动子调控变异、Evo2、DNA foundation model、delta score、非编码变异优先级排序
- **DOI/ID**：10.64898/2026.05.25.727528
- **代码**：https://github.com/lolsripal/CRCRegCheck
- **数据**：GEO GSE39582（566例CRC肿瘤样本）、TCGA-COAD/READ体细胞突变、PCAWG非编码驱动目录
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「蛋白质-DNA互作（聚焦TF–DNA结合机制）× AI方法」方向中的**非编码变异功能预测**子方向。其核心创新在于使用DNA foundation model（Evo2）直接对启动子序列进行概率评分，以delta score作为调控破坏的代理指标，无需监督训练或预定义注释。与TF–DNA结合机制的直接关联在于：delta score高的变异被验证富集于TF结合位点和motif破坏位置，说明该方法的信号部分来源于对TF结合语法（regulatory grammar）的隐式编码。该方法可迁移至TF–DNA结合预测任务，作为无监督的序列扰动评分工具。

---

## 02 一句话总结

本文使用Evo2（自回归DNA foundation model）对CRC相关基因启动子区域（±1,024 bp）内的变异计算delta score（参考等位基因与替代等位基因的序列概率差），以无监督方式优先排序非编码调控变异，发现高影响变异富集于Wnt/p53/细胞周期通路、GWAS位点及TF结合位点，证明序列基础模型可规模化识别调控变异而不依赖注释或监督训练。

---

## 03 研究问题

- **具体问题**：如何在不依赖预定义注释（如ENCODE、Roadmap）或监督训练的情况下，对结直肠癌相关启动子区域内的非编码调控变异进行功能影响优先级排序？
- **为什么重要**：非编码调控变异对CRC易感性有重要贡献，但大多数非编码区域缺乏可靠注释，且调控效应具有上下文依赖性（context-dependent）。现有方法（如CADD、DeepSEA、保守性评分）要么依赖注释，要么无法捕捉上下文依赖的调控效应。
- **现有方法为何不足**：
  - 保守性评分（如PhastCons）仅反映进化约束，无法捕捉组织/上下文特异的调控效应；
  - CADD整合多种注释但依赖特征工程，对非编码区域的调控机制建模有限；
  - DeepSEA需要监督训练且依赖染色质特征标签，对缺乏注释的区域覆盖不足。
- **精确研究问题（Can...?）**：Can an autoregressive DNA foundation model (Evo2) trained solely on genomic sequences, without supervised fine-tuning or predefined regulatory annotations, produce delta scores that reliably prioritize promoter-associated regulatory variants in colorectal cancer?

---

## 04 背景与发展脉络

*注：以下脉络基于本文框架及引文，部分经外部核验，标注如下。*

| 阶段 | 代表性方法 | 优点 | 局限 | 本文主张的位置 |
|------|-----------|------|------|---------------|
| 保守性评分 | PhastCons, GERP++ | 计算简单，跨物种可比较 | 仅反映进化约束，无法捕捉上下文依赖的调控效应 | 作为baseline对比，显示Evo2捕捉了保守性之外的信号 |
| 整合注释方法 | CADD | 整合多源注释，全基因组可评分 | 依赖特征工程和注释质量，对非编码调控机制建模有限 | 作为baseline对比，Evo2与其中等相关（ρ=0.47） |
| 监督深度学习 | DeepSEA, Enformer | 直接从序列预测功能（染色质、表达） | 需要监督标签（如DNase、ChIP-seq），对缺乏注释区域覆盖不足 | 与DeepSEA相关性最高（ρ=0.61），作为收敛证据 |
| 无监督DNA foundation model | Evo2, Nucleotide Transformer | 无需监督标签，直接从序列学习调控语法和进化约束 | 输出为序列概率而非直接功能预测，需设计代理指标 | **本文位置**：使用Evo2 delta score作为无监督调控破坏代理指标 |

**本文主张的位置**：在「保守性 → 注释整合 → 监督深度学习 → 无监督基础模型」的演进脉络中，本文属于最后阶段——利用无监督DNA foundation model直接对序列扰动进行评分，避免了对注释和标签的依赖，同时通过TF结合位点富集验证表明其捕捉了调控语法信号。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 非编码变异功能解读困难 | CRC易感性相关非编码变异难以优先排序 | 调控效应具有上下文依赖性，大多数非编码区域缺乏可靠注释 | Abstract: "regulatory effects being context-dependent and most noncoding regions lack reliable genomic annotations" |
| 现有方法依赖注释或监督标签 | CADD依赖特征工程，DeepSEA需要染色质标签 | 注释覆盖不全，监督标签获取成本高 | Introduction: "these methods rely on sequence alignments or fixed annotations that miss context-dependent effects" |
| 保守性评分无法捕捉上下文依赖效应 | PhastCons与Evo2相关性弱（ρ=0.31） | 保守性仅反映跨物种约束，不反映组织/细胞类型特异的调控功能 | Results: "weak correlation with phastCons vertebrate conservation scores (ρ=0.31)" |
| 非编码变异效应量小 | delta score绝对值小（mean=0.018, SD=0.011） | 调控变异通常产生微小但生物学上有意义的效应 | Results: "consistent with expected effect sizes for regulatory variants, which typically exert subtle but biologically meaningful effects" |
| 启动子区域变异与TF结合破坏的关联难以规模化验证 | 需要实验验证每个候选变异 | 计算预测与实验验证之间存在鸿沟 | Discussion: "High-impact variants identified by this pipeline are direct candidates for experimental follow-up" |

---

## 06 核心思想

### 1) 表面方法
将CRC相关基因的启动子区域（±1,024 bp from TSS）内的变异映射到参考基因组（GRCh37/hg19），对每个变异生成参考和替代等位基因的序列，分别输入Evo2-40B模型获得序列概率，计算delta score（参考概率 - 替代概率），以delta score作为调控破坏的代理指标，通过分布阈值（75th percentile, delta > 0.020）识别高影响变异。

### 2) 核心洞察
Evo2作为自回归DNA foundation model，在训练过程中隐式学习了跨物种的调控语法（regulatory grammar），包括TF结合基序、启动子结构等序列特征。因此，**序列概率的变化（delta score）可以作为调控功能破坏的代理指标**——如果一个变异使序列在模型看来"不太可能"，说明它可能破坏了模型学到的调控模式（如TF结合位点）。这一洞察的关键在于：**无需任何监督标签或预定义注释，仅凭序列本身即可捕捉调控效应**，且该效应具有上下文依赖性（因为模型考虑的是整个启动子窗口的序列上下文）。

### 3) 可能的普适教训 [Analysis]
- **无监督基础模型可作为"序列语法"的通用探针**：Evo2的delta score本质上是在测"这个变异违反了模型学到的序列语法多少"。这一思路可迁移到TF–DNA结合预测——如果某个变异破坏了TF结合位点，Evo2的序列概率应该会下降。本文的TF结合位点富集结果（32.8%重叠）支持这一假设。
- **代理指标的设计比模型选择更重要**：本文没有微调Evo2，而是设计了一个巧妙的代理指标（delta score），将生成模型的输出转化为变异效应评分。这种"零样本"思路对缺乏标注数据的场景极具价值。
- **分布阈值而非绝对阈值**：由于调控变异效应量小，本文使用数据驱动的分布阈值（75th percentile）而非固定阈值，这避免了绝对阈值在不同数据集间不可迁移的问题。

---

## 07 方法总览

- **输入**：
  - 变异列表（VCF/manual/23andMe格式），标准化为chr:pos:ref:alt
  - 基因列表（来自CMS亚型差异表达分析）
  - 参考基因组（GRCh37/hg19）
- **输出**：
  - 每个变异的delta score
  - 高影响变异列表（delta > 0.020）
  - 高影响基因列表及通路富集结果
- **模块**：
  1. **数据预处理**：GEO GSE39582表达数据 → CMS亚型差异表达 → 候选基因集（~1,250基因）
  2. **启动子提取**：Ensembl REST API获取TSS → ±1,024 bp窗口 → 参考序列
  3. **Evo2评分**：NVIDIA ARC API → 参考/替代等位基因序列概率 → delta score
  4. **统计分析**：变异分类（启动子vs非启动子）、分布阈值设定、通路富集、GWAS位点富集、TF结合位点重叠分析
  5. **基准对比**：与CADD、DeepSEA、PhastCons的相关性分析
- **训练**：无监督（Evo2预训练模型，未微调）
- **反馈回路**：无（单次前向计算）
- **文字流程**：
  1. 从GSE39582获取CRC表达数据，按CMS亚型进行差异表达分析，合并得到候选基因集；
  2. 从TCGA-COAD/READ和PCAWG获取CRC相关变异，映射到候选基因启动子区域（±1,024 bp from TSS）；
  3. 对每个变异，提取参考和替代等位基因的启动子序列，分别输入Evo2-40B获得序列概率；
  4. 计算delta score = P(reference) - P(alternate)，作为调控破坏的代理指标；
  5. 以75th percentile（delta > 0.020）为阈值识别高影响变异；
  6. 对高影响变异进行通路富集、GWAS位点富集、TF结合位点重叠分析；
  7. 与CADD、DeepSEA、PhastCons进行相关性基准对比。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CMS亚型差异表达分析 | 识别CRC亚型特异的差异表达基因，构建候选基因集 | 聚焦于转录失调的基因，缩小启动子扫描范围 | 输入：GSE39582表达矩阵+临床注释；输出：~1,250个候选基因 | Methods: "Differential expression analysis was performed separately for each CMS Subtypes" | 预期影响：移除后候选基因集将失去亚型特异性，可能遗漏亚型特异的调控变异（预期效应，未实测） |
| 启动子区域提取（±1,024 bp） | 定义变异映射的基因组窗口 | 匹配Evo2输入窗口大小，覆盖核心启动子和近端调控元件 | 输入：基因列表+Ensembl注释；输出：启动子FASTA序列 | Methods: "A fixed genomic window of ±1,024 base pairs from the TSS" | 预期影响：窗口过小会遗漏远端调控元件，过大则引入噪声；敏感性分析显示±500至±2,000 bp结果一致（r=0.89-0.93） |
| Evo2-40B序列评分 | 计算参考/替代等位基因的序列概率 | 核心创新——利用无监督模型捕捉调控语法 | 输入：启动子序列（参考/替代）；输出：token-level概率 → delta score | Methods: "Each sequence was submitted to the model to obtain token-level probabilities" | 实测影响：移除后整个方法不成立；替代模型（如Nucleotide Transformer）需重新验证 |
| 负对照（null distribution） | 建立delta score的零分布 | 区分真实调控信号与序列组成效应 | 输入：随机非调控区变异+shuffled启动子；输出：null delta分布 | Results: "Random genomic variants falling outside regulatory regions yielded a median delta of 0.003" | 实测影响：无负对照则无法证明delta score的特异性；shuffled对照排除了序列组成混淆 |
| 分布阈值设定（75th percentile） | 识别高影响变异 | 调控变异效应量小，需数据驱动阈值 | 输入：所有启动子变异delta score分布；输出：delta > 0.020的287个变异 | Results: "The 75th percentile of the promoter variant delta score distribution was 0.020" | 预期影响：阈值过严会遗漏真阳性，过松会增加假阳性；TF motif破坏频率在阈值以上显著增加支持该阈值 |
| 基准对比（CADD/DeepSEA/PhastCons） | 验证delta score与现有工具的一致性 | 建立方法的有效性 | 输入：同一变异集的各工具评分；输出：Spearman相关系数 | Results: "moderate correlation with CADD (ρ=0.47), weak with phastCons (ρ=0.31), strongest with DeepSEA (ρ=0.61)" | 预期影响：移除后无法定位方法在现有工具谱系中的位置；中等相关性表明delta score捕捉了部分独立信号 |

---

## 09 关键公式符号

**Delta Score（核心公式）**：

$$\Delta = \frac{1}{L} \sum_{i=1}^{L} \left[ \log P_{\text{Evo2}}(x_i^{\text{ref}} | x_{<i}^{\text{ref}}) - \log P_{\text{Evo2}}(x_i^{\text{alt}} | x_{<i}^{\text{alt}}) \right]$$

其中：
- $L$ = 启动子序列长度（2,048 bp，即±1,024 bp窗口）
- $x^{\text{ref}}$ = 参考等位基因的启动子序列
- $x^{\text{alt}}$ = 替代等位基因的启动子序列（仅变异位点不同）
- $P_{\text{Evo2}}(x_i | x_{<i})$ = Evo2模型在位置$i$给定前文$i-1$个token的条件概率
- 实际实现中，delta score为参考与替代序列的**平均token概率差**（文中描述为"difference in sequence probability between reference and alternate alleles"）

**高影响阈值**：
$$\text{High-impact} = \{\text{variant} : \Delta > Q_{75}(\Delta_{\text{all promoter variants}})\}$$
其中$Q_{75}$为所有启动子变异delta score分布的75th percentile，文中值为0.020。

**富集分析**：
- 通路富集：超几何检验（Hypergeometric test），FDR校正（Benjamini-Hochberg）
- GWAS富集：Fisher精确检验
- 背景基因集：~19,000个人类蛋白编码基因（用于排除输入基因选择带来的循环性）

*注：文中未给出完整公式推导，以上为基于方法描述的合理重构。*

---

## 10 实验设计与证据链

### 数据集与资源
| 资源 | 规模/描述 | 用途 |
|------|-----------|------|
| GEO GSE39582 | 566例原发CRC肿瘤样本，含生存、分期、MSI、CIMP、KRAS/BRAF/TP53突变状态 | 差异表达分析 → 候选基因集 |
| TCGA-COAD/READ | 体细胞突变调用 | 变异来源 |
| PCAWG非编码驱动目录 | 非编码驱动变异 | 变异来源 |
| 参考基因组 | GRCh37/hg19 | 序列提取 |
| Evo2-40B | NVIDIA ARC Biology API | 序列概率计算 |
| 负对照1 | 1,250个非调控区随机变异（匹配等位基因频率谱） | null分布 |
| 负对照2 | 启动子序列的dinucleotide-shuffled版本 | 排除序列组成效应 |
| 背景基因集 | ~19,000个人类蛋白编码基因 | 通路富集背景 |

### 评测指标
- Delta score分布比较（启动子vs非启动子变异）
- 高影响变异（delta > 0.020）的通路富集p值
- 与已知癌症基因的重叠倍数富集（2.3-fold, p=8.7×10⁻⁶）
- 与CADD/DeepSEA/PhastCons的Spearman相关性
- TF结合位点重叠率（32.8%）和motif破坏率（21.3%）

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|-------------------|------|
| 启动子vs非启动子变异delta score比较 | Evo2能区分调控区域与非调控区域的变异效应 | 启动子变异 vs 非调控区随机变异 | 启动子变异delta score显著更高（median 0.015 vs 0.002, p<1×10⁻⁵） | Evo2对调控区域的变异更敏感 | 不能证明所有高delta score变异都有功能效应 | Results, Figure 3 |
| 负对照：shuffled启动子 | delta score反映真实调控结构而非序列组成 | 真实启动子变异 vs dinucleotide-shuffled启动子变异 | shuffled序列delta score显著更低（median 0.004） | delta score捕捉了learned regulatory structure | 不能排除其他序列特征（如CpG密度）的贡献 | Results, Supplementary Table S1 |
| 高影响变异通路富集 | 高delta score变异富集于CRC相关通路 | 高影响变异基因 vs 全部人类基因背景 | Wnt (p=3.2×10⁻⁶), p53 (p=7.4×10⁻⁵), cell cycle (p=1.4×10⁻⁴) | 高影响变异具有生物学相关性 | 富集不等于因果性 | Results, Supplementary Table S2 |
| 已知癌症基因重叠 | 高影响变异富集于已知癌症基因 | 198个高影响基因 vs 已知癌症基因列表 | 72/198重叠，2.3-fold富集，p=8.7×10⁻⁶ | 方法能识别已知癌症相关基因 | 不能证明新基因的致癌性 | Results |
| TF结合位点重叠 | 高影响变异破坏TF结合 | 高影响变异 vs TF结合位点注释 | 32.8%重叠TFBS，21.3%破坏motif | 变异可能通过破坏TF结合发挥功能 | 未做实验验证；TFBS注释可能不完整 | Results, Supplementary Table S3 |
| 与现有工具基准对比 | delta score与现有工具一致但互补 | 同一变异集的Evo2 delta vs CADD/DeepSEA/PhastCons | DeepSEA相关性最高（ρ=0.61），CADD中等（ρ=0.47），PhastCons弱（ρ=0.31） | delta score捕捉了部分独立于保守性的信号 | 相关性不等于因果；各工具评分体系不同 | Results, Supplementary Table S4 |
| 变异类型分层 | indel比SNP效应更大 | SNP vs indel的delta score | indel mean delta=0.022 vs SNP=0.017；29% vs 22%高影响 | indel对序列结构破坏更大 | 样本量可能不均衡 | Results, Supplementary Table S5 |
| 窗口大小敏感性 | 结果对启动子窗口大小不敏感 | ±500 vs ±1,024 vs ±2,000 bp | 相关性r=0.89-0.93 | 结果稳健 | 未测试更大窗口（如±5 kb） | Methods |

---

## 11 结论正确解读

- **任务范围**：本文仅针对**启动子区域**（±1,024 bp from TSS）的变异，不涵盖增强子、绝缘子、LCR等其他调控元件。结论不能外推到非启动子调控区域。
- **Oracle/真值输入**：变异来源为TCGA-COAD/READ体细胞突变和PCAWG非编码驱动目录，属于**已观测到的体细胞变异**，非从头预测。delta score是计算预测，无实验验证（如报告基因、CRISPR）。
- **端到端状态**：**非端到端**。流程包含多个独立步骤（差异表达→基因选择→启动子映射→Evo2评分→阈值→富集），每步都有独立误差累积。Evo2评分本身是"零样本"推理，未针对CRC或调控变异进行微调。
- **算力成本**：未报告。Evo2-40B通过API访问，本地计算成本未披露。40B参数模型的推理成本不可忽略，但API封装降低了使用门槛。
- **历史数据依赖**：依赖GEO GSE39582（2013年前后数据）和TCGA/PCAWG的变异调用，这些数据集的覆盖度和变异检测方法会影响结果。
- **模型依赖**：结果完全依赖Evo2-40B的预训练质量。Evo2的训练数据以多物种基因组为主，对人类调控语法的覆盖程度未在文中量化。
- **最难情形**：对于位于启动子边缘（接近±1,024 bp边界）的变异、位于GC-rich区域的变异、以及影响远距离调控（如3D基因组结构）的变异，delta score的可靠性未验证。
- **群体/领域边界**：仅限CRC；仅限启动子区域；仅限体细胞变异（非胚系）；仅限SNP和indel（未覆盖结构变异）。
- **不确定性**：delta score的绝对值小（mean=0.018），阈值（0.020）是数据驱动的，但未报告置信区间或bootstrap稳定性。富集分析的p值未做多重检验校正的敏感性分析。

**有边界的复述**：本文证明，在CRC相关基因的启动子区域内，Evo2的delta score（参考与替代等位基因的序列概率差）能优先排序体细胞非编码变异，高delta score变异富集于Wnt/p53/细胞周期通路、GWAS位点和TF结合位点。该结论仅限于启动子区域、体细胞变异、CRC场景，且未经实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 仅限启动子区域 | 不涵盖增强子、绝缘子等远端调控元件 | "provides a natural foundation for extending the framework to distal elements as annotation quality improves" | Discussion |
| 计算预测非实验验证 | delta score是序列概率差，非直接功能证据 | "Reporter assays can test whether the alternate allele reduces promoter activity, and CRISPR-based perturbation studies can interrogate the functional consequences" | Discussion |
| 依赖公开变异数据 | 使用TCGA/PCAWG的已观测变异，非患者来源WGS | "extending this to large-scale patient-derived whole-genome sequencing cohorts represents an important direction for future validation" | Discussion |
| 未整合表观基因组数据 | 未使用ATAC-seq、ChIP-seq等染色质状态信息 | "Integrating chromatin accessibility (ATAC-seq) and transcription factor binding (ChIP-seq) data would provide orthogonal evidence" | Discussion |
| 单模态模型 | 仅使用序列信息，未结合表达、甲基化等多模态数据 | "Combining sequence scores with epigenomic and expression data in a multi-modal model along the lines of Enformer" | Discussion |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 基因选择依赖CMS亚型差异表达 | 差异表达基因未必是调控变异的功能靶点；启动子变异可能影响未差异表达的基因 | 基因选择偏差可能引入循环论证——先选差异表达基因，再发现这些基因富集于相关通路 | 使用全部~19,000个基因的启动子作为背景，而非仅CMS差异表达基因 | Methods: 基因集来自差异表达分析 |
| delta score与DeepSEA相关性最高（ρ=0.61） | 可能反映两者捕捉了相似的序列特征（如motif破坏），而非独立验证 | 如果delta score只是DeepSEA的近似，则无增量价值 | 比较delta score与DeepSEA在独立数据集上的预测一致性；检查高delta score但低DeepSEA评分的变异是否仍有功能 | Results, Supplementary Table S4 |
| TF结合位点重叠率32.8% | 未说明TFBS注释来源（ENCODE? JASPAR?）、细胞类型匹配性；CRC相关TFBS可能与其他组织不同 | TFBS重叠是功能相关性的关键证据，注释不匹配会高估或低估 | 使用CRC相关细胞系的TFBS数据（如Caco-2、SW480 ChIP-seq）重新分析 | Results, Supplementary Table S3 |
| 负对照仅用非调控区变异 | 非调控区变异可能位于其他功能元件（如lncRNA、绝缘子），导致null分布被污染 | 负对照不纯会低估delta score的区分能力 | 使用更严格的负对照：同启动子区域的同义突变或已知中性变异 | Results, Supplementary Table S1 |
| 未报告多重检验校正 | 通路富集涉及多个通路同时检验，未说明FDR校正的具体方法 | 可能产生假阳性通路 | 报告Benjamini-Hochberg FDR的具体q值 | Results, Supplementary Table S2 |
| 窗口大小敏感性仅测试±500至±2,000 bp | 未测试更大窗口（如±5 kb或±10 kb），而启动子-增强子互作可跨越更大距离 | 窗口边界效应可能遗漏或引入噪声 | 在更大窗口范围（±5 kb, ±10 kb）重复分析 | Methods: "Sensitivity analyses confirmed consistent results across window sizes of ±500 to ±2,000 bp" |
| 未报告Evo2 API的版本和超参数 | 模型版本、温度、采样参数等会影响概率输出 | 可复现性存疑 | 明确报告Evo2模型版本、API调用参数、随机种子 | Methods: 仅提及"accessed via the NVIDIA ARC Biology API" |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **零样本delta score作为TF–DNA结合破坏的代理指标**：本文最核心的可迁移方法。对于TF–DNA互作研究，可以直接将TF结合位点内的变异输入Evo2（或其他DNA foundation model），计算delta score作为结合亲和力变化的预测。相比传统的position weight matrix (PWM) 或基于结构的预测，该方法考虑了更长的序列上下文。**迁移路径**：对已知TF（如TP53、CTCF）的结合位点变异，计算delta score并与实验测定的结合亲和力变化（如SELEX、HT-SELEX数据）做相关性验证。

2. **分布阈值而非绝对阈值的变异筛选策略**：由于调控变异效应量小，本文使用75th percentile作为阈值。这一策略可迁移到TF–DNA结合预测中——当预测分数分布偏移时，使用数据驱动的分位数阈值比固定阈值更稳健。**迁移路径**：在TF结合位点预测中，对每个TF单独计算其结合位点变异delta score的分位数阈值。

3. **负对照设计的两层策略**：本文使用了两层负对照——非调控区变异（排除区域特异性）和dinucleotide-shuffled启动子（排除序列组成效应）。这种设计可迁移到TF–DNA结合预测的验证中。**迁移路径**：在验证TF结合预测模型时，使用shuffled motif序列作为负对照，排除GC含量和k-mer组成的混淆。

4. **多工具基准对比的框架**：本文与CADD、DeepSEA、PhastCons的对比框架可迁移。对于TF–DNA结合预测，可以对比delta score与PWM score、DeepBind、DeepSEA的TF binding预测、以及基于结构的预测（如Rosetta、FoldX）的相关性。**迁移路径**：建立统一的变异集，计算各工具评分，用Spearman相关性和AUC评估增量价值。

5. **启动子窗口大小敏感性分析**：本文测试了±500至±2,000 bp窗口的一致性（r=0.89-0.93）。这一分析思路可迁移到TF–DNA结合预测中——测试不同上下文窗口大小对预测稳定性的影响。**迁移路径**：在预测TF结合位点变异效应时，测试±100 bp、±500 bp、±1 kb窗口的预测一致性。

6. **循环论证风险的意识**：本文的基因选择（差异表达基因）可能引入偏差。在TF–DNA互作研究中，如果从已知TF靶基因出发验证预测，也会面临类似问题。**迁移路径**：使用全基因组背景而非TF靶基因集作为验证背景。

---

## 15 与已有知识连接

- **Evo2模型**：本文使用的Evo2是Evo系列DNA foundation model的后续版本（Brixi et al., 2025, 未在文中引用但为已知工作）。Evo2-40B是40B参数的因果Transformer，训练数据覆盖多物种基因组。与本文相关的已知工作包括Evo2在变异效应预测上的应用（如cryptic splice site检测）。本文将其扩展到启动子调控变异优先排序，属于该模型的新应用场景。

- **DNA foundation model家族**：本文与Nucleotide Transformer（Dalla-Torre et al., 2023）、DNABERT-2（Zhou et al., 2023）、Genomic Transformer等模型同属一个技术路线。与这些模型相比，Evo2的优势在于生成式训练（autoregressive），可以直接计算序列概率差，而BERT类模型需要设计额外的评分头。本文的delta score思路可迁移到其他生成式DNA模型。

- **非编码变异解读工具**：本文与CADD（Rentzsch et al., 2019）、DeepSEA（Zhou & Troyanskaya, 2015）、PrimateAI等工具形成对比。这些工具要么依赖注释整合（CADD），要么需要监督训练（DeepSEA）。本文的零样本方法填补了「无注释、无监督」场景的空白。在TF–DNA互作领域，这些工具通常无法直接预测TF结合破坏，而本文的delta score天然适合这一任务。

- **TF–DNA结合预测**：本文的TF结合位点富集分析（32.8%重叠）与已知的TF motif数据库（JASPAR、TRANSFAC）和预测工具（PWM、DeepBind、DeepSEA的TF任务）形成连接。delta score与PWM score的相关性未在文中报告，但这是一个值得探索的方向——如果delta score与PWM高度相关，则说明Evo2主要捕捉了motif保守性；如果低相关，则说明捕捉了更复杂的上下文效应。

- **CRC调控基因组学**：本文与CRC的调控基因组学研究（如ENCODE的CRC细胞系数据、TCGA的调控变异分析）相关。已知的CRC风险位点（如rs6983267位于TCF7L2增强子区域）是TF–DNA互作在CRC中的经典案例。本文识别的Wnt通路富集与此一致，但未具体讨论已知风险位点。

- **启动子结构研究**：本文的±1,024 bp窗口选择与启动子结构研究一致——核心启动子（~±50 bp）、近端启动子（~±500 bp）、远端启动子（~±2 kb）的层级结构。Evo2的2,048 bp上下文窗口恰好覆盖近端启动子区域，这可能是作者选择该窗口的原因。

---

## 16 研究想法

**Agent 生成的研究候选**

### 候选1：基于Evo2 delta score的TF–DNA结合亲和力变化预测器
- **名称**：Evo2-Delta-Bind：零样本TF结合位点变异效应预测
- **来源局限/观察**：本文验证了delta score在启动子变异优先排序中的有效性，但未直接验证delta score与TF结合亲和力变化的相关性。TF–DNA互作领域需要无监督的变异效应预测工具。
- **核心假设**：Evo2 delta score与实验测定的TF结合亲和力变化（ΔΔG或IC50变化）显著相关，且优于PWM-based预测。
- **初步方法**：收集HT-SELEX、SELEX、Protein Binding Microarray数据中的TF结合位点变异-亲和力变化对；对每个变异计算Evo2 delta score（使用与本文相同的±1,024 bp窗口）；与PWM score变化、DeepBind预测对比；评估Spearman相关性和AUC。
- **验证方式**：独立测试集（如不同TF家族、不同细胞类型）；与现有工具（DeepSEA、DeepBind）的基准对比。
- **创新状态**：unverified（本文未做此验证，但方法直接可迁移）

### 候选2：启动子变异delta score与染色质状态的多模态整合
- **名称**：Multi-modal promoter variant prioritization：整合Evo2 delta score与ATAC-seq/ChIP-seq
- **来源局限/观察**：作者明确提到"Integrating chromatin accessibility (ATAC-seq) and transcription factor binding (ChIP-seq) data would provide orthogonal evidence"，但未实施。
- **核心假设**：在启动子变异优先排序中，整合序列概率（Evo2 delta score）与染色质状态（ATAC-seq峰、TF ChIP-seq峰）比单一模态更准确。
- **初步方法**：使用CRC细胞系（如Caco-2、SW480、HCT116）的ATAC-seq和TF ChIP-seq数据；对启动子变异标注染色质状态特征；训练轻量级模型（如logistic regression或gradient boosting）整合Evo2 delta score与染色质特征；与纯序列方法对比。
- **验证方式**：交叉验证；独立CRC数据集；与实验验证（报告基因）的相关性。
- **创新状态**：unverified（作者提出但未实施）

### 候选3：TF结合基序破坏的delta score分解分析
- **名称**：Decomposing delta score：区分核心基序破坏与上下文效应
- **来源局限/观察**：本文发现21.3%的高影响变异破坏TF motif，但78.7%未破坏motif的变异仍有高delta score。这些"非基序"变异可能通过改变基序侧翼序列、核小体定位或启动子结构发挥作用。
- **核心假设**：Evo2 delta score可以分解为基序核心效应和上下文效应两部分，后者与TF协同结合、核小体排斥等机制相关。
- **初步方法**：对高delta score变异分类：位于TF motif核心 vs motif侧翼 vs 非motif区域；比较三类变异的delta score分布；对非motif变异进行motif扫描（FIMO），检查是否破坏了其他TF的结合位点；分析侧翼序列特征（GC含量、k-mer组成）。
- **验证方式**：与已知的TF协同结合数据（如ChIA-PET、HiChIP）交叉验证；电泳迁移率实验（EMSA）验证代表性变异。
- **创新状态**：unverified（本文数据支持但未分析）

### 候选4：跨癌症类型的启动子变异优先排序泛化性测试
- **名称**：Cross-cancer generalization of Evo2 delta score prioritization
- **来源局限/观察**：本文仅针对CRC。Evo2的训练数据覆盖多物种基因组，理论上其序列语法学习具有泛化性，但未验证。
- **核心假设**：Evo2 delta score在乳腺癌、肺癌等其他癌症类型的启动子变异优先排序中同样有效，且跨癌症类型的top-ranked变异富集于共同的调控通路。
- **初步方法**：收集TCGA-BRCA、TCGA-LUAD等癌症的启动子变异；使用与本文相同的流程计算delta score；评估高delta score变异在GWAS位点、TFBS、已知癌症基因中的富集；比较跨癌症类型的通路富集模式。
- **验证方式**：与CRC结果对比；独立验证集。
- **创新状态**：unverified（本文未涉及）

### 候选5：Evo2 delta score与MD模拟的互补验证
- **名称**：Bridging sequence probability and structural dynamics：Evo2 delta score与TF–DNA MD模拟的关联
- **来源局限/观察**：本文的delta score是纯序列层面的预测，未涉及结构机制。TF–DNA互作领域常用MD模拟研究突变对结合自由能的影响，但MD计算成本高，无法全基因组扫描。
- **核心假设**：Evo2 delta score高的变异在MD模拟中表现出更大的结合自由能变化或构象扰动，两者互补——delta score用于全基因组筛选，MD用于候选变异的机制验证。
- **初步方法**：选取本文识别的top-ranked变异（如RNF43、AXIN2启动子变异）；对代表性变异进行TF–DNA复合物的MD模拟（如使用GROMACS或AMBER）；计算结合自由能变化（MM-PBSA或FEP）；与delta score进行相关性分析。
- **验证方式**：MD结果与delta score的一致性；实验数据（如报告基因）验证。
- **创新状态**：unverified（本文未涉及结构模拟，但为自然延伸）