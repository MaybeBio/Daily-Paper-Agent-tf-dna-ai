## 01 基本信息
- **标题**: Comprehensive analysis of computational approaches in plant transcription factors binding regions discovery
- **作者与单位**: Jyoti; Ritu; Sagar Gupta; Ravi Shankar（CSIR-Institute of Himalayan Bioresource Technology, India；Academy of Scientific and Innovative Research, India）
- **期刊/预印本平台**: Heliyon
- **年份**: 2024-12-06
- **论文类型**: 综述/基准评测（Comparative analysis / Benchmarking study）
- **领域**: 生物信息学；转录因子结合区域（TFBRs）计算预测；植物基因组学
- **关键词**: Transcription factors; TFBS; TFBR; Machine learning; Deep learning; Plant genomics; Peak calling; Motif discovery
- **DOI/arXiv 号**: 10.1016/j.heliyon.2024.e39140
- **代码**: https://github.com/SCBB-LAB/Comparative-analysis-of-plant-TFBS-software（修正后的脚本）
- **数据**: 公开数据（ENCODE、Plant Cistrome Database、GEO 等），详见补充材料
- **阅读日期**: 未提供
- **在该方向中的位置**: 本文是植物 TF–DNA 互作计算方法的系统性基准评测，覆盖从 peak calling → TFBR 预测 → motif 发现的完整流程，对比了 19 种 TFBR 预测工具和 9 种 motif 发现工具，并首次系统评估了跨物种泛化能力。对「TF–DNA 结合机制 × AI」课题的价值在于：提供了植物特有的基因组变异性（TF 结构变异、结合位点分歧）对模型泛化影响的量化证据，以及工具可复现性（bug 修复）的工程实践。

## 02 一句话总结
本文系统评测了植物 TFBR 发现流程中三个环节（peak calling、TFBR 预测、motif 发现）的 19+9 种计算工具，发现多数工具存在代码缺陷、对数据量敏感、跨物种泛化能力差，而基于 TF 结构与结合区域协变学习的 PTFSpot/PTF-Vāc 是唯一能真正跨物种工作的方案。

## 03 研究问题
- **具体问题**: 植物转录因子结合区域（TFBRs）的计算预测工具，其声称的性能是否可复现？在跨物种场景下是否有效？现有工具的设计哲学（基于 motif 富集 vs. 基于序列上下文）哪种更符合植物 TF–DNA 结合的真实机制？
- **为什么重要**: 植物基因组具有高度变异性（复杂重复序列、TF 结构分歧大），而绝大多数工具基于人类数据开发。若工具无法跨物种泛化，则对新测序植物基因组的注释毫无价值。此外，工具的可复现性（代码 bug）直接决定其科学可用性。
- **现有方法不足**: (1) 多数工具代码年久失修，存在依赖冲突、API 变更、逻辑错误，无法直接运行；(2) 训练数据集中于人类/模式动物，植物数据量少且分散；(3) 几乎所有工具将 TF–DNA 结合简化为 motif 富集问题，忽略 flanking region 上下文、染色质状态、TF 结构变异等关键因素；(4) 跨物种评估几乎缺失。
- **精确研究问题**: "Can existing computational tools for TFBR discovery, developed primarily on human/animal data, be reliably applied to plant genomes across different species, and what design principles enable true cross-species generalization?"

## 04 背景与发展脉络
*（注：以下脉络基于本文框架，未经外部独立核验）*

| 阶段 | 代表性方法 | 优点 | 局限 | 本文定位 |
|------|-----------|------|------|---------|
| **早期（~2010前）** | PWM 扫描（如 FIMO）、consensus 序列 | 简单、可解释 | 仅捕获核心 motif，忽略上下文；对植物复杂基因组无效 | 本文将其归为「motif 即 TFBS」的错误范式 |
| **传统 ML（2010-2016）** | gkmSVM、k-mer grammar、Wimtrap | 引入 k-mer 特征，可捕获部分序列上下文 | 特征工程依赖人工；浅层模型无法学习长程依赖；跨物种泛化差 | 本文评测显示 gkmSVM 在跨物种时性能骤降 |
| **深度学习 CNN（2015-2020）** | DeepBind、DeepSEA、BPNet、TSPTFBS、SeqConv | 自动特征提取；局部 motif 识别能力强 | 感受野有限，难以捕获长程上下文；对数据量敏感；过拟合严重 | 本文显示 CNN 类工具在植物数据上过拟合明显 |
| **复杂 CNN/混合架构（2020-2022）** | MAResNet、WSCNNLSTM、PlantBind、TSPTFBS 2.0 | 引入注意力、残差连接、多任务学习 | 仍以 motif 为核心；跨物种泛化未解决 | 本文显示这些工具在跨物种时仍失败 |
| **Transformer/生成式（2023-）** | DNABERT、PTFSpot、PTF-Vāc | 长程上下文建模；PTF 系列引入 TF 结构协变学习 | 计算成本高；需要 3D 结构信息 | 本文认为 PTFSpot/PTF-Vāc 是唯一真正跨物种方案 |

**本文主张的位置**: 现有工具（除 PTF 系列外）均未考虑植物基因组变异性的核心问题——TF 结构随物种分化而变异，导致结合偏好改变。因此，任何基于固定 motif 或单一物种训练的模型，跨物种时必然失败。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| **代码不可用** | 38 个工具中仅 19 个可运行；多数报错（ImportError、TypeError、FileNotFoundError 等） | 维护不善、依赖过时、文档缺失 | Methods 节、Table 2、补充材料 S3 |
| **跨物种泛化失败** | 除 PTFSpot 外，所有工具在 Dataset C（玉米→拟南芥）上准确率降至 50-70% | 模型过拟合训练物种；未考虑 TF 结构变异 | Results 节、Fig. 8D |
| **数据量敏感** | 多数工具在 <50 条序列时无法工作；结果随输入量线性变化 | 深度学习需要大数据；植物数据稀缺 | Results 节、Fig. 10A |
| **motif 与 TFBS 混淆** | 工具将富集 motif 直接等同于 TFBS，忽略上下文 | 历史遗留范式；缺乏对结合机制的深入理解 | Discussion 节 |
| **负样本构建不当** | 多数工具随机抽取基因组序列作为负样本，未考虑序列相似性 | 简化处理；缺乏对假阴性/假阳性的控制 | Methods 节（Dataset B 构建） |
| **评估指标不全面** | 多数工具仅报告准确率，忽略 MCC、敏感度/特异度平衡 | 指标选择偏颇；掩盖类别不平衡问题 | Results 节、Fig. 8 |

## 06 核心思想

### 1) 表面方法
对 38 种 TFBR 预测工具和 9 种 motif 发现工具进行系统评测，分为三个环节：peak calling（6 种）、TFBR 预测（19 种）、motif 发现（9 种）。构建三个数据集：Dataset A（各工具原始训练数据）、Dataset B（拟南芥 265 个 TF 的 DAP-seq 数据，统一处理）、Dataset C（拟南芥与玉米共有的 5 个 TF 的跨物种测试数据）。

### 2) 核心洞察
- **TF–DNA 结合不是「motif 匹配」问题，而是「结构协变」问题**：植物 TF 结构随物种分化而变异（如 WRKY75 在拟南芥与油菜间 RMSD=1.285Å），导致结合偏好改变。因此，固定 motif 模型必然失败。
- **上下文比 motif 更重要**：所有高性能工具（PTFSpot、TSPTFBS 2.0）都利用了 flanking region 上下文，而非仅核心 motif。
- **负样本质量决定模型上限**：多数工具负样本构建粗糙，导致模型学到的是「序列组成差异」而非「结合机制」。
- **代码可复现性是科学有效性的前提**：19/38 工具无法运行，意味着大量已发表结果不可验证。

### 3) 可能的普适教训 [Analysis]
- 对 TF–DNA 互作建模，应放弃「固定 PWM」范式，转向「序列 + 结构 + 上下文」的联合建模。
- 跨物种泛化应作为模型设计的首要约束，而非事后测试。
- 负样本构建应模拟真实基因组背景（如匹配 GC 含量、重复含量、染色质状态），而非随机抽样。
- 工具发布应附带可运行的测试用例和依赖锁定，否则科学贡献无法累积。

## 07 方法总览
- **输入**: 
  - Peak calling: 原始 ChIP-seq/DAP-seq 测序 reads（FASTQ）
  - TFBR 预测: peak 区域序列（±75bp 至 ±200bp）
  - Motif 发现: TFBR 序列集合
- **输出**: 
  - Peak calling: peak 坐标列表（BED 格式）
  - TFBR 预测: 每个序列的结合概率/二分类标签
  - Motif 发现: motif 矩阵（PWM/PFM）及基因组扫描结果
- **模块**:
  1. 数据预处理（Trimmomatic 去接头、Bowtie2 比对、SAMtools 排序）
  2. Peak calling（6 种工具并行）
  3. TFBR 预测（19 种工具，含传统 ML 和 DL）
  4. Motif 发现（9 种工具，含传统统计和 DL）
  5. 跨物种评估（Dataset C）
- **训练**: 各工具按其原始论文设置训练；Dataset B 上统一进行超参数优化
- **工具**: 见 Table 1（19 种 TFBR 工具）和 Methods 节（9 种 motif 工具）
- **反馈回路**: 无显式反馈回路；各环节独立评估
- **假设**: 
  - DAP-seq peak 是 TF 结合的真实近似
  - 跨物种测试中，同源 TF 的结合功能保守
  - 默认超参数在 Dataset A 上有效

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|---------------------|
| Peak calling 模块 | 从 ChIP-seq/DAP-seq 原始数据中识别富集区域 | 提供 TFBR 预测的输入 | 输入: FASTQ reads; 输出: peak BED 文件 | Fig. 6A-D | 预期影响：peak 质量直接影响下游所有环节 [Analysis] |
| 数据集构建模块 | 构建统一评估基准（Dataset A/B/C） | 公平比较不同工具 | 输入: 公开数据; 输出: 标准化训练/测试集 | Methods 节、Fig. 4 | 预期影响：无统一基准则无法比较 [Analysis] |
| TFBR 预测模块 | 从序列预测 TF 结合区域 | 核心任务 | 输入: peak 序列; 输出: 结合概率 | Fig. 8A-D | 实测影响：不同工具间准确率差异达 30%+ |
| Motif 发现模块 | 从 TFBR 中提取结合 motif | 提供可解释的生物学标记 | 输入: TFBR 序列; 输出: PWM/motif | Fig. 10A-B | 实测影响：多数工具 motif 与实验 motif 相似度 <70% |
| 跨物种评估模块 | 测试模型在未见物种上的泛化 | 验证实际可用性 | 输入: 拟南芥训练模型 + 玉米测试数据 | Fig. 8D | 实测影响：除 PTFSpot 外全部失败（准确率 <70%） |
| Bug 修复模块 | 修正工具代码使其可运行 | 保证评测可行性 | 输入: 原始代码; 输出: 修正后代码 | Table 2、补充材料 S3 | 预期影响：无此模块则 50% 工具无法评测 [Analysis] |

## 09 关键公式符号
本文为评测性研究，未提出新公式。以下为评估指标：

- **准确率 (Accuracy)**: $Acc = \frac{TN + TP}{TN + TP + FN + FP}$
- **敏感度 (Sensitivity/Recall)**: $Sn = \frac{TP}{TP + FN}$
- **特异度 (Specificity)**: $Sp = \frac{TN}{TN + FP}$
- **Matthews 相关系数 (MCC)**: $MCC = \frac{TN \times TP - TN \times FP}{\sqrt{(TP+FP)(TP+FN)(TN+FP)(TN+FN)}}$
- **F1 分数**: $F1 = 2 \times \frac{Precision \times Recall}{Precision + Recall}$
- **AUC**: $AUC = \int_0^1 Pr[TP](v) dv$

其中 TP=True Positives, TN=True Negatives, FP=False Positives, FN=False Negatives。

## 10 实验设计与证据链

### 数据集
| 数据集 | 内容 | 规模 | 用途 |
|--------|------|------|------|
| Dataset A | 各工具原始训练数据（人类/动物为主） | 因工具而异 | 验证工具声称性能 |
| Dataset B | 拟南芥 265 个 TF 的 DAP-seq peak 数据 | 911,342 个结合区域 | 统一基准训练/测试 |
| Dataset C | 拟南芥与玉米共有的 5 个 TF（LHY1, MYB62, MYB81, MYB88, WRKY25） | 5 个 TF 的跨物种测试集 | 跨物种泛化评估 |

### 评估协议
- 19 种 TFBR 工具在 Dataset A 上按默认参数运行，验证声称性能
- 在 Dataset B 上进行超参数优化后重新训练/微调
- Dataset C 上使用 Dataset B 训练的模型直接测试（不微调）
- 指标：Accuracy, Sensitivity, Specificity, F1, MCC, AUC

### 关键实验与结果

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|----------------|------|
| Peak calling 工具评测 | 不同 peak caller 在植物数据上的可靠性 | 6 种工具，5 个玉米 TF | 工具间 peak 数量差异达 10 倍以上；MACS2/LanceOtron/PeakRanger 最可靠 | peak calling 是主要误差来源 | 未评估 peak 长度/位置精度 | Fig. 6 |
| Dataset A 性能复现 | 工具声称性能可复现 | 19 种工具 vs 原始论文报告 | 多数工具复现性能与声称一致 | 工具本身性能可靠 | 未独立验证所有工具 | Fig. 8A |
| Dataset B 统一基准 | 植物数据上工具相对性能 | 19 种工具，265 个拟南芥 TF | PTFSpot 最佳（Acc 96.14%, MCC 0.9190）；TSPTFBS 2.0 次之 | DL 优于传统 ML；上下文建模关键 | 未评估计算成本 | Fig. 8B |
| Dataset C 跨物种 | 工具能否跨物种泛化 | 拟南芥训练 → 玉米测试 | 仅 PTFSpot 表现良好（Acc 92.50%, MCC 0.8594）；其余工具 50-70% | 跨物种泛化是核心挑战 | 仅 5 个 TF，样本量小 | Fig. 8D |
| 数据量敏感性 | 工具对输入数据量的依赖 | 不同输入规模（10-1000 序列） | 多数工具在 <50 序列时失效；PTF-Vāc 对数据量不敏感 | 数据量是实际应用瓶颈 | 未系统评估所有工具 | Fig. 10A |
| Motif 发现工具评测 | motif 发现工具与实验 motif 的一致性 | 9 种工具，10 个拟南芥 TF | PTF-Vāc 最佳（相似度 96.61%）；传统工具平均 <70% | 生成式 AI 优于统计富集 | 未评估 motif 位置精度 | Fig. 10B |
| 类不平衡影响 | 不平衡数据对模型的影响 | 1:1 vs 1:4 正负比 | 不平衡导致所有工具性能下降；敏感度受影响最大 | 平衡数据集是必要条件 | 未测试其他比例 | Fig. 8C |
| TF 结构变异性分析 | 植物 TF 结构跨物种变异程度 | 5 个 TF 家族，拟南芥 vs 4 种作物 | RMSD 0.401-1.472Å；WRKY75 变异最大 | 结构变异是跨物种失败的主因 | 仅基于 AlphaFold2 预测结构 | Fig. 9、Table 3-4 |

## 11 核心结论
- **Peak calling 环节**: MACS2、LanceOtron、PeakRanger 是植物 ChIP-seq/DAP-seq 数据最可靠的选择；工具间一致性低，建议多工具交叉验证。
- **TFBR 预测环节**: PTFSpot 在拟南芥数据上最优（Acc 96.14%），且是唯一在跨物种测试中保持高性能的工具（Acc 92.50%）。其成功关键在于利用 TF 序列/结构协变信息，而非仅序列 motif。
- **Motif 发现环节**: PTF-Vāc 显著优于所有对比工具（相似度 96.61%），且对数据量不敏感，支持单序列 motif 发现。
- **跨物种泛化**: 除 PTFSpot 外，所有工具在跨物种场景下失败（准确率 50-70%），表明现有工具的实际应用价值有限。
- **可复现性**: 38 个工具中 19 个无法运行，代码维护是领域内被严重忽视的问题。
- **核心机制洞察**: TF–DNA 结合由「TF 结构 + 序列上下文 + 基因组环境」共同决定，motif 仅是必要非充分条件。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| 跨物种测试样本量小 | 仅 5 个 TF（LHY1, MYB62, MYB81, MYB88, WRKY25）在拟南芥与玉米间测试 | 扩大跨物种测试范围，覆盖更多 TF 家族 | Discussion 节 |
| 依赖 AlphaFold2 预测结构 | 无实验解析结构的 TF 使用预测结构，可能引入误差 | 结合实验结构（X-ray/Cryo-EM）验证 | Discussion 节 |
| 未评估计算成本 | 未系统比较各工具的训练/推理时间与资源消耗 | 提供计算资源需求报告 | Discussion 节 |
| 未覆盖表观遗传因素 | 未整合染色质可及性、DNA 甲基化等表观遗传数据 | 多组学整合建模 | Discussion 节 |
| 工具版本固定 | 评测基于特定版本，后续更新可能改变性能 | 建立持续更新的基准平台 | Discussion 节 |
| 仅二分类评估 | 未评估结合强度/亲和力的定量预测 | 引入回归任务评估 | Discussion 节 |

## 12.5 作者提及的相关约束（非正式局限）
- 多数工具需要至少 50 条输入序列才能稳定工作，限制了在低丰度 TF 或小规模实验中的应用。
- 植物基因组中复杂重复序列对 peak calling 和 motif 发现均有干扰，但现有工具缺乏针对性处理。
- 跨物种测试中，同源 TF 的功能保守性假设可能不成立，需结合系统发育信息。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| PTFSpot 的跨物种优势可能源于评估偏差 | 5 个测试 TF 可能恰好是结构保守的 TF 家族；若选择结构分歧更大的 TF，PTFSpot 可能同样失败 | 跨物种泛化结论的普适性 | 在更多 TF 家族和物种对（如单子叶 vs 双子叶）上测试 | Fig. 8D、Table 3-4 |
| 评测集中于拟南芥和玉米 | 拟南芥基因组简单（~135Mb），玉米复杂（~2.3Gb），但未覆盖多倍体作物（如小麦） | 植物基因组复杂性谱系覆盖不足 | 增加小麦、棉花等多倍体物种测试 | Methods 节 |
| 未评估 ensemble 策略 | 多工具集成可能优于单一最优工具，但未测试 | 实际应用中的鲁棒性方案 | 设计工具集成实验 | 未提供 |
| 对「motif 非充分条件」的论证依赖 PTF-Vāc 单一工具 | 结论基于一个工具的表现，缺乏独立验证 | 核心生物学论断的稳健性 | 用其他结构感知方法（如 AlphaFold3 对接）独立验证 | Fig. 10 |
| 代码修复可能改变工具行为 | 修复 bug 后工具性能可能与原始发表版本不同，评测结果不能完全代表文献中的工具 | 评测公平性 | 与原始版本对比，报告修复前后差异 | Table 2、补充材料 S3 |
| 未讨论数据泄漏风险 | 拟南芥 DAP-seq 数据可能与其他工具训练数据重叠 | 评测有效性 | 检查训练/测试集序列相似性 | 未提供 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **TF–DNA 结合建模应超越固定 motif**：本文核心证据表明，TF 结构跨物种变异（RMSD 0.4-1.5Å）导致结合偏好改变，固定 PWM 模型必然失败。迁移到本课题：开发 TF–DNA 结合预测模型时，应将 TF 序列/结构嵌入作为输入，而非仅 DNA 序列。

2. **上下文特征比核心 motif 更具判别力**：所有高性能工具都利用了 flanking region 上下文。迁移：构建特征时，应包含 ±100bp 以上的序列上下文、GC 含量、重复元件密度等基因组环境特征。

3. **负样本构建质量决定模型上限**：多数工具负样本与正样本存在序列组成差异，导致模型学到伪特征。迁移：负样本应从匹配的基因组背景中采样（相同 GC、重复含量、染色质状态），而非随机或简单打乱。

4. **跨物种泛化应作为设计约束**：本文显示除 PTFSpot 外所有工具跨物种失败。迁移：模型设计时应引入结构协变学习（如 TF 嵌入随物种变化），并在训练时加入多物种数据。

5. **可复现性是科学贡献的一部分**：19/38 工具无法运行。迁移：发布模型时，应提供容器化环境、固定依赖版本、测试用例和修正脚本。

6. **生成式 AI 在 motif 发现中的优势**：PTF-Vāc 的 encoder-decoder 架构对数据量不敏感，支持单序列分析。迁移：在数据稀缺的植物 TF 研究中，生成式方法可能优于判别式方法。

7. **多工具交叉验证是必要的**：peak calling 工具间一致性低。迁移：在构建训练数据集时，应使用多种 peak caller 并取交集或加权并集。

## 15 与已有知识连接
- **ENCODE 项目**（Consortium, 2012）：本文 Dataset A 的人类数据主要来自 ENCODE，与 ENCODE 的 peak calling 基准评测（如 ENCODE3 的 IDR 流程）直接相关。
- **DeepBind**（Alipanahi et al., 2015）：首个大规模 CNN 预测 TF 结合，本文将其作为 DL 基线工具评测。
- **gkmSVM**（Ghandi et al., 2014）：gapped k-mer SVM 方法，本文评测显示其在植物数据上表现中等。
- **DNABERT**（Ji et al., 2021）：Transformer 预训练模型，本文评测其在跨物种场景下失败。
- **AlphaFold2**（Jumper et al., 2021）：本文使用 AF2 预测 TF 结构用于 PTFSpot 的结构协变学习。
- **PTFSpot/PTF-Vāc**（Shankar 团队前期工作）：本文是这些工具的独立评测和扩展。
- **JASPAR 数据库**：本文 motif 相似性比较的参考标准。
- **与「shape readout」文献的连接**：本文讨论 flanking region 上下文时，与 DNA shape（如 minor groove width）影响结合特异性的研究（Rohs et al., 2009）一致。
- **与「TF 结构变异」文献的连接**：本文的 RMSD 分析支持了植物 TF 结构快速进化的观点（Jin et al., 2015）。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**: 结构感知的跨物种 TF–DNA 结合预测模型
   - **来源局限/观察**: 本文显示除 PTFSpot 外所有工具跨物种失败，但 PTFSpot 仅用 5 个 TF 验证
   - **核心假设**: 将 TF 的 AlphaFold2 结构嵌入与 DNA 序列上下文联合建模，可显著提升跨物种泛化
   - **初步方法**: 构建 TF 结构编码器（GNN/PointNet）+ DNA 序列编码器（CNN/Transformer）的双塔架构，在拟南芥、玉米、水稻多物种数据上联合训练
   - **验证方式**: 在未见物种（如小麦、大豆）上测试，与 PTFSpot、TSPTFBS 2.0 对比
   - **创新状态**: unverified

2. **候选名称**: 上下文感知的负样本采样策略
   - **来源局限/观察**: 本文指出多数工具负样本构建粗糙，导致模型学到伪特征
   - **核心假设**: 匹配基因组背景（GC、重复、染色质状态）的负样本可提升模型真实判别力
   - **初步方法**: 开发基于基因组特征匹配的负样本采样算法，在拟南芥 DAP-seq 数据上对比不同采样策略
   - **验证方式**: 比较模型在独立测试集上的 MCC 和跨物种性能
   - **创新状态**: unverified

3. **候选名称**: 基于生成式 AI 的植物 TF 结合 motif 从头发现
   - **来源局限/观察**: PTF-Vāc 是唯一对数据量不敏感的 motif 发现工具
   - **核心假设**: 变分自编码器（VAE）或扩散模型可从少量结合序列中生成高保真 motif 表示
   - **初步方法**: 在 10 个拟南芥 TF 上训练 VAE-based motif 生成器，与 MEME、HOMER 对比
   - **验证方式**: 生成的 motif 与 JASPAR 实验 motif 的相似度、结合位点预测精度
   - **创新状态**: unverified

4. **候选名称**: TF 结构变异与结合偏好共变的系统分析
   - **来源局限/观察**: 本文 RMSD 分析显示 TF 结构跨物种变异显著，但未系统量化与结合偏好变化的关系
   - **核心假设**: TF 结构变异程度与结合 motif 分歧程度呈正相关
   - **初步方法**: 对 50+ 个 TF 家族，计算跨物种 RMSD、motif 相似度（TomTom）、结合亲和力变化，建立回归模型
   - **验证方式**: 统计显著性检验、预测能力评估
   - **创新状态**: unverified

5. **候选名称**: 植物 TFBR 预测的集成学习框架
   - **来源局限/观察**: 本文显示 peak calling 工具间一致性低，但未测试集成策略
   - **核心假设**: 多工具集成可提升 peak calling 和 TFBR 预测的鲁棒性
   - **初步方法**: 对 6 种 peak caller 输出进行加权投票/堆叠，在 5 个玉米 TF 数据上验证
   - **验证方式**: 与单一最优工具比较 F1、MCC、跨物种性能
   - **创新状态**: unverified

6. **候选名称**: 可解释的 TF–DNA 结合上下文特征提取
   - **来源局限/观察**: 本文强调 flanking region 上下文的重要性，但未解析具体贡献
   - **核心假设**: 通过注意力权重可识别决定结合特异性的关键上下文位点
   - **初步方法**: 在 PTFSpot 或自建模型上应用 attention 可视化，与已知的 TF 协同因子结合位点交叉验证
   - **验证方式**: 注意力热点与实验验证的协同结合位点重叠率
   - **创新状态**: unverified