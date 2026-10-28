## 01 基本信息
- **标题**：Deep neural networks identify sequence context features predictive of transcription factor binding
- **作者**：Zheng, An; Lamkin, Michael; Zhao, Hanqing; Wu, Cynthia; Su, Hao; Gymrek, Melissa
- **单位**：未提供（根据通讯作者 Gymrek Melissa 推断为 UC San Diego，但原文未明确列出单位信息）
- **期刊/预印本平台**：Nature Machine Intelligence
- **年份**：2021
- **论文类型**：方法学 + 应用研究
- **领域**：计算生物学 / 机器学习 / 转录因子结合预测
- **关键词**：transcription factor binding, deep learning, CNN, Grad-CAM, sequence context, motif instances
- **DOI/arXiv 号**：10.1038/s42256-020-00282-y
- **代码**：https://github.com/Pandaman-Ryan/AgentBind (doi:10.5281/zenodo.4281456)
- **数据**：https://github.com/Pandaman-Ryan/AgentBind（含变异注释分数）；ENCODE ChIP-seq 峰文件；GEO GSM2545819（STAT3 CD4+ T 细胞）
- **阅读日期**：2026-05-13（按当前日期填写）
- **在该课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」方向，核心贡献在于：(1) 提出一种基于 CNN 的框架（AgentBind），专门预测**给定 motif 实例是否被结合**（而非传统的峰/非峰分类）；(2) 将 Grad-CAM 引入基因组序列解释，实现**单碱基分辨率**的上下文特征重要性评分；(3) 系统比较不同训练集选择（baseline / GC-controlled / DNaseI-controlled）对特征学习的影响。该文为后续基于深度学习的 TF 结合机制解析和变异优先级排序提供了可迁移的框架。

## 02 一句话总结
本文提出 AgentBind 框架，通过预训练 CNN（DeepSEA/DanQ 架构）并在 38 个 TF 的 motif 实例上微调，以二分类方式预测 motif 是否被 ChIP-seq 结合，并利用 Grad-CAM 在单碱基分辨率下识别最关键的序列上下文特征，发现开放染色质（DNaseI 敏感性）是主要预测因子，而 TF 特异性序列特征（如共结合基序）贡献较小且高度依赖训练集选择。

## 03 研究问题
- **具体问题**：给定一个 TF 的 motif 在基因组中的某个实例（occurrence），如何仅从局部 DNA 序列预测它是否会被该 TF 结合？哪些序列上下文特征（motif 之外的碱基）对结合状态贡献最大？
- **为什么重要**：TF 结合是转录调控的核心步骤。基因组中 motif 出现次数远多于实际结合位点（如 SP1 仅有 <1% 的 motif 被结合），理解「什么决定了 motif 实例是否被结合」是解析细胞类型特异性调控和解读非编码变异的关键。
- **现有方法不足**：(1) 传统方法（如 DeepSEA、DanQ）预测的是「区域是否开放/活跃」，而非「特定 motif 实例是否被结合」，因此无法直接回答 motif 层面的问题；(2) 这些方法以开放染色质区域为正样本，未包含不活跃区域作为负样本，导致模型无法学习「区分结合 vs. 不结合」的通用特征；(3) CNN 模型的可解释性差，难以定位具体哪些碱基/特征驱动预测。
- **精确研究问题（Can...?）**：Can a CNN-based framework, fine-tuned on motif-centered sequences, accurately predict whether a given motif instance is bound, and can Grad-CAM attribution identify the specific sequence context features (e.g., co-binding motifs, chromatin-associated motifs) that drive binding predictions?

## 04 背景与发展脉络
*注：以下脉络基于本文引用和讨论，属于「经外部核验」的领域发展概述。*

1. **早期基于 PWM 的方法**：TF 结合位点通常用位置权重矩阵（PWM）建模，但 PWM 仅描述 motif 本身，无法解释为何相同 motif 在不同位置结合状态不同。
2. **基于 k-mer 的方法**：如 KSM（k-mer set method）通过富集分析识别结合位点附近的短序列模式，但无法捕捉长距离依赖和复杂组合。
3. **深度学习进入调控基因组学**：DeepSEA (2015) 和 DanQ (2016) 用 CNN 和 RNN 从序列预测染色质特征（如 DNase、ChIP-seq 峰），取得高精度，但缺乏对「motif 实例级」结合状态的建模。
4. **可解释性方法兴起**：saliency maps、in silico mutagenesis、DeepLIFT 等被用于解释 CNN 预测，但各有局限（如 saliency 噪声大、in silico mutagenesis 计算昂贵）。
5. **本文位置**：在 DeepSEA/DanQ 基础上，提出「motif 条件化」的二分类框架（正负样本均含 motif），并引入 Grad-CAM 实现快速、单碱基分辨率的归因，填补了「从序列预测 motif 实例结合状态 + 解释上下文特征」的空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 正负样本定义不匹配 | 传统模型以开放染色质区域为正样本，未包含不活跃区域为负样本，导致模型学习的是「区域活跃度」而非「motif 结合」 | 作者指出：现有框架「do not consider regions inactive in all cell types as controls」，因此无法学习区分结合 vs. 不结合的通用特征 | Introduction 第 2 段 |
| motif 实例级预测缺失 | 基因组中 motif 出现次数远多于实际结合位点，但现有方法无法回答「这个 motif 是否被结合」 | 作者认为：需要「conditioning on sequences that contain the core TF motif in both the positive and negative samples」 | Introduction 第 3 段 |
| CNN 可解释性不足 | 高精度模型难以定位关键碱基/特征 | 作者指出：现有解释方法（saliency、in silico mutagenesis）各有缺陷，Grad-CAM 结合了定位精度和计算效率 | Results「Identifying the context-specific determinants」节 |
| 训练集选择影响特征学习 | 不同负样本选择导致模型学到不同特征（开放染色质 vs. TF 特异性） | 作者通过 GC-controlled 和 DNaseI-controlled 实验证明：负样本选择显著改变特征重要性排序 | Results 图 2、图 3；Supplementary Tables 6–7 |
| 计算成本高 | in silico mutagenesis 需要逐碱基突变并重新预测，计算量巨大 | 作者指出：in silico mutagenesis「run time is two orders of magnitude higher than the other methods」 | Results「Identifying the context-specific determinants」节、图 2a |

## 06 核心思想
1. **表面方法**：构建一个两阶段框架 AgentBind：(1) 用 DeepSEA 或 DanQ 架构在大型染色质特征数据集上预训练 CNN；(2) 对每个 TF，在 motif 中心化的 1kb 序列上微调二分类模型（结合 vs. 不结合）。随后用 Grad-CAM 对每个输入序列计算单碱基重要性分数，并聚合分析富集的 5-mer 基序。
2. **核心洞察**：**将「预测 motif 实例是否被结合」重构为「在正负样本均含 motif 的条件下的二分类问题」**，迫使模型学习 motif 之外的上下文特征。通过控制负样本（GC 匹配、DNaseI 匹配），可以分离「开放染色质特征」和「TF 特异性序列特征」的贡献。Grad-CAM 的引入使得在单碱基分辨率下定位关键上下文成为可能，且计算效率远高于 in silico mutagenesis。
3. **可能的普适教训 [Analysis]**：在生物序列预测任务中，**训练集的正负样本定义方式直接决定模型学到的生物学特征**。本文通过系统比较三种训练集（baseline / GC-controlled / DNaseI-controlled），展示了「控制混杂因素」如何改变特征归因结果。这一思路可迁移到任何「给定基序/结构域，预测其功能状态」的场景——例如预测突变对 TF 结合的影响时，需匹配 GC 和染色质状态以避免混淆。

## 07 方法总览
- **输入**：1kb DNA 序列（以 motif 为中心），one-hot 编码（4×1000 矩阵）；N 编码为 [0.25, 0.25, 0.25, 0.25]。
- **输出**：二分类概率（该 motif 实例是否被结合）。
- **模型架构**：两种可选——DeepSEA（3 层卷积 + 2 层全连接）和 DanQ（1 层卷积 + 1 层双向 GRU + 2 层全连接）。损失函数为 sigmoid cross entropy。
- **预训练**：在 DeepSEA 数据集（4,863,024 条 1kb 序列，919 个 ChIP-seq/DNase-seq 特征）上预训练，染色体 8 留作交叉验证，染色体 9 留作测试。
- **微调**：对每个 TF，用其 motif 实例（正：ChIP-seq 峰内；负：非峰区域）微调模型。三种负样本设置：
  - baseline：随机非峰 motif 实例
  - GC-controlled：匹配 GC 含量
  - DNaseI-controlled：仅考虑 DNaseI 高敏感区域内的 motif 实例
- **解释**：Grad-CAM（以第一个卷积层为感兴趣层），对每个输入序列计算每个碱基的重要性分数。
- **下游分析**：从正序列中提取 5-mer，按平均 Grad-CAM 分数排序，用 Fisher's exact test 检验富集，并与已知基序（HOCOMOCO）比对。
- **流程**：序列提取 → one-hot → 预训练模型微调 → 二分类预测 → Grad-CAM 归因 → 5-mer 富集分析 → 生物学解释。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 预训练 CNN（DeepSEA/DanQ） | 学习通用调控序列特征 | 小样本 TF 数据不足以从头训练；预训练提供染色质特征先验 | 输入：1kb 序列；输出：919 维染色质特征预测 | Results 图 1b：预训练显著提升性能，尤其对低样本 TF（如 FOS） | 预期影响：低样本 TF 性能大幅下降（作者指出预训练「noticeably improves the performance」） |
| 微调二分类头 | 将通用特征适配到特定 TF 的结合预测 | 将「区域活跃度预测」转化为「motif 实例结合预测」 | 输入：预训练特征 + 新分类层；输出：结合概率 | Results 图 1b：微调后平均 auROC=0.941（DanQ） | 预期影响：模型退化为通用染色质预测器，无法区分同一 motif 的不同实例 |
| 负样本控制（GC / DNaseI） | 消除混杂因素，分离不同特征贡献 | 开放染色质与序列特征混淆，需控制以识别 TF 特异性特征 | 输入：负样本选择策略；输出：不同训练集 | Results 图 3：三种模型富集到不同 5-mer 集合 | 预期影响：无法区分「开放染色质特征」与「TF 特异性特征」；DNaseI-controlled 模型对共结合基序更敏感 |
| Grad-CAM 归因 | 单碱基分辨率的重要性评分 | 定位关键上下文碱基，识别共结合基序 | 输入：训练好的 CNN + 单条序列；输出：每个碱基的重要性分数 | Results 图 2a：Grad-CAM 在模拟数据上优于 saliency 和 DeepLIFT（综合指标） | 预期影响：无法定位关键碱基；in silico mutagenesis 可替代但计算成本高 100 倍 |
| 5-mer 富集分析 | 将碱基级分数转化为可解释的序列模式 | 单碱基分数噪声大，需要聚合到 motif 水平 | 输入：Grad-CAM 分数 + 5-mer 集合；输出：富集 5-mer 列表及 OR 值 | Results 图 3：富集到已知共结合基序（如 NFY、AP-1、RUNX） | 预期影响：无法识别共结合关系；结果停留在碱基级，难以生物学解释 |

## 09 关键公式符号
本文为深度学习应用型论文，未引入新的数学公式。核心计算组件如下：

1. **CNN 卷积操作**（DeepSEA/DanQ 标准组件）：
   \[
   h_i = \text{ReLU}(W \cdot x_{i:i+k} + b)
   \]
   其中 \(x_{i:i+k}\) 为位置 \(i\) 处长度为 \(k\) 的 one-hot 编码子序列，\(W\) 为卷积核权重，\(b\) 为偏置。

2. **损失函数**（sigmoid cross entropy，二分类）：
   \[
   L = -\frac{1}{N}\sum_{i=1}^{N} [y_i \log(\hat{y}_i) + (1-y_i)\log(1-\hat{y}_i)]
   \]
   其中 \(y_i \in \{0,1\}\) 为标签，\(\hat{y}_i = \sigma(z_i)\) 为 sigmoid 输出。

3. **Grad-CAM 权重**（本文核心解释工具）：
   \[
   \alpha_k = \frac{1}{Z}\sum_i \sum_j \frac{\partial y^c}{\partial A^k_{ij}}
   \]
   其中 \(y^c\) 为类别 \(c\) 的 logit，\(A^k\) 为第 \(k\) 个特征图，\(Z\) 为归一化常数。最终重要性图：
   \[
   L^c = \text{ReLU}\left(\sum_k \alpha_k A^k\right)
   \]
   本文将其应用于第一个卷积层，得到碱基级重要性分数。

4. **Fisher's exact test**（5-mer 富集分析）：
   用于检验某个 5-mer 在 top 1% 高分 5-mer 中的富集是否显著，输出 odds ratio (OR) 和 P 值。

## 10 实验设计与证据链
**数据集与资源**：
- 38 个 TF，GM12878 细胞系，ChIP-seq 数据来自 ENCODE
- Motif 来自 JASPAR
- 预训练数据：DeepSEA 数据集（4,863,024 条 1kb 序列，919 个特征）
- 每个 TF 平均 18,892 条序列（正+负）
- 测试：染色体 9 留出；交叉验证：染色体 8
- 对比方法：KSM（k-mer set method）、IMPACT（基于实验表观特征的模型）
- 硬件：NVIDIA Tesla K40c GPU

**实验表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 预训练 vs. 从头训练 | 预训练提升微调性能 | DeepSEA/DanQ 架构，有/无预训练 | 预训练显著提升 auROC，尤其对低样本 TF（如 FOS） | 预训练提供通用调控特征先验 | 未比较不同预训练数据规模的影响 | Results 图 1b |
| 三种训练集对比 | 负样本选择影响特征学习 | baseline / GC-controlled / DNaseI-controlled | 平均 auROC：baseline=0.941，GC-controlled=0.928，DNaseI-controlled=0.795 | 开放染色质是主要预测因子；控制 DNaseI 后性能下降 | 未量化各特征贡献比例 | Results 图 1b、Supplementary Tables 6–7 |
| 解释方法基准测试 | Grad-CAM 优于其他解释方法 | 模拟数据（嵌入已知 motif），对比 saliency、DeepLIFT、in silico mutagenesis | Grad-CAM 在准确率、召回率、运行时间综合最优 | Grad-CAM 适合碱基级归因 | 模拟数据可能不完全反映真实基因组复杂性 | Results 图 2a、Supplementary Table 11 |
| 5-mer 富集分析 | 识别共结合基序 | 38 个 TF 的 top 1% 5-mer vs. 背景 | 富集到已知共结合基序（NFY、AP-1、RUNX、IRF 等） | 上下文特征包含共结合 TF 的 motif | 未验证这些共结合关系是否在实验中直接互作 | Results 图 3 |
| 近端 vs. 远端结合位点 | 启动子与增强子区域特征不同 | 按距 TSS 3kb 划分近端/远端 | 部分 TF（如 SP1）近端/远端 top 5-mer 差异显著 | 结合机制在启动子/增强子间存在差异 | 未深入分析机制差异 | Results 图 4、Extended Data 图 4 |
| 跨细胞类型 STAT3 | 模型捕获细胞类型特异性特征 | GM12878、Th17、HeLa 三细胞类型交叉预测 | 各细胞类型由自身模型预测最佳；富集基序高度细胞类型特异 | 上下文特征具有细胞类型特异性 | 仅测试 1 个 TF | Results 图 4 |
| 变异优先级排序 | Grad-CAM 分数富集于功能变异 | 与 gnomAD 等位基因频率、MPRA 数据比较 | top 0.5% 分数 SNP 显著富集 singleton（P=3.3×10⁻⁸）；MPRA 阳性 SNP 分数更高（P=0.013） | Grad-CAM 分数可辅助变异优先级排序 | 预测能力中等，不能单独作为因果变异判据 | Results「Allele frequency analysis」节、Extended Data 图 5 |

## 11 结论正确解读
- **任务范围**：本文仅预测「给定 motif 实例是否被 ChIP-seq 结合」，不预测结合强度、不涉及三维基因组结构、不包含非序列因素（如 TF 浓度、竞争性结合）。
- **Oracle/真值输入**：标签来自 ChIP-seq 峰（存在/不存在），这是实验观测而非真实结合亲和力；负样本为「非峰区域中的 motif 实例」，但「非峰」不等于「不结合」（可能因 ChIP 灵敏度限制）。
- **端到端状态**：框架是端到端的（序列 → 结合预测），但解释部分（Grad-CAM → 5-mer 富集）是后处理分析，非端到端学习。
- **算力成本**：预训练在 DeepSEA 数据集上完成，微调每个 TF 独立进行；Grad-CAM 计算效率高（比 in silico mutagenesis 快两个数量级），但未报告具体训练时间。
- **历史数据依赖**：依赖 ENCODE ChIP-seq 和 JASPAR motif 数据库，这些数据本身存在细胞类型覆盖不均和 motif 表示不完整的问题。
- **模型依赖**：结果基于 DeepSEA/DanQ 两种架构，其他架构（如 Transformer）可能表现不同。
- **最难情形**：低样本 TF（如 FOS）、DNaseI 控制后性能显著下降（auROC 从 0.928 降至 0.795），说明在染色质状态相似时，仅靠序列区分结合与否仍具挑战。
- **群体/领域边界**：仅在 GM12878 淋巴母细胞系验证；跨细胞类型仅测试 STAT1 个 TF。
- **不确定性**：Grad-CAM 分数是模型归因，不等于因果效应；5-mer 富集基于统计关联，未做实验验证。
- **有边界的复述**：在 GM12878 中，对于 38 个 TF，基于 1kb 局部序列的 CNN 模型能以平均 auROC≈0.94 预测 motif 实例是否被结合；Grad-CAM 归因显示开放染色质特征（DNaseI 敏感性）贡献最大，而 TF 特异性序列特征（共结合基序）贡献较小且高度依赖训练集选择；该框架可用于非编码变异优先级排序，但预测能力中等。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 训练集选择影响特征归因 | 不同负样本设置（baseline / GC-controlled / DNaseI-controlled）导致 top 5-mer 显著不同 | 作者建议根据应用场景选择合适的训练集；未提出统一解决方案 | Results 图 3、Discussion |
| 依赖 PWM 识别 motif | PWM 无法捕获 motif 内部位置间依赖，可能错误分类部分实例 | 作者承认「PWM suffer from known limitations, including an inability to capture dependencies between positions」 | Discussion 第 2 段 |
| 解释方法仍有改进空间 | Grad-CAM 等现有方法无法提取复杂规则（如 motif 间距、方向、组合） | 作者建议使用 DeepResolve 等可视化技术揭示特征交互 | Discussion 第 2 段 |
| TF 结合 ≠ 调控功能 | 高 Grad-CAM 分数的位点不一定影响基因表达 | 作者指出「TF binding does not necessarily imply regulatory function」 | Discussion 第 2 段 |
| 仅测试单一细胞类型 | 主要分析集中在 GM12878 | 作者建议未来在更多细胞类型中验证 | Discussion 第 2 段 |
| 变异优先级排序能力有限 | Grad-CAM 分数对 MPRA 阳性变异的区分能力中等 | 作者建议将分数整合到其他框架中提升因果变异识别 | Discussion 第 2 段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| 负样本定义依赖「非峰」区域 | ChIP-seq 峰检测存在假阴性，部分「非峰」motif 可能实际被结合 | 若负样本含假阴性，模型学到的「不结合」特征可能不准确 | 使用独立方法（如 STARR-seq、MPRA）验证负样本的真实结合状态 | Methods「ChIP-sequencing datasets and preprocessing」节 |
| Grad-CAM 归因未与因果验证结合 | 高分数碱基可能只是与结合相关的代理特征（如 GC 含量），而非直接参与结合 | 归因分数用于变异优先级排序时，可能产生假阳性 | 对 top 分数碱基进行饱和突变实验，验证突变对结合的影响 | Results「Allele frequency analysis」节 |
| 5-mer 富集分析仅基于统计关联 | 富集的 5-mer 可能反映序列组成偏差而非功能共结合 | 可能高估共结合关系的普遍性 | 用 ChIP-seq 共占据数据或 Hi-C 数据验证预测的共结合关系 | Results 图 3 |
| 跨细胞类型分析仅测试 STAT3 | 单一 TF 的结果不能推广到所有 TF | 细胞类型特异性可能因 TF 类型而异 | 在更多 TF 上重复跨细胞类型分析 | Results 图 4 |
| 预训练数据与微调数据分布差异 | DeepSEA 预训练数据包含多种细胞类型和标记，可能与 GM12878 TF 结合任务不完全匹配 | 预训练可能引入与目标任务无关的特征 | 比较不同预训练数据（如仅用 GM12878 数据预训练）的效果 | Methods「CNN model architecture and training」节 |
| 未报告模型不确定性 | 二分类输出为点估计，无置信区间 | 在低置信度区域做变异优先级排序时可能误导 | 使用 MC-dropout 或 ensemble 方法估计预测不确定性 | 未提供 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **训练集设计决定特征归因**：本文最核心的可迁移思想是「通过控制负样本选择，分离不同生物学因素的贡献」。在 TF–DNA 互作研究中，若想识别「直接参与结合的序列特征」，应使用 DNaseI-controlled 负样本（即开放染色质中的非结合 motif）；若想预测「整体结合可能性」，则使用 baseline 负样本。这一设计可迁移到其他「基序→功能」预测任务。

2. **Grad-CAM 用于基因组序列归因**：将 Grad-CAM 应用于第一个卷积层，可在单碱基分辨率下定位关键序列特征，且计算效率远高于 in silico mutagenesis。该方法可迁移到任何 CNN 类 DNA 序列模型，用于识别功能 SNP、共结合基序等。

3. **预训练 + 微调范式**：在大型染色质特征数据集上预训练 CNN，再在特定 TF 的小样本数据上微调，显著提升低样本 TF 的性能。这一范式可迁移到其他 TF 或 DNA 结合蛋白（如 RNA 结合蛋白）的结合预测。

4. **5-mer 富集分析作为解释工具**：将碱基级归因分数聚合到 5-mer 水平，用 Fisher's exact test 识别富集基序，可将黑盒模型转化为可检验的生物学假设。该方法可迁移到任何序列归因结果的后续分析。

5. **变异优先级排序的实用路径**：Grad-CAM 分数与负选择信号（singleton 富集）和功能实验（MPRA）的关联验证，提供了一条从模型归因到功能验证的完整路径，可迁移到非编码变异解读。

## 15 与已有知识连接
- **DeepSEA (Zhou & Troyanskaya, 2015)**：本文直接使用 DeepSEA 架构和预训练数据，属于对其框架的扩展——从「区域级预测」到「motif 实例级预测」。
- **DanQ (Quang & Xie, 2016)**：本文同样评估了 DanQ 架构，并发现其性能略优于 DeepSEA，与原文结论一致。
- **Grad-CAM (Selvaraju et al., 2017)**：本文首次将 Grad-CAM 系统应用于基因组序列归因，属于计算机视觉解释方法向基因组学的迁移。
- **KSM (Gymrek et al., 2016)**：本文与 KSM 直接对比，证明深度学习方法在 motif 实例预测上优于基于 k-mer 的方法。
- **IMPACT (Amariuta et al., 2019)**：本文与 IMPACT 对比，证明纯序列方法可达到与基于实验表观特征方法相当的性能。
- **ENCODE 和 JASPAR**：本文依赖这两个数据库的 ChIP-seq 和 motif 数据，属于标准资源。
- **与 AlphaFold 等结构预测方法的关系 [Analysis]**：本文仅从序列层面预测结合，未涉及三维结构。但 Grad-CAM 识别的关键上下文碱基可作为结构建模（如分子对接、MD 模拟）的候选位点，为「序列→结构→功能」的整合研究提供输入。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合机制的多任务归因框架
   - **来源局限/观察**：本文仅预测二分类结合状态，未区分结合强度（ChIP-seq 峰高）或结合动力学（on/off rate）。
   - **核心假设**：结合强度与序列上下文的关系可能不同于结合状态，多任务学习可提升归因精度。
   - **初步方法**：在 AgentBind 基础上增加回归头预测 ChIP-seq 信号强度，用 Grad-CAM 分别计算分类和回归任务的归因图，比较差异。
   - **验证方式**：在 ENCODE 数据上评估多任务 vs. 单任务的 auROC/auPRC 和归因一致性。
   - **创新状态**：unverified

2. **候选名称**：结合 MD 模拟的 TF–DNA 上下文碱基功能验证
   - **来源局限/观察**：Grad-CAM 识别的高分碱基缺乏结构层面的验证，无法区分「直接接触」与「间接影响」。
   - **核心假设**：Grad-CAM 高分碱基中，与 TF 有直接范德华/氢键接触的碱基对结合贡献更大。
   - **初步方法**：选取 2–3 个 TF（如 CTCF、YY1），对 top 5-mer 进行分子对接或短时 MD 模拟，计算结合自由能变化，与 Grad-CAM 分数关联。
   - **验证方式**：比较直接接触碱基 vs. 非接触碱基的 Grad-CAM 分数分布；突变模拟验证。
   - **创新状态**：unverified

3. **候选名称**：细胞类型特异性 TF 结合上下文的跨细胞学习
   - **来源局限/观察**：本文仅详细分析 GM12878，跨细胞类型仅测试 STAT3。
   - **核心假设**：不同细胞类型中，同一 TF 的结合上下文特征存在共享和特异部分，多细胞联合建模可提升泛化。
   - **初步方法**：收集 5+ 细胞类型的 ChIP-seq 数据，用多任务或元学习框架联合训练，比较单细胞 vs. 多细胞模型的归因差异。
   - **验证方式**：留一细胞类型交叉验证；比较共享 vs. 特异 5-mer 的生物学注释。
   - **创新状态**：unverified

4. **候选名称**：基于归因分数的非编码变异功能预测器
   - **来源局限/观察**：本文仅初步验证了 Grad-CAM 分数与 singleton 富集和 MPRA 的关联，未构建完整预测器。
   - **核心假设**：Grad-CAM 分数可与其他功能注释（如保守性、染色质状态）整合，提升非编码变异的功能预测精度。
   - **初步方法**：将 Grad-CAM 分数作为新特征，与 CADD、FunSeq2 等现有工具整合，训练集成模型。
   - **验证方式**：在 ClinVar 和 GWAS 变异上评估 AUC 提升。
   - **创新状态**：unverified

5. **候选名称**：TF 结合上下文中的基序间距与方向性建模
   - **来源局限/观察**：本文的 5-mer 分析未考虑基序间的间距和相对方向。
   - **核心假设**：共结合基序的间距和方向对结合预测有显著贡献，且可通过 CNN 的卷积核自动学习。
   - **初步方法**：在 AgentBind 基础上，对 top 5-mer 对进行间距和方向统计分析，与随机背景比较；可视化 CNN 卷积核的基序组合模式。
   - **验证方式**：在已知共结合对（如 AP-1–IRF）上验证间距/方向偏好。
   - **创新状态**：unverified