## 01 基本信息

- **标题**：EPInformer: scalable and integrative prediction of gene expression from promoter-enhancer sequences with multimodal epigenomic profiles
- **作者与单位**：Lin, Jiecong; Li, Zhijian; Zhao, Yajie; Luo, Ruibang（香港大学）; Pinello, Luca（哈佛大学/麻省总医院）
- **期刊/预印本平台**：Nature Communications
- **年份**：2026
- **论文类型**：研究论文（Research Article）
- **领域**：计算基因组学、基因表达调控、深度学习
- **关键词**：gene expression prediction, promoter-enhancer interactions, transformer, epigenomics, chromatin contacts, TF motifs
- **DOI/arXiv 号**：10.1038/s41467-026-70535-8
- **代码**：未提供
- **数据**：ENCODE（DNase-seq, H3K27ac ChIP-seq）、4DN Nucleome（Hi-C）、Xpresso 数据集（RNA-seq）、FANTOM（CAGE）
- **阅读日期**：2026-05-15
- **在该课题方向中的位置**：本文属于「AI/深度学习 × 蛋白质-DNA 互作」方向，聚焦于**增强子-启动子（enhancer-promoter）互作**对基因表达的调控预测。与 TF-DNA 结合机制课题的关联在于：其序列编码器学习增强子中的 TF 结合 motif，并通过注意力机制识别关键增强子-启动子互作，为 TF 结合位点功能解读提供可迁移的深度学习框架。

## 02 一句话总结

EPInformer 通过 transformer 架构显式建模启动子与候选增强子之间的互作，整合 DNA 序列、表观基因组信号（DNase、H3K27ac）和染色质接触（Hi-C）等多模态数据，在跨染色体验证中优于 Enformer、Borzoi、Seq-GraphReg 等现有方法，并能通过注意力权重识别经 CRISPR 验证的增强子-基因互作及 TF 结合 motif。

## 03 研究问题

- **具体问题**：如何从 DNA 序列和表观基因组数据中准确预测基因表达水平，并同时识别调控基因表达的远端增强子及其中的 TF 结合 motif？
- **为什么重要**：顺式调控元件（增强子、启动子）的互作是转录调控的核心机制，理解其编码规则对解析细胞分化、疾病变异功能注释至关重要。现有方法要么忽略远端增强子（如 Xpresso 仅用启动子附近序列），要么需要大量计算资源（如 Enformer、Borzoi 参数规模巨大），且难以适应新细胞类型。
- **现有方法不足**：(1) Enformer/Borzoi 训练成本高、参数庞大（2.5亿/1.86亿），难以被普通实验室采用；(2) 这些模型虽能预测表达，但缺乏对增强子-启动子互作的显式建模，可解释性有限；(3) Seq-GraphReg 依赖 Hi-C 数据，但受限于 Hi-C 数据在多种细胞系中的可用性；(4) 现有方法难以同时完成表达预测和增强子-基因互作识别两个任务。
- **精确研究问题**：Can a lightweight transformer architecture that explicitly models promoter-enhancer interactions with multimodal epigenomic inputs achieve state-of-the-art gene expression prediction while simultaneously enabling accurate enhancer-gene prioritization and TF motif discovery?

## 04 背景与发展脉络

**注：以下脉络基于本文框架整理，部分经外部核验。**

1. **序列直接预测表达（CNN 时代）**：Xpresso（Agarwal & Shendure, 2020）利用 CNN 从启动子附近 20 kb 序列预测 mRNA 表达，但忽略远端增强子信息，性能受限。
2. **长上下文序列模型（Transformer 时代）**：Enformer（Avsec et al., 2021）将输入扩展到 200 kb，用 transformer 捕获长程调控；Borzoi（Calico, 2023）进一步扩展到 524 kb。这些模型性能优越但参数庞大（Enformer 2.5亿、Borzoi 1.86亿），训练和推理成本高，且难以解释具体增强子-基因互作。
3. **图神经网络整合染色质互作**：Seq-GraphReg（Karbalayghareh et al., 2022）引入图注意力网络整合 Hi-C/HiChIP 数据，但依赖染色质互作数据的可用性，限制了其在新细胞类型中的应用。
4. **多模态整合与显式互作建模（本文位置）**：EPInformer 提出轻量级 transformer（仅 0.4M 参数），通过显式的 promoter-enhancer 注意力模块建模互作，灵活整合序列、表观信号和染色质接触，在性能、效率和可解释性之间取得平衡。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 远端增强子效应捕获不足 | Xpresso 仅用启动子附近 20 kb 序列，无法利用远端增强子信息 | 输入范围限制，缺乏长程调控建模 | Results 图 2a：EPInformer-PE (0.78) 显著优于 Xpresso (0.67) |
| 模型参数规模过大 | Enformer 2.5亿参数、Borzoi 1.86亿参数，训练和推理成本高 | 全序列 transformer 架构需要大量参数处理长上下文 | Discussion：EPInformer 仅 0.4M 参数，约为 Enformer 的 0.2% |
| 缺乏显式增强子-启动子互作建模 | 现有序列模型隐式学习调控关系，难以直接解读具体增强子-基因对 | 注意力机制未针对 promoter-enhancer 结构进行设计 | Results 图 3b：注意力分数优于 ABC 分数预测 CRISPR 验证的增强子 |
| 对新细胞类型适应性差 | Enformer/Borzoi 需要大规模重新训练才能适应新细胞类型 | 预训练模型固定，微调成本高 | Discussion：EPInformer 仅需 1 小时即可完成单细胞类型训练 |
| Hi-C 数据依赖限制 | Seq-GraphReg 依赖 Hi-C 数据，但 Hi-C 在多数细胞系中不可用 | 图注意力网络需要染色质互作作为输入 | Results：EPInformer-PE-Activity（无 Hi-C）仍优于 Seq-GraphReg (0.744) |
| 可解释性不足 | 现有模型难以定位关键调控序列和 TF motif | 缺乏针对增强子序列的注意力权重提取机制 | Results 图 4：结合注意力分数和 TF-MoDISco-lite 识别关键 motif |

## 06 核心思想

### 1) 表面方法
EPInformer 是一个四模块 transformer 框架：(a) 序列编码器（EPInformer-seq）用残差卷积和空洞卷积学习启动子与增强子的 DNA 序列嵌入；(b) 融合层将序列嵌入与表观信号（DNase、H3K27ac）、染色质接触（Hi-C）和距离信息拼接；(c) 互作编码器用 3 层 transformer 的注意力机制显式建模启动子-增强子互作；(d) 预测器用全连接层输出基因表达值。

### 2) 核心洞察
**将增强子-启动子互作作为显式归纳偏置**：不同于 Enformer 对所有序列位置做全注意力，EPInformer 将输入组织为「1 个启动子 + 最多 60 个候选增强子」的结构化形式，注意力仅在这 61 个 token 之间计算。这一设计大幅减少计算量（0.4M 参数），同时使注意力权重天然对应增强子-基因互作强度，兼具高效性和可解释性。

### 3) 可能的普适教训 [Analysis]
- **结构化归纳偏置优于纯数据驱动**：在生物序列建模中，将已知的生物学结构（如 promoter-enhancer 关系）编码为架构约束，可以显著降低参数需求并提升可解释性。
- **多模态融合的灵活性**：EPInformer 的融合层设计允许用户根据数据可用性灵活选择输入模态（仅序列、序列+表观、序列+表观+Hi-C），这种「渐进式增强」策略对数据稀缺场景具有实用价值。
- **注意力权重作为可解释输出**：将注意力机制从「黑盒组件」转化为「生物学假设输出」，为深度学习模型在调控基因组学中的应用提供了范式。

## 07 方法总览

- **输入**：(1) 启动子序列（2 kb，以 TSS 为中心）；(2) 候选增强子序列（最多 60 个，来自 ABC 流程识别的 DNase 峰，2 kb 窗口）；(3) 每个增强子的表观信号（DNase 和 H3K27ac 的 RPM 值）；(4) 增强子-启动子距离；(5) 可选 Hi-C 接触值；(6) mRNA 半衰期特征（8 维：GC 含量、UTR 长度、ORF 长度、内含子长度、外显子连接密度等）
- **输出**：基因表达水平（log10 转换后的 CAGE 或 RNA-seq 值）
- **模块**：
  1. **EPInformer-seq**：5 层残差卷积 + 4 层空洞卷积 + 线性层，将每条 2 kb 序列编码为 64 维嵌入
  2. **融合层**：将序列嵌入与表观信号、距离、Hi-C 接触值拼接，经 1×1 卷积降维
  3. **互作编码器**：3 层 transformer，每层 4 头注意力，注意力 mask 确保只关注 promoter-enhancer 对
  4. **预测器**：3 层全连接网络，输出表达值
- **训练**：PyTorch 2.2.0，AdamW 优化器（lr=5e-4, weight decay=1e-6, β1=0.9, β2=0.99），smooth L1 loss，early stopping（6 epochs 无改善则停止），单张 A100 GPU 约 1 小时
- **评估**：12 折跨染色体验证（每折留 2 条染色体测试，2 条验证，其余训练）
- **可解释性工具**：注意力权重归一化为增强子-基因互作分数；TF-MoDISco-lite + Tangermeme（DeepLIFT/ISM）进行 motif 发现
- **流程**：输入基因 TSS → 提取启动子序列 → ABC 流程识别候选增强子 → 编码序列和表观信号 → 融合层整合多模态 → transformer 建模互作 → 预测表达 → 提取注意力分数用于增强子优先级排序和 motif 分析

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| EPInformer-seq（序列编码器） | 从 2 kb DNA 序列学习启动子和增强子的序列嵌入 | DNA 序列是调控信息的载体，需提取 motif 级特征 | 输入：one-hot 序列 (2000, 4)；输出：64 维嵌入 | Results 图 2：仅序列输入的 EPInformer-PE 已达 0.78 相关 | [预期] 移除后模型无法学习序列特征，性能大幅下降 |
| 融合层 | 将序列嵌入与表观信号、距离、Hi-C 接触整合 | 多模态信息互补，表观信号反映增强子活性状态 | 输入：序列嵌入 + 表观特征；输出：融合嵌入 (61, 64) | Results 图 2a：加入表观信号后从 0.78 提升至 0.83 | [预期] 移除后丢失表观信息，性能下降至接近 EPInformer-PE 水平 |
| 互作编码器（transformer） | 用注意力显式建模启动子-增强子互作 | 增强子效应需通过空间互作传递至启动子 | 输入：融合嵌入 (61, 64)；输出：启动子上下文表示 | Results 图 3b：注意力分数优于 ABC 分数 | [预期] 移除后退化为简单的序列拼接模型，无法建模互作 |
| 预测器 | 从启动子表示预测表达值 | 将学习到的调控信息映射到表达水平 | 输入：64 维启动子表示 + 8 维 mRNA 半衰期特征；输出：标量表达值 | Results 图 2：整体性能优于所有基线 | [预期] 移除后无法输出表达预测 |
| 注意力权重提取 | 从互作编码器最后一层提取 promoter-enhancer 注意力分数 | 将模型内部注意力转化为可解释的增强子-基因互作预测 | 输入：transformer 注意力矩阵；输出：每个增强子的归一化分数 | Results 图 3b-f：CRISPR 验证和 eQTL 富集分析 | [预期] 移除后模型失去可解释性，无法进行增强子优先级排序 |

## 09 关键公式符号

**注意力机制公式**（Methods 节）：

Attention(Q, K, V, M) = softmax(QKᵀ/√dₖ · M) · V

- Q, K, V：查询、键、值矩阵，由输入嵌入 X ∈ R^(61×dₓ) 经可学习参数矩阵 W^Q ∈ R^(dₓ×d_q)、W^K ∈ R^(dₓ×d_k)、W^V ∈ R^(dₓ×d_v) 线性变换得到
- dₖ：键向量的维度，用于缩放点积防止 softmax 饱和
- M：mask 矩阵，对 padding 增强子位置设为接近负无穷的值，确保注意力忽略无效位置
- 单对 promoter-enhancer 的注意力权重：a_(P-Ei) = softmax(Q_P · K_Eiᵀ / √dₖ)，表示启动子查询对第 i 个增强子键的注意力权重

**增强子活性计算**（Methods 节，遵循 ABC 流程）：
- Enhancer activity = geometric mean of DNase and H3K27ac RPM（DNase 和 H3K27ac 信号的几何均值）

**损失函数**：smooth L1 loss（Huber loss），对预测值与真实表达值之间的差异进行鲁棒回归。

## 10 实验设计与证据链

**数据集与资源**：
- 6 个细胞系：K562, GM12878, HepG2, NHEK, HUVEC, H1
- 表观数据：ENCODE DNase-seq 和 H3K27ac ChIP-seq
- 染色质互作：4DN Nucleome Hi-C 数据
- 基因表达：CAGE（FANTOM）和 RNA-seq（Xpresso 数据集）
- 基因数量：18,377 个蛋白编码基因（训练/评估）
- 候选增强子：ABC 流程识别，每基因最多 60 个，100 kb 范围内
- 评估协议：12 折跨染色体验证（每折留 2 条染色体测试）
- 基线模型：Xpresso, Enformer, Borzoi, CREaTor, Seq-GraphReg
- 验证数据：K562 CRISPR 增强子扰动数据集（1,575 对，370 个实验验证）；GM12878 eQTL 数据（166 个远端非编码 eQTL，PIP > 70%）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| RNA-seq 表达预测 | EPInformer 优于现有方法 | 12 折跨染色体验证，6 细胞系 | EPInformer-PE-Activity-HiC 平均 Pearson r 最高（K562: 0.875, GM12878: 0.891） | EPInformer 在跨染色体泛化上优于 Xpresso、CREaTor | 未与 Enformer/Borzoi 在相同 RNA-seq 协议下直接对比 | Results 图 2a |
| CAGE 表达预测 | EPInformer 优于 Enformer/Borzoi | Enformer/Borzoi 官方测试集 | EPInformer-PE-Activity 超过 Enformer（K562: 0.841 vs 0.792；GM12878: 0.847 vs 0.800）；EPInformer-PE-Activity-HiC 超过 Borzoi | EPInformer 在 CAGE 预测上优于大规模预训练模型 | 对比使用不同训练协议，非完全公平 | Results 图 2b-d |
| 增强子-基因互作预测 | 注意力分数优于 ABC 分数 | K562 CRISPR 扰动数据，1,575 对 | Attention.score.Hi-C AUPRC 0.732 > ABC.score.Hi-C 0.698；Attention.score.distance 0.600 > ABC.score.distance 0.579 | 注意力分数更准确识别功能增强子 | 仅在 K562 一个细胞系验证 | Results 图 3b |
| 远端增强子预测 | 注意力分数在远端增强子上优势更大 | 按距离分层分析 | 60-100 kb 距离：Attention.score.Hi-C AUPRC 0.510 vs ABC.score.Hi-C 0.429 | 注意力机制更好捕获远端增强子效应 | 样本量在远端区间较小 | Results 图 3d |
| eQTL 富集 | 注意力分数富集因果变异 | GM12878 eQTL，PIP > 70% | Attention.score.Hi-C 在 recall < 10% 时富集显著高于 ABC.score.Hi-C | 注意力分数更好定位因果调控变异 | eQTL 样本量有限（n=166） | Results 图 3c, 3e |
| 消融分析 | 各模态贡献 | 移除 Hi-C、表观信号等 | 加入 Hi-C 和表观信号逐步提升性能 | 多模态整合有效 | 未提供逐模块消融的详细数值 | Results 图 2a |
| motif 发现 | 模型识别已知 TF motif | K562 和 GM12878 增强子 | 识别出 GATA1, GATA2, TAL1（K562 红系）和 SPI1, FOSL1（GM12878 淋巴）等细胞类型特异性 motif | 序列编码器学到有生物学意义的 TF 结合模式 | motif 验证限于已知数据库匹配 | Results 图 4b-c |
| KLF1 增强子案例 | 模型定位关键调控序列 | K562 中 KLF1 远端增强子 | 识别出 GATA1, SP4, ETV6 motif，与 CRISPRi 验证增强子区域重叠 | 模型可用于单基因调控机制解析 | 案例分析，非系统性验证 | Results 图 4d |

## 11 结论正确解读

- **任务范围**：本文解决的是**基因表达水平预测**（CAGE/RNA-seq），而非直接的 TF-DNA 结合预测。其与 TF-DNA 互作课题的关联在于：通过注意力机制和序列编码器间接推断增强子中的 TF 结合 motif 及其对基因表达的功能影响。
- **oracle/真值输入**：模型使用了 ABC 流程预定义的候选增强子（基于 DNase 峰），这相当于提供了「增强子位置」的先验知识。模型并未从零开始发现增强子，而是学习哪些候选增强子对目标基因重要。
- **端到端状态**：模型是端到端训练的（序列+表观 → 表达），但增强子候选集来自外部流程（ABC），并非完全端到端的增强子发现。
- **算力成本**：0.4M 参数、单 GPU 1 小时训练，远低于 Enformer/Borzaoi，但需要预计算 ABC 候选增强子。
- **历史数据依赖**：训练数据来自 ENCODE/4DN 等公开数据库，模型性能依赖这些数据的质量和细胞系覆盖度。
- **模型依赖**：性能依赖 ABC 流程的增强子候选质量；若 ABC 漏掉关键增强子，模型无法捕获。
- **最难情况**：跨染色体验证中，模型未见过的染色体上的基因表达预测；远端增强子（>60 kb）的互作识别。
- **群体/领域边界**：仅在 6 个人类细胞系中验证，未测试其他物种或更多细胞类型；主要针对蛋白编码基因，未覆盖非编码 RNA。
- **不确定性**：注意力分数与增强子功能之间的因果关系未直接验证（仅相关性）；eQTL 分析样本量有限。
- **有边界的复述**：EPInformer 在 6 个人类细胞系中，通过显式建模启动子-增强子互作，以 0.4M 参数的轻量级架构实现了优于 Xpresso、CREA Tor 的表达预测性能，并在 CAGE 预测上超过 Enformer/Borzoi；其注意力分数在 K562 CRISPR 验证数据中优于 ABC 分数，且能识别细胞类型特异性 TF motif。这些结论限于所测试的细胞系、基因集和评估协议。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 基因水平表达预测 | 模型预测基因总表达水平，而非等位基因特异性表达 | 未来可整合等位基因特异性数据 | Discussion |
| 仅使用激活型表观标记 | 当前实现聚焦 H3K27ac 和 DNase，未纳入抑制性标记（如 H3K27me3） | 未来版本可显式整合抑制性组蛋白修饰以区分活跃抑制与静息状态 | Discussion |
| 候选增强子依赖 ABC 流程 | 增强子候选集来自外部流程，可能遗漏部分调控元件 | 开发更完善的增强子定义方法 | Discussion |
| 单细胞类型建模 | 每个细胞类型单独训练模型，未利用跨细胞类型共享信息 | 多任务学习、跨细胞类型联合建模 | Discussion |
| 未建模 TF 协同效应 | 模型隐式学习 motif 组合，未显式建模 TF-TF 协同结合 | 引入蛋白质-DNA 互作先验知识 | Discussion |

**作者提及的相关约束（非正式局限）**：
- 模型输入需要预计算的 ABC 候选增强子，对无 DNase/H3K27ac 数据的细胞类型不适用
- 对比 Enformer/Borzoi 时使用了不同训练协议，非完全公平比较
- 增强子-基因互作验证依赖 CRISPR 数据，此类数据在多数细胞系中不可用

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 与 Enformer/Borzoi 的比较使用不同训练协议 | 性能差异可能部分来自训练数据/协议差异，而非架构优势 | 影响「优于 SOTA」结论的可靠性 | 在完全相同的训练/测试协议下重新对比 | Results 图 2b-d 描述 |
| 注意力分数与 ABC 分数比较的公平性 | ABC 分数是独立流程计算的，而注意力分数是端到端学习得到的，两者信息基础不同 | 影响「注意力优于 ABC」结论的解读 | 控制输入特征一致后比较 | Results 图 3b |
| 候选增强子来自 ABC 流程 | 模型性能可能受限于 ABC 增强子候选质量，存在循环依赖 | 影响模型独立发现增强子的能力评估 | 使用不同增强子定义流程（如 cCRE）对比 | Methods 节 |
| 注意力分数与 CRISPR 验证的相关性 | 注意力分数可能反映的是增强子活性而非增强子-基因连接的特异性 | 影响「注意力分数识别增强子-基因互作」结论 | 与随机增强子-基因对比较，检验连接特异性 | Results 图 3b-f |
| 仅 6 个细胞系验证 | 细胞类型多样性有限，可能无法代表广泛调控机制 | 影响泛化性结论 | 扩展到更多细胞类型和组织 | Results 图 2a |
| motif 发现依赖已知数据库匹配 | 可能遗漏新型或非经典 motif | 影响「发现新调控模式」的claim | 与 de novo motif 发现方法交叉验证 | Results 图 4 |
| 未报告置信区间和统计显著性 | 性能差异的统计显著性未充分报告 | 影响结论的稳健性 | 多次重复实验并报告方差 | Results 全文 |
| 模型对 TSS 注释的依赖 | 使用 Xpresso 的 TSS 注释，可能影响非经典 TSS 基因的预测 | 影响模型在 TSS 异质性场景的适用性 | 使用不同 TSS 注释源对比 | Methods 节 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **结构化注意力作为 TF-DNA 互作的可解释接口**：EPInformer 将「启动子-增强子」组织为 token 序列，注意力权重直接对应互作强度。这一设计可迁移到 TF-DNA 结合预测：将「TF 结合位点-目标基因启动子」组织为 token 对，用注意力权重表征结合强度，同时完成结合预测和功能注释。

2. **多模态融合的渐进式设计**：EPInformer 的融合层允许灵活添加/移除模态（序列→表观→Hi-C），这种设计对 TF-DNA 结合预测具有直接借鉴意义——可以从序列出发，逐步整合 ChIP-seq、ATAC-seq、甲基化等数据，适应不同数据可用性场景。

3. **轻量级架构 + 预训练编码器的组合策略**：EPInformer 用 0.4M 参数达到 SOTA 性能，关键在于将序列编码（EPInformer-seq）与互作建模分离，且序列编码器可独立预训练。这一「编码器预训练 + 任务特定头部」的范式可直接迁移到 TF 结合预测模型。

4. **注意力分数作为增强子优先级排序工具**：EPInformer 的注意力分数在 CRISPR 验证中优于 ABC 分数，说明学习到的注意力权重比手工设计的调控评分更有效。这一思路可迁移到 TF 结合位点功能优先级排序，替代或补充传统的 motif 匹配分数。

5. **跨染色体验证协议**：12 折跨染色体验证是评估模型泛化能力的严格协议，避免了同染色体训练/测试的信息泄漏。TF-DNA 结合预测模型应采用类似协议，确保模型学到的是通用调控规则而非染色体特异的记忆。

6. **TF-MoDISco-lite + 注意力分数的联合 motif 发现流程**：将注意力分数作为权重，引导 motif 发现聚焦于功能相关的增强子区域，比全基因组无差别扫描更高效。这一流程可直接用于 TF 结合 motif 的功能注释。

7. **mRNA 半衰期特征作为表达预测的辅助输入**：EPInformer 将 mRNA 稳定性特征（GC 含量、UTR 长度等）纳入预测，说明转录后调控对表达水平的重要贡献。TF-DNA 结合预测模型可考虑类似思路，将染色质状态等辅助特征纳入。

## 15 与已有知识连接

- **Enformer (Avsec et al., 2021, Nature Methods)**：EPInformer 的直接前身，本文在 CAGE 预测上超越 Enformer，但架构更轻量。Enformer 的 200 kb 输入窗口和 transformer 架构是 EPInformer 设计的基础。
- **Borzoi (Calico, 2023)**：扩展 Enformer 到 524 kb，EPInformer 在 CAGE 预测上超越 Borzoi，但参数减少 99.8%。
- **Xpresso (Agarwal & Shendure, 2020, PNAS)**：EPInformer 的 RNA-seq 预测基线，本文引入远端增强子信息后显著超越。
- **Seq-GraphReg (Karbalayghareh et al., 2022)**：图注意力网络整合 Hi-C 的先行工作，EPInformer 在 CAGE 预测上超越（0.883 vs 0.744），且不依赖 Hi-C 数据。
- **ABC model (Fulco et al., 2019, Nature Genetics)**：EPInformer 使用 ABC 流程定义候选增强子和计算增强子活性，是模型输入的基础。
- **TF-MOdisco-lite (Shrikumar et al., 2019)** 和 **Tangermeme**：用于模型解释和 motif 发现的标准工具，EPInformer 将其整合到注意力分数引导的分析流程中。
- **DeepLIFT (Shrikumar et al., 2017)**：用于计算核苷酸贡献分数的归因方法，EPInformer 用于 motif 发现。
- **候选方向**：与 AlphaFold 等结构预测方法不同，EPInformer 不预测 TF-DNA 三维结构，而是从序列和表观数据推断调控功能。与 DeepSEA、Basenji 等调控基因组学模型相比，EPInformer 的创新在于显式建模增强子-启动子互作而非全序列扫描。

## 16 研究想法

**Agent 生成的研究候选**：

1. **TF-EPInformer：将 EPInformer 架构迁移到 TF-DNA 结合预测**
   - **来源局限/观察**：EPInformer 的注意力机制有效建模增强子-启动子互作，但未直接预测 TF 结合。现有 TF 结合预测模型（如 DeepSEA）缺乏对远端调控互作的显式建模。
   - **核心假设**：将「TF motif 位置-目标启动子」组织为 token 对，用注意力权重表征结合强度，可同时预测 TF 结合和功能影响。
   - **初步方法**：将 EPInformer 的 promoter-enhancer 结构改为「TF 结合位点-启动子」结构，输入 TF  motif 序列和启动子序列，输出结合概率和表达影响分数。
   - **验证方式**：使用 ChIP-seq 数据评估结合预测 AUC，使用 CRISPR 扰动数据评估功能预测准确性。
   - **创新状态**：unverified

2. **多模态 TF 结合预测：整合序列、染色质可及性和 3D 互作**
   - **来源局限/观察**：EPInformer 证明多模态整合（序列+表观+Hi-C）优于单一模态。TF 结合预测通常仅用序列，忽略染色质状态。
   - **核心假设**：整合 ATAC-seq、ChIP-seq 和 Hi-C 数据可显著提升 TF 结合预测的细胞类型特异性。
   - **初步方法**：在 EPInformer 融合层基础上，加入 TF 特异性特征（如 motif 匹配分数、ChIP-seq 峰强度），训练多任务模型同时预测结合和表达。
   - **验证方式**：跨细胞类型迁移测试，比较与单模态模型的 AUC 差异。
   - **创新状态**：unverified

3. **注意力分数引导的 TF motif 功能优先级排序**
   - **来源局限/观察**：EPInformer 的注意力分数优于 ABC 分数，说明学习到的互作权重有功能意义。但 motif 发现仍依赖传统归因方法。
   - **核心假设**：将注意力分数作为 motif 重要性权重，可优先排序功能相关的 TF 结合位点。
   - **初步方法**：对 EPInformer 识别的增强子，用注意力分数加权 TF-MOdisco-lite 的 motif 发现结果，与未加权结果比较。
   - **验证方式**：使用 CRISPR 扰动和 eQTL 数据验证优先级排序的准确性。
   - **创新状态**：unverified

4. **跨细胞类型 TF 调控网络推断**
   - **来源局限/观察**：EPInformer 在单细胞类型中训练，未利用跨细胞类型共享的调控规则。
   - **核心假设**：多任务学习框架可同时建模多个细胞类型，捕捉共享和细胞类型特异的 TF 调控机制。
   - **初步方法**：将 EPInformer 扩展为多任务架构，共享序列编码器，每个细胞类型独立预测头，加入细胞类型嵌入。
   - **验证方式**：在 6 个细胞类型上交叉验证，比较与单细胞类型模型的性能差异。
   - **创新状态**：unverified

5. **TF 协同结合建模：显式编码 TF-TF 互作**
   - **来源局限/观察**：EPInformer 隐式学习 motif 组合，未显式建模 TF-TF 协同结合。TF 常以复合物形式协同调控基因表达。
   - **核心假设**：在注意力机制中加入 TF-TF 互作先验（如已知蛋白-蛋白互作），可提升对协同调控的预测。
   - **初步方法**：在互作编码器中加入 TF 类型嵌入，注意力权重分解为「TF-增强子」和「TF-TF」两个通道。
   - **验证方式**：使用已知协同 TF 对（如 GATA1-TAL1）验证模型是否学习到协同效应。
   - **创新状态**：unverified