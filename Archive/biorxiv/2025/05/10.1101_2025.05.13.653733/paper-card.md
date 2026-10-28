## 01 基本信息

- **标题**：Decoding Plasticity Regulators and Transition Trajectories in Glioblastoma with Single-cell Multiomics
- **作者与单位**：Saraswat M; Rueda-Gensini L; Heinzelmann E; Gracia T; Memi F; de Jong G; Straub J; Schloo C; Hoffmann DC; Jung E; Kindinger T; Weigel B; Lim B; Weil S; Gould O; Mair R; Mikulik K; Rohbeck M; Wick W; Winkler F; Bayraktar OA; Stegle O; Mall M（单位未在摘要中提供）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2025
- **论文类型**：预印本（研究论文）
- **领域**：癌症表观遗传学、单细胞多组学、基因调控网络、计算生物学
- **关键词**：胶质母细胞瘤、细胞可塑性、增强子驱动的基因调控网络（eGRN）、单细胞多组学、MYT1L、深度学习
- **DOI/arXiv 号**：10.1101/2025.05.13.653733
- **代码**：https://github.com/bioFAM/scDORI ；https://github.com/PMBio/GBM_analysis
- **数据**：www.gbmspace.org/ （ATAC 数据将在同行评审后公开）
- **阅读日期**：未提供
- **在「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法/物理模拟」方向中的位置**：本文属于「AI 方法用于 TF–DNA 结合与基因调控网络推断」子方向。核心贡献是开发了深度学习框架 scDORI，从单细胞多组学数据中推断增强子驱动的基因调控网络（eGRN），并识别了调控细胞状态转换的关键转录因子（如 MYT1L）。该文与 TF–DNA 结合机制直接相关，但方法层面不涉及物理模拟（如 MD 或对接），而是基于序列与染色质可及性数据的统计/深度学习建模。

---

## 02 一句话总结

本文开发了可扩展的深度学习框架 scDORI，从超过 100 万细胞的单核 RNA+染色质可及性多组学数据中推断增强子驱动的基因调控网络（eGRN），识别出胶质母细胞瘤细胞状态的可塑性层级，并实验验证了神经元样状态特异性抑制因子 MYT1L 通过直接抑制其他状态的主调控因子来限制肿瘤可塑性和恶性进展。

---

## 03 研究问题

- **具体问题**：胶质母细胞瘤（GB）细胞在不同状态之间转换的调控逻辑是什么？哪些转录因子（TF）和顺式调控元件（CRE）决定或限制这些状态转换？神经元样细胞状态为何表现出低可塑性？
- **为什么重要**：GB 的异质性和治疗抵抗被认为与细胞可塑性密切相关。理解状态转换的调控机制，可能揭示限制肿瘤适应性的治疗靶点。
- **现有方法为何不足**：
  - 已有 eGRN 推断方法（如 SCENIC、Pando 等）难以扩展到百万级细胞数据集；
  - 依赖预定义的细胞类型注释，无法建模连续的状态差异；
  - 主要关注转录激活，忽略转录抑制在状态维持中的作用。
- **精确的「Can ... ?」研究问题**：Can a scalable deep-learning framework infer cell-state-specific enhancer-driven gene regulatory networks from single-cell multi-omics data to identify regulators that constrain or permit glioblastoma cell state transitions?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架，未经外部系统核验，标注为「仅本文框架」。

1. **单细胞转录组定义 GB 细胞状态**（约 2019–2022）：代表性方法为 scRNA-seq 聚类，识别出 OPC-like、NPC-like、AC-like、MES-like 等状态（如 Neftel et al. 2019）。局限：仅基于转录组，缺乏调控层面的解释。
2. **染色质可及性揭示表观遗传状态**（约 2020–2023）：scATAC-seq 或 snRNA-ATAC 多组学揭示状态特异的染色质景观。局限：缺乏将增强子与靶基因连接的可扩展方法。
3. **基因调控网络推断**（约 2021–2024）：如 SCENIC（基于 motif 的 regulon 推断）、Pando（结合 TF 结合位点与染色质可及性）。局限：可扩展性差、依赖注释、主要建模激活。
4. **深度学习用于调控建模**（约 2022–2025）：如 Enformer、Basenji 等从序列预测表达/染色质。局限：主要针对 bulk 或细胞系，难以直接用于原发肿瘤的单细胞异质性。
5. **本文位置**：将深度学习（变分自编码器 + 主题建模）与 eGRN 推断结合，实现百万级细胞的可扩展推断，并显式建模激活与抑制两种调控模式，填补了「单细胞规模 × 调控网络 × 抑制机制」的空白。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有 eGRN 方法可扩展性差 | 无法处理百万级细胞数据集 | 基于 motif 扫描或全基因组相关性的计算复杂度高 | Results 节「Established eGRN inference methods face limitations that hamper their applicability…poor scalability to large datasets」 |
| 依赖预定义细胞类型注释 | 无法建模连续状态差异和状态内异质性 | 传统方法先聚类再推断网络，丢失连续梯度信息 | Results 节「their reliance on pre-defined cell type annotations means they cannot model continuous and cell state-specific differences of eGRNs」 |
| 忽视转录抑制在状态维持中的作用 | 已有方法主要建模激活，无法解释低可塑性状态 | 抑制性调控（如 MYT1L）在肿瘤可塑性中的角色未被系统研究 | Results 节「previous methods primarily focus on signatures of transcriptional activation, despite the growing recognition of gene repression as a key regulator of cell identity and plasticity in cancer」 |
| 预测的调控关系缺乏实验验证 | 计算预测的 TF–靶基因关系多为推测 | 缺乏高通量验证手段 | 作者通过 MYT1L 的 CUT&RUN、ATAC-seq、体内实验进行验证（Results 节） |

---

## 06 核心思想

### 1) 表面方法
- 开发 scDORI（single-cell Deep Omics Regulatory Inference），一个基于变分自编码器（VAE）的深度学习框架，联合建模基因表达和染色质可及性，将细胞分解为「主题」（Topics）的混合，每个主题对应一个调控程序。
- 通过耦合多个解码器，施加调控约束：TF 表达 → TF 结合位点（motif）→ 染色质可及性 → 靶基因表达。
- 定义「主题调控因子」（Topic Regulators, TRs）和「主题抑制评分」（Topic Repression Score, TRS），并构建「主题激活潜力」（Topic Activation Potential, TAP）指标来量化状态间转换的可能性。

### 2) 核心洞察
- **调控逻辑是「激活 + 抑制」的双重机制**：状态转换不仅由激活因子驱动，还由状态特异性抑制因子（如 MYT1L）主动阻断替代命运。神经元样细胞通过 MYT1L 主动抑制其他状态的主调控因子，形成低可塑性的「表观遗传屏障」。
- **连续调控梯度而非离散状态**：细胞状态不是离散的类别，而是由多个调控程序（Topics）的连续混合构成，这解释了状态内异质性和部分转换潜力。
- **可迁移的「调控屏障」概念**：在肿瘤中，低可塑性状态可能不是「被动缺乏激活信号」，而是「主动抑制」的结果，这为治疗提供了新靶点——解除抑制可能使细胞进入更可塑、更易被治疗的状态。

### 3) 可能的普适教训 [Analysis]
- 在 TF–DNA 互作研究中，**抑制性调控（repression）与激活同等重要**，但多数计算方法偏向激活建模。将抑制信号显式纳入网络推断，可能在其他肿瘤或发育系统中发现类似「可塑性屏障」机制。
- **连续建模优于离散聚类**：当研究状态转换时，将细胞建模为调控程序的连续混合（而非硬聚类），能更准确地捕捉中间态和转换潜力。
- **计算预测 + 功能验证的闭环**：本文展示了从计算预测（scDORI）到分子验证（CUT&RUN、ATAC-seq）再到功能验证（体内移植）的完整路径，这种闭环是可信度的关键。

---

## 07 方法总览

- **输入**：配对单核 RNA 表达矩阵 + 染色质可及性矩阵（snRNA-ATAC-seq），来自 12 例原发 IDH 野生型 GB 患者的 100 万+细胞，覆盖肿瘤核心和瘤周区域。
- **输出**：
  1. 每个细胞的 Topic 混合比例（连续调控程序组成）；
  2. 每个 Topic 的 TF 激活/抑制活性评分；
  3. 细胞状态间的 TAP（激活潜力）和 TRS（抑制评分）矩阵；
  4. 状态转换轨迹。
- **核心模块**：
  1. **多组学 VAE 编码器**：将基因表达和染色质可及性联合嵌入低维空间；
  2. **耦合解码器**：施加调控约束（TF→motif→peak→基因），支持激活和抑制两种方向；
  3. **Topic 建模**：类似主题模型，每个 Topic 对应一个协同调控程序；
  4. **TR 识别**：每个 Topic 中调控影响力最强的 TF；
  5. **TAP/TRS 计算**：基于 Topic 间 TF→TR 的调控连接强度、靶 TR 的染色质可及性（表观遗传预备状态）和 TF 相对重要性。
- **训练**：VAE 端到端训练，损失函数包含表达重建、染色质重建和调控约束正则化。具体细节在 Methods 文件中（摘要未提供）。
- **反馈回路**：无显式闭环（如主动学习），但通过实验验证（MYT1L 功能实验）反馈到模型解释。
- **假设**：
  - 染色质可及性反映 TF 结合的潜力；
  - TF 对靶基因的调控方向（激活/抑制）可从数据中推断；
  - Topic 是调控程序的合理抽象。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 多组学 VAE 编码器 | 联合嵌入表达+染色质 | 降维并捕捉跨模态关联 | 输入：表达+peak 矩阵；输出：潜在表示 | Results 节「Building on autoencoders…combines principles of multi-omics dimensionality reduction」 | 预期影响：无法联合建模跨模态调控关系 [预期效应] |
| 耦合解码器（调控约束） | 施加 TF→motif→peak→基因的调控链 | 确保 Topic 具有生物学可解释性 | 输入：潜在表示；输出：重建的表达+peak | Results 节「multiple coupled decoders that capture established signatures of eGRNs」 | 预期影响：Topic 失去调控可解释性，退化为纯统计因子 [预期效应] |
| Topic 建模 | 将细胞分解为调控程序的混合 | 无需预定义注释，捕捉连续状态 | 输入：潜在表示；输出：Topic 混合比例 | Results 节「model the multi-omic profile of each cell as a mixture of Topics」 | 预期影响：无法解析状态内异质性 [预期效应] |
| TR 识别 | 每个 Topic 中调控影响力最强的 TF | 识别状态特异性主调控因子 | 输入：Topic 权重；输出：TR 列表 | Results 节「defined Topic Regulators (TRs) as TFs with the strongest downstream regulatory influence」 | 预期影响：无法定位关键调控节点 [预期效应] |
| TAP 计算 | 量化状态间激活潜力 | 预测哪些转换更可能发生 | 输入：Topic 间调控连接；输出：TAP 矩阵 | Results 节「estimates how readily the TRs of a target Topic can be activated within a different source Topic」 | 预期影响：无法预测转换方向 [预期效应] |
| TRS 计算 | 量化状态间抑制强度 | 解释低可塑性状态的主动抑制机制 | 输入：Topic 间抑制连接；输出：TRS 矩阵 | Results 节「defined a Topic Repression Score (TRS)」 | 预期影响：无法解释「屏障」机制 [预期效应] |
| 空间验证模块 | 用 Visium 空间转录组验证 TAP-TRS 预测的空间邻近性 | 独立验证转换模型 | 输入：Visium 数据；输出：空间距离 vs 转换分数相关性 | Results 节「analyzed the spatial distribution of Topics within matched tumor sections using Visium spatial transcriptomics」 | 预期影响：缺乏独立验证维度 [预期效应] |
| MYT1L 功能验证模块 | CUT&RUN、ATAC-seq、体内移植 | 验证计算预测的因果性 | 输入：MYT1L OE/KO 细胞；输出：染色质/表达/肿瘤表型变化 | Results 节「MYT1L gain-of-function…reduced proliferation and invasion in vivo」 | 预期影响：计算预测停留在相关性层面 [预期效应] |

---

## 09 关键公式符号

> 注：摘要和正文未提供具体数学公式。以下基于方法描述推断，标注为 [Analysis]。

- **Topic 混合模型**（推断）：
  - 设细胞 i 的潜在表示 zᵢ，Topic 权重 θᵢ ∈ Δᴷ（K 个 Topic 的单纯形），则 p(xᵢ, aᵢ | zᵢ) = Σₖ θᵢₖ · p(xᵢ | zᵢ, k) · p(aᵢ | zᵢ, k)，其中 xᵢ 为表达，aᵢ 为染色质可及性。
  - 用途：将每个细胞分解为多个调控程序的连续混合。
  - 来源：Results 节「model the multi-omic profile of each cell as a mixture of Topics」[Analysis]

- **TAP（Topic Activation Potential）**：
  - TAP(S→T) = Σ_{tf∈TR_S} w_tf · Accessibility_T(tf) · Regulatory_Strength(tf→TR_T)
  - 其中 w_tf 为 TF 在源 Topic 中的相对重要性，Accessibility_T(tf) 为靶 Topic 中该 TF 结合位点的染色质可及性，Regulatory_Strength 为 TF 对靶 Topic TR 的调控连接强度。
  - 用途：量化从源 Topic 激活靶 Topic 的潜力。
  - 来源：Results 节「integrates three components: (i) the presence of regulatory interactions…(ii) the accessibility of target TRs…(iii) the relative importance of each TR」[Analysis]

- **TRS（Topic Repression Score）**：
  - TRS(S→T) = Σ_{tf∈Rep_S} w_tf · Repressive_Strength(tf→TR_T)
  - 其中 Rep_S 为源 Topic 中具有抑制活性的 TF 集合。
  - 用途：量化源 Topic 对靶 Topic 的主动抑制强度。
  - 来源：Results 节「conceptually analogous to TAP but considering signatures of repression」[Analysis]

- **净转换得分**：
  - Net(S→T) = TAP(S→T) − TRS(S→T)
  - 用途：综合评估状态间转换的可能性与方向。
  - 来源：Results 节「defined a net transition score of TAP minus TRS」[Analysis]

---

## 10 实验设计与证据链

### 数据集/群体/规模/指标/基线/预算/评测协议

- **数据集**：
  - 训练/发现集：12 例原发 IDH 野生型 GB 患者的 snRNA-ATAC 多组学数据，>100 万细胞，覆盖肿瘤核心和瘤周区域（4–15 个采样位点/例）。
  - 独立验证集：已发表的独立单细胞 GB 图谱（用于 Topic 映射验证）。
  - 空间验证：匹配肿瘤切片的 Visium 空间转录组。
  - 功能验证：患者来源的胶质母细胞瘤细胞（PDGCs；S24 无内源 MYT1L，BG5 有内源 MYT1L）。
- **指标**：
  - eGRN 预测性能：增强子-启动子连接预测的 AUROC/AUPRC（与已有方法对比）。
  - 可塑性评分：基于染色质可及性预测转录状态的置信度。
  - TAP/TRS 与空间距离的相关性。
  - MYT1L 功能：差异可及性区域数量、差异表达基因数、肿瘤生长/侵袭/生存（体内）。
- **基线/对比方法**：已有 eGRN 推断方法（如 SCENIC、Pando 等，具体名称在 Methods 中，摘要未列出）。
- **预算/算力**：未提供。
- **评测协议**：交叉验证（Topic 稳健性）、独立数据集映射、空间转录组验证、功能实验验证。

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 可塑性评分分析 | 恶性细胞比 TME 细胞更具表观遗传可塑性 | 恶性 vs 非恶性细胞 | 恶性细胞可塑性显著更高（p=9.8×10⁻¹⁴） | 可塑性是恶性细胞的特性 | 未证明可塑性直接导致治疗抵抗 | Results 节 Fig. 1C |
| 状态间可塑性比较 | 神经元样细胞是最低可塑性状态 | 各 GB 状态间两两比较 | NPC/OPC 神经元样细胞可塑性最低（p=6.7×10⁻⁶） | 神经元样状态是「低可塑性陷阱」 | 未证明该状态不可逆 | Results 节 Fig. 1E |
| scDORI Topic 稳健性 | Topics 在多次重启和独立数据集中可重复 | 多次模型重启 + 独立 GB 图谱映射 | Topics 稳健映射 | scDORI 结果可靠 | 未在所有患者中验证每个 Topic | Results 节 Extended Data Fig. 3C, 5A-C |
| eGRN 预测性能 | scDORI 优于已有 eGRN 方法 | 与 SCENIC/Pando 等对比 | scDORI 在增强子-启动子连接预测上表现更优 | scDORI 方法学优势 | 未在非肿瘤数据上验证 | Results 节 Extended Data Fig. 2C, 5D-E |
| TAP-TRS vs 空间距离 | 高转换潜力的状态对在空间上更接近 | Visium 空间转录组 | 高 TAP-TRS 的 Topic 对空间距离更近 | 转换潜力反映真实空间邻近性 | 相关性不等于因果 | Results 节 Fig. 4I-J |
| TAP-TRS vs 时间共现 | 高转换潜力的状态在克隆轨迹上共现 | 假时间克隆分析（N=60 克隆） | 高 TAP-TRS 的 Topic 对在时间上共现 | 转换潜力反映时间顺序 | 未直接观察转换事件 | Results 节 Extended Data Fig. 8A-C |
| MYT1L 过表达（S24） | MYT1L 足以诱导神经元样状态并抑制可塑性 | OE vs 对照 | >80% 差异可及区域关闭；神经元样特征上调；增殖/侵袭下降 | MYT1L 是神经元样状态的驱动因子 | 未证明 MYT1L 是唯一必要因子 | Results 节 Fig. 5C-E |
| MYT1L 敲除（BG5） | MYT1L 缺失解除对替代状态的抑制 | KO vs 对照 | >80% 差异可及区域开放；替代状态基因上调；增殖/侵袭增强 | MYT1L 是维持低可塑性的必要因子 | 未证明解除抑制足以完全转换状态 | Results 节 Fig. 5C-E |
| MYT1L 体内移植 | MYT1L 限制体内肿瘤生长和侵袭 | OE vs 对照原位移植 | 肿瘤生长减慢、侵袭受限、生存延长 | MYT1L 在体内限制恶性进展 | 未测试治疗性干预 | Results 节 Fig. 5J-L |
| MYT1L 直接靶标验证 | MYT1L 直接结合并抑制替代状态 TF | CUT&RUN | 55.5% 差异可及基因被 MYT1L 直接结合；包括 SMAD3、TRPS1、TCF7L2、MYBL1 | MYT1L 直接抑制替代状态主调控因子 | 未验证所有结合位点的功能 | Results 节 Fig. 5D, Extended Data Fig. 10H |
| 工程化 MYT1L 融合实验 | MYT1L 的抑制功能依赖其 RD 结构域 | MYT1L-RD 融合 vs 对照 | 抑制功能依赖 RD 结构域 | MYT1L 通过主动抑制而非被动结合发挥作用 | 未测试其他结构域 | Results 节 Fig. 5I |

---

## 11 结论正确解读

- **任务范围**：本文聚焦于原发 IDH 野生型 GB 的细胞状态可塑性和转换调控，不涉及复发肿瘤、IDH 突变型或儿童 GB。
- **oracle/真值输入**：功能实验（MYT1L OE/KO）使用了患者来源的细胞系（S24、BG5），这些细胞系可能无法完全代表原发肿瘤的异质性。
- **端到端状态**：从计算预测到功能验证的闭环已建立，但仅针对 MYT1L 一个因子；其他预测的 TR 和抑制因子未进行同等深度的验证。
- **算力成本**：未提供。
- **历史数据依赖**：模型依赖训练数据中的细胞状态覆盖度；罕见状态可能未被充分采样。
- **模型依赖**：scDORI 的 Topic 数量（K=31）是超参数，可能影响结果粒度。
- **最难情形**：低丰度状态、高度异质性肿瘤、非编码突变对调控的影响。
- **群体/领域边界**：结论基于 12 例患者，样本量有限；不同遗传背景（如 EGFR 扩增、PTEN 缺失等）对可塑性的影响未分层分析。
- **不确定性**：TAP/TRS 是计算指标，其与真实生物学转换概率的定量关系未校准。

**有边界的复述**：在 12 例原发 IDH 野生型 GB 的 100 万+细胞多组学数据中，scDORI 识别出 31 个调控主题，其中神经元样状态通过 MYT1L 等抑制因子主动限制状态转换；MYT1L 的功能实验支持其作为可塑性屏障的角色，但该结论仅限于所测试的细胞系和实验条件。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 预测需要实验验证 | scDORI 预测的调控因子（除 MYT1L 外）未经功能验证 | 未来需对更多预测因子进行功能实验 | Discussion 节「its predictions require experimental validation to confirm the functional roles of identified regulators」 |
| 仅覆盖原发肿瘤 | 未分析复发肿瘤及其治疗反应 | 未来应研究复发肿瘤和治疗反应 | Discussion 节「investigating recurrent tumors and their therapy response would provide an exciting future perspective」 |
| 神经元样状态的角色可能不完整 | 低可塑性状态可能通过非细胞自主机制促进肿瘤 | 未来需研究该状态在肿瘤生态系统中的非细胞自主功能 | Discussion 节「this may not fully capture its role in the GB ecosystem…future work is needed to test whether this epigenetically constrained state serves specialized, tumor-promoting functions via non-cell-autonomous mechanisms」 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| 可塑性评分基于「可及性-表达不一致性」的间接指标 | 可及性高但表达低可能反映转录后调控、RNA 降解或技术噪声，而非「可塑性」 | 可塑性是全文核心概念，若指标有偏，结论可能不成立 | 用独立方法（如 ATAC 染色质状态转换速率、谱系追踪）交叉验证可塑性评分 | Results 节 Fig. 1B 方法描述 |
| MYT1L 功能实验仅在 2 个 PDGC 系中进行 | 细胞系可能无法代表原发肿瘤的异质性；S24 和 BG5 的遗传背景差异可能混淆结果 | 结论的普适性取决于细胞系代表性 | 在更多 PDGC 系和原位模型（如类器官）中重复实验 | Results 节 Fig. 5 |
| TAP/TRS 与空间距离的相关性可能受组织采样偏差影响 | 空间距离近可能反映组织解剖结构而非调控关系 | 空间验证是独立证据链，若存在混淆，支持力度下降 | 用空间变异基因表达/配体-受体分析排除解剖结构混淆 | Results 节 Fig. 4I-J |
| scDORI 的 Topic 数量（K=31）为超参数 | 不同 K 值可能产生不同的调控模块划分，影响 TR 识别 | 结果对超参数的敏感性未报告 | 进行 K 敏感性分析，报告不同 K 下的 TR 稳定性 | Results 节「scDORI identified 31 Topics」 |
| 抑制评分的计算依赖「抑制性 motif」的注释 | motif 注释库可能不完整或存在偏差，低估非经典抑制因子 | 若抑制因子注释不全，TRS 可能低估真实抑制强度 | 用无偏的蛋白-DNA 结合实验（如 HT-SELEX）补充 motif 注释 | Methods 节（未提供细节） |
| 与已有 eGRN 方法的比较可能不全面 | 对比方法的选择和调参可能影响结论 | 方法学优势的声明需要公平比较 | 在多个基准数据集上系统比较，报告所有方法的超参数设置 | Results 节 Extended Data Fig. 2C |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **抑制性调控是状态稳定性的关键机制**：在 TF–DNA 互作研究中，不要只关注激活因子。本文展示了状态特异性抑制因子（如 MYT1L）通过直接结合并抑制替代状态的主调控因子来维持状态身份。可迁移到其他系统：寻找「状态屏障因子」时，应同时分析抑制性 motif 和染色质关闭事件。

2. **连续主题建模优于离散聚类**：将细胞建模为多个调控程序的连续混合（而非硬聚类），能捕捉状态内异质性和中间态。对于 TF–DNA 互作研究，这意味着同一细胞中多个调控程序可以共存，TF 的调控作用应视为「概率性」而非「开关式」。

3. **多组学联合建模增强调控推断**：同时建模表达和染色质可及性，并施加 TF→motif→peak→基因的调控链约束，比单独使用任一模态更能识别因果调控关系。可迁移：在 TF 结合位点预测中，加入染色质可及性作为中间层可提高精度。

4. **「可及性-表达不一致」可作为可塑性指标**：染色质已开放但未转录的基因区域可能代表「预备状态」（primed state），这种不一致性可用于量化细胞的状态转换潜力。可迁移到 TF–DNA 结合研究：预测 TF 结合时，应考虑「已结合但未激活」的状态。

5. **计算预测 + 功能验证的闭环设计**：本文从计算预测（scDORI）到分子验证（CUT&RUN、ATAC-seq）再到功能验证（体内移植）的完整路径，是建立可信度的关键。可迁移：任何 TF–DNA 互作的计算预测都应设计对应的实验验证方案。

6. **空间转录组可作为调控模型的独立验证**：用 Visium 数据验证「高转换潜力的状态对在空间上邻近」这一预测，提供了不依赖表达数据的独立验证维度。可迁移：TF–DNA 互作模型的空间预测可用空间组学验证。

---

## 15 与已有知识连接

- **Neftel et al. 2019（Cell）**：定义了 GB 的四种经典细胞状态（OPC-like、NPC-like、AC-like、MES-like）。本文在此基础上增加了「神经元样」状态，并提供了调控层面的解释。可连接：本文的 Topic 可映射到这些经典状态。
- **SCENIC（Aibar et al. 2017）**：基于 motif 的 regulon 推断方法。本文的 scDORI 在概念上类似但更可扩展，且支持抑制性调控。可连接：SCENIC 的 regulon 可作为 scDORI 的输入或验证。
- **Pando（Fleck et al. 2022）**：结合 TF 结合位点与染色质可及性的 GRN 推断。本文的 scDORI 与之类似但使用深度学习框架。可连接：Pando 的预测可作为 scDORI 的基准。
- **Burdziak et al. 2023（引用为「Inspired by Burdziak et al.」）**：可塑性评分的灵感来源。可连接：本文扩展了该评分到 GB 多组学场景。
- **Enformer / Basenji（Avsec et al. 2021）**：从序列预测表达/染色质的深度学习模型。scDORI 可视为将类似思路应用于单细胞肿瘤数据。可连接：Enformer 的序列特征可作为 scDORI 的输入。
- **MYT1L 在神经发育中的角色（Mall et al. 2017）**：MYT1L 是神经元分化的已知调控因子。本文将其在 GB 中的角色与发育功能连接。可连接：发育生物学中的「谱系屏障」概念。
- **TCGA GB 数据**：作者用 TCGA 数据验证 MYT1L 表达与预后的相关性。可连接：公共数据库验证计算预测。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：跨癌种「可塑性屏障因子」的系统性发现
- **名称**：Pan-cancer plasticity barrier factor discovery
- **来源局限/观察**：本文在 GB 中发现 MYT1L 作为神经元样状态的抑制屏障；类似机制可能存在于其他肿瘤类型。
- **核心假设**：在多种肿瘤中，低可塑性状态由状态特异性抑制因子维持，这些因子可通过「抑制性 motif + 染色质关闭」模式识别。
- **初步方法**：将 scDORI 应用于 TCGA 或 CCLE 的多癌种多组学数据；识别各状态特异性抑制因子；用 CRISPR 筛选验证候选因子的功能。
- **验证方式**：计算预测的抑制因子在独立数据集中可重复；功能实验显示敲除后状态转换增加。
- **创新状态**：unverified

### 候选 2：TF–DNA 结合预测的「抑制性」扩展
- **名称**：Repression-aware TF–DNA binding prediction
- **来源局限/观察**：现有 TF–DNA 结合预测模型（如 DeepSEA、Enformer）主要预测激活型结合；本文显示抑制性结合在状态维持中同样关键。
- **核心假设**：在 TF–DNA 结合预测中显式加入抑制性上下文（如共抑制因子、组蛋白修饰状态）可提高预测精度。
- **初步方法**：在现有深度学习模型基础上，加入抑制性标记（如 H3K27me3、共抑制因子 ChIP-seq）作为额外输入；在 GB 和神经发育数据上训练和评估。
- **验证方式**：与现有模型在 TF 结合预测基准上比较 AUROC/AUPRC；用 CUT&RUN 数据验证预测的抑制性结合位点。
- **创新状态**：unverified

### 候选 3：基于 TAP-TRS 的肿瘤进化轨迹预测
- **名称**：TAP-TRS guided tumor evolution trajectory prediction
- **来源局限/观察**：本文的 TAP-TRS 指标与空间邻近性和时间共现相关，但未直接预测肿瘤进化。
- **核心假设**：TAP-TRS 矩阵可以预测肿瘤在治疗压力下的状态转换方向。
- **初步方法**：将 TAP-TRS 作为先验，结合谱系追踪数据（如 barcode 或线粒体突变）构建状态转换的马尔可夫模型；在治疗前后样本中验证。
- **验证方式**：预测的状态转换方向与实际谱系追踪结果一致；预测的耐药状态与临床预后相关。
- **创新状态**：unverified

### 候选 4：MYT1L 作为治疗靶点的机制解析
- **名称**：Mechanistic dissection of MYT1L as a therapeutic target
- **来源局限/观察**：MYT1L 过表达在体内限制肿瘤生长，但其下游机制和潜在耐药途径未知。
- **核心假设**：MYT1L 通过直接抑制特定增强子来关闭替代状态程序；长期 MYT1L 激活可能导致代偿性去抑制。
- **初步方法**：MYT1L 过表达/敲除后的时间序列 ATAC-seq + RNA-seq；结合 CUT&RUN 鉴定直接靶标；用 CRISPR 筛选寻找 MYT1L 功能的合成致死伙伴。
- **验证方式**：MYT1L 直接靶标的染色质状态变化与表达变化一致；合成致死伙伴的敲除增强 MYT1L 的抗肿瘤效果。
- **创新状态**：unverified

### 候选 5：将 scDORI 扩展到 TF–DNA 结合机制解析
- **名称**：scDORI-based TF–DNA binding mechanism elucidation
- **来源局限/观察**：scDORI 目前用于推断调控网络，但其框架可扩展为显式建模 TF–DNA 结合的序列决定因素。
- **核心假设**：scDORI 的 Topic 特异性 eGRN 可用于训练序列到结合强度的预测模型，揭示状态特异性 TF 结合 motif 的上下文依赖。
- **初步方法**：从 scDORI 的 Topic 中提取高置信度的 TF–peak 对；用这些对训练基于序列的深度学习模型（如 CNN/Transformer）；分析模型注意力以识别关键序列特征。
- **验证方式**：模型在独立 ChIP-seq 数据上预测准确；注意力分析识别的 motif 与已知结合位点一致。
- **创新状态**：unverified