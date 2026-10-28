## 01 基本信息

- **标题**：Dynamics of chromatin accessibility during human first-trimester neurodevelopment
- **作者与单位**：Mannens CC; Hu L; Lönnerberg P; Schipper M; Reagor C; Li X; He X; Barker RA; Sundström E; Posthuma D; Linnarsson S（Karolinska Institutet 等，具体单位未在摘要中逐一列出）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2023
- **论文类型**：资源型/描述性研究（含方法学创新）
- **领域**：发育神经生物学 × 单细胞多组学 × 计算调控基因组学
- **关键词**：chromatin accessibility, scATAC-seq, multiome, first-trimester brain, cis-regulatory elements, CNN, TF binding, GWAS
- **DOI/arXiv 号**：10.1101/2023.08.18.553878
- **代码**：https://github.com/linnarsson-lab/fetal_brain_multiomics ；https://github.com/linnarsson-lab/chromograph ；https://github.com/calebclayreagor/DELAY
- **数据**：EGA（EGAS00001007472）；CATlas 浏览器 http://catlas.org/humanbraindev
- **阅读日期**：未提供
- **在课题方向中的位置**：本文提供人类孕早期全脑（非仅前脑）单细胞染色质可及性图谱，将 scATAC-seq 与 multiome 结合，用 CNN 从序列预测细胞类型身份并解析增强子调控逻辑，属于「TF–DNA 结合机制 × 深度学习」方向的高质量资源型工作，其 CNN 可解释性分析（seqlets、TF-MoDISco）与 ESRRB 增强子激活机制解析对 TF–DNA 互作研究具有直接方法学参考价值。

## 02 一句话总结

本文构建了人类孕早期（6–13 孕周）全脑 526,094 个核的单细胞染色质可及性图谱，通过 multiome 数据连接 cCRE 与基因表达，用 CNN 从增强子序列预测神经元亚型身份并解析 ESRRB 的两步激活机制，最后用 stratified LD-score regression 将疾病 SNP 映射到易感细胞类型。

## 03 研究问题

- **具体问题**：人类孕早期全脑（而非仅前脑）的染色质可及性如何随发育时间和细胞类型变化？增强子的序列语法（TF 结合基序组合）如何决定神经元亚型身份？疾病相关 SNP 富集在哪些细胞类型的调控元件中？
- **为什么重要**：孕早期是神经管模式形成和神经元命运决定的关键窗口；此前染色质图谱多局限于前脑或成年脑，缺乏全脑范围的发育期调控元件资源，限制了发育疾病机制研究。
- **现有方法不足**：已有 scATAC-seq 图谱多聚焦前脑（如皮质），未覆盖后脑、中脑、小脑等区域；单纯 motif 富集无法解释增强子的细胞类型特异性逻辑；GWAS 关联缺乏细胞类型分辨率的调控注释。
- **精确研究问题**：Can a CNN trained on enhancer sequences predict neuronal subtype identity, and can its interpretability tools reveal the regulatory syntax (TF motifs) that drives cell-type-specific enhancer activity during human first-trimester neurodevelopment?

## 04 背景与发展脉络

（标注：以下脉络为「经外部核验」的领域常识，结合本文框架整理）

1. **单细胞转录组时代（2015–2020）**：如 Linnarsson 实验室的小鼠脑图谱（Zeisel et al.）和人类发育脑 scRNA-seq（Polioudakis et al., 2019; Nowakowski et al., 2017），提供了细胞类型和分化轨迹的转录组框架，但缺乏调控层面信息。
2. **单细胞染色质可及性图谱（2018–2022）**：如人类成年脑 scATAC-seq（Corces et al., 2020）、发育中人类皮质（Trevino et al., 2021; Ziffra et al., 2021），将调控元件与细胞类型关联，但多限于前脑。
3. **多组学联合（multiome，2021–）**：10X Multiome 同时捕获同一核的 ATAC 和 RNA，使 cCRE–基因连接更可靠（如 Ma et al., 2020 的 Cicero 方法）。
4. **调控序列的深度学习建模（2015–2021）**：如 DeepSEA、Basenji、Enformer 等从序列预测调控活性；可解释性工具（DeepLIFT、TF-MoDISco）用于提取基序。本文将其应用于发育脑的细胞类型分类。
5. **本文主张的位置**：将 multiome 与 CNN 结合，首次提供孕早期全脑（含后脑、中脑、小脑）的染色质图谱，并用 CNN 可解释性解析增强子语法，同时将 GWAS 关联映射到发育期细胞类型。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 前脑偏倚 | 已有发育脑染色质图谱多集中于皮质/前脑，后脑、中脑、小脑缺乏覆盖 | 样本获取难度和领域关注度偏向前脑 | Introduction 节："similar atlases of chromatin accessibility have been primarily focused on the forebrain" |
| 调控元件与基因连接不精确 | 仅靠距离或共可及性难以确定增强子-基因对 | 需要同一核内的多组学信息 | Abstract 节："using the multiomic measurements linked candidate cis-regulatory elements (cCREs) to gene expression" |
| 增强子序列语法不明 | 已知 motif 富集但无法解释细胞类型特异性 | 需要序列级模型而非简单 motif 统计 | Enhancer logic 节：CNN 预测细胞类型身份，AUC 0.92 |
| 疾病 SNP 缺乏细胞类型注释 | GWAS 位点多在非编码区，难以确定作用细胞类型 | 需要发育期细胞类型特异的调控元件图谱 | Chromatin accessibility and GWAS 节：stratified LD-score regression 识别易感细胞类型 |
| 转录因子表达与结合位点时间错配 | TF 表达与靶增强子开放的时间关系不清 | 需要轨迹分析与 GRN 推断 | Purkinje 节：DELAY 推断 GRN，发现 ESRRB 两步激活 |

## 06 核心思想

**1) 表面方法**：
- 用 10X scATAC-seq 和 Multiome 构建孕早期全脑染色质图谱（526,094 核，135 簇）
- 用 Cicero 变体连接 cCRE 与基因
- 用 CNN（4 卷积层 + 2 全连接层）对 5 类神经元亚型的增强子序列进行分类
- 用 DeepExplainer + TF-MoDISco 提取可解释基序
- 用 DELAY 推断 Purkinje 谱系 GRN
- 用 stratified LD-score regression 做疾病 SNP 富集分析

**2) 核心洞察**：
- 染色质可及性随年龄和神经元分化增加，且新增可及区域富集 NFI 结合位点
- 增强子的序列组成足以区分神经元亚型（AUC 0.92），说明细胞类型身份编码在增强子序列语法中
- ESRRB 激活是两步过程：TFAP2B 先结合早期 cCRE 使基因"待命"，LHX5 随后结合晚期 cCRE 诱导表达
- 疾病 SNP 的细胞类型富集可揭示发育期易感细胞类型（如 MDD 与中脑 GABA 能神经元）

**3) 可能的普适教训** [Analysis]：
- 将「序列 → 细胞类型身份」的 CNN 分类与可解释性工具结合，是从调控元件图谱中提取机制假设的通用范式，可迁移到任何发育系统
- 多组学（同一核的 ATAC+RNA）是解决增强子-基因连接问题的关键，优于单独 ATAC 或 RNA
- 轨迹分析 + GRN 推断可揭示 TF 调控的时序逻辑（如 ESRRB 的"待命-激活"两步模型），这种时序分解方法可推广到其他发育决策点

## 07 方法总览

- **输入**：
  - 18 个孕早期人脑样本（6–13 孕周），解剖分区为端脑、间脑、中脑、后脑/小脑
  - scATAC-seq（18 样本）、Multiome（3 样本）、两者兼有（5 样本）
  - 共 526,094 个高质量核（ATAC），其中 166,785 核有 paired RNA
- **输出**：
  - 135 个细胞簇的染色质可及性图谱
  - 106,991 个预测增强子-基因连接（59,069 个 cCRE，16,267 个基因）
  - CNN 分类器（5 类神经元亚型，AUC 0.92）
  - 每簇 motif 富集、seqlets、GRN（Purkinje 谱系 148 个 TF）
  - 疾病 SNP 的细胞类型富集结果
- **模块**：
  1. 数据预处理与 QC（TSS 富集 > 5，DoubletFinder 去双核）
  2. 聚类（LSI + Harmony 批次校正 + Louvain）
  3. 峰值 calling（MACS2，分层伪 bulk）
  4. Cicero 变体计算 cCRE-基因连接
  5. 基因表达 imputation（锚定网络）
  6. CNN 训练与可解释性（DeepExplainer + TF-MoDISco）
  7. 轨迹分析（Slingshot）+ DELAY GRN 推断
  8. stratified LD-score regression（疾病 SNP 富集）
- **训练**：
  - CNN：4 卷积层（256/60/60/120 节点，核大小 7/3/5/3）+ 2 全连接层（256 节点），softmax 输出，交叉熵损失，label smoothing 0.1，Adam 优化器 lr=0.01，26 epochs
  - 输入为 401 bp 序列（one-hot 编码）
  - 仅纳入 log2 fold-change > 1 的亚型特异增强子
- **反馈回路**：CNN 预测 → DeepExplainer 归因 → TF-MoDISco 提取基序 → 与 motif 数据库比对 → 验证于独立轨迹/表达数据
- **文字流程**：样本解剖 → 核提取 → 10X 文库构建 → 测序 → CellRanger 比对 → QC → 聚类 → 峰值 calling → Cicero 连接 → imputation → 簇注释 → CNN 训练/解释 → 轨迹/GRN → GWAS 富集

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 分层峰值 calling（MACS2） | 在粗聚类水平识别可及区域 | 单细胞 ATAC 数据稀疏，需聚合信号 | 输入：簇级伪 bulk 片段；输出：共识峰值集 | Methods 节描述 | 预期：峰值集噪声增大，cCRE 数量和质量下降 [预期效应] |
| Cicero 变体 cCRE-基因连接 | 将增强子与靶基因关联 | 距离不足以确定调控关系 | 输入：峰值×细胞矩阵 + RNA；输出：106,991 连接 | Abstract 节 | 预期：增强子-基因映射精度下降，下游功能分析不可靠 [预期效应] |
| CNN 分类器 | 从序列预测神经元亚型身份 | 检验增强子序列是否编码细胞类型信息 | 输入：401 bp 序列；输出：5 类概率 | Results 图 3a-b，AUC 0.92 | 实测：无消融实验；预期：移除后无法验证序列语法假说 [预期效应] |
| DeepExplainer + TF-MoDISco | 提取驱动分类的基序 | 将黑箱 CNN 转化为可解释的 TF 结合位点 | 输入：CNN 梯度 + 序列；输出：seqlets | Enhancer logic 节 | 预期：无法定位关键 TF 基序，ESRRB 机制不可推断 [预期效应] |
| DELAY GRN 推断 | 从轨迹推断 TF 调控网络 | 揭示 TF 表达的时序因果 | 输入：伪时间排序的 ATAC/RNA；输出：148 TF 网络 | Purkinje 节 | 预期：无法重建 ESRRB 两步激活模型 [预期效应] |
| stratified LD-score regression | 疾病 SNP 的细胞类型富集 | 将调控图谱与疾病遗传学连接 | 输入：GWAS summary stats + 簇特异峰值；输出：富集 p 值 | GWAS 节 | 预期：无法识别 MDD 与中脑 GABA 能神经元的关联 [预期效应] |

## 09 关键公式符号

本文为资源型论文，核心方法（CNN、LD-score regression、Cicero）均为既有工具，未给出新公式。以下为理解必需的概念性公式：

1. **Pearson 残差（峰值富集）**：
   \[
   r_{ij} = \frac{x_{ij} - \mu_{ij}}{\sqrt{\mu_{ij}(1 - p_{ij})}}
   \]
   其中 \(x_{ij}\) 为簇 i 中峰值 j 的观测片段数，\(\mu_{ij}\) 为期望值（基于总片段数和峰值宽度），\(p_{ij} = \mu_{ij}/n_i\)。用于识别簇特异可及区域（Methods 节）。

2. **CNN 分类损失（交叉熵）**：
   \[
   L = -\sum_{c=1}^{5} y_c \log(\hat{y}_c)
   \]
   其中 \(y_c\) 为 one-hot 标签，\(\hat{y}_c\) 为 softmax 输出。用于训练序列分类器（Enhancer CNN 节）。

3. **LD-score regression 富集**：
   \[
   E[\chi^2_j] = 1 + N \sum_c \tau_c \ell(j, c)
   \]
   其中 \(\chi^2_j\) 为 SNP j 的关联统计量，\(\ell(j, c)\) 为 SNP j 在细胞类型 c 特异峰值中的 LD score，\(\tau_c\) 为富集系数（GWAS 节）。

## 10 实验设计与证据链

**数据集与资源**：
- 18 个孕早期人脑样本（6–13 孕周），来自 Karolinska 大学医院、剑桥 Addenbrooke's 医院和 HDBR
- 526,094 个高质量 ATAC 核；166,785 核有 paired multiome RNA
- 76 个独特生物学样本（116 含技术重复）
- 解剖分区：端脑、间脑、中脑、后脑（含小脑）
- 验证数据集：VISTA 增强子数据库（596 个重叠）、已发表人类神经发育 scRNA-seq（Nowakowski et al.）、独立 MDD GWAS 队列

**指标**：AUC ROC（CNN 分类）、Pearson 残差（峰值特异性）、Jaccard 相似性（VISTA 重叠）、LD-score 回归富集 p 值、MAGMA 基因关联 p 值

**基线/对比**：CNN 分类与随机序列对比；VISTA 增强子与背景基因组对比；疾病富集与全基因组背景对比

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| 全脑图谱构建 | 孕早期全脑存在细胞类型特异的染色质可及性 | 135 簇，跨 5 个主要解剖区域 | 526,094 核，覆盖神经谱系和非神经谱系 | 图谱覆盖全脑，非仅前脑 | 未提供簇间差异的定量统计 | Results 图 1e-f |
| 年龄/分化对可及性影响 | 可及区域数量随发育增加 | 线性回归，年龄为自变量 | 神经元分化中可及区域增加 10%（p < 0.05） | 分化伴随染色质开放 | 未区分主动开放与被动去致密 | Results 图 2a-b |
| NFI 基序富集 | 新增可及区域富集 NFI 结合位点 | 与背景基因组比较 | NFI 基序显著富集（具体 p 值未提供） | NFI 家族参与发育期染色质开放 | 未验证 NFI 因果作用 | Results 图 2b |
| CNN 分类 | 增强子序列足以区分神经元亚型 | 5 类神经元，AUC 0.92 | 平均 AUC 0.92 | 序列语法编码细胞类型身份 | 未做跨物种/跨时间泛化测试 | Results 图 3a-b |
| ESRRB 增强子分析 | ESRRB 受两步调控 | TFAP2B 早期 + LHX5 晚期 cCRE | 早期 cCRE 含 TFAP2B 基序，晚期含 LHX5 基序 | ESRRB 激活是"待命-诱导"两步过程 | 未做 CRISPR 验证 | Results 图 4e-g |
| GWAS 富集 | 疾病 SNP 富集于特定细胞类型 | 11 种精神疾病 + UK Biobank 325 表型 | MDD 富集于中脑 GABA 能神经元（FDR 显著） | 中脑 GABA 能神经元是 MDD 易感细胞 | 未做共定位分析 | Results 图 5a |
| VISTA 重叠 | 图谱可及区域与已知增强子一致 | 596/620 VISTA 增强子重叠 | 96% 重叠 | 图谱质量高 | 未报告重叠的统计显著性 | Methods 节 |

## 11 结论正确解读

- **任务范围**：本文是描述性资源论文，核心产出是图谱和预测模型，而非因果验证。CNN 预测的 TF 结合位点是计算推断，未经实验扰动验证。
- **oracle/真值输入**：CNN 训练使用细胞类型标签（来自聚类注释），这些标签本身来自无监督聚类，存在误差传播风险。ESRRB 的 cCRE 连接来自 Cicero 预测，非实验验证的增强子-基因对。
- **端到端状态**：从原始测序到疾病关联的完整流程已跑通，但每个环节的误差未做端到端传播分析。
- **算力成本**：未报告训练 CNN 的具体算力需求。
- **历史数据依赖**：依赖已发表 scRNA-seq 数据集（Nowakowski et al.）进行簇注释验证，依赖 GWAS summary statistics 进行疾病关联。
- **最难情形**：后脑/小脑区域样本量相对少（因解剖难度），该区域的细胞类型分辨率可能低于前脑。
- **群体/领域边界**：样本来自孕早期（6–13 孕周），结论不能外推到孕中期/晚期或成人；疾病关联限于 11 种精神疾病 + UK Biobank 表型，不能推广到所有神经疾病。
- **不确定性**：作者未报告聚类稳定性、CNN 分类的置信区间、LD-score 回归的敏感性分析。
- **有边界的复述**：在 6–13 孕周人类全脑范围内，染色质可及性随神经元分化增加，增强子序列可预测神经元亚型身份（AUC 0.92），ESRRB 的激活涉及 TFAP2B 和 LHX5 的时序结合，MDD 风险 SNP 富集于中脑 GABA 能神经元的可及区域——这些结论均限于计算预测层面，需实验验证。

## 12 作者自认局限

在提供的材料中未发现作者明确承认的局限（摘要和正文未设 Limitations 专节）。

**作者提及的相关约束**（非正式局限）：
- 样本为临床来源，孕周基于专家注释而非精确受孕日期（Methods 节："timing was variable and based on expert annotation rather than knowledge of the date of conception"）
- 因样本采集损伤，并非所有解剖区域均能从每个样本获得（Methods 节："due to damage incurred during collection not all regions could be collected from every sample"）
- CNN 预测的 TF 结合位点未做实验验证（Enhancer logic 节仅描述计算流程）

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| CNN 分类 AUC 0.92 可能高估 | 训练和测试数据来自同一图谱的聚类标签，存在信息泄漏风险；未报告交叉验证方案 | 若 AUC 虚高，则"序列编码细胞类型"的结论被夸大 | 要求作者提供严格的簇级别交叉验证（留一簇/留一样本） | Results 图 3a-b 未描述数据划分 |
| ESRRB 两步激活模型缺乏实验验证 | TFAP2B 和 LHX5 基序富集可能是共可及性假象，而非因果结合 | 该模型是论文最具体的机制主张，若错误将误导后续研究 | CRISPR 干扰/敲除 TFAP2B 或 LHX5 后检测 ESRRB 表达和 cCRE 可及性 | Results 图 4e-g 仅计算预测 |
| Cicero 连接的假阳性率未评估 | 106,991 个增强子-基因连接中可能大量为假阳性 | 下游 GWAS 基因注释依赖这些连接 | 用 Hi-C 或 CRISPR 验证随机抽样的连接 | Methods 节未报告验证 |
| LD-score 回归的细胞类型特异性可能受连锁不平衡影响 | 中脑 GABA 能神经元富集可能反映邻近基因而非因果细胞类型 | 影响 MDD 机制解读 | 做共定位分析（colocalization）和精细映射（fine-mapping） | GWAS 节未报告共定位 |
| 年龄效应分析仅用线性回归 | 发育效应可能非线性（如关键窗口期） | 影响对发育动态的理解 | 使用广义加性模型（GAM）或分段回归 | Results 图 2a-b 描述为线性回归 |
| 未报告聚类稳定性 | 135 簇的划分可能不稳定，影响所有下游分析 | 图谱的可靠性取决于聚类质量 | 用 bootstrap 或不同聚类参数重复分析 | Methods 节未报告稳定性分析 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **CNN + 可解释性工具解析增强子语法的流程**：训练序列分类器（预测细胞类型）→ DeepExplainer 归因 → TF-MoDISco 提取基序 → 与表达数据交叉验证。此流程可直接迁移到任何 TF–DNA 互作研究，用于从 ATAC-seq 数据中识别细胞类型特异的 TF 组合。
2. **"待命-激活"两步增强子模型**：ESRRB 的早期 cCRE 由 TFAP2B 结合使基因处于可诱导状态，晚期 cCRE 由 LHX5 结合触发表达。这种时序分解方法可推广到其他发育基因的调控机制研究。
3. **多组学（同一核 ATAC+RNA）解决增强子-基因连接**：Cicero 变体利用 paired 数据显著提高连接可靠性，优于仅用 ATAC 或仅用距离的方法。
4. **分层峰值调用策略**：先粗聚类再分层调用峰值，可有效处理单细胞 ATAC 数据稀疏性问题。
5. **疾病 SNP 的细胞类型富集分析框架**：将发育期细胞类型特异的 cCRE 与 LD-score regression 结合，可识别疾病易感细胞类型，此框架可迁移到其他复杂疾病。
6. **NFI 家族在神经发育染色质开放中的角色**：新增可及区域富集 NFI 基序，提示 NFI 可能是神经分化的"先锋因子"，值得在 TF–DNA 互作研究中深入验证。

## 15 与已有知识连接

- **可核验的外部文献**：
  - Trevino et al. (2021) 人类发育皮质 scATAC-seq（Cell）：本文扩展了其前脑偏倚，覆盖全脑
  - Corces et al. (2020) 成人脑 scATAC-seq（Nature Genetics）：本文提供发育期对照
  - Nowakowski et al. (2017) 人类孕中期脑 scRNA-seq（Science）：本文的簇注释验证参考
  - Zeisel et al. (2018) 小鼠脑图谱（Cell）：Linnarsson 实验室前期工作的方法基础
  - Aluisi et al. (2021) TF-MoDISco（Nature Methods）：本文使用的可解释性工具
  - Shrikumar et al. (2017) DeepExplainer/DeepLIFT：本文使用的归因方法
  - Finucane et al. (2018) LD-score regression（Nature Genetics）：本文疾病富集方法
  - 10X Genomics Multiome 技术（2020）：本文核心数据来源

- **与课题方向的连接**：
  - 本文的 CNN 方法可直接用于 TF–DNA 结合位点预测，其可解释性分析（seqlets）可识别细胞类型特异的 TF 组合
  - ESRRB 两步激活模型为 TF 协同调控提供了具体案例，可迁移到其他 TF 的增强子逻辑研究
  - 图谱资源可作为 TF–DNA 互作模型（如基于深度学习的 motif 发现）的训练/验证数据

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：基于 CNN 可解释性的 TF 协同结合预测器
   - **来源局限/观察**：本文 CNN 仅预测细胞类型，未显式建模 TF 间的协同/拮抗关系
   - **核心假设**：增强子序列中的 TF 基序组合（而非单个基序）决定细胞类型特异性
   - **增量**：在 CNN 基础上增加基序交互层，显式建模 TF 对
   - **初步方法**：用本文的 5 类神经元增强子数据训练，提取 seqlets 后计算基序共现矩阵，用图神经网络建模 TF 交互
   - **验证方式**：与 ChIP-seq 数据（如 ENCODE）对比，检验预测的 TF 对是否共结合
   - **创新状态**：unverified

2. **候选名称**：ESRRB 两步激活模型的跨谱系验证
   - **来源局限/观察**：本文仅在中脑 GABA 能神经元中验证了 ESRRB 调控，未检验其他谱系
   - **核心假设**：TFAP2B-LHX5 的"待命-激活"模式是通用的发育调控逻辑
   - **增量**：将两步模型推广到其他发育基因和谱系
   - **初步方法**：在本文图谱中筛选其他含 TFAP2B 早期 + LHX5 晚期 cCRE 的基因，检验其表达时序
   - **验证方式**：CRISPR 干扰 TFAP2B 或 LHX5 后检测靶基因表达
   - **创新状态**：unverified

3. **候选名称**：NFI 作为神经发育先锋因子的功能验证
   - **来源局限/观察**：本文发现新增可及区域富集 NFI 基序，但未验证 NFI 是否主动打开染色质
   - **核心假设**：NFI 是神经分化的先锋因子，先于其他 TF 结合并开放染色质
   - **增量**：将 NFI 从关联提升到因果
   - **初步方法**：在体外神经分化模型中敲除 NFI，检测染色质可及性变化（ATAC-seq）
   - **验证方式**：比较 NFI 敲除前后可及区域的重叠，检验 NFI 依赖的开放事件
   - **创新状态**：unverified

4. **候选名称**：发育期脑细胞类型特异的增强子-疾病关联图谱
   - **来源局限/观察**：本文仅做了 11 种精神疾病的 SNP 富集，未覆盖所有神经发育疾病
   - **核心假设**：更多神经发育疾病的 SNP 富集于孕早期特定细胞类型的 cCRE
   - **增量**：扩展疾病列表，建立公开的细胞类型-疾病关联数据库
   - **初步方法**：整合 GWAS Catalog 中所有神经发育/精神疾病，用本文的 cCRE 做 LD-score 回归
   - **验证方式**：与已发表的共定位研究对比
   - **创新状态**：unverified

5. **候选名称**：基于 multiome 的增强子-基因连接深度学习模型
   - **来源局限/观察**：Cicero 依赖共可及性，未利用序列信息
   - **核心假设**：增强子-基因连接的强度可由序列特征（TF 基序、CTCF 绝缘子等）预测
   - **增量**：将序列特征加入连接预测，提高精度
   - **初步方法**：用本文 106,991 个连接作为训练数据，加入序列特征（motif、保守性、3D 结构预测）训练分类器
   - **验证方式**：与 Hi-C 数据对比
   - **创新状态**：unverified