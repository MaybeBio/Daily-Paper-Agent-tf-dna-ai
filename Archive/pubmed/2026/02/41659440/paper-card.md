## 01 基本信息
- **标题**：TPCAV: Interpreting deep learning genomics models via concept attribution
- **作者与单位**：Yang, Jianyu; Mahony, Shaun（宾夕法尼亚州立大学，Center for Eukaryotic Gene Regulation）
- **期刊/预印本平台**：bioRxiv（预印本服务器）
- **年份**：2026
- **论文类型**：方法学论文（提出新解释方法）
- **领域**：计算基因组学、深度学习可解释性
- **关键词**：概念归因、TCAV、深度学习、基因组学、TF结合预测、可解释AI
- **DOI/arXiv 号**：10.64898/2026.01.20.700723
- **代码**：https://github.com/seqcode/TPCAV
- **数据**：ENCODE Dream Challenge数据集、Vierstra lab motif数据库、RepeatMasker注释、ENCODE DNase/ATAC-seq数据
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA互作（TF–DNA结合机制）× AI」方向中的**模型可解释性**子方向。它提出了一种基于概念归因的全局解释方法，可直接用于解析TF–DNA结合预测模型所依赖的序列特征（如motif、染色质状态、重复元件），是该方向中少数能处理非one-hot输入（如tokenized DNA、多模态输入）的解释工具。

## 02 一句话总结
本文提出TPCAV方法，通过在概念激活向量计算前引入PCA去相关变换，解决了原始TCAV在基因组学深度模型（特征冗余且相关）中概念归因方向不稳定的问题，并实现了对多种输入格式（one-hot、tokenized、多模态）和多种任务（单TF结合、多任务BPNet）的全局概念级解释。

## 03 研究问题
- **具体问题**：如何对基因组学深度学习模型进行全局、输入格式无关的概念级归因解释？特别是当模型嵌入层存在高度相关、冗余的特征时，如何保证概念归因的方向（正/负）可靠？
- **为什么重要**：基因组学深度模型（如TF结合预测、染色质状态预测）已被广泛使用，但其内部决策机制难以理解。现有局部归因方法（如DeepLIFT、Saliency）难以总结全局规律；而全局方法TF-MoDISco仅适用于one-hot DNA输入，无法处理tokenized输入或多模态输入（如序列+染色质信号）。
- **现有方法不足**：原始TCAV在图像领域表现良好，但在基因组学模型中，由于嵌入层特征高度相关且冗余（多个节点共同编码同一motif，但方向可能相反），线性分类器可能错误地利用负向节点，导致概念归因方向错误（如CTCF motif被误判为负贡献）。
- **精确研究问题**：Can a PCA-decorrelated concept attribution framework (TPCAV) provide reliable, input-agnostic global interpretation of genomics deep learning models across diverse architectures and input modalities?

## 04 背景与发展脉络
*注：以下脉络基于本文框架，未经外部系统核验，标注为「仅本文框架」。*

1. **局部归因时代**：DeepLIFT、Saliency maps等逐位置归因方法，可解释单个输入对预测的贡献，但难以总结全局规律。
2. **全局归因（one-hot限定）**：TF-MoDISco通过聚类归因分数中的序列片段（seqlets）来发现motif，但仅适用于one-hot DNA输入，无法处理tokenized输入或非序列特征。
3. **概念归因（图像领域）**：TCAV（Testing with Concept Activation Vectors）通过概念样本与随机样本在嵌入层的线性可分性，定义概念方向（CAV），并计算预测对该方向的敏感性。但TCAV假设嵌入特征相对独立，在基因组学模型中失效。
4. **TPCAV（本文）**：在TCAV流程中引入PCA去相关变换，解决冗余特征导致的CAV方向不稳定问题，并扩展至多模态、多任务、tokenized输入场景。

**本文主张的位置**：TPCAV是首个系统性地将概念归因应用于基因组学深度模型的方法，填补了全局解释方法在非one-hot输入场景的空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 原始TCAV在基因组学模型中归因方向错误 | CTCF motif在HepG2 CTCF结合模型中被判为负贡献；NANOG motif在H1-hESC NANOG模型中被判为负贡献 | 嵌入层存在多个相关节点共同编码同一motif，但部分节点对预测有正贡献、部分有负贡献；线性分类器可能利用负向节点作为判别特征，导致CAV方向反转 | Results 图1b；Results 图1c（展示多个节点对CTCF motif响应但方向相反） |
| 嵌入特征高度相关 | 同一motif由多个节点冗余编码，节点间相关性高 | 基因组学模型常使用卷积+Transformer架构，特征提取层存在大量冗余表示 | Results 图1d（PCA变换前后相关性对比）；Supplementary Figure S1a |
| 现有全局方法无法处理非one-hot输入 | TF-MoDISco仅适用于one-hot DNA；tokenized模型（如DNABERT-2）和多模态模型（如maxATAC）无法用TF-MoDISco解释 | TF-MoDISco依赖序列级别的归因分数聚类，无法处理token嵌入或非序列特征 | Introduction；Results 图3a（TPCAV成功解释DNABERT-2） |
| 缺乏对非序列概念（如染色质状态、重复元件）的全局归因 | 现有方法无法评估染色质状态、重复元件等非序列特征对预测的贡献 | 概念归因框架天然支持任意输入类型的概念定义，但此前未在基因组学中系统应用 | Results 图2c（重复元件概念分析）；Results 图3c（开放染色质概念分析） |

## 06 核心思想
1. **表面方法**：将TCAV概念归因框架引入基因组学，并在CAV计算前对嵌入层激活进行PCA去相关变换（TPCAV）。同时引入motif概念敏感性评分（motif concept sensitivity score）和概念特异性归因图（concept-specific attribution maps）两个新工具。
2. **核心洞察**：基因组学深度模型的嵌入层特征高度冗余且相关，原始TCAV的线性分类器会利用这些相关特征中的“异常值”节点（方向相反的节点）来分类，导致CAV方向错误。PCA去相关后，每个主成分方向独立，线性分类器无法再“钻空子”，CAV方向更稳定、更符合生物学直觉。
3. **可能的普适教训** [Analysis]：**任何基于嵌入层线性可分性的解释方法，在特征高度相关的模型中都需要先做去相关处理**。这一教训不仅适用于基因组学，也适用于其他高冗余表示的学习任务（如蛋白质语言模型、多模态模型）。此外，**概念归因的价值在于将“黑箱”模型的决策与人类可理解的生物学概念（motif、染色质状态、重复元件）对接**，这为TF–DNA结合机制研究提供了一种“假设检验”工具——可以验证模型是否依赖已知的调控元件，或发现新的候选调控特征。

## 07 方法总览
- **输入**：任意格式的输入样本（one-hot DNA序列、tokenized DNA序列、序列+染色质信号多模态输入）；概念样本集（如含特定motif的序列、特定重复元件区域、开放染色质区域）和随机对照样本集。
- **输出**：每个概念对模型预测的全局归因分数（TPCAV score，正/负/零）；概念特异性输入归因图（concept-specific attribution maps）；概念敏感性评分（motif concept sensitivity score）。
- **模块**：
  1. 嵌入层激活提取：从目标模型指定层（通常是最后一层卷积/Transformer层）提取激活向量。
  2. PCA去相关变换：对概念样本和对照样本的标准化激活进行SVD分解，得到变换矩阵V，将激活投影到主成分空间（保留残差）。
  3. 概念分类器训练：在PCA变换后的特征空间训练线性SVM（L2正则化，SGD优化），区分概念样本与对照样本。
  4. TPCAV score计算：对每个测试样本，计算其激活沿CAV方向的梯度（通过DeepLIFT归因），得到该样本对概念的敏感性分数。
  5. 概念特异性归因图：将DeepLIFT归因分数投影到CAV方向，得到仅由该概念解释的输入归因图。
- **训练**：TPCAV本身不训练目标模型，仅训练概念分类器（SVM）。目标模型为预训练模型（本文中为自训练的TF结合预测模型、DNABERT-2、maxATAC、BPNet）。
- **反馈回路**：TPCAV score可用于评估模型对概念的依赖程度，若某概念分数异常（如CTCF motif在CTCF模型中为负），提示模型可能依赖了非预期的特征，需进一步检查。
- **文字流程**：定义概念样本集和对照样本集 → 从目标模型指定层提取激活 → 对激活做标准化和PCA去相关 → 训练线性SVM分类器 → 得到CAV方向 → 对测试样本计算DeepLIFT归因 → 将归因投影到CAV方向 → 得到TPCAV score和概念特异性归因图。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| PCA去相关变换 | 对嵌入层激活进行去相关，消除冗余特征对CAV方向的干扰 | 基因组学模型嵌入层特征高度相关，原始TCAV的线性分类器会利用方向相反的冗余节点，导致CAV方向错误 | 输入：标准化激活矩阵X_std；输出：PCA投影Z（含残差） | Results 图1b（TPCAV修正了CTCF/NANOG motif方向）；Results 图1d（PCA后相关性显著降低） | 移除后TPCAV退化为原始TCAV，在基因组学模型中归因方向不可靠（实测：CTCF motif方向错误） |
| 概念分类器（线性SVM） | 在PCA空间中区分概念样本与对照样本，得到CAV方向 | 概念方向需要从数据中学习，线性分类器提供可解释的方向向量 | 输入：PCA投影Z和标签y；输出：CAV权重向量w_cav | Methods节（SGDClassifier，L2正则化，网格搜索alpha） | 移除后无法定义概念方向，TPCAV score无法计算 |
| DeepLIFT层归因 | 计算每个输入位置对模型输出的贡献分数 | 需要将概念方向映射回输入空间，得到概念特异性归因图 | 输入：测试样本和基线样本；输出：层归因分数C | Methods节（Layer DeepLift，10个随机基线平均） | 移除后无法生成概念特异性归因图，只能得到全局TPCAV score |
| 概念特异性归因图 | 将归因分数投影到CAV方向，得到仅由该概念解释的输入区域 | 区分“模型使用了该概念”和“模型使用了与该概念相关的其他特征” | 输入：DeepLIFT归因分数C和CAV权重w；输出：概念特异性归因图 | Results 图5c（motif实例周期性出现）；Supplementary Figure S8 | 移除后无法定位概念在输入中的具体位置 |
| motif概念敏感性评分 | 通过不同motif插入数下的F-score曲线下面积，校正GC含量偏差后排名 | 不同motif的GC含量不同，影响分类器可分离性，需要校正 | 输入：不同插入数下的F-score；输出：校正后的敏感性评分 | Results 图2a；Methods节（IC_GC加权线性回归） | 移除后motif排名受GC含量偏差影响，可能高估GC-rich motif的重要性 |

## 09 关键公式符号
1. **F-score**（概念分类器性能）：
   \[
   F\text{-score} = \frac{2 \cdot \text{precision} \cdot \text{recall}}{\text{precision} + \text{recall}}
   \]
   用途：衡量概念样本与对照样本在嵌入层的可分离性。

2. **标准化**：
   \[
   X_{\text{std}} = \frac{X - \mu}{\sigma}, \quad X \in \mathbb{R}^{m \times n}, \mu \in \mathbb{R}^n, \sigma \in \mathbb{R}^n
   \]
   用途：PCA前的数据标准化。

3. **SVD分解**：
   \[
   X_{\text{std}} = U \Sigma V^T, \quad V \in \mathbb{R}^{n \times \min(m,n)}
   \]
   用途：得到PCA变换矩阵V。

4. **PCA投影与残差**：
   \[
   X_{\text{proj}} = X_{\text{std}} V, \quad X_{\text{res}} = X_{\text{std}} - X_{\text{proj}} V^T
   \]
   \[
   Z = \begin{cases} [X_{\text{proj}}; X_{\text{res}}] & \text{if } X_{\text{res}} \neq 0 \\ X_{\text{proj}} & \text{else} \end{cases}
   \]
   用途：保留主成分方向信息的同时，不丢失残差信息（因m<n时SVD无法完全分解）。

5. **TPCAV score**：
   \[
   S_{\text{tpcav}} = M \odot \text{abs}(A_{\text{input}} - A_{\text{baseline}}) \times W_{\text{concept}}
   \]
   其中M为DeepLIFT乘子，A为激活值，W_concept为CAV方向权重。用途：计算测试样本沿概念方向的敏感性。

6. **概念特异性归因**：
   \[
   Z_{\text{projected}} = Z Q Q^T, \quad Z_{\text{orthogonal}} = Z - Z_{\text{projected}}
   \]
   其中Q来自CAV矩阵的QR分解。用途：将激活分解为概念方向分量和正交分量，仅回传概念方向分量的梯度。

7. **GC加权信息含量**：
   \[
   IC_{GC} = \sum_{i=1}^{k} r_i^{GC} \cdot IC_i
   \]
   其中r_i^GC为位置i的GC比例，IC_i为位置i的信息含量，k为motif长度。用途：校正motif敏感性评分中的GC含量偏差。

## 10 实验设计与证据链
- **数据集**：
  - TF结合预测模型：ENCODE Dream Challenge数据集（HepG2和H1-hESC细胞系，多个TF）
  - 多模态模型：maxATAC（ATF2在GM12878，RUNX1在K562）
  - 多任务模型：BPNet（小鼠ES细胞，Oct4/Sox2/Klf4/Nanog）
  - 基础模型：DNABERT-2、Nucleotide Transformer、HyenaDNA（预训练权重）
- **指标**：概念分类器F-score；TPCAV score（正/负/零）；motif概念敏感性评分；与TF-MoDISco结果的一致性
- **基线**：原始TCAV；TF-MoDISco
- **评测协议**：对每个模型，定义概念样本集（motif嵌入序列、重复元件区域、开放染色质区域）和对照样本集（随机基因组序列），计算TPCAV score并排名。

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|------------|------|-------------|-------------------|------|
| 同源motif概念在TF结合模型中的归因 | TPCAV能正确识别同源motif的正贡献 | 对比原始TCAV；CTCF在HepG2，NANOG在H1-hESC | 原始TCAV将CTCF/NANOG motif判为负贡献；TPCAV修正为正贡献 | PCA去相关解决了冗余特征导致的CAV方向错误 | 未在更多TF/细胞系中系统验证 | Results 图1b |
| motif概念排名与TF-MoDISco对比 | TPCAV的motif归因与TF-MoDISco的motif发现一致 | 多个TF结合模型；对比TF-MoDISco的motif排名 | TPCAV识别的top motif与TF-MoDISco高度一致 | TPCAV提供与TF-MoDISco相当的motif级解释 | 未量化一致性指标（如排名相关系数） | Results 图2b |
| 重复元件概念归因 | TPCAV能评估重复元件对TF结合预测的贡献 | 多个TF模型；重复元件概念来自RepeatMasker | 低复杂度GC-rich重复元件在多数模型中为正贡献 | 模型可能使用GC含量作为染色质可及性的代理 | 未验证GC-rich重复元件与染色质可及性的因果关系 | Results 图2c |
| 基础模型（DNABERT-2）解释 | TPCAV能解释tokenized输入模型 | DNABERT-2微调后预测FOXA1结合 | FOXA1同源motif和JUND motif排名top | TPCAV适用于tokenized输入 | 未与其他tokenized模型解释方法对比 | Results 图3a |
| 多模态模型（maxATAC）解释 | TPCAV能解释非序列输入（染色质信号） | ATF2在GM12878，RUNX1在K562 | 匹配细胞系的开放染色质概念最可分类且正贡献 | TPCAV能评估染色质信号对预测的贡献 | 未验证开放染色质概念与序列motif概念的交互 | Results 图3c,d |
| BPNet多任务模型解释 | TPCAV能区分不同任务对概念的依赖 | BPNet的4个TF×2个任务（count/profile） | 各任务依赖的motif概念与已知生物学一致；profile任务依赖更多motif | TPCAV能解析多任务模型的共享嵌入空间 | 未验证概念归因与实验扰动（如motif突变）的一致性 | Results 图4a-c |
| 概念特异性归因图 | 能定位概念在输入中的具体位置 | BPNet的Oct4 peak；SOX motif概念 | 归因图显示周期性motif实例 | 概念特异性归因图能定位概念实例 | 未与ChIP-exo等高分辨率实验对比 | Results 图5c |

## 11 结论正确解读
- **任务范围**：TPCAV是**解释工具**，不改进预测性能。它回答“模型依赖哪些概念”，不回答“这些概念在生物学上是否真实因果”。
- **Oracle/真值输入**：概念定义依赖人工选择的样本集（如motif嵌入序列、RepeatMasker注释），概念质量受注释数据库完整性影响。
- **端到端状态**：TPCAV是**post-hoc**解释方法，不参与模型训练。它需要访问模型中间层激活，因此要求模型可提供中间层输出。
- **算力成本**：PCA分解和SVM训练开销小（样本量通常为数千），但DeepLIFT归因需要前向和反向传播，对长序列（如1Mb）可能计算量大。
- **历史数据依赖**：概念样本集来自参考基因组注释（Vierstra motif库、RepeatMasker），对非参考基因组或新物种需重新构建。
- **模型依赖**：TPCAV结果依赖所选嵌入层。不同层可能编码不同抽象级别的概念，本文未系统比较层选择的影响。
- **最难情形**：概念样本与对照样本在嵌入层不可分（F-score低）时，TPCAV score不可靠；高度相似的motif家族可能难以区分。
- **群体/领域边界**：本文验证了TF结合预测、多模态、多任务、基础模型四类场景，但未涉及RNA结合蛋白、剪接预测等任务。
- **不确定性**：TPCAV score的显著性检验未提供（如bootstrap置信区间）；概念分类器训练存在随机性，未报告多次重复的方差。
- **有边界的复述**：TPCAV在本文测试的模型和概念类型中，提供了比原始TCAV更稳定、更符合生物学预期的概念归因结果，并能扩展到tokenized和多模态输入，但其生物学解释力仍需实验验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 概念定义依赖人工选择 | 概念样本集需手动构建，可能遗漏重要概念 | 探索自动概念发现方法 | Discussion |
| 概念分类器性能影响结果 | F-score低的分类器导致TPCAV score不可靠 | 未明确提及 | Results（F-score作为可分类性指标） |
| 未与实验验证结合 | TPCAV识别的概念未通过突变实验等验证 | 提出可用于生成可测试假设 | Discussion |
| 层选择未系统比较 | 不同嵌入层可能产生不同结果 | 未明确提及 | 未提供 |
| 基础模型比较有限 | 仅比较了DNABERT-2、Nucleotide Transformer、HyenaTransformer，未涵盖所有主流基础模型 | 未明确提及 | Results 图3b |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|----------------------|----------|----------|------|
| PCA去相关是否总是最优？ | PCA是线性变换，可能无法处理非线性相关；保留残差的做法可能引入噪声 | 如果嵌入层特征存在非线性依赖，PCA可能无法完全去相关 | 对比其他去相关方法（如ICA、白化）在相同任务上的表现 | Methods节（PCA+SVD） |
| 概念样本集构建的偏差 | motif嵌入序列的侧翼序列可能引入额外特征，影响分类器 | 概念定义的纯度直接影响归因结果 | 使用不同侧翼长度、不同随机种子构建概念集，检查结果稳定性 | Methods节（motif概念构建） |
| TPCAV score的绝对值意义不明 | 论文主要使用排名和方向（正/负），未讨论score绝对值的生物学含义 | 用户可能误读score大小 | 设计模拟实验，已知概念贡献强度，检验score是否线性反映 | Results 图2b（仅排名对比） |
| 与TF-MoDISco的一致性未量化 | 论文仅展示视觉一致性，未计算排名相关系数 | 无法判断TPCAV与现有方法的定量差异 | 计算Spearman相关系数、重叠率等指标 | Results 图2b |
| 基础模型比较的公平性 | 不同基础模型的微调策略、数据增强可能不同，影响公平比较 | 结论“DNABERT-2编码motif更好”可能受训练细节影响 | 统一微调流程、数据划分，多次重复 | Results 图3b |
| 概念特异性归因图的验证不足 | 仅展示单个peak的示例，未系统评估归因图质量 | 无法判断该方法在基因组规模上的可靠性 | 在多个peak集上计算归因图与已知motif位点的重叠率 | Results 图5c |
| 未讨论计算成本 | DeepLIFT归因在长序列上的计算开销未报告 | 影响方法在大规模基因组上的实用性 | 报告不同序列长度下的运行时间和内存 | 未提供 |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **概念归因框架（TCAV/TPCAV）**：可直接迁移到TF–DNA结合机制研究。通过定义“含某motif的序列”为概念，可检验预测模型是否依赖该motif，以及依赖方向（激活/抑制）。这为验证或发现TF结合机制提供了计算假设检验工具。
2. **PCA去相关预处理**：在分析嵌入层特征时，先做去相关可提高线性探针（如SVM分类器）的可靠性。这一技巧可迁移到其他嵌入层分析任务（如蛋白质语言模型的特征分析）。
3. **概念敏感性评分（motif concept sensitivity score）**：通过不同motif插入数下的F-score曲线下面积，校正GC含量偏差后排名，可系统评估模型对motif的敏感度。可迁移到TF–DNA结合预测模型的motif重要性排序。
4. **概念特异性归因图**：将归因分数投影到概念方向，可定位概念在输入中的具体位置。这可用于在基因组中扫描TF结合位点，或验证模型是否在正确位置使用motif。
5. **多模态概念定义**：将开放染色质信号与随机序列配对定义概念，可检验模型是否真正使用染色质信号而非序列代理特征。这一设计思路可迁移到其他多模态基因组模型（如ATAC+序列预测）。
6. **基础模型benchmark框架**：用概念分类F-score作为基础模型编码生物学信息的指标，可迁移到评估不同DNA基础模型（如DNABERT-2、Nucleotide Transformer）在TF–DNA结合任务上的表示质量。

## 15 与已有知识连接
- **TCAV（原方法）**：本文直接改进自Kim et al. (2018)的TCAV方法。原方法在图像分类中提出，本文首次系统应用于基因组学。可对比阅读原TCAV论文以理解改进动机。
- **TF-MoDISco**：本文多次与TF-MoDISco对比。TF-MoDISco是one-hot DNA模型的motif发现标准工具，TPCAV是其补充（可处理非one-hot输入）。
- **DeepLIFT**：本文使用DeepLIFT作为归因基础。DeepLIFT是局部归因方法，TPCAV将其扩展为全局概念归因。
- **ENCODE Dream Challenge**：本文使用的TF结合预测数据集，是TF–DNA结合预测的基准数据集。相关文献：ENCODE Dream Challenge (2017)。
- **DNA基础模型**：本文评估了DNABERT-2、Nucleotide Transformer、HyenaDNA。这些模型是当前DNA序列表示学习的前沿，可参考各自原始论文。
- **BPNet**：本文使用BPNet作为多任务模型案例。BPNet是碱基分辨率TF结合预测的经典模型，其原始论文（Avsec et al., 2021）值得参考。
- **maxATAC**：本文使用maxATAC作为多模态模型案例。该模型整合序列和ATAC-seq信号预测TF结合，相关文献可查。
- **候选方向** [Analysis]：本文的概念归因框架可进一步与**物理模拟**结合——例如，将MD模拟或分子对接得到的TF–DNA结合自由能作为“概念”，检验深度学习模型是否隐式学习了物理化学特征。这是一个未探索的交叉方向。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA结合特异性中的概念冲突检测
   - **来源局限/观察**：TPCAV发现某些motif在特定细胞系中贡献方向异常（如CTCF在HepG2中为负），可能反映了细胞系特异的调控机制或模型伪影。
   - **核心假设**：TF–DNA结合预测模型在不同细胞系中可能依赖不同的motif组合，且存在概念冲突（同一motif在不同细胞系中贡献方向相反）。
   - **初步方法**：使用TPCAV对多个细胞系的同一TF结合模型进行概念归因，比较motif概念的方向和强度，聚类分析细胞系特异的调控逻辑。
   - **验证方式**：与ChIP-seq实验数据对比，检查TPCAV识别的细胞系特异motif是否在对应细胞系中富集。
   - **创新状态**：unverified

2. **候选名称**：基于概念归因的DNA基础模型可解释性基准
   - **来源局限/观察**：本文比较了DNABERT-2、Nucleotide Transformer、HyenaTransformer的motif编码能力，但未提供系统化基准框架。
   - **核心假设**：DNA基础模型的嵌入空间对已知TF motif的线性编码能力可预测其在下游TF–DNA结合任务上的微调性能。
   - **初步方法**：构建包含数百个TF motif概念的标准概念库，对多个DNA基础模型计算概念分类F-score和TPCAV score，与下游微调性能（如TF结合预测AUPRC）做相关性分析。
   - **验证方式**：在多个下游任务和多个基础模型上验证相关性；检查是否与模型规模、训练数据组成相关。
   - **创新状态**：partially checked（本文已初步比较，但未系统化）

3. **候选名称**：多模态TF结合模型中的序列-染色质概念交互分析
   - **来源局限/观察**：TPCAV在maxATAC中发现开放染色质概念与GC-rich序列概念方向相反，提示模型可能使用染色质信号替代序列特征。
   - **核心假设**：在多模态TF结合预测模型中，序列motif概念和染色质可及性概念存在交互效应，且这种交互在不同细胞类型中不同。
   - **初步方法**：使用TPCAV分别评估序列motif概念和染色质概念在单模态与多模态模型中的贡献，分析概念间的协同或拮抗关系。
   - **验证方式**：通过消融实验（移除染色质输入）检验序列概念贡献是否增强，验证模型是否用染色质信号“掩盖”了序列特征。
   - **创新状态**：unverified

4. **候选名称**：概念归因引导的TF结合位点发现
   - **来源局限/观察**：TPCAV的概念特异性归因图可定位概念在输入中的位置，但本文仅展示了示例。
   - **核心假设**：概念特异性归因图可在全基因组范围内识别模型依赖的TF结合位点，且比传统motif扫描更准确（因为考虑了模型上下文）。
   - **初步方法**：对全基因组序列进行滑动窗口预测，使用概念特异性归因图定位高贡献区域，与ChIP-seq peak和已知motif位点对比。
   - **验证方式**：计算与ChIP-seq peak的重叠率，与FIMO等传统motif扫描工具对比。
   - **创新状态**：unverified

5. **候选名称**：物理化学概念注入的TF–DNA结合预测解释
   - **来源局限/观察**：TPCAV的概念定义完全基于序列或注释，未利用物理化学信息（如结合自由能、构象变化）。
   - **核心假设**：将MD模拟或分子对接得到的TF–DNA结合自由能作为概念，可揭示深度学习模型是否隐式学习了物理化学特征。
   - **初步方法**：对一组TF–DNA复合物进行MD模拟，计算结合自由能；将高/低自由能复合物的序列作为概念样本，使用TPCAV检验模型是否区分。
   - **验证方式**：若模型能区分高/低自由能概念，说明其隐式学习了物理化学特征；进一步分析归因图，识别关键接触残基。
   - **创新状态**：unverified