## 01 基本信息
- **标题**：Modeling and designing enhancers by introducing and harnessing transcription factor binding units
- **作者与单位**：Li, Jiaqi; Zhang, Pengcheng; Xi, Xi; Liu, Liyang; Wei, Lei; Wang, Xiaowo（清华大学，推测；未在摘要中明确列出单位）
- **期刊/预印本平台**：Nature Communications
- **年份**：2025-02-09
- **论文类型**：研究论文（含实验验证）
- **领域**：基因调控、增强子设计、转录因子结合、深度学习
- **关键词**：enhancer design, transcription factor binding unit (TFBU), deep learning, TFBS context, MPRA
- **DOI/arXiv 号**：10.1038/s41467-025-56749-2
- **代码**：未提供
- **数据**：补充数据集 1-11（含 MPRA 数据、模型训练数据等）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦 TF–DNA 结合机制中的核心问题——TFBS 侧翼序列（context）对 TF 结合及增强子活性的定量影响。方法上采用深度学习（DenseNet-LSTM）建模 TFBS-context 的序列偏好，并结合遗传算法进行增强子序列设计。与课题方向（蛋白质-DNA 互作 × AI/物理模拟）高度相关，属于「AI 驱动的 TF 结合偏好建模与序列设计」路线，不涉及物理模拟（MD/对接）。

## 02 一句话总结
本文提出转录因子结合单元（TFBU）概念，用深度学习模型量化 TFBS 侧翼序列对 TF 结合和增强子活性的贡献，并基于此开发 DeepTFBU 工具包，通过 MPRA 实验验证了设计的增强子活性可被显著调控（单 TFBU 平均提升 >20 倍，多 TFBU 设计提升 >30 倍）。

## 03 研究问题
- **具体问题**：TFBS 侧翼序列（context）如何定量影响 TF 结合和增强子活性？如何利用这种影响进行理性的增强子设计？
- **为什么重要**：传统模型仅关注核心 TFBS 基序，但基因组中相同基序的 TF 结合行为差异显著，说明 context 序列起关键作用。理解并利用这一机制对合成增强子设计、基因治疗和基因调控网络建模具有重要意义。
- **现有方法不足**：TFBS 基序可显式描述（PWM/PPM），但 context 序列特征复杂、隐式，缺乏定量建模方法；已有增强子设计方法多聚焦于 TFBS 排列组合，未系统考虑 context 序列的贡献。
- **精确研究问题（Can...?）**：Can deep learning models quantitatively capture TF-specific and cell type-specific preferences of TFBS-context sequences, and can these models guide the design of enhancers with desired activity levels?

## 04 背景与发展脉络
- **阶段一：TFBS 基序为中心**。早期研究认为 TF 结合主要由核心基序决定（5-20 bp），代表性方法为 PWM/PPM 匹配打分。局限：无法解释相同基序在不同基因组位置的结合差异。
- **阶段二：context 序列作用被发现**。研究发现侧翼序列可通过多种机制影响 TF 结合：短串联重复序列直接与 TF 互作、DNA 形状（MGW、roll 等）影响结合、弱结合位点协同、非 B 型 DNA 结构（R-loop、G-四链体）等。局限：这些特征零散、难以统一量化。
- **阶段三：深度学习用于调控序列建模**。已有工作用 CNN、LSTM 等模型预测 TF 结合、染色质可及性等（如 DeepSEED、Enformer 等），但多用于预测而非设计，且未将 context 序列作为独立可设计的模块。
- **本文位置**：提出 TFBU 概念，将核心 TFBS 与 context 序列整合为可量化的功能单元；用深度学习分别建模 TF 特异性和细胞类型特异性的 context 偏好；将模型与遗传算法结合，实现从「预测」到「设计」的闭环。属于「模块化增强子建模 + AI 引导设计」路线。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| context 序列作用难以量化 | 相同 TFBS 基序在不同基因组位置结合差异大，但缺乏定量指标 | context 序列特征复杂、隐式，包含 DNA 形状、弱结合位点、结构特征等多重因素 | Introduction 第 2 段；Results 图 2 |
| 传统增强子设计忽略 context | 仅优化 TFBS 排列组合，设计空间受限 | 缺乏对 context 序列贡献的建模方法 | Introduction 第 3 段 |
| 细胞类型特异性难以实现 | 同一 TF 在不同细胞类型中结合偏好不同，但核心基序相同 | context 序列偏好可能反映细胞类型特异的共因子或染色质环境 | Results 图 3；CSpTFBU 模块 |
| 多 TFBS 协同优化困难 | 多个 TFBS 及其 context 可能重叠，单独优化每个 TFBU 无法保证全局最优 | 需要联合优化所有 TFBU 的 context 序列 | Results 图 4；DeMulTFBU 模块 |
| 模型可能学到虚假的 TFBS 特征 | 优化后的 context 序列可能包含其他明显 TFBS，而非真正的 context 效应 | 深度学习模型可能捕捉到 TFBS 共现模式而非 context 本身 | Results 图 2c 过滤策略；Methods 节 |

## 06 核心思想
1. **表面方法**：提出 TFBU（TFBS + 侧翼 context）作为增强子的基本功能单元；用 DenseNet-LSTM 深度学习模型分别对每个 TF 训练 context 分类器（正样本：ChIP-seq 峰内 context；负样本：可及染色质区非结合 context）；用遗传算法以模型输出为适应度函数优化 context 序列；通过 MPRA 实验验证设计序列的增强子活性。
2. **核心洞察**：TFBS 侧翼序列对 TF 结合和增强子活性的贡献是 TF 特异性和细胞类型特异性的，且这种贡献可以被深度学习模型定量捕捉并用于序列设计。context 序列的作用不依赖于额外 TFBS 的存在，而是通过 DNA 形状、弱结合位点、结构特征等隐式机制实现。
3. **可能的普适教训 [Analysis]**：将「功能单元」概念引入调控序列建模（类似蛋白质结构域），可有效降低序列设计的复杂度；深度学习模型不仅能用于预测，还能作为可微/可优化的目标函数指导序列设计；模块化分解（TFBS + context）与联合优化（多 TFBU）的结合是处理复杂序列设计问题的有效策略。

## 07 方法总览
- **输入**：DNA 序列（168 bp TFBU，核心 TFBS 居中，两侧为 context）
- **输出**：TFBS-context 匹配分数（0-1 二分类概率）；设计的增强子序列
- **模块**：
  1. **数据构建**：从 ENCODE ChIP-seq（198 TF，HepG2；部分 K562）提取正样本（峰内 context），从可及染色质区提取负样本，平衡 GC 含量和组蛋白修饰状态
  2. **深度学习模型**：DenseNet-LSTM 架构（1D CNN + 池化 → 双向 LSTM → Dense Block），输入 one-hot 编码（核心 TFBS 掩码为 N），输出 context 匹配分数
  3. **遗传算法**：以模型输出为适应度，对 context 序列进行突变和重组优化，保持核心 TFBS 不变
  4. **MPRA 验证**：构建质粒文库，转染 HepG2/K562 细胞，测量增强子活性
  5. **增强子建模框架**：将增强子解耦为多个 TFBU 的线性组合，用线性回归预测活性
- **训练**：每个 TF 单独训练模型；10 个模型平均以减少随机性
- **反馈回路**：模型预测 → 遗传算法优化 → 实验验证 → （可选）模型更新
- **假设**：context 序列对 TF 结合的影响可通过序列本身预测；ChIP-seq 结合峰反映功能性 TF 结合；MPRA 活性可反映增强子功能

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 数据构建与平衡 | 生成正负样本，平衡 GC 和组蛋白修饰 | 避免模型学习到简单序列组成或染色质状态而非 context 偏好 | 输入：ChIP-seq 峰、ATAC-seq 峰；输出：平衡的 context 数据集 | Methods 节；图 1b | 预期：模型可能学习到 GC 含量或染色质标记的混淆信号，导致 context 效应被高估 [预期效应] |
| DenseNet-LSTM 模型 | 提取 context 序列的局部和长程特征，输出匹配分数 | CNN 捕捉局部 motif，LSTM 捕捉长程依赖，Dense Block 整合特征 | 输入：one-hot context 序列（168 bp）；输出：0-1 分数 | Methods 节；图 1c；Supplementary Fig. 1 | 实测：模型 AUC 显著 >0.5（0.56-0.96），说明 context 信息可被捕捉；移除 LSTM 预期降低长程依赖建模能力 [预期效应] |
| 遗传算法优化 | 在保持核心 TFBS 不变的前提下优化 context 序列 | 模型可评估任意 context，遗传算法可高效搜索序列空间 | 输入：初始序列 + 模型；输出：优化后的 context 序列 | Methods 节；图 1c | 实测：优化后增强子活性显著提升（>20 倍），说明优化有效 |
| MPRA 实验验证 | 测量设计序列的增强子活性 | 验证模型预测与真实功能的一致性 | 输入：质粒文库；输出：RNA/DNA 比值（活性） | Results 图 2-4；Methods 节 | 实测：验证了模型预测的有效性；移除实验验证则无法确认模型是否真正捕捉功能相关特征 |
| 增强子解耦框架 | 将增强子活性建模为多个 TFBU 分数的线性组合 | 实现任意长度增强子的建模与优化 | 输入：增强子序列；输出：预测活性 | Results 图 5；ModOptTFBU 模块 | 实测：线性模型性能优于深度学习基线（PCC 0.7942 vs 0.77）；移除该框架则无法处理长增强子 |
| 细胞类型特异性模型 | 训练 HepG2 vs K562 判别模型 | 实现细胞类型特异的增强子设计 | 输入：两种细胞类型的 context 数据；输出：特异性分数 | Results 图 3；CSpTFBU 模块 | 实测：设计的序列在预期细胞类型中活性显著更高（>7 倍） |

## 09 关键公式符号
1. **归一化 read count**（MPRA 数据处理）：
   \[
   \text{Normalized read count} = \frac{\text{barcode read count}}{\text{total sample reads}} \times 10^6
   \]
   符号：barcode read count（某条形码的 reads 数），total sample reads（样本总 reads 数）

2. **增强子活性**（MPRA）：
   \[
   \text{Enhancer activity} = \frac{\sum(\text{RNA counts for enhancer barcodes})}{\sum(\text{DNA counts for enhancer barcodes})}
   \]
   符号：RNA/DNA counts（对应条形码的 RNA/DNA 测序 reads 数）

3. **信息含量**（PPM 构建）：
   \[
   \log_2 N - \left(-\sum_{n=1}^{N} p_n \log_2 p_n\right)
   \]
   其中 \(N=4\)（四种碱基），\(p_n\) 为第 n 种碱基在该位置的概率。用于筛选 PPM 中信息含量较高的位置。

4. **核心 TFBS 匹配分数**：
   \[
   S_{\text{core}} = \frac{\prod_{i=1}^{L} \text{PPM}_{i(C_i)}}{\prod_{i=1}^{L} \max(\text{PPM}_i)}
   \]
   其中 \(L\) 为 PPM 长度，\(C_i\) 为位置 i 的碱基，\(\text{PPM}_{i(C_i)}\) 为对应碱基的概率，\(\max(\text{PPM}_i)\) 为该位置最大概率。用于在序列中定位核心 TFBS。

5. **遗传算法优化目标**（多 TFBU 联合优化）：
   \[
   \text{Seq} = \arg\max_{\text{Seq}} \text{Metric}(\text{Seq})
   \]
   其中 Metric 为任务特定目标函数（如单 TFBU 分数、多 TFBU 分数之和、细胞类型特异性分数）。

6. **细胞类型特异性优化目标**（以 HepG2 特异性为例）：
   \[
   \text{Metric}(\text{Seq}) = \text{Score}_{\text{HepG2}}(\text{TFBS\_context}) - \text{Score}_{\text{K562}}(\text{TFBS\_context}) + \text{Score}_{\text{specific}}(\text{TFBS\_context})
   \]
   符号：Score_HepG2/K562 为对应细胞类型模型的输出，Score_specific 为 HepG2 vs K562 判别模型的输出。

7. **多细胞类型泛化目标**：
   \[
   \text{Metric}(\text{Seq}) = \frac{1}{n}\sum_{i=1}^{n}\text{Score}_{\text{active\_type}_i}(\text{TFBS\_context}) - \frac{1}{m}\sum_{j=1}^{m}\text{Score}_{\text{mute\_type}_j}(\text{TFBS\_context}) + \text{Score}_{\text{specific}}(\text{TFBS\_context})
   \]
   符号：active_types（期望表达的细胞类型集合，n 个），mute_types（不期望表达的细胞类型集合，m 个）。

## 10 实验设计与证据链
- **数据集**：
  - ChIP-seq：ENCODE 数据库，198 TF（HepG2），部分 TF 有 K562 数据
  - ATAC-seq：HepG2 可及染色质区域（用于负样本）
  - MPRA 实验：36,000+ 设计序列，HepG2 和 K562 细胞系
  - 对照组：已知无增强子活性的基因组序列（空白对照）
- **指标**：AUC（模型分类性能）、增强子活性（RNA/DNA 比值）、fold change（设计序列 vs 对照）
- **基线**：随机/基因组 context 序列、未优化序列、深度学习模型直接预测（DeepSEED）
- **评测协议**：MPRA 实验（3 个生物学重复），流式细胞术验证细胞类型特异性

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 单 TFBU 优化（3 TF） | 设计 context 可调控增强子活性 | 优化 vs 对照（无 core TFBS 或随机 context） | 平均提升 >20 倍（ELF1、HNF1A、HNF4A） | context 序列对增强子活性有显著贡献 | 未证明对所有 TF 均有效 | Results 图 2a |
| 分数-活性相关性 | 模型分数可预测增强子活性 | 不同分数的 context 序列 vs 实测活性 | PCC 0.81-0.97（不同 TF） | 模型捕捉到功能相关特征 | 相关性不等于因果性 | Results 图 2b-d |
| 过滤明显 TFBS 后 | context 效应不依赖额外 TFBS | 过滤含明显 TFBS 的序列后重新分析 | PCC 仍显著（HNF4A 从 0.68 提升至 0.96） | context 效应独立于额外 TFBS | 未排除弱 TFBS 或非经典 motif 的贡献 | Results 图 2c |
| 118 TF 筛选 | context 效应具有普遍性 | 117 TF 的优化 context vs 对照 | 82.9%（97/117）TF 显著提升 | context 效应是普遍现象 | 部分 TF 效应不显著，机制可能不同 | Results 图 2e |
| 细胞类型特异性设计 | 可设计细胞类型特异的增强子 | HepG2 特异性 vs K562 特异性设计 | 预期细胞类型中活性高 7.63-27.43 倍 | context 序列可编码细胞类型特异性 | 仅验证 4 个 TF，未覆盖所有类型 | Results 图 3 |
| 多 TFBU 联合优化 | 联合优化优于单 TFBU 叠加 | 8 TFBS 联合优化 vs 基线（串联重复） | 平均提升 >30 倍，最高 >100 倍 | 联合优化可有效协调多个 TFBU | 未与所有现有方法对比 | Results 图 4 |
| CMV 增强子优化 | 可优化天然增强子 | 优化 CMV 增强子 vs 原始 | 活性提升 1.41-1.59 倍 | 框架可应用于天然增强子 | 仅测试一个增强子 | Results 图 5 |

## 11 结论正确解读
- **任务范围**：本文聚焦于增强子序列设计，通过 TFBU 概念将 TFBS 与 context 整合。结论限于增强子活性调控，不涉及 TF 结合动力学、三维结构或体内染色质环境。
- **oracle/真值输入**：模型训练使用 ChIP-seq 结合峰作为正样本标签，这是「结合与否」的二元标签，不包含结合强度或动力学信息。MPRA 活性测量反映转录输出，而非直接测量 TF 结合。
- **端到端状态**：方法链为「序列 → 模型分数 → 设计序列 → 实验验证」，但模型本身不是端到端的增强子活性预测器（仅预测 context 对 TF 结合的贡献），最终活性由多个 TFBU 分数线性组合估计。
- **算力成本**：未报告具体训练成本；模型为 DenseNet-LSTM，规模中等，可推断在单 GPU 上可训练。
- **历史数据依赖**：依赖 ENCODE ChIP-seq 数据质量；不同 TF 的 ChIP-seq 数据量差异可能影响模型性能。
- **模型依赖**：结果依赖于 DenseNet-LSTM 架构选择；未系统比较其他架构（如 Transformer）。
- **最难情形**：对于结合 motif 不明确或 ChIP-seq 数据质量差的 TF，context 效应可能难以捕捉；细胞类型特异性设计仅验证了 4 个 TF。
- **群体/领域边界**：实验仅在 HepG2 和 K562 细胞系中验证；结论可能不适用于其他细胞类型或体内环境。
- **不确定性**：未报告模型预测的置信区间；MPRA 活性测量存在技术噪声（但通过 3 个生物学重复控制）。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| TFBU 长度选择 | 168 bp 为经验选择，可能非最优 | 系统研究不同 TFBU 长度的影响 | Discussion 第 2 段 |
| 细胞类型特异性机制未完全阐明 | 观察到了细胞类型特异性，但未揭示具体分子机制 | 结合共因子和染色质状态信息进一步研究 | Discussion 第 3 段 |
| 多 TFBU 联合优化的通用性 | 仅测试了 4 个 TF 的组合 | 扩展到更多 TF 组合和更复杂的增强子架构 | Discussion 第 4 段 |
| 模型可解释性有限 | 深度学习模型是黑箱，难以直接提取生物学规则 | 结合可解释性方法分析关键序列特征 | Discussion 第 5 段 |
| 体内验证不足 | 实验均在细胞系中完成，未进行动物模型验证 | 在体内环境中验证设计增强子的功能 | Discussion 第 6 段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|----------------------|----------|----------|------|
| 正负样本均来自可及染色质区域 | 负样本虽无 ChIP-seq 峰，但可能仍存在低水平结合或增强子活性，导致模型学到「强 vs 弱」而非「有 vs 无」 | 影响模型分数的生物学解释 | 使用 STARR-seq 或 MPRA 直接测量负样本的增强子活性 | Methods 节「Preparation of dataset」 |
| 优化后 context 可能包含弱 TFBS | 作者过滤了明显 TFBS，但弱 TFBS（p 值 0.001-0.0001）可能仍存在并贡献活性 | 可能高估 context 的「非 TFBS」效应 | 系统性突变弱 TFBS 后测量活性变化 | Results 图 2c；Methods 节「The definition of weak binding sites」 |
| 细胞类型特异性可能来自共因子而非 context 本身 | 模型可能捕捉到细胞类型特异的染色质状态或共因子结合位点，而非 context 序列本身 | 影响对机制的理解 | 在相同染色质环境下比较不同 context 的活性 | Results 图 3；Discussion 第 3 段 |
| 线性组合模型可能过于简化 | 增强子活性可能涉及 TFBU 间的非线性交互（如协同、拮抗） | 影响长增强子设计的准确性 | 比较线性模型与非线性模型（如 Transformer）在长增强子上的预测性能 | Results 图 5b |
| 未报告模型在不同细胞类型间的迁移性能 | HepG2 训练的模型是否适用于 K562 或其他细胞类型未知 | 影响模型的泛化性 | 交叉细胞类型验证模型性能 | 未提供 |
| 遗传算法可能陷入局部最优 | 未与更先进的优化方法（如贝叶斯优化、强化学习）比较 | 影响设计序列的质量上限 | 使用多种优化方法对比设计序列的活性分布 | Methods 节「Sequence design and optimization」 |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **TFBS-context 作为可设计的模块**：将 TFBS 与侧翼序列整合为「功能单元」的概念，可迁移到 TF–DNA 结合机制研究中——不仅关注核心 motif，还要系统建模侧翼序列的贡献。
2. **深度学习模型作为序列-功能映射器**：DenseNet-LSTM 架构可有效捕捉 context 序列的局部和长程特征，这一架构选择可迁移到其他 TF 结合预测任务（如预测 TF 结合强度、细胞类型特异性）。
3. **数据平衡策略**：在构建正负样本时平衡 GC 含量和组蛋白修饰状态，避免模型学习混淆变量——这一策略对任何基于 ChIP-seq 的 TF 结合模型都至关重要。
4. **遗传算法 + 深度学习作为序列设计框架**：将模型输出作为适应度函数，用遗传算法搜索序列空间，可迁移到其他调控元件的设计（如启动子、绝缘子）。
5. **细胞类型特异性建模**：通过训练细胞类型判别模型（HepG2 vs K562）实现特异性设计，可迁移到其他细胞类型或组织特异性的调控元件设计。
6. **增强子解耦策略**：将增强子分解为多个 TFBU 的线性组合，用线性回归建模活性，可迁移到长序列调控元件的可解释性建模。
7. **实验验证闭环**：模型预测 → 设计 → MPRA 验证 → 模型修正的闭环流程，是 AI 驱动的序列设计研究的标准范式。

## 15 与已有知识连接
- **相似工作**：DeepSEED（作者前期工作，利用深度学习设计增强子间隔序列）；Enformer（DeepMind，长序列调控预测）；BPNet（预测 TF 结合并解释序列特征）；引文 [34] 为 DeepSEED，[45] 为 Enformer 类工作。
- **组合关系**：本文的 TFBU 概念可视为对传统 PWM 匹配的扩展——PWM 仅覆盖核心 motif，TFBU 将 context 纳入考量；与 DNA 形状预测工具（如 DNAshape）互补，本文用深度学习隐式学习形状特征。
- **冲突/竞争**：与「TFBS 密度决定增强子活性」的经典观点部分冲突——本文证明 context 序列可独立于 TFBS 密度调控活性；与「增强子活性主要由共因子招募决定」的观点互补而非冲突。
- **可迁移领域**：本文的「功能单元 + 深度学习 + 遗传算法」框架可迁移到其他 DNA 调控元件（启动子、沉默子、绝缘子）的设计；细胞类型特异性建模方法可迁移到细胞状态特异性的调控元件设计。
- **理论支撑**：TF 在基因组上的结合受侧翼序列影响已有实验证据（如 DNA 形状、弱结合位点协同），本文提供了定量建模和设计验证。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合动力学的 TFBU 扩展模型
   - **来源局限/观察**：本文仅用 ChIP-seq 静态结合数据，未考虑结合动力学（on/off rate）
   - **核心假设**：TFBS-context 不仅影响结合概率，还影响结合动力学参数
   - **初步方法**：结合 smFRET 或 SPR 测量不同 context 下的结合动力学，训练深度学习模型预测动力学参数
   - **验证方式**：比较 TFBU 模型预测的动力学参数与实验测量值
   - **创新状态**：unverified

2. **候选名称**：TFBS-context 的三维结构特征解析
   - **来源局限/观察**：本文用序列特征隐式建模 context，未直接解析 DNA 三维结构
   - **核心假设**：context 序列通过改变 DNA 局部结构（弯曲、柔韧性）影响 TF 结合
   - **初步方法**：对优化前后的 context 序列进行 MD 模拟或使用 AlphaFold3 预测 DNA 结构，比较结构特征差异
   - **验证方式**：将结构特征（如 MGW、roll）与 TFBU 分数关联，验证结构-功能关系
   - **创新状态**：unverified

3. **候选名称**：多 TF 协同结合的 TFBU 联合优化
   - **来源局限/观察**：本文联合优化了同一 TF 的多个 TFBU，未涉及不同 TF 间的协同
   - **核心假设**：不同 TF 的 TFBU 间存在协同或拮抗效应，联合优化可增强特异性
   - **初步方法**：扩展 DeMulTFBU 模块，将不同 TF 的 TFBU 分数加权组合，用多目标优化平衡活性与特异性
   - **验证方式**：设计包含不同 TF 组合的增强子，测量活性与细胞类型特异性
   - **创新状态**：unverified

4. **候选名称**：TFBS-context 的跨物种保守性分析
   - **来源局限/观察**：本文仅使用人类数据，未检验 TFBU 概念的进化保守性
   - **核心假设**：功能重要的 context 序列在进化中保守，可用于识别功能性 TFBU
   - **初步方法**：比较多个物种中同源 TF 的 TFBU context 序列保守性，结合深度学习分数验证
   - **验证方式**：保守 TFBU 是否在 MPRA 中显示更高活性
   - **创新状态**：unverified

5. **候选名称**：TFBS-context 的物理模拟验证
   - **来源局限/观察**：本文完全依赖数据驱动，未从物理原理角度解释 context 效应
   - **核心假设**：context 序列通过改变 DNA 的机械性质（持久长度、弯曲刚度）影响 TF 结合
   - **初步方法**：对高/低分数 context 进行 MD 模拟，计算 DNA 机械性质差异；将物理特征作为深度学习模型的输入特征
   - **验证方式**：物理特征增强的模型是否优于纯序列模型
   - **创新状态**：unverified