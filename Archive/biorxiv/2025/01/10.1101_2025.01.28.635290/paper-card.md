## 01 基本信息

- **标题**：ShapeME: A tool and web front-end for de novo discovery of structural motifs underpinning protein-DNA interactions
- **作者与单位**：Jeremy W. Schroeder; Michael B. Wolfe; Lydia Freddolino（美国密歇根大学医学院，Freddolino 实验室）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2025
- **论文类型**：方法学/工具论文
- **领域**：生物信息学；蛋白质-DNA 互作；转录因子结合位点预测；DNA 结构基序发现
- **关键词**：DNA shape motifs, de novo motif discovery, transcription factor binding, DNAshapeR, mutual information, LASSO regression, ChIP-seq, SELEX
- **DOI/arXiv 号**：10.1101/2025.01.28.635290
- **代码**：https://github.com/freddolino-lab/ShapeME
- **数据**：ENCODE ChIP-seq 数据（29 个人类转录因子）、E. coli H-NS ChIP-seq 数据、JUND 敲低 RNA-seq 数据（均为公开数据，具体 accession 见原文 Table 2/3）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦于**转录因子（TF）–DNA 结合机制**的结构层面，提出了一种不依赖序列基序（PWM）锚定的**从头（de novo）DNA 结构基序发现**方法。它将 DNAshapeR 的结构预测与信息论（互信息）结合，可处理多种数据类型（ChIP-seq、RNA-seq、SELEX 等），是该课题方向中「结构基序发现 × 信息论/机器学习」的代表性工具，与基于序列的 STREME 形成互补。

---

## 02 一句话总结

本文开发了 ShapeME——一个将 DNAshapeR 预测的 DNA 结构特征（EP、HelT、MGW、ProT、Roll）与信息论（AMI/CAMI）及 LASSO 回归相结合的从头结构基序发现工具，在 29 个人类 TF 的 ENCODE ChIP-seq 数据中，结构基序在 11/29 例中优于序列基序，且结构+序列混合模型在 15/29 例中优于任一单独模态。

---

## 03 研究问题

- **具体问题**：如何在不依赖已知序列基序（如 PWM）锚定的情况下，从多种类型的实验数据（ChIP-seq、RNA-seq、SELEX 等）中从头发现具有解释力的 DNA 结构基序（structural motifs）？
- **为什么重要**：许多 DNA 结合蛋白（特别是结构特异性的转录因子）的 DNA 结合偏好不能仅由序列基序解释，DNA 的局部结构特征（如小沟宽度、螺旋扭转等）是决定结合特异性的关键因素。现有工具要么依赖序列基序锚定（如 DNAShape 的 anchored 方法），要么仅适用于单一数据类型，缺乏通用性。
- **精确的 Can 问题**：Can a unified, data-type-agnostic de novo structural motif discovery framework identify short DNA shape motifs that outperform sequence-based motifs (PWM/STREME) in predicting TF–DNA binding across diverse experimental datasets?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 的叙述，标注为「仅本文框架」；未逐一核对外部文献。

1. **PWM 时代**：传统上使用 Position Weight Matrix（PWM）描述 TF 的 DNA 结合偏好，假设每个碱基位置独立且加性贡献。局限：忽略碱基间相互作用和 DNA 结构特征。
2. **高阶序列模型**：考虑相邻碱基相互作用的生物物理模型（如 dinucleotide 模型）提高了预测精度，但仍停留在序列空间。
3. **DNA 结构特征的引入**：DNAshapeR 等工具通过全原子蒙特卡洛模拟从序列预测 DNA 结构参数（小沟宽度 MGW、螺旋扭转 HelT、螺旋桨扭转 ProT、滚动 Roll、静电势 EP），使结构信息可用于结合预测。
4. **结构+序列的锚定方法**：已有工作将 DNA shape 特征围绕核心 PWM 基序计算（anchored approach），提高了 ChIP-seq 峰预测精度，但会遗漏不依赖 PWM 的 shape 模式。
5. **从头结构基序发现**：少数工具（如基于 ChIP-seq 或 SELEX 的 shape motif 发现）存在数据类型局限，无法处理多种实验设计。
6. **本文位置**：ShapeME 是第一个统一的、数据类型无关的从头结构基序发现框架，将信息论（AMI/CAMI）与 DNAshapeR 结合，并原生整合序列基序（STREME）与结构基序的联合建模。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PWM 无法捕捉结构决定因素 | 某些 TF 的 DNA 结合偏好无法用独立碱基模型解释 | PWM 假设碱基独立且加性，忽略 DNA 局部结构（如 MGW、HelT）对结合的贡献 | Introduction 第 1-2 段 |
| 现有 shape motif 工具数据类型受限 | 已有工具仅适用于 ChIP-seq 或 SELEX 单一数据类型 | 缺乏统一框架处理二值、多类别、连续等不同输入格式 | Introduction 第 3 段；Results 中 ShapeME 可处理二值/多类别/连续数据 |
| 锚定方法遗漏非 PWM 相关 shape 模式 | anchored approach 围绕已知 PWM 计算 shape，无法发现独立于序列基序的结构模式 | 结构模式可能存在于 PWM 覆盖区域之外或与序列基序无对应关系 | Introduction 第 3 段 |
| 结构基序与序列基序的冗余 | 多个候选基序可能提供重复信息 | 需要信息论准则（CAMI）和 LASSO 回归进行非冗余筛选 | Methods "Pruning of motifs based on CAMI" 节 |
| 现有工具缺乏交叉验证框架 | 无法评估结构基序在独立数据上的泛化能力 | 缺少统一的交叉验证和性能评估流程 | Methods "Assessment of motif model performance" 节 |

---

## 06 核心思想

1. **表面方法**：ShapeME 是一个三阶段流程——(1) 用 DNAshapeR 将输入序列转换为 5 个结构参数（EP、HelT、MGW、ProT、Roll）的 z-score 矩阵；(2) 用信息论（AMI）筛选与输入标签（二值/多类别/连续）具有互信息的种子基序，并用条件调整互信息（CAMI）剪枝冗余；(3) 用模拟退火优化基序参数，LASSO 回归做最终模型选择。可选集成 STREME 序列基序。

2. **核心洞察**：DNA 序列空间与结构空间的拓扑不同——序列上相近的 DNA 片段在结构上可能差异很大，反之亦然（Fig. 1B-C）。这意味着仅靠序列基序无法捕捉结构层面的结合决定因素。ShapeME 的核心创新在于**不依赖序列基序锚定**，直接从结构参数空间搜索具有解释力的短基序，并允许结构基序与序列基序在统一框架下竞争或互补。

3. **可能的普适教训** [Analysis]：对于 TF–DNA 互作研究，**特征空间的选择（序列 vs. 结构）本身就是一种先验假设**。ShapeME 的成功表明，当序列基序表现不佳时，切换到结构特征空间可能揭示新的结合决定因素。此外，**信息论准则（AMI/CAMI）提供了一种与模型无关的特征筛选方式**，可迁移到其他生物序列特征发现任务中。

---

## 07 方法总览

- **输入**：
  - Score 文件：TSV 格式，含 "name" 和 "score" 两列；score 可为二值、多类别或连续值（连续值自动分位数离散化）
  - Sequence 文件：FASTA 格式，每条序列长度一致，至少为 k+4（k 为结构基序长度）
- **输出**：
  - 结构基序（含每个位置的 shape 参数 z-score 均值和权重）
  - 可选：序列基序（STREME 输出）
  - 基序富集热图、交叉验证性能曲线（AUPR）
- **核心模块**：
  1. **DNAshapeR 转换**：序列 → 5 个结构参数（EP, HelT, MGW, ProT, Roll）的 z-score 矩阵
  2. **种子筛选**：滑动窗口扫描，计算每个窗口的 AMI 与输入标签的关联，保留高 AMI 种子
  3. **CAMI 剪枝**：去除与已有种子冗余的候选
  4. **模拟退火优化**：迭代调整基序的 shape 参数和阈值，最大化 AMI
  5. **LASSO 回归**：最终模型选择，去除贡献为零的基序
  6. **交叉验证**：5 折交叉验证，计算 AUPR
- **训练/推理**：无传统"训练"过程；基序发现基于信息论准则，LASSO 回归用于模型选择
- **工具/依赖**：DNAshapeR、STREME（可选）、R（glmnet, PRROC）、Python、Apptainer 容器
- **反馈回路**：模拟退火中 AMI 作为目标函数，迭代更新基序参数；LASSO 回归后若基序被移除，则重新评估剩余基序
- **文字流程**：输入序列 → DNAshapeR 计算结构参数 → 滑动窗口扫描种子 → AMI 排序 → CAMI 剪枝 → 模拟退火优化 → LASSO 模型选择 → 5 折交叉验证 → 输出最终基序集和性能报告

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| DNAshapeR 结构参数计算 | 将 DNA 序列转换为 5 个结构参数（EP, HelT, MGW, ProT, Roll）的 z-score | 提供序列无法直接编码的结构信息 | 输入：FASTA 序列；输出：shape 矩阵 | Methods "Produce input shape array A" 节；引用 DNAshapeR 原始文献 | 预期影响：ShapeME 退化为纯序列工具，失去结构基序发现能力 [预期效应] |
| 种子筛选（AMI 扫描） | 滑动窗口扫描，计算每个窗口与标签的 AMI | 从海量候选窗口中筛选信息量高的种子 | 输入：shape 矩阵 + 标签；输出：候选种子列表 | Methods "Screen batches of S in A for informative seeds" 节 | 预期影响：无此模块则无法初始化基序搜索 [预期效应] |
| CAMI 剪枝 | 去除与已有种子冗余的候选 | 避免输出大量高度相似的基序 | 输入：候选种子列表；输出：非冗余种子集 | Methods "Pruning of motifs based on CAMI" 节；公式 4 | 预期影响：基序集冗余度增加，模型解释性下降 [预期效应] |
| 模拟退火优化 | 迭代优化基序的 shape 参数和阈值 | 种子是离散窗口，需连续优化以匹配真实基序 | 输入：种子 + shape 矩阵；输出：优化后的基序 | Methods "Shape motif optimization" 节；公式 11-14 | 预期影响：基序质量下降，AUPR 降低 [预期效应] |
| LASSO 回归模型选择 | 从候选基序集中选择预测标签的最小子集 | 去除冗余和无关基序，提高泛化性 | 输入：所有基序的 hit 向量 + 标签；输出：最终基序集 | Methods "Model selection with LASSO regression" 节 | 预期影响：模型复杂度增加，过拟合风险上升 [预期效应] |
| STREME 序列基序集成 | 可选地发现序列基序并与结构基序联合建模 | 序列和结构信息可能互补 | 输入：正集序列；输出：序列基序 | Methods "Application of information theory..." 节；Results 中 "both" 模式 | 预期影响：无法利用序列-结构互补性 [预期效应] |
| 5 折交叉验证 | 评估基序模型的泛化性能 | 避免过拟合，提供可靠的性能估计 | 输入：基序集 + 数据；输出：AUPR | Methods "Assessment of motif model performance" 节 | 预期影响：无法评估模型泛化能力 [预期效应] |

---

## 09 关键公式符号

1. **调整互信息（AMI）**（公式 2，引用 Vinh et al. 32）：
   - AMI(U, V) = [MI(U, V) − EMI(U, V)] / [max(H(U), H(V)) − EMI(U, V)]
   - 其中 MI 为互信息，H 为信息熵，EMI 为期望互信息（随机排列下的期望值）
   - 用途：衡量基序 hit 向量与输入标签之间的关联强度，校正随机性

2. **条件调整互信息（CAMI）**（公式 4）：
   - CAMI(C | D) = [MI(C; Y | D) − EMI(C; Y | D)] / [max(H(C | D), H(Y | D)) − EMI(C; Y | D)]
   - 其中 D 为已有基序的 hit 向量，C 为候选基序的 hit 向量，Y 为标签
   - 用途：判断候选基序在已知基序条件下是否仍提供额外信息

3. **信息准则 IC_m**（公式 5-6）：
   - IC_m = −2·L_m + k·d
   - 其中 L_m 为基序 m 的对数似然（基于最小 CAMI），d 为基序参数数量，k 为惩罚系数
   - 用途：平衡基序的信息贡献与模型复杂度，决定是否保留基序

4. **加权曼哈顿距离**（公式 7）：
   - d(x, y) = Σᵢ wᵢ |xᵢ − yᵢ|
   - 其中 wᵢ 为位置 i 的权重，xᵢ 和 yᵢ 为 shape 参数值
   - 用途：衡量查询序列与基序之间的结构相似度，低于阈值视为"hit"

5. **模拟退火接受概率**（公式 11-14）：
   - p(a) = exp(−ΔAMI / T)
   - 其中 T 为温度参数，随迭代次数衰减
   - 用途：允许一定概率接受劣化更新，避免局部最优

---

## 10 实验设计与证据链

**数据集与设置**：
- **合成数据**：随机生成 3000 条 60 nt 序列，20% 标记为正类，嵌入已知目标序列；用于验证基序发现准确性
- **多类别合成数据**：3000 条序列，5 个类别，每类含不同目标基序
- **连续值合成数据**：模拟连续 score 与基序存在性的关系
- **ENCODE ChIP-seq**：29 个人类转录因子，峰序列 60 bp，负集为随机基因组位点（3 倍于正集），5 折交叉验证
- **E. coli H3N 数据**：H-NS ChIP-seq，4 个生长阶段（EE/ME/TS/S），100 bp 和 300 bp 窗口
- **JUND 敲低 RNA-seq**：CRISPRi 敲低 vs 对照，增强子序列 100 bp，score 为 shrunken log2(fold-change)

**指标**：AUPR（精确率-召回率曲线下面积）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| 合成数据单基序 | ShapeME 能恢复已知目标基序 | 单基序嵌入，二值标签 | AUPR = 0.999 | 高精度恢复已知基序 | 未测试多基序复杂场景 | Results 图 2A |
| 合成数据多类别 | ShapeME 能处理多类别标签 | 5 类，每类不同基序 | 最低 AUPR = 0.96 | 多类别场景有效 | 未与真实多类别生物数据对比 | Results 图 2C |
| 合成数据连续值 | ShapeME 能处理连续 score | 连续值，5 类/10 类 | 性能随数据量增加而提升 | 连续数据可用 | 未与回归方法对比 | Results 图 2D |
| 序列收敛到相似 shape | ShapeME 能识别序列不同但 shape 相似的基序 | 两条序列编辑距离为 5，shape 距离最小 | shape 模式被识别 | shape 空间与序列空间互补 | 未验证生物学意义 | Results 图 2E-F |
| ENCODE 29 TF | shape 基序与序列基序的性能对比 | ShapeME shape-only vs STREME vs both vs JASPAR | 11/29 shape 优于序列；15/29 both 优于任一单独 | shape 信息对部分 TF 至关重要 | 未覆盖所有 TF 家族 | Results 图 4、Supp. 图 2 |
| H-NS ChIP-seq | shape 基序能解释 H-NS 结合偏好 | 4 个生长阶段，100/300 bp | shape 基序富集于高结合区域，含高 roll 特征 | H-NS 结合与 DNA 结构特征相关 | 未做突变验证 | Results 图 3 |
| JUND 敲低 RNA-seq | shape 基序能发现间接调控信号 | 增强子序列 vs 敲低后表达变化 | 发现潜在 SP5 基序 | 可发现间接调控关系 | 未实验验证 SP5 结合 | Results 图 6 |
| ShapeME vs ShapeMotifEM | ShapeME 优于现有工具 | 95 百分位峰 vs 全峰 | ShapeME 在多数情况下 AUPR 更高 | 优于现有方法 | 未测试所有数据集 | Results 图 5 |

---

## 11 结论正确解读

- **任务范围**：本文的任务是**从头发现短 DNA 结构基序**（5-10 bp 窗口），用于预测 TF 结合位点（分类任务）或解释结合偏好。它**不是**端到端的 TF 结合位点预测器，而是基序发现工具。
- **Oracle/真值输入**：合成数据中目标基序已知；ENCODE 数据中"正集"为 ChIP-seq 峰（实验确定的结合区域），"负集"为随机基因组位点——这是标准做法，但负集可能包含未检测到的真实结合位点。
- **端到端状态**：ShapeME 是**基序发现 + 预测模型**的完整流程，但预测性能（AUPR）是在特定数据集上评估的，不能直接推广到所有 TF 或细胞类型。
- **算力成本**：模拟退火 20,000 次迭代/基序，计算成本中等；DNAshapeR 预测为一次性预处理。
- **历史数据依赖**：依赖 DNAshapeR 的结构预测模型（基于蒙特卡洛模拟），该模型本身有误差；不依赖训练数据。
- **模型依赖**：LASSO 回归选择基序子集，结果可能受正则化参数影响。
- **最难情形**：序列基序与结构基序高度相关时，难以区分各自贡献；低质量 ChIP-seq 数据（峰少、噪声大）可能降低基序发现能力。
- **群体/领域边界**：测试集中于人类 TF 和 E. coli H-NS，未覆盖所有物种和 TF 家族；RNA-seq 分析仅针对 JUND 一个案例。
- **不确定性**：作者未报告基序发现的置信区间或统计显著性检验；交叉验证 AUPR 的方差未报告。
- **有边界的复述**：ShapeME 能在多种数据类型（二值/多类别/连续）中从头发现 DNA 结构基序，在 29 个人类 TF 的 ChIP-seq 数据中，结构基序在约 38% 的案例中优于序列基序，混合模型在约 52% 的案例中优于任一单独模态；但这一性能依赖于 DNAshapeR 的结构预测准确性，且未在所有 TF 家族中验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 依赖单一结构预测模型 | 仅使用 DNAshapeR 从序列预测结构，忽略细胞状态（如超螺旋、染色质环境）对 DNA 结构的影响 | 未来工作可纳入细胞状态对 DNA 结构的影响 | Discussion 第 3 段 |
| 无法工程化改造 shape 基序 | 与序列基序不同，shape 基序难以直接设计突变实验验证 | 需要开发工具将 shape 基序映射回序列上下文 | Discussion 第 4 段 |
| 缺乏 shape 基序比较工具 | 没有类似 TomTom 的 shape 基序数据库比对工具 | 开发 ShapeMotif 数据库和比对工具 | Discussion 第 4 段；Results 中 ShapeIT 仅用于实例搜索 |
| 结构预测的固有误差 | DNAshapeR 预测的 shape 参数可能与真实 DNA 结构有偏差 | 可结合分子动力学模拟或实验结构数据验证 | Discussion 第 3 段（隐含） |
| 未测试所有数据类型 | 连续值数据仅用合成数据验证，未在真实连续生物学数据（如 ChIP-seq 峰强度）上测试 | 未来可在更多真实连续数据上验证 | Results 图 2D 上下文 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 合成数据中 AUPR 接近 1.0 | 合成数据过于简单（单基序、无噪声），可能高估真实性能 | 真实 ChIP-seq 数据中基序信号弱、背景噪声大 | 在更复杂的合成数据（多基序、可变基序位置、噪声标签）上测试 | Results 图 2A |
| 29 个 TF 中仅 11 个 shape 优于序列 | 可能反映的是 DNAshapeR 预测误差而非 shape 信息的真实贡献 | 若结构预测更准确，shape 基序可能表现更好 | 使用实验测定的 DNA 结构数据（如 NMR、X-ray）验证 | Results 图 4 |
| "both" 模式在 15/29 中优于单独模态 | 未报告"both"模式是否显著优于最佳单独模态（统计检验缺失） | 需要统计显著性来判断混合模型的真实增益 | 对 AUPR 差异进行配对检验（如 Wilcoxon） | Results 图 4 |
| 负集为随机基因组位点 | 随机位点可能包含未检测到的真实结合位点，导致 AUPR 被低估 | 负集质量直接影响性能评估 | 使用 ChIP-seq 输入 DNA 作为负集，或使用已知非结合位点 | Methods "ShapeME analysis of ENCODE data" 节 |
| 基序长度固定为 k | 真实 TF 结合位点长度可变，固定 k 可能遗漏重要模式 | 基序长度是超参数，影响发现能力 | 测试不同 k 值，或使用多尺度扫描 | Methods 中 k 为参数 |
| 未与深度学习基线比较 | 未与 CNN/DNN 等基于序列的深度模型比较 | 无法判断 shape 基序相对 SOTA 序列模型的增益 | 在相同数据集上运行 DeepBind、DeepSEA 等模型 | Results 中仅与 STREME/JASPAR 比较 |
| ShapeMotifEM 比较中仅用 95 百分位峰 | 高置信峰可能偏向强结合位点，弱结合位点上的性能未知 | 弱结合位点可能更依赖结构特征 | 在不同百分位阈值下比较 | Methods "ShapeMotifEM" 节 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **结构基序发现可脱离序列基序锚定**：ShapeME 证明，直接从结构参数空间（而非围绕 PWM 计算 shape）搜索基序，可以发现序列基序无法捕捉的结合决定因素。**可迁移到 TF–DNA 课题**：当目标 TF 的 PWM 不明确或结合位点高度退化时，可尝试纯结构基序发现。

2. **信息论准则（AMI/CAMI）是模型无关的特征筛选工具**：AMI 衡量基序与标签的关联，CAMI 处理基序间冗余，无需训练标签的分布假设。**可迁移**：在构建 TF 结合预测模型时，可用 AMI/CAMI 作为特征预筛选步骤，减少维度。

3. **结构-序列混合建模优于单一模态**：在 15/29 案例中，"both" 模式优于任一单独模态，说明序列和结构信息互补。**可迁移**：设计 TF–DNA 结合预测模型时，应同时输入序列 one-hot 编码和 DNAshapeR 结构特征，而非仅用其一。

4. **结构基序的可解释性**：ShapeME 输出的 shape motif 包含每个位置的 shape 参数 z-score 和权重，可直接解释为"该位置需要窄小沟"或"该位置需要高螺旋扭转"。**可迁移**：在 AI 模型中引入结构特征可提高可解释性，帮助理解 TF 结合的物理机制。

5. **数据类型的灵活性**：ShapeME 支持二值（峰 vs 非峰）、多类别（多个细胞类型/条件）和连续（峰强度、表达变化）标签。**可迁移**：在 TF–DNA 课题中，可利用连续 ChIP-seq 峰强度或 RNA-seq 表达变化作为标签，而非仅用二值分类。

6. **结构基序的保守性分析**：ShapeME 在 JUND 敲低 RNA-seq 数据中发现的基序与 SP5 ChIP-seq 基序相似，提示结构基序可能跨 TF 家族保守。**可迁移**：可系统比较不同 TF 的结构基序，探索结构层面的 TF 家族分类。

---

## 15 与已有知识连接

- **DNAshapeR（Zhou et al., 2013）**：ShapeME 直接依赖 DNAshapeR 从序列预测 5 个结构参数。DNAshapeR 本身基于 Monte Carlo 模拟的 pentamer 结构数据库，其预测精度直接影响 ShapeME 的基序质量。**连接**：若 DNAshapeR 对某类序列（如甲基化 DNA）预测不准，ShapeME 结果需谨慎解读。

- **FIRE（Elemento et al., 2007）**：ShapeME 的 AMI 方法明确受 FIRE 算法启发。FIRE 是序列基序发现工具，用互信息筛选与表达谱相关的基序。**连接**：ShapeME 将 FIRE 的思想从序列空间扩展到结构空间。

- **STREME（Bailey, 2021）**：ShapeME 集成 STREME 作为序列基序发现组件。STREME 是 MEME Suite 中的高效基序发现工具。**连接**：ShapeME 的 "both" 模式将 STREME 输出与结构基序统一纳入 LASSO 回归。

- **ShapeMotifEM（Yang et al., 2022）**：ShapeME 直接与 ShapeMotifEM 对比，后者是现有的从头 shape motif 发现工具。**连接**：ShapeME 在 29 个 TF 数据上优于 ShapeMotifEM，且更稳定（ShapeMotifEM 在 41% 案例中崩溃）。

- **ENCODE 项目（ENCODE Project Consortium, 2012）**：ShapeME 使用 ENCODE 的 ChIP-seq 数据（29 个 TF）和 JUND 敲低 RNA-seq 数据。**连接**：ENCODE 数据是 TF–DNA 互作研究的标准基准。

- **TF–DNA 结合的结构决定因素（Rohs et al., 2009）**：本文的生物学动机——DNA 小沟宽度、螺旋扭转等结构特征决定 TF 结合特异性——源于 Rohs 等人的经典工作。**连接**：ShapeME 为这一理论提供了计算工具支持。

- **候选方向 [Analysis]**：ShapeME 的结构基序可进一步与 AlphaFold3 或 RoseTTAFoldNA 等结构预测工具结合，预测 TF–DNA 复合物的三维结构，验证结构基序的物理意义。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

1. **候选名称**：TF–DNA 结构基序跨物种保守性分析
   - **来源局限/观察**：ShapeME 仅在人类 TF 和 E. coli H-NS 上验证，未测试跨物种保守性。
   - **核心假设**：DNA 结构基序（如窄小沟、高螺旋扭转）在进化上比序列基序更保守，因为结构约束更直接反映物理结合机制。
   - **初步方法**：对多个物种（酵母、果蝇、小鼠、人类）的同源 TF 运行 ShapeME，比较结构基序的相似性；用 ShapeIT 在跨物种基因组中搜索基序实例。
   - **验证方式**：计算结构基序的跨物种富集分数，与序列基序保守性对比。
   - **创新状态**：unverified

2. **候选名称**：结构基序引导的 TF–DNA 复合物结构预测
   - **来源局限/观察**：ShapeME 输出的是 1D 结构基序，未与 3D 结构预测结合。
   - **核心假设**：将 ShapeME 发现的结构基序作为约束输入 AlphaFold3 或 MD 模拟，可提高 TF–DNA 复合物结构预测的准确性。
   - **初步方法**：对 ShapeME 基序高置信的 TF 运行 AlphaFold3，比较有无结构基序约束下的预测精度；用 MD 模拟验证基序区域的构象稳定性。
   - **验证方式**：与实验测定的 TF–DNA 复合物结构（PDB）对比 RMSD。
   - **创新状态**：unverified

3. **候选名称**：基于结构基序的合成 TF 结合位点设计
   - **来源局限/观察**：ShapeME 的基序难以直接工程化改造（作者自认局限）。
   - **核心假设**：给定目标结构基序，可反向设计 DNA 序列，使其在结构空间中匹配基序，从而设计合成 TF 结合位点。
   - **初步方法**：将 ShapeME 基序作为目标，用遗传算法或梯度优化在序列空间中搜索结构匹配的 DNA 序列；用 DNAshapeR 验证结构匹配度。
   - **验证方式**：体外实验（EMSA、SELEX）验证设计序列的 TF 结合亲和力。
   - **创新状态**：unverified

4. **候选名称**：结构基序与表观遗传修饰的互作
   - **来源局限/观察**：ShapeME 仅使用未修饰 DNA 的结构预测，未考虑甲基化等修饰对 DNA 结构的影响。
   - **核心假设**：CpG 甲基化通过改变 DNA 结构（如 MGW）影响 TF 结合，且这种影响可通过结构基序差异捕捉。
   - **初步方法**：对甲基化和未甲基化序列分别运行 DNAshapeR，比较结构基序差异；用 ShapeME 在甲基化 ChIP-seq 数据上发现基序。
   - **验证方式**：与甲基化敏感的 TF 结合实验数据对比。
   - **创新状态**：unverified

5. **候选名称**：结构基序与 TF 协同结合的预测
   - **来源局限/观察**：ShapeME 处理单个 TF 的结合数据，未考虑多个 TF 协同结合时的结构约束。
   - **核心假设**：协同结合的 TF 对在 DNA 上形成组合结构基序，且该基序可预测协同结合位点。
   - **初步方法**：对共结合 ChIP-seq 数据（如 ChIA-PET、HiChIP）运行 ShapeME，搜索双 TF 组合结构基序。
   - **验证方式**：与已知协同结合位点对比，或进行突变验证。
   - **创新状态**：unverified