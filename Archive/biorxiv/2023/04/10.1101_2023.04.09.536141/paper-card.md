## 01 基本信息

- **标题**：Predicting splicing patterns from the transcription factor binding sites in the promoter with deep learning
- **作者与单位**：Tzu-Chieh Lin; Cheng-Hung Tsai; Cheng-Kai Shiau; Jia-Hsin Huang; Huai-Kuang Tsai（台湾中央研究院信息科学研究所，Institute of Information Science, Academia Sinica）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2023-04-09
- **论文类型**：方法学/计算生物学研究（预印本，未经同行评审）
- **领域**：计算生物学、转录调控、RNA剪接、深度学习
- **关键词**：alternative splicing、transcription factor binding sites、promoter、deep learning、CNN、ENCODE
- **DOI/arXiv 号**：10.1101/2023.04.09.536141
- **代码**：https://github.com/bio-it-station/DoTA
- **数据**：ENCODE 15个人体组织的 DNase-seq 和 RNA-seq 数据（GRCh37/GENCODE V19）
- **阅读日期**：未提供
- **在「蛋白质-DNA互作(聚焦TF–DNA结合机制) × AI方法/物理模拟」方向中的位置**：本文属于「TF–DNA 结合 → 下游功能输出」的调控链条建模，将启动子区 TFBS 占用状态作为输入特征，用 CNN 预测下游外显子剪接模式（PSI 变化）。与经典 TF–DNA 结合机制研究（如结合亲和力、结构域识别）不同，本文不关注 TF 如何物理结合 DNA，而是将 TFBS 占用作为调控信号，研究其与远端剪接事件的关联。对课题方向的可迁移点在于：TFBS 特征编码方式、跨组织差异建模、in silico 扰动分析识别关键 TF 的方法论。

## 02 一句话总结

本文利用 ENCODE 15 个人体组织的 DNase-seq 和 RNA-seq 数据，将启动子区域（−2 kb 至 +500 bp）内 TF 结合位点占用变化编码为特征，训练 CNN 模型预测基因第一盒式外显子的剪接模式变化（ΔZΨ），在 AUROC 达 0.889 的精度下验证了启动子 TFBS 组合与下游剪接调控的关联，并通过 in silico 扰动识别出 CTCFL 等候选剪接调控 TF。

## 03 研究问题

- **具体问题**：启动子区域的 TF 结合位点（TFBS）占用状态是否能够预测下游第一盒式外显子的剪接模式（包含/跳跃）变化？
- **为什么重要**：剪接调控的传统研究聚焦于外显子/内含子附近的顺式元件和剪接因子结合位点，而启动子区域如何通过转录偶联机制影响远端剪接事件尚不清楚。如果启动子 TFBS 组合确实携带剪接调控信息，将为理解「转录-剪接偶联」提供新的调控层级，并可能揭示疾病相关剪接异常的新的调控位点。
- **现有方法不足**：已有剪接预测模型（如 splicing code 类方法）主要使用外显子/内含子序列特征、剪接因子基序、RNA-seq 定量等，未系统纳入启动子区域 TF 结合信息；且多数模型在单一组织或细胞系中训练，缺乏跨组织的泛化评估。
- **精确研究问题（Can...?）**：Can the changes of TF binding occupancy in the promoter region predict the changes of splicing patterns (PSI) of the first cassette exon across human tissues?

## 04 背景与发展脉络

**注：以下脉络基于本文引用与论述，属「仅本文框架」，未经外部系统核验。**

1. **剪接调控的序列编码时代（~2010s）**：Barash et al. (2010) 提出 "splicing code"，利用外显子/内含子序列特征、剪接因子结合基序等预测组织特异性剪接。后续深度学习方法（如 SpliceAI、MMSplice 等）进一步提升精度，但特征仍集中于剪接位点附近。
2. **转录-剪接偶联的机制研究**：RNA Pol II 延伸速率、CTD 磷酸化状态、染色质环境等被证明影响共转录剪接。启动子结构（如启动子类型、TF 组成）可通过影响 Pol II 过程性来间接调控剪接（Cramer et al. 1997; Kornblihtt 2007）。
3. **启动子-TF 与剪接关联的个案证据**：少数基因（如 CD44、FGFR2）被证明启动子结合的 TF（如 SR 蛋白、CTCF）可通过招募剪接因子或改变 Pol II 延伸来影响剪接，但缺乏全基因组尺度的系统验证。
4. **本文主张的位置**：首次在全基因组尺度、跨 15 个人体组织，以启动子 TFBS 占用变化为特征，用机器学习/深度学习预测剪接模式变化，填补「启动子 TF 组合 → 剪接输出」的系统性建模空白。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 启动子与剪接的关联缺乏全基因组证据 | 已有研究多为单基因机制验证，缺乏系统尺度分析 | 缺乏整合启动子 TF 结合与剪接定量的计算方法 | Background 末段："the relationship between promoter-bound transcription factors and the downstream alternative splicing remains largely unexplored" |
| 跨组织剪接预测的泛化困难 | 组织间 TF 表达差异大，TFBS 占用变化复杂 | 需要高质量配对数据（同一组织的 DNase-seq 与 RNA-seq） | Results 节：仅选用 ENCODE 中 15 个同时具有 DNase-seq 和 RNA-seq 的组织 |
| 传统 ML 难以处理 TFBS 位置信息 | 使用 TFBS 变化频率作为特征时性能下降约 6%（AUROC） | 频率特征丢失了 TFBS 在启动子中的位置分布信息 | Results 节："The overall performance of prediction of splicing phase change was decreased about 6% based on AUROC" |
| 基因共享启动子特征导致数据泄漏 | 同一基因在不同组织中的启动子序列相同，TFBS 基序位置高度相似 | 事件/组织维度的交叉验证可能高估性能 | Results 节 Fig. 1E-G：基因维度验证（gene-wise CV）性能显著下降至接近随机 |
| 剪接效率的度量标准不统一 | 绝对 PSI 值跨基因分布不均，直接比较不公平 | 不同基因的 PSI 范围差异大，需按基因标准化 | Results 节 Fig. 2A："some genes that had a smaller PSI range (< 0.2) and/or expressed in less than three tissues were discarded" |

## 06 核心思想

### 1) 表面方法
构建启动子区域（−2 kb 至 +500 bp）内 345 个 TF 基序的占用变化矩阵（2,500 bp × 345 TF），以组织对之间的差异作为输入，用 CNN 预测第一盒式外显子剪接效率变化（ΔZΨ）的二分类标签。

### 2) 核心洞察
- **启动子 TFBS 组合携带剪接调控信息**：尽管 TFBS 位于启动子而剪接发生在外显子/内含子边界，CNN 仍能以高精度（AUROC 0.889）从启动子 TFBS 变化预测剪接变化，说明启动子区域的调控信号确实通过某种机制（如 Pol II 延伸偶联、染色质环化）传递到剪接位点。
- **位置信息是关键**：将 TFBS 从「有无」变为「位置分布」表示后，CNN 显著优于 DNN，说明 TFBS 在启动子中的相对位置（而非仅存在与否）对剪接调控有重要影响。
- **跨组织差异是信号而非噪声**：通过组织对之间的差异编码，将静态的 TFBS 占用转化为动态变化，捕捉了组织特异性剪接的调控逻辑。

### 3) 可能的普适教训 [Analysis]
- **特征表示决定模型上限**：同样的生物学信息（TFBS），用频率 vs. 位置分布表示，模型性能差异显著。在蛋白质-DNA 互作建模中，将结合位点的空间分布信息编码为序列/位置特征，可能比简单的二值化占用更有效。
- **验证方案设计影响结论可靠性**：本文通过三种 CV 方案（event-wise、tissue-wise、gene-wise）揭示了数据泄漏问题，说明在跨组织/跨条件的调控建模中，必须考虑样本间非独立性。
- **扰动分析是解释深度学习模型的实用工具**：in silico zero-out 方法简单有效，可迁移到其他 TF–DNA 互作模型中识别关键调控因子。

## 07 方法总览

- **输入**：启动子区域（−2 kb 至 +500 bp）内 TFBS 占用变化矩阵。具体为 2,500 bp 的启动子区域，345 个 TF 基序（JASPAR 2018，排除融合 TF 和重复版本），每个位置记录该 TF 是否在开放染色质区域（DNase-seq peak）内有基序匹配（FIMO, FDR < 10⁻³），并过滤 TF 表达（TPM > 1）。组织对之间的差异构成输入矩阵。
- **输出**：二分类标签——第一盒式外显子剪接效率变化（ΔZΨ）是否超过阈值（变化 vs. 不变）。
- **模型**：
  - 逻辑回归（Logistic Regression）
  - XGBoost（梯度提升树）
  - DNN：3 层全连接（512→256→128），ReLU + Dropout(25%)
  - CNN：1D 卷积层 + ReLU + MaxPooling（窗口 10，步长 10）+ Dropout，后接 2 层全连接（128→128）
- **训练**：PyTorch 框架，五折交叉验证，balanced sampler 处理类别不平衡
- **特征重要性分析**：in silico zero-out 扰动——将每个 TF 的输入通道置零，计算预测标签变化比例（N_changed / N_total）
- **数据流程**：
  1. ENCODE 下载 15 个组织的 DNase-seq peak 和 RNA-seq BAM
  2. 启动子区域定义（−2 kb 至 +500 bp from TSS）
  3. FIMO 扫描 TF 基序 → 候选 TFBS
  4. 过滤 TF 表达（TPM > 1）→ 推定占用 TFBS
  5. RNA-seq 经 CATANA 注释剪接事件，MISO 计算 PSI
  6. Z-score 标准化 PSI（按基因），定义剪接效率变化标签
  7. 组织对差异编码 → 训练/评估模型

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| TFBS 占用推断 | 将 DNase-seq 开放染色质 + JASPAR 基序扫描 + TF 表达过滤整合为推定 TFBS | 需要将「潜在结合位点」转化为「可能实际占用的位点」 | 输入：DNase-seq peak、JASPAR 基序、RNA-seq 表达；输出：每个启动子的 TFBS 占用矩阵 | Methods 节 "Identification of putative in vivo TF binding sites" | 若仅用基序扫描不滤表达，将引入大量假阳性 TFBS，降低信噪比 [预期效应] |
| 剪接模式量化 | 用 MISO 计算 PSI，Z-score 标准化 | 需要统一的剪接效率度量以跨基因比较 | 输入：RNA-seq BAM、CATANA 注释；输出：每个基因第一盒式外显子的 ZΨ | Methods 节 "RNA-seq processing and calculation of cassette exon usage (PSI)" | 若直接用绝对 PSI，跨基因比较不公平，模型可能学到基因长度等混淆因素 [预期效应] |
| 组织对差异编码 | 将两个组织的 TFBS 占用和 ZΨ 差异作为样本 | 将静态特征转化为动态变化，捕捉组织间调控差异 | 输入：两个组织的 TFBS 矩阵和 ZΨ；输出：差异矩阵 + 二分类标签 | Results 节 Fig. 2B | 若用绝对占用而非差异，模型可能学到组织身份而非剪接调控 [预期效应] |
| CNN 架构 | 1D 卷积学习 TFBS 位置组合模式 | 捕获 TFBS 在启动子中的空间分布和共定位模式 | 输入：2,500 bp × 345 TF 差异矩阵；输出：剪接变化概率 | Results 节 Fig. 4B：CNN AUROC 0.889 优于 DNN 0.853 | 移除卷积层（仅用 DNN）性能下降约 3.6% AUROC [实测消融效应] |
| In silico zero-out 重要性分析 | 逐个将 TF 通道置零，测量预测变化 | 识别对剪接预测贡献最大的 TF | 输入：训练好的 CNN + 测试集；输出：每个 TF 的重要性分数 | Results 节 Fig. 5A：识别出 19 个候选 TF | 无此模块则模型为黑箱，无法生成可验证的生物学假设 [预期效应] |
| 三种交叉验证方案 | event-wise / tissue-wise / gene-wise | 评估模型泛化能力，检测数据泄漏 | 输入：全部样本；输出：三种方案下的性能指标 | Results 节 Fig. 1E-G：gene-wise 性能接近随机 | 仅用 event-wise 会高估模型泛化能力 [实测消融效应] |

## 09 关键公式符号

**1. Z-score 标准化（ZΨ）**

$$Z_{\Psi} = \frac{\Psi - \mu_g}{\sigma_g}$$

- $\Psi$：该基因在特定组织的 PSI 值
- $\mu_g$：该基因在所有组织中的平均 PSI
- $\sigma_g$：该基因在所有组织中的 PSI 标准差
- 用途：将不同基因的 PSI 值标准化到可比尺度，消除基因间 PSI 分布差异
- 直觉：衡量某组织中外显子使用相对于该基因自身基线的高低

**2. Tau 组织特异性指数**

$$\tau = \frac{\sum_{i=1}^{n} (1 - \hat{x}_i)}{n - 1}, \quad \hat{x}_i = \frac{x_i}{\max_{1 \leq j \leq n} x_j}$$

- $x_i$：TF 在组织 $i$ 中的表达量（TPM）
- $n$：组织数量
- 用途：衡量 TF 表达的组织特异性，$\tau \geq 0.8$ 定义为组织特异性 TF
- 直觉：$\tau$ 接近 1 表示该 TF 仅在少数组织中高表达

**3. 输出变化比（Importance Score）**

$$\text{Importance}_k = \frac{N_{\text{changed}}^{(k)}}{N_{\text{total}}}$$

- $N_{\text{changed}}^{(k)}$：将 TF $k$ 的输入通道置零后，预测标签发生变化的样本数
- $N_{\text{total}}$：总测试样本数
- 用途：衡量 TF $k$ 对模型预测的贡献度
- 直觉：若某 TF 对剪接预测至关重要，置零后大量样本的预测结果会翻转

**4. 卡方检验（χ²）与比值比（OR）**

- 用于 2×2 列联表检验 TFBS 占用与剪接模式的关联
- $OR = \frac{a \cdot d}{b \cdot c}$（$a, b, c, d$ 为列联表四格频数）
- 用途：评估单个 TF 的占用变化与剪接相位变化的关联强度
- 直觉：OR > 1 表示 TF 占用与剪接变化正相关

## 10 实验设计与证据链

**数据集与评测协议：**
- **数据来源**：ENCODE 15 个人体组织（DNase-seq + RNA-seq 配对）
- **样本规模**：未提供具体数字（仅提及 15 个组织）
- **特征规模**：345 个 TF 基序 × 2,500 bp 启动子区域
- **标签定义**：第一盒式外显子剪接效率变化（ΔZΨ），分为变化/不变二分类
- **评测指标**：AUROC、AUPRC、F1-score、accuracy
- **验证方案**：五折交叉验证，三种划分方式（event-wise、tissue-wise、gene-wise）
- **基线模型**：逻辑回归、XGBoost、DNN
- **主要模型**：CNN（1D 卷积）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| TFBS 基序富集分析 | 启动子 TFBS 组成与剪接模式相关 | 排除组 vs. 包含组，χ² 检验，Bonferroni 校正 | 超过半数 TF 基序显著富集于某一剪接模式组 | 启动子 TFBS 组成与剪接模式存在统计关联 | 关联不等于因果，未控制连锁不平衡 | Results 节 Fig. 1D |
| 三种 ML 模型预测剪接相位变化 | TFBS 变化可预测剪接相位变化 | LR vs. XGB vs. DNN，五折 CV | AUROC：LR 0.691，XGB 0.771，DNN 0.766 | 树模型和神经网络可学习 TFBS-剪接关联 | 性能中等，不能替代剪接位点附近特征 | Results 节 Fig. 3A-B |
| CNN 整合位置信息 | TFBS 位置分布提升预测性能 | CNN vs. DNN（相同数据） | CNN AUROC 0.889 > DNN 0.853 | 位置信息对剪接调控预测有增量价值 | 未与基于序列的 splicing code 模型直接对比 | Results 节 Fig. 4B-C |
| 三种 CV 方案对比 | 模型具有跨组织/跨基因泛化能力 | event-wise vs. tissue-wise vs. gene-wise | gene-wise 性能接近随机（~0.5） | 模型学到的是基因特异的 TFBS-剪接关联，而非通用规则 | 模型不能泛化到未见基因 | Results 节 Fig. 1F-G |
| In silico zero-out 重要性分析 | 少数 TF 对剪接预测贡献突出 | 逐个 TF 置零，测量预测变化 | 19 个 TF 为离群值（Q3 + 1.5×IQR） | 存在关键剪接调控候选 TF | 重要性不等于生物学因果性 | Results 节 Fig. 5A |
| CTCFL 外部验证 | CTCFL 是真实剪接调控因子 | CTCFL shRNA 敲低 RNA-seq 数据 | CTCFL 靶基因 ΔZΨ 显著高于非靶基因（p < 0.0001, Wilcoxon） | CTCFL 确实影响剪接，支持模型预测 | 仅验证一个 TF，且为间接证据 | Results 节 Fig. 5B-C |

## 11 结论正确解读

- **任务范围**：本文任务是从启动子 TFBS 占用变化预测第一盒式外显子剪接效率变化，属于「启动子 → 剪接」的关联建模，不涉及剪接位点附近的顺式元件。
- **oracle/真值输入**：TFBS 占用由 DNase-seq 开放染色质 + JASPAR 基序扫描 + TF 表达过滤推断，是计算预测而非实验验证的结合事件；PSI 由 RNA-seq 经 MISO 计算，依赖转录本定量准确性。
- **端到端状态**：非端到端。中间依赖多个外部工具（FIMO、CATANA、MISO）和数据库（JASPAR、ENCODE），每个环节都有误差累积。
- **算力成本**：未提供具体训练时间或硬件信息。
- **历史数据依赖**：依赖 ENCODE 特定批次数据（GRCh37 参考基因组），换用新版本基因组或数据批次需重新处理。
- **模型依赖**：CNN 架构简单（单层卷积），未与更先进的架构（如 Transformer、图神经网络）对比。
- **最难情况**：gene-wise CV 性能接近随机，说明模型无法泛化到训练中未见的基因；跨组织泛化也仅适用于共享剪接模式的基因。
- **不确定性**：未提供置信区间或多次运行的标准差；预印本未经同行评审。
- **有边界的复述**：在 ENCODE 15 个人体组织中，以计算推断的启动子 TFBS 占用变化为特征，CNN 能以 AUROC 0.889 的精度区分第一盒式外显子剪接效率是否发生显著变化；但该性能主要来自基因特异模式，不能泛化到未见基因；in silico 扰动分析识别出的 CTCFL 在外部敲低数据中得到部分验证。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 组织数量有限 | 仅使用 15 个人体组织，可能不足以覆盖剪接调控的多样性 | 未明确提及 | Discussion 节（隐含） |
| 基因维度泛化失败 | gene-wise CV 性能接近随机，模型不能预测未见基因的剪接模式 | 未明确提及 | Results 节 Fig. 1F-G |
| 数据质量限制 | 为获得高质量数据，排除了不符合 ENCODE 质量标准的数据，导致组织数量减少 | 未明确提及 | Discussion 节："The main drawback of this study is the limited number of tissues because we aimed to use a high-quality dataset to avoid the noise and artifacts" |
| TFBS 推断的近似性 | 使用基序扫描和开放染色质推断 TF 结合，非实验验证的结合事件 | 未明确提及 | Methods 节（隐含） |
| 仅关注第一盒式外显子 | 未扩展到其他类型剪接事件（如内含子保留、互斥外显子） | 未明确提及 | 全文范围限定 |

**注：作者在 Discussion 中明确承认的主要局限是组织数量有限（上述第 3 条）。其他条目为从文中推断的隐含局限，非作者明确表述。**

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| gene-wise CV 性能接近随机 | 模型可能主要学习了基因身份（gene identity）而非 TFBS-剪接调控规则；同一基因在不同组织中的剪接模式可能高度相关，导致数据泄漏 | 如果模型不能泛化到新基因，其实用价值有限；需要明确区分「基因特异模式」与「通用调控规则」 | 在训练集中完全排除某些基因家族，测试集仅包含未见家族；或使用跨物种验证 | Results 节 Fig. 1F-G |
| TFBS 占用推断依赖 DNase-seq 和基序扫描 | DNase-seq 反映开放染色质而非实际 TF 结合；基序扫描存在大量假阳性；FDR < 10⁻³ 较宽松 | TFBS 特征噪声可能影响模型学习真实调控信号；可能高估或低估某些 TF 的重要性 | 使用 ChIP-seq 验证关键 TF 的实际结合；或使用更严格的基序匹配阈值 | Methods 节 |
| 未与剪接位点附近特征对比 | 未将启动子 TFBS 特征与经典剪接调控特征（外显子/内含子序列、剪接因子基序）联合或对比 | 无法判断启动子 TFBS 的增量预测价值；可能启动子特征只是剪接位点特征的弱代理 | 在相同数据上比较「仅剪接位点特征」「仅启动子 TFBS」「两者联合」的性能 | Results 节（未提供此类对比） |
| 二分类标签可能丢失信息 | 将 ΔZΨ 二值化（变化/不变）丢失了剪接变化的幅度信息；阈值选择可能影响结果 | 连续预测可能更精确地刻画 TFBS-剪接剂量关系 | 使用回归任务预测 ΔZΨ 连续值，比较与分类的性能差异 | Results 节 Fig. 2A |
| 组织对差异编码引入组合爆炸 | 15 个组织产生 105 个组织对，样本间非独立可能影响统计检验 | 交叉验证的独立性假设可能被违反，导致性能估计偏乐观 | 使用更严格的嵌套交叉验证，或在组织对级别进行分组 | Methods 节（未明确说明如何处理非独立性） |
| CTCFL 验证仅为一个 TF | 单一 TF 的外部验证不足以证明整体方法的可靠性；可能存在选择偏差 | 需要更多 TF 的独立验证才能建立方法可信度 | 对多个 top-ranked TF 进行敲低/过表达实验验证 | Results 节 Fig. 5B-C |

## 14 学到什么

**Agent 提炼的知识候选：**

1. **TFBS 位置编码优于频率编码**：本文将 TFBS 从「有无」变为「位置分布」表示后，CNN 性能显著提升。可迁移到 TF–DNA 互作建模：在预测 TF 结合位点或功能输出时，将结合位点的空间分布（如距离 TSS 的距离、相对方向、共定位模式）编码为输入特征，而非仅用二值化占用。

2. **跨条件差异编码策略**：本文通过组织对之间的差异（ΔTFBS、ΔZΨ）构建训练样本，将静态特征转化为动态变化。可迁移到课题：在研究 TF–DNA 结合动态时，可用「条件 A vs. 条件 B」的差异编码捕捉 TF 结合变化的调控效应，而非仅用单一条件的绝对结合强度。

3. **三种 CV 方案的系统比较**：event-wise、tissue-wise、gene-wise 三种划分方式揭示了不同层面的泛化能力。可迁移到课题：在构建 TF–DNA 互作预测模型时，应同时报告「随机划分」「按细胞类型/组织划分」「按基因/位点划分」三种性能，以识别模型是学到了通用规则还是记忆了特例。

4. **In silico zero-out 扰动分析**：通过将单个 TF 通道置零并测量预测变化来评估特征重要性。可迁移到课题：在 TF–DNA 结合模型中，可用类似方法识别关键 TF 或关键序列基序，无需额外的可解释性工具。

5. **启动子-剪接偶联的建模框架**：本文建立了「启动子 TFBS → 远端剪接事件」的预测框架，提示在蛋白质-DNA 互作研究中，TF 结合的功能输出可能超出局部转录调控，延伸至 RNA 加工层面。可迁移到课题：在预测 TF 结合功能后果时，不应局限于转录起始/增强子活性，还应考虑剪接、3' 端加工等共转录事件。

6. **数据质量过滤策略**：本文严格筛选 ENCODE 质量标准的数据，以牺牲数量换取质量。可迁移到课题：在整合公共 ChIP-seq/DNase-seq/RNA-seq 数据时，应建立明确的质量过滤标准，避免跨实验室批次效应。

7. **Z-score 标准化消除基因间差异**：对 PSI 按基因进行 Z-score 标准化，使不同基因的剪接效率可比。可迁移到课题：在比较不同基因座的 TF 结合强度或功能输出时，按基因座自身基线标准化可能比绝对数值更有生物学意义。

## 15 与已有知识连接

1. **Splicing code 系列工作**：Barash et al. (2010) "Deciphering the splicing code" 和后续深度学习方法（如 SpliceAI, Jaganathan et al. 2019）建立了从序列预测剪接的框架。本文与之不同在于输入特征从外显子/内含子序列扩展到启动子 TFBS，输出从剪接位点选择扩展到外显子包含水平。可对比：SpliceAI 使用序列上下文预测剪接位点，本文使用 TFBS 占用预测剪接模式变化。

2. **转录-剪接偶联机制研究**：Cramer et al. (1997) 证明启动子结构影响剪接；Kornblihtt (2007) 综述了 Pol II 延伸速率与剪接的偶联。本文为这一机制提供了全基因组尺度的计算证据，与单基因机制研究互补。

3. **TF–DNA 结合预测的深度学习方法**：DeepBind (Alipanahi et al. 2015)、DeepSEA (Zhou & Troyanskaya 2015) 等用 CNN 从序列预测 TF 结合。本文的 CNN 架构与之一脉相承，但输入从 DNA 序列变为 TFBS 占用矩阵，输出从结合强度变为剪接模式。

4. **ENCODE 数据资源**：本文使用的 DNase-seq 和 RNA-seq 数据来自 ENCODE 项目（ENCODE Project Consortium 2012），与课题中常用的 ChIP-seq、ATAC-seq 数据同源，可复用其质量标准和处理流程。

5. **剪接定量工具**：MISO (Katz et al. 2010) 用于计算 PSI 值，CATANA 用于注释剪接事件。这些工具在课题中分析 RNA-seq 数据时可直接复用。

6. **特征重要性分析方法**：zero-out 扰动分析与模型无关，类似于 permutation importance (Breiman 2001)，可迁移到其他深度学习模型的解释中。

## 16 研究想法

**Agent 生成的研究候选：**

**候选 1：基于 TF–DNA 结合动力学的剪接调控预测模型**
- **名称**：TF-binding dynamics to splicing (TFDS) predictor
- **来源局限/观察**：本文使用静态 TFBS 占用（有无）作为特征，未考虑 TF 结合强度、结合动力学（ residence time）或协同结合效应；且仅覆盖 15 个组织，未纳入时间序列或扰动数据
- **核心假设**：TF 结合强度的连续变化（而非二元占用）携带更多剪接调控信息；TF 间的协同/拮抗结合模式可提高剪接预测精度
- **初步方法**：将 ChIP-seq 信号强度（而非仅 peak 有无）编码为连续特征，结合 TF 表达协变网络，用图神经网络建模 TF-TF 协同效应，预测下游剪接变化
- **验证方式**：使用 ENCODE 更多细胞系/组织数据，比较连续 vs. 二元特征的预测性能；用 CRISPR 干扰（CRISPRi）靶向候选 TF 结合位点验证因果性
- **创新状态**：unverified

**候选 2：跨物种的启动子-TFBS-剪接调控保守性分析**
- **名称**：Cross-species conservation of promoter-splicing coupling
- **来源局限/观察**：本文仅使用人类数据，未检验启动子-TFBS-剪接关联是否在物种间保守；基因维度泛化失败可能部分源于训练数据中基因数量有限
- **核心假设**：如果启动子-TFBS-剪接调控是进化保守的机制，跨物种训练可提高泛化能力，并帮助区分「基因特异」与「通用」调控规则
- **初步方法**：整合小鼠、斑马鱼等模式生物的 DNase-seq/ATAC-seq 和 RNA-seq 数据，用迁移学习在人类数据上预训练、跨物种微调
- **验证方式**：比较同源基因在不同物种中的 TFBS-剪接关联一致性；评估跨物种训练的模型在人类未见基因上的预测性能
- **创新状态**：unverified

**候选 3：物理模拟与深度学习的混合框架：TF 结合位点空间构象对剪接的影响**
- **名称**：Conformation-aware promoter-splicing model (CAPSM)
- **来源局限/观察**：本文的 CNN 输入是线性启动子序列上的 TFBS 分布，未考虑 3D 基因组结构（染色质环化）如何将启动子 TF 复合物与剪接位点空间邻近
- **核心假设**：启动子 TF 复合物通过染色质环化与剪接位点空间接触，TFBS 的 3D 空间排列（而非线性距离）对剪接调控更关键
- **初步方法**：整合 Hi-C/3C 数据构建启动子-剪接位点空间接触图谱，用图神经网络编码 3D 接触信息，结合 TFBS 占用特征预测剪接；对关键 TF-染色质接触对进行分子动力学（MD）模拟验证空间互作稳定性
- **验证方式**：比较加入 3D 接触信息前后模型性能；用 Hi-C 数据预测的接触频率与 TF 敲低后剪接变化的相关性验证
- **创新状态**：unverified

**候选 4：基于 TF 结合 motif 突变扰动的剪接异常预测**
- **名称**：Motif perturbation to splicing aberration (MPSA)
- **来源局限/观察**：本文的 in silico 扰动仅针对 TF 通道（zero-out），未模拟启动子序列变异（SNV/indel）对 TFBS 结合和下游剪接的影响；而疾病相关剪接异常常由非编码区变异引起
- **核心假设**：启动子区域的非编码变异通过改变 TFBS 结合亲和力来影响下游剪接，且这种效应可通过深度学习模型预测
- **初步方法**：在训练好的 CNN 模型上执行 in silico 饱和突变（对启动子每个碱基做 A/C/G/T 替换），计算剪接预测变化分数；与 ClinVar/gnomAD 中疾病相关非编码变异对照验证
- **验证方式**：用 minigene 剪接报告实验验证 top-ranked 变异位点；比较预测分数与实验测定的 PSI 变化相关性
- **创新状态**：unverified

**候选 5：整合 TF–DNA 结合亲和力（物理化学特征）的剪接预测**
- **名称**：Physicochemical TF-binding features for splicing prediction (PTSP)
- **来源局限/观察**：本文的 TFBS 特征来自 PWM 基序扫描，未考虑 TF-DNA 结合的物理化学特性（如结合自由能、氢键模式、构象变化），这些特性可能影响 TF 结合强度和功能输出
- **核心假设**：将 TF-DNA 结合的物理化学特征（如结合自由能 ΔG、静电势、形状匹配）纳入模型，可捕捉 PWM 无法编码的结合特异性信息，提高剪接预测精度
- **初步方法**：用 MD 模拟或机器学习势函数（如 AlphaFold3、RoseTTAFoldNA）计算 TF-motif 复合物的结合自由能，作为额外特征输入 CNN/图神经网络；与纯 PWM 特征对比
- **验证方式**：在独立测试集上比较加入物理化学特征前后的 AUROC/AUPRC；用表面等离子体共振（SPR）或电泳迁移率变动分析（EMSA）验证 top-ranked TF-motif 对的结合亲和力预测
- **创新状态**：unverified