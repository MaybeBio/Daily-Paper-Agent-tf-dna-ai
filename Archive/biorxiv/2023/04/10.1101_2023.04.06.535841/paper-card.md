## 01 基本信息

- **标题**：Predictions of DNA mechanical properties at a genomic scale reveal potentially new functional roles of DNA-flexibility
- **作者与单位**：Back G; Walther D（Max Planck Society 资助，具体单位未在摘要中提供）
- **期刊/预印本平台**：bioRxiv
- **年份**：2023
- **论文类型**：预印本（方法学 + 基因组规模应用研究）
- **领域**：DNA 力学性质 / 生物信息学 / 深度学习
- **关键词**：DNA flexibility, cyclizability, loop-seq, deep learning, CNN/LSTM, transcription start sites, transcription factor binding, mutation rate
- **DOI/arXiv 号**：10.1101/2023.04.06.535841
- **代码**：https://github.com/georgback/CycPred
- **数据**：loop-seq 数据（Basu et al. 2021）、JASPAR、DAP-seq（O'Malley et al.）、1001 基因组计划、Spo11-oligo-seq（Choi et al.）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「DNA 力学性质（cyclizability）的深度学习预测」方向，与 TF–DNA 结合机制直接相关——其核心问题之一是 DNA 局部柔性是否影响 TF 结合。方法上采用 CNN/LSTM 架构预测 DNA 柔性，属于 AI 方法预测 DNA 力学性质，而非 MD/对接模拟。对 TF–DNA 互作课题的可迁移点在于：提供了「序列 → 力学性质」的端到端预测工具，以及「结合位点 vs 非结合位点柔性比较」的分析范式。

---

## 02 一句话总结

本文开发了深度学习模型 CycPred（CNN/LSTM），基于 loop-seq 实验数据预测 DNA 局部 cyclizability（柔性），并将其应用于多个物种基因组，发现 TSS 附近存在特征性柔性变化（主要由二核苷酸组成驱动）、部分拟南芥转录因子的结合位点具有区别于非结合位点的柔性特征，且刚性区域与突变率、Spo11 双链断裂位点相关。

---

## 03 研究问题

- **具体问题**：DNA 局部力学性质（cyclizability/flexibility）在基因组尺度上如何分布？这些分布是否与转录起始、TF 结合、突变、甲基化、交叉重组等基因组功能特征相关？
- **为什么重要**：DNA 柔性被认为影响核小体定位、TF 结合、突变率等关键生物学过程。但此前缺乏基因组规模的柔性预测工具，且对柔性在 TF 结合中的角色存在争议（特别是 TSS 上游刚性区域假说）。
- **现有方法不足**：实验测量（loop-seq）通量有限，无法覆盖全基因组；已有预测模型（如 DNAcycP）计算成本高，难以用于大规模基因组分析。
- **精确研究问题**：Can a deep learning model trained on loop-seq data accurately predict DNA cyclizability at genomic scale, and can these predictions reveal functionally relevant patterns of DNA flexibility associated with transcription initiation, TF binding, and mutation?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 及引用，属于「经外部核验」的领域发展脉络（本文引用了相关文献）。

| 阶段 | 代表性方法/发现 | 优点 | 局限 |
|------|----------------|------|------|
| 早期力学测量 | 单分子实验（原子力显微镜、光镊等） | 直接测量力学参数 | 通量极低，无法覆盖基因组 |
| 序列-力学关联研究 | 凝胶电泳、环化实验 | 建立序列与柔性的初步关联 | 低通量，序列覆盖有限 |
| 高通量实验 | loop-seq（Basu et al. 2021） | 大规模测量 DNA 环化能力 | 仅覆盖特定物种/序列库 |
| 计算预测 | DNAcycP（Li et al. 2022）、Khan et al. 模型 | 可预测任意序列的 cyclizability | 计算成本高（DNAcycP），可解释性有限 |
| 本文 | CycPred（CNN/LSTM） | 性能与 DNAcycP 相当，计算成本低 60-80 倍 | 依赖 loop-seq 训练数据，跨物种泛化需验证 |

**本文主张的位置**：在已有预测模型基础上，提供更高效的预测工具，并将预测应用于多物种基因组规模分析，探索 DNA 柔性与多种基因组特征（TSS、TF 结合、突变、Spo11）的关联。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 实验测量通量不足 | loop-seq 仅覆盖有限序列库，无法直接获得全基因组柔性图谱 | 实验方法本身通量限制 | Methods 节「Utilized Datasets」 |
| 已有预测模型计算成本高 | DNAcycP 处理时间比 CycPred 多 60-80 倍 | 模型架构复杂（Inception-ResNet + LSTM） | Results 节「The CNN/LSTM model shows similar performance as DNAcycP...」 |
| TSS 上游刚性区域假说缺乏跨物种验证 | 酵母中发现的 TSS 上游刚性区域未在其它物种中系统验证 | 缺乏跨物种预测工具 | Results 节「Pronounced changes of cyclizability around transcription start sites」 |
| TF 结合位点柔性特征不明确 | 同一 motif 的不同实例结合状态不同，柔性是否起区分作用未知 | 此前研究多关注 motif 序列本身，忽略侧翼序列力学性质 | Results 节「A subgroup of Arabidopsis thaliana transcription factors shows distinct DNA rigidity patterns...」 |
| 突变率与 DNA 力学关联缺乏基因组规模证据 | 突变偏好性是否与局部柔性相关 | 缺乏大规模预测数据 | Results 节「De novo mutations and fixed SNPs in Arabidopsis thaliana appear more frequently in rigid genomic DNA contexts」 |

---

## 06 核心思想

### 1) 表面方法
- 训练 CNN/LSTM 深度学习模型（CycPred），以 DNA 序列为输入，预测 loop-seq 实验测得的 cyclizability 值。
- 将训练好的模型应用于多个物种全基因组，计算 TSS 附近、TF 结合位点、突变位点等区域的 cyclizability 分布。
- 通过置换检验/随机化比较，评估实际序列与随机序列的柔性差异。

### 2) 核心洞察
- **二核苷酸组成是柔性的主要决定因素**：单碱基水平随机化会破坏柔性信号，而二核苷酸水平随机化几乎保留原始信号（图 4），说明 DNA 柔性主要由相邻碱基对（二核苷酸步）的堆叠相互作用决定。
- **TSS 柔性特征具有物种特异性**：酵母的 TSS 上游刚性区域并非普遍现象；多数物种（6/8）表现为 TSS 下游柔性降低，且 TSS 本身位置柔性较高。
- **TF 结合位点的柔性特征因 TF 而异**：部分 TF（如 TCX3）偏好刚性结合位点，另一些（如 TRP2）偏好柔性结合位点，说明 DNA 力学性质是 TF 结合特异性的潜在贡献因素。
- **刚性区域与突变/重组相关**：突变（特别是 indel）富集在刚性 DNA 区域，Spo11 双链断裂位点也与刚性区域相关。

### 3) 可能的普适教训 [Analysis]
- **序列 → 力学性质 → 功能的因果链**：本文展示了「序列编码力学性质，力学性质影响功能」的分析框架，可迁移到 TF–DNA 互作研究——即不仅考虑 motif 序列，还应考虑侧翼序列的力学性质对结合的影响。
- **随机化对照是区分「组成效应」与「序列顺序效应」的关键**：通过单碱基 vs 二核苷酸随机化的对比，可以判断柔性信号是来自组成还是顺序，这一实验设计值得借鉴。
- **跨物种比较可避免过度泛化**：酵母中发现的模式未必适用于其它物种，跨物种验证是必要的。

---

## 07 方法总览

- **输入**：DNA 序列（50bp 窗口，来自 loop-seq 训练数据或基因组序列）
- **输出**：预测的 cyclizability 值（连续标量）
- **模型架构**：1D CNN 层 + max pooling + LSTM 层 + dropout + dense 层（图 1）
- **训练**：以 loop-seq 实验数据为标签，MSE 为损失函数；训练/测试集来自 tiling library（70/30 划分）；预测时对正反链分别预测取均值
- **工具**：TensorFlow 2.6（GPU）、KerasTuner 1.04（超参数优化）、DeepLIFT（重要性分数）、TF-MoDISco（motif 发现）
- **下游分析**：
  - TSS 周围 cyclizability 分布（±525bp，1000 个窗口）
  - 随机化对照：单碱基随机化 vs 二核苷酸随机化
  - TF 结合位点 vs 非结合位点比较（拟南芥 DAP-seq + JASPAR motif）
  - 突变位点（de novo / fixed SNP / indel）与 cyclizability 关联
  - Spo11-oligo 信号与 cyclizability 相关
- **反馈回路**：无显式反馈回路（非主动学习/迭代优化）
- **假设**：① loop-seq 测得的 cyclizability 可代表 DNA 内在柔性；② 模型可跨物种泛化（基于 DNA 力学性质普遍性假设）；③ 预测值可作为实验值的可靠替代

**文字流程**：
1. 从 loop-seq 数据中提取 50bp 序列-cyclizability 对
2. 训练 CNN/LSTM 模型（含超参数搜索）
3. 在测试集上验证模型性能（与 DNAcycP 对比）
4. 将模型应用于 8 个物种基因组，计算全基因组 cyclizability
5. 提取 TSS 周围窗口，绘制 cyclizability 分布图
6. 对 TSS 周围序列进行单碱基/二核苷酸随机化，比较预测差异
7. 对拟南芥 TF 结合位点（DAP-seq）进行结合 vs 非结合比较
8. 对突变位点、Spo11 位点进行 cyclizability 关联分析

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CNN 层（1D 卷积 + max pooling） | 提取局部序列模式（k-mer 类特征） | DNA 柔性由局部序列（尤其是二核苷酸步）决定，CNN 可捕获局部模式 | 输入：one-hot 编码的 50bp 序列；输出：特征图 | 模型整体性能与 DNAcycP 相当（r=0.93 随机库） | [预期] 移除后模型无法捕获局部序列-柔性关联，性能显著下降 |
| LSTM 层 | 捕获序列中的长程依赖 | 柔性可能受较远距离序列影响（如弯曲协同性） | 输入：CNN 特征序列；输出：上下文向量 | 模型整体性能 | [预期] 移除后可能影响对长程效应的建模，但短序列（50bp）上影响可能有限 |
| 正反链平均 | 消除链方向偏差 | loop-seq 数据中正反链 cyclizability 存在差异 | 输入：正链和反链预测值；输出：均值 | Methods 节「both the forward and reverse-complement... were predicted and the mean was reported」 | [预期] 移除后预测值可能偏向某一链方向，引入系统偏差 |
| DeepLIFT 重要性分析 | 识别对预测贡献大的序列位置 | 理解模型学到的序列-柔性规则 | 输入：序列 + 模型；输出：每个碱基的重要性分数 | Results 节「For identification of potential motifs identified by the model, we used deeplift」 | [预期] 移除后无法解释模型学到的序列特征 |
| TF-MoDISco | 从重要性分数中提取 motif | 发现影响柔性的序列 motif | 输入：DeepLIFT 分数；输出：motif 共识序列 | Results 节（未发现 motif 超过二核苷酸） | [预期] 移除后无法验证是否存在高阶 motif 效应 |
| 随机化对照（单碱基/二核苷酸） | 区分组成效应与顺序效应 | 判断柔性信号来源 | 输入：实际序列 + 随机化序列；输出：cyclizability 分布对比 | 图 4：单碱基随机化消除信号，二核苷酸随机化保留信号 | [预期] 移除后无法判断柔性是否由二核苷酸组成驱动 |

---

## 09 关键公式符号

本文未提供显式数学公式（如损失函数、注意力机制等），核心方法为深度学习模型。以下为隐含的公式/概念：

1. **Cohen's d 效应量**（Methods 节）：
   \[
   d = \frac{\bar{x}_1 - \bar{x}_2}{s}
   \]
   其中 \(\bar{x}_1, \bar{x}_2\) 为两组均值，\(s\) 为合并标准差。用于量化实际序列与随机化序列的 cyclizability 差异大小。

2. **Pearson 相关系数**（Results 节）：
   \[
   r = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum (x_i - \bar{x})^2 \sum (y_i - \bar{y})^2}}
   \]
   用于评估模型预测值与实验值的一致性（r=0.93 随机库，r=0.77 染色体 V）。

3. **MSE 损失函数**（Methods 节）：
   \[
   \text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
   \]
   用于训练回归模型。

4. **Log2 比值**（Spo11 分析）：
   \[
   \log_2(\text{spo11-oligonucleotides}/\text{gDNA})
   \]
   用于量化 Spo11 信号强度。

---

## 10 实验设计与证据链

### 数据集/群体
- **训练数据**：loop-seq 实验数据（Basu et al. 2021），包括：
  - 随机序列库（12,472 条）
  - 染色体 V tiling library（82,368 条窗口，步长 7bp）
  - 核小体库（19,907 条）
- **测试数据**：随机库和染色体 V 库的 30% 测试集
- **应用基因组**：8 个物种（拟南芥、水稻、烟草、衣藻、酵母、线虫、小鼠、人类），另加鲑鱼、玉米用于特定分析
- **TF 结合数据**：拟南芥 DAP-seq（O'Malley et al.）+ JASPAR motif
- **突变数据**：拟南芥 de novo 突变（Monroe et al.）、固定 SNP（1001 基因组计划）
- **Spo11 数据**：拟南芥 Spo11-oligo-seq（Choi et al.）

### 指标
- 预测性能：Pearson 相关系数（预测 vs 实验 cyclizability）
- 效应量：Cohen's d
- 统计检验：t 检验、Fisher 精确检验

### 评测协议
- 模型在 tiling library 上训练，在随机库和染色体 V 上测试
- 正反链预测取均值
- 随机化对照：对 TSS 周围序列进行单碱基或二核苷酸水平随机化，比较 cyclizability 分布

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 模型性能验证 | CycPred 能准确预测 cyclizability | 预测 vs 实验值，随机库和染色体 V | 随机库 r=0.93，染色体 V r=0.77 | 模型预测准确，可用于基因组规模分析 | 未与 DNAcycP 做正式统计比较（仅中位数距离） | Results 节「The CNN/LSTM model shows similar performance as DNAcycP...」 |
| TSS 周围 cyclizability 分布 | TSS 附近存在特征性柔性变化 | 8 个物种 TSS ±525bp 窗口 | 6/8 物种在 TSS 下游有柔性降低；酵母为上游降低 | TSS 柔性特征具有物种特异性 | 未证明该模式的功能因果性 | Results 节「Pronounced changes of cyclizability around transcription start sites」 |
| 随机化对照 | 二核苷酸组成驱动 TSS 柔性信号 | 单碱基 vs 二核苷酸随机化 | 单碱基随机化消除信号，二核苷酸随机化保留信号 | 柔性主要由二核苷酸组成决定 | 未排除更高阶序列模式的作用 | Results 节「Dinucleotide composition is a driving factor in local DNA-rigidity」 |
| TF 结合位点柔性比较 | 部分 TF 结合位点具有独特柔性特征 | 结合 vs 非结合 motif 实例（拟南芥 25 个 TF） | 7 个 TF 显示明显差异（如 TCX3 刚性、TRP2 柔性） | DNA 柔性是 TF 结合特异性的潜在因素 | 未证明柔性直接导致结合差异（可能为关联） | Results 节「A subgroup of Arabidopsis thaliana transcription factors shows distinct DNA rigidity patterns...」 |
| 突变位点 cyclizability | 突变富集在特定柔性区域 | 含突变 vs 不含突变窗口（拟南芥） | 突变窗口 cyclizability 显著更低（更刚性） | 刚性 DNA 区域更易发生突变 | 未区分突变类型/机制 | Results 节「De novo mutations and fixed SNPs in Arabidopsis thaliana appear more frequently in rigid genomic DNA contexts」 |
| Spo11 位点 cyclizability | Spo11 双链断裂偏好特定柔性 | Spo11 信号与 cyclizability 相关 | 高 Spo11 信号区域 cyclizability 更低（更刚性） | 刚性区域与重组热点相关 | 未证明因果关系 | Results 节「Sites of high Spo11 oligonucleotide accumulation in Arabidopsis thaliana is associated with rigid DNA windows」 |

---

## 11 结论正确解读

- **任务范围**：本文是「预测 + 关联分析」研究，非因果实验。所有结论均为统计关联，不涉及分子机制验证。
- **Oracle/真值输入**：模型以 loop-seq 实验数据为训练标签，loop-seq 测量的是 DNA 环化能力，是柔性的间接指标，非直接力学测量（如弯曲刚度）。
- **端到端状态**：模型是「序列 → cyclizability」的端到端预测，但下游分析（TF 结合、突变）是独立于模型的统计关联，非端到端。
- **算力成本**：未提供具体训练时间/硬件信息，仅提及 CycPred 比 DNAcycP 快 60-80 倍。
- **历史数据依赖**：模型依赖 loop-seq 实验数据（酵母来源），跨物种应用基于「DNA 力学性质普遍性」假设，未做实验验证。
- **模型依赖**：结果依赖 CycPred 的预测准确性；在非酵母物种上无实验验证。
- **最难情形**：TSS 注释准确性（备选 TSS 问题）、TF 结合位点的 DAP-seq 数据噪声、Spo11 数据稀疏性。
- **群体/领域边界**：结论适用于真核生物基因组（8 个物种），不涵盖原核生物；拟南芥分析最深入，其它物种仅 TSS 分布。
- **不确定性**：所有效应量均较小（Cohen's d 0.03-0.3），统计显著性可能受大样本量驱动，生物学意义需谨慎解读。

**有边界的复述**：本文开发了高效的 cyclizability 预测工具，并基于预测值发现：(1) TSS 附近柔性变化具有物种特异性，主要由二核苷酸组成驱动；(2) 部分拟南芥 TF 的结合位点具有区别于非结合位点的柔性特征；(3) 拟南芥中刚性区域与突变率、Spo11 双链断裂位点正相关。这些发现为「DNA 力学性质参与基因组功能调控」提供了计算层面的支持，但因果机制和实验验证尚待开展。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 跨物种泛化未验证 | 模型基于酵母 loop-seq 数据训练，应用于其它物种 | 未明确提及 | Discussion 节「In as much as i) DNA is universally the same polymer...」 |
| 统计关联非因果 | 所有发现均为相关性，不能证明因果关系 | 「experimental evidence is needed to confirm them as association does not imply causation」 | Discussion 节末段 |
| TSS 注释不确定性 | 备选 TSS 可能影响分析 | 「we believe that the fact that we did observe characteristic profiles...suggests that indeed a signal is present」 | Discussion 节末段 |
| 预测模型依赖 | 结果基于预测值而非实验测量 | 未明确提及 | Discussion 节「we developed a computational prediction model, and reported results obtained by applying it」 |
| 效应量较小 | 多数效应量 Cohen's d < 0.3 | 未明确提及 | Results 节各分析 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 跨物种应用未做实验验证 | 模型在非酵母物种上的预测可能不准确；不同物种的 DNA 力学性质可能存在差异（如 GC 含量、修饰） | 所有下游结论（TF 结合、突变）均依赖预测准确性 | 在至少一个非酵母物种（如拟南芥）上做 loop-seq 实验验证 | Methods 节仅提及酵母训练数据 |
| TF 结合分析仅覆盖 25 个 TF | 拟南芥有 >1500 个 TF，样本量有限；且仅用 DAP-seq 数据，未考虑体内染色质环境 | 可能遗漏重要模式或过度泛化 | 扩大 TF 数量，结合 ChIP-seq 数据交叉验证 | Results 节「25 TFs, for which sufficient data was available」 |
| 突变分析未区分突变类型 | SNP 和 indel 的机制不同，可能对 DNA 力学性质有不同的响应 | 混合分析可能掩盖真实关联 | 分别分析 SNP、indel 与 cyclizability 的关系 | Results 节「grouped sequence windows into four classes」 |
| 随机化对照仅检验二核苷酸组成 | 三核苷酸或更高阶模式可能也有贡献，但未检验 | 可能低估序列顺序效应的复杂性 | 进行三核苷酸水平随机化对照 | Results 节仅提及单碱基和二核苷酸随机化 |
| Spo11 分析未控制其他因素 | 重组热点可能与染色质状态、序列 motif 等相关，不一定是力学性质直接作用 | 可能混淆因果关系 | 多变量回归控制已知重组相关因素 | Results 节「Sites of high Spo11 oligonucleotide accumulation...」 |
| 模型可解释性有限 | DeepLIFT 仅识别重要性分数，未揭示具体力学机制（如弯曲角度、扭转刚度） | 限制了对「序列如何编码力学性质」的理解 | 结合分子动力学模拟验证关键 motif 的力学性质 | Results 节「no motif beyond dimers were identified」 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

### 可迁移概念

1. **「序列 → 力学性质 → 功能」分析框架**：本文展示了从序列预测力学性质，再关联功能位点的完整流程。在 TF–DNA 互作研究中，可迁移为「序列 → DNA 形状/柔性 → TF 结合特异性」的预测框架。

2. **二核苷酸组成作为力学性质的主要编码单元**：本文通过随机化对照证明二核苷酸组成是柔性的主要决定因素。在 TF–DNA 互作中，可关注 TF 结合位点侧翼序列的二核苷酸偏好是否影响 DNA 形变能力，从而影响结合亲和力。

3. **随机化对照区分「组成效应」与「顺序效应」**：单碱基 vs 二核苷酸随机化的对比设计，可用于区分 TF 结合位点的柔性信号是来自碱基组成还是特定序列顺序。

4. **结合 vs 非结合位点的柔性比较范式**：本文比较了同一 motif 的结合/非结合实例的 cyclizability，这一范式可直接迁移到 TF–DNA 互作研究——即检验 DNA 柔性是否有助于解释「同一 motif 不同结合状态」的经典问题。

5. **跨物种比较避免过度泛化**：酵母中发现的 TSS 上游刚性区域未在其它物种中重现，提示在 TF–DNA 互作研究中应谨慎跨物种推广结论。

### 可迁移方法

1. **CNN/LSTM 架构用于 DNA 序列力学性质预测**：该架构可迁移到其他 DNA 结构性质预测任务（如 DNA 弯曲度、扭转刚度、小沟宽度等），这些性质均与 TF 结合相关。

2. **DeepLIFT + TF-MoDISco 的序列解释流程**：可用于识别影响 DNA 力学性质的关键序列 motif，进而与 TF 结合 motif 交叉分析。

3. **基因组窗口化 + 随机化置换检验**：适用于大规模基因组关联分析，可迁移到 TF 结合位点全基因组扫描。

### 对 TF–DNA 互作课题的具体启示

- **TF 结合位点设计**：在设计或预测 TF 结合位点时，除 motif 序列外，可加入侧翼序列的 cyclizability 预测值作为特征，可能提高预测精度。
- **解释「同 motif 不同结合」问题**：DNA 柔性可作为「同一 motif 序列在不同基因组位置结合效率不同」的潜在解释变量。
- **突变偏好与 TF 结合**：刚性 DNA 区域突变率更高，可能影响 TF 结合位点的进化稳定性——这一关联值得在 TF 结合位点进化研究中关注。

---

## 15 与已有知识连接

### 可验证的外部连接

1. **Basu et al. (2021)**：loop-seq 原始实验方法，本文训练数据的来源。可验证 loop-seq 实验设计、cyclizability 定义。
2. **Li et al. (2022) DNAcycP**：本文对比的已有预测模型，架构为 Inception-ResNet + LSTM。可对比两者性能与架构差异。
3. **Khan et al. (2022)**：另一独立开发的 cyclizability 预测模型，本文提及并对比。
4. **O'Malley et al. (2016) DAP-seq**：拟南芥 TF 结合数据来源，可验证 TF 结合位点定义。
5. **Monroe et al. (2022)**：拟南芥 de novo 突变数据来源，可验证突变 calling 方法。
6. **Choi et al. (2018) Spo11-oligo-seq**：拟南芥重组热点数据来源。

### 与课题方向的连接

- **TF–DNA 结合机制**：本文发现部分 TF 结合位点具有独特柔性特征，与「DNA 形状读码」（shape readout）假说一致。可连接至 DNA 形状预测工具（如 DNAshape）的相关研究。
- **DNA 力学与蛋白质识别**：本文的 cyclizability 预测可视为「DNA 力学编码」的一种表示，与「间接读码」（indirect readout）概念相关——即蛋白质通过识别 DNA 的可变形性而非直接碱基接触来结合。
- **突变与 TF 结合位点进化**：刚性区域突变率高的发现，与 TF 结合位点的进化保守性研究相关——保守的 TF 结合位点可能位于特定力学性质区域。

### 候选方向（标注为未验证）

- [候选] 将 cyclizability 预测值作为特征加入 TF 结合位点预测模型（如 DeepSEA、Basenji），可能提高预测精度。
- [候选] 结合分子动力学模拟，验证 CycPred 预测的高/低柔性区域是否对应真实的 DNA 弯曲自由度差异。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：TF 结合位点侧翼序列的 cyclizability 作为结合亲和力预测特征

- **名称**：FlankFlex-TF
- **来源局限/观察**：本文发现部分 TF 的结合位点具有区别于非结合位点的柔性特征，但未系统评估侧翼序列柔性的预测能力
- **核心假设**：TF 结合位点侧翼区域的 DNA 柔性（cyclizability）独立于 motif 序列，对结合亲和力有增量预测价值
- **初步方法**：使用 CycPred 预测拟南芥所有 TF 结合位点 ±50bp 的 cyclizability 谱，与 ChIP-seq/DAP-seq 信号强度回归，控制 motif 序列后检验柔性特征的增量贡献
- **验证方式**：交叉验证 AUC 提升；在独立数据集（如 ENCODE TF 数据）上验证泛化性
- **创新状态**：unverified

### 候选 2：DNA 柔性介导的 TF 结合「同 motif 不同结合」机制研究

- **名称**：FlexDecode
- **来源局限/观察**：本文比较了结合/非结合 motif 实例的 cyclizability，但未深入机制
- **核心假设**：同一 TF 的 motif 在不同基因组位置的结合效率差异，部分由局部 DNA 柔性决定，且该效应在「弱 motif」上更强（柔性补偿序列特异性）
- **初步方法**：对拟南芥 25 个 TF 的结合/非结合位点，计算 cyclizability 与 motif 匹配分数的交互项，检验柔性是否在弱 motif 位点起补偿作用
- **验证方式**：统计交互效应显著性；选择预测为「刚性但强 motif」和「柔性但弱 motif」的位点进行体外结合实验（EMSA）
- **创新状态**：unverified

### 候选 3：跨物种 TF 结合位点的 cyclizability 保守性分析

- **名称**：ConservedFlex
- **来源局限/观察**：本文发现 TSS 柔性模式具有物种特异性，但未分析 TF 结合位点的柔性保守性
- **核心假设**：直系同源 TF 的结合位点在不同物种中可能序列不保守，但 cyclizability 谱保守（力学性质的功能约束）
- **初步方法**：对拟南芥、水稻、衣藻的直系同源 TF，比较其结合位点区域的 cyclizability 分布；使用 CycPred 预测，计算种间相关性
- **验证方式**：置换检验评估保守性显著性；与序列保守性对比，检验力学保守是否独立于序列保守
- **创新状态**：unverified

### 候选 4：CycPred 预测与分子动力学模拟的交叉验证

- **名称**：MD-CycVal
- **来源局限/观察**：CycPred 基于 loop-seq 间接测量，缺乏直接力学验证
- **核心假设**：CycPred 预测的高/低 cyclizability 区域对应 MD 模拟中不同的弯曲自由能
- **初步方法**：选取拟南芥 TSS 附近高/低 cyclizability 的 50bp 片段各 20 条，进行 MD 模拟（如使用 GROMACS + parmBSC1 力场），计算弯曲持久长度与自由能，与 CycPred 预测值比较
- **验证方式**：Pearson 相关性；若相关性低，分析系统偏差来源（如 loop-seq 与 MD 测量尺度差异）
- **创新状态**：unverified

### 候选 5：DNA 柔性作为 TF 结合位点 SNP 致病性预测的附加特征

- **名称**：FlexVar
- **来源局限/观察**：本文发现刚性区域突变率更高，但未连接至功能变异解读
- **核心假设**：位于刚性 DNA 区域的 TF 结合位点 SNP 更可能破坏结合（刚性区域对突变更敏感）
- **初步方法**：使用拟南芥 1001 基因组 SNP 数据，将 SNP 按所在区域 cyclizability 分层，比较各层 SNP 对 TF 结合影响的预测效应（结合 DAP-seq 数据）
- **验证方式**：分层分析效应量差异；在人类 ENCODE 数据上验证（使用 CycPred 预测人类基因组）
- **创新状态**：unverified