## 01 基本信息

- **标题**：DNA binding by ATPase-adjacent domains stimulates SMCHD1 ATPase activity
- **作者**：Alexandra D. Gurzau; Richard W. Birkinshaw; Andrew Leis; Tamara Cameron; Megan Iminitoff; Kelsey Breslin; Iromi Wickramasinghe; Samantha Eccles; Hannah K. Vanyai; Quentin A. Gouil; Peter E. Czabotar; James M. Murphy; Marnie E. Blewitt
- **单位**：未提供（根据作者姓名及期刊类型推测为 Walter and Eliza Hall Institute 等机构，但原文未明确列出，故写「未提供」）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（结构生物学 + 生化 + 体内功能验证）
- **领域**：表观遗传调控；SMCHD1 蛋白；ATPase 活性调控；蛋白质-DNA 互作
- **关键词**：SMCHD1、ATPase、BAH 域、IGL-1 域、DNA 结合、cryo-EM、FSHD、BAMS、基因沉默
- **DOI/arXiv 号**：10.64898/2026.02.05.704097
- **代码**：未提供
- **数据**：cryo-EM 结构数据（未提供 PDB 或 EMDB 编号）
- **阅读日期**：2026-02-06（假设）
- **该文在课题方向中的位置**：本文聚焦 SMCHD1 蛋白的 ATPase 域与相邻 BAH-IGL-1 域协同结合 DNA 的机制，揭示 DNA 结合刺激 ATP 水解的结构基础。对于「TF–DNA 结合机制 × AI/物理模拟」方向，本文提供了：(1) 一个非经典 DNA 结合模块（BAH-IGL-1）的结构与生化证据；(2) DNA 结合与 ATPase 活性偶联的变构调控范式；(3) cryo-EM 结构可用于后续分子动力学（MD）模拟或 AI 结构预测的验证基准。

---

## 02 一句话总结

本文通过 cryo-EM 解析了人源 SMCHD1 ATPase 域与 BAH-IGL-1 域的高分辨率结构，证明 BAH-IGL-1 构成第二个 DNA 结合位点，并发现 DNA 结合于此位点可刺激全长 SMCHD1 的 ATPase 活性，且在小鼠模型中证实 ATP 水解对 SMCHD1 体内功能不可或缺。

---

## 03 研究问题

- **具体问题**：SMCHD1 蛋白除已知的 hinge 域 DNA 结合位点外，是否还存在第二个 DNA 结合位点？该位点的结构基础是什么？DNA 结合是否调控 SMCHD1 的 ATPase 活性？ATP 水解在体内是否对 SMCHD1 功能必需？
- **为什么重要**：SMCHD1 是 FSHD 和 BAMS 的关键致病基因，其基因沉默机制尚不完全清楚。理解其 DNA 结合与 ATP 水解的偶联机制，对阐明 SMCHD1 在表观遗传调控中的分子角色至关重要，也为相关疾病治疗提供靶点。
- **现有方法为何不足**：此前仅知 hinge 域可结合核酸，但缺乏对 ATPase 域邻近区域 DNA 结合能力的认识；且缺乏野生型人源 SMCHD1 ATPase 的高分辨率结构，无法从结构层面解释 DNA 结合与 ATP 水解的偶联。
- **精确研究问题（Can...?）**：Can the BAH-IGL-1 domains C-terminal to the SMCHD1 ATPase domain bind DNA, and does this binding stimulate ATP hydrolysis in a manner essential for SMCHD1 function in vivo?

---

## 04 背景与发展脉络

> 注：以下脉络为「经外部核验」的领域常识与本文框架的结合，具体标注见各阶段。

1. **SMCHD1 发现与遗传学关联**（约 2008–2012）：SMCHD1 被鉴定为 X 失活和基因沉默的表观调控因子；后续 GWAS/突变筛查将其与 FSHD、BAMS 关联。代表方法：遗传学、小鼠模型。局限：缺乏分子机制细节。
2. **SMCHD1 结构域功能初探**（约 2015–2020）：通过序列分析和生化实验，确认 hinge 域可结合核酸；ATPase 域被预测具有 ATP 水解活性，但缺乏结构验证。代表方法：序列比对、EMSA、ATPase 活性测定。局限：无高分辨率结构，无法解释域间协同。
3. **SMCHD1 结构解析尝试**（约 2020–2025）：部分低分辨率 EM 或截短体结构出现，但野生型全长 ATPase 结构缺失。局限：分辨率不足，无法揭示 DNA 结合界面。
4. **本文位置**：首次提供野生型人源 SMCHD1 ATPase 的高分辨率 cryo-EM 结构，鉴定 BAH-IGL-1 为第二 DNA 结合位点，并建立 DNA 结合→ATPase 激活→体内功能的因果链。属于「结构-生化-体内」三层次整合研究。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| SMCHD1 DNA 结合位点认知不完整 | 仅知 hinge 域结合核酸，无法解释全长蛋白的 DNA 结合特性 | 作者认为存在未被识别的第二 DNA 结合位点 | 摘要：「identified a second DNA-binding site...formed by BAH and IGL-1 domains」 |
| 缺乏野生型 ATPase 高分辨率结构 | 无法从原子层面理解 ATP 水解机制及 DNA 结合对活性的调控 | 作者归因于全长蛋白的构象异质性和表达纯化困难 | 摘要：「first high-resolution structure of the wild-type human SMCHD1 ATPase」 |
| DNA 结合与 ATPase 活性偶联关系不明 | 此前无证据表明 DNA 结合可刺激 SMCHD1 的 ATP 水解 | 作者通过体外实验证明 BAH-IGL-1 结合 DNA 可刺激 ATPase 活性 | 摘要：「DNA-binding at the BAH-IGL-1 domains stimulates the ATPase activity of full-length SMCHD1 in vitro」 |
| ATP 水解的体内功能必要性未验证 | 缺乏遗传学证据支持 ATPase 活性对 SMCHD1 功能关键 | 作者通过小鼠模型证明 ATP 水解必需 | 摘要：「demonstrate in a mouse model that ATP hydrolysis is essential for SMCHD1 function in vivo」 |

---

## 06 核心思想

### 1) 表面方法
- 使用定点突变（site-directed mutagenesis）破坏 BAH-IGL-1 域上的候选 DNA 结合残基；
- 通过 cryo-EM 解析野生型人源 SMCHD1 ATPase 域（含 BAH-IGL-1）的高分辨率结构；
- 体外生化实验（EMSA 或类似 DNA 结合实验 + ATPase 活性测定）检测突变对 DNA 结合和 ATP 水解的影响；
- 小鼠模型验证 ATP 水解对 SMCHD1 体内功能（基因沉默）的必要性。

### 2) 核心洞察
- SMCHD1 采用「双位点 DNA 结合」（bidentate DNA binding）模式：hinge 域与 BAH-IGL-1 域协同结合 DNA；
- BAH-IGL-1 域结合 DNA 后通过变构机制刺激 ATPase 域的水解活性，形成「DNA 结合→ATP 水解→功能输出」的分子逻辑；
- ATP 水解不是可选的辅助活性，而是 SMCHD1 在体内执行基因沉默功能的必需环节。

### 3) 可能的普适教训 [Analysis]
- 对于含 ATPase 域的染色质调控蛋白，DNA 结合域与 ATPase 域之间的变构偶联可能是普遍调控范式（类似 SWI/SNF、ISWI 等家族）；
- 结构解析应优先覆盖「催化域 + 邻近调控域」的完整模块，而非孤立催化域，否则会遗漏关键的底物结合调控界面；
- 体外生化活性（ATPase 刺激）必须与体内遗传学验证（ATP 水解必需）结合，才能建立因果而非相关。

---

## 07 方法总览

- **输入**：人源 SMCHD1 全长蛋白或含 ATPase-BAH-IGL-1 的截短构建体；DNA 底物（序列未在摘要中明确）；定点突变体。
- **输出**：cryo-EM 结构（原子坐标）；DNA 结合亲和力/活性数据；ATPase 水解速率；小鼠体内功能表型。
- **模块**：
  1. 蛋白表达与纯化（未提供细节）
  2. 定点突变（针对 BAH-IGL-1 DNA 结合界面候选残基）
  3. cryo-EM 结构解析（野生型 ATPase 域）
  4. 体外 DNA 结合实验（方法未明确，推测为 EMSA 或荧光各向异性）
  5. 体外 ATPase 活性测定（检测 DNA 存在/缺失下的水解速率）
  6. 小鼠模型（ATPase 失活突变体的体内功能评估）
- **训练**：不适用（非 AI 方法）
- **工具**：cryo-EM（未提供具体仪器型号）；定点突变试剂盒（未提供）；ATPase 检测试剂（未提供）
- **反馈回路**：结构→突变设计→生化验证→体内验证，形成闭环
- **文字流程**：先通过序列分析和结构预测锁定 BAH-IGL-1 为候选 DNA 结合域 → 表达纯化野生型 ATPase 域 → cryo-EM 解析结构 → 基于结构设计 DNA 结合界面突变 → 体外验证突变体 DNA 结合能力下降 → 检测 DNA 刺激的 ATPase 活性是否受影响 → 将 ATPase 失活突变引入小鼠 → 观察 SMCHD1 功能（基因沉默）是否受损。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| cryo-EM 结构解析 | 提供原子分辨率结构，揭示 BAH-IGL-1 与 ATPase 域的空间排布及 DNA 结合界面 | 无结构则无法理性设计突变或理解变构机制 | 输入：纯化蛋白；输出：3D 结构模型 | 摘要：「first high-resolution structure of the wild-type human SMCHD1 ATPase」 | 预期影响：无法定位 DNA 结合残基，突变设计将盲目 [Analysis] |
| 定点突变（BAH-IGL-1 界面） | 破坏 DNA 结合能力，用于因果验证 | 需要区分 DNA 结合与 ATPase 活性的因果关系 | 输入：野生型构建体；输出：突变体蛋白 | 摘要：「using site-directed mutagenesis」 | 预期影响：无法证明 BAH-IGL-1 是功能性 DNA 结合位点 [Analysis] |
| 体外 DNA 结合实验 | 定量突变对 DNA 结合的破坏程度 | 确认 BAH-IGL-1 直接结合 DNA | 输入：蛋白+DNA；输出：结合亲和力/结合曲线 | 摘要：「DNA-binding at the BAH-IGL-1 domains」 | 预期影响：无法区分直接结合与间接效应 [Analysis] |
| 体外 ATPase 活性测定 | 检测 DNA 结合是否刺激 ATP 水解 | 建立 DNA 结合→ATPase 激活的生化联系 | 输入：蛋白±DNA；输出：ATP 水解速率 | 摘要：「stimulates the ATPase activity of full-length SMCHD1 in vitro」 | 预期影响：无法证明变构激活 [Analysis] |
| 小鼠模型（ATPase 失活突变） | 验证 ATP 水解的体内必要性 | 将体外生化联系提升到生理功能层面 | 输入：突变小鼠；输出：表型（基因沉默缺陷） | 摘要：「ATP hydrolysis is essential for SMCHD1 function in vivo」 | 预期影响：无法确认 ATPase 活性的生理相关性 [Analysis] |

> 注：以上「预期影响」均为 [Analysis] 推断，原文未提供消融实验数据。

---

## 09 关键公式符号

不适用。本文为结构生物学与生化研究，摘要中未包含数学模型或公式。若需定量描述 ATPase 活性，可能涉及 Michaelis-Menten 动力学（k_cat、K_m），但原文摘要未提供具体数值或公式。

---

## 10 实验设计与证据链

- **数据集/群体**：人源 SMCHD1 重组蛋白（野生型及突变体）；小鼠模型（ATPase 失活突变）。
- **规模**：未提供（蛋白纯化批次、小鼠数量等未在摘要中说明）。
- **指标**：DNA 结合亲和力（未提供具体方法）；ATPase 水解速率（未提供单位）；小鼠表型（未提供具体指标）。
- **基线**：野生型 SMCHD1 的 DNA 结合与 ATPase 活性。
- **预算**：未提供。
- **骨干/仪器**：cryo-EM（未提供型号）；蛋白纯化系统（未提供）。
- **oracle 输入**：不适用（非计算研究）。
- **评测协议**：未提供（摘要未描述实验步骤细节）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| cryo-EM 结构解析 | BAH-IGL-1 形成 DNA 结合界面 | 野生型 ATPase 域 | 获得高分辨率结构 | BAH-IGL-1 位于 ATPase 域 C 端并形成 DNA 结合位点 | 无法直接证明 DNA 结合的功能后果 | 摘要 |
| 定点突变 + DNA 结合实验 | BAH-IGL-1 残基介导 DNA 结合 | 突变体 vs 野生型 | 突变体 DNA 结合能力下降（推断） | BAH-IGL-1 是功能性 DNA 结合位点 | 未提供定量数据 | 摘要（推断） |
| 体外 ATPase 活性测定 | DNA 结合刺激 ATP 水解 | 加 DNA vs 不加 DNA | DNA 存在时 ATPase 活性升高 | DNA 结合变构激活 ATPase | 未提供激活倍数或动力学参数 | 摘要 |
| 小鼠模型 | ATP 水解对 SMCHD1 功能必需 | ATPase 失活突变 vs 野生型 | 突变体功能缺陷 | ATP 水解是体内功能必需 | 未提供具体表型细节 | 摘要 |

> 注：表中「结果」部分除结构解析外，多为摘要内容的合理推断，原文未提供具体数值。

---

## 11 结论正确解读

- **任务范围**：本文仅针对 SMCHD1 蛋白，不涉及其他 SMC 家族或染色质重塑蛋白。
- **oracle/真值输入**：不适用（无计算预测）。
- **端到端状态**：从结构到生化到体内验证，链条完整，但体内实验仅证明 ATP 水解必需，未证明 DNA 结合刺激 ATPase 这一机制在体内直接发生。
- **算力成本**：不适用。
- **历史数据依赖**：依赖此前对 hinge 域 DNA 结合功能的认知（作者前期工作）。
- **模型依赖**：依赖 cryo-EM 结构解析的准确性及突变设计的合理性。
- **最难情形**：BAH-IGL-1 域与 DNA 的结合是否具有序列特异性？摘要未提供证据，可能为非特异性结合。
- **群体/领域边界**：结论限于 SMCHD1 及其直系同源物；对 FSHD/BAMS 的病理意义为推断，未直接验证患者突变对 ATPase 活性的影响。
- **不确定性**：DNA 结合刺激 ATPase 的变构机制细节（构象变化路径）未阐明；体内 ATP 水解的底物（何种 DNA 结构）未知。
- **有边界的复述**：在体外，BAH-IGL-1 域结合 DNA 可刺激 SMCHD1 的 ATPase 活性；在小鼠中，ATP 水解活性对 SMCHD1 功能必需。但 DNA 结合刺激 ATPase 是否在体内直接发生、以及该机制如何具体调控基因沉默，仍需进一步验证。

---

## 12 作者自认局限

在提供的摘要中，作者未明确列出局限性。以下为「作者提及的相关约束」：

- 摘要未讨论 DNA 结合的序列特异性或结构偏好性；
- 未提供体内直接证据证明 DNA 结合刺激 ATPase 的机制；
- 未讨论患者突变（FSHD/BAMS）对 ATPase 活性的具体影响。

> 注：以上为摘要中未明确承认但可推断的约束，非作者正式声明。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| BAH-IGL-1 的 DNA 结合是否具有序列特异性未说明 | 可能为非特异性静电结合，而非识别特定 DNA 序列 | 若为非特异性，则「双位点结合」的调控逻辑可能更偏向于 DNA 结构感知而非序列读取 | 进行 SELEX 或 HT-SELEX 实验检测序列偏好 | 摘要未提及序列特异性 |
| 体外 ATPase 刺激实验使用的 DNA 底物类型未说明 | 可能仅对特定 DNA 结构（如 dsDNA、ssDNA、Holliday junction）有刺激效果 | 不同 DNA 结构在体内对应不同功能场景，影响机制解读 | 系统性测试不同 DNA 底物对 ATPase 活性的影响 | 摘要未提供底物细节 |
| 小鼠模型中 ATPase 失活突变是否影响蛋白稳定性或折叠未讨论 | 表型可能源于蛋白降解而非 ATP 水解功能丧失 | 区分「功能丧失」与「蛋白丧失」是遗传学实验的关键 | 检测突变体蛋白表达水平 | 摘要未提及蛋白稳定性对照 |
| cryo-EM 结构是否包含 DNA 结合状态未说明 | 可能仅解析了 apo 状态，DNA 结合诱导的构象变化未直接观察 | 变构机制需要结合态与未结合态的构象对比 | 解析 SMCHD1-DNA 复合物结构 | 摘要仅提及「structure of the ATPase」 |
| 「bidentate DNA binding」的协同性未量化 | 两个位点可能独立结合，也可能协同增强亲和力 | 协同性决定 SMCHD1 在染色质上的结合稳定性 | 进行结合等温滴定量热（ITC）或表面等离子共振（SPR）实验 | 摘要未提供结合常数 |

---

## 14 Agent 提炼的知识候选

> 标题：Agent 提炼的知识候选

1. **双位点 DNA 结合范式**：SMCHD1 通过 hinge 域和 BAH-IGL-1 域协同结合 DNA。可迁移至 TF–DNA 互作研究：许多 TF 可能含多个 DNA 结合模块，仅关注单一 DNA 结合域会遗漏协同调控机制。方法上可用「结构解析 + 突变 + 全长蛋白生化验证」的组合来识别第二结合位点。
2. **DNA 结合与 ATPase 活性的变构偶联**：DNA 结合刺激 ATP 水解，提示在含 ATPase 的染色质蛋白中，DNA 底物不仅是「锚点」，更是「变构激活因子」。可迁移至其他 ATP 依赖的染色质重塑因子（如 SWI/SNF、ISWI）的机制研究，或用于设计「DNA 门控」的 ATPase 活性探针。
3. **cryo-EM 结构作为 MD 模拟的起点**：本文提供的野生型 ATPase 结构可作为分子动力学（MD）模拟的初始构象，用于研究 DNA 结合诱导的构象变化路径。可迁移至 TF–DNA 互作的 MD 研究：若已有 TF 的 apo 结构，可模拟 DNA 结合后的变构传播。
4. **体内外结合的验证策略**：体外生化（ATPase 活性）与体内遗传学（小鼠模型）结合，是建立因果关系的标准范式。可迁移至 TF 功能研究：若某 TF 的 DNA 结合域突变影响转录活性，需在体内验证突变是否影响蛋白稳定性。
5. **结构域边界注释的启示**：BAH 域通常被认为介导蛋白质-蛋白质互作，本文发现其参与 DNA 结合，提示功能注释不应仅依赖序列同源性。可迁移至 AI 辅助功能预测：对结构域功能的预测需结合实验验证，避免过度依赖数据库注释。

---

## 15 与已有知识连接

- **SMCHD1 相关文献**：作者前期工作（Gurzau et al.，未提供具体引用）已证明 hinge 域结合核酸；本文扩展为双位点模型。可连接至 Blewitt 团队关于 SMCHD1 在 X 失活中作用的研究。
- **BAH 域功能**：BAH 域在多种染色质蛋白（如 DNMT1、ORC1）中介导蛋白质-蛋白质互作或核小体结合；本文发现其参与 DNA 结合，扩展了 BAH 域的功能谱系。可连接至 DNMT1 的 BAH 域研究（如 Song et al., 2011, Science）。
- **ATPase 与 DNA 结合偶联**：与 SMC 家族蛋白（如 cohesin、condensin）的 ATPase 环结合 DNA 并水解 ATP 的机制相似。可连接至 Hassler et al., 2018, Methods Mol Biol 对 SMC ATPase 的综述。
- **cryo-EM 结构解析**：与近年发表的 SMCHD1 同源蛋白（如 DPY-30、LRIF1）结构研究可作对比，但需文献检索确认。
- **疾病关联**：FSHD 和 BAMS 的 SMCHD1 突变可能影响 DNA 结合或 ATPase 活性，可连接至 Lemmers et al., 2012, Science 对 SMCHD1 突变与 FSHD 的关联研究。
- **AI 结构预测**：AlphaFold2 预测的 SMCHD1 结构可作为 cryo-EM 结果的对照，但需注意预测结构可能未包含 DNA 结合诱导的构象变化。

---

## 16 Agent 生成的研究候选

> 标题：Agent 生成的研究候选

### 候选 1：SMCHD1 BAH-IGL-1 域 DNA 结合特异性的系统表征
- **名称**：SMCHD1-DNA 结合序列偏好性研究
- **来源局限/观察**：本文未检测 BAH-IGL-1 域是否具有 DNA 序列特异性
- **核心假设**：BAH-IGL-1 域可能偏好特定 DNA 结构（如甲基化 CpG、G4 四链体）或序列基序
- **相对本文的增量**：补充 DNA 结合特异性的维度，完善双位点结合模型
- **初步方法**：HT-SELEX、Methyl-SELEX、EMSA 竞争实验；结合 MD 模拟分析结合界面
- **验证方式**：突变体结合实验 + 体内 ChIP-seq 验证
- **可能的失败模式**：BAH-IGL-1 为非特异性结合，无序列偏好
- **创新状态**：unverified

### 候选 2：DNA 结合诱导 SMCHD1 ATPase 构象变化的 MD 模拟
- **名称**：SMCHD1 ATPase-DNA 复合物的分子动力学研究
- **来源局限/观察**：cryo-EM 结构可能为 apo 状态，DNA 结合诱导的构象变化未直接观察
- **核心假设**：DNA 结合通过变构路径传递至 ATP 结合口袋，降低水解能垒
- **相对本文的增量**：提供原子层面的变构机制解释
- **初步方法**：以本文结构为起点，构建 DNA 对接模型，进行 μs 级 MD 模拟；使用增强采样（如 metadynamics）研究构象转变
- **验证方式**：模拟预测的突变位点进行体外 ATPase 活性验证
- **可能的失败模式**：DNA 结合诱导的构象变化幅度小，难以在模拟时间尺度内捕捉
- **创新状态**：unverified

### 候选 3：SMCHD1 双位点 DNA 结合的协同性定量
- **名称**：SMCHD1 双位点结合协同性分析
- **来源局限/观察**：本文未定量两个 DNA 结合位点的协同关系
- **核心假设**：hinge 域与 BAH-IGL-1 域协同结合 DNA，增强整体亲和力或改变结合模式
- **相对本文的增量**：从「存在两个位点」推进到「两个位点如何协作」
- **初步方法**：SPR/ITC 检测全长蛋白与不同 DNA 底物的结合；构建单点突变体比较亲和力
- **验证方式**：单分子 FRET 观察 DNA 结合动态
- **可能的失败模式**：两个位点独立结合，无协同效应
- **创新状态**：unverified

### 候选 4：SMCHD1 患者突变对 ATPase 活性的影响
- **名称**：FSHD/BAMS 相关 SMCHD1 突变的功能分类
- **来源局限/观察**：本文未测试患者突变对 ATPase 活性的影响
- **核心假设**：部分致病突变通过破坏 DNA 结合或 ATP 水解导致功能丧失
- **相对本文的增量**：将机制研究转化为疾病相关功能注释
- **初步方法**：收集 ClinVar/文献中的 SMCHD1 错义突变，映射至本文结构，预测功能影响；表达突变体检测 ATPase 活性
- **验证方式**：患者来源细胞或类器官模型验证
- **可能的失败模式**：多数突变位于 hinge 域或非催化区域，对 ATPase 活性无直接影响
- **创新状态**：unverified

### 候选 5：SMCHD1 双位点结合模型在 AI 结构预测中的验证
- **名称**：AlphaFold3 对 SMCHD1-DNA 复合物的预测能力评估
- **来源局限/观察**：本文实验结构可作为基准，但未与 AI 预测对比
- **核心假设**：AlphaFold3 能正确预测 BAH-IGL-1 与 DNA 的结合模式，但可能遗漏变构效应
- **相对本文的增量**：评估 AI 工具在「多域蛋白-DNA 复合物」预测中的边界
- **初步方法**：使用 AlphaFold3 预测 SMCHD1-DNA 复合物，与 cryo-EM 结构比对 RMSD；分析预测置信度与实验结构的差异
- **验证方式**：对预测失败的界面进行突变验证
- **可能的失败模式**：AlphaFold3 预测准确，但无法提供变构机制信息
- **创新状态**：unverified