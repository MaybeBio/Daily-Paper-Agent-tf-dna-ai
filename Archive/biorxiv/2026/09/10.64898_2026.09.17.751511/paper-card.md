## 01 基本信息

- **标题**：SurfGraphPro: Integrating Protein Language Models with Geometric Deep Learning On Coarse Protein Surfaces for Binding Site Prediction
- **作者**：Adela Habib; Li-Wei Hung; Kaetlyn Gibson; Martha Dix; Patrick Sum Guy Chain; Bin Hu
- **单位**：未提供（作者声明来自 Los Alamos National Laboratory，依据 Competing Interest Statement）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026（预印本日期 2026-09-24）
- **论文类型**：预印本（方法学/算法论文）
- **领域**：蛋白质结合位点预测；几何深度学习；蛋白质语言模型
- **关键词**：binding site prediction, geometric deep learning, protein language model, coarse-grained surface, solvent-excluded surface mesh
- **DOI/arXiv 号**：10.64898/2026.09.17.751511
- **代码**：未提供
- **数据**：未提供（文中提及测试于 diverse binding interfaces 与 antibody-antigen complexes，但具体数据集未在摘要中列出）
- **阅读日期**：未提供
- **在该方向中的位置**：本文属于「蛋白质-配体/蛋白质-蛋白质结合位点预测 × 几何深度学习 + 蛋白质语言模型」交叉方向。对于 TF–DNA 互作课题，其核心可迁移点在于：用 PLM embedding 替代手工特征与 MSA，在粗粒化分子表面上做几何 transformer 预测结合位点——这一「表面几何 + 进化嵌入」的范式可直接迁移到 TF–DNA 结合界面预测（如预测 DNA 结合残基或 TF 结合界面）。

---

## 02 一句话总结

本文提出 SurfGraphPro，一种在粗粒化三角化溶剂排除表面上、以氨基酸残基为中心构建 patch、用蛋白质语言模型 embedding 替代 MSA 与手工特征、通过几何 transformer 预测蛋白质结合位点的方法，在保持与现有最先进表面模型相当精度的同时实现约 18–28 倍加速。

---

## 03 研究问题

- **具体问题**：如何在不依赖昂贵 MSA 与大量手工特征工程的前提下，快速且准确地预测蛋白质结合位点（binding interface）？
- **为什么重要**：结合位点预测是理解分子互作、指导蛋白质工程与药物设计的核心步骤；现有表面模型精度高但计算开销大，难以扩展到大规模蛋白质组学场景。
- **现有方法为何不足**：现有 surface-based 模型（如 MaSIF 类方法）依赖大量手工设计的物理化学特征（如静电、疏水性、几何形状等），且需要 MSA 生成进化信息，计算成本高、流程复杂。
- **精确研究问题（Can ... ?）**：Can protein language model embeddings, when coupled with geometric transformers on coarse-grained protein surfaces, replace traditional MSA-derived features and hand-crafted physicochemical descriptors for binding site prediction without sacrificing accuracy, while achieving significant computational speedup?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文摘要的框架性描述，标注为「仅本文框架」；未做外部文献核验。

1. **早期方法（序列/模板驱动）**：基于序列保守性、模板比对或简单结构特征预测结合位点。优点：快速；局限：精度有限，难以捕捉几何互补性。
2. **基于原子/残基级结构的方法**：利用原子坐标与残基接触图，结合传统机器学习或早期深度学习。优点：引入结构信息；局限：特征工程繁重，泛化性受限。
3. **基于表面的几何深度学习方法（如 MaSIF 系列）**：在溶剂排除表面网格上定义几何特征，用深度学习（如 geodesic CNN、transformer）编码表面 patch。优点：精度高，能捕捉几何与化学互补性；局限：依赖大量手工特征与 MSA，计算开销大。
4. **蛋白质语言模型（PLM）时代**：PLM 从大规模序列语料中学习进化与结构隐含信息，可替代 MSA 与手工特征。优点：无需 MSA、特征自动学习；局限：尚未与表面几何表示有效结合。
5. **本文主张的位置**：首次将 PLM embedding 与粗粒化表面几何表示结合，用几何 transformer 在残基中心 patch 上做结合位点预测，声称在保持精度的同时实现 18–28 倍加速，并首次验证该组合在抗体-抗原等挑战性界面上有效。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 计算开销大 | 现有 surface-based 模型对约 100 到数千氨基酸的蛋白质预测耗时显著 | 依赖 MSA 生成进化信息 + 大量手工物理化学特征工程 | 摘要：现有方法依赖 "computationally expensive multiple sequence alignments and hand-crafted features" |
| 特征工程繁重 | 需要人工设计静电、疏水、几何等描述符 | 传统表面模型将物理化学知识手工编码为输入特征 | 摘要：现有方法 "rely on extensive physicochemical feature engineering" |
| 精度与速度难以兼得 | 高精度模型通常计算慢，快速方法精度不足 | 表面网格细粒度 + 特征维度高导致计算瓶颈 | 摘要：SurfGraphPro 在 "maintaining comparable accuracy" 的同时实现加速 |
| 挑战性界面（抗体-抗原）预测困难 | 抗体-抗原界面几何与化学互补性复杂，传统方法易失效 | 界面大、形状互补性强、进化信号弱 | 摘要：方法在 "challenging antibody-antigen complexes" 上保持精度 |

---

## 06 核心思想

### 1) 表面方法
- 输入蛋白质结构，计算溶剂排除表面（solvent-excluded surface）并三角化。
- 将表面网格粗粒化（downsample）为以氨基酸残基为中心的 patch。
- 用蛋白质语言模型（PLM）生成每个残基的 embedding，作为 patch 的节点特征。
- 用几何 transformer 在粗粒化表面 patch 上编码几何与进化信息，输出每个残基/表面点的结合位点概率。

### 2) 核心洞察
- **PLM embedding 可替代 MSA 与手工特征**：PLM 已隐式编码进化与结构信息，无需显式 MSA 或手工物理化学描述符。
- **粗粒化表面保留关键几何信息同时大幅降低计算量**：以残基为中心的 patch 而非原子级网格，在保持表面几何互补性表征能力的同时减少节点数。
- **几何 transformer 能有效融合「几何结构」与「进化语义」两类异质信息**：在表面网格上做注意力，使模型同时感知局部形状与序列进化上下文。

### 3) 可能的普适教训 [Analysis]
- 对于 TF–DNA 互作课题：**「用 PLM 替代 MSA + 手工特征」是可迁移的核心思想**——TF 的 DNA 结合域（DBD）保守性高，PLM embedding 可能比传统 PSSM 更高效地编码结合特异性信息。
- **「粗粒化 + 残基中心 patch」是降低计算复杂度的通用策略**：在 TF–DNA 界面预测中，可将 DNA 结合残基作为中心构建 patch，而非全原子网格。
- **几何 transformer 是融合「结构 + 序列进化」的通用架构**：适用于任何「表面/界面几何 + 进化信息」联合建模的任务。

---

## 07 方法总览

- **输入**：蛋白质三维结构（推测为 PDB 格式或等效结构文件）；序列（用于 PLM 推理）。
- **输出**：每个残基（或表面点）的结合位点概率/标签。
- **模块**：
  1. 表面生成模块：计算溶剂排除表面并三角化。
  2. 粗粒化模块：将表面网格下采样为残基中心 patch。
  3. 特征提取模块：PLM 生成残基级 embedding。
  4. 几何编码模块：几何 transformer 在 patch 上编码结构与进化信息。
  5. 预测头：输出结合位点概率。
- **训练**：监督学习，标签为已知结合位点（具体损失函数、优化器、训练集未在摘要中提供）。
- **工具**：未提供（推测使用 PyTorch Geometric 或类似几何深度学习库，但无证据）。
- **反馈回路**：未提及（无主动学习或迭代优化机制）。
- **文字流程**：输入蛋白质结构 → 计算溶剂排除表面并三角化 → 下采样为残基中心 patch → 用 PLM 为每个残基生成 embedding → 将 embedding 作为节点特征输入几何 transformer → transformer 在 patch 内做注意力，融合几何与进化信息 → 预测头输出每个残基的结合位点概率 → 与真实标签计算损失并反向传播更新参数。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 溶剂排除表面生成与三角化 | 生成蛋白质表面的几何表示 | 结合位点本质上是表面几何与化学性质的函数 | 输入：原子坐标；输出：三角化表面网格 | 摘要：方法 "operates on coarse-graphed triangulated protein surfaces, utilizing solvent-excluded surface meshes" | 预期：移除后无表面几何可编码，模型退化为序列方法，失去几何互补性信息 [Analysis] |
| 粗粒化（残基中心 patch） | 将表面网格下采样为残基级 patch | 降低计算复杂度，使模型可扩展到数千氨基酸蛋白 | 输入：三角化表面；输出：残基中心 patch 集合 | 摘要：表面 "downsampled into amino acid residue centered patches" | 预期：移除后节点数剧增，计算开销上升，可能无法处理大蛋白 [Analysis] |
| PLM embedding 生成 | 为每个残基生成进化/语义特征 | 替代 MSA 与手工物理化学特征，消除昂贵预处理 | 输入：氨基酸序列；输出：残基级 embedding 向量 | 摘要：利用 "evolutionary information directly from protein language model embeddings, eliminating the need for computationally expensive multiple sequence alignments and hand-crafted features" | 预期：移除后需回归 MSA + 手工特征，速度优势消失 [Analysis] |
| 几何 transformer | 在表面 patch 上融合几何与进化信息 | 同时编码局部形状互补性与序列进化上下文 | 输入：patch 节点特征（PLM embedding + 几何位置）；输出：更新后的节点表示 | 摘要：方法 "bridges protein language models with surface-based structural representations" | 预期：移除后无法联合建模几何与进化信息，精度可能下降 [Analysis] |
| 预测头 | 输出结合位点概率 | 将学习到的表示映射为结合位点标签 | 输入：transformer 输出表示；输出：每个残基的结合位点概率 | 摘要：方法用于 "binding site prediction" | 预期：移除后无法产生预测 [Analysis] |

> 注：以上「预期影响」均为 [Analysis] 推断，摘要中未提供消融实验数据。

---

## 09 关键公式符号

**不适用**。摘要中未提供任何数学公式、损失函数或模型架构的符号化描述。所有数值（18–28 倍加速）为实验结果的文字描述，无公式支撑。

---

## 10 实验设计与证据链

- **数据集**：未提供（摘要仅提及 "diverse binding interfaces, including challenging antibody-antigen complexes"）。
- **规模**：未提供（蛋白质数量、残基数量范围未给出）。
- **指标**：未提供（未说明使用 AUC、DCC、F1 或其他指标）。
- **基线**：未提供（仅提及 "current state-of-the-art surface-based model"，未指名具体模型）。
- **预算/硬件**：未提供。
- **骨干/仪器**：未提供。
- **Oracle 输入**：未提供（推测使用已知结构，但无证据）。
- **评测协议**：未提供（无交叉验证、独立测试集等描述）。

| 实验 | 检验的 Claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| 速度对比 | SurfGraphPro 比现有 SOTA surface-based 模型更快 | 蛋白质大小约 100 到数千氨基酸 | 平均加速 18–28 倍 | 方法在速度上显著优于现有表面模型 | 未说明加速的具体测量方式（端到端 vs 推理）、硬件条件、是否包含 MSA 时间 | 摘要 |
| 精度对比 | SurfGraphPro 精度与现有 SOTA 相当 | 多样结合界面，含抗体-抗原复合物 | "maintaining comparable accuracy" | 方法在精度上不逊于现有模型 | 未提供具体数值、误差棒、统计显著性检验；"comparable" 定义模糊 | 摘要 |

> 注：摘要中未提供任何具体数值（除加速倍数外）、图表引用或统计细节。所有实验描述均为定性。

---

## 11 结论正确解读

- **任务范围**：本文解决的是蛋白质结合位点预测（binding site prediction），即预测蛋白质表面上参与结合的残基/区域。**注意：本文并未区分配体类型（小分子、肽、蛋白质、DNA/RNA）**，摘要中未明确说明是否包含蛋白质-DNA 互作界面。
- **Oracle/真值输入**：方法需要蛋白质三维结构作为输入（表面计算的前提），因此**不适用于仅有序列的场景**；PLM 部分仅需序列，但整体流程依赖结构。
- **端到端状态**：方法声称是端到端可训练的（从结构+序列到预测），但摘要未明确说明训练流程是否完全可微（表面生成与粗粒化步骤可能不可微）。
- **算力成本**：加速 18–28 倍是相对现有 surface-based 模型的**相对**加速，绝对算力成本未报告；PLM 推理本身有固定开销。
- **历史数据依赖**：PLM 预训练于大规模序列语料，其 embedding 质量依赖预训练数据的覆盖度与偏差。
- **模型依赖**：结果依赖 PLM 的选择（未指明具体模型，如 ESM-2、ProtTrans 等）与几何 transformer 架构细节（未提供）。
- **最难情形**：摘要未讨论失败案例或最难情形（如低质量结构、同源寡聚界面、DNA 结合界面等）。
- **群体/领域边界**：结论仅适用于「有结构、可计算溶剂排除表面」的蛋白质；未验证于膜蛋白、 intrinsically disordered regions 等特殊场景。
- **不确定性**：未提供置信度校准、不确定性量化或误差分析。

**有边界的复述**：SurfGraphPro 在「有已知三维结构的蛋白质」上，用 PLM embedding + 粗粒化表面 + 几何 transformer，能在与现有 surface-based 模型相当的精度下实现 18–28 倍加速；该结论仅基于摘要中的定性描述，未提供具体数据集、指标与统计细节，且未明确覆盖蛋白质-DNA 互作场景。

---

## 12 作者自认局限

在提供的材料（摘要 + 声明）中，**未发现作者明确承认的局限**。作者未在摘要中讨论方法的失败模式、适用边界或潜在缺陷。

**作者提及的相关约束**（非正式局限）：
- 方法需要蛋白质结构作为输入（隐含约束，因表面计算依赖结构）。
- 作者声明 Los Alamos National Laboratory 正在申请相关专利（Competing Interest Statement），这可能影响方法的开源可用性。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 摘要未提供具体数据集与指标 | "comparable accuracy" 可能掩盖特定界面类型上的显著性能差距 | 无法判断方法在 TF–DNA 等特定互作类型上的真实表现 | 要求作者提供按互作类型分层的性能报告（如 protein-protein vs protein-DNA vs protein-small molecule） | 摘要仅定性描述 "comparable accuracy" |
| 加速 18–28 倍的计算口径不明确 | 加速可能仅指推理阶段，未包含 PLM embedding 生成时间；或对比基线未做公平优化 | 若包含 MSA 时间，加速可能更显著；若仅推理，实际端到端加速可能远低于 18–28 倍 | 要求提供端到端时间对比（含 MSA/PLM/表面计算/推理全流程）与硬件配置 | 摘要仅称 "on average ~18-28× speedup" |
| 粗粒化为残基中心 patch 可能丢失原子级几何细节 | 对需要精确原子接触的界面（如 DNA 碱基与残基侧链的氢键网络），残基级 patch 可能过于粗糙 | TF–DNA 互作依赖原子级互补性，残基级粗粒化可能不足以捕捉 | 在 TF–DNA 数据集上对比残基级 vs 原子级表面 patch 的预测精度 | 摘要称表面 "downsampled into amino acid residue centered patches" |
| 未指明 PLM 具体型号与版本 | 不同 PLM（ESM-2, ProtTrans, ProstT5 等）的 embedding 质量差异显著 | 结果的可复现性与可迁移性受影响 | 要求作者披露 PLM 型号、版本与微调策略 | 摘要仅称 "protein language model embeddings" |
| 未讨论 DNA/RNA 结合位点 | 摘要仅提及 "binding interfaces" 与 "antibody-antigen complexes"，未明确是否包含核酸结合蛋白 | 若方法未在核酸结合蛋白上验证，则对 TF–DNA 课题的迁移需谨慎 | 在 TF–DNA 基准（如 TFBS 预测数据集）上独立测试 | 摘要未提及核酸相关实验 |
| 专利声明可能限制方法可用性 | 若方法不开源，社区难以复现与改进 | 影响方法的科学影响力与可迁移性 | 关注后续是否发布代码与模型权重 | Competing Interest Statement |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **PLM embedding 替代 MSA 的范式**：本文核心主张是 PLM embedding 可完全替代 MSA 与手工物理化学特征。对于 TF–DNA 互作课题，这意味着：**在预测 TF 的 DNA 结合残基或结合界面时，可尝试直接用 ESM-2 等 PLM 的 per-residue embedding 作为输入特征，替代传统的 PSSM/位置特异性打分矩阵**。迁移方式：将 TF 序列输入 PLM，取 DBD 区域残基的 embedding 作为特征，输入下游分类器或几何模型。

2. **粗粒化表面 + 残基中心 patch 的计算策略**：将全原子表面下采样为残基级 patch，大幅降低图规模。对于 TF–DNA 互作：**可将 DNA 结合域表面按残基中心构建 patch，每个 patch 包含该残基周围局部表面几何 + PLM embedding**，用于预测该残基是否参与 DNA 结合。迁移方式：在 TF 结构上计算溶剂排除表面，按残基中心聚类表面点，构建 patch 图。

3. **几何 transformer 融合「结构 + 进化」的架构思路**：在表面网格上做注意力，使模型同时感知局部形状与序列上下文。对于 TF–DNA 课题：**可设计一个双通道几何 transformer，一个通道编码 TF 表面几何，另一个通道编码 DNA 结合 motif 的序列上下文，在交叉注意力中融合**，用于预测结合界面或结合亲和力。

4. **速度-精度权衡的评估框架**：本文强调在保持精度的同时追求速度。对于 TF–DNA 课题：**在筛选全基因组 TF 结合位点时，速度是关键瓶颈；可借鉴本文的「粗粒化 + PLM 特征」策略，构建快速筛选模型，再用高精度方法（如 MD 或对接）验证候选位点**。

5. **「首次组合」的定位策略**：本文声称是首个将 PLM 与粗粒化表面几何结合的工作。对于 TF–DNA 课题：**可探索「PLM + 表面几何」在核酸结合蛋白上的首次应用，作为差异化创新点**，但需先验证本文方法在蛋白质-DNA 界面上的可迁移性。

---

## 15 与已有知识连接

- **MaSIF（Molecular Surface Interaction Fingerprinting）系列**：本文明确将自己定位为 surface-based 模型的改进，其对比基线应为 MaSIF 或类似方法。MaSIF 使用手工几何与化学特征在溶剂排除表面上做深度学习，本文用 PLM embedding 替代这些特征。→ 对 TF–DNA 课题：MaSIF 已有应用于蛋白质-DNA 界面预测的变体，可对比本文方法与 MaSIF-DNA 类方法的性能。
- **ESM-2 / ProtTrans 等蛋白质语言模型**：PLM 已被广泛用于预测蛋白质功能、结构、互作位点。本文的创新在于将 PLM 与表面几何结合。→ 对 TF–DNA 课题：已有工作用 ESM-2 预测 DNA 结合残基（如 DNABind 类方法），本文的增量在于引入表面几何约束。
- **几何深度学习在结构生物学中的应用**：如 GVP-GNN（Geometric Vector Perceptron）、SE(3)-Transformer 等，已在蛋白质设计、互作预测中应用。本文的几何 transformer 属于这一谱系。→ 对 TF–DNA 课题：可借鉴 GVP 的向量特征编码方式处理 DNA 磷酸二酯键骨架的方向性。
- **TF–DNA 互作预测的现有方法**：如 DeepTFBS、TFBSshape（基于 DNA 形状特征）、DeepBind（序列-based）。本文方法属于「结构-based」路线，与序列-based 方法互补。→ 可探索将本文的「表面几何 + PLM」特征与 DNA 形状特征（如 DNAshape）融合，提升 TF 结合位点预测精度。
- **候选方向（未验证）**：本文方法若扩展至蛋白质-DNA 界面，需处理 DNA 的刚性棒状几何与 TF 的柔性 loop 的互补性，这比蛋白质-蛋白质界面更复杂。可参考 HADDOCK 或 ATTRACT 等对接方法中的 DNA 几何处理策略。

---

## 16 研究想法

> **Agent 生成的研究候选**

### 候选 1：SurfGraphPro-DNA——将 SurfGraphPro 范式迁移至 TF–DNA 结合位点预测
- **名称**：TF-DNA Surface Binding Predictor
- **来源局限/观察**：本文方法未明确验证于蛋白质-DNA 界面；TF–DNA 互作具有独特的几何特征（DNA 双螺旋的大沟/小沟、碱基特异性氢键），与蛋白质-蛋白质界面不同。
- **核心假设**：PLM embedding + 粗粒化表面几何可有效编码 TF 的 DNA 结合偏好，且比传统 PSSM 特征更高效。
- **初步方法**：在 TF 结构上计算溶剂排除表面，以 DBD 残基为中心构建 patch；用 ESM-2 生成残基 embedding；几何 transformer 编码 patch；标签为已知 DNA 结合残基（如来自 BioLiP 或 PDB 的 TF-DNA 复合物）。对比基线：PSSM + 手工特征 + 相同几何 backbone。
- **验证方式**：在 TF-DNA 基准数据集（如 BioLiP 的 DNA-binding 子集）上评估 AUC、F1；与现有 DNA 结合残基预测方法（如 DNABind、TargetDNA）对比。
- **可能的失败模式**：粗粒化表面可能丢失 DNA 结合所需的原子级细节（如碱基特异性接触）；PLM embedding 可能未编码 DNA 结合特异性所需的构象变化信息。
- **创新状态**：unverified（本文未涉及 DNA 界面，需独立验证）

### 候选 2：双通道几何 transformer——联合编码 TF 表面与 DNA 形状特征
- **名称**：Dual-Surface TF-DNA Interface Transformer
- **来源局限/观察**：本文仅编码蛋白质表面；TF–DNA 互作是双侧的，DNA 的局部形状（roll, tilt, shift 等）显著影响结合特异性。
- **核心假设**：联合编码 TF 表面几何与 DNA 局部形状特征，可提升结合位点预测精度，优于仅编码 TF 表面。
- **初步方法**：在 SurfGraphPro 基础上增加第二通道：对 DNA 片段计算 DNAshape 特征（或 DNA 表面几何），在交叉注意力层与 TF 表面 patch 融合。输出为 TF 残基的 DNA 结合概率。
- **验证方式**：在 TF-DNA 复合物数据集上对比单通道 vs 双通道的 AUC；分析注意力权重是否对应已知的 DNA 结合 motif。
- **可能的失败模式**：DNA 柔性大，单一静态结构可能不足以表征结合构象；双通道增加计算复杂度。
- **创新状态**：unverified（需结合 DNAshape 工具与本文架构）

### 候选 3：PLM embedding 与 MSA 特征在 TF 结合位点预测中的系统对比
- **名称**：PLM vs MSA for TF-DNA Binding Prediction
- **来源局限/观察**：本文主张 PLM 可替代 MSA，但未提供系统对比；TF 家族（如 C2H2、bZIP、homeodomain）的进化保守性模式不同，PLM 与 MSA 的相对优劣可能因家族而异。
- **核心假设**：PLM embedding 在高通量场景下优于 MSA，但在低同源性 TF 家族上可能不如 MSA 敏感。
- **初步方法**：在多个 TF 家族数据集上，分别用 PLM embedding、PSI-BLAST PSSM、HHblits 特征训练相同 backbone 模型，对比精度与速度。
- **验证方式**：分家族评估 AUC、F1、推理时间；统计检验（如 Wilcoxon signed-rank test）。
- **可能的失败模式**：PLM 与 MSA 特征高度相关，差异不显著；TF 家族数据集规模不足。
- **创新状态**：unverified（需独立实验）

### 候选 4：粗粒化表面分辨率对 TF-DNA 结合位点预测的影响
- **名称**：Surface Granularity-Accuracy Trade-off for TF-DNA
- **来源局限/观察**：本文选择残基中心 patch 作为粗粒化粒度，但未讨论不同粒度（原子级、残基级、二级结构级）对精度的具体影响；TF-DNA 界面可能对粒度更敏感。
- **核心假设**：存在最优粗粒化粒度，在精度与速度间取得平衡；TF-DNA 界面的最优粒度可能比蛋白质-蛋白质界面更细。
- **初步方法**：在固定 backbone 下，系统变化 patch 粒度（如 1Å、3Å、5Å、残基级），在 TF-DNA 数据集上评估精度-速度 Pareto 曲线。
- **验证方式**：绘制精度 vs 推理时间曲线；确定 Pareto 最优粒度。
- **可能的失败模式**：粒度影响因数据集而异，难以得出普适结论。
- **创新状态**：unverified（需系统实验）

### 候选 5：将 SurfGraphPro 的「表面 + PLM」特征用于 TF-DNA 结合亲和力预测
- **名称**：Surface-PLM Features for TF-DNA Binding Affinity
- **来源局限/观察**：本文仅做结合位点（二分类）预测；TF-DNA 结合亲和力（连续值）预测是更细粒度的任务，现有方法多基于序列或对接打分。
- **核心假设**：SurfGraphPro 学习到的表面-进化联合表示可迁移至亲和力预测任务，优于纯序列特征。
- **初步方法**：用 SurfGraphPro 预训练模型提取 TF 表面 patch 表示，与 DNA 序列特征拼接，训练回归模型预测结合亲和力（如来自 SELEX 或 PBMC 数据）。
- **验证方式**：在标准 TF-DNA 亲和力数据集上评估 Pearson/Spearman 相关系数；与 DeepBind、DeepSELEX 对比。
- **可能的失败模式**：亲和力数据噪声大；表面表示可能不包含结合强度所需的能量信息。
- **创新状态**：unverified（需预训练模型与亲和力数据）