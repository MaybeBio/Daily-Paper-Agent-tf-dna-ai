## 01 基本信息
- **标题**：A transcription factor regulatory atlas for activity inference and perturbation prediction
- **作者与单位**：Sugimoto, Hikaru; Tsuyuzaki, Koki; Zou, Zhaonan; Oki, Shinya; Ohta, Tazro; Kawakami, Eiryo（单位未在摘要中提供）
- **期刊/预印本平台**：Nucleic Acids Research
- **年份**：2026（在线日期 2026-09-15）
- **论文类型**：方法学/资源型研究（Resource & Method）
- **领域**：转录因子（TF）调控网络、TF 活性推断、扰动预测、计算生物学
- **关键词**：TF activity inference, TF–mRNA regulatory network, perturbation prediction, transcriptomics, regulatory atlas
- **DOI/arXiv 号**：10.1093/nar/gkag897
- **代码**：https://github.com/HikaruSugimoto/tfactprofiler
- **数据**：Zenodo (https://zenodo.org/records/20779282)；多个公开数据集（详见 Data availability 节）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI/深度学习/物理模拟」方向中的**转录组学推断与调控网络建模**分支。它不直接建模 TF 与 DNA 的物理结合（如 ChIP-seq 峰、结构域、结合 motif 的物理化学性质），而是从转录组共变模式中学习 TF–mRNA 的**符号化、定量调控系数**，用于 TF 活性推断和扰动响应预测。其核心创新在于：将 ChIP-based、motif-based 和 curated 三类先验知识整合，通过大规模 RNA-seq 数据学习 signed regulatory coefficients，并引入**不确定性度量**（reliability score）。对本课题的可迁移价值在于：提供了一种将「结合先验（ChIP/motif）」转化为「功能调控系数」的框架，可作为连接 TF–DNA 结合事件与下游转录组功能的桥梁。

## 02 一句话总结
本文构建了 TFActProfiler——一个包含 2,606,176 条 signed TF–mRNA 调控关系的资源库，通过整合 ChIP-based、motif-based 和 curated 先验知识并在大规模 bulk/single-cell RNA-seq 上做 cluster-wise 岭回归，实现了无需任务匹配训练数据的 TF 活性推断与扰动响应预测，并在 1,423 个 TF 敲低实验中优于现有资源（如 CollecTRI）。

## 03 研究问题
- **具体问题**：如何从转录组数据中准确推断 TF 活性，并在无任务匹配训练数据的情况下预测 TF 扰动（如敲低）后的全转录组响应？
- **为什么重要**：TF 是基因调控的核心，异常 TF 活性与多种疾病相关。大规模扰动实验（如 Perturb-seq）成本高、覆盖有限，亟需计算方法从常规转录组数据中推断 TF 活性并预测扰动效应，以支持疾病机制解析和治疗靶点发现。
- **现有方法不足**：
  1. 现有 TF–mRNA 资源在**精度与覆盖度之间存在权衡**——要么覆盖广但含大量间接/非功能关联（如 ChIP-Atlas），要么精度高但覆盖有限（如 curated 资源）。
  2. 大多数资源**缺乏符号化（signed）调控信息**，无法区分激活与抑制。
  3. 现有扰动预测模型（如 foundation models）**需要大量任务匹配的训练数据**，在小样本 bulk RNA-seq 场景下不适用。
- **精确研究问题**：Can a signed, quantitative TF–mRNA regulatory resource, learned by integrating heterogeneous prior evidence with large-scale transcriptomic atlases, improve TF activity inference accuracy and enable zero-shot perturbation response prediction without task-matched training data?

## 04 背景与发展脉络
*注：以下脉络基于本文框架整理，标注「仅本文框架」或「经外部核验」。*

1. **早期 TF 活性推断方法（基于 curated regulon）**：如 DoRothEA、CollecTRI，依赖文献手工 curated 的 TF–target 关系，精度高但覆盖有限。代表方法：VIPER、decoupleR 中的 ulm/zscore 等。局限：覆盖度不足，且 curated 资源更新慢。（经外部核验：CollecTRI 为领域内广泛使用的 signed resource）
2. **基于 ChIP-seq/motif 的宽覆盖资源**：如 ChIP-Atlas、ENCODE ChIP-seq 数据，覆盖大量 TF–target 候选关系，但缺乏符号化调控信息，且包含大量非功能性结合事件。（经外部核验：ChIP-Atlas 为公开 ChIP-seq 数据库）
3. **基于共表达的调控网络推断**：如 WGCNA、GENIE3 等，从转录组共变模式推断调控关系，但无法区分直接/间接调控，且缺乏方向性。（经外部核验：这些为经典共表达网络方法）
4. **基于深度学习的扰动预测模型**：如 scFoundation、scGPT、Geneformer、scBERT 等 foundation models，以及 CPA、GEARS 等专用扰动预测模型。优势：可学习复杂非线性关系；局限：需要大量训练数据，在小样本场景下表现不佳。（经外部核验：这些模型在领域内已有广泛评测）
5. **本文主张的位置**：TFActProfiler 位于上述脉络的交叉点——**用大规模转录组数据为宽覆盖先验知识赋予符号化和定量权重**，从而同时获得覆盖度和精度，并支持零样本扰动预测。其方法学核心是 cluster-wise 岭回归 + 跨数据集归一化聚合，而非深度学习。（仅本文框架）

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 覆盖度与精度权衡 | 宽覆盖资源（ChIP-Atlas）精度低，高精度资源（CollecTRI）覆盖有限 | ChIP-seq 结合事件不必然代表功能调控；curated 资源依赖人工整理，更新慢 | Results 节：TFActProfiler 在保持宽覆盖的同时达到更高精度（图 2B） |
| 缺乏符号化调控信息 | 多数资源无法区分激活/抑制 | ChIP-seq 和 motif 数据本身不含调控方向信息 | Methods 节：需通过转录组数据学习 signed coefficients |
| 扰动预测依赖任务匹配训练数据 | Foundation models 在小样本 bulk RNA-seq 场景下表现不佳 | 这些模型需要大规模配对扰动数据训练 | Results 节：零样本预测框架无需训练数据即可工作（图 4B） |
| 缺乏不确定性度量 | 用户无法判断 TF 活性推断的可靠性 | 先验知识质量参差不齐，模型假设可能被违反 | Results 节：提出 MSE-based reliability score（图 3） |
| 跨数据集异质性 | 不同 RNA-seq 数据集的预处理和归一化方式不同 | 各数据库采用不同 pipeline，直接合并会产生批次效应 | Methods 节：cluster-wise 回归 + 数据集内归一化后再聚合 |

## 06 核心思想
1. **表面方法**：构建 TFActProfiler 资源库——整合 ChIP-Atlas、motif-based 预测和 curated 数据库作为候选 TF–mRNA 关系，然后在大型 bulk 和 single-cell RNA-seq 数据集上，对每个 cluster 做岭回归，估计每个 TF 对其 target mRNA 的 signed 定量调控系数。基于该资源，用 ulm 方法推断 TF 活性，并用线性映射预测扰动响应。

2. **核心洞察**：**先验知识提供「哪些 TF 可能调控哪些基因」的候选结构，而大规模转录组数据提供「调控方向和强度」的功能证据**。通过将两者结合，可以在不牺牲覆盖度的前提下获得符号化、定量的调控信息。关键在于：(a) 保留各数据集的 native preprocessing，不做跨数据集 harmonization，而是数据集内归一化后聚合系数；(b) 用 cluster-wise 回归处理不同细胞类型/组织背景下的调控异质性；(c) 通过「先验结构 + 数据估计」的两步法，将 ChIP-seq 的结合事件转化为功能调控关系。

3. **可能的普适教训** [Analysis]：在生物信息学中，**「宽覆盖但嘈杂的先验」+「数据驱动的符号/权重学习」** 是一种可推广的范式——先验提供结构约束（哪些边可能存在），数据提供功能证据（边的方向和强度）。这种「结构-功能分离」的策略比单纯依赖先验或纯数据驱动都更稳健，尤其适用于先验知识不完整但数据量充足的场景。

## 07 方法总览
- **输入**：
  - 先验 TF–mRNA 候选关系：ChIP-Atlas、motif-based predictions、curated 数据库（如 CollecTRI）
  - 大规模 bulk 和 single-cell RNA-seq 数据集（多个公开资源）
- **输出**：
  - TFActProfiler 资源：2,606,176 条 signed TF–mRNA 调控系数（2017 TFs, 18,163 target mRNAs）
  - TF 活性推断结果（per-sample TF activity scores）
  - 扰动响应预测结果（per-TF perturbation 的全转录组响应）
- **核心模块**：
  1. **先验整合模块**：从 ChIP-Atlas、motif 预测和 curated 数据库收集候选 TF–mRNA 关系，构建候选边集
  2. **系数估计模块**：对每个 cluster（细胞类型/组织），用岭回归估计 TF→mRNA 的 signed 系数；数据集内归一化后跨数据集聚合
  3. **TF 活性推断模块**：基于 signed weighted network，用 ulm（univariate linear model）计算 per-sample TF activity
  4. **扰动预测模块**：用学习到的系数矩阵 W，通过线性映射 Δy = W·Δx 预测 TF 敲低后的转录组响应
  5. **可靠性评估模块**：MSE-based reliability score，衡量先验与数据的一致性
- **训练**：岭回归（ridge regression），λ=0.01（零样本预测）或 λ=0.1（有训练数据时）
- **工具**：Python；scikit-learn, NumPy, Pandas, Statsmodels, SciPy；decoupleR (v2.1.1) 用于 TF 活性推断基准
- **文字流程**：收集先验候选边 → 对每个 RNA-seq 数据集做 cluster-wise 岭回归估计 signed 系数 → 数据集内归一化 → 跨数据集聚合得到 consensus coefficients → 用 consensus network 进行 TF 活性推断（ulm）和扰动预测（线性映射）→ 用 MSE-based score 评估可靠性

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 先验整合 | 从 ChIP-Atlas、motif 预测、curated 数据库收集候选 TF–mRNA 边 | 提供候选结构，约束回归的稀疏模式，避免在全基因网络上做无约束回归 | 输入：三类先验资源；输出：候选 TF–mRNA 边集 | Methods 节：三类先验整合策略 | 预期影响 [Analysis]：移除后回归将面临超高维问题，且无法区分功能与非功能关系，精度会显著下降 |
| Cluster-wise 岭回归 | 在每个 cluster 内估计 TF→mRNA 的 signed 系数 | 不同细胞类型/组织的调控关系可能不同，cluster-wise 可捕捉背景特异性 | 输入：cluster 内 RNA-seq 表达矩阵 + 候选边集；输出：signed coefficient matrix K | Methods 节：cluster-wise 回归设计 | 实测影响：作者未提供 ablation；预期影响 [Analysis]：全局回归会模糊背景特异性调控，降低跨组织泛化能力 |
| 跨数据集聚合 | 数据集内归一化后平均系数 | 各数据集 preprocessing 不同，直接合并会产生批次效应 | 输入：各数据集的系数矩阵；输出：consensus coefficient matrix | Methods 节：数据集内归一化策略 | 预期影响 [Analysis]：移除后系数会被高方差数据集主导，降低鲁棒性 |
| TF 活性推断（ulm） | 从表达数据 + signed network 计算 per-sample TF activity | 将转录组数据转化为可解释的调控活性信号 | 输入：表达矩阵 + consensus network；输出：TF activity scores | Results 图 2B：优于 CollecTRI | 实测影响：作者未提供单独 ablation；预期影响 [Analysis]：替换为 zscore 等方法可能降低精度（ulm 为 decoupleR 中表现最佳方法之一） |
| 扰动预测（线性映射） | 用 W·Δx 预测 TF 敲低后的转录组响应 | 无需训练数据即可预测扰动效应 | 输入：TF 敲低幅度 Δx + coefficient matrix W；输出：预测的 Δy | Results 图 4B：与实验显著相关 | 实测影响：作者未提供 ablation；预期影响 [Analysis]：移除符号信息后预测方向会随机，性能大幅下降 |
| 可靠性评估（MSE score） | 衡量先验与数据的一致性 | 用户需要判断推断结果的可靠性 | 输入：先验 W 与数据估计 K；输出：per-sample MSE | Results 图 3：区分高低可靠性场景 | 预期影响 [Analysis]：移除后用户无法判断推断质量，在低质量先验场景下可能误用结果 |

## 09 关键公式符号
1. **岭回归估计 TF–mRNA 系数**（Methods 节）：
   - 模型：Y ≈ K·X，其中 Y ∈ R^(n×c) 为 mRNA 表达矩阵（n 个 mRNA，c 个样本），X ∈ R^(m×c) 为 TF 表达矩阵（m 个 TF），K ∈ R^(n×m) 为 signed coefficient matrix
   - 估计：对每个 mRNA i，在候选 TF 集合上做岭回归，目标函数为 ||y_i - K_i·X||² + λ||K_i||²
   - 符号含义：K 中正系数表示激活，负系数表示抑制；零表示无调控关系（由先验约束）
   - 用途：从转录组共变模式中学习 TF 对 target 的调控方向和强度
   - 直觉：在给定先验候选边的前提下，用表达数据的共变模式估计调控的符号和幅度

2. **TF 活性推断（ulm）**（Methods 节）：
   - 模型：x_j ≈ W·y_j，其中 W ∈ R^(m×n) 为 signed TF–mRNA 系数矩阵（行 = TF，列 = mRNA），x_j 为样本 j 的 TF 活性向量，y_j 为样本 j 的 mRNA 表达向量
   - 符号含义：W 中正条目表示 TF 激活该 mRNA，负条目表示抑制
   - 用途：从 mRNA 表达反推 TF 活性
   - 直觉：TF 活性是其所有 target 表达变化的加权综合，权重由 signed coefficients 决定

3. **扰动预测**（Methods 节）：
   - 模型：Δy = W·Δx，其中 Δx = −γ·x_k·e_k（TF k 敲低），γ 控制扰动强度
   - 符号含义：Δy 为预测的 mRNA 表达变化，e_k 为第 k 个标准基向量
   - 用途：预测单个 TF 敲低后的全转录组响应
   - 直觉：TF 敲低的效果通过其调控的 target 网络线性传播

4. **可靠性评估**（Methods 节）：
   - 公式：MSE_j = (1/m)·||x_j − W·K·x_j||²
   - 符号含义：x_j 为样本 j 的 TF 表达，W·K 为先验与数据估计的复合映射
   - 用途：衡量先验 W 与数据估计 K 的自洽性
   - 直觉：如果先验与数据高度一致，则 W·K 应接近恒等映射，MSE 低

## 10 实验设计与证据链
- **数据集**：
  - 训练/构建资源：大规模 bulk 和 single-cell RNA-seq 数据集（具体来源未在摘要中详列，见 Data availability 节）
  - TF 活性推断基准：1,423 个 TF 敲低（KD）实验，来自 4 个人类细胞系（RPE1, K562, HepG2, Jurkat）[6, 45]
  - 独立基准：KnockTF 2.0 小鼠资源 [47]（跨物种验证）
  - 单细胞验证：scTF-seq 数据 [59]（177 个扰动条件）
  - 磷酸化验证：MPXV 感染 HFF 时间序列数据 [60]
  - 下游应用：ccRCC bulk RNA-seq（157 例）[4]、PBMC scRNA-seq [34, 80]、MS 病变空间转录组 [81]、DepMap 细胞系表达数据 [82]、IPF bulk RNA-seq [84]、人类睾丸 scRNA-seq [63]
- **指标**：TF 活性推断的排序精度（识别真正被扰动 TF 的能力）、预测与实验表达变化的 Pearson 相关和 MSE、AUC（配体-受体推断）
- **基线**：CollecTRI（curated signed resource）、ChIP-Atlas（宽覆盖无符号）、随机化对照
- **评测协议**：对每个 KD 实验，用 TF 活性推断方法计算所有 TF 的活性分数，检查真正被扰动的 TF 是否排名靠前；扰动预测则比较预测的 Δy 与实验观察的 Δy

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|-------------|-------------------|------|
| TF 活性推断基准（人类 4 细胞系） | TFActProfiler 能更准确定位被扰动 TF | 与 CollecTRI、ChIP-Atlas 等对比，1,423 个 KD 实验 | TFActProfiler + ulm 达到最佳整体性能 | TFActProfiler 的 signed quantitative 信息提升了活性推断精度 | 未证明在所有细胞类型/条件下均最优 | Results 图 2B |
| 小鼠跨物种验证 | 人类训练的 TF–mRNA 系数可迁移到小鼠 | KnockTF 2.0 小鼠 KD 数据，orthology mapping | TFActProfiler 优于 CollecTRI 小鼠版本 | 调控关系在物种间部分保守 | 未证明全基因组范围内均保守 | Results 节（Supplementary 图 S1D） |
| 磷酸化验证 | TF 活性推断能反映蛋白水平调控 | MPXV 感染 HFF，mRNA 推断 vs 磷酸化数据 | TFActProfiler 与磷酸化轨迹相关性高于 CollecTRI | TF 活性推断可捕捉翻译后修饰层面的调控变化 | 相关性仍有限，不能替代磷酸化测量 | Results 图 2D-E |
| 配体-受体推断增强 | 下游 TF 活性提升细胞互作推断 | ST→SSC 互作，有/无 TF 活性增强 | TFActProfiler 增强后 AUC 提升 | TF 活性信息可改善细胞间通讯推断 | 仅在单一组织类型验证 | Results 图 2H |
| 零样本扰动预测 | 无需训练数据即可预测 KD 效应 | 4 细胞系 KD 数据，预测 vs 实验 Δy | 预测与实验显著相关，优于 CollecTRI | 线性 signed network 可捕捉扰动的主要方向 | 预测精度有限，不能替代实验 | Results 图 4B |
| 有训练数据时的扰动预测 | 加入训练数据可进一步提升性能 | 与 scFoundation、scGPT 嵌入对比 | TFActProfiler 达到与 scFoundation 相当或更好的性能 | 先验知识可替代部分训练数据需求 | 未证明在更大规模数据上优于 foundation models | Results 图 4D |
| 可靠性 score 验证 | MSE score 能反映推断质量 | 不同细胞类型/组织，比较 score 与推断精度 | 低 MSE 场景推断精度更高 | 可靠性 score 可作为实用指导 | score 为启发式，非严格置信区间 | Results 图 3 |
| 案例研究（ccRCC、PBMC、脂肪生成、IPF、torpor） | TFActProfiler 能恢复已知调控因子 | 各数据集的已知生物学结论 | 成功恢复 E2F7（ccRCC）、PAX5/EOMES（PBMC）、TRPS1（脂肪生成）、Atf3（torpor）等 | TFActProfiler 具有广泛适用性 | 案例研究为探索性，非系统性验证 | Results 节案例 1-4 |

## 11 结论正确解读
- **任务范围**：本文的 TF 活性推断和扰动预测均基于**转录组数据**，不涉及 TF 的 DNA 结合位点、染色质状态或蛋白构象。结论限于「从 mRNA 表达推断 TF 功能活性」这一层面。
- **oracle/真值输入**：基准测试使用实验 KD 数据作为真值，但 KD 的效应可能受补偿机制、脱靶效应等影响，并非完美的 ground truth。
- **端到端状态**：TFActProfiler 是**预训练资源**，用户可直接用于新数据集的 TF 活性推断，无需重新训练。扰动预测为**零样本**（无需任务匹配训练数据），但加入训练数据可提升性能。
- **算力成本**：资源构建阶段需要大规模 RNA-seq 数据上的回归计算，但使用阶段（推断/预测）计算成本低。
- **历史数据依赖**：TF–mRNA 系数从历史 RNA-seq 数据中学习，可能受数据覆盖的细胞类型/组织范围限制。
- **模型依赖**：线性模型假设 TF 对 target 的调控是加性、线性的，忽略了非线性交互、剂量效应和时间延迟。
- **最难情形**：低表达 TF、组织特异性调控、翻译后修饰主导的调控、以及 TF 表达与活性解耦的场景。
- **群体/领域边界**：主要基于人类数据训练，跨物种需 orthology mapping；在非模式生物中的适用性未验证。
- **不确定性**：reliability score 为启发式度量，不提供统计置信区间；系数本身受共线性、混杂因素影响。
- **有边界的复述**：TFActProfiler 是一个从大规模转录组数据中学习的 signed TF–mRNA 调控资源，在人类细胞系的 TF KD 基准中，其活性推断精度优于现有资源，并能零样本预测 TF 敲低后的转录组响应方向；但其线性假设和转录组推断的局限性意味着它应作为假设生成工具，而非精确的调控机制模型。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 线性近似 | 扰动预测是线性模型，只能捕捉局部、一阶效应 | 整合非线性或动态模型 | Discussion 节 |
| 上下文依赖性 | TF–mRNA 调控关系随细胞类型/组织变化，cluster-wise 回归只能部分解决 | 需要更多上下文特异性数据 | Discussion 节 |
| 非因果推断 | 系数从共表达回归中学习，不保证因果关系 | 整合 CRISPR 筛选等因果数据 | Discussion 节 |
| 覆盖度限制 | 稀有细胞类型和特定生理条件的数据不足 | 扩展训练数据覆盖范围 | Discussion 节 |
| 与 CollecTRI 的关系 | TFActProfiler 不替代 CollecTRI，后者在追溯文献证据方面有独特价值 | 用户应根据目标选择资源 | Discussion 节 |
| 未进行严格跨方法比较 | 作者明确表示未与所有现有扰动预测方法进行严格对比 | 未来需要更全面的基准测试 | Discussion 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| 线性回归估计 TF–mRNA 系数 | 共线性问题：TF 之间高度相关，回归系数可能不稳定或反映的是联合效应而非独立效应 | 影响系数的可解释性和扰动预测的准确性 | 检查系数对输入数据扰动的稳定性（bootstrap）；与独立 ChIP-seq 验证集对比 | Methods 节：岭回归设计 |
| 先验整合的偏差 | ChIP-Atlas 和 motif 数据本身有偏差（如偏好高表达/研究充分的 TF），可能传导到最终资源 | 影响资源的覆盖均匀性和下游推断的公平性 | 分析资源中 TF 的分布是否与基因功能重要性相关；在低研究充分度 TF 上单独评估 | Results 节：资源构成 |
| 基准测试的局限性 | KD 实验本身有脱靶和补偿效应；且基准覆盖的 TF 可能偏向于有强表型效应的 TF | 可能高估方法在弱效应 TF 上的表现 | 在包含弱效应 TF 的独立数据集上验证；使用多种 KD 技术（RNAi vs CRISPRi）交叉验证 | Results 节：基准设计 |
| 零样本预测的评估方式 | 预测与实验 Δy 的相关性可能受基因表达动态范围影响，高表达基因主导相关性 | 可能掩盖低表达但重要靶基因的预测失败 | 分层分析（按表达水平、按调控强度）；使用 rank-based 指标 | Results 图 4B |
| 可靠性 score 的实用性 | MSE-based score 需要先验与数据的一致性，但用户可能无法判断何时该信任该 score | 如果 score 本身不可靠，用户可能误判推断质量 | 在不同数据质量条件下系统评估 score 的预测能力；与交叉验证方法对比 | Results 图 3 |
| 与 foundation models 的比较 | 作者仅与线性模型对比，未与更复杂的深度学习方法进行系统比较 | 无法判断 TFActProfiler 的相对优势是否随数据规模变化 | 在更大规模、更多样化的基准上对比 | Discussion 节：作者承认未进行严格比较 |
| 跨物种迁移的验证深度 | 仅用小鼠数据验证，未测试更远物种 | 进化距离较远的物种中调控网络可能差异更大 | 在更多物种（如斑马鱼、果蝇）的 KD 数据上验证 | Results 节：小鼠验证 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **「结构先验 + 数据加权」的两步法**：先验知识（ChIP/motif/curated）提供候选边的结构约束，大规模转录组数据提供边的符号和权重。这种「结构-功能分离」策略可迁移到 TF–DNA 结合机制研究中——例如，将 ChIP-seq 峰或 motif 预测作为「候选结合事件」，用表达数据或功能数据（如 CRISPR 筛选）为每个结合事件赋予功能权重，从而区分功能性结合与非功能性结合。

2. **Cluster-wise 回归处理上下文特异性**：不在所有数据上拟合单一模型，而是按细胞类型/组织分 cluster 回归，再跨 cluster 聚合。这提示在 TF–DNA 结合研究中，结合事件的功能后果可能高度依赖细胞背景，分 cluster 建模比全局建模更合理。

3. **符号化（signed）信息的重要性**：作者强调「signed regulatory information」是提升活性推断精度的关键。在 TF–DNA 结合研究中，仅知道「TF 是否结合」不够，还需要知道「结合后是激活还是抑制」——这可以通过整合表达数据或表观遗传标记（如 H3K27ac vs H3K27me3）来实现。

4. **不确定性/可靠性度量**：作者提出 MSE-based reliability score 来量化推断的置信度。在 TF–DNA 结合预测中，类似的思路可应用于：对每个 TF–靶基因预测给出置信度分数，帮助用户判断哪些预测值得实验验证。

5. **零样本扰动预测的线性基线**：作者证明简单的线性映射（Δy = W·Δx）在零样本设置下即可达到有意义的预测精度。这提示在缺乏大规模训练数据时，线性模型作为基线的重要性——不应一味追求复杂模型。

6. **跨物种迁移的 orthology mapping**：作者通过 orthology mapping 将人类 TF–mRNA 资源迁移到小鼠。在 TF–DNA 结合研究中，类似的策略可用于将结合位点注释从模式生物迁移到非模式生物。

7. **多资源整合的偏差控制**：作者整合了 ChIP-based、motif-based 和 curated 三类资源，但未详细讨论各资源的偏差如何影响最终结果。在整合多源数据时，应明确各数据源的偏差特征，并考虑加权策略。

## 15 与已有知识连接
- **CollecTRI / DoRothEA**：本文的直接基线资源。CollecTRI 提供 curated signed TF–target 关系，DoRothEA 提供 TF 活性推断的 regulon 资源。TFActProfiler 在覆盖度和精度上均优于 CollecTRI（Results 图 2B）。可连接：CollecTRI 论文（Müller-Dott et al.）和 DoRothEA 论文（Garcia-Alonso et al.）。
- **decoupleR**：本文使用的 TF 活性推断框架。decoupleR 提供多种活性推断方法（ulm、zscore、wmean 等），本文系统比较了不同方法组合。可连接：decoupleR 论文（Badia-i-Mompel et al.）。
- **CellOracle**：本文对比的另一种网络建模方法。CellOracle 从 scRNA-seq 中学习 TF–target 关系并模拟扰动。与 TFActProfiler 的区别在于：CellOracle 需要用户提供训练数据，而 TFActProfiler 是预训练资源。可连接：CellOracle 论文（Kamimoto et al.）。
- **VIPER / ARACNe**：经典的 TF 活性推断方法，基于互信息网络。本文的方法在概念上类似（从表达数据推断调控活性），但使用先验结构约束 + 回归而非纯数据驱动网络推断。可连接：VIPER 论文（Alvarez et al.）。
- **Foundation models（scGPT, scFoundation）**：本文在扰动预测任务中对比了这些模型。这些模型需要大规模训练数据，而 TFActProfiler 的线性方法在零样本设置下即可工作。可连接：scGPT 论文（Cui et al.）、scFoundation 论文（Hao et al.）。
- **Perturb-seq / CRISPR 筛选**：本文的基准数据来源。Perturb-seq 提供大规模 TF 扰动数据，是验证 TF 活性推断和扰动预测的金标准。可连接：Perturb-seq 论文（Dixit et al.、Adamson et al.）。
- **TF–DNA 结合机制**：本文不直接建模 TF–DNA 结合，但其「先验结构 + 数据加权」框架可迁移到结合机制研究中。例如，可将 ChIP-seq 峰作为先验结构，用 MPRA（massively parallel reporter assay）或 CRISPR 干扰数据为每个结合事件赋予功能权重。可连接：MPRA 方法论文（Patwardhan et al.）、CRISPRi 筛选论文（Fulco et al.）。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合事件的功能加权框架（Functional Weighting of TF–DNA Binding Events）
   - **来源局限/观察**：TFActProfiler 从转录组共变中学习 TF–mRNA 调控系数，但未利用 TF 的 DNA 结合信息（如 ChIP-seq 峰、motif 位置）。反过来，ChIP-seq 数据本身缺乏功能信息——结合 ≠ 调控。
   - **核心假设**：将 ChIP-seq/motif 结合事件作为先验结构，用大规模转录组或 CRISPR 筛选数据为每个结合事件赋予功能权重（激活/抑制/无功能），可以构建「结合-功能」映射，优于单独使用任一类数据。
   - **初步方法**：对每个 TF，收集其 ChIP-seq 峰和 motif 预测位点；对每个结合事件，用靶基因的表达变化（来自 KD/过表达数据）或染色质状态（H3K27ac/H3K27me3）标注功能方向；用类似 TFActProfiler 的 cluster-wise 回归框架学习结合事件的权重。
   - **验证方式**：在独立 KD 数据上比较「结合-功能」加权网络与纯 ChIP-seq 网络、纯共表达网络的活性推断精度。
   - **创新状态**：unverified

2. **候选名称**：上下文感知的 TF 结合功能预测（Context-Aware Prediction of TF Binding Functionality）
   - **来源局限/观察**：TFActProfiler 的 cluster-wise 回归表明 TF–mRNA 调控关系具有上下文特异性，但该框架未显式建模「上下文」的分子特征（如染色质状态、共因子表达）。
   - **核心假设**：TF 结合事件的功能后果（激活/抑制/无功能）由局部染色质环境和共因子表达决定，可以通过多模态数据（ATAC-seq、ChIP-seq、共因子表达）预测。
   - **初步方法**：对每个 TF–靶基因对，提取结合位点的染色质特征（开放性、组蛋白修饰）、共因子表达、序列特征（motif 强度、位置）；训练分类器预测结合事件的功能方向；与 TFActProfiler 的系数整合。
   - **验证方式**：在独立细胞类型中验证预测的上下文特异性调控关系，与实验 KD 数据对比。
   - **创新状态**：unverified

3. **候选名称**：零样本扰动预测的物理约束增强（Physics-Informed Zero-Shot Perturbation Prediction）
   - **来源局限/观察**：TFActProfiler 的扰动预测是纯线性映射，未利用 TF–DNA 结合的物理化学约束（如结合亲和力、结合位点位置、TF 浓度）。
   - **核心假设**：将 TF–DNA 结合的物理约束（如结合自由能、位点亲和力）作为正则化项加入扰动预测模型，可以提高预测精度，尤其在训练数据稀缺时。
   - **初步方法**：从 PDB 或 AlphaFold 结构获得 TF–DNA 结合界面信息，用分子力学或统计势能计算结合亲和力；将亲和力作为先验权重加入 TFActProfiler 的线性映射；在 KD 数据上比较有无物理约束的预测精度。
   - **验证方式**：在多个细胞系的 KD 数据上评估，重点关注物理约束是否改善低亲和力但功能重要的结合事件。
   - **创新状态**：unverified

4. **候选名称**：TF 活性推断的不确定性量化与主动学习（Uncertainty-Aware TF Activity Inference with Active Learning）
   - **来源局限/观察**：TFActProfiler 的 reliability score 是启发式度量，未提供统计置信区间，且未指导实验设计。
   - **核心假设**：将 reliability score 形式化为贝叶斯框架中的后验不确定性，并利用不确定性指导主动学习——优先实验验证不确定性最高的 TF–靶基因关系，可以高效改进资源质量。
   - **初步方法**：将 TFActProfiler 的岭回归替换为贝叶斯线性回归或高斯过程，获得系数的不确定性分布；设计主动学习策略，选择不确定性最高的 TF–靶基因对进行实验验证；迭代更新资源。
   - **验证方式**：模拟主动学习过程，比较不同选择策略下资源质量的提升速度。
   - **创新状态**：unverified

5. **候选名称**：跨物种 TF 调控网络的进化守恒分析（Evolutionary Conservation Analysis of TF Regulatory Networks）
   - **来源局限/观察**：TFActProfiler 通过 orthology mapping 迁移到小鼠，但未系统分析哪些调控关系在进化中保守、哪些是物种特异的。
   - **核心假设**：进化保守的 TF–靶基因关系更可能是功能性核心调控，而物种特异的更可能是适应性调控；区分这两类关系可以提高跨物种预测的可靠性。
   - **初步方法**：将 TFActProfiler 的人类和小鼠版本对比，结合多序列比对和系统发育分析，分类保守/特异调控关系；分析保守关系的序列特征（如 motif 保守性、增强子保守性）。
   - **验证方式**：在第三种物种（如大鼠）的 KD 数据上验证保守关系的预测精度是否更高。
   - **创新状态**：unverified