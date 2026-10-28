## 01 基本信息

- **标题**：Local DNA shape is a general principle of transcription factor binding specificity in Arabidopsis thaliana
- **作者**：Sielemann, Janik; Wulf, Donat; Schmidt, Romy; Brautigam, Andrea
- **单位**：Bielefeld University（根据致谢部分推断，具体单位列表未提供）
- **期刊/平台**：Nature Communications
- **年份**：2021
- **论文类型**：研究论文（Research Article）
- **领域**：植物转录调控；蛋白质-DNA互作；计算生物学；机器学习
- **关键词**：DNA shape；transcription factor binding specificity；random forest；Arabidopsis thaliana；ampDAP-seq
- **DOI/arXiv 号**：10.1038/s41467-021-26819-2
- **代码**：https://github.com/janiksielemann/shape-based-TF-binding-prediction
- **数据**：Plant Cistrome Database (neomorph.salk.edu/dap_web/pages/index.php)；TAIR10 参考基因组
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「TF–DNA 结合机制 × 机器学习」方向，核心主张是 DNA 三维形状（而非仅一维序列 motif）是决定 TF 结合特异性的普适原则。方法上采用随机森林回归，输入为 DNA shape 特征（由序列通过查询表计算），输出为结合亲和力预测。该文为「序列→结构→功能」的预测范式提供了植物领域的系统性证据，覆盖 216 个 TF，是 TF–DNA 互作机制研究中将 DNA shape 作为通用特征的代表性工作。

---

## 02 一句话总结

本文用随机森林回归模型，以 DNA 三维 shape 特征（而非仅序列 motif）作为输入，对拟南芥 216 个 TF 的 ampDAP-seq 结合亲和力进行预测，发现 shape 特征普遍提升结合位点预测精度（AUPRC 平均提升 93.2%），并能区分共享同一序列 motif 的家族成员间的差异结合。

---

## 03 研究问题

- **具体问题**：DNA 序列 motif 不足以解释 TF 在基因组中的实际结合位置——基因组中含 motif 的位点远多于实际被结合的位点（平均 14 倍）。本文问：DNA 的三维 shape 信息能否作为普适特征，提升 TF 结合位点的预测精度，并解释共享同一 motif 的家族成员间的差异结合？
- **为什么重要**：理解基因表达调控需要准确预测 TF 在基因组中的结合位置。序列 motif 方法存在大量假阳性，限制了调控网络的构建和基因表达的直接预测。
- **现有方法为何不足**：传统 motif 扫描（如 FIMO）仅考虑一维序列信息，忽略 DNA 的局部三维结构。而 DNA shape（如 minor groove width、roll、helix twist 等）已被证明影响蛋白质-DNA 识别，但缺乏系统性的、跨多个 TF 家族的验证。
- **精确的「Can ... ?」问题**：Can DNA shape features, when incorporated into a machine learning model, universally improve the prediction of TF binding affinity across diverse TF families in Arabidopsis thaliana, and resolve differential binding among family members sharing the same sequence motif?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论，属于「仅本文框架」，未经外部系统核验。

1. **序列 motif 时代**：早期方法用位置权重矩阵（PWM）描述 TF 结合位点，如 MEME、FIMO 等。优点：简单、可解释；局限：仅编码一维序列，无法解释同一 motif 在不同基因组位置的差异结合。
2. **DNA shape 的引入**：实验与计算研究表明 DNA 局部结构（如 minor groove width、roll、propeller twist 等）影响蛋白质-DNA 识别。代表性工作包括 DNAshape 数据库（本文使用的查询表来源，Rohs 实验室）。优点：提供序列之外的物理化学信息；局限：多为个案研究，未系统验证其普适性。
3. **机器学习预测 TF 结合**：已有工作用深度学习（如 DeepBind、DeepSEA）或传统 ML 预测 ChIP-seq 结合。优点：能捕捉非线性关系；局限：多数依赖序列特征，或未系统比较 shape 特征的增量贡献。
4. **本文主张的位置**：在「序列 motif → DNA shape → 结合亲和力」的链条中，本文系统性地将 shape 特征纳入随机森林模型，覆盖 216 个 TF（远超此前研究），证明 shape 是普适的预测因子，并首次在多个家族内展示 shape 可区分共享 motif 的成员。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 序列 motif 预测精度低 | 基因组中 motif 出现频率平均比实际结合事件高 14 倍 | motif 仅编码一维序列，忽略 DNA 三维结构对结合的贡献 | Introduction 节；Supplementary Fig. 1 |
| 同家族 TF 共享 motif 但结合不同位点 | 同一家族的 TF（如 WRKY、bHLH）结合相同 motif 序列，但实际结合位置不同 | 序列 motif 无法区分家族成员间的结合偏好，需要 shape 信息 | Introduction 节；Results 图 2 |
| 传统 motif 扫描产生大量假阳性 | 仅用序列 motif 扫描基因组，预测的结合位点远多于实验验证的位点 | 缺乏对 DNA shape 的考虑，导致无法排除结构上不利的位点 | Results 图 1a；Supplementary Fig. 1 |
| shape 特征维度高、非线性关系复杂 | 简单线性模型难以捕捉 shape 特征与结合亲和力之间的非线性关系 | shape 特征可能以组合方式影响结合，需要非线性模型 | Introduction 节；Results 图 1b |

---

## 06 核心思想

1. **表面方法**：对每个 TF，用 MEME-ChIP 从 ampDAP-seq 峰中提取核心 motif；用 FIMO 扫描全基因组获得所有含 motif 的位点；对每个位点计算 13 种 DNA shape 特征（通过 DNAshape 查询表）；训练随机森林回归模型，以 shape 特征为输入、ampDAP-seq 信号值为标签，预测结合亲和力。

2. **核心洞察**：DNA 的三维 shape 是 TF 结合特异性的普适决定因素——不仅提升单个 TF 的预测精度，还能区分共享同一序列 motif 的家族成员。关键发现是 shape 特征的贡献是**逐 TF 加权**的：不同 TF 依赖不同的 shape 特征组合，即使它们结合相同的核心序列。

3. **可能的普适教训 [Analysis]**：序列信息是「必要但不充分」的——TF 结合特异性由序列编码的结构特征（shape）而非序列本身决定。这提示在蛋白质-DNA 互作研究中，将一维序列映射到三维结构特征（无论是通过查询表、MD 模拟还是结构预测）是提升预测能力的关键步骤。此外，逐 TF 的特征重要性分析（SHAP）表明，不能期望一个通用的 shape 特征集适用于所有 TF，而应针对每个 TF 学习其特有的结构偏好。

---

## 07 方法总览

- **输入**：ampDAP-seq 峰文件（含结合信号值）、A. thaliana 参考基因组（TAIR10）
- **输出**：每个 TF 的随机森林回归模型，可对任意含 motif 的序列预测结合亲和力
- **模块**：
  1. **数据获取与过滤**：从 Plant Cistrome Database 获取 ampDAP-seq 数据，仅保留 FRiP > 5% 的数据集
  2. **Motif 检测**：MEME-ChIP 从峰序列中检测核心 motif（取最低 E-value 的 motif）
  3. **基因组扫描**：FIMO 在全基因组中扫描 motif 出现位置（阈值 5e-4）
  4. **Shape 特征计算**：对每个 motif 位点（含侧翼序列）用 DNAshape 查询表计算 13 种 shape 特征
  5. **数据预处理**：过滤多 motif 位点；处理同源二聚体情况；样本加权（正负样本比例控制）
  6. **模型训练**：随机森林回归（scikit-learn），5 折交叉验证 + 随机超参数搜索（75 次迭代，共 375 次训练/TF）
  7. **特征重要性分析**：SHAP 值提取每个 TF 的关键 shape 特征
  8. **实验验证**：EMSA 验证 HY5 和 ANAC050 的预测结果

- **流程**：峰文件 → motif 检测 → 全基因组扫描 → shape 计算 → 训练/验证 → 预测 → 实验验证

- **关键假设**：
  - ampDAP-seq 信号值可作为结合亲和力的代理指标
  - DNA shape 可由序列通过查询表准确计算（无需实验结构）
  - 核心 motif 加侧翼序列的 shape 足以捕捉结合特异性

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ampDAP-seq 数据获取与过滤 | 获取实验结合数据，过滤低质量数据集 | 提供训练标签（结合信号值） | 输入：Plant Cistrome 数据库峰文件；输出：FRiP > 5% 的峰文件 | Methods 节 | 移除后无训练数据；FRiP 过滤移除后可能引入噪声数据 [预期] |
| MEME-ChIP motif 检测 | 从峰序列中提取核心序列 motif | 定义「含 motif 位点」的搜索空间 | 输入：峰序列；输出：每个 TF 的核心 motif | Methods 节 | 移除后无法定义候选位点；motif 质量差会降低下游预测 [预期] |
| FIMO 全基因组扫描 | 在基因组中定位所有含 motif 的位点 | 生成候选结合位点集合（正负样本） | 输入：motif + 基因组；输出：所有 motif 出现位置 | Methods 节 | 移除后无法生成负样本；扫描阈值影响候选集大小 [预期] |
| DNAshape 特征计算 | 将序列转换为 13 种三维结构特征 | 将一维序列信息映射到三维结构空间 | 输入：含侧翼的 motif 序列；输出：13 维 shape 特征向量 | Methods 节；图 1d | 移除后模型退化为纯序列模型，预测精度显著下降 [实测：图 1b 显示 shape 模型优于 motif 基线] |
| 随机森林回归 | 学习 shape 特征与结合信号值的非线性映射 | 捕捉 shape 特征的组合效应和非线性贡献 | 输入：shape 特征 + 信号值标签；输出：训练好的回归模型 | Methods 节 | 替换为线性模型可能丢失非线性关系 [预期]；替换为深度学习可能需更多数据 [预期] |
| SHAP 特征重要性 | 提取每个 TF 的关键 shape 特征 | 解释模型决策，揭示 TF 特有的结构偏好 | 输入：训练好的模型；输出：每个特征的重要性排序 | Results 图 2d | 移除后无法解释不同 TF 的 shape 偏好差异 [预期] |
| EMSA 实验验证 | 体外验证预测的高/低亲和力序列 | 验证模型预测的生物学真实性 | 输入：预测序列；输出：结合/不结合的实验证据 | Results 图 3a, b | 移除后预测仅停留在计算层面，缺乏实验支撑 [预期] |

---

## 09 关键公式符号

本文未提供显式的数学公式。核心概念符号如下：

- **AUPRC**：Area Under the Precision-Recall Curve，精确率-召回率曲线下面积，用于评估分类/回归排序性能
- **FRiP**：Fraction of Reads in Peaks，峰中读段比例，用于评估 ChIP/ampDAP-seq 数据质量
- **13 种 DNA shape 特征**：包括但不限于 minor groove width (MGW)、roll、helix twist (HelT)、propeller twist (ProT)、shear、stretch、stagger、buckle、opening、shift、slide、rise、tilt（图 1d）
- **SHAP**：SHapley Additive exPlanations，基于博弈论的特征重要性归因方法
- **FIMO**：Find Individual Motif Occurrences，基于 PWM 的 motif 扫描工具
- **样本加权**：正负样本比例被强制为 1:5 或 1:3（当正样本过多时），以平衡训练

---

## 10 实验设计与证据链

**数据集与规模**：
- 216 个 A. thaliana TF 的 ampDAP-seq 数据（Plant Cistrome Database）
- 仅保留 FRiP > 5% 的数据集
- 每个 TF 平均 146,326 条含 motif 的序列（最少 18,210，最多 640,292）
- 基因组：TAIR10

**指标**：AUPRC（精确率-召回率曲线下面积）

**基线**：序列 motif 扫描（FIMO）作为 baseline，比较 shape 模型的增量提升

**评测协议**：训练/验证集 80/20 划分，5 折交叉验证，随机超参数搜索（75 次迭代）

**实验表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| 全 TF 预测性能 | shape 特征普遍提升结合预测 | 216 个 TF 的 shape 模型 vs motif 基线 | AUPRC 平均提升 93.2%（范围 2.8%–362.7%）；33 个 TF AUPRC > 0.8 | shape 特征对几乎所有 TF 都有增量贡献 | 提升幅度因 TF 而异，部分 TF 仍预测不佳 | Results 图 1b |
| 序列宽度影响 | shape 信息主要位于核心 motif 及邻近区域 | 改变输入序列宽度（侧翼碱基数） | 核心 motif 加两侧各 2 bp 即达主要贡献，更宽侧翼增益有限 | shape 的贡献集中在 motif 近旁 | 未测试更远距离的 shape 效应 | Results 图 1c |
| PCA 降维对比 | shape 特征非高度冗余 | 原始 shape 特征 vs PCA 降维后特征 | 降维后性能显著下降 | shape 特征包含互补信息，不可简单降维 | 未测试其他降维方法 | Results；Supplementary Fig. 4 |
| 家族内区分 | shape 可区分共享 motif 的家族成员 | ERF/AP2 的 CBF4 vs ERF036；NAC 的 ANAC050 vs BRN2 | 模型能正确预测 84%（CBF4）和 83.8%（ERF036）的独特结合位点；假阳性降低 86–93% | shape 特征编码了家族成员间的差异结合特异性 | 仅测试了少数家族，未覆盖所有家族 | Results 图 2 |
| 随机森林 vs 其他 ML | RF 是合理选择 | RF vs 梯度提升 vs 神经网络 | RF 与梯度提升相当，均优于简单神经网络 | RF 适合该任务且可解释性好 | 未进行深度学习的充分调参 | Supplementary Fig. 10 |
| EMSA 实验验证 | 预测的高/低亲和力序列真实反映结合差异 | HY5 和 ANAC050 的预测序列进行竞争性 EMSA | 10/12 预测正确 | 模型预测具有实验可验证性 | 仅验证 2 个 TF，样本量小 | Results 图 3 |

---

## 11 结论正确解读

- **任务范围**：本文预测的是**体外** ampDAP-seq 结合亲和力（无染色质背景、无竞争性 TF、无共因子），而非体内结合（ChIP-seq）。作者明确比较了 ampDAP-seq 与 ChIP-seq，发现 ampDAP-seq 预测效果更好，说明体内因素（染色质可及性等）未被模型捕捉。
- **Oracle/真值输入**：训练标签来自 ampDAP-seq 实验信号值，是实验测量值而非计算模拟值。DNA shape 特征由序列通过查询表计算，非实验结构测定。
- **端到端状态**：**非端到端**。流程为「序列 → shape 特征（查询表）→ 随机森林」，shape 计算是独立的预处理步骤，非可学习模块。
- **算力成本**：随机森林训练成本低，375 次训练/TF × 216 TF 在常规计算资源上可行。未报告具体 GPU/CPU 时间。
- **历史数据依赖**：依赖 Plant Cistrome Database 的 ampDAP-seq 数据，该数据基于体外扩增 DNA 结合实验，不包含体内染色质状态信息。
- **模型依赖**：随机森林为非线性模型，可捕捉 shape 特征的组合效应；但作者未测试深度学习模型（如 CNN）在相同任务上的表现，因此无法判断 shape 特征 + 简单 ML 是否优于序列 + 深度学习的范式。
- **最难情形**：AUPRC < 0.5 的 82 个 TF 表明，部分 TF 的结合特异性可能由 shape 之外的因素（如蛋白柔性、共因子、翻译后修饰）决定，或 ampDAP-seq 数据质量不足以训练有效模型。
- **边界复述**：在拟南芥 216 个 TF 的体外 ampDAP-seq 数据上，DNA shape 特征作为随机森林输入，平均提升结合位点预测 AUPRC 93.2%，并能区分共享同一序列 motif 的家族成员。该结论限于体外结合实验、拟南芥基因组、以及所测试的 13 种 shape 特征。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 体内 vs 体外差异 | ChIP-seq 数据预测效果低于 ampDAP-seq | 需整合染色质状态、共因子等体内信息 | Results 节；Supplementary Fig. 8 |
| 部分 TF 预测精度低 | 82 个 TF 的 AUPRC 未超过 0.5 | 可能需要更复杂的模型或额外特征 | Results 图 1b |
| 同源二聚体处理 | 仅对多 motif 位点进行了简单过滤 | 需更精细地建模二聚体结合模式 | Methods 节 |
| 序列宽度有限 | 测试的最大侧翼宽度有限 | 未测试更远距离的 shape 效应或更长的调控区域 | Results 图 1c |
| 实验验证范围小 | 仅对 2 个 TF 进行了 EMSA 验证 | 需更大规模的实验验证 | Results 图 3 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| AUPRC 提升幅度差异大（2.8%–362.7%） | 部分 TF 的「提升」可能来自 motif 本身质量差，而非 shape 的真实贡献 | 若 baseline motif 质量差，shape 的增量贡献可能被高估 | 用统一的 motif 质量标准（如信息含量）分层分析提升幅度 | Results 图 1b |
| 训练数据来自 ampDAP-seq 体外实验 | 体外结合 ≠ 体内结合，shape 特征在体内可能被染色质结构覆盖 | 结论推广到体内调控时需谨慎 | 与 ChIP-seq 数据对比，或整合染色质可及性数据 | Results 节；Supplementary Fig. 8 |
| 13 种 shape 特征来自查询表 | 查询表基于晶体结构统计，可能不适用于所有序列上下文 | 某些 shape 特征在特定序列背景下可能计算不准 | 用 MD 模拟或实验结构验证查询表预测的 shape 值 | Methods 节 |
| 随机森林为黑箱模型 | SHAP 提供了特征重要性，但未揭示 shape 特征与结合的具体物理机制 | 理解机制需要更直接的物理模型 | 结合 MD 模拟或结构预测分析关键 shape 特征 | Results 图 2d |
| 仅测试了拟南芥 | 结论是否适用于其他物种（如动物、人类）未知 | 若 shape 是普适原则，应在跨物种数据上验证 | 在人类或酵母 TF 数据上重复相同流程 | 未提供 |
| 未与深度学习模型充分比较 | 简单神经网络未调参，CNN/Transformer 可能优于随机森林 | 若深度学习 + 序列即可达到同等效果，shape 特征的必要性需重新评估 | 用相同数据训练 CNN/Transformer 并比较 | Supplementary Fig. 10 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **Shape 特征作为通用中间表示**：将序列映射到三维结构特征（而非直接输入序列）是提升 TF 结合预测的有效策略。可迁移到本课题：在构建 TF–DNA 结合预测模型时，可考虑将 DNA shape 特征（MGW、roll、helix twist 等）作为输入，或将其与序列 embedding 结合。

2. **逐 TF 的特征加权**：不同 TF 依赖不同的 shape 特征组合，即使共享同一 motif。可迁移：在建模 TF–DNA 互作时，不应假设所有 TF 有统一的「结构偏好模板」，而应允许模型为每个 TF 学习独立的特征权重。

3. **局部 shape 的贡献范围有限**：核心 motif 加两侧各 2 bp 即达主要预测贡献。可迁移：在设计特征时，侧翼长度不需要过长；但这也提示更远端的结构效应（如 DNA 弯曲、核小体定位）可能未被捕捉。

4. **体外 vs 体内的信息差距**：ampDAP-seq 预测优于 ChIP-seq，说明体内结合还受染色质状态、竞争性结合等因素影响。可迁移：在构建 TF–DNA 结合模型时，应明确预测目标是体外亲和力还是体内占用，并相应选择训练数据。

5. **实验验证的计算-实验闭环**：用计算模型生成预测，再用 EMSA 验证，是建立模型可信度的有效路径。可迁移：在提出新的 TF–DNA 预测方法时，应设计小规模实验验证关键预测。

6. **SHAP 用于机制解释**：SHAP 值可揭示每个 TF 的关键 shape 特征，为理解 TF 家族内的分化提供线索。可迁移：在 AI 模型中引入可解释性分析，将「预测」提升为「机制假设生成」。

---

## 15 与已有知识连接

- **DNAshape 数据库（Rohs 实验室）**：本文使用的 shape 特征查询表来源。该数据库基于晶体结构统计，提供 MGW、roll、helix twist 等结构参数。相关文献：Zhou et al., *Nucleic Acids Research*, 2013。
- **ampDAP-seq 技术**：O'Malley et al., *Cell*, 2016 开发的体外 TF 结合谱技术，本文数据来源于该工作的 Plant Cistrome Database。
- **TF 结合预测的深度学习工作**：DeepBind (Alipanahi et al., *Nature Biotechnology*, 2015) 和 DeepSEA (Zhou & Troyanskaya, *Nature Methods*, 2015) 用 CNN 直接从序列预测结合，未显式使用 shape 特征。本文可视为「序列 + 结构特征」范式的代表，与纯序列深度学习方法形成互补。
- **DNA shape 与 TF 结合的特异性研究**：此前有工作（如 Rohs et al., *Nature*, 2009）证明 shape readout 在特定 TF 中的作用，本文将其扩展为跨 216 个 TF 的普适原则。
- **TF 家族内分化**：bHLH、WRKY 等家族成员共享 motif 但功能不同，本文提供了一种基于 shape 的机制解释，与「TF 平行进化」和「顺式调控元件分化」的研究相衔接。
- **与 MD 模拟的潜在连接**：本文用查询表计算 shape，未使用 MD 模拟。但 shape 特征可作为 MD 模拟的粗粒化初始条件或验证目标，连接统计方法与物理模拟。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：基于 DNA shape 的跨物种 TF 结合预测迁移
- **名称**：Cross-species transfer of DNA shape-based TF binding predictors
- **来源局限/观察**：本文仅在拟南芥中验证，未测试 shape 特征的跨物种普适性
- **核心假设**：DNA shape 对 TF 结合的贡献在物种间保守，shape 特征模型可迁移到其他物种（如人类、水稻）
- **增量**：将本文的随机森林 + shape 流程应用于人类 TF 数据（如 ENCODE ChIP-seq 或 HT-SELEX），比较跨物种迁移性能
- **初步方法**：用拟南芥训练的模型直接预测人类 TF 结合，或进行迁移学习微调
- **验证方式**：AUPRC 比较 + 跨物种 motif 匹配分析
- **创新状态**：unverified

### 候选 2：Shape 特征与深度学习序列模型的融合
- **名称**：Hybrid sequence-shape deep learning for TF binding prediction
- **来源局限/观察**：本文用随机森林 + shape 特征，未与深度序列模型比较或融合
- **核心假设**：将 DNA shape 特征作为辅助输入注入 CNN/Transformer，可超越纯序列模型
- **增量**：设计双通道架构（序列 embedding + shape 特征），在本文的 216 个 TF 数据上比较
- **初步方法**：在 DeepBind 或 Enformer 架构基础上增加 shape 特征输入通道
- **验证方式**：与纯序列模型和纯 shape 模型比较 AUPRC
- **创新状态**：unverified

### 候选 3：用 MD 模拟验证 shape 特征的物理基础
- **名称**：Molecular dynamics validation of DNA shape features in TF binding
- **来源局限/观察**：本文的 shape 特征来自统计查询表，未经过物理模拟验证
- **核心假设**：查询表预测的 shape 特征在原子级 MD 模拟中可复现，且 shape 特征与结合自由能相关
- **增量**：选取若干高/低预测亲和力的位点，进行 MD 模拟，比较 shape 特征的动态行为
- **初步方法**：对 5-10 个 TF 结合位点进行 μs 级 MD 模拟，计算 shape 特征的时间平均与涨落
- **验证方式**：MD 计算的 shape 与查询表预测的相关性；shape 特征与 MM-PBSA 结合自由能的相关性
- **创新状态**：unverified

### 候选 4：TF 家族内 shape 偏好差异的系统图谱
- **名称**：Systematic atlas of DNA shape preferences across TF families
- **来源局限/观察**：本文仅展示了少数家族的 shape 差异（ERF/AP2、NAC），未系统覆盖所有家族
- **核心假设**：每个 TF 家族（甚至每个成员）有独特的 shape 偏好谱，可用于预测 TF 的功能分化
- **增量**：为 216 个 TF 生成完整的 shape 特征重要性图谱，聚类分析家族内/间模式
- **初步方法**：从本文的 SHAP 值中提取每个 TF 的特征重要性向量，进行聚类和功能富集分析
- **验证方式**：聚类结果与 TF 家族系统发育、已知功能注释的对应关系
- **创新状态**：partially checked（本文已有部分数据，但未做系统聚类分析）

### 候选 5：Shape 感知的合成启动子设计
- **名称**：Shape-aware design of synthetic promoters for precise TF recruitment
- **来源局限/观察**：本文证明 shape 影响结合，但未探索其在合成生物学中的应用
- **核心假设**：通过操纵结合位点的 shape 特征（而非仅序列），可精细调控 TF 结合亲和力
- **增量**：提出「shape 密码」概念，设计具有目标 shape 特征的合成结合位点
- **初步方法**：用本文的模型作为评分函数，进行序列设计（如遗传算法或梯度优化），生成高/低亲和力变体
- **验证方式**：EMSA 或报告基因实验验证设计序列的结合差异
- **创新状态**：unverified