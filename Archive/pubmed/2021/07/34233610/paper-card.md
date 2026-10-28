## 01 基本信息

- **标题**：DeepHBV: a deep learning model to predict hepatitis B virus (HBV) integration sites
- **作者**：Wu, Canbiao; Guo, Xiaofang; Li, Mengyuan; Shen, Jingxian; Fu, Xiayu; Xie, Qingyu; Hou, Zeliang; Zhai, Manman; Qiu, Xiaofan; Cui, Zifeng; Xie, Hongxian; Qin, Pengmin; Hu, Zheng; Liang, Jiuxing
- **单位**：未提供（作者所属机构未在摘要/全文中明确列出）
- **期刊/平台**：BMC Ecology and Evolution
- **年份**：2021
- **论文类型**：方法学/应用研究（深度学习模型开发与验证）
- **领域**：病毒基因组整合预测；计算生物学；深度学习
- **关键词**：HBV integration; Deep learning; Attention mechanism; Transcription factor binding sites; Genomic features
- **DOI/arXiv 号**：10.1186/s12862-021-01869-8
- **代码**：未提供
- **数据**：dsVIS 数据库（http://dsvis.wuhansoftware.com）；VISDB 数据库（独立验证集）
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 深度学习」方向，但对象是**病毒（HBV）DNA 整合位点**而非 TF–DNA 结合位点。其核心可迁移价值在于：(1) 用 CNN + attention 从 DNA 序列中自动学习局部基因组特征；(2) 用 attention 权重定位关键序列区域，再通过 HOMER 富集 TFBS 基序，将深度学习"黑箱"输出与 TF–DNA 结合机制关联。该思路可直接迁移到 TF–DNA 结合位点预测与基序发现任务。

---

## 02 一句话总结

本文开发了一个基于 attention 机制的 CNN 模型 DeepHBV，以 2000 bp DNA 序列为输入预测 HBV 整合位点，通过加入重复序列（repeat peaks）和 TCGA Pan-Cancer 峰特征将 AUROC 从 0.6363 提升至 0.9430，并利用 attention 权重定位关键区域，经 HOMER 富集发现 AR-halfsite、Arnt、Atf1、bHLHE40、BMAL1、CLOCK、c-Myc 等 TFBS 在整合位点附近显著富集。

---

## 03 研究问题

- **具体问题**：HBV 整合位点在人类基因组中的分布看似随机，但实际存在偏好性。能否用深度学习模型从 DNA 序列中自动学习这些偏好特征，并预测一个给定的 2000 bp 基因组区域是否为 HBV 整合位点？
- **为什么重要**：HBV 整合是病毒促进肝细胞癌（HCC）恶性转化的关键步骤之一。理解整合位点的选择偏好，有助于揭示 HBV 相关肝癌的分子机制，并可能为治疗靶点提供线索。
- **现有方法不足**：此前尚无专门针对 HBV 整合位点预测的深度学习模型。已有的 DeepHINT 是为 HIV 整合位点设计的，其网络结构较浅（单卷积层），在 HBV 数据上表现有限。传统方法多依赖已知基因组特征（如重复区、CpG 岛）的统计富集，缺乏从序列本身自动学习特征的能力。
- **精确研究问题**：Can an attention-based deep learning model learn local genomic sequence features to accurately predict HBV integration sites, and can the attention mechanism highlight biologically meaningful regions enriched for transcription factor binding sites?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引用与讨论，属于「经外部核验」的领域发展概述，但具体分期与代表性方法的选择是本文框架下的整理。

1. **HBV 整合的生物学研究阶段**（~2000s–2010s）
   - 代表方法：基于高通量测序的整合位点检测（如 RNA-seq、WGS 数据中的嵌合 reads）
   - 发现：HBV 整合在 HCC 中普遍存在（85–90%），且倾向于整合到基因区、重复区、CpG 岛附近
   - 局限：多为描述性统计，缺乏预测能力

2. **基于基因组特征的统计富集阶段**（~2010s）
   - 代表方法：对已知整合位点做 repeat、CpG、组蛋白修饰、DNase 等特征的富集分析
   - 发现：整合位点附近存在特定基因组环境偏好
   - 局限：特征需人工定义，无法捕捉序列层面的复杂模式

3. **深度学习应用于病毒整合预测阶段**（~2019–2021）
   - 代表方法：DeepHINT（HIV 整合位点预测，单层 CNN）
   - 优点：首次将 CNN 用于病毒整合位点预测
   - 局限：网络较浅，未使用 attention，未针对 HBV 优化
   - **本文位置**：DeepHBV 是首个针对 HBV 的 attention-based CNN 模型，通过加深网络（2 层卷积）和引入基因组特征（repeat、TCGA Pan-Cancer）显著提升性能，并利用 attention 机制实现可解释性分析。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| HBV 整合位点预测精度低 | 仅用序列数据时 AUROC 仅 0.6363 | 序列本身携带的信号有限，需结合基因组特征 | Results 节，图 2 |
| 已有模型（DeepHINT）不适用于 HBV | DeepHINT 在 HBV 数据上 AUROC 0.6199，低于 DeepHBV | DeepHINT 网络结构简单（单卷积层），特征提取能力不足 | Results 节，图 2 |
| 深度学习"黑箱"问题 | 模型预测准确但无法解释哪些序列区域起关键作用 | CNN 的层级特征提取难以直接对应到生物学功能单元 | Discussion 节 |
| 整合位点附近 TFBS 富集不明确 | 已知整合偏好重复区、CpG 等，但 TFBS 层面的偏好未知 | 缺乏从序列层面系统扫描 TFBS 的手段 | Results 节，表 2 |
| 基因组特征整合方式粗糙 | 简单拼接特征与序列，未考虑特征间的空间关系 | 需要更精细的特征融合策略 | [Analysis] 作者未明确讨论此点，但方法中特征以 one-hot 扩展方式加入 |

---

## 06 核心思想

### 1) 表面方法
- 构建一个 2 层 CNN + attention 的深度学习模型，输入为 2000 bp DNA 序列的 one-hot 编码（4×2000 二进制矩阵），输出为该序列是否为 HBV 整合位点的二分类概率。
- 训练数据来自 dsVIS 数据库，正样本为已知 HBV 整合位点上下游各 1000 bp，负样本为远离已知整合位点的随机区域（数量为 2 倍）。
- 在序列基础上，将基因组特征（repeat peaks、TCGA Pan-Cancer peaks 等）以额外通道或拼接方式加入模型，测试不同特征组合对性能的影响。

### 2) 核心洞察
- **序列局部特征 + 基因组环境特征互补**：仅用序列时模型性能有限（AUROC 0.6363），但加入 repeat 或 TCGA Pan-Cancer 峰后 AUROC 分别提升至 0.8378 和 0.9430，说明 HBV 整合位点的可预测性主要来自基因组环境特征，而非单纯的序列基序。
- **Attention 权重可定位关键区域**：通过反卷积和反池化将 attention 权重映射回基因组坐标，发现高权重区域与已知基因组特征（如 repeat、TCGA 峰）有对应关系，且这些区域富集 TFBS。
- **TFBS 富集揭示整合偏好机制**：HOMER 富集分析发现 AR-halfsite、Arnt、Atf1、bHLHE40、bHLHE41、BMAL1、CLOCK、c-Myc 等 TFBS 在 attention 高权重区域显著富集，提示 HBV 整合可能偏好 TF 密集结合的染色质区域。

### 3) 可能的普适教训 [Analysis]
- **Attention 不只是"可解释性工具"，更是特征发现工具**：本文展示了 attention 权重可以引导下游基序富集分析，这一思路可迁移到 TF–DNA 结合位点预测中——用 attention 定位模型认为关键的序列区域，再用基序扫描工具验证这些区域是否富集已知或 novel TFBS。
- **基因组特征与序列特征的融合策略值得借鉴**：本文通过简单拼接方式加入特征即获得显著提升，说明在 TF–DNA 结合预测中，将 DNase-seq、ChIP-seq 峰等实验特征与序列特征结合可能比纯序列模型更有效。
- **负样本选择策略**：负样本取远离已知整合位点 50 kb 以上的区域，避免"热点"区域污染，这一策略对 TF–DNA 结合位点预测的负样本设计有参考价值。

---

## 07 方法总览

- **输入**：2000 bp DNA 序列（整合位点上下游各 1000 bp），one-hot 编码为 4×2000 二进制矩阵；可选附加基因组特征（repeat peaks、TCGA Pan-Cancer peaks 等）以 one-hot 扩展方式并入。
- **输出**：二分类概率（该 2000 bp 区域是否为 HBV 整合位点）。
- **模型结构**：
  1. 卷积层 1：128 个卷积核，核大小 8
  2. 卷积层 2：256 个卷积核，核大小 6
  3. 池化层：最大池化，池化大小 3
  4. Attention 层：对池化后的特征向量计算 attention 权重
  5. 反卷积 + 反池化：将 attention 权重映射回输入序列位置
  6. 全连接层 + sigmoid 分类器
- **训练**：损失函数为二元交叉熵；优化器未明确说明；框架为 TensorFlow 1.13.1 + scikit-learn 0.24；硬件为 NVIDIA Tesla V100-PCIE-32G。
- **评估**：十折交叉验证；指标包括 accuracy、sensitivity、specificity、AUROC、AUPR、MCC、F1-score。
- **可解释性分析**：提取 attention 权重，经反卷积/反池化映射回基因组坐标，定义 attention 高权重区域（attention-intensive regions），用 HOMER v4.11.1 做 TFBS 基序富集。
- **流程**：数据准备（正负样本提取）→ one-hot 编码 → 模型训练（十折交叉验证）→ 性能评估 → attention 权重提取 → 基因组映射 → TFBS 富集分析。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| One-hot 编码层 | 将 DNA 序列转换为数值矩阵 | 神经网络无法直接处理字符序列 | 输入：2000 bp 序列；输出：4×2000 二进制矩阵 | Methods 节 | 无法移除（模型输入必需） |
| 卷积层 1（128 核，核大小 8） | 提取局部序列模式（k-mer 类特征） | 捕获短程序列基序 | 输入：4×2000 矩阵；输出：128 通道特征图 | Methods 节；与 DeepHINT 对比中体现更深网络优势 | [预期] 减少卷积核或层数会降低特征提取能力，导致 AUROC 下降（作者未做消融实验） |
| 卷积层 2（256 核，核大小 6） | 提取更高层级的序列组合特征 | 捕获更长距离的序列依赖 | 输入：卷积层 1 输出；输出：256 通道特征图 | Methods 节 | [预期] 移除后模型退化为单层 CNN，接近 DeepHINT 结构，性能可能下降至 AUROC ~0.62 |
| 最大池化层（大小 3） | 降维并引入平移不变性 | 使模型对特征位置微移不敏感 | 输入：卷积层 2 输出；输出：降维特征图 | Methods 节 | [预期] 移除后特征维度增大，可能过拟合 |
| Attention 层 | 计算每个位置对预测的贡献权重 | 提供可解释性，定位关键区域 | 输入：池化后特征；输出：权重向量 W | Results 节图 3；attention 权重用于后续 TFBS 富集 | [预期] 移除后模型变为纯 CNN，失去可解释性，无法定位关键区域 |
| 反卷积 + 反池化 | 将 attention 权重映射回基因组坐标 | 将抽象特征对应到具体序列位置 | 输入：attention 权重；输出：667×1 权重向量（每 3 bp 一个值） | Methods 节 | [预期] 移除后无法进行基因组层面的可解释分析 |
| 基因组特征融合（repeat/TCGA Pan-Cancer） | 将实验/注释特征并入模型 | 序列信息不足，需外部特征补充 | 输入：one-hot 序列 + 特征 one-hot；输出：扩展矩阵 | Results 节图 2：加入后 AUROC 从 0.6363 提升至 0.8378/0.9430 | [实测] 移除后性能显著下降（对比图 2 中不同模型曲线） |
| 全连接 + sigmoid 分类器 | 输出二分类概率 | 完成预测任务 | 输入：拼接后的特征向量；输出：0-1 概率 | Methods 节 | 无法移除（模型输出必需） |

---

## 09 关键公式符号

1. **卷积操作**：
   $$X_{k,j} = \sum_{j=0}^{p-1} \sum_{l=1}^{L} W_{k,j,l} E_{l,i+j}$$
   - $X_{k,j}$：第 $k$ 个卷积核在位置 $j$ 的输出
   - $W_{k,j,l}$：第 $k$ 个卷积核的权重
   - $E_{l,i+j}$：one-hot 编码矩阵在通道 $l$、位置 $i+j$ 的值
   - $p$：卷积核大小（8 或 6）
   - $L$：输入通道数（4，对应 A/T/C/G）

2. **Attention 权重计算**：
   $$W = att(a_1, a_2, \dots, a_q)$$
   - $W$：attention 权重向量
   - $a_i$：第 $i$ 个位置的特征向量
   - $q$：特征向量数量（667，对应 2000 bp / 3 bp 每位置）

3. **Attention 加权特征**：
   $$F_a = \sum_{j=1}^{q} a_j v_j$$
   - $F_a$：attention 加权后的特征向量
   - $a_j$：第 $j$ 个位置的 attention 权重
   - $v_j$：第 $j$ 个位置的特征向量

4. **最终预测**：
   $$P = sigmoid(concat(F_a, F_v))$$
   - $P$：预测概率
   - $F_a$：attention 加权特征
   - $F_v$：全连接层映射后的特征向量
   - $concat()$：向量拼接操作

5. **损失函数（二元交叉熵）**：
   $$Loss = -\sum_{i} y_i \log(P) + (1-y_i) \log(1-P)$$
   - $y_i$：第 $i$ 个样本的真实标签（1 为正样本，0 为负样本）
   - $P$：模型预测概率

---

## 10 实验设计与证据链

### 数据集与设置
- **训练/测试数据**：dsVIS 数据库 HBV 整合位点；正样本 2902 条（训练）、1264 条（测试）；负样本为 2 倍数量（5804 训练、2528 测试），取自远离已知整合位点 ≥50 kb 的区域。
- **独立验证集**：VISDB 数据库（未说明具体样本量）。
- **输入长度**：2000 bp（500/1000/2000/4000 bp 均测试，2000 bp 最优）。
- **基准模型**：DeepHINT（HIV 整合位点预测模型，单层 CNN）。
- **指标**：accuracy、sensitivity、specificity、AUROC、AUPR、MCC、F1-score。
- **硬件**：NVIDIA Tesla V100-PCIe-32G。
- **框架**：TensorFlow 1.13.1、scikit-learn 0.24。

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 序列长度选择 | 2000 bp 为最优输入长度 | 500/1000/2000/4000 bp 对比 | 2000 bp 时 accuracy 0.7368、AUROC 0.6901 最高 | 2000 bp 包含足够上下文信息 | 未测试更长序列（如 10 kb） | Results 节，Additional file 4: Table S5 |
| DeepHBV vs DeepHINT（仅序列） | DeepHBV 结构优于 DeepHINT | 相同 HBV 训练/测试数据 | DeepHBV AUROC 0.6363 vs DeepHINT 0.6199 | DeepHBV 的 2 层卷积结构更优 | 差异较小，未报告显著性检验 | Results 节，图 2 |
| 加入 repeat 特征 | 重复序列特征提升预测 | DeepHBV+序列 vs DeepHBV+序列+repeat | AUROC 从 0.6363 提升至 0.8378 | repeat 特征是强预测因子 | 未分析 repeat 亚型（如 LINE/SINE）的贡献差异 | Results 节，图 2 |
| 加入 TCGA Pan-Cancer 特征 | 癌症相关峰特征提升预测 | DeepHBV+序列 vs DeepHBV+序列+TCGA | AUROC 从 0.6363 提升至 0.9430 | TCGA 峰特征是最强预测因子 | 未说明 TCGA 峰的具体类型（如 ChIP-seq 峰、CNV 峰等） | Results 节，图 2 |
| VISDB 独立验证 | 模型泛化性 | dsVIS 训练 → VISDB 测试 | repeat 模型 AUROC 0.6657；TCGA 模型 AUROC 0.7603 | 模型可泛化至独立数据集 | 性能下降明显（0.94→0.76），可能存在数据集偏差 | Results 节 |
| Attention 权重分布 | 正样本存在 attention 峰-谷-峰模式 | 正样本 vs 负样本 attention 分布 | 正样本呈现峰-谷-峰模式，负样本无此模式 | Attention 捕获了整合位点的结构特征 | 未量化峰-谷-峰的统计显著性 | Results 节，图 3 |
| TFBS 富集分析 | 高 attention 区域富集特定 TFBS | HOMER 已知基序数据库 | 富集 AR-halfsite、Arnt、Atf1、bHLHE40、bHLHE41、BMAL1、CLOCK、c-Myc、COUP-TFII、E2A、EBF1、Erra、Foxo3 等 | 整合位点偏好 TF 密集区域 | 未做 motif 置换检验或共富集分析 | Results 节，表 2 |

---

## 11 结论正确解读

- **任务范围**：本文解决的是**二分类预测问题**——给定 2000 bp 基因组区域，判断是否为 HBV 整合位点。不是回归、不是整合断点精确定位、不是整合机制建模。
- **Oracle/真值输入**：正样本标签来自 dsVIS 数据库的已知整合位点，负样本为远离整合位点的随机区域。模型性能高度依赖数据库质量；若 dsVIS 存在假阳性/假阴性，模型性能会被高估/低估。
- **端到端状态**：模型是端到端训练的（序列 → 预测），但**特征融合**（repeat/TCGA）需要外部注释数据，并非纯序列端到端。
- **算力成本**：模型规模较小（2 层 CNN），在单张 V100 上可训练，成本可控。
- **历史数据依赖**：训练数据来自 dsVIS（截至 2021 年），整合位点检测技术（如 WGS 深度、分析流程）会影响位点集合的完整性和准确性。
- **模型依赖**：性能高度依赖基因组特征（TCGA Pan-Cancer 峰），若在无这些注释的物种/细胞系中应用，性能会显著下降。
- **最难情形**：模型在独立数据集 VISDB 上 AUROC 从 0.94 降至 0.76，说明跨数据库泛化是薄弱环节；对非编码区、重复区内的整合位点预测可能更困难（未单独分析）。
- **有边界的复述**：DeepHBV 在 dsVIS 数据上，通过结合序列与基因组特征，能以 AUROC 0.94 的准确度区分 HBV 整合位点与非整合区域；attention 机制定位的关键区域富集多种 TFBS，提示整合偏好与 TF 结合相关。该结论仅适用于人类基因组（hg38）、HBV 整合场景，且未经过实验验证。

---

## 12 作者自认局限

在提供的材料中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限）：
- 模型性能在独立数据集 VISDB 上明显下降（AUROC 0.94→0.76），作者未解释原因，但暗示跨数据库泛化存在挑战。
- Attention 高权重区域与基因组特征的对应关系"not quite clear"（Results 节），说明可解释性分析仍有模糊之处。
- TFBS 富集结果来自生物信息学预测（HOMER），作者指出"biological significance that warrants future experimental confirmation"（Discussion 节），即缺乏实验验证。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 负样本选取策略可能引入偏差 | 负样本取远离已知整合位点 ≥50 kb 的区域，但这些区域可能包含未检测到的整合位点（假阴性），导致模型学到"距离已知位点远"这一简单特征而非真正的序列特征 | 若负样本被污染，模型性能被高估 | 用独立实验验证的整合位点集合重新标注负样本；或对比不同负样本选取策略下的模型性能 | Methods 节 |
| TCGA Pan-Cancer 特征提升幅度过大（AUROC 0.64→0.94） | 可能因为 TCGA 峰与整合位点存在直接重叠（即 TCGA 数据本身包含 HBV 整合样本），造成特征泄漏 | 若存在泄漏，模型在无 TCGA 数据的场景中不可用 | 检查 TCGA 峰与训练/测试集整合位点的重叠比例；用不含 HBV 相关样本的 TCGA 数据重新训练 | Results 节，图 2 |
| Attention 权重与 TFBS 富集的因果方向不明 | 高 attention 区域富集 TFBS 可能只是反映了整合位点附近的染色质开放性（DNase 峰），而非 TF 结合直接驱动整合 | 因果方向影响对机制的解读 | 用 DNase-seq 数据做共富集分析；比较 TFBS 富集与随机区域背景的差异 | Results 节，表 2 |
| 未报告模型不确定性或置信度校准 | 模型输出概率未评估校准度，高置信度预测可能不可靠 | 实际应用中需要可靠的置信度 | 绘制可靠性图（reliability diagram）；计算 ECE 指标 | 未提供 |
| 与 DeepHINT 的对比不充分 | 仅比较了 AUROC/AUPR，未比较其他指标（如精确率-召回率曲线下面积、校准度、推理速度） | 无法全面评估模型优势 | 补充多指标对比实验 | Results 节，图 2 |
| 未做消融实验 | 未单独评估 attention 模块的贡献，无法确定 attention 是否真正提升了预测性能 | 无法判断 attention 是核心组件还是附加组件 | 训练无 attention 的版本对比性能 | 未提供 |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **Attention 权重作为"可解释性引导的基序发现"工具** [可迁移，高价值]
   - 本文展示了 attention 权重 → 反卷积/反池化 → 基因组坐标 → HOMER 富集的完整流程。在 TF–DNA 结合位点预测中，可完全复用此流程：训练一个预测 TF 结合位点的 CNN+attention 模型，提取 attention 高权重区域，用 HOMER 或 FIMO 富集已知 TF 基序，或发现 novel 基序。
   - 迁移方式：将"整合位点"替换为"TF 结合位点"，将"HBV 序列"替换为"ChIP-seq 峰内序列"。

2. **基因组特征与序列特征的融合策略** [可迁移，中高价值]
   - 本文通过将 repeat/TCGA 峰以 one-hot 方式并入输入，显著提升性能。在 TF–DNA 结合预测中，可类似地并入 DNase-seq 峰、组蛋白修饰峰、染色质状态注释等特征，作为序列特征的补充。
   - 注意：需警惕特征泄漏（见批判性分析第 2 条），融合前应检查特征与标签的独立性。

3. **负样本设计原则** [可迁移，中价值]
   - 负样本选取时避开已知正样本周围 50 kb 区域，避免"热点"污染。在 TF–DNA 结合位点预测中，负样本应取远离已知结合位点的区域，且最好匹配 GC 含量、重复密度等分布。

4. **"峰-谷-峰"attention 模式作为正样本标志** [可迁移，需验证]
   - 本文发现正样本 attention 分布呈峰-谷-峰模式，负样本无此模式。在 TF–DNA 结合预测中，可检验 attention 是否在结合位点中心形成类似模式，并作为可解释性指标。

5. **跨数据库泛化评估的必要性** [方法论，高价值]
   - 本文在独立数据集 VISDB 上验证了模型泛化性（尽管性能下降）。在 TF–DNA 结合预测中，应始终用独立物种/细胞系/实验条件的数据集验证模型，而非仅依赖同源数据交叉验证。

6. **HOMER 基序富集作为深度学习输出的下游验证** [可迁移，高价值]
   - 将模型关注的区域用 HOMER 做基序富集，可将"黑箱"输出转化为可解释的 TF 结合假设。在 TF–DNA 结合研究中，这不仅是验证手段，更是新基序发现的起点。

---

## 15 与已有知识连接

1. **DeepHINT（Hu et al., 2019）**：本文直接对比的基线模型，用于 HIV 整合位点预测。DeepHBV 在结构上加深了网络并引入 attention，性能优于 DeepHINT。在 TF–DNA 结合预测中，可参考此对比思路，将新模型与已有工具（如 DeepBind、DeepSEA）对比。

2. **DeepBind（Alipanahi et al., 2015）**：用 CNN 预测 TF–DNA 结合，是本文 CNN 架构的学术源头之一。DeepHBV 的贡献在于加入 attention 和基因组特征融合，这两点可迁移到 DeepBind 类模型中。

3. **DeepSEA（Zhou & Troyanskaya, 2015）**：用 CNN 预测染色质特征（含 TF 结合），与本文同属"序列 → 功能预测"范式。DeepSEA 的 multi-task 思路可与 DeepHBV 的特征融合策略互补。

4. **HOMER（Heinz et al., 2010）**：本文用于 TFBS 富集的工具，是基序发现的标准工具。在 TF–DNA 结合研究中，HOMER 的 known motif 和 de novo motif 分析是标配流程。

5. **HBV 整合与 HCC 研究（Sung et al., 2012; Zhao et al., 2016）**：本文的生物学背景。已知 HBV 整合倾向 TERT、MLL4 等基因，本文的 TFBS 富集结果（如 c-Myc、CLOCK）与此类研究互补，提示整合位点可能位于 TF 密集的增强子/启动子区域。

6. **Attention 机制在基因组学中的应用（e.g., Enformer, Avsec et al., 2021）**：本文是 attention 用于病毒整合预测的早期尝试。后续 Enformer 等模型将 attention 扩展到长程调控预测，可视为本文思路的延伸。

7. **[Analysis] 与 TF–DNA 结合机制的联系**：本文发现的 TFBS 富集（AR-halfsite、Arnt、Atf1、bHLHE40、bHLHE41、BMAL1、CLOCK、c-Myc 等）多为 bHLH 家族和核受体家族，这些 TF 在肝细胞中高表达且参与昼夜节律、代谢调控。提示 HBV 整合可能偏好"开放染色质 + TF 密集结合"的区域，这与真核 TF–DNA 结合需要染色质开放的基本机制一致。该假设可迁移到 TF–DNA 结合位点预测中：将染色质开放性特征（DNase-seq、ATAC-seq）作为模型输入，可能比纯序列模型更准确。

---

## 16 研究想法

> **Agent 生成的研究候选**

### 候选 1：TF–DNA 结合位点预测的 Attention-Guided Motif Discovery 框架
- **名称**：AGMD-TF（Attention-Guided Motif Discovery for TF–DNA Binding）
- **来源局限/观察**：DeepHBV 用 attention 权重定位关键区域后做 HOMER 富集，但该流程是"事后分析"，未将 motif 信息反馈到模型训练中。
- **核心假设**：将 attention 权重与 motif 扫描结果耦合，可同时提升预测精度和可解释性。
- **增量**：在 DeepHBV 架构基础上，增加一个 motif 正则化项——鼓励 attention 高权重区域与已知 TF motif 匹配位置对齐。
- **初步方法**：用 ChIP-seq 数据训练 CNN+attention 模型；在损失函数中加入 attention-motif 对齐损失；用 HOMER 验证新发现的 motif。
- **验证方式**：在 ENCODE TF ChIP-seq 数据集上对比有无 motif 正则化的 AUROC 和 motif 发现率。
- **创新状态**：unverified

### 候选 2：整合染色质可及性特征的 TF–DNA 结合预测模型
- **名称**：ChromTF（Chromatin-aware TF–DNA Binding Predictor）
- **来源局限/观察**：DeepHBV 加入 repeat/TCGA 特征后性能大幅提升，说明基因组环境特征对结合位点预测至关重要。TF–DNA 结合同样依赖染色质状态。
- **核心假设**：将 ATAC-seq/DNase-seq 峰作为附加通道并入序列模型，可显著提升 TF 结合位点预测精度。
- **增量**：将 DeepHBV 的特征融合策略迁移到 TF–DNA 结合预测，系统比较不同染色质特征（ATAC、DNase、H3K27ac、H3K4me3）的贡献。
- **初步方法**：用 ENCODE 数据构建"序列 + 染色质特征"双通道输入；训练 CNN 或 CNN+attention 模型；做消融实验评估各特征贡献。
- **验证方式**：在多个 TF 的 ChIP-seq 数据集上对比纯序列模型与 ChromTF 的 AUROC/AUPR。
- **创新状态**：partially checked（已有研究如 Basenji 用类似思路，但未系统比较特征组合）

### 候选 3：跨病毒整合位点预测的迁移学习
- **名称**：Viral-Integrate-Transfer
- **来源局限/观察**：DeepHBV 仅针对 HBV，且跨数据库泛化性能下降（VISDB AUROC 0.76）。不同病毒（HBV、HIV、HPV、AAV）整合机制可能共享部分特征。
- **核心假设**：用多病毒整合位点数据预训练，可提升单病毒预测的泛化性。
- **增量**：构建多病毒整合位点数据集，用预训练 + 微调策略训练模型。
- **初步方法**：收集 HBV、HIV、HPV、AAV 整合位点数据；用共享的 CNN+attention 架构预训练；在 HBV 数据上微调；对比直接训练 vs 迁移学习的性能。
- **验证方式**：在留出数据集上比较 AUROC，并分析 attention 区域是否富集共享的 TFBS。
- **创新状态**：unverified

### 候选 4：TF–DNA 结合机制的结构-序列联合建模
- **名称**：StructSeq-TF
- **来源局限/观察**：DeepHBV 仅用序列和基因组注释，未利用 3D 结构信息。TF–DNA 结合特异性由氨基酸-碱基接触决定，结构信息可提供正交约束。
- **核心假设**：将 AlphaFold 预测的 TF 结构 + DNA 序列共同编码，可提升结合位点预测精度，尤其在低同源性 TF 上。
- **增量**：在序列模型基础上，加入 TF 结构编码器（如 GNN），输出结构感知的嵌入向量。
- **初步方法**：用 AlphaFold 预测 TF 结构；用 GNN 编码结构；与序列 CNN 特征拼接；在 ChIP-seq 数据上训练。
- **验证方式**：对比纯序列模型与 StructSeq-TF 在多个 TF 上的 AUROC，重点关注结构域差异大的 TF。
- **创新状态**：unverified

### 候选 5：Attention 权重与 TF 结合机制的因果验证
- **名称**：ATT-Causal-TF
- **来源局限/观察**：DeepHBV 发现 attention 高权重区域富集 TFBS，但未验证这些区域是否真正驱动整合（因果性）。
- **核心假设**：attention 高权重区域中的 TFBS 是整合位点选择的因果驱动因素，而非伴随现象。
- **增量**：用 CRISPR 干扰（CRISPRi）或突变实验验证 attention 高权重区域的 TFBS 功能。
- **初步方法**：在肝癌细胞系中对 attention 高权重区域的候选 TFBS 做 CRISPRi 敲低；检测 HBV 整合频率变化。
- **验证方式**：比较野生型 vs 突变型细胞系的 HBV 整合频率；若 attention 区域被破坏后整合频率显著下降，则支持因果性。
- **创新状态**：unverified（需湿实验合作）