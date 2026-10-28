## 01 基本信息
- **标题**：TF-EPI: an interpretable enhancer-promoter interaction detection method based on Transformer
- **作者与单位**：Liu, Bowen; Zhang, Weihang; Zeng, Xin; Loza, Martin; Park, Sung-Joon; Nakai, Kenta（单位未在摘要中提供，推测为东京大学人类基因组中心相关机构，因致谢提及SHIROKANE超算系统）
- **期刊/预印本平台**：Frontiers in Genetics
- **年份**：2024-08-26
- **论文类型**：方法学（Method）论文
- **领域**：基因组学 / 调控基因组学 / 深度学习
- **关键词**：enhancer-promoter interaction (EPI)、Transformer、attention mechanism、interpretability、motif discovery、transfer learning
- **DOI/arXiv 号**：10.3389/fgene.2024.1444459
- **代码**：https://github.com/lbw1995/TF-EPI
- **数据**：BENGI 数据集（6 个细胞系：GM12878, HeLa-S3, HMEC, IMR90, K562, NHEK）；Fulco 数据集（K562 细胞系，CRISPR 验证的 EPI）
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 深度学习」交叉方向，聚焦增强子-启动子互作（EPI）这一顺式调控核心问题。与 TF–DNA 结合机制课题的关联在于：EPI 本质上由 TF 结合增强子/启动子上的 motif 所介导，本文通过 Transformer 注意力机制定位关键 motif 并识别对应 TF，为从序列出发解析 TF–DNA 结合提供了可迁移的注意力解释框架。其方法（k-mer tokenization + Transformer + 注意力解释）可直接迁移到 TF 结合位点预测与 motif 发现任务。

## 02 一句话总结
本文提出 TF-EPI，一个仅以 DNA 序列为输入的 Transformer 编码器 + TextCNN 分类器模型，在 BENGI 和 Fulco 数据集上以更高 AUROC 预测增强子-启动子互作，并通过注意力机制实现序列层面的可解释性，发现与 JASPAR/UniBind 数据库匹配的细胞系特异性 TF motif。

## 03 研究问题
- **具体问题**：能否仅从 DNA 序列（增强子与启动子序列对）准确预测增强子-启动子互作（EPI），并同时提供序列层面的可解释性（即定位哪些子序列对互作起决定性作用）？
- **为什么重要**：EPI 是基因表达调控的核心机制，与疾病密切相关。实验方法（Hi-C、PCHi-C 等）成本高、耗时；现有计算方法要么依赖大量表观基因组数据（限制新样本应用），要么使用 CNN 等黑箱模型缺乏可解释性，难以定位关键调控序列。
- **现有方法不足**：
  - 基于表观基因组特征的方法（如 RIPPLE、TargetFinder、TransEPI）需要 ChIP-seq、DNase-seq 等数据，对新样本或缺乏这些数据的细胞系不适用。
  - 纯序列方法（EPIANN、EPI-DLMH）在 BENGI 数据集上 AUROC 仅约 0.5，几乎无效，且使用 CNN 难以解释哪些子序列贡献了分类结果。
  - 深度模型（如 Enformer、DeepC）受限于输入序列长度，无法检测远距离 EPI。
- **精确研究问题（Can 形式）**：Can a Transformer-based model, using only DNA sequences of enhancer-promoter pairs, achieve accurate EPI detection while providing interpretable identification of cell type-specific regulatory motifs via its attention mechanism?

## 04 背景与发展脉络
> 注：以下脉络基于本文引言与相关文献，标注为「经外部核验」的部分来自文中引用的已知文献；「仅本文框架」的部分为作者叙述。

1. **实验方法时代**（经外部核验）：
   - Hi-C（Rao et al., 2014）、ChIA-PET（Fullwood et al., 2009）、PCHi-C（Schoenfelder et al., 2018）等高通量染色质构象捕获技术可直接检测 EPI，但成本高、需深度测序、分辨率有限。
   - 局限：难以大规模应用于多种细胞类型和条件。

2. **基于表观基因组特征的计算方法**（经外部核验）：
   - RIPPLE（Roy et al., 2015）、TargetFinder（Whalen et al., 2016）、TransEPI（Chen et al., 2022）利用 ChIP-seq、DNase-seq 等特征训练分类器。
   - 优点：准确率较高；局限：依赖大量实验数据，对新样本或缺乏特定数据的细胞系不适用。

3. **纯序列深度学习方法**（经外部核验）：
   - EPIANN（Mao et al., 2017）、SPEID（Singh et al., 2019）、EPI-DLMH（Min et al., 2021）直接从 DNA 序列预测 EPI。
   - 局限：主要在 TargetFinder 数据集上验证，该数据集存在 inflated performance 问题（Xi and Beer, 2018）；在 BENGI 数据集上表现差（AUROC ≈ 0.5）；CNN 架构缺乏可解释性。

4. **大规模序列模型**（经外部核验）：
   - DeepC（Schwessinger et al., 2020）、Akita（Fudenberg et al., 2020）、Enformer（Avsec et al., 2021）可预测染色质互作，但要求输入序列在限定距离内，无法处理远距离 EPI。

5. **Transformer 在基因组学中的应用**（经外部核验）：
   - Transformer（Vaswani et al., 2017）在 NLP 和 DNA 序列分析中表现优异（Ji et al., 2021），其注意力机制天然适合捕捉长程依赖和关键子序列。

6. **本文主张的位置**（仅本文框架）：
   - TF-EPI 是首个将 Transformer 编码器 + TextCNN 用于纯序列 EPI 检测的方法，在 BENGI 数据集上显著优于 EPIANN 和 EPI-DLMH，同时通过注意力机制提供序列级可解释性，实现 de novo motif 发现和 TF 识别。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 实验方法成本高 | Hi-C、PCHi-C 需深度测序，耗时昂贵 | 技术本身需要高分辨率染色质构象捕获 | Introduction 第 2 段 |
| 表观基因组方法依赖大量数据 | 新样本或缺乏 ChIP-seq/DNase-seq 数据的细胞系无法应用 | 特征工程需要对应实验数据 | Introduction 第 3 段 |
| 纯序列方法在 BENGI 上失效 | EPIANN、EPI-DLMH 在 BENGI 数据集 AUROC ≈ 0.5，AUPR ≈ 0.1 | TargetFinder 数据集存在 inflated performance；CNN 难以学习高阶序列互作 | Results 3.2 节，图 2A-C |
| 现有深度模型缺乏可解释性 | CNN 固定参数无法定位关键子序列 | CNN 的池化与卷积操作难以回溯到具体序列位置 | Introduction 第 4 段 |
| 远距离 EPI 检测受限 | DeepC、Enformer 等要求输入序列在限定距离内 | 模型设计时对输入长度有约束 | Introduction 第 4 段 |
| 细胞系特异性调控机制难以解析 | 不同细胞系 EPI 的 TF 组合不同，难以统一建模 | 基因调控具有高度细胞类型特异性 | Results 3.6 节，图 4A-B |

## 06 核心思想
1. **表面方法**：
   - 将增强子和启动子 DNA 序列分别切分为 6-mer token，添加 CLS 和 SEP 特殊 token 后输入 Transformer 编码器（4 层），提取特征后经 TextCNN（3 种卷积核，6 维）分类，输出 EPI 二分类结果。
   - 预训练阶段在人类参考基因组 hg19 的非重叠序列上做 masked language modeling（mask 15% token），微调阶段使用细胞系特异的 EPI 数据。

2. **核心洞察**：
   - Transformer 的注意力机制天然适合捕捉序列中远距离的、非线性的互作关系，而 EPI 正是增强子与启动子之间通过 TF 结合 motif 介导的长程调控事件。
   - 注意力权重可以直接解释为「哪些 6-mer 子序列对分类决策贡献最大」，从而将黑箱分类转化为可验证的生物学假设（motif → TF → 调控机制）。
   - 通过对比正负样本的注意力模式，可以区分「通用调控 motif」与「细胞系特异性 motif」，揭示 EPI 的异质性与共性。

3. **可能的普适教训** [Analysis]：
   - 在序列级调控预测任务中，将「分类性能」与「注意力解释」联合优化，比单独追求准确率更有价值——因为生物学验证成本高，可解释性直接决定方法能否产生可检验的假设。
   - 预训练 + 微调范式在基因组序列上有效：预训练学习通用序列语法，微调适配特定调控任务，可缓解小样本细胞系数据不足的问题。
   - 注意力矩阵的「多粒度分析」（单点注意力、pair 注意力、跨区域注意力）为解析顺式调控语法提供了新工具。

## 07 方法总览
- **输入**：增强子序列（3,000 bp）与启动子序列（2,000 bp，TSS 上游 1,500 bp + 下游 500 bp）的 DNA 序列对。
- **输出**：二分类概率（该增强子-启动子对是否互作）。
- **模块**：
  1. **Tokenizer**：6-mer 切分，构建词典，添加 [CLS]（序列对开头）和 [SEP]（增强子与启动子之间）特殊 token。
  2. **Embedding**：token embedding + position embedding。
  3. **Transformer Encoder**：4 层编码器，多头自注意力，捕捉序列内与跨序列的 token 依赖。
  4. **TextCNN**：3 种卷积核（尺寸 6），对 Transformer 输出做卷积 + max pooling，捕捉局部 n-gram 特征。
  5. **分类头**：全连接层 + softmax，输出二分类。
- **训练**：
  - 预训练：hg19 非重叠序列，mask 15% token，MLM 目标。
  - 微调：各细胞系 EPI 数据，二分类交叉熵损失。
  - 数据增强：正负样本平衡（训练集调整至正负均衡）。
- **反馈回路**：注意力矩阵 → de novo motif 发现 → 与 JASPAR/UniBind 比对 → 验证生物学意义 → 反馈到模型解释。
- **工具**：Tommot（motif 比对）、BEDTools（序列重叠分析）、STRING（TF 互作网络）。
- **流程**：序列对 → 6-mer tokenize → embedding → Transformer 编码 → TextCNN 分类 → 注意力矩阵提取 → motif 发现与 TF 匹配 → 生物学验证。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 6-mer Tokenizer | 将 DNA 序列切分为 6-mer token | 将连续序列离散化为可学习的 token；6-mer 可覆盖大部分 TF 结合位点核心序列 | 输入：DNA 序列；输出：token 序列 | Methods 2.2 节 | 预期影响：token 粒度改变会影响 motif 发现分辨率；更短 k-mer 可能丢失长 motif 信息，更长 k-mer 增加词典稀疏性 [Analysis] |
| Transformer Encoder（4 层） | 捕捉 token 间长程依赖与高阶互作 | EPI 涉及增强子-启动子间远距离互作，需全局上下文建模 | 输入：embedding 序列；输出：上下文增强的 token 表示 | Results 3.3 节，图 2D-E（注意力可视化显示预训练与微调后注意力模式差异） | 实测消融：移除 Transformer 或固定其参数导致 t-SNE 中正负样本混杂（图 2G），说明 Transformer 对特征判别至关重要 |
| TextCNN | 对 Transformer 输出做局部 n-gram 特征提取与分类 | 捕捉局部序列模式（如 motif 组合），将序列特征映射为分类结果 | 输入：Transformer 输出；输出：分类 logits | Methods 2.4 节 | 预期影响：移除 TextCNN 需替换为其他分类头，可能降低对局部 motif 组合的敏感性 [Analysis] |
| 注意力解释模块 | 从最后一层 Transformer 的注意力矩阵提取高注意力区域，发现 de novo motif | 提供序列级可解释性，定位关键调控子序列 | 输入：注意力矩阵；输出：高注意力区域 → motif 序列 | Results 3.4 节，图 3A-B（>95% motif 与 JASPAR 匹配，p < 0.02） | 预期影响：移除后模型仍可分类但失去生物学解释能力，无法发现新 motif [Analysis] |
| DANN 域自适应模块 | 跨细胞系 EPI 检测时对齐源域与目标域特征 | 细胞系间 EPI 高度异质，直接迁移效果差 | 输入：源域+目标域特征；输出：域判别损失 + 分类损失 | Results 3.6 节，图 4C（DANN 平均 AUROC 提升 0.015） | 实测消融：无 DANN 时跨细胞系 AUROC 下降（图 4C），说明域自适应对跨细胞系泛化有效 |

## 09 关键公式符号
1. **注意力机制**（Transformer 标准公式）：
   - Attention(Q, K, V) = softmax(QK^T / √d_k) V
   - 其中 Q、K、V 分别为 query、key、value 矩阵，d_k 为 key 维度。多头注意力将多个注意力头拼接后线性变换。

2. **注意力归一化**（Methods 2.5 节）：
   - attention_i^normalized = (attention_i^mean − attention_min) / (attention_max − attention_min)
   - 其中 attention_i^mean 为第 i 个碱基的平均注意力值，attention_max 和 attention_min 分别为所有碱基中 attention_i^mean 的最大值和最小值。

3. **超几何检验**（Methods 2.5 节）：
   - P(k-mer 在正样本中富集) = [C(K, k) · C(N−K, n−k)] / C(N, n)
   - 其中 k 为包含特定高注意力序列的正样本数，N 为总 EPI 对数，K 为总正样本数，n 为包含该序列的总样本数。

4. **分类损失**（Methods 2.7 节）：
   - L_class = −Σ_{i∈src} y_i · log p(y_i | x_i)
   - 其中 src 为源域样本，y_i 为标签，p(y_i | x_i) 为预测概率。

5. **域判别损失**（Methods 2.7 节）：
   - L_domain = −Σ_{i∈src} log p(domain=src | x_i) − Σ_{j∈tgt} log p(domain=tgt | x_j)
   - 其中 src 和 tgt 分别表示源域和目标域。

6. **总损失**（Methods 2.7 节）：
   - L_total = L_class − λ · L_domain
   - 其中 λ 为平衡分类与域判别损失的权重。

## 10 实验设计与证据链
- **数据集**：
  - BENGI 数据集：6 个细胞系（GM12878, HeLa-S3, HMEC, IMR90, K562, NHEK），包含正负 EPI 对。
  - Fulco 数据集：K562 细胞系，CRISPR 验证的 EPI。
- **指标**：AUROC（主要指标）、AUPR。
- **基线方法**：EPIANN、EPI-DLMIH（均为纯序列方法）。
- **训练/验证/测试划分**：每个细胞系生成三组独立的训练、验证、测试集（Methods 2.1 节）。
- **硬件**：NVIDIA Tesla A100 40G GPU。
- **评测协议**：各细胞系独立训练与测试；跨细胞系实验使用 DANN 域自适应。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| BENGI 数据集性能对比 | TF-EPI 优于现有纯序列方法 | 与 EPIANN、EPI-DLMIH 对比，6 个细胞系 | TF-EPI 在所有细胞系上 AUROC 最高 | Transformer 架构能更有效学习序列互作特征 | 未与基于表观基因组特征的方法对比，不能声称全面最优 | Results 3.2 节，图 2A-C |
| Fulco 数据集性能对比 | TF-EPI 在 CRISPR 验证数据上有效 | K562 细胞系，与 EPIANN、EPI-DLMIH 对比 | TF-EPI AUROC 高于基线 | 在实验验证的 EPI 上具有泛化能力 | 样本量小，统计显著性未报告 | Results 3.2 节 |
| 注意力可视化（预训练 vs 微调） | 微调改变注意力模式，聚焦关键区域 | 同一 EPI 对输入预训练与微调模型 | 微调后注意力更集中，SEP token 附近出现高注意力垂直线 | 微调使模型学习到任务相关的序列特征 | 未定量评估注意力与真实调控元件的重叠 | Results 3.3 节，图 2D-F |
| 消融实验（移除/固定 Transformer） | Transformer 对分类性能必要 | t-SNE 可视化，对比完整模型 vs 移除 Transformer vs 固定 Transformer 参数 | 移除或固定 Transformer 后正负样本 t-SNE 混杂 | Transformer 编码器对特征判别至关重要 | 未报告定量 AUROC 变化，仅可视化 | Results 3.3 节，图 2G |
| De novo motif 发现 | 注意力区域富集已知 TF motif | 与 JASPAR 数据库比对（Tomtom） | >95% motif 与已知 motif 匹配（p < 0.02） | 注意力机制能识别生物学真实的 TF 结合位点 | 未与 ChIP-seq 实验直接验证 | Results 3.4 节，图 3A-B |
| 细胞系特异性 TF 分析 | 不同细胞系 EPI 使用不同 TF | 对比各细胞系发现的 motif 对应 TF | 多数 TF 仅存在于 1-2 个细胞系，少数（如 MXI1）在所有细胞系中出现 | EPI 具有细胞系特异性与共性 | 未系统比较 TF 表达水平与 motif 活性的关系 | Results 3.6 节，图 4B |
| 跨细胞系 EPI 检测（DANN） | DANN 提升跨细胞系泛化 | 有 DANN vs 无 DANN，源域→目标域 | DANN 平均 AUROC 提升 0.015 | 域自适应能缓解细胞系间异质性 | 提升幅度小，可能受限于数据规模 | Results 3.6 节，图 4C |

## 11 结论正确解读
- **任务范围**：本文仅针对增强子-启动子互作（EPI）的二分类预测，输入为 DNA 序列对，不涉及 TF 结合位点的逐碱基定位或结合强度预测。
- **Oracle/真值输入**：训练标签来自 BENGI 和 Fulco 数据集的实验定义（如 Hi-C、PCHi-C、CRISPR 验证），非本方法独立验证。
- **端到端状态**：模型为端到端训练（序列 → 分类），但 de novo motif 发现和 TF 识别是事后分析（post-hoc），不参与训练。
- **算力成本**：训练时间在 BENGI GM12878 上为 39 小时（A100 GPU），显著长于 EPI-DLMIH（24 小时），但短于 EPIANN（115 小时）；内存占用未报告。
- **历史数据依赖**：预训练使用 hg19 参考基因组序列，不依赖特定细胞系；微调依赖各细胞系 EPI 标签。
- **模型依赖**：性能高度依赖 Transformer 编码器 + TextCNN 的组合；移除 Transformer 后特征判别显著下降。
- **最难情形**：Fulco 数据集（CRISPR 验证）上所有方法性能均较低，提示小样本和实验噪声是挑战；远距离 EPI 的检测能力未专门评估。
- **群体/领域边界**：仅在人类细胞系（B 淋巴细胞、宫颈癌、乳腺上皮、肺成纤维、白血病、表皮角质形成细胞）上验证，未涉及其他物种或体内数据。
- **不确定性**：注意力权重与真实调控元件的因果关系未建立；motif 与 TF 的对应依赖数据库注释，可能存在假阳性。
- **有边界的复述**：TF-EPI 在 BENGI 和 Fulco 数据集的多个细胞系上，以仅序列输入的方式取得了优于 EPIANN 和 EPI-DLMIH 的 EPI 分类性能，并通过注意力机制识别出与已知数据库匹配的细胞系特异性 TF motif；但该方法的泛化性、因果解释力和远距离 EPI 检测能力尚未充分验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 模型复杂度高 | 结构复杂，增加时间和内存使用 | 引入更轻量级的 Transformer 模型 | Limitations 节 |
| 序列信息有限 | 仅从 DNA 序列获取信息，可能不如基于表观基因组特征的方法准确 | 整合 DNA 序列与选定的表观基因组特征 | Limitations 节 |
| 数据分辨率不足 | 使用较低分辨率的 EPI 数据 | 使用更高分辨率的 EPI 互作数据进行验证 | Limitations 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 基线方法选择有限 | 仅对比 EPIANN 和 EPI-DLMIH，未与基于表观基因组特征的方法（如 TargetFinder、TransEPI）或更现代的深度模型（如 Enformer）对比 | 无法判断 TF-EPI 在更广泛方法谱系中的真实位置 | 在相同数据划分下加入更多基线方法，特别是基于表观基因组特征的方法 | Results 3.2 节 |
| 消融实验缺乏定量指标 | 移除/固定 Transformer 仅用 t-SNE 可视化，未报告 AUROC/AUPR 变化 | 无法量化 Transformer 的贡献大小 | 对消融变体重新计算 AUROC/AUPR 并报告统计显著性 | Results 3.3 节，图 2G |
| Motif 发现验证依赖数据库 | 与 JASPAR/UniBind 的匹配是计算预测，未用 ChIP-seq 或突变实验验证 | 注意力区域可能富集非功能性序列 | 对高注意力 motif 进行电泳迁移率变动分析（EMSA）或报告基因实验验证 | Results 3.4 节 |
| 跨细胞系提升幅度小 | DANN 仅提升 AUROC 0.015，可能不具实际意义 | 跨细胞系泛化仍是核心挑战，提升可能来自噪声 | 在更多细胞系对上进行系统评估，并报告置信区间 | Results 3.6 节，图 4C |
| 注意力解释的因果性未建立 | 注意力权重高不代表该区域对互作有因果贡献 | 可解释性方法常存在「注意力不是解释」的争议 | 用输入扰动或梯度归因方法交叉验证注意力区域的重要性 | Results 3.4 节 |
| 未评估远距离 EPI | 输入序列长度固定（增强子 3kb + 启动子 2kb），未测试更远距离的互作 | EPI 可跨越数百 kb，长度限制可能遗漏重要互作 | 在长距离 EPI 数据集上测试，或设计可变长度输入 | Methods 2.1 节 |
| 预训练数据与任务不匹配 | 预训练使用 hg19 全基因组序列，与 EPI 任务无直接关联 | 预训练收益可能有限，领域自适应预训练可能更有效 | 对比在 EPI 相关序列上预训练 vs 全基因组预训练的性能差异 | Methods 2.3 节 |

## 14 学到什么
> 标题：Agent 提炼的知识候选

1. **注意力即解释的范式**：TF-EPI 展示了将 Transformer 注意力权重直接转化为生物学可解释结果（motif → TF）的完整流程。对于 TF–DNA 结合课题，可迁移此思路：训练 TF 结合位点预测模型后，用注意力权重定位关键碱基，再与已知 motif 数据库比对，实现「预测 + 解释」一体化。

2. **k-mer tokenization 的粒度选择**：6-mer 被证明能有效覆盖 TF 结合位点核心序列，同时保持词典规模可控。在 TF–DNA 结合预测中，可系统比较不同 k 值（4/5/6/7）对 motif 发现分辨率和分类性能的影响。

3. **预训练 + 微调的两阶段策略**：在基因组序列上预训练（MLM）再在特定调控任务上微调，能提升小样本细胞系上的性能。对 TF–DNA 结合课题，可考虑在 ChIP-seq 峰序列上预训练，再微调到特定 TF 的结合预测任务。

4. **域自适应（DANN）处理细胞系异质性**：通过梯度反转层对齐不同细胞系的特征分布，缓解了 EPI 的细胞系特异性问题。TF–DNA 结合同样具有细胞类型特异性，此方法可迁移到跨细胞系 TF 结合预测。

5. **多粒度注意力分析**：作者不仅分析单点注意力，还分析 token pair 的注意力（6-mer pairs），揭示了序列间的互作模式。对 TF–DNA 结合，可分析 TF 结合位点内部及位点间的注意力模式，理解协同结合机制。

6. **正负样本对比发现特异性 motif**：通过对比正负样本的注意力模式，区分「通用」与「细胞系特异性」motif。对 TF–DNA 结合课题，可对比不同细胞类型中同一 TF 的结合 motif 差异，揭示结合特异性的序列基础。

7. **外部数据库验证流程**：用 JASPAR、UniBind、STRING 等数据库交叉验证发现的 motif 和 TF，增强了结果的可信度。此验证流程可直接迁移到 TF–DNA 结合研究。

8. **超几何检验用于 motif 富集分析**：用超几何检验筛选显著富集的 k-mer，是简单有效的统计方法，可迁移到 TF 结合 motif 的显著性评估。

## 15 与已有知识连接
- **Enformer（Avsec et al., 2021）**：同为 Transformer 架构的调控预测模型，但 Enformer 使用更长的输入（200 kb）和回归目标（多种功能基因组信号），TF-EPI 则聚焦 EPI 二分类且强调注意力解释。两者可互补：Enformer 提供更广的调控上下文，TF-EPI 提供更精细的序列级解释。
- **DNABERT（Ji et al., 2021）**：TF-EPI 的预训练策略和 k-mer tokenization 直接借鉴 DNABERT，但 DNABERT 面向通用基因组理解，TF-EPI 针对 EPI 任务微调并利用注意力做解释。
- **TargetFinder（Whalen et al., 2016）**：基于表观基因组特征的 EPI 预测方法，TF-EPI 与其对比显示纯序列方法的可行性，但两者可融合：序列特征 + 表观基因组特征可能进一步提升性能。
- **DeepC / Akita（Schwessinger et al., 2020; Fudenberg et al., 2020）**：基于 Hi-C 数据的染色质互作预测模型，TF-EPI 的输入更简单（仅序列），但无法捕捉 3D 基因组结构信息。两者可结合：TF-EPI 预测的候选互作对可用 Hi-C 数据验证。
- **JASPAR / UniBind 数据库**：TF-EPI 的 motif 验证依赖这两个数据库，它们也是 TF–DNA 结合研究的基础资源。
- **BENGI 数据集（Moore et al., 2020）**：EPI 预测的基准数据集，TF-EPI 在此验证，该数据集也可用于 TF–DNA 结合模型的间接评估。
- **DANN（Ganin and Lempitsky, 2015）**：域自适应网络，TF-EPI 将其用于跨细胞系迁移，此方法在 TF 结合预测中已有类似应用（如跨细胞系 ChIP-seq 预测）。

## 16 研究想法
> 标题：Agent 生成的研究候选

1. **候选名称**：TF-EPI-TFBS：基于注意力共享的 TF 结合位点与增强子-启动子互作联合预测模型
   - **来源局限/观察**：TF-EPI 将 EPI 视为黑箱分类任务，虽能发现 motif，但未显式建模 TF 结合事件。TF–DNA 结合是 EPI 的上游机制，联合建模可能提升两者性能。
   - **核心假设**：EPI 的正样本中，增强子和启动子区域应富集协同结合的 TF motif；联合预测 TF 结合位点和 EPI 可共享注意力特征，互相约束。
   - **初步方法**：在 TF-EPI 架构上增加 TF 结合位点预测头（多任务学习），用 ChIP-seq 数据作为辅助监督；注意力权重同时用于 EPI 分类和 TFBS 定位。
   - **验证方式**：在 BENGI + ENCODE ChIP-seq 数据上评估，比较联合模型 vs 单任务模型的 AUROC 和 motif 发现准确率。
   - **创新状态**：unverified

2. **候选名称**：CrossCell-TFEPI：基于预训练 + 域自适应的跨细胞系 TF–DNA 结合预测
   - **来源局限/观察**：TF-EPI 的 DANN 仅提升 0.015 AUROC，说明域自适应在 EPI 任务上效果有限。TF–DNA 结合具有更强的细胞类型特异性，可能需要更精细的域对齐策略。
   - **核心假设**：TF 结合位点的细胞类型特异性主要来自染色质可及性和协同因子差异，而非核心 motif 序列差异；域自适应应聚焦于可及性特征而非序列特征。
   - **初步方法**：在 TF-EPI 的 DANN 基础上，引入 ATAC-seq 可及性特征作为辅助输入，并设计「序列域」和「可及性域」双域判别器。
   - **验证方式**：在 ENCODE 多细胞系 ChIP-seq 数据上评估跨细胞系 TF 结合预测 AUROC。
   - **创新状态**：unverified

3. **候选名称**：LongRange-TFEPI：支持长距离（>100 kb）EPI 检测的稀疏注意力 Transformer
   - **来源局限/观察**：TF-EPI 输入仅 5 kb（增强子 3 kb + 启动子 2 kb），无法检测远距离 EPI。真实增强子-启动子距离可达数百 kb。
   - **核心假设**：远距离 EPI 的序列信号稀疏但存在，稀疏注意力可高效捕捉长程依赖而不引入过多计算。
   - **初步方法**：将 TF-EPI 的密集注意力替换为 Longformer 或 BigBird 风格的稀疏注意力，输入扩展到 100 kb 以上；用 Hi-C 数据生成远距离训练样本。
   - **验证方式**：在包含远距离 EPI 的测试集上评估 AUROC，并与 Enformer 对比。
   - **创新状态**：unverified

4. **候选名称**：MutScan-TFEPI：基于注意力归因的 TF 结合位点突变效应预测
   - **来源局限/观察**：TF-EPI 的注意力可定位关键 motif，但未评估突变对 EPI 的影响。疾病相关 SNP 常位于 TF 结合位点。
   - **核心假设**：注意力权重的变化可预测突变对 EPI 的破坏程度，且与 eQTL 效应相关。
   - **初步方法**：对每个 SNP，计算突变前后注意力权重差异和分类概率变化，作为突变效应分数；与 eQTL 和 GWAS 数据关联分析。
   - **验证方式**：在 GTEx eQTL 数据上评估突变效应分数与 eQTL 效应的相关性。
   - **创新状态**：unverified

5. **候选名称**：Epigenome-Integrated TFEPI：融合染色质状态特征的 EPI 预测
   - **来源局限/观察**：TF-EPI 仅用序列，但作者承认序列信息有限，可能不如基于表观基因组特征的方法。染色质状态（如 H3K27ac、H3K4me1）是增强子活性的关键标志。
   - **核心假设**：将染色质状态特征作为辅助输入可提升 EPI 预测性能，同时保持序列级可解释性。
   - **初步方法**：在 TF-EPI 的 Transformer 输出后拼接染色质状态 embedding（如 ChromHMM 状态），联合训练分类器。
   - **验证方式**：在 BENGI 数据集上对比有/无染色质特征的 AUROC，并评估注意力解释是否仍有效。
   - **创新状态**：unverified