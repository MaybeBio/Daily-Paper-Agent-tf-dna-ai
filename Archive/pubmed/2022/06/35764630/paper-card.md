## 01 基本信息

- **标题**: Learning representations of chromatin contacts using a recurrent neural network identifies genomic drivers of conformation
- **作者与单位**: Dsouza, Kevin B; Maslova, Alexandra; Al-Jibury, Ediem; Merkenschlager, Matthias; Bhargava, Vijay K; Libbrecht, Maxwell W（单位未在摘要中提供）
- **期刊/预印本平台**: Nature Communications
- **年份**: 2022-06-29
- **论文类型**: 方法学（深度学习模型开发 + 生物学验证）
- **领域**: 三维基因组学 / 染色质构象 / 表示学习
- **关键词**: Hi-C, LSTM, representation learning, chromatin conformation, CTCF, Cohesin, in-silico perturbation
- **DOI/arXiv 号**: 10.1038/s41467-022-31337-w
- **代码**: GitHub 仓库（Methods 节提及，具体 URL 未在摘要中提供）
- **数据**: GM12878, H1-hESC, HFF-hTERT, WTC11 的 Hi-C 数据（来自 4DN Data Portal 及 Rao et al.）
- **阅读日期**: 未提供
- **在课题方向中的位置**: 本文属于「AI 方法 × 染色质构象」方向，核心创新在于用 LSTM 对 Hi-C 接触矩阵进行表示学习，生成位点特异性低维嵌入，并用于识别构象驱动元件（CTCF、Cohesin 等）。与 TF–DNA 互作课题的关联在于：其表示学习方法可迁移至 TF 结合位点的构象上下文建模，其 in-silico 扰动框架可类比 TF 结合位点突变对构象影响的预测。

## 02 一句话总结

本文提出 Hi-C-LSTM，用 LSTM 循环神经网络将每条染色体的 Hi-C 接触矩阵压缩为每位点的低维表示向量，通过联合优化表示与解码器重建接触矩阵，所得表示可分类基因组元件、识别构象驱动 TF（CTCF、Cohesin 等），并支持 in-silico 模拟重复、敲除和方向替换实验，在 SOX9 2.1 Mb 重复变异中正确预测了实验观察到的 neo-TAD 结构。

## 03 研究问题

- **具体问题**: 如何从 Hi-C 接触矩阵中学习每位点的低维表示，使得该表示既能忠实重建接触图谱，又能用于识别驱动 3D 构象的基因组元件（如 TF 结合位点、TAD 边界）？
- **为什么重要**: 1D 基因组如何决定 3D 构象是理解基因表达调控和疾病机制的核心问题。现有方法（如 PCA、SNIPER、SCI）要么只利用染色体间接触（丢失重要的染色体内结构信息），要么不利用基因组的序列特性，导致表示信息不完整。
- **现有方法不足**:
  - SNIPER 仅使用染色体间接触，无法捕捉 TAD、loop 等染色体内结构。
  - SCI 虽使用染色体内接触，但未考虑基因组的序列性（sequential nature），即相邻位点的表示应具有连续性。
  - PCA 等线性方法无法捕捉非线性、层级化的构象特征。
- **精确研究问题 (Can...?)**: Can a recurrent neural network that treats the genome as a sequence learn latent representations of intra-chromosomal Hi-C contacts that (a) reconstruct the contact matrix more accurately than existing methods, and (b) identify genomic elements (CTCF/Cohesin binding sites, TAD boundaries) that drive 3D conformation?

## 04 背景与发展脉络

*注：以下脉络基于本文框架，未经外部核验。*

1. **PCA 时代（Lieberman-Aiden et al., 2009）**：用 Hi-C 矩阵第一主成分划分 A/B compartment。局限：线性、仅捕捉全局趋势，无法定位局部元件。
2. **隐马尔可夫模型（Imakaev et al.）**：改进 compartment 分类，但仍为线性方法。
3. **表示学习方法（SNIPER, SCI）**：
   - SNIPER：全连接自编码器，输入为染色体间接触，输出低维表示。局限：忽略染色体内接触。
   - SCI：图嵌入方法，利用染色体内接触，但未利用序列性。
4. **Hi-C 预测方法（Akita 等）**：从序列预测接触，但不产生位点表示，且无法直接用于元件识别。
5. **本文位置**：首次将 LSTM 应用于 Hi-C 表示学习，将基因组视为序列，利用循环网络的序列归纳偏置（sequential inductive bias）学习每位点的表示，同时实现高精度重建和元件识别。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有表示方法忽略染色体内接触 | SNIPER 仅用染色体间接触，无法捕捉 TAD/loop 结构 | 作者指出 SNIPER 的设计初衷是补全稀疏的染色体间矩阵，而非建模染色体内结构 | Results 节 "SNIPER takes only inter-chromosomal contacts as input" |
| 现有方法未利用基因组序列性 | SCI 将 Hi-C 视为图，位点间无顺序关系 | 作者认为基因组是线性序列，相邻位点的构象特征应连续变化，图模型无法捕捉 | Results 节 "do not account for the inherent sequential nature of the genome" |
| 表示信息量不足 | 现有表示无法同时支持高精度重建和元件分类 | 作者认为非序列模型的信息瓶颈导致表示缺乏局部结构信息 | Results 节 "limits existing methods' informativeness" |
| 无法进行可靠的 in-silico 扰动 | 现有方法无法模拟位点删除/重复对构象的影响 | 表示与解码器未联合优化，扰动表示无法产生有意义的构象变化 | Results 节 "enables in-silico perturbation experiments" |

## 06 核心思想

### 1) 表面方法
- 用 LSTM 作为解码器，将位点表示向量序列作为输入，逐位点重建 Hi-C 接触向量。
- 表示向量（embedding）与 LSTM 参数通过最小化重建误差（MSE）联合优化。
- 训练完成后，每位点的表示向量可直接用于下游分类任务（基因表达、增强子、TAD 等）。

### 2) 核心洞察
- **基因组是序列，不是图**：Hi-C 矩阵的每一行（某位点对所有其他位点的接触）可视为该位点的"构象签名"，而相邻位点的签名应平滑变化。LSTM 的循环结构天然适合建模这种序列依赖性。
- **表示即解释**：通过联合优化重建损失，表示被迫编码所有影响接触的生物学因素（CTCF 结合、compartment 状态、TAD 归属等），因此表示本身即可用于元件识别。
- **扰动即实验**：由于表示是输入，修改表示（删除、重复、替换）后通过解码器生成新接触矩阵，即可模拟基因组变异对构象的影响。

### 3) 可能的普适教训 [Analysis]
- 对于基因组线性数据（如 Hi-C、ChIP-seq、甲基化），显式建模序列性（RNN/CNN/Transformer）通常优于无序模型（图嵌入、全连接）。
- 联合优化表示与解码器（而非两阶段训练）能迫使表示保留更多可解释信息。
- In-silico 扰动实验的价值在于：它提供了一种无需湿实验即可检验"表示是否真正编码生物学机制"的手段。

## 07 方法总览

- **输入**：N×N 染色体内 Hi-C 接触矩阵（每个染色体独立处理），已转换为接触概率（0-1）。
- **输出**：每位点的 K 维表示向量（K=16，经超参数选择）；以及重建的 Hi-C 矩阵。
- **模块**：
  1. **Embedding 层**：将位点 ID 映射为 K 维向量（可学习参数）。
  2. **LSTM 解码器**：单层、单向、带 layer normalization；输入为表示向量序列，输出为预测的接触概率向量。
  3. **损失函数**：MSE（预测接触概率 vs 观测接触概率）。
- **训练**：PyTorch 实现，Adam 优化器，学习率 0.01（5 epochs）→ 0.001（5 epochs），batch size 2000，序列长度 150 位点（1.5 Mb 窗口）。
- **下游任务**：
  - 分类：基因表达、复制时间、增强子、TAD、subTAD、loop、subcompartment 等（XGBoost 或线性分类器）。
  - 特征归因：Integrated Gradients 计算每位点对接触预测的贡献。
  - In-silico 扰动：删除/重复/替换表示向量，通过解码器预测新接触矩阵。
- **反馈回路**：无显式反馈回路；训练为一次性联合优化。
- **假设**：Hi-C 接触矩阵可被低维表示 + 序列解码器充分重建；表示向量编码了所有构象相关生物学信息。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Embedding 层 | 将位点 ID 映射为 K 维向量 | 将离散位点转化为连续可优化表示 | 输入：位点 ID；输出：K 维向量 | Results 节 "representation matrix R ∈ R^(N×M)" | 预期影响：表示无法学习，模型退化为纯序列模型（预期，未实测） |
| LSTM 解码器 | 从表示序列重建接触向量 | 利用序列性建模接触的平滑变化 | 输入：表示序列 (R_i, R_j)；输出：预测接触概率 | Results 节 "LSTM that takes these representations as input" | 实测：LSTM 解码器比 CNN/FC 重建精度高（Results 图 3a） |
| Layer normalization | 稳定 LSTM 训练 | 防止梯度消失/爆炸 | 输入：LSTM 隐状态；输出：归一化隐状态 | Methods 节 "unidirectional layer norm LSTM" | 预期影响：训练不稳定，收敛慢（预期，未实测） |
| 联合优化（表示+解码器） | 同时学习表示与解码参数 | 迫使表示保留重建所需全部信息 | 输入：Hi-C 矩阵；输出：重建矩阵 | Results 节 "jointly trained to minimize the reconstruction error" | 实测：联合优化优于两阶段训练（Results 图 3a 对比） |
| Integrated Gradients | 计算位点对接触预测的贡献 | 识别构象驱动元件 | 输入：表示向量；输出：归因分数 | Results 节 "Feature attribution" | 预期影响：无法定位关键位点（预期，未实测） |
| In-silico 扰动模块 | 修改表示并预测新接触矩阵 | 模拟基因组变异效应 | 输入：修改后的表示矩阵；输出：预测接触矩阵 | Results 节 "In-silico perturbation" | 预期影响：无法进行变异模拟（预期，未实测） |

## 09 关键公式符号

1. **接触概率转换**（Methods 节，Eq. 1）：
   - cf = 1/(v + δ)，其中 v 为原始接触强度，δ = 10⁻¹⁰
   - CP = exp(-a × cf)，其中 a = 8（系数乘子）
   - 用途：将原始 Hi-C 计数转换为 0-1 概率，稳定训练。

2. **LSTM 单元**（Methods 节，Eq. 2）：
   - f_t = σ(W_f x_t + U_f h_{t-1} + b_f)（遗忘门）
   - i_t = σ(W_i x_t + U_i h_{t-1} + b_i)（输入门）
   - o_t = σ(W_o x_t + U_o h_{t-1} + b_o)（输出门）
   - c_t = f_t ∘ c_{t-1} + i_t ∘ σ(W_c x_t + U_c h_{t-1} + b_c)（细胞状态）
   - h_t = o_t ∘ σ(c_t)（隐状态）
   - 其中 ∘ 为 Hadamard 积，σ 为 sigmoid 激活。

3. **预测模型**（Methods 节，Eq. 3）：
   - Ĥ_{i,j} = LSTM((R_i, R_j), h_j, c_j)，对 j = 1, 2, ..., N，对 i = 1, 2, ..., N
   - 用途：给定位点 i 和 j 的表示，预测接触概率。

4. **损失函数**（Methods 节，Eq. 4）：
   - MSE_i = (1/N) Σ_{j=1}^{N} (H_{i,j} - Ĥ_{i,j})²
   - 用途：最小化重建误差，联合优化表示与解码器。

5. **Integrated Gradients 归一化**（Methods 节，Eq. 5）：
   - IG_norm = (IG - IG_min) / (IG_max - IG_min)
   - 用途：将归因分数归一化到 [0,1]，便于跨位点比较。

## 10 实验设计与证据链

**数据集与资源**：
- Hi-C 数据：GM12878（~30 亿过滤 reads）、H1-hESC（~9 亿）、HFF-hTERT（~1.5 亿）、WTC11（~2.16 亿）
- 分辨率：10 kbp（主要）、2/100/500 kbp（多分辨率实验）
- 参考基因组：hg19
- 基因表达数据：GM12878 和 H1-hESC 的 RNA-seq
- 元件注释：增强子、TAD、subTAD、loop、subcompartment 等（来源未在摘要中详述）
- 5C 数据：TAL1 和 LMO2 位点（HEK-293T，Hnisz et al.）

**指标**：
- 重建精度：R²（预测 vs 观测接触概率）
- 分类精度：平均精度均值（mAP）、AUC、F1、准确率
- 扰动验证：预测接触变化与实验观测的相关性

**对比方法**：SNIPER（inter/intra）、SCI、PCA、subcompartment-ID（SBCID）

**实验表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 重建精度（图 3a-d） | LSTM 表示能更准确重建 Hi-C | Hi-C-LSTM vs SNIPER-FC vs SCI-LSTM，4 种细胞类型 | Hi-C-LSTM 平均 R² 比 SNIPER 高 10%，比 SCI 高 12% | LSTM 解码器 + 序列性建模提升重建精度 | 未证明 LSTM 是唯一最优架构 | Results 图 3a-d |
| 跨复制一致性（图 3b） | 表示捕捉真实生物学而非噪声 | 训练于 rep1，测试于 rep2 | R² 略降但趋势保持 | 表示具有生物学可重复性 | 未量化噪声贡献 | Results 图 3b |
| 元件分类（图 4a-b） | 表示编码功能基因组状态 | 基因表达、增强子、TAD 等 8 类任务 | Hi-C-LSTM 在多数任务上 mAP 最高 | 表示包含功能相关信息 | 分类性能受限于训练数据质量 | Results 图 4a-b |
| 多分辨率（图 5） | 模型在不同分辨率下均有效 | 2/10/100/500 kbp | 各分辨率均能重建，但元件分类性能随分辨率变化 | 模型具有尺度适应性 | 未系统比较分辨率间信息差异 | Results 图 5 |
| 特征归因（图 6） | 归因分数识别构象驱动元件 | Integrated Gradients vs CTCF/Cohesin ChIP-seq | 归因分数在 CTCF/Cohesin 位点显著升高 | 表示编码了 TF 结合信息 | 归因分数与结合强度的定量关系未验证 | Results 图 6 |
| SOX9 重复模拟（图 7） | 模型能预测结构变异效应 | 模拟 2.1 Mb 串联重复 vs 实验 Hi-C | 预测的 neo-TAD 与实验一致 | 模型可用于 in-silico 变异预测 | 仅验证了一个位点 | Results 图 7 |
| TAL1/LMO2 敲除（图 9） | 模型能预测锚点删除效应 | 模拟锚点删除 vs 5C 实验 | 预测与实验显著相关（TAL1 强，LMO2 中等） | 模型可预测 cis 敲除效应 | LMO2 预测精度有限 | Results 图 9 |

## 11 结论正确解读

- **任务范围**: 本文仅针对 bulk Hi-C 的染色体内接触，不涉及单细胞 Hi-C、HiChIP 等其他构象捕获技术。模型预测的是"接触概率"而非"3D 结构坐标"。
- **Oracle/真值输入**: 训练时使用观测 Hi-C 矩阵作为重建目标；分类任务使用外部注释（基因表达、ChIP-seq 等）作为标签。无 oracle 输入。
- **端到端状态**: 模型是端到端训练的（表示+解码器联合优化），但下游任务（分类、归因）是训练后独立进行的，非端到端。
- **算力成本**: 未在摘要中提供具体训练时间/GPU 数量；提及使用 GeForce GTX 1080 Ti，但未给出总耗时。
- **历史数据依赖**: 模型仅依赖 Hi-C 数据本身，不依赖序列或表观遗传数据；但分类任务依赖外部注释数据。
- **模型依赖**: 性能受 Hi-C 数据质量（测序深度）影响显著；低深度数据（如 HFF-hTERT）性能下降。
- **最难情形**: 长距离相互作用（>10 Mb）和 subcompartment 分类是模型表现最弱的任务。
- **群体/领域边界**: 模型在人类细胞系（GM12878, H1-hESC, HFF-hTERT, WTC11）上验证，未测试其他物种。仅适用于有配对端 Hi-C 数据的位点。
- **不确定性**: 预测的接触变化是"相对趋势"而非绝对定量；LMO2 位点的预测精度有限，说明模型对某些位点类型的泛化能力有限。

**有边界的复述**: 在人类 4 种细胞系的 bulk Hi-C 数据上，Hi-C-LSTM 能以高于现有方法的精度重建染色体内接触矩阵，其表示向量可分类多种基因组元件，并能通过 in-silico 扰动预测 cis 变异（重复、敲除、方向替换）对构象的影响，但仅限 cis 效应，无法模拟 trans 效应（如 TF 蛋白耗竭）。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 仅能模拟 cis 效应 | 无法模拟 trans 效应（如 RAD21、CTCF 蛋白耗竭） | 未明确提及 | Discussion 节 "Hi-C-LSTM can model only cis effects" |
| 无法利用单细胞 Hi-C 数据 | 模型输入为 bulk Hi-C 矩阵 | 未明确提及 | Discussion 节 "Hi-C-LSTM cannot utilize single-cell Hi-C data" |
| 短帧长限制长距离相互作用 | 帧长 150 位点（1.5 Mb），无法捕捉 >1.5 Mb 的相互作用 | 计划使用 Transformer 等长序列模型 | Discussion 节 "In future work, we plan to work with longer sequences efficiently" |
| 低测序深度下性能下降 | R² 随 reads 减少而降低 | 未明确提及 | Results 节 "sequencing depth and model performance" |
| 无标准 in-silico 敲除方法 | 四种敲除方法各有局限，无公认最优 | 未明确提及 | Discussion 节 "there is no accepted standard way of simulating in-silico knockout" |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| LSTM 优于 CNN/FC 的结论可能受限于比较公平性 | 三种方法的参数量、训练策略是否完全对齐未说明 | 若 CNN/FC 未充分调参，LSTM 的优势可能被夸大 | 检查补充材料中三种方法的参数量、训练 epoch、学习率是否一致 | Results 图 3a 仅给出 R² 差异，未给出模型复杂度对比 |
| 表示向量维度 K=16 的选择依据 | 未提供 K 的消融实验 | K 过小可能丢失信息，过大可能过拟合 | 检查补充材料是否有 K 的敏感性分析 | Methods 节仅提及 "representation size of 16" 为超参数选择结果 |
| In-silico 敲除的验证仅依赖相关性 | 相关性高不等于因果正确 | 模型可能捕捉了与敲除效应相关的混淆因素 | 检查是否与 CRISPR 实验或已知突变数据对比 | Results 图 9 仅给出相关性，未给出因果验证 |
| 特征归因分数与 TF 结合强度的关系未定量 | 仅比较了有/无结合位点的均值差异 | 无法区分"强结合"与"弱结合"位点的构象贡献 | 检查归因分数是否与 ChIP-seq 信号强度相关 | Results 图 6 仅给出分组比较，未给出连续相关性 |
| 模型仅验证了 4 种细胞系 | 未测试其他物种或疾病状态 | 泛化能力未知 | 检查是否有跨物种或疾病样本的验证 | Results 节仅提及 4 种细胞系 |
| 与 Akita 等序列预测方法未直接比较 | 本文聚焦表示学习，但未与序列→构象预测方法对比 | 无法判断表示学习 vs 序列建模的相对优势 | 检查是否与 Akita 在相同任务上比较 | Introduction 节提及 Akita 但未在 Results 中比较 |

## 15 与已有知识连接

- **Hi-C 数据分析**：本文与 Lieberman-Aiden et al. (2009) 的 PCA 方法、Imakaev et al. 的改进方法一脉相承，但用深度学习替代线性降维。可连接至 Rao et al. (2014) 的 TAD/loop 注释，作为分类任务的 ground truth。
- **表示学习**：本文与 SNIPER (Xiong et al.)、SCI (Ashoor et al.) 同属 Hi-C 表示学习范畴，但首次引入序列模型。可连接至自然语言处理中的 word2vec/ELMo 思想——位点表示类似于词嵌入，LSTM 类似于语言模型。
- **深度学习架构**：LSTM 的选择与基因组序列的线性特征相关，可连接至 Akita (Fudenberg et al.) 的 CNN 方法、Enformer 的 Transformer 方法，形成架构演进脉络。
- **可迁移至 TF–DNA 互作课题**：
  - 表示学习方法可直接迁移：将 TF ChIP-seq 峰所在的位点表示作为特征，用于预测 TF 结合强度或结合协同性。
  - In-silico 扰动框架可迁移：模拟 TF 结合位点突变（敲除、替换）对局部染色质构象的影响，预测突变是否破坏 TAD/loop 结构。
  - Integrated Gradients 归因可迁移：识别对构象贡献最大的 TF 结合位点，优先验证候选 TF。
  - 序列性建模思想可迁移：TF 结合位点沿基因组的分布具有序列性，LSTM/Transformer 可捕捉 TF 簇的协同效应。

## 16 研究想法

### 候选 1: TF–DNA 结合位点的构象上下文表示学习
- **名称**: TF-Context-LSTM
- **来源局限/观察**: Hi-C-LSTM 的表示仅基于接触数据，未整合 TF 结合信息；而 TF 结合位点的构象影响可能依赖于其局部序列上下文。
- **核心假设**: 将 TF ChIP-seq 峰、motif 序列与 Hi-C 表示联合嵌入，可提高 TF 结合位点对构象影响的预测精度。
- **初步方法**: 在 Hi-C-LSTM 框架中增加 TF 结合特征通道（如 motif 存在、ChIP-seq 信号强度），联合训练表示与解码器；用 Integrated Gradients 分析 TF 特征对接触预测的贡献。
- **验证方式**: 在 GM12878 上比较有/无 TF 特征通道的构象重建精度；用已知 TF 敲除实验（如 CTCF 耗竭）验证预测的构象变化。
- **创新状态**: unverified

### 候选 2: TF 结合位点突变的 in-silico 构象预测
- **名称**: TF-Mut-Contact
- **来源局限/观察**: Hi-C-LSTM 已验证重复和敲除的模拟，但未针对单核苷酸变异（SNV）或小插入缺失（indel）进行预测。
- **核心假设**: 在 TF 结合位点引入 SNV 后，修改对应位点的表示向量，可预测突变对局部构象（TAD 边界、loop 强度）的影响。
- **初步方法**: 对 CTCF motif 内的每个碱基引入 SNV，重新生成表示并预测接触矩阵；比较突变前后接触概率差异，与已知致病突变（如癌症相关 SNV）的构象表型对比。
- **验证方式**: 使用 ClinVar 或 COSMIC 中位于 CTCF motif 的 SNV，检查预测的构象变化是否与疾病关联。
- **创新状态**: unverified

### 候选 3: 多尺度表示聚合用于 TF 协同性分析
- **名称**: MultiScale-TF-Contact
- **来源局限/观察**: Hi-C-LSTM 在单一分辨率（10 kbp）下训练，但 TF 协同作用可能跨越不同尺度（如 CTCF 成对 loop 在 100 kb-1 Mb 尺度）。
- **核心假设**: 聚合多分辨率表示可捕捉 TF 在不同尺度上的协同效应，提高对复杂构象元件（如 subTAD 层级）的预测。
- **初步方法**: 在 2/10/100/500 kbp 分辨率下分别训练 Hi-C-LSTM，将表示向量拼接或注意力融合；用融合表示分类 TF 协同对（如 CTCF-CTCF、CTCF-Cohesin）。
- **验证方式**: 比较单分辨率 vs 多分辨率表示在 TF 协同分类任务上的 mAP；检查融合表示是否捕捉到已知的 loop 层级结构。
- **创新状态**: unverified

### 候选 4: 从 Hi-C 表示到 TF 结合位点功能的因果推断
- **名称**: Contact-TF-Causal
- **来源局限/观察**: Hi-C-LSTM 的表示是描述性的，未建立 TF 结合与构象变化的因果方向。
- **核心假设**: 通过干预表示向量（如移除某 TF 结合位点的表示分量），可推断该位点对构象的因果贡献，区分"驱动因子"与"伴随效应"。
- **初步方法**: 对每个 TF 结合位点，将其表示向量置零或替换为随机向量，观察接触矩阵预测的变化；将变化量作为该位点的"构象驱动分数"，与 CRISPR 干扰实验数据对比。
- **验证方式**: 使用已发表的 CRISPRi 筛选数据（如 Gasperini et al.），检查预测的驱动分数是否与实验验证的调控元件一致。
- **创新状态**: unverified