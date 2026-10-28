## 01 基本信息
- **标题**：Prediction of mammalian tissue-specific CLOCK-BMAL1 binding to E-box DNA motifs
- **作者与单位**：Marri, Daniel; Filipovic, David; Kana, Omar; Tischkau, Shelley; Bhattacharya, Sudin（单位未在摘要中提供）
- **期刊/预印本平台**：Scientific Reports
- **年份**：2023
- **论文类型**：研究论文（Research Article）
- **领域**：计算生物学 / 生物信息学 / 转录因子-DNA 互作 / 昼夜节律
- **关键词**：BMAL1, CLOCK, E-box, 转录因子结合位点预测, 机器学习, DNA shape, 组蛋白修饰
- **DOI/arXiv 号**：10.1038/s41598-023-34115-w
- **代码**：未提供
- **数据**：GEO accession GSE11060（BMAL1 ChIP-seq）；ENCODE（DNase-seq、组蛋白修饰 ChIP-seq）
- **阅读日期**：未提供
- **在该方向中的位置**：本文属于「TF–DNA 结合机制 × 机器学习」方向，聚焦哺乳动物昼夜节律核心转录因子 CLOCK–BMAL1 的组织特异性 E-box 结合预测。与纯序列 motif 扫描方法不同，本文引入 DNA shape 与组蛋白修饰特征，构建可解释的 XGBoost 模型，并揭示组织特异性结合的决定因素。对 TF–DNA 互作课题的可迁移点在于：将 DNA 三维结构特征（shape）与表观遗传特征（histone marks）纳入预测框架，并利用可解释性方法（ELI5 permutation importance）解析结合机制。

## 02 一句话总结
本文使用 XGBoost 机器学习模型，以 DNA 序列、DNA shape 和组蛋白修饰为特征，预测小鼠肝、肾、心中 CLOCK–BMAL1 对 E-box motif 的结合状态，发现 DNA shape（尤其是 EP、Roll、MGW）和组蛋白修饰（H3K27ac、H3K4me3）是组织特异性结合的关键预测因子，且肝中 E-box 上游第二位点的 G 核苷酸对结合预测贡献最大。

## 03 研究问题
- **具体问题**：在哺乳动物不同组织（肝、肾、心）中，哪些基因组特征（序列、DNA shape、组蛋白修饰）能够预测 CLOCK–BMAL1 对 E-box motif 的结合？这些特征的贡献是否具有组织特异性？
- **为什么重要**：CLOCK–BMAL1 是哺乳动物昼夜节律的核心调控因子，其结合位点的组织特异性决定了节律基因表达的差异。理解其结合机制有助于揭示昼夜节律调控的分子基础及相关疾病（如代谢疾病、癌症）的发病机制。
- **现有方法不足**：传统 motif 扫描方法（如仅基于序列的 PWM）无法解释为何基因组中大量 E-box 中只有少数被结合；深度学习方法虽预测准确但缺乏可解释性，难以提供机制性见解。
- **精确研究问题**：Can a machine learning model incorporating DNA sequence, DNA shape, and histone modification features accurately predict tissue-specific CLOCK–BMAL1 binding to E-box motifs, and can feature importance analysis reveal the underlying binding mechanisms?

## 04 背景与发展脉络
（注：以下脉络基于本文引言与讨论，属「仅本文框架」，未经外部系统核验）

1. **阶段一：序列 motif 扫描时代**。代表性方法：PWM/consensus 扫描（如 E-box CANNTG）。优点：简单、可解释。局限：基因组中 motif 出现次数远多于实际结合位点（如小鼠基因组中 E-box 出现超 700 万次，但结合率 <0.7%），无法解释结合选择性。
2. **阶段二：表观遗传特征整合**。代表性方法：将染色质可及性（DNase-seq/ATAC-seq）纳入预测。优点：显著提升预测精度。局限：仍缺乏对结合机制（如 DNA 构象偏好）的深入解释。
3. **阶段三：机器学习/深度学习预测**。代表性方法：基于序列的 CNN/DNN 模型。优点：预测精度高。局限：黑箱性质，难以提取生物学机制。
4. **阶段四（本文位置）**：可解释机器学习 + 多模态特征。本文主张：将 DNA sequence、DNA shape（EP、MGW、ProT、Roll、HelT）和组蛋白修饰（H3K27ac、H3K4me1、H3K4me3、H3K27me3、H3K36me3）整合进 XGBoost，在保持高预测性能的同时，通过 permutation importance 揭示组织特异性结合的决定因素。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| E-box motif 数量庞大但结合率极低 | 小鼠基因组中 E-box 出现超 700 万次，但 <0.7% 被 CLOCK–BMAL1 结合 | 仅凭核心 motif 序列不足以决定结合，需考虑序列上下文、DNA 构象和染色质环境 | Introduction 第 2 段；Results 图 1C |
| 组织特异性结合机制不明 | 肝、肾、心三组织间结合的 E-box 重叠极少（仅 398 个三组织共有） | 不同组织可能依赖不同的特征组合（如肝依赖上游 G 核苷酸，肾/心依赖组蛋白修饰） | Results 图 1B；Discussion 末段 |
| 深度模型缺乏可解释性 | 现有深度学习方法预测准确但无法提供机制性见解 | 黑箱模型难以解析特征贡献，限制了对 TF–DNA 结合规则的理解 | Introduction 第 3 段 |
| DNA shape 特征单独使用效果不佳 | DNA shape-only 模型性能低于 sequence-only 模型 | shape 特征需与序列信息结合才能发挥预测力，单独使用信息不足 | Results 第 3 节（"DNA shape alone... lower than sequence-only"） |
| 跨组织泛化困难 | 跨组织预测时，加入 shape 和 histone 特征反而降低性能 | 组织间特征分布差异大，肝中重要的特征（如上游 G）在肾/心中不重要 | Results 图 6；Discussion 第 2 段 |

## 06 核心思想
1. **表面方法**：构建三类 XGBoost 模型（sequence-only、sequence+shape、sequence+shape+histone modifications），以 E-box 及其 4bp 侧翼序列为输入，预测结合状态；用 ELI5 permutation importance 解析特征贡献。
2. **核心洞察**：
   - DNA shape 特征（EP、Roll、MGW）和组蛋白修饰（H3K27ac、H3K4me3）是预测 CLOCK–BMAL1 结合的关键，而非核心 motif 序列本身。
   - 组织特异性结合源于不同组织依赖不同的特征组合：肝中 E-box 上游第二位点的 G 核苷酸贡献极大（>50% 特征权重），而肾/心更依赖组蛋白修饰和 DNA shape。
   - 跨组织预测性能下降说明结合规则具有组织特异性，不能简单迁移。
3. **可能的普适教训** [Analysis]：TF–DNA 结合预测不应仅关注核心 motif，侧翼序列、DNA 三维构象和表观遗传状态共同构成"结合密码"；可解释模型（如 XGBoost + permutation importance）在保持性能的同时能揭示生物学机制，是深度黑箱模型的有力替代。

## 07 方法总览
- **输入**：E-box motif（CANNTG）及其 4bp 上游/下游侧翼序列（共 14bp）；对应区域的 DNA shape 特征（EP、MGW、ProT、Roll、HelT）；±750bp 范围内 5 种组蛋白修饰（H3K27ac、H3K4me1、H3K4me3、H3K27me3、H3K36me3）的 ChIP-seq 信号。
- **输出**：E-box 是否被 CLOCK–BMAL1 结合（二分类）。
- **模块**：
  1. 数据预处理：从 GSE11060 获取 BMAL1 ChIP-seq peaks；从 ENCODE 获取 DNase-seq 和组蛋白修饰 ChIP-seq；提取 E-box 及侧翼序列。
  2. 特征工程：one-hot 编码 14bp 序列；DNAshapeR 计算 DNA shape 特征；binned 组蛋白修饰信号（10 bins × 150bp）。
  3. 模型训练：XGBoost 分类器，grid search 超参数调优（n_estimators, min_child_weight, subsample, max_depth, learning_rate, colsample_bytree），五折交叉验证。
  4. 特征重要性分析：ELI5 permutation importance。
- **训练**：五折分层交叉验证；正负样本比例 1:51（肝）、1:82（肾）、1:223（心）。
- **反馈回路**：无显式反馈回路；模型为静态监督学习。
- **文字流程**：提取基因组中所有 E-box → 筛选 DNase-seq 可及区域内的 E-box → 标注结合状态（与 ChIP-seq peaks 重叠）→ 计算序列、shape、histone 特征 → 训练 XGBoost → 评估 AUROC/AUPRC → permutation importance 解析特征贡献。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| E-box 提取与标注 | 从基因组中识别所有 E-box 并标注结合状态 | 构建训练数据集的基础 | 输入：参考基因组、ChIP-seq peaks、DNase-seq peaks；输出：正负样本集 | Results 图 1A-F | 无法训练模型 |
| 序列 one-hot 编码 | 将 14bp 序列转换为数值特征 | 序列特征输入模型的基本表示 | 输入：14bp 序列；输出：14×4 二进制矩阵 | Methods "ChIP-seq dataset preprocessing" | 模型失去序列信息，性能大幅下降 |
| DNA shape 特征计算（DNAshapeR） | 计算 EP、MGW、ProT、Roll、HelT 五种构象特征 | 捕获序列无法直接体现的 DNA 三维结构信息 | 输入：14bp 序列；输出：归一化 binned shape 特征向量 | Methods "DNA shape preprocessing"；Results 图 2A | 性能显著下降（AUPRC 从 0.79 降至 0.09，肝）——实测效应 |
| 组蛋白修饰特征提取 | 提取 ±750bp 内 5 种 histone mark 信号 | 捕获染色质环境对结合的影响 | 输入：组蛋白 ChIP-seq BAM；输出：10 bins 平均信号 | Methods "Histone modification preprocessing" | 性能下降（肝 AUPRC 从 0.95 降至 0.79）——实测效应 |
| XGBoost 分类器 | 预测 E-box 结合状态 | 核心预测模型 | 输入：特征矩阵；输出：结合概率 | Methods "XGBoost"；Results 表 1 | 无替代模型 |
| ELI5 permutation importance | 计算各特征对预测的贡献 | 提供模型可解释性，揭示结合机制 | 输入：训练好的模型 + 验证集；输出：特征重要性分数 | Results 图 4A-C | 无法获得机制性见解 |

## 09 关键公式符号
不适用。本文未提供显式数学公式；模型为 XGBoost 集成树，特征重要性通过 permutation importance 计算（打乱某特征后模型性能下降幅度），无需要列出的核心公式。

## 10 实验设计与证据链
- **数据集**：小鼠（C57BL/6J）肝、肾、心三组织；BMAL1 ChIP-seq（GSE11060，ZT6 时间点）；DNase-seq 和组蛋白修饰 ChIP-seq 来自 ENCODE。
- **样本量**：肝：3725 结合 vs 189,581 未结合；肾：3237 vs 262,053；心：1313 vs 291,840。
- **指标**：AUROC、AUPRC（五折交叉验证均值 ± 95% CI）。
- **基线**：Logistic 回归。
- **评测协议**：五折分层交叉验证；正负样本不平衡（1:51 至 1:223），AUPRC 作为主要指标。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-------------|------------------|------|
| 序列特征分布分析 | E-box 类型在基因组与结合位点中分布不同 | 全基因组 vs 可及染色质 vs ChIP-seq 结合位点 | CACGTG 在基因组中最少（1.83%）但结合率最高 | CLOCK–BMAL1 对 CACGTG 有强偏好 | 未证明 CACGTG 是唯一决定因素 | Results 图 1C-E |
| sequence-only 模型 | 仅序列可预测结合 | XGBoost vs Logistic 回归 | 肝 AUROC 0.71，AUPRC 0.09 | 序列信息有限 | 序列不足以稳健预测 | Results 表 1 |
| sequence+shape 模型 | DNA shape 提升预测 | 加 shape vs 仅序列 | 肝 AUROC 0.97，AUPRC 0.79 | shape 特征大幅提升性能 | 未比较不同 shape 特征的独立贡献 | Results 表 1、图 3 |
| sequence+shape+HM 模型 | 组蛋白修饰进一步提升 | 加 HM vs 无 HM | 肝 AUROC 0.99，AUPRC 0.95 | HM 提供额外预测信息 | 未测试 HM 单独使用效果 | Results 表 1、图 3 |
| 特征重要性分析 | 识别关键预测因子 | ELI5 permutation importance | 肝：Seq-2 位 G 贡献 >50%；肾/心：H3K27ac、EP 主导 | 组织特异性结合规则 | 未验证因果性 | Results 图 4 |
| 跨组织预测 | 结合规则是否跨组织通用 | 训练于组织 X，预测组织 Y | 加入 shape+HM 后多数跨组织模型性能下降 | 结合规则具有组织特异性 | 未测试所有组织组合 | Results 图 6 |

## 11 结论正确解读
- **任务范围**：仅预测 E-box motif 在 DNase-seq 可及染色质区域内的结合状态，不涵盖不可及染色质中的结合；仅针对 ZT6 时间点，未考虑昼夜节律时间动态。
- **oracle/真值输入**：ChIP-seq 峰作为结合金标准；DNase-seq 峰定义可及染色质；组蛋白修饰 ChIP-seq 信号作为特征。这些均为实验数据，非模拟或预测值。
- **端到端状态**：模型为端到端监督学习，但特征工程（shape 计算、histone binning）为手工设计，非端到端深度学习。
- **算力成本**：未报告训练时间或硬件需求；XGBoost 在表格数据上通常计算高效。
- **历史数据依赖**：依赖特定小鼠品系（C57BL/6J）和特定组织；跨品系、跨物种泛化性未验证。
- **模型依赖**：XGBoost 为树集成模型，特征重要性基于 permutation，反映相关性而非因果性。
- **最难情形**：心组织预测性能最低（AUPRC 0.80），可能因心组织中结合位点较少或特征差异大。
- **群体/领域边界**：仅限哺乳动物昼夜节律 TF（CLOCK–BMAL1/NPAS2–BMAL1），不适用于其他 TF 家族。
- **不确定性**：未报告置信区间外的预测不确定性；未进行独立数据集外部验证。
- **有边界的复述**：在小鼠肝、肾、心中，结合 DNA shape 和组蛋白修饰特征的 XGBoost 模型能以高 AUROC/AUPRC 预测 CLOCK–BMAL1 对可及染色质中 E-box 的结合，且特征重要性显示组织特异的结合规则——肝依赖上游 G 核苷酸，肾/心依赖组蛋白修饰和 DNA 构象。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 仅考虑可及染色质中的 E-box | 排除了不可及染色质中的潜在结合位点 | 未明确提及 | Discussion 第 1 段（"we had only considered E-boxes in accessible chromatin"） |
| 单一时间点（ZT6） | 未捕捉昼夜节律时间动态对结合的影响 | 未明确提及 | Methods "ChIP-seq dataset preprocessing"（ZT6 时间点） |
| 心组织结合位点少 | 心组织模型性能较低，可能因样本量不足 | 未明确提及 | Results 图 1B、表 1 |
| 未验证因果性 | 特征重要性反映相关性，不证明因果作用 | 未明确提及 | Discussion 末段（"we propose that..."） |
| 跨组织泛化有限 | 跨组织预测时性能下降，表明组织特异性强 | 未明确提及 | Results 图 6；Discussion 第 2 段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 正负样本极度不平衡（1:51 至 1:223） | AUPRC 对不平衡敏感，模型可能偏向多数类；未报告 F1 或 MCC 等平衡指标 | 高 AUPRC 可能部分由不平衡驱动，需验证模型在平衡条件下的表现 | 使用下采样或 SMOTE 后重新评估；报告 F1、MCC | Results 表 1 |
| 未进行独立外部验证 | 模型仅在 GSE11060 同一数据集内交叉验证，可能过拟合 | 泛化性未证实，尤其跨实验室、跨批次 | 在独立 ChIP-seq 数据集（如 ENCODE 其他小鼠组织）上测试 | Methods "ChIP-seq dataset preprocessing" |
| DNA shape 特征由序列计算而来 | shape 与序列高度相关，shape 的增量贡献可能被高估 | 需区分 shape 的独立贡献 vs 序列的间接效应 | 控制序列后比较 shape 特征的 permutation importance；使用部分依赖图 | Methods "DNA shape preprocessing" |
| 组蛋白修饰数据来自未同步组织 | 作者承认 DNase-seq 和组蛋白 ChIP-seq 来自未同步组织，而 BMAL1 ChIP-seq 在 ZT6 | 时间不匹配可能导致特征与标签间的虚假关联 | 使用同步组织的组蛋白数据重新训练 | Discussion 第 2 段 |
| 仅用 permutation importance 解释模型 | 树模型的 permutation importance 可能受特征相关性影响，产生误导 | 机制性结论需多方法交叉验证 | 使用 SHAP 值、LIME 或 ICE 图交叉验证 | Results 图 4 |
| 未比较深度学习方法 | 未与 CNN/DeepBind 等深度模型对比，无法评估 XGBoost 的相对优势 | 深度模型可能捕获更复杂的序列模式 | 在相同数据上训练 CNN 基线并比较 | Introduction 第 3 段 |
| 肝中 Seq-2 G 的贡献可能受 E-box 类型混淆 | 肝中结合位点 CACGTG 富集，而 CACGTG 的侧翼序列可能系统性不同 | 需控制 E-box 类型后检验侧翼序列的独立贡献 | 分层分析：仅对 CACGTG 位点重新计算特征重要性 | Results 图 4A、5A |

## 14 学到什么
**Agent 提炼的知识候选**

1. **多模态特征融合策略**：将序列（one-hot）、DNA shape（DNAshapeR 计算的 5 种构象特征）和表观遗传（组蛋白修饰信号）三类特征整合进树模型，显著优于单一特征类型。→ 迁移到 TF–DNA 课题：对任意 TF，可构建"序列 + shape + 染色质状态"的多模态预测框架，而非仅用 PWM 或序列特征。
2. **可解释性优先的建模思路**：选择 XGBoost + permutation importance 而非深度黑箱模型，在保持高性能（AUROC 0.99）的同时获得机制性见解。→ 迁移：当研究目标是理解结合机制而非仅预测时，优先考虑可解释模型或对深度模型进行事后解释（SHAP）。
3. **组织特异性结合规则**：不同组织依赖不同特征组合（肝依赖侧翼序列，肾/心依赖组蛋白修饰和 shape），说明 TF–DNA 结合规则具有组织/细胞类型特异性。→ 迁移：研究 TF 结合时不应假设跨组织通用规则，需按组织/细胞类型分别建模并比较特征重要性。
4. **侧翼序列的重要性**：E-box 上游第二位点的 G 核苷酸在肝中贡献 >50% 特征权重，表明核心 motif 之外的侧翼序列对结合选择性至关重要。→ 迁移：在 TF–DNA 结合预测中，应扩展窗口至 motif 外 4bp 或更长，并关注侧翼序列的核苷酸偏好。
5. **DNA shape 的增量价值**：shape 特征（EP、Roll、MGW）在加入序列后仍显著提升性能，说明 DNA 三维构象提供了序列无法直接编码的信息。→ 迁移：对 bHLH 家族 TF（如 CLOCK、BMAL1、Myc、Max），DNA shape 可能是保守的结合决定因素，值得优先纳入特征集。
6. **跨组织泛化诊断**：跨组织预测性能下降（尤其加入 shape+HM 后）可作为组织特异性结合规则的诊断工具。→ 迁移：若跨条件/跨细胞类型预测性能骤降，提示结合机制存在条件特异性，需分别建模。
7. **不平衡数据的处理**：正负样本比例 1:51 至 1:223，使用 AUPRC 而非仅 AUROC 评估。→ 迁移：TF 结合位点预测天然存在不平衡问题，应优先报告 AUPRC 并考虑采样策略。
8. **特征重要性归一化方法**：将每个 shape/histone 特征的多个 bin 的重要性求和，得到该特征的总贡献。→ 迁移：对连续型特征（如 shape 曲线、histone 信号谱），可先分 bin 再聚合重要性，便于跨特征比较。

## 15 与已有知识连接
- **相似工作**：DNAshapeR 方法（Zhou et al., 2013, Nucleic Acids Research）——本文使用的 shape 特征计算工具；此前研究（Yang et al., 2014, PNAS）表明 DNA shape 可提升 bHLH TF 结合预测，本文在哺乳动物组织层面扩展了这一发现。
- **TF–DNA 结合预测的经典方法**：PWM 扫描（如 FIMO/MAST）仅基于序列；本文证明加入 shape 和 histone 特征可大幅提升预测（AUPRC 从 0.09 到 0.95），呼应了"序列不足以决定结合"的共识。
- **昼夜节律领域**：CLOCK–BMAL1 的 E-box 结合已有大量 ChIP-seq 研究（Koike et al., 2012, Science），本文的贡献在于用可解释 ML 模型解析组织特异性结合规则。
- **可解释 AI 在基因组学中的应用**：与 DeepSEA、Basenji 等深度模型形成对比，本文展示了树模型 + permutation importance 在机制解析上的优势。
- **组蛋白修饰与 TF 结合**：H3K27ac 和 H3K4me3 是活性增强子/启动子标记，本文证实其与 CLOCK–BMAL1 结合高度相关，与已知的"TF 倾向于结合开放染色质"一致。
- **候选方向（未验证）**：本文的"侧翼序列 + shape + histone"框架可迁移至其他 bHLH TF（如 Myc、Max、USF1）或组织特异性 TF 的结合预测；也可与 AlphaFold 预测的 TF–DNA 复合物结构结合，验证 shape 特征的物理基础。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：TF–DNA 结合预测的通用多模态框架（MultiModal-TFBind）
   - **来源局限/观察**：本文仅针对 CLOCK–BMAL1 和三个组织，框架未在其他 TF 上验证。
   - **核心假设**：序列 + DNA shape + 组蛋白修饰的多模态特征可泛化至多种 TF 的结合预测。
   - **初步方法**：在 ENCODE 多个 TF 的 ChIP-seq 数据集上，统一提取 E-box 或各 TF 的 motif 及侧翼序列、DNAshapeR shape 特征、组蛋白修饰信号，训练 XGBoost 并比较 AUPRC。
   - **验证方式**：跨 TF 交叉验证；与 DeepBind/DeepSEA 基线对比。
   - **创新状态**：unverified

2. **候选名称**：DNA shape 特征的物理基础解析（Shape-Physics Link）
   - **来源局限/观察**：本文发现 EP、Roll、MGW 是重要预测因子，但未解释其物理机制。
   - **核心假设**：DNA shape 特征通过影响 TF 的 DNA 结合结构域（DBD）的几何匹配度来调控结合亲和力。
   - **初步方法**：对 CLOCK–BMAL1 的 bHLH 结构域与不同 shape 特征的 E-box 进行分子动力学（MD）模拟或对接，计算结合自由能与 shape 特征的相关性。
   - **验证方式**：MD 模拟的结合能排序与 ML 模型预测概率排序的一致性。
   - **创新状态**：unverified

3. **候选名称**：组织特异性结合规则的跨组织迁移学习（Tissue-Transfer TF Binding）
   - **来源局限/观察**：本文跨组织预测性能下降，表明组织特异性强，但未尝试迁移学习。
   - **核心假设**：组织间存在共享的结合规则（如核心 motif 偏好）和特异规则（如侧翼序列、histone 组合），迁移学习可分离两者。
   - **初步方法**：用多任务学习或域适应（domain adaptation）在肝、肾、心数据上联合训练，显式建模共享与特异特征。
   - **验证方式**：迁移后目标组织 AUPRC 是否优于单组织模型；特征重要性分析是否分离出共享/特异特征。
   - **创新状态**：unverified

4. **候选名称**：侧翼序列 G 富集的机制验证（Flanking-G Functional Assay）
   - **来源局限/观察**：肝中 E-box 上游第二位 G 贡献 >50% 权重，但未做实验验证。
   - **核心假设**：上游 -2 位 G 通过改变 DNA 局部 shape（如 roll 或 minor groove width）增强 CLOCK–BMAL1 结合。
   - **初步方法**：设计 E-box 上游 -2 位 G→A/T/C 突变的报告基因实验（luciferase assay）或体外 EMSA 结合实验，测量结合亲和力变化；同时用 DNAshapeR 预测突变后的 shape 变化。
   - **验证方式**：实验结合亲和力与 shape 预测变化的相关性。
   - **创新状态**：unverified

5. **候选名称**：时间维度上的 TF 结合动态预测（Circadian-Time TF Binding）
   - **来源局限/观察**：本文仅使用 ZT6 单时间点 ChIP-seq，未考虑昼夜节律时间动态。
   - **核心假设**：组蛋白修饰和染色质状态随时间变化，可预测 CLOCK–BMAL1 结合的昼夜节律动态。
   - **初步方法**：使用多时间点（ZT0/ZT6/ZT12/ZT18）的 ChIP-seq 数据，将时间作为特征或构建时序模型（如 RNN）。
   - **验证方式**：时间点间 AUPRC 对比；预测的结合动态与已知节律基因表达相位的一致性。
   - **创新状态**：unverified

6. **候选名称**：TF–DNA 结合预测中的 shape 特征可解释性基准（ShapeXAI Benchmark）
   - **来源局限/观察**：本文使用 permutation importance，但未与其他可解释性方法（SHAP、LIME）对比。
   - **核心假设**：不同可解释性方法对 shape 特征重要性的排序存在差异，需建立基准。
   - **初步方法**：在本文数据集上比较 permutation importance、SHAP、LIME 的特征重要性排序，并评估与已知生物学知识（如 bHLH 结合偏好）的一致性。
   - **验证方式**：方法间排序一致性（如 Spearman 相关）；与实验验证的 shape 偏好对比。
   - **创新状态**：unverified