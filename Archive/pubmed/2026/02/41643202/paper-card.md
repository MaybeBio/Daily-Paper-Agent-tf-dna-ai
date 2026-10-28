## 01 基本信息
- **标题**：Deciphering hierarchical regulatory network of cell fate via an epigenetics-informed heterogeneous graph transformer on single-cell multi-omics data
- **作者**：Huang, Yuhong; Liu, Chao; Yang, Zhiling; Liu, Bo; Zhai, Xiao; Zheng, Jiajin; Xiao, Jing; Song, Tao
- **单位**：未提供（推测为大连医科大学，依据基金信息）
- **期刊/平台**：Briefings in Bioinformatics
- **年份**：2026（在线日期 2026-02-05）
- **论文类型**：方法学（算法开发 + 应用验证）
- **领域**：单细胞多组学、基因调控网络推断、图深度学习
- **关键词**：hierarchical regulatory network; single-cell multi-omics; heterogeneous graph transformer; transcription factor; cis-regulatory element; cell fate
- **DOI/arXiv**：10.1093/bib/bbaf664
- **代码**：https://github.com/YuHongHuang-lab/SMOGT
- **数据**：GEO、10x Genomics、ENCODE、TCGA（详见补充表 S1–S3）
- **阅读日期**：2026-05-13
- **在本课题方向中的位置**：本文属于「TF–DNA 结合机制 × AI 方法」交叉方向，核心贡献是将表观遗传层级调控逻辑（TF-TF → TF-CRE → CRE-CRE → CRE-TG）显式编码为异质图 Transformer 的元路径，用于从单细胞多组学数据推断因果调控网络，并支持扰动模拟与细胞命运预测。与物理模拟（MD/对接）无直接关联，但为 TF–CRE 结合预测提供了可迁移的图表示学习框架。

## 02 一句话总结
针对现有单细胞调控网络推断方法忽略层级性与因果性的问题，SMOGT 将表观遗传层级调控逻辑编码为异质图 Transformer 的元路径（TF-TF → TF-CRE → CRE-CRE → CRE-TG），通过半监督学习从配对 scRNA-seq 和 scATAC-seq 数据构建层级调控网络，在 ChIP-seq/Hi-C 基准上显著提升 TF–CRE 与 CRE–CRE 预测精度，并驱动下游的驱动因子识别与扰动模拟。

## 03 研究问题
- **具体问题**：如何从单细胞多组学数据中推断具有层级结构和因果属性的转录调控网络（HRNet），并利用该网络准确识别驱动细胞命运的 TFs 和 CREs、预测扰动响应？
- **为什么重要**：细胞命运决定由 TFs 和 CREs 通过层级因果作用精确调控。准确建模这一层级因果逻辑是理解发育和疾病（如 AML、黑色素瘤 EMT）中细胞命运转变机制的基础，也是构建"虚拟细胞"的关键环节。
- **现有方法不足**：(1) 统计相关（SC）和线性回归（LR）方法（如 FigR、TRIPOD、SCENIC+）难以区分直接与间接效应，无法捕捉非线性长程互作；(2) 概率图模型（PGM）常省略 CREs 或简化其角色；(3) 已有深度学习方法（如 regX、LINGER）虽整合 PPI，但网络结构多为单层，未显式建模 TF-TF 协同、CRE-CRE 长程染色质互作等层级表观遗传逻辑；(4) 注意力机制在现有 HGT 应用中未遵循生物学层级约束。
- **精确研究问题**：Can an epigenetics-informed heterogeneous graph transformer, which structures information flow along a hierarchical meta-path (TF-TF → TF-CRE → CRE-CRE → CRE-TG), accurately infer causal regulatory networks from single-cell multi-omics data and predict cell fate responses to perturbations?

## 04 背景与发展脉络
*注：以下脉络基于本文框架及文中引用，标记为「经外部核验」的部分来自文中明确引用的文献。*

1. **统计相关与回归时代**（FigR、TRIPOD、SCENIC+）：基于 TF 表达与 CRE 可及性/基因表达的统计关联或多元回归推断调控关系。优点：计算简单、可解释；局限：无法区分直接/间接效应，忽略非线性与长程互作（本文 Introduction 第 2 段）。
2. **概率图模型时代**（scMTNI、MAGICAL）：引入概率图模型刻画条件依赖。优点：可建模因果结构；局限：为降低复杂度常省略 CREs 或简化层级，难以扩展到全基因组尺度（Introduction 第 2 段）。
3. **先验知识 + 机器学习时代**（STREAM、REUNION）：STREAM 将 TF-CRE 推断建模为 Steiner Forest 问题；REUNION 用半监督学习以高置信互作作为伪标签。优点：引入结构先验；局限：受限于先验覆盖度，且仅建模部分 TF-CRE-TG 关系（Introduction 第 2 段）。
4. **深度学习 + 图神经网络时代**（regX、LINGER、CEFCON、DeepMAPS、scMultiomeGRN）：regX 和 LINGER 整合 PPI 网络增强信号传播；DeepMAPS 和 scMultiomeGRN 首次将 HGT 应用于单细胞多组学。优点：可扩展、能捕捉非线性；局限：注意力机制未遵循生物学层级约束，网络结构多为单层或双组学，未完整建模 TF-TF → TF-CRE → CRE-CRE → CRE-TG 的层级因果流（Introduction 第 3 段）。
5. **本文位置**：在上述脉络上，SMOGT 首次将表观遗传层级调控逻辑显式编码为 HGT 的元路径，以半监督方式联合优化网络拓扑与节点表示，填补了"层级性 + 因果性 + 多组学整合"的空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 层级性缺失 | 现有方法仅建模单层 TF-CRE 或 TF-TG 关系，忽略 TF-TF 协同与 CRE-CRE 长程互作 | 作者认为调控本质是层级因果流（TF-TF → TF-CRE → CRE-CRE → CRE-TG），单层模型无法承载该逻辑 | Introduction 第 1–3 段；图 1B 元路径设计 |
| 因果性不足 | 统计相关/回归方法无法区分直接与间接效应 | 表达相关性不等于因果性，需结构化的信息流约束 | Introduction 第 2 段（对 SC/LR 的批评） |
| 注意力机制偏离生物学 | 已有 HGT 应用的注意力未遵循表观遗传层级约束 | 注意力应沿生物学元路径流动，而非任意节点间 | Introduction 第 3 段（对 DeepMAPS、scMultiomeGRN 的批评）；图 1B |
| 网络稀疏性与假阳性 | 全基因组尺度上已知调控边极少，监督信号不足 | 需要半监督策略利用高置信互作作为伪标签 | Methods "Loss function and training process" 节；图 1C |
| 扰动模拟失真 | 单层网络无法传播 TF 扰动的长程效应（如通过 CRE-CRE 的 3D 基因组效应） | 信息流在单层网络中截断，无法模拟真实表观遗传传播 | Introduction 第 4 段；Results 图 3B |

## 06 核心思想
1. **表面方法**：构建一个异质图 Transformer（HGT），节点为 TFs、CREs、TGs，边为四类（TF-TF、TF-CRE、CRE-CRE、CRE-TG）。注意力机制沿表观遗传层级元路径（TF-TF → TF-CRE → CRE-CRE → CRE-TG）流动，通过半监督学习（网络重建 + 基因表达预测双任务）联合优化。下游模块包括 MRWR_Pert（预测 TF 扰动基因）、MRWR_CTS（识别驱动因子）、Louvain_Co-CRE（发现共调控 CRE 模块）。
2. **核心洞察**：调控网络不是扁平图，而是具有明确层级因果流的异质图。将"信息如何流动"这一生物学先验编码为元路径，比让模型自由学习注意力更符合表观遗传机制，从而在数据稀疏时仍能准确推断调控关系。层级因果流的设计使网络天然支持扰动传播模拟。
3. **可能的普适教训** [Analysis]：在生物网络推断中，将领域机制知识（如调控层级、信号传播方向）显式编码为模型架构约束（元路径、信息流方向），比单纯增加模型容量或数据量更有效。这一原则可迁移到其他"层级因果"生物系统（如信号通路、代谢网络）的图学习建模。

## 07 方法总览
- **输入**：配对的单细胞 scRNA-seq（基因表达矩阵）和 scATAC-seq（染色质可及性矩阵），以及先验的 TF-TF（PPI）、CRE-TG（启动子-基因）关系。
- **输出**：层级调控网络 HRNet（含 TF-TF、TF-CRE、CRE-CRE、CRE-TG 四类边及权重）、驱动因子排序、扰动响应预测、共调控 CRE 模块。
- **模块**：
  1. **特征编码器**：TF 用表达特征，CRE 用可及性特征，TG 用表达特征；三种 GNN 编码器（GCN 用于 TF-TF，HGT 用于 TF-CRE/CRE-CRE/CRE-TG，GraphSAGE 用于 Loop）。
  2. **层级元路径注意力**：注意力沿 TF-TF → TF-CRE → CRE-CRE → CRE-TG 方向流动，每层输出更新节点表示。
  3. **双任务解码器**：网络重建（BLCE 损失，处理边稀疏不平衡）+ 基因表达预测（MSE 损失，4 层 FCNN）。
  4. **下游模块**：MRWR_Pert（以扰动 TF 为种子，多层随机游走预测受影响基因）、MRWR_CTS（以 DEGs 为种子，反向游走识别驱动 TFs/CREs）、Louvain_Co-CRE（对 CRE 表示聚类，识别共调控模块）。
- **训练**：半监督，总损失 = 网络重建损失 + 基因表达预测损失（加权组合）。伪标签来自高置信 TF-CRE/CRE-CRE 对（基于表达相关性阈值）。
- **文字流程**：输入多组学数据 → 构建异质图（节点+先验边）→ 特征编码 → 沿层级元路径的 HGT 注意力传播（多轮）→ 双任务解码（重建网络 + 预测表达）→ 输出优化后的 HRNet → 下游模块（MRWR、Louvain）进行驱动因子识别、扰动模拟、共调控模块发现。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 层级元路径注意力（HGT） | 沿 TF-TF → TF-CRE → CRE-CRE → CRE-TG 方向计算注意力并传播信息 | 将表观遗传层级因果逻辑编码为信息流约束，避免任意节点间注意力 | 输入：异质图节点特征；输出：更新后的节点表示 | 图 2A：TF-CRE 预测显著优于 6 个基线；补充图 S3：消融实验显示层级元路径设计贡献最大 | 预期影响 [Analysis]：移除后退化为普通 HGT，层级因果信息丢失，TF-CRE 预测精度下降（文中补充图 S3 支持） |
| 半监督学习策略 | 用高置信互作对作为伪标签，联合优化网络重建与表达预测 | 全基因组已知边稀疏，需伪标签扩充监督信号 | 输入：先验边 + 伪标签边；输出：优化后的边权重 | Methods "Loss function" 节；图 1C | 预期影响 [Analysis]：移除后监督信号不足，网络稀疏性导致预测精度下降 |
| 双任务解码器（BLCE + MSE） | 同时优化网络拓扑重建与基因表达预测 | 网络结构学习与功能预测相互促进，增强表示质量 | 输入：节点表示；输出：边概率 + 表达预测值 | Methods "Dual-task decoder" 节 | 预期影响 [Analysis]：移除表达预测任务后，表示可能过度拟合网络拓扑，泛化性下降 |
| MRWR_Pert | 多层随机游走预测 TF 扰动后的受影响基因 | 验证 HRNet 能否传播扰动信号，评估网络因果性 | 输入：HRNet + 扰动 TF；输出：受影响基因排序 | Results 图 3B：K562 Perturb-seq 富集显著高于基线网络 | 预期影响 [Analysis]：移除后无法验证网络因果传播能力 |
| MRWR_CTS | 从 DEGs 反向游走识别驱动 TFs/CREs | 将网络拓扑与细胞命运转变关联，识别因果驱动因子 | 输入：HRNet + DEGs；输出：驱动因子排序 | Results 图 5E：BM 谱系驱动因子识别优于 SCENIC+、CEFCON、STREAM | 预期影响 [Analysis]：移除后驱动因子识别退化为单纯差异表达分析 |
| Louvain_Co-CRE | 对 CRE 表示聚类，发现共调控模块 | 识别协同工作的 CRE 群组，关联疾病位点 | 输入：CRE 节点表示；输出：共调控模块 | Results 图 4B–D：GWAS/eQTL/SE 富集显著高于 Cicero、ArchR | 预期影响 [Analysis]：移除后无法发现 CRE 协同模块，疾病位点富集分析不可行 |

## 09 关键公式符号
*注：原文公式以 LaTeX 呈现，以下为理解必需的公式。*

1. **GCN 层**（TF-TF 编码）：
   H^(l) = σ( D̃^(-1/2) Ã D̃^(-1/2) H^(l-1) W^(l-1) )
   - Ã = A + I（A 为邻接矩阵，I 为单位阵）
   - D̃_ii = Σ_j Ã_ij（度矩阵）
   - H^(l-1) 为第 l-1 层激活，H^0 = X^TF（TF 特征矩阵）
   - W^(l-1) 为可训练权重
   - σ(·) 为激活函数（ReLU/Sigmoid）
   - 用途：聚合 TF-TF 互作信息，更新 TF 节点表示

2. **HGT 注意力**（TF-CRE、CRE-CRE、CRE-TG 编码）：
   Attention(s, e, t) = Softmax( (Q(s) · K(e, t)) / √d )
   - Q(s) 为源节点查询向量，K(e, t) 为目标节点-边类型键向量
   - d 为特征维度
   - 用途：沿元路径计算异质注意力权重，控制信息流动方向

3. **GraphSAGE 聚合**（Loop 编码）：
   h_v^(l) = σ( W · CONCAT(h_v^(l-1), AGGREGATE({h_u^(l-1), ∀u ∈ N(v)})) )
   - AGGREGATE 可为 mean/pool/LSTM
   - CONCAT 保留自身与邻居信息
   - 用途：编码自环/循环调控关系

4. **总损失函数**：
   L_total = L_BLCE + λ · L_MSE
   - L_BLCE：平衡二元交叉熵（网络重建），引入类别权重 α 处理边稀疏
   - L_MSE：均方误差（基因表达预测）
   - λ：权重系数
   - 用途：联合优化网络拓扑与功能预测

5. **MRWR 迭代**（MRWR_Pert / MRWR_CTS）：
   s^(t+1) = (1 - β) · W^T · s^(t) + β · s^(0)
   - s^(t) 为节点得分向量，W 为归一化转移矩阵
   - β 为重启概率
   - 用途：从种子节点（扰动 TF 或 DEGs）出发，在网络中传播信号，识别受影响基因或驱动因子

## 10 实验设计与证据链
- **数据集**：7 个配对 scRNA-seq + scATAC-seq 数据集（BM、PBMC、人脑皮层、LSC、K562、HCT116、A549、GM12878），来源 GEO/10x/ENCODE（补充表 S1）。K562 Perturb-seq 用于扰动验证。GWAS/eQTL/SE 数据来自公共数据库。
- **基准真值**：TF-CRE 来自 ChIP-seq（补充表 S2），CRE-CRE 来自 Hi-C（补充表 S3）。
- **指标**：AUPR、AUC、最大 F1、富集分数（GWAS/eQTL/SE）、PCC（表达预测）。
- **基线**：regX、LINGER、TRIPOD、Pando、REUNION、Pearson（TF-CRE 预测）；Cicero、ArchR（CRE-CRE 预测）；SCENIC+、CEFCON、STREAM（驱动因子识别）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|-------------|-------------------|------|
| TF-CRE 预测 | SMOGT 优于现有方法 | 6 基线（regX、LINGER、TRIPOD、Pando、REUNION、Pearson），AUPR/F1 | SMOGT 显著最高（图 2A） | 层级元路径设计提升 TF-CRE 推断精度 | 未报告统计显著性检验细节 | Results 图 2A；补充图 S4 |
| CRE-CRE 预测 | SMOGT 优于滑动窗口方法 | Cicero、ArchR，AUC/AUPR，4 细胞系 | SMOGT 全面最优（图 2C） | 能捕捉长程染色质互作 | 未报告 Hi-C 分辨率对结果的影响 | Results 图 2C |
| 消融实验 | 层级元路径是关键设计 | 同构版本（无元路径）对比 | SMOGT 显著更高（补充图 S3） | 层级表观遗传约束是精度提升核心 | 未报告各组件独立消融的完整矩阵 | 补充图 S3 |
| 扰动基因预测 | HRNet 能传播 TF 扰动信号 | K562 Perturb-seq，富集分数 | SMOGT 网络显著富集 DEGs（图 3B） | 网络具有因果传播能力 | 未与 CellOracle 等专门扰动模型对比 | Results 图 3B |
| 表达预测 | HRNet 边权重有功能意义 | 与 regX、SCARlink 对比，3 数据集 | SMOGT 最高 PCC（图 3D–E） | 网络拓扑与表达调控一致 | 未报告预测误差的方差 | Results 图 3D–E |
| 驱动因子识别 | SMOGT 识别谱系特异 TFs | SCENIC+、CEFCON、STREAM，BM 谱系 | SMOGT top5/top10 富集谱系特异 TFs 最优（图 5E） | 层级网络提升驱动因子识别 | 未报告跨数据集一致性 | Results 图 5E；补充 S14 |
| 共调控模块 | SMOGT 识别疾病相关 CRE 模块 | GWAS/eQTL/SE 富集，与 Cicero/ArchR 对比 | SMOGT 模块富集最高（图 4B–D） | CRE 表示蕴含疾病相关功能信息 | 未报告模块稳定性分析 | Results 图 4B–D |
| 扰动模拟（KLF1/IRF8） | 网络能预测谱系转变方向 | 模拟敲除/过表达，观察谱系向量场 | KLF1 敲除抑制红系、IRF8 敲除抑制髓系（图 6B–F） | 网络具有机制可解释性 | 未与湿实验验证对比 | Results 图 6B–F |
| AML 预后 | Hub-CRE 有预后价值 | TCGA AML，LASSO + 生存分析 | 7 个 Hub-CRE 相关基因显著分层（图 4F–G） | 网络发现具有临床意义的非编码元件 | 未报告独立验证队列 | Results 图 4F–G |

## 11 结论正确解读
- **任务范围**：本文聚焦于从单细胞多组学数据推断细胞内层级调控网络（TF-TF → TF-CRE → CRE-CRE → CRE-TG），并利用该网络进行驱动因子识别、扰动模拟和疾病相关 CRE 发现。不涉及细胞间通讯、空间转录组或蛋白质结构预测。
- **oracle/真值输入**：TF-CRE 和 CRE-CRE 的真值来自 ChIP-seq 和 Hi-C 实验数据；TF-TF 和 CRE-TG 来自先验知识库。模型本身不预测全新 TF 结合基序，而是在已知调控框架内优化边权重。
- **端到端状态**：SMOGT 是端到端可训练的，但依赖先验边（TF-TF、CRE-TG）作为输入约束，并非完全从原始序列/染色质数据出发的端到端预测。
- **算力成本**：未报告训练时间、GPU 型号等具体算力信息。
- **历史数据依赖**：模型依赖配对 scRNA-seq + scATAC-seq 数据，且需要 ChIP-seq/Hi-C 作为监督信号，对数据质量要求较高。
- **最难情形**：从文中结果推断，K562 中 STREAM 在 top60-200 区间与 SMOGT 相当，提示在特定细胞系或高置信区间内，简单基序方法仍有竞争力；HCT116 中 SMOGT 在 top 区间表现相对较弱。
- **群体/领域边界**：验证限于血液系统（BM、AML）、免疫细胞（PBMC）、脑皮层、黑色素瘤及 4 个细胞系。结论外推到其他组织或物种需谨慎。
- **不确定性**：未报告置信区间、多次运行方差或统计显著性检验细节；扰动模拟未与湿实验验证对比。
- **有边界的复述**：SMOGT 在 7 个单细胞多组学数据集上，通过将表观遗传层级因果逻辑编码为 HGT 元路径，显著提升了 TF-CRE 和 CRE-CRE 预测精度（相对 6 个基线），并能利用该网络识别谱系特异驱动因子、预测扰动响应、发现疾病相关 CRE 模块。其有效性限于有配对多组学数据且已知先验调控关系的场景。

## 12 作者自认局限
*注：原文未设独立"Limitations"章节，以下从全文提取作者明确提及的限制。*

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 依赖先验调控关系 | TF-TF 和 CRE-TG 边来自先验知识库，可能遗漏未知调控关系 | 未明确提及 | Methods "Dual-task decoder" 节（隐含） |
| 数据质量依赖 | 需要高质量配对 scRNA-seq + scATAC-seq 数据 | 未明确提及 | Methods "Datasets" 节（隐含） |
| 未整合细胞间通讯 | 模型限于细胞内调控网络 | 结论中提及"integration of cell–cell communication models"作为未来方向 | Conclusion 节 |
| 未整合空间信息 | 未利用空间多组学数据 | 结论中提及"incorporation of spatial multi-omics data"作为未来方向 | Conclusion 节 |
| 扰动模拟未湿实验验证 | 模拟结果缺乏实验验证 | 未明确提及 | Results 图 6（隐含） |

## 12.1 作者提及的相关约束（非正式局限）
- 模型在 K562 中 top60-200 区间与 STREAM 相当，提示简单基序方法在特定场景仍有竞争力（Results 图 2B）。
- 表达预测性能随网络边数增加变化不显著（补充图 S5），提示特征选择比网络规模更重要。
- 使用 Deekseek R1 辅助英文润色，可能影响表述一致性（Acknowledgements 节）。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|---------------------|----------|----------|------|
| 半监督伪标签来自表达相关性阈值 | 高相关 ≠ 因果调控，可能引入系统性偏差 | 伪标签质量直接影响网络学习上限 | 对比不同伪标签来源（如 ChIP-seq 直接标注 vs 相关性阈值）对最终预测的影响 | Methods "Loss function" 节 |
| 基线选择偏向深度学习模型 | 未与经典统计方法（如 GENIE3、GRNBoost2）全面对比 | 需确认增益来自模型设计而非基线弱势 | 补充经典 GRN 推断基线 | Results 图 2A |
| 消融实验仅报告层级元路径 vs 同构版本 | 未系统消融各组件（如 GCN vs GAT、BLCE vs BCE、双任务 vs 单任务） | 无法归因性能提升的具体来源 | 设计完整消融矩阵 | 补充图 S3 |
| 扰动模拟缺乏定量评估指标 | 仅展示向量场变化，未与湿实验数据定量对比 | 因果推断 claim 需要更强验证 | 与 CRISPR 扰动实验数据定量对比（如 AUC 或相关性） | Results 图 6 |
| 跨数据集泛化未充分验证 | 主要结果集中在 BM 和 K562，其他数据集仅部分展示 | 模型是否具有普遍适用性存疑 | 在更多独立数据集上系统评估 | Results 各节 |
| 与 CellOracle 等专门扰动模型未对比 | CellOracle 是扰动预测的 SOTA 基线 | 需证明 SMOGT 在扰动预测上的增量价值 | 与 CellOracle 在相同数据集上对比 | Introduction 第 4 段 |
| 计算效率未报告 | 图 Transformer 在大规模单细胞数据上的可扩展性未知 | 实际应用需考虑计算成本 | 报告训练时间、显存占用、扩展性分析 | 未提供 |
| 未报告超参数敏感性 | 阈值（TF-CRE: 0.8, CRE-CRE: 2%）的选取依据不明确 | 结果可能对阈值敏感 | 阈值敏感性分析 | Results 图 3D–E |

## 14 学到什么
**Agent 提炼的知识候选**

1. **层级元路径设计**：将生物学层级因果逻辑（TF-TF → TF-CRE → CRE-CRE → CRE-TG）显式编码为图 Transformer 的元路径，而非让模型自由学习注意力。这一"知识约束 + 数据驱动"的混合策略可迁移到 TF–DNA 结合预测：将"TF 结合基序 → 染色质可及性 → 远程增强子 → 靶基因"的层级关系编码为元路径，可能比扁平图更准确。
2. **半监督学习应对边稀疏**：用高置信互作对作为伪标签，结合网络重建 + 表达预测双任务，缓解全基因组调控边稀疏问题。可迁移到 TF–DNA 结合预测：用 ChIP-seq 验证的高置信结合位点作为伪标签，联合优化结合预测与下游基因表达预测。
3. **多任务联合优化**：网络重建（结构）与表达预测（功能）联合训练，使表示同时编码拓扑与功能信息。对 TF–DNA 结合预测的启示：结合位点预测可与靶基因表达预测联合优化，增强表示的功能相关性。
4. **MRWR 用于因果传播**：多层随机游走从扰动 TF 出发传播信号，识别受影响基因，为 TF 扰动效应预测提供轻量级替代方案（相比 CellOracle 的 ODE 模拟）。可迁移到 TF–DNA 结合机制研究：从候选 TF 出发，在调控网络中传播信号，预测敲除/过表达的下游效应。
5. **Louvain 共调控模块发现**：对 CRE 表示聚类识别协同调控模块，结合疾病位点富集验证。可迁移到 TF–DNA 结合研究：对预测的 TF 结合位点聚类，识别协同调控的增强子模块，关联疾病变异。
6. **评估框架**：用 ChIP-seq/Hi-C 作为真值评估边预测，用 Perturb-seq 评估扰动预测，用 GWAS/eQTL/SE 富集评估疾病相关性。这一"三层验证"框架可迁移到 TF–DNA 结合预测模型的评估设计。
7. **特征编码策略**：TF 用表达特征、CRE 用可及性特征、TG 用表达特征，不同节点类型使用不同模态特征。对 TF–DNA 结合预测的启示：TF 节点可用序列 embedding + 表达，CRE 节点可用可及性 + 序列 motif 打分，TG 节点可用表达 + 保守性。

## 15 与已有知识连接
- **Heterogeneous Graph Transformer (HGT)**：Hu et al., 2020, WWW（本文核心架构基础）。可连接：HGT 在异质图上的注意力机制设计。
- **SCENIC+**：Bravo González-Blas et al., 2023, Nature Methods（基线方法）。可连接：基于回归的 eRegulon 推断。
- **CellOracle**：Kamimoto et al., 2023, Nature（扰动预测基线）。可连接：基于 ODE 的扰动模拟框架。
- **regX**：Wang et al., 2023（基线方法）。可连接：结合 PPI 的调控推断。
- **LINGER**：Li et al., 2023（基线方法）。可连接：跨组学线性化调控建模。
- **eNet 2.0**：Huang et al.（本文引用的共 CRE 识别方法）。可连接：基于表达相似的共调控网络。
- **DeepMAPS**：Chen et al., 2022（HGT 在单细胞多组学的早期应用）。可连接：HGT 在 scMultiome 的图构建方式。
- **scMultiomeGRN**：Zhang et al., 2024（HGT 在双组学的应用）。可连接：HGT 在染色质可及性 + 表达的 GRN 推断。
- **SEAcell / Monocle3 / scVelo**：本文使用的轨迹推断工具。可连接：细胞命运分析的预处理流程。
- **TF–DNA 结合机制方向**：本文未涉及物理模拟（MD/对接）或结构预测（AlphaFold 等），但图学习方法可迁移到结合位点预测。可连接：DeepSEA、Basenji 等序列深度学习方法，以及 TF–DNA 结构预测的 AlphaFold 3 等。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：TF–DNA 结合层级元路径图 Transformer（TF-DNA Hierarchical Meta-path Graph Transformer, TF-HMGT）
   - **来源局限/观察**：SMOGT 的层级元路径设计显著提升调控网络推断，但未利用 TF 的 DNA 结合基序序列信息；现有 TF–DNA 结合预测多为序列模型，未整合细胞类型特异的染色质状态。
   - **核心假设**：将"TF 基序 → 染色质可及性 → 增强子-启动子互作 → 靶基因表达"的层级因果流编码为元路径，可提升 TF–DNA 结合预测的细胞类型特异性。
   - **增量**：在 SMOGT 框架基础上，为 TF 节点加入序列 embedding（如 DNABERT 或残差基序打分），为 CRE 节点加入可及性 + 基序共现特征，并引入 ChIP-seq 作为强监督信号。
   - **初步方法**：构建异质图（TF、CRE、TG 节点），沿 TF-TF → TF-CRE → CRE-CRE → CRE-TG 元路径传播，半监督训练（ChIP-seq 边 + 表达预测双任务）。
   - **验证方式**：在 ENCODE 多细胞系 ChIP-seq 基准上评估 TF–CRE 预测 AUPR；与 DeepSEA、Basenji、SCENIC+ 对比。
   - **创新状态**：unverified（需文献调研确认无同类工作）

2. **候选名称**：物理模拟与图学习联合的 TF–DNA 结合亲和力预测（Physics-informed Graph Network for TF-DNA Binding, PiGN-Bind）
   - **来源局限/观察**：SMOGT 完全数据驱动，未利用 TF–DNA 结合的物理化学原理（氢键、形状互补、静电）；MD/对接方法精度高但计算昂贵，无法扩展到全基因组。
   - **核心假设**：将 MD 模拟或 Rosetta 对接得到的结合自由能作为边权重先验，注入图 Transformer，可提升低数据场景下的结合预测。
   - **增量**：在 SMOGT 的 TF-CRE 边初始化中，用短 MD 模拟或分子对接打分替代纯相关性阈值。
   - **初步方法**：对高置信 TF–DNA 复合物做短 MD 模拟提取结合自由能，作为伪标签/边权重先验；图 Transformer 学习残差修正。
   - **验证方式**：在 ChIP-seq 基准上对比有无物理先验的预测精度；在低数据细胞系上测试泛化。
   - **创新状态**：unverified（需确认无同类物理-图学习混合方法）

3. **候选名称**：基于 SMOGT 的 TF 扰动响应跨细胞类型迁移预测（Cross-celltype TF Perturbation Transfer, CPT-Transfer）
   - **来源局限/观察**：SMOGT 的扰动模拟在单一数据集内验证，未测试跨细胞类型迁移；实际应用中目标细胞类型常缺乏配对多组学数据。
   - **核心假设**：在源细胞类型上训练的 HRNet 可通过元学习或域适应迁移到目标细胞类型，保留层级调控逻辑。
   - **增量**：在 SMOGT 框架中加入域适应模块（如对抗训练或元学习），使 TF-CRE 边预测跨细胞类型泛化。
   - **初步方法**：源域（如 BM）训练 SMOGT，目标域（如 PBMC）仅用少量标注微调；评估扰动预测一致性。
   - **验证方式**：跨 7 个数据集的留一法交叉验证；与不迁移的基线对比。
   - **创新状态**：unverified（需确认无同类跨细胞类型迁移工作）

4. **候选名称**：SMOGT 与 AlphaFold 3 结合的 TF–DNA 复合物结构感知调控网络（Structure-aware Regulatory Network via SMOGT+AF3, StructRegNet）
   - **来源局限/观察**：SMOGT 预测的 TF-CRE 边缺乏结构验证；AlphaFold 3 可预测 TF–DNA 复合物结构，但未与单细胞调控网络整合。
   - **核心假设**：将 AF3 预测的 TF–DNA 结合结构特征（界面残基、结合亲和力）作为边特征注入 SMOGT，可提升调控网络的功能可解释性。
   - **增量**：为 SMOGT 的 TF-CRE 边增加 AF3 结构特征通道。
   - **初步方法**：对高置信 TF-CRE 对运行 AF3 预测，提取结合界面特征；与 SMOGT 的注意力分数融合。
   - **验证方式**：在 ChIP-seq 基准上对比有无结构特征的预测精度；在 AML 数据上验证结构特征是否富集疾病相关突变。
   - **创新状态**：unverified（需确认 AF3 在 TF–DNA 复合物上的预测精度和计算可行性）