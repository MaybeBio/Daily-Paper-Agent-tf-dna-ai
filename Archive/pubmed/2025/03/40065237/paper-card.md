## 01 基本信息

- **标题**：SNPeBoT: a tool for predicting transcription factor allele specific binding
- **作者**：Gohl, Patrick; Oliva, Baldo
- **单位**：未提供（据URL推测为西班牙UPF大学结构生物信息学实验室，但原文未明确）
- **期刊/平台**：BMC Bioinformatics
- **年份**：2025
- **论文类型**：方法学/工具类论文
- **领域**：生物信息学、转录因子-DNA结合、深度学习
- **关键词**：SNP、等位基因特异性结合（ASB）、转录因子、深度学习、CNN、ChIP-seq、PBM
- **DOI/arXiv**：10.1186/s12859-025-06094-4
- **代码**：https://github.com/structuralbioinformatics/SNPeBoT
- **数据**：ADASTRA数据库（ChIP-seq ASB数据）、CISBP数据库（PBM E-score数据）、GTRD（对照数据）、AlleleDB（泛化测试数据）
- **阅读日期**：未提供
- **在本课题方向中的位置**：该文属于「TF–DNA结合机制 × 深度学习」方向，聚焦于预测SNP对TF结合的影响（ASB gain/loss/no-change），核心创新在于将PBM实验的E-score（体外结合亲和力）与ChIP-seq的ASB数据（体内结合事件）结合作为CNN输入特征，为TF–DNA结合特异性的序列编码提供了新视角。

## 02 一句话总结

该文训练了一个以PBM E-score谱和FIMO PWM扫描得分为输入的CNN模型（SNPeBoT），用于预测SNP导致TF结合增益、丧失或无变化，在基准测试中准确率和ASB召回率均优于MotifbreakR和atSNP。

## 03 研究问题

- **具体问题**：如何准确预测非编码区SNP对TF结合的影响（即等位基因特异性结合，ASB）？
- **为何重要**：非编码区突变可通过破坏TF结合导致疾病，但我们对TF结合模式及其突变效应的理解仍有限。准确预测ASB有助于解析疾病病因和处理GWAS数据。
- **现有方法不足**：
  - 现有工具（如MotifbreakR、atSNP）基于PWM，假设结合位点各位置核苷酸统计独立，丢失了位置间关联信息。
  - 深度学习模型需要大量训练数据，用户难以自行生成。
  - 现有工具对ASB事件的召回率低，许多真实ASB未被识别。
- **精确研究问题**：能否利用PBM E-score谱（保留位置间关联的原始结合数据）作为CNN输入，比基于PWM的方法更准确地预测SNP对TF结合的影响？

## 04 背景与发展脉络

**脉络标注**：以下脉络基于本文引言及讨论部分，属「仅本文框架」，未经外部系统核验。

1. **PWM时代**：TF结合位点用位置权重矩阵（PWM）建模，假设各位置独立。代表工具：MotifbreakR、atSNP。局限：忽略位置间关联信息，对ASB召回率低。
2. **深度学习时代**：CNN等模型直接学习DNA序列特征，但需要大量训练数据，且多基于ChIP-seq数据，受染色质可及性等间接因素干扰。
3. **PBM数据利用**：PBM实验可测量TF对所有k-mer（如8-mer）的结合亲和力（E-score），保留了序列位置间的关联信息，但此前未被用于SNP效应预测。
4. **本文位置**：首次将PBM E-score谱与FIMO PWM得分结合作为CNN输入，利用PBM数据的丰富信息同时保留PWM的位点定位能力，在ASB预测上超越现有工具。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PWM方法忽略位置间关联 | MotifbreakR和atSNP对ASB召回率低 | PWM假设各位置核苷酸独立，丢失了TF结合中位置间协同效应信息 | Discussion: "PWM...assuming statistical independence from all other positions within the binding site. This will lead to loss of information" |
| 现有工具ASB召回率低 | 大量真实ASB事件未被识别 | 基于PWM的评分方法对结合变化不敏感 | Benchmarking结果：SNPeBoT召回率显著高于MotifbreakR和atSNP（Table 1） |
| 深度学习模型训练数据需求高 | 用户难以自行微调模型 | 需要大量标记数据，且ChIP-seq数据受间接因素干扰 | Introduction: "may also require...fine tuning before and therefore necessitate the generation of large amounts of training data" |
| ChIP-seq数据受间接因素干扰 | ASB可能由染色质可及性、LD等间接因素导致 | 非直接由序列变异引起的结合变化被误标为ASB | Methods: 过滤Non Concordant数据（34,374→9,215） |
| 工具安装复杂 | 现有工具对一般用户不友好 | 依赖R包及复杂依赖 | Introduction: "retain prohibitive installation or implementation requirements for the general user" |

## 06 核心思想

### 1) 表面方法
训练一个CNN模型，输入为：(a) 16个PBM E-score值（覆盖SNP位点±7bp的8-mer滑动窗口），(b) 2个FIMO PWM扫描得分（参考和替代等位基因各一个），输出为三分类（gain/loss/no-change）。

### 2) 核心洞察
- **PBM E-score保留了PWM丢失的信息**：PWM将结合位点压缩为独立位置权重，而PBM E-score直接测量了TF对所有8-mer序列的实际结合亲和力，隐含了位置间协同效应。
- **E-score谱作为"序列嵌入"**：将SNP周围的序列上下文转化为E-score谱，相当于用实验测量的结合亲和力对序列进行编码，比one-hot编码或PWM更接近TF的实际结合偏好。
- **FIMO作为后验过滤器**：CNN预测后，用FIMO在参考/替代序列上扫描PWM命中，过滤掉无PWM结合位点的SNP，减少假阳性。

### 3) 可能的普适教训 [Analysis]
- **实验数据作为特征而非标签**：本文不是用深度学习从序列预测结合（如DeepSEA），而是将实验测量的结合亲和力（E-score）作为输入特征。这种"实验引导的特征工程"思路可迁移到其他结合机制预测任务。
- **多数据源互补**：PBM（体外、定量）与ChIP-seq（体内、定性）的互补使用，类似于将体外生化数据与体内功能数据结合，可提高预测的生物学相关性。
- **后验过滤的实用价值**：深度学习预测后加一个可解释的生物学过滤器（PWM扫描），在保持召回率的同时提高精度，这种混合策略值得借鉴。

## 07 方法总览

- **输入**：
  - SNP信息（参考/替代等位基因，或VCF/RSID格式）
  - 目标TF名称
  - 序列上下文（SNP位点±7bp，共15bp核心区域）
- **输出**：三分类预测（gain/loss/no-change），附带概率
- **特征构建流程**：
  1. 从CISBP数据库获取目标TF的PWM和PBM E-score数据
  2. 用FIMO扫描PWM于参考/替代序列，获取最佳命中得分（2个特征）
  3. 提取所有包含SNP位点的8-mer（共16个），从PBM数据中检索对应E-score
  4. 滑动窗口平均，将16个E-score压缩为30个（参考/替代各15个）
  5. 将32个特征（30个E-score + 2个FIMO得分）重塑为8×4矩阵
- **模型架构**：
  - 输入：(8,4,1) 特征矩阵
  - 2个2D卷积层 + 池化层，再2个卷积层 + 池化层
  - Flatten → BatchNorm → 2个Dense层 → Softmax三分类
  - 超参数（卷积核数、Dense单元数）用Keras Tuner优化，目标为验证集准确率
- **训练数据**：
  - 正样本：ADASTRA数据库的ASB事件（gain/loss），经Non Concordant过滤后9,215个
  - 负样本：GTRD数据中无显著ASB的SNP，8,996个
  - 总计18,211个数据点，113个TF
  - 训练/验证/测试划分：70%最小类别（gain）用于训练，10%验证（934样本），测试集8,400样本
- **后验过滤**：FIMO扫描，无PWM命中的SNP标记为no-change
- **工具**：TensorFlow 2.13.0，SBILib（预处理），FIMO（MEME套件），genopyc（序列获取）

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| PBM E-score特征提取 | 从CISBP数据库检索SNP周围8-mer的E-score | 提供实验测量的结合亲和力，保留位置间关联信息 | 输入：SNP序列、TF；输出：16个E-score | Methods: "for every 8-mer that includes the SNP we can derive an E-score" | [预期] 移除后模型退化为仅依赖PWM特征，可能丢失位置协同信息，准确率下降（未做消融实验） |
| 滑动窗口平均 | 将16个E-score压缩为30个（±7bp） | 平滑E-score谱，匹配序列长度 | 输入：16个E-score；输出：30个平均值 | Methods: "sliding window averages the E-scores assigned to each Nucleotide" | [预期] 移除后特征维度不匹配，需调整网络结构 |
| FIMO PWM扫描 | 获取参考/替代序列的PWM最佳命中得分 | 提供序列特异性结合位点定位信息 | 输入：序列、PWM；输出：2个得分 | Methods: "the PWM with the best scoring FIMO hit" | [预期] 移除后模型失去位点定位能力，可能增加假阳性 |
| CNN分类器 | 从特征矩阵学习三分类 | 捕捉特征间的非线性关系 | 输入：(8,4,1)矩阵；输出：三分类概率 | Results: 81%准确率（无后验过滤） | [实测] 无后验过滤时准确率81%，加入后85% |
| 后验FIMO过滤 | 无PWM命中的SNP标记为no-change | 过滤间接因素导致的ASB | 输入：CNN预测、FIMO命中；输出：修正后预测 | Results: 准确率从81%提升至85% | [实测] 移除后准确率下降4个百分点，但召回率从62%降至55%（后验过滤降低了召回率） |
| 数据预处理（SBILib） | TF-DBD匹配、序列获取 | 确保TF有对应的PBM数据 | 输入：原始SNP/TF；输出：可训练特征 | Methods: "This preprocessing step was handled by SBILib" | [预期] 移除后无法生成E-score特征，模型不可用 |

## 09 关键公式符号

本文未提供明确的数学公式。核心概念符号如下：

- **E-score**：PBM实验测定的TF对8-mer序列的结合富集分数，范围通常为[-0.5, 0.5]，正值表示结合增强。
- **FIMO score**：PWM扫描序列得到的对数似然比得分，反映序列与PWM的匹配程度。
- **特征矩阵**：8×4矩阵，由30个E-score平均值和2个FIMO得分经变换得到（具体变换方式原文未详述）。
- **三分类输出**：P(gain), P(loss), P(no-change)，经Softmax归一化。

**不适用**：本文无需要单独列出的数学公式。

## 10 实验设计与证据链

**数据集与评测协议**：
- **训练数据**：ADASTRA ChIP-seq ASB事件（9,215个，过滤后）+ GTRD对照（8,996个），共18,211个，113个TF
- **测试集**：8,400个SNP（gain:1,140, loss:1,822, no-change:5,438）
- **验证集**：934个样本（10%）
- **基准工具**：MotifbreakR（相对熵方法，阈值10⁻⁴）、atSNP（q-value < 0.05）
- **指标**：准确率（accuracy）、ASB召回率（recall，即gain+loss中被正确识别的比例）、ROC AUC（二分类，gain/loss vs no-change）
- **外部数据测试**：eY1H（Enhanced Yeast 1 Hybrid）体外实验数据、AlleleDB数据库

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|-------------------|------|
| CNN holdout测试（无后验过滤） | 模型能预测ASB | 8,400测试样本 | 准确率81%，ASB召回率62% | CNN能从E-score特征学习ASB预测 | 未与基准工具在此条件下对比 | Results: "Holdout testing...81% accuracy at 62% ASB recall" |
| 完全未见SNP测试 | 模型泛化到新SNP | 移除训练中见过的SNP | 准确率80%，召回率61% | 模型非记忆训练数据 | 性能略降，但差异小 | Results: "unseen SNPs regardless of the TF...80%...61%" |
| 未见TF测试 | 模型泛化到新TF | 移除训练中见过的TF | 准确率83% | 模型学到TF结合的一般规律 | 样本量可能较小 | Results: "TF not included in training...83%" |
| 后验过滤效果 | FIMO过滤提升精度 | 不同p值阈值 | 最佳准确率85%，召回率55% | 后验过滤提升准确率 | 召回率下降，需权衡 | Results: "highest accuracy SNPeBoT implementation (85%)...55%" |
| 与MotifbreakR对比 | SNPeBoT优于现有工具 | 各自最佳阈值 | SNPeBoT准确率和召回率均更高 | E-score+CNN优于纯PWM方法 | 未报告统计显著性检验 | Table 1, Fig 4 |
| 与atSNP对比 | SNPeBoT优于现有工具 | 各自最佳阈值 | SNPeBoT准确率和召回率均更高 | 同上 | 同上 | Table 1, Fig 4 |
| ROC AUC对比 | SNPeBoT判别能力更强 | 二分类（ASB vs no-change） | SNPeBoT AUC高于两者 | 判别能力更强 | 仅二分类，非三分类 | Fig 6 |
| eY1H外部数据测试 | 泛化到体外数据 | 仅考虑模型预测ASB的案例 | 准确率70%，ASB召回率56%，预测ASB中88%准确 | 模型可迁移到体外数据 | 性能下降，且eY1H数据仅含正样本 | Results: "Generalizability" |
| AlleleDB测试 | 跨数据源泛化 | p值阈值0.001 | 未提供具体数值 | 未明确 | 未提供 | Supplementary |

## 11 结论正确解读

- **任务范围**：仅适用于有PBM E-score数据的TF（113个TF），且SNP位于TF结合位点附近（±7bp窗口内）。对于无PBM数据的TF，模型无法预测。
- **Oracle/真值输入**：训练标签来自ADASTRA的ChIP-seq ASB数据，该数据本身受细胞类型、实验条件影响，且经过Non Concordant过滤（排除可能由间接效应导致的ASB）。因此模型预测的是"直接由序列变异导致的结合变化"。
- **端到端状态**：非端到端。需要外部工具（SBILib、FIMO、genopyc）进行预处理和后处理。用户需提供SNP和TF信息，模型输出三分类概率。
- **算力成本**：未报告训练时间或硬件需求。推理阶段为轻量级CNN，成本低。
- **历史数据依赖**：训练数据来自ADASTRA（ChIP-seq）和CISBP（PBM），均为已发表数据。模型性能受这些数据质量限制。
- **模型依赖**：CNN结构简单，但特征工程（E-score谱）是关键。若CISBP数据库更新，需重新提取特征。
- **最难情形**：eY1H体外数据上性能下降（70% vs 85%），说明体内外数据差异仍是挑战。此外，对训练中未见过的TF家族，性能可能不稳定。
- **群体/领域边界**：仅覆盖113个TF，主要为人类TF。对非人类物种或新型TF，需验证。
- **不确定性**：未报告置信区间或不确定性量化。三分类概率未校准。
- **有边界的复述**：SNPeBoT在113个人类TF、18,211个SNP的训练数据上，对ChIP-seq来源的ASB预测准确率达85%（含后验过滤），优于MotifbreakR和atSNP；在eY1H体外数据上准确率70%。该性能仅限于有PBM数据的TF，且依赖CISBP数据库的E-score质量。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 依赖PBM数据可用性 | 仅能预测有PBM E-score数据的TF | 计划将方法扩展到无PBM数据的TF | Discussion: "tools such as SNPeBoT relying on data from PBM...are limited by data availability" |
| 未纳入蛋白质互作信息 | 模型仅使用序列和E-score，未考虑蛋白-DNA互作的其他因素 | 计划结合ModCRE的统计势能，纳入蛋白质互作信息 | Discussion: "incorporating information important to TF binding other than the target sequence such as the sequence environment and protein interaction landscape" |
| eY1H数据性能下降 | 体外数据上准确率从85%降至70% | 未明确 | Results: "Generalizability"部分 |
| 后验过滤降低召回率 | 最高准确率配置下召回率仅55% | 未明确 | Results: "yielded a lower ASB recall rate (55%)" |

**作者提及的相关约束**（非正式局限）：
- 训练数据中gain/loss/no-change类别不平衡（no-change占多数），可能影响模型对少数类的预测。
- 对VCF/RSID输入，序列转换依赖参考基因组版本（hg38），不同版本可能影响结果。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| 特征矩阵构建细节不透明 | 30个E-score + 2个FIMO得分如何变换为8×4矩阵未详细说明 | 影响可复现性；不同变换方式可能显著影响性能 | 联系作者获取代码；检查GitHub实现 | Methods: "transformed into a 8×4 matrix" 未给出具体变换 |
| 训练/测试划分可能泄漏 | 测试集允许SNP在训练中出现过（仅TF不同），可能高估泛化能力 | 实际应用中SNP是新的，模型性能可能低于报告值 | 要求作者提供严格SNP-level划分的结果 | Methods: "SNPs were allowed even when they occurred in the training data set if the TF applied was unique" |
| 与基准工具比较公平性存疑 | MotifbreakR和atSNP使用默认阈值，而SNPeBoT在9个阈值中选择最佳 | 可能高估SNPeBoT优势 | 要求所有工具在多个阈值下比较，或使用无阈值指标（如AUC） | Benchmarking部分：SNPeBoT多阈值测试，基准工具单阈值 |
| 后验过滤的"no-change"标记逻辑 | FIMO无命中即标记为no-change，可能将真实ASB（但PWM不匹配）误分类 | 可能人为提高准确率（因为no-change占多数） | 分析被FIMO过滤的样本中gain/loss分布 | Methods: "SNPs without hits...were labelled as no-change" |
| 未报告类别平衡处理 | 训练集no-change占多数（8,996/18,211），CNN可能偏向多数类 | 影响gain/loss的召回率 | 检查混淆矩阵；要求报告各类别F1分数 | 数据分布：no-change 8,996 vs gain 4,987 vs loss 4,228 |
| eY1N测试仅用正样本 | eY1H数据只含ASB事件，无法评估假阳性率 | 70%准确率可能虚高 | 在包含负样本的体外数据上测试 | Results: "considering only cases where the model predicted ASB" |
| 未与其他深度学习方法比较 | 仅与PWM方法比较，未与DeepSEA、Basenji等深度学习模型对比 | 无法判断E-score特征是否优于纯序列深度学习 | 在相同数据上训练序列CNN对比 | Benchmarking部分仅对比MotifbreakR和atSNP |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **实验数据作为特征（而非标签）的范式**：本文用PBM E-score作为CNN输入特征，而非仅作为训练标签。这提示在TF–DNA结合预测中，体外定量结合数据（如PBM、SELEX、HT-SELEX）可作为"实验先验"嵌入模型输入，弥补纯序列特征的不足。可迁移：在蛋白质-DNA对接或MD模拟中，将实验结合亲和力作为偏置项或特征通道。

2. **E-score谱作为序列的"结合感知"编码**：将SNP周围序列转化为E-score谱，相当于用TF的实际结合偏好对序列进行嵌入。这比one-hot编码更紧凑且生物学可解释。可迁移：设计"结合感知"的序列嵌入层，用于其他TF–DNA结合预测任务。

3. **多数据源互补策略**：PBM（体外、定量、高通量）与ChIP-seq（体内、定性、低通量）的互补使用，是处理体内外数据差异的有效策略。可迁移：在MD模拟中，用体外实验数据（如ITC、SPR）校准力场参数，再用体内数据（如ChIP-seq）验证。

4. **后验可解释过滤器**：CNN预测后加FIMO扫描作为生物学合理性检查，在保持深度学习表达能力的同时增加可解释性。可迁移：在AI预测TF–DNA结合后，用PWM或位置权重矩阵作为后验验证，过滤生物学不合理的预测。

5. **数据过滤的重要性**：ADASTRA的Non Concordant过滤（排除间接效应导致的ASB）是提高训练数据质量的关键步骤。可迁移：在构建TF–DNA结合训练集时，需区分直接结合与间接结合（如通过辅因子介导），避免标签噪声。

6. **TF-DBD匹配策略**：用BLAST将TF序列与PBM实验的DNA结合域匹配（≥70%序列同一性），扩展了可预测的TF范围。可迁移：在缺乏直接实验数据时，用同源TF的PBM数据作为替代，但需注意同一性阈值对预测可靠性的影响。

## 15 与已有知识连接

- **与PWM方法的连接**：本文直接对比MotifbreakR和atSNP，两者均基于PWM。本文的改进在于引入PBM E-score，验证了"PWM丢失位置间关联信息"的假设。这与Berg & von Hippel（1987）的PWM理论基础形成对照，提示位置独立性假设的局限。

- **与深度学习预测TF结合的连接**：与DeepSEA（Zhou & Troyanskaya, 2015）、Basenji（Kelley et al., 2018）等从序列直接预测调控功能的模型不同，本文聚焦于SNP的等位基因效应，且输入包含实验测量值。这类似于"物理信息驱动"的深度学习思路。

- **与PBM数据分析的连接**：本文利用CISBP数据库的E-score，与gkm-SVM（Alipanahi et al., 2015）、DeepBind（Alipanahi et al., 2015）等基于PBM数据训练序列模型的方法互补。本文不是从PBM学习结合模型，而是直接用E-score作为特征。

- **与TF–DNA结合机制的联系**：本文的E-score特征隐含了TF对8-mer序列的结合偏好，这与TF–DNA识别的结构机制（如氢键、疏水作用）相关。可进一步与结构信息（如PDB中的TF–DNA复合物）结合，探索序列-结构-结合亲和力的映射关系。

- **与MD模拟的潜在连接**：本文的预测可生成SNP对TF结合影响的假设，这些假设可用MD模拟或对接方法验证。反之，MD模拟可提供E-score无法捕捉的构象动态信息，两者互补。

- **与GWAS分析的连接**：本文的ASB预测可用于优先排序GWAS中的非编码变异，与RegulomeDB、FunSeq2等工具互补，但本文提供了实验数据驱动的深度学习方案。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：E-score引导的TF–DNA结合结构预测
   - **来源局限/观察**：本文用E-score作为CNN特征，但未利用TF–DNA复合物的三维结构信息。E-score反映结合亲和力，但无法解释结合的构象基础。
   - **核心假设**：将E-score与AlphaFold3或RoseTTAFold预测的TF–DNA复合物结构结合，可提高SNP效应预测的准确性和可解释性。
   - **初步方法**：对每个SNP，用结构预测工具生成参考/替代等位基因的TF–DNA复合物结构，提取界面残基接触、氢键等结构特征，与E-score特征融合输入CNN或图神经网络。
   - **验证方式**：在ADASTRA和eY1H数据上对比融合模型与SNPeBoT的性能；分析结构特征对预测的贡献。
   - **创新状态**：unverified

2. **候选名称**：基于MD模拟的SNP对TF–DNA结合动力学影响预测
   - **来源局限/观察**：SNPeBoT是静态预测，未考虑TF–DNA结合的动态过程。SNP可能通过影响结合动力学（如结合速率、解离速率）而非仅结合亲和力来影响功能。
   - **核心假设**：SNP导致的结合自由能变化（ΔΔG）与MD模拟的结合动力学参数（如驻留时间）相关，可作为ASB预测的补充特征。
   - **初步方法**：选取SNPeBoT预测的gain/loss SNP子集，用MD模拟（如MARTINI粗粒化或全原子）计算参考/替代等位基因的TF–DNA结合自由能差和动力学参数，训练一个元模型整合SNPeBoT输出和MD特征。
   - **验证方式**：在独立测试集上比较元模型与SNPeBoT的AUC；分析MD特征对预测的增量贡献。
   - **创新状态**：unverified

3. **候选名称**：跨物种TF–DNA结合特异性预测的迁移学习
   - **来源局限/观察**：SNPeBoT仅覆盖113个人类TF，对非人类物种或新型TF无法预测。PBM数据在物种间分布不均。
   - **核心假设**：TF–DNA结合特异性的序列编码在进化上保守，可通过迁移学习从数据丰富的物种（人类、小鼠）迁移到数据稀缺的物种。
   - **初步方法**：用人类PBM E-score预训练CNN，然后用目标物种少量ASB数据微调；或利用TF氨基酸序列的进化保守性作为辅助特征。
   - **验证方式**：在果蝇、线虫等模式生物的ASB数据上测试迁移学习性能；对比直接训练与迁移学习的差异。
   - **创新状态**：unverified

4. **候选名称**：SNP对TF–DNA结合与染色质可及性联合效应的多任务学习
   - **来源局限/观察**：SNPeBoT过滤了Non Concordant数据（可能由染色质可及性等间接因素导致），但实际中SNP可能同时影响TF结合和染色质状态。
   - **核心假设**：联合建模TF结合和染色质可及性可提高对功能性非编码变异的识别。
   - **初步方法**：构建多任务CNN，共享序列编码层，分别预测ASB和染色质可及性变化（用ATAC-seq数据）；比较多任务与单任务性能。
   - **验证方式**：在包含匹配ChIP-seq和ATAC-seq的数据集上评估；分析共享表示是否捕捉到TF结合与染色质状态的协同关系。
   - **创新状态**：unverified

5. **候选名称**：基于E-score的TF–DNA结合协同效应建模
   - **来源局限/观察**：SNPeBoT处理单个SNP，但实际中多个SNP可能协同影响TF结合。E-score的8-mer窗口无法捕捉长距离协同效应。
   - **核心假设**：多个SNP的联合效应可通过E-score谱的组合特征建模，且存在非线性协同。
   - **初步方法**：扩展输入窗口至±20bp，用注意力机制捕捉SNP间的长距离依赖；或在多个SNP位点同时突变时，用E-score谱的差异作为特征。
   - **验证方式**：在含多个SNP的调控区域数据上测试；对比单SNP与多SNP模型的预测性能。
   - **创新状态**：unverified