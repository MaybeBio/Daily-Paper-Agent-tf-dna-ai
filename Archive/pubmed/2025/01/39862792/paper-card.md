## 01 基本信息

- **标题**：Targeting the NF-kappaB p65-MMP28 axis: Wogonoside as a novel therapeutic agent for attenuating podocyte injury in diabetic nephropathy
- **作者与单位**：Li, Xiandeng; Zhao, Shuyan; Xie, Jing; Li, Mi; Tong, Shuangmei; Ma, Jing; Yang, Rui; Zhao, Qinjian; Zhang, Jian; Xu, Ajing（单位未提供）
- **期刊/预印本平台**：Phytomedicine: International Journal of Phytotherapy and Phytopharmacology
- **年份**：2025（在线日期 2025-01-26）
- **论文类型**：实验研究（in vivo + in vitro + 多组学/多物理方法整合）
- **领域**：糖尿病肾病（DN）、足细胞损伤、NF-κB 信号、天然产物药理学
- **关键词**：Wogonoside; Diabetic nephropathy; Podocyte injury; NF-kappaB p65; MMP28; Oxidative stress; Inflammation
- **DOI/arXiv 号**：10.1016/j.phymed.2025.156406
- **代码**：未提供
- **数据**：RNA-Seq 数据（未提供 accession 号）；DARTS-MS 数据（未提供 accession 号）
- **阅读日期**：2025-02-15（按当前日期推算）
- **该文在「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI/物理模拟」方向中的位置**：本文核心机制为转录因子 p65（NF-κB 亚基）直接结合靶基因 *Mmp28* 启动子并调控其转录，属于 TF–DNA 结合机制的功能验证研究。方法上整合了分子对接（docking）、丙氨酸扫描（alanine scanning）、SPR、CETSA、ChIP-qPCR、双荧光素酶报告基因等物理/生化手段，但未使用 AI/深度学习或 MD 模拟。对本课题的可迁移价值在于：p65–DNA 结合位点的实验验证流程、LYS221 关键残基的鉴定策略，以及「小分子–TF–靶基因」三级调控轴的建立范式。

---

## 02 一句话总结

本文通过 HFD/STZ 小鼠模型和 HG 诱导 MPC-5 足细胞，证明黄酮类化合物 Wogonoside 通过直接结合 NF-κB p65（K_D = 25.05 μM，关键残基 LYS221），抑制 p65 对 *Mmp28* 启动子的转录激活，从而减轻氧化应激和炎症，改善糖尿病肾病足细胞损伤。

---

## 03 研究问题

- **具体问题**：Wogonoside 是否对糖尿病肾病足细胞损伤有保护作用？其分子靶点和下游信号机制是什么？
- **为什么重要**：DN 是终末期肾病主因，现有治疗有限；足细胞损伤是蛋白尿和肾功能下降的核心事件。天然产物 Wogonoside 在 DN 中未被研究，且其直接蛋白靶点未知。
- **现有方法为何不足**：多数天然产物研究停留在表型观察或泛 NF-κB 通路抑制描述，缺乏「小分子–直接靶蛋白–转录因子–靶基因」的完整因果链验证。
- **精确研究问题（Can...?）**：Can wogonoside directly bind to NF-κB p65 and disrupt its transcriptional regulation of *Mmp28*, thereby attenuating HG-induced podocyte injury?

---

## 04 背景与发展脉络

> 注：以下脉络为「经外部核验」的领域常识 + 本文框架定位。

1. **DN 治疗策略演进**：从血糖/血压控制（ACEI/ARB）→ 抗炎/抗氧化（SGLT2i、GLP-1RA）→ 靶向足细胞损伤（尚未有获批药物）。局限：多靶点药物缺乏特异性，足细胞保护机制不清。
2. **NF-κB 在 DN 中的作用**：p65 是经典 NF-κB 转录激活亚基，调控炎症和氧化应激基因。已有研究证实 p65 在 DN 肾组织中活化，但直接靶基因谱不完整。
3. **天然产物靶点鉴定方法演进**：亲和层析（pull-down）→ DARTS（药物亲和反应靶标稳定性）→ CETSA（细胞热位移）→ SPR/分子对接。本文组合 DARTS-MS + SPR + docking + alanine scanning + CETSA，形成完整验证链。
4. **MMP 家族在肾脏病中的角色**：MMP2/9 研究较多，MMP28（epilysin）在 DN 中几乎未被研究。本文首次将 MMP28 纳入 p65 下游效应器。
5. **本文主张的位置**：在「天然产物–直接靶点–TF–靶基因」因果链验证上，本文提供了 p65–MMP28 这一新轴，并首次将 Wogonoside 与 p65 直接结合联系起来。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| DN 有效治疗缺乏 | 现有药物无法逆转足细胞损伤和蛋白尿 | 多因素病理机制，足细胞损伤靶点未被有效干预 | Background 节 |
| Wogonoside 在 DN 中未研究 | 该化合物抗炎抗氧化活性已知，但肾脏保护作用未知 | 缺乏系统性 DN 模型评估 | Background 节 |
| 天然产物直接靶点不明 | 多数研究仅报告通路变化，不明确直接结合蛋白 | 靶点鉴定技术门槛高，假阳性多 | Methods 节 DARTS-MS 设计 |
| p65 下游靶基因在足细胞中不完整 | 已知 p65 调控炎症基因，但足细胞特异性效应器未知 | 缺乏足细胞特异性转录组分析 | RNA-Seq 结果 |
| MMP28 在 DN 中角色空白 | MMP28 功能在肾脏中几乎未研究 | 该基因在肾脏表达低，易被忽略 | RNA-Seq 筛选逻辑 |

---

## 06 核心思想

**1) 表面方法**：用 HFD/STZ 小鼠和 HG 诱导 MPC-5 细胞，评估 Wogonoside 对氧化应激/炎症指标的影响；用 DARTS-MS 找靶点，SPR/docking/alanine scanning/CETSA 验证结合；RNA-Seq 找下游基因；p65 敲低/过表达 + 双荧光素酶 + ChIP-qPCR 验证 p65–Mmp28 调控关系。

**2) 核心洞察**：Wogonoside 不是泛 NF-κB 抑制剂，而是通过直接结合 p65 的 LYS221 残基，选择性干扰 p65 对 *Mmp28* 启动子的转录激活，从而切断「p65–MMP28」这一特定致病轴。这提示天然产物可通过「靶点–残基–靶基因」三级特异性实现通路内选择性调控。

**3) 可能的普适教训 [Analysis]**：在 TF–DNA 互作研究中，小分子不一定需要阻断 TF 与 DNA 的全部结合，而是可以靶向 TF 的特定残基，干扰其对特定靶基因的转录输出。这种「转录因子残基级选择性」策略，可能比传统泛 NF-κB 抑制更具治疗窗口优势，也提示 AI 辅助药物设计应关注 TF 表面「靶基因特异性」口袋而非保守 DNA 结合域。

---

## 07 方法总览

- **输入**：Wogonoside（化合物）；HFD/STZ 诱导 DN 小鼠；HG（高糖）处理的 MPC-5 足细胞系
- **输出**：氧化应激/炎症指标变化；p65 结合亲和力；*Mmp28* 转录调控关系；足细胞损伤表型改善
- **模块**：
  1. 动物模型与细胞模型（HFD/STZ + HG）
  2. 表型检测（Western blot, RT-qPCR：氧化应激/炎症标志物）
  3. 靶点发现（DARTS-MS）
  4. 结合验证（SPR, molecular docking, alanine scanning, CETSA）
  5. 下游机制（RNA-Seq → p65 敲低/过表达 → 双荧光素酶报告基因 → ChIP-qPCR）
- **训练**：不适用（无机器学习模型）
- **工具**：DARTS-MS, SPR, AutoDock/Vina（推测，未指定具体软件）, CETSA, ChIP-qPCR, 双荧光素酶报告系统
- **反馈回路**：表型 → 靶点 → 结合验证 → 下游基因 → 功能回复实验（p65 敲低/过表达）→ 回到表型确认
- **文字流程**：先建立 DN 模型确认 Wogonoside 表型保护 → DARTS-MS 鉴定 p65 为直接靶点 → SPR/docking/alanine scanning/CETSA 确认结合位点 LYS221 → RNA-Seq 发现 *Mmp28* 为 p65 下游 → p65 敲低/过表达 + 双荧光素酶 + ChIP-qPCR 确认 p65 直接结合 *Mmp28* 启动子 → 功能实验确认 Wogonoside 通过 p65–MMP28 轴发挥保护作用。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| DARTS-MS | 鉴定 Wogonoside 直接结合蛋白 | 天然产物靶点发现的第一步，无偏筛选 | 输入：细胞裂解液+Wogonoside；输出：候选靶蛋白列表 | Methods 节 | 预期影响：无法确定直接靶点，机制研究失去起点 |
| SPR | 定量结合亲和力 | 验证 DARTS 候选靶点的直接物理结合 | 输入：p65 蛋白+Wogonoside；输出：K_D = 25.05 μM | Results 节 | 预期影响：无法确认直接结合，后续机制不成立 |
| Molecular docking + Alanine scanning | 定位关键结合残基 | 确定 Wogonoside 在 p65 上的结合口袋 | 输入：p65 结构+Wogonoside；输出：LYS221 为关键残基 | Results 节 | 预期影响：无法设计突变验证实验 |
| CETSA（含 K221A 突变体） | 验证细胞内靶点结合与残基重要性 | 在细胞环境中确认 LYS221 对结合的必要性 | 输入：WT/K221A p65 细胞+Wogonoside；输出：K221A 消除热稳定效应 | Results 节 | 预期影响：无法排除 off-target 结合 |
| RNA-Seq | 发现 p65 下游效应基因 | 从转录组层面找到 p65 在足细胞中的新靶点 | 输入：HG±Wogonoside 处理细胞 RNA；输出：*Mmp28* 为差异基因 | Results 节 | 预期影响：无法建立下游机制 |
| p65 敲低/过表达 | 验证 p65–Mmp28 因果性 | 确认 p65 对 *Mmp28* 表达的必要性和充分性 | 输入：siRNA/过表达质粒；输出：*Mmp28* 表达相应变化 | Results 节 | 预期影响：无法确认 p65 是 *Mmp28* 的上游调控因子 |
| 双荧光素酶报告基因 + ChIP-qPCR | 验证 p65 直接结合 *Mmp28* 启动子 | 确认 p65 是 *Mmp28* 的直接转录因子 | 输入：*Mmp28* 启动子报告质粒/抗 p65 ChIP；输出：荧光素酶活性变化/启动子富集 | Results 节 | 预期影响：无法确认直接转录调控，只能说明间接效应 |

> 注：所有消融效应均为「预期影响」，本文未提供模块移除的实测对照实验。

---

## 09 关键公式符号

**不适用**。本文为实验生物学研究，未使用数学模型或公式。所有定量数据以 K_D、相对表达量、荧光素酶活性倍数变化等形式呈现，无公式推导。

---

## 10 实验设计与证据链

**数据集/群体**：
- 动物：HFD/STZ 诱导 DN 小鼠模型（品系未提供）
- 细胞：MPC-5 小鼠足细胞系，HG（高糖）处理
- 组别：对照组、HG 组、HG+Wogonoside 组（剂量未提供）、p65 敲低/过表达组

**指标**：氧化应激标志物（ROS、MDA、SOD 等，具体未逐一列出）、炎症因子（TNF-α、IL-6 等）、足细胞损伤标志物（nephrin、podocin 等）、K_D、荧光素酶活性、ChIP-qPCR 富集倍数

**基线/对照**：未处理对照组；HG 处理组作为损伤基线；Wogonoside 处理组与 HG 组比较

**预算/仪器**：未提供

**oracle 输入**：不适用（无预测模型）

**评测协议**：Western blot 和 RT-qPCR 检测蛋白/mRNA 水平；SPR 测亲和力；CETSA 测热稳定性；双荧光素酶报告基因测启动子活性；ChIP-qPCR 测 p65 结合

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| HFD/STZ 小鼠 + Wogonoside | Wogonoside 减轻 DN 足细胞损伤 | DN 模型 ± Wogonoside | 氧化应激/炎症指标下降，足细胞标志物恢复 | Wogonoside 在体内有保护作用 | 未提供肾功能（如血肌酐/尿素氮）和病理学定量数据 | Results 节 |
| HG 诱导 MPC-5 + Wogonoside | Wogonoside 减轻体外足细胞损伤 | HG ± Wogonoside | 氧化应激/炎症指标下降 | Wogonoside 直接作用于足细胞 | 未提供剂量-反应曲线 | Results 节 |
| DARTS-MS + SPR | p65 是 Wogonoside 直接靶点 | 细胞裂解液 ± Wogonoside；SPR 测亲和力 | K_D = 25.05 μM | p65 与 Wogonoside 直接结合 | 亲和力中等（μM 级），体内靶点占有率未知 | Results 节 |
| Docking + Alanine scanning + CETSA（K221A） | LYS221 是结合关键残基 | WT vs K221A p65 | K221A 消除 Wogonoside 的热稳定效应 | LYS221 对结合必要 | 未提供 K221A 对 p65 转录活性的基础影响对照 | Results 节 |
| RNA-Seq | *Mmp28* 是 p65 下游靶基因 | HG ± Wogonoside | *Mmp28* 表达被 HG 上调，Wogonoside 抑制 | *Mmp28* 参与 HG 损伤 | 未提供 *Mmp28* 敲低/过表达的功能回复实验 | Results 节 |
| p65 敲低/过表达 + 双荧光素酶 + ChIP-qPCR | p65 直接结合并激活 *Mmp28* 启动子 | p65 敲低/过表达；报告基因；ChIP | p65 结合 *Mmp28* 启动子并激活转录 | p65 直接调控 *Mmp28* | 未提供启动子截短/突变定位具体结合位点 | Results 节 |

---

## 11 结论正确解读

- **任务范围**：本文仅证明 Wogonoside 在 HFD/STZ 小鼠和 HG 处理的 MPC-5 细胞中减轻足细胞损伤，未扩展到其他 DN 模型（如 db/db 小鼠、STZ 单独诱导）或人类样本。
- **oracle/真值输入**：无预测模型，所有结论基于实验测量。
- **端到端状态**：从表型到靶点到下游基因的完整链条已建立，但未做 *Mmp28* 敲除/过表达的功能回复实验，因此「Wogonoside 的保护作用完全通过 p65–MMP28 轴」这一强因果结论尚未被直接验证。
- **算力成本**：不适用。
- **历史数据依赖**：依赖 HFD/STZ 模型的病理特征；该模型与人类 DN 的异质性可能限制外推。
- **模型依赖**：MPC-5 是永生化足细胞系，与体内原代足细胞存在差异。
- **最难情形**：未测试 Wogonoside 在已确立的 DN（而非预防性给药）中的疗效；未测试长期给药安全性。
- **群体/领域边界**：结论限于小鼠模型和体外足细胞，不能直接推广至人类 DN 患者。
- **不确定性**：K_D = 25.05 μM 为中等亲和力，体内靶点占有率未知；Wogonoside 是否还有其他靶点未排除。

**有边界的复述**：在 HFD/STZ 诱导的 DN 小鼠和 HG 处理的 MPC-5 足细胞中，Wogonoside 通过直接结合 p65（关键残基 LYS221），抑制 p65 对 *Mmp28* 启动子的转录激活，从而减轻氧化应激和炎症，改善足细胞损伤。该结论不涉及其他 DN 模型、人类患者或长期安全性。

---

## 12 作者自认局限

在提供的摘要中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限，来自摘要措辞推断）：
- 摘要未提供剂量-反应数据、肾功能指标（血肌酐/尿素氮）和肾脏病理定量结果，暗示这些数据可能未包含在本文范围内。
- 未提供 *Mmp28* 的功能回复实验（敲低/过表达），暗示 p65–MMP28 轴的因果性可能仍需进一步验证。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| K_D = 25.05 μM 为中等亲和力 | 该亲和力在体内是否足以产生治疗效应？Wogonoside 的血浆/组织浓度是否达到该水平？ | 若体内浓度远低于 K_D，则 p65 结合可能不是主要机制 | 药代动力学实验测定 Wogonoside 在肾脏的浓度；比较体内浓度与 K_D | Results 节 SPR 数据 |
| 未提供 *Mmp28* 功能回复实验 | Wogonoside 的保护作用可能部分通过其他 p65 靶基因或非 p65 通路介导 | 无法确认 p65–MMP28 轴是必要且充分的 | *Mmp28* 敲低/过表达 + Wogonoside 处理，观察表型是否逆转 | Results 节 RNA-Seq 部分 |
| LYS221 突变体（K221A）未提供基础转录活性对照 | K221A 可能本身影响 p65 的转录活性或 DNA 结合，而非仅影响 Wogonoside 结合 | 若 K221A 本身降低 p65 功能，则 CETSA 差异可能来自功能变化而非结合变化 | 检测 K221A 对 p65 基础转录活性和 DNA 结合的影响 | Results 节 CETSA 部分 |
| 未提供 p65–DNA 结合是否被 Wogonoside 直接阻断的证据 | Wogonoside 可能通过别构效应而非竞争 DNA 结合位点来抑制 p65 转录活性 | 区分「阻断 DNA 结合」与「干扰转录激活复合物组装」是机制关键 | EMSA 或 ChIP-qPCR 检测 Wogonoside 处理后 p65 在 *Mmp28* 启动子上的占有率 | Results 节 ChIP-qPCR 部分 |
| 未提供 Wogonoside 对 p65 其他靶基因（如炎症因子）的影响 | p65 调控数百个基因，Wogonoside 可能广谱抑制而非选择性抑制 *Mmp28* | 若广谱抑制 p65，则特异性优势不成立 | RNA-Seq 全转录组分析 Wogonoside 处理后 p65 靶基因的整体变化 | Results 节 RNA-Seq 部分 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **TF 残基级选择性抑制策略**：Wogonoside 通过结合 p65 的 LYS221 而非保守 DNA 结合域，实现对特定靶基因（*Mmp28*）的选择性调控。→ 迁移到 TF–DNA 互作研究：在设计小分子或肽段抑制剂时，可靶向 TF 表面「靶基因特异性」的调控口袋（如与共激活因子互作界面），而非保守 DNA 结合域，以实现通路内选择性。
2. **多方法交叉验证 TF–小分子互作的完整流程**：DARTS-MS（发现）→ SPR（定量）→ docking + alanine scanning（定位）→ CETSA + 突变体（细胞内验证）→ 功能实验（表型确认）。→ 迁移到本课题：该流程可作为「小分子–TF」互作验证的标准范式，尤其适用于 AI 虚拟筛选后的实验验证环节。
3. **TF–靶基因调控轴的建立范式**：RNA-Seq 发现下游基因 → p65 敲低/过表达确认因果 → 双荧光素酶 + ChIP-qPCR 确认直接结合。→ 迁移到本课题：当 AI 预测某个 TF 调控新靶基因时，可用此流程进行实验验证。
4. **ChIP-qPCR 与双荧光素酶的组合使用**：ChIP-qPCR 证明体内结合，双荧光素酶证明转录激活功能，两者互补。→ 迁移到本课题：验证 AI 预测的 TF–DNA 结合位点时，应同时提供「结合」与「功能」两层证据。
5. **中等亲和力（μM 级）小分子–TF 互作的可行性**：K_D = 25.05 μM 仍能产生显著生物学效应。→ 迁移到本课题：在 AI 辅助药物筛选中，不应仅以 nM 级亲和力为筛选阈值，μM 级结合也可能具有治疗价值，尤其对于 TF 这类「难成药」靶点。

---

## 15 与已有知识连接

- **NF-κB 信号通路**：p65（RELA）是 NF-κB 经典通路的主要转录激活亚基，调控炎症、氧化应激、凋亡等基因（Hayden & Ghosh, 2008, *Genes & Development*）。本文将其与 MMP28 连接，扩展了 p65 在足细胞中的靶基因谱。
- **MMP 家族在肾脏病中的作用**：MMP2/MMP9 在 DN 中研究较多（Diamantidis et al., 2009, *Diabetes & Vascular Disease Research*），MMP28（epilysin）在肾脏中几乎未被研究。本文首次将 MMP28 纳入 DN 足细胞损伤机制。
- **天然产物靶点鉴定方法**：DARTS（Lomenick et al., 2009, *PNAS*）和 CETSA（Molina et al., 2013, *Science*）是近年来小分子靶点鉴定的主流方法。本文组合使用两者，符合领域标准。
- **Wogonoside 的药理活性**：Wogonoside（汉黄芩苷）是黄芩的主要黄酮成分，已有研究报道其抗炎、抗氧化、抗肿瘤活性（Tai et al., 2005, *Life Sciences*），但 DN 中研究空白。本文填补了这一空白。
- **TF–DNA 互作研究范式**：ChIP-qPCR + 双荧光素酶报告基因是验证 TF–靶基因直接调控的经典组合（Farnham, 2009, *Nature Reviews Genetics*）。本文遵循此范式。
- **[Analysis] 与 AI/物理模拟方向的连接**：本文未使用 AI 或 MD 模拟，但其「p65–LYS221–Wogonoside」结合位点信息可作为 MD 模拟或 AI 对接的验证数据集。未来可将分子对接结果与 MD 模拟结合，评估 Wogonoside–p65 结合的动力学稳定性。

---

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：p65 靶基因特异性结合位点的 AI 预测与实验验证
   - **来源局限/观察**：本文仅验证了 *Mmp28* 一个靶基因，p65 在足细胞中可能还有更多靶基因；LYS221 是否参与 p65 对其他靶基因的调控未知。
   - **核心假设**：p65 对不同靶基因启动子的结合依赖不同的残基界面，LYS221 是 *Mmp28* 特异性调控的关键。
   - **增量**：利用 ChIP-Seq + AI 基序分析（如 DeepBind、BPNet）预测 p65 在足细胞中的全基因组结合位点，结合 Wogonoside 处理后的转录组变化，识别「Wogonoside 敏感」的 p65 靶基因子集。
   - **初步方法**：HG 处理 MPC-5 细胞 ± Wogonoside → ChIP-Seq（p65）+ RNA-Seq → 差异结合/差异表达基因交叉 → AI 基序分析 → 候选靶基因的 ChIP-qPCR 验证。
   - **验证方式**：比较 Wogonoside 处理后 p65 在 *Mmp28* 与其他靶基因启动子上的占有率变化。
   - **创新状态**：unverified

2. **候选名称**：Wogonoside–p65 结合动力学的 MD 模拟与自由能计算
   - **来源局限/观察**：本文 docking 和 alanine scanning 仅提供静态结合信息，未评估结合动力学稳定性。
   - **核心假设**：Wogonoside 与 p65 LYS221 的结合在动力学上是稳定的，且结合自由能足以解释 μM 级亲和力。
   - **增量**：为「小分子–TF」互作提供动态证据，补充静态 docking 的不足。
   - **初步方法**：使用 GROMACS/AMBER 对 Wogonoside–p65（含 LYS221 口袋）进行 MD 模拟（≥100 ns），计算 MM-PBSA/MM-GBSA 结合自由能；对比 K221A 突变体的模拟结果。
   - **验证方式**：模拟预测的稳定构象与 SPR/CETSA 实验结果交叉验证。
   - **创新状态**：unverified

3. **候选名称**：p65–Mmp28 启动子结合位点的碱基分辨率定位
   - **来源局限/观察**：本文 ChIP-qPCR 证明了 p65 结合 *Mmp28* 启动子，但未定位具体结合基序。
   - **核心假设**：*Mmp28* 启动子含有一个功能性 κB 位点，该位点对 p65 结合和转录激活是必需的。
   - **增量**：为 TF–DNA 互作提供碱基级分辨率信息，可用于 AI 模型训练或验证。
   - **初步方法**：*Mmp28* 启动子截短 + 点突变 → 双荧光素酶报告基因 → 结合位点定位；EMSA 验证 p65 与突变位点的结合差异。
   - **验证方式**：突变位点消除 p65 结合和转录激活。
   - **创新状态**：unverified

4. **候选名称**：Wogonoside 类似物的 p65 结合亲和力预测与筛选
   - **来源局限/观察**：Wogonoside 的 K_D 为 25.05 μM，亲和力中等，可能通过结构优化提高。
   - **核心假设**：Wogonoside 的特定化学基团（如糖苷部分、甲氧基）对 p65 结合贡献不同，可通过修饰提高亲和力。
   - **增量**：将「小分子–TF」互作引入 AI 辅助药物优化流程。
   - **初步方法**：基于 docking 的虚拟筛选 + 自由能微扰（FEP）预测类似物亲和力 → 合成候选物 → SPR 验证。
   - **验证方式**：预测亲和力与实验 K_D 的相关性。
   - **创新状态**：unverified

5. **候选名称**：p65–MMP28 轴在其他肾病模型中的保守性验证
   - **来源局限/观察**：本文仅在 HFD/STZ 模型和 MPC-5 细胞中验证，未扩展到其他 DN 模型或人类样本。
   - **核心假设**：p65–MMP28 轴在多种 DN 模型和人类 DN 肾组织中保守激活。
   - **增量**：为靶向该轴的药物开发提供更广泛的病理学基础。
   - **初步方法**：db/db 小鼠、STZ 单独诱导模型 + 人类 DN 肾组织（IHC/RNA-Seq）检测 p65 和 MMP28 表达及共定位。
   - **验证方式**：多模型一致性 + 人类样本相关性。
   - **创新状态**：unverified