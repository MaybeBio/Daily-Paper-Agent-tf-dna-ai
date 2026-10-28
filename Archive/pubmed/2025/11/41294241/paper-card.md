## 01 基本信息
- **标题**：QTFPred: robust high-performance quantum machine learning modeling that predicts main and cooperative transcription factor bindings with base resolution
- **作者**：Matsubara, Taichi; Machida, Shuto; Owusu, Samuel Papa Kwesi; Asakura, Akihiro; Hashimoto, Hiroki; Matsuoka, Masanori; Nagasaki, Masao
- **单位**：未提供（通讯作者 Nagasaki Masao 所属为 Kyushu University，依据致谢部分推断）
- **期刊/平台**：Briefings in Bioinformatics
- **年份**：2025-11-26
- **论文类型**：方法学（Method）论文
- **领域**：计算基因组学 / 量子机器学习 / 转录因子结合位点预测
- **关键词**：quantum machine learning; transcription factor binding; base resolution; cooperative binding; deep learning
- **DOI/arXiv 号**：10.1093/bib/bbaf604
- **代码**：https://nagasakilab.csml.org/en/qtfpred
- **数据**：ENCODE ChIP-seq 数据集（49 个用于评测，具体 ID 见补充表 S1、S2）；JASPAR 2024 CORE；HOCOMOCO v11
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「TF–DNA 结合机制 × AI/深度学习」方向，创新点在于将量子卷积层（QConv）引入 TF 结合位点预测，实现碱基分辨率预测，并利用量子特征空间提升小样本场景下的鲁棒性；同时通过 motif 共现分析揭示协同结合（cooperative binding）机制，属于「AI 方法 + 结合机制解析」的交叉定位。

## 02 一句话总结
QTFPred 通过将量子卷积层（QConv）嵌入 FCN 架构，在 GPU 上模拟量子电路训练，以碱基分辨率预测 TF 结合位点，在 49 个 ENCODE ChIP-seq 数据集上于 92% 二分类和 96% 信号预测任务中达到 SOTA，并在小样本场景下保持稳定，同时通过 motif 共现分析揭示协同结合关系。

## 03 研究问题
- **具体问题**：如何在数据稀疏（<10,000 peaks）的 TF 结合位点预测场景下，构建一个碱基分辨率的、鲁棒且高精度的预测模型？
- **为什么重要**：约 45.6% 的 ENCODE ChIP-seq 实验 peak 数不足 10,000，传统深度学习方法在小样本下性能退化严重；而 TF 结合位点的准确预测是理解基因调控、疾病突变机制的基础。
- **现有方法不足**：传统 PWM 假设位点内位置独立；SVM 受限于 k-mer 长度和过拟合；深度学习方法（DeepBind、BPNN、BPNet 等）依赖大量训练数据，小样本下泛化能力差；已有量子方法（如 D-Wave 量子退火）仅能处理约 10 bp 序列、覆盖 4 种 TF，且特征表示非学习得到。
- **精确研究问题（Can...?）**：Can a quantum-classical hybrid neural network with quantum convolutional layers achieve robust, base-resolution TF binding prediction superior to classical deep learning models, particularly under limited training data conditions?

## 04 背景与发展脉络
- **阶段一：传统方法**：PWM（位置独立假设，可解释但无法捕捉核苷酸间依赖）；SVM（k-mer 频率特征，优于 PWM 但受限于 k-mer 长度和过拟合）。
- **阶段二：深度学习二分类**：DeepBind 等将 TFBS 预测视为序列二分类任务，性能大幅提升，但缺乏碱基分辨率。
- **阶段三：碱基分辨率建模**：FCNA（全卷积网络，单碱基预测）、BPNet（扩张 CNN，提取调控 motif，发现顺式调控语法），实现核苷酸级精度。
- **阶段四：Transformer 架构**：DNABERT、Enformer、Nucleotide Transformer 等利用自注意力捕捉长程依赖，但需要大量预训练计算资源。
- **阶段五：量子机器学习**：已有量子退火方法（D-Wave）受限于平台约束、序列长度（~10 bp）和 TF 覆盖度（4 种），且特征表示静态。
- **本文位置**：首次将 QCL（量子电路学习）与 FCN 结合，实现碱基分辨率 TF 结合预测，覆盖 49 个 TF 数据集、1000 bp 序列，并系统验证量子增强在小样本场景下的优势。
- **脉络标注**：以上脉络基于本文 Introduction 的叙述框架，未经外部独立核验。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 小样本性能退化 | 多数 TF 的 ChIP-seq peak 数 <10,000，传统深度学习方法在此场景下精度显著下降 | 深度模型参数量大，数据不足时过拟合；特征提取能力受限 | Introduction 引用 [23]；Results 图 2a-b 显示低 peak 组 QTFPred 优势最大 |
| 量子方法覆盖度低 | 已有量子方法仅能处理 ~10 bp 序列、4 种 TF，无法用于全基因组规模 | 量子退火平台约束、静态特征表示（QUBO 预定义） | Introduction 对 [31-33] 的评述 |
| 碱基分辨率缺失 | 早期深度学习方法（如 DeepBind）仅做二分类，无法定位精确结合位点 | 模型设计未考虑逐碱基输出 | Introduction 对 DeepBind 的定位 |
| 协同结合机制不明 | 传统方法难以揭示多个 TF 在共享调控区域的协同关系 | 缺乏对 motif 共现模式的系统分析框架 | Results 图 6c-e 的检测热图与共现分析 |
| 计算资源瓶颈 | 量子电路模拟计算开销大，难以扩展到长序列 | 量子态维度随 qubit 数指数增长 | Results 图 5a-c 计算资源对比；Kernel Division Strategy 的提出 |

## 06 核心思想
1. **表面方法**：将 FCN 的第一层卷积替换为量子卷积层（QConv），通过 GPU 模拟量子电路，实现端到端训练的量子-经典混合模型，用于碱基分辨率的 TF 结合预测。
2. **核心洞察**：量子电路通过 angle encoding 将输入映射到指数级特征空间（4-qubit → 16 维），自动生成输入特征的乘法组合，无需显式核方法；这种高维非线性特征提取在小样本场景下比经典卷积更高效。
3. **普适教训 [Analysis]**：量子增强的核心价值不在于"量子优势"的抽象承诺，而在于其在小样本、高维特征交互场景下的具体收益——这提示在 TF–DNA 结合预测中，特征交互（核苷酸间非加性依赖）是关键瓶颈，量子电路天然适合捕捉这类交互。

## 07 方法总览
- **输入**：DNA 序列（二分类：500 bp；信号预测：1000 bp），one-hot 编码（A/C/G/T → 4 维向量）
- **输出**：二分类任务：每个碱基位置的结合概率；信号预测任务：每个碱基位置的结合信号强度
- **核心模块**：
  1. QConv1 层：量子卷积层（4-qubit PQC + angle encoding + 测量），处理 4 bp 窗口
  2. 经典卷积层（13 bp kernel）：补充量子层，扩展感受野至 16 bp
  3. FCN 编码器-解码器结构：沿用 FCNA/FCNsignal 的 U-Net 类似架构
  4. 输出层：逐碱基预测
- **训练**：AdamW 优化器，Xavier 初始化（含 PQC 参数），最大 40 epochs，早停 patience=6，GPU（H100/A100），二分类用单精度、信号预测用双精度
- **反馈回路**：无显式反馈回路；采用硬负样本挖掘损失（hard negative mining loss）用于二分类
- **文字流程**：输入 DNA 序列 → one-hot 编码 → QConv1 层（量子卷积提取 4 bp 窗口特征）→ 13 bp 经典卷积扩展上下文 → FCN 编码器-解码器逐层提取与上采样 → 逐碱基输出预测值 → 与实验 ChIP-seq 数据计算损失 → 反向传播更新经典与量子参数

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| QConv1 层（量子卷积） | 在 4 bp 窗口内提取高维非线性特征 | 量子电路提供指数级特征空间，自动生成特征乘法组合，小样本下比经典卷积更高效 | 输入：4 bp one-hot 序列（4×4 矩阵）；输出：16 维特征向量 | Results 图 5d-e 消融实验显示 qubit 数增加提升性能；图 6a 显示训练后滤波器 IC 显著高于随机初始化 | 移除后性能下降（实测，图 5d-e），尤其低 peak 组；[Analysis] 预期经典卷积无法完全替代量子特征提取 |
| 13 bp 经典卷积层 | 扩展感受野至 16 bp，整合量子特征与空间上下文 | 4-qubit 量子层仅覆盖 4 bp，需经典层补充长程上下文 | 输入：QConv1 输出特征图；输出：16 bp 感受野特征 | Kernel Division Strategy 描述（Methods 节） | [Analysis] 预期移除后感受野不足，无法覆盖完整 motif；未提供单独消融 |
| FCN 编码器-解码器 | 层次化特征提取与逐碱基预测 | 沿用 FCNA/FCNsignal 验证过的架构，保证公平对比 | 输入：QConv1+Conv2 特征；输出：逐碱基预测 | 方法描述（Methods 节） | [Analysis] 预期替换为其他架构会改变性能，但非本文核心贡献 |
| 硬负样本挖掘损失 | 二分类任务中聚焦难分样本 | 提升小样本下的判别能力 | 输入：预测概率与标签；输出：损失值 | Methods 节训练描述 | [Analysis] 预期移除后低 peak 组性能下降，但未单独消融 |
| 滤波器→PFM 转换 | 将 QConv 滤波器转化为可解释的 motif 表示 | 连接黑箱模型与生物学可解释性 | 输入：训练后滤波器权重；输出：16 bp PFM | Results 图 6a-b；Methods 节 motif 分析 | [Analysis] 移除后无法进行 motif 与协同分析，但不影响预测精度 |

## 09 关键公式符号
1. **Angle encoding**：将 one-hot 输入 x_i ∈ {0,1} 映射为量子态，通过 Y 轴旋转门 R_Y(θ)：
   - 符号：R_Y(θ) = 绕 Y 轴旋转 θ 角的单量子比特门；x_i = 第 i 个核苷酸的 one-hot 值
   - 用途：将经典数据编码为量子态
   - 直觉：每个核苷酸值映射为量子态旋转角度，4 个 qubit 对应 4 bp 窗口
   - 来源：Methods 节 "Architecture of quantum convolutional layer"

2. **量子态张量积**：|ψ⟩ = ⊗ᵢ R_Y(x_i)|0⟩
   - 符号：⊗ = 张量积；|0⟩ = 初始量子态
   - 用途：4 个 qubit 的联合态，维度 2⁴ = 16
   - 直觉：张量积结构自动生成输入特征的乘法组合（如 x₁x₂x₃x₄），无需显式核方法
   - 来源：Methods 节

3. **测量期望值**：⟨σ_z⁽ⁱ⁾⟩ = ⟨ψ|σ_z⁽ⁱ⁾|ψ⟩
   - 符号：σ_z⁽ⁱ⁾ = 作用于第 i 个 qubit 的 Pauli-Z 算符
   - 用途：将量子态解码为经典实数特征，输入后续神经网络层
   - 直觉：每个 qubit 的测量给出一个实数值，4 qubit 共 4 个特征
   - 来源：Methods 节

4. **信息含量（IC）**：IC = Σᵢ Σⱼ pᵢⱼ log₂(pᵢⱼ / bⱼ)
   - 符号：pᵢⱼ = PFM 中第 i 位第 j 个核苷酸的频率；bⱼ = 背景频率（假设均匀分布）
   - 用途：量化 motif 的信息丰富度，比较训练后与随机滤波器
   - 直觉：IC 越高表示 motif 越保守、信息越集中
   - 来源：Methods 节 "Motif calculation algorithm"

## 09 关键公式符号（续）
5. **Kernel Division Strategy**：将 16 bp 感受野分解为 4 bp 量子卷积 + 13 bp 经典卷积
   - 符号：k_quantum = 4（量子卷积核大小），k_classical = 13（经典卷积核大小）
   - 用途：在保持 16 bp 感受野的同时，避免 16-qubit 量子模拟的计算爆炸
   - 直觉：量子部分捕捉短程高维交互，经典部分补充长程上下文
   - 来源：Methods 节 "Kernel division strategy for practical implementation"

## 10 实验设计与证据链
- **数据集**：ENCODE ChIP-seq，二分类 53 个数据集（A549 19 个，4 个用于调参；GM12878 20 个；MCF7 14 个），评测 49 个；信号预测 52 个数据集（K562 20 个，3 个用于调参；GM12878 20 个；HeLa-S3 12 个），评测 49 个
- **指标**：二分类用 IoU（Intersection over Union）；信号预测用 Pearson 相关系数
- **基线**：二分类对比 FCN、FCNA；信号预测对比 BPNet、FCNsignal
- **评测协议**：10 次独立试验，随机数据划分（80% 训练/20% 测试），固定随机种子保证公平对比；二分类用硬负样本挖掘损失，信号预测用 RMSE
- **消融实验**：qubit 数（1-4）对性能的影响，替换 FCNsignal 第一层卷积

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|--------------|--------------------|------|
| 二分类性能（MCF7） | QTFPred 优于 FCN/FCNA | 49 个数据集，10 次试验 | QTFPred 在 92% 数据集 SOTA；低 peak 组（TAF1 4093 peaks）IoU 0.77 vs FCNA 0.66 | 量子增强在小样本下优势显著 | 未证明在所有 peak 规模下均最优 | Results 图 2a-b |
| 信号预测性能（HeLa-S3） | QTFPred 优于 BPNet/FCNsignal | 49 个数据集，10 次试验 | QTFPred 在 96% 数据集 SOTA；低 peak 组 Pearson 0.70 vs BPNet 0.36 | 量子增强在信号预测中同样有效 | 未与 Transformer 类模型对比 | Results 图 2c-d |
| 信号预测（K562, GM12878） | 跨细胞系泛化 | 相同协议 | QTFPred 在所有 peak 组一致最优 | 跨细胞系鲁棒性 | 未测试更多细胞系 | Results 图 S6 |
| qubit 消融（E2F6, ELK1） | qubit 数增加提升性能 | 1-4 qubit vs FCNsignal | 低 peak 组 1 qubit 即显著提升（0.56 vs 0.48），4 qubit 进一步改善（0.61） | 量子特征提取驱动性能提升 | 未测试 >4 qubit | Results 图 5d-e |
| qubit 消融（MAZ, E2F1） | 中 peak 组同样受益 | 同上 | 4 qubit 显著优于 FCNsignal（0.74 vs 0.70） | 量子增强不限于小样本 | 高 peak 组差异不显著 | Results 图 5e, S10 |
| motif 分析（JUND, ELK4, MAFF） | QConv 滤波器学习真实 motif | 训练后 vs 随机初始化滤波器，TOMTOM 比对 JASPAR | 训练后 IC 显著更高（JUND 5.68 vs 3.58, p < 1e-30）；成功匹配已知 motif | 量子层学习生物学相关表示 | 未验证所有 49 个 TF 的 motif | Results 图 6a-b |
| 协同结合分析（HeLa-S3） | 检测 TF 共现模式 | 12 个 TF 的检测热图 + 层次聚类 | 识别出 E2F6-MAX 功能相似组，与已知生化实验一致 | 模型可揭示协同结合关系 | 未做湿实验验证新预测 | Results 图 6c-e, 7 |

## 11 结论正确解读
- **任务范围**：本文结论仅适用于 TF 结合位点的碱基分辨率预测（二分类和信号回归），不涉及染色质可及性、三维基因组等其他调控层面。
- **oracle/真值输入**：训练和评测均使用 ENCODE ChIP-seq 实验数据作为真值，未使用合成数据或模拟数据。
- **端到端状态**：模型是端到端训练的，但量子部分通过 GPU 模拟实现，并非在真实量子硬件上运行。
- **算力成本**：QTFPred 训练时间约为 FCNsignal 的 8-22.5 倍，GPU 内存需求约为 1.9 倍，这是实际部署中需权衡的成本。
- **历史数据依赖**：模型依赖 ChIP-seq 数据的质量和数量；在极低数据量（<250 peaks）下的表现未测试。
- **模型依赖**：量子增强效果依赖于 Kernel Division Strategy 的设计；更换量子电路结构或编码方式可能改变结论。
- **最难场景**：低 peak 组（<10,000 peaks）是 QTFPred 优势最明显的场景，但也是所有方法性能最低的场景。
- **有边界的复述**：QTFPred 在 49 个 ENCODE ChIP-seq 数据集上，以碱基分辨率预测 TF 结合位点，在 92% 二分类和 96% 信号预测任务中达到 SOTA，尤其在小样本场景下性能稳定；同时通过 motif 共现分析识别出与已知生物学一致的协同结合关系（如 E2F6-MAX），但计算成本显著高于经典方法。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 计算成本高 | 训练时间比 FCNsignal 慢 8-22.5 倍，GPU 内存需求高 1.9 倍 | 未来量子硬件发展可能缓解；优化量子电路设计 | Discussion 段落 |
| 量子比特数受限 | 当前实现仅支持 4 qubit，无法探索更大量子电路 | 量子硬件或模拟技术进步后扩展 qubit 数 | Discussion 段落 |
| 未覆盖全部 TF | 评测限于 49 个数据集，未覆盖所有人类 TF | 扩展到更多细胞系和 TF | Discussion 未来工作 |
| 协同分析依赖已知数据库 | motif 匹配依赖 JASPAR 数据库，可能遗漏未知 motif | 结合 de novo motif 发现方法 | Discussion 段落 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| 量子增强的"纯效应"未完全隔离 | 替换第一层卷积的同时，可能改变了模型容量、初始化、训练动态等混杂因素 | 若性能提升来自架构变化而非量子特性，则"量子优势"结论不成立 | 用相同参数量的随机非线性层替换 QConv1 做对照实验 | Methods 节描述仅替换第一层，未报告对照 |
| 小样本优势可能来自正则化效应 | 量子电路参数化可能隐式引入正则化，而非量子特征空间的本质优势 | 若为隐式正则化，经典方法可通过 dropout/weight decay 达到类似效果 | 对 FCN/FCNA 增加强正则化后对比 | Results 图 2a-b 未报告正则化对照 |
| 4-qubit 的"指数特征空间"论证有限 | 2⁴=16 维特征空间远小于经典高维卷积特征，量子优势的机制解释可能过度 | 若 16 维特征空间是优势来源，经典方法可用 16 维手工特征复现 | 用 16 维核方法（如 RBF kernel）替换 QConv1 对比 | Methods 节对量子特征空间的论述 |
| 协同结合分析的统计显著性未充分报告 | 仅报告了 E2F6-MAX 等已知关系，未报告新预测的验证或 FDR 控制 | 若共现分析仅复现已知结果，其"发现"价值有限 | 检查是否报告多重检验校正；对新预测做独立验证 | Results 图 6c-e 未报告统计检验细节 |
| 与 Transformer 基线缺失 | 未与 DNABERT、Enformer 等 SOTA Transformer 模型对比 | 若 Transformer 在小样本下同样鲁棒，则量子增强的必要性存疑 | 在相同数据集上对比 QTFPred 与轻量 Transformer | Results 仅对比 FCN/FCNA/BPNet |
| 计算成本报告不完整 | 仅报告相对倍数，未报告绝对时间/能耗 | 8-22.5 倍慢可能在实际应用中不可接受 | 报告端到端训练时间、推理时间、能耗的绝对值 | Results 图 5a-c 仅相对比较 |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **量子卷积层（QConv）作为特征提取器**：将量子电路嵌入 CNN 第一层，通过 angle encoding 将序列映射到高维特征空间，自动生成特征交互项。可迁移到 TF–DNA 结合预测中，用于捕捉核苷酸间的非加性交互（如协同结合中的 spacing 约束）。
2. **Kernel Division Strategy**：将大感受野分解为小量子核 + 经典核的组合，在保持感受野的同时控制量子模拟成本。可迁移到其他长序列建模任务（如增强子-启动子交互预测）。
3. **小样本鲁棒性验证框架**：通过 peak 数分组（低/中/高）系统评估模型在不同数据规模下的表现，并配合 down-sampling 实验验证鲁棒性。可迁移到 TF–DNA 结合预测的模型评测设计中。
4. **滤波器到 PFM 的可解释性转换**：将训练后的卷积滤波器转换为位置频率矩阵，与已知数据库比对，实现黑箱模型的可解释性分析。可迁移到其他序列模型（如 CNN-based motif 发现）。
5. **TF 检测热图 + 层次聚类**：通过 motif 共现模式构建 TF 功能相似性矩阵，识别协同结合组。可迁移到 TF–DNA 互作网络中预测 TF 协同关系。
6. **硬负样本挖掘损失**：在二分类任务中聚焦难分样本，提升小样本下的判别能力。可迁移到 TF 结合位点预测中处理类别不平衡问题。

## 15 与已有知识连接
- **与 PWM 模型的连接**：本文的 QConv 滤波器可视为 PWM 的非线性推广，保留了位置特异性但引入核苷酸间依赖。与经典 PWM 方法（如 JASPAR 数据库）的对比可验证量子特征提取的增量价值。
- **与深度学习方法的连接**：本文以 FCN/FCNA/BPNet 为基线，与 DeepBind（二分类）、BPNet（碱基分辨率）形成方法谱系。与 Transformer 方法（DNABERT、Enformer）的对比缺失，是后续研究可补充的方向。
- **与量子机器学习的连接**：本文基于 Mitarai et al. 的 QCL 框架，与量子核方法、量子神经网络等方向相关。与量子退火方法（D-Wave）的对比凸显了门模型量子计算在序列建模中的潜力。
- **与 TF–DNA 结合机制研究的连接**：本文的协同结合分析（E2F6-MAX）与已知生化实验一致，支持了"motif 共现 → 功能协同"的分析范式。与 ChIP-seq、ChIP-exo 等高分辨率实验数据的结合可进一步验证预测。
- **可迁移方向 [Analysis]**：本文的量子增强思路可迁移到其他序列-功能预测任务（如 RNA 结合蛋白、剪接位点预测），但需注意量子模拟的计算成本；在真实量子硬件成熟前，GPU 模拟是主要实现方式。

## 16 研究想法
1. **名称**：量子增强的 TF 协同结合基序发现（Quantum-enhanced cooperative TF motif discovery）
   - **来源局限/观察**：本文通过 motif 共现分析识别协同关系，但依赖已知数据库匹配，可能遗漏未知协同基序。
   - **核心假设**：量子卷积层的高维特征空间能捕捉更复杂的协同结合模式（如 spacing 可变、方向可变的基序组合）。
   - **初步方法**：在 QTFPred 基础上，对 QConv1 滤波器进行 de novo motif 发现，结合共现网络分析，预测未知的 TF 协同关系。
   - **验证方式**：用独立 ChIP-seq 数据集（如 ENCODE 其他细胞系）验证新预测的协同关系；与 ChIP-exo 高分辨率数据比对。
   - **创新状态**：unverified

2. **名称**：量子-经典混合模型用于 TF 结合特异性的物理约束建模（Physics-constrained quantum-classical TF binding specificity model）
   - **来源局限/观察**：本文纯数据驱动，未利用 TF–DNA 结合的物理化学约束（如氢键、形状读码）。
   - **核心假设**：将物理约束（如 DNA 形状特征、结合自由能）作为正则化项引入量子-经典混合模型，可提升泛化能力。
   - **初步方法**：在 QTFPred 损失函数中加入基于分子动力学（MD）模拟或结构预测的物理约束项；或使用量子电路编码 DNA 形状特征。
   - **验证方式**：在低 peak 组数据集上对比有无物理约束的性能；用突变实验数据验证预测的物理合理性。
   - **创新状态**：unverified

3. **名称**：跨细胞系 TF 协同结合的可迁移量子模型（Transferable quantum model for cross-cell-type cooperative TF binding）
   - **来源局限/观察**：本文验证了跨细胞系迁移（ELK1 实验），但未系统评估所有 TF 的迁移性能。
   - **核心假设**：量子特征空间的共享表示能捕捉细胞系无关的 TF 结合规则，提升迁移学习效率。
   - **初步方法**：在 QTFPred 中加入域适应模块（如对抗训练或最大均值差异），在源细胞系预训练、目标细胞系微调。
   - **验证方式**：在多个细胞系对（如 GM12878→K562）上评估迁移性能，对比无迁移基线。
   - **创新状态**：unverified

4. **名称**：量子卷积滤波器作为可解释的 TF 结合基序表示（Quantum convolutional filters as interpretable TF binding motif representations）
   - **来源局限/观察**：本文展示了滤波器可转换为 PFM，但未系统分析滤波器与已知基序的对应关系。
   - **核心假设**：量子卷积滤波器能学习到与已知 TF 基序高度一致且更丰富的表示。
   - **初步方法**：对 49 个 TF 的 QConv1 滤波器进行全量 TOMTOM 比对，量化匹配率；分析未匹配滤波器的序列特征。
   - **验证方式**：与 FCN/FCNA 滤波器的基序匹配率对比；用 MEME 等工具进行 de novo 发现。
   - **创新状态**：unverified

5. **名称**：量子增强的碱基分辨率预测在变异效应预测中的应用（Quantum-enhanced base-resolution prediction for variant effect annotation）
   - **来源局限/观察**：本文预测精度高，但未测试在遗传变异（SNP/indel）效应预测中的表现。
   - **核心假设**：碱基分辨率的量子模型能更准确预测单核苷酸变异对 TF 结合的影响。
   - **初步方法**：用 QTFPred 对已知致病 SNP 所在位点进行结合预测，比较变异前后结合分数变化；与 ClinVar 等数据库比对。
   - **验证方式**：用实验验证的变异效应数据（如 MPRA、STARR-seq）评估预测准确性。
   - **创新状态**：unverified