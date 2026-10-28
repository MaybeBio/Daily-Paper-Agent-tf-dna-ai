## 01 基本信息
- **标题**：DRBpred: A sequence-based machine learning method to effectively predict DNA- and RNA-binding residues
- **作者与单位**：Kabir, Md Wasi Ul; Alawad, Duaa Mohammad; Pokhrel, Pujan; Hoque, Md Tamjidul（单位未在摘要中提供，推测为 University of New Orleans，因 webserver 域名为 bmll.cs.uno.edu）
- **期刊/预印本平台**：Computers in Biology and Medicine
- **年份**：2024-02-01
- **论文类型**：方法学（method）论文，提出新的预测工具
- **领域**：生物信息学；蛋白质-核酸互作（DNA/RNA-binding residue 预测）
- **关键词**：DNA-binding residues; RNA-binding residues; LightGBM; PSSM; HMM; SHAP; sequence-based prediction
- **DOI/arXiv 号**：10.1016/j.compbiomed.2024.108081
- **代码**：https://github.com/wasicse/DRBpred
- **数据**：https://bmll.cs.uno.edu（webserver）；数据集源自 DRNApred [15] 的处理流程
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「蛋白质-DNA 互作（TF–DNA 结合机制）× AI 方法」中的**序列-based 残基级预测**分支。与结构-based 方法（MD/对接）互补，不依赖实验结构，直接以序列特征（PSSM、HMM、理化性质等）预测 DNA/RNA 结合残基。对 TF–DNA 结合机制研究的价值在于：提供了一种可迁移的残基级结合位点预测框架，可用于识别 TF 蛋白序列上的 DNA 结合残基（如 DNA-binding domain 的关键残基），且不依赖 3D 结构。

## 02 一句话总结
本文提出 DRBpred，一种基于序列的 LightGBM 分类器，利用 PSSM、HMM、理化性质、结构性质、扭转角、无序区等 119 维特征（经 SHAP-RFE 特征选择后保留 96 维）和滑动窗口上下文，在 DRNApred 数据集上预测 DNA/RNA 结合残基，相比 SOTA 方法 DRNApred 在 DNA 测试集上 Sensitivity 提升 112.00%、MCC 提升 33.33%、AUC 提升 6.49%，在 RNA 测试集上分别提升 112.50%、16.67%、7.46%。

## 03 研究问题
- **具体问题**：仅从蛋白质序列（无实验 3D 结构）出发，如何准确预测 DNA-binding 和 RNA-binding 残基？
- **为什么重要**：DNA/RNA 结合蛋白在 DNA 复制、转录、修复、基因表达调控及 RNA 代谢中起核心作用。实验方法（NMR、X-ray、ChIP-chip）耗时费力，且许多蛋白无实验结构。计算预测可大规模注释结合残基，辅助理解 TF–DNA 互作机制、致病突变解读和药物设计。
- **现有方法不足**：
  - 依赖 3D 结构的方法（如 [9, 10]）受限于实验结构数量稀少；
  - 已有序列-based 方法（如 DRNApred、BindN+、RNABindR、Pprint）性能有限，Sensitivity 和 MCC 较低；
  - 深度学习方法（如 EL-LSTM [25]）虽有效，但可解释性差、训练成本高。
- **精确研究问题（Can...?）**：Can a sequence-based machine learning method, using evolutionary (PSSM, HMM) and physicochemical features with sliding window context and optimized LightGBM, achieve higher Sensitivity, MCC, and AUC than existing state-of-the-art methods (e.g., DRNApred) for DNA- and RNA-binding residue prediction?

## 04 背景与发展脉络
*注：以下脉络基于本文 Related Work 及引用，标注为「经外部核验」的部分仅指文中明确引用的文献；整体脉络为「仅本文框架」。*

| 阶段 | 代表方法 | 优点 | 局限 | 本文主张的位置 |
|---|---|---|---|---|
| 早期序列特征 | Ahmad et al. [9] | 仅用序列特征，简单 | 精度有限 | 本文在其基础上扩展特征类型 |
| SVM-based | Cai & Lin [11], Zou et al. [12], BindN+ [17] | 引入理化性质、PSSM | 特征单一，SVM 对大规模数据扩展性差 | 本文用 LightGBM 替代 SVM |
| 随机森林 | Lou et al. [13], DNA-Prot [14] | 集成学习，鲁棒性提升 | 特征工程依赖人工，性能仍有提升空间 | 本文用 Boosting 替代 Bagging |
| 结构-based | PDRLGB [9]（依赖 DSSP 结构特征） | 结构信息丰富 | 依赖实验 3D 结构，覆盖有限 | 本文完全序列-based，不依赖结构 |
| 深度学习方法 | EL-LSTM [25] | 自动特征学习，性能强 | 可解释性差，训练成本高 | 本文用可解释的树模型 + SHAP |
| 本文 | **DRBpred** | 序列-only、特征丰富（119维）、SHAP-RFE 特征选择、LightGBM 优化、可解释 | 依赖 DRNApred 数据集，特征提取计算成本高 | 在 DRNApred 数据集上超越 SOTA |

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 实验结构稀缺 | 大量 DNA/RNA 结合蛋白无实验 3D 结构，结构-based 方法无法应用 | 实验方法（NMR、X-ray）耗时费力 | Introduction 节："the number of experimentally derived structures (DNA and RNA complexes) is limited" |
| 已有序列方法性能低 | DRNApred 等 SOTA 在 Sensitivity 和 MCC 上表现不佳 | 特征类型不足、分类器未优化 | Results 节表 4、5：本文相比 DRNApred 在 Sensitivity 上提升 >112% |
| 特征提取计算成本高 | PSSM、HMM 等特征计算耗时 | 需要 PSI-BLAST 多轮迭代、HMMER 搜索 | Conclusions 节："feature extraction is computationally expensive"（作者明确承认） |
| 数据不平衡 | 结合残基远少于非结合残基，模型易偏向多数类 | 蛋白质序列中结合位点稀疏 | 作者选择 Sensitivity、MCC、AUC 而非 Accuracy 作为主要指标（Results 节） |
| 可解释性不足 | 深度学习方法（如 EL-LSTM）难以解释预测依据 | 黑箱模型 | 本文引入 SHAP 和 LIME 进行特征解释（Case Study 节） |

## 06 核心思想
1. **表面方法**：提取 119 维序列特征（氨基酸组成、PSSM、HMM、理化性质、结构性质、扭转角、无序区），用滑动窗口（最优窗口 11）融合邻域信息，经 SHAP-RFE 特征选择保留 96 维，训练 LightGBM 分类器，分别预测 DNA- 和 RNA-binding 残基。
2. **核心洞察**：
   - **进化信息是关键**：PSSM 和 HMM 特征在 SHAP 重要性排序中占据主导地位（Figures 3、4），说明保守性强的残基更可能参与核酸结合。
   - **邻域上下文重要**：滑动窗口显著提升性能（窗口 11 最优），说明结合残基的判定依赖其局部序列环境。
   - **可解释性可落地**：SHAP 不仅用于特征选择，还用于解释单个预测，LIME 进一步提供局部解释，使模型从"黑箱"变为可审计工具。
3. **可能的普适教训 [Analysis]**：
   - 对于残基级预测任务，**进化特征（PSSM/HMM）+ 邻域上下文 + 树模型**的组合在数据量中等时往往优于深度学习方法，且可解释性更强。
   - **特征选择（SHAP-RFE）** 在特征维度高时能有效去噪，提升泛化能力。
   - 对不平衡数据，**Sensitivity + MCC + AUC** 比 Accuracy 更能反映真实性能。

## 07 方法总览
- **输入**：蛋白质氨基酸序列（仅序列，无结构）
- **输出**：每个残基的 DNA-binding / RNA-binding 二分类标签（0/1）
- **特征提取模块**：
  - 氨基酸组成（20 维 one-hot）
  - PSSM（20 维，PSI-BLAST 生成）
  - HMM profile（30 维，HMMER 生成）
  - 理化性质（7 维，来自 AAindex）
  - 结构性质（预测的二级结构 SS 概率、可及表面积 ASA）
  - 扭转角（Φ/Ψ 波动）
  - 无序区概率
  - 总计 119 维/残基
- **上下文融合**：滑动窗口（1~19 搜索，最优 11），将窗口内所有残基的特征拼接
- **特征选择**：SHAP 重要性 + 递归特征消除（RFE），119 → 96 维
- **分类器**：LightGBM（梯度提升树），超参数经 Optuna 优化（n_estimators, learning_rate, num_leaves, max_depth, min_child_samples, max_bin, subsample, subsample_freq, colsample_bytree）
- **训练**：10 折交叉验证（训练集），独立测试集评估
- **解释**：SHAP 全局特征重要性 + LIME 局部解释
- **流程**：序列 → 特征提取（含窗口）→ SHAP-RFE 特征选择 → LightGBM 训练 → 预测 → SHAP/LIME 解释

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 特征提取（119维） | 编码残基的进化、理化、结构、无序信息 | 单一特征类型不足以刻画结合位点 | 输入：序列；输出：119维向量/残基 | Figures 3、4 显示多类特征均有贡献 | 预期性能下降（未做消融实验，[Analysis] 推测） |
| 滑动窗口（窗口=11） | 融合邻域残基信息 | 结合残基的判定依赖局部序列上下文 | 输入：单残基特征；输出：96×11=1056维向量 | Figures 12、13 显示窗口 11 最优 | 窗口=1 时性能显著下降（作者未明确量化，[Analysis] 推测） |
| SHAP-RFE 特征选择 | 筛选最重要的 96 个特征 | 去除冗余特征，提升泛化、降低过拟合 | 输入：119维特征；输出：96维子集 | Figures 5、6 展示选择结果 | 预期性能略降或持平，但模型更简洁（未做消融，[Analysis] 推测） |
| LightGBM 分类器 | 二分类预测结合/非结合 | 梯度提升树对表格数据性能强、训练快 | 输入：特征向量；输出：结合概率 | Figures 7、8 显示 LightGBM 优于其他 6 种方法 | 替换为 SVM/RF 时性能下降（Figures 7、8 实测） |
| Optuna 超参数优化 | 自动搜索最优超参数 | 默认参数非最优，手动调参效率低 | 输入：超参数空间；输出：最优参数 | Table 2 列出最终参数 | 预期性能略降（未做对照，[Analysis] 推测） |
| SHAP 解释 | 全局特征重要性排序 | 理解模型决策依据，识别关键特征 | 输入：训练模型+数据；输出：重要性分数 | Figures 3、4 | 不影响预测性能，仅用于解释 |
| LIME 解释 | 单样本局部解释 | 审计单个预测的可信度 | 输入：单样本；输出：局部特征贡献 | Case Study 节 Figures 18、19 | 不影响预测性能，仅用于解释 |

## 09 关键公式符号
本文核心公式为评估指标，无复杂数学模型：

1. **Sensitivity / Recall**：
   \[
   \text{Sensitivity} = \frac{TP}{TP + FN}
   \]
   - TP：正确预测的结合残基数（true positives）
   - FN：漏检的结合残基数（false negatives）

2. **Matthews Correlation Coefficient (MCC)**：
   \[
   \text{MCC} = \frac{TP \times TN - FN \times FP}{\sqrt{(TP+FN)(TP+FP)(TN+FP)(TN+FN)}}
   \]
   - TN：正确预测的非结合残基数（true negatives）
   - FP：误报的非结合残基数（false positives）

3. **AUC (Area Under ROC Curve)**：未给出公式，为标准 ROC 曲线下面积。

*注：特征提取中的 PSSM、HMM、AAindex 等均为标准生物信息学编码，文中未给出具体公式。*

## 10 实验设计与证据链
**数据集**：
- 来源：DRNApred [15] 处理后的数据集
- 原始数据：564 个蛋白-DNA、72 个蛋白-RNA、16 个蛋白-DNA-RNA 复合物（分辨率 < 2.5Å）
- 扩充后：2827 个 DNA-binding 链、1125 个 RNA-binding 链
- 测试集：独立测试集（与训练集序列相似性 < 30%）
- 标注：结合残基定义基于复合物结构中与 DNA/RNA 原子距离 < 某阈值（具体阈值文中未明确，[Analysis] 推测为 0.5Å 或类似标准）

**指标**：Sensitivity、MCC、AUC（针对不平衡数据选择）

**基线/对比方法**：DRNApred、Pprint、RNABindR、BindN+（结果取自 DRNApred 论文 [15]）

**评测协议**：训练集 10 折交叉验证 + 独立测试集评估

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 7 种 ML 方法比较 | LightGBM 优于其他分类器 | 相同特征+窗口，对比 SVM、RF、KNN 等 | LightGBM 在 AUC/Recall/MCC 上最优 | LightGBM 适合该任务 | 未与其他 boosting 变体（如 XGBoost）对比 | Figures 7、8 |
| 窗口大小搜索 | 窗口 11 最优 | 窗口 1~19 扫描 | DNA 和 RNA 均在窗口 11 达到最优 | 邻域上下文重要 | 未测试窗口 >19 | Figures 12、13 |
| 与 SOTA 对比（DNA） | DRBpred 优于 DRNApred | 独立测试集 | Sensitivity 提升 112.00%，MCC 提升 33.33%，AUC 提升 6.49% | DRBpred 在 DNA 预测上显著优于 SOTA | 未报告 Precision/F1 的对比 | Table 5、Figure 15 |
| 与 SOTA 对比（RNA） | DRBpred 优于 DRNApred | 独立测试集 | Sensitivity 提升 112.50%，MCC 提升 16.67%，AUC 提升 7.46% | DRBpred 在 RNA 预测上显著优于 SOTA | 未报告 Precision/F1 的对比 | Table 4、Figure 14 |
| 5 折交叉验证 | 模型稳定性 | 训练集 5 折 | ROC-AUC 约 0.91，各折间低方差 | 模型稳定、未过拟合 | 未报告测试集上的方差 | Figures 9、10 |
| LIME 案例研究 | 模型可解释性 | 随机选取测试样本 | 高 ASA、特定 HMM profile 特征贡献最大 | 模型决策可审计 | 仅 2 个案例，不具统计意义 | Case Study 节 |

## 11 结论正确解读
- **任务范围**：仅限**序列-based 残基级二分类**（结合/非结合），不预测结合强度、不区分结合模式（如 minor/major groove）、不预测蛋白-level 是否结合。
- **Oracle/真值输入**：训练标签来自实验复合物结构（X-ray/NMR），依赖结构质量（<2.5Å）。测试集标签同样来自结构注释。
- **端到端状态**：**非端到端**。特征提取依赖外部工具（PSI-BLAST、HMMER、DisPredict2、SPOT-Disorder2），这些工具本身有误差，会传播到最终预测。
- **算力成本**：特征提取阶段计算量大（PSI-BLAST 多轮搜索），但训练阶段 LightGBM 高效。作者明确承认特征提取耗时。
- **历史数据依赖**：训练数据来自 PDB 中已解析的复合物，存在**结构覆盖偏差**——高分辨率复合物偏向特定蛋白家族（如转录因子、核酸酶），对未解析家族泛化能力未知。
- **模型依赖**：仅用 LightGBM，未与其他 SOTA 深度学习方法（如 EL-LSTM）在同一数据集上直接对比。
- **最难情形**：低 ASA 残基、无序区域内的结合残基、非标准结合模式（如 RNA 结合中的碱基特异性识别）。
- **群体/领域边界**：适用于球蛋白、可溶性蛋白；对膜蛋白、 intrinsically disordered proteins（IDPs）的适用性未验证。
- **不确定性**：未报告预测的置信区间或概率校准。

**有边界的复述**：DRBpred 在 DRNApred 数据集上，以序列为输入，通过 119 维特征 + 窗口 11 + LightGBM，在 Sensitivity、MCC、AUC 上超越 DRNApred 等基线，但该结论仅适用于该数据集、该特征组合、该分类器，且依赖外部特征提取工具的准确性。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 特征提取计算成本高 | PSSM、HMM 等特征计算耗时，依赖 PSI-BLAST 等外部工具 | 计划采用并行处理（多 CPU）加速 | Conclusions 节 |
| 依赖外部工具 | 特征提取依赖 DisPredict2、SPOT-Disorder2 等程序 | 未明确提及 | Conclusions 节（隐含） |
| 未利用 3D 结构信息 | 当前为序列-only 方法 | 计划在未来工作中整合预测的 3D 结构信息 | Conclusions 节 |
| 未使用大语言模型（LLM） | 当前用传统特征工程 | 计划探索 LLM 提取特征以提升精度 | Conclusions 节 |

*注：作者未明确讨论数据偏差、跨数据集泛化、类别不平衡处理等潜在局限。*

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 对比基线结果取自 DRNApred 论文 [15]，而非复现 | 基线方法可能在不同硬件/实现下表现不同，对比不公平 | 性能提升可能部分来自实验设置差异而非方法优势 | 在相同数据划分下复现 DRNApred、BindN+ 等方法 | Results 节："results of these state-of-the-art methods were gathered from the DRNApred paper" |
| 未报告 Precision、F1-score 的对比 | Sensitivity 大幅提升可能以 Precision 下降为代价 | 对实际应用（如突变注释），假阳性率同样关键 | 补充 Precision、F1、Specificity 的对比表 | Table 4、5 仅报告 Sensitivity、MCC、AUC |
| 特征选择（119→96）的增益未量化 | 未对比"全特征" vs "96维特征"的性能差异 | 无法判断特征选择是否真正有效，还是仅简化模型 | 做消融实验：全特征 vs 选择后特征 | Methods 节描述 SHAP-RFE，但无消融数据 |
| 窗口大小搜索仅到 19 | 更大窗口可能进一步提升性能，但计算成本增加 | 最优窗口可能未找到 | 测试窗口 21、23、25 | Figures 12、13 仅展示 1~19 |
| 未与深度学习方法（EL-LSTM 等）直接对比 | 深度学习方法可能在相同数据集上表现更好 | 无法判断树模型 vs 深度学习的优劣 | 在相同数据划分下实现 EL-LSTM 等对比 | Related Work 提及 EL-LSTM，但 Results 未对比 |
| 数据集来自 DRNApred，存在结构偏差 | 高分辨率复合物偏向特定蛋白家族，泛化性存疑 | 对 TF–DNA 互作研究，若训练集缺乏特定 TF 家族，预测可能失效 | 在独立 TF 数据集（如 CIS-BP）上验证 | Dataset 节描述数据来源 |
| LIME 分析仅 2 个案例 | 样本量过小，无法得出统计结论 | 可解释性结论可能不具代表性 | 在更多样本上系统评估 LIME 解释 | Case Study 节仅展示 2 个案例 |
| 未报告类别不平衡处理细节 | 结合残基远少于非结合残基，模型可能偏向多数类 | 影响 Sensitivity 和 MCC 的可信度 | 检查训练集正负样本比例、是否用 class weight 等 | Methods 节未提及不平衡处理 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **特征组合策略**：PSSM + HMM + 理化性质 + 预测结构特征（SS/ASA）+ 无序区 + 扭转角的多源特征融合，是残基级预测任务的有效范式。可迁移到 TF–DNA 结合机制研究：对 TF 蛋白序列，用同样特征组合预测 DNA 结合残基，可快速定位 DNA-binding domain 关键残基。

2. **滑动窗口的邻域建模**：窗口 11 最优说明结合残基的判定依赖 ±5 残基的上下文。对 TF–DNA 互作，可进一步分析窗口内残基的序列偏好（如富集碱性残基 Arg/Lys），揭示结合 motif。

3. **SHAP-RFE 特征选择**：先用 SHAP 重要性排序，再用 RFE 递归消除，可有效降维并提升泛化。对 TF–DNA 研究，SHAP 重要性排序可识别**决定结合特异性的关键特征**（如特定位置的 PSSM 得分），为突变功能预测提供依据。

4. **树模型 + 可解释性**：LightGBM 在中等规模表格数据上可达到接近深度学习的性能，且 SHAP/LIME 提供局部解释。对 TF–DNA 机制研究，可用 SHAP 分析单个 TF 突变体预测变化，辅助理解突变如何影响 DNA 结合。

5. **不平衡数据的评估指标**：选择 Sensitivity、MCC、AUC 而非 Accuracy，是处理结合/非结合残基比例失衡的正确做法。TF–DNA 研究中同样适用。

6. **可迁移到物理模拟的接口**：预测的结合残基可作为 MD 模拟或分子对接的**初始结合位点假设**，缩小搜索空间。例如，先用 DRBpred 预测 TF 的 DNA 结合残基，再用这些残基引导蛋白-DNA 对接。

7. **方法局限的启示**：特征提取计算成本高、依赖外部工具，提示在构建 TF–DNA 预测流程时需考虑端到端方案或轻量特征。

## 15 与已有知识连接
- **DRNApred [15]**：本文数据集和对比基线直接来自 DRNApred。DRNApred 是区分 DNA/RNA 结合蛋白和残基的早期方法，本文在其数据集上改进。可延伸阅读 DRNApred 原文了解数据构建细节。
- **BindN+ [17]**：基于 SVM 的 DNA/RNA 结合残基预测方法，本文对比基线之一。BindN+ 使用 PSSM 和理化性质，本文扩展了特征类型。
- **Pprint [相关文献]**：基于序列的蛋白-核酸结合位点预测，本文对比基线。
- **RNABindR [相关文献]**：RNA 结合残基预测方法，本文对比基线。
- **LightGBM [53]**：梯度提升树框架，本文核心分类器。LightGBM 在生物信息学表格任务中广泛使用。
- **SHAP [52]**：基于博弈论的特征解释方法，本文用于特征选择和解释。SHAP 在可解释 AI 中为标准工具。
- **Optuna [53]**：超参数优化框架，本文用于 LightGBM 调参。
- **DisPredict2 [35]、SPOT-Disorder2 [41]**：分别提供 ASA/SS 预测和无序区预测，本文特征来源工具。
- **与 TF–DNA 互作机制的联系**：本文方法可直接应用于 TF 蛋白的 DNA 结合残基预测。已知 TF 的 DNA-binding domain（如 helix-turn-helix、zinc finger、bZIP）中，关键残基通常具有高 PSSM 保守性和特定理化性质（如正电荷残基与 DNA 磷酸骨架的静电互作）。DRBpred 的特征组合恰好覆盖这些维度，可作为 TF 结合位点注释的补充工具。
- **与结构生物学方法的衔接**：本文是纯序列方法，与 MD 模拟、分子对接互补。预测的结合残基可作为 MD 模拟的初始接触残基，或用于验证对接构象的合理性。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF-DNA 结合特异性的可解释预测：基于 DRBpred 框架的 TF 家族迁移学习
   - **来源局限/观察**：DRBpred 在通用 DNA 结合蛋白上训练，未针对 TF 家族优化；TF 的 DNA 结合域具有家族特异性（如 bZIP 的碱性区、锌指的 α-helix）。
   - **核心假设**：在 TF 家族数据上微调 DRBpred 可提升家族内预测精度，且 SHAP 可揭示家族特异的结合决定残基。
   - **初步方法**：收集 CIS-BP 或 TRANSFAC 中 TF-DNA 复合物结构，按家族划分训练/测试；用 DRBpred 预训练权重初始化，在 TF 家族数据上微调；用 SHAP 分析家族特异的特征贡献。
   - **验证方式**：与 DRBpred 原版、DRNApred 对比 Sensitivity/MCC/AUC；用已知 TF 突变体（如 p53 癌症突变）验证预测残基的生物学意义。
   - **创新状态**：unverified

2. **候选名称**：结合 DRBpred 预测与 MD 模拟的 TF-DNA 结合残基验证管道
   - **来源局限/观察**：DRBpred 预测无结构验证；MD 模拟可验证残基-碱基互作的物理合理性。
   - **核心假设**：DRBpred 预测的高置信结合残基在 MD 模拟中与 DNA 碱基/磷酸骨架形成稳定接触（氢键、盐桥）。
   - **初步方法**：对目标 TF，用 DRBpred 预测结合残基；选取高置信残基作为 MD 模拟的初始接触位点；用 GROMACS/AMBER 模拟 TF-DNA 复合物，分析接触残基的互作能量和占有率。
   - **验证方式**：预测残基与 MD 模拟接触残基的重合率；与已知实验突变数据对比。
   - **创新状态**：unverified

3. **候选名称**：基于 DRBpred 特征重要性的 TF 结合域突变效应预测
   - **来源局限/观察**：DRBpred 的 SHAP 重要性显示 ASA 和 HMM profile 是关键特征；TF 突变（如癌症相关突变）常改变结合亲和力。
   - **核心假设**：SHAP 特征贡献变化可预测突变对 DNA 结合的影响方向（增强/减弱）。
   - **初步方法**：对 TF 的每个残基，计算 SHAP 贡献；引入点突变，重新计算 SHAP 贡献变化；用实验结合亲和力数据（如 PBMs）验证。
   - **验证方式**：预测的突变效应与实验 ΔΔG 或 PBM 信号变化的相关性。
   - **创新状态**：unverified

4. **候选名称**：结合 DRBpred 与 AlphaFold 结构的 TF-DNA 结合位点预测增强
   - **来源局限/观察**：DRBpred 使用预测的 SS/ASA 特征，但未利用 AlphaFold 预测的 3D 结构；AlphaFold 结构可提供更准确的 ASA 和接触信息。
   - **核心假设**：用 AlphaFold 结构替换预测特征，可提升 DRBpred 在无实验结构 TF 上的预测精度。
   - **初步方法**：对测试 TF，用 AlphaFold 生成结构，计算 ASA、SS、扭转角等特征；与 DRBpred 原特征对比，评估性能差异。
   - **验证方式**：在 DRNApred 测试集和独立 TF 数据集上对比 Sensitivity/MCC/AUC。
   - **创新状态**：unverified

5. **候选名称**：DNA 与 RNA 结合残基的差异特征分析：DRBpred 的跨类型迁移
   - **来源局限/观察**：DRBpred 分别训练 DNA 和 RNA 模型，但未分析两类结合残基的特征差异；TF 通常特异性结合 DNA，但部分蛋白可结合 RNA。
   - **核心假设**：DNA 和 RNA 结合残基在理化性质（如电荷、疏水性）和进化保守性上存在可区分的特征模式。
   - **初步方法**：用 SHAP 对比 DNA 和 RNA 模型的特征重要性；训练一个联合模型，输出 DNA/RNA 结合双标签；分析误分类样本的特征模式。
   - **验证方式**：双标签模型的 AUC 和 MCC；特征差异的统计显著性检验。
   - **创新状态**：unverified