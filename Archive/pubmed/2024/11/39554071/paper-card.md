## 01 基本信息

- **标题**：Altered AP-1, RUNX and EGR chromatin dynamics drive fibrotic lung disease
- **作者与单位**：Valenzi, Eleanor; Jia, Minxue; Gerges, Peter; Fan, Jingyu; Tabib, Tracy; Behara, Rithika; Zhou, Yuechen; Sembrat, John; Das, Jishnu; Benos, Panayiotis V; Singh, Harinder; Lafyatis, Robert（单位未提供，推测为匹兹堡大学，依据致谢中的 University of Pittsburgh Center for Research Computing）
- **期刊/预印本平台**：bioRxiv : the preprint server for biology
- **年份**：2024（预印本发布于 2024-10-23，PubMed 收录 2024-11-18）
- **论文类型**：预印本（研究论文）
- **领域**：肺纤维化表观基因组学；单细胞多组学；转录因子-染色质互作
- **关键词**：肺纤维化、SSc-ILD、snATAC-seq、snRNA-seq、ChromBPNet、AP-1、RUNX、EGR、转录因子、染色质可及性
- **DOI/arXiv 号**：10.1101/2024.10.23.619858
- **代码**：未提供
- **数据**：未提供（文中提及数据来自 3 例 SSc-ILD + 2 例对照 snATAC/snRNA，以及 6 例 SSc-ILD + 7 例对照 multiome）
- **阅读日期**：2026-05-13（按当前日期）
- **在该方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」方向，利用 ChromBPNet（卷积神经网络）在单碱基分辨率下推断肺纤维化中成纤维细胞和巨噬细胞的 TF 结合动态变化，并结合 HALO 构建 TF-CRE-基因调控网络。对 TF–DNA 互作课题的可迁移价值在于：展示了如何将深度学习模型（ChromBPNet）应用于疾病场景下的 TF 结合位点推断，以及如何将 TF 结合变化与下游基因表达调控网络连接。

## 02 一句话总结

利用 snATAC/snRNA 多组学数据，通过深度学习模型 ChromBPNet 在单碱基分辨率下推断 SSc-ILD 肺组织中成纤维细胞和 SPP1hi 巨噬细胞的 TF 结合变化，发现 AP-1、RUNX、EGR 家族在纤维化成纤维细胞中结合增强，bHLH-ZIP 和 AP-1 在纤维化巨噬细胞中结合增强，并构建了 TF-CRE-基因调控网络。

## 03 研究问题

- **具体问题**：在系统性硬化症相关间质性肺病（SSc-ILD）中，成纤维细胞和 SPP1hi 巨噬细胞的 profibrotic 基因程序受哪些转录因子的调控？这些 TF 在染色质上的结合动态如何改变？
- **为什么重要**：肺纤维化是多种疾病的致死性特征，肌成纤维细胞和 SPP1hi 巨噬细胞是纤维化的关键驱动细胞。理解其转录调控机制可为治疗提供新靶点。
- **现有方法不足**：scRNA-seq 只能提供转录组层面的信息，无法揭示上游转录调控机制；传统 ATAC-seq 分析（如 chromVAR）只能推断 motif 富集，无法在单碱基分辨率下区分 TF 结合的具体位置和强度变化。
- **精确研究问题**：Can deep learning-based chromatin accessibility modeling (ChromBPNet) identify disease-specific TF binding dynamics at single-base resolution in fibrotic lung cell populations, and can these TF binding changes be linked to downstream gene regulatory networks?

## 04 背景与发展脉络

*注：以下脉络基于本文框架，未经外部系统核验，标注为「仅本文框架」。*

1. **阶段一：scRNA-seq 描绘纤维化细胞图谱**（~2019-2021）
   - 代表方法：scRNA-seq 聚类、DEG 分析
   - 优点：揭示细胞类型组成和转录状态变化
   - 局限：无法解释转录状态变化的调控机制
   - 代表工作：本文引用的 prior scRNA-seq 研究（ref 12-14, 36）

2. **阶段二：ATAC-seq 揭示染色质可及性变化**（~2020-2022）
   - 代表方法：snATAC-seq、chromVAR motif 活性分析
   - 优点：提供表观基因组层面的调控信息
   - 局限：chromVAR 只能给出 motif 富集分数，无法定位具体 TF 结合位点或区分结合强度
   - 本文位置：使用 chromVAR 作为初步验证（Supp Fig 4）

3. **阶段三：深度学习预测 TF 结合**（~2021-2023）
   - 代表方法：ChromBPNet（卷积神经网络）、TF-MoDISco（de novo motif 发现）
   - 优点：单碱基分辨率、可去除 Tn5 酶切偏好、可比较不同细胞状态的 TF 结合差异
   - 局限：需要高质量的伪 bulk 数据；预测结果需要实验验证
   - 本文位置：核心创新点，将 ChromBPNet 应用于疾病 vs 对照的比较

4. **阶段四：调控网络构建**（~2022-2024）
   - 代表方法：HALO（变分自编码器）、DIRECT-NFT（XGBoost 回归）、RNA velocity
   - 优点：将 TF 结合与下游基因表达连接，构建可解释的调控网络
   - 本文位置：整合以上方法构建 TF-CRE-基因网络

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| scRNA-seq 无法揭示转录调控机制 | 已知成纤维细胞和巨噬细胞亚群在纤维化中改变，但不知道哪些 TF 驱动这些变化 | 转录组反映的是调控的最终结果，而非调控过程本身 | Introduction 第 2-3 段 |
| chromVAR motif 分析分辨率有限 | 只能给出 motif 富集分数，无法定位具体结合位点 | motif 活性分数是区域级别的汇总统计，不提供单碱基分辨率信息 | Results 图 1 相关段落（Supp Fig 4） |
| Tn5 酶切偏好干扰 TF 结合推断 | 直接使用 ATAC-seq 信号会被 Tn5 序列偏好污染 | Tn5 转座酶对特定 DNA 序列有切割偏好，造成假阳性信号 | Methods: ChromBPNet Analysis 节 |
| 单细胞数据稀疏性限制调控网络构建 | 单细胞水平的 ATAC 数据过于稀疏，难以直接推断 TF-基因调控关系 | 单细胞测序深度有限，每个细胞仅覆盖基因组的一小部分 | Methods: Multi-Omics METAcell Construction 节 |
| 疾病相关 TF 结合变化难以定位到具体基因 | 需要将差异 TF 结合与下游基因表达变化连接 | 远端增强子与基因的对应关系不明确 | Results: Gene regulatory network construction 节 |

## 05 核心思想

### 1) 表面方法

对 SSc-ILD 和对照肺组织进行 snATAC/snRNA 多组学测序，使用 ChromBPNet 深度学习模型在单碱基分辨率下推断成纤维细胞和 SPP1hi 巨噬细胞中的 TF 结合，通过比较疾病与对照的 TF 结合差异，识别驱动 profibrotic 基因程序的转录因子，并利用 HALO 构建 TF-CRE-基因调控网络。

### 2) 核心洞察

- **TF 结合变化是疾病特异性的**：AP-1、RUNX、EGR 在 SSc-ILD 成纤维细胞中结合增强，而 bHLH-ZIP 和 AP-1 在 SSc-ILD 巨噬细胞中结合增强，不同细胞类型由不同 TF 驱动。
- **单碱基分辨率可揭示 motif 水平无法捕捉的动态**：ChromBPNet 的 contribution score 可以区分同一 TF 家族中不同成员的结合差异，以及疾病与对照间结合位点的重分布。
- **TF 结合变化与基因表达变化可连接**：通过构建 TF-CRE-基因网络，可以将 TF 结合变化与下游基因表达变化直接关联，如 AP-1 与 CTHRC1、ADAM12 的调控关系。

### 3) 可能的普适教训 [Analysis]

- 深度学习模型（如 ChromBPNet）可以从 ATAC-seq 数据中提取远超传统 motif 分析的信息量，尤其适用于疾病场景下 TF 结合动态的比较。
- 多组学整合（RNA + ATAC）是连接 TF 结合变化与功能后果的关键桥梁，单一组学难以建立完整的调控图景。
- 细胞类型特异性的 TF 调控分析比整体分析更能揭示疾病机制，不同细胞类型可能由不同的 TF 驱动。

## 07 方法总览

- **输入**：SSc-ILD 和对照肺组织的单细胞多组学数据（snATAC-seq + snRNA-seq），包括 3 例 SSc-ILD + 2 例对照的独立 snATAC/snRNA 数据，以及 6 例 SSc-ILD + 7 例对照的 multiome 数据
- **输出**：TF 结合图谱（单碱基分辨率 contribution scores）、TF-CRE-基因调控网络、疾病相关 TF 列表
- **主要模块**：
  1. 数据预处理与聚类（Seurat, Signac, Harmony）
  2. chromVAR motif 活性分析（初步验证）
  3. ChromBPNet 训练与 TF 结合推断（核心）
  4. TF-MoDISco de novo motif 发现与 JASPAR 注释
  5. HALO 变分自编码器构建 metacells
  6. DIRECT-NFT（XGBoost）构建 TF-CRE-基因连接
  7. RNA velocity 轨迹分析（scVelo）
  8. Milo 差异丰度分析
- **训练**：ChromBPNet 分别在 SSc 和对照的伪 bulk 数据上训练，先训练 bias 模型（非可及区域），再训练可及区域模型
- **反馈回路**：TF-CRE-基因网络构建后，通过 GWAS 位点叠加验证疾病相关性
- **文字流程**：多组学数据 → 聚类注释细胞类型 → 提取成纤维细胞和 SPP1hi 巨噬细胞亚群 → 生成伪 bulk ATAC 数据 → ChromBPNet 训练与 contribution score 计算 → TF-MoDISco motif 发现 → 比较 SSc vs 对照的 TF 结合差异 → HALO 构建 metacells → DIRECT-NFT 构建 TF-CRE-基因网络 → RNA velocity 验证细胞状态转变 → 整合 GWAS 数据验证疾病相关性

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ChromBPNet | 单碱基分辨率 TF 结合预测 | 传统 motif 分析无法定位具体结合位点；可去除 Tn5 偏好 | 输入：伪 bulk ATAC-seq BAM + peak 文件；输出：contribution scores | Results 图 3A-B；Methods: ChromBPNet Analysis | 预期影响：无法获得单碱基分辨率的 TF 结合差异，只能依赖 chromVAR 的 motif 富集分析，分辨率大幅降低 |
| TF-MoDISco | de novo motif 发现 | 识别 ChromBPNet 预测的结合位点中的序列 motif | 输入：contribution score 峰；输出：motif 共识序列 | Results 图 3B；Methods: ChromBPNet Analysis | 预期影响：无法将 contribution scores 与已知 TF motif 对应，失去生物学解释性 |
| HALO | 多组学数据整合与 metacell 构建 | 单细胞数据稀疏，需要聚合相似细胞以增强信号 | 输入：multiome RNA + ATAC 数据；输出：metacells | Methods: Multi-Omics METAcell Construction | 预期影响：无法进行稳健的轨迹分析和调控网络构建 |
| DIRECT-NFT (XGBoost) | TF-CRE-基因调控关系推断 | 将 TF 结合与基因表达连接，构建可解释的调控网络 | 输入：基因表达 + CRE 可及性；输出：TF-CRE-基因连接 | Methods: Construction of TF-CRE-Gene Linkages | 预期影响：无法将 TF 结合变化与下游基因表达变化直接关联 |
| RNA velocity | 细胞状态转变轨迹推断 | 验证肌成纤维细胞来源于成纤维细胞亚群 | 输入：spliced/unspliced RNA 计数；输出：细胞状态转变方向 | Results 图 6D, 6H | 预期影响：无法确认细胞状态转变方向，削弱调控网络的功能解释 |
| Milo | 差异丰度分析 | 识别疾病中细胞亚群丰度变化 | 输入：细胞邻域图；输出：差异丰度邻域 | Results 图 6B-C | 预期影响：无法确认疾病相关细胞亚群的统计显著性 |

## 09 关键公式符号

本文未提供明确的数学公式。核心方法 ChromBPNet 和 HALO 的数学细节在原文中未展开，仅描述为卷积神经网络和变分自编码器。因此：

**不适用**（原文未提供可提取的公式）。

## 10 实验设计与证据链

- **数据集**：
  - 3 例 SSc-ILD + 2 例对照：snATAC-seq + scRNA-seq（独立数据）
  - 6 例 SSc-ILD + 7 例对照：multiome snRNA-seq/snATAC-seq
  - 17 例 SSc-ILD + 13 例对照：scRNA-seq（来自 prior 发表数据，ref 36）
- **样本来源**：SSc-ILD 患者移植时收集的胸膜下肺组织；对照为无肺病的器官捐献者
- **指标**：chromVAR motif 活性、ChromBPNet contribution scores、DEG、DAR、TF-CRE-基因连接数
- **基线/对照**：对照肺组织（无肺病）
- **评测协议**：差异 motif 活性（logistic 回归）、差异 contribution scores（K-means 聚类）、TF-CRE-基因连接（XGBoost importance scores）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 全肺细胞聚类与注释 | 多组学数据可区分主要肺细胞类型 | 35 个聚类，基于 marker 基因 | 识别出所有主要肺细胞类型 | 数据质量可靠，可用于下游分析 | 未验证聚类稳定性 | Results 图 1A-B |
| chromVAR motif 活性分析 | 纤维化中特定 TF motif 活性改变 | SSc vs 对照，各细胞类型 | AP-1、RUNX、EGR 在成纤维细胞中富集 | 初步提示这些 TF 家族参与纤维化 | chromVAR 无法定位具体结合位点 | Results 图 2H；Supp Fig 4 |
| ChromBPNet contribution scores | 单碱基分辨率下 TF 结合在 SSc 中增强 | SSc vs 对照成纤维细胞 | AP-1、RUNX、EGR 的 contribution scores 在 SSc 中显著升高 | 这些 TF 在纤维化成纤维细胞中结合增强 | 未进行 ChIP-seq 或 CRISPR 验证 | Results 图 3B-E |
| AP-1 在 CTHRC1/ADAM12 位点的结合 | AP-1 直接调控 profibrotic 基因 | SSc vs 对照，CTHRC1 启动子上游和 ADAM12 intron 11 | 检测到强 AP-1 footprint | AP-1 可能直接调控这些基因 | 未验证功能后果 | Results 图 3H-I |
| HALO metacell 构建与轨迹分析 | 肌成纤维细胞来源于特定成纤维细胞亚群 | RNA velocity 预测 | 肌成纤维细胞来源于肺泡和血管周围成纤维细胞 | 支持肌成纤维细胞分化轨迹 | 未进行谱系追踪实验 | Results 图 6D |
| TF-CRE-基因网络构建 | 可识别疾病相关的调控回路 | SSc vs 对照，整合 DEG 和 DAR | AP-1、EGR、YY1、ETS 家族连接最多 DEG | 这些 TF 是 profibrotic 程序的核心调控因子 | 网络为计算预测，未实验验证 | Results 图 6E；Supp Table 4-5 |
| SSc 成纤维细胞中 AP-1 连接基因 | AP-1 调控的基因与纤维化相关 | 243 个上调基因连接 AP-1 | 包括 CTHRC1、ADAM12、IGFBP2、SPP1、TGFBI | AP-1 调控 profibrotic 基因程序 | 未验证因果关系 | Results 图 6 相关段落 |
| SPP1hi 巨噬细胞中 bHLH-ZIP 结合 | bHLH-ZIP 调控巨噬细胞 profibrotic 程序 | SSc vs 对照 SPP1hi 巨噬细胞 | TFEB、MXI1 连接 64 个 DEG，包括 CHIT1、CHI3L1、MMP7 | bHLH-ZIP 是巨噬细胞 profibrotic 程序的关键调控因子 | 未验证 TFEB/MXI1 的直接结合 | Results 图 6I；Supp Table 5 |

## 11 结论正确解读

- **任务范围**：本文仅覆盖 SSc-ILD 终末期肺组织（移植样本），不涵盖早期/轻度纤维化或其他类型 ILD（如 IPF 的独立验证）。
- **oracle/真值输入**：ChromBPNet 的 contribution scores 是计算预测，未用 ChIP-seq 或 CRISPR 实验验证；TF-CRE-基因连接基于计算推断，非实验验证的调控关系。
- **端到端状态**：从数据到 TF 结合推断到网络构建的流程是端到端的计算流程，但未进行任何湿实验验证。
- **算力成本**：未提供训练 ChromBPNet 和 HALO 的具体算力需求。
- **历史数据依赖**：DEG 分析部分依赖 prior 发表的 scRNA-seq 数据（ref 36），该数据集的批次效应可能影响结果。
- **模型依赖**：结果高度依赖 ChromBPNet 的预测准确性；不同深度学习架构可能产生不同结果。
- **最难情况**：RUNX 结合位点数量少但变化显著，可能代表稀有但关键的调控事件；TEAD 结合在 SSc 和对照间差异较小，提示并非所有 profibrotic TF 都表现出显著结合变化。
- **群体/领域边界**：结论仅适用于 SSc-ILD 的终末期肺纤维化，不能推广到其他纤维化疾病或早期阶段。
- **不确定性**：作者未提供 contribution scores 的置信区间或统计检验的效应量；TF 家族内成员（如 AP-1 的 JUN vs JUNB vs JUND）无法通过 motif 分析区分。

**有边界的复述**：在 SSc-ILD 终末期肺组织中，成纤维细胞和 SPP1hi 巨噬细胞表现出 AP-1、RUNX、EGR（成纤维细胞）和 bHLH-ZIP、AP-1（巨噬细胞）的染色质结合增强，这些 TF 结合变化与 profibrotic 基因表达程序相关，但该结论基于计算预测，未经实验验证，且仅适用于所分析的终末期 SSc-ILD 样本。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 样本量有限 | 仅 3 例 SSc-ILD + 2 例对照（snATAC），6 例 SSc-ILD + 7 例对照（multiome） | 未明确提及 | Methods 节（样本数） |
| 疾病阶段局限 | 仅包含终末期移植肺组织，不反映早期/轻度疾病 | 未明确提及 | Discussion 节（"explanted tissue from patients with severe SSc-ILD"） |
| 无法区分 TF 家族成员 | AP-1、RUNX、EGR 家族内多个成员共享相似 motif，无法确定具体哪个 TF 结合 | 未明确提及 | Discussion 节（"Because these TFs share the same consensus motif, we cannot clearly distinguish which is most important"） |
| 计算预测未经实验验证 | ChromBPNet 预测的 TF 结合和 TF-CRE-基因连接未用 ChIP-seq、CRISPR 或报告基因实验验证 | "This knowledge could guide the development of targeted therapeutics"（暗示需要功能验证） | Discussion 节 |
| OCR 注释可能不准确 | OCR 按最近距离注释到基因，可能不反映真实调控关系 | 未明确提及 | Methods 节（"annotated by least base-pairs distance"） |
| 未纳入其他调控机制 | 未分析组蛋白修饰、DNA 甲基化、长非编码 RNA 等 | 提及 "additional non-coding regulatory mechanisms including long non-coding RNAs, microRNAs, and transposable elements may also influence gene expression" | Discussion 节 |

**作者提及的相关约束**（非正式局限）：研究使用 explanted 组织，可能受器官捐献者临床特征（如机械通气时间、缺血时间）影响；部分样本进行了成纤维细胞富集处理，可能引入选择偏差。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| ChromBPNet 训练数据量有限 | 每个细胞状态的伪 bulk 数据来自少量样本（3-6 例），深度学习模型可能过拟合 | 影响 TF 结合预测的泛化性 | 使用独立数据集验证；交叉验证 | Methods: ChromBPNet Analysis 节 |
| 未进行 ChIP-seq 验证 | contribution scores 是计算预测，可能包含假阳性 | 核心结论（AP-1/RUNX/EGR 结合增强）可能不成立 | 对 CTHRC1、ADAM12 等位点进行 ChIP-qPCR 或 CUT&Tag | Results 图 3H-I |
| TF 家族成员无法区分 | AP-1 家族包含 JUN、JUNB、JUND、FOS、FOSL1 等，功能可能相反 | 治疗靶点不明确 | 使用家族成员特异性抗体进行 ChIP-seq；或使用 siRNA 敲低单个成员 | Discussion 节（作者自认） |
| 相关性不等于因果性 | TF 结合增强可能与基因表达变化相关，但不一定是驱动因素 | 影响对疾病机制的理解 | 在体外或动物模型中敲低/过表达候选 TF，观察 profibrotic 基因表达变化 | Results 图 6E |
| 样本选择偏差 | 移植肺组织来自终末期患者，可能受免疫抑制治疗影响 | 结果可能不反映自然病程 | 纳入早期/轻度 ILD 样本；动物模型验证 | Methods 节（样本来源） |
| OCR 注释策略可能误导 | 最近距离注释可能将增强子错误分配给非目标基因 | 影响 TF-CRE-基因网络的准确性 | 使用 Hi-C 或 CRISPR 干扰验证增强子-基因连接 | Methods 节（"annotated by least base-pairs distance"） |
| 未报告 contribution scores 的统计检验细节 | 差异 contribution scores 的显著性阈值和多重检验校正未明确 | 可能包含假阳性 | 检查补充材料中的统计细节 | Results 图 3B-E |
| GWAS 叠加分析未详细说明 | 仅提及将 GWAS 位点叠加到网络，未说明具体方法和显著性 | 影响疾病相关性的可信度 | 检查补充材料中的 GWAS 分析方法 | Methods: Construction of TF-CRE-Gene Linkages 节 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **ChromBPNet 应用于疾病场景的完整流程**：从伪 bulk ATAC-seq 生成 → bias 模型训练 → contribution score 计算 → TF-MoDISco motif 发现 → 疾病 vs 对照比较。可迁移到任何 TF–DNA 互作研究，尤其适用于缺乏 ChIP-seq 数据的疾病组织。
2. **多组学整合策略**：将 snATAC（TF 结合）与 snRNA（基因表达）通过 metacell 框架（HALO）整合，构建 TF-CRE-基因调控网络。对 TF–DNA 互作课题的启示：单细胞 ATAC 数据稀疏性可通过 metacell 聚合解决。
3. **TF 家族内成员区分的挑战**：共享 motif 的 TF 家族成员（如 AP-1）无法通过序列 motif 区分，需要结合表达数据（如 RNA 层面的 TF 表达量）或蛋白互作数据来推断具体成员。
4. **疾病特异性的 TF 结合重分布**：本文展示了同一 TF 家族在不同细胞类型和疾病状态下的结合位点重分布，提示 TF–DNA 互作研究不应只关注 motif 富集，还应关注结合位点的位置变化。
5. **计算预测与实验验证的差距**：本文所有结论基于计算预测，未进行实验验证。对课题的启示：计算预测的 TF 结合变化需要 ChIP-seq/CUT&Tag 或报告基因实验验证。
6. **细胞类型特异性的调控分析**：不同 profibrotic 细胞类型（成纤维细胞 vs 巨噬细胞）由不同 TF 驱动，提示 TF–DNA 互作研究应关注细胞类型特异性，而非整体分析。

## 15 与已有知识连接

- **相似工作**：本文与 IPF 领域的 scRNA-seq 研究（ref 12-14）和 SSc 皮肤纤维化的 ATAC-seq 研究（ref 26, 48）在方法上相似，但本文首次将 ChromBPNet 应用于肺纤维化疾病组织。
- **方法来源**：ChromBPNet 来自 ENCODE 项目（Brenton et al.），本文是其疾病应用的代表性工作。
- **TF 与纤维化的已知联系**：AP-1（特别是 Fra-2/JUNB）在纤维化中的作用已有较多文献支持（ref 40-43）；RUNX1 在肌成纤维细胞分化中的作用也有报道（ref 47）；EGR1 在 TGF-β 信号通路中的作用已有研究（ref 59-62）。本文将这些已知联系整合到统一的调控网络框架中。
- **可迁移领域**：本文的方法流程（ChromBPNet + HALO + DIRECT-NFT）可迁移到其他纤维化疾病（肾、肝、心）或其他涉及 profibrotic 细胞转化的疾病。
- **与 AI 方法的关系**：本文属于「深度学习预测 TF 结合」方向，与 AlphaFold 等结构预测方法互补——前者关注序列层面的结合，后者关注结构层面的互作。
- **潜在冲突**：本文未发现 AP-1 结合位点邻近的其他 TF motif 共富集，与某些研究中 AP-1 与 SMAD 共结合的观点不完全一致，可能需要进一步分析。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF 结合动态的跨纤维化器官比较
   - **来源局限/观察**：本文仅覆盖肺纤维化，但 profibrotic 程序在肾、肝、心纤维化中可能共享
   - **核心假设**：AP-1/RUNX/EGR 调控的 profibrotic 程序在不同器官纤维化中保守
   - **增量**：将本文的 ChromBPNet 流程应用于多器官纤维化数据，识别保守的 TF 调控模块
   - **初步方法**：收集肾、肝、心纤维化的 snATAC 数据，重复本文分析流程，比较 TF 结合变化的重叠
   - **验证方式**：跨器官的 TF-CRE-基因网络重叠分析；保守增强子的报告基因验证
   - **创新状态**：unverified

2. **候选名称**：AP-1 家族成员的功能分化解析
   - **来源局限/观察**：本文无法区分 AP-1 家族成员（JUN vs JUNB vs JUND vs FOS 等），但不同成员可能功能相反
   - **核心假设**：不同 AP-1 成员在纤维化成纤维细胞中结合不同的基因组位点，发挥不同功能
   - **增量**：结合 TF 表达量（RNA）和蛋白互作数据，推断具体结合的 AP-1 成员
   - **初步方法**：使用 JASPAR 中不同 AP-1 成员的偏好 motif 变体进行分层分析；结合 scRNA-seq 中 TF 表达量进行加权
   - **验证方式**：对候选成员进行 ChIP-seq 或 CUT&Tag 验证；siRNA 敲低后检测 profibrotic 基因表达
   - **创新状态**：unverified

3. **候选名称**：TF 结合变化的因果性验证——CRISPR 增强子编辑
   - **来源局限/观察**：本文的 TF-CRE-基因连接为计算预测，未验证因果关系
   - **核心假设**：编辑 AP-1/RUNX/EGR 结合位点（如 CTHRC1 增强子）可改变 profibrotic 基因表达
   - **增量**：提供 TF 结合与基因调控的因果证据
   - **初步方法**：选择本文鉴定的关键增强子，使用 CRISPR-Cas9 删除或突变 TF 结合 motif，检测靶基因表达变化
   - **验证方式**：报告基因实验；原代肺成纤维细胞中的增强子编辑
   - **创新状态**：unverified

4. **候选名称**：TF 结合 motif 的碱基分辨率突变效应预测
   - **来源局限/观察**：ChromBPNet 提供单碱基 contribution scores，但未系统分析 motif 内单碱基突变对结合的影响
   - **核心假设**：motif 内特定位置的碱基突变可显著改变 TF 结合，影响 profibrotic 基因表达
   - **增量**：将 contribution scores 与疾病相关 SNP 关联，识别功能性 SNP
   - **初步方法**：对本文鉴定的关键 TF 结合位点进行 in silico 饱和突变分析，预测突变对 contribution scores 的影响；与 GWAS 和 eQTL 数据交叉
   - **验证方式**：EMSA 或报告基因实验验证预测的功能性突变
   - **创新状态**：unverified

5. **候选名称**：TF 协同结合的序列语法解析
   - **来源局限/观察**：本文发现 AP-1 结合位点呈「孤岛」分布，未发现邻近 motif 共富集，但 TF 协同结合是常见机制
   - **核心假设**：AP-1 与 RUNX/EGR 的协同结合需要特定的序列间距和方向
   - **增量**：解析 profibrotic 增强子的序列语法，为预测 TF 协同结合提供规则
   - **初步方法**：对本文鉴定的 AP-1/RUNX/EGR 共结合位点进行间距和方向分析；使用 TF-MoDISco 的 motif 间距信息
   - **验证方式**：合成增强子报告基因实验，系统改变 motif 间距和方向
   - **创新状态**：unverified