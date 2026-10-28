## 01 基本信息
- **标题**: Fine-tuned GPT-based foundation models effectively reconstruct bacterial transcriptional regulatory networks from literature
- **作者与单位**: Romero-Vilchis, Jose; Barajas-Sanchez, Maximiliano; Azpeitia-Garcia, Karyme-Ivette; Posada-Reyes, Ali-Berenice; Collado-Vides, Julio; Mendez-Cruz, Carlos-Francisco（未提供单位，推测为墨西哥国立自治大学 UNAM，因致谢提及 Programa de Genómica Computacional, UNAM）
- **期刊/预印本平台**: Frontiers in Artificial Intelligence
- **年份**: 2026-04-29
- **论文类型**: 研究论文（方法学 + 应用）
- **领域**: 计算生物学 / NLP / 转录调控网络重建
- **关键词**: 转录调控网络（TRN）、GPT、LLaMA-3、GPT-4o mini、微调、关系抽取（RE）、命名实体识别（NER）、Salmonella、E. coli
- **DOI/arXiv 号**: 10.3389/frai.2026.1788196
- **代码**: https://github.com/laigen-unam/GPT-trn-reconstruction
- **数据**: 1,562 句 E. coli 文献句子（微调）；264 篇 Salmonella 全文（评估）；2,278 篇 Salmonella 文献（大规模重建）
- **阅读日期**: 未提供
- **在课题方向中的位置**: 本文属于「TF–DNA 互作 × AI/深度学习」方向，聚焦于从文献文本中自动抽取 TF–靶基因/操纵子之间的调控关系（激活/抑制/调控），并重建细菌转录调控网络。与结构预测或 MD 模拟不同，本文不涉及物理机制，而是利用 GPT 基础模型的语义理解能力进行关系分类，属于 NLP 驱动的知识抽取与网络重建。

## 02 一句话总结
本文通过监督微调两个 GPT 基础模型（LLaMA-3 8B 和 GPT-4o mini），以 E. coli 文献句子为训练数据，预测 TF 与靶基因/操纵子之间的调控效应类型（激活/抑制/调控/无关系），并以集成投票策略在 Salmonella 全文文献上重建转录调控网络，在 264 篇人工精选文献上达到 F1=0.645，优于此前基于 BERT 的方法。

## 03 研究问题
- **具体问题**: 如何从生物医学文献中自动、准确地抽取细菌转录调控相互作用（TF–靶基因/操纵子），并重建完整的转录调控网络（TRN）？
- **为什么重要**: 细菌 TRN 是理解环境适应、致病机制和耐药性的基础。目前高质量 TRN 依赖人工文献审编（如 RegulonDB），耗时费力且覆盖不全。自动化抽取可加速 TRN 构建，尤其对缺乏现成网络的细菌。
- **现有方法不足**: 传统基于规则的方法需要人工构建模式，难以扩展；经典机器学习需要大量标注数据；已有的 BERT 基础模型方法（如 Varela-Vega et al., 2024）仅做二分类（真/假交互），无法预测调控效应类型，且在实际文献上性能下降明显（F1 低至 0.26，如 Gill et al., 2024）。
- **精确研究问题**: Can fine-tuned GPT-based foundation models predict the type of regulatory effect (activation/repression/regulation) between a transcription factor and a regulated element from literature sentences, and can an ensemble of such models reconstruct a bacterial TRN from full-text articles with performance surpassing prior BERT-based approaches?

## 04 背景与发展脉络
*注：以下脉络基于本文引言与讨论，属「仅本文框架」，未经外部系统核验。*

1. **人工审编时代**: RegulonDB 等数据库依赖训练有素的审编人员从文献中手工提取调控相互作用。优点：高精度；缺点：耗时、难以跟上文献增长速度。
2. **规则/模式匹配方法**: 早期工作（Sarić et al., 2005; Rodríguez-Penagos et al., 2007; Leitner et al., 2013）使用手工构建的文本模式和语法规则抽取基因-蛋白相互作用。优点：可解释；缺点：规则构建劳动密集、难以覆盖多样化的语言表达。
3. **经典机器学习**: 基于特征工程的方法需要大量人工标注数据，泛化能力有限。
4. **BERT 基础模型**: Gill et al. (2024) 使用 BioBERT 和 BERN2 进行基因-蛋白交互抽取，在标准数据集上表现优异，但在真实文献审编场景下性能大幅下降（F1=0.26）。Varela-Vega et al. (2024) 比较了六种 BERT 变体，在 E. coli 句子分类上达到 F1≈0.55-0.89，但仅做二分类。
5. **GPT 基础模型（本文位置）**: 首次将 GPT 架构（LLaMA-3、GPT-4o mini）用于细菌 TF–基因调控关系抽取，利用其大规模预训练知识，通过少量监督微调实现四分类（激活/抑制/调控/无关系），并引入集成投票策略提升网络重建性能。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 人工审编效率低 | TRN 数据库构建需数年人工工作，许多细菌缺乏现成网络 | 文献数量爆炸式增长，人工阅读和提取无法跟上 | Introduction: "traditional procedure... manual extraction... accumulate years of curation work" |
| 现有 NLP 方法性能不足 | BERT 方法在真实文献上 F1 仅 0.26（Gill et al.） | 标准数据集与真实文献存在分布差异；仅做二分类无法区分调控效应类型 | Discussion: "performance declines... F1-score of 0.26" |
| 无法预测调控效应类型 | 已有方法仅判断交互是否存在，不区分激活/抑制 | 任务被简化为二分类，丢失关键生物学信息 | Introduction: "prevailing approach is to predict only if the interaction is true or false" |
| 假阳性过多 | 网络重建 Precision 低（0.55） | 模型将无关系句子误判为调控交互；训练数据仅含典型表达 | Results 表 7: Precision=0.55; Discussion: "high number of false positive instances" |
| 非典型语言表达难以处理 | 缺乏规范调控动词的句子被误分类 | 训练数据来自审编流程，偏向典型表达；模型未见过非原型例句 | Discussion: "limited generalization to correctly predict the effect of sentences... not prototypical" |
| 调控效应矛盾 | 同一 TF-靶基因对在不同句子中出现不同效应 | 生物学上同一 TF 在不同条件下可激活或抑制；模型保留所有效应 | Methods: "When the same TF-regulatory element appeared with different regulatory effects across multiple sentences, all interactions were kept" |

## 06 核心思想
1. **表面方法**: 使用两个 GPT 基础模型（LLaMA-3 8B 和 GPT-4o mini），通过监督微调进行四分类任务（activator/repressor/regulator/no_relation）。输入为匿名化后的句子（实体替换为 @TF$ 和 @Regulated$ 标签），输出为调控效应类别。微调后，模型对全文文献中的句子进行推理，聚合为唯一调控交互，并通过两模型投票（ensemble）得到最终网络。

2. **核心洞察**: 
   - **匿名化是关键**: 将实体名称替换为通用标签，迫使模型学习上下文模式和句法结构，而非记忆特定基因/蛋白名称。这使得模型可以泛化到不同细菌的文献。
   - **生成模型的优势**: GPT 架构在预训练阶段学习了丰富的语言知识和推理能力，微调所需数据量远小于从头训练的 BERT 模型，且能捕捉更复杂的语义关系。
   - **集成投票提升精度**: 两个独立模型（不同架构、不同训练方式）的共识可显著减少假阳性，提高网络重建的 Precision。

3. **可能的普适教训** [Analysis]: 
   - 在生物医学文本挖掘中，实体匿名化是一种简单而有效的泛化策略，可跨物种迁移。
   - 生成式 LLM 在少样本微调下即可超越判别式模型，尤其在需要语义推理的任务中。
   - 集成方法（多模型投票）在 Precision 和 Recall 之间提供了可调的平衡点，适合对假阳性敏感的生物网络重建任务。

## 07 方法总览
- **输入**: 文献句子（来自 E. coli 微调集或 Salmonella 全文），句子中 TF 和靶基因/操纵子实体已通过词典识别并匿名化为 @TF$ 和 @Regulated$ 标签。
- **输出**: 每个句子的调控效应分类（activator/repressor/regulator/no_relation），聚合为唯一调控交互（TF-regulated element-effect），最终构建 TRN 图。
- **模块**:
  1. **数据预处理**: PDF→文本转换（GROBID）、句子分割与分词（Stanford CoreNLP）、词典实体识别、匿名化。
  2. **微调**: 两个 GPT 模型分别用 E. coli 1,562 句微调，5 折交叉验证选最优模型。
  3. **推理**: 对 Salmonella 文献句子进行批量分类。
  4. **网络构建**: 去除 no_relation，提取唯一交互，处理矛盾效应（保留所有效应）。
  5. **集成**: 两模型投票（仅保留两模型一致预测的交互）。
  6. **网络分析**: 度分布、社区检测、过表达分析（PANTHER）。
- **训练**: GPT-4o mini 通过 OpenAI API 微调（3 epochs, batch size 1）；LLaMA-3 通过 Unsloth 框架微调（4-bit 量化 + LoRA, rank 16, lr 2e-4, batch size 8）。
- **反馈回路**: 无显式反馈回路；模型推理为一次性前向过程。
- **假设**: (1) 文献句子包含足够的上下文信息来判断调控效应；(2) 词典能准确识别 TF 和靶基因实体；(3) 训练数据（E. coli）的语义模式可迁移到其他细菌（Salmonella）。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 实体匿名化 | 将 TF 和靶基因名称替换为 @TF$ 和 @Regulated$ 标签 | 防止模型记忆特定实体名称，强制学习上下文模式，实现跨物种泛化 | 输入: 原始句子；输出: 匿名化句子 | Methods 节: "entity mentions were anonymized using the @TF$ and @Regulated$ pre-defined tags" | [预期] 模型将过拟合训练集中的实体名称，无法泛化到 Salmonella 等新物种 |
| GPT 微调（LLaMA-3 8B） | 将通用 LLM 适配到调控效应分类任务 | 利用预训练知识，少量标注数据即可获得高精度 | 输入: 匿名化句子；输出: 四类概率分布 | Results 表 4-5: F1=0.892 (test) | [预期] 失去 LLM 语义理解能力，性能大幅下降 |
| GPT 微调（GPT-4o mini） | 同上，独立训练的第二模型 | 提供多样性，用于集成投票 | 输入: 匿名化句子；输出: 四类概率分布 | Results 表 4-5: F1=0.874 (test) | [预期] 集成失去多样性，投票退化为单模型 |
| 集成投票 | 仅保留两模型一致预测的交互 | 减少假阳性，提高 Precision | 输入: 两模型预测结果；输出: 共识交互集 | Results 表 7: Precision 0.55→0.64 (vs 单模型) | [实测] Precision 下降至 0.55，F1 下降至 0.60（表 7） |
| 网络构建与矛盾处理 | 聚合唯一交互，保留矛盾效应 | 同一 TF-靶基因对在不同条件下可有不同效应 | 输入: 分类后的句子；输出: TRN 图 | Methods: "all interactions were kept" | [预期] 网络包含生物学上合理的多效调控边 |
| 词典 NER | 识别句子中的 TF 和靶基因实体 | 确定候选交互对 | 输入: 原始句子；输出: 实体标注句子 | Methods 节: "Using TF and regulated element dictionaries" | [预期] 无法识别新基因或变体名称，召回率下降 |

## 09 关键公式符号
本文为 NLP 分类任务，无复杂数学公式。核心指标定义如下：

- **Precision** = TP / (TP + FP)
  - TP: 预测为某调控效应且与人工审编一致的交互数
  - FP: 预测为某调控效应但人工审编中不存在的交互数
- **Recall** = TP / (TP + FN)
  - FN: 人工审编中存在但模型未预测出的交互数
- **F1-Score** = 2 × Precision × Recall / (Precision + Recall)
- **MCC** (Matthews Correlation Coefficient) = cov(c, l) / (σc × σl)
  - c: 真实类别向量；l: 预测类别向量；cov: 协方差；σ: 标准差
  - 用于多分类不平衡数据的相关性度量

## 10 实验设计与证据链
**数据集与规模**:
- 微调集: 1,562 句 E. coli 文献句子（来自 119 篇文章），四类分布见表 2（未提供具体数值）
- 评估集: 264 篇 Salmonella 全文文章，人工审编出 909 个唯一调控交互
- 大规模应用: 2,278 篇 Salmonella 文献（含 1,381 篇全文 + 897 篇摘要）

**指标**: Precision, Recall, F1-Score (Macro), MCC

**基线**: Varela-Vega et al. (2024) 的 BERT 基础模型（六种变体中最佳者）

**评测协议**: 
1. 微调阶段: 5 折交叉验证，选平均 F1 最高的模型
2. 测试阶段: 用最优模型在独立测试集（20% 数据）上评估
3. 网络重建: 对 264 篇 Salmonella 全文推理，与 909 个人工审编交互比较

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 微调性能 | GPT 模型能高精度分类调控效应 | LLaMA-3 8B vs GPT-4o mini vs BERT 基线 | LLaMA-3 8B: F1=0.892, MCC=0.85; GPT-4o mini: F1=0.874, MCC=0.82（表 5） | GPT 模型在测试集上优于 BERT 基线 | 测试集为 E. coli 句子，不代表真实全文场景 | Results 表 5 |
| TRN 重建（单模型） | 模型能从全文提取调控交互 | LLaMA-3 8B vs GPT-4o mini vs BERT | LLaMA-3: F1=0.60, P=0.55, R=0.66; GPT-4o mini: F1=0.60, P=0.55, R=0.66（表 7） | 单模型性能有限，假阳性较多 | 与 BERT 相比无显著优势 | Results 表 7 |
| TRN 重建（集成） | 投票策略提升性能 | 集成 vs 单模型 vs BERT | 集成: F1=0.645, P=0.64, R=0.65（表 7） | 集成显著提升 Precision（0.55→0.64），F1 超过 BERT（0.546） | 提升幅度有限，Recall 略降 | Results 表 7 |
| 大规模网络重建 | 方法可扩展到全文献库 | 2,278 篇文献 vs 264 篇 | 提取 2,243 个交互，1,061 节点 | 方法可处理大规模文献集 | 未与人工审编全库比较 | Results 节 3.5 |
| 网络生物学验证 | 重建网络符合已知生物学知识 | 度分布、社区、过表达分析 | PhoP、RpoS、H-NS 为高连接枢纽；社区富集已知生物过程 | 网络具有生物学一致性 | 未进行实验验证 | Results 节 3.5, Discussion |

## 11 结论正确解读
- **任务范围**: 本文解决的是「从文献句子中分类 TF–靶基因调控效应」这一 NLP 任务，而非从头发现新调控关系。模型依赖词典识别实体，无法发现未知 TF 或靶基因。
- **Oracle/真值输入**: 微调数据来自 RegulonDB 人工审编，评估数据来自 264 篇 Salmonella 文章的人工审编。模型性能上限受限于审编数据的完整性和准确性。
- **端到端状态**: 方法并非全自动端到端——需要预先构建 TF 和靶基因词典，且最终网络需人工审编确认（作者建议用于辅助审编而非替代）。
- **算力成本**: GPT-4o mini 微调通过云端 API 完成（约 1 小时），LLaMA-3 在单张 NVIDIA T4 GPU 上微调约 6.7 小时，推理成本较低。
- **历史数据依赖**: 训练数据来自 E. coli 文献，评估数据来自 Salmonella。跨物种迁移成功，但仅限于细菌；对真核生物（如人类）的适用性未验证。
- **最难场景**: 非典型语言表达（缺乏规范调控动词）、假设性/待验证的调控关系、间接调控（通过其他 TF 中介）等场景下模型性能下降明显。
- **群体/领域边界**: 结论仅适用于细菌转录调控；对翻译后调控、非编码 RNA 调控等未涉及。
- **不确定性**: 模型预测的调控交互未经过湿实验验证；网络中的矛盾效应（同一 TF-靶基因对既有激活又有抑制）未解决，可能反映真实生物学复杂性，也可能是模型错误。

**有边界的复述**: 本文证明，在 E. coli 文献上微调的 GPT 基础模型，通过匿名化句子输入和集成投票策略，能够以 F1=0.645 的性能从 Salmonella 全文文献中重建转录调控网络，显著优于此前 BERT 方法（F1=0.546），且提取的网络与已知生物学知识一致。该方法的适用边界为：细菌、有词典覆盖的实体、文献中明确表述的调控关系。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 低 Precision | 网络重建 Precision 仅 0.64，存在大量假阳性 | 增加负样本训练；引入置信度阈值；人工审编确认 | Discussion: "low Precision score due to the high number of false positive instances" |
| 非典型表达泛化不足 | 缺乏规范调控动词的句子被误分类 | 丰富训练数据，纳入更多非原型例句 | Discussion: "limited generalization to correctly predict the effect of sentences from articles that are not prototypical" |
| 未考虑"去抑制"效应 | 模型将去抑制（derepression）误判为抑制 | 在训练数据中增加"去抑制"类别 | Discussion: "The model predicted the 'repressor' effect for those instances, as the 'derepressor' category was not considered" |
| 假设性调控关系处理不当 | 假设性/待验证的调控被当作已确认关系 | 引入自然语言推理（NLI）方法区分事实与假设 | Discussion: "integration of Natural Language Inference approaches to detect interactions with a high level of certainty" |
| 依赖词典 | 无法识别词典外的实体 | 结合机器学习 NER 工具（如 BERN2）扩展实体覆盖 | Discussion: "applying our BERN2-based algorithm may be a way to increase them" |
| 矛盾效应未解决 | 同一 TF-靶基因对保留多个效应 | 未提出明确方案 | Methods: "all interactions were kept" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 训练与评估数据同源 | 微调数据（E. coli）和评估数据（Salmonella）均来自 RegulonDB 审编流程，可能共享相似的句子风格和标注标准 | 若数据分布过于相似，跨物种泛化结论可能被高估 | 在独立来源的文献集（如 PubMed 随机抽样）上评估 | Methods: 两个数据集均来自 RegulonDB 团队 |
| 匿名化可能丢失信息 | 实体名称本身可能携带语义线索（如已知调控子名称），匿名化虽提升泛化但可能降低特定领域的性能 | 需要在泛化与特异性之间权衡 | 对比匿名化 vs 非匿名化的性能差异 | Methods: "entity mentions were anonymized" |
| 集成策略的增益有限 | 集成 F1=0.645 vs 单模型 F1=0.60，提升 0.045，但 Precision 提升 0.09 的同时 Recall 下降 0.01 | 增益可能来自两模型错误模式的互补，而非本质能力提升 | 分析两模型预测的误差相关性 | Results 表 7 |
| 未报告置信度校准 | 模型输出的概率未用于阈值调整或不确定性估计 | 实际应用中需要知道预测的可靠性 | 绘制 PR 曲线，分析不同阈值下的性能 | 未提供 |
| 网络验证较浅 | 仅通过度分布和过表达分析与已知知识对比，未与现有 Salmonella TRN 数据库（如 SalmoNet2）系统比较 | 需要定量评估重建网络的完整性和准确性 | 与 SalmoNet2 等数据库计算重叠率、Jaccard 相似度 | Discussion: 仅定性讨论 |
| 未讨论计算成本细节 | GPT-4o mini 微调成本未详细说明，LLaMA-3 训练时间仅提及 | 可复现性和实际部署需要考虑成本 | 报告详细的硬件配置和训练时间 | Methods: 仅提及 "1:05:00 h" 和 "06:43:23 h" |
| 矛盾效应处理可能掩盖错误 | 保留所有矛盾效应虽符合生物学复杂性，但也可能掩盖模型的不一致预测 | 需要区分真实的多效调控与模型错误 | 对矛盾效应进行人工审编抽样验证 | Methods: "all interactions were kept" |

## 14 学到什么
**Agent 提炼的知识候选**:

1. **实体匿名化策略**: 将实体名称替换为通用标签（如 @TF$、@Regulated$）是提升跨物种泛化的有效手段。可迁移到 TF–DNA 互作的结构预测任务中，例如在训练多物种模型时，将物种特异的 TF 名称替换为通用类别标签，避免模型过拟合特定物种的序列特征。

2. **生成模型 vs 判别模型的权衡**: GPT 基础模型在少样本微调下即可超越 BERT 判别模型，尤其在需要语义推理的分类任务中。对于 TF–DNA 结合位点预测，可尝试用生成式 LLM 替代传统的 CNN/Transformer 判别模型，利用其上下文理解能力捕捉结合基序的语义特征。

3. **集成投票的 Precision-Recall 权衡**: 多模型投票可显著提升 Precision（0.55→0.64），但 Recall 略降。在 TF–DNA 互作预测中，若下游实验验证成本高，可优先采用高 Precision 的集成策略；若目标是发现新互作，则需平衡 Recall。

4. **错误分析驱动的数据增强**: 作者通过人工分析 250 个假阳性句子，识别出"去抑制"、"假设性调控"等系统性错误模式，为数据增强提供了方向。类似地，在 TF–DNA 结合预测中，可通过分析假阳性预测来识别训练数据的偏差（如缺乏非典型结合位点样本）。

5. **词典 + 模型的分工**: 词典负责实体识别（召回），模型负责关系分类（精度）。这种流水线设计可迁移到 TF–DNA 互作预测中：先用序列比对或结构预测筛选候选互作对，再用 LLM 或分类器验证。

6. **网络级验证方法**: 通过度分布、枢纽节点识别、社区检测和过表达分析验证重建网络的生物学一致性。类似方法可用于验证 AI 预测的 TF–DNA 互作网络，例如检查已知全局调控子（如 CRP、Fis）是否出现在高连接节点中。

## 15 与已有知识连接
- **RegulonDB** (Salgado et al., 2024): 本文微调数据的来源，也是 E. coli TRN 的金标准数据库。与本文方法结合，可加速 RegulonDB 的更新和扩展。
- **Varela-Vega et al. (2024)**: 本文的直接基线，使用 BERT 基础模型做同样的任务。本文的 GPT 方法在 F1 上提升约 0.1。
- **Gill et al. (2024)**: 使用 BioBERT + BERN2 提取基因-蛋白互作，在真实数据上 F1 仅 0.26，本文方法显著优于该结果。
- **BERN2** (Sung et al., 2022): 本文探索了基于 BERN2 的 NER 替代方案，但最终因词典方法更优而放弃。
- **SalmoNet2** (Métris et al., 2017): 已有的 Salmonella TRN 数据库，本文重建的网络可与之比较和互补。
- **PANTHER** (Thomas et al., 2022): 用于过表达分析的工具，验证重建网络的生物学相关性。
- **Cytoscape** (Shannon et al., 2003): 网络可视化和分析工具，用于本文 TRN 的展示和分析。
- **与 TF–DNA 结构预测的关联** [Analysis]: 本文的 NLP 方法提取的是「谁调控谁」的互作关系，而结构预测（如 AlphaFold、MD 模拟）回答的是「如何结合」的机制问题。两者可互补：NLP 提取的互作网络可为结构预测提供候选 TF–DNA 对，结构预测结果可反过来验证 NLP 提取的互作是否在结构上可行。

## 16 研究想法
**Agent 生成的研究候选**:

1. **候选名称**: 跨物种 TF–DNA 互作预测的 LLM 微调框架
   - **来源局限/观察**: 本文证明 GPT 模型在 E. coli 上微调后可迁移到 Salmonella，但仅限细菌。真核生物（如人类）的 TF–DNA 互作更复杂，涉及染色质可及性、共因子等。
   - **核心假设**: 在细菌文献上微调的 LLM 可迁移到真核生物，但需加入真核特异的上下文特征（如组蛋白修饰、增强子-启动子互作）。
   - **初步方法**: 收集人类 TF–DNA 互作文献句子，构建类似本文的微调数据集；在 GPT 模型上微调，并与 ChIP-seq 数据库（如 ENCODE）交叉验证。
   - **验证方式**: 在独立的人类 TF–DNA 互作数据集上评估 F1，与现有数据库比较。
   - **创新状态**: unverified

2. **候选名称**: NLP 提取的 TRN 与结构预测的 TF–DNA 结合位点一致性分析
   - **来源局限/观察**: 本文重建的 TRN 仅基于文献文本，未与结构层面的结合证据（如晶体结构、MD 模拟）交叉验证。
   - **核心假设**: NLP 提取的调控互作中，结构上可结合的 TF–DNA 对占比显著高于随机对。
   - **初步方法**: 从本文重建的 Salmonella TRN 中选取高置信度互作对，用 AlphaFold 或 MD 模拟预测结合亲和力，与随机 TF–DNA 对比较。
   - **验证方式**: 计算结构预测得分与 NLP 置信度的相关性；在已知结构数据库（如 PDB）中验证。
   - **创新状态**: unverified

3. **候选名称**: 基于 LLM 的 TF–DNA 结合基序发现
   - **来源局限/观察**: 本文的模型学习的是句子级别的调控关系，未利用 TF 的 DNA 结合基序信息。
   - **核心假设**: LLM 在预训练中已隐含 DNA 序列-蛋白结合的知识，可通过提示工程或微调直接生成/预测结合基序。
   - **初步方法**: 将 TF 名称和已知基序作为输入，让 LLM 预测未知靶基因的启动子区域是否包含结合位点；与 PWM 扫描方法比较。
   - **验证方式**: 在 ChIP-seq 数据上评估预测的 AUC。
   - **创新状态**: unverified

4. **候选名称**: 结合 NLP 与 MD 模拟的 TF 调控机制注释
   - **来源局限/观察**: 本文仅分类调控效应（激活/抑制），未解释调控的分子机制（如构象变化、竞争结合）。
   - **核心假设**: NLP 提取的调控关系可与 MD 模拟的 TF–DNA 结合构象变化关联，从而自动注释调控机制。
   - **初步方法**: 选取 NLP 高置信度的激活/抑制互作对，进行 MD 模拟比较结合构象差异；用 LLM 生成机制性描述。
   - **验证方式**: 与已知机制的 TF（如 CRP、LacI）比较，评估注释准确性。
   - **创新状态**: unverified

5. **候选名称**: 主动学习框架用于 TRN 审编加速
   - **来源局限/观察**: 本文的模型仍有 36% 假阳性，需要人工审编。审编成本是 TRN 构建的瓶颈。
   - **核心假设**: 模型的不确定性估计可用于优先排序人工审编的句子，从而在有限审编预算下最大化 TRN 覆盖。
   - **初步方法**: 在本文的 ensemble 框架中加入不确定性估计（如预测概率的方差），对低置信度预测优先人工审编；模拟不同审编预算下的 TRN 质量。
   - **验证方式**: 与随机审编策略比较，计算相同预算下的 F1 提升。
   - **创新状态**: unverified