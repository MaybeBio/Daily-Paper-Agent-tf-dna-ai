## 01 基本信息
- **标题**：Benchmarking large language models for identifying transcription factor regulatory interactions
- **作者**：Noel, Lake; Hsiao, Yi-Wen; He, Yimeng; Hung, Andrew; Cui, Xiaojiang; Ray, Edward; Moore, Jason H; Peng, Pei-Chen; Huang, Xiuzhen
- **单位**：未提供（PubMed 记录未列出单位信息）
- **期刊/平台**：Bioinformatics (Oxford, England)
- **年份**：2025-12-13（在线发表日期）
- **论文类型**：基准测试/评估研究（Benchmarking study）
- **领域**：生物信息学；转录调控；大语言模型应用
- **关键词**：transcription factors, TF–target interactions, large language models, benchmarking, regulatory networks
- **DOI/arXiv 号**：10.1093/bioinformatics/btaf653
- **代码**：https://github.com/pengpclab/LLM-TF-interactions（交互式 Python notebook）
- **数据**：TRRUST v2 人类数据集（8432 对 TF–target 互作）；TFLink 人类小规模互作表（5148 对实验来源互作）
- **阅读日期**：2026-05-13（卡片生成日）
- **在该课题方向中的位置**：本文属于「蛋白质–DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法」方向中的 **LLM 作为知识检索/问答工具** 的基准测试研究。它不涉及结构预测、分子模拟或结合机制建模，而是评估通用大语言模型能否从预训练知识中准确回忆 TF–target 调控关系（互作存在性与调控类型）。其核心价值在于：为「AI 辅助转录调控知识获取」提供系统评测框架，并揭示 prompt 工程、温度参数、多轮对话对 LLM 输出质量的影响。

---

## 02 一句话总结
本文用 8432 条 TRRUST v2 文献策展的人类 TF–target 互作对和 5148 条 TFLink 实验来源互作对，系统评测了 Claude 3.5 Sonnet、GPT-4o、Gemini 1.0 Pro/2.0 Flash、Llama3 8b 四个通用 LLM 在单轮/多轮查询下识别 TF–target 调控关系（方向与类型）的能力，发现 Claude 3.5 Sonnet 和 GPT-4o 整体最优（平衡准确率最高约 50–73%），零温度提升可重复性、多轮提示提升多数模型准确率、排除 unknown 类型可显著提升表现，但所有模型仍存在幻觉与数据泄漏风险。

---

## 03 研究问题
- **具体问题**：通用预训练大语言模型（LLM）能否准确识别人类 TF–target 调控互作及其调控类型（激活/抑制/未知）？其表现受哪些因素影响（模型选择、温度参数、提示策略、调控类别）？
- **为什么重要**：TF–target 互作是基因调控网络的核心组成部分，与疾病机制密切相关。现有计算方法（如 tREMAP、InteGRaNet、TGPred）和策展数据库（TRRUST、TFLink）需要专业知识或繁琐查询，而 LLM 聊天机器人提供了一种无需专门训练的、自然语言交互的替代方案，可能大幅降低非计算背景研究者的使用门槛。
- **精确的 Can 问题**：Can general-purpose pre-trained LLMs, without fine-tuning, accurately identify TF–target regulatory interactions and their regulation types from literature-curated and experimentally derived data, under varying temperature settings and prompting strategies?

---

## 04 背景与发展脉络
> 注：以下脉络基于本文引言与讨论，属于「仅本文框架」，未经外部系统核验。

1. **实验方法时代**：ChIP-seq、RNA-seq 等高通量技术推动了 TF–target 互作的全基因组鉴定，催生了 GTRD、ENCODE、TRANSFAC、JASPAR、ChEA 等实验驱动数据库。
2. **文献策展数据库时代**：TRRUST v2、TFLink、hTFtarget 等通过人工阅读文献、文本挖掘策展 TF–target 关系，提供高质量 gold standard，但更新慢、覆盖有限。
3. **计算方法时代**：tREMAP、InteGRaNet、TGPred 等机器学习/统计方法尝试整合多源数据预测 TF–target 互作，但需要特征工程、训练数据和计算资源，对非专家不友好。
4. **LLM 时代（本文位置）**：通用 LLM（Claude、GPT、Gemini、Llama）凭借大规模预训练语料中蕴含的生物学知识，可作为零样本（zero-shot）知识检索工具。本文首次系统评测其在 TF–target 互作识别上的基线能力，建立评测框架，并探索温度、多轮提示、unknown 排除等策略对性能的影响。

**本文主张的位置**：在「实验 → 策展 → 计算预测 → LLM 知识检索」的演进链条中，本文为 LLM 作为轻量级、可访问的 TF–target 知识查询工具提供首个系统基准，但不声称 LLM 可替代实验或专用计算方法。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有工具门槛高 | 数据库查询和计算方法需要专业知识、编程技能或计算资源 | 传统数据库需手动检索多个来源；计算方法需特征工程和训练 | Introduction 第 1–2 段 |
| LLM 输出不可控 | 模型偶尔返回非指定格式（如 "induction"、"autoactivation"、完整句子） | 提示词不够严格；模型对指令遵循能力有限 | Results 3.1 节，<2% 非格式响应 |
| 可重复性差 | 同一查询多次运行结果不一致 | 温度参数控制随机性，默认温度下输出有波动 | Results 3.2 节，零温度降低标准差 |
| 数据泄漏风险 | 文献策展数据可能已包含在 LLM 训练语料中，导致虚高表现 | TRRUST 是公开文献数据库，LLM 训练数据可能覆盖 | Discussion 第 2 段（作者明确提及） |
| unknown 类别干扰 | 含 unknown 调控类型的样本拉低准确率 | unknown 表示未明确或情境依赖的调控效应，模型难以判断 | Results 3.4 节，排除后准确率提升 9.5–24.1% |
| 小模型/本地部署性能不足 | Llama3 8b 在多数指标上落后于商业 API 模型 | 参数量小、知识覆盖有限 | Results 3.1–3.5 节，Llama3 8b 整体最低 |

---

## 06 核心思想

### 1) 表面方法
用固定模板提示词（"How does transcription factor {TF} regulate {target} in humans? Restrict your answer to one word and nothing more: repression, activation, or unknown."）对四个 LLM 进行单轮查询，对 8432 条 TRUST 互作对按四种调控方向（bidirectional、ambiguous、self-regulated、unidirectional）分别评测；随后在零温度、多轮提示、排除 unknown 等条件下重复评测；最后用 TFLink 实验数据（5148 对）做二分类（yes/no）验证，并合成负样本对。

### 2) 核心洞察
- **LLM 具备零样本 TF–target 知识检索能力**，但性能高度依赖模型选择与提示策略，且远未达到可靠替代策展数据库的水平。
- **调控方向类别是性能的关键调节变量**：self-regulated 和 bidirectional 对模型更具挑战性，而 unidirectional 相对简单。
- **prompt 工程 > 模型参数**：多轮提示（引导模型先推理再回答）比单纯调温度更能提升准确率，说明 LLM 的推理链（chain-of-thought）能力可被有效激发。
- **unknown 类别的处理策略直接影响评测结论**：排除 unknown 后性能大幅提升，提示评测设计需明确区分「互作存在性」与「调控类型判定」两个子任务。

### 3) 可能的普适教训 [Analysis]
- 对「LLM 用于科学知识查询」类任务，**评测框架的设计（类别划分、负样本构造、指标选择）比模型本身更能影响结论**。本文的类别分层（bidirectional/ambiguous/self-regulated/unidirectional）和 unknown 排除策略是值得借鉴的评测范式。
- **零温度 + 多轮提示** 是低成本提升 LLM 科学问答可靠性的通用组合拳，可迁移到其他生物医学知识检索任务。
- 对 TF–DNA 互作课题而言，LLM 的「知识回忆」能力与「机制推理」能力是两回事：本文证明 LLM 能回忆「谁调控谁」，但未测试其能否解释「如何调控」（如结合位点、协同因子、染色质背景）。这为后续研究留下空间。

---

## 07 方法总览
- **输入**：TF–target 互作对（TF 名称 + 靶基因名称），来自 TRRUST v2（8432 对，含调控类型标注）和 TFLink（5148 对实验来源互作，无调控类型标注）。
- **输出**：模型对每个互作对的调控类型判定（activation/repression/unknown）或互作存在性判定（yes/no）。
- **模块**：
  1. 数据预处理：从 TRRUST v2 提取四类调控方向子集（bidirectional 206、ambiguous 801、self-regulated 24、unidirectional 7390→随机抽 250）；从 TFLink 构建正负样本集（正：5148 对；负：随机打乱 TF–target 配对并排除已知互作，250 对）。
  2. 模型 API 调用：Claude 3.5 Sonnet（2024-06-20）、GPT-4o（2024-05-13）、Gemini 1.0 Pro（gemini-1.0-pro-latest）、Llama3 8b（Ollama 本地部署）。
  3. 提示策略：单轮固定模板；多轮（先推理后回答）；温度默认 vs 零温度。
  4. 评测指标：accuracy、balanced accuracy、macro F1、macro precision、macro recall。
- **训练**：无训练/微调，全部为零样本推理。
- **反馈回路**：无（静态评测）。
- **文字流程**：从数据库提取互作对 → 按类别分层抽样 → 构造提示词 → 调用 LLM API → 解析单字响应 → 与 ground truth 比对 → 计算多类指标 → 在不同温度/提示策略下重复 → 用 TFLink 数据做交叉验证。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 数据分层（TRRUST 四类方向） | 按调控方向分组评测 | 不同方向类别的难度差异大，混合评测会掩盖模型短板 | 输入：8432 对；输出：4 个子集 | Results 3.1 节，各方向类别性能差异显著 | 移除后无法定位模型在哪些方向类别上失效 |
| 单轮固定提示 | 统一查询格式，保证可比性 | 提示词差异会引入混淆变量 | 输入：TF+target；输出：单字响应 | Results 3.1 节 | 移除后评测结果不可比 |
| 零温度设置 | 消除采样随机性，提升可重复性 | 默认温度下同一查询多次结果不同 | 输入：temperature=0；输出：确定性响应 | Results 3.2 节，标准差显著降低 | 移除后无法区分模型能力与随机波动 |
| 多轮提示 | 引导模型先推理再回答 | 单轮直接回答可能跳过推理步骤 | 输入：3 轮对话；输出：最终单字响应 | Results 3.3 节，多数模型准确率提升 | 移除后 self-regulated 等难类别的性能提升消失 |
| unknown 排除策略 | 区分「互作存在性」与「调控类型判定」 | unknown 类别定义模糊，干扰类型判定评测 | 输入：含/不含 unknown 的样本集；输出：两组指标 | Results 3.4 节，排除后提升 9.5–24.1% | 移除后无法评估模型在明确调控类型上的真实能力 |
| TFLink 交叉验证 | 用实验来源数据验证泛化性 | 文献策展数据可能存在数据泄漏 | 输入：5148 正 + 250 负；输出：二分类指标 | Results 3.5 节，Claude 3.5 Sonnet 最佳 72.6% | 移除后无法排除数据泄漏对结论的污染 |
| 负样本合成 | 构造不存在的 TF–target 对 | 二分类任务需要负类 | 输入：打乱配对；输出：250 负样本 | Methods 2.1 节 | 移除后无法评估误报率 |

---

## 09 关键公式符号
本文为基准测试研究，无数学模型或公式。核心指标定义如下（Methods 2.5 节）：

- **Accuracy** = (TP + TN) / (TP + TN + FP + FN)
- **Balanced Accuracy** = (TPR + TNR) / 2，其中 TPR = TP/(TP+FN)，TNR = TN/(TN+FP)
- **Macro Precision** = (1/C) Σᵢ Precisionᵢ，C 为类别数
- **Macro Recall** = (1/C) Σᵢ Recallᵢ
- **Macro F1** = 2 × (Macro Precision × Macro Recall) / (Macro Precision + Macro Recall)

符号说明：TP = 真阳性，TN = 真阴性，FP = 假阳性，FN = 假阴性，i 为类别索引。

---

## 10 实验设计与证据链
- **数据集**：
  - TRRUST v2 人类数据集：8432 对 TF–target 互作，含调控类型（activation/repression/unknown）标注；按方向分为 bidirectional（206）、ambiguous（801）、self-regulated（24）、unidirectional（7390→随机抽 250）。
  - TFLink 人类小规模互作表：5148 对实验来源互作（GTRD ChIP-seq 或 DoRoTHea ChIP-seq+RNA-seq），无调控类型标注；负样本为 250 对合成非互作对。
- **规模**：每模型每子集查询 10 次（iteration），共 4 模型 × 4 方向 × 10 次 + 4 模型 × 2 数据集 × 10 次。
- **指标**：accuracy、balanced accuracy、macro F1、macro precision、macro recall。
- **基线**：随机猜测（三分类 33.3%，二分类 50%）。
- **评测协议**：单轮 vs 多轮；默认温度 vs 零温度；全样本 vs 排除 unknown。
- **硬件/预算**：Apple M2 芯片、16GB 内存、无 GPU（仅 Llama3 8b 本地部署，其余 API 调用）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|--------------|-------------------|------|
| 单轮基准测试（TRRUST） | LLM 能否识别 TF–target 调控类型 | 4 模型 × 4 方向类别，默认温度 | Claude 3.5 Sonnet 和 GPT-4o 平衡准确率最高（约 45–50%），均优于随机猜测（33%） | 通用 LLM 具备零样本调控类型识别能力 | 不能证明 LLM 可替代策展数据库；准确率仍偏低 | Results 3.1 节，Fig. 2 |
| 零温度测试 | 零温度是否提升可重复性 | 默认 vs 零温度，同模型同子集 | 零温度下标准差显著降低，部分类别准确率略降 | 零温度提升可重复性，代价是轻微性能损失 | 不能证明零温度总是最优 | Results 3.2 节，Fig. 3 |
| 多轮提示测试（self-regulated） | 多轮推理能否提升难类别性能 | 单轮 vs 多轮，self-regulated 子集 | Claude 3.5 Sonnet 准确率提升 32.6%（相对提升约 50%） | 多轮提示可显著提升难类别表现 | 仅测试 self-regulated，未覆盖其他方向 | Results 3.3 节，Fig. 4 |
| unknown 排除测试 | 排除 unknown 是否提升准确率 | 全样本 vs 排除 unknown 样本 | 排除后平衡准确率提升 9.5–24.1%，unidirectional 接近 70% | unknown 类别是性能的主要拖累因素 | 不能证明模型对明确调控类型的判断完全可靠 | Results 3.4 节，Fig. 5 |
| TFLink 交叉验证 | LLM 能否泛化到实验来源数据 | 4 模型 × 2 数据集（无 TRRUST / 仅 TRRUST） | Claude 3.5 Sonnet 最佳 72.6%（无 TRRUST），GPT-4o 次之 64.0% | 实验来源数据上性能优于文献策展数据 | 不能排除数据泄漏；负样本为合成数据 | Results 3.5 节，Fig. 6 |
| 采样稳健性检验 | 单次采样是否可靠 | 10 次随机采样 vs 单次采样 | 10 次采样结果与单次采样一致 | 单次采样结果可靠 | 仅验证了 unidirectional 子集 | Results 3.1 节，Fig. 2（补充） |

---

## 11 结论正确解读
- **任务范围**：本文仅评测 LLM 对「TF–target 互作存在性」和「调控类型（激活/抑制/未知）」的**知识回忆**能力，不涉及结合位点预测、结合亲和力、结构机制、染色质背景等更深层的 TF–DNA 互作问题。
- **Oracle/真值输入**：ground truth 来自 TRRUST v2（文献策展）和 TFLink（实验来源），两者均为人工/半自动策展，可能存在标注噪声和覆盖偏差。
- **端到端状态**：评测为「提示词 → 单字响应 → 比对」的端到端流程，但模型输出未经过任何后处理或置信度过滤。
- **算力成本**：API 模型（Claude、GPT、Gemini）成本未报告；Llama3 8b 可在个人电脑运行（Apple M2 16GB），但性能最低。
- **历史数据依赖**：LLM 训练语料可能已包含 TRRUST/TFLink 中的文献，存在数据泄漏风险，作者明确承认无法量化其影响。
- **最难情形**：self-regulated（样本仅 24 对，统计功效低）和 bidirectional 互作对模型最具挑战性；unknown 类型是主要干扰源。
- **群体/领域边界**：仅人类 TF–target 互作；未测试其他物种、非 TF 调控因子、细胞类型特异性。
- **不确定性**：所有指标均为 10 次迭代的均值±标准差，但未报告置信区间或显著性检验。

**有边界的复述**：在人类 TF–target 互作知识回忆任务上，Claude 3.5 Sonnet 和 GPT-4o 的平衡准确率约为 45–50%（三分类）和 60–73%（二分类），显著优于随机猜测但远未达到可靠水平；零温度提升可重复性、多轮提示提升难类别性能、排除 unknown 可显著提升表观准确率；结果受数据泄漏和 ground truth 质量限制，不能外推到机制性 TF–DNA 结合问题。

---

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 数据泄漏风险 | TRRUST 为公开文献数据库，LLM 训练语料可能已包含，导致性能虚高 | 使用更近期、未公开的数据集进行评测 | Discussion 第 2 段 |
| 缺乏细胞类型特异性 | 现有 ground truth 未区分细胞类型，无法评估 LLM 在特定情境下的表现 | 整合单细胞或空间组学数据，构建细胞类型特异的评测集 | Discussion 第 3 段 |
| 幻觉与不一致响应 | 模型偶尔产生生物学上不合理的回答 | 开发可解释 AI 框架，增强输出可验证性 | Discussion 第 3 段 |
| 仅覆盖人类数据 | 未测试其他物种的 TF–target 互作 | 扩展至多物种评测 | Discussion 第 3 段（隐含） |
| 样本量限制 | self-regulated 仅 24 对，统计功效不足 | 扩充稀有类别样本量 | Results 3.1 节（隐含） |
| 未测试微调模型 | 仅评测通用预训练模型，未涉及领域微调 | 探索领域适配的微调策略 | Discussion 第 2 段（隐含） |

---

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| 平衡准确率最高仅约 50%（三分类），但作者仍称「有潜力」 | 50% 仅比随机猜测高 17 个百分点，实际可用性存疑；可能因提示词设计不佳而低估模型能力 | 若结论被过度解读，可能误导研究者依赖 LLM 而非策展数据库 | 用更多提示词变体（如 few-shot、chain-of-thought）重测，看性能上限 | Results 3.1 节，Fig. 2 |
| unknown 排除后性能大幅提升，但排除标准可能引入选择偏差 | 排除的 unknown 样本可能恰好是模型最不确定的样本，排除后高估模型在「明确」样本上的能力 | 评测设计应区分「模型不确定性」与「ground truth 模糊性」 | 对 unknown 样本单独分析模型输出分布，而非简单排除 | Results 3.4 节，Fig. 5 |
| 负样本为随机打乱配对，可能过于简单 | 真实场景中「非互作」往往与「互作」在序列/功能上相似，随机配对低估了判别难度 | 若负样本太简单，二分类准确率（72.6%）可能虚高 | 用保守负样本（如相近家族 TF、同通路基因）重测 | Methods 2.1 节 |
| 多轮提示仅测试 self-regulated 子集 | 该子集仅 24 对，提升 32.6% 可能受小样本噪声影响 | 无法确认多轮提示对其他类别的普适性 | 在 bidirectional 和 ambiguous 子集上重复多轮测试 | Results 3.3 节，Fig. 4 |
| 未报告 API 调用成本与延迟 | 实际应用中成本可能成为限制因素 | 影响方法可推广性评估 | 补充各模型的 token 消耗与响应时间数据 | 未提供 |
| 未与其他计算方法（如 tREMAP、TFLink 预测器）对比 | 缺乏与专用工具的横向比较，无法判断 LLM 的相对优势 | 若专用工具显著更优，LLM 的实用价值需重新评估 | 在同一数据集上运行现有计算方法并对比 | 未提供 |

---

## 14 学到什么
> 标题：Agent 提炼的知识候选

1. **评测框架可迁移**：本文的「调控方向分层 + unknown 排除 + 多轮提示 + 零温度」评测范式，可直接迁移到其他蛋白质–DNA 互作知识问答任务（如「某 TF 是否结合某增强子」「某突变是否影响结合」）。对 TF–DNA 结合机制研究，可构建分层评测集（如结合/不结合、高/低亲和力、直接/间接结合），系统评估 LLM 的知识边界。

2. **Prompt 工程是 LLM 应用的核心杠杆**：多轮提示（先推理后回答）在 self-regulated 任务上带来 32.6% 的相对提升，说明 LLM 的隐式推理能力可被结构化提示激发。对 TF–DNA 结合机制问题，可设计「先描述结合位点特征，再判断结合与否」的两阶段提示，提升推理质量。

3. **unknown 类别的处理策略影响结论**：在 TF–DNA 互作数据中，「未知调控类型」或「情境依赖调控」是常态。评测 LLM 时应明确区分「互作存在性」与「调控效应方向」两个子任务，避免将 ground truth 模糊性误判为模型缺陷。

4. **零温度 + 多轮提示是低成本可靠性组合**：对需要可重复输出的科学查询场景（如文献综述辅助、假设生成），零温度可消除随机性，多轮提示可提升准确率，两者组合无需微调即可获得稳定增益。

5. **数据泄漏是 LLM 评测的固有风险**：文献策展数据（如 TRRUST）很可能已进入 LLM 训练语料。对 TF–DNA 互作研究，应优先使用实验来源数据（如 ChIP-seq、HT-SELEX 原始数据）或近期未公开数据构建评测集，并报告泄漏风险。

6. **小模型本地部署的可行性边界**：Llama3 8b 在个人电脑（Apple M2 16GB）可运行，但性能显著低于 API 模型。对资源受限环境，需权衡模型规模与任务复杂度，或考虑蒸馏/量化方案。

---

## 15 与已有知识连接
- **TRRUST v2**（Han et al. 2018）：本文 ground truth 来源之一，是文献策展的 TF–target 互作数据库。与 TFLink、hTFtarget 等同类数据库可交叉验证。
- **TFLink**（Liska et al. 2022）：本文实验来源 ground truth，整合多数据库并提供证据等级标注。其「实验来源 vs 文献来源」的区分对评测 LLM 数据泄漏至关重要。
- **GTRD**（Kolmykov et al. 2021）：ChIP-seq 衍生 TF 结合数据库，本文 TFLink 数据中实验来源互作的主要贡献者。与 TF–DNA 结合机制研究直接相关。
- **DoRoTHea**（Garcia-Alonso et al. 2018；Badia-I-Mompel et al. 2022；Müller-Dott et al. 2023）：整合 ChIP-seq 和 RNA-seq 的调控网络数据库，本文实验来源互作另一贡献者。
- **LLM 生物医学应用综述**（如 Meyer et al. 2023）：本文引用的 LLM 在学术研究中应用背景，可扩展至更广泛的 LLM-for-science 文献。
- **Prompt 工程研究**（如 Yin et al. 2023）：本文引用的「please」措辞影响 Llama3 响应的先验工作，与 LLM 提示敏感性研究脉络一致。
- **[Analysis] 可连接方向**：本文未涉及但可延伸的领域包括——(1) 用 LLM 生成 TF–DNA 结合机制假设（如结合位点突变效应预测）；(2) LLM 与结构预测工具（AlphaFold、RoseTTAFold）的协同；(3) LLM 辅助 ChIP-seq/HT-SELEX 数据分析的提示模板设计。

---

## 16 研究想法
> 标题：Agent 生成的研究候选

1. **候选名称**：TF–DNA 结合机制问答的分层评测框架（Hierarchical Benchmark for TF–DNA Binding Mechanism QA）
   - **来源局限/观察**：本文仅评测「谁调控谁」和「激活/抑制」，未触及「如何结合」「结合亲和力」「突变效应」等机制性问题。
   - **核心假设**：LLM 对 TF–DNA 结合机制问题的回答准确率显著低于互作存在性问题，且可通过结构化提示（如提供结合位点序列上下文）提升。
   - **初步方法**：构建包含结合位点序列、ChIP-seq 峰、HT-SELEX 亲和力数据的评测集，设计「结合与否→亲和力等级→突变效应」三级问题，评测多个 LLM。
   - **验证方式**：与实验数据（如 ENCODE、Cis-BP）比对，计算分层准确率与置信度校准。
   - **创新状态**：unverified

2. **候选名称**：LLM 与结构预测协同的 TF–DNA 结合位点突变效应预测（LLM-Structure Hybrid for TF–DNA Mutation Effect Prediction）
   - **来源局限/观察**：本文证明 LLM 能回忆互作知识，但未利用结构信息；AlphaFold 等工具对蛋白–DNA 复合物预测仍有限。
   - **核心假设**：LLM 的序列知识 + 结构预测的几何约束可提升突变效应预测准确率，优于任一单模型。
   - **初步方法**：用 LLM 提取 TF 家族保守 motif 与已知突变文献，用 AlphaFold3 或 RoseTTAFold 预测突变体结构，融合两者特征训练分类器。
   - **验证方式**：在公开突变效应数据集（如 SELEX 突变库、ClinVar 相关变异）上对比单模型与混合模型。
   - **创新状态**：unverified

3. **候选名称**：细胞类型特异的 TF–target 互作 LLM 提示模板（Cell-type-specific Prompting for TF–target Interaction Retrieval）
   - **来源局限/观察**：本文 ground truth 缺乏细胞类型维度，作者在讨论中明确承认此局限。
   - **核心假设**：在提示中注入细胞类型上下文（如「在肝细胞中」）可提升 LLM 对情境依赖调控的识别准确率。
   - **初步方法**：从单细胞多组学数据（如 scRNA-seq + scATAC-seq）构建细胞类型特异的 TF–target 评测集，设计含/不含细胞类型上下文的提示对，对比性能差异。
   - **验证方式**：与单细胞调控网络推断工具（如 SCENIC、CellOracle）输出比对。
   - **创新状态**：unverified

4. **候选名称**：LLM 幻觉检测器用于 TF–target 知识过滤（Hallucination Detector for TF–target Knowledge Filtering）
   - **来源局限/观察**：本文承认 LLM 偶尔产生生物学上不合理的响应，但未系统量化或过滤。
   - **核心假设**：LLM 对同一互作对多次查询的响应一致性可作为幻觉的代理指标，一致性低的回答更可能错误。
   - **初步方法**：对每个互作对多次查询，计算响应熵与自洽性，训练一个轻量分类器预测回答正确性，过滤低置信度输出。
   - **验证方式**：在 TRRUST/TFLink 上对比过滤前后的准确率与覆盖率。
   - **创新状态**：unverified

5. **候选名称**：跨物种 TF–target 互作 LLM 泛化性评估（Cross-species Generalization of LLMs for TF–target Interactions）
   - **来源局限/观察**：本文仅覆盖人类数据，未测试其他物种。
   - **核心假设**：LLM 对模式生物（小鼠、果蝇、酵母）的 TF–target 互作识别准确率低于人类，且与训练数据覆盖度相关。
   - **初步方法**：从 RegulonDB、Yeastract 等数据库构建多物种评测集，评测同一组 LLM，分析准确率与物种、TF 家族的关系。
   - **验证方式**：与物种特异的策展数据库比对，报告分层准确率。
   - **创新状态**：unverified