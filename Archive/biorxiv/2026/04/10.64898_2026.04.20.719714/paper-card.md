## 01 基本信息

- **标题**：Retracing and rewriting the evolutionary trajectories of mammalian developmental enhancers
- **作者**：Li T; Lalanne J; Kajiwara EA; Jain S; Li X; Do TV; Martin BK; Regalado SG; Daza RM; Shendure J
- **单位**：未提供（Shendure J 通常关联 University of Washington / Brotman Baty Institute，但原文未提供，不臆断）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026（预印本日期 2026-04-21）
- **论文类型**：预印本（研究论文）
- **领域**：进化基因组学 × 顺式调控元件（enhancer）功能进化 × 深度学习预测 × 大规模平行报告分析（MPRA）
- **关键词**：enhancer evolution, massively parallel reporter assays (MPRA), ancestral reconstruction, deep learning, transcription factor binding sites (TFBS), epistasis, chromatin accessibility
- **DOI/arXiv**：10.64898/2026.04.20.719714
- **代码**：未提供
- **数据**：Zoonomia 1（480 个哺乳动物基因组）、Cactus 2（多序列比对/祖先重建）、MPRA 数据（未提供数据仓库链接）
- **阅读日期**：2026-05-15（假设，按当前日期推算）
- **在「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」方向中的位置**：本文聚焦 enhancer 的进化轨迹，核心机制层面涉及 TFBS 的获得/丢失/重排及其对 enhancer 活性的影响。方法上以深度学习（chromatin accessibility 预测）驱动突变引入策略，属于「AI 指导的 TF–DNA 结合功能编辑」方向，与 TF–DNA 结合机制直接相关（TFBS 是 TF–DNA 互作的功能单元），但未涉及物理模拟（MD/对接）。位置：AI 预测 × 进化功能基因组学 × TFBS 机制解析的交叉点。

---

## 02 一句话总结

本文通过 MPRA 对 5 个小鼠发育 enhancer 的 480 个哺乳动物直系同源/祖先重建序列进行功能测定，结合深度学习预测染色质可及性来指导突变回补，揭示了 enhancer 进化的多种模式、TFBS 变化及顺序依赖的上位效应，并发现模型引导的 enhancer 编辑中「功能丧失易（1–7 个突变）、功能增强难（受活性上限约束）」的不对称性。

---

## 03 研究问题

- **具体问题**：哺乳动物发育 enhancer 在进化过程中如何获得、丢失、维持或改变功能？哪些具体序列变化（尤其是 TFBS 变化）是功能转变的因果驱动？这些变化之间是否存在上位效应（epistasis）？
- **为什么重要**：Enhancer 是发育调控的核心，其进化机制直接关联物种形态多样性与疾病易感性。理解「哪些突变、以什么顺序、在什么背景下改变 enhancer 功能」是连接基因型-表型的关键。
- **现有方法不足**：传统比较基因组学只能识别保守序列，无法直接测量功能；单点突变实验规模有限，无法系统覆盖进化路径；且缺乏对突变间上位效应的系统检测。
- **精确研究问题（Can...?）**：Can we densely map the functional trajectories of enhancer evolution across mammalian phylogeny, and can deep learning-guided mutation reconstitution pinpoint causal TFBS changes and their epistatic interactions?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架及作者引用的经典方法，部分经外部核验（标注）。

1. **比较基因组学时代**：通过序列保守性（如 phyloP, phastCons）识别候选 enhancer。优点：全基因组可扩展；局限：保守≠功能，不保守≠无功能，无法测活性。
2. **MPRA 时代**：大规模平行报告分析（Patwardhan et al. 2012; Melnikov et al. 2012）允许在体外/体内批量测量 enhancer 活性。优点：功能直接可测；局限：通常限于单一物种/单一序列，难以覆盖进化深度。
3. **祖先序列重建 + 功能测定**：如 Zoonomia 联盟（Genereux et al. 2020）提供多物种基因组；Cactus 比对（Armstrong et al. 2020）支持祖先重建。结合 MPRA 可测祖先序列活性。局限：仅测「静态」序列，无法解释功能转变的因果突变。
4. **深度学习预测调控活性**：如 Enformer（Avsec et al. 2021）、Basenji（Kelley et al. 2018）预测染色质可及性/表达。优点：可对任意序列变体做快速预测；局限：预测精度有限，且难以直接指导「如何编辑」。
5. **本文主张的位置**：将上述三者结合——MPRA 提供高密度功能读数，祖先重建提供进化路径，深度学习提供「可及性预测」作为突变引入的指导信号，形成「预测-回补-验证」闭环，首次在核苷酸分辨率上「重写」enhancer 进化轨迹。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 进化功能数据稀疏 | 传统研究仅测少数物种或单一序列，无法覆盖进化深度 | 多物种 MPRA 成本高、通量受限 | Abstract: "densely mapped... 480 extant and ancestrally reconstructed mammalian genomes" |
| 保守性≠功能 | 序列保守的 enhancer 可能功能冗余，序列分歧的 enhancer 可能功能保守 | 进化中功能维持可由不同 TFBS 组合实现（redundancy / turnover） | Abstract: "deep functional conservation despite extensive sequence divergence" |
| 因果突变难以定位 | 功能差异常涉及多个突变，单点实验无法区分因果与伴随变化 | 缺乏系统回补策略 | Abstract: "model-driven reconstitution strategy" |
| 上位效应被忽视 | 突变效应可能依赖背景或引入顺序，传统单突变实验无法检测 | 进化路径上突变顺序影响最终功能 | Abstract: "pervasive context-dependent epistasis... strongly contingent on the order of their introduction" |
| 功能增强难以预测 | 模型引导的编辑中，增强活性受「活性上限」约束 | 可能存在 enhancer 固有的活性天花板（ceiling） | Abstract: "enhancement was constrained by element-specific activity ceilings" |

---

## 06 核心思想

**1) 表面方法**：
- 对 5 个小鼠发育 enhancer，取 480 个哺乳动物直系同源序列 + 祖先重建序列，用 MPRA 测活性。
- 用深度学习（预测染色质可及性）对祖先序列的突变回补进行排序和选择，逐步引入突变，观察活性变化。
- 对现存直系同源序列，用同样策略尝试「功能丧失」和「功能增强」编辑。

**2) 核心洞察**：
- Enhancer 进化不是「保守 vs 分歧」的二元对立，而是多种模式并存（lineage-restricted, deeply conserved, etc.）。
- 功能转变的因果基础是 TFBS 的获得/丢失，但这些变化之间存在强顺序依赖的上位效应——即「先加 A 后加 B」与「先加 B 后加 A」效果不同。
- 模型引导的编辑存在不对称性：破坏功能容易（少突变即可），增强功能难（受活性上限约束）。这暗示 enhancer 在进化中可能已接近其「功能上限」，而功能丧失是更易达成的进化路径。

**3) 可能的普适教训 [Analysis]**：
- 对 TF–DNA 互作研究：TFBS 的「存在与否」不足以预测功能，必须考虑 TFBS 组合的上下文和引入顺序——这提示 TF–DNA 互作是「组合编码」而非「单点编码」。
- 对 AI 引导的基因编辑：预测模型可用于「破坏性编辑」（loss-of-function），但「增益性编辑」（gain-of-function）受限于模型对活性上限的刻画能力——这提示需要显式建模「活性饱和/上限」。
- 对进化模拟：祖先重建 + 功能回补是「实验进化」的可行替代，但需注意重建误差和背景依赖。

---

## 07 方法总览

- **输入**：
  - 5 个小鼠发育 enhancer 的序列（具体基因座未提供）
  - 480 个哺乳动物直系同源序列（Zoonomia）
  - 祖先重建序列（Cactus 比对 + 祖先状态推断）
- **输出**：
  - 每个序列的 MPRA 活性值（enhancer activity）
  - 因果突变位点（TFBS 变化）
  - 突变引入顺序对活性的影响（epistasis 图谱）
  - 功能编辑的最小突变集（loss / gain）
- **模块**：
  1. 直系同源序列收集与比对（Zoonomia + Cactus）
  2. 祖先序列重建
  3. MPRA 文库构建与测定
  4. 深度学习模型（预测染色质可及性）——用于对候选突变进行排序
  5. 突变回补策略（model-driven reconstitution）：在祖先序列上逐步引入突变，每步用 MPRA 验证
  6. 现存序列的功能编辑（loss / gain）
- **训练**：深度学习模型的具体架构、训练数据未提供（推测为已有模型，如 Basenji/Enformer 类，但原文未明确）
- **反馈回路**：MPRA 结果 → 更新突变选择 → 下一轮回补（若存在迭代）；深度学习预测 → 突变排序 → MPRA 验证 → 预测修正（若存在）
- **假设**：
  - 祖先重建序列近似真实祖先状态
  - MPRA 活性反映体内 enhancer 功能（至少部分）
  - 深度学习预测的染色质可及性与 enhancer 活性相关

**文字流程**：
1. 从 Zoonomia 获取 480 个哺乳动物基因组，用 Cactus 比对到小鼠 enhancer 区域，提取直系同源序列。
2. 用 Cactus 的祖先重建模块推断各分支祖先序列。
3. 将所有序列（现存 + 祖先）克隆进 MPRA 报告载体，转染/注射后测定活性。
4. 对每个 enhancer，比较现存/祖先序列的活性差异，定位候选因果突变。
5. 用深度学习模型预测每个候选突变的染色质可及性影响，排序突变引入顺序。
6. 在祖先序列上按预测顺序逐步引入突变，每步 MPRA 验证，记录活性变化轨迹。
7. 对现存序列，用类似策略尝试最小突变集实现功能丧失或增强。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 直系同源序列收集（Zoonomia + Cactus） | 获取 480 个物种的 enhancer 直系同源序列 | 覆盖哺乳动物进化深度，避免单物种偏差 | 输入：小鼠 enhancer 坐标；输出：480 个直系同源序列 | Abstract: "480 extant and ancestrally reconstructed mammalian genomes" | 移除后只能做单/少数物种比较，无法绘制进化轨迹 |
| 祖先序列重建（Cactus） | 推断各进化分支的祖先 enhancer 序列 | 提供「中间态」序列，用于回补实验 | 输入：多序列比对；输出：祖先序列 | Abstract: "ancestrally reconstructed" | 移除后无法区分「祖先状态」与「现存状态」，回补实验失去参照 |
| MPRA 活性测定 | 批量测量所有序列的 enhancer 活性 | 功能读数是所有推断的基础 | 输入：序列文库；输出：每个序列的活性值 | Abstract: "massively parallel reporter assays (MPRAs)" | 移除后只能做序列比较，无法测功能 |
| 深度学习预测（染色质可及性） | 预测突变对可及性的影响，排序突变引入顺序 | 提供「先加哪个突变」的指导，避免穷举所有组合 | 输入：序列；输出：可及性预测分数 | Abstract: "deep learning-based predictions of chromatin accessibility" | 移除后突变引入顺序只能随机/穷举，无法高效定位因果突变 |
| 突变回补策略 | 在祖先序列上逐步引入突变，重建进化轨迹 | 直接测试「哪些突变、什么顺序」驱动功能转变 | 输入：祖先序列 + 候选突变列表；输出：每步的活性值 | Abstract: "re-introduce a succession of mutations into ancestral orthologs" | 移除后只能做「终点比较」，无法检测顺序依赖的上位效应 |
| 功能编辑（loss/gain） | 在现存序列上尝试最小突变集实现功能改变 | 测试模型预测的「可编辑性」及活性上限 | 输入：现存序列；输出：编辑后活性 | Abstract: "ablation... as few as one to seven mutations... enhancement constrained by ceilings" | 移除后无法验证「不对称性」结论 |

**消融效应区分**：
- 实测消融：未提供（本文未做模块消融实验）
- 预期效应：上表「移除后」列均为 [Analysis] 预期，非实测

---

## 09 关键公式符号

不适用。本文为实验驱动 + 深度学习预测，未提供数学模型或公式。深度学习模型的损失函数、架构等未在摘要/正文中披露。

---

## 10 实验设计与证据链

**数据集/群体**：
- 5 个小鼠发育 enhancer（具体基因座未提供）
- 480 个哺乳动物直系同源序列（Zoonomia）
- 祖先重建序列（Cactus）
- 突变回补系列（数量未提供）

**指标**：
- MPRA 活性值（enhancer activity，具体归一化方式未提供）

**基线**：
- 未明确提及基线（推测为小鼠内源 enhancer 活性或随机突变对照，但原文未提供）

**预算/骨干/仪器**：
- 未提供（MPRA 平台细节、测序深度等未披露）

**Oracle 输入**：
- 深度学习模型预测的染色质可及性作为「突变排序」的 oracle 信号

**评测协议**：
- 未提供（MPRA 实验重复数、统计检验方法等未披露）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 480 个直系同源 + 祖先序列 MPRA | Enhancer 功能在进化中呈多种模式 | 跨物种/跨分支活性比较 | 发现 lineage-restricted 到 deep conservation 的多种模式 | Enhancer 进化模式多样，非二元 | 无法推广到所有 enhancer（仅 5 个） | Abstract |
| 深度学习引导的突变回补 | 因果突变可被定位，且存在顺序依赖上位效应 | 不同突变引入顺序的活性比较 | 发现关键 TFBS 变化及顺序依赖效应 | TFBS 变化是功能转变的因果基础，且存在 epistasis | 无法确定所有 enhancer 均如此 | Abstract |
| 现存序列功能编辑（loss） | 功能丧失可由少数突变实现 | 编辑前后活性比较 | 1–7 个突变即可消除活性 | 功能丧失是「易达」的进化路径 | 未测试所有可能突变组合 | Abstract |
| 现存序列功能编辑（gain） | 功能增强可被模型预测并实现 | 编辑前后活性比较 | 增强受活性上限约束 | 存在 element-specific activity ceiling | 未揭示 ceiling 的分子机制 | Abstract |

---

## 11 结论正确解读

- **任务范围**：仅 5 个小鼠发育 enhancer，不能推广到所有 enhancer 或所有物种。
- **Oracle/真值输入**：深度学习预测仅用于「排序突变引入顺序」，最终功能判定依赖 MPRA 实测；预测本身不是真值。
- **端到端状态**：非端到端——深度学习只做可及性预测，不直接预测 enhancer 活性；MPRA 是独立的功能读数。
- **算力成本**：未提供（深度学习模型训练/推理成本未知）。
- **历史数据依赖**：依赖 Zoonomia 基因组质量、Cactus 比对准确性、祖先重建的统计推断可靠性；重建误差可能影响回补实验的起点序列。
- **模型依赖**：深度学习模型的具体架构、训练数据、物种范围未披露，无法评估其泛化性。
- **最难情形**：深度保守但序列高度分歧的 enhancer（"deep functional conservation despite extensive sequence divergence"）——这类情形下序列比对和祖先重建的可靠性存疑。
- **群体/领域边界**：哺乳动物；发育 enhancer；不涵盖非哺乳动物或非发育相关 enhancer。
- **不确定性**：MPRA 的体外/异源环境与体内真实调控的差异未讨论；活性上限的分子机制未阐明。

**有边界的复述**：在 5 个小鼠发育 enhancer 中，通过 480 个哺乳动物直系同源/祖先序列的 MPRA 测定，结合深度学习引导的突变回补，观察到 enhancer 功能进化的多种模式、TFBS 变化的因果作用及顺序依赖的上位效应，并发现功能丧失（1–7 突变）比功能增强（受活性上限约束）更易实现。这些结论限于所测 enhancer 和所用方法，不构成对 enhancer 进化的普遍定律。

---

## 12 作者自认局限

在提供的材料（摘要）中未发现作者明确承认的局限。作者提及的相关约束（非正式局限）：
- 仅 5 个 enhancer（Abstract 中 "five mouse developmental enhancers"），样本量有限。
- 深度学习预测仅用于染色质可及性，而非直接预测 enhancer 活性。
- 活性上限（activity ceiling）的存在被观察到，但机制未解释。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 仅 5 个 enhancer | 样本量小，可能偏向特定进化模式；不同 enhancer 的调控逻辑差异大 | 结论的普适性存疑 | 扩展至更多 enhancer 类型（不同发育阶段、不同组织） | Abstract: "five mouse developmental enhancers" |
| 深度学习预测可及性作为突变排序依据 | 可及性≠活性；预测误差可能引入排序偏差 | 若预测有偏，回补实验的「顺序依赖」结论可能受方法学影响 | 用多个独立预测模型交叉验证，或改用无偏的穷举策略 | Abstract: "deep learning-based predictions of chromatin accessibility" |
| 祖先重建依赖 Cactus 推断 | 重建误差（尤其在高分歧区域）可能使「祖先序列」偏离真实 | 回补实验的起点若不准，因果突变定位可能失真 | 用多种重建算法比较，或对高分歧区域做敏感性分析 | Abstract: "ancestrally reconstructed" |
| MPRA 为体外/异源环境 | 报告基因 assay 可能不反映体内染色质环境、3D 互作 | 功能结论可能高估/低估真实调控效应 | 用体内验证（如 CRISPR 编辑 + 表型）抽查关键结论 | 未提供（方法学常识） |
| 「活性上限」的观察 | 可能是 MPRA 检测动态范围的伪影，而非真实生物学约束 | 若为伪影，「增强难」结论不成立 | 用不同报告系统/不同剂量验证活性上限 | Abstract: "element-specific activity ceilings" |
| 顺序依赖上位效应 | 可能部分源于 MPRA 的随机噪声或文库构建偏差 | 上位效应结论若受噪声影响，因果推断不稳 | 增加重复数、用独立文库验证关键路径 | Abstract: "strongly contingent on the order of their introduction" |

---

## 14 学到什么

**Agent 提炼的知识候选**：

1. **「回补式」进化轨迹重建**：在祖先序列上逐步引入突变并测功能，可直接定位因果突变。可迁移到 TF–DNA 互作研究：对任意 TF–enhancer 对，可用祖先重建 + 逐步回补来解析 TFBS 的获得/丢失如何改变结合亲和力与功能输出。
2. **顺序依赖上位效应的检测框架**：突变引入顺序影响最终功能，提示 TFBS 组合的「语法」（syntax）而非「词汇」（vocabulary）决定 enhancer 活性。可迁移：在 TF–DNA 结合研究中，系统改变 TFBS 排列顺序/间距，检测协同或拮抗效应。
3. **深度学习预测作为突变排序的 oracle**：用可及性预测指导「先测哪些突变」，大幅减少实验组合数。可迁移：对 TF–DNA 结合，可用现有模型（如 DeepSEA、Enformer）预测 TFBS 突变对结合的影响，排序后做湿实验验证。
4. **功能丧失 vs 功能增强的不对称性**：破坏功能易、增强功能难，提示进化中 enhancer 可能已接近功能上限。可迁移：在设计合成 enhancer 或 TF 结合位点工程时，应预期「增强」比「敲除」更难实现，需考虑活性饱和。
5. **深度保守但序列分歧**：功能保守可由不同 TFBS 组合实现（binding site turnover）。可迁移：在 TF–DNA 互作预测中，不能仅依赖序列保守性，需考虑功能等价性（不同位点组合产生相同输出）。

---

## 15 与已有知识连接

- **Zoonomia 联盟**（Genereux et al. 2020, Nature）：240+ 哺乳动物基因组，本文扩展至 480 个，是 Zoonomia 资源的直接应用。
- **Cactus 比对**（Armstrong et al. 2020, Genome Research）：本文用 Cactus 做多序列比对和祖先重建，与 Zoonomia 配套。
- **MPRA 方法**（Patwardhan et al. 2012; Melnikov et al. 2012）：本文的活性测定方法基础。
- **Enhancer 进化研究**：与 Villar et al. 2015（Cell, "Enhancer evolution across 20 mammalian species"）形成对比——Villar 用 20 物种，本文扩展至 480 并加入祖先重建和深度学习引导。
- **深度学习调控预测**：与 Enformer（Avsec et al. 2021, Nature Methods）、Basenji（Kelley et al. 2018）相关，本文将其用于「突变排序」而非直接预测活性。
- **TFBS 进化与 turnover**：与 Arnold et al. 2014（Cell, "Quantitative genome-wide enhancer evolution"）及 Smith et al. 2013 的 binding site turnover 概念一致。
- **上位效应**：与进化生物学中关于适应性景观上位效应的经典文献（如 Weinreich et al. 2006, Science）在概念上呼应，但本文在 enhancer 功能层面检测。

---

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TFBS 组合语法图谱（TFBS Combinatorial Syntax Atlas）
   - **来源局限/观察**：本文发现顺序依赖上位效应，但未系统绘制 TFBS 排列规则。
   - **核心假设**：TFBS 的排列顺序、间距、方向决定 enhancer 活性，且存在可预测的「语法规则」。
   - **增量**：在本文框架上，对同一 enhancer 系统突变 TFBS 顺序/间距，用 MPRA + 深度学习预测建立语法图谱。
   - **初步方法**：选取 5–10 个已知 enhancer，生成 TFBS 重排/间距变异库，MPRA 测定 + 深度学习特征归因。
   - **验证方式**：预测的语法规则在独立 enhancer 集上验证；与已知 TF 协同结合数据（如 ChIP-seq 共定位）交叉验证。
   - **创新状态**：unverified

2. **候选名称**：活性上限的分子机制解析（Molecular Basis of Enhancer Activity Ceiling）
   - **来源局限/观察**：本文观察到增强受活性上限约束，但未解释机制。
   - **核心假设**：活性上限由 TF 可用性、染色质状态或报告系统饱和共同决定，而非 enhancer 序列本身。
   - **增量**：区分「序列固有上限」与「环境依赖上限」。
   - **初步方法**：在不同细胞类型/不同 TF 过表达背景下重复增强实验；用无细胞转录系统排除染色质因素。
   - **验证方式**：若上限随 TF 浓度变化，则支持环境依赖；若不变，则支持序列固有。
   - **创新状态**：unverified

3. **候选名称**：深度学习引导的 TF–DNA 结合编辑（Deep Learning-Guided TF–DNA Binding Editing）
   - **来源局限/观察**：本文用深度学习预测可及性来指导突变排序，但未直接优化 TF 结合。
   - **核心假设**：深度学习模型可预测单个 TFBS 突变对结合亲和力的影响，并指导「最小突变集」实现结合增益/丧失。
   - **增量**：将本文的「enhancer 活性编辑」下沉到「TF–DNA 结合编辑」层面。
   - **初步方法**：用现有模型（DeepSEA/Enformer）对 TFBS 做 in silico 饱和突变，选出预测增益/丧失的突变，用 EMSA/SELEX 验证。
   - **验证方式**：预测与实验结合亲和力变化的相关性；在报告基因中验证功能后果。
   - **创新状态**：partially checked（已有类似工作，但未与进化轨迹结合）

4. **候选名称**：祖先 TFBS 重演实验（Ancestral TFBS Resurrection）
   - **来源局限/观察**：本文重建了祖先 enhancer 序列，但未在蛋白层面重演祖先 TF。
   - **核心假设**：祖先 enhancer 的活性变化部分源于 TF 本身的进化，而非仅 TFBS 变化。
   - **增量**：将 enhancer 进化与 TF 蛋白进化联合分析。
   - **初步方法**：对同一 enhancer 的祖先序列，用祖先重建的 TF 蛋白（如 ChIP-seq 或体外结合）测试结合；比较「祖先 TF + 祖先 enhancer」vs「现代 TF + 祖先 enhancer」。
   - **验证方式**：若祖先 TF 对祖先 enhancer 的结合强于现代 TF，则支持共进化假说。
   - **创新状态**：unverified

5. **候选名称**：跨 enhancer 的进化轨迹泛化性检验（Generalizability of Enhancer Evolutionary Trajectories）
   - **来源局限/观察**：本文仅 5 个 enhancer，结论可能受限于样本。
   - **核心假设**：本文发现的模式（多种进化模式、顺序依赖上位效应、丧失/增强不对称性）在更大规模 enhancer 集合中可复现。
   - **增量**：扩展至数百个 enhancer，建立系统性的进化-功能数据库。
   - **初步方法**：从 ENCODE/FANTOM 选取 100+ 发育 enhancer，用本文流程（Zoonomia + Cactus + MPRA + 深度学习）批量处理。
   - **验证方式**：统计检验各模式在不同 enhancer 类型中的分布；与已知疾病相关变异（GWAS）交叉验证。
   - **创新状态**：unverified