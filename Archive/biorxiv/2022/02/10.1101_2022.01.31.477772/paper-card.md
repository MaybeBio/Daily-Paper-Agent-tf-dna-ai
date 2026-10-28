## 01 基本信息

- **标题**：Learning probabilistic protein-DNA recognition codes from DNA-binding specificities using structural mappings
- **作者与单位**：Joshua L. Wetzel; Kaiqian Zhang; Mona Singh（普林斯顿大学，计算机科学系）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2022-02-01
- **论文类型**：方法学（Method），提出新计算框架
- **领域**：蛋白质-DNA互作（转录因子TF–DNA结合机制）× 概率建模 / 机器学习
- **关键词**：recognition code, transcription factor, DNA-binding specificity, PWM, contact map, Gibbs sampling, homeodomain
- **DOI/arXiv 号**：10.1101/2022.01.31.477772
- **代码**：https://github.com/jlwetzel-slab/rCLAMPS
- **数据**：Cis-BP 2.00（623个野生型homeodomain PWM）、Chu et al. 2012（151个合成homeodomain）、Barrera et al. 2016（30个突变homeodomain）；73个BioLip共晶结构用于构建contact map
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「TF–DNA结合机制 × 概率建模/机器学习」交叉方向，核心创新在于**自动推断TF氨基酸-碱基接触映射**（无需人工标注），并同时学习可解释的线性识别码（recognition code）。与纯结构模拟（MD/对接）不同，本文采用统计学习+结构先验（contact map）的混合路线，对「从大规模PWM数据中逆向推断蛋白-DNA互作机制」具有直接参考价值。

---

## 02 一句话总结

本文提出rCLAMPS框架，利用同一结构家族TF的PWM数据和结构衍生的contact map，通过Gibbs采样**同时推断**每个TF的PWM列到contact map位置的映射（即氨基酸-碱基接触关系）和线性识别码参数，从而实现对未知TF及突变TF的DNA结合特异性预测，在homeodomain家族上达到91%的列级预测准确率。

---

## 03 研究问题

- **具体问题**：对于已知DNA结合特异性（PWM）但缺乏结构信息的转录因子，如何自动推断其氨基酸-碱基接触映射，并学习一个可解释的家族级识别码？
- **为什么重要**：数千个TF的PWM已知，但绝大多数TF的氨基酸-碱基接触界面未知。若能自动推断接触映射，则可：(1) 预测未表征TF的从头特异性；(2) 预测疾病相关TF突变对结合特异性的影响；(3) 揭示蛋白-DNA识别的物理化学决定因素。
- **现有方法不足**：
  - 已有识别码方法（如homeodomain的早期工作）依赖人工标注的接触映射或实验确定的共晶结构，无法扩展到大规模数据；
  - 基于序列比对的方法（如STAMP）仅利用PWM信息，忽略蛋白序列，对多样性大的家族效果差；
  - 深度学习方法（如DeepBind）虽能预测，但缺乏可解释性，无法定位到具体氨基酸-碱基接触。
- **精确研究问题**：Can we simultaneously infer amino acid-to-base contact mappings and a probabilistic recognition code from a corpus of TF-PWM pairs, using only a structural contact map as prior, such that the learned code predicts de novo specificities and mutant-specificity changes accurately?

---

## 04 背景与发展脉络

> 注：以下脉络为「经外部核验」的领域发展概述，结合本文引用与领域常识。

1. **结构生物学阶段（~1990s-2000s）**：通过共晶结构解析少数TF-DNA复合物，人工总结识别码（如POU、homeodomain的Asn50-Ade接触）。代表：Pabo & Nekludova（2000）综述；Luscombe & Thornton（2002）结构分类。局限：仅覆盖少量TF，无法泛化。
2. **统计/机器学习阶段（~2005-2015）**：利用PWM数据库（Cis-BP、JASPAR、UniPROBE）训练预测模型。代表：rf_extant（Christensen et al. 2012，随机森林预测homeodomain特异性）、rf_joint（Chu et al. 2012，加入合成数据）。局限：需要人工对齐PWM、特征选择，且无法推断接触映射。
3. **深度学习方法（~2015-2020）**：DeepBind、DeepSEA等用CNN从序列预测结合。局限：黑箱，无法定位氨基酸-碱基接触，难以解释突变效应。
4. **结构感知的统计学习（本文位置，2022）**：rCLAMPS将结构contact map作为先验，用Gibbs采样自动推断PWM列到结构位置的映射，同时学习线性识别码。优势：无需人工标注、可解释、可迁移到突变预测。与后续工作（如DeepZF、AlphaFold辅助的接触预测）形成互补。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 氨基酸-碱基接触映射未知 | 绝大多数TF的PWM已知，但无法确定PWM的哪一列对应结构中的哪个碱基位置 | 共晶结构仅覆盖少量TF；实验测定接触界面成本高 | Introduction第2段："for the vast majority of TFs for which DNA-binding specificities are known, the specific amino acid-base interactions comprising the underlying interaction interfaces are largely unknown" |
| 已有识别码方法依赖人工标注 | 早期方法需要人工指定接触映射或依赖实验确定的共晶结构 | 人工标注耗时且主观，无法扩展到大规模数据 | Further related work："these approaches to infer recognition codes explicitly incorporate prior knowledge of known DNA-contacting residues or curated protein-DNA interface contact maps" |
| PWM对齐困难 | 同一家族不同TF的PWM长度和位置差异大，难以自动对齐 | 现有对齐工具（如STAMP）仅利用序列信息，忽略蛋白序列，对多样性大的家族效果差 | Results第4节：STAMP在NK-2和Abd-B组上表现差 |
| 突变效应预测缺乏机制 | 无法预测TF突变如何改变结合特异性 | 缺乏氨基酸-碱基接触级别的解析 | Introduction第1段："predicting altered DNA-binding specificities due to mutations or SNPs within TFs" |
| 模型可解释性不足 | 深度学习方法预测准确但无法解释 | 黑箱模型缺乏物理/化学可解释性 | Discussion："the pairwise energetic approximation provided by rCLAMPS allows for statistically interpretable coefficients" |

---

## 06 核心思想

### 1) 表面方法
rCLAMPS是一个概率框架，输入为同一结构家族TF的PWM集合和结构衍生的contact map，通过Gibbs采样交替更新：(a) 每个TF的PWM列到contact map位置的映射（registration）；(b) 线性识别码参数（每个氨基酸-碱基接触对的能量贡献）。

### 2) 核心洞察
**结构先验 + 数据驱动的联合推断**：contact map提供了氨基酸位置与碱基位置之间的候选接触关系（哪些氨基酸可能接触哪些碱基），但具体哪个PWM列对应哪个结构位置是未知的。rCLAMPS的关键洞察是：**通过Gibbs采样在数据中自动推断这个映射**，而不是依赖人工标注。一旦映射确定，识别码参数就可以从大量PWM数据中统计估计。

### 3) 可能的普适教训 [Analysis]
- **结构先验可以显著降低学习难度**：即使结构信息不完整（如仅知道家族级contact map），也能作为强先验引导统计推断，避免从零学习。
- **联合推断优于流水线**：先对齐再学习的流水线会传播对齐错误；联合推断允许映射和识别码参数互相校正。
- **线性模型的可解释性在生物问题中具有独特价值**：虽然非线性模型（如随机森林）可能略优，但线性模型的系数可直接解释为氨基酸-碱基接触的能量贡献，这对机制研究至关重要。

---

## 07 方法总览

- **输入**：
  1. 同一结构家族TF的PWM集合（每个TF一个PWM，4×L矩阵）
  2. 家族级contact map C（从共晶结构推断，定义氨基酸位置i与碱基位置j的候选接触对）
  3. 每个TF的蛋白序列（映射到HMM match states）
- **输出**：
  1. 每个TF的PWM列到contact map位置的映射（registration R）
  2. 识别码参数θ（每个氨基酸-碱基接触对的能量贡献）
  3. 预测的PWM（对未知TF或突变TF）
- **模块**：
  1. **Contact map构建**：从BioLip获取共晶结构，用HMMer映射蛋白位置，定义接触（<3.6Å），计算接触频率矩阵D，阈值化得到contact map C
  2. **概率模型**：每个碱基位置j的碱基概率由Boltzmann分布给出，能量为接触氨基酸的加性贡献
  3. **Gibbs采样**：交替更新每个TF的映射R_p（基于当前θ计算各映射概率）和θ（基于当前映射用多分类逻辑回归估计）
  4. **预测**：对未知TF，用学习到的θ和其氨基酸序列直接计算PWM；对突变TF，仅改变突变位置的氨基酸，其余位置用野生型映射
- **训练**：无监督学习（无标签），通过最大化数据似然进行推断
- **工具**：scikit-learn（逻辑回归）、HMMer、BioLip
- **反馈回路**：Gibbs采样中，映射更新和θ更新交替进行，形成反馈循环
- **假设**：
  1. 同一家族TF的contact map保守（结构同源性）
  2. 结合自由能可加性（线性模型）
  3. 碱基位置间条件独立（给定氨基酸序列）

**文字流程**：
1. 从共晶结构构建家族级contact map C
2. 初始化所有TF的映射R（随机或基于序列相似性）
3. 迭代Gibbs采样：
   a. 固定R，用多分类逻辑回归估计θ
   b. 固定θ，对每个TF采样新的映射R_p（考虑所有可能的偏移和方向）
4. 收敛后，用最终θ和映射进行预测

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Contact map构建 | 从共晶结构推断家族级氨基酸-碱基接触关系 | 提供结构先验，定义哪些氨基酸可能接触哪些碱基 | 输入：73个BioLip共晶结构；输出：contact map C（8个碱基位置，6个核心位置） | Methods 2.2节；阈值t_d=t_e=0.05 | 移除后无法定义候选接触对，模型退化为无结构先验的序列比对 |
| 概率模型（Boltzmann分布） | 将氨基酸序列映射为碱基概率 | 提供物理可解释的生成模型 | 输入：氨基酸序列、θ；输出：PWM | Methods 2.3节公式(1)-(3) | 移除后无法计算似然，Gibbs采样无目标函数 |
| Gibbs采样（映射推断） | 自动推断每个TF的PWM列到contact map位置的映射 | 核心创新点，替代人工标注 | 输入：PWM、θ、contact map；输出：映射R | Methods 2.7节；Results图2 | 移除后需人工标注映射，无法扩展到大规模数据 |
| 多分类逻辑回归（θ估计） | 从映射后的数据估计氨基酸-碱基接触能量 | 提供可解释的识别码参数 | 输入：映射后的PWM数据；输出：θ | Methods 2.5节 | 移除后无法学习识别码，预测退化为直接使用实验PWM |
| 混合预测（transfer） | 对突变TF，仅预测受影响的碱基位置 | 利用野生型信息提高突变预测精度 | 输入：野生型PWM、突变位置；输出：突变PWM | Results图3 | 移除后需完全从头预测，精度下降（文中显示transfer列93% vs de novo 90%） |
| 外部验证（fly映射） | 用实验确定的fly homeodomain映射验证推断的映射 | 验证映射推断的准确性 | 输入：fly PWM、推断映射；输出：一致性比较 | Results图4；97%一致率 | 移除后无法确认映射推断的生物学正确性 |

---

## 09 关键公式符号

**公式1：总自由能（加性模型）**
ΔG = Σ_(i,j)∈C ε(i,j,a_i,b_j)

- ΔG：蛋白-DNA结合总自由能
- C：contact map（氨基酸位置i与碱基位置j的接触对集合）
- ε(i,j,a_i,b_j)：氨基酸a_i在位置i与碱基b_j在位置j的接触能量贡献
- a_i：位置i的氨基酸（20种之一）
- b_j：位置j的碱基（A/C/G/T之一）

**公式2：单碱基位置能量**
ΔG_j = Σ_(i:(i,j)∈C) ε(i,j,a_i,b_j)

- ΔG_j：碱基位置j的总能量贡献
- 求和遍历所有接触位置i

**公式3：Boltzmann分布（碱基概率）**
Pr(B_j = b | A_i = a_i ∀i:(i,j)∈C) = exp(-ΔG_j(b)) / Z_j

- Z_j = Σ_b' exp(-ΔG_j(b'))：配分函数
- 该公式将能量转化为碱基概率，用于计算PWM

**公式4：多分类逻辑回归（θ估计）**
log(Pr(B_j = b) / Pr(B_j = b_0)) = Σ_(i:(i,j)∈C) Σ_a X_{i,j,a,b} · θ_{i,j,a,b}

- b_0：参考碱基
- X_{i,j,a,b}：指示变量（位置i氨基酸是否为a）
- θ_{i,j,a,b}：待估计系数（即ε的估计值）

**用途**：公式1-3定义了生成模型（从氨基酸到PWM），公式4用于从数据中估计参数。Gibbs采样在映射R和参数θ之间交替。

---

## 10 实验设计与证据链

### 数据集与设置
- **训练数据**：623个野生型homeodomain PWM（Cis-BP 2.00）+ 151个合成homeodomain（Chu et al. 2012）+ 30个突变homeodomain（Barrera et al. 2016），共763个（去除缺失后593个用于训练）
- **结构数据**：73个BioLip共晶结构，构建contact map
- **测试集**：141个蛋白（50%合成+全部突变）用于de novo预测评估；88个突变体用于transfer评估
- **指标**：列级PCC（预测PWM与实验PWM的Pearson相关系数），阈值0.5视为"一致"
- **基线**：rf_extant（Christensen et al. 2012）、rf_joint（Chu et al. 2012）
- **评测协议**：留出法（hold-out），确保测试集蛋白与训练集在DNA结合残基组合上不重叠

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| De novo预测（全测试集） | rCLAMPS能预测未见过的TF特异性 | 141个蛋白，rCLAMPS vs rf_extant | rCLAMPS 90%列正确，rf_extant 85% | 自动推断映射+线性模型优于人工对齐+随机森林 | 未与深度学习（如DeepBind）比较 | Results第1节，图2 |
| 分位置预测精度 | 各碱基位置预测精度 | 6个核心位置分别计算 | 位置3（Asn50-Ade接触）精度最高（97%），位置5-6精度较低（86-88%） | 保守接触预测准确，可变接触预测困难 | 未分析精度与接触保守性的定量关系 | Results第1节，图2右 |
| 与rf_joint比较 | 加入合成数据后仍具竞争力 | 77个蛋白（rf_joint训练集外） | 两者均94%列正确 | 线性模型不逊于随机森林 | 测试集小（77个），且仅覆盖16种结合残基组合 | Results第2节 |
| Transfer预测（野生型→突变体） | 利用野生型信息提高突变预测 | 88个突变体，transfer vs de novo | transfer 93% vs de novo 90%列正确 | 接触映射可有效迁移 | 未与实验测定突变体特异性比较 | Results第3节，图3 |
| 外部验证（fly映射） | 推断的映射与实验一致 | 235个fly homeodomain，rCLAMPS vs 实验映射 | 97%（228/235）一致 | 自动推断映射准确 | 仅验证homeodomain家族，未验证其他家族 | Results第4节，图4 |
| 与STAMP比较 | 联合推断优于仅PWM比对 | 235个fly蛋白，rCLAMPS vs STAMP | rCLAMPS 97% vs STAMP 80% | 蛋白序列信息+结构先验优于纯PWM比对 | STAMP非为映射设计，比较不完全公平 | Results第4节，图4 |

---

## 11 结论正确解读

- **任务范围**：本文仅针对homeodomain家族，且仅预测核心6个碱基位置（排除侧翼位置）。结论不能外推到其他TF家族或全长结合位点。
- **Oracle/真值输入**：训练使用实验PWM（Cis-BP等），contact map来自共晶结构。预测时假设TF的DNA结合结构域序列已知且能映射到HMM。
- **端到端状态**：方法端到端可运行（输入序列→输出PWM），但依赖家族级contact map先验，非完全从头预测。
- **算力成本**：Gibbs采样100次运行，计算成本中等（未报告具体时间），远低于MD模拟。
- **历史数据依赖**：依赖PWM数据库的覆盖度和质量；对未表征家族无法应用。
- **模型依赖**：线性加性模型假设可能忽略协同效应（如氨基酸-氨基酸相互作用），对复杂识别机制可能不足。
- **最难情形**：结合位点位置5-6（可变接触区域）预测精度最低（86-88%），说明可变接触的推断仍是挑战。
- **群体/领域边界**：仅验证homeodomain；对锌指、bHLH等其他家族需重新构建contact map。
- **不确定性**：未报告预测PWM的置信区间；Gibbs采样可能陷入局部最优（作者用block sampling缓解）。

**有边界的复述**：rCLAMPS在homeodomain家族上，利用结构先验和PWM数据，能自动推断氨基酸-碱基接触映射并学习线性识别码，实现90%以上的列级预测精度，且能有效预测单氨基酸突变对特异性的影响。该方法的适用前提是：目标TF属于结构已知且接触保守的家族。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 线性模型假设 | 仅考虑加性氨基酸-碱基能量贡献，忽略协同效应 | 扩展为非线性模型（如梯度提升、随机森林） | Discussion第1段："Our linear model... can serve as a jumping off point for training models that account for higher order interactions" |
| 未纳入DNA形状特征 | 未考虑DNA结构变形对识别的影响 | 加入DNA shape信息（基于侧翼序列） | Discussion第2段："extending our model to include DNA shape information... may lead to more accurate predictions" |
| 仅验证homeodomain家族 | 方法通用性未验证 | 应用于其他TF家族 | Discussion第3段："our general approach can be applied to... a diverse set of DNA-binding families" |
| 依赖结构数据 | 需要家族级contact map先验 | 未明确提及 | Methods 2.2节（隐含） |
| 初步探索非线性模型未报告 | 作者提到尝试了梯度提升和随机森林但未展示结果 | 未来优化非线性模型 | Discussion第1段："in a preliminary exploration... we found that they provide subtle improvements" |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| 91%列级精度可能高估 | 测试集与训练集可能共享保守的DNA结合残基组合，导致"记忆"而非"泛化" | 若高估，则方法对新家族或远缘TF的预测能力有限 | 用系统发育距离更远的TF作为测试集；或仅用合成homeodomain测试 | Results第1节：测试集包含合成和突变体，但未报告与训练集的序列相似性分布 |
| 线性模型与随机森林比较不公平 | rf_extant/rf_joint需要人工对齐和特征选择，rCLAMPS自动完成，但比较时未控制预处理差异 | 若预处理差异是主要因素，则核心贡献可能在对齐而非识别码 | 用相同预处理流程重新运行rf_extant | Further related work描述rf_extant需人工对齐 |
| 97%的fly映射一致性可能受选择偏差影响 | 仅比较了235个可映射到fly同源物的TF，可能排除了映射困难的案例 | 若排除的案例映射错误率高，则实际精度更低 | 报告所有593个TF的映射结果，而非仅可验证的子集 | Results第4节：仅235/593可比较 |
| 未与深度学习方法比较 | DeepBind等可能在该任务上表现更好 | 若深度学习方法更优，则rCLAMPS的增量价值需重新评估 | 在相同测试集上运行DeepBind等 | 全文未提及深度学习基线 |
| 突变预测的临床相关性未验证 | 88个突变体来自Barrera et al. 2016，但未与疾病表型关联 | 若突变预测与疾病无关，则临床价值有限 | 与ClinVar或COSMIC中的TF突变关联分析 | Results第3节：仅报告预测精度，未涉及疾病关联 |
| 接触阈值选择敏感 | t_d=t_e=0.05的选择可能影响结果 | 不同阈值可能改变contact map结构，影响识别码 | 进行阈值敏感性分析 | Methods 2.2节：未报告敏感性分析 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **结构先验+统计推断的混合范式**：rCLAMPS展示了如何用粗粒度结构信息（家族级contact map）作为先验，通过统计推断自动细化到具体TF的接触映射。**可迁移到本课题**：对于TF-DNA互作，可尝试用AlphaFold预测的结构或同源建模的contact map作为先验，结合PWM/ChIP-seq数据自动推断结合模式。

2. **Gibbs采样解决"映射未知"问题**：当数据中存在隐变量（如PWM列到结构位置的映射）时，Gibbs采样是有效的推断工具。**可迁移**：在MD模拟或对接中，若初始结合姿态不确定，可类似地用采样方法探索姿态空间。

3. **线性可加模型的解释性价值**：虽然非线性模型可能略优，但线性模型的系数可直接解释为能量贡献。**可迁移**：在构建TF-DNA结合预测模型时，优先考虑可解释的线性/加性模型，便于机制研究。

4. **Transfer策略提升突变预测**：对突变TF，仅预测受影响的碱基位置（而非全序列）可提高精度。**可迁移**：在预测TF突变效应时，利用野生型信息作为先验，只对突变接触位点进行局部预测。

5. **外部验证的重要性**：用独立实验数据（fly映射）验证推断的映射，增强了结果可信度。**可迁移**：在开发新方法时，应寻找独立实验数据（如突变实验、结构数据）验证中间预测（不仅是最终输出）。

6. **数据预处理的关键性**：PWM的归一化、信息量校正（rescaling）对模型性能有显著影响。**可迁移**：在使用公共PWM数据库时，注意不同实验平台间的系统性偏差。

7. **合成数据增强泛化**：加入合成homeodomain（Chu et al. 2012）显著提升了模型对非天然序列的预测能力。**可迁移**：在训练TF-DNA结合模型时，可考虑用合成文库数据增强训练集多样性。

---

## 15 与已有知识连接

- **可核验的外部文献**：
  - **Noyes et al. 2008 (Cell)**：homeodomain结合特异性的系统性实验测定，本文的contact map和PWM数据部分来源于此。
  - **Chu et al. 2012 (Cell)**：合成homeodomain文库，本文用于增强训练数据。
  - **Barrera et al. 2016 (AJHG)**：人类TF突变体结合特异性测定，本文用于验证突变预测。
  - **Persikov & Singh 2014 (NAR)**：基于结构的锌指识别码方法，本文的线性模型思想与之相关。
  - **Jolma et al. 2010, Weirauch et al. 2014 (Cell)**: Cis-BP数据库，本文PWM数据来源。
  - **Luscombe & Thornton 2002 (NAR)**：蛋白-DNA接触的结构分类，本文contact map构建的基础。

- **与用户已有知识的连接**：
  - 若用户熟悉**DeepBind/DeepSEA**：rCLAMPS的线性模型可视为深度模型的可解释替代，但牺牲了部分非线性表达能力。
  - 若用户熟悉**MD模拟**：rCLAMPS的contact map类似于MD中的静态接触图，但用统计学习替代了物理力场计算。
  - 若用户熟悉**AlphaFold**：rCLAMPS的contact map构建可被AlphaFold预测结构替代，实现无实验结构的家族扩展。

- **候选方向（未验证）**：
  - 将rCLAMPS扩展到其他TF家族（如bHLH、bZIP）需要重新构建contact map，可尝试用AlphaFold预测结构自动生成。
  - 与深度学习结合：用rCLAMPS的映射作为中间层，输入到CNN/Transformer中预测更复杂的结合模式。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

**候选1：基于AlphaFold结构的自动contact map构建与跨家族识别码学习**
- **来源局限/观察**：rCLAMPS依赖实验共晶结构构建contact map，限制了其对新家族的应用。
- **核心假设**：AlphaFold预测的TF-DNA复合物结构（或单体结构+DNA对接）可提供足够准确的contact map先验。
- **增量**：将rCLAMPS的contact map构建自动化，扩展到无实验结构的TF家族。
- **初步方法**：用AlphaFold预测TF结构，与DNA进行刚性对接或使用PDNA-3D等工具预测复合物，提取接触对；在多个家族上验证。
- **验证方式**：与实验确定的接触映射比较；预测PWM与实验PWM的PCC。
- **创新状态**：unverified

**候选2：非线性识别码——图神经网络替代线性可加模型**
- **来源局限/观察**：rCLAMPS的线性模型忽略氨基酸-氨基酸协同效应，在可变接触位置（位置5-6）精度较低。
- **核心假设**：图神经网络（GNN）可以捕捉氨基酸-氨基酸-碱基的三体相互作用，提升可变位置预测。
- **增量**：在保持自动映射推断的同时，用GNN替代线性模型。
- **初步方法**：将contact map扩展为图（节点=氨基酸/碱基，边=接触），用GNN预测每个碱基位置的概率分布；与rCLAMPS的Gibbs采样结合。
- **验证方式**：在homeodomain测试集上比较GNN vs 线性模型的列级PCC；分析GNN学到的注意力权重是否对应已知关键接触。
- **创新状态**：unverified

**候选3：突变效应预测的物理约束增强**
- **来源局限/观察**：rCLAMPS的transfer方法仅利用序列相似性，未利用物理化学约束（如电荷、疏水性）。
- **核心假设**：在transfer预测中加入氨基酸理化性质约束（如突变前后电荷变化）可提升突变预测精度。
- **增量**：将rCLAMPS的线性模型扩展为带理化特征的正则化回归。
- **初步方法**：在θ估计中加入氨基酸理化特征（如疏水性、体积、电荷）作为协变量；比较有无理化特征的预测精度。
- **验证方式**：在Barrera et al. 2016的30个突变体上比较；与实验测定的特异性变化相关性。
- **创新状态**：unverified

**候选4：从ChIP-seq到contact map的联合推断**
- **来源局限/观察**：rCLAMPS仅使用PWM数据，未利用基因组结合数据（ChIP-seq）。
- **核心假设**：ChIP-seq数据可提供额外的约束，帮助推断接触映射，特别是对于结合位点侧翼区域。
- **增量**：将ChIP-seq峰序列纳入Gibbs采样的似然函数。
- **初步方法**：对每个TF，用ChIP-seq峰序列计算k-mer富集，作为PWM的补充；在Gibbs采样中联合优化映射和识别码。
- **验证方式**：在ENCODE ChIP-seq数据上验证；比较加入ChIP-seq前后的预测精度。
- **创新状态**：unverified

**候选5：与MD模拟的混合方法——统计识别码指导的增强采样**
- **来源局限/观察**：rCLAMPS的识别码是静态的，未考虑构象变化。
- **核心假设**：rCLAMPS学到的接触映射可作为MD模拟的约束，加速采样并提高结合自由能计算精度。
- **增量**：将统计识别码与物理模拟结合，实现"统计先验+物理精化"。
- **初步方法**：用rCLAMPS的接触映射定义偏置势，在MD模拟中增强采样；比较有无偏置的结合自由能预测。
- **验证方式**：对已知结构的TF-DNA复合物，比较MD预测与实验的结合亲和力。
- **创新状态**：unverified