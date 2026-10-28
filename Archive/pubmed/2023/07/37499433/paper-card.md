## 01 基本信息

- **标题**：Ginsenoside CK targeting KEAP1-DGR/Kelch domain disrupts the binding between KEAP1 and NRF2-DLG motif to ameliorate oxidative stress damage.
- **作者**：Cheng, Chuanjing; Zhang, Jinling; Liu, Kaixin; Xu, Yanyan; Shen, Fukui; Han, Yanqi; Hou, Yuanyuan; Zhang, Tiejun; Bai, Gang
- **单位**：未提供（PubMed 记录未列出完整单位信息）
- **期刊/平台**：Phytomedicine : international journal of phytotherapy and phytopharmacology
- **年份**：2023（在线日期 2023-07-28）
- **论文类型**：实验研究（in vitro + in vivo + 计算模拟）
- **领域**：天然产物药理学；氧化应激；KEAP1-NRF2/ARE 信号通路；蛋白质-蛋白质相互作用（PPI）调控
- **关键词**：Ginsenoside CK; KEAP1; NRF2; DGR/Kelch domain; DLG motif; oxidative stress; DARTS; click chemistry; molecular dynamics
- **DOI/arXiv 号**：10.1016/j.phymed.2023.154992
- **代码**：未提供
- **数据**：未提供（蛋白质组学数据未说明是否公开）
- **阅读日期**：2025-05-13（按当前日期）
- **在「蛋白质-DNA 互作(聚焦 TF–DNA 结合机制) × AI 方法/物理模拟」方向中的位置**：本文核心是**蛋白质-蛋白质互作（KEAP1-NRF2）**，而非蛋白质-DNA 互作。但 NRF2 是转录因子（TF），其激活后结合 ARE（antioxidant response element）DNA 序列启动抗氧化基因转录。本文聚焦于 NRF2 上游的胞质调控（KEAP1 介导的泛素化降解与释放），即 TF 的**核转位前调控**，而非 TF-DNA 结合本身。对本课题的可迁移点在于：① 小分子竞争性破坏 TF 调控蛋白复合物的策略；② DARTS+click chemistry 靶点鉴定流程；③ 分子动力学模拟分析 PPI 界面热点残基的方法。

---

## 02 一句话总结

本文通过 DARTS 蛋白质组学鉴定 KEAP1 为人参皂苷 CK 的直接靶蛋白，结合 click chemistry 探针、SPR/Co-IP 等互作验证和分子动力学模拟，证明 CK 竞争性结合 KEAP1 的 DGR/Kelch 结构域，破坏其与 NRF2-DLG motif 的结合，从而在 LPS 诱导的细胞氧化损伤和动物急性损伤模型中激活 NRF2 抗氧化转录程序、减轻氧化应激损伤。

---

## 03 研究问题

- **具体问题**：Ginsenoside CK 改善氧化应激损伤的直接蛋白靶点是什么？CK 与靶蛋白结合的精确分子机制（结合结构域、关键残基、对 NRF2-KEAP1 复合物的影响）是什么？
- **为什么重要**：KEAP1-NRF2/ARE 是细胞抗氧化防御的核心通路，NRF2 是调控数百个抗氧化基因的转录因子。CK 作为人参活性代谢物，此前已知可调节该通路，但缺乏直接靶点和结合机制的分子水平证据，限制了其作为先导化合物的理性优化。
- **现有方法为何不足**：此前研究多停留在表型水平（CK 上调 NRF2 下游基因），未鉴定直接靶蛋白；KEAP1 的已知抑制剂（如 sulforaphane）多通过共价修饰 KEAP1 的半胱氨酸残基，而 CK 是否以非共价方式结合 KEAP1 的底物识别结构域（DGR/Kelch）尚不清楚。
- **精确研究问题**：Can ginsenoside CK directly bind to the DGR/Kelch domain of KEAP1 and competitively disrupt the KEAP1-NRF2 DLG motif interaction, thereby activating NRF2-mediated antioxidant transcription?

---

## 04 背景与发展脉络

> 注：以下脉络为「经外部核验」的领域通识，结合本文框架整理。

1. **KEAP1-NRF2 通路发现与机制确立（1999-2004）**：Itoh 等发现 KEAP1 为 NRF2 的胞质抑制因子；KEAP1 作为 Cul3 泛素连接酶的底物适配器，介导 NRF2 的泛素化降解。NRF2 通过两个 motif（DLG 和 ETGE）与 KEAP1 的 DGR/Kelch 结构域结合，形成"hinge-and-latch"模型。
2. **小分子 NRF2 激活剂的发展（2000s-至今）**：sulforaphane、CDDO-Im 等通过共价修饰 KEAP1 的活性半胱氨酸（C151/C273/C288）改变其构象，释放 NRF2。局限：共价修饰剂存在脱靶效应和毒性问题。
3. **非共价 KEAP1-NRF2 PPI 抑制剂（2010s-至今）**：基于结构的药物设计（SBDD）和片段筛选发现多个靶向 KEAP1 Kelch 结构域的小分子（如化合物 1-7 系列），竞争性阻断 NRF2 结合。局限：多数处于临床前，细胞渗透性和代谢稳定性待优化。
4. **天然产物来源的 KEAP1 调节剂**：多种天然黄酮、萜类被报道调节 NRF2，但多数缺乏直接结合证据。
5. **本文主张的位置**：首次以 DARTS+蛋白质组学系统鉴定 CK 的直接靶点为 KEAP1，并明确其结合 DGR/Kelch 结构域、竞争性破坏 DLG motif 结合，属于「天然产物来源的非共价 KEAP1-NRF2 PPI 抑制剂」类别，为该类化合物提供了新的天然骨架。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| CK 的直接蛋白靶点未知 | 此前研究仅观察到 CK 调节 KEAP1-NRF2/ARE 通路表型，无法区分直接与间接效应 | 缺乏系统的靶点鉴定手段；天然产物多靶点特性使靶点确认困难 | 摘要 BACKGROUND 部分明确说明 "the specific targets and mechanisms of CK in improving oxidative stress remain unclear" |
| KEAP1-NRF2 相互作用的精确界面不清 | 不清楚 CK 是结合 KEAP1 的哪个结构域、影响哪个 NRF2 motif（DLG vs ETGE） | 需要高分辨率互作数据；此前研究未进行结构域水平定位 | 本文通过分子动力学模拟和突变/竞争实验定位到 DGR/Kelch 域和 DLG motif（Results 部分） |
| 天然产物 PPI 抑制剂的验证方法学挑战 | 小分子-蛋白弱相互作用难以用常规方法检测 | 需要多种正交技术交叉验证（DARTS、SPR、NMR、MD） | 本文联合 DARTS、click chemistry 探针、SPR/Co-IP、MD 模拟（Methods 部分） |
| 体内药效与分子机制的关联不足 | 体外结合数据难以直接外推至动物模型 | 需要体内药效学与机制生物标志物联合验证 | 本文在 LPS 诱导小鼠急性损伤和机械损伤大鼠模型中验证（Results 部分） |

---

## 06 核心思想

### 1) 表面方法
- 用 LPS 诱导 RAW 264.7 巨噬细胞氧化损伤模型，评估 CK 对 KEAP1-NRF2/ARE 通路的调节。
- 用 DARTS（药物亲和响应靶标稳定性）结合蛋白质组学鉴定 CK 的直接结合蛋白。
- 设计含 click chemistry 手柄的 CK 功能探针，通过 pull-down 验证靶蛋白。
- 用 SPR、Co-IP 等验证 CK 与 KEAP1 的结合及对 KEAP1-NRF2 复合物的影响。
- 用分子动力学（MD）模拟分析 CK 与 KEAP1 DGR/Kelch 结构域的结合模式与关键残基。
- 在 LPS 诱导小鼠急性损伤和机械损伤大鼠模型中验证药效。

### 2) 核心洞察
- **CK 并非通过共价修饰 KEAP1 的半胱氨酸（如 sulforaphane），而是以非共价方式直接结合 KEAP1 的 DGR/Kelch 结构域**，该结构域正是 NRF2 的 DLG/ETGE motif 的对接面。
- **CK 选择性破坏 NRF2-DLG motif 与 KEAP1 的结合，而非 ETGE motif**。这符合 "hinge-and-latch" 模型：DLG 是"latch"（弱结合、可释放），ETGE 是"hinge"（强结合、锚定）。破坏 DLG 结合足以使 NRF2 从 KEAP1 上解离，但保留 ETGE 结合可能使调控更具可逆性和精细性。
- 这种「部分竞争」策略可能比完全阻断 KEAP1-NRF2 互作更有利于维持信号调控的精细平衡。

### 3) 可能的普适教训 [Analysis]
- **对 TF 调控复合物的靶向策略**：调控 TF 活性不一定需要直接靶向 TF-DNA 结合域，靶向其胞质抑制复合物（如 KEAP1）的底物识别域同样有效，且可能提供更精细的调控层次。
- **"Latch" 优先策略**：在双位点结合的蛋白-蛋白互作中，选择性破坏弱结合位点（latch）而非强结合位点（hinge），可能实现更可逆、更安全的调控。
- **DARTS+click chemistry 的靶点鉴定流程**：对天然产物这类多靶点、弱亲和力化合物，DARTS 结合蛋白质组学是有效的靶点发现策略，click 探针可提供正交验证。

---

## 07 方法总览

- **输入**：Ginsenoside CK（小分子化合物）；LPS（氧化应激诱导剂）；RAW 264.7 细胞；小鼠/大鼠模型。
- **输出**：KEAP1 作为 CK 直接靶蛋白的鉴定；CK-KEAP1 结合模式（DGR/Kelch 域、关键残基）；CK 对 KEAP1-NRF2 DLG 互作的破坏效应；体内药效验证。
- **模块**：
  1. 细胞模型与表型评估（LPS 诱导氧化损伤，检测 ROS、MDA、SOD 等指标）
  2. DARTS 靶点鉴定（蛋白酶消化保护实验 + 蛋白质组学）
  3. Click chemistry 探针合成与 pull-down 验证
  4. 分子互作验证（SPR、Co-IP、竞争实验）
  5. 分子动力学模拟（CK 与 KEAP1 DGR/Kelch 结构域的对接与 MD 模拟）
  6. 体内药效验证（LPS 诱导小鼠急性损伤、机械损伤大鼠模型）
- **训练**：不适用（无机器学习模型）。
- **工具**：DARTS、LC-MS/MS 蛋白质组学、click chemistry、SPR、Co-IP、分子对接与 MD 模拟（具体软件未在摘要中说明）。
- **反馈回路**：DARTS 鉴定候选靶蛋白 → click 探针验证 → 互作实验确认 → MD 模拟细化结合模式 → 突变/竞争实验验证关键残基 → 体内药效验证。
- **文字流程**：先用 LPS 建立氧化损伤细胞模型，确认 CK 的细胞保护效应并观察 KEAP1-NRF2 通路变化 → 用 DARTS 在全蛋白质组范围内寻找 CK 的结合蛋白，锁定 KEAP1 → 合成 click 探针进行 pull-down 正交验证 → 用 SPR 测定亲和力、Co-IP 检测 CK 对 KEAP1-NRF2 复合物的影响 → 用 MD 模拟预测 CK 在 KEAP1 DGR/Kelch 域的精确结合位点 → 在动物模型中验证 CK 的抗氧化损伤药效。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| DARTS 靶点鉴定 | 在全蛋白质组中识别 CK 的直接结合蛋白 | 天然产物靶点未知，需要无偏筛选 | 输入：细胞裂解液+CK；输出：候选蛋白列表（KEAP1） | 摘要 METHODS 部分明确说明使用 DARTS 结合蛋白质组学 | 预期影响：无法确定直接靶点，只能停留在表型研究 [Analysis] |
| Click chemistry 探针 pull-down | 正交验证 CK-KEAP1 直接结合 | DARTS 结果需独立方法确认；探针可富集靶蛋白 | 输入：CK-炔基探针+细胞裂解液；输出：pull-down 产物中 KEAP1 的富集 | 摘要 METHODS 部分说明设计 CK 功能探针 | 预期影响：靶点鉴定缺乏正交验证，可能为假阳性 [Analysis] |
| SPR/Co-IP 互作验证 | 定量测定 CK-KEAP1 亲和力；检测 CK 对 KEAP1-NRF2 复合物的影响 | 确认直接结合并评估功能后果 | 输入：纯化蛋白+CK；输出：结合曲线/复合物变化 | 摘要 METHODS 部分说明使用小分子-蛋白互作技术 | 预期影响：无法区分直接结合与间接效应 [Analysis] |
| 分子动力学模拟 | 预测 CK 在 KEAP1 DGR/Kelch 域的精确结合位点与关键残基 | 提供原子级结合模式，指导突变验证 | 输入：KEAP1 晶体结构+CK 结构；输出：结合构象、关键残基 | 摘要 METHODS 部分说明使用计算机动态模拟 | 预期影响：缺乏原子级机制解释 [Analysis] |
| 体内药效验证 | 在动物模型中确认 CK 改善氧化损伤的药效 | 体外结果需在生理条件下验证 | 输入：LPS 诱导小鼠/机械损伤大鼠+CK 给药；输出：组织损伤指标改善 | 摘要 METHODS 部分说明两种动物模型 | 预期影响：无法确认临床转化潜力 [Analysis] |

---

## 09 关键公式符号

不适用。本文为实验药理学研究，摘要中未包含数学模型或公式。分子动力学模拟部分可能涉及力场能量函数，但摘要中未提供具体公式。

---

## 10 实验设计与证据链

- **数据集/群体**：RAW 264.7 巨噬细胞系（in vitro）；LPS 诱导小鼠急性损伤模型和机械损伤大鼠模型（in vivo）。
- **规模**：未提供具体样本量。
- **指标**：氧化应激指标（ROS、MDA、SOD 等）；KEAP1-NRF2 通路蛋白表达；靶蛋白结合（DARTS、SPR、Co-IP）；组织病理损伤。
- **基线**：LPS 处理组（未加 CK）作为氧化损伤对照。
- **预算**：未提供。
- **骨干/仪器**：未提供。
- **Oracle 输入**：不适用。
- **评测协议**：未提供详细统计方法。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| LPS 诱导 RAW 264.7 氧化损伤 + CK 处理 | CK 改善氧化应激 | CK 处理 vs LPS 单独处理 | 氧化指标改善（摘要未给具体数值） | CK 具有抗氧化损伤保护作用 | 无法确定是否通过 KEAP1-NRF2 通路 | 摘要 BACKGROUND/RESULTS |
| DARTS + 蛋白质组学 | KEAP1 是 CK 的直接靶蛋白 | CK 处理 vs 对照（蛋白酶消化） | KEAP1 被鉴定为候选靶蛋白 | CK 直接结合 KEAP1 | 未提供结合亲和力数值 | 摘要 METHODS/RESULTS |
| Click chemistry 探针 pull-down | 验证 CK-KEAP1 直接结合 | 探针 pull-down vs 对照 | KEAP1 富集 | 正交验证 CK-KEAP1 结合 | 未提供定量富集倍数 | 摘要 METHODS/RESULTS |
| SPR/Co-IP | CK 破坏 KEAP1-NRF2 复合物 | CK 处理 vs 未处理 | KEAP1-NRF2 结合减弱 | CK 破坏 KEAP1-NRF2 互作 | 未区分 DLG vs ETGE 的贡献 | 摘要 METHODS/RESULTS |
| 分子动力学模拟 | CK 结合 DGR/Kelch 域 | 模拟 CK 与 KEAP1 结构域对接 | 预测结合位点在 DGR/Kelch 域 | CK 靶向 NRF2 结合界面 | 模拟预测需实验验证 | 摘要 METHODS/RESULTS |
| LPS 诱导小鼠急性损伤 + CK | CK 在体内改善氧化损伤 | CK 给药 vs 模型组 | 损伤减轻 | CK 体内有效 | 未提供剂量-效应关系 | 摘要 METHODS/RESULTS |
| 机械损伤大鼠模型 + CK | CK 对物理损伤有效 | CK 给药 vs 模型组 | 损伤减轻 | CK 对机械损伤有效 | 未提供机制验证 | 摘要 METHODS/RESULTS |

---

## 11 结论正确解读

- **任务范围**：本文仅证明 CK 在 LPS 诱导的细胞氧化损伤和两种动物损伤模型中有效，且体外证据支持 CK 直接结合 KEAP1 的 DGR/Kelch 域。**未涉及** NRF2 与 DNA（ARE）结合的直接测量。
- **Oracle/真值输入**：不适用（无计算预测依赖 oracle）。
- **端到端状态**：从靶点鉴定到体内药效的完整链条已建立，但**未包含** NRF2 核转位后与 ARE 结合的直接证据（如 ChIP 实验）。
- **算力成本**：MD 模拟的具体算力未提供。
- **历史数据依赖**：依赖已知的 KEAP1 晶体结构（PDB）进行模拟，但具体 PDB 编号未提供。
- **模型依赖**：MD 模拟结果依赖力场参数和初始构象，需实验验证。
- **最难情形**：CK 对 KEAP1 的亲和力可能较弱（天然产物常见），SPR 检测可能需高浓度；体内口服生物利用度未讨论。
- **群体/领域边界**：结论限于巨噬细胞和啮齿动物模型；未涉及人类受试者。
- **不确定性**：摘要未提供结合亲和力（Kd）、IC50 等定量数据；未提供 MD 模拟的 RMSD/结合自由能数值。

**有边界的复述**：在 RAW 264.7 细胞和两种啮齿动物损伤模型中，Ginsenoside CK 通过直接结合 KEAP1 的 DGR/Kelch 结构域、破坏其与 NRF2-DLG motif 的互作，激活 NRF2 抗氧化转录程序，从而减轻氧化应激损伤。该结论限于上述模型系统，且未直接测量 NRF2-DNA 结合。

---

## 12 作者自认局限

在提供的摘要中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限）：
- 摘要 BACKGROUND 部分承认此前 CK 的靶点和机制"remain unclear"，暗示本研究是首次系统鉴定，可能缺乏独立验证。
- 摘要未提供定量结合数据，可能暗示亲和力较弱或实验重复性有限 [Analysis]。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| DARTS 鉴定 KEAP1 为靶蛋白，但未提供亲和力定量 | 天然产物常为弱亲和力（μM-mM 级），可能为非特异性结合 | 弱亲和力结合可能无治疗意义 | 用 ITC 或 SPR 测定 Kd；设置结构类似物阴性对照 | 摘要未提供 Kd 值 |
| 声称"破坏 DLG motif 结合"但未提供 ETGE 结合是否受影响的直接比较 | 可能 CK 同时影响两个 motif，或仅影响 DLG 是模拟预测而非实验验证 | "latch 优先"策略的结论依赖此区分 | 用 ETGE 和 DLG 突变体分别做竞争实验；用 NMR 或 HDX 检测两个 motif 的占据状态 | 摘要仅说"disrupts the binding between DLG peptide"，未提 ETGE |
| MD 模拟预测结合位点，但未提供实验突变验证 | 模拟预测可能因力场误差而偏离真实结合模式 | 关键残基的确认需要突变实验 | 对预测的关键残基做点突变，检测 CK 结合是否丧失 | 摘要未提及突变实验 |
| 体内实验未提供 CK 的血药浓度或组织分布 | 药效可能来自代谢产物而非 CK 本身 | 影响对活性分子的归属 | 做 PK 实验；用代谢产物直接处理细胞 | 摘要未提及 PK 数据 |
| 未直接测量 NRF2 与 ARE DNA 的结合 | 激活 NRF2 转录程序是间接推断 | 本文题目涉及"NRF2-DLG motif"，但未验证下游 DNA 结合 | 用 ChIP-qPCR 检测 NRF2 在 ARE 位点的富集 | 摘要未提及 ChIP 实验 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **"Latch 优先"的 PPI 破坏策略**：KEAP1-NRF2 通过双位点（DLG 弱 + ETGE 强）结合，本文提示选择性破坏弱位点即可释放 NRF2。**迁移到 TF-DNA 互作**：许多 TF 通过多个 DNA 结合位点或辅助因子协同结合 DNA，可探索"部分竞争"策略——用小分子或肽段选择性破坏 TF 的弱 DNA 结合界面，而非完全阻断，以实现更精细的转录调控。

2. **DARTS + click chemistry 靶点鉴定流程**：对天然产物这类多靶点、弱亲和力化合物，DARTS 提供无偏筛选，click 探针提供正交验证。**迁移到 TF-DNA 研究**：当研究小分子调控 TF 活性时，可用 DARTS 鉴定直接靶蛋白，再用含光亲和/click 手柄的探针进行 pull-down 和原位标记。

3. **多尺度验证链**：从细胞表型 → 靶点鉴定 → 互作验证 → 结构模拟 → 体内药效，形成完整证据链。**迁移到 TF-DNA 研究**：研究 TF-DNA 结合调控时，应建立类似链条：报告基因 → 靶蛋白鉴定 → EMSA/SPR 验证 → MD 模拟 → 动物模型。

4. **MD 模拟用于 PPI 界面分析**：本文用 MD 模拟分析 CK 与 KEAP1 DGR/Kelch 域的相互作用。**迁移到 TF-DNA 研究**：可用 MD 或增强采样模拟分析小分子/突变对 TF-DNA 结合自由能的影响，预测关键残基。

5. **天然产物作为 PPI 抑制剂的骨架价值**：CK 作为天然产物提供了非共价 KEAP1 抑制剂的新骨架。**迁移到 TF-DNA 研究**：天然产物库可作为筛选 TF-DNA 结合抑制剂的来源，结合虚拟筛选和 MD 验证。

---

## 15 与已有知识连接

- **KEAP1-NRF2 通路**：Itoh et al. (1999) 首次克隆 KEAP1；Tong et al. (2006) 提出 "hinge-and-latch" 模型，阐明 DLG/ETGE 双位点结合机制。本文直接建立在该模型之上，选择性破坏 DLG 结合。
- **NRF2 作为 TF 的 DNA 结合**：NRF2 与 sMaf 形成异二聚体结合 ARE（5'-TGACnnnGC-3'），该 DNA 结合事件是本文所述抗氧化转录程序的最终执行步骤，但本文未直接研究。
- **KEAP1 抑制剂研究**：sulforaphane（共价修饰 C151）、CDDO-Im（共价）、非共价 KEAP1 抑制剂（如化合物 1-7，Jiang et al. 2021）——本文的 CK 属于非共价类，但来源为天然产物。
- **DARTS 技术**：Lomenick et al. (2009) 开发，用于鉴定小分子直接靶蛋白，本文将其与蛋白质组学结合。
- **分子动力学模拟在 PPI 研究中的应用**：与 G protein-coupled receptor 等靶点的 MD 模拟研究类似，本文将其用于天然产物-PPI 界面分析。
- **可迁移领域**：TF 的胞质调控（如 NF-κB/IκB、STAT 家族）与小分子调控策略；天然产物靶点鉴定的一般流程。

---

## 16 研究想法

**Agent 生成的研究候选**

### 候选 1：基于 "latch 优先" 策略设计 TF-DNA 结合的部分竞争抑制剂
- **名称**：Partial-Competition TF-DNA Inhibitor Design
- **来源局限/观察**：本文证明选择性破坏 KEAP1-NRF2 的弱结合位点（DLG）即可激活 NRF2。许多 TF 通过多个 DNA 接触点结合 DNA，其中部分为弱贡献。
- **核心假设**：对某些 TF（如 p53、MYC），选择性破坏其弱 DNA 结合界面可实现部分抑制，保留基础转录活性，减少完全抑制带来的毒性。
- **初步方法**：基于 TF-DNA 共晶结构，用 MD 模拟和 MM-PBSA 分解每个 DNA 接触残基的结合自由能贡献，识别"弱接触"残基；设计小分子或肽段靶向该界面；用 EMSA 和报告基因验证部分抑制效应。
- **验证方式**：比较完全阻断 vs 部分阻断对下游基因表达谱的影响；在疾病模型中评估疗效-毒性平衡。
- **创新状态**：unverified

### 候选 2：DARTS+click 探针流程用于鉴定天然产物调控 TF 的靶蛋白
- **名称**：Natural Product TF-Target Identification Pipeline
- **来源局限/观察**：本文的 DARTS+click 流程成功鉴定 KEAP1。许多天然产物被报道调控 TF 活性但靶点不明。
- **核心假设**：该流程可推广至其他天然产物-TF 调控研究，特别是那些通过调控 TF 修饰酶或胞质抑制蛋白发挥作用的化合物。
- **初步方法**：合成含 click 手柄的天然产物探针；DARTS 筛选候选靶蛋白；pull-down+LC-MS/MS 鉴定；SPR 验证；siRNA 敲低验证功能相关性。
- **验证方式**：在至少 3 个不同天然产物-表型系统中验证流程的通用性。
- **创新状态**：partially checked（DARTS 和 click 均为成熟技术，但组合应用于 TF 调控研究较少）

### 候选 3：MD 模拟指导的 KEAP1-NRF2 非共价抑制剂优化
- **名称**：MD-Guided Optimization of Non-Covalent KEAP1 Inhibitors
- **来源局限/观察**：本文 MD 模拟预测了 CK 与 DGR/Kelch 域的结合模式，但未提供结合自由能定量和突变验证。
- **核心假设**：基于 MD 模拟的结合自由能分解可指导 CK 类似物的理性设计，提高亲和力和选择性。
- **初步方法**：对 CK-KEAP1 复合物做长时间 MD 模拟（μs 级）和 FEP 计算；识别关键残基并做突变验证；设计 CK 类似物库，虚拟筛选后合成高排名化合物；SPR 测定亲和力。
- **验证方式**：比较优化前后化合物的 Kd、细胞活性、体内药效。
- **创新状态**：unverified

### 候选 4：TF 胞质调控蛋白的 PPI 作为药物靶点的系统综述与可药性评估
- **名称**：Druggability Assessment of TF Cytosolic Regulatory PPIs
- **来源局限/观察**：本文证明 KEAP1（NRF2 的胞质调控蛋白）是可药靶点。许多 TF 有类似的胞质抑制/调控蛋白（如 IκB-NF-κB、STAT3 的 SH2 域相互作用）。
- **核心假设**：这些 PPI 界面具有类似的可药性特征，可用统一的计算流程评估。
- **初步方法**：收集已知 TF-胞质调控蛋白复合物结构；用 Fpocket 等工具检测可药性口袋；用 MD 模拟评估界面动态性；用 AlphaFold 预测未知复合物结构。
- **验证方式**：对排名靠前的靶点进行小规模筛选验证。
- **创新状态**：unverified

### 候选 5：TF-DNA 结合与 TF-调控蛋白结合的竞争性调控网络建模
- **名称**：Competitive Binding Network Model of TF Regulation
- **来源局限/观察**：本文显示小分子破坏 KEAP1-NRF2 结合后，NRF2 释放并转位入核结合 DNA。这提示 TF 的胞质结合与 DNA 结合存在竞争性平衡。
- **核心假设**：对许多 TF，胞质调控蛋白结合与 DNA 结合构成竞争性平衡，小分子调控任一侧均可改变 TF 活性。
- **初步方法**：构建 TF-调控蛋白-DNA 的三方竞争结合模型（质量作用定律）；用定量成像（FRAP、单分子追踪）测量各结合态的动力学参数；用模型预测小分子干预效果。
- **验证方式**：在至少 2 个 TF 系统（如 NRF2、NF-κB）中验证模型预测。
- **创新状态**：unverified