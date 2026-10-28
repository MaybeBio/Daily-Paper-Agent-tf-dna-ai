## 01 基本信息

- **标题**：GenoME: a MoE-based generative model for individualized, multimodal prediction and perturbation of genomic profiles
- **作者与单位**：Wei J; Xue Y; Chai H; Gao YQ（单位未提供）
- **期刊/预印本平台**：bioRxiv
- **年份**：2025-12-28
- **论文类型**：预印本（方法学/工具型论文）
- **领域**：计算基因组学；深度学习；基因调控
- **关键词**：Mixture of Experts (MoE)；多模态预测；ATAC-seq；基因表达；组蛋白修饰；染色质构象；in silico perturbation；增强子-启动子互作
- **DOI/arXiv 号**：10.64898/2025.12.28.696482
- **代码**：未提供
- **数据**：ENCODE 公共数据（ATAC-seq、RNA-seq、ChIP-seq、Hi-C），具体 accession 见补充表 1-3
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 深度学习」交叉方向，聚焦于**转录因子（TF）结合**与基因调控的多模态预测。其核心贡献在于：(1) 以 ATAC-seq 作为细胞类型定义信号，条件化预测 TF 结合（ChIP-seq）、组蛋白修饰、基因表达和 3D 染色质构象；(2) 通过 in silico perturbation 框架（ISM、表观信号激活/沉默、渐变）实现因果性调控机制探究；(3) 提出 Gradient-ABC 评分用于增强子-启动子（E-P）功能连接预测，并利用 TF-MoDISco 解码细胞类型特异的 TF 结合基序（motif）。对 TF-DNA 结合机制研究而言，本文提供了「从序列+染色质可及性到 TF 结合与调控后果」的统一生成式建模框架。

---

## 02 一句话总结

GenoME 是一个基于 Mixture of Experts (MoE) 的生成式模型，以 1-Mb DNA 序列和细胞类型特异的 ATAC-seq 信号为输入，统一预测基因表达、TF 结合、组蛋白修饰和 Hi-C 染色质构象，并通过 in silico perturbation 实现跨细胞类型泛化、增强子-启动子功能连接鉴定和 TF 结合基序解码。

---

## 03 研究问题

- **具体问题**：如何构建一个统一的、可跨细胞类型泛化的生成式模型，从 DNA 序列和染色质可及性信号出发，同时预测多尺度的调控输出（基因表达、TF 结合、组蛋白修饰、3D 构象），并支持因果性 in silico perturbation 分析？
- **为什么重要**：非编码基因组通过多尺度、细胞类型特异的调控系统运作。现有模型要么仅基于序列（无法捕捉细胞类型特异性），要么针对单一模态（如仅预测表达或仅预测 Hi-C），缺乏统一的、可条件化的生成框架。能够从单一 ATAC-seq 输入推断完整调控景观，对解读非编码变异、预测扰动后果、解码细胞身份逻辑至关重要。
- **精确的 Can 问题**：Can a single MoE-based generative model, conditioned on DNA sequence and cell-type-specific ATAC-seq, accurately predict multimodal regulatory profiles (expression, TF binding, histone marks, Hi-C) for both seen and unseen cell types, and support causal in silico perturbation for enhancer-promoter linkage and TF motif discovery?

---

## 04 背景与发展脉络

> 注：此脉络基于本文 Introduction 与 Discussion 的叙述，属「仅本文框架」，未经外部系统核验。

1. **第一代：序列-only 的深度模型**（Enformer、Borzoi、AlphaGenome）
   - 优点：从序列学习通用调控编码，预测多种染色质和表达谱。
   - 局限：只能预测训练数据中细胞类型的平均谱，无法动态条件化到用户指定的细胞状态；无法处理训练分布之外的细胞类型。

2. **第二代：细胞类型条件化模型**（Enformer-Celltyping、EPCOT、GET、C.Origami）
   - 优点：引入细胞类型定义信号（如 ATAC-seq、DNase-seq）作为输入，实现细胞类型特异的预测。
   - 局限：多为单模态专用（GET 仅表达，C.Origami 仅 Hi-C），缺乏统一的多模态生成；对与训练细胞差异极大的新细胞类型泛化能力有限。

3. **第三代（本文主张的位置）：MoE 架构的统一多模态生成模型**
   - GenoME 通过 MoE 层学习可复用的调控「专家」函数，结合 Swin Transformer 编码器和多任务解码器，实现表达、TF 结合、组蛋白修饰、Hi-C 的统一预测，并支持 in silico perturbation 与跨细胞类型泛化。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 序列-only 模型无法动态条件化 | Enformer/AlphaGenome 只能输出训练细胞类型的平均谱，无法针对用户指定细胞类型预测 | 模型未接收细胞类型定义信号作为输入，缺乏条件化机制 | Introduction 第 2 段 |
| 现有细胞类型条件化模型多为单模态 | GET 仅预测表达，C.Origami 仅预测 Hi-C，缺乏统一框架 | 各模型针对单一任务设计，未共享跨模态调控表征 | Introduction 第 2-3 段 |
| 跨细胞类型泛化不足 | 对与训练细胞差异大的新细胞类型，预测精度下降 | 模型可能过拟合训练细胞类型的调控模式，缺乏可复用的调控「构建块」 | Discussion 第 1 段（MoE 学习可复用 building blocks） |
| 多任务联合训练存在负迁移 | 加入剪接位点预测头后，其他任务精度略有下降 | 共享表征与任务特异表征之间存在冲突；复杂任务的最优特征空间可能稀释关键特征 | Discussion 第 2 段；Supplementary Fig. 7 |
| 静态染色质输入无法建模动态过程 | 模型将 ATAC-seq 视为静态条件，无法模拟时间序列或刺激响应 | 当前框架未纳入时间维度或动态信号 | Discussion 第 4 段（未来方向） |

---

## 06 核心思想

### 1) 表面方法
GenoME 是一个多模态生成模型，输入为 1-Mb DNA 序列（one-hot 编码）和细胞类型特异的 ATAC-seq 信号（经 log 变换），通过 7 层 1D-CNN 下采样至 128-bp 分辨率，经 Swin Transformer 编码器（含 MoE 层）处理，再由多个解码器头分别输出基因表达（1-bp 分辨率）、TF 结合（ChIP-seq）、组蛋白修饰（128-bp 分辨率）和 Hi-C 接触图（2-kb 分辨率）。训练损失为各任务的加权 Poisson + Multinomial NLL 之和，并辅以基因水平辅助损失。

### 2) 核心洞察
- **MoE 作为可复用的调控「构建块」**：编码器（SwinT）MoE 层在基因组区域层面特化（如 forest/prairie 区室），解码器 MoE 层在细胞类型层面特化。这种设计使模型能够将训练中习得的调控模块重新组合，从而泛化到未见细胞类型。
- **ATAC-seq 作为细胞类型定义的「主控信号」**：仅需一个 ATAC-seq 输入即可条件化全部模态预测，将染色质可及性视为调控状态的综合表征。
- **in silico perturbation 作为因果探针**：通过操纵输入（序列突变、ATAC 信号沉默/激活、渐变插值），模型可输出多模态响应轨迹，从而推断因果调控关系。

### 3) 可能的普适教训 [Analysis]
- **多模态统一优于单模态专用**：共享编码器 + 多任务解码器的设计使不同模态（表达、TF 结合、组蛋白修饰、Hi-C）之间能够互相提供归纳偏置，提升整体预测一致性。
- **条件化输入比纯序列更灵活**：将「细胞状态」作为显式输入而非隐式参数，使模型天然支持新细胞类型的零样本泛化。
- **MoE 的稀疏激活是跨域泛化的关键机制**：专家特化 + 门控重组的架构，比密集网络更擅长在未见组合下复用已有知识。

---

## 07 方法总览

- **输入**：
  - DNA 序列：1-Mb 窗口，5-channel one-hot 编码（A/C/G/T/N），越界用 N 填充
  - ATAC-seq 信号：同窗口，经 log 变换（数值稳定性处理）
  - 全局细胞类型上下文向量：3 kb 窗口内 1216 个 marker 基因（PanglaoDB）的 ATAC-seq 平均信号，250-bp 分辨率，压缩为 14,592 维向量，输入 MoE 门控
- **输出**（多模态，各任务原生分辨率）：
  - 基因表达（total RNA-seq，1-bp 分辨率）
  - TF 结合（TF ChIP-seq，128-bp 分辨率）
  - 组蛋白修饰（Histone ChIP-seq，128-bp 分辨率）
  - 染色质构象（Hi-C 接触图，2-kb 分辨率）
  - 剪接位点（辅助任务，见 Supplementary Fig. 7）
- **核心模块**：
  1. 1D-CNN 编码器（7 块，降维至 128-bp token）
  2. Swin Transformer 编码器（5 块，含 MoE 层，窗口大小 256）
  3. 多任务解码器（各任务独立头，含 MoE 门控）
  4. 2D-CNN 解码器（Hi-C 接触图，含 MoE 门控，8 个专家 + 1 个共享专家）
- **训练**：
  - 优化器：Adam，lr = 2×10⁻⁴，weight decay = 10⁻⁴
  - 学习率：线性 warmup 20 epochs → Cosine annealing 至 0（共 100 epochs）
  - 数据增强：随机平移 ±8192 bp；约半数序列反向互补
  - 损失：各任务 Poisson + Multinomial NLL 加权和；RNA 任务附加基因水平辅助损失（权重 0.1）
  - 硬件：8× NVIDIA A100 80GB
- **反馈回路**：无显式强化学习或迭代精炼；in silico perturbation 为推理时操作，不涉及训练时反馈。
- **假设**：ATAC-seq 信号足以作为细胞类型调控状态的充分统计量；1-Mb 窗口足以捕获大多数调控互作。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 1D-CNN 编码器 | 将 1-bp 序列和 ATAC 信号降维至 128-bp token | 降低计算复杂度，聚合局部序列特征 | 输入：1-Mb 序列 + ATAC（1-bp）；输出：128-bp 嵌入 | Methods「Model architecture」 | 预期：无法捕获 128-bp 以下精细特征（未消融） |
| Swin Transformer 编码器（含 MoE） | 建模长程序列依赖，MoE 层特化基因组区域调控模式 | 捕获增强子-启动子等远距离互作；MoE 提供可复用调控模块 | 输入：128-bp 嵌入；输出：多分辨率嵌入（128/256/512/1024/2048-bp） | Results 图 1；Supplementary Fig. 9（SwinT MoE 区域特化） | 预期：长程调控捕获能力显著下降（未消融） |
| 解码器 MoE 门控 | 根据全局细胞类型上下文向量选择专家 | 实现细胞类型特异的输出调制 | 输入：全局上下文向量（14,592 维）+ 编码器嵌入；输出：门控权重 | Results 图 2c-e（UMAP 显示细胞类型聚类）；图 2e（门控权重热图） | 预期：跨细胞类型泛化能力大幅下降（未消融） |
| 2D-CNN 解码器（Hi-C） | 从 2048-bp 嵌入生成接触图 | 预测 3D 染色质构象 | 输入：2048-bp 嵌入；输出：512×512 接触矩阵 | Results 图 1h-i | 预期：无法预测染色质结构（未消融） |
| 1D 解码器（表达/ChIP） | 生成基因表达和 TF/组蛋白结合谱 | 多模态输出 | 输入：多分辨率嵌入（U-Net 上采样）；输出：1-bp 或 128-bp 信号 | Results 图 1b-g | 预期：多模态预测能力丧失（未消融） |
| 剪接位点预测头 | 预测剪接位点 | 辅助任务，可能提升共享表征质量 | 输入：1-bp 嵌入；输出：剪接位点概率 | Supplementary Fig. 7（加入后其他任务精度略降） | 实测：加入后其他任务精度略降（负迁移） |
| in silico perturbation 框架 | 操纵输入（序列/ATAC）并观察输出变化 | 因果推断、增强子-启动子连接、TF motif 发现 | 输入：扰动后的序列/ATAC；输出：多模态差分信号 | Results 图 3-5 | 预期：无此框架则无法进行因果分析（未消融） |

---

## 09 关键公式符号

> 注：原文 Methods 中损失函数公式以文字描述为主，未给出完整编号公式。以下为可辨识的关键数学对象。

1. **训练损失（各任务加权和）**：
   \[
   \mathcal{L} = \sum_{t \in \text{tasks}} w_t \left( \lambda_t \mathcal{L}_{\text{Poisson},t} + (1-\lambda_t) \mathcal{L}_{\text{Multinomial},t} \right)
   \]
   - \( t \)：任务索引（RNA、TF ChIP、Histone ChIP、Hi-C）
   - \( w_t \)：任务权重
   - \( \lambda_t \)：Poisson 与 Multinomial 损失的混合系数
   - 用途：多任务联合训练
   - 来源：Methods「Training」段（公式以文字描述）

2. **Hi-C 归一化（log-fold over background）**：
   \[
   \text{norm}(i,j) = \log\left( \frac{\text{count}(i,j)}{\epsilon_{|i-j|}} \right)
   \]
   - \( i, j \)：基因组 bin 索引
   - \( \epsilon_d \)：基因组距离为 \( d = |i-j| \) 的平均背景接触频率
   - 用途：消除距离依赖的接触衰减
   - 来源：Methods「Data preprocessing」Hi-C 段

3. **ATAC 信号变换（数值稳定性）**：
   \[
   \text{ATAC}_{\text{in}} = \text{clip}\left( \log(\text{ATAC}_{\text{raw}} + 1), 0, c \right)
   \]
   - \( c \)：裁剪阈值（具体值未提供）
   - 用途：压缩动态范围，稳定训练
   - 来源：Methods「Data preprocessing」ATAC 段（以文字描述）

4. **渐变扰动（线性插值）**：
   \[
   \text{ATAC}_{\alpha_i} = (1-\alpha_i) \cdot \text{ATAC}_{\text{source}} + \alpha_i \cdot \text{ATAC}_{\text{target}}, \quad \alpha_i = \frac{i}{N-1}, \quad i=0,\dots,N-1
   \]
   - \( N = 50 \)：插值步数
   - 用途：模拟细胞状态连续转变，追踪输出轨迹
   - 来源：Methods「Perturbation analysis」段

5. **Gating 温度退火**：
   \[
   p_k = \frac{\exp(z_k / \tau)}{\sum_{j=1}^{K} \exp(z_j / \tau)}, \quad \tau: 0.8 \to 0.5, \text{ decay } 0.95
   \]
   - \( z_k \)：第 \( k \) 个专家的 logit
   - \( K \)：专家数（8 个 specialist + 1 个 shared）
   - 用途：控制门控 softmax 的锐度，平衡探索与利用
   - 来源：Methods「Model architecture」MoE 段

---

## 10 实验设计与证据链

### 数据集/群体、规模、指标、基线、预算、评测协议
- **训练数据**：ENCODE 公共数据，63 组组织 ATAC-seq、9 组原代细胞、17 组细胞系；每组含 RNA-seq、7 种组蛋白 ChIP-seq、TF ChIP-seq（CTCF）、Hi-C。具体 accession 见补充表 1-3。
- **数据划分**：按染色体划分——chr10 为验证集，chr15 为测试集，其余为训练集。
- **指标**：Pearson 相关系数（bin-wise 和 track-averaged）；Hi-C 额外使用距离分层相关、绝缘分数相关、observed/expected (O/E) 相关。
- **基线模型**：AlphaGenome（序列-only）、Enformer-Celltyping、EPCOT2、GET、Orca、C.Origami、HiCGen。
- **评测协议**：
  - 对已见细胞类型：在 chr15 上比较预测与实验信号。
  - 对未见细胞类型：直接输入该细胞类型的 ATAC-seq，不微调，比较全基因组预测。
  - 对扰动实验：与真实 CRISPR 扰动（auxin-induced degradation）数据比较。
  - 对 E-P 连接：与 CRISPRi-FlowFISH 数据比较，使用 auPRC。

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 多模态预测保真度 | GenoME 能高保真预测已见细胞类型的多模态信号 | chr15 测试集，GenoME-basic vs AlphaGenome | H3K27ac 和 RNA-seq 相关高于 AlphaGenome | GenoME 在调控关键信号上优于序列-only 模型 | 未提供全基因组所有模态的完整对比表 | Results 图 1e-g |
| Hi-C 预测 | GenoME 能预测染色质构象 | chr15 测试集，GenoME vs Orca、C.Origami、HiCGen | 距离分层和绝缘相关优于 Orca 和 C.Origami；HiCGen 在 >0.7 Mb 长程接触占优 | GenoME 在 1-Mb 窗口内 Hi-C 预测最优 | HiCGen 因输入窗口更大在超长程占优，非公平对比 | Results 图 1h-i |
| 未见细胞类型泛化 | GenoME 能从单一 ATAC-seq 泛化到未见细胞类型 | 未见肝、食管样本；GenoME-basic vs Enformer-Celltyping、EPCOT2 | GenoME-basic 在 RNA-seq 和 ChIP-seq 上优于两者 | MoE 架构支持跨细胞类型零样本泛化 | 仅测试了少数组织，未覆盖全部 63 组 | Results 图 2f-g |
| 完全未见细胞系（HCT116） | GenoME 能预测完全未见细胞系的 3D 构象 | HCT116（非训练细胞系），GenoME vs C.Origami、HiCGen | GenoME 距离分层和绝缘相关优于两者 | 对完全未见细胞系具有强泛化能力 | 仅测试一个细胞系 | Results 图 2h-i |
| 扰动预测（CDK7 降解） | GenoME 能预测未见于训练的扰动后果 | HCT116 + CDK7 降解，GenoME 预测 vs 实验 | 准确预测 HBG2 位点转录上调 | 模型具备因果扰动预测能力 | 仅验证单个位点 | Results 图 3a-b |
| 扰动预测（CTCF/RAD21 降解） | GenoME 能预测结构蛋白降解的染色质后果 | HCT116 ΔCTCF、ΔRAD21，预测 vs 实验 Hi-C | 准确预测拓扑结构域边界破坏 | 模型捕获了 CTCF/cohesin 的绝缘功能 | 未提供全基因组定量指标 | Results 图 3c |
| 大规模沉默扰动 | 沉默 40,000 个活性区域可量化调控影响范围 | 40,000 个 1-kb ATAC 峰沉默，统计差分信号 | H3K27me3 呈现数百 kb 长程扩散；H3K4me1 扩散范围更窄 | 模型能区分不同组蛋白修饰的空间调控范围 | 未与实验逐一验证 | Results 图 3d-e |
| E-P 连接预测 | Gradient-ABC 优于现有方法 | HCT116 CRISPRi-FlowFISH 数据（173 对，38 阳性） | Gradient-ABC auPRC 优于 ABC、ISM、DeepLIFT | 结合梯度与 ABC 的混合评分更优 | 仅测试一个细胞系 | Results 图 4a-b |
| 定量 E-P 效应预测 | GenoME 能定量预测增强子扰动对表达的影响 | FAMC3 位点，预测 vs CRISPRi 实验 | Pearson r = 0.53 | 模型可定量估计增强子-启动子互作强度 | 仅单个位点 | Results 图 4c-d |
| TF motif 发现 | ISM 梯度能识别功能 TF 结合位点 | HCT116 增强子区域，ISM vs TF ChIP-seq | 识别出 FOS::JUN、EGR1 等已知 motif，与 ChIP-seq 峰重叠 | 模型编码了可解释的 TF 结合语法 | 未做全基因组 motif 富集分析 | Results 图 5a-c |
| 消融：ATAC 输入 | ATAC-seq 输入对预测的贡献 | 移除 ATAC 输入 vs 完整模型 | 未提供具体数值 | 未提供 | 未提供 | 未提供（footnote 提及消融但未给结果） |
| 消融：Gradient-ABC 组件 | 各组件对 E-P 预测的贡献 | 移除梯度/ABC/ATAC 组件 | 未提供具体数值 | 未提供 | 未提供 | 未提供（footnote 提及消融但未给结果） |

---

## 11 结论正确解读

- **任务范围**：GenoME 预测的是**调控信号的稳态水平**（基因表达、TF 结合、组蛋白修饰、Hi-C 接触频率），而非动态过程或绝对分子计数。预测基于 1-Mb 窗口，无法捕获超长程（>1 Mb）互作。
- **Oracle/真值输入**：模型以实验测量的 ATAC-seq 作为条件输入。这意味着预测质量受 ATAC-seq 数据质量影响；对于无 ATAC-seq 的细胞类型，模型无法直接应用。
- **端到端状态**：模型是端到端训练的（序列+ATAC → 多模态输出），但 in silico perturbation 是推理时操作，不涉及训练时反事实学习。
- **算力成本**：训练需 8× A100 GPU，约 80 小时（不含预训练）；推理成本未报告。
- **历史数据依赖**：模型依赖 ENCODE 数据，其覆盖偏向常见组织/细胞系；对罕见细胞类型或疾病状态的泛化能力未验证。
- **模型依赖**：MoE 架构的专家数量、门控机制、温度退火等超参数未做系统敏感性分析。
- **最难情形**：完全未见细胞系（如 HCT116）的 3D 构象预测是较难任务，但仅测试了一个细胞系；对遗传扰动（CDK7 降解）的预测仅验证了单个位点。
- **群体/领域边界**：模型基于人类基因组训练，不适用于非人物种；仅覆盖 ENCODE 中已注释的调控信号类型。
- **不确定性**：模型未提供预测不确定性估计（如贝叶斯或 ensemble 方法）。
- **有边界的复述**：GenoME 能够在 1-Mb 窗口内、以 ATAC-seq 为条件，对已见和部分未见人类细胞类型的多模态调控信号进行高保真预测，并支持 in silico perturbation 以推断增强子-启动子连接和 TF 结合基序；但其泛化能力仅在有限组织/细胞系上验证，且依赖高质量 ATAC-seq 输入。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 上下文窗口有限 | 1-Mb 窗口无法捕获超长程染色质互作或全染色体组织 | 引入更长上下文或层次化建模 | Discussion 第 4 段 |
| 静态输入 | 将 ATAC-seq 视为静态条件，无法建模时间序列或刺激响应 | 纳入时间序列或刺激响应数据 | Discussion 第 4 段 |
| 未整合遗传变异 | 模型未将 SNP/变异作为显式输入，限制了个性化基因组预测 | 将遗传变异作为显式输入 | Discussion 第 4 段 |
| 多任务负迁移 | 加入剪接位点预测头后其他任务精度略降 | 更精细的任务权重或条件计算 | Discussion 第 2 段；Supplementary Fig. 7 |
| 效率与扩展性 | 更长序列需更高效架构（如 Mamba/Hyena） | 混合架构设计 | Discussion 第 4 段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| 未见细胞系泛化仅测试 HCT116 | HCT116 是常见癌细胞系，可能与其他训练组织共享大量调控特征；「未见」程度有限 | 若泛化仅因数据重叠而非 MoE 机制，则对真正 novel 细胞类型（如罕见分化态）的适用性存疑 | 在系统发育或调控状态距离更远的细胞类型上测试（如 iPSC、罕见免疫亚群） | Results 图 2h-i |
| Gradient-ABC 的消融未报告数值 | Footnote 声称做了消融但未给出具体 auPRC 变化 | 无法判断各组件（梯度、ABC、ATAC）的相对贡献 | 要求补充消融表格 | Footnote 1 |
| 与 HiCGen 的对比不公平 | HiCGen 在 >0.7 Mb 长程占优，作者归因于其输入窗口更大，但未控制输入长度 | 若 HiCGen 在相同输入窗口下仍占优，则 GenoME 的 3D 预测能力需重新评估 | 在相同 1-Mb 输入下重跑 HiCGen | Results 图 1h-i |
| 扰动预测验证规模有限 | CDK7 降解仅验证 HBG2 单一位点；40,000 区域沉默无实验验证 | 单点验证不足以支撑「因果扰动预测」的强 claim | 在多个位点、多种扰动类型上系统验证 | Results 图 3a-b |
| TF motif 发现依赖已知 motif 数据库 | 与 JASPAR 比对只能发现已知 motif，无法评估模型发现新 motif 的能力 | 若模型仅复现已知 motif，则其「解码 TF 语法」的新颖性有限 | 使用 de novo motif 发现方法评估 | Results 图 5 |
| 未报告预测不确定性 | 模型输出为点估计，无置信区间 | 在调控预测中，不确定性估计对下游决策（如候选增强子优先级）至关重要 | 引入 MC-dropout 或 ensemble | 全文未提及 |
| 训练数据组织类型有限 | 63 组织 + 9 原代 + 17 细胞系，但未报告性别、年龄、疾病状态分布 | 若训练数据偏向健康成人，则对疾病状态或发育阶段的泛化能力未知 | 在 GTEx 或 TCGA 数据上测试 | Methods「Data preprocessing」 |
| MoE 专家可解释性未深入 | 仅展示门控权重热图，未分析专家功能特化的生物学意义 | 若专家特化无生物学对应，则 MoE 的「可复用构建块」claim 缺乏机制支撑 | 对专家激活模式与已知调控模块（如增强子状态、启动子类型）做关联分析 | Results 图 2e；Supplementary Fig. 9 |

---

## 14 学到什么

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题的可迁移知识。

### 概念层面
1. **条件化生成优于纯序列预测**：将「细胞状态」作为显式输入（而非隐式训练标签），使模型天然支持新细胞类型的零样本泛化。对 TF-DNA 结合研究，这意味着可以用 ATAC-seq（或 DNase-seq）作为「染色质状态条件」，预测特定细胞类型中的 TF 结合谱。
2. **MoE 作为跨域泛化机制**：专家特化 + 门控重组的架构，比密集网络更擅长在未见组合下复用已有知识。对 TF-DNA 建模，可类比为「不同 TF 结合模式 = 不同专家」，门控根据局部序列和染色质上下文选择专家。
3. **多模态联合训练提供归纳偏置**：表达、TF 结合、组蛋白修饰、Hi-C 共享编码器，使不同模态互相约束，提升整体一致性。对 TF-DNA 研究，可将 TF 结合与下游表达、上游染色质状态联合建模，获得更一致的调控图景。

### 方法层面
4. **in silico perturbation 作为因果探针**：通过操纵输入（序列突变、表观信号沉默/激活、渐变插值）观察多模态输出变化，可系统性地推断增强子-启动子功能连接和 TF 结合位点的因果效应。
5. **Gradient-ABC 混合评分**：将模型梯度（反映输入对输出的敏感性）与领域知识评分（ABC）结合，优于单一方法。对 TF-DNA 研究，可将深度学习归因（如 Integrated Gradients、DeepLIFT）与物理/生化先验（如结合自由能、motif 匹配）结合。
6. **ISM 用于 motif 发现**：通过逐碱基替换并观察表达变化，可识别功能关键的 TF 结合位点，且与 ChIP-seq 实验数据一致。
7. **距离分层评估**：对 Hi-C 预测采用距离分层相关，避免长程接触稀疏性掩盖短程精度。对 TF-DNA 结合预测，可类似地按结合位点与 TSS 距离分层评估。

### 实验设计层面
8. **按染色体划分数据**：避免同一位点在不同细胞类型间的泄漏，是跨细胞类型泛化评估的合理策略。
9. **完全未见细胞系作为强泛化测试**：比随机划分更能检验模型的泛化能力，值得在 TF-DNA 模型评估中采用。

---

## 15 与已有知识连接

- **Enformer**（Avsec et al., 2021, Nature Methods）：序列-only 的调控预测模型。GenoME 在编码器设计上与其有相似之处（1D-CNN + Transformer），但引入了 ATAC-seq 条件输入和 MoE 架构。对 TF-DNA 研究，Enformer 的序列特征提取方法可迁移。
- **AlphaGenome**（Tan et al., 2025）：多模态序列模型，GenoME 的直接对比基线。其剪接位点预测头与 GenoME 的负迁移现象（Supplementary Fig. 7）提示多任务学习中的任务冲突问题。
- **GET**（Ibarra et al., 2024）：表达预测的细胞类型条件化模型。GenoME 的全局上下文向量设计与之类似，但 GenoME 扩展到了多模态。
- **C.Origami**（Tan et al., 2023）：3D 基因组预测模型。GenoME 在 Hi-C 预测上与其对比，并指出其输入窗口限制。
- **Activity-by-Contact (ABC) model**（Fulco et al., 2019, Nature Genetics）：基于 ATAC、H3K27ac 和 Hi-C 的增强子-启动子连接预测。GenoME 的 Gradient-ABC 将其与深度学习梯度结合，是领域知识+深度学习的典型融合。
- **TF-MoDISco**（Shrikumar et al., 2018）：基于深度学习的 motif 发现工具。GenoME 使用其从 ISM 归因图中识别 TF 结合 motif。
- **DeepLIFT/SHAP**（Shrikumar et al., 2017；Lundberg & Lee, 2017）：特征归因方法。GenoME 使用其计算核苷酸级别的贡献分数。
- **ChromBPNet**（Bentsen et al., 2020）：ATAC-seq 信号处理流程，GenoME 采用其 bias 解耦方法。
- **PanglaoDB**（Franzén et al., 2019）：细胞类型 marker 基因数据库，GenoME 用于构建全局上下文向量。
- **ENCODE**（ENCODE Project Consortium, 2012）：数据来源，涵盖多组织/细胞类型的多模态调控数据。

---

## 16 研究想法

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题的研究候选。

### 候选 1：TF 结合特异性的条件化生成模型
- **名称**：TF-BindMoE：基于 MoE 的 TF 结合谱条件化预测模型
- **来源局限/观察**：GenoME 将 ATAC-seq 作为细胞类型条件，但未显式建模单个 TF 的 DNA 结合特异性。现有 TF 结合预测模型（如 DeepSEA、Basenji）多为序列-only，无法捕捉细胞类型特异的 TF 结合。
- **核心假设**：将 TF 身份（或 TF motif 嵌入）作为条件输入，与序列和染色质状态共同决定结合预测，可提升跨细胞类型的 TF 结合预测精度。
- **初步方法**：在 GenoME 框架基础上，将 TF 嵌入向量与序列编码拼接，解码器输出该 TF 在窗口内的结合概率；MoE 专家按 TF 家族或 DNA 结合域类型特化。
- **验证方式**：使用 ENCODE TF ChIP-seq 数据（多 TF × 多细胞类型），比较与序列-only 基线（如 DeepSEA）的 AUC；测试未见 TF 的零样本预测。
- **创新状态**：unverified

### 候选 2：物理模拟与深度学习的混合 TF-DNA 结合自由能预测
- **名称**：PhysGenome：将 MD/对接自由能与深度学习归因结合的 TF-DNA 结合强度预测
- **来源局限/观察**：GenoME 的 ISM 归因分数反映序列对表达的贡献，但缺乏物理可解释性（如结合自由能变化）。MD 模拟虽物理精确但计算昂贵，无法全基因组扫描。
- **核心假设**：将深度学习归因分数（如 ISM、Integrated Gradients）与基于物理的 TF-DNA 结合自由能（如来自 MD 或 FoldX）进行对比校准，可提升结合强度预测的物理一致性。
- **初步方法**：对一组 TF-DNA 复合物，计算 MD 结合自由能；同时用 GenoME 类模型计算 ISM 分数；训练一个映射函数将 ISM 分数校准为自由能估计；在全基因组增强子上应用。
- **验证方式**：与实验结合亲和力数据（如 HT-SELEX、PBMs）比较；评估校准后的自由能是否比原始 ISM 分数更接近实验值。
- **创新状态**：unverified

### 候选 3：增强子-启动子连接的因果扰动图谱
- **名称**：Perturb-EP：基于 GenoME 的增强子-启动子因果连接全基因组图谱
- **来源局限/观察**：GenoME 的 Gradient-ABC 在 HCT116 上优于 ABC，但仅测试了一个细胞系；且未系统评估不同扰动类型（沉默 vs 激活）的对称性。
- **核心假设**：GenoME 的 in silico perturbation 可系统性地绘制全基因组增强子-启动子因果连接图谱，且在不同细胞类型间具有可迁移性。
- **初步方法**：在多个细胞类型（如 K562、GM12878、HepG2）上运行大规模沉默/激活扰动，构建连接图谱；与 CRISPRi-FlowFISH、CRISPRa 数据对比；分析连接强度与 CTCF/cohesin 绝缘的关联。
- **验证方式**：与实验扰动数据（CRISPRi-FlowFISH、CRISPRa）的 auPRC；跨细胞类型连接图谱的一致性分析。
- **创新状态**：unverified

### 候选 4：TF 结合 motif 的细胞类型特异性语法解码
- **名称**：TF-Grammar：基于 GenoME 归因的细胞类型特异性 TF 结合语法解码
- **来源局限/观察**：GenoME 的 ISM 分析在 HCT116 上识别了 FOS::JUN、EGR1 等 motif，但未系统比较不同细胞类型间 TF 结合语法的差异。
- **核心假设**：不同细胞类型中，同一 TF 的结合 motif 偏好和协同作用模式存在系统性差异，可通过 GenoME 类模型的归因分数解码。
- **初步方法**：在多个细胞类型上运行 ISM，提取高重要性 motif；比较 motif 位置权重矩阵（PWM）的细胞类型间差异；分析 TF-TF 协同（motif 共现）的细胞类型特异性。
- **验证方式**：与已知细胞类型特异性 TF 结合数据（如来自 Cistrome 的 ChIP-seq）比较；验证新发现的 motif 是否在实验数据中富集。
- **创新状态**：unverified

### 候选 5：整合遗传变异的个性化调控预测
- **名称**：Variant-GenoME：整合 SNP 的个性化多模态调控预测
- **来源局限/观察**：GenoME 未将遗传变异作为显式输入，限制了对个体间调控差异的预测。
- **核心假设**：将 SNP 作为序列扰动输入 GenoME 类模型，可预测变异对多模态调控信号（表达、TF 结合、组蛋白修饰、Hi-C）的个体化影响。
- **初步方法**：在 GenoME 框架中增加变异编码通道，或在推理时对变异位点进行 ISM；在 GTEx eQTL 数据上验证变异效应预测；与现有 eQTL 预测方法（如 Enformer 变异效应）对比。
- **验证方式**：与 GTEx eQTL 的效应方向一致性；与 fine-mapping 结果的 overlap。
- **创新状态**：unverified

### 候选 6：TF-DNA 结合动力学的生成式模拟
- **名称**：TF-DynGen：基于 GenoME 的 TF 结合动力学轨迹生成
- **来源局限/观察**：GenoME 的 perturbation 是静态的（单步扰动），无法模拟 TF 结合的动态过程（如结合-解离、协同装配）。
- **核心假设**：将 GenoME 的 perturbation 框架扩展为多步动态模拟，可生成 TF 结合的时间演化轨迹，揭示协同结合和竞争结合的动态机制。
- **初步方法**：将 GenoME 的 perturbation 视为马尔可夫决策过程，逐步扰动 ATAC-seq 或序列并观察输出变化；用强化学习或扩散模型生成动态轨迹；与单分子实验（如 smFRET）数据对比。
- **验证方式**：与单分子 TF 结合动力学实验数据比较；验证生成的轨迹是否重现已知的协同结合现象。
- **创新状态**：unverified