## 01 基本信息

- **标题**: Causal circuit tracing reveals distinct computational architectures in single-cell foundation models: inhibitory dominance, biological coherence, and cross-model convergence
- **作者**: Kendiukhov, Ihor
- **单位**: Department of Computer Science, University of Tübingen（由 Funding 信息推断）
- **期刊/平台**: Bioinformatics (Oxford, England)
- **年份**: 2026-06-15
- **论文类型**: 研究论文（方法 + 实证分析）
- **领域**: 单细胞基础模型可解释性 / 机制可解释性（mechanistic interpretability）
- **关键词**: sparse autoencoders (SAEs), causal circuit tracing, single-cell foundation models, Geneformer, scGPT, CRISPRi validation, ChIP-seq
- **DOI/arXiv 号**: 10.1093/bioinformatics/btag379
- **代码**: https://github.com/Biodyn-AI/bio-sae-circuits (Python)
- **数据**: 未提供（使用公开数据：Replogle et al. 2022 CRISPRi K562/RPE1, Shifrut et al. 2018 原代T细胞, Tabula Sapiens v1.0, ENCODE ChIP-seq）
- **阅读日期**: 未提供
- **在该课题方向中的位置**: 本文属于「AI 方法 × 蛋白质-DNA 互作」交叉方向中的**模型内部机制解析**分支。它不直接预测 TF–DNA 结合，而是通过因果干预（ablation）揭示单细胞基础模型内部如何编码调控信息（包括 TF→靶基因关系），并利用 ChIP-seq 和 CRISPRi 作为生物学先验来验证模型内部表征的调控真实性。对 TF–DNA 结合课题的可迁移价值在于：(1) 提供了一套「模型内部因果图 vs. 实验调控网络」的系统性验证框架；(2) 其 sign-bias correction 方法对任何使用方向性预测（如 TF 激活/抑制靶基因）的评估都至关重要；(3) 其「直接 vs 间接靶标」的划分策略可直接用于 TF–DNA 结合预测的评估设计。

---

## 02 一句话总结

本文通过在 Geneformer V2-316M 和 scGPT 两个单细胞基础模型上对 120 个 SAE 特征执行逐特征消融（ablation）并测量下游所有 SAE 特征的变化（共 96,892 条边、80,191 次前向传播），构建了模型内部的因果特征图，发现其以抑制性边为主（65.5%–89.4%）、与 GO/KEGG 等本体论注释显著共现（50.9%–68.5%，随机特征降至 21.5%–26.3%），且跨模型存在 1,142 个架构不变的结构域对；但经 sign-bias 校正后，模型对 CRISPRi 扰动方向的预测能力仅略高于零（K562 超额 +0.03 个百分点，RPE1 +0.35 个百分点），表明模型主要编码了调控的描述性结构而非干预性因果。

---

## 03 研究问题

**具体问题**: 单细胞基础模型（scFMs）内部的 SAE 特征之间是否存在可识别的因果计算结构？这些结构是否具有生物学一致性（即是否对应真实的调控关系）？不同架构的模型（Geneformer vs. scGPT）是否收敛到相似的计算架构？

**为什么重要**: 
- 单细胞基础模型（如 Geneformer、scGPT）被广泛用于基因调控预测，但其内部计算机制完全不透明
- 已有的 SAE 分析只揭示了「存在哪些特征」，未揭示「特征之间如何因果互动」
- 如果模型内部确实编码了真实的调控结构（如 TF→靶基因），则可作为调控网络推断的新工具；如果只是统计共现，则需重新审视其生物学解释

**现有方法为何不足**:
- 相关分析（co-activation, PMI）只能给出无向、无符号的共现关系，无法区分因果方向
- 激活 patching 等方法在语言模型中已有应用，但未在生物基础模型的 SAE 特征层面系统实施
- 已有验证多使用单一生物学先验（如仅 GO 或仅 ChIP-seq），缺乏多层次、可 falsifiable 的验证栈

**精确研究问题 (Can...?)**: 
Can model-internal causal circuit tracing on SAE features of single-cell foundation models reveal computationally distinct architectures that are (a) predominantly inhibitory, (b) biologically coherent beyond chance, and (c) convergent across architecturally different models—while remaining distinguishable from marginal coexpression and showing only weak, sign-bias-corrected predictive power for CRISPRi perturbation outcomes?

---

## 04 背景与发展脉络

*注：以下脉络基于本文框架及其引用，标记为「仅本文框架」；未逐一核验外部文献。*

**阶段一：单细胞基础模型的兴起（2022–2024）**
- 代表方法：scBERT (Yang et al. 2022)、Geneformer (Theodoris et al. 2023)、scGPT (Cui et al. 2024)、scFoundation (Hao et al. 2024)、UCE (Rosen et al. 2023)
- 优点：在大规模单细胞转录组上预训练，可迁移到细胞类型注释、扰动预测等下游任务
- 局限：内部表征不可解释，预测机制未知

**阶段二：SAE 特征分解（2022–2025）**
- 代表方法：稀疏自编码器（SAE）应用于 Transformer 激活（Sharkey et al. 2022; Bricken et al. 2023; Huben et al. 2024; Templeton et al. 2024; Gao et al. 2025）
- 优点：将稠密激活分解为稀疏、可解释的特征
- 局限：只揭示「特征存在」，不揭示「特征间因果互动」；特征-生物学映射多为相关性而非因果性

**阶段三：因果干预与电路发现（2021–2025，语言模型领域）**
- 代表方法：激活 patching (Vig et al. 2020; Meng et al. 2022)、因果抽象 (Geiger et al. 2021)、稀疏特征电路发现 (Marks et al. 2025)
- 优点：能识别模型内部真正的因果通路
- 局限：主要应用于语言模型，未迁移到生物基础模型

**阶段四（本文位置）：生物基础模型的因果电路追踪（2026）**
- 本文首次将 SAE 特征级别的因果电路追踪系统应用于单细胞基础模型
- 贡献：(i) 规模化（96,892 条边）；(ii) 跨模型比较；(iii) 输入条件分解（细胞类型 × SAE 训练数据）；(iv) 可组合的 falsifiable 验证栈；(v) 诚实的偏差量化（sign-bias correction、随机特征基线）

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| SAE 特征分析停留在「存在性」层面 | 已有 SAE atlases 只描述特征及其激活位置，未揭示特征间因果互动 | 缺乏系统性的特征间干预方法；计算成本高 | Introduction: "Those atlases... did not reveal how features causally interact across network depth" |
| 相关 ≠ 因果 | Co-activation (PMI) 只能给出无向、无符号的共现关系 | PMI 无法区分方向、符号和因果强度 | Section 4.7: "PMI yields undirected, unsigned edges... while ablation assigns direction, sign, and magnitude" |
| 注释选择偏差（annotation selection bias） | 用注释质量筛选特征会系统性高估生物学一致性 | 注释质量评分本身与本体论注释重叠 | Results 3.2: 注释选择特征共享本体论 50.9%–68.5%，随机特征降至 21.5%–26.3% |
| 方向性预测的 sign bias | 原始方向准确率看似可观，但扣除边际分布后几乎无信号 | 预测和观测的符号边际分布都高度偏斜（~85% vs 53–59% 负向） | Section 2.9, 3.11: 校正后 K562 超额仅 +0.03 pp，RPE1 +0.35 pp |
| 跨模型泛化未知 | 单模型分析无法区分「模型特有的伪影」与「普遍的计算架构」 | 缺乏跨架构比较的通用协议 | Results 3.7: 1,142 个跨模型共识结构域对，10.6× 富集 |
| 验证先验不匹配 | 使用泛组织调控数据库（如 TRRUST）验证特定细胞类型的预测 | 调控关系具有细胞类型特异性 | Section 3.8: 匹配细胞类型的 ChIP-seq 先验（2.06×）远优于泛 TRRUST（1.12×） |

---

## 06 核心思想

**1) 表面方法**：
对 SAE 分解后的特征执行逐特征消融（将目标特征的稀疏系数置零，经解码器重构后替换原隐藏状态），测量所有下游层 SAE 特征的变化（Cohen's d），构建有向、有符号、有量级的特征间因果图。在 4 种条件下（Geneformer K562/K562、Geneformer 多组织、scGPT K562/K562、scGPT 多组织）重复，并用多种生物学先验（GO/KEGG/Reactome/STRING/TRRUST、ChIP-seq、CRISPRi）验证。

**2) 核心洞察**：
- **抑制性主导**：模型内部特征间以「必要性」编码为主（消融一个特征导致下游特征激活下降），而非「冗余性」编码（消融后下游特征激活上升）。这意味着模型用「特征 A 是特征 B 的前提」的方式组织知识，而非「A 和 B 可互相替代」。
- **注释选择偏差可量化**：用注释质量筛选特征会将共享本体论率从 21.5%–26.3%（随机基线）推高到 50.9%–68.5%（注释选择），即约 2.5 倍的膨胀。任何使用注释选择特征的解释研究都必须报告随机基线。
- **跨模型收敛**：尽管架构、训练数据、分词方案不同，两个模型在结构域对层面共享 1,142 个一致的「A→B」调控关系，且富集 10.6 倍——提示存在模型共同学习的真实调控结构。
- **描述性 vs 干预性编码的分离**：模型内部因果图与 ChIP-seq 直接靶标有弱但显著的富集（2.06×），但对 CRISPRi 扰动方向的预测经 sign-bias 校正后几乎为零。模型编码了「什么和什么相关」的描述性结构，但未编码「扰动 A 会改变 B」的干预性因果。

**3) 可能的普适教训 [Analysis]**：
- 任何「模型内部表征 vs 生物学真实」的验证都必须区分**选择偏差**和**真实信号**：用注释质量筛选特征会系统性高估一致性，随机基线是必须的对照。
- 方向性预测的评估必须做 sign-bias correction：当预测和观测的符号边际都偏斜时，原始准确率可能完全由边际分布驱动。
- 「模型内部因果图」与「实验扰动响应」的弱对应可能不是模型的失败，而是训练目标（masked language modeling）本身只要求描述性结构——如果要让模型编码干预性因果，需要改变训练目标（如加入扰动监督）。

---

## 07 方法总览

**输入**：
- 单细胞转录组数据（K562 细胞系、Tabula Sapiens 多组织）
- 预训练模型：Geneformer V2-316M（18 层 transformer, d_model=1152, 18 头, 上下文 4096 tokens）和 scGPT whole-human（12 层, d=512, 8 头, 1200 padded positions）
- 预训练 SAE：TopK (k=32) 架构，4× 过完备字典（Geneformer 4608 特征，scGPT 2048 特征），在 K562-only 或多组织数据上训练

**输出**：
- 有向特征级因果图（96,892 条边，4 种条件）
- 每条边带 Cohen's d（效应量）、方向（源→目标）、符号（正/负）
- 结构域对（GO BP 类别 A→B）级别的跨模型共识图（1,142 对）

**模块**：
1. **SAE 特征分解**：对每层残差流进行 SAE 编码，得到稀疏特征激活
2. **因果消融**：对源特征执行零消融（zero-ablation），通过 SAE 解码器重构修改后的隐藏状态，用 forward hook 替换原状态
3. **下游测量**：对所有下游层的 SAE 特征计算消融前后激活变化的 Cohen's d
4. **边筛选**：|d| > 0.5 且一致性 > 0.7（即超过 70% 的细胞中 d 的符号一致）
5. **注释映射**：将特征映射到 GO BP/KEGG/Reactome/STRING/TRRUST 注释，计算共享本体论率
6. **验证栈**：与 ENCODE ChIP-seq（匹配细胞类型）、CRISPRi 扰动数据（Replogle K562/RPE1, Shifrut 原代 T 细胞）比较

**训练/计算细节**：
- 200 个 K562 非靶向对照细胞（K562 条件）或 200 个分层抽样细胞（Tabula Sapiens 条件，88 种细胞类型）
- 80,191 次前向传播（含消融和干净 pass）
- 所有实验在单台 Apple Silicon 笔记本（MPS 后端）上完成；K562/K562 全流程 7.5 小时

**反馈回路**：
- 无显式训练反馈回路；验证结果用于修正解释（如 sign-bias correction 后重新解读方向准确率）

**文字流程**：
输入细胞 → tokenize（Geneformer rank-value encoding 或 scGPT 连续值）→ 模型前向传播 → 在目标层 SAE 编码残差流 → 选择源特征 → 零消融该特征 → 解码重构修改后隐藏状态 → forward hook 替换 → 继续前向传播至所有下游层 → 每层 SAE 编码 → 计算所有下游特征激活的 Δ → 累积 200 细胞的 Cohen's d 和一致性 → 筛选边 → 注释映射 → 与生物学先验比较。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| SAE 特征分解 | 将稠密残差流激活分解为稀疏、可解释的特征 | 直接对残差流做消融不可行（维度高、不可解释）；SAE 提供语义上有意义的干预单元 | 输入：层残差流 h_l ∈ R^d；输出：稀疏特征激活 z ∈ R^m (m=4d, TopK k=32) | Section 2.1; 引用 SAE atlases (Kendiukhov 2026) 中每特征重建 R²>0.95 | 无 SAE 则无法定义「特征」级别的干预单元；消融将退化为对单个神经元或随机方向的干预，不可解释 |
| 零消融 + 解码重构 | 将目标特征从表示中移除，重构修改后的残差流 | 实现「如果该特征不存在，下游会怎样」的反事实干预 | 输入：稀疏码 z，目标特征索引 i；输出：修改后残差流 h'_l = dec(z with z_i=0) | Section 2.3: "zero the source feature in the sparse code and decode to obtain a modified residual stream" | 移除后无法进行因果干预；只能做相关性分析 |
| Forward hook 状态替换 | 在模型前向传播中替换指定层的隐藏状态 | 实现真正的因果干预（而非仅分析激活模式） | 输入：原始前向 pass 的中间状态；输出：替换后的前向 pass | Section 2.3: "hidden-state replacement via torch.nn.Module forward hooks" | 移除后只能做「观察性」分析，无法建立因果方向 |
| Cohen's d 效应量计算 | 量化消融对下游特征的影响大小和方向 | 需要标准化、可跨特征比较的效应量 | 输入：200 细胞的 Δ 分布；输出：d = Δ̄/σ_Δ | Section 2.3; Results 3.1: mean |d|=1.05 (Geneformer), 1.40 (scGPT) | 移除后无法设定统一的边筛选阈值（|d|>0.5） |
| 一致性阈值 | 确保边的方向在大多数细胞中一致 | 单个细胞的噪声可能产生虚假的边 | 输入：每细胞的 Δ 符号；输出：一致性分数（>0.7 才保留边） | Section 2.3: "consistency (fraction of cells whose delta sign matches the mean-delta sign)" | 移除后边集合将包含大量噪声驱动的虚假连接 |
| 配置保持置换零（permutation null） | 生成随机基线以量化注释选择偏差 | 注释选择特征会系统性高估生物学一致性 | 输入：特征-注释映射；输出：500 次置换的期望共享本体论率 | Results 3.2: 随机特征共享率 8.5%–23.4%，注释选择 50.9%–68.5% | 移除后无法区分「真实生物学编码」与「选择偏差」 |
| Sign-bias correction | 扣除预测和观测符号边际分布带来的虚假准确率 | 方向性预测的原始准确率可能完全由边际分布驱动 | 输入：预测符号、观测符号；输出：超额准确率 = 原始 − 边际零 | Section 2.9, 3.11: K562 超额 +0.03 pp，RPE1 +0.35 pp | 移除后可能得出「模型能预测扰动方向」的错误结论 |
| 特征份额归一化（feature-share normalization） | 消除 SAE 字典大小差异对效应量的影响 | scGPT 字典更小（2048 vs 4608），每个特征承载更大表示份额 | 输入：原始 d，特征数；输出：d_norm = d × n_features/4608 | Results 3.6: 归一化后 Geneformer/scGPT 比值从 1.43 反转为 0.64 | 移除后可能得出「scGPT 效应更强」的错误结论 |

---

## 09 关键公式符号

**1. Cohen's d（消融效应量）**

$$d = \frac{\bar{\Delta}}{\sigma_{\Delta}}$$

- $\Delta$ = 消融前后下游特征激活的变化（per-cell）
- $\bar{\Delta}$ = 200 个细胞的平均变化
- $\sigma_{\Delta}$ = 变化的标准差
- 用途：标准化、可跨特征比较的效应量；|d| > 0.5 为显著边
- 来源：Section 2.3

**2. 特征份额归一化**

$$d_{\text{norm}} = d \times \frac{n_{\text{features}}}{4608}$$

- $n_{\text{features}}$ = 该模型的 SAE 特征数（Geneformer: 4608, scGPT: 2048）
- 用途：消除字典大小差异对效应量的影响
- 来源：Section 3.6

**3. Sign-bias 零模型**

$$\text{Null} = P(\text{pred} < 0) \cdot P(\text{obs} < 0) + P(\text{pred} > 0) \cdot P(\text{obs} > 0)$$

- $P(\text{pred} < 0)$ = 预测（模型 d）为负的比例（~85%）
- $P(\text{obs} < 0)$ = 观测（CRISPRi log2FC）为负的比例（53–59%）
- 用途：计算方向准确率的期望基线；超额 = 原始准确率 − Null
- 来源：Section 2.9, 3.11

**4. 共享本体论率（Shared ontology rate）**

$$\text{SharedOntology} = \frac{|\{(s,t) \in E : \text{Ann}(s) \cap \text{Ann}(t) \neq \emptyset\}|}{|E|}$$

- $E$ = 消融边集合
- $\text{Ann}(f)$ = 特征 f 的注释集合（GO/KEGG/Reactome/STRING/TRRUST）
- 用途：衡量边的生物学一致性
- 来源：Section 2.8, Results 3.2

**5. 富集倍数（Fold enrichment）**

$$\text{FE} = \frac{\text{Observed rate}}{\text{Permutation null rate}}$$

- 用途：量化注释选择特征 vs 随机特征的共享本体论率差异（2.9–6.2×）
- 来源：Results 3.2

**6. 跨模型共识富集**

$$\text{Consensus FE} = \frac{\text{Observed consensus pairs}}{E[\text{consensus pairs under null}]} = 10.6\times$$

- 用途：衡量两个模型独立恢复相同结构域对的显著性
- 来源：Section 3.7

---

## 10 实验设计与证据链

**数据集/群体**：
- K562 条件：200 个 Replogle et al. (2022) CRISPRi 数据集的非靶向对照细胞
- Tabula Sapiens 条件：200 个细胞，分层抽样覆盖 88 种细胞类型（免疫 67 细胞/41 型、肾 67 细胞/13 型、肺 66 细胞/34 型）
- 验证数据：Replogle K562（10,691 非靶向对照）、Replogle RPE1 非癌臂（11,485 非靶向对照；1,446 靶基因通过池级过滤）、Shifrut et al. (2018) 原代 CD8+ T 细胞 CRISPR-KO（52,236 细胞，20 免疫检查点靶基因，30,683 非靶向对照）

**指标**：
- 边数、平均出度、抑制性边比例（65.5%–89.4%）
- 共享本体论率（50.9%–68.5% 注释选择；21.5%–26.3% 随机）
- 富集倍数（2.9–6.2×）
- 跨模型共识富集（10.6×）
- 方向准确率及 sign-bias 校正后超额（K562 +0.03 pp，RPE1 +0.35 pp）
- 直接 vs 间接靶标超额比（K562 30×，RPE1 3×）
- 稳定性：Pearson r(d)（0.973–0.989）、符号一致性（100%）、边 Jaccard（0.44–0.64）

**基线/对照**：
- 配置保持置换零（500 次置换，同层内打乱特征-注释映射）
- 随机特征源（20 个随机采样特征，两个种子）
- 符号边际零模型（sign-bias null）
- PMI 共现基线（与消融边集合对比）

**消融/敏感性分析**：
- 阈值扫描：|d| ∈ {0.1, 0.2, 0.3, 0.5, 0.7, 1.0}，抑制性比例和共享本体论率变化 ≤6 pp
- 一致性阈值扫描：{0.6, 0.7, 0.8}，头条数变化 ≤8%
- 样本量：N ∈ {50, 100, 200}，边 Jaccard 单调增长

**主要实验表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|-----------------|------|
| E1: 全图消融追踪 | 模型内部存在密集的因果特征图 | 4 种条件 × 120 源特征 | 96,892 条边，80,191 次前向 | 因果图可规模化构建 | 图的具体生物学意义需进一步验证 | Results 3.1, Table 1 |
| E2: 抑制性主导 | 特征间以必要性编码为主 | 各条件下抑制性边比例 | 65.5%–89.4% 边为 d<0 | 模型偏好「必要性」编码 | 不排除部分抑制是消融伪影 | Results 3.1, Fig 2C |
| E3: 注释选择偏差量化 | 注释选择特征高估生物学一致性 | 注释选择 vs 随机特征 | 50.9%–68.5% vs 21.5%–26.3% | 选择偏差约 2.5 倍 | 随机特征仍有 2.5–3.1× 富集，存在真实信号 | Results 3.2, Table 2 |
| E4: 跨模型共识 | 不同架构收敛到相似结构 | Geneformer vs scGPT 结构域对 | 1,142 对共识，10.6× 富集 | 存在架构不变的计算结构 | 共识对的功能意义需实验验证 | Results 3.7 |
| E5: 与共表达对比 | 消融图 ≠ 共表达图 | 消融 d vs 边际 Pearson r | R²=0.010 (n=31,176) | 消融图编码共表达之外的结构 | 不能排除非线性共表达 | Results 3.3 |
| E6: ChIP-seq 富集 | 消融边对应真实 TF→靶标 | 匹配细胞类型 ENCODE | 2.06× 富集（K562） | 弱但可检测的调控信号 | 富集远低于 ChIP-seq 内部一致性 | Results 3.8 |
| E7: CRISPRi 方向预测 | 模型能预测扰动方向 | sign-bias 校正后 | K562 +0.03 pp，RPE1 +0.35 pp | 几乎无干预性预测能力 | 直接靶标子集有 10–30× 相对富集 | Results 3.11, Table 3 |
| E8: 原代 T 细胞对照 | 跨细胞类型泛化 | Shifrut 原代 CD8+ T | 超额 −0.03 pp（零结果） | K562 训练特征不迁移到 T 细胞 | 需 T 细胞定向特征选择 | Results 3.11.1 |
| E9: 稳定性分析 | 结果对样本量稳健 | N ∈ {50,100,200} | r≥0.97，100% 符号一致 | 效应量高度可重复 | 边身份在低 N 下不稳定 | Results 3.12, Table 4 |

---

## 11 结论正确解读

**任务范围**: 本文的因果追踪限于 SAE 特征层面，而非单个基因或神经元层面；验证限于 K562 细胞系和 Tabula Sapiens 多组织数据；生物学验证限于 ChIP-seq（TF 结合）和 CRISPRi（扰动表达）两类先验。

**oracle/真值输入**: 本文没有使用 oracle 或人工标注的真值图；生物学先验（GO/KEGG/Reactome/STRING/TRRUST、ENCODE ChIP-seq、Replogle/Shifrut CRISPRi）作为独立验证集，而非训练输入。

**端到端状态**: 本文**不是**端到端的「序列→调控预测」系统；它是对已训练模型（Geneformer, scGPT）的**事后分析**（post-hoc analysis）。模型本身是冻结的，因果追踪是分析工具。

**算力成本**: 所有实验在单台 Apple Silicon 笔记本上完成（MPS 后端），K562/K562 全流程 7.5 小时——这是一个极低的算力门槛，意味着该方法对大多数实验室可复现。

**历史数据依赖**: 模型权重来自预训练 checkpoint（Geneformer V2-316M, scGPT whole-human），SAE 在特定数据上训练（K562-only 或多组织）。因果追踪结果依赖这些预训练权重的数据分布。

**模型依赖**: 结论仅对这两个模型成立；不能推广到所有单细胞基础模型。作者明确报告了跨模型差异（如 scGPT 的 L4 特征最广泛连接 vs Geneformer 的 L0 主导）。

**最难情形**: 原代 T 细胞（Shifrut）验证失败——K562 训练的注释选择特征不迁移到免疫检查点生物学。这界定了方法的适用边界：特征选择偏差会限制跨领域迁移。

**有边界的复述**: 在 Geneformer V2-316M 和 scGPT whole-human 这两个模型上，SAE 特征间的因果图以抑制性边为主（65.5%–89.4%），注释选择特征的共享本体论率（50.9%–68.5%）显著高于随机特征（21.5%–26.3%），跨模型存在 1,142 个共识结构域对（10.6× 富集）；但经 sign-bias 校正后，模型对 CRISPRi 扰动方向的预测超额仅为 +0.03（K562）和 +0.35（RPE1）个百分点，且对原代 T 细胞免疫检查点靶标无预测能力。模型主要编码了调控的描述性结构，而非干预性因果。

---

## 12 局限与未解问题

**作者明确承认的局限**（见 Section 4.4）：
1. 注释选择特征将共享本体论率从 21.5%–26.3% 膨胀至 50.9%–68.5%（约 2.5 倍），所有头条数字应同时阅读随机基线
2. CRISPRi 验证仍以 K562 为中心；RPE1 是 hTERT 永生化细胞系，非原代
3. 严格前向消融设计（源层早于目标层）无法测试同层内的方向不对称性
4. 动态过程（如分化轨迹）仅以静态方式捕获

**作者未明确提及但可推断的局限 [Analysis]**：
1. 零消融（zero-ablation）是一种强干预，可能产生非物理的激活模式（模型从未在训练中见过特征被完全置零的输入）；替代方案如「均值消融」或「方向扰动」可能更温和
2. 120 个源特征仅覆盖每层 30 个（Geneformer）或 90 个（scGPT），远非全特征覆盖；饱和追踪（所有特征作为源）被明确标记为计算上不可行
3. 特征-基因映射依赖 top-15 driver genes，可能遗漏弱但真实的调控信号
4. 跨模型共识分析仅在结构域对层面（GO BP 类别），未在特征层面直接比较——两个模型的特征空间不可直接对齐
5. 未报告不同细胞类型输入下特征激活的方差，可能掩盖细胞类型特异性的动态范围

**未解问题**：
1. 抑制性主导是否源于训练目标（masked language modeling）的固有属性，还是模型架构的普遍特征？
2. 如果改变训练目标（如加入扰动监督），模型内部因果图是否会向干预性因果偏移？
3. 跨模型共识的 1,142 个结构域对中，有多少对应已知的调控机制，有多少是模型特有的伪影？
4. 特征层面的因果图能否「提升」到基因调控网络层面，用于预测未知的 TF→靶基因关系？

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 零消融可能产生非物理激活模式 | 模型从未见过特征被完全置零的输入；观察到的「抑制性主导」可能部分源于消融方式而非模型真实计算结构 | 如果抑制性主导是消融伪影，则核心结论「必要性编码」不成立 | 比较零消融 vs 均值消融 vs 方向扰动（沿特征方向的梯度步长）的结果 | Section 2.3: "zero the source feature" |
| 注释选择偏差的「校正」可能过度 | 随机特征基线（21.5%–26.3%）仍显著高于纯随机（8.5%–23.4%），说明即使随机特征也有生物学一致性——这可能是因为 SAE 特征本身倾向于编码常见生物学过程，而非模型学到了调控结构 | 如果随机特征也有高共享率，则注释选择 vs 随机的差异可能反映的是特征「可注释性」而非「调控真实性」 | 使用与注释质量无关的特征选择标准（如激活频率、稀疏性）重复 E3 | Results 3.2: 随机特征 2.5–3.1× 富集 |
| 跨模型共识的 10.6× 富集可能被结构域对的数量膨胀 | GO BP 类别约 30,000 个，结构域对空间约 9×10⁸；1,142 个共识对在如此大的空间中即使随机也可能出现少量富集 | 如果富集是空间搜索的假阳性，则「架构不变的计算结构」结论被削弱 | 使用更严格的多重检验校正（如 FDR），或限制在已知调控通路内的结构域对 | Section 3.7: "10.6× enrichment over permutation null" |
| CRISPRi 验证的 sign-bias 校正可能过于保守 | 校正后超额接近零，但直接靶标子集有 10–30× 相对富集——这可能说明模型确实编码了直接调控信号，只是被大量间接靶标的噪声淹没 | 如果直接靶标信号真实存在，则「模型不编码干预性因果」的结论需要弱化为「模型编码的干预性因果很弱且集中在直接靶标」 | 在直接靶标子集上做更细致的功率分析，或使用更严格的直接靶标定义 | Results 3.11: "direct ChIP-seq-supported target pairs show 10–30× larger excess" |
| 120 个源特征的选择标准未充分报告 | 注释质量评分可能偏向「容易注释」的特征（如已知通路基因），导致 hub 分析偏向特定生物学功能 | 如果源特征选择有偏，则 hub 特征（如神经发育、DNA 损伤）的突出地位可能是选择伪影 | 报告注释质量评分的分布，使用不同评分阈值重复 hub 分析 | Section 2.4: "score = 10·n_ontologies + n_annotations − log10 p_min" |
| 未报告特征激活的细胞间方差 | 200 个细胞的 Cohen's d 可能掩盖了细胞亚群间的异质性；某些「稳定」的边可能只在少数细胞中驱动 | 如果边在不同细胞类型间不稳定，则「细胞类型特异性」的结论需要更细致的分析 | 按细胞类型分层计算 Cohen's d 和一致性 | Section 2.3: "accumulate per-cell deltas" |

---

## 14 术语解释

- **Sparse Autoencoder (SAE)**：稀疏自编码器。一种无监督学习模型，将高维输入（如 transformer 的残差流激活）压缩为稀疏的、可解释的特征表示。本文中 SAE 将每层激活分解为 4× 过完备字典中的稀疏组合（TopK k=32）。
- **Causal circuit tracing**：因果电路追踪。通过干预（本文为零消融）模型内部的一个组件，测量其对下游组件的影响，从而构建有向因果图的方法。
- **Cohen's d**：效应量指标，表示两组均值差异除以合并标准差。本文中 d = Δ̄/σ_Δ，即消融前后激活变化的均值除以标准差。
- **Zero-ablation**：零消融。将目标特征的激活值设为 0，通过解码器重构修改后的隐藏状态，替换原状态后继续前向传播。
- **Feature**：特征。SAE 分解后的一个稀疏单元，对应某种可解释的生物学模式（如「DNA 损伤响应」）。
- **Driver genes**：驱动基因。对某个 SAE 特征激活贡献最大的 top-k 基因（本文 k=15），用于将特征映射到基因层面。
- **Ontology coherence / shared ontology**：本体论一致性。一条边的源特征和目标特征是否共享至少一个 GO/KEGG/Reactome/STRING/TRRUST 注释项。
- **Configuration-preserving permutation null**：配置保持置换零。一种零模型，在保持每层特征-注释映射的总体分布不变的前提下，随机打乱特征-注释配对，用于估计随机期望的共享本体论率。
- **Sign-bias correction**：符号偏差校正。当预测和观测的符号边际分布都偏斜时，计算方向准确率相对于「仅靠边际分布」的期望准确率的超额。
- **Feature-share normalization**：特征份额归一化。将效应量乘以特征数的比例因子（d_norm = d × n_features/4608），以消除不同模型字典大小差异的影响。
- **Direct vs indirect targets**：直接 vs 间接靶标。直接靶标指 ChIP-seq 支持的 TF 结合靶基因；间接靶标指仅通过 CRISPRi 扰动观察到表达变化但无 ChIP-seq 结合证据的基因。
- **Masked language modeling (MLM)**：掩码语言建模。预训练任务，模型需根据上下文预测被掩码的 token。Geneformer 和 scGPT 均使用类似 MLM 的目标。
- **Residual stream**：残差流。transformer 中每层输出的隐藏状态，是后续层输入的基础。
- **Forward hook**：前向钩子。PyTorch 中在模块前向传播时插入自定义操作的机制，本文用于在指定层替换隐藏状态。
- **Hub features**：枢纽特征。在图论中，出度或入度显著高于平均的特征节点，代表对大量下游特征有广泛影响的「中心」特征。
- **CRISPRi**：CRISPR 干扰。利用失活 Cas9（dCas9）融合转录抑制域，在 DNA 水平抑制目标基因转录的技术。
- **ChIP-seq**：染色质免疫沉淀测序。用于鉴定蛋白质（如转录因子）在基因组上的结合位点。
- **TRRUST**：转录调控关系数据库，包含人类和小鼠的 TF-靶基因调控关系。
- **Tabula Sapiens**：人类多组织单细胞转录组图谱数据集。
- **Pseudo-bulk**：伪批量。将单细胞数据按细胞类型或条件聚合为「伪样本」，用于差异表达分析。

---

## 15 与已有知识连接

**相似方法（可核验）**：
- **激活 patching / 因果干预**：Vig et al. (2020) "Causal mediation analysis for interpreting neural networks"；Meng et al. (2022) "Locating and editing factual associations in GPT"；Geiger et al. (2021) "Causal abstraction"——本文将这些方法从语言模型迁移到生物基础模型。
- **SAE 可解释性**：Bricken et al. (2023) "Monosemantic features"；Templeton et al. (2024) "Scaling monosemanticity"；Gao et al. (2025)——本文建立在 SAE 特征分解的基础上。
- **电路发现**：Wang et al. (2023) "Interpretability in the wild"；Marks et al. (2025) "Sparse feature circuits"——本文的「特征间因果图」与语言模型中的「电路发现」直接对应。

**与 TF–DNA 结合课题的连接**：
- **ChIP-seq 作为验证先验**：本文使用 ENCODE ChIP-seq 验证模型内部特征图的调控真实性。TF–DNA 结合预测课题可直接借鉴此策略：用 ChIP-seq 作为「直接结合」的金标准，区分模型预测中的直接 vs 间接效应。
- **CRISPRi 作为因果验证**：本文使用 CRISPRi 扰动数据验证模型的方向性预测。TF–DNA 结合预测课题中，若预测某个 TF 调控某个靶基因，可用 CRISPRi 敲低 TF 后检测靶基因表达变化作为因果验证。
- **Sign-bias correction 的普适性**：任何使用方向性预测（TF 激活/抑制靶基因）的评估都可能面临符号边际分布偏斜的问题。本文的校正方法可直接迁移到 TF–DNA 结合预测的评估流程中。
- **特征选择偏差的警示**：本文发现注释选择特征会系统性高估生物学一致性（约 2.5 倍）。TF–DNA 结合预测中，如果训练数据偏向已知调控关系（如 TRRUST），评估时也会高估模型性能——需要随机基线对照。
- **跨模型共识作为稳健性指标**：本文用跨模型共识（1,142 个结构域对）识别「架构不变」的调控结构。TF–DNA 结合预测中，可比较不同模型（如 AlphaFold 3、RoseTTAFold 等）对同一 TF–DNA 复合物的预测是否收敛，作为预测可信度的指标。

**可迁移的方法论**：
1. **配置保持置换零**：在评估任何「特征-注释」或「预测-先验」重叠时，应使用保持配置的置换零而非简单随机置换。
2. **直接 vs 间接靶标划分**：在验证调控预测时，应区分 ChIP-seq 支持的直接靶标和仅表达相关的间接靶标。
3. **效应量 + 一致性双阈值**：边筛选同时使用效应量（|d|>0.5）和一致性（>0.7），比单一阈值更稳健。

---

## 16 研究想法

### 候选 1：TF–DNA 结合预测的「模型内部因果图 vs. ChIP-seq」验证框架
- **名称**: Causal Circuit-TF Binding Validation (CCTF-Bind)
- **来源局限/观察**: 本文证明单细胞基础模型内部存在与 ChIP-seq 弱但显著富集的调控结构，但未直接用于 TF–DNA 结合预测。现有 TF–DNA 结合预测（如 DeepBind、DeepSEA）多为黑箱，缺乏模型内部机制验证。
- **核心假设**: 在 TF–DNA 结合预测模型中，SAE 特征间的因果图应富集于 ChIP-seq 支持的 TF–靶标对，且该富集可作为模型「是否真正学习到调控机制」的指标。
- **增量**: 将本文的因果电路追踪 + 匹配细胞类型 ChIP-seq 验证框架迁移到 TF–DNA 结合预测模型（如 Enformer、Basenji），提供模型内部机制层面的验证。
- **初步方法**: (1) 对 TF–DNA 结合模型训练 SAE；(2) 对 TF 相关特征执行零消融；(3) 测量下游靶基因特征的变化；(4) 与 ENCODE ChIP-seq 比较富集；(5) 报告注释选择 vs 随机特征基线。
- **验证方式**: 在 ENCODE 多细胞系 ChIP-seq 数据上评估富集；与现有模型解释方法（如 saliency map、DeepLIFT）对比。
- **创新状态**: unverified

### 候选 2：TF 结合位点预测的「直接 vs 间接靶标」评估协议
- **名称**: Direct-Target-Aware Evaluation (DTAE) Protocol
- **来源局限/观察**: 本文发现直接 ChIP-seq 支持的靶标对超额远高于间接靶标（10–30×），但现有 TF–DNA 结合预测评估多使用全基因表达变化作为金标准，混淆了直接和间接效应。
- **核心假设**: 在 TF–DNA 结合预测评估中，区分直接（ChIP-seq 支持）和间接靶标可以更准确地衡量模型性能，避免间接效应带来的虚假高估。
- **增量**: 提出一个标准化的评估协议，要求所有 TF–DNA 结合预测模型在直接和间接靶标子集上分别报告性能。
- **初步方法**: (1) 从 ENCODE 获取匹配细胞类型的 ChIP-seq 直接靶标；(2) 从 CRISPRi 筛选获取表达变化基因；(3) 将评估集划分为直接/间接/非靶标三组；(4) 分别计算 AUROC、AUPRC；(5) 报告 sign-bias 校正后的超额。
- **验证方式**: 在多个 TF（如 MYC、TP53、CTCF）和多个模型（DeepBind、Enformer、AlphaFold 3）上验证协议的可区分性。
- **创新状态**: unverified

### 候选 3：跨模型共识的 TF–DNA 结合结构域预测
- **名称**: Cross-Model Consensus TF-DNA Domain Prediction (CMCDP)
- **来源局限/观察**: 本文发现两个架构不同的模型（Geneformer, scGPT）在 1,142 个结构域对上收敛，且富集 10.6 倍。这种「跨模型共识」策略可用于 TF–DNA 结合预测：不同模型（如 AlphaFold 3、RoseTTAFold、MD 模拟）对同一 TF–DNA 复合物的预测共识可能比单一模型更可靠。
- **核心假设**: 多个架构不同的 TF–DNA 结合预测模型对同一复合物的预测共识（结构域对级别）富集于实验验证的结合位点，且共识度可作为预测置信度。
- **增量**: 提出一个「跨模型共识」框架，将 AlphaFold 3、RoseTTAFold、MD 模拟的预测结果在结构域对级别整合，输出共识结合位点。
- **初步方法**: (1) 对同一 TF–DNA 复合物运行多个预测模型；(2) 将预测的接触残基映射到结构域对；(3) 计算跨模型共识分数；(4) 与实验结构（PDB）和 ChIP-seq 比较富集。
- **验证方式**: 在已知 TF–DNA 复合物（如 p53-DNA、CTCF-DNA）上评估共识预测的精度；与单一模型预测对比。
- **创新状态**: unverified

### 候选 4：TF–DNA 结合模型的 sign-bias 校正评估
- **名称**: Sign-Bias-Corrected TF Binding Evaluation (SBC-TF)
- **来源局限/观察**: 本文指出方向性预测的准确率可能完全由符号边际分布驱动（~85% 负向预测 vs 53–59% 负向观测）。TF–DNA 结合预测中，如果预测的激活/抑制比例与实验观测的边际分布不匹配，准确率评估会产生误导。
- **核心假设**: TF–DNA 结合预测模型的方向性准确率在 sign-bias 校正后显著下降，校正后的超额是模型真实调控预测能力的更准确度量。
- **增量**: 将 sign-bias 校正方法引入 TF–DNA 结合预测评估，作为标准报告指标。
- **初步方法**: (1) 对 TF 敲低/过表达预测的基因表达变化方向进行分类；(2) 计算预测和观测的符号边际分布；(3) 计算 sign-bias 零模型期望准确率；(4) 报告超额准确率。
- **验证方式**: 在 Replogle CRISPRi 和 Perturb-seq 数据上评估多个 TF 结合预测模型的校正后性能。
- **创新状态**: unverified

### 候选 5：TF–DNA 结合预测的「必要性编码」分析
- **名称**: Necessity-Encoding Analysis for TF-DNA Binding (NEAT-Bind)
- **来源局限/观察**: 本文发现模型内部以「必要性」编码为主（消融特征导致下游激活下降），而非「冗余性」编码。这一发现可迁移到 TF–DNA 结合预测：如果模型以「TF 特征是靶基因表达的必要条件」的方式编码调控关系，则消融 TF 特征应导致靶基因特征激活下降。
- **核心假设**: TF–DNA 结合预测模型中，TF 相关特征对靶基因特征呈必要性编码（消融 TF 特征降低靶基因激活），且该必要性编码强度与 ChIP-seq 支持的直接结合强度正相关。
- **增量**: 提出「必要性编码强度」作为 TF–DNA 结合预测模型的新解释指标，补充现有的相关性分析。
- **初步方法**: (1) 对 TF 相关 SAE 特征执行零消融；(2) 测量靶基因特征的激活变化；(3) 计算必要性编码强度（d 值）；(4) 与 ChIP-seq 结合强度、CRISPRi 效应量比较。
- **验证方式**: 在 Geneformer 和 scGPT 上对多个 TF 进行必要性编码分析，与 ENCODE ChIP-seq 和 Replogle CRISPRi 数据验证。
- **创新状态**: unverified