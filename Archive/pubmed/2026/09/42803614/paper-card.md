## 01 基本信息
- **标题**：Supervised clustering of bacterial promoter identifies two groups with different relevant positions at −10
- **作者**：Cambranis-Boldo, Paulo; Martinez, Gustavo Sganzerla; Farias, Andre Borges; Perez-Rueda, Ernesto
- **单位**：未提供（据通讯作者 Perez-Rueda 推断与 UNAM 相关，但原文未明确列出单位列表）
- **期刊/平台**：Briefings in Functional Genomics
- **年份**：2026（在线日期 2026-09-28）
- **论文类型**：研究论文（Research Article）
- **领域**：细菌启动子分类；σ因子–DNA互作；可解释机器学习（SHAP）；监督聚类
- **关键词**：promoter classification; sigma factor; Shapley values; supervised clustering; DNA duplex stability
- **DOI/arXiv**：10.1093/bfgp/elag008
- **代码**：未提供
- **数据**：RegulonDB v12.0 下载的 3217 条启动子序列（处理后 2938 条）；补充材料 S1–S19
- **阅读日期**：2026-05-12（按当前日期推算）
- **在课题方向中的位置**：本文属于「TF–DNA 互作 × 可解释 AI」交叉方向，聚焦细菌 σ因子–启动子识别。其核心贡献在于：用 SHAP 值（而非序列 motif 或结构特征）作为监督聚类的输入，发现 σ70 启动子内部存在 −10 区域不同保守模式的亚类，并关联到 DNA 双链解链（open complex formation）机制。对 TF–DNA 结合机制研究提供了「从 ML 特征重要性到生物学亚类发现」的可迁移范式。

## 02 一句话总结
本文用 DNA 双链稳定性（DDS）编码 2938 条 E. coli K-12 启动子序列，训练随机森林区分启动子与非启动子，用 SHAP 值做监督聚类，发现 σ70 启动子可分成 5 个亚类，其核心差异在于 −9 至 −7 位置的碱基保守性（AT/TA 富集 vs. 低信息含量），提示 −10 区域存在不同的 DNA 解链机制。

## 03 研究问题
- **具体问题**：细菌启动子序列在 σ70 家族内部是否存在可区分的亚类？这些亚类是否在 −10 区域（关键识别位点）具有不同的序列保守模式？
- **为什么重要**：σ70 是细菌最主要的持家 σ因子，其启动子识别机制被认为是相对统一的（−10 TATAAT、−35 TTGACA）。如果 σ70 内部存在序列亚类，则意味着 σ70–DNA 互作存在多种模式，可能对应不同的转录调控策略或不同的 DNA 解链动力学。
- **现有方法不足**：传统启动子分类依赖 motif 比对（如 PWM）或 unsupervised clustering（如 k-means on k-mer），这些方法无法利用「哪些位置对功能重要」的先验信息，且难以处理高维序列特征中的低方差区域。无监督聚类对高维稀疏序列数据敏感，聚类结果往往反映序列组成差异而非功能相关差异。
- **精确研究问题**：Can a supervised clustering workflow (RF + SHAP + UMAP + DBSCAN) identify biologically meaningful subgroups within σ70 promoter sequences that differ in their −10 region conservation patterns?

## 04 背景与发展脉络
*注：以下脉络为「经外部核验」的领域常识与本文框架的结合。*

1. **阶段一：启动子 consensus 描述（1970s–1990s）**
   - 代表方法：Pribnow box（−10 TATAAT）和 −35 TTGACA 的 consensus 序列比对。
   - 优点：简单、可解释，奠定了启动子识别的核心概念。
   - 局限：无法解释序列变异如何影响功能；consensus 掩盖了亚类差异。

2. **阶段二：PWM 与信息论方法（1990s–2010s）**
   - 代表方法：Position Weight Matrix、sequence logo、information content 分析。
   - 优点：量化每个位置的保守程度，识别关键碱基。
   - 局限：PWM 假设位置独立，无法捕捉协同效应；仍以「单一 motif」为假设前提。

3. **阶段三：机器学习分类（2010s–2020s）**
   - 代表方法：CNN（如 DeepPromoter）、XGBoost、SVM 用于启动子/非启动子分类。
   - 优点：高准确率，可处理复杂非线性特征。
   - 局限：黑箱模型，难以解释「哪些位置、什么模式」驱动分类；分类 ≠ 发现新亚类。

4. **阶段四：可解释 ML + 聚类（本文位置，2020s 中期）**
   - 代表方法：SHAP 值 + 降维 + 密度聚类（本文 workflow）。
   - 优点：利用 ML 的特征重要性指导聚类，使聚类结果反映「功能相关」的序列差异而非任意序列组成差异。
   - 局限：依赖训练标签（启动子 vs 非启动子）的质量；SHAP 值反映的是模型视角而非直接生物学机制。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 启动子分类未捕捉功能亚类 | 传统分类将 σ70 视为单一同质群体 | 现有分类依赖 motif 保守性或序列相似性，未利用「哪些位置对功能重要」的信息 | Introduction 节：promoter sequences may differ even inside the same family, and this classification may not fully capture the sequence and functional diversity of groups |
| 高维序列特征难以聚类 | DNA 序列高维、稀疏、低方差特征多，无监督聚类结果不稳定 | 无监督聚类无法区分「功能相关」与「功能无关」的序列变异 | Introduction 节：DNA sequence data represents a challenge to identify patterns due to its high dimensionality and low variance of some features |
| ML 模型黑箱问题 | 分类准确但无法解释决策依据 | 标准 ML 分类不提供位置级别的特征归因 | Methods 节：Shapley values... allowing a deeper understanding of model predictions |
| 随机负样本可能影响结果 | 负样本（非启动子）的生成方式可能影响 SHAP 值 | 作者通过多随机种子重复实验验证稳健性 | Methods 节 Robustness 段落：re-executed five times using a different random seed... Pearson correlation coefficient |
| DDS 编码的生物学解释 | DDS 是间接特征，需映射回序列/结构机制 | DDS 反映 DNA 双链稳定性，与启动子解链直接相关 | Discussion 节：local duplex stability governs DNA strand separation during transcription initiation |

## 06 核心思想
1. **表面方法**：用 DDS 值编码启动子序列 → 训练随机森林区分启动子/非启动子 → 对每个启动子计算 SHAP 值向量 → UMAP 降维 → DBSCAN 聚类 → 对每个簇做 sequence logo 和 DDS 谱分析。
2. **核心洞察**：SHAP 值不仅解释模型预测，其本身可作为「功能重要性谱」用于聚类。聚类结果揭示 σ70 启动子存在两类：一类在 −9 至 −7 有强 AT/TA 保守（P 型，peak），另一类在该区域信息含量极低（V 型，valley）。这一差异直接对应 DNA 解链的难易程度，提示 σ70 可能通过不同的解链策略识别启动子。
3. **可能的普适教训** [Analysis]：在序列-功能关系研究中，用「模型特征重要性」而非「原始序列」做聚类，可以过滤掉功能无关的序列变异，使聚类结果更贴近生物学机制。这一思路可迁移到 TF–DNA 结合位点亚型发现、增强子/启动子功能分类等场景。

## 07 方法总览
- **输入**：2938 条 E. coli K-12 启动子序列（81 bp，−60 至 +20），来自 RegulonDB v12.0；6 个 σ因子家族（σ70, σ38, σ32, σ28, σ24, σ54）；负样本为随机生成的 DNA 序列（保持碱基频率一致）。
- **特征编码**：DDS（DNA duplex stability）值，每个二核苷酸一个值，序列长度 81 bp → 80 维特征向量。
- **模型**：随机森林（Random Forest），用于启动子/非启动子二分类。
- **可解释性**：TreeSHAP 计算每个样本每个特征的 SHAP 值。
- **降维**：UMAP（n_neighbors 参数扫描 10–1000）。
- **聚类**：DBSCAN（epsilon=1.5, min_samples=10）。
- **下游分析**：每个簇的 sequence logo（Logomaker）、DDS 谱、信息含量、与实验活性数据（参考文献 [40]）比对。
- **稳健性检验**：5 个随机种子生成负样本，重复全流程，计算 SHAP 谱 Pearson 相关和聚类一致性（ARI）。
- **统计检验**：Kruskal–Wallis 检验 + Dunn 事后检验比较簇间 DDS 差异。
- **输出**：σ70 的 5 个亚类（C0–C4），其中 C0 为 P 型（−9 至 −7 高保守 AT/TA），C1–C4 为 V 型（低保守）；全家族聚类得到 P/V 两大类。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| DDS 特征编码 | 将序列转换为连续物理化学特征 | 捕获 DNA 双链稳定性，直接关联解链机制；比 one-hot 编码更紧凑 | 输入：81 bp 序列；输出：80 维 DDS 向量 | Methods 节；Fig 2 显示 σ70 在 −10 附近 DDS 方差低 | [预期] 若用 one-hot 编码，特征维度高 4 倍，SHAP 值更稀疏，聚类可能更碎片化 |
| 随机森林分类器 | 区分启动子/非启动子 | 提供 SHAP 值计算的基础模型；RF 支持精确 TreeSHAP | 输入：DDS 特征；输出：二分类概率 | Methods 节：RF selected for exact TreeSHAP implementation | [预期] 若用 SVM 或神经网络，SHAP 为近似值，聚类稳定性可能下降 |
| TreeSHAP 特征归因 | 计算每个位置对分类的贡献 | 将模型决策分解到每个序列位置 | 输入：RF 模型 + 样本；输出：80 维 SHAP 向量/样本 | Methods 节；Fig 3 显示 SHAP 峰值与 DDS 峰对齐 | [预期] 若用 permutation importance 替代，只能得到全局重要性，无法做单样本聚类 |
| UMAP 降维 | 将 80 维 SHAP 空间降至 4 维 | 使 DBSCAN 在高维空间可行且可视化 | 输入：SHAP 向量矩阵；输出：4 维嵌入 | Methods 节；Fig 4 显示清晰分离 | [预期] 若用 PCA，可能无法保留局部密度结构，聚类效果差 |
| DBSCAN 聚类 | 识别 SHAP 空间中的稠密区域 | 无需预设簇数，可发现任意形状簇 | 输入：4 维 UMAP 嵌入；输出：簇标签 | Methods 节；Fig 4 显示正负样本分离、正样本内多簇 | [实测] 作者报告 n_neighbors 参数影响簇数量，但簇成员组成稳定 |
| Sequence logo 分析 | 可视化每个簇的序列保守性 | 将 SHAP 聚类结果映射回序列特征 | 输入：簇内序列；输出：PWM/logo | Fig 5–6 显示 P/V 型在 −9 至 −7 的保守性差异 | [预期] 若不做此步，无法解释簇的生物学意义 |
| 稳健性检验 | 验证结果不依赖随机种子 | 排除负样本生成方式导致的假阳性 | 输入：5 组随机种子；输出：Pearson r、ARI | Methods 节 Robustness 段落 | [实测] 作者报告 SHAP 谱高度相关，ARI 显示聚类一致 |

## 09 关键公式符号
本文未使用显式数学公式。核心概念定义如下：

- **DDS（DNA duplex stability）**：每个二核苷酸的自由能参数，值越低表示该二核苷酸对越稳定（GC 含量高），值越高表示越不稳定（AT 含量高）。序列 S 的 DDS 向量为 D(S) = [d_1, d_2, ..., d_{L-1}]，其中 d_i 为位置 i 和 i+1 处二核苷酸的稳定性值。
- **SHAP 值**：对样本 x 的第 j 个特征，SHAP 值 φ_j 满足：
  φ_j = Σ_{S ⊆ F \ {j}} [ |S|! (|F|-|S|-1)! / |F|! ] × [ f_{S ∪ {j}}(x_S ∪ {j}) - f_S(x_S) ]
  其中 F 为全部特征集，f_S 为仅用 S 中特征训练的模型。本文中 φ_j 表示位置 j 的 DDS 值对「启动子/非启动子」分类的边际贡献。
- **信息含量（Information Content）**：IC_i = 2 + Σ_b p_{i,b} log₂ p_{i,b}（bits），其中 p_{i,b} 为位置 i 碱基 b 的频率。

## 10 实验设计与证据链
- **数据集**：2938 条 E. coli K-12 启动子（RegulonDB v12.0），6 个 σ因子家族；负样本为随机生成的 DNA 序列（保持碱基频率一致）。
- **数据规模**：σ70 家族 1500 条（用于亚聚类）；全家族 540 条（90/家族，用于 P/V 分析）。
- **指标**：分类准确率、AUC、SHAP 谱 Pearson 相关系数、ARI（聚类一致性）。
- **基线**：SVM（RBF kernel）作为替代分类器；无监督聚类（未明确指定具体算法，但对比了 SHAP 聚类与直接序列聚类的差异）。
- **评测协议**：80/20 train-test split 用于评估分类性能；SHAP 聚类在全量数据上进行；5 个随机种子重复验证稳健性。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-------------|-------------------|------|
| 分类器性能比较 | RF 适合此任务 | RF vs Extra Trees, AdaBoost, Gradient Boosting, SVM | 所有 tree-based 方法性能相当，均优于 SVM | RF 因 TreeSHAP 精确性被选中 | 不证明 RF 在生物学上最优 | Results 节；Supplementary S8 |
| SHAP 峰值定位 | 模型关注 −10 区域 | 正类（启动子）SHAP 谱 vs 负类 | SHAP 峰值在 −11 至 −6 位置，与 DDS 低方差区重合 | 模型识别到 −10 区域为关键判别特征 | 不证明 −10 是唯一功能区域 | Fig 3 |
| 全家族聚类 | 启动子存在 P/V 两类 | DBSCAN on SHAP 嵌入 | 正样本聚为两类：P（高 AT/TA 保守）和 V（低保守） | 启动子可按 −9 至 −7 保守性二分 | 不证明 P/V 对应不同生物学功能 | Fig 5 |
| σ70 亚聚类 | σ70 内部存在多个亚类 | DBSCAN on σ70 SHAP 嵌入 | 5 个簇（C0–C4），C0 为 P 型，C1–C4 为 V 型 | σ70 启动子内部存在结构异质性 | 不证明 5 个簇均有独立功能 | Fig 4a, Fig 6 |
| 稳健性检验 | 结果不依赖随机种子 | 5 个种子重复全流程 | SHAP 谱 Pearson r 高，ARI 显示聚类一致 | 负样本生成方式不影响主要结论 | 不排除其他负样本生成策略的影响 | Methods 节 Robustness |
| 与实验活性数据比对 | P/V 型与启动子强度相关 | 参考文献 [40] 的活性数据 vs 簇标签 | 平均 20% 的启动子/簇有活性；C6, C8, C2 活性最高 | P 型（高保守）可能对应更强启动子 | 样本量小，未做统计检验 | Discussion 节；Supplementary S18 |

## 11 结论正确解读
- **任务范围**：本文仅针对 E. coli K-12 的 6 个 σ因子家族启动子，不涉及其他细菌物种或真核启动子。
- **Oracle/真值输入**：启动子/非启动子标签来自 RegulonDB 注释；负样本为随机生成序列（非真实基因组非启动子区域）。
- **端到端状态**：非端到端。分类器仅用于生成 SHAP 值，聚类和生物学解释是独立的下游分析。
- **算力成本**：低。RF + SHAP + UMAP + DBSCAN 均为轻量级算法，可在普通工作站运行。
- **历史数据依赖**：依赖 RegulonDB v12.0 的注释质量；启动子集合可能存在实验偏差（偏好已知强启动子）。
- **模型依赖**：SHAP 值依赖 RF 模型；不同分类器可能产生不同 SHAP 谱，但作者验证了 tree-based 方法间的一致性。
- **最难情形**：σ54 启动子（数量少、motif 结构不同）在聚类中分离度较低；V 型启动子的功能意义尚不明确。
- **群体/领域边界**：结论限于 E. coli σ70 启动子；P/V 分类是否适用于其他 σ因子或物种未知。
- **不确定性**：P/V 型与启动子活性的关联仅基于参考文献 [40] 的初步比对，未做独立实验验证；5 个簇的生物学意义（除 C0 外）未深入讨论。

**有边界的复述**：在 E. coli K-12 的 σ70 启动子集合中，基于 SHAP 值的监督聚类可稳定识别出至少两类启动子：一类在 −9 至 −7 位置具有高保守的 AT/TA 富集（P 型），另一类在该区域序列保守性极低（V 型）。这一差异提示 σ70–DNA 互作可能存在不同的解链策略，但 P/V 分类的功能后果（如转录强度差异）仍需实验验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 负样本为随机生成序列 | 非真实基因组非启动子区域，可能高估分类性能 | 使用真实基因组背景序列作为负样本 | Methods 节：negative sequences consist of randomly generated DNA strings |
| 聚类参数需人工调整 | n_neighbors 和 epsilon 需经验选择 | 未明确提及 | Methods 节：parameters determined empirically |
| P/V 功能意义未验证 | 未做实验验证 P/V 型启动子的转录活性差异 | 与实验数据比对（参考文献 [40]）是初步的，需更多实验证据 | Discussion 节：further experimental evidence is necessary |
| 仅限 E. coli | 结论可能不适用于其他细菌 | 未明确提及 | 全文范围限定于 E. coli K-12 |
| 分类性能非主要目标 | 模型「记忆」特征而非泛化 | 作者明确说明分类不是主要目标 | Methods 节：Classification is not the main objective of this work |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|----------------------|----------|----------|------|
| 负样本为随机 DNA 序列 | 随机序列缺乏真实基因组背景特征（如 GC 含量分布、调控区域结构），模型可能学习到「非随机性」而非「启动子特征」 | 若负样本不具代表性，SHAP 值反映的「重要位置」可能偏向区分随机 vs 非随机，而非启动子功能关键位点 | 使用 E. coli 基因组中非启动子间区序列作为负样本，重复全流程 | Methods 节：randomly generated DNA strings |
| SHAP 聚类依赖模型选择 | 不同分类器（如 SVM）的 SHAP 近似值可能产生不同聚类结果 | 结论的稳健性应跨模型验证，而非仅 tree-based | 用 SVM 或神经网络 + KernelSHAP 重复聚类，比较簇结构 | Methods 节：RF selected for exact TreeSHAP |
| P/V 分类的生物学解释偏推测 | 作者将 P/V 型与 DNA 解链机制关联，但未提供直接实验证据（如解链温度、open complex 形成速率） | 如果 P/V 仅是序列组成的统计差异，而非功能差异，则生物学意义有限 | 测量 P/V 型启动子的体外转录活性、解链动力学 | Discussion 节：suggest that this region is central for the transcription initiation |
| 5 个 σ70 簇的稳定性未充分验证 | 作者报告 n_neighbors 影响簇数，但未报告簇间距离/分离度指标 | 如果簇间边界模糊，5 簇划分可能过细 | 计算簇间 Silhouette score，或使用层次聚类验证 | Methods 节：parameters determined empirically |
| 与实验活性数据的比对样本量小 | 参考文献 [40] 的活性数据可能仅覆盖部分启动子 | 20% 活性比例可能受采样偏差影响 | 扩大活性数据集，或使用报告基因系统验证 | Discussion 节：Supplementary S18 |
| DDS 编码的粒度限制 | DDS 是二核苷酸级特征，无法捕获更长范围的 motif 协同效应 | σ因子可能识别更长的结合位点，二核苷酸级编码可能遗漏关键信息 | 使用三核苷酸或 k-mer 特征重复分析 | Methods 节：DDS value to every dinucleotide |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **SHAP 值作为聚类输入的可迁移方法**：本文最核心的可迁移思路——用模型特征重要性（SHAP 值）而非原始特征做聚类。在 TF–DNA 互作研究中，若目标是发现结合位点亚型，可先训练一个「结合 vs 非结合」分类器，然后用 SHAP 值对结合位点聚类，这样聚类结果直接反映「驱动结合的序列特征」而非所有序列变异。**迁移路径**：对 ChIP-seq 定义的 TF 结合位点，用 CNN 或 RF 训练结合/非结合分类器，SHAP 值聚类后分析各簇的 motif 和结构特征。

2. **DDS 作为序列编码的生物学可解释性**：用 DNA 双链稳定性编码序列，使 ML 特征直接对应物理化学机制（解链难度）。在 TF–DNA 互作研究中，可类似地用 DNA 弯曲性、电荷分布、氢键模式等物理化学参数编码序列，使 SHAP 值直接反映「哪些位置的物理化学性质驱动结合」。**迁移路径**：对 TF 结合位点，计算 DDS、DNA 弯曲刚度、minor groove width 等结构参数作为特征，训练结合预测模型。

3. **P/V 二分的生物学假设**：启动子（或 TF 结合位点）可能存在「高保守核心 + 低保守侧翼」的连续谱，而非单一 consensus。在 TF–DNA 互作研究中，可检验 TF 的结合位点是否也存在类似的二分（如高亲和力/低亲和力位点的序列特征差异）。**迁移路径**：对同一 TF 的高/低亲和力结合位点分别做 SHAP 分析，比较关键位置差异。

4. **稳健性检验的简洁设计**：用多个随机种子生成负样本，重复全流程，用 Pearson 相关和 ARI 量化结果稳定性。这一设计成本低、易实现，适合作为任何 ML+生物学发现工作的标准检验。**迁移路径**：在 TF 结合位点亚型发现中，用不同随机种子生成负样本，验证聚类结果一致性。

5. **从 ML 重要性到序列 logo 的闭环**：SHAP 值 → 聚类 → 每个簇的 sequence logo → 回到生物学机制。这个闭环确保 ML 结果可被序列层面验证。**迁移路径**：对每个 TF 结合位点亚类，生成 sequence logo 和结构模型，验证亚类间的机制差异。

## 15 与已有知识连接
- **RegulonDB**（Salgado et al., 2024, Nucleic Acids Research）：本文数据来源，E. coli 调控元件的权威数据库。TF–DNA 互作研究中常用的启动子、TFBS 注释来源。
- **DNA 双链稳定性与启动子强度**（文献 [8,9]）：已有研究表明 DDS 与启动子活性相关，本文将其扩展为分类特征。
- **SHAP 值在调控基因组学中的应用**（Lundberg & Lee, 2017; Shapley, 1953）：SHAP 已在 TFBS 预测、变异效应预测中广泛使用，本文将其用于聚类是较新用法。
- **σ因子–启动子互作的机制研究**（文献 [3,4,39]）：−10 区域在 open complex 形成中的作用已有大量生化研究，本文的 P/V 分类为这一机制提供了序列层面的新视角。
- **监督聚类（supervised clustering）**（文献 [25]）：利用标签信息指导聚类的思想在图像、文本领域已有应用，本文将其引入启动子分类。
- **可迁移的候选方向** [Analysis]：本文的 workflow 可直接迁移到真核 TF–DNA 互作研究，如对同一 TF 在不同细胞类型或不同染色质状态下的结合位点做 SHAP 聚类，可能发现序列偏好差异。此外，结合 AlphaFold 或 MD 模拟，可进一步验证 P/V 型启动子与 σ70 结合时的结构差异。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合位点的 SHAP 驱动亚型发现（SHAP-Driven Subtyping of TF–DNA Binding Sites）
   - **来源局限/观察**：本文仅针对细菌启动子，真核 TF 结合位点通常更复杂（含辅助 motif、染色质上下文），尚无类似 SHAP 聚类分析。
   - **核心假设**：同一 TF 在不同基因组上下文中的结合位点可分成功能相关的亚型，其差异集中在核心 motif 侧翼的特定位置。
   - **初步方法**：用 ChIP-seq 数据训练 CNN 分类器（结合 vs 非结合），对结合位点计算 SHAP 值，UMAP + HDBSCAN 聚类，对每个簇做 motif 分析和功能富集（如 GO、eQTL 共定位）。
   - **验证方式**：用 CRISPR 突变验证簇间关键位置的功能差异；比较簇间 TF 结合亲和力（如 HT-SELEX 数据）。
   - **创新状态**：unverified

2. **候选名称**：σ因子–启动子互作的 MD 模拟验证（MD Simulation of σ Factor–Promoter Complexes Across P/V Subtypes）
   - **来源局限/观察**：本文提出 P/V 型启动子可能对应不同解链机制，但未做结构验证。
   - **核心假设**：P 型（高 AT 保守）启动子在 open complex 形成中具有更低的自由能壁垒，V 型需要额外的辅助因子或超螺旋协助。
   - **初步方法**：选取 P/V 型代表性启动子，用 AlphaFold3 或 MD 模拟 σ70–启动子复合物，比较 DNA 解链动力学、σ70 结构域构象变化。
   - **验证方式**：计算 open complex 形成自由能剖面；与单分子 FRET 实验数据对比。
   - **创新状态**：unverified

3. **候选名称**：跨物种启动子亚型保守性分析（Cross-Species Conservation of Promoter Subtypes）
   - **来源局限/观察**：本文结论限于 E. coli K-12，未知 P/V 分类是否在其他细菌中保守。
   - **核心假设**：P/V 二分在 γ-proteobacteria 中保守，但在 σ因子 repertoire 不同的物种中可能消失或改变。
   - **初步方法**：从 RegulonDB 和 NCBI 收集多个物种的启动子数据，用本文 workflow 重复分析，比较簇结构和 −10 区域保守性。
   - **验证方式**：系统发育比较；检查 P/V 型与 σ因子共进化关系。
   - **创新状态**：unverified

4. **候选名称**：基于 SHAP 的启动子强度预测与设计（SHAP-Based Promoter Strength Prediction and Design）
   - **来源局限/观察**：本文发现 −9 至 −7 位置对分类最重要，这些位置可能也影响启动子强度。
   - **核心假设**：SHAP 值高的位置对启动子强度贡献大，可用于指导合成启动子设计。
   - **初步方法**：用本文 workflow 在启动子强度数据集（如 EMOPEC）上训练回归模型，用 SHAP 值识别关键位置，设计变异库并测量强度。
   - **验证方式**：比较 SHAP 引导设计与随机突变的强度分布；与现有预测模型（如 PromoterCalculator）对比。
   - **创新状态**：unverified

5. **候选名称**：TF–DNA 结合机制的物理化学特征编码比较（Comparative Analysis of Physicochemical Encodings for TF–DNA Binding）
   - **来源局限/观察**：本文用 DDS 编码，但未与其他编码（one-hot、k-mer、结构特征）系统比较。
   - **核心假设**：物理化学编码（DDS、弯曲刚度、静电势）比序列身份编码更能捕获 TF–DNA 结合的机制性差异。
   - **初步方法**：在多个 TF–DNA 结合数据集上，比较不同编码 + 同一分类器的性能，并用 SHAP 值分析各编码下的关键位置。
   - **验证方式**：跨数据集一致性检验；与已知 TF–DNA 结构（PDB）比对，验证 SHAP 高值位置是否对应直接接触残基。
   - **创新状态**：unverified