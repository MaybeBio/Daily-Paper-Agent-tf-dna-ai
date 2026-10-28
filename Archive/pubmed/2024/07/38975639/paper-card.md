## 01 基本信息

- **标题**：iMAX FRET (Information Maximized FRET) for Multipoint Single-Molecule Structural Analysis
- **作者**：Joshi, Bhagyashree S; de Lannoy, Carlos; Howarth, Mark R; Kim, Sung Hyun; Joo, Chirlmin
- **单位**：未提供（根据通讯作者 Joo, Chirlmin 推测为代尔夫特理工大学/梨花女子大学，但原文未明确列出）
- **期刊/平台**：Nano Letters
- **年份**：2024-07-08
- **论文类型**：方法学（Method）论文
- **领域**：单分子生物物理、FRET 成像、结构生物学
- **关键词**：FRET、单分子、三维结构重建、DNA 纳米结构、蛋白质复合物、构象变化
- **DOI/arXiv 号**：10.1021/acs.nanolett.4c00447
- **代码**：未提供
- **数据**：未提供（补充材料中有序列和 Monte Carlo 模拟方法）
- **阅读日期**：2025-01-15（假设）
- **在该课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 物理模拟/结构解析」交叉方向中的**实验方法创新**。它不直接研究 TF-DNA 结合机制，但提供了一种**无需先验结构信息**的单分子多距离测量方案，可为 TF-DNA 复合物的构象动态研究提供实验约束数据，进而与 AlphaFold 等 AI 结构预测方法结合（作者在讨论中明确提及此方向）。


## 02 一句话总结

本文提出 iMAX FRET 方法，利用弱结合 DNA 探针的随机交换，在单分子水平上同时测量多个 FRET 距离，并通过几何建模实现最多四点的三维结构重建，在 DNA 纳米结构、链霉亲和素四聚体和蛋白质构象变化中验证了可行性。


## 03 研究问题

- **具体问题**：如何用简单的双色 FRET 实验，在单分子水平上同时获取多个距离约束，从而实现无需先验结构信息的（ab initio）三维结构重建？
- **为什么重要**：传统 ensemble 结构方法（如晶体学、冷冻电镜）难以捕捉动态构象和异质性；单分子 FRET 虽能提供距离信息，但通常一次只能测一对距离，获取多点结构信息需要多次标记和多次实验，效率低且可能改变样品性质。
- **现有方法不足**：多色 FRET 需要更多染料种类和复杂的光学系统；顺序标记/多次测量耗时且可能引入系统误差；其他单分子结构方法（如 DNA-PAINT 类）需要复杂设备和长时间采集。
- **精确研究问题**：Can a one-pot, two-color FRET measurement with stochastic weak binder exchange provide sufficient distance constraints to reconstruct 3D coordinates of up to four points in a biomolecule without prior structural knowledge?


## 04 背景与发展脉络

*注：以下脉络基于本文引用和作者叙述，标注为「仅本文框架」；未逐一核验外部文献。*

1. **传统 ensemble 结构方法**（晶体学、NMR、冷冻电镜）：提供高分辨率结构，但难以捕捉动态过程、需要大量样品、不适用于异质体系。
2. **单分子 FRET (smFRET)**：可实时监测分子动态和构象变化，但传统 smFRET 一次只能测一对供体-受体距离，多点结构信息获取困难。
3. **多色 FRET 方法**：通过多种染料组合获取多距离，但需要复杂的光学系统、染料选择受限、串扰问题严重。
4. **DNA 杂交成像方法**（如 DNA-PAINT、Exchange-PAINT）：利用 DNA 探针可编程性实现多重标记，但通常需要多次溶液交换或长时间成像。
5. **本文位置**：iMAX FRET 结合了 smFRET 的高灵敏度和 DNA 弱结合探针的随机交换特性，在**单次实验、双色检测**条件下实现多距离同时测量，填补了「简单实验获取多点结构约束」的空白。


## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单分子 FRET 信息量有限 | 一次只能测一对供体-受体距离 | 传统 smFRET 依赖固定标记的一对染料 | Abstract: "only limited structural information could be obtained experimentally" |
| 多距离测量需要复杂方案 | 需要多色染料、多次标记、多次实验 | 多色 FRET 光学复杂；顺序标记耗时且可能改变样品 | Introduction: "other methods for multiple distance observation often require the inclusion and observation of more dye colors, repeated measurements, or multiple sample preparations" |
| 多聚体蛋白难以用传统 FRET 分析 | 无法控制亚基的选择性标记 | 多聚体亚基同源，无法特异性地将供体/受体标记到特定亚基 | Results: "inability to control labeling with donor and acceptor fluorophores of subunits within a multimeric protein" |
| 结构方法需要大量样品或复杂制备 | 晶体学需要结晶、冷冻电镜需要纯化 | 传统方法对样品量和纯度要求高 | Discussion: "With only picomolar-range quantities needed, this approach facilitates the analysis of precious samples" |
| 距离简并性导致结构解析困难 | 多个距离值相近时难以区分 | FRET 值与距离呈非线性关系，相近距离产生相近 FRET 值 | Results: "D1, D2, D4, and D6 generated highly similar FRET values" |


## 06 核心思想

### 1) 表面方法
利用短 ssDNA 作为弱结合探针（imager），与靶分子上标记的互补 docking strand 瞬时杂交。由于结合是瞬时的（dwell time ~1 s），供体和受体标记的 imager 会随机、独立地结合到不同 docking site，从而在单分子水平上产生随机的供体-受体配对，一次实验即可获得所有位点两两之间的距离信息。

### 2) 核心洞察
**随机性即信息**：传统方法试图控制「谁和谁配对」，而 iMAX FRET 反其道而行——让配对随机发生，通过统计大量随机事件来提取所有可能的距离组合。这类似于压缩感知或随机采样思想：不需要逐一测量每个距离对，而是通过大量随机采样一次性获取全部信息。

### 3) 可能的普适教训 [Analysis]
- **「弱相互作用 + 随机采样」可作为通用策略**：在生物分子互作研究中，如果强结合会干扰体系，弱结合 + 高频采样的策略可以最小化扰动同时获取丰富信息。
- **信息论视角**：作者将方法命名为 "Information Maximized"，暗示其核心是最大化单次实验的信息量。这种「信息最大化」思维可迁移到其他实验设计——考虑如何用最少的实验次数获取最多的正交约束。
- **对 TF-DNA 研究的启示**：TF 与 DNA 的结合通常具有序列特异性，但结合亲和力可调。iMAX FRET 的弱结合探针策略可类比为「低亲和力 TF 突变体 + 高频采样」来研究 TF 在 DNA 上的搜索和结合动力学。


## 07 方法总览

- **输入**：靶分子（DNA 纳米结构、蛋白质或多聚体复合物），其上标记有多个 docking strand（ssDNA 序列）；两种 imager（供体标记和受体标记的互补 ssDNA，长度 8-9 nt）
- **输出**：多个位点两两之间的距离集合 → 三维坐标重建
- **核心模块**：
  1. **样品制备**：靶分子表面固定 + docking strand 标记
  2. **随机交换成像**：混合供体/受体 imager（10:1 比例），TIRF 显微镜采集单分子时间轨迹
  3. **事件提取**：从时间轨迹中识别 FRET 事件（供体和受体同时结合）
  4. **距离转换**：FRET 效率 → 距离（基于标准 FRET 公式）
  5. **几何重建**：所有距离对 → 三维坐标（枚举所有可能构型，选择最满足距离约束者）
- **训练**：不涉及传统机器学习训练；但使用 Monte Carlo 模拟优化 imager 浓度和长度配比
- **反馈回路**：Monte Carlo 模拟 → 预测事件频率 → 调整实验参数 → 实验验证
- **假设**：
  - 靶分子在测量期间保持刚性/固定构象
  - docking strand 位置已知（通过标记设计）
  - FRET-距离转换准确（需校准染料特性和连接臂长度）


## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 弱结合 imager 设计 | 实现随机、瞬时的探针结合 | 强结合会导致多个位点同时被占据，无法区分单对 FRET | 输入：docking strand 序列；输出：8-9 nt imager | Results: 8 nt imager dwell time = 1.0 ± 0.1 s | 预期：移除后无法实现随机交换，回到传统固定标记 |
| 供体/受体比例优化 | 最大化单 FRET 事件概率 | 需要保证「一个供体 + 一个受体」同时结合的概率最高 | 输入：浓度比例；输出：10:1 受体:供体 | Results: "10-fold excess of acceptor" | 预期：比例不当会降低有效事件数或增加多受体占据 |
| Monte Carlo 模拟 | 预测最优实验条件 | 实验参数空间大，需理论指导 | 输入：浓度、dwell time、位点数；输出：事件频率预测 | Results: "Using Monte Carlo simulations...across various concentrations and binding dwell times" | 预期：移除后需经验试错，效率降低 |
| FRET 事件提取与平均 | 从原始轨迹提取距离信息 | 单分子轨迹含噪声和随机结合/解离 | 输入：时间轨迹；输出：FRET 效率直方图 | Results: "histogram of the averaged FRET value/event" | 预期：移除后无法量化距离 |
| 几何重建算法 | 从距离集合重建三维坐标 | 距离本身不直接给出结构 | 输入：所有两两距离；输出：三维坐标 | Results: "all possible three-dimensional constructs using these lengths are generated" | 预期：移除后只能获得距离约束，无法得到结构 |
| 机器学习分类器（辅助验证） | 验证重建结构包含可识别信息 | 需要客观评估重建质量 | 输入：三角形坐标的旋转/平移/反射不变嵌入；输出：分类准确率 74% | Results: "trained a tree-based machine learning algorithm...attained an accuracy of 74%" | 预期：移除后仍可重建结构，但缺乏客观验证手段 |


## 09 关键公式符号

本文未提供显式公式，但涉及以下隐含关系：

1. **FRET 效率-距离关系**（标准 Förster 公式，文中未显式给出但为方法基础）：
   \[
   E = \frac{1}{1 + (r/R_0)^6}
   \]
   - \( E \)：FRET 效率
   - \( r \)：供体-受体距离
   - \( R_0 \)：Förster 半径（取决于染料对）

2. **几何重建中的距离约束**（文中描述为算法，未给公式）：
   - 对 N 个点，有 N(N-1)/2 个两两距离
   - 三维空间中 N=4 时，6 个距离足以确定构型（刚性体假设下）
   - 文中提到「30 个不相似四边形」：4 个点的完全图有 6 条边，但三维空间中四边形有 30 种不相似构型（考虑二面角自由度）

3. **Monte Carlo 模拟**（补充方法，未提供具体公式）：
   - 模拟 imager 结合/解离的随机过程
   - 参数：结合速率 \( k_{on} \)、解离速率 \( k_{off} \)、浓度 \( c \)
   - 事件概率与 \( k_{on} \cdot c \cdot \tau_{binding} \) 相关

*注：以上公式为领域标准知识，非原文显式给出。*


## 10 实验设计与证据链

**数据集/群体**：
- DNA 靶标：4 种 ssDNA 构建体，含 2-3 个 docking site
- DNA 纳米结构：四边形 DNA 纳米结构，4 个角各有一个 docking strand
- 蛋白质：链霉亲和素（链霉亲和素）四聚体、二价突变体（1,3 trans 和 1,2 cis）
- 构象变化：Gln PQ 底物结合域（SBD2）蛋白，野生型（可结合配体）和 null 突变体（不结合配体）

**指标**：FRET 效率直方图峰值、重建坐标与已知结构的偏差、分类准确率

**基线**：传统 smFRET（单距离测量）、已知晶体结构（链霉亲和素、SBD2）

**预算/资源**：未提供

**骨干/仪器**：TIRF 显微镜（单分子 FRET 成像）

**Oracle 输入**：已知晶体结构用于验证重建准确性

**评测协议**：将重建坐标与已知结构比对，计算偏差

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| ssDNA 多距离测量 | 随机交换可同时测量多个距离 | 2-3 个 docking site 的 ssDNA 构建体 | 预期 FRET 峰值（0.73、0.21 等）均被观测到 | 随机交换方案可行 | 仅验证了线性分子上的距离，未验证三维构型 | Results 图 S1 |
| 四边形 DNA 纳米结构 | 可重建三维结构 | 4 个 docking site，6 个距离 | 重建出非平面四边形构型 | 可进行三维重建 | 重建精度未与独立方法交叉验证 | Results 图 3 |
| 三角形分类 | 重建结构包含可识别信息 | 4 种三角形类型，ML 分类器 | 74% 准确率 | 重建结构具有判别力 | 74% 非极高，可能受噪声和简并性影响 | Results 图 3d |
| 链霉亲和素二价突变体 | 可测量多聚体蛋白中特定位点距离 | 1,3 trans（预期中 FRET）vs 1,2 cis（预期高 FRET） | 0.56 vs 0.89，符合预期 | 可定位配体结合口袋 | 仅验证了二价体系，四价体系存在简并 | Results 图 4a-b |
| 链霉亲和素四聚体 | 可解析四聚体中多个结合口袋 | 野生型四聚体 | 三个 FRET 峰（0.28、0.58、0.94） | 可区分四聚体中的不同距离 | 峰分配依赖对称性假设 | Results 图 4c |
| SBD2 构象变化 | 可检测配体诱导的构象变化 | 野生型 + 谷氨酰胺 vs null 突变体 | FRET 从 0.31 升至 0.45（谷氨酰胺）或 0.34（天冬酰胺） | 可检测配体诱导的构象变化 | 仅一个标记位点对，未全面表征构象变化 | Results 图 5c-d |


## 11 结论正确解读

- **任务范围**：本文验证了 iMAX FRET 在**最多 4 个点**的三维重建能力，对象为 DNA 纳米结构、链霉亲和素和 SBD2 蛋白。未在更大体系（>4 点）或天然 TF-DNA 复合物上验证。
- **Oracle/真值输入**：重建验证依赖已知晶体结构（链霉亲和素、SBD2）和 DNA 纳米结构的设计参数。对于未知结构，重建精度无法独立验证。
- **端到端状态**：方法已实现从原始 FRET 轨迹到三维坐标的完整流程，但几何重建算法需要枚举所有可能构型，计算复杂度随点数增加而急剧上升。
- **算力成本**：未提供具体计算资源信息；几何重建和 Monte Carlo 模拟的计算成本未量化。
- **历史数据依赖**：不依赖历史训练数据；但 Monte Carlo 模拟需要准确的动力学参数（结合/解离速率）。
- **模型依赖**：FRET-距离转换依赖 Förster 半径的准确性；几何重建依赖刚性体假设。
- **最难情形**：距离简并（多个距离产生相似 FRET 值）、柔性体系（不满足刚性假设）、标记位点过多导致事件组合爆炸。
- **群体/领域边界**：适用于体外单分子实验；不适用于活细胞或需要高时间分辨率的快速动态过程。
- **不确定性**：FRET 效率的测量误差未系统量化；重建坐标的置信区间仅在链霉亲和素实验中通过 bootstrap 评估（SD 2.75 Å）。

**有边界的复述**：iMAX FRET 能在体外单分子条件下，通过双色 FRET 和弱结合 DNA 探针的随机交换，在数分钟内获取最多 4 个标记点的距离约束并重建三维坐标，在刚性 DNA 纳米结构和多聚体蛋白上验证了可行性，但尚未在柔性体系或天然 TF-DNA 复合物上验证。


## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 适用距离范围有限 | FRET 可检测距离受 Förster 半径限制 | 使用不同 FRET 对（如 Cy2-Cy3 或 Cy5-Cy7）覆盖更短或更长距离 | Discussion: "the range of distances can also be covered by using different FRET pairs" |
| DNA 标记可能改变蛋白质结构/活性 | DNA 偶联可能诱导结构改变 | 需进行功能实验确认标记后活性保持 | Discussion: "DNA conjugation to proteins may induce structural alterations...a functional assay should be performed" |
| 复杂/大体系分析困难 | 过多标记点导致距离简并和计算复杂度增加 | 迭代多轮测量，利用探针可编程性 | Discussion: "certain challenging scenarios...may be analyzed over iterative rounds of measurements" |
| 需要已知结构指导标记设计 | 标记位点选择需基于已有结构信息 | 未明确提及 | Discussion: "a rational design strategy for positioning DNA strands on exposed surface of the biomolecules guided by the known structures may be necessary" |


## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 4 点重建依赖刚性假设 | 实际蛋白质/DNA 复合物可能具有柔性，重建坐标可能只是平均构象 | TF-DNA 复合物通常具有构象动态性，刚性假设可能掩盖关键动态信息 | 在已知柔性体系（如 intrinsically disordered proteins）上测试重建精度 | 作者在讨论中承认 iMAX FRET 目前适用于刚性体系 |
| 距离简并问题未系统讨论 | 当多个距离产生相似 FRET 值时，峰分配可能出错 | 在复杂体系中，简并可能导致错误的结构推断 | 系统改变标记位置，检验重建稳定性 | Results 中 D1/D2/D4/D6 的 FRET 值高度相似（0.30-0.45），峰分配存在主观性 |
| 74% 分类准确率并非极高 | 可能反映重建结构中的噪声或信息损失 | 如果重建精度不足，结构推断可能不可靠 | 增加标记点数量或重复测量，检验分类准确率是否提升 | Results 图 3d |
| 未与独立结构验证方法交叉验证 | 重建坐标仅与已知结构「符合良好」，但未给出定量误差 | 无法评估方法在未知结构上的可靠性 | 对同一体系使用 cryo-EM 或 SAXS 独立验证 | Results 图 4e 仅给出 bootstrap SD |
| 链霉亲和素四聚体的峰分配依赖对称性假设 | 如果四聚体不对称，峰分配可能错误 | 多聚体蛋白通常具有对称性，但突变或修饰可能破坏对称性 | 使用不对称突变体检验峰分配 | Results 图 4c 中三个峰被分配给三对距离，但未验证对称性假设 |


## 14 学到什么

**Agent 提炼的知识候选**

1. **弱结合探针 + 随机采样策略**：在 TF-DNA 互作研究中，可设计弱结合的 TF 突变体或弱亲和力 DNA 序列，通过高频随机结合事件来同时探测多个 DNA 位点的占据状态，从而获取 TF 在 DNA 上的搜索轨迹和结合偏好。
   - 迁移方式：将 iMAX FRET 的 imager 概念替换为荧光标记的 TF 突变体，docking strand 替换为 DNA 上不同位置的特定序列。

2. **信息最大化实验设计**：核心思想是「一次实验获取最大正交信息」，而非逐步测量。对 TF-DNA 研究，可设计多色或多次 FRET 实验来同时获取 TF 结合位点、构象变化和化学计量信息。

3. **几何重建 + 机器学习验证**：作者用旋转/平移/反射不变嵌入 + 树模型分类来验证重建结构的信息含量。此策略可迁移到 TF-DNA 复合物结构验证——将重建坐标编码为不变特征，训练分类器区分不同构象状态。

4. **Monte Carlo 模拟指导实验参数**：在复杂互作体系中，先模拟再实验可大幅减少试错成本。对 TF-DNA 结合动力学研究，可先模拟 TF 浓度、结合速率和 dwell time 对 FRET 事件频率的影响，再优化实验条件。

5. **多聚体蛋白的对称性利用**：链霉亲和素实验中，作者利用四聚体的对称性简化了峰分配。对 TF 二聚体/四聚体与 DNA 的互作研究，可利用已知对称性来减少需要测量的距离数量。

6. **距离简并的应对**：当多个距离产生相似 FRET 值时，作者通过增加标记点或改变染料位置来区分。对 TF-DNA 复合物，可通过在 TF 和 DNA 上多个位置标记来打破简并。


## 15 与已有知识连接

- **smFRET 领域**：本文建立在传统 smFRET 基础上，与 Förster 共振能量转移理论直接相关。可连接至 Ha et al. (1996) 的早期 smFRET 工作，以及近期多色 FRET 方法（如 3-color FRET）。
- **DNA-PAINT / Exchange-PAINT**：本文的随机交换策略与 DNA-PAINT 成像（Jungmann et al., 2014）有概念相似性，但 iMAX FRET 用于距离测量而非超分辨成像。
- **AlphaFold 整合**：作者在讨论中明确提到 iMAX FRET 的距离约束可整合到 AlphaFold 预测中（参考 AlphaFold 的 distance restraint 功能），这与蛋白质-DNA 复合物结构预测直接相关。
- **转录因子研究**：作者提到 iMAX FRET 可用于转录因子等难结晶蛋白的结构分析。可连接至 TF-DNA 复合物的结构生物学研究（如 p53、NF-κB 等），以及 TF 构象动态与功能调控的关系。
- **单分子动态结构研究**：与 smFRET 探测蛋白质构象变化的工作（如酶催化动态、分子马达步进）相关，本文扩展了 smFRET 从单距离到多距离的维度。
- **[Analysis] 候选连接**：iMAX FRET 的多点距离约束可作为 MD 模拟的输入约束（类似 SAXS 或 FRET 约束的 MD），用于 TF-DNA 复合物的构象采样和动态模拟。


## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：TF-DNA 复合物的 iMAX FRET 构象动态分析
   - **来源局限/观察**：本文未在天然 TF-DNA 复合物上验证；TF 通常具有柔性 DNA 结合域，刚性假设可能不适用
   - **核心假设**：iMAX FRET 可捕捉 TF 结合 DNA 时的构象变化，且多点距离约束可区分不同结合状态
   - **增量**：将 iMAX FRET 从刚性体系扩展到柔性 TF-DNA 复合物；提供 TF 构象动态的实验约束
   - **初步方法**：选择已知结构的 TF（如 p53），在 DNA 结合域和 DNA 上标记 docking strand，测量配体/共因子结合前后的距离变化
   - **验证方式**：与已知晶体结构比对；用 MD 模拟验证重建构象的合理性
   - **创新状态**：unverified

2. **候选名称**：iMAX FRET 约束的 TF-DNA 复合物 MD 模拟
   - **来源局限/观察**：作者提到 iMAX FRET 距离约束可整合到 AlphaFold，但未提及 MD 模拟
   - **核心假设**：将 iMAX FRET 多点距离作为 MD 模拟的约束，可提高 TF-DNA 复合物构象采样的准确性
   - **增量**：建立实验-模拟整合流程，将 FRET 距离约束嵌入 MD 力场
   - **初步方法**：在 AMBER/OpenMM 中实现距离约束；对已知 TF-DNA 复合物进行约束 MD，比较与无约束 MD 的构象分布差异
   - **验证方式**：约束 MD 生成的构象是否与实验 FRET 数据一致；是否比无约束 MD 更好地重现已知结构
   - **创新状态**：unverified

3. **候选名称**：基于 iMAX FRET 的 TF 二聚体结合化学计量分析
   - **来源局限/观察**：本文展示了多聚体蛋白（链霉亲和素）的距离测量，但未涉及结合化学计量
   - **核心假设**：通过 iMAX FRET 的多点距离模式，可区分 TF 以单体、同源二聚体或异源二聚体形式结合 DNA
   - **增量**：将 iMAX FRET 从结构测量扩展到化学计量分析
   - **初步方法**：在 TF 二聚化界面两侧标记 docking strand，测量不同浓度下的距离分布；结合 Monte Carlo 模拟预测不同化学计量下的 FRET 模式
   - **验证方式**：与已知二聚化倾向的 TF（如 bZIP 家族）比较；用荧光相关光谱（FCS）独立验证化学计量
   - **创新状态**：unverified

4. **候选名称**：iMAX FRET 与 AlphaFold 整合的 TF-DNA 复合物结构预测
   - **来源局限/观察**：作者在讨论中提出此方向但未实施
   - **核心假设**：iMAX FRET 距离约束可显著提高 AlphaFold 对 TF-DNA 复合物（尤其是柔性区域）的预测精度
   - **增量**：实现实验约束到 AlphaFold 的输入管道；系统评估不同数量/质量的 FRET 约束对预测精度的影响
   - **初步方法**：对已知 TF-DNA 复合物，从 iMAX FRET 模拟数据生成距离约束，输入 AlphaFold 的 restraint 模块；比较有无约束的预测精度
   - **验证方式**：预测结构与晶体结构/冷冻电镜结构的 RMSD 比较
   - **创新状态**：unverified

5. **候选名称**：单分子水平 TF-DNA 结合动力学的 iMAX FRET 分析
   - **来源局限/观察**：本文聚焦静态结构重建，未利用时间信息
   - **核心假设**：iMAX FRET 的随机结合事件时间轨迹包含 TF-DNA 结合/解离动力学信息
   - **增量**：从结构测量扩展到动力学测量，提供 TF 在 DNA 上搜索和结合的实时信息
   - **初步方法**：分析 FRET 事件的 dwell time 分布和转移速率；与表面等离子共振（SPR）或生物层干涉（BLI）的 ensemble 动力学数据比较
   - **验证方式**：动力学参数与已知 TF-DNA 结合速率常数比较
   - **创新状态**：unverified