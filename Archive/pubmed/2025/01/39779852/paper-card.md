## 01 基本信息

- **标题**：A foundation model of transcription across human cell types
- **作者**：Fu, Xi; Mo, Shentong; Buendia, Alejandro; Laurent, Anouchka P; Shao, Anqi; Alvarez-Torres, Maria Del Mar; Yu, Tianji; Su, Jiayu; Sagatelian, Romella; Ferrando, Adolfo A; Ciccia, Alberto; Lan, Yanyan; Owens, David M; Palomero, Teresa; Xing, Eric P; Rabadan, Raul
- **单位**：Columbia University（根据作者信息推断，原文未完整列出所有单位）
- **期刊/平台**：Nature
- **年份**：2025-01-09
- **论文类型**：研究论文（Research Article）
- **领域**：计算生物学 / 基因组学 / 转录调控
- **关键词**：foundation model, transcription, chromatin accessibility, gene expression, TF–TF interaction, interpretability
- **DOI/arXiv 号**：10.1038/s41586-024-08391-z
- **代码**：未提供（GET 模型可通过 Hugging Face 平台访问 demo，见 https://huggingface.co/spaces/get-foundation/getdemo）
- **数据**：213 种人类胎儿和成人细胞类型的 scATAC-seq 图谱（来自 refs. 1,2,22）；配对 scRNA-seq 数据（refs. 23,24）；lentiMPRA 数据（refs. 5,6）；GBM 肿瘤数据（ref. 26）
- **阅读日期**：2026-05-13（按当前日期填写）
- **在课题方向中的位置**：该文是「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法」方向的代表性工作。它构建了一个基于染色质可及性（chromatin accessibility）和 TF motif 的 foundation model（GET），通过自监督预训练学习跨细胞类型的转录调控语法，并用于预测基因表达、识别顺式调控元件（CREs）、推断 TF–TF 互作网络。与传统的基于序列的模型（如 Enformer、Basenji）不同，GET 以「peak × TF motif」矩阵为输入，强调 motif 组合与调控元件之间的互作，而非直接读取 DNA 序列。该文还结合 AlphaFold2/3 结构预测和分子动力学模拟，验证了 TF–TF 互作的物理基础，为「AI 预测 + 结构验证」的范式提供了范例。

## 02 一句话总结

GET 是一个以染色质可及性（peak × TF motif 矩阵）为输入的 interpretable foundation model，通过自监督掩码预训练学习跨 213 种人类细胞类型的转录调控语法，在未见细胞类型中达到实验级基因表达预测精度（Pearson r = 0.94），并可用于零样本预测 lentiMPRA 调控活性、识别远端 CREs、推断 TF–TF 互作网络，且通过 AlphaFold 和分子动力学模拟验证了预测的 TF–TF 物理互作。

## 03 研究问题

- **具体问题**：能否构建一个可泛化到未见细胞类型的转录调控模型，使其不仅能预测基因表达，还能解释调控机制（如识别远端增强子、推断 TF 协同/拮抗关系）？
- **为什么重要**：转录调控是理解发育、疾病和癌症的核心。现有模型（如 Enformer、Basenji）在训练细胞类型上表现良好，但泛化到新细胞类型时性能下降；且这些模型多为黑箱，难以提取可解释的调控规则（如 TF–TF 互作、远端调控）。
- **现有方法不足**：
  - Enformer/Basenji 需要大量配对的功能基因组数据（如 ChIP-seq、CAGE），且对未见细胞类型的泛化能力有限。
  - 传统 motif 扫描方法（如 HOMER）缺乏对远端调控和 TF 组合效应的建模。
  - 现有模型难以直接预测调控元件的功能活性（如 lentiMPRA 读出）。
- **精确的「Can ... ?」研究问题**：Can a foundation model pretrained on chromatin accessibility across diverse cell types achieve experimental-level gene expression prediction in unseen cell types, and can its interpretable components (motif importance, region importance) reveal novel TF–TF interactions and distal regulatory elements that are biologically validated?

## 04 背景与发展脉络

- **阶段一：基于序列的调控预测模型**（2015-2021）
  - 代表：DeepSEA（2015）、Basenji（2018）、Enformer（2021）
  - 优点：直接从 DNA 序列预测功能输出（如染色质状态、CAGE）
  - 局限：需要大量配对功能数据；对未见细胞类型泛化差；黑箱性质，难以提取调控规则
- **阶段二：基于染色质可及性的表达预测**（2018-2023）
  - 代表：Gene expression prediction from ATAC-seq（如用 peak 距离、motif 计数做线性/树模型）
  - 优点：染色质可及性本身包含细胞类型特异性调控信息
  - 局限：多为浅层模型，无法捕捉远端调控和 TF 组合效应
- **阶段三：Foundation models 在基因组学中的应用**（2022-2024）
  - 代表：Geneformer、scGPT、scFoundation（单细胞转录组）；DNABERT、Nucleotide Transformer（DNA 序列）
  - 优点：大规模预训练 + 微调范式，泛化能力强
  - 局限：多聚焦于转录组或序列本身，未直接建模「调控元件 × TF」的互作语法
- **本文主张的位置**：GET 是首个以「peak × TF motif」为 token 的 foundation model，通过自监督掩码预训练学习调控语法，将「染色质环境」与「序列 motif」结合，实现跨细胞类型泛化，并提供可解释的调控推断（motif importance、region importance、TF–TF causal network）。该文还首次将 foundation model 预测与 AlphaFold 结构验证结合，形成「AI 预测 → 结构验证 → 实验确认」的闭环。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有模型泛化性差 | Enformer 在未见细胞类型上预测精度低 | 模型在特定细胞类型上微调，过拟合训练数据；缺乏跨细胞类型的调控语法学习 | Results 图 2b、Extended Data 图 2c：GET 在未见细胞类型上优于 Enformer |
| 黑箱性质 | 无法解释哪些 TF 或调控元件驱动表达变化 | 基于序列的模型（如 Enformer）使用卷积/注意力直接处理序列，难以提取 motif 级别的归因 | Methods: 'Model interpretation' 节；Results 图 3b-c 展示 motif/region importance |
| 远端调控识别困难 | 传统方法（如 ABC）在远端增强子预测上精度低 | 仅依赖染色质可及性和 Hi-C 距离，缺乏对 TF 组合语法的建模 | Results 图 3d：GET 在远端（>100 kb）增强子预测上优于 ABC、Enformer、HyenaDNA |
| TF–TF 互作推断缺失 | 现有模型无法预测 TF 之间的协同/拮抗关系 | 缺乏跨细胞类型的共调控信息建模 | Results 图 4a-b：GET causal network 与 STRING 数据库比对，精度 25.2%（top 1%） |
| 计算成本高 | Enformer 推理需大量计算资源 | 基于序列的模型需处理长序列（100 kb 以上） | Supplementary Information: 'Computational cost comparison'：GET 可在一周内完成预训练，推理速度远快于 Enformer |

## 06 核心思想

1. **表面方法**：构建一个 Transformer 架构的 foundation model（GET），输入为「peak × TF motif」矩阵（200 个连续 peak，每个 peak 有 282 个 motif 簇的扫描得分 + 1 个可及性得分），通过自监督掩码预训练（随机掩码 50% 的 peak，预测其 motif 得分和可及性），然后在配对 scRNA-seq 数据上微调预测基因表达。

2. **核心洞察**：转录调控的「语法」可以从染色质可及性模式中学习，而不需要显式的 DNA 序列。通过将「peak」视为 token、「TF motif」视为特征，模型可以学习到：
   - 哪些 TF motif 组合倾向于共现（协同调控）
   - 哪些远端 peak 与启动子存在功能关联（增强子-启动子互作）
   - 这种语法在不同细胞类型间共享，因此可以泛化到未见细胞类型

3. **可能的普适教训** [Analysis]：
   - **特征选择比架构更重要**：GET 没有使用最先进的序列模型，而是将问题简化为「peak × motif」矩阵，这大大降低了计算复杂度，同时保留了关键的调控信息。这提示在蛋白质-DNA 互作建模中，选择合适的生物学先验（如 motif 扫描）可能比堆叠更深的网络更有效。
   - **自监督预训练 + 轻量微调是跨细胞类型泛化的关键**：掩码预测任务迫使模型学习调控元件的「上下文」关系，而非特定细胞类型的表达模式。
   - **可解释性设计应内置于架构**：通过 Jacobian 归因和 causal discovery，GET 天然支持 motif/region 级别的解释，而非事后分析。

## 07 方法总览

- **输入**：对于每个细胞类型，将基因组划分为 peak 集合（来自 scATAC-seq），每个 peak 用 282 个 TF motif 簇的扫描得分（min-max 归一化）+ 1 个可及性得分表示。输入样本为连续的 200 个 peak（约 2-4 Mb 基因组跨度）。
- **输出**：每个 peak 的基因表达预测值（log10(TPM+1)），或用于下游任务的嵌入表示。
- **模块**：
  1. **RegionEmb**：将每个 peak 的 283 维特征向量线性投影到 768 维嵌入空间。
  2. **Encoder**：12 层 Transformer encoder，使用 multi-head attention 捕捉 peak 之间的长程互作。
  3. **输出头**：线性层将嵌入映射到基因表达（正负链各一个输出）。
- **训练**：
  - **预训练**：自监督掩码预测。随机掩码 50% 的 peak，模型需预测被掩码 peak 的 motif 得分和可及性得分。损失为 Poisson negative log-likelihood。
  - **微调**：在配对 scATAC-seq + scRNA-seq 数据上，以基因表达为标签进行监督微调。
- **工具**：PyTorch；AdamW 优化器（weight decay 0.05）；预训练 800 epochs（16×V100，约 1 周）；微调 100 epochs（8×A100，约 1 天）。
- **反馈回路**：无显式反馈回路；但通过下游任务（lentiMPRA、CRISPRi、TF–TF 互作验证）的评估结果反馈模型改进方向。
- **假设**：
  - 染色质可及性模式足以表征调控元件的功能状态。
  - 跨细胞类型的调控语法是共享的（至少在胎儿和成人细胞类型中）。
  - 基因表达可由其启动子附近（±2 Mb）的调控元件状态近似预测。

**文字流程**：
1. 从 scATAC-seq 图谱中提取每个细胞类型的 peak 集合，扫描 282 个 TF motif 簇，得到 peak × motif 矩阵。
2. 将矩阵按 200 个连续 peak 分窗，输入 RegionEmb 得到嵌入。
3. 12 层 Transformer encoder 处理嵌入，捕捉 peak 间互作。
4. 预训练阶段：掩码 50% peak，预测被掩码 peak 的 motif 得分和可及性。
5. 微调阶段：在配对 RNA-seq 数据上，用线性头预测基因表达。
6. 下游应用：通过 Jacobian 归因计算 motif/region importance；通过 causal discovery（LiNGAM）构建 TF–TF 互作网络；通过 AlphaFold 验证互作结构。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| RegionEmb（peak 嵌入层） | 将 283 维 peak 特征（282 motif + 1 可及性）线性投影到 768 维 | 将稀疏的 motif 得分压缩为稠密表示，便于注意力机制处理 | 输入：200×283 矩阵；输出：200×768 嵌入 | Methods: 'Model architecture' 节 | 预期影响：模型无法有效区分不同 motif 组合，表达预测精度显著下降 [Analysis] |
| Encoder（12 层 Transformer） | 捕捉 peak 之间的长程互作（增强子-启动子、远端调控） | 转录调控涉及远端元件（>1 Mb），需要注意力机制建模长程依赖 | 输入：200×768 嵌入；输出：200×768 上下文嵌入 | Methods: 'Model architecture' 节；Results 图 3c：GET 识别 >1 Mb 远端调控 | 预期影响：模型退化为仅基于局部 peak 的预测，无法识别远端增强子 [Analysis] |
| 掩码预训练头 | 预测被掩码 peak 的 motif 得分和可及性 | 自监督学习调控语法，无需标签数据 | 输入：掩码后的嵌入；输出：被掩码 peak 的 283 维预测 | Methods: 'Training scheme' 节；Extended Data 图 2d：预训练对最终性能至关重要 | 预期影响：模型仅能记忆训练细胞类型，无法泛化到未见细胞类型（Extended Data 图 2d 显示无预训练时 r 从 0.94 降至 0.6） |
| 表达预测头（微调） | 将 peak 嵌入映射到基因表达值 | 将调控语法转化为可验证的表达预测 | 输入：200×768 上下文嵌入；输出：2 维（正负链）表达值 | Results 图 1c：未见细胞类型 r = 0.94 | 预期影响：模型无法进行定量预测，仅能定性分类 [Analysis] |
| Jacobian 归因 | 计算每个 motif/region 对表达预测的梯度贡献 | 提供可解释的调控元件重要性 | 输入：模型和特定输入；输出：motif importance 向量、region importance 向量 | Methods: 'Model interpretation' 节；Results 图 3b-c | 预期影响：无法解释模型决策，失去生物学可解释性 [Analysis] |
| Causal discovery（LiNGAM） | 从 motif importance 矩阵推断 TF–TF 因果互作 | 识别协同/拮抗 TF 对，构建调控网络 | 输入：gene-by-motif 矩阵；输出：有向因果图 | Methods: 'Causal discovery of regulator interaction' 节；Results 图 4a-b | 预期影响：仅能获得相关性而非因果性，无法区分直接与间接互作 [Analysis] |
| AlphaFold2/3 结构预测 | 预测 TF–TF 互作的三维结构 | 验证预测的互作是否具有物理基础 | 输入：TF 蛋白序列；输出：多聚体结构模型 | Results 图 5c、Extended Data 图 8-9 | 预期影响：无法区分真实互作与假阳性预测 [Analysis] |

## 09 关键公式符号

1. **可及性得分**：
   $$s_i = \log_{10}\left(\frac{c_i}{t} + 1\right), \quad t = \sum_i c_i$$
   - $s_i$：peak $i$ 的可及性得分
   - $c_i$：peak $i$ 中的片段数
   - $t$：该细胞类型总片段数

2. **注意力头输出**：
   $$O_h = \text{softmax}\left(\frac{X'W_q(X'W_k)^T}{\sqrt{d_k}}\right)(X'W_v)$$
   - $O_h$：第 $h$ 个注意力头的输出
   - $X'$：输入嵌入（经 RegionEmb 后）
   - $W_q, W_k \in \mathbb{R}^{(n \times D) \times d_k}$：query 和 key 的线性变换
   - $W_v \in \mathbb{R}^{(n \times D) \times d_v}$：value 的线性变换
   - $d_k$：key 的维度

3. **Transformer 层输出**：
   $$z'_l = \text{MHA}(\text{LN}(z_{l-1})) + z_{l-1}; \quad z_l = \text{FFN}(\text{LN}(z'_l)) + z'_l$$
   - $z_l$：第 $l$ 层的输出
   - MHA：multi-head attention
   - LN：layer normalization
   - FFN：feed-forward network（两层线性 + GELU 激活）

4. **预训练损失**：
   $$\mathcal{L} = \mathbb{E}\left(\sum_{i \in M} -\log p(x_i | X^{\text{masked}})\right)$$
   - $M$：被掩码的 peak 集合
   - $x_i$：被掩码 peak $i$ 的原始特征
   - $X^{\text{masked}}$：掩码后的输入

5. **Jacobian 归因**：
   $$v_g = \sum_{i=1}^{r} (\nabla g \odot X)[i, :]$$
   - $v_g$：基因 $g$ 的 motif importance 向量
   - $\nabla g = J_X[r//2, s]$：基因 $g$ 对应输出对输入的梯度
   - $J_X = \frac{\partial E}{\partial X}$：输出对输入的 Jacobian 矩阵
   - $\odot$：Hadamard 乘积

## 10 实验设计与证据链

- **数据集**：
  - 预训练：213 种人类胎儿和成人细胞类型的 scATAC-seq 图谱（refs. 1,2,22），共 1.3M peaks，约 1.3M 单细胞核。
  - 微调：153 种细胞类型的配对 scRNA-seq 数据（refs. 23,24）。
  - 下游验证：lentiMPRA（K562，226,243 个序列）、CRISPRi（K562，ENCODE）、HiChIP（HUDEP-2）、AlphaFold 结构预测、分子动力学模拟。
- **指标**：Pearson 相关系数、Spearman 相关系数、R²、AUPRC（增强子-启动子预测）、精度（TF–TF 互作验证）。
- **基线**：Enformer、Basenji、基因可及性得分（gene activity score）、top correlated cell type expression、mean expression across training cell types。
- **评测协议**：
  - 留一细胞类型验证：在 153 种细胞类型中，每次留出一种细胞类型进行微调评估。
  - 留一染色体验证：在 K562 中，每次留出一条染色体进行微调评估。
  - 零样本 lentiMPRA：使用 K562 微调模型，不接触 lentiMPRA 数据，预测 226,243 个序列的调控活性。
  - TF–TF 互作验证：将 GET 预测的 motif–motif 互作与 STRING 数据库、AlphaFold 结构预测、共免疫沉淀实验比对。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 留一细胞类型表达预测 | GET 可泛化到未见细胞类型 | 留出 astrocyte，比较 GET vs Enformer vs gene activity score | GET Pearson r = 0.94（R² = 0.88），Enformer r = 0.83，gene activity r = 0.51 | GET 在未见细胞类型上达到实验级精度 | 未比较所有 153 种细胞类型的平均性能 | Results 图 1c、Extended Data 图 2a |
| 预训练消融 | 自监督预训练对泛化至关重要 | 仅微调（无预训练） vs 预训练+微调 | 无预训练时 r 降至 0.6 | 预训练是跨细胞类型泛化的关键 | 未测试不同预训练数据规模的影响 | Extended Data 图 2d |
| 零样本 lentiMPRA 预测 | GET 可预测调控元件活性 | GET vs Enformer，K562 中 226,243 个序列 | GET Pearson r = 0.55（结合可及性），Enformer r = 0.44 | GET 在零样本设置下优于 Enformer | 仅测试了 K562 一个细胞系 | Results 图 2b、Extended Data 图 5a |
| 远端增强子识别（胎儿红母细胞） | GET 可识别 >1 Mb 的远端调控 | GET vs Enformer vs ABC vs HyenaDNA vs DeepSEA，HbF 相关位点 | GET 在远端（>100 kb）增强子预测上 AUPRC 最高 | GET 对长程调控有更好的建模能力 | 仅测试了 4 个 HbF 相关位点 | Results 图 3c-d、Extended Data 图 6a-c |
| TF–TF 互作网络与 STRING 比对 | GET 预测的 TF–TF 互作具有生物学意义 | GET causal vs GET correlation vs 随机，top 1% 互作对 | GET causal 精度 25.2%，correlation 15.9%，随机 5.6% | Causal discovery 优于简单相关性 | 未与全部已知 TF–TF 互作数据库比对 | Results 图 4b |
| AlphaFold 验证 TFAP2A–ZFX 互作 | GET 预测的互作具有结构基础 | AlphaFold2 预测 TFAP2A–ZFX 多聚体结构 | ZFX IDR 折叠并与 TFAP2A 结构域形成静电互作 | 预测的互作具有物理基础 | 仅验证了 2 对 TF 互作 | Extended Data 图 8c-e |
| 共免疫沉淀验证 TFAP2A–ZFX | GET 预测的互作在体内存在 | 抗 TFAP2A 抗体 pull-down，检测 ZFX | ZFX 被 pull-down，阴性对照 SRF 无互作 | TFAP2A–ZFX 互作在体内存在 | 未在多种细胞类型中验证 | Extended Data 图 8g、图 9e |
| PAX5 G183S 突变对互作的影响 | GET 可解释疾病相关突变的功能 | AlphaFold3 预测 PAX5 WT vs G183S 与 NR2C2 互作 | G183S 增强 PAX5–NR2C2 互作 | 突变可能通过改变 TF–TF 互作影响疾病风险 | 未进行功能实验验证突变效应 | Results 图 5c-e、Extended Data 图 10-11 |

## 11 结论正确解读

- **任务范围**：GET 预测的是「基因表达水平」（log10 TPM），基于染色质可及性和 motif 信息，而非直接预测 TF 结合位点或 TF–DNA 亲和力。其输出是基因水平的表达值，而非蛋白质-DNA 互作的物理参数。
- **oracle/真值输入**：在 lentiMPRA 预测中，模型使用了 K562 的染色质可及性数据作为输入，但未使用 lentiMPRA 实验数据（零样本）。在 TF–TF 互作验证中，使用了 STRING 数据库作为真值标签。
- **端到端状态**：GET 是一个端到端的表达预测模型，但其「调控语法」的提取（motif importance、region importance）是通过事后归因分析实现的，而非模型直接输出。TF–TF 互作网络也是通过因果发现算法从归因矩阵中推断的，并非模型直接预测。
- **算力成本**：预训练约 1 周（16×V100），微调约 1 天（8×A100）。推理速度较快（单细胞类型几分钟）。相比 Enformer 需数天推理，GET 计算成本显著降低。
- **历史数据依赖**：模型依赖 scATAC-seq 和 scRNA-seq 数据的质量与细胞类型注释准确性。预训练数据仅包含正常组织，未包含疾病状态。
- **模型依赖**：结果依赖于 282 个 motif 簇的定义（来自 Vierstra et al. 13）和 peak 集合的构建方式。不同 motif 扫描工具或 peak calling 方法可能影响结果。
- **最难情形**：模型在以下情形表现受限：(1) 与训练数据细胞类型差异极大的新型细胞类型；(2) 需要区分 motif 高度相似的 TF 同源物（模型分辨率有限）；(3) 涉及三维基因组结构（如环状互作）的调控。
- **群体/领域边界**：模型基于人类细胞类型训练，未验证在其他物种（如小鼠）中的适用性。胎儿和成人细胞类型覆盖广泛，但未包含所有组织。
- **不确定性**：预测的 TF–TF 互作网络仅与 STRING 数据库比对，未进行大规模实验验证。AlphaFold 结构预测的置信度未系统评估。

**有边界的复述**：GET 是一个基于染色质可及性和 TF motif 的 foundation model，能够在未见的人类细胞类型中达到实验级基因表达预测精度（r = 0.94），并可用于零样本预测调控元件活性、识别远端增强子、推断 TF–TF 互作网络。其预测的 TFAP2A–ZFX 和 PAX5–NR2C2 互作得到了实验验证。然而，模型仅基于人类正常组织数据训练，对疾病状态、非人类物种和 motif 相似 TF 的区分能力有限。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 依赖染色质可及性数据 | 模型主要依赖 scATAC-seq 数据，未整合其他调控信息（如组蛋白修饰、三维基因组） | 整合多组学数据（如 ATAC + RNA + 蛋白质） | Discussion 节 |
| 分辨率有限 | 无法区分 motif 高度相似的 TF 同源物 | 引入核苷酸级别的 TF footprint 数据 | Discussion 节 |
| 粗粒度细胞状态 | 训练使用粗粒度的细胞类型注释，未考虑细胞状态连续体 | 整合单细胞嵌入（如 scGPT、Geneformer） | Discussion 节 |
| 缺乏时间动态 | 模型是静态的，未建模转录调控的时间动态 | 引入时间序列数据 | Discussion 节 |
| 疾病状态覆盖不足 | 预训练数据仅包含正常组织，未包含疾病、扰动或治疗状态 | 纳入更多疾病和扰动数据 | Discussion 节 |
| 非编码变异预测有限 | 模型未直接预测非编码变异的效应 | 整合 multiplex 核苷酸水平扰动数据 | Discussion 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 输入特征仅含 motif 得分和可及性，不含序列信息 | 模型可能无法捕捉非 motif 依赖的调控机制（如 DNA 甲基化、组蛋白修饰） | 限制了模型的生物学适用范围 | 在输入中加入 DNA 序列嵌入或组蛋白修饰数据，比较性能变化 | Methods: 'Input data' 节 |
| 282 个 motif 簇的划分基于序列相似性，可能掩盖功能差异 | 同一簇内不同 TF 可能具有不同的功能（如激活 vs 抑制） | 影响 TF–TF 互作推断的准确性 | 使用更细粒度的 motif 表示（如单个 TF 的 motif）重新训练 | Methods: 'Motif features' 节 |
| 留一细胞类型验证仅展示了 astrocyte 结果 | 未报告所有 153 种细胞类型的平均性能，可能存在选择性报告 | 无法评估模型的平均泛化能力 | 要求作者提供所有细胞类型的性能分布 | Results 图 1c |
| lentiMPRA 预测中，模型使用了 K562 可及性数据 | 模型可能依赖可及性信号而非 motif 语法进行预测 | 削弱了「零样本」声明的说服力 | 在无可及性数据的情况下（仅序列）测试模型性能 | Methods: 'LentiMPRA zero-shot prediction' 节 |
| TF–TF 互作网络仅与 STRING 数据库比对 | STRING 数据库本身不完整，且包含非直接互作 | 可能高估了互作预测的精度 | 使用独立的实验数据（如 CoIP、Y2H）进行验证 | Results 图 4b |
| AlphaFold 结构预测仅验证了少数 TF 对 | 未系统评估所有预测互作的结构基础 | 无法确定结构验证的普适性 | 对 top 100 互作对进行 AlphaFold 预测 | Extended Data 图 8-9 |
| 分子动力学模拟仅 100 ns | 100 ns 可能不足以捕捉 IDP 的构象变化 | 对 IDP 折叠的结论可能不稳健 | 延长模拟时间或使用增强采样方法 | Methods: 'Molecular dynamics simulation' 节 |
| 模型未与最新的序列 foundation model（如 Nucleotide Transformer）比较 | 可能高估了 GET 的优越性 | 无法确定「peak × motif」表示是否优于直接序列建模 | 在相同任务上比较 GET 与 Nucleotide Transformer | Results 图 2b |

## 14 学到什么

**Agent 提炼的知识候选**

1. **「peak × motif」矩阵作为调控建模的紧凑表示**：GET 的成功表明，将基因组简化为「可及性 × motif 得分」矩阵可以捕捉大部分调控信息，且计算效率远高于直接序列建模。对于 TF–DNA 互作研究，可考虑将 ChIP-seq 或 ATAC-seq 数据转化为类似的矩阵表示，作为模型的输入特征。

2. **自监督掩码预训练学习调控语法**：通过掩码预测任务（预测被掩码 peak 的 motif 得分），模型被迫学习 peak 之间的上下文关系，而非简单的局部特征。这一策略可迁移到 TF–DNA 互作预测：例如，掩码一个 TF 的结合位点，预测其是否被其他 TF 协同招募。

3. **Jacobian 归因作为可解释性工具**：通过计算输出对输入的梯度，GET 能够识别对基因表达最重要的 motif 和 peak。这一方法可迁移到 TF–DNA 互作模型，用于识别关键 TF 结合位点和远端调控元件。

4. **Causal discovery（LiNGAM）从归因矩阵推断 TF–TF 互作**：GET 使用 LiNGAM 从 gene-by-motif 矩阵中推断 motif–motif 因果关系，而非简单相关性。这一方法可迁移到 TF–TF 互作网络推断，特别是当有多个细胞类型的调控数据时。

5. **AlphaFold 验证 AI 预测的互作**：GET 将预测的 TF–TF 互作与 AlphaFold 结构预测结合，形成「AI 预测 → 结构验证」的闭环。对于 TF–DNA 互作研究，可考虑用 AlphaFold 或 RoseTTAFold 验证预测的 TF–TF 或 TF-DNA 复合物结构。

6. **零样本预测的评估框架**：GET 在 lentiMPRA 上的零样本预测提供了一个评估框架：模型在训练时未接触实验数据，但能预测调控元件的功能活性。这一框架可迁移到 TF–DNA 互作预测，例如预测未测序细胞类型中的 TF 结合位点。

7. **可迁移的模型架构**：GET 的「嵌入层 + Transformer encoder + 线性输出头」架构可迁移到其他调控预测任务，如预测 TF 结合位点、增强子活性、染色质状态等。关键在于选择合适的「token」表示（如 peak、motif、基因）。

8. **跨细胞类型泛化的训练策略**：GET 通过大规模多细胞类型预训练 + 轻量微调实现跨细胞类型泛化。这一策略可迁移到 TF–DNA 互作模型，特别是在数据稀缺的细胞类型中。

## 15 与已有知识连接

- **Enformer (Avsec et al., 2021)**：GET 与 Enformer 目标相似（预测基因表达），但输入表示不同（Enformer 用 DNA 序列，GET 用 peak × motif 矩阵）。GET 在未见细胞类型上表现更好，且计算成本更低。可连接点：将 Enformer 的序列嵌入与 GET 的 motif 特征结合，可能进一步提升预测精度。
- **Basenji (Kelley et al., 2018)**：Basenji 是 Enformer 的前身，同样基于序列预测功能基因组数据。GET 的「peak × motif」表示可视为对 Basenji 序列输入的降维简化。
- **AlphaFold2/3 (Jumper et al., 2021; Abramson et al., 2024)**：GET 使用 AlphaFold 验证 TF–TF 互作，这是 AI 预测与结构生物学结合的代表。可连接：AlphaFold 的 TF 结构预测可用于筛选 GET 预测的互作对。
- **scGPT / Geneformer (Cui et al., 2024; Theodoris et al., 2023)**：单细胞 foundation models，聚焦于转录组而非染色质。GET 与这些模型互补：GET 提供调控层面的解释，而 scGPT/Geneformer 提供细胞状态层面的信息。
- **Vierstra et al. (2020) motif 聚类**：GET 使用的 282 个 motif 簇来自 Vierstra 的聚类，该聚类基于 TF 结合位点序列相似性。可连接：更精细的 motif 表示（如考虑 TF 家族）可能提升 GET 的解析度。
- **LiNGAM (Shimizu et al., 2006)**：因果发现算法，GET 用于推断 motif–motif 因果关系。可连接：其他因果发现方法（如 PC、FCI）可能提供互补的互作网络。
- **lentiMPRA (Inoue et al., 2019)**：大规模平行报告基因分析，GET 的零样本预测为该实验设计提供计算筛选工具。
- **STRING 数据库 (Szklarczyk et al., 2021)**：蛋白质-蛋白质互作数据库，GET 的 TF–TF 互作预测与其比对验证。

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：TF–DNA 结合特异性的多模态 foundation model
   - **来源局限/观察**：GET 使用 motif 得分作为 TF 结合的代理，但 motif 得分无法区分同一 TF 在不同染色质环境下的结合差异（如先锋因子 vs 沉降因子）。
   - **核心假设**：将 DNA 序列嵌入（如 Enformer 的序列表示）与染色质可及性、TF motif 得分结合，可以更准确地预测 TF 结合位点。
   - **初步方法**：构建一个双编码器模型，一个编码器处理 DNA 序列（如 Nucleotide Transformer），另一个处理 peak × motif 矩阵（类似 GET），通过交叉注意力融合两种表示，预测 TF 结合。
   - **验证方式**：使用 ChIP-seq 数据（如 ENCODE）评估 TF 结合预测的 AUPRC，与 GET、Enformer、传统 motif 扫描方法比较。
   - **创新状态**：unverified

2. **候选名称**：基于 GET 的 TF–TF 协同/拮抗互作的结构验证管道
   - **来源局限/观察**：GET 通过 causal discovery 预测 TF–TF 互作，但仅与 STRING 数据库比对，未进行系统结构验证。
   - **核心假设**：GET 预测的高置信度 TF–TF 互作对中，有显著比例具有物理结合结构。
   - **初步方法**：从 GET causal network 中选取 top 1% 互作对，用 AlphaFold3 预测异二聚体结构，用 pDockQ 和 ipTM 筛选高置信度互作；对筛选出的互作对进行分子动力学模拟验证稳定性。
   - **验证方式**：与已知 TF 二聚体结构（如 PDB）比对，计算预测结构的 RMSD；对未知互作对进行 CoIP 实验验证。
   - **创新状态**：unverified

3. **候选名称**：单细胞分辨率的 TF 调控语法解析
   - **来源局限/观察**：GET 使用 pseudobulk 数据，丢失了单细胞水平的调控异质性。
   - **核心假设**：在单细胞水平应用 GET 的架构，可以解析细胞状态转变过程中的 TF 调控逻辑。
   - **初步方法**：将 GET 的输入从 pseudobulk 改为单细胞 ATAC-seq 数据，使用单细胞 RNA-seq 作为表达标签，训练单细胞版本的 GET。
   - **验证方式**：在分化时间序列数据（如造血分化）中，比较单细胞 GET 与 pseudobulk GET 的调控推断差异。
   - **创新状态**：unverified

4. **候选名称**：TF 结合 motif 的上下文依赖建模
   - **来源局限/观察**：GET 的 motif 得分是静态的，未考虑 motif 在不同染色质环境下的可及性差异。
   - **核心假设**：TF 的调控功能取决于其结合位点的染色质上下文（如增强子 vs 启动子、活跃 vs 抑制状态）。
   - **初步方法**：在 GET 的输入中加入染色质状态注释（如 ChromHMM 状态），或在注意力机制中引入染色质状态作为偏置项。
   - **验证方式**：比较加入染色质状态前后，TF–TF 互作预测的精度变化。
   - **创新状态**：unverified

5. **候选名称**：从 GET 到 TF–DNA 结合自由能预测
   - **来源局限/观察**：GET 预测基因表达，但未直接预测 TF–DNA 结合的物理化学性质（如结合自由能、解离常数）。
   - **核心假设**：GET 学习到的调控语法可以迁移到 TF–DNA 结合亲和力预测任务。
   - **初步方法**：将 GET 的嵌入层和 encoder 作为预训练模型，在 TF–DNA 结合亲和力数据集（如 SELEX、HT-SELEX）上微调，预测结合强度。
   - **验证方式**：与传统的基于 motif 的亲和力预测方法（如 PWM、DeepBind）比较。
   - **创新状态**：unverified

6. **候选名称**：跨物种 TF 调控语法迁移
   - **来源局限/观察**：GET 仅基于人类数据训练，未验证在其他物种中的适用性。
   - **核心假设**：TF 调控语法在哺乳动物中高度保守，GET 可迁移到小鼠等模式生物。
   - **初步方法**：将 GET 的输入特征（peak × motif）应用于小鼠 scATAC-seq 数据，使用人类训练的模型进行零样本预测，评估性能。
   - **验证方式**：与小鼠 ENCODE 数据比较，评估跨物种预测精度。
   - **创新状态**：unverified