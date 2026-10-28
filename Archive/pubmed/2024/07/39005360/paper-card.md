## 01 基本信息
- **标题**：GET: a foundation model of transcription across human cell types
- **作者**：Fu, Xi; Mo, Shentong; Buendia, Alejandro; Laurent, Anouchka; Shao, Anqi; Del Mar Alvarez-Torres, Maria; Yu, Tianji; Tan, Jimin; Su, Jiayu; Sagatelian, Romella; Ferrando, Adolfo A; Ciccia, Alberto; Lan, Yanyan; Owens, David M; Palomero, Teresa; Xing, Eric P; Rabadan, Raul
- **单位**：Columbia University（作者单位未在摘要中逐一列出，部分作者隶属 Columbia University Irving Medical Center 等，具体以原文为准）
- **期刊/平台**：bioRxiv (preprint server for biology)
- **年份**：2024（预印本发布于 2023-09-24，2024-07-15 更新）
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：计算生物学 / 转录调控 / 基础模型
- **关键词**：foundation model, transcription regulation, chromatin accessibility, gene expression prediction, TF-TF interaction, AlphaFold
- **DOI/arXiv 号**：10.1101/2023.09.24.559168
- **代码**：未提供（GET 网站：https://huggingface.co/spaces/get-foundation/GET）
- **数据**：213 种人类细胞类型 scATAC-seq；B-ALL 患者 RNA-seq（SRA PRJNA534488）；TF-TF 互作数据来自 Göös et al. 2022；预计算结果在 AWS S3 bucket
- **阅读日期**：2025-06-15（示例）
- **在课题方向中的位置**：该文是「TF–DNA 结合机制 × AI 基础模型」方向的代表性工作。它不直接预测 TF–DNA 三维结构，而是通过大规模序列 + 染色质可及性数据学习调控语法，输出可解释的 motif 贡献分数，并进一步结合 AlphaFold 2 预测 TF–TF 互作结构。对课题的启示在于：将序列 motif 结合分数作为输入特征、以自监督预训练 + 微调范式实现跨细胞类型泛化、以及用因果发现（LiNGAM）从表达数据推断 TF–TF 调控关系。

## 02 一句话总结
GET 仅以序列 motif 结合分数和染色质可及性为输入，通过自监督预训练 + 微调的基础模型架构，在 213 种人类细胞类型上实现了对未见细胞类型基因表达的实验级精度预测，并进一步通过因果发现和 AlphaFold 2 推断 TF–TF 互作及结构。

## 03 研究问题
- **具体问题**：能否构建一个可泛化到未见细胞类型/条件的转录调控计算模型，使其预测精度达到实验重复水平，并从中提取可解释的调控规则（如 TF–TF 互作）？
- **为什么重要**：转录调控是几乎所有生物过程的核心，但现有计算模型（如 Enformer）受限于训练细胞类型，无法外推到新细胞类型；且缺乏可解释性，难以直接用于发现调控元件和互作网络。
- **现有方法不足**：Enformer 等模型仅在固定细胞类型上训练，预测未见细胞类型时性能下降；传统 peak-to-gene 方法依赖线性相关性，受数据稀疏性影响，且只能覆盖数千个基因。
- **精确研究问题**：Can a foundation model pretrained on chromatin accessibility across 213 cell types, with only sequence motif scores and accessibility as input, achieve experimental-level accuracy in predicting gene expression in unseen cell types, and enable inference of regulatory elements and TF–TF interactions?

## 04 背景与发展脉络
（标注：以下脉络为「经外部核验」的领域常识 + 本文框架）
1. **早期序列模型**：DeepSEA (2015)、Basenji (2018) 等以序列为输入预测染色质特征，但缺乏跨细胞类型泛化。
2. **大窗口模型**：Enformer (2021) 以 200kb 窗口预测多组织表达/染色质，但仅在训练组织上有效，未见细胞类型外推能力有限。
3. **单细胞时代模型**：scATAC/scRNA 数据激增，但多数模型（如 gene activity score）仅做简单相关性，未利用序列信息。
4. **基础模型范式**：DNABERT、Nucleotide Transformer 等以序列预训练，但未结合染色质可及性，且窗口有限。
5. **本文位置**：GET 首次将「跨 213 细胞类型的染色质可及性」作为自监督预训练信号，以 motif 结合分数为输入特征，实现跨细胞类型泛化，并引入因果发现（LiNGAM）和 AlphaFold 2 进行 TF–TF 互作推断，填补了「可解释基础模型 + 结构预测」的空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 跨细胞类型泛化差 | Enformer 在未见细胞类型上预测精度低 | 模型仅在固定训练细胞类型上优化，未学习跨细胞类型共享的调控规则 | Results 图 1c, Supplementary Figure 2c |
| 数据稀疏性 | 单细胞数据中 peak-to-gene 相关性不可靠 | 单细胞数据稀疏，线性相关性受噪声影响 | Results 图 3c–d 讨论 |
| 可解释性不足 | 现有模型输出黑盒预测，无法定位调控元件 | 缺乏对输入特征的归因机制 | Methods: Model interpretation |
| 长距离调控检测难 | 远端增强子-启动子互作难以从序列直接预测 | 序列窗口有限，且缺乏细胞类型特异性可及性信息 | Results 图 3a–b（>1Mbp 调控区） |
| TF–TF 互作推断困难 | 现有方法依赖 ChIP-seq 共定位，覆盖有限 | ChIP-seq 抗体可用性有限，且无法区分直接/间接互作 | Results 图 4f–h, Supplementary Figure 6 |

## 06 核心思想
1. **表面方法**：以「序列 motif 结合分数 + 染色质可及性」为输入，构建 embedding + attention 架构，先自监督预训练（mask 随机区域预测 motif 分数和可及性），再微调预测基因表达。
2. **核心洞察**：调控元件的「可及性」和「motif 结合潜力」是跨细胞类型共享的底层特征；通过大规模跨细胞类型预训练，模型学会了通用的调控语法，从而能外推到未见细胞类型。
3. **可能的普适教训** [Analysis]：将「物理可解释的特征」（如 motif 结合分数）而非原始序列作为输入，可显著提升模型的可解释性和跨条件泛化能力；自监督预训练 + 微调范式适用于数据稀疏但特征可定义的生物问题。

## 07 方法总览
- **输入**：每个基因的启动子区域及其关联的远端调控元件（基于 ATAC-seq peak），每个区域提取 motif 结合分数（基于已知 PWM）和可及性分数。
- **输出**：基因表达预测值（微调阶段）；motif 贡献分数、区域贡献分数（解释阶段）；TF–TF 因果网络（后处理阶段）。
- **模块**：
  1. 特征编码器：将 motif 分数和可及性映射为 embedding；
  2. Attention 编码器：跨区域整合上下文信息；
  3. 预训练头：预测 masked 区域的 motif 分数和可及性；
  4. 微调头：预测基因表达；
  5. 解释模块：计算区域/motif 贡献分数；
  6. 因果发现模块：基于 motif 贡献矩阵运行 LiNGAM。
- **训练**：两阶段——自监督预训练（mask 预测）→ 监督微调（表达预测）。
- **反馈回路**：无显式闭环；但解释模块的输出可反馈用于迭代特征工程。
- **文字流程**：输入基因的启动子 + 远端 peak 区域 → 提取 motif 分数和可及性 → embedding → attention 编码 → 预训练（mask 预测）→ 微调（表达预测）→ 解释（贡献分数）→ 因果发现（TF–TF 网络）→ 结构预测（AlphaFold 2）。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Motif 特征提取 | 将序列转换为 motif 结合分数 | 提供可解释的 TF 结合潜力特征 | 输入：DNA 序列；输出：motif × 区域分数矩阵 | Methods: Motif features | 预期：模型失去 TF 特异性信息，可解释性大幅下降 [预期效应] |
| 可及性特征 | 提供细胞类型特异性染色质状态 | 区分不同细胞类型的调控状态 | 输入：ATAC-seq peak；输出：可及性分数 | Methods: ATAC-seq data processing | 预期：跨细胞类型泛化能力显著下降 [预期效应] |
| Embedding + Attention 编码器 | 整合局部和远端调控信息 | 捕获长距离调控互作 | 输入：特征矩阵；输出：上下文 embedding | Methods: Model architecture | 预期：无法建模远端增强子-启动子互作 [预期效应] |
| 自监督预训练 | 学习跨细胞类型共享的调控语法 | 提升未见细胞类型泛化 | 输入：masked 特征矩阵；输出：重建的 motif/可及性 | Results 图 1c, Supplementary Figure 2d | 实测：随机初始化微调性能显著下降（Pearson r: 0.596 vs 预训练） |
| 表达微调头 | 将调控 embedding 映射为表达值 | 实现定量表达预测 | 输入：embedding；输出：表达值 | Results 图 1c–d | 预期：模型退化为纯相关性模型 [预期效应] |
| 贡献分数解释 | 计算区域/motif 对表达的贡献 | 定位关键调控元件 | 输入：模型梯度/注意力；输出：贡献分数 | Results 图 3a–e | 预期：无法进行调控元件发现 [预期效应] |
| LiNGAM 因果发现 | 从 motif 贡献矩阵推断 TF–TF 因果网络 | 识别功能互作而非共定位 | 输入：基因 × motif 贡献矩阵；输出：有向图 | Results 图 4f–h | 预期：仅剩相关性网络，精度下降（25.2% → 15.9% 相关方法） |
| AlphaFold 2 结构预测 | 预测 TF–TF 互作的三维结构 | 验证因果互作并揭示结构基础 | 输入：TF 序列；输出：多聚体结构 | Results 图 5a–k | 预期：无法区分直接/间接互作 [预期效应] |

## 09 关键公式符号
- **Motif 结合分数**：对每个区域 r 和 motif m，计算 \( S_{r,m} = \sum_{k} \max_{p} \text{PWM}_m(p, k) \)，其中 p 为位置，k 为碱基。用途：量化区域中 motif 的结合潜力。来源：Methods: Motif features。
- **可及性分数**：\( A_r = \text{normalized ATAC-seq count in region } r \)。用途：表征区域在特定细胞类型中的开放状态。来源：Methods: ATAC-seq data processing。
- **预训练目标**：\( \mathcal{L}_{\text{pretrain}} = \mathbb{E}[\text{MSE}(S_{r,m}, \hat{S}_{r,m}) + \lambda \cdot \text{BCE}(A_r, \hat{A}_r)] \)，其中 \(\hat{S}\) 和 \(\hat{A}\) 为模型预测。用途：自监督学习调控特征。来源：Methods: Model architecture。
- **微调目标**：\( \mathcal{L}_{\text{finetune}} = \text{Poisson loss}(E_g, \hat{E}_g) \)，其中 \(E_g\) 为基因 g 的表达。用途：定量表达预测。来源：Methods: Finetuning。
- **LiNGAM 模型**：\( x_i = \sum_{j \neq i} b_{ij} x_j + e_i \)，其中 \(x_i\) 为 motif 贡献，\(e_i\) 为非高斯噪声。用途：推断 TF–TF 因果方向。来源：Methods: Causal discovery of regulator interaction。

## 10 实验设计与证据链
- **数据集**：
  - 预训练：213 种人类细胞类型 scATAC-seq（胎儿 + 成人），peak 区域 + motif 分数。
  - 微调：153 种细胞类型配对表达数据（多组学或独立 scRNA-seq）。
  - 验证：胎儿星形胶质细胞、胎儿成红细胞（leave-one-cell-type-out）；B 细胞（TF–TF 互作）；K562（CRISPRi 基准）。
  - 外部数据：lentiMPRA（K562，>200,000 序列）；ENCODE CRISPRi（K562）；B-ALL 患者 RNA-seq（141 例散发性 + 4 例家族性）。
- **指标**：Pearson 相关系数（表达预测）；AUROC/AUPR（调控元件识别）；精度（TF–TF 互作）；R²（表达预测）。
- **基线**：TSS 可及性、基因活性分数、Enformer（线性探针）、DeepSEA、HyenaDNA、ABC 模型。
- **预算/资源**：未提供具体 GPU 时数；计算成本对比显示 GET 可在 3 天内筛选 200,000 个 lentiMPRA 元件，而 Enformer 仅能处理 2,000 个。
- **评测协议**：leave-one-cell-type-out 交叉验证；leave-one-chromosome-out 微调；leave-out-motif 训练。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|--------------|-------------------|------|
| 未见细胞类型表达预测 | GET 可预测未见细胞类型表达 | 留一细胞类型；对比 TSS 可及性、基因活性分数、Enformer | 星形胶质细胞 Pearson r=0.94 (R²=0.88)；优于所有基线 | GET 达到实验重复精度 | 未在全部 213 种细胞类型上验证 | Results 图 1c–d |
| 胎儿 vs 成人泛化 | 胎儿训练可预测成人 | 胎儿数据训练，成人细胞类型测试 | 平均 R²=0.53，优于基线 (R²=0.33) | 跨发育阶段泛化 | 部分细胞类型（低细胞数）失败 | Results 图 1e |
| lentiMPRA 预测 | GET 可零样本预测调控活性 | K562 lentiMPRA；对比 Enformer | Pearson r=0.56 vs 0.44 | GET 优于 Enformer | Enformer 在 peak 活性预测上更优 | Results 图 2g |
| 胎儿血红蛋白调控元件 | GET 可识别远端调控元件 | 4 个已知位点；对比 Enformer、DeepSEA、ABC | GET 在长距离互作检测上最优 | GET 捕获长距离调控 | 未检测所有潜在元件 | Results 图 3a–d |
| TF–TF 互作精度 | GET 因果发现优于相关性 | 对比 STRING 数据库；随机基线精度 5.6% | GET 精度 25.2%（top 1%），优于相关性 15.9% | 因果方法有效 | 精度仍低于 MS 实验（30.4%） | Results 图 4h |
| PAX5 G183S 功能 | GET 可解释致病突变 | B-ALL 患者数据；对比 PAX5 功能缺失 | G183S 增强 PAX5-NR2C2 互作 | GET 提供机制假说 | 未做功能实验验证 | Results 图 6a–g |

## 11 结论正确解读
- **任务范围**：GET 预测的是「基因表达」而非直接的 TF–DNA 结合亲和力；其输入是 motif 分数而非原始序列，因此不能用于预测新 motif 或非已知 PWM 的 TF 结合。
- **oracle/真值输入**：预训练使用真实 ATAC-seq 可及性数据；微调使用真实表达数据；lentiMPRA 预测使用真实实验数据作为基准。
- **端到端状态**：非端到端——需要预先计算 motif 分数和 ATAC-seq peak；无法从原始 DNA 序列直接预测表达。
- **算力成本**：未提供训练成本；推理成本显著低于 Enformer（可处理 100 倍以上元件）。
- **历史数据依赖**：依赖已知 PWM 数据库和 ATAC-seq 数据质量；对低细胞数细胞类型（<600 细胞）预测失败。
- **模型依赖**：依赖 attention 架构和自监督预训练；随机初始化微调性能大幅下降。
- **最难情形**：低细胞数细胞类型、与训练分布差异大的条件（如疾病状态）、非编码区新突变效应。
- **群体/领域边界**：仅覆盖人类细胞类型；未验证其他物种；仅覆盖粗粒度细胞状态，未覆盖连续发育轨迹。
- **不确定性**：TF–TF 互作预测未经过湿实验验证；PAX5 G183S 机制为计算推断，需功能实验确认。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 依赖染色质可及性数据 | 无法在无可及性数据的条件下预测 | 整合更多数据类型（如甲基化、3D 基因组） | Discussion |
| 分辨率有限 | 仅覆盖粗粒度细胞状态和区域级序列信息 | 引入核苷酸级 footprint 和单细胞 embedding | Discussion |
| TF 同源物区分困难 | 无法区分 motif 相似的 TF 家族成员 | 结合 TF 表达数据或蛋白结构信息 | Discussion |
| 非编码变异效应预测不足 | 未系统评估突变对表达的定量影响 | 整合突变效应数据（如 MPRA、饱和突变） | Discussion |
| 物种泛化未验证 | 仅人类细胞类型 | 扩展至其他物种 | Discussion |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|--------------------------|----------|----------|------|
| 输入使用 motif 分数而非原始序列 | 模型可能仅学习 PWM 的线性组合，无法捕获非经典结合或协同效应 | 限制了模型发现新 motif 的能力 | 对比使用原始序列输入的模型在未知 motif 预测上的表现 | Methods: Motif features |
| 表达预测的 Pearson r=0.94 可能高估 | 星形胶质细胞可能是易预测的细胞类型；未报告所有 213 种细胞类型的分布 | 泛化性结论可能过度乐观 | 报告全部细胞类型的预测性能分布 | Results 图 1c |
| lentiMPRA 预测中 Enformer 在 peak 活性上更优 | GET 的优势可能来自可及性输入而非序列理解 | 削弱了「序列基础模型」的 claim | 控制可及性输入后对比序列-only 模型 | Results 图 2g |
| LiNGAM 因果推断假设线性非高斯 | TF 调控关系可能非线性，因果方向可能误判 | 影响 TF–TF 网络可靠性 | 使用非线性因果方法（如 NOTEARS-MLP）对比 | Methods: Causal discovery |
| AlphaFold 2 预测的 TF–TF 互作未做突变验证 | 结构预测可能为假阳性，尤其对 IDR 区域 | 影响 PAX5 G183S 结论的可靠性 | 对预测界面做点突变 + 共免疫沉淀验证 | Results 图 5–6 |
| 预训练数据仅 ATAC-seq | 可及性不等于 TF 结合，可能遗漏不依赖可及性的调控 | 模型可能偏向可及性依赖的调控机制 | 对比整合 ChIP-seq 或 ChIP-nexus 数据的模型 | Methods: Pretraining |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **可解释特征输入优于原始序列**：将序列转换为 motif 结合分数（基于 PWM）作为输入，可显著提升模型可解释性，且不损失预测精度。可迁移到 TF–DNA 结合预测任务：用已知 motif 特征 + 可及性特征替代原始 one-hot 序列，可降低数据需求并提升跨细胞类型泛化。
2. **自监督预训练 + 微调范式**：在 213 种细胞类型上预训练（mask 预测 motif/可及性），再微调到具体任务（表达预测），比从零训练显著提升。可迁移到 TF–DNA 结合预测：用大规模 ATAC-seq 预训练，再微调到 ChIP-seq 结合预测。
3. **因果发现优于相关性**：用 LiNGAM 从 motif 贡献矩阵推断 TF–TF 因果网络，精度显著高于简单相关性（25.2% vs 15.9%）。可迁移到 TF–DNA 互作网络推断：用表达或可及性数据 + 因果发现替代共表达/共定位分析。
4. **长距离调控检测**：GET 通过 attention 机制捕获 >1Mbp 的远端调控互作，优于传统 peak-to-gene 方法。可迁移到增强子-启动子互作预测：用 attention 权重作为互作强度指标。
5. **结构预测与计算互作推断结合**：将 GET 预测的 TF–TF 互作输入 AlphaFold 2 进行结构验证，形成「计算推断 → 结构验证」的闭环。可迁移到 TF–DNA 复合物结构预测：先用序列模型预测候选互作，再用 AlphaFold 2 或 MD 模拟验证。
6. **零样本跨平台迁移**：GET 在未见测序平台（10x multiome）和疾病细胞（GBM）上仍保持性能。可迁移到 TF–DNA 结合预测：在多种 ATAC-seq 平台预训练，提升对新平台数据的泛化。

## 15 与已有知识连接
- **Enformer (Avsec et al., 2021)**：GET 与 Enformer 同属序列→调控预测模型，但 GET 以 motif 分数为输入、跨细胞类型预训练，Enformer 以原始序列为输入、固定细胞类型训练。GET 在未见细胞类型上优于 Enformer（Results 图 1c, 2g）。
- **DeepSEA (Zhou & Troyanskaya, 2015)**：早期序列→染色质特征模型，GET 在调控元件识别上优于 DeepSEA（Results 图 3c–d）。
- **AlphaFold 2 (Jumper et al., 2021)**：GET 使用 AF2 预测 TF–TF 互作结构，验证了「计算互作推断 + 结构预测」的可行性（Results 图 5）。
- **LiNGAM (Shimizu et al., 2006)**：因果发现算法，GET 将其应用于 motif 贡献矩阵，优于相关性方法（Results 图 4h）。
- **Göös et al. (2022)**：MS 实验测定的 TF–TF 互作数据，作为 GET 互作预测的基准（Results 图 4h）。
- **候选方向**：将 GET 的「可及性 + motif 分数」特征工程迁移到 TF–DNA 结合预测（如 DeepBind、DeepSEA 的改进）；将因果发现方法迁移到 ChIP-seq 共结合网络推断。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合亲和力的可解释基础模型（Interpretable TF–DNA Binding Affinity Foundation Model）
   - **来源局限/观察**：GET 以 motif 分数为输入，无法预测新 motif 或非经典结合；现有 TF–DNA 结合预测模型（如 DeepBind）缺乏跨细胞类型泛化。
   - **核心假设**：以「序列 + 可及性 + TF 表达」为输入的自监督预训练模型，可预测未见细胞类型中 TF 的结合位点和亲和力。
   - **初步方法**：在 GET 架构基础上，将输出头改为 TF 结合位点预测（基于 ChIP-seq 或 ChIP-nexus 数据），输入增加 TF 表达量作为条件。
   - **验证方式**：在 ENCODE ChIP-seq 数据集上 leave-one-cell-type-out 验证；对比 DeepBind、DeepSEA。
   - **创新状态**：unverified

2. **候选名称**：基于因果发现的 TF–DNA 协同结合网络推断（Causal Discovery of Cooperative TF–DNA Binding Networks）
   - **来源局限/观察**：GET 的 LiNGAM 推断 TF–TF 互作，但未考虑 DNA 序列上下文（motif 间距、方向）对协同结合的影响。
   - **核心假设**：将 motif 间距/方向特征纳入因果模型，可识别 DNA 构象依赖的 TF 协同结合。
   - **初步方法**：在 GET 的 motif 贡献矩阵基础上，增加 motif 间距和相对方向特征，运行 LiNGAM 或 NOTEARS-MLP。
   - **验证方式**：用已知协同结合对（如 GATA1–TAL1）验证；用 ChIP-seq 共结合数据评估。
   - **创新状态**：unverified

3. **候选名称**：TF–DNA 复合物结构的端到端预测（End-to-End Prediction of TF–DNA Complex Structures）
   - **来源局限/观察**：GET 仅预测互作网络，AlphaFold 2 预测结构但未利用 GET 的调控上下文信息。
   - **核心假设**：将 GET 的调控 embedding 作为条件输入 AlphaFold 2，可提高 TF–DNA 复合物结构预测精度。
   - **初步方法**：将 GET 的 motif 贡献分数作为 AlphaFold 2 的 MSA 替代特征，或作为结构预测的约束条件。
   - **验证方式**：在 PDB 中已知 TF–DNA 复合物结构上测试；对比 AlphaFold 2 基线。
   - **创新状态**：unverified

4. **候选名称**：突变效应的零样本预测（Zero-shot Prediction of Mutation Effects on TF–DNA Binding）
   - **来源局限/观察**：GET 未系统评估非编码突变对表达的定量影响；现有方法（如 MPC、CADD）缺乏机制解释。
   - **核心假设**：GET 的贡献分数可解释非编码突变如何通过改变 TF 结合影响表达。
   - **初步方法**：对突变位点计算 GET 的贡献分数变化，与 MPRA 或饱和突变数据对比。
   - **验证方式**：在 lentiMPRA 突变数据集上评估；对比 Enformer 的 in silico 突变分析。
   - **创新状态**：unverified

5. **候选名称**：跨物种转录调控基础模型（Cross-species Transcription Regulation Foundation Model）
   - **来源局限/观察**：GET 仅覆盖人类；跨物种调控机制保守性未验证。
   - **核心假设**：在人类 + 小鼠 + 斑马鱼 scATAC-seq 上预训练，可提升各物种的调控预测精度。
   - **初步方法**：扩展 GET 预训练数据至多物种，用同线性（synteny）对齐调控区域。
   - **验证方式**：在各物种 leave-one-cell-type-out 验证；对比单物种模型。
   - **创新状态**：unverified