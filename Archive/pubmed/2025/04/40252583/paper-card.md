## 01 基本信息

- **标题**：20(S)-ginsenoside Rg3 suppresses gastric cancer cell proliferation by inhibiting E2F-DP dimerization
- **作者**：Li, Fuqiang; Cai, Chengyu; Wang, Fei; Zhang, Na; Zhao, Qingzhi; Chen, Yuyang; Cui, Xueli; Wang, Siyang; Zhang, Wenjie; Liu, Da; Cai, Yong; Jin, Jingji
- **单位**：未提供（PubMed 记录未列出作者单位）
- **期刊/平台**：Phytomedicine : international journal of phytotherapy and phytopharmacology
- **年份**：2025（在线日期 2025-04-20）
- **论文类型**：实验研究（体外 + 体内）
- **领域**：天然产物药理学；癌症生物学；转录因子调控
- **关键词**：Gastric cancer; Ginsenoside Rg3; E2F; E2F-DP dimerization; Cell cycle; p53-p21 pathway
- **DOI/arXiv**：10.1016/j.phymed.2025.156740
- **代码**：未提供
- **数据**：RNA-Seq 数据（未提供 accession 号）
- **阅读日期**：2025-04-22
- **在课题方向中的位置**：本文属于「小分子天然产物直接靶向转录因子（TF）并干扰其蛋白-蛋白互作（PPI）」的机制研究。对「TF–DNA 结合机制 × 物理模拟」方向而言，其核心价值在于：(1) 提供了 E2F-DP 异源二聚化作为药物干预靶点的实验证据；(2) 展示了分子对接（3D molecular docking）在预测小分子-TF 结合位点中的应用；(3) 提供了 CETSA、pull-down 等验证小分子-TF 直接结合的实验范式。但本文未涉及 AI 方法，且分子对接仅作为辅助验证手段，未进行 MD 模拟或自由能计算。

---

## 02 一句话总结

本文通过 RNA-Seq 发现人参皂苷 Rg3 抑制胃癌细胞中 E2F 转录因子表达，并利用 CETSA、pull-down 和分子对接证明 Rg3 直接结合 E2F 的异源二聚化结构域，通过氢键破坏 E2F-DP 二聚体形成，从而抑制 G1/S 期基因转录、诱导细胞周期阻滞和凋亡，在体外和异种移植小鼠模型中均抑制胃癌增殖。

---

## 03 研究问题

- **具体问题**：人参皂苷 Rg3 对胃癌的抗增殖作用是否通过直接靶向 E2F 转录因子并干扰其功能实现？其分子机制是什么？
- **为什么重要**：胃癌治疗受限于耐药性和靶向治疗/免疫治疗的不良反应；E2F 是细胞周期核心转录因子，在多种肿瘤中高表达，是潜在的药物靶点。若天然小分子能直接抑制 E2F 功能，则提供了一种新的治疗策略。
- **现有方法不足**：此前已知 Rg3 具有抗肿瘤活性，但其在 GC 中的分子靶点不明确；E2F 作为转录因子，传统上被认为是"不可成药"（undruggable）靶点，缺乏直接靶向 E2F 的小分子研究。
- **精确研究问题**：Can 20(S)-ginsenoside Rg3 directly bind to E2F and disrupt E2F-DP heterodimer formation, thereby inhibiting E2F-dependent transcription and gastric cancer cell proliferation?

---

## 04 背景与发展脉络

*注：以下脉络基于本文引言及作者引用，标注为「仅本文框架」——未逐一核验外部文献。*

1. **阶段一：Rg3 抗肿瘤活性的表型发现**（早期）
   - 代表方法：体外增殖抑制、凋亡检测
   - 优点：确认 Rg3 广谱抗肿瘤活性
   - 局限：机制不清，靶点不明
2. **阶段二：Rg3 信号通路层面的机制研究**（近年）
   - 代表方法：Western blot 检测通路蛋白（如 PI3K/AKT、MAPK）
   - 优点：揭示下游信号变化
   - 局限：多为间接效应，缺乏直接靶点证据
3. **阶段三：转录因子作为药物靶点的探索**（当前趋势）
   - 代表方法：小分子-TF 直接结合验证（CETSA、pull-down、分子对接）
   - 优点：提供直接靶点证据，拓展"不可成药"靶点边界
   - 局限：分子对接精度有限，缺乏 MD 验证
4. **本文主张的位置**：首次证明 Rg3 直接结合 E2F 蛋白并破坏 E2F-DP 二聚化，将 Rg3 的作用机制从"通路调节"推进到"直接靶向 TF-PPI"层面。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| E2F 被视为"不可成药"靶点 | 缺乏直接靶向 E2F 的小分子抑制剂 | 转录因子缺乏经典药物结合口袋，PPI 界面平坦 | 未提供（作者未明确讨论此痛点，[Analysis] 推断） |
| Rg3 抗 GC 机制不清 | 已知 Rg3 抑制 GC 生长，但分子靶点不明 | 缺乏系统性靶点筛选 | Abstract: "molecular mechanisms underlying its therapeutic effects against GC remain insufficiently understood" |
| E2F-DP 二聚化难以干预 | 二聚化界面大且疏水，传统小分子难以高亲和结合 | 作者未明确解释，[Analysis] 推测为 PPI 靶向的一般性挑战 | 未提供 |
| 现有 E2F 抑制策略多为间接 | 通过 CDK 抑制间接降低 E2F 活性 | 间接抑制导致补偿机制和耐药 | 未提供（作者未明确讨论，[Analysis] 推断） |

---

## 06 核心思想

**1) 表面方法**：
- RNA-Seq 筛选 Rg3 处理后的差异表达基因，锁定 E2F 为候选靶点
- 通过 CETSA、Rg3-PEGA pull-down、pull-down 蛋白质谱、3D 分子对接验证 Rg3-E2F 直接结合
- 通过 qRT-PCR、Co-IP、Western blot、流式、Annexin V、Hoechst、荧光素酶报告基因验证功能后果
- 通过克隆形成（体外）和 C57BL/6 小鼠异种移植（体内）验证抗增殖效果

**2) 核心洞察**：
- Rg3 并非通过经典信号通路间接调节 E2F，而是**直接物理结合 E2F 蛋白的异源二聚化结构域**，通过氢键作用破坏 E2F-DP 异源二聚体形成，从而在转录因子复合物组装层面阻断其功能。
- 这一机制同时解释了 Rg3 对多个 E2F 靶基因（cyclin D1, CDK4, cyclin A, CDK1, CDK2, CDC6）的一致抑制，以及 p53-p21 通路的激活（可能为代偿性反应）。

**3) 可能的普适教训** [Analysis]：
- 天然产物小分子可能通过靶向 TF 的 PPI 界面（而非 DNA 结合域）发挥功能，这为"不可成药"转录因子提供了新的干预窗口。
- RNA-Seq 差异表达分析可作为发现 TF 靶点的无偏筛选策略，但需后续物理结合实验（CETSA/pull-down）确认直接互作。
- 分子对接在此类研究中可作为"结合位点预测"的辅助工具，但需注意其精度限制，建议结合 MD 模拟验证。

---

## 07 方法总览

- **输入**：人胃癌细胞系（具体细胞系未在摘要中说明，Methods 未提供）；20(S)-ginsenoside Rg3
- **输出**：Rg3 抗 GC 增殖的分子机制模型（E2F-DP 二聚化抑制）
- **模块**：
  1. 转录组筛选（RNA-Seq）
  2. 物理结合验证（CETSA、Rg3-PEGA pull-down、pull-down 质谱）
  3. 结构预测（3D 分子对接）
  4. 功能验证（qRT-PCR、Co-IP、Western blot、流式、Annexin V、Hoechst、荧光素酶报告基因）
  5. 表型验证（克隆形成、异种移植）
- **训练**：不适用（非 ML 方法）
- **工具**：未提供具体软件/版本（如 AutoDock 等）
- **反馈回路**：RNA-Seq 发现 → 物理验证确认 → 功能验证 → 体内验证
- **假设**：Rg3 的直接蛋白靶点可通过转录组变化反推；E2F 是 Rg3 的直接结合靶点

**文字流程**：
Rg3 处理 GC 细胞 → RNA-Seq 鉴定差异表达基因 → 发现 E2F 相关转录程序受抑 → CETSA 验证 Rg3 与 E2F 结合（热稳定性变化）→ Rg3-PEGA pull-down + 质谱确认直接互作 → 分子对接预测结合位点（异源二聚化结构域，氢键介导）→ 功能实验验证 E2F 靶基因（cyclin/CDK/CDC6）下调 → Co-IP 验证 E2F-DP 二聚化受抑 → 细胞周期/凋亡表型确认 → 体内异种移植验证抗肿瘤效果。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| RNA-Seq 转录组筛选 | 无偏发现 Rg3 调控的基因/通路 | 确定候选靶点 | 输入：Rg3 处理 vs 对照 GC 细胞 RNA；输出：差异表达基因列表 | Abstract: "RNA-Seq was conducted to identify potential Rg3-regulated targets" | 预期影响：失去发现 E2F 的线索（预期效应，未做消融） |
| CETSA | 验证小分子与靶蛋白直接结合 | 提供细胞内物理结合证据 | 输入：Rg3 处理细胞；输出：E2F 热稳定性曲线 | Abstract: "interaction between Rg3 and E2F was analyzed using CETSA" | 预期影响：失去直接结合证据（预期效应） |
| Rg3-PEGA pull-down + 质谱 | 确认 Rg3 特异性结合 E2F | 提供体外直接互作证据 | 输入：Rg3-PEGA 树脂 + 细胞裂解液；输出：E2F 蛋白鉴定 | Abstract: "Rg3-PEGA pull-down, Rg3 pull-down protein mass spectrometry" | 预期影响：失去靶点特异性证据（预期效应） |
| 3D 分子对接 | 预测 Rg3 在 E2F 上的结合位点 | 提供结构层面的结合模式 | 输入：E2F 结构 + Rg3 结构；输出：结合构象/氢键 | Abstract: "3D molecular docking analysis demonstrated that Rg3 binds with high affinity to E2F at the heterodimeric domain via hydrogen bonding" | 预期影响：失去结合位点信息（预期效应）；注意：对接结果未经 MD 或突变验证 |
| Co-IP | 验证 E2F-DP 二聚化是否被破坏 | 直接验证机制假设 | 输入：Rg3 处理细胞裂解液；输出：E2F-DP 共沉淀量 | Abstract: "disrupting E2F-DP heterodimer formation" | 预期影响：失去机制直接证据（预期效应） |
| 荧光素酶报告基因 | 验证 E2F 转录活性 | 连接二聚化抑制与转录功能 | 输入：E2F 报告质粒 + Rg3；输出：荧光素酶活性 | Abstract: "luciferase reporter assays were employed" | 预期影响：失去转录功能证据（预期效应） |
| 异种移植 | 体内验证抗肿瘤效果 | 确认临床前转化潜力 | 输入：Rg3 处理荷瘤 C57BL/6 小鼠；输出：肿瘤体积/重量 | Abstract: "tumor xenograft experiments in C57BL/6 mice in vivo" | 预期影响：失去体内证据（预期效应） |

*注：所有消融影响均为预期效应，作者未提供模块移除实验。*

---

## 09 关键公式符号

**不适用**。本文为实验药理学研究，未涉及数学模型或算法公式。分子对接虽涉及打分函数，但摘要中未提供具体公式或能量项。

---

## 10 实验设计与证据链

**数据集/群体**：
- 体外：人胃癌细胞系（具体名称未在摘要中提供）
- 体内：C57BL/6 小鼠异种移植模型
- 样本量：未提供

**指标**：
- 增殖：克隆形成、肿瘤体积/重量
- 细胞周期：流式细胞术
- 凋亡：Annexin V-FITC、Hoechst 染色
- 蛋白表达：Western blot
- 转录：qRT-PCR、RNA-Seq
- 结合：CETSA、pull-down、质谱、分子对接

**基线/对照**：未提供（推测为未处理或溶剂对照，Methods 未提供）

**预算/骨干/仪器**：未提供

**oracle 输入**：不适用（非 AI 方法）

**评测协议**：未提供详细统计方法

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| RNA-Seq | Rg3 调控 E2F 相关转录程序 | Rg3 处理 vs 对照 | E2F 及靶基因表达下调 | Rg3 影响 E2F 通路 | 不能证明直接结合 | Abstract |
| CETSA | Rg3 与 E2F 直接结合 | 升温梯度下 E2F 稳定性 | Rg3 存在时 E2F 热稳定性改变 | Rg3 与 E2F 有物理互作 | 不能确定结合位点 | Abstract |
| Rg3-PEGA pull-down + 质谱 | Rg3 特异性结合 E2F | pull-down 产物中鉴定 E2F | E2F 被富集/鉴定 | Rg3 直接结合 E2F | 不能排除其他互作蛋白 | Abstract |
| 分子对接 | Rg3 结合 E2F 异源二聚化结构域 | 对接打分/氢键分析 | 高亲和力结合，氢键介导 | 预测结合位点在二聚化界面 | 对接精度有限，未经 MD/突变验证 | Abstract |
| Co-IP | E2F-DP 二聚化被破坏 | Rg3 处理 vs 对照 | E2F-DP 互作减弱 | Rg3 抑制二聚化 | 未提供定量数据 | Abstract |
| 荧光素酶报告 | E2F 转录活性受抑 | Rg3 处理 vs 对照 | 报告基因活性下降 | 二聚化抑制导致转录抑制 | 未提供具体倍数 | Abstract |
| 克隆形成/异种移植 | Rg3 抑制 GC 增殖 | 体外克隆 + 体内肿瘤生长 | 增殖/肿瘤生长受抑 | Rg3 具有抗 GC 活性 | 未提供剂量-反应曲线 | Abstract |

---

## 11 结论正确解读

- **任务范围**：本文仅研究了 20(S)-ginsenoside Rg3 在胃癌模型中的抗增殖机制，不涉及其他 Rg3 异构体或其他癌症类型。
- **oracle/真值输入**：不适用（非 AI 方法）。
- **端到端状态**：从靶点发现（RNA-Seq）到功能验证（体外/体内）形成完整链条，但分子对接预测的结合位点未经点突变实验验证。
- **算力成本**：不适用。
- **历史数据依赖**：RNA-Seq 依赖参考基因组注释；未提供数据 accession。
- **模型依赖**：分子对接结果依赖 E2F 结构模型（PDB 来源未提供）和对接软件参数。
- **最难情形**：未测试 Rg3 在 E2F 高表达耐药模型中的效果；未测试正常细胞毒性选择性。
- **群体/领域边界**：结论限于胃癌细胞系和小鼠异种移植模型，不能外推至人类患者。
- **不确定性**：摘要未提供统计显著性数值、效应量、样本量；Co-IP 和报告基因实验的具体数据未展示。

**有边界的复述**：在胃癌细胞系和 C57BL/6 小鼠异种移植模型中，20(S)-ginsenoside Rg3 通过直接结合 E2F 蛋白并破坏 E2F-DP 异源二聚化，抑制 E2F 靶基因转录，导致 G1/S 阻滞和凋亡，从而抑制增殖。该结论依赖于 CETSA、pull-down 和分子对接证据，但结合位点的原子级细节和体内靶点占有率尚未确证。

---

## 12 作者自认局限

在提供的摘要材料中，作者未明确列出局限性讨论。摘要以结论性陈述结束，未包含 Limitations 段落。

**作者提及的相关约束**（非正式局限）：
- 作者在结论中谨慎表述为"potential therapeutic strategy"，暗示尚需进一步验证。
- 分子对接结果仅作为支持性证据，作者未声称其具有原子级精度。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| RNA-Seq 发现 E2F 下调，但 E2F 本身是转录因子，其 mRNA 水平变化可能是下游效应而非直接靶点 | Rg3 可能通过其他上游通路（如 p53 激活）间接下调 E2F 表达；直接结合 E2F 蛋白与下调 E2F mRNA 是不同事件 | 区分"直接靶点"与"下游效应"是机制研究的关键 | 检测 Rg3 处理早期（<2h）E2F 蛋白水平；使用翻译抑制剂（CHX）检测 E2F 蛋白稳定性 | Abstract 将 RNA-Seq 作为发现手段，但未说明时间点 |
| 分子对接预测的"异源二聚化结构域结合"缺乏实验验证 | 对接结果可能为假阳性；氢键预测需突变实验确认 | 若结合位点错误，则机制模型不成立 | E2F 二聚化界面关键残基点突变 + 结合实验（ITC/SPR）；或 HDX-MS 验证结合区域 | Abstract 仅提及 docking，未提及突变验证 |
| CETSA 和 pull-down 证明结合，但未提供亲和力定量 | 弱结合（mM 级）可能无药理学意义 | 药物靶点需明确亲和力范围 | ITC/SPR 测定 Kd；等温滴定量热法 | Abstract 未提供 Kd 或 IC50 |
| 体内实验仅用 C57BL/6 小鼠异种移植，未用免疫缺陷鼠或 PDX 模型 | 同种移植模型可能受免疫系统影响；异种移植（human GC cells into mouse）通常用裸鼠 | 模型选择影响结论普适性 | 补充裸鼠异种移植或 PDX 数据 | Abstract 提及 C57BL/6 小鼠，但未说明接种细胞来源 |
| 未提供 Rg3 对正常胃上皮细胞的毒性数据 | 抗增殖可能非选择性 | 治疗窗口未知 | 正常胃细胞系（GES-1）毒性对照 | 未提供 |
| 未讨论 Rg3 是否影响 E2F 的 DNA 结合能力（而非仅二聚化） | 二聚化抑制与 DNA 结合抑制可能是独立事件 | 完整机制需区分 | EMSA 检测 E2F-DP-DNA 复合物形成 | 未提供 |

---

## 14 Agent 提炼的知识候选

**可迁移概念**：

1. **TF-PPI 作为药物靶点的验证范式**：本文提供了从转录组筛选 → 物理结合验证（CETSA + pull-down）→ 结构预测（docking）→ 功能验证的完整流程。对于「TF–DNA 互作 × AI/物理模拟」方向，此范式可迁移至其他 TF（如 MYC、p53、NF-κB）的小分子抑制剂发现。

2. **CETSA 作为小分子-TF 结合验证的金标准**：在 AI 预测小分子-TF 互作后，CETSA 是实验验证的首选方法。可迁移至虚拟筛选后的实验确认环节。

3. **二聚化界面作为 TF 药物靶点的概念**：本文证明 E2F 的二聚化结构域（而非 DNA 结合域）可被小分子靶向。这提示在 AI 辅助的 TF 药物设计中，应同时考虑 DBD 和 PPI 界面两个口袋。

4. **RNA-Seq 作为靶点发现工具**：通过转录组变化反推上游 TF 靶点，可迁移至 AI 辅助的 TF 靶点预测流程中作为验证信号。

**可迁移方法**：

5. **分子对接在 TF-小分子研究中的定位**：本文使用 docking 作为结合位点预测工具，但未进行 MD 模拟。对于本课题，建议在 docking 后补充 MD 模拟（如 100ns）验证结合稳定性，并计算 MM-PBSA 自由能。

6. **多方法交叉验证策略**：CETSA（细胞内）+ pull-down（体外）+ docking（计算）三重证据链，可迁移至任何小分子-TF 互作研究。

**可迁移公式/工具**：不适用（本文无公式）。

---

## 15 与已有知识连接

- **E2F 家族与细胞周期调控**：E2F1-8 与 DP1/DP2 形成异源二聚体，调控 G1/S 期基因转录（经典知识，Dyson 1998, Genes & Dev）。本文靶向 E2F-DP 二聚化，与此经典模型一致。
- **天然产物靶向 TF**：已有研究报道小分子直接靶向 TF 的先例，如 Nutlin-3 靶向 MDM2-p53 互作（Vassilev et al., 2004, Science）；本文为天然产物直接靶向 E2F 提供了新证据。
- **人参皂苷 Rg3 的抗肿瘤研究**：Rg3 已被报道通过多种通路（AKT、VEGF、NF-κB）抑制肿瘤，本文首次提出直接靶向 E2F 的机制，是对既有知识的补充。
- **TF 作为"不可成药"靶点的挑战**：与 KRAS 的"不可成药"历史类似，TF 正逐渐被证明可被小分子靶向（如 p53 突变体恢复剂）。本文支持这一趋势。
- **与本课题方向的关联**：本文的 docking 分析可作为「物理模拟 × TF-DNA 互作」的参考案例，但其精度有限，建议后续结合 AlphaFold 预测的 E2F-DP 复合物结构进行更精确的对接和 MD 模拟。

---

## 16 Agent 生成的研究候选

### 候选 1：基于 AI 的 E2F-DP 二聚化界面小分子虚拟筛选
- **名称**：AI-driven virtual screening for E2F-DP dimerization inhibitors
- **来源局限/观察**：本文仅测试了 Rg3 一个化合物，未进行系统筛选；docking 精度有限
- **核心假设**：E2F-DP 二聚化界面存在可成药口袋，可通过 AI 生成 + 虚拟筛选发现更优抑制剂
- **相对本文的增量**：从单一化合物扩展到化合物库；从 docking 升级为 AI + MD 组合
- **初步方法**：使用 AlphaFold 预测 E2F1-DP1 复合物结构 → 识别二聚化界面热点残基 → 使用生成模型（如 DiffSBDD）设计候选分子 → Glide/AutoDock Vina 对接 → MD 模拟（100ns）+ MM-PBSA 筛选 → CETSA 验证
- **验证方式**：CETSA、pull-down、Co-IP、细胞增殖实验
- **创新状态**：unverified

### 候选 2：Rg3 类似物的构效关系（SAR）研究
- **名称**：SAR study of Rg3 analogs targeting E2F-DP interface
- **来源局限/观察**：本文仅研究 20(S)-Rg3 一种构型，未探讨 20(R)-Rg3 或其他人参皂苷
- **核心假设**：Rg3 的糖链部分和 C20 立体化学影响 E2F 结合亲和力
- **相对本文的增量**：系统探索化学空间，优化结合亲和力
- **初步方法**：合成 Rg3 系列类似物 → 表面等离子共振（SPR）测定 E2F 结合亲和力 → 分子对接 + MD 计算结合自由能 → 细胞实验验证
- **验证方式**：SPR/ITC、CETSA、细胞增殖
- **创新状态**：unverified

### 候选 3：E2F-DP 二聚化抑制剂的 DNA 结合影响评估
- **名称**：Impact of E2F-DP dimerization inhibitors on E2F-DNA binding
- **来源局限/观察**：本文未检测 Rg3 是否影响 E2F 与 DNA 的直接结合（仅检测了二聚化和转录活性）
- **核心假设**：Rg3 可能同时影响 E2F-DP 二聚化和 E2F-DP-DNA 三元复合物形成
- **相对本文的增量**：将研究从"二聚化抑制"扩展到"DNA 结合抑制"，更完整地刻画机制
- **初步方法**：EMSA 检测 Rg3 对 E2F-DP-DNA 复合物的影响 → 荧光各向异性（FA）定量 DNA 结合亲和力 → ChIP-seq 检测 Rg3 处理后 E2F 基因组结合位点变化
- **验证方式**：EMSA、FA、ChIP-seq
- **创新状态**：unverified

### 候选 4：基于 MD 模拟的 E2F-DP 二聚化解离机制研究
- **名称**：Molecular dynamics study of Rg3-induced E2F-DP dissociation
- **来源局限/观察**：本文 docking 仅提供静态结合模式，未揭示解离动力学
- **核心假设**：Rg3 结合二聚化界面后通过变构效应或竞争性结合导致 DP 亚基解离
- **相对本文的增量**：从静态结构到动态机制
- **初步方法**：全原子 MD 模拟（Rg3-E2F-DP 三元复合物）→ 伞形采样计算解离自由能 → 与无 Rg3 对照比较 → 识别关键解离路径
- **验证方式**：MD 模拟 + 突变实验验证关键残基
- **创新状态**：unverified

### 候选 5：E2F 高表达胃癌亚型的 Rg3 精准治疗策略
- **名称**：Precision therapy strategy for E2F-high gastric cancer using Rg3
- **来源局限/观察**：本文未分层分析 E2F 表达水平与 Rg3 敏感性的关系
- **核心假设**：E2F 高表达 GC 亚型对 Rg3 更敏感
- **相对本文的增量**：从机制研究推进到生物标志物指导的精准治疗
- **初步方法**：TCGA GC 数据分层 E2F 高/低表达 → 对应细胞系 Rg3 敏感性测试 → 类器官验证
- **验证方式**：IC50 比较、类器官生长抑制
- **创新状态**：unverified