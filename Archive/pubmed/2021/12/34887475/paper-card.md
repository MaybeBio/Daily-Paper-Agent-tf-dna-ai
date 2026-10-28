## 01 基本信息

- **标题**：NF-Y subunits overexpression in gastric adenocarcinomas (STAD)
- **作者**：Gallo, Alberto; Ronzio, Mirko; Bezzecchi, Eugenia; Mantovani, Roberto; Dolfini, Diletta
- **单位**：未提供（推测为意大利米兰大学，因致谢提及 University of Milan）
- **期刊/平台**：Scientific Reports
- **年份**：2021-12-11
- **论文类型**：生物信息学/转录组学分析（TCGA 数据挖掘）
- **领域**：癌症转录调控；转录因子 NF-Y 在胃癌中的表达与临床意义
- **关键词**：NF-Y、CCAAT box、胃癌（STAD）、TCGA 分子分型、转录因子异构体
- **DOI/arXiv**：10.1038/s41598-021-03027-y
- **代码**：未提供
- **数据**：TCGA-STAD RNA-seq（415 肿瘤 + 35 正常）；CCLE 及 Lee et al. 胃癌细胞系 RNA-seq；ChIP-Atlas 数据库
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「TF–DNA 互作 × 癌症转录组学」交叉方向，聚焦 NF-Y（CCAAT-box 结合 pioneer TF）在胃癌中的表达模式、异构体比例与临床关联。对「TF–DNA 结合机制 × AI/物理模拟」课题的可迁移价值在于：(1) 展示了如何利用深度学习工具（DeepCC）对 TCGA 样本进行分子分型；(2) 提供了 TF 异构体比例（而非总表达量）作为功能开关的分析范式；(3) 提供了 CCAAT-box 在特定亚型/通路中富集的分析流程（Pscan + ChIP-Atlas 交叉验证）。

---

## 02 一句话总结

本文通过分析 TCGA-STAD 转录组数据，发现 NF-Y 三个亚基（尤其 NF-YA）在胃癌中过表达，且 NF-YAl/NF-YAs 异构体比例在 GS/EMT/Claudin-low 亚型中显著升高并与更差预后相关，而 CCAAT box 仅在所有亚型共有的核心上调基因启动子中富集。

---

## 03 研究问题

- **具体问题**：NF-Y 三个亚基及其两种主要异构体（NF-YAs/NF-YAl）在胃癌（STAD）各分子亚型中的表达模式如何？异构体比例是否具有临床预后价值？CCAAT box 在胃癌差异表达基因启动子中的富集模式如何？
- **为什么重要**：NF-Y 是 pioneer TF，调控细胞周期和代谢基因，在多种上皮癌中过表达。胃癌预后差、分子异质性强，明确 NF-Y 在亚型中的差异表达可为预后分层和靶向治疗提供依据。
- **现有方法不足**：此前两项胃癌研究（Cao et al.；另一项 TCGA 分析）仅报告 NF-YA 总表达量，未区分 NF-YAl/NF-YAs 异构体，也未系统分析 HFD 亚基（NF-YB/NF-YC）及亚型特异性。
- **精确研究问题**：Can NF-YA 异构体比例（NF-YAl/NF-YAs）而非总表达量，在 STAD 特定分子亚型（GS/EMT/Claudin-low）中作为预后生物标志物？

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论，属「仅本文框架」，未经外部系统综述核验。

1. **胃癌分类演进**：Lauren 组织学分类（IT/DF/MX）→ 分子分型（TCGA 四型：EBV/MSI/GS/CIN；ACRG 四型：EMT/MSS;TP53-/MSS;TP53+/MSI）。两套分类部分重叠。
2. **TF 结合位点富集分析**：早期微阵列研究（Ref. 15）发现 CCAAT box 是癌症过表达基因启动子中最富集的元件之一。
3. **NF-Y 结构与功能**：NF-Y 由序列特异性亚基 NF-YA 和组蛋白样二聚体 NF-YB/NF-YC 组成；NF-YA 有两种剪接异构体（NF-YAs/NF-YAl），差异在 Gln-rich TAD 区域（外显子 3 的 28/29 氨基酸）。
4. **NF-Y 在癌症中的研究**：卵巢癌、乳腺癌、肺癌、肝癌、头颈癌中均报道 NF-YA 过表达；乳腺癌中 NF-YAl 与 Claudin-low 亚型相关。
5. **本文位置**：首次在 STAD 中系统分析 NF-Y 三亚基 + NF-YA 异构体，结合 TCGA 与 ACRG 双分类体系，并引入 DeepCC 深度学习工具补全未分类样本。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 异构体信息丢失 | 既往研究仅报告 NF-YA 总表达量，未区分 NF-YAl/NF-YAs | 异构体差异仅在 TAD 区域，常规探针/引物难以区分 | 引言：Ref. 30, 31 未报告异构体比例 |
| 样本分类不完整 | TCGA 官方仅对 387/415 肿瘤完成分子分型 | 分类依赖多组学数据，部分样本数据缺失 | Results 图 2a：未分类 6.22% |
| CCAAT 富集信号被稀释 | 全局 DEG 分析中 CCAAT 非最显著元件 | 亚型特异性 DEG 稀释了核心共有信号 | Results 图 3a：仅核心 898 基因中 CCAAT 居首 |
| 亚型间异构体差异被掩盖 | GS 与 EMT 中 NF-YAl 升高，但总 NF-YA 水平在 GS 中较低 | 异构体比例变化与总表达量变化方向不一致 | Results 图 2b、图 5b |
| 预后关联不稳定 | 总 NF-YA 水平无预后价值，但异构体比例有 | 异构体功能差异（TAD 长度影响转录激活能力） | Results 图 4a：仅比例有显著 p 值 |

---

## 06 核心思想

### 1) 表面方法
对 TCGA-STAD RNA-seq 数据，用 DESeq2 做差异表达分析；用 DeepCC 深度学习工具将未分类样本补入 TCGA/ACRG 分子分型；用 Pscan 做启动子 TFBS 富集；用 Kaplan-Meier + log-rank 做生存分析；用层次聚类识别 Claudin-low 亚群。

### 2) 核心洞察
- **异构体比例 > 总表达量**：NF-YAl/NF-YAs 比例（而非 NF-YA 总水平）才是临床相关的功能指标，在 GS/EMT/Claudin-low 中升高并与预后差相关。
- **CCAAT 是"核心"信号而非"普遍"信号**：CCAAT box 仅在所有亚型共有的 898 个上调基因启动子中富集，而非在任一亚型特异性 DEG 中——提示 NF-Y 驱动的是跨亚型的核心增殖程序，亚型特异性由其他 TF 决定。
- **HFD 亚基的独立意义**：NF-YB 在 MSS;TP53+ 中高表达且具保护性，提示 HFD 亚基可能独立于 NF-YA 发挥功能（可能与 p53 状态相关）。

### 3) 可能的普适教训 [Analysis]
- 对 TF 功能研究，**异构体分辨**可能比总表达量更关键——尤其当异构体差异位于功能域（如 TAD）时。
- 对 TFBS 富集分析，**先取交集再富集**（而非全局富集）可揭示核心调控逻辑，避免亚型特异性信号掩盖共有机制。
- 深度学习分类工具（DeepCC）可有效扩展现有分子分型的覆盖度，但需注意训练集与目标集分布一致性。

---

## 07 方法总览

- **输入**：TCGA-STAD RNA-seq count 数据（RSEM scaled，415 肿瘤 + 35 正常）；CCST 37 株 + Lee et al. 29 株胃癌细胞系 FASTQ；TCGA/ACRG 官方分子分型标签（部分样本缺失）
- **输出**：NF-Y 亚基/异构体表达差异；亚型特异性 DEG 列表；TFBS 富集结果；生存曲线与风险分层；Claudin-low 亚群定义
- **模块**：
  1. 数据下载与预处理（firebrowse.org；SRA Explorer）
  2. 分子分型补全（DeepCC，以官方分类为训练集）
  3. 差异表达分析（DESeq2，|log2FC|>0.5，FDR<0.01）
  4. TFBS 富集（Pscan，启动子 -450~+50）
  5. GO/通路富集（KOBAS 3.0）
  6. ChIP-seq 交叉验证（ChIP-Atlas）
  7. 层次聚类（SigClust2，average linkage，euclidean）
  8. 生存分析（Kaplan-Meier + log-rank）
- **工具**：R 4.0.3（ggplot2, survival, survminer 等）；DeepCC；Pscan；KOBAS；SigClust2；RSEM 1.3.3
- **反馈回路**：无显式迭代反馈；分析流程为单向流水线
- **假设**：(i) TCGA 与 ACRG 分类可互相映射；(ii) DeepCC 分类结果可靠；(iii) 启动子区域 -450~+50 为 TFBS 分析的有效窗口

**文字流程**：
下载 TCGA count 数据 → 用 DeepCC 补全 TCGA/ACRG 分型 → DESeq2 计算肿瘤 vs 正常 DEG → 对全局及亚型 DEG 用 Pscan 做 TFBS 富集 → 用 KOBAS 做 GO 富集 → 对核心 898 基因做 Pscan → 用 ChIP-Atlas 验证候选 TF → 对 NF-Y 亚基/异构体做亚型间差异比较 → 层次聚类识别 Claudin-low → 生存分析评估预后价值。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| DeepCC 分型补全 | 将未分类 TCGA 样本归入 TCGA/ACRG 亚型 | 官方分类仅覆盖 387/415，未分类样本无法参与亚型分析 | 输入：RNA-seq 表达谱 + 官方分类标签；输出：全样本亚型标签 | Results 图 2a：未分类从 6.22% 降至 0 | [预期] 亚型特异性 DEG 分析样本量减少，统计功效下降 |
| DESeq2 差异表达 | 识别肿瘤 vs 正常 DEG | 定义各亚型及全局的基因表达变化 | 输入：count 矩阵；输出：DEG 列表（log2FC, FDR） | Methods；Supplementary Table S1 | [预期] 无 DEG 列表则后续富集分析无法进行 |
| Pscan TFBS 富集 | 识别 DEG 启动子中富集的 TF 结合基序 | 将 DEG 与上游调控因子关联 | 输入：DEG 基因列表 + 启动子序列；输出：富集 TF 矩阵及 p 值 | Results 图 3b、图 8a、S2a、S3a | [预期] 无法识别 CCAAT 为核心信号 |
| KOBAS GO 富集 | 注释 DEG 的生物学通路 | 将基因列表转化为功能解读 | 输入：DEG 列表；输出：GO term 及 p 值 | Results 图 3b、S2b、S3b | [预期] 无法判断 DEG 的功能类别 |
| 层次聚类（SigClust2） | 基于 24 基因 signature 识别 Claudin-low 亚群 | 验证 Nishijima 亚群在 TCGA 全集中存在 | 输入：24 基因表达矩阵；输出：聚类树 + 显著性 | Results 图 7a：79 样本显著分离 | [预期] Claudin-low 分析无法进行 |
| Kaplan-Meier 生存分析 | 评估 NF-Y 表达/比例与预后的关联 | 将分子特征转化为临床意义 | 输入：表达分层 + PFI 时间；输出：生存曲线 + log-rank p 值 | Results 图 4、图 6 | [预期] 无法得出异构体比例的预后价值 |
| ChIP-Atlas 验证 | 交叉验证 Pscan 预测的 TF 是否真实结合靶基因 | 避免仅基于序列基序的假阳性 | 输入：TF 列表；输出：ChIP-seq 实验证据 | Results 图 8a；Supplementary Table S3 | [预期] 预测的 MAZ/E2F6/KLF 缺乏实验支持 |

---

## 09 关键公式符号

本文为纯转录组分析，无数学模型或物理公式。关键统计量：

- **log2FC**：log2 倍数变化，阈值 |log2FC| > 0.5
- **FDR**：错误发现率，阈值 < 0.01
- **p 值**：Wilcoxon 秩和检验（组间表达差异）；log-rank 检验（生存曲线差异）
- **Z score**：对 24 基因 signature 表达量做 log2 转换、中位数中心化后计算

不适用（无公式可列）。

---

## 10 实验设计与证据链

- **数据集**：TCGA-STAD RNA-seq（415 肿瘤 + 35 正常）；CCLE 37 株 + Lee et al. 29 株胃癌细胞系；ChIP-Atlas 数据库
- **规模**：415 肿瘤样本；50 细胞系（去重后）
- **指标**：表达量（TPM）、log2FC、FDR、生存概率（PFI）、富集 p 值
- **基线**：正常胃组织（35 例）作为表达差异基线；官方 TCGA/ACRG 分类作为 DeepCC 训练标签
- **预算**：未提供
- **骨干/仪器**：无实验仪器；纯计算分析
- **oracle 输入**：TCGA 官方分子分型标签（用于 DeepCC 训练）；Nishijima 24 基因 signature（用于 Claudin-low 识别）
- **评测协议**：Wilcoxon 秩和检验（表达差异）；log-rank 检验（生存差异）；Pscan 富集 p 值；SigClust2 聚类显著性

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| NF-Y 亚基表达（肿瘤 vs 正常） | NF-Y 在 STAD 中过表达 | 415 肿瘤 vs 35 正常 | NF-YA p=10⁻¹⁴，NF-YB/NF-YC p=10⁻⁷/10⁻⁸ | 三亚基均过表达，NF-YA 最显著 | 未做蛋白水平验证；未校正多因素 | Results 图 1a |
| NF-YA 异构体表达 | NF-YAs 是主要异构体 | 肿瘤 vs 正常 | NF-YAs p=10⁻¹⁵，NF-YAl 无显著差异 | NF-YAs 驱动总 NF-YA 升高 | 未验证蛋白异构体比例 | Results 图 1b |
| 亚型间 NF-YA 表达 | 亚型间存在差异 | TCGA 四亚型互比 | GS 中 NF-YA 较低 | 亚型间表达异质性 | 未做多重比较校正 | Results 图 2b |
| 亚型间异构体比例 | GS 中 NF-YAl/NF-YAs 比例升高 | TCGA 四亚型互比 | GS 比例显著高于其他 | 异构体比例是亚型特征 | 未验证功能后果 | Results 图 2b |
| 核心 DEG 的 TFBS 富集 | CCAAT 是核心上调基因的主要元件 | 898 核心基因 vs 亚型特异性 DEG | CCAAT 在核心基因中居首，亚型特异性 DEG 中无 | NF-Y 驱动跨亚型核心增殖程序 | 未做 motif 突变验证 | Results 图 3b |
| NF-YAl/NF-YAs 比例与预后 | 比例高预后差 | 全体 STAD 按四分位分层 | p=0.0099 | 比例有预后价值 | 未做多变量 Cox 回归 | Results 图 4a |
| 亚型内预后分析 | CIN/EBV 中比例有预后价值 | CIN、EBV 亚型内分层 | CIN p=0.0099，EBV 显著 | 亚型特异性预后价值 | 样本量小（EBV） | Results 图 4b |
| ACRG 分型下 NF-Y 表达 | EMT 中 NF-YAl 高、NF-YAs 低 | ACRG 四亚型互比 | EMT 比例最高 | ACRG 分型更能揭示异构体差异 | 未与 TCGA 分型做一致性检验 | Results 图 5b |
| ACRG 分型下预后 | EMT 中比例高预后差 | EMT 亚型内分层 | p=0.012 | EMT 中比例有预后价值 | 未做多变量校正 | Results 图 6a-c |
| NF-YB 在 MSS;TP53+ 中保护性 | NF-YB 高表达预后好 | MSS;TP53+ 亚型内分层 | 显著保护 | NF-YB 独立于 NF-YA 有临床意义 | 机制不明 | Results 图 6d |
| Claudin-low 亚群识别 | 24 基因 signature 可识别 79 样本 | 全体 TCGA 样本聚类 | 79 样本显著分离 | Claudin-low 亚群存在 | 未与 Nishijima 原始 46 样本完全重叠 | Results 图 7a |
| Claudin-low 中 NF-YA 异构体 | NF-YAl 在 Claudin-low 中最高 | Claudin-low vs 其他亚型 | NF-YAl 显著高，NF-YAs 最低 | 异构体比例与 Claudin-low 表型相关 | 未做功能实验 | Results 图 7c-d |
| Claudin-low 中 CCAAT 富集 | CCAAT 在 Claudin-low 上调通路中富集 | Claudin-low DEG 通路分析 | 间充质相关通路中 CCAAT 富集 | NF-Y 参与 Claudin-low 的间充质程序 | 未做 ChIP-seq 直接验证 | Results 图 8 |

---

## 11 结论正确解读

- **任务范围**：本文仅分析 mRNA 表达水平（RNA-seq），未涉及蛋白水平、DNA 结合活性或染色质状态。
- **oracle/真值输入**：TCGA 官方分子分型作为 DeepCC 训练标签；Nishijima 24 基因 signature 作为 Claudin-low 定义依据。这些标签本身来自其他研究，存在分类标准差异。
- **端到端状态**：非端到端。分析流程为「表达 → 分型 → DEG → 富集 → 生存」，各步骤独立，未形成可预测模型。
- **算力成本**：未提供。DeepCC 为轻量级工具，整体计算成本低。
- **历史数据依赖**：完全依赖 TCGA 公共数据（截至 2020 年 12 月），无独立验证队列。
- **模型依赖**：DeepCC 分类结果依赖训练集标签质量；Pscan 依赖 motif 数据库完整性。
- **最难情形**：GS 亚型样本量小（~60），EBV 更小（~25），亚型内生存分析统计功效有限。
- **群体/领域边界**：仅限胃腺癌（STAD），不涵盖其他胃癌类型（如胃食管交界癌）；结论基于 mRNA 水平，不直接推广至蛋白功能。
- **不确定性**：NF-YAl/NF-YAs 比例的预后价值未做多变量 Cox 回归校正年龄、分期、治疗等因素；Claudin-low 亚群与 Nishijima 原始定义存在样本差异。

**有边界的复述**：在 TCGA-STAD 的 mRNA 表达数据中，NF-Y 三亚基过表达，NF-YAs 为主要异构体；在 GS/EMT/Claudin-low 亚型中 NF-YAl/NF-YAs 比例升高并与较差无进展生存相关；CCAAT box 仅在跨亚型核心上调基因中富集。这些关联未经独立队列验证，也未在蛋白或功能层面确认。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 未做蛋白水平验证 | 仅分析 mRNA 表达，未检测 NF-Y 蛋白水平 | 讨论中提及"measurement of protein levels in tumors deserve a close look in the future" | Discussion 末段 |
| 异构体功能机制不明 | NF-YAl/NF-YAs 比例与预后的因果关系未建立 | 未明确给出 | Discussion（间接） |
| 细胞系数据有限 | 仅分析表达水平，未做功能实验 | 未明确给出 | 未提供 |
| 样本量限制 | GS 亚型样本量小，亚型内分析功效有限 | 未明确给出 | 未提供 |

> 注：作者在 Discussion 中明确提及蛋白水平验证为未来方向，其余局限为本文分析框架内隐含约束，作者未系统列出。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| DeepCC 分型补全依赖训练集 | 未分类样本可能因数据质量差而被 DeepCC 错误分类，导致亚型 DEG 分析偏差 | 分型错误会直接污染后续所有亚型特异性分析 | 比较 DeepCC 分类与官方分类在重叠样本上的一致性；用独立方法（如 PAM50）交叉验证 | Results 图 2a；Methods |
| CCAAT 富集分析仅基于序列 motif | Pscan 预测的 motif 富集不等于 NF-Y 实际结合；未用 ChIP-seq 数据验证 STAD 中 NF-Y 结合位点 | pioneer TF 的序列偏好与实际染色质结合可能不一致 | 用 TCGA 或 ENCODE 中胃癌细胞系 NF-Y ChIP-seq 数据交叉验证 | Results 图 3b；Methods |
| 生存分析未做多变量校正 | 年龄、分期、治疗等混杂因素未纳入 Cox 模型，NF-YAl/NF-YAs 比例可能只是其他因素的代理 | 预后标志物需独立于已知临床因素 | 用多变量 Cox 回归校正年龄、TNM 分期、MSI 状态等 | Results 图 4、图 6 |
| Claudin-low 亚群定义依赖 24 基因 signature | 该 signature 来自 Nishijima 研究，可能过度拟合其训练集；79 样本与原始 46 样本不完全重叠 | 亚群定义不稳定会影响所有下游分析 | 用不同 signature 或聚类方法验证 Claudin-low 亚群的稳健性 | Results 图 7a |
| 细胞系分析仅报告表达模式 | 未做 NF-Y 敲低/过表达的功能实验，无法区分因果与关联 | 表达关联不能证明 NF-Y 驱动肿瘤表型 | 在胃癌细胞系中敲低 NF-YA 异构体，观察增殖/迁移表型 | Results S1 |
| 异构体比例的计算方式未明确 | 未说明 NF-YAl/NF-YAs 比例是基于外显子表达量还是转录本重构，不同方法可能结果不同 | 异构体定量方法影响结论可重复性 | 用 Salmon/kallisto 等转录本定量工具独立验证 | Results 图 1b |
| 正常组织对照仅 35 例 | 正常样本量小且可能来自肿瘤邻近组织，存在"场效应"污染 | 对照偏差会影响 DEG 可靠性 | 使用 GTEx 正常胃组织作为独立对照 | Methods |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **异构体比例作为功能开关的分析范式**：本文展示了在 TF 研究中，区分剪接异构体（而非仅总表达量）可揭示临床相关信号。迁移到 TF–DNA 互作课题：对具有多种剪接异构体的 TF（如 p53、RUNX1），应优先分析异构体比例而非总表达量，尤其当异构体差异位于 DNA 结合域或 TAD 时。

2. **"先交集再富集"的 TFBS 分析策略**：本文对核心 898 基因（所有亚型共有）做 TFBS 富集，发现 CCAAT 是核心信号，而亚型特异性 DEG 中无此信号。迁移价值：在比较不同条件/亚型的 TF 结合模式时，先取交集再富集可揭示核心调控逻辑，避免被条件特异性信号干扰。

3. **深度学习工具扩充分子分型的可迁移性**：DeepCC 用已分类样本训练、对未分类样本补全分型，有效扩大了分析覆盖度。迁移到 AI×TF–DNA 课题：当实验数据部分缺失标签时，可用半监督或迁移学习策略补全，但需验证分类一致性。

4. **pioneer TF 的"核心程序"概念**：NF-Y 驱动的是跨亚型的核心增殖程序（细胞周期、DNA 复制），而非亚型特异性程序。迁移价值：对 pioneer TF（如 FOXA1、GATA3），其功能可能在于维持核心细胞程序，而非决定细胞身份——这影响对 TF 结合位点分析结果的解读。

5. **HFD 亚基的独立临床意义**：NF-YB 在 MSS;TP53+ 中具保护性，提示组蛋白样亚基可能独立于序列特异性亚基发挥功能。迁移价值：对多亚基 TF 复合物，各亚基的表达/功能应独立分析，而非仅关注 DNA 结合亚基。

6. **ChIP-Atlas 作为 TFBS 预测的交叉验证资源**：本文用 ChIP-Atlas 验证 Pscan 预测的 TF。迁移到课题：对 AI 预测的 TF 结合位点，应使用公共 ChIP-seq 数据库（ChIP-Atlas、ENCODE、CistromeDB）进行实验验证，避免仅依赖序列 motif。

---

## 15 与已有知识连接

- **NF-Y 结构与功能**：本文引用的 Ref. 17（NF-Y 三聚体结构）、Ref. 16（CCAAT box 功能）、Ref. 20（NF-Y 调控细胞周期）为该领域经典文献。可进一步阅读 Mantovani R. 的综述（Gene, 1999）了解 NF-Y 结构-功能关系。
- **pioneer TF 概念**：本文讨论中提及 NF-Y 的 pioneer 角色（Ref. 39），与 FOXA1、GATA3 等 pioneer TF 研究可类比。可参考 Zaret & Carroll (2011) 关于 pioneer TF 的综述。
- **TCGA 分子分型**：本文使用的 TCGA 四型分类来自 TCGA 网络 (Nature, 2014)；ACRG 分类来自 Cristescu et al. (Nature Medicine, 2015)。两套分类的对应关系可参考本文引用的 Ref. 11-13。
- **乳腺癌中的 NF-Y 异构体**：本文与作者前期乳腺癌研究（Ref. 25）直接关联，后者报道了 Claudin-low 亚型中 NF-YAl 升高。两文联合阅读可理解异构体比例在不同癌种中的一致性。
- **DeepCC 工具**：本文使用的 DeepCC 来自 Gao et al. (2019)，是基于深度学习的分子分型工具。与 PAM50、CMOIC 等传统分型方法可对比。
- **CCAAT box 在癌症中的富集**：本文引用的 Ref. 15（微阵列 meta 分析）是 CCAAT 富集信号的经典来源。可进一步阅读该文献了解跨癌种 CCAAT 富集模式。
- **与 AI×TF–DNA 课题的关联**：本文的 TFBS 富集分析（Pscan）可视为「序列 motif → TF 关联」的经典方法，与基于深度学习的 motif 发现（如 DeepBind、DeepSEA）形成互补。本文的「核心 vs 亚型特异性」富集策略可迁移到深度学习模型的可解释性分析中。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：基于深度学习的 NF-Y 异构体特异性结合位点预测
- **名称**：Isoform-aware NF-Y binding predictor
- **来源局限/观察**：本文仅分析表达水平，未区分 NF-YAs/NF-YAl 在 DNA 结合偏好上的差异；两种异构体共享 DNA 结合域，但 TAD 差异可能影响染色质开放能力
- **核心假设**：NF-YAs 与 NF-YAl 虽识别相同 CCAAT 基序，但在染色质可及性不同的区域结合偏好不同
- **增量**：现有 DeepBind/DeepSEA 类模型未考虑异构体差异；可训练异构体特异性模型
- **初步方法**：使用 ENCODE/ChIP-Atlas 中 NF-Y ChIP-seq 数据，按细胞类型中 NF-YAs/NF-YAl 表达比例分组，训练两个结合预测模型；比较 motif 侧翼序列特征
- **验证方式**：在独立细胞系中预测结合位点，与 ChIP-seq 比较 AUC
- **创新状态**：unverified

### 候选 2：CCAAT 核心程序 vs 亚型特异性程序的调控逻辑建模
- **名称**：Core-vs-specific cis-regulatory logic model
- **来源局限/观察**：本文发现 CCAAT 仅在核心上调基因中富集，亚型特异性 DEG 由其他 TF 驱动
- **核心假设**：pioneer TF（NF-Y）建立核心程序，而亚型特异性 TF 在 pioneer 开放的染色质上叠加次级调控
- **增量**：将「pioneer + 次级 TF」的层级调控形式化为可计算模型
- **初步方法**：用 STAD 各亚型 DEG 的启动子/增强子序列，训练一个两层模型：第一层预测 CCAAT 存在，第二层预测亚型特异性 TF 基序；用逻辑回归或决策树比较层级 vs 平行模型拟合度
- **验证方式**：在独立数据集（如 LIHC、BRCA）中检验模型可迁移性
- **创新状态**：unverified

### 候选 3：NF-YB 保护性作用的机制假设与验证
- **名称**：NF-YB protective axis in TP53-wildtype gastric cancer
- **来源局限/观察**：本文发现 NF-YB 高表达在 MSS;TP53+ 中具保护性，但未提供机制解释
- **核心假设**：NF-YB 通过与 p53 互作或调控 p53 靶基因，在 TP53 野生型背景下发挥肿瘤抑制作用
- **增量**：将表达关联推进到机制假设
- **初步方法**：使用 TCGA-STAD 中 MSS;TP53+ 样本，分析 NF-YB 高/低组的差异表达通路；用 ChIP-Atlas 检查 NF-YB 与 p53 共结合位点；在 p53 野生型胃癌细胞系中敲低 NF-YB，检测 p53 靶基因表达
- **验证方式**：体外实验验证 NF-YB-p53 互作；临床数据验证 NF-YB 与 p53 状态交互作用
- **创新状态**：unverified

### 候选 4：TF 异构体比例作为泛癌预后标志物的系统分析
- **名称**：Pan-cancer TF isoform ratio atlas
- **来源局限/观察**：本文在 STAD 中发现 NF-YAl/NF-YAs 比例有预后价值，但未在泛癌中验证
- **核心假设**：TF 异构体比例（而非总表达量）在多种癌症中具有预后价值
- **增量**：将单癌种发现推广为泛癌规律
- **初步方法**：从 TCGA 泛癌数据中提取所有具有剪接异构体的 TF，计算异构体比例；对每个 TF 做生存分析，筛选与预后相关的比例变化；与总表达量预后价值对比
- **验证方式**：在独立队列（如 GEO）中验证 top hits
- **创新状态**：unverified

### 候选 5：NF-Y 结合位点的三维结构预测与突变效应分析
- **名称**：NF-Y-CCAAT complex structure-activity prediction
- **来源局限/观察**：本文未涉及 NF-Y-DNA 结合的结构机制；NF-Y 的组蛋白样结构域（HFD）与 DNA 弯曲的机制已有晶体结构（如 Nye et al. 2017）
- **核心假设**：NF-YA 异构体差异（TAD 长度）通过影响 NF-Y 三聚体稳定性或 DNA 弯曲角度改变结合亲和力
- **增量**：将 AlphaFold2 预测与分子动力学模拟结合，预测异构体特异性结合差异
- **初步方法**：用 AlphaFold2 预测 NF-YAs/NF-YAl 三聚体结构；对 CCAAT 盒 DNA 做分子对接；用 MD 模拟比较两种异构体的 DNA 弯曲角度和结合自由能
- **验证方式**：与已知 NF-Y-DNA 晶体结构对比 RMSD；用表面等离子共振（SPR）验证结合亲和力差异
- **创新状态**：unverified