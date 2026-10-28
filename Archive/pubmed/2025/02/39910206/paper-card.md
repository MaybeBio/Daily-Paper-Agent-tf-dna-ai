## 01 基本信息

- **标题**：CoTF-reg reveals cooperative transcription factors in oligodendrocyte gene regulation using single-cell multi-omics
- **作者**：Choi, Jerome J; Svaren, John; Wang, Daifeng
- **单位**：未提供（根据作者信息推测为美国威斯康星大学麦迪逊分校相关机构，但原文未明确列出）
- **期刊/预印本平台**：Communications Biology
- **年份**：2025
- **论文类型**：方法学/分析框架研究（含实验验证）
- **领域**：单细胞多组学、基因调控、转录因子协同作用、深度学习
- **关键词**：cooperative transcription factors, oligodendrocyte, scRNA-seq, scATAC-seq, deep learning, Shapley interaction
- **DOI/arXiv 号**：10.1038/s42003-025-07570-6
- **代码**：未提供（文中提及代码在 GitHub 上公开，但未给出具体链接）
- **数据**：scRNA-seq（SEA-AD、Multi-omics、ROSMAP、Cross-disorder）、scATAC-seq、ChIP-seq（GSE64703、GSE42447、GSM1906296）
- **阅读日期**：2026-05-13（以当前日期为准）
- **在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**：该文聚焦于**TF-TF协同结合**的识别，而非单TF-DNA结合。它通过整合单细胞多组学数据（scRNA-seq + scATAC-seq），利用 motif 共定位推断 TF 共结合，再用深度学习预测靶基因表达，最后用 Shapley interaction 量化 TF 对之间的协同贡献。该方法为从表达和染色质可及性数据中推断 TF 协同调控提供了可迁移的框架，与传统的基于序列的 TF-DNA 结合预测（如 DeepBind、BPNet）互补。

---

## 02 一句话总结

该文开发了 coTF-reg 分析框架，整合 scRNA-seq 和 scATAC-seq 数据，通过 motif 共定位识别少突胶质细胞特异调控区中的共结合 TF 对，用深度神经网络预测靶基因表达，并利用 Shapley interaction 分数量化 TF 对间的协同效应，最终通过 eQTL 和 ChIP-seq 验证了 SOX10-OLIG2、SOX10-NKX2.2 等协同 TF 对。

---

## 03 研究问题

- **具体问题**：在少突胶质细胞中，哪些转录因子（TF）对协同调控靶基因（TG）的表达？如何从单细胞多组学数据中系统性地识别这些协同 TF 对？
- **为什么重要**：TF 通常以组合方式协同调控基因表达，但大多数现有工具只关注单个 TF 与靶基因的关系，忽略了 TF-TF 协同效应。理解 TF 协同调控对于阐明细胞类型特异性基因调控机制（如少突胶质细胞髓鞘形成）至关重要。
- **现有方法不足**：现有工具（如 SCENIC+、Signac、scGRNom）主要预测单个 TF 与 TG 的调控关系，不涉及 TF-TF 相互作用及其对 TG 表达的联合效应。此外，这些工具多基于相关性或 motif 扫描，缺乏对 TF 间协同效应的定量评估。
- **精确的「Can ... ?」研究问题**：Can we identify cooperative TF pairs that co-regulate target gene expression in oligodendrocytes by integrating scRNA-seq and scATAC-seq data with deep learning and Shapley interaction scores?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注为「仅本文框架」，未经外部系统核验。

1. **单细胞多组学时代**：scRNA-seq 和 scATAC-seq 的出现使得在单细胞水平同时测量基因表达和染色质可及性成为可能，为构建细胞类型特异性基因调控网络（GRN）提供了数据基础。
2. **GRN 推断工具**：SCENIC+、Signac、scGRNom 等工具利用 motif 扫描和相关性分析预测 TF-TG 关系，但主要关注单个 TF，忽略了 TF 间的协同作用。
3. **深度学习在调控基因组学中的应用**：深度神经网络（DNN）已被用于从序列或表达数据预测基因表达，但其在 TF 协同作用识别中的应用尚少。
4. **可解释性方法**：Shapley 值及其交互版本（Shapley interaction）为解释黑箱模型提供了理论基础，可量化特征间交互对预测的贡献。
5. **本文主张的位置**：coTF-reg 首次将「motif 共定位 → DNN 预测 → Shapley interaction 评分」整合为一个完整流程，专门用于识别协同 TF 对，填补了现有 GRN 工具在 TF-TF 协同层面的空白。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有 GRN 工具忽略 TF-TF 协同 | SCENIC+、Signac 等只预测单 TF-TG 关系 | 这些工具的设计目标是单 TF 调控关系，未考虑 TF 对靶基因的联合效应 | Introduction 第 3 段 |
| 缺乏对 TF 协同效应的定量评估 | 无法区分 TF 对是独立作用还是协同作用 | 现有方法多基于相关性或共定位，缺乏对交互效应的直接度量 | Introduction 第 3 段；Results 第 1 段 |
| 单细胞数据噪声大、维度高 | 直接使用原始单细胞数据训练模型易过拟合 | 单细胞数据存在 dropout 和批次效应，需要降维和 metacell 聚合 | Methods: scRNA-seq 数据部分 |
| motif 数据库不完整 | 部分 TF（如 MYRF）缺乏高质量 motif | motif 预测依赖 JASPAR 等数据库，某些关键 TF 的 motif 质量差或缺失 | Methods: Position Frequency Matrices 部分 |
| 协同 TF 对的验证困难 | 缺乏直接的蛋白质-蛋白质互作或 ChIP-seq 共结合数据 | 人类少突胶质细胞 ChIP-seq 数据有限，需借助跨物种（大鼠）数据验证 | Results: ChIP-seq 验证部分 |

---

## 06 核心思想

### 1) 表面方法
coTF-reg 是一个五步流程：
1. 从 scATAC-seq 数据中提取少突胶质细胞特异开放染色质区域（peak），并通过 peak-to-gene link 关联到靶基因；
2. 在 peak 区域中扫描 TF motif，识别共结合的 TF 对；
3. 从 scRNA-seq 数据中提取 TF 和 TG 的表达量（metacell 聚合）；
4. 为每个 TG 训练一个 DNN，输入为共结合 TF 的表达量，输出为 TG 表达量；
5. 计算 Shapley interaction 分数，量化 TF 对间的协同效应，筛选高协同 TF 对。

### 2) 核心洞察
- **共结合 ≠ 协同**：TF 在相同调控区共结合（motif 共定位）只是协同的必要条件，真正的协同需要体现在对靶基因表达的联合效应上。因此，作者用 DNN 建模 TF 表达 → TG 表达的非线性关系，再用 Shapley interaction 捕捉超出独立贡献的交互效应。
- **表达层面的协同可被量化**：即使没有直接的 ChIP-seq 共结合数据，通过表达数据的非线性建模和可解释性分析，也能推断 TF 间的协同调控关系。

### 3) 可能的普适教训 [Analysis]
- 将「共定位（空间）→ 表达关联（功能）」两阶段筛选策略，可推广到其他细胞类型或物种的 TF 协同调控研究。
- Shapley interaction 不仅适用于 DNN，也可用于其他预测模型（如梯度提升树），为可解释 AI 在调控基因组学中的应用提供了范例。
- 该方法不依赖 TF 的 DNA 结合结构域信息，因此可扩展到非典型 TF 或辅因子的协同研究。

---

## 07 方法总览

- **输入**：
  - scATAC-seq peak-to-gene links（人类少突胶质细胞）
  - scRNA-seq 表达矩阵（同一批细胞）
  - JASPAR2022 motif 数据库（+ 补充 motif）
- **输出**：
  - 协同 TF 对列表（按 Shapley interaction 分数排序）
  - 基因调控网络（GRN），连接 TF 对与靶基因
  - TF 层级（master/middle/bottom regulator）
- **模块**：
  1. Peak 筛选与注释（少突胶质细胞特异、差异可及）
  2. Motif 扫描与 TF 共结合对识别
  3. Metacell 构建与表达量化
  4. DNN 训练（每个 TG 一个模型）
  5. Shapley interaction 计算与协同 TF 对筛选
  6. 验证模块（eQTL 映射、ChIP-seq 共定位、布尔逻辑）
- **训练**：每个 TG 一个 DNN，输入为 206 个 TF 的表达量，输出为 TG 表达量；80% 数据训练，5 折交叉验证，20% 数据测试；Adam 优化器，学习率 0.001，early stopping。
- **反馈回路**：无显式反馈回路；模型为前馈预测，Shapley interaction 在训练后计算。
- **文字流程**：
  scATAC-seq peaks → 少突胶质细胞特异 peak 筛选 → motif 扫描 → 共结合 TF 对 → 匹配 scRNA-seq 表达 → 构建 DNN 训练集 → 逐 TG 训练 DNN → 计算 Shapley interaction → 筛选高协同 TF 对 → 构建 GRN → eQTL/ChIP-seq/布尔逻辑验证。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Peak 筛选与注释 | 识别少突胶质细胞特异开放染色质区域 | 限定调控区范围，减少噪声 | 输入：scATAC-seq peaks；输出：787 个少突胶质细胞特异 peak | Results 图 2a | 预期影响：peak 数量减少，可能遗漏部分调控区 [预期效应] |
| Motif 扫描与共结合识别 | 在 peak 中扫描 TF motif，识别共定位 TF 对 | 提供 TF 共结合的候选对 | 输入：peak 序列 + JASPAR motif；输出：8101 个共结合 TF 对 | Results 图 2a | 预期影响：无 motif 的 TF 无法被检测 [预期效应] |
| Metacell 构建 | 将单细胞聚合成 metacell，降低噪声 | 单细胞表达数据稀疏，直接建模不稳定 | 输入：scRNA-seq 细胞；输出：2004 个 metacell | Methods: scRNA-seq 部分 | 预期影响：丢失单细胞分辨率 [预期效应] |
| DNN 训练 | 预测 TG 表达，捕捉 TF 间非线性交互 | 线性模型无法捕捉协同效应 | 输入：206 TF 表达；输出：TG 表达 | Methods: Deep learning 部分 | 预期影响：无法捕捉非线性交互 [预期效应] |
| Shapley interaction 计算 | 量化 TF 对间的协同贡献 | 提供协同效应的定量指标 | 输入：训练好的 DNN + 测试数据；输出：TF 对 SI 分数 | Results 图 4 | 预期影响：无法区分协同与独立效应 [预期效应] |
| eQTL 映射 | 验证调控区的功能意义 | 提供遗传变异→表达的因果证据 | 输入：eQTL 数据 + peak 区域；输出：383 个 eSNP 映射 | Results 图 6a | 预期影响：失去独立验证 [预期效应] |
| ChIP-seq 共定位 | 验证 TF 对的实际共结合 | 提供蛋白质-DNA 结合的直接证据 | 输入：大鼠 ChIP-seq 数据；输出：SOX10-OLIG2、SOX10-NKX2.2 共定位 | Results 图 6c-e | 预期影响：失去实验验证 [预期效应] |
| 布尔逻辑分析 | 用逻辑门描述 TF 对协同方式 | 提供协同的另一种形式化描述 | 输入：TF-TF-TG 表达三元组；输出：逻辑门分类（AND/OR 等） | Results: Boolean 部分 | 预期影响：失去协同的布尔描述 [预期效应] |

---

## 09 关键公式符号

1. **超几何检验（共富集分析）**：
   $$\Pr(X \ge k | n; N; m) = \sum_{x=k}^{\min(n,m)} \frac{\binom{m}{x}\binom{N-m}{n-x}}{\binom{N}{n}}$$
   - N：所有 TF 结合位点总数
   - m：TF1 的结合位点数
   - n：TF2 的结合位点数
   - k：TF1 和 TF2 共定位的位点数
   - 用途：判断两个 TF 的共定位是否显著高于随机预期

2. **DNN 隐藏层输出**：
   $$Z_i = f(W_i \cdot X + b_i)$$
   - X：输入（206 个 TF 的表达量）
   - W_i、b_i：第 i 层的权重矩阵和偏置向量
   - f：激活函数（LeakyReLU）
   - 用途：逐层非线性变换，最终输出 TG 表达量

3. **均方误差（MSE）损失**：
   $$MSE = \frac{1}{N}\sum_{i=1}^{N}(Z_i - Y_{true,i})^2$$
   - Z_i：预测的 TG 表达量
   - Y_true,i：实际的 TG 表达量
   - 用途：训练 DNN 的损失函数

4. **Shapley interaction（SI）**：
   $$\delta_{ij}^f = f(X_k; S \cup \{i,j\}) - f(X_k; S \cup \{i\}) - f(X_k; S \cup \{j\}) + f(X_k; S)$$
   $$SI_{ij}^f(X_k) = E_{p(S)}[\delta_{ij}^f(X_k; S)]$$
   $$SI_{ij} = E_{p(X)}[|SI_{ij}^f(X)|]$$
   - f：DNN 模型
   - X_k：第 k 个样本
   - S：特征子集
   - 用途：量化 TF i 和 j 对 TG 表达的交互贡献

5. **变异系数（CV）**：
   $$CV = \frac{\sigma}{\mu}$$
   - σ：标准差，μ：均值
   - 用途：筛选 SI 分数稳定的 TF 对（CV > 0.5 移除）

6. **层级高度（hierarchy height）**：
   $$h = \frac{O - I}{O + I}$$
   - O：出度（该 TF 调控的 TG 数），I：入度（调控该 TF 的 TF 数）
   - 用途：将 TF 分为 top (h > 0.33)、middle (−0.33 < h < 0.33)、bottom (h < −0.33) regulator

---

## 10 实验设计与证据链

### 数据集与规模
- **主数据集**：SEA-AD（西雅图阿尔茨海默病研究中心）背外侧前额叶皮层 scRNA-seq，1,395,601 细胞，18 种细胞类型；少突胶质细胞亚群用于分析
- **scATAC-seq**：同一脑区的少突胶质细胞 peak-to-gene link 数据
- **验证数据集**：Multi-omics（同一批细胞的多组学）、ROSMAP（宗教秩序研究/记忆与衰老项目）、Cross-disorder（跨疾病）
- **ChIP-seq**：大鼠少突胶质细胞 SOX10、OLIG2、NKX2.2 数据（GSE64703、GSE42447、GSM1906296）
- **eQTL**：少突胶质细胞 eQTL 数据（PsychENCODE）
- **指标**：MSE、NRMSE（归一化均方根误差）、Shapley interaction 分数、富集 p 值（超几何检验）、CV

### 实验列表

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| 少突胶质细胞特异 peak 鉴定 | 存在少突胶质细胞特异的调控区 | 少突胶质细胞 vs 其他脑细胞类型 | 787 个特异 peak | 少突胶质细胞具有独特的调控景观 | 未证明这些 peak 全部有功能 | Results 图 2a |
| Motif 共定位分析 | 存在显著共定位的 TF 对 | 超几何检验，FDR < 0.1 | 8101 个共结合 TF 对 | 大量 TF 对在少突胶质细胞调控区中共定位 | 共定位不等于功能协同 | Results 图 2a |
| DNN 预测 TG 表达 | TF 表达可预测 TG 表达 | 206 TF 输入，逐 TG 建模 | 445 个 TG 的模型 | TF 表达与 TG 表达存在可学习的关系 | 未与线性模型对比 | Methods: Deep learning |
| Shapley interaction 分析 | 共结合 TF 对具有高交互分数 | 关键 TF 对 vs 非关键 TF 对 | 关键 TF 对 SI 分数显著更高（p < 0.0001） | 共结合 TF 对确实协同调控 TG | 未证明所有高 SI 对都有直接蛋白质互作 | Results 图 4b |
| eQTL 映射 | 协同 TF 对所在区域富集 eQTL | eQTL 映射到 643 个 peak | 383 个 eSNP、159 个 eGene 映射 | 协同 TF 对区域具有遗传调控证据 | eQTL 不直接证明 TF 结合 | Results 图 6a |
| ChIP-seq 共定位验证 | SOX10-OLIG2、SOX10-NKX2.2 实际共结合 | 大鼠 ChIP-seq 数据 | SOX10 信号在 OLIG2/NKX2.2 位点富集 | 预测的协同 TF 对在实验数据中得到验证 | 仅验证了少数 TF 对 | Results 图 6c-e |
| 布尔逻辑分析 | TF 对协同符合 AND/OR 逻辑 | 100 次置换检验 | 82.2% 的 TF 对有一致逻辑门 | TF 对协同具有布尔结构 | 布尔逻辑是简化描述 | Results: Boolean 部分 |
| 消融研究 | 随机 TF 集预测能力下降 | 206 随机 TF vs 206 共结合 TF | 共结合 TF 预测 NRMSE 更低 | 共结合 TF 确实携带靶基因调控信息 | 未比较不同模型架构 | Results: Ablation 部分 |

---

## 11 结论正确解读

- **任务范围**：该研究仅针对**少突胶质细胞**（人类背外侧前额叶皮层），结论不一定适用于其他脑区或其他细胞类型。
- **Oracle/真值输入**：peak-to-gene link 来自已发表数据，其准确性直接影响下游分析；motif 扫描依赖 JASPAR 数据库，存在 motif 不完整或假阳性问题。
- **端到端状态**：coTF-reg 是分析框架而非端到端预测工具；DNN 仅用于预测 TG 表达，不直接预测 TF 结合位点。
- **算力成本**：每个 TG 训练一个 DNN，445 个 TG 需训练 445 个模型，计算成本较高但未报告具体 GPU 时间。
- **历史数据依赖**：依赖已发表的 scATAC-seq 和 scRNA-seq 数据，数据质量直接影响结果。
- **模型依赖**：DNN 架构（7 层全连接）较简单，未与更复杂架构（如 Transformer、GNN）对比。
- **最难情形**：低表达的 TF 或 TG 预测困难；缺乏高质量 motif 的 TF（如 MYRF）可能被遗漏。
- **群体/领域边界**：仅人类少突胶质细胞；跨物种验证仅使用大鼠 ChIP-seq，未在其他物种中系统验证。
- **不确定性**：Shapley interaction 分数依赖模型训练，不同随机种子可能产生不同结果；CV 筛选虽降低了不稳定性，但未报告置信区间。

**有边界的复述**：coTF-reg 在人类少突胶质细胞中识别出 8101 个共结合 TF 对，其中关键 TF 对的 Shapley interaction 分数显著高于非关键 TF 对，并通过 eQTL 和 ChIP-seq 验证了 SOX10-OLIG2、SOX10-NKX2.2 等协同关系。该方法可推广到其他细胞类型，但需注意 motif 数据库覆盖度和单细胞数据质量的限制。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 仅分析两两 TF 互作 | 当前框架限于 TF 对，无法处理三个及以上 TF 的协同 | 开发能处理 TF 簇的方法 | Discussion 第 2 段 |
| motif 数据库依赖 | MYFX 等关键 TF 缺乏高质量 motif，可能遗漏 | 结合蛋白质-DNA 结合实验数据改进 motif 预测 | Methods: Position Frequency Matrices 部分 |
| 缺乏直接蛋白质互作证据 | ChIP-seq 验证仅覆盖少数 TF 对 | 未来可用 Hi-C、3C 等技术验证空间互作 | Discussion 第 3 段 |
| 未考虑 TF 翻译后修饰 | 模型仅使用表达量，未纳入磷酸化等修饰信息 | 整合蛋白质组学数据 | Discussion 第 4 段 |
| 跨物种验证有限 | 仅用大鼠 ChIP-seq 验证 | 在更多物种中验证 | Results: ChIP-seq 部分 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| DNN 预测 TG 表达可能仅捕捉相关性而非因果性 | TF 表达与 TG 表达的相关可能由共同上游调控因子驱动，而非直接调控 | 若为相关性，则 Shapley interaction 可能高估 TF 协同的因果贡献 | 用扰动实验（如 CRISPR 敲低 TF）验证预测的协同 TF 对 | Methods: Deep learning 部分 |
| 共定位分析依赖 motif 扫描，存在大量假阳性 | JASPAR motif 短且简并，可能在不同位点误匹配 | 假阳性共定位对会稀释真正的协同信号 | 用 ChIP-exo 或 SELEX 数据验证 motif 预测 | Methods: Position Frequency Matrices 部分 |
| 未与线性模型或简单基线对比 | DNN 的优越性未得到证明 | 若线性模型表现相当，则无需深度学习 | 对比线性回归、随机森林等模型的预测性能 | Methods: Deep learning 部分 |
| Shapley interaction 计算依赖模型可解释性假设 | Shapley 值在特征相关时可能不稳定 | 特征相关性可能导致 SI 分数偏差 | 用模拟数据检验 SI 分数在已知协同关系下的恢复能力 | Methods: Shapley interaction 部分 |
| 少突胶质细胞特异 peak 的筛选标准可能过于严格 | 可能遗漏在少突胶质细胞中低水平但功能重要的调控区 | 遗漏的调控区可能包含关键协同 TF 对 | 用不同显著性阈值进行敏感性分析 | Results 图 2a |
| 布尔逻辑分析（Loregic）的生物学解释有限 | AND/OR 逻辑门是简化模型，真实调控可能更复杂 | 过度简化可能误导对协同机制的理解 | 用定量模型（如 Michaelis-Menten）替代布尔逻辑 | Results: Boolean 部分 |

---

## 14 学到什么

### Agent 提炼的知识候选

1. **「共定位 → 功能验证」两阶段策略**：先通过 motif 共定位筛选候选 TF 对，再用表达数据建模验证功能协同。可迁移到本课题：在 TF-DNA 结合预测中，先用 ChIP-seq 或 ATAC-seq 鉴定共结合位点，再用表达数据或报告基因实验验证协同功能。

2. **Shapley interaction 用于量化 TF 协同**：Shapley interaction 可分解预测模型中特征对的联合贡献，适用于任何黑盒模型。可迁移到本课题：在基于深度学习的 TF-DNA 结合预测模型中，用 Shapley interaction 识别对结合贡献显著的 TF 对或序列特征组合。

3. **Metacell 聚合降低单细胞噪声**：将单细胞聚合成 metacell 再进行下游分析，可减少 dropout 和采样噪声。可迁移到本课题：在单细胞 ATAC-seq 数据中分析 TF 结合时，可先用 metacell 聚合提高信噪比。

4. **多组学整合的互补性**：scATAC-seq 提供调控区位置信息，scRNA-seq 提供表达信息，两者结合可同时考虑「在哪里结合」和「结合后有何效果」。可迁移到本课题：将 TF-DNA 结合预测与表达数据结合，可区分「结合但不调控」与「结合且调控」的位点。

5. **跨物种验证策略**：用大鼠 ChIP-seq 验证人类预测的 TF 对，增强了结论的普适性。可迁移到本课题：在物种间保守性分析中，用跨物种 ChIP-seq 数据验证 TF 结合位点的功能保守性。

6. **布尔逻辑描述协同调控**：用 AND/OR 逻辑门形式化描述 TF 对的协同方式，可提供直观的调控逻辑。可迁移到本课题：在构建基因调控网络时，用逻辑门描述 TF 组合的调控规则，可与定量模型互补。

---

## 15 与已有知识连接

- **SCENIC+**（González-Blas et al., 2023）：基于 motif 的 TF 调控网络推断，但仅考虑单 TF-TG 关系。coTF-reg 扩展了 TF-TF 维度。
- **Signac**（Stuart et al., 2021）：单细胞 ATAC-seq 分析工具，提供 peak-gene link 方法，coTF-reg 依赖其类似方法。
- **DeepBind**（Alipanahi et al., 2015）和 **BPNet**（Avsec et al., 2021）：基于深度学习的 TF-DNA 结合预测，但聚焦单 TF 的序列偏好，未涉及 TF 协同。
- **Shapley 值**（Shapley, 1953）和 **SHAP**（Lundberg & Lee, 2017）：可解释 AI 的经典方法，coTF-reg 将其扩展为 interaction 版本。
- **Loregic**（Huang et al., 2020）：布尔逻辑调控推断工具，coTF-reg 用于验证 TF 对的逻辑协同。
- **PsychENCODE**（Wang et al., 2018）：提供脑组织多组学数据资源，coTF-reg 使用其 eQTL 数据。
- **少突胶质细胞 TF 研究**：SOX10（Stolt et al., 2002）、OLIG2（Lu et al., 2000）、NKX2.2（Qi et al., 2001）等已知关键 TF，coTF-reg 的发现与此一致并扩展了新的协同对。

---

## 16 研究想法

### Agent 生成的研究候选

**候选 1：基于序列的 TF 协同结合预测模型**
- **名称**：CoBindNet
- **来源局限/观察**：coTF-reg 依赖 motif 共定位，但 motif 扫描无法捕捉 TF 协同结合的序列语法（如 spacing、orientation、合作性结合导致的亲和力变化）。
- **核心假设**：TF 对在 DNA 上的协同结合具有可学习的序列模式，超越独立 motif 的简单叠加。
- **初步方法**：用 CNN 或 Transformer 架构，输入为调控区 DNA 序列，输出为 TF 对结合概率；训练数据来自 ChIP-seq 共结合位点；用 Shapley interaction 解释序列特征。
- **验证方式**：在独立 ChIP-seq 数据集上评估共结合预测 AUC；用 CRISPR 突变验证预测的关键序列特征。
- **创新状态**：unverified

**候选 2：将 coTF-reg 扩展到 TF 簇（>2 TF）协同**
- **名称**：CoTF-cluster
- **来源局限/观察**：coTF-reg 仅分析两两 TF 对，但真实调控往往涉及多个 TF 的协同复合物。
- **核心假设**：三个及以上 TF 的协同组合可通过对两两交互分数的聚类分析来识别。
- **初步方法**：将 SI 分数矩阵作为输入，用图神经网络或非负矩阵分解识别 TF 模块；用共调控靶基因的富集验证模块功能。
- **验证方式**：与已知蛋白复合物数据库（如 CORUM）比对；用共免疫沉淀验证预测的 TF 复合物。
- **创新状态**：unverified

**候选 3：将 coTF-reg 与物理模拟结合预测 TF 协同结合**
- **名称**：CoTF-MD
- **来源局限/观察**：coTF-reg 是纯数据驱动方法，缺乏对 TF-TF 物理互作机制的考虑；分子动力学（MD）模拟可提供结合自由能信息。
- **核心假设**：数据驱动的协同预测与物理模拟的结合自由能具有一致性，可互相验证。
- **初步方法**：对 coTF-reg 预测的高协同 TF 对，用 MD 模拟或分子对接计算 TF-TF-DNA 三元复合物的结合自由能；比较数据预测与物理模拟结果。
- **验证方式**：在已知协同 TF 对（如 SOX10-OLIG2）上验证方法一致性；用突变体模拟验证关键残基。
- **创新状态**：unverified

**候选 4：跨细胞类型的 TF 协同调控比较**
- **名称**：CoTF-Atlas
- **来源局限/观察**：coTF-reg 仅分析少突胶质细胞，TF 协同是否具有细胞类型特异性尚不清楚。
- **核心假设**：核心 TF 协同模块在不同细胞类型中保守，而细胞类型特异性由辅助 TF 的差异协同决定。
- **初步方法**：将 coTF-reg 应用于多种脑细胞类型（神经元、星形胶质细胞、小胶质细胞）的公开数据；比较 SI 分数矩阵的相似性。
- **验证方式**：用跨细胞类型的 ChIP-seq 数据验证保守的 TF 对；用细胞类型特异性敲除实验验证差异 TF 对。
- **创新状态**：unverified

**候选 5：利用 eQTL 精细定位 TF 协同的因果变异**
- **名称**：CoTF-eQTL
- **来源局限/观察**：coTF-reg 仅将 eQTL 映射到调控区，未利用 eQTL 效应方向来推断 TF 协同的因果性。
- **核心假设**：位于协同 TF 结合位点的 eQTL 变异会同时影响两个 TF 的结合，导致靶基因表达的协同改变。
- **初步方法**：对 coTF-reg 识别的协同 TF 对，筛选位于两个 TF 结合位点重叠区域的 eQTL；用等位基因特异性分析验证变异对 TF 结合的影响。
- **验证方式**：用报告基因实验验证 eQTL 变异对 TF 协同结合的影响；用孟德尔随机化评估因果性。
- **创新状态**：unverified