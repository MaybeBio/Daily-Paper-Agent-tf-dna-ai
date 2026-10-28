## 01 基本信息

- **标题**：ChromaFold predicts the 3D contact map from single-cell chromatin accessibility
- **作者与单位**：Gao, Vianne R; Yang, Rui; Das, Arnav; Luo, Renhe; Luo, Hanzhi; McNally, Dylan R; Karagiannidis, Ioannis; Rivas, Martin A; Wang, Zhong-Min; Barisic, Darko; Karbalayghareh, Alireza; Wong, Wilfred; Zhan, Yingqian A; Chin, Christopher R; Noble, William S; Bilmes, Jeff A; Apostolou, Effie; Kharas, Michael G; Beguelin, Wendy; Viny, Aaron D; Huangfu, Danwei; Rudensky, Alexander Y; Melnick, Ari M; Leslie, Christina S（单位未在摘要中提供）
- **期刊/预印本平台**：Nature Communications
- **年份**：2024
- **论文类型**：研究论文（方法学）
- **领域**：计算基因组学 / 三维基因组 / 单细胞表观基因组学 / 深度学习
- **关键词**：3D contact map, scATAC-seq, deep learning, CTCF, chromatin interactions, Hi-C
- **DOI/arXiv 号**：10.1038/s41467-024-53628-0
- **代码**：未提供
- **数据**：未提供（提及使用九个人类和三只小鼠数据集，详见补充表1）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「蛋白质-DNA互作 × AI/深度学习」方向，聚焦于**不依赖实验3D基因组数据**，仅从单细胞染色质可及性（scATAC-seq）预测3D接触图谱。与TF–DNA结合机制的直接关联在于：CTCF（一种关键的结构性转录因子）的基序信息被作为核心输入特征，模型隐式学习了CTCF结合与染色质环化之间的映射关系。该工作为从可及性数据推断TF介导的染色质互作提供了可迁移的深度学习框架。

## 02 一句话总结

本文提出ChromaFold——一个轻量级卷积神经网络模型，以伪批量染色质可及性、跨元细胞共可及性和CTCF基序得分为输入，预测10 kb分辨率的3D接触图谱（Hi-C），在未见过的细胞类型和跨物种（人→小鼠）场景下达到与使用多种批量表观基因组输入的模型相当或更优的性能，并可通过微调实现复杂组织中细胞亚群的接触图谱反卷积。

## 03 研究问题

- **具体问题**：能否仅从单细胞ATAC-seq数据（而非实验3D基因组数据）准确预测细胞类型特异的3D染色质接触图谱，包括调控元件之间的互作？
- **为何重要**：Hi-C等3D基因组技术在稀有细胞群体中难以实施（需要大量细胞和深度测序），而scATAC-seq可轻松从少量细胞生成。若能仅从scATAC-seq预测3D接触，将极大扩展3D染色质结构研究的适用范围，并有助于解读非编码疾病变异。
- **现有方法不足**：(1) 无监督方法（如Cicero）精度有限；(2) 基于DNA序列的模型（DeepC、Akita、Orca）难以泛化到新细胞类型；(3) C.Origami和Epiphany需要多种批量表观基因组输入（如ATAC-seq、CTCF ChIP-seq），这些数据并非总是可得。
- **精确的"Can ... ?"问题**：Can a lightweight deep learning model trained on paired scATAC-seq and Hi-C data in human cell types accurately predict cell-type-specific 3D contact maps in unseen human and mouse cell types using only scATAC-seq and CTCF motif scores as inputs?

## 04 背景与发展脉络

*注：此脉络基于本文框架，未经外部系统核验。*

1. **实验3D基因组时代**：Hi-C、HiChIP、ChIA-PET等技术可绘制全基因组染色质互作图，但需要大量细胞和深度测序，难以用于稀有细胞群体。
2. **从1D表观基因组预测3D结构**：观察到染色质可及性与3D结构之间存在关联，催生了计算方法。
   - **Cicero**（2018）：首个利用scATAC-seq共可及性推断互作的无监督方法，但精度有限。
   - **DeepC / Akita / Orca**：基于DNA序列的深度神经网络，预测接触图谱，但泛化到新细胞类型能力差。
   - **C.Origami**：使用DNA序列+批量ATAC-seq+CTCF ChIP-seq，实现细胞类型特异预测，但需要多种输入模态，模型复杂易过拟合。
   - **Epiphany**：使用多种批量表观基因组轨道+bi-LSTM，实现新细胞类型泛化，但仍需多种输入。
3. **本文位置**：ChromaFold将输入需求降至**仅scATAC-seq**（+通用CTCF基序得分），通过轻量级架构和共可及性特征，在保持SOTA泛化能力的同时大幅降低输入要求，并新增了接触图谱反卷积功能。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 3D基因组实验在稀有细胞中不可行 | Hi-C等需要大量细胞和深度测序，稀有细胞群体难以获得高质量接触图谱 | 实验技术固有局限：需要足够输入材料生成高复杂度文库 | Introduction 第1段 |
| 现有预测模型输入要求高 | C.Origami和Epiphany需要多种批量表观基因组轨道（ATAC-seq、CTCF ChIP-seq等），并非所有细胞类型都有这些数据 | 模型设计依赖多种输入模态 | Introduction 第2段 |
| 序列模型泛化能力差 | DeepC、Akita、Orca倾向于在不同细胞类型中预测相似的接触图谱 | 序列特征本身不携带细胞类型特异信息 | Introduction 第2段 |
| 无监督方法精度不足 | Cicero精度有限，产生大量假阳性/假阴性 | 仅依赖共可及性相关性，缺乏监督信号 | Introduction 第2段；Results 图2c-d |
| 复杂组织中的细胞亚群分辨率缺失 | 批量Hi-C反映混合细胞信号，无法区分亚群特异的染色质互作 | 实验技术无法在组织水平解析亚群 | Results "ChromaFold can deconvolve..." 节 |

## 06 核心思想

**1) 表面方法**：
- 输入：伪批量染色质可及性（50 bp bin）、跨元细胞共可及性（500 bp bin）、CTCF基序得分
- 架构：双分支特征提取器（1D CNN处理可及性+CTCF；1D CNN处理共可及性）+ 线性预测器
- 输出：中心10 kb bin与周围2 Mb内所有bin的接触强度（Hi-C Z-score）
- 训练：在三个人类细胞类型上训练，15条染色体训练、2条验证、4条测试

**2) 核心洞察**：
- **单细胞共可及性编码3D互作信息**：由于染色质环化在单细胞中是异步事件，跨细胞的共可及性相关性可反映空间邻近性——这是Cicero的直觉，但ChromaFold将其作为监督学习中的**输入特征**而非直接输出，从而通过训练数据中的Hi-C标签学习更精确的映射。
- **CTCF基序作为通用先验**：CTCF是3D基因组结构的关键组织者，其基序得分（而非实验ChIP-seq）作为输入，既提供了结构生物学先验，又避免了额外实验数据需求。
- **轻量级架构+数据增强**：随机子采样单细胞和元细胞作为训练时数据增强，使模型对输入数据质量和规模具有鲁棒性，这是泛化到新细胞类型的关键。

**3) 可能的普适教训 [Analysis]**：
- 将**无监督启发式特征**（如共可及性）转化为**监督学习输入**，可以显著提升其预测能力——这是"特征工程+深度学习"的经典范式。
- 在生物序列建模中，**基序/模体得分**可以作为实验数据的廉价替代品，在保持性能的同时大幅降低数据需求。
- **训练时数据增强**（子采样）可以模拟不同规模/质量的数据集，提升模型在真实应用中的鲁棒性。

## 07 方法总览

- **输入**：
  1. 伪批量染色质可及性（50 bp bin，log变换+库大小归一化）
  2. 跨元细胞共可及性（500 bp bin，Jaccard相似度）
  3. CTCF基序得分（50 bp bin，FIMO扫描JASPAR PWM）
  - 所有输入覆盖4.01 Mb基因组窗口
- **输出**：中心bin与2 Mb范围内所有bin的接触强度（HiC-DC+ Z-score归一化）
- **模型架构**：
  - 特征提取器1：15层1D CNN，处理可及性+CTCF基序（2通道）
  - 特征提取器2：3层1D CNN + 2个残差块 + 3层1D CNN，处理共可及性
  - 外连接（outer-concatenation）将1D特征转换为2D特征对
  - 3层2D CNN + 线性层 → 预测V-stripe
- **训练**：
  - 数据：三个人类细胞类型（IMR-90, GM12878, HUVEC）
  - 染色体划分：15条训练、2条验证（3, 15）、4条测试（5, 18, 20, 21）
  - 损失：MSE
  - 优化器：SGD，学习率1e-6，权重衰减1e-3
  - 30 epochs，早停patience=10
  - 数据增强：每迭代随机子采样500-5000个单细胞和400-1000个元细胞
- **推理**：直接应用于新细胞类型/物种，无需重训练；反卷积场景需在目标组织上微调1 epoch
- **评估指标**：距离分层Pearson相关、AUROC、AUPRC（bin-level和peak-level）

**文字流程**：
1. 从scATAC-seq数据计算伪批量可及性和元细胞共可及性
2. 从基因组序列扫描CTCF基序得分
3. 三个输入轨道经预处理后输入双分支网络
4. 特征提取器1处理可及性+CTCF，特征提取器2处理共可及性
5. 外连接合并特征，2D CNN进一步处理
6. 线性层输出中心bin的V-stripe预测
7. 沿染色体滑动中心bin，拼接所有V-stripe得到完整接触图谱

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 特征提取器1（1D CNN，15层） | 从可及性和CTCF基序提取局部染色质状态特征 | 可及性反映调控元件活性，CTCF基序提供结构蛋白结合先验 | 输入：2通道×4.01 Mb（50 bp bin）；输出：L×C特征矩阵 | Results 图2b：完整模型在训练和测试细胞类型上均达到最高相关 | [预期] 移除后模型失去局部染色质状态信息，预测精度显著下降 |
| 特征提取器2（1D CNN+残差块） | 从共可及性提取长程互作特征 | 共可及性编码跨细胞异步环化信号，是scATAC-seq独有信息 | 输入：1通道×4.01 Mb（500 bp bin）；输出：L×C特征矩阵 | Results 图2b：无共可及性模型在所有细胞类型上性能显著下降（p<1e-16） | [实测] 移除共可及性输入导致性能显著下降（图2b），证明该模块是关键贡献 |
| 外连接（outer-concatenation） | 将1D特征转换为2D特征对 | 使模型能同时考虑中心bin与所有其他bin的特征组合 | 输入：两个L×C特征矩阵；输出：L×L×2C张量 | Methods "ChromaFold model architecture" | [预期] 移除后模型无法建模特征间的非线性交互 |
| 2D CNN+线性预测器 | 从特征对预测接触强度 | 2D卷积可捕捉特征对之间的空间模式 | 输入：L×L×2C张量；输出：V-stripe预测（L×1） | Results 图1b架构示意 | [预期] 移除后模型退化为线性模型，无法捕捉复杂非线性映射 |
| 数据增强（随机子采样） | 每迭代随机子采样单细胞和元细胞 | 提升模型对数据规模/质量的鲁棒性 | 输入：完整细胞集；输出：随机子集 | Methods "ChromaFold model training"；Results 图2c：在~1500细胞的小数据集上仍表现良好 | [预期] 移除后模型可能过拟合训练数据规模，泛化能力下降 |
| 微调（反卷积场景） | 在目标组织上微调1 epoch | 适应组织特异的可及性-互作关系 | 输入：预训练模型+目标组织scATAC-seq+批量Hi-C；输出：微调后模型 | Results 图5：成功反卷积α/β细胞互作 | [预期] 不微调则无法适应组织特异特征 |

## 09 关键公式符号

**1) HiC-DC+ Z-score归一化**（目标值）：
- 对每个距离d的接触计数，用负二项回归建模期望值：
  - E[count] = NB(μ, θ)，其中log(μ) = β₀ + β₁·log(d) + β₂·GC + β₃·mappability + β₄·effective_size
  - Z = (count - μ) / sqrt(μ + μ²/θ)
- 用途：消除距离、GC含量、可作图性等协变量对接触计数的影响，使不同距离的接触可比
- 来源：Methods "Preprocessing of Hi-C and Micro-C data"

**2) Jaccard相似度**（共可及性计算）：
- J(A,B) = |A ∩ B| / |A ∪ B|
- 用途：衡量两个500 bp bin在元细胞中的共可及性
- 来源：Methods "Preprocessing of scATAC-seq data"

**3) 损失函数**：
- L = MSE(y_pred, y_true) = (1/N) Σ(y_pred - y_true)²
- 用途：训练ChromaFold预测Z-score
- 来源：Methods "ChromaFold model training"

**4) 距离分层Pearson相关**：
- 对每个距离d，计算corr(y_pred(d), y_true(d))
- 用途：评估接触图谱预测质量，避免距离效应主导相关性
- 来源：Methods "Distance-stratified correlation"

## 10 实验设计与证据链

**数据集与资源**：
- 训练：3个人类细胞类型（IMR-90, GM12878, HUVEC），15条染色体训练，2条验证（chr3, chr15），4条测试（chr5, chr18, chr20, chr21）
- 测试（人类）：K562, hESC, 活化CD4+ T细胞
- 测试（小鼠）：生发中心B细胞（GCB）、造血干细胞（HSC）、调节性T细胞（Treg）
- 反卷积：人类胰腺胰岛（α细胞、β细胞）
- 共9个人类+3个小鼠数据集（补充表1）
- Hi-C目标：HiC-DC+ Z-score归一化
- 对比模型：Cicero、C.Origami、Epiphany

**指标**：距离分层Pearson相关（接触图谱）、AUROC/AUPRC（bin-level和peak-level互作预测）

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|-------------|-------------------|------|
| 接触图谱预测（训练细胞类型） | ChromaFold能准确预测训练细胞类型的接触图谱 | 在IMR-90, GM12878, HUVEC上评估，4条测试染色体 | 平均距离分层Pearson相关0.55-0.60 | ChromaFold在训练细胞类型上表现良好 | 未与C.Origami在相同条件下直接对比 | Results 图2b |
| 接触图谱预测（新人类细胞类型） | ChromaFold能泛化到未见过的细胞类型 | 在K562, hESC, 活化CD4+ T细胞上评估 | 平均Pearson相关0.45-0.55；AUROC 0.77-0.79 | ChromaFold能泛化到新细胞类型 | 泛化性能低于训练细胞类型 | Results 图2b |
| 共可及性消融 | 共可及性输入对性能有贡献 | 完整模型 vs. 无共可及性模型 | 无共可及性模型在所有细胞类型上显著下降（p<1e-16） | 共可及性是关键输入特征 | 未测试其他消融组合 | Results 图2b |
| 与Cicero对比（peak-level） | ChromaFold优于无监督方法Cicero | 在K562上对比peak-level互作预测 | ChromaFold AUPRC 0.65-0.7 vs. Cicero显著更低（p<1e-16） | ChromaFold显著优于Cicero | 仅在一个细胞类型上对比 | Results 图2c-d |
| 与C.Origami对比（同训练条件） | ChromaFold在相同输入条件下优于C.Origami | 两者均在IMR-90上训练，测试GM12878, K562, hESC | ChromaFold（CTCF ChIP版）在所有指标上优于C.Origami；ChromaFold（CTCF motif版）与C.Origami相当 | ChromaFold在更少输入下达到SOTA | 对比仅在3个细胞类型上进行 | Results 图3 |
| 跨物种泛化（人类→小鼠） | ChromaFold能跨物种预测 | 人类训练的模型直接应用于小鼠GCB, HSC, Treg | 性能与人类测试细胞类型相当 | 可及性-3D互作映射在哺乳动物中保守 | 仅测试3个小鼠细胞类型 | Results 图4 |
| 反卷积（胰腺胰岛） | 微调后能反卷积复杂组织中的亚群互作 | 在胰岛scATAC-seq+bulk Hi-C上微调1 epoch，预测α/β细胞 | 成功预测α/β细胞特异的互作，与实验数据一致 | ChromaFold能反卷积组织亚群互作 | 仅在一个组织类型上验证 | Results 图5 |
| 细胞数鲁棒性 | 在小细胞数下仍表现良好 | 下采样至~3000细胞 | 性能仅轻微下降 | 模型对细胞数鲁棒 | 未测试<1000细胞 | Results 图2c |

## 11 结论正确解读

- **任务范围**：ChromaFold预测的是**10 kb分辨率**的接触图谱（可扩展至5 kb），覆盖2 Mb范围内的互作。它预测的是**染色质接触强度**（HiC-DC+ Z-score），而非直接的TF结合位点或增强子-启动子调控功能。
- **输入范围**：仅需scATAC-seq数据（实验）和CTCF基序得分（计算预测），**不需要**CTCF ChIP-seq、H3K27ac等额外表观基因组数据。
- **端到端状态**：模型是端到端训练的（输入→接触图谱），但**不是**从原始测序数据端到端——需要先经过scATAC-seq标准处理流程（比对、峰值 calling、元细胞生成）。
- **泛化边界**：在9个人类+3个小鼠细胞类型上验证，跨物种泛化成功。但**未测试**非哺乳动物物种，也未测试疾病状态或极端染色质重塑场景。
- **功能vs.结构**：ChromaFold预测**结构接触**，不等于**功能互作**。作者明确警告：接触图谱本身不足以推断增强子-启动子功能，需要H3K27ac等活性标记（Discussion）。
- **反卷积的适用条件**：反卷积需要目标组织的bulk Hi-C用于微调，并非完全无监督。
- **性能对比的边界**：与C.Origami的对比是在相同训练条件下（IMR-90训练）进行的，C.Origami原始论文可能使用不同训练设置。
- **不确定性**：预测的接触图谱是确定性输出，未提供置信区间或不确定性估计。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 接触≠功能 | 预测的3D互作（包括增强子-启动子接触）不保证调控功能；3D接触强度不能区分功能性vs非功能性增强子-启动子互作 | 需结合H3K27ac等活性标记（如activity-by-contact模型、ENCODE-E2G）来预测功能互作 | Discussion 第2段；Results 图S3 |
| 分辨率限制 | 标准模型为10 kb分辨率，5 kb分辨率需要高质量训练数据 | 在更高分辨率数据上训练 | Results "ChromaFold predicts..." 节；图S2 |
| 细胞数要求 | 测试显示~3000细胞时性能仅轻微下降，但未测试极低细胞数 | 未明确提及 | Results 图S2c |
| 物种泛化范围 | 仅验证了人类→小鼠的跨物种泛化 | 未明确提及 | Results 图4 |
| 反卷积依赖微调 | 反卷积需要目标组织的bulk Hi-C用于微调 | 未明确提及 | Results "ChromaFold can deconvolve..." 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 训练数据仅3个人类细胞类型 | 模型可能过拟合这3个细胞类型的特定染色质特征，泛化到更广泛细胞类型的能力未充分验证 | 训练数据多样性直接影响模型适用性 | 在更多样化的细胞类型面板上训练和测试 | Methods "ChromaFold model training" |
| 与C.Origami的对比条件可能不完全公平 | C.Origami原始论文可能使用不同训练/测试划分、不同归一化方法或不同超参数 | 对比公平性影响"达到SOTA"结论的可信度 | 使用C.Origami原始训练设置进行对比实验 | Results 图3 |
| 共可及性计算依赖元细胞质量 | Jaccard相似度对元细胞生成参数敏感，不同聚类/元细胞算法可能影响结果 | 输入特征稳定性影响模型可重复性 | 测试不同元细胞生成参数下的性能变化 | Methods "Preprocessing of scATAC-seq data" |
| 未报告不确定性估计 | 模型输出确定性接触图谱，无法区分高置信度和低置信度预测 | 在生物学应用中，不确定性信息对实验验证优先级很重要 | 添加MC-dropout或集成方法估计预测不确定性 | 全文未提及 |
| 反卷积验证仅限胰腺胰岛 | 仅在一个复杂组织上验证反卷积能力，其他组织（如脑、肿瘤微环境）的适用性未知 | 反卷积是重要应用场景，需更广泛验证 | 在多种复杂组织上测试反卷积性能 | Results 图5 |
| 未与单细胞Hi-C直接对比 | 模型预测的是"伪批量"接触图谱，未与真实单细胞Hi-C数据对比 | 单细胞Hi-C虽稀疏但提供真实单细胞互作信息 | 在匹配的scATAC-seq+单细胞Hi-C数据上对比 | 全文未提及 |
| CTCF基序得分可能遗漏非CTCF介导的互作 | 模型依赖CTCF基序作为关键输入，可能对CTCF独立的互作（如涉及其他结构蛋白）预测不佳 | 染色质互作的机制多样性 | 测试不含CTCF基序的互作区域的预测精度 | Results 图S4 |

## 14 学到什么

*标题：Agent 提炼的知识候选*

1. **共可及性作为监督学习特征**：将无监督方法（Cicero）的核心直觉——跨细胞共可及性反映空间邻近性——转化为深度学习输入特征，通过Hi-C标签监督学习更精确的映射。**可迁移到TF–DNA互作**：TF共结合模式（跨细胞的共可及性）可能编码TF协同结合信息，可作为预测TF–TF互作或TF介导环化的输入特征。

2. **基序得分作为实验数据的廉价替代**：用CTCF基序得分（计算预测）替代CTCF ChIP-seq（实验数据），在保持性能的同时大幅降低数据需求。**可迁移到TF–DNA互作**：对于缺乏ChIP-seq的TF，可用基序扫描得分作为输入特征，预测该TF参与的染色质互作。

3. **轻量级架构+数据增强实现鲁棒泛化**：通过随机子采样模拟不同数据规模/质量，使模型对输入数据变化鲁棒。**可迁移到TF–DNA互作**：在训练TF结合预测模型时，可通过子采样模拟不同测序深度/细胞数的场景，提升模型在实际应用中的稳定性。

4. **微调实现反卷积**：在复杂组织上微调预训练模型，利用scATAC-seq的细胞亚群信息反卷积bulk Hi-C。**可迁移到TF–DNA互作**：类似策略可用于从混合组织的表观数据中推断细胞类型特异的TF结合模式。

5. **距离分层评估**：使用距离分层Pearson相关和AUROC/AUPRC评估，避免距离效应主导性能指标。**可迁移到TF–DNA互作**：在评估TF结合位点预测时，应考虑基因组距离/序列上下文的分层评估，避免简单相关性误导。

6. **接触≠功能的明确边界**：作者明确区分结构接触与功能互作，避免过度解读。**可迁移到TF–DNA互作**：预测的TF结合/互作需要功能验证（如报告基因、CRISPR扰动），不能仅凭预测置信度断言调控功能。

## 15 与已有知识连接

1. **Cicero (Pliner et al., 2018, Molecular Cell)**：首次提出scATAC-seq共可及性推断互作。ChromaFold将其核心思想（共可及性→互作）从无监督转为监督学习，并显著提升精度。**连接点**：共可及性作为互作信号的生物学基础。

2. **C.Origami (Fudenberg et al., 2023, Nature Genetics)**：使用DNA序列+ATAC-seq+CTCF ChIP-seq预测细胞类型特异接触图谱。ChromaFold在相同对比条件下超越C.Origami，且输入需求更少。**连接点**：细胞类型特异3D基因组预测的方法学对比。

3. **Epiphany (Rui Yang et al., 2023)**：使用多种批量表观基因组轨道+bi-LSTM预测接触图谱。ChromaFold用更少输入达到可比性能。**连接点**：表观基因组特征到3D结构的映射。

4. **DeepC / Akita (Fudenberg et al., 2020)**：基于DNA序列的接触图谱预测。ChromaFold与这类序列模型的区别在于使用实验表观数据（scATAC-seq）而非纯序列，因此能捕捉细胞类型特异信息。**连接点**：序列vs.表观特征对3D结构预测的贡献。

5. **CTCF基序与染色质环化 (Rao et al., 2014, Cell)**：CTCF是3D基因组结构的核心组织者。ChromaFold利用这一生物学先验，将CTCF基序得分作为输入。**连接点**：TF（CTCF）结合与染色质结构的因果关系。

6. **Activity-by-contact模型 (Fulco et al., 2019, Nature Genetics)**：结合可及性、H3K27ac和3D接触预测增强子-启动子功能。ChromaFold的peak-level互作预测可作为该模型的输入。**连接点**：3D接触→功能调控的桥梁。

7. **单细胞多组学（scATAC+scRNA）**：ChromaFold的反卷积能力可与单细胞多组学数据整合，推断细胞类型特异的调控程序。**连接点**：单细胞分辨率下的基因调控推断。

## 16 研究想法

*标题：Agent 生成的研究候选*

**候选1：TF–DNA结合基序作为通用先验的泛化**
- **名称**：TF-motif-augmented contact prediction
- **来源局限/观察**：ChromaFold仅使用CTCF基序，但其他结构相关TF（如 cohesin 亚基、YY1、SPI1）也可能参与环化
- **核心假设**：将多种TF基序得分作为输入特征，可提升接触图谱预测精度，尤其在CTCF缺失区域
- **增量**：扩展ChromaFold输入通道，从单一CTCF到多TF基序集合
- **初步方法**：在ChromaFold架构基础上，将CTCF基序通道替换为多TF基序通道（如CTCF+YY1+SPI1+...），在相同训练/测试条件下对比
- **验证方式**：在ChromaFold的测试细胞类型上对比多TF vs. 单CTCF的Pearson相关和AUROC/AUPRC
- **创新状态**：unverified

**候选2：从接触图谱反推TF–DNA结合位点**
- **名称**：Contact-to-binding inverse prediction
- **来源局限/观察**：ChromaFold预测接触图谱，但未利用接触图谱反推TF结合状态
- **核心假设**：3D接触模式编码TF结合信息，可从接触图谱反推TF结合位点
- **增量**：将ChromaFold的输出（接触图谱）作为输入，预测TF ChIP-seq峰/基序占用
- **初步方法**：构建逆模型，输入为ChromaFold预测的接触图谱，输出为TF结合概率；在ENCODE TF ChIP-seq数据上训练
- **验证方式**：在未见过的细胞类型上评估TF结合预测的AUROC
- **创新状态**：unverified

**候选3：TF–DNA结合动力学与接触图谱的物理模拟整合**
- **名称**：Physics-informed contact prediction with TF binding dynamics
- **来源局限/观察**：ChromaFold是纯数据驱动模型，未利用3D基因组物理约束（如聚合物模型）
- **核心假设**：将TF结合位点作为锚点，结合聚合物物理模型（如Strings & Binders Switch模型），可提升接触图谱预测的物理合理性
- **增量**：在ChromaFold预测基础上，用物理模拟（如聚合物模拟）对预测结果进行约束或后处理
- **初步方法**：先用ChromaFold预测接触图谱，再用基于TF结合位点的聚合物模拟生成物理可行的接触矩阵，与ChromaFold预测融合
- **验证方式**：在Hi-C数据上对比融合模型 vs. 纯ChromaFold的接触图谱质量
- **创新状态**：unverified

**候选4：TF–DNA互作的细胞类型特异3D图谱反卷积**
- **名称**：Cell-type-resolved TF interaction atlas
- **来源局限/观察**：ChromaFold反卷积仅验证了α/β细胞，未扩展到TF结合层面
- **核心假设**：反卷积的接触图谱可用于推断细胞类型特异的TF–TF协同结合模式
- **增量**：将ChromaFold反卷积与TF基序/ChIP-seq整合，构建细胞类型特异的TF互作图谱
- **初步方法**：在胰腺胰岛反卷积结果上，分析α/β细胞特异的接触区域中TF基序富集模式
- **验证方式**：与已知α/β细胞特异TF（如ARX、PDX1）的功能验证数据对比
- **创新状态**：unverified

**候选5：低细胞数下的接触图谱预测**
- **名称**：Low-input contact prediction via transfer learning
- **来源局限/观察**：ChromaFold在~3000细胞时性能仅轻微下降，但未测试极低细胞数
- **核心假设**：通过迁移学习，可将高细胞数训练的模型适应到极低细胞数（<500）的scATAC-seq数据
- **增量**：开发域适应策略，使ChromaFold在极低细胞数下仍能预测接触图谱
- **初步方法**：在ChromaFold预训练模型基础上，用低细胞数数据的伪批量特征进行微调，评估性能-细胞数曲线
- **验证方式**：在稀有细胞群体（如循环肿瘤细胞、早期胚胎细胞）的scATAC-seq数据上验证
- **创新状态**：unverified