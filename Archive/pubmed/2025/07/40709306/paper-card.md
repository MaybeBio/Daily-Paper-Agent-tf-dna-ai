## 01 基本信息
- **标题**：Explainable AI in Genomics: Transcription Factor Binding Site Prediction with Mixture of Experts
- **作者与单位**：Tripathi, Aakash; Nielsen, Ian E; Umer, Muhammad; Ramachandran, Ravi P; Rasool, Ghulam（单位未提供）
- **期刊/预印本平台**：ArXiv
- **年份**：2025-07-25
- **论文类型**：预印本（方法学 + 实验研究）
- **领域**：基因组学 / 深度学习 / 可解释 AI / 转录因子结合位点预测
- **关键词**：TFBS prediction, Mixture of Experts, CNN, Explainable AI, ShiftSmooth, Out-of-Distribution Generalization
- **DOI/arXiv 号**：DOI/ID 40709306（PubMed）；arXiv 号未提供
- **代码**：未提供
- **数据**：JASPAR 数据库（ARID3A, FOXM1, GATA3 基序）、ENCODE 数据库（ChIP-seq 数据，含 BCLAF1, CTCF, POLR2A, RBBP5, SAP30, STAT3）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」方向，核心贡献为：(1) 将 Mixture of Experts (MoE) 框架引入 TFBS 预测，通过集成多个预训练 CNN 专家提升泛化能力；(2) 提出 ShiftSmooth 可解释性方法，改进基序定位与发现。与物理模拟（MD/对接）无直接关联，但 MoE 的「多专家-门控」思想与「多构象/多模式识别」的物理视角有潜在可迁移性。

## 02 一句话总结
本文提出一个 MoE 框架，集成三个分别针对 ARID3A、FOXM1、GATA3 基序预训练的 CNN 专家模型，通过门控网络动态加权组合输出，在六个未见过的 TF（OOD）数据集上取得优于或持平于单个专家的 AUC 表现；同时提出 ShiftSmooth 归因方法，通过对输入序列的循环移位与梯度平均，获得比 Vanilla Gradient 更稳健、更可解释的基序定位结果。

## 03 研究问题
- **具体问题**：单个 CNN 模型在 TFBS 预测中泛化能力有限，尤其面对训练分布之外的 TF 时性能下降明显；同时，现有梯度归因方法（如 Vanilla Gradient）对输入序列的微小移位敏感，导致基序定位不稳定。
- **为什么重要**：TFBS 预测是理解基因调控的关键；真实基因组数据中 TF 种类繁多、基序模式多样，模型需在未见过的 TF 上保持性能；可解释性对于生物学发现（基序鉴定）和临床可信度至关重要。
- **现有方法不足**：
  - 单模型（如 DeepBind）针对单一 TF 训练，难以泛化到其他 TF。
  - 集成方法多采用简单平均，未考虑不同专家对不同输入的适应性。
  - SmoothGrad 等图像领域的平滑归因方法无法直接用于序列数据（不能加高斯噪声）。
- **精确研究问题**："Can a Mixture of Experts framework, combining multiple pre-trained CNN experts via a learned gating mechanism, achieve better generalization to out-of-distribution transcription factors than individual expert models, and can a shift-based smoothing attribution method (ShiftSmooth) provide more robust motif localization than Vanilla Gradient?"

## 04 背景与发展脉络
（标注：以下脉络为「经外部核验」+「仅本文框架」混合，具体标注于各阶段后）

1. **传统方法（PWMs, SVM, Random Forest）**：依赖手工特征和预定义基序，无法捕捉非线性互作，跨细胞类型泛化差。[经外部核验，本文 Introduction 引用]
2. **CNN 方法（DeepBind, DeepSEA）**：自动从序列学习局部模式，性能优于传统方法；但受限于局部感受野，难以捕捉长程依赖，且单模型泛化有限。[经外部核验，本文 Introduction 引用]
3. **RNN/LSTM 方法（DeepRAM）**：更好处理序列依赖，但计算成本高，易梯度消失。[经外部核验，本文 Introduction 引用]
4. **Transformer 方法（DNABERT）**：自注意力机制处理长程互作，预训练-微调范式；但本文初步实验显示其在 TFBS 预测上不如 DeepBind（AUC 0.7032 vs 0.89），且计算开销大。[仅本文框架，作者初步实验]
5. **MoE 框架**：在 NLP/图像领域已成熟，但未应用于 TFBS 预测。[经外部核验，本文 Related Work 引用]
6. **归因方法**：Vanilla Gradient 简单但易受输入扰动影响；SmoothGrad 通过加噪平滑提升鲁棒性，但不适用于离散序列数据。[经外部核验，本文 Background 引用]
7. **本文位置**：首次将 MoE 应用于 TFBS 预测，并针对序列数据特性设计 ShiftSmooth 归因方法。[仅本文框架]

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单模型泛化不足 | 单个 CNN 专家在 OOD TF 上性能波动大 | 每个专家仅针对单一 TF 基序训练，特征提取偏向特定模式 | Results 图 7-9，OOD 数据集上各专家 AUC 差异显著 |
| 集成方式简单 | 简单平均/投票未考虑不同专家对不同输入的适应性 | 不同 TF 基序模式差异大，固定权重无法动态适配 | Methods 节 MoE 设计动机 |
| 归因方法对移位敏感 | Vanilla Gradient 在基序定位时遗漏关键核苷酸（如 GATA3 的 'G'） | 梯度对输入序列的窗口位置敏感，微小移位导致归因变化 | Results 图 11 vs 图 12，'G' 在 Vanilla 中几乎为零 |
| 图像平滑方法不适用 | SmoothGrad 无法直接用于序列数据 | 序列是离散符号（A/T/C/G），不能加高斯噪声 | Background 节 ShiftSmooth 设计动机 |
| 可解释性与性能平衡 | 高性能模型（如 Transformer）可解释性差 | 模型复杂度增加导致归因困难 | Introduction 节，DNABERT AUC 0.7032 低于 DeepBind 0.89 |

## 06 核心思想
**1) 表面方法**：
- 三个 CNN 专家（基于 DeepBind 架构）分别用 ARID3A、FOXM1、GATA3 数据预训练，冻结权重后作为特征提取器。
- 门控网络接收三个专家的嵌入（concatenated），输出每个专家的权重（softmax），加权求和得到最终预测。
- ShiftSmooth：对输入序列进行循环移位（-N 到 +N），分别计算梯度，移位回原位后取平均。

**2) 核心洞察**：
- 不同 TF 基序模式存在重叠与差异，MoE 的门控机制可以动态选择最合适的专家组合，而非固定权重。
- 序列数据的归因应模拟「窗口滑动」的真实场景——基因组分析中基序位置本身不确定，通过对移位后的梯度取平均，可以消除窗口位置带来的归因噪声。
- 冻结专家权重、仅训练门控网络，大幅降低训练成本，同时保留专家各自的专精能力。

**3) 可能的普适教训 [Analysis]**：
- 在生物序列任务中，「多模式识别」是常态（同一 TF 可结合多种基序变体，不同 TF 共享部分基序），MoE 的「分而治之 + 动态组合」思想可迁移到其他序列预测任务（如 splice site、enhancer 预测）。
- 归因方法的鲁棒性应针对数据本身的「自然变换」设计（如序列移位），而非通用噪声扰动——这提示在蛋白质-DNA 互作研究中，归因应模拟结合位点的天然变异性。

## 07 方法总览
- **输入**：DNA 序列（one-hot 编码），长度未明确说明（推测为 DeepBind 标准长度，如 101bp 或类似）
- **输出**：TFBS 结合概率（二分类，sigmoid）
- **模块**：
  1. 三个 CNN 专家（DeepBind 架构，各自预训练）
  2. 门控网络（输入为三个专家的嵌入拼接，输出 softmax 权重）
  3. 加权求和层（最终预测）
  4. ShiftSmooth 归因模块（后处理，不参与训练）
- **训练**：
  - 阶段一：每个 CNN 专家独立训练（用各自 TF 数据，Optuna 超参优化，early stopping patience=5）
  - 阶段二：冻结专家权重，训练门控网络（SGD + Nesterov momentum，learning rate=0.01，momentum=0.98，binary cross-entropy loss，early stopping patience=10，max 500 epochs）
- **评测**：AUC（ROC 曲线下面积），30 次 bootstrap 重复
- **工具**：PyTorch，GPU
- **反馈回路**：无显式反馈回路（门控训练时专家权重冻结，无端到端联合微调）
- **假设**：三个专家的嵌入空间具有互补性，门控网络能学习到有效的组合策略

**文字流程**：
1. 三个 CNN 专家分别用 ARID3A、FOXM1、GATA3 数据预训练，得到各自的最优超参数。
2. 冻结专家权重，将输入序列分别通过三个专家，得到三个嵌入（各 32 维）。
3. 三个嵌入拼接后输入门控网络，门控输出三个权重（softmax）。
4. 三个嵌入分别乘以对应权重后求和，得到混合嵌入。
5. 混合嵌入通过分类层（线性 + sigmoid）得到最终预测。
6. 测试时，对输入序列进行循环移位（-N 到 +N），对每个移位版本计算梯度，移位回原位后取平均，得到 ShiftSmooth 归因图。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CNN 专家（×3） | 提取序列局部基序特征 | 每个专家专精于特定 TF 的基序模式 | 输入：DNA 序列；输出：32 维嵌入 | Results 图 4-5，各专家在对应 TF 上 AUC 最高 | 移除任一专家将失去对应基序模式的专精能力，MoE 泛化性下降（预期） |
| 门控网络 | 动态计算专家权重 | 不同输入需要不同专家组合 | 输入：96 维拼接嵌入；输出：3 维 softmax 权重 | Results 图 7-9，MoE 在 5/6 OOD 数据集上最优 | 退化为简单平均，OOD 性能下降（预期） |
| 加权求和层 | 组合专家输出 | 融合多专家信息 | 输入：3×32 维嵌入 + 权重；输出：32 维混合嵌入 | Results 图 7-9 | 无法融合多专家信息，性能下降（预期） |
| ShiftSmooth 归因 | 生成稳健的基序定位图 | Vanilla Gradient 对窗口位置敏感 | 输入：序列 + 模型；输出：归因图 | Results 图 12 vs 图 11，'G' 被正确归因 | 基序定位不完整，可解释性下降（实测对比） |
| Bootstrap 评估 | 统计显著性检验 | 确认性能差异非随机 | 输入：测试集；输出：30 个 AUC 值 + ANOVA | Results 图 5, 8，ANOVA p 值极小 | 无法确认性能差异的统计显著性（预期） |

## 09 关键公式符号
1. **专家嵌入**：$h_i = \phi(e_i W_{expert}^i + \beta)$
   - $h_i$：第 i 个专家的隐藏输出（B×32）
   - $e_i$：第 i 个专家的嵌入（B×32）
   - $W_{expert}^i$：第 i 个专家的权重矩阵（32×32）
   - $\beta$：偏置矩阵（B×32），每行为 $b_{expert}^i$（1×32）
   - $\phi(\cdot)$：ReLU 激活函数

2. **门控分数**：$g = E W_{gate} + \beta_{gate}$
   - $E$：三个专家嵌入的拼接（B×96）
   - $W_{gate}$：门控权重矩阵（96×3）
   - $\beta_{gate}$：门控偏置矩阵（B×3）

3. **门控权重**：$\alpha = \text{softmax}(g)$
   - $\alpha$：B×3，每行和为 1

4. **混合输出**：$m = \sum_{i=1}^{N_e} \alpha_{:,i} \odot h_i$
   - $\alpha_{:,i}$：第 i 个专家的权重列向量（B×1）
   - $\odot$：逐元素乘法（广播到 B×32）

5. **最终预测**：$o = m W_{class} + b_{class}$，$\hat{y} = \sigma(o)$
   - $W_{class}$：32×1，$b_{class}$：B×1，$\sigma$：sigmoid

6. **ShiftSmooth 归因**：$\hat{A}_c(x) = \frac{1}{2N+1} \sum_{n=-N}^{N} A_c(x_n) \ll n$
   - $x_n = x \gg n$：循环右移 n 位
   - $A_c(x_n) = \frac{\partial S_c(x_n)}{\partial x_n}$：移位输入的梯度
   - $\ll n$：循环左移 n 位（对齐回原位）

7. **超参优化**：$\theta^* = \arg\max_\theta \text{AUC}_{val}(f_\theta)$

8. **SGD 更新**：$\theta_{t+1} = \theta_t - \eta \nabla L(\theta_t)$
   - 带 Nesterov 动量：$v_t = \mu v_{t-1} + \eta \nabla L(\theta_t - \mu v_{t-1})$

## 10 实验设计与证据链
**数据集与规模**：
- 训练集：JASPAR 数据库，3 个 TF（ARID3A, FOXM1, GATA3），具体序列数未提供
- 测试集（OOD）：ENCODE 数据库 ChIP-seq 数据，6 个 TF（BCLAF1, CTCF, POLR2A, RBBP5, SAP30, STAT3），具体序列数未提供
- 每个 TF 的专家模型独立训练，MoE 使用三个专家的嵌入

**指标**：AUC（ROC 曲线下面积），30 次 bootstrap 重复，ANOVA 检验

**基线**：三个独立的 CNN 专家模型（DeepBind 架构）

**评测协议**：
- 每个模型在 3 个 in-distribution 数据集 + 6 个 OOD 数据集上评估
- 30 次 bootstrap 采样生成 AUC 分布
- 单因素 ANOVA 检验模型间差异显著性

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| In-distribution 性能 | 各专家在其专精 TF 上最优 | 3 专家 vs MoE，3 个数据集 | 各专家在对应数据集上 AUC 最高，MoE 第二 | 专家具有专精性 | MoE 未超越最佳专家 | Results 图 4-5 |
| OOD 泛化性能 | MoE 在未见 TF 上优于单个专家 | 3 专家 vs MoE，6 个 OOD 数据集 | MoE 在 5/6 数据集上最优，1 个第二 | MoE 提升 OOD 泛化 | MoE 非所有情况最优 | Results 图 7-9 |
| 统计显著性 | 模型间差异非随机 | ANOVA，30 次 bootstrap | p 值极小，支持备择假设 | 性能差异显著 | 未提供效应量 | Results 节 |
| 归因质量（GATA3） | ShiftSmooth 优于 Vanilla Gradient | 同一模型，两种归因方法 | ShiftSmooth 正确归因 'G'，Vanilla 遗漏 | ShiftSmooth 更稳健 | 仅定性分析，无定量指标 | Results 图 11-14 |
| 归因质量（OOD） | ShiftSmooth 在 OOD 上同样有效 | 随机序列，两种归因方法 | ShiftSmooth 无显著基序归因，Vanilla 有噪声 | ShiftSmooth 避免虚假归因 | 仅定性分析 | Results 图 16-19 |

## 11 结论正确解读
- **任务范围**：本文仅针对 3 个训练 TF + 6 个测试 TF 的 TFBS 二分类预测，不涉及其他类型的蛋白质-DNA 互作（如结构域-基序物理结合机制）。
- **Oracle/真值输入**：使用 JASPAR 和 ENCODE 的 ChIP-seq 数据作为标签，这些是实验测定的结合位点，但 ChIP-seq 本身有噪声和偏差。
- **端到端状态**：MoE 的门控网络训练时专家权重冻结，非端到端联合优化；ShiftSmooth 是后处理归因方法，不参与训练。
- **算力成本**：作者声称 MoE 训练高效（仅训练门控网络），但未提供具体训练时间或 FLOPs 对比。
- **历史数据依赖**：模型依赖 ChIP-seq 数据的质量和覆盖度，不同细胞类型/条件下 ChIP-seq 偏差可能影响泛化。
- **模型依赖**：专家架构固定为 DeepBind CNN，门控网络结构未详细说明（层数、维度）。
- **最难情形**：OOD 中 CTCF 数据集上 MoE 仅第二，说明某些 TF 的基序模式可能无法被现有专家覆盖。
- **有边界的复述**：在 3 个训练 TF 和 6 个测试 TF 的范围内，MoE 框架通过门控组合三个预训练 CNN 专家，在多数 OOD 场景下优于单个专家；ShiftSmooth 归因方法在 GATA3 基序定位上比 Vanilla Gradient 更完整。这些结论不扩展到其他 TF、其他模型架构或其他归因方法。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 专家数量有限 | 仅 3 个专家，覆盖 3 个 TF | 增加更多专家以覆盖更广泛的 TF 基序 | Conclusion 节（隐含） |
| 未探索端到端联合训练 | 专家权重冻结，门控仅学习组合 | 未明确提及 | 未提供 |
| ShiftSmooth 仅定性评估 | 归因质量无定量指标 | 未明确提及 | 未提供 |
| 未与其他归因方法对比 | 仅对比 Vanilla Gradient | 未明确提及 | 未提供 |
| 未报告具体数据规模 | 训练/测试序列数未提供 | 未明确提及 | 未提供 |

**作者提及的相关约束**（非正式局限）：
- 选择 CNN 而非 Transformer 的原因：DNABERT 在初步实验中 AUC 较低（0.7032 vs 0.89），且计算成本高。
- 选择 N:1 MoE 而非 1:N 的原因：N:1 更灵活、可解释、计算高效。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| OOD 测试 TF 仅 6 个，且随机选择 | 样本量小，结论可能受特定 TF 选择影响 | 泛化性结论需更大规模验证 | 扩展到更多 TF（如 20+），报告平均排名 | Results 图 7-9 |
| 未报告基线模型（如单模型集成、简单平均）对比 | MoE 的优势可能来自集成效应而非门控机制 | 无法区分门控贡献 vs 集成贡献 | 增加简单平均/投票基线 | Methods 节 |
| ShiftSmooth 仅与 Vanilla Gradient 对比 | 未与 Integrated Gradients、DeepLIFT 等成熟方法对比 | 无法判断 ShiftSmooth 的相对优势 | 增加多种归因方法对比，使用定量指标（如 motif 发现率） | Results 图 11-14 |
| 归因评估仅定性 | 无量化指标（如 AUPRC、motif 匹配率） | 定性观察可能受主观影响 | 使用 TomTom、MEME 等工具定量评估基序发现 | Results 图 11-14 |
| 未报告门控网络的权重分布 | 无法判断门控是否真正学到有意义的专家选择策略 | 门控机制的可解释性未验证 | 分析门控权重与输入序列特征的相关性 | Methods 节 |
| 未讨论 MoE 在训练 TF 上的性能上限 | MoE 在 in-distribution 上均第二，未超越最佳专家 | MoE 的「组合」是否真正提升上限未验证 | 分析 MoE 与最佳专家的性能差距是否随数据量缩小 | Results 图 4-5 |
| 未报告计算成本对比 | MoE 推理需运行 3 个专家 + 门控，成本高于单模型 | 实际部署需权衡性能与成本 | 报告 FLOPs、推理时间 | 未提供 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **MoE 的 N:1 配置适用于生物序列多模式识别**：不同于经典的 1:N 路由，N:1 配置（所有专家处理同一输入，门控加权组合）更适合 TFBS 预测，因为同一序列可能包含多个基序特征，需要同时利用多个专家的专精能力。可迁移到蛋白质-DNA 对接预测中，将不同构象或不同结合模式的预测器作为专家。

2. **冻结专家 + 训练门控的两阶段训练策略**：先独立训练各专家，再冻结权重训练门控，大幅降低训练成本，且保留专家专精性。可迁移到多任务蛋白质-DNA 互作预测中，将不同任务（如不同 TF 家族）的模型作为专家，训练一个门控网络进行任务自适应。

3. **ShiftSmooth 的「自然变换」平滑思想**：对序列进行循环移位模拟基因组中基序位置的不确定性，比加高斯噪声更符合生物数据的真实扰动模式。可迁移到蛋白质-DNA 结合位点预测中，对蛋白质序列或 DNA 序列进行位移/旋转增强，提升归因鲁棒性。

4. **归因分析应区分「专家特异性」与「模型整体」**：作者分别分析单个专家和 MoE 的归因图，揭示专家专精性与 MoE 综合性的差异。可迁移到蛋白质-DNA 互作研究中，分别分析不同结合模式（如序列特异性 vs 结构特异性）的贡献。

5. **OOD 评估是模型泛化的关键**：作者使用 6 个未见过的 TF 评估模型，比仅报告 in-distribution 性能更有说服力。可迁移到蛋白质-DNA 互作预测中，使用不同物种或不同家族的 TF 作为 OOD 测试集。

6. **统计检验（ANOVA）在模型比较中的必要性**：30 次 bootstrap + ANOVA 确认性能差异显著性，避免单次划分的偶然性。可迁移到蛋白质-DNA 互作模型比较中，使用 bootstrap 或交叉验证 + 统计检验。

## 15 与已有知识连接
- **DeepBind (Alipanahi et al., 2015)**：本文的 CNN 专家直接基于 DeepBind 架构，DeepBind 是 TFBS 预测的经典方法，本文将其作为 MoE 的基础组件。可连接：DeepBind 的序列特征提取能力是 MoE 专家专精性的基础。
- **DeepSEA (Zhou & Troyanskaya, 2015)**：同为 CNN 基因组方法，本文未直接使用但属于同一技术脉络。可连接：DeepSEA 的多任务学习思想与 MoE 的多专家组合有相似之处。
- **DNABERT (Ji et al., 2021)**：本文将其作为对比基线，发现其在 TFBS 预测上不如 DeepBind（AUC 0.7032 vs 0.89）。可连接：Transformer 在短序列基序识别上可能不如 CNN 高效。
- **SmoothGrad (Smilkov et al., 2017)**：ShiftSmooth 的直接灵感来源，但针对序列数据改进了噪声扰动方式（移位 vs 加噪）。可连接：图像领域的归因平滑方法向序列数据的迁移需要重新设计扰动策略。
- **Mixture of Experts (Jacobs et al., 1991; Shazeer et al., 2017)**：MoE 的经典框架，本文采用 N:1 配置而非经典的 1:N 路由。可连接：MoE 在生物序列任务中的应用尚少，本文是早期探索。
- **EvalAttAI (Nielsen et al., 2022)**：本文引用其评估归因方法忠实性的框架。可连接：归因方法的系统评估在基因组学中仍不成熟。
- **JASPAR 数据库 (Fornes et al., 2020)**：训练数据来源，TF 基序的权威数据库。可连接：基序注释质量直接影响模型训练和评估。
- **ENCODE 数据库 (ENCODE Project Consortium, 2012)**：OOD 测试数据来源，ChIP-seq 数据的标准资源。可连接：ChIP-seq 数据的噪声和偏差是 TFBS 预测的固有挑战。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：Structure-Aware MoE for TF-DNA Binding Specificity Prediction
   - **来源局限/观察**：本文 MoE 仅使用序列信息，未利用 TF 的 3D 结构或 DNA 形状特征（如 minor groove width, roll, helix twist），而这些特征已被证明影响 TF-DNA 结合特异性。
   - **核心假设**：将结构特征（来自 PDB 或 AlphaFold 预测）作为额外专家输入，可提升 MoE 对 OOD TF 的泛化能力。
   - **初步方法**：在现有 MoE 框架中增加一个「结构专家」（输入为 TF 结构编码 + DNA 形状特征），与序列专家并行，门控网络学习动态组合。
   - **验证方式**：在 ENCODE 更多 TF 上评估，对比有无结构专家的 MoE 性能；使用 DNA 形状特征（DNAshapeR）作为辅助输入。
   - **创新状态**：unverified

2. **候选名称**：ShiftSmooth for Protein-DNA Binding Interface Attribution
   - **来源局限/观察**：ShiftSmooth 仅用于 DNA 序列的基序定位，未扩展到蛋白质侧或蛋白质-DNA 界面残基的归因。
   - **核心假设**：对蛋白质序列进行位移/旋转增强的归因平滑，可更稳健地识别 DNA 结合界面残基。
   - **初步方法**：将 ShiftSmooth 思想扩展到蛋白质序列（氨基酸位移），应用于蛋白质-DNA 复合物结构预测模型的归因分析。
   - **验证方式**：在已知蛋白质-DNA 复合物结构上评估界面残基定位精度，对比 Vanilla Gradient 和 Integrated Gradients。
   - **创新状态**：unverified

3. **候选名称**：Uncertainty-Aware Gating for TFBS MoE
   - **来源局限/观察**：本文门控网络输出确定性权重，未考虑专家对特定输入的不确定性（如某专家对某序列的预测置信度低）。
   - **核心假设**：将专家预测的不确定性（如 MC-Dropout 或 ensemble variance）纳入门控权重计算，可进一步提升 OOD 鲁棒性。
   - **初步方法**：在门控网络输入中增加各专家的不确定性估计，或使用 Bayesian 门控。
   - **验证方式**：在 OOD 数据集上对比确定性门控 vs 不确定性感知门控的 AUC 和 calibration error。
   - **创新状态**：unverified

4. **候选名称**：Cross-Species TFBS Generalization via MoE
   - **来源局限/观察**：本文 OOD 测试 TF 来自同一物种（人类），未评估跨物种泛化。
   - **核心假设**：MoE 的多专家组合可提升跨物种 TFBS 预测的泛化能力，因为不同物种的 TF 基序存在保守与变异。
   - **初步方法**：使用人类训练的专家，在小鼠、斑马鱼等物种的 TFBS 数据上评估 MoE vs 单专家。
   - **验证方式**：跨物种 AUC 对比，分析门控权重在不同物种上的分布差异。
   - **创新状态**：unverified

5. **候选名称**：End-to-End Fine-Tuning of MoE with Attribution Regularization
   - **来源局限/观察**：本文两阶段训练（先专家后门控）未进行端到端联合优化，且未将归因质量纳入训练目标。
   - **核心假设**：端到端微调 + 归因正则化（如鼓励归因图与已知基序对齐）可同时提升预测性能和可解释性。
   - **初步方法**：在 MoE 训练损失中加入归因一致性正则项，端到端联合优化专家和门控。
   - **验证方式**：对比两阶段 vs 端到端训练的 AUC 和基序发现率。
   - **创新状态**：unverified