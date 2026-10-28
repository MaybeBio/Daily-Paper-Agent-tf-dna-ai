## 01 基本信息
- **标题**：Predicting the impact of sequence motifs on gene regulation using single-cell data
- **作者**：Hepkema, Jacob; Lee, Nicholas Keone; Stewart, Benjamin J; Ruangroengkulrith, Siwat; Charoensawan, Varodom; Clatworthy, Menna R; Hemberg, Martin
- **单位**：未提供（根据作者信息推测为 Wellcome Sanger Institute 等，但原文未明确列出）
- **期刊/平台**：Genome Biology
- **年份**：2023-08-16
- **论文类型**：方法学（Method）论文，提出新计算工具
- **领域**：计算基因组学 / 单细胞生物信息学 / 基因调控
- **关键词**：单细胞 RNA-seq、调控基序、卷积神经网络、转录因子、基因表达预测
- **DOI/arXiv**：10.1186/s13059-023-03021-9
- **代码**：https://github.com/jacobhepkema/scover（MIT 许可证）
- **数据**：人类胎儿/成人肾脏 scRNA-seq（67,471 细胞）、Tabula Muris 20 组织 scRNA-seq（38,080 细胞）、人类大脑皮层 scRNA+ATAC-seq（8,981 细胞）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」方向，核心贡献在于从单细胞转录组数据中**同时**进行 de novo 基序发现和定量评估基序对基因表达的贡献，无需预先提供 motif 注释或 ChIP-seq 数据。与 BPNet、Enformer 等需要大量 bulk 数据的深度学习方法不同，scover 专门针对单细胞数据的高稀疏性设计，并输出可直接用于 TF 优先级排序的「influence score」。

## 02 一句话总结
本文提出 scover——一个单层卷积神经网络，以 one-hot 编码的启动子或远端开放染色质序列为输入，预测单细胞池（pooled）的基因表达或染色质可及性值，通过 leave-one-out 扰动计算每个 motif 的 influence score，从而在无需先验 motif 注释的情况下实现 de novo 基序发现及其对基因调控贡献的定量评估。

## 03 研究问题
- **具体问题**：如何从单细胞转录组/染色质可及性数据中，同时实现 (1) de novo 调控基序发现和 (2) 定量评估每个基序对基因表达或染色质状态的贡献？
- **为什么重要**：在高等真核生物中，绝大多数碱基是非编码 DNA，理解这些序列如何调控基因表达是基因组学的核心目标之一。单细胞数据提供了细胞类型特异性的调控信息，但现有工具无法充分利用这些数据同时完成基序发现和贡献量化。
- **现有方法不足**：
  - SCENIC、Homer 等主要做 motif 富集分析，需要预先已知 motif 数据库，且不能定量评估 motif 对表达水平的贡献。
  - BPNet、Enformer 等深度学习方法需要大量 bulk 数据（ChIP-seq、DNase-seq），且模型架构深、表示分布式，生物学解释困难。
  - 没有方法专门针对单细胞数据的高稀疏性和 dropout 问题设计。
- **精确的「Can ... ?」问题**：Can a single-layer convolutional neural network trained on pooled single-cell data simultaneously discover regulatory motifs de novo and quantify their cell type-specific impact on gene expression and chromatin accessibility?

## 04 背景与发展脉络
**脉络标注**：以下脉络基于本文引言和讨论部分整理，属于「仅本文框架」，未经外部系统综述核验。

1. **阶段一：基于序列的 motif 扫描与富集（pre-deep-learning 时代）**
   - 代表方法：HOMER、FIMO、MEME
   - 优点：计算简单、可解释性强
   - 局限：需要已知 motif 数据库；只能判断「是否富集」，不能定量评估对表达的贡献；无法处理 motif 间的非线性交互

2. **阶段二：基于 bulk 数据的深度学习方法**
   - 代表方法：BPNet（ChIP-seq 峰值预测）、Enformer（长程调控预测）、Basset（染色质可及性预测）
   - 优点：预测精度高，可学习复杂序列特征
   - 局限：需要大量 bulk 数据；深层架构的分布式表示难以直接提取「单个 motif 的贡献」；不适用于单细胞数据的高稀疏性

3. **阶段三：单细胞调控推断方法**
   - 代表方法：SCENIC（基于共表达和 motif 富集的调控网络推断）
   - 优点：利用单细胞分辨率
   - 局限：依赖已知 motif 数据库；不能 de novo 发现 motif；不提供定量贡献分数

4. **本文主张的位置**：scover 填补了「单细胞数据 + de novo motif 发现 + 定量贡献评估」的空白，采用极浅架构（单卷积层 + 全局最大池化 + 线性层）保证可解释性，并通过 pooling 策略解决单细胞稀疏性问题。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单细胞数据高稀疏性 | 大量 dropout 事件，基因表达矩阵含大量零值 | 单细胞测序技术本身的捕获效率限制 | Methods "Pooling" 节：通过 k-NN pooling 将稀疏单细胞数据聚合为较稠密的池 |
| 现有 motif 工具依赖先验数据库 | SCENIC、HOMER 需要已知 motif 注释 | 数据库覆盖不完整，尤其对非模式生物 | Background 节："determining which motifs are functional and quantifying their importance remains a major challenge" |
| 深度学习方法可解释性差 | BPNet 等深层模型难以提取单个 motif 的独立贡献 | 多层非线性变换导致表示分布式 | Background 节：指出深层模型"representation is distributed and may be difficult to interpret biologically" |
| 缺乏同时发现 motif 和量化贡献的工具 | 现有方法要么只做富集分析，要么只做预测 | 技术路线上的割裂 | Background 节："none of these methods is designed for both de novo motif identification and quantification of the contribution to gene expression levels with scRNAseq" |
| 计算成本高 | 深层模型需要大量 GPU 资源和训练数据 | 模型复杂度与数据需求正相关 | 未提供直接证据；[Analysis] 从模型架构（单卷积层）可推断作者有意控制计算成本 |

## 06 核心思想
1. **表面方法**：训练一个单层 CNN（600 个尺寸为 12×4 的卷积滤波器），输入 one-hot 编码的 1 kb 启动子序列或 240 bp 开放染色质区域序列，输出预测的池化基因表达值或染色质可及性值。训练后，通过 leave-one-out 策略——将某个卷积滤波器的权重置零，比较预测值变化——计算每个 motif 的 influence score。

2. **核心洞察**：
   - **浅层架构 = 可解释性**：单卷积层 + 全局最大池化 + 线性层，使得每个滤波器直接对应一个序列 motif（通过 PFM 提取），线性层权重直接反映该 motif 对输出的贡献方向（激活/抑制）。
   - **Pooling 解决稀疏性**：不依赖细胞类型注释，而是通过 k-NN（k=100）在图谱空间中聚合相似细胞，将单细胞级别的稀疏计数转化为池级别的稠密信号，同时保留细胞类型异质性。
   - **Leave-one-out 作为贡献量化**：通过扰动单个滤波器并测量预测变化，将「预测性能」转化为「生物学贡献」，避免了对网络内部表示的复杂解释。

3. **可能的普适教训** [Analysis]：在调控基因组学中，「模型复杂度」与「生物学可解释性」之间存在直接权衡。scover 证明了对于启动子近端调控这类相对局部的任务，极浅架构足以捕获关键信号，且其输出天然具有生物学意义。这提示该领域研究者：在追求预测精度的同时，应优先考虑能直接映射到生物学实体（如 motif、TF）的模型设计。

## 07 方法总览
- **输入**：one-hot 编码的 DNA 序列。启动子任务：1 kb（±500 bp 围绕 TSS）；开放染色质任务：240 bp（±120 bp 围绕 ATAC 峰值中心）。
- **输出**：池化后的基因表达值（log 变换）或染色质可及性值，维度为池数量 p。
- **核心模块**：
  1. **Pooling 模块**：PCA（100 维）→ UMAP → 几何采样（geometric sketching）选 1000 个种子细胞 → 每个种子细胞取 k 个最近邻（k=100）求和 → 得到 1000 个池的稠密表达矩阵。
  2. **CNN 模块**：单卷积层（600 个滤波器，尺寸 12×4，无 bias）→ ELU 激活 → 全局最大池化 → 全连接层（带 bias，600 输入 → p 输出）。
  3. **Motif 提取模块**：对每个滤波器，在训练集序列上计算激活，提取产生最大正激活的 12 bp 子序列，汇总为 PFM → PPM → MEME 格式。
  4. **Influence score 模块**：对每个滤波器 i，将其权重置零，重新计算预测，influence score n_ij = (1/N) Σ (b_ijk - c_ijk)，其中 b 为原始预测，c 为扰动后预测，N 为验证集序列数。
  5. **TF 关联模块**：对每个 motif cluster，计算其 influence score 与候选 TF 表达量之间的 Spearman 相关。
- **训练**：MSE 损失，Adam 优化器，贝叶斯超参数优化（Ray Tune + hyperopt），10 折交叉验证，每折训练 10 个模型（r=10），共 100 个模型。
- **反馈回路**：无显式反馈回路；训练与解释是两阶段流程。
- **假设**：启动子/开放染色质序列中的局部 motif 组合足以解释大部分表达/可及性变异；k-NN pooling 保留细胞类型特异性；leave-one-out 扰动能有效估计单个 motif 的边际贡献。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| k-NN Pooling | 将稀疏单细胞数据聚合为稠密池 | 单细胞数据 dropout 严重，直接训练难以收敛 | 输入：单细胞表达矩阵 + PCA/UMAP 嵌入；输出：1000 个池的聚合表达向量 | Methods "Pooling" 节；Fig. 1a；Fig. S1 显示池内细胞类型同质性 >80% | 预期影响 [Analysis]：移除后模型无法处理稀疏数据，训练不稳定，预测精度大幅下降（未做消融实验，属预期推断） |
| 单层卷积（600 滤波器，12-mer） | 学习序列 motif 特征 | 浅层架构保证每个滤波器可解释为独立 motif | 输入：one-hot 序列（4×L）；输出：600 维特征向量 | Methods "Convolutional neural network architecture" 节；Fig. 1b | 实测影响：移除卷积层则模型退化为线性模型，无法捕获序列特征（未直接消融，[Analysis] 从架构设计推断） |
| 全局最大池化 | 提取序列中最强的 motif 匹配信号 | 允许 motif 在序列任意位置出现 | 输入：卷积层输出（600×L'）；输出：600 维最大值向量 | Methods 同上 | 预期影响 [Analysis]：替换为平均池化会稀释强信号，降低对稀疏 motif 的敏感性 |
| Leave-one-out influence score | 量化每个 motif 对预测的边际贡献 | 将黑盒预测转化为可解释的生物学贡献 | 输入：训练好的模型 + 验证集；输出：每个 motif 在每个池的 influence score | Methods "Leave-one-out analysis and influence scores" 节；Fig. 1d | 实测影响：移除该模块则无法获得 motif 贡献排序，退化为纯预测工具 |
| Motif 聚类与注释 | 将 600 个滤波器归并为 motif family，并与已知数据库比对 | 减少冗余，提高可解释性 | 输入：600 个 PFM；输出：motif clusters + 数据库比对结果 | Methods "Alignment of motifs" 节；Fig. 1c | 预期影响 [Analysis]：移除后 600 个独立滤波器难以人工解读，生物学结论无法提炼 |
| TF 关联分析 | 通过表达相关性将 motif 关联到具体 TF | 从 motif 层面提升到 TF 层面，便于生物学验证 | 输入：motif influence scores + TF 表达矩阵；输出：Spearman 相关及 p 值 | Methods "Assignment of putative transcription factors" 节；Fig. 3b-c | 预期影响 [Analysis]：移除后无法判断哪个 TF 是 motif 的 functional binder |

## 09 关键公式符号
1. **Influence score**（Methods "Leave-one-out analysis and influence scores" 节）：
   n_ij = (1/N) Σ_{k=1}^{N} (b_ijk - c_ijk)
   - n_ij：motif i 在池 j 的 influence score
   - b_ijk：原始模型对序列 k 在池 j 的预测值
   - c_ijk：将 motif i 对应滤波器权重置零后，模型对序列 k 在池 j 的预测值
   - N：验证集序列总数
   - 直觉：衡量移除该 motif 后预测值的变化量，正值表示激活贡献，负值表示抑制贡献

2. **Spearman 相关**（TF 关联分析）：
   r_ct = corr(aggregate influence of motif cluster c, expression of TF t)
   - 用于判断哪个 TF 最可能结合该 motif cluster

3. **损失函数**：MSE（均方误差），未给出具体公式，但明确使用 Adam 优化器

4. **Pooling 变换**：pooled_count = log(1 + Σ raw_counts)，对每个种子细胞及其 k 个最近邻的原始计数求和后取 log 变换

## 10 实验设计与证据链
**数据集与规模**：
1. 人类肾脏：67,471 细胞（胎儿+成人），18,150 基因，1000 池（每池 120 细胞）
2. Tabula Muris：20 组织，38,080 细胞（排除 297 红细胞），17,270 基因，1000 池（每池 80 细胞）
3. 人类大脑皮层：8,981 细胞，292,338 个远端开放染色质区域（±120 bp），1000 池（每池 100 细胞）

**指标**：Pearson R²（预测值与真实值的相关性平方）；influence score 的 z-score 变换用于可视化

**基线/对比方法**：
- FIMO + 线性回归（FIMO 先扫描已知 motif，再用线性回归拟合表达）
- FIMO + 随机森林（20 个估计器）
- 置换实验：序列核苷酸顺序打乱（scrambled sequences）、池顺序打乱（permuted cell pools）

**评测协议**：10 折交叉验证，每折独立训练和测试

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-------------------|------|
| 肾脏启动子预测 | scover 能同时发现 motif 并预测表达 | scover vs FIMO+线性回归 vs FIMO+随机森林 | scover 平均 R²=15%，优于 FIMO+线性回归（12%）和 FIMO+随机森林（10%）；置换对照降至 5% | 联合 motif 发现与贡献评估优于两阶段方法 | 未证明 scover 优于所有可能的深度学习方法 | Results 节；Fig. S4 |
| 肾脏 motif 发现 | 发现的 motif 与已知肾脏相关 TF 匹配 | 与 CIS-BP 数据库比对 | 16 个可重复 motif family，包括 ETS、Ebox、SNAI2 等 | de novo 发现能恢复已知调控基序 | 未证明能发现全新未知 motif | Results 节；Fig. 2a-b |
| 肾脏 TF 优先级排序 | 表达相关性可识别 functional TF | Spearman 相关 | SNAI2 与 Ebox/CACCTG 强相关；YY1 与 YY2 中 YY1 相关更高 | 表达相关可辅助 TF 鉴定 | 相关性不等于因果性，需实验验证 | Results 节；Fig. 2e, 3b-c |
| Tabula Muris 跨组织验证 | 方法可泛化到多组织 | 20 组织独立训练 | 13 个 motif family，ETS 影响最高；免疫细胞中 ETS/1 高影响 | 方法具有跨组织泛化能力 | 未证明对所有组织类型均最优 | Results 节；Fig. 4 |
| 大脑远端调控元件 | 方法可扩展到非启动子序列 | scRNA+ATAC-seq 数据 | 38 个 motif family，MEF2 在谷氨酸能神经元中显示抑制性影响 | 方法适用于远端增强子分析 | 未与专门针对 ATAC-seq 的深度学习方法对比 | Results 节；Fig. 6 |
| 置换对照 | 结果非偶然 | 序列打乱 vs 原始 | 序列打乱后 R² 降至 5-7% | 模型确实学习了序列信息 | 未排除其他混杂因素 | Fig. S4 |

## 11 结论正确解读
- **任务范围**：scover 解决的是「给定一组序列及其关联的连续值（表达/可及性），发现调控 motif 并量化其贡献」的回归任务。它**不**做以下事情：(1) 不预测 TF 结合位点的精确位置（只给出 motif 级别的贡献）；(2) 不建模 motif 间的非线性交互（线性层假设加性贡献）；(3) 不处理剪接、表观遗传修饰等非序列信息。
- **oracle/真值输入**：训练标签是池化的基因表达值或染色质可及性值，这些来自真实单细胞实验测量，但经过 pooling 和 log 变换，属于「近似真值」。没有使用模拟数据或已知调控关系的 gold standard 进行验证。
- **端到端状态**：scover 是端到端可训练的（序列→预测值），但 motif 提取和 TF 关联是训练后的后处理步骤，不在端到端流程内。
- **算力成本**：单层 CNN 参数量极小（600×12×4 + 600×1000 ≈ 63 万参数），训练时间在 8×V100 GPU 上为数小时（原文仅提及"a few hours"），远低于 Enformer 等模型。
- **历史数据依赖**：模型仅依赖输入的序列和对应的表达/可及性数据，不依赖历史 ChIP-seq 或 motif 数据库。
- **模型依赖**：结果高度依赖 pooling 参数（k=100）、滤波器数量（600）和 motif 长度（12 bp）。改变这些超参数可能影响 motif 发现结果。
- **最难情形**：低表达基因（信号弱）、高度相似的 motif family（难以区分）、远端增强子（序列长度仅 240 bp 可能不足以捕获完整调控逻辑）。
- **群体/领域边界**：验证仅限于人类肾脏、小鼠 20 组织、人类大脑皮层。对植物、微生物或其他物种的适用性未验证。
- **不确定性**：influence score 的方差、motif 聚类的稳定性、TF 关联的假阳性率均未系统评估。

**有边界的复述**：scover 在三个单细胞数据集上，能够以约 15% 的预测 R² 从启动子序列预测基因表达，同时发现 13-16 个与已知生物学一致的 motif family，其性能优于 FIMO+回归/随机森林两阶段方法；但预测精度有限（85% 方差未解释），且未与最先进的深度学习方法（如 Enformer）进行直接对比。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 仅覆盖近端启动子 | 肾脏和 Tabula Muris 分析仅使用 ±500 bp 启动子，可能遗漏远端调控元件 | 未明确提及；[Analysis] 大脑 ATAC-seq 分析是对此的补充尝试 | Discussion 节 |
| 线性加性假设 | 线性层假设各 motif 对表达的贡献是加性的，无法建模协同/拮抗交互 | 未明确提及 | Methods 节（线性层设计） |
| 非匹配 motif 的生物学意义不明 | 大量滤波器未比对到已知 motif，可能是新 motif 或噪声 | 未明确提及 | Results 节（"we are unsure about the biological interpretation" 类似表述） |
| 计算成本高 | 600 个滤波器 × 10 折 × 10 次重复 = 60,000 次模型评估，超参数搜索耗时 | 未明确提及 | Methods 节（训练策略描述） |
| 仅适用于有连续读出的序列 | 需要表达或可及性作为训练标签，不适用于纯序列分类任务 | 未明确提及 | [Analysis] 从方法设计推断 |
| TF 关联仅为相关性 | 表达相关不能证明直接结合，可能存在间接效应 | 未明确提及 | Discussion 节（"we cannot rule out that multiple TFs correspond to the same motif cluster"） |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 预测 R² 仅 15% | 模型可能只捕获了启动子中少数强 motif 的贡献，大量调控信息未被利用；或 pooling 过程丢失了关键信息 | 若 R² 无法提升，scover 的实用价值仅限于 motif 发现，而非定量预测 | 尝试增加滤波器数量、motif 长度、或引入二阶特征后观察 R² 变化 | Results 节 R² 数据 |
| 与 FIMO+回归的对比可能不公平 | FIMO 使用默认阈值可能遗漏弱 motif 位点；线性回归未做特征选择 | 对比基准的公平性影响结论强度 | 对 FIMO 做阈值扫描，或使用更强大的基线（如 gkm-SVM） | Methods 节 FIMO 描述 |
| Leave-one-out 的线性近似 | 将滤波器权重置零假设了线性效应，但 CNN 中 ELU 和 max-pooling 引入非线性，实际影响可能非加性 | 若非线性效应显著，influence score 可能系统性偏差 | 用梯度归因方法（如 DeepLIFT）与 leave-one-out 结果对比 | Methods 节 influence score 定义 |
| 未报告置信区间 | 10 折交叉验证的 R² 波动范围未给出，无法判断模型稳定性 | 影响结论的可靠性 | 补充各折 R² 的标准差或置信区间 | Results 节（未提供） |
| 大脑 ATAC-seq 分析缺乏置换对照 | 仅报告了 R²=19%，未说明 scrambled sequence 对照的表现 | 无法确认该结果是否真的来自序列信号 | 补充大脑数据的置换实验 | Results 节；Fig. S4 仅显示肾脏和 Tabula Muris 的置换结果 |
| 未与单细胞专用深度学习方法对比 | 未与 scBasset、scEnformer 等可能存在的单细胞深度学习方法比较 | 无法判断 scover 是否代表该任务的最优方法 | 在相同数据上运行其他方法进行对比 | Background 节（未提及这些方法） |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **浅层 CNN 的可解释性红利**：scover 证明了在启动子调控预测任务中，单层卷积 + 全局最大池化足以达到有意义的预测性能（R²=15%），同时每个滤波器可直接提取为 PFM。这提示在 TF–DNA 结合机制研究中，**模型架构的选择应优先考虑可解释性**，而非盲目追求深度。可迁移到本课题：设计预测 TF 结合位点的模型时，可考虑浅层架构 + 显式 motif 提取层，而非端到端黑箱。

2. **Leave-one-out 扰动作为贡献归因**：通过将单个滤波器权重置零并测量预测变化，scover 将「预测贡献」转化为「生物学重要性」。这一策略比梯度归因更直接、更稳健，且计算成本低。可迁移到本课题：在评估某个 TF 结合 motif 对基因表达的调控强度时，可采用类似的扰动策略，而非仅依赖注意力权重或梯度。

3. **k-NN pooling 解决单细胞稀疏性**：不依赖细胞类型注释，而是通过几何采样 + k-NN 聚合构建「池」，既降低稀疏性又保留细胞类型异质性。可迁移到本课题：在单细胞 ATAC-seq 数据分析 TF 结合时，可借鉴此策略构建 pseudo-bulk 样本，提高信噪比。

4. **表达相关性辅助 TF 优先级排序**：scover 通过 motif influence score 与 TF 表达量的 Spearman 相关来推断最可能的结合 TF。这一策略简单有效，可迁移到本课题：当多个 TF 共享相似 motif 时，可用表达相关性作为初步筛选标准，再结合 DNA 序列特征（如 ChIP-seq 或 HT-SELEX 数据）进行精细区分。

5. **置换实验作为必要对照**：scover 通过序列核苷酸置换和池顺序置换两个对照，确认了模型确实学习了序列信息而非混杂因素。可迁移到本课题：任何基于序列的预测模型都应包含至少一种置换对照，以排除「记忆训练集」或「学习非序列特征」的假阳性。

6. **motif 聚类与数据库比对的流程**：scover 将 600 个滤波器归并为 motif family，再与 CIS-BP 比对。这一「从冗余滤波器到生物学 motif」的流程可迁移到本课题：在 de novo motif 发现后，应进行聚类去冗余和数据库注释，以提高结果的可解释性和可验证性。

## 15 与已有知识连接
- **与 BPNet (Avsec et al., 2021) 的关系**：BPNet 使用更深的架构（多卷积层 + 注意力）预测 ChIP-seq 峰值，并利用梯度归因提取 motif。scover 与之互补：BPNet 需要 bulk ChIP-seq 数据，scover 仅需 scRNA-seq/ATAC-seq。两者都强调从模型中提取可解释的 motif，但 scover 的 leave-one-out 策略比 BPNet 的梯度归因更直接。
- **与 Enformer (Avsec et al., 2021) 的关系**：Enformer 预测长程调控（100 kb 窗口），scover 仅处理局部序列（1 kb 启动子或 240 bp 开放染色质）。两者在任务尺度上互补，scover 的浅层架构更适合小样本单细胞数据。
- **与 SCENIC (Aibar et al., 2017) 的关系**：SCENIC 基于共表达网络和 motif 富集推断调控网络，依赖已知 motif 数据库（RcisTarget）。scover 的 de novo 能力可补充 SCENIC 在非模式生物中的不足。
- **与 Homer (Heinz et al., 2010) 的关系**：Homer 是经典的 motif 富集工具，需要预先定义背景集和已知 motif 数据库。scover 的 influence score 提供了比富集 p 值更定量的「贡献」度量。
- **与 CIS-BP (Weirauch et al., 2014) 的关系**：scover 依赖 CIS-BP 进行 motif 注释和 TF 关联，CIS-BP 的覆盖度直接影响 scover 的注释质量。
- **与单细胞 ATAC-seq 分析工具（如 SnapATAC、ArchR）的关系**：这些工具主要处理 peak calling 和细胞聚类，scover 提供了从 peak 序列到 motif 贡献的定量映射，可与之串联使用。
- **潜在冲突**：scover 的线性加性假设与已知的 TF 协同/拮抗效应（如 enhanceosome 模型）存在张力。本课题若关注 motif 间互作，需注意此局限。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合特异性的多模态整合模型
   - **来源局限/观察**：scover 仅使用序列信息预测表达，未整合 TF 浓度、染色质状态（如 H3K27ac、H3K4me1）等已知影响结合的因素。
   - **核心假设**：整合 TF 表达量和染色质可及性作为额外输入特征，可显著提升 motif influence score 的准确性和细胞类型特异性。
   - **初步方法**：扩展 scover 架构，在 CNN 输出后拼接 TF 表达向量和染色质状态向量，再通过线性层预测表达。在肾脏和 Tabula Muris 数据上对比有无额外特征的 R²。
   - **验证方式**：与 scover 原始结果对比；用已知的 TF–motif 互作（如 ENCODE ChIP-seq）验证 influence score 的排序准确性。
   - **创新状态**：unverified

2. **候选名称**：基于 influence score 的 TF–DNA 结合协同效应检测
   - **来源局限/观察**：scover 的线性层假设 motif 贡献加性，无法检测 motif 间的协同或拮抗。
   - **核心假设**：在启动子中同时出现的 motif 对（如 ETS + AP-1）存在非加性互作，可通过引入二阶交互项检测。
   - **初步方法**：在 scover 的线性层后添加 motif pair 的交互项（或使用因式分解机），比较有/无交互项的 R² 和 motif pair 的交互系数。
   - **验证方式**：用已知的协同 motif 对（如 SOX2–OCT4）验证交互系数方向；用 ChIP-seq 共结合数据验证。
   - **创新状态**：unverified

3. **候选名称**：跨物种 motif 调控保守性分析
   - **来源局限/观察**：scover 在人类和小鼠数据上发现的 motif family 有重叠，但未系统比较跨物种保守性。
   - **核心假设**：在人类和小鼠中均高影响的 motif 更可能是功能性保守的调控元件。
   - **初步方法**：分别训练人类肾脏和小鼠肾脏（Tabula Muris 中肾脏数据）的 scover 模型，比较 motif family 的 influence score 排序，计算跨物种保守性得分。
   - **验证方式**：与 UCSC 保守性分数（phastCons）对比；用 CRISPR 干扰验证保守 motif 的功能。
   - **创新状态**：unverified

4. **候选名称**：单细胞 ATAC-seq 的远端增强子–启动子配对调控模型
   - **来源局限/观察**：scover 在大脑 ATAC-seq 分析中仅独立处理每个开放染色质区域，未考虑增强子–启动子配对关系。
   - **核心假设**：将同一基因的启动子序列和远端增强子序列拼接作为输入，可捕获增强子对启动子表达的协同调控。
   - **初步方法**：使用 Hi-C 或共可及性分析确定增强子–启动子配对，将两个序列拼接后输入扩展版 scover。
   - **验证方式**：与仅启动子模型的 R² 对比；用 CRISPRi 干扰增强子验证预测。
   - **创新状态**：unverified

5. **候选名称**：基于 influence score 的致病非编码变异优先级排序
   - **来源局限/观察**：scover 的 influence score 可量化 motif 对表达的贡献，但未应用于变异效应预测。
   - **核心假设**：位于高 influence score motif 内的非编码变异更可能影响基因表达并导致疾病。
   - **初步方法**：对 GWAS 或 ClinVar 中的非编码变异，计算其所在 motif 的 influence score，并与变异致病性注释（如 CADD、FunSeq2）对比。
   - **验证方式**：用已知致病非编码变异（如 ALDOB 启动子变异）验证排序；用报告基因实验验证 top 变异。
   - **创新状态**：unverified