## 01 基本信息
- **标题**: A transcription factor regulatory atlas for activity inference and perturbation prediction
- **作者与单位**: Sugimoto, Hikaru; Tsuyuzaki, Koki; Zou, Ziyang; Oki, Shinya; Ohta, Tazro; Kawakami, Eiryo（单位未在摘要中提供）
- **期刊/预印本平台**: Nucleic Acids Research
- **年份**: 2026
- **论文类型**: 资源/方法学论文（Resource & Methodology）
- **领域**: 计算生物学；转录调控；TF–mRNA 调控网络；扰动预测
- **关键词**: transcription factor activity inference; TF–mRNA regulatory network; perturbation prediction; RNA-seq; regulon
- **DOI/arXiv 号**: 10.1093/nar/gkag897
- **代码**: https://github.com/HikaruSugimoto/tfactprofiler
- **数据**: 见 Data availability 节（多个公开数据集，详见第 10 节）
- **阅读日期**: 未提供
- **在该课题方向中的位置**: 本文属于「TF–DNA 互作 × AI/计算方法」中的**调控网络推断与下游效应预测**分支。它不是直接预测 TF–DNA 物理结合（如 ChIP-seq 或 motif 扫描），而是从转录组共变模式中学习**带符号、定量的 TF→mRNA 调控系数**，并用于 (1) 从表达谱推断 TF 活性；(2) 零样本预测 TF 敲低（KD）后的全转录组响应。其核心可迁移点在于：将先验 TF–DNA 结合信息（ChIP、motif）与大规模转录组整合，转化为可复用的调控先验矩阵，并支持不确定性估计。

## 02 一句话总结
本文构建了 TFActProfiler——一个包含 2,606,176 条带符号 TF–mRNA 调控系数的资源，通过整合 ChIP/motif 先验与大规模 bulk/single-cell RNA-seq 共变模式，在 TF 敲低基准上提升了 TF 活性推断准确率，并能在无任务匹配训练数据的情况下（零样本）预测 TF 敲低后的全转录组表达响应方向。

## 03 研究问题
- **具体问题**: 如何从转录组数据中准确推断 TF 活性，并在没有匹配扰动训练数据的情况下预测 TF 扰动（如敲低）后的全转录组响应？
- **为什么重要**: TF 是基因调控的核心，异常 TF 活性与多种疾病相关。但 RNA-seq 直接测量的只是 TF 的 mRNA 丰度，并不等于 TF 活性（受翻译后修饰、核定位、竞争性结合等影响）。同时，全面扰动实验（如 Perturb-seq）成本高昂，无法覆盖所有 TF × 细胞类型组合。因此，计算推断 TF 活性与预测扰动响应具有重要转化价值（如疾病机制解析、药物靶点发现）。
- **现有方法不足**:
  1. **精度-覆盖度权衡**: 高精度 curated 资源（如 DoRothEA、CollecTRA）覆盖 TF 少；高覆盖资源（如 ChIP-Atlas、共表达网络）含大量间接/非功能性结合，精度低。
  2. **缺乏符号信息**: 多数资源只给出 TF–mRNA 关联，不标注激活/抑制方向，导致活性推断时符号混淆。
  3. **缺乏不确定性估计**: 现有方法对推断出的 TF 活性没有可靠性度量，无法判断哪些结果可信。
  4. **扰动预测依赖任务匹配数据**: 现有模型（如 CPA、scGPT、scFoundation）需要大量扰动训练数据，在常见的小样本 bulk case-control 场景（无匹配扰动数据）下不可用。
- **精确研究问题 (Can...?)**: Can a signed, quantitative TF–mRNA regulatory prior, learned by integrating heterogeneous binding/motif evidence with large-scale transcriptomic covariation, enable accurate TF activity inference and zero-shot prediction of transcriptome-wide responses to TF knockdown, without task-matched perturbation training data?

## 04 背景与发展脉络
> 注：以下脉络基于本文摘要与引文框架整理，标注为「仅本文框架」；未经外部系统核验。

- **阶段一：基于 curated 数据库的 regulon 方法**（如 DoRothEA、CollecTRA）
  - 优点：符号明确、精度较高
  - 局限：覆盖度有限，依赖人工文献 curation，难以扩展到新细胞类型/物种
- **阶段二：基于 ChIP-seq / motif 的高覆盖资源**（如 ChIP-Atlas、ENCODE）
  - 优点：覆盖广，直接反映 TF–DNA 物理结合
  - 局限：结合 ≠ 功能调控；缺乏符号信息；含大量非功能性/间接结合
- **阶段三：基于共表达的调控网络推断**（如 WGCNA、GENIE3、SCENIC）
  - 优点：数据驱动，可扩展到任意转录组
  - 局限：共表达 ≠ 因果调控；符号推断困难；易受混淆因素影响
- **阶段四：深度生成模型 / 基础模型**（如 scGPT、scFoundation、CPA、Geneformer）
  - 优点：可学习复杂非线性关系，扰动预测能力强
  - 局限：需要大量任务匹配训练数据；在小样本 bulk 场景下性能不稳定；可解释性差
- **本文主张的位置**：TFActProfiler 位于阶段二与阶段三之间——以 ChIP/motif 先验定义候选边集（保证覆盖度与生物学相关性），再用大规模转录组共变回归估计符号与权重（补充功能信息），从而在精度与覆盖度之间取得平衡，并额外支持零样本扰动预测与不确定性估计。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 精度-覆盖度权衡 | 高精度资源覆盖 TF 少，高覆盖资源精度低 | curated 资源受限于人工 curation 成本；ChIP/共表达资源含大量间接/非功能性关联 | Results 节（TFActProfiler 构建部分）；"existing approaches often face a trade-off between regulator coverage and prediction accuracy" |
| 缺乏符号信息 | 多数资源不区分激活/抑制，导致活性推断方向混淆 | 结合数据（ChIP/motif）本身不含功能方向；共表达无法可靠推断因果方向 | Introduction 节；"most lack information about whether a TF activates or represses its target" |
| 缺乏不确定性估计 | 用户无法判断推断出的 TF 活性是否可信 | 现有方法未建模先验与数据之间的不一致性 | Discussion 节；"we defined a simple mean-squared-error-based reliability metric" |
| 扰动预测依赖任务匹配数据 | 小样本 bulk 场景下无法使用现有扰动预测模型 | 深度模型需要大量扰动数据训练；回归模型需要匹配的 perturbation 数据 | Introduction 节；"often require substantial task-specific training data" |
| 跨物种迁移困难 | 人类训练的调控资源难以直接用于小鼠等模式生物 | 缺乏跨物种的系统性迁移策略 | Results 节（小鼠基准）；"orthology-mapped TFActProfiler prior" |

## 06 核心思想
1. **表面方法**：整合三类先验（ChIP-Atlas 结合、motif 预测、curated 数据库）构建候选 TF–mRNA 边集，然后在大规模 bulk 和 single-cell RNA-seq 图谱上，对每个候选边做 cluster-wise 岭回归，估计带符号的调控系数；最终得到全局与器官特异性的 TF–mRNA 调控矩阵。下游任务：(a) 用 ulm 等富集方法从表达谱推断 TF 活性；(b) 用线性映射零样本预测 TF 敲低后的表达响应；(c) 用 MSE 度量推断可靠性。
2. **核心洞察**：**先验定义结构，数据估计参数**——用 ChIP/motif 先验限定候选边（解决覆盖度与生物学相关性），用转录组共变回归估计符号与权重（解决功能方向与定量强度）。这一「结构先验 + 数据参数化」的范式避免了纯数据驱动方法的混淆问题，也避免了纯先验方法的覆盖度限制。
3. **可能的普适教训 [Analysis]**：在生物网络推断中，**异质先验的整合比单一数据源的深度建模更有效**。本文表明，即使使用简单的线性回归，只要先验边集设计合理（结合多个互补证据源），其性能也能超越复杂的深度模型。这提示在 TF–DNA 互作建模中，**先验质量 > 模型复杂度**。

## 07 方法总览
- **输入**：
  - 先验 TF–mRNA 候选边集（来自 ChIP-Atlas、motif 预测、curated 数据库）
  - 大规模 bulk RNA-seq 图谱（多个公开数据集）
  - 大规模 single-cell RNA-seq 图谱（用于 cluster-wise 回归）
  - 用户提供的目标表达矩阵（用于 TF 活性推断或扰动预测）
- **输出**：
  - TFActProfiler 资源：2,606,176 条带符号 TF–mRNA 系数（全局 + 器官特异性）
  - TF 活性评分（每个样本 × 每个 TF）
  - 零样本扰动预测：TF 敲低后的全转录组表达变化向量
  - 可靠性评分（MSE-based）
- **模块**：
  1. 先验整合模块：合并 ChIP-Atlas、motif、curated 三类证据，去重、统一基因标识
  2. 岭回归估计模块：对每个 cluster（细胞类型/组织），以 TF 表达为自变量、mRNA 表达为因变量，拟合稀疏线性模型（系数矩阵 K，非先验边置零）
  3. 归一化与聚合模块：cluster 内系数归一化，跨 cluster 聚合得到全局与器官特异性共识系数
  4. TF 活性推断模块：基于 ulm（univariate linear model）等富集方法，将表达矩阵与调控矩阵结合
  5. 零样本扰动预测模块：给定 TF 敲低幅度 Δx，通过线性映射 Δy = W·Δx 预测下游表达变化
  6. 可靠性估计模块：计算先验系数与数据重估系数之间的 MSE
- **训练/估计流程**：先验边集 → 对每个 cluster 做岭回归 → 系数归一化 → 跨 cluster 聚合 → 得到最终调控矩阵 → 用于下游任务
- **工具**：Python；scikit-learn、NumPy、Pandas、Statsmodels、SciPy；decoupleR（用于基准测试）
- **假设**：
  - TF mRNA 丰度可作为 TF 活性的近似代理（线性关系）
  - 先验边集覆盖了大部分功能性 TF–mRNA 调控关系
  - 调控关系在相似细胞类型间可迁移（cluster-wise 聚合）
  - 线性模型足以捕捉 TF→mRNA 的主要调控效应（一阶近似）

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 先验整合 | 合并 ChIP-Atlas、motif、curated 三类证据，构建候选 TF–mRNA 边集 | 单一先验源覆盖不全或含噪声；整合可互补 | 输入：三类先验数据库；输出：候选边集（含方向先验） | Results 节（构建部分）；"integrating heterogeneous prior evidence" | 预期影响 [Analysis]：移除后候选边集覆盖度下降，可能遗漏功能性调控关系，导致活性推断召回率降低 |
| Cluster-wise 岭回归 | 在每个细胞类型/组织 cluster 内估计 TF→mRNA 系数 | 调控关系具有细胞类型特异性；岭回归处理高维共线性 | 输入：cluster 内 TF/mRNA 表达矩阵 + 候选边集；输出：cluster 特异性系数矩阵 | Methods 节（回归部分）；"cluster-wise regularized regression" | 预期影响 [Analysis]：移除后无法捕捉细胞类型特异性调控，全局系数在特定组织中精度下降 |
| 系数归一化与聚合 | 将 cluster 内系数归一化，跨 cluster 聚合为共识系数 | 不同 cluster 表达量纲不同；需要全局可用的调控矩阵 | 输入：cluster 特异性系数；输出：全局 + 器官特异性共识矩阵 | Methods 节（聚合部分）；"coefficients were first normalized within each dataset before aggregation" | 预期影响 [Analysis]：移除后跨数据集系数不可比，全局矩阵质量下降 |
| TF 活性推断（ulm） | 从表达谱推断 TF 活性评分 | 核心下游任务之一 | 输入：表达矩阵 + 调控矩阵；输出：TF 活性评分 | Results 节（基准部分）；"TFActProfiler combined with ulm achieved the best overall performance" | 实测效应：替换为无符号资源（如 ChIP-Atlas）后性能下降（Results 图 2B） |
| 零样本扰动预测 | 用线性映射预测 TF 敲低后的表达变化 | 无需任务匹配训练数据即可预测扰动响应 | 输入：TF 敲低幅度 Δx + 调控矩阵；输出：Δy_pred | Results 节（扰动预测部分）；"predicted responses using TFActProfiler significantly correlated with the experimental measurements" | 预期影响 [Analysis]：移除后丧失零样本预测能力，需依赖 Perturb-seq 等昂贵实验数据 |
| 可靠性估计（MSE） | 量化先验与数据的一致性 | 用户需要判断推断结果的置信度 | 输入：先验系数 + 数据重估系数；输出：MSE 评分 | Methods 节（可靠性部分）；"a scale-comparable reliability score was defined as a mean squared error" | 预期影响 [Analysis]：移除后用户无法判断推断结果的可靠性，降低实际应用价值 |

## 09 关键公式符号
1. **岭回归估计 TF→mRNA 系数**（Methods 节）：
   - $Y \approx K \cdot X$
   - $Y \in \mathbb{R}^{n \times c}$：mRNA 表达矩阵（n 个 mRNA，c 个样本）
   - $X \in \mathbb{R}^{m \times c}$：TF 表达矩阵（m 个 TF，c 个样本）
   - $K \in \mathbb{R}^{n \times m}$：TF–mRNA 系数矩阵（行 = mRNA，列 = TF；非先验边置零）
   - 岭回归目标：$\min_K \|Y - KX\|_F^2 + \lambda \|K\|_F^2$（λ 为岭正则化参数）

2. **TF 活性推断的线性映射**（Methods 节）：
   - $x_j \approx W \cdot y_j$
   - $x_j \in \mathbb{R}^m$：样本 j 的 TF 活性向量
   - $y_j \in \mathbb{R}^n$：样本 j 的 mRNA 表达向量
   - $W \in \mathbb{R}^{m \times n}$：TF–mRNA 系数矩阵的转置形式（行 = TF，列 = mRNA；正 = 激活，负 = 抑制，缺失 = 0）

3. **零样本扰动预测**（Methods 节）：
   - $\Delta y = W \cdot \Delta x$
   - $\Delta x = -\gamma x_k e_k$：TF k 敲低引起的 TF 活性变化（$e_k$ 为标准基向量，$\gamma$ 控制敲低强度）
   - $\Delta y$：预测的 mRNA 表达变化

4. **可靠性评分**（Methods 节）：
   - $MSE_j = \frac{1}{m} \|x_j - W \cdot K \cdot x_j\|^2$
   - 衡量先验系数 W 与数据重估系数 K 的自洽性；值越低表示推断越可靠

## 10 实验设计与证据链
**数据集/群体**：
- 训练数据：大规模 bulk RNA-seq 图谱（多个公开数据集，具体来源未在摘要中列出）
- 单细胞数据：PBMC 数据集（decoupleR 分发）、人类睾丸单细胞数据（GSE106487）
- 基准数据：
  - 人类 TF 敲低（KD）RNA-seq：4 个细胞系（RPE1、K562、HepG2、Jurkat），共 1,423 个扰动实验（来源：Perturb-seq 相关研究，PRJNA831566、PRJNA1100571）
  - 小鼠 TF KD RNA-seq：KnockTF 2.0 资源
  - 磷酸化蛋白质组数据：猴痘病毒（MPXV）感染的人原代成纤维细胞（HFFs）时间序列（0/6/12/24 hpi）
  - 疾病数据：透明细胞肾细胞癌（ccRCC）bulk RNA-seq（n=157，含复发随访）；特发性肺纤维化（IPF）bulk RNA-seq（n=95 组织芯，10 IPF + 6 对照，GSE124685）
  - 脂肪生成：人脂肪生成单核 RNA-seq（GSE 未提供）
  - 小鼠 torpor：GSE117937

**指标**：
- TF 活性推断：识别被敲低 TF 的排名（rank）或 AUC
- 扰动预测：预测 Δy 与观测 Δy 的 Pearson 相关系数、MSE
- 可靠性：MSE 评分与推断准确率的相关性
- 磷酸化验证：TF 活性轨迹与磷酸化位点变化的相关性
- 配体-受体推断：AUC（ROC 分析）

**基准/对比方法**：
- TF 活性推断：CollecTRA、ChIP-Atlas、DoRothEA 等 regulon 资源（经 decoupleR 框架）
- 扰动预测：scFoundation、scGPT 嵌入 + 线性模型；CellOracle 风格回归模型
- 消融对照：TFActProfiler−（系数替换为均匀 1，即无定量信息）

**评测协议**：
- 每个 KD 实验中，计算所有 TF 的活性得分，检查被敲低 TF 的排名是否显著靠前（方向正确）
- 扰动预测：留一法（leave-one-out）评估未见过的 TF 敲低
- 跨物种：人类训练的 TFActProfiler 经同源映射后用于小鼠数据

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|--------------|-------------------|------|
| 人类 TF KD 基准（4 细胞系，1,423 实验） | TFActProfiler 提升 TF 活性推断准确率 | TFActProfiler vs CollecTRA、ChIP-Atlas 等，均用 ulm | TFActProfiler + ulm 最佳（具体数值未提供） | 定量符号信息提升活性推断 | 未提供与非线性方法的对比 | Results 图 2B |
| 消融实验（TFActProfiler−） | 定量系数贡献 | 保留边集、系数置 1 | 性能下降 | 定量权重 > 二元边集 | 未提供具体下降幅度 | Results 节 |
| 小鼠 KnockTF 基准 | 跨物种迁移 | 人类 TFActProfiler 同源映射 vs CollecTRA 小鼠版 | TFActProfiler 更优（具体数值未提供） | 调控信息跨物种保守 | 未提供与小鼠专属资源的全面对比 | Results 节（补充图 S1C、S1D） |
| scTF-seq 验证 | TF 活性与实验扰动剂量相关 | TFActProfiler vs CollecTRA 的活性得分与 TF 剂量相关 | TFActProfiler 相关性更强 | 活性得分反映真实 TF 活性 | 未提供因果性证据 | Results 节（补充图 S1E） |
| 磷酸化蛋白质组（MPXV 感染 HFFs） | TF 活性反映磷酸化调控 | TFActProfiler 活性轨迹 vs 磷酸化位点变化 | 显著正相关（具体数值未提供） | 活性推断捕获翻译后修饰效应 | 相关性不等于因果；样本量小 | Results 图 2D、2E |
| 配体-受体推断（人类睾丸） | TF 活性增强 LR 推断 | 有/无 TF 活性增强的 LR 评分 | AUC 提升 | 下游 TF 活性提供额外信息 | 仅在单一组织验证 | Results 图 2H |
| ccRCC 复发分析 | TF 活性与临床结局相关 | Cox 比例风险模型 | E2F7、NFYA、NFYB、IRX5 与复发显著相关 | 活性推断有临床转化价值 | 未做多变量校正或独立验证 | Results 节（补充图 S1G、S1H） |
| 脂肪生成（TRPS1） | 活性推断复现已知调控因子 | TRPS1 活性在早期脂肪生成中升高 | 显著升高（P < .01） | 活性推断可发现已知调控因子 | 未验证新因子 | Results 节（补充图 S1K） |
| 小鼠 torpor（Atf3） | 活性推断识别已知 torpor 调控因子 | Atf3 活性在 torpor 中升高 | 显著升高（P < .01）；CollecTRA 未检出 | TFActProfiler 灵敏度更高 | 单基因案例 | Results 节（补充图 S1M） |
| IPF 逆转筛选 | 零样本扰动预测可用于疾病逆转 | 预测各 TF 敲低后表达变化与 IPF-健康差异表达的相关性 | SMAD7、HMGB2 排名靠前 | 可优先候选 TF 用于实验验证 | 仅为 in silico 预测，无实验验证 | Results 节（补充图 S3B） |

## 11 结论正确解读
- **任务范围**：本文的 TF 活性推断与扰动预测均基于**转录组共变**，而非 TF–DNA 物理结合的直接测量。结论仅适用于「TF mRNA 丰度可近似反映 TF 活性」的假设下。
- **Oracle/真值输入**：基准测试使用实验 KD 数据作为真值，但 KD 效率、脱靶效应、补偿机制等未完全控制。磷酸化验证使用 curated 磷酸化位点注释（SIGNOR），其覆盖度有限。
- **端到端状态**：TFActProfiler 是**预训练资源**，用户需自行运行 ulm 等推断方法；不是端到端的深度学习模型。零样本扰动预测是线性近似，不捕捉非线性调控、反馈回路、表观遗传状态等。
- **算力成本**：岭回归在 cluster 级别运行，计算成本远低于深度模型；但大规模图谱的预处理和存储需要一定资源。
- **历史数据依赖**：训练数据来自公开 RNA-seq 图谱，存在批次效应、组织覆盖不均、细胞类型偏差。跨物种迁移依赖同源映射的准确性。
- **最难场景**：低表达 TF、高共线性 TF 家族、细胞类型特异性调控、翻译后修饰主导的 TF 活性变化。
- **群体/领域边界**：主要基于人类数据训练，小鼠验证有限；未覆盖非模式生物。疾病应用（ccRCC、IPF）为回顾性分析，无前瞻性验证。
- **有边界的复述**：TFActProfiler 是一个带符号、定量的 TF–mRNA 调控资源，在已测试的人类细胞系和小鼠数据中，其活性推断准确率优于现有 regulon 资源，并能零样本预测 TF 敲低后的表达变化方向；但其预测为线性近似，不适用于需要精确效应量或非线性动力学的场景。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 线性近似 | 扰动预测是线性映射，无法捕捉非线性调控、反馈回路、动态变化 | 整合非线性或动态模型 | Discussion 节；"they are merely linear approximations of regulatory dynamics rather than exact forecasts of expression changes" |
| 上下文依赖性 | TF–mRNA 调控关系具有高度细胞类型/状态特异性，全局系数可能不适用于特定场景 | 扩展至更多细胞类型和生理/病理状态；开发上下文感知的系数估计 | Discussion 节；"expanding to rare cell types and diverse physiological contexts requires more data and context-aware transfer strategies" |
| 非因果性 | 系数来自共变回归，不能证明因果关系；部分符号可能受混淆因素影响 | 结合 CRISPR 筛选等因果扰动数据验证 | Discussion 节；"should be interpreted as heuristic consensus estimates rather than definitive causal mode-of-regulation annotations" |
| 未与其他方法全面对比 | 未与非线性深度模型（如 scGPT、scFoundation 全模型）在完全匹配条件下对比 | 未来在匹配条件下进行基准测试 | Discussion 节；"A priority for future work is to evaluate our model against nonlinear methods under matched conditions" |
| 资源非替代品 | TFActProfiler 不替代 CollecTRA 等 curated 资源，后者在文献追溯方面有独特价值 | 两者互补使用 | Discussion 节；"TFActProfiler does not replace CollecTRA" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| 线性回归估计 TF→mRNA 系数 | 共变 ≠ 因果；高共线性 TF 家族（如 AP-1 成员）可能导致系数不稳定或符号翻转 | 若系数不可靠，下游活性推断和扰动预测的准确性将受影响 | 在合成数据中注入已知调控关系，检验系数恢复能力；或在 TF 家族成员间进行交叉验证 | Methods 节（岭回归部分） |
| 以 TF mRNA 作为 TF 活性代理 | 许多 TF 活性受翻译后修饰（如磷酸化）、核定位、竞争性抑制调控，mRNA 丰度可能严重偏离活性 | 这是整个方法的核心假设，若违反则所有推断失效 | 在磷酸化数据集中比较 mRNA 丰度与磷酸化位点状态的预测能力 | Results 节（磷酸化验证部分） |
| 先验整合的边集可能引入偏差 | ChIP-Atlas 和 motif 预测偏向于研究充分的 TF，对未充分研究的 TF 覆盖不足 | 可能导致对「已知」TF 的过度拟合，对「未知」TF 的推断能力有限 | 按 TF 研究密度分层分析推断准确率 | Results 节（构建部分） |
| 零样本扰动预测的评估方式 | 仅用 Pearson 相关和 MSE 评估，未报告方向准确率（符号一致性）或效应量校准 | 相关高但方向错误的情况可能被掩盖 | 补充方向准确率、top-k 富集分析等指标 | Results 节（扰动预测部分） |
| 跨物种迁移的验证有限 | 仅验证了小鼠 KnockTF 和 torpor 数据，未覆盖更多物种 | 同源映射可能丢失物种特异性调控信息 | 在更多物种（如斑马鱼、果蝇）的扰动数据上验证 | Results 节（补充图 S1C、S1D） |
| 与深度模型的对比不完整 | 未与 scGPT、scFoundation 的完整模型（而非仅嵌入）对比 | 无法判断线性先验方法是否真的优于深度模型 | 在相同基准上运行完整深度模型并对比 | Discussion 节；"A priority for future work is to evaluate our model against nonlinear methods under matched conditions" |
| 可靠性评分的验证不足 | MSE 评分仅作为启发式指标，未与实验验证的准确率建立定量关系 | 用户无法将 MSE 值映射为实际置信度 | 在多个数据集中建立 MSE 与准确率的校准曲线 | Methods 节（可靠性部分） |

## 14 学到什么
> 标题：Agent 提炼的知识候选

1. **结构先验 + 数据参数化的范式**：本文最核心的可迁移思路是「用先验定义搜索空间，用数据估计参数」。在 TF–DNA 互作建模中，可借鉴此思路：用 ChIP-seq/motif 先验定义候选 TF–DNA 结合位点，再用大规模转录组/表观基因组数据估计功能性权重，而非直接对所有位点做无差别建模。
2. **符号信息的重要性**：本文反复强调带符号（激活/抑制）的调控信息对活性推断的关键作用。在 TF–DNA 互作研究中，仅知道「结合」不够，还需知道「结合后是激活还是抑制」。可迁移到 ChIP-seq 数据分析中：结合峰 + 方向性注释（如 H3K27ac vs H3K27me3 共定位）可显著提升下游推断质量。
3. **不确定性估计的实用价值**：本文提出的 MSE 可靠性评分为用户提供了判断依据。在 AI 辅助的 TF–DNA 结合预测中，类似的不确定性估计（如 ensemble 方差、Bayesian 置信区间）可帮助实验学家优先验证高置信度预测。
4. **跨物种迁移策略**：通过同源映射将人类调控资源迁移到小鼠，并取得优于小鼠专属资源的效果，说明**调控逻辑的进化保守性**可被利用。在 TF–DNA 结合预测中，可考虑跨物种迁移学习以弥补模式生物训练数据不足的问题。
5. **线性模型的竞争力**：在扰动预测任务中，简单的线性映射（基于良好设计的先验）可以媲美甚至超越深度模型。这提示在 TF–DNA 互作建模中，**特征/先验设计比模型架构更重要**，不应盲目追求模型复杂度。
6. **多组学验证框架**：本文的验证策略（KD 基准 + 磷酸化验证 + 单细胞 + 疾病关联）为 TF–DNA 互作模型的评估提供了模板：不仅要在结合预测上评估，还要在下游功能效应（基因表达变化、表型关联）上验证。

## 15 与已有知识连接
- **相似工作**：与 **DoRothEA**（Garcia-Alonso et al.）、**CollecTRA**（Müller-Dott et al.）、**CellOracle**（Kamimoto et al.）同属 regulon-based TF 活性推断方法。本文的差异化在于：整合多源先验 + 大规模数据估计定量系数 + 零样本扰动预测。
- **组合方向**：与 **SCENIC+**（Braun-Breton et al.）的 enhancer-based regulon 推断可互补——SCENIC+ 从增强子-基因连接推断 regulon，TFActProfiler 从表达共变估计系数，两者可组合为「增强子-启动子-表达」的端到端调控模型。
- **冲突/竞争**：与 **scGPT / scFoundation** 等基础模型的扰动预测能力形成对比。本文表明线性先验方法在小样本场景下可能更优，但未在完全匹配条件下对比，需谨慎解读。
- **可迁移领域**：本文的「先验整合 + 岭回归 + 零样本预测」框架可迁移到其他调控层级：(1) **miRNA–mRNA** 调控推断；(2) **增强子–启动子** 互作预测；(3) **TF–TF** 协同调控建模。方法本身不限于转录调控，也可用于蛋白质–蛋白质互作网络的功能权重估计。
- **与物理模拟的关联 [Analysis]**：本文方法不涉及 MD 或对接模拟，但其「先验结构 + 数据参数」的思路与**粗粒化分子模拟**中的「已知接触图 + 数据驱动势函数」有方法论上的相似性。在 TF–DNA 结合自由能预测中，可借鉴此思路：用已知晶体结构/接触图定义候选相互作用，再用大规模突变实验数据估计能量参数。

## 16 研究想法
> 标题：Agent 生成的研究候选

1. **候选名称**：TF–DNA 结合方向性预测器（Directional TF–DNA Binding Predictor）
   - **来源局限/观察**：本文表明带符号的 TF–mRNA 调控信息显著提升活性推断，但 TF–DNA 结合数据（ChIP-seq）本身不含方向性。现有方法（如 DeepSEA、Basenji）预测结合概率但不预测激活/抑制方向。
   - **核心假设**：TF–DNA 结合的方向性（激活 vs 抑制）可由局部序列上下文 + 共结合因子 + 表观基因组状态预测。
   - **初步方法**：以 ChIP-seq 峰为中心，提取序列 + 表观基因组特征（H3K27ac、H3K4me1、H3K27me3），训练一个多任务模型同时预测结合概率和方向性；用 TFActProfiler 的符号系数作为弱监督标签。
   - **验证方式**：在 TF KD 数据中检验「预测为激活的 TF–DNA 结合」是否对应 KD 后下调的靶基因。
   - **创新状态**：unverified

2. **候选名称**：跨物种 TF 调控迁移学习框架（Cross-species TF Regulatory Transfer）
   - **来源局限/观察**：本文展示了人类→小鼠的调控迁移有效性，但仅用同源映射，未利用现代迁移学习技术。
   - **核心假设**：TF–DNA 结合基序和调控逻辑在物种间高度保守，可通过对抗域适应或元学习实现更精准的跨物种调控推断。
   - **初步方法**：在人类 TF–DNA 结合数据上预训练模型，用小鼠的少量标记数据微调；引入同源基因/同源 TF 作为锚点；比较不同迁移策略（同源映射 vs 域适应 vs 元学习）。
   - **验证方式**：在小鼠 KnockTF 和 torpor 数据上评估，与本文的同源映射基线对比。
   - **创新状态**：unverified

3. **候选名称**：不确定性感知的 TF 扰动优先级排序（Uncertainty-aware TF Perturbation Prioritization）
   - **来源局限/观察**：本文的 MSE 可靠性评分是全局的，未用于单 TF 级别的优先级排序。
   - **核心假设**：对每个 TF，其活性推断的可靠性不同；将可靠性纳入排序可提高实验验证的成功率。
   - **初步方法**：为每个 TF 计算可靠性评分（基于先验与数据的一致性），在疾病逆转筛选（如 IPF）中，将可靠性作为排序权重；与仅按效应量排序的基线对比。
   - **验证方式**：在 IPF 和 ccRCC 数据中，检验高可靠性 TF 是否更可能被独立实验验证。
   - **创新状态**：unverified

4. **候选名称**：物理模拟与调控网络联合的 TF 效应预测（Physics-informed TF Effect Prediction）
   - **来源局限/观察**：本文的线性模型不捕捉 TF–DNA 结合的物理化学细节（如结合亲和力、构象变化），而这些可能影响调控效应。
   - **核心假设**：将 MD 模拟或对接计算的结合亲和力作为先验特征，可提升 TF 敲低后表达变化的预测精度。
   - **初步方法**：对目标 TF–DNA 复合物进行短时 MD 模拟，提取结合自由能、接触面积等特征；将这些特征作为岭回归或轻量 ML 模型的额外输入；与纯转录组特征对比。
   - **验证方式**：在已有 TF KD 数据中，比较加入物理特征前后的预测精度。
   - **创新状态**：unverified

5. **候选名称**：单细胞分辨率下的 TF 活性异质性推断（Single-cell TF Activity Heterogeneity Inference）
   - **来源局限/观察**：本文的 TF 活性推断主要面向 bulk 数据，但单细胞数据中 TF 活性的细胞异质性对理解细胞命运决定至关重要。
   - **核心假设**：TFActProfiler 的调控矩阵可迁移到单细胞数据，且能捕获细胞亚群间的 TF 活性差异。
   - **初步方法**：将 TFActProfiler 的调控矩阵应用于 PBMC 单细胞数据，用 ulm 计算每个细胞的 TF 活性；用 UMAP 可视化 TF 活性景观；比较不同细胞亚群的 TF 活性差异。
   - **验证方式**：与已知的细胞类型标志 TF 对比，检验推断的 TF 活性是否与细胞类型一致。
   - **创新状态**：unverified