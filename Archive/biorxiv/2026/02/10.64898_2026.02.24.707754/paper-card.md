## 01 基本信息

- **标题**：Estimation of Absolute Protein–DNA Binding Free Energy using Streamlined Geometric Formalism
- **作者**：Shreya Mukherjee; Diship Srivastava; Niladri Patra
- **单位**：Indian Institute of Technology (ISM), Dhanbad（基于致谢中 HPC 集群信息推断，作者单位未在摘要中明确列出）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026-02-26
- **论文类型**：方法学应用研究（计算模拟）
- **领域**：计算生物物理；蛋白质-DNA 互作；结合自由能计算
- **关键词**：绝对结合自由能（ABFE）、几何路线（geometric route）、高斯加速分子动力学（GaMD）、蛋白质-DNA 复合物、PMF
- **DOI/ID**：10.64898/2026.02.24.707754
- **代码**：未提供
- **数据**：未提供（PDB 结构：3QMD、2NBJ、3MKW）
- **阅读日期**：2026-05-13
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 物理模拟」方向，聚焦于利用改进的几何路线（geometric route）结合增强采样（GaWTM-eABF）计算蛋白质-DNA 复合物的**绝对**结合自由能（ABFE），而非相对结合自由能。该方法不依赖机器学习训练数据，而是基于物理原理的 PMF 计算，为 TF-DNA 结合机制研究提供了一种计算成本适中、精度达化学精度（< k_bT）的替代方案。与 AI 方法相比，本文方法不依赖大量实验数据，可迁移至任意大小的蛋白质-DNA 复合物。

---

## 02 一句话总结

本文提出一种精简几何形式（streamlined geometric formalism），通过将高斯加速分子动力学（GaMD）与几何路线结合，仅需 6 个 PMF 模拟即可计算蛋白质-DNA 复合物的绝对结合自由能，在三个测试体系（CFP1-CpG、MC1-DNA、SopB-DNA）上均达到化学精度（与实验值偏差 < 0.6 kcal/mol）。

---

## 03 研究问题

- **具体问题**：如何以适中的计算成本获得蛋白质-DNA 复合物的**绝对**结合自由能（ABFE），并达到化学精度（误差 < k_bT ≈ 0.6 kcal/mol）？
- **为什么重要**：蛋白质-DNA 结合是基因调控、转录、复制等核心生命过程的基础。实验测定结合亲和力成本高、耗时长；计算预测可加速理解 TF-DNA 结合机制、突变效应（如 p53 错义突变导致结合失效）及药物设计。
- **现有方法不足**：
  - 炼金方法（alchemical methods）存在收敛问题，因态间采样不足导致滞后（hysteresis）；
  - 机器学习方法受限于训练数据稀缺；
  - 隐式溶剂和"端点"近似影响精度；
  - 多数研究仅提供**相对**结合自由能，而非绝对结合自由能；
  - 以往研究多使用小 DNA 片段，难以推广至大复合物。
- **精确研究问题**：Can a streamlined geometric formalism (combining GaMD with geometric route) compute the absolute binding free energy of protein-DNA complexes within chemical accuracy (|ΔG_calc − ΔG_exp| < k_bT) at modest computational cost?

---

## 04 背景与发展脉络

*注：以下脉络基于本文摘要及引文构建，部分为「仅本文框架」，已标注。*

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|---------|
| 早期 | 广义 Born（GB）模型（Jayaram et al., EcoRI-DNA） | 计算快 | 精度有限，依赖隐式溶剂近似 | 本文引用为早期工作 |
| 中期 | 拉伸分子动力学（Steered MD, Heesch et al., H-NS-DNA） | 可识别高亲和力共有序列 | 非平衡过程，结果依赖拉动速度 | 本文引用 |
| 近期 | MELD-DNA、多位点 λ 动力学、机器学习方法 | 精度提升 | 收敛问题（炼金）、数据稀缺（ML）、多为相对自由能 | 本文引用为现有方法 |
| **本文** | **精简几何形式（GaMD + 几何路线）** | **绝对自由能、化学精度、仅 6 个 PMF 模拟、不依赖训练数据** | 需验证更大体系；RMSD 简并性可能影响收敛 | **本文主张** |

*注：此脉络主要基于本文摘要中的引文框架，未经外部系统核验，标注为「仅本文框架」。*

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 炼金方法收敛困难 | 态间采样不足导致滞后（hysteresis） | 端点态之间缺乏充分采样 | 摘要：「convergence issues for alchemical methods due to lack of sampling between end states leading to hysteresis」 |
| 机器学习数据稀缺 | 训练数据有限，预测精度受限 | 缺乏足够的蛋白质-DNA 结合亲和力实验数据 | 摘要：「limited data availability for machine learning approaches」 |
| 隐式溶剂/端点近似 | 精度不足 | 隐式溶剂和"end point"近似在结合自由能计算中引入误差 | 摘要：「utilization of implicit solvent and 'end point' approximation during binding energy calculation」 |
| 小 DNA 片段限制 | 难以推广至大蛋白质-DNA 复合物 | 以往研究使用小 DNA 片段 | 摘要：「previous studies involved small sized DNA fragments, translating these studies to large Protein-DNA complex may not be appropriate」 |
| 仅提供相对自由能 | 无法直接与实验绝对亲和力比较 | 多数方法输出相对结合自由能 | 摘要：「The outcome of most of these studies is the relative binding free energy」 |
| 几何路线中 RMSD 简并性 | PMF 估计难以收敛 | RMSD 的简并性质导致 PMF 收敛困难 | 摘要：「due to the degenerate nature of RMSD, the corresponding PMF estimations are hard to converge」 |

---

## 06 核心思想

### 1) 表面方法
采用几何路线（geometric route）计算 ABFE，通过一系列 PMF 计算逐步释放蛋白质-DNA 之间的约束（RMSD、欧拉角、极角/方位角、距离），每个 PMF 沿一个集体变量（CV）进行，前序步骤的 CV 以谐振约束固定在其 PMF 最小值处。共 6 个 PMF 模拟（而非原始几何路线的 14 个）。

### 2) 核心洞察
**将高斯加速分子动力学（GaMD）嵌入几何路线的 PMF 计算中**，利用 GaMD 的遍历采样能力隐式采样结合伙伴的构象空间，从而**消除对 RMSD 约束的需求**（RMSD 的简并性是原始几何路线收敛困难的主因），将独立模拟数从 14 个减少到 6 个，同时保持化学精度。

### 3) 可能的普适教训 [Analysis]
- **增强采样与约束策略的协同**：不是简单地增加采样强度，而是用遍历采样替代特定约束（RMSD），从而规避该约束本身的数学缺陷（简并性）。这种「用更好的采样替代有问题的约束」的思路可迁移至其他自由能计算方法。
- **方法精简而非堆叠**：通过减少模拟数量（14→6）而非增加，反而提升了可操作性和收敛性，说明「少而精」的约束设计优于「多而杂」。
- **对 TF-DNA 研究的启示**：TF 结合 DNA 时通常涉及构象变化（induced fit），GaMD 的遍历采样可有效覆盖这些构象变化，使 ABFE 计算更可靠。

---

## 07 方法总览

- **输入**：蛋白质-DNA 复合物三维结构（PDB: 3QMD、2NBJ、3MKW），力场参数，溶剂环境
- **输出**：绝对结合自由能（ΔG_bind），结合常数（K_b，通过 Equation 4）
- **模块**：
  1. 体系准备与平衡（短时间平衡）
  2. 6 步 PMF 计算（表 1）：
     - Step 1: 欧拉角 Θ 的 PMF（无约束）
     - Step 2-5: 依次对极角 θ、方位角 φ、欧拉角 Φ/Ψ 进行 PMF，前序 CV 以谐振约束固定在其 PMF 最小值
     - Step 6: 沿质心距离 r 的 PMF（分离 PMF）
  3. 使用 GaWTM-eABF（混合高斯加速-良态亚稳态-扩展自适应偏置力）采样方法，通过 Colvar Library 和 NAMD MD 引擎实现
  4. ABFE 计算：通过公式 ΔG_bind = ΔG_Θ + ΔG_θ + ΔG_φ + ΔG_Φ + ΔG_Ψ + ΔG_r + 校正项（I*、S* 分离/表面项）
- **训练**：不涉及（非机器学习方法）
- **反馈回路**：每个 PMF 步骤的约束中心从前一步 PMF 最小值获取，形成顺序依赖链
- **验证**：与实验值比较（表 2），5 个独立重复（各 200 ns）检验可重复性

**文字流程**：
1. 从 PDB 获取复合物结构 → 2. 溶剂化、加离子、平衡 → 3. Step 1: 欧拉角 Θ PMF（无约束）→ 4. 找到 Θ 最小值 → 5. Step 2: 约束 Θ 于最小值，计算 θ PMF → 6. 依次类推完成 φ、Φ、Ψ 的 PMF → 7. Step 6: 约束所有角度，沿 r 计算分离 PMF → 8. 组合各 PMF 贡献 + 校正项 → 9. 得到 ΔG_bind → 10. 与实验值比较验证

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|----------------------|
| GaMD 增强采样 | 隐式采样结合伙伴构象空间，克服 RMSD 简并性 | 原始几何路线因 RMSD 简并难以收敛；GaMD 提供遍历采样 | 输入：体系坐标/力场；输出：加速轨迹 | 摘要：「ergodic sampling algorithm implicitly samples the conformational space...reducing the total number of required independent simulations to six」 | 预期：若无 GaMD，需恢复 RMSD 约束，模拟数回到 14，且收敛困难（作者解释） |
| 6 步顺序 PMF 计算 | 逐步释放约束，计算各自由度自由能贡献 | 将多维自由能分解为可处理的一维 PMF 序列 | 输入：前一步 PMF 最小值；输出：各步骤 ΔG 贡献 | 表 1 流程描述；结果中「terms involving [ΔG_r] and [ΔG_Θ] were the primary contributors」 | 预期：若跳过某步，后续 PMF 的约束中心可能不在真实最小值，导致误差累积（[Analysis]） |
| GaWTM-eABF 采样器 | 执行 PMF 计算的具体采样方法 | 结合 GaMD 加速与 eABF 的自适应偏置，提高 PMF 收敛效率 | 输入：CV 定义、体系坐标；输出：一维 PMF 曲线 | 方法节：「hybrid Gaussian-Accelerated Well-Tempered Metamadynamics-Extended Adaptive Biasing Force sampling method (GaWTM-eABF)」 | 预期：若替换为普通 eABF 或 metadynamics，可能需更长采样时间或收敛更慢（[Analysis]） |
| 角度/距离 CV 定义 | 定义欧拉角、极角、方位角、质心距离 | 描述蛋白质-DNA 相对位置和取向 | 输入：复合物坐标；输出：CV 值轨迹 | 方法节：「Euler angles Θ, Φ, and Ψ...polar and azimuthal angles θ and φ...distance between the center of mass」 | 预期：若 CV 定义不当，PMF 可能无法正确反映结合自由能（[Analysis]） |
| 校正项（I*、S*） | 分离/表面项校正 | 标准浓度校正和表面项对 ABFE 的贡献 | 输入：PMF 结果、体系几何；输出：校正后的 ΔG_bind | 公式：「I* and S* denote the separation and surface term respectively」 | 预期：若忽略，ΔG_bind 可能偏离实验值（[Analysis]） |
| 5×200 ns 重复轨迹 | 可重复性验证 + 分子互作分析 | 确认结果稳定性；分析结合界面互作类型 | 输入：同一体系不同初始条件；输出：ΔG 标准差 + 互作谱 | 结果：「comparable values for the complex's independent replicas indicated that the formalism was reproducible」 | 预期：若重复数少，无法评估方法稳定性（[Analysis]） |

---

## 09 关键公式符号

*注：摘要中公式以图片形式给出，具体符号未在文本中展开，以下基于描述重建。*

**主公式**（ABPE 计算）：

ΔG_bind = ΔG_Θ + ΔG_θ + ΔG_φ + ΔG_Φ + ΔG_Ψ + ΔG_r + k_bT·ln(C°/C) + I* + S*

其中：
- ΔG_Θ, ΔG_θ, ΔG_φ, ΔG_Φ, ΔG_Ψ：各角度自由能贡献（来自对应 PMF）
- ΔG_r：分离 PMF 贡献
- k_b：玻尔兹曼常数
- T：温度
- C°：标准浓度（1 M）
- C：体系浓度
- I*：分离项（separation term）
- S*：表面项（surface term）

**结合常数公式**（Equation 4）：

K_b = exp(−ΔG_bind / k_bT)

**符号说明**：
- CV：集体变量（collective variable）
- PMF：平均力势（potential of mean force）
- RMSD：均方根偏差
- GaMD：高斯加速分子动力学
- GaWTM-eABF：混合高斯加速-良态亚稳态-扩展自适应偏置力

*注：具体公式的完整展开在 Supporting Information (SI) 中，摘要未提供。*

---

## 10 实验设计与证据链

### 数据集/体系
| 体系 | PDB ID | 描述 | 大小 |
|------|--------|------|------|
| CFP1-CpG | 3QMD | CXXC 结构域蛋白 CFP1 结合非甲基化 CpG DNA | 最小 |
| MC1-DNA | 2NBJ | 染色体蛋白 MC1 结合 15 bp DNA | 中等 |
| SopB-DNA | 3MKW | 着丝粒结合蛋白 SopB 结合 18 bp DNA | 最大 |

### 指标
- 化学精度定义：|ΔG_calc − ΔG_exp| < k_bT（≈ 0.6 kcal/mol 在室温）
- 可重复性：5 个独立重复的标准差

### 评测协议
- 每个体系：5 个独立重复，每个 200 ns MD 轨迹
- PMF 计算使用 GaWTM-eABF，Colvar Library + NAMD
- 互作分析使用 ProLIF Python 库

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|----------------|------|
| CFP1-CpG ABPE 计算 | 方法可计算小复合物 ABPE 且达化学精度 | 计算值 vs 实验值 | ΔG = −6.5 ± 1.4 kcal/mol，与实验值偏差 < k_bT | 方法在小体系上有效 | 单一体系不足以证明普适性 | 摘要「Results」段 |
| MC1-DNA ABPE 计算 | 方法可推广至中等大小复合物 | 计算值 vs 实验值 | 与实验值偏差 0.3 kcal/mol | 方法在中等体系上有效 | 仅一个中等体系 | 同上 |
| SopB-DNA ABPE 计算 | 方法可推广至较大复合物 | 计算值 vs 实验值 | 与实验值偏差 0.4 kcal/mol | 方法在较大体系上有效 | 仅一个较大体系 | 同上 |
| 5 重复可重复性 | 结果可重复 | 5 个独立重复 | 各体系重复间值可比（表 S2-S4） | 方法具有可重复性 | 重复数有限（5） | 摘要：「comparable values for the complex's independent replicas」 |
| 能量分解 | 识别主要贡献项 | 各 PMF 项贡献比较 | ΔG_r 和 ΔG_Θ 为主要贡献；角度项边际但必需 | 结合主要由分离能和 Θ 取向决定 | 未提供各体系分解数值 | 摘要：「terms involving [ΔG_r] and [ΔG_Θ] were the primary contributors」 |
| ProLIF 互作分析 | 表征结合界面互作类型 | 3 个体系的 MD 轨迹 | 检测到疏水、vdW、氢键、Pi-阳离子、静电互作 | 互作类型与已知蛋白质-DNA 结合机制一致 | 未提供定量互作强度 | 摘要「Results」段 |

---

## 11 结论正确解读

- **任务范围**：仅测试了 3 个蛋白质-DNA 复合物，均为序列特异性结合。未测试非特异性结合、多结构域蛋白、含辅助因子体系。
- **Oracle/真值输入**：使用实验测定的结合自由能作为真值（具体实验方法未在摘要中说明）。
- **端到端状态**：方法端到端可用（结构 → ABPE），但依赖实验结构（PDB）作为起点，未测试从序列/结构预测出发的流程。
- **算力成本**：摘要声称「modest computational cost」，但未给出具体计算时间或资源需求。
- **历史数据依赖**：不依赖训练数据（非 ML 方法），但依赖力场参数准确性。
- **模型依赖**：依赖 GaWTM-eABF 采样效率、力场精度、PMF 收敛性。
- **最难情形**：未测试构象高度灵活的体系、多亚基复合物、含水介导氢键的体系。
- **群体/领域边界**：仅适用于蛋白质-DNA 体系，未测试蛋白质-RNA（作者在展望中提及）。
- **不确定性**：误差报告为 ±1.4 kcal/mol（CFP1-CpG），其他体系未给出误差范围。

**有边界的复述**：本文方法可在 3 个测试的蛋白质-DNA 复合物上，以 6 个 PMF 模拟的计算成本获得与实验值偏差 < 0.6 kcal/mol 的绝对结合自由能，但该结论仅适用于所测试的体系类型，尚需更大规模验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| 未提供明确的局限声明 | 摘要中未列出「Limitations」章节 | — | 摘要全文 |
| RNA 体系未测试 | RNA 比 DNA 更灵活，方法可能需调整 | 「in future work it would be interesting to evaluate the ABPE of a Protein-RNA complex using the streamlined geometric formalism」 | 摘要末段 |
| 溶剂化方案可改进 | 当前方案在 Step 6 可进一步优化 | 「application of telescopic solvation scheme during Step 6」 | 摘要末段 |
| 多结合位点场景 | 未测试多结合位点蛋白 | 方法可用于多结合位点蛋白，但未验证 | 摘要末段（展望） |

*注：作者未在摘要中明确列出局限性，以上为摘要中可识别的隐含局限与展望。*

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 仅 3 个测试体系 | 样本量小，可能无法代表蛋白质-DNA 互作的多样性（如锌指、亮氨酸拉链、bHLH 等不同 TF 家族） | 方法普适性存疑；TF-DNA 结合机制因家族而异 | 在更多 TF-DNA 体系（不同结构家族、不同 DNA 序列）上测试 | 摘要列出 3 个体系 |
| 化学精度定义宽松 | 以 k_bT（~0.6 kcal/mol）为阈值，但实验误差本身可能 > 0.6 kcal/mol | 若实验值本身不确定，则「化学精度」声明可能过度 | 检查实验方法误差范围；与多个独立实验值比较 | 摘要：「chemical accuracy such that the difference...was less than k_bT」 |
| 未报告计算成本细节 | 「modest computational cost」缺乏量化 | 无法评估方法是否真正可扩展至大型 TF-DNA 复合物 | 要求作者提供计算时间、核心数、墙钟时间 | 摘要：「modest computational cost」 |
| 能量分解仅定性 | 未给出各 PMF 项的数值贡献 | 无法判断哪些自由度对 TF-DNA 结合特异性贡献最大 | 要求补充各体系 PMF 分解数值表 | 摘要：「terms involving [ΔG_r] and [ΔG_Θ] were the primary contributors」 |
| 未讨论力场敏感性 | 不同力场（AMBER、CHARMM）可能给出不同 ABPE | 力场选择影响结果可靠性 | 使用多种力场重复计算 | 摘要未提及力场 |
| 未与 ML 方法对比 | 未与近年 ML 预测结合亲和力的方法（如 DeepBind、DeepSEA 等）比较 | 无法判断该方法相对 AI 方法的优劣 | 在相同测试集上与 ML 方法对比 | 摘要未提及 ML 对比 |
| 互作分析仅描述性 | ProLIF 分析仅列出互作类型，未定量 | 无法将互作强度与结合自由能关联 | 使用 MM-PBSA、能量分解等定量方法 | 摘要：「interactions...were categorized into...」 |

---

## 14 学到什么

**Agent 提炼的知识候选**

| 可迁移知识 | 类型 | 如何迁移至 TF-DNA 结合机制 × AI/物理模拟课题 |
|-----------|------|---------------------------------------------|
| **用遍历采样替代有问题的约束** | 方法论 | 在 TF-DNA 结合自由能计算中，若某约束（如 RMSD）导致收敛困难，可考虑用增强采样（如 GaMD、REMD）隐式覆盖构象空间，而非强行约束。这对研究 TF 结合时的 induced fit 构象变化尤为重要。 |
| **顺序 PMF 分解策略** | 方法论 | 将多维结合自由能分解为角度/距离的一维 PMF 序列，可降低计算维度。可迁移至研究 TF 识别 DNA 序列时的取向偏好（如 TF 如何「搜索」DNA 上的特异位点）。 |
| **化学精度验证标准** | 评估框架 | 以 k_bT 为精度阈值，为 AI 预测 TF-DNA 结合亲和力的模型提供了可操作的精度基准。 |
| **能量分解识别主导项** | 分析框架 | 通过分解各自由度贡献，可识别 TF-DNA 结合中哪些自由度（如取向 vs 距离）主导亲和力，为设计 AI 特征提供物理依据。 |
| **GaWTM-eABF 混合采样** | 技术工具 | 结合多种增强采样方法的思路可迁移至 AI 辅助的 MD 模拟中，提高采样效率。 |
| **多重复验证可重复性** | 实验设计 | 5 个独立重复验证结果稳定性，为 AI 模型训练数据的生成提供质量控制标准。 |
| **从 PDB 结构出发的端到端流程** | 流程设计 | 展示了从实验结构直接计算 ABPE 的流程，可迁移至结合 AlphaFold 预测结构的 TF-DNA 复合物自由能评估。 |

---

## 15 与已有知识连接

- **几何路线方法**：本文引用了几何路线在蛋白质-配体、蛋白质-蛋白质体系中的成功应用（文献 14-17），将其扩展至蛋白质-DNA 体系。这与 TF-DNA 研究中常用的 MM-PBSA、MM-GBSA 等方法形成互补。
- **GaMD 方法**：Miao et al. 开发的高斯加速分子动力学（文献 18-19）已被广泛用于增强采样。本文将其嵌入几何路线，是方法组合创新。
- **MELD-DNA**（文献 10）：基于 MELD 的 DNA 结合预测方法，与本文方法同属物理模拟路线，但 MELD 使用元动力学集成，本文使用顺序 PMF。
- **多位点 λ 动力学**（文献 11）：炼金方法代表，本文指出其收敛问题。
- **机器学习方法**（文献 12）：本文承认 ML 方法的价值但指出数据稀缺限制，与当前 AI 预测 TF-DNA 结合的主流方向形成对照。
- **p53 突变与癌症**：引言中以 p53 为例说明蛋白质-DNA 结合异常与疾病的关系，连接至 TF 突变功能预测的临床意义。
- **ProLIF**（文献 26）：Python 库，用于 MD 轨迹的蛋白质-配体互作分析，可迁移至 TF-DNA 互作指纹分析。
- **[Analysis] 与 AlphaFold 的潜在连接**：本文方法依赖实验结构，但可预期与 AlphaFold3 等结构预测工具结合，实现「预测结构 → 计算 ABPE」的端到端流程，这是 TF-DNA 研究的重要方向。

---

## 16 研究想法

**Agent 生成的研究候选**

### 候选 1：TF-DNA 结合自由能基准数据集构建
- **名称**：TF-DNA-ABPE-Bench
- **来源局限/观察**：本文仅测试 3 个体系，缺乏系统基准；ML 方法受限于数据稀缺
- **核心假设**：利用 streamlined geometric formalism 可系统计算多种 TF 家族（锌指、bHLH、bZIP、homeodomain）与不同 DNA 序列的 ABPE，构建高质量基准数据集
- **初步方法**：选取 20-50 个已知结构的 TF-DNA 复合物，统一力场和协议，计算 ABPE 并与实验值（如 ITC、SPR 数据）对比
- **验证方式**：与实验数据交叉验证；评估不同 TF 家族的计算精度差异
- **创新状态**：unverified

### 候选 2：ML 代理模型加速 ABPE 预测
- **名称**：ABPE-Net
- **来源局限/观察**：本文方法虽比传统炼金方法快，但仍需 6 个 PMF 模拟；ML 方法可即时预测但缺数据
- **核心假设**：以本文方法生成的数据为训练集，训练图神经网络（GNN）或等变网络预测 TF-DNA ABPE，实现近即时预测
- **初步方法**：用候选 1 的数据集训练 GNN，输入为蛋白质-DNA 复合物结构（或 AlphaFold 预测结构），输出为 ABPE；与 MD 计算结果对比
- **验证方式**：留出法测试；与实验值对比；与 MD 计算时间对比
- **创新状态**：unverified

### 候选 3：TF 突变对 ABPE 影响的系统评估
- **名称**：TF-Mut-ABPE
- **来源局限/观察**：引言中 p53 突变导致结合失效是重要临床问题；本文方法可计算 ABPE 但未测试突变效应
- **核心假设**：streamlined geometric formalism 可灵敏捕捉 TF 点突变对 DNA 结合亲和力的影响
- **初步方法**：选取 p53 或其他 TF 的已知致病突变，计算突变体与野生型的 ABPE 差异，与实验结合亲和力变化对比
- **验证方式**：与实验突变数据（如 p53 数据库）对比；评估计算精度是否足以区分致病/非致病突变
- **创新状态**：unverified

### 候选 4：TF-DNA 结合机制的能量分解分析
- **名称**：TF-DNA-Energy-Decomp
- **来源局限/观察**：本文发现 ΔG_r 和 ΔG_Θ 为主要贡献项，但未深入分析不同 TF 家族的差异
- **核心假设**：不同 TF 家族在结合 DNA 时，自由能贡献的主导项不同（如有的以取向熵为主，有的以分离能为主），这反映了不同的识别机制
- **初步方法**：对多个 TF 家族计算各 PMP 项贡献，聚类分析能量指纹，与结构特征（如结合界面大小、弯曲程度）关联
- **验证方式**：统计显著性检验；与已知 TF 结合机制文献对比
- **创新状态**：unverified

### 候选 5：结合位点预测与 ABPE 计算的集成流程
- **名称**：TF-Bind-Scan
- **来源局限/观察**：本文方法需已知复合物结构；实际应用中常需从序列预测结合位点
- **核心假设**：将 AlphaFold3 或 docking 预测的 TF-DNA 复合物结构作为输入，用 streamlined geometric formalism 计算 ABPE，可实现对 TF 候选靶基因的亲和力排序
- **初步方法**：对同一 TF 的多个候选 DNA 序列，预测复合物结构 → 计算 ABPE → 排序；与 ChIP-seq 或 SELEX 数据对比
- **验证方式**：预测的亲和力排序与实验富集分数对比；ROC/AUC 评估
- **创新状态**：unverified

### 候选 6：溶剂化方案改进
- **名称**：Telescopic-Solvation-ABPE
- **来源局限/观察**：作者提出可用 telescopic solvation scheme 改进 Step 6
- **核心假设**：在分离 PMP 阶段采用分层溶剂化（近端原子显式、远端隐式）可提高精度或降低计算成本
- **初步方法**：实现 telescopic solvation 方案，与当前方案对比精度和计算时间
- **验证方式**：在本文 3 个体系上对比；扩展至更多体系
- **创新状态**：unverified（作者提出方向，未实现）