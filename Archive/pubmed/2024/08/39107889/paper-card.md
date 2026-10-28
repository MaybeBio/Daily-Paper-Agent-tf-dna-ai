## 01 基本信息
- **标题**：BertSNR: an interpretable deep learning framework for single-nucleotide resolution identification of transcription factor binding sites based on DNA language model
- **作者**：Luo, Hanyu; Tang, Li; Zeng, Min; Yin, Rui; Ding, Pingjian; Luo, Lingyun; Li, Min
- **单位**：未提供（推测为中南大学，依据 Funding 信息）
- **期刊/平台**：Bioinformatics (Oxford, England)
- **年份**：2024-08-07
- **论文类型**：方法学（Method）研究
- **领域**：计算生物学 / 生物信息学；转录因子结合位点（TFBS）预测
- **关键词**：转录因子结合位点（TFBS）、单核苷酸分辨率、DNA语言模型、可解释深度学习、多任务学习
- **DOI/arXiv 号**：10.1093/bioinformatics/btae461
- **代码**：https://github.com/lhy0322/BertSNR
- **数据**：JASPAR 数据库（188 个 TFBS 数据集 + 33 个 motif 分析数据集），数据 ID 见补充材料
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× 深度学习」方向，具体为基于 DNA 语言模型（BERT 架构）的 TFBS 单核苷酸分辨率预测方法，并强调模型可解释性（注意力权重可视化与 motif 分析）。与物理模拟（MD/对接）无直接关联，但可作为 AI 方法预测 TF–DNA 结合位点的代表性工作，与结构预测方法互补。

## 02 一句话总结
本文提出 BertSNR，一个基于预训练 DNA 语言模型（DNABERT）的多任务深度学习框架，通过同时进行序列级和 token 级分类，在 188 个 ChIP-seq TFBS 数据集上实现单核苷酸分辨率的 TFBS 预测，并利用注意力权重可视化和 motif 分析增强模型可解释性，性能优于现有方法（如 DeepSNR、D-AEDNet）。

## 03 研究问题
- **具体问题**：如何从 DNA 序列中高分辨率（单核苷酸级别）且可解释地识别转录因子结合位点（TFBS）？
- **为什么重要**：TFBS 是基因表达调控的关键元件，精确定位 TFBS 对理解基因调控机制、疾病机制及治疗策略至关重要。传统方法（如 PWM）和现有深度学习方法（如 DeepSNR、D-AEDNet）在分辨率或可解释性上存在不足。
- **现有方法为何不足**：
  - PWM 方法依赖位置权重矩阵，无法捕捉序列上下文和长程依赖。
  - CNN 方法（如 DeepSNR）受限于卷积核大小，难以捕捉全局上下文信息，且缺乏可解释性。
  - 现有深度学习方法多基于 one-hot 编码，无法利用预训练 DNA 语言模型中的丰富序列表示。
- **精确的「Can ... ?」研究问题**：Can a pre-trained DNA language model with multi-task learning achieve single-nucleotide resolution TFBS prediction with better performance and interpretability than existing CNN-based methods?

## 04 背景与发展脉络
- **阶段一：传统方法（PWM/位置权重矩阵）**：如 Match（Kel et al. 2003），基于已知 motif 的 PWM 扫描序列，简单但分辨率低、无法捕捉上下文。
- **阶段二：CNN 深度学习方法**：DeepBind（Alipanahi et al. 2015）首次将 CNN 用于 DNA 序列建模；DeepSNR（Salekin et al. 2018）首次实现单核苷酸分辨率 TFBS 预测，采用卷积-反卷积架构；D-AEDNet（Zhang et al. 2021）引入编码器-解码器架构和注意力机制改进。局限：CNN 受限于卷积核大小，难以捕捉长程上下文；one-hot 编码缺乏语义信息。
- **阶段三：DNA 语言模型**：DNABERT（Ji et al. 2021）等预训练 DNA 语言模型在多种下游任务中表现优异，能捕捉序列上下文和语义信息。
- **本文主张的位置**：将 DNA 语言模型（DNABERT）与多任务学习结合，首次将预训练语言模型应用于单核苷酸分辨率 TFBS 预测，并通过注意力可视化增强可解释性。
- **脉络核验状态**：仅本文框架（基于文中 Introduction 的叙述，未进行外部系统核验）。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 分辨率不足 | 多数现有方法只能预测序列中是否存在 TFBS，无法精确定位到单核苷酸 | 传统方法（PWM）和早期深度学习方法设计目标为序列级分类 | Introduction 第 1 段 |
| 上下文信息捕捉有限 | CNN 方法受限于卷积核大小，无法捕捉长程序列依赖 | 卷积操作仅关注局部特征，缺乏全局上下文建模能力 | Introduction 第 2 段（"CNN-based methods ignore positional information between nucleotides due to the convolutional kernel that only focus on the local features"） |
| 缺乏可解释性 | 深度学习方法多为黑盒，难以理解模型决策依据 | 未设计可解释性机制 | Introduction 第 1 段（"often lack interpretability"） |
| 序列表示信息不足 | one-hot 编码无法捕捉序列的语义和上下文信息 | one-hot 编码为离散稀疏表示，缺乏预训练知识 | Introduction 第 2 段（对比 DNA 语言模型的优势） |

## 06 核心思想
1. **表面方法**：基于预训练 DNA 语言模型（DNABERT）构建多任务学习框架，同时进行序列级分类（判断序列是否含 TFBS）和 token 级分类（判断每个核苷酸是否在 TFBS 内），最终输出单核苷酸分辨率的 TFBS 预测。
2. **核心洞察**：
   - 将 TFBS 预测类比为 NLP 中的命名实体识别（NER）任务，将 DNA 序列视为"语言"，核苷酸视为"token"，TFBS 视为"实体"，从而利用预训练语言模型的上下文表示能力。
   - 多任务学习（序列级 + token 级）可以共享底层特征，通过辅助任务（序列级分类）提升主任务（token 级定位）的性能。
   - 注意力权重可反映模型对关键核苷酸的关注程度，与 motif 位置存在相关性，从而提供可解释性。
3. **可能的普适教训** [Analysis]：
   - 将序列分析任务类比为 NLP 任务（如 NER）并利用预训练语言模型，是提升性能的有效策略。
   - 多任务学习（粗粒度 + 细粒度任务）可以互相促进，尤其当任务间存在层级关系时。
   - 注意力权重可视化可作为深度学习模型可解释性的通用工具，尤其在序列分析任务中。

## 07 方法总览
- **输入**：100 bp DNA 序列（包含 TFBS，位置随机）
- **输出**：每个核苷酸属于 TFBS 的概率（单核苷酸分辨率预测）
- **模块**：
  1. **Tokenization**：k-mer 分词（k=3,4,5,6，最优为 3-mer），将 DNA 序列转换为 token 序列
  2. **Embedding**：token embedding + position embedding（使用 DNABERT 预训练权重）
  3. **Feature Extraction**：12 层双向 Transformer encoder（DNABERT 预训练）
  4. **Prediction**：两个任务分支——序列级分类（[CLS] token 经全连接层+sigmoid）和 token 级分类（每个 token 经全连接层+sigmoid）
- **训练**：每个 TF 单独训练模型；5 折交叉验证；10 epochs + early stopping；损失函数为 λ·loss_sequence + (1-λ)·loss_token（λ 为超参数）
- **工具**：PyTorch 框架；NVIDIA TITAN X GPU
- **反馈回路**：无显式反馈回路（非迭代式预测）
- **假设**：DNA 语言模型（DNABERT）的预训练表示可迁移到 TFBS 预测任务；多任务学习可提升 token 级定位性能

**文字流程**：
1. 输入 100 bp DNA 序列
2. 使用 k-mer（最优 3-mer）分词，生成 token 序列
3. 将 token 序列输入 DNABERT（12 层 Transformer），获得每个 token 的上下文表示
4. 序列级任务：取 [CLS] token 表示，经全连接层+sigmoid，输出序列是否含 TFBS
5. token 级任务：取每个 token 的表示，经全连接层+sigmoid，输出每个 token 是否在 TFBS 内
6. 将 token 级预测映射回核苷酸级别，得到单核苷酸分辨率预测
7. 训练时联合优化两个任务的损失函数

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| k-mer Tokenization | 将 DNA 序列分割为 k-mer token | DNA 语言模型需要 token 化输入；k-mer 可捕捉局部序列模式 | 输入：100 bp DNA 序列；输出：token 序列 | Methods 2.2.1；Results 3.3（3-mer 最优） | 预期影响：移除后无法使用预训练 DNABERT；k 值变化影响性能（3-mer 最优，4-mer 次之） |
| Embedding（token + position） | 将 token 映射为稠密向量并加入位置信息 | Transformer 需要向量输入；位置信息对序列顺序敏感任务至关重要 | 输入：token 序列；输出：embedding 序列 | Methods 2.2.2 | 预期影响：移除后模型无法捕捉 token 语义和位置关系 |
| 12 层 Transformer Encoder（DNABERT 预训练） | 提取序列的上下文表示 | 捕捉长程依赖和全局上下文信息，优于 CNN 的局部特征提取 | 输入：embedding 序列；输出：每个 token 的上下文表示 | Methods 2.2.3；Results 3.1（性能优于 CNN 方法） | 预期影响：替换为 CNN 或浅层网络将降低性能（作者对比 DeepSNR、D-AEDNet 均基于 CNN） |
| 序列级分类分支 | 判断序列是否含 TFBS | 作为辅助任务，提供粗粒度监督信号 | 输入：[CLS] token 表示；输出：二分类概率 | Methods 2.2.3；Results 3.2（多任务学习有效） | 实测消融效应：移除后 5/6 指标下降（Results 3.2，平均提升 0.1-0.8%） |
| token 级分类分支 | 预测每个 token 是否在 TFBS 内 | 主任务，实现单核苷酸分辨率定位 | 输入：每个 token 的表示；输出：二分类概率 | Methods 2.2.3；Results 3.1 | 移除后无法实现单核苷酸分辨率预测 |
| Motif 分析模块 | 从预测结果中提取 motif 并与数据库比对 | 验证模型可解释性和生物学有效性 | 输入：模型预测的 TFBS 区域；输出：motif logo、PWM、与数据库比对结果 | Methods 2.4；Results 3.6 | 预期影响：移除后模型仍可预测，但可解释性验证缺失 |

## 09 关键公式符号
1. **输入 embedding**：
   E_i^input = E_i^token + E_i^position
   - E_i^input：第 i 个 token 的输入 embedding
   - E_i^token：第 i 个 token 的 token embedding
   - E_i^position：第 i 个 token 的 position embedding

2. **多头自注意力**：
   MultiHeadAtt(X) = Concat(head_1, ..., head_n) W^O
   head_i = softmax( (X W_i^Q · (X W_i^K)^T) / √d_k ) · (X W_i^V)
   - X：输入矩阵
   - W_i^Q, W_i^K, W_i^V：第 i 个头的 query、key、value 投影矩阵
   - W^O：输出投影矩阵
   - n：注意力头数
   - d_k：每个头的维度（缩放因子）

3. **多任务损失函数**：
   Loss = λ · loss_sequence + (1-λ) · loss_token
   - λ：超参数，平衡两个任务的权重
   - loss_sequence：序列级二分类的二元交叉熵损失
   - loss_token：token 级二分类的二元交叉熵损失

## 10 实验设计与证据链
- **数据集**：JASPAR 数据库，188 个 TFBS 数据集（人类，ChIP-seq 来源）；33 个额外数据集用于 motif 分析
- **数据规模**：每个数据集包含正样本（含 TFBS 的 100 bp 序列）和负样本（不含 TFBS 的序列）；具体数量未在摘要中提供
- **指标**：accuracy, precision, recall, F1-score, AUC, AUPR（6 个指标）
- **基线/对比方法**：Match（PWM 方法）、DeepSNR、D-AEDNet（深度学习方法）
- **评测协议**：每个 TF 单独训练模型；5 折交叉验证；测试集独立于训练集
- **硬件**：NVIDIA TITAN X GPU

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 主实验：188 数据集 TFBS 预测 | BertSNR 优于现有方法 | 对比 Match、DeepSNR、D-AEDNet；6 个指标 | BertSNR 在 AUPR 上显著优于第二名 D-AEDNet（P=2.15e-15，配对 t 检验）；其余指标也全面领先 | BertSNR 在单核苷酸分辨率 TFBS 预测上优于现有方法 | 未提供具体数值，无法判断提升幅度是否在所有数据集上一致 | Results 3.1，图 3a |
| 消融实验：多任务学习 | 多任务学习提升性能 | BertSNR-multi vs BertSNR-single（移除序列级任务） | 多任务学习在 5/6 指标上提升（accuracy +0.1%, precision +0.8%, F1 +0.2%, AUC +0.1%, AUPR +0.3%） | 多任务学习可有效提升 TFBS 预测性能 | 提升幅度较小，可能因序列级任务与 token 级任务高度相关 | Results 3.2，图 3b，表 S8 |
| k-mer 比较 | 3-mer 最优 | k=3,4,5,6 四种设置 | 3-mer 在 AUPR 上最优（+0.4% vs 4-mer） | 3-mer 提供最佳序列表示 | 未分析 k-mer 与 TF 类型或 motif 长度的交互 | Results 3.3，表 S9 |
| 注意力可视化 | 注意力权重与 motif 相关 | 随机样本（AR、ASCL1）注意力图 vs 数据库 motif | 深层 Transformer 注意力集中在 motif 区域；保守区域注意力更高 | 注意力权重可反映 motif 位置，提供可解释性 | 仅定性分析，无定量指标（如注意力与 motif 位置的相关性系数） | Results 3.5，图 4a-b |
| 全数据集注意力图 | 注意力在群体水平上聚焦 motif | CD2X 数据集 32,021 条序列的平均注意力图 | 注意力集中在序列中心（motif 固定位置） | 注意力模式在群体水平上具有一致性 | 未与其他方法（如 DeepSNR 的 saliency map）对比可解释性 | Results 3.5，图 4c |
| Motif 比对 | BertSNR 生成的 motif 更接近数据库参考 | BertSNR vs D-AEDNet vs DeepSNR；33 个数据集；P-value, e-value, q-value | BertSNR 在三个指标上均优于对比方法 | BertSNR 能更准确地识别 motif 模式 | 未报告具体数值；未与 PWM 方法（Match）对比 motif 质量 | Results 3.6，表 S10-S11 |
| 应用实验：POU5F1 启动子 | BertSNR 能识别启动子区 TFBS | 188 个模型扫描 POU5F1 启动子 2000 bp 区域 | 识别出 58 个 TFBS；其中 YY1、IKZF1、FOSL2、HNF4G、ELF1 有 ChIP-seq 验证；EGR1、GATA1、STAT3、ELF3、SOX2 有文献支持 | BertSNR 可发现已知和潜在的 TFBS，具有生物学实用性 | 未进行实验验证新发现的 TFBS；未与其他方法在启动子区域对比 | Results 3.7，图 S7，表 S12 |

## 11 结论正确解读
- **任务范围**：本文仅针对人类 TFBS 预测，基于 JASPAR 数据库的 ChIP-seq 数据；模型为每个 TF 单独训练，非通用模型。
- **Oracle/真值输入**：训练标签来自 ChIP-seq 实验定义的 TFBS 区域；负样本通过打乱正样本序列生成（保持二核苷酸频率）。
- **端到端状态**：模型端到端训练，但依赖 DNABERT 预训练权重；预测后处理（motif 发现）为独立模块。
- **算力成本**：每个 TF 单独训练，188 个数据集 × 5 折交叉验证；使用单张 NVIDIA TITAN X GPU；具体训练时间未报告。
- **历史数据依赖**：依赖 JASPAR 数据库的 TFBS 注释质量；ChIP-seq 数据本身存在实验偏差（如抗体特异性、峰 calling 阈值）。
- **模型依赖**：依赖 DNABERT 预训练模型（基于人类参考基因组）；k-mer 选择（3-mer）为经验最优。
- **最难情形**：TFBS 保守性低的 TF、motif 长度短的 TF、序列上下文复杂的区域（如启动子/增强子重叠区）。
- **群体/领域边界**：仅人类；未测试其他物种；未测试体内外一致性（ChIP-seq vs 体外结合实验）。
- **不确定性**：注意力权重与 motif 的关系为定性观察，无定量统计检验；新发现的 TFBS 未经过实验验证。
- **有边界的复述**：BertSNR 在 188 个人类 ChIP-seq TFBS 数据集上，以单核苷酸分辨率预测 TFBS，性能优于 Match、DeepSNR 和 D-AEDNet；多任务学习带来小幅提升；注意力权重可视化显示模型关注 motif 区域；在 POU5F1 启动子区域识别出多个已知和潜在的 TFBS。结论限于人类 TFBS 预测任务，未涉及其他物种或体内结合机制。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 模型为每个 TF 单独训练 | 无法利用跨 TF 的共享信息，泛化性受限 | 收集更多 TFBS 数据集，训练一个可预测多种 TFBS 的大型模型 | Discussion 第 1 段 |
| 未整合表观遗传信息 | 模型仅使用 DNA 序列，未考虑染色质可及性、组蛋白修饰等 | 整合表观遗传数据（如 ChIP-seq 信号、ATAC-seq 信号）以增强建模 | Discussion 第 2 段 |
| 注意力权重与 motif 关系为定性分析 | 未定量评估注意力与 motif 位置的相关性 | 进一步量化注意力与 motif 的关系 | Discussion 第 3 段（隐含） |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|----------------------|----------|----------|------|
| 对比方法仅包含 Match、DeepSNR、D-AEDNet | 未与更新的方法（如 Enformer、Basenji、DeepSTARR 等）对比 | 无法判断 BertSNR 是否代表当前最优水平 | 在相同数据集上复现并对比更多 SOTA 方法 | Results 3.1 |
| 消融实验提升幅度极小（0.1-0.8%） | 多任务学习的增益可能不显著，或仅在部分数据集上有效 | 若增益不稳健，模型复杂度增加可能不值得 | 报告每个数据集的消融差异分布，进行显著性检验 | Results 3.2，表 S8 |
| 注意力可视化仅展示 2 个 TF 的少量样本 | 样本量小，可能无法代表整体模式 | 注意力与 motif 的关系需要在大规模数据上验证 | 在全部 188 个数据集上系统计算注意力与 motif 位置的重叠率 | Results 3.5，图 4a-b |
| 未报告具体性能数值 | 仅提供分布图和统计检验 P 值，缺乏具体指标数值 | 无法评估实际性能差距和实际应用价值 | 补充各指标的具体数值和标准差 | Results 3.1 |
| 负样本生成方式（打乱序列）可能过于简单 | 真实基因组中负样本可能包含与正样本相似的序列特征 | 模型可能学习到打乱序列的伪特征而非真实 TFBS 特征 | 使用真实基因组背景序列作为负样本进行验证 | Methods 2.1 |
| 未讨论模型对 motif 方向/间距的敏感性 | TFBS 常以二聚体或协同方式结合，模型可能无法捕捉 | 对理解 TF 协同结合机制重要 | 设计实验检验模型对 motif 排列的响应 | 全文未涉及 |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **任务类比迁移**：将 TFBS 单核苷酸分辨率预测类比为 NLP 的 NER 任务，利用预训练 DNA 语言模型（DNABERT）的上下文表示。→ 可迁移到本课题：对 TF–DNA 结合机制研究，可尝试将其他序列分析任务（如增强子预测、剪接位点识别）类比为 NLP 任务，利用预训练模型。
2. **多任务学习策略**：序列级分类（粗粒度）与 token 级分类（细粒度）联合训练，共享底层特征，小幅提升性能。→ 可迁移到本课题：在预测 TF–DNA 结合时，可同时训练"是否结合"和"结合位置"两个任务，利用任务间层级关系提升性能。
3. **注意力权重作为可解释性工具**：深层 Transformer 的注意力集中在 motif 区域，且保守区域注意力更高。→ 可迁移到本课题：注意力权重可作为 TF–DNA 结合机制研究的线索，帮助识别关键核苷酸和 motif 结构。
4. **k-mer 选择影响表示质量**：3-mer 优于 4/5/6-mer，可能因为 3-mer 覆盖密码子尺度的序列模式。→ 可迁移到本课题：在构建 DNA 序列表示时，应系统比较不同 k-mer 大小，而非默认使用单一设置。
5. **motif 发现作为验证手段**：从预测结果中提取 motif 并与数据库比对，验证模型生物学有效性。→ 可迁移到本课题：任何 AI 预测 TF–DNA 结合的方法，都应通过 motif 分析验证预测结果是否与已知生物学知识一致。
6. **启动子区域扫描应用**：用训练好的模型扫描启动子区域，识别已知和潜在的 TFBS。→ 可迁移到本课题：可用于发现新的 TF–DNA 互作位点，为实验验证提供候选。

## 15 与已有知识连接
- **DNABERT（Ji et al. 2021）**：本文直接基于 DNABERT 预训练模型，属于 DNA 语言模型的下游应用。可连接：DNABERT 的预训练策略（k-mer masking）对 TFBS 预测的影响。
- **DeepSNR（Salekin et al. 2018）**：首个单核苷酸分辨率 TFBS 预测方法，本文的主要对比基线。可连接：CNN 与 Transformer 在序列建模上的能力差异。
- **D-AEDNet（Zhang et al. 2021）**：编码器-解码器架构的 TFBS 预测方法，本文的另一对比基线。可连接：注意力机制在序列定位任务中的应用。
- **JASPAR 数据库（Castro-Mondragon et al. 2022）**：TFBS 数据来源，本课题常用数据库。可连接：数据质量对模型性能的影响。
- **DeepBind（Alipanahi et al. 2015）**：CNN 用于 DNA 序列建模的开创性工作。可连接：深度学习在 TF–DNA 结合预测中的发展脉络。
- **Enformer（Avsec et al. 2021）**：Discussion 中提及的整合表观遗传数据的未来方向。可连接：多模态数据融合在基因调控预测中的潜力。
- **POU5F1/Oct4 调控网络**：本文应用场景之一，连接胚胎干细胞多能性调控研究。可连接：TF–DNA 互作在细胞命运决定中的作用。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：跨 TF 泛化的多任务 TFBS 预测模型
   - **来源局限/观察**：BertSNR 为每个 TF 单独训练，无法利用跨 TF 共享信息；Discussion 中作者也提及此局限。
   - **核心假设**：不同 TF 的 DNA 结合偏好存在共享的序列模式（如结构特征、染色质上下文），多任务学习可捕捉这些共享表示。
   - **初步方法**：在 BertSNR 基础上，将所有 188 个 TF 数据集合并，以 TF 类型作为条件输入（如 TF embedding），训练一个统一模型；采用硬参数共享或软共享（如 MoE）架构。
   - **验证方式**：在未见过的 TF 数据集上测试零样本或少样本泛化能力；对比单任务模型在低资源 TF 上的性能提升。
   - **创新状态**：unverified

2. **候选名称**：注意力引导的 TF–DNA 结合机制解析
   - **来源局限/观察**：BertSNR 发现注意力集中在 motif 区域，但仅定性分析，未量化注意力与结合机制的关系。
   - **核心假设**：注意力权重分布可反映 TF–DNA 结合的物理化学特征（如氢键、疏水作用），且在不同 TF 家族中呈现不同模式。
   - **初步方法**：系统计算 188 个 TF 数据集的注意力图，与已知 motif 结构（如 PDB 结构、HT-SELEX 数据）对比；分析注意力模式与 TF 结构家族（如锌指、bZIP、homeodomain）的关联。
   - **验证方式**：统计检验注意力与 motif 保守性的相关性；聚类分析注意力模式是否对应 TF 结构分类。
   - **创新状态**：unverified

3. **候选名称**：结合结构信息的 TFBS 预测增强
   - **来源局限/观察**：BertSNR 仅使用序列信息，未利用 TF 蛋白结构或 DNA 结构特征；Discussion 中提及整合表观遗传数据但未涉及结构。
   - **核心假设**：将 AlphaFold 预测的 TF 结构或 DNA 形状特征（如 minor groove width、roll）作为辅助输入，可提升 TFBS 预测精度，尤其在序列 motif 不明显的 TF 上。
   - **初步方法**：在 BertSNR 的 token 级分类分支中，加入 DNA 形状特征（如 DNAShape 计算的 4 种特征）作为额外输入；或使用 TF 结构 embedding 作为条件输入。
   - **验证方式**：对比有无结构/形状特征的模型在 188 个数据集上的性能；重点分析在 motif 保守性低的 TF 上的提升。
   - **创新状态**：unverified

4. **候选名称**：TFBS 预测中的不确定性量化
   - **来源局限/观察**：BertSNR 输出确定性预测，未提供预测置信度；对低置信度区域无法区分"无结合"和"不确定"。
   - **核心假设**：通过贝叶斯深度学习或深度集成，可量化 TFBS 预测的不确定性，且不确定性高的区域对应 motif 不明确的结合位点。
   - **初步方法**：在 BertSNR 上应用 MC-Dropout 或深度集成，计算每个核苷酸预测的方差；分析不确定性分布与 motif 保守性、ChIP-seq 信号强度的关系。
   - **验证方式**：在保留测试集上评估不确定性校准（如 reliability diagram）；对比高/低不确定性区域的生物学特征。
   - **创新状态**：unverified

5. **候选名称**：启动子-增强子互作中的 TFBS 协同预测
   - **来源局限/观察**：BertSNR 在 POU5F1 启动子区域识别出多个 TFBS，但未考虑启动子-增强子互作对 TF 结合的协同效应。
   - **核心假设**：启动子-增强子互作区域的 TFBS 存在协同结合模式，联合建模可提升预测精度。
   - **初步方法**：将 BertSNR 扩展到长序列（如 10 kb），结合 Hi-C 或 eQTL 数据标注启动子-增强子互作区域；在互作区域和非互作区域分别评估 TFBS 预测性能。
   - **验证方式**：对比互作/非互作区域的预测性能差异；分析协同结合的 TF 对（如 POU5F1-SOX2）在互作区域的共定位模式。
   - **创新状态**：unverified