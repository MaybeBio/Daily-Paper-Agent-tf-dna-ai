## 01 基本信息
- **标题**：ChromBPNet: bias factorized, base-resolution deep learning models of chromatin accessibility reveal cis-regulatory sequence syntax, transcription factor footprints and regulatory variants
- **作者与单位**：Pampari, Anusri; Shcherbina, Anna; Kvon, Evgeny Z; Kosicki, Michael; Nair, Surag; Kundu, Surag; Kathiria, Arwa S; Risca, Viviana I; Kuningas, Kristiina; Alasoo, Kaur; Greenleaf, William James; Pennacchio, Len A; Kundaje, Anshul（单位未在摘要中提供）
- **期刊/预印本平台**：bioRxiv : the preprint server for biology
- **年份**：2025-01-20
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：计算基因组学；调控基因组学；深度学习
- **关键词**：染色质可及性；转录因子足迹；深度学习；序列语法；调控变异；碱基分辨率
- **DOI/arXiv 号**：10.1101/2024.12.25.630221
- **代码**：https://github.com/kundajelab/chrombpnet
- **数据**：ENCODE portal；H1-hESC ATAC-seq 数据在 GEO GSE267154；Synapse 仓库 syn59449898 等
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文是「TF–DNA 结合机制 × 深度学习」方向的代表性工作，核心贡献在于：(1) 将染色质可及性测序（ATAC-seq/DNase-seq）中的酶切偏好（enzyme bias）与真实的 TF 结合信号（footprint）解耦；(2) 在碱基分辨率上预测可及性谱，并从中提取 TF motif 语法和足迹；(3) 将模型用于调控变异效应预测。对 TF–DNA 互作研究而言，本文提供了一种「从可及性数据中无偏提取 TF 结合信号」的通用框架，其 bias factorization 思想可迁移到其他基于酶切/切割的互作检测实验（如 ChIP-exo、CUT&Tag 等）。

## 02 一句话总结
本文提出 ChromBPNet——一种 bias-factorized 的碱基分辨率深度学习模型，通过显式建模并去除 Tn5/DNase-I 酶切偏好，从 ATAC-seq/DNase-seq 数据中准确预测染色质可及性谱，从而揭示紧凑的 TF motif 词典、协同结合的序列语法（如 FOS-TEAD 复合元件）和高精度 TF 足迹，并在多个 QTL 和报告基因数据集上验证了其变异效应预测能力。

## 03 研究问题
- **具体问题**：如何从碱基分辨率的染色质可及性数据（ATAC-seq/DNase-seq）中，准确识别决定染色质开放的 TF 结合序列语法和足迹，并预测调控变异的效应？
- **为什么重要**：染色质可及性数据被广泛用于定位顺式调控元件（cREs），但其中的酶切信号同时包含 TF 结合保护和酶切偏好两种信息。若不能将二者解耦，将无法准确推断 TF 结合位点、足迹和序列语法，也无法可靠预测变异效应。
- **现有方法不足**：
  - 传统足迹方法（如 HINT-ATAC、TOBIAS）依赖预定义 motif 库，无法发现新 motif，且对低深度数据敏感；
  - 现有深度学习模型（如 BPNet 的原始版本）直接训练于原始可及性谱，未显式建模酶切偏好，导致模型将酶切偏好误学为 TF 结合信号；
  - 大规模多任务模型（如 Enformer）虽预测能力强，但参数量大、训练成本高，且其变异效应评分存在系统性偏差（如使用过宽的窗口稀释局部信号）。
- **精确研究问题（Can 问题）**：Can a bias-factorized, base-resolution deep learning model trained on chromatin accessibility data accurately deconvolve enzyme sequence preferences from TF binding signals, thereby enabling robust discovery of TF motifs, footprints, and regulatory variant effects?

## 04 背景与发展脉络
（注：以下脉络基于本文框架，部分经外部核验，标注如下）

1. **染色质可及性测序与足迹分析**（经外部核验）：DNase-seq 和 ATAC-seq 通过酶切开放染色质区域，产生碱基分辨率的切割谱。TF 结合会保护 DNA 免受切割，形成「足迹」（footprint）。早期足迹方法（如 DNase-seq 时代的 Wellington、HINT）利用统计模型识别足迹，但受限于深度和酶切偏好。
2. **深度学习预测可及性**（经外部核验）：BPNet（Avsec et al., 2021）首次将碱基分辨率预测框架用于 ChIP-seq 和 ATAC-seq，但其原始 ATAC-seq 模型未显式处理酶切偏好。后续工作（如 Basenji、Enformer）转向长上下文多任务预测，但牺牲了碱基分辨率的可解释性。
3. **酶切偏好的显式建模**（本文核心贡献）：本文发现，直接在原始可及性谱上训练的模型会学习到 Tn5/DNase-I 的序列偏好（如 Tn5 偏好 GC 富集区域），这些偏好与 TF 结合信号混淆。ChromBPNet 通过两阶段训练——先在背景区域训练「bias model」捕获酶切偏好，再在峰区域训练「residual model」学习 TF 贡献——实现了二者的解耦。
4. **变异效应预测**（经外部核验）：从 deltaSVM 到 Enformer，深度学习模型被广泛用于预测调控变异的效应。本文提出新的变异效应评分（整合 count 和 profile 变化），并在多个独立 QTL 数据集上验证，同时指出 Enformer 原始评分窗口过宽的问题。
5. **本文主张的位置**：ChromBPNet 填补了「碱基分辨率可解释模型」与「大规模多任务模型」之间的空白——它比 Enformer 更轻量、可解释，但预测性能相当；比传统足迹方法更全面，能同时发现 motif、语法和足迹。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 酶切偏好与 TF 信号混淆 | 在原始可及性谱上训练的模型，其 profile 贡献分数中大量碱基被归因于非 TF 的序列偏好（如 Tn5 的 GC 富集偏好），导致足迹识别失真 | 酶（Tn5/DNase-I）本身具有序列偏好，在切割位点附近产生系统性偏差；模型无法区分「酶偏好」与「TF 保护」 | Results 图 1f–g：未校正模型 profile 贡献分数中检测到 Tn5 偏好 motif；Results 图 2c：bias model 的 TF-MODISCO 仅发现 Tn5/DNase-I 偏好 motif |
| 传统足迹方法依赖预定义 motif | HINT-ATAC、TOBIAS 等需要已知 motif 数据库，无法发现新 motif 或非经典结合模式 | 这些方法本质上是「在已知 motif 位置寻找足迹」，而非从头发现 | Results 图 2e–g：ChromBPNet 无需预定义 motif 即可发现 TF 足迹，且与 ChIP-seq 数据高度一致 |
| 低深度数据下足迹不可靠 | 传统足迹方法在 <100M reads 时无法稳定识别足迹 | 足迹信号本质上是局部切割减少，深度不足时统计功效不足 | Results 图 4a–d：ChromBPNet 在 25M reads 下仍能准确恢复足迹和 motif，而原始谱已无法目视识别 |
| 变异效应预测窗口选择不当 | Enformer 原始评分使用 ~100Kb 窗口，稀释了局部变异效应 | 变异对可及性的影响是局部的（~1Kb），过宽窗口引入大量无关信号 | Results 图 6a：ChromBPNet 的局部评分（1Kb）优于 Enformer 的全局评分；Methods 节「Enformer variant effect prediction metrics」 |
| 多任务模型不可解释 | Enformer 等模型预测准确但难以提取序列语法和 motif | 长上下文、多任务设计使归因分析复杂化 | Discussion：ChromBPNet 的轻量设计使其可解释性更强，能直接提取 motif 和语法 |

## 06 核心思想
1. **表面方法**：ChromBPNet 是一个序列到谱的卷积神经网络（CNN），输入 2114 bp DNA 序列，输出 1000 bp 的碱基分辨率可及性谱（分为 count 和 profile 两个头）。训练分为两阶段：第一阶段在背景区域（非峰区域）训练一个浅层「bias model」捕获酶切偏好；第二阶段在峰区域训练一个深层「residual model」，其输入包含原始序列和 bias model 的预测输出，学习去除酶切偏好后的 TF 贡献。

2. **核心洞察**：酶切偏好与 TF 结合信号在可及性谱中是可分离的——酶切偏好主要影响 profile 形状（局部切割概率），而 TF 结合同时影响 count（总可及性）和 profile（足迹）。通过两阶段残差学习，模型能够将二者解耦，使得 residual model 的贡献分数只反映 TF 结合信号。这一设计使得 ChromBPNet 能够在碱基分辨率上同时实现：(a) 准确的谱预测；(b) 无偏的 TF 足迹识别；(c) 紧凑的 motif 词典发现。

3. **可能的普适教训** [Analysis]：在基于酶切的分子实验中（如 ATAC-seq、DNase-seq、ChIP-exo、CUT&Tag），酶切偏好是普遍存在的系统性偏差。ChromBPNet 的「先学偏差、再学残差」两阶段框架，可以推广到任何「信号 + 噪声」可分离的深度学习任务中。此外，本文强调「模型解释」而非仅「预测性能」作为模型设计的核心目标，这一思路对 TF–DNA 互作研究尤为重要——因为最终目标是理解机制，而非仅预测数值。

## 07 方法总览
- **输入**：2114 bp 的 one-hot 编码 DNA 序列（A/C/G/T）
- **输出**：1000 bp 的碱基分辨率可及性谱，包含两个头：
  - Count head：预测总可及性（标量）
  - Profile head：预测碱基分辨率的切割概率分布（1000 维向量）
- **模块**：
  1. **Bias model**：浅层 CNN（128 filters，4 层 dilation），在背景区域训练，捕获 Tn5/DNase-I 酶切偏好
  2. **Residual model**：深层 CNN（512 filters，8 层 dilation），在峰区域训练，输入为原始序列 + bias model 的预测输出，学习 TF 贡献
  3. **两阶段训练**：第一阶段固定 bias model，第二阶段训练 residual model
- **训练**：Adam 优化器，学习率 0.001，5 折交叉验证；损失函数为 BPNet 多尺度损失（count 的 MSE + profile 的多项式负对数似然）
- **解释工具**：DeepLIFT/DeepSHAP 计算贡献分数；TF-MODISCO 进行 motif 发现
- **变异效应评分**：整合 count 和 profile 变化的多个指标（logFC、JSD、AAQ、IES、IPS）
- **流程**：训练 bias model → 训练 residual model → 在峰区域计算贡献分数 → TF-MODISCO 发现 motif → 变异效应评分 → 与 QTL/报告基因数据验证

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Bias model | 捕获 Tn5/DNase-I 酶切偏好 | 酶切偏好是 profile 形状的主要干扰源，需先建模并去除 | 输入：2114 bp 序列；输出：1000 bp 背景切割概率 | Results 图 2c：bias model 的 TF-MODISCO 仅发现 Tn5/DNase-I 偏好 motif，无已知 TF motif | 预期影响 [Analysis]：移除后 residual model 将重新学习酶切偏好，导致足迹失真（类似未校正的 BPNet） |
| Residual model | 学习 TF 结合对可及性的贡献 | 去除酶切偏好后，残差信号主要反映 TF 结合 | 输入：2114 bp 序列 + bias model 输出；输出：1000 bp 可及性谱（count + profile） | Results 图 2e–g：residual model 的贡献分数清晰识别 TF motif 和足迹 | 预期影响 [Analysis]：移除后模型无法区分 TF 信号与酶切偏好，motif 发现将受污染 |
| Count head | 预测总可及性 | 捕获峰的整体强度，反映 TF 结合的总效应 | 输入：bottleneck 特征；输出：标量 | Results 图 1c：count 预测与实测高度相关（r=0.70–0.71） | 预期影响 [Analysis]：移除后无法预测变异的可及性总效应，仅剩 profile 形状信息 |
| Profile head | 预测碱基分辨率切割概率 | 提供足迹信息，反映 TF 结合的精确位置 | 输入：bottleneck 特征；输出：1000 维概率向量 | Results 图 1d：profile 预测与实测高度一致（JSD 接近伪复制上限） | 预期影响 [Analysis]：移除后无法进行足迹分析，变异效应评分失去 profile 维度 |
| DeepLIFT/DeepSHAP | 计算碱基贡献分数 | 将模型预测归因到具体碱基，用于 motif 发现 | 输入：模型 + 序列；输出：每个碱基的贡献分数 | Methods 节「DeepLIFT contribution scores」 | 预期影响 [Analysis]：移除后无法解释模型，motif 发现和语法分析不可行 |
| TF-MODISCO | 从贡献分数中发现 motif | 无监督地从贡献分数中提取序列 motif | 输入：贡献分数；输出：motif 矩阵（CWM/PFM） | Results 图 1e–f：发现已知 TF motif（CTCF、SP1 等） | 预期影响 [Analysis]：移除后无法获得 motif 词典，只能依赖外部数据库 |
| 变异效应评分模块 | 计算多种变异效应指标 | 将模型预测转化为可验证的变异效应评分 | 输入：参考/变异序列的预测谱；输出：logFC、JSD、AAQ、IES、IPS | Results 图 6a–k：多个 QTL 数据集验证 | 预期影响 [Analysis]：移除后无法进行变异优先级排序 |

## 09 关键公式符号
（注：原文 Methods 节未提供完整公式推导，以下基于描述性内容整理）

1. **多尺度损失函数**（BPNet 损失）：
   - Count 损失：MSE(log(1+n_obs), log(1+n_pred))
   - Profile 损失：多项负对数似然，-log(n_obs! / (k_1!...k_L!)) * p_1^k_1...p_L^k_L
   - 总损失 = Profile 损失 + λ * Count 损失，其中 λ = ñ_obs / 10，ñ_obs 为验证集总 count 的中位数

2. **Bias factorization 预测**：
   - p_pred = p_tf * p_bias（profile 概率的逐元素乘积）
   - n_pred = n_tf + γ * n_bias（count 的加性组合）
   - 其中 γ = exp(Σ[log(n_bias+1) - log(n_obs+1)] / N)，N 为训练+验证样本数

3. **变异效应评分**：
   - logFC = log(n_pred(alt) + 1) - log(n_pred(ref) + 1)
   - JSD = Jensen-Shannon Distance(p_pred(alt), p_pred(ref))
   - AAQ = 变异位点处 alt 等位基因的 profile 概率在基因组中的百分位
   - IES = 整合 logFC 和 JSD 的评分
   - IPS = 整合 logFC、JSD 和 AAQ 的评分

4. **符号说明**：
   - p_tf：residual model 预测的 profile 概率
   - p_bias：bias model 预测的 profile 概率
   - n_tf：residual model 预测的 count
   - n_bias：bias model 预测的 count
   - n_obs：观测到的 count

## 10 实验设计与证据链
**数据集/群体**：
- 训练数据：5 个 ENCODE Tier-1 细胞系（K562, HepG2, GM12878, IMR90, H1-hESC）的 ATAC-seq 和 DNase-seq 数据
- 变异效应验证：
  - dsQTL：70 个约鲁巴 LCL 的 DNase-seq QTL（~500 个显著 QTL，27,735 个对照）
  - caQTL：~100 个欧洲 LCL 和 ~100 个非洲 LCL 的 ATAC-seq QTL
  - MPRA：CAGI5 竞赛的 14 个疾病相关调控元件（9 个启动子，5 个增强子）
  - 罕见病：DECIPHER 发育障碍（DDD）队列的 de novo 变异

**指标**：
- 谱预测：Pearson 相关（count）、JSD（profile）
- 变异效应：AUROC、AUPRC、Pearson 相关（预测 vs 实测效应）

**基线**：
- 未校正的 BPNet（无 bias factorization）
- 传统足迹方法：HINT-ATAC、TOBIAS
- 大规模模型：Enformer（原始和修正评分）
- 传统方法：deltaSVM、gkm-SVM

**关键实验与结果**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|-------------|-------------------|------|
| 谱预测性能 | ChromBPNet 能准确预测碱基分辨率可及性谱 | 5 折交叉验证，与未校正 BPNet 对比 | count r=0.70±0.02（ATAC）、0.71±0.02（DNase）；profile JSD 接近伪复制上限 | ChromBPNet 预测性能与未校正 BPNet 相当 | 未证明 bias factorization 提升预测精度（其价值在解释而非预测） | Results 图 1c–d |
| Bias model 验证 | Bias model 仅学习酶切偏好，不学习 TF motif | TF-MODISCO 分析 bias model 的贡献分数 | 仅发现 Tn5/DNase-I 偏好 motif，无已知 TF motif | Bias model 成功隔离了酶切偏好 | 未证明 bias model 捕获了所有酶切偏好 | Results 图 2c |
| 足迹识别 | ChromBPNet 能识别高精度 TF 足迹 | 与 ChIP-seq 数据对比，与 HINT-ATAC、TOBIAS 对比 | ChromBPNet 足迹与 ChIP-seq 峰高度一致，优于传统方法 | Bias factorization 提升了足迹识别的准确性 | 未在全部 TF 类型上验证 | Results 图 2e–g |
| 低深度鲁棒性 | ChromBPNet 在低深度数据下仍能识别足迹 | 对 250M/100M/50M/25M/5M reads 子采样数据训练 | 25M reads 下足迹和 motif 恢复率仍高 | ChromBPNet 对低深度数据鲁棒 | 5M reads 下性能下降 | Results 图 4a–d |
| dsQTL 变异优先级 | ChromBPNet 能预测染色质 QTL 变异效应 | 与 Enformer、deltaSVM 对比 | AP=0.54（ATAC 572M）、0.43（DNase 68M），优于 Enformer 原始评分（AP=0.33） | ChromBPNet 在变异优先级上优于 Enformer 原始评分 | Enformer 修正评分后 AP=0.53，与 ChromBPNet 相当 | Results 图 6a |
| 跨祖先泛化 | ChromBPNet 能跨祖先预测变异效应 | 欧洲 LCL 模型预测非洲 LCL QTL | 非洲亚组间 r=0.96–0.97，欧洲-非洲 r=0.93–0.95 | 模型跨祖先泛化良好 | 未在非 LCL 组织验证 | Results 图 6i |
| 罕见病 de novo 变异 | ChromBPNet 能优先排序罕见病 de novo 变异 | DDD 队列，与 Enformer 对比 | 成功识别致病性 de novo 变异 | ChromBPNet 可用于罕见病变异解读 | 样本量有限 | Results 图 7g–h |
| 报告基因验证 | ChromBPNet 预测的变异效应与实验一致 | CAGI5 MPRA 数据 | 14 个位点中 5 个显著优于 Enformer，其余相当 | ChromBPNet 预测与实验测量一致 | 部分位点预测精度有限 | Results 图 7d |

## 11 结论正确解读
- **任务范围**：本文的模型预测的是「染色质可及性」而非「TF 结合」本身。可及性变化是 TF 结合、核小体重塑等多种因素的综合结果，因此 ChromBPNet 识别的「足迹」反映的是 TF 对染色质开放的综合贡献，而非直接的 TF 占据率。
- **Oracle/真值输入**：训练标签来自实验测量的 ATAC-seq/DNase-seq 切割谱，这些谱本身包含酶切偏好和实验噪声。Bias model 在背景区域训练，假设背景区域无 TF 结合，这一假设在弱峰区域可能不成立。
- **端到端状态**：ChromBPNet 是端到端训练的序列到谱模型，但变异效应预测需要额外的评分步骤（logFC、JSD 等），并非直接从序列输出变异效应。
- **算力成本**：模型参数量约 6M（远小于 Enformer 的 250M），训练成本较低，但 5 折交叉验证和多次子采样训练仍需一定计算资源。
- **历史数据依赖**：模型仅使用参考基因组序列作为输入，不依赖等位基因频率或群体数据，因此可应用于任意变异。
- **最难情况**：低频率 motif、弱 TF 结合位点、非经典结合模式（如间接结合）的识别仍具挑战性；变异效应预测在非 LCL 组织或远端调控元件上未充分验证。
- **群体/领域边界**：跨祖先验证仅在 LCL 中进行，其他组织或物种的泛化性未验证。
- **不确定性**：变异效应预测的置信区间未系统评估；模型对 indel 和结构变异的预测能力未测试。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 可解释性 vs 预测精度的权衡 | 模型仅使用 2Kb 局部序列上下文，可能遗漏远端调控信息 | 未来可探索更长上下文或与长程模型结合 | Discussion 节 |
| 对「settler」TF 的覆盖不足 | 模型主要识别影响可及性的 TF（多为 pioneer 或先锋因子），对仅结合开放染色质但不影响可及性的 TF 不敏感 | 结合 TF 结合数据（如 ChIP-seq）进行多任务学习 | Discussion 节 |
| 变异效应预测的验证范围有限 | 主要在 LCL 和少数细胞类型中验证，其他组织/细胞类型未充分测试 | 扩展至更多细胞类型和组织 | Discussion 节 |
| 模型对远端调控变异的预测能力有限 | 2Kb 窗口无法捕获远端增强子-启动子互作 | 与 3D 基因组数据结合 | Discussion 节 |
| 未系统评估 indel 和结构变异 | 主要针对 SNP 进行变异效应预测 | 扩展至其他变异类型 | Discussion 节 |
| 计算资源需求 | 虽然模型轻量，但 5 折交叉验证和子采样训练仍需较多 GPU 资源 | 优化训练流程 | 未明确提及，[Analysis] 推断 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| Bias model 在背景区域训练，假设背景区域无 TF 结合 | 背景区域可能包含弱 TF 结合位点，导致 bias model 混入 TF 信号 | 若 bias model 混入 TF 信号，residual model 将低估 TF 贡献，影响足迹定量 | 在已知无 TF 结合的「真背景」区域（如异染色质）验证 bias model 的预测 | Methods 节「BPNet based bias model training」 |
| 模型仅使用 2Kb 局部序列上下文 | 远端增强子对可及性的影响可能超出 2Kb 窗口 | 若远端调控重要，模型可能错过关键调控变异 | 比较 2Kb 与更长窗口（如 10Kb）模型的变异预测性能 | Discussion 节 |
| 变异效应评分依赖多个启发式指标（logFC、JSD、AAQ 等） | 这些指标可能捕获不同的生物学信号，整合方式缺乏理论指导 | 指标选择影响变异优先级排序的准确性 | 系统比较不同评分组合在多个 QTL 数据集上的表现 | Results 图 6a–k |
| 与 Enformer 的比较可能不公平 | Enformer 是多任务模型，其染色质可及性预测仅是众多任务之一；且 Enformer 使用更长的上下文窗口 | 公平比较需要控制模型架构和训练数据差异 | 在相同训练数据上训练相同架构的模型进行比较 | Results 图 6a |
| 模型在 LCL 中训练和验证，跨组织泛化未充分测试 | 不同细胞类型的染色质环境（如核小体密度、TF 表达谱）差异可能影响模型泛化 | 若模型不能跨组织泛化，其应用范围受限 | 在多种细胞类型的可及性数据上测试模型 | Results 图 6j–k（仅 microglia 和 SMC） |
| 足迹定量缺乏直接实验验证 | 模型预测的足迹深度和宽度未与高分辨率实验（如 ChIP-exo、Methylation footprinting）直接对比 | 足迹是模型解释的核心输出，需实验验证其准确性 | 在已知 TF 结合位点比较模型足迹与实验足迹 | Results 图 2e–g（仅与 ChIP-seq 峰重叠，未定量比较足迹形状） |

## 14 与已有知识连接
- **BPNet（Avsec et al., 2021, Nature Genetics）**：ChromBPNet 直接继承 BPNet 的架构和损失函数，但增加了 bias factorization 模块。BPNet 原始模型未处理酶切偏好，ChromBPNet 通过两阶段训练解决了这一问题。
- **Enformer（Avsec et al., 2021, Nature Methods）**：Enformer 是长上下文（200Kb）多任务 transformer 模型，ChromBPNet 在变异优先级任务上与其对比。两者互补：Enformer 捕获远端调控，ChromBPNet 提供碱基分辨率的局部可解释性。
- **TF footprinting 方法（HINT-ATAC, TOBIAS）**：这些方法使用统计模型从可及性谱中识别足迹，但依赖预定义 motif 库。ChromBPNet 无需预定义 motif，可从头发现 motif 和足迹。
- **deltaSVM（Lee et al., 2015）**：基于 gapped k-mer SVM 的变异效应预测方法，ChromBPNet 在 dsQTL 任务上显著优于 deltaSVM。
- **TF–DNA 结合机制**：本文的「pioneer factor」概念（如 OCT4-SOX2、GATA1）与已知的先锋因子在染色质开放中的主导作用一致。ChromBPNet 识别的 motif 语法（如 FOS-TEAD 复合体）为 TF 协同结合提供了序列层面的证据。
- **可迁移性**：bias factorization 思想可迁移到其他基于酶切的实验（如 ChIP-exo、CUT&Tag、MNase-seq），这些实验同样存在酶切偏好问题。此外，本文的「先学偏差、再学残差」框架可推广到任何信号与噪声可分离的深度学习任务。

## 15 学到什么
（Agent 提炼的知识候选）
1. **Bias factorization 是处理实验偏差的通用策略**：在基于酶切的分子实验中，酶切偏好是系统性偏差。ChromBPNet 的两阶段训练（先学偏差、再学残差）可迁移到 ChIP-exo、CUT&Tag 等实验的建模中，帮助分离真实生物学信号与技术噪声。
2. **碱基分辨率模型的可解释性优于粗粒度模型**：ChromBPNet 的 1Kb 碱基分辨率输出使其能直接提取足迹和 motif 语法，而粗粒度模型（如 128bp bin）无法做到。对于 TF–DNA 互作研究，碱基分辨率是必要的。
3. **模型解释应作为设计目标而非事后分析**：ChromBPNet 的架构设计（bias model + residual model）从一开始就考虑了可解释性，而非仅追求预测精度。这一思路对机制研究尤为重要。
4. **变异效应预测需要局部与全局信号的平衡**：ChromBPNet 的 2Kb 窗口在局部变异效应预测上优于 Enformer 的 100Kb 窗口，说明过大的上下文可能稀释局部信号。但远端调控仍需要长上下文模型，未来可探索「局部碱基分辨率 + 全局上下文」的混合架构。
5. **跨祖先泛化是评估模型鲁棒性的重要维度**：ChromBPNet 在欧洲训练的模型在非洲 LCL 上表现良好，说明模型学习的是保守的调控机制而非群体特异的连锁模式。
6. **足迹形态（深度、宽度）可反映 TF 结合模式**：ChromBPNet 的 marginal footprint 分析显示不同 TF 具有不同的足迹形态，这为研究 TF 结合模式（如 residence time、协同结合）提供了新的定量工具。

## 16 研究想法
（Agent 生成的研究候选）
1. **候选名称**：Bias-factorized 的 TF–DNA 结合预测模型（TF-BindNet）
   - **来源局限/观察**：ChromBPNet 预测的是染色质可及性，而非直接的 TF 结合。可及性变化是 TF 结合、核小体重塑等综合结果，无法区分「直接结合」与「间接影响」。
   - **核心假设**：将 ChromBPNet 的 bias factorization 框架扩展到 TF 结合预测，可以分离「TF 直接结合」与「染色质环境效应」。
   - **初步方法**：在 ChromBPNet 架构基础上，增加 TF 结合标签（如 ChIP-seq 峰）作为辅助输出，使用多任务学习同时预测可及性和 TF 结合。bias model 仍捕获酶切偏好，residual model 学习 TF 结合信号。
   - **验证方式**：在 ENCODE TF ChIP-seq 数据上评估，比较与现有 TF 结合预测模型（如 DeepSEA、Basenji）的性能。
   - **创新状态**：unverified

2. **候选名称**：足迹形态的定量分析与 TF 结合动力学推断
   - **来源局限/观察**：ChromBPNet 的 marginal footprint 分析显示不同 TF 具有不同足迹形态，但未系统量化足迹形态与 TF 结合动力学（如 residence time）的关系。
   - **核心假设**：足迹深度和宽度可反映 TF 的结合强度和解离速率，可用于推断 TF 结合动力学。
   - **初步方法**：从 ChromBPNet 的 bias-corrected 足迹中提取形态特征（深度、宽度、对称性），与已知 TF 结合动力学参数（如 SPR 测量）关联，建立预测模型。
   - **验证方式**：在已知 residence time 的 TF 上验证，比较预测与实验测量。
   - **创新状态**：unverified

3. **候选名称**：跨细胞类型的 TF 结合序列语法迁移学习
   - **来源局限/观察**：ChromBPNet 为每个细胞类型单独训练模型，未利用跨细胞类型的共享调控语法。
   - **核心假设**：TF 结合序列语法在细胞类型间部分共享，迁移学习可以提高低资源细胞类型的预测性能。
   - **初步方法**：使用多任务学习或预训练-微调策略，在多个细胞类型的可及性数据上联合训练 ChromBPNet，评估对低资源细胞类型的提升。
   - **验证方式**：在稀有细胞类型（如原代细胞）的可及性数据上测试，比较与单细胞类型训练的模型。
   - **创新状态**：unverified

4. **候选名称**：结合 MD 模拟的 TF 足迹解释
   - **来源局限/观察**：ChromBPNet 的足迹反映统计意义上的切割保护，但缺乏分子层面的机制解释。
   - **核心假设**：MD 模拟可以揭示 TF 结合如何改变局部 DNA 柔性和可及性，为足迹提供分子机制解释。
   - **初步方法**：选择 ChromBPNet 识别的高置信度 TF 结合位点，进行 MD 模拟（TF-DNA 复合物），分析 DNA 的局部柔性和切割敏感性，与足迹深度关联。
   - **验证方式**：比较 MD 预测的切割敏感性与 ChromBPNet 足迹，评估一致性。
   - **创新状态**：unverified

5. **候选名称**：基于 ChromBPNet 的调控变异功能评分（ChromBPNet-Var）
   - **来源局限/观察**：ChromBPNet 的变异效应评分在多个 QTL 数据集上表现良好，但未与现有工具（如 CADD、Eigen）系统比较。
   - **核心假设**：ChromBPNet 的碱基分辨率预测可提供比现有工具更精确的调控变异功能评分。
   - **初步方法**：在 ClinVar、GWAS 目录等数据上系统比较 ChromBPNet 与现有工具的性能，评估其独立贡献。
   - **验证方式**：在多个独立数据集上评估 AUROC、AUPRC，并与现有工具进行集成分析。
   - **创新状态**：partially checked（本文已在 dsQTL、caQTL 上验证，但未与 CADD 等系统比较）