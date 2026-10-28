## 01 基本信息

- **标题**：Modeling chromatin state from sequence across angiosperms using recurrent convolutional neural networks
- **作者**：Wrightsman, Travis; Marand, Alexandre P; Crisp, Peter A; Springer, Nathan M; Buckler, Edward S
- **单位**：未提供（根据致谢推测含 USDA-ARS、康奈尔大学等，但原文未明确列出单位列表）
- **期刊/平台**：The Plant Genome
- **年份**：2022-08-05
- **论文类型**：研究论文（方法学 + 应用）
- **领域**：植物基因组学；染色质可及性预测；深度学习
- **关键词**：chromatin accessibility, DNA methylation, deep learning, DanQ, angiosperms, TF–DNA binding
- **DOI/arXiv**：10.1002/tpg2.20249
- **代码**：Zenodo 仓库（Wrightsman et al., 2021），具体链接未在摘要中给出
- **数据**：ATAC-seq 数据来自 NCBI GEO GSE128434；甲基化数据来自 Crisp et al. (2020) 及新测序数据（Supplemental Table S14）；玉米 scATAC-seq 数据来自 GSE155178
- **阅读日期**：2025-01-15（示例）
- **在该课题方向中的位置**：本文属于「序列 → 染色质状态」的深度学习预测模型，聚焦跨物种泛化。对 TF–DNA 互作课题的关联在于：(1) 使用 DanQ（CNN + BiLSTM）从序列直接预测染色质可及性，可及性区域富含 TF 结合位点；(2) 通过解释方法（TF-MoDISco、k-mer occlusion、pGIA）识别对模型预测重要的 TF 基序，直接关联 TF–DNA 结合特异性；(3) 跨物种训练策略为在缺少实验数据的物种中预测 TF 结合位点提供了可迁移框架。

---

## 02 一句话总结

本文训练 DanQ（CNN+BiLSTM）架构，利用 12 个被子植物物种的 ATAC-seq 和 10 个物种的甲基化数据，构建跨物种的染色质状态预测模型（a2z），发现跨物种模型性能与种内模型相当或更优，并通过多种解释方法识别出 TCP 和 AP2/ERF 等 TF 家族基序对模型预测最为重要。

---

## 03 研究问题

- **具体问题**：能否仅从 DNA 序列跨物种预测被子植物的染色质可及性（ACR）和 DNA 甲基化状态？哪些 TF 基序对模型预测贡献最大？
- **为什么重要**：ACR 是基因调控的关键元件，但实验测定成本高、物种特异性强。若能直接从序列预测，则可推广到任意被测序的被子植物基因组，加速非模式物种的调控元件注释和育种应用。
- **现有方法不足**：(1) 大多数深度学习方法仅在单物种内训练和测试（如人类），跨物种泛化能力未知；(2) 植物染色质重塑机制与动物不同，需要植物特异性模型；(3) 已有植物模型（如 CharPlant）未系统评估跨物种性能；(4) 模型解释不足，难以提取生物学可检验的 TF–DNA 结合假设。
- **精确研究问题**：Can a recurrent convolutional neural network trained on multiple angiosperm species predict chromatin accessibility and methylation state from DNA sequence in held-out angiosperm species with performance comparable to within-species models?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及引用，经外部核验部分已标注。

| 阶段 | 代表方法 | 优点 | 局限 | 本文位置 |
|------|----------|------|------|----------|
| 早期序列特征方法 | PWM/位置权重矩阵、k-mer 计数 | 可解释、计算快 | 无法捕捉长程依赖和复杂语法 | 本文用 bag-of-k-mers 作为基线 |
| 传统机器学习 | SVM、随机森林 + 手工特征 | 可解释 | 特征工程繁琐，性能有限 | 未直接使用 |
| 第一代深度学习 | DeepSEA (Zhou & Troyanskaya, 2015)、Basset (Kelley, 2020) | 端到端学习 motif 和语法 | 单物种训练；CNN 无法捕捉长程依赖 | 本文对比 Basset 和 DeeperDeepSEA |
| 循环+卷积混合 | DanQ (Quang & Xie, 2016) | BiLSTM 捕捉长程依赖 | 计算量大；原为人类设计 | **本文核心架构** |
| 植物特异性模型 | CharPlant (Zhao et al., 2021) | 针对植物优化 | 未系统评估跨物种 | 本文对比对象之一 |
| 跨物种建模 | **本文 a2z 模型** | 多物种联合训练，跨物种预测 | 仅覆盖 12 个物种的叶片组织 | **本文贡献** |
| 模型解释 | TF-MoDISco (Shrikumar et al., 2020)、GIA (Koo et al., 2021) | 识别重要 motif | 计算昂贵；结果需实验验证 | 本文组合使用多种解释方法 |

**本文主张的位置**：在「序列 → 染色质状态」预测中，首次系统评估跨被子植物物种的泛化能力，并证明多物种训练可替代或超越单物种模型，同时提供可解释的 TF 基序重要性排序。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 跨物种预测性能未知 | 大多数模型仅在单物种内训练/测试 | 缺乏多物种统一训练数据；物种间调控机制差异未知 | 引言："Many of these models have so far only been trained within a single species" |
| 植物染色质建模缺乏专用模型 | 植物 ACR 机制与动物不同 | 植物有独特的染色质重塑因子和转座子景观 | 引言："plant-specific chromatin accessibility models are likely to be necessary" |
| 深度学习数据需求大 | CNN 需要大量训练数据才能达到传统方法性能 | 单物种数据有限，尤其非模式植物 | 引言引用 Krützfeldt et al. (2020) |
| 模型解释困难 | 黑箱模型难以提取生物学假设 | 梯度方法噪声大；motif 简并性高 | 方法节：采用 occlusion 替代梯度方法，"trade longer computational times for reduced noise" |
| 细胞类型特异性预测差 | 叶片训练的模型难以预测组织特异性 ACR | 训练数据仅来自叶片；细胞类型特异性位点占比小 | Results 图 2：随细胞类型特异性增加，性能下降 |
| 转座子区域假阳性 | 大基因组中重复序列导致误报 | 转座子可能被误认为可及性信号 | Results：masking repeats 后 auPR 提升（ΔauPR 0.15） |

---

## 06 核心思想

### 1) 表面方法
- 使用 DanQ 架构（CNN 层 + BiLSTM 层 + 全连接输出层），以 600 bp DNA 序列为输入，预测中心区域是否为可及染色质（ACR）或未甲基化区域。
- 训练策略：跨物种模型（leave-one-species-out）与种内模型对比。
- 解释方法：TF-MoDISco 发现 motif → k-mer occlusion 量化效应 → pGIA 定位 motif 位置效应 → FIMO 匹配 JASPAR 数据库。

### 2) 核心洞察
- **跨物种训练的有效性**：多物种联合训练不仅没有稀释信号，反而通过增加进化多样性减少了中性变异对学习的干扰，使模型学到更保守的调控语法。
- **可及性 vs 甲基化的不同基序偏好**：两种染色质状态的模型识别出不同的 TF 家族，说明二者由不同的调控逻辑驱动。
- **位置效应**：TF 基序对模型预测的贡献随其在窗口中的位置变化（锯齿状模式），提示模型学到了核小体/螺旋周期等结构约束。

### 3) 可能的普适教训 [Analysis]
- 对 TF–DNA 互作课题：跨物种训练是提升模型泛化和 motif 发现能力的通用策略——进化保守的 TF 结合位点在多物种比对中信号更强。
- 解释方法的选择：occlusion 类方法虽计算昂贵，但在 motif 效应量估计上比梯度方法更稳健，适合 TF 结合位点这类简并序列特征。
- 训练数据平衡策略（按物种、距离类别、染色质状态）直接影响模型在不同基因组区域的泛化能力，这对 TF 结合预测同样关键。

---

## 07 方法总览

- **输入**：600 bp DNA 序列（one-hot 编码，N 编码为等概率向量）
- **输出**：二分类概率——中心 200 bp 是否为 ACR（可及）或未甲基化区域
- **模型架构**：DanQ = 1 层 CNN（motif 检测）→ BiLSTM（语法/长程依赖）→ 全连接 → sigmoid
- **训练数据**：
  - ATAC-seq：12 个被子植物物种（拟南芥、盐芥、菜豆、大豆、短柄草、水稻、谷子、杨树、高粱、玉米、大麦、芦笋）
  - 甲基化：10 个物种（含 5 个已发表禾本科 + 5 个新测序）
  - 每物种 26,280（ATAC）/ 35,652（甲基化）训练区域，正负样本平衡
- **训练策略**：
  - 跨物种模型：每次留出一个物种作为测试，其余 11 个物种训练
  - 种内模型：单物种训练，同物种留出染色体测试
  - 对比架构：Basset、CharPlant、DeeperDeepSEA
- **评估指标**：auPR（主要）、auROC（辅助）
- **解释方法**：
  - TF-MoDISco：从 CNN 卷积核中提取 motif
  - k-mer occlusion：滑动 10 bp 掩码，测量预测变化
  - pGIA：在 1,000 个随机背景序列上嵌入 JASPAR motif，测量位置效应
  - FIMO：将高效应 k-mer 匹配到 JASPAR 2020 CORE Plantae（530 个 motif）
- **反馈回路**：无显式主动学习或迭代优化；模型训练后固定，仅解释阶段迭代
- **工具**：Keras + TensorFlow；conda 环境管理；GNU coreutils、gawk、bedtools 用于区间操作；BioPython/pyfaidx 提取序列

**文字流程**：
1. 从各物种基因组中提取 ACR/未甲基化区域中心，扩展至 600 bp
2. 随机采样非 ACR/甲基化区域作为负样本
3. One-hot 编码序列 → DanQ 前向传播 → 二分类输出
4. 跨物种训练（留一法）或种内训练（留一染色体）
5. 在测试集上计算 auPR/auROC
6. 对训练好的模型运行 TF-MoDISco 提取 motif
7. 对测试集序列运行 k-mer occlusion 计算每个 10-mer 的效应量
8. 对 JASPAR motif 运行 pGIA 获得位置-效应曲线
9. FIMO 匹配高效应 k-mer 到已知 TF 基序

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CNN 卷积层 | 检测序列 motif（TF 结合位点） | 捕获局部序列模式，类似 PWM 扫描 | 输入：600 bp one-hot；输出：motif 激活图 | DanQ 优于 bag-of-k-mers（Supplemental Fig S3） | 失去 motif 检测能力，模型退化为纯序列组成模型 [预期] |
| BiLSTM 层 | 建模 motif 间的长程依赖和语法 | TF 协同结合、核小体定位等需要上下文 | 输入：CNN 特征序列；输出：上下文向量 | DanQ 优于纯 CNN 架构（Basset、DeeperDeepSEA）（Supplemental Fig S5） | 失去长程依赖建模，跨物种泛化能力下降 [预期] |
| 全连接输出层 | 二分类决策 | 将高维特征映射到类别概率 | 输入：BiLSTM 输出；输出：P(ACR) | 标准分类头，无特殊设计 | 替换为线性分类器可能降低性能 [预期] |
| 跨物种训练策略 | 利用多物种数据提升泛化 | 增加进化多样性，减少中性变异干扰 | 输入：12 物种训练数据；输出：通用模型 | 跨物种 auPR ≥ 种内 auPR（Fig 1） | 退回单物种训练则无法预测未观测物种 [实测对比] |
| 距离类别平衡 | 平衡 genic/proximal/distal 样本 | 不同距离类别的 ACR 密度差异大 | 输入：原始样本；输出：平衡后训练集 | 距离类别间性能差异显著（Fig 1 bottom left） | 不平衡训练导致 distal 区域预测偏差 [预期] |
| TF-MoDISco | 从卷积核提取可解释 motif | 将黑箱模型转化为生物学假设 | 输入：CNN 权重+测试序列；输出：motif 矩阵 | 定性识别出多个已知 TF 家族（Supplemental Fig S11） | 无法获得 motif 级解释 [预期] |
| k-mer occlusion | 量化每个 10-mer 对预测的贡献 | 获得基序级效应量排序 | 输入：测试序列+模型；输出：效应量分布 | 20-40% 高效应 k-mer 匹配 JASPAR（Supplemental Fig S12） | 无法区分 motif 间相对重要性 [预期] |
| pGIA | 定位 motif 在窗口中的位置效应 | 检测位置依赖的调控逻辑 | 输入：JASPAR motif+背景序列；输出：位置-效应曲线 | 观察到锯齿状模式（Fig 4） | 无法检测位置效应 [预期] |
| 重复序列掩蔽（两步模型） | 降低转座子假阳性 | 大基因组中 TE 干扰预测 | 输入：模型预测+RepeatMasker 注释；输出：掩蔽后预测 | ΔauPR 0.15（accessibility）（Supplemental Fig S8） | 假阳性率升高 [实测] |

---

## 09 关键公式符号

本文未提供显式数学公式。以下为方法中隐含的关键概念：

| 符号/概念 | 含义 | 用途 | 来源 |
|-----------|------|------|------|
| one-hot 编码 | 将 DNA 序列表示为 4×L 二进制矩阵 | CNN 输入 | Methods: Training data preprocessing |
| N 编码 | N 位置分配等概率向量 [0.25, 0.25, 0.25, 0.25] | 处理缺失碱基 | Methods: "The Ns were encoded as vectors with equal probability assigned to each base" |
| auPR | Area under Precision-Recall curve | 主要性能指标（类别不平衡下更稳健） | Methods: Training and evaluating models |
| auROC | Area under ROC curve | 辅助性能指标 | Methods: Training and evaluating models |
| ΔauPR | 掩蔽前后 auPR 差值 | 量化重复序列对预测的贡献 | Results: ΔauPR 0.15 for accessibility |
| k-mer effect size | 掩蔽 k-mer 前后预测概率之差 | 量化序列基序重要性 | Methods: k-mer occlusion |
| global importance | 嵌入 motif 前后预测概率之差的平均 | 量化 TF 基序对模型的重要性 | Methods: GIA |
| 阈值 q < 0.05 | FIMO 匹配显著性阈值 | 将 k-mer 匹配到 JASPAR motif | Methods: FIMO |

---

## 10 实验设计与证据链

### 数据集与设置
- **ATAC-seq 训练数据**：12 个被子植物物种，每物种 26,280 个训练区域（正负各半），共 315,360 区域
- **甲基化训练数据**：10 个物种，每物种 35,652 区域，共 356,520 区域
- **测试协议**：
  - 跨物种：留一物种法（12 折）
  - 种内：留一染色体法
- **外部测试**：酵母（酿酒酵母）和人类 GM12878 细胞系 ATAC-seq
- **玉米多组织测试**：6 个器官的 scATAC-seq（GSE155178）
- **基线**：bag-of-k-mers 模型
- **对比架构**：Basset、CharPlant、DeeperDeepSEA
- **重复次数**：每个模型训练 3 次取均值（估计变异性）
- **窗口大小**：600 bp（对比 300、1000 bp 后选定）

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 跨物种 vs 种内性能 | 跨物种训练不劣于种内训练 | 12 折留一物种 vs 单物种留一染色体 | 跨物种 auPR ≥ 种内 auPR（多数物种） | 染色质调控机制在被子植物中保守 | 不能证明跨物种模型优于所有单物种模型 | Results 图 1 |
| 架构对比 | DanQ 优于纯 CNN | DanQ vs Basset/CharPlant/DeeperDeepSEA，相同数据 | DanQ 在多数留出物种上 auPR 最高 | BiLSTM 层对跨物种泛化有贡献 | 未做统计显著性检验 | Supplemental Fig S5 |
| 距离类别分析 | 模型在 genic 区域表现最好 | genic vs proximal vs distal 分层评估 | genic > proximal > distal | 训练数据中 genic ACR 占比高 | 不能区分是数据偏差还是生物学差异 | Results 图 1 bottom left |
| 酵母/人类测试 | 植物模型对远缘物种有预测能力 | 玉米留出模型预测酵母/人类 ATAC | 酵母 auPR 0.21，人类 auPR 0.02 | 部分染色质机制跨真核生物保守 | 人类预测能力极弱，不能推广到动物 | Supplemental Fig S9 |
| 重复掩蔽 | 转座子导致假阳性 | 掩蔽重复区域前后对比 | ΔauPR 0.15（accessibility） | 重复序列是主要假阳性来源 | 未分析具体 TE 家族 | Supplemental Fig S8 |
| 多组织 scATAC | 模型预测组成型 ACR 更好 | 按细胞类型特异性分层 | 广谱可及区域预测好，特异性区域差 | 训练数据以叶片为主，限制细胞类型泛化 | 未测试其他组织训练效果 | Results 图 2 |
| TF-MoDISco motif 发现 | 模型学到已知 TF 基序 | 与 JASPAR 数据库匹配 | 识别出 TCP、AP2/ERF 等家族 | 模型学到生物学真实的 motif | 未验证新发现的 motif 功能 | Results: Interpretation |
| k-mer occlusion 与 JASPAR 匹配 | 高效应 k-mer 富集已知 TF 基序 | 20-40% 高效应 k-mer 匹配 JASPAR | 匹配率因物种和特征而异 | 模型依赖已知 TF 结合位点 | 60-80% 高效应 k-mer 未匹配，可能为未知 motif | Supplemental Fig S12 |
| pGIA 位置效应 | TF 基序位置影响模型预测 | 在 1,000 个随机背景上嵌入 motif | 观察到锯齿状位置效应模式 | 模型学到核小体/螺旋周期结构约束 | 未与实验数据（如 MNase-seq）直接对比 | Results 图 4 |

---

## 11 结论正确解读

### 任务范围
- 仅预测**叶片组织**的染色质可及性和甲基化状态，不覆盖其他组织/发育阶段
- 仅覆盖 12 个被子植物物种，主要为作物和模式植物
- 预测窗口为 600 bp，分辨率有限（~200 bp 中心区域）

### Oracle/真值输入
- 训练标签来自实验测定的 ATAC-seq peaks 和未甲基化区域，属于实验真值，非模拟数据
- 但 peaks 的 calling 依赖保守阈值，可能遗漏低置信度但真实的 ACR

### 端到端状态
- 是端到端模型：输入原始序列 → 输出染色质状态，无需中间特征
- 但解释阶段（motif 识别）是后处理，不参与训练

### 算力成本
- 未提供具体训练时间/GPU 配置
- 12 物种 × 26,280 序列 × 600 bp 的规模对现代 GPU 可承受

### 历史数据依赖
- 依赖当前参考基因组组装质量；组装不完整的物种可能影响预测
- 训练数据来自已发表数据集，存在实验批次效应

### 模型依赖
- 仅测试了 DanQ 架构；其他架构（如 Transformer）可能表现不同
- 未做超参数敏感性分析

### 最难情形
- 细胞类型特异性 ACR（scATAC 测试中表现最差）
- 远端/基因间区域（distal 表现最差）
- 大基因组物种（如玉米）中重复序列干扰

### 群体/领域边界
- 仅被子植物；对裸子植物、蕨类等未验证
- 仅叶片组织；根、花、果实等未覆盖

### 不确定性
- 模型预测的置信度未校准，不能直接解释为概率
- motif 重要性排序是计算推断，未经实验验证（如 CRISPR 突变）

### 有边界的复述
本文证明：在 12 个被子植物物种的叶片 ATAC-seq 数据上，跨物种训练的 DanQ 模型能够以与单物种模型相当或更优的 auPR 预测留出物种的染色质可及性；该模型对组成型 ACR 的预测优于细胞类型特异性 ACR；通过 k-mer occlusion 和 pGIA 识别出的高重要性基序富集于 TCP 和 AP2/ERF 家族。这些结论仅适用于叶片组织、被子植物范围内，且 motif 发现未经湿实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 单组织训练 | 模型仅基于叶片数据训练，难以预测其他组织的染色质状态 | 收集多组织数据训练通用模型 | Discussion: "Future work looking at ways to balance or weight observations in rarer peak classes would likely improve the generalizability" |
| 细胞类型特异性预测差 | scATAC 测试中，特异性 ACR 预测性能显著下降 | 需要更多细胞类型分辨率的数据 | Results 图 2 讨论 |
| 缺乏 trans 信息 | 模型仅使用 cis 序列，无法解释 trans 因子（如染色质重塑复合物）的贡献 | 整合 trans 因子表达数据 | Discussion: "Model architectures that can effectively incorporate trans factors... will likely surpass current methods" |
| 重复序列假阳性 | 大基因组中 TE 导致误报 | 重复掩蔽两步策略 | Results: "two-step repeat-masked models do much better" |
| JASPAR 数据库覆盖不全 | 仅 530 个植物 motif，远低于估计的 ~1,500 个 TF 基因 | 需要更全面的 motif 数据库 | Discussion: "there are only 530 motifs in the database... critical TFs may still be missing" |
| 解释方法计算昂贵 | k-mer occlusion 和 pGIA 需要大量前向传播 | 未提出具体改进方向 | Methods: "trade longer computational times for reduced noise" |
| 跨物种外推有限 | 对酵母有一定预测能力，但对人类几乎无效 | 未明确讨论 | Supplemental Fig S9 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 跨物种模型与种内模型性能"相当" | 可能因为 12 个物种中多数是近缘物种（禾本科占 5/12），跨物种增益被高估 | 若仅对近缘物种有效，则"跨被子植物"的结论过于宽泛 | 按系统发育距离分层分析性能；增加远缘物种（如木兰类）测试 | Results 图 1 物种列表 |
| 锯齿状 pGIA 模式归因于核小体/螺旋周期 | 也可能是 BiLSTM 的序列位置编码偏差或训练数据中 peak 中心对齐造成的伪影 | 若为伪影，则 motif 位置效应的生物学解释不成立 | 用随机序列对照；用核小体定位实验数据（MNase-seq）验证 | Results 图 4 讨论 |
| k-mer occlusion 中 60-80% 高效应 k-mer 未匹配 JASPAR | 可能包含未知 motif，也可能是模型学到的非特异性序列偏好（如 GC 含量） | 若为后者，则 motif 发现结论需打折 | 对未匹配 k-mer 做 GC 含量/序列组成分析；用饱和突变验证 | Supplemental Fig S12 |
| 跨物种模型在酵母中有一定预测能力 | 可能因为酵母基因组小、TE 少，假阳性率天然低，而非真正的跨真核保守机制 | 不能作为"跨真核保守"的证据 | 在更多远缘真核生物（如昆虫、鱼）上测试 | Supplemental Fig S9 |
| 训练数据中正负样本按物种平衡 | 但未按系统发育关系平衡，近缘物种可能造成数据泄漏 | 可能高估跨物种泛化能力 | 按物种亲缘关系聚类交叉验证 | Methods: Training data preprocessing |
| 仅使用 auPR/auROC 评估 | 未报告校准误差或阈值依赖指标 | 实际应用中需要校准的概率输出 | 增加 expected calibration error 等指标 | Methods: Training and evaluating models |
| 未与最新方法对比 | 对比对象为 2015-2020 年方法；未与 Enformer、Borzoi 等更新架构比较 | 无法判断当前最优水平 | 在相同数据上复现并对比新架构 | Results 图 1, Supplemental Fig S5 |
| 解释方法仅关注 motif 本身 | 未分析 motif 间的协同/拮抗相互作用 | TF 结合是组合性的，单 motif 分析可能遗漏关键机制 | 使用更高的交互项或注意力分析 | Discussion 未涉及 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

### 可迁移概念

1. **跨物种训练策略**：将多个物种数据联合训练，通过增加进化多样性减少中性变异干扰，可提升模型在未观测物种上的泛化能力。→ 迁移到 TF–DNA 结合预测：可联合多个物种的 ChIP-seq/HT-SELEX 数据训练通用 TF 结合模型，尤其对缺少实验数据的非模式物种。

2. **Leave-one-species-out 评估协议**：严格评估跨物种泛化的标准方法。→ 迁移：评估 TF 结合模型时，按物种留出而非随机划分，避免近缘序列泄漏。

3. **k-mer occlusion 方法**：通过掩蔽滑动窗口测量预测变化，获得基序级效应量。→ 迁移：可用于量化任意 TF 结合模型中每个 k-mer 对预测的贡献，比梯度方法更稳健。

4. **pGIA（positional global importance analysis）**：在随机背景上嵌入 motif 并测量位置效应。→ 迁移：可用于检测 TF 结合模型是否学到位置依赖的调控逻辑（如距离 TSS 的偏好、核小体相位）。

5. **两步重复掩蔽策略**：对预测结果按重复序列注释进行后处理，可显著降低假阳性。→ 迁移：TF 结合预测中，转座子插入的假结合位点可通过类似策略过滤。

6. **多解释方法组合**：TF-MoDISco（发现）+ occlusion（量化）+ pGIA（定位）+ FIMO（注释）的组合流程。→ 迁移：为 TF–DNA 互作模型的解释提供完整方法论模板。

7. **距离类别分层评估**：按 genic/proximal/distal 分层报告性能，揭示模型在不同基因组区域的适用边界。→ 迁移：TF 结合预测应区分启动子/增强子/异染色质区域分别评估。

### 可迁移方法

- **DanQ 架构**（CNN + BiLSTM）：CNN 捕获 motif，BiLSTM 捕获 motif 间长程依赖。→ 迁移：TF 结合位点预测中，BiLSTM 层可建模多个 TF 协同结合的语法。

- **数据平衡策略**：按物种、距离类别、染色质状态平衡训练数据。→ 迁移：TF 结合训练数据中，正负样本应按基因组特征分层采样。

- **JASPAR motif 匹配流程**：FIMO + q-value 阈值。→ 迁移：将模型学到的 motif 与已知 TF 基序数据库匹配，快速获得生物学注释。

### 对 TF–DNA 互作课题的具体启示

- 本文识别的 TCP 和 AP2/ERF 家族在染色质可及性预测中重要性最高，提示这些 TF 可能是被子植物染色质开放的通用调控因子，值得在 TF–DNA 结合实验中优先验证。
- 甲基化模型与可及性模型识别出不同的 motif 集合，说明两种染色质状态由不同的 TF 网络驱动，TF 结合预测应区分染色质上下文。
- 锯齿状位置效应模式提示 TF 结合位点的螺旋周期定位（~10 bp 周期）可能被模型隐式学习，这为从序列预测 TF 结合位点的空间约束提供了线索。

---

## 15 与已有知识连接

### 可核验的外部连接

1. **DanQ 原始论文**：Quang & Xie (2016), "DanQ: a hybrid convolutional and recurrent deep neural network for quantifying the function of DNA sequences", Nucleic Acids Research。本文直接使用该架构，可对比原始人类模型与本文植物模型的性能差异。

2. **DeepSEA**：Zhou & Troyanskaya (2015), Nature Methods。本文对比的架构之一，代表纯 CNN 方法。

3. **Basset**：Kelley (2020), PLoS Computational Biology。本文对比的架构之一，同样为 CNN 方法。

4. **ATAC-seq 数据来源**：Lu et al. (2019), 12 个被子植物物种的叶片 ATAC-seq 数据。可交叉验证本文使用的训练数据质量。

5. **甲基化数据**：Crisp et al. (2020), 禾本科植物未甲基化区域数据。本文扩展了该数据到非禾本科物种。

6. **JASPAR 2020 CORE Plantae**：Fornes et al. (2019), Nucleic Acids Research。本文使用的 motif 数据库，包含 530 个植物 TF 基序。

7. **TF-MoDISco**：Shrikumar et al. (2020), Bioinformatics。本文使用的 motif 发现工具。

8. **GIA**：Koo et al. (2021), "Global importance analysis: An interpretability method to quantify importance of genomic features", Bioinformatics。本文使用的解释方法。

9. **玉米 scATAC-seq**：Marand et al. (2021), 多组织单细胞染色质可及性图谱。本文用于评估细胞类型特异性预测。

10. **CharPlant**：Zhao et al. (2021), 植物染色质状态预测的 CNN 模型。本文对比的植物专用模型。

### 与 TF–DNA 互作课题的连接

- 本文的 motif 重要性排序可作为 TF–DNA 结合预测模型的先验特征权重。
- 跨物种训练策略与系统发育比较方法（如 PhyloGWAS）互补：前者从序列直接学习，后者从多序列比对推断保守性。
- 本文识别的 TCP/AP2/ERF 基序可链接到 PlantTFDB 等 TF 数据库进行功能注释。
- 锯齿状位置效应与已知的核小体 DNA 弯曲周期性（~10.5 bp）一致，可链接到 DNA 结构预测文献（如 DNAshape）。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：跨物种 TF–DNA 结合预测模型

- **名称**：PhyloTF-Bind：跨被子植物物种的 TF 结合位点通用预测器
- **来源局限/观察**：本文证明染色质可及性可跨物种预测，但未直接预测 TF 结合。现有 TF 结合模型（如 DeepBind、DeepSEA）多为单物种训练，跨物种泛化未知。
- **核心假设**：TF 结合位点的序列偏好（motif）在被子植物中高度保守，跨物种训练可提升未观测物种的预测性能。
- **初步方法**：收集多个物种的 ChIP-seq/HT-SELEX 数据，采用 DanQ 或 Enformer 架构，leave-one-species-out 评估；结合本文的 k-mer occlusion 和 pGIA 进行解释。
- **验证方式**：在留出物种的 ChIP-seq 数据上评估 auPR；与单物种模型对比；用已知 TF 突变实验验证 motif 重要性排序。
- **创新状态**：unverified

### 候选 2：TF 基序位置效应的结构解释

- **名称**：Helical-Fingerprint：从深度学习模型提取 TF 结合位点的 DNA 结构偏好
- **来源局限/观察**：本文观察到 pGIA 的锯齿状模式但未深入解释。已知 TF 结合受 DNA 形状（螺旋周期、小沟宽度）影响。
- **核心假设**：锯齿状位置效应模式反映模型学到了 DNA 螺旋周期（~10.5 bp）对 TF 结合的结构约束。
- **初步方法**：将 pGIA 位置效应曲线与 DNAshape 预测的螺旋参数（螺旋扭角、小沟宽度）做相关分析；用模拟的周期性序列验证模型响应。
- **验证方式**：位置效应曲线的傅里叶分析检测 ~10.5 bp 周期；与实验核小体定位数据（MNase-seq）对比。
- **创新状态**：unverified

### 候选 3：转座子插入对 TF 结合预测的干扰建模

- **名称**：TE-Aware：整合转座子注释的 TF 结合预测框架
- **来源局限/观察**：本文发现重复序列掩蔽可提升预测精度（ΔauPR 0.15），但未建模 TE 的调控功能。TE 可携带或破坏 TF 结合位点。
- **核心假设**：TE 插入是 TF 结合预测的主要噪声源，显式建模 TE 状态可提升预测精度。
- **初步方法**：在输入序列中附加 TE 注释通道（one-hot 或 embedding），训练多任务模型同时预测 TF 结合和 TE 状态；对比掩蔽策略。
- **验证方式**：在玉米等 TE 丰富物种中评估 auPR 提升；分析模型对 TE 内部 vs 侧翼序列的注意力权重。
- **创新状态**：unverified

### 候选 4：从染色质可及性反推 TF 协同规则

- **名称**：CoBind-Infer：从跨物种 ACR 预测中推断 TF 协同结合语法
- **来源局限/观察**：本文模型预测 ACR 但未分析 TF 间的协同/拮抗关系。已知增强子功能依赖多个 TF 的协同结合。
- **核心假设**：跨物种 ACR 预测模型的内部表示编码了 TF 协同结合的语法规则，可通过解释方法提取。
- **初步方法**：对模型进行高阶解释（如 SHAP 交互项、注意力头分析），提取共现 motif 对；用 DNA 亲和纯化（DAP-seq）数据验证预测的协同关系。
- **验证方式**：预测的 TF 对共现频率与实验 ChIP-seq 共结合数据对比；用 motif 置换实验验证协同必要性。
- **创新状态**：unverified

### 候选 5：单细胞分辨率下的跨物种染色质状态预测

- **名称**：scAngio-Atlas：跨物种单细胞染色质可及性预测模型
- **来源局限/观察**：本文仅使用 bulk ATAC-seq 训练，但用 scATAC-seq 评估，发现细胞类型特异性预测差。单细胞数据可提供更高分辨率。
- **核心假设**：在单细胞 ATAC-seq 数据上训练可捕获细胞类型特异的调控语法，提升特异性 ACR 的预测。
- **初步方法**：使用多个物种的 scATAC-seq 数据，将细胞类型作为辅助标签，训练多任务模型；评估跨物种、跨细胞类型的泛化。
- **验证方式**：在留出物种的 scATAC-seq 上评估；与 bulk 训练模型对比细胞类型特异性预测。
- **创新状态**：unverified