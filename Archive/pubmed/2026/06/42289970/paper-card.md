## 01 基本信息
- **标题**：GRNContext: an interactive web platform for contextualized gene regulatory networks visualization across human cancers
- **作者与单位**：Pezoa-Soto, Ignacio; Hernandez-Galaz, Sergio; De Las Rivas, Javier; Lladser, Alvaro; Varas-Godoy, Manuel; Martin, Alberto J M（Centro Ciencia & Vida, Chile 等，具体单位未提供）
- **期刊/预印本平台**：Bioinformatics (Oxford, England)
- **年份**：2026-06-15（在线发表日期）
- **论文类型**：方法/资源型（Web 平台 + 数据库）
- **领域**：基因调控网络（GRN）、癌症转录组学、生物信息学平台
- **关键词**：Gene Regulatory Networks, Transcription Factors, Cancer, TCGA, Web Platform, Context-specific
- **DOI/arXiv 号**：10.1093/bioinformatics/btag389
- **代码**：https://doi.org/10.5281/zenodo.18355998
- **数据**：TCGA 33 种癌症类型 bulk RNA-Seq（9927 样本）；TFLink 人类参考 GRN（19 599 节点，1605 TF，>670 万边）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/深度学习」方向的**下游应用与资源整合**环节。它不直接预测 TF–DNA 结合位点或物理互作，而是利用已有参考 GRN（TFLink，含 TF–DNA 结合证据）作为先验，结合 TCGA 转录组数据，通过机器学习（Random Forest）与统计方法（Spearman 相关）推断**在特定癌症背景下哪些 TF–靶基因互作是活跃的**。其核心贡献在于**上下文（context）特异性**的 GRN 推断与可视化，而非新的结合机制发现。对本课题的可迁移价值在于：如何将静态 TF–DNA 结合知识转化为动态、条件依赖的调控网络，以及如何用集成评分（consensus score）融合多种互补信号。

## 02 一句话总结
本文构建了一个名为 GRNContext 的交互式 Web 平台，以 TFLink 人类参考 GRN 为骨架，整合 TCGA 33 种癌症类型的转录组数据，通过 Random Forest 回归与 Spearman 相关分析计算 consensus score，为每个基因在每种癌症中筛选并可视化最可能的转录调控因子，从而将静态 TF–DNA 结合知识转化为癌症背景下的条件性调控网络。

## 03 研究问题
- **具体问题**：现有 GRN 数据库（如 TFLink）整合了来自多种实验系统的 TF–靶基因互作证据，但这些互作是「可能的」而非「在特定背景下活跃的」。在癌症中，转录程序具有组织特异性，因此需要一种方法来判断**在特定癌症类型中，哪些 TF–靶基因互作是实际活跃的**。
- **为什么重要**：癌症的转录失调具有高度组织特异性，静态参考 GRN 无法区分哪些调控关系在特定肿瘤中起作用。若能提供上下文特异的 GRN，将有助于机制研究、假设生成和转化医学。
- **现有方法不足**：已有的上下文特异 GRN 资源（如 GRAND、aracne.networks、MOMA）虽然基于 TCGA 等大数据集，但主要以计算包或复杂数据集形式分发，需要较强的生物信息学技能，对实验生物学家不友好。
- **精确研究问题**：Can we build an accessible, interactive platform that infers and visualizes cancer-type-specific TF–target gene regulatory interactions by integrating a reference GRN with TCGA transcriptomic profiles?

## 04 背景与发展脉络
*注：以下脉络基于本文引言，标注为「仅本文框架」，未经外部系统核验。*

1. **阶段一：静态参考 GRN 数据库**（如 TFLink、TRRUST、ENCODE 等）
   - 代表性方法：整合多种实验证据（ChIP-seq、文献、基序预测等）构建全基因组 TF–靶基因互作图。
   - 优点：全面、覆盖广。
   - 局限：不区分生物学上下文，无法反映特定组织/疾病状态下的活跃调控。

2. **阶段二：数据驱动的上下文特异 GRN 推断**
   - 代表性方法：GRAND（Ben Guebila et al. 2022）、aracne.networks（Giorgi 2017）、MOMA（Paull et al. 2021）。
   - 优点：利用 TCGA 等大规模转录组数据，推断特定癌症中的调控网络。
   - 局限：以计算包/数据集形式分发，使用门槛高；缺乏交互式可视化；对实验生物学家不友好。

3. **阶段三（本文位置）：上下文特异 GRN + 交互式 Web 平台**
   - 本文主张：以 TFLink 为参考骨架，结合 TCGA 表达数据，用 RF + Spearman 生成 consensus score，并通过 Web 平台实现低门槛的交互式可视化和跨癌症比较。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 参考 GRN 缺乏上下文信息 | 数据库列出所有可能的 TF–靶基因互作，但无法告知哪些在特定癌症中活跃 | 参考 GRN 整合了多种实验系统的证据，不区分组织/疾病状态 | Introduction 第 1 段 |
| 现有上下文特异资源使用门槛高 | GRAND、aracne.networks、MOMA 等以计算包或复杂数据集形式分发 | 需要编程技能和计算基础设施，实验生物学家难以直接使用 | Introduction 第 2 段 |
| 缺乏交互式可视化 | 已有资源难以直观探索和比较不同癌症中的调控模式 | 未提供用户友好的图形界面 | Introduction 第 2 段、第 3 段 |
| 单一方法可能不可靠 | 单一统计或机器学习方法可能对特定数据分布敏感 | 作者采用 RF + Spearman 互补方法并统一为 consensus score | Methods 2.3 节 |

## 06 核心思想
1. **表面方法**：以 TFLink 人类参考 GRN 为骨架，对每个基因在每种癌症中构建 Random Forest 回归模型（以已知 TF 表达为特征预测靶基因表达），同时计算 Spearman 相关，将两种信号经 Z-score 归一化和 min-max 缩放后融合为 consensus score，用 elbow method 自动选择每基因的最优调控因子数量，并提供 Top 5/10/20/30/40/50 的过滤版本。
2. **核心洞察**：静态 TF–DNA 结合知识（参考 GRN）与条件性转录组数据（TCGA）的结合，可以将「可能的调控」转化为「在特定癌症中活跃的调控」。RF 捕捉非线性、非单调的调控关系，Spearman 捕捉单调关系，两者互补，consensus score 提供稳健的排序。
3. **可能的普适教训** [Analysis]：在 TF–DNA 互作研究中，**先验知识（如 ChIP-seq 结合位点、基序预测）与条件性功能数据（如表达谱、ATAC-seq）的整合**，比单独使用任何一种数据更能揭示上下文依赖的调控逻辑。Consensus score 的思路（多种互补信号归一化后融合）可迁移到其他评分任务（如结合位点优先级排序、增强子-启动子互作打分）。

## 07 方法总览
- **输入**：
  - TFLink 人类参考 GRN（19 599 节点，1605 TF，>670 万边）
  - TCGA 33 种癌症类型 bulk RNA-Seq 原始计数矩阵（9927 样本）
- **输出**：
  - 每种癌症中每个靶基因的排序 TF 列表（含 consensus score）
  - 交互式 Web 可视化（Cytoscape.js 网络图，支持边权重、consensus score、跨癌症保守性等覆盖层）
  - 6 种过滤版本（Top 5/10/20/30/40/50）及 elbow method 自动版本
- **模块**：
  1. 数据预处理：TMM 归一化（edgeR），过滤低表达基因（median < 10）
  2. 调控推断：对每个基因-癌症对，构建 RF 回归模型（输入=已知 TF 表达，输出=靶基因表达），提取特征重要性；并行计算 Spearman 相关
  3. 评分融合：Z-score 归一化 + min-max 缩放（0-1），融合为 consensus score
  4. 阈值选择：elbow method 自动确定每基因的调控因子数量
  5. 保守性计算：跨 33 种癌症计算调控边保守性
  6. Web 平台：FastAPI 后端（解析 SIF 文件，REST API）+ React 前端（Cytoscape.js 可视化），Docker 容器化
- **训练**：RF 回归模型（每基因-癌症对独立训练），无显式超参数调优描述
- **反馈回路**：无（静态推断，非迭代优化）
- **假设**：TFLink 中的 TF–靶基因关系是真实的潜在互作；TCGA 表达数据能反映调控活性；RF 特征重要性与 Spearman 相关能捕捉调控信号

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| TFLink 参考 GRN 过滤 | 限定每个靶基因的候选 TF 集合 | 减少搜索空间，利用已有 TF–DNA 结合知识 | 输入：TFLink 全 GRN；输出：每基因的已知 TF 列表 | Methods 2.2 节 | 预期影响：移除后需从头推断所有 TF–基因关系，计算量剧增且假阳性升高 [预期效应] |
| RF 回归模型 | 量化每个 TF 对靶基因表达的预测贡献 | 捕捉非线性、多因子协同的调控关系 | 输入：候选 TF 表达矩阵 + 靶基因表达；输出：特征重要性分数 | Methods 2.3 节 | 预期影响：移除后仅剩线性相关信号，可能遗漏非线性调控 [预期效应] |
| Spearman 相关分析 | 量化 TF 与靶基因的单调关联 | 补充 RF 未捕捉的线性/单调信号，提供方向性信息 | 输入：TF 表达 + 靶基因表达；输出：相关系数 | Methods 2.3 节 | 预期影响：移除后 consensus score 仅依赖 RF，可能对异常值更敏感 [预期效应] |
| Consensus score 融合 | 统一 RF 与 Spearman 信号为单一排序指标 | 综合互补信号，提高稳健性 | 输入：RF 重要性 + Spearman 相关；输出：0-1 分数 | Methods 2.3 节 | 预期影响：移除后需选择单一指标，可能降低排序可靠性 [预期效应] |
| Elbow method 阈值选择 | 自动确定每基因的调控因子数量 | 避免人为设定固定阈值，数据驱动 | 输入：consensus score 排序；输出：最优截断点 | Methods 2.3 节 | 预期影响：移除后需手动设定 Top N，可能引入主观偏差 [预期效应] |
| 跨癌症保守性计算 | 量化调控边在 33 种癌症中的重现性 | 识别核心 vs 癌症特异的调控 | 输入：各癌症 consensus score；输出：保守性指标 | Methods 2.3 节、Results 3.1 节 | 预期影响：移除后无法区分核心调控与癌症特异调控 [预期效应] |
| Web 可视化平台 | 交互式探索网络 | 降低使用门槛，支持假设生成 | 输入：SIF 文件 + 用户查询；输出：交互式网络图 | Methods 2.4 节、Figure 1 | 预期影响：移除后平台退化为静态数据集，失去易用性优势 [预期效应] |

## 09 关键公式符号
本文未提供显式数学公式。核心评分逻辑可描述为：

- **Consensus score**：对每个 TF-靶基因对 (i, j) 在癌症 c 中：
  - 计算 RF 特征重要性分数 \( RF_{ijc} \)
  - 计算 Spearman 相关系数 \( \rho_{ijc} \)
  - 分别进行 Z-score 归一化：\( Z_{RF} = (RF_{ijc} - \mu_{RF}) / \sigma_{RF} \)，\( Z_{\rho} = (\rho_{ijc} - \mu_{\rho}) / \sigma_{\rho} \)
  - 再经 min-max 缩放至 [0, 1]：\( S_{RF} = (Z_{RF} - \min Z_{RF}) / (\max Z_{RF} - \min Z_{RF}) \)，\( S_{\rho} \) 同理
  - 最终 consensus score：\( C_{ijc} = (S_{RF} + S_{\rho}) / 2 \)（或加权组合，原文未明确权重）

*注：以上公式为 [Analysis] 基于 Methods 2.3 节文字描述的合理重构，原文未给出具体数学表达式。*

## 10 实验设计与证据链
- **数据集**：TCGA 33 种癌症类型 bulk RNA-Seq（9927 样本）；TFLink 人类参考 GRN（19 599 节点，1605 TF，>670 万边）
- **指标**：无定量评测指标（如 AUROC、精确率等）；主要依赖案例验证和文献一致性
- **基线**：无显式基线对比
- **预算**：未提供
- **骨干/仪器**：未提供
- **oracle 输入**：TFLink 参考 GRN 作为先验知识（oracle-like）
- **评测协议**：案例研究（PTTG1 在 LIHC、RAB31 在 OV），与已发表文献进行定性比较

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| PTTG1 在 LIHC 的调控因子识别 | 平台能识别已知的 PTTG1 调控因子 | Top 5 调控因子 vs 文献报道 | FOXM1 和 E2F1 被识别为 Top 调控因子，与肝癌中已知调控一致 | 平台能有效恢复已知调控关系 | 不能证明平台优于其他方法；仅单一案例 | Results 3.1 节 |
| PTTG1 调控保守性分析 | 核心调控因子跨癌症保守 | Top 5 TF 在 33 种癌症中的出现频率 | H2AZ1 在 24 种癌症中出现，E2F1 在 12 种，FOXM1/MYBL2 在 11 种 | PTTG1 受核心保守调控网络控制 | 保守性高不等于功能重要性 | Results 3.1 节 |
| RAB31 在 OV 的调控因子识别 | 平台能预测未在 OV 中验证的调控关系 | Top 调控因子 vs 跨上下文文献证据 | RUNX1 被预测为 RAB31 调控因子，在巨核细胞中有实验验证 | 平台能生成跨上下文的可检验假设 | 缺乏 OV 直接实验验证 | Results 3.2 节 |
| 全局保守性统计 | 大多数调控是癌症特异的 | 835 367 条边中 68.45% 仅出现在单一癌症 | 571 784 条边为单一癌症特有，仅 1085 条（0.13%）在 ≥24 种癌症中保守 | 调控网络高度上下文特异 | 未提供统计显著性检验 | Results 3.1 节 |

## 11 结论正确解读
- **任务范围**：本文构建的是**上下文特异的 GRN 推断与可视化平台**，而非新的 TF–DNA 结合机制发现工具。其输出是「在特定癌症中，哪些已知 TF–靶基因关系最可能活跃」的排序。
- **oracle/真值输入**：TFLink 参考 GRN 作为先验知识输入，其本身整合了多种实验证据，但可能包含假阳性/假阴性。
- **端到端状态**：平台已上线可用（https://apps.cienciavida.org/grncontext），但**未经过独立的基准测试**（如与 GRAND、ARACNe 等方法的定量比较）。
- **算力成本**：未提供；RF 模型按基因-癌症对独立训练，计算量较大但可并行化。
- **历史数据依赖**：完全依赖 TCGA 的 bulk RNA-Seq 数据，无法区分细胞类型异质性；TFLink 的参考 GRN 可能偏向研究充分的 TF。
- **模型依赖**：RF 特征重要性与 Spearman 相关均为相关性度量，不能证明因果关系；consensus score 的权重组合未公开。
- **最难情形**：低表达基因、样本量小的癌症类型、TF 表达高度共线性的情况。
- **群体/领域边界**：仅覆盖 TCGA 的 33 种癌症类型；不包含正常组织（未来计划加入 GTEx）；不包含单细胞分辨率。
- **不确定性**：未提供置信区间或统计检验；elbow method 的选择可能不稳定。
- **有边界的复述**：GRNContext 是一个基于 TFLink 先验和 TCGA 表达数据的交互式平台，能生成 33 种癌症类型中每个基因的排序调控因子列表，并通过案例验证其能恢复已知调控关系、生成跨上下文假设，但其预测的调控关系未经实验验证，且未与其他 GRN 推断方法进行系统比较。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 仅覆盖 TCGA 癌症类型 | 不包含正常组织 | 计划整合 GTEx 数据以表征正常组织中的 GRN | Future plans 节 |
| 缺乏单细胞分辨率 | 基于 bulk RNA-Seq，无法解析细胞类型特异性调控 | 计划开发单细胞 GRN 生成协议 | Future plans 节 |
| 物种限制 | 仅人类 | 计划整合 ARCHS4 以纳入小鼠表达谱 | Future plans 节 |
| 依赖参考 GRN 先验 | TFLink 的覆盖度和质量影响下游推断 | 未明确提及 | [Analysis] 基于 Methods 2.2 节的推断 |

**作者提及的相关约束**（非正式局限）：平台为静态推断，不包含动态调控或表观遗传信息；consensus score 的权重组合未公开细节。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 无定量基准测试 | 平台可能不如现有方法（如 GRAND、ARACNe）准确，但作者未进行比较 | 用户无法判断该工具的相对优劣 | 在相同 TCGA 数据上运行 GRAND、ARACNe 等方法，比较排序一致性或下游验证率 | Methods 节未提及任何基准 |
| 案例验证存在选择性偏差 | PTTG1 和 RAB31 可能是作者预先知道有文献支持的基因 | 无法评估平台在未知案例上的表现 | 随机选择基因进行盲测，或使用留一法交叉验证 | Results 3.1、3.2 节仅两个案例 |
| RF 特征重要性的可解释性 | RF 特征重要性可能受特征共线性影响，且不提供方向性 | 用户可能误读特征重要性为因果效应 | 与 SHAP 值或其他可解释性方法对比 | Methods 2.3 节未讨论 |
| Consensus score 的权重未公开 | 无法复现或评估权重选择的合理性 | 科学可复现性受损 | 要求作者公开权重或提供敏感性分析 | Methods 2.3 节仅描述归一化流程 |
| 保守性计算缺乏统计检验 | 0.13% 的保守边比例可能受 TFLink 覆盖度偏差影响 | 可能高估或低估调控的保守性 | 对 TFLink 的 TF 覆盖度进行分层分析 | Results 3.1 节仅提供描述性统计 |
| 未考虑表观遗传状态 | 仅用表达数据推断调控，未整合染色质可及性、甲基化等 | 可能遗漏关键的调控机制 | 在部分案例中整合 ATAC-seq 或 ChIP-seq 数据验证 | Methods 节未提及表观遗传数据 |

## 14 学到什么
**Agent 提炼的知识候选**

1. **先验知识 + 条件数据的整合框架**：本文展示了如何将静态 TF–DNA 结合知识（TFLink）与条件性表达数据（TCGA）结合，推断上下文特异的调控活性。**可迁移到本课题**：在预测 TF–DNA 结合时，可类似地将 ChIP-seq 基序信息（先验）与细胞类型特异的 ATAC-seq/表达数据（条件）结合，构建条件依赖的结合预测模型。

2. **Consensus score 的多信号融合策略**：RF（非线性）+ Spearman（单调）两种互补信号经归一化后融合为单一评分。**可迁移到本课题**：在 TF–DNA 结合预测中，可融合结构特征（如 PDB 接触图）、序列特征（如 PWM 打分）和进化保守性等多种信号，通过归一化后加权融合提高预测稳健性。

3. **Elbow method 的自适应阈值选择**：用数据驱动方式确定每基因的调控因子数量，避免固定阈值。**可迁移到本课题**：在筛选显著 TF–DNA 互作时，可用 elbow method 确定结合位点打分阈值，而非依赖任意 p-value 截断。

4. **跨上下文保守性分析**：通过跨 33 种癌症计算调控保守性，区分核心调控与上下文特异调控。**可迁移到本课题**：在 TF–DNA 结合研究中，可跨细胞类型或物种比较结合事件，识别保守结合位点（功能性）与物种/细胞特异结合位点。

5. **Web 平台的可访问性设计**：以交互式可视化降低使用门槛，使计算资源对实验生物学家可及。**可迁移到本课题**：将 TF–DNA 结合预测模型封装为类似 Web 工具，支持用户输入序列/结构并可视化预测结果。

6. **TFLink 作为参考 GRN 的利用**：TFLink 整合了多种数据库的 TF–靶基因证据，可作为先验网络。**可迁移到本课题**：在构建 TF–DNA 结合预测模型时，可用 TFLink 作为正例集来源，或作为负例集筛选的参考。

## 15 与已有知识连接
- **TFLink (Liska et al. 2022)**：本文的参考 GRN 来源。TFLink 整合了 10 个数据库的 TF–靶基因证据，是 TF–DNA 互作领域的重要资源。与本课题直接相关：可作为训练数据或先验知识。
- **GRAND (Ben Guebila et al. 2022)**：本文引用的上下文特异 GRN 资源之一。GRAND 使用类似思路（TCGA + 参考网络）推断癌症特异调控。与本课题相关：可比较不同推断策略的优劣。
- **ARACNe (Giorgi 2017)**：基于互信息的 GRN 推断方法。本文将其列为现有资源但未使用。与本课题相关：互信息方法可作为 consensus score 的替代或补充信号。
- **TCGA (Weinstein et al. 2013)**：本文的数据来源。TCGA 是癌症基因组学最全面的公共资源，包含 33 种癌症类型的多组学数据。与本课题相关：可用于验证 TF–DNA 结合预测的临床相关性。
- **Cytoscape.js**：前端可视化库。与本课题相关：可用于展示 TF–DNA 互作网络或结合位点图谱。
- **Random Forest 回归**：本文的核心 ML 方法。在 TF–DNA 结合预测中，RF 已被广泛用于整合序列和结构特征（如 DeepBind 之前的经典方法）。
- **Spearman 相关**：本文的统计方法。在基因共表达网络分析中常用，可补充 ML 方法的线性信号。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：Context-Aware TF–DNA Binding Prediction via Multi-Omics Integration
   - **来源局限/观察**：GRNContext 仅用表达数据推断调控活性，未整合染色质可及性（ATAC-seq）或组蛋白修饰（ChIP-seq），而这些是 TF 结合的直接前提。
   - **核心假设**：整合染色质可及性、TF 基序和表达数据，可显著提高 TF–DNA 结合位点的上下文特异预测精度。
   - **初步方法**：以 TFLink 互作作为先验，对每个 TF-靶基因对，提取 (a) 启动子/增强子区域的 ATAC-seq 信号，(b) TF 基序匹配强度，(c) TF 与靶基因的表达相关性，构建多模态特征，用梯度提升机或深度学习模型预测结合活性。
   - **验证方式**：在独立 ChIP-seq 数据集上验证预测的结合位点；比较与仅用表达数据的方法（如 GRNContext）的 AUC 差异。
   - **创新状态**：unverified

2. **候选名称**：Consensus Score with Structural Priors for TF–DNA Interaction Ranking
   - **来源局限/观察**：GRNContext 的 consensus score 仅基于表达数据，未利用 TF–DNA 结合的结构信息（如 AlphaFold3 预测的 TF-DNA 复合物结构或 PDB 实验结构）。
   - **核心假设**：将结构预测评分（如 AlphaFold3 的 pLDDT 或 docking 能量）作为先验权重加入 consensus score，可优先排序结构上更可能结合的 TF-靶基因对。
   - **初步方法**：对 TFLink 中的高置信 TF-靶基因对，用 AlphaFold3 预测 TF-DNA 复合物结构，提取结合界面评分；将结构评分与表达推断的 consensus score 加权融合，重新排序。
   - **验证方式**：在已知的癌症驱动 TF-靶基因对（如 MYC 靶基因）上检查排序提升；与仅用表达数据的方法比较 top-K 命中率。
   - **创新状态**：unverified

3. **候选名称**：Cross-Cancer Conserved vs. Specific TF–DNA Regulatory Modules
   - **来源局限/观察**：GRNContext 提供了跨 33 种癌症的保守性数据，但未深入分析保守调控模块的功能意义。
   - **核心假设**：跨癌症高度保守的 TF-靶基因模块对应核心细胞功能（如细胞周期），而癌症特异的模块对应组织特异的致癌程序。
   - **初步方法**：利用 GRNContext 的保守性数据，将 TF-靶基因对分为保守组和特异组，进行 GO/KEGG 富集分析，比较两组的功能差异；结合生存分析验证特异模块的预后价值。
   - **验证方式**：在 TCGA 临床数据上检验特异模块与患者生存的关联；在独立数据集（如 GEO）上验证模块重现性。
   - **创新状态**：unverified

4. **候选名称**：Single-Cell GRN Contextualization Using GRNContext Framework
   - **来源局限/观察**：GRNContext 基于 bulk RNA-Seq，无法解析细胞类型或状态特异的调控。
   - **核心假设**：将 GRNContext 的推断框架扩展到单细胞数据，可识别细胞类型特异的 TF–DNA 调控网络。
   - **初步方法**：对单细胞 RNA-seq 数据，按细胞类型聚类后，对每个簇应用 RF + Spearman 的 consensus score 流程，生成细胞类型特异的 GRN。
   - **验证方式**：在已知细胞类型标记基因的调控网络上验证；与 SCENIC 等单细胞 GRN 方法比较。
   - **创新状态**：unverified

5. **候选名称**：GRNContext-Inspired Benchmark for TF–DNA Binding Prediction Methods
   - **来源局限/观察**：GRNContext 未与其他 GRN 推断方法进行系统比较，缺乏基准。
   - **核心假设**：基于 TCGA + TFLink 的 consensus score 可作为评估 TF–DNA 结合预测方法的基准数据集。
   - **初步方法**：将 GRNContext 的 consensus score 作为弱标签，评估现有 TF–DNA 结合预测工具（如 DeepBind、DeepSEA、AlphaFold3）在癌症上下文中的表现。
   - **验证方式**：比较各方法在 consensus score 高/低分组上的区分度；用 ChIP-seq 数据作为金标准验证。
   - **创新状态**：unverified