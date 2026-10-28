## 01 基本信息

- **标题**：Mammalian conservation of endogenous G-quadruplex reveals their associations with complex traits
- **作者与单位**：Zhang, Ze-Hao; Wang, Zi-Yan; Li, Cong-Hui; Qian, Sheng Hu; Zhang, Wen; Zhang, Zhen-Xia（通讯作者，单位未在摘要中提供）
- **期刊/预印本平台**：Genome Biology
- **年份**：2025-09-02
- **论文类型**：研究论文（Research article）
- **领域**：基因组学、表观遗传学、计算生物学
- **关键词**：G-quadruplex、进化保守性、调控元件、复杂性状、GWAS、eQTL、DNA 结构
- **DOI/arXiv 号**：10.1186/s13059-025-03750-z
- **代码**：未提供
- **数据**：EndoQuad 数据库（eG4 数据库，覆盖 41 个人类细胞系）；G4 CUT&Tag 数据（7 个人类细胞系、2 个小鼠细胞系、2 个猪细胞系）；Zoonomia 241 哺乳动物基因组比对；GWAS Catalog；GTEx v10 eQTL；1000 Genomes Project；NIH Roadmap Epigenomics；GTRD TFBS 数据库
- **阅读日期**：2026-05-13
- **在课题方向中的位置**：本文聚焦 DNA G-quadruplex（G4）这一非 B 型 DNA 结构，而非经典 TF–DNA 序列基序互作。但其核心发现——高保守 eG4 富集于启动子/增强子区域、作为 TF 结合 hub、与复杂性状关联——为「TF–DNA 互作」课题提供了重要的结构层面补充视角。其 eG4finder 工具（基于 DNABERT-2 大语言模型）展示了将预训练基因组基础模型用于 DNA 结构元件预测的可行路径，可直接迁移到 TF 结合位点预测或 TF–DNA 互作建模。

## 02 一句话总结

本文整合 EndoQuad 数据库与自产 G4 CUT&Tag 数据构建人类 eG4 参考集，利用 Zoonomia 241 哺乳动物基因组比对将 eG4 分为高保守、活跃进化、灵长类特异三类，发现高保守 eG4 富集于启动子、具有更高染色质可及性、更强的 TF 结合亲和力与转录激活能力，且其内的 GWAS 变异富集度最高，表明高保守 eG4 是驱动复杂性状的重要调控元件。

## 03 研究问题

- **具体问题**：人类内源 G-quadruplex（eG4）在哺乳动物进化中的保守性图谱如何？不同保守程度的 eG4 在调控功能（染色质状态、TF 结合、转录活性）和复杂性状关联上是否存在系统性差异？
- **为什么重要**：eG4 已被证实是基因表达的关键调控元件，但此前缺乏对其进化保守性的系统刻画。进化保守性是判断功能相关性的黄金标准——若某 eG4 在哺乳动物中高度保守，则其很可能承受纯化选择、具有重要功能。将保守性与复杂性状关联结合，可优先锁定真正有因果潜力的 eG4 变异。
- **精确研究问题**：Can evolutionary conservation of human eG4s across mammals predict their regulatory potential, TF-binding affinity, and association with complex human traits?

## 04 背景与发展脉络

**注：以下脉络基于本文框架，未经外部系统核验。**

1. **G4 检测技术的演进**：早期基于序列基序（如 G3+N1-7G3+N1-7G3+N1-7G3）的预测工具（如 Quadruplex Finder）→ 体外 G4-seq（在 G4 稳定条件下检测全基因组体外 G4）→ 体内抗体-based 方法（G4 ChIP-seq、G4 CUT&Tag，使用 BG4 结构特异性抗体）。本文使用 G4 CUT&Tag，信噪比和分辨率优于 ChIP-seq。
2. **eG4 功能认识的深化**：从「基因组中的结构噪音」→「启动子区域富集的调控元件」→「TF 结合 hub」→「与疾病相关的功能性变异载体」。本文进一步将 eG4 置于进化框架下，区分不同保守层级的调控贡献。
3. **进化保守性分析方法的成熟**：Zoonomia 联盟提供 241 哺乳动物无参考基因组比对（reference-free alignment），使非编码元件的跨物种保守性量化成为可能。此前类似方法已用于候选 cis-调控元件（cCREs）和 TF 结合位点的保守性研究。
4. **深度学习在 G4 预测中的应用**：已有工具如 DeepG4、G4Beacon 使用 CNN/RNN 预测特定细胞类型的 eG4。本文的 eG4finder 首次将 DNA 基础模型（DNABERT-2）用于 eG4 预测，并输出连续值（recurrence）而非二分类，更精细地刻画 eG4 形成潜力。

**本文主张的位置**：首次将「人类 eG4 综合参考集」与「哺乳动物进化保守性」结合，建立 eG4 的三分类进化框架（高保守/活跃进化/灵长类特异），并系统证明保守性层级与调控功能、复杂性状关联的梯度关系。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| eG4 参考注释不完整 | 单一数据库或单一细胞系无法覆盖全部 eG4；不同研究间 eG4 集合差异大 | 不同细胞类型 eG4 高度特异；已有数据库（如 EndoQuad）虽覆盖 41 个细胞系但可能未饱和 | Results 节：作者整合 EndoQuad 与自产 7 个细胞系 G4 CUT&Tag 数据，发现新细胞系中 91.2%-95.5% 的 eG4 已在 EndoQuad 中注释，证明 EndoQuad 接近饱和 |
| 非人哺乳动物 eG4 数据缺乏 | 无法直接验证人类 eG4 在其它物种中的结构保守性 | G4 CUT&Tag/ChIP-seq 仅在人类细胞系中大规模开展；其它物种数据稀少 | Results 节：作者开发 eG4finder 以预测非人物种的 eG4，弥补实验数据缺失 |
| 现有 G4 预测工具无法泛化到跨物种 | 已有工具（DeepG4、G4Beacon）针对特定人类细胞类型训练，依赖染色质可及性等特征，无法直接用于其它物种 | 这些工具需要 ATAC-seq 等额外输入，而非人物种缺乏对应数据 | Results 节：eG4finder 仅基于 DNA 序列即可预测，无需染色质数据，可泛化到任意物种 |
| 进化保守性与功能关联缺乏系统验证 | 已知 eG4 有调控功能，但不知道「保守的 eG4」是否比「新近起源的 eG4」功能更强 | 此前无哺乳动物尺度的 eG4 保守性图谱 | Results 节：作者系统比较三类 eG4 的染色质状态、TF 结合、转录活性、变异富集度，建立保守性-功能梯度 |
| 复杂性状关联的调控元件定位困难 | GWAS 变异大多位于非编码区，难以判断哪些变异通过影响 DNA 结构（而非序列基序）发挥作用 | 传统分析聚焦序列基序（如 TF 结合基序），忽略 DNA 结构元件 | Results 节：高保守 eG4 中 GWAS 变异富集度最高，且 eQTL 富集模式与基因保守性相关 |

## 06 核心思想

### 1) 表面方法

- 整合 EndoQuad（41 个人类细胞系）与自产 G4 CUT&Tag（7 个人类细胞系）数据，构建人类 eG4 综合参考集（404,538 个 eG4）。
- 利用 Zoonomia 241 哺乳动物无参考比对，计算每个 eG4 在 240 个非人物种中的碱基比对率（base alignment rate），据此将 eG4 分为三类：高保守（C1）、活跃进化（C2）、灵长类特异（C3）。
- 开发 eG4finder：基于 DNABERT-2 大语言模型 + 3 层 MLP，仅用 DNA 序列预测 eG4 recurrence（在多少细胞系中形成 eG4），无需染色质数据。
- 用 eG4finder 预测 6 个非人物种（黑猩猩、猕猴、兔、小鼠、大鼠、猪）的全基因组 eG4，验证人类 eG4 的结构保守性。
- 整合功能基因组学数据（ATAC-seq、DNase-seq、ChIP-seq 组蛋白修饰、GTRD TF 结合位点、DNA 甲基化）和遗传学数据（GWAS Catalog、GTEx eQTL），比较三类 eG4 的调控功能与复杂性状关联。

### 2) 核心洞察

- **进化保守性可作为 eG4 功能重要性的排序指标**：高保守 eG4 在染色质可及性、TF 结合多样性、转录激活能力上均显著高于活跃进化和灵长类特异的 eG4，形成清晰的梯度。
- **eG4 的保守性不仅体现在序列层面，还体现在结构层面**：即使序列不完全保守，高保守 eG4 在其它物种中仍更可能形成 G4 结构（通过 eG4finder 验证），说明选择压力作用于结构而非单纯序列。
- **eG4 是 TF 结合的非经典平台**：高保守 eG4 结合更多样的 TF，且这种结合不依赖经典序列基序，而是通过 DNA 二级结构实现——这对 TF–DNA 互作的传统基序范式构成补充。
- **高保守 eG4 是复杂性状变异的富集热点**：GWAS 变异在高保守 eG4 中富集度最高，且 eQTL 对高保守基因表达的影响更强，提示 eG4 结构变异可能是复杂性状的因果机制之一。

### 3) 可能的普适教训 [Analysis]

- **「保守性分层」是功能基因组元件的通用排序策略**：面对海量候选调控元件，进化保守性可提供独立于实验数据的先验排序，优先聚焦最可能具有因果功能的子集。此思路可直接迁移到 TF 结合位点的跨物种保守性分析。
- **结构元件（而非仅序列基序）应纳入调控基因组学的分析框架**：本文证明 DNA 二级结构（G4）是 TF 结合的独立平台，提示 TF–DNA 互作研究不能仅关注线性基序，还需考虑结构态。
- **基础模型（如 DNABERT-2）可有效编码 DNA 结构形成倾向**：仅用序列即可预测 eG4 形成，说明预训练基因组模型隐式学习了结构决定因素，这为缺乏实验数据的物种提供了可迁移的预测工具。

## 07 方法总览

- **输入**：
  - 人类基因组（GRCh38）中所有 PQS（putative quadruplex sequences，来自 EndoQuad）
  - EndoQuad 数据库（41 个人类细胞系的 eG4 注释）
  - 自产 G4 CUT&Tag 数据（7 个人类细胞系：HT29, HCT116, NCM460, SW620, HepG2, HEK293T, A549；2 个小鼠细胞系：C2C12, 3T3；2 个猪细胞系：PK15, ST）
  - Zoonomia 241 哺乳动物基因组比对（HAL 文件）
  - 功能基因组数据：ATAC-seq（33 个样本组，EpiMap）、DNase-seq、组蛋白修饰 ChIP-seq（Roadmap Epigenomics）、DNA 甲基化（37 个 consolidated epigenomes）、GTRD TF 结合位点（1355 个 TF）
  - 遗传学数据：GWAS Catalog、GTEx v10 fine-mapped eQTL、1000 Genomes Project Phase 3

- **输出**：
  - 人类 eG4 的进化保守性分类（C1 高保守 / C2 活跃进化 / C3 灵长类特异）
  - eG4finder 模型（输入 DNA 序列 → 输出 eG4 recurrence 预测值）
  - 6 个非人物种的 eG4 预测参考集
  - 三类 eG4 在功能基因组学指标上的系统比较
  - 三类 eG4 中 GWAS 变异和 eQTL 的富集分析结果

- **模块**：
  1. eG4 参考集构建（EndoQuad + G4 CUT&Tag 整合）
  2. 进化保守性量化（Zoonomia 比对 → 碱基比对率 → 三分类）
  3. eG4finder 模型（DNABERT-2 编码 + MLP 回归）
  4. 跨物种结构保守性验证（eG4finder 预测 + 实验 eG4 数据）
  5. 功能基因组学比较（染色质状态、TF 结合、组蛋白修饰、甲基化）
  6. 复杂性状关联分析（GWAS 富集、eQTL 富集、基因保守性分层）

- **训练**：
  - eG4finder 在人类 PQS 数据上训练（6:1:3 划分训练/验证/测试，三次随机划分取平均）
  - 训练目标：预测 eG4 recurrence（连续值回归）
  - 使用 AdaLoRA（Adaptive Low-Rank Adaptation）进行参数高效微调
  - 对比工具：Quadron、G4detector、PENGUINN、DeepG4

- **反馈回路**：无显式闭环反馈；模型预测结果用于跨物种 eG4 注释，但未反馈回模型训练。

- **假设**：
  - eG4 的碱基比对率可反映其进化保守性（假设比对率高的区域承受更强的纯化选择）
  - eG4 recurrence 与 G4 结构稳定性正相关（引用 EndoQuad 前期发现）
  - DNABERT-2 预训练模型能够编码与 G4 形成相关的序列特征

- **文字流程**：
  1. 从 EndoQuad 获取人类 PQS 及 eG4 注释，补充自产 G4 CUT&Tag 数据，构建综合 eG4 参考集
  2. 对每个 eG4，利用 Zoonomia HAL 比对计算其在 240 个非人物种中的碱基比对率，根据 N1（≥90% 比对的物种数）和 N2（≤10% 比对的物种数）将 eG4 分为 C1/C2/C3 三类
  3. 训练 eG4finder：以 PQS 序列 ±500 nt 侧翼为输入，DNABERT-2 编码后经 3 层 MLP 输出 recurrence
  4. 用 eG4finder 预测 6 个非人物种的全基因组 eG4，与人类 eG4 的跨物种比对结果交叉验证结构保守性
  5. 对三类 eG4 分别计算 ATAC-seq 信号、DNase 信号、组蛋白修饰信号、DNA 甲基化水平、TF 结合多样性
  6. 用 GREAT 做 GO 富集分析，比较三类 eG4 的功能类别
  7. 用 GWAS Catalog 和 GTEx eQTL 数据计算三类 eG4 中变异和 eQTL 的富集度，按基因保守性分层分析 eQTL 效应

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| eG4 参考集构建 | 整合多来源 eG4 注释，形成人类 eG4 综合参考集 | 单一数据库可能不饱和；需要最全面的 eG4 集合作为进化分析基础 | 输入：EndoQuad 41 细胞系 + 自产 7 细胞系 G4 CUT&Tag；输出：404,538 个人类 eG4 | Results 节：新细胞系中 91.2%-95.5% eG4 已在 EndoQuad 中，证明参考集接近饱和 | 若移除自产数据，参考集可能遗漏少量细胞系特异 eG4，但影响有限（因 EndoQuad 已接近饱和） |
| 进化保守性分类 | 将 eG4 分为 C1（高保守）、C2（活跃进化）、C3（灵长类特异） | 保守性是功能重要性的代理指标，分类是后续所有比较的基础 | 输入：eG4 坐标 + Zoonomia 241 基因组比对；输出：三类 eG4 标签 | Results 图 1B-C：三类 eG4 在 N1/N2 平面上形成清晰分离的聚类 | 若移除分类，无法进行任何保守性-功能关联分析 |
| eG4finder 模型 | 仅基于 DNA 序列预测 eG4 recurrence | 非人物种缺乏实验 eG4 数据，需要序列预测工具验证结构保守性 | 输入：PQS 序列 ±500 nt；输出：recurrence 预测值（连续） | Results 图 3B-E：人类测试集 AUROC=0.94，AUPRC=0.86，显著优于对比工具 | 若移除，无法验证跨物种结构保守性，保守性-功能关联的因果推断减弱 |
| 跨物种结构保守性验证 | 用 eG4finder 预测 6 个非人物种 eG4，与序列比对结果交叉验证 | 序列保守 ≠ 结构保守，需要独立验证 | 输入：6 物种全基因组 PQS + eG4finder；输出：各物种 eG4 参考集 | Results 图 4A-B：高保守 eG4 在非人物种中结构保守比例显著更高 | 若移除，无法区分「序列保守」与「结构保守」的贡献 |
| 功能基因组学比较 | 比较三类 eG4 的染色质可及性、组蛋白修饰、甲基化、TF 结合 | 建立保守性-功能梯度，验证保守 eG4 的功能增强 | 输入：三类 eG4 + ATAC-seq/DNase/ChIP-seq/甲基化数据；输出：各指标的比较统计 | Results 图 5B-F：高保守 eG4 在 ATAC-seq、DNase、激活型组蛋白修饰上信号最高，甲基化最低 | 若移除，无法建立保守性与功能的因果关系 |
| TF 结合分析 | 评估三类 eG4 的 TF 结合多样性和亲和力 | 直接关联到 TF–DNA 互作机制，解释保守 eG4 的调控优势 | 输入：三类 eG4 + GTRD 1355 TF 结合位点；输出：TF 多样性、结合富集分析 | Results 图 6A-D：高保守 eG4 的 TF 多样性最高，富集特定 TF 类别 | 若移除，无法将保守性与 TF 互作机制直接关联 |
| 复杂性状关联分析 | 检验三类 eG4 中 GWAS 变异和 eQTL 的富集差异 | 将保守性从分子功能延伸到表型关联，证明疾病相关性 | 输入：三类 eG4 + GWAS Catalog + GTEx eQTL；输出：富集统计 | Results 图 8A-E：高保守 eG4 中 GWAS 变异富集最高，eQTL 效应与基因保守性正相关 | 若移除，无法建立从保守性到复杂性状的完整证据链 |

**消融效应区分**：文中未报告对上述模块的正式消融实验。上述「移除后影响」为 [Analysis] 基于模块逻辑依赖关系的推断，非实测消融结果。

## 09 关键公式符号

本文方法部分未提供显式数学公式。以下为基于描述可推断的关键定义：

1. **碱基比对率（base alignment rate）**：
   - 定义：eG4 区域中能比对到给定物种基因组的碱基比例
   - 用途：量化每个 eG4 在 240 个非人物种中的保守程度
   - 来源：Results 节「we used halLiftover...to calculate the base alignment rates」；具体公式未提供

2. **N1 和 N2 统计量**：
   - N1 = 碱基比对率 ≥ 90% 的物种数
   - N2 = 碱基比对率 ≤ 10% 的物种数
   - 分类规则：C1（高保守）：N1 ≥ 120 且 N2 ≤ 25；C2（活跃进化）：20 ≤ N1 ≤ 50 且 N2 ≤ 120；C3（灵长类特异）：N1 ≤ 50 且 N2 ≥ 180
   - 来源：Methods 节「Category 1 (C1): highly conserved eG4s with N1 ≥ 120 and N2 ≤ 25; Category 2 (C2): actively evolving eG4s with 20 ≤ N1 ≤ 50 and N2 ≤ 120; and Category 3 (C3): primate-specific eG4s with N1 ≤ 50 and N2 ≥ 180」

3. **eG4 recurrence**：
   - 定义：PQS 在 EndoQuad 数据库中被检测为 eG4 的细胞系数量（非 eG4 的 recurrence = 0）
   - 用途：eG4finder 的预测目标，反映 G4 结构形成的稳健性
   - 来源：Methods 节「the recurrence of every input PQS denoted as y. The goal of this model is to predict the value of recurrence」

4. **eG4finder 模型结构**：
   - 输入序列 x = {x₁, x₂, ..., xₙ}，其中 xᵢ ∈ {"A","G","C","T","N"}
   - 编码器：DNABERT-2（12 层 transformer）
   - 输出层：3 层 MLP → 预测 recurrence 值
   - 来源：Methods 节「we utilize a large pre-trained model DNABERT-2...to tokenize x and learn the embedding of every token...put into 12 transformer layers...aggregate all token embeddings...put it into a 3-layer Multi-Layer Perceptron (MLP)」

5. **统计检验**：
   - Fisher's exact test（双侧）：用于分类比例比较（如 eG4 类别间 TE 重叠比例、GWAS SNP 富集）
   - Wilcoxon rank sum test（双侧）：用于连续分布比较（如 PhastCons 得分、ATAC-seq 信号、TF 多样性）
   - 来源：Results 节多处标注

## 10 实验设计与证据链

### 数据集与资源

| 数据类型 | 来源 | 规模/细节 |
|----------|------|-----------|
| 人类 eG4 参考集 | EndoQuad 数据库 + 自产 G4 CUT&Tag | 404,538 个 eG4；EndoQuad 覆盖 41 个人类细胞系；自产数据覆盖 7 个人类细胞系 |
| G4 CUT&Tag 数据 | 本研究产生 | 7 个人类细胞系（HT29, HCT116, NCM460, SW620, HepG2, HEK293T, A549）；2 个小鼠细胞系（C2C12, 3T3）；2 个猪细胞系（PK15, ST） |
| 哺乳动物基因组比对 | Zoonomia Consortium | 241 个哺乳动物基因组无参考比对（HAL 文件） |
| 功能基因组数据 | NIH Roadmap Epigenomics、EpiMap | ATAC-seq（33 样本组）、DNase-seq、组蛋白修饰 ChIP-seq（10 种修饰）、DNA 甲基化（37 个 consolidated epigenomes） |
| TF 结合位点 | GTRD 数据库 | 1355 个 TF 的非冗余结合位点 |
| 遗传变异数据 | GWAS Catalog、GTEx v10、1000 Genomes Project Phase 3 | GWAS 关联 SNP；fine-mapped eQTL；常见 SNP 及衍生等位基因频率 |

### 实验列表

| 实验 | 检验的 Claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| eG4 参考集饱和性验证 | EndoQuad 已覆盖绝大多数人类 eG4 | 自产 7 细胞系 vs EndoQuad 41 细胞系 | 新细胞系中 91.2%-95.5% 的 eG4 已在 EndoQuad 中 | EndoQuad 接近饱和，可作为参考集 | 不能排除未检测细胞系中存在新 eG4 | Results 节；Additional file 1: Fig. S1, S6 |
| eG4 进化分类 | eG4 可按保守性分为三类 | 基于 N1/N2 的二维分类 | C1/C2/C3 三类在 UMAP 上形成连续但可分的分布 | 三类分类有效概括 eG4 进化模式 | 分类边界有一定任意性 | Results 图 1B-G |
| eG4 vs 非 eG4 保守性比较 | eG4 比非 eG4 更保守 | eG4 vs 非 eG4 vs 随机区域 | eG4 在 C1 中比例更高 | eG4 整体承受更强的纯化选择 | 不能排除基因组位置混杂效应 | Results 图 1C |
| TE 对灵长类特异 eG4 的贡献 | TE 驱动灵长类特异 eG4 的扩张 | C3 vs C1/C2 的 TE 重叠比例 | C3 中 TE 重叠比例 51.5%，远高于 C1（7.0%）和 C2（12.1%） | SVA 和 ERV1 是灵长类特异 eG4 的主要来源 | TE 插入与 eG4 形成的因果方向需进一步验证 | Results 图 2A-D |
| eG4finder 性能评估 | eG4finder 可仅基于序列预测 eG4 | eG4finder vs Quadron、G4detector、PENGUINN、DeepG4 | AUROC=0.94，AUPRC=0.86，Accuracy=0.84，均优于对比工具 | eG4finder 是当前最优的序列-only eG4 预测器 | 跨物种泛化性能需更多物种验证 | Results 图 3C-E |
| 跨物种结构保守性验证 | 高保守 eG4 在其它物种中结构保守 | C1 vs C2 vs C3 在 6 物种中的结构保守比例 | C1 结构保守比例最高，C3 最低 | 序列保守与结构保守一致 | 预测的结构保守需实验验证 | Results 图 4A-B |
| GO 富集分析 | 不同保守类别的 eG4 关联不同功能 | C1 vs C2 vs C3 的 GREAT 分析 | C1 富集发育过程；C2 富集代谢过程；C3 富集嗅觉 | 保守性层级反映功能层级 | GO 分析受基因组背景影响 | Results 图 4C；Additional file 2: Table S1 |
| 染色质状态比较 | 高保守 eG4 具有更强的调控活性 | C1 vs C2 vs C3 的 ATAC-seq、DNase、组蛋白修饰信号 | C1 在 ATAC-seq、DNase、H3K4me3、H3K27ac 等激活信号上最高 | 高保守 eG4 是更强的调控元件 | 信号差异可能受基因组位置（如启动子富集）驱动 | Results 图 5B-D |
| DNA 甲基化分析 | 高保守 eG4 处于低甲基化状态 | C1 vs C2 vs C3 的甲基化水平 | C1 甲基化最低，C3 最高 | 高保守 eG4 处于活跃调控状态 | 甲基化与 eG4 形成的因果方向未定 | Results 图 5E-F |
| TF 结合分析 | 高保守 eG4 结合更多 TF | C1 vs C2 vs C3 的 TF 多样性 | C1 TF 多样性最高 | 高保守 eG4 是 TF 结合 hub | 多样性可能反映结合位点长度而非亲和力 | Results 图 6A-D |
| GWAS SNP 富集 | 高保守 eG4 富集复杂性状变异 | C1 vs C2 vs C3 的 GWAS SNP 富集 | C1 中 GWAS SNP 富集最高 | 高保守 eG4 与复杂性状关联最强 | 富集可能受连锁不平衡影响 | Results 图 8A-C |
| eQTL 富集 | 高保守 eG4 富集表达调控变异 | C1 vs C2 vs C3 的 fine-mapped eQTL 富集 | 高保守 eG4 中 eQTL 富集更高，且对高保守基因表达影响更强 | 高保守 eG4 通过调控基因表达影响性状 | eQTL 效应方向需功能验证 | Results 图 8E |
| 案例验证 | 高保守 eG4 变异影响具体基因表达 | rs402072 位于 PRKD2 启动子附近高保守 eG4 | rs402072 为 fine-mapped eQTL，与 1 型糖尿病相关 | 高保守 eG4 变异可影响疾病相关基因表达 | 单案例不能推广 | Results 节；Additional file 1: Fig. S24 |

## 11 结论正确解读

- **任务范围**：本文仅研究 DNA G-quadruplex（G4）结构，不涉及 RNA G4、也不涉及经典 TF–DNA 序列基序互作。结论限于「人类 eG4 的哺乳动物保守性及其与调控功能和复杂性状的关联」。
- **oracle/真值输入**：eG4 标签来自 EndoQuad 数据库（基于 G4 ChIP-seq/CUT&Tag 实验）和本研究自产 G4 CUT&Tag 数据。这些实验数据本身依赖 BG4 抗体的特异性和检测阈值，存在假阳性和假阴性。
- **端到端状态**：eG4finder 是端到端训练的（序列 → recurrence），但仅用于预测，未与下游功能分析形成闭环。跨物种 eG4 预测未经实验验证。
- **算力成本**：未报告训练 eG4finder 的具体算力需求。DNABERT-2 为 12 层 transformer，参数量较大，但使用 AdaLoRA 参数高效微调，实际训练成本未披露。
- **历史数据依赖**：所有分析基于当前人类参考基因组（GRCh38）和 Zoonomia 241 物种比对。比对质量受物种间序列分歧度影响，灵长类远缘物种的比对率可能被低估。
- **模型依赖**：eG4finder 依赖 DNABERT-2 的预训练表征，其泛化能力受预训练数据分布影响。对比工具（Quadron 等）为体外 G4 预测器，与体内 eG4 的差异可能影响比较公平性。
- **最难情形**：C2（活跃进化）类别的边界定义依赖 N1/N2 阈值（20 ≤ N1 ≤ 50 且 N2 ≤ 120），该阈值的选择可能影响分类结果。跨物种结构保守性验证中，非人物种 eG4 全部来自预测而非实验，存在系统性偏差风险。
- **群体/领域边界**：结论基于人类 eG4 在哺乳动物中的保守性，不适用于植物、真菌等非哺乳动物。复杂性状关联基于 GWAS Catalog 和 GTEx 数据，受限于这些数据库的群体代表性和组织覆盖。
- **不确定性**：作者未报告 eG4finder 预测的置信区间或不确定性量化。GWAS 富集分析未进行共定位或孟德尔随机化，不能推断因果关系。

**有边界的复述**：在人类基因组中，约 68.1% 的 eG4 可归类为高保守（C1）、活跃进化（C2）或灵长类特异（C3）三种进化模式之一；高保守 eG4 在启动子区域富集、具有更高的染色质可及性和激活型组蛋白修饰、结合更多样的 TF、且富集更多 GWAS 和 eQTL 变异。这些关联在统计上显著，但基于观察性数据，不能证明 eG4 结构本身是复杂性状的因果机制。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| eG4 参考集可能未完全饱和 | 尽管 EndoQuad 覆盖 41 个细胞系且新数据中 91.2%-95.5% 为已知 eG4，但仍有少量新 eG4 被发现 | 未明确提及 | Results 节（对饱和性的验证本身暗示不完全性） |
| 非人物种 eG4 依赖预测 | 除人类外，小鼠和猪有实验数据，但黑猩猩、猕猴、兔、大鼠的 eG4 全部来自 eG4finder 预测 | 未明确提及 | Results 节（eG4finder 用于跨物种预测的表述） |
| eG4finder 在部分物种中 AUPRC 和精度欠佳 | 尤其在猪和鸡中，AUPRC 和 precision 不理想，可能因非 eG4 集合包含未观测到的 eG4 | 未明确提及 | Results 节「Although the AUPRC and precision are suboptimal, especially in pig and chicken...」 |
| 平均化信号可能掩盖细胞类型特异性 | 作者指出平均化的表观基因组信号和合并的 TFBS 可能掩盖各 eG4 类别中潜在的细胞类型特异性差异 | 未明确提及 | Discussion 节「Although average epigenomic signals and consolidated TFBSs may obscure potential cell type-specific nuances...」 |
| 复杂性状关联的因果推断受限 | 观察性关联不能证明因果关系 | 未明确提及 | Discussion 节（对关联结果的谨慎表述） |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| eG4 分类依赖 N1/N2 阈值 | C1/C2/C3 的边界（N1 ≥ 120、N2 ≤ 25 等）是人为设定的，不同阈值可能改变分类结果和后续所有比较 | 若分类不稳定，则「高保守 eG4 功能更强」的结论可能对阈值敏感 | 进行阈值敏感性分析（如改变 N1/N2 临界值，检验分类稳健性） | Methods 节分类定义 |
| 保守性-功能关联可能受基因组位置混杂 | 高保守 eG4 富集于启动子，而启动子本身具有高 ATAC-seq 信号、高 H3K4me3、低甲基化。保守性可能与功能无关，而是启动子位置的副产物 | 若位置是混杂因素，则「保守性导致功能增强」的因果推断不成立 | 在匹配启动子/非启动子位置后重新比较三类 eG4 的功能指标 | Results 图 5 未报告位置匹配分析 |
| eG4finder 跨物种预测缺乏实验验证 | 黑猩猩、猕猴、兔、大鼠的 eG4 全部来自预测，预测误差可能系统性影响结构保守性结论 | 若预测在远缘物种中偏差大，则「高保守 eG4 结构保守」的结论可能为假 | 在至少一个非人物种中开展 G4 CUT&Seq/ChIP-seq 验证 | Results 节仅在小鼠和猪中有实验数据 |
| GWAS SNP 富集未控制连锁不平衡和等位基因频率 | 高保守 eG4 中 GWAS SNP 富集可能反映的是高保守区域本身 SNP 密度低（因纯化选择），而非因果变异富集 | 若未控制背景 SNP 密度，富集分析可能产生假阳性 | 使用与 SNP 密度匹配的零模型重新计算富集 | Results 图 8A-C 未报告 SNP 密度匹配 |
| TE 贡献分析仅基于重叠比例 | SVA/ERV1 与灵长类特异 eG4 的重叠比例高，但未排除这些 TE 插入本身携带其他调控元件（如 TF 结合位点）的混杂 | 若 TE 内的其他调控元件驱动功能，则「eG4 结构」而非「TE 序列」是功能载体的结论不成立 | 比较 TE 内 eG4 与非 eG4 区域的功能指标 | Results 图 2 未进行此对照 |
| 转录激活实验仅用报告基因 | 未在内源基因组位点验证 eG4 的转录激活功能 | 报告基因实验可能高估 eG4 在天然染色质环境中的效应 | 使用 CRISPR 编辑破坏内源 eG4 结构后检测基因表达变化 | Results 节未报告内源验证 |
| 未报告 eG4finder 的消融实验 | 未分析 DNABERT-2 预训练、侧翼长度、MLP 结构等设计选择的贡献 | 无法判断哪些设计选择对性能提升最关键 | 进行消融实验（如替换编码器、改变侧翼长度） | Methods 节未报告消融 |

## 14 学到什么

**Agent 提炼的知识候选**

1. **保守性分层策略**：将调控元件按跨物种保守性分为高保守/活跃进化/谱系特异三类，是筛选功能候选元件的通用框架。可迁移到 TF–DNA 互作研究：对 TF 结合位点进行跨物种保守性分层，优先研究高保守位点，可提高发现功能位点的效率。
2. **结构元件与序列基序的互补性**：本文证明 eG4 作为 DNA 二级结构元件，其保守性独立于序列基序保守性。在 TF–DNA 互作研究中，应考虑 TF 是否通过识别 DNA 结构（而非仅线性基序）实现结合——可借鉴本文方法，将结构预测（如 G4 形成倾向）纳入 TF 结合位点注释。
3. **基础模型用于结构预测**：eG4finder 展示了 DNABERT-2 预训练基础模型 + 轻量 MLP 头即可实现仅基于序列的高性能结构元件预测（AUROC=0.94）。这一架构可迁移到 TF 结合位点预测、染色质状态预测等任务，尤其适合缺乏实验数据的物种。
4. **多组学整合验证框架**：本文从「保守性分类 → 结构预测验证 → 染色质状态 → TF 结合 → 表达调控 → 复杂性状关联」构建了完整的证据链。该框架可迁移到 TF–DNA 互作研究：从 TF 结合位点的保守性出发，逐层验证其调控功能和表型关联。
5. **TE 对调控元件进化的贡献**：灵长类特异 eG4 主要由 TE（SVA、ERV1）驱动，提示 TE 插入是调控元件新生的主要来源。在 TF–DNA 互作研究中，分析 TF 结合位点的 TE 来源可揭示谱系特异调控网络的进化机制。
6. **eQTL 与保守性结合**：高保守 eG4 中 eQTL 对高保守基因表达影响更强，提示「保守调控元件 + 保守靶基因」的调控关系可能具有更强的表型效应。可迁移到 TF–DNA 互作：将 TF 结合位点的保守性与靶基因保守性联合分析，可优先锁定功能重要的 TF–靶基因关系。
7. **G4 作为 TF 结合平台**：eG4 通过形成二级结构为 TF 提供非经典结合位点，且高保守 eG4 结合更多样化的 TF。在 TF–DNA 互作建模中，应纳入 DNA 结构特征（如 G4 形成倾向、弯曲度、柔韧性）作为预测特征，而非仅使用序列基序。

## 15 与已有知识连接

- **Zoonomia 联盟**：本文使用的 241 哺乳动物比对来自 Zoonomia Consortium（Genome Res, 2020; Nature, 2020 等）。该资源已被广泛用于非编码元件保守性分析，如 cCREs 和 TF 结合位点的跨物种保守性研究。
- **EndoQuad 数据库**：本文引用的 eG4 数据库，由同一团队前期建立（Nucleic Acids Res, 2023）。该数据库整合了 41 个人类细胞系的 G4 ChIP-seq/CUT&Tag 数据。
- **G4 检测技术**：G4 ChIP-seq（Hänsel-Hertsch et al., Nat Genet, 2016）、G4 CUT&Tag（Li et al., Genome Biol, 2023 等）为本文实验基础。BG4 抗体为 G4 结构特异性单链抗体（Biffi et al., Nat Chem, 2013）。
- **DNABERT-2**：本文使用的预训练基因组基础模型（Zhou et al., 2023, bioRxiv），基于 BERT 架构，在人类和多物种基因组上预训练。属于基因组基础模型（genomic foundation models）家族，与 Nucleotide Transformer、Enformer 等并列。
- **G4 预测工具谱系**：早期基于序列基序的 QGRS Mapper、Quadparser → 基于机器学习的 Quadron（Sahakyan et al., Nat Methods, 2017）→ 基于深度学习的 DeepG4（Barshai et al., NAR Genom Bioinform, 2023）、G4Beacon（Kaur et al., 2023）→ 本文的 eG4finder（基于 DNABERT-2）。
- **保守性-功能关联研究**：本文方法类似 ENCODE 项目的 cCRE 保守性分析（Moore et al., Nature, 2020）和 Zoonomia 的保守非编码元件研究（Sullivan et al., Nature, 2023），但首次将这一框架应用于 eG4。
- **TF–DNA 互作的结构层面**：本文关于 eG4 作为 TF 结合 hub 的发现，与「非 B 型 DNA 结构参与转录调控」的研究方向一致（如 R-loop、三链体 DNA 等），可连接到 Georgakopoulos-Soares et al. (2022) 关于非 B 型 DNA 与调控的综述。
- **GWAS/eQTL 富集分析**：本文方法类似 fgwas、GARFIELD 等基因组注释富集工具，但针对 eG4 这一特定注释集。与「调控元件中 GWAS 变异富集」的经典研究（如 Farh et al., Nature, 2015）一致。

## 16 研究想法

**Agent 生成的研究候选**

1. **TF–G4 共保守性网络分析**
   - 名称：Conserved G4-TF Regulatory Network Mapping
   - 来源局限/观察：本文证明高保守 eG4 是 TF 结合 hub，但未系统分析哪些 TF 家族优先结合高保守 eG4，以及这种结合是否在哺乳动物中保守。
   - 核心假设：特定 TF 家族（如发育相关 TF）通过识别 G4 结构实现跨物种保守的调控功能，其结合位点的 G4 保守性高于非保守 TF。
   - 初步方法：整合本文 eG4 保守性分类与 GTRD/ENCODE TF ChIP-seq 数据，计算每个 TF 在高保守 vs 灵长类特异 eG4 的结合富集度；对富集 TF 进行 motif 分析，区分序列基序依赖与结构依赖的结合模式。
   - 验证方式：CRISPR 破坏高保守 eG4 结构后检测 TF 结合变化（CUT&Tag）；跨物种（人/小鼠）比较 TF 结合谱。
   - 创新状态：unverified

2. **基于基础模型的 TF–G4 协同结合预测器**
   - 名称：G4TF-Bind：A Foundation Model for G4-Aware TF Binding Prediction
   - 来源局限/观察：eG4finder 仅预测 G4 形成，未将 G4 结构信息纳入 TF 结合预测。现有 TF 结合预测模型（如 DeepBind、DeepSEA）仅使用序列基序，忽略 DNA 结构。
   - 核心假设：将 G4 结构预测分数作为额外特征输入 TF 结合预测模型，可显著提高在 G4 富集区域的预测精度，尤其对结构感知型 TF。
   - 初步方法：以 DNABERT-2 编码序列，将 eG4finder 输出的 G4 分数作为辅助特征，训练多任务模型同时预测 TF 结合和 G4 形成；在 ENCODE 和 CUT&Tag 数据上评估。
   - 验证方式：与 DeepBind、DeepSEA 在独立测试集上比较 AUROC/AUPRC；分析模型注意力权重是否关注 G4 形成区域。
   - 创新状态：unverified

3. **eG4 保守性作为功能变异优先级排序工具**
   - 名称：G4Conservation Score for Variant Prioritization
   - 来源局限/观察：本文证明高保守 eG4 富集 GWAS 和 eQTL 变异，但未开发可直接用于临床或功能基因组学的评分工具。
   - 核心假设：结合 eG4 保守性、G4 形成概率和序列上下文，可构建优于现有 CADD/GWAVA 的非编码变异优先级评分。
   - 初步方法：基于本文 404,538 个 eG4 的保守性分类和 eG4finder 分数，训练梯度提升模型预测变异是否为 eQTL 或 GWAS 关联变异；与 CADD、LINSIGHT 比较。
   - 验证方式：独立 GWAS 数据集的富集分析；精细定位（fine-mapping）中后验概率比较。
   - 创新状态：unverified

4. **G4 结构扰动对 TF 结合动力学的分子模拟研究**
   - 名称：Molecular Dynamics of G4-TF Interactions：Conserved vs Lineage-Specific
   - 来源局限/观察：本文从基因组学层面证明高保守 eG4 与 TF 结合相关，但缺乏分子层面的机制解释——G4 结构如何被 TF 识别、保守性如何影响结合亲和力。
   - 核心假设：高保守 eG4 形成的 G4 结构具有更高的热力学稳定性，从而为 TF 提供更稳定的结合平台；灵长类特异 eG4 的 G4 结构更动态、更易被解旋。
   - 初步方法：选取代表性高保守和灵长类特异 eG4 序列，用 CDOCKER/Glide 进行 TF–G4 对接，用 AMBER/GROMACS 进行 μs 级 MD 模拟，比较结合自由能和结构稳定性。
   - 验证方式：表面等离子共振（SPR）或等温滴定量热法（ITC）测量 TF–G4 结合亲和力；圆二色谱（CD）检测 G4 结构稳定性。
   - 创新状态：unverified

5. **跨物种 eG4 图谱与 TF 结合位点进化**
   - 名称：Evolutionary Dynamics of G4-Associated TF Binding Sites
   - 来源局限/观察：本文仅预测了 6 个非人物种的 eG4，未系统分析 eG4 相关的 TF 结合位点在哺乳动物中的获得与丢失模式。
   - 核心假设：高保守 eG4 附近的 TF 结合位点倾向于共保守，而灵长类特异 eG4 附近的 TF 结合位点则快速周转（turnover），驱动谱系特异调控网络进化。
   - 初步方法：利用本文 eG4 保守性数据与 Zoonomia 比对，分析 eG4 与 TF 结合位点的共保守性；比较不同进化枝的 eG4-TF 位点获得/丢失速率。
   - 验证方式：系统发育广义最小二乘（PGLS）检验共保守性；与已知的谱系特异调控进化案例交叉验证。
   - 创新状态：unverified

6. **eG4 变异与复杂性状的孟德尔随机化分析**
   - 名称：Causal Inference of G4-Associated Variants on Complex Traits
   - 来源局限/观察：本文的 GWAS 富集分析是观察性的，不能排除连锁不平衡或混杂因素。
   - 核心假设：高保守 eG4 中的变异通过改变 G4 结构稳定性影响基因表达，从而对复杂性状产生因果效应。
   - 初步方法：以 eG4 保守性分类作为工具变量，使用孟德尔随机化（MR）分析 eG4 变异对基因表达和复杂性状的因果效应；结合 eQTL 和 GWAS 数据进行共定位分析。
   - 验证方式：MR-Egger 和加权中位数法进行敏感性分析；在独立队列中验证。
   - 创新状态：unverified