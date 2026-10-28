## 01 基本信息
- **标题**：Genome modelling and design across all domains of life with Evo 2
- **作者**：Brixi, Garyk; Durrant, Matthew G; Ku, Jerome; Naghipourfar, Mohsen; Poli, Michael; Sun, Gwanggyu; Brockman, Greg; Chang, Daniel; Fanton, Alison; Gonzalez, Gabriel A; King, Samuel H; Li, David B; Nguyen, Eric; Ricci-Tam, Chiara; Romero, David W; Vorontsov, Anton; Yang, Brandon; Deng, May; Gorton, Liv; Nguyen, Nam; Wang, Nicholas K; Pearce, Michael T; Simon, Elana; Amador, Zachary J; Ashley, Euan A; Baccus, Stephen A; Dai, Haoyu; Dillmann, Steven; Ermon, Stefano; Guo, Daniel; Herschl, Michael H; Ilango, Ken; Janik, Ken; Lu, Amy X; Mehta, Reshma; Mofrad, Mohammad R K; Nguyen, Eric; Pannu, Madelena Y; Re, Christopher; St John, John; Tey, Joseph; Viggiano, Ben; Zhu, Kevin; Zynda, Greg; Balsam, Daniel; Collison, Patrick; Goodarzi, Hani; Hsu, Patrick D; Hie, Brian L
- **单位**：Arc Institute（主要）；Stanford University 等（部分作者）
- **期刊/平台**：Nature
- **年份**：2026
- **论文类型**：研究论文（Research Article）
- **领域**：基因组学 × 深度学习（基础模型）
- **关键词**：基因组基础模型、DNA语言模型、变异效应预测、可解释性、基因组设计
- **DOI/arXiv 号**：10.1038/s41586-026-10176-5
- **代码**：已开源（训练代码、推理代码，见 Data/Code availability）
- **数据**：OpenGenome2 数据集（已公开）
- **阅读日期**：未提供
- **在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**：Evo 2 是一个全基因组尺度的 DNA 基础模型，其核心能力包括：零样本变异效应预测（含非编码区致病突变）、转录因子结合位点（TFBS）的内部表征学习、以及基于预测模型引导的染色质可及性设计。对于 TF–DNA 结合机制研究，Evo 2 提供了：(1) 无需微调即可预测非编码区突变效应的范式；(2) 通过可解释性分析定位 TFBS 表征的方法；(3) 生成式设计 + 预测模型引导（oracle-guided）的闭环框架，可迁移至 TF 结合位点设计。

## 02 一句话总结
Evo 2 是一个在 9.3 万亿碱基对（覆盖细菌、古菌、真核生物和噬菌体）上训练的 40B 参数 DNA 基础模型，通过 1M token 上下文窗口和单核苷酸分辨率，实现了零样本变异效应预测（含非编码致病突变和 BRCA1 变异）以及基因组尺度的生成式设计（含可实验验证的染色质可及性模式），并通过稀疏自编码器揭示了 TFBS、外显子-内含子边界等生物学表征。

## 03 研究问题
- **具体问题**：能否训练一个覆盖所有生命域、具有单核苷酸分辨率和长上下文窗口的基因组基础模型，使其同时具备：(1) 零样本预测遗传变异功能影响的能力；(2) 生成具有生物学真实性的基因组尺度序列的能力？
- **为什么重要**：基因组中绝大多数变异位于非编码区，其功能影响难以通过传统方法预测；同时，基因组尺度的序列设计（如合成基因组）缺乏可靠的生成模型。一个通用的基因组基础模型可同时服务预测与设计。
- **现有方法不足**：Evo 1 仅覆盖原核生物；其他基因组语言模型（如 Nucleotide Transformer）上下文窗口短（~6kb），无法捕获长程调控相互作用；且多数模型在变异效应预测上需要任务特定微调。
- **精确研究问题（Can...?）**：Can a single genomic foundation model trained on all domains of life achieve zero-shot variant effect prediction and genome-scale generative design without task-specific fine-tuning?

## 04 背景与发展脉络
- **阶段一：序列语言模型用于蛋白质**（如 ESM 系列）——证明语言模型可学习蛋白质适应度景观，但仅覆盖蛋白质模态。
- **阶段二：基因组语言模型**（如 Nucleotide Transformer、DNABERT）——扩展到 DNA 序列，但上下文窗口短（~6kb），主要覆盖人类或原核基因组，泛化能力有限。
- **阶段三：Evo 1**——首个大规模原核基因组语言模型（7B 参数，131k 上下文），证明可建模原核基因组并预测变异效应，但无法处理真核基因组的长程调控结构。
- **阶段四（本文）：Evo 2**——扩展到所有生命域（9.3T 碱基），上下文窗口提升至 1M token，单核苷酸分辨率，引入多阶段训练（短序列预训练 + 长上下文中训练），并配套可解释性工具（SAE）和推理时引导生成框架。
- **脉络标注**：以上脉络基于本文引言与讨论的叙述框架，经外部核验（Evo 1 论文、Nucleotide Transformer 论文）确认主要节点。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 基因组语言模型上下文窗口不足 | 无法捕获长程调控相互作用（如增强子-启动子互作、TAD 结构） | 标准 Transformer 注意力复杂度随序列长度二次增长，训练成本过高 | Main 节 "Evo 2 architecture" 段；Fig. 1c |
| 多域基因组数据异质性 | 不同物种的基因组结构、密码子偏好、调控元件差异巨大 | 单一模型难以同时建模细菌（紧凑基因组）和真核（大基因组、内含子丰富） | Main 节 "Evo 2 architecture" 段；Fig. 1b |
| 变异效应预测需任务特定微调 | 已有基因组语言模型在 ClinVar 等基准上需微调才能达到可用性能 | 预训练目标（next-token prediction）与变异效应任务之间的差距 | Main 节 "Human variant effect prediction" 段 |
| 非编码区变异预测困难 | 非编码区缺乏保守性，传统方法（如 PhyloP）依赖多序列比对 | 非编码区功能约束弱，序列保守性不足以反映功能重要性 | Main 节 "Human variant effect prediction" 段；Fig. 3c |
| 基因组尺度生成缺乏引导 | 无约束生成产生非功能性序列 | 生成模型缺乏对下游功能（如染色质可及性）的感知 | Main 节 "Designing mammalian chromatin patterns" 段；Fig. 6a-b |
| 模型可解释性不足 | 难以定位模型内部编码的生物学概念 | 大规模语言模型内部表征复杂，缺乏有效解释工具 | Main 节 "Feature interpretation in Evo 2" 段；Fig. 4a |

## 06 核心思想
1. **表面方法**：训练一个 40B 参数的 StripedHyena 2 架构模型，在 9.3T 碱基对（覆盖所有生命域）上分两阶段训练（8k 上下文预训练 → 1M 上下文中训练），然后通过零样本似然评分进行变异效应预测，通过自回归生成 + 推理时引导（beam search + oracle 评分）进行序列设计。
2. **核心洞察**：DNA 序列本身编码了跨模态的生物学信息（DNA、RNA、蛋白质、调控元件），一个在足够多样数据上训练的模型可以隐式学习这些信息，无需显式任务标注。关键在于：(1) 数据多样性（所有生命域）使模型学习通用序列语法；(2) 长上下文窗口使模型捕获长程调控逻辑；(3) 单核苷酸分辨率使模型能区分细微变异效应。
3. **可能的普适教训 [Analysis]**：Evo 2 的成功表明，对于生物序列建模，「数据规模 + 架构效率 + 多阶段训练」的组合可以替代任务特定的归纳偏置。其「生成 + 引导」框架（用预测模型作为 oracle 引导生成模型）是一种可迁移的通用设计范式，尤其适用于缺乏大量实验数据的生物设计任务。

## 07 方法总览
- **输入**：DNA 序列（单核苷酸 token，4 字符 + 特殊 token）
- **输出**：(1) 序列似然分数（用于变异效应预测）；(2) 生成的 DNA 序列（自回归）
- **模型架构**：StripedHyena 2——多混合架构，包含三种输入依赖卷积算子（short explicit, medium regularized, long implicit）+ 注意力机制，在 1M 上下文下比 Transformer 快 3 倍
- **训练数据**：OpenGenome2——9.3T 碱基对，来自细菌、古菌、真核生物和噬菌体，经过去重和 QC
- **训练阶段**：
  - 阶段 1（预训练）：8,192 token 上下文，9.3T token
  - 阶段 2（中训练）：多阶段扩展上下文至 1M token，额外 5B token
- **变异效应预测**：计算参考序列和变异序列的似然比（log-likelihood ratio）
- **可解释性**：在层 26 训练 Batch-TopK 稀疏自编码器（SAE），提取可解释特征
- **生成引导**：beam search + Enformer/Borzoi 集成评分，每 128bp 重新评分
- **反馈回路**：无显式训练反馈；推理时通过 oracle 评分选择最优生成路径
- **假设**：序列似然与功能重要性相关；预训练捕获的分布隐含了进化约束

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| StripedHyena 2 架构 | 高效处理长序列，混合卷积 + 注意力 | 1M 上下文下 Transformer 计算不可行 | 输入：token 序列；输出：隐藏状态 | Fig. 1f-g；Extended Data Fig. 1c | 预期：无法扩展到 1M 上下文，或训练成本大幅上升 [预期效应] |
| 两阶段训练（预训练 + 中训练） | 先学短程语法，再学长程依赖 | 直接长上下文训练效率低 | 输入：8k 上下文预训练权重；输出：1M 上下文模型 | Fig. 1c-e；Main 节 "Evo 2 architecture" 段 | 预期：长上下文建模能力显著下降 [预期效应] |
| 零样本似然评分 | 变异效应预测 | 无需微调即可预测功能影响 | 输入：参考/变异序列；输出：delta likelihood | Fig. 2b-f；Fig. 3b-e | 实测：移除后无法进行零样本预测 [实测效应，Fig. 3 对比] |
| SAE 可解释性 | 提取可解释的生物学特征 | 理解模型内部表征，验证生物学学习 | 输入：层 26 激活；输出：稀疏特征 | Fig. 4a-g；Extended Data Fig. 6-8 | 预期：无法定位 TFBS、外显子等特征 [预期效应] |
| Beam search + oracle 引导 | 生成满足目标功能的序列 | 无约束生成产生非功能性序列 | 输入：prompt + oracle 评分；输出：优化序列 | Fig. 6a-d；Extended Data Fig. 10 | 实测：移除引导后生成序列功能显著下降 [实测效应，Fig. 6c 对比] |
| 数据过滤（排除真核病毒） | 生物安全 | 防止模型被用于设计致病病毒 | 输入：原始序列库；输出：过滤后数据集 | Main 节 "Evo 2 architecture" 段；Extended Data Fig. 2 | 预期：模型对真核病毒序列建模能力弱 [实测效应，Extended Data Fig. 2a] |

## 09 关键公式符号
- **变异效应评分**：ΔL = log P(seq_mutant) − log P(seq_wildtype)，其中 P(seq) 是 Evo 2 对序列的似然。用途：零样本变异效应预测，ΔL < 0 表示变异降低序列似然，预测为有害。
- **SAE 重构**：x ≈ W_d h + b_d，其中 h = TopK(W_e x + b_e)，x 为层激活，W_e/W_d 为编码/解码权重，TopK 保留 K 个最大激活。用途：将模型激活分解为稀疏可解释特征。
- **Beam search 评分**：score(seq) = Σ_t log P(token_t | seq_<t) + λ · oracle(seq)，其中 oracle 是 Enformer/Borjori 的染色质可及性预测。用途：生成时平衡语言模型先验与功能目标。
- **Perplexity**：PPL = exp(−(1/N)Σ log P(token_i | context))，用于评估语言建模质量（Extended Data Fig. 1c）。
- **AUROC/AUPRC**：用于评估变异效应预测的分类性能（Fig. 3b-e）。

## 10 实验设计与证据链
- **数据集**：
  - 训练：OpenGenome2（9.3T 碱基对，>8.8T 核苷酸，覆盖细菌、古菌、真核、噬菌体）
  - 变异效应预测：ClinVar（人类致病变异）、SpliceVarDB（剪接变异）、BRCA1/BRCA2 饱和突变数据
  - 可解释性：E. coli K12 MG1655、人类基因组、猛犸象基因组
  - 生成：人类线粒体、M. genitalium、S. cerevisiae 染色体 III
- **指标**：AUROC、AUPRC、序列恢复率（amino acid recovery）、结构预测置信度、MitoZ 注释准确率
- **基线**：Evo 1、Nucleotide Transformer、ESM-1b/ESM-2、GPN-MSA、AlphaMissense、CADD、SpliceAI、Pangolin、PhyloP
- **评测协议**：零样本（无微调）变异效应预测；生成序列用 MitoZ/Prodigal 注释、AlphaFold 3 结构预测、BLAST 同源性分析

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 变异效应预测（ClinVar 编码区） | Evo 2 可零样本预测编码变异致病性 | 对比 ESM-1b、ESM-2、AlphaMissense、GPN-MSA | 40B 与 7B 表现竞争性，优于多数零样本方法 | 零样本编码变异预测可行 | 未超越监督方法 AlphaMissense | Fig. 3b |
| 变异效应预测（ClinVar 非编码区） | Evo 2 可零样本预测非编码变异致病性 | 对比 PhyloP、CADD、GPN-MSA | 40B 排名第一（非编码 SNV） | 非编码变异预测是 Evo 2 的优势 | 非编码非 SNV 表现未单独报告 | Fig. 3c |
| 剪接变异预测（SpliceVarDB） | Evo 2 可预测剪接效应 | 对比 SpliceAI、Pangolin | 40B 在剪接变异上表现良好 | 剪接位点信息被隐式学习 | 未超越监督模型 SpliceAI | Fig. 3d |
| BRCA1 变异预测 | Evo 2 可预测 BRCA1 功能丧失 | 对比 GPN-MSA、AlphaMissense | 编码区表现良好，非编码区优于所有基线 | BRCA1 非编码调控变异可预测 | 非编码区 AUROC 仍有限 | Fig. 3e；Extended Data Fig. 5 |
| 外显子-内含子边界识别 | Evo 2 嵌入捕获剪接信号 | 训练线性分类器，对比 Nucleotide Transformer、Evo 1 | AUROC 0.91-0.99，优于基线 | 嵌入包含剪接信息 | 未与监督注释工具全面对比 | Fig. 2g-i |
| 基因必需性预测 | Evo 2 似然可预测基因必需性 | 对比 Evo 1 | 与 Evo 1 相当 | 原核基因必需性信息保留 | 未超越专门模型 | Fig. 2j |
| 线粒体基因组生成 | Evo 2 可生成功能性线粒体基因组 | MitoZ 注释，对比自然序列 | 生成的 CDS/tRNA/rRNA 数量正确 | 可生成细胞器基因组 | 未验证体内功能 | Fig. 5c-e |
| M. genitalium 基因组生成 | Evo 2 可生成原核基因组 | Prodigal 注释，hmmscan 比对 | 70% 基因有 Pfam hit（Evo 1 为 18%） | 生成序列具有蛋白质编码潜力 | 未验证全基因组功能 | Fig. 5g-k |
| 染色质可及性设计 | 引导生成可产生目标染色质模式 | Enformer/Borjori 评分，ATAC-seq 验证 | Morse code 模式 AUROC 0.92-0.95 | 引导生成可设计染色质可及性 | 仅验证了简单模式 | Fig. 6e-h |
| 跨细胞类型设计 | 可设计细胞类型特异性模式 | HEK293T/K562 对比 | 33/36 设计 AUROC > 0.8 | 可设计细胞类型特异性 | 差异可及性设计成功率低 | Fig. 6i-k |

## 11 结论正确解读
- **任务范围**：Evo 2 的验证覆盖了变异效应预测（编码/非编码/剪接）、基因组生成（细胞器/原核/真核染色体片段）和染色质可及性设计。其核心能力是序列似然建模，而非直接的 TF–DNA 结合亲和力预测。
- **oracle/真值输入**：变异效应预测使用 ClinVar、SpliceVarDB、BRCA1/BRCA2 实验数据作为真值；染色质设计使用 Enformer/Borjori 预测作为 oracle，ATAC-seq 作为实验验证。
- **端到端状态**：变异效应预测是端到端的（序列→预测）；染色质设计是「生成 + 评分」两阶段，非端到端。
- **算力成本**：40B 模型训练成本未在摘要中明确报告，但 9.3T token 训练量暗示极高算力需求。
- **历史数据依赖**：训练数据来自公共数据库（如 NCBI），存在对已有基因组注释的依赖。
- **模型依赖**：染色质设计依赖 Enformer/Borjori 的预测质量；变异效应预测依赖序列似然与功能相关的假设。
- **最难情形**：非编码远端调控变异、跨细胞类型差异可及性设计（成功率仅 17%）。
- **群体/领域边界**：训练数据排除真核病毒，导致该领域性能差；对未在训练分布中的物种（如极端嗜热菌）泛化能力未验证。
- **不确定性**：生成序列的体内功能未验证；SAE 特征的功能注释依赖已有数据库。
- **有边界的复述**：Evo 2 是一个在多样基因组数据上训练的 DNA 语言模型，能够零样本预测多种变异的功能影响（尤其非编码区），并能生成具有统计和结构相似性的基因组序列；在染色质可及性设计任务中，通过 oracle 引导可产生实验可验证的模式，但复杂模式设计成功率有限。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 真核病毒序列性能差 | 因生物安全排除训练数据，导致语言建模和下游任务性能差 | 未明确提及（仅说明数据排除是有意为之） | Main 节 "Evo 2 architecture" 段；Extended Data Fig. 2 |
| 基因组规模生成缺乏功能验证 | 生成的基因组序列未在体内验证功能 | 需要大规模、迭代的实验测试 | Discussion 节 "Genome-scale generation" 段 |
| 染色质设计复杂模式成功率低 | 差异可及性设计仅 17% 成功率 | 需要更复杂的引导策略 | Fig. 6i-k；Discussion 节 |
| 生成评估指标有限 | 当前评估基于序列统计和结构预测，不保证功能 | 需要更全面的功能评估 | Discussion 节 "Genome-scale generation" 段 |
| 推理时引导计算成本高 | beam search 需要大量采样 | 未明确提及 | Fig. 6c-d |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 变异效应预测的零样本性能可能部分来自序列保守性而非功能理解 | Evo 2 可能只是学习了「保守序列 = 高似然」的统计规律，而非真正的功能机制 | 若如此，模型对低保守但功能重要的变异（如新发调控突变）预测能力有限 | 对比去除保守性特征后的预测性能；在低保守但已知功能的变异上测试 | Fig. 3 中与 PhyloP 的对比 |
| SAE 特征与生物学注释的匹配可能受注释数据库偏差影响 | 特征匹配可能反映的是训练数据中的注释偏差，而非真正的生物学机制 | 影响可解释性结论的可靠性 | 在独立注释数据集上验证特征-注释关联 | Fig. 4；Extended Data Fig. 7-8 |
| 染色质设计实验仅验证了简单模式 | Morse code 是高度人工化的模式，可能无法推广至自然染色质结构 | 限制了「设计」能力的实际应用价值 | 在更复杂的自然染色质模式上测试 | Fig. 6e-h |
| 训练数据排除真核病毒导致性能差，但未报告排除后对其他任务的影响 | 数据排除可能同时影响了模型对真核基因组的整体理解 | 影响模型作为通用基因组模型的定位 | 对比有无病毒数据训练的模型在真核任务上的性能 | Extended Data Fig. 2 |
| 40B 模型相对 7B 的提升幅度未系统报告 | 模型规模效益不明确，可能 7B 已足够 | 影响算力投入决策 | 系统对比 7B vs 40B 在所有任务上的性能差异 | Fig. 2-6 中部分对比 |
| 生成序列的「功能性」评估依赖计算预测 | MitoZ/Prodigal/AlphaFold 3 均为计算预测，非实验验证 | 生成序列的真实功能未知 | 对生成序列进行实验验证（如合成生物学） | Fig. 5c-k |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **零样本变异效应预测范式**：Evo 2 展示了无需微调即可预测非编码区变异效应的能力。对于 TF–DNA 互作研究，可借鉴此方法预测 TFBS 内的变异对结合亲和力的影响，无需大量 ChIP-seq 或 SELEX 数据。
2. **SAE 可解释性方法**：通过稀疏自编码器定位 TFBS 相关特征，为从基础模型中提取 TF 结合 motif 提供了新工具。可迁移至 TF–DNA 互作研究：训练 TF 特异性的 SAE，识别与结合相关的隐空间维度。
3. **生成 + oracle 引导框架**：beam search + Enformer/Borjori 评分的闭环设计范式，可直接迁移至 TF 结合位点设计——用 TF 结合预测模型作为 oracle，引导 Evo 2 生成高结合亲和力的调控序列。
4. **多阶段训练策略**：短上下文预训练 + 长上下文中训练，可迁移至 TF–DNA 互作模型——先在短序列（如 motif 级）预训练，再扩展至长调控区域。
5. **跨物种泛化**：Evo 2 在多个物种上的泛化能力表明，基因组语言模型可捕获保守的调控逻辑。对 TF–DNA 研究，可构建跨物种的 TF 结合模型，识别保守结合位点。
6. **数据过滤的权衡**：排除特定数据（如病毒）会显著降低该领域性能，提示在构建 TF–DNA 训练数据时需谨慎选择排除策略。

## 15 与已有知识连接
- **Evo 1**（Brixi et al., 2024）：Evo 2 的直接前身，仅覆盖原核生物。Evo 2 扩展至所有生命域并提升上下文窗口至 1M。可对比两者在 TFBS 预测上的性能差异。
- **Nucleotide Transformer**（Dalla-Torre et al., 2023）：基于 Transformer 的 DNA 语言模型，上下文窗口短（~6kb）。Evo 2 在长上下文和跨物种泛化上超越之。
- **Enformer**（Avsec et al., 2021）与 **Borjori**（Calandra et al., 2024）：序列→染色质可及性预测模型，在本文中作为 oracle 引导生成。可迁移至 TF 结合位点预测。
- **AlphaFold 3**（Abramson et al., 2024）：蛋白质结构预测，本文用于验证生成序列编码的蛋白质结构。可扩展至 TF–DNA 复合物结构预测。
- **DeepSEA**（Zhou & Troyanskaya, 2015）与 **Basenji**（Kelley et al., 2018）：早期序列→调控功能预测模型，Evo 2 的零样本能力与之形成对比。
- **gkm-SVM**（Lee, 2016）：基于 k-mer 的 TFBS 预测方法，Evo 2 的 SAE 特征可与之结合提升预测性能。
- **候选方向 [Analysis]**：Evo 2 的 SAE 特征与 TF motif 数据库（如 JASPAR、HOCOMOCO）的系统性对比尚未见报道，是潜在研究方向。

## 16 研究想法
**Agent 生成的研究候选**：

1. **TF–DNA 结合亲和力的零样本预测**
   - 来源局限/观察：Evo 2 在 ClinVar 非编码变异预测中表现优异，但未直接评估 TFBS 内的变异效应。
   - 核心假设：Evo 2 的序列似然变化可预测 TFBS 内变异对结合亲和力的影响。
   - 初步方法：使用 SELEX 或 ChIP-seq 衍生的 TF 结合亲和力数据，计算 Evo 2 对参考/变异序列的 ΔL，与实验测得的亲和力变化对比。
   - 验证方式：与现有方法（如 DeepSEA、gkm-SVM）在多个 TF 上的性能对比。
   - 创新状态：unverified

2. **TFBS 的 SAE 特征发现与跨物种保守性分析**
   - 来源局限/观察：Evo 2 的 SAE 特征与 TFBS 相关，但未系统分析其跨物种保守性。
   - 核心假设：SAE 中与 TFBS 相关的特征在跨物种间保守，可用于注释非模式生物的调控元件。
   - 初步方法：在多个物种的基因组上运行 Evo 2 + SAE，提取 TFBS 相关特征，分析其序列 motif 与已知 TFBS 的相似性，并评估跨物种迁移能力。
   - 验证方式：与 JASPAR/HOCOMOCO motif 数据库比对，并在 ChIP-seq 数据上验证。
   - 创新状态：unverified

3. **TF 结合位点的生成式设计**
   - 来源局限/观察：Evo 2 的染色质设计框架仅针对可及性，未直接设计 TF 结合位点。
   - 核心假设：Evo 2 生成 + TF 结合预测模型引导可设计高亲和力 TFBS。
   - 初步方法：将 Enformer/Borjori 替换为 TF 结合预测模型（如 DeepSEA 或基于 Evo 2 微调的模型），用 beam search 引导 Evo 2 生成 TFBS 序列。
   - 验证方式：合成设计的 TFBS 序列，用实验（如 EMSA、SELEX）验证结合亲和力。
   - 创新状态：unverified

4. **长程调控元件的 TF–DNA 协同建模**
   - 来源局限/观察：Evo 2 的 1M 上下文窗口可覆盖增强子-启动子互作，但未用于 TF 协同结合分析。
   - 核心假设：Evo 2 可捕获多个 TFBS 间的长程协同关系，预测组合调控逻辑。
   - 初步方法：在增强子-启动子对区域计算 Evo 2 的序列似然，分析多个 TFBS 变异对似然的联合影响，与实验数据（如 STARR-seq）对比。
   - 验证方式：在已知协同调控的增强子数据集上验证预测准确性。
   - 创新状态：unverified

5. **跨物种 TFBS 预测的迁移学习**
   - 来源局限/观察：Evo 2 在多个物种上训练，但未评估其在非模式生物 TFBS 预测上的迁移能力。
   - 核心假设：Evo 2 的预训练表征可迁移至低资源物种的 TFBS 预测。
   - 初步方法：在模式生物（如人类、小鼠）上微调 Evo 2 进行 TFBS 预测，评估其在非模式生物（如作物、昆虫）上的零样本/少样本性能。
   - 验证方式：与现有跨物种 TFBS 预测方法对比。
   - 创新状态：unverified