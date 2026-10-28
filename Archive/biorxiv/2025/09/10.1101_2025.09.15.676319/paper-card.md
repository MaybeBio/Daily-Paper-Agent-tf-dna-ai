## 01 基本信息

- **标题**：Integrating Protein and DNA Embeddings for Improving Genome-Wide Transcription Factor Binding Site Prediction
- **作者**：Shreya Basnet; Jianlin Cheng
- **单位**：未提供（作者信息中未列出单位）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2025
- **论文类型**：预印本（方法学/应用研究）
- **领域**：计算生物学；调控基因组学；深度学习
- **关键词**：转录因子结合位点预测、蛋白质语言模型、DNA序列嵌入、交叉注意力、零样本预测
- **DOI/arXiv 号**：10.1101/2025.09.15.676319
- **代码**：https://github.com/jianlin-cheng/TransBind
- **数据**：EPBDXDNA 数据集（源自 ENCODE ChIP-seq，690 个 TF-细胞类型实验，161 个 TF，91 个人类细胞类型）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文是「TF–DNA 结合机制 × 深度学习」方向的直接工作，首次将蛋白质语言模型（ESM-DBP）生成的 TF 嵌入与 DNA 序列特征通过交叉注意力机制整合，用于全基因组 TF 结合位点预测，并支持对未见 TF 的零样本预测。与仅用 DNA 序列的经典方法（DeepSEA、DanQ、TBiNet）形成对照，属于「蛋白质信息增强 DNA 结合预测」这一新兴子方向。

---

## 02 一句话总结

本文提出 TransBind，一种将 TF 蛋白质嵌入（由 ESM-DBP 生成）与 DNA 序列嵌入通过交叉注意力机制融合的深度学习架构，在 690 个 ChIP-seq 实验（161 个 TF、91 个细胞类型）上以 AUROC 0.950、AUPR 0.371 超越现有方法，并实现对训练中未见 TF 的零样本结合位点预测。

---

## 03 研究问题

- **具体问题**：现有深度学习方法仅使用 DNA 序列信息预测 TF 结合位点，完全忽略 TF 蛋白质的序列和结构特征，导致（1）预测精度受限；（2）无法泛化到训练数据中未出现的 TF。
- **为什么重要**：人类基因组中有超过 1,600 个预测 TF，但大多数缺乏 ChIP-seq 数据。若能利用 TF 蛋白质本身的信息进行零样本预测，将极大加速未表征 TF 的调控注释和疾病相关非编码变异解读。
- **现有方法为何不足**：DeepSEA、DanQ、TBiNet 等均为「DNA-only」模型——输入固定长度的 DNA 序列，输出一组预定义 TF 的结合概率。它们无法对训练集之外的 TF 做预测，也无法利用 TF 之间的相似性进行知识迁移。
- **精确研究问题**：Can a deep learning model that integrates TF protein embeddings with DNA sequence embeddings via cross-attention achieve higher accuracy in TF binding site prediction and generalize to unseen TFs in a zero-shot manner?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 及相关引用，属于「经外部核验」的领域发展框架。

1. **早期序列模型**：位置权重矩阵（PWM）、隐马尔可夫模型（HMM）、支持向量机（SVM）——依赖手工特征，高假阳性率，无法捕捉复杂非线性互作。
2. **第一代深度学习**：DeepBind（CNN 学习 DNA 基序）→ DeepSEA（多任务 CNN 预测染色质特征）→ DanQ（CNN+RNN 捕捉长程依赖）→ TBiNet（双向 Transformer 增强序列建模）。这些方法均为 DNA-only，输入序列、输出预定义 TF 集合的结合概率。
3. **蛋白质语言模型兴起**：ESM-2 等 PLM 从海量蛋白质序列中学习结构-功能表征；ESM-DBP 进一步在 DNA 结合蛋白上微调，编码与 DNA 识别相关的生化特征。
4. **本文主张的位置**：首次将 PLM 生成的 TF 嵌入与 DNA 序列嵌入通过交叉注意力动态融合，使模型「知道」每个 TF 的独特结合偏好，而非对所有 TF 共享同一套序列特征提取器。同时将多标签分类重构为「TF-DNA 对」二分类，实现零样本泛化。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| DNA-only 模型忽略 TF 身份 | 所有 TF 共享同一套序列特征提取器，无法区分不同 TF 的结合偏好 | 输入仅含 DNA 序列，TF 信息完全缺失 | Introduction：「almost all existing approaches use only DNA sequences and/or other genomics data as input without using TF information at all」 |
| 无法泛化到新 TF | 对训练集中未出现的 TF 完全无法预测 | 模型输出层固定为预定义 TF 集合，无 TF 输入通道 | Introduction：「makes the methods not generalizable to predicting binding sites of new TFs that do not exist in the training data」 |
| 预测精度受限 | AUPR 显著低于蛋白质感知模型 | 忽略 TF 蛋白序列/结构决定 DNA 识别特异性这一生物学事实 | Results 表 2：TransBind AUPR 0.371 vs TBiNet 0.333（相对提升 ≥11.3%） |
| 类别极度不平衡 | 约 50% 的 TF-细胞类型实验中 TF 结合频率 <1% | ChIP-seq 实验本身的性质：大多数 TF 在大多数基因组区域不结合 | Materials and Methods 图 1：「in approximately 50% of the TF-cell type experiments the TF binds to fewer than 1% of bins」 |
| 缺乏可解释性 | 黑箱预测难以验证模型是否学到真实调控基序 | 多数深度模型不提供基序层面的解释 | Results 图 5：TransBind 通过基序恢复分析（TOMTOM vs JASPAR）提供可解释性证据 |

---

## 06 核心思想

### 1) 表面方法
- 用 ESM-DBP（DNA 结合蛋白微调的 PLM）为每个 TF 生成 1280 维嵌入，经线性投影降至与 DNA 特征同维。
- DNA 序列经 Conv1D + BiLSTM + Transformer 编码为位置特征 H 和全局特征 x₁。
- 通过交叉注意力（TF 嵌入作为 query，DNA 位置特征作为 key/value）生成 TF 感知的 DNA 摘要向量 z，与 x₁ 拼接后经全连接层输出结合概率。

### 2) 核心洞察
- **生物学洞察**：TF–DNA 识别是「双向匹配」——DNA 序列特征本身不足以决定结合与否，必须结合 TF 的氨基酸序列/结构特征。不同 TF 的 DNA 结合域（DBD）不同，识别模式也不同。
- **架构洞察**：交叉注意力天然模拟「TF 扫描基因组」的过程——TF 嵌入作为 query 主动「查询」DNA 各位置，注意力权重即 TF 对各基因组区域的结合倾向。这比简单的拼接或相加更符合生物学机制。
- **任务重构洞察**：将多标签分类（一个 DNA 序列 → 多个 TF 的概率）重构为「TF-DNA 对」二分类（一个 TF + 一个 DNA 序列 → 是否结合），使模型学习的是「通用互作规则」而非「特定 TF 的模式」，从而支持零样本预测。

### 3) 可能的普适教训 [Analysis]
- 在分子互作预测中，**双侧信息融合**（蛋白质 + DNA/配体）通常优于单侧信息，因为互作本质是双方特征的联合函数。
- 交叉注意力是「条件化特征提取」的通用范式：让一个模态的信息引导另一个模态的特征选择，可迁移到蛋白质-蛋白质、蛋白质-RNA、药物-靶点等互作预测。
- 将「封闭集分类」重构为「开放集匹配」是获得零样本泛化能力的关键架构决策。

---

## 07 方法总览

- **输入**：
  - DNA：1,000 bp 序列（200 bp bin + 两侧各 400 bp 上下文），one-hot 编码为 1000 × 4 矩阵
  - 蛋白质：TF 氨基酸序列（来自 UniProt），经 ESM-DBP 生成 1280 维嵌入
- **输出**：对每个 TF-细胞类型实验，输出该 DNA bin 是否包含 TF 结合位点的二分类概率
- **模块**：
  1. **DNA 编码器**：Conv1D（320 filters，kernel size 26）→ ReLU → MaxPool（window 13）→ 2 层 BiLSTM（160 hidden units/方向）→ Transformer encoder（16 heads，feed-forward 1024）→ 位置特征 H（75 × 320）和全局特征 x₁（平均池化）
  2. **蛋白质编码器**：ESM-DBP 生成 1280 维嵌入 → 线性投影至 320 维（与 DNA 特征同维）
  3. **交叉注意力融合**：TF 嵌入作为 query，H 作为 key/value → TF 感知的 DNA 摘要 z → 与 x₁ 拼接 → 2 层全连接 → sigmoid
- **训练**：PyTorch Lightning；损失函数为带 logits 的二元交叉熵；优化器 AdamW（lr=3.28×10⁻⁴，weight decay=0.028）；cosine annealing 调度，60 epochs；dropout=0.088；batch size=256；超参数经 Optuna 在验证集上优化
- **零样本变体（TransBind zeroshot）**：架构相同，仅将多标签输出层改为单输出二分类，训练时每个 DNA bin 与多个 TF 配对，测试时对未见 TF 直接输入其 ESM-DBP 嵌入进行预测
- **数据划分**：染色体级别划分（chr8/9 测试，chr7 验证，其余训练），与 DeepSEA 一致

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Conv1D 基序检测层 | 从 DNA 序列中提取局部基序模式 | 捕获 TF 结合的序列偏好（类似 PWM 的深度学习版本） | 输入：1000×4 one-hot；输出：320 通道特征图 | Results 图 5：基序恢复分析证明卷积核学到真实 TF 基序 | [预期] 失去局部基序检测能力，模型退化为纯长程特征提取，精度显著下降 |
| BiLSTM 长程依赖层 | 捕捉序列上下游上下文信息 | TF 结合常受邻近序列环境影响 | 输入：卷积池化后特征；输出：双向上下文特征 | 继承自 DanQ 的成熟设计 | [预期] 失去对远端调控元件的感知，AUPR 下降 |
| Transformer 自注意力层 | 全局整合序列各位置信息 | 使模型能关注远距离的协同调控信号 | 输入：BiLSTM 输出 + 位置编码；输出：75×320 上下文特征 | 继承自 TBiNet 的设计 | [预期] 长程依赖建模能力减弱 |
| ESM-DBP 蛋白质嵌入 | 生成 TF 的序列+结构特征表示 | 提供 TF 身份和 DNA 结合域信息，是本文核心创新 | 输入：TF 氨基酸序列；输出：1280 维嵌入 | 表 2：完整 TransBind 优于所有 DNA-only 基线 | [实测] 消融实验（表 4）显示移除蛋白质特征后 AUPR 从 0.3710 降至 0.3685 |
| 交叉注意力融合 | 让 TF 嵌入选择性关注 DNA 序列相关区域 | 模拟 TF 扫描基因组并聚焦结合位点的生物学过程 | 输入：TF query + DNA key/value；输出：TF 感知的 DNA 摘要 z | 表 2：相对 TBiNet AUPR 提升 ≥11.3% | [预期] 移除后模型退化为 DNA-only，丧失 TF 特异性 |
| 全连接分类头 | 将融合特征映射为结合概率 | 最终决策层 | 输入：z 与 x₁ 拼接；输出：sigmoid 概率 | 表 2、表 3 | [预期] 分类能力丧失 |

---

## 09 关键公式符号

本文未提供显式公式编号，以下为方法描述中隐含的关键计算：

1. **交叉注意力**：
   - q = x₂W_q ∈ ℝ^{1×d}（TF 嵌入作为 query）
   - K = HW_k ∈ ℝ^{L×d}，V = HW_v ∈ ℝ^{L×d}（DNA 位置特征作为 key/value）
   - Attention(Q,K,V) = softmax(qK^T/√d)·V
   - 其中 x₂ 为投影后的 TF 嵌入（1280→320 维），H 为 DNA 位置特征（75×320），W_q、W_k、W_v 为可学习投影矩阵，d 为注意力维度

2. **蛋白质嵌入投影**：
   - x₂ = W_p · ESM-DBP(TF_sequence) + b_p
   - 将 1280 维 ESM-DBP 嵌入线性投影至 320 维

3. **最终预测**：
   - p(binding) = σ(MLP([z; x₁]))
   - z 为交叉注意力输出，x₁ 为 DNA 全局嵌入（平均池化），σ 为 sigmoid 函数

4. **损失函数**：L = BCEWithLogitsLoss(y, ŷ)，对 690 个 TF-细胞类型实验分别计算后取平均

---

## 10 实验设计与证据链

**数据集**：
- EPBDXDNA 数据集（DeepSEA 数据集的更新版，基于 hg19）
- 690 个 TF-细胞类型 ChIP-seq 实验，161 个 TF，91 个人类细胞类型
- 1,903,668 个唯一 200 bp bin（去除含 N 的序列后），正负样本比例约 1.44% 为正
- 染色体级别划分：chr8/9 测试，chr7 验证，其余训练

**指标**：AUROC、AUPR

**基线**：DeepSEA、DanQ、TBiNet、DNABERT-2（均在相同训练集上重新训练）

**评测协议**：盲测（blind evaluation）于测试集，所有模型使用相同数据划分

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 主实验：全模型对比 | TransBind 优于现有 SOTA | 与 DeepSEA、DanQ、TBiNet、DNABERT-2 在相同测试集上对比 | AUROC 0.950，AUPR 0.371；相对 TBiNet AUPR 提升 ≥11.3% | 蛋白质信息增强 DNA 结合预测有效 | 未报告各基线具体数值，无法判断提升的统计显著性 | Results 表 2 |
| 逐 TF-细胞类型对比 | TransBind 在大多数组合中优于 TBiNet | 690 个组合逐一对比 | AUROC 胜出 96.1%（663/690），AUPR 胜出 97.1%（670/690） | 优势具有广泛性而非少数案例驱动 | 未报告失败案例的特征分析 | Results 图 4 |
| 消融实验 | 蛋白质特征贡献 | 有/无蛋白质嵌入的 TransBind | AUROC 0.9493→0.9504，AUPR 0.3685→0.3710 | 蛋白质特征带来一致提升 | 提升幅度较小（AUPR +0.0025），需统计检验确认显著性 | Results 表 4 |
| 基序恢复分析 | 模型学到真实 TF 基序 | 320 个卷积核 vs JASPAR 数据库 | 160 个核匹配已知基序（p<0.05），27 个达 p<10⁻⁶ | 模型具有生物学可解释性 | 未报告与基线模型的基序恢复率对比 | Results 图 5 |
| 零样本预测 | 对未见 TF 可预测 | HNF1A、ATF4、FOXA3（分别属 homeodomain、bZIP、forkhead 家族） | AUROC 0.575–0.628，显著高于随机（0.5） | 零样本泛化可行 | 性能中等，且仅测试 3 个 TF，样本量小 | Results 表 3 |

---

## 11 结论正确解读

- **任务范围**：本文解决的是「给定 TF 和 DNA 序列，预测是否结合」的二分类问题，而非「预测结合强度/亲和力」或「在全基因组中扫描峰位」。
- **oracle/真值输入**：训练标签来自 ChIP-seq 峰（ENCODE 标准化流程），本质是体内结合事件，受染色质可及性、共因子等因素影响，并非纯体外亲和力。
- **端到端状态**：模型端到端训练，但 TF 嵌入来自预训练 ESM-DBP（冻结或微调未明确说明），DNA 编码器从头训练。
- **算力成本**：未报告训练时间、GPU 数量等。
- **历史数据依赖**：训练数据仅来自人类（91 个细胞类型），跨物种泛化未验证。
- **模型依赖**：性能依赖 ESM-DBP 嵌入质量；若 ESM-DBP 对某类 TF 嵌入不佳，预测可能失效。
- **最难情形**：类别极不平衡（1.44% 正样本），AUPR 0.371 虽优于基线但仍偏低，说明正样本召回仍是瓶颈。
- **零样本性能边界**：AUROC 0.575–0.628 仅略高于随机，实际应用需谨慎；且仅测试 3 个 TF。
- **有边界的复述**：在人类 ChIP-seq 数据上，将 TF 蛋白质嵌入与 DNA 序列通过交叉注意力融合，可在多标签预测中取得优于 DNA-only 方法的性能，并初步展示对未见 TF 的零样本预测能力；但零样本性能中等，且未验证跨物种、跨细胞类型的泛化。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 零样本预测性能中等 | AUROC 仅 0.575–0.628 | 使用更大规模、更多样化的训练数据（涉及更多 TF） | Discussion：「The performance of the zero-shot prediction (i.e., AUROC between 0.575 and 0.628) is moderate」 |
| 训练数据量有限 | 仅 161 个 TF | 需要数百或更多 TF 的训练数据以提升泛化 | Discussion：「a much larger training dataset involving hundreds or more TFs may be needed」 |
| 未考虑染色质可及性 | 模型仅用 TF 和 DNA 序列，未纳入染色质状态 | 整合 ATAC-seq 染色质可及性数据 | Discussion：「without considering the accessibility of chromatin and the higher-order chromatin architecture」 |
| 未利用 3D 结构信息 | 蛋白质嵌入仅含间接结构信息 | 直接使用 TF 的 3D 结构（如 AlphaFold 预测） | Discussion：「protein embeddings derived from the protein language model contain only protein sequence and indirect structural information, without directly leveraging the 3D structures of TFs」 |
| 零样本模型缺少细胞类型信息 | 与多标签模型不同，零样本模型未隐式编码细胞类型 | 整合细胞类型特异的调控数据 | Discussion：「the input for the zero-shot prediction in TransBind zeroshot does not implicitly contain cell type information」 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 消融实验提升幅度极小 | AUPR 仅从 0.3685 提升至 0.3710（+0.0025），AUROC 从 0.9493 至 0.9504（+0.0011），未报告统计显著性 | 若提升不显著，则「蛋白质信息增强」的核心 claim 被削弱 | 对 690 个组合进行配对检验（如 Wilcoxon signed-rank），报告效应量和置信区间 | Results 表 4 |
| 零样本测试仅 3 个 TF | HNF1A、ATF4、FOXA3 样本量过小，且均为常见 TF 家族 | 无法判断零样本能力是否可推广到结构新颖的 TF | 在更多 TF 家族（如锌指、螺旋-环-螺旋）上测试，并报告按家族分层的性能 | Results 表 3 |
| 未报告基线模型具体数值 | 表 2 仅给出 TransBind 的 AUROC/AUPR 和相对提升百分比，未列出 DeepSEA、DanQ、TBiNet 的绝对数值 | 读者无法独立验证提升幅度，也无法判断基线是否被公平训练 | 补充各基线模型的绝对 AUROC/AUPR 值及训练配置 | Results 表 2 |
| 基序恢复未与基线对比 | 仅报告 TransBind 恢复 160 个 JASPAR 基序，未报告 DNA-only 模型（如 TBiNet）的基序恢复率 | 无法判断基序学习能力是否真的来自蛋白质信息融合 | 对基线模型执行相同的 TOMTOM 分析并对比恢复率 | Results 图 5 |
| 未讨论嵌入冻结/微调 | 未明确 ESM-DBP 在训练中是否冻结 | 若冻结，TF 嵌入可能未针对结合预测任务优化；若微调，可能过拟合 | 报告 ESM-DBP 的训练策略及消融 | Methods 训练部分 |
| 未报告类别不平衡处理 | 数据仅 1.44% 正样本，未说明是否使用类别权重、Focal Loss 等 | 不平衡处理方式直接影响 AUPR 数值 | 报告损失函数是否加权及正负样本采样策略 | Materials and Methods 训练部分 |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **双侧信息融合范式**：TF–DNA 结合预测不应只从 DNA 侧建模。将蛋白质语言模型嵌入作为条件信号，通过交叉注意力引导 DNA 特征提取，是「蛋白质信息增强 DNA 结合预测」的可迁移框架。可推广至 TF–RNA 结合、DNA 修复蛋白–损伤位点识别等互作预测。

2. **交叉注意力 = 条件化特征提取**：让一个模态（TF 嵌入）作为 query 主动查询另一个模态（DNA 序列）的位置特征，注意力权重天然对应「结合位点」位置。这一设计既提升性能又提供可解释性（注意力热图 = 预测的结合区域）。

3. **任务重构实现零样本**：将「封闭集多标签分类」重构为「开放集 TF-DNA 对二分类」，是获得零样本泛化能力的关键。核心在于让模型学习「互作规则」而非「特定 TF 的模式」。这对任何「新实体预测」问题（新 TF、新药物、新突变）都有启发。

4. **预训练嵌入的领域适配**：ESM-DBP（在 DNA 结合蛋白上微调的 ESM-2）比通用 PLM 更适合 TF 嵌入生成。领域适配的预训练模型是迁移学习的关键环节。

5. **基序可解释性验证**：通过 TOMTOM 将卷积核与 JASPAR 数据库比对，是验证深度学习模型是否学到真实生物学基序的标准流程，可作为任何序列模型的解释性评估模板。

6. **类别不平衡下的评估**：在 1.44% 正样本的极端不平衡场景下，AUPR 比 AUROC 更能反映模型实际性能，应作为主要报告指标。

7. **消融实验的粒度**：本文消融仅对比「有/无蛋白质特征」，未来可细化为「随机蛋白质嵌入 vs. ESM-DBP 嵌入」「交叉注意力 vs. 简单拼接」等多层次消融，以更精确归因性能来源。

---

## 15 与已有知识连接

- **DeepSEA (Zhou & Troyanskaya, 2015)**：本文数据集的直接前身，首次用 CNN 从 DNA 序列预测染色质特征。TransBind 在相同数据划分和评估协议下对比，是直接的代际改进。
- **DanQ (Quang & Xie, 2016)**：CNN+BiLSTM 混合架构，TransBind 的 DNA 编码器继承此设计并叠加 Transformer。
- **TBiNet (2021)**：基于 Transformer 的 DNA-only 模型，是 TransBind 的最强基线。
- **ESM-2 (Lin et al., 2023)**：通用蛋白质语言模型，TransBind 的 TF 嵌入基础。
- **ESM-DBP (2024)**：在 DNA 结合蛋白上微调的 ESM 变体，是 TransBind 的核心创新组件。
- **AlphaFold 3 / RoseTTAFold All-Atom**：可预测 TF–DNA 复合物 3D 结构，与 TransBind 互补——结构预测提供原子级互作细节，TransBind 提供全基因组规模预测。未来可探索将结构信息注入 TransBind 嵌入。
- **JASPAR 数据库**：TF 结合基序参考库，本文用于模型可解释性验证。
- **ENCODE 项目**：ChIP-seq 数据来源，是 TF 结合位点预测的标准训练数据。
- **本课题方向连接**：本文是「TF–DNA 结合机制 × 深度学习」的 SOTA 工作，其「蛋白质嵌入 + 交叉注意力」框架可直接迁移至：
  - 变异效应预测（如 eQTL 中 TF 结合破坏的预测）
  - 细胞类型特异性结合预测（加入 ATAC-seq 等染色质特征）
  - 跨物种 TF 结合预测（利用蛋白质嵌入的保守性）

---

## 16 研究想法

> **Agent 生成的研究候选**

### 候选 1：结构感知的 TF–DNA 结合预测
- **名称**：Structure-Augmented TransBind (SAT-Bind)
- **来源局限/观察**：TransBind 的蛋白质嵌入仅含序列和间接结构信息，未直接利用 TF 3D 结构；作者在 Discussion 中承认此局限
- **核心假设**：将 AlphaFold 预测的 TF 结构（或实验结构）编码为结构嵌入，与序列嵌入融合，可提升结合预测精度，尤其对结构新颖的 TF
- **初步方法**：用 ESM-IF（结构条件蛋白质语言模型）或 GearNet 生成 TF 结构嵌入，与 ESM-DBP 序列嵌入拼接或门控融合后输入交叉注意力
- **验证方式**：在 EPBDXDNA 上对比 SAT-Bind vs. TransBind；在零样本设置下按 TF 结构家族分层报告性能
- **创新状态**：unverified

### 候选 2：细胞类型条件化的 TF–DNA 结合预测
- **名称**：Cell-Type-Conditioned TransBind (CT-TransBind)
- **来源局限/观察**：TransBind 仅用 TF + DNA 序列，未纳入细胞类型信息；作者承认零样本模型缺少细胞类型信息是局限
- **核心假设**：将细胞类型的染色质可及性（ATAC-seq）或组蛋白修饰（ChIP-seq of H3K27ac/H3K4me1）作为条件输入，可提升细胞类型特异性的结合预测
- **初步方法**：在交叉注意力后增加条件归一化层（FiLM），以细胞类型嵌入调制特征；或直接将 ATAC-seq 信号作为 DNA 编码器的辅助输入通道
- **验证方式**：在 ENCODE 多细胞类型数据上对比 CT-TransBind vs. TransBind；评估同 TF 不同细胞类型的预测差异
- **创新状态**：unverified

### 候选 3：结合强度回归与基序协同效应建模
- **名称**：TransBind-Affinity (TB-Affinity)
- **来源局限/观察**：TransBind 仅做二分类（结合/不结合），未预测结合强度；且未显式建模多个 TF 在邻近位点的协同/竞争
- **核心假设**：将二分类扩展为结合强度回归（如 ChIP-seq 峰强度或 HT-SELEX 亲和力），并引入多 TF 共定位特征，可更精细刻画 TF–DNA 互作
- **初步方法**：将输出层改为回归头，损失函数改为 MSE 或有序回归；在 DNA 编码器中加入邻近 TF 结合位点的嵌入作为上下文
- **验证方式**：在 HT-SELEX 体外亲和力数据上验证回归精度；在 ENCODE 共结合位点上验证协同效应建模
- **创新状态**：unverified

### 候选 4：跨物种 TF–DNA 结合预测的迁移学习
- **名称**：Cross-Species TransBind (CS-TransBind)
- **来源局限/观察**：TransBind 仅用人类数据训练，作者在 Discussion 中提出未来计划训练多物种数据
- **核心假设**：TF 蛋白质嵌入的保守性可支持跨物种迁移——在小鼠、斑马鱼等物种的 ChIP-seq 数据上微调，可提升低资源物种的结合预测
- **初步方法**：用人类数据预训练 TransBind，在目标物种少量 ChIP-seq 数据上微调；评估蛋白质嵌入相似度与迁移性能的关系
- **验证方式**：在 ENCODE 小鼠数据、modENCODE 果蝇数据上测试零样本和微调性能
- **创新状态**：unverified

### 候选 5：注意力可解释性作为基序发现工具
- **名称**：TransBind-Motif (TB-Motif)
- **来源局限/观察**：TransBind 已展示基序恢复能力（160 个 JASPAR 基序），但未系统利用注意力权重进行新基序发现
- **核心假设**：交叉注意力权重高的 DNA 区域即 TF 结合位点，可用于从 ChIP-seq 数据中从头发现未知 TF 基序
- **初步方法**：对注意力权重进行峰值检测，提取高权重区域序列，用 MEME/STREME 进行从头基序发现；与已知基序数据库比对验证
- **验证方式**：在留出 TF 上评估新基序发现率；与现有基序发现工具（HOMER）对比
- **创新状态**：unverified