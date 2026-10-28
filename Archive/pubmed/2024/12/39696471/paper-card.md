## 01 基本信息

- **标题**：EpiGePT: a pretrained transformer-based language model for context-specific human epigenomics
- **作者**：Gao, Zijing; Liu, Qiao; Zeng, Wanwen; Jiang, Rui; Wong, Wing Hung
- **单位**：未提供（根据作者信息推测为清华大学/斯坦福大学相关机构，原文未明确列出）
- **期刊/预印本平台**：Genome Biology
- **年份**：2024-12-19
- **论文类型**：方法学（Method）论文，提出新模型
- **领域**：基因组学 / 表观基因组学 / 深度学习
- **关键词**：表观基因组学、Transformer、预训练语言模型、染色质状态预测、TF–DNA 互作、3D 基因组、变异效应预测
- **DOI/arXiv 号**：10.1186/s13059-024-03449-7
- **代码**：未提供（原文未明确给出代码仓库地址）
- **数据**：ENCODE 项目数据（DNase-seq、RNA-seq、ChIP-seq、HiChIP），ROADMAP 项目数据
- **阅读日期**：2026-05-13（按当前日期填写）
- **在该课题方向中的位置**：本文属于「AI/深度学习 × 表观基因组学」方向，核心创新在于将 TF 表达谱作为上下文条件输入 Transformer 模型，实现跨细胞类型的表观遗传信号预测。与「TF–DNA 结合机制」课题的关联在于：模型显式建模 TF 表达与染色质状态的关系，并通过梯度重要性分数（GIS）推断 TF–靶基因调控关系，为从序列+上下文预测 TF 结合下游效应提供了可迁移的框架。

## 02 一句话总结

本文提出 EpiGePT——一个以 DNA 序列和 711 个 TF 的表达谱为输入的 Transformer 预训练模型，通过自注意力机制和 3D 染色质互作数据引导训练，实现跨细胞类型的表观遗传信号预测，并利用梯度重要性分数推断 TF–靶基因调控关系。

## 03 研究问题

- **具体问题**：如何构建一个能够预测**新细胞类型**（训练中未见过的 context）中表观遗传信号的深度学习模型？现有模型（如 Enformer）仅以 DNA 序列为输入，无法泛化到训练数据中未覆盖的细胞类型。
- **为什么重要**：非编码区调控信息解码是基因组学核心问题。不同细胞类型中相同的 DNA 序列会产生不同的染色质状态和基因表达，理解这种 context-specificity 对解析基因调控机制和疾病变异效应至关重要。
- **现有方法不足**：
  - Enformer 等序列模型只能预测训练中见过的细胞类型，无法外推到新 context；
  - 传统任务特定模型（如 BIRD、ChromDragoNN、DeepCAGE）仅针对单一信号（如 DNase），缺乏多任务联合建模能力；
  - 现有基因组语言模型未利用 3D 染色质互作数据，而 3D 互作是基因调控的关键机制。
- **精确研究问题（Can...?）**：Can a transformer-based model conditioned on TF expression profiles predict context-specific epigenomic signals in unseen cell types, and can its attention mechanism capture regulatory interactions such as enhancer-promoter contacts?

## 04 背景与发展脉络

**发展脉络（经外部核验 + 本文框架）**：

1. **早期调控预测模型**：基于卷积神经网络（CNN）的模型（如 DeepSEA、Basset）以 DNA 序列为输入预测染色质特征，但无法区分细胞类型。
2. **任务特定模型**：BIRD（线性回归）、ChromDragoNN（深度神经网络）、DeepCAGE（密集连接 CNN）开始引入 TF 表达作为辅助输入，但仅针对单一信号（DNase），且未使用 Transformer 架构。
3. **基因组语言模型**：Enformer 将 Transformer 架构引入基因组学，以 32kb 窗口的 DNA 序列为输入预测 5313 个基因组轨道，但**无法预测新细胞类型**，且未纳入 3D 互作信息。
4. **EpiGePT 的位置**：在 Enformer 的 Transformer 架构基础上，创新性地将 TF 表达谱作为条件输入，使模型具备 context-specific 预测能力；同时引入 3D 染色质互作数据作为训练信号，增强模型对长程调控关系的捕捉。这是首个将 TF 表达作为上下文条件、并利用 3D 基因组数据训练的基因组语言模型。

**与 TF–DNA 结合机制课题的关联**：本文的 TF 模块设计（表达 × 结合位点）和 GIS 归因方法，为从表观遗传信号反推 TF 调控关系提供了新思路，可迁移到 TF 结合位点预测和 TF–靶基因关系推断任务。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 无法预测新细胞类型 | Enformer 等模型仅能预测训练中见过的细胞类型，无法外推到新 context | 模型仅以 DNA 序列为输入，缺乏细胞类型信息 | Results 节 "EpiGePT removes this limitation by making both the input and output context-dependent" |
| 3D 互作数据未利用 | 现有基因组语言模型未纳入 Hi-C/HiChIP 数据 | 3D 互作数据难以直接融入序列模型训练 | Results 节 "3D interaction data have not been included in the training of current genomic LLMs" |
| 数据缺失问题 | 不同细胞类型中可用的表观遗传信号集合不同，难以联合训练 | 简单丢弃缺失数据会损失大量训练样本 | Methods 节 masked training strategy 处理缺失数据 |
| 模型可解释性不足 | 深度学习模型难以解释预测背后的调控机制 | 缺乏对模型内部注意力的调控语义解读 | Results 节 利用自注意力权重预测 E-P 互作，GIS 推断 TF 调控关系 |
| 跨物种迁移困难 | 人类训练的模型难以直接应用于其他物种 | TF 表达谱和调控网络存在物种差异 | Results 节 通过零样本学习和微调策略适应小鼠数据 |

## 06 核心思想

**1) 表面方法**：
- 构建四模块架构：序列模块（CNN 提取 DNA 特征）、TF 模块（编码 711 个 TF 的表达谱）、Transformer 模块（自注意力建模长程互作）、预测模块（多任务输出 8 种表观遗传信号）。
- 输入为 128kb DNA 序列 + 细胞类型特异的 TF 表达向量，输出为 1000 个 bin × 8 种表观信号的预测。
- 训练策略：masked training 处理缺失数据；3D 互作数据通过自注意力引导（cosine similarity loss）融入训练。

**2) 核心洞察**：
- **TF 表达作为 context 的桥梁**：将 TF 表达谱作为条件输入，使模型能够将序列信息与细胞类型状态关联起来，从而泛化到新细胞类型——只需提供该细胞类型的 TF 表达数据即可预测其表观遗传状态。
- **自注意力即调控关系**：Transformer 的自注意力权重天然对应序列位置间的调控关联，通过 3D 互作数据引导注意力权重，使模型学到的注意力模式与真实染色质互作一致。
- **梯度归因揭示调控逻辑**：通过计算预测信号对 TF 输入的梯度（GIS），可以推断哪些 TF 对特定基因的调控最重要，实现从预测到机制解释的跨越。

**3) 可能的普适教训 [Analysis]**：
- 在生物序列建模中，将「上下文条件」作为输入而非仅依赖序列本身，是提升模型泛化能力的有效策略——这一思路可迁移到 TF 结合位点预测（以细胞类型特异的 TF 表达为条件）和蛋白质-DNA 对接（以蛋白构象状态为条件）。
- 利用实验数据（如 HiChIP）作为注意力权重的软约束，是一种将结构先验注入 Transformer 的轻量级方法，不改变模型架构即可提升可解释性。

## 07 方法总览

- **输入**：
  - DNA 序列：128kb，one-hot 编码，分为 1000 个 bin（每个 128bp）
  - TF 表达谱：711 个 TF 的 log 转换 + 分位数归一化表达值
  - TF 结合状态：基于 HOCOMOCO motif 扫描的 711 维结合分数
- **输出**：1000 个 bin × 8 种表观遗传信号（DNase、CTCF、H3K27ac、H3K4me3、H3K36me3、H3K27me3、H3K9me3、H3K4me1）
- **模块**：
  1. 序列模块：5 层 1D CNN + maxpooling，将 128kb 序列压缩为 1000 个 token
  2. TF 模块：将 TF 表达 × 结合分数（逐元素乘积）编码为 context 向量
  3. Transformer 模块：16 层编码器，8 头注意力，输入 token 维度 968（序列特征 256 + TF 特征 712）
  4. 预测模块：全连接层，多任务输出
- **训练**：
  - 优化器：Adam，学习率 5×10⁻⁵，batch size 10
  - 损失函数：MSE（回归）+ 交叉熵（分类）+ cosine similarity loss（3D 互作引导，权重 α=2）
  - 总参数量：71.3M
- **文字流程**：DNA 序列经 CNN 提取局部特征 → 与 TF 模块输出的 context 向量拼接 → 输入 Transformer 编码器进行长程建模 → 预测模块输出各 bin 的表观信号。3D 互作数据在训练时通过约束注意力权重（cosine similarity loss）引导模型学习真实的染色质互作模式。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 序列模块（CNN） | 提取 DNA 序列局部特征，压缩长序列 | 将 128kb 序列降维为可处理的 token 序列 | 输入：128kb one-hot 序列；输出：1000×256 特征 | Methods 节 "sequence module...contains five 1-dimentional convolutional blocks" | 预期：模型无法捕捉局部序列模式（如 motif），性能显著下降 [Analysis] |
| TF 模块 | 编码细胞类型特异的 TF 表达和结合状态 | 提供 context 信息，使模型能区分不同细胞类型 | 输入：711 维表达 + 711 维结合分数；输出：712 维 context 向量 | Results 节 "TF module...specifies the state of a few hundred TFs" | 消融实验（EpiGePT-seq）显示跨细胞类型预测性能下降，DNase 预测 PCC 从 0.787 降至 0.74 |
| Transformer 模块 | 建模 bin 间的长程互作关系 | 捕捉增强子-启动子等远距离调控 | 输入：1000×(256+712) token 序列；输出：1000×968 上下文表示 | Methods 节 "16 layers of Transformer encoder with 8 attention heads" | 预期：无法捕捉长程调控，短程 CNN 特征不足以预测 3D 互作 [Analysis] |
| 预测模块 | 多任务输出 8 种表观信号 | 实现多信号联合预测，利用信号间的协同信息 | 输入：Transformer 输出；输出：1000×8 预测值 | Methods 节 "prediction module...linear transformation" | 多任务消融显示联合训练优于单任务（Additional file 1: Fig. S22） |
| 3D 互作引导（CSL） | 约束注意力权重与 HiChIP 数据一致 | 将实验互作数据注入模型，提升注意力可解释性 | 输入：注意力矩阵 + HiChIP 互作矩阵；输出：cosine similarity loss | Methods 节 "cosine similarity loss between the rows of H̃ᵢ and Ãⁱ" | EpiGePT-3D 在 E-P 互作预测上优于无 3D 引导版本（Fig. 3d） |

## 09 关键公式符号

**1) 序列模块特征提取**：
- 输入：one-hot 序列 X ∈ ℝ^(L×4)，L = 128,000
- 经 5 层 CNN + maxpooling 后输出：S ∈ ℝ^(1000×256)

**2) TF 模块特征**：
- TF 表达向量 e ∈ ℝ^711（log 转换 + 分位数归一化）
- TF 结合分数向量 b ∈ ℝ^711（motif 扫描最大分数）
- 组合特征：t = e ⊙ b ∈ ℝ^711（逐元素乘积），padding 后为 712 维

**3) Transformer 输入 token**：
- 第 i 个 bin 的 token：zᵢ = [sᵢ; t] ∈ ℝ^968，其中 sᵢ 为序列特征，t 为 TF context 特征（所有 bin 共享）

**4) 自注意力机制**：
- Attention(Q, K, V) = softmax(QKᵀ/√dₖ)V
- 其中 Q = XW_Q，K = XW_K，V = XW_V，dₖ = d_model/n_h = 968/8 = 121

**5) 3D 互作引导损失（CSL）**：
- L_CSL = 1 - cos(H̃ᵢ, Ãⁱ)，其中 H̃ᵢ 为行归一化的 HiChIP 互作矩阵，Ãⁱ 为平均后的注意力矩阵
- 总损失：L = L_task + α·L_CSL，α = 2

**6) 梯度重要性分数（GIS）**：
- GIS_ijk = (1/|ζ|) Σ_{l∈ζ} |∂ŷ_ljk / ∂tf_ij|
- 其中 ζ 为 TF 有结合位点的 bin 集合，tf_ij 为第 i 个 TF 在第 j 个细胞类型中的表达 × 结合分数

**7) 集成梯度重要性分数（IGIS）**：
- IGIS_ij = (1/8) Σ_k rank(GIS_ijk)，对 8 种表观信号分别排名后取平均

**8) 变异效应分数（LOS）**：
- ΔO_signal = log(output(I_alt) / output(I_ref))
- ΔO_attention = Σ_{i=-5}^{5} |log(attn(bin_i)_I(alt) / attn(bin_i)_I(ref))|

## 10 实验设计与证据链

**数据集与规模**：
- DNase-seq：129 个细胞类型，1,175,374 个基因组区域（ENCODE）
- 多表观信号：28 个细胞类型（hg19），104 个细胞类型（hg38），8 种信号（DNase、CTCF、H3K27ac、H3K4me3、H3K36me3、H3K27me3、H3K9me3、H3K4me1）
- HiChIP：13 个细胞类型的 H3K27ac 互作数据（来自 HiChIPdb）
- 小鼠数据：3 个器官（脑、肺、肾）
- 变异数据：eQTL 数据集（49 个组织，20,913 对因果/非因果变异-基因对）；ClinVar（52,876 致病 SNP + 418,863 良性 SNP）；COVID-19 GWAS（9,484 个变异）

**评估指标**：PCC（Pearson 相关系数）、SCC（Spearman 相关系数）、auROC、auPRC、PSR（预测平方误差）

**评测协议**：五折交叉验证（细胞类型级别划分）；跨细胞类型预测（训练集和测试集细胞类型不重叠）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| DNase 跨细胞类型预测 | EpiGePT 优于任务特定模型 | 对比 BIRD、ChromDragoNN、DeepCAGE、Enformer | 跨细胞类型 PCC 0.787，比 ChromDragoNN 高 6.9% | EpiGePT 在跨细胞类型预测中显著优于基线 | 未提供显著性检验细节 | Results 图 2a-c |
| 多表观信号预测 | EpiGePT 优于 Enformer | 78 个基因组轨道，19 个未见细胞类型 | EpiGePT 平均 PCC 0.510 vs Enformer 0.440 | EpiGePT 在多信号预测中优于 Enformer | 未报告每个信号的详细分解 | Results 图 2d |
| E-P 互作预测（Setting A） | 自注意力分数可预测 E-P 互作 | 使用预训练模型注意力分数 vs Enformer | EpiGePT auPRC 0.647-0.887（不同距离组） | 注意力分数捕捉增强子-启动子互作 | 仅限 K562 细胞系 | Results 图 3a |
| E-P 互作预测（Setting B/C） | 3D 数据引导提升互作预测 | EpiGePT vs EpiGePT-3D vs 微调版本 | EpiGePT-3D 在 K562 上 auPRC 从 0.652 提升至 0.695（24-40kb 组） | 3D 数据引导提升互作预测 | 仅测试了 K562 和 GM12878 | Results 图 3d, 3h |
| GIS 验证 TF-TF 互作 | GIS 识别已知 TF 调控关系 | POU5F1 和 ESRRB 的 GIS 排名 vs ChIP-seq 验证 | ESRRB 的 POU5F1 排名第 3/711；ChIP-seq 重叠 bin 的 GIS 显著更高 | GIS 有效识别已知调控 TF | 仅验证了少数 TF | Results 图 4a-b |
| TF-TG 数据库验证 | GIS 排名优于表达量排名 | TRRUST（2705 对）和 GRNdb（1066 对） | GIS 中位排名百分位 3.1% vs 表达量 20.4% | GIS 比单纯表达量更准确识别 TF-TG 关系 | 依赖数据库的完整性 | Results 图 4e |
| 变异效应预测 | EpiGePT 特征提升致病 SNP 分类 | EpiGePT 特征 + CADD vs 仅 CADD | auROC 从 0.772 提升至 0.806（1:1 比例） | EpiGePT 特征补充 CADD 提升变异分类 | 未与其他深度学习方法对比 | Results 图 5c |
| COVID-19 SNP 优先级 | EpiGePT 识别 COVID-19 相关 SNP | 肺组织表达作为 context | 平均排名 0.250（随机为 0.5） | EpiGePT 有效优先 COVID-19 相关 SNP | 缺乏实验验证 | Results 图 5d |
| 消融实验 | 各模块均有贡献 | 移除 TF 模块、序列模块、多任务 | TF 模块移除后 PCC 从 0.787 降至 0.74；多任务移除后平均 PCC 下降 0.074 | 所有模块对性能均有贡献 | 未报告所有组合的消融 | Results 图 S22 |
| 跨物种迁移 | EpiGePT 可迁移至小鼠 | 零样本 + 微调 | 微调后 PCC 提升 18.1-19.5% | EpiGePT 可跨物种迁移 | 仅测试了 3 个器官 | Results 图 S10 |

## 11 结论正确解读

- **任务范围**：本文的结论仅限于**表观遗传信号预测**（DNase、组蛋白修饰、CTCF 结合），而非直接的 TF–DNA 结合亲和力预测。模型预测的是染色质状态，TF 表达作为 context 条件输入。
- **Oracle/真值输入**：模型依赖 TF 表达数据作为输入条件。在预测新细胞类型时，需要提供该细胞类型的 TF 表达谱（通常来自 RNA-seq），这在实际应用中可能构成瓶颈——如果目标细胞类型没有 RNA-seq 数据，则无法进行预测。
- **端到端状态**：模型是端到端训练的，但 3D 互作引导（CSR）是辅助损失，不改变模型架构。E-P 互作预测需要额外提取注意力权重，并非模型直接输出。
- **算力成本**：总参数量 71.3M，作者声称可在单张 GPU 上训练和推理（Additional file 1: Text S11），但未提供具体训练时间。
- **历史数据依赖**：模型在 ENCODE 数据上训练，其泛化能力受限于训练数据的细胞类型覆盖范围。虽然声称可预测新细胞类型，但前提是新细胞类型的 TF 表达谱与训练数据分布相似。
- **最难情况**：跨物种迁移（小鼠）需要微调才能达到较好性能；零样本性能有限（PCC 0.330-0.422）。
- **不确定性**：未报告预测的置信区间或不确定性估计；变异效应预测依赖下游分类器（随机森林/MLP），EpiGePT 本身不直接输出致病性分数。
- **有边界的复述**：EpiGePT 是一个以 DNA 序列和 TF 表达为输入的 Transformer 模型，能够在**提供目标细胞类型 TF 表达谱**的条件下，跨细胞类型预测 8 种表观遗传信号，并利用注意力权重和梯度归因推断调控关系；其性能在多个基准上优于现有方法，但跨物种泛化需要微调，且预测质量受 TF 表达数据可用性限制。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未纳入染色质调控因子（CRs） | TF 模块仅包含 711 个 TF，未考虑其他反式作用因子 | 将 CRs 纳入 TF 模块以增强调控建模 | Discussion 节 "incorporation of chromatin regulators (CRs) as trans-acting factors" |
| 未整合 DNA 甲基化信息 | 模型仅基于 DNA 序列和 TF 表达，未利用甲基化数据 | 整合 DNA 甲基化信息以更全面解码表观基因组 | Discussion 节 "integration of DNA methylation information" |
| 未利用单细胞数据 | 模型基于 bulk 数据训练，无法捕捉单细胞水平的调控异质性 | 将单细胞数据作为 pseudo-bulk 数据整合 | Discussion 节 "Integrating single-cell level data into EpiGePT as pseudo-bulk data" |
| 3D 基因组数据有限 | 仅 13 个细胞类型有 HiChIP 数据，限制了 3D 引导训练 | 通过 3D 基因组生成模型填补缺失数据 | Discussion 节 "imputing the missing 3D genome data through 3D genome data generative models" |
| 跨物种应用受限 | 直接迁移到植物、真菌等物种效果有限 | 探索跨物种迁移策略 | Discussion 节 "limitations when applying it across species" |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 跨细胞类型预测的评估方式 | 五折交叉验证中细胞类型随机划分，但相近的细胞类型（如不同血液细胞）可能共享大量调控特征，导致性能被高估 | 如果测试细胞类型与训练细胞类型高度相似，则"跨细胞类型"的泛化能力被夸大 | 按细胞谱系（如造血、上皮、神经）划分训练/测试集，评估谱系间泛化 | Methods 节 "five-fold cross-validation on cell-type level" |
| TF 表达作为 context 的因果性 | 模型使用 TF 表达预测染色质状态，但 TF 表达与染色质状态可能存在反向因果或混淆因素 | 模型学到的"TF→染色质"关系可能不是因果性的，而是相关性 | 使用 TF 扰动实验数据（如 TF 敲低/过表达后的染色质变化）验证模型预测 | Results 图 4 GIS 验证部分 |
| 注意力权重作为互作证据 | 自注意力权重与 HiChIP 互作的一致性可能源于序列距离等混淆因素，而非真实调控关系 | 注意力可解释性结论可能过度解读 | 与随机序列的注意力分布对比，控制序列距离效应 | Results 图 3c, 3f |
| GIS 验证的局限性 | GIS 验证仅使用 ChIP-seq 重叠和数据库已知关系，可能存在选择偏差 | 对未知调控关系的发现能力未被充分验证 | 在多个细胞类型中系统验证 GIS 预测的新 TF-TG 关系 | Results 图 4 |
| 与 Enformer 的比较公平性 | EpiGePT 使用了 TF 表达作为额外输入，而 Enformer 仅用序列，比较条件不对等 | 性能提升可能主要来自额外输入信息而非模型架构优势 | 为 Enformer 添加 TF 表达输入，进行公平对比 | Results 图 2b, 2d |
| 变异效应预测的临床相关性 | 使用 CADD 分数作为特征可能引入循环论证，因为 CADD 本身包含表观基因组注释 | 变异预测的增量贡献可能被高估 | 使用不依赖 CADD 的独立特征集进行对比 | Results 图 5c |
| 模型对 TF 表达数据质量的敏感性 | 未系统评估 TF 表达数据噪声对预测性能的影响 | 实际应用中 RNA-seq 数据可能存在批次效应和噪声 | 在 TF 表达数据中添加噪声，评估性能下降曲线 | 未提供 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **上下文条件化是跨细胞类型泛化的关键**：EpiGePT 的核心创新在于将 TF 表达谱作为条件输入，而非仅依赖 DNA 序列。这一思路可直接迁移到 TF–DNA 结合预测任务——以细胞类型特异的 TF 表达为条件，预测 TF 结合位点的细胞类型特异性，解决传统 motif 扫描无法区分细胞类型的问题。

2. **3D 互作数据可作为注意力权重的软约束**：通过 cosine similarity loss 将 HiChIP 互作数据注入注意力权重训练，是一种轻量级的知识注入方法。在 TF–DNA 互作建模中，可类似地将 ChIA-PET、HiChIP 等 3D 互作数据作为辅助损失，引导模型学习真实的远程调控关系。

3. **梯度归因（GIS）作为调控关系推断工具**：GIS 通过计算预测信号对 TF 输入的梯度来排名 TF 的重要性，无需额外训练即可推断 TF–靶基因关系。这一方法可迁移到 TF 结合位点预测模型，用于解释哪些 TF 的 expression 变化对特定基因组位点的结合影响最大。

4. **Masked training 处理缺失表观数据**：不同细胞类型可用的表观信号集合不同，EpiGePT 通过 masked loss 处理缺失数据，最大化利用可用训练样本。在整合多来源 TF 结合数据（如不同实验室的 ChIP-seq）时，这一策略可有效处理数据不完整性问题。

5. **跨物种迁移需要微调**：EpiGePT 从人类迁移到小鼠需要微调才能达到较好性能，提示在 TF–DNA 互作建模中，跨物种迁移不能依赖零样本学习，需要设计物种适配层或微调策略。

6. **多任务联合训练提升单任务性能**：EpiGePT 同时预测 8 种表观信号，利用信号间的协同信息提升整体性能。在 TF–DNA 互作建模中，可联合预测 TF 结合、染色质可及性、组蛋白修饰等多种相关信号，利用任务间的生物学关联提升预测精度。

## 15 与已有知识连接

- **Enformer（Avsec et al., 2021, Nature Genetics）**：EpiGePT 直接继承并改进了 Enformer 的 Transformer 架构，核心区别在于加入 TF 表达作为条件输入。两者对比表明，序列信息 + 上下文条件的组合优于纯序列模型。
- **ChromDragoNN（Zhang et al., 2019）**：早期引入 TF 表达预测染色质可及性的深度模型，EpiGePT 在架构（Transformer vs CNN）和规模（711 TF vs 1630 TF）上均有升级。
- **DeepCAGE（Li et al., 2019）**：密集连接 CNN 预测染色质可及性，EpiGePT 在跨细胞类型泛化能力上优于此类任务特定模型。
- **BIRD（Zhou et al., 2018）**：线性回归模型，仅利用基因表达预测 DNase 信号，EpiGePT 通过深度学习架构显著提升性能。
- **DeepTACT（Li et al., 2020）**：预测增强子-启动子互作的深度模型，EpiGePT 的 Setting C 微调策略与之对比，展示了预训练模型在互作预测上的优势。
- **CADD（Rentzsch et al., 2019）**：变异致病性预测工具，EpiGePT 将其分数作为特征之一，展示了表观预测与变异解读的整合思路。
- **TF–DNA 结合预测方向**：本文的 GIS 方法与传统的 motif 扫描（如 HOMER）和基于位置的权重矩阵（PWM）方法形成互补——从表达梯度而非序列 motif 角度推断 TF 调控关系，为结合机制研究提供了新视角。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合亲和力的上下文条件化预测模型
   - **来源局限/观察**：EpiGePT 预测的是染色质状态而非直接的 TF–DNA 结合亲和力；现有 TF 结合预测模型（如 DeepBind、DeepSEA）缺乏细胞类型上下文。
   - **核心假设**：以 TF 表达为条件输入，可提升 TF 结合位点预测的细胞类型特异性。
   - **初步方法**：在 EpiGePT 框架基础上，将输出层改为 TF 结合事件（ChIP-seq peak）预测，以 711 个 TF 的表达谱为条件，联合预测多个 TF 在给定细胞类型中的结合。
   - **验证方式**：在 ENCODE ChIP-seq 数据上评估跨细胞类型 TF 结合预测性能，与 DeepBind、Enformer 对比。
   - **创新状态**：unverified

2. **候选名称**：基于自注意力权重的 TF–增强子–启动子三元互作推断
   - **来源局限/观察**：EpiGePT 的注意力权重可预测 E-P 互作，但未系统分析 TF 在其中的中介作用。
   - **核心假设**：注意力权重中可分解出 TF 介导的增强子-启动子互作信号。
   - **初步方法**：对 EpiGePT 的注意力头进行聚类分析，识别与特定 TF 结合模式相关的注意力头；结合 TF motif 位置信息，构建 TF-增强子-启动子三元互作图。
   - **验证方式**：与 HiChIP、ChIA-PET 实验数据对比，评估预测的互作是否富集已知 TF 靶基因。
   - **创新状态**：unverified

3. **候选名称**：结合 MD 模拟的 TF–DNA 结合变异效应预测
   - **来源局限/观察**：EpiGePT 的变异效应预测基于表观信号变化，未考虑 TF–DNA 结合的物理化学机制。
   - **核心假设**：将 EpiGePT 的表观预测与 MD 模拟的结合自由能变化结合，可提升对 TF 结合破坏性变异的预测精度。
   - **初步方法**：对 EpiGePT 预测的高影响变异进行 MD 模拟（如利用 AlphaFold 预测 TF–DNA 复合物结构后做结合自由能计算），将物理模拟特征与 EpiGePT 的表观特征融合。
   - **验证方式**：在 ClinVar 致病 SNP 和 eQTL 数据集上评估融合模型的分类性能。
   - **创新状态**：unverified

4. **候选名称**：单细胞分辨率的 TF–DNA 互作预测
   - **来源局限/观察**：EpiGePT 使用 bulk RNA-seq 的 TF 表达，无法捕捉单细胞水平的调控异质性。
   - **核心假设**：以单细胞 TF 表达为条件输入，可预测单细胞水平的染色质状态和 TF 结合。
   - **初步方法**：利用 scRNA-seq 数据构建单细胞 TF 表达谱，输入 EpiGePT 框架预测单细胞染色质可及性，与 scATAC-seq 数据对比验证。
   - **验证方式**：在人类细胞图谱数据上评估单细胞水平预测精度。
   - **创新状态**：unverified

5. **候选名称**：TF 表达梯度与 DNA 序列变异的交互效应建模
   - **来源局限/观察**：EpiGePT 的 GIS 仅考虑 TF 表达对表观信号的梯度，未建模 TF 表达 × 序列变异的交互效应。
   - **核心假设**：某些序列变异仅在特定 TF 表达背景下才影响表观状态（即 G×E 交互）。
   - **初步方法**：在 EpiGePT 框架中引入 TF 表达 × 序列 embedding 的交互项，或在 GIS 计算中考虑二阶导数。
   - **验证方式**：在 eQTL 数据中检验交互效应是否富集于 EpiGePT 预测的高交互区域。
   - **创新状态**：unverified