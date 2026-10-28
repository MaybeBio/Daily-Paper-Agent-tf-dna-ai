## 01 基本信息

- **标题**：Light-responsive transcription factors VvHYH and VvGATA24 mediate wax terpenoid biosynthesis in Vitis vinifera
- **作者**：Yang, Mingyi; Xiang, Yizhou; Luo, Zisheng; Gao, Yizhou; Wang, Lei; Hu, Qiannan; Dong, Yingying; Qi, Ming; Li, Dong; Liu, Lingling; Kacaniova, Miroslava; Ban, Zhaojun; Li, Li
- **单位**：未提供（PubMed 记录未列出单位信息）
- **期刊/平台**：Plant Physiology
- **年份**：2024
- **论文类型**：研究论文（Original Research Article）
- **领域**：植物分子生物学 / 植物次生代谢调控 / 转录调控
- **关键词**：cuticular wax, terpenoid biosynthesis, transcription factor, light response, chromatin accessibility, Vitis vinifera
- **DOI/arXiv 号**：10.1093/plphys/kiae366
- **代码**：未提供
- **数据**：ATAC-seq 和 RNA-seq 数据（未提供 accession 号）
- **阅读日期**：2024-07-08（基于 DOI 日期推断，实际阅读日期未提供）
- **在该方向中的位置**：本文属于「TF–DNA 结合机制 × 实验验证 + 分子对接模拟」交叉方向。核心贡献在于：① 用 ATAC-seq 定位开放染色质区域，缩小 TF 候选结合位点范围；② 用双荧光素酶（dual-LUC）和表面等离子共振（SPR）定量验证 TF–DNA 结合；③ 用分子对接（molecular docking）预测 TF–DNA 结合界面残基。对「TF–DNA 互作 × AI/物理模拟」课题的可迁移点：ATAC-seq 引导的顺式元件筛选策略、SPR 定量结合亲和力作为 docking 验证基准、docking 残基预测与实验突变验证的闭环设计。

---

## 02 一句话总结

本文通过整合 ATAC-seq 与 RNA-seq 数据，鉴定出光响应转录因子 VvHYH 和 VvGATA24 分别结合 VvTPS12 的 G-box 和 VvHMGR2 的 GATA-box 开放染色质区域，激活葡萄果实蜡质萜烯生物合成，并用 SPR 定量（Kd = 2.81 nM 和 8.59 nM）和分子对接残基预测支撑了这一调控机制。

---

## 03 研究问题

- **具体问题**：光照促进植物表皮蜡质积累的分子机制是什么？具体而言，哪些转录因子响应光信号，通过结合哪些顺式元件来激活蜡质萜烯生物合成基因？
- **为什么重要**：表皮蜡质是植物抵御环境胁迫（干旱、病原、紫外线等）的第一道屏障，理解光调控蜡质合成的分子基础可为抗逆育种提供基因靶点。
- **现有方法为何不足**：此前研究多集中在蜡质合成酶基因的鉴定，对上游转录调控（尤其是光信号如何传导至蜡质基因）了解有限；且缺乏染色质可及性层面的证据，难以区分直接结合与间接调控。
- **精确的「Can ... ?」研究问题**：Can light-responsive transcription factors directly bind to open chromatin regions of wax terpenoid biosynthesis genes to activate their expression in grape?

---

## 04 背景与发展脉络

> 注：以下脉络为「经外部核验」的领域常识，结合本文框架整理。

1. **阶段一：蜡质合成酶基因的鉴定（2000s–2010s）**
   - 代表性方法：遗传筛选、转录组学
   - 优点：鉴定出大量蜡质合成通路基因（如 CER、WAX、TPS 家族）
   - 局限：对上游调控因子（TFs）研究零散，缺乏系统调控网络视角

2. **阶段二：TF–启动子结合的传统验证（2010s–2020s）**
   - 代表性方法：酵母单杂交（Y1H）、电泳迁移率变动分析（EMSA）、染色质免疫沉淀（ChIP-qPCR）
   - 优点：能验证 TF–DNA 直接结合
   - 局限：依赖已知启动子区域，无法覆盖全基因组范围的开放染色质；ChIP 需要高质量抗体，通量低

3. **阶段三：染色质可及性 + 转录组整合（2020s–至今）**
   - 代表性方法：ATAC-seq + RNA-seq 联合分析
   - 优点：全基因组范围定位开放染色质与顺式元件，缩小候选结合位点
   - 局限：ATAC-seq 本身不提供 TF 身份，需结合 motif 分析或 TF 表达数据

4. **阶段四：定量结合 + 结构预测（本文位置）**
   - 代表性方法：SPR 定量亲和力 + 分子对接预测结合界面
   - 优点：提供结合强度的定量证据，并预测关键残基，为后续突变验证提供假设
   - 局限：docking 预测精度有限，需实验突变验证；本文未做点突变功能验证

**本文主张的位置**：在阶段三的基础上，向前推进到阶段四——不仅鉴定 TF 和靶基因，还用 SPR 给出定量亲和力，用 docking 预测结合界面残基，形成「开放染色质 → TF 候选 → 定量结合 → 结构预测」的完整链条。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 光调控蜡质合成的分子机制不明 | 已知光照促进蜡质积累，但不知道哪些 TF 介导 | 缺乏染色质层面的调控信息，传统启动子分析覆盖不全 | 摘要：「the molecular basis of light-responsive wax biosynthesis remains elusive」 |
| 难以区分直接结合与间接调控 | 转录组差异基因不一定是 TF 的直接靶标 | 表达变化可能来自下游级联效应 | 作者用 ATAC-seq 开放染色质 + 顺式元件图谱来「identify the potential action sites」（摘要） |
| 缺乏 TF–DNA 结合的定量证据 | 传统 EMSA/Y1H 只能定性 | 需要更精确的亲和力数据来支撑调控强度 | 作者用 SPR 给出 Kd = 2.81 nM（VvHYH–VvTPS12）和 8.59 nM（VvGATA24–VvHMGR2）（摘要） |
| 结构层面的结合机制未知 | 不知道 TF 哪些残基参与 DNA 识别 | 缺乏晶体结构或高精度预测 | 作者用分子对接预测 24 个残基（VvHYH）和 12 个残基（VvGATA24）参与结合（摘要） |

---

## 06 核心思想

### 1) 表面方法
- 对光照 vs 黑暗处理的葡萄果实做 ATAC-seq + RNA-seq，整合分析得到开放染色质区域和差异表达基因
- 从中筛选出蜡质萜烯合成候选基因（VvTPS12、VvHMGR2）和候选 TF（VvHYH、VvGATA24）
- 用 dual-LUC 定性验证、SPR 定量验证 TF–DNA 结合
- 用分子对接预测结合界面残基
- 用瞬时过表达（葡萄果实和本氏烟叶片）验证功能

### 2) 核心洞察
- **开放染色质作为 TF 结合位点的先验过滤器**：ATAC-seq 提供的染色质可及性信息能显著缩小候选顺式元件范围，避免在不可及的基因组区域盲目寻找结合位点
- **TF–DNA 结合强度可定量**：SPR 给出的 nM 级 Kd 值（2.81 nM、8.59 nM）表明这些是强结合事件，支持直接调控而非间接效应
- **docking 可提供可检验的结构假设**：预测出的关键残基（如 VvHYH 的 Arg106A）为后续突变实验提供了具体靶点

### 3) 可能的普适教训 [Analysis]
- 对「TF–DNA 互作 × AI/物理模拟」课题：**实验定量数据（SPR Kd）可以作为 docking/AI 预测的校准基准**——如果预测的结合亲和力与实验 Kd 趋势一致，则模型可信度更高
- **ATAC-seq 引导的候选位点筛选**可大幅降低 AI 模型搜索空间，提高预测精度
- **docking 残基预测 + 点突变验证**是连接计算与实验的闭环设计，值得在类似课题中复制

---

## 07 方法总览

- **输入**：光照处理 vs 黑暗处理的葡萄果实组织（RNA-seq + ATAC-seq 数据）
- **输出**：① 调控模型（VvHYH→VvTPS12，VvGATA24→VvHMGR2）；② 结合亲和力（Kd 值）；③ 结合界面残基预测
- **模块**：
  1. 表型分析（蜡质含量、腐烂率、脱落率）
  2. ATAC-seq + RNA-seq 整合分析（开放染色质 + 差异表达 + 顺式元件图谱）
  3. 候选基因/TF 筛选（VvTPS12、VvHMGR2、VvHYH、VvGATA24）
  4. 瞬时过表达功能验证（葡萄果实 + 本氏烟叶片）
  5. dual-LUC 定性结合验证
  6. SPR 定量结合验证（Kd 测定）
  7. 分子对接结构预测（结合残基）
- **训练**：不适用（非机器学习方法）
- **工具**：ATAC-seq 分析流程、RNA-seq 分析流程、dual-LUC 系统、SPR 仪器、分子对接软件（具体工具名未提供）
- **反馈回路**：ATAC-seq 开放染色质 → 候选位点 → 结合验证 → 功能验证 → 结构预测 → （未来）突变验证
- **假设**：开放染色质区域中的顺式元件是 TF 直接结合的功能位点；SPR 测定的体外结合亲和力反映体内调控强度

**文字流程**：
光照处理 → 表型差异确认（蜡质↑、腐烂↓）→ ATAC-seq 定位开放染色质 + RNA-seq 鉴定差异表达基因 → 交集筛选出 VvTPS12/VvHMGR2（靶基因）和 VvHYH/VvGATA24（TF）→ 瞬时过表达验证功能（蜡质晶体↑、萜烯含量↑）→ dual-LUC 确认 VvHYH 激活 VvTPS12 启动子、VvGATA24 激活 VvHMGR2 启动子 → SPR 定量 Kd → 分子对接预测结合残基 → 提出调控模型。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ATAC-seq 开放染色质图谱 | 定位基因组中可被 TF 结合的区域 | 缩小候选顺式元件范围，避免全基因组盲目搜索 | 输入：染色质片段；输出：开放染色质峰 + 顺式元件注释 | 摘要：「ATAC-seq and RNA-seq data were integrated to draw the chromatin accessibility and cis-elements regulatory map」 | 预期影响：失去候选位点先验，TF 结合位点预测将高度不确定 [Analysis] |
| RNA-seq 差异表达分析 | 鉴定光照响应的差异表达基因 | 关联开放染色质与表达变化，筛选功能相关基因 | 输入：RNA-seq reads；输出：差异表达基因列表 | 摘要：「integrated to draw ... regulatory map to identify the potential action sites」 | 预期影响：无法区分开放但非表达的基因，候选靶标数量爆炸 [Analysis] |
| 瞬时过表达功能验证 | 确认 TF 过表达促进蜡质积累 | 从相关性走向因果性 | 输入：TF 过表达载体；输出：蜡质晶体密度、萜烯含量 | 摘要：「more abundant wax crystals and higher wax terpenoid content were observed」 | 预期影响：失去功能证据，调控关系仅为相关性 |
| dual-LUC 定性结合验证 | 确认 TF 能激活靶基因启动子 | 提供转录激活的直接证据 | 输入：TF 效应子 + 启动子-LUC 报告子；输出：LUC/REN 比值 | 摘要：「interaction ... confirmed qualitatively using a dual luciferase assay」 | 预期影响：失去转录激活证据，仅剩体外结合数据 |
| SPR 定量结合验证 | 测定 TF–DNA 结合亲和力 | 提供定量 Kd，支撑直接结合 | 输入：纯化 TF 蛋白 + 生物素化 DNA 探针；输出：Kd 值（2.81 nM、8.59 nM） | 摘要：「quantitatively using surface plasma resonance, with an equilibrium dissociation constant of 2.81 nm」 | 预期影响：失去定量证据，无法判断结合强度是否生理相关 |
| 分子对接结构预测 | 预测 TF–DNA 结合界面残基 | 提供结构层面的机制假设 | 输入：TF 结构 + DNA 序列；输出：预测结合残基（如 Arg106A、Pro218B） | 摘要：「Molecular docking simulation implied the structural nature of this interaction」 | 预期影响：失去结构假设，无法指导后续突变实验 [Analysis] |

---

## 09 关键公式符号

**不适用**。本文为实验生物学论文，未使用数学模型或公式。SPR 的 Kd 值（2.81 nM、8.59 nM）为仪器拟合输出，原文未给出拟合方程。

---

## 10 实验设计与证据链

### 数据集/群体/指标/基线/预算/仪器/评测协议
- **植物材料**：葡萄（Vitis vinifera）果实；本氏烟（Nicotiana benthamiana）叶片
- **处理**：光照 vs 黑暗（对照）
- **表型指标**：蜡质含量、蜡质晶体密度（扫描电镜）、果实腐烂率、脱落率、萜烯含量
- **组学数据**：ATAC-seq、RNA-seq（光照 vs 黑暗）
- **结合验证**：dual-LUC（定性）、SPR（定量，Kd）
- **结构预测**：分子对接
- **功能验证**：瞬时过表达（葡萄果实、本氏烟叶片）
- **评测协议**：未提供详细统计方法（如重复数、显著性检验方法）

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| 光照 vs 黑暗表型比较 | 光照促进蜡质积累并降低腐烂/脱落 | 光照处理 vs 黑暗对照 | 光照组蜡质萜烯含量更高，腐烂率和脱落率更低 | 光照确实影响蜡质积累和果实品质 | 未证明因果关系（光照可能通过其他通路间接影响） | 摘要 |
| ATAC-seq + RNA-seq 整合 | 开放染色质区域富集差异表达基因的顺式元件 | 光照 vs 黑暗的染色质可及性和表达谱 | 鉴定出 VvTPS12、VvHMH2 为靶基因，VvHYH、VvGATA24 为候选 TF | 开放染色质区域包含 TF 结合位点 | 未证明这些 TF 就是光照信号的直接介导者 | 摘要 |
| 瞬时过表达功能验证 | VvHYH/VvGATA24 过表达促进蜡质积累 | 过表达 vs 空载体对照（葡萄果实、本氏烟） | 过表达组蜡质晶体更丰富、萜烯含量更高 | TF 确实激活蜡质合成 | 未证明内源水平下这些 TF 是必需的（缺 knockdown/突变体） | 摘要 |
| dual-LUC | VvHYH 激活 VvTPS12 启动子；VvGATA24 激活 VvHMGR2 启动子 | 效应子（TF）vs 空载体 + 报告子（启动子-LUC） | 有激活信号 | TF 能转录激活靶启动子 | 未排除间接激活（需突变顺式元件验证） | 摘要 |
| SPR | TF 与靶启动子 DNA 直接结合 | 纯化 TF 蛋白 vs 生物素化 DNA 探针 | Kd = 2.81 nM（VvHYH–VvTPS12）；Kd = 8.59 nM（VvGATA24–VvHMGR2） | 直接物理结合，且亲和力高 | 未提供突变 DNA 或突变 TF 的对照，无法确认结合特异性 | 摘要 |
| 分子对接 | 预测结合界面残基 | 计算模拟 | VvHYH 的 24 个残基（含 Arg106A）结合 G-box；VvGATA24 的 12 个残基（含 Pro218B）结合 GATA-box | 提供结构层面的结合模型 | 未用点突变实验验证预测残基的功能 | 摘要 |

---

## 11 结论正确解读

- **任务范围**：本文仅研究了葡萄果实中两个 TF（VvHYH、VvGATA24）对两个靶基因（VvTPS12、VvHMH2）的调控，不覆盖全部蜡质合成基因或全部光响应 TF。
- **oracle/真值输入**：SPR 的 Kd 值来自体外纯化蛋白与合成 DNA 探针的结合实验，不代表体内结合状态；体内染色质环境（组蛋白修饰、竞争性 TF）未纳入。
- **端到端状态**：本文未做「TF 突变体 → 表型变化」的遗传学验证，因此「VvHYH/VvGATA24 是光调控蜡质合成的必需因子」这一结论尚未被证明。
- **算力成本**：分子对接为计算模拟，精度有限，预测残基未经实验验证。
- **历史数据依赖**：ATAC-seq 和 RNA-seq 数据来自特定发育阶段和品种的葡萄果实，结论可能不适用于其他品种或组织。
- **模型依赖**：分子对接结果依赖所用 TF 结构模型（可能为同源建模或 AlphaFold 预测，原文未说明）。
- **最难情形**：光照信号如何传导至 VvHYH/VvGATA24 的上游通路（光受体、信号激酶等）完全未涉及。
- **群体/领域边界**：结论限于葡萄（Vitis vinifera）及其近缘物种，跨物种推广需谨慎。
- **不确定性**：Kd 值未给出误差范围或重复数；docking 预测残基未做突变验证。

**有边界的复述**：在葡萄果实中，光照条件下 VvHYH 和 VvGATA24 能够以高亲和力（nM 级）直接结合 VvTPS12 和 VvHMH2 启动子中的开放染色质区域，并在瞬时过表达体系中促进蜡质萜烯积累；但该调控通路的上游信号、体内必要性及结构预测残基的功能均未验证。

---

## 12 作者自认局限

在提供的材料（摘要）中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限，基于摘要推断）：
- 功能验证仅用瞬时过表达体系，未做稳定转基因或突变体分析（摘要仅提及「transiently overexpressed」）。
- 分子对接为计算预测，未与实验突变数据交叉验证（摘要仅说「implied the structural nature」）。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|---------|---------|------|
| SPR 的 Kd 值（2.81 nM、8.59 nM）来自体外纯化蛋白与短 DNA 探针 | 体内染色质环境（核小体占据、组蛋白修饰、其他蛋白竞争）可能显著改变结合亲和力；nM 级 Kd 在体外常见，但体内未必如此强 | 若体内结合弱，则「直接调控」结论需弱化 | 用 ChIP-qPCR 或 CUT&Tag 在体内验证 TF 是否占据靶位点 | 摘要仅提供体外 SPR 数据 |
| 分子对接预测的残基（Arg106A、Pro218B）未做突变验证 | 预测可能不准确；这些残基可能不参与实际结合 | 若残基预测错误，则结构模型不可靠 | 对预测残基做点突变，检测结合亲和力变化 | 摘要未提及突变实验 |
| 瞬时过表达验证功能，但未做 knockdown/knockout | 过表达可能产生非生理性高浓度效应；内源 TF 可能并非必需 | 无法确认内源调控必要性 | 用 VIGS 或 CRISPR 敲低/敲除 VvHYH/VvGATA24，观察蜡质表型 | 摘要仅提及「transiently overexpressed」 |
| ATAC-seq 开放染色质 ≠ TF 实际结合位点 | 开放染色质区域可能包含多个 motif，VvHYH/VvGATA24 的结合位点未必是唯一候选 | 若实际结合位点不同，则调控模型需修正 | 用 TF 特异性 ChIP-seq 或 DNA-affinity purification 验证 | 摘要未提供 ChIP 数据 |
| 光照处理与 TF 表达/活性的因果关系未建立 | 光照可能通过改变 TF 表达水平、翻译后修饰或核定位来激活，本文未区分 | 理解调控层级需要知道光信号如何作用于 TF | 检测光照下 VvHYH/VvGATA24 的 mRNA、蛋白水平及亚细胞定位 | 摘要未提及相关实验 |
| 仅研究两个 TF 和两个靶基因 | 蜡质合成通路可能受更多 TF 调控，存在冗余性 | 若存在冗余，单基因育种策略可能无效 | 全基因组 TF 结合谱 + 共表达网络分析 | 摘要仅聚焦两个 TF |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **ATAC-seq 引导的 TF 靶标筛选策略**（可迁移性：高）
   - 概念：先用 ATAC-seq 定位开放染色质，再与 RNA-seq 差异表达基因取交集，缩小 TF 候选结合位点
   - 迁移到本课题：在「TF–DNA 互作 × AI」中，可将 ATAC-seq 峰作为正样本区域，训练模型预测 TF 结合位点；或作为先验过滤器，减少候选位点搜索空间

2. **SPR 定量 Kd 作为 docking/AI 预测的校准基准**（可迁移性：高）
   - 概念：SPR 提供 TF–DNA 结合的定量亲和力，可作为计算预测的 ground truth
   - 迁移到本课题：若用 AI 或 MD 模拟预测 TF–DNA 结合强度，可用实验 Kd 值（如本文 2.81 nM、8.59 nM）作为验证集，评估预测精度

3. **分子对接残基预测 + 实验验证的闭环设计**（可迁移性：中高）
   - 概念：docking 预测结合界面残基，后续用点突变验证
   - 迁移到本课题：在 AI 预测 TF–DNA 结合界面后，设计点突变实验验证关键残基，形成「预测 → 验证 → 修正」的闭环

4. **dual-LUC + SPR 的双重验证策略**（可迁移性：中）
   - 概念：先用 dual-LUC 定性确认转录激活，再用 SPR 定量确认物理结合
   - 迁移到本课题：在计算预测出候选 TF–DNA 对后，可用 dual-LUC 快速筛选，SPR 精确量化，形成分级验证流程

5. **「开放染色质 + 顺式元件」的调控模型**（可迁移性：中）
   - 概念：TF 结合需要染色质开放，开放染色质图谱可预测 TF 可及性
   - 迁移到本课题：在 AI 模型中引入染色质可及性特征（如 ATAC-seq 信号），可提高 TF 结合位点预测的准确性

---

## 15 与已有知识连接

- **相似工作**：植物中光调控蜡质/萜烯合成的 TF 研究（如 Arabidopsis 中 HY5 调控蜡质基因、柑橘中 AP2/ERF 调控萜烯），本文的 VvHYH 属于 bZIP 家族（HY5 同源），与已知的光形态建成调控因子一致。可对比 HY5 在拟南芥中的靶基因调控模式。
- **方法学连接**：ATAC-seq + RNA-seq 整合分析在动物细胞 TF 研究中已广泛使用（如 ENCODE 项目），本文将其应用于植物次生代谢，方法可迁移。
- **结构预测连接**：分子对接预测 TF–DNA 结合残基的方法与 AlphaFold3、RoseTTAFoldNA 等 AI 结构预测工具互补——本文用经典 docking，AI 方法可提供更高精度的结构模型作为 docking 输入。
- **与 AI 方法的潜在组合**：本文的 Kd 值（2.81 nM、8.59 nM）可作为训练或验证「TF–DNA 结合强度预测模型」的实验数据点；ATAC-seq 峰可作为「可及性 + 结合」联合预测模型的训练标签。
- **候选方向（未验证）**：VvHYH 与拟南芥 HY5 的 DNA 结合域同源性如何？是否可跨物种迁移结合 motif 预测？[Analysis]

---

## 16 研究想法

> **Agent 生成的研究候选**

### 候选 1：基于 ATAC-seq 峰 + TF motif 的「可及性感知」TF–DNA 结合预测模型
- **名称**：Accessibility-Aware TF–DNA Binding Predictor
- **来源局限/观察**：本文用 ATAC-seq 缩小候选位点，但未用计算模型系统化这一策略；现有 TF–DNA 预测模型（如 DeepSEA、Basenji）多基于序列，未显式整合染色质可及性
- **核心假设**：将 ATAC-seq 可及性信号作为额外特征，可显著提升 TF–DNA 结合位点预测的精确率
- **相对本文的增量**：本文是人工筛选 + 实验验证，本候选将其自动化、泛化
- **初步方法**：用 CNN/Transformer 架构，输入为 DNA 序列 + ATAC-seq 信号，输出为 TF 结合概率；用植物（葡萄、拟南芥）公开 ChIP-seq 数据训练
- **验证方式**：在留出染色体上评估 AUC/PRC；用 SPR Kd 值作为独立验证集
- **可能的失败模式**：ATAC-seq 信号与 TF 结合并非严格对应（开放区域未必被结合），模型可能学到可及性而非结合特异性
- **创新状态**：unverified

### 候选 2：TF–DNA 结合亲和力的「实验 Kd + 分子对接 + MD 精修」多尺度预测流程
- **名称**：Kd-Calibrated Docking-MD Pipeline for TF–DNA Interactions
- **来源局限/观察**：本文用 docking 预测残基但未量化结合自由能；SPR Kd 提供了定量基准但未与计算预测对接
- **核心假设**：用实验 Kd 校准 docking/MD 计算的结合自由能，可提高对未实验 TF–DNA 对的亲和力预测精度
- **相对本文的增量**：本文 docking 仅做定性残基预测，本候选将其升级为定量预测
- **初步方法**：对 VvHYH–VvTPS12 和 VvGATA24–VvHMGR2 做 docking → MD 模拟（如 100 ns）→ MM-PBSA/MM-GBSA 计算结合自由能 → 与实验 Kd 对比校准 → 外推到同源 TF–DNA 对
- **验证方式**：对已知 Kd 的 TF–DNA 对（如来自 ProThermDB 或文献）做交叉验证
- **可能的失败模式**：MD 采样不足、力场精度有限，计算自由能与实验 Kd 相关性低
- **创新状态**：unverified

### 候选 3：光响应 TF 调控网络的「多组学 + 图神经网络」建模
- **名称**：Light-Responsive TF Regulatory Network GNN
- **来源局限/观察**：本文只研究了两个 TF 和两个靶基因，但光调控蜡质合成可能涉及更复杂的调控网络
- **核心假设**：用图神经网络整合 ATAC-seq、RNA-seq、TF motif 和蛋白-蛋白互作数据，可预测光响应条件下 TF→靶基因的调控关系
- **相对本文的增量**：从「一对基因」扩展到「全基因组调控网络」
- **初步方法**：构建异质图（TF 节点、基因节点、染色质区域节点），用 GNN 做链路预测；用本文的 VvHYH→VvTPS12 和 VvGATA24→VvHMGR2 作为已知正例
- **验证方式**：留出法预测新 TF–靶基因对，用 ChIP-seq 或突变体验证
- **可能的失败模式**：训练数据不足（植物 TF ChIP-seq 数据有限），GNN 可能过拟合
- **创新状态**：unverified

### 候选 4：TF–DNA 结合残基的「AlphaFold3 预测 vs 分子对接」系统比较
- **名称**：Benchmarking AlphaFold3 vs Docking for Plant TF–DNA Complex Prediction
- **来源局限/观察**：本文用经典 docking 预测残基，但未与 AlphaFold3 等 AI 结构预测工具比较；AI 方法可能提供更准确的复合物结构
- **核心假设**：AlphaFold3 对植物 bZIP/GATA TF–DNA 复合物的结构预测精度高于经典 docking
- **相对本文的增量**：为「TF–DNA 结构预测」提供方法学选择依据
- **初步方法**：收集植物 bZIP/GATA TF–DNA 复合物实验结构（如 PDB），用 AlphaFold3 和 docking 分别预测，比较界面残基和复合物 RMSD
- **验证方式**：用本文的 VvHYH–G-box 和 VvGATA24–GATA-box 作为测试集，SPR 突变数据（如有）验证
- **可能的失败模式**：AlphaFold3 对无同源模板的 TF–DNA 复合物预测精度有限
- **创新状态**：unverified

### 候选 5：光信号→TF 激活的「上游信号传导 + 染色质动态」整合模型
- **名称**：Light-to-Wax Signaling Cascade Model
- **来源局限/观察**：本文证明了光照→TF→靶基因的调控，但未涉及光受体、激酶等上游信号如何传递至 VvHYH/VvGATA24
- **核心假设**：光信号通过光受体（如 phytochrome/cryptochrome）→ 激酶级联 → TF 磷酸化/核定位变化 → 染色质开放 → 靶基因激活
- **相对本文的增量**：将本文的「TF–靶基因」模块嵌入完整信号通路
- **初步方法**：用磷酸化蛋白组学 + 核质分离实验 + ATAC-seq 时间序列，构建信号传导模型
- **验证方式**：用激酶抑制剂或光受体突变体验证通路必要性
- **可能的失败模式**：信号通路存在冗余，单基因扰动表型不明显
- **创新状态**：unverified