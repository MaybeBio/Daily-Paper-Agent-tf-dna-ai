## 01 基本信息
- 标题：Unlocking the Regulatory Genome by ARGUS: An Evidence-Constrained Agentic Framework for Interpreting Single Nucleotide Variants
- 作者与单位：Dutta, Pratik; Obusan, Matthew B; Chao, Max; Sathian, Rekha; Papineni, Nimisha; Davuluri, Ramana V（单位未在提供材料中列出）
- 期刊/预印本平台：ArXiv（PubMed 收录，ID 42926727）
- 年份：2026-10-25
- 论文类型：方法/系统论文（agentic framework + 案例研究）
- 领域：调控基因组学、非编码变异解读、agentic AI、TF–DNA 结合预测
- 关键词：未提供（正文未列关键词）
- DOI/arXiv 号：PubMed ID 42926727（arXiv 号未提供）
- 代码：https://github.com/duttaprat/ARGUS
- 数据：本地 ADASTRA、JASPAR、ENCODE cCRE 证据源；AlphaGenome Atlas（SDK 0.9.0）交叉引用
- 阅读日期：未提供
- 在「蛋白质–DNA 互作(TF–DNA 结合机制) × AI/物理模拟」方向中的位置：本文不提出新的 TF–DNA 结合预测模型，而是把已有的 458 个 DNABERT-based TF binding 模型（来自 DeepVRegulome 管线）作为上游预测器，构建一个「证据约束的 agentic 解读层」，用真实实验证据（ADASTRA allele-specific binding）对预测做证伪/救援/弃权。对本课题的价值在于：提供了一套「预测 vs 解读」分离的架构范式、确定性 verifier 设计、以及饱和（saturation）导致模型假阴性的具体机制案例。

## 02 一句话总结
针对非编码变异解读中 LLM 幻觉 TF 结合变化的问题，ARGUS 用确定性代码做全部生物学分类、用 LLM 只做证据源选择与报告生成，在 rs6983267 上对 4 个 TF 产生 4 条由真实证据驱动的分歧轨迹（1 rescued、3 abstained），证明「观察依赖的分支式调查」可在可审计框架内实现，但评估仅限 5 个 TF 假设、2 个位点，不构成准确性基准。

## 03 研究问题
- 具体问题：给定一个上游 TF–DNA 结合预测模型（DNABERT-based）对某非编码 SNV 的输出，系统能否在整合独立实验证据后，诚实地判断「该预测是否应被相信」，并在证据不足时弃权？
- 为什么重要：>90% 的 GWAS 疾病相关变异位于非编码调控区，其功能解读是基因组医学的核心开放问题；预测与解读是两个不同问题，现有资源（如 AlphaGenome Atlas 预计算 90 亿 SNV）不区分「模型预测有影响」与「独立证据支持该影响」。
- 现有方法为何不足：通用 LLM 被提示解读变异时会幻觉 TF 结合变化、编造实验支持、对统计上可忽略的信号赋予生物学意义（原型中 Qwen 2.5 7B 把 ref=0.007/alt=0.0009 两个远低于 0.5 阈值的概率之比 log_odds_ratio=3.02 报告为 SP1「binding gain」）；prompt 层面的约束不足以阻止此类错误。
- 精确研究问题（Can ... ?）：Can an evidence-constrained agentic framework, with deterministic biological classification and LLM-mediated evidence selection, produce observation-dependent investigation trajectories that abstain when direct experimental evidence is absent, rather than hallucinating TF binding changes?

## 04 背景与发展脉络
（注：以下脉络为「仅本文框架」，作者在 Introduction 中给出的叙述，未经外部核验）
- 阶段 1：GWAS 与非编码变异解读瓶颈（Maurano et al. 2012; Corpas et al. 2026）——大量疾病相关变异落在非编码调控区，机制解读困难。
- 阶段 2：序列基深度学习变异效应预测（Zhou & Troyanskaya 2015 等）——在预测问题上进展显著，但不解决解读问题。
- 阶段 3：大规模预计算资源（AlphaGenome Atlas, Cheng et al. 2026）——为全部 90 亿 SNV 预计算影响预测；作者主张预测与解读仍是不同问题。
- 阶段 4：生物研究 agentic AI（Li et al. 2026; Corpas et al. 2026）——LLM agent 协调多步分析、调用工具、检索文献；但存在特有失败模式：语言流畅性 ≠ 生物学推理可靠性；基准显示通用 LLM 会产生不准确的癌症变异分类并倾向过度分类弱证据变异（Lin et al. 2025）。
- 本文主张的位置：不竞争上游预测模型，而是补足下游「解读」环节；提出「deterministic science, agentic reasoning」设计原则与 hypothesis-directed investigation loop，把证伪（falsification）作为一等组件。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| LLM 幻觉 TF 结合变化 | 把两个远低于阈值的概率之比报告为「binding gain」 | 作者解释：LLM 会把数值输出误读为生物学显著事件；prompt 约束可被覆盖 | Introduction 原型：Qwen 2.5 7B 对 rs6983267 报告 SP1 log_odds_ratio=3.02，而 ref=0.007、alt=0.0009 |
| 预测与解读混淆 | 不区分「模型预测有影响」与「独立证据支持」 | 作者解释：现有资源与工具未在架构上区分二者 | Introduction；Discussion「Prediction vs. Interpretation」 |
| 计算证据被当作实验确认 | 计算一致性被呈现为实验验证 | 作者解释：agentic 系统常见失败模式 | Discussion「Falsification as a Design Pattern」 |
| 模型饱和导致假阴性 | 两个等位基因都预测为近最大结合，模型无法分辨等位差异 | 作者解释：DNABERT 模型在高结合概率处饱和，动态范围触顶 | Results FOXA1：pref=palt=0.995，>0.95 saturation 阈值；ADASTRA 显示显著 ASB（FDR=0.030） |
| 前沿 LLM 不弃权 | 把 8q24/MYC 已知生物学与变异特异性 TF 结合主张混为一谈，引用文献不验证变异级分辨率 | 作者解释：LLM 不自发识别知识边界 | Results「Frontier LLM Baseline」（作者注明为非受控基准） |
| 无信息证据被反复查询 | 固定优先级 planner 会查询无法改变结论的证据源 | 作者解释：固定优先级不等于价值信息导向 | Results「Fixed vs. LLM-Mediated Planning」：LLM planner 9 次工具调用 vs 固定 13 次 |

## 06 核心思想
1) 表面方法：ARGUS 分两阶段——确定性预测阶段（复用 DeepVRegulome 管线，458 个 DNABERT-based TF binding 模型，0.5 阈值四分类 + 0.95 饱和标记）与 agentic 调查阶段（planner 选证据源、verifier 确定性解读、stopping rule 定终态、reporter 仅用 LLM 生成叙述）。
2) 核心洞察：LLM 与生物学分类的边界必须由架构强制，而非 prompt 约束；把每个预测当作可检验假设，用真实实验证据（ADASTRA）做证伪，证据不足时弃权；「agency 的定义性判据是：一个观察改变了 ARGUS 下一步做什么」。
3) 可能的普适教训 [Analysis]：在 TF–DNA 结合机制研究中，模型输出（概率、log-odds）本身不构成证据；需要显式的证据类型标签（experimental/direct_to_claim）与终态语义（supported/contradicted/rescued/abstained）来防止「计算一致性冒充实验确认」。该教训可迁移到任何以深度学习预测 TF 结合为上游的解读流程。

## 07 方法总览
- 输入：用户查询（variant / gene / region / TF 四种模式，由确定性 regex 路由，无 LLM 参与）；对 variant 模式，输入为变异标识（如 rs6983267, chr8:127401060 G>T, GRCh38）。
- 输出：每个 TF 假设的终态（active / supported / contradicted / rescued / abstained / partially_supported）、证据记录（含 verdict 与 provenance 标签）、完整决策轨迹（trajectory JSON）、以及受约束的叙述报告（CAN_CLAIM_EXPERIMENTAL 标志）。
- 模块：Prediction Stage（TF 选择知识库 + 458 DNABERT 模型 + 确定性分类器）、State（state.py）、Planner（planner.py，固定优先级或 LLM-mediated）、Tools（ADASTRA / JASPAR / ENCODE cCRE）、Verifier（verifier.py，10 分支决策树）、Stopping rule（stopping.py）、Evidence-Constrained Reporter。
- 训练：无新模型训练；DNABERT 模型为既有；LLM planner 使用 Claude Sonnet 4.6（结构化 tool use），reporter 为唯一默认使用 LLM 的组件。
- 工具：LangGraph 编排；本地 ADASTRA、JASPAR、ENCODE cCRE 数据；AlphaGenome Atlas SDK 0.9.0（仅交叉引用，不进入 planner/verifier）。
- 反馈回路：at=π(St,𝒯), ot=Tat(St), St+1=V(St,ot)；中间观察改变下一步动作；planner 可按风险优先级排序假设（saturated 最高，其次 LOF/GOF、quantitative shifts、retained binding、null）。
- 假设：上游预测可被独立实验证据证伪；非显著不等于无效应；计算证据不能独立确认或证伪 TF 结合。
- 文字流程：查询 → regex 路由 → 选 TF（GTEx 表达 + ChIP-seq peak 重叠 193M+ peaks/700 TFs + 疾病相关注释）→ 510-bp 序列 ref/alt 替换 → DNABERT 输出 pref/palt → 确定性四分类 + 饱和标记 → 初始化 HypothesisState → planner 按优先级选证据源 → tool 查询真实数据 → verifier 确定性解读并更新状态 → 若未终态则继续，否则 stopping rule 定终态 → reporter 从预分类事实生成叙述。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 确定性分类器（0.5 阈值 + 0.95 饱和标记） | 把 pref/palt 分为 LOF/GOF、strengthened/weakened、retained、no confident binding，并标记饱和 | 结构性地阻止「两个亚阈值概率之比」被解读为结合变化 | 输入 pref/palt；输出标签 + saturation 警告 | Architecture「Prediction Stage」；Introduction SP1 幻觉案例 | 预期：SP1 类幻觉重新出现（作者主张，未做消融） |
| State (state.py) | 存储科学事实：DVR 预测、证据记录、假设状态、轨迹事件 | 分离事实存储与决策 | 输入/输出 HypothesisState | Architecture「Investigation Stage」 | 预期：无法追踪决策轨迹（未做消融） |
| Planner (planner.py) | 基于当前不确定性选下一证据源；固定优先级 ADASTRA→JASPAR→cCRE→ABSTAIN；或 LLM-mediated | 决定「下一步测什么」 | 输入 St 与工具集 𝒯；输出动作 at | Architecture；Results「Fixed vs. LLM-Mediated Planning」 | 实测对比：LLM planner 与固定 planner 终态一致，工具调用 9 vs 13 |
| Tools（ADASTRA / JASPAR / ENCODE cCRE） | 执行真实证据查询 | 提供可证伪的外部证据 | 输入查询；输出原始证据 | Architecture「Tools」；Results 各轨迹 | 预期：无证据则只能停在预测（未做消融） |
| Verifier (verifier.py) | 确定性解读工具原始输出，更新假设状态；ADASTRA 用 10 分支决策树 | 保证分类不由 LLM 完成 | 输入 ot；输出 St+1 | Architecture「Verifier」；Results FOXA1/KLF6/RAD21/SP1 | 预期：终态语义失效（未做消融） |
| Stopping rule (stopping.py) | planner 返回 ABSTAIN 时定终态；一致间接支持→partially_supported；混合间接→abstained；欠功效直接证据→abstained；无解决性证据→abstained | 防止间接证据被升级为强结论 | 输入证据集合；输出终态 | Architecture「Stopping rule」；Results KLF6/RAD21/SP1 | 预期：间接证据可能被误升级（未做消融） |
| Evidence-Constrained Reporter | 从预分类事实块生成叙述；不能覆盖 verdict、不能重分类、不能在 CAN_CLAIM_EXPERIMENTAL=False 时声称实验确认 | 限制 LLM 只做叙述 | 输入结构化 facts block；输出叙述文本 | Architecture「Evidence-Constrained Reporter」 | 作者明确：约束状态转移不保证下游自由文本的事实性，完整叙述评估留待未来工作 |

## 09 关键公式符号
- 调查循环：at=π(St,𝒯), ot=Tat(St), St+1=V(St,ot)
  - 符号含义：St 当前状态；𝒯 可用工具集；π 规则式 planner 策略；Tat 被选中的证据工具；V 确定性 verifier；at 动作；ot 观察。
  - 用途：形式化「观察依赖的分支式调查」。
  - 直觉：下一步动作是当前状态与可用工具的函数，而非预定序列。
  - 来源指针：Architecture「Investigation Stage: The Agentic Loop」。
- 饱和判据：pref > 0.95 且 palt > 0.95
  - 用途：标记模型动态范围触顶。
  - 来源指针：Architecture「Prediction Stage」。
- 结合阈值：0.5 active-binding threshold
  - 用途：四分类的判定边界。
  - 来源指针：Architecture「Prediction Stage」。
- 其余定量结果（FDR、Δ、AVI 等）为实验数值，非理解框架所必需的公式，见第 10 节。

## 10 实验设计与证据链
数据集/群体/规模：单变异 rs6983267（chr8:127401060 G>T, GRCh38），8q24 癌症风险位点；5 个 TF 假设（FOXA1、KLF6、RAD21、SP1，及「五个案例」中的第五个未在提供材料中具名）；2 个位点（作者 Limitations 称「five TF hypotheses at two loci」）。
指标：终态标签（rescued/abstained 等）、工具调用次数、FDR、Δ motif score、AVI 分数、max |Δ|。
基线：固定优先级 planner vs LLM-mediated planner（Claude Sonnet 4.6，预算 3 次工具调用/假设）；前沿 LLM 基线（GPT-4o、Claude 4.6 Sonnet、Gemini 2.5 Pro，作者注明为非受控基准）。
预算：LLM planner 每次调用约 1,200 input tokens + 250 output tokens，约 $0.01/假设。
骨干/仪器：458 个 DNABERT-based TF binding 模型（445 个有匹配 ADASTRA 表）；LangGraph 编排；本地 ADASTRA/JASPAR/ENCODE cCRE；AlphaGenome Atlas SDK 0.9.0。
oracle 输入：初始 DVR 输出为预计算（precomputed），非端到端自然语言到推断。
评测协议：案例研究 + 两 planner 对比 + 独立计算模型交叉引用；作者明确不构成预测准确性基准。

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| FOXA1 轨迹 | 饱和预测可被实验证据救援 | pref=palt=0.995（>0.95 饱和）；查 ADASTRA | 显著 ASB，preferred allele=ref，FDR=0.030，15 个 ChIP-seq 实验，475 reads；3 步 rescued | 存在模型假阴性，实验数据可救援 | 不能推广到所有饱和预测 | Results「FOXA1」 |
| KLF6 轨迹 | 混合间接证据应弃权 | pref=0.596, palt=0.915；ADASTRA 无该 SNP；JASPAR MA1517.2 ref_rel=0.725, alt_rel=0.577, Δ=−0.147；cCRE 为 pELS + CTCF | 8 步 abstained；CAN_CLAIM_EXPERIMENTAL=False | 混合间接证据下系统拒绝升级为发现 | 不能说明 JASPAR 方向性可靠 | Results「KLF6」 |
| RAD21 轨迹 | 有功效但非显著的实验测试应弃权 | pref=0.999, palt=0.9995；ADASTRA 非显著但过覆盖过滤（5 实验，104 reads，FDR=0.65）；JASPAR 无匹配 motif；cCRE 仅上下文 | 8 步 abstained | 非显著不establish 无效应，故弃权 | 不能说明无等位效应 | Results「RAD21」 |
| SP1 轨迹 | 无直接实验证据时应弃权 | pref=palt=0.9995；ADASTRA 有表但 rs6983267 未测；JASPAR MA0079.5 Δ=−0.120 但不裁决方向；cCRE 仅上下文 | 8 步 abstained | 与 FOXA1 同起点但无直接证据则弃权 | 不能说明 SP1 无结合变化 | Results「SP1」 |
| 观察依赖分支 | 同一 planner 因中间观察不同产生结构不同轨迹 | 同变异、同工具集 | FOXA1 1 次工具调用解决；KLF6/RAD21/SP1 走完三工具但停止原因不同 | 条件分支区别于固定管线 | 不能说明分支策略最优 | Results「Observation-Dependent Branching」 |
| 前沿 LLM 基线 | 前沿 LLM 会混淆已知生物学与变异特异主张 | GPT-4o、Claude 4.6 Sonnet、Gemini 2.5 Pro | 均产生自信分析，不区分表达与 ASB，不弃权 | 支持「架构强制优于 prompt」 | 作者注明非受控基准，不能量化 | Results「Frontier LLM Baseline」 |
| AlphaGenome 交叉引用 | 独立计算模型是否方向一致 | AVI=0.570；1,617 CHIP_TF tracks | FOXA1 max |Δ|=0.463（4 tracks，含 HepG2、MCF-7）；KLF6 Δ=−0.240（1 track）；RAD21 16 tracks max |Δ|=0.107；SP1 8 tracks max |Δ|=0.206 | 与 ADASTRA/JASPAR 方向一致 | 作者明确排除出 planner/verifier，因 AVI 为变异级、不产生观察依赖分支 | Results「AlphaGenome Atlas Cross-Reference」 |
| 固定 vs LLM planner | LLM planner 能否以更少工具调用达相同终态 | 5 个假设，预算 3 次调用/假设，3 次独立重复 | 终态全一致；LLM planner 3 次重复工具序列相同；9 vs 13 次调用 | LLM 选择可避免无信息证据 | 作者明确：不establish 一般性规划优势 | Results「Fixed vs. LLM-Mediated Planning」 |

## 11 结论正确解读
- 任务范围：仅 5 个 TF 假设、2 个位点、1 个主变异（rs6983267）的案例研究；作者明确不构成预测准确性基准或幻觉减少的受控测量。
- oracle/真值输入：初始 DVR 输出为预计算；未评估端到端自然语言到推断。
- 端到端状态：非端到端；reporter 的下游自由文本事实性未评估（作者明确）。
- 算力成本：LLM planner 约 $0.01/假设（约 1,200 input + 250 output tokens）；无 GPU 训练成本报告。
- 历史数据依赖：依赖本地 ADASTRA、JASPAR、ENCODE cCRE 快照；ENCODE cCRE 因 SCREEN API 不可达改用本地 BED，缺 biosample 特异性活性注释。
- 模型依赖：458 个 DNABERT 模型有已知盲点（高概率饱和、核心 motif 外位置敏感性有限）；445/458 有匹配 ADASTRA 表。
- 最难情形：饱和预测（FOXA1 被救援，SP1 因无直接证据弃权）；混合间接证据（KLF6）；有功效但非显著（RAD21）。
- 群体/领域边界：8q24/MYC 癌症风险位点、结直肠癌相关细胞系（HCT116）等；组织匹配限制生物学解读。
- 不确定性：ADASTRA 的 assay 聚合、ref/alt 等位基因协调、组织匹配均被作者列为限制。
- 有边界的复述：在 rs6983267 上，ARGUS 用真实证据对 4 个 TF 产生 4 条分歧轨迹，其中 1 个被实验证据救援、3 个弃权；固定与 LLM planner 终态一致而工具调用数不同；这些结果展示系统行为与轨迹分歧，不证明其预测准确性或幻觉减少幅度。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 评估规模小 | 5 个 TF 假设、2 个位点；非预测准确性基准，非幻觉减少受控测量 | 未明确（称需更广变异集系统比较） | Discussion「Limitations」；Results「Frontier LLM Baseline」 |
| 非端到端 | 初始 DVR 输出预计算；未评估自然语言到推断的端到端 | 未明确 | Discussion「Limitations」 |
| planner 非学习型 | 固定证据优先级，非学习或 value-of-information 策略 | 自适应规划、基于期望信息增益的形式化停止准则、跨 TF 依赖的 regulatory hypothesis graph | Discussion「Limitations」 |
| 证伪证据源有限 | 仅 3 个证据源 | 扩展至 eQTL（GTEx）、染色质可及性（ATAC-seq）、文献（PubMed）、独立模型预测（AlphaGenome Atlas CHIP_TF） | Discussion「Limitations」 |
| DNABERT 模型盲点 | 高结合概率饱和、核心 motif 外位置敏感性有限 | 系统性刻画模型失败模式（进行中） | Discussion「Limitations」 |
| 生物学解读限制 | 模型训练上下文与证据源的组织匹配、ADASTRA assay 聚合、ref/alt 等位基因协调 | 未明确 | Discussion「Limitations」 |
| ENCODE cCRE 数据获取 | SCREEN API 不可达，改用本地 BED，缺 biosample 特异性活性注释 | 未明确 | Discussion「Limitations」 |
| reporter 下游文本 | 约束状态转移不保证自由文本事实性 | 完整叙述评估留待未来工作 | Architecture「Evidence-Constrained Reporter」 |

作者提及的相关约束（非正式局限）：前沿 LLM 基线为 informal observation，非受控基准；固定 vs LLM planner 对比仅 5 假设 1 替代策略，不establish 一般性规划优势。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 评估仅 5 假设 2 位点，且主结果集中在单一变异 rs6983267 | 轨迹分歧可能对该位点证据分布特化；换位点可能不出现 4 条分歧轨迹 | 决定框架是否可推广到全基因组解读 | 在多个 GWAS 位点、多变异上运行并统计终态分布与工具调用数 | Discussion「Limitations」；Results 全部 |
| 饱和救援路径依赖 ADASTRA 恰好覆盖该 TF-SNP | FOXA1 被救援可能因 ADASTRA 数据可得，而非框架普适能力；445/458 有表但 SNP 覆盖未知 | 「救援」结论的可得性偏差 | 统计 ADASTRA 对随机 TF-SNP 对的覆盖率，报告救援率与覆盖率关系 | Results FOXA1；Architecture「Tools」 |
| 固定与 LLM planner 终态一致可能因任务过易 | 5 个案例中 cCRE 均无法改变结论，LLM planner 的「优势」只是省调用；在 cCRE 可改变结论的场景未测 | 影响对 LLM planner 价值的判断 | 构造 cCRE 可翻转结论的案例，比较两 planner | Results「Fixed vs. LLM-Mediated Planning」 |
| JASPAR 方向性证据被 verifier 在非方向性预测下记为 unavailable | 可能丢弃真实信号（SP1 Δ=−0.120） | 影响弃权率与灵敏度 | 对非方向性预测引入方向性 motif 证据的敏感性分析 | Results SP1 |
| AlphaGenome 交叉引用被排除出决策，但方向一致被用作支持 | 存在「用未进入决策的证据支持结论」的循环风险 | 影响结论独立性 | 预注册：交叉引用仅作事后一致性检查，或纳入为第四证据源后重跑 | Results「AlphaGenome Atlas Cross-Reference」 |
| 前沿 LLM 基线为非受控观察 | 「LLM 不弃权」的结论缺乏可量化对照 | 影响「架构强制优于 prompt」的强度 | 设计受控基准：同变异集、同提示、盲评、统计弃权率与幻觉率 | Results「Frontier LLM Baseline」 |
| 0.5 阈值与 0.95 饱和阈值为固定超参 | 阈值选择可能影响分类与救援触发 | 影响可复现性与跨模型迁移 | 阈值敏感性扫描，报告终态随阈值变化 | Architecture「Prediction Stage」 |

## 14 学到什么
### Agent 提炼的知识候选
- 可迁移概念 1：deterministic science, agentic reasoning——把生物学分类全部放在规则式可审计代码中，LLM 只做动作选择或叙述。迁移到 TF–DNA 结合课题：任何以深度学习预测 TF 结合为上游的解读流程，都应把「结合变化分类」与「LLM 叙述」在架构上分离。
- 可迁移概念 2：证据类型标签（experimental / direct_to_claim）与 CAN_CLAIM_EXPERIMENTAL 标志。迁移：在 TF–DNA 互作研究中，明确区分 ChIP-seq/ASB 等直接实验证据与 motif 打分、cCRE 注释等间接计算证据，防止计算一致性冒充实验确认。
- 可迁移概念 3：饱和（saturation）作为模型失败模式的显式标记。迁移：对任何 TF 结合预测模型（DNABERT、Enformer、AlphaGenome 等），当两等位基因预测都接近动态范围上限时，应标记为不可分辨，并优先用实验证据检验。
- 可迁移概念 4：观察依赖的分支式调查（at=π(St,𝒯), ot=Tat(St), St+1=V(St,ot)）。迁移：把 TF–DNA 结合预测当作可检验假设，用证据源（ASB、motif、cCRE、eQTL、ATAC）按不确定性选择，而非固定管线。
- 可迁移方法：10 分支 ADASTRA 决策树（no data / significant ASB with saturated model / significant ASB contradicting null / direction match / direction mismatch / non-significant with adequate power / non-significant with inadequate power 等）。迁移：可作为 TF–DNA 结合证据裁决的模板。
- 可迁移实验设计：固定优先级 vs LLM-mediated planner 的对照，报告终态一致性与工具调用数；以及「同一 planner 同变异同工具集产生分歧轨迹」作为 agency 的判据。
- 可迁移公式：调查循环三式；饱和判据 pref>0.95 且 palt>0.95；0.5 结合阈值。
- 面向本课题的迁移路径：把 ARGUS 的 verifier/stopping rule 层接到物理模拟（MD/对接）或结构预测（AlphaFold 类）输出上，用实验证据（ASB、ChIP-seq）做证伪，形成「预测–模拟–实验」闭环。

## 15 与已有知识连接
- 相似：DeepVRegulome（Dutta et al. 2025）——ARGUS 复用其预测阶段；AlphaGenome Atlas（Cheng et al. 2026）——同为变异影响预测资源，本文用作独立计算交叉引用；Enformer——被作者列为同类预测模型。
- 组合：LangGraph（LangChain 2024）——编排框架；ADASTRA（allele-specific binding 实验数据）、JASPAR（motif）、ENCODE cCRE（调控注释）——三类证据源组合。
- 冲突：与「LLM 直接解读变异」的 agentic 系统路线（Li et al. 2026; Corpas et al. 2026）在架构原则上冲突：本文主张 LLM 不得做生物学分类；与 Lin et al. 2025 的基准发现（LLM 过度分类弱证据变异）一致。
- 可迁移领域：agentic science 的证伪设计模式（Xin et al. 2025 workshop 议题）；临床变异解读中的证据分级（本文未直接引用，属 [Analysis] 候选连接）。
- 用户已有知识连接：若用户熟悉 TF–DNA 结合预测模型（DNABERT、Enformer）与 ASB 实验（ADASTRA），本文提供的是其下游解读层的架构范式；若用户熟悉 MD/对接，本文未涉及物理模拟，但 verifier/stopping rule 设计可迁移。
- 候选方向（明确标注）：将 ARGUS 的证据约束层与结构预测/物理模拟输出结合，作为「计算预测 → 实验证伪」的通用模板（unverified）。

## 16 研究想法
### Agent 生成的研究候选
1. 名称：ARGUS-MD——把分子动力学/对接的 TF–DNA 结合自由能预测接入证据约束 verifier
   - 来源局限/观察：本文上游仅 DNABERT 序列模型，无物理模拟；饱和假阴性说明序列模型有动态范围盲点。
   - 核心假设：MD/对接给出的等位基因特异性结合自由能差可作为独立证据源，补充序列模型在饱和区的不可分辨性。
   - 相对本文的增量：新增第四类证据源（物理模拟），并检验其 direct_to_claim 标签应如何设定。
   - 初步方法：对 rs6983267 类位点跑 TF–DNA 复合物 MD，计算 ref/alt 结合自由能差；接入 planner 作为可选工具。
   - 验证方式：与 ADASTRA ASB 结果比对方向一致性；在饱和预测上检验救援率。
   - 可能的失败模式：MD 力场精度不足、采样收敛慢、与实验 ASB 方向不一致。
   - 创新状态：unverified。
2. 名称：饱和感知的 TF 结合预测校准
   - 来源局限/观察：DNABERT 在 pref/palt>0.95 时饱和，FOXA1 假阴性由此产生。
   - 核心假设：对饱和区预测做温度缩放或分位数校准，可恢复等位分辨力。
   - 相对本文的增量：本文只标记饱和并转实验证据，未尝试修复模型。
   - 初步方法：在带 ASB 标签的数据上对 458 个模型做校准，评估饱和区 AUC。
   - 验证方式：校准前后在 ADASTRA 覆盖的 TF-SNP 对上比较救援率与假阴性率。
   - 可能的失败模式：饱和是数据分布问题而非校准问题，校准无效。
   - 创新状态：unverified。
3. 名称：Value-of-Information planner 替代固定优先级
   - 来源局限/观察：作者自认 planner 为固定优先级，非 value-of-information。
   - 核心假设：基于期望信息增益选证据源可进一步减少工具调用且不损失终态正确性。
   - 相对本文的增量：把 LLM planner 的启发式替换为形式化 VOI 策略。
   - 初步方法：为每个证据源估计在给定假设下的信息增益，贪心选择。
   - 验证方式：在更大变异集上与固定/LLM planner 比较终态一致性与调用数。
   - 可能的失败模式：信息增益估计依赖先验，先验错误导致次优。
   - 创新状态：unverified。
4. 名称：跨 TF 依赖的 regulatory hypothesis graph
   - 来源局限/观察：作者提出未来扩展「regulatory hypothesis graph that tracks cross-TF dependencies」。
   - 核心假设：TF 间共享位点/复合物依赖会影响单 TF 假设的裁决。
   - 相对本文的增量：本文各 TF 假设独立调查，未建模依赖。
   - 初步方法：构建 TF–TF 与 TF–位点依赖图，在 verifier 中传播证据。
   - 验证方式：在已知 TF 复合物（如 FOXA1 与其它 pioneer factor）位点上检验。
   - 可能的失败模式：依赖图错误传播导致过度弃权或过度支持。
   - 创新状态：unverified。
5. 名称：受控 LLM 幻觉基准（非编码变异 TF 结合解读）
   - 来源局限/观察：本文前沿 LLM 基线为非受控观察。
   - 核心假设：在受控基准下，架构约束相比 prompt 约束可量化降低幻觉率。
   - 相对本文的增量：把 informal observation 升级为可复现基准。
   - 初步方法：固定变异集、固定提示、盲评、统计弃权率与幻觉率。
   - 验证方式：多模型多轮重复，报告置信区间。
   - 可能的失败模式：基准本身被 LLM 训练数据污染。
   - 创新状态：unverified。