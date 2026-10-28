## 01 基本信息

- **标题**：maxATAC: Genome-scale transcription-factor binding prediction from ATAC-seq with deep neural networks
- **作者与单位**：Cazares, Tareian A; Rizvi, Faiz W; Iyer, Balaji; Chen, Xiaoting; Kotliar, Michael; Bejjani, Anthony T; Wayman, Joseph A; Donmez, Omer; Wronowski, Benjamin; Parameswaran, Suresh; Kottyan, Leah C; Barski, Artem; Weirauch, Matthew T; Prasath, V B S; Miraldi, Emily R（单位：Cincinnati Children's Hospital Medical Center 等，具体单位未在摘要中列出）
- **期刊/预印本平台**：PLoS Computational Biology
- **年份**：2023
- **论文类型**：方法学 + 基准资源构建
- **领域**：计算基因组学 / 转录因子结合位点预测 / 深度学习
- **关键词**：ATAC-seq、转录因子结合位点预测、深度卷积神经网络、跨细胞类型预测、染色质可及性
- **DOI/arXiv 号**：10.1371/journal.pcbi.1010863
- **代码**：https://github.com/MiraldiLab/maxATAC
- **数据**：https://doi.org/10.5281/zenodo.6761768
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」方向，核心贡献是构建了基于 ATAC-seq 信号 + DNA 序列的跨细胞类型 TFBS 预测模型，并提供了大规模基准数据集（127 个 TF），是该方向目前规模最大的模型集合之一。

---

## 02 一句话总结

本文构建了 maxATAC——一组深度卷积神经网络模型，以 DNA 序列和 ATAC-seq 可及性信号为输入，在 127 个人类转录因子上实现跨细胞类型的 TFBS 预测，在 74 个可基准测试的 TF 上达到中位 AUPR 0.43，并证明其优于传统 motif 扫描和足迹分析（TOBIAS）。

---

## 03 研究问题

- **具体问题**：如何从 ATAC-seq 数据中准确预测转录因子结合位点（TFBS），尤其是在训练数据稀疏（仅 2–3 个细胞类型）的情况下实现跨细胞类型的泛化？
- **为什么重要**：TF–DNA 结合是基因调控的核心环节。实验测量 TF 占据（如 ChIP-seq）成本高、通量低，尤其难以覆盖大量 TF 和稀有细胞类型。ATAC-seq 数据快速增长，若能从中可靠预测 TFBS，将极大推动基因调控网络推断和疾病机制研究。
- **现有方法不足**：
  - 传统 motif 扫描精度低（中位 AUPR ~0.1），且依赖已知 motif 数据库，无法覆盖无 motif 的 TF。
  - 足迹分析（如 TOBIAS）依赖测序深度和切割模式，在稀疏数据下表现不佳。
  - 已有深度学习方法（如 Leopard、DeepGRN）多基于 DNase-seq 训练，未针对 ATAC-seq 优化，且模型数量有限。
- **精确研究问题**：Can a deep convolutional neural network trained on ATAC-seq signal and DNA sequence predict TFBS in cell types not used for training, with performance exceeding motif scanning and footprinting?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，部分经外部核验（标注）。

1. **早期：motif 扫描时代**（代表性方法：FIMO、MOODS + CIS-BP 数据库）
   - 优点：简单、可解释、无需训练数据
   - 局限：依赖已知 motif，精度低（中位 AUPR ~0.1），无法捕捉细胞类型特异性结合

2. **中期：染色质特征 + 经典机器学习**（代表性方法：ChromHMM、Centipede）
   - 优点：整合可及性、组蛋白修饰等特征
   - 局限：特征工程繁琐，跨细胞类型泛化有限

3. **深度学习兴起**（代表性方法：DeepBind、DeepSEA、Basset、Basenji）
   - 优点：自动学习序列特征，性能大幅提升
   - 局限：多为序列单输入，未整合染色质可及性；多为细胞类型内预测

4. **DNase-seq 时代的深度模型**（代表性方法：Leopard、DeepGRN、FactorNet）
   - 优点：整合 DNase-seq 信号，跨细胞类型预测能力提升
   - 局限：DNase-seq 数据量有限，未适配 ATAC-seq 特性

5. **本文位置**：首次系统构建 ATAC-seq 驱动的跨细胞类型 TFBS 预测模型集合（127 TF），并配套大规模基准数据集，填补了 ATAC-seq 时代深度模型缺失的空白。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| motif 扫描精度低 | 中位 AUPR ~0.1，远低于深度模型 | motif 数据库不完整，且 motif 存在本身不足以预测实际结合 | Results 图 3C |
| 足迹分析依赖测序深度 | TOBIAS 在稀疏数据下表现差 | 足迹检测需要高覆盖度的切割信号 | Results 图 S4B-S4D |
| 已有深度模型未适配 ATAC-seq | Leopard 等基于 DNase-seq 训练 | ATAC-seq 与 DNase-seq 信号特性不同（Tn5 切割偏好、线粒体污染等） | Discussion 节 |
| 训练数据稀疏 | 多数 TF 仅有 2–3 个细胞类型的 ChIP-seq | ChIP-seq 实验成本高，难以覆盖所有 TF×细胞类型组合 | Results 图 1B |
| 跨细胞类型泛化困难 | 模型在未见细胞类型上性能下降 | 细胞类型特异的染色质环境影响 TF 结合 | Results 图 3A-3B |
| 无 motif 的 TF 难以预测 | 部分 TF 缺乏已知 motif 注释 | CIS-BP 数据库覆盖不全 | Results 图 3C（motif-less 模型标注） |

---

## 06 核心思想

### 1) 表面方法
构建 127 个独立的深度卷积神经网络（每个 TF 一个模型），输入为 1,024bp × 5 的矩阵（4 通道 one-hot DNA 序列 + 1 通道 ATAC-seq 信号），输出为 32bp 分辨率的 TFBS 概率预测。采用「peak-centric, pan-cell」训练策略：训练样本来自 ATAC-seq 峰与 ChIP-seq 峰的并集，且训练样本跨多个细胞类型混合采样。

### 2) 核心洞察
- **ATAC-seq 信号是跨细胞类型泛化的关键**：仅靠 DNA 序列无法区分细胞类型特异的结合，而 ATAC-seq 提供了染色质环境的直接读数，使模型能够在未见过的细胞类型中推断 TF 结合。
- **「peak-centric」采样解决类别不平衡**：随机采样基因组会导致正样本过少，而仅在 ATAC-seq 峰内采样可有效富集正样本，同时保留挑战性负样本（可及但未结合的位点）。
- **「pan-cell」训练增强泛化**：将多个细胞类型的样本混合训练，迫使模型学习 TF 结合的通用规则，而非过拟合单一细胞类型。

### 3) 可能的普适教训 [Analysis]
- 对于「数据稀疏 + 跨条件泛化」的预测任务，**在相关但更易获取的辅助信号上训练**（如 ATAC-seq 作为 ChIP-seq 的代理）是一种高效策略。
- **挑战性负样本的设计**（可及但未结合）比随机负样本更能提升模型的判别能力。
- 单任务模型在数据量有限时可能优于多任务模型，因为多任务学习需要更大的数据规模才能发挥优势。

---

## 07 方法总览

- **输入**：1,024bp × 5 矩阵（one-hot DNA 序列 4 通道 + ATAC-seq 信号 1 通道）
- **输出**：32 × 1 的 TFBS 概率预测（32bp 分辨率）
- **模型架构**：深度扩张卷积神经网络（dilated CNN），5 个卷积块，每块含 2 层 ReLU 激活的 1D 卷积 + 批归一化，块间插入最大池化层；卷积核宽度固定为 7，滤波器数量从 15 逐块增长至 75；扩张率从 1 增至 16，感受野逐步扩展至 ±512bp
- **训练策略**：
  - 损失函数：交叉熵
  - 优化器：Adam，初始学习率 0.001
  - 训练轮数：100 epochs，batch size 1000，每 epoch 100 batches
  - 权重初始化：Glorot 初始化
  - 模型选择：基于验证集（chr2、chr19）的最大 Dice 系数
- **数据增强**：包含反向互补序列（序列和信号同时反转）
- **训练/验证/测试划分**：按细胞类型划分（N-1 个细胞类型训练，1 个测试），染色体独立划分（训练：chr3-7, 9-11, 13-15, 20；验证：chr2, 19；测试：chr1, 8）
- **推理流程**：输入 1,024bp 窗口 → CNN 前向传播 → 输出 32 个 32bp 窗口的 TFBS 概率 → 按 200bp bin 取最大值用于评估

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 扩张卷积层 | 多尺度捕获序列与信号模式 | 在有限层数下扩大感受野，同时保持 32bp 分辨率 | 输入：1,024×5 特征图；输出：同尺寸特征图 | Methods 节；Results 图 2 | 预期降低远距离特征捕获能力 [预期效应] |
| 批归一化 | 稳定训练、加速收敛 | 深度网络训练稳定性 | 输入：卷积输出；输出：归一化特征 | Methods 节 | 预期训练不稳定、收敛变慢 [预期效应] |
| 最大池化层 | 逐步降低空间维度 | 减少计算量，增加平移不变性 | 输入：卷积特征；输出：降采样特征 | Methods 节 | 预期分辨率降低，但 32bp 输出依赖池化设计 [预期效应] |
| Peak-centric 采样 | 富集正样本与挑战性负样本 | 基因组中 TFBS 极稀疏，随机采样效率低 | 输入：ATAC-seq 峰 ∪ ChIP-seq 峰；输出：训练样本集 | Results 图 S2A | 实测：随机采样性能显著下降（S2A 图） |
| Pan-cell 训练 | 跨细胞类型混合采样 | 增强模型在未见细胞类型的泛化能力 | 输入：多个训练细胞类型的样本；输出：混合训练集 | Results 图 S2A | 实测：去除后跨细胞类型性能下降（S2A 图） |
| 反向互补增强 | 数据增广 | 序列方向不应影响结合预测 | 输入：正向样本；输出：正向+反向样本 | Methods 节 | 预期小幅提升泛化 [预期效应] |
| 验证 Dice 系数模型选择 | 选择最优 epoch | 避免过拟合，平衡精度与召回 | 输入：验证集预测；输出：最优 epoch 参数 | Methods 节 | 预期使用其他指标可能导致精度-召回失衡 [预期效应] |

---

## 09 关键公式符号

**1. ATAC-seq 信号归一化（RP20M）**

$$RP20M_{scaled\ reads} = \frac{counts}{sequencing\ depth} \times 20{,}000{,}000$$

- $counts$：某位置的原始 read 计数
- $sequencing\ depth$：该样本的总测序深度

**2. 缩放因子**

$$scale\ factor = \frac{1}{sequencing\ depth} \times 20{,}000{,}000$$

**3. min-max 归一化（p 百分位）**

$$minmax_{P\%}(signal) = \frac{signal - min}{max_{P\%} - min}$$

- $min$：信号最小值
- $max_{P\%}$：第 p 百分位的信号值（p = 95% 或 99%）

**4. 交叉熵损失**

$$\mathcal{L} = -\frac{1}{N}\sum_{i=1}^{N}[y_i \log(\hat{y}_i) + (1-y_i)\log(1-\hat{y}_i)]$$

- $y_i$：真实标签（0/1）
- $\hat{y}_i$：模型预测概率

**5. Dice 系数（模型选择指标）**

$$Dice = \frac{2 \times TP}{2 \times TP + FP + FN}$$

- $TP$：真阳性数
- $FP$：假阳性数
- $FN$：假阴性数

**6. 精确率与召回率**

$$Precision = \frac{TP}{TP + FP}, \quad Recall = \frac{TP}{TP + FN}$$

**7. 随机精确率（用于 AUPR 比较）**

$$Precision_{random} = \frac{\text{number of positive bins}}{\text{total number of bins}}$$

---

## 10 实验设计与证据链

### 数据集与评估设置
- **训练数据**：CistromeDB + ENCODE 数据库，438 个 TF-细胞类型组合（127 个 TF，20 个细胞类型），仅使用未受扰动的实验
- **测试数据**：74 个 TF 有 ≥3 个细胞类型可用于跨细胞类型测试（N-1 交叉验证）
- **基准指标**：AUPR（200bp bin 分辨率）、precision at 5% recall
- **对比方法**：motif 扫描（CIS-BP + MOODS）、TOBIAS 足迹分析、平均训练 ChIP-seq 信号、Leopard（DNase-seq 训练的深度模型）
- **独立测试**：scATAC-seq（10x Genomics 平台）、原代 CD4+ T 细胞（刺激后 5 小时）

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 跨细胞类型基准测试 | maxATAC 优于 motif 扫描 | 74 TF，N-1 交叉验证 | 中位 AUPR = 0.43 vs motif 扫描 ~0.1 | maxATAC 显著优于 motif 扫描 | 未与所有现有深度模型逐一对比 | Results 图 3A-3C |
| 与 TOBIAS 比较 | maxATAC 优于足迹分析 | 55 个 TF 有 TOBIAS 结果 | maxATAC 在 AUPR 和 precision@5% recall 上均优于 TOBIAS（55/55 和 53/55） | maxATAC 优于足迹分析 | TOBIAS 在 precision@5% recall 上部分 TF 接近 | Results 图 S4B-S4D |
| 与平均训练 ChIP-seq 比较 | maxATAC 学到超越简单平均的信号 | 74 TF | maxATAC 在 61/74 TF 上优于平均 ChIP-seq 信号 | maxATAC 整合了序列与可及性信息 | 部分 TF 上平均 ChIP-seq 信号已足够好 | Results 图 3D |
| 与 Leopard 比较 | maxATAC 在 ATAC-seq 上优于 DNase-seq 模型 | 7 个共有 TF，8 个测试细胞类型 | maxATAC 在 20/29 比较中 AUPR 更高 | maxATAC 在 ATAC-seq 上具有优势 | Leopard 在部分比较中仍具竞争力 | Results 图 3E |
| 训练策略消融 | peak-centric, pan-cell 优于随机采样 | 11 TF 子集 | 100% peak-centric, pan-cell 训练性能最佳 | 训练采样策略对性能至关重要 | 未系统评估所有采样比例 | Results 图 S2A |
| scATAC-seq 泛化 | maxATAC 适用于单细胞数据 | 10x Genomics scATAC-seq，7 个共有细胞系 | 性能与 bulk ATAC-seq 相当 | maxATAC 可扩展至 scATAC-seq | 未测试罕见细胞类型 | Results 图 4 |
| 原代细胞泛化 | maxATAC 适用于原代细胞 | 刺激的 CD4+ T 细胞，3 TF（FOS, JUNB, MYC） | 优于 motif 扫描，与 ChIP-seq 一致性良好 | maxATAC 可推广至原代细胞 | 仅测试 3 个 TF | Results 图 6 |
| 特应性皮炎风险位点 | maxATAC 可识别疾病相关 TFBS | 6 患者 vs 6 对照，2 个风险位点 | 识别出 MYB 和 FOXP1 的等位基因依赖性结合 | maxATAC 可用于疾病机制研究 | 样本量小，需功能验证 | Results 图 7 |

---

## 11 结论正确解读

- **任务范围**：本文解决的是「从 ATAC-seq + DNA 序列预测 TFBS」任务，输出为 32bp 分辨率的二值预测。它不预测 TF 结合强度（定量），也不建模 TF-TF 协同或竞争。
- **Oracle/真值输入**：训练和评估均使用 ChIP-seq 峰作为金标准。ChIP-seq 本身有噪声和抗体依赖性，因此模型性能上限受限于 ChIP-seq 质量。
- **端到端状态**：模型是端到端训练的（序列 + 信号 → 预测），但信号预处理（Tn5 偏移、归一化）是手工流程。
- **跨细胞类型泛化的边界**：模型在「训练中见过的细胞类型」上表现最好；对「全新细胞类型」的泛化依赖于该细胞类型的 ATAC-seq 信号质量。对于信号诱导型 TF（如激素激活），模型可能失效，因为训练数据排除了扰动条件。
- **性能边界**：中位 AUPR = 0.43 意味着在 200bp 分辨率下，模型能恢复约 43% 的精确-召回曲线下面积，但不同 TF 间差异巨大（0.01–0.75）。对于结合位点分散、motif 弱的 TF（如 NFXL1），性能接近随机。
- **与 ChIP-seq 的关系**：模型不是要替代 ChIP-seq，而是在 ChIP-seq 不可行时提供「in silico ChIP-seq」的近似。对于疾病位点分析，模型预测需要实验验证。
- **不确定性**：模型输出为概率分数，但未提供校准的不确定性区间。用户需根据验证集 precision/recall 自行选择阈值。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 训练数据稀疏 | 53/127 个 TF 仅有 2 个细胞类型可用于训练，无法进行跨细胞类型测试 | 持续扩充训练数据，纳入更多细胞类型和 TF | Results 图 1B；Discussion 节 |
| 二值预测 | 模型将 TFBS 预测为二值事件，忽略结合强度的定量信息 | 采用定量损失函数建模 ChIP-seq 信号强度 | Discussion 节 |
| 独立训练 | 每个 TF 单独建模，未利用 TF 之间的共享信息 | 探索多任务学习、预训练-微调策略 | Discussion 节 |
| 信号诱导型 TF 缺失 | 训练数据排除了扰动条件，模型无法预测信号诱导的 TF 结合 | 纳入扰动条件下的 ChIP-seq 和 ATAC-seq 数据 | Methods 节（数据筛选标准） |
| 跨平台泛化有限 | 模型在非 ATAC-seq 平台（如 DNase-seq）上性能下降 | 开发平台自适应方法 | Results 图 5 |
| 分辨率限制 | 32bp 输出分辨率不足以精确到单碱基 | 采用更高分辨率的输出层设计 | Discussion 节 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 与 Leopard 的比较仅在 7 个 TF 上进行 | 7 个 TF 可能不代表整体性能；Leopard 在 DNase-seq 上训练，直接比较可能有失公平 | 影响「maxATAC 优于现有方法」的结论强度 | 在更多共有 TF 上比较，或重新训练 Leopard 于 ATAC-seq 数据 | Results 图 3E |
| 「peak-centric」采样可能引入标签泄漏 | 训练样本来自 ATAC-seq 峰 ∪ ChIP-seq 峰，测试时也使用 ATAC-seq 峰，可能高估真实泛化性能 | 若存在泄漏，模型在随机基因组区域上的表现可能远低于报告值 | 在随机采样的基因组区域上评估模型 | Methods 节（训练采样策略） |
| 中位 AUPR 0.43 的解读需谨慎 | AUPR 对正样本比例敏感；不同 TF 的正样本数量差异大，直接比较 AUPR 可能误导 | 影响对模型「好」或「差」的判断 | 报告标准化 AUPR 或使用其他指标（如 NDCG） | Results 图 3A-3B |
| 未与最新的基础模型（如 Enformer）比较 | Enformer 等模型在序列-功能预测上表现优异，可能优于 maxATAC | 影响「最先进」的定位 | 在相同基准上比较 maxATAC 与 Enformer 等 | Discussion 节（未提及） |
| 特应性皮炎分析缺乏功能验证 | 预测的 MYB/FOXP1 结合位点未通过实验（如 CRISPR、EMSA）验证 | 影响「发现疾病机制」的结论强度 | 进行实验验证或至少使用独立数据集复现 | Results 图 7 |
| 模型可解释性有限 | 虽然用 DeepLIFT/TF-MoDISco 提取了 motif，但未系统评估这些 motif 与已知 motif 的一致性 | 影响对模型学习机制的信任 | 与 CIS-BP 数据库系统比对提取的 motif | Results 节（模型解释部分） |

---

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题方向。

1. **ATAC-seq 信号作为跨细胞类型泛化的关键桥梁**：纯序列模型难以区分细胞类型特异的 TF 结合，而整合染色质可及性信号可显著提升跨细胞类型预测能力。这一思路可迁移至其他「序列 + 环境」联合建模任务，如 DNA 甲基化、组蛋白修饰预测。

2. **「Peak-centric, pan-cell」采样策略**：在正样本极稀疏的任务中，从「候选区域」（而非全基因组）采样可有效提升训练效率；跨条件混合采样可增强模型泛化。此策略适用于任何「稀有事件 + 多条件」的预测问题。

3. **扩张卷积 + 多尺度感受野**：通过扩张率递增的卷积层，在保持高分辨率输出的同时扩大感受野，是处理长序列（1kb+）局部与远程特征的有效架构选择。可迁移至 TF 结合机制中的协同结合、远端调控元件建模。

4. **验证集 Dice 系数作为模型选择标准**：在不平衡分类任务中，Dice 系数比准确率或 AUROC 更合适，因为它直接优化了精确率与召回率的调和平均。此经验适用于 TFBS 预测、蛋白质互作位点预测等不平衡问题。

5. **「In silico ChIP-seq」的概念**：用深度学习模型为大量 TF 提供「虚拟 ChIP-seq」预测，可在实验不可行时提供假设生成工具。这一概念可扩展至「in silico 突变扫描」——预测 TF 结合对序列变异的敏感性。

6. **模型解释与机制发现**：DeepLIFT + TF-MoDISco 可从训练好的模型中提取序列 motif，用于发现非经典结合模式。这为「AI 辅助发现新 TF 结合机制」提供了可操作的技术路径。

7. **数据质量控制的严格性**：手动验证每个 ChIP-seq 实验的注释、排除扰动条件、统一 peak calling 标准，是构建可靠基准的关键。对于任何「AI + 组学数据」项目，数据清洗流程的严谨性直接影响模型可信度。

---

## 15 与已有知识连接

1. **ENCODE-DREAM Challenge（2017）**：本文直接对标该挑战赛的基准设置，但将数据从 DNase-seq 扩展到 ATAC-seq，并将 TF 数量从 12 扩展到 127。可对比阅读挑战赛冠军方法（如 FactorNet）的架构设计。

2. **Leopard（Chen et al., 2021）**：本文最直接的对比方法，基于 DNase-seq 训练的深度模型。两者差异在于输入信号类型和训练数据规模，可深入分析 ATAC-seq 与 DNase-seq 信号对 TFBS 预测的差异贡献。

3. **DeepSEA / Basenji / Enformer**：这些模型从序列预测多种功能基因组信号（包括 TF 结合），但均为「序列 → 信号」的通用模型，不针对特定 TF 或细胞类型。maxATAC 的独特之处在于「序列 + 可及性 → 特定 TF 结合」的条件预测框架。

4. **TOBIAS（Bentsen et al., 2020）**：基于 ATAC-seq 足迹的经典方法，本文系统比较了 maxATAC 与 TOBIAS 的性能，结论是深度模型在大多数 TF 上优于足迹分析。

5. **CIS-BP 数据库**：本文使用 CIS-BP v2 作为 motif 扫描的参考数据库，也是评估无 motif TF 预测难度的依据。该数据库的覆盖度直接影响 motif 扫描基线的公平性。

6. **扩张卷积网络（Dilated CNN）**：架构灵感来自 WaveNet 等模型，在基因组序列建模中已有应用（如 DeepCpG）。本文将其与 ATAC-seq 信号结合，验证了该架构在「序列 + 信号」联合输入下的有效性。

7. **单细胞 ATAC-seq 分析流程**：本文展示了模型在 scATAC-seq 上的应用，与 ArchR、SnapATAC 等工具链互补——后者负责聚类和注释，maxATAC 提供 TF 层面的功能解读。

---

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题方向。

### 候选 1：基于 maxATAC 的 TF 协同结合预测
- **名称**：CoBindNet：从单 TF 预测扩展到 TF-TF 协同结合建模
- **来源局限/观察**：maxATAC 对每个 TF 独立建模，未显式建模 TF 之间的协同或竞争关系；而真实调控中 TF 常协同结合增强子
- **核心假设**：在 maxATAC 架构中加入「TF 对共现」的注意力机制，可提升协同结合位点的预测精度
- **初步方法**：在 maxATAC 输出层之上增加 TF-TF 共现注意力层，或在训练时引入多任务损失（同时预测多个 TF）
- **验证方式**：使用 ENCODE 中同一细胞类型的多 TF ChIP-seq 数据，比较 CoBindNet 与单 TF 模型在协同结合区域的 AUPR
- **创新状态**：unverified

### 候选 2：将 maxATAC 预测与 3D 基因组结构整合
- **名称**：3D-TF：利用 Hi-C 环状互作信息增强 TFBS 预测
- **来源局限/观察**：maxATAC 对每个 1kb 窗口独立预测，未利用增强子-启动子环状互作信息；而 TF 结合常发生在空间邻近的调控元件上
- **核心假设**：将 Hi-C 互作矩阵作为图结构输入，可提升远端增强子上 TFBS 的预测精度
- **初步方法**：构建「窗口-窗口」图，节点为 1kb 窗口，边权重为 Hi-C 互作强度；用图神经网络（GNN）对 maxATAC 预测进行后处理或端到端联合训练
- **验证方式**：在 GM12878 等有 Hi-C 数据的细胞系上，比较 GNN 增强模型与原始 maxATAC 在远端增强子区域的 AUPR
- **创新状态**：unverified

### 候选 3：用 AlphaFold 结构信息约束 TFBS 预测
- **名称**：StructTF：将 TF-DNA 结构预测与序列-可及性模型融合
- **来源局限/观察**：maxATAC 是纯序列-信号模型，未利用 TF 的 3D 结构信息；而 TF 的 DNA 结合域结构决定了其序列偏好
- **核心假设**：将 AlphaFold 预测的 TF 结构特征（如 DNA 结合域的表面电荷分布）作为条件输入，可提升对低表达或结构特殊 TF 的预测
- **初步方法**：对每个 TF 提取 AlphaFold 结构嵌入，与 maxATAC 的序列嵌入拼接，训练条件生成模型
- **验证方式**：在结构已知的 TF 子集上比较 StructTF 与 maxATAC 的性能，分析结构特征对预测增益的贡献
- **创新状态**：unverified

### 候选 4：等位基因特异性 TFBS 预测的深度模型
- **名称**：AlleleTF：从 ATAC-seq 预测等位基因特异性 TF 结合
- **来源局限/观察**：maxATAC 使用参考基因组序列，未利用个体水平的遗传变异信息；而等位基因特异性结合是疾病机制研究的关键
- **核心假设**：将 SNP 信息编码为序列变异通道，可预测 SNP 对 TF 结合的等位基因效应
- **初步方法**：在 maxATAC 输入中增加「变异通道」（参考/替代等位基因差异），训练模型预测等位基因特异性结合概率
- **验证方式**：使用已发表的等位基因特异性 ChIP-seq 数据（如 ENCODE 的 heterozygous SNP 分析）评估
- **创新状态**：unverified

### 候选 5：基于 maxATAC 的 TF 结合机制可解释性分析
- **名称**：TF-MechX：用可解释性方法揭示 TF 结合的决定性序列与信号特征
- **来源局限/观察**：maxATAC 是黑盒模型，虽用 DeepLIFT 提取了 motif，但未系统分析不同 TF 的「序列 vs 可及性」依赖差异
- **核心假设**：通过系统化的可解释性分析，可揭示 TF 结合机制的类型学（如「序列主导型」vs「可及性主导型」）
- **初步方法**：对 127 个 TF 模型计算序列和信号通道的梯度归因，聚类分析 TF 的「机制指纹」
- **验证方式**：将聚类结果与 TF 的已知功能分类（如 pioneer factor vs settler factor）对比
- **创新状态**：unverified

### 候选 6：将 maxATAC 扩展至非人类物种
- **名称**：xATAC：跨物种 TFBS 预测的迁移学习
- **来源局限/观察**：maxATAC 仅覆盖人类 TF，而模式生物（小鼠、斑马鱼等）的 TFBS 预测需求同样迫切
- **核心假设**：人类训练的模型可通过迁移学习适配至其他物种，尤其是 TF 结合域高度保守的家族
- **初步方法**：使用人类模型作为预训练，用小鼠等物种的少量 ChIP-seq 数据进行微调
- **验证方式**：在小鼠 ENCODE 数据上评估迁移学习 vs 从头训练的性能差异
- **创新状态**：unverified