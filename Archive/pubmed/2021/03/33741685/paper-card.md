## 01 基本信息
- **标题**: Fast decoding cell type-specific transcription factor binding landscape at single-nucleotide resolution
- **作者与单位**: Li, Hongyang; Guan, Yuanfang（密歇根大学，计算医学与生物信息学系）
- **期刊/预印本平台**: Genome Research
- **年份**: 2021
- **论文类型**: 研究论文（方法学）
- **领域**: 计算基因组学；深度学习；转录因子结合位点预测
- **关键词**: transcription factor binding, deep learning, single-nucleotide resolution, cell type-specific, DNase-seq, U-Net
- **DOI/arXiv 号**: 10.1101/gr.269613.120
- **代码**: https://github.com/GuanLab/Leopard
- **数据**: ENCODE 项目 ChIP-seq（51 个实验）、DNase-seq（13 个细胞系）、ChIP-exo（6 个实验）
- **阅读日期**: 未提供
- **在课题方向中的位置**: 本文属于「TF–DNA 结合机制 × 深度学习」方向，核心贡献是将图像分割领域的 U-Net 架构迁移到一维基因组序列，实现跨细胞类型的单核苷酸分辨率 TF 结合位点预测，并引入 ΔDNase-seq 特征以捕捉细胞类型特异的染色质开放性。与 Anchor、FactorNet 等方法的对比表明，多对多架构在精度和速度上均优于多对一架构。

## 02 一句话总结
本文提出深度学习模型 Leopard，以 DNA 序列和 DNase-seq 信号为输入，通过 U-Net 风格的多对多卷积神经网络架构，在单核苷酸分辨率下预测跨细胞类型的 TF 结合位点，平均 AUROC 达 0.982，较 Anchor 和 FactorNet 分别提升 AUPRC 19% 和 27%，并实现百倍至千倍的速度提升。

## 03 研究问题
- **具体问题**: 如何在单核苷酸分辨率下、跨细胞类型准确预测 TF 结合位点？
- **为什么重要**: TF 结合位点的细胞类型特异性是理解基因调控和疾病机制的关键；高分辨率实验（如 ChIP-exo）成本高、通量低，无法覆盖所有 TF–细胞类型组合。
- **现有方法不足**: 
  - 基于 motif 扫描的方法（如 FIMO）无法区分同源 motif 的 TF，且对间接结合（tethering）事件失效；
  - 已有深度学习方法（如 Anchor、FactorNet）采用多对一架构，一次只能预测一个位点，速度慢且分辨率低（通常为 200 bp）；
  - 序列-only 方法无法捕捉细胞类型特异的染色质状态。
- **精确研究问题 (Can...?)**: Can a many-to-many deep learning architecture, leveraging complete DNase-seq signals and DNA sequence, predict cell type-specific TF binding sites at single-nucleotide resolution with higher accuracy and speed than existing many-to-one methods?

## 04 背景与发展脉络
*注：以下脉络基于本文框架及引文，部分经外部核验。*

1. **序列基序时代（~2010s 前）**: 基于位置权重矩阵（PWM）的 motif 扫描（如 FIMO）是主流方法。局限：无法区分同源 motif、无法处理间接结合、无细胞类型信息。
2. **传统机器学习（~2010s）**: gkmSVM 等基于 k-mer 特征的方法，提升了序列特征利用效率，但仍缺乏染色质上下文。
3. **深度学习初期（~2015-2018）**: DeepSEA、Basset 等 CNN 模型从序列预测调控功能，但输出为粗粒度（如 200 bp bin），且多为多对一架构。
4. **多对一集成方法（~2018-2019）**: Anchor（XGBoost + 特征工程）和 FactorNet（多对一神经网络）在 ENCODE-DREAM 挑战赛中表现优异，但速度慢、分辨率低。
5. **多对多架构（本文，2021）**: Leopard 将 U-Net 从图像分割迁移到一维基因组序列，实现单碱基输出；引入 ΔDNase-seq 特征捕捉细胞类型差异；利用 GEM peak caller 获得高分辨率标签。
6. **后续方向（本文展望）**: 多对多架构可推广至其他表观遗传修饰预测；结合 DeepLIFT 等可解释性方法可进一步提升模型理解。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 分辨率不足 | 已有方法仅能预测 200 bp 级别的结合区域，无法定位精确结合位点 | 多对一架构输出为 bin 级别标签；ENCODE-DREAM 挑战赛的评测标准即为 200 bp | Results "Leopard substantially outperforms..." 节；Methods "Method comparison at 200-bp resolution" 节 |
| 速度瓶颈 | 多对一模型需逐位点滑动窗口预测，全基因组预测需数天 | 每个输入窗口仅产生一个输出，计算冗余 | Results "Overview of experimental design" 节；Discussion 节 |
| 细胞类型特异性缺失 | 序列-only 模型无法区分不同细胞类型中的结合差异 | DNA 序列不包含染色质状态信息 | Results "Leopard accurately identifies..." 节（GM12878 vs. liver 对比） |
| 标签噪声 | ChIP-seq 峰通常为宽峰（数百 bp），难以定义单碱基金标准 | 传统 peak caller 输出宽峰；ChIP-exo 数据有限 | Methods "Data collection and preprocessing" 节（使用 GEM 提取高分辨率峰） |
| motif 依赖 | 基于 motif 的方法对无明确 motif 的 TF（如间接结合）失效 | 间接结合不依赖 TF 自身 motif | Results "Leopard accurately identifies..." 节（对比 FIMO 基线） |
| 类别不平衡 | 全基因组中结合位点极稀疏（平均 0.0156%），导致 AUPRC 极低 | 正负样本比例严重失衡 | Results "Leopard accurately identifies..." 节（AUPRC 基线 0.000156） |

## 06 核心思想
1. **表面方法**: 构建一个一维 U-Net 架构的深度卷积神经网络，输入为 6×10,240 的矩阵（4 通道 one-hot DNA 序列 + 2 通道 DNase-seq/ΔDNase-seq 信号），输出为 1×10,240 的单碱基结合概率。
2. **核心洞察**:
   - **多对多架构是关键**: 与多对一模型（一个窗口一个输出）不同，多对多模型同时输出窗口内所有位置的预测，既提升速度又允许模型利用上下文信息。
   - **ΔDNase-seq 特征设计**: 通过减去所有细胞系的平均信号，ΔDNase-seq 能突出细胞类型特异的染色质开放性差异，这是跨细胞类型预测的关键信息。
   - **GEM 高分辨率标签**: 使用 GEM peak caller 从 ChIP-seq 原始比对文件中提取单碱基级别的峰，解决了宽峰标签导致的训练信号模糊问题。
   - **U-Net 的跳跃连接**: 编码器-解码器结构配合 concatenation 操作，在保留高分辨率位置信息的同时整合多尺度上下文。
3. **可能的普适教训 [Analysis]**: 将图像分割领域的架构迁移到一维基因组问题时，关键在于保持「输入-输出分辨率一致」的设计原则；特征工程（如 ΔDNase-seq）与深度学习架构的互补性仍不可忽视。

## 07 方法总览
- **输入**: 
  - DNA 序列（one-hot 编码，4 通道）
  - DNase-seq 信号（1 通道）
  - ΔDNase-seq 信号（1 通道，即该细胞系信号减去所有细胞系平均）
  - 总输入维度：6 × 10,240 bp
- **输出**: 1 × 10,240 的单碱基结合概率（sigmoid 激活）
- **模型架构**: 一维 U-Net
  - 编码器：5 个 conv-conv-pool (ccp) 块，通道数从 6 增至 109，长度从 10,240 降至 320
  - 解码器：5 个 up-conv-conv (ucc) 块，逐步恢复分辨率
  - 跳跃连接：编码器各层输出与解码器对应层 concatenation
  - 卷积核大小：7
  - 池化：max pooling
- **训练**:
  - 损失函数：交叉熵（binary cross-entropy）
  - 优化器：Adam
  - 学习率：1e-3（前 5 epoch），1e-4（后 15 epoch）
  - 每个 epoch：100,000 个随机采样的 10,240 bp 窗口
- **标签定义**: 正样本 = 位于 GEM 峰内且为 FIMO motif 命中位点；负样本 = 其余位置
- **评测协议**: 
  - ChIP-seq 数据：23 个测试 TF–细胞类型对，跨细胞类型训练（28 个训练对）
  - ChIP-exo 数据：6 个测试对，同细胞类型跨染色体训练
  - 固定测试染色体：Chr 1, 8, 21
- **工具**: GEM peak caller（参数：--s 2000000000 --k_min 6 --k_max 13）；FIMO（motif 扫描）；Python keras-vis（saliency map）
- **反馈回路**: 无显式主动学习或迭代优化；saliency map 用于事后解释

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ΔDNase-seq 特征 | 捕捉细胞类型特异的染色质开放性差异 | 原始 DNase-seq 信号含全局偏差，Δ 变换可突出细胞间差异 | 输入：某细胞系 DNase-seq 信号；输出：减去所有细胞系平均后的差值信号 | Methods "ΔDNase-seq Feature" 节；Supplemental Fig. S8（不同参考细胞系数量下 Δ 特征稳定性） | [预期] 移除后跨细胞类型预测能力下降，因模型无法区分不同细胞类型的染色质状态 |
| 一维 U-Net 编码器 | 逐步下采样提取多尺度特征 | 需要同时捕捉局部 motif 和远端调控信息 | 输入：6×10,240；输出：109×320 特征图 | Methods "The Neural Network Architecture of Leopard" 节；Supplemental Table S1 | [预期] 移除深层编码器将丧失长程上下文信息，短输入窗口模型性能下降（见 Supplemental Fig. S9 输入长度实验） |
| 跳跃连接（concatenation） | 将编码器高分辨率特征传递到解码器 | 防止下采样导致的位置信息丢失 | 编码器各层输出 → 解码器对应层 | Methods 节（U-Net 结构描述） | [预期] 移除后单碱基定位精度下降，因解码器无法恢复精细位置信息 |
| 解码器（ucc 块） | 逐步上采样恢复原始分辨率 | 实现单碱基输出 | 输入：编码器特征 + 跳跃连接；输出：1×10,240 | Methods 节 | [预期] 移除后无法输出单碱基预测，退化为低分辨率模型 |
| GEM peak caller | 从 ChIP-seq 比对文件提取高分辨率峰 | 传统宽峰标签无法训练单碱基模型 | 输入：ChIP-seq BAM 文件；输出：单碱基峰 | Methods "Data collection and preprocessing" 节 | [预期] 使用传统宽峰标签将降低模型定位精度，因训练信号模糊 |
| 多对多输出层 | 同时输出窗口内所有位置的预测 | 核心创新，实现速度提升和上下文利用 | 输入：解码器最终特征；输出：10,240 个概率值 | Results "Leopard substantially outperforms..." 节（速度对比）；Supplemental Fig. S6（多对一版本对比） | [实测] 多对一版本速度慢百倍以上（图 4B），且精度略低 |

## 09 关键公式符号
1. **交叉熵损失**:
   \[
   H(y, \hat{y}) = \sum_{i=1}^{N} \left[ -y_i \cdot \log \hat{y}_i - (1 - y_i) \cdot \log(1 - \hat{y}_i) \right]
   \]
   - \( y_i \): 位置 i 的金标准标签（0 或 1）
   - \( \hat{y}_i \): 位置 i 的预测概率
   - \( N = 10,240 \): 窗口长度

2. **ReLU 激活**:
   \[
   f(x) = \max(0, x)
   \]

3. **Sigmoid 激活**（输出层）:
   \[
   f(x) = \frac{1}{1 + e^{-x}}
   \]

4. **总体 AUPRC**:
   \[
   \text{AUPRC} = \sum_j P_j (R_j - R_{j+1})
   \]
   - \( P_j \): 在 cutoff j 处的精确率（precision）
   - \( R_j \): 在 cutoff j 处的召回率（recall）
   - cutoff 序列: \( j = 0, 0.001, 0.002, \ldots, 0.998, 0.999, 1.000 \)

5. **精确率与召回率**:
   \[
   \text{Precision} = \frac{TP}{TP + FP}, \quad \text{Recall} = \frac{TP}{TP + FN}
   \]
   - TP: 真阳性，FP: 假阳性，FN: 假阴性

## 10 实验设计与证据链
- **数据集**: 
  - 训练：28 个 ChIP-seq 实验（10 个 TF × 多个细胞系）
  - 测试：23 个 ChIP-seq 实验（跨细胞类型）
  - ChIP-exo 验证：6 个实验（CTCF, NR2F2, ER, EP300, GR×2）
  - DNase-seq：13 个细胞系
  - 基因组：hg19 (GRCh37)
- **指标**: AUROC, AUPRC（整体及部分曲线）
- **基线**: Anchor, FactorNet, DeepSEA, Basset, gkmSVM
- **评测协议**: 固定测试染色体（Chr 1, 8, 21）；跨细胞类型训练-测试划分；200 bp 分辨率对比实验
- **预算/资源**: 未提供具体 GPU 型号；速度对比实验在相同硬件条件下进行

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 跨细胞类型 ChIP-seq 预测 | Leopard 在单碱基分辨率下准确预测 TF 结合 | 23 个测试对；与 Anchor、FactorNet 对比 | 平均 AUROC = 0.982；AUPRC 较 Anchor 提升 19%，较 FactorNet 提升 27% | Leopard 显著优于已有方法 | 未与所有可能方法对比；AUPRC 绝对值仍低（0.208） | Results 图 2A-D |
| ChIP-exo 验证 | 单碱基分辨率预测具有生物学意义 | 6 个 ChIP-exo 实验；计算预测与 ChIP-exo 峰距离 | 70% 以上预测位点与 ChIP-exo 峰中心距离为 0 bp | Leopard 预测精度达到单碱基水平 | ChIP-exo 数据量有限，可能不代表所有 TF | Results 图 3E |
| 200 bp 分辨率对比 | 在低分辨率任务中 Leopard 仍优于 SOTA | ENCODE-DREAM 挑战赛数据集；与 Anchor、FactorNet 对比 | Leopard 平均 AUPRC 最高 | 多对多架构在低分辨率下同样有效 | 200 bp 分辨率下优势小于单碱基分辨率 | Results 图 4A |
| 速度对比 | 多对多架构显著加速 | 全基因组预测；与多对一版本、Anchor 对比 | Leopard <1h (GPU) / 4h (CPU)；多对一需 583.6h；Anchor 需 1220.8h | 多对多架构实现百倍至千倍加速 | 速度对比仅在特定硬件条件下 | Results 图 4B；Supplemental Fig. S7 |
| 输入长度实验 | 长输入提升性能 | 512/1024/5120/10240/20480 bp 输入 | 10,240 bp 和 20,480 bp 性能最高 | 长程上下文对 TF 结合预测重要 | 20,480 bp 相比 10,240 bp 提升不显著 | Supplemental Fig. S9, S10 |
| ΔDNase-seq 特征消融 | Δ 特征对跨细胞类型预测必要 | 有/无 ΔDNase-seq 特征对比 | 未提供具体数值 | [作者主张] Δ 特征提升跨细胞类型性能 | 消融实验细节未充分展示 | 未提供（作者在 Methods 中描述设计动机） |

## 11 结论正确解读
- **任务范围**: 本文解决的是「跨细胞类型」TF 结合位点预测，即模型在训练时未见过的细胞类型上进行预测。这比同细胞类型预测更具挑战性。
- **oracle/真值输入**: 测试时使用了真实 DNase-seq 信号作为输入特征。这意味着模型依赖实验测量的染色质开放性数据，而非纯序列预测。若 DNase-seq 不可用，模型性能会下降。
- **端到端状态**: 模型是端到端训练的，但输入包含实验测量值（DNase-seq），并非纯计算预测。
- **算力成本**: 训练成本未详细报告；推理速度显著优于基线，但需要 GPU 才能达到 <1h 的全基因组预测。
- **历史数据依赖**: 模型依赖 ENCODE 项目的 ChIP-seq 和 DNase-seq 数据质量；不同实验室、不同批次的 ChIP-seq 数据可能存在系统性偏差。
- **最难情形**: 间接结合（tethering）事件、无明确 motif 的 TF、染色质状态极端异常的细胞类型。
- **群体/领域边界**: 模型在 10 个 TF 上验证，未覆盖所有人类 TF；未测试非人类物种。
- **不确定性**: AUPRC 绝对值（0.208）表明正样本召回率仍有限，模型可能漏检大量真实结合位点。
- **有边界的复述**: Leopard 在 10 个 TF、23 个跨细胞类型测试对上，以单碱基分辨率实现了平均 AUROC 0.982、AUPRC 0.208 的预测性能，显著优于 Anchor 和 FactorNet，并将全基因组预测时间从数天缩短至 1 小时内（GPU）。该性能依赖于输入中的真实 DNase-seq 信号，且仅在 ENCODE 数据覆盖的 TF 和细胞类型范围内得到验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 依赖 DNase-seq 输入 | 模型需要实验测量的染色质开放性数据，无法仅从序列预测 | 未明确提及 | Discussion 节（隐含） |
| 未覆盖所有 TF | 仅验证 10 个 TF | 未明确提及 | Results "Overview of experimental design" 节 |
| 可解释性有限 | 仅使用 saliency map，未深入分析模型学习到的生物学特征 | 提及 DeepLIFT 作为潜在改进 | Discussion 节 |
| 参考基因组版本 | 使用 hg19，未在 hg38 上验证 | 未明确提及 | Methods "The reference genome" 节 |
| 未与其他多对多方法对比 | 仅与多对一方法（Anchor、FactorNet）和早期深度学习方法对比 | 未明确提及 | Results "Leopard substantially outperforms..." 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|----------------------|----------|----------|------|
| AUPRC 绝对值较低（0.208） | 尽管相对提升显著，但绝对性能可能不足以支撑实际应用中的全基因组筛选 | 实际应用中需要高精确率以减少实验验证成本 | 计算在更高精确率阈值下的召回率；与 ChIP-seq 生物学重复的一致性比较 | Results 图 2C-D |
| 标签定义依赖 motif 扫描 | 正样本要求同时满足 GEM 峰和 FIMO motif 命中，可能排除无 motif 的结合事件 | 间接结合事件可能被系统性漏检 | 使用无 motif 的 TF（如辅激活因子）进行验证 | Methods "Data collection and preprocessing" 节 |
| ΔDNase-seq 特征消融证据不足 | 作者声称 Δ 特征重要，但未提供具体消融实验数值 | 无法判断该特征的实际贡献大小 | 要求作者提供消融实验数据 | 未提供 |
| 跨细胞类型泛化可能被高估 | 测试细胞系与训练细胞系可能共享相似的染色质特征 | 真实应用中的新细胞类型可能具有未见过的染色质状态 | 在远离训练分布的细胞类型（如疾病状态）上测试 | Results "Leopard accurately identifies..." 节 |
| 与 ChIP-exo 的比较方法 | 仅计算预测位点与 ChIP-exo 峰中心的距离，未比较峰强度或占据度 | 距离接近不等于结合强度一致 | 比较预测概率与 ChIP-exo 信号强度的相关性 | Results 图 3E |
| 速度对比的公平性 | 多对一模型可能未经过同等程度的超参数优化 | 速度优势可能部分来自实现差异而非架构本质 | 使用相同训练时长和超参数搜索预算重新对比 | Results 图 4B |

## 14 学到什么
**Agent 提炼的知识候选**

1. **多对多架构迁移（高价值）**: 将图像分割的 U-Net 架构迁移到一维基因组序列，实现单碱基分辨率输出。**迁移到本课题**: 可用于预测 TF 结合位点、DNA 甲基化位点、突变效应等需要单碱基分辨率的任务；也可用于「序列 + 表观修饰」多通道输入的整合建模。

2. **Δ特征设计（高价值）**: 通过减去所有细胞系的平均信号，构造「相对差异」特征，突出细胞类型特异的信号。**迁移到本课题**: 在比较不同条件（如疾病 vs. 正常、处理 vs. 对照）的 TF 结合差异时，可构造类似的 Δ 特征（如 ΔATAC-seq、ΔH3K27ac）作为模型输入。

3. **GEM 高分辨率标签提取（中价值）**: 使用 GEM peak caller 从 ChIP-seq 原始比对文件中提取单碱基峰，而非使用传统宽峰。**迁移到本课题**: 在构建 TF 结合位点训练集时，优先使用具有单碱基分辨率的实验数据（ChIP-exo、ChIP-nexus）或高分辨率 peak caller，避免标签模糊。

4. **跨细胞类型训练-测试协议（高价值）**: 采用「留出细胞类型」的评估方式，测试模型的泛化能力。**迁移到本课题**: 在评估 TF 结合预测模型时，应区分「同细胞类型」和「跨细胞类型」性能，后者更贴近实际应用场景。

5. **类别不平衡处理（中价值）**: 面对极稀疏的正样本（0.0156%），使用 AUPRC 而非仅 AUROC 作为主要指标。**迁移到本课题**: 在 TF 结合位点预测、增强子预测等高度不平衡任务中，应同时报告 AUPRC 和部分 AUPRC 曲线。

6. **Saliency map 用于模型解释（中价值）**: 通过梯度反传计算输入特征的重要性。**迁移到本课题**: 可用于识别模型关注的 motif 和染色质开放区域，辅助发现新的结合模式。

7. **速度与精度的权衡（低价值）**: 多对多架构在保持精度的同时大幅提升速度。**迁移到本课题**: 在全基因组规模的 TF 结合预测中，计算效率是实际应用的关键瓶颈，多对多架构值得优先考虑。

## 15 与已有知识连接
- **U-Net 架构**: 原始 U-Net 来自医学图像分割（Ronneberger et al., 2015, MICCAI）。本文将其适配到一维基因组数据，与后续的 Enformer（Avsec et al., 2021, Nat. Genet.）和 Borzoi（Calico, 2023）等长上下文模型形成对比——后者使用 Transformer 而非 U-Net。
- **Basenji**: Kelley et al. (2018) 也采用多对多架构预测表观遗传信号，但分辨率为 128 bp，本文将其推进到单碱基。
- **BPNet**: Avsec et al. (2021) 使用多对多 CNN 预测 ChIP-nexus 数据，输入长度 1 kb，本文输入长度 10 kb，更强调长程上下文。
- **Anchor**: Li et al. (2019) 是 ENCODE-DREAM 挑战赛的优胜方法，基于 XGBoost 和特征工程。本文直接对比并超越之。
- **Δ 特征思想**: 与差分表达分析（如 DESeq2）中的「处理 vs. 对照」思想类似，但应用于染色质开放性信号。
- **GEM peak caller**: Guo et al. (2012) 开发的基于模型的 peak calling 工具，本文将其用于生成单碱基标签。
- **ENCODE-DREAM 挑战赛**: 2017 年举办的 TF 结合位点预测挑战赛，本文使用其数据集进行基准测试。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**: 多模态 Δ 特征融合的 TF 结合预测
   - **来源局限/观察**: Leopard 仅使用 DNase-seq 一种染色质开放性信号；其他表观修饰（H3K27ac、H3K4me1/2/3）可能提供互补信息。
   - **核心假设**: 融合多种表观修饰的 Δ 特征可进一步提升跨细胞类型 TF 结合预测精度。
   - **初步方法**: 在 Leopard 架构基础上，将输入通道扩展为 DNA 序列 + 多种表观修饰信号（每种均计算 Δ 特征），使用 1D U-Net 或 Transformer 编码器。
   - **验证方式**: 在 ENCODE 数据上对比单模态 vs. 多模态输入的 AUPRC；在独立细胞类型上测试泛化性。
   - **创新状态**: unverified

2. **候选名称**: 单碱基分辨率下的 TF 协同结合建模
   - **来源局限/观察**: Leopard 对每个 TF 独立建模，未显式建模 TF-TF 协同结合（如 pioneer factor 与 settle factor 的先后结合）。
   - **核心假设**: 多任务学习（同时预测多个 TF 的结合位点）可隐式捕捉 TF 协同关系，提升单 TF 预测精度。
   - **初步方法**: 将 Leopard 扩展为多任务输出（每个 TF 一个输出通道），共享编码器但使用任务特定解码器；分析任务间注意力权重以识别协同 TF 对。
   - **验证方式**: 对比单任务 vs. 多任务 AUPRC；验证预测的协同 TF 对是否与已知蛋白-蛋白相互作用数据库（如 BioGRID）一致。
   - **创新状态**: unverified

3. **候选名称**: 结合物理模拟的 TF 结合能预测
   - **来源局限/观察**: Leopard 是纯数据驱动模型，未利用 TF-DNA 结合的物理化学原理（如氢键、形状读码）。
   - **核心假设**: 将分子动力学（MD）模拟或 Rosetta 对接得到的结合自由能作为辅助特征或正则化项，可提升数据稀疏场景下的预测精度。
   - **初步方法**: 对每个 TF 的已知 motif 进行 MD 模拟，提取结合自由能谱；将能量特征与 Leopard 的序列特征融合；或在损失函数中加入物理约束项。
   - **验证方式**: 在低数据量 TF（如仅 1-2 个细胞系有 ChIP-seq）上对比有无物理特征的 AUPRC。
   - **创新状态**: unverified

4. **候选名称**: 突变效应预测的 Δ 特征扩展
   - **来源局限/观察**: Leopard 预测的是结合位点存在性，未直接预测突变对结合亲和力的影响。
   - **核心假设**: 利用 Leopard 的 saliency map 或积分梯度，可计算每个碱基对结合预测的贡献，从而预测 SNP/突变效应。
   - **初步方法**: 对参考序列和突变序列分别运行 Leopard，计算预测概率差异；与 eQTL 数据或 MPRA（大规模平行报告基因分析）数据对比验证。
   - **验证方式**: 在已知致病 SNP（如 ClinVar 中的启动子突变）上测试预测准确率。
   - **创新状态**: unverified

5. **候选名称**: 长上下文 U-Net 与 Transformer 混合架构
   - **来源局限/观察**: Leopard 输入 10 kb，但增强子-启动子互作可跨越数百 kb；U-Net 的感受野有限。
   - **核心假设**: 在 U-Net 编码器末端加入 Transformer 层，可捕捉超长程相互作用，同时保持单碱基输出分辨率。
   - **初步方法**: 将 Leopard 的编码器输出（320 长度）输入 Transformer encoder，再送入解码器；对比不同 Transformer 层数的性能-速度权衡。
   - **验证方式**: 在已知长程调控位点（如 SHH 增强子）上测试预测精度；对比 Enformer 的 100 kb 输入。
   - **创新状态**: unverified