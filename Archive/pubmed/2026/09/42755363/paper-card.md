## 01 基本信息

- **标题**：GenoME: a MoE-based generative model for individualized, multimodal prediction and perturbation of genomic profiles
- **作者**：Wei, Jiachen; Xue, Yue; Chai, Hao; Gao, Yi Qin
- **单位**：未提供（通讯作者 Gao Yi Qin 所属机构未在摘要中列出）
- **期刊/平台**：Nucleic Acids Research
- **年份**：2026
- **论文类型**：研究论文（方法学 + 应用验证）
- **领域**：计算基因组学 / 深度学习 / 基因调控
- **关键词**：Mixture of Experts (MoE)、生成模型、多模态预测、ATAC-seq、基因表达、组蛋白修饰、染色质构象、in silico perturbation
- **DOI/arXiv 号**：10.1093/nar/gkag902
- **代码**：https://github.com/JWei2015/GenoME
- **数据**：ENCODE 公共数据（ATAC-seq、RNA-seq、ChIP-seq、Hi-C），具体 accession 见补充表 S1–S3
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 深度学习」方向，聚焦于**转录因子（TF）结合**的预测与调控机制解析。其核心贡献在于：(1) 以 ATAC-seq 作为细胞类型特异性输入，预测 TF ChIP-seq 等多模态输出，直接涉及 TF–DNA 结合位点的预测；(2) 通过 in silico perturbation 框架（ISM、IG）识别 TF 基序（motif）及其对基因表达的调控效应，为解析 TF–DNA 结合机制提供了可迁移的方法论；(3) MoE 架构的「共享编码器 + 细胞类型特异解码器」设计，为跨细胞类型的 TF 结合预测提供了新思路。

---

## 02 一句话总结

GenoME 是一个基于 Mixture of Experts (MoE) 的生成模型，以 1-Mb DNA 序列和细胞类型特异性 ATAC-seq 信号为输入，统一预测基因表达、TF 结合、组蛋白修饰和 3D 染色质构象等多模态基因组特征，并通过 in silico perturbation 框架（ISM、IG）实现因果性调控解析，在跨细胞类型泛化和增强子-启动子连接预测上优于现有专用模型。

---

## 03 研究问题

- **具体问题**：如何构建一个统一的生成模型，能够从 DNA 序列和细胞类型特异性染色质可及性信号出发，同时预测多种调控特征（基因表达、TF 结合、组蛋白修饰、3D 构象），并支持对遗传或表观遗传扰动的因果性预测？
- **为什么重要**：非编码基因组通过多尺度调控系统运作，TF 结合、组蛋白修饰和 3D 构象共同决定基因表达的时空特异性。现有模型要么仅基于序列（无法区分细胞类型），要么仅针对单一模态（无法捕捉跨模态调控关系），缺乏统一的、可个性化的预测框架。
- **现有方法不足**：
  - 纯序列模型（如 Enformer、AlphaGenome）只能预测训练数据中细胞类型的平均谱，无法泛化到未见过的细胞类型或个体。
  - 细胞类型条件模型（如 Enformer-Celltyping、EPCOT、GET、C.Origami）通常只针对单一输出模态（如仅基因表达或仅染色质构象），缺乏多模态统一框架。
  - 现有模型的 perturbation 能力有限，难以进行因果性调控解析。
- **精确研究问题**："Can a single MoE-based generative model, conditioned on DNA sequence and cell-type-specific ATAC-seq, accurately predict multimodal genomic profiles (expression, TF binding, histone marks, 3D conformation) for both seen and unseen cell types, and enable causal in silico perturbation analysis that identifies functional enhancer–promoter connections and TF motifs?"

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论的叙述，标注为「仅本文框架」；未逐一核验外部文献。

| 阶段 | 代表方法 | 优点 | 局限 | 本文位置 |
|------|----------|------|------|----------|
| 序列-only 生成模型 | Enformer [9]、Borzoi [10]、AlphaGenome [11] | 从序列学习调控编码；多模态输出 | 只能预测训练细胞类型的平均谱；无法个性化 | 本文继承其多模态输出设计，但引入细胞类型条件输入 |
| 细胞类型条件模型 | Enformer-Celltyping [24]、EPCOT [23,30]、GET [25]、C.Origami [26] | 可预测特定细胞类型 | 通常单一输出模态；对与训练分布差异大的样本表现不佳 | 本文以 ATAC-seq 为统一条件输入，覆盖多模态 |
| 基因组大语言模型 | Evo [33]、Nucleotide Transformer [34] | 学习序列语义 | 无法摄入表观遗传上下文；缺乏机制性模拟能力 | 本文不采用 token 化序列方法，保留连续信号处理 |
| 本文方法 | **GenoME** | 统一多模态 + 跨细胞类型泛化 + in silico perturbation | 1-Mb 窗口限制长程调控；依赖 ATAC-seq 质量 | — |

**本文主张的位置**：GenoME 填补了「多模态统一 + 细胞类型可泛化 + 因果扰动」三者交叉的空白，其 MoE 架构是关键创新——编码器专家学习共享的调控「积木块」，解码器专家按细胞类型路由，实现知识复用与个性化输出的平衡。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 纯序列模型无法个性化 | Enformer/AlphaGenome 对每个组织只输出一个平均谱，无法区分同一组织不同个体 | 模型仅以序列为输入，缺乏细胞状态信息 | Introduction 第 2 段；Results 图 2A–B 展示 GenoME 能区分同一组织不同供体 |
| 细胞类型条件模型模态单一 | GET 仅预测表达，C.Origami 仅预测构象，缺乏统一框架 | 各模型针对单一任务设计，未考虑跨模态调控关系 | Introduction 第 2 段 |
| 对分布外细胞类型泛化差 | 现有条件模型对与训练细胞差异大的样本性能下降 | 模型过拟合训练细胞类型的特征组合 | Results 图 2F–I：GenoME 在未见细胞类型上优于 EPCOT2、C.Origami、HiCGen |
| 缺乏因果扰动能力 | 多数模型只能做静态预测，无法模拟遗传或表观扰动后果 | 模型架构不支持输入干预后的重新预测 | Results 图 3：GenoME 的 perturbation 框架预测蛋白降解和增强子沉默的后果 |
| 增强子-启动子连接预测不准确 | 现有方法（如 ABC）依赖实验数据且精度有限 | 缺乏从序列+可及性到功能连接的端到端学习 | Results 图 4：Grad-ABC 分数优于 ABC、ISM、DeepLIFT |

---

## 06 核心思想

### 1) 表面方法

GenoME 以 1-Mb DNA 序列（one-hot 编码）和同区域 ATAC-seq 信号为输入，通过 7 层 1D-CNN 下采样至 128-bp 分辨率，再经混合 Swin-Transformer + Mamba 编码器提取多尺度特征，最后通过多个任务专用解码器（各含 MoE 层）分别输出 RNA-seq、TF ChIP-seq、组蛋白 ChIP-seq 和 Hi-C 接触图。训练时以多任务损失联合优化，推理时给定任意细胞类型的 ATAC-seq 即可预测该细胞类型的全套调控谱。

### 2) 核心洞察

- **MoE 的双重角色**：编码器 MoE 专家学习跨细胞类型共享的调控「积木块」（如启动子/增强子相关的序列-可及性组合模式），解码器 MoE 专家则按细胞类型路由，将共享表示转化为细胞类型特异性输出。这种「共享编码 + 条件解码」的设计使模型既能利用跨细胞类型的统计力量，又能保留个体特异性。
- **ATAC-seq 作为细胞状态指纹**：可及性染色质谱本身是 TF 结合、核小体定位和调控活性的综合体现，将其作为条件输入而非仅作为预测目标，使模型能够将序列编码的调控潜力与实际的细胞状态对接。
- **Perturbation 作为因果工具**：通过修改输入（序列或 ATAC-seq）并重新前向传播，模型可以直接模拟遗传变异或表观扰动对多模态输出的影响，将关联性预测转化为因果性假设生成。

### 3) 可能的普适教训 [Analysis]

- **多模态统一优于单模态专用**：调控特征（TF 结合、组蛋白修饰、表达、构象）本质上是同一调控过程的不同观测面，联合建模可让各任务互相正则化、共享统计力量。
- **条件生成比无条件生成更适合个性化**：以易测量的表观信号（如 ATAC-seq）为条件，可以避免为每个新细胞类型重新训练模型。
- **MoE 是平衡共享与特化的有效机制**：在生物数据中，不同细胞类型共享大量基础调控机制，同时各有特异组合，MoE 的结构化稀疏激活天然契合这一特性。

---

## 07 方法总览

- **输入**：
  - DNA 序列：1-Mb 窗口，5-channel one-hot 编码（A/C/G/T/N）
  - ATAC-seq 信号：同窗口，1-bp 分辨率（训练时用实验数据，推理时用用户提供数据）
  - 全局细胞类型上下文向量：由 1216 个 marker 基因 TSS 周围 3-kb 可及性均值构成，长度 14,592，以 250-bp 分辨率压缩，作为 MoE 门控的额外标签
- **输出**（多任务头）：
  - RNA-seq（±链，1-bp 分辨率）
  - TF ChIP-seq（CTCF，128-bp 分辨率）
  - 组蛋白 ChIP-seq（H3K27ac、H3K27me3、H3K4me1、H3K4me3、H3K9me3、H3K36me3，128-bp 分辨率）
  - Hi-C 接触图（2-kb 分辨率，512×512 矩阵）
- **架构**：
  - 编码器：7 层 1D-CNN 下采样（1-bp → 128-bp），随后 5 个 Swin-Transformer + Mamba 混合块，输出多分辨率特征（128/256/512/1024/2048-bp）
  - 解码器：各任务独立解码器；1-D 任务用 U-Net 风格上采样 + 跳跃连接；Hi-C 用 2D-CNN + MoE 门控
  - MoE 层：集成在前两个 Swin-Transformer 块的 FFN 中（编码器），以及各解码器中；1 个共享专家 + 5 个（编码器）或 8 个（解码器）专科专家；Top-2 路由；温度 τ 从 0.8 退火至 0.5（衰减率 0.95）
- **训练**：
  - 优化器：Adam，峰值学习率 2×10⁻⁴，权重衰减 10⁻⁴
  - 学习率调度：20 epoch 线性 warmup + 80 epoch 余弦退火
  - 损失：各任务加权和（Poisson + Multinomial NLL 用于 1-D 信号；MSE 用于 Hi-C）
  - 辅助损失：MoE 负载均衡损失（z-loss 系数 0.0001，负载均衡损失系数 0.001，均带 0.95 衰减率）
  - 数据增强：随机平移 ±8192 bp；约 50% 序列反向互补
  - 批次大小 B=16（预训练）/ B=8（微调）
- **训练策略**：
  - GenoME-basic：在 8 个组织上训练 100 epoch
  - GenoME-ft：先在 64 组织 + 9 原代细胞上预训练 100 epoch，再在 8 个组织上微调 100 epoch
  - GenoME-HCT116：在 15 个 HCT116 样本（含遗传扰动）上训练 100 epoch
- **推理/应用**：
  - 给定任意细胞类型 ATAC-seq → 预测全套多模态谱
  - In silico perturbation：修改输入（序列碱基替换、ATAC 信号置平/增强）→ 重新前向 → 计算差分
- **Perturbation 框架**：
  - 表观扰动：将窗口内 ATAC-seq 信号置为 ln(2)（模拟沉默）或替换为其他细胞类型信号（模拟激活）
  - 序列扰动（ISM）：逐碱基替换为 N，计算对目标基因表达的影响
  - 梯度归因：IG（积分梯度），从基线（均匀序列 + 平均 ATAC）插值到真实输入，50 步
  - DeepLIFT/SHAP：50 个二核苷酸打乱基线，ATAC 设均值
- **评估指标**：
  - 1-D 信号：Pearson 相关系数（bin-wise 和 track-averaged）
  - Hi-C：距离分层 Pearson 相关、绝缘分数相关
  - E-P 预测：auPRC（以 CRISPRi-FlowFISH 为金标准）
- **基线模型**：AlphaGenome（序列-only）、Enformer-Celltyping、EPCOT2、GET、C.Origami、HiCGen、Orca
- **计算资源**：8× NVIDIA A100 80GB GPU（预训练）；4 GPU 用于微调（约 80 小时/任务）

**文字流程**：  
输入 1-Mb 序列 + ATAC 信号 → 1D-CNN 下采样至 128-bp → SwinT-Mamba 编码器提取多尺度特征（同时输出 128/256/512/1024/2048-bp 分辨率）→ 各任务解码器（含 MoE 门控，以 marker 基因可及性向量为额外条件）→ 输出 RNA-seq / TF ChIP-seq / 组蛋白 ChIP-seq / Hi-C 接触图 → 训练时计算多任务损失反向传播；推理时可直接预测或进行 perturbation 分析。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 1D-CNN 下采样编码器（7 层） | 将 1-bp 分辨率序列和 ATAC 信号压缩为 128-bp 特征 | 降低序列长度至可处理范围，同时保留局部序列模式 | 输入：1-Mb 序列 + ATAC（1-bp）；输出：128-bp 特征图 | Methods "Model architecture" 节 | 预期：无法捕获碱基级精细特征，模型不可训练（序列过长）[预期效应] |
| SwinT-Mamba 混合编码器（5 块） | 捕获多尺度远程依赖和局部窗口模式 | Swin 处理局部窗口注意力，Mamba 提供线性复杂度序列建模 | 输入：128-bp 特征；输出：128/256/512/1024/2048-bp 多分辨率特征 | Methods "Model architecture" 节；Results 图 1 | 预期：移除后长程调控信息丢失，Hi-C 预测显著下降 [预期效应] |
| 编码器 MoE 层（前 2 个 SwinT 块内） | 学习跨细胞类型共享的调控「积木块」 | 使不同细胞类型复用共同的序列-调控模式 | 输入：token 特征 + 门控信号；输出：路由后的专家加权特征 | Results 图 2E；Discussion 第 2 段 | 预期：移除后跨细胞类型泛化能力下降 [预期效应] |
| 解码器 MoE 层（各任务） | 按细胞类型路由，将共享表示转化为特异性输出 | 实现「共享编码 + 条件解码」的核心机制 | 输入：编码器特征 + marker 基因上下文向量；输出：任务特异预测 | Results 图 2E–G；Supplementary Fig. S9 | 实测：门控权重显示细胞类型特异性模式；移除后未见细胞类型预测性能下降 [部分实测] |
| Marker 基因上下文向量（14,592 维） | 提供全局细胞类型身份信息，辅助 MoE 门控 | 使模型在推理时能根据全局可及性状态调整路由 | 输入：1216 基因 TSS ±3-kb 可及性均值（250-bp bin）；输出：门控条件向量 | Methods "Data preprocessing" 节 | 预期：移除后门控失去细胞类型判别依据，泛化下降 [预期效应] |
| 1-D 信号解码器（U-Net + 跳跃连接） | 上采样至碱基级分辨率输出 RNA-seq 和 ChIP-seq | 保留编码器多尺度信息，实现高分辨率预测 | 输入：多分辨率编码器特征；输出：1-bp（RNA）或 128-bp（ChIP）预测 | Methods "Model architecture" 节；Results 图 1C | 预期：移除跳跃连接后精细峰形预测退化 [预期效应] |
| Hi-C 解码器（2D-CNN + MoE） | 从 2048-bp 特征生成 512×512 接触图 | 将 1-D 序列特征转化为 2-D 构象预测 | 输入：2048-bp 特征；输出：512×512 接触矩阵（2-kb bin） | Methods "Model architecture" 节；Results 图 1D | 预期：移除 MoE 后细胞类型特异的构象差异无法区分 [预期效应] |
| In silico perturbation 框架 | 修改输入并重算输出，量化因果效应 | 将静态预测转化为可干预的因果模型 | 输入：原始/扰动输入；输出：差分预测 | Methods "In silico perturbation framework" 节；Results 图 3 | 实测：正确预测蛋白降解和增强子扰动的多模态后果 [实测] |
| ISM（饱和突变） | 逐碱基替换为 N，计算对目标基因表达的影响 | 识别关键调控碱基和 TF 基序 | 输入：目标增强子序列；输出：逐碱基重要性分数 | Methods "Motif discovery" 节；Results 图 5B | 实测：识别出 FOS::JUN、EGR1 等已知 TF 基序 [实测] |
| Grad-ABC 评分 | 结合 IG 梯度与预测 ABC 分数，排序增强子-启动子对 | 综合序列重要性和调控活性预测功能连接 | 输入：候选 E-P 对；输出：连接强度分数 | Methods "Enhancer–promoter pair prediction" 节；Results 图 4 | 实测：优于 ABC、ISM、DeepLIFT 的 auPRC [实测] |

---

## 09 关键公式符号

> 注：原文为期刊排版，部分公式以 LaTeX 呈现；以下仅列理解必需者。

1. **Hi-C 归一化（log-fold over background）**：
   \[
   M_{ij} = \log_2\left(\frac{C_{ij}}{\varepsilon_{|i-j|}}\right)
   \]
   - \( C_{ij} \)：bin i 与 bin j 之间的原始接触计数
   - \( \varepsilon_d \)：基因组距离 d = |i−j| 处的平均背景接触频率
   - 用途：消除距离依赖的接触衰减，使远/近程接触可比
   - 来源：Methods "Data preprocessing" 节

2. **MoE 门控（Top-2 routing with SoftMax temperature）**：
   \[
   p_k = \frac{\exp(g_k / \tau)}{\sum_{j=1}^{K} \exp(g_j / \tau)}
   \]
   - \( g_k \)：第 k 个专家的门控 logit
   - \( \tau \)：温度，从 0.8 退火至 0.5（衰减率 0.95）
   - \( K \)：专家总数（编码器 5 专科 + 1 共享；解码器 8 专科 + 1 共享）
   - 用途：选择 Top-2 专家并计算加权输出
   - 来源：Methods "Model architecture" 节

3. **辅助损失（z-loss + load-balancing）**：
   \[
   \mathcal{L}_{\text{aux}} = \alpha_z \cdot \frac{1}{K}\sum_{k=1}^{K} \left(\frac{1}{B}\sum_{b=1}^{B} g_{k,b}\right)^2 + \alpha_{\text{lb}} \cdot \text{CV}(f_k)
   \]
   - \( \alpha_z = 0.0001 \)，\( \alpha_{\text{lb}} = 0.001 \)（均带 0.95 衰减率）
   - \( f_k \)：第 k 个专家的 token 分配频率
   - 用途：z-loss 惩罚 logit 幅值过大；load-balancing 惩罚专家使用不均
   - 来源：Methods "Model architecture" 节

4. **训练损失（多任务加权和）**：
   \[
   \mathcal{L}_{\text{total}} = \sum_{t \in \mathcal{T}} w_t \cdot \mathcal{L}_t
   \]
   - \( \mathcal{T} \)：任务集合（RNA-seq、TF ChIP-seq、组蛋白 ChIP-seq、Hi-C）
   - \( \mathcal{L}_t \)：各任务损失（Poisson NLL、Multinomial NLL、MSE）
   - 来源：Methods "Training" 节（具体权重未在摘要中给出）

5. **IG（积分梯度）归因**：
   \[
   \text{IG}_i(x) = (x_i - x'_i) \int_{0}^{1} \frac{\partial F(x' + \alpha(x - x'))}{\partial x_i} d\alpha
   \]
   - \( x \)：输入（序列或 ATAC 信号）；\( x' \)：基线（均匀序列 + 平均 ATAC）
   - \( F \)：模型输出（如目标基因表达）
   - 用途：计算每个碱基/位置对目标输出的贡献
   - 来源：Methods "In silico perturbation framework" 节（N=50 步离散近似）

---

## 10 实验设计与证据链

### 数据集与评测协议

| 项目 | 详情 |
|------|------|
| 训练数据 | ENCODE 公共数据：8 个组织（GenoME-basic）、64 组织 + 9 原代细胞（预训练）、15 个 HCT116 样本（含遗传扰动） |
| 测试数据 | 留出染色体（chr10 验证、chr15 测试）；未见细胞类型（如胰腺 F/61、HCT116） |
| 模态 | RNA-seq（总 RNA）、TF ChIP-seq（CTCF）、组蛋白 ChIP-seq（6 种修饰）、Hi-C |
| 分辨率 | RNA/ChIP：1-bp（RNA）或 128-bp（ChIP）；Hi-C：2-kb bin，512×512 窗口 |
| 指标 | Pearson 相关（bin-wise、track-averaged）、距离分层相关、绝缘分数相关、auPRC |
| 基线 | AlphaGenome（序列-only）、Enformer-Celltyping、EPCOT2、GET、C.Origami、HiCGen、Orca |
| 金标准 | CRISPRi-FlowFISH（HCT116 和 K562 的增强子-启动子对） |
| 硬件 | 8× A100 80GB（预训练）；4 GPU（微调，约 80 小时/任务） |

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 多模态预测保真度 | GenoME 能高保真预测多种调控特征 | 与实验数据比较；与 AlphaGenome 对比 | 在 held-out chr15 上，GenoME 的 H3K27ac 和 RNA-seq 预测与实验相关性优于 AlphaGenome | GenoME 在多种模态上达到或超过现有模型 | 未提供全基因组所有模态的完整统计表 | Results 图 1E–G；Supplementary Figs S2–8 |
| 跨细胞类型泛化 | GenoME 能预测训练中未见的细胞类型 | 未见肝脏、食管样本；与 EPCOT2、Enformer-Celltyping 对比 | GenoME-basic 在未见细胞类型上优于 EPCOT2 和 Enformer-Celltyping | MoE 架构支持零样本跨细胞类型泛化 | 仅测试了少数组织类型 | Results 图 2F–G；Supplementary Table S7 |
| 3D 构象预测 | GenoME 能预测未见细胞系的 Hi-C | HCT116（完全未见）；与 C.Origami、HiCGen 对比 | GenoME 在距离分层和绝缘分数相关上优于 C.Origami 和 HiCGen | 从 ATAC-seq 可推断 3D 构象 | 仅比较了 1-Mb 窗口内 | Results 图 2H–I |
| 蛋白降解扰动预测 | 模拟 CDK7、POLR2A、CTCF、RAD21 降解的后果 | 输入突变系 ATAC-seq，预测 RNA/ChIP 变化 | 正确预测 HBG2 位点的表达变化和 CTCF 结合变化；预测 Hi-C 结构破坏（CTCF/RAD21 缺失） | Perturbation 框架能捕获已知调控后果 | 未与所有可用扰动实验系统比较 | Results 图 3A–C |
| 区域沉默扰动 | 模拟 40,000 个活性区域的沉默 | 将 ATAC 信号置为 ln(2)，计算平均差分 | H3K27me3 显示长距离传播（数百 kb），在 ΔCTCF 中增强；H3K4me1 在 SUPT16H 缺失中扩散更广 | 模型捕获了 Polycomb 介导的 H3K27me3 扩散和 CTCF 的绝缘功能 | 差分曲线与实验 ChIP-seq 的定量吻合度未给出完整统计 | Results 图 3D–E |
| E-P 连接预测 | Grad-ABC 分数优于现有方法 | HCT116 CRISPRi-FlowFISH（173 对，38 阳性） | Grad-ABC 的 auPRC 优于 ABC、ISM、DeepLIFT | 结合 IG 与 ABC 可提升 E-P 连接预测 | 仅测试了 HCT116 和 K562 两个细胞系 | Results 图 4A–B；Supplementary Fig. S10 |
| TF 基序发现 | ISM 能识别功能性 TF 基序 | HBG2 增强子；与 JASPAR 比对 | 识别出 FOS::JUN、EGR1 等基序，与 ChIP-seq 峰重叠 | ISM 分数与 TF 结合实验一致 | 仅展示了少数位点 | Results 图 5B–C；Supplementary Fig. S12 |
| 消融：GE 门控位置 | GE 仅注入解码器（而非编码器）对泛化至关重要 | 将 GE 注入编码器的变体 | 注入编码器后，未见细胞类型预测性能下降 | 编码器需保持细胞类型无关，解码器负责特化 | 未提供具体数值 | Discussion 第 2 段；Supplementary Fig. S15 |
| 消融：MoE 层位置 | 仅前 2 个 SwinT 块使用 MoE 足以 | 更多/更少 MoE 块 | 前 2 块 MoE 在性能与计算间最优 | MoE 在早期层捕获共享调控模式 | 未提供完整消融曲线 | Supplementary Fig. S16 |

---

## 11 结论正确解读

- **任务范围**：GenoME 预测的是**细胞类型特异性**的多模态调控谱（RNA-seq、TF ChIP-seq、组蛋白 ChIP-seq、Hi-C），输入为 DNA 序列 + ATAC-seq。它**不是**一个从头预测 TF 结合基序的模型，而是将 TF 结合作为多模态输出之一进行联合预测。
- **Oracle/真值输入**：训练和推理均使用**实验测定的 ATAC-seq** 作为条件输入。这意味着 GenoME 的预测质量高度依赖输入 ATAC-seq 的质量和代表性。它不能仅从序列预测细胞状态，而是将序列与可及性状态结合。
- **端到端状态**：模型是端到端训练的（序列 + ATAC → 多模态输出），但**不是**一个从原始测序数据（FASTQ）到注释的完整流水线，需要预先处理好的 ATAC-seq 信号。
- **算力成本**：预训练 8× A100、微调 4× A100 约 80 小时/任务。对于大多数课题组而言，这一成本是可复现的，但并非轻量级。
- **历史数据依赖**：训练数据来自 ENCODE 的特定组织/细胞类型集合，模型对训练分布之外的组织类型（如罕见细胞类型或疾病状态）的泛化能力未被系统验证。
- **最难情形**：从结果看，模型在**未见细胞类型**上的表现是核心卖点，但测试的未见类型数量有限（胰腺、HCT116 等），且未涉及极端情况（如肿瘤异质性、单细胞分辨率）。
- **不确定性**：论文未报告预测的置信区间或不确定性量化。对于 perturbation 分析，差分信号的大小是否具有统计显著性未明确说明。
- **有边界的复述**：GenoME 是一个以 ATAC-seq 为条件输入的多模态生成模型，在测试的组织和细胞系范围内，其预测保真度和跨细胞类型泛化能力优于现有基线；其 perturbation 框架能识别已知的调控后果（如 CTCF 缺失导致 H3K27me3 扩散）和功能性 TF 基序，但验证范围限于少数位点和细胞系。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 1-Mb 上下文窗口限制 | 无法分析超长距离（>1 Mb）的调控相互作用 | 更高效的架构设计以扩展上下文长度 | Discussion 第 3 段 |
| 静态 ATAC-seq 输入 | 将可及性视为静态条件，无法建模动态调控过程 | 引入时间序列或刺激响应数据 | Discussion 第 3 段 |
| 未整合遗传变异 | 当前模型不直接以 SNP/变异为输入，限制了变异效应预测 | 将遗传变异作为显式输入 | Discussion 第 3 段 |
| 多任务权衡 | 添加 splice junction 预测头略微降低了其他任务的性能 | 更精细的多任务损失加权或任务分组 | Discussion 第 3 段；Supplementary Fig. S13 |
| 计算开销 | MoE 架构增加了训练和推理的计算成本 | 更高效的专家路由和稀疏化策略 | Discussion 第 3 段；Supplementary Fig. S16 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 跨细胞类型泛化测试范围有限 | 仅测试了胰腺、HCT116 等少数未见类型，可能高估泛化能力 | 核心卖点是「unseen cell types」，若测试集与训练集组织类型相近，结论可能不稳健 | 在更多差异大的细胞类型（如免疫细胞、肿瘤系）上系统评估 | Results 图 2F–I |
| ATAC-seq 作为 oracle 输入 | 实际应用中用户可能没有高质量的 ATAC-seq 数据，模型实用性受限 | 若 ATAC-seq 获取困难，模型的「个性化」优势难以落地 | 评估输入 ATAC-seq 噪声/降采样对预测质量的影响 | Methods "Data preprocessing" 节 |
| 与基线比较的公平性 | AlphaGenome 是纯序列模型，EPCOT2 等可能使用不同预处理；比较条件是否完全对齐未说明 | 若基线模型未获得同等信息（如 ATAC-seq），比较可能不公平 | 检查是否所有基线均在相同输入条件下评估 | Results 图 1E–I |
| Grad-ABC 评分的可解释性 | IG 梯度与 ABC 分数的乘积缺乏理论推导，可能只是经验组合 | 若机制不清晰，难以推广到新场景 | 在更多 E-P 数据集上验证，并分析 Grad-ABC 的组成部分贡献 | Methods "Enhancer–promoter pair prediction" 节 |
| 未报告不确定性量化 | 预测和 perturbation 效应均无置信区间 | 对于临床或实验验证，需要知道预测的可靠性 | 添加 MC-dropout 或 ensemble 不确定性估计 | 全文未提及 |
| 消融实验细节有限 | GE 门控位置和 MoE 层数的消融仅在补充材料中简要提及，缺乏完整数据 | 核心设计选择的证据强度不足 | 提供完整的消融表格和统计检验 | Supplementary Figs S15–16 |
| 训练数据组织类型偏向 | 8 个训练组织可能偏向特定谱系，影响对远缘细胞类型的泛化 | 若训练数据多样性不足，模型可能对特定调控程序过拟合 | 分析训练组织的谱系覆盖度，评估谱系距离与预测性能的关系 | Supplementary Table S5 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

| 知识候选 | 类型 | 可迁移性说明（面向 TF–DNA 互作 × AI/物理模拟） |
|----------|------|------------------------------------------------|
| **MoE 的「共享编码 + 条件解码」范式** | 架构设计 | 在 TF–DNA 结合预测中，可设计共享的序列编码器（学习通用调控语法）+ 细胞类型/条件特异的解码器（学习 TF 组合逻辑），实现跨细胞类型的 TF 结合位点泛化预测 |
| **ATAC-seq 作为细胞状态指纹** | 输入设计 | 对 TF–DNA 互作建模，可及性染色质是 TF 结合的直接上游信号。将 ATAC-seq 作为条件输入而非仅预测目标，可让模型将序列潜力和实际结合状态对接 |
| **多模态联合预测的协同效应** | 训练策略 | TF 结合、组蛋白修饰、表达和构象是同一调控过程的不同观测面。联合建模可互相正则化，尤其对数据稀疏的 TF 结合任务有利 |
| **Perturbation 作为因果验证工具** | 方法论 | 对 TF–DNA 互作研究，ISM（逐碱基替换）可直接定位 TF 基序的关键碱基；ATAC 信号扰动可模拟增强子激活/沉默，预测下游表达和构象变化 |
| **Grad-ABC 评分：梯度 × 活性** | 评分函数 | 将模型梯度（序列重要性）与实验衍生活性分数（如 ABC）结合，可提升增强子-启动子连接预测精度，此思路可迁移到 TF-靶基因关系预测 |
| **门控温度退火** | 训练技巧 | 从高温到低温的退火策略可稳定 MoE 训练，对需要稳定收敛的 TF 结合预测模型有参考价值 |
| **Marker 基因全局上下文向量** | 特征工程 | 用少量 marker 基因的可及性状态作为全局细胞类型指纹，可低成本地为模型提供细胞身份信息，避免高维全基因组输入 |
| **U-Net 跳跃连接用于多分辨率输出** | 架构设计 | 在预测 TF 结合峰时，跳跃连接可同时保留局部序列模式和全局调控背景，提升峰形预测精度 |

---

## 15 与已有知识连接

- **Enformer [9] / Borzoi [10] / AlphaGenome [11]**：GenoME 直接继承并扩展了这些序列模型的「序列 → 多模态调控特征」范式。区别在于 GenoME 引入 ATAC-seq 条件输入和 MoE 架构，实现细胞类型特异性预测。对本课题：这些模型共同构成了「序列编码调控语法」的技术基线，GenoME 的条件化思路是对 TF–DNA 结合预测的重要升级。
- **EPCOT [23,30] / Enformer-Celltyping [24] / GET [25] / C.Origami [26]**：这些模型已尝试将细胞类型信号（ATAC/DNase/ChIP）作为条件输入。GenoME 的差异化在于：(1) 多模态统一输出；(2) MoE 的显式「共享-特异」分解；(3) 内置 perturbation 框架。对本课题：TF–DNA 结合预测应关注这些条件化模型的输入设计差异。
- **TF-MoDISco [53] / JASPAR / Tomtom [54]**：GenoME 使用 TF-MoDISco 从 ISM 分数中识别基序，并与 JASPAR 比对。这是将深度学习重要性分数转化为可解释 TF 基序的标准流程，可直接迁移到 TF–DNA 互作研究。
- **Activity-by-Contact (ABC) 模型 [50]**：GenoME 的 Grad-ABC 评分直接基于 ABC 框架，将模型梯度与 ABC 分数结合。ABC 是增强子-启动子连接的经验模型，GenoME 展示了深度学习可增强其精度。
- **CRISPRi-FlowFISH [50–52]**：作为 E-P 连接的金标准验证数据，GenoME 使用该数据集验证 Grad-ABC 评分。对本课题：CRISPRi-FlowFISH 是验证 TF-增强子-靶基因因果关系的实验基准。
- **ChromBPNet [37]**：GenoME 的 ATAC-seq 预处理（bias 解耦、read shifting）遵循 ChromBPNet 流程。对本课题：ATAC-seq 的碱基分辨率处理直接影响 TF 足迹（footprint）分析质量。
- **Swin-Transformer [44,45] / Mamba [46]**：GenoME 的骨干架构。Swin 的窗口注意力适合局部序列模式，Mamba 的线性复杂度适合长序列。对本课题：TF–DNA 结合预测需同时捕获基序级局部特征和远程调控背景，混合架构值得借鉴。
- **Raichu 归一化 [40] / cooltools [42]**：Hi-C 数据预处理标准工具。对本课题：3D 构象与 TF 结合的耦合分析需要标准化的 Hi-C 归一化流程。
- **Captum [48] / DeepLIFT [49] / 积分梯度**：GenoME 的归因工具。对本课题：这些归因方法可定位 TF 结合位点中的关键碱基，与物理模拟（如 MD）结合可验证预测的分子机制。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：TF–DNA 结合特异性的跨细胞类型泛化预测
- **名称**：TF-Bind-MoE：基于 MoE 的转录因子结合位点跨细胞类型预测框架
- **来源局限/观察**：GenoME 以 ATAC-seq 为条件实现跨细胞类型泛化，但其输出是宽泛的 ChIP-seq 信号，未聚焦于单个 TF 的结合特异性。现有 TF 结合预测模型（如 DeepSEA、Basenji）多为序列-only，无法区分细胞类型。
- **核心假设**：将 MoE 的「共享编码器 + 条件解码器」架构应用于单 TF 结合预测，以 ATAC-seq 为条件输入，可显著提升未见细胞类型上的 TF 结合位点预测精度。
- **初步方法**：以 GenoME 的编码器为骨干，替换输出头为单 TF 的 ChIP-seq 预测；在 ENCODE 的多个 TF × 细胞类型组合上训练；评估未见细胞类型的 AUPRC。
- **验证方式**：与序列-only 基线（Enformer 微调）和现有条件模型（EPCOT）比较；在独立 ChIP-seq 数据集上验证。
- **创新状态**：unverified

### 候选 2：TF 基序语法解析：从 ISM 到可解释的协同结合规则
- **名称**：Motif-Syntax：利用生成模型的 ISM 分数解析 TF 协同结合的序列语法
- **来源局限/观察**：GenoME 的 ISM 能识别单个增强子中的 TF 基序，但未系统分析基序之间的间距、方向和组合规则。TF 协同结合（如 pioneer factor + 合作因子）的序列语法仍是开放问题。
- **核心假设**：对大量增强子进行 ISM 扰动，统计基序重要性分数的共变模式，可提取 TF 协同结合的序列语法规则（间距、方向、组合偏好）。
- **初步方法**：在 GenoME 预测的增强子集合上运行 ISM；对基序对的重要性分数进行共变分析；用隐马尔可夫或图神经网络建模基序组合规则。
- **验证方式**：与已知 TF 协同结合实验（如 ChIP-seq 共占据、STARR-seq）比较；在 CRISPR 突变实验中验证预测的语法规则。
- **创新状态**：unverified

### 候选 3：TF 结合与 3D 构象的因果耦合分析
- **名称**：TF-3D-Coupling：利用 perturbation 框架解析 TF 结合对染色质构象的因果影响
- **来源局限/观察**：GenoME 同时预测 TF ChIP-seq 和 Hi-C，但未分析两者的因果关系。TF 结合（如 CTCF）与 3D 构象的相互作用是已知的，但缺乏系统性的计算因果分析。
- **核心假设**：通过联合 perturbation（同时扰动 TF 基序和 ATAC 信号），可以区分 TF 结合对构象的直接与间接影响。
- **初步方法**：在 CTCF/RAD21 相关位点上进行联合 perturbation；比较单扰动与双扰动的 Hi-C 预测差异；用因果推断框架（如 Pearl's do-calculus）建模 TF→构象路径。
- **验证方式**：与 Hi-C 实验（如 CTCF 降解后的 Hi-C）比较；在 CRISPR 编辑的细胞系中验证预测的构象变化。
- **创新状态**：unverified

### 候选 4：从静态 ATAC 到动态可及性：时间序列条件的 TF 结合预测
- **名称**：Dyn-TF-Bind：时间序列 ATAC-seq 条件下的动态 TF 结合预测
- **来源局限/观察**：GenoME 将 ATAC-seq 视为静态输入，无法建模可及性动态变化（如增强子激活/沉默的时间过程）。TF 结合是动态过程，静态快照可能丢失关键信息。
- **核心假设**：将时间序列 ATAC-seq 作为条件输入，可预测 TF 结合的动态变化，并识别时序调控的 TF 网络。
- **初步方法**：扩展 GenoME 以接受多时间点 ATAC-seq 输入；使用时序注意力机制建模可及性变化；在分化或刺激时间序列数据上训练。
- **验证方式**：与时间序列 ChIP-seq 数据比较；在扰动实验中验证预测的动态 TF 结合变化。
- **创新状态**：unverified

### 候选 5：物理模拟与深度学习的混合框架：TF–DNA 结合亲和力的多尺度预测
- **名称**：Hybrid-TF-Affinity：结合 MD 模拟与生成模型的 TF–DNA 结合亲和力预测
- **来源局限/观察**：GenoME 是纯数据驱动模型，缺乏物理约束。TF–DNA 结合亲和力受结构互补性、氢键、水介导作用等物理因素控制，纯深度学习可能无法捕捉稀有突变效应。
- **核心假设**：将 MD 模拟导出的结构特征（如结合自由能、接触图）作为辅助输入或正则化项，可提升 TF–DNA 结合亲和力预测的物理合理性。
- **初步方法**：对已知 TF–DNA 复合物进行 MD 模拟，提取结构特征；将这些特征作为 GenoME 编码器的辅助输入；在突变体数据集上评估预测精度。
- **验证方式**：与实验测定的结合亲和力（如 MITOMI、SPR）比较；在未知突变体上验证泛化能力。
- **创新状态**：unverified