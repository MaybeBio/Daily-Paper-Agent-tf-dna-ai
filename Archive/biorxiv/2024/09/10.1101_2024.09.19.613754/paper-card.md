## 01 基本信息

- **标题**：scooby: Modeling multi-modal genomic profiles from DNA sequence at single-cell resolution
- **作者与单位**：Hingerl JC; Martens LD; Karollus A; Manz T; Buenrostro JD; Theis FJ; Gagneur J（具体单位未在摘要中提供）
- **期刊/预印本平台**：bioRxiv
- **年份**：2024
- **论文类型**：预印本（方法学/工具类）
- **领域**：计算基因组学；单细胞多组学；深度学习序列建模
- **关键词**：单细胞RNA-seq（scRNA-seq）、单细胞ATAC-seq（scATAC-seq）、DNA序列、深度学习、转录调控、Borzoi、LoRA
- **DOI/arXiv 号**：10.1101/2024.09.19.613754
- **代码**：https://github.com/gagneurlab/scooby ；复现脚本：https://github.com/gagneurlab/scooby_reproducibility ；Zenodo存档：https://zenodo.org/records/14051793
- **数据**：NeurIPS 2021骨髓多组学数据集（SRA: SRP356158；AWS；GEO: GSE194122）；心类器官数据集（SRA: SRP359250, SRP359249）；OneK1K数据集（SRA: SRP359840；CZ CELLxGENE）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA互作（聚焦TF–DNA结合机制）× 深度学习」方向。核心贡献是将预训练的多组学序列模型（Borzoi）扩展到单细胞分辨率，联合建模scRNA-seq和scATAC-seq，并通过TF motif in silico deletion和eQTL效应分解来解析细胞类型特异的TF调控逻辑。对TF–DNA结合机制研究提供了从序列到单细胞表型（表达+染色质可及性）的端到端预测框架。

---

## 02 一句话总结

本文提出scooby，通过将预训练的Borzoi序列模型与细胞特异的轻量解码器结合（以单细胞嵌入为条件），在单细胞分辨率下联合预测scRNA-seq和scATAC-seq覆盖度谱，并利用in silico motif deletion和eQTL分解验证了其捕捉细胞类型特异TF调控与变异效应的能力。

---

## 03 研究问题

- **具体问题**：如何从DNA序列直接预测单细胞分辨率的基因表达（scRNA-seq）和染色质可及性（scATAC-seq）谱，从而捕捉细胞类型特异的转录调控机制？
- **为什么重要**：基因调控具有高度细胞类型特异性，bulk水平的序列模型（如Borzoi、Enformer）无法解析细胞异质性；而现有单细胞序列模型（如seq2cells）仅建模表达、依赖TSS注释、且每个细胞需独立输出头导致计算不可扩展。
- **现有方法不足**：
  - 早期scATAC-seq模型（如scBasset）输入序列窗口过短（~1 kb），无法捕捉远端调控元件；
  - seq2cells虽使用200 kb上下文，但仅预测表达、依赖TSS注释、每细胞独立输出头导致参数随细胞数线性增长；
  - 缺乏联合建模表达与染色质可及性的单细胞序列模型。
- **精确的"Can ... ?"研究问题**：Can a single sequence-based model, conditioned on a low-dimensional cell-state embedding, jointly predict scRNA-seq and scATAC-seq profiles at single-cell resolution and generalize to unseen cells and cell types?

---

## 04 背景与发展脉络

**注：以下脉络基于本文Introduction及引用，属于「经外部核验」的领域发展框架。**

1. **Bulk序列→功能预测**：Enformer（Avsec et al., 2021）和Borzoi（Calico/Calico, 2023）等模型从DNA序列预测bulk RNA-seq/染色质谱，证明了序列包含大量调控信息，但无法解析细胞异质性。
2. **单细胞ATAC序列建模**：早期工作（如scBasset, Yuan & Kelley, 2022）用CNN在~1 kb窗口预测单细胞染色质可及性，但上下文过短，无法捕捉远端增强子-启动子互作。
3. **单细胞表达序列建模**：seq2cells（GSK-AI, 2024）将Enformer扩展到单细胞表达预测，使用200 kb上下文，但依赖TSS注释、每细胞独立输出头、仅建模表达。
4. **多组学联合建模**：scooby首次将预训练的多组学bulk模型（Borzoi）作为基础模型，通过LoRA微调序列嵌入+细胞条件解码器，实现单细胞分辨率下表达与可及性的联合预测，且参数不随细胞数增长。

**本文主张的位置**：scooby填补了「单细胞分辨率 × 多组学 × 长上下文序列建模」的空白，是首个可扩展至百万级细胞的联合建模框架。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单细胞数据稀疏性 | 单细胞RNA/ATAC谱高度稀疏，直接预测噪声大 | 单细胞技术捕获效率低，dropout率高 | Results 图1d：单细胞与100近邻平均的相关性对比 |
| 现有模型无法捕捉细胞异质性 | bulk模型（Borzoi）输出为群体平均，无法区分细胞类型 | bulk数据混合了多种细胞状态 | Introduction：bulk模型无法捕捉细胞异质性 |
| seq2cells计算不可扩展 | 每细胞独立输出头，参数随细胞数线性增长 | 输出头数量=细胞数 | Introduction：seq2cells computational intractability |
| 依赖TSS注释 | seq2cells需基因注释定义预测目标 | 基因注释不完整或模糊时性能下降 | Introduction：relies on potentially ambiguous TSS annotations |
| 单模态局限 | 仅建模表达或仅建模可及性，无法解析调控层级 | 表达与可及性由不同但耦合的机制驱动 | Introduction：joint modeling of both modalities |
| 远端调控信息缺失 | 短窗口模型（~1 kb）无法捕捉增强子等远端元件 | 调控元件可位于距TSS数百kb处 | Introduction：local predictors fail to capture distal regulation |
| 变异效应细胞类型特异性 | bulk eQTL无法解析变异在何种细胞类型中起作用 | 同一变异在不同细胞类型中效应不同 | Results 图4：单细胞eQTL分解 |

---

## 06 核心思想

### 1) 表面方法
- 以预训练的Borzoi（多组学bulk序列模型）为基础，冻结其卷积+Transformer主干；
- 引入LoRA低秩适配器微调序列嵌入（rank=8）；
- 在Borzoi penultimate层后添加可训练GELU层；
- 设计细胞条件解码器：以低维单细胞嵌入（来自Poisson-MultiVI）为条件，动态生成1×1卷积权重，将序列嵌入映射到每个细胞的表达/可及性谱。

### 2) 核心洞察
- **细胞状态作为条件而非输出**：将细胞嵌入作为解码器的条件输入，而非为每个细胞训练独立输出头，使参数不随细胞数增长，且能利用细胞间相似性。
- **预训练基础模型+轻量适配**：Borzoi已编码丰富的序列-调控关系，通过LoRA微调即可适应单细胞数据分布，避免从头训练。
- **多组学联合解码**：同一序列嵌入通过不同解码头同时预测表达和可及性，强制模型学习共享的调控逻辑。

### 3) 可能的普适教训 [Analysis]
- 将「群体平均」的预训练模型适配到「单细胞分辨率」时，条件化解码器比独立输出头更高效且泛化更好。
- 多组学联合建模可互相正则化，缓解单模态稀疏性问题。
- 基础模型+轻量适配（LoRA）是迁移到新数据域的高效策略。

---

## 07 方法总览

**输入**：
- DNA序列（524,288 bp，以基因/峰为中心）
- 细胞嵌入（低维向量，来自Poisson-MultiVI，维度14）

**输出**：
- 每个细胞的scRNA-seq覆盖度谱（32 bp分辨率，中心196,608 bp区域）
- 每个细胞的scATAC-seq插入谱（32 bp分辨率）

**模块**：
1. **Borzoi主干**：预训练卷积+Transformer编码器，提取序列嵌入（32 bp分辨率）
2. **LoRA适配器**：在主干各层注入低秩矩阵（rank=8），微调序列嵌入
3. **GELU层**：在penultimate层后添加可训练非线性层
4. **细胞条件解码器**：MLP接收细胞嵌入，输出1×1卷积核权重（形状1921×2×1或1921×1×1），对序列嵌入做位置线性变换

**训练**：
- 优化器：AdamW
- 学习率：4×10⁻⁴（解码器）/ 2×10⁻⁴（LoRA+新层）
- 批量：8序列 × 64随机采样细胞
- 硬件：8× NVIDIA A40 GPU，训练2天
- 损失：Poisson + multinomial（与Borzoi一致）
- 数据增强：随机平移±3 bp、反向互补

**流程**：
1. 输入DNA序列 → Borzoi主干（含LoRA）→ 序列嵌入
2. 输入细胞嵌入 → MLP → 解码器权重
3. 序列嵌入 × 解码器权重 → 预测该细胞的表达/可及性谱
4. 与观测谱计算损失，反向传播更新LoRA、GELU层和解码器

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Borzoi主干（冻结） | 提取序列的调控特征嵌入 | 预训练已编码丰富的序列-调控关系，避免从头训练 | 输入：524 kb DNA序列；输出：32 bp分辨率嵌入 | Results：scooby性能与Borzoi相当（bulk水平） | 预期大幅下降，需从头训练且数据量不足 [预期] |
| LoRA适配器 | 微调序列嵌入以适应单细胞数据分布 | 单细胞数据与bulk数据分布不同（稀疏性、3'偏差） | 输入：主干各层激活；输出：低秩更新后的激活 | Extended Data Fig.5：无LoRA变体性能下降（across cell types R=0.501 vs 0.55） | 实测：across cell types相关性从0.55降至0.501 |
| GELU层 | 增加非线性变换能力 | 单细胞解码需要比bulk更复杂的映射 | 输入：penultimate层嵌入；输出：变换后嵌入 | 未单独消融 | 预期小幅下降 [预期] |
| 细胞条件解码器 | 将序列嵌入映射到特定细胞的表达/可及性谱 | 核心创新：以细胞嵌入为条件，实现参数共享 | 输入：序列嵌入+细胞嵌入；输出：该细胞的预测谱 | Results 图1d：优于伪bulk基线 | 移除后退化为bulk模型，无法区分细胞类型 [预期] |
| Poisson-MultiVI嵌入 | 生成低维细胞状态表示 | 提供细胞身份信息，无需独立输出头 | 输入：原始多组学矩阵；输出：14维嵌入 | Methods：嵌入生成细节 | 替换为其他嵌入（如PCA）可能影响性能 [预期] |
| 数据增强（平移/互补） | 增加训练数据多样性 | 单细胞数据稀疏，需正则化 | 输入：原始序列；输出：增强序列 | Methods：训练细节 | 预期过拟合增加 [预期] |

---

## 09 关键公式符号

**损失函数**（与Borzoi一致，未在摘要中给出完整公式，以下为基于Borzoi的合理推断 [Analysis]）：

- 总损失 = λ_RNA × L_RNA + λ_ATAC × L_ATAC
- L_RNA = Poisson负对数似然：Σᵢ (yᵢ - xᵢ·log(yᵢ) + log(xᵢ!))，其中xᵢ为预测值，yᵢ为观测值
- L_ATAC = 二项/负二项负对数似然（ATAC插入计数）

**解码器**：
- 预测值 = W_cell · h_seq + b_cell
- 其中W_cell = MLP(cell_embedding)，h_seq为序列嵌入

**LoRA**：
- W' = W + BA，其中B∈R^{d×r}，A∈R^{r×d}，r=8

**评估指标**：
- Pearson相关系数（对数尺度，预测vs观测）
- 基因水平：跨细胞类型相关性
- 细胞水平：跨基因相关性

---

## 10 实验设计与证据链

**数据集**：
1. **NeurIPS 2021骨髓多组学数据集**：63,683个人骨髓单核细胞，配对scRNA-seq + scATAC-seq，10x Multiome平台
2. **心类器官数据集**：人心脏类器官，含JCF祖细胞异质性
3. **OneK1K数据集**：1,048,472个PBMC，982个供体，用于eQTL分析

**指标**：
- Pearson相关性（对数尺度）
- 基因水平/细胞水平相关性
- eQTL Spearman相关性
- TF motif效应与TF表达的相关性

**基线**：
- Borzoi（bulk模型，使用对应bulk track）
- seq2cells（单细胞表达模型）
- 伪bulk基线（将单细胞平均后预测）

**评测协议**：
- 与Borzoi相同的序列级train/val/test划分（避免数据泄漏）
- 测试集基因/峰在训练中完全未见

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|------------------|------|
| 单细胞谱预测 | scooby能预测单细胞分辨率表达/可及性 | 与伪bulk基线对比 | RNA R=0.15 vs 0.09；ATAC R=0.11 vs 0.08（单细胞水平）；100近邻平均后R=0.63/0.70 | scooby捕捉了细胞特异信号 | 单细胞水平相关性仍低，受稀疏性限制 | Results 图1d |
| 细胞类型特异表达 | scooby捕捉细胞类型差异 | 跨细胞类型相关性 | 与Borzoi bulk性能相当（R=0.86） | 细胞类型水平预测准确 | 未与更多单细胞模型对比 | Results 图2d |
| 与seq2cells对比 | scooby优于现有单细胞表达模型 | 共享测试基因 | 平均相关性0.87 vs 0.77 | scooby显著优于seq2cells | 仅在表达任务上对比 | Results 图2e |
| 无LoRA消融 | LoRA微调的必要性 | 移除LoRA | across cell types R=0.501 vs 0.55 | LoRA提升细胞类型区分 | 未报告其他消融 | Extended Data Fig.5 |
| 未见细胞类型泛化 | 模型可泛化到训练中未见的细胞状态 | 移除normoblast训练 | R=0.79 vs 0.81（全模型） | 可外推至相近细胞状态 | 仅测试了单一细胞类型 | Results 图2f |
| TF motif效应验证 | motif删除得分反映TF活性 | 与TF表达相关性 | 显著优于chromVAR（P=9×10⁻⁸）和scBasset（P=0.04） | motif效应得分捕捉真实TF活性 | 未与实验ChIP-seq直接验证 | Results 图3b |
| eQTL预测 | scooby能预测细胞类型特异eQTL | 与Borzoi对比 | OneK1K上显著优于Borzoi | 单细胞分辨率提升eQTL预测 | 仅评估了eQTL，未评估其他变异类型 | Results 图4a |
| eQTL分解 | 能将bulk eQTL分解为细胞类型特异效应 | 与GTEx bulk对比 | 识别出细胞类型特异的eQTL | 可解析bulk信号的细胞来源 | 未与实验验证的细胞类型eQTL对比 | Results 图4e-f |
| 心类器官案例 | 可解析组织内细胞异质性 | 与CellRank转移概率相关 | 识别出JCF命运决定TF | 可应用于非血液系统 | 单一案例研究 | Results 图3f-i |

---

## 11 结论正确解读

- **任务范围**：scooby预测的是单细胞RNA/ATAC覆盖度谱，而非直接的TF结合事件。TF调控信息通过in silico motif deletion间接推断。
- **oracle/真值输入**：细胞嵌入来自Poisson-MultiVI，该模型使用了原始多组学数据（包括测试基因/峰的表达），因此细胞嵌入包含了一定程度的"泄漏"信息——即细胞嵌入不是纯序列预测的产物，而是数据驱动的。这意味着scooby的端到端能力（纯序列→单细胞谱）并未被完全验证。
- **端到端状态**：scooby并非完全端到端——它依赖预计算的细胞嵌入。真正的端到端需要从序列同时预测细胞嵌入和谱。
- **算力成本**：8×A40 GPU训练2天，推理时LoRA可合并，无额外开销。但细胞嵌入计算（Poisson-MultiVI）需要额外成本。
- **历史数据依赖**：Borzoi预训练权重来自bulk数据，scooby继承了其训练数据中的潜在偏差。
- **模型依赖**：性能高度依赖Borzoi的预训练质量；更换基础模型需重新验证。
- **最难情形**：远端eQTL（>100 kb）效应预测仍不准确；单细胞水平相关性低（R≈0.15），主要受数据稀疏性限制。
- **群体/领域边界**：仅在骨髓造血和心脏类器官数据上验证；未测试其他组织或物种。
- **不确定性**：TF motif效应得分基于motif匹配，无法区分同家族TF（如GATA1/2/3）；未提供置信区间。

**有边界的复述**：scooby在骨髓造血和心脏类器官数据上，能够以细胞嵌入为条件，从DNA序列预测单细胞RNA/ATAC谱，其细胞类型水平的预测精度与bulk模型相当，且TF motif删除得分与TF表达的相关性优于chromVAR和scBasset。但其单细胞水平预测精度仍受稀疏性限制，且依赖预计算的细胞嵌入，并非完全端到端。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 单细胞数据稀疏性 | 单细胞水平相关性低（R≈0.15） | 未明确提及 | Results 图1d讨论 |
| 3'覆盖偏差 | scRNA-seq 3'端覆盖偏差限制isoform分析 | 应用SMART-seq或长读长测序数据 | Discussion |
| 远端eQTL效应预测不足 | 远端调控元件效应捕捉有限 | 改进模型架构以更好建模长程互作 | Discussion |
| 细胞嵌入依赖 | 需要预计算的细胞嵌入，非完全端到端 | 未明确提及 | Methods（嵌入生成） |
| 训练数据领域限制 | 仅在骨髓和心脏类器官上验证 | 推广至更多组织和物种 | Discussion |
| 计算资源需求 | 8×A40 GPU训练2天 | 使用更高效的基础模型 | Methods（训练细节） |
| TF motif效应无法区分同家族TF | GATA1/2/3等相似motif得分相近 | 结合ChIP-seq等实验数据 | Results 图3讨论 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 细胞嵌入来自Poisson-MultiVI，使用了测试基因的表达信息 | 细胞嵌入可能编码了测试基因的表达模式，导致评估乐观 | 若嵌入包含泄漏，则scooby的泛化能力被高估 | 使用仅基于训练基因的嵌入重新评估；或使用纯序列预测的嵌入 | Methods：嵌入生成部分 |
| 与seq2cells对比不公平 | seq2cells仅用100k细胞训练，scooby用63k细胞+预训练Borzoi | 性能差异可能来自数据量而非架构 | 在相同数据量和训练预算下对比 | Results 图2e |
| TF motif效应验证使用TF表达作为代理 | TF表达≠TF活性（存在翻译后修饰、竞争性结合等） | 可能高估或低估motif效应的生物学意义 | 与ChIP-seq、ATAC footprint等直接实验对比 | Results 图3b |
| 未报告单细胞水平ATAC预测的详细指标 | ATAC单细胞相关性可能更低 | 无法评估ATAC预测的实际质量 | 补充单细胞ATAC水平的详细指标 | Results 图1d |
| 消融实验不完整 | 仅报告了无LoRA变体，未报告无GELU层、无数据增强等 | 无法确定各组件贡献 | 补充完整消融矩阵 | Extended Data Fig.5 |
| eQTL分解验证使用统计共定位而非实验验证 | 预测的细胞类型特异性可能不代表真实生物学 | 可能产生假阳性细胞类型归属 | 使用CRISPR扰动或等位基因特异性表达验证 | Results 图4 |
| 未报告模型在不同基因组区域（如重复区域、MHC区域）的性能 | 复杂区域可能表现不佳 | 影响变异解读的可靠性 | 分层评估不同基因组区域 | 未提供 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **条件解码器设计**：以低维细胞嵌入为条件动态生成解码器权重，而非为每个细胞训练独立输出头。这一思路可迁移到TF–DNA结合预测：以细胞类型/状态嵌入为条件，预测不同细胞状态下的TF结合谱（如ChIP-seq、CUT&Tag），避免为每个细胞/状态训练独立模型。

2. **预训练基础模型+LoRA适配**：将bulk水平的预训练模型（Borzoi）通过LoRA微调适配到单细胞数据，大幅降低训练成本。可迁移到TF–DNA结合领域：使用预训练的蛋白质语言模型（如ESM）或DNA语言模型（如Enformer）作为基础，通过LoRA适配到特定TF的结合预测任务。

3. **多组学联合建模**：同一序列嵌入同时预测表达和可及性，利用共享调控逻辑互相正则化。可迁移到TF–DNA结合研究：联合建模TF结合（ChIP-seq）、染色质可及性（ATAC-seq）和基因表达（RNA-seq），捕捉从TF结合到转录输出的完整调控级联。

4. **TF motif效应得分**：通过in silico motif删除计算TF对表达的贡献，比单纯motif扫描更接近功能效应。可迁移到TF–DNA结合机制研究：对候选TF结合位点进行in silico突变，预测其对表达/可及性的影响，从而区分功能性结合与非功能性结合。

5. **eQTL细胞类型分解**：利用单细胞模型将bulk eQTL分解为细胞类型特异的效应，并关联到TF motif。可迁移到TF–DNA结合研究：将GWAS/eQTL变异映射到细胞类型特异的TF结合变化，识别疾病相关细胞类型中的关键TF调控轴。

6. **数据泄漏控制**：作者在计算细胞嵌入时排除了测试基因/峰，但嵌入仍包含测试信息。这提醒我们在设计评估流程时，需严格区分「序列→表型」的端到端能力与「表型→表型」的插值能力。

7. **评估指标选择**：使用Pearson相关性（对数尺度）评估单细胞预测，同时报告单细胞水平和细胞类型水平指标。可迁移到TF–DNA结合预测评估：区分单细胞分辨率与群体平均水平的性能。

---

## 15 与已有知识连接

- **Borzoi（Calico, 2023）**：scooby的直接基础模型。Borzoi是bulk多组学序列预测模型，scooby将其扩展到单细胞。连接点：序列嵌入的迁移学习。
- **Enformer（Avsec et al., 2021, Nature Methods）**：seq2cells的基础模型，也是Borzoi的前身。scooby与seq2cells的对比直接源于此。
- **seq2cells（GSK-AI, 2024）**：首个单细胞表达序列预测模型，scooby的主要对比对象。差异：seq2cells仅预测表达、依赖TSS注释、每细胞独立输出头。
- **scBasset（Yuan & Kelley, 2022）**：基于CNN的scATAC-seq序列模型，输入窗口~1 kb。scooby在TF motif效应上与其对比。
- **chromVAR（Schep et al., 2017）**：基于motif的TF活性推断方法，scooby的TF motif效应得分与其对比。
- **Poisson-MultiVI（Martens et al., 2024）**：多组学单细胞嵌入方法，scooby使用其生成细胞嵌入。
- **LoRA（Hu et al., 2021）**：参数高效微调方法，scooby用于适配Borzoi。
- **TF–DNA结合机制方向**：本文的TF motif效应得分和eQTL分解方法可迁移到TF结合位点功能预测；条件解码器思路可迁移到细胞类型特异的TF结合预测。

---

## 16 研究想法

**Agent 生成的研究候选**

### 候选1：TF–DNA结合特异性的细胞状态条件预测器
- **名称**：Cell-conditioned TF binding predictor
- **来源局限/观察**：scooby以细胞嵌入为条件预测表达/可及性，但未直接预测TF结合。现有TF结合预测模型（如DeepSEA、Basenji）多为bulk水平，无法捕捉细胞类型特异的结合。
- **核心假设**：TF结合谱可分解为「序列编码的潜在结合能力」与「细胞状态调制的结合概率」的乘积。
- **增量**：将scooby的条件解码器思路迁移到TF–ChIP-seq/cUT&Tag预测，以细胞嵌入为条件预测TF结合峰。
- **初步方法**：使用预训练的DNA模型（如Borzoi/Enformer）提取序列嵌入，以单细胞ATAC-seq嵌入为条件，预测特定TF的结合概率。
- **验证方式**：在ENCODE/单细胞ChIP-seq数据上评估，对比bulk模型和细胞状态无关模型。
- **创新状态**：unverified

### 候选2：TF motif效应得分的单细胞分解
- **名称**：Single-cell TF motif effect decomposition
- **来源局限/观察**：scooby的TF motif效应得分是细胞类型平均的，无法解析同一TF在不同细胞状态下的差异效应。
- **核心假设**：TF motif效应得分可分解为细胞类型共享的「基础效应」和细胞类型特异的「调制效应」。
- **增量**：将scooby的motif删除方法扩展到单细胞水平，为每个细胞计算TF motif效应得分。
- **初步方法**：对每个细胞独立进行in silico motif删除，计算该细胞的TF效应得分；使用矩阵分解（如NMF）分解为共享和特异成分。
- **验证方式**：在造血分化数据上验证GATA1等已知谱系特异TF的效应分解。
- **创新状态**：unverified

### 候选3：eQTL的TF介导细胞类型特异效应预测
- **名称**：TF-mediated cell-type-specific eQTL prediction
- **来源局限/观察**：scooby能分解eQTL的细胞类型效应，但未明确关联到具体TF。现有eQTL解读工具（如coloc、SMR）无法在单细胞水平解析TF介导机制。
- **核心假设**：细胞类型特异的eQTL效应主要由该细胞类型中活跃的TF结合差异介导。
- **增量**：将scooby的eQTL预测与TF motif效应得分结合，构建「变异→TF结合改变→表达改变」的因果链。
- **初步方法**：对每个eQTL变异，计算其所在区域的TF motif效应得分变化，并与细胞类型特异的eQTL效应关联。
- **验证方式**：在OneK1K和GTEx数据上验证，对比已知的TF-eQTL调控对。
- **创新状态**：unverified

### 候选4：多模态TF调控的物理-深度学习混合模型
- **名称**：Hybrid physics-informed TF binding model
- **来源局限/观察**：scooby是纯数据驱动模型，未利用TF–DNA结合的物理化学约束（如结合自由能、构象变化）。MD模拟虽能提供物理细节，但计算成本高，无法覆盖全基因组。
- **核心假设**：将MD模拟得到的TF–DNA结合自由能作为先验约束，可提升深度学习模型的泛化能力和可解释性。
- **增量**：在scooby的框架中引入物理约束损失项，或在解码器中加入结合自由能特征。
- **初步方法**：对代表性TF–DNA复合物进行MD模拟，提取结合自由能特征；将这些特征作为辅助输入或正则化项加入scooby。
- **验证方式**：在TF结合预测任务上对比有无物理约束的模型性能。
- **创新状态**：unverified

### 候选5：TF协同结合的序列语法学习
- **名称**：TF combinatorial syntax learner
- **来源局限/观察**：scooby的motif删除是单TF的，无法捕捉TF间的协同或拮抗效应。现有方法（如MARZ、TFimpute）对TF组合的序列语法建模不足。
- **核心假设**：细胞类型特异的基因表达由TF组合的「序列语法」决定，可通过联合motif删除学习。
- **增量**：将scooby的motif删除扩展到TF对或TF组合，学习TF间的协同/拮抗关系。
- **初步方法**：对每个细胞类型，随机删除TF对motif，计算联合效应与单TF效应的差异，构建TF互作网络。
- **验证方式**：在造血分化数据上验证已知的TF协同对（如GATA1-FOG1、PU.1-CEBPA）。
- **创新状态**：unverified