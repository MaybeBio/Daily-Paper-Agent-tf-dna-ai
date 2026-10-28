## 01 基本信息

- **标题**: Functional analysis of a down-regulated transcription factor-SoxNeuroA gene involved in the acaricidal mechanism of scopoletin against spider mites
- **作者与单位**: Zhou, Hong; Ning, Yeshuang; Jian, Yufan; Zhang, Miao; Klakong, Matthana; Guo, Fuyou; Shao, Qingyi; Li, Yanhong; Yang, Pinglong; Li, Zongquan; Yang, Liang; Li, Shili; Ding Wei（单位未在摘要中提供）
- **期刊/平台**: Pest Management Science
- **年份**: 2023-11-21（在线发表）
- **论文类型**: 实验研究（功能基因验证）
- **领域**: 植物源杀螨剂作用机制 / 转录因子功能 / 钙离子通道调控
- **关键词**: scopoletin; SoxNeuroA; Tetranychus cinnabarinus; Orai1; Ca²⁺ homeostasis; acaricidal mechanism（基于摘要推断）
- **DOI/arXiv 号**: 10.1002/ps.7892
- **代码**: 未提供
- **数据**: 未提供（原始测序/结合数据未公开）
- **阅读日期**: 2025-05-14（按当前日期）
- **在课题方向中的位置**: 本文属于「蛋白质-DNA互作（转录因子TF–DNA结合机制）× 化学物作用机制」交叉方向，核心是**小分子配体（scopoletin）与转录因子（SoxNeuroA）的直接结合**，以及该TF对下游靶基因（Orai1）启动子的转录调控。对TF–DNA结合机制课题的可迁移点在于：①TF作为小分子药物靶点的概念；②TF–DNA结合位点的实验验证流程（Y1H + 双荧光素酶）；③分子对接预测结合位点 + 点突变验证的闭环方法。

---

## 02 一句话总结

本文通过克隆朱砂叶螨的转录因子基因 TcSoxNeuroA，结合 RNAi、酵母单杂交、双荧光素酶报告基因、分子对接与点突变等手段，证明植物源杀螨剂 scopoletin 通过抑制 SoxNeuroA 蛋白（关键结合位点 ASP185/ARG189/LYS217）解除其对 Orai1 钙通道基因的转录抑制，导致 Ca²⁺ 超载和螨虫死亡。

---

## 03 研究问题

- **具体问题**: 在 scopoletin 暴露下显著下调的转录因子 SoxNeuroA 在杀螨机制中扮演什么功能角色？它如何被 scopoletin 调控？其下游靶基因是什么？
- **为什么重要**: 阐明植物源杀螨剂的作用靶点和分子机制，是设计下一代绿色杀螨剂（以新靶点为基础）的前提。SoxNeuroA 作为转录因子，若被证实是 scopoletin 的直接靶蛋白，则开辟了「以 TF 为靶点」的农药设计新思路。
- **现有方法不足**: 此前仅观察到 SoxNeuroA 在 scopoletin 暴露下表达下调（转录水平），但缺乏功能验证（敲低/过表达）、缺乏下游靶基因鉴定、缺乏蛋白水平直接结合证据。
- **精确研究问题（Can...?）**: Can scopoletin directly bind to the SoxNeuroA protein and thereby deepress the transcription of the Orai1 Ca²⁺ channel gene, leading to Ca²⁺ overload and mite lethality?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文摘要及引言推断，标注为「仅本文框架」——因未提供全文引言，无法核验外部文献引用。

- **阶段一：植物源杀螨剂活性筛选**（前期）
  - 代表性方法：生物活性测定（LC50等）
  - 优点：能发现先导化合物
  - 局限：作用机制不明，难以理性优化
- **阶段二：转录组学揭示候选靶基因**（前期）
  - 代表性方法：RNA-seq 比较 scopoletin 处理 vs 对照
  - 优点：高通量发现差异表达基因
  - 局限：仅提供相关性，缺乏因果验证
- **阶段三：单基因功能验证**（本文位置）
  - 代表性方法：RNAi 敲低 + 表型（死亡率/敏感性）测定
  - 优点：建立因果联系
  - 局限：RNAi 表型可能受脱靶/不完全敲低影响
- **阶段四：TF–DNA 调控网络解析**（本文核心）
  - 代表性方法：Y1H + 双荧光素酶报告基因 + 启动子截短/突变
  - 优点：直接证明 TF 对靶基因启动子的结合与调控
  - 局限：体外/异源系统，需体内验证
- **阶段五：小分子–蛋白直接互作**（本文亮点）
  - 代表性方法：分子对接 + 点突变 + 微量热泳动（MST）
  - 优点：提供直接物理结合证据
  - 局限：MST 为体外实验，体内结合仍需证实

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 转录因子在杀螨机制中的功能未知 | SoxNeuroA 仅在转录组中显示下调，但功能角色空白 | 缺乏系统的功能验证（RNAi、靶基因鉴定、蛋白互作） | 摘要 Results 首句：「the functional role of this gene remains unknown」 |
| 缺乏下游靶基因信息 | 不知道 SoxNeuroA 调控哪些基因 | 未进行 Y1H/ChIP 等靶基因筛选 | 摘要 Results 中 Y1H 和双荧光素酶实验为首次揭示 Orai1 为靶基因 |
| 小分子与 TF 的直接结合证据缺失 | 仅观察到表达水平变化，无法区分直接/间接效应 | 未进行蛋白水平结合实验 | 摘要 Results 中 MST 和点突变实验为直接结合提供证据 |
| 关键结合位点不明确 | 无法指导杀螨剂结构优化 | 缺乏分子对接 + 突变验证 | 摘要 Results 中 ASP185/ARG189/LYS217 位点鉴定 |

---

## 06 核心思想

**1) 表面方法**：
- 克隆 TcSoxNeuroA 基因 → 确认 scopoletin 暴露下表达/蛋白水平下调（RT-PCR、qPCR、Western blot）→ RNAi 敲低验证功能 → Y1H + 双荧光素酶鉴定下游靶基因（Orai1）及结合序列 → 分子对接预测 scopoletin 结合位点 → 点突变 + MST 验证关键氨基酸。

**2) 核心洞察**：
- **Scopoletin 不是通过「抑制 TF 表达」而是通过「直接结合 TF 蛋白并抑制其转录抑制功能」发挥作用**。SoxNeuroA 正常情况下是 Orai1 的转录抑制因子（维持 Ca²⁺ 稳态），scopoletin 结合后解除抑制 → Orai1 上调 → Ca²⁺ 内流超载 → 细胞死亡。
- 这是一个「**抑制抑制子**」的双重负调控逻辑：杀螨剂靶向的是一个抑制性 TF，而非激活子。

**3) 可能的普适教训 [Analysis]**：
- 转录因子可以作为农药/药物的直接靶点，而不仅仅是下游基因表达变化的「旁观者」。
- 对于 TF–DNA 结合机制研究，**「小分子–TF 直接结合」+「TF–DNA 结合位点」两个层面的实验可以串联成一个完整的故事**：先证明小分子结合 TF，再证明 TF 结合 DNA 并调控转录，最后将两者因果连接。
- 分子对接预测 + 点突变验证 + 物理结合实验（MST）是验证「小分子–蛋白」互作位点的低成本闭环，可迁移到其他 TF–配体体系。

---

## 07 方法总览

- **输入**: 朱砂叶螨（Tetranychus cinnabarinus）个体/细胞；scopoletin 化合物；TcSoxNeuroA 基因序列；Orai1 启动子序列
- **输出**: ①TcSoxNeuroA 基因 cDNA 序列；②scopoletin 暴露下表达/蛋白水平变化；③RNAi 后螨虫对 scopoletin 敏感性变化；④Orai1 为 SoxNeuroA 直接靶基因的证据；⑤SoxNeuroA 上 scopoletin 关键结合位点
- **模块**:
  1. 基因克隆与鉴定（RT-PCR、qPCR、Western blot）
  2. RNAi 功能验证（dsRNA 注射/饲喂 + 生物测定）
  3. TF–DNA 互作鉴定（Y1H + 双荧光素酶报告基因 + 启动子截短/点突变）
  4. 小分子–蛋白互作预测与验证（分子对接 + 点突变 + MST）
- **训练**: 不适用（非机器学习方法）
- **工具**: 分子克隆、qPCR、Western blot、RNAi、Y1H、双荧光素酶报告基因、分子对接软件（未指定）、MST（如 NanoTemper）
- **反馈回路**: RNAi 表型 → 确认功能；MST 结合常数 → 确认直接互作；点突变 → 确认关键残基
- **假设**: ①SoxNeuroA 在螨虫中功能保守；②scopoletin 直接结合 SoxNeuroA 而非通过代谢物；③Orai1 启动子上的 ATCAAAG 是功能性结合位点

**文字流程**：
克隆 TcSoxNeuroA → 确认 scopoletin 处理下 mRNA/蛋白下调 → RNAi 敲低 → 表型（对 scopoletin 敏感性↑）→ 假设 SoxNeuroA 是 scopoletin 靶点 → Y1H 筛选 SoxNeuroA 结合的启动子 → 发现 Orai1 → 双荧光素酶确认 SoxNeuroA 抑制 Orai1 转录 → 截短/突变定位 ATCAAAG 为关键序列 → 分子对接预测 scopoletin 结合 SoxNeuroA 的位点 → 点突变 + MST 验证 ASP185/ARG189/LYS217 → 整合模型：scopoletin 结合 SoxNeuroA → 解除对 Orai1 抑制 → Ca²⁺ 超载 → 死亡。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 基因克隆与表达分析 | 获得 TcSoxNeuroA 序列并确认 scopoletin 下调效应 | 建立研究对象和表型基础 | 输入：cDNA；输出：基因序列、表达/蛋白水平 | 摘要 Results：「RT-PCR, qPCR, and Western blotting assays all confirmed...」 | 无此模块则无法确认 SoxNeuroA 与 scopoletin 的相关性 |
| RNAi 功能验证 | 敲低 SoxNeuroA 观察表型 | 建立因果联系（表达下调是否导致敏感性增加） | 输入：dsRNA；输出：死亡率/敏感性变化 | 摘要 Results：「RNA interference silencing...significantly enhanced the susceptibility」 | 无此模块则只能证明相关性，不能证明因果 |
| Y1H + 双荧光素酶 | 鉴定 SoxNeuroA 的直接 DNA 靶基因及结合序列 | 揭示 TF 的转录调控网络 | 输入：SoxNeuroA 蛋白 + 启动子文库；输出：靶基因、结合序列 | 摘要 Results：「TcSoxNeuroA was a repressor of Orai1...key binding sequence was ATCAAAG」 | 无此模块则无法将 SoxNeuroA 与 Ca²⁺ 稳态联系起来 |
| 分子对接 + 点突变 + MST | 验证 scopoletin 与 SoxNeuroA 的直接结合及关键残基 | 证明小分子直接靶向 TF 蛋白 | 输入：scopoletin 结构 + SoxNeuroA 结构；输出：结合位点、结合亲和力 | 摘要 Results：「ASP185, ARG189, and LYS217...may be the vital binding sites」 | 无此模块则无法区分「直接靶向」与「间接效应」 |

> 注：摘要未提供消融实验（如突变 ATCAAAG 后双荧光素酶活性变化的具体数值、MST 结合常数等），因此「移除后影响」多为预期效应而非实测消融效应。

---

## 09 关键公式符号

**不适用**。本文为实验生物学研究，摘要中未涉及数学模型或公式。分子对接评分函数和 MST 结合常数（Kd）虽被使用，但具体公式未在摘要中提供。

---

## 10 实验设计与证据链

- **数据集/群体**: 朱砂叶螨（Tetranychus cinnabarinus）实验室种群；未提供具体品系/地理来源
- **规模**: 未提供（样本量、生物学重复数未在摘要中说明）
- **指标**: 基因表达水平（qPCR）、蛋白水平（Western blot）、死亡率/敏感性（生物测定）、转录抑制活性（双荧光素酶）、结合亲和力（MST）
- **基线**: 未处理对照组（scopoletin 未暴露）；野生型 SoxNeuroA
- **预算**: 未提供
- **骨干/仪器**: 未提供（qPCR 仪、Western blot 系统、MST 仪器型号未说明）
- **oracle 输入**: 不适用（非预测性任务）
- **评测协议**: 未提供详细统计方法

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| 表达/蛋白水平检测 | scopoletin 暴露下调 SoxNeuroA | 处理 vs 对照 | 三种方法均确认显著下调 | SoxNeuroA 是 scopoletin 响应基因 | 不能证明是直接靶点 | 摘要 Results 第 1-2 句 |
| RNAi 敲低 + 生物测定 | SoxNeuroA 低表达增强 scopoletin 敏感性 | dsRNA 处理 vs 对照 | 敏感性显著增强 | SoxNeuroA 参与 scopoletin 杀螨机制 | 不能证明 SoxNeuroA 是唯一靶点 | 摘要 Results 第 3 句 |
| Y1H + 双荧光素酶 | SoxNeuroA 抑制 Orai1 转录 | 报告基因 + 启动子片段 | 确认抑制，结合序列为 ATCAAAG（-361~-368） | SoxNeuroA 是 Orai1 的转录抑制因子 | 未提供体内 ChIP 证据 | 摘要 Results 第 4 句 |
| 点突变 + MST | ASP185/ARG189/LYS217 是 scopoletin 结合位点 | 突变体 vs 野生型 | 突变影响结合 | 这三个残基参与 scopoletin 结合 | 未提供结合常数数值；未做体内功能验证 | 摘要 Results 第 5 句 |

---

## 11 结论正确解读

- **任务范围**: 本文仅针对朱砂叶螨（T. cinnabarinus）中的 SoxNeuroA 基因，不涉及其他螨种或昆虫。
- **oracle/真值输入**: 无预测性任务；实验数据为直接测量。
- **端到端状态**: 从基因克隆到表型验证到分子互作，链条完整，但**未包含体内（in vivo）结合证据**（如 ChIP-qPCR 或转基因回补实验）。
- **算力成本**: 不适用。
- **历史数据依赖**: 依赖转录组学前期数据（未在摘要中展示）。
- **模型依赖**: 分子对接模型依赖 SoxNeuroA 三维结构（可能为同源建模，未说明）。
- **最难情形**: 摘要未讨论 scopoletin 对其他转录因子的潜在影响（选择性）；未讨论 SoxNeuroA 在螨虫发育中的正常生理功能。
- **群体/领域边界**: 结论仅适用于 scopoletin 对 T. cinnabarinus 的杀螨机制；不能外推至其他杀螨剂或螨种。
- **不确定性**: 摘要未提供统计显著性水平、效应量、重复数；MST 结合常数未给出；点突变对结合的具体影响程度未量化。

**有边界的复述**: 在朱砂叶螨中，scopoletin 暴露导致 SoxNeuroA 表达和蛋白水平下降；RNAi 敲低 SoxNeuroA 增强螨虫对 scopoletin 的敏感性；SoxNeuroA 通过结合 Orai1 启动子上的 ATCAAAG 序列抑制其转录；分子对接和 MST 提示 ASP185/ARG189/LYS217 是 scopoletin 与 SoxNeuroA 结合的关键残基。这些结果共同支持「scopoletin 通过抑制 SoxNeuroA 功能、解除对 Orai1 的转录抑制、导致 Ca²⁺ 超载」的模型，但该模型仍需体内实验进一步验证。

---

## 12 作者自认局限

在提供的摘要中，**未发现作者明确承认的局限**。

**作者提及的相关约束**（非正式局限，基于摘要措辞推断）：
- 摘要使用「may be the vital binding sites」表述，暗示结合位点结论为预测性，需进一步验证。
- 未提供体内（in vivo）功能验证数据，如转基因回补或组织特异性敲除。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| RNAi 敲低 SoxNeuroA 增强 scopoletin 敏感性 | 敲低可能影响螨虫整体健康，非特异性增强对药物的敏感性；也可能存在脱靶效应 | 若表型非特异性，则 SoxNeuroA 在杀螨机制中的因果作用被高估 | 设置无关基因 dsRNA 对照；检测 SoxNeuroA 敲低后其他生理指标（如发育、繁殖力） | 摘要仅报告「significantly enhanced the susceptibility」，未提供对照细节 |
| Y1H/双荧光素酶为异源系统 | 体外/异源细胞中 SoxNeuroA 对 O1rai1 的抑制可能不代表体内真实情况 | TF–DNA 结合具有细胞环境依赖性 | 在螨虫体内进行 ChIP-qPCR 或转基因报告基因实验 | 摘要未提供 ChIP 数据 |
| 分子对接预测的位点未经体内验证 | ASP185/ARG189/LYS217 突变可能影响蛋白折叠而非直接破坏 scopoletin 结合 | 若突变导致蛋白不稳定，则「关键位点」结论不成立 | 检测突变体蛋白表达水平和稳定性（如 Western blot 定量）；进行等温滴定量热（ITC）验证 | 摘要未提供突变体蛋白稳定性数据 |
| 未检测 SoxNeuroA 是否还有其他靶基因 | Orai1 可能是众多靶基因之一，Ca²⁺ 超载可能不是唯一致死机制 | 若存在其他靶基因，杀螨机制模型不完整 | 进行 ChIP-seq 或 RNA-seq 联合分析 | 摘要仅报告 Orai1 一个靶基因 |
| scopoletin 是否直接结合 SoxNeuroA 的结论依赖 MST | MST 可能受缓冲液、蛋白聚集等影响产生假阳性 | 直接结合是全文核心 claim，需多方法交叉验证 | 使用表面等离子共振（SPR）或核磁共振（NMR）交叉验证 | 摘要仅提及 MST |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **「抑制抑制子」的调控逻辑**：小分子药物可以靶向一个转录抑制因子，通过「去抑制」激活下游基因表达。在 TF–DNA 互作研究中，不要只关注激活型 TF，抑制型 TF 同样可以是功能性靶点。**可迁移**：在筛选小分子调控 TF–DNA 结合时，同时考虑「抑制解除」这一机制。

2. **TF–DNA 结合位点验证的标准流程**：Y1H（体内/异源 DNA 结合）+ 双荧光素酶报告基因（转录调控功能）+ 启动子截短/点突变（顺式元件定位）三者串联，是验证 TF–DNA 结合及其功能后果的经典组合。**可迁移**：在 AI 预测 TF 结合位点后，可用此流程进行湿实验验证。

3. **小分子–TF 互作验证闭环**：分子对接（预测）→ 点突变（验证关键残基）→ MST（物理结合确认），这一「预测-突变-结合」闭环成本低、逻辑清晰。**可迁移**：在 AI 辅助药物设计中，对预测的 TF–小分子互作位点，可用此流程快速验证。

4. **多层面证据链设计**：从基因表达（qPCR）→ 蛋白水平（Western blot）→ 功能（RNAi）→ 靶基因（Y1H）→ 直接互作（MST），每一层都回答不同层面的问题，层层递进。**可迁移**：在设计 TF–DNA 互作研究时，按「表达-功能-靶点-互作」四层设计实验。

5. **钙信号通路作为杀虫/杀螨靶点的概念**：Ca²⁺ 稳态（Orai1 钙通道）是细胞生存的关键，TF 调控钙通道基因的转录是潜在干预点。**可迁移**：在探索 TF–DNA 互作的生理后果时，关注钙信号等核心稳态通路。

---

## 15 与已有知识连接

- **Sox 家族转录因子**：SoxNeuroA 属于 Sox 转录因子家族（SRY-related HMG-box），该家族在神经发育中高度保守。本文将其与钙稳态联系，扩展了 Sox 因子的非发育功能。可连接至 Sox 家族在昆虫/螨类中的功能研究。
- **Orai1/STIM1 钙释放激活钙通道（CRAC）通路**：Orai1 是 CRAC 通道的孔道亚基，在免疫细胞中研究最深入。本文首次（据摘要推断）将 Orai1 与螨虫杀螨机制联系。可连接至 CRAC 通道药理学（如免疫抑制剂）研究。
- **植物源杀螨剂**：scopoletin（东莨菪内酯）是香豆素类化合物，广泛存在于植物中。本文为其提供了分子靶点。可连接至其他香豆素类化合物的杀虫/杀螨机制研究。
- **TF 作为药物靶点**：传统上药物靶点多为酶/受体，TF 因「难以成药」而较少被直接靶向。本文为「TF 直接靶向」提供了案例。可连接至 PROTAC、分子胶等靶向蛋白降解技术在 TF 领域的应用。
- **分子对接 + 点突变 + MST 的验证范式**：该范式在药物发现中常见，但在农药分子机制研究中较少见。可连接至计算机辅助农药设计（CADD）领域。

---

## 16 研究想法

> **Agent 生成的研究候选**

**候选 1：基于 AlphaFold 的 SoxNeuroA–DNA 复合物结构预测与 scopoletin 结合位点验证**
- **来源局限/观察**：本文分子对接可能基于同源建模结构，精度有限；未提供 SoxNeuroA 的实验结构。
- **核心假设**：AlphaFold 预测的 SoxNeuroA 结构 + 分子对接可更精确地定位 scopoletin 结合口袋，且该口袋与 DNA 结合域（HMG-box）空间邻近。
- **增量**：用 AI 结构预测替代同源建模，提高对接可靠性；可进一步用 MD 模拟验证结合稳定性。
- **初步方法**：AlphaFold2/3 预测 SoxNeuroA 结构 → 与 DNA 共对接 → scopoletin 分子对接 → MD 模拟（100 ns）→ 结合自由能计算（MM-PBSA）。
- **验证方式**：与本文 ASP185/ARG189/LYS217 突变数据对比；若预测的新位点与实验一致，则验证方法可靠性。
- **创新状态**：unverified

**候选 2：SoxNeuroA 的全基因组结合位点鉴定（ChIP-seq）与 scopoletin 处理后的动态变化**
- **来源局限/观察**：本文仅验证了 Orai1 一个靶基因，SoxNeuroA 可能调控更多基因。
- **核心假设**：SoxNeuroA 在螨虫基因组中结合数百个位点，scopoletin 处理后结合谱发生全局性改变。
- **增量**：从单基因到全基因组，揭示 scopoletin 的全局转录调控网络。
- **初步方法**：抗 SoxNeuroA 抗体 ChIP-seq（处理 vs 对照）→ 结合基序 de novo 分析 → 与 RNA-seq 联合分析 → 通路富集。
- **验证方式**：随机选取 5-10 个新靶基因进行 Y1H/双荧光素酶验证。
- **创新状态**：unverified

**候选 3：基于深度学习的 SoxNeuroA–DNA 结合位点预测模型**
- **来源局限/观察**：本文仅鉴定了一个 7-bp 基序（ATCAAAG），可能未覆盖 SoxNeuroA 的全部结合特异性。
- **核心假设**：用深度学习模型（如 CNN/DNABERT）可从 SoxNeuroA ChIP-seq 数据中学习更复杂的结合特异性，预测精度高于位置权重矩阵（PWM）。
- **增量**：为 Sox 家族 TF 提供可迁移的预测模型，可用于其他螨类/节肢动物 TF。
- **初步方法**：收集 SoxNeuroA ChIP-seq 数据 → 训练 CNN 模型 → 与 PWM 比较 AUC → 模型可解释性分析（如 saliency map）。
- **验证方式**：预测的新位点用 EMSA 验证。
- **创新状态**：unverified

**候选 4：scopoletin 类似物的结构-活性关系（SAR）与 SoxNeuroA 结合优化**
- **来源局限/观察**：本文仅研究了 scopoletin 一个化合物，未探索其结构类似物。
- **核心假设**：scopoletin 的香豆素母核和特定取代基对 SoxNeuroA 结合至关重要，修饰可提高亲和力和杀螨活性。
- **增量**：为杀螨剂先导优化提供方向。
- **初步方法**：合成 10-20 个 scopoletin 衍生物 → MST 测定结合亲和力 → 杀螨活性测定 → 建立 SAR 模型（可结合机器学习）。
- **验证方式**：最优化合物进行 RNAi 表型对比和 Ca²⁺ 成像。
- **创新状态**：unverified

**候选 5：SoxNeuroA–Orai1 调控轴的体内功能验证（CRISPR/Cas9 敲入报告系统）**
- **来源局限/观察**：本文所有功能实验均为体外/异源系统，缺乏体内证据。
- **核心假设**：在螨虫体内敲除 SoxNeuroA 或突变 Orai1 启动子上的 ATCAAAG 位点，可模拟 scopoletin 的杀螨效果。
- **增量**：将体外机制提升至体内因果验证。
- **初步方法**：CRISPR/Cas9 敲入荧光报告基因至 Orai1 位点 → 突变 ATCAAAG → 观察 scopoletin 敏感性变化 → 钙成像。
- **验证方式**：突变体螨虫对 scopoletin 的 LC50 变化。
- **创新状态**：unverified（注：螨虫 CRISPR 技术可能尚不成熟，需先验证可行性）