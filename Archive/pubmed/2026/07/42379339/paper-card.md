## 01 基本信息
- **标题**：Partial-label metric ceilings for evaluating gene regulatory networks inferred from single-cell foundation models
- **作者**：Kendiukhov, Ihor
- **单位**：未提供
- **期刊/平台**：Bio Systems
- **年份**：2026
- **论文类型**：方法学/基准分析研究
- **领域**：基因调控网络推断 × 单细胞基础模型评估
- **关键词**：GRN inference, partial labels, metric ceilings, single-cell foundation models, scGPT, missing-at-random, AUPR, F1
- **DOI/arXiv 号**：10.1016/j.biosystems.2026.105864
- **代码**：未提供
- **数据**：15 种方法 × 5 个参考网络的 benchmark 输出；CistromeDB/ChIP-Atlas（TF ChIP-seq 注释）；Reactome 通路注释
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文不直接提出新的 TF–DNA 结合预测模型，而是对 GRN 推断（含基于单细胞基础模型 scGPT 的 TF–DNA 调控边推断）的评估协议进行批判性审计。其核心贡献——部分标签下的指标天花板形式化——直接适用于任何以 curated 数据库（如 ChIP-seq 注释）为真值评估 TF–DNA 结合预测器的场景，属于「评估方法论 × AI 方法」交叉位置。

## 02 一句话总结
本文形式化推导了在部分正标签（partial positive labels）下观测 F1 与 AUPR 的理论天花板，并用 15 种方法（含 scGPT 的 attention/gradient 探针）在 5 个参考网络上重分析，证明缺失标签只能解释部分性能差距，模型与生物学真值之间仍存在实质失配。

## 03 研究问题
- **具体问题**：GRN benchmark 通常将 curated 参考网络视为完整真值，但实际参考仅覆盖部分真实调控边。这种部分标签如何影响观测指标（F1、AUPR）的解释？在考虑标签缺失后，现有方法（尤其单细胞基础模型）的真实性能如何？
- **为什么重要**：若 curated 参考不完整，则所有基于这些参考的 GRN 评估结论都可能被系统性高估或误读，影响方法选择与生物学结论。
- **现有方法不足**：现有 benchmark 分析通常假设参考完整（或忽略缺失），未对标签缺失率进行建模或校正；非随机缺失（如研究偏好）更未被系统处理。
- **精确研究问题**：Can we derive explicit ceilings for observed F1 and AUPR under partial positive labels, and does correcting for these ceilings change the ranking and interpretation of GRN inference methods (including single-cell foundation model probes)?

## 04 背景与发展脉络
- **阶段一：GRN 推断经典方法**——统计方法（如相关性、互信息）、树集成方法（如 GENIE3、GRNBoost2）。优点：可解释、计算轻量；局限：难以捕捉非线性调控、依赖特征工程。
- **阶段二：单细胞基础模型**——scGPT 等通过 attention 或梯度归因探针提取调控边。优点：利用大规模预训练表征；局限：评估仍依赖不完整的 curated 参考，性能解读模糊。
- **阶段三：评估协议批判**——本文主张：curated 参考是部分标签，需形式化天花板并校正指标。位置：在「方法性能比较」与「评估可信度」之间插入一层统计校正。
- **脉络标注**：仅本文框架（作者在文中构建的阶段划分与主张），未经外部核验。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 参考网络不完整 | curated 参考仅覆盖部分真实调控边，被当作完整真值 | 实验验证成本高，研究集中于已知调控子 | 摘要：curated references are not complete |
| 观测指标被高估/误读 | F1、AUPR 在部分标签下偏离真实性能 | 缺失正标签导致分母与分子同时失真 | 摘要：formalize observed-metric ceilings under partial positive labels |
| 非随机缺失被忽略 | 研究偏好使参考集中于已充分研究的调控子 | 真实 curated 参考集中于 extensively studied regulators | 摘要：real curated references concentrate on extensively studied regulators |
| 基础模型性能解读模糊 | scGPT 探针排名靠前但远低于天花板 | 标签缺失与模型-生物学失配混合 | 摘要：foundation-model probes occupy the top of the ranking but still operate far below the observable ceiling |

## 06 核心思想
1. **表面方法**：在 missing-at-random (MAR) 标签模型下推导观测 F1 与 AUPR 的显式天花板；用 Beta 后验传播覆盖率不确定性；用基于 CistromeDB/ChIP-Atlas 与 Reactome 的 study-biased 缺失模型替代 stylized 非 MAR 测试；对 15 种方法 × 5 参考的 benchmark 输出进行重分析。
2. **核心洞察**：部分标签下观测指标存在可解析的天花板；真实缺失模式是 study-biased 而非 MAR；校正后仍存在模型-生物学失配，说明性能差距不能全部归因于标签缺失。
3. **可能的普适教训** [Analysis]：任何以 curated 数据库为真值的评估（包括 TF–DNA 结合预测）都应先量化标签完整性，再解释指标；基础模型的高排名可能部分反映其与「研究偏好」的耦合而非纯生物学信号。

## 07 方法总览
- **输入**：15 种方法的 GRN 推断边集（含 scGPT attention/gradient 探针、经典统计与树集成方法、随机对照）；5 个 curated 参考网络；CistromeDB/ChIP-Atlas 的 TF ChIP-seq 注释；Reactome 通路注释。
- **输出**：观测 F1/AUPR 的天花板估计；校正后的归一化指标；方法排名与随机基线比较。
- **模块**：(1) MAR 天花板推导；(2) Beta 后验不确定性传播；(3) study-biased 缺失模型构建；(4) 基准重分析与归一化。
- **训练**：不涉及模型训练，纯评估分析。
- **工具**：未提供具体软件/库。
- **反馈回路**：无（静态分析）。
- **假设**：MAR 模型为基线；study-biased 缺失由 ChIP-seq 与通路注释驱动；观测边与标签缺失独立（在给定缺失模型下）。
- **流程**：推导 MAR 天花板 → 用 Beta 后验估计覆盖率 → 构建 study-biased 缺失模型 → 对 39 个 AUPR 可评估行计算归一化指标 → 比较随机基线与天花板 → 量化通路注释限制下的可观测边比例 → 评估模型分数与 study status 的耦合对 AUPR 的膨胀效应。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| MAR 天花板推导 | 给出部分标签下 F1/AUPR 的显式上界 | 建立评估基准 | 输入：标签缺失率；输出：天花板公式 | 摘要：derive explicit ceilings | 预期：失去指标解释的锚点 [Analysis] |
| Beta 后验传播 | 量化覆盖率不确定性 | 标签缺失率本身有估计误差 | 输入：观测边数、缺失率先验；输出：后验分布 | 摘要：propagate coverage uncertainty via Beta posteriors | 预期：低估不确定性 [Analysis] |
| study-biased 缺失模型 | 替代 stylized 非 MAR 测试 | 真实缺失由研究偏好驱动 | 输入：ChIP-seq 注释、通路注释；输出：缺失概率 | 摘要：replace stylized non-MAR tests with study-biased missingness | 预期：缺失模式被错误建模 [Analysis] |
| 基准重分析 | 计算归一化指标并比较 | 统一比较 15 种方法 | 输入：边集+参考；输出：归一化 F1/AUPR | 摘要：39 AUPR-evaluable rows | 预期：无法判断方法相对性能 |

## 09 关键公式符号
- **观测 F1 天花板**：在 MAR 下，观测 F1 ≤ 真实 F1 的某个函数，受缺失率约束。符号：F1_obs, F1_true, 缺失率 p。用途：界定观测指标上界。直觉：缺失正标签使 precision 与 recall 同时受限。来源：摘要「derive explicit ceilings for observed F1 and AUPR」；具体公式未在摘要中给出。
- **观测 AUPR 天花板**：类似地，AUPR_obs 受缺失率约束。符号：AUPR_obs, AUPR_true, p。用途：评估 AUPR 可解释范围。直觉：正标签缺失降低 precision-recall 曲线下面积。来源：同上。
- **Beta 后验**：覆盖率 c ~ Beta(α, β)，用于传播不确定性。符号：c, α, β。用途：量化天花板估计的置信区间。直觉：观测边数与缺失率决定后验形状。来源：摘要「propagate coverage uncertainty via Beta posteriors」。
- **注**：具体公式与符号定义在摘要中未展开，仅能确认存在性与用途。

## 10 实验设计与证据链
- **数据集**：15 种方法的 GRN 推断输出；5 个 curated 参考网络；CistromeDB/ChIP-Atlas（TF ChIP-seq 注释）；Reactome 通路注释。
- **规模**：39 个 AUPR 可评估行（15 方法 × 5 参考的部分组合）。
- **指标**：F1、AUPR、归一化 F1/AUPR 比率、随机基线比较。
- **基线**：随机对照（random control）。
- **评测协议**：MAR 天花板校正；study-biased 缺失模型；通路注释限制下的可观测边比例。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| MAR 天花板推导 | 部分标签下观测指标有界 | 理论推导 vs 无界假设 | 显式天花板存在 | 观测指标不能直接解释为真实性能 | 不能确定真实性能的具体值 | 摘要 |
| 15 方法重分析 | 方法性能低于天花板 | 15 方法 vs 天花板 vs 随机 | 最佳归一化 F1=0.137, AUPR=0.014；中位 AUPR=5.56e-5；仅 3/39 行超过随机基线 | 所有方法远低于可观测天花板 | 不能区分方法间真实差距 | 摘要 |
| scGPT 探针排名 | 基础模型探针是否优于经典方法 | scGPT attention/gradient vs 统计/树集成 | 探针占据排名顶部 | 基础模型在观测指标上领先 | 不能证明其生物学优越性（可能反映研究偏好耦合） | 摘要 |
| study-biased 缺失测试 | 非随机缺失对 AUPR 的影响 | study-biased vs MAR vs stylized worst case | 通路注释限制下仅 ~60% 边可观测；AUPR 膨胀 +0.040（介于 MAR ~0 与 worst case +0.151 之间） | 缺失模式显著影响指标解读 | 不能确定真实缺失机制 | 摘要 |

## 11 结论正确解读
- **任务范围**：仅针对 GRN 推断的评估协议，不涉及新模型或新生物学发现。
- **oracle/真值输入**：curated 参考网络被视为部分标签而非完整真值；CistromeDB/ChIP-Atlas 与 Reactome 注释用于构建缺失模型。
- **端到端状态**：非端到端；纯评估分析，无预测流程。
- **算力成本**：未提供；推测为轻量统计计算。
- **历史数据依赖**：依赖已有 benchmark 输出与注释数据库的覆盖范围。
- **模型依赖**：scGPT 探针仅作为被评估对象，不依赖其内部机制。
- **最难情形**：study-biased 缺失下，模型分数与 study status 耦合时，AUPR 膨胀最显著。
- **群体/领域边界**：结论限于 GRN 推断评估；对 TF–DNA 结合预测的适用性需类比迁移。
- **不确定性**：Beta 后验传播了覆盖率不确定性，但缺失模型本身（MAR vs study-biased）的选择影响结论。
- **有边界的复述**：在部分标签假设下，15 种方法（含 scGPT 探针）的观测 AUPR 均远低于理论天花板；校正缺失后仍存在模型-生物学失配，因此现有评估结论应被收窄解读。

## 12 作者自认局限
在提供的材料（摘要）中未发现作者明确承认的局限。
- **作者提及的相关约束**（非正式局限）：摘要提到「stress-test assumption violations」，暗示 MAR 假设可能不成立，但未展开为正式局限声明。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 天花板推导依赖 MAR 假设 | 真实缺失可能非 MAR，study-biased 模型也仅是一种近似 | 若缺失机制更复杂，天花板可能不准确 | 用合成数据模拟多种缺失机制，比较天花板预测与真实值 | 摘要「stress-test assumption violations」 |
| scGPT 探针排名顶部可能反映研究偏好耦合 | 高排名可能源于模型学习到「哪些基因被研究过」而非真实调控 | 影响对基础模型价值的判断 | 控制 study status 后重算指标，观察排名变化 | 摘要「empirically measured coupling between model scores and studied status」 |
| 39 行 AUPR 可评估样本量有限 | 15 方法 × 5 参考的完整组合应更多，39 行可能因缺失值筛选 | 小样本可能降低结论稳健性 | 检查完整组合数与缺失原因 | 摘要「39 AUPR-evaluable rows」 |
| 归一化指标的定义未在摘要中明确 | 归一化方式（如除以天花板）影响数值解读 | 不同归一化可能导致不同结论 | 查阅全文方法节 | 摘要仅给出比值 |

## 14 Agent 提炼的知识候选
- **概念候选：部分标签天花板**：任何以 curated 数据库（如 ChIP-seq 注释、TRANSFAC、JASPAR）为真值的 TF–DNA 结合预测评估，都应先量化标签完整性并推导观测指标天花板。迁移：在 TF–DNA 结合预测中，curated 结合位点仅覆盖部分真实结合事件，评估时应报告天花板校正后的指标。
- **方法候选：study-biased 缺失建模**：用领域注释（如 ChIP-seq 覆盖、通路注释）构建非随机缺失模型，替代 stylized 假设。迁移：在 TF–DNA 结合预测中，可用「该 TF 被 ChIP-seq 研究次数」作为缺失概率的代理，校正评估偏差。
- **方法候选：Beta 后验不确定性传播**：对标签覆盖率的不确定性进行显式建模。迁移：在 TF–DNA 结合预测评估中，报告覆盖率后验区间而非点估计。
- **实验设计候选：随机对照 + 天花板比较**：将方法性能与随机基线及理论天花板同时比较。迁移：在 TF–DNA 结合预测中，加入随机预测器作为下界，天花板作为上界，明确方法所处区间。
- **概念候选：模型-生物学失配诊断**：校正缺失后仍存在的性能差距，应被解读为模型与生物学真值的失配，而非评估噪声。迁移：在 TF–DNA 结合预测中，区分「标签缺失导致的低估」与「模型真实缺陷」。

## 15 与已有知识连接
- **相似领域**：部分标签学习（partial label learning）在机器学习中有成熟理论，本文将其应用于 GRN 评估，可类比迁移到 TF–DNA 结合预测的评估协议。
- **可组合方法**：scGPT 的 attention/gradient 探针（本文评估对象）与 TF–DNA 结合预测中的基础模型（如 Enformer、AlphaFold 3）在评估上面临相同的部分标签问题。
- **冲突观点**：部分 GRN benchmark 研究（如 BEELINE）将 curated 参考视为完整真值，本文直接挑战这一假设，与 TF–DNA 结合预测中「以 ChIP-seq 为金标准」的常见做法形成张力。
- **可迁移工具**：CistromeDB/ChIP-Atlas 注释（本文用于构建缺失模型）可直接用于 TF–DNA 结合预测的评估校正。
- **候选方向**：将本文的天花板推导推广到 TF–DNA 结合预测的常用指标（如 AUC、precision@k），并探索更复杂的缺失机制（如偏好于高表达基因）。

## 16 Agent 生成的研究候选
- **候选 1：TF–DNA 结合预测的部分标签天花板**
  - 名称：Partial-label ceilings for TF–DNA binding predictors
  - 来源局限/观察：本文对 GRN 的结论可迁移到 TF–DNA 结合预测，但后者常用指标（AUC、precision@k）与缺失模式不同
  - 核心假设：在 ChIP-seq 部分标签下，TF–DNA 结合预测的观测 AUC 存在可推导的天花板，且 study-biased 缺失会显著膨胀指标
  - 初步方法：用 JASPAR/ENCODE ChIP-seq 数据构建部分标签模型，推导 AUC 天花板，用 Beta 后验传播不确定性
  - 验证方式：合成数据模拟 + 真实 ChIP-seq 基准重分析
  - 创新状态：unverified
- **候选 2：研究偏好感知的评估校正**
  - 名称：Study-bias-aware evaluation for TF–DNA binding
  - 来源局限/观察：本文发现模型分数与 study status 耦合会膨胀 AUPR；TF–DNA 结合预测可能同样受「研究热门 TF」偏差影响
  - 核心假设：控制 TF 研究热度后，现有 TF–DNA 结合预测器的排名会显著变化
  - 初步方法：用 ChIP-seq 覆盖次数作为 study status 代理，分层重算指标
  - 验证方式：对多个公开 benchmark 进行重分析
  - 创新状态：unverified
- **候选 3：基础模型探针的公平比较协议**
  - 名称：Fair comparison protocol for foundation model probes in TF–DNA binding
  - 来源局限/观察：本文对 scGPT 探针的评估显示其排名顶部但远低于天花板；TF–DNA 基础模型探针可能面临同样问题
  - 核心假设：在部分标签校正后，基础模型探针的相对优势可能缩小或消失
  - 初步方法：对 Enformer、AlphaFold 3 等模型的 TF–DNA 探针应用本文的天花板校正
  - 验证方式：重分析现有 benchmark 输出
  - 创新状态：unverified
- **候选 4：缺失机制敏感性分析框架**
  - 名称：Sensitivity analysis framework for label-missing mechanisms
  - 来源局限/观察：本文仅测试 MAR 与 study-biased 两种机制；真实缺失可能更复杂
  - 核心假设：不同缺失机制下，天花板校正的结论可能不一致
  - 初步方法：模拟多种缺失机制（偏好高表达、偏好已知 motif、随机），比较校正后指标
  - 验证方式：合成数据 + 真实数据交叉验证
  - 创新状态：unverified