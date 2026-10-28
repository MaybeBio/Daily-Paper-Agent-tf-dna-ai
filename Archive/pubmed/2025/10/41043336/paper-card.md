## 01 基本信息
- **标题**：EnsembleRegNet: Interpretable deep learning for transcriptional network inference from single-cell RNA-seq
- **作者与单位**：Alawad, Duaa Mohammad; Katebi, Ataur; Hoque, Md Tamjidul（美国新奥尔良大学，University of New Orleans）
- **期刊/预印本平台**：Computational Biology and Chemistry
- **年份**：2025（在线日期 2025-10-04）
- **论文类型**：方法学（Method）论文，提出新计算框架
- **领域**：计算生物学 / 单细胞转录组学 / 基因调控网络推断 / 深度学习
- **关键词**：Gene regulatory network (GRN)；scRNA-seq；Deep learning；Transcription factor；Regulon；Interpretability
- **DOI/arXiv 号**：10.1016/j.compbiolchem.2025.108702
- **代码**：https://github.com/DuaaAlawad/EnsembleRegNet.git
- **数据**：GSE60361（小鼠大脑皮层）、GSE115978（人皮肤黑色素瘤）、GSE103322（人头颈鳞癌）、10x Genomics PBMC 10k
- **阅读日期**：2026-05-13（按当前日期）
- **在该课题方向中的位置**：本文属于「TF–DNA 互作 × 深度学习」交叉方向，聚焦于从 scRNA-seq 表达数据推断 TF–靶基因调控关系（GRN 推断），而非直接建模 TF–DNA 物理结合。其核心贡献在于：(1) 将深度学习（encoder-decoder + MLP 集成）用于 TF–靶基因关系预测；(2) 通过 HLE 二值化、case-deletion 分析、RcisTarget 基序富集和 AUCell 调控子活性打分增强可解释性。对「TF–DNA 结合机制」课题的可迁移点在于：其 TF 重要性评估框架（case-deletion）和基序验证流程（RcisTarget）可迁移至基于结构或序列的 TF–DNA 结合预测任务。

## 02 一句话总结
本文提出 EnsembleRegNet——一个集成 encoder-decoder 与 MLP 的深度学习框架，通过 HLE 二值化、case-deletion 分析、RcisTarget 基序富集和 AUCell 活性打分，从 scRNA-seq 数据推断 TF–靶基因调控关系，在三个真实数据集和 PBMC 基准上优于 SCENIC、SIGNET、GENIE3 和 PIDC。

## 03 研究问题
- **具体问题**：如何从高维、稀疏、含 dropout 噪声的 scRNA-seq 数据中准确推断 TF–靶基因的调控关系（GRN 结构）？
- **为什么重要**：GRN 编码细胞身份和行为的调控逻辑，理解 TF–靶基因关系是解析细胞分化、疾病机制（如癌症、免疫）和细胞重编程的关键。scRNA-seq 提供了单细胞分辨率的表达谱，但技术噪声和维度灾难使 GRN 推断极具挑战。
- **现有方法不足**：(1) 线性回归（如 SINCERITIES）无法捕捉非线性调控；(2) 微分方程模型（如 SCODE）对数据质量要求高；(3) 信息论方法（如 PIDC）计算复杂度高且难以处理高维；(4) 贝叶斯网络和布尔网络在规模上受限；(5) 深度学习方法（如 scMGATGRN）虽能建模非线性，但可解释性不足，难以提供生物学可验证的调控模块。
- **精确研究问题（Can...?）**：Can an ensemble of encoder-decoder and MLP models, combined with HLE-based binarization and motif enrichment validation, accurately infer TF–target gene regulatory relationships from scRNA-seq data while maintaining biological interpretability?

## 04 背景与发展脉络
*注：以下脉络基于本文 Introduction 的文献综述，属于「仅本文框架」，未经外部系统核验。*

| 阶段 | 代表性方法 | 优点 | 局限 |
|------|-----------|------|------|
| 线性回归 | SINCERITIES | 简单、可解释 | 仅捕捉线性关系，需时间序列数据 |
| 微分方程 | SCODE | 可建模动态调控 | 对噪声敏感，需分化轨迹 |
| 信息论 | PIDC | 捕捉非线性依赖 | 计算复杂度高，高维受限 |
| 贝叶斯网络 | 变分贝叶斯 ARMA | 建模不确定性 | 扩展性差，需先验假设 |
| 布尔网络 | 离散逻辑模型 | 直观、计算高效 | 过度简化，丢失定量信息 |
| 因果推断 | Scribe | 利用 RNA velocity | 依赖 velocity 估计准确性 |
| 深度学习（近期） | scMGATGRN, scAMZI, scRGCL | 建模非线性、图结构 | 可解释性不足，难以验证生物学意义 |
| **本文** | **EnsembleRegNet** | **非线性建模 + 可解释性（基序验证 + 调控子活性）** | **依赖基序数据库覆盖度，计算成本较高** |

**本文主张的位置**：在深度学习 GRN 推断方法中，EnsembleRegNet 通过集成策略和多重可解释性模块（HLE 二值化、case-deletion、RcisTarget、AUCell），在预测精度和生物学可解释性之间取得平衡，填补了「深度学习 GRN 推断缺乏可解释验证」的空白。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|----------|
| scRNA-seq 数据稀疏性和 dropout | 大量零表达值，基因检测不完全 | 技术限制导致低丰度转录本丢失 | Methods 2.1 节：数据预处理中需过滤低表达基因 |
| 高维非线性调控关系 | 线性模型无法捕捉 TF–靶基因的复杂依赖 | 调控关系涉及协同、竞争和间接效应 | Introduction：现有线性/信息论方法局限 |
| 深度学习模型可解释性差 | 预测结果难以映射到生物学机制 | 黑箱模型缺乏特征归因和验证手段 | Introduction：scMGATGRN 等虽能建模非线性但可解释性不足 |
| 高假阳性率 | 纯统计/线性方法产生大量假阳性调控边 | 缺乏基序证据和功能验证 | Introduction：需要 motif enrichment 验证 |
| 调控子（regulon）的细胞类型特异性 | 同一 TF 在不同细胞类型中调控不同靶基因 | 调控上下文依赖性 | Results：通过 AUCell 识别细胞类型特异性调控模块 |
| 计算可扩展性 | 大规模数据集推断 GRN 耗时 | 部分方法（如 PIDC）计算复杂度高 | Results 表 4：EnsembleRegNet 447 min vs PIDC 661 min |

## 06 核心思想

### 1) 表面方法
EnsembleRegNet 是一个六组件流水线：(1) 数据预处理与 HLE 二值化；(2) 集成 encoder-decoder + MLP 预测 TF–靶基因关系；(3) RcisTarget 基序富集验证；(4) AUCell 调控子活性打分；(5) 基于调控子活性的细胞聚类；(6) GRN 可视化。

### 2) 核心洞察
- **HLE 二值化**：使用 Hodges-Lehmann 估计器（非参数中位数估计）对表达矩阵二值化，比固定阈值更鲁棒，能适应不同数据集的分布特征。
- **Case-deletion 分析**：通过逐一将 TF 表达置零并观察靶基因预测精度的变化，量化每个 TF 对靶基因的调控贡献——这是一种「扰动分析」思路，类似于深度学习中的 occlusion sensitivity。
- **集成策略**：encoder-decoder 擅长捕捉非线性重构特征，MLP 擅长直接分类，两者加权集成（权重偏向 MLP，w=4）兼顾特征学习与直接预测。
- **基序验证闭环**：预测的 TF–靶基因关系通过 RcisTarget 基序富集验证，将表达相关性锚定到 DNA 序列基序，增强生物学可信度。

### 3) 可能的普适教训 [Analysis]
- **「预测 + 验证」闭环**：纯表达数据推断的调控关系需要独立证据（如基序、ChIP-seq）验证，这一思路可迁移到 TF–DNA 结合预测——结构预测结果应通过已知基序或突变实验交叉验证。
- **扰动分析优于静态特征重要性**：case-deletion 通过「如果该 TF 不存在，预测会怎样变化」来评估调控贡献，比静态权重更接近因果推断，可迁移到基于深度学习的 TF–DNA 结合预测中的特征归因。
- **非参数二值化**：HLE 作为鲁棒阈值选择方法，可迁移到处理 ChIP-seq peak calling 或 DNase-seq 数据的二值化预处理。

## 07 方法总览

- **输入**：scRNA-seq 表达矩阵（基因 × 细胞），经质量控制和归一化后，使用 HLE 对每个基因的表达进行二值化（0/1）。
- **输出**：(1) TF–靶基因调控关系（GRN 边）；(2) 每个细胞的调控子活性评分（AUC 矩阵）；(3) 细胞聚类结果；(4) GRN 可视化网络。
- **模块**：
  1. **预处理与二值化**：Scanpy 过滤（基因表达 > 6 细胞）、归一化（total=10,000）、log1p 变换、HLE 二值化。
  2. **集成预测模型**：Encoder-Decoder 分类器 + MLP 分类器，输入为二值化表达矩阵，输出为 TF–靶基因关系概率；集成权重 w=4（偏向 MLP）。
  3. **Case-deletion 分析**：逐一将 TF 表达置零，重新预测靶基因，计算精度变化（Acc_mn），识别关键调控 TF。
  4. **RcisTarget 验证**：对预测的靶基因集进行基序富集分析，保留具有显著基序支持的 TF–靶基因关系。
  5. **AUCell 打分**：基于验证后的调控子，计算每个细胞的 AUC 活性分数。
  6. **聚类与可视化**：基于 AUC 矩阵进行细胞聚类（t-SNE 可视化），构建 TF–TF 和 TF–靶基因网络。
- **训练**：使用 PyTorch 1.13.1，固定随机种子 42，CPU 线程 24；具体训练轮数、学习率等超参数未在摘要中提供。
- **反馈回路**：RcisTarget 验证结果可反馈调整预测模型的阈值（文中未明确说明是否迭代，[Analysis] 推测为单向流水线）。
- **假设**：TF 表达与靶基因表达的二值化状态（开/关）足以捕捉调控关系；基序数据库覆盖度足够支持验证。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| HLE 二值化 | 将连续表达值转为 0/1 二值状态 | 减少 dropout 噪声影响，提供鲁棒阈值 | 输入：归一化表达矩阵；输出：二值矩阵 B | Methods 2.2.1 节：HLE 作为非参数中位数估计 | [预期] 移除后模型对噪声更敏感，预测精度下降 |
| Encoder-Decoder 分类器 | 学习表达数据的压缩表征并分类 TF–靶基因关系 | 捕捉非线性、高阶特征交互 | 输入：二值表达向量；输出：关系概率 | Methods 2.2.2 节：公式 5-8 | [预期] 移除后丧失非线性特征提取能力 |
| MLP 分类器 | 直接基于原始特征分类 | 提供直接、可解释的基线预测 | 输入：二值表达向量；输出：关系概率 | Methods 2.2.2 节：公式 9-11 | [预期] 移除后集成多样性降低，鲁棒性下降 |
| 集成加权（w=4） | 融合两个分类器输出 | 平衡特征学习与直接预测 | 输入：两个分类器输出；输出：集成预测 | Methods 2.2.2 节：公式 12 | [预期] 权重调整影响精度-鲁棒性权衡 |
| Case-deletion 分析 | 逐一置零 TF 表达，评估预测精度变化 | 量化 TF 对靶基因的调控贡献 | 输入：二值矩阵 + 集成模型；输出：Acc_mn 矩阵 | Methods 2.2.3 节：公式 14-15 | [预期] 移除后无法识别关键调控 TF |
| RcisTarget 基序富集 | 验证预测靶基因是否富集已知 TF 基序 | 锚定预测到 DNA 序列证据，过滤假阳性 | 输入：预测靶基因集；输出：富集评分/调控子 | Methods 2.2.4 节 | [预期] 移除后假阳性率升高，可解释性下降 |
| AUCell 活性打分 | 计算每个细胞的调控子活性 | 连接 GRN 到单细胞功能状态 | 输入：调控子 + 表达矩阵；输出：AUC 矩阵 | Methods 2.2.5 节 | [预期] 移除后无法进行细胞类型特异性分析 |
| 聚类与可视化 | 基于调控子活性聚类细胞、展示 GRN | 识别细胞类型特异性调控程序 | 输入：AUC 矩阵；输出：聚类标签、网络图 | Results 图 2-4、图 6 | [预期] 移除后丧失生物学解释能力 |

## 09 关键公式符号

| 公式 | 符号含义 | 用途 | 直觉 |
|------|----------|------|------|
| Z = [Z₁; Z₂]（公式 1） | Z：表达矩阵（R×C）；Z₁：TF 基因部分（R×F）；Z₂：非 TF 基因部分（R×N） | 定义输入数据结构 | 将基因分为 TF 和非 TF 两类，便于分别处理 |
| HLE = median_{i,j} (aᵢ + aⱼ)/2（公式 2） | aᵢ, aⱼ：数据点对 | 计算 Hodges-Lehmann 估计器 | 所有数据点对平均值的中间值，比均值更抗离群值 |
| Dₗ = median_{i,j} (Zᵢc + Zⱼc)/2（公式 3） | Dₗ：第 l 列的二值化阈值；Zᵢc, Zⱼc：第 c 列中第 i, j 行的表达值 | 为每个基因（列）计算独立阈值 | 每个基因有自己的阈值，适应不同表达水平 |
| b_rc = I{z_rc ≥ Dₗ}（公式 4） | b_rc：二值化后的元素；I{·}：指示函数 | 将表达值转为 0/1 | 表达值 ≥ 阈值则记为 1（活跃），否则为 0 |
| h = ReLU(Wₑx + bₑ)（公式 5） | h：编码向量；Wₑ, bₑ：编码器权重和偏置 | Encoder 压缩输入 | 将高维输入压缩为低维表征 |
| x′ = ReLU(W_d h + b_d)（公式 6） | x′：重构输出；W_d, b_d：解码器权重和偏置 | Decoder 重构输入 | 从压缩表征恢复原始输入，验证信息保留 |
| Z = ReLU(W_c1 x′ + b_c1)（公式 7） | Z：隐藏层输出；W_c1, b_c1：分类器第一层参数 | 分类器特征变换 | 对重构特征进一步非线性变换 |
| y = W_c2 z + b_c2（公式 8） | y：原始 logits；W_c2, b_c2：分类器输出层参数 | 输出分类分数 | 无 sigmoid，配合 CrossEntropyLoss 使用 |
| y_ensemble = (w·y_MLP + y_encoder-decoder)/5（公式 12） | w=4：集成权重 | 融合两个模型输出 | MLP 贡献 80%，encoder-decoder 贡献 20% |
| L1 = λ_L1 Σ|wᵢ|（公式 13） | λ_L1：正则化强度；wᵢ：模型权重 | L1 正则化 | 鼓励权重稀疏，提升可解释性 |
| Acc_mn = 1 - (1/K)‖f_n(B_m) - b_{M+n}‖₀（公式 15） | f_n：预测函数；B_m：第 m 个 case-deleted 矩阵；b_{M+n}：第 n 个靶基因的真实标签；‖·‖₀：L0 范数 | 计算 case-deletion 后的预测精度 | 精度下降越多，说明该 TF 对靶基因越重要 |

## 10 实验设计与证据链

### 数据集与设置
- **数据集 1**：GSE60361（小鼠大脑皮层，Zeisel et al. 2015），3,005 个细胞，67 只小鼠
- **数据集 2**：GSE115978（人皮肤黑色素瘤 SKCM，Jerby-Arnon et al. 2018），7,186 个细胞，31 个肿瘤
- **数据集 3**：GSE103322（人头颈鳞癌 HNSCC，Puram et al. 2017），5,902 个细胞，18 例患者
- **基准数据集**：10x Genomics PBMC 10k（外周血单核细胞）
- **对比方法**：SIGNAL（SIGNET）、SCENIC、GENIE3、PIDC
- **评估指标**：
  - 聚类：ARI、NMI、PSI、NVD、F-score、RMSSTD、Silhouette、Modified Hubert Γ
  - 调控关系：Macro-AUROC、Macro-AUPRC（基于 TRRUST v2 + DoRothEA 整合的 gold standard）
- **硬件**：Intel Core i9-14900HX（24 核），32 GB RAM，NVIDIA GPU 8 GB
- **软件**：Python 3.8.18，PyTorch 1.13.1，Scanpy 1.9.6，pySCENIC 0.11.2

### 实验表格

| 实验 | 检验的 Claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-----------------|------|
| GSE60361 聚类比较 | EnsembleRegNet 聚类优于 SCENIC/SIGNET | 三种方法，外部+内部指标 | ARI 0.544（最高），NMI 0.592（最高），PSI 0.725（最高），NVD 0.236（最低） | EnsembleRegNet 在 GSE60361 上聚类精度最高 | 单一数据集，不能推广到所有组织类型 | Results 表 1、图 2 |
| GSE115978 聚类比较 | EnsembleRegNet 在黑色素瘤数据上同样领先 | 三种方法 | ARI、NMI、PSI 均最高，NVD 最低 | 跨数据集一致性支持方法泛化性 | 仅两个真实数据集 | Results 表 2、图 3 |
| GSE103322 聚类比较 | EnsembleRegNet 在 HNSCC 数据上表现 | 三种方法 | ARI 0.466（SCENIC 0.261，SIGNET 0.011），NMI 0.685，PSI 最高 | 在复杂肿瘤数据中优势更明显 | 肿瘤异质性可能影响结论 | Results 表 3、图 4 |
| PBMC 调控关系基准 | EnsembleRegNet 恢复已知 TF–靶基因关系的能力 | vs GENIE3、PIDD，Macro-AUROC/AUPRC | AUROC 0.687（GENIE3 0.588，PIDC 0.691），AUPRC 0.0116（与 PIDC 持平） | 优于 GENIE3，与 PIDC 相当 | AUPRC 绝对值低，gold standard 覆盖有限 | Results 表 4 |
| 运行时间比较 | EnsembleRegNet 计算效率 | 三种方法 | 447 min（GENIE3 545 min，PIDC 661 min） | 计算效率最高 | 单次运行，未报告方差 | Results 表 4 |
| 网络可视化 | 识别已知和新型 TF–TF 互作 | 文献/TRUUST 验证 | 识别出 CEBPB–EGR2、IRF7–STAT1、EBF1–LMO2、STAT3–JUNB 等已知互作 | 预测具有生物学可信度 | 新型互作未经验证 | Results 图 6 |

## 11 结论正确解读

- **任务范围**：本文解决的是「从 scRNA-seq 表达数据推断 TF–靶基因调控关系」的计算任务，而非直接建模 TF–DNA 物理结合。其输出是 GRN 边（调控关系），不是结合位点或结合亲和力。
- **Oracle/真值输入**：在 PBMC 基准中，gold standard 由 TRRUST v2（人工 curated）和 DoRothEA（文献整合）构成，这些数据库本身存在覆盖偏差（偏向研究充分的 TF）和实验条件差异。
- **端到端状态**：EnsembleRegNet 是端到端可运行的完整流水线，但「端」是「表达矩阵 → 调控网络」，不涉及 DNA 序列或结构信息输入。
- **算力成本**：447 分钟（约 7.5 小时）在单机（i9 + 8GB GPU）上完成 PBMC 10k 推断，属于中等计算成本；但未报告训练轮数、batch size 等细节。
- **历史数据依赖**：方法依赖基序数据库（RcisTarget 内置）和 TF 列表的完整性；对未注释的 TF 或非模式物种可能失效。
- **模型依赖**：集成权重 w=4 是针对本研究三个数据集调优的，迁移到其他数据可能需要重新调整。
- **最难情形**：稀疏性极高的数据（如 10x 平台）、罕见细胞类型、低表达 TF 的调控关系推断。
- **群体/领域边界**：方法在哺乳动物（小鼠、人）数据上验证，对非模式物种的适用性未测试。
- **不确定性**：未报告置信区间或多次运行的方差；AUPRC 绝对值低（0.0116）表明正样本极少，预测精度有限。

**有边界的复述**：EnsembleRegNet 在三个 scRNA-seq 数据集上，通过集成 encoder-decoder 与 MLP 并辅以 HLE 二值化、case-deletion 分析和基序验证，在细胞聚类和已知调控关系恢复方面优于 SCENIC 和 SIGNET，在 PBMC 基准上与 PIDC 相当且计算更快；但其预测的调控关系仍需实验验证，且方法依赖基序数据库覆盖度。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 需要足够样本量避免过拟合 | 深度学习模型在小样本数据上可能过拟合 | 作者在 Conclusions 中提及「requires sufficient sample size to avoid overfitting」 | Conclusions 节 |
| 计算需求高 | 对非常大的数据集可能计算密集 | 作者提及「can be computationally demanding for very large datasets」 | Conclusions 节 |
| 稀疏/噪声数据需额外预处理 | 极端稀疏或高噪声数据可能需要额外预处理或阈值调整 | 作者提及「may need additional preprocessing or careful threshold adjustments in sparse or noisy data」 | Conclusions 节 |
| 无法完全区分直接与间接调控 | 预测的调控关系可能包含间接效应 | 作者提及「cannot fully distinguish direct from indirect regulatory effects without complementary experimental validation」 | Conclusions 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 对比方法仅限 SCENIC、SIGNET、GENIE3、PIDC | 未与最新深度学习方法（如 scMGATGRN、DeepSEM、GRNBoost2）对比 | 无法确认 EnsembleRegNet 是否代表当前最优 | 在相同数据集上复现并对比更多基线方法 | Results 节 |
| 聚类评估使用 ARI/NMI 等指标，但未报告细胞类型注释的生物学准确性 | 高聚类指标不一定对应正确的生物学细胞类型 | 聚类是中间步骤，最终目标是生物学发现 | 使用 marker gene 验证聚类结果的生物学意义 | Results 表 1-3 |
| PBMC 基准的 AUPRC 绝对值极低（0.0116） | 即使优于 GENIE3，绝对性能可能不足以支撑实际生物学发现 | 低 AUPRC 意味着大量假阳性预测 | 检查预测的 top-ranked 调控关系是否通过 ChIP-seq 验证 | Results 表 4 |
| Case-deletion 方法计算成本高 | 对每个 TF 需重新运行模型，O(M) 次推理 | 限制了在大型 TF 库上的可扩展性 | 分析计算复杂度与 TF 数量的关系 | Methods 2.2.3 节 |
| HLE 二值化可能丢失定量信息 | 将连续表达转为 0/1 可能忽略表达水平梯度信息 | 某些调控关系可能依赖表达量的连续变化 | 对比连续表达输入与二值化输入的预测性能 | Methods 2.2.1 节 |
| 集成权重 w=4 的选取依据未充分说明 | 可能是经验调优而非理论驱动 | 影响方法在新数据集上的可迁移性 | 在不同数据集上测试 w 的敏感性 | Methods 2.2.2 节 |
| 未报告模型训练的详细超参数 | 学习率、epoch、batch size 等缺失 | 影响可复现性 | 联系作者获取或从代码仓库推断 | Methods 节 |
| 网络可视化中的「新型互作」未经验证 | 可能只是假阳性 | 声称的「novel interactions」需要实验支持 | 对预测的新型互作进行 ChIP-seq 或报告基因验证 | Results 图 6 |

## 14 学到什么
**Agent 提炼的知识候选**

1. **「预测 + 独立验证」闭环设计**：EnsembleRegNet 将表达数据预测与 RcisTarget 基序验证串联，形成「计算预测 → 序列证据确认」的流水线。**可迁移到 TF–DNA 结合课题**：基于结构预测（如 AlphaFold、MD 模拟）的 TF–DNA 结合候选位点，应通过已知基序数据库（如 JASPAR、CIS-BP）或突变实验交叉验证，形成闭环。

2. **Case-deletion 作为因果归因方法**：通过逐一移除输入特征（TF 表达）并观察预测变化来量化特征重要性，比静态注意力权重更接近因果推断。**可迁移到 TF–DNA 结合预测**：在基于深度学习的结合位点预测中，可通过逐点突变（in-silico mutagenesis）每个 DNA 碱基或蛋白残基，观察结合预测分数的变化，识别关键结合残基/碱基——这等价于计算「结合热图」或「重要性图谱」。

3. **HLE 非参数二值化**：使用 Hodges-Lehmann 估计器（所有数据点对平均值的中间值）作为二值化阈值，比固定阈值或均值更抗离群值。**可迁移到 TF–DNA 结合课题**：在处理 ChIP-seq 峰强度、DNase-seq 信号或 HT-SELEX 富集分数时，HLE 可作为鲁棒的信号/噪声分割阈值，尤其适用于分布偏斜的数据。

4. **集成模型权重可调**：通过加权集成（w=4 偏向 MLP）平衡不同模型的优势。**可迁移到 TF–DNA 结合预测**：可集成基于序列的模型（如 CNN、Transformer）与基于结构的模型（如 GNN、MD 特征），通过可调权重适应不同数据场景（如已知结构 vs. 仅序列）。

5. **调控子活性（regulon activity）作为中间表征**：将 TF–靶基因关系压缩为每个细胞的调控子活性分数，再基于此进行聚类和可视化。**可迁移到 TF–DNA 结合课题**：可将 TF 的结合事件（如 ChIP-seq 峰）压缩为每个细胞/条件的「调控活性」分数，用于连接结合事件到功能表型，弥合「结合」与「功能」之间的鸿沟。

6. **多数据集验证策略**：使用三个不同组织/疾病的数据集 + 一个独立基准数据集，覆盖正常（大脑皮层）和肿瘤（黑色素瘤、HNSCC）场景。**可迁移到 TF–DNA 结合课题**：TF–DNA 结合预测模型应在多种细胞类型和条件下验证，避免单一数据集的过拟合。

## 15 与已有知识连接

- **SCENIC**（Aibar et al., 2017）：本文直接对比的基准方法，也是 RcisTarget 和 AUCell 的来源。SCENIC 是 GRN 推断的金标准之一，本文在聚类和调控子恢复方面声称超越 SCENIC。
- **SIGNET**（Luo et al., 2022）：另一个对比基准，同样使用 HLE 二值化，本文在此基础上引入深度学习集成。
- **GENIE3**（Huynh-Thu et al., 2010）：基于随机森林的经典 GRN 推断方法，本文在 PBMC 基准上对比。
- **PIDC**（Chan et al., 2017b）：基于部分信息分解的 GRN 推断方法，本文在 PBMC 基准上对比。
- **TRRUST v2**（Han et al., 2019）：人工 curated 的 TF–靶基因数据库，本文用作 gold standard 的一部分。
- **DoRothEA**（Garcia-Alonso et al., 2019）：文献整合的调控子数据库，本文用作 gold standard 的一部分。
- **RcisTarget**（Aibar et al., 2017）：基序富集分析工具，本文用于验证预测的 TF–靶基因关系。
- **AUCell**（Van de Sande et al., 2020）：调控子活性打分工具，本文用于单细胞水平的调控活性量化。
- **与 TF–DNA 结合机制课题的关联**：本文的 GRN 推断本质上是「表达层面的功能关联」，而 TF–DNA 结合机制关注「物理层面的分子互作」。两者互补：GRN 推断提供候选调控关系，TF–DNA 结合预测/实验提供分子机制验证。本文的 case-deletion 归因方法可迁移到结合预测中的关键残基/碱基识别。

## 16 研究想法
**Agent 生成的研究候选**

### 候选 1：基于结构信息的 TF–DNA 结合预测增强 GRN 推断
- **名称**：StructEnhance-GRN
- **来源局限/观察**：EnsembleRegNet 仅使用表达数据推断调控关系，缺乏 DNA 序列和结构信息，导致无法区分直接与间接调控（作者自认局限）。
- **核心假设**：将 TF–DNA 结构预测（如 AlphaFold3、MD 模拟）或基序信息（JASPAR）作为先验约束，可过滤 GRN 推断中的间接调控边，提高精度。
- **增量**：在 EnsembleRegNet 的 RcisTarget 验证步骤中，引入结构预测评分（如结合亲和力预测）作为额外过滤条件。
- **初步方法**：对 EnsembleRegNet 预测的每个 TF–靶基因对，提取靶基因启动子区域序列，使用基于结构的预测器（如 DeepMind 的 AlphaFold3 或基于 CNN 的 DeepBind）计算结合概率，与表达相关性联合评分。
- **验证方式**：在 ChIP-seq 验证的 TF–靶基因对（如 ENCODE 数据）上比较联合评分 vs 纯表达评分的 AUROC。
- **创新状态**：unverified

### 候选 2：基于 in-silico 突变的 TF–DNA 结合关键碱基识别
- **名称**：MutScan-TFBS
- **来源局限/观察**：EnsembleRegNet 的 case-deletion 方法在表达层面识别关键 TF，但未延伸到 DNA 序列层面的关键碱基识别。
- **核心假设**：对 DNA 序列进行逐碱基 in-silico 突变，观察 TF–DNA 结合预测分数的变化，可识别关键结合碱基，其准确度可通过已知的 position weight matrix（PWM）或 SELEX 实验验证。
- **增量**：将 case-deletion 思想从「基因表达」迁移到「DNA 序列」，为 TF–DNA 结合机制提供碱基级分辨率。
- **初步方法**：使用训练好的 TF–DNA 结合预测模型（如 DeepBind、BPNet），对每个候选结合位点进行逐碱基替换（A/C/G/T），计算预测分数变化矩阵，生成「突变敏感性图谱」。
- **验证方式**：与 HT-SELEX 实验数据或 SNP 关联数据（如 GWAS 中 TF 结合位点变异）对比。
- **创新状态**：partially checked（类似方法在 DeepBind 等模型中有初步应用，但未系统化）

### 候选 3：调控子活性引导的细胞类型特异性 TF–DNA 结合分析
- **名称**：CellType-TFBind
- **来源局限/观察**：EnsembleRegNet 通过 AUCell 识别细胞类型特异性调控子，但未将调控子活性与 TF–DNA 结合事件（如染色质可及性、甲基化状态）关联。
- **核心假设**：细胞类型特异性调控子的活性差异，部分由 TF–DNA 结合位点的染色质可及性差异解释；整合 scRNA-seq 与 scATAC-seq 可揭示这一机制。
- **增量**：将 EnsembleRegNet 的调控子输出与染色质可及性数据整合，建立「调控子活性 → 结合位点可及性」的关联模型。
- **初步方法**：对 EnsembleRegNet 识别的细胞类型特异性调控子，提取其靶基因的启动子/增强子区域，与 scATAC-seq 峰重叠分析；使用 motif 匹配（如 FIMO）和可及性评分联合预测结合事件。
- **验证方式**：在已发表的同时具有 scRNA-seq 和 scATAC-seq 的数据集（如人类骨髓、肿瘤微环境）上验证。
- **创新状态**：unverified

### 候选 4：基于 MD 模拟的 TF–DNA 结合亲和力预测作为 GRN 边权重
- **名称**：MD-Weighted-GRN
- **来源局限/观察**：EnsembleRegNet 的调控关系权重来自表达预测，缺乏物理化学基础；TF–DNA 结合亲和力是调控关系的物理决定因素。
- **核心假设**：对关键 TF–DNA 对进行 MD 模拟（或使用 MM/PBSA 等自由能计算方法）预测的结合亲和力，可作为 GRN 边的物理权重，提高调控关系排序的准确性。
- **增量**：将物理模拟（MD）与深度学习 GRN 推断结合，为调控边提供「物理可信度」评分。
- **初步方法**：从 EnsembleRegNet 预测的 top-ranked TF–靶基因对中，选取有结构信息的 TF–DNA 复合物（PDB），进行短时 MD 模拟（如 100 ns），计算结合自由能（MM/PBSA），与表达相关性联合排序。
- **验证方式**：在已知结合亲和力数据（如 SELEX 或 SPR 实验）上验证 MD 预测的准确性；在 ChIP-seq 数据上验证联合排序的精度提升。
- **创新状态**：unverified（MD 用于 TF–DNA 结合已有先例，但与 GRN 推断整合未见报道）

### 候选 5：基于图神经网络的 TF–DNA 结合位点预测与 GRN 推断联合模型
- **名称**：GNN-TFBS-GRN
- **来源局限/观察**：EnsembleRegNet 将 GRN 推断和基序验证作为两个独立步骤，未实现端到端联合优化。
- **核心假设**：图神经网络（GNN）可同时建模「TF–靶基因表达关系」和「TF–DNA 序列结合」两种异质信息，实现联合学习，提升两者性能。
- **增量**：构建一个统一框架，将表达图（TF–靶基因）和序列图（TF–DNA motif）作为多模态输入，通过 GNN 消息传递实现信息融合。
- **初步方法**：构建异构图，节点为 TF 和靶基因，边分为「表达调控边」（来自 scRNA-seq）和「序列结合边」（来自 motif 匹配）；使用 GraphSAGE 或 GAT 进行节点表示学习，同时优化边预测（GRN 推断）和结合位点分类。
- **验证方式**：在多个 scRNA-seq 数据集上比较联合模型 vs 两阶段模型的 GRN 推断精度；在 ChIP-seq 数据上验证结合位点预测。
- **创新状态**：unverified