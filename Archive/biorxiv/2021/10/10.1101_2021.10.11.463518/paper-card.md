## 01 基本信息

- **标题**：Factorbook: an Updated Catalog of Transcription Factor Motifs and Candidate Regulatory Motif Sites
- **作者与单位**：Pratt HE; Andrews GR; Phalke N; Purcaro MJ; van der Velde A; Moore JE; Weng Z（马萨诸塞大学医学院，Weng Lab；未提供完整单位列表）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2021
- **论文类型**：数据库/资源描述 + 方法学（工具/资源型）
- **领域**：调控基因组学、转录因子（TF）基序目录、候选调控元件注释
- **关键词**：转录因子、DNA 结合基序、ChIP-seq、HT-SELEX、卷积神经网络（CNN）、候选顺式调控元件（cCREs）、LD 分数回归
- **DOI/arXiv 号**：10.1101/2021.10.11.463518
- **代码**：https://www.github.com/weng-lab/motif-workflow（MEME 与 ZMotif 流程）；https://www.github.com/weng-lab/ldr（LDSC Docker 镜像）
- **数据**：https://www.factorbook.org/（数据库）；ENCODE Phase II/III ChIP-seq 与 HT-SELEX 数据
- **阅读日期**：未提供
- **该文在课题方向中的位置**：本文属于「TF–DNA 结合机制 × AI/深度学习」方向的**资源基础设施型**工作。它不直接提出新的结合机制模型，而是提供：(1) 大规模 TF 基序目录（MEME 基序 + ZMotif 深度学习基序）；(2) 全基因组候选 TF 结合位点注释（整合 cCRE 与 rDHS）；(3) 可直接用于迁移学习的 CNN 卷积核（HDF5 格式）。对 TF–DNA 互作研究而言，本文是**训练数据与预训练特征来源**，而非机制发现本身。

---

## 02 一句话总结

本文通过整合 ENCODE Phase II/III 的 ChIP-seq 数据（MEME 流程）与 HT-SELEX 数据（新开发的 ZMotif 卷积神经网络），构建了覆盖 694 个人类 TF 和 62 个小鼠 TF 的基序目录，并将基序实例注释到全基因组候选调控元件（cCRE/rDHS）上，同时提供深度学习卷积核导出、SNP 注释和遗传力分区分析工具。

---

## 03 研究问题

- **具体问题**：如何构建一个大规模、多来源（ChIP-seq + HT-SELEX）、可直接用于机器学习的 TF 基序目录，并将基序实例系统注释到候选调控元件上？
- **为什么重要**：TF 结合基序是理解基因调控的基础。现有目录（如 HOCOMOCO、JASPAR）覆盖有限，且缺乏与调控元件注释的整合；深度学习模型在调控基因组学中日益重要，但缺乏可直接迁移的基序特征。
- **现有方法不足**：
  - HOCOMOCO 和 JASPAR 覆盖的 TF 数量有限（约 700 个），且主要依赖体外数据；
  - 已有 Factorbook 第一版仅覆盖 119 个人类 TF，基于 ENCODE Phase II；
  - 缺乏将基序实例与 cCRE 调控元件注释整合的全基因组资源；
  - 缺乏以深度学习格式（如 HDF5 卷积核）提供的基序模型，难以直接用于迁移学习。
- **精确研究问题**：Can we build a comprehensive TF motif catalog from ENCODE Phase II/III ChIP-seq and HT-SELEX data, annotate motif instances in candidate cis-regulatory elements genome-wide, and provide deep-learning-ready motif models for transfer learning?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及参考文献，经外部核验（HOCOMOCO、JASPAR、ENCODE 为公开已知资源），标记为「经外部核验」。

| 阶段 | 代表性方法/资源 | 优点 | 局限 | 本文位置 |
|---|---|---|---|---|
| 早期体外基序 | UniPROBE（蛋白结合微阵列） | 高精度、体外可控 | 仅覆盖部分 TF，缺乏体内上下文 | — |
| 综合目录 | HOCOMOCO、JASPAR | 覆盖数百 TF，整合多来源 | 主要依赖体外或低通量体内数据，缺乏与调控元件注释的整合 | 本文与之比较，声称覆盖更广 |
| 体内 ChIP-seq 基序 | 第一版 Factorbook（ENCODE Phase II） | 基于体内 ChIP-seq，覆盖 119 个人类 TF | 覆盖有限，缺乏深度学习格式 | 本文为第二版，扩展至 694 个人类 TF |
| 深度学习基序发现 | DeepBind、DeepSEA 等 | 可学习复杂序列特征 | 基序可解释性差，缺乏与实验数据的系统整合 | 本文提出 ZMotif，专门用于 HT-SELEX 基序发现 |
| 调控元件注释 | ENCODE Registry of cCREs | 全基因组候选调控元件 | 缺乏 TF 基序层面的系统注释 | 本文将基序实例映射到 cCRE/rDHS |

**本文主张的位置**：在基序目录的「覆盖广度」与「深度学习可用性」两个维度上同时推进，并首次将基序实例与 cCRE 注释系统整合。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 基序目录覆盖不足 | 约 1,600 个人类 TF 中，仅约 700 有注释基序 | 体外方法（如 HT-SELEX）覆盖有限，ChIP-seq 数据分散 | Introduction 引用 HOCOMOCO/JASPAR 覆盖数；Results 报告本文覆盖 694 个人类 TF |
| 缺乏深度学习可用格式 | 现有基序多为 PWM 格式，难以直接用于 CNN 迁移学习 | 深度学习模型通常以卷积核权重形式存储，PWM 需转换 | Overview 与 Tools 节描述 HDF5 导出功能 |
| 基序实例与调控元件注释脱节 | 研究者难以判断某基序是否位于候选增强子/启动子中 | 缺乏将基序扫描结果与 cCRE 注释整合的资源 | Results 描述将基序实例映射到 cCRE/rDHS 的流程 |
| 基序质量评估困难 | 难以判断某基序是真实 TF 结合位点还是共因子/噪声 | ChIP-seq 基序可能受共结合因子影响 | 作者用保守性、DNase 保护、峰中心性等指标辅助评估（Results 图 2D-F） |
| 遗传变异功能注释缺乏 TF 维度 | GWAS 变异难以快速判断是否影响 TF 结合 | 缺乏将 SNP 与基序实例交叉的交互工具 | Tools 节描述 SNP 注释功能 |

---

## 06 核心思想

### 1) 表面方法
- 用 MEME 对 ENCODE Phase II/III ChIP-seq 峰进行 de novo 基序发现；
- 开发 ZMotif（CNN）对 HT-SELEX 数据进行基序发现；
- 用 FIMO 将基序扫描到 ChIP-seq 峰和 cCRE/rDHS 中；
- 提供交互式网站、HDF5 卷积核导出、SNP 注释和 LDSC 遗传力分区工具。

### 2) 核心洞察
- **多来源互补**：ChIP-seq 基序反映体内结合上下文（含共因子影响），HT-SELEX 基序反映体外纯化 DNA 结合偏好；两者互补，可交叉验证。
- **深度学习基序可迁移**：将 CNN 卷积核视为「可迁移的基序特征」，直接以 HDF5 格式导出，供其他模型做迁移学习初始化。
- **调控元件注释是基序实例的「功能上下文」**：仅知道基序序列不够，需知道它位于哪个候选增强子/启动子中，才能推断调控意义。
- **基序实例的「质量三重证据」**：保守性（phyloP）、染色质可及性（DNase 保护）、峰中心性三者联合，可区分真实 TF 结合位点与噪声。

### 3) 可能的普适教训 [Analysis]
- 在 TF–DNA 互作研究中，**基序目录的价值不仅在于序列本身，更在于与调控元件注释、保守性、染色质状态的整合**。单一基序列表不足以支撑机制推断。
- **深度学习模型的可解释性输出（卷积核）可以成为资源**，而非仅作为黑箱预测器。将卷积核导出为基序格式，是连接 DL 与传统基序分析的桥梁。
- **多数据源交叉验证**（体内 ChIP-seq vs 体外 HT-SELEX）是降低基序假阳性率的有效策略，可迁移到其他 TF–DNA 互作研究。

---

## 07 方法总览

- **输入**：
  - ENCODE Phase II/III 非组蛋白 ChIP-seq 峰（人类 + 小鼠），IDR 阈值化；
  - 公共 HT-SELEX 数据集（两个来源，参考文献 2 和 24）；
  - ENCODE Registry of cCREs V3（rDHS 集合）；
  - 1000 Genomes 群体数据（用于 LD）；
  - UK Biobank GWAS 汇总统计（三种性状）。

- **输出**：
  - 基序目录（MEME 格式 PWM + ZMotif 卷积核 HDF5）；
  - 全基因组基序实例（BED 格式，含保守性、DNase 保护、峰中心性注释）；
  - 交互式网站（搜索、可视化、BED 上传交集）；
  - LDSC 遗传力分区模型。

- **模块**：
  1. MEME 基序发现流程（ChIP-seq 峰 → 前 500 峰 → MEME de novo）；
  2. ZMotif CNN（HT-SELEX 序列 → 卷积核 → PWM 转换）；
  3. FIMO 扫描（基序 → ChIP-seq 峰 / cCRE / rDHS）；
  4. 质量评估（保守性、DNase 保护、峰中心性聚合）；
  5. SNP 注释工具（SNP × 基序实例 × LD × ChIP-seq 峰）；
  6. LDSC 遗传力分区（基序实例作为注释集）。

- **训练**：
  - ZMotif：单卷积层（16 核，宽 24 bp）+ 全局最大池化 + sigmoid 输出；正样本为 HT-SELEX 结合序列，负样本为未结合序列（二核苷酸打乱）；Adam 优化器，循环学习率 0.1–0.01，1000 epoch，每 epoch 5000 序列；权重约束为正（防止反基序）；随机权重平均（最后 200 epoch）。

- **工具**：ReactJS 前端 + GraphQL API；Docker 镜像（motif-workflow、ldr）。

- **反馈回路**：无显式闭环反馈；但用户可通过 BED 上传实时交集、SNP 注释获得交互式分析结果。

- **假设**：
  - ChIP-seq 峰的前 500 个（按 q 值排序）足以代表 TF 的真实结合偏好；
  - HT-SELEX 的富集序列可反映体外 DNA 结合特异性；
  - FIMO p 值阈值（10⁻⁴ 用于峰内，10⁻⁶/10⁻⁵ 用于 rDHS）可平衡灵敏度与假阳性。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| MEME 基序发现流程 | 从 ChIP-seq 峰中 de novo 发现富集基序 | ChIP-seq 反映体内结合上下文，可发现共因子基序 | 输入：前 500 峰序列；输出：最多 5 个基序/PWM | Results 报告 6,921 个人类基序；与 HOCOMOCO/JASPAR 比较覆盖近 100% | 移除后失去体内上下文基序，仅剩体外基序 |
| ZMotif CNN | 从 HT-SELEX 数据中学习 DNA 结合基序 | 体外数据无共因子干扰，反映纯 DNA 结合偏好；CNN 可学习复杂 motif 表示 | 输入：HT-SELEX 序列（one-hot）；输出：16 个卷积核（HDF5）+ PWM | Results 报告 6,700 个 HT-SELEX 基序；与 MEME 基序互补 | 移除后失去体外高精度基序，且无 HDF5 卷积核可导出 |
| FIMO 扫描 | 将基序实例定位到 ChIP-seq 峰和 cCRE/rDHS | 将基序从「序列偏好」转化为「基因组位置」 | 输入：PWM + 基因组序列；输出：基序实例 BED | Results 报告 1.1 亿峰内实例、3,300 万 rDHS 实例 | 移除后无法提供候选 TF 结合位点 |
| 质量三重证据（保守性/DNase/峰中心性） | 评估基序实例是否为真实 TF 结合位点 | 区分真实结合与噪声/共因子 | 输入：phyloP、DNase-seq、峰坐标；输出：聚合指标 | Results 图 2D-F 显示高质量基序更保守、更居中、更受 DNase 保护 | 移除后用户无法判断基序实例可信度 |
| SNP 注释工具 | 将 SNP 与基序实例交叉，评估对 TF 结合的潜在影响 | 连接遗传变异与 TF 结合机制 | 输入：rsID + 群体；输出：受影响基序、ChIP-seq 支持 | Tools 节描述；图 5A-C 示例 | 移除后失去变异功能注释入口 |
| LDSC 分区模型 | 量化基序实例对性状遗传力的贡献 | 评估 TF 结合位点在疾病/性状中的富集 | 输入：GWAS 汇总统计 + 基序实例 BED；输出：分区遗传力富集 | Results 图 5D 显示疾病相关细胞类型富集 | 移除后失去遗传力层面的功能验证 |

---

## 09 关键公式符号

本文为数据库/资源型论文，核心方法（MEME、FIMO、LDSC）为既有工具，未给出新公式。以下为隐含或引用的关键概念：

1. **FIMO p 值**（MEME Suite 工具）：
   - 基于位置权重矩阵（PWM）的似然比检验，计算给定序列位置与基序匹配的统计显著性。
   - 符号：`p`（匹配 p 值），阈值 10⁻⁴（峰内）、10⁻⁶/10⁻⁵（rDHS）。
   - 用途：判定基序实例是否显著。
   - 来源：Methods「Motif site identification」节。

2. **ZMotif 卷积核激活**：
   - 单卷积层：`h_i = σ(Σ_j W_j · x_{i:i+24})`，其中 `W` 为卷积核权重（16 个，宽 24 bp），`x` 为 one-hot 编码序列。
   - 全局最大池化后经 sigmoid 输出：`ŷ = σ(w·max(h) + b)`。
   - 用途：学习基序表示；权重约束为正以防止反基序。
   - 来源：Methods「ZMotif」节。

3. **LDSC 分区遗传力**（引用文献 15）：
   - `E[χ²_j] = N·Σ_c τ_c·ℓ(j,c) + 1`，其中 `χ²_j` 为 SNP j 的卡方统计量，`ℓ(j,c)` 为 SNP j 在注释集 c 中的 LD 得分，`τ_c` 为注释集 c 的贡献系数。
   - 用途：评估基序实例对性状遗传力的富集。
   - 来源：Methods「LD Score Regression」节。

---

## 10 实验设计与证据链

### 数据集/群体/规模/指标/基线/预算/评测协议

- **数据集**：
  - ENCODE Phase II/III 非组蛋白 ChIP-seq：人类 249 个细胞类型、694 个 TF；小鼠 38 个细胞类型、62 个 TF；
  - HT-SELEX：两个公共数据集（参考文献 2 和 24）；
  - ENCODE Registry of cCREs V3（rDHS 集合）；
  - 1000 Genomes 群体（LD 计算）；
  - UK Biobank GWAS：红细胞分布宽度、类风湿关节炎、血清胆固醇。

- **规模**：
  - MEME 基序：6,921 个人类基序（来自 ChIP-seq）；
  - ZMotif 基序：6,700 个（来自 HT-SELEX）；
  - 峰内基序实例：110,001,176（允许重叠）；合并后 6,720,871；
  - rDHS 内基序实例：33,452,885（允许重叠）；合并后 7,189,228；其中 68.2% 不在 ChIP-seq 峰内。

- **指标**：
  - 基序覆盖率（与 HOCOMOCO/JASPAR 比较）；
  - 保守性（phyloP 100-way）；
  - DNase 保护（DNase-seq 切割位点分布）；
  - 峰中心性（基序距峰 summit 距离）；
  - LDSC 遗传力富集。

- **基线**：HOCOMOCO、JASPAR 目录；第一版 Factorbook。

- **评测协议**：无独立基准测试；通过保守性/DNase/中心性三重证据间接验证基序质量；通过 LDSC 验证功能相关性。

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| MEME 基序覆盖 | 覆盖超过现有目录 | 与 HOCOMOCO/JASPAR 比较 | 覆盖近 100% 的 HOCOMOCO/JASPAR 基序 | Factorbook 基序目录覆盖广 | 未证明覆盖所有真实 TF 基序 | Results 图 2B |
| 新基序发现 | 发现未注释的 TF 基序 | 358 个 TF 无 HOCOMOCO/JASPAR 基序 | 为 358 个 TF 提供候选基序 | 扩展了基序目录 | 未验证这些基序的功能 | Results 图 2B |
| 保守性分析 | 基序实例比非基序序列更保守 | 基序实例 vs 周围序列 phyloP | 基序实例显著更保守 | 基序实例具有进化约束 | 未区分真实结合与被动保守 | Results 图 2D |
| DNase 保护 | 基序实例受 TF 结合保护 | 基序实例 vs 非基序序列 DNase 切割 | 基序实例 DNase 切割减少 | 基序实例被蛋白结合保护 | 未直接证明是目标 TF 结合 | Results 图 2F |
| 峰中心性 | 真实基序位于峰 summit 附近 | 基序距 summit 距离分布 | 高质量基序更居中 | 基序与 ChIP-seq 峰一致 | 未排除共因子基序 | Results 图 2E |
| LDSC 富集 | 基序实例富集疾病遗传力 | 三种 GWAS 性状 × 细胞类型分层 | 疾病相关细胞类型中基序富集 | 基序实例具有功能相关性 | 未证明因果性 | Results 图 5D |
| ZMotif 基序 | CNN 可从 HT-SELEX 发现基序 | 与 MEME 基序比较 | 6,700 个基序，与 MEME 互补 | CNN 基序发现可行 | 未与 DeepBind 等 DL 方法系统比较 | Results 图 3A |

---

## 11 结论正确解读

- **任务范围**：本文是**资源构建**，而非机制发现。它不提出新的 TF–DNA 结合机制，而是提供基序目录、实例注释和工具。
- **oracle/真值输入**：ChIP-seq 峰（IDR 阈值化）和 HT-SELEX 结合序列作为「真值」；基序发现依赖这些实验数据的质量。
- **端到端状态**：非端到端。基序发现、实例扫描、功能注释是分步流水线，各步骤独立。
- **算力成本**：未报告训练 ZMotif 的具体 GPU 时间；但单卷积层 + 小批量（32） + 1000 epoch 的架构计算成本较低。
- **历史数据依赖**：依赖 ENCODE Phase II/III 数据；基序目录随 ENCODE Phase IV 数据发布将更新。
- **模型依赖**：ZMotif 的基序质量依赖 CNN 架构选择（单层、16 核、宽 24 bp）；MEME 基序依赖峰选择策略（前 500 峰）。
- **最难情形**：低表达或低占位的 TF（ChIP-seq 峰少）、长基序（>30 bp）、以及共因子干扰严重的 TF。
- **群体/领域边界**：主要覆盖人类和小鼠；其他物种需重新训练/扫描。
- **不确定性**：基序实例的假阳性率未系统评估；FIMO p 值阈值选择对结果影响大；LDSC 富集受 LD 结构影响。

**有边界的复述**：本文构建了一个覆盖 694 个人类 TF 的基序目录，其中约 100% 覆盖 HOCOMOCO/JASPAR 已知基序，并为 358 个此前无注释基序的 TF 提供候选基序；基序实例在 ChIP-seq 峰内和 cCRE/rDHS 内均有系统注释，且表现出保守性、DNase 保护和峰中心性三重证据；LDSC 分析显示基序实例在疾病相关细胞类型中富集遗传力。这些结论仅限于 ENCODE Phase II/III 数据覆盖的 TF 和细胞类型。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 数据覆盖有限 | 基序目录基于 ENCODE Phase II/III 数据，主要覆盖 5 个细胞系 | 将随 ENCODE Phase IV 数据发布更新 | Abstract 末句 |
| 基序实例可能含假阳性 | FIMO 扫描的 p 值阈值选择影响结果 | 提供多个阈值版本供用户选择 | Results 图 4B 描述 |
| 共因子干扰 | ChIP-seq 基序可能反映共结合因子而非目标 TF | 用 HT-SELEX 基序交叉验证 | Introduction 与 Results 图 3 |
| 物种限制 | 主要覆盖人类和小鼠 | 未明确说明 | 数据描述（人类 249 细胞类型、小鼠 38 细胞类型） |
| 遗传力分析仅限三种性状 | LDSC 分析仅验证了三种 UK Biobank 性状 | 提供模型下载供用户自行分析更多性状 | Tools 节 |

> 注：作者未在文中以「limitations」专节列出局限，以上为从文中可明确推断的作者承认的边界条件。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 基序覆盖率「近 100%」的声明 | 与 HOCOMOCO/JASPAR 比较可能受数据库重叠偏差影响；「覆盖」定义（最佳匹配阈值）未明确 | 覆盖率是本文核心卖点，若定义模糊则削弱结论 | 检查比较方法：是否用相同 PWM 匹配阈值？是否排除低质量基序？ | Results 图 2B 描述 |
| ZMotif 与 MEME 基序未系统比较 | 未报告 ZMotif 与 MEME 在相同数据上的基序发现性能对比（如 ROC、motif 恢复率） | 无法判断 CNN 方法是否优于传统方法 | 在相同 ChIP-seq 峰上运行 MEME 与 ZMotif，比较基序质量指标 | Methods「ZMotif」节 |
| 基序实例「三重证据」为间接验证 | 保守性、DNase 保护、峰中心性均非直接功能验证；DNase 保护可能由其他蛋白造成 | 基序实例可能含大量假阳性 | 用 CRISPR 扰动或报告基因实验验证部分基序实例 | Results 图 2D-F |
| LDSC 富集未控制共线性 | 基序实例与 DNase 峰、组蛋白标记高度重叠，LDSC 富集可能由连锁位点驱动 | 遗传力富集可能高估基序实例的独立贡献 | 在 LDSC 模型中同时纳入 DNase 峰和组蛋白标记作为协变量 | Results 图 5D |
| 未报告 ZMotif 训练细节 | 未给出训练集/验证集划分、正负样本比例、超参数搜索范围 | 影响可复现性 | 检查 GitHub 代码是否包含完整训练配置 | Methods「ZMotif」节 |
| 基序实例「68.2% 不在 ChIP-seq 峰内」的解释 | 作者解释为「可能反映未检测到的结合」，但也可能是 FIMO 假阳性 | 该数字可能高估了基序实例的生物学意义 | 对这部分实例做保守性/DNase 保护分析，看是否与峰内实例有差异 | Results 图 4B 描述 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **多源基序交叉验证策略**：ChIP-seq 基序（体内、含共因子）与 HT-SELEX 基序（体外、纯 DNA 结合）互补。在 TF–DNA 互作研究中，可设计「体内 + 体外」双通道基序发现，交叉验证降低假阳性。**迁移**：对未表征 TF，可先用 HT-SELEX 获取纯结合偏好，再用 ChIP-seq 验证体内上下文。

2. **CNN 卷积核作为可迁移基序特征**：ZMotif 将 CNN 卷积核直接导出为 HDF5，供其他模型做迁移学习初始化。**迁移**：在构建 TF–DNA 结合预测模型时，可加载 Factorbook 的卷积核作为预训练权重，而非从随机初始化开始训练。

3. **基序实例的「三重证据」质量评估框架**：保守性（phyloP）+ 染色质可及性（DNase 保护）+ 峰中心性三者联合，可区分真实 TF 结合位点与噪声。**迁移**：在预测 TF 结合位点时，可将这三个特征作为后验过滤条件，而非仅依赖序列匹配分数。

4. **基序实例与调控元件注释的整合**：将基序实例映射到 cCRE/rDHS 上，提供「功能上下文」。**迁移**：在 TF–DNA 互作研究中，不应仅报告「基序存在」，而应报告「基序位于何种调控元件中」，以推断其可能的调控角色。

5. **LDSC 分区遗传力作为功能验证手段**：用 GWAS 数据验证基序实例的疾病相关性。**迁移**：对预测的 TF 结合位点，可用 LDSC 检验其在特定性状遗传力中的富集，作为功能相关性的间接证据。

6. **基序目录的「覆盖广度」与「深度学习可用性」双维度设计**：同时提供 PWM（传统格式）和 HDF5 卷积核（深度学习格式）。**迁移**：构建任何基序资源时，应同时考虑传统格式兼容性和深度学习框架可用性。

---

## 15 与已有知识连接

1. **ENCODE 项目**（ENCODE Project Consortium, 2012; ENCODE Phase III, 2020）：本文是 ENCODE Phase II/III 的下游资源，与 ENCODE Registry of cCREs（Moore et al., 2020）直接整合。**连接**：TF–DNA 互作研究可同时使用 Factorbook 基序 + cCRE 注释。

2. **HOCOMOCO**（Kulakovskiy et al., 2018）与 **JASPAR**（Fornes et al., 2020）：本文与之比较，声称覆盖近 100% 的已知基序。**连接**：可作为基序目录的交叉验证基准。

3. **DeepBind**（Alipanahi et al., 2015）与 **DeepSEA**（Zhou & Troyanskaya, 2015）：本文的 ZMotif 属于同一类 CNN 方法，但专门用于基序发现而非预测。**连接**：ZMotif 的卷积核可作为 DeepBind/DeepSEA 类模型的预训练特征。

4. **LDSC**（Bulik-Sullivan et al., 2015）：本文使用 LDSC 进行分区遗传力分析。**连接**：TF 结合位点作为注释集，可评估其在疾病遗传力中的贡献。

5. **MEME Suite**（Bailey et al., 2009）与 **FIMO**（Grant et al., 2011）：本文的基序发现和扫描工具。**连接**：标准基序分析流程。

6. **TF 基序数据库**（UniPROBE、CisBP）：本文引用的体外基序来源。**连接**：体外基序与体内基序的互补性。

7. **候选 TF 结合位点的功能验证**（如 CRISPR 扰动、MPRA）：本文未做实验验证，但提供了候选位点资源，可作为实验设计的输入。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：基于 Factorbook 基序的 TF–DNA 结合特异性预测模型
- **名称**：Factorbook-MotifNet：融合 ChIP-seq 与 HT-SELEX 基序的 TF 结合预测
- **来源局限/观察**：Factorbook 提供双通道基序（MEME + ZMotif），但未提供统一的结合预测模型；现有模型（DeepBind 等）未充分利用双通道互补性。
- **核心假设**：融合体内（ChIP-seq）与体外（HT-SELEX）基序特征，可提高 TF 结合位点预测的准确性和可解释性。
- **初步方法**：用 Factorbook 的 HDF5 卷积核初始化 CNN，输入为 DNA 序列 + 保守性 + DNase 可及性特征，输出为结合概率；在 ENCODE ChIP-seq 峰上训练，用独立细胞系验证。
- **验证方式**：与 DeepBind、DeepSEA 在相同测试集上比较 AUROC/AUPRC；用 Factorbook 的「三重证据」位点作为正例集。
- **创新状态**：unverified

### 候选 2：基序实例的「功能上下文」分类器
- **名称**：MotifContext：基于 cCRE 类型的 TF 结合位点功能分类
- **来源局限/观察**：Factorbook 将基序实例映射到 cCRE/rDHS，但未区分不同调控元件类型（增强子/启动子/绝缘子）中基序的功能差异。
- **核心假设**：同一 TF 的基序在不同 cCRE 类型中具有不同的序列特征和染色质环境，可据此分类其功能角色。
- **初步方法**：以 Factorbook 基序实例为输入，特征包括基序序列、保守性、DNase 保护、组蛋白修饰（H3K4me1/me3、H3K27ac），用随机森林或 GNN 分类 cCRE 类型；分析不同 TF 家族的基序在增强子 vs 启动子中的偏好。
- **验证方式**：用 ENCODE 的 cCRE 类型标签作为真值；交叉验证分类准确率；与已知 TF 功能注释（如激活/抑制）对照。
- **创新状态**：unverified

### 候选 3：TF 基序的「保守性-可及性」二维景观
- **名称**：MotifLandscape：TF 结合位点的进化-染色质二维图谱
- **来源局限/观察**：Factorbook 提供保守性和 DNase 保护数据，但未系统分析二者与 TF 家族、基序强度之间的关系。
- **核心假设**：不同 TF 家族的基序在「保守性-可及性」二维空间中占据不同区域，反映其不同的结合策略（如先锋因子 vs 定居因子）。
- **初步方法**：从 Factorbook 提取所有基序实例的 phyloP 和 DNase 保护值，按 TF 家族聚类，绘制二维密度图；分析先锋因子（如 FOXA1）与定居因子（如 CTCF）的分布差异。
- **验证方式**：与已知先锋因子列表对照；用独立数据集（如 ENCODE Phase IV）验证聚类稳定性。
- **创新状态**：unverified

### 候选 4：基于 Factorbook 基序的变异效应预测
- **名称**：MotifVar：TF 基序内 SNP 的功能效应预测
- **来源局限/观察**：Factorbook 提供 SNP 注释工具，但仅报告基序匹配变化，未预测对 TF 结合亲和力的定量影响。
- **核心假设**：结合 PWM 分数变化和 ZMotif 卷积核激活变化，可更准确预测 SNP 对 TF 结合的影响。
- **初步方法**：对每个 SNP，计算参考/替代等位基因的 PWM 分数差和 ZMotif 激活差，训练逻辑回归预测 eQTL 或 ChIP-seq 等位基因不平衡（ASB）数据。
- **验证方式**：用 ENCODE ASB 数据或 GTEx eQTL 数据作为真值；与现有工具（如 FABIAN-variant、DeepSEA 效应预测）比较。
- **创新状态**：unverified

### 候选 5：跨物种 TF 基序的迁移学习
- **名称**：CrossSpeciesMotif：从人类到小鼠的 TF 基序迁移
- **来源局限/观察**：Factorbook 同时覆盖人类和小鼠 TF，但未提供跨物种基序比较或迁移工具。
- **核心假设**：同源 TF 的基序在人类和小鼠间高度保守，可用人类基序初始化小鼠模型，减少小鼠数据需求。
- **初步方法**：用人类 Factorbook 基序初始化 CNN，在小鼠 ChIP-seq 数据上微调；比较迁移学习与从头训练的性能差异。
- **验证方式**：在小鼠 ChIP-seq 峰上评估 AUROC；与同源 TF 基序相似性（TOMTOM）对照。
- **创新状态**：unverified