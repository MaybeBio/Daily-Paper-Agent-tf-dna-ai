## 01 基本信息
- **标题**：ExplaiNN: interpretable and transparent neural networks for genomics
- **作者与单位**：Novakovsky, Gherman; Fornes, Oriol; Saraswat, Manu; Mostafavi, Sara; Wasserman, Wyeth W（加拿大不列颠哥伦比亚大学，UBC）
- **期刊/预印本平台**：Genome Biology
- **年份**：2023-06-28
- **论文类型**：方法学（Method）
- **领域**：基因组学 × 深度学习可解释性
- **关键词**：可解释深度学习、转录因子结合位点预测、染色质可及性、de novo motif 发现、神经网络
- **DOI/arXiv 号**：10.1186/s13059-023-02985-y
- **代码**：未提供（原文提及开源仓库，但未给出具体 URL）
- **数据**：公开数据（ChIP-seq、ATAC-seq、scATAC-seq、HT-SELEX、PBM、SMiLE-seq、STARR-seq）
- **阅读日期**：未提供
- **在「蛋白质-DNA 互作 × AI/物理模拟」方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习可解释性」交叉方向，提出一种基于神经加法模型（NAM）的完全可解释 CNN 架构，用于 TF 结合位点预测、染色质可及性预测和 de novo motif 发现，是该方向中「透明模型设计」路线的代表性工作。

## 02 一句话总结
本文提出 ExplaiNN——一种由多个独立单滤波器 CNN 单元线性组合而成的可解释深度学习架构，在 TF 结合位点预测、染色质可及性预测和 de novo motif 发现等任务上达到与复杂黑箱模型（如 DanQ、DeepSTARR、AI-TAC）相当的性能，同时通过直接可视化滤波器权重和单元重要性分数提供全局与局部可解释性。

## 03 研究问题
- **具体问题**：如何设计一种既保持深度学习预测性能、又天然透明可解释的基因组序列模型，避免依赖事后解释方法（如 filter visualization、DeepLIFT + TF-MoDISco）？
- **为什么重要**：基因组学中深度模型（如 DanQ、DeepSTARR、AI-TAC）预测性能优异但黑箱性质严重，阻碍了生物学机制发现和非专家用户的采用。
- **现有方法不足**：
  - Filter visualization 依赖架构选择（如 max pooling、滤波器大小），且难以解释深层特征组合；
  - Attribution 方法（如 DeepLIFT）提供局部重要性但缺乏全局可解释性；
  - 全局解释需逐滤波器消融（filter nullification），计算昂贵且依赖任意阈值。
- **精确的「Can ... ?」研究问题**：Can a neural network architecture based on additive combination of independent single-filter CNN units achieve comparable predictive performance to complex black-box models while providing inherent interpretability for TF–DNA binding and chromatin accessibility prediction?

## 04 背景与发展脉络
（标注：以下脉络为「经外部核验」的领域发展主线，结合本文框架整理）
1. **PWM 时代**：传统 motif 发现用位置权重矩阵（PWM）表示 TF 结合模式，如 JASPAR 数据库。
2. **深度学习进入基因组学**：CNN（如 DeepSEA、Basset）、混合模型（DanQ 引入 LSTM）、大规模模型（Enformer、Basenji）在 TF 结合、染色质可及性、基因表达预测上表现优异，但可解释性差。
3. **可解释性方法发展**：
   - Filter visualization：将第一层卷积滤波器比对为 PWM（如 DeepSEA 的滤波器可视化）；
   - Attribution 方法：DeepLIFT、Saliency maps 等提供核苷酸级重要性；
   - 事后聚类：TF-MoDISco 将重要性分数聚类为 motif。
4. **NAM 启发**：Agarwal 等提出神经加法模型（NAM），将预测分解为各特征独立子网络的线性组合，实现线性模型级别的可解释性。
5. **本文位置**：将 NAM 思想引入基因组序列建模，用多个单滤波器 CNN 单元替代单一复杂网络，每个单元对应一个可解释的 PWM 类 motif，实现「设计即解释」。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 黑箱模型难以解释 | DanQ、DeepSTARR 等模型预测准确但无法直接看出依据的序列特征 | 多层非线性变换和特征组合掩盖了输入-输出关系 | Background 节：深度学习模型「opaque; they do not readily reveal the features」 |
| Filter visualization 依赖架构 | 滤波器可视化效果受 max pooling、滤波器大小等选择影响 | 池化层和深层组合破坏单滤波器与 motif 的对应关系 | Background 节：可视化「highly dependent on model architectural choices such as max pooling or filter sizes」 |
| 全局解释计算昂贵 | 需逐滤波器消融（nullification）才能评估各滤波器对预测的贡献 | 消融需重新推理多次，且需设定任意阈值 | Background 节：消融「computationally intensive and dependent on arbitrary thresholds」 |
| Attribution 缺乏全局性 | DeepLIFT 等提供局部核苷酸重要性，但无法直接回答「哪个 motif 驱动了预测」 | 重要性分数需进一步聚类（如 TF-MoDISco）才能形成 motif | Background 节：attribution「provide local interpretability...quantifying the contribution of each feature to the overall model's predictions remains challenging」 |
| 模型不透明阻碍采用 | 非深度学习专家难以信任和使用黑箱模型 | 缺乏共识性的解释实践 | Discussion 节：模型「adoption...remains largely in the hands of deep learning experts」 |

## 06 核心思想
1. **表面方法**：将 NAM 架构应用于基因组序列——模型由多个独立 CNN 单元组成，每个单元仅含一个卷积滤波器（19×4），后接 batch norm、指数激活、max pooling 和两个全连接层；所有单元输出通过最终线性层加权求和得到预测。
2. **核心洞察**：每个单元可视为一个独立的「PWM 扫描器」，其滤波器可直接可视化为 PWM 并比对 JASPAR 数据库获得生物学注释；最终线性层的权重天然提供全局可解释性（该单元对某任务的贡献），单元重要性分数（激活×权重）提供局部可解释性（该单元对某序列的贡献）。
3. **可能的普适教训** [Analysis]：**「约束架构以换取可解释性」比「事后解释黑箱」更高效**——通过将复杂模型分解为语义上可解释的独立单元，可同时获得性能与透明度，且避免了昂贵的消融计算。这一思路可迁移到其他需要「特征-预测」对应关系的生物序列任务。

## 07 方法总览
- **输入**：one-hot 编码的 DNA 序列（4×L，L 为序列长度）
- **输出**：任务相关预测（如 TF 结合概率、染色质可及性分数、enhancer 活性）
- **模块**：
  1. N 个独立单元（N 为超参数，如 100/300/400），每单元含：单滤波器卷积层（19×4）→ batch norm → 指数激活 → max pooling（kernel=7, stride=7）→ 全连接层（100 节点，batch norm + ReLU + 30% dropout）→ 全连接层（1 节点，batch norm + ReLU）
  2. 最终线性层：将 N 个单元输出加权求和，映射到任务输出维度
- **训练**：Adam 优化器，binary cross entropy 损失（PBM 数据用 MSE），学习率 0.003，batch size 100，early stopping
- **工具**：PyTorch 1.9.0；Tommot 用于 PWM-JASPAR 比对；DeepLIFT + TF-MoDISco 作为基线解释方法
- **反馈回路**：无显式反馈回路；训练后通过滤波器可视化→PWM→JASPAR 注释→单元重要性分数形成解释闭环
- **假设**：序列中的调控信息可分解为独立可加的 motif 识别模块（即假设调控逻辑以加性为主，非线性交互有限）

**文字流程**：输入序列 → one-hot 编码 → 并行送入 N 个独立单元 → 每单元滤波器扫描序列产生 motif 匹配信号 → 全连接层变换 → 最终线性层加权组合各单元输出 → 预测分数 → 训练后：每单元滤波器转为 PWM → Tomtom 比对 JASPAR → 单元获得生物学注释 → 权重/重要性分数用于全局/局部解释

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 单滤波器卷积层（19×4） | 扫描序列中与滤波器匹配的 motif 模式 | 每个滤波器可独立可视化为 PWM，实现「一单元一 motif」 | 输入：one-hot 序列；输出：匹配分数图 | Results 图 1A；滤波器可视化成功比对 JASPAR（Results 图 1E） | 预期：移除后单元失去可解释性，退化为普通 CNN 滤波器（[Analysis] 预期效应） |
| 指数激活 | 非线性变换匹配分数 | 已证明可改善滤波器恢复 motif 的能力 | 输入：卷积输出；输出：非线性变换后分数 | Methods 节引用 [26] | 预期：替换为 ReLU 可能降低 motif 恢复质量（[Analysis] 预期效应，基于引用文献） |
| max pooling（kernel=7, stride=7） | 降采样并保留最强匹配信号 | 压缩序列长度，提取局部最大值 | 输入：激活图；输出：池化后特征 | Methods 节 | 预期：移除后序列长度不变，计算量增加（[Analysis] 预期效应） |
| 两层全连接网络（100→1） | 将 motif 匹配信号转换为单元输出分数 | 提供单元内部的非线性变换，增强表达能力 | 输入：池化特征；输出：标量 | Methods 节 | 预期：移除后单元退化为纯线性扫描器，可能降低性能（[Analysis] 预期效应） |
| 最终线性层 | 加权组合各单元输出 | 实现 NAM 式加性组合，权重即全局重要性 | 输入：N 个单元输出；输出：任务预测 | Results 图 1F 热图展示权重可解释性 | 实测：移除后模型无法输出预测（核心组件，不可移除） |
| 单元重要性分数 | 计算每单元对每序列的贡献 | 提供局部可解释性，区分「该单元对该序列是否重要」 | 输入：单元激活×权重；输出：重要性值 | Results 图 1G 展示 FOXA1 单元重要性 | 预期：移除后失去局部解释能力（[Analysis] 预期效应） |

## 09 关键公式符号
本文未提供显式数学公式，以下为基于方法描述的符号化重建（[Analysis] 标注）：

- **单元输出**：$u_i(x) = f_i(\text{pool}(\text{conv}_i(x)))$，其中 $x$ 为 one-hot 输入序列，$\text{conv}_i$ 为第 $i$ 个单元的单滤波器卷积，$\text{pool}$ 为 max pooling，$f_i$ 为全连接网络
- **模型预测**：$\hat{y}(x) = \sum_{i=1}^{N} w_i \cdot u_i(x) + b$，其中 $w_i$ 为最终线性层权重，$b$ 为偏置
- **单元重要性分数**：$s_i(x) = w_i \cdot u_i(x)$（对特定输入序列 $x$）
- **PWM 转换**：滤波器权重 $F \in \mathbb{R}^{19 \times 4}$ 直接作为 PWM 的 log-odds 表示，通过 softmax 或概率转换得到位置频率矩阵

## 10 实验设计与证据链
**数据集与指标**：
- **TF 结合预测**：163 个 TF 的 ChIP-seq 数据（52 种细胞/组织类型），1.8M+ 个 200bp DHS 区域；指标：AUPRC
- **染色质可及性**：AI-TAC 数据集（81 种免疫细胞类型，6 个谱系）；指标：平均 PCC
- **Enhancer 活性**：DeepSTARR 数据集（果蝇发育/管家增强子）；指标：PCC
- **De novo motif 发现**：163 TF 的 ChIP-seq 数据；指标：最佳 PWM 的 AUPRC、与 JASPAR 的比对
- **scATAC-seq**：人类胰岛数据集（15,298 细胞，12 簇）；指标：单元权重/重要性的生物学一致性

**基线模型**：DanQ、DeepSTARR、AI-TAC、CNN1、CNN1Exp、DeepCNN

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| TF 结合预测性能 | ExplaiNN 与复杂模型性能相当 | 50 TF 子集，100 单元 ExplaiNN vs DanQ/DeepCNN | ExplaiNN 平均 AUPRC 优于 CNN 模型，接近 DanQ | 加性架构不牺牲预测性能 | 未超过 DanQ，不能声称更优 | Results 图 1B-C |
| 单元数量影响 | 更多单元提升性能 | 1-200 单元 | 性能随单元数增加而提升，~100 单元饱和 | 单元数可调，性能-可解释性可权衡 | 未测试 >200 单元 | Results 图 1B |
| Motif 恢复能力 | ExplaiNN 滤波器可恢复已知 TF motif | 163 TF，100 单元模型 vs STREME | 85.3% TF 的最佳 PWM 来自前 10 重要单元；核受体可恢复完整 motif | 滤波器可视化可发现高质量 motif | 小数据集 TF 上 STREME 更优 | Results 图 3A-C |
| 核受体 motif | ExplaiNN 可恢复完整核受体 motif | 12 个核受体 vs STREME | ExplaiNN 恢复完整 motif，STREME 仅部分 | 加性架构利于恢复长/复杂 motif | 仅核受体家族 | Results 图 3E |
| 跨平台一致性 | ExplaiNN 在不同 assay 中表现一致 | GATA3 的 ChIP-seq、HT-SELEX、PBM、SMiLE-seq | 各 assay 的 motif 一致且与 JASPAR 匹配 | 通用 de novo motif 发现工具 | 仅测试 GATA3 | Results 图 3F-G |
| 染色质可及性预测 | ExplaiNN 与 AI-TAC 性能相当 | 81 免疫细胞类型，300 单元 vs AI-TAC | PCC 差异 1-2%，AI-TAC 略优 | 可解释模型在复杂任务上仍具竞争力 | 未超过 AI-TAC | Results 图 4A-B |
| 谱系特异性 motif | ExplaiNN 识别已知谱系 TF motif | 免疫细胞 6 谱系 | 识别 NFE2/NFI/GATA（干细胞）、POU/EBF/PAX（B 细胞）等 | 权重热图提供全局可解释性 | 未与 ChIP-seq 直接验证 | Results 图 4C |
| 同源 TF 区分 | ExplaiNN 可区分相似 DNA 结合域 TF | IRF4 vs IRF8，PAX5 vs PAX3/7 | 单元重要性显示不同谱系特异性 | 可区分同家族 TF 功能差异 | 仅免疫细胞数据 | Results 图 6E-F |
| 非线性交互检测 | ExplaiNN 无法捕获异源 cooperativity | DeepSTARR 数据集，距离依赖性分析 | ExplaiNN 无距离依赖性，DeepSTARR 有 | 加性架构限制异源互作建模 | 同源 cooperativity 可捕获 | Results 图 2 |
| 迁移学习 | 预训练 DanQ 单元可嵌入 ExplaiNN | 350 个 DanQ 模型嵌入 | 性能接近 AI-TAC，且保留单元可解释性 | 灵活架构支持模块替换 | 仅测试 DanQ | Results 图 6D-G |

## 11 结论正确解读
- **任务范围**：本文结论仅适用于序列级预测任务（TF 结合、染色质可及性、enhancer 活性），不涉及 3D 基因组结构或蛋白质-DNA 物理互作。
- **Oracle/真值输入**：所有训练标签来自实验数据（ChIP-seq、ATAC-seq、STARR-seq 等），无模拟或 oracle 输入。
- **端到端状态**：ExplaiNN 是端到端训练的完整模型，非辅助解释工具。
- **算力成本**：训练时间远低于复杂模型（作者声称更快，但未提供具体数值）。
- **历史数据依赖**：模型依赖训练数据的实验条件和细胞类型，跨条件泛化未验证。
- **模型依赖**：性能与单元数相关，最优单元数需针对任务调优。
- **最难情形**：异源 cooperativity（不同 TF motif 间的非线性互作）无法捕获；小样本 TF 的 motif 发现不如 STREME。
- **群体/领域边界**：仅验证了脊椎动物（人类、小鼠）和果蝇数据，未测试其他物种。
- **不确定性**：未提供置信区间或多次运行的标准差。

**有边界的复述**：ExplaiNN 在 TF 结合位点预测、染色质可及性预测和 de novo motif 发现任务上，以加性单滤波器 CNN 单元组合的架构，达到了与 DanQ、AI-TAC 等复杂模型接近的预测性能，同时通过滤波器可视化和单元权重/重要性分数提供了全局与局部可解释性；但该架构无法捕获异源 TF 协同互作，且在小样本数据集上 motif 发现能力弱于专用工具。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 无法捕获异源 cooperativity | 距离依赖性分析显示 ExplaiNN 无法学习不同 TF motif 间的非线性互作 | 集成更复杂架构以处理非线性交互 | Results 图 2；Discussion 节 |
| 大感受野任务受限 | 无法处理需要大感受野的任务（如 Enformer、Basenji 类） | 在系统内实现更大感受野能力 | Discussion 节 |
| 小数据集 motif 发现弱 | 对训练数据量小的 TF，motif 发现不如 STREME | 未明确提及 | Results 图 3C |
| 冻结滤波器限制 | 冻结 JASPAR 初始化滤波器时性能下降 | 允许滤波器微调（unfreezing） | Results 图 6B-C |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 加性架构的性能优势可能依赖任务简单性 | TF 结合预测和染色质可及性可能本身以加性调控为主，复杂非线性任务（如增强子-启动子互作）可能表现不佳 | 决定 ExplaiNN 的适用范围边界 | 在已知强非线性互作的数据集（如发育增强子）上系统比较 | Results 图 2 已显示异源 cooperativity 失败 |
| 「性能相当」的结论基于有限基准 | 仅对比 DanQ、DeepSTARR、AI-TAC，未与最新模型（如 Enformer、Borzoi）比较 | 无法评估 ExplaiNN 在更复杂模型面前的竞争力 | 在相同数据集上对比更多 SOTA 模型 | Results 图 1B、4A |
| 单元重要性分数的生物学验证较浅 | 仅通过已知 TF 功能进行定性验证，缺乏定量指标 | 可解释性的「正确性」需严格验证 | 与 ChIP-seq 峰内 motif 富集做定量比较 | Results 图 4D-E、6E-F |
| 未报告超参数敏感性 | 单元数、学习率等超参数对性能-可解释性权衡的影响未系统分析 | 用户难以选择最优配置 | 对关键超参数做网格搜索并报告方差 | Methods 节未提供敏感性分析 |
| 与 PWM 扫描的等价性未严格证明 | 滤波器虽可转为 PWM，但全连接层可能引入位置依赖，与经典 PWM 扫描不等价 | 影响「可解释性」的严格性 | 比较 ExplaiNN 滤波器与独立 PWM 扫描的预测一致性 | Discussion 节提及全连接层可能编码位置信息 |
| 训练数据规模影响未充分讨论 | 163 TF 数据集中各 TF 的 ChIP-seq 数据量差异大，小样本 TF 性能下降 | 实际应用中数据量不均很常见 | 按数据量分层报告性能 | Results 图 3C 显示数据量影响 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **「加性可解释架构」设计模式**：将复杂预测任务分解为多个语义可解释的独立子网络（单元），通过线性组合输出，可在保持性能的同时获得天然可解释性。**可迁移到 TF–DNA 结合预测**：每个单元可对应一个 TF 结合 motif，直接输出「哪些 TF 驱动了该区域的结合预测」。

2. **滤波器→PWM 的直接转换流程**：单滤波器 CNN 的权重可直接转为 PWM 并与 JASPAR 比对，避免了事后解释的复杂流程。**可迁移到物理模拟**：若用 CNN 学习 MD 模拟中的结合自由能图谱，滤波器可转为结合基序，直接与实验 motif 比对验证。

3. **单元重要性分数（激活×权重）作为局部解释**：比单纯权重或激活更精细，可区分「该单元对该序列是否真正重要」。**可迁移到 TF–DNA 互作**：用于识别特定基因组位点由哪些 TF 驱动结合，辅助解析细胞类型特异的调控逻辑。

4. **冻结预训练单元作为先验注入**：用 JASPAR PWM 初始化滤波器并冻结，可注入已知 TF 结合先验，但需允许微调以保持性能。**可迁移到物理模拟**：用已知蛋白-DNA 复合物结构初始化模型，加速结合模式学习。

5. **「同源 TF 区分」的验证范式**：通过单元重要性区分 DNA 结合域高度相似的 TF（如 IRF4 vs IRF8），验证模型分辨率。**可迁移到 TF–DNA 互作研究**：用于解析旁系同源 TF 的靶基因差异。

6. **跨 assay 一致性验证**：在 ChIP-seq、HT-SELEX、PBM、SMiLE-seq 等不同实验数据上验证 motif 发现一致性，增强方法可信度。**可迁移到 AI 方法评估**：多数据源交叉验证可避免单一 assay 的系统偏差。

## 15 与已有知识连接
- **神经加法模型（NAM）**：本文直接受 Agarwal et al. (2021) NAM 启发，将 NAM 从表格数据扩展到基因组序列。可进一步探索 NAM 在其他生物序列任务（RNA 结合、剪接位点预测）的应用。
- **DanQ (Quang & Xie, 2016)**：本文主要对比的混合 CNN-LSTM 模型，ExplaiNN 在性能上接近但解释性更强。可对比两者在 TF 结合预测上的特征学习差异。
- **DeepSTARR (de Almeida et al., 2022)**：本文在 enhancer 活性预测任务上对比 DeepSTARR，并验证 ExplaiNN 无法捕获异源 cooperativity。可进一步研究如何扩展 ExplaiNN 以处理非线性互作。
- **AI-TAC (Maslova et al., 2022)**：本文在染色质可及性预测任务上对比 AI-TAC，并采用其滤波器转 PWM 的流程。可对比两者在免疫细胞分化调控逻辑上的发现。
- **TF-MoDISco (Shrikumar et al., 2018)**：本文对比了基于 DeepLIFT + TF-MoDISco 的事后解释流程，ExplaiNN 避免了这一复杂流程。可评估两种解释方法在 motif 发现上的一致性。
- **JASPAR 数据库 (Fornes et al., 2020)**：本文使用 JASPAR 2020 脊椎动物库进行 PWM 注释。可扩展至其他物种或最新版本。
- **Tomtom (Gupta et al., 2007)**：本文使用 Tomtom 进行 PWM 相似性比对。可探索其他 motif 比对工具（如 STAMP）的互补性。
- **候选方向 [Analysis]**：ExplaiNN 的架构思想可与 AlphaFold 等结构预测模型结合，将结构特征作为单元输入，预测 TF 结合特异性；或与 MD 模拟结合，用 ExplaiNN 单元表示模拟中识别的结合模式。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：ExplaiNN-3D：结合三维结构特征的 TF–DNA 结合预测
   - **来源局限/观察**：ExplaiNN 仅使用序列信息，未利用 TF 的 3D 结构特征；TF–DNA 结合特异性受结构约束。
   - **核心假设**：将 TF 的 DNA 结合域结构特征（如来自 AlphaFold 或 PDB）编码为额外单元输入，可提升结合预测精度并解释结构-序列协同。
   - **初步方法**：在 ExplaiNN 架构中增加结构特征单元，与序列单元并行，最终线性组合；用 PDB 中 TF-DNA 复合物验证。
   - **验证方式**：在 TF 结合预测基准上对比 ExplaiNN-3D 与 ExplaiNN；检查结构单元是否捕获已知的 DNA 识别机制。
   - **创新状态**：unverified

2. **候选名称**：ExplaiNN-MD：用 MD 模拟增强的 TF–DNA 结合 motif 发现
   - **来源局限/观察**：ExplaiNN 的 motif 发现依赖实验 ChIP-seq 数据，缺乏物理互作信息；MD 模拟可提供结合自由能细节。
   - **核心假设**：MD 模拟衍生的结合自由能图谱可作为 ExplaiNN 单元的先验或辅助输入，提高 motif 发现精度，尤其对弱结合 TF。
   - **初步方法**：对目标 TF-DNA 复合物进行 MD 模拟，提取 per-nucleotide 结合自由能；将自由能特征作为 ExplaiNN 单元的辅助输入或初始化权重。
   - **验证方式**：在已知弱结合 TF 数据集上比较 ExplaiNN-MD 与标准 ExplaiNN 的 motif 发现性能。
   - **创新状态**：unverified

3. **候选名称**：ExplaiNN-Cooperativity：扩展以捕获异源 TF 协同互作
   - **来源局限/观察**：ExplaiNN 无法捕获异源 cooperativity（Results 图 2），限制了其在复杂调控区域的应用。
   - **核心假设**：在 ExplaiNN 的线性组合层中增加成对交互项，可捕获异源 TF 间的协同效应而不牺牲整体可解释性。
   - **初步方法**：在最终线性层中增加单元对的乘积项（类似二阶 NAM），正则化以保持稀疏性；在 DeepSTARR 数据集上验证。
   - **验证方式**：对比 ExplaiNN-Cooperativity 与 ExplaiNN、DeepSTARR 在 enhancer 活性预测上的 PCC 和 motif 互作检测能力。
   - **创新状态**：unverified

4. **候选名称**：ExplaiNN-scRNA：单细胞分辨率下的 TF 结合调控逻辑解析
   - **来源局限/观察**：ExplaiNN 已应用于 scATAC-seq（Results 图 5），但未与单细胞转录组（scRNA-seq）整合。
   - **核心假设**：将 ExplaiNN 单元重要性与 scRNA-seq 表达的 TF 活性整合，可解析细胞类型特异的 TF 调控网络。
   - **初步方法**：在 scATAC-seq 上训练 ExplaiNN，将单元重要性矩阵与 scRNA-seq 的 TF 表达进行关联分析。
   - **验证方式**：在已知细胞分化轨迹上验证识别的 TF 调控逻辑与实验一致。
   - **创新状态**：unverified

5. **候选名称**：ExplaiNN-Transfer：跨物种 TF–DNA 结合模型迁移
   - **来源局限/观察**：ExplaiNN 在人类和小鼠数据上分别训练，未探索跨物种迁移。
   - **核心假设**：在人类数据上预训练的 ExplaiNN 单元可迁移至小鼠，通过微调适应物种特异的 DNA 结合偏好。
   - **初步方法**：人类 TF 数据预训练 ExplaiNN，在小鼠数据上微调；评估迁移后 motif 发现性能。
   - **验证方式**：对比迁移学习与从头训练在跨物种 TF 结合预测上的 AUPRC。
   - **创新状态**：unverified