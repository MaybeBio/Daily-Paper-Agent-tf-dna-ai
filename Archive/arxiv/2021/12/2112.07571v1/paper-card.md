## 01 基本信息

- **标题**：Epigenomic language models powered by Cerebras
- **作者**：Meredith V. Trotter; Cuong Q. Nguyen; Stephen Young; Rob T. Woodruff; Kim M. Branson
- **单位**：未提供（推测为 Cerebras Systems 相关团队）
- **期刊/平台**：arXiv 预印本
- **年份**：2021
- **论文类型**：预印本（方法学 + 应用验证）
- **领域**：基因组学 × 自然语言处理（Transformer） × 表观遗传学
- **关键词**：epigenomics, language model, BERT, transcription factor binding, transfer learning, Cerebras
- **DOI/arXiv 号**：arXiv:2112.07571v1
- **代码**：未提供（提及 DNABERT 仓库 https://github.com/jerryji1993/DNABERT 作为参考）
- **数据**：IDEAS36 数据集（127 细胞类型）、ENCODE-DREAM TF 结合基准、hg19 参考基因组、DNase-seq 与 mappability 数据（来自 FactorNet 仓库）
- **阅读日期**：未提供
- **在本课题方向中的位置**：该文是「DNA 语言模型 × TF–DNA 结合预测」方向的代表性工作，首次将表观遗传状态（IDEAS）作为与 DNA 序列平行的输入模态纳入 BERT 预训练，并系统比较了有无表观输入、有无辅助特征对 TF 结合预测的影响。其核心贡献在于证明了「序列 + 表观状态」联合建模优于纯序列模型，且预训练带来的增益在表观信息缺失时更为显著。

---

## 02 一句话总结

该文提出 EBERT——一个以 DNA 序列和 IDEAS 表观遗传状态为双输入的 BERT 模型，通过大规模预训练（127 个细胞类型的全基因组数据）和下游微调，在 ENCODE-DREAM TF 结合预测基准上达到第 3 名，证明了表观遗传信息加入预训练阶段可显著提升细胞类型特异性 TF 结合预测性能。

---

## 03 研究问题

**具体问题**：DNA 序列本身不足以解释细胞类型特异性的 TF 结合模式，因为结合还受染色质可及性、组蛋白修饰等表观遗传状态调控。该文问：能否将表观遗传状态作为语言模型的输入模态，与 DNA 序列联合建模，从而学习到更具细胞类型特异性的基因组表征？

**为什么重要**：TF 结合是基因调控的核心事件，其预测对理解发育、疾病机制至关重要。纯序列模型（如 DNABERT）忽略了细胞类型间的表观差异，无法解释同一序列在不同细胞类型中结合不同的现象。

**现有方法不足**：
- DNABERT 等纯序列模型无法利用表观信息；
- ENCODE-DREAM 竞赛的顶级方案（如 Quang 2019; Keilwagen 2019; Li 2019）虽使用 DNase-seq 等辅助特征，但均为任务特化模型，缺乏可迁移的预训练表征；
- 表观遗传数据（如 IDEAS 状态）虽已被证明包含调控信息，但从未被纳入语言模型的预训练阶段。

**精确研究问题**：Can a Transformer language model pre-trained on paired DNA sequence and epigenetic state inputs learn representations that improve cell type-specific TF binding prediction over sequence-only models?

---

## 04 背景与发展脉络

*注：以下脉络基于本文框架及引用文献，部分经外部核验。*

| 阶段 | 代表方法 | 优点 | 局限 | 本文位置 |
|------|----------|------|------|----------|
| 序列基序匹配 | PWM、位置权重矩阵 | 简单、可解释 | 无法捕捉长程依赖与协同结合 | 基础 |
| 卷积/循环网络 | DeepBind、DeepSEA | 可学习局部序列特征 | 缺乏长程上下文，需大量标注数据 | 前驱 |
| Transformer 语言模型 | DNABERT (Ji 2021)、Levy 2021 | 自监督预训练，捕捉长程依赖 | 仅用序列，忽略表观状态 | 直接前驱 |
| 表观增强的监督模型 | ENCODE-DREAM 顶级方案（DNase-seq 等） | 任务性能高 | 任务特化，无预训练表征 | 竞争基线 |
| **本文** | **EBERT（序列 + IDEAS 双输入 BERT）** | **预训练阶段即纳入表观状态，可迁移至多种下游任务** | **依赖 IDEAS 推断数据，非直接测量** | **本文位置** |

**本文主张的位置**：首次将「表观遗传状态」作为语言模型的第二输入模态，在预训练阶段即学习序列与表观状态的联合分布，从而在下游任务中同时获得序列与表观信息。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 纯序列模型无法区分细胞类型 | DNABERT 等模型在 TF 结合预测中无法解释同一序列在不同细胞类型中的差异结合 | 序列信息在细胞类型间不变，缺乏表观状态输入 | Introduction 节："DNA sequence alone may contain insufficient information to model many important genomic processes" |
| 表观数据未纳入预训练 | 现有语言模型仅用序列预训练，表观信息仅在微调阶段以辅助特征形式加入 | 缺乏将表观状态与序列联合建模的框架 | Introduction 节：现有工作仅用序列（Ji 2021; Levy 2021） |
| 大规模预训练计算成本高 | 全基因组 × 127 细胞类型的数据规模在 GPU 上训练需数周 | 标准 GPU 硬件无法高效处理该规模 | Introduction 节："Using standard GPU hardware, training a model with a large capacity appropriate to the dataset would have taken weeks or months" |
| IDEAS 状态与序列的粒度不匹配 | IDEAS 为 200bp 分辨率，DNA token 为 k-mer 粒度 | 需要设计 pooling 策略将表观状态对齐到 token 级别 | Methods 2.1 节：IDEAS k-mer 基于最频繁状态进行 pooling |
| 微调阶段辅助特征与预训练表征的融合方式不明确 | 直接拼接或仅用辅助特征均非最优 | 需要系统比较不同融合策略 | Results 3.2-3.4 节：比较 DBERT、EBERT、EBERT+ 三种设置 |

---

## 06 核心思想

### 1) 表面方法
构建一个 BERT 架构的 Transformer 模型，输入为 DNA 序列的 k-mer token 序列和对应的 IDEAS 表观遗传状态 token 序列。两者分别经过独立的 embedding 层后相加，再送入标准 BERT encoder。预训练目标为联合掩码语言建模（同时预测被掩码的 DNA token 和 IDEAS token）。微调阶段，在 BERT 输出之上堆叠卷积层和全连接层，用于 TF 结合二分类预测。

### 2) 核心洞察
**表观遗传状态是细胞类型特异性的「上下文」**。DNA 序列在细胞类型间不变，但 IDEAS 状态编码了染色质可及性、组蛋白修饰等细胞类型特异性信息。将 IDEAS 作为与序列平行的输入模态，使模型在预训练阶段即学习「序列-表观状态」的联合分布，从而在下游任务中无需额外表观特征即可获得细胞类型特异性。

### 3) 可能的普适教训 [Analysis]
- **多模态预训练优于单模态 + 微调时拼接**：本文表明，在预训练阶段即纳入表观信息（EBERT）比仅在微调阶段添加辅助特征（DBERT+aux）更有效，因为预训练让模型学会了表观状态与序列的交互模式。
- **推断数据可作为预训练信号**：IDEAS 状态本身是推断结果而非直接测量，但作为预训练目标仍然有效，说明「弱标签」在自监督预训练中具有价值。
- **计算硬件是模型规模的瓶颈**：Cerebras CS-1 的 wafer-scale 架构使大规模预训练成为可能，提示硬件创新与算法创新同样重要。

---

## 07 方法总览

**输入**：
- DNA 序列：1,000 bp 片段，来自 hg19 参考基因组
- IDEAS 状态：与 DNA 片段对应的 200bp 分辨率表观遗传状态（36 种状态之一）

**输出**：
- 预训练：被掩码位置的 DNA token 和 IDEAS token 的预测分布
- 微调：每个 200bp bin 的 TF 结合概率（二分类）

**模块**：
1. Tokenization：DNA 序列按 k-mer（k=7, stride=7）切分为 150 个 token；IDEAS 状态按相同窗口 pooling（取窗口内最频繁状态）
2. Embedding：DNA token 和 IDEAS token 分别经过独立的 embedding 层
3. BERT Encoder：RoBERTa 风格，12 层 × 12 头 × 768 维（BASE 配置）
4. 微调头：2 层 1D 卷积 + 2 层全连接分类器

**训练**：
- 预训练：掩码语言模型目标，联合预测 DNA 和 IDEAS token，损失为两者加权和（α=0.5）
- 微调：TF 结合二分类，使用 ENCODE-DREAM 数据集，10:1 负正样本比

**工具**：TensorFlow 2.0（Estimator API），Cerebras CS-1 系统（预训练），16 GPU（微调）

**反馈回路**：无显式反馈回路；预训练-微调为单向流程。

**假设**：
- IDEAS 状态在 200bp 窗口内可视为均匀（pooling 策略的合理性）
- 序列与表观状态的联合分布包含下游任务所需信息

**文字流程**：
1. 从参考基因组提取 1,000bp DNA 片段，并从 IDEAS36 数据集获取对应位置的 36 状态标注
2. 将 DNA 序列切分为 7-mer token，IDEAS 状态按窗口 pooling 为对应 token
3. 分别 embedding 后相加，送入 BERT encoder
4. 预训练：随机掩码 15% 位置，联合预测 DNA 和 IDEAS token
5. 微调：取 BERT 输出序列，经卷积和全连接层，预测每个 200bp bin 是否被 TF 结合

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| DNA k-mer Tokenization | 将 1,000bp 序列转为 150 个 7-mer token | 将连续序列离散化为可学习的 token | 输入：1,000bp DNA；输出：150 个 token | Methods 2.1 节；与 DNABERT 一致 | 预期：无法捕捉 k-mer 边界外的序列模式 [Analysis] |
| IDEAS Tokenization & Pooling | 将 200bp 分辨率的 IDEAS 状态对齐到 k-mer token | 使表观状态与序列 token 一一对应 | 输入：IDEAS 状态序列；输出：每个 DNA token 对应的 IDEAS token | Methods 2.1 节："IDEAS k-mers are pooled based on the most frequent IDEAS state" | 预期：丢失 200bp 窗口内的表观状态异质性 [Analysis] |
| 双通道 Embedding | DNA 和 IDEAS 分别 embedding 后相加 | 将两种模态映射到同一向量空间 | 输入：token 索引；输出：768 维向量 | Methods 2.1 节："separate embedding layers, which are combined" | 预期：若改为拼接，模型参数量增加但可能无法有效融合 [Analysis] |
| BERT Encoder | 12 层 Transformer 编码器 | 学习序列与表观状态的上下文表征 | 输入：embedding 序列；输出：上下文向量序列 | Methods 2.1 节；RoBERTa 架构 | 实测：移除后模型退化为浅层模型，性能显著下降（未直接消融，但预训练必要性在 Results 3.6 节验证） |
| 联合掩码预训练目标 | 同时预测掩码的 DNA 和 IDEAS token | 迫使模型学习两种模态的联合分布 | 输入：掩码后的 token 序列；输出：DNA 和 IDEAS 的预测分布 | Methods 2.1 节公式 (1) | 预期：若仅预测 DNA，模型可能忽略表观状态信息 [Analysis] |
| 微调头（卷积+全连接） | 将 BERT 输出转为 TF 结合预测 | 将预训练表征适配到监督任务 | 输入：BERT 输出序列；输出：结合概率 | Methods 2.2 节 | 预期：若移除卷积层，可能无法有效聚合局部上下文 [Analysis] |
| 辅助特征拼接（EBERT+） | 将 DNase-seq 和 mappability 特征拼接到 BERT 输出 | 提供直接测量的表观信号 | 输入：BERT 输出 + pooling 后的辅助特征；输出：拼接后的特征 | Methods 2.2 节；Results 3.4 节 | 实测：EBERT+ 比 EBERT 平均提升 0.12 AUPRC（非 IDEAS 类数据集） |

---

## 09 关键公式符号

**总损失函数**（Methods 2.1 节）：

$$\mathcal{L}_{total} = \alpha \mathcal{L}_{DNA} + (1-\alpha) \mathcal{L}_{IDEAS}$$

- $\mathcal{L}_{total}$：总预训练损失
- $\mathcal{L}_{DNA}$：DNA token 的掩码预测交叉熵损失
- $\mathcal{L}_{IDEAS}$：IDEAS token 的掩码预测交叉熵损失
- $\alpha$：权重项，本文取 0.5（等权）

**Tokenization 参数**：
- $k$：k-mer 大小，本文最优为 7
- $L_{input}$：输入 token 序列长度，$L_{input} = 1000/k = 150$（k=7 时）

**模型配置**：
- $L \times A \times H = 12 \times 12 \times 768$（BASE 配置）
- 总参数量约 1 亿（~100M）

**数据规模**：
- 预训练：127 个细胞类型 × 全基因组（约 3M 个 1,000bp 片段/细胞类型，总计约 3.8 亿样本）
- 微调：13 个 TF-细胞类型数据集，10:1 负正样本比

---

## 10 实验设计与证据链

**数据集**：
- 预训练：IDEAS36 数据集（127 细胞类型，36 种表观状态，200bp 分辨率），人类参考基因组 hg19
- 微调：ENCODE-DREAM TF 结合基准（13 个 TF-细胞类型数据集），含 DNA 序列、DNase-seq、mappability 数据

**指标**：
- 预训练：损失收敛
- 微调：AUPRC（主要）、AUROC、Recall@50% FDR、Recall@10% FDR（竞赛定义）

**基线/对比模型**：
- DBERT（仅 DNA 序列输入的 BERT）
- EBERT（DNA + IDEAS 输入的 BERT）
- EBERT+（EBERT + DNase-seq + mappability 辅助特征）
- ENCODE-DREAM 竞赛前 5 名模型（Quang 2019; Keilwagen 2019; Li 2019; DeepGRN Chen 2021）

**预算/硬件**：
- 预训练：Cerebras CS-1 系统（wafer-scale engine），EBERT BASE 约 2.5 天
- 微调：16 GPU，最大学习率 0.0001，线性 warmup 25,000 步

**评测协议**：
- 竞赛定义的训练/验证/测试染色体划分（训练：chr2-7, 9-20, 22, X；评估：chr1, 8, 21）
- 200bp bin 分类，重叠滑动窗口 50bp

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|-------------|-------------------|------|
| 预训练速度对比 | Cerebras CS-1 能显著加速大规模预训练 | DBERT 在 CS-1 上 vs DNABERT 在 8-GPU 集群 | DBERT 预训练 <2 天（2× 基因组 epoch），DNABERT 需 25 天 | CS-1 将预训练时间缩短一个数量级以上 | 未提供精确的 GPU 时间对比 | Results 3.1 节 |
| DBERT vs EBERT 微调 | IDEAS 表观输入提升 TF 结合预测 | 相同微调架构，仅预训练输入不同 | EBERT 在 12/13 数据集上优于 DBERT，平均 AUPRC 提升 0.25（非 CTCF 数据集） | 表观状态信息在预训练阶段即提供增益 | 未报告所有数据集的完整 AUPRC 数值 | Results 3.3 节；Figure 4 |
| EBERT vs EBERT+ | 辅助特征（DNase-seq, mappability）进一步增益 | EBERT+ 在微调阶段拼接辅助特征 | EBERT+ 在 4/13 数据集上排名第 1，整体排名第 3 | 辅助特征与预训练表观表征互补 | 增益幅度因数据集而异，CTC 数据集增益最大 | Results 3.2, 3.4 节；Table 1 |
| 预训练 vs 随机初始化 | 预训练权重对微调性能的必要性 | EBERT+ 用预训练权重 vs 随机初始化 | 预训练版本 AUPRC 提升 0.05-0.204，且收敛更快 | 预训练提供显著且一致的增益 | 未报告随机初始化模型的完整排名 | Results 3.6 节；Figure S1 |
| k-mer 大小影响 | k=7 为最优 tokenization | k ∈ {5,6,7} 的 EBERT 预训练 | k=7 表现最佳 | 与 DNABERT 的发现一致（k 增大至 6-7 有增益） | 未系统比较 k>7 | Methods 2.1 节 |

---

## 11 结论正确解读

**任务范围**：本文聚焦于「细胞类型特异性 TF 结合预测」，使用 ENCODE-DREAM 基准的 13 个 TF-细胞类型数据集。结论仅适用于该任务范围，不涉及其他基因组调控任务（如基因表达、剪接等）。

**Oracle/真值输入**：微调阶段使用 ENCODE-DREAM 提供的 ChIP-seq 峰标注作为真值标签；辅助特征（DNase-seq, mappability）为真实测量数据，非模型预测。

**端到端状态**：本文为「预训练 + 微调」两阶段流程，非端到端训练。预训练阶段使用掩码语言建模（自监督），微调阶段使用监督分类。两阶段使用不同的损失函数和数据分布。

**算力成本**：预训练在 Cerebras CS-1 上约 2.5 天（EBERT BASE），微调在 16 GPU 上完成。作者未报告精确的 GPU 小时数，但指出 CS-1 相比传统 GPU 集群有数量级加速。

**历史数据依赖**：预训练数据为 hg19 参考基因组和 IDEAS36 推断状态（基于 ENCODE 数据）。IDEAS 状态本身是推断结果，可能包含推断误差。

**模型依赖**：EBERT 基于 RoBERTa 架构，与 DNABERT 结构相似，但输入为双模态（DNA + IDEAS）。结论可能不适用于其他架构（如 CNN、Hyena 等）。

**最难情形**：CTCF 数据集对辅助特征（DNase-seq）依赖最大，而 IDEAS 状态对 CTCF 的增益最小——因为 CTCF 结合主要依赖序列基序，表观状态贡献有限。相反，FOXA2、HNF4A 等肝脏数据集从 IDEAS 状态中获益最大。

**群体/领域边界**：结论基于人类基因组（hg19）和 127 个 ENCODE 细胞类型。不适用于非人类物种或其他表观遗传标记体系。

**不确定性**：作者未报告置信区间或统计显著性检验；排名基于竞赛定义的指标，未提供方差估计。

**有边界的复述**：在 ENCODE-DREAM TF 结合预测任务中，将 IDEAS 表观遗传状态作为 BERT 预训练的第二输入模态，相比纯序列预训练（DBERT）在 12/13 数据集上带来 AUPRC 提升；进一步在微调阶段拼接 DNase-seq 和 mappability 辅助特征（EBERT+）可达到竞赛第 3 名。该结论限于人类基因组、127 细胞类型、13 个 TF 数据集，且依赖 Cerebras CS-1 硬件实现大规模预训练。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 模型容量未充分探索 | 仅报告 BASE 配置（12×12×768），未测试 LARGE 配置 | 未来将利用 CS-2 训练更大模型 | Discussion 节："we hypothesize that an EBERT model with larger capacity may produce better performance" |
| 任务范围有限 | 仅验证了 TF 结合预测，未测试其他调控任务 | 未来将扩展到基因表达、剪接、3D 相互作用等任务 | Discussion 节："can also be easily adapted to fine-tune any number of other cell type specific classification tasks" |
| 表观数据依赖推断 | IDEAS 状态为推断结果，非直接测量 | 未明确提及 | 未提供（隐含局限） |
| 未与其他预训练方法系统比较 | 未与 DNABERT 的预训练权重直接对比微调性能 | 未明确提及 | 未提供 |
| 计算资源依赖特殊硬件 | 预训练依赖 Cerebras CS-1，可及性有限 | 未明确提及 | 未提供 |

---

## 13 与已有知识连接

**直接相关文献**：
- **DNABERT (Ji et al. 2021)**：本文的直接前驱，EBERT 采用其架构和 tokenization 策略，但增加了 IDEAS 输入模态。DNABERT 在纯序列任务上表现良好，但无法处理细胞类型特异性问题。
- **Levy et al. 2021**：另一 DNA 语言模型，本文引用其作为序列建模的代表工作。
- **ENCODE-DREAM 竞赛方案 (Quang 2019; Keilwagen 2019; Li 2019)**：这些方案均使用 DNase-seq 等辅助特征，但为任务特化模型。本文的 EBERT+ 与之对比，证明了预训练表征的竞争力。
- **DeepGRN (Chen et al. 2021)**：同样使用 Transformer + DNase-seq 输入的 TF 结合模型，本文将其纳入排名对比。

**可迁移到本课题（TF–DNA 结合机制 × AI/物理模拟）的知识**：
1. **多模态输入设计**：将「序列 + 表观状态」作为平行输入模态的思路，可迁移到「序列 + 结构特征（如 DNA shape, 弯曲性）」或「序列 + 物理模拟特征（如 MD 导出的柔性/静电势）」的联合建模。
2. **预训练-微调范式**：在大规模无标注数据上预训练，再在特定 TF 结合任务上微调，可缓解标注数据稀缺问题。本课题可考虑在全部 TF 结合数据上预训练，再针对特定 TF 微调。
3. **辅助特征融合策略**：本文比较了「预训练时加入表观信息」vs「微调时拼接辅助特征」两种策略，发现前者更优。这提示：若要将物理模拟特征（如 MD 轨迹导出的特征）纳入模型，最好在预训练阶段即引入，而非仅在微调时拼接。
4. **细胞类型特异性的处理**：本文通过 IDEAS 状态编码细胞类型信息，本课题可类比为「通过染色质状态或 3D 基因组结构编码细胞类型上下文」。

---

## 14 学到什么

**Agent 提炼的知识候选**：

1. **多模态预训练优于单模态 + 微调拼接**：EBERT 在预训练阶段即纳入 IDEAS 表观状态，比 DBERT 仅在微调时添加辅助特征更有效。→ 可迁移：若要将 DNA shape 或 MD 模拟特征纳入 TF 结合预测模型，应在预训练阶段即作为输入模态，而非微调时拼接。

2. **表观状态可作为「细胞类型上下文」的编码**：IDEAS 36 状态将复杂的表观遗传信号压缩为离散标签，使模型能够区分不同细胞类型。→ 可迁移：可考虑将染色质可及性（ATAC-seq）、组蛋白修饰等表观信息编码为离散状态，作为 TF 结合模型的上下文输入。

3. **弱标签（推断状态）可用于预训练**：IDEAS 状态本身是推断结果，但作为预训练目标仍然有效。→ 可迁移：物理模拟导出的特征（如结合自由能、柔性评分）即使有噪声，也可作为预训练信号。

4. **大规模预训练需要专用硬件**：Cerebras CS-1 使 127 细胞类型 × 全基因组的预训练在 2.5 天内完成，而 GPU 集群需数周。→ 可迁移：本课题若涉及全基因组规模的预训练，需考虑硬件选择；或采用更高效的架构（如线性注意力）降低计算需求。

5. **任务特化 vs 通用表征的权衡**：ENCODE-DREAM 顶级方案为任务特化模型，EBERT 为通用预训练模型，两者性能接近但 EBERT 更具泛化潜力。→ 可迁移：TF 结合预测可考虑「通用预训练 + 任务微调」范式，而非从头训练任务特化模型。

6. **CTCF 与其它 TF 的差异**：CTCF 结合主要依赖序列基序，表观状态增益小；而 FOXA2、HNF4A 等依赖表观状态。→ 可迁移：不同 TF 的结合机制差异显著，模型设计应考虑 TF 类别（如 pioneer factor vs. 依赖染色质开放的 TF）。

---

## 15 与已有知识连接

**可核验的外部文献**：
- **Ji et al. 2021 (DNABERT)**：DNABERT 的架构和 tokenization 策略，EBERT 的直接前驱。可对比两者在纯序列任务上的表现差异。
- **Devlin et al. 2019 (BERT)**：掩码语言模型和 Transformer 架构的原始来源。
- **Liu et al. 2019 (RoBERTa)**：EBERT 采用的 RoBERTa 风格架构。
- **Zhang et al. 2016 (IDEAS)**：IDEAS36 数据集的来源，36 种表观状态的推断方法。
- **ENCODE-DREAM Challenge**：竞赛官网和数据集描述，13 个 TF-细胞类型基准的详细定义。
- **Quang 2019; Keilwagen 2019; Li 2019**：竞赛顶级方案，均使用 DNase-seq 辅助特征。
- **Chen et al. 2021 (DeepGRN)**：同样使用 Transformer + DNase-seq 的 TF 结合模型。

**与用户已有知识的连接**：
- 若用户熟悉 DNABERT，可重点关注 EBERT 的增量：IDEAS 输入模态和联合掩码目标。
- 若用户熟悉 ENCODE-DREAM 竞赛，可对比 EBERT+ 与竞赛顶级方案（如 FactorNet）的架构差异。
- 若用户熟悉表观遗传学，可关注 IDEAS 36 状态的定义和生物学意义。

**候选方向**：
- 将 EBERT 的「序列 + 表观状态」双输入思路扩展到「序列 + DNA shape 特征」或「序列 + MD 模拟特征」。
- 将 EBERT 的预训练-微调范式应用于其他 TF 结合预测任务（如 ChIP-seq 峰调用、变异效应预测）。
- 探索更大模型（LARGE 配置）在 CS-2 上的性能提升。

---

## 16 研究想法

**Agent 生成的研究候选**：

### 候选 1：DNA shape 感知的 TF 结合语言模型
- **名称**：ShapeBERT：融合 DNA 结构特征的转录因子结合预测
- **来源局限/观察**：EBERT 证明了表观状态作为第二输入模态的有效性，但未考虑 DNA 三维结构（shape）特征。已知 DNA shape（如 minor groove width, roll, helix twist）对 TF 结合特异性有重要影响（Rohs et al. 2009）。
- **核心假设**：将 DNA shape 特征（从序列预测或 MD 模拟导出）作为与序列平行的输入模态，可进一步提升 TF 结合预测性能，尤其是对结构选择性 TF。
- **相对本文的增量**：将 EBERT 的双输入（序列 + 表观）扩展为三输入（序列 + 表观 + shape），或替换表观为 shape 以比较不同信息源贡献。
- **初步方法**：使用 DNAShape 或 MD 模拟生成每个 k-mer 的 shape 特征向量，与 DNA embedding 拼接或相加后送入 BERT encoder；预训练目标可加入 shape 特征的重建任务。
- **验证方式**：在 ENCODE-DREAM 基准上对比 ShapeBERT vs EBERT vs DBERT；分析 shape 特征对结构选择性 TF（如 bZIP 家族）的增益是否大于一般 TF。
- **可能的失败模式**：shape 特征与序列特征高度冗余，导致增益有限；或 shape 预测误差在预训练阶段被放大。
- **创新状态**：unverified（需文献调研确认是否已有类似工作）

### 候选 2：物理模拟特征作为预训练信号的可行性研究
- **名称**：MD-BERT：以分子动力学导出的结合自由能作为预训练辅助目标
- **来源局限/观察**：EBERT 使用推断的 IDEAS 状态作为预训练信号，说明「弱标签」有效。MD 模拟可提供更精细的物理化学特征（如结合自由能、柔性、溶剂可及性），但计算成本高。
- **核心假设**：对少量代表性 TF-DNA 复合物进行 MD 模拟，导出结合自由能或柔性特征，作为预训练的辅助目标或对比学习信号，可提升模型对结合亲和力的预测能力。
- **相对本文的增量**：将预训练信号从离散表观状态扩展为连续物理量；探索「物理模拟 + 深度学习」的混合范式。
- **初步方法**：选取 10-20 个代表性 TF-DNA 复合物进行 MD 模拟，提取每个位置的柔性/能量特征；将这些特征作为预训练的回归目标或对比学习正负样本构造依据。
- **验证方式**：在 TF 结合预测任务上对比 MD-BERT vs EBERT；分析 MD 特征是否提供序列和表观之外的新信息。
- **可能的失败模式**：MD 模拟的体系代表性不足，导致特征泛化差；或计算成本过高，难以覆盖足够多的 TF 家族。
- **创新状态**：unverified（需确认是否有类似「物理信息预训练」工作）

### 候选 3：TF 家族感知的微调策略
- **名称**：TF-Family Adapter：基于 TF 家族先验的适配器微调
- **来源局限/观察**：EBERT 的微调对所有 TF 使用相同架构，但不同 TF 家族（如 C2H2 锌指、bZIP、homeodomain）的结合机制差异显著（CTCF 依赖序列基序，FOXA2 依赖表观状态）。
- **核心假设**：为不同 TF 家族设计专门的适配器模块，可提升模型对家族特异性结合机制的建模能力。
- **相对本文的增量**：在 EBERT 基础上增加 TF 家族条件化模块，而非单一微调头。
- **初步方法**：在 BERT encoder 之上，为每个 TF 家族设计独立的低秩适配器（LoRA），微调时仅更新适配器参数；或使用超网络根据 TF 家族生成微调头参数。
- **验证方式**：对比 TF-Family Adapter vs 标准微调在 13 个 ENCODE-DREAM 数据集上的性能；分析家族内 vs 家族间的泛化差异。
- **可能的失败模式**：TF 家族内异质性大，家族先验反而限制模型灵活性；或适配器参数增加导致过拟合。
- **创新状态**：partially checked（已有 TF 家族分类知识，但适配器方法需验证）

### 候选 4：跨细胞类型的零样本 TF 结合预测
- **名称**：Zero-Shot TF Binding：利用预训练表观状态实现新细胞类型的零样本预测
- **来源局限/观察**：EBERT 的预训练覆盖 127 个细胞类型，但微调仅针对有 ChIP-seq 数据的 TF-细胞类型对。实际应用中，新细胞类型可能缺乏 ChIP-seq 数据。
- **核心假设**：预训练的表观状态表征可迁移到未见过的细胞类型，实现零样本 TF 结合预测。
- **相对本文的增量**：将 EBERT 从「有监督微调」扩展到「零样本/少样本预测」。
- **初步方法**：对目标细胞类型，仅需提供其 IDEAS 状态（可从 ATAC-seq 或组蛋白修饰数据推断），无需 ChIP-seq 标签；使用预训练 EBERT 直接生成结合预测，或使用少量样本进行少样本微调。
- **验证方式**：留出若干细胞类型的 ChIP-seq 数据作为测试集，评估零样本预测性能；对比有监督微调的性能差距。
- **可能的失败模式**：表观状态在不同细胞类型间的分布差异大，零样本泛化失败；或 IDEAS 状态对新细胞类型的推断不准确。
- **创新状态**：unverified（需确认是否有类似零样本 TF 结合预测工作）