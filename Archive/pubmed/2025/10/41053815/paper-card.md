## 01 基本信息
- **标题**: Cisformer: a scalable cross-modality generation framework for decoding transcriptional regulation at single-cell resolution
- **作者与单位**: Ji, Luzhang; Zou, Qihang; Tang, Ke; Wang, Chenfei（单位未提供）
- **期刊/预印本平台**: Genome Biology
- **年份**: 2025-10-07
- **论文类型**: 方法学（Method）+ 应用研究
- **领域**: 单细胞多组学、转录调控、深度学习
- **关键词**: 单细胞、跨模态生成、染色质可及性、基因表达、转录调控、注意力机制
- **DOI/arXiv 号**: 10.1186/s13059-025-03823-z
- **代码**: 未提供
- **数据**: 10X Genomics PBMC multiome、SHARE-seq K562、BCL multiome、Tabula Muris Senis 小鼠肾脏 scRNA-seq、UK Biobank GWAS fine-mapping 数据
- **阅读日期**: 2026-05-13
- **在该课题方向中的位置**: 本文属于「AI/深度学习 × 转录调控」方向，聚焦于单细胞水平上基因表达（RNA）与染色质可及性（ATAC）之间的跨模态生成与调控关系推断。与 TF–DNA 结合机制的直接关联在于：通过注意力机制推断 CRE–基因调控关系，并进一步通过 motif 富集识别候选 TF。其核心创新在于用 cross-attention 替代 VAE/AE 架构，提升可解释性，为从表观基因组推断 TF 结合位点提供了新思路。

## 02 一句话总结
Cisformer 采用 decoder-only + cross-attention 的 Transformer 架构，在单细胞水平上实现 RNA↔ATAC 双向跨模态生成，通过注意力分数推断 CRE–基因调控关系，并在癌症与衰老场景中识别候选功能 CRE 和 TF。

## 03 研究问题
- **具体问题**: 如何从单细胞 RNA-seq 数据准确生成对应的染色质可及性（ATAC）谱，并同时从模型中提取可解释的 CRE–基因调控关系？
- **为什么重要**: 单细胞多组学实验成本高、噪声大，难以大规模实施；若能仅凭 RNA 数据可靠推断染色质状态，将极大扩展表观基因组分析的适用范围。同时，理解 CRE–基因调控关系是解析 TF 功能与基因调控网络的核心。
- **现有方法不足**: 现有方法（BABEL、scButterfly）基于 AE/VAE 架构，生成精度有限，尤其在跨组织预测任务上泛化能力不足；且 VAE 的隐空间难以解释，无法直接提取 CRE–基因调控关系。ArchR 和 SCARlink 虽可推断 CRE–基因关联，但分别受限于相关性方法（易受混杂因素影响）和线性模型（无法捕捉非线性关系）。
- **精确研究问题 (Can...?)**: Can a cross-attention-based generative model achieve accurate single-cell RNA↔ATAC translation while simultaneously providing interpretable CRE–gene regulatory links that are validated by independent ChIP-seq and GWAS data?

## 04 背景与发展脉络
*注：以下脉络基于本文框架整理，未经外部系统核验，标注为「仅本文框架」。*

- **阶段一：单细胞多组学实验方法**（SNARE-seq、SHARE-seq、CITE-seq 等）：可同时测量同一细胞的多种模态，但成本高、操作复杂、数据稀疏。
- **阶段二：计算跨模态预测**（BABEL、scButterfly）：利用 AE/VAE 在共享隐空间中对齐不同模态，实现 RNA→ATAC 或 ATAC→RNA 预测。局限：隐空间不可解释，跨组织泛化差，生成精度有限。
- **阶段三：CRE–基因关联推断**（ArchR、SCARlink）：从多组学数据中识别 CRE–基因调控关系。ArchR 基于相关性，SCARlink 基于正则化泊松回归。局限：线性假设，难以捕捉复杂非线性调控。
- **本文主张的位置**: Cisformer 将生成任务与调控关系推断统一在同一个 cross-attention 框架中，既提升生成精度（尤其跨组织场景），又通过注意力分数直接提供可解释的 CRE–基因调控关系，填补了「高精度生成」与「可解释调控推断」之间的空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单细胞多组学实验成本高、难以规模化 | 多组学实验需要精细样本处理，难以大规模应用 | 多组学方法需同时捕获多种分子，实验复杂度高 | Background 第 1 段 |
| 现有跨模态生成模型精度不足 | BABEL、scButterfly 在跨组织预测任务上表现不佳 | AE/VAE 架构的隐空间压缩导致信息丢失，模型容量受限 | Results 图 2a |
| 现有模型泛化能力差 | 跨组织（PBMC→脑）预测时聚类指标显著下降 | 训练数据与测试数据分布差异大，模型过拟合于训练组织 | Results 图 2a、2b |
| 模型不可解释，无法提取调控关系 | VAE 隐空间缺乏生物学语义 | 隐空间是压缩的连续向量，不保留输入特征间的显式关系 | Discussion 第 1 段 |
| 现有 CRE–基因关联方法受限于线性/相关性假设 | ArchR 相关性方法易受混杂因素影响，SCARlink 无法捕捉非线性 | 调控关系本质上是非线性的，线性模型表达力有限 | Background 第 3 段 |
| 单细胞数据稀疏性导致训练偏差 | 模型倾向于预测全零或低值输出 | 大多数染色质位点处于关闭状态，类别不平衡 | Methods: Feature duplication and selection |

## 06 核心思想
1. **表面方法**: 构建一个 decoder-only 的 Transformer 模型，输入为基因表达向量（RNA）或染色质可及性向量（ATAC），通过 cross-attention 机制在两种模态间进行信息交互，最终输出目标模态的预测值。RNA→ATAC 方向用 BCE 损失预测二值可及性；ATAC→RNA 方向用 CCE 损失预测 8-bin 离散化表达值。

2. **核心洞察**: 
   - 将「跨模态生成」与「调控关系推断」统一在同一个注意力机制中——注意力分数天然编码了「哪些 CRE 对哪些基因有调控作用」这一信息，无需额外解释模块。
   - 特征选择策略（只保留非零表达的基因和活跃 CRE）不仅降低计算量，还聚焦于生物学上更相关的信号，减少稀疏性带来的训练偏差。
   - 索引编码（peak index encoding）将大规模 CRE 词汇表分解为逐位数字嵌入，避免存储巨大的嵌入矩阵，使模型可扩展到百万级 CRE。

3. **[Analysis] 可能的普适教训**: 
   - 在生物序列/特征建模中，将「预测任务」与「关系推断任务」共享同一表征空间，可以同时提升任务性能和可解释性。
   - 对高维稀疏生物数据，显式的特征选择（而非全量输入）往往比模型架构本身更重要。
   - 索引/位置编码的分解策略（如逐位数字嵌入）是处理超大规模词汇表的有效手段，可迁移到其他大规模基因组特征建模场景。

## 07 方法总览
- **输入**: 
  - RNA→ATAC: 单细胞基因表达向量（非零表达基因，最多 2048 个），每个基因由基因索引嵌入 + 表达值嵌入拼接表示
  - ATAC→RNA: 单细胞染色质可及性向量（活跃 CRE，最多 10000 个），每个 CRE 由 peak 索引嵌入表示
  
- **输出**: 
  - RNA→ATAC: 所有 CRE 的二值可及性预测（sigmoid 概率）
  - ATAC→RNA: 非零表达基因的 8-bin 离散化表达预测

- **模块**: 
  1. 输入编码：基因/peak 索引嵌入 + 表达值嵌入（RNA）或索引嵌入（ATAC）
  2. Cross-attention Transformer 层：query 来自目标模态，key/value 来自源模态
  3. 输出 MLP：将 Transformer 输出映射为预测值
  4. 损失函数：BCE（RNA→ATAC）或 CCE（ATAC→RNA）

- **训练**: Adam 优化器，StepLR 学习率衰减，梯度裁剪（max norm=1），混合精度训练（FP16），分布式训练（≥2 张 A800 GPU），early stopping

- **反馈回路**: 无显式反馈回路；训练为单轮监督学习

- **文字流程**: 
  1. 数据预处理：将 RNA 和 ATAC 数据映射到固定词汇表（人类 38,244 基因 / 1,033,239 CRE）
  2. 特征选择：RNA 保留非零表达基因，ATAC 保留活跃 CRE，构建基因-CRE 对
  3. 输入编码：基因/peak 索引通过嵌入层编码，表达值通过值嵌入编码
  4. Cross-attention 编码：目标模态序列作为 query，源模态序列作为 key/value，经过多层 Transformer 块
  5. 输出预测：MLP 将编码结果映射为预测值（BCE 或 CCE）
  6. 注意力分数提取：从训练好的模型中提取 gene-CRE 注意力分数作为调控强度
  7. 下游分析：基于注意力分数进行 CRE 排序、motif 富集、GWAS 富集等

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 特征选择（非零基因/活跃 CRE） | 过滤稀疏特征，聚焦生物学相关信号 | 单细胞数据极度稀疏，全量输入导致计算浪费和训练偏差 | 输入：全量基因/CRE 向量；输出：筛选后的子集 | Methods: Feature duplication and selection | [预期] 模型可能因稀疏性而偏向预测全零，训练不稳定 |
| 特征复制（feature duplication） | 将非零基因复制多份以平衡类别 | 非零基因远少于零基因，直接采样导致类别不平衡 | 输入：非零基因集合；输出：复制后的基因集合 | Methods: Feature duplication and selection | [预期] 模型可能忽略稀有但重要的基因信号 |
| Peak 索引编码 | 将 CRE 索引分解为逐位数字嵌入 | 1,033,239 个 CRE 的直接嵌入矩阵过大（约 1M × d） | 输入：CRE 索引（整数）；输出：d 维嵌入向量 | Methods: Peak index encoding | [预期] 无法处理大规模 CRE 词汇表，内存溢出 |
| Cross-attention Transformer 层 | 在基因和 CRE 之间建立交互关系 | 核心机制：让模型学习哪些 CRE 调控哪些基因 | 输入：query（目标模态嵌入）、key/value（源模态嵌入）；输出：编码后的目标模态表示 | Results 图 3a–i | [实测] 注意力分数无法提取，模型退化为纯黑箱预测器 |
| 输出 MLP + 损失函数 | 将编码映射为预测值并计算损失 | 将 Transformer 表示转换为具体的生物学预测 | 输入：Transformer 输出；输出：BCE 概率或 CCE 分布 | Methods: Loss functions | [预期] 无法端到端训练 |
| FlashAttention2 | 高效注意力计算 | 长序列（2048/10000 token）注意力计算开销大 | 输入：Q、K、V 矩阵；输出：注意力输出 | Methods: Memory-efficient attention | [预期] 训练速度下降，显存不足 |

## 09 关键公式符号
1. **Cross-attention 计算**:
   Attention(Q, K, V) = softmax(QK^T / √d) V
   - Q: query 矩阵（来自目标模态，如 RNA→ATAC 时的 CRE 嵌入）
   - K: key 矩阵（来自源模态，如 RNA 基因嵌入）
   - V: value 矩阵（同 K）
   - d: 嵌入维度
   - 用途: 计算目标模态中每个 token 对源模态中所有 token 的注意力权重
   - 直觉: 注意力权重即「调控强度」——CRE 对基因的注意力越高，表示该 CRE 越可能调控该基因
   - 来源: Methods, Cross-attention mechanism

2. **Multi-head attention**:
   MultiHead(Q, K, V) = Concat(head₁, ..., head_h) W^O
   - headᵢ = Attention(QWᵢ^Q, KWᵢ^K, VWᵢ^V)
   - Wᵢ^Q, Wᵢ^K, Wᵢ^V: 第 i 个头的投影矩阵
   - W^O: 输出投影矩阵
   - 用途: 从不同表征子空间捕捉调控关系
   - 来源: Methods, Cross-attention mechanism

3. **FFN（逐位置前馈网络）**:
   FFN(x) = max(0, xW₁ + b₁)W₂ + b₂
   - W₁, W₂: 权重矩阵；b₁, b₂: 偏置
   - 用途: 对每个 token 独立进行非线性变换
   - 来源: Methods, Position-wise feedforward network

4. **BCE 损失（RNA→ATAC）**:
   L_BCE = -(1/N) Σᵢ [yᵢ log(ŷᵢ) + (1-yᵢ) log(1-ŷᵢ)]
   - yᵢ: 真实二值可及性标签；ŷᵢ: 预测概率；N: peak 数量
   - 用途: 优化二值染色质可及性预测
   - 来源: Methods, Loss functions

5. **CCE 损失（ATAC→RNA）**:
   L_CCE = -(1/M) Σᵢ Σₖ₌₁⁸ yᵢₖ log(ŷᵢₖ)
   - yᵢₖ: one-hot 编码的表达 bin 标签；ŷᵢₖ: 预测概率；M: 基因数量
   - 用途: 优化 8-bin 离散化基因表达预测
   - 来源: Methods, Loss functions

6. **表达值离散化（ATAC→RNA）**:
   xᵢ' = log(1 + eᵢ)，然后分配到 7 个等宽 bin（bin 0 保留给 eᵢ = 0）
   - eᵢ: 原始表达值；xᵢ': 变换值
   - 用途: 将连续表达值离散化为分类标签
   - 来源: Methods, Value embedding

## 10 实验设计与证据链
- **数据集**:
  1. 10X Genomics PBMC multiome（9,964 细胞，RNA+ATAC 配对）
  2. SHARE-seq K562（1,413 细胞）
  3. BCL（B-cell lymphoma）multiome（14,566 细胞）
  4. 泛癌数据集（>100 万细胞，仅 RNA）
  5. Tabula Muris Senis 小鼠肾脏 scRNA-seq（21,647 细胞，含年龄注释）
  6. 小鼠肾脏 multiome（10X Genomics，用于训练跨物种模型）

- **指标**: 细胞聚类指标（AMI、NMI、ARI、HOM）；peak 水平 precision、recall、F1；基因表达 Pearson/Spearman 相关系数；GWAS 富集分数

- **基线**: BABEL、scButterfly（RNA→ATAC 和 ATAC→RNA）；ArchR、SCARlink（ATAC→RNA / CRE-gene 关联）

- **评测协议**: 四种场景（intra-dataset 1: 随机细胞划分；intra-dataset 2: 按细胞类型划分；inter-dataset 1: 相似组织跨数据集；inter-dataset 2: 不同组织跨数据集）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| RNA→ATAC 生成（intra-dataset） | Cisformer 在细胞内生成任务上优于现有方法 | PBMC 数据集，对比 BABEL、scButterfly | Cisformer 聚类指标略优 | Cisformer 在标准场景下具有竞争力 | 优势幅度有限，非显著突破 | Results 图 2a |
| RNA→ATAC 生成（inter-dataset 2: PBMC→脑） | Cisformer 跨组织泛化能力更强 | 训练 PBMC，测试脑组织 | Cisformer 显著优于 BABEL、scButterfly | 跨组织泛化是 Cisformer 的核心优势 | 未在更多组织类型上验证 | Results 图 2a、2b |
| Peak 水平精度评估 | Cisformer 生成的 ATAC 在 peak 水平更准确 | PBMC 测试集，precision/recall/F1 | Cisformer recall 提升约 50% | Cisformer 能更全面地恢复真实开放染色质区域 | precision 仅相当，可能伴随更多假阳性 | Additional file 1: Fig. S2b |
| ATAC→RNA 生成 | Cisformer 从染色质推断基因表达 | PBMC、SHARE-seq K562、BCL，对比 ArchR、SCARlink | Cisformer Pearson/Spearman 相关更高 | Cisformer 在 ATAC→RNA 方向同样有效 | 未与更多深度学习方法对比 | Results 图 2d、2e |
| 注意力分数 vs. 已知调控关系 | 注意力分数编码真实调控信息 | PBMC CD4+ T 细胞，12 个 TF ChIP-seq | 有 ChIP-seq 结合位点的 CRE 注意力分数显著更高 | 注意力分数可作为 TF 结合位点的代理指标 | 仅验证了少数 TF，非全基因组验证 | Results 图 3b、3c |
| CRE-gene 关联 vs. 表达-可及性相关性 | Cisformer 识别的调控关系更可靠 | BCL 数据集，比较随机 CRE-gene 对 | 高注意力 CRE-gene 对表达-可及性相关性更强 | 注意力分数优于随机基线 | 未与 ArchR/SCARlink 的关联直接比较 | Results 图 3d |
| GWAS 变异富集 | Cisformer 识别的 CRE 富集因果变异 | BCL 4 种细胞类型，94 个性状 | 免疫相关性状变异在对应细胞类型 CRE 中富集 | Cisformer 可优先排序功能 CRE | 富集程度中等，需实验验证 | Results 图 3e、3f |
| 泛癌 TF 识别 | Cisformer 可识别细胞类型特异性 TF | 泛癌 5 种非肿瘤细胞类型 | 识别出已知谱系特异性 TF（如 FLI1、RUNX 家族） | Cisformer 可扩展至大规模数据集 | 未与实验验证的 TF 调控网络对比 | Results 图 4b |
| 衰老相关 CRE/TF | Cisformer 可识别衰老相关调控变化 | 小鼠肾脏，TAL/PCT 上皮细胞 | 识别出年龄相关 CRE 和候选 TF（如 HNF、RXR、PPAR 家族） | Cisformer 可应用于衰老研究 | 未进行功能实验验证 | Results 图 5e、5f |

## 11 结论正确解读
- **任务范围**: 本文聚焦于单细胞 RNA↔ATAC 跨模态生成，而非直接的 TF–DNA 结合位点预测。注意力分数是「调控关联」的代理指标，不等同于物理结合。
- **Oracle/真值输入**: 训练时使用配对的 RNA+ATAC 多组学数据；ATAC→RNA 方向需要先验的基因表达信息（非零基因列表）作为辅助输入，这限制了其纯生成能力。
- **端到端状态**: 模型端到端训练完成，但下游分析（motif 富集、GWAS 富集）是独立的后处理步骤，不参与训练。
- **算力成本**: 使用 ≥2 张 A800 GPU，具体训练时间未报告。
- **历史数据依赖**: 依赖训练数据中的细胞类型组成；跨物种（人→小鼠）迁移需要额外训练。
- **模型依赖**: 注意力分数受模型容量、训练数据规模和特征选择策略影响；不同随机种子可能产生不同注意力分布。
- **最难情形**: 跨组织（PBMC→脑）和跨物种（人→小鼠）预测；高度相似的细胞亚型（如 CD8+ T 细胞亚型）区分。
- **群体/领域边界**: 仅适用于有配对 RNA-ATAC 数据的物种/组织；对没有参考 ATAC 数据的物种需重新训练。
- **不确定性**: 注意力分数未提供置信区间；GWAS 富集分析未报告多重检验校正细节。
- **有边界的复述**: Cisformer 在配对单细胞多组学数据上训练的 cross-attention 模型，能够以较高精度实现 RNA→ATAC 和 ATAC→RNA 双向生成，其注意力分数在验证的细胞类型和 TF 子集中与 ChIP-seq 结合位点和 GWAS 因果变异显著相关，但该相关性仅在有限验证集上建立，不等同于全基因组范围内的 TF 结合预测。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| ATAC→RNA 生成依赖先验基因信息 | 需要已知非零表达基因列表作为输入，无法完全从头生成 | 未明确提及 | Methods: Feature duplication and selection |
| 跨物种泛化需重新训练 | 小鼠肾脏模型需用小鼠 multiome 数据重新训练 | 未明确提及 | Results 图 5a |
| 注意力分数未覆盖所有 TF | 部分 TF 的 ChIP-seq 数据在相关细胞类型中不可用，无法验证 | 未明确提及 | Results 图 3b |
| 30 月龄小鼠未显示预期衰老趋势 | 衰老相关信号在最高龄组减弱 | 可能由于长寿动物的较慢衰老速率 | Results 图 5c |
| 模型可扩展性受限于特征选择 | 特征选择策略可能丢失低频但重要的信号 | 未明确提及 | Methods: Feature duplication and selection |
| 计算资源需求较高 | 需要至少 2 张 A800 GPU | 未明确提及 | Methods: Cisformer training |

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| ATAC→RNA 生成依赖先验基因信息 | 需要已知非零表达基因列表作为输入，无法完全从头生成 | 未明确提及 | Methods: Feature duplication and selection |
| 跨物种泛化需重新训练 | 小鼠肾脏模型需用小鼠 multiome 数据重新训练 | 未明确提及 | Results 图 5a |
| 注意力分数未覆盖所有 TF | 部分 TF 的 ChIP-seq 数据在相关细胞类型中不可用，无法验证 | 未明确提及 | Results 图 3b |
| 30 月龄小鼠未显示预期衰老趋势 | 衰老相关信号在最高龄组减弱 | 可能由于长寿动物的较慢衰老速率 | Results 图 5c |
| 模型可扩展性受限于特征选择 | 特征选择策略可能丢失低频但重要的信号 | 未明确提及 | Methods: Feature duplication and selection |
| 计算资源需求较高 | 需要至少 2 张 A800 GPU | 未明确提及 | Methods: Cisformer training |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 注意力分数作为调控强度的验证仅基于少数 TF（12 个 ChIP-seq） | 注意力分数可能与 TF 结合无关，而是反映了染色质状态的一般性特征（如开放程度） | 若注意力分数仅是开放染色质的代理，则其「调控关系」推断价值有限 | 在更多 TF、更多细胞类型上系统比较注意力分数与 ChIP-seq 的 ROC-AUC；与随机初始化模型对比 | Results 图 3b、3c |
| 跨组织泛化优势可能来自特征选择而非模型架构 | 非零基因/活跃 CRE 筛选可能在不同组织中保留了更保守的信号 | 若优势来自预处理而非 cross-attention，则架构创新价值被高估 | 对 BABEL/scButterfly 应用相同的特征选择策略后重新对比 | Results 图 2a |
| 未与最新的单细胞基础模型（如 scGPT、Geneformer）对比 | 这些模型可能具有更强的泛化能力 | 无法判断 Cisformer 在当前 SOTA 中的相对位置 | 在相同数据集上对比 Cisformer 与 scGPT 等模型的生成精度 | Results 图 2a–e |
| 注意力分数与表达-可及性相关性的比较未包含负对照 | 随机权重模型可能也产生类似的相关性模式 | 需要排除注意力分数仅是模型伪影的可能性 | 使用未训练模型或随机打乱标签的模型计算注意力分数作为负对照 | Results 图 3d |
| 泛癌分析中识别的 TF 多为已知谱系因子 | 模型可能只是复现了已知生物学，未发现新调控因子 | 若无法发现新因子，则模型的发现能力存疑 | 比较 Cisformer 识别的 TF 与随机背景的差异；在缺乏先验知识的细胞类型中验证 | Results 图 4b |
| 衰老分析中 30 月龄组未显示预期趋势 | 模型可能无法捕捉晚期衰老的表观遗传变化 | 限制了模型在衰老研究中的应用范围 | 使用更大样本量、更多时间点验证；与甲基化时钟等衰老指标交叉验证 | Results 图 5c |
| 未报告注意力分数的稳定性/可重复性 | 不同训练种子可能产生不同的调控关系推断 | 若注意力分数不稳定，则下游生物学结论不可靠 | 多次重复训练，计算注意力分数的一致性（如 ICC） | Methods: Cisformer training |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **Cross-attention 作为调控关系推断的统一框架** [可迁移概念]：将生成任务与关系推断共享同一注意力机制，避免额外的解释模块。可迁移到 TF–DNA 结合预测：用 TF 表达/活性作为 query，DNA 序列或染色质特征作为 key/value，注意力分数直接作为结合强度预测。

2. **特征选择策略（非零特征 + 复制）** [可迁移方法]：对高维稀疏生物数据，显式筛选非零特征并复制以平衡类别，可显著提升训练稳定性。可迁移到 TF 结合位点预测：只保留有 ChIP-seq 信号的区域作为正样本，复制以平衡负样本。

3. **Peak 索引编码（digit decomposition）** [可迁移方法]：将大规模离散词汇表（百万级）分解为逐位数字嵌入，避免存储巨大嵌入矩阵。可迁移到基因组位置编码：将基因组坐标分解为逐位数字嵌入，用于处理全基因组范围的调控元件。

4. **跨组织泛化评估协议** [可迁移实验设计]：四种递进难度的评估场景（随机划分→细胞类型划分→相似组织→不同组织）为模型泛化能力提供了系统评估框架。可迁移到 TF 结合预测：在不同细胞类型、不同组织间评估模型泛化。

5. **注意力分数 + 外部验证的闭环** [可迁移实验设计]：用 ChIP-seq 和 GWAS 变异独立验证注意力分数的生物学有效性。可迁移到 TF–DNA 结合研究：用 ChIP-seq、SNP 富集、eQTL 等独立数据验证模型预测的结合位点。

6. **[Analysis] 注意力分数 ≠ 结合强度** [可迁移警示]：注意力分数是模型内部的关联度量，可能受训练数据分布、特征选择等影响，不能直接等同于物理结合亲和力。在 TF–DNA 结合研究中，需用独立实验数据（如 ChIP-seq、EMSA、SPR）校准。

## 15 与已有知识连接
- **BABEL**（Wu et al., 2021）：基于 VAE 的单细胞跨模态预测，Cisformer 的直接对比基线。Cisformer 用 cross-attention 替代 VAE 隐空间，提升可解释性。
- **scButterfly**（Cao et al., 2023）：基于 dual-aligned VAE 的单细胞跨模态预测，同样为 Cisformer 的对比基线。
- **ArchR**（Granja et al., 2021）：基于相关性的 CRE-gene 关联方法，Cisformer 在 ATAC→RNA 任务中与之对比。
- **SCARlink**（Herring et al., 2023）：基于正则化泊松回归的 CRE-gene 关联方法，Cisformer 的对比基线。
- **Enformer**（Avsec et al., 2021）：基于 Transformer 的 DNA 序列→表达预测模型，与 Cisformer 共享 Transformer 架构思想，但输入为 DNA 序列而非单细胞表达谱。
- **scGPT / Geneformer**（Cui et al., 2024; Theodoris et al., 2023）：单细胞基础模型，Cisformer 未与之对比，但同属 Transformer 在单细胞领域的应用。
- **TF–DNA 结合预测**（如 DeepBind、DeepSEA、BPNet）：这些模型从 DNA 序列预测 TF 结合，与 Cisformer 的注意力分数可形成互补——Cisformer 提供细胞类型特异的调控关联，序列模型提供基序层面的结合偏好。
- **[Analysis] 候选连接方向**：Cisformer 的注意力分数可作为先验特征输入到 TF–DNA 结合预测模型中，或将序列模型的基序信息作为注意力分数的正则化约束。

## 16 研究想法
**Agent 生成的研究候选**：

1. **TF–DNA 结合预测的 Cross-attention 框架** [unverified]
   - **名称**: TF-BindFormer
   - **来源局限/观察**: Cisformer 用 cross-attention 推断 CRE-gene 调控，但未直接预测 TF 结合位点；现有 TF 结合预测模型多为序列卷积/Transformer，缺乏细胞类型上下文
   - **核心假设**: 以 TF 表达/活性为 query、DNA 序列 embedding 为 key/value 的 cross-attention 可同时预测结合位点和细胞类型特异性
   - **初步方法**: 在 Cisformer 架构基础上，将 query 改为 TF 嵌入，key/value 改为 DNA 序列 k-mer embedding，输出为逐位置结合概率
   - **验证方式**: ENCODE ChIP-seq 数据，与 BPNet、DeepSEA 对比 AUC；细胞类型特异性用同一 TF 在不同细胞类型中的结合差异评估
   - **创新状态**: unverified

2. **注意力分数作为 TF 结合先验的迁移学习** [unverified]
   - **名称**: AttnPrior-TF
   - **来源局限/观察**: Cisformer 的注意力分数在验证的 TF 中与 ChIP-seq 显著相关，但未与序列模型结合
   - **核心假设**: 将 Cisformer 注意力分数作为序列模型的先验特征可提升低数据量 TF 的结合预测
   - **初步方法**: 在 BPNet 的输入中拼接 Cisformer 注意力分数作为附加特征通道，在低数据量 TF 上微调
   - **验证方式**: 与无先验的 BPNet 对比；在 ChIP-seq 数据量 < 100 峰的 TF 上评估
   - **创新状态**: unverified

3. **单细胞 TF 结合动态推断** [unverified]
   - **名称**: scTF-Dynamics
   - **来源局限/观察**: Cisformer 在泛癌和衰老中识别了细胞类型特异性 TF，但未追踪 TF 结合动态变化
   - **核心假设**: 在分化或疾病进展的伪时间轨迹上，Cisformer 注意力分数的变化可反映 TF 结合动态
   - **初步方法**: 对分化轨迹上的细胞分别计算注意力分数，分析 TF-CRE 调控强度的伪时间变化
   - **验证方式**: 与已知分化调控 TF 的 ChIP-seq 时间序列对比；敲低实验验证
   - **创新状态**: unverified

4. **多模态调控基础模型** [partially checked]
   - **名称**: MultiModal-RegFormer
   - **来源局限/观察**: Cisformer 仅处理 RNA 和 ATAC 两种模态，但 DNA 甲基化、组蛋白修饰等也参与调控
   - **核心假设**: 将更多表观遗传模态纳入 cross-attention 框架可提升调控推断精度
   - **初步方法**: 扩展 Cisformer 输入为 RNA + ATAC + 甲基化 + H3K27ac，用共享的 cross-attention 层建模多模态交互
   - **验证方式**: 与 Cisformer 在相同数据集上对比；用 CRISPR 干扰验证新识别的调控关系
   - **创新状态**: partially checked（Cisformer 已验证双模态可行性，多模态扩展未验证）

5. **TF 结合基序与注意力分数的联合建模** [unverified]
   - **名称**: Motif-Attn-TF
   - **来源局限/观察**: Cisformer 的注意力分数缺乏序列层面的可解释性，无法回答「TF 结合在哪个基序」
   - **核心假设**: 将 DNA 序列基序信息作为注意力分数的正则化约束，可同时获得位点级和序列级可解释性
   - **初步方法**: 在 Cisformer 损失函数中加入基序一致性正则项，约束高注意力 CRE 区域富集已知 TF 基序
   - **验证方式**: 与 Cisformer 原始注意力分数对比基序富集程度；用突变分析验证关键碱基
   - **创新状态**: unverified