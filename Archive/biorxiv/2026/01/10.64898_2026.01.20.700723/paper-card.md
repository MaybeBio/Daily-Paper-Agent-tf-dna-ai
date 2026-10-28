## 01 基本信息

- **标题**：TPCAV: Interpreting deep learning genomics models via concept attribution
- **作者**：Yang J; Mahony S
- **单位**：未提供
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：方法学论文（预印本）
- **领域**：基因组学深度学习模型的可解释性 × 概念归因
- **关键词**：TCAV、概念归因、深度学习可解释性、基因组学、TF–DNA 结合、染色质状态、重复元件、tokenized foundation models
- **DOI/arXiv 号**：10.64898/2026.01.20.700723
- **代码**：未提供
- **数据**：未提供
- **阅读日期**：未提供
- **在该方向中的位置**：本文属于「蛋白质–DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法」中的**模型可解释性**子方向。它不直接预测 TF–DNA 结合，而是为已有的深度学习结合预测模型提供**全局概念级归因**工具，可解释模型依赖哪些生物学概念（如基序、染色质状态、重复元件）做出结合预测。与 TF-MoDISco（基序发现）形成互补，且可迁移到 tokenized foundation models 与多模态输入模型。

---

## 02 一句话总结

本文将 TCAV 概念归因方法首次系统应用于基因组学深度学习模型，通过 PCA 去相关变换（TPCAV）解决嵌入特征冗余问题，实现对 TF–DNA 结合预测模型及其他基因组模型的全局概念级解释，并支持概念特异性输入归因图提取。

---

## 03 研究问题

- **具体问题**：如何对基因组学深度学习模型进行**输入无关的全局概念归因**，即评估任意生物学概念（如染色质状态、重复元件、基序）对模型预测的贡献，而不局限于 one-hot DNA 序列输入？
- **为什么重要**：现有特征归因方法（如 saliency maps、DeepLIFT）仅适用于 one-hot DNA 输入，无法处理更一般的基因组特征（染色质状态、重复元件等），也无法解释 tokenized foundation models 或融合染色质信号的模型。概念归因（TCAV）提供输入无关的全局解释框架，但尚未系统应用于基因组学。
- **现有方法为何不足**：TCAV 原始方法假设嵌入特征相互独立，但基因组学深度学习模型的嵌入特征高度相关且冗余，直接应用 TCAV 会导致概念向量估计不稳定。
- **精确研究问题**：Can a PCA-decorrelated TCAV variant (TPCAV) provide robust and interpretable concept attribution for diverse genomics deep learning models, including one-hot DNA models, chromatin-signal models, and tokenized foundation models?

---

## 04 背景与发展脉络

> 注：此脉络基于本文框架整理，未经外部系统核验，标注为「仅本文框架」。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|----------|
| 特征归因（局部） | Saliency maps, DeepLIFT, Integrated Gradients | 输入级归因，直观 | 仅限 one-hot DNA 输入；无法处理一般基因组特征 | 本文不采用 |
| 基序发现 | TF-MoDISco | 从 one-hot 序列中发现基序 | 仅限序列输入；无法解释非序列概念 | 本文作为对比基线 |
| 概念归因（全局） | TCAV（原始） | 输入无关、全局解释 | 假设特征独立；未应用于基因组学 | 本文改进并首次系统应用 |
| 本文方法 | TPCAV | PCA 去相关 + 概念归因 + 概念特异性输入归因图 | 依赖概念集定义；需预训练模型 | 本文核心贡献 |

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 特征归因方法受限于 one-hot DNA 输入 | 无法评估染色质状态、重复元件等一般基因组特征对预测的贡献 | 现有归因方法设计上依赖输入梯度，仅适用于序列 one-hot 编码 | 摘要：「Existing feature attribution methods are largely restricted to one-hot DNA inputs」 |
| 原始 TCAV 在基因组学模型中不稳定 | 概念向量估计受嵌入特征相关性影响 | 基因组学深度学习模型的嵌入特征高度相关且冗余，违反 TCAV 的独立性假设 | 摘要：「incorporating a PCA-based decorrelation transformation to address correlated and redundant embedding features」 |
| 概念归因未系统应用于基因组学 | 缺乏输入无关的全局解释工具 | TCAV 提出于计算机视觉领域，未迁移到基因组学 | 摘要：「they have not been systematically applied to interpret neural network applications in genomics」 |
| 缺乏概念特异性输入归因图 | 无法定位与特定概念相关的基因组区域 | 原始 TCAV 仅提供概念级分数，不提供输入级定位 | 摘要：「We also introduce a strategy for extracting concept-specific input attribution maps」 |

---

## 06 核心思想

### 1) 表面方法
将 TCAV 概念归因框架迁移到基因组学深度学习模型，并在概念向量估计前加入 PCA 去相关变换（TPCAV），同时引入概念特异性输入归因图的提取策略。

### 2) 核心洞察
- 基因组学模型的嵌入特征（embedding features）存在高度相关性和冗余性，直接使用原始 TCAV 的线性判别或回归估计概念向量会受共线性干扰；PCA 投影可去除这种冗余，使概念向量估计更稳定。
- 概念归因的「输入无关」特性使其天然适合解释多模态基因组模型（如染色质信号输入、tokenized foundation models），这是传统特征归因无法做到的。
- 概念特异性输入归因图可将全局概念归因「下放」到具体基因组区域，连接全局解释与局部定位。

### 3) 可能的普适教训 [Analysis]
- 任何将计算机视觉/自然语言处理中的可解释性方法迁移到基因组学时，都需要重新审视其底层假设（如特征独立性），并针对基因组数据的特有结构（高相关嵌入、多模态输入）做适配。
- 概念归因的价值在于「解释模型学到了什么概念」，而非「解释单个预测」，这对 TF–DNA 结合模型尤其重要——研究者关心的是模型依赖哪些生物学机制（基序、染色质可及性、重复元件），而非单个碱基的重要性。

---

## 07 方法总览

- **输入**：预训练基因组学深度学习模型（支持 one-hot DNA、染色质信号、tokenized 序列等输入表示）+ 用户定义的概念集（如基序、重复元件、染色质状态注释）
- **输出**：每个概念对模型预测的全局归因分数（TCAV score）+ 概念特异性输入归因图
- **模块**：
  1. 概念激活向量（CAV）估计：从概念样本与随机对照样本的嵌入特征中估计概念方向
  2. PCA 去相关变换：对嵌入特征做 PCA 投影，去除相关与冗余维度
  3. TCAV score 计算：沿 CAV 方向计算模型预测的梯度方向一致性
  4. 概念特异性输入归因图：将概念归因映射回输入空间，定位相关基因组区域
- **训练**：不训练新模型；仅使用预训练模型的嵌入与梯度
- **反馈回路**：无（静态解释工具）
- **文字流程**：用户定义概念集 → 收集概念正样本与随机对照样本 → 提取预训练模型嵌入 → PCA 去相关 → 估计 CAV → 计算 TCAV score → 生成概念特异性输入归因图 → 输出全局与局部解释

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| PCA 去相关变换 | 去除嵌入特征的相关性与冗余 | 基因组学模型嵌入特征高度相关，直接估计 CAV 不稳定 | 输入：嵌入特征矩阵；输出：PCA 投影后的特征 | 摘要明确说明 PCA 用于「address correlated and redundant embedding features」 | 预期影响：CAV 估计不稳定，TCAV score 方差增大（预期效应，未实测） |
| CAV 估计 | 从概念样本与对照样本中学习概念方向 | 概念归因的核心——将概念表示为嵌入空间中的方向 | 输入：概念正样本嵌入 + 随机对照嵌入；输出：概念向量 | 摘要：「adapting the Testing with Concept Activation Vectors (TCAV) method」 | 无法估计概念方向，方法失效（核心模块） |
| TCAV score 计算 | 量化概念对预测的全局贡献 | 提供概念级归因分数 | 输入：CAV + 模型梯度；输出：TCAV score | 摘要：「provides comparable motif feature interpretation to TF-MoDISco」 | 无全局归因分数，退化为仅局部解释（预期效应） |
| 概念特异性输入归因图 | 将概念归因映射回输入空间 | 定位与概念相关的具体基因组区域 | 输入：CAV + 输入样本；输出：输入级归因图 | 摘要：「introduce a strategy for extracting concept-specific input attribution maps」 | 无法定位具体区域，仅保留全局分数（预期效应） |

> 注：本文未提供消融实验数据，以上「移除后影响」均为基于方法逻辑的预期效应，非实测结果。

---

## 09 关键公式符号

> 本文为预印本，摘要中未提供具体公式。以下基于 TCAV 原始方法的标准形式，标注为「基于 TCAV 原始文献的通用形式，本文具体公式未提供」。

**TCAV score（通用形式）**：

\[
\text{TCAV}_{C,l} = \frac{|\{x \in X_C : S_{C,l}(x) > 0\}|}{|X_C|}
\]

- \( C \)：概念
- \( l \)：网络层
- \( X_C \)：概念正样本集合
- \( S_{C,l}(x) = \nabla h_l(x) \cdot v_C^l \)：输入 \( x \) 在层 \( l \) 的梯度与概念向量 \( v_C^l \) 的点积

**符号含义**：
- \( h_l(x) \)：输入 \( x \) 在层 \( l \) 的嵌入表示
- \( v_C^l \)：概念 \( C \) 在层 \( l \) 的 CAV（概念激活向量）

**用途**：衡量概念 \( C \) 对模型预测的正向贡献比例。

**直觉**：若模型预测沿概念方向梯度为正的比例高，则该概念对预测有正向贡献。

**来源指针**：本文摘要未提供公式；上述为 TCAV 原始方法（Kim et al., 2018, ICML）的通用形式，本文的 PCA 变体具体公式未在摘要中给出。

---

## 10 实验设计与证据链

- **数据集**：未提供（摘要未说明具体数据集）
- **模型**：多个基因组学深度学习模型，涵盖多种输入表示（one-hot DNA、染色质信号、tokenized 序列）与预测任务
- **指标**：TCAV score；与 TF-MoDISco 的基序解释对比
- **基线**：TF-MoDISco（基序发现）
- **评测协议**：在 one-hot DNA 编码的 TF 结合预测模型上，比较 TPCAV 与 TF-MoDISco 的基序特征解释一致性；在染色质信号模型与 tokenized foundation models 上评估概念归因的稳健性

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| TF 结合预测模型的基序解释 | TPCAV 能提供与 TF-MoDISco 相当的基序特征解释 | TPCAV vs TF-MoDISco，one-hot DNA 模型 | 摘要：「provides comparable motif feature interpretation to TF-MoDISco」 | TPCAV 在基序解释上与专用基序发现工具相当 | 未说明比较的具体指标与统计显著性 | 摘要 |
| 染色质状态概念归因 | TPCAV 能解释染色质状态对预测的贡献 | 染色质信号输入模型 | 摘要：「enables robust interpretive analysis of how ... chromatin state annotations contribute towards predictions」 | TPCAV 可解释非序列概念 | 未提供定量评估细节 | 摘要 |
| 重复元件概念归因 | TPCAV 能解释重复元件对预测的贡献 | 含重复元件注释的模型 | 摘要：「repetitive elements ... contribute towards predictions」 | TPCAV 可解释重复元件概念 | 未提供定量评估细节 | 摘要 |
| tokenized foundation models | TPCAV 能解释 tokenized 模型的嵌入特征 | tokenized foundation models | 摘要：「uniquely generalizes to interpret features learned by tokenized foundation models」 | TPCAV 可迁移到 tokenized 模型 | 未说明具体模型与任务 | 摘要 |
| 概念特异性输入归因图 | TPCAV 能定位与概念相关的基因组区域 | 概念特异性归因图提取 | 摘要：「identify representative regions associated with specific concepts」 | TPCAV 可提供局部定位 | 未提供可视化或定量验证 | 摘要 |

---

## 11 结论正确解读

- **任务范围**：本文解决的是**已训练模型的概念级归因**问题，不涉及模型训练或预测性能提升。
- **oracle/真值输入**：概念集由用户定义（如基序、染色质状态、重复元件），概念正样本与随机对照样本的选取依赖用户判断；无独立真值。
- **端到端状态**：非端到端——需要预训练模型 + 用户定义概念集 + 嵌入提取 + PCA + CAV 估计 + score 计算。
- **算力成本**：未提供；预期主要成本在嵌入提取与 PCA 计算，远低于模型训练。
- **历史数据依赖**：依赖预训练模型训练时使用的数据分布；概念归因结果受训练数据偏差影响。
- **模型依赖**：方法适用于任何可提取嵌入与梯度的深度学习模型；但 PCA 去相关的有效性依赖嵌入维度与样本量。
- **最难情形**：概念定义模糊或概念样本与对照样本区分度低时，CAV 估计可能不稳定；高维嵌入且样本量不足时 PCA 可能失效。
- **群体/领域边界**：本文在基因组学模型上验证，但方法本身可迁移到其他领域；结论的稳健性仅在摘要所述模型集合上得到支持。
- **不确定性**：摘要未提供统计显著性检验、置信区间或跨种子稳定性分析。
- **有边界的复述**：TPCAV 在摘要所述的基因组学模型集合上，提供了与 TF-MoDISco 相当的基序解释，并能解释染色质状态、重复元件等非序列概念，且可迁移到 tokenized foundation models；但定量评估细节、统计显著性与失败案例未在摘要中披露。

---

## 12 作者自认局限

> 在提供的材料（摘要）中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限，基于摘要措辞推断）：
- 方法依赖用户定义概念集，概念选择可能影响归因结果（摘要未明说，但「user-defined concepts」是 TCAV 框架的固有特性）。
- 与 TF-MoDISco 的比较仅说明「comparable」，未声称超越。
- 摘要未提供失败案例或方法失效条件。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 摘要声称「comparable motif feature interpretation to TF-MoDISco」 | 未说明比较指标、阈值与统计检验；「comparable」可能意味着 TPCAV 在部分基序上一致但在其他基序上不一致 | 若 TPCAV 仅部分复现 TF-MoDISco 结果，其作为基序解释工具的可靠性存疑 | 要求作者提供逐基序的匹配率、精确率/召回率及统计检验 | 摘要：「provides comparable motif feature interpretation」 |
| PCA 去相关的有效性未提供消融实验 | 无法判断 PCA 是提升还是损害了 CAV 估计；在某些嵌入空间中 PCA 可能丢失判别信息 | PCA 是本文核心创新点，若无消融，其贡献无法验证 | 对比原始 TCAV vs TPCAV 在相同模型与概念上的 score 稳定性与准确率 | 摘要：「incorporating a PCA-based decorrelation transformation」 |
| 概念特异性输入归因图未提供定量验证 | 归因图可能只是梯度热图的变体，未必真正「概念特异性」 | 若归因图无法区分不同概念，其生物学解释价值有限 | 设计实验：同一区域在不同概念下的归因图是否显著不同 | 摘要：「introduce a strategy for extracting concept-specific input attribution maps」 |
| 未提供失败案例或方法失效条件 | 方法可能在概念样本量小、嵌入维度高、概念间高度重叠时失效 | 了解失效边界对实际应用至关重要 | 要求作者提供概念样本量扫描实验与失败案例分析 | 摘要未提及 |
| 与 TF-MoDISco 的比较仅限 one-hot DNA 模型 | 未说明在染色质信号模型或 tokenized 模型上如何验证基序解释的正确性 | 若无法在其他输入表示上验证，TPCAV 在这些模型上的解释可信度降低 | 要求作者提供在其他输入表示上的基序解释验证方案 | 摘要：「comparable motif feature interpretation to TF-MoDISco on one-hot encoded DNA-based ... models」 |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **概念归因的输入无关性**：TCAV/TPCAV 不依赖输入表示，可解释任何嵌入层的概念贡献。**迁移到本课题**：对 TF–DNA 结合预测模型，可定义「基序」「染色质可及性」「重复元件」「启动子/增强子状态」等生物学概念，评估模型依赖哪些机制做结合预测，而不局限于单碱基归因。

2. **PCA 去相关预处理**：当嵌入特征高度相关时，直接估计概念向量不稳定；PCA 投影可提升 CAV 估计稳健性。**迁移到本课题**：TF–DNA 结合模型的嵌入（如从 CNN 或 Transformer 提取的序列嵌入）通常维度高且相关，TPCAV 的 PCA 策略可直接复用。

3. **概念特异性输入归因图**：将全局概念归因映射回输入空间，可定位与特定概念相关的基因组区域。**迁移到本课题**：可定位「模型认为的 TF 结合基序区域」或「与染色质状态概念相关的调控区域」，辅助下游实验设计（如突变验证）。

4. **多模态模型解释**：TPCAV 可解释融合染色质信号输入的模型。**迁移到本课题**：TF–DNA 结合预测常融合序列 + 染色质可及性（ATAC-seq）或修饰（ChIP-seq）数据，TPCAV 可评估各模态概念的相对贡献。

5. **概念集定义是关键**：概念归因质量依赖概念正样本与对照样本的选择。**迁移到本课题**：定义「基序概念」时需注意基序变体与随机对照的区分度；定义「染色质状态概念」时需注意状态注释的粒度。

---

## 15 与已有知识连接

- **TCAV 原始方法**：Kim et al. (2018) "Interpretability Beyond Feature Attribution: Quantitative Testing with Concept Activation Vectors (TCAV)"，ICML。本文是 TCAV 在基因组学领域的首次系统应用与改进。
- **TF-MoDISco**：Shrikumar et al. (2018) "TF-MoDISco v0.4.2.2: An end-to-end approach for discovering transcription factor binding motifs from neural network activations"，bioRxiv。本文将其作为基序解释的对比基线。
- **特征归因方法**：Saliency maps (Simonyan et al., 2014)、DeepLIFT (Shrikumar et al., 2017)、Integrated Gradients (Sundararajan et al., 2017)——本文指出这些方法受限于 one-hot DNA 输入。
- **基因组学深度学习模型**：本文涉及的模型涵盖 one-hot DNA 编码的 TF 结合预测模型（如 DeepSEA、DeepBind 类架构）、染色质信号输入模型、tokenized foundation models（如 Enformer、DNABERT 类架构）。
- **可迁移领域**：概念归因方法可迁移到蛋白质–DNA 互作预测中的其他任务（如染色质可及性预测、增强子–启动子互作预测），以及蛋白质–蛋白质互作模型的可解释性。

---

## 16 研究想法

> **Agent 生成的研究候选**

### 候选 1：TF–DNA 结合模型的多概念归因框架
- **名称**：Multi-concept TPCAV for TF–DNA binding models
- **来源局限/观察**：现有 TF–DNA 结合预测模型的可解释性多依赖单碱基归因或基序发现，缺乏对「染色质状态」「重复元件」「启动子/增强子状态」等非序列概念的全局归因。
- **核心假设**：TF–DNA 结合预测模型在概念层面依赖多种生物学机制，TPCAV 可量化各概念的相对贡献。
- **增量**：将 TPCAV 系统应用于多个 TF 结合预测模型（如 DeepSEA、Basenji、Enformer），定义统一的概念集（基序、染色质状态、重复元件、保守性），输出跨模型的概念归因对比。
- **初步方法**：选取 3–5 个公开 TF–DNA 结合预测模型，定义 4–6 个生物学概念，提取嵌入 → PCA → CAV → TCAV score → 跨模型对比。
- **验证方式**：与 TF-MoDISco 基序结果对比；用已知生物学知识（如某 TF 已知依赖特定染色质状态）验证归因合理性；跨模型一致性检验。
- **可能的失败模式**：概念定义模糊导致 CAV 不稳定；不同模型嵌入空间差异大导致跨模型对比困难。
- **创新状态**：unverified

### 候选 2：概念特异性输入归因图用于 TF 结合位点定位
- **名称**：Concept-specific attribution maps for TFBS localization
- **来源局限/观察**：TPCAV 提出概念特异性输入归因图，但未在 TF–DNA 结合任务上验证其定位精度。
- **核心假设**：概念特异性归因图可精确定位与特定概念（如某基序）相关的 TF 结合位点，优于通用梯度归因。
- **增量**：将 TPCAV 的归因图与现有 TFBS 定位方法（如 saliency、DeepLIFT）在 ChIP-seq 峰内定位精度上对比。
- **初步方法**：使用 ENCODE ChIP-seq 数据，训练/使用 TF 结合预测模型，生成概念特异性归因图，与 peak 中心距离评估定位精度。
- **验证方式**：与已知基序位置（如 JASPAR 注释）比对；与 saliency/DeepLIFT 定位精度对比。
- **可能的失败模式**：归因图分辨率受模型池化层限制；概念定义与真实生物学机制不完全对应。
- **创新状态**：unverified

### 候选 3：PCA 去相关策略的消融研究
- **名称**：Ablation study of PCA decorrelation in genomic concept attribution
- **来源局限/观察**：本文未提供 PCA 去相关的消融实验，无法判断其独立贡献。
- **核心假设**：PCA 去相关显著提升 CAV 估计稳定性，尤其在嵌入维度高、样本量有限的基因组学场景。
- **增量**：系统对比原始 TCAV vs TPCAV 在不同嵌入维度、概念样本量、概念相似度下的表现。
- **初步方法**：在公开 TF 结合模型上，变化嵌入维度（如不同层）、概念样本量（如 50/100/500）、概念相似度（如相近基序 vs 远缘概念），测量 TCAV score 的方差与准确率。
- **验证方式**：方差分析；与已知生物学知识的一致性。
- **可能的失败模式**：PCA 在某些场景下可能丢失判别信息，导致归因退化。
- **创新状态**：unverified

### 候选 4：TF–DNA 结合模型的概念级跨物种迁移
- **名称**：Cross-species concept transfer for TF–DNA binding models
- **来源局限/观察**：TPCAV 的概念归因依赖预训练模型，但未探讨概念在不同物种模型间的迁移性。
- **核心假设**：TF–DNA 结合模型学到的概念（如基序、染色质状态）在近缘物种间可迁移，TPCAV 可量化迁移程度。
- **增量**：将人类 TF 结合模型的概念归因迁移到小鼠或斑马鱼模型，评估概念一致性。
- **初步方法**：训练/使用人类与小鼠 TF 结合模型，定义共享概念集，比较 TCAV score 的跨物种相关性。
- **验证方式**：与已知保守基序和保守染色质状态注释比对。
- **可能的失败模式**：物种间调控机制差异大，概念迁移性低。
- **创新状态**：unverified

### 候选 5：概念归因与物理模拟的联合解释
- **名称**：Integrating concept attribution with molecular dynamics for TF–DNA binding
- **来源局限/观察**：TPCAV 提供模型层面的概念归因，但未与物理层面的 TF–DNA 结合机制（如结构域接触、氢键模式）连接。
- **核心假设**：深度学习模型学到的概念（如基序、染色质状态）与物理模拟（MD/对接）中的结合自由能贡献存在对应关系。
- **增量**：将 TPCAV 识别的关键概念区域与 MD 模拟中的高接触频率残基/碱基对比，建立「概念–物理」映射。
- **初步方法**：选取 2–3 个 TF–DNA 复合物（如 p53、GATA3），用 TPCAV 识别关键概念区域，用 MD 模拟计算结合界面接触频率，对比一致性。
- **验证方式**：空间重叠率；结合自由能分解与概念归因的相关性。
- **可能的失败模式**：模型概念与物理机制粒度不匹配；MD 模拟成本高。
- **创新状态**：unverified