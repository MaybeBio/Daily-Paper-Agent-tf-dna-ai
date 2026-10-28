## 01 基本信息

- **标题**：Explainable AI in Genomics: Transcription Factor Binding Site Prediction with Mixture of Experts
- **作者**：Aakash Tripathi; Ian E. Nielsen; Muhammad Umer; Ravi P. Ramachandran; Ghulam Rasool
- **单位**：未提供（根据作者信息推测为美国高校，具体单位未在摘要中列出）
- **期刊/平台**：arXiv 预印本
- **年份**：2025-07-13（v2 版本日期）
- **论文类型**：预印本（方法学 + 实验研究）
- **领域**：基因组学 / 转录因子结合位点预测 / 可解释 AI / 混合专家模型
- **关键词**：Transcription Factor Binding Site (TFBS), Mixture of Experts (MoE), Convolutional Neural Network (CNN), Explainable AI, Attribution Mapping, ShiftSmooth, Out-of-Distribution Generalization
- **DOI/arXiv 号**：arXiv:2507.09754v2
- **代码**：未提供
- **数据**：JASPAR 数据库（ARID3A, FOXM1, GATA3 三个 TF 的 in-distribution 数据）；ENCODE 数据库（BCLAF1, CTCF, POLR2A, RBBP5, SAP30, STAT3 六个 OOD TF 数据）
- **阅读日期**：2026-05-13（按当前日期）
- **在该方向中的位置**：本文聚焦 TF–DNA 结合位点预测，采用 MoE 集成多个预训练 CNN 专家模型，并引入新的可解释性方法 ShiftSmooth。属于「TF–DNA 互作 × 深度学习」方向，核心贡献在于：(1) 用 MoE 架构提升跨 TF 泛化能力（尤其 OOD 场景）；(2) 提出针对序列数据的鲁棒归因方法。与物理模拟（MD/对接）无直接关联，但 MoE 集成思路和归因方法可迁移至结构预测或结合亲和力预测任务。

---

## 02 一句话总结

本文提出一个 MoE 框架，集成三个分别针对 ARID3A、FOXM1、GATA3 预训练的 CNN 专家模型，通过门控网络动态加权组合输出，在 in-distribution 和六个 OOD TF 数据集上取得优于或持平单个专家的 AUC 表现，并引入 ShiftSmooth 归因方法，通过对输入序列的循环移位和梯度平均，提供比 Vanilla Gradient 更鲁棒、更可解释的基序定位结果。

---

## 03 研究问题

- **具体问题**：如何构建一个既能保持单个 TF 专精模型的高精度，又能泛化到未见过的 TF 结合位点（OOD）的预测模型？同时，如何为这类模型提供鲁棒、可解释的归因分析，以支持基序发现和定位？
- **为什么重要**：TFBS 预测是理解基因调控的核心。现有模型（如 DeepBind）通常为单个 TF 训练，泛化能力有限；而通用模型（如 DNABERT）虽泛化好但精度可能不足。此外，基因组数据的可解释性对生物学发现至关重要，但现有归因方法（如 Vanilla Gradient）对序列窗口的微小偏移敏感，导致归因不稳定。
- **现有方法不足**：
  - 单 TF 模型（DeepBind）无法泛化到新 TF；
  - 通用预训练模型（DNABERT）在特定 TF 任务上精度可能不如专精模型；
  - 传统归因方法（Vanilla Gradient）对输入扰动敏感，归因结果不稳定；
  - 现有 MoE 应用多集中于 NLP/CV，未在 TFBS 预测中系统验证。
- **精确研究问题**：*Can a Mixture of Experts framework, integrating multiple pre-trained CNN experts with a learned gating mechanism, achieve superior or comparable TFBS prediction performance on both in-distribution and out-of-distribution transcription factors, while a shift-averaged gradient attribution method (ShiftSmooth) provides more robust and plausible motif localization than Vanilla Gradient?*

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 和 Related Work 的叙述，标注为「仅本文框架」，未经外部系统核验。

1. **传统方法阶段**：PWM（Position Weight Matrix）、SVM、Random Forest 等。依赖手工特征工程和预定义基序，无法捕捉非线性互作，跨细胞类型泛化差。
2. **深度学习阶段（CNN/RNN）**：
   - DeepBind（2015）：CNN 架构，自动从序列学习特征，显著优于传统方法；
   - DeepSEA（2015）：多层 CNN，捕捉更复杂模式，但计算成本高、可解释性下降；
   - DeepRAM：引入 RNN/LSTM，更好处理序列依赖，但存在梯度消失和计算开销问题。
3. **Transformer 阶段**：DNABERT 等基于 k-mer 嵌入和自注意力，擅长长程依赖，但作者初步实验显示其在 TFBS 任务上（GATA3 测试 AUC 0.7032）不如 DeepBind（0.89），可能因预训练目标与下游任务不匹配。
4. **本文主张的位置**：在 CNN 专精模型基础上引入 MoE 集成，保留每个专家的专精能力，同时通过门控机制实现跨 TF 泛化；在可解释性方面，提出 ShiftSmooth 以解决归因对窗口偏移的敏感性。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单模型泛化能力不足 | 单个 CNN 专家在非自身 TF 数据上表现差 | 每个专家仅针对单一 TF 的基序模式训练，特征提取偏向特定序列上下文 | Section IV-B：OOD 测试中单个专家在不同 TF 上表现波动大 |
| 通用模型精度不足 | DNABERT 在 GATA3 上 AUC 仅 0.7032，低于 DeepBind 的 0.89 | 预训练目标（k-mer 语言建模）与 TFBS 二分类任务不匹配；Transformer 可能过度平滑局部基序特征 | Section I 作者初步实验 |
| 归因对窗口偏移敏感 | Vanilla Gradient 对同一基序在不同窗口位置给出不一致的归因 | 梯度在序列边界处不稳定，微小移位导致梯度分布剧变 | Section V-A：GATAA 中 'G' 在 Vanilla Gradient 下归因接近零，ShiftSmooth 恢复其重要性 |
| 归因结果不可靠 | 负归因值出现在已知基序内部 | 梯度符号受局部曲率影响，单一梯度无法反映全局重要性 | Section V-A：MoE 模型 Vanilla Gradient 对 'GATAA' 第二个 'A' 给出负归因，ShiftSmooth 转为正 |
| 模型可解释性不足 | 集成模型（MoE）的决策过程难以追溯 | 多专家输出经门控加权，单一归因方法难以覆盖整个集成路径 | Section V：作者对 MoE 模型同时使用两种归因方法进行对比分析 |

---

## 06 核心思想

### 1) 表面方法
- **MoE 架构**：3 个预训练 CNN 专家（分别针对 ARID3A、FOXM1、GATA3），每个专家输出 32 维嵌入；门控网络接收所有专家嵌入的拼接，输出 3 个权重（softmax），最终预测为加权和。
- **两阶段训练**：先独立训练各 CNN 专家（含超参数优化），再冻结专家权重，仅训练门控网络。
- **ShiftSmooth 归因**：对输入序列进行循环移位（范围 -N 到 N），对每个移位版本计算梯度，将梯度移回原位后取平均。

### 2) 核心洞察
- **N:1 MoE 优于 1:N MoE**：传统 MoE 是"一个输入路由到部分专家"，本文采用"所有专家处理全部输入，门控加权输出"，避免路由稀疏性导致的信息丢失，且更易解释。
- **冻结专家 + 训练门控**：专家已在各自 TF 上收敛，冻结可保留专精能力；门控仅需学习如何组合，降低训练难度和过拟合风险。
- **归因的鲁棒性来自移位平均**：基因组序列的窗口选择本身具有任意性（起点偏移几个碱基是常见的），ShiftSmooth 通过对多个窗口的梯度平均，模拟了"窗口不变性"，从而获得更稳定的归因。

### 3) 可能的普适教训 [Analysis]
- **集成不是简单投票**：MoE 的价值在于门控能根据输入动态调整专家权重，而非静态平均。这提示在 TF–DNA 互作建模中，不同 TF 可能共享某些通用结合模式（如 DNA 骨架接触），也存在独特模式（如侧链特异性识别），门控可自动学习何时依赖哪个专家。
- **可解释性方法应匹配数据特性**：图像领域的 SmoothGrad 假设噪声是高斯分布，但基因组序列的"噪声"更多来自窗口偏移和上下文变化。ShiftSmooth 的移位平均更贴合序列数据的实际扰动模式。
- **专精与泛化的权衡可通过集成解决**：与其训练一个"万能"模型，不如保留多个专精模型并学习组合策略，这在数据异构（不同 TF 基序差异大）时尤其有效。

---

## 07 方法总览

- **输入**：DNA 序列（one-hot 编码，具体长度未在摘要中说明）
- **输出**：二分类概率（该序列是否为给定 TF 的结合位点）
- **模块**：
  1. 3 个 CNN 专家（DeepBind 架构），各自独立预训练；
  2. 门控网络（线性层 + softmax），输入为 3 个专家嵌入的拼接（3×32=96 维），输出 3 维权重；
  3. 最终预测 = Σ(αᵢ · hᵢ) 经分类层 + sigmoid。
- **训练**：
  - 阶段一：各专家用对应 TF 数据训练，Optuna 超参优化，early stopping（patience=5）；
  - 阶段二：冻结专家，门控 + 分类层用所有 in-distribution 数据训练，SGD + Nesterov momentum（momentum=0.98），学习率 0.01，early stopping（patience=10），最多 500 epochs。
- **评估**：AUC（ROC 曲线下面积），30 次 bootstrap 重复，报告均值和标准差；in-distribution 和 OOD 分别评估。
- **可解释性**：对同一输入序列，分别用 Vanilla Gradient 和 ShiftSmooth 生成归因图，对比基序区域（GATAA/TTATC）的归因值。

**文字流程**：
1. 从 JASPAR 获取 ARID3A、FOXM1、GATA3 的 ChIP-seq 数据；
2. 分别训练 3 个 CNN 专家；
3. 冻结专家，训练门控网络；
4. 在 in-distribution 和 OOD（ENCODE 的 6 个 TF）上评估 MoE vs 单个专家；
5. 对 GATA3 序列和 OOD 随机序列进行归因分析，对比 Vanilla Gradient 和 ShiftSmooth。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| CNN 专家（×3） | 从序列中提取局部基序特征，输出 32 维嵌入 | 每个 TF 的基序模式不同，专精模型可捕捉细微差异 | 输入：one-hot DNA 序列；输出：32 维嵌入 | Section IV：单个专家在自身 TF 上 AUC 最高 | [预期] 移除后 MoE 无特征来源，无法工作 |
| 门控网络 | 根据输入动态分配专家权重 | 不同序列可能更接近不同 TF 的基序模式，需要自适应加权 | 输入：3×32 维拼接嵌入；输出：3 维 softmax 权重 | Section IV-B：MoE 在 5/6 个 OOD TF 上最优 | [预期] 退化为静态平均，OOD 泛化能力下降 |
| 分类层 | 将加权嵌入映射为二分类 logit | 将特征组合转化为结合/不结合预测 | 输入：32 维加权嵌入；输出：标量 logit | Section IV：AUC 评估 | [预期] 无法输出概率，模型不完整 |
| ShiftSmooth 归因 | 对移位序列的梯度取平均，生成鲁棒归因图 | 解决 Vanilla Gradient 对窗口偏移敏感的问题 | 输入：序列 + 模型；输出：逐位置归因值 | Section V-A：GATAA 的 'G' 在 ShiftSmooth 下获得正归因 | [预期] 归因恢复 Vanilla Gradient 的不稳定性，基序定位精度下降 |
| Bootstrap 评估 | 30 次重采样计算 AUC 分布 | 提供统计显著性证据 | 输入：测试集；输出：AUC 均值±标准差 | Section IV：所有结果均报告 30 次重复 | [预期] 无法判断差异是否显著 |

---

## 09 关键公式符号

1. **专家嵌入**（训练阶段）：
   hᵢ = φ(x · W_expertᵢ + b_expertᵢ)
   - hᵢ ∈ ℝ^{B×H}：第 i 个专家的隐藏输出（H=32）
   - x：输入序列嵌入
   - W_expertᵢ ∈ ℝ^{E×H}：第 i 个专家的权重矩阵（E=32）
   - b_expertᵢ ∈ ℝ^{1×H}：偏置向量
   - φ(·)：ReLU 激活函数

2. **门控分数**：
   g = W_gate · E + b_gate
   - E ∈ ℝ^{B×(E×Nₑ)}：3 个专家嵌入的拼接（3×32=96 维）
   - W_gate ∈ ℝ^{(E×Nₑ)×Nₑ}：门控权重矩阵
   - b_gate ∈ ℝ^{B×Nₑ}：门控偏置

3. **门控权重**：
   α = softmax(g)
   - αᵢ ∈ ℝ^{B×1}：第 i 个专家的权重

4. **MoE 输出**：
   m = Σᵢ α_{:,i} ⊙ hᵢ
   - ⊙：逐元素乘法（广播到 batch 维度）

5. **最终预测**：
   o = W_class · m + b_class
   ŷ = σ(o)
   - W_class ∈ ℝ^{H×1} = ℝ^{32×1}
   - σ(·)：sigmoid 函数

6. **超参数优化目标**：
   θ* = argmax_θ AUC_val(f(θ))
   - θ：超参数集合
   - f(θ)：CNN 模型
   - AUC_val：验证集 AUC

7. **ShiftSmooth 归因**：
   Â_c(x) = (1/(2N+1)) Σ_{n=-N}^{N} ∂S_c(x_n)/∂x，其中 x_n = x >> n（循环右移 n 位）
   - 实际实现中，对每个移位版本计算梯度后，将梯度循环左移 n 位对齐，再取平均。

---

## 10 实验设计与证据链

### 数据集与设置
- **In-distribution**：ARID3A、FOXM1、GATA3 的 ChIP-seq 数据（JASPAR 数据库）
- **OOD**：BCLAF1、CTCF、POLR2A、RBBP5、SAP30、STAT3 的 ChIP-seq 数据（ENCODE 数据库）
- **指标**：AUC（ROC 曲线下面积）
- **重复**：30 次 bootstrap 采样，报告均值±标准差
- **基线**：3 个独立 CNN 专家模型
- **训练硬件**：GPU（具体型号未提供）
- **实现框架**：PyTorch

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| In-distribution 性能 | MoE 在已知 TF 上不劣于最佳专家 | MoE vs 3 个专家，各 30 次 bootstrap | MoE 在 3 个数据集上均排名第二（仅次于对应专家） | MoE 能保持与专精模型相当的精度 | 不能说明 MoE 优于最佳专家 | Section IV-A, 图 4-5 |
| OOD 泛化性能 | MoE 在未见 TF 上优于单个专家 | MoE vs 3 个专家，6 个 OOD TF | MoE 在 5/6 个 TF 上最优，1 个第二 | MoE 显著提升跨 TF 泛化能力 | 不能说明 MoE 对所有 OOD TF 都最优 | Section IV-B, 图 7-8 |
| 统计显著性 | 性能差异非随机 | ANOVA 检验，p < 0.05 | 所有数据集 p 值极小，95% CI 无重叠 | 性能差异具有统计显著性 | ANOVA 仅说明存在差异，不说明效应量 | Section IV, 图 6, 9 |
| GATAA 基序归因 | ShiftSmooth 比 Vanilla Gradient 更准确定位基序 | 同一 GATAA 序列，两种归因方法 | Vanilla 对 'G' 归因≈0；ShiftSmooth 对 'G' 和 'A' 均给正归因 | ShiftSmooth 恢复被 Vanilla 忽略的关键碱基 | 未提供定量指标（如基序定位精度） | Section V-A, 图 11-12 |
| MoE 归因 vs 专家归因 | MoE 的归因更综合 | MoE vs GATA3 专家，同一序列 | MoE 对 GATAA 和 TTATC 均给正归因；专家对 TTATC 归因更高 | MoE 的归因反映多专家综合视角 | 未说明 MoE 归因是否更"正确" | Section V-A, 图 13-14 |
| OOD 归因 | 模型在无基序序列上的行为 | 随机序列，两种归因方法 | 两种方法均未标记显著基序；'CG' 出现负归因 | 模型未在随机序列上产生虚假基序 | 负归因的生物学意义未讨论 | Section V-B, 图 16-19 |

---

## 11 结论正确解读

- **任务范围**：本文仅针对 TFBS 二分类预测（结合/不结合），不涉及结合强度（affinity）回归、染色质可及性、三维结构等。
- **Oracle/真值输入**：训练和评估均使用 ChIP-seq 实验数据作为标签，属于实验测定而非计算预测的 ground truth。
- **端到端状态**：MoE 模型是端到端训练的（两阶段：先专家后门控），但专家是预训练后冻结的，并非完全联合优化。
- **算力成本**：作者未报告具体训练时间或 FLOPs。MoE 推理时需所有专家前向传播，计算量是单专家的 3 倍。
- **历史数据依赖**：所有数据来自 JASPAR/ENCODE 的 ChIP-seq，存在实验条件、抗体质量、细胞类型等偏差。
- **模型依赖**：专家均为 DeepBind 架构，未测试其他骨干（如 ResNet、Transformer）。
- **最难情况**：OOD 中 CTCF 数据集上 MoE 仅排第二（FOXM1 专家最优），说明 MoE 并非在所有 OOD 场景都最优。
- **不确定性**：ANOVA 仅证明组间差异显著，未报告效应量（如 Cohen's d）或配对比较。
- **有边界的复述**：在 3 个 in-distribution TF 和 6 个 OOD TF 的 ChIP-seq 数据上，MoE 集成 3 个 DeepBind 专家，在 OOD 场景下显著优于单个专家（5/6 最优），在 in-distribution 下保持次优；ShiftSmooth 归因在 GATAA 基序上恢复了 Vanilla Gradient 遗漏的 'G' 碱基重要性，且对窗口移位更鲁棒。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 专家数量有限 | 仅 3 个专家，覆盖 3 个 TF | 未明确说明 | 未提供（作者未在摘要中明确讨论） |
| 骨干架构单一 | 仅使用 DeepBind 架构 | 未明确说明 | 未提供 |
| OOD 覆盖有限 | 仅 6 个 OOD TF，且 CTCF 上 MoE 非最优 | 未明确说明 | 未提供 |
| 归因验证缺乏定量指标 | 仅定性对比归因图，未计算基序定位精度 | 未明确说明 | 未提供 |
| 未与其他集成方法对比 | 未与 bagging、boosting、简单平均等对比 | 未明确说明 | 未提供 |

> 注：作者在摘要和引言中未系统列出局限性。以上基于文中可推断的内容，标注为「未提供」表示作者未明确承认。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| MoE 在 in-distribution 上仅排第二 | 门控网络可能过度平滑专家输出，牺牲了专精模型的峰值精度 | 若 MoE 在已知 TF 上无法超越最佳专家，其价值仅在 OOD 场景 | 对比不同门控策略（如稀疏门控、top-k 路由） | Section IV-A：MoE 均排名第二 |
| OOD 测试仅 6 个 TF，且随机选择 | 6 个 TF 可能无法代表全部 TF 多样性；随机选择可能引入偶然性 | 结论的泛化性取决于 OOD 样本的代表性 | 扩大 OOD TF 数量，分层抽样（不同结构家族、不同基序长度） | Section IV-B |
| ShiftSmooth 仅与 Vanilla Gradient 对比 | 未与 Integrated Gradients、DeepLIFT、SHAP 等成熟方法对比 | 无法判断 ShiftSmooth 是否优于现有 SOTA 归因方法 | 在相同数据上对比多种归因方法的基序定位精度 | Section V |
| 归因评估缺乏定量指标 | 仅目视对比热力图，无客观指标（如基序命中率、AUC 归因） | 定性结论难以复现和量化 | 使用基序匹配（如 Tomtom）或区域 AUC 指标 | Section V |
| 未报告专家单独在 OOD 上的完整统计 | 仅报告均值±标准差，未报告每个专家的完整分布 | 无法判断 MoE 的优势是否来自特定专家的贡献 | 提供每个专家在 6 个 OOD TF 上的完整结果表 | Section IV-B |
| 门控网络输入为所有专家嵌入拼接，计算成本高 | 推理时需运行 3 个完整 CNN，计算量是单模型的 3 倍 | 实际应用中可能不划算 | 对比推理时间、参数量、FLOPs | Section III-A |
| 未讨论门控权重的可解释性 | 门控权重本身可揭示"哪个专家对哪个输入更相关"，但未分析 | 这可能是 MoE 的额外价值 | 分析门控权重与 TF 基序相似性的关联 | Section III-A |

---

## 14 个人收获与启发

> 注：本节为 [Analysis]，基于个人判断，非原文内容。

1. **N:1 MoE 的启发**：传统 MoE 的稀疏路由在基因组数据上可能不是最优选择。本文的"所有专家处理全部输入 + 门控加权"策略，本质上是一种软注意力机制，避免了路由决策的离散性。这提示在 TF–DNA 互作建模中，不同 TF 的结合机制可能共享底层特征（如 DNA 形状、氢键模式），也存在独特特征（如侧链特异性），软加权比硬路由更合适。

2. **冻结专家的两阶段训练**：先独立训练专精模型再冻结集成，这种策略在数据量有限时很实用。可迁移到蛋白质–DNA 对接或亲和力预测：先为不同 TF 家族训练专精模型，再用门控组合，避免从头训练大模型的成本。

3. **ShiftSmooth 的通用性**：移位平均的思想不仅适用于序列窗口，也可用于三维结构——对蛋白质–DNA 复合物做微小旋转/平移扰动，平均梯度可获得更鲁棒的界面残基归因。这比单次梯度更稳定。

4. **归因的"窗口不变性"**：基因组数据的窗口选择确实具有任意性，ShiftSmooth 通过显式模拟这种不确定性来获得鲁棒归因。这提示在评估归因方法时，应测试其对输入扰动的敏感性，而不仅是视觉质量。

5. **可迁移到结构预测**：MoE 集成多个结构预测模型（如 AlphaFold 变体或不同 MD 力场），用门控学习何时信任哪个模型，可能比简单平均更优。

---

## 15 与已有知识连接

- **DeepBind (Alipanahi et al., 2015)**：本文的 CNN 专家直接基于 DeepBind 架构，验证了其作为基础特征提取器的有效性。连接点：DeepBind 的局限（单 TF 专精）正是 MoE 要解决的问题。
- **DeepSEA (Zhou & Troyanskaya, 2015)**：多层 CNN 捕捉更复杂模式，但可解释性下降。本文的 ShiftSmooth 可视为对这类深层模型可解释性的补充。
- **DNABERT (Ji et al., 2021)**：本文初步实验显示 DNABERT 在 TFBS 任务上不如 DeepBind，提示预训练语言模型并非所有基因组任务的万能解。连接点：MoE 可考虑将 DNABERT 作为专家之一，与 CNN 互补。
- **SmoothGrad (Smilkov et al., 2017)**：ShiftSmooth 的直接前身，但针对图像噪声设计。本文将其改造为序列移位，是领域适配的典型案例。
- **Mixture of Experts (Jacobs et al., 1991; Shazeer et al., 2017)**：MoE 的经典框架，本文采用 N:1 配置而非稀疏路由，是对传统 MoE 的变体。
- **ENCODE 项目 (ENCODE Project Consortium, 2012)**：OOD 测试数据的来源，提供了跨 TF 的 ChIP-seq 基准。
- **JASPAR 数据库 (Fornes et al., 2020)**：in-distribution 训练数据的来源，是 TF 结合位点研究的标准资源。
- **可解释 AI 在基因组学中的应用 (Novakovsky et al., 2022)**：本文属于该综述中"归因方法用于基序发现"的范畴，ShiftSmooth 是对现有方法库的补充。

---

## 16 研究想法

> 注：本节为 [Analysis]，基于本文的启发，面向「TF–DNA 互作 × AI/物理模拟」方向。

### 候选 1：结构感知的 ShiftSmooth 归因
- **名称**：StructShiftSmooth
- **来源局限/观察**：ShiftSmooth 仅考虑序列移位，未利用三维结构信息。TF–DNA 结合特异性由结构互补决定，序列归因无法捕捉接触界面残基。
- **核心假设**：对蛋白质–DNA 复合物施加微小刚体扰动（旋转/平移），平均梯度可获得比单次梯度更鲁棒的界面残基归因。
- **初步方法**：在 AlphaFold3 或 MD 模拟生成的复合物结构上，对 DNA 做 ±1-2Å 平移和 ±5° 旋转，计算梯度并对齐后平均。
- **验证方式**：与已知突变实验数据（如饱和突变）对比，检查归因是否识别关键接触残基。
- **创新状态**：unverified

### 候选 2：MoE 用于结合亲和力预测
- **名称**：AffinityMoE
- **来源局限/观察**：本文 MoE 仅做二分类（结合/不结合），未预测结合强度。TF–DNA 互作的定量预测（Kd 值）更具生物学价值。
- **核心假设**：不同 TF 家族的结合机制不同，门控网络可自动学习何时依赖序列特征专家、何时依赖结构特征专家。
- **初步方法**：专家 1 为序列 CNN（DeepBind 风格），专家 2 为结构特征提取器（如从 PDB 计算静电/形状描述符），专家 3 为进化保守性模型；门控输出加权预测 log(Kd)。
- **验证方式**：SELEX 或 HT-SELEX 数据，回归指标（R²、Pearson r）。
- **创新状态**：unverified

### 候选 3：门控权重的生物学解释
- **名称**：GateInterpret
- **来源局限/观察**：本文未分析门控权重本身。门控权重可能反映输入序列与各专家训练 TF 的相似性，可作为"软分类器"。
- **核心假设**：门控权重向量可视为输入序列在 TF 空间中的软聚类表示，可用于发现未知 TF 的功能相似性。
- **初步方法**：对大量 TF 序列输入 MoE，记录门控权重，做聚类分析，与已知 TF 家族分类对比。
- **验证方式**：聚类纯度（purity）、调整兰德指数（ARI）。
- **创新状态**：unverified

### 候选 4：ShiftSmooth 与物理模拟结合
- **名称**：MD-ShiftSmooth
- **来源局限/观察**：ShiftSmooth 的移位是离散的，未考虑 DNA 的柔性。MD 模拟可提供更真实的构象系综。
- **核心假设**：从 MD 轨迹采样的构象比均匀移位更接近真实生物学扰动，归因更准确。
- **初步方法**：对 TF–DNA 复合物做短 MD（~100ns），从轨迹中采样构象，计算梯度并平均。
- **验证方式**：与 DMS 突变数据对比，计算归因的 AUC。
- **创新状态**：unverified

### 候选 5：跨物种 TF 泛化
- **名称**：CrossSpeciesMoE
- **来源局限/观察**：本文 OOD 测试仅限人类 TF。跨物种 TF 结合位点预测是进化生物学的重要问题。
- **核心假设**：不同物种的 TF 结合机制保守性不同，MoE 门控可学习物种无关的通用特征。
- **初步方法**：用人类 TF 训练专家，在小鼠、果蝇、酵母的 TF 数据上测试 MoE vs 单专家。
- **验证方式**：跨物种 AUC 对比，分析门控权重是否与物种系统发育距离相关。
- **创新状态**：unverified