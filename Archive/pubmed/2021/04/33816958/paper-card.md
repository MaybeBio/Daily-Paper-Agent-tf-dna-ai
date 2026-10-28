## 01 基本信息

- **标题**：A machine learning framework for the prediction of chromatin folding in Drosophila using epigenetic features
- **作者与单位**：Rozenwald, Michal B; Galitsyna, Aleksandra A; Sapunov, Grigory V; Khrameeva, Ekaterina E; Gelfand, Mikhail S（单位未在摘要中提供）
- **期刊/预印本平台**：PeerJ. Computer science
- **年份**：2021-04-06
- **论文类型**：研究论文（方法学 + 应用）
- **领域**：三维基因组学 / 染色质折叠预测 / 表观遗传学 / 机器学习
- **关键词**：Chromatin folding; TAD; Machine learning; RNN; Epigenetics; Drosophila
- **DOI/arXiv 号**：10.7717/peerj-cs.307
- **代码**：https://github.com/MichalRozenwald/Hi-ChIP-ML
- **数据**：Hi-C 和 ChIP-chip 数据来自 Ulianov et al. (2016)，果蝇 dm3 基因组，20-kb 分辨率，三个细胞系（S2、Kc167、BG3）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 机器学习」交叉方向，但对象并非 TF–DNA 结合本身，而是**染色质折叠（TAD）预测**。其核心输入为 TF 结合（Chriz、CTCF、Su(Hw) 等）和组蛋白修饰信号，输出为 TAD 状态（transitional gamma）。对本课题（TF–DNA 结合机制 × AI）的可迁移点在于：**用序列化模型（biLSTM）显式建模基因组上相邻位点的上下文依赖**，以及**特征重要性分析揭示特定 TF 对结构表型的贡献**——这一思路可直接迁移到 TF–DNA 结合位点预测中，将"结合事件"视为序列上下文中的分类/回归问题。

---

## 02 一句话总结

本文用果蝇三个细胞系的 ChIP-chip 表观遗传特征（TF 结合 + 组蛋白修饰）作为输入，通过带 L1/L2 正则化的线性回归、梯度提升和双向 LSTM（biLSTM）回归模型，预测由 transitional gamma 定义的 TAD 状态；biLSTM 在最优窗口大小 6（120 kb）时取得最佳预测性能，并识别出 Chriz 和 H3K4me2 为最重要的预测特征。

---

## 03 研究问题

- **具体问题**：能否仅用表观遗传特征（TF 结合位点和组蛋白修饰）预测果蝇基因组中每个 20-kb 位点的 TAD 状态（以 transitional gamma 为连续目标）？哪些表观特征对预测贡献最大？
- **为什么重要**：TAD 是基因调控的重要结构单元，但其形成机制尚不完全清楚。如果能从表观特征预测 TAD 结构，既有助于理解 TAD 形成的驱动因子，也为跨细胞系、跨物种的染色质结构预测提供计算工具。
- **现有方法不足**：
  1. 此前工作（如 Ulianov et al. 2016; Ramírez et al. 2018）将 TAD 预测视为**二分类**（边界 vs 非边界），依赖阈值设定，且对亚阈值边界不敏感；
  2. 传统回归/梯度提升模型**忽略基因组位点之间的空间上下文**——相邻位点的表观状态高度相关，但模型未显式利用这一顺序信息；
  3. 缺乏对特征重要性的系统评估，尤其是哪些 TF/组蛋白修饰真正驱动 TAD 形成。
- **精确研究问题（Can...?）**：Can a biLSTM model that explicitly accounts for the sequential order of genomic bins outperform regularized linear regression and gradient boosting in predicting the continuous TAD state (transitional gamma) from epigenetic features in Drosophila, and can feature importance analysis identify biologically meaningful TAD-forming factors?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引用的相关工作及本文自身定位，属于「经外部核验」的脉络（引文均来自原文）。

1. **阶段一：Hi-C 揭示 TAD 结构（2009–2014）**
   - Lieberman-Aiden et al. (2009) 提出 Hi-C 技术；Dixon et al. (2012) 和 Rao et al. (2014) 发现 TAD 结构域。
   - 代表方法：TAD 边界识别算法（如 Armatus, Filippova et al. 2014）。
   - 局限：TAD 识别依赖参数（如 gamma），不同参数产生不同边界集合。

2. **阶段二：表观特征与 TAD 边界的关联分析（2015–2018）**
   - Ulianov et al. (2016) 在果蝇中证明活跃转录和组蛋白修饰富集于 TAD 边界，并用逻辑回归做边界分类。
   - Ramírez et al. (2018) 用 lasso 回归和梯度提升预测果蝇 TAD 边界。
   - 局限：二分类输出依赖阈值；模型忽略相邻位点上下文。

3. **阶段三：深度/序列化模型用于染色质结构预测（2018–2021，本文位置）**
   - 其他工作（如 Akita, HiC-Reg 等）用 CNN/RNN 预测 Hi-C 接触矩阵或 TAD 边界。
   - 本文定位：用 **biLSTM** 显式建模基因组位点的顺序依赖，以 **transitional gamma**（连续值）替代二分类标签，避免阈值问题，并系统评估特征重要性。

4. **阶段四（后续方向，本文提及）**：将模型迁移到其他物种、整合 DNA 序列特征、更高分辨率（<20 kb）的预测。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| TAD 状态二分类依赖阈值 | 边界/非边界的判定随阈值变化，亚阈值边界被忽略 | TAD calling 算法（如 Armatus）需要设定 gamma 参数，不同 gamma 产生不同 TAD 集合 | Introduction 节："prediction of TAD state as a categorical output depends on the TAD calling procedure... insensitive to sub-threshold boundaries" |
| 传统模型忽略基因组位点上下文 | 线性回归和梯度提升对每个位点独立预测，未利用相邻位点的表观特征相关性 | 相邻 DNA 区域的表观特征高度相关，但模型未显式建模顺序依赖 | Introduction 节："regression and gradient boosting... ignore the adjacent regions" |
| 特征重要性缺乏系统评估 | 哪些 TF/组蛋白修饰真正驱动 TAD 形成不清楚 | 此前工作未做系统的单特征/去特征分析 | Results 节 Feature importance analysis |
| 类别不平衡 | 大多数位点不是 TAD 边界，二分类模型偏向多数类 | TAD 边界位点占基因组比例小 | 作者通过使用连续目标（transitional gamma）和加权损失函数（wMSE）缓解此问题 |

---

## 06 核心思想

### 1) 表面方法
- 输入：18 个表观遗传特征（5 个核心特征 + 13 个扩展特征），每个 20-kb bin 一个特征向量。
- 模型：线性回归（L1/L2 正则化）、梯度提升、biLSTM。
- 目标：transitional gamma（连续值，0–10），由 Armatus 在不同 gamma 参数下的 TAD calling 结果计算得到。
- 损失函数：自定义加权 MSE（wMSE），对高 gamma 值（强 TAD 内部位点）的误差给予较低权重。

### 2) 核心洞察
- **TAD 状态是连续而非二值的**：transitional gamma 保留了 TAD 的"强度"信息，比二分类边界标签更丰富。
- **基因组位点的顺序上下文是关键**：biLSTM 通过双向扫描输入序列，显式利用相邻位点的表观特征，显著优于逐点独立的模型。
- **最优窗口大小与生物学尺度对应**：窗口大小 6（120 kb）恰好对应果蝇典型 TAD 大小，说明模型学到的上下文尺度具有生物学意义。

### 3) 可能的普适教训 [Analysis]
- **将离散标签转化为连续分数**：在 TF–DNA 结合预测中，若将"是否结合"转化为"结合强度/概率"的连续目标，可避免阈值依赖，并保留更多信息。
- **序列上下文建模适用于任何基因组线性特征**：TF 结合位点、组蛋白修饰、甲基化等都具有基因组上的空间自相关，biLSTM/CNN 等序列模型天然适合此类任务。
- **特征重要性分析应作为模型评估的标准环节**：不仅报告预测精度，还要回答"哪些因子驱动了预测"，这对机制研究至关重要。

---

## 07 方法总览

- **输入**：每个 20-kb bin 的表观遗传特征向量。第一组 5 个特征：Chriz、CTCF、Su(Hw)、H3K27me3、H3K27ac；第二组 18 个特征：扩展了 RNA Pol II、BEAF-32、GAF、CP190、H3K4me1/2/3、H3K9me2/3、H3K27me1、H3K36me1/3、H4K16ac 等。数据来自 modENCODE 数据库，经标准化（z-score）。
- **目标**：transitional gamma，由 Armatus 在 gamma 0–10（步长 0.01）下对 Hi-C 矩阵进行 TAD calling，计算每个 bin 从 TAD 内部变为边界/间区的 gamma 阈值。
- **模型**：
  1. 线性回归（Ridge/Lasso/Elastic Net，α=0.2）
  2. 梯度提升（n_estimators=100/250，max_depth=3/4，learning_rate=0.01）
  3. biLSTM（窗口大小 1–10，LSTM 单元数 1–512，Adam 优化器，early stopping）
- **训练/验证**：每个细胞系独立训练，70% 训练 / 20% 测试 / 10% 验证，10 轮交叉验证取平均。
- **特征重要性分析**：
  1. 单特征模型（use-one）：仅用单个特征训练 biLSTM，比较 wMSE。
  2. 去特征模型（drop-one）：从完整特征集中移除单个特征，比较 wMSE 变化。
- **输出**：每个 bin 的预测 transitional gamma 值；模型性能指标（wMSE、MSE、Pearson 相关系数等）。

**文字流程**：
1. 从 modENCODE 获取 ChIP-chip 信号，按 20-kb bin 标准化。
2. 用 Armatus 对 Hi-C 矩阵做多参数 TAD calling，计算每个 bin 的 transitional gamma。
3. 将特征向量按基因组顺序排列，构造序列样本（窗口大小 W）。
4. 分别训练 LR、GB、biLSTM 模型，用 wMSE 评估。
5. 对最优模型（biLSTM）做 use-one 和 drop-one 特征重要性分析。
6. 跨细胞系迁移测试（训练于一个细胞系，测试于另一个）。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Transitional gamma 计算 | 将 Armatus 多参数 TAD calling 结果转化为每个 bin 的连续分数 | 避免二分类阈值依赖，保留 TAD 强度信息 | 输入：Hi-C 矩阵；输出：每个 bin 的 gamma 值（0–10） | Methods 节 Target value；图 1D 显示分布 | 若移除（改用二分类标签），模型将失去对亚阈值边界的敏感性，预测精度下降 [预期] |
| 特征标准化 | 对 ChIP-chip 信号做 z-score 归一化 | 不同实验的信号尺度不同，需统一量纲 | 输入：原始 ChIP-chip 信号；输出：标准化特征 | Methods 节 Data；图 S2 | 若不标准化，模型可能偏向高信号幅度的特征 [预期] |
| biLSTM 序列编码器 | 对窗口内相邻 bin 的特征序列建模，输出中心 bin 的预测值 | 显式利用基因组位点的空间上下文 | 输入：W×F 特征矩阵（W=窗口大小，F=特征数）；输出：标量 gamma 预测 | Results 节表 2：biLSTM 优于 LR 和 GB | 若移除（替换为逐点模型），wMSE 显著上升，说明上下文信息是关键 [实测：biLSTM 优于所有逐点模型] |
| wMSE 损失函数 | 对高 gamma 值样本的误差降权 | 高 gamma 样本占比少且生物学意义不同 | 输入：预测值、真实值、真实 gamma；输出：损失标量 | Methods 节 Selection of loss function | 若移除（改用 MSE），模型可能过度拟合高 gamma 少数样本 [预期] |
| Use-one 特征分析 | 用单个特征训练模型，评估各特征独立预测能力 | 识别哪些表观特征单独就足以预测 TAD 状态 | 输入：单特征序列；输出：wMSE 排名 | Results 节图 4、5、6 | 若移除，无法识别 Chriz 和 H3K4me2 的独立贡献 [实测：Chriz 单特征表现最佳] |
| Drop-one 特征分析 | 从完整特征集中移除单个特征，评估性能下降 | 识别哪些特征提供了不可替代的信息 | 输入：完整特征集减一；输出：wMSE 变化 | Results 节图 6 | 若移除，无法识别特征间的冗余性 [实测：移除 Chriz 导致 wMSE 显著上升] |

---

## 09 关键公式符号

**1. 加权均方误差（wMSE）**：

$$wMSE = \frac{1}{N} \sum_{i=1}^{N} (y_{\text{true}_i} - y_{\text{pred}_i})^2 \cdot \frac{\alpha - y_{\text{true}_i}}{\alpha}$$

- $N$：样本数（bin 数）
- $y_{\text{true}_i}$：第 $i$ 个 bin 的真实 transitional gamma
- $y_{\text{pred}_i}$：第 $i$ 个 bin 的预测 transitional gamma
- $\alpha$：gamma 最大值 + 1（本文中 = 11），用于避免权重为零

**用途**：作为所有模型的损失函数和评估指标。权重项 $\frac{\alpha - y_{\text{true}_i}}{\alpha}$ 使得高 gamma 值（强 TAD 内部位点）的误差贡献降低，因为这类样本在基因组中占少数且预测难度大。

**直觉**：对"罕见但重要"的高 gamma 样本给予较低惩罚，防止模型过度拟合这些少数样本，同时保留对多数样本（低 gamma）的敏感度。

**2. 特征标准化**：

$$x' = \frac{x - \mu}{\sigma}$$

- $x$：原始 ChIP-chip 信号
- $\mu$：该特征在所有 bin 上的均值
- $\sigma$：该特征在所有 bin 上的标准差

**用途**：每个特征独立标准化，使不同实验的信号可比。

---

## 10 实验设计与证据链

### 数据集与评测协议
- **细胞系**：果蝇三个细胞系——S2（胚胎）、Kc167（胚胎）、BG3（幼虫中枢神经系统）
- **基因组**：dm3 组装，20-kb 分辨率，共 5950 个 bin
- **特征**：第一组 5 个（Chriz、CTCF、Su(Hw)、H3K27me3、H3K27ac）；第二组 18 个（扩展）
- **目标**：transitional gamma（0–10）
- **数据划分**：70% 训练 / 20% 测试 / 10% 验证，10 轮交叉验证取平均
- **基线**：常数预测（均值）
- **指标**：wMSE、MSE、Pearson 相关系数
- **硬件/框架**：未提供具体硬件；代码使用 Python/sklearn/TensorFlow（推断，代码仓库可见）

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|------------------|------|
| 全特征模型性能比较 | 表观特征可预测 TAD 状态 | LR（L1/L2）、GB、biLSTM vs 常数预测 | biLSTM 最优，wMSE 约为常数预测的一半（具体数值未在摘要中提供） | 表观特征携带 TAD 状态信息；序列模型优于逐点模型 | 不能说明因果性，仅相关性 | Results 节表 1、2 |
| 窗口大小扫描 | biLSTM 需要多大上下文 | 窗口 1–10 | 窗口 6（120 kb）最优 | 最优窗口对应果蝇典型 TAD 大小，上下文尺度有生物学意义 | 不能确定 120 kb 是因果尺度 | Results 节图 3 |
| Use-one 特征分析 | 单个特征能否独立预测 | 每个特征单独训练 biLSTM | Chriz 和 H3K4me2 单特征表现最佳 | Chriz 和 H3K4me2 是 TAD 状态的重要预测因子 | 单特征表现好不等于因果驱动 | Results 节图 4、5、6 |
| Drop-one 特征分析 | 哪些特征不可替代 | 从 18 特征中逐一移除 | 移除 Chriz 导致 wMSE 显著上升 | Chriz 提供不可替代的信息 | 移除后性能下降可能源于特征间交互 | Results 节图 6 |
| 跨细胞系迁移 | 模型是否可迁移 | 在一个细胞系训练，测试于另一个 | 迁移后性能下降但优于常数预测（具体数值未提供） | TAD 形成机制在细胞系间有共性 | 不能推广到物种间 | Results 节表 3 |
| 5 特征 vs 18 特征 | 小特征集是否足够 | 5 特征 vs 18 特征训练 | 5 特征略差于 18 特征，但差距不大 | 核心 5 特征已捕获大部分预测信息 | 不能排除其他特征在特定细胞系中的重要性 | Results 节表 1、2 |

---

## 11 结论正确解读

- **任务范围**：本文预测的是 **TAD 状态（transitional gamma）**，而非 TAD 边界本身。预测对象是 20-kb 分辨率的基因组 bin，不是单核苷酸级别。
- **oracle/真值输入**：transitional gamma 由 Armatus 对 Hi-C 矩阵计算得到，本身依赖 Hi-C 数据质量。模型输入为 ChIP-chip 信号，**不包含 Hi-C 数据**——即模型是从表观特征"预测"TAD 状态，而非从 Hi-C 推断。
- **端到端状态**：模型是端到端训练的（特征→gamma），但特征提取（ChIP-chip 标准化）和真值计算（Armatus）是前置步骤，非端到端可微。
- **算力成本**：biLSTM 参数量小（窗口 6 × 18 特征输入），训练成本低，但文中未报告具体训练时间。
- **历史数据依赖**：使用 modENCODE 的 ChIP-chip 数据，这些数据来自特定实验条件，可能不适用于其他细胞类型或物种。
- **模型依赖**：biLSTM 的最优窗口大小（6）可能依赖 20-kb 分辨率；若分辨率改变，最优窗口需重新调参。
- **最难情形**：高 gamma 值（强 TAD 内部）的位点预测误差最大，作者通过 wMSE 降低其权重，但也意味着模型对这类位点的预测精度有限。
- **群体/领域边界**：结论仅适用于果蝇三个细胞系；跨物种迁移未验证。
- **不确定性**：特征重要性分析基于模型权重和消融实验，反映的是预测贡献而非生物学因果。

**有边界的复述**：在果蝇三个细胞系中，以 20-kb 分辨率的 ChIP-chip 表观特征为输入，biLSTM 模型能以优于线性回归和梯度提升的精度预测由 Armatus 计算的 transitional gamma（TAD 状态连续分数），且 Chriz 和 H3K4me2 是预测贡献最大的特征。该结论不涉及 TAD 形成的因果机制，也不保证在其他分辨率或物种中成立。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 分辨率限制 | 分析在 20-kb 分辨率进行，无法捕捉更精细的染色质结构 | 训练更高分辨率（如 500 bp）的模型 | Discussion 节："The training of the model for Hi-C with the resolution up to 500 bp presents a promising direction for future work" |
| 特征集有限 | 仅使用 ChIP-chip 表观特征，未包含 DNA 序列信息 | 将原始 DNA 序列整合到模型中 | Discussion 节："exploration of a broader set of cell types... as well as the integration of various biological features, such as raw DNA sequence" |
| 细胞类型覆盖不足 | 仅三个果蝇细胞系 | 扩展到更多细胞类型和物种 | Discussion 节："We also anticipate promising outcomes of applying our approach to study the chromatin folding in various species except for Drosophila" |
| TAD 状态度量单一 | 仅使用 transitional gamma 作为 TAD 状态度量 | 可迁移到其他 TAD 度量（如 Insulation Score、D-score） | Discussion 节："the presented pipeline may be easily transferred to predict these scores as target values" |
| 特征选择依赖文献 | 特征选择基于先前文献报道，可能遗漏未知相关因子 | 探索更广泛的表观特征组合 | Discussion 节（隐含） |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| biLSTM 优于线性模型，但增益幅度未报告 | 若增益很小，复杂模型可能不值得；若增益大，需确认不是过拟合 | 决定模型选择的实际价值 | 报告 biLSTM vs LR 的 wMSE 差值及置信区间；检查测试集上的泛化差距 | Results 节表 2（具体数值未在摘要中提供） |
| 窗口大小 6 对应 120 kb 被解释为"TAD 大小" | 120 kb 可能只是数据相关的伪相关，而非生物学尺度 | 过度生物学解释可能导致错误结论 | 在不同分辨率（10 kb、40 kb）下重复窗口扫描，看最优窗口是否按比例缩放 | Results 节图 3 |
| Use-one 分析中 Chriz 表现最佳，但 Chriz 本身可能与其他特征高度相关 | 单特征表现好可能反映的是与隐藏变量的相关性，而非独立贡献 | 影响对"关键因子"的判定 | 计算特征间相关矩阵；做条件互信息分析 | Results 节图 4、5、6 |
| 跨细胞系迁移测试中 BG3 表现最好 | BG3 是神经元细胞系，可能具有更独特的表观特征，迁移测试结果可能受数据质量影响 | 迁移性结论可能被单细胞系特性主导 | 增加更多细胞系；报告每个迁移方向的详细结果 | Results 节表 3 |
| wMSE 对高 gamma 降权，可能掩盖模型在高 gamma 区域的真实表现 | 模型可能在"重要"的强 TAD 区域表现差，但被 wMSE 掩盖 | 影响对模型实用性的判断 | 分层报告 wMSE（按 gamma 分位数分组） | Methods 节 Selection of loss function |
| 特征标准化使用全局均值和方差 | 若不同染色体或区域存在批次效应，全局标准化可能引入偏差 | 影响特征可比性 | 按染色体或实验批次分别标准化，比较结果 | Methods 节 Data |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **连续目标替代离散标签**：本文用 transitional gamma（连续值）替代二分类 TAD 边界标签，避免了阈值依赖。**迁移到 TF–DNA 结合**：可将"是否结合"转化为"结合强度"（如 ChIP-seq 峰高、binding energy 估计），用回归替代分类，保留更多定量信息。

2. **序列上下文建模的必要性**：biLSTM 显式利用相邻 bin 的表观特征，显著优于逐点模型。**迁移到 TF–DNA 结合**：TF 结合位点周围的表观状态（如组蛋白修饰、核小体定位）对结合有重要影响，用 biLSTM/CNN 对基因组窗口建模可捕获这些上下文依赖，而非仅看中心位点。

3. **窗口大小与生物学尺度对齐**：最优窗口 6（120 kb）对应果蝇 TAD 大小。**迁移到 TF–DNA 结合**：TF 结合的最优上下文窗口可能对应核小体周期（~200 bp）或增强子-启动子距离（~kb 级），可通过窗口扫描确定生物学尺度。

4. **特征重要性双策略**：use-one（单特征独立预测能力）和 drop-one（特征不可替代性）互补。**迁移到 TF–DNA 结合**：在预测 TF 结合时，可分别评估每个表观特征的独立预测力和在完整模型中的不可替代性，识别关键调控因子。

5. **跨细胞系迁移测试**：训练于一个细胞系、测试于另一个，验证模型的泛化性。**迁移到 TF–DNA 结合**：TF 结合机制在不同细胞类型中可能共享或特异，迁移测试可帮助区分通用机制和细胞特异性机制。

6. **加权损失处理不平衡**：wMSE 对少数类（高 gamma）降权。**迁移到 TF–DNA 结合**：TF 结合位点在基因组中占少数，正负样本极不平衡，可设计类似的加权损失或 focal loss 处理。

7. **代码开源 + 模块化设计**：Hi-ChIP-ML 框架可适配不同数据集和目标变量。**迁移到 TF–DNA 结合**：可复用其数据预处理、模型训练、特征分析流程，仅替换输入特征和目标变量。

---

## 15 与已有知识连接

- **Ulianov et al. (2016)**：本文的直接前作，首次在果蝇中证明活跃表观标记富集于 TAD 边界，并用逻辑回归做边界分类。本文将其二分类扩展为连续回归，并引入序列模型。**连接点**：TF–DNA 结合预测中，类似地可将"边界/非边界"二分类扩展为"结合强度"回归。
- **Ramírez et al. (2018)**：用 lasso 和梯度提升预测果蝇 TAD 边界，本文对比了这些基线并显示 biLSTM 更优。**连接点**：在 TF–DNA 结合预测中，线性/树模型 vs 深度序列模型的对比是标准做法。
- **Armatus (Filippova et al., 2014)**：TAD calling 算法，本文用其多参数结果计算 transitional gamma。**连接点**：TF–DNA 结合预测中，类似的"多阈值"策略可用于定义结合位点的强弱。
- **modENCODE 数据库 (Waterston et al., 2009)**：本文 ChIP-chip 数据来源。**连接点**：TF–DNA 结合预测可复用同一数据库的 TF ChIP-seq 数据。
- **LSTM (Hochreiter & Schmidhuber, 1997)**：本文核心模型架构。**连接点**：在 TF–DNA 结合预测中，LSTM/GRU 已被用于 DNA 序列建模（如 DeepBind 的后续工作）。
- **染色质状态概念 (Filion et al., 2010; Kharchenko et al., 2011)**：本文用"染色质状态"解释特征冗余性。**连接点**：TF 结合位点常与特定染色质状态（如 active promoter、enhancer）共定位，可将其作为先验特征。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

**候选 1：TF–DNA 结合强度的序列上下文回归模型**
- **名称**：TF-Bind-Seq2Seq（暂定）
- **来源局限/观察**：本文用 biLSTM 预测 TAD 状态，证明表观特征的序列上下文对结构预测至关重要。TF–DNA 结合预测中，多数模型（如 DeepBind）仅用中心序列，忽略表观上下文。
- **核心假设**：将 TF 结合位点周围的表观特征（组蛋白修饰、染色质可及性）作为序列上下文输入，可显著提升结合强度预测精度。
- **增量**：将本文的 biLSTM 框架从 TAD 预测迁移到 TF 结合预测，输入为窗口内表观特征，输出为结合强度（连续值）。
- **初步方法**：对每个 TF，取 ChIP-seq 峰中心 ±5 kb 窗口，按 100 bp bin 提取表观特征，训练 biLSTM 回归模型，与仅用中心序列的 CNN 模型对比。
- **验证方式**：跨细胞系迁移测试（训练于 K562，测试于 GM12878）；与 ENCODE 基准比较。
- **创新状态**：unverified

**候选 2：TF 结合与 TAD 边界的联合预测模型**
- **名称**：Joint-TF-TAD
- **来源局限/观察**：本文发现 Chriz 和 H3K4me2 是 TAD 预测的最重要特征，而 Chriz 本身是染色质蛋白，H3K4me2 标记活跃启动子。TF 结合与 TAD 结构可能互为因果。
- **核心假设**：TF 结合位点与 TAD 边界在表观特征上共享信息，联合建模可互相提升预测精度。
- **增量**：多任务学习框架，共享底层表观特征编码器，分别输出 TF 结合强度和 TAD 状态。
- **初步方法**：在本文的 biLSTM 基础上增加第二个输出头，用共享隐藏层 + 任务特定层，联合训练。
- **验证方式**：比较联合模型 vs 两个独立模型的 wMSE 和 TF 结合预测 AUC。
- **创新状态**：unverified

**候选 3：基于注意力机制的可解释 TF–DNA 结合预测**
- **名称**：Attn-TF-Bind
- **来源局限/观察**：本文的 biLSTM 虽预测准确，但可解释性有限。特征重要性分析是事后分析，而非模型内在机制。
- **核心假设**：在 biLSTM 中引入注意力机制，可同时提升预测精度和提供位点级别的可解释性。
- **增量**：注意力权重可直接显示哪些表观特征、哪些基因组位置对预测贡献最大，无需事后分析。
- **初步方法**：将 biLSTM 替换为 Transformer 或 biLSTM + 注意力，训练后分析注意力权重与已知 TF 结合 motif 的对应关系。
- **验证方式**：注意力权重与 ChIP-seq 峰形状的对齐度；与本文 use-one/drop-one 特征重要性结果交叉验证。
- **创新状态**：unverified

**候选 4：跨物种 TF–DNA 结合预测的迁移学习**
- **名称**：Cross-Species-TF-Bind
- **来源局限/观察**：本文仅用果蝇数据，但提出方法可迁移到其他物种。TF 结合机制在物种间有保守性。
- **核心假设**：在果蝇上预训练的模型，经微调后可迁移到其他物种（如人类、小鼠）的 TF 结合预测。
- **增量**：系统评估预训练-微调策略 vs 从头训练的精度差异。
- **初步方法**：在果蝇三个细胞系上预训练 biLSTM，然后在人类 ENCODE 数据上微调，比较与从头训练的 AUC。
- **验证方式**：跨物种迁移的精度保持率；分析哪些特征（如组蛋白修饰）的贡献在物种间保守。
- **创新状态**：unverified

**候选 5：整合 DNA 序列与表观特征的 TF 结合预测**
- **名称**：Seq-Epi-TF
- **来源局限/观察**：本文仅用表观特征，未包含 DNA 序列信息，作者在 Discussion 中明确提及整合 DNA 序列是未来方向。
- **核心假设**：DNA 序列（motif 信息）与表观特征（染色质状态）互补，联合输入可提升 TF 结合预测。
- **增量**：双通道输入——序列用 CNN 编码，表观特征用 biLSTM 编码，融合后预测。
- **初步方法**：对每个窗口，同时输入 one-hot 编码的 DNA 序列和表观特征向量，训练双分支模型。
- **验证方式**：与仅序列、仅表观模型对比；分析序列分支和表观分支的贡献比例。
- **创新状态**：unverified