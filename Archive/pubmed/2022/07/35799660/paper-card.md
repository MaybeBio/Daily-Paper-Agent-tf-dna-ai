## 01 基本信息
- **标题**：Comparative Analysis on Alignment-Based and Pretrained Feature Representations for the Identification of DNA-Binding Proteins
- **作者与单位**：Chen, Die; Zhang, Hua; Chen, Zeqi; Xie, Bo; Wang, Ye（单位未提供）
- **期刊/预印本平台**：Computational and Mathematical Methods in Medicine
- **年份**：2022-07-09
- **论文类型**：方法比较研究（comparative study）
- **领域**：蛋白质-DNA互作（DNA-binding protein 识别）× 机器学习/预训练语言模型
- **关键词**：DNA-binding proteins (DBPs)；PSSM；ESM-1b；feature selection；ensemble
- **DOI/arXiv 号**：10.1155/2022/5847242
- **代码**：未提供
- **数据**：PDB1616（训练集，808 DBP + 808 non-DBP）；PDB186（独立测试集，93 DBP + 93 non-DBP）；数据可在论文及补充材料中获取
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文聚焦于 DNA-binding protein（DBP）的序列级二分类识别，比较了传统 alignment-based 的 PSSM 特征与基于预训练蛋白质语言模型 ESM-1b 的特征表示。该文不涉及 TF–DNA 结合机制的结构解析或结合位点预测，但其核心问题——"预训练表示 vs. 传统进化特征"——对 TF–DNA 结合预测中特征工程的选择具有直接参考价值，尤其是对基于序列的 TF 结合预测器设计。

## 02 一句话总结
本文在 DBP 二分类任务上，用统一的平均化操作从 PSSM（PSI-BLAST 生成）和 ESM-1b（预训练语言模型）中提取特征，通过多种特征选择方法比较两者性能，发现 ESM 表示在公平比较下优于 PSSM，且基于软投票集成多个特征选择模型（FSEiDBP）可进一步提升分类性能。

## 03 研究问题
- **具体问题**：在 DNA-binding protein（DBP）识别任务中，alignment-based 的 PSSM 特征与基于预训练蛋白质语言模型（ESM-1b）的特征表示，在公平比较下孰优孰劣？
- **为什么重要**：PSSM 生成依赖 PSI-BLAST 对大型数据库（如 NCBI NR）的搜索，耗时且随数据库增长而加剧，限制了 DBP 预测器的可扩展性。预训练语言模型（如 ESM-1b）无需数据库搜索即可生成表示，若性能相当或更优，则可替代 PSSM，加速预测流程。
- **现有方法不足**：以往 DBP 预测研究几乎都依赖 PSSM 及其变体，鲜有研究系统评估预训练语言模型表示在 DBP 识别中的表现；且缺乏在统一特征提取和特征选择框架下的公平比较。
- **精确研究问题（Can...?）**：Can pretrained ESM-1b representations outperform alignment-based PSSM features for the identification of DNA-binding proteins under a unified feature extraction and feature selection framework?

## 04 背景与发展脉络
（标注：以下脉络为「经外部核验」——基于本文引言及引用文献，结合领域常识整理）

1. **早期实验方法**：滤膜结合实验、遗传分析、ChIP-chip、X 射线晶体学等，准确但昂贵耗时。
2. **序列/结构特征 + 机器学习**：结构特征（溶剂可及性、扭转角、接触图）性能高但受限于结构数据稀缺；序列特征（氨基酸组成、PseAAC、PSSM 变体）可扩展性好，其中 PSSM 因携带进化信息成为主流。
3. **PSSM 的瓶颈**：PSI-BLAST 搜索耗时随数据库膨胀而增加，限制大规模应用。
4. **蛋白质语言模型兴起**：ProtTrans、MSA Transformer、ESM-1b 等在大规模蛋白质序列上自监督预训练，学习到结构与功能信息，无需 MSA 即可预测接触图等。
5. **本文位置**：首次系统比较 PSSM 与 ESM-1b 在 DBP 识别中的表现，填补预训练表示在该任务上的评估空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PSSM 生成耗时 | PSI-BLAST 对长序列搜索 NCBI NR 数据库越来越慢 | 数据库序列数量持续增长，搜索成本上升 | Introduction 第 2 段："one run of the PSI-BLAST program on a long protein sequence is becoming more and more time-consuming due to the increasing number of sequences in the NCBI NR database" |
| 预训练表示在 DBP 任务上缺乏评估 | 以往 DBP 预测几乎全部依赖 PSSM，少有人关注 pLMs | 领域惯性，pLMs 主要应用于结构预测 | Introduction 第 3 段："Little attention by researchers has been paid to the application of pLMs to the identification of DBPs" |
| 特征维度高 | ESM-All 特征数达 37120，远超 PSSM 的 580 | ESM-1b 每残基 1280 维，平均化操作后仍高维 | Methods 2.3 节：ESM_All = 29 × 1280 = 37120 |
| 特征选择方法选择困难 | 不同 FS 方法性能差异大，需系统比较 | 缺乏统一框架下的 FS 方法评估 | Results 3.2 节：比较 6 种 FS 方法，LR/LinSVM 最优 |

## 05 核心思想
1. **表面方法**：用四种统一平均化操作（全残基平均、k-separation 平均、氨基酸类型平均、残基-残基相关）从 PSSM（20 维/残基）和 ESM-1b（1280 维/残基）中提取序列级特征，形成 6 个特征集（PSSMR_All、PSSMR_Avg、PSSMS_All、PSSMS_Avg、ESM_All、ESM_Avg），在 8 个分类器上比较，再用 6 种特征选择方法（3 种 filter + 3 种 embedded）筛选，最后用 RFECV 精炼，并集成 34 个模型。

2. **核心洞察**：
   - ESM-1b 表示在公平比较下（相同平均化操作、相同分类器、相同 FS 流程）一致优于 PSSM，说明预训练语言模型捕获的进化/结构信息比传统 MSA 衍生的 PSSM 更丰富。
   - 平均化操作本身对性能影响有限（ESM_Avg 与 ESM_All 差距小），说明 ESM 表示的信息密度高，简单池化即可获得强特征。
   - 集成多个 FS 模型（FSEiDBP）可显著提升性能，说明不同 FS 方法捕获互补信息。

3. **可能的普适教训** [Analysis]：
   - 在蛋白质功能预测任务中，预训练表示（如 ESM）可作为 PSSM 的即插即用替代品，尤其当计算资源有限或需要快速预测时。
   - 特征选择 + 集成的组合策略可有效缓解高维特征带来的过拟合风险，这一思路可迁移到 TF–DNA 结合位点预测中。

## 07 方法总览
- **输入**：蛋白质氨基酸序列（训练集 PDB1616，测试集 PDB186）
- **特征表示**：
  - PSSM：PSI-BLAST（3 次迭代，E-value 0.001）对 Swiss-Prot 和 RefSeq 数据库搜索，得到 PSSMS 和 PSSMR 两个 L×20 矩阵，sigmoid 归一化
  - ESM-1b：预训练 Transformer 模型，得到 L×1280 矩阵，sigmoid 归一化
- **特征提取**：四种平均化操作 → 6 个特征集（PSSMR_All、PSSMR_Avg、PSSMS_All、PSSMS_Avg、ESM_All、ESM_Avg）
- **分类器**：8 个基线分类器（GNB、KNN、DT、LR、SVM、RF、GBDT、XGB），默认参数
- **特征选择**：
  - 第一阶段：6 种重要性排序方法（variance、Chi2、MIC、LR、LinSVM、RF），取 top 10%-80%
  - 第二阶段：RFECV 精炼（仅对最优的 LR/LinSVM 排序结果）
- **集成**：FSEiDBP，软投票集成 34 个模型（32 个 FS 模型 + 2 个 NFS 模型）
- **评测**：5 折交叉验证（训练集）+ 独立测试集 PDB186；指标：ACC、MCC、SN、SP
- **流程**：序列 → 特征矩阵（PSSM/ESM）→ 平均化 → 特征集 → 分类器训练/FS → 模型评估 → 集成

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| PSSM 生成（PSI-BLAST） | 从 MSA 中提取进化保守性信息 | 传统 DBP 预测的黄金标准特征 | 输入：序列；输出：L×20 矩阵 | Results 表 2：PSSM 特征在 SVM 下 ACC 约 71-73% | 移除后失去进化信息，但可避免数据库搜索耗时 |
| ESM-1b 表示 | 从预训练语言模型中提取上下文相关残基表示 | 无需 MSA，捕获结构与功能信息 | 输入：序列；输出：L×1280 矩阵 | Results 表 2：ESM 特征在 SVM 下 ACC 约 78-79% | 移除后失去最强特征，性能显著下降 |
| 平均化操作（4 种） | 将变长残基级表示压缩为定长序列级特征 | 分类器需要定长输入 | 输入：L×d 矩阵；输出：d 或 29d 维向量 | Results 3.1：Avg 与 All 性能差距小（<1%） | 移除后无法获得序列级特征，但可尝试更复杂池化 |
| 重要性排序 FS（6 种） | 筛选 top 特征，降维 | 高维特征（尤其 ESM_All 37120 维）导致过拟合 | 输入：全特征集；输出：top k% 特征子集 | Results 3.2：LR/LinSVM 最优，filter 方法较差 | 移除后维度灾难，性能下降 |
| RFECW 精炼 | 递归消除最不重要特征，交叉验证选最优子集 | 进一步降维，提升泛化 | 输入：重要性排序特征子集；输出：精炼子集 | Results 3.3：RFECV 后性能小幅提升或持平 | 移除后特征冗余，可能轻微过拟合 |
| FSEiDBP 集成 | 软投票集成 34 个模型 | 综合不同 FS 方法的互补信息 | 输入：34 个模型的概率输出；输出：最终预测 | Results 3.4：ACC 从 80.65% 提升至 83.33% | 移除后性能下降约 2.7% ACC |

## 09 关键公式符号
1. **PSSM 矩阵**：PSSM = (s_{i,j})_{L×20}，其中 s_{i,j} 为第 i 个残基突变为第 j 种氨基酸的得分，L 为序列长度。归一化：sigmoid(PSSM)。

2. **全残基平均**（式 3）：
   AvgR = (1/L) Σ_{i=1}^{L} R_i
   其中 R_i ∈ R^d 为第 i 个残基的表示向量（d=20 或 1280），输出 d 维特征。

3. **k-separation 平均**（式 4）：
   AvgR_Sep_{k,s} = (1/N_{k,s}) Σ_{i=0}^{N_{k,s}-1} R_{ki+s}
   其中 k=2,3 为分离距离，s=1,...,k 为起始位置，N_{k,s} = ⌊(L-s+k)/k⌋ 为子集大小。输出 5d 维特征（k=2 的 2 个 + k=3 的 3 个）。

4. **氨基酸类型平均**（式 5）：
   AvgR_AA_t = (1/N_t) Σ_{A_i=t} R_i
   其中 t 为 20 种标准氨基酸之一，N_t 为类型 t 的残基数。输出 20d 维特征。

5. **残基-残基相关**（式 6）：
   AvgR_Corr_φ = (1/(L-φ)) Σ_{i=1}^{L-φ} (R_i - R_{i+φ}) ⊙ (R_i - R_{i+φ})
   其中 ⊙ 为逐元素乘法，φ=1,2,3 为序列距离。输出 3d 维特征。

6. **集成投票**（式 8）：
   p_c = Σ_{i=1}^{34} w_i p_{i,c}
   其中 w_i = ACC_i / (Σ_{k=1}^{34} ACC_k)，p_{i,c} 为第 i 个模型对类别 c（0=non-DBP，1=DBP）的预测概率。

## 10 实验设计与证据链
**数据集与评测协议**：
- 训练集：PDB1616（808 DBP + 808 non-DBP），从 PDB 搜索 "DNA binding protein" 关键词获取，CD-HIT 25% 序列一致性过滤
- 独立测试集：PDB186（93 DBP + 93 non-DBP），广泛使用的基准集
- 评测：5 折交叉验证（训练集）+ 独立测试集；指标：ACC、MCC、SN、SP
- 基线：8 个分类器（GNB、KNN、DT、LR、SVM、GBDT、RF、XGB），默认参数
- 特征集：6 个（PSSMR_All、PSSMR_Avg、PSSMS_All、PSSMS_Avg、ESM_All、ESM_Avg）
- FS 方法：6 种（variance、Chi2、MIC、LR、LinSVM、RF）+ RFECV
- 集成：FSEiDBP（34 个模型软投票）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|--------------|-------------------|------|
| 无 FS 的 6 特征集 × 8 分类器比较 | ESM 表示是否优于 PSSM | 相同分类器、相同平均化操作下比较 | ESM 特征在多数分类器上 ACC 高于 PSSM（如 SVM：ESM_All 78.9% vs PSSMR_All 71.47%） | ESM 表示在 DBP 识别中优于 PSSM | 未证明 ESM 在所有分类器/所有特征集上均最优 | Results 表 2 |
| 重要性排序 FS 比较 | 哪种 FS 方法最优 | 6 种 FS 方法在 4 个特征集上比较 | LR 和 LinSVM 最优，filter 方法（variance、Chi2、MIC）较差 | embedded 方法优于 filter 方法 | 未证明 LR 在所有情况下严格优于 LinSVM | Results 3.2、图 1 |
| ESM_All 低比例 FS 探索 | ESM_All 是否可用少量特征达到高性能 | top 1%-9% 特征 | LR 在 4% 特征时达到最高 ACC | ESM_All 可用约 4% 特征（约 1485 维）获得最优性能 | 未证明更低比例不可行 | Results 3.2、图 2 |
| RFECV 精炼 | RFECV 能否进一步提升性能 | 对 LR/LinSVM 最优子集执行 RFECV | 多数情况性能持平或小幅提升；ESM_All 的 LR4→LR4_RFE 有提升 | RFECV 可小幅优化，但提升有限 | 未证明 RFECV 总是有益（部分情况下降） | Results 3.3、表 4 |
| FSEiDBP 与 13 个现有预测器比较 | 集成模型是否优于现有方法 | 独立测试集 PDB186 | FSEiDBP 的 ACC 和 MCC 优于所有 13 个现有预测器（ACC 83.33%） | 集成策略有效 | 未证明 FSEiDBP 是 SOTA（作者自认非 SOTA） | Results 3.4、表 5 |

## 11 结论正确解读
- **任务范围**：仅限 DBP 二分类（是否结合 DNA），不涉及结合位点定位、结合亲和力预测或 TF 特异性。
- **特征比较的公平性**：比较在统一平均化操作和统一分类器下进行，但 PSSM 和 ESM 的维度差异大（580 vs 37120），FS 阶段可能对高维特征更有利。
- **Oracle/真值输入**：无 oracle 输入；标签来自 PDB 注释（"DNA binding protein" 关键词），可能存在注释噪声。
- **端到端状态**：非端到端；特征提取（PSSM/ESM）与分类器训练分离，ESM 表示未针对 DBP 任务微调。
- **算力成本**：ESM-1b 推理需要 GPU，但无需数据库搜索；PSSM 需要 PSI-BLAST 搜索，CPU 耗时随数据库增长。
- **历史数据依赖**：ESM-1b 在 2.5 亿条序列上预训练（截至 2020 年），PSSM 依赖 Swiss-Prot/RefSeq 2020 年 6 月版本。
- **模型依赖**：仅用 SVM（RBF 核）作为 FS 评估分类器，其他分类器（如深度学习）未测试。
- **最难情形**：未分析长序列、低复杂度序列或非球状蛋白等困难案例。
- **群体/领域边界**：训练集来自 PDB，偏向结构已知蛋白；对无结构注释的蛋白泛化性未验证。
- **有边界的复述**：在 PDB1616/PDB186 基准上，ESM-1b 表示在统一框架下优于 PSSM，且集成 FS 模型可进一步提升性能；但该结论限于 DBP 二分类任务，不适用于 TF–DNA 结合位点预测或亲和力预测。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 非 SOTA 模型 | 作者明确表示 FSEiDBP 不是 SOTA 预测器 | 设计更精细的特征提取操作或集成其他特征（如二级结构、溶剂可及性） | Conclusion 第 1 段："the proposed classification model of DBPs is not state-of-the-art" |
| 特征提取简单 | 仅用平均化操作，未设计更复杂的特征 | 设计更精细的特征提取操作 | Conclusion 第 1 段："designing much more delicate features" |
| 未整合其他特征类型 | 未加入二级结构、溶剂可及性等互补特征 | 整合其他类型特征 | Conclusion 第 1 段："integrating other types of features such as predicted secondary structure and solvent accessibility" |

**作者提及的相关约束**（非正式局限）：
- 训练集 PDB1616 与测试集 PDB186 均来自 PDB，可能存在分布偏移（PDB186 为广泛使用的基准，但两者序列一致性已通过 CD-HIT 25% 控制）。
- ESM-1b 特征维度高（37120），FS 阶段计算开销大。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| ESM 优于 PSSM 的结论可能受维度影响 | ESM_All 有 37120 维，PSSM_All 仅 580 维，FS 阶段高维特征有更多选择空间 | 若维度是主因，则低维 ESM 特征（如 ESM_Avg）与高维 PSSM 特征的比较更公平 | 用 PCA 将 ESM 降至 580 维再比较 | Results 表 2：ESM_Avg（1280 维）已优于 PSSM_All（580 维），部分缓解此担忧 |
| 分类器仅用默认参数 | SVM、RF 等未调参，可能低估某些特征集性能 | 不同特征集对超参数敏感度不同，默认参数可能偏向 ESM | 对每个特征集做超参数搜索 | Methods 2.4.4："we just utilize default parameters for all baseline classifiers" |
| 训练集与测试集同源（均来自 PDB） | PDB 注释的 "DNA binding protein" 可能不完整或有误，且测试集 PDB186 可能被其他方法反复使用导致过拟合 | 影响泛化性评估 | 用独立的新注释数据或跨物种验证 | Methods 2.1：训练集和测试集均来自 PDB |
| 集成模型增益可能来自模型多样性而非特征质量 | FSEiDBP 集成 34 个模型，增益可能来自投票平均而非 ESM 特征本身 | 无法分离特征质量与集成策略的贡献 | 用 PSSM 特征构建同等规模的集成模型对比 | Results 3.4：未报告 PSSM 集成的对照 |
| ESM-1b 预训练数据可能包含测试集同源序列 | ESM-1b 在 UniRef50 等数据库预训练，可能已见过 PDB186 中序列的同源物，造成信息泄漏 | 高估 ESM 表示的真实泛化能力 | 检查 ESM-1b 预训练数据与 PDB186 的序列重叠 | Methods 2.2.2：未讨论预训练数据与测试集重叠问题 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **预训练表示可替代 PSSM 的实证依据**：在 DBP 识别中，ESM-1b 表示在统一框架下优于 PSSM。可迁移到 TF–DNA 结合预测：用 ESM-2/ESM-C 等更新的模型替换 PSSM 作为序列特征，避免 PSI-BLAST 的耗时搜索。

2. **统一平均化框架**：四种平均化操作（全残基、k-separation、氨基酸类型、残基-残基相关）为比较不同表示提供了公平框架。可迁移到 TF 结合位点预测：对 TF 结合区域（如 ChIP-seq peak 序列）用相同池化操作提取 ESM 特征，便于与 PSSM 基线公平比较。

3. **FS + 集成策略**：重要性排序 FS（LR/LinSVM）配合 RFECV 精炼，再软投票集成，可显著提升性能。可迁移到 TF–DNA 结合预测：高维 ESM 特征下，先用 embedded FS 降维，再集成多个模型，可缓解过拟合。

4. **ESM_Avg 的性价比**：ESM_Avg（1280 维）与 ESM_All（37120 维）性能差距小（<1%），说明简单平均池化已捕获大部分信息。可迁移到 TF 结合预测：优先使用 ESM_Avg 而非全特征，降低计算成本。

5. **特征选择方法选择建议**：embedded 方法（LR、LinSVM）优于 filter 方法（variance、Chi2、MIC）。可迁移到 TF–DNA 结合预测：优先用线性模型系数作为特征重要性排序，而非统计检验。

6. **集成权重设计**：软投票按 5 折 CV 的 ACC 加权，简单有效。可迁移到 TF 结合预测：集成多个 FS 模型时，用验证集性能作为权重。

## 15 与已有知识连接
- **PSSM 在 DBP 预测中的主导地位**：本文引用的先前工作（Zhang et al. [9]、Zou et al. [10]、Hu et al. [15] 等）均以 PSSM 为核心特征，本文是对这一范式的直接挑战。可连接至 TF–DNA 结合预测中广泛使用的 PSSM 类特征（如 TRANSFAC 位置权重矩阵）。
- **ESM-1b 的提出**：Rives et al. [35] 的 ESM-1b 是本文预训练表示的基础。该模型在结构预测（contact map）上已证明无需 MSA 即可超越传统方法，本文将其推广到 DBP 识别。
- **蛋白质语言模型家族**：ProtTrans [33]、MSA Transformer [34] 与 ESM-1b 同属预训练蛋白质语言模型，本文仅用 ESM-1b，未比较其他 pLMs。可连接至 TF–DNA 结合预测中 ProtT5、ESM-2 等更新的表示。
- **特征选择在生物信息学中的应用**：本文使用的 filter/embedded/wrapper FS 框架与蛋白质功能预测中的标准实践一致。可连接至 TF 结合预测中常用的 mRMR、LASSO 等特征选择方法。
- **DBP 预测基准**：PDB186 是广泛使用的独立测试集（本文引用 [1, 38–43]），可连接至 TF–DNA 结合预测中的公共基准（如 ChIP-seq 数据集）。
- **[Analysis] 与 TF–DNA 结合机制的联系**：本文的 DBP 二分类是 TF–DNA 结合预测的粗粒度版本。TF 特异性结合预测（如 motif 识别、结合亲和力回归）可借鉴本文的"预训练表示 vs. PSSM"比较框架，但需注意 TF 结合更依赖局部序列上下文，平均化操作可能丢失关键位置信息。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合位点预测中 ESM-2 与 PSSM 特征的公平比较
   - **来源局限/观察**：本文仅比较 ESM-1b 与 PSSM 在 DBP 二分类上的表现，未涉及 TF 特异性结合位点定位；且 ESM-1b 已被 ESM-2 等更新模型超越。
   - **核心假设**：在 TF–DNA 结合位点预测（如 ChIP-seq peak 分类）中，ESM-2 表示优于 PSSM，且对低序列相似性 TF 泛化更好。
   - **初步方法**：用统一平均化框架从 ESM-2 和 PSSM 提取特征，在多个 TF 的 ChIP-seq 数据集上比较；加入位置权重矩阵（PWM）特征作为互补。
   - **验证方式**：独立测试集上的 AUC、PR-AUC；跨 TF 交叉验证。
   - **创新状态**：unverified

2. **候选名称**：基于 ESM 表示和注意力机制的 TF 结合 motif 发现
   - **来源局限/观察**：本文的平均化操作丢失了残基位置信息，而 TF 结合高度依赖特定位置（motif）。
   - **核心假设**：ESM 的残基级表示结合注意力权重可定位 TF 结合的关键残基，优于传统 PWM 扫描。
   - **初步方法**：用 ESM-2 提取残基级表示，训练注意力模型预测结合位点，注意力权重作为 motif 重要性分数。
   - **验证方式**：与 MEME、HOMER 等 motif 发现工具比较，用已知 motif 数据库（JASPAR）评估。
   - **创新状态**：unverified

3. **候选名称**：TF–DNA 结合亲和力预测的预训练表示与物理特征融合
   - **来源局限/观察**：本文仅用序列特征，未结合结构信息；TF–DNA 结合亲和力受三维结构影响。
   - **核心假设**：ESM 表示与物理化学特征（如氢键、疏水作用）融合可提升结合亲和力预测精度。
   - **初步方法**：对 TF–DNA 复合物提取 ESM 表示 + 结构特征（如 Rosetta 能量项），训练回归模型预测结合亲和力。
   - **验证方式**：在公开亲和力数据集（如 Protein-DNA 结合亲和力数据库）上比较。
   - **创新状态**：unverified

4. **候选名称**：基于 ESM 表示和对比学习的 TF 结合特异性预测
   - **来源局限/观察**：本文的 FS 方法仅用监督信息，未利用大规模无标注序列；TF 结合特异性可从序列上下文中学习。
   - **核心假设**：对比学习预训练的 ESM 表示可捕获 TF 结合特异性，优于有监督 FS 特征。
   - **初步方法**：用 ESM-2 的对比学习变体提取表示，在 TF 结合位点预测任务上微调。
   - **验证方式**：与本文的 FS 方法在相同基准上比较。
   - **创新状态**：unverified

5. **候选名称**：TF–DNA 结合预测中 PSSM 与 ESM 特征的互补性分析
   - **来源局限/观察**：本文发现 ESM 优于 PSSM，但未分析两者是否互补。
   - **核心假设**：PSSM 捕获的进化保守性与 ESM 捕获的上下文信息互补，融合可进一步提升性能。
   - **初步方法**：将 PSSM 和 ESM 特征拼接或双通道输入，比较融合与单独使用的性能。
   - **验证方式**：在 PDB1616/PDB186 及 TF 特异性数据集上比较。
   - **创新状态**：unverified