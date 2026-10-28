## 01 基本信息

- **标题**：The amniote-conserved DNA-binding domain of CGGBP1 restricts cytosine methylation of transcription factor binding sites in proximal promoters to regulate gene expression
- **作者**：Ishani Morbia; Praveen Kumar; Aditi Lakshmi Satish; Akanksha Mudgal; Subhamoy Datta; Umashankar Singh
- **单位**：Indian Institute of Technology Gandhinagar（基于通讯作者信息推断，原文未明确列出单位列表）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2024
- **论文类型**：实验生物学研究（wet-lab 为主，含生物信息学分析）
- **领域**：表观遗传学、基因表达调控、蛋白质-DNA 互作
- **关键词**：CGGBP1、DNA-binding domain、cytosine methylation、transcription factor binding sites、proximal promoters、amniote evolution
- **DOI/arXiv 号**：10.1101/2024.06.20.599840
- **代码**：未提供
- **数据**：MeDIP-seq、ChIP-seq、microarray 数据（GEO  accession 未在文中明确给出）
- **阅读日期**：2026-05-13（按当前日期）
- **在该方向中的位置**：本文聚焦于一个非经典 DNA 结合蛋白 CGGBP1 的 N 端 DNA 结合结构域（DBD）如何通过限制近端启动子区转录因子结合位点（TFBS）的胞嘧啶甲基化来调控基因表达。与「TF–DNA 结合机制 × AI/物理模拟」课题方向的关联在于：①提供了 DBD 结构域功能解析的实验范式（截短突变体 + 全基因组甲基化/结合谱）；②揭示了 DNA 结合蛋白通过空间位阻保护 TFBS 免于甲基化的机制，可作为结构模拟/分子动力学研究的生物学假设来源；③其进化分析（跨物种保守性）为 AI 模型训练提供序列特征标签。

---

## 02 一句话总结

本文通过表达 CGGBP1 的 N 端（含 DBD）和 C 端截短突变体，结合 MeDIP-seq、ChIP-seq 和 microarray，证明 CGGBP1 的 N 端 DBD 通过直接结合 GC-rich TFBS 并限制其胞嘧啶甲基化，从而维持这些位点的可及性并介导基因抑制，且该功能在羊膜动物中保守。

---

## 03 研究问题

- **具体问题**：CGGBP1 仅含一个已知的 DNA 结合结构域（N 端 Znf BED），其 C 端无明确结构域。CGGBP1 如何通过其简单的结构实现多种功能（基因组完整性、CTCF 占位调控、基因表达调控）？特别是，其 DNA 结合结构域在胞嘧啶甲基化调控和基因表达中的具体贡献是什么？
- **为什么重要**：CGGBP1 是 GC-rich DNA 结合蛋白，参与 CTCF 占位、转座子沉默、端粒维持等关键过程。理解其 DBD 的功能有助于阐明 DNA 结合蛋白如何通过保护 TFBS 免于甲基化来塑造调控景观，这对转录因子结合机制研究具有普适意义。
- **现有方法不足**：此前研究主要依赖 CGGBP1 全长的敲低/过表达，无法区分 N 端 DBD 与 C 端的功能贡献；且缺乏对 TFBS 甲基化保护的直接证据。
- **精确研究问题**：Can the N-terminal DNA-binding domain of CGGBP1 alone restrict cytosine methylation at GC-rich transcription factor binding sites in proximal promoters, and is this function conserved across amniotes?

---

## 04 背景与发展脉络

*（标注：以下脉络为「经外部核验」+「仅本文框架」混合，具体标注于各阶段）*

1. **CGGBP1 的发现与初步表征**（经外部核验）：CGGBP1 最初被鉴定为结合 CGG 重复序列的蛋白（Singh and Westermark, 2015）。早期研究确认其结合 GC-rich DNA，并参与多种基因组功能。
2. **CGGBP1 与 CTCF/甲基化的关联**（经外部核验）：后续研究发现 CGGBP1 影响 CTCF 占位和胞嘧啶甲基化（Patel et al., 2019, 2020）。但机制不清——是直接结合保护，还是间接通过调控甲基化酶表达？
3. **结构域功能解析的缺失**（仅本文框架）：本文指出，此前无研究系统比较 N 端 DBD 与 C 端的功能差异。本文首次使用截短突变体进行全基因组甲基化和表达分析。
4. **进化视角的引入**（仅本文框架）：本文通过跨物种启动子序列分析，将 CGGBP1 的甲基化保护功能与羊膜动物进化联系起来，提出「DBD 保守性 → TFBS 保留 → 基因调控」的进化叙事。
5. **本文主张的位置**：在「DNA 结合蛋白通过空间位阻保护 TFBS 免于甲基化」这一机制假设中，本文提供了 CGGBP1 作为案例的直接实验证据，并首次将这一机制与羊膜动物进化联系起来。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| CGGBP1 结构简单但功能多样 | 仅含一个 DBD 和低复杂度 C 端，却参与甲基化、CTCF、端粒、转座子等多过程 | 作者认为 DBD 负责靶向，C 端负责效应（蛋白互作/招募），但此前未验证 | Introduction 节；Results 节 1 |
| DBD 缺失导致核定位下降 | C 端截短体（无 DBD）在核外分布增加 | 作者推测 DNA 结合/染色质掺入是核滞留的必要条件 | Results 图 1B-C；Fig S1A |
| DBD 缺失导致全局甲基化上升 | C 端表达细胞中 MeDIP 信号整体升高 | 作者认为 DBD 直接结合 DNA 并空间阻碍甲基化酶接近 | Results 图 1D-F；Fig S2-S4 |
| TFBS 甲基化保护具有位点特异性 | 仅 GC-rich TFBS 被保护，非随机 | 作者认为 CGGBP1 的 GC-rich 结合偏好决定了靶位点 | Results 图 2A-B；Fig S8 |
| 进化保守性功能验证困难 | 跨物种启动子序列分析受限于基因组组装质量 | 作者仅用代表性物种，未覆盖全部羊膜动物 | Results 图 4；Methods 节 |

---

## 06 核心思想

1. **表面方法**：构建 CGGBP1 的 N 端（aa1-90，含 DBD）和 C 端（aa79-167，无 DBD）截短突变体，在敲低内源 CGGBP1 的 HEK293T 细胞中过表达，然后进行 MeDIP-seq（甲基化）、ChIP-seq（结合）、microarray（表达）和跨物种启动子序列分析。

2. **核心洞察**：CGGBP1 的 N 端 DBD 不仅负责 DNA 结合，还通过空间位阻直接保护 GC-rich TFBS 免于胞嘧啶甲基化。这种保护是位点特异性的（GC-rich、特定 TFBS），且与基因抑制相关。C 端则可能负责效应功能（如招募共抑制因子），但本身不结合 DNA。进化分析表明，这一机制在羊膜动物中保守，且与启动子区 GC 含量演化相关。

3. **可能的普适教训** [Analysis]：
   - 对于「DNA 结合蛋白如何调控甲基化」这一问题，空间位阻（steric protection）是一种常被忽视的简单机制，值得在结构模拟/MD 研究中显式建模。
   - 截短突变体 + 全基因组读出的组合是解析多结构域蛋白功能的高效策略，可迁移到其他 TF 的功能域解析。
   - 跨物种序列分析可作为「功能保守性」的间接证据，但需注意与直接实验证据的区分。

---

## 07 方法总览

- **输入**：HEK293T 细胞（敲低内源 CGGBP1 + 过表达 N 端/C 端/全长）；基因组 DNA（MeDIP）；染色质（ChIP）；RNA（microarray）；跨物种启动子序列（36 种羊膜动物）。
- **输出**：全基因组甲基化谱（MeDIP-seq）、CGGBP1 结合谱（ChIP-seq）、基因表达谱（microarray）、TFBS 保守性/GC 含量分析。
- **模块**：
  1. 截短突变体构建（N-term aa1-90；C-term aa79-167；全长 aa1-167）
  2. 慢病毒 shRNA 敲低 + 过表达
  3. MeDIP-seq（5-mC 抗体富集）
  4. ChIP-seq（抗 FLAG 标签）
  5. Microarray（Agilent Human GXP 8x60k）
  6. 跨物种启动子序列分析（36 种，含哺乳类、鸟类、爬行类）
  7. 系统发育树构建（PhyML）
- **训练**：不适用（无监督/无训练模型）
- **工具**：fastp、bowtie2、MACS2、deeptools、RepeatMasker、FIMO（MEME Suite）、RStudio、GraphPad Prism、PhyML、FigTree
- **反馈回路**：无显式反馈回路；实验设计为「敲低 + 回补截短体」的比较逻辑
- **假设**：① N 端 DBD 是 DNA 结合所必需；② 甲基化变化反映 CGGBP1 直接保护而非间接酶调控；③ 跨物种启动子序列保守性可反映功能保守性

**文字流程**：
1. 构建 N 端/C 端/全长 CGGBP1 表达载体（FLAG-GFP 标签）
2. 在 HEK293T 中用 shRNA 敲低内源 CGGBP1，再分别过表达三种形式
3. 收集细胞，分别进行 MeDIP-seq、ChIP-seq（抗 FLAG）、microarray
4. 对 MeDIP-seq 数据：call peaks、计算差异甲基化区域、分析 GC 含量/G/C-skew
5. 对 ChIP-seq 数据：call peaks、与甲基化数据整合、分析 TFBS 富集
6. 对 microarray 数据：差异表达分析、与甲基化/TFBS 数据关联
7. 跨物种启动子序列提取、TFBS 扫描、GC 含量分析、系统发育比较

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 截短突变体构建 | 分离 N 端 DBD 与 C 端功能 | CGGBP1 结构简单但功能多，需定位功能域 | 输入：CGGBP1 cDNA；输出：N-term/C-term/FL 表达载体 | Results 图 1A；Methods 节 | 无法区分 DBD 与 C 端贡献（预期影响） |
| shRNA 敲低 + 回补 | 在无内源背景条件下测试截短体功能 | 避免内源 CGGBP1 干扰 | 输入：shRNA + 表达载体；输出：敲低/回补细胞系 | Results 图 1A；Fig S1C | 无法排除内源背景（预期影响） |
| MeDIP-seq | 全基因组甲基化谱 | 检测 DBD 缺失对甲基化的全局影响 | 输入：基因组 DNA；输出：甲基化峰/差异区域 | Results 图 1D-F；Fig S2-S4 | 无法检测非 CpG 甲基化（已知局限） |
| ChIP-seq（抗 FLAG） | 检测 N 端/C 端/全长的基因组结合位点 | 验证 DBD 是否直接结合 TFBS | 输入：交联染色质；输出：结合峰 | Results 图 5A-B；Methods 节 | 无法区分直接/间接结合（预期影响） |
| Microarray | 基因表达谱 | 关联甲基化变化与表达变化 | 输入：RNA；输出：差异表达基因 | Results 图 3A-B；Fig S11-S12 | 无法检测非编码 RNA（已知局限） |
| 跨物种启动子分析 | 评估 TFBS 保守性与 GC 含量 | 验证进化保守性 | 输入：36 种羊膜动物启动子；输出：TFBS 保守性/GC 含量 | Results 图 4；Fig S14 | 受基因组组装质量影响（已知局限） |
| 系统发育树 | 重建 CGGBP1 进化史 | 理解 DBD 保守性 | 输入：CGGBP1 序列；输出：ML 树 | Results 图 2C-D；Fig S9-S10 | 无法推断祖先序列（预期影响） |

---

## 09 关键公式符号

本文为实验生物学论文，无核心数学模型或公式。以下为分析中隐含的统计/计算概念：

- **Spearman 秩相关系数**：用于评估 TFBS GC 含量与甲基化变化的相关性（Results 图 2A-B）。符号：r_s。用途：非参数相关性检验。
- **配对 t 检验**：用于比较 F-len 与 N-term/C-term 的 TFBS 甲基化差异（Results 图 S8）。符号：t。用途：配对样本均值差异检验。
- **Fisher 精确检验**：用于评估 CpG/TG 二核苷酸频率差异的显著性（Results 图 4D-F）。用途：2×2 列联表独立性检验。
- **Phred 质量分数**：测序数据质控（fastp 默认参数）。符号：Q。用途：碱基质量评估。
- **峰 calling 统计**：MACS2 默认参数，未给出具体公式。

---

## 10 实验设计与证据链

**数据集/群体**：
- 细胞系：HEK293T（人胚肾上皮细胞）
- 样本数：3 种条件（N-term、C-term、FL），每种 3 个生物学重复（microarray）
- MeDIP-seq：N-term、C-term、FL 各 1 个样本（未明确重复数）
- ChIP-seq：N-term、C-term、FL 各 1 个样本（未明确重复数）
- 跨物种启动子：36 种羊膜动物（含哺乳类、鸟类、爬行类）

**指标**：
- MeDIP-seq：峰数量、差异甲基化区域、GC 含量、G/C-skew
- ChIP-seq：峰数量、TFBS 富集
- Microarray：差异表达基因数、表达变化倍数
- 进化分析：TFBS 保守性、CpG/TG 二核苷酸频率

**基线/对照**：
- 内源 CGGBP1 敲低 + 空载体（未明确说明，推测为对照）
- F-len（全长 CGGBP1）作为功能对照
- 随机启动子集作为 null set（图 3D）

**预算/资源**：未提供

**骨干/仪器**：Illumina HiSeq 2500（MeDIP-seq）、Illumina NovaSeq 6000（ChIP-seq）、Agilent 扫描仪（microarray）

**oracle 输入**：不适用（无监督分析）

**评测协议**：未提供（预印本，无同行评审）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| 核定位分析 | DBD 缺失导致核滞留下降 | N-term vs C-term vs FL 的免疫荧光 | C-term 核外分布增加 | DBD 对核滞留必要 | 不能证明 DBD 单独足以核滞留 | Results 图 1B-C |
| 核质分离 | 同上 | 同上 | C-term 在胞质中富集 | 同上 | 同上 | Fig S1A |
| MeDIP-seq 全局比较 | DBD 缺失导致全局甲基化上升 | C-term vs FL 的 MeDIP 信号分布 | C-term 中低-中甲基化信号频率升高 | DBD 限制全局甲基化 | 不能区分直接/间接机制 | Results 图 1D-F |
| TFBS GC 含量分析 | GC-rich TFBS 是甲基化保护靶点 | F-len/C-term 甲基化比 vs GC 含量 | 负相关（r_s = -0.56） | GC-rich TFBS 被优先保护 | 不能证明因果关系 | Results 图 2A-B |
| 进化保守性分析 | 保护功能在羊膜动物中保守 | 36 种羊膜动物启动子 TFBS 保守性 | 45 个 TFBS 在哺乳类中保守 | 功能与进化保守性相关 | 不能证明功能直接保守 | Results 图 4 |
| ChIP-seq 富集 | CGGBP1 直接结合这些 TFBS | N-term/FL ChIP vs input | 45 个 TFBS 显著富集 | CGGBP1 直接结合靶位点 | 不能排除间接结合 | Results 图 5A-B |
| 表达-甲基化关联 | 甲基化保护与基因抑制相关 | C-repressed 基因的启动子甲基化 | 甲基化降低伴随表达降低 | 甲基化保护与抑制相关 | 不能证明因果方向 | Results 图 3 |

---

## 11 结论正确解读

- **任务范围**：本文仅在人 HEK293T 细胞中验证，未在其它细胞类型或体内验证。结论限于该细胞系。
- **oracle/真值输入**：无监督分析，无 oracle。甲基化数据来自 MeDIP-seq（抗体富集），非全基因组亚硫酸盐测序（WGBS），分辨率有限。
- **端到端状态**：非端到端。实验流程为「敲低 + 回补」的比较设计，未进行纯化蛋白体外甲基化保护实验。
- **算力成本**：未提供。
- **历史数据依赖**：依赖已发表的 ChIP-seq 数据（GSE129548、GSE187851），未重新生成。
- **模型依赖**：无 AI/计算模型。
- **最难情形**：非哺乳类（鸟类、爬行类）中甲基化保护功能未直接验证，仅通过序列分析间接推断。
- **群体/领域边界**：结论限于羊膜动物 CGGBP1 同源基因；不适用于无 CGGBP1 直系同源的非羊膜动物。
- **不确定性**：MeDIP-seq 无法区分 5-mC 与 5-hmC；ChIP-seq 无法区分直接/间接结合；截短突变体可能影响蛋白折叠/稳定性。

**有边界的复述**：在 HEK293T 细胞中，CGGBP1 的 N 端 DBD 通过直接结合 GC-rich TFBS 并限制其 CpG 甲基化，维持这些位点的低甲基化状态，从而介导基因抑制。该功能在羊膜动物中保守，但非羊膜动物中未验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未直接证明空间位阻机制 | 作者称「steric protection」为可能性，未做体外结合/甲基化酶竞争实验 | 未明确提及 | Discussion 节 |
| 非 CpG 甲基化未分析 | 仅分析 CpG 背景 | 未明确提及 | Results 节 4 |
| 细胞类型单一 | 仅 HEK293T | 未明确提及 | Methods 节 |
| 进化分析为间接证据 | 未在非哺乳类中直接验证功能 | 未明确提及 | Results 节 4 |
| 截短突变体可能影响蛋白稳定性 | 未做蛋白稳定性对照 | 未明确提及 | 未提供 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| MeDIP-seq 仅 1 个样本/条件 | 无生物学重复，无法评估技术/生物变异 | 甲基化差异可能为噪声 | 增加重复数，或使用 WGBS 验证 | Results 节 1；Methods 节 |
| 「C-repressed 基因」定义依赖 N-term 过表达 | N-term 可能非生理性表达水平 | 可能引入人为效应 | 使用内源水平表达或 CRISPR 敲入 | Results 节 3 |
| ChIP-seq 使用 FLAG 标签 | 标签可能影响蛋白构象/结合 | 可能改变结合谱 | 使用内源抗体 ChIP 验证 | Methods 节 |
| 进化分析中「保守性」未做统计检验 | 45 个 TFBS 的选择标准未明确 | 可能为偶然富集 | 使用置换检验或系统发育独立对比 | Results 节 4 |
| 甲基化保护与基因抑制的因果方向未定 | 可能是基因抑制导致甲基化降低，而非反之 | 机制方向是关键 | 时间序列实验或甲基化酶抑制剂处理 | Results 节 3 |
| 未检测蛋白-蛋白互作 | C 端可能通过招募其他因子间接影响甲基化 | 可能混淆直接/间接机制 | Co-IP + 甲基化酶活性实验 | Discussion 节 |

---

## 14 学到什么

**Agent 提炼的知识候选**：

1. **空间位阻作为甲基化保护机制**：CGGBP1 的 DBD 通过直接结合 GC-rich DNA 阻止甲基化酶接近。这一机制可迁移到 TF–DNA 互作研究中：在分子动力学（MD）模拟中，可显式建模 TF 结合与 DNA 甲基转移酶（如 DNMT3A/B）的空间竞争，计算结合自由能差异。
2. **截短突变体 + 全基因组读出的功能域解析范式**：将蛋白分为 DBD 和效应域，分别过表达并检测甲基化/表达/结合谱，可系统定位功能域。此范式可迁移到其他 TF 的功能域-表型关联研究。
3. **GC 含量与 G/C-skew 作为甲基化敏感性的序列特征**：本文发现 GC-rich、G/C-skew 高的 TFBS 更易被 CGGBP1 保护。这为 AI 模型提供可量化的序列特征（GC 含量、skew、CpG 密度），可用于预测 TFBS 的甲基化敏感性。
4. **进化保守性作为功能重要性的代理指标**：羊膜动物中保守的 DBD 和 TFBS 更可能具有功能。可迁移到 AI 辅助的 TFBS 预测中，将跨物种保守性作为特征或先验。
5. **「敲低 + 回补」实验设计**：通过 shRNA 敲低内源蛋白 + 过表达突变体，可区分不同结构域的功能贡献。此设计可迁移到 TF 功能研究中，尤其适用于多结构域 TF。

---

## 15 与已有知识连接

- **CGGBP1 与 CTCF 的关联**：本文引用 Patel et al. (2019, 2020) 表明 CGGBP1 影响 CTCF 占位和甲基化。这与 CTCF 甲基化敏感结合的特性一致（Wang et al., 2012, Genome Research）。可连接：CTCF 结合位点的甲基化调控是 TF–DNA 互作研究的重要案例。
- **甲基化敏感 TF**：已知多个 TF（如 CTCF、YY1、SP1）的 DNA 结合受 CpG 甲基化影响。本文的「保护」机制与「甲基化阻断结合」形成互补视角。可连接 Yin et al. (2017, Science) 关于甲基化敏感 TF 的系统鉴定。
- **Znf BED 结构域**：BED 锌指结构域见于多种染色质相关蛋白（如 ZBED 家族）。可连接结构数据库（PDB）中 BED 结构域的 DNA 结合模式。
- **羊膜动物进化**：本文的进化分析可连接脊椎动物基因组进化研究，特别是 GC 含量分布与调控元件演化的关系（如 Bernardi 等关于 isochore 的研究）。
- **AI 可迁移方向**：本文的 TFBS 甲基化保护数据可作为训练集，用于开发预测「甲基化敏感 TFBS」的深度学习模型。特征可包括序列 GC 含量、G/C-skew、CpG 密度、ChIP-seq 峰强度等。

---

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合与甲基化竞争的空间位阻 MD 模拟
   - **来源局限/观察**：本文提出空间位阻假说但未直接验证
   - **核心假设**：TF 结合 GC-rich motif 后，DNMT3A/B 因空间冲突无法接近 CpG 位点
   - **增量**：用 MD/对接模拟量化 TF 结合对 DNMT 接近的阻碍效应
   - **初步方法**：选取本文鉴定的 45 个 TFBS，构建 TF–DNA 复合物结构（AlphaFold3 或实验结构），与 DNMT3A-DNMT3L 复合物做竞争对接；计算结合自由能
   - **验证方式**：体外甲基化酶活性实验（TF 存在/不存在时 CpG 甲基化速率）
   - **创新状态**：unverified

2. **候选名称**：甲基化敏感 TFBS 的深度学习预测模型
   - **来源局限/观察**：本文鉴定了 GC-rich TFBS 的甲基化保护，但未系统建模
   - **核心假设**：序列特征（GC 含量、skew、CpG 密度、motif 位置）可预测 TFBS 的甲基化敏感性
   - **增量**：将本文 MeDIP-seq 数据与公共甲基化数据（如 TCGA、ENCODE WGBS）整合，训练 CNN/Transformer 模型
   - **初步方法**：以 TFBS 为中心 ±200 bp 序列为输入，预测甲基化水平；特征包括序列 embedding、GC 含量、进化保守性
   - **验证方式**：独立数据集验证 AUC；与已知甲基化敏感 TF（CTCF、YY1）交叉验证
   - **创新状态**：partially checked（已有甲基化预测模型如 DeepCpG，但未聚焦 TFBS 保护机制）

3. **候选名称**：CGGBP1 DBD 的 DNA 结合特异性结构解析
   - **来源局限/观察**：本文未解析 DBD 的 3D 结构
   - **核心假设**：CGGBP1 DBD 的 BED 锌指结构域以特定方式识别 GC-rich motif
   - **增量**：提供 CGGBP1 DBD 的原子级结构，为 MD 模拟和药物设计提供基础
   - **初步方法**：X 射线晶体学或 Cryo-EM；辅以 AlphaFold3 预测 + MD 验证
   - **验证方式**：突变 DBD 关键残基，检测 DNA 结合亲和力（EMSA/SPR）
   - **创新状态**：unverified

4. **候选名称**：羊膜动物 CGGBP1 靶位点的进化基因组学分析
   - **来源局限/观察**：本文仅用 36 种羊膜动物做启动子分析
   - **核心假设**：CGGBP1 靶位点在羊膜动物中受纯化选择，且与甲基化水平共进化
   - **增量**：扩展至全部羊膜动物基因组，结合系统发育模型检测选择压力
   - **初步方法**：从 UCSC/Ensembl 获取多物种比对，用 PHAST/PhyloP 检测保守性；结合甲基化数据（如 ENCODE 多物种）分析共进化
   - **验证方式**：置换检验；与随机位点比较
   - **创新状态**：partially checked（本文已做初步分析，但未用系统发育模型）

5. **候选名称**：TFBS 甲基化保护与基因表达调控的因果推断
   - **来源局限/观察**：本文观察到甲基化保护与基因抑制相关，但因果方向未定
   - **核心假设**：CGGBP1 通过保护 TFBS 免于甲基化，维持抑制性 TF 的结合，从而抑制基因
   - **增量**：用 CRISPR 编辑 CGGBP1 靶位点（引入/去除 CpG），检测甲基化和表达变化
   - **初步方法**：在 HEK293T 中用碱基编辑（BE3）靶向 CpG 位点；检测甲基化（WGBS）和表达（RNA-seq）
   - **验证方式**：编辑后甲基化变化与表达变化的关联；TF 结合（ChIP-seq）变化
   - **创新状态**：unverified