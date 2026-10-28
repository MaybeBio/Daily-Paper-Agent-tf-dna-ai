## 01 基本信息

- **标题**：Solubility-aware protein binding peptide design using AlphaFold
- **作者与单位**：Takatsugu Kosugi; Masahito Ohue（东京工业大学，Tokyo Institute of Technology）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2022
- **论文类型**：方法学（方法开发 + 计算验证）
- **领域**：蛋白质-肽相互作用（PPI）设计；AI 驱动的蛋白质设计
- **关键词**：AlphaFold；AfDesign；binder hallucination；肽设计；溶解度；PPI
- **DOI/arXiv 号**：10.1101/2022.05.14.491955
- **代码**：https://github.com/ohuelab/Solubility_AfDesign
- **数据**：未提供（除代码仓库中的实验数据外）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「AI 驱动的蛋白质-肽结合设计」方向，核心是利用 AlphaFold 作为结构预测 oracle，通过可微损失函数（binder hallucination）从头设计结合靶蛋白的肽序列，并首次引入溶解度约束。与「TF–DNA 互作 × AI」课题的直接关联有限（对象是蛋白-肽而非蛋白-DNA），但其「在生成过程中同时优化结合亲和力与理化性质」的框架、以及「用结构预测器作为可微 oracle 进行序列优化」的范式，对 TF–DNA 结合肽/蛋白设计具有直接可迁移性。

---

## 02 一句话总结

本文在 AfDesign binder hallucination 框架中引入溶解度损失函数（基于三种氨基酸溶解度指数），以 MDM2 为靶蛋白设计 13-mer 结合肽，在保持或提升对接预测结合亲和力的同时提高肽的水溶性（logS）。

---

## 03 研究问题

- **具体问题**：AfDesign binder hallucination 设计的 PPI 靶向肽序列倾向于富集疏水/芳香残基，导致水溶性（logS）偏低，不利于药物开发。能否在序列生成过程中同时优化结合亲和力与溶解度？
- **为什么重要**：PPI 界面大而平坦（1,000–4,000 Å²），小分子难以靶向；肽是可行的替代 modality，但低溶解度会损害生物利用度、膜渗透性和重组生产可行性。若能在设计阶段同时控制溶解度，可减少后期实验筛选成本。
- **现有方法不足**：
  - 先设计后过滤（design-then-filter）策略中，AfDesign 本身偏向疏水界面，过滤后候选序列所剩无几；
  - 先建库后对接策略中，20ᴺ 序列空间太大，对接计算不可行；
  - 两者均未实现「设计」与「溶解度优化」的同步进行。
- **精确研究问题（Can...?）**：Can a solubility-aware loss function be added to the AfDesign binder hallucination protocol to design PPI-targeting peptide sequences with controlled solubility while maintaining or improving predicted binding affinity?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与参考文献，属于「经外部核验」的领域发展框架，但具体分期与代表性方法选择为本文作者视角。

1. **PPI 作为药物靶点（2000s 起）**：PPI 参与多种疾病通路，小分子抑制剂如 Venetoclax（BH3 mimetic）已获批，但 PPI 界面大而平坦，小分子成功率低。
2. **肽作为 PPI 靶向 modality（2010s–）**：肽兼具亲和力与可设计性，但膜渗透性差、溶解度低是瓶颈。
3. **计算肽设计早期方法**：基于序列模式（如 PDGA 遗传算法）或基于已知小分子 footprint，但需要大量实验数据或已知配体，且不考虑真实 3D 结构。
4. **深度结构预测革命（2020–2021）**：AlphaFold2 / RoseTTAFold 实现高精度结构预测，使「从序列预测结构」成为可靠 oracle。
5. **Deep network hallucination / binder hallucination（2021–2022）**：利用 AlphaFold 的可微性，通过反向传播优化序列，使预测结构满足目标约束（如结合靶蛋白）。AfDesign 是该范式的代表性实现。
6. **本文位置**：在 binder hallucination 基础上首次引入溶解度损失，实现「结合亲和力 + 理化性质」的多目标同步优化。属于该脉络中「从纯结构约束走向多目标约束」的早期尝试。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| AfDesign 设计序列溶解度低 | 默认 binder hallucination 设计的序列 logS 显著低于 p53 天然肽 | PPI 结合界面本身疏水，AfDesign 优化结合时倾向于富集疏水/芳香残基（Leu、Tyr、Phe、Trp） | Results 图 2(a)：默认设计序列 logS 分布远低于 p53 肽；图 2(b)：序列 logo 显示 4–11 位富集疏水/芳香残基 |
| 先设计后过滤策略失效 | 过滤后候选序列数量不足 | 溶解度约束与 AfDesign 的默认优化目标冲突，二者未同步优化 | Introduction 节：作者指出「after design, few candidate sequences will remain when filtered using solubility indices」 |
| 先建库后对接策略不可行 | 20ᴺ 序列空间太大，对接计算量不可承受 | 序列空间指数爆炸，对接评分函数计算昂贵 | Introduction 节：作者明确计算「20ᴺ patterns... computationally expensive and impractical」 |
| 溶解度优化缺乏统一框架 | 传统溶解度优化依赖实验迭代或经验替换 | 缺乏可微的溶解度度量，难以嵌入深度学习生成流程 | 全文方法：作者将三种氨基酸溶解度指数归一化后直接作为可微损失项 |

---

## 06 核心思想

### 1) 表面方法
在 AfDesign binder hallucination 的损失函数中，额外加入一项「溶解度损失」——即设计序列中每个氨基酸残基的溶解度指数（归一化后）的几何平均。通过调整该损失的权重（0.1–1.0），在反向传播优化序列时同时惩罚低溶解度残基。

### 2) 核心洞察
- **可微损失 = 可控属性**：AlphaFold 作为可微 oracle 不仅输出结构置信度，其梯度可以携带任何「可表示为序列函数」的约束。溶解度指数是纯序列函数，因此可以无缝嵌入。
- **不同溶解度指数编码不同偏好**：三种指数（Hydrophobicity Index、Hydropathy Index、SWI）对氨基酸的排序不同，导致设计序列的氨基酸组成变化方向不同——这提供了一种「按需选择指数」的灵活性。
- **溶解度与亲和力并非必然对立**：通过 Hydropathy Index 或 SWI 约束，可以在不损失（甚至提升）对接预测亲和力的前提下提高 logS，说明存在「既亲水又高亲和」的序列区域。

### 3) 可能的普适教训 [Analysis]
- **多目标设计不必后验过滤**：将属性约束嵌入生成过程的损失函数，比「生成→筛选」更高效，尤其当属性与主要目标（结合）存在部分冲突时。
- **oracle 的可微性是关键资产**：任何可微的结构预测器（AlphaFold、RoseTTAFold）都可以作为「可微环境」，将任意序列级约束（溶解度、电荷、毒性等）转化为梯度信号。
- **指数选择影响结果分布**：不同理化指数对同一属性的编码不同，选择哪个指数本身就是一种设计决策，应基于下游应用（如膜渗透 vs. 重组表达）来选择。

---

## 07 方法总览

- **输入**：靶蛋白结构（PDB 1YCR chain A，MDM2）；待设计肽长度（13 aa，对应 p53 肽段长度）；溶解度指数表（三种）；损失权重 λ ∈ {0.1, 0.3, 0.5, 0.7, 1.0}；随机种子 1–100。
- **输出**：优化后的肽序列（每条 13 aa），及其预测结合亲和力（AutoDock CrankPep）和 logS（QikProp）。
- **核心模块**：
  1. **AfDesign binder hallucination**：以 AlphaFold 为 oracle，损失函数由 pLDDT、PAE_inter、distogram 等置信度指标组成，通过反向传播优化「binder 序列」的 logits。
  2. **溶解度损失模块**：将设计序列每个位置的氨基酸映射到归一化溶解度指数值，取几何平均作为额外损失项。
  3. **评估模块**：AutoDock CrankPep（对接结合亲和力）、QikProp（logS）、DockQ（对接质量）、WebLogo（序列 logo）。
- **训练/优化流程**：
  1. 输入靶蛋白结构 + 随机初始化的 binder 序列 logits；
  2. 前向：AlphaFold 预测复合物结构，计算原始损失（pLDDT/PAE/distogram）+ 溶解度损失；
  3. 反向传播：更新 binder 序列 logits；
  4. 迭代（soft → temp → hard 三阶段，各 100 轮）；
  5. 输出最优序列，用 AutoDock CrankPep 和 QikProp 评估。
- **工具**：ColabDesign（AfDesign 实现）、AlphaFold 参数（2021-07-14 版本）、jax 0.3.1 / jaxlib 0.3.1、Schrödinger 套件（LigPrep/QikProp）、AutoDockFR 1.0、WebLogo 3。
- **反馈回路**：无显式实验反馈；所有评估均为计算预测（对接 + logS 预测）。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| AfDesign binder hallucination 主损失 | 优化 binder 序列使其与靶蛋白形成高置信度复合物 | 核心结合亲和力优化引擎 | 输入：靶蛋白结构 + binder logits；输出：pLDDT/PAE/distogram 损失 | Results 图 2(a)：默认设计序列对接亲和力高于随机序列 | 移除后无法设计结合肽（核心模块） |
| 溶解度损失（几何平均） | 惩罚低溶解度残基，提高序列整体亲水性 | 解决默认设计序列 logS 偏低问题 | 输入：设计序列；输出：标量损失 | Results 图 3：随权重增加 logS 上升 | 移除后回到默认低溶解度设计（实测：图 3 权重 0 与 >0 对比） |
| 三种溶解度指数（Hydrophobicity / Hydropathy / SWI） | 提供不同的氨基酸溶解度偏好编码 | 不同指数对残基排序不同，影响设计序列组成 | 输入：氨基酸类型；输出：归一化指数值 | Results 图 4：不同指数导致不同残基频率变化模式 | 替换指数会改变设计序列的氨基酸偏好方向（实测：图 4 三种指数序列 logo 不同） |
| AutoDock CrankPep 评估 | 独立于 AlphaFold 的对接结合亲和力验证 | 避免 AlphaFold 自评偏差，提供外部验证 | 输入：靶蛋白 + 设计肽；输出：结合自由能 | Results 图 5、图 6：与 p53 及随机序列对比 | 移除后无法验证「亲和力是否保持」（核心验证模块） |
| QikProp logS 评估 | 独立计算水溶性 | 验证溶解度损失是否真正提高 logS | 输入：肽序列 → SMILES；输出：logS | Results 图 3、图 6：logS 随权重增加 | 移除后无法量化溶解度改善（核心验证模块） |

---

## 09 关键公式符号

**溶解度损失**（文中公式，未编号）：

\[
L_{sol} = \left( \prod_{i=1}^{N} f(s_i) \right)^{1/N}
\]

- \( s_i \)：设计序列第 i 个位置的氨基酸残基
- \( N \)：设计序列长度（binder_len，本文为 13）
- \( f(s) \)：氨基酸 s 的归一化溶解度指数值（三种指数分别归一化到 [0,1]）
- \( L_{sol} \)：溶解度损失，取几何平均

**总损失**（文中描述，未给出显式公式）：

\[
L_{total} = L_{AfDesign} + \lambda \cdot L_{sol}
\]

- \( L_{AfDesign} \)：原始 AfDesign binder hallucination 损失（pLDDT + PAE_inter + distogram 相关项）
- \( \lambda \)：溶解度损失权重，本文取 {0.1, 0.3, 0.5, 0.7, 1.0}

**其他符号**：
- logS：水溶性对数值（QikProp 计算）
- pLDDT：预测局部距离差异测试（per-residue 置信度）
- PAE_inter：链间预测对齐误差（复合物界面置信度）
- DockQ：对接质量评分（0–1，本文报告 0.500）

---

## 10 实验设计与证据链

### 数据集/群体/规模
- **靶蛋白**：MDM2（PDB 1YCR chain A），p53 肽（chain B，13 aa "ETFSDLWKLLPEN"）为天然结合肽
- **设计规模**：每个条件（指数 × 权重）100 次独立设计（种子 1–100）
- **权重条件**：λ ∈ {0.1, 0.3, 0.5, 0.7, 1.0}，加上无溶解度损失的基线（λ=0）
- **指数条件**：Hydrophobicity Index、Hydropathy Index、SWI 三种
- **对照**：p53 天然肽序列、随机序列、p53 单残基替换序列

### 指标
- **溶解度**：logS（QikProp 预测）
- **结合亲和力**：AutoDock CrankPep 结合自由能（对接评分）
- **结构质量**：DockQ（仅对最优序列）

### 评测协议
- 对每个设计条件，取 100 次设计的最优序列（最低总损失），计算其 logS 和对接亲和力
- 与 p53 天然肽、随机序列、p53 单残基替换序列进行对比

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-------------|-------------------|------|
| 默认 AfDesign 设计序列的溶解度分布 | 默认 binder hallucination 产生低溶解度序列 | 100 次设计 vs p53 肽 logS | 设计序列 logS 分布远低于 p53 肽 | 默认设计序列溶解度偏低 | 未提供 p53 肽 logS 具体数值 | Results 图 2(a) |
| 默认设计序列的氨基酸组成 | 设计序列富集疏水/芳香残基 | 序列 logo 分析 | 4–11 位富集 Leu、Tyr、Phe、Trp | 疏水/芳香残基富集是低溶解度原因 | 未做定量组成统计 | Results 图 2(b) |
| 溶解度损失权重对 logS 的影响 | 增加溶解度损失权重可提高 logS | 三种指数 × 5 个权重 vs λ=0 | logS 随权重增加而上升；Hydrophobicity Index 变化最显著 | 溶解度损失可有效控制 logS | 未报告 logS 具体数值 | Results 图 3 |
| 溶解度损失对结合亲和力的影响 | 溶解度优化不牺牲结合亲和力 | 各条件设计序列 vs p53 肽、随机序列、单残基替换 | Hydropathy Index 和 SWI 设计序列亲和力 ≥ p53 肽；Hydrophobicity Index 设计序列亲和力下降 | 部分指数可同时优化溶解度与亲和力 | 未报告结合自由能具体数值 | Results 图 5、图 6 |
| 最优序列的结构验证 | 设计序列能形成正确复合物结构 | DockQ 评估 | DockQ = 0.500（中等质量） | 设计序列与 MDM2 的结合模式接近天然 p53 肽 | 仅评估 1 条序列；DockQ 中等而非高质量 | Results 图 S2 |
| 与随机/单残基替换序列对比 | 设计序列优于朴素基线 | 随机序列、p53 单残基替换序列 | 设计序列亲和力高于随机序列和单残基替换序列 | AfDesign 设计优于朴素基线 | 未报告具体数值 | Discussion 节、图 S1 |

---

## 11 结论正确解读

- **任务范围**：本文仅针对 MDM2 一个靶蛋白、13-mer 肽长度；未测试其他靶点、其他肽长度、其他 PPI 界面类型（如 β-sheet 界面仅做了初步测试，见 PD-1 实验）。
- **oracle/真值输入**：结合亲和力由 AutoDock CrankPep 对接评分预测，非实验测定；溶解度由 QikProp 预测 logS，非实验测量。两者均为计算预测，存在系统性误差。
- **端到端状态**：非端到端。设计流程为「AfDesign 生成 → 对接评估 → logS 评估」，无 wet-lab 验证。
- **算力成本**：未报告具体算力需求；100 次设计 × 5 权重 × 3 指数 = 1500 次 AfDesign 运行，加上对接评估，计算量较大但未量化。
- **历史数据依赖**：AlphaFold 参数基于 PDB 训练，对 MDM2-p53 这类已知复合物可能有偏；对全新 PPI 靶点的泛化能力未验证。
- **模型依赖**：结果依赖 AlphaFold 的置信度指标（pLDDT/PAE）与真实结合自由能的相关性；若该相关性在目标体系上较弱，设计质量会下降。
- **最难情形**：β-sheet 界面（PD-1 实验）中，默认 AfDesign 设计的序列亲和力与随机序列相当，说明该方法对非螺旋界面的适用性有限。
- **群体/领域边界**：结论仅适用于「以 α-helix 为结合界面的 PPI 靶向肽设计」；对 TF–DNA 互作（蛋白-核酸界面）无直接证据。
- **有边界的复述**：在 MDM2-p53 这一 α-helix 介导的 PPI 体系中，将溶解度指数作为可微损失加入 AfDesign binder hallucination，可以在计算预测层面同时提高肽的 logS 并保持或提升对接结合亲和力；该结论未经实验验证，且对其他 PPI 类型（如 β-sheet 界面）的适用性存疑。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 结果基于计算预测，未经实验验证 | 结合亲和力由 AutoDock CrankPep 预测，溶解度由 QikProp 预测 | 作者在 Discussion 中承认「these results are based on computer simulations; true solubility and binding affinity will not be known until experiments are conducted」 | Discussion 节 |
| 对 β-sheet 界面 PPI 的适用性有限 | PD-1 实验中，默认 AfDesign 设计序列的亲和力与随机序列相当 | 作者提出「further optimization of our approach could be applied to drug discovery」但未给出具体方案 | Discussion 节、图 S4 |
| 设计序列可能具有对抗性 | 作者指出「The sequences designed by AfDesign could be adversarial, such as those simply preferred by AlphaFold」 | 通过使用独立于 AlphaFold 的对接工具（AutoDock CrankPep）进行外部验证来缓解 | Discussion 节 |
| 仅测试单一靶点 | 主要实验仅针对 MDM2 | 未明确提及，但 PD-1 实验可视为初步扩展 | 全文 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 溶解度损失使用几何平均，对单残基极端低溶解度不敏感 | 几何平均对异常值不敏感，可能允许个别极疏水残基存在 | 若设计序列中单个残基主导溶解度问题，几何平均可能无法有效惩罚 | 对比几何平均与算术平均/最小值的惩罚效果 | Methods 节公式 |
| 结合亲和力评估仅用 AutoDock CrankPep 单一工具 | 不同对接工具的评分函数差异大，单一工具可能产生系统性偏差 | 结论的稳健性依赖单一评分函数 | 使用多种对接工具（如 HADDOCK、ClusPro）或 MD 模拟验证 | Methods 节 2.4 |
| 未报告 logS 和结合亲和力的具体数值 | 图 3、图 5、图 6 仅展示趋势，无定量数据 | 无法评估效应量大小，难以判断实际应用价值 | 补充数值表格和统计检验 | Results 图 3、5、6 |
| PD-1 实验仅作为初步测试，未系统评估 | 作者承认 β-sheet 界面设计效果差，但未深入分析原因 | 对方法适用范围的理解不完整 | 系统测试多种界面类型（α-helix、β-sheet、loop） | Discussion 节、图 S4 |
| 未讨论溶解度损失对序列多样性的影响 | 强溶解度约束可能降低序列多样性，导致设计空间收缩 | 可能影响后续优化空间 | 分析不同权重下设计序列的多样性指标 | 未提供 |
| 未与现有溶解度预测/优化方法对比 | 未与先设计后过滤策略做定量对比 | 无法判断「同步优化」是否优于「先生成后筛选」 | 实现 baseline 方法并对比相同指标 | 未提供 |
| 溶解度指数选择缺乏理论依据 | 三种指数结果不同，但作者未解释为何选择这三种或如何选择 | 方法对指数选择敏感，缺乏指导原则 | 系统比较更多溶解度指数（如 Kyte-Doolittle、Eisenberg） | Methods 节 2.2 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **可微 oracle + 可微属性损失 = 多目标序列设计框架**：本文最核心的可迁移思想是「任何可表示为序列函数的属性（溶解度、电荷、疏水性等）都可以作为额外损失项，嵌入以 AlphaFold 为 oracle 的生成流程」。对 TF–DNA 互作课题，可将 DNA 结合特异性（如 position weight matrix 分数）、氨基酸组成约束等作为可微损失，与 AlphaFold 结构置信度联合优化。

2. **几何平均作为序列级属性聚合**：对整条序列的属性（如溶解度）取几何平均，是一种简单且可微的聚合方式。对 TF–DNA 结合肽设计，可类似地聚合 DNA 结合残基的理化属性。

3. **外部验证工具的选择**：作者使用与优化 oracle（AlphaFold）无关的对接工具（AutoDock CrankPep）进行验证，以缓解「对抗性序列」风险。对 TF–DNA 课题，应使用独立于 AlphaFold 的 DNA 结合预测工具（如 DeepBind、DeepSEA）或实验数据验证设计序列。

4. **多指数对比作为稳健性检验**：使用三种溶解度指数交叉验证，若不同指数均显示溶解度提升，则结论更稳健。对 TF–DNA 课题，可类似地使用多种 DNA 结合特异性预测器交叉验证。

5. **「先设计后过滤」vs「同步优化」的权衡**：本文明确论证了同步优化优于先设计后过滤（因过滤后候选太少）。对 TF–DNA 结合肽设计，若结合界面本身疏水性强，同步优化策略可能同样必要。

6. **α-helix 介导的 PPI 是 AI 设计的最适场景**：MDM2-p53 是 α-helix 介导的经典 PPI，AfDesign 在此类界面上表现良好，但在 β-sheet 界面上失效。对 TF–DNA 课题，应评估目标 TF 的 DNA 结合域（通常含 α-helix，如 helix-turn-helix、zinc finger）是否适合此类方法。

7. **计算预测的边界**：本文所有结论基于计算预测，作者明确承认需要实验验证。对 TF–DNA 课题，应同样区分「计算设计」与「实验验证」的边界，避免过度解读 in silico 结果。

---

## 15 与已有知识连接

- **AlphaFold 作为设计工具**：本文与 AlphaFold 的「反向使用」（从结构到序列）相关，与以下工作形成脉络：(1) 蛋白质设计中的 hallucination 方法（Anishchenko et al., 2021, Nature；trRosetta hallucination）；(2) AlphaFold 用于肽-蛋白复合物预测（Johansson-Åkhe & Wallner, 2022）；(3) AlphaFold 用于蛋白-核酸复合物预测（近期工作显示 AlphaFold 对蛋白-DNA 复合物预测能力有限，但正在改进）。
- **溶解度预测与设计**：本文使用三种氨基酸溶解度指数（Hydrophobicity Index、Hydropathy Index、SWI），与蛋白质溶解度预测工具（如 CamSol、PROSO）相关，但本文是首次将溶解度作为可微损失嵌入生成流程。
- **PPI 靶向肽设计**：与以下方法形成对比：(1) 基于 Rosetta 的肽对接设计（如 FlexPepDock）；(2) 基于深度学习的肽设计（如 PepDesign、PepGAN）；(3) 基于 AlphaFold 的 binder hallucination（本文基础）。本文的独特贡献是「多目标」优化。
- **对 TF–DNA 课题的映射**：
  - **相似性**：TF–DNA 互作与 PPI 类似，都是大而平坦的界面，小分子难以靶向；肽/蛋白设计策略可迁移。
  - **差异性**：DNA 结合特异性由碱基接触决定，需要序列级别的特异性约束（如 PWM），而不仅是结构置信度；本文的溶解度损失框架可扩展为「溶解度 + DNA 特异性」双损失。
  - **可迁移工具**：AfDesign 的 binder hallucination 可直接用于设计结合 TF 的肽（以 TF 为靶蛋白）；溶解度损失可直接复用；DNA 结合特异性需额外引入。
- **候选方向（未验证）**：将本文框架应用于「设计结合转录因子 DNA 结合域的肽」，以阻断 TF–DNA 互作（即 peptide-based TF inhibitor），是自然的下一步。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：TF–DNA 互作阻断肽的溶解度感知设计
- **名称**：Solubility-aware design of TF-binding peptides targeting DNA-binding domains
- **来源局限/观察**：本文仅针对 MDM2-p53 这一 α-helix 介导的 PPI；TF 的 DNA 结合域（如 bZIP、homeodomain）通常以 α-helix 插入 DNA 大沟，结构特征相似，但 DNA 结合特异性未被考虑。
- **核心假设**：将本文的溶解度损失与「DNA 结合竞争」约束（如设计肽与 TF 的 DNA 结合界面重叠）联合优化，可设计出高溶解度、高亲和力的 TF 阻断肽。
- **增量**：在 AfDesign 损失中加入「界面重叠」约束（如设计肽与 TF 的 DNA 结合残基的空间接触最大化），并评估对 DNA 结合的竞争性抑制。
- **初步方法**：以已知 TF–DNA 复合物（如 p53、MYC、TP53）为靶，用 AfDesign + 溶解度损失 + 界面重叠损失设计 10–20 mer 肽；用 AutoDock CrankPep 评估亲和力，用 QikProp 评估 logS，用 MD 模拟验证结合稳定性。
- **验证方式**：计算层面与随机/单残基替换序列对比；若可能，进行体外 pull-down 或荧光偏振实验验证。
- **创新状态**：unverified（本文框架 + 新约束，未见已发表工作直接实现）

### 候选 2：DNA 结合特异性作为可微损失的嵌入
- **名称**：Differentiable DNA-binding specificity loss for TF-binding peptide design
- **来源局限/观察**：本文的溶解度损失是「序列函数」，但未涉及 DNA 序列特异性；TF 结合肽若想模拟 TF 的 DNA 结合偏好，需要序列级别的特异性约束。
- **核心假设**：将 TF 的 DNA 结合偏好（如 PWM 分数）编码为可微损失，可设计出「模拟 TF 的 DNA 结合界面」的肽，从而竞争性抑制 TF–DNA 互作。
- **增量**：将 PWM 分数作为可微函数嵌入 AfDesign 损失，与溶解度损失联合优化。
- **初步方法**：对目标 TF，提取其 DNA 结合域的 PWM；将设计肽的氨基酸序列映射到「DNA 接触偏好」分数（需建立氨基酸-碱基接触的统计模型）；联合优化结构置信度 + PWM 模拟分数 + 溶解度。
- **验证方式**：计算层面评估设计肽与目标 DNA 序列的对接；与已知 TF 的 DNA 结合域序列对比。
- **创新状态**：unverified（需建立氨基酸-碱基接触的可微映射，未见直接先例）

### 候选 3：多靶点泛化性评估
- **名称**：Generalization of solubility-aware binder hallucination across PPI and TF–DNA interfaces
- **来源局限/观察**：本文仅测试 MDM2（α-helix 界面）和 PD-1（β-sheet 界面，效果差）；未系统评估方法在不同界面类型上的表现。
- **核心假设**：溶解度感知的 binder hallucination 在 α-helix 介导的界面上有效，但在 β-sheet、loop 介导的界面上可能失效；系统评估可揭示方法的适用边界。
- **增量**：构建包含多种界面类型（α-helix、β-sheet、loop、TF–DNA）的测试集，系统评估溶解度损失的影响。
- **初步方法**：选取 10–20 个已知 PPI 和 TF–DNA 复合物，运行 AfDesign ± 溶解度损失，比较 logS 和对接亲和力的变化模式。
- **验证方式**：统计不同界面类型下溶解度-亲和力权衡的差异。
- **创新状态**：unverified（本文仅提供两个案例，无系统评估）

### 候选 4：溶解度损失与实验验证的闭环
- **名称**：Experimental validation of solubility-aware designed PPI-targeting peptides
- **来源局限/观察**：本文所有结论基于计算预测，作者明确承认需要实验验证。
- **核心假设**：溶解度感知设计的肽在实验中确实表现出更高的溶解度和可检测的结合亲和力。
- **增量**：将计算设计推进到实验验证，形成「设计→合成→表征→反馈」闭环。
- **初步方法**：选取 5–10 条设计肽（不同指数 × 权重），固相合成，测量溶解度（DLS 或 UV-Vis）、结合亲和力（ITC 或 SPR）、复合物结构（X-ray 或 Cryo-EM）。
- **验证方式**：实验数据与计算预测对比，评估溶解度损失的实际效果。
- **创新状态**：unverified（需实验资源，但逻辑直接）