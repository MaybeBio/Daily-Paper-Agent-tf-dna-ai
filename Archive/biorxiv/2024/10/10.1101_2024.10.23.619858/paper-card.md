## 01 基本信息

- **标题**：Altered AP-1, RUNX and EGR chromatin dynamics drive fibrotic lung disease
- **作者**：Valenzi E; Jia M; Gerges P; Fan J; Tabib T; Behara R; Zhou Y; Sembrat J; Das J; Benos PV; Singh H; Lafyatis R
- **单位**：University of Pittsburgh（匹兹堡大学，据致谢与基金信息推断）；具体单位列表未提供
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2024
- **论文类型**：预印本（研究论文）
- **领域**：肺纤维化表观基因组学；单细胞多组学；转录因子调控网络
- **关键词**：肺纤维化、SSc-ILD、snATAC-seq、snRNA-seq、ChromBPNet、AP-1、RUNX、EGR、转录因子、染色质可及性
- **DOI/ID**：10.1101/2024.10.23.619858
- **代码**：未提供
- **数据**：未提供（原始测序数据未给出存取号）
- **阅读日期**：2026-05-12（按当前日期）
- **在该课题方向中的位置**：本文属于「蛋白质-DNA互作（TF–DNA结合机制）× AI/深度学习」方向，核心是利用深度学习工具 ChromBPNet 在体内（人肺组织）单细胞分辨率下推断 TF 结合动态，并结合 HALO 构建 TF-CRE-基因调控网络。对 TF–DNA 结合机制研究而言，本文提供了一个「从染色质可及性数据推断 TF 结合变化」的完整分析流程，可迁移至其他疾病或细胞类型。

## 02 一句话总结

利用 snATAC/snRNA 多组学数据，通过深度学习模型 ChromBPNet 在单碱基分辨率下推断肺纤维化（SSc-ILD）中成纤维细胞和巨噬细胞的 TF 结合变化，发现 AP-1、RUNX、EGR 在肌成纤维细胞中结合增强、C/EBP 结合减弱，并构建了 TF-CRE-基因调控网络，揭示这些 TF 驱动促纤维化基因程序。

## 03 研究问题

- **具体问题**：在系统性硬化症相关间质性肺病（SSc-ILD）中，成纤维细胞向肌成纤维细胞转化以及 SPP1^hi 巨噬细胞的促纤维化表型，是由哪些转录因子通过怎样的染色质动态变化来驱动的？
- **为什么重要**：肺纤维化是多种疾病的致死性结局，肌成纤维细胞和 SPP1^hi 巨噬细胞是核心驱动细胞。理解其转录调控机制有助于发现新的治疗靶点。现有 scRNA-seq 研究虽已描绘细胞状态变化，但无法解释这些状态转变背后的转录调控逻辑。
- **现有方法为何不足**：scRNA-seq 仅提供基因表达信息，无法直接反映 TF 在顺式调控元件上的结合活性；传统 motif 富集分析（如 chromVAR）只能提供相对活性评分，缺乏单碱基分辨率的结合位置信息，也无法区分同一 TF 家族内不同成员的贡献。
- **精确研究问题**：Can deep learning-based chromatin accessibility modeling (ChromBPNet) identify disease-specific TF binding changes at single-base resolution in fibrotic lung cell populations, and can these changes be linked to profibrotic gene programs via TF-CRE-gene networks?

## 04 背景与发展脉络

**注：以下脉络为「经外部核验」的领域发展主线，结合本文引用与领域常识。**

1. **阶段一：scRNA-seq 描绘纤维化细胞图谱**（~2019-2021）
   - 代表方法：单细胞转录组测序，如 Habermann et al. (2020) 对 IPF 的 scRNA-seq 分析
   - 优点：高分辨率识别细胞亚群，发现肌成纤维细胞和 SPP1^hi 巨噬细胞
   - 局限：无法直接推断上游转录调控机制

2. **阶段二：snATAC-seq 揭示染色质可及性**（~2020-2022）
   - 代表方法：单细胞 ATAC-seq 结合 chromVAR motif 活性分析
   - 优点：提供顺式调控元件的开放状态信息
   - 局限：chromVAR 只能给出 motif 活性的相对变化，无法定位具体结合位点，分辨率有限

3. **阶段三：深度学习预测 TF 结合**（~2021-2023）
   - 代表方法：ChromBPNet (Bhattacharyya et al. 2021)、BPNet 等基于卷积神经网络的模型
   - 优点：从 DNA 序列和 ATAC-seq 切割模式学习 TF 结合规则，可生成单碱基分辨率的贡献分数，并去除 Tn5 酶切偏好
   - 局限：需要足够的测序深度；对罕见细胞类型可能不适用

4. **阶段四：多组学整合与调控网络构建**（~2023-2024）
   - 代表方法：HALO（层次变分自编码器）、DIRECT-NET（XGBoost 回归）
   - 优点：整合 RNA 和 ATAC 数据，构建 TF-CRE-基因三元调控关系
   - 局限：网络为推断性质，需要实验验证

**本文主张的位置**：本文处于阶段三与阶段四的交汇点，首次将 ChromBPNet 应用于人肺纤维化组织，在单碱基分辨率下刻画疾病相关的 TF 结合动态，并结合 HALO 构建 TF-CRE-基因网络，是该技术路线在纤维化疾病中的首次系统应用。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| scRNA-seq 无法揭示转录调控机制 | 已知肌成纤维细胞和 SPP1^hi 巨噬细胞驱动纤维化，但不知道哪些 TF 控制其促纤维化基因程序 | 基因表达是调控的最终结果，不包含 TF 结合信息 | Introduction 第 2-3 段 |
| chromVAR motif 活性分析分辨率有限 | 只能给出 motif 活性的相对变化，无法定位具体结合位点 | chromVAR 基于 motif 在可及区域中的出现频率，不建模序列-染色质关系 | Results 图 1H；Methods "ChromBPNet Analysis" 节 |
| Tn5 酶切偏好干扰 TF 足迹分析 | 直接分析 ATAC-seq 切割模式会被 Tn5 序列偏好污染 | Tn5 转座酶本身有 DNA 序列偏好，产生非生物学信号 | Methods "ChromBPNet Analysis" 节 |
| 单细胞数据稀疏性限制调控推断 | 单个细胞的 ATAC-seq 数据极其稀疏，难以直接分析 | 每个细胞仅捕获少量可及位点 | Methods "Multi-Omics METAcell Construction" 节（使用 METAcells 聚合） |
| 无法区分 TF 家族内不同成员 | AP-1 家族包含多个成员（Jun、Fos、ATF、Maf），共享相似 motif | 同家族 TF 的 DNA 结合域高度相似，motif 几乎相同 | Results "Enhanced binding of AP-1, RUNX and EGR..." 节 |
| 从 TF 结合变化到靶基因的映射缺失 | 知道 TF 结合位点，但不知道调控哪些基因 | 需要将 TF 结合位点与基因表达变化关联 | Results "Gene regulatory network construction" 节 |

## 06 核心思想

### 1) 表面方法

对 SSc-ILD 和正常供体肺组织进行 snATAC/snRNA 多组学测序，使用 ChromBPNet 深度学习模型在单碱基分辨率下推断成纤维细胞和巨噬细胞中的 TF 结合，通过 TF-MoDISco 进行 de novo motif 发现，结合 HALO 构建 TF-CRE-基因调控网络。

### 2) 核心洞察

**TF 结合动态变化而非简单的表达变化驱动纤维化表型**。具体而言：
- AP-1、RUNX、EGR 家族在 SSc-ILD 成纤维细胞中结合增强，C/EBP 结合减弱，这种「结合重分布」而非「表达量变化」是驱动促纤维化基因程序的关键机制。
- 同一 TF 家族内部存在异质性：AP-1 的不同结合位点簇在疾病中变化方向不同（部分增强、部分不变），提示不同 AP-1 二聚体组合或远端调控机制参与。
- TF 结合位点呈现「岛状」分布，而非与邻近 TF 协同结合，提示远端染色质互作（如 DNA loop）可能比局部 TF 协同更重要。

### 3) 可能的普适教训 [Analysis]

- **深度学习模型可以从染色质可及性数据中提取远超传统 motif 分析的信息**：ChromBPNet 的单碱基分辨率贡献分数能够区分同一家族内不同结合位点的动态变化，这是 chromVAR 等传统方法无法实现的。
- **「结合变化」与「表达变化」是不同维度的调控信息**：在研究 TF 功能时，仅关注表达量可能遗漏关键调控事件；结合位点的染色质动态变化可能更直接地反映 TF 功能状态。
- **体内（ex vivo）单细胞多组学是研究 TF 结合机制的重要补充**：相较于体外实验（如 ChIP-seq 或 HT-SELEX），该方法能在原代组织、疾病状态下直接推断 TF 结合变化，具有更高的生理相关性。

## 07 方法总览

- **输入**：
  - 人肺组织（SSc-ILD 和正常供体）的配对 snATAC-seq 和 snRNA-seq 数据
  - 独立 scRNA-seq 数据集（17 SSc-ILD、13 对照，来自先前发表研究）
  - GWAS 位点数据（用于网络叠加）

- **输出**：
  - 单碱基分辨率的 TF 结合贡献分数图谱
  - 疾病相关的 TF 结合变化（增强/减弱）
  - TF-CRE-基因调控网络

- **模块**：
  1. **数据预处理与聚类**：Seurat、Signac、Harmony 进行批次校正和细胞类型注释
  2. **ChromBPNet 训练**：在非可及区域训练 Tn5 偏好模型，冻结后在可及区域训练主模型，生成贡献分数
  3. **TF-MoDISco 分析**：从贡献分数中提取 de novo motif，用 JASPAR 注释
  4. **HALO 变分自编码器**：推断 RNA/ATAC 联合潜在表征，构建 METAcells
  5. **DIRECT-NET（XGBoost）**：回归基因表达对远端 CRE 可及性，筛选 CRE-基因关联
  6. **调控网络构建**：整合 TF motif、CRE 可及性、基因表达，构建 TF-CRE-基因三元关系

- **训练**：ChromBPNet 分别在四个细胞状态（SSc 成纤维细胞、对照成纤维细胞、SSc SPP1^hi 巨噬细胞、对照 SPP1^hi 巨噬细胞）的伪批量数据上训练

- **反馈回路**：无显式闭环反馈；分析流程为单向流水线

- **文字流程**：
  1. 对 snATAC/snRNA 数据进行质控、聚类、注释
  2. 提取成纤维细胞和 SPP1^hi 巨噬细胞的伪批量 ATAC 数据
  3. 训练 ChromBPNet 模型，生成单碱基贡献分数
  4. 用 TF-MoDISco 发现 de novo motif 并注释
  5. 比较 SSc 与对照的 TF 结合差异
  6. 用 HALO 构建 METAcells，用 DIRECT-NET 识别 CRE-基因关联
  7. 整合 TF-CRE-基因，构建调控网络并叠加 GWAS 信息

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ChromBPNet | 从 ATAC-seq 数据推断单碱基分辨率 TF 结合贡献分数 | 传统 motif 分析无法定位具体结合位点，且受 Tn5 偏好干扰 | 输入：伪批量 ATAC-seq BAM + peak 文件；输出：贡献分数图谱 | Results 图 3A-H；Methods "ChromBPNet Analysis" 节 | 预期影响：失去单碱基分辨率，无法区分同一家族内不同结合位点的动态变化 [预期效应] |
| TF-MoDISco | 从贡献分数中提取 de novo motif | 需要无偏发现 TF 结合基序，而非仅依赖已知 motif 数据库 | 输入：贡献分数图谱；输出：motif 序列及注释 | Results 图 3B；Methods "ChromBPNet Analysis" 节 | 预期影响：无法发现未知 motif 或变体 [预期效应] |
| HALO | 推断 RNA/ATAC 联合潜在表征，构建 METAcells | 单细胞数据稀疏，需要聚合相似细胞状态以提高信噪比 | 输入：配对 RNA/ATAC 矩阵；输出：METAcells 及潜在表征 | Methods "Multi-Omics METAcell Construction" 节 | 预期影响：失去统计功效，无法进行稳健的轨迹分析 [预期效应] |
| DIRECT-NET (XGBoost) | 回归基因表达对远端 CRE 可及性，筛选 CRE-基因关联 | 需要将 TF 结合位点与靶基因关联，构建调控网络 | 输入：基因表达 + CRE 可及性；输出：CRE-基因重要性评分 | Methods "Construction of TF-CRE-Gene Linkages" 节 | 预期影响：无法建立 TF-CRE-基因三元关系 [预期效应] |
| chromVAR | 计算 motif 活性评分 | 提供 TF 活性的初步概览，与 ChromBPNet 结果互补 | 输入：peak 矩阵 + motif 注释；输出：motif 活性评分 | Results 图 1H、4D | 预期影响：失去 TF 活性的全局概览 [预期效应] |
| RNA velocity (scVelo) | 推断细胞状态转变方向 | 验证肌成纤维细胞来源于成纤维细胞亚群 | 输入：spliced/unspliced 计数；输出：速度向量 | Results 图 6D、6H | 预期影响：无法确认细胞分化轨迹 [预期效应] |

## 09 关键公式符号

本文为方法应用型论文，未给出新的数学公式。以下为方法内在的、理解结果所必需的公式概念：

1. **ChromBPNet 贡献分数（contribution scores）**：
   - 概念：对输入序列每个碱基的梯度 × 输入值（gradient × input），衡量该碱基对预测染色质可及性的贡献
   - 符号：设模型输出为 y（可及性概率），输入序列为 x，则贡献分数 c_i = x_i × ∂y/∂x_i
   - 用途：定位对染色质开放状态起关键作用的碱基，即 TF 结合位点
   - 直觉：正值表示该碱基促进开放，负值表示抑制
   - 来源：Methods "ChromBPNet Analysis" 节；引用 Bhattacharyya et al. 2021

2. **Tn5 偏差校正**：
   - 概念：ChromBPNet 先在非可及区域学习 Tn5 切割偏好，再从可及区域信号中减去该偏好
   - 符号：校正后信号 = 原始信号 − Tn5 偏好模型输出
   - 用途：去除酶切偏好对 TF 足迹的干扰
   - 来源：Methods "ChromBPNet Analysis" 节

3. **TF-CRE 关联的 motif 匹配**：
   - 概念：在贡献分数峰值区域内扫描 JASPAR motif，匹配的 motif 视为候选 TF 结合位点
   - 符号：匹配得分基于 position weight matrix (PWM) 的对数似然比
   - 来源：Methods "Construction of TF-CRE-Gene Linkages" 节

4. **XGBoost 回归（DIRECT-NET）**：
   - 概念：以 CRE 可及性为特征，基因表达为标签，训练梯度提升树回归模型
   - 符号：ŷ = Σ_k f_k(x)，其中 f_k 为第 k 棵决策树
   - 用途：评估 CRE 对基因表达的预测重要性，筛选 CRE-基因关联
   - 来源：Methods "Construction of TF-CRE-Gene Linkages" 节

## 10 实验设计与证据链

**数据集与资源**：
- 人肺组织：3 例 SSc-ILD + 2 例对照（snATAC-seq 单独数据集）；6 例 SSc-ILD + 7 例对照（多组学数据集）
- 独立 scRNA-seq 数据集：17 例 SSc-ILD + 13 例对照（来自先前发表研究，引用 36）
- 测序平台：Illumina NovaSeq 6000
- 分析工具：CellRanger ATAC v2.0.0、CellRanger Arc v2.0.2、Seurat、Signac、Harmony、ChromBPNet、TF-MoDISco、HALO、DIRECT-NET、scVelo、Milo

**评测指标**：
- 差异可及性：logistic 回归检验，FDR 校正
- 差异表达：Wilcoxon 秩和检验，Bonferroni FDR 校正
- motif 活性差异：logistic 回归，以 peak 片段数和 MACS2 peak 片段数为潜在变量
- 贡献分数差异：SSc 与对照的聚合贡献分数比较

**实验表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| 全肺细胞图谱构建 | 多组学可识别主要肺细胞类型 | 35 个聚类，基于基因表达和启动子可及性 | 识别出所有主要肺细胞类型，成纤维细胞和巨噬细胞亚群清晰 | 数据质量足以进行下游分析 | 未验证聚类生物学意义的独立实验 | Results 图 1A-D |
| 成纤维细胞差异可及性分析 | SSc-ILD 成纤维细胞存在广泛染色质重塑 | SSc vs 对照成纤维细胞，6,002 个 peak 更可及、6,693 个更不可及 | 大量差异可及区域，富集于促纤维化基因附近 | 染色质重塑是纤维化成纤维细胞的核心特征 | 未证明因果关系 | Results 图 2E-F |
| chromVAR motif 活性分析 | 特定 TF 家族在 SSc 成纤维细胞中活性改变 | SSc vs 对照，logistic 回归 | AP-1、RUNX、EGR 活性增加，C/EBP 活性降低 | 这些 TF 家族参与纤维化调控 | chromVAR 无法区分家族内成员 | Results 图 2H |
| ChromBPNet 贡献分数分析 | TF 结合在单碱基分辨率下发生疾病相关变化 | SSc vs 对照成纤维细胞，比较贡献分数 | AP-1 结合增强于 CTHRC1、ADAM12 等促纤维化基因；RUNX、EGR 类似 | TF 结合动态变化驱动促纤维化基因程序 | 未用 ChIP-seq 等正交方法验证结合 | Results 图 3A-I |
| AP-1 结合位点聚类 | AP-1 结合变化具有位点特异性 | K-means 聚类贡献分数模式 | 部分簇在 SSc 中增强，部分不变或减弱 | AP-1 调控具有位点特异性，非全局性 | 未鉴定具体 AP-1 二聚体组成 | Results 图 3D-E |
| 巨噬细胞 ChromBPNet 分析 | SPP1^hi 巨噬细胞存在独特 TF 结合程序 | SSc vs 对照 SPP1^hi 巨噬细胞 | bHLH-ZIP、AP-1、EGR 结合增强 | 巨噬细胞促纤维化程序由这些 TF 驱动 | 未验证 bHLH-ZIP 具体成员 | Results 图 5A-J |
| HALO + DIRECT-NET 网络构建 | 可构建 TF-CRE-基因调控网络 | 多组学 METAcells + XGBoost 回归 | 构建了成纤维细胞和巨噬细胞的 TF-CRE-基因网络 | 网络提供了 TF 到靶基因的调控路径 | 网络为推断性质，未实验验证 | Results 图 6A-I |
| RNA velocity 分析 | 肌成纤维细胞来源于特定成纤维细胞亚群 | scVelo 动态模型 | 肌成纤维细胞来源于肺泡和血管周围成纤维细胞 | 支持肌成纤维细胞的多来源模型 | 速度分析为推断性质 | Results 图 6D |

## 11 结论正确解读

- **任务范围**：本文仅覆盖 SSc-ILD 终末期肺移植组织，不涵盖早期/轻度疾病或其他类型肺纤维化（如 IPF 的独立验证）。
- **oracle/真值输入**：TF 结合推断基于 ChromBPNet 模型预测，未用 ChIP-seq、CUT&Tag 等实验方法进行正交验证。模型预测的「结合」是计算推断，非直接实验证据。
- **端到端状态**：分析流程为「数据 → 推断 → 网络构建」，未进行功能实验（如 TF 敲低/过表达、报告基因实验）验证因果性。
- **算力成本**：未报告训练 ChromBPNet 的具体算力需求。
- **历史数据依赖**：依赖先前发表的 scRNA-seq 数据集（17 SSc-ILD + 13 对照）进行差异表达分析，该数据集的批次效应可能影响结果。
- **最难情形**：RUNX 结合位点数量较少（"small number of seqlets"），统计功效有限；bHLH-ZIP 家族成员共享 motif，无法区分具体 TF。
- **群体/领域边界**：结论限于人肺组织；皮肤纤维化（SSc 皮肤）中 AP-1 的作用已有报道，但本文未做跨组织验证。
- **不确定性**：作者未提供置信区间或效应量；差异可及性和结合变化的生物学意义需要功能验证。

**有边界的复述**：在 SSc-ILD 终末期肺组织中，成纤维细胞和 SPP1^hi 巨噬细胞存在广泛的染色质可及性改变；基于 ChromBPNet 的计算推断表明，AP-1、RUNX、EGR 家族 TF 在促纤维化基因位点的结合增强，C/EBP 结合减弱；这些变化可通过 TF-CRE-基因网络与差异表达基因关联。该结论限于计算推断层面，未经实验验证。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 样本量小且为终末期疾病 | 组织来自移植患者，可能不代表早期/轻度疾病 | 未明确说明 | Discussion 第 1 段（"may not reflect changes in mild disease"） |
| 基因注释的近似性 | OCR 按最近距离注释到基因，可能不反映真实调控关系 | 未明确说明 | Discussion 第 2 段（"not all annotations may reflect the regulated gene"） |
| 未覆盖非编码调控机制 | lncRNA、miRNA、转座子等未纳入分析 | 未明确说明 | Discussion 第 2 段 |
| 无法区分 TF 家族内成员 | bHLH-ZIP 等家族共享 motif，无法确定具体 TF | 未明确说明 | Results 图 5 相关段落 |
| 缺乏功能验证 | 未进行实验验证 TF 结合的功能后果 | 未明确说明 | 全文未提及功能实验 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| ChromBPNet 预测的 TF 结合未用 ChIP-seq 验证 | 模型预测可能存在假阳性；结合变化可能反映染色质可及性变化而非 TF 结合变化 | 核心结论依赖该预测的准确性 | 对 CTHRC1、ADAM12 等位点进行 ChIP-qPCR 或 CUT&Tag 验证 | Methods "ChromBPNet Analysis" 节；Results 图 3H-I |
| AP-1 结合增强与基因表达上调的因果关系未建立 | 可能是染色质开放导致 TF 结合增加（被动），而非 TF 驱动开放（主动） | 影响治疗靶点的选择 | 使用 AP-1 抑制剂或敲低实验观察染色质可及性和基因表达变化 | Results 图 3；Discussion 引用 AP-1 抑制剂研究 |
| 样本量小（3+2 和 6+7） | 个体间异质性可能驱动部分差异；统计功效有限 | 结论的普适性存疑 | 扩大样本量或使用独立队列验证 | Methods 数据描述 |
| RUNX 结合位点数量少 | 统计功效不足，可能为假阳性 | RUNX 是本文重点结论之一 | 增加测序深度或使用靶向富集 | Results "RUNX footprints were present in a small number of seqlets" |
| 未报告批次效应处理细节 | 多组学数据来自不同批次，可能引入混杂 | 影响差异可及性和表达结果的可靠性 | 提供 Harmony 校正前后的对比分析 | Methods "snATAC-seq/multiome Analysis" 节 |
| 网络构建为纯计算推断 | DIRECT-NET 的 CRE-基因关联可能包含大量假阳性 | 网络生物学解释的可靠性 | 使用 CRISPR 干扰（CRISPRi）验证关键 CRE-基因对 | Methods "Construction of TF-CRE-Gene Linkages" 节 |
| 未与 IPF 或其他纤维化疾病比较 | 结论可能仅适用于 SSc-ILD | 普适性未知 | 在 IPF 独立数据集中重复分析 | 全文未提及 IPF 数据 |

## 14 学到什么

**Agent 提炼的知识候选**

1. **ChromBPNet 工作流（可直接迁移）**：本文展示了从 snATAC-seq 伪批量数据到单碱基 TF 结合贡献分数的完整流程，包括：(a) 在非可及区域训练 Tn5 偏好模型并冻结；(b) 在可及区域训练主模型；(c) 用 TF-MoDISco 做 de novo motif 发现。该流程可迁移至任何疾病/细胞类型的 TF–DNA 结合研究。

2. **「结合重分布」分析框架**：本文比较 SSc 与对照的贡献分数差异，而非仅比较 motif 活性。这种「差异结合」分析能识别传统方法遗漏的位点特异性变化，对 TF–DNA 互作研究具有方法论价值。

3. **多组学整合策略**：HALO（变分自编码器）构建 METAcells + DIRECT-NET（XGBoost）回归的组合，解决了单细胞数据稀疏性和 RNA/ATAC 时间滞后问题。该策略可迁移至其他需要整合转录组和表观基因组数据的研究。

4. **TF 家族内异质性的处理**：本文通过 K-means 聚类贡献分数模式，区分同一 TF 家族内不同结合位点的变化方向（增强/不变/减弱），提示「家族水平」分析可能掩盖位点特异性调控。

5. **GWAS 叠加策略**：将 SSc 相关 GWAS 位点叠加到 TF-CRE-基因网络上，将遗传变异与调控机制关联。该策略可迁移至其他复杂疾病的调控机制研究。

6. **体内（ex vivo）研究的价值与局限**：人原代组织单细胞多组学提供了体外实验无法获得的疾病状态 TF 结合信息，但缺乏正交验证。结合体外实验（如 HT-SELEX、EMSA）可互补。

## 15 与已有知识连接

- **与 ChromBPNet 原始论文的关联**：ChromBPNet 由 Bhattacharyya et al. (2021, Nature Genetics) 开发，本文是其首次应用于人肺纤维化组织。原始论文在 K562 等细胞系中验证了模型准确性，本文将其推广到原代组织。

- **与纤维化 TF 研究的关联**：AP-1 在纤维化中的作用已有广泛报道（如 Wernig et al. 2017 关于 Fra-2 的研究；本文 Discussion 引用 40-43）。本文的新贡献在于单碱基分辨率的结合动态刻画，而非发现新的 TF 家族。

- **与 RUNX 在纤维化中作用的关联**：RUNX1 在肌成纤维细胞分化中的作用已有报道（如 Kim et al. 2014），本文提供了 RUNX 结合位点在 SSc-ILD 中增强的体内证据。

- **与单细胞多组学方法的关联**：本文的方法组合（ChromBPNet + HALO + DIRECT-NET）与近期单细胞调控网络推断工具（如 SCENIC、CellOracle）形成互补。SCENIC 基于 motif 共表达，CellOracle 基于 scATAC 可及性，本文方法在单碱基分辨率上更精细。

- **与 TF–DNA 结合机制研究的关联**：本文的「贡献分数」概念与「结合足迹」（footprinting）分析（如 TOBIAS、HINT-ATAC）相关，但 ChromBPNet 通过深度学习建模序列-可及性关系，理论上能捕获更复杂的序列特征。

- **潜在冲突**：本文未用 ChIP-seq 验证 ChromBPNet 预测，与部分文献中「计算预测需实验验证」的共识存在张力。读者应谨慎对待未经验证的结合预测。

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：跨疾病 TF 结合动态比较（IPF vs SSc-ILD）
   - **来源局限/观察**：本文仅覆盖 SSc-ILD，未验证 IPF 中是否共享相同的 TF 结合变化
   - **核心假设**：IPF 和 SSc-ILD 的肌成纤维细胞共享 AP-1/RUNX/EGR 结合增强的核心调控程序
   - **增量**：将本文分析流程应用于 IPF 公开数据集（如 Habermann et al. 2020），比较两种纤维化疾病的 TF 结合动态
   - **初步方法**：下载 IPF snATAC 数据，重复 ChromBPNet 流程，比较 AP-1/RUNX/EGR 贡献分数变化
   - **验证方式**：与本文 SSc-ILD 结果做 meta 分析，识别共享和疾病特异的结合位点
   - **创新状态**：unverified

2. **候选名称**：AP-1 结合位点突变的报告基因验证
   - **来源局限/观察**：本文的 TF 结合预测未经过功能验证
   - **核心假设**：CTHRC1 和 ADAM12 上游/内含子中的 AP-1 结合位点突变会消除纤维化相关表达上调
   - **增量**：将计算预测转化为可操作的实验假设
   - **初步方法**：在成纤维细胞系中使用 CRISPR 编辑 AP-1 结合位点，检测 CTHRC1/ADAM12 表达变化
   - **验证方式**：报告基因实验 + 编辑细胞系的 RNA-seq
   - **创新状态**：unverified

3. **候选名称**：TF 结合动态的跨细胞类型调控网络比较
   - **来源局限/观察**：本文分别分析了成纤维细胞和巨噬细胞，但未比较两者 TF 结合程序的异同
   - **核心假设**：成纤维细胞和巨噬细胞中的促纤维化程序由不同的 TF 组合驱动（成纤维细胞以 AP-1/RUNX 为主，巨噬细胞以 bHLH-ZIP/AP-1 为主）
   - **增量**：系统比较两种细胞类型的 TF-CRE-基因网络，识别细胞类型特异的调控节点
   - **初步方法**：对本文构建的两种细胞网络做差异分析，识别共享和特异的 TF-CRE 关联
   - **验证方式**：细胞类型特异 ChIP-seq 或 CUT&Tag
   - **创新状态**：unverified

4. **候选名称**：TF 结合动态与遗传变异的共定位分析
   - **来源局限/观察**：本文将 GWAS 位点叠加到网络上，但未做系统共定位
   - **核心假设**：SSc 相关 GWAS 变异富集于 AP-1/RUNX/EGR 结合位点，且这些变异影响 TF 结合亲和力
   - **增量**：将遗传关联与 TF 结合动态整合，识别因果调控变异
   - **初步方法**：对 SSc GWAS 汇总统计做共定位分析（coloc），结合 ChromBPNet 贡献分数识别影响结合的变异
   - **验证方式**：等位基因特异性结合实验（allele-specific binding assay）
   - **创新状态**：unverified

5. **候选名称**：分子动力学模拟 AP-1 结合位点突变效应
   - **来源局限/观察**：本文的 TF 结合预测基于序列-染色质关联，未考虑三维结构效应
   - **核心假设**：AP-1 结合位点的疾病相关突变通过改变 Jun/Fos 二聚体的结合自由能影响染色质开放
   - **增量**：将深度学习预测与物理模拟结合，提供机制层面的解释
   - **初步方法**：对 CTHRC1/ADAM12 的 AP-1 位点进行 MD 模拟或 MM-PBSA 计算，比较突变前后的结合自由能
   - **验证方式**：表面等离子共振（SPR）或等温滴定量热（ITC）实验
   - **创新状态**：unverified