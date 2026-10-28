## 01 基本信息
- **标题**：RNA sequence design and protein-DNA specificity prediction with NA-MPNN
- **作者**：Kubaney, Andrew; Favor, Andrew; McHugh, Lilian; Mitra, Raktim; Pecoraro, Robert; Dauparas, Justas; Glasscock, Cameron; Baker, David
- **单位**：未提供（通讯作者 Baker, David 所属 Institute for Protein Design, University of Washington，但原文未明确列出）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2025（预印本日期 2025-11-19）
- **论文类型**：预印本（方法学/工具类）
- **领域**：计算生物学；RNA 序列设计；蛋白质-DNA 结合特异性预测；深度学习
- **关键词**：NA-MPNN, message-passing neural network, inverse folding, RNA design, protein-DNA specificity, fixed-dock
- **DOI/arXiv 号**：10.1101/2025.10.03.679414
- **代码**：https://github.com/baker-laboratory/NA-MPNN
- **数据**：https://github.com/baker-laboratory/NA-MPNN（PDB ID 列表、非 TRANSFAC PPM 来源）
- **阅读日期**：2026-05-13（按当前日期）
- **在该课题方向中的位置**：本文提出统一核酸逆折叠模型 NA-MPNN，将 RNA 序列设计与固定对接（fixed-dock）蛋白质-DNA 结合特异性预测统一为同一图神经网络框架。对于 TF-DNA 结合机制研究，本文提供了基于结构的特异性预测新方法，可直接用于转录因子-DNA 互作的特异性建模，且其"侧链不可知"（side-chain-agnostic）设计可作为早期筛选工具。

## 02 一句话总结
本文提出 NA-MPNN，一种将蛋白质、DNA、RNA 统一为图表示的消息传递神经网络，通过扩展 ProteinMPNN 架构，在 RNA 序列设计（中位恢复率 60.5%）和固定对接蛋白质-DNA 结合特异性预测（中位 MAE 0.53）两个任务上均达到或超过现有方法，并在 OpenKnot 挑战中验证了实验可行性。

## 03 研究问题
- **具体问题**：能否用单一深度学习架构同时解决核酸逆折叠的两个互补问题——(1) 给定 RNA 骨架结构设计序列；(2) 给定蛋白质-DNA 复合物结构预测 DNA 结合特异性？
- **为什么重要**：RNA 序列设计对适配体、核酶、CRISPR 支架等设计至关重要；蛋白质-DNA 特异性预测对理解转录调控、设计转录因子和基因组编辑工具有直接意义。两者本质都是"给定结构找序列"的逆折叠问题，但此前无统一模型。
- **现有方法不足**：RNA 设计方法（gRNAde、RhoDesign）与蛋白质-DNA 特异性方法（DeepPBS）各自独立，无法共享数据与表征；且 RNA 结构数据稀缺（PDB 中 RNA 条目仅 8,961 vs 蛋白质 235,538），限制了模型训练。
- **精确研究问题**："Can a single message-passing neural network, trained on unified biopolymer graph representations, simultaneously achieve state-of-the-art performance on both RNA sequence design and fixed-dock protein-DNA specificity prediction?"

## 04 背景与发展脉络
*注：以下脉络基于本文框架，未经外部系统核验，标注为「仅本文框架」。*

1. **蛋白质逆折叠（ProteinMPNN, 2022）**：消息传递图神经网络，以 Cα 为节点、距离为边特征，实现蛋白质序列设计。本文的直接前身。
2. **配体感知扩展（LigandMPNN, 2023）**：将小分子配体纳入图表示，证明图神经网络可扩展至非蛋白质节点。
3. **RNA 逆折叠（gRNAde, 2023；RhoDesign, 2024）**：gRNAde 用几何深度学习处理 RNA 骨架；RhoDesign 引入扩散模型。两者均仅针对 RNA，未统一核酸-蛋白质复合物。
4. **蛋白质-DNA 特异性预测（DeepPBS, 2024）**：直接从结构预测 DNA 结合偏好，但仅处理蛋白质-DNA 界面，不涉及 RNA 设计。
5. **结构预测蒸馏（RFNA/RFNAll, RoseTTAFold 系列）**：提供大规模蛋白质-DNA 复合物预测结构，弥补共晶结构不足。
6. **本文位置**：首次将蛋白质、DNA、RNA 统一为单一图表示，用同一架构（不同训练目标）同时解决 RNA 设计与蛋白质-DNA 特异性预测，并利用 RFNA/RFAA 蒸馏数据扩充训练集。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| RNA 结构数据稀缺 | PDB 中 RNA 条目仅 8,961，远少于蛋白质 235,538 | RNA 结构解析难度大，天然数据不平衡 | Introduction 节 |
| 任务割裂 | RNA 设计与蛋白质-DNA 特异性预测各自独立建模，无法共享数据 | 缺乏统一表征框架 | Introduction 节 |
| 特异性预测依赖侧链信息 | DeepPBS 等需完整原子坐标，计算开销大 | 未利用骨架级抽象 | Discussion 节（作者主张） |
| 训练数据标签不一致 | 设计任务用单序列标签，特异性任务用分布标签（PPM） | 两种任务目标本质不同 | Results: NA-MPNN Architecture 节 |
| 非界面位置信息干扰 | 远离蛋白质的 DNA 位置无特异性信号 | 模型可能过度拟合核酸骨架几何 | Data Augmentation 节 |

## 06 核心思想
1. **表面方法**：扩展 ProteinMPNN 图神经网络，将节点类型从蛋白质残基扩展至 DNA/RNA 碱基，边特征基于 Cα（蛋白质）和 C1′（核酸）原子距离，训练两个任务特定模型（设计模型与特异性模型）。
2. **核心洞察**：蛋白质-DNA/RNA 复合物与纯核酸结构可统一为同一图表示——所有残基/碱基共享相同的消息传递框架，仅需区分节点类型（蛋白质/DNA/RNA）和原子集。这使得 RNA 设计可利用蛋白质-DNA 复合物数据，特异性预测也可从 RNA 相关结构中获益。
3. **可能的普适教训 [Analysis]**：逆折叠问题的本质是"结构→序列"的映射，而结构可由骨架原子（Cα/C1′）近似表征。侧链不可知（side-chain-agnostic）的图表示不仅简化计算，还天然避免目标序列信息泄漏——这对 TF-DNA 特异性预测尤为重要，因为 DNA 序列本身是预测目标，不能作为输入特征。

## 07 方法总览
- **输入**：蛋白质-DNA/RNA 复合物或纯核酸的三维结构（PDB 格式），包含骨架原子坐标（蛋白质 N/Cα/C/O/虚拟 Cβ；核酸 P/OP1/OP2/C1′-C5′/O3′-O5′/O2′）
- **输出**：
  - 设计模型：每个核酸位置的概率分布（4 种碱基）
  - 特异性模型：每个 DNA 位置的概率分布（4 种碱基）
- **图构建**：节点 = 残基/碱基；边 = 32 最近邻（基于 Cα/C1′ 距离）；边特征 = 所有骨架原子对距离的 RBF 嵌入
- **节点特征**：聚合物类型 one-hot（蛋白质/DNA/RNA/未知）→ 线性层 → LayerNorm → 线性层
- **编码器-解码器**：与 ProteinMPNN 相同的消息传递编码器 + 随机顺序自回归解码器
- **训练**：
  - 设计模型：交叉熵损失，目标为晶体结构序列（label smoothing ε=0.1，仅核酸类内）
  - 特异性模型：交叉熵损失，目标为实验 PPM（可用时）或 label-smoothing one-hot
- **数据增强（仅特异性模型）**：
  - 核酸-only 复合物：所有位置赋 uniform PPM
  - 蛋白质-核酸复合物：50% 概率丢弃蛋白质链，所有位置赋 uniform PPM
  - 非界面位置（>5Å 无蛋白质侧链接触）且无实验 PPM：赋 uniform PPM
- **训练数据**：PDB（≤3.5Å，总长度 ≤6,000 残基）+ RFNA/RFAA 蒸馏结构（CIS-BP、TRANSFAC）
- **推理**：特异性预测时，30 次随机自回归采样，温度 0.6，平均得到 PPM

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 统一图表示 | 将蛋白质/DNA/RNA 节点统一为同一图 | 实现跨聚合物类型的信息传递 | 输入：骨架坐标；输出：图结构 | Results 图 1a-b | 预期影响：无法处理混合复合物 [Analysis] |
| 聚合物类型嵌入 | 显式编码节点类型（蛋白质/DNA/RNA） | 模型需区分不同聚合物 | 输入：one-hot；输出：嵌入向量 | Results 图 1b | 预期影响：模型无法区分 DNA/RNA，导致碱基预测混淆 [Analysis] |
| 32 最近邻边构建 | 定义消息传递范围 | 控制计算复杂度同时保留局部结构 | 输入：Cα/C1′ 坐标；输出：边列表 | Methods: Additional Featurization | 预期影响：增大邻域可捕获长程互作但增加计算量 [Analysis] |
| 随机顺序自回归解码器 | 逐步生成序列 | 捕捉序列内相关性 | 输入：编码器隐状态；输出：逐位置概率 | Results 图 2a | 实测影响：未报告消融；预期影响：固定顺序可能降低多样性 [Analysis] |
| PPM 目标替换 | 用实验 PPM 替代 one-hot 作为训练目标 | 学习分布而非单序列 | 输入：PPM 列；输出：交叉熵损失 | Methods: Loss | 实测影响：特异性任务 MAE 显著优于 DeepPBS（0.53 vs 0.86） |
| 数据增强（蛋白质丢弃、uniform PPM） | 强制模型关注蛋白质诱导的特异性 | 避免仅依赖核酸骨架几何 | 输入：结构+标签；输出：增强后样本 | Data Augmentation 节 | 预期影响：移除后模型可能过度拟合核酸几何 [Analysis] |
| 侧链不可知表征 | 仅用骨架原子，不含侧链坐标 | 避免目标序列泄漏，加速计算 | 输入：骨架原子；输出：图特征 | Discussion 节 | 预期影响：无法捕捉侧链级互作细节 [Analysis] |

## 09 关键公式符号
**1. 信息瓶颈（ICPPM）**：
$$ICPPM_{true,i} = \sum_{c \in \{A,C,G,T\}} \frac{\ln PPM_{true,i,c}}{\ln(0.25)}$$

- $PPM_{true,i,c}$：实验 PPM 中第 i 位、碱基 c 的概率
- 用途：计算每个位置的信息含量，用于 PPM 对齐时的加权
- 直觉：信息含量越高，该位置特异性越强，对齐时权重越大

**2. IC 加权 Pearson 相关系数**：
$$IC\text{-}weighted PCC(PPM_{true,i}, S_{true,j}) = \frac{1}{2} ICPPM_{true,i} \times \frac{\sum_{c}(PPM_{true,i,c} - \overline{PPM_{true,i}})(S_{true,j,c} - \overline{S_{true,j}})}{\sqrt{\sum_{c}(PPM_{true,i,c} - \overline{PPM_{true,i}})^2} \times \sqrt{\sum_{c}(S_{true,j,c} - \overline{S_{true,j}})^2}}$$

- $S_{true,j}$：结构位置 j 的 one-hot 序列
- 用途：PPM 与结构序列的对齐评分
- 直觉：同时考虑分布相似性和位置信息含量

**3. 损失函数**：
$$Loss = \frac{1}{6000} \sum_{b=1}^{N_{batch}} \sum_{i=1}^{N_{res,max}} mask_{b,i} \times \sum_{c \in \{A,C,G,T\}} -y_{b,i,c} \ln p_{b,i,c}$$

- $mask_{b,i}$：位置是否存在且被设计
- $y_{b,i,c}$：label-smoothed 目标（one-hot 或 PPM）
- $p_{b,i,c}$：模型预测概率
- 用途：设计任务与特异性任务共用，仅目标不同

**4. 序列恢复率**：
$$Sequence Recovery(S_{true}, S_{design}) = \frac{1}{N_{res}} \sum_{i=1}^{N_{res}} \mathbb{I}[S_{true,i} = S_{design,i}]$$

- 用途：设计任务主要评估指标

**5. 采样权重**：
$$Sampling Weight = \frac{1}{N_{chains}} \sum_{i=1}^{N_{chains}} \frac{1}{1 + d_i}$$

- $d_i$：序列聚类中链 i 的度
- 用途：稀有序列簇的样本获得更高权重

## 10 实验设计与证据链
**数据集与设置**：
- **设计任务训练**：PDB 中 15,657 个核酸结构（≤3.5Å，总长度 ≤6,000）
- **设计任务测试**：4,864 训练簇 / 609 验证簇 / 619 测试簇（按核酸序列 80% 聚类）
- **特异性任务训练**：PDB 结构 + RFNA/RFNAll 蒸馏结构（CIS-BP、TRANSFAC），共 45,093 条目
- **特异性任务测试**：228 个 RFNA/RFAA 蒸馏复合物，均有实验 PPM
- **基线**：gRNAde、RhoDesign（设计）；DeepPBS（特异性）
- **评估协议**：设计任务 10 次采样温度 0.1；特异性任务 30 次采样温度 0.6

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| RNA 序列设计（RNA-only） | NA-MPNN 优于现有 RNA 设计方法 | vs gRNAde, RhoDesign | 中位恢复率 60.5% vs 51.7% / 66.7% | NA-MPNN 优于 gRNAde，但低于 RhoDesign | 不能声称 NA-MPNN 是 RNA 设计最优方法 | Results 图 2c |
| RNA 序列设计（RNA 蛋白复合物） | NA-MPNN 在蛋白-RNA 复合物中有效 | vs gRNAde, RhoDesign | 中位恢复率 55.4% | NA-MPNN 在复合物场景中表现稳健 | 未与更多基线对比 | Results 图 2b |
| DNA 序列设计（DNA-only） | NA-MPNN 可设计 DNA 序列 | 无直接基线 | 中位恢复率 57.4% | NA-MPNN 适用于 DNA 设计 | 无对比方法 | Results 图 2b |
| 伪结 RNA 设计 | NA-MPNN 处理复杂拓扑 | vs gRNAde, RhoDesign | 中位恢复率 58.9% vs 47.2% / 67.7% | 优于 gRNAde，低于 RhoDesign | 伪结场景非最优 | Results 图 2d |
| 结构保真度（伪结） | NA-MPNN 设计序列折叠正确 | 预测结构 vs 天然结构 | 中位 C1′-RMSD 9.0Å vs gRNAde 11.6Å / RhoDesign 22.6Å | NA-MPNN 结构保真度最高 | 样本量小（10 个伪结） | Results 图 2f |
| 结构置信度（伪结） | NA-MPNN 设计折叠更可靠 | AlphaFold 3 pLDDT | 中位 56.2 vs 51.6 / 44.2 | NA-MPNN 预测置信度最高 | pLDDT 非实验验证 | Results 图 2g |
| 特异性预测（整体） | NA-MPNN 优于 DeepPBS | vs DeepPBS，228 个复合物 | 中位 MAE 0.53 vs 0.86；交叉熵 1.44 vs 1.05 | NA-MPNN 显著优于 DeepPBS | 仅 RFNA/RFAA 蒸馏结构 | Results 图 4c-d |
| 特异性预测（CIS-BP） | NA-MPNN 在 CIS-BP 上优于 DeepPBS | 子集分析 | MAE 0.52 vs 0.87 | 一致优于 DeepPBS | 子集划分标准未详述 | Results 图 4c |
| 特异性预测（TRANSFAC） | NA-MPNN 在 TRANSFAC 上优于 DeepPBS | 子集分析 | MAE 0.53 vs 0.85 | 一致优于 DeepPBS | 子集划分标准未详述 | Results 图 4d |
| OpenKnot 挑战（第 6 轮） | NA-MPNN 实验可行 | 12 个固定骨架伪结 | 中位实验 OpenKnot 分数 89.9 vs gRNAde 80.7 / 起始序列 87.0 | NA-MPNN 实验表现最优 | 仅 12 个靶标 | Results 图 3a |

## 11 结论正确解读
- **任务范围**：本文结论仅适用于 (1) 骨架条件 RNA 序列设计（backbone-conditioned）和 (2) 固定对接（fixed-dock）蛋白质-DNA 特异性预测。不涉及自由对接（docking）或共进化预测。
- **oracle/真值输入**：设计任务使用晶体结构骨架；特异性任务使用 RFNA/RFAA 预测结构（非实验结构），且 PPM 来自 CIS-BP/TRANSFAC 实验数据。
- **端到端状态**：特异性预测是端到端的（结构→PPM），但依赖外部结构预测器（RFNA/RFAA）生成输入结构。
- **算力成本**：单张 A100 GPU 训练 100,000 batches；推理成本低（30 次采样）。
- **历史数据依赖**：训练数据截至 2025 年 1 月 PDB；RFNA/RFAA 蒸馏数据依赖 RoseTTAFold 系列模型性能。
- **模型依赖**：特异性预测质量受限于 RFNA/RFAA 结构预测精度；设计任务受限于 AlphaFold 3 评估的可靠性。
- **最难场景**：伪结 RNA 设计（恢复率 58.9% 仍低于 RhoDesign 的 67.7%）；非界面 DNA 位置特异性预测（作者通过 uniform PPM 处理，但未单独报告性能）。
- **群体/领域边界**：仅覆盖 RNA/DNA 与蛋白质互作，不涉及 RNA-RNA 或 DNA-DNA 互作；未测试单链 DNA 设计。
- **不确定性**：实验验证仅 12 个伪结靶标；特异性预测的生物学验证（如凝胶迁移实验）未在本文进行。

**有边界的复述**：NA-MPNN 在固定骨架 RNA 序列设计上优于 gRNAde 但不如 RhoDesign，在固定对接蛋白质-DNA 特异性预测上显著优于 DeepPBS，且其设计序列在 12 个伪结靶标上实验折叠正确率最高。这些结论限于 PDB 结构域和 RFNA/RFAA 可预测的复合物类型。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| RNA 设计恢复率低于 RhoDesign | 伪结子集恢复率 58.9% vs 67.7% | 未明确提及改进方向 | Results 图 2c-d |
| 特异性预测依赖 RFNA/RFAA 结构 | 测试集全部为蒸馏结构 | 未明确提及 | Methods: RFNA/RFAA Distillation Dataset |
| 侧链不可知设计 | 未利用侧链原子信息 | 作者认为这避免了信息泄漏，但可能遗漏侧链级互作 | Discussion 节 |
| 未探索其他应用 | RNA 结合蛋白特异性、单链 DNA 设计等未测试 | 作者提及这些是未来应用方向 | Discussion 节 |
| TRANSFAC 数据不可再分发 | 限制可复现性 | 提供非 TRANSFAC 数据列表 | Data Availability 节 |

**作者提及的相关约束**（非正式局限）：
- 设计任务中蛋白质序列固定，未联合设计蛋白质-DNA 界面
- 特异性预测未考虑 DNA 甲基化等化学修饰
- 未与基于序列的预测方法（如 DeepSEA）对比

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 特异性测试集全部为 RFNA/RFAA 蒸馏结构 | 模型可能在蒸馏结构上有偏；真实共晶结构上性能未知 | 蒸馏结构可能比实验结构更"规整"，导致性能虚高 | 在 PDB 共晶结构子集上重新评估 | Methods: RFNA/RFAA Distillation Dataset |
| 与 DeepSEA 等序列方法无对比 | 固定对接场景下，序列方法可能已足够 | 需明确结构信息的增量价值 | 在相同测试集上对比序列基方法 | 未提供 |
| 侧链不可知设计可能丢失关键互作 | 蛋白质-DNA 特异性常由侧链-碱基氢键决定 | 骨架级表征可能无法捕捉这些细节 | 对比含侧链信息的模型（如全原子图） | Discussion 节 |
| 恢复率指标可能高估设计质量 | 高恢复率不等于功能活性 | 需功能实验验证设计序列 | 对设计序列进行体外功能测试 | Results 图 3（仅 12 个靶标） |
| 数据增强中 uniform PPM 可能过度简化 | 非界面位置也可能有序列偏好（如弯曲偏好） | 可能低估非界面位置的生物学意义 | 对比无 uniform PPM 增强的模型 | Data Augmentation 节 |
| 未报告设计序列的多样性 | 高恢复率可能来自记忆训练集 | 需评估生成序列的多样性 | 计算设计序列对间的平均距离 | 未提供 |
| 与 RhoDesign 的差距未深入分析 | 可能 RhoDesign 的扩散模型更适合 RNA 拓扑 | 理解架构差异有助于改进 | 消融 NA-MPNN 的图构建参数 | Results 图 2c |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **统一图表示可跨聚合物类型迁移**：NA-MPNN 证明蛋白质/DNA/RNA 可共享同一图神经网络框架，仅需调整节点类型和原子集。对 TF-DNA 研究：可将转录因子（蛋白质节点）与 DNA 结合位点（DNA 节点）统一建模，无需分别处理。

2. **侧链不可知（side-chain-agnostic）表征避免信息泄漏**：仅用骨架原子（Cα/C1′）而非侧链，天然防止目标序列信息泄漏。对 TF-DNA 特异性预测：DNA 序列是预测目标，不能作为输入特征；骨架级表征是安全选择。

3. **PPM 作为训练目标优于 one-hot**：用实验 PPM 替代单一序列标签，使模型学习分布而非点估计。对 TF-DNA 研究：转录因子结合位点本质是位置频率矩阵，PPM 目标更符合生物学实际。

4. **数据增强策略可强制模型关注界面**：通过丢弃蛋白质链、uniform PPM 非界面位置，迫使模型学习蛋白质诱导的特异性。对 TF-DNA 研究：可迁移至"仅界面"特异性建模，减少骨架几何伪影。

5. **RFNA/RFAA 蒸馏可扩充训练数据**：用结构预测器生成大规模复合物结构，弥补实验结构不足。对 TF-DNA 研究：可对已知 TF 家族批量生成预测复合物，用于特异性模型训练。

6. **随机顺序自回归解码器适用于分布预测**：多次采样平均得到 PPM，比单次贪婪解码更稳健。对 TF-DNA 研究：可用于生成 TF 结合位点候选序列集合。

7. **稀有簇加权采样提升泛化**：对序列聚类度低的样本加权，防止常见结构主导训练。对 TF-DNA 研究：TF 家族间序列差异大，此策略可提升稀有 TF 的特异性预测。

## 15 与已有知识连接
- **ProteinMPNN (Dauparas et al., 2022, Science)**：NA-MPNN 的直接架构基础。ProteinMPNN 证明消息传递图神经网络可用于蛋白质序列设计；NA-MPNN 将其扩展至核酸。对 TF-DNA 研究：ProteinMPNN 的蛋白质设计能力可与 NA-MPNN 的 DNA 设计能力组合，实现 TF-DNA 共设计。
- **LigandMPNN (Dauparas et al., 2023)**：NA-MPNN 的 token-budget 训练策略和优化器设置继承自 LigandMPNN。对 TF-DNA 研究：LigandMPNN 的配体感知设计思路可迁移至"小分子-TF-DNA"三元复合物设计。
- **gRNAde (Joshi et al., 2023)**：RNA 逆折叠的几何深度学习方法。NA-MPNN 在 RNA-only 任务上优于 gRNAde，但伪结任务上两者差距缩小。对 TF-DNA 研究：gRNAde 的 RNA 骨架表征可补充 NA-MPNN 的 RNA 处理能力。
- **RhoDesign (2024)**：基于扩散模型的 RNA 设计。NA-MPNN 在恢复率上低于 RhoDesign，但结构保真度更高。对 TF-DNA 研究：扩散模型与图神经网络的组合可能是未来方向。
- **DeepPBS (2024)**：固定对接蛋白质-DNA 特异性预测的现有方法。NA-MPNN 在 MAE 和交叉熵上均优于 DeepPBS。对 TF-DNA 研究：DeepPBS 的 PPM 对齐算法被 NA-MPNN 采用，可视为该子任务的基准。
- **RoseTTAFoldNA / RoseTTAFold All-Atom (Baek et al., 2023)**：NA-MPNN 特异性训练数据的来源。对 TF-DNA 研究：这些结构预测器可用于生成 TF-DNA 复合物结构，作为特异性预测的输入。
- **CIS-BP (Weirauch et al., 2014) / TRANSFAC (Matys et al., 2003)**：转录因子结合特异性数据库，提供 PPM 标签。对 TF-DNA 研究：这些数据库是 TF 特异性预测的标准训练/评估资源。
- **OpenKnot Challenge (Eterna)**：RNA 伪结设计的社区竞赛。NA-MPNN 在实验验证中表现最优。对 TF-DNA 研究：该竞赛模式可迁移至 TF-DNA 特异性设计的湿实验验证。

## 16 研究想法
**Agent 生成的研究候选**：

1. **TF-DNA 共设计框架**
   - 名称：TF-DNA Co-Design with NA-MPNN
   - 来源局限/观察：NA-MPNN 固定蛋白质序列设计 DNA，但未联合设计蛋白质
   - 核心假设：联合设计 TF 与 DNA 序列可获得更高亲和力/特异性组合
   - 初步方法：扩展 NA-MPNN 解码器，交替采样蛋白质残基与 DNA 碱基；用实验 PPM 约束 DNA 位点
   - 验证方式：对已知 TF 家族（如锌指、bHLH）进行回测，比较共设计 vs 单独设计的结合亲和力
   - 创新状态：unverified

2. **界面感知特异性预测**
   - 名称：Interface-Focused Specificity Prediction
   - 来源局限/观察：NA-MPNN 对非界面位置赋 uniform PPM，但未显式建模界面贡献
   - 核心假设：显式加权界面位置可提升特异性预测精度
   - 初步方法：在 NA-MPNN 损失中引入界面距离加权项；对比均匀权重
   - 验证方式：在 CIS-BP 测试集上比较加权 vs 均匀权重的 MAE
   - 创新状态：unverified

3. **TF 家族迁移学习**
   - 名称：Cross-Family TF Specificity Transfer
   - 来源局限/观察：NA-MPNN 训练数据覆盖多种 TF，但未评估家族间迁移
   - 核心假设：在数据丰富的 TF 家族（如 C2H2 锌指）上预训练，可提升数据稀缺家族（如翼螺旋）的特异性预测
   - 初步方法：按 TF 家族划分训练/测试，评估零样本与少样本迁移
   - 验证方式：家族间迁移性能对比；与从头训练对比
   - 创新状态：unverified

4. **DNA 骨架弯曲感知设计**
   - 名称：Bend-Aware DNA Sequence Design
   - 来源局限/观察：NA-MPNN 仅用 C1′ 原子，未显式编码 DNA 局部弯曲/扭转
   - 核心假设：DNA 骨架几何（弯曲角、扭转角）影响 TF 结合特异性
   - 初步方法：在边特征中加入 DNA 局部螺旋参数（从 C1′/P 原子计算）；对比有无该特征
   - 验证方式：在伪结和蛋白-DNA 复合物测试集上比较恢复率
   - 创新状态：unverified

5. **PPM 不确定性量化**
   - 名称：Uncertainty-Aware Specificity Prediction
   - 来源局限/观察：NA-MPNN 输出点估计 PPM，未提供置信区间
   - 核心假设：对低置信度位置进行实验验证可提高效率
   - 初步方法：在 NA-MPNN 解码器中加入 MC-dropout 或深度集成，输出 PPM 方差
   - 验证方式：比较预测方差与实验 PPM 误差的相关性
   - 创新状态：unverified

6. **RNA 适配体-TF 竞争设计**
   - 名称：Aptamer Competition Design for TF Sequestration
   - 来源局限/观察：NA-MPNN 可设计 RNA 序列，但未用于设计竞争性 RNA 适配体
   - 核心假设：设计高亲和 RNA 适配体可竞争性抑制 TF-DNA 结合
   - 初步方法：以 TF 结构为上下文，用 NA-MPNN 设计 RNA 适配体；用 docking 或实验验证竞争
   - 验证方式：EMSA 竞争实验；比较适配体与天然 DNA 位点的亲和力
   - 创新状态：unverified