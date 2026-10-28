## 01 基本信息

- **标题**：Advances in computational and experimental approaches for deciphering transcriptional regulatory networks: Understanding the roles of cis-regulatory elements is essential, and recent research utilizing MPRAs, STARR-seq, CRISPR-Cas9, and machine learning has yielded valuable insights
- **作者**：Moeckel, Camille; Mouratidis, Ioannis; Chantzi, Nikol; Uzun, Yasin; Georgakopoulos-Soares, Ilias
- **单位**：Penn State College of Medicine（作者 C.M., I.M., N.C., I.G.S. 受 I.G.S. 启动基金支持）；Y.U. 受 Four Diamonds Pediatric Cancer Research Center 及 NIH R35GM150616 资助
- **期刊/平台**：BioEssays : news and reviews in molecular, cellular and developmental biology
- **年份**：2024-05-08（在线发表）
- **论文类型**：综述（Review）
- **领域**：转录调控网络；顺式调控元件；计算与实验方法
- **关键词**：cis-regulatory elements; transcriptional regulatory networks; MPRA; STARR-seq; CRISPR-Cas9; machine learning; deep learning; transcription factor binding
- **DOI/arXiv 号**：10.1002/bies.202300210
- **代码**：未提供
- **数据**：未提供（本文为综述，未产生新数据，见 Data Availability Statement）
- **阅读日期**：2025年（具体日期未记录）
- **在该方向中的位置**：本文是一篇综述，系统梳理了从表达数据推断转录调控网络（TRN）的计算方法（相关分析、互信息、回归、贝叶斯、深度学习等）、表观基因组数据整合方法，以及功能验证顺式调控元件的实验技术（MPRA、STARR-seq、CRISPR-Cas9 筛选），并讨论了机器学习/深度学习在解析顺式调控语法（cis-regulatory grammar）中的应用。对于「TF–DNA 结合机制 × AI/物理模拟」课题，本文提供了方法学全景图，特别是 TF 结合位点（TFBS）预测、调控语法解析、以及实验数据（MPRA/STARR-seq）如何为 AI 模型提供训练/验证数据的桥梁性论述。

---

## 02 一句话总结

本文系统综述了从表达数据、表观基因组数据和序列数据构建转录调控网络的计算方法（从相关分析到深度学习），以及 MPRA、STARR-seq、CRISPR-Cas9 等实验技术如何功能性地验证顺式调控元件，并讨论了机器学习在解析顺式调控语法中的进展与局限。

---

## 03 研究问题

- **具体问题**：如何整合计算与实验方法，理解顺式调控元件（cis-regulatory elements）如何通过转录因子（TF）结合、染色质可及性、结构约束和细胞类型差异来调控基因表达？
- **为什么重要**：超过 90% 的疾病相关变异位于非编码区，但 cis-regulatory grammar 的不完整知识阻碍了从序列先验预测突变后果的能力。
- **现有方法为何不足**：
  - 表达数据方法（相关、互信息、回归）无法建模 TF 结合特异性，且只能捕捉线性关系；
  - 监督学习方法依赖高质量标注数据，且模型可解释性差；
  - 实验方法（ChIP-seq、DNase-seq）提供全基因组图谱但缺乏功能性读出；
  - 单细胞数据带来 dropout、噪声和计算资源挑战。
- **精确的「Can ... ?」研究问题**：Can we integrate expression-based, epigenomic, and sequence-based computational approaches with high-throughput functional assays (MPRA, STARR-seq, CRISPR-Cas9) to decipher the cis-regulatory grammar that governs TF–DNA binding and gene expression across cell types and contexts?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注「仅本文框架」；外部核验部分单独标注。

**阶段一：表达数据统计方法（仅本文框架）**
- 代表方法：WGCNA（共表达网络）、相关分析（Pearson/Spearman）、互信息（MI）、回归方法、贝叶斯网络
- 优点：直观、计算简单、适用于 bulk 数据
- 局限：无方向性、无法区分直接/间接互作、假设线性、不含序列信息

**阶段二：监督机器学习（仅本文框架）**
- 代表方法：SVM、随机森林（RF）、KNN、决策树、逻辑回归
- 优点：可整合多特征、在单细胞数据上优于无监督方法
- 局限：需要标注数据、特征工程依赖领域知识

**阶段三：深度学习（仅本文框架）**
- 代表方法：CNN（DeepBind、DeepSea、DanQ、BPNet、DeepSTARR、Sei、LegNet）、RNN、Transformer（Enformer）、GNN（GenKI、GRGNN、DeepRIG、GRINCD、GeneLINK）、生成模型（ExpressionGAN）、注意力机制（DeepGRM、STGRNS）、扩散模型（RegDiffusion）
- 优点：自动特征提取、捕捉非线性依赖、长程相互作用
- 局限：可解释性差、数据需求大、评测基准可能高估性能

**阶段四：表观基因组整合（仅本文框架）**
- 代表方法：scATAC-seq 整合、多组学方法（SCENIC+、scREG、IReNA、DIRECT-NET、SOM、Dictys、scMEGA）
- 优点：纳入染色质可及性、TF 足迹
- 局限：成本高、多模态整合复杂

**阶段五：功能实验验证（仅本文框架）**
- MPRA / STARR-seq：并行测试数千至数百万顺式调控元件活性
- CRISPR-Cas9 筛选：CRISPRi、CRISPRa、表观基因组编辑（dCas9-KRAB、dCas9-p300）
- 优点：功能性读出、因果推断
- 局限：MPRA 为游离体（episomal）环境，与基因组整合环境有差异；CRISPR 筛选成本高

**外部核验**：ENCODE 联盟（参考文献 17）、JASPAR/CIS-BP（参考文献 18-19）、ReMap/UniBind（参考文献 20-21）为 TF 结合数据资源；BEELINE 基准框架（参考文献 77）用于 TRN 推断方法评测。这些外部资源在本文中被引用，但本文未对它们进行独立评估。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| cis-regulatory grammar 不完整 | 无法从序列先验预测突变后果 | 结合位点简并性、染色质结构约束、TF 互作复杂、细胞类型差异 | Introduction 第 1 段 |
| 表达数据方法无法建模 TF 结合特异性 | 相关/互信息方法无方向性、无法区分直接/间接互作 | 不含序列信息、假设线性 | Introduction 第 2 段；Expression-based methods 节 |
| 监督学习方法依赖高质量标注 | 单细胞数据 dropout、噪声大 | 数据稀疏、随机表达噪声 | Expression-based methods 节末段 |
| 深度学习模型可解释性差 | 黑箱预测，难以提取生物学机制 | 多层非线性变换、参数过多 | Conclusions 节 |
| Transformer 模型性能可能被高估 | 某些测试场景下质量被高估 | 评测基准设计问题 | Identifying promoters, enhancers 节（引用 194-195） |
| MPRA 的游离体环境与基因组环境不一致 | 游离体与整合到染色质中的调控元件活性有显著差异 | 染色质环境、位置效应 | MPRA 节（引用 106） |
| 湿实验技术可重复性差 | 即使同一实验的重复之间也出现较差可重复性 | 实验设计、技术噪声 | MPRA 节（引用 106） |
| 单细胞数据计算资源需求大 | bulk 方法在单细胞数据上无法完成 | 数据量指数级增长 | Expression-based methods 节末段 |

---

## 06 核心思想

**1) 表面方法**
本文是一篇综述，不提出新方法。其表面结构为：① 梳理 TRN 构建的计算方法（表达数据、表观数据、深度学习）；② 梳理功能验证顺式调控元件的实验方法（MPRA、STARR-seq、CRISPR-Cas9）；③ 讨论机器学习在解析 cis-regulatory grammar 中的应用。

**2) 核心洞察**
- 单一数据模态（仅表达或仅序列）不足以解析 cis-regulatory grammar；需要整合表达、表观遗传（染色质可及性、组蛋白修饰）和序列特征。
- 实验方法（MPRA/STARR-seq）提供功能性读出，是连接序列变异与调控活性的关键桥梁，也是训练/验证 AI 模型的高质量数据来源。
- 深度学习（特别是 CNN 和 Transformer）能够从序列直接预测调控活性，但可解释性仍是瓶颈；可解释性方法（如 TF-MoDISco + DeepLIFT）可以反推网络学到的 motif。
- 单细胞多组学为构建细胞类型特异的 TRN 提供了前所未有的数据规模，但也带来稀疏性、噪声和计算挑战。

**3) 可能的普适教训 [Analysis]**
- 对「TF–DNA 结合 × AI」课题：高质量功能实验数据（MPRA/STARR-seq）是训练可解释 AI 模型的关键，纯序列模型缺乏实验验证时容易过拟合。
- 对「物理模拟」方向：本文未涉及 MD/对接，但强调了染色质可及性和结构约束对 TF 结合的影响，提示物理模拟需考虑染色质环境而非仅孤立的 TF–DNA 结构。
- 模型可解释性不是附加功能，而是生物学发现的前提；黑箱预测无法转化为可检验的机制假说。

---

## 07 方法总览

本文为综述，无统一方法流程。按主题归纳各方法类别的输入-输出流程：

**A. 表达数据 TRN 构建**
- 输入：bulk RNA-seq 或 scRNA-seq 表达矩阵（基因 × 样本/细胞）
- 处理：数据归一化、缺失值处理（单细胞需插补）、基因过滤
- 方法：相关分析（Pearson/Spearman）、偏相关、互信息（需离散化）、回归（线性/非线性）、贝叶斯网络、SVM/RF/KNN 等监督分类
- 输出：基因-基因互作网络（有向/无向）、TF-靶基因调控关系
- 反馈回路：无（多为静态网络）

**B. 表观基因组整合 TRN 构建**
- 输入：scRNA-seq + scATAC-seq（多组学）、motif 数据库（JASPAR、CIS-BP）
- 处理：TF motif 扫描、足迹分析、染色质可及性峰-基因关联
- 方法：SCENIC+（LDA + 调控子）、SCREG（NMF）、IReNA（决策树）、DIRECT-NET（梯度提升）、Dictys（随机过程建模）、scMEGA（信号相关）
- 输出：细胞类型特异的 TF-增强子-靶基因调控网络
- 反馈回路：部分方法（如 Dictys）用随机过程建模动态调控

**C. 深度学习序列模型**
- 输入：DNA 序列（one-hot 编码）、可选染色质特征
- 架构：CNN（DeepBind、DeepSea、BPNet、DeepSTARR、LegNet）、CNN+Transformer（Enformer）、GNN（图结构输入）
- 训练：监督学习（MPRA/STARR-seq/ChIP-seq 标签）、自监督（部分）
- 输出：TF 结合概率、增强子活性、表达水平预测
- 可解释性：DeepLIFT/TF-MoDISco 提取 motif

**D. 功能实验（数据生成）**
- MPRA：候选调控序列 → 克隆到报告载体 → 转染/转导 → 测序定量 → 调控活性分数
- STARR-seq：基因组片段 → 克隆到 3'UTR → 自身转录驱动 → 测序定量 → 增强子活性
- CRISPRi/a：sgRNA 文库 → dCas9-KRAB/p300 → 靶向调控元件 → 表达变化 → 功能注释

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 表达数据统计方法（相关/互信息/回归） | 从共表达推断调控关系 | 基础方法、计算简单、可处理 bulk 数据 | 输入：表达矩阵；输出：无向/有向网络 | 文中引用 WGCNA、互信息方法等 | 预期影响：失去基线方法，无法对比新方法优劣（未做消融实验） |
| 监督学习（SVM/RF/KNN） | 将 TRN 构建转为二分类 | 在单细胞数据上优于无监督方法 | 输入：表达特征对；输出：互作/非互作 | 引用文献 6 的综合评测 | 预期影响：失去强基线，尤其在小样本场景（未做消融实验） |
| 深度学习序列模型（CNN/Transformer） | 从序列直接预测调控活性 | 自动特征提取、捕捉非线性与长程依赖 | 输入：DNA 序列；输出：结合/活性预测 | DeepBind、Enformer、BPNet 等 | 预期影响：失去最先进预测能力；可解释性分析（TF-MoDISco）无法进行 |
| 可解释性工具（DeepLIFT/TF-MoDISco） | 从训练好的网络提取 motif | 黑箱模型无法直接产生生物学假说 | 输入：训练好的 CNN；输出：motif 集 | 文中明确提及 | 预期影响：模型预测无法转化为可检验的机制假说 |
| MPRA/STARR-seq | 功能性验证调控元件活性 | 提供因果性读出，弥补 ChIP-seq 等相关性方法 | 输入：候选序列文库；输出：活性分数 | 文中多处引用 | 预期影响：失去高质量训练/验证数据，AI 模型缺乏监督信号 |
| CRISPRi/a 筛选 | 扰动调控元件观察表型 | 建立因果联系，验证网络预测 | 输入：sgRNA 文库；输出：表达变化/表型 | 文中引用多项研究 | 预期影响：失去因果验证手段，网络预测无法闭环 |
| 单细胞多组学整合（SCENIC+ 等） | 构建细胞类型特异 TRN | 解析异质性、细胞状态特异调控 | 输入：scRNA+scATAC；输出：细胞特异网络 | 文中引用 | 预期影响：失去细胞分辨率，无法解析发育/疾病中的动态调控 |

---

## 09 关键公式符号

本文为综述，未给出具体数学公式。以下为文中提及方法所涉及的概念性符号/度量（基于文中描述，非原文公式）：

| 符号/概念 | 含义 | 用途 | 来源 |
|-----------|------|------|------|
| Pearson/Spearman 相关系数 | 基因表达两两线性/单调相关 | 构建共表达网络 | Expression-based methods 节 |
| 偏相关 | 控制其他变量后的条件相关 | 区分直接/间接互作 | Expression-based methods 节 |
| 互信息（MI） | 基于 KL 散度的变量间信息共享量 | 捕捉非线性依赖 | Expression-based methods 节 |
| 精度矩阵（协方差逆矩阵） | 条件独立关系编码 | 高斯图模型推断 | Expression-based methods 节（隐含） |
| 归一化经验概率函数矩阵 | 将表达数据转为图像表示 | CNN 输入 | Deep learning methods 节（文献 78） |
| 注意力权重 | 序列位置间相关性 | Transformer/注意力机制 | DeepGRM、STGRNS 节 |
| 扩散/去噪目标 | 预测添加噪声 | 扩散模型训练 | RegDiffusion 节 |

> 注：以上符号为文中方法描述的概念性归纳，非原文显式公式。原文未提供任何数学公式。

---

## 10 实验设计与证据链

本文为综述，无原始实验。以下为文中引用的代表性研究及其证据类型：

**数据集/群体**：
- 文中提及的数据资源：ENCODE（多细胞类型 TF ChIP-seq、染色质状态）、JASPAR/CIS-BP（TF motif）、ReMap/UniBind（TF 结合位点汇总）、MPRA/STARR-seq 数据集（如肝脏增强子、全基因组 STARR-seq）、单细胞多组学数据（scRNA-seq + scATAC-seq）
- 规模：未提供具体数字

**指标**：
- TRN 推断：AUROC、AUPRC（文献 6 的评测）
- 序列模型：预测与实验活性相关性、AUC（DeepBind、Enformer 等）
- 可解释性：motif 恢复率（TF-MoDISco）

**基线**：
- 监督 vs 无监督方法对比（文献 6）
- CNN vs Transformer 架构对比（Enformer vs Basenji 等）

| 实验/研究 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|-----------|-------------|------------|------|-------------|-------------------|------|
| 文献 6 综合评测 | 监督方法优于无监督方法 | SVM/RF/KNN vs 相关/互信息/贝叶斯，单细胞表达数据 | 监督方法表现更优 | 监督学习适合单细胞 TRN 推断 | 未证明在 bulk 数据上同样成立；未评估泛化性 | Expression-based methods 节 |
| DeepBind | CNN 可从序列预测 TF 结合 | 多 TF ChIP-seq 数据集 | 高 AUC | 序列信息足以预测结合 | 未解释结合机制；跨细胞类型泛化有限 | TF binding identification 节 |
| BPNet | 碱基分辨率结合预测 + 可解释 motif | ChIP-exo 数据 | 识别复合 motif、间接结合足迹 | 可解释 CNN 能揭示结合语法 | 仅限少数 TF；需高分辨率数据 | 同上 |
| Enformer | Transformer 捕捉长程调控 | 预测表达 vs Basenji | 长程预测改善 | 注意力机制增强长程依赖建模 | 计算成本高；可解释性仍有限 | Identifying promoters, enhancers 节 |
| 文献 198（Georgakopoulos-Soares 2023） | TFBS 方向影响调控活性 | 209,440 序列 lentiMPRA | 方向显著影响表达 | 调控语法包含方向性 | 仅测试特定 TFBS 组合 | Deciphering cis-regulatory sequences 节 |
| 文献 24（Agarwal 2023） | 序列特征预测 CRE 活性 | 680,000+ 序列 lentiMPRA，3 细胞类型 | 准确预测 CRE 功能 | 序列模型可泛化至多细胞类型 | 限于测试的细胞类型 | 同上 |
| 文献 106（Klein 2020） | MPRA 实验设计影响结果 | 序列长度、测定设计、方向对比 | 长度影响最大 | 实验设计需标准化 | 未提供最优设计准则 | MPRA 节 |

---

## 11 结论正确解读

**任务范围**：
- 本文是方法学综述，覆盖 TRN 构建（表达/表观/序列）和顺式调控元件功能验证（MPRA/STARR-seq/CRISPR）两大板块，不涉及蛋白质结构、分子动力学或物理模拟。

**oracle/真值输入**：
- 文中讨论的监督学习方法依赖实验标注（如 ChIP-seq 峰、MPRA 活性）作为真值；这些真值本身有噪声和实验偏差。

**端到端状态**：
- 文中描述的 AI 模型（如 Enformer、BPNet）是端到端序列→功能预测，但未达到「序列→机制理解」的端到端；可解释性分析是事后步骤。

**算力成本**：
- 文中提及 Transformer 模型计算成本高（Enformer），但未提供具体数字。

**历史数据依赖**：
- 所有模型依赖已有实验数据（ENCODE、MPRA 等）训练；数据质量直接决定模型性能。

**模型依赖**：
- 不同架构（CNN vs Transformer vs GNN）在不同任务上各有优劣，无统一最优解。

**最难情形**：
- 细胞类型特异性调控、远端增强子-启动子互作、TF 协同/竞争结合、染色质环境效应。

**群体/领域边界**：
- 本文结论主要基于人类和模式生物（果蝇、小鼠）数据；对非模式生物、植物等领域的适用性未讨论。

**不确定性**：
- 作者明确指出湿实验技术（如 MPRA）可重复性问题、深度学习模型可解释性不足、Transformer 性能可能被高估。

**有边界的复述**：
本文主张：在现有技术条件下，整合表达数据、表观遗传数据和序列数据，结合 MPRA/STARR-seq 功能验证和可解释深度学习，能够部分解析顺式调控语法，但受限于数据质量、模型可解释性和细胞类型特异性，尚无法实现从序列到调控机制的完整预测。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 湿实验技术可重复性差 | 即使同一实验的重复之间也出现较差可重复性 | 未明确提及 | MPRA 节（引用 106） |
| 深度学习模型可解释性不足 | CNN/RNN 等黑箱模型提供准确预测但缺乏机制解释 | 强调需要更多可解释 AI 技术 | Conclusions 节 |
| Transformer 模型性能可能被高估 | 某些测试场景下质量被高估 | 未明确提及 | Identifying promoters, enhancers 节（引用 194-195） |
| 单细胞数据计算挑战 | 数据量大、dropout 和噪声问题 | 需要设计高效处理单细胞数据的方法 | Expression-based methods 节末段 |
| 表达数据方法无法捕捉 TF 结合特异性 | 相关/互信息方法不含序列信息 | 整合序列和表观数据 | Introduction 节 |
| MPRA 的游离体环境局限 | 游离体与基因组整合环境中的调控活性有差异 | 开发整合型 MPRA 方法 | MPRA 节（引用 106） |

**作者提及的相关约束**（非正式局限）：
- 监督学习方法依赖高质量标注数据，而 wet lab 技术（如 MPRA）的可重复性问题直接影响训练数据质量。
- 单细胞数据虽然规模大，但噪声和稀疏性可能引入假阳性/假阴性互作。
- 现有模型多针对特定细胞类型或物种，跨条件泛化能力未充分验证。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 综述对「表达数据方法无法建模 TF 结合特异性」的论断可能过于绝对 | 部分方法（如回归模型）可整合 motif 特征作为协变量 | 影响方法选择策略 | 检查是否有整合序列特征的表达方法被遗漏 | Expression-based methods 节 |
| 对深度学习模型的讨论集中于 CNN/Transformer，未充分讨论物理模拟或结构预测方法 | 结构预测（如 AlphaFold）和 MD 模拟在 TF–DNA 互作中也有应用 | 课题方向需了解全谱方法 | 检索该综述是否引用结构生物学方法 | 全文未提及 MD/对接/结构预测 |
| 对 MPRA 可重复性问题的描述缺乏量化数据 | 未提供具体重复性指标（如相关系数） | 无法评估问题严重程度 | 查阅引用文献 106 的原始数据 | MPRA 节 |
| 对监督方法优于无监督方法的结论依赖单一评测（文献 6） | 不同数据集/物种上结论可能不同 | 方法选择需考虑场景 | 查阅文献 6 的评测范围 | Expression-based methods 节 |
| 综述未讨论数据预处理和批次效应对 TRN 推断的影响 | 批次效应可能引入假互作 | 影响模型可靠性 | 检查文中是否提及批次效应 | 全文未提及 |
| 对「cis-regulatory grammar」的定义较为宽泛 | 不同研究对 grammar 的理解不同（motif 组合 vs 空间组织 vs 动力学） | 影响问题框架 | 检查文中是否给出精确定义 | 全文未给出统一定义 |
| 综述未讨论 AI 模型在罕见变异解读中的具体性能 | 疾病变异解读是重要应用场景 | 影响临床转化评估 | 检查文中是否提及 ClinVar 等资源 | 仅提及疾病关联，未讨论具体性能 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

**K1: 多模态数据整合是解析 TF–DNA 结合机制的关键**
- 来源：本文反复强调表达数据 + 表观数据 + 序列数据整合的必要性
- 迁移到本课题：TF–DNA 结合预测模型不应仅使用序列，应整合染色质可及性（ATAC-seq）、组蛋白修饰（ChIP-seq）和 3D 基因组结构（Hi-C）作为特征。可设计多模态深度学习架构，输入层分别编码序列（one-hot）、可及性（连续值）、修饰（分类值），在中间层融合。

**K2: MPRA/STARR-seq 是连接序列变异与功能的高质量训练数据源**
- 来源：文中详述 MPRA/STARR-seq 可并行测试数千至数百万序列的调控活性
- 迁移到本课题：构建 TF–DNA 结合预测模型时，可使用 MPRA/STARR-seq 数据作为监督信号，而非仅依赖 ChIP-seq（后者分辨率低、受抗体质量影响）。特别是饱和突变 MPRA 数据（如文献 118）可用于训练变异效应预测模型。

**K3: 可解释性分析（如 TF-MoDISco + DeepLIFT）是从黑箱模型提取生物学机制的必要步骤**
- 来源：文中讨论 TF-MoDISco 利用 DeepLIFT 从 CNN 提取 motif
- 迁移到本课题：训练 TF 结合预测模型后，应使用可解释性工具（如 DeepLIFT、SHAP、Integrated Gradients）提取模型学到的 motif，与已知 JASPAR motif 比对验证，并发现新 motif。这比单纯追求预测精度更有生物学价值。

**K4: 单细胞多组学为细胞类型特异的 TF–DNA 结合研究提供新维度**
- 来源：文中讨论 scRNA-seq + scATAC-seq 构建细胞类型特异 TRN
- 迁移到本课题：TF 结合具有细胞类型特异性，bulk 数据掩盖了这种异质性。可设计单细胞水平的 TF 结合预测模型，利用 scATAC-seq 的足迹分析推断单细胞 TF 结合，或使用多组学整合方法（如 SCENIC+）在单细胞分辨率下研究 TF–DNA 互作。

**K5: 实验设计对模型训练数据质量有决定性影响**
- 来源：文中引用文献 106 指出 MPRA 实验设计（序列长度、方向、测定设计）对结果有最大影响
- 迁移到本课题：使用公共 MPRA/STARR-seq 数据训练模型时，需注意实验设计差异（如序列长度、载体类型、细胞类型），必要时进行批次校正或仅使用相同设计的数据。模型泛化能力受训练数据实验设计异质性限制。

**K6: 监督学习方法在单细胞 TRN 推断中优于无监督方法**
- 来源：文中引用文献 6 的综合评测
- 迁移到本课题：在构建 TF–DNA 结合预测模型时，优先考虑监督学习（如有标注数据），而非无监督聚类或相关分析。但需注意监督方法对标注质量的依赖。

**K7: CRISPRi/a 筛选可验证 AI 模型预测的因果性**
- 来源：文中讨论 CRISPRi/a 可测试顺式调控元件的必要性/充分性
- 迁移到本课题：AI 模型预测的候选调控元件或 TF 结合位点，可通过 CRISPRi/a 实验进行因果验证。这为「计算预测 → 实验验证」的闭环提供了范式。

**K8: 模型可解释性与预测精度同等重要**
- 来源：文中多处强调可解释性挑战
- 迁移到本课题：在发表 TF–DNA 结合预测模型时，应同时提供可解释性分析（motif 提取、注意力权重可视化、突变敏感性分析），以增强生物学可信度和可检验性。

---

## 15 与已有知识连接

**可核验的外部文献**：
- ENCODE 联盟（参考文献 17）：提供 TF ChIP-seq、染色质状态等全基因组数据，是 TF–DNA 结合模型训练的标准数据源。
- JASPAR（参考文献 18-19）：TF motif 数据库，可用于验证模型提取的 motif。
- CIS-BP（参考文献 18-19）：跨物种 TF motif 数据库。
- ReMap（参考文献 20-21）：TF 结合位点汇总数据库。
- UniBind（参考文献 20-21）：统一格式的 TF 结合位点数据库。
- BEELINE 框架（参考文献 77）：TRN 推断方法基准测试平台，可用于评估新方法。
- DeepBind（参考文献 168）：早期 CNN 预测 TF 结合的经典工作。
- DeepSea（参考文献 169）：预测非编码变异效应的 CNN 模型。
- DanQ（参考文献 170）：结合 CNN 和 RNN 的模型。
- Basset（参考文献 172）：预测染色质可及性的 CNN。
- BPNet（参考文献 175）：碱基分辨率 TF 结合预测 + 可解释性分析。
- Enformer（参考文献 190）：Transformer 架构预测基因表达。
- TF-MoDISco（参考文献 173）：从 CNN 提取 motif 的工具。
- SCENIC+（参考文献 82）：单细胞多组学 TRN 推断。
- Georgakopoulos-Soares et al. 2023（参考文献 198）：TFBS 方向对调控活性的影响。
- Agarwal et al. 2023（参考文献 24）：大规模 lentiMPRA 构建 CRE 功能图谱。
- Klein et al. 2020（参考文献 106）：MPRA 实验设计系统比较。

**与用户已有知识的连接**：
- 若用户熟悉 ChIP-seq 数据分析：本文提供了 ChIP-seq 的替代/补充方法（MPRA/STARR-seq、CUT&Tag/RUN），可扩展实验数据获取思路。
- 若用户熟悉 CNN 序列模型：本文的 BPNet、DeepSTARR 案例可作为可解释性设计的参考。
- 若用户熟悉 MD 模拟：本文未涉及 MD，但强调了染色质可及性和结构约束，提示 MD 模拟需考虑染色质环境（如核小体占据、TF 竞争）。

**候选方向（标注为候选）**：
- [候选] 将 MPRA 饱和突变数据与 AlphaFold 结构预测结合，研究 TF 结合位点变异对蛋白-DNA 结合亲和力的影响。
- [候选] 利用 Enformer 的注意力权重识别远端增强子-启动子互作，再通过 Hi-C 数据验证。
- [候选] 将 TF-MoDISco 提取的 motif 与 MD 模拟的 TF-DNA 结合构象进行交叉验证。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

**R1: 基于 MPRA 饱和突变数据的 TF–DNA 结合特异性可解释深度学习模型**
- 来源局限/观察：现有 TF 结合预测模型多基于 ChIP-seq，分辨率低且受抗体质量影响；MPRA 可提供碱基分辨率的调控活性数据，但尚未被充分利用。
- 核心假设：MPRA 饱和突变数据可训练出比 ChIP-seq 数据更高分辨率的 TF–DNA 结合特异性模型，且模型学到的 motif 与已知 JASPAR motif 高度一致。
- 初步方法：收集公开 MPRA 饱和突变数据集（如文献 118），构建 CNN 或 Transformer 模型预测调控活性；使用 DeepLIFT/TF-MoDISco 提取 motif；与 JASPAR 比对验证；在独立数据集上测试泛化。
- 验证方式：与现有 ChIP-seq 模型（DeepBind、BPNet）对比 AUROC/AUPRC；motif 恢复率；在疾病相关变异（ClinVar）上测试预测能力。
- 创新状态：partially checked（MPRA 数据已被用于训练模型，但系统性的碱基分辨率模型 + 可解释性分析 + 疾病变异解读的整合尚不充分）

**R2: 整合 3D 基因组结构的 TF–DNA 结合预测模型**
- 来源局限/观察：本文强调染色质结构约束对 TF 结合的影响，但现有序列模型（如 DeepBind、Enformer）未显式整合 3D 基因组结构信息。
- 核心假设：将 Hi-C 衍生的染色质区室/拓扑关联域（TAD）信息作为特征，可显著提高远端调控元件上的 TF 结合预测精度。
- 初步方法：以 Enformer 为基础架构，在输入层增加 Hi-C 衍生的染色质状态特征（如区室 A/B、TAD 边界距离）；在 ENCODE 数据上训练；比较有无结构特征的性能差异。
- 验证方式：在独立细胞类型上测试跨细胞泛化；消融实验验证结构特征的贡献；与 HiChIP 数据交叉验证。
- 创新状态：unverified（现有模型多为序列+染色质可及性，显式整合 3D 结构的较少）

**R3: 基于扩散模型的顺式调控序列生成与语法解析**
- 来源局限/观察：本文讨论深度学习可生成合成增强子（如 ExpressionGAN），但生成模型的可控性和语法可解释性不足。
- 核心假设：扩散模型（diffusion model）可生成具有指定调控语法特征的合成顺式调控序列，且生成过程可反推语法规则。
- 初步方法：使用 STARR-seq 数据训练扩散模型，条件生成具有特定活性水平的增强子序列；通过反向过程分析生成序列的 motif 组合规律；与 DeepSTARR 的语法预测对比。
- 验证方式：生成的序列在 MPRA 中实验验证；语法规则与已知调控语法模型（增强体/账单模型）对比。
- 创新状态：unverified（扩散模型在调控序列生成中的应用尚属新兴）

**R4: 单细胞多组学驱动的细胞类型特异 TF–DNA 结合预测**
- 来源局限/观察：本文讨论单细胞多组学构建 TRN 的进展，但现有 TF 结合预测模型多为 bulk 水平，未充分利用单细胞分辨率。
- 核心假设：利用 scATAC-seq 足迹分析推断的单细胞 TF 结合信号，可训练出细胞类型特异的 TF 结合预测模型，优于 bulk 模型。
- 初步方法：收集多细胞类型 scATAC-seq 数据，提取足迹信号作为训练标签；使用序列 + 染色质可及性特征训练模型；在独立单细胞数据上验证。
- 验证方式：与 bulk ChIP-seq 模型对比；跨细胞类型泛化测试；在发育/疾病数据上验证细胞类型特异预测。
- 创新状态：unverified（单细胞 TF 结合预测模型尚不成熟）

**R5: 结合 AlphaFold 结构预测与 MPRA 功能数据的 TF–DNA 结合变异效应解析**
- 来源局限/观察：本文未涉及结构预测，但 TF–DNA 结合机制的核心是结构基础；AlphaFold 在蛋白-DNA 复合物预测上已有进展。
- 核心假设：AlphaFold 预测的 TF–DNA 复合物结构可解释 MPRA 测得的变异效应，结构特征（如结合界面残基、氢键网络）可提升变异效应预测精度。
- 初步方法：对已知 TF–DNA 复合物进行 AlphaFold 预测，提取结构特征；与 MPRA 变异效应数据关联；训练结构感知的变异效应预测模型。
- 验证方式：与纯序列模型对比；在独立变异数据集上验证；结构预测与实验结构（PDB）对比。
- 创新状态：unverified（AlphaFold 在蛋白-DNA 复合物预测上仍具挑战，但方向可行）

**R6: 可解释性驱动的顺式调控语法规则提取框架**
- 来源局限/观察：本文强调深度学习可解释性不足，TF-MoDISco 等工具提取 motif 但未系统提取语法规则。
- 核心假设：通过系统扰动训练好的序列模型（如 in silico mutagenesis），可提取 motif 之间的协同/拮抗关系，形式化为语法规则。
- 初步方法：以 DeepSTARR 或 BPNet 为基础，对训练好的模型进行系统突变扫描；聚类分析突变效应模式；构建 motif-motif 互作图；与已知语法模型对比。
- 验证方式：提取的语法规则在 MPRA 数据上验证；与增强体/账单模型预测对比。
- 创新状态：partially checked（in silico mutagenesis 已有应用，但系统语法规则提取尚不充分）