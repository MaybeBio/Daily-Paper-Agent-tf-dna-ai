## 01 基本信息

- **标题**：Dockground: Expanding the Resource to Protein-DNA Complexes
- **作者与单位**：Collins, Keeley W; Copeland, Matthew M; Kundrotas, Petras J; Vakser, Ilya A（美国堪萨斯大学计算生物学中心，University of Kansas）
- **期刊/预印本平台**：Journal of Molecular Biology
- **年份**：2025（在线发表日期 2025-11-23）
- **论文类型**：数据库/资源描述论文（Database Resource Paper）
- **领域**：结构生物学、蛋白质-DNA 互作、计算建模、基准数据集
- **关键词**：Dockground；protein-DNA complexes；docking benchmark；AlphaFold3；macromolecular interactions
- **DOI/arXiv 号**：10.1016/j.jmb.2025.169553
- **代码**：未提供（数据库本身为资源）
- **数据**：Dockground 数据库，公开访问 https://dockground.compbio.ku.edu
- **阅读日期**：2026-05-13
- **该文在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 计算建模」方向的**数据基础设施**类工作。它不提出新的 AI 方法或物理模拟算法，而是提供**最大规模、每周自动更新的蛋白-DNA 复合物基准数据集**，用于 docking 和机器学习方法的训练与评测。对 TF-DNA 结合机制研究而言，该资源可作为 benchmark 数据源和模型评测平台，尤其文中以 AlphaFold3 为例展示了如何用该数据集评测 AI 结构预测方法在蛋白-DNA 界面建模上的表现。

---

## 02 一句话总结

本文扩展 Dockground 数据库以纳入蛋白-DNA 复合物，提供每周自动更新、含冗余与非冗余版本的最大规模蛋白-DNA 互作数据集，并以 AlphaFold3 在 691 个非冗余结构上的基准测试展示其用于评测 AI 预测工具在蛋白-DNA 界面建模能力的实用性。

---

## 03 研究问题

- **具体问题**：如何构建一个大规模、持续更新、覆盖全面且便于检索的蛋白-DNA 复合物结构数据集，以支持 docking 和机器学习方法的开发与基准测试？
- **为什么重要**：蛋白-DNA 互作是复制、转录、包装和 DNA 修复等关键细胞过程的基础。实验解析蛋白-DNA 复合物结构困难且数量有限，计算建模（尤其是 AI 方法）成为重要补充。但现有蛋白-DNA 基准数据集规模小、更新不及时，难以满足新一代 AI 方法（如 AlphaFold3）的训练与评测需求。
- **现有方法为何不足**：已发表的蛋白-DNA benchmark 数据集（文献 [13-15]）通常结构数量有限且不持续更新，无法跟上 PDB 中新增结构的步伐，也难以支撑需要大规模训练数据的深度学习方法。
- **精确的「Can ... ?」研究问题**：Can a comprehensive, weekly-updated, non-redundant protein-DNA complex dataset be constructed from the PDB to serve as a benchmarking resource for evaluating AI-based structure prediction methods such as AlphaFold3?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 及相关引用，属于「经外部核验」的领域发展框架。

1. **实验结构解析阶段**：蛋白-DNA 复合物结构解析困难（不稳定、成本高），实验结构数量远少于蛋白-蛋白复合物。代表性方法：X-ray crystallography、cryo-EM、NMR。
2. **计算 docking 阶段**：基于物理/几何互补的蛋白-DNA docking 方法，如 pyDockDNA [8]、NPDock [9]、HDOCK [10]。局限：依赖评分函数精度，对构象变化敏感，成功率有限。
3. **机器学习预测阶段**：AlphaFold [11] 的成功推动了蛋白-蛋白复合物预测的突破，随后 AlphaFold3 和 RoseTTAFoldNA [12] 扩展至蛋白-核酸复合物预测。局限：需要大规模高质量训练/评测数据，现有 benchmark 数据集规模不足。
4. **Dockground 资源演化**：Dockground 项目此前已建立蛋白-蛋白 [16-19] 和蛋白-RNA [20] 复合物数据集，本文将其扩展至蛋白-DNA，并引入每周自动更新机制。

**本文主张的位置**：Dockground 蛋白-DNA 数据集是当前**最大、最全面、每周更新**的蛋白-DNA 复合物基准资源，填补了现有数据集在规模、时效性和可检索性上的空白。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 蛋白-DNA 复合物实验结构稀缺 | 实验解析困难、成本高、结构不稳定 | DNA 复合物稳定性差，结晶困难 | Introduction 节，引用文献 [6] |
| 现有蛋白-DNA benchmark 数据集规模小 | 结构数量有限，覆盖面窄 | 数据集构建后未持续更新 | Introduction 节，引用文献 [13-15] |
| 现有数据集更新不及时 | 无法纳入 PDB 新增结构 | 缺乏自动化更新流程 | Introduction 节：「such sets often are not updated」 |
| 机器学习方法需要大规模评测数据 | AlphaFold3 等新方法缺乏足够大的基准集 | 现有数据集不足以支撑可靠 benchmark | Introduction 节：「it is important to benchmark these programs on large representative sets」 |
| 蛋白-DNA 界面建模精度不足 | AlphaFold3 在界面水平预测准确率有限 | 模型可能整体结构正确但界面错误 | Benchmarking 节：「AlphaFold3 modeling may yield an overall accurate structure with a less accurate or even possibly wrong interface」 |

---

## 06 核心思想

### 1) 表面方法
构建一个从 PDB 自动提取蛋白-DNA 复合物结构的数据集，提供冗余和非冗余两个版本，配备用户友好的 Web 检索界面，并每周自动更新。

### 2) 核心洞察
- **数据规模与时效性是 AI 方法评测的关键**：机器学习方法（如 AlphaFold3）的可靠评测需要大规模、非冗余、持续更新的基准数据集，而现有资源无法满足这一需求。
- **蛋白-DNA 复合物的定义需要明确标准**：一个复合物 = 一条蛋白链 + 两条形成双螺旋的 DNA 链（或单链 DNA 时一条链），且每条链至少有一个界面残基/核苷酸。
- **多维度非冗余策略**：同时基于序列同一性（MMseqs2）和结构相似性（Foldseek/TM-score）进行冗余去除，提供不同严格度的非冗余版本。

### 3) 可能的普适教训 [Analysis]
- **数据基础设施是 AI 方法发展的瓶颈**：在结构预测领域，方法创新与数据资源建设同等重要。一个高质量、持续更新的基准数据集可以显著加速方法迭代。
- **「每周更新」机制值得借鉴**：将数据集的更新自动化、常态化，使其与 PDB 增长同步，是维持资源长期价值的有效策略。
- **多版本非冗余设计**：提供不同严格度的非冗余版本（序列 vs 结构、不同阈值），可满足不同应用场景（如训练 vs 评测）的需求。

---

## 07 方法总览

- **输入**：PDB 数据库中的 CIF biounit 文件（截至 2025 年 6 月 16 日的全部结构）
- **输出**：蛋白-DNA 复合物数据集（含冗余和非冗余版本），可通过 Web 界面检索和下载
- **主要模块**：
  1. **数据提取**：从 PDB CIF biounit 文件中检测所有蛋白-DNA 互作链对
  2. **复合物定义**：蛋白-DNA 复合物 = 1 条蛋白链 + 2 条形成双螺旋的 DNA 链（或单链 DNA 时 1 条 DNA 链）
  3. **过滤标准**：蛋白链 ≥ 30 残基，DNA 链 ≥ 6 核苷酸，每条链至少 1 个界面残基/核苷酸
  4. **注释生成**：每条链记录链 ID、biounit 模型号、链类型、总残基数、界面残基数、埋藏溶剂可及表面积（VoroContacts [21]）、界面残基范围；蛋白链额外记录 UniProt ID、canonical 序列、SEQRS 比对、Pfam/InterPro 结构域数 [22]；复合物级注释包括物种、实验方法及分辨率、多聚状态、同源/异源类型、PDB 关键词、释放日期、膜存在、二硫键和界面配体
  5. **冗余去除**：序列同一性（MMseqs2 [24]，蛋白 30%/40%/50%，DNA 70%）和结构相似性（Foldseek [25]，TM-score 0.6/0.9）两种策略
  6. **Web 界面**：支持按 PDB 代码或过滤条件检索，提供 Jmol [23] 可视化
- **训练**：不适用（数据集构建，非模型训练）
- **反馈回路**：每周二自动更新，跟随 PDB 周一更新
- **假设**：PDB 中 CIF biounit 文件能正确反映生物学相关的蛋白-DNA 复合物组装状态

**文字流程**：从 PDB 获取全部 CIF biounit 文件 → 检测所有蛋白-DNA 链对 → 按复合物定义组装（1 蛋白 + 2 DNA 或 1 蛋白 + 1 ssDNA）→ 应用过滤标准 → 计算界面特征和注释 → 执行序列和结构层面的冗余去除 → 发布至 Web 界面供检索和下载 → 每周自动重复。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 数据提取与复合物定义 | 从 PDB 中识别蛋白-DNA 互作复合物 | 定义清晰、一致的复合物标准是数据集质量的基础 | 输入：PDB CIF biounit 文件；输出：蛋白-DNA 链对列表 | Database Curation 节 | 预期影响：无此模块则无法从 PDB 中系统提取蛋白-DNA 复合物 [Analysis] |
| 过滤标准（≥30 残基、≥6 核苷酸、≥1 界面残基） | 排除过短或非功能性互作 | 确保复合物具有生物学意义和结构可建模性 | 输入：候选链对；输出：合格复合物 | Database Curation 节 | 预期影响：放宽标准会增加噪声数据，收紧则减少覆盖 [Analysis] |
| 界面特征计算（VoroContacts） | 计算埋藏溶剂可及表面积和界面残基 | 提供界面定量描述，支持 docking 和 ML 特征工程 | 输入：复合物结构；输出：埋藏面积、界面残基列表 | Database Curation 节，引用 [21] | 预期影响：无此模块则数据集缺乏界面级信息，降低对 TF-DNA 结合机制研究的直接可用性 [Analysis] |
| 蛋白链注释（UniProt、Pfam/InterPro） | 关联蛋白功能、结构域和序列信息 | 支持功能分析和同源关系识别 | 输入：蛋白链序列；输出：UniProt ID、结构域注释 | Database Curation 节，引用 [22] | 预期影响：移除后难以将结构数据与功能注释关联 [Analysis] |
| 序列冗余去除（MMseqs2） | 按序列同一性聚类去冗余 | 避免训练/评测集中的序列偏差 | 输入：全部链序列；输出：非冗余链集合 | Database Curation 节，引用 [24] | 预期影响：移除后数据集存在序列偏差，影响 benchmark 公平性 [Analysis] |
| 结构冗余去除（Foldseek/TM-score） | 按结构相似性聚类去冗余 | 结构层面的去冗余对 docking 评测更严格 | 输入：全部链结构；输出：结构非冗余集合 | Database Curation 节，引用 [25] | 预期影响：移除后结构相似的复合物可能重复计入，高估方法性能 [Analysis] |
| Web 检索界面 | 用户可搜索和下载复合物子集 | 提升资源可用性和灵活性 | 输入：用户查询条件；输出：匹配复合物列表和下载 | User Interface 节 | 预期影响：移除后资源可用性大幅下降 [Analysis] |
| 每周自动更新 | 定期纳入 PDB 新增结构 | 保持数据集时效性 | 输入：PDB 每周更新；输出：新增复合物 | Database Curation 节 | 预期影响：移除后数据集逐渐过时，重蹈现有数据集覆辙 [Analysis] |

---

## 09 关键公式符号

**不适用**。本文为数据库资源描述论文，未提出新的数学模型或算法公式。涉及的量化指标（如序列同一性阈值、TM-score 阈值）为已有工具（MMseqs2、Foldseek）的参数设置，而非本文新提出的公式。

---

## 10 实验设计与证据链

### 数据集/群体
- **数据源**：PDB 全部 CIF biounit 文件（截至 2025 年 6 月 16 日）
- **数据集规模**：Table 1 展示数据库内容（具体数值未在摘要中提供，需查阅原文）
- **评测子集**：691 个非冗余蛋白-DNA 结构（序列同一性 30% 蛋白 / 70% DNA 去冗余），含 2042 个 pairwise 蛋白-DNA 复合物
- **时间过滤**：所有评测结构为 2021 年 9 月 30 日之后存入 PDB，确保不在 AlphaFold3 训练集中

### 评测指标
- **DockQ score**：复合物模型质量综合评分
- **i-RMSD**：界面均方根偏差
- **L-RMSD**：配体均方根偏差
- **CAPRI-like 分类**：按 Supplemental Table S1 标准将模型质量分级

### 评测协议
- AlphaFold3 对每个结构生成 5 个模型，各指标取 5 模型平均值
- 质量分级按 CAPRI-like 标准

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-------------------|------|
| AlphaFold3 在 691 个非冗余蛋白-DNA 复合物上的基准测试 | Dockground 蛋白-DNA 数据集可用于评测 AI 预测方法 | 2021 年 9 月 30 日后存入 PDB 的结构，5 模型平均 | 结果分布见 Figure S2（具体数值未在摘要中提供） | 数据集可用于 AI 方法基准测试 | 无法从摘要判断 AlphaFold3 的绝对性能水平 | Benchmarking 节，Figure S2 |
| i-RMSD 与 L-RMSD 评估结果对比 | AlphaFold3 可能整体结构正确但界面不准确 | 同一批 691 个结构，两种指标分别评估 | i-RMSD 评估的「错误建模」比例高于 L-RMSD | AlphaFold3 在界面水平预测精度可能低于整体结构精度 | 无法从摘要判断差异的具体幅度 | Benchmarking 节 |

---

## 11 结论正确解读

- **任务范围**：本文结论仅涉及数据集的构建和可用性展示，不涉及对 AlphaFold3 性能的全面评测结论。
- **Oracle/真值输入**：数据集以 PDB 实验结构为真值，但未讨论实验结构的质量差异（分辨率范围未在摘要中给出）。
- **端到端状态**：数据集构建流程已完整实现并公开部署，但「每周更新」的长期运行效果尚需时间验证。
- **算力成本**：未提供 AlphaFold3 推理的计算资源信息。
- **历史数据依赖**：数据集内容依赖 PDB 的积累速度和质量；评测子集的时间过滤（2021 年 9 月 30 日后）确保与 AlphaFold3 训练集无重叠，但其他 AI 方法的训练集重叠情况未讨论。
- **模型依赖**：基准测试仅针对 AlphaFold3，不代表其他方法在该数据集上的表现。
- **最难情形**：摘要未讨论哪些类型的蛋白-DNA 复合物（如 TF 特异性、弯曲 DNA、多聚体等）对预测最具挑战性。
- **群体/领域边界**：数据集覆盖所有蛋白-DNA 复合物类型，但未按 TF 家族、DNA 基序或生物学功能分类；对 TF-DNA 结合机制研究而言，需要自行筛选相关子集。
- **不确定性**：i-RMSD 与 L-RMSD 的差异提示界面预测精度可能低于整体结构精度，但差异幅度和具体失败模式未在摘要中详述。

**有边界的复述**：Dockground 蛋白-DNA 数据集提供了当前最大规模、每周更新的蛋白-DNA 复合物结构资源，并展示了其用于评测 AlphaFold3 界面预测能力的可行性；初步证据提示 AlphaFold3 在界面水平（i-RMSD）的预测准确率可能低于整体结构水平（L-RMSD），但具体性能需查阅完整数据。

---

## 12 作者自认局限

在提供的摘要和正文框架中，作者未明确列出「局限性」章节。以下为作者提及的相关约束（非正式局限）：

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未提供（作者未在摘要中明确承认局限） | — | — | — |

**作者提及的相关约束**（非正式局限）：
- 数据集依赖 PDB 中已有的实验结构，而蛋白-DNA 复合物实验结构本身数量有限（Introduction 节）。
- 冗余去除中 DNA 链仅使用 70% 序列同一性阈值，作者指出「无法确定当前文献中 DNA 结构相似性的标准 cutoff」（Database Curation 节：「We could not identify current publications that suggest a sequence identity cutoff for DNA structural similarity」）。
- 未来计划包括为蛋白-DNA 结构添加 unbound/modeled、docking decoys 和 templates 等衍生数据集（Conclusion 节），暗示当前版本尚缺这些功能。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 复合物定义（1 蛋白 + 2 DNA 链）可能过于简化 | 某些蛋白-DNA 复合物可能涉及多蛋白亚基或多段 DNA；将复合物简化为单蛋白链可能丢失生物学上下文 | TF 常以二聚体或多聚体形式结合 DNA，单链定义可能不适用于所有 TF-DNA 复合物 | 检查数据集中是否包含多链蛋白-DNA 复合物的替代表示；与 PDB 中已知 TF-DNA 复合物的生物学组装对比 | Database Curation 节 |
| 过滤标准（蛋白 ≥30 残基）可能排除 DNA 结合结构域（DBD）较短的蛋白 | 许多 TF 的 DBD 小于 30 残基（如某些锌指蛋白），但全长蛋白可能满足标准；若按链而非结构域过滤，短 DBD 可能被遗漏 | 对 TF-DNA 结合机制研究，短 DBD 的识别和建模同样重要 | 统计数据集中 DBD 长度分布；与已知 TF DBD 数据库（如 TRANSFAC）交叉验证 | Database Curation 节 |
| DNA 冗余去除仅用 70% 序列同一性，缺乏结构层面标准 | DNA 序列同一性与结构相似性相关性可能不如蛋白；不同序列的 DNA 可能形成相似结构 | 结构层面的 DNA 冗余可能影响 benchmark 的公平性 | 对 DNA 链执行结构比对（如 RNAcomposer 或 Curves+），比较序列 vs 结构聚类结果 | Database Curation 节 |
| AlphaFold3 基准测试仅用 DockQ 系列指标 | DockQ 主要评估整体复合物几何质量，可能不敏感于 TF 特异性碱基识别（base readout）或 DNA 构象变化 | TF-DNA 结合机制研究关注序列特异性识别，需要更细粒度的界面评估指标 | 使用碱基接触图、氢键网络、DNA 弯曲角度等补充指标重新评估 | Benchmarking 节 |
| 时间过滤（2021 年 9 月 30 日后）仅确保与 AlphaFold3 训练集无重叠 | 其他 AI 方法（如 RoseTTAFoldNA）的训练集时间范围可能不同 | 数据集用于其他方法评测时可能存在数据泄漏 | 与各方法的训练集时间戳逐一核对 | Benchmarking 节 |
| 未讨论实验结构质量（分辨率）对 benchmark 的影响 | 低分辨率结构可能引入界面几何误差，影响评测公平性 | 对 docking 和 ML 方法评测，结构质量是重要协变量 | 按分辨率分层分析 AlphaFold3 性能 | Benchmarking 节 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **可迁移概念：多版本非冗余数据集设计**
   - 本文同时提供基于序列（MMseqs2）和结构（Foldseek/TM-score）的非冗余版本，且设置多个阈值（30%/40%/50% 蛋白，70% DNA；TM-score 0.6/0.9）。
   - **迁移到 TF-DNA 课题**：构建 TF-DNA 结合数据集时，可同时提供序列和结构层面的非冗余版本，满足不同训练/评测需求。对 TF 而言，DNA 结合结构域的序列保守性可能比全长蛋白更重要，可考虑按 DBD 区域而非全长序列做冗余去除。

2. **可迁移方法：复合物定义与界面检测标准**
   - 明确的复合物定义（1 蛋白 + 2 DNA 链形成双螺旋）和界面残基/核苷酸检测标准（至少 1 个界面残基）。
   - **迁移到 TF-DNA 课题**：研究 TF-DNA 结合机制时，可借鉴此标准定义「功能性结合界面」，并进一步细化——如区分直接碱基接触（base readout）和骨架接触（shape readout），或按接触类型（氢键、疏水、范德华）分类界面残基。

3. **可迁移工具：VoroContacts 用于界面特征计算**
   - 使用 Voronoi 镶嵌计算埋藏溶剂可及表面积和界面残基。
   - **迁移到 TF-DNA 课题**：VoroContacts 可扩展用于计算 TF-DNA 界面的几何互补性、接触面积和原子接触数，这些特征可作为 ML 模型的输入特征，或用于分析 TF 结合特异性与界面几何的关系。

4. **可迁移实验设计：时间过滤确保训练/评测分离**
   - 评测 AlphaFold3 时仅使用 2021 年 9 月 30 日后存入 PDB 的结构，确保不在训练集中。
   - **迁移到 TF-DNA 课题**：在评测任何 AI 结构预测或结合亲和力预测方法时，应严格按时间戳过滤训练集，避免数据泄漏。对 TF-DNA 结合预测，还需注意同一 TF 家族不同成员间的序列相似性可能导致的信息泄漏。

5. **可迁移洞察：界面精度 vs 整体精度的差异**
   - 本文发现 i-RMSD 评估的错误率高于 L-RMSD，提示模型可能整体结构正确但界面错误。
   - **迁移到 TF-DNA 课题**：对 TF-DNA 结合机制研究，界面精度比整体结构精度更重要。评估 AI 预测方法时应同时报告整体和界面级指标，并特别关注 DNA 结合残基的预测准确性。这一发现也提示：即使整体结构预测成功，界面细节（如碱基特异性接触）仍可能是 AI 方法的薄弱环节。

6. **可迁移资源：Dockground 作为 benchmark 平台**
   - 该数据集可直接用于 TF-DNA 结合预测方法的评测。
   - **迁移到 TF-DNA 课题**：可基于 Dockground 蛋白-DNA 子集，进一步按 TF 家族（如 C2H2 锌指、bZIP、homeodomain）或 DNA 结合模式（major groove vs minor groove）分类，构建 TF 特异性的 benchmark 子集。

---

## 15 与已有知识连接

1. **与 AlphaFold3 的连接**：本文直接以 AlphaFold3 [11] 为基准测试对象，其发现（界面精度可能低于整体精度）与 AlphaFold3 原始论文中关于蛋白-核酸复合物预测的讨论相关。AlphaFold3 论文报告了蛋白-DNA 复合物预测的 DockQ 分数，本文提供了更大规模、更新数据的独立验证。

2. **与蛋白-DNA docking 方法的连接**：本文引用的 pyDockDNA [8]、NPDock [9]、HDOCK [10] 是经典的蛋白-DNA docking 工具。Dockground 数据集可作为这些方法的新 benchmark，其规模远超早期数据集（如 [13-15]）。

3. **与蛋白-蛋白 docking benchmark 的连接**：Dockground 项目此前已建立蛋白-蛋白复合物数据集 [16-19]，本文是同一框架的扩展。蛋白-DNA 数据集的设计（冗余/非冗余、Web 界面、自动更新）与蛋白-蛋白版本保持一致，便于跨互作类型的方法比较。

4. **与结构预测领域的连接**：本文的时间过滤策略（2021 年 9 月 30 日后）与 CASP 和 CAMEO 等社区评测的时间分离原则一致，是避免数据泄漏的标准做法。

5. **与 TF-DNA 结合机制研究的连接**：本文数据集包含大量 TF-DNA 复合物结构，可作为研究 TF 结合特异性（base readout vs shape readout）的结构数据源。结合 Pfam/InterPro 结构域注释 [22]，可分析不同 TF 家族的 DNA 结合模式。

6. **与机器学习特征工程的连接**：本文提供的界面特征（埋藏面积、界面残基）可扩展为 ML 特征。VoroContacts [21] 的 Voronoi 镶嵌方法在蛋白-蛋白界面分析中已有广泛应用，迁移到蛋白-DNA 界面是自然延伸。

---

## 16 研究想法

**Agent 生成的研究候选**

### 候选 1：TF 家族特异的 DNA 结合界面几何特征分析
- **名称**：TF-Family-Specific Interface Geometry Atlas
- **来源局限/观察**：Dockground 数据集覆盖所有蛋白-DNA 复合物，但未按 TF 家族分类；不同 TF 家族（C2H2 锌指、bZIP、homeodomain 等）的 DNA 结合模式差异显著
- **核心假设**：不同 TF 家族的 DNA 结合界面在几何特征（埋藏面积、原子接触类型、界面残基组成）上存在可量化的差异，这些差异可用于家族分类和结合特异性预测
- **初步方法**：从 Dockground 提取 TF-DNA 复合物，按 Pfam 结构域分类；使用 VoroContacts 计算界面几何特征；用统计检验和 ML 分类器（如 Random Forest）验证家族间差异
- **验证方式**：交叉验证分类准确率；与已知 TF 结合特异性数据库（如 TRANSFAC、JASPAR）交叉验证
- **可能的失败模式**：同一 TF 家族内结合模式差异过大，或数据集覆盖不足导致统计功效不够
- **创新状态**：unverified

### 候选 2：基于 Dockground 的 TF-DNA 界面精度分层评测框架
- **名称**：Layer-wise Interface Accuracy Benchmark for TF-DNA Prediction
- **来源局限/观察**：本文仅用 Dockground 评测 AlphaFold3 整体性能，未区分不同界面类型（如 base readout vs shape readout、major vs minor groove）的预测难度
- **核心假设**：AI 方法在不同类型 TF-DNA 界面上的预测精度存在系统性差异，识别这些差异可指导方法改进
- **初步方法**：将 Dockground 蛋白-DNA 复合物按界面类型分层（直接碱基接触 vs 骨架接触、弯曲 DNA vs 直线 DNA）；分别计算各层的 i-RMSD、DockQ 和碱基接触 F1 分数；分析预测失败模式
- **验证方式**：与 AlphaFold3 和 RoseTTAFoldNA 的预测结果对比；统计各层间性能差异的显著性
- **可能的失败模式**：界面类型分类标准难以客观化，或各层样本量不足
- **创新状态**：unverified

### 候选 3：DNA 序列冗余去除的优化策略
- **名称**：Sequence-Structure Hybrid Redundancy Reduction for DNA
- **来源局限/观察**：本文 DNA 冗余去除仅用 70% 序列同一性，作者承认缺乏结构相似性标准；DNA 序列同一性与结构相似性的关系可能不同于蛋白
- **核心假设**：结合序列同一性和结构相似性（如 RMSD、DNA 构象参数）的混合冗余去除策略，能比单一序列阈值产生更优的非冗余数据集
- **初步方法**：对 Dockground 中 DNA 链计算序列同一性（MMseqs2）和结构相似性（如 Curves+ 构象参数、RMSD）；比较不同冗余去除策略对下游 benchmark 结果的影响
- **验证方式**：在不同冗余去除策略下重新运行 AlphaFold3 benchmark，比较性能评估的稳定性
- **可能的失败模式**：DNA 结构相似性计算计算量大，或不同策略对 benchmark 结果影响不显著
- **创新状态**：unverified

### 候选 4：TF-DNA 结合界面残基的 ML 预测模型
- **名称**：TF-DNA Interface Residue Predictor (TFIRP)
- **来源局限/观察**：Dockground 提供了大量带界面注释的蛋白-DNA 复合物，可用于训练界面残基预测模型；现有方法多针对蛋白-蛋白界面
- **核心假设**：利用 Dockground 的界面注释数据，训练一个能准确预测 TF 蛋白中 DNA 结合残基的 ML 模型，且该模型能泛化到未见过的 TF
- **初步方法**：从 Dockground 提取界面残基标签；使用蛋白语言模型（如 ESM-2）编码残基上下文；训练序列-结构混合模型（如 CNN + attention）预测界面残基
- **验证方式**：在 Dockground 非冗余测试集上评估 AUC/PRC；与现有 DNA 结合残基预测工具（如 DRNApred、BindUP）对比
- **可能的失败模式**：界面残基定义依赖 Dockground 的检测标准，可能与其他标注不一致；跨 TF 家族泛化困难
- **创新状态**：unverified

### 候选 5：TF-DNA 复合物结构预测的物理-机器学习混合方法
- **名称**：Hybrid Physics-ML Scoring for TF-DNA Docking
- **来源局限/观察**：本文展示了 AI 方法（AlphaFold3）在蛋白-DNA 界面预测上的不足（i-RMSD 错误率高于 L-RMSD）；经典 docking 方法（pyDockDNA 等）依赖物理评分函数
- **核心假设**：将物理评分函数（静电、范德华、溶剂化）与 ML 界面特征（来自 Dockground 训练的模型）结合，能比纯物理或纯 ML 方法更准确地区分正确和错误的 TF-DNA 对接构象
- **初步方法**：从 Dockground 生成 docking decoys；提取物理能量项和 ML 界面特征；训练排序模型（如 gradient boosting）对 decoys 重新排序
- **验证方式**：在 Dockground 测试集上评估 docking 成功率（top 10 命中率）；与 pyDockDNA、HDOCK 和 AlphaFold3 对比
- **可能的失败模式**：docking decoy 生成质量影响训练；物理和 ML 特征冗余导致过拟合
- **创新状态**：unverified