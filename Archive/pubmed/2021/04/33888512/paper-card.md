## 01 基本信息
- **标题**：Modeling transcriptional regulation of model species with deep learning
- **作者**：Cofer, Evan M; Raimundo, Joao; Tadych, Alicja; Yamazaki, Yuki; Wong, Aaron K; Theesfeld, Chandra L; Levine, Michael S; Troyanskaya, Olga G
- **单位**：Lewis-Sigler Institute for Integrative Genomics, Princeton University; Flatiron Institute; 等（作者单位未在摘要中完整列出，部分来自机构信息）
- **期刊/平台**：Genome Research
- **年份**：2021（在线发表 2021-04-24）
- **论文类型**：方法学/资源型研究（深度学习模型开发 + 实验验证）
- **领域**：调控基因组学；深度学习；顺式调控元件建模
- **关键词**：deep learning, cis-regulatory activity, transcription factors, histone marks, chromatin accessibility, model organisms, variant effect prediction
- **DOI/arXiv**：10.1101/gr.266171.120
- **代码**：https://github.com/FunctionLab/DeepArk
- **数据**：训练数据来自 ChIP-Atlas、DANIO-CODE 等公共数据库；预测结果与原始视频数据存放于 Zenodo（链接见正文 Data access 节）
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「序列 → 调控活性」的端到端深度学习映射，是 TF–DNA 结合机制研究中「以序列为中心、以 ChIP-seq 为监督信号」的代表性工作。它不直接建模 TF–DNA 三维结构或物理相互作用，而是通过大规模多任务 CNN 学习顺式调控语法，为 TF 结合位点预测、变异效应评估和跨物种调控注释提供了可迁移的框架。与 MD/对接等物理模拟方法互补：物理方法提供机制解释，DeepArk 提供高通量序列-功能映射。

## 02 一句话总结
本文开发了 DeepArk——一组针对四个模式物种（C. elegans、D. rerio、D. melanogaster、M. musculus）的深度 CNN 模型，以 4095 bp DNA 序列为输入，预测 6562 个调控特征（染色质状态、组蛋白修饰、TF 结合等）的活性，并通过体内实验验证了其在变异效应预测和跨物种调控注释中的实用性。

## 03 研究问题
- **具体问题**：能否用统一的深度学习架构，从 DNA 序列出发，为多个模式物种建立高精度的顺式调控活性预测模型？
- **为什么重要**：模式物种（如果蝇、线虫、斑马鱼、小鼠）是研究转录调控机制的核心系统，但此前缺乏类似人类基因组中 Enformer/DeepSEA 那样的序列-调控资源。建立此类模型可加速调控变异解读、基因组注释和机制假设生成。
- **现有方法不足**：已有深度模型（如 DeepSEA、Basenji）主要针对人类；模式物种数据分散、质量不一，缺乏统一处理的资源。此外，现有模型对 TF 结合预测的覆盖度有限，尤其缺乏对多种调控特征（组蛋白修饰、染色质可及性、RNA Pol II 等）的联合建模。
- **精确研究问题（Can 形式）**：Can a single deep CNN architecture, trained on publicly available ChIP-seq/DNase-seq/ATAC-seq data, accurately predict context-specific cis-regulatory activity across four model species, and can its predictions generalize to variant effect assessment and cross-species regulatory annotation?

## 04 背景与发展脉络
*注：以下脉络基于本文引用与领域常识，标注「经外部核验」的部分为领域公认事实。*

1. **早期序列基调控预测（2015 年前）**：基于 PWM/位置权重矩阵的 motif 扫描，只能捕捉短序列模式，无法建模长程相互作用和染色质环境。局限：精度低、覆盖度有限。
2. **深度学习进入调控基因组学（2015–2018）**：DeepSEA（Zhou & Troyanskaya 2015）和 Basenji（Kelley et al. 2018）等模型证明 CNN 可从序列预测染色质特征和 TF 结合，且长序列上下文（kb 级）显著提升精度。主要针对人类。
3. **模式物种调控资源建设（2016–2020）**：modENCODE、DANIO-CODE 等联盟积累了模式物种的 ChIP-seq/ATAC-seq 数据，但缺乏统一的深度学习建模。
4. **DeepArk 的位置（2021）**：首次将多任务 CNN 系统性地应用于四个模式物种，覆盖 6562 个调控特征，并提供交互式 web 界面。其创新点不在架构，而在数据整合、跨物种泛化验证和实验验证闭环。

*经外部核验*：DeepSEA、Basenji 为人类调控预测的里程碑工作；modENCODE 和 DANIO-CODE 为模式物种数据来源。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 模式物种缺乏序列-调控预测资源 | 人类有 DeepSEA/Basenji，但 C. elegans、D. rerio、D. melanogaster、M. musculus 无同类工具 | 数据分散、质量参差，缺乏统一处理流程 | Results 第 1 段："To the best of our knowledge, DeepArk is the first such resource for these model organisms." |
| 调控特征覆盖不足 | 已有模型主要针对人类，且特征类别有限 | 多任务学习需要大量高质量标注数据，模式物种数据不足 | Results 第 1 段：DeepArk 覆盖 6562 个特征，包括 554 个 TF、62 个组蛋白修饰、RNA Pol II 和染色质可及性 |
| 变异效应预测缺乏模式物种支持 | 无法评估模式物种中非编码变异的调控影响 | 缺乏序列-功能映射模型 | Results 第 2 段：DeepArk 可预测任意变异的调控效应，如 ALDOB 增强子 |
| 跨物种调控注释困难 | 未研究物种缺乏实验数据，难以注释调控元件 | 序列保守性 ≠ 功能保守性，需要直接的功能预测 | Results 第 4 段：D. rerio 模型可预测青鳉（O. latipes）的调控活性，平均 ROC AUC 0.927 |
| 长程调控上下文需求 | 短序列窗口无法捕捉复杂调控逻辑 | 已有研究表明宽序列上下文对精度至关重要 | Methods "DeepArk model architecture"：输入 4095 bp；Results 第 1 段引用 Zhou & Troyanskaya 2015; Kelley et al. 2016, 2018 |

## 06 核心思想
1. **表面方法**：构建四个独立的深度 CNN（每个物种一个），输入 4095 bp 的 one-hot 编码 DNA 序列，输出为该序列中心碱基处各调控特征（TF 结合、组蛋白修饰、染色质可及性等）的活性概率。多任务学习，共享底层特征提取器，每个特征有独立的输出头。使用公开 ChIP-seq/DNase-seq/ATAC-seq 数据训练，以二元交叉熵 + L2 正则化为目标函数。

2. **核心洞察**：调控逻辑可以从序列中直接学习，且这种学习可以跨物种泛化。关键在于：(a) 宽序列上下文（4095 bp）捕捉顺式调控元件的组合逻辑；(b) 多任务学习让模型共享调控语法，提升数据效率；(c) 统一的架构和数据处理流程使得跨物种比较成为可能。

3. **可能的普适教训 [Analysis]**：对于 TF–DNA 结合机制研究，DeepArk 表明「序列 → 结合」的映射可以在不需要显式三维结构信息的情况下被高精度地学习。这意味着：(1) TF 结合特异性在很大程度上由局部序列编码，但需要足够的侧翼上下文来捕捉辅助因子效应；(2) 多任务学习（同时预测多种 TF 和组蛋白修饰）能隐式地学习 TF 之间的竞争与合作关系；(3) 跨物种迁移是可行的，但需要谨慎处理物种间的调控语法差异。

## 07 方法总览
- **输入**：4095 bp DNA 序列（one-hot 编码，4 通道：A/C/G/T）
- **输出**：每个调控特征的活性概率向量（长度 N，N 因物种而异，总计 6562 个特征）
- **模型架构**：深度 CNN，包含 5 个卷积块，每个块由批归一化 → ReLU → 卷积 → 最大池化组成。最后一个卷积块输出经 1×1 卷积（输出通道数 = 特征数）和 sigmoid 激活，得到各特征的预测概率。
- **训练**：随机梯度下降 + 动量，mini-batch 128；损失函数 = 二元交叉熵 + L2 正则化（λ 为权重衰减超参数）；学习率在验证损失连续 5 个 epoch 不下降时衰减 20%；早停。
- **数据**：训练标签来自公共 ChIP-seq（TF、组蛋白修饰）、DNase-seq、ATAC-seq 数据；C. elegans、D. melanogaster、M. musculus 使用 ChIP-Atlas 的 peak 数据（Q ≤ 1e-5）；D. rerio 使用 DANIO-CODE 数据，peak 由 MACS2 调用。
- **数据划分**：按染色体划分训练/验证/测试集（整条染色体留出），避免数据泄漏。
- **正则化**：前向/反向互补序列预测平均 + 空间 dropout（随机将卷积层输入的整个通道置零）。
- **推理/应用**：给定任意序列（包括含变异的序列），预测中心碱基处各特征活性；通过比较参考与变异序列的预测差异，评估变异的调控效应。
- **反馈回路**：无显式闭环；但通过体内实验（T48 增强子）验证预测，形成「预测 → 实验验证 → 模型改进」的迭代。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 多任务输出头 | 同时预测多个调控特征 | 共享序列特征提取器，提升数据效率；TF 间隐式竞争/合作关系 | 输入：最后一个卷积块的输出；输出：N 维概率向量 | Results 第 1 段：6562 个特征同时预测 | [预期] 移除后需为每个特征单独训练模型，数据效率大幅下降；无法隐式学习特征间相关性 |
| 宽序列上下文（4095 bp） | 捕捉长程调控信息 | 已知宽上下文提升预测精度 | 输入：4095 bp；输出：中心碱基预测 | Methods "DeepArk model architecture"：4095 bp 优于 2047 bp（作者在文中明确比较） | [实测] 作者报告 4095 bp 模型在四个物种中均优于 2047 bp 模型（Methods 节） |
| 前向/反向互补平均 | 保证反向互补不变性 | DNA 无方向性，预测应对两条链一致 | 输入：序列及其反向互补；输出：两者预测的平均 | Methods "DeepArk model architecture" | [预期] 移除后模型对反向互补序列的预测不一致，降低可靠性 |
| 空间 dropout | 正则化，防止过拟合 | CNN 输入通道间高度相关，传统 dropout 效果有限 | 输入：卷积层输入张量；输出：随机置零通道后的张量 | Methods "DeepArk model architecture" | [预期] 移除后可能过拟合，泛化性能下降 |
| 染色体级数据划分 | 防止训练/测试数据泄漏 | 相邻碱基高度相关，随机划分会高估性能 | 输入：全基因组；输出：训练/验证/测试染色体集合 | Methods "Training examples" | [预期] 移除后性能估计过于乐观，无法反映真实泛化能力 |
| 数据质量过滤 | 确保训练标签可靠 | 低质量实验引入噪声 | 输入：原始 peak 数据；输出：过滤后的训练集 | Methods "Training data preparation"：移除无抗体靶标、reads 过少、平均读长 <32 bp 的实验 | [预期] 移除后模型性能下降，尤其对稀有特征 |

## 09 关键公式符号
1. **损失函数**：L = BCE + λ‖W‖₂²
   - BCE = −(1/N) Σᵢ [yᵢ log(ŷᵢ) + (1−yᵢ) log(1−ŷᵢ)]
   - yᵢ：第 i 个样本的标签向量（0/1，表示该特征是否有 peak）
   - ŷᵢ：模型预测的概率向量
   - N：mini-batch 大小
   - λ：权重衰减系数
   - W：网络权重矩阵
   - 用途：多任务二元分类，每个特征独立计算 BCE 后求和；L2 项防止过拟合。

2. **预测目标**：P(feature_j = 1 | sequence) = σ(fⱼ(x))
   - σ：sigmoid 函数
   - fⱼ：网络对第 j 个特征的 logit 输出
   - x：one-hot 编码的 4095 bp 序列（4095 × 4 矩阵）
   - 用途：将网络输出映射为概率，表示中心碱基处该调控特征是否活跃。

3. **变异效应**：ΔP = P(feature_j = 1 | seq_ref) − P(feature_j = 1 | seq_alt)
   - seq_ref：参考等位基因序列
   - seq_alt：变异等位基因序列
   - 用途：通过比较参考与变异序列的预测概率差异，评估 SNP 的调控效应（如 ALDOB 增强子分析）。

## 10 实验设计与证据链
**数据集与评测协议**：
- 训练/验证/测试：按染色体划分（每个物种留出 1 条染色体作为测试集，1 条作为验证集），测试集每物种 100 万个样本。
- 特征数量：C. elegans、D. rerio、D. melanogaster、M. musculus 分别有不同数量的调控特征，总计 6562 个。
- 数据来源：C. elegans、D. melanogaster、M. musculus 使用 ChIP-Atlas（Q ≤ 1e-5）；D. rerio 使用 DANIO-CODE，MACS2 调用 peak。
- 指标：ROC AUC（报告于 Supplemental Table S1）；变异效应预测用 Pearson/Spearman 相关。
- 基线：未明确报告与传统方法（如 PWM）的系统比较；主要与随机基线比较（"higher than baseline"）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 各物种调控特征预测 | DeepArk 能准确预测多种调控特征 | 测试集 100 万样本/物种，按特征类别分层报告 AUC | 所有类别 AUC 高于基线；D. rerio 表现最佳 | 序列 → 调控活性的映射可学习 | 未与 PWM 等传统方法系统比较；AUC 高 ≠ 实际生物学机制正确 | Results 图 1B–D；Supplemental Table S1 |
| 序列长度比较 | 4095 bp 优于 2047 bp | 同架构、同数据，仅输入长度不同 | 4095 bp 在四个物种中验证损失均更低 | 宽序列上下文对预测精度重要 | 未测试更长序列（如 8191 bp）是否更优 | Methods "DeepArk model architecture" |
| ALDOB 增强子变异效应预测 | DeepArk 预测的变异效应与体内测量相关 | 与 Patwardhan et al. 2012 的 MPRA 数据比较（n=777 SNPs） | Pearson r = 0.714, P = 3.58×10⁻¹²²；Spearman ρ = 0.587, P = 2.91×10⁻⁷³ | 预测的变异效应反映体内调控活性 | 仅一个增强子；MPRA 测量的是表达效应而非直接结合 | Results 图 2A,B |
| T48 增强子突变体体内验证 | DeepArk 预测的 TF 结合变化与体内表达一致 | 3 个突变体（CTT>CTA, CTT>GTA, CTT>CTG）在果蝇胚胎中活体成像 | 预测的 Zld 结合概率与体内表达趋势一致（平均 Pearson r = 0.7217, n=6） | DeepArk 可指导基因组编辑实验设计 | 仅一个增强子、一个 TF；样本量小 | Results 图 3A–C；Supplemental Table S4 |
| 跨物种预测（D. rerio → O. latipes） | DeepArk 可注释未研究物种的调控活性 | 青鳉基因组序列，去除保守区域后测试 | 平均 ROC AUC = 0.927 | 调控语法在鱼类中保守 | 仅测试一个跨物种对；未测试更远缘物种 | Results 第 4 段；Supplemental Table S6 |

## 11 结论正确解读
- **任务范围**：DeepArk 预测的是「中心碱基处某调控特征是否有 peak」，即局部调控活性的二元分类，而非 TF 结合强度的定量预测，更非 TF–DNA 三维结构或结合动力学。
- **oracle/真值输入**：训练标签来自 ChIP-seq/DNase-seq/ATAC-seq 的 peak 调用，这些是实验测量，但 peak 存在 ≠ 直接结合，可能包含间接效应（如染色质开放区域的非特异性结合）。
- **端到端状态**：模型是端到端的（序列 → 活性），但「序列 → 调控机制」的解释性有限——CNN 的中间特征不可直接映射为 motif 或 TF 协同规则。
- **算力成本**：作者未报告具体训练时间/硬件；但 4 个物种 × 6562 特征 × 100 万测试样本的规模暗示需要 GPU 集群。
- **历史数据依赖**：模型依赖公共 ChIP-seq 数据的质量和覆盖度；数据稀疏的特征（如罕见细胞类型的 TF）预测可靠性较低。
- **最难情形**：TF 预测方差最高（Results 图 1B–D），尤其对 pioneer factor 与 chromatin remodeler 这类结合模式差异大的 TF；跨物种预测仅在保守区域有效。
- **群体/领域边界**：模型适用于有足够 ChIP-seq 数据的模式物种；对数据匮乏物种需依赖跨物种迁移，但迁移效果随进化距离下降。
- **不确定性**：作者未报告预测的置信区间或校准度；变异效应预测仅在一个增强子（ALDOB）和一个 TF（Zld）上验证，泛化性未知。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 调控特征覆盖不全 | 某些 TF 或细胞类型因缺乏数据未被建模 | 计划随新数据发布更新模型 | Discussion 第 2 段："there are certainly regulatory features that DeepArk has not yet modeled because of the lack of data" |
| 跨组织/细胞类型预测的复杂性 | 特征间相关性在不同组织中可能不同，简单多任务可能不够 | 引入已知调控网络、物理 TF 互作信息 | Discussion 第 2 段："cross-tissue predictions that systematically incorporate information about causal relationships (e.g., known regulatory networks, physical TF interactions) may also be a fruitful avenue for future research" |
| 序列长度可能不足 | 4095 bp 可能无法捕捉更远端的增强子-启动子互作 | 尝试更长序列或引入 3D 基因组信息 | Methods "DeepArk model architecture"（作者仅报告 4095 bp 优于 2047 bp，未测试更长） |
| 架构未针对物种优化 | 四个物种共用同一架构，可能未充分适配各物种的调控语法差异 | 神经架构搜索、物种特异超参数 | Discussion 第 3 段："novel CNN architectures will prove central to such endeavors" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 变异效应验证仅限一个增强子（ALDOB） | ALDOB 可能具有异常清晰的调控逻辑，不代表一般情况 | 若 DeepArk 的变异预测在复杂调控位点失效，其应用价值受限 | 在多个增强子（不同 TF 组合、不同染色质环境）上重复 MPRA 比较 | Results 图 2A,B |
| T48 验证中 Zld 是 pioneer factor，结合机制相对简单 | Pioneer factor 的结合可能比 cooperative TF 更易从序列预测 | 若 DeepArk 对 cooperative binding 预测不佳，则对多数增强子的适用性存疑 | 在依赖多个 TF 协同的增强子上测试突变预测 | Results 图 3A–C |
| 跨物种预测仅测试 D. rerio → O. melastigma（鱼类） | 鱼类调控语法可能高度保守，不代表哺乳动物或昆虫间可迁移 | 跨物种迁移是 DeepArk 的重要卖点，若仅限近缘物种则价值有限 | 测试 D. melanogaster → 蚊子、M. musculus → 大鼠等更远距离迁移 | Results 第 4 段 |
| 未报告与 PWM/motif 扫描的基线比较 | 传统方法可能在某些 TF 上仍有竞争力 | 若 DeepArk 仅在小部分特征上优于 PWM，其增量价值需重新评估 | 在相同测试集上比较 DeepArk 与 FIMO/HOMER 的 AUC | 未提供 |
| 多任务学习的收益未量化 | 未报告单任务模型的对比 | 若多任务收益有限，模型可简化，降低训练成本 | 训练单任务模型，比较 AUC 差异 | 未提供 |
| 数据过滤标准可能引入偏差 | 移除低质量实验可能系统性排除某些细胞类型或 TF | 模型可能对特定实验条件存在隐式偏好 | 分析被排除实验的特征，评估其对预测覆盖度的影响 | Methods "Training data preparation" |

## 14 学到什么
**Agent 提炼的知识候选**

1. **宽序列上下文的价值**：4095 bp 输入显著优于 2047 bp，说明 TF 结合不仅由局部 motif 决定，还受远端增强子、绝缘子等元件影响。→ 迁移到 TF–DNA 结合机制研究：在构建结合预测模型时，应优先考虑 kb 级上下文，而非仅聚焦 motif 区域。

2. **多任务学习隐式编码调控语法**：同时预测多种 TF 和组蛋白修饰，让模型学习到 TF 之间的竞争/合作关系。→ 迁移：在分析 TF 共结合（co-binding）或先后结合（sequential binding）时，多任务预测可作为「调控语法」的代理特征，辅助发现 TF 组合逻辑。

3. **跨物种迁移的可行性**：D. rerio 模型可预测青鳉的调控活性（AUC 0.927），说明顺式调控语法在进化中部分保守。→ 迁移：对缺乏 ChIP-seq 数据的物种，可先用近缘物种模型进行初步注释，再通过少量实验验证。

4. **变异效应预测的实用路径**：通过比较参考/变异序列的预测差异，可优先排序候选调控 SNP。→ 迁移：在 TF–DNA 结合机制研究中，可用此方法筛选可能影响 TF 结合的 SNP，再通过 EMSA、SPR 等实验验证。

5. **体内验证闭环**：T48 增强子实验展示了「计算预测 → 体内突变验证」的闭环设计。→ 迁移：任何计算模型都应设计可实验检验的预测，形成「预测-验证-修正」循环。

6. **数据质量过滤的工程实践**：对公共 ChIP-seq 数据设置严格过滤标准（reads 数、读长、抗体特异性），显著影响模型质量。→ 迁移：在整合公共 ChIP-seq 数据时，应建立统一的质量控制流程，而非直接使用原始 peak 调用。

## 15 与已有知识连接
- **DeepSEA（Zhou & Troyanskaya 2015）**：DeepArk 的直接前身，首次将 CNN 应用于染色质特征预测。DeepArk 将其扩展到多物种，并验证了跨物种迁移。→ 对 TF–DNA 研究：DeepSEA/DeepArk 的架构设计（卷积核捕捉 motif、多任务共享特征）是理解序列-结合映射的基础。
- **Basenji（Kelley et al. 2018）**：强调宽序列上下文（kb 级）的重要性，DeepArk 的 4095 bp 输入直接继承此思想。→ 对 TF–DNA 研究：支持「远端调控元件影响 TF 结合」的假说。
- **Enformer（Avsec et al. 2021）**：后续工作，引入 Transformer 架构捕捉更长程互作。DeepArk 可视为其前奏。→ 对 TF–DNA 研究：长程互作建模是未来方向。
- **Patwardhan et al. 2012（MPRA）**：DeepArk 的变异效应验证数据来源。MPRA 是连接计算预测与体内功能的桥梁。→ 对 TF–DNA 研究：MPRA 可用于高通量验证 TF 结合位点突变效应。
- **modENCODE / DANIO-CODE**：DeepArk 的数据基础。→ 对 TF–DNA 研究：这些资源是模式物种 TF 结合数据的主要来源。
- **Selene（Chen et al. 2019）**：DeepArk 的训练框架。→ 对 TF–DNA 研究：可用于复现或扩展 DeepArk 类模型。
- **[Analysis] 与物理模拟的互补性**：DeepArk 提供「序列 → 活性」的端到端映射，但不提供结合机制解释。MD/对接模拟可提供原子级结合模式，但计算成本高、难以高通量。未来方向：用 DeepArk 类模型筛选候选位点，再用物理模拟深入分析关键位点的结合机制。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：TF 结合机制的可解释性蒸馏
   - **来源局限/观察**：DeepArk 预测准确但不可解释，无法回答「为什么这个 TF 结合这里」。
   - **核心假设**：CNN 的中间层特征可被蒸馏为可解释的 motif 组合规则（如「motif A + 辅助因子 motif B 在 50 bp 内 → 结合」）。
   - **增量**：使用 attention 或 feature attribution（如 DeepLIFT、Integrated Gradients）提取关键序列位置，聚类为 motif 组合模式，与已知 TF 协同结合知识对比。
   - **验证**：在 DeepArk 预测的 TF 结合位点上，比较蒸馏规则与 ChIP-exo 高分辨率结合数据的吻合度。
   - **创新状态**：unverified

2. **候选名称**：跨物种 TF 结合语法差异的量化
   - **来源局限/观察**：DeepArk 显示 D. rerio 模型可预测青鳉，但未量化「调控语法」的进化距离。
   - **核心假设**：TF 结合语法的保守性与序列保守性相关，但存在「语法漂移」（同 motif 不同协同规则）。
   - **增量**：用 DeepArk 的四个物种模型，对同源增强子进行交叉预测，计算预测误差作为「语法距离」；与序列保守性比较。
   - **验证**：选择语法距离大的增强子，用报告基因实验验证功能差异。
   - **创新状态**：unverified

3. **候选名称**：结合深度学习和分子动力学模拟的 TF 结合位点优先级排序
   - **来源局限/观察**：DeepArk 预测变异效应但无机制解释；MD 模拟提供机制但计算昂贵。
   - **核心假设**：DeepArk 预测的「结合概率变化」与 MD 模拟的「结合自由能变化」相关，可互为验证。
   - **增量**：对 DeepArk 预测的高影响变异，用 MD 模拟（如增强采样）计算结合自由能变化，建立「序列 → 概率 → 自由能」的级联流程。
   - **验证**：对已知 TF–DNA 复合物结构（如 PDB 中的 TF–DNA 复合物），比较预测与实验结合亲和力。
   - **创新状态**：unverified

4. **候选名称**：单细胞分辨率的 DeepArk 扩展
   - **来源局限/观察**：DeepArk 使用 bulk 数据，无法捕捉细胞异质性。
   - **核心假设**：单细胞 ATAC-seq 数据可训练细胞类型特异的调控模型，揭示 TF 结合的细胞类型依赖性。
   - **增量**：将 DeepArk 架构适配单细胞 ATAC-seq 数据，引入细胞类型标签作为条件输入。
   - **验证**：在已知细胞类型特异的增强子上比较模型预测与单细胞实验数据。
   - **创新状态**：unverified

5. **候选名称**：TF 结合协同性的序列编码
   - **来源局限/观察**：DeepArk 的 TF 预测方差高，可能源于协同结合（co-binding）的复杂性。
   - **核心假设**：TF 结合可由「主 motif + 辅助 motif 组合」的语法编码，且该语法在不同细胞类型中可迁移。
   - **增量**：用 DeepArk 的多任务预测，分析 TF 对之间的预测相关性，构建「TF 协同网络」；与已知蛋白-蛋白互作数据库对比。
   - **验证**：对预测的高协同 TF 对，用 ChIP-seq 共定位分析验证。
   - **创新状态**：unverified