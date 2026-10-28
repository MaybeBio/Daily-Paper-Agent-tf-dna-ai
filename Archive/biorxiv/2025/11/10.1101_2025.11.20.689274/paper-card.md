## 01 基本信息

- **标题**：Dissecting sequence determinants of DNA methylation and in silico perturbation
- **作者**：Chen F; Zhang Q; Zhu S; Liang J; Zhong S; Zhang Z; Su J; Guo Y; Fan X; Zhang Y; Yu F
- **单位**：未提供（通讯作者 Yu F 所属实验室，Yu-Lab-Genomics）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2025
- **论文类型**：预印本（方法学 + 机制发现）
- **领域**：表观基因组学 × 深度学习（DNA 甲基化预测与可解释性）
- **关键词**：DNA methylation, deep learning, transcription factor motifs, cis-regulatory elements, in silico perturbation, mQTL, GWAS
- **DOI/arXiv 号**：10.1101/2025.11.20.689274
- **代码**：https://github.com/Yu-Lab-Genomics/MethylAI
- **数据**：1,900 个 WGBS 样本（12 物种，含 1,574 个人类样本，52 组织，238 细胞类型）；eGTEx mQTL 数据；GWAS Catalog 数据；ENCODE ChIP-seq 数据
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文聚焦 DNA 甲基化（而非 TF–DNA 结合本身），但其核心方法——序列→甲基化状态的深度学习预测 + 核苷酸级 attribution 解析 TF motif 贡献 + in silico 扰动验证——为「TF–DNA 结合机制 × AI」提供了可直接迁移的范式：将 TF motif 视为序列特征，通过 attribution 量化其对表观遗传输出的因果贡献，并以实验（CRISPR 敲除）验证预测。对 TF–DNA 结合课题的启示在于：attribution 方法可迁移至 TF 结合位点预测、motif 活性定量、以及变异效应（variant effect）的功能注释。

---

## 02 一句话总结

本文提出 MethylAI——一个跨物种预训练 + 人类特化的深度学习框架，直接从基因组序列预测单 CpG 甲基化状态（测试集平均 PCC = 0.875），通过 DeepSHAP 核苷酸级 attribution 识别出对甲基化有因果贡献的 TF motif（如 CTCF、GATA、AP-1 家族），并用 CRISPR 敲除实验验证了 in silico 扰动预测的甲基化变化（PCC = 0.859–0.861），最终将变异映射到组织特异活性 motif 上以解释复杂性状关联。

## 03 研究问题

- **具体问题**：基因组序列中哪些序列特征（特别是 TF 结合 motif）决定 DNA 甲基化的建立与维持？能否通过深度学习模型实现可解释的、可扰动的序列→甲基化映射？
- **为什么重要**：DNA 甲基化是细胞身份和基因调控的核心表观遗传标记，但其序列编码规则（"methylation grammar"）长期未被系统解析。理解这一规则对发育、疾病（癌症、衰老）和表观遗传工程至关重要。
- **现有方法不足**：传统方法依赖 CpG 密度、GC 含量等粗粒度特征，无法捕捉 TF motif 的精细贡献；已有深度学习模型（如 INTERACT、HyenaDNA）预测精度有限，且缺乏核苷酸级可解释性和实验验证。
- **精确研究问题**：Can a cross-species-pretrained deep learning model, combined with nucleotide-level attribution, identify TF motifs that causally regulate DNA methylation, and can its in silico perturbation predictions be validated experimentally?

## 04 背景与发展脉络

*注：以下脉络基于本文 Introduction 与 Results 的叙述，属「仅本文框架」，未经外部系统核验。*

1. **经典阶段（CpG 密度/GC 含量）**：早期研究确立 CpG 岛概念，认为 CpG 密度和 GC 含量是甲基化的主要序列决定因素。局限：无法解释组织特异性甲基化差异和 TF 的主动调控作用。
2. **统计关联阶段（mQTL）**：通过大规模群体甲基化 QTL 定位，发现遗传变异与甲基化水平的关联。局限：仅覆盖已测量位点，无法外推至未观测变异，缺乏机制解释。
3. **深度学习预测阶段（INTERACT、HyenaDNA 等）**：利用 CNN/Transformer 架构从序列预测甲基化。局限：预测精度有限，缺乏核苷酸级可解释性，未系统解析 TF motif 贡献。
4. **本文位置（可解释深度学习 + 实验验证）**：MethylAI 通过跨物种预训练提升泛化能力，结合 DeepSHAP attribution 实现核苷酸级解释，并通过 CRISPR 敲除和 in silico 扰动建立因果验证闭环。主张：序列→甲基化的映射可被分解为可解释的 TF motif 规则，且这些规则具有跨组织、跨物种的保守性。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 序列特征与甲基化的关系仅被粗粒度描述 | CpG 密度、GC 含量只能解释部分甲基化变异 | 缺乏对 TF motif 等精细序列特征的系统量化 | Results 节 "The sequence composition and patterns contributing to the methylation"：19.5% 的 TF motif 比 CpG 二核苷酸更具信息量 |
| 现有模型预测精度不足 | INTERACT 平均 PCC = 0.813，HyenaDNA = 0.828，低于 MethylAI 的 0.875 | 缺乏跨物种预训练和任务特化微调 | Results 图 1d、Extended Data 图 3 |
| 深度学习模型缺乏可解释性 | 无法定位哪些核苷酸/基序驱动预测 | 标准 CNN/Transformer 不提供核苷酸级归因 | Methods "Sequence attribution score and motif analysis"：采用 DeepSHAP 计算每个核苷酸的边际贡献 |
| 预测缺乏实验验证 | 多数模型仅做计算评估 | 缺乏 CRISPR 扰动实验与预测对照 | Results "Experimental validation"：CTCF 敲除后甲基化变化与预测 PCC = 0.859–0.861 |
| 遗传变异效应难以机制化解释 | mQTL 关联缺乏功能注释 | 无法将变异映射到具体 TF motif 的破坏/增强 | Results "MethylAI predicts genetic effects on DNA methylation"：活性 motif 区域变异方向预测准确率 87.0–89.8% |

## 06 核心思想

**1) 表面方法**：
- 构建跨物种（12 物种，1,900 WGBS 样本）预训练 + 人类数据微调的深度学习模型，输入 18,432 bp 单 CpG 中心序列，输出 5 个甲基化指标（raw site、smoothed site、200/500/1000 bp 区域水平）。
- 使用 DeepSHAP 计算每个输入核苷酸的 attribution score，聚合到 TF motif 水平定义 motif attribution score 和 motif activation score (MAS)。
- 通过 in silico 变异替换和 motif 删除模拟扰动，预测甲基化变化。
- 用 CRISPR/Cas9 敲除 CTCF 和删除 TRMU 基因内 CTCF motif 进行实验验证。

**2) 核心洞察**：
- 序列对甲基化的影响可被分解为可解释的 TF motif 贡献，且这些贡献超越 CpG 组成本身——即 TF 结合基序是甲基化调控的独立序列特征。
- 跨物种预训练捕获了进化保守的甲基化调控规则，使人类特化模型在小样本组织上仍能保持高精度。
- Attribution 分数与实验扰动结果高度一致，说明模型学到的不是表面关联，而是因果性的序列→甲基化规则。

**3) 可能的普适教训 [Analysis]**：
- 对 TF–DNA 结合课题：attribution 方法（DeepSHAP）可直接迁移至 TF 结合位点预测模型，用于量化每个核苷酸对结合亲和力的贡献，识别"核心接触位点"与"辅助位点"。
- 跨物种预训练策略适用于 TF–DNA 结合模型：TF 结合机制在进化中高度保守，跨物种预训练可提升人类数据的泛化能力。
- in silico 扰动 + 实验验证的闭环设计是建立因果性的关键，值得在 TF–DNA 结合研究中复制。

## 07 方法总览

- **输入**：18,432 bp 单 CpG 中心 DNA 序列（one-hot 编码，A/T/G/C），来自 12 物种参考基因组。
- **输出**：5 个甲基化指标——raw site methylation、smoothed site methylation、200 bp / 500 bp / 1,000 bp 区域平均甲基化水平。
- **模型架构**：输入块（卷积 + 物种特异 batch normalization + ELU）→ 6 个多尺度卷积块（每个含两个残差连接的卷积子块，不同 kernel size 捕获不同尺度特征）→ 物种特异输出头（自适应平均池化 + 线性层 + ELU + 线性层 + sigmoid）。
- **训练策略**：
  - 预训练：12 物种数据，物种特异 batch normalization 和输出头，共享卷积骨干。
  - 微调：人类数据（1,574 样本），生成 4 个特化模型（全人类、ENCODE、人类图谱、HEK-293T）。
  - 损失函数：smoothed site 和区域水平用 MSE，raw site 用 Huber loss；低覆盖度位点损失置零。
  - 优化器：AdamW，学习率 6×10⁻⁴（预训练）/ 1×10⁻⁴（微调），batch size 300（6 GPU × 50）。
- **可解释性模块**：DeepSHAP 计算核苷酸级 attribution → 聚合到 JASPAR TF motif 位点（match score > 400，p < 1×10⁻⁴）→ motif attribution score = 位点内所有核苷酸 attribution 绝对值的均值 → MAS = motif match score × motif attribution score。
- **in silico 扰动**：变异替换（reference → alternative allele）和 motif 删除（替换为空串后重新定中心），计算 Δmethylation = alt − ref 或 KO − control。
- **实验验证**：CRISPR/Cas9 敲除 CTCF（LentiCRISPR-v2 载体，sgRNA 靶向 CTCF 外显子），WGBS 测序（30×），比较敲除前后甲基化变化与模型预测。
- **下游分析**：mQTL 方向预测（eGTEx 7 组织）、GWAS 变异富集分析（52 组织活性 motif）、进化保守性分析（470 哺乳动物 phyloP）。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 跨物种预训练 | 在 12 物种 1,900 样本上学习保守的甲基化序列规则 | 人类数据有限，跨物种信息可提升泛化 | 输入：12 物种 CpG 序列；输出：各物种甲基化预测 | Extended Data 图 4：预训练是性能主导因素，优于仅人类训练 | [预期] 移除后人类测试集 PCC 显著下降（作者称预训练为"dominant performance determinant"） |
| 多尺度卷积块 | 在不同感受野下提取序列特征（局部 motif 与远端调控） | 甲基化受局部序列和远端调控共同影响 | 输入：前一卷积块特征图；输出：多尺度融合特征 | 图 1a 架构图；Extended Data 图 3 | [预期] 移除后模型无法同时捕获局部与远端特征，预测精度下降 |
| 物种特异 batch normalization + 输出头 | 适配不同物种的甲基化分布差异 | 跨物种训练需处理分布偏移 | 输入：共享特征；输出：物种特异预测 | Extended Data 图 3 | [预期] 移除后跨物种训练不稳定，模型偏向高样本量物种 |
| DeepSHAP attribution | 计算每个核苷酸对预测的边际贡献 | 实现核苷酸级可解释性，定位关键序列特征 | 输入：模型 + 单序列；输出：每个位置的 attribution score | Results 图 2a；Methods "Sequence attribution score" | [预期] 移除后模型变为黑箱，无法识别 TF motif 贡献 |
| motif attribution score / MAS | 将核苷酸级 attribution 聚合到 TF motif 水平 | 连接序列特征与生物学功能（TF 结合） | 输入：attribution + JASPAR motif 位点；输出：每个 motif 的激活分数 | Results 图 2c、3a；Extended Data 图 6 | [预期] 移除后无法将序列贡献归因到具体 TF |
| in silico 扰动 | 模拟变异/删除对甲基化的影响 | 实现变异效应预测和因果验证 | 输入：reference/alternative 序列；输出：Δmethylation | Results 图 4e、5a；Extended Data 图 10 | [预期] 移除后丧失变异功能预测能力 |
| CRISPR 实验验证 | 验证模型预测的因果性 | 区分相关性与因果性 | 输入：CTCF KO / TRFM motif 删除；输出：WGBS 甲基化变化 | Results 图 4e、4f：预测与实验 PCC = 0.859–0.861 | [预期] 移除后模型预测缺乏实验背书，因果性存疑 |

## 09 关键公式符号

**1) Motif attribution score**（Methods "Sequence attribution score and motif analysis"）：

\[
\text{MotifAttributionScore}_m = \frac{1}{L} \sum_{b=1}^{L} |\text{AttributionScore}_{m,b}|
\]

- \( m \)：第 \( m \) 个 TF motif 位点
- \( b \)：motif 内的核苷酸位置
- \( L \)：motif 位点长度
- \(\text{AttributionScore}_{m,b}\)：DeepSHAP 计算的第 \( m \) 个 motif 第 \( b \) 个位置的 attribution score

**用途**：量化每个 TF motif 位点对甲基化预测的平均贡献强度。

**2) Motif activation score (MAS)**（Methods 同节）：

\[
\text{MAS}_m = \text{MotifMatchScore}_m \times \text{MotifAttributionScore}_m
\]

- \(\text{MotifMatchScore}_m\)：JASPAR PWM 匹配分数（文中未给出具体公式，仅说明 > 400 阈值）

**用途**：综合 motif 序列匹配强度与模型 attribution 强度，识别"激活"的 TF motif。

**3) 归一化 MAS (nMAS)**（Methods 同节）：

\[
\text{nMAS}_{m,c} = \frac{\sum_{a \in \text{active}} \text{MAS}_{a,m,c}}{N_{\text{UUR},c}}
\]

- \( c \)：细胞类型
- \( a \)：该细胞类型 UUR 中的活性 motif
- \( N_{\text{UUR},c} \)：该细胞类型的 UUR 数量

**用途**：跨细胞类型比较 motif 激活程度，识别组织特异性调控因子。

**4) in silico 变异效应**（Methods "In Silico Variant and Motif Knockout Prediction"）：

\[
\Delta\text{methylation} = \text{Prediction}_{\text{alt}} - \text{Prediction}_{\text{ref}}
\]

**用途**：预测遗传变异对甲基化的影响方向与大小。

## 10 实验设计与证据链

**数据集与资源**：
- 训练/验证/测试：1,900 WGBS 样本（12 物种），其中 1,574 人类样本（52 组织，238 细胞类型）；染色体划分：1-9、12-22 训练，10 验证，11 测试
- 外部验证：eGTEx mQTL（7 组织：乳腺、结肠、肺、骨骼肌、卵巢、前列腺、睾丸）；GWAS Catalog（2025 年 8 月下载）；ENCODE ChIP-seq（HEK-293/293T）
- 实验数据：自产 HEK-293T WGBS（30× 覆盖），CTCF KO 和 TRMU motif 删除细胞系
- 指标：Pearson correlation coefficient (PCC)、Spearman correlation coefficient (SCC)、方向预测准确率
- 基线：INTERACT（CNN-Transformer）、HyenaDNA（基因组基础模型）
- 计算资源：6 GPU（batch size 300，每 GPU 50）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 全基因组甲基化预测 | MethylAI 能从序列高精度预测单 CpG 甲基化 | 与 INTERACT、HyenaDNA 对比，matched model size | 平均 PCC = 0.875（MethylAI）vs 0.813（INTERACT）、0.828（HyenaDNA） | MethylAI 优于现有方法 | 未报告 SCC 或分组织详细对比 | Results 图 1d、Extended Data 图 3 |
| 与甲基化芯片比较 | 模型预测优于实验芯片 | WGBS 为 ground truth，对比甲基化芯片 | MethylAI 平均相关 0.854–0.923，芯片 0.803–0.871 | 序列模型可超越实验测量 | 未说明芯片类型和覆盖度差异 | Results 图 1d、Supplementary Table 2 |
| Attribution 距离衰减 | 近端序列主导甲基化预测 | 分析 attribution 随距离分布 | ±1 kb 贡献 31.7%，5.8 倍富集 | 局部序列是主要决定因素 | 未分析 >1 kb 的远端贡献 | Results 图 2a |
| TF motif 贡献分析 | TF motif 超越 CpG 组成影响甲基化 | 781 个 JASPAR motif，比较 motif attribution vs CpG 二核苷酸 | 19.5% 的 motif 比 CpG 二核苷酸更具信息量 | TF motif 是独立于 CpG 组成的调控特征 | 未做 motif 组合/交互效应分析 | Results Extended Data 图 6 |
| 组织特异 motif 激活 | motif 激活模式定义细胞身份 | 39 细胞类型 UUR，计算 nMAS | ETS 家族在免疫细胞、MyoD 在肌肉细胞中特异激活 | motif 激活具有组织特异性 | 未验证所有 39 种细胞类型 | Results 图 3b、3c |
| CTCF KO 实验验证 | 模型预测的 CTCF 调控效应真实存在 | CRISPR KO vs 非靶向对照，WGBS 比较 | 预测与实验甲基化变化 PCC = 0.859–0.861 | 模型捕获了 CTCF 的因果调控作用 | 仅验证了 CTCF 一个 TF | Results 图 4e、4f |
| TRMU motif 删除 | 单个 motif 的删除足以改变局部甲基化 | CRISPR 删除 TRMU 外显子内 CTCF motif | 删除后局部甲基化显著上升 | motif 是甲基化维持的充分条件 | 未检查远端效应 | Results 图 4e |
| mQTL 方向预测 | 模型能预测遗传变异对甲基化的影响 | eGTEx 7 组织 mQTL，比较预测方向 vs 统计方向 | 活性 motif 区域准确率 87.0–89.8%，非 motif 区域 52.6–58.1% | motif 区域变异效应可被准确预测 | 未做效应量（magnitude）的定量比较 | Results 图 5a、Extended Data 图 10 |
| GWAS 富集分析 | 活性 motif 富集疾病相关变异 | 52 组织活性 motif vs GWAS Catalog | 组织特异富集模式与已知疾病组织相关 | motif 连接遗传变异与疾病 | 未做共定位/Mendelian randomization | Results 图 5c |

## 11 结论正确解读

- **任务范围**：本文预测的是 CpG 甲基化状态（而非 TF 结合强度或 occupancy），模型输出为 5 个甲基化指标。TF motif 是通过 attribution 分析间接推断的调控因子，并非直接预测 TF–DNA 结合。
- **Oracle/真值输入**：训练标签来自 WGBS 实验测量值（smoothed 和 raw 两种形式），属于实验真值而非模拟数据。in silico 扰动预测以 CRISPR 实验为验证标准。
- **端到端状态**：模型是端到端的序列→甲基化映射，但 attribution 分析是事后解释（post-hoc），并非模型内生可解释。
- **算力成本**：预训练 140,000 步 × 12 物种交替采样，共 1,680,000 batch，6 GPU；未报告具体训练时间或 FLOPs。
- **历史数据依赖**：模型依赖参考基因组序列（hg38 等）和 JASPAR motif 数据库，变异效应预测依赖 eGTEx 和 GWAS Catalog 的统计关联数据。
- **模型依赖**：attribution 结果依赖 DeepSHAP/DeepLIFT 的近似质量；作者未报告 attribution 的稳定性或不确定性估计。
- **最难情形**：从结果看，非 motif 区域的变异方向预测准确率仅 ~53–58%（接近随机），说明模型对"非经典调控区域"的解释力有限。
- **群体/领域边界**：模型主要在人类组织/细胞系上评估；跨物种泛化仅通过预训练间接体现，未报告非人类物种的测试结果。
- **不确定性**：未报告预测置信区间或位点特异的不确定性度量。
- **有边界的复述**：MethylAI 能从序列高精度预测人类 CpG 甲基化（PCC ≈ 0.875），其 attribution 分析识别出约 1/5 的 TF motif 比 CpG 二核苷酸更具信息量，且这些 motif 的激活模式具有组织特异性；CRISPR 实验证实了 CTCF 相关预测的因果性；在活性 motif 区域，模型对遗传变异方向的预测准确率达 87–90%，但非 motif 区域预测能力接近随机。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 计算资源限制 | 未对全部 ~2700 万人类 CpG 位点进行 attribution 分析，仅随机抽样 100,000 个位点 | 未明确提及 | Results 节 "The sequence composition and patterns contributing to the methylation" |
| 组织覆盖有限 | 详细 motif 分析主要在肺组织上进行 | 未明确提及 | Results 节 同前 |
| 远端调控捕获不足 | 模型输入为 18 kb 窗口，可能无法捕获更远端的调控元件 | 未明确提及 | Methods 节 "MethylAI pre-training and fine-tuning" |
| 实验验证范围窄 | 仅验证了 CTCF 一个 TF 的敲除效应 | 未明确提及 | Results 节 "Experimental validation" |
| mQTL 数据组织有限 | eGTEx 仅覆盖 7 个组织 | 未明确提及 | Methods 节 "In Silico Variant and Motif Knockout Prediction" |

*注：作者在 Discussion 中未系统列出局限性，以上为从方法描述中可推断的隐含限制，非作者明确承认的局限。*

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| Attribution 分析仅基于 100,000 个抽样 CpG 位点 | 抽样偏差可能导致 motif 贡献估计不具全基因组代表性；位点选择偏向基因相关区域（按 10 类基因组区域各取 10,000） | 若抽样有偏，motif 排名和 MAS 分布可能无法推广 | 在全量 CpG 位点上重复 attribution 分析，比较 motif 排名稳定性 | Results 节 "The sequence composition and patterns contributing to the methylation" |
| DeepSHAP attribution 的可靠性未经验证 | DeepSHAP 对深度模型的归因近似可能有偏差，尤其对长距离交互；作者未与其它归因方法（如 Integrated Gradients、mutagenesis）对比 | Attribution 是全文核心解释工具，若不可靠则 motif 结论动摇 | 用输入扰动（in silico mutagenesis）交叉验证 attribution 排名 | Methods "Sequence attribution score and motif analysis" |
| "活性 motif" 定义依赖阈值（attribution < −0.02） | 阈值选择可能影响 motif 分类结果；未报告阈值敏感性分析 | 不同阈值可能改变组织特异 motif 的结论 | 对阈值进行扫描，报告 motif 分类的稳定性 | Methods 节 "Sequence attribution score and motif analysis" |
| CTCF 验证仅一个 TF、一个细胞系 | 单一实验不足以确立方法的普适因果性；CTCF 是已知甲基化绝缘子，可能选择性地验证了"容易验证"的案例 | 方法声称的普适性需要多 TF、多细胞系验证 | 对 GATA、AP-1 等预测的 motif 进行同样的 CRISPR 验证 | Results 节 "Experimental validation" |
| mQTL 方向预测准确率在非 motif 区域接近随机（~53%） | 模型对非经典调控区域的变异效应预测能力有限，可能高估了整体变异解释力 | 若用户将模型用于全基因组变异注释，需知晓其适用边界 | 按基因组区域分层报告预测准确率，明确模型适用边界 | Results 图 5a、Extended Data 图 10 |
| 跨物种预训练的优势未与非跨物种基线充分对比 | 作者称预训练是"dominant performance determinant"，但未报告仅用人类数据从头训练的完整对比曲线 | 预训练策略的可迁移性需要更严格的消融 | 报告无预训练、随机初始化、不同预训练数据规模的完整消融 | Extended Data 图 4 |
| 模型对甲基化"建立"vs"维持"的区分不明确 | 序列→甲基化映射可能主要反映维持机制（DNMT1 保真复制），而非从头建立（DNMT3A/B） | 对理解 TF 在发育中的主动调控作用有本质区别 | 使用时序甲基化数据（如分化过程）区分建立与维持 | Discussion 节 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **Attribution 驱动的 motif 发现流程**：训练序列→表观输出模型后，用 DeepSHAP 计算核苷酸级 attribution，再聚合到已知 TF motif 位点，可系统识别"有功能的" TF 结合位点。**迁移到 TF–DNA 结合课题**：可将此流程用于 ChIP-seq/HT-SELEX 数据训练的 TF 结合模型，识别哪些 motif 变异对结合亲和力影响最大。

2. **跨物种预训练策略**：在多个物种上预训练共享卷积骨干，配合物种特异 batch normalization 和输出头，可显著提升目标物种的预测精度。**迁移到 TF–DNA 结合课题**：TF 结合机制在物种间高度保守，跨物种预训练可缓解单物种数据不足问题，尤其适用于罕见 TF 或非模式物种。

3. **in silico 扰动 + 实验验证闭环**：模型预测变异/敲除效应后，用 CRISPR 实验验证，形成"预测→实验→模型修正"的闭环。**迁移到 TF–DNA 结合课题**：对 TF 结合模型预测的关键接触位点进行点突变实验验证，可建立因果性而非仅相关性。

4. **组织特异性 motif 激活评分 (nMAS)**：通过归一化 motif 激活分数，可跨细胞类型比较同一 TF 的调控活性，识别谱系决定因子。**迁移到 TF–DNA 结合课题**：类似评分可用于比较同一 TF 在不同细胞类型/条件下的结合活性，揭示 TF 功能的上下文依赖性。

5. **多任务学习整合多尺度信息**：同时预测单点甲基化和区域平均甲基化，迫使模型同时学习局部和区域特征。**迁移到 TF–DNA 结合课题**：TF 结合同时受局部 motif 和远端染色质环境调控，多任务目标可提升模型对两类特征的捕捉能力。

6. **变异效应方向预测**：模型不仅能预测甲基化水平，还能预测遗传变异导致的甲基化变化方向（Δmethylation），且准确率在功能区域显著更高。**迁移到 TF–DNA 结合课题**：类似框架可用于预测非编码变异对 TF 结合的影响，为 GWAS 变异的机制注释提供工具。

## 15 与已有知识连接

- **与 DeepSEA / Basenji 系列**：本文延续了"序列→调控输出"的深度学习范式，但创新在于跨物种预训练 + 核苷酸级 attribution 的 motif 解析，以及 CRISPR 实验验证闭环。可对比 DeepSEA 的变异效应预测功能。
- **与 Enformer**：Enformer 使用 Transformer 捕获长程调控，本文使用多尺度 CNN 捕获 18 kb 上下文。两者可互补：Enformer 的长程捕获能力可迁移至甲基化预测任务。
- **与 AlphaFold 系列**：AlphaFold 预测蛋白质结构，本文预测表观状态；两者共享"序列→功能"的映射逻辑，但本文的 attribution 可解释性更强。
- **与 DeepBind / DeepSEA 的 TF 结合预测**：本文的 motif attribution 方法可直接迁移至 TF 结合预测模型，用于识别关键接触核苷酸。
- **与 mQTL 研究（GTEx/eGTEx）**：本文将 mQTL 统计关联与序列模型预测结合，实现了从"关联"到"机制"的跨越，与 eQTL 的 fine-mapping 思路互补。
- **与 CRISPR 筛选**：本文的 CRISPR 验证策略与 CRISPR 干扰/激活筛选互补——前者验证单个 TF 的因果作用，后者可系统筛选多个 TF。
- **与 DNA 甲基化经典模型**：本文用数据驱动方式重新审视了 CpG 密度/GC 含量等经典特征，将其细化为 TF motif 层面的贡献，与经典表观遗传学模型形成对话。
- **与单细胞甲基化研究**：本文的模型可扩展至单细胞甲基化数据，为 sc-mWGBS 提供序列层面的先验。

## 16 研究想法

**Agent 生成的研究候选**：

1. **TF–DNA 结合特异性的可解释深度学习模型**
   - 名称：TF-BindAttribution
   - 来源局限/观察：本文的 attribution 方法仅用于甲基化预测，未直接用于 TF 结合预测；现有 TF 结合模型（如 DeepBind）缺乏核苷酸级归因
   - 核心假设：将 DeepSHAP attribution 应用于 TF 结合模型，可识别每个 TF 的核心接触位点与辅助位点，且与结构生物学数据（如 PDB 晶体结构）一致
   - 初步方法：用 HT-SELEX / ChIP-seq 数据训练 CNN 模型，计算核苷酸级 attribution，与已知 TF–DNA 接触残基比对
   - 验证方式：与 PDB 结构比对、突变实验验证
   - 创新状态：unverified

2. **跨物种 TF 结合 motif 保守性分析**
   - 名称：CrossTF-Conservation
   - 来源局限/观察：本文跨物种预训练提升了甲基化预测，但未分析 TF motif 的跨物种保守性；TF 结合机制在进化中的保守程度未知
   - 核心假设：跨物种预训练模型可揭示 TF 结合 motif 的保守核心与物种特异扩展
   - 初步方法：用多物种 ChIP-seq/HT-SELEX 数据训练共享模型，比较各物种 attribution 模式
   - 验证方式：与系统发育分析、已知 TF 直系同源物比对
   - 创新状态：unverified

3. **TF 结合变异的 in silico 扰动预测与 CRISPR 验证**
   - 名称：TF-VariantPerturb
   - 来源局限/观察：本文验证了甲基化变异的 in silico 预测，但未对 TF 结合变异进行系统验证
   - 核心假设：序列模型可准确预测单核苷酸变异对 TF 结合亲和力的影响，且预测效应与实验测量一致
   - 初步方法：训练 TF 结合模型，对已知致病/风险变异进行 in silico 突变，预测结合变化，用 CRISPR 或电泳迁移实验验证
   - 验证方式：与 gSELEX / MITOMI 实验数据比对
   - 创新状态：unverified

4. **甲基化与 TF 结合的联合建模**
   - 名称：MethTF-JointModel
   - 来源局限/观察：本文仅预测甲基化，未联合建模 TF 结合与甲基化的双向关系；TF 结合可招募 DNMT/TET，甲基化也可影响 TF 结合
   - 核心假设：联合建模可揭示 TF–甲基化调控回路的序列编码规则
   - 初步方法：多任务学习同时预测 TF 结合和甲基化，分析 attribution 的交叉模式
   - 验证方式：与 ChIP-seq + WGBS 配对数据比对
   - 创新状态：unverified

5. **组织特异性 TF 激活评分的泛化应用**
   - 名称：TissueTF-ActivationMap
   - 来源局限/观察：本文的 nMAS 仅用于 39 种细胞类型的 UUR 分析，未扩展至全基因组
   - 核心假设：全基因组 nMAS 图谱可系统揭示组织特异性 TF 调控网络
   - 初步方法：对 52 组织计算全基因组 nMAS，聚类分析组织特异调控模块
   - 验证方式：与已知组织特异增强子/超级增强子数据比对
   - 创新状态：unverified

6. **长程调控的甲基化预测扩展**
   - 名称：Meth-LongRange
   - 来源局限/观察：本文使用 18 kb 窗口，可能遗漏更远端的调控元件；Enformer 的长程捕获能力未被用于甲基化预测
   - 核心假设：引入长程注意力机制可提升甲基化预测精度，特别是 CTCF 介导的绝缘子边界效应
   - 初步方法：在 MethylAI 架构中引入 Transformer 层或扩大输入窗口至 100 kb+
   - 验证方式：与 Hi-C 数据比对，检验模型是否捕获 3D 基因组结构信息
   - 创新状态：unverified