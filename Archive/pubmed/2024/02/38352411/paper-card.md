## 01 基本信息
- **标题**：Predicting the DNA binding specificity of transcription factor mutants using family-level biophysically interpretable machine learning
- **作者**：Liu, Shaoxun; Gomez-Alcala, Pilar; Leemans, Christ; Glassford, William J; Melo, Lucas A N; Lu, Xiang-Jun; Mann, Richard S; Bussemaker, Harmen J
- **单位**：未提供（根据通讯作者 Bussemaker 推断为 Columbia University，但原文未明确列出）
- **期刊/平台**：bioRxiv (preprint server for biology)
- **年份**：2024（预印本日期 2024-02-14）
- **论文类型**：预印本（方法学 + 实验验证）
- **领域**：蛋白质-DNA 互作；转录因子（TF）结合特异性；生物物理可解释机器学习
- **关键词**：transcription factor; DNA binding specificity; machine learning; biophysical model; bHLH; homeodomain; mutant; ΔΔΔG
- **DOI/arXiv 号**：10.1101/2024.01.24.577115
- **代码**：https://github.com/BussemakerLab/FamilyCode
- **数据**：NCBI SRA BioProject PRJNA1244358（SELEX-seq 原始数据）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「TF–DNA 结合机制 × 可解释机器学习」交叉方向，核心贡献是提出一个**家族级（family-level）**、**无参考结构（structure-agnostic）** 的机器学习框架 FamilyCode，利用野生型同源 TF 的定量结合数据预测**突变体**的 DNA 结合特异性变化（ΔΔΔG/RT）。与物理模拟（MD/对接）和结构预测（AlphaFold）路径形成互补，属于「序列→功能」的直接映射路线。

## 02 一句话总结
本文提出 FamilyCode 框架，利用同一 TF 家族内野生型同源蛋白的高通量结合数据（HT-SELEX/PBM），通过无参考四面体表示和 PCA-回归模型，预测 TF 点突变引起的 DNA 结合自由能变化（ΔΔΔG/RT），并在 bHLH 和 homeodomain 两个家族上验证了可行性。

## 03 研究问题
- **具体问题**：给定一个 TF 的蛋白序列点突变，如何定量预测其 DNA 结合特异性（base preference）的变化？
- **为什么重要**：疾病相关的 TF 错义突变可能不破坏结合，而是**改变结合偏好**（quantitative shift），这种微妙变化难以用实验逐一检测；高通量实验（PBM/SELEX）成本高、通量有限，需要计算预测来筛选候选突变。
- **现有方法不足**：
  - 结构预测（如 AlphaFold）只能给出静态结构，无法直接给出结合自由能变化；
  - 基于结构的能量计算（如 Rosetta、MD）对结合界面微小变化的精度有限，且需要结构信息；
  - 已有的序列-结合模型（如 DeepPBS、rCLAMPS）要么需要结构输入，要么是跨家族通用模型，对家族内精细变异不敏感。
- **精确研究问题（Can ... ?）**：Can a family-level, structure-agnostic machine learning model trained on wild-type TF binding data accurately predict the quantitative shift in DNA binding specificity (ΔΔΔG/RT) caused by point mutations in the TF DNA-binding domain?

## 04 背景与发展脉络
> 注：以下脉络基于本文引言与讨论，属于「经外部核验」的领域发展概述，但具体分期为本文框架。

1. **TF 结合特异性的定量建模**：从 PWM/PSSM 到能量模型（ΔΔG/RT），再到 ProBound 等可解释机器学习框架（Bussemaker lab 前期工作，Ref 22）。关键进展是能从 HT-SELEX 等数据中直接推断生物物理参数。
2. **高通量结合数据积累**：Taipale lab 的 HT-SELEX 数据（Ref 16, 33, 34）和 CisBP 的 PBM 数据（Ref 57-59）为数百个 TF 提供了定量结合模型。
3. **家族内变异分析**：早期工作（Ref 25-29）分析了野生型 TF 家族内结合特异性的差异，但多为定性或半定量。
4. **突变效应预测**：大规模突变体结合数据（Ref 18, 30）提供了 benchmark 机会，但计算方法仍以结构为基础（如 DeepPBS, Ref 49）或需要训练数据覆盖突变体（如 rCLAMPS, Ref 48）。
5. **本文位置**：提出**无需突变体数据**、**无需结构信息**的家族级预测方案，利用野生型同源 TF 的序列变异来推断突变效应，填补了「野生型数据丰富、突变体数据稀缺」场景下的预测空白。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 突变体结合数据稀缺 | 大多数 TF 突变体没有实验结合数据 | 实验成本高、通量有限 | Introduction: "PBM and SELEX-seq involve in vitro protein purification... labor-intensive and expensive" |
| 结构信息不可用或不可靠 | 许多 TF 无晶体结构，AlphaFold 预测的复合物结构精度不足以计算能量变化 | 结构预测 ≠ 能量预测 | Discussion: "predicting the energetic effect of base-pair or amino-acid substitutions at the protein-DNA interface... vastly simpler task" |
| 跨家族模型精度不足 | 通用模型（如 DeepPBS）对家族内精细变异不敏感 | 不同家族结合模式差异大，通用模型无法捕捉家族特异的序列-功能关系 | Results: DeepPBS 在 homeodomain 突变体预测上表现不佳（R² = 0.33 vs FamilyCode R² = 0.98，针对 HLH-1） |
| 直接相减 ΔΔG 的数值不稳定 | 对不利碱基的 ΔΔG 估计波动大，直接相减产生噪声 | 实验数据对低亲和力事件的估计误差大 | Methods: "the undue influence of large fluctuations in the estimated value of unfavorable bases" → 用四面体表示解决 |
| 序列位置间的共变/连锁不平衡 | 同源 TF 的氨基酸位点间存在相关性，简单回归会混淆因果 | 进化选择造成位点间依赖 | Methods: 使用迭代特征选择（forward selection）而非全模型回归 |

## 06 核心思想
1. **表面方法**：
   - 用 ProBound 从 HT-SELEX/PBM 数据推断每个野生型 TF 的 ΔΔG/RT 结合模型；
   - 将每个 DNA 位置的 4 个相对亲和力映射到**四面体**中的 3D 坐标（无参考表示，避免选择参考碱基）；
   - 对每个 DNA 位置，以 TF 蛋白序列的氨基酸身份为特征，用 PCA + 迭代线性回归预测四面体坐标；
   - 对突变体，将突变后的氨基酸身份代入模型，预测新的四面体坐标，再变换回 ΔΔG/RT，与野生型相减得到 ΔΔΔG/RT。

2. **核心洞察**：
   - **家族内同源 TF 的序列变异是天然的「突变实验」**：进化已经采样了大量氨基酸替换，野生型同源物之间的结合差异可以用于学习「序列→结合偏好」的映射；
   - **四面体表示消除了参考碱基的任意性**：直接对 4 个碱基的相对偏好建模，避免因参考碱基选择不同导致的数值不稳定；
   - **PCA 降维 + 迭代特征选择**：将 3D 坐标投影到主成分方向，分别回归，避免多变量共线性和过拟合。

3. **可能的普适教训 [Analysis]**：
   - 在数据稀缺的突变体预测场景中，**利用同源家族的天然变异**是一种高效策略，比依赖结构计算或大规模突变体实验更经济；
   - **表示选择至关重要**：将物理量（ΔΔG）映射到几何空间（四面体）可以改善数值稳定性和可解释性；
   - 结构信息不是预测结合特异性的必要条件——**序列层面的统计关联**在家族内可以捕捉到足够的信号。

## 07 方法总览
- **输入**：
  - 训练集：同一 TF 家族内多个野生型 TF 的蛋白序列（已对齐到 PFAM HMM）+ 对应的 DNA 结合模型（ΔΔG/RT，由 ProBound 从 HT-SELEX 或 PBM 推断）；
  - 预测目标：一个 TF 突变体的蛋白序列。
- **输出**：突变体的 DNA 结合模型（ΔΔG/RT 矩阵），以及相对野生型的 ΔΔΔG/RT 变化。
- **模块**：
  1. **数据预处理**：蛋白序列对齐（HMMER 到 PFAM 家族 HMM）；结合模型推断（ProBound/PyProBound）；
  2. **四面体嵌入**：将每个 DNA 位置的 4 个相对亲和力 → 归一化频率 → 四面体 3D 坐标；
  3. **PCA 降维**：对每个 DNA 位置的 3D 坐标做 PCA，取 3 个主成分方向；
  4. **迭代特征选择 + 线性回归**：对每个主成分，以氨基酸身份为特征，用 forward selection 选择显著相关的蛋白位置，拟合线性模型；
  5. **预测与逆变换**：对突变体序列，用模型预测 3D 坐标 → 逆 PCA → 逆四面体变换 → ΔΔG/RT → 与野生型相减得 ΔΔΔG/RT。
- **训练**：无传统训练/测试划分，采用 leave-one-out 交叉验证（每次留出一个 TF 作为测试）。
- **工具**：ProBound（https://github.com/RubeGroup/ProBound）、PyProBound、R（manova, svd, aov 函数）、HMMER。
- **反馈回路**：无显式反馈回路；模型为单次前向预测。
- **假设**：
  - 家族内同源 TF 的骨架几何固定，结合特异性差异主要由侧链化学性质决定；
  - 氨基酸身份对结合偏好的效应是**可加**的（线性模型）；
  - 训练集中的野生型 TF 覆盖了足够的序列多样性。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ProBound 结合模型推断 | 从 HT-SELEX/PBM 原始数据推断每个 TF 的 ΔΔG/RT 参数 | 提供定量的结合特异性度量，而非定性 consensus | 输入：HT-SELEX reads / PBM 荧光强度；输出：ΔΔG/RT 矩阵 | Methods: "fit a single binding energy model to data from all rounds of the SELEX assay simultaneously" | 无法获得定量结合模型，整个框架失去输入 |
| 四面体嵌入 | 将 4 个相对亲和力映射到 3D 坐标 | 消除参考碱基选择带来的数值不稳定；提供几何可解释性 | 输入：4 个相对亲和力；输出：3D 坐标 (x,y,z) | Methods: "maps each PSAM column containing four elements to the Cartesian coordinates" | 直接相减 ΔΔG 会产生噪声（作者明确说明） |
| PCA 降维 | 对 3D 坐标做主成分分析 | 将 3D 空间旋转到数据自然变化方向，使回归更有效 | 输入：所有 TF 在某 DNA 位置的 3D 坐标矩阵；输出：3 个主成分方向 | Methods: "performed principal component analysis (PCA) on the cloud of points" | 回归目标不再是物理方向，但预测精度可能下降 [预期效应] |
| 迭代特征选择 + 线性回归 | 对每个主成分选择显著蛋白位置并拟合线性模型 | 避免过拟合；处理位点间共线性 | 输入：氨基酸身份编码 + 主成分值；输出：回归系数 | Methods: "iteratively selected for the features to include" | 若用全模型，可能因共线性导致系数不稳定 [预期效应] |
| 四面体逆变换 | 将预测的 3D 坐标变换回 ΔΔG/RT | 将预测结果转化为可解释的结合能量 | 输入：预测的 3D 坐标；输出：ΔΔG/RT 矩阵 | Methods: "transformed the difference back to energy space" | 无法获得能量值，预测不可解释 |
| 突变体 ΔΔΔG/RT 计算 | 预测突变体与野生型的结合能量差 | 直接量化突变效应 | 输入：突变体预测 ΔΔG/RT 与野生型 ΔΔG/RT；输出：ΔΔΔG/RT | Methods: "calculated the shift between the mutant and wild-type TF in tetrahedron space" | 无法评估突变效应 |

## 09 关键公式符号
1. **四面体嵌入**：
   \[
   \mathbf{v}_j = \begin{bmatrix} f_{jA} & f_{jC} & f_{jG} & f_{jT} \end{bmatrix} \times \begin{bmatrix} 1 & 1 & 1 \\ 1 & -1 & -1 \\ -1 & 1 & -1 \\ -1 & -1 & 1 \end{bmatrix}
   \]
   - \( f_{jb} = w_{jb} / \sum_{b'} w_{jb'} \)：归一化相对亲和力（频率）
   - \( w_{jb} \)：PSAM 中位置 j 碱基 b 的相对亲和力
   - \( \mathbf{v}_j = (v_{jx}, v_{jy}, v_{jz}) \)：四面体中的 3D 坐标
   - 用途：将 4 个碱基偏好映射到无参考的 3D 空间
   - 来源：Methods "Tetrahedral representation of DNA binding energies"

2. **线性回归模型**（对每个主成分 c）：
   \[
   m_{cf} = \beta_{cr} \sum_a \delta(a, a(f,r)) \frac{1}{F_{r a(f)}} \sum_{f' \in F_{r a(f)}} m_{cf'}
   \]
   - \( m_{cf} \)：TF f 在主成分 c 上的坐标值（中心化后）
   - \( \beta_{cr} \)：回归系数
   - \( \delta(a, a') \)：Kronecker delta（0/1 指示函数）
   - \( a(f,r) \)：TF f 在蛋白位置 r 的氨基酸身份
   - \( F_{r a(f)} \)：除 f 外所有在位置 r 具有相同氨基酸的 TF 集合
   - 用途：用氨基酸身份预测主成分坐标
   - 来源：Methods "Construction of SVD-regression model"

3. **置信度评分**：
   \[
   \text{Confidence}(f) = \sum_{r,a,c} \delta(a, a(f,r)) \frac{n_{ra}}{\max_{a'} n_{ra'}} \frac{\beta_{rac}}{\sum_{ra'} \delta(a', a(f,r)) \beta_{ra'c}}
   \]
   - \( n_{ra} \)：训练集中位置 r 氨基酸 a 的计数
   - \( \beta_{rac} \)：位置 r 氨基酸 a 对主成分 c 的回归系数
   - 用途：评估预测的可靠性
   - 来源：Methods "Assessment of prediction confidence"

## 10 实验设计与证据链
**数据集与群体**：
- bHLH 家族：62 个蛋白（HT-SELEX 数据来自 Ref 16, 33, 34），52 个通过质量过滤；
- homeodomain 家族：414 个蛋白（HT-SELEX + PBM 混合数据）；
- 突变验证：HES2（野生型偏好 CACGTG）和 ASCL2（野生型偏好 CAGCTG）的 6 个突变体（R5K、V13R、R5K+V13R 等），通过 SELEX-seq 实验验证；
- HLH-1 突变体（L13R、L13T、L13V）：来自 Ref 59 的 PBM 数据。

**指标**：
- 预测 vs 实验 ΔΔΔG/RT 的 R²（决定系数）
- RMSD（均方根偏差）
- 与基线方法比较：closest-paralog、similarity regression（rCLAMPS）、DeepPBS

**评测协议**：
- bHLH 野生型：leave-one-out 交叉验证；
- 突变体：模型仅在野生型数据上训练，预测突变体，与实验比较。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| bHLH 野生型 leave-one-out 交叉验证 | FamilyCode 能预测野生型 TF 的结合特异性 | 与 closest-paralog、similarity regression 比较 | R² = 0.69, RMSD = 0.66；优于 closest-paralog（R² = 0.63, p < 10⁻²⁴）和 similarity regression（R² = 0.58, p < 10⁻³³） | FamilyCode 在野生型预测上优于基线方法 | 未与 DeepPBS 比较 | Results 图 3D |
| ASCL2 突变体预测 | FamilyCode 能预测突变体的结合偏好变化 | 预测 vs SELEX-seq 实验 | R² = 0.94, RMSD = 0.37 | 对偏好 CAGCTG 的 TF，突变预测高度准确 | 仅验证了 4 个突变体 | Results 图 4F |
| HES2 突变体预测 | FamilyCode 能预测突变体的结合偏好变化 | 预测 vs SELEX-seq 实验 | R² = 0.61, RMSD = 1.21 | 预测有一定准确性，但低于 ASCL2 | 野生型 HES2 模型本身可重复性较低（RMSD = 0.61） | Results 图 4G |
| HLH-1 突变体预测（PBM 数据） | FamilyCode 能跨平台预测突变效应 | 预测 vs PBM 实验（Ref 59） | 位置 -1 预测 R² = 0.98, RMSD = 0.19；优于 DeepPBS（R² = 0.33） | FamilyCode 在 PBM 数据上表现优异，显著优于结构方法 | 仅 3 个突变体 | Results 图 S8C, D |
| homeodomain 家族 92 突变体预测 | FamilyCode 在 homeodomain 家族上泛化 | 预测 vs PBM 实验（Ref 30） | 整体 R² 接近实验可重复性上限 | FamilyCode 可推广到 homeodomain 家族 | 预测精度受限于训练数据覆盖度 | Results 图 6D |
| 与 rCLAMPS 比较 | FamilyCode 优于现有序列方法 | 92 个 homeodomain 突变体 | FamilyCode 显著优于 rCLAMPS（p = 0.0057, rank sum test） | FamilyCode 在家族内突变预测上优于 rCLAMPS | rCLAMPS 使用不同训练数据，比较不完全公平 | Results 图 6D |

## 11 结论正确解读
- **任务范围**：仅针对**单点错义突变**对 DNA 结合**特异性**（base preference）的影响，不预测结合亲和力绝对值，也不预测突变对蛋白稳定性或折叠的影响。
- **oracle/真值输入**：训练数据来自野生型 TF 的高通量实验（HT-SELEX/PBM），经 ProBound 推断为 ΔΔG/RT 模型；突变体验证数据来自 SELEX-seq 或 PBM 实验。
- **端到端状态**：非端到端。需要先有 ProBound 推断的野生型结合模型，且需要蛋白序列对齐到 PFAM HMM。
- **算力成本**：极低。线性回归 + PCA，无需 GPU 或深度学习训练。
- **历史数据依赖**：依赖训练集中野生型 TF 的序列多样性和结合数据质量；对训练集中未出现的氨基酸-位置组合，预测依赖 BLOSUM62 近似。
- **模型依赖**：假设结合特异性效应可加（线性），忽略氨基酸间协同效应（epistasis）；假设家族内骨架几何固定。
- **最难情形**：训练集中稀疏覆盖的蛋白位置；突变引入训练集中未出现的氨基酸；需要预测多个位点协同突变时。
- **群体/领域边界**：仅在 bHLH 和 homeodomain 两个家族验证；对其他家族（如锌指、bZIP）的适用性未验证。bZIP 存在替代二聚体构象，本文方法可能不适用（作者在 Discussion 中提及）。
- **不确定性**：预测置信度评分与准确度相关（R² = 0.86），但未给出预测的置信区间。

**有边界的复述**：FamilyCode 能够在 bHLH 和 homeodomain 家族内，仅利用野生型同源 TF 的定量结合数据，以线性回归方式预测单点错义突变引起的 DNA 结合特异性变化（ΔΔΔG/RT），在验证集上达到接近实验可重复性的精度，并显著优于 closest-paralog、rCLAMPS 和 DeepPBS 等基线方法。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 训练集规模有限 | bHLH 家族仅 52 个蛋白，homeodomain 家族 414 个 | 纳入更多物种的 TF 和更多实验平台数据 | Discussion: "The number of TFs in the training set... was several dozen in our study" |
| 可加性假设 | 线性模型忽略氨基酸间协同效应 | 引入非线性模型或考虑位点间交互项 | Discussion: "It would be interesting to leverage the tetrahedron representation to account for such dependence on protein sequence context" |
| 不适用于远距离突变 | 预测多个位点协同突变时精度下降 | 需要开发考虑多位点联合效应的模型 | Discussion: "we expect that the accuracy of the predictions would be significantly lower in those cases" |
| 不适用于 de novo 设计 | 对远离野生型序列的人工 TF 预测不可靠 | 结合结构预测或定向进化数据 | Discussion: "our approach may be less suitable for the de novo engineering of novel TFs" |
| 骨架固定假设 | 忽略突变可能引起的骨架构象变化 | 结合结构预测方法（如 AlphaFold）进行修正 | Discussion: "leveraging structure prediction methods to account for this... may be a valuable extension" |
| 未考虑二聚体构象差异 | bZIP 等家族存在替代二聚体构象 | 需要扩展模型以处理构象多样性 | Discussion: "some TF families such as basic leucine zipper (bZIP) factors are capable of binding to DNA in alternative homodimer configurations" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 验证集规模小 | ASCL2 仅 4 个突变体、HES2 仅 4 个突变体、HLH-1 仅 3 个突变体，统计功效有限 | 高 R² 可能由小样本和特定突变选择造成 | 在更多突变体（如饱和突变扫描）上验证 | Results 图 4F, G; 图 S8 |
| 与基线方法比较的公平性 | rCLAMPS 和 DeepPBS 使用不同训练数据/特征，比较可能不公平 | 影响「优于 SOTA」结论的可靠性 | 在统一 benchmark 上重新训练所有方法 | Results 图 6D |
| 线性可加性假设的合理性 | 蛋白-DNA 结合自由能可能具有非线性协同效应，线性模型可能欠拟合 | 若存在强 epistasis，预测在多位点突变时失效 | 在多位点突变数据上测试；比较非线性模型（如 GBM、神经网络） | Discussion 中作者自认 |
| 四面体表示的信息损失 | 将 4 维频率映射到 3D 空间可能丢失部分信息（虽然理论上等距） | 影响预测精度的上限 | 比较直接对 ΔΔG 回归 vs 四面体回归 | Methods 图 2A |
| 训练数据质量依赖 | ProBound 推断的 ΔΔG/RT 模型质量直接影响 FamilyCode 训练 | 低质量结合模型会传播误差 | 用不同质量阈值的模型进行敏感性分析 | Methods: 质量过滤标准（R² > 0.15） |
| 未与物理模拟方法比较 | 未与 MD、Rosetta 等基于结构的方法在相同数据集上比较 | 无法判断「序列统计」vs「结构物理」路线的优劣 | 在相同突变数据集上运行 Rosetta 或 MD 并比较 | 未提供 |
| 泛化性声明过强 | 仅在两个家族验证，作者声称「general」但证据有限 | 影响方法可信度 | 在更多家族（如锌指、bZIP、核受体）上测试 | Discussion 中作者自认 |
| 未报告预测不确定性 | 置信度评分与准确度相关，但未给出校准的置信区间 | 实际应用中需要知道预测的可靠性 | 用 conformal prediction 或贝叶斯方法校准 | Methods "Assessment of prediction confidence" |

## 14 学到什么
> 标题：Agent 提炼的知识候选

1. **家族级迁移学习策略**：在突变体数据稀缺时，利用同一家族内野生型同源物的天然序列变异作为训练信号，是一种高效且可迁移的范式。可迁移到其他 TF 家族（如锌指、bZIP）或 RNA 结合蛋白。
2. **无参考表示的重要性**：四面体嵌入将 4 碱基偏好映射到无参考的 3D 空间，避免了选择参考碱基的任意性。这一思想可推广到其他多类别偏好问题（如氨基酸偏好、密码子偏好）。
3. **PCA + 迭代特征选择**：在高维稀疏特征（氨基酸身份）下，先用 PCA 降维再逐步回归，能有效避免过拟合并处理共线性。可迁移到其他「序列→功能」回归任务。
4. **结构无关的可行性证明**：本文证明在家族内预测突变效应时，纯序列统计方法可以超越结构方法（DeepPBS）。这提示在结构信息不可靠时，序列层面的统计关联可能更鲁棒。
5. **ΔΔΔG 的稳健估计**：在四面体空间中计算突变效应而非直接相减 ΔΔG，可减少不利碱基估计噪声的影响。这一技巧可迁移到任何基于能量模型的突变效应预测。
6. **跨平台数据整合**：将 HT-SELEX 和 PBM 数据统一到 ΔΔG/RT 框架后可以联合训练，说明不同实验平台的数据在统一物理模型下可互操作。
7. **置信度评分的实用设计**：基于训练数据覆盖度的置信度评分（而非模型不确定性）简单有效，可迁移到其他家族级预测任务。

## 15 与已有知识连接
- **ProBound / PyProBound**（Bussemaker lab 前期工作，Ref 22, 23）：本文直接建立在其上，使用 ProBound 推断 ΔΔG/RT 参数。读者可参考 ProBound 的 biophysical 模型假设（position-independent additive energy）。
- **rCLAMPS**（Ref 48）：基于卷积神经网络的 TF 结合特异性预测器，本文在 homeodomain 突变体上与其比较。rCLAMPS 使用全序列输入，本文使用家族级特征。
- **DeepPBS**（Ref 49）：基于结构的深度学习预测器，本文在 HL-1 突变体上与其比较。DeepPBS 需要蛋白-DNA 复合物结构（AlphaFold3 预测），本文方法无需结构。
- **CisBase / CisBP 数据库**（Ref 57-59）：PBM 数据的来源，包含大量 TF 的 PWM 和原始荧光数据。
- **HT-SELEX 数据**（Ref 16, 33, 34）：Taipale lab 的高通量 SELEX 数据，本文 bHLH 训练集的主要来源。
- **Kock et al. 2022**（Ref 30）：homeodomain 突变体 PBM 数据，本文用于验证。
- **Slattery et al.**（Ref 41）：蛋白表达纯化方案，本文 SELEX 实验参考。
- **与物理模拟的关系**：本文方法不依赖结构，但与 MD/对接方法互补——MD 可提供机制解释，本文提供高通量预测。可考虑将本文预测作为 MD 模拟的初始候选筛选。
- **与 AlphaFold 的关系**：本文在 Discussion 中提及可结合结构预测处理骨架构象变化，但未实现。这是一个明确的未来方向。

## 16 研究想法
> 标题：Agent 生成的研究候选

1. **候选名称**：FamilyCode-3D：结合 AlphaFold 结构特征的家族级突变效应预测
   - **来源局限/观察**：本文方法忽略骨架构象变化，作者自认对 bZIP 等存在替代构象的家族不适用。
   - **核心假设**：将 AlphaFold3 预测的蛋白-DNA 复合物结构特征（如界面残基接触距离、氢键网络）作为额外特征，可提升对骨架敏感突变的预测精度。
   - **初步方法**：在 FamilyCode 的线性回归基础上，加入结构特征作为协变量；对每个突变体，用 AlphaFold3 预测结构，提取界面特征。
   - **验证方式**：在 bZIP 家族突变体数据上测试，与纯序列 FamilyCode 和 DeepPBS 比较。
   - **创新状态**：unverified

2. **候选名称**：TF 突变效应的非线性协同建模：从线性可加到 epistasis 感知
   - **来源局限/观察**：本文线性可加假设忽略氨基酸间协同效应，多位点突变预测可能失效。
   - **核心假设**：引入成对交互项或轻量级非线性模型（如 GBM、带正则化的神经网络），可捕捉 epistasis 效应。
   - **初步方法**：在 FamilyCode 框架中，将单点效应替换为成对效应模型；用 SHAP 值解释交互项。
   - **验证方式**：在多位点突变数据（如深度突变扫描）上比较线性 vs 非线性模型的预测精度。
   - **创新状态**：unverified

3. **候选名称**：跨家族泛化：从 bHLH/Homeodomain 到锌指蛋白的迁移学习
   - **来源局限/观察**：本文仅在两个家族验证，锌指蛋白存在模块化串联结构，与 bHLH/HD 的单域结合模式不同。
   - **核心假设**：FamilyCode 的框架可扩展到锌指蛋白，但需要调整特征编码以处理多锌指协同结合。
   - **初步方法**：将每个锌指模块的序列特征分别编码，再用注意力机制融合；训练数据来自 CisBP 的锌指 PWM。
   - **验证方式**：在锌指突变体数据上测试，与 rCLAMPS 和 DeepPBS 比较。
   - **创新状态**：unverified

4. **候选名称**：从体外到体内：整合 ChIP-seq 数据的家族级突变效应预测
   - **来源局限/观察**：本文仅使用体外数据（HT-SELEX/PBM），未考虑染色质可及性、竞争性结合等体内因素。
   - **核心假设**：将 ChIP-seq 数据（如 Ref 63 ENCODE）纳入训练，可提升对体内突变效应的预测。
   - **初步方法**：用 ProBound 的 peak-agnostic 分析从 ChIP-seq 推断 ΔΔG/RT，与体外数据联合训练 FamilyCode。
   - **验证方式**：在已知致病突变上测试，比较体外-only vs 体外+体内模型的预测精度。
   - **创新状态**：unverified

5. **候选名称**：突变效应的不确定性量化：为临床变异解读提供置信区间
   - **来源局限/观察**：本文给出置信度评分但未校准为概率。
   - **核心假设**：用 conformal prediction 或贝叶斯线性回归，可为每个突变体的 ΔΔΔG/RT 预测提供校准的置信区间。
   - **初步方法**：在 FamilyCode 的回归模型上应用 conformal prediction；在 ClinVar 的 TF 变异上验证区间覆盖率。
   - **验证方式**：比较校准前后区间覆盖率与区间宽度。
   - **创新状态**：unverified