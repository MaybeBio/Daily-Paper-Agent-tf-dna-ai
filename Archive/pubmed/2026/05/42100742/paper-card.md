## 01 基本信息

- **标题**：Predicting protein-nucleic acid interactions via protein language models with biophysical and evolutionary priors
- **作者与单位**：Su, Zidong; Zhang, Xiaochun; Tian, Boxue（清华大学，Tsinghua University）
- **期刊/预印本平台**：iScience
- **年份**：2026
- **论文类型**：研究论文（Research Article）
- **领域**：蛋白质-核酸互作预测；生物信息学；深度学习
- **关键词**：protein-nucleic acid interactions; protein language model; ESM-2; biophysical priors; evolutionary priors; binding site prediction
- **DOI/arXiv 号**：10.1016/j.isci.2026.115795
- **代码**：https://doi.org/10.5281/zenodo.19572111
- **数据**：https://doi.org/10.5281/zenodo.19572111
- **阅读日期**：2026-05-15
- **在该课题方向中的位置**：本文属于「蛋白质-DNA互作（聚焦TF-DNA结合机制）× AI方法」方向中的**序列-based预测方法**分支。它不依赖结构信息，仅用蛋白质序列预测核酸结合蛋白分类和结合位点，与结构预测（AlphaFold）和分子动力学模拟方法互补。对TF-DNA结合机制研究而言，本文提供了一种可迁移的**多模态特征融合框架**，尤其适用于TF结合位点预测和功能注释。

## 02 一句话总结

本文提出PNABPred框架，将ESM-2蛋白质语言模型嵌入与Atchley因子（生物物理先验）和BLOSUM50（进化先验）三种特征融合，通过Transformer骨干网络仅从蛋白质序列预测核酸结合蛋白分类和残基级结合位点，在多个基准数据集上超越现有序列方法，且能识别无序区域中的结合位点。

## 03 研究问题

- **具体问题**：仅从蛋白质序列出发，如何准确预测（1）蛋白质是否结合核酸（DNA/RNA），（2）哪些残基参与核酸结合？
- **为什么重要**：核酸结合蛋白（NABPs）参与转录、复制、信号转导等核心生物过程。准确预测结合位点对理解TF-DNA识别机制、药物开发、基因组功能注释至关重要。实验方法（如交联、共晶结构）耗时费力，计算预测可大规模筛选。
- **现有方法不足**：
  - 传统ML方法依赖手工特征（氨基酸组成、理化性质），缺乏上下文语义信息；
  - 纯pLM方法（如仅用ESM-2）虽捕捉序列语义，但未显式注入生物物理和进化约束；
  - 结构-based方法（如GraphBind）依赖实验结构或AlphaFold预测结构，对无序区域（IDRs）效果差，且预测结构噪声会传播到下游任务。
- **精确研究问题**：Can a multi-modal framework that integrates pLM embeddings with biophysical (Atchley factors) and evolutionary (BLOSUM50) priors outperform single-modality sequence-based methods in protein-nucleic acid binding classification and binding site prediction?

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及参考文献，经外部核验部分已标注。

1. **早期序列特征方法**（2010s）：基于氨基酸组成、理化性质、PSSM等手工特征，使用SVM、随机森林等分类器。代表：DNAPred、RNABindPlus。局限：缺乏长程依赖建模，泛化性差。
2. **深度学习方法**（2018-2022）：CNN（Deep-RBPPred）、RNN/LSTM（EL_LSTM、LBi-DBP、Seq-RBPPred）捕捉局部和时序模式。局限：特征表示仍受限于单模态，难以整合多源信息。
3. **结构-based方法**（2019-2023）：GraphBind等利用实验或预测结构，通过GNN建模几何特征。局限：依赖结构质量，对IDRs失效，计算成本高。
4. **蛋白质语言模型**（2021-至今）：ESM-2、ProtTrans等通过大规模无监督预训练捕捉序列语义。代表：CLAPE、CLAPE-DB/CLAPE-RB。局限：单独使用pLM嵌入未显式利用生物物理和进化先验。
5. **本文位置**：提出多模态融合策略，将pLM（ESM-2）与生物物理（Atchley）和进化（BLOSUM50）先验结合，通过Transformer骨干融合，在分类和位点预测任务上均超越单模态方法。**对TF-DNA课题的启示**：TF结合特异性由序列、结构和进化共同决定，多模态融合思路可迁移到TF结合位点预测。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单模态特征表达不足 | 仅用pLM或仅用手工特征的方法在分类和位点预测上性能有限 | pLM捕捉语义但缺乏显式生物物理/进化约束；手工特征缺乏上下文 | Results 图2；Table 1-2 中PNABPred vs CLAPE/Seq-RBPPred对比 |
| 结构依赖方法对IDRs失效 | GraphBind使用AlphaFold预测结构时性能下降 | IDRs无稳定三级结构，预测结构不可靠 | Results 图2E-F；Discussion节提及IDRs |
| 泛化性差 | 模型在跨数据集测试时性能显著下降 | 训练集与测试集分布差异大，模型过拟合特定数据模式 | Results 图2E-F；Test_181交叉训练实验 |
| 特征融合方式简单 | 简单拼接特征无法学习跨模态关系 | 不同模态特征尺度、语义层级不同，需要注意力机制建模交互 | Methods节：Transformer backbone设计 |
| 无序区域结合位点预测困难 | 结构方法无法处理IDRs中的结合位点 | IDRs缺乏稳定结构，结构特征不可用 | Case study：2GZK（含IDRs的HMGB蛋白） |

## 06 核心思想

**1) 表面方法**：
- 三模态特征提取：ESM-2（pLM，1280维/残基）+ Atchley因子（5维生物物理特征，投影至512维）+ BLOSUM50（20维进化替换分数，投影至512维）
- 特征融合：三路特征拼接为2304维/残基向量
- Transformer骨干：8头自注意力，多层堆叠，建模长程依赖
- 分类头：MLP输出残基级二分类（结合/非结合）
- 训练：端到端，交叉熵损失，AdamW优化器，LoRA微调ESM-2

**2) 核心洞察**：
- pLM嵌入捕捉序列语义和上下文，但缺乏显式的生物物理（氨基酸理化性质）和进化（替换偏好）约束；三者互补
- 生物物理先验（Atchley因子）编码了极性、二级结构倾向、分子体积、密码子多样性、静电荷等直接影响核酸结合的理化性质
- 进化先验（BLOSUM50）编码了保守替换模式，反映功能约束
- Transformer自注意力天然适合建模残基间长程依赖，这对核酸结合界面（通常由空间邻近但序列远隔的残基组成）至关重要
- 仅用序列即可隐式编码空间邻近性，无需显式结构信息

**3) 可能的普适教训 [Analysis]**：
- 多模态融合优于单模态：对TF-DNA结合预测，可考虑将pLM嵌入与DNA序列特征（如one-hot、position weight matrix）结合
- 生物物理先验可解释性强：Atchley因子维度少但贡献显著，说明显式注入领域知识可弥补pLM的盲区
- LoRA微调策略：冻结预训练权重、只训练低秩矩阵，既保留通用知识又适配下游任务，适合计算资源有限的场景

## 07 方法总览

- **输入**：蛋白质氨基酸序列（仅序列，无结构信息）
- **输出**：（1）蛋白质级二分类（结合/非结合核酸）；（2）残基级二分类（每个残基是否参与核酸结合）
- **模块**：
  1. ESM-2嵌入模块：33层Transformer，6.5亿参数，取最后一层输出，1280维/残基
  2. Atchley因子模块：5维→线性投影→512维→ReLU→LayerNorm
  3. BLOSUM50模块：20维→线性投影→512维→ReLU→LayerNorm
  4. 位置编码+模态内自注意力：对Atchley和BLOSUM特征分别做8头自注意力
  5. 特征拼接：2304维/残基
  6. Transformer骨干：多层8头自注意力+前馈网络，LayerNorm+Dropout
  7. 分类头：MLP（多层线性+ReLU+Dropout），输出2维logits
- **训练**：端到端，交叉熵损失，AdamW优化器，LoRA微调ESM-2的Q和V投影矩阵
- **硬件**：NVIDIA A100 GPU
- **流程**：序列输入→三路并行嵌入→拼接→Transformer编码→MLP分类头→输出结合概率

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ESM-2嵌入 | 捕捉序列语义和上下文依赖 | pLM通过大规模预训练学习蛋白质序列的深层模式，是预测性能的基础 | 输入：序列；输出：1280维/残基 | 消融实验：移除pLM后MCC大幅下降（DBS: 0.468→0.124；RBS: 0.256→0.072） | **实测**：性能灾难性下降，pLM是核心特征 |
| Atchley因子 | 注入生物物理先验（极性、二级结构倾向、分子体积、密码子多样性、静电荷） | 这些理化性质直接影响核酸结合，pLM可能未显式编码 | 输入：5维/残基；输出：512维/残基 | 消融实验：移除后DBS MCC 0.468→0.460，RBS 0.256→0.239 | **实测**：性能下降较小但显著，尤其在RNA结合预测中 |
| BLOSUM50 | 注入进化先验（保守替换模式） | 进化保守残基更可能参与功能界面 | 输入：20维/残基；输出：512维/残基 | 消融实验：移除后DBS MCC 0.468→0.457，RBS 0.256→0.221 | **实测**：RNA结合预测中贡献大于DNA结合预测 |
| 模态内自注意力 | 在拼接前增强各模态特征的上下文 | 使生物物理和进化特征获得序列上下文，而非孤立残基特征 | 输入：512维/残基；输出：512维/残基 | Methods节描述；未单独消融 | **预期**：移除后各模态特征失去上下文，性能下降 [Analysis] |
| Transformer骨干 | 融合三模态特征，建模长程依赖 | 核酸结合界面由空间邻近但序列远隔的残基组成，需要全局注意力 | 输入：2304维/残基；输出：隐状态 | 与RNN/MLP对比实验（Figure S1） | **实测**：Transformer优于RNN和MLP骨干 |
| LoRA微调 | 高效适配ESM-2到下游任务 | 全量微调6.5亿参数计算成本高，LoRA减少可训练参数数量级 | 输入：预训练权重；输出：适配后权重 | Methods节描述 | **预期**：移除后需全量微调，计算成本大幅增加 [Analysis] |

## 09 关键公式符号

**1) BLOSUM50替换分数**：
$$score(A,B) = \log_2\left(\frac{f(A \rightarrow B)}{f(A) \times f(B)}\right)$$

- $score(A,B)$：氨基酸A替换为B的对数几率分数
- $f(A \rightarrow B)$：在保守蛋白块比对中观察到的A→B替换概率
- $f(A)$、$f(B)$：氨基酸A和B的背景频率

**用途**：为每个残基生成20维向量（该残基与所有20种标准氨基酸的替换分数），编码进化保守性。

**2) LoRA权重更新**：
$$W + \Delta W = W + BA$$

$$\Delta W \approx BA$$

- $W \in \mathbb{R}^{d \times k}$：原始权重矩阵
- $B \in \mathbb{R}^{d \times r}$、$A \in \mathbb{R}^{r \times k}$：低秩分解矩阵
- $r \ll d, k$：秩远小于矩阵维度

**用途**：冻结预训练权重W，仅训练低秩矩阵A和B，大幅减少可训练参数。

**3) 评估指标**（标准定义，未在文中给出新公式）：
- Precision = TP/(TP+FP)
- Recall = TP/(TP+FN)
- F1 = 2·Recall·Precision/(Recall+Precision)
- MCC = (TP·TN − FN·FP)/√[(TP+FN)(TP+FP)(TN+FN)(TN+FP)]

## 10 实验设计与证据链

**数据集**：
- 蛋白质级分类：UniSwiss数据集（DBP），RBPPred和Seq-RBPPred数据集（RBP）
- 残基级位点预测：Test_46（DNA）、Test_129（DNA）、Test_117（RNA）
- 交叉验证：Test_181（独立测试集）
- 新测试集：BioLiP数据库（截至2025年1月），30%序列同一性截止
- 结合位点定义：残基含原子距核酸分子最近原子距离 < 0.5Å + 范德华半径之和

**指标**：Precision、F1、MCC、AUROC

**基线**：CLAPE-DB、CLAPE-RB、ULDNA、Seq-RBPPred、GraphBind（含AlphaFold2预测结构版本）等

**训练设置**：10次独立运行（不同随机种子），报告均值±标准差；Mann-Whitney U检验（p<0.05），Benjamini-Hochberg校正

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|-------------------|------|
| DBP分类 | PNABPred优于现有方法 | vs LBi-DBP, TPSO-DBP等 | MCC 0.825 vs 0.762 (LBi-DBP)；AUROC 0.959 vs 0.932 | 多模态融合提升分类性能 | 未在更大规模多样数据集验证 | Results 图2A；Table 1 |
| RBP分类 | PNABPred优于现有方法 | vs Seq-RBPPred, Deep-RBPPred等 | MCC 0.889 vs 0.757 (Seq-RBPPred)；AUROC 0.990 vs 0.959 | 多模态融合在RBP分类上提升显著 | 未测试RNA结合特异性亚型 | Results 图2B；Table 1 |
| DNA结合位点预测 | PNABPred优于序列方法 | Test_46, Test_129 | Test_129: MCC 0.468 vs 0.389 (CLAPE-DB)；AUROC 0.922 vs 0.881 | 多模态特征优于单模态pLM | 未与结构方法在高质量结构集上对比 | Results 图2C-D；Table 2 |
| RNA结合位点预测 | PNABPred优于序列方法 | Test_117 | MCC 0.256 vs 0.240 (CLAPE-RB)；AUROC 0.833 vs 0.800 | 多模态融合提升RNA位点预测 | 绝对MCC仍较低，预测难度大 | Results 图2C-D；Table 2 |
| 新数据泛化 | PNABPred泛化到新数据 | BioLiP新测试集（2025年1月截止） | 优于CLAPE-DB（MCC 0.451 vs 0.309，提升45.95%） | 模型学到可泛化的结合特征 | 新测试集规模有限 | Results 图2E-F |
| 交叉训练 | 训练集组成不影响优势 | Train_646 vs Train_573，Test_181评估 | 两种训练条件下均优于CLAPE-DB | 优势不依赖特定训练集 | 未测试更多训练集组合 | Results 图2E-F |
| 消融-pLM | pLM是核心特征 | 移除ESM-2嵌入 | DBS MCC 0.468→0.124；RBS 0.256→0.072 | pLM贡献最大 | 未测试其他pLM（如ProtTrans） | Results 图3A-B；Table S7 |
| 消融-Atchley | 生物物理先验有贡献 | 移除Atchley因子 | DBS MCC 0.468→0.460；RBS 0.256→0.239 | 生物物理特征提升性能 | 贡献小于pLM | Results 图3A-B；Table S7 |
| 消融-BLOSUM50 | 进化先验有贡献 | 移除BLOSUM50 | DBS MCC 0.468→0.457；RBS 0.256→0.221 | 进化先验在RNA预测中更重要 | 贡献小于pLM | Results 图3A-B；Table S7 |
| 骨干对比 | Transformer优于RNN/MLP | 相同特征，不同骨干 | Transformer全面优于RNN和MLP | 自注意力适合长程依赖建模 | 未测试其他注意力变体 | Figure S1；Table S9 |
| 氨基酸分布分析 | 预测位点符合已知互作原理 | 预测结合位点富集R、K、W（DNA），R、K、H（RNA） | KL散度接近零（DNA: 0.0185/0.0168；RNA: 0.0217/0.0202） | 模型捕捉了真实的生物物理偏好 | 仅统计分布，未验证结构层面 | Results 图S3 |
| 案例研究 | 在多样蛋白上准确 | 14个代表性蛋白（TF、RBP、非特异性DBP） | 正确识别结合位点，包括IDR区域 | 对TF和IDR结合蛋白有效 | 案例数量有限 | Results 图4；图S5-S7 |

## 11 结论正确解读

- **任务范围**：本文解决的是**蛋白质侧**核酸结合位点预测，不预测核酸序列特异性（即不预测TF识别哪个DNA motif）。对TF-DNA课题，本文提供的是"哪些残基可能结合DNA"的预测，而非"结合什么DNA序列"。
- **Oracle/真值输入**：训练和评估均使用实验确定的结合位点（来自PDB结构或实验注释），无oracle输入。模型仅输入蛋白质序列。
- **端到端状态**：完全端到端，从序列到预测，无需中间结构预测步骤。
- **算力成本**：使用A100 GPU训练，具体时间未报告。LoRA显著降低微调成本。
- **历史数据依赖**：训练数据来自历史PDB和基准数据集，存在注释偏差（已知蛋白/结构域覆盖更多）。
- **模型依赖**：核心依赖ESM-2预训练质量；更换pLM可能改变性能。
- **最难情形**：RNA结合位点预测（MCC仅0.256）显著难于DNA（MCC 0.468-0.490）；IDR区域预测虽优于结构方法，但仍有假阳性。
- **边界复述**：PNABPred在序列-only条件下，对DNA/RNA结合蛋白分类和结合位点预测优于现有序列方法，且对IDR区域有效；但它不预测核酸序列特异性，不建模结合后的构象变化，不区分直接/间接读码机制。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 不预测核酸序列特异性 | 模型仅预测蛋白质侧结合位点，不推断识别的核酸序列motif | 采用双编码器架构同时处理蛋白和核酸序列 | Discussion节 |
| 忽略动态构象变化 | 预测反映静态结合潜力，不捕捉诱导契合 | 整合分子动力学模拟 | Discussion节 |
| 二聚体/多聚体性能有限 | 对依赖寡聚化的TF（如bHLH、bZIP）在界面边界敏感性降低 | 多链输入策略（如拼接亚基序列） | Discussion节 |
| 不包含体内环境因素 | 预测基于序列内在性质，不考虑细胞环境、翻译后修饰 | 整合PTM和细胞上下文特征 | Discussion节 |
| 依赖训练数据质量 | 预测基于curated数据，可能遗漏新型结合模式 | 持续更新训练数据 | Discussion节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 消融实验中pLM贡献远大于其他模态 | 可能因为ESM-2已隐式编码了部分生物物理和进化信息，Atchley/BLOSUM的增量贡献有限 | 多模态融合的"必要性"需更严格论证 | 测试不同pLM（如ProtT5、ESM-C）与Atchley/BLOSUM的组合 | Results 图3A-B |
| RNA结合位点MCC仅0.256 | 模型对RNA结合预测能力有限，可能因RNA结合界面更分散、更依赖结构 | 对RNA结合蛋白研究价值受限 | 分析RNA结合位点预测的假阳性/假阴性模式 | Table 2 |
| 与结构方法比较不全面 | 仅与GraphBind（AlphaFold2结构）比较，未与更近的结构预测方法（如AlphaFold3）对比 | 结构方法进步可能缩小差距 | 在相同数据集上对比AlphaFold3等最新方法 | Results 图2E-F |
| 案例研究选择偏倚 | 14个案例可能偏向模型表现好的蛋白 | 无法评估在困难案例上的表现 | 在更大规模、更困难的数据集上系统评估 | Results 图4 |
| 未报告推理时间 | 实际应用（如全蛋白质组扫描）需要推理效率数据 | 影响工具实用性 | 报告每序列推理时间 | 未提供 |
| 未与其他多模态方法比较 | 仅与单模态方法比较，未与同样融合多特征的模型对比 | 无法确认多模态融合策略的独特优势 | 与DeepDNA、iDNA-MS等比较 | Table 1-2 |
| 结合位点定义依赖距离阈值 | 0.5Å+范德华半径的阈值可能遗漏长程相互作用 | 影响训练标签质量 | 测试不同距离阈值敏感性 | Methods节 |

## 14 学到什么

> 以下为面向「蛋白质-DNA互作（聚焦TF-DNA结合机制）× AI/深度学习」课题的可迁移知识。

**概念层面**：
1. **多模态特征互补性**：pLM语义嵌入 + 生物物理先验 + 进化先验三者互补。对TF-DNA课题，可类比为：TF序列嵌入 + TF理化性质 + TF进化保守性 + DNA序列特征（如PWM、k-mer）的多模态融合。
2. **序列-only预测的可行性**：即使无结构信息，序列特征可隐式编码空间邻近性。对TF结合位点预测，可先做序列预测，再用结构方法验证。
3. **IDR区域的可预测性**：无序区域中的结合位点可通过序列特征预测，这对许多含IDR的TF（如p53、MYC）尤为重要。

**方法层面**：
1. **LoRA微调策略**：冻结预训练pLM、只训练低秩适配器，适合在有限数据上微调大模型。可迁移到TF-DNA结合预测的模型微调。
2. **模态内自注意力**：在特征融合前先对各模态做自注意力增强，比直接拼接更有效。可迁移到多模态TF-DNA特征融合。
3. **消融实验设计**：系统移除每个模态评估贡献，明确各特征的必要性。TF-DNA模型应同样做模态消融。
4. **KL散度验证**：用预测位点与真实位点的氨基酸分布KL散度验证模型是否学到真实生物物理偏好。可迁移到TF结合位点预测的验证。

**对TF-DNA课题的具体迁移建议**：
- 将PNABPred框架改造为TF-DNA结合预测器：输入TF蛋白序列 + 候选DNA序列，输出结合概率和结合位点
- 在TF嵌入中融合DNA结合域（DBD）的进化保守性特征
- 对TF二聚化界面，采用多链输入策略（拼接两个亚基序列）
- 结合PWM或ChIP-seq数据作为DNA侧特征，预测TF结合特异性

## 15 与已有知识连接

- **ESM-2**：Lin et al. 2023, Science。本文使用ESM-2作为pLM骨干，与AlphaFold2的Evoformer编码器同源。可连接：ESM-2在TF结构预测中的应用。
- **Atchley因子**：Atchley et al. 2005, PNAS。将氨基酸理化性质降维为5个因子。可连接：TF-DNA结合中氨基酸理化性质的作用。
- **BLOSUM50**：Henikoff & Henikoff 1992, PNAS。经典替换矩阵。可连接：TF DBD的进化保守性分析。
- **GraphBind**：Xia et al. 2021, Briefings in Bioinformatics。结构-based核酸结合位点预测，本文与其对比。可连接：结构方法在TF-DNA结合预测中的表现。
- **CLAPE/CLAPE-DB**：本文作者前期工作，基于ProtTrans的pLM方法。可连接：pLM在核酸结合预测中的演进。
- **Seq-RBPPred**：Yan et al. 2023。RNN-based RNA结合蛋白预测。可连接：序列方法在RNA结合预测中的发展。
- **LoRA**：Hu et al. 2022, ICLR。参数高效微调。可连接：大模型在生物序列任务中的高效适配。
- **AlphaFold2**：Jumper et al. 2021, Nature。本文讨论其预测结构在IDR区域的局限。可连接：结构预测在TF-DNA复合物建模中的适用边界。
- **TF-DNA结合机制**：本文案例包含TF（如WhiB7、NikR、434 Cro），可连接TF-DNA识别的直接/间接读码机制、二聚化对结合的影响。

## 16 研究想法

> 以下为面向「蛋白质-DNA互作（聚焦TF-DNA结合机制）× AI/深度学习」的研究候选。

**候选1：TF-DNA共序列双编码器预测框架**
- **名称**：TF-DNA Dual-Encoder Binding Specificity Predictor
- **来源局限/观察**：PNABPred仅预测蛋白质侧结合位点，不预测DNA序列特异性（作者自认局限）
- **核心假设**：TF蛋白序列嵌入与DNA序列嵌入的交叉注意力可同时预测结合位点和DNA motif
- **初步方法**：双编码器架构，TF序列经ESM-2编码，DNA序列经DNA语言模型（如DNABERT）编码，交叉注意力融合后输出结合概率和位点
- **验证方式**：在ChIP-seq数据集上评估motif预测准确性，与现有PWM方法对比
- **创新状态**：unverified

**候选2：TF二聚化界面感知的结合位点预测**
- **名称**：Dimerization-Aware TF Binding Site Prediction
- **来源局限/观察**：PNABPred对二聚化TF（bHLH、bZIP）在界面边界敏感性降低（作者自认局限）
- **核心假设**：显式建模TF二聚化可提升结合位点预测精度
- **初步方法**：多链输入（拼接两个亚基序列），或图神经网络建模亚基间残基交互
- **验证方式**：在已知二聚化TF数据集上对比单链vs多链输入
- **创新状态**：unverified

**候选3：IDR介导的TF-DNA结合预测**
- **名称**：IDR-Aware TF-DNA Binding Prediction
- **来源局限/观察**：PNABPred对含IDR的蛋白（如HMGB）有效，但结构方法失效
- **核心假设**：IDR中的结合位点可通过序列特征和生物物理先验预测
- **初步方法**：在PNABPred框架基础上，增加IDR区域标注作为辅助特征，或训练专门的IDR结合位点预测头
- **验证方式**：在含IDR的TF数据集上评估，与AlphaFold3结构方法对比
- **创新状态**：unverified

**候选4：多模态特征融合的消融方法论迁移**
- **名称**：Systematic Modality Ablation for TF-DNA Prediction
- **来源局限/观察**：PNABPred的消融实验显示pLM贡献最大，但未测试不同pLM组合
- **核心假设**：不同pLM（ESM-2 vs ProtT5 vs ESM-C）与生物物理/进化先验的组合存在最优配置
- **初步方法**：系统测试不同pLM与Atchley/BLOSUM/HMMER特征的组合，建立模态贡献矩阵
- **验证方式**：在多个TF-DNA基准数据集上报告完整消融表
- **创新状态**：unverified

**候选5：KL散度验证方法推广到TF-DNA motif**
- **名称**：Distributional Validation for TF-DNA Motif Prediction
- **来源局限/观察**：PNABPred用KL散度验证预测位点的氨基酸分布合理性
- **核心假设**：预测的TF结合motif应与已知motif数据库（如JASPAR）的碱基分布一致
- **初步方法**：在TF-DNA预测模型的输出上计算与JASPAR motif的KL散度，作为额外验证指标
- **验证方式**：在多个TF上比较KL散度与motif匹配准确率的相关性
- **创新状态**：unverified