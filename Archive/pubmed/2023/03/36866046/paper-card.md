## 01 基本信息
- **标题**: DeepBend: An interpretable model of DNA bendability
- **作者**: Khan, Samin Rahman; Sakib, Sadman; Rahman, M Sohel; Samee, Md Abul Hassan
- **单位**: 未提供（通讯作者：Md. Abul Hassan Samee, samee@bcm.edu，贝勒医学院）
- **期刊/平台**: iScience
- **年份**: 2023-03-04
- **论文类型**: 研究论文（含方法学创新）
- **领域**: 计算基因组学 / 深度学习可解释性 / DNA力学性质
- **关键词**: DNA bendability, convolutional neural network, interpretable model, Loop-Seq, sequence motifs, chromatin conformation
- **DOI/arXiv**: 10.1016/j.isci.2023.105945
- **代码**: https://github.com/SameeLab-BCM/DeepBend
- **数据**: Loop-Seq数据集（Basu et al. 2021）、酵母Hi-C数据（Costantino et al. 2020）、核小体dyad位置（Brogaard et al. 2012）、SGD基因组数据
- **阅读日期**: 未提供
- **在课题方向中的位置**: 本文属于「蛋白质-DNA互作 × 深度学习」交叉方向，聚焦于DNA内在力学性质（bendability）的序列决定因素。虽不直接建模TF-DNA结合，但bendability是TF-DNA结合的重要物理前提，且其可解释CNN架构（multinomial convolution + 空间模式层）可直接迁移至TF-DNA结合基序发现与结合机制解析。

## 02 一句话总结
本文提出DeepBend——一个三层CNN回归模型，通过multinomial convolution层直接学习DNA bendability的序列基序，并通过第二层宽卷积和方差正则化揭示基序的周期性与相对空间排列对bendability的调控，在预测性能与DNACycP相当的同时提供机制性解释，并发现新基序GAAGAGC及bendability与染色质TAD边界形成的关联。

## 03 研究问题
- **具体问题**: DNA序列中哪些基序（motifs）及其空间排列模式决定DNA的内在可弯曲性（bendability）？这些模式如何影响染色质高级结构？
- **为什么重要**: DNA bendability直接影响核小体包装、蛋白质-DNA结合（包括TF结合）以及染色质三维结构。理解其序列决定因素有助于解析基因调控的物理基础。
- **现有方法不足**: 
  - 基于手工特征的模型（如Basu et al. 2021）仅使用二核苷酸频率和周期性，预测精度有限（r≈0.6），且无法发现新基序。
  - 黑箱深度模型（如DNACycP）预测精度高但缺乏可解释性，post hoc分析难以系统识别基序及其空间关系。
  - 缺乏能同时实现高精度与直接机制解释的模型。
- **精确研究问题**: Can a convolutional neural network with biologically grounded multinomial convolutions simultaneously achieve state-of-the-art prediction accuracy of DNA bendability and directly reveal the sequence motifs and their spatial arrangement patterns that determine bendability?

## 04 背景与发展脉络
*（注：以下脉络基于本文引用与论述，标注为「经外部核验」的部分来自文中引用的文献信息）*

1. **DNA bendability的生化测量**（经外部核验）: Basu et al. (2021) 开发Loop-Seq实验，高通量测量酵母全基因组50bp片段的bendability（内在环化能力），提供了大规模训练数据。
2. **基于手工特征的建模**（经外部核验）: Basu et al. (2021) 使用二核苷酸频率、周期性等特征建立线性模型，r≈0.6，可解释但精度有限。
3. **黑箱深度模型**（经外部核验）: DNACycp (Li et al.) 使用CNN-RNN混合架构，精度更高但缺乏直接解释能力。
4. **可解释深度学习的兴起**（经外部核验）: 可见神经网络（visible neural networks）思想（如MuSeAM, Park et al. 2022）将领域知识编码进网络结构，使模型内部表征直接可解释。
5. **本文位置**: DeepBend将MuSeAM的multinomial convolution思想引入bendability预测，并创新性地加入第二层宽卷积以捕获基序间空间关系，配合方差正则化实现基序贡献方向的清晰分离，是「可解释深度学习 × DNA力学性质」的代表性工作。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 预测精度与可解释性不可兼得 | 手工特征模型r≈0.6，黑箱模型精度高但无法直接解释 | 手工特征无法捕获复杂基序组合；黑箱模型内部表征难以映射到生物学概念 | Results节：Basu模型r=0.6 vs DeepBend r=0.87-0.90；DNACycp需post hoc分析 |
| Post hoc解释方法不可靠 | 重要性分析需选择多个阈值参数，缺乏系统方法 | 梯度/相关性传播方法对阈值敏感，且无法揭示基序间空间关系 | Introduction节：post hoc方法涉及阈值选择，系统方法不明确 |
| 基序空间排列信息丢失 | 传统模型仅考虑基序出现频率，忽略相对位置 | 固定特征（如k-gapped二核苷酸）无法覆盖所有可能的基序间距 | Introduction节：固定特征如k-gapped二核苷酸或k-mer计数 |
| 新基序发现困难 | 已知基序（二核苷酸、AT/GC-tract）无法解释全部bendability变异 | 可能存在更复杂的序列模式未被手工特征捕获 | Results节：DeepBend发现新基序GAAGAGC（Motif #40） |
| 基序贡献方向不明确 | 同一基序在不同上下文中可能促进或抑制bendability | 基序的空间排列决定其功能效应 | Results节：Motif #196在周期排列时正贡献、持续排列时负贡献 |

## 06 核心思想

### 1) 表面方法
- 三层CNN回归模型：第一层为multinomial convolution（256个8bp基序滤波器），第二层为宽卷积（捕获基序间空间关系），第三层为单滤波器卷积输出预测值。
- 输入为50bp one-hot编码DNA序列（同时处理正链和反向互补链）。
- 训练目标为Loop-Seq测得的bendability值（回归任务）。
- 通过方差正则化使第二层滤波器权重沿位置轴稳定，从而清晰分离正/负贡献模式。

### 2) 核心洞察
- **基序是概率分布而非确定性序列**：将卷积滤波器参数化为multinomial分布（每个位置4个核苷酸的概率），使滤波器直接可解释为序列基序的position weight matrix (PWM)，无需post hoc分析。
- **空间排列是bendability的关键调控维度**：第二层宽卷积（长度40）捕获基序在50bp窗口内的相对位置关系，揭示基序的周期性（如10bp螺旋周期）和相互排列（如交错分布）对bendability的贡献。
- **方差正则化实现贡献方向分离**：通过约束第三层权重沿位置轴的方差，使每个第二层滤波器要么整体正贡献、要么整体负贡献，避免同一滤波器在不同位置符号翻转导致的解释困难。

### 3) 可能的普适教训 [Analysis]
- 将领域知识（如PWM、基序周期性）直接编码进网络结构，比事后解释黑箱模型更可靠、更高效。
- 对于序列-表型映射问题，捕获特征间的空间关系往往比增加特征数量更重要。
- 正则化不仅可以防止过拟合，还可以作为「可解释性工程」工具，引导网络内部表征符合生物学直觉。

## 07 方法总览

- **输入**: 50bp DNA序列的one-hot编码（4×50矩阵），同时输入正链和反向互补链。
- **输出**: 预测的bendability值（连续标量，对应Loop-Seq的环化率对数比）。
- **第一层**: Multinomial convolution，256个滤波器，每个尺寸8×4，stride=1，same padding。滤波器权重经softmax变换为概率分布，直接解释为8bp基序的PWM。ReLU激活。
- **第二层**: 标准1D convolution，2-16个滤波器（默认2个），每个尺寸40×256，stride=1，same padding。捕获基序在50bp窗口内的空间分布模式。ReLU激活。
- **第三层**: 单滤波器1D convolution，尺寸50×n_filters（n_filters为第二层滤波器数），无padding，输出单个标量。线性激活。
- **方差正则化**: 对第三层权重沿位置轴施加方差惩罚，使第二层各滤波器的贡献方向一致。
- **训练**: 使用TensorFlow/Keras实现，损失函数为均方误差（MSE），优化器未明确说明（推测为Adam），超参数（滤波器数、长度、正则化强度）通过验证集调优。
- **解释流程**: 训练后直接读取第一层滤波器权重→变换为PWM→获得基序；读取第二层滤波器权重→获得基序空间排列模式；结合第三层权重符号→判断正/负贡献。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Multinomial convolution层（第一层） | 学习可解释的序列基序 | 使滤波器直接映射为PWM，避免post hoc分析 | 输入：one-hot序列；输出：基序匹配分数矩阵 | Results节：滤波器直接可视化为基序，确认已知基序（二核苷酸、AT/GC-tract）并发现新基序 | 预期影响：若替换为标准卷积，基序提取需post hoc分析，可能丢失弱基序 [Analysis] |
| 宽卷积层（第二层） | 捕获基序间空间排列模式 | 基序的相对位置关系（周期性、交错）是bendability的重要决定因素 | 输入：基序匹配分数矩阵；输出：空间模式匹配分数 | Results节：揭示10bp周期性正贡献模式、持续排列负贡献模式；Figure 3A-C | 预期影响：若移除，模型退化为仅考虑基序频率，预测精度下降且无法解释空间效应 [Analysis] |
| 方差正则化 | 稳定第三层权重沿位置轴的符号 | 防止同一滤波器在不同位置符号翻转，确保解释清晰 | 输入：第三层权重矩阵；输出：正则化损失项 | Methods节：明确说明加入方差正则化以分离正/负贡献模式 | 实测影响：未提供消融实验；预期影响：移除后滤波器贡献方向可能混杂，解释性显著下降 [Analysis] |
| 双链处理（正链+反向互补链） | 同时检测两条链上的基序 | DNA基序可能以链对称方式起作用 | 输入：正链和反向互补链one-hot编码；输出：两套匹配分数 | Methods节：第一、二层并行应用于两条链 | 预期影响：若移除，可能遗漏反向互补链上的关键基序 [Analysis] |
| 第三层单滤波器卷积 | 聚合空间模式分数为最终预测 | 将各位置的空间模式匹配分数加权求和 | 输入：空间模式匹配分数矩阵；输出：标量预测值 | Methods节：单滤波器、线性激活 | 预期影响：若替换为全连接层，可能丧失位置信息且增加过拟合风险 [Analysis] |

## 09 关键公式符号

**1. Multinomial convolution变换**（Methods节，Equation 1）:
$$m_i = \max_{j=0}^{3}(W_{i,j})$$
$$T_{i,j} = \frac{e^{\alpha \cdot (W_{i,j} - m_i)}}{\sum_{j=0}^{3} e^{\alpha \cdot (W_{i,j} - m_i)}}$$

- $W_{i,j}$: 原始卷积权重，$i$为滤波器位置索引，$j$为核苷酸索引（0-3对应A/C/G/T）
- $T_{i,j}$: 变换后的概率权重，构成PWM
- $m_i$: 行最大值，用于数值稳定
- $\alpha$: 特异性参数（本文取75.0），控制PWM的锐利程度

**2. Multinomial convolution操作**（Methods节，Equation 2）:
$$\sum_{i=0}^{L} \sum_{j=0}^{3} \ln(T_{i,j} \cdot B_j) \cdot s_{i,j}$$

- $L$: 序列长度（50bp）
- $B_j$: 背景核苷酸频率
- $s_{i,j}$: one-hot编码的输入序列子段

**3. 方差正则化损失**（Methods节）:
$$V_i = \frac{1}{l_2} \sum_{j}^{l_2} (W_{i,j} - \bar{W_i})^2$$
$$L = \frac{1}{n_2} \sum_{i}^{n_2} V_i$$

- $W_{i,j}$: 第三层权重，$i$为第二层滤波器索引，$j$为位置索引
- $l_2$: 位置维度长度（50）
- $n_2$: 第二层滤波器数
- $\bar{W_i}$: 第$i$个滤波器权重的均值

**4. Bendability quotient**（Methods节）:
$$Q(kmer) = \frac{1}{N}\sum_{i}^{N} y_i \cdot I(kmer \in seq_i)$$
- 定义为包含某k-mer的序列的平均bendability值，用于独立验证基序重要性。

## 10 实验设计与证据链

### 数据集与评测协议
- **训练数据**: Loop-Seq四个文库——Random（12,472条随机序列）、ChrV（82,404条酵母V号染色体序列）、Nucleosomal（19,907条核小体高占据区序列）、Tiling（82,368条，来自576个基因的±1核小体区域）
- **数据划分**: 对ChrV和Tiling文库，训练/测试集按染色体位置分离，确保测试序列与训练序列在基因组上不重叠（Methods节）
- **指标**: Pearson相关系数r（预测bendability与真实值）
- **对比模型**: Basu et al. 线性模型（二核苷酸特征）、SVM、Random Forest、DNACycp（CNN-RNN混合）、标准CNN、CNN-RNN
- **解释验证**: 基序匹配分数与已知bendability基序对比；GAAGAGC的bendability quotient独立验证；TAD边界/结构域bendability分析

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|------------|-------------------|------|
| 预测性能基准测试 | DeepBend预测精度与SOTA相当 | 各模型在Random/Nucleosomal/ChrV/Tiling测试集上比较r | Random: 0.87; Nucleosomal: 0.89; ChrV: 0.74; Tiling: 0.90（与DNACycp相当） | DeepBend在保持可解释性的同时达到SOTA精度 | 未证明DeepBend在所有条件下严格优于DNACycp（差异不显著） | Results节, Table 1 |
| 基序发现与验证 | DeepBend能发现已知和新型bendability基序 | 可视化第一层PWM，与文献已知基序对比 | 确认二核苷酸（TT、TA等）、AT/GC-tract；发现新基序GAAGAGC（Motif #40） | 模型学到的基序与生化知识一致，且能发现新基序 | 新基序的因果作用需进一步实验验证 | Results节, Figure 2B |
| GAAGAGC独立验证 | GAAGAGC是强bendability促进基序 | 计算bendability quotient（Random文库中所有7-mer比较） | GAAGAGC和GCTCTTC为最高bendability quotient的7-mer | 独立于模型确认GAAGAGC的bendability促进作用 | 未做突变实验证明因果性 | Results节, Figure 4A-B |
| 空间模式分析 | 基序的周期性和排列影响bendability | 分析第二层滤波器权重模式 | 正贡献基序呈~10bp周期性；负贡献基序呈持续排列 | 基序空间排列是bendability的重要调控维度 | 未系统量化不同排列模式的效应大小 | Results节, Figure 3 |
| TAD边界bendability分析 | bendability与染色质结构相关 | 比较TAD边界与结构域内部的预测bendability | 边界区域更刚性（bendability更低），结构域内部更柔性 | bendability基序可能参与TAD边界形成 | 相关性不等于因果性；未控制其他因素 | Results节, Figure 5 |
| 消融/替代架构比较 | 各层贡献及架构选择的合理性 | 对比标准CNN、CNN-RNN、不同第二层滤波器数 | DeepBend精度与DNACycp相当，优于标准CNN | 架构设计有效 | 未提供逐模块消融实验数据 | Results节, Table S2 |

## 11 结论正确解读

- **任务范围**: 本文仅针对酵母（S. cerevisiae）50bp DNA片段的bendability预测，未涉及其他物种或其他长度。
- **预测目标**: 预测的是内在bendability（Loop-Seq测得的环化能力），而非蛋白质-DNA结合强度或特异性。
- **可解释性边界**: 模型可解释性限于第一层基序PWM和第二层空间模式；第三层为黑箱聚合，无法解释基序间非线性交互的具体机制。
- **新基序GAAGAGC**: 其bendability促进作用经bendability quotient独立验证，但未通过实验突变验证因果性；其生物学功能（如是否影响TF结合）仅为推测。
- **TAD边界关联**: 相关性分析，未控制混杂因素（如CTCF类似蛋白、复制起点等），不能得出bendability直接导致TAD边界形成的结论。
- **性能比较**: DeepBend与DNACycp性能「相当」（r差异≤0.01），并非显著优于；其优势在于可解释性而非精度。
- **端到端状态**: 模型为端到端训练（序列→bendability），但解释过程（基序提取、模式分析）为训练后处理，非训练过程中自动生成。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 超参数未穷尽搜索 | 基序数量、长度、第二层滤波器数等未系统优化 | 寻找最优基序和模式表征的高效搜索算法 | Limitations节 |
| 基序表征非最优 | 密集排列的基序可能由不同基序组合共同表征，非唯一解 | 改进基序表征方法 | Limitations节 |
| 模型泛化性未验证 | 仅在酵母数据上训练和测试 | 探索其他物种和功能性质的适用性 | Limitations节 |
| 基序结构基础未探究 | 未研究新基序（如GAAGAGC）的结构基础 | 研究新基序的结构基础 | Limitations节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 性能比较仅报告r值 | 未报告RMSE、R²等绝对误差指标；r对线性变换不变，可能掩盖系统偏差 | 影响对模型实际预测能力的判断 | 补充报告RMSE、MAE、R²及误差分布图 | Results节仅给出r值 |
| 基序重要性排序依赖全局重要性分析 | 该方法假设基序独立贡献，忽略基序间交互效应 | 可能高估/低估某些基序的真实作用 | 使用交互检测方法（如SHAP交互值）交叉验证 | Methods节：全局重要性分析 |
| GAAGAGC验证仅用bendability quotient | 该统计量受序列组成混淆影响，未控制GC含量等 | 可能将GC含量效应误归因于特定基序 | 使用置换检验或匹配对照序列验证 | Results节, Figure 4A |
| TAD边界分析未控制已知边界因子 | 酵母TAD边界与多种因素相关（如tRNA基因、复制起点） | 可能将其他因素的效应归因于bendability | 多变量回归控制已知边界相关特征 | Results节, Figure 5 |
| 第二层滤波器数量（2个）过少 | 可能无法捕获所有重要的空间模式类型 | 限制模型表达力 | 系统扫描滤波器数量并比较解释质量 | Methods节：超参数调优 |
| 未与实验扰动验证结合 | 所有结论基于计算预测，缺乏实验验证 | 计算模型可能存在系统性偏差 | 对预测的高/低bendability序列进行体外环化实验验证 | 全文未提及实验验证 |

## 14 学到什么
*（Agent 提炼的知识候选）*

1. **可解释CNN架构设计范式**: 将生物物理先验（PWM/基序）直接编码为网络层（multinomial convolution），使模型内部表征天然可解释。可迁移至TF-DNA结合预测：用multinomial convolution学习TF结合基序，替代传统position weight matrix扫描。
2. **空间模式捕获策略**: 第二层宽卷积（长度接近输入序列）可捕获基序间的周期性（如10bp螺旋周期）和相对排列，这对TF-DNA结合中的基序间距、相对方向（二聚体结合位点）建模有直接借鉴意义。
3. **方差正则化作为可解释性工具**: 通过约束高层权重沿位置轴的方差，迫使网络形成「整体正/负贡献」的清晰分离，避免解释模糊。可用于TF结合预测中区分激活/抑制型基序组合。
4. **双链并行处理**: 同时处理正链和反向互补链，避免遗漏链对称基序。对TF-DNA结合预测尤为重要，因为TF可结合双链任一方向。
5. **全局重要性分析流程**: 通过逐基序消融（置零）计算对预测的贡献，可系统评估每个基序的重要性。可迁移至TF结合基序重要性排序。
6. **bendability作为TF结合的物理特征**: 本文揭示的bendability基序可整合为TF-DNA结合预测模型的结构特征（如局部DNA柔性特征），提升预测精度。
7. **TAD边界与bendability关联**: 提示DNA力学性质可能参与染色质结构域形成，TF结合位点可能倾向于位于特定bendability环境，可作为TF结合位点预测的上下文特征。

## 15 与已有知识连接

- **Loop-Seq技术**（Basu et al., Nature 2021）: 本文使用的数据来源，该技术测量DNA内在环化能力，与TF-DNA结合实验（如SELEX、HT-SELEX）互补。
- **MuSeAM模型**（Park et al., Genes 2022）: 本文第一层multinomial convolution的直接来源，该模型用于转录因子结合位点预测，本文将其扩展至bendability预测并增加空间模式层。
- **DNACycp模型**（Li et al.）: 本文主要对比的深度模型，为CNN-RNN混合架构，预测bendability但缺乏可解释性。
- **DNA形状特征**（DNAShape, Chiu et al. 2015）: 本文用DNAShapeR分析GAAGAGC的结构特征（HelT、MGW、ProT、Roll），与TF-DNA结合中的shape readout概念直接相关。
- **核小体定位与DNA力学**（Brogaard et al. 2012; Struhl & Segal 2013）: 本文核小体dyad数据来源，核小体定位与DNA bendability密切相关，TF结合常发生在核小体排斥区域。
- **TAD边界与染色质结构**（Costantino et al. 2020; Hsieh et al. 2016）: 本文TAD边界分析的数据来源，酵母TAD边界与启动子、tRNA基因等相关，本文补充了bendability维度。
- **可解释深度学习在基因组学中的应用**（综述类）: 本文属于「visible neural networks」思潮的一部分，与TF-DNA结合预测中的可解释模型（如DeepSEA、BPNet的后续可解释变体）形成互补。

## 16 研究想法
*（Agent 生成的研究候选）*

### 候选1: TF-DNA结合的可解释基序-间距联合模型
- **名称**: Interpretable TF-DNA Binding Model with Motif Spacing Awareness
- **来源局限/观察**: DeepBend证明bendability由基序及其空间排列共同决定；TF-DNA结合同样依赖基序间距（如二聚体协同结合），但现有深度模型多忽略间距信息。
- **核心假设**: 将DeepBend的「基序层+空间模式层」架构迁移至TF-DNA结合预测，可同时实现高精度与基序间距的机制性解释。
- **初步方法**: 以HT-SELEX或ChIP-seq数据为训练集，第一层用multinomial convolution学习TF结合基序，第二层用宽卷积捕获基序间距模式，输出结合强度。
- **验证方式**: 与现有TF结合预测模型（如DeepSEA、BPNet）比较AUC；用已知协同结合TF对（如Fos-Jun）验证间距模式合理性。
- **创新状态**: unverified

### 候选2: bendability基序作为TF结合预测的结构特征
- **名称**: Integrating Bendability Motifs into TF-DNA Binding Prediction
- **来源局限/观察**: DeepBend发现bendability基序（如GAAGAGC）与染色质结构相关；TF结合需要DNA局部柔性，但现有TF结合模型未显式使用bendability特征。
- **核心假设**: 将DeepBend预测的bendability值或基序匹配分数作为TF结合预测模型的附加特征，可提升预测精度，尤其对间接结合或需要DNA弯曲的TF。
- **初步方法**: 在TF结合预测模型输入中拼接bendability预测值或bendability基序匹配分数；比较有无该特征的性能差异。
- **验证方式**: 在多个TF的ChIP-seq数据集上比较AUC；分析bendability特征对结合预测的贡献权重。
- **创新状态**: unverified

### 候选3: 基于MD模拟验证DeepBend新基序的力学机制
- **名称**: Molecular Dynamics Validation of DeepBend-Predicted Bendability Motifs
- **来源局限/观察**: DeepBend预测GAAGAGC为最强bendability促进基序，但未提供结构机制解释；MD模拟可揭示序列如何通过局部结构柔性影响DNA弯曲。
- **核心假设**: GAAGAGC通过降低局部螺旋稳定性或改变小沟宽度来促进DNA弯曲，MD模拟可定量验证。
- **初步方法**: 对含GAAGAGC及其突变体的DNA片段进行MD模拟，计算弯曲刚度、小沟宽度、螺旋参数等；与DeepBend预测对比。
- **验证方式**: MD计算的弯曲自由能与Loop-Seq测量值相关性；突变体模拟与预测一致。
- **创新状态**: unverified

### 候选4: 跨物种bendability基序保守性分析
- **名称**: Cross-Species Conservation Analysis of Bendability Motifs
- **来源局限/观察**: DeepBend仅在酵母上训练，其发现的基序是否在高等真核生物中保守未知；TF结合基序常跨物种保守。
- **核心假设**: bendability相关基序在真核生物中保守，且保守的bendability基序富集在TF结合位点附近。
- **初步方法**: 用DeepBend在人类、小鼠等基因组上预测bendability，分析基序保守性；与TF结合位点数据库（如ENCODE）交叉分析。
- **验证方式**: 保守基序的bendability贡献一致性；保守bendability基序与TF结合位点的共定位显著性。
- **创新状态**: unverified

### 候选5: 可解释CNN用于TF-DNA结合特异性的物理机制解析
- **名称**: Physical Mechanism Discovery via Interpretable CNN for TF-DNA Specificity
- **来源局限/观察**: DeepBend的可解释架构成功解析了bendability的序列决定因素；类似方法可解析TF-DNA结合特异性中的「直接读取」（碱基接触）与「间接读取」（结构变形）机制。
- **核心假设**: 用multinomial convolution学习TF结合基序，结合DNA形状特征（DNAShape），可区分直接读取与间接读取的贡献。
- **初步方法**: 对多个TF的HT-SELEX数据训练可解释CNN，提取基序PWM与形状特征；分析基序内保守形状模式。
- **验证方式**: 与已知TF-DNA共晶结构对比，验证基序内关键接触位点；形状特征与MD模拟结果交叉验证。
- **创新状态**: unverified