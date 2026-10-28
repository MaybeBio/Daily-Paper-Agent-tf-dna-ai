## 01 基本信息

- **标题**：ProSiteHunter: A unified framework for sequence-based prediction of protein-nucleic acid and protein-protein binding sites
- **作者**：Dongliang Hou; Qihang Zhen; Zexin Lv; Xinyue Cui; Suhui Wang; Minghua Hou; Zhan Zhou; Xiaogen Zhou; Guijun Zhang
- **单位**：浙江工业大学信息工程学院（College of Information Engineering, Zhejiang University of Technology）等
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2025
- **论文类型**：方法学（Method）论文，提出新预测框架
- **领域**：蛋白质结合位点预测（蛋白-核酸、蛋白-蛋白、抗体-抗原）
- **关键词**：binding site prediction, protein language model, feature fusion, sequence-based, protein-DNA, protein-RNA, protein-protein, antibody-antigen
- **DOI/arXiv 号**：10.1101/2025.10.22.683834
- **代码**：https://github.com/iobio-zjut/ProSiteHunter/tree/main
- **数据**：BioLiP 数据库（蛋白-核酸）、EnsemPPIS 数据集（蛋白-蛋白）、SEMA1.0 数据集（抗体-抗原）
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 深度学习」方向，聚焦于**基于序列的 TF-DNA 结合位点预测**。与结构方法（如 AlphaFold3）互补，强调从序列直接预测结合位点，并验证了与 AlphaFold3 的协同性。对 TF-DNA 结合机制研究具有直接参考价值，其多源特征融合策略可迁移至 TF 结合位点预测任务。

## 02 一句话总结

ProSiteHunter 通过微调蛋白语言模型（SiteT5）并结合多源特征融合网络（MSFF + MIL），以单条氨基酸序列为输入，统一预测蛋白-DNA、蛋白-RNA、蛋白-蛋白和抗体-抗原四类结合位点，在 PRAUC 上较现有最优方法平均提升 39.1%（蛋白-DNA/RNA/蛋白）和 7.4%（抗体-抗原），并能识别 AlphaFold3 遗漏的柔性结合位点。

## 03 研究问题

- **具体问题**：能否用一个统一的序列-based 框架，同时准确预测多种类型的蛋白结合位点（蛋白-DNA、蛋白-RNA、蛋白-蛋白、抗体-抗原）？
- **为什么重要**：结合位点预测是理解蛋白功能、基因调控机制（如转录调控）、药物设计和抗体开发的关键。现有方法多为特定任务定制，缺乏通用性；结构方法依赖高质量结构，对柔性区域和动态构象无能为力。
- **现有方法不足**：(1) 序列方法多为单任务设计，特征和架构不通用；(2) 结构方法（GNN、几何特征）依赖结构质量，对柔性结合位点预测不准；(3) 现有序列方法对长程依赖和全局上下文建模不足。
- **精确研究问题**：Can a unified sequence-based framework with fine-tuned protein language model and multi-source feature fusion achieve state-of-the-art performance across protein-DNA, protein-RNA, protein-protein, and antibody-antigen binding site prediction tasks?

## 04 背景与发展脉络

*注：此脉络基于本文 Introduction 的叙述框架，未经外部独立核验。*

| 阶段 | 代表性方法 | 优点 | 局限 |
|------|-----------|------|------|
| 实验方法 | 亲和纯化-质谱、免疫沉淀、杂交筛选 | 精确 | 耗时、昂贵、难以大规模 |
| 结构-based GNN | GraphPPIS, GraphBind, EGPDI | 利用空间拓扑 | 依赖高质量结构，对柔性区域失效 |
| 结构-based 几何特征 | PeSTo, epitope3D, SEMA2.0-3D | 表面形状刻画 | 同上，且特征工程复杂 |
| 序列-based 单任务 | DELPHI (PPI), iDRNA-ITF (RNA), CLAPE (核酸), BepiPred-3.0 (表位) | 仅需序列，鲁棒 | 单任务定制，缺乏通用性；长程依赖建模不足 |
| 序列-based 统一框架（本文） | ProSiteHunter | 统一多任务，融合 PLM + 多源特征 | 依赖训练数据质量，对高度柔性区域仍有挑战 |

**本文主张的位置**：在序列-based 方法脉络中，ProSiteHunter 是首个统一覆盖蛋白-DNA/RNA/蛋白/抗体-抗原四类任务的框架，通过微调 PLM（SiteT5）和三层特征融合（MSFF + MIL）解决通用性和长程依赖问题。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|----------|
| 任务专用性 | 现有方法针对单一结合位点类型设计，无法跨任务泛化 | 各任务使用不同特征集和网络架构，缺乏统一设计 | Introduction: "existing sequence-based approaches are often designed for specific binding-site types and therefore lack generality" |
| 结构依赖 | 结构方法在结构预测不准或柔性区域失效 | 静态结构快照无法捕捉动态构象变化 | Introduction: "accurately modeling flexible binding regions remains a major technical hurdle"; "predictions derived from static structural snapshots may fail to capture authentic binding mechanisms" |
| 长程依赖建模不足 | 局部感受野受限，无法捕捉远端功能残基关联 | 单网络架构（如仅 CNN 或仅 BiLSTM）无法同时建模局部和全局 | Introduction: "owing to constraints in local receptive fields and insufficient global context modeling, current methods often fail to capture long-range dependencies" |
| 类别不平衡 | 结合位点远少于非结合位点，影响分类性能 | 正负样本比例严重失衡 | Methods/Training: 使用加权交叉熵损失，class 0 权重 1，class 1 权重 5 |
| 柔性表位预测难 | 抗体-抗原表位高度构象多样，预测准确率低 | 表位区域富含柔性环区，结构不稳定 | Results: "Antibody-antigen binding interfaces are often highly structurally diverse and flexible, making prediction challenging" |

## 06 核心思想

1. **表面方法**：ProSiteHunter 是一个编码器-解码器架构的深度学习框架。输入为单条氨基酸序列，输出为每个残基的结合位点概率分数。框架包含两个核心模块：多源特征融合（MSFF）和多层交互学习（MIL）。特征层面整合了微调蛋白语言模型（SiteT5）、结构语言模型（ProstT5）、BLOSUM62、理化性质、相对溶剂可及性（RSA）、二级结构、氨基酸倾向性和对称归一化位置编码。

2. **核心洞察**：不同特征类型（进化、统计、几何）在结合位点预测中具有互补性，而三种序列建模范式（CNN 的局部模式、BiLSTM 的双向语义、注意力机制的全局依赖）分别对应了结合位点识别的不同层次需求。作者将三者分别映射到注意力机制的 Q、K、V 空间，实现特征层面的动态对齐和融合。此外，通过微调 PLM（SiteT5）而非直接使用通用 PLM，使模型专门学习结合位点的进化保守特征。

3. **可能的普适教训** [Analysis]：本文的核心可迁移思想是「**异构特征通过注意力机制在语义空间对齐**」——不是简单拼接特征，而是将不同特征源映射到 Q/K/V 的不同角色，让模型学习何时以何种权重参考何种特征。这一设计对 TF-DNA 结合位点预测同样适用：TF 结合特异性由序列保守性（进化特征）、结构可及性（几何特征）和理化互补性（统计特征）共同决定，三者通过注意力对齐可能比简单拼接更有效。

## 07 方法总览

- **输入**：单条氨基酸序列，长度 L
- **输出**：每个残基的结合位点概率分数（二分类：结合/非结合）
- **特征来源**：
  - SiteT5（微调自 ProtT5-XL-UniRef50，输入 MSAs，1024 维）
  - ProstT5（结构语言模型，1024 维）
  - BLOSUM62（20 维）
  - 理化性质（5 维：位阻、极化率、疏水性、等电点等）
  - RSA 和二级结构（由 NetSurfP3.0 预测）
  - 氨基酸倾向性（统计特征）
  - 对称归一化位置编码（1 维）
  - 总计：43 维非 PLM 特征（pcf）+ 2×1024 维 PLM 特征
- **网络结构**：
  1. **MSFF 模块**（三轨并行）：
     - 多尺度 CNN（kernel 3, 5, 7）→ 提取局部模式 → 作为 Q
     - BiLSTM（2 层，32 units/层）→ 双向语义 → 作为 K
     - Gated Attention（8-head self-attention + 门控）→ 全局依赖 → 作为 V
     - 三者经 8-head cross-attention 动态融合
  2. **MIL 模块**（3 个相同子块堆叠）：
     - 每个子块 = 8-head self-attention + 门控机制 + 位置前馈网络（PFFN）
  3. **分类头**：MLP（3 层隐藏层）→ softmax → 二分类概率
- **训练**：
  - 优化器：RAdam
  - 损失函数：加权交叉熵（正类权重 5，负类权重 1）
  - 学习率：初始 0.0005，指数衰减
  - Epochs：最多 30
  - 硬件：NVIDIA GeForce RTX 3090，约 1 小时
  - Batch size：1
- **四个独立模型**：分别针对蛋白-DNA、蛋白-RNA、蛋白-蛋白、抗体-抗原训练，共享架构但参数独立
- **流程**：序列 → 特征提取（PLM + 传统特征）→ MSFF 三轨融合 → MIL 多层交互 → MLP 分类 → 残基级概率分数

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| SiteT5（微调 PLM） | 捕捉进化保守特征 | 结合位点在进化上保守，通用 PLM 未针对结合位点优化 | 输入：MSA 序列；输出：1024 维残基嵌入 | Results 图 4c 消融实验：移除 SiteT5 后 MCC/F1 下降 >11% | **实测消融效应**：MCC 和 F1 下降超 11%，PRAUC 和 ROCAUC 分别下降 6.3% 和 2.2% |
| ProstT5 | 提供结构先验（从序列预测结构） | 结合位点与结构可及性相关，ProstT5 提供无结构输入的几何线索 | 输入：序列；输出：1024 维残基嵌入 | Results 图 4c 消融实验 | **实测消融效应**：贡献低于 SiteT5，但仍是有效特征源 |
| 多尺度 CNN（Q） | 提取局部序列模式 | 结合位点常由短基序（motif）决定 | 输入：融合特征；输出：64 维局部特征 | Results 图 4f 架构消融 | **预期效应** [Analysis]：移除后局部基序识别能力下降，可能影响 DNA 结合位点预测（DNA 结合常依赖保守基序） |
| BiLSTM（K） | 双向语义建模 | 结合位点受上下游序列上下文影响 | 输入：融合特征；输出：64 维双向特征 | Results 图 4f 架构消融 | **预期效应** [Analysis]：移除后对方向性序列依赖的建模减弱 |
| Gated Attention（V） | 全局依赖 + 自适应加权 | 远端残基可共同形成结合界面 | 输入：融合特征；输出：64 维全局特征 | Results 图 4f 架构消融 | **预期效应** [Analysis]：移除后长程相互作用捕获能力下降 |
| Cross-attention 融合 | 动态对齐三轨特征 | 不同特征源重要性因残基位置而异 | 输入：Q/K/V 三轨特征；输出：融合表示 | Results 图 4f：三轨融合优于单轨 | **实测消融效应**：三轨融合较单轨平均提升 2.4%（PRAUC/F1/MCC） |
| MIL（3 子块堆叠） | 迭代精化特征表示 | 单次特征融合不足以捕捉高阶残基交互 | 输入：MSFF 输出；输出：精化表示 | Results 图 4f 架构消融 | **预期效应** [Analysis]：减少子块数量可能降低高阶交互建模能力 |
| 加权交叉熵损失 | 处理类别不平衡 | 结合位点远少于非结合位点 | 输入：预测概率与标签；输出：损失值 | Methods/Training 节 | **预期效应** [Analysis]：移除后模型可能偏向预测多数类（非结合位点），召回率下降 |

## 09 关键公式符号

**1. 加权交叉熵损失**（Methods/Training 节）：

$$Loss = -\frac{1}{N}\sum_{i=1}^{N} [w_1 \cdot y_i \cdot \log(p_{i,1}) + w_0 \cdot (1-y_i) \cdot \log(p_{i,0})]$$

- $N$：残基总数
- $y_i \in \{0, 1\}$：残基 $i$ 的真实标签（1 = 结合位点）
- $p_{i,1}$：残基 $i$ 属于结合位点的预测概率
- $p_{i,0}$：残基 $i$ 属于非结合位点的预测概率
- $w_1 = 5$：正类（结合位点）权重
- $w_0 = 1$：负类（非结合位点）权重

**2. Softmax 归一化**（Methods/Training 节）：

$$p_{i,k} = \frac{e^{z_{i,k}}}{\sum_{j=0}^{1} e^{z_{i,j}}}, \quad k \in \{0, 1\}$$

- $z_{i,k}$：模型输出的 logit 分数

**3. 结合残基定义**（Methods/Data set 节，来自 BioLiP）：

$$\text{结合残基} \iff d_{min}(\text{残基原子}, \text{核酸原子}) < 0.5\,Å + r_{vdW}(\text{残基原子}) + r_{vdW}(\text{核酸原子})$$

- $d_{min}$：残基与核酸分子间最小原子距离
- $r_{vdW}$：范德华半径

**4. 对称归一化位置编码**（Methods/Sequence features 节）：

$$PE(i) = \frac{i}{L} \in [0, 1]$$

- $i$：残基索引
- $L$：序列总长度

## 10 实验设计与证据链

**数据集与评测协议**：

| 任务 | 训练集 | 测试集 | 数据来源 | 划分方式 |
|------|--------|--------|----------|----------|
| 蛋白-DNA | 573 条链（预处理后） | 129 条链 | BioLiP（2018-12-05 发布） | 时间划分（2016-01-06 前/后） |
| 蛋白-RNA | 495 条链（预处理后） | 117 条链 | BioLiP（2018-12-05 发布） | 时间划分（2016-01-06 前/后） |
| 蛋白-蛋白 | 351 条（训练）+ 50 条（验证） | 70 条 | EnseemPPIS 数据集（Dset_186 + Dset_72 + PDBset_164） | 序列同一性 < 25% |
| 抗体-抗原 | 713 条（训练）+ 70 条（验证） | 101 条 | SEMA1.0 | 时间划分（2020-01-01 后） |

**指标**：ROCAUC、PRAUC、F1-score、MCC、Recall、Precision

**关键实验表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| 蛋白-DNA 结合位点预测 | ProSiteHunter 优于现有方法 | 对比 DRNApred, iDRNA-ITF, CLAPE-DB | ROCAUC=0.911，较 CLAPE-DB 提升 5.3% | 统一框架在 DNA 结合位点预测上达到 SOTA | 未提供显著性检验 | Results 图 2a |
| 蛋白-RNA 结合位点预测 | ProSiteHunter 优于现有方法 | 对比 DRNApred, iDRNA-ITF, CLAPE-RB | ROCAUC=0.852，较 CLAPE-RB 提升 8.4% | 统一框架在 RNA 结合位点预测上达到 SOTA | 未提供显著性检验 | Results 图 2a |
| 蛋白-蛋白结合位点预测 | ProSiteHunter 优于现有方法 | 对比 EnsemPPIS, DELPHI, DeepPPISP | 较 EnsemPPIS 提升：ROCAUC +9.3%，PRAUC +24.7%，F1 +16.1%，MCC +34.3% | 统一框架在 PPI 位点预测上显著优于基线 | 未提供显著性检验 | Results 图 3a, 3b；Supplementary Table 6 |
| 抗体-抗原表位预测 | ProSiteHunter 优于现有方法 | 对比 CALIBER | 较 CALIBER 提升：ROCAUC +2.1%，PRAUC +7.4%，F1 +8.3%，MCC +10.0% | 统一框架在表位预测上优于基线 | 提升幅度较小，可能受任务难度限制 | Results 图 3a, 3b；Supplementary Table 7 |
| 特征消融 | SiteT5 是关键特征 | 移除 SiteT5 vs 完整模型 | MCC/F1 下降 >11%，PRAUC 下降 6.3%，ROCAUC 下降 2.2% | SiteT5 提供关键的进化保守信息 | 未报告各特征独立贡献的完整矩阵 | Results 图 4c |
| 架构消融 | 三轨融合优于单轨 | 单轨 vs 三轨 | 三轨融合在 PRAUC/F1/MCC 上平均提升 2.4% | 多源特征互补有效 | 未报告每种组合的详细结果 | Results 图 4f |
| AlphaFold3 互补性 | ProSiteHunter 可补充结构方法 | 案例：RSV G 蛋白-抗体复合物（T1225, CASP16） | ProSiteHunter F1=0.630, MCC=0.608；AlphaFold3 F1=0.424, MCC=0.389 | 序列方法在结构预测不准时更可靠 | 仅单案例，非系统性评估 | Results 图 3e |
| 构象变化案例 | 可识别柔性位点 | 溶菌酶两种构象（4GN4 vs 1J1X） | AUC：4GN4=0.910, 1J1X=0.962 | 能捕捉构象变化导致的结合位点差异 | 仅两个构象，未覆盖更多动态场景 | Results 图 5e |
| 氨基酸倾向性分析 | 不同结合位点类型有共享模式 | 蛋白-DNA vs 蛋白-RNA 位点 | Pearson=0.976, Spearman=0.905 | DNA/RNA 结合位点氨基酸组成高度相似 | 未分析 TF 特异性模式 | Supplementary Fig. 1a |
| 二级结构分析 | 环区主导结合位点 | 四类结合位点 | 环区占 45%-57%；RNA 结合位点和表位环区比例最高（54.3%, 57.2%） | 环区柔性是预测难点 | 未与 TF 结合位点直接对比 | Supplementary Fig. 1c |

## 11 结论正确解读

- **任务范围**：本文解决的是**残基级结合位点二分类预测**（每个残基是否参与结合），而非结合亲和力预测、结合构象预测或复合物结构预测。输出是概率分数，不是结合界面坐标。
- **输入限制**：仅使用序列信息，不依赖实验结构或预测结构。但 SiteT5 的微调使用了 MSAs（多序列比对），因此**隐含依赖同源序列信息**。
- **四任务独立**：虽然称为"统一框架"，但四个任务（DNA/RNA/蛋白/抗体-抗原）各自训练独立模型，共享的是架构而非参数。跨任务迁移能力未被直接验证。
- **性能边界**：PRAUC 提升 39.1% 是四任务平均值，各任务提升幅度不同。抗体-抗原任务提升最小（7.4%），说明该任务难度最高。
- **与 AlphaFold3 的关系**：本文**不是替代** AlphaFold3，而是互补。在结构预测准确时，结构方法可能更优；在结构预测失败或柔性区域，序列方法更可靠。案例仅证明互补性，不证明全面优越性。
- **因果性限制**：相关性分析（氨基酸倾向性、二级结构组成）是描述性的，不建立因果机制。模型学到的模式不一定对应已知的生化机制。
- **可复现性**：代码已开源，但预训练模型权重、MSA 生成细节、超参数搜索范围等未在摘要中完整披露。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 抗体-抗原表位预测难度高 | 提升幅度（7.4% PRAUC）低于其他任务 | 探索混合策略，结合结构建模 | Results: "the particularly challenging antibody-antigen task" |
| 结构方法互补而非替代 | AlphaFold3 在部分案例中预测错误区域 | 将序列预测与结构预测结合 | Discussion: "highly complementary to structure-based methods" |
| 柔性区域预测仍有挑战 | 构象变化导致结合位点区域改变 | 纳入构象系综信息 | Results 图 5e 讨论 |
| 数据依赖 | 依赖 BioLiP、SOTA 数据集的质量和覆盖度 | 随训练数据增长进一步提升泛化能力 | Discussion: "As training data continues to grow and diversify, ProSiteHunter's generalization capabilities are expected to further enhance" |
| 扩展性待验证 | 尚未覆盖蛋白-小分子、蛋白-离子结合位点 | 扩展至更多结合位点类型 | Discussion: "extend to protein-small molecule ligand and protein-ion binding sites" |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 四任务独立训练，共享架构而非参数 | "统一框架"的表述可能过度承诺；实际是四个独立模型 | 跨任务泛化能力未被验证，TF-DNA 特定任务可能需要专门调优 | 测试一个模型在多个任务上的零样本/少样本性能 | Results: "Four specialized models are independently trained on type-specific datasets" |
| PRAUC 提升 39.1% 为平均值 | 各任务提升幅度差异大，可能掩盖某些任务提升有限 | 对 TF-DNA 任务的实际增益需单独评估 | 查看各任务单独结果（Supplementary Tables 4, 5） | Abstract: "39.1% average improvement" |
| 与 AlphaFold3 比较仅限单案例 | 案例选择可能有偏，非系统性基准 | 互补性结论的普适性存疑 | 在多样本上系统比较序列方法与结构方法 | Results 图 3e：仅 RSV G 一个案例 |
| SiteT5 微调使用 MSAs | 输入"仅序列"的表述不完全准确；MSA 生成依赖同源序列数据库 | 对孤儿蛋白（无同源序列）性能可能大幅下降 | 在无 MSA 条件下测试性能 | Methods: "we used UniRef30 for multiple sequence alignment (MSA) generation" |
| 加权交叉熵权重（1:5）固定 | 不同任务最优权重可能不同 | 权重选择可能影响跨任务公平性 | 对每个任务搜索最优权重 | Methods/Training: "class 0 has a weight of 1 and class 1 has a weight of 5" |
| 未报告不确定性估计 | 预测分数无置信区间 | 实际应用中无法判断预测可靠性 | 添加 MC-Dropout 或 ensemble 不确定性 | 全文未提及 |
| 与 TF 结合机制的直接关联未展开 | 论文聚焦预测性能，未深入分析 TF 结合 motif 的生物学机制 | 对机制研究读者的直接价值有限 | 分析模型注意力权重与已知 TF motif 的对应关系 | 全文未提及 TF 特异性分析 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **多源特征通过 Q/K/V 语义角色分配实现融合**：本文最核心的可迁移设计。将 CNN（局部）、BiLSTM（双向语义）、Gated Attention（全局）分别映射到注意力机制的 Q、K、V，让模型学习动态对齐异构特征。迁移到 TF-DNA 结合位点预测时，可考虑：CNN 捕捉 DNA 结合 motif 的局部模式（Q），BiLSTM 建模 TF 结合位点上下游的上下文依赖（K），Gated Attention 捕捉远端协同结合的残基对（V）。

2. **微调 PLM 而非直接使用通用 PLM**：SiteT5 在 ProtT5 基础上用 MSAs 微调，比直接使用通用嵌入效果显著更好（MCC/F1 提升 >11%）。对 TF-DNA 任务，可用已知 TF 结合实验数据（如 ChIP-seq、SELEX）微调 PLM，使模型专门学习 TF 结合位点的进化保守特征。

3. **序列方法可作为结构方法的互补**：在 AlphaFold3 预测失败或柔性区域，序列方法更可靠。对 TF-DNA 研究，可构建「序列预测 + 结构验证」的级联策略：先用序列方法筛选候选 TF 结合位点，再用结构方法（对接/MD）验证。

4. **氨基酸倾向性分析揭示结合位点组成规律**：DNA/RNA 结合位点氨基酸组成高度相似（Pearson=0.976），而蛋白-蛋白与抗体-抗原也相似。这提示 TF-DNA 结合位点可能共享某些通用氨基酸偏好（如正电荷残基 K/R 富集），可用于特征工程。

5. **环区比例与预测难度正相关**：RNA 结合位点和表位环区比例最高（54.3%, 57.2%），预测难度也最高。对 TF-DNA 结合位点，若结合区域富含环区（柔性），需注意序列方法的性能边界。

6. **加权交叉熵处理类别不平衡**：结合位点/非结合位点比例约 1:10 时，正类权重设为 5 是合理起点。TF-DNA 结合位点同样面临严重类别不平衡，可参考此设置。

7. **时间划分避免数据泄漏**：按结构发布日期划分训练/测试集，比随机划分更贴近实际应用场景。TF-DNA 数据集构建时应采用类似策略。

## 15 与已有知识连接

- **GraphBind (Zhang et al., 2020)**：本文直接使用 GraphBind 的蛋白-DNA/RNA 数据集和预处理流程，是方法对比的基准之一。GraphBind 是结构-based 方法，ProSiteHunter 是序列-based，两者对比体现了结构 vs 序列范式的互补性。
- **ProtT5-XL-UniRef50 (Elnaggar et al., 2022)**：SiteT5 的基座模型，ProtT5 是蛋白语言模型的代表性工作。本文展示了如何针对特定任务微调通用 PLM。
- **ProstT5 (Heinzinger et al., 2024)**：结构-序列双向转换模型，本文将其作为结构先验特征源，体现了「序列 → 结构 → 序列」的闭环思路。
- **ESM-2 (Lin et al., 2023)**：BepiPred-3.0 等表位预测方法使用 ESM-2，本文使用 ProtT5 系列，两者对比可评估不同 PLM 对结合位点预测的影响。
- **AlphaFold3 (Abramson et al., 2024)**：本文明确将 ProSiteHunter 定位为 AlphaFold3 的补充工具，在结构预测失败时提供替代方案。对 TF-DNA 研究，AlphaFold3 对 TF-DNA 复合物预测精度有限，序列方法可作为补充。
- **TF-DNA 结合机制相关**：本文未直接研究 TF 结合机制，但其氨基酸倾向性分析（K/R 富集）与已知 TF-DNA 结合域（如锌指、螺旋-转角-螺旋）的正电荷残基偏好一致，可作为机制研究的计算线索。
- **DeepPPISP (Zeng et al., 2020)**：蛋白-蛋白结合位点预测的经典方法，本文作为基线对比，体现了新方法对旧方法的改进幅度。

## 15 与已有知识连接

- **GraphBind (Zhang et al., 2020)**：本文直接使用 GraphBind 的蛋白-DNA/RNA 数据集和预处理流程，是方法对比的基准之一。GraphBind 是结构-based 方法，ProSiteHunter 是序列-based，两者对比体现了结构 vs 序列范式的互补性。
- **ProtT5-XL-UniRef50 (Elnaggar et al., 2022)**：SiteT5 的基座模型，ProtT5 是蛋白语言模型的代表性工作。本文展示了如何针对特定任务微调通用 PLM。
- **ProstT5 (Heinzinger et al., 2024)**：结构-序列双向转换模型，本文将其作为结构先验特征源，体现了「序列 → 结构 → 序列」的闭环思路。
- **ESM-2 (Lin et al., 2023)**：BepiPred-3.0 等表位预测方法使用 ESM-2，本文使用 ProtT5 系列，两者对比可评估不同 PLM 对结合位点预测的影响。
- **AlphaFold3 (Abramson et al., 2024)**：本文明确将 ProSiteHunter 定位为 AlphaFold3 的补充工具，在结构预测失败时提供替代方案。对 TF-DNA 研究，AlphaFold3 对 TF-DNA 复合物预测精度有限，序列方法可作为补充。
- **TF-DNA 结合机制相关**：本文未直接研究 TF 结合机制，但其氨基酸倾向性分析（K/R 富集）与已知 TF-DNA 结合域（如锌指、螺旋-转角-螺旋）的正电荷残基偏好一致，可作为机制研究的计算线索。
- **DeepPPISP (Zeng et al., 2020)**：蛋白-蛋白结合位点预测的经典方法，本文作为基线对比，体现了新方法对旧方法的改进幅度。

## 16 研究想法

**Agent 生成的研究候选**：

1. **TF 特异性微调的多任务结合位点预测框架**
   - **来源局限/观察**：ProSiteHunter 四任务独立训练，未利用 TF 家族间的共享结合模式；且未针对 TF-DNA 特异性优化。
   - **核心假设**：TF 家族内部共享结合机制（如同一 DNA 结合域家族的残基偏好），多任务学习可提升低资源 TF 家族的预测性能。
   - **初步方法**：在 ProSiteHunter 架构基础上，引入 TF 家族层次的多任务学习（family-aware multi-task learning），共享低层特征提取器，为每个 TF 家族设置适配层。
   - **验证方式**：在 CIS-BP 或 JASPAR 数据库上按 TF 家族划分训练/测试，对比单任务 vs 多任务 PRAUC。
   - **创新状态**：unverified

2. **结合位点预测与 AlphaFold3 的主动学习协同框架**
   - **来源局限/观察**：ProSiteHunter 与 AlphaFold3 互补但未系统整合；AlphaFold3 计算成本高，不适合大规模筛选。
   - **核心假设**：序列-based 预测的不确定性可指导 AlphaFold3 的定向结构验证，形成高效筛选管线。
   - **初步方法**：为 ProSiteHunter 添加不确定性估计（如 MC-Dropout），对高不确定性残基区域优先调用 AlphaFold3 验证，迭代优化预测。
   - **验证方式**：在 TF-DNA 复合物数据集上，对比「全量 AlphaFold3」vs「ProSiteHunter 引导的 AlphaFold3」的精度-成本曲线。
   - **创新状态**：unverified

3. **TF-DNA 结合位点的构象系综感知预测**
   - **来源局限/观察**：ProSiteHunter 在构象变化案例（4GN4 vs 1J1X）中表现良好但未显式建模构象多样性；TF-DNA 结合常伴随诱导拟合。
   - **核心假设**：将构象系综信息（如 MD 模拟或 AlphaFold 多构象输出）编码为特征，可提升柔性 TF 结合位点预测。
   - **初步方法**：对每个 TF 生成多构象（MD 或 AF3 采样），提取构象系综的结构特征（如残基柔性、可及性波动），与序列特征融合。
   - **验证方式**：在已知构象变化的 TF-DNA 复合物上测试，对比单构象 vs 系综特征的预测精度。
   - **创新状态**：unverified

4. **TF-DNA 结合 motif 的可解释性分析**
   - **来源局限/观察**：ProSiteHunter 的注意力权重可能编码了 TF 结合 motif 信息，但未系统分析。
   - **核心假设**：模型注意力权重与已知 TF 结合 motif（如 JASPAR 矩阵）存在可对齐的模式，可提取新的 motif 候选。
   - **初步方法**：对 ProSiteHunter 的 cross-attention 权重进行 motif 发现分析（如 TF-MoDISco 风格），与 JASPAR 已知 motif 比对。
   - **验证方式**：在 ChIP-seq 数据上验证新发现 motif 的富集显著性。
   - **创新状态**：unverified

5. **跨物种 TF-DNA 结合位点迁移学习**
   - **来源局限/观察**：ProSiteHunter 训练数据以人类/模式生物为主，未验证跨物种泛化。
   - **核心假设**：TF 结合机制在进化上保守，预训练模型可迁移至非模式生物。
   - **初步方法**：在人类 TF-DNA 数据上训练，在果蝇、酵母等物种上零样本测试，评估迁移性能。
   - **验证方式**：跨物种测试集上的 PRAUC 对比，分析性能下降与进化距离的关系。
   - **创新状态**：unverified