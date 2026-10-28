## 01 基本信息

- **标题**：Predicting transcriptional regulators in plants in the era of artificial intelligence
- **作者**：Ko, Dae Kwan; Brandizzi, Federica
- **单位**：未提供（据基金信息推测为 Michigan State University / MSU-DOE Plant Research Laboratory 相关机构，但原文未明确标注）
- **期刊/平台**：Current Opinion in Plant Biology
- **年份**：2026（在线日期 2026-08-26）
- **论文类型**：综述（Review）
- **领域**：植物转录调控、基因调控网络（GRN）、多组学整合、AI/机器学习/深度学习
- **关键词**：转录因子（TF）、顺式调控元件（CRE）、基因调控网络（GRN）、多组学、机器学习、深度学习、基础模型（foundation models）
- **DOI/arXiv**：10.1016/j.pbi.2026.102955
- **代码**：未提供
- **数据**：未提供（综述性论文，无原始数据）
- **阅读日期**：2026-08-26
- **在课题方向中的位置**：本文是植物 TF–DNA 结合机制与 AI 方法交叉方向的综述，系统梳理了从共表达网络到 GRN 推断、再到多组学整合与深度学习/基础模型在植物转录调控预测中的应用。对「蛋白质-DNA 互作 × AI」课题读者而言，本文提供了植物体系下 TF–靶基因预测的方法谱系、代表性工具（GENIE3、WGCNA、MINI-EX、MINI-AC、NEEDLE、DeFine、TADA、AlphaFold、ESM、AgroNT、PlantCaduceus 等）及当前挑战，可作为方法选型与课题定位的参考框架。

## 02 一句话总结

本文综述了植物转录调控预测从单基因研究到网络级分析、再到多组学整合与 AI/深度学习/基础模型驱动的发展历程，指出当前核心挑战在于将描述性 GRN 重建推进为可预测 TF–靶基因响应（如遗传扰动或环境变化）的机制性模型。

## 03 研究问题

- **具体问题**：如何从日益复杂和高维的组学数据中准确识别植物中控制重要生物学通路的转录调控因子（TF）及其靶基因，并进一步构建可预测的调控模型？
- **为什么重要**：TF–DNA 结合是植物发育、生长、生理和环境响应的核心调控层。识别 TF 靶基因是理解调控机制、网络层级和表型变异的基础，对作物改良和合成生物学有直接应用价值。
- **现有方法为何不足**：
  - 共表达网络无法区分直接/间接调控关系，缺乏方向性；
  - 单一组学数据（如仅转录组）信息量有限，难以捕捉染色质状态、TF 结合等关键调控层；
  - 传统统计方法难以学习高维数据中的非线性、上下文依赖的调控模式；
  - 植物体系缺乏足够大且注释良好的训练数据集，基础模型在植物中的成熟度远低于动物体系。
- **精确研究问题（Can 句式）**：Can AI-driven multi-omics integration move plant transcriptional regulator prediction beyond descriptive GRN reconstruction toward predictive, mechanism-aware models that forecast TF–target responses to genetic or environmental perturbations?

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注为「仅本文框架」，未经外部系统核验。

| 阶段 | 代表性方法/技术 | 优点 | 局限 | 本文主张的位置 |
|---|---|---|---|---|
| 单基因研究时代 | 经典遗传学、酵母双杂交、电泳迁移率变动分析（EMSA）等 | 直接、机制明确 | 通量低，无法覆盖全基因组 | 背景铺垫 |
| 转录组学/共表达网络时代 | RNA-seq、WGCNA | 可大规模缩小候选基因列表，模块化分析稳健易实现 | 无法区分直接/间接调控，无方向性 | 网络级基因发现的基石 |
| GRN 推断时代 | GENIE3（树模型）、GENIST（概率图模型）、回归/信息论方法 | 提供有方向的 TF–靶基因关系 | 需要大量过滤与整合，噪声敏感，易产生假阳性 | 从共表达到有向调控的过渡 |
| 多组学整合时代 | ChIP-seq、DAP-seq、DNase-seq、ATAC-seq、单细胞/空间转录组 | 提供 TF 结合、染色质可及性、细胞类型特异性等多层证据 | 数据整合复杂，不同组学间异质性大 | 提升预测精度的关键 |
| AI/深度学习时代 | XGBoost、Random Forest、SVM、CNN（如 DeFine）、Transformer、基础模型（AgroNT、PlantCaduceus）、结构预测（AlphaFold）、蛋白语言模型（ESM） | 可学习非线性、高维、上下文依赖模式 | 数据需求大、可解释性差、植物训练数据不足、跨物种迁移受限 | 当前前沿与未来方向 |

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 共表达无法区分直接/间接调控 | 共表达网络中的基因可能因间接效应或共同上游调控而共表达，无法确定 TF 是否直接结合靶基因 | 共表达基于相关性，不包含调控方向或物理结合信息 | Introduction 与 Network-enabled gene discovery 节：「coexpression alone cannot distinguish direct from indirect relationships and therefore does not define regulatory directionality」 |
| GRN 推断噪声大、假阳性高 | 从大型转录组数据推断的 TF–靶基因关系需要大量过滤和整合才能产生生物学上有意义的结果 | 数据维度高、样本量有限、调控关系上下文依赖 | Network-enabled gene discovery 节：「large transcriptional and regulatory datasets often require substantial filtering and integration before biologically meaningful TF–target relationships emerge」 |
| 单一组学信息不足 | 仅用表达数据预测靶基因精度有限 | 转录调控涉及 TF 结合、染色质可及性、表观遗传等多层因素 | Multi-omics 节：「transcriptional regulation depends on several interacting molecular layers」 |
| 植物 AI 训练数据不足 | 基础模型和深度学习在植物中的成熟度低于动物体系 | 植物调控基因组学缺乏大规模、注释良好的训练数据集 | AI 节：「plant regulatory genomics still lacks sufficiently large and well-annotated training datasets」 |
| 模型跨上下文迁移困难 | 基因调控高度依赖组织、发育阶段和环境条件，模型泛化受限 | 调控的上下文依赖性 | AI 节：「gene regulation is highly context dependent across tissues, developmental stages, and environmental conditions, complicating model transferability」 |
| 基础模型未必优于简单基线 | 单细胞扰动响应模型在基准测试中并不总是优于简单基线 | 模型复杂度与数据量/任务匹配度问题 | AI 节：「recent benchmarks of single-cell perturbation-response models show that they do not always outperform simple baselines」 |

## 06 核心思想

1. **表面方法**：本文是一篇综述，系统梳理了植物转录调控因子预测的方法演进——从共表达网络（WGCNA）、GRN 推断（GENIE3、GENIST）、多组学整合（ChIP-seq、DAP-seq、ATAC-seq、单细胞/空间转录组），到 AI/ML/深度学习（XGBoost、CNN、Transformer）与基础模型（AgroNT、PlantCaduceus、AlphaFold、ESM）的应用，并讨论了这些方法如何逐步提升 TF–靶基因预测的精度与可扩展性。

2. **核心洞察**：植物转录调控预测正从「描述性网络重建」转向「预测性机制建模」。真正的突破不在于单一方法或单一组学，而在于**多层数据的系统整合**（TF 结合 + 染色质可及性 + 表达动态 + 序列特征）与 **AI 对非线性、上下文依赖模式的学习能力**相结合。同时，作者强调 AI 方法需要严格的植物特异性评估——不能想当然认为复杂模型一定优于简单基线。

3. **可能的普适教训** [Analysis]：对于「蛋白质-DNA 互作 × AI」课题，本文隐含一个方法论教训：**预测精度的提升来自「物理约束（如 TF 结合、染色质可及性）+ 统计学习（如共表达、GRN 推断）+ AI 非线性建模」的三层叠加**，而非任何单一方法的胜利。此外，跨物种迁移（如拟南芥→作物）需要进化保守性作为先验知识，这与 TF–DNA 结合机制研究中「motif 保守性」的思路一致。

## 07 方法总览

> 本文为综述，无统一方法流程。以下按文中描述的各方法类别整理其输入-输出逻辑。

- **输入**：转录组数据（bulk RNA-seq、单细胞 RNA-seq）、染色质可及性数据（ATAC-seq、DNase-seq）、TF 结合数据（ChIP-seq、DAP-seq）、基因组序列、TF motif 数据库、遗传扰动数据（CRISPR 等）
- **输出**：TF–靶基因关系（有向/无向）、候选调控因子排序、调控网络、TF 结合位点预测、基因表达预测、调控变异功能注释
- **模块/方法类别**：
  1. 共表达网络（WGCNA）：输入表达矩阵 → 输出基因模块与共表达关系
  2. GRN 推断（GENIE3、GENIST）：输入表达矩阵 + TF 列表 → 输出有向 TF–靶基因边
  3. 多组学整合（MINI-EX、MINI-AC）：输入表达 + motif + 染色质可及性 → 输出细胞类型特异或染色质可及性约束的调控网络
  4. 传统 ML（XGBoost、RF、SVM）：输入特征矩阵（表达、序列、保守性等）→ 输出基因分类或候选排序
  5. 深度学习（CNN 如 DeFine、Transformer）：输入序列/染色质特征 → 输出 TF 结合强度、调控变异优先级
  6. 基础模型（AgroNT、PlantCaduceus、DNA 语言模型）：输入基因组序列 → 输出调控注释、表达预测、变异效应
  7. 结构预测/蛋白语言模型（AlphaFold、ESM）：输入蛋白序列 → 输出结构/功能特征，辅助 TF 功能推断
- **反馈回路**：文中提及「预测 → 实验验证 → 网络修正」的迭代模式（如 NEEDLE 流程中 in silico 预测后经实验验证），但未详述闭环机制
- **假设**：共表达假设功能相关基因共表达；GRN 推断假设表达动态可反映调控关系；多组学整合假设物理结合（ChIP/DAP）与功能调控（表达变化）的交集更接近真实靶基因

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 共表达网络（WGCNA） | 从表达数据中识别共表达基因模块，缩小候选范围 | 将数千基因缩减为可管理的候选集 | 输入：表达矩阵；输出：基因模块 | Network-enabled gene discovery 节：「highly effective for reducing large candidate lists from thousands of genes to a more manageable set」 | 预期影响：失去初步筛选能力，候选基因池过大（[Analysis] 预期效应，原文未做消融） |
| GRN 推断（GENIE3、GENIST） | 推断有向 TF–靶基因调控关系 | 提供超越共表达的调控方向信息 | 输入：表达矩阵 + TF 列表；输出：有向调控边 | Network-enabled gene discovery 节：「seek to identify directional relationships between TFs and their candidate targets」 | 预期影响：失去方向性信息，无法区分上游调控因子与下游效应基因（[Analysis] 预期效应） |
| 多组学整合（MINI-EX、MINI-AC） | 整合单细胞表达、motif、染色质可及性，构建细胞类型特异或染色质约束的 GRN | 单组学预测精度有限，需多层证据交叉验证 | 输入：scRNA-seq + motif + ATAC-seq；输出：细胞类型特异 GRN | Multi-omics 节：「incorporating single-cell expression, TF motif, and chromatin accessibility information」 | 预期影响：失去细胞类型分辨率与染色质约束，预测精度下降（[Analysis] 预期效应） |
| 传统 ML（XGBoost、RF、SVM） | 从特征矩阵学习分类/排序模型，用于基因优先级排序 | 能整合多源特征并学习非线性关系 | 输入：特征矩阵（表达、序列、保守性等）；输出：候选基因排序/分类 | AI 节：Cheng et al. 用 XGBoost 预测氮利用效率相关基因 | 实测效果：Cheng et al. 的模型预测 NUE 相关基因准确率高，且部分预测经实验验证（AI 节） |
| 深度学习（CNN/Transformer） | 从序列或染色质特征学习 TF 结合、表达调控模式 | 能自动学习局部序列特征与调控语法 | 输入：DNA 序列/染色质特征；输出：TF 结合强度、调控变异优先级 | AI 节：DeFine 模型（非植物体系）预测 TF–DNA 结合强度并优先排序功能非编码变异 | 预期影响：失去对序列特征与调控变异的直接建模能力（[Analysis] 预期效应） |
| 基础模型（AgroNT、PlantCaduceus） | 从大规模基因组学习通用调控表征，可适配多种下游任务 | 有望解决植物训练数据不足问题，学习跨物种调控语法 | 输入：基因组序列；输出：调控注释/表达预测/变异效应 | AI 节：「beginning to learn regulatory grammar from large genome collections」 | 预期影响：失去跨物种调控语法先验，模型泛化能力下降（[Analysis] 预期效应） |
| 结构预测/蛋白语言模型（AlphaFold、ESM） | 推断 TF 结构、结构域、蛋白互作界面 | 为 TF 功能推断和调控变异解释提供结构证据 | 输入：蛋白序列；输出：结构/功能特征 | AI 节：「can help infer functional properties of candidate regulators, including domain architecture, protein–protein interaction potential, and possible TF–DNA or TF–cofactor interfaces」 | 预期影响：失去对 TF 结构与互作界面的先验约束（[Analysis] 预期效应） |

## 09 关键公式符号

**不适用。** 本文为综述性论文，未包含数学公式或算法伪代码。文中涉及的模型（GENIE3、XGBoost、CNN、Transformer 等）均为已有方法，原文未给出其数学表述。

## 10 实验设计与证据链

> 本文为综述，无原始实验。以下记录文中引用的代表性研究案例及其证据类型。

- **数据集/群体**：文中提及拟南芥（Arabidopsis）、玉米（maize）等植物体系；具体数据集规模未提供
- **指标**：预测准确率（Cheng et al. 的 NUE 预测）、TF 结合预测能力（DeFine）、实验验证率（NEEDLE 流程）等，具体数值未提供
- **基线**：文中未系统报告基线对比
- **评测协议**：文中提及「in silico 分析 + 实验验证 in planta」的验证模式（NEEDLE），但未详述协议细节

| 实验/案例 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| Cheng et al.：XGBoost 预测氮响应基因与 NUE | ML 可从进化保守的氮响应基因中学习并预测 NUE 相关基因 | 拟南芥 + 玉米保守基因训练；未报告基线对比 | 预测 NUE 相关基因准确率高；部分基因经实验验证 | ML 可有效优先排序复杂性状相关候选基因 | 未证明该方法优于其他 ML 方法或传统统计方法；未报告量化指标 | AI 节 |
| Tu et al.：玉米原生质体 ChIP-seq + ML 预测 TF 结合 | ML 可学习 TF 结合区域特征并全基因组预测结合位点 | 原生质体 ChIP-seq 数据训练；未报告基线 | 可预测 TF 结合与共定位 | ML 可处理 TF 家族内 motif 相似性与上下文依赖问题 | 未报告预测精度与泛化性量化指标 | AI 节 |
| Moore et al.：RF/SVM 区分拟南芥特化代谢基因 | ML 可从序列/表达特征区分基因功能类别 | RF vs SVM；未报告基线 | 可区分特化代谢基因与一般代谢基因 | ML 可用于功能基因类别判别 | 未报告跨物种泛化能力 | AI 节 |
| TADA 网络：预测拟南芥 1,500+ TF 的激活结构域 | 深度学习可从序列预测 TF 转录激活功能 | 1,500+ 拟南芥 TF；未报告基线 | 揭示多种与激活相关的序列特征组合 | 深度学习可预测 TF 功能结构域 | 未报告与实验验证的对照率 | AI 节 |
| NEEDLE 流程：RNA-seq + WGCNA + GENIE3 预测作物 TF 靶基因 | 简化流程可桥接共表达与 GRN 推断 | 作物物种；未报告基线 | 产生可实验验证的 TF–靶基因预测 | 简化流程可降低 GRN 推断门槛 | 未报告预测精度与假阳性率 | Network-enabled gene discovery 节 |

## 11 结论正确解读

- **任务范围**：本文聚焦**植物**（尤其拟南芥与作物）中 TF–靶基因预测的方法学综述，不涉及动物或微生物体系；不涉及 TF–DNA 结合的物理/结构机制细节（如结合动力学、构象变化）。
- **oracle/真值输入**：文中引用的实验验证（如 NEEDLE 的 in planta 验证、Cheng et al. 的实验验证）作为「真值」来源，但未报告验证规模与阳性率。
- **端到端状态**：文中明确表示植物调控预测尚未达到「端到端」的预测性模型状态——当前仍以「候选基因优先排序 + 实验验证」为主，而非直接预测调控响应。
- **算力成本**：未讨论。
- **历史数据依赖**：文中指出植物缺乏大规模、良好注释的训练数据是基础模型应用的主要瓶颈。
- **模型依赖**：文中强调基础模型在植物中的成熟度低于动物体系，且单细胞扰动预测模型在基准测试中未必优于简单基线。
- **最难情形**：上下文依赖的调控（组织/发育/环境特异）、TF 家族内 motif 相似性、跨物种迁移。
- **群体/领域边界**：结论仅适用于植物转录调控预测领域；对动物体系的引用仅作为方法借鉴。
- **不确定性**：文中未提供任何量化不确定性估计。

**有边界的复述**：本文主张，在植物体系中，通过整合多层组学数据（表达、染色质可及性、TF 结合、序列）并借助 ML/深度学习/基础模型，可以比传统共表达或单一组学方法更有效地优先排序候选 TF 及其靶基因；但当前仍缺乏可预测调控响应的端到端模型，且 AI 方法的优势需在植物特异性基准上严格验证。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 植物训练数据不足 | 植物调控基因组学缺乏足够大且注释良好的训练数据集，限制基础模型应用 | 随植物单细胞、空间、扰动、多组学数据集扩展，AI 方法将更有效 | AI 节 |
| 基因调控高度上下文依赖 | 调控模式随组织、发育阶段、环境条件变化，模型迁移困难 | 需要整合更多上下文信息（如单细胞、空间数据） | AI 节 |
| 基础模型未必优于简单基线 | 单细胞扰动响应模型在基准测试中不总是优于简单基线 | 需要严格的植物特异性评估 | AI 节 |
| 从描述到预测的跨越尚未完成 | 当前 GRN 研究以识别候选关系为主，缺乏机制性预测模型 | 发展整合多生物层、保留动态与上下文依赖性的预测框架 | Conclusions 节 |

> 注：作者未以「局限」章节形式系统列出，以上为文中明确表述的约束性陈述。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 综述对「AI 优于传统方法」的论证主要依赖案例引用，缺乏系统性比较 | 可能选择性引用成功案例；传统方法（如单纯 motif 富集）在部分场景可能同样有效或更优 | 读者可能高估 AI 方法的增量收益 | 在统一基准数据集上系统比较 WGCNA/GENIE3 vs ML/DL 方法的预测精度与假阳性率 | AI 节仅引用个别成功案例，未报告失败案例或对比数据 |
| 文中将「TF 结合（ChIP/DAP）」与「功能调控（表达变化）」视为互补证据，但未讨论两者不一致的生物学含义 | TF 结合不一定导致表达变化（可能为旁观者结合或冗余调控），整合策略可能引入系统性偏差 | 多组学整合的权重分配直接影响预测结果 | 分析 ChIP-seq 阳性但表达不变化的位点比例，评估整合策略对精度的影响 | Multi-omics 节未讨论结合-功能不一致问题 |
| 对基础模型的讨论偏乐观，未充分讨论过拟合与泛化风险 | 植物基因组规模大、调控元件注释不完整，基础模型可能学习到物种特异而非保守的调控语法 | 跨物种迁移是作物改良的关键需求 | 在跨物种迁移任务（如拟南芥→玉米/水稻）上评估基础模型 vs 传统方法的泛化差距 | AI 节承认数据不足但未讨论过拟合风险 |
| 文中提到「预测性模型」但未明确其验证标准 | 「预测」可指预测 TF 靶基因、预测表达响应、预测变异效应，三者验证方式不同 | 目标不明确会导致方法评估混乱 | 明确区分三类预测任务并分别定义评估指标 | Conclusions 节使用「predictive modeling」但未操作化定义 |
| 对 NEEDLE 等简化流程的推荐缺乏与更复杂方法的成本-收益比较 | 简化流程可能牺牲精度换取易用性，但文中未量化 | 用户需根据自身数据条件选择合适方法 | 在相同数据集上比较 NEEDLE 与完整多组学整合流程的精度与计算成本 | Network-enabled gene discovery 节仅描述流程，未报告对比 |

## 14 学到什么

**Agent 提炼的知识候选**

1. **多层证据交叉验证策略**：将 TF 结合（ChIP-seq/DAP-seq）、染色质可及性（ATAC-seq/DNase-seq）、表达动态（bulk/scRNA-seq）与 motif 分析整合，取交集或加权融合来预测 TF 靶基因。
   - **迁移到本课题**：在 TF–DNA 结合机制研究中，可设计「序列特征（motif + 保守性）+ 物理结合（ChIP/DAP）+ 功能响应（表达/表型）」三层证据的整合框架，减少单层数据的假阳性。

2. **从共表达到有向 GRN 的递进逻辑**：先以共表达网络（WGCNA）缩小候选范围，再用 GRN 推断（GENIE3 等）建立有向关系，最后用多组学或实验验证精修。
   - **迁移到本课题**：在预测 TF–DNA 结合时，可先用共表达或序列保守性做粗筛，再用结构预测（AlphaFold/DNA 结合域建模）或分子模拟（MD）做精筛，形成「粗筛-精筛-验证」的级联流程。

3. **AI 方法需植物/体系特异性评估**：作者强调基础模型未必优于简单基线，需在目标体系上严格评测。
   - **迁移到本课题**：在开发 TF–DNA 结合预测模型时，应设置传统方法（如 position weight matrix、简单 motif 匹配）作为基线，报告增量收益而非仅报告绝对性能。

4. **跨物种迁移需保守性先验**：拟南芥→作物的迁移依赖进化保守的调控元件和 TF 家族。
   - **迁移到本课题**：在构建 TF–DNA 结合预测模型时，可将系统发育保守性（phyloP/phastCons 或跨物种比对）作为特征或先验，提升跨物种泛化能力。

5. **结构预测与语言模型的辅助角色**：AlphaFold/ESM 可用于推断 TF 结构域、互作界面和功能特性，作为调控预测的补充证据而非替代。
   - **迁移到本课题**：在 TF–DNA 结合机制研究中，可将 AlphaFold 预测的 TF–DNA 复合物结构与 MD 模拟结合，用于解释突变效应或预测结合亲和力变化。

6. **扰动预测是终极目标**：作者指出从「描述性网络」到「预测性模型」的转变是关键，即预测 TF 过表达/敲除后的转录响应。
   - **迁移到本课题**：在 TF–DNA 结合研究中，可构建「结合预测 → 表达响应预测」的端到端框架，用 CRISPR 扰动数据作为训练/验证信号。

## 15 与已有知识连接

- **TF–DNA 结合机制基础**：文中讨论的 TF 结合 motif、顺式调控元件（CRE）、染色质可及性对 TF 可及性的影响，与经典 TF–DNA 结合机制研究（如 zinc finger、bZIP、MYB 等家族的结构-功能关系）直接相关。可连接至 Berg & von Hippel 的序列特异性识别模型、Luscombe 等人的 TF–DNA 结合结构分类。
- **GRN 推断方法学**：GENIE3（Huynh-Thu et al., 2010）为基于树的 GRN 推断方法；WGCNA（Langfelder & Horvath, 2008）为共表达网络分析标准工具。这些方法在动物体系中也有广泛应用，可交叉验证。
- **深度学习在调控基因组学中的应用**：DeFine（Wang et al.）为 CNN 模型预测 TF 结合，与 DeepSEA、Basenji 等非植物体系模型同源。植物体系可借鉴这些模型的架构但需重新训练。
- **基础模型与 DNA 语言模型**：AgroNT、PlantCaduceus 为植物基因组基础模型，与动物/人类基因组模型（如 Enformer、Nucleotide Transformer）思路一致，但针对植物基因组特征（如多倍体、转座子丰富）做了适配。
- **结构预测工具**：AlphaFold（Jumper et al., 2021）和 ESM（Rives et al., 2021）为蛋白质结构/功能预测工具，可用于 TF 结构域分析和互作界面推断，与 MD 模拟结合可研究 TF–DNA 结合的动态机制。
- **单细胞与空间转录组**：文中提及这些技术为 GRN 推断提供细胞类型分辨率，与动物体系中 scRNA-seq + ATAC-seq 的调控网络重建（如 SCENIC）思路一致。
- **候选方向（未验证）** [Analysis]：文中提到的「扰动感知预测模型」与动物体系中 Perturb-seq 驱动的调控模型思路相似，但植物体系中此类数据仍稀缺，是潜在的研究空白。

## 16 研究想法

**Agent 生成的研究候选**

1. **名称**：PlantTF-Bind：基于多组学整合与深度学习的植物 TF–DNA 结合预测框架
   - **来源局限/观察**：现有植物 TF 靶基因预测多依赖单一组学或简单整合，缺乏统一框架；动物体系已有较成熟的 TF 结合预测模型但植物适配不足。
   - **核心假设**：整合序列特征（motif、保守性）、染色质可及性（ATAC-seq）、TF 结合（DAP-seq/ChIP-seq）与表达动态（scRNA-seq）可显著提升植物 TF–DNA 结合预测精度。
   - **初步方法**：构建多模态深度学习模型（CNN/Transformer 混合架构），以序列 + 染色质特征为输入，DAP-seq 结合峰为监督信号；在拟南芥上训练，在作物（玉米、水稻）上测试跨物种迁移。
   - **验证方式**：与 GENIE3、WGCNA+motif 等基线比较 AUC/PRC；用 CRISPR 扰动数据验证预测靶基因的表达响应。
   - **创新状态**：unverified

2. **名称**：TF–DNA 结合的结构感知预测：AlphaFold 与 MD 模拟增强的调控变异效应预测
   - **来源局限/观察**：现有调控变异预测多基于序列保守性或 motif 破坏，忽略 TF–DNA 结合的物理结构基础；AlphaFold 可预测 TF 结构但尚未系统用于结合亲和力预测。
   - **核心假设**：AlphaFold 预测的 TF–DNA 复合物结构 + MD 模拟的结合自由能变化可预测 TF 结合亲和力差异，优于纯序列方法。
   - **初步方法**：选取拟南芥代表性 TF 家族（如 bZIP、MYB、ERF），用 AlphaFold 预测 TF–DNA 复合物结构，对已知调控变异做 MD 模拟（如数百 ns 尺度），计算结合自由能变化（MM-PBSA/MM-GBSA），与 DAP-seq 亲和力数据对照。
   - **验证方式**：与 position weight matrix 破坏分数、保守性分数比较预测精度；用表面等离子共振（SPR）或电泳迁移率变动分析（EMSA）实验验证部分预测。
   - **创新状态**：unverified

3. **名称**：PlantGRN-Perturb：面向植物 TF 扰动响应的预测性 GRN 模型
   - **来源局限/观察**：作者指出植物 GRN 研究仍以描述性为主，缺乏可预测扰动响应的模型；植物体系中大规模扰动数据稀缺。
   - **核心假设**：利用现有植物 TF 过表达/敲除的转录组数据（如拟南芥 TF 突变体库），训练可预测 TF 扰动后转录响应的模型。
   - **初步方法**：收集拟南芥 TF 突变体/过表达系的 RNA-seq 数据，构建「TF 扰动 → 差异表达基因」的训练集；以 TF 序列特征、motif、染色质可及性为输入，训练图神经网络（GNN）预测扰动响应；用 NEEDLE 或 MINI-EX 的 GRN 作为先验结构。
   - **验证方式**：留一 TF 交叉验证；用未参与训练的 TF 扰动数据测试；与线性回归/随机森林基线比较。
   - **创新状态**：unverified

4. **名称**：Cross-species TF–DNA binding transfer：利用基础模型实现植物间调控知识迁移
   - **来源局限/观察**：植物基础模型（AgroNT、PlantCaduceus）已能学习基因组表征，但尚未系统评估其在 TF–DNA 结合预测上的跨物种迁移能力。
   - **核心假设**：在拟南芥上微调的 DNA 基础模型可迁移到作物（玉米、水稻、大豆）的 TF–DNA 结合预测，且优于从头训练的模型。
   - **初步方法**：以 PlantCaduceus 或 AgroNT 为骨干，在拟南芥 DAP-seq 数据上微调，输出 TF 结合概率；在作物 DAP-seq 数据上测试零样本/少样本迁移；分析迁移性能与进化距离的关系。
   - **验证方式**：与从头训练的 CNN 模型比较跨物种 AUC；用 motif 保守性分层分析迁移性能差异。
   - **创新状态**：unverified

5. **名称**：TF–DNA 结合动力学的多尺度模拟：从分子识别到网络响应
   - **来源局限/观察**：本文聚焦预测性建模但未涉及 TF–DNA 结合的物理动力学；MD 模拟可提供结合机制的原子级理解，但计算成本高，难以直接用于全基因组预测。
   - **核心假设**：对代表性 TF–DNA 复合物做 MD 模拟得到的结合动力学特征（如结合位点残基柔性、水介导氢键）可作为特征，提升序列模型的预测精度。
   - **初步方法**：选取 10-20 个拟南芥 TF–DNA 复合物（覆盖不同 TF 家族），做微秒级 MD 模拟，提取结合界面动力学特征；将这些特征作为序列模型的辅助输入，预测同家族 TF 的结合偏好。
   - **验证方式**：与纯序列模型比较预测精度；用突变体 DAP-seq 数据验证动力学特征的预测力。
   - **创新状态**：unverified