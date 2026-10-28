## 01 基本信息

- **标题**: A scalable computational framework for predicting gene expression from candidate cis-regulatory elements
- **作者**: Zhang, Qinhu; Wang, Siguo; Li, Zhipeng; Bao, Wenzheng; Liu, Wenjian; Huang, De-Shuang
- **单位**: 未提供（根据基金信息推测为中国高校/研究所，具体单位未在摘要中列出）
- **期刊/平台**: Genome Research
- **年份**: 2026
- **论文类型**: 研究论文（方法学）
- **领域**: 计算基因组学 / 基因表达调控 / 深度学习
- **关键词**: cis-regulatory elements (CREs), gene expression prediction, convolutional neural networks, transformers, chromatin loops, TF motifs
- **DOI/arXiv**: 10.1101/gr.281219.125
- **代码**: https://github.com/turningpoint1988/ScPGE
- **数据**: ENCODE (RNA-seq, DNase-seq, ChIP-seq, CAGE-seq), SCREEN Registry V3 (cCREs), HOCOMOCO V11 (TF motifs), Loop Catalog (chromatin loops)
- **阅读日期**: 2026-01-17
- **在课题方向中的位置**: 本文属于「蛋白质-DNA互作 × 深度学习」方向，聚焦于TF–DNA结合与基因表达调控的建模。其核心贡献在于：(1) 将离散cCREs的DNA序列、TF结合分数和表观遗传信号整合为三维张量，用CNN+Transformer建模cCRE–基因关系；(2) 通过注意力机制识别增强子-基因互作；(3) 发现调控效应随距离衰减的规律并据此引入染色质环。对TF–DNA结合机制研究提供了从序列+表观+3D结构多模态预测基因表达的框架。

---

## 02 一句话总结

本文提出ScPGE框架，将候选顺式调控元件(cCREs)的DNA序列、TF结合分数和表观遗传信号组装为三维张量，用CNN+Transformer建模cCRE–基因关系以预测细胞类型特异的基因表达，并通过注意力机制识别增强子-基因互作、发现调控效应随距离衰减的规律，进而引入染色质环提升远端互作识别能力。

---

## 03 研究问题

- **具体问题**: 如何从离散的候选顺式调控元件(cCREs)出发，准确预测细胞类型特异的基因表达水平，并识别哪些cCRE与目标基因存在功能性互作？
- **为什么重要**: 顺式调控元件与靶基因的对应关系是基因表达调控的核心问题。实验方法（如CRISPR筛选、HiChIP）成本高、通量低，计算预测方法可以在全基因组范围内优先候选互作，指导实验验证。同时，不同细胞类型中cCRE的动态变化使得这一问题更具挑战性。
- **现有方法不足**:
  - Enformer等模型需要长距离连续DNA序列（196kb），计算资源消耗大，难以在资源受限条件下部署。
  - 现有模型大多未充分利用cCRE的离散分布特性，也未显式建模cCRE之间的互作关系。
  - 对远端增强子-基因互作的识别精度有限，尤其是>100kb的互作。
- **精确的"Can..."问题**: Can a lightweight CNN+Transformer framework that integrates DNA sequences, TF binding scores, and epigenomic signals from discrete cCREs accurately predict cell type–specific gene expression and identify active enhancer–gene interactions?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注为「仅本文框架」，未经外部系统核验。

| 阶段 | 代表方法 | 优点 | 局限 | 本文位置 |
|------|----------|------|------|----------|
| 早期：基于距离/共定位 | 最近基因法、Hi-C互作法 | 简单、可解释 | 忽略序列和表观信息，精度低 | — |
| 中期：序列特征+机器学习 | gkm-SVM、Basenji | 利用序列motif信息 | 缺乏多模态整合，无法建模长程互作 | — |
| 近期：深度学习端到端 | Enformer (2021) | 长序列建模，多任务预测 | 计算资源需求大，输入为连续序列而非离散cCRE | 对比基线 |
| 近期：cCRE+注意力 | CREaTor (2023) | 利用cCRE离散性，层次注意力 | 未充分利用TF结合分数和染色质环 | 对比基线 |
| 近期：增强子-启动子+Transformer | EPInformer (2024) | 整合增强子-启动子互作 | 依赖染色质接触数据，部分细胞类型不可用 | 对比基线 |
| **本文** | **ScPGE** | **轻量级、多模态三维张量、CNN+Transformer、可扩展、引入染色质环** | 远端互作精度仍有提升空间 | **本文位置** |

**本文主张的位置**: ScPGE在保持轻量级计算开销的同时，通过离散cCRE的三维张量表示和CNN+Transformer架构，在基因表达预测和增强子-基因互作识别上达到或超过现有SOTA，并首次系统揭示预测结果中"调控效应随距离衰减"的规律。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 计算资源需求高 | Enformer等模型需要长序列输入，训练/推理开销大 | 长距离连续序列(196kb)作为输入，模型参数量大 | Results "Overview of ScPGE" 节；Supplemental Table S1 |
| 远端cCRE-基因互作识别精度低 | 所有方法在>100kb距离上性能下降 | 训练数据中远端互作样本少，模型难以学习长程依赖 | Results 图3B "performance of all methods decreases with increasing distance" |
| cCRE数量增加引入噪声 | 使用更多cCRE时性能下降 | 无关cCRE的序列/表观信息干扰模型 | Results 图2D "decrease in ScPGE's performance as the number of cCREs increases" |
| 跨物种预测绝对水平偏差 | 跨物种MAE显著高于同物种 | 不同物种间表观遗传景观和调控逻辑存在差异 | Results 图4C "MAE of the interspecies prediction is significantly higher" |
| 染色质环数据稀疏 | 多数细胞类型缺乏HiChIP数据 | 实验成本高，难以覆盖所有细胞类型 | Methods "Incorporation of chromatin loops" 节 |
| 注意力机制与物理互作的对齐不完美 | 注意力分数高的cCRE不总是实验验证的增强子 | 注意力反映的是模型学到的统计关联，不等同于物理结合 | Results 图3C "comparable to EPInformer" |

---

## 06 核心思想

### 1) 表面方法

ScPGE是一个三模块深度学习框架：
- **特征学习模块**：将每个基因及其周围cCRE的DNA序列（one-hot编码）、TF结合分数（基于HOCOMOCO motif扫描）和表观遗传信号（DNase, H3K27ac, H3K4me3, CTCF）分别组装为三维张量，通过多个2D卷积块并行学习多模态特征。
- **交互学习模块**：4层Transformer块（多头自注意力+前馈网络），建模cCRE与基因之间、cCRE与cCRE之间的关系。使用T5式相对位置编码。
- **预测模块**：提取Transformer输出中基因对应行的向量，通过全连接层+Softplus激活预测基因表达值。

### 2) 核心洞察

- **离散cCRE的三维张量表示**：不同于Enformer将长连续序列作为输入，ScPGE将离散cCREs的多种模态信息（序列、TF结合、表观）组织为三维张量，使CNN可以并行处理所有cCRE，大幅降低计算复杂度。
- **调控效应随距离衰减的规律**：通过分析TP（真阳性）预测，发现cCRE对基因的调控效应随距离增加呈指数衰减（exp−|x|/2），这一规律被用于设计染色质环整合方法。
- **注意力机制作为互作推断工具**：自注意力权重可以直接解释为cCRE-基因互作的强度，无需额外训练分类器。
- **染色质环的两种整合方式**：直接法（将环信息乘入注意力权重）和间接法（KL散度损失对齐注意力分布与环分布），两者互补，分别擅长远端和近端互作。

### 3) 可能的普适教训 [Analysis]

- **多模态三维张量组织**：将离散的基因组元件（而非连续序列）作为基本单元，可以显著降低计算复杂度，同时保留空间关系。这一思路可迁移到其他基因组元件互作建模任务。
- **从预测结果中挖掘生物学规律**：本文从TP/FP分类中发现了距离衰减规律，反过来指导模型设计——这种"预测→分析→反馈优化"的闭环思路值得借鉴。
- **直接+间接的领域知识注入**：将先验知识（染色质环）同时通过架构修改（直接法）和损失函数（间接法）注入模型，两种方式效果互补，说明知识注入的"双通道"策略可能优于单一方式。

---

## 07 方法总览

- **输入**：
  - 目标基因及其周围最多m个cCRE（默认m=20）
  - 每个cCRE的三种模态特征：
    - DNA序列（600bp，one-hot编码，4×600）
    - TF结合分数（600个active TF motifs的扫描分数，1×600）
    - 表观遗传信号（DNase, H3K4me3, H3K27ac, CTCF，4×600）
  - 可选：染色质环矩阵（m+1）×（m+1）
- **输出**：目标基因的表达水平（连续值，回归任务）
- **模块**：
  1. 特征学习模块：3个stem blocks（分别处理序列、TF分数、表观信号）+ 4个残差卷积块（2D Conv + MaxPool，kernel size沿cCRE轴为1）
  2. 交互学习模块：4层Transformer块（多头自注意力 + 前馈网络 + 相对位置编码）
  3. 预测模块：全连接层 + Softplus激活
- **训练**：
  - 损失函数：MSE + L2正则化（Eq. 2）
  - 优化器：AdamW，warm-up策略（先随机初始化多个模型选最优，再正式训练）
  - 学习率：第一阶段从1×10⁻⁶升至1×10⁻³（5000步），第二阶段降至1×10⁻⁶（3000步）
  - 硬件：单张A100 GPU
- **反馈回路**：训练完成后，通过注意力权重和in silico perturbation识别重要cCRE → 分析TP/FP模式 → 发现距离衰减规律 → 设计染色质环整合方法（ScPGE-LP, ScPGE-KL, ScPGE-Loop）
- **假设**：
  - cCRE对基因的调控效应随距离衰减（由TP分析发现，用于KL方法设计）
  - 自注意力权重可以反映cCRE-基因的功能互作强度
  - 染色质环信息可以引导模型关注物理互作的cCRE对

**文字流程**：
1. 从SCREEN Registry获取基因周围cCREs，提取序列、TF结合分数、表观信号
2. 将三种模态分别组装为三维张量
3. 特征学习模块并行提取各cCRE的多模态特征
4. 交互学习模块通过自注意力建模cCRE-基因、cCRE-cCRE关系
5. 预测模块输出基因表达值
6. （可选）将染色质环通过直接法（注意力加权）或间接法（KL损失）注入模型
7. 训练完成后，提取注意力权重进行增强子-基因互作推断

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 特征学习模块（3个stem blocks + 4个残差卷积块） | 从序列、TF结合分数、表观信号中提取cCRE的局部特征 | 三种模态信息互补，需要分别提取后融合 | 输入：4×(m+1)×600（序列）、1×(m+1)×600（TF分数）、4×(m+1)×600（表观）；输出：(m+1)×256特征嵌入 | Results 图2A-B：ScPGE优于基线；Supplemental Fig. S5：表观信号是最重要特征 | 预期影响：移除任一模态会显著降低性能（尤其表观信号）；[Analysis] 未提供逐模态消融的定量数据 |
| 交互学习模块（4层Transformer） | 建模cCRE-基因、cCRE-cCRE的全局关系 | cCRE对基因的调控依赖其与其他cCRE的协同/竞争 | 输入：(m+1)×256；输出：(m+1)×256 | Results 图2E-F：Transformer层数影响性能，Tran-0显著下降 | 实测消融：Tran-0（无Transformer）显著降低预测性能，证明交互建模的必要性 |
| 预测模块（FC + Softplus） | 从基因对应嵌入预测表达值 | 回归任务需要非线性映射 | 输入：256维向量；输出：标量表达值 | Results 图2A-B：整体性能 | 预期影响：移除Softplus可能使预测出现负值，影响MSE计算 |
| 注意力权重提取 | 推断cCRE-基因互作强度 | 无需额外训练即可获得可解释的互作推断 | 输入：Transformer注意力矩阵；输出：归一化互作分数 | Results 图3A-C：注意力分数用于增强子-基因互作优先级排序 | 预期影响：无法直接评估，因为这是推断工具而非预测模块 |
| 染色质环直接注入（ScPGE-LP） | 将HiChIP环信息乘入注意力权重 | 物理互作应增强注意力 | 输入：注意力权重+环矩阵；输出：加权注意力 | Results 图5A-B：ScPGE-LP在远端互作上优于ScPGE | 实测消融：ScPGE-LP在cCRE-200时优于ScPGE-KL，说明直接法擅长远端 |
| 染色质环间接注入（ScPGE-KL） | 通过KL散度损失对齐注意力与环分布 | 软约束避免硬编码错误 | 输入：注意力分布+环分布；输出：KL损失项 | Results 图5A-B：ScPGE-KL在近端互作上优于ScPGE-LP | 实测消融：ScPGE-KL在cCRE-20时优于ScPGE-LP，说明间接法擅长近端 |
| 组合方法（ScPGE-Loop） | 近端用KL、远端用LP | 两种方法互补 | 输入：两种方法的输出；输出：组合预测 | Results 图5D：ScPGE-Loop在42个基因中30个优于ScPGE | 实测消融：组合方法整体最优，但未提供与单独方法的统计显著性检验 |

---

## 09 关键公式符号

**公式1：多头自注意力（Transformer核心）**

$$Q_i = XW_i^Q, \quad K_i = XW_i^K, \quad V_i = XW_i^V$$

$$A_i = \text{softmax}\left(\frac{Q_i K_i^T}{\sqrt{d_k}} + \Phi(\bar{P})\right)$$

$$H_i = \text{Attention}(Q_i, K_i, V_i) = A_i V_i$$

$$H = \text{MultiHead}(Q, K, V) = \text{Concat}(H_1, H_2, \ldots, H_n)$$

$$Z = \text{FFN}(H) = HW^F$$

- $X$：输入特征嵌入（(m+1)×256）
- $W_i^Q, W_i^K, W_i^V$：第i个注意力头的线性投影权重
- $d_k$：键向量的维度
- $\Phi(\bar{P})$：T5式相对位置编码
- $A_i$：注意力权重矩阵（(m+1)×(m+1)），表示cCRE间及cCRE-基因间的互作强度
- $H_i$：第i个头的输出
- $W^F$：前馈网络权重

**用途**：注意力权重$A_i$是后续互作推断的核心——基因对应行的注意力分数被解释为cCRE对基因的调控强度。

---

**公式2：MSE损失**

$$\text{MSE} = \frac{1}{N}\sum_{i=1}^{N}(y_i - \bar{y}_i)^2 + \alpha\|W\|^2$$

- $N$：样本数
- $y_i$：真实表达值
- $\bar{y}_i$：预测表达值
- $\alpha$：L2正则化系数
- $\|W\|^2$：权重矩阵的L2范数

**用途**：回归任务的主损失函数。

---

**公式3：直接法（ScPGE-LP）注意力修改**

$$A_i = \text{softmax}\left(\exp(M) * \left(\frac{Q_i K_i^T}{\sqrt{d_k}} + \Phi(\bar{P})\right)\right)$$

- $M$：染色质环互作矩阵（(m+1)×(m+1)），有环为1，无环为0
- $*$：逐元素乘法
- $\exp(M)$：将环信息作为乘法门控，有环的cCRE对注意力权重指数放大

**用途**：将物理互作信息直接注入注意力计算。

---

**公式4：间接法（ScPGE-KL）KL散度损失**

$$R_g = \exp\left(-\frac{|x|}{2}\right)$$

$$M_g = M_g + R_g$$

$$\text{KLDivLoss} = M_g \log\frac{M_g}{\bar{A}_g}$$

$$\text{JointLoss} = \text{MSE} + \alpha * \text{KLDivLoss}$$

- $x$：cCRE与基因间的距离
- $R_g$：距离衰减的调控效应先验（由TP分析发现）
- $M_g$：基因g对应的环互作向量（加入距离衰减先验）
- $\bar{A}_g$：基因g对应的平均注意力权重向量
- $\alpha$：KL损失权重（设为1）

**用途**：通过KL散度将注意力分布对齐到"距离衰减+染色质环"的先验分布。

---

## 10 实验设计与证据链

### 数据集与设置

| 项目 | 详情 |
|------|------|
| RNA-seq数据 | 19个人类细胞系（ENCODE） |
| CAGE-seq数据 | 10个人类细胞系（与Enformer一致） |
| cCREs | SCREEN Registry V3（人类GRCh38），去除DNase-only和low-DNase标记，相邻cCRE合并（600bp窗口） |
| TF motifs | HOCOMOCO V11，769个motifs，按表达量取前600个active TFs |
| 表观信号 | DNase, H3K4me3, H3K27ac, CTCF（ENCODE） |
| 染色质环 | 5-kb分辨率，来自Loop Catalog（K562, GM12878） |
| 训练/验证/测试划分 | 染色体级别划分：chr16验证，chr8/9测试，其余训练 |
| 增强子-基因互作验证 | 3个公开数据集：Fulco et al. 2019 (677正/2239负), Gasperini et al. 2019, Schraivel et al. 2020；按距离分4组：<10kb, 10-50kb, 50-100kb, >100kb |
| 基线模型 | Enformer (预训练), CREaTor (重训练), EPInformer (重训练) |
| 指标 | 基因表达预测：PCC, MAE；互作识别：PRAUC, TPR |
| 硬件 | 单张A100 GPU |

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| RNA-seq表达预测（19细胞系） | ScPGE优于现有SOTA | ScPGE vs CREaTor vs EPInformer | ScPGE PCC比CREaTor高2.5%，MAE低27%；比EPInformer PCC高1.3%，MAE低1% | ScPGE在RNA-seq预测上优于基线 | 未提供逐细胞系breakdown；未报告显著性检验 | Results 图2A |
| CAGE-seq表达预测（10细胞系） | ScPGE优于Enformer和EPInformer | ScPGE vs Enformer(预训练) vs EPInformer | ScPGE PCC比Enformer高10%，MAE低9.6%；比EPInformer PCC高4.2%，MAE低2.7% | ScPGE在CAGE-seq预测上显著优于Enformer | 与Enformer比较时训练数据不完全一致（Enformer为预训练模型） | Results 图2B |
| 基因表达分类（GM12878/K562） | ScPGE能准确分类基因是否表达 | 二分类任务，表达>4为正，<1为负；负样本含cCRE/序列打乱 | 分类AUC接近1 | ScPGE在分类任务上高效 | 分类任务比回归简单，不能直接推广到回归性能 | Supplemental Fig. S3 |
| 表观信号可扩展性 | 增加表观信号数量提升性能 | 4 vs 13种表观信号 | 13种信号优于4种 | 表观信号数量是性能提升因素 | 未测试超过13种信号；未报告边际收益递减点 | Results 图2C |
| cCRE数量影响 | 更多cCRE不一定更好 | cCRE-20 vs cCRE-100 vs cCRE-200 | 性能随cCRE增加而下降 | 过多cCRE引入噪声 | 未分析最优cCRE数量的决定因素 | Results 图2D |
| Transformer层数影响 | Transformer是核心组件 | Tran-0 vs Tran-2 vs Tran-4 | Tran-0显著降低性能 | Transformer对建模cCRE关系至关重要 | 未测试超过4层 | Results 图2E,F |
| 增强子-基因互作识别（K562） | ScPGE能优先排序真实增强子-基因对 | ScPGE(attention) vs ScPGE(perturbation) vs EPInformer vs Enformer vs CREaTor；PRAUC指标 | ScPGE与EPInformer相当，优于Enformer和CREaTor | ScPGE的注意力机制可用于互作推断 | 仅K562细胞系；正负样本比例不平衡（677正/2239负） | Results 图3B |
| 距离分层互作识别 | 不同距离上性能有差异 | <10kb, 10-50kb, 50-100kb, >100kb四组 | 所有方法在>100kb上性能下降 | 远端互作识别是共同挑战 | 未报告各距离组的详细PRAUC数值 | Results 图3B |
| 基因案例验证（JUNB, KLF1） | ScPGE能识别已知增强子 | CRISPRi-FlowFISH验证的增强子；TPR指标 | ScPGE(attention)在JUNB上发现3/4增强子（TPR=75%）；ScPGE(attention+perturbation)在KLF1上发现全部6个 | ScPGE能识别实验验证的增强子 | 仅2个基因案例；TPR计算基于top-k选择，k=验证增强子数 | Results 图3C；Supplemental Fig. S4 |
| 染色质环整合效果 | ScPGE-LP/KL优于无环版本 | ScPGE vs ScPGE-LP vs ScPGE-KL；不同cCRE数量 | LP和KL在cCRE-100/200时优于ScPGE；KL在cCRE-20时优于LP | 染色质环提升远端互作识别 | 未报告与无环版本的统计显著性；未测试其他环数据来源 | Results 图5A,B |
| 组合方法（ScPGE-Loop） | 近端+远端互补 | ScPGE-Loop vs ScPGE-LP vs ScPGE-KL；42个基因TPR | Loop在30/42基因上优于单独方法 | 组合策略有效 | 未报告组合方法的计算开销 | Results 图5D |
| 跨物种预测 | ScPGE可跨物种泛化 | 人类训练→小鼠测试（CH12.LX, MEL） | PCC与种内相当，MAE显著升高 | ScPGE能捕获跨物种保守的调控规律 | 仅人类→小鼠；未测试更远物种 | Results 图4C |
| 跨细胞预测 | ScPGE可跨细胞泛化 | GM12878训练→K562测试（及反向） | 性能接近种内 | 调控规律在细胞间保守 | 仅2个细胞系 | Results 图4B |
| 模型复杂度 | ScPGE计算开销低 | 训练/推理时间、FLOPs、参数量 vs 基线 | ScPGE复杂度最低 | ScPGE适合资源受限场景 | 未提供具体数值对比表 | Supplemental Table S1 |
| 预测模式分析 | TP/FP/TN/FN有不同调控特征 | 分析四类预测的染色质信号分布 | TP中信号随距离衰减；FP类似TP；TN/FN信号接近0 | 距离衰减是真实调控规律 | 仅基于K562/GM12878 | Results 图4A；Supplemental Fig. S6 |
| TF motif发现 | ScPGE可发现已知TF motif | MEME-ChIP分析TP序列；与HOCOMOCO比对 | 发现SP1-like, CTCF-like, Kr-like等motifs | ScPGE优先的cCRE富集已知TF motif | 未与随机背景的富集显著性比较 | Results 图6A |
| 调控类型分析 | 不同cCRE类型有不同功能 | 统计TP中cCRE类型（PLS, pELS, dELS） | 近端元件（PLS, pELS）最频繁，dELS次之 | 近端调控占主导 | 未按细胞类型分层分析 | Results 图6B |

---

## 11 结论正确解读

- **任务范围**: 本文解决的是**基因表达预测**（回归任务）和**增强子-基因互作推断**（排序/优先化任务），而非直接的TF–DNA结合位点预测。TF结合分数作为输入特征，而非输出。
- **Oracle/真值输入**: 训练标签为实验测定的RNA-seq/CAGE-seq表达值；增强子-基因互作验证使用CRISPRi-FlowFISH实验数据。cCRE定义来自SCREEN Registry（基于实验的DNase/表观标记）。
- **端到端状态**: 是端到端训练——从cCRE的多模态特征直接预测基因表达，无需中间步骤。但cCRE的**选择**（来自SCREEN Registry）和**TF motif集合**（HOCOMOCO）是外部输入，非模型自动发现。
- **算力成本**: 单张A100 GPU即可训练，模型复杂度低于Enformer（具体数值见Supplemental Table S1，但摘要未提供具体数字）。
- **历史数据依赖**: 依赖ENCODE、SCREEN、HOCOMOCO等公共数据资源；跨物种泛化依赖调控机制的进化保守性。
- **模型依赖**: 性能依赖cCRE数量（默认20）、表观信号类型（默认4-13种）、TF motif集合（前600个active TFs）等超参数选择。
- **最难情形**: 远端互作（>100kb）的识别是所有方法的共同短板；跨物种的绝对表达水平预测（MAE高）是另一个难点。
- **群体/领域边界**: 训练和验证主要基于人类细胞系（K562, GM12878等血液/癌症细胞系），跨物种仅验证了人类→小鼠。对非模式生物、原代细胞、疾病样本的适用性未验证。
- **不确定性**: 未报告预测的置信区间；注意力权重作为互作推断的解释力缺乏与HiChIP/3C等物理互作数据的直接对比验证。

**有边界的复述**: ScPGE在19个人类细胞系的RNA-seq和10个细胞系的CAGE-seq表达预测中优于CREaTOR、EPInformer和Enformer，在K562增强子-基因互作优先化上与EPInformer相当，且通过引入染色质环可进一步提升远端互作识别。这些结论限于人类细胞系数据，跨物种（人类→小鼠）仅验证了相关性模式而非绝对表达水平。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 远端cCRE-基因互作预测性能有限 | 所有方法在>100kb距离上性能下降 | 引入染色质环（ScPGE-LP/KL）作为缓解手段 | Results 图3B；Discussion |
| cCRE数量增加引入噪声 | 使用更多cCRE时性能下降 | 未明确提及；[Analysis] 可探索注意力机制自动筛选重要cCRE | Results 图2D |
| 跨物种绝对表达预测偏差 | 跨物种MAE显著高于种内 | 未明确提及；[Analysis] 可能需要物种特异微调或领域自适应 | Results 图4C |
| 染色质环数据稀疏 | 多数细胞类型缺乏HiChIP数据 | 未明确提及；[Analysis] 可探索从序列预测染色质环 | Methods "Incorporation of chromatin loops" 节 |
| 超参数未系统探索 | 如cCRE数量、Transformer层数、motif数量等 | 作者仅做了初步探索（Supplemental Fig. S12），未做全网格搜索 | Discussion |
| 注意力机制与物理互作的非完全对齐 | 注意力分数高的cCRE不总是实验验证的增强子 | 未明确提及；[Analysis] 可结合可解释性方法进一步验证 | Results 图3C |
| 模型可解释性有限 | 注意力权重和DeepLIFT贡献提供了部分解释，但缺乏系统性验证 | 未明确提及 | Discussion |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| 与基线比较的公平性 | ScPGE使用cCRE离散输入，而Enformer使用连续长序列；训练数据、预处理流程可能不一致 | 性能提升可能来自输入表示差异而非模型架构优势 | 在完全相同的训练/测试划分和预处理下重跑所有基线；报告标准化流程 | Results 图2A,B；Methods "Baseline methods" 节 |
| 注意力机制作为互作推断的效度 | 注意力权重高不必然意味着因果调控关系；可能反映的是共发生模式而非功能互作 | 如果注意力推断不可靠，则基于注意力的增强子优先化可能产生误导 | 与HiChIP、CRISPR筛选等实验数据做系统对比；计算注意力与物理互作的相关性 | Results 图3B,C |
| 距离衰减规律的普适性 | 该规律可能仅适用于K562/GM12878等特定细胞类型或血液系统 | 如果规律不普适，基于该规律设计的KL方法可能在其他细胞类型失效 | 在更多细胞类型（如上皮、神经）中验证距离衰减模式 | Results 图4A；Supplemental Fig. S7 |
| 染色质环整合的增益来源 | ScPGE-LP/KL的增益可能来自正则化效应而非环信息的生物学意义 | 如果增益来自正则化，则任何先验分布都可能有效 | 使用随机/打乱的环矩阵作为阴性对照 | Results 图5A,B |
| 跨物种泛化的解释 | PCC相当但MAE高可能反映的是分布偏移而非调控机制保守 | 跨物种结论可能被过度解读 | 分析跨物种预测误差与基因功能/保守性的关联 | Results 图4C |
| 案例验证的选择偏差 | JUNB和KL1是血液系统重要基因，可能偏向ScPGE的优势区域 | 案例验证不能代表全基因组性能 | 在随机选择的基因集上做系统验证 | Results 图3C；Supplemental Fig. S4 |
| 未报告统计显著性 | 性能提升（如2.5% PCC）未报告置信区间或显著性检验 | 小幅度提升可能不具统计显著性 | 多次重复实验，报告均值±标准差和p值 | Results 图2A,B |
| 超参数敏感性 | 默认cCRE=20可能不是最优；不同细胞类型可能需要不同设置 | 模型鲁棒性未验证 | 在多个细胞类型上做超参数敏感性分析 | Results 图2D；Supplemental Fig. S12 |
| 与TF–DNA结合机制的直接关联 | 本文预测的是基因表达，TF结合分数是输入特征而非输出；对TF–DNA结合机制本身的贡献有限 | 如果读者期望本文揭示TF结合机制，可能失望 | 明确区分"基因表达预测"与"TF–DNA结合机制解析"两个任务 | 全文 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

### 可迁移概念

1. **离散cCRE的三维张量表示**：将基因组上的离散调控元件（而非连续序列）作为基本处理单元，将多模态信息（序列、TF结合、表观）组织为张量，用CNN并行处理。这一表示方法可迁移到TF–DNA结合位点预测任务——将候选结合位点及其周围元件组织为张量，整合序列+染色质可及性+TF共结合信息。

2. **调控效应距离衰减规律**：通过分析预测结果的TP/FP模式，发现cCRE对基因的调控效应随距离呈指数衰减（exp−|x|/2）。这一规律可作为先验知识注入模型（如KL散度损失），也可用于TF–DNA结合预测中的特征加权——距离越远的元件权重越低。

3. **注意力机制作为互作推断工具**：自注意力权重可直接解释为cCRE-基因互作强度，无需额外训练分类器。在TF–DNA结合研究中，可类似地用注意力权重推断"哪些TF协同结合同一调控区域"。

4. **直接+间接双通道知识注入**：将先验知识（染色质环）同时通过架构修改（直接法）和损失函数（间接法）注入模型，两种方式效果互补。这一策略可迁移到TF–DNA结合预测——将已知的TF结合协同性通过注意力掩码（直接）和辅助损失（间接）注入。

5. **轻量级设计**：ScPGE在单张A100 GPU上即可训练，远低于Enformer的资源需求。对于资源受限的实验室，这种轻量级框架更易复现和部署。

### 可迁移方法

1. **多模态特征组装流程**：序列（one-hot）+ TF motif扫描分数 + 表观信号 → 三维张量 → CNN特征提取 → Transformer关系建模 → 预测。这一pipeline可直接迁移到TF–DNA结合强度预测，将"表观信号"替换为"染色质可及性/DNase-seq"。

2. **In silico perturbation**：通过masking每个cCRE计算预测变化，评估cCRE对基因表达的功能贡献。在TF–DNA结合研究中，可类似地通过perturbation评估每个TF motif对结合强度的贡献。

3. **DeepLIFT特征归因**：计算每个TF motif对预测的贡献分数，用于识别关键调控因子。可迁移到TF–DNA结合预测中，解释哪些序列特征驱动了结合预测。

4. **TP/FP模式分析**：将预测结果分类为TP/FP/TN/FN，分析各类别的特征分布差异，从中发现生物学规律（如距离衰减）。这种"预测→分类→模式发现→模型优化"的闭环方法可推广到其他调控预测任务。

5. **跨物种验证策略**：人类训练→小鼠测试，验证模型的物种泛化能力。在TF–DNA结合研究中，可类似地验证模型在模式生物（小鼠、果蝇）上的迁移能力。

### 对TF–DNA结合机制研究的启示

- **从"预测表达"到"预测结合"**：ScPGE的框架可改造为预测TF在特定基因组位点的结合强度，将cCRE替换为候选结合位点，将基因表达标签替换为ChIP-seq peak强度。
- **多模态整合的必要性**：ScPGE证明序列+TF结合+表观的多模态整合优于单一模态。TF–DNA结合预测同样需要整合序列motif、染色质可及性、TF共结合等信息。
- **距离衰减规律可能适用于TF结合**：TF对远端增强子的结合可能也遵循距离衰减规律，可作为先验知识引入结合预测模型。

---

## 15 与已有知识连接

### 相似工作

- **Enformer (Avsec et al. 2021)**: 本文的主要基线之一。Enformer使用长连续序列（196kb）预测基因表达，而ScPGE使用离散cCREs，计算效率更高。两者都使用Transformer架构，但ScPGE的输入表示更紧凑。
- **CREaTOR (Li et al. 2023)**: 本文的另一主要基线。CREaTOR使用层次注意力建模cCRE-基因关系，与ScPGE的Transformer思路相似，但ScPGE额外整合了TF结合分数和染色质环。
- **EPInformer (Lin et al. 2024)**: 整合增强子-启动子互作的Transformer模型，与ScPGE在互作建模上思路相近。
- **Basenji / DeepSEA**: 早期用CNN预测调控功能的模型，ScPGE的CNN特征提取部分与其一脉相承。

### 可组合方向

- **AlphaFold-style TF-DNA结构预测**: ScPGE的序列编码思路可与结构预测结合——先预测结合位点，再预测结合构象。
- **DeepMind的Enformer**: ScPGE可视为Enformer的轻量级替代，两者可互相验证。
- **Chromatin loop预测模型 (如HiC-Reg)**: ScPGE将染色质环作为输入特征，而HiC-Reg等模型预测染色质环——两者可组合成闭环：预测环→用环预测表达。

### 理论框架

- **cis-regulatory grammar**: ScPGE的注意力机制可视为在学习"顺式调控语法"——哪些元件组合驱动表达。
- **增强子-启动子互作模型**: ScPGE的注意力权重提供了增强子-启动子互作的统计推断，与HiChIP等实验数据互补。

### 候选研究方向

- **TF结合位点预测**: 将ScPGE框架改造为预测TF结合强度，整合序列+染色质可及性+共结合TF信息。
- **突变效应预测**: ScPGE的in silico perturbation可扩展为预测SNV对基因表达的影响，类似DeepSEA的eQTL分析。
- **跨物种调控预测**: ScPGE的跨物种验证可扩展到更多物种，探索调控机制的进化保守性。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选1：TF–DNA结合强度预测的轻量级多模态框架

- **名称**: TF-BindPGE (Transcription Factor Binding Prediction from cis-regulatory Elements)
- **来源局限/观察**: ScPGE将TF结合分数作为输入特征预测基因表达，但未直接预测TF结合本身。ChIP-seq实验成本高，计算预测TF结合位点仍有提升空间。
- **核心假设**: 将cCRE的序列、表观遗传信号和共结合TF信息整合为三维张量，用CNN+Transformer可以准确预测TF在特定基因组位点的结合强度。
- **初步方法**: 借鉴ScPGE的三维张量组装和CNN+Transformer架构，将输出层改为TF结合强度回归（或二分类），训练标签使用ENCODE ChIP-seq peak强度。整合DNA序列（one-hot）、DNase-seq、其他TF的ChIP-seq信号作为输入。
- **验证方式**: 在ENCODE 690个TF ChIP-seq数据集上评估，与DeepSEA、Basenji等基线比较AUC和AUPRC。
- **创新点**: 轻量级设计（单GPU可训练）、多模态整合、注意力机制可解释TF协同结合。
- **创新状态**: unverified

### 候选2：基于距离衰减先验的远端增强子-基因互作预测

- **名称**: DistalLoopPrior
- **来源局限/观察**: ScPGE发现调控效应随距离衰减，但仅用exp−|x|/2作为先验，未系统建模距离与调控强度的关系。远端互作（>100kb）仍是所有方法的短板。
- **核心假设**: 将距离衰减先验从简单的指数函数扩展为可学习的距离-调控强度函数，可以提升远端增强子-基因互作的预测精度。
- **初步方法**: 在ScPGE的注意力机制中引入可学习的距离核函数（如高斯核、Matern核），替代固定的exp−|x|/2。同时引入染色质环作为硬约束，将HiChIP数据作为注意力掩码。
- **验证方式**: 在K562/GM12878增强子-基因互作数据集上比较不同距离核函数的PRAUC，重点分析>100kb的互作。
- **创新点**: 可学习的距离衰减函数、距离与染色质环的联合建模。
- **创新状态**: unverified

### 候选3：跨物种TF–DNA结合motif的进化保守性分析

- **名称**: CrossSpeciesTFMotifConservation
- **来源局限/观察**: ScPGE的跨物种预测（人类→小鼠）显示MAE升高，但PCC保持，说明调控逻辑保守但绝对水平有差异。TF–DNA结合motif的跨物种保守性尚未被系统分析。
- **核心假设**: 通过对比人类和小鼠的TF结合预测，可以识别进化保守的TF–DNA结合motif，这些motif可能对应核心调控功能。
- **初步方法**: 训练人类和小鼠的TF结合预测模型，对同源基因的启动子/增强子区域进行预测，比较注意力权重和DeepLIFT贡献分数，识别跨物种保守的高贡献motif。
- **验证方式**: 与已知的保守非编码元件（如PhyloP评分）比较，验证保守motif的功能重要性。
- **创新点**: 将深度学习可解释性方法用于跨物种进化分析。
- **创新状态**: unverified

### 候选4：从基因表达预测到TF结合协同性推断

- **名称**: TFCoBindingInference
- **来源局限/观察**: ScPGE的注意力机制可以识别重要cCRE，但未分析cCRE内部TF的协同结合模式。TF协同结合是调控复杂性的重要来源。
- **核心假设**: 通过分析ScPGE注意力权重中cCRE间的共注意力模式，可以推断TF的协同结合关系。
- **初步方法**: 对ScPGE的注意力矩阵进行聚类分析，识别共调控的cCRE模块；对模块内的TF motif进行富集分析，推断TF协同结合对。
- **验证方式**: 与已知的TF协同结合数据库（如ENCODE ChIP-seq共结合数据）比较。
- **创新点**: 将基因表达预测模型的注意力机制转化为TF协同结合发现工具。
- **创新状态**: unverified

### 候选5：基于ScPGE的SNV调控效应预测

- **名称**: ScPGE-SNV
- **来源局限/观察**: ScPGE的in silico perturbation可以评估cCRE对基因表达的功能贡献，但未扩展到SNV水平的调控效应预测。
- **核心假设**: 通过比较参考和变异序列的ScPGE预测差异，可以准确预测SNV对基因表达的调控效应。
- **初步方法**: 对给定SNV，分别用参考和变异序列构建cCRE张量，计算预测表达差异。在eQTL数据上验证。
- **验证方式**: 与GTEx eQTL数据比较，评估AUC。
- **创新点**: 将基因表达预测模型直接应用于变异效应预测。
- **创新状态**: unverified