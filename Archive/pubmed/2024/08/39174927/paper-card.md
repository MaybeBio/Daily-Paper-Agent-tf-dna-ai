## 01 基本信息

- **标题**：TIANA: transcription factors cooperativity inference analysis with neural attention
- **作者与单位**：Li, Rick Z; Han, Claudia Z; Glass, Christopher K（单位未在摘要中提供，推测为加州大学圣迭戈分校，未提供）
- **期刊/预印本平台**：BMC Bioinformatics
- **年份**：2024
- **论文类型**：方法学（Method）论文，提出新计算工具
- **领域**：计算生物学 / 生物信息学；转录因子（TF）协同性推断；深度学习可解释性
- **关键词**：转录因子协同性、神经注意力、可解释深度学习、顺式调控元件、整合梯度
- **DOI/arXiv 号**：10.1186/s12859-024-05852-0
- **代码**：https://github.com/rzzli/TIANA
- **数据**：使用公开数据（GSE109965、GSE111856、ENCODE 等），具体数据清单见正文
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」交叉方向，聚焦于从远端调控序列（增强子/开放染色质）中推断 TF 之间的协同结合关系。与物理模拟（MD/对接）无直接关联，但属于 AI 方法用于解析 TF 协同结合规则的代表性工作，其「已知 motif 初始化卷积核 + 注意力归因」的思路可迁移至 TF–DNA 结合特异性和协同性的建模。

---

## 02 一句话总结

本文提出 TIANA，一个用已知 TF motif 初始化卷积核、结合 multi-head attention 和 integrated gradients 的深度学习框架，从 ATAC-seq/ChIP-seq 峰序列中推断显著共现的 TF motif 对，并在模拟数据、已知协同结合 TF 对（GATA1-TAL1、ETS1-RUNX1、SOX2-OCT4）及巨噬细胞增强子数据上验证了其识别 TF 协同性的能力。

---

## 03 研究问题

- **具体问题**：如何从远端调控元件（增强子、开放染色质区域）的 DNA 序列中，推断哪些转录因子（TF）之间存在协同结合（cooperativity）关系？
- **为什么重要**：TF 协同结合是增强子调控特异性的核心机制。远端调控序列中 motif 的共现模式蕴含细胞类型特异性的调控程序，但 TF 之间的协同关系是非线性、多重叠加的，传统 motif 富集工具（如 HOMER、MEME）只能处理单个 motif 的过表达，无法捕捉 motif 之间的依赖关系。
- **现有方法不足**：
  - 传统工具（HOMER、MEME）只关注单个 motif 的富集，无法推断 TF 对之间的协同性。
  - 已有的深度学习方法（如 SATORI）虽然使用 attention，但其卷积层从头学习 motif，导致卷积核与已知 motif 的对应关系模糊，注释困难，且 attention score 的可解释性有限。
  - 需要一种既能保持深度学习分类性能、又能直接关联已知 motif 并量化 TF 对协同显著性的方法。
- **精确研究问题（Can...?）**：Can a deep learning model with preloaded known motif filters and integrated gradients-based attention attribution infer statistically significant TF cooperativity pairs from distal regulatory sequences?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，部分外部引用未逐一核验，标注为「仅本文框架」或「经外部核验」。

1. **传统 motif 富集阶段**（HOMER、MEME 等）
   - 方法：在调控序列中统计单个 motif 的过表达。
   - 优点：简单、可解释、广泛使用。
   - 局限：无法捕捉 motif 之间的协同/排斥关系；对 motif 间距、方向等约束不敏感。
   - 来源：本文 Background 节提及，属「经外部核验」的领域共识。

2. **深度学习序列模型阶段**（DeepSEA 等）
   - 方法：用 CNN 从序列中学习调控特征，预测染色质状态。
   - 优点：分类性能强，能捕捉序列中的复杂模式。
   - 局限：卷积核是「学习到的」模式，与已知 motif 的对应关系模糊，难以注释；不直接输出 TF 对关系。
   - 来源：本文 Results 图 2 对比，属「经外部核验」。

3. **注意力机制阶段**（SATORI）
   - 方法：CNN + multi-head attention，用 attention score 推断 TF 对关系。
   - 优点：能捕捉长程依赖，输出 TF 对级别的注意力。
   - 局限：卷积核从头学习，注释困难；attention score 本身可解释性有限，易产生虚假关联。
   - 来源：本文 Background 及 Results 表 1 对比，属「经外部核验」。

4. **TIANA 的定位**（本文）
   - 方法：用已知 motif PSSM 初始化卷积核并固定，训练分类器；用 integrated gradients 计算 attention 归因，替代原始 attention score。
   - 优点：卷积核直接对应已知 motif，无需注释；integrated gradients 比 attention score 更可靠；在少量数据下仍保持性能。
   - 局限：依赖已知 motif 库的覆盖度；无法发现全新 motif。
   - 来源：本文核心贡献，属「仅本文框架」。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 卷积核注释困难 | 深度学习模型（如 DeepSEA、SATORI）学习到的卷积核与已知 motif 的对应关系模糊，难以解释模型学到了什么 | 卷积核从头学习，没有先验约束；motif 长度不一，固定卷积核大小难以匹配 | Discussion 节：「annotating filters to motifs has been frequently reported as a challenge」 |
| attention score 可解释性有限 | SATORI 的 attention score 易产生虚假关联，无法可靠反映 TF 对协同性 | NLP 研究表明 attention score 本身可解释性有限；attention 可能关注非功能性的序列模式 | Background 节引用 [11, 12] |
| 卷积核大小与 motif 长度不匹配 | 固定卷积核大小（如 5–20 bp）无法同时覆盖短 motif（如 TAL1 半 E-box 3–4 bp）和长 motif（如 CTCF 19 bp） | 领域内对卷积核大小无共识；不同 TF 的 motif 长度差异大 | Discussion 节：「TF motifs are naturally very different in size」 |
| 数据量不足时性能下降 | SATORI 和 DeepSEA 在仅用 25% 训练数据时性能显著下降 | 从头学习 motif 需要大量数据；预加载 motif 可减少需要学习的参数 | Results 图 2B |
| 无法区分高度相似的 motif | REL/p65 与 NFκB/p50 的 motif 高度相似，传统富集工具无法区分其不同功能 | motif 序列相似度高，传统方法仅基于序列匹配，缺乏功能上下文 | Results 图 5 及 Discussion 节 |

---

## 06 核心思想

### 1) 表面方法
- 用已知 TF motif PSSM 初始化一维卷积核并固定（不训练），对输入序列（200 bp，one-hot 编码）做卷积，得到每个位置的 motif 激活分数。
- 在卷积层后接 multi-head attention（4 头），让模型学习 motif 之间的依赖关系。
- 用 integrated gradients 对 attention score 矩阵计算归因，得到「attention attribution」矩阵，作为 TF 对协同性的度量。
- 对每个 motif 对，比较正序列（峰序列）与负序列（随机基因组序列）的 attention attribution 分布，用 Mann-Whitney U 检验判断显著性。

### 2) 核心洞察
- **已知 motif 先验**：将卷积核固定为已知 motif PSSM，避免了「学习到的卷积核难以注释」的问题，使模型的中间表示直接对应生物学上有意义的单元（motif）。
- **Integrated gradients 优于 attention score**：直接使用 attention score 作为重要性度量在 NLP 中已被证明不可靠；integrated gradients 通过计算梯度路径积分，能更忠实地反映输入特征对输出的贡献，从而减少虚假关联。
- **正负序列对比**：通过对比正序列（真实峰）与负序列（随机基因组）的 attention attribution，可以过滤掉基因组背景中普遍存在的 motif 共现，只保留与功能相关的协同关系。

### 3) 可能的普适教训 [Analysis]
- **先验注入是深度学习方法在生物学中可解释性的关键**：与其让模型从头学习一切，不如将已知的生物学知识（如 motif 数据库）作为硬约束注入模型架构，这既提高了可解释性，也减少了数据需求。
- **归因方法的选择比模型架构更重要**：在注意力模型中，attention score 本身不是可靠的重要性度量；使用梯度类归因方法（如 integrated gradients）可以显著提升解释质量。
- **正负样本对比是推断生物学显著性的通用策略**：在基因组序列分析中，随机基因组序列作为负对照，可以有效区分「功能相关」与「背景共现」的 motif 对。

---

## 07 方法总览

- **输入**：200 bp DNA 序列（one-hot 编码），来自 ATAC-seq/ChIP-seq 峰；负序列为随机基因组序列。
- **输出**：显著共现的 TF motif 对列表，附带 p 值、attention attribution 水平、motif 间距统计。
- **模块**：
  1. 卷积层（固定为已知 motif PSSM，448 个滤波器 = 224 个 motif × 正反链）
  2. 垂直 max-pooling（pool size 2）
  3. 批归一化
  4. 水平 max-pooling（pool size 4）
  5. Multi-head attention（4 头）
  6. Flatten + 全连接层（256、64 单元）+ sigmoid 输出（二分类）
- **训练**：二分类任务（正序列 vs 负序列），50 epochs，TensorFlow 2.9.1 实现。
- **解释**：训练完成后，用 integrated gradients 计算 attention score 矩阵的归因，得到 attention attribution 矩阵；对每个 motif 对，比较正/负序列的 attribution 分布，用 Mann-Whitney U 检验 + Bonferroni 校正。
- **反馈回路**：无显式反馈回路；训练和解释是两阶段流程。
- **文字流程**：输入峰序列 → 固定 motif 卷积核扫描 → 得到 motif 激活图 → 位置编码 → multi-head attention 建模 motif 间依赖 → 分类器判断峰/非峰 → 训练完成后，用 integrated gradients 对 attention 归因 → 提取 motif 对 attribution → 统计检验 → 输出显著协同 TF 对。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 固定 motif 卷积层 | 用已知 PSSM 扫描序列，得到每个位置的 motif 激活分数 | 将模型中间表示直接对应已知 motif，避免注释困难；减少需学习的参数 | 输入：one-hot 序列 (200×4)；输出：motif 激活图 (200×448) | Results 图 2B：25% 数据下性能下降小于 SATORI/DeepSEA | 预期影响：模型需从头学习 motif，注释困难，数据需求增加 [预期效应，未做消融] |
| Multi-head attention | 建模序列位置间的长程依赖，捕捉 motif 间的协同关系 | 协同结合往往涉及间距较远的 motif，CNN 感受野有限 | 输入：位置编码后的 motif 激活图；输出：attention score 矩阵 (4 头) | Results 表 1：TIANA 在 GATA1-TAL1 上识别出 68% 的峰含 7–9 bp 间距 motif 对 | 预期影响：无法捕捉长程 motif 依赖，协同性推断能力下降 [预期效应，未做消融] |
| Integrated gradients 归因 | 计算 attention score 对输出的梯度积分，得到 attention attribution | attention score 本身可解释性有限，需要更可靠的归因方法 | 输入：attention score 矩阵；输出：attention attribution 矩阵 | Results 图 3：TIANA 在已知协同 TF 对上 attribution 显著高于 SATORI 的 attention score | 预期影响：若用原始 attention score，可能产生更多虚假协同对 [预期效应，未做消融] |
| 正负序列对比 + 统计检验 | 对每个 motif 对，比较正/负序列的 attribution 分布，用 Mann-Whitney U 检验判断显著性 | 过滤基因组背景中普遍存在的 motif 共现，保留功能相关的协同 | 输入：正/负序列的 attribution 值；输出：显著 motif 对列表 | Results 图 5：TIANA 区分了 p65-p50 异源二聚体与 p50-p50 同源二聚体的不同功能 | 预期影响：无统计检验则无法区分背景共现与功能协同 [预期效应，未做消融] |

---

## 09 关键公式符号

1. **Multi-head attention score**：
   \[
   \text{Attention}(S_h) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)
   \]
   - \( Q \)：Query 矩阵
   - \( K \)：Key 矩阵
   - \( d_k \)：Key 的维度
   - \( S_h \)：第 \( h \) 个 attention head 的 score 矩阵，维度 \( \mathbb{R}^{m \times m} \)，\( m \) 为序列长度

2. **Integrated gradients attention attribution**：
   \[
   G = \frac{S}{a} \odot \sum_{k=1}^{a} \frac{\partial F\left(\frac{k}{a}S\right)}{\partial S}
   \]
   - \( G \)：integrated gradients attention attribution 矩阵，维度 \( \mathbb{R}^{m \times m} \)
   - \( S \)：attention score 矩阵
   - \( a \)：Riemann 近似的步数，默认 100
   - \( F \)：TIANA 的分类函数
   - \( \odot \)：逐元素乘法

3. **位置编码**（正弦/余弦函数，来自 Transformer 原论文 [17]）：
   \[
   P_{i,2j} = \sin\left(\frac{i}{n^{2j/f}}\right), \quad P_{i,2j+1} = \cos\left(\frac{i}{n^{2j/f}}\right)
   \]
   - \( i \)：序列位置
   - \( j \)：特征维度索引
   - \( f \)：特征总数
   - \( n \)：标量因子，默认 10,000
   - 输出：\( X_{\text{output}} = X_{\text{input}} + P \)

---

## 10 实验设计与证据链

**数据集与规模**：
- KLA 激活的 BMDM 增强子（ATAC-seq + H3K27ac ChIP-seq，GSE109965）
- LDTF ChIP-seq：ATF3、SPI1（PU.1）、CEBPB（GSE111856 和 GSE109965）
- GATA1-TAL1 共结合峰（K562 细胞，来源未明确标注）
- ETS1-RUNX1 共结合峰（ENCODE：ENCSR588AKU、ENCSR000BKQ）
- SOX2-OCT4 共结合峰（GSE103980）
- 模拟数据：40,000 条序列，嵌入 3 对 motif（SPI1-SIX1、SPI1-CEBPE、RXRA-NRF1），重复 5 次

**指标**：
- 分类性能：AUC（ROC 曲线）
- 协同性推断：p 值（Mann-Whitney U 检验 + Bonferroni 校正）、attention attribution 水平、motif 间距统计

**基线/对比方法**：
- SATORI（MHA 模型，从头学习卷积核）
- DeepSEA（CNN 模型）

**评测协议**：
- 分类：训练/测试按染色体划分（chr1、8、18 为测试集）
- 协同性：模拟数据中检验能否恢复嵌入的 motif 对；真实数据中与已知文献结果对比

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|-------------|-------------------|------|
| 分类性能（全数据） | TIANA 能达到与 SATORI/DeepSEA 相当的分类性能 | 三种模型在 KLA 增强子和 EGR1_ETV5 峰上比较 AUC | 三者 AUC 均 > 0.9 | TIANA 的固定 motif 卷积不影响分类性能 | 未提供精确 AUC 数值 | Results 图 2A |
| 分类性能（25% 数据） | TIANA 在数据量少时更鲁棒 | 随机下采样至 25% 训练数据，重复 5 次 | SATORI 和 DeepSEA 性能下降更大 | 预加载 motif 减少了对数据量的需求 | 未提供精确下降幅度 | Results 图 2B |
| 模拟数据恢复 | TIANA 能恢复嵌入的 motif 对 | 3 对 motif 嵌入 40,000 条序列，重复 5 次 | 所有嵌入 motif 对 p 值接近零，分类准确率接近 100% | TIANA 能准确识别已知协同 motif 对 | 模拟数据未考虑真实序列的复杂性 | Results 及 Supplementary Table 4 |
| GATA1-TAL1 共结合峰 | TIANA 能识别已知协同 TF 对 | 与 SATORI 对比，检查 7–9 bp 间距的 motif 对 | TIANA 识别出 68% 的峰含 7–9 bp 间距 motif 对，SATORI 仅 8% | TIANA 的固定 motif 卷积 + integrated gradients 显著优于 SATORI 的 attention score | 未提供 SATORI 的 p 值对比 | Results 表 1、图 3A |
| 松弛间距 TF 对 | TIANA 能识别松弛间距的协同 TF 对 | 6 对已知松弛间距 TF 对（如 ETS1-RUNX1、SOX2-OCT4） | TIANA 的 attention attribution 显著高于 SATORI | TIANA 能识别非固定间距的协同关系 | 未提供具体 p 值 | Results 图 3B |
| LDTF ChIP-seq | TIANA 能识别谱系决定因子的协同关系 | ATF3、CEBPB、SPI1 三个 LDTF 的 ChIP-seq 峰 | 结果与已知文献一致（如 SPI1 依赖 Ets motif，CEBPB 与 MEF2C 相关） | TIANA 能发现生物学上合理的 TF 协同关系 | 未与随机背景对比 | Results 图 4 |
| KLA 激活/抑制增强子 | TIANA 能区分 NF-κB 亚基的不同功能 | 比较 p65-p50 异源二聚体与 p50-p50 同源二聚体的 attention | 激活增强子中 p65-p50 显著，抑制增强子中 p50-p50 显著 | TIANA 能识别功能上不同的 TF 复合物 | 未与 ChIP-seq 验证对比 | Results 图 5 |

---

## 11 结论正确解读

- **任务范围**：TIANA 的任务是从峰序列（增强子/开放染色质/TF 结合位点）中推断 TF motif 对的协同共现，而非预测 TF 结合的物理机制或三维结构。它不涉及蛋白质构象、DNA 弯曲等物理化学细节。
- **oracle/真值输入**：模型使用了已知 motif 数据库（JASPAR）作为先验，这既是优势（可解释性）也是限制（无法发现新 motif）。「真值」是文献中已知的 TF 协同关系，而非实验验证的物理结合。
- **端到端状态**：TIANA 是端到端可训练的，但解释阶段（integrated gradients）是训练后的独立步骤，不是端到端的一部分。
- **算力成本**：模型规模较小（单卷积层 + 单 MHA 层 + 2 个全连接层），训练 50 epochs，算力需求低，适合普通 GPU。
- **历史数据依赖**：依赖 JASPAR motif 数据库的覆盖度和质量；不同物种、不同细胞类型的 motif 数据库可能不完整。
- **模型依赖**：结果依赖 attention head 数量（4 头）、卷积核固定策略、integrated gradients 的步数（100）等超参数；未做敏感性分析。
- **最难情形**：短 motif（如 TAL1 半 E-box 3–4 bp）容易被背景噪声淹没；高度相似的 motif 家族（如 REL/p65 与 NF-κB/p50）难以区分；松弛间距的 motif 对需要 attention 覆盖较远距离。
- **群体/领域边界**：验证集中在巨噬细胞（KLA 刺激）和 K562 细胞系；未在多种细胞类型或体内数据上系统验证。方法依赖峰序列输入，不适用于无峰定义的调控元件。
- **不确定性**：p 值基于 Mann-Whitney U 检验，但未报告效应量或置信区间；模拟数据与真实数据的差距未量化。

**有边界的复述**：TIANA 在峰序列数据上，通过固定已知 motif 卷积核 + integrated gradients 归因，能够以较高的分类性能（AUC > 0.9）和优于 SATORI 的注意力归因质量，识别出文献已知的 TF 协同结合对（如 GATA1-TAL1、ETS1-RUNX1、SOX2-OCT4），并能区分 NF-κB 亚基在激活/抑制增强子中的不同功能；但其发现范围受限于已知 motif 数据库，且未在多种细胞类型上系统验证。

---

## 12 作者自认局限

在提供的摘要和正文中，作者明确承认的局限如下：

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 固定 motif 卷积限制新 motif 发现 | 卷积核固定为已知 motif，无法学习未知的 DNA 结合模式 | 未明确提及 | Discussion 节（「may limit the kind of DNA patterns that can be learned」） |
| 依赖已知 motif 数据库 | 结果受 JASPAR 数据库覆盖度限制 | 未明确提及 | Discussion 节（隐含） |
| 未在多种细胞类型上系统验证 | 验证集中在巨噬细胞和 K562 细胞 | 未明确提及 | 未提供 |

> 注：作者在 Discussion 中承认「known motif approach may limit the kind of DNA patterns that can be learned」，但未将其作为正式局限列出，也未提出具体未来方向。其余局限（如泛化性、数据库依赖）在摘要中未明确承认。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| GATA1-TAL1 对比中 TIANA 与 SATORI 的 p 值差异巨大（0.06 vs 3.5e−26），但峰百分比差异也大（68% vs 8%） | 两者可能使用了不同的 motif 匹配阈值或峰集；p 值差异可能源于统计检验方法不同而非模型优劣 | 直接对比不公平，结论「TIANA 优于 SATORI」可能被夸大 | 统一 motif 匹配阈值、峰集和统计检验后重新对比 | Results 表 1 |
| 模拟数据中嵌入的 motif 对是「已知答案」，但真实数据中缺乏独立验证 | 模拟数据过于理想化，真实序列的 motif 共现可能受染色质状态、DNA 甲基化等影响 | 模拟数据不能证明真实场景下的有效性 | 使用独立 ChIP-seq 数据集或 CRISPR 验证预测的 TF 对 | Results 及 Supplementary Table 4 |
| Integrated gradients 的计算依赖分类器的梯度，但分类器可能学到非生物学的捷径 | 模型可能通过序列组成（如 GC 含量）而非 motif 共现来分类，导致归因反映的是混淆因素 | 归因结果可能不可靠 | 对输入序列做置换检验或使用对抗样本测试归因稳定性 | 未提供 |
| 未报告 attention attribution 的方差或置信区间 | 单次训练的归因可能不稳定 | 结果可重复性存疑 | 多次随机初始化训练，报告归因的分布 | 未提供 |
| 与 SATORI 的对比仅在一个数据集（GATA1-TAL1）上进行了详细比较 | 样本量小，结论泛化性不足 | 需要更多数据集上的系统对比 | 在多个 TF 对和细胞类型上重复对比 | Results 表 1、图 3 |
| 固定 motif 卷积核虽然提高可解释性，但可能丢失 motif 变体信息 | JASPAR 中的 PSSM 可能无法覆盖所有天然存在的 motif 变体 | 可能漏掉重要的 TF 结合位点 | 对比固定 motif 与可学习卷积核在未知 motif 上的表现 | Discussion 节（作者承认此限制） |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **已知先验注入深度学习的可解释性策略**：将 JASPAR motif PSSM 作为固定卷积核，使模型的中间表示直接对应生物学上有意义的单元。这一策略可迁移到 TF–DNA 结合机制研究中：例如，在预测 TF 结合位点的模型中，用已知 motif 初始化卷积核，避免「黑盒」卷积核的注释难题。
2. **Integrated gradients 替代 attention score 作为重要性度量**：直接使用 attention score 作为特征重要性在 NLP 中已被证明不可靠；integrated gradients 通过路径积分提供更忠实的归因。这一思路可迁移到任何使用 attention 机制的 TF–DNA 结合模型，用于识别关键序列位置或 motif 对。
3. **正负序列对比推断功能相关性**：通过对比真实峰序列与随机基因组序列的归因分布，过滤背景共现，保留功能相关的 motif 对。这一策略可迁移到 TF 结合位点预测中，用于区分「结合」与「非特异性结合」的序列特征。
4. **固定 motif 卷积 + attention 的架构组合**：先用已知 motif 扫描序列得到激活图，再用 attention 建模 motif 间的长程依赖。这一「先局部匹配、再全局整合」的架构可迁移到 TF–DNA 协同结合建模中，尤其适合处理间距可变的 motif 对。
5. **统计检验与深度学习的结合**：用 Mann-Whitney U 检验比较正负序列的归因分布，而非仅依赖模型输出的注意力分数。这一「模型生成特征 + 统计检验验证」的流程可迁移到任何深度学习驱动的调控元件分析中。

---

## 15 与已有知识连接

- **与 SATORI 的关系**：TIANA 是 SATORI 的直接改进，核心差异在于（1）固定已知 motif 卷积核 vs 从头学习卷积核；（2）integrated gradients 归因 vs 原始 attention score。SATORI 的局限（卷积核注释困难、attention 可解释性差）正是 TIANA 的出发点。
- **与 DeepSEA 的关系**：DeepSEA 是纯 CNN 模型，TIANA 在分类性能上与其相当，但增加了可解释性。DeepSEA 的「多任务预测染色质状态」思路与 TIANA 的「单任务二分类」不同，可考虑将 TIANA 扩展为多任务框架。
- **与 HOMER/MEME 的关系**：传统 motif 富集工具只能处理单个 motif，TIANA 通过 attention 建模 motif 对关系，是对传统工具的补充而非替代。
- **与 TF 协同结合实验文献的关系**：GATA1-TAL1（7–9 bp 间距）、ETS1-RUNX1、SOX2-OCT4 均为实验验证的协同 TF 对，TIANA 在这些数据集上的验证为方法提供了生物学可信度。
- **与 MAGGIE 的关系**：MAGGIE 利用进化保守性推断 TF 协同性，需要多物种数据；TIANA 仅需单物种序列数据，两者可互补。
- **可迁移的外部方向**：
  - 将 TIANA 的「固定 motif 卷积 + integrated gradients」思路迁移到 TF 结合特异性预测（如预测 SNP 对 TF 结合的影响）。
  - 将 attention attribution 作为特征，与三维结构预测（如 AlphaFold 3）结合，研究 TF 协同结合的构象基础。
  - 将正负序列对比策略迁移到增强子-启动子互作预测中。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：TIANA-3D：将 attention attribution 与三维结构预测结合，解析 TF 协同结合的构象基础
- **来源局限/观察**：TIANA 从序列层面推断 TF 协同性，但无法解释协同结合的物理机制（如蛋白-蛋白互作界面、DNA 弯曲）。
- **核心假设**：序列层面的 attention attribution 高的 TF 对，其蛋白产物在三维空间中更可能形成稳定的协同结合复合物。
- **初步方法**：对 TIANA 识别的高置信 TF 对，用 AlphaFold 3 或 MD 模拟预测 TF-TF-DNA 三元复合物结构，比较协同与非协同 TF 对的结合自由能。
- **验证方式**：与已知晶体结构（如 GATA1-TAL1 复合物）对比，或使用突变实验验证预测的互作界面。
- **创新状态**：unverified

### 候选 2：TIANA-SNP：用 attention attribution 预测 SNP 对 TF 协同结合的破坏效应
- **来源局限/观察**：TIANA 的固定 motif 卷积对序列变异敏感，但未测试 SNP 对协同性的影响。
- **核心假设**：位于高 attention attribution 区域的 SNP 更可能破坏 TF 协同结合，从而影响增强子功能。
- **初步方法**：对 eQTL/GWAS 位点做 TIANA 分析，比较风险等位基因与参考等位基因的 attention attribution 差异。
- **验证方式**：与实验验证的 allele-specific TF 结合数据（如 ChIP-seq 中的 allele imbalance）对比。
- **创新状态**：unverified

### 候选 3：TIANA-ATAC：从 ATAC-seq 足迹推断 TF 协同性的时序动态
- **来源局限/观察**：TIANA 使用静态峰序列，未利用染色质可及性的动态变化。
- **核心假设**：在细胞激活过程中，协同 TF 对的 attention attribution 会随时间协同变化，反映增强子激活的时序逻辑。
- **初步方法**：对 KLA 刺激时间序列的 ATAC-seq 数据运行 TIANA，追踪 attention attribution 的动态变化。
- **验证方式**：与 TF 表达时序数据对比，或使用 CRISPR 干扰验证预测的时序协同 TF 对。
- **创新状态**：unverified

### 候选 4：TIANA-Motif：扩展固定 motif 卷积为「部分可学习」以发现新 motif 变体
- **来源局限/观察**：TIANA 固定卷积核为已知 motif，无法发现新 motif 或变体。
- **核心假设**：在固定 motif 初始化后允许卷积核微调，可以保留可解释性的同时发现新的 DNA 结合模式。
- **初步方法**：在 TIANA 基础上增加「微调模式」，训练后对比微调前后卷积核的差异，提取新发现的 motif 模式。
- **验证方式**：用 SELEX 或 HT-SELEX 数据验证新发现的 motif 是否具有体外结合活性。
- **创新状态**：unverified

### 候选 5：TIANA-Enhancer：从增强子序列推断细胞类型特异的 TF 协同网络
- **来源局限/观察**：TIANA 在巨噬细胞和 K562 上验证，但未系统比较多种细胞类型。
- **核心假设**：不同细胞类型的增强子中，高 attention attribution 的 TF 对网络不同，反映细胞类型特异的调控逻辑。
- **初步方法**：对多种细胞类型的 ATAC-seq/H3K27ac 数据运行 TIANA，构建细胞类型特异的 TF 协同网络，比较网络拓扑差异。
- **验证方式**：与已知的细胞类型特异 master regulator 对比，或使用 CRISPR 干扰验证网络中的关键节点。
- **创新状态**：unverified