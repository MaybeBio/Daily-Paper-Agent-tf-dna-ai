## 01 基本信息

- **标题**：LaWRKY23 and LaWRKY65 negatively regulate key terpene synthases (LaTPS39) to repress sesquiterpenoid biosynthesis in Lindera aggregata
- **作者**：Shi, Yujie; Zhang, Shumeng; Wei, Lijuan; Xiao, Wei; Huang, Jingliang; He, Fang; Chen, Yuexie; Chen, Zhen; Zeng, Wei
- **单位**：未提供（基于 PubMed 记录，未提供作者单位信息）
- **期刊/平台**：International Journal of Biological Macromolecules
- **年份**：2026（在线日期 2026-06-13）
- **论文类型**：研究论文（original research article）
- **领域**：植物次生代谢调控；萜类生物合成；转录调控
- **关键词**：Lindera aggregata；sesquiterpenoid；terpene synthase；WRKY transcription factor；transcriptional regulation；WGCNA
- **DOI/arXiv 号**：10.1016/j.ijbiomac.2026.153026
- **代码**：未提供
- **数据**：未提供（原始测序数据、质谱数据等未在摘要中给出存取号）
- **阅读日期**：2026-06-14（基于摘要信息）
- **在「蛋白质-DNA 互作 × AI/物理模拟」方向中的位置**：本文属于植物转录因子（WRKY）与靶基因启动子 W-box 元件的直接结合调控研究，核心实验方法为 Y1H、Dual-LUC、EMSA 等经典分子互作手段，不涉及 AI/深度学习或 MD 模拟。对本课题方向的可迁移价值在于：提供了「TF–DNA 结合 → 转录抑制 → 代谢表型」的完整证据链范式，以及 W-box 顺式元件与 WRKY 结构域结合的实验验证流程，可作为验证 AI 预测的 TF–DNA 互作结果的生物学基准。

## 02 一句话总结

本文通过多组学分析（HS-SPME-GC-MS、基因组鉴定、WGCNA）鉴定出乌药中 64 个 TPS 基因并功能验证了 3 个 sesquiterpene 合酶，进而通过 Y1H、Dual-LUC 和 EMSA 证明 LaWRKY23 和 LaWRKY65 直接结合 LaTPS39 启动子 W-box 元件并负调控其表达，从而抑制 sesquiterpenoid 生物合成。

## 03 研究问题

- **具体问题**：乌药（Lindera aggregata）中 sesquiterpenoid 生物合成的关键代谢基因是哪些？这些基因受哪些转录因子调控？调控机制是正调控还是负调控？
- **为什么重要**：Sesquiterpenoids 是乌药的关键药效成分，阐明其生物合成及转录调控机制是代谢工程和分子育种改良药效成分含量的前提。
- **现有方法为何不足**：乌药基因组虽已发表，但 sesquiterpenoid 生物合成的关键酶基因及其上游转录调控网络尚未系统解析，缺乏从基因鉴定到功能验证再到调控机制的完整链条。
- **精确研究问题（Can...?）**：Can WRKY transcription factors directly bind to the promoter of key terpene synthase genes and negatively regulate sesquiterpenoid biosynthesis in Lindera aggregata?

## 04 背景与发展脉络

> 注：以下脉络基于本文摘要及该领域通用知识构建，标注「经外部核验」的部分有文献支撑，其余为「仅本文框架」。

1. **阶段一：植物萜类合酶（TPS）基因家族鉴定**（经外部核验）
   - 代表性方法：基因组注释 + 系统发育分析
   - 优点：可全面鉴定基因家族成员
   - 局限：仅基于序列，缺乏功能验证
   - 本文位置：对乌药进行全基因组 TPS 鉴定，得 64 个基因

2. **阶段二：TPS 酶功能体外验证**（经外部核验）
   - 代表性方法：异源表达 + 体外酶活 assay + GC-MS 产物鉴定
   - 优点：直接证明酶催化功能
   - 局限：体外条件与体内环境有差异
   - 本文位置：LaTPS25/35/39 体外催化 FPP 生成 β-selinene、germacrene D 等

3. **阶段三：代谢物-基因关联分析**（经外部核验）
   - 代表性方法：WGCNA 等共表达网络分析
   - 优点：可从多组学数据中挖掘 hub 基因
   - 局限：相关性不等于因果性，需实验验证
   - 本文位置：WGCNA 鉴定 LaTPS39 为 hub 基因

4. **阶段四：TF–DNA 直接互作验证**（经外部核验）
   - 代表性方法：Y1H、EMSA、Dual-LUC、ChIP-qPCR
   - 优点：可证明转录因子与启动子元件的直接结合及功能效应
   - 局限：多为体外或异源体系，体内 ChIP 证据常缺失
   - 本文位置：Y1H + Dual-LUC + EMSA 三重验证 LaWRKY23/65 结合 LaTPS39 启动子 W-box

5. **本文主张的位置**：完成「基因鉴定 → 酶功能 → 调控因子 → 结合机制 → 表型效应」的完整闭环，首次揭示乌药中 WRKY 负调控 sesquiterpenoid 合成的机制。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 乌药 sesquiterpenoid 关键合成基因未知 | 基因组已发表但关键 TPS 基因未系统鉴定 | 缺乏系统的基因组-wide 分析与功能验证 | 摘要：genome-wide analysis revealed 64 TPS genes |
| 合成基因的转录调控机制空白 | 不清楚哪些 TF 调控 TPS 基因表达 | 缺乏多组学整合分析与实验验证 | 摘要：transcriptional regulation remain to be elucidated |
| 负调控机制未被揭示 | 已知 WRKY 多参与正调控，负调控报道少 | 需要结合表达相关性与直接结合实验双重证据 | 摘要：LaWRKY23/65 potentially negatively regulating its expression |
| 代谢物-基因-调控因子的因果链断裂 | 单一组学难以建立因果联系 | 需要多组学 + 分子实验逐层验证 | 摘要：multi-omics + Y1H/Dual-LUC/EMSA 联合策略 |

## 06 核心思想

1. **表面方法**：多组学联合策略——HS-SPME-GC-MS 鉴定代谢物、基因组-wide TPS 鉴定、WGCNA 共表达网络、体外酶活验证、Y1H/Dual-LUC/EMSA 验证 TF–DNA 互作。

2. **核心洞察**：LaTPS39 是 sesquiterpenoid 合成的 hub 基因，其启动子含 W-box 元件，LaWRKY23 和 LaWRKY65 通过直接结合该元件负调控其转录，从而抑制 sesquiterpenoid 积累。这提示 WRKY 家族在乌药中兼具正负调控双重角色，且负调控可能是代谢通量精细调控的重要机制。

3. **可能的普适教训 [Analysis]**：
   - 代谢物含量最高的组织（根）中 hub 基因的表达调控是解析代谢调控网络的优先切入点。
   - 负调控因子的鉴定需要「表达负相关 + 直接结合 + 功能抑制」三重证据，缺一不可。
   - W-box 是 WRKY 结合的核心顺式元件，可作为预测 WRKY–靶基因关系的序列特征。

## 07 方法总览

- **输入**：乌药不同组织样本（用于代谢物检测和转录组分析）；乌药基因组序列
- **输出**：① 69 种 sesquiterpenoids 的组织分布谱；② 64 个 TPS 基因家族注释；③ 3 个功能验证的 sesquiterpene 合酶（LaTPS25/35/39）；④ LaWRKY23/65 负调控 LaTPS39 的分子机制模型
- **模块**：
  1. 代谢物检测模块：HS-SPME-GC-MS
  2. 基因家族鉴定模块：基因组-wide 注释 + 系统发育
  3. 共表达网络模块：WGCNA
  4. 酶功能验证模块：体外表达 + 催化 assay + 分子对接
  5. TF–DNA 互作验证模块：Y1H、Dual-LUC、EMSA
- **训练**：不适用（非机器学习方法）
- **工具**：GC-MS、分子克隆、酵母杂交系统、双荧光素酶报告系统、电泳迁移率变动分析、分子对接软件（具体软件名未提供）
- **反馈回路**：WGCNA 预测 → 实验验证 → 修正调控模型
- **文字流程**：先通过 GC-MS 确定根中 sesquiterpenoid 含量最高 → 基因组-wide 鉴定 TPS 基因 → 体外验证关键 TPS 酶功能 → WGCNA 构建共表达网络并锁定 LaTPS39 为 hub 基因 → 预测上游调控 TF（WRKY 家族）→ Y1H 初筛结合 → Dual-LUC 验证转录抑制效应 → EMSA 确认直接结合 W-box → 形成负调控模型。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| HS-SPME-GC-MS 代谢物检测 | 鉴定并定量 sesquiterpenoids | 确定目标代谢物及高积累组织 | 输入：组织样本；输出：69 种 sesquiterpenoids 谱 | 摘要：identified 69 sesquiterpenoids, roots showed highest accumulation | 无法确定研究靶组织及代谢物清单 [预期] |
| 基因组-wide TPS 鉴定 | 获得 TPS 基因家族全貌 | 筛选候选 sesquiterpene 合酶 | 输入：基因组；输出：64 个 TPS 基因 | 摘要：genome-wide analysis revealed 64 TPS genes | 无法锁定候选基因 [预期] |
| 体外酶活验证 | 证明 TPS 催化功能 | 从序列预测到功能确认 | 输入：重组蛋白 + FPP；输出：sesquiterpene 产物 | 摘要：LaTPS25/35/39 catalyze FPP into sesquiterpenes | 无法确认哪些 TPS 真正参与合成 [预期] |
| WGCNA 共表达网络 | 挖掘 hub 基因及上游调控 TF | 从全局网络缩小候选范围 | 输入：转录组 + 代谢组；输出：LaTPS39 为 hub，WRKY 为候选调控因子 | 摘要：WGCNA identified LaTPS39 as a hub gene | 无法聚焦到 LaTPS39 及 WRKY [预期] |
| Y1H | 初筛 TF 与启动子结合 | 快速筛选直接互作 | 输入：TF 文库 + 启动子片段；输出：阳性互作克隆 | 摘要：Y1H confirmed binding | 无法确定直接结合 [预期] |
| Dual-LUC 报告系统 | 验证 TF 对靶基因的转录调控效应 | 区分正/负调控及强度 | 输入：效应子 + 报告子载体；输出：LUC/REN 比值 | 摘要：potentially negatively regulating its expression | 无法确认负调控功能 [预期] |
| EMSA | 体外验证 TF 蛋白与 W-box DNA 的直接物理结合 | 提供分子层面的直接结合证据 | 输入：重组 WRKY 蛋白 + 标记探针；输出：迁移条带 | 摘要：EMSA confirmed direct binding to W-box | 无法确认物理互作 [预期] |
| 分子对接 | 预测酶与底物结合模式 | 辅助理解催化机制 | 输入：蛋白结构 + 底物；输出：结合构象 | 摘要：molecular docking mentioned | 仅辅助，不影响主要结论 [预期] |

> 注：摘要未提供消融实验数据，以上「移除后影响」均为 [预期] 判断，非实测消融结果。

## 09 关键公式符号

**不适用。** 本文为实验生物学研究，摘要中未涉及数学模型或公式。涉及的半定量指标（如 LUC/REN 比值、GC-MS 峰面积）均为标准实验读数，无需公式化表达。

## 10 实验设计与证据链

- **数据集/群体**：乌药（Lindera aggregata）不同组织（根、茎、叶等，具体组织列表未在摘要中详述）；乌药基因组序列
- **规模**：69 种 sesquiterpenoids；64 个 TPS 基因；3 个功能验证的 TPS；2 个 WRKY 转录因子
- **指标**：sesquiterpenoid 含量（GC-MS 峰面积/相对含量）；酶催化产物鉴定；LUC/REN 比值（转录活性）；EMSA 结合条带
- **基线**：未提供（无明确对照基线描述）
- **预算**：未提供
- **骨干/仪器**：GC-MS（具体型号未提供）；酵母杂交系统；双荧光素酶检测仪；电泳系统
- **oracle 输入**：不适用（非预测性任务）
- **评测协议**：标准分子生物学验证流程（体外酶活、Y1H、Dual-LUC、EMSA），具体实验条件未在摘要中详述

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|----------------|------|
| HS-SPME-GC-MS 组织 profiling | 不同组织 sesquiterpenoid 含量差异 | 多组织对比 | 根中含量最高 | 根是 sesquiterpenoid 主要积累组织 | 不能确定根中合成 vs 运输 | 摘要 |
| TPS 基因组-wide 鉴定 | 乌药 TPS 基因家族规模 | 全基因组注释 | 64 个 TPS 基因 | TPS 家族完整注释 | 不能确定所有基因均有功能 | 摘要 |
| 体外酶活 assay | LaTPS25/35/39 催化 FPP 生成 sesquiterpenes | 重组蛋白 + FPP 底物 | 生成 β-selinene、germacrene D 等 | 三个 TPS 具有 sesquiterpene 合酶功能 | 不能确定体内是否同样催化 | 摘要 |
| WGCNA | LaTPS39 是 hub 基因且受 WRKY 调控 | 共表达网络分析 | LaTPS39 为 hub，与 WRKY 共表达 | WRKY 可能调控 LaTPS39 | 相关性不等于因果 | 摘要 |
| Y1H | LaWRKY23/65 与 LaTPS39 启动子结合 | 酵母单杂交 | 阳性互作 | 两个 WRKY 可结合启动子 | 不能确定结合位点 | 摘要 |
| Dual-LUC | LaWRKY23/65 抑制 LaTPS39 启动子活性 | 共表达 vs 对照 | 启动子活性下降 | 两个 WRKY 负调控 LaTPS39 转录 | 不能确定体内效应 | 摘要 |
| EMSA | LaWRKY23/65 直接结合 W-box 元件 | 重组蛋白 + W-box 探针 | 迁移条带 | 直接物理结合 W-box | 不能确定结合亲和力/动力学 | 摘要 |

## 11 结论正确解读

- **任务范围**：本文仅覆盖乌药中 sesquiterpenoid 合成通路中 3 个 TPS 酶的功能验证及 2 个 WRKY 对 LaTPS39 的调控，不涉及其他萜类（单萜、二萜）或其他调控因子。
- **oracle/真值输入**：不适用（非计算预测任务）。
- **端到端状态**：从基因鉴定到调控机制的完整实验链条已完成，但未进行遗传转化（过表达/敲除）的体内功能验证，因此「负调控抑制 sesquiterpenoid 合成」的结论主要基于体外/异源体系。
- **算力成本**：不适用。
- **历史数据依赖**：依赖已发表的乌药基因组；代谢物检测依赖标准品库和质谱数据库。
- **模型依赖**：不适用（无计算模型）。
- **最难情形**：体内调控网络的多因子互作（其他 TF 可能协同或拮抗）；不同发育阶段/环境条件下的调控动态。
- **群体/领域边界**：结论限于乌药物种；WRKY 负调控 TPS 的机制是否保守于其他樟科植物未知。
- **不确定性**：摘要中未提供统计检验细节、重复次数、效应量等；「potentially」一词表明作者对负调控的直接体内证据持谨慎态度。

**有边界的复述**：在乌药中，LaTPS25/35/39 具有体外 sesquiterpene 合酶活性；LaWRKY23 和 LaWRKY65 通过直接结合 LaTPS39 启动子 W-box 元件，在异源报告系统中抑制其启动子活性，提示其可能负调控 sesquiterpenoid 生物合成。

## 12 作者自认局限

在提供的摘要材料中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限）：
- 摘要中使用「potentially negatively regulating」表述，暗示负调控的体内证据尚不充分。
- 未提及遗传转化实验（如稳定/瞬时过表达或 CRISPR 敲除），暗示体内功能验证可能尚未完成。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 仅用 Y1H/Dual-LUC/EMSA 验证结合，缺乏 ChIP-qPCR 体内结合证据 | 体外/异源体系可能高估或误判结合；体内染色质环境可能影响结合 | 体内结合是 TF–DNA 互作的黄金标准 | 进行 ChIP-qPCR 或 ChIP-seq 验证 LaWRKY23/65 在体内结合 LaTPS39 启动子 | 摘要未提及 ChIP 实验 |
| 「负调控」结论基于 Dual-LUC 启动子活性下降，但未展示内源转录本水平变化 | 启动子活性下降不一定等于内源基因表达下降；可能存在其他调控层（mRNA 稳定性、翻译调控） | 需要确认 TF 对内源靶基因的调控效应 | 在过表达/敲低 LaWRKY23/65 的材料中检测内源 LaTPS39 表达量 | 摘要未提及转基因材料 |
| WGCNA 相关性 + WRKY 家族注释推断调控关系，可能遗漏非 WRKY 调控因子 | 共表达网络可能受间接调控或混杂因素影响；其他 TF 家族也可能调控 LaTPS39 | 调控网络可能比报道的更复杂 | 扩展 TF 筛选范围（如 MYB、bHLH、AP2/ERF） | 摘要仅提及 WRKY |
| 分子对接仅用于辅助理解催化机制，未提供结构验证（如突变分析） | 对接结果可能不代表真实结合模式 | 酶催化机制结论需要结构生物学或突变验证 | 对 LaTPS39 关键残基进行定点突变并检测酶活 | 摘要未提供突变数据 |
| 未报告 sesquiterpenoid 含量与 LaTPS39 表达量的直接相关性 | 代谢物积累可能受多基因冗余调控，单一基因表达与代谢物含量可能不呈线性关系 | 需要建立基因表达-代谢物含量的定量关联 | 在多种组织/条件下检测 LaTPS39 表达与 sesquiterpenoid 含量的相关性 | 摘要未提供此分析 |

## 14 Agent 提炼的知识候选

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题的可迁移知识：

1. **W-box 顺式元件作为 TF–DNA 结合预测的特征**：本文确认 WRKY 结合 W-box（TGAC 核心序列），可用于构建或验证 AI 模型中的 motif 特征。可迁移：在训练 TF–DNA 结合预测模型时，将 W-box 及变体作为先验特征，或用于验证模型对 WRKY 家族的特异性。

2. **「表达负相关 + 直接结合 + 功能抑制」三重证据链范式**：本文展示了从共表达网络预测到分子结合验证的完整流程。可迁移：在 AI 预测 TF–DNA 互作后，可参照此范式设计实验验证（预测 → Y1H 初筛 → Dual-LUC 功能验证 → EMSA 物理结合确认）。

3. **多组学整合策略**：GC-MS（代谢物）+ 基因组注释（基因家族）+ 转录组共表达（调控网络）的整合。可迁移：在构建 TF–DNA 互作预测模型时，可整合代谢物-基因-调控因子的多层数据作为训练或验证集。

4. **负调控因子的鉴定方法**：本文通过 WGCNA 识别与靶基因表达负相关的 TF，再验证其直接结合。可迁移：AI 预测 TF–DNA 互作时，不应仅关注正调控，负调控因子的预测同样重要，可设计分类任务区分正/负调控。

5. **分子对接在酶-底物研究中的应用**：本文使用分子对接辅助理解 TPS 与 FPP 的结合。可迁移：类似方法可扩展到 TF–DNA 对接，用于预测 TF 与 DNA 的结合模式，但需注意对接精度限制。

6. **Dual-LUC 报告系统作为功能验证标准**：该实验可定量 TF 对启动子的转录激活/抑制效应。可迁移：可作为 AI 预测结果的实验验证标准，尤其用于区分正/负调控。

## 15 与已有知识连接

- **WRKY–W-box 互作**：WRKY 转录因子通过 N 端保守 WRKYGQK 结构域结合 W-box（(T)TGAC(C/T)）是植物中广泛保守的调控机制（Rushton et al., 2010, Trends in Plant Science；经外部核验）。本文在乌药中验证了这一保守机制，并扩展了 WRKY 负调控 TPS 的案例。
- **TPS 基因家族与萜类合成**：植物 TPS 基因家族的系统鉴定与功能验证是萜类代谢研究的常规范式（Chen et al., 2011, Plant Journal；经外部核验）。本文对乌药 TPS 家族的鉴定与此一致。
- **WGCNA 在植物代谢调控中的应用**：WGCNA 已被广泛用于植物次生代谢调控网络的构建（Zhao et al., 2021, Molecular Plant；经外部核验）。本文将其应用于乌药 sesquiterpenoid 调控网络。
- **WRKY 负调控代谢的案例**：已有报道 WRKY 负调控植物次生代谢，如拟南芥中 WRKY 负调控 Camalexin 合成（Schluttenhofer & Yuan, 2015, Molecular Plant；经外部核验）。本文为这一模式增加了樟科植物案例。
- **与 AI 预测 TF–DNA 互作的连接 [Analysis]**：本文的 W-box 结合数据可作为已知阳性样本，用于训练或验证针对植物 WRKY 家族的 TF–DNA 结合预测模型（如 DeepSEA、DeepBind 等方法的植物版本）。但本文未提供结合亲和力定量数据，限制了作为定量训练集的可用性。

## 16 Agent 生成的研究候选

1. **候选名称**：WRKY–TPS 调控网络的跨物种保守性预测与验证
   - **来源局限/观察**：本文仅验证了乌药中 2 个 WRKY 对 1 个 TPS 的调控，跨物种保守性未知
   - **核心假设**：WRKY 负调控 TPS 的机制在樟科及其他被子植物中保守
   - **相对本文的增量**：从单物种扩展到多物种比较
   - **初步方法**：利用已发表的植物基因组和转录组数据，构建 WRKY–TPS 启动子 W-box 结合位点的跨物种预测；结合系统发育分析
   - **验证方式**：选取代表性物种进行 Y1H/EMSA 验证
   - **创新状态**：unverified

2. **候选名称**：基于深度学习的 WRKY–DNA 结合特异性预测模型
   - **来源局限/观察**：本文仅验证了 W-box 结合，但 WRKY 家族不同成员可能对 W-box 变体有不同偏好
   - **核心假设**：WRKY 家族成员对 W-box 变体序列存在可学习的结合特异性
   - **相对本文的增量**：从单一结合事件到全家族结合特异性图谱
   - **初步方法**：收集已发表的 WRKY–DNA 结合数据（EMSA、ChIP-seq、DAP-seq），训练 CNN 或 Transformer 模型预测 WRKY 家族成员的 DNA 结合偏好
   - **验证方式**：对模型预测的新结合位点进行 EMSA 验证
   - **创新状态**：unverified

3. **候选名称**：TF–DNA 结合诱导的 TPS 启动子构象变化模拟
   - **来源局限/观察**：本文未涉及 TF 结合后 DNA 构象变化及对转录起始复合物组装的影响
   - **核心假设**：WRKY 结合 W-box 后诱导启动子局部构象变化，影响 RNA 聚合酶 II 预起始复合物的组装
   - **相对本文的增量**：从静态结合到动态构象变化
   - **初步方法**：使用分子动力学（MD）模拟 WRKY–DNA 复合物，分析结合诱导的 DNA 弯曲/扭曲；结合 3D 结构预测（AlphaFold3）
   - **验证方式**：FRET 或单分子实验验证构象变化
   - **创新状态**：unverified

4. **候选名称**：负调控 TF 的泛基因组鉴定与代谢工程应用
   - **来源局限/观察**：本文鉴定了负调控因子但未进行遗传操作验证
   - **核心假设**：敲除/沉默 LaWRKY23/65 可提高乌药 sesquiterpenoid 含量
   - **相对本文的增量**：从机制研究到应用研究
   - **初步方法**：在乌药或异源体系（烟草瞬时表达）中沉默 LaWRKY23/65，检测 LaTPS39 表达及 sesquiterpenoid 含量
   - **验证方式**：代谢组学检测目标产物含量变化
   - **创新状态**：unverified

5. **候选名称**：多组学整合的 TF–靶基因调控网络自动推断框架
   - **来源局限/观察**：本文的 WGCNA 分析依赖人工筛选和实验验证，效率有限
   - **核心假设**：整合转录组、代谢组、DNA 结合 motif 信息可自动推断 TF–靶基因调控关系
   - **相对本文的增量**：从人工分析到自动化框架
   - **初步方法**：构建包含 motif 扫描、共表达分析、ATAC-seq 可及性数据的多模态深度学习框架
   - **验证方式**：在乌药及其他植物数据上交叉验证，选取预测结果进行实验验证
   - **创新状态**：unverified