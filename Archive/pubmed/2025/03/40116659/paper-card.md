## 01 基本信息

- **标题**: AttentionGRN: a functional and directed graph transformer for gene regulatory network reconstruction from scRNA-seq data
- **作者与单位**: Gao, Zhen; Su, Yansen; Tang, Jin; Jin, Huaiwan; Ding, Yun; Cao, Rui-Fen; Wei, Pi-Jing; Zheng, Chun-Hou（单位未在摘要中提供）
- **期刊/平台**: Briefings in Bioinformatics
- **年份**: 2025-03-21
- **论文类型**: 方法学（Method）——提出新模型
- **领域**: 计算生物学 / 单细胞转录组学 / 基因调控网络推断
- **关键词**: scRNA-seq; gene regulatory network; graph transformer; directed graph; functional modules
- **DOI/arXiv 号**: 10.1093/bib/bbaf118
- **代码**: https://github.com/Phoebe-GaoZhen/AttentionGRN/tree/master
- **数据**: BEELINE 数据集（https://doi.org/10.5281/zenodo.3378975），预处理后见 Supplementary Table S1
- **阅读日期**: 未提供
- **在该方向中的位置**: 本文属于「蛋白质-DNA 互作（TF–DNA 结合机制）× AI 方法」方向中的**GRN 推断**子领域。它聚焦于从 scRNA-seq 数据中重建 TF–靶基因调控网络，属于**监督学习 + 图 Transformer** 路线。与物理模拟（MD/对接）无关，但与 TF–DNA 结合机制直接相关——其预测的 TF–靶基因边即代表 TF 对下游基因的调控关系（通常通过 TF 结合靶基因启动子区域实现）。本文的核心贡献在于将图 Transformer 引入 GRN 推断，并设计了有向结构编码和功能基因采样策略。

## 02 一句话总结

本文提出 AttentionGRN，一个基于图 Transformer 的监督学习模型，通过软编码（soft encoding）替代 GNN 的硬编码消息传递，结合有向结构编码和功能基因采样，在 88 个 BEELINE 基准数据集上实现了优于现有方法的 GRN/TRN 推断性能，并在人成熟肝细胞中识别出新的 hub 基因和 TF–靶基因调控关系。

## 03 研究问题

- **具体问题**: 如何从 scRNA-seq 数据中准确重建基因调控网络（GRN），特别是 TF–靶基因之间的有向调控关系？
- **为什么重要**: GRN 控制细胞分化、凋亡和发育等关键生物学过程。从 scRNA-seq 重建细胞类型特异的 GRN 有助于理解正常和病理状态下的基因调控机制，为疾病治疗和生物技术应用提供基础。
- **现有方法为何不足**:
  1. 基于 CNN 的方法（如 CNNC）将基因表达数据转换为直方图，引入噪声并丢失重要特征；
  2. 直接输入表达数据的深度学习方法（如 STGRNS）忽略了 GRN 的网络结构信息；
  3. 基于 GNN 的方法（如 GENELink、GNNLink）受限于硬编码消息传递机制，存在 over-smoothing 和 over-squashing 问题，难以有效传播远距离节点信息；
  4. 混合方法（如 DeepFGRN）虽同时利用表达和结构特征，但仅识别基因的邻居而不有效传播邻居信息。
- **精确的 "Can ... ?" 研究问题**: Can a graph transformer with soft encoding, directed structural encoding, and functional gene sampling outperform existing GNN/CNN-based methods in reconstructing GRNs and TRNs from scRNA-seq data?

## 04 背景与发展脉络

*注：以下脉络基于本文框架整理，标注为「仅本文框架」，未经外部系统核验。*

- **阶段一：无监督/统计方法**（如相关性、互信息等）——利用基因表达统计相关性推断调控关系，计算效率高但精度有限，无法捕捉非线性调控。
- **阶段二：基于 CNN 的监督方法**（如 CNNC）——将 TF–靶基因对的表达数据转换为直方图输入 CNN，利用卷积提取特征。局限：直方图转换引入噪声，丢失原始数据细节。
- **阶段三：基于 Transformer 的监督方法**（如 STGRNS）——直接输入表达数据到 Transformer，避免直方图信息损失。局限：忽略 GRN 的网络结构。
- **阶段四：基于 GNN 的方法**（如 GENelink、GNNLink、DGCGRN、GATCL）——将 GRN 建模为图，通过消息传递捕捉网络结构。局限：硬编码消息传递导致 over-smoothing（节点表示趋同）和 over-squashing（远距离信息传播失效）。
- **阶段五：混合方法**（如 DeepFGRN）——同时利用表达特征和网络结构特征。局限：仅识别邻居而不有效传播邻居信息。
- **本文主张的位置**: 首次将图 Transformer 引入 GRN 推断，利用软编码（self-attention）替代硬编码消息传递，结合有向结构编码和功能基因采样，同时捕捉有向网络拓扑、全局结构和功能模块信息。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| GNN 的 over-smoothing | 多次消息传递后节点表示趋同，丧失区分度 | 硬编码消息传递机制导致信息过度混合 | Introduction 第 2 段；Results 图 6 中 GAE/GAT 性能低于 GT-DI |
| GNN 的 over-squashing | 远距离节点间信息传播失效 | 深度模型中信息被过度压缩 | Introduction 第 2 段 |
| CNN 直方图转换信息损失 | CNNC 性能低于直接输入表达数据的 STGRNS | 将表达数据转换为直方图引入噪声、丢失特征 | Results 图 3-4 中 STGRNS 优于 CNNC |
| 忽略网络结构 | 仅用表达数据的方法无法利用 GRN 拓扑信息 | 未建模基因间调控关系 | Introduction 第 3 段 |
| 邻居信息传播不足 | DeepFGRN 等混合方法仅识别邻居而不传播信息 | 缺乏有效的信息聚合机制 | Introduction 第 3 段 |
| 有向性缺失 | 部分方法将 GRN 视为无向图，丢失调控方向信息 | 未设计有向编码机制 | Methods 节 Directed structure encoding；Ablation 中移除 DI 后性能下降 |

## 06 核心思想

### 1) 表面方法
AttentionGRN 是一个监督学习模型，输入为 scRNA-seq 表达矩阵和先验 GRN（prior GRN），输出为 TF–靶基因对的调控概率。模型包含四个阶段：输入准备、信息预提取、双流特征提取、GRN 推断。双流特征提取包括：(a) 基于 Transformer 的基因表达特征提取；(b) 基于图 Transformer（GT）的有向网络结构特征提取，其中 GT 的消息传递被限制在 r-hop 邻居和功能相关基因（FN）范围内，并加入有向结构编码（DI）。

### 2) 核心洞察
- **软编码优于硬编码**: 图 Transformer 的 self-attention 机制允许自适应地聚合邻居信息，避免了 GNN 硬编码消息传递导致的 over-smoothing 和 over-squashing。
- **有向性至关重要**: GRN 本质是有向图（TF→靶基因），通过设计有向结构编码（包含入度、出度、度中心性、r-hop 源/目标邻居信息），模型能学习非对称的调控语义。
- **功能基因采样弥补结构稀疏性**: 仅依赖已知 GRN 的 r-hop 邻居可能因高阶层邻居稀疏而信息不足，通过余弦相似度筛选功能相关基因作为额外邻居，可捕捉全局功能模块信息。

### 3) 可能的普适教训 [Analysis]
- 对于生物网络推断任务，**方向性（directionality）** 是核心先验信息，显式编码方向比隐式学习更有效。
- **结构信息与功能信息互补**: 已知网络结构（先验 GRN）和表达相似性（功能相关）提供了不同维度的信息，二者结合可弥补单一来源的不足。
- 图 Transformer 的软编码机制为处理生物网络的稀疏性和异质性提供了比 GNN 更灵活的框架。

## 07 方法总览

- **输入**: 
  - scRNA-seq 表达矩阵（基因 × 细胞）
  - 先验 GRN（有向图，边表示已知/候选 TF–靶基因调控关系）
  - 基因表达子向量（TF–靶基因对的表达特征）
  
- **输出**: TF–靶基因对的调控概率（用于 GRN/TRN 重建）

- **模块**:
  1. **信息预提取**: 从先验 GRN 和表达矩阵中提取功能相关基因（FN）、r-hop 邻居、有向结构编码（DI）
  2. **基因表达特征提取**: 将 TF–靶基因对的表达子向量输入 Transformer（含位置编码和编码模块），提取 64 维表达特征
  3. **有向网络结构特征提取**: 通过 L 层图 Transformer，每层含多头自注意力、有向结构编码、前馈层，提取 64 维结构特征
  4. **GRN 推断**: 拼接表达特征和结构特征（128 维/基因，256 维/对），通过全连接层预测调控概率

- **训练**: 监督学习，使用 88 个 BEELINE 基准数据集（7 种细胞类型 × 4 类先验 GRN × 2 种预处理 × 2 种基因数），采用独立测试（GRN）和 TF-aware 三折交叉验证（TTCV，TRN）两种策略

- **工具**: PyTorch（推测，未明确说明）；Cytoscape + Cytohubba 用于 hub 基因分析

- **反馈回路**: 无显式反馈回路；模型为前馈结构

- **假设**: 
  - 先验 GRN 提供了可靠的候选调控关系
  - 功能相关基因（高表达余弦相似度）与调控关系相关
  - 有向结构编码能捕捉 GRN 的非对称调控语义

- **文字流程**: 输入 scRNA-seq 表达矩阵和先验 GRN → 信息预提取（计算 FN、r-hop 邻居、DI）→ 双流特征提取（Transformer 提取表达特征，GT 提取结构特征）→ 特征拼接 → 全连接层预测 TF–靶基因调控概率 → 输出 GRN/TRN

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 信息预提取（FN 采样） | 基于余弦相似度筛选功能相关基因 | 弥补 r-hop 邻居在高阶时的稀疏性，捕捉功能模块信息 | 输入：表达矩阵、先验 GRN；输出：FN 集合 | Ablation 中移除 FN 后性能下降（Supplementary Figs S8-S9） | 预期：失去功能模块信息，全局结构捕捉能力下降 [预期效应] |
| 有向结构编码（DI） | 编码入度、出度、度中心性、r-hop 源/目标邻居 | GRN 是有向图，需显式编码方向性以学习非对称调控语义 | 输入：先验 GRN；输出：DI 向量 | Ablation 中移除 DI 后性能显著下降（Supplementary Figs S8-S9）；Results 图 6 中 GT-DI 优于 GAE/GAT/GAN | 预期：模型退化为无向图模型，丢失调控方向信息 [预期效应] |
| 基因表达特征提取（Transformer） | 从 TF–靶基因对表达子向量提取特征 | 表达模式包含调控线索 | 输入：表达子向量；输出：64 维表达特征 | Ablation 中移除表达特征后性能下降（Supplementary Figs S8-S9） | 预期：模型仅依赖结构信息，对表达模式不敏感 [预期效应] |
| 图 Transformer 层（GT） | 通过多头自注意力聚合 r-hop 和 FN 邻居信息 | 软编码替代硬编码消息传递，避免 over-smoothing/over-squashing | 输入：节点特征 + DI；输出：64 维结构特征 | Results 图 6 中 GT-DI 优于 GAE/GAT/GAN；Ablation 中 GT 单独使用性能低于完整模型 | 预期：若替换为 GNN，将出现 over-smoothing/over-squashing 问题 [预期效应] |
| 预测层（全连接层） | 将拼接特征映射为调控概率 | 二分类（调控/非调控） | 输入：256 维拼接特征；输出：调控概率 | Results 图 3-4 中整体性能优于基线 | 预期：若移除，模型无法输出预测 [预期效应] |

## 09 关键公式符号

**公式 1（功能相关基因定义）**：
$$N_i^{(fn)} = \{j \mid \text{cosine\_similarity}(x_i, x_j) > mean_i + std_i \cdot a\}$$

- $N_i^{(fn)}$: 基因 $v_i$ 的功能相关邻居集合
- $x_i, x_j$: 基因 $i$ 和 $j$ 的表达向量
- $mean_i, std_i$: 基因 $i$ 与所有其他基因余弦相似度的均值和标准差
- $a$: 阈值超参数（范围 {2.5, 2.6, 2.7, 2.8, 2.9, 3.0}）

**公式 2（有向结构编码 DI）**：
$$DI_i = [d_i^{in}, d_i^{out}, I_i^c, T_{ir}^s, T_{ir}^t]$$

- $d_i^{in}$, $d_i^{out}$: 基因 $v_i$ 的入度和出度
- $I_i^c$: 度中心性（degree centrality）
- $T_{ir}^s$, $T_{ir}^t$: r-hop 源邻居和目标邻居的结构信息

**公式 3（度中心性）**：
$$I_i^c = \frac{d_i^{in} + d_i^{out}}{N-1}$$

- $N$: 图中节点总数

**公式 4-7（r-hop 邻居结构信息）**：
$$T_{ir}^s = [I_{ir}^{in}, I_{ir}^{out}, I_{ir}^{uc}]$$
$$T_{ir}^t = [I_{ir}^{in}, I_{ir}^{out}, I_{ir}^{uc}]$$

- $I_{ir}^{in}$, $I_{ir}^{out}$: r-hop 源/目标邻居的入度和出度信息
- $I_{ir}^{uc}$: r-hop 邻居的度中心性信息

**公式 8-13（图 Transformer 层）**：
- 多头自注意力（公式 8）：$Attention(Q, K, V) = softmax(\frac{QK^T}{\sqrt{d_k}})V$
- 多头整合（公式 9）：$MultiHead(Q, K, V) = Concat(head_1, ..., head_H)W^O$
- 加入 DI（公式 10）：$Z = MultiHead(Q, K, V) + DI$
- 层归一化（公式 11）：$LayerNorm(Z)$
- 前馈层（公式 12-13）：$FFN(x) = W_B \cdot GELU(W_A \cdot x)$

- $Q, K, V$: 查询、键、值矩阵
- $d_k$: 键向量维度
- $H$: 注意力头数
- $W_A \in \mathbb{R}^{2d \times d}$, $W_B \in \mathbb{R}^{d \times 2d}$: 前馈层权重

## 10 实验设计与证据链

**数据集**: 88 个 BEELINE 基准数据集，来自 7 种细胞类型（hESC, hHEP, mDC, mESC, mHSC-E, mHSC-GM, mHSC-L）× 4 类先验 GRN（细胞类型特异、非特异、STRING、LOF/GOF）× 2 种预处理（DATA1, DATA2）× 2 种基因数（500, 1000）。DATA1 用于 GRN 推断（44 个网络），DATA2 用于 TRN 推断（44 个网络）。

**指标**: AUROC（Area Under the Receiver Operating Characteristic curve）和 AUPR（Area Under the Precision-Recall curve）的平均值。

**基线模型**: CNNC、STGRNS、GENELink、GNNLink、DeepFGRN。

**评测协议**: 
- GRN 推断：独立测试（independent testing），正样本为 ground-truth TF–基因对，负样本为未知 TF–靶基因对，按 3:1:1 划分训练/验证/测试。
- TRN 推断：TF-aware 三折交叉验证（TTCV），确保每个 TF 在训练和测试中不重叠。

**预算/骨干/仪器**: 未提供具体硬件信息。

**Oracle 输入**: 先验 GRN（来自 BEELINE 的 ground-truth 调控关系）作为输入。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 参数敏感性分析 | 阈值 a、r-hop、GT 层数、epoch 对性能的影响 | 逐一调整参数，固定其他参数 | 最优 a 在 2.5-3.0 范围；r=1 最优；L=10 最优；epoch 因数据集而异 | 参数选择影响性能，需针对数据集调优 | 未提供所有数据集的完整参数扫描结果 | Results 图 2；Supplementary Figs S1-S7, Tables S2-S4 |
| GRN 推断性能对比 | AttentionGRN 优于现有方法 | 与 CNNC, STGRNS, GENELink, GNNLink, DeepFGRN 在 DATA1 上对比 | AttentionGRN 在大多数数据集上取得最佳 AUROC/AUPR | AttentionGRN 在 GRN 推断上具有优势 | 未提供统计显著性检验 | Results 图 3 |
| TRN 推断性能对比 | AttentionGRN 优于现有方法 | 与 CNNC, STGRNS, GENELink, GNNLink, DeepFGRN 在 DATA2 上对比 | AttentionGRN 在所有数据集上取得最佳 AUROC/AUPR | AttentionGRN 在 TRN 推断上具有优势 | 未提供统计显著性检验 | Results 图 4 |
| 消融研究 | 各模块（DI、FN、表达特征）的贡献 | 5 种模型：GT、GT+DI、GT+FN、GT+DI+FN（无表达特征）、AttentionGRN（完整） | 完整模型性能最佳；移除 DI 或 FN 均导致性能下降 | DI 和 FN 均对性能有贡献 | 未提供各消融组合的详细数值 | Results 图 5；Supplementary Figs S8-S9 |
| 图嵌入方法对比 | GT-DI 捕捉最有效的网络结构特征 | 比较 GAE（GCN）、GAT、GAN、GT-DI 四种嵌入方法 | GT-DI 性能最佳，GAE 最差 | 图 Transformer + 有向编码优于 GNN 方法 | 未提供嵌入维度、训练细节的对比 | Results 图 6 |
| hHEP 应用 | AttentionGRN 能识别新的 hub 基因和调控关系 | 预测 hHEP 的 GRN，分析 hub 基因 | 识别出 ZNF101, ZNF143, BRCA2, EED, ZNF146 等新 hub 基因；BRCA1 的 top 30 预测关联中 27 个有文献支持 | AttentionGRN 能产生生物学可解释的预测 | 未提供实验验证（如 ChIP-seq、报告基因实验） | Results 图 7；Supplementary Tables S5-S6 |

## 11 结论正确解读

- **任务范围**: 本文解决的是 GRN/TRN 推断任务，即从 scRNA-seq 表达数据和先验 GRN 中预测 TF–靶基因调控关系。这是一个**监督学习**任务，依赖先验 GRN 作为 ground truth。
- **Oracle/真值输入**: 模型使用 BEELINE 提供的 ground-truth 调控关系作为监督信号。这意味着模型性能高度依赖先验 GRN 的质量和覆盖度。
- **端到端状态**: 模型是端到端训练的，但输入包含先验 GRN（非纯表达数据驱动），因此不是完全端到端的 GRN 推断。
- **算力成本**: 未提供具体训练时间/硬件需求，仅报告平均推理时间（GRN 推断约 536 秒，TRN 推断约 108 秒）。
- **历史数据依赖**: 模型依赖先验 GRN 和 scRNA-seq 表达矩阵，两者均为静态快照，不涉及时间序列或动态信息。
- **模型依赖**: 性能依赖超参数（阈值 a、r-hop、GT 层数、epoch），需针对不同数据集调优。
- **最难情形**: 从结果看，非细胞类型特异的 GRN（如 STRING）和 LOF/GOF GRN 上性能提升相对较小，说明先验 GRN 质量对模型影响显著。
- **群体/领域边界**: 模型在 7 种细胞类型上验证，但未测试跨物种泛化能力；作者在结论中明确承认跨物种 GRN 推断是未来工作。
- **不确定性**: 未提供预测置信区间或不确定性量化；hub 基因分析基于文献验证而非实验验证。

**有边界的复述**: AttentionGRN 在 88 个 BEELINE 基准数据集上，通过图 Transformer 的软编码机制、有向结构编码和功能基因采样，在 GRN 和 TRN 推断任务上取得了优于 CNNC、STGRNS、GENELink、GNNLink 和 DeepFGRN 的平均 AUROC/AUPR 性能，并在 hHEP 中识别出有文献支持的新 hub 基因和调控关系。该结论限于监督学习框架、BEELINE 数据分布和所比较的基线模型。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 跨物种泛化 | 模型仅在单一物种（人类/小鼠）的细胞类型上验证 | 跨物种 GRN 推断是未来工作 | Conclusion 最后一段 |
| 功能相关基因识别方法 | 使用余弦相似度作为功能相关性的度量，可能不是最优 | 可探索其他功能相关性度量方法 | Conclusion 最后一段（提及"alternative methods such as community detection or clustering techniques could be explored"） |
| 计算效率 | GRN 推断任务中 AttentionGRN 运行时间最长（平均 536 秒） | 未明确提及优化方向 | Results 时间复杂度分析；Supplementary Tables S8-S9 |

*注：作者在 Conclusion 中明确提到的局限包括跨物种泛化问题和功能相关基因识别方法的改进空间。*

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 监督学习依赖先验 GRN | 模型性能可能主要来自先验 GRN 的质量而非模型设计；在无先验 GRN 的场景下（如新物种）可能失效 | 限制了模型的实用性和泛化性 | 在无先验 GRN 或先验 GRN 高度不完整的场景下测试模型性能 | Methods 节 Model input；Results 图 3-4 |
| 基线模型选择有限 | 仅比较 5 个基线（CNNC, STGRNS, GENELink, GNNLink, DeepFGRN），未包含最新的 GRN 推断方法（如基于扩散模型、LLM 的方法） | 可能高估 AttentionGRN 的相对优势 | 与更多近期 SOTA 方法（如 2023-2025 年发表的 GRN 推断工具）进行对比 | Results 节 Performance on GRN and TRN inference |
| 消融实验粒度不足 | 消融仅报告了"移除 DI"和"移除 FN"的总体效果，未报告各组件在不同数据集类型上的交互效应 | 无法判断组件贡献是否一致 | 按数据集类型（细胞类型特异 vs 非特异）分层报告消融结果 | Results 图 5；Supplementary Figs S8-S9 |
| 生物学验证深度有限 | hHEP 应用仅通过文献验证 hub 基因，未进行实验验证（如 ChIP-seq、siRNA 敲低、报告基因实验） | 预测的调控关系可能只是统计关联而非真实调控 | 对预测的新调控关系进行实验验证 | Results 图 7；Supplementary Tables S5-S6 |
| 未报告不确定性量化 | 模型输出为点估计，无置信区间或概率校准 | 实际应用中无法判断预测的可靠性 | 添加预测不确定性估计（如 MC Dropout、集成方法） | 全文未提及 |
| 超参数敏感性 | 阈值 a、r-hop、GT 层数需针对每个数据集调优，可能过拟合特定数据分布 | 影响模型的可复现性和泛化性 | 在独立测试集上评估固定超参数的性能 | Results 图 2；Supplementary Figs S1-S7 |
| 与 TF–DNA 结合机制的直接关联未验证 | 模型预测的 TF–靶基因关系未与 TF 结合位点、ChIP-seq 数据或 DNA 序列特征交叉验证 | 对于理解 TF–DNA 结合机制，需要验证预测的调控关系是否对应实际的 TF 结合事件 | 将预测的调控关系与 ChIP-seq 数据、TF 结合 motif 进行交叉验证 | 全文未涉及 |

## 14 学到什么

**Agent 提炼的知识候选**（面向蛋白质-DNA 互作 × AI/物理模拟方向）：

1. **有向结构编码（Directed Structural Encoding）**：在建模 TF–DNA 调控网络时，方向性（TF→靶基因）是关键先验。可迁移到 TF–DNA 结合预测任务中，将 DNA 序列的方向性（正/负链）和 TF 结合方向（上游/下游）显式编码为结构特征，而非隐式学习。

2. **软编码消息传递（Soft-encoded Message Passing）**：图 Transformer 的 self-attention 机制可自适应聚合邻居信息，避免 GNN 的 over-smoothing 问题。在 TF–DNA 互作预测中，可考虑用 Transformer 替代 GNN 来聚合序列上下文和结构上下文。

3. **功能相关基因采样（Functional Gene Sampling）**：通过表达相似性筛选功能相关邻居，弥补结构稀疏性。可迁移到 TF–DNA 结合预测中，将共表达基因或共调控基因作为额外上下文特征，增强模型对功能模块的感知。

4. **双流特征提取架构（Dual-stream Feature Extraction）**：将表达特征和结构特征分开提取再融合。在 TF–DNA 互作预测中，可设计双流架构分别提取序列特征（如 DNA 序列 embedding）和结构特征（如染色质可及性、3D 基因组结构），再融合预测。

5. **TF-aware 交叉验证（TF-aware Cross-Validation）**：TTCV 策略确保 TF 在训练/测试中不重叠，避免数据泄漏。在 TF–DNA 结合预测中，应采用类似的划分策略（如按 TF 划分），确保模型对新 TF 的泛化能力。

6. **hub 基因分析流程**：通过预测网络识别 hub 基因并用文献验证。可迁移到 TF–DNA 互作研究中，通过预测的调控网络识别关键 TF hub，并结合 ChIP-seq 或 motif 分析验证。

## 15 与已有知识连接

- **BEELINE 基准数据集**（Pratapa et al., 2020, Nature Methods）：本文使用的 88 个数据集源自 BEELINE，该基准已被广泛用于 GRN 推断方法评估。可连接至其他基于 BEELINE 的方法（如 GENIE3、GRNBoost2、PIDC 等）进行性能对比。
- **图 Transformer 架构**：本文的 GT 层基于标准 Transformer（Vaswani et al., 2017），但引入了图结构信息。可连接至 Graphormer（Ying et al., 2021）、GraphTrans（Wu et al., 2021）等图 Transformer 变体。
- **GRN 推断方法谱系**：从无监督方法（相关性、互信息）到监督方法（CNN、GNN、Transformer），本文属于监督 + 图 Transformer 路线。可连接至 scGSL、GENELink、GNNLink、DeepFGRN 等方法。
- **TF–DNA 结合机制**：本文预测的 TF–靶基因调控关系隐含 TF 结合靶基因启动子/增强子区域的机制。可连接至 ChIP-seq 分析、TF motif 扫描（如 MEME、HOMER）、以及基于序列的 TF 结合预测方法（如 DeepBind、DeepSEA）。
- **单细胞数据分析**：本文使用 scRNA-seq 数据，可连接至单细胞数据处理流程（如 Seurat、Scanpy）和细胞类型注释方法。
- **[Analysis] 候选方向**：本文的图 Transformer 框架可迁移至蛋白质-DNA 互作的结构预测任务（如 AlphaFold3 的蛋白质-DNA 模块），将 DNA 序列和蛋白质序列作为多模态输入，通过图注意力机制捕捉相互作用界面。

## 16 研究想法

**Agent 生成的研究候选**：

1. **名称**: TF-DNA-GT：基于图 Transformer 的 TF–DNA 结合位点预测模型
   - **来源局限/观察**: AttentionGRN 在基因层面预测 TF–靶基因调控关系，但未细化到 DNA 序列层面的结合位点预测；现有 TF 结合位点预测方法（如 DeepBind）主要基于序列，未充分利用调控网络结构信息。
   - **核心假设**: 将调控网络结构信息（TF–靶基因关系）与 DNA 序列特征结合，可提高 TF 结合位点预测的准确性。
   - **初步方法**: 构建双流架构——序列流（DNA 序列 embedding + CNN/Transformer）和结构流（调控网络中的节点特征 + 图 Transformer），融合后预测 TF 结合位点。
   - **验证方式**: 使用 ENCODE ChIP-seq 数据评估；与 DeepBind、DeepSEA 等基线对比 AUPRC。
   - **创新状态**: unverified

2. **名称**: Cross-Species GRN Transfer via Graph Transformer
   - **来源局限/观察**: 作者承认跨物种 GRN 推断是开放挑战；不同物种的调控网络存在保守性，但直接迁移面临基因同源性映射和网络结构差异问题。
   - **核心假设**: 图 Transformer 的软编码机制可学习物种间保守的调控模式，实现跨物种 GRN 推断。
   - **初步方法**: 利用同源基因映射构建跨物种图，设计域适应（domain adaptation）损失函数，在源物种上预训练、目标物种上微调。
   - **验证方式**: 在人类-小鼠-斑马鱼等跨物种数据集上评估；与单物种模型对比。
   - **创新状态**: unverified

3. **名称**: Integrating 3D Genome Structure into GRN Inference
   - **来源局限/观察**: AttentionGRN 仅使用表达数据和先验 GRN，未利用染色质构象（Hi-C）数据；TF–DNA 互作受 3D 基因组结构调控。
   - **核心假设**: 将 Hi-C 衍生的染色质互作信息作为图边权重，可提高 GRN 推断的准确性。
   - **初步方法**: 在 AttentionGRN 的图 Transformer 中引入 Hi-C 互作强度作为注意力偏置（attention bias），或在图构建阶段加入染色质互作边。
   - **验证方式**: 在具有 Hi-C 数据的细胞类型（如 hESC、hHEP）上评估；与不使用 Hi-C 的版本对比。
   - **创新状态**: unverified

4. **名称**: Uncertainty-Aware GRN Inference with Ensemble Graph Transformers
   - **来源局限/观察**: AttentionGRN 未提供预测不确定性量化；GRN 推断结果的可信度对生物学实验设计至关重要。
   - **核心假设**: 通过深度集成（deep ensemble）或 MC Dropout 量化预测不确定性，可帮助识别高置信度的调控关系。
   - **初步方法**: 在 AttentionGRN 基础上添加不确定性估计模块，输出调控概率及其置信区间。
   - **验证方式**: 评估不确定性校准（calibration）；比较高/低置信度预测的生物学验证率。
   - **创新状态**: unverified

5. **名称**: TF–DNA Binding Motif-Aware Graph Transformer
   - **来源局限/观察**: AttentionGRN 未显式利用 TF 的 DNA 结合 motif 信息；TF 结合特异性由 motif 序列决定。
   - **核心假设**: 将 TF motif 相似性作为图构建的边权重或注意力偏置，可增强模型对 TF 结合特异性的建模。
   - **初步方法**: 计算 TF motif 之间的相似性矩阵，在 AttentionGRN 的图 Transformer 中引入 motif 相似性作为额外的结构编码。
   - **验证方式**: 在 BEELINE 数据集上评估；与不使用 motif 信息的版本对比；分析 motif 相似性对预测的贡献。
   - **创新状态**: unverified