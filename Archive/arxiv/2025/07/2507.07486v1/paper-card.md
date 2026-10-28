## 01 基本信息

- **标题**：Sparse Autoencoders Reveal Interpretable Structure in Small Gene Language Models
- **作者**：Haoxiang Guan; Jiyan He; Jie Zhang
- **单位**：中国科学技术大学（University of Science and Technology of China）；新加坡科技研究局（A*STAR, CFAR and IHPC）
- **期刊/预印本平台**：arXiv 预印本（标注为 2025 IAC 会议格式，但未提供正式会议录用信息）
- **年份**：2025（提交日期 2025-07-10）
- **论文类型**：预印本（会议格式）
- **领域**：可解释性（interpretability）× 基因语言模型（gene language model）× 稀疏自编码器（SAE）
- **关键词**：Sparse Autoencoders, Gene Language Models, Interpretability, Transcription Factor Binding Sites, HyenaDNA
- **DOI/arXiv 号**：arXiv:2507.07486v1
- **代码**：未提供
- **数据**：人类参考基因组（用于训练 HyenaDNA-small-32k 的原始数据）；JASPAR TFBS 注释（经 UCSC Table Browser 获取）；染色体 14 用于评估
- **阅读日期**：2025-07-11（按提交日期推算，实际阅读日期未提供）
- **该文在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × AI 可解释性」交叉方向，聚焦于**转录因子（TF）结合基序（motif）在基因语言模型内部表征中的可解释性**。与课题方向（TF–DNA 结合机制 × AI/深度学习）直接相关：它不预测 TF 结合位点，而是**事后解释**一个已预训练的小型基因语言模型（HyenaDNA-small-32k）是否在内部编码了 TF 结合基序信息。方法上属于**机制可解释性（mechanistic interpretability）**路线，与结构预测/对接/分子动力学（MD）等物理模拟路线互补。

---

## 02 一句话总结

本文对小型基因语言模型 HyenaDNA-small-32k 的第三层激活训练稀疏自编码器（SAE），发现其稀疏特征能高精度地对应单个核苷酸身份和已知的转录因子结合基序（如 C2H2 锌指类 MA1596.1/MA2121.1、MADS-box 类 MA0052.5），从而证明紧凑模型也能编码生物学相关的调控信息。

---

## 03 研究问题

- **具体问题**：SAE 能否从**小型**基因语言模型（而非大型模型如 Evo 2）中提取出具有生物学意义的可解释特征？具体而言，小型基因语言模型的内部表征是否编码了核苷酸身份和转录因子结合基序（TFBS）？
- **为什么重要**：基因语言模型的可解释性是连接深度学习预测与生物学机制理解的关键桥梁。如果小型模型也能被 SAE 有效解释，则意味着可解释性分析不必依赖大规模算力，可推广到更多轻量级模型和资源受限场景。对于 TF–DNA 互作研究而言，若模型内部确实编码了 TF 结合基序，则说明这些模型学到的表征与已知调控逻辑一致，增强了模型作为调控预测工具的可信度。
- **现有方法为何不足**：SAE 已被成功应用于大型语言模型（LLM）和大型蛋白质/基因模型（如 Evo 2），但**小型基因语言模型**参数量少、表达能力有限，其内部表征是否仍包含可被 SAE 解耦的生物学结构尚不清楚。已有工作未系统回答这一问题。
- **精确的「Can ... ?」研究问题**：Can sparse autoencoders extract biologically meaningful features (specifically, nucleotide identity and transcription factor binding motifs) from the activations of a small gene language model (HyenaDNA-small-32k)?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引用与作者叙述整理，标注为「仅本文框架」；未经外部系统核验。

1. **阶段一：SAE 用于 LLM 可解释性**（代表：Bricken et al. 等，引用 [1]）
   - 方法：在 LLM 激活上训练稀疏自编码器，将稠密表征分解为稀疏、语义可解释的特征。
   - 优点：揭示模型内部潜在的语义维度。
   - 局限：主要应用于大型模型，计算成本高。

2. **阶段二：SAE 用于蛋白质语言模型**（引用 [2]，InterPLM）
   - 方法：将 SAE 应用于蛋白质语言模型，发现与蛋白质结构和功能相关的特征。
   - 优点：证明 SAE 可迁移到生物序列模型。
   - 局限：聚焦蛋白质（氨基酸序列），未系统探索基因（核苷酸序列）模型，尤其是小型模型。

3. **阶段三：SAE 用于基因组模型**（引用 [3]，Evo 2）
   - 方法：对 Evo 2 这类大规模基因组模型应用 SAE，识别基因序列中的可解释特征。
   - 优点：在基因组尺度验证了 SAE 的有效性。
   - 局限：Evo 2 规模大，小型模型是否同样适用未知。

4. **本文主张的位置**：填补「小型基因语言模型 × SAE 可解释性」的空白，证明紧凑模型（HyenaDNA-small-32k）也能编码核苷酸和 TF 结合基序级别的可解释结构。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 小型基因语言模型的可解释性未知 | 已有 SAE 可解释性研究集中于大型模型（LLM、Evo 2），小型模型是否具备可解释结构不清楚 | 小型模型参数量少、表达能力有限，可能无法形成清晰的特征解耦 | Introduction 节：「it remains unclear whether SAEs can extract meaningful representations from small gene language models」 |
| 基因序列中调控元件的冗余性与复杂性 | TF 结合基序在基因组中重复出现、背景噪声高，导致特征召回率（recall）波动 | 调控元件的内在冗余性和序列背景复杂性 | Results 节：「the observed variability in recall highlights the inherent complexity and redundancy of regulatory elements in genomic sequences」 |
| 特征与生物学注释的对齐评估困难 | 需要将 SAE 特征与已知 TFBS 注释进行系统比较，涉及多步骤注释处理 | 注释来源（JASPAR/UCSC）需质量过滤，且需将 motif 级注释转换为核苷酸级标签 | Methods 节：「applied quality filtering based on motif frequency and p-value thresholds... converted motif-level annotations into nucleotide-level labels」 |

---

## 06 核心思想

### 1) 表面方法
对 HyenaDNA-small-32k 第三层激活训练 SAE（扩展因子 32×，字典大小 8,192），然后通过将 SAE 特征与 JASPAR TFBS 注释对齐，评估特征的生物学意义。

### 2) 核心洞察
**小型基因语言模型虽然参数量小，但其内部表征仍然编码了可被 SAE 解耦的、生物学相关的结构信息**——包括单核苷酸身份和 TF 结合基序。这意味着「模型小」不等于「表征无结构」，SAE 的可解释性分析可以扩展到轻量级模型。

### 3) 可能的普适教训 [Analysis]
- 对于 TF–DNA 互作研究：**模型内部表征的可解释性可以作为模型质量的间接指标**——如果模型内部确实编码了已知的 TF 结合基序，则说明模型学到的序列-调控关系与实验知识一致。
- 方法上：**SAE 提供了一种「无监督」的基序发现途径**——不依赖已知 motif 数据库，而是从模型内部自动涌现出与已知 TFBS 对齐的特征，这为从头发现新的调控元件提供了潜在工具。
- 规模上：**可解释性分析不必局限于大模型**，小型模型也能提供有价值的生物学洞察，降低了计算门槛。

---

## 07 方法总览

- **输入**：人类参考基因组中采样的 32k 核苷酸长度序列
- **前置模型**：HyenaDNA-small-32k（预训练，单核苷酸分辨率，第三层激活被提取）
- **SAE 训练**：
  - 激活来源：第三层（layer 3）
  - 扩展因子：32×
  - 字典大小：8,192
  - 学习率：前 5% 训练步线性 warmup，之后固定为 1e-6
  - L1 惩罚：0.1
  - 批大小：2,048
  - 全局洗牌（global shuffling）激活，防止同源序列出现在同一 batch
- **评估流程**：
  1. 用 JASPAR TFBS 注释染色体 14（经 UCSC Table Browser 获取）
  2. 基于 motif 频率和 p 值阈值进行质量过滤
  3. 将 motif 级注释转换为核苷酸级标签
  4. 使用激活阈值 0.15 判定 SAE 特征是否激活
  5. 计算 precision、recall、F1 分数（方法学参考 InterPLM [2]）
- **输出**：SAE 特征与核苷酸身份、TF 结合基序的对齐程度（precision/recall/F1）

**文字流程**：
人类参考基因组序列 → HyenaDNA-small-32k 前向传播 → 提取第三层激活 → 全局洗牌 → 训练 SAE（32× 扩展，8,192 字典）→ 获得稀疏特征 → 在染色体 14 上计算特征激活（阈值 0.15）→ 与 JASPAR TFBS 核苷酸级标签比对 → 计算 precision/recall/F1 → 识别核苷酸特异性特征和 TF 基序特征

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| HyenaDNA-small-32k 第三层激活提取 | 提供待解释的模型内部表征 | 第三层为中间层，可能编码中等粒度的序列特征 | 输入：32k 核苷酸序列；输出：第三层激活向量 | Methods 节：「extracted latent representations from the third layer」 | [预期] 更换层数可能改变特征粒度；浅层可能偏向局部序列模式，深层可能更抽象 |
| 全局洗牌（global shuffling） | 防止同源序列的激活出现在同一训练 batch | 避免 SAE 过拟合到特定基因组上下文 | 输入：原始激活；输出：洗牌后的激活 | Methods 节：「globally shuffled these activations, ensuring that representations derived from the same input sequence were unlikely to appear together in the same training batch」 | [预期] 移除后 SAE 可能过拟合特定序列上下文，降低特征泛化性 |
| SAE（32× 扩展，8,192 字典） | 将稠密激活分解为稀疏可解释特征 | 稀疏约束迫使模型用少量特征解释输入，利于语义解耦 | 输入：第三层激活；输出：稀疏特征向量 | Methods 节：「expansion factor of 32×, creating feature dictionaries of size 8,192」 | [预期] 降低扩展因子会减少特征容量；提高 L1 惩罚会增加稀疏性但可能损失重建精度 |
| JASPAR TFBS 注释 + 质量过滤 | 提供生物学真值标签 | 需要已知调控元件作为评估基准 | 输入：JASPAR 注释；输出：高质量核苷酸级 TFBS 标签 | Methods 节：「annotated chromosome 14 with JASPAR... applied quality filtering based on motif frequency and p-value thresholds」 | [预期] 过滤过严会减少正样本，过松会增加假阳性 |
| 激活阈值（0.15） | 判定特征是否激活 | 需要将连续激活值二值化以计算分类指标 | 输入：SAE 特征激活值；输出：二值激活标签 | Methods 节：「used an activation threshold of 0.15 to determine whether an SAE feature was activated」 | [预期] 阈值升高会降低 recall 提高 precision；降低则相反 |

---

## 09 关键公式符号

本文未提供明确的数学公式。核心方法（SAE 训练）涉及的标准目标函数（重建损失 + L1 稀疏惩罚）在文中以文字描述给出，未列出具体方程。

**可推断的标准 SAE 目标函数**（基于引用 [1][2] 的通用框架，非本文显式给出）：

- 重建损失：L_recon = ‖x − x̂‖²（x 为输入激活，x̂ 为 SAE 重建）
- 稀疏惩罚：L_sparse = λ · ‖f(x)‖₁（λ = 0.1，文中给出）
- 总损失：L = L_recon + λ · ‖f(x)‖₁

**评估指标**（文中明确使用）：
- Precision = TP / (TP + FP)
- Recall = TP / (TP + FN)
- F1 = 2 · Precision · Recall / (Precision + Recall)

> 注：以上公式为基于文中描述的标准形式重建，文中未显式写出方程。

---

## 10 实验设计与证据链

### 数据集与设置
- **训练数据**：人类参考基因组采样的 32k 核苷酸序列（具体条数未提供）
- **模型**：HyenaDNA-small-32k（预训练，参数冻结）
- **SAE 配置**：扩展因子 32×，字典 8,192，L1 = 0.1，batch size = 2,048，学习率 warmup 5% 后固定 1e-6
- **评估区域**：染色体 14
- **注释来源**：JASPAR TFBS（经 UCSC Table Browser 获取）
- **质量过滤**：基于 motif 频率和 p 值阈值
- **激活阈值**：0.15
- **指标**：Precision、Recall、F1

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 核苷酸特异性特征识别 | SAE 特征能对应单个核苷酸身份 | 在染色体 14 上评估，计算特征与核苷酸位置的对应关系 | 核苷酸特异性特征表现出高 precision，recall 有变化 | 小型基因语言模型编码了核苷酸级别的选择性表征 | 未证明所有核苷酸都被同等程度地编码；未提供定量数值 | Results 节，图 3-A |
| 特征 f/357 激活模式分析 | 单个 SAE 特征能一致地识别特定核苷酸（胞嘧啶 C） | 在 500 bp 染色体 14 片段上可视化激活 | 激活峰与胞嘧啶位置一致 | 该特征独立学会了识别胞嘧啶 | 仅展示单个特征，未系统统计所有核苷酸特征的表现 | Results 节，图 2 |
| TF 基序特征识别 | SAE 特征与已知 TF 结合基序对齐 | 与 JASPAR 注释比对，计算 precision/recall/F1 | 识别出与 MA1596.1、MA2121.1（C2H2 锌指类）、MA0052.5（MADS-box 类）对齐的特征，precision 较高 | 小型模型编码了 TF 结合特异性 | 未提供所有 motif 的完整统计；未与大型模型（如 Evo 2）做定量对比 | Results 节，图 3-B |

---

## 11 结论正确解读

- **任务范围**：本文仅证明 SAE 能从 HyenaDNA-small-32k 的第三层激活中提取与核苷酸身份和已知 TF 结合基序对齐的稀疏特征。**不涉及** TF 结合位点预测、结合亲和力定量、突变效应预测等任务。
- **Oracle/真值输入**：评估使用了 JASPAR 数据库的 TFBS 注释作为「真值」，但注释本身经过质量过滤（motif 频率 + p 值阈值），且从 motif 级转换为核苷酸级标签，这一转换可能引入误差。
- **端到端状态**：**非端到端**。SAE 是事后训练的（post-hoc），HyenaDNA-small-32k 的参数未参与微调。整个流程是「预训练模型 → 提取激活 → 训练 SAE → 与外部注释比对」。
- **算力成本**：未提供具体训练成本。但 HyenaDNA-small-32k 为小型模型，SAE 训练成本相对可控（作者暗示这是优势）。
- **历史数据依赖**：依赖人类参考基因组（GRCh 系列）和 JASPAR 注释库的版本，具体版本未提供。
- **模型依赖**：结论仅针对 HyenaDNA-small-32k 的第三层。不同架构、不同层、不同预训练数据可能导致不同结果。
- **最难情形**：作者承认 recall 存在波动，说明在基因组复杂区域（如重复序列、motif 冗余区域）特征识别可能不稳定。
- **群体/领域边界**：仅人类基因组；未涉及其他物种、非编码区变异、表观遗传修饰等。
- **有边界的复述**：在 HyenaDNA-small-32k 这一特定小型基因语言模型的第三层激活上，SAE 能够以较高 precision 提取与单核苷酸身份和特定 TF 结合基序（C2H2 锌指类、MADS-box 类）对齐的稀疏特征，但 recall 存在波动，且结论不推广到其他模型、层或物种。

---

## 12 作者自认局限

在提供的材料中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限，作者在行文中暗示但未明确标注为局限）：
- recall 的变异性：作者在 Results 节提到「the observed variability in recall highlights the inherent complexity and redundancy of regulatory elements in genomic sequences」，暗示特征对 TFBS 的覆盖不完整。
- 评估范围有限：仅使用 JASPAR 注释的已知 motif，未探索未知调控元件。
- 未提供与大型模型（如 Evo 2）的定量对比，无法判断小型模型与大型模型在可解释性上的差距。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 仅评估了第三层激活 | 不同层可能编码不同粒度的信息；第三层可能恰好是 TF 基序信息最丰富的层，选择该层可能有 cherry-picking 嫌疑 | 若结论要推广到「小型基因模型可解释」，需证明多层一致 | 对每一层分别训练 SAE 并比较 TFBS 对齐指标 | Methods 节：「extracted latent representations from the third layer」 |
| 仅使用 JASPAR 已知 motif 作为评估真值 | 模型可能编码了 JASPAR 之外的调控信息，但评估无法捕捉；反之，高 precision 可能部分源于 JASPAR 注释本身的偏好 | 评估的完整性直接影响结论可信度 | 使用多种 motif 数据库（如 CIS-BP、HOCOMOCO）交叉验证；或使用 ChIP-seq 实验数据 | Methods 节：「annotated chromosome 14 with JASPAR transcription factor binding sites」 |
| 未报告定量数值 | 文中仅以图的形式展示结果，未给出 precision/recall/F1 的具体数值 | 无法评估效果的实际水平，也无法与其他方法定量比较 | 补充数值表格和统计检验 | Results 节仅引用图 2、图 3 |
| 未与大型模型对比 | 作者声称「SAE 可扩展到各种模型规模」，但未提供小型 vs 大型模型的对比实验 | 无法判断小型模型的可解释性是否显著弱于大型模型 | 在相同数据上对 Evo 2 等大型模型应用相同 SAE 流程并对比 | Introduction 节：「SAEs offer a scalable approach for interpreting gene models across various model sizes」 |
| 未讨论 SAE 特征与 TF 基序对齐的因果性 | 特征与 motif 对齐可能反映的是序列组成偏差（如 GC 含量）而非真正的 TF 结合特异性 | 若特征只是捕捉序列统计偏差，则生物学解释力有限 | 使用打乱序列（shuffled with same k-mer composition）作为阴性对照 | Results 节仅展示对齐结果，未做对照实验 |
| 未报告 SAE 重建质量 | 未给出重建损失或下游任务保持率，无法判断 SAE 是否丢失了重要信息 | 如果 SAE 牺牲了重建保真度，则特征可能不完整 | 报告重建 MSE 或在下游任务（如启动子预测）上测试 SAE 特征的可替代性 | Methods 节未提及重建质量评估 |

---

## 14 Agent 提炼的知识候选

### 可迁移概念

1. **SAE 作为 TF 基序发现的「无监督探针」**
   - 本文证明 SAE 特征能自发对齐已知 TF 结合基序。对于 TF–DNA 互作研究，这提供了一种**不依赖已知 motif 数据库**的基序发现途径：训练 SAE 后，将高激活特征对应的序列区域做 de novo motif 发现，可能找到新的调控元件。
   - 迁移方式：在更大规模的基因模型（如 Evo 2、Nucleotide Transformer）上应用相同流程，比较不同规模模型编码的 TF 基序谱。

2. **「小模型也有结构」的验证思路**
   - 本文的方法论启示：**在评估模型生物学相关性时，可解释性分析（SAE）可以作为一种补充验证手段**，与下游任务性能（如 TF 结合预测 AUC）互补。如果模型内部表征与已知生物学一致，则模型预测的可信度更高。
   - 迁移方式：在训练新的 TF–DNA 结合预测模型时，用 SAE 检查模型是否学到了 motif 级别的特征，作为模型诊断工具。

3. **激活阈值 + 核苷酸级标签的评估协议**
   - 本文将 motif 级注释转换为核苷酸级标签，并用激活阈值（0.15）二值化特征激活，然后计算 precision/recall/F1。这一评估协议可直接迁移到其他模型的特征-基序对齐评估中。
   - 迁移方式：在评估蛋白质语言模型中的 DNA 结合结构域特征时，采用类似的「特征激活 vs 实验注释」对齐协议。

4. **全局洗牌防止上下文过拟合**
   - 训练 SAE 时对激活做全局洗牌，避免同源序列出现在同一 batch。这一技巧对任何基于基因组序列的表示学习任务都适用，可防止模型利用序列位置信息而非内容信息。
   - 迁移方式：在训练 TF 结合预测模型时，对训练数据的序列-标签对做类似的去相关处理，防止模型依赖基因组位置偏差。

### 可迁移方法

5. **层选择策略**：本文选择第三层激活，说明中间层可能编码基序级别的信息。在 TF–DNA 互作研究中，可系统扫描不同层的 SAE 特征，找到基序信息最丰富的层，作为下游分析的「最佳表征层」。

6. **JASPAR + UCSC Table Browser 的注释获取管线**：本文的注释获取和质量过滤流程（motif 频率 + p 值阈值）可直接复用于其他基因组区域的特征评估。

### 对课题方向的直接启示

7. **TF–DNA 结合机制的可解释性桥梁**：本文的方法为「深度学习模型预测 TF 结合」提供了可解释性工具——通过 SAE 特征与已知基序的对齐，可以回答「模型到底学到了什么」这一关键问题，从而增强模型在调控基因组学中的可信度。

8. **小型模型的实用价值**：对于资源受限的实验室，本文证明小型基因模型 + SAE 也能提供有意义的生物学洞察，降低了可解释性分析的计算门槛。

---

## 15 与已有知识连接

- **SAE 可解释性框架**：本文直接继承 Bricken et al.（Anthropic 的 SAE 工作，引用 [1]）和 InterPLM（引用 [2]）的方法论。InterPLM 将 SAE 应用于蛋白质语言模型，本文将其迁移到基因语言模型，并聚焦于小型模型。
- **Evo 2 可解释性工作**：引用 [3] 已对 Evo 2 应用 SAE 并识别了基因序列中的可解释特征。本文的贡献在于验证了**小型**模型（HyenaDNA-small-32k）也能获得类似结果，填补了「模型规模 vs 可解释性」的空白。
- **HyenaDNA 架构**：引用 [4][5] 为 HyenaDNA 系列模型，本文使用其 small-32k 变体。HyenaDNA 采用 Hyena 算子（非注意力机制），在长序列（32k）上高效。本文的发现暗示该架构在小型规模下也能学习到生物学相关的表征。
- **JASPAR 数据库**：引用 [6] 为 TF 结合基序的权威数据库，本文使用其注释作为评估真值。JASPAR 也是 TF–DNA 互作研究中常用的基序来源。
- **与课题方向的连接**：
  - 与「TF–DNA 结合预测」方向互补：本文不预测结合，但提供模型内部表征的验证工具。
  - 与「物理模拟（MD/对接）」方向正交：本文是纯数据驱动的可解释性分析，不涉及物理建模，但可作为物理模拟的「先验验证」——如果模型内部编码了已知基序，则说明模型学到的序列-结构关系与实验一致，可为 MD 模拟提供候选区域。
  - 与「结构预测（AlphaFold 等）」方向：本文不涉及结构预测，但 SAE 特征与基序的对齐可视为「序列-功能」映射的一种表征，与结构预测的「序列-结构」映射互补。

---

## 16 Agent 生成的研究候选

### 候选 1：跨模型规模的 TF 基序编码比较
- **名称**：SAE-based Comparative Analysis of TF Motif Encoding Across Gene Model Scales
- **来源局限/观察**：本文仅分析 HyenaDNA-small-32k，未与大型模型（Evo 2、Nucleotide Transformer）定量对比；作者声称「可扩展」但无证据。
- **核心假设**：模型规模越大，SAE 特征与 TF 基序的对齐程度（precision/F1）越高，且能编码更复杂的组合调控（多个 motif 的组合）。
- **相对本文的增量**：在相同评估协议下，对多个规模的基因模型（small/base/large）应用相同 SAE 流程，系统比较 TF 基序编码质量。
- **初步方法**：固定 SAE 超参数（扩展因子、L1、阈值），在不同模型上训练；用相同 JASPAR 注释评估；绘制「模型参数量 vs TF 基序 F1」曲线。
- **验证方式**：统计检验（如 Spearman 相关）确认规模与 F1 的关系；对每个模型检查是否覆盖相同的 motif 集合。
- **可能的失败模式**：小型模型可能在某些 motif 类别上反而优于大型模型（如高频 motif），规模效应不单调。
- **创新状态**：unverified

### 候选 2：SAE 特征驱动的 de novo TF 基序发现
- **名称**：De Novo TF Motif Discovery via SAE Feature Activation Peaks
- **来源局限/观察**：本文仅验证 SAE 特征与**已知** JASPAR motif 的对齐，未探索未知基序。
- **核心假设**：SAE 中高激活特征对应的基因组区域富集了未知的调控基序，可通过 de novo motif 发现算法提取。
- **相对本文的增量**：将 SAE 从「验证工具」升级为「发现工具」。
- **初步方法**：对每个 SAE 特征，提取高激活区域（如 top 1% 激活的 100bp 窗口）；用 MEME/STREME 做 de novo motif 发现；将新 motif 与 JASPAR 比对，筛选未注释的候选；用独立 ChIP-seq 数据验证。
- **验证方式**：新 motif 在 ChIP-seq 峰中富集程度；与已知 motif 的相似性分布。
- **可能的失败模式**：SAE 特征可能主要反映序列组成偏差（如 GC 含量）而非真正的 TF 结合特异性，导致发现的「motif」为假阳性。
- **创新状态**：unverified

### 候选 3：SAE 特征与 TF 结合亲和力的定量关联
- **名称**：Quantitative Linkage Between SAE Features and TF Binding Affinity
- **来源局限/观察**：本文仅做定性对齐（特征是否对应 motif），未探索特征激活强度与结合亲和力的定量关系。
- **核心假设**：SAE 特征激活强度与 TF 结合亲和力（如 Kd 或 ChIP-seq 峰强度）呈正相关，可作为结合强度的代理指标。
- **相对本文的增量**：将可解释性从「分类」（是否结合）提升到「回归」（结合多强）。
- **初步方法**：对特定 TF（如 CTCF、SP1），收集 ChIP-seq 峰强度或 SELEX 亲和力数据；计算对应 SAE 特征在峰区域的激活值；拟合激活-亲和力回归模型。
- **验证方式**：回归 R² 和 Pearson 相关；与现有结合预测工具（如 DeepSEA、Basenji）比较。
- **可能的失败模式**：SAE 特征激活可能受序列上下文影响而非仅由 motif 决定，导致与亲和力相关性弱。
- **创新状态**：unverified

### 候选 4：SAE 引导的 TF–DNA 结合预测模型诊断
- **名称**：SAE-guided Diagnostic Framework for TF-DNA Binding Prediction Models
- **来源局限/观察**：本文仅分析 HyenaDNA，未将 SAE 用于诊断其他 TF 结合预测模型的内部表征。
- **核心假设**：通过 SAE 检查 TF 结合预测模型（如基于 CNN/Transformer 的模型）的内部表征，可以诊断模型是否真正学习了 motif 级别的特征，而非依赖序列伪影。
- **相对本文的增量**：将 SAE 从「解释工具」扩展为「模型审计工具」。
- **初步方法**：对任意 TF 结合预测模型，提取中间层激活；训练 SAE；检查 SAE 特征与已知 motif 的对齐；若对齐差，则提示模型可能依赖非 motif 线索（如 GC 含量、序列复杂度）。
- **验证方式**：对已知表现好/差的模型分别审计，比较 SAE-motif 对齐分数；用特征归因方法（如 SHAP）交叉验证。
- **可能的失败模式**：SAE 特征与 motif 对齐差可能反映的是 SAE 训练不充分而非模型问题，需要控制 SAE 超参数。
- **创新状态**：unverified

### 候选 5：多物种基因模型的 TF 基序编码保守性分析
- **名称**：Cross-species Conservation of TF Motif Encoding in Gene Language Models
- **来源局限/观察**：本文仅使用人类参考基因组，未探索跨物种泛化。
- **核心假设**：在不同物种上预训练的基因模型，其 SAE 特征编码的 TF 基序具有保守性——进化上保守的 TF 结合机制在模型表征中呈现相似结构。
- **相对本文的增量**：将可解释性分析扩展到进化维度。
- **初步方法**：对多个物种（人、小鼠、斑马鱼、果蝇）的基因组分别训练小型基因模型；应用相同 SAE 协议；比较跨物种的 SAE 特征与 motif 对齐模式；分析保守 TF 家族（如 bZIP、homeodomain）的跨物种表征相似性。
- **验证方式**：跨物种特征相似性矩阵；与系统发育距离的相关性。
- **可能的失败模式**：不同物种的基因组组成差异（GC 含量、重复序列比例）可能引入混淆因素，导致表征差异反映的是序列统计而非生物学功能。
- **创新状态**：unverified