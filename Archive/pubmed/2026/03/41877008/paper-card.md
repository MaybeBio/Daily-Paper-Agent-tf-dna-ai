## 01 基本信息

- **标题**：DcSE: an improved densenet with enhanced attention fusion for super-enhancer prediction
- **作者**：Zhang, Ao; Jia, Jianhua
- **单位**：未提供
- **期刊/平台**：BMC Genomics
- **年份**：2026
- **论文类型**：方法学（深度学习架构改进 + 应用）
- **领域**：基因组学 / 调控元件预测（super-enhancer 识别）
- **关键词**：Super-enhancer, DenseNet, CBAM, Attention fusion, Deep learning, TF motif
- **DOI/ID**：10.1186/s12864-026-12768-x
- **代码**：未提供
- **数据**：基于 Luo et al. [9] 的公开数据集（源自 SEdb 2.0 数据库，人类 hg38 与小鼠 mm10）
- **阅读日期**：2026-05-12
- **在该课题方向中的位置**：本文属于「DNA 序列 → 调控元件功能预测」的深度学习分类任务，与 TF–DNA 结合机制相关但非直接建模 TF 结合。其可迁移价值在于：(1) 动态注意力融合机制（channel + spatial）可迁移至 TF 结合位点预测中的特征融合；(2) 基于 mask 的 motif 归因分析为 TF 结合 motif 发现提供了可借鉴的框架；(3) 跨物种验证策略对评估 TF–DNA 结合模型的泛化性有参考意义。

## 02 一句话总结

本文提出 DcSE——一种在 DenseNet 中引入改进 CBAM（动态融合 channel 与 spatial attention）并采用五折集成策略的深度学习框架，用于从 DNA 序列预测 super-enhancer，在人类与小鼠基准数据集上取得优于现有模型的 ACC/AUC/AUPR/F1，并通过 mask 归因分析识别出物种特异的 TF motif（人类 ZKSCAN3、小鼠 STAT1）。

## 03 研究问题

- **具体问题**：如何仅从 DNA 序列（不依赖 ChIP-seq 等多组学实验数据）准确、稳定且可解释地预测 super-enhancer（SE）区域？
- **为什么重要**：SE 是调控基因表达的关键顺式调控元件，其失调与多种重大疾病（尤其癌症）密切相关。实验方法（如 ChIP-seq）成本高、耗时且依赖特定抗体，计算预测方法可大规模、低成本地辅助 SE 鉴定。
- **现有方法不足**：(1) 多数方法依赖 ChIP-seq 等多组学特征，难以在实验条件受限时应用；(2) 基于序列的方法（如 DeepSE、SENet、MuSE）多采用静态特征融合（拼接、固定权重），无法根据输入样本自适应调整不同特征的重要性；(3) 单一模型对数据划分和初始化敏感，稳定性不足。
- **精确研究问题（Can...?）**：Can a DenseNet architecture with dynamically fused channel-spatial attention (via learnable weights) outperform existing static-fusion deep learning models in predicting super-enhancers from raw DNA sequences across species, while maintaining biological interpretability?

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及参考文献，属于「经外部核验」的领域发展框架（结合本文引用与领域常识）。

| 阶段 | 代表方法 | 优点 | 局限 |
|---|---|---|---|
| 实验方法 | ChIP-seq（SE 鉴定金标准） | 直接检测蛋白结合/组蛋白修饰 | 成本高、耗时、依赖抗体质量、难以覆盖所有细胞类型 |
| 传统机器学习 | Improse（36 基因组特征 + ML） | 可解释性较好 | 依赖多组学特征工程，特征获取成本高 |
| 早期深度学习（多组学输入） | DeepSEN（CNN + 表观组学） | 自动特征提取 | 仍依赖 ChIP-seq 数据 |
| 序列-only 深度学习 | DeepSE（DNA2Vec + CNN）、SENet（Transformer）、MuSE（多特征融合） | 仅需序列，成本低 | 静态特征融合，无法自适应；单模型稳定性不足 |
| 本文位置 | DcSE（DenseNet + 动态融合 CBAM + 集成） | 自适应融合 channel/spatial 注意力；集成提升稳定性；mask 归因提供可解释性 | 固定输入长度截断长序列；计算开销高于单模型 |

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 静态特征融合限制精度 | 现有模型（DeepSE、SENet、MuSE）在基准数据集上 ACC/AUC 等指标低于 DcSE | 拼接或固定权重融合无法根据样本特征自适应调整 channel 与 spatial 注意力的贡献 | Results 表 4、5；Introduction 第 4 段 |
| 单模型稳定性不足 | 单一模型对数据划分和初始化敏感，性能波动大 | 模型方差高，缺乏集成策略 | Introduction 第 4 段（"sensitivity to data partitioning and initialization"）；Methods Ensemble Module 节 |
| 序列-only 方法特征提取精度有限 | 无注意力机制的 DenseNet 基线 ACC 仅 57.12%，F1 仅 22.75% | SE 与 TE 序列相似性高，关键调控 motif 稀疏，需注意力机制增强关键特征 | Results 表 3（D 行） |
| 长序列信息丢失 | SE 跨度 8–20 kb，模型采用固定输入长度需截断 | 计算资源限制导致无法处理全长度序列 | Conclusion 节（作者自认局限） |
| 跨物种泛化挑战 | 跨物种预测性能低于种内预测 | 不同物种间调控语法存在差异，但共享保守特征 | Results Cross-species 节（AUC 0.78–0.80 vs 种内 >0.82） |

## 06 核心思想

**1) 表面方法**：构建一个改进的 DenseNet 分类器，在 Dense Block 与 Transition Layer 之间插入改进的 CBAM 模块。该模块并行计算 channel attention 和 spatial attention，并通过两个可学习权重参数（经 sigmoid 约束至 [0,1]）动态加权融合，而非传统 CBAM 的串行相乘。训练阶段采用五折分层交叉验证构建集成模型，预测时对五个子模型输出取平均。

**2) 核心洞察**：SE 与 TE 的序列差异不在于整体组成，而在于稀疏的关键调控 motif 及其空间组织。Channel attention 擅长捕捉"哪些特征通道重要"（对应 motif 组合模式），spatial attention 擅长捕捉"哪些位置重要"（对应 motif 空间分布）。二者是互补信息，但不同样本中二者的相对重要性不同——动态融合允许模型为每个样本自适应分配权重，优于固定顺序或固定权重的融合。

**3) 可能的普适教训 [Analysis]**：在生物序列分类任务中，"注意力机制的类型选择"不如"注意力信息的融合方式"关键。传统 CBAM 的串行结构（channel→spatial）强制了一个固定的信息处理顺序，可能引入偏置；并行计算 + 可学习权重融合允许模型根据输入自适应决定依赖哪种注意力信息，这种"软融合"思想可推广到其他基因组调控元件预测任务（如 promoter、enhancer、TF 结合位点预测）。

## 07 方法总览

- **输入**：DNA 序列（经 DNA2Vec 预训练嵌入，k=6, stride=1），转换为 3000 × 100 维特征矩阵
- **输出**：二分类概率（SE vs TE），sigmoid 输出
- **主要模块**：
  1. **嵌入层**：DNA2Vec 预训练嵌入（可训练微调）
  2. **改进 DenseNet**：2 个 Dense Block（各 5 层，growth rate=32），Block 间插入改进 CBAM，Transition Layer 进行降维
  3. **改进 CBAM**：并行计算 channel attention 与 spatial attention，经可学习权重（sigmoid 约束）加权求和融合
  4. **分类头**：BatchNorm → 全连接（256→64，ReLU）→ Dropout(0.2) → 输出层（sigmoid）
  5. **集成模块**：五折分层交叉验证训练 5 个子模型，预测取平均
- **训练**：优化器、损失函数、学习率调度等具体细节未提供
- **超参数**：growth rate=32，Dense Block 层数=5×2，dropout=0.3（DenseNet 内）/0.2（分类头），嵌入维度=100，序列长度=3000
- **反馈回路**：无显式反馈回路（非迭代式方法）
- **假设**：DNA2Vec 嵌入能捕获序列语义信息；注意力机制能定位关键 motif 区域

**文字流程**：原始 DNA 序列 → DNA2Vec 嵌入（3000×100 矩阵）→ Dense Block 1 特征提取 → 改进 CBAM 动态融合 channel/spatial 注意力 → Transition Layer 降维 → Dense Block 2 进一步特征提取 → 改进 CBAM → Transition Layer → 展平 → 全连接层（256→64，ReLU）→ Dropout → sigmoid 输出概率。五折集成：5 个子模型独立训练，预测概率取平均。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| DNA2Vec 嵌入层 | 将 DNA 序列映射为稠密向量 | 捕获 k-mer 语义信息，避免稀疏 one-hot | 输入：DNA 序列；输出：3000×100 矩阵 | Methods Feature embedding 节；引用 [8] | 预期：特征表示能力下降，模型难以捕获序列语义 [Analysis] |
| DenseNet 骨干（2 个 Dense Block） | 层级特征提取与重用 | 密集连接促进梯度流动与特征复用 | 输入：嵌入矩阵；输出：高维特征图 | Methods Improve DenseNet 节；引用 [24] | 实测：D 基线 ACC 57.12%，F1 22.75%（表 3），远低于完整模型 |
| 改进 CBAM（动态融合） | 并行计算 channel/spatial attention 并动态加权融合 | 自适应平衡两类注意力信息的贡献 | 输入：Dense Block 输出特征图；输出：加权后的特征图 | Results 表 3（DcSE vs D+CA/D+SA/D+TC）；Methods Improve CBAM 节 | 实测：D+CA ACC 77.24%，D+SA 77.78%，D+TC 68.92%，均低于 DcSE 80.81%（表 3） |
| Transition Layer | 降维与压缩 | 控制模型复杂度，减少计算量 | 输入：注意力加权特征图；输出：降维特征图 | Methods Improve DenseNet 节 | 预期：移除后模型参数增加，可能过拟合 [Analysis] |
| 分类头（FC + Dropout + sigmoid） | 特征到概率的映射 | 二分类决策 | 输入：256 维特征；输出：概率 | Methods Sequence prediction 节 | 预期：结构简化可能降低判别能力 [Analysis] |
| 五折集成 | 多模型平均 | 降低方差，提升稳定性 | 输入：5 个子模型预测概率；输出：平均概率 | Methods Ensemble Model 节；Results 表 2（低标准差） | 预期：移除后性能波动增大，标准差上升 [Analysis] |

## 09 关键公式符号

**公式 1：Dense Block 内第 i 层输出**
$$X_i = H_i([X_0, X_1, ..., X_{i-1}])$$

- $X_i$：第 i 层输出特征图
- $H_i(\cdot)$：非线性变换（BatchNorm → ReLU → 64×1 卷积）
- $[\cdot]$：沿通道维度拼接

**公式 2：动态注意力融合**
$$H_{fused} = \sigma(w_t) \cdot h_{Channel} + \sigma(w_g) \cdot h_{Spatial}$$

- $H_{fused}$：融合后的特征
- $\sigma(\cdot)$：sigmoid 函数
- $w_t$：channel attention 的可学习权重（对应 weight_channel）
- $w_g$：spatial attention 的可学习权重（对应 weight_spatial）
- $h_{Channel}$：channel attention 分支输出
- $h_{Spatial}$：spatial attention 分支输出

**公式 3：评估指标**
$$ACC = \frac{TP+TN}{TP+TN+FP+FN}$$
$$REC = \frac{TP}{TP+FN}$$
$$PRE = \frac{TP}{TP+FP}$$
$$F1 = 2 \times \frac{2 \times TP}{2 \times TP + FP + FN} \quad \text{（注：原文公式疑有误，标准 F1 = 2·PRE·REC/(PRE+REC)）}$$
$$AUC = \int_0^1 TPR(FPR) \, d(FPR)$$

- TP/TN/FP/FN：真阳/真阴/假阳/假阴

## 10 实验设计与证据链

**数据集与规模**：
- 人类：10,341 SE（正样本）+ 10,341 TE（负样本），共 20,682 条序列
- 小鼠：11,677 SE + 11,677 TE，共 23,354 条序列
- 数据来源：Luo et al. [9] 公开数据集（源自 SEdb 2.0 数据库）

**指标**：ACC、AUC、AUPR、F1、Recall、Precision

**评测协议**：10 次独立分层随机划分（90% 训练 / 10% 测试），报告均值 ± 标准差。DcSE 内部使用五折交叉验证构建集成模型。

**基线模型**：LR、KNN、NB、SVM、RF（传统 ML）；MuSE、DeepSE、SENet（深度学习方法）

**消融变体**：D（纯 DenseNet）、D+CA（仅 channel attention）、D+SA（仅 spatial attention）、D+TC（传统串行 CBAM）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 主实验（人类） | DcSE 优于现有模型 | 10 次分层划分，同数据同协议 | ACC 80.81±0.97，AUC 87.86±0.81，AUPR 88.11±0.79，F1 80.15±1.07 | DcSE 在人类数据集上全面最优 | 未与更多 SOTA（如 Transformer 大模型）对比 | 表 2、4 |
| 主实验（小鼠） | DcSE 跨物种稳定 | 同上 | ACC 80.16±0.98，AUC 87.04±0.67，AUPR 88.43±0.81，F1 77.96±1.07 | DcSE 在小鼠数据集上同样最优 | 小鼠 Recall 相对较低（70.15%） | 表 2、5 |
| 消融：D vs DcSE | 注意力机制有效性 | 同数据同协议 | D ACC 57.12±7.99，F1 22.75±22.80；DcSE ACC 80.81±0.97 | 注意力机制显著提升性能 | 消融仅验证了注意力整体贡献，未单独验证动态融合 | 表 3 |
| 消融：D+CA / D+SA / D+TC vs DcSE | 动态融合优于单一/串行注意力 | 同上 | D+CA ACC 77.24，D+SA 77.78，D+TC 68.92，均低于 DcSE 80.81 | 动态融合策略优于静态或串行方案 | D+TC 性能波动大（标准差 11.44），可能受初始化影响 | 表 3 |
| 不平衡测试（1:10） | 真实场景鲁棒性 | 训练用平衡数据，测试用 1:10 不平衡 | 人类 ACC 83.60，AUPR 52.32，F1 46.48；小鼠 ACC 88.21，AUPR 55.06，F1 51.64 | DcSE 在不平衡场景下仍保持最优 F1 | AUPR 绝对值不高（~52-55%），仍有改进空间 | 表 6、7 |
| 跨物种验证 | 泛化能力 | 人类训练→小鼠测试，反之亦然 | AUC 0.78-0.80，优于随机但低于种内 | DcSE 捕获跨物种保守调控特征 | 跨物种性能下降明显，物种特异信号仍占主导 | 图 13 |
| Motif 分析 | 生物学可解释性 | mask 归因 + MEME + TomTom | 人类：ZKSCAN3（MA1973.1）；小鼠：STAT1 | DcSE 识别的关键区域富集已知 TF motif | 仅验证了单一 motif，未做全基因组 motif 扫描验证 | Results Motif analysis 节、图 14、15 |

## 11 结论正确解读

- **任务范围**：本文解决的是 **super-enhancer vs typical enhancer 的二分类**问题，而非 SE 的回归打分或全基因组扫描。结论仅适用于该二分类设定。
- **Oracle/真值输入**：训练标签来自 SEdb 2.0 数据库（基于实验数据整理的 SE/TE 注释），本质上是"已注释的 SE/TE 区域"，模型学习的是这些注释区域的序列特征，而非直接学习 SE 的生物学定义。
- **端到端状态**：是端到端的序列→分类，但嵌入层使用 DNA2Vec 预训练初始化（可微调），并非完全从零训练。
- **算力成本**：未提供具体训练时间、GPU 型号等。五折集成 × 10 次划分 = 50 次模型训练，计算成本高于单模型方法。
- **历史数据依赖**：依赖 SEdb 2.0 数据库的注释质量；DNA2Vec 嵌入基于人类基因组训练，可能对非人物种有偏。
- **模型依赖**：DenseNet 超参数（growth rate=32, 2 blocks × 5 layers）基于经验设定，未做系统搜索；CBAM 压缩比固定为 16。
- **最难情形**：不平衡数据下 Recall 较低（人类 78.06%，小鼠 68.71%），表明模型对弱 SE 信号的识别仍有不足；跨物种场景性能下降明显。
- **不确定性**：所有指标为 10 次划分的均值±标准差，但未提供置信区间或统计检验的详细结果（仅提及 Wilcoxon 检验）。
- **边界化复述**：DcSE 在"已注释 SE/TE 的平衡二分类"任务上，以动态融合 channel-spatial 注意力的 DenseNet + 五折集成，在人类和小鼠数据集上取得了优于对比模型的 ACC/AUC/AUPR/F1，并通过 mask 归因识别出物种特异的 TF motif（人类 ZKSCAN3、小鼠 STAT1），但其在不平衡场景下的绝对性能（AUPR ~52-55%）和跨物种泛化（AUC 0.78-0.80）仍有提升空间。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 固定输入长度导致信息丢失 | SE 跨度 8–20 kb，模型需截断长序列 | 探索 Transformer 架构以处理更长上下文 | Conclusion 节 |
| 计算开销高 | 五折集成训练 5 个子模型，计算成本高于单模型 | 研究轻量级模型蒸馏技术 | Conclusion 节 |
| 缺乏细胞类型特异性 | 序列-only 方法无法捕获表观遗传标记提供的动态上下文 | 未明确提及（隐含于对表观数据依赖的讨论中） | Conclusion 节（"inherently lacks the cell-type-specific dynamic context"） |
| 未预测变异功能影响 | 模型仅做 SE/TE 分类，不直接评估非编码变异的功能后果 | 计划扩展至预测 SE 内非编码变异的功能影响 | Conclusion 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 消融实验中 D 基线 F1 仅 22.75%，标准差高达 22.80 | 纯 DenseNet 可能未充分调参，或训练不稳定，导致基线过弱 | 若基线过弱，DcSE 的相对提升可能被夸大 | 对 D 基线进行超参数搜索，报告最佳配置下的性能 | 表 3 |
| D+TC（传统 CBAM）性能波动极大（ACC 68.92±11.44） | 串行 CBAM 可能对初始化敏感，或训练不稳定 | 对比公平性存疑：D+TC 的不稳定性可能源于实现细节而非方法本身 | 多次重复实验，检查收敛曲线和初始化敏感性 | 表 3 |
| 动态融合权重分析仅报告均值（channel ~0.71, spatial ~0.29），未报告样本级分布 | 权重均值可能掩盖重要的样本异质性 | 若权重在不同样本间变化不大，动态融合的优势可能有限 | 分析权重分布与序列特征（如 GC 含量、motif 密度）的相关性 | Results Quantitative analysis 节 |
| 跨物种验证仅报告 AUC，未报告 ACC/F1 等指标 | 跨物种场景下类别不平衡可能影响 AUC 解读 | 完整指标有助于评估实际可用性 | 补充跨物种实验的完整指标矩阵 | 图 13 |
| Motif 分析仅验证了单一 motif（每物种一个） | 可能只报告了最显著的 motif，遗漏其他重要 motif | 单一 motif 不足以支撑"模型捕获关键 TF 调控模式"的结论 | 报告所有显著 motif 及其统计量，与已知 SE 相关 TF 数据库全面比对 | Results Motif analysis 节 |
| 未与最新大模型（如 DNABERT、Nucleotide Transformer）对比 | 对比模型均为较早方法（DeepSE、SENet、MuSE） | 无法判断 DcSE 在当前 SOTA 中的实际位置 | 在相同数据上复现并对比最新预训练基因组模型 | 表 4、5 |
| 不平衡实验中模型权重/采样策略未说明 | 训练集为平衡数据，测试集为 1:10 不平衡，但训练时是否使用类别权重未知 | 影响结果可复现性 | 明确说明训练时的类别不平衡处理策略 | Results Imbalanced datasets 节 |

## 14 学到什么

> **Agent 提炼的知识候选**

1. **动态注意力融合范式**：本文核心可迁移思想是"并行计算多种注意力 + 可学习权重融合"，而非传统串行级联。在 TF–DNA 结合预测中，可设计类似机制融合"序列 motif 注意力"（对应 channel）与"位置/间距注意力"（对应 spatial），让模型自适应决定依赖哪种信息。迁移路径：将改进 CBAM 插入现有 TF 结合预测 CNN/Transformer 的卷积块之间。

2. **Mask 归因 + motif 发现的解释框架**：本文用 mask 滑动窗口识别关键序列区域，再通过 MEME/TomTom 匹配已知 TF motif。该框架可直接迁移至 TF–DNA 结合模型的可解释性分析：对训练好的结合预测模型做 mask 归因，提取高重要性区域做 de novo motif 发现，验证模型是否学到已知 TF 结合偏好。

3. **跨物种验证作为泛化性检验**：本文通过人类↔小鼠交叉验证证明模型捕获跨物种保守特征。在 TF–DNA 结合建模中，可借鉴此策略：用 ChIP-seq 数据丰富的物种（如人类）训练，在数据稀缺物种（如小鼠、斑马鱼）上测试，评估模型是否学到保守的结合机制而非物种特异偏差。

4. **集成策略降低方差**：五折交叉验证 + 多初始化集成有效降低了性能波动（表 2 标准差低）。在 TF 结合预测中，单模型对数据划分敏感是常见问题，可借鉴此集成策略提升稳定性。

5. **序列-only 方法的边界认知**：本文明确承认序列-only 方法缺乏细胞类型特异性上下文。在 TF–DNA 结合建模中，应明确区分"序列内在编码能力"与"细胞上下文依赖"，避免过度宣称序列-only 模型的普适性。

6. **类别不平衡评估协议**：本文用平衡训练 + 不平衡测试的协议模拟真实场景，并强调 AUPR/F1 优于 ACC/AUC。TF 结合位点预测天然存在严重类别不平衡，此评估协议值得借鉴。

## 15 与已有知识连接

- **DenseNet**：Huang et al. (2017) 提出的密集连接卷积网络，本文作为骨干网络。在基因组序列建模中，DenseNet 的密集连接有利于梯度流动和特征复用，适合捕获序列中的层级模式。
- **CBAM**：Woo et al. (2018) 提出的卷积注意力模块，本文改进其串行结构为并行+动态融合。CBAM 在计算机视觉中广泛验证，本文将其适配到一维序列数据。
- **DNA2Vec**：Ng (2017) 提出的 k-mer 词嵌入方法，本文用于序列编码。与 One-Hot、k-mer 计数相比，DNA2Vec 能捕获 k-mer 语义关系。
- **SE 识别方法谱系**：从实验方法（ChIP-seq + ROSE, Whyte et al. 2013）到计算预测（DeepSE、SENet、MuSE），本文属于序列-only 深度学习方法的发展分支。
- **可解释性方法**：mask 归因与 LIME/SHAP 思想一致，但针对序列数据做了滑动窗口适配；MEME/TomTom 是 motif 发现的经典工具（Bailey et al.）。
- **与 TF–DNA 结合预测的关联**：SE 区域的特征之一是高密度 TF 结合位点富集，本文识别的 ZKSCAN3（人类）和 STAT1（小鼠）均为已知转录因子。本文的架构和解释框架可迁移至更细粒度的 TF 结合位点预测任务（如 DeepBind、DeepSEA、BPNet 等方法的补充或改进方向）。

## 16 研究想法

> **Agent 生成的研究候选**

1. **候选名称**：TF-DynFusion——动态注意力融合的 TF 结合位点预测模型
   - **来源局限/观察**：DcSE 的动态融合思想在 SE 预测中有效，但 SE 是区域级标签，TF 结合是位点级标签，分辨率不同。现有 TF 结合预测模型（如 DeepBind、DeepSEA）多使用固定融合或简单拼接。
   - **核心假设**：在 TF 结合位点预测中，动态融合 motif 特征注意力与位置特征注意力可提升预测精度，尤其对结合 motif 较弱但位置保守的 TF。
   - **初步方法**：以 DcSE 的改进 CBAM 为核心，替换 TF 结合预测模型的卷积块间连接；在 ENCODE 多个 TF 的 ChIP-seq 数据集上评估。
   - **验证方式**：与 DeepBind、DeepSEA 等基线对比 AUC/AUPR；消融验证动态融合 vs 串行 CBAM。
   - **创新状态**：unverified

2. **候选名称**：Cross-Species TF Motif Transferability 评估框架
   - **来源局限/观察**：DcSE 的跨物种验证显示模型捕获保守特征，但仅验证了 SE 分类任务。TF 结合机制在物种间的保守性是否可迁移至结合位点预测，缺乏系统评估。
   - **核心假设**：在人类训练的 TF 结合模型可迁移至小鼠，但迁移效果因 TF 的保守性而异（如基本转录因子 vs 物种特异因子）。
   - **初步方法**：用 DcSE 的跨物种验证协议（人类训练→小鼠测试，反之亦然），在多个 TF 上系统评估迁移性能，结合 motif 保守性分析解释迁移差异。
   - **验证方式**：跨物种 AUC 与 TF 保守性（如序列同源性、motif 相似性）的相关性分析。
   - **创新状态**：unverified

3. **候选名称**：Mask Attribution 与 TF Motif 发现的系统比较
   - **来源局限/观察**：DcSE 用 mask 归因识别关键区域，但未与梯度类方法（saliency map、DeepLIFT）或 attention 权重做系统比较。不同归因方法在 TF motif 发现上的优劣缺乏基准。
   - **核心假设**：mask 归因在识别稀疏、短小的 TF motif 上优于梯度类方法，因其对不连续特征的敏感性不同。
   - **初步方法**：在已知 motif 的合成序列和真实 ChIP-seq 数据上，比较 mask 归因、saliency、DeepLIFT、attention 权重的 motif 恢复率（以 TomTom 匹配为指标）。
   - **验证方式**：motif 恢复率、定位精度（与已知结合位点的距离分布）。
   - **创新状态**：unverified

4. **候选名称**：长序列 SE 预测的 Transformer 替代方案
   - **来源局限/观察**：DcSE 作者自认固定输入长度限制是局限，并提出 Transformer 作为未来方向。但 Transformer 在超长序列（8–20 kb）上的计算成本极高。
   - **核心假设**：结合 CNN 下采样与稀疏注意力（如 Longformer、BigBird）可在不截断序列的前提下处理全长度 SE，且性能优于截断方案。
   - **初步方法**：设计 CNN 下采样 + 稀疏注意力的混合架构，在 DcSE 数据集上对比截断 vs 全长度处理。
   - **验证方式**：ACC/AUC/AUPR 对比 + 计算效率（训练时间、显存占用）对比。
   - **创新状态**：unverified

5. **候选名称**：SE 预测中的类别不平衡鲁棒性基准
   - **来源局限/观察**：DcSE 在不平衡测试集上 AUPR 仅 ~52-55%，表明真实场景下性能仍有瓶颈。现有 SE 预测文献对不平衡处理的讨论不足。
   - **核心假设**：结合 focal loss 或困难样本挖掘可显著提升不平衡场景下的 AUPR，且与架构改进正交。
   - **初步方法**：在 DcSE 架构上替换损失函数（focal loss、weighted BCE），在 1:10 和 1:100 不平衡测试集上系统评估。
   - **验证方式**：AUPR、F1 对比；与阈值调整、重采样等传统方法比较。
   - **创新状态**：unverified