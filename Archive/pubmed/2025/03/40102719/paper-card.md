## 01 基本信息
- **标题**：CacPred: a cascaded convolutional neural network for TF-DNA binding prediction
- **作者**：Zhang, Shuangquan; Ma, Anjun; Xie, Xuping; Lian, Zhichao; Wang, Yan
- **单位**：未提供（作者单位未在摘要/正文中明确列出）
- **期刊/平台**：BMC Genomics（Volume 26 Supplement 2, 2025: 17th International Symposium on Bioinformatics Research and Applications）
- **年份**：2025-03-19
- **论文类型**：方法学/算法研究（提出新深度学习模型）
- **领域**：生物信息学；转录因子-DNA结合预测；深度学习
- **关键词**：TF-DNA binding prediction, cascaded convolutional neural network, motif finding, ChIP-seq, ChIP-nexus
- **DOI/arXiv 号**：10.1186/s12864-025-11399-y
- **代码**：https://github.com/zhangsq06/CacPred
- **数据**：790 个 ChIP-seq 数据集（覆盖 261 个 TF，含 690 个 ENCODE 数据集和 100 个 Cistrome 数据集）、7 个 ChIP-nexus 数据集
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「TF–DNA 结合预测 × 深度学习（CNN）」方向，提出一种仅使用卷积（无池化）的级联 CNN 架构，在 790 个 ChIP-seq 和 7 个 ChIP-nexus 数据集上系统对比 6 个现有深度模型，并利用第一层卷积核进行 motif 发现与解释。其核心主张是池化操作会丢失序列信息，级联卷积可提升预测性能。

## 02 一句话总结
本文提出一个仅由卷积层（无池化）组成的级联 CNN 模型 CacPred，以正反向序列（forward 与 reverse complement）为双输入，在 790 个 ChIP-seq 数据集上平均 ACC、MCC、AEMR 分别提升 3.3%、9.2%、6.4%，在 7 个 ChIP-nexus 数据集上分别提升 5.5%、16.8%、12.9%，并通过第一层卷积核提取的 motif 与 HOCOMOCO v11 数据库比对验证了模型的可解释性。

## 03 研究问题
- **具体问题**：如何设计一个更准确的深度学习模型来预测 TF–DNA 结合，同时保持模型的可解释性（motif 发现）？
- **为什么重要**：TF 通过结合 DNA 上的 TFBS 调控基因表达，准确预测 TF–DNA 结合是理解转录调控机制的基础；现有深度学习方法虽优于传统方法，但精度仍有提升空间，且卷积在 TF–DNA 结合预测中的潜力尚未被充分挖掘。
- **现有方法不足**：已有 DL 模型（如 DeepBind、DeeperBind、Basset、DeepHistone、DESSO、TBiNet）均使用卷积+池化结构，作者认为池化可能丢失序列信息；且现有模型精度需要进一步提高。
- **精确研究问题**：Can a cascaded convolutional neural network without pooling outperform existing deep learning models in TF–DNA binding prediction across ChIP-seq and ChIP-nexus datasets?

## 04 背景与发展脉络
（注：以下脉络主要基于本文框架，部分经外部知识核验）

1. **传统方法阶段**：MEME-ChIP（EM + DREME）和 gkm-SVM 利用期望最大化、gap-kmer 和 SVM 进行 motif 发现与结合预测。局限：难以处理大规模基因组数据，无法揭示复杂调控机制。
2. **深度学习早期阶段**：DeepBind（2015）首次将 CNN 用于 TF–DNA 结合预测，将卷积核视为 motif 检测器。后续出现 DeeperBind（CNN+RNN）、Basset、DeepHistone、DESSO（引入 DNA 形状特征）、TBiNet 等改进模型。这些模型均采用卷积+池化结构。
3. **本文位置**：作者基于前期对 20 个 DL 模型在 871 个 ChIP-seq 数据集上的系统评估，发现卷积在 TF–DNA 结合预测中起关键作用，但池化的必要性未被充分检验。CacPred 提出纯卷积（无池化）的级联架构，并采用正反向双序列输入，在更大规模数据上验证了性能提升。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有 DL 模型精度不足 | 在 790 个 ChIP-seq 数据集上，6 个对比模型的平均 ACC、MCC、AEMR 均低于 CacPred | 池化操作可能丢失序列中的关键位置信息 | Results 图 2、图 3；Discussion 节 |
| 池化导致信息丢失 | 现有模型均使用卷积+池化，CacPred 仅用卷积即取得更好性能 | 作者推断池化在降维过程中丢失了部分序列信息 | Discussion 节："we reason that the pooling process may lose some sequence information" |
| 单序列输入信息不足 | 仅使用正向序列的模型性能低于双输入模型 | 正反向互补序列提供更完整的序列信息 | Methods 节（双输入设计）；Discussion 节 |
| 模型可解释性不足 | 黑箱模型难以揭示 TF 结合的序列特征 | 通过第一层卷积核提取 motif 并与数据库比对 | Results "Explaining CacPred model" 节、图 5 |
| 固定长度 motif 检测局限 | CacPred 只能识别固定长度的 TFBS | 卷积核宽度固定 | Discussion 节（作者自述局限） |

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有 DL 模型精度不足 | 在 790 个 ChIP-seq 数据集上，6 个对比模型的平均 ACC、MCC、AEMR 均低于 CacPred | 池化操作可能丢失序列中的关键位置信息 | Results 图 2、图 3；Discussion 节 |
| 池化导致信息丢失 | 现有模型均使用卷积+池化，CacPred 仅用卷积即取得更好性能 | 作者推断池化在降维过程中丢失了部分序列信息 | Discussion 节："we reason that the pooling process may lose some sequence information" |
| 单序列输入信息不足 | 仅使用正向序列的模型性能低于双输入模型 | 正反向互补序列提供更完整的序列信息 | Methods 节（双输入设计）；Discussion 节 |
| 模型可解释性不足 | 黑箱模型难以揭示 TF 结合的序列特征 | 通过第一层卷积核提取 motif 并与数据库比对 | Results "Explaining CacPred model" 节、图 5 |
| 固定长度 motif 检测局限 | CacPred 只能识别固定长度的 TFBS | 卷积核宽度固定 | Discussion 节（作者自述局限） |

## 06 核心思想
1. **表面方法**：构建一个 6 层的级联 CNN，包含卷积层、转置卷积层、合并层、两个级联卷积层和全连接层，以正向序列和反向互补序列为双输入，输出二分类预测（结合/不结合）。
2. **核心洞察**：池化操作在现有 DL 模型中可能是不必要的，甚至是有害的——它丢失了 TF–DNA 结合中关键的序列位置信息。通过移除池化并采用级联卷积结构，模型可以保留更完整的序列信息，从而提升预测精度。同时，正反向双序列输入提供了互补的序列特征。
3. **可能的普适教训** [Analysis]：在序列类生物信息学任务中，"信息保留"比"特征压缩"更重要。池化作为图像领域的主流操作，迁移到序列任务时需重新审视其必要性。级联（cascading）结构允许模型在不同尺度上逐步抽象特征，而不必依赖池化来扩大感受野。

## 07 方法总览
- **输入**：正向序列和反向互补序列，各编码为 4×1001 的 one-hot 矩阵（A=[1,0,0,0], G=[0,1,0,0], C=[0,0,1,0], T=[0,0,0,1]）
- **输出**：二分类概率（TF 是否结合该 DNA 序列）
- **模块**：
  1. 第一层：两个独立的卷积层（各 32 个 4×16 卷积核，无参数共享），分别处理正向和反向互补序列
  2. 第二层：两个转置卷积层（各 32 个 1×16 卷积核，stride=1）
  3. 第三层：合并层（concatenate 两个分支的输出）
  4. 第四层：卷积层（8 个 1×15 卷积核）
  5. 第五层：卷积层（16 个 1×15 卷积核）
  6. 第六层：全连接层（1001 个神经元）+ sigmoid 输出
- **训练**：损失函数为 Binary Cross Entropy (BCELoss)，优化器为 Adadelta，dropout 用于防止过拟合，epochs=20，基于验证集 AUC 选择最优超参数（dropout ratio、batch size、learning rate 通过 3 折交叉验证优化）
- **工具**：PyTorch
- **反馈回路**：验证集 AUC 驱动超参数选择；测试集上 9 个指标评估最终性能
- **文字流程**：正向序列和反向互补序列分别经 one-hot 编码 → 各自通过独立的卷积层提取局部 motif 特征 → 经转置卷积层上采样/重构 → 两分支输出合并 → 经两级级联卷积进一步抽象特征 → 全连接层 + sigmoid 输出结合概率

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 双分支卷积层（第一层） | 分别从正向和反向互补序列提取局部序列特征 | 正反向序列提供互补信息，独立卷积核可分别捕捉不同方向的 motif | 输入：4×1001 one-hot 矩阵；输出：32 通道特征图 | Methods 节公式 (3)(4)；Discussion 节提及双输入提供更多信息 | [预期] 移除反向互补分支会损失序列互补信息，降低预测性能 |
| 转置卷积层（第二层） | 上采样/重构特征图 | 可能用于恢复卷积降维后的空间分辨率，保留位置信息 | 输入：第一层输出；输出：上采样特征图 | Methods 节公式 (5)(6) | [预期] 移除后特征图分辨率降低，可能损失位置信息 |
| 合并层（第三层） | 拼接两分支特征 | 融合正反向序列信息 | 输入：两个 32 通道特征图；输出：64 通道合并特征 | Methods 节公式 (7) | [预期] 移除后无法融合双序列信息 |
| 级联卷积层（第四、五层） | 逐步抽象高阶序列特征 | 级联结构允许模型学习更复杂的序列模式，无需池化即可扩大感受野 | 输入：合并特征；输出：8 通道、16 通道特征图 | Methods 节公式 (8)(9)；图 6 | [预期] 移除后模型容量降低，无法捕捉复杂 motif 组合模式 |
| 全连接层 + sigmoid（第六层） | 输出二分类概率 | 将特征映射到结合/不结合决策 | 输入：展平特征；输出：标量概率 | Methods 节公式 (10) | [预期] 移除后无法输出预测结果 |

## 09 关键公式符号

1. **第一层输出**：
   - C₁₁ = ReLU(conv₁₁(M₁))
   - C₁₂ = ReLU(conv₁₂(M₂))
   - 其中 M₁、M₂ 分别为正向和反向互补序列的 one-hot 编码矩阵（4×1001），conv₁₁(·)、conv₁₂(·) 为第一层的两个独立卷积操作

2. **第二层输出**：
   - C₂₁ = trans_conv₂₁(C₁₁)
   - C₂₂ = trans_conv₂₂(C₁₂)
   - 其中 trans_conv₂₁(·)、trans_conv₂₂(·) 为转置卷积操作

3. **第三层合并**：
   - C₃ = concatenate([C₂₁, C₂₂])

4. **第四、五层级联卷积**：
   - C₄ = concatenate([C₃, ReLU(conv(C₃))])
   - C₅ = concatenate([C₄, ReLU(conv(C₄))])

5. **输出层**：
   - ŷ = sigmoid(ω·C₅ + b)
   - sigmoid(x) = 1/(1+e⁻ˣ)
   - 其中 ω 为权重矩阵，b 为偏置

6. **损失函数**：
   - BCELoss = -[y·log(ŷ) + (1-y)·log(1-ŷ)]
   - 其中 y 为真实标签

7. **AEMR 计算**（用于综合排名）：
   - Oᵢ,ᵢ₊₁ = ½·Rᵢ·Rᵢ₊₁·sin(π/4)，i = 1,...,8
   - R = [precision, recall, F1_score, ACC, specificity, MCC, AUC, PRC, precision]
   - AEMR = sum(Oᵢ,ᵢ₊₁, ...)

## 10 实验设计与证据链
- **数据集**：790 个 ChIP-seq 数据集（690 个 ENCODE + 100 个 Cistrome，覆盖 261 个 TF）；7 个 ChIP-seq 数据集（覆盖 7 个 TF）
- **数据规模**：每个数据集包含正样本（peak 序列，标签 1）和负样本（与正样本 GC 含量匹配、不与 peak 重叠的序列，标签 0），正负比 1:1
- **序列长度**：固定 1001 bp
- **数据划分**：80% 训练 / 20% 测试
- **指标**：precision, recall, F1_score, ACC, specificity, MCC, AUC, PRC, AEMR（9 个指标）
- **基线/对比模型**：6 个现有 DL 模型（DeepBind、DeeperBind、Basset、DeepHistone、DESSO、TBiNet）
- **评测协议**：所有模型在相同数据划分下训练和测试，计算 9 个指标的平均值，以 AEMR 作为综合排名指标
- **交叉验证**：超参数通过训练集上 3 折交叉验证优化
- **可解释性验证**：第一层卷积核提取的 motif 通过 TOMTOM v5.1.0 与 HOCOMOCO v11 数据库比对，P < 0.05 视为显著

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 790 个 ChIP-seq 数据集上的性能对比 | CacPred 优于现有 DL 模型 | 与 6 个模型对比，9 个指标 | CacPred 在全部 9 个指标上取得最高平均分；ACC、MCC、AEMR 分别提升 3.3%、9.2%、6.4% | CacPred 在 ChIP-seq 数据上优于现有模型 | 未报告逐数据集显著性检验；未报告方差分析 | Results 图 2、图 3 |
| 7 个 ChIP-nexus 数据集上的泛化验证 | CacPred 可泛化到 ChIP-nexus 数据 | 与 6 个模型对比 | CacPred 在 ACC、MCC、AEMR 上分别提升 5.5%、16.8%、12.9% | CacPred 在 ChIP-nexus 数据上同样最优 | 数据集数量少（7 个），统计功效有限 | Results Table 1 |
| 跨细胞类型预测 | CacPred 在跨细胞类型场景下有效 | ETS1 的 ChIP-seq 数据：训练于 K562，测试于 GM12878 和 K549 | CacPred 在 AEMR 上优于对比模型 | CacPred 具备跨细胞类型泛化能力 | 仅测试 1 个 TF（ETS1），结论外推有限 | Results 节；Table S2 |
| Motif 发现与可解释性 | CacPred 第一层卷积核能发现显著 motif | 以 wgEncodeEH001833 数据集为例，TOMVT 比对 HOCOMOCO v11 | 发现 5 个显著 motif（P < 0.05） | CacPred 可自动学习有意义的序列特征 | 仅展示 1 个数据集的 motif 结果 | Results "Explaining CacPred model" 节、图 5 |

## 11 结论正确解读
- **任务范围**：二分类任务——预测给定 1001 bp DNA 序列是否被特定 TF 结合。不涉及结合强度预测、不涉及染色质可及性等表观遗传因素。
- **数据范围**：人类基因组序列；790 个 ChIP-seq 数据集覆盖 261 个 TF，7 个 ChIP-nexus 数据集覆盖 7 个 TF。负样本为 GC 匹配的非 peak 序列。
- **oracle/真值输入**：ChIP-seq/ChIP-nexus 实验定义的 peak 区域作为正样本标签。标签质量依赖实验条件、peak calling 方法。
- **端到端状态**：模型端到端训练，输入为 one-hot 编码序列，输出为结合概率。但 motif 发现是事后分析（post-hoc），非端到端可解释。
- **算力成本**：未报告训练时间、GPU 型号、参数量等计算资源信息。
- **历史数据依赖**：模型依赖 ChIP-seq 实验数据质量；不同实验室、不同抗体的 ChIP-seq 数据可能存在系统性偏差。
- **模型依赖**：仅使用 CNN 架构，未与 Transformer、GNN 等最新架构对比；对比模型为 6 个，非全部现有方法。
- **最难情形**：未报告模型在低置信度 peak、重复序列区域、非标准 motif 等困难场景下的表现。
- **群体/领域边界**：仅在人类数据上验证；未测试其他物种。仅测试 TF–DNA 结合，不涉及其他 DNA 结合蛋白。
- **不确定性**：未报告置信区间、方差分析或统计显著性检验；性能提升的稳健性未充分讨论。
- **有边界的复述**：CacPred 在 790 个 ChIP-seq 和 7 个 ChIP-nexus 数据集上，以 9 个指标评估，平均性能优于 6 个对比 DL 模型，且能通过第一层卷积核发现与数据库匹配的显著 motif。该结论限于人类 TF–DNA 结合二分类预测任务，且未与其他所有现有方法进行全面对比。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 固定长度 motif 识别 | CacPred 只能识别固定长度的 TFBS | 开发不同宽度的卷积核以识别不同长度的 TFBS | Discussion 节 |
| 间接结合未处理 | 模型未考虑 TF 间接结合其他 TF motif 的情况 | 结合 ATAC-seq 数据揭示 TF 协同作用 | Discussion 节 |
| 单数据集分类 | 模型针对每个数据集单独训练二分类模型 | 改进模型以支持多数据集多分类任务 | Discussion 节 |
| 未融合图方法 | 未利用 GNN 等图神经网络捕捉 TF 协同性 | 探索 GNN 在 motif 发现和 TF 协同性研究中的应用 | Discussion 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| 性能提升幅度未报告具体数值 | 摘要仅给出相对提升百分比（3.3%、9.2%、6.4%），未报告绝对数值和方差 | 无法判断提升是否在实际应用中有意义 | 查阅原文表格获取具体数值和标准差 | Results 图 3 |
| 对比模型选择有限 | 仅对比 6 个模型，未包含近年 SOTA（如 Transformer-based 方法） | 无法确认 CacPred 是否真正达到 SOTA | 与更多最新模型对比 | Results 节 |
| 无消融实验 | 未报告移除各模块（如转置卷积、级联结构、双输入）后的性能变化 | 无法确认各设计选择的必要性 | 设计消融实验逐一验证 | 全文未提及消融 |
| 跨细胞类型验证仅 1 个 TF | ETS1 单一 TF 的跨细胞类型测试不足以支持泛化结论 | TF 结合机制因 TF 而异，单一 TF 结论外推有限 | 在多个 TF 上重复跨细胞类型实验 | Results 节；Table S2 |
| "池化丢失信息"解释缺乏直接证据 | 作者将性能提升归因于去除池化，但未通过实验直接验证（如对比有/无池化版本） | 因果归因不充分 | 设计 CacPred 的池化版本进行对比 | Discussion 节 |
| Motif 发现仅展示 1 个数据集 | 仅以 wgEncodeEH001833 为例展示 motif 结果 | 无法评估 motif 发现的整体成功率 | 在所有数据集上系统评估 motif 发现率 | Results "Explaining CacPred model" 节 |
| 未报告超参数敏感性 | 未讨论 dropout ratio、batch size、learning rate 对结果的影响 | 模型稳健性未知 | 进行超参数敏感性分析 | Methods 节 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **池化非必需**：在序列二分类任务中，移除池化层并采用级联卷积可以保留更完整的位置信息，这一设计思路可直接迁移到 TF–DNA 结合预测的其他模型架构中。对于本课题，若使用 CNN 类模型，可考虑去除池化层并加深卷积层数。

2. **双序列输入策略**：同时输入正向和反向互补序列，通过独立卷积核分别提取特征后合并，可提供互补信息。这一策略可迁移到其他 DNA 序列分析任务（如 motif 发现、增强子预测），也可与注意力机制结合。

3. **AEMR 综合评估指标**：将 8 个指标（precision, recall, F1, ACC, specificity, MCC, AUC, PRC）通过雷达图面积（AEMR）综合排名，避免单一指标偏差。本课题在评估 TF–DNA 结合模型时可采用类似综合评分策略。

4. **第一层卷积核作为 motif 检测器**：将训练好的第一层卷积核提取激活序列并构建 PWM，再与数据库比对验证可解释性。这是 CNN 可解释性的低成本方案，可迁移到本课题的 motif 发现任务。

5. **大规模基准测试框架**：在 790 个 ChIP-seq 数据集上系统对比多个模型，覆盖 261 个 TF，这种大规模基准测试策略值得借鉴，可为本课题提供更可靠的模型评估。

6. **GC 匹配负样本选择**：负样本选择采用与正样本 GC 含量匹配且不与 peak 重叠的序列，这一负样本构建策略可减少 GC 偏差对模型评估的影响，值得在本课题中采用。

## 15 与已有知识连接
- **DeepBind (Alipanahi et al., 2015)**：首个将 CNN 用于 TF–DNA 结合预测的模型，CacPred 的第一层卷积核作为 motif 检测器的设计直接继承自 DeepBind 的思想。CacPred 的贡献在于去除池化并引入级联结构。
- **DeeperBind**：在 DeepBind 基础上引入 RNN 捕捉序列依赖，CacPred 未使用 RNN，但通过级联卷积达到类似的特征抽象效果。
- **DESSO**：引入 DNA 形状特征（HelT, MGW, ProT, Roll），CacPred 未使用形状特征，但两者均强调可解释性（motif 发现）。
- **MEME-ChIP 与 gkm-SVM**：传统方法代表，CacPred 在性能上超越这些方法，验证了深度学习在 TF–DNA 结合预测中的优势。
- **ENCODE 与 Cistrome 数据库**：CacPred 使用的数据来源，是本课题可复用的公共数据资源。
- **HOCOMOCO v11 与 TOMTOM**：motif 数据库与比对工具，可用于本课题的 motif 验证。
- **[Analysis] 与 AlphaFold 等结构预测方法的关联**：CacPred 仅基于序列预测结合，未涉及 3D 结构。本课题若结合结构信息（如 AlphaFold 预测的 TF 结构或 DNA 形状），可能进一步提升预测性能，这是 CacPred 未覆盖的潜在改进方向。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：CacPred-Transformer 混合架构
   - **来源局限/观察**：CacPred 仅使用 CNN，未与 Transformer 等注意力机制结合；Transformer 在捕捉长程依赖方面优于 CNN
   - **核心假设**：在 CacPred 的级联卷积基础上引入注意力机制，可同时保留局部 motif 特征和长程序列依赖，进一步提升 TF–DNA 结合预测精度
   - **初步方法**：将 CacPred 的级联卷积输出作为 Transformer encoder 的输入，或在第一层卷积后加入自注意力层
   - **验证方式**：在 790 个 ChIP-seq 数据集上对比 CacPred-Transformer 与 CacPred、DeepBind、DESSO 等模型
   - **创新状态**：unverified

2. **候选名称**：多尺度卷积核 CacPred（Multi-scale CacPred）
   - **来源局限/观察**：CacPred 的卷积核宽度固定（4×16），只能识别固定长度 motif；作者自认此局限
   - **核心假设**：使用不同宽度的卷积核并行提取不同长度的 motif 特征，可识别可变长度的 TFBS，提升预测性能
   - **初步方法**：在第一层使用多个不同宽度的卷积核（如 8、12、16、20），将输出合并后进入后续级联层
   - **验证方式**：对比多尺度 CacPred 与原始 CacPred 在 motif 发现数量和预测精度上的差异
   - **创新状态**：unverified

3. **候选名称**：CacPred-DNA形状融合模型
   - **来源局限/观察**：CacPred 仅使用序列信息，未利用 DNA 形状特征（如 DESSO 中的 HelT, MGW, ProT, Roll）；DNA 形状已被证明影响 TF 结合特异性
   - **核心假设**：将 DNA 形状特征与序列特征融合输入 CacPred，可提供互补信息，提升预测精度
   - **初步方法**：使用 DNAshape 工具预测 DNA 形状特征，与 one-hot 序列编码拼接后输入 CacPred
   - **验证方式**：对比 CacPred-DNA形状 与 CacPred、DESSO 在相同数据集上的性能
   - **创新状态**：unverified

4. **候选名称**：CacPred-ATAC 协同预测模型
   - **来源局限/观察**：CacPred 仅使用 ChIP-seq 数据，未利用 ATAC-seq 数据；作者在 Discussion 中提及 ATAC-seq 可揭示 TF 协同作用
   - **核心假设**：融合 ATAC-seq 染色质可及性信息可提升 TF–DNA 结合预测，特别是在间接结合场景下
   - **初步方法**：将 ATAC-seq 信号作为额外输入通道，与序列编码共同输入 CacPred
   - **验证方式**：在同时具有 ChIP-seq 和 ATAC-seq 的数据集上对比融合模型与仅序列模型
   - **创新状态**：unverified

5. **候选名称**：CacPred-GNN 协同 motif 发现
   - **来源局限/观察**：CacPred 仅识别单个 TF 的 motif，未建模 TF 间协同作用；作者在 Discussion 中提出 GNN 在揭示 TF 协同性方面的潜力
   - **核心假设**：将 TF–TF 相互作用图与序列特征结合，通过 GNN 捕捉 TF 协同结合模式，可提升预测性能并发现协同 motif
   - **初步方法**：构建 TF 共结合网络，将 CacPred 的序列特征作为节点特征输入 GNN
   - **验证方式**：在多个 TF 共结合的 ChIP-seq 数据集上评估协同预测性能
   - **创新状态**：unverified