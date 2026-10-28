## 01 基本信息

- **标题**：Dissecting cell identity via network inference and in silico gene perturbation
- **作者与单位**：Kamimoto, Kenji; Stringa, Blerta; Hoffmann, Christy M; Jindal, Kunal; Solnica-Krezel, Lilianna; Morris, Samantha A（华盛顿大学圣路易斯分校等）
- **期刊/预印本平台**：Nature
- **年份**：2023-02-10
- **论文类型**：方法学（Method）+ 应用验证
- **领域**：单细胞组学、基因调控网络推断、计算扰动模拟
- **关键词**：gene-regulatory network, single-cell multi-omics, in silico perturbation, cell identity, transcription factor
- **DOI/arXiv 号**：10.1038/s41586-022-05688-9
- **代码**：https://github.com/morris-lab/CellOracle
- **数据**：https://celloracle.org
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「基因调控网络（GRN）推断 + 计算机模拟扰动」方法学论文，核心对象是转录因子（TF）调控的细胞身份转变。与「TF–DNA 结合机制 × AI/物理模拟」课题的关联在于：其 GRN 推断以 TF 基序（motif）扫描为起点，将 TF–DNA 结合信息（motif）与单细胞表达数据整合，构建可解释的调控网络，并模拟 TF 扰动对细胞身份的影响。该方法为从序列基序到细胞表型的因果推断提供了可迁移框架，但其 GRN 推断采用线性回归而非深度学习或物理模拟，属于「基于统计学习的网络推断」路线。

## 02 一句话总结

本文提出 CellOracle 方法，利用 scRNA-seq 和 scATAC-seq 数据推断细胞类型特异的基因调控网络（GRN），通过线性回归模型模拟 TF 敲除（KO）后基因表达的级联变化，并将模拟的细胞身份转变向量与自然分化向量比对，从而预测 TF 对细胞命运的调控作用；该方法在造血和小鼠/斑马鱼胚胎发育中验证，并成功预测了此前未知的 lhx1a 在轴向中胚层发育中的调控功能。

## 03 研究问题

- **具体问题**：如何仅利用未受扰动的野生型单细胞多组学数据，推断细胞类型特异的 GRN，并模拟 TF 扰动后细胞身份的转变方向？
- **为什么重要**：实验性 TF 扰动（如 KO）在许多生物系统中难以实施或耗时费力；若能通过计算模拟准确预测 TF 扰动后果，将极大加速对细胞命运决定机制的理解，尤其在发育生物学和疾病研究中。
- **现有方法不足**：
  - 实验扰动方法（如 CRISPR 筛选）无法在多种细胞类型和发育阶段系统实施；
  - 已有的计算扰动方法（如 scGen）需要实验扰动数据作为训练集，限制了其在新场景中的应用；
  - 已有 GRN 推断方法（如 GENIE3、GRNBoost）虽能推断网络，但其模型形式（树模型等）不支持信号传播模拟，无法用于扰动预测；
  - 深度学习方法缺乏可解释性，难以揭示具体的基因调控机制。
- **精确研究问题**：Can we predict TF perturbation outcomes (cell identity shifts) using only unperturbed wild-type single-cell multi-omics data, without any experimental perturbation training data?

## 04 背景与发展脉络

**注：以下脉络基于本文框架，未经外部系统核验。**

1. **单细胞测序技术发展**（2010s 至今）：scRNA-seq 实现单细胞转录组 profiling；scATAC-seq 提供染色质可及性信息。代表性方法：Smart-seq2、10X Chromium、sci-ATAC-seq。
2. **GRN 推断方法**（2010s 至今）：
   - 基于相关/互信息：WGCNA（无方向网络）
   - 基于回归/树模型：GENIE3、GRNBoost（有方向，但模型不可微，不支持扰动模拟）
   - 基于 motif 信息：SCENIC（整合 TF 基序与共表达）
   - 局限：多数方法仅输出静态网络结构，无法模拟扰动后的动态变化
3. **计算扰动模拟**（2018 至今）：
   - scGen：基于变分自编码器 + 潜空间向量运算，但需要实验扰动数据训练
   - 本文主张位置：CellOracle 填补了「无需实验扰动数据即可模拟 TF 扰动」的空白，通过 GRN 线性模型 + 信号传播实现可解释的扰动模拟

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 实验扰动不可规模化 | TF KO 实验耗时费力，无法覆盖所有 TF × 细胞类型组合 | 作者未明确解释，属领域共识 | 未提供（作者在引言中暗示） |
| 已有计算扰动需实验数据 | scGen 等方法需要扰动前后的配对数据训练 | 作者解释：这些方法依赖实验扰动数据，限制了在新场景的应用 | 引言部分 |
| GRN 推断模型不可用于扰动模拟 | GENIE3/GRNBoost 等树模型无法进行梯度传播或信号传播 | 作者解释：线性模型是信号传播的必要条件 | Methods「Context-dependent GRN inference」节 |
| 静态网络无法反映动态细胞身份 | 传统 GRN 分析仅关注网络结构，无法预测细胞身份转变方向 | 作者解释：需要将网络与分化轨迹结合 | 引言及 Results 图 1 |
| 深度学习方法不可解释 | 黑箱模型无法揭示具体调控机制 | 作者解释：线性模型提供可解释的调控关系 | 引言部分 |
| 数据噪声和稀疏性 | 单细胞数据存在 dropout 和噪声，影响 GRN 推断准确性 | 作者通过 Ridge 正则化和聚类策略缓解 | Methods「Context-dependent GRN inference」节 |

## 06 核心思想

### 1) 表面方法

CellOracle 是一个五步流程：
1. **Base GRN 构建**：利用 scATAC-seq 数据（或通用启动子数据库）识别开放染色质区域，扫描 TF 结合基序（motif），构建 TF→靶基因的候选调控边（有向、无权）。
2. **上下文特异 GRN 推断**：将 scRNA-seq 表达矩阵按细胞聚类分组，对每个 cluster 用 Ridge 线性回归拟合靶基因表达 ~ TF 表达，得到加权有向 GRN。
3. **信号传播模拟**：模拟 TF 表达量变化（如 KO 设为 0），通过 GRN 线性模型迭代传播信号，计算所有基因的表达变化（ΔX）。
4. **细胞身份转变向量**：将 ΔX 投影到 2D 降维空间（如 force-directed graph），得到每个细胞的模拟转变向量。
5. **扰动评分（Perturbation Score, PS）**：计算模拟转变向量与自然分化向量的内积，量化 TF 扰动对分化的促进/抑制作用。

### 2) 核心洞察

- **将 GRN 从「静态描述」转化为「可计算的动力学模型」**：线性回归模型不仅用于推断网络结构，还作为信号传播的函数，实现「可微分的 GRN」。
- **基序信息提供方向性先验**：利用 TF 结合基序扫描确定调控方向（TF→靶基因），避免从表达数据中推断因果方向的困难。
- **Cluster-wise 建模捕捉上下文依赖性**：不同细胞类型/状态有不同 GRN 配置，反映 TF 调控的上下文特异性。
- **2D 向量比较实现可解释的扰动预测**：将高维基因表达变化压缩为 2D 向量，与分化轨迹比对，直观展示 TF 扰动如何改变细胞命运。

### 3) 可能的普适教训 [Analysis]

- **线性模型 + 网络传播是「可解释 AI」的一种有效范式**：在需要因果解释的生物场景中，线性模型的可解释性可能比深度学习的预测精度更有价值。
- **多模态数据整合的关键在于「互补性」**：scATAC-seq 提供静态的序列信息（motif），scRNA-seq 提供动态的表达信息，二者互补而非冗余。
- **模拟结果的可验证性是方法可信度的核心**：本文通过多个已知 TF 扰动表型验证，再预测新表型并实验验证，这种「回顾验证 + 前瞻预测 + 实验确认」的闭环是计算方法验证的典范。

## 07 方法总览

- **输入**：
  - scRNA-seq 表达矩阵（基因 × 细胞）
  - scATAC-seq 数据（或通用启动子数据库，如 UCSC TSS）
  - TF 基序数据库（如 CisBP）
- **输出**：
  - 细胞类型/状态特异的加权有向 GRN
  - TF 扰动模拟的细胞身份转变向量（2D）
  - 扰动评分（PS），用于排序 TF 对分化的调控潜力
- **模块**：
  1. Base GRN 构建（motif 扫描）
  2. Cluster-wise Ridge 回归 GRN 推断
  3. 信号传播模拟（迭代 ΔX 计算）
  4. 2D 向量投影（基于 force-directed graph）
  5. PS 计算与排序
- **训练**：Ridge 回归（Bayesian Ridge 或 Bagging Ridge），无端到端训练；信号传播为确定性计算
- **工具**：Python、scikit-learn、Scanpy、Velocyto.py（修改）、Cicero、gimmemotifs
- **反馈回路**：无显式反馈回路；模拟结果通过实验验证（CRISPR-Cas9 斑马鱼胚胎）
- **假设**：
  - TF 表达水平线性影响靶基因表达（线性回归假设）
  - 基序扫描识别的候选调控关系是真实调控的先验
  - 细胞身份可由 2D 降维空间中的位置近似表征
  - 信号传播的迭代次数（默认 3 次）足以捕捉主要调控效应

**文字流程**：
1. 从 scATAC-seq 或启动子数据库获取开放染色质区域 → 扫描 TF 基序 → 构建 base GRN（TF→靶基因候选边）
2. 将 scRNA-seq 细胞聚类，对每个 cluster 用 Ridge 回归拟合靶基因 ~ TF 表达，得到加权 GRN
3. 模拟 TF KO：将目标 TF 表达设为 0，通过 GRN 线性模型迭代传播信号，计算 ΔX
4. 将 ΔX 投影到 2D force-directed graph 空间，得到每个细胞的模拟转变向量
5. 计算转变向量与自然分化向量的内积（PS），排序 TF 调控潜力

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Base GRN 构建（motif 扫描） | 确定 TF→靶基因的候选调控边及方向 | 提供方向性先验，避免从表达数据推断因果方向的困难 | 输入：开放染色质区域、TF 基序数据库；输出：无权有向候选边 | 基准测试显示 scATAC-seq base GRN 优于 promoter base GRN（Extended Data 图 2） | 预期影响：移除后 GRN 推断失去方向性先验，可能引入大量假阳性反向边 [预期效应] |
| Cluster-wise Ridge 回归 | 推断上下文特异的加权 GRN | 不同细胞类型/状态有不同调控配置；线性模型支持信号传播 | 输入：scRNA-seq 表达矩阵、base GRN；输出：加权有向 GRN | 基准测试 AUROC 0.66–0.91（Extended Data 图 2） | 实测影响：无 base GRN 时 AUROC 排名 13/13（Extended Data 图 2a,b） |
| 信号传播模拟 | 计算 TF 扰动后的基因表达变化 | 将静态网络转化为可计算的动力学模型 | 输入：加权 GRN、TF 扰动设定；输出：ΔX 向量 | 与实验 KO 数据对比验证（图 2、Extended Data 图 5-9） | 预期影响：移除后无法模拟扰动效应 [预期效应] |
| 2D 向量投影 | 将高维 ΔX 压缩为可视化向量 | 直观展示细胞身份转变方向 | 输入：ΔX、2D 降维坐标；输出：转变向量 | 与 RNA velocity 可视化方法一致（Methods） | 预期影响：移除后无法直观比较扰动效应 [预期效应] |
| PS 计算 | 量化 TF 扰动对分化的促进/抑制作用 | 提供客观、可排序的指标 | 输入：转变向量、分化向量；输出：PS 值 | 85% 的 top 30 TF 为已知造血调控因子（Results 图 1i） | 预期影响：移除后无法系统排序 TF 调控潜力 [预期效应] |

## 09 关键公式符号

**1. GRN 线性回归模型**（Methods「Context-dependent GRN inference」节）：

$$x_j = \sum_{i=0}^{n} b_{i,j} x_i + c_j$$

- $x_j$：靶基因 j 的表达量
- $x_i$：候选调控 TF i 的表达量
- $b_{i,j}$：TF i 对靶基因 j 的调控权重（回归系数），$b_{i,j}=0$ 当 $i=j$
- $c_j$：截距项
- **用途**：推断 GRN 边的权重，构建加权有向网络
- **直觉**：靶基因表达是调控其表达的 TF 表达量的线性组合

**2. 信号传播的链式法则**（Methods「Simulation of cell identity following perturbation of regulatory genes」节）：

$$\frac{\partial x_j}{\partial x_i} = \prod_{k=0}^{n} \frac{\partial x_{k+1}}{\partial x_k} = \prod_{k=0}^{n} b_{k,k+1}$$

- $x_k$：从 TF i 到靶基因 j 最短路径上的有序节点
- **用途**：计算间接调控效应，实现信号在网络中的传播
- **直觉**：间接效应是路径上各边权重的乘积，类似深度学习中反向传播的链式法则

**3. 扰动评分（PS）**（Methods「Calculation of perturbation score」节，Extended Data 图 4）：

$$\text{PS} = \text{inner product of perturbation vector and differentiation vector}$$

- **用途**：量化 TF 扰动对分化的促进（正 PS）或抑制（负 PS）作用
- **直觉**：模拟转变方向与自然分化方向一致则促进分化，相反则抑制分化

## 10 实验设计与证据链

**数据集/群体**：
1. 小鼠造血：Paul et al. 2015 数据集（2,730 个髓系祖细胞，16 个 cluster）
2. 小鼠造血：Dahlin et al. 2018 数据集
3. 人类造血：Setty et al. 2019 数据集（Human Cell Atlas）
4. 小鼠器官发生：Pijuan-Sala et al. 2019（Tal1 KO 嵌合体，25,307 WT + 26,311 KO 细胞）
5. 斑马鱼胚胎发生：Farrell et al. 2018（38,731 细胞，38 个细胞类型/状态）
6. 自产斑马鱼数据：WT 参考图谱（38,606 细胞）、noto crispants、lhx1a crispants、sebox crispants、irx3a crispants

**指标**：
- GRN 推断：AUROC、EPR（early precision ratio）
- 扰动模拟：PS（扰动评分）、模拟细胞密度分布 vs 实验 KO 细胞密度分布
- 统计检验：卡方检验（细胞组成差异）、Wilcoxon 秩和检验（基因表达差异，Bonferroni 校正）

**评测协议**：
- GRN 基准测试：使用 ChIP-seq 数据构建 ground truth，比较 CellOracle vs WGCNA、DCOL、GENIE3、SCENIC
- 扰动模拟验证：将模拟结果与已知 KO 表型对比（如 Spi1、Gata1、Cebpa、Cebpe、Tal1）
- 前瞻预测：预测 lhx1a 等新调控因子，通过 CRISPR-Cas9 斑马鱼实验验证

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| GRN 推断基准测试 | CellOracle GRN 推断准确 | 5 组织 × 4 种对比方法（WGCNA、DCOL、GENIE3、SCENIC） | AUROC 0.66–0.91，scATAC-seq base GRN 最佳 | CellOracle 推断准确，优于或持平现有方法 | 基准测试仅在 5 组织，未覆盖所有细胞类型 | Extended Data 图 2 |
| Spi1/Gata1 KO 模拟 | 模拟结果与已知造血调控一致 | 模拟 KO vs 已知表型 | Spi1 KO 促进 ME 分化、抑制 GM 分化；Gata1 KO 相反 | CellOracle 能正确模拟已知 TF 调控 | 未检测到 Spi1 KO 后红系祖细胞耗竭（可能因增殖效应未建模） | Results 图 1e,f |
| Cebpa/Cebpe KO 模拟 | 模拟结果与实验 KO 细胞分布一致 | 模拟 vs 实验 KO scRNA-seq | 模拟预测的细胞密度分布与实验 KO 一致 | CellOracle 能定量预测 KO 后的细胞组成变化 | 模拟的是稳态分布而非动态过程 | Results 图 2b-d |
| Tal1 KO 模拟 | 模拟结果与嵌合体实验一致 | 模拟 vs Pijuan-Sala et al. Tal1 KO | 正确模拟血液内皮祖细胞分化抑制 | CellOracle 适用于器官发生数据 | 仅验证了 Tal1 一个基因 | Extended Data 图 9 |
| noto KO 模拟 | 预测 noto 调控轴向中胚层命运 | 模拟 vs 斑马鱼突变体 | 预测 prechordal plate 扩张，实验验证 | CellOracle 能预测已知表型的新方面 | 未检测到脊索完全消失（可能因模型未包含形态发生） | Results 图 3e,f |
| lhx1a 前瞻预测 | 发现新的轴向中胚层调控因子 | 模拟预测 vs CRISPR-Cas9 实验 | lhx1a crispants 显示早期脊索分化抑制、prechordal plate 扩张 | CellOracle 能发现此前未知的调控因子 | 未验证 lhx1a 的直接靶基因 | Results 图 5 |

## 11 结论正确解读

- **任务范围**：CellOracle 模拟的是 TF 扰动后基因表达的「一阶线性响应」，通过信号传播捕捉间接效应，但**不模拟**细胞增殖、凋亡、细胞间通讯等非转录调控过程。
- **Oracle/真值输入**：base GRN 构建依赖 TF 基序数据库和开放染色质数据，这些是「先验知识」而非从数据中学习；模拟结果的质量受限于 base GRN 的完整性。
- **端到端状态**：CellOracle **不是**端到端模型——GRN 推断和扰动模拟是分离的步骤，中间有人工干预（如 cluster 划分、阈值设定）。
- **算力成本**：Ridge 回归和信号传播计算量较小，可在普通工作站运行；但 scATAC-seq 数据处理和 motif 扫描需要较多计算资源。
- **历史数据依赖**：模型完全依赖输入数据中的细胞类型/状态覆盖度；未观察到的细胞状态无法被模拟。
- **模型依赖**：线性回归假设 TF 对靶基因的调控是线性的、可加的，忽略了非线性调控（如协同、竞争、表观遗传修饰）。
- **最难情形**：低表达 TF、基序未知的 TF、以及调控效应主要通过非转录机制（如蛋白修饰）介导的 TF。
- **群体/领域边界**：验证集中在造血和早期胚胎发育；在成体组织、疾病状态或非模式生物中的表现未验证。
- **不确定性**：PS 的统计显著性依赖于随机化 null 分布，但未提供置信区间；模拟的定量精度（如 ΔX 的绝对值）未与实验定量对比。

**有边界的复述**：CellOracle 能够利用野生型单细胞多组学数据，通过线性 GRN 模型和信号传播，在造血和胚胎发育场景中正确预测已知 TF 扰动表型，并发现新的调控因子（如 lhx1a）；但其预测限于转录调控层面的细胞身份转变方向，不涵盖非转录机制，且定量精度有限。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 无法模拟细胞增殖 | Spi1 KO 模拟未检测到红系祖细胞耗竭，可能因增殖效应未建模 | 未明确提及 | Results 图 1e 相关讨论 |
| 数据质量依赖 | TF 表达稀疏或基序未知时无法推断 | 未明确提及 | Methods「Context-dependent GRN inference」节 |
| 线性模型假设 | 无法捕捉非线性调控关系 | 未明确提及 | Methods「Context-dependent GRN inference」节 |
| 2D 投影信息损失 | 高维 ΔX 压缩为 2D 向量可能丢失信息 | 未明确提及 | Methods「Simulation of cell identity」节 |
| 需要先验 base GRN | 无 scATAC-seq 数据时使用通用启动子数据库，性能下降 | 未明确提及 | Extended Data 图 2 |
| 模拟限于转录层面 | 不包含表观遗传、翻译后修饰等调控 | 未明确提及 | Discussion 部分 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 线性回归假设可能过于简化 | TF 调控常涉及非线性协同/拮抗效应，线性模型可能遗漏关键调控 | 影响 GRN 推断的生物学真实性 | 在已知非线性调控模块（如增强子-启动子环）中测试模型预测 | Methods 中明确使用线性模型 |
| 信号传播的迭代次数（默认 3）缺乏理论依据 | 不同网络拓扑可能需要不同传播深度 | 影响模拟 ΔX 的准确性 | 对不同迭代次数进行敏感性分析，与实验数据对比 | Methods「Simulation of cell identity」节 |
| PS 的 null 分布基于随机化，但未报告效应量置信区间 | 无法评估预测的定量可靠性 | 影响方法在筛选场景中的实用性 | 对多个已知 TF 重复计算 PS 的置信区间 | Methods「Calculation of perturbation score」节 |
| 验证集中在高表达、已知功能的 TF | 低表达 TF 或非经典 TF 的预测能力未验证 | 影响方法在发现新调控因子时的可靠性 | 对低表达 TF 进行模拟并与实验对比 | Results 图 5 中验证的均为高表达 TF |
| 2D 投影依赖降维方法选择 | 不同降维方法（UMAP、t-SNE、force-directed）可能产生不同结果 | 影响模拟转变向量的稳健性 | 使用多种降维方法重复分析，比较结果一致性 | Methods 中仅使用 force-directed graph |
| 未与深度学习基线对比 | 深度生成模型（如 scGen）在扰动预测上可能更优 | 影响方法在「AI 方法」谱系中的定位 | 在相同数据集上对比 CellOracle 与 scGen 等 | 引言中仅提及 scGen 需实验数据，未做直接对比 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **可解释的扰动模拟框架**：CellOracle 展示了「线性 GRN + 信号传播」如何将静态网络转化为可计算的扰动模型，这一「可微分网络」思想可迁移到 TF–DNA 结合机制研究中——例如，将 TF–DNA 结合亲和力（来自 PBM、SELEX 或深度学习预测）作为 GRN 边的先验权重，结合表达数据微调。

2. **多模态数据互补整合**：scATAC-seq（染色质可及性 + motif）提供「静态先验」，scRNA-seq 提供「动态证据」，二者整合优于单一数据源。这一原则可迁移到 TF–DNA 结合预测：将序列特征（motif、进化保守性）与功能数据（ChIP-seq、表达）结合。

3. **Cluster-wise 上下文建模**：不同细胞状态有不同 GRN 配置，而非全局单一网络。这一「上下文依赖」思想对 TF–DNA 结合研究有启示：TF 的结合靶点可能因细胞类型/状态而异，预测模型应考虑细胞上下文。

4. **回顾验证 + 前瞻预测 + 实验确认的闭环**：本文的验证策略（先用已知 TF 验证，再预测新 TF 并实验确认）是计算方法开发的黄金标准，适用于任何 TF–DNA 结合预测模型的验证。

5. **2D 向量比较作为可解释输出**：将高维基因表达变化压缩为 2D 向量并与参考轨迹比较，提供直观、可解释的预测结果。这一可视化策略可迁移到 TF 结合位点预测的解读。

6. **线性模型的「够用」原则**：在需要因果解释的场景中，线性模型的可解释性可能比复杂模型的预测精度更有价值。这提示在 TF–DNA 结合机制研究中，简单可解释的模型（如位置权重矩阵的改进版）仍有重要地位。

## 15 与已有知识连接

- **GRN 推断方法谱系**：本文与 GENIE3、GRNBoost、SCENIC 等方法的对比（Extended Data 图 2），可连接到这些方法的原始文献（Huynh-Thu et al. 2010; Moerman et al. 2019; Aibar et al. 2017）。
- **RNA velocity 方法**：CellOracle 的可视化方法修改自 Velocyto（La Manno et al. 2018），可连接到 RNA velocity 及其后续发展（scVelo, Bergen et al. 2020）。
- **单细胞扰动预测**：本文与 scGen（Lotfollahi et al. 2019）的对比，可连接到深度生成模型在扰动预测中的应用。
- **TF 基序数据库**：本文使用 CisBP（Weirauch et al. 2014）和 gimmemotifs（van Heeringen 2017），可连接到 TF–DNA 结合 motif 预测的基准资源。
- **斑马鱼发育生物学**：noto、lhx1a 的验证实验涉及轴向中胚层发育，可连接到脊索/前索板发育的经典文献（Halpern et al. 1997; Toyama et al. 1995）。
- **[Analysis] 候选方向**：本文的 GRN 推断以 motif 扫描为先验，但未使用深度学习进行 motif 发现或结合亲和力预测。可连接到近期基于深度学习的 TF–DNA 结合预测方法（如 DeepBind, Alipanahi et al. 2015; BPNet, Avsec et al. 2021），探讨将深度学习预测的 TF 结合位点作为 GRN 先验的可行性。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：DeepGRN-Perturb——将深度学习 TF–DNA 结合预测与 CellOracle 式扰动模拟整合
   - **来源局限/观察**：CellOracle 的 base GRN 依赖传统 motif 扫描，可能遗漏非经典结合位点；深度学习模型（如 BPNet）可更准确预测 TF 结合
   - **核心假设**：用深度学习预测的 TF 结合概率替代传统 motif 扫描，可提高 GRN 推断的准确性，进而提升扰动模拟的预测能力
   - **初步方法**：在 CellOracle 框架中，将 base GRN 构建步骤替换为深度学习预测的 TF–DNA 结合概率矩阵；在造血和斑马鱼数据上对比新旧方法的 AUROC 和扰动预测准确性
   - **验证方式**：与 CellOracle 原始结果对比，用已知 TF KO 表型验证
   - **创新状态**：unverified

2. **候选名称**：BindingAffinity-GRN——将 TF–DNA 结合亲和力（定量）纳入 GRN 边权重
   - **来源局限/观察**：CellOracle 的 GRN 边权重仅由表达数据回归得到，未显式利用 TF–DNA 结合亲和力信息
   - **核心假设**：将体外结合亲和力（如 PBM、SELEX 数据）作为正则化先验，可减少 GRN 推断中的假阳性边
   - **初步方法**：在 Ridge 回归中加入结合亲和力先验项；在造血数据上比较有无先验的 GRN 质量和扰动预测准确性
   - **验证方式**：与 ChIP-seq ground truth 对比，评估边权重的生物学合理性
   - **创新状态**：unverified

3. **候选名称**：CellOracle-MD——将分子动力学（MD）模拟的 TF–DNA 结合构象变化与 GRN 扰动预测结合
   - **来源局限/观察**：CellOracle 完全基于转录组数据，不包含 TF–DNA 结合的物理化学信息；MD 模拟可提供结合动力学和构象变化
   - **核心假设**：MD 模拟揭示的 TF–DNA 结合稳定性（如结合自由能）可作为 GRN 边权重的物理约束，提高预测准确性
   - **初步方法**：对关键 TF（如 Spi1、Gata1）进行 MD 模拟，计算结合自由能；将自由能作为先验纳入 CellOracle 的 GRN 推断；在造血数据上验证
   - **验证方式**：对比有无 MD 先验的扰动预测准确性
   - **创新状态**：unverified

4. **候选名称**：CellOracle-3D——整合 3D 基因组结构（Hi-C）数据改进 GRN 推断
   - **来源局限/观察**：CellOracle 的 base GRN 仅考虑线性距离（启动子-增强子），未利用 3D 基因组结构信息
   - **核心假设**：3D 基因组接触频率可更准确识别增强子-启动子配对，减少 base GRN 中的假阳性边
   - **初步方法**：将 Hi-C 数据整合到 base GRN 构建中，仅保留 3D 空间邻近的 TF-靶基因对；在造血和斑马鱼数据上对比
   - **验证方式**：与 CellOracle 原始 base GRN 对比 AUROC 和扰动预测准确性
   - **创新状态**：unverified

5. **候选名称**：Perturb-Transfer——跨物种 TF 扰动预测迁移学习
   - **来源局限/观察**：CellOracle 在斑马鱼中预测的 lhx1a 功能可能在小鼠/人类中保守，但未验证跨物种迁移
   - **核心假设**：从斑马鱼训练的 GRN 模型可通过迁移学习适应小鼠/人类数据，实现跨物种 TF 功能预测
   - **初步方法**：用斑马鱼 GRN 作为先验，在小鼠/人类造血数据上微调；对比迁移学习与从头训练的预测准确性
   - **验证方式**：用已知跨物种保守 TF 功能验证
   - **创新状态**：unverified