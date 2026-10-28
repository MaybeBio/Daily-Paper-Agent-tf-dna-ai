## 01 基本信息

- **标题**：Structural interplay between DNA-shape protein recognition and supercoiling: the case of IHF
- **作者**：George D. Watson; Elliot W. Chan; Mark C. Leake; Agnes Noy
- **单位**：未提供（根据 bioRxiv 平台及作者信息推断为英国机构，具体单位未在摘要中提供）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2022
- **论文类型**：预印本（研究论文）
- **领域**：计算生物物理学；蛋白质-DNA 互作；DNA 超螺旋；分子动力学模拟
- **关键词**：IHF（integration host factor）；indirect readout；DNA supercoiling；molecular dynamics；DNA minicircles；plectonemes
- **DOI/arXiv 号**：10.1101/2022.03.31.486518
- **代码**：未提供
- **数据**：未提供（模拟轨迹数据未明确说明是否公开）
- **阅读日期**：2026-05-09（按当前日期）
- **在该方向中的位置**：本文聚焦于 DNA 结合蛋白 IHF 与 DNA 超螺旋之间的双向互作，属于「蛋白质-DNA 互作（TF–DNA 结合机制）× 物理模拟（原子级 MD）」方向。其核心贡献在于揭示 DNA 形状识别（indirect readout）与拓扑约束（supercoiling）之间的耦合，为理解转录因子如何在生理性超螺旋 DNA 上识别并结合提供了新的机制视角。

---

## 02 一句话总结

本文通过原子级分子动力学模拟 DNA 小环（minicircles），发现 IHF 蛋白与超螺旋 DNA 之间存在双向互作：超螺旋增强 IHF 结合与 DNA 缠绕，而 IHF 则固定 plectoneme 位置、分割拓扑结构域，并根据超螺旋符号（正/负）分别抑制过旋或欠旋 DNA，从而充当「超螺旋缓冲器」。

---

## 03 研究问题

- **具体问题**：IHF 作为间接读取（indirect readout）的典型蛋白，能在松弛线性 DNA 上施加极强的弯曲。然而，IHF 与生理条件下普遍存在的扭转约束 DNA（超螺旋 DNA）之间的互作机制尚不清楚。本文要回答：IHF 与超螺旋 DNA 之间是否存在双向（reciprocal）影响？具体表现为何？
- **为什么重要**：在活细胞中，DNA 几乎总是处于超螺旋状态（由拓扑异构酶和转录等活动产生），因此理解 IHF 在超螺旋 DNA 上的行为对于揭示其生理功能（如基因调控、DNA 压缩）至关重要。此外，该问题也推广到其他依赖 DNA 变形的蛋白-DNA 复合物。
- **现有方法为何不足**：以往对 IHF-DNA 复合物的研究多基于松弛线性 DNA 或短寡核苷酸，忽略了拓扑约束对 DNA 构象和蛋白结合的影响。实验方法难以在原子尺度同时控制超螺旋密度并观测蛋白-DNA 动态互作。
- **精确研究问题（Can ... ?）**：Can atomistic molecular dynamics simulations on DNA minicircles reveal the reciprocal influence between IHF binding and DNA supercoiling, and characterize the topological consequences of this interplay?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文摘要及该领域已知背景，标注为「经外部核验」的部分基于公开文献常识，其余为「仅本文框架」。

- **阶段一：IHF 作为间接读取的经典模型**（约 1990s–2010s）
  - 代表性方法：X 射线晶体学、单分子实验、早期 MD 模拟。
  - 优点：确定了 IHF 对 DNA 的强弯曲（约 160°），揭示了间接读取的分子机制（通过 DNA 形状而非直接碱基接触）。
  - 局限：多基于松弛线性 DNA，未考虑拓扑约束。
- **阶段二：DNA 超螺旋的原子级模拟**（约 2010s–2020s）
  - 代表性方法：原子级 MD 模拟 DNA minicircles（如 Noy 课题组的系列工作）。
  - 优点：能够在原子尺度控制超螺旋密度（σ），观察 plectoneme 形成、DNA 呼吸等动态行为。
  - 局限：早期工作多聚焦于裸 DNA，未引入蛋白。
- **阶段三：蛋白-DNA 复合物在超螺旋 DNA 上的模拟**（本文位置）
  - 本文首次将 IHF 蛋白引入超螺旋 DNA minicircle 模拟，揭示蛋白与超螺旋之间的双向互作。
  - 主张：IHF 不仅响应超螺旋，还主动组织 DNA 拓扑结构（固定 plectoneme、分割拓扑域、缓冲超螺旋变化）。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 缺乏对 IHF 与超螺旋 DNA 互作的原子级理解 | 以往研究仅关注松弛线性 DNA 上的 IHF 结合 | 生理条件下 DNA 几乎总是超螺旋，但实验和模拟均未系统考察 | 摘要首句：「the relation between IHF and torsionally constrained DNA, as occurs physiologically, remains unclear」 |
| 超螺旋对 IHF 结合的影响未知 | 超螺旋 DNA 的弯曲是否增强或减弱 IHF 缠绕？ | 超螺旋增加 DNA 曲率，可能促进 IHF 结合，但缺乏直接证据 | 摘要：「the increased curvature of supercoiled DNA enhances wrapping around IHF」 |
| IHF 对超螺旋拓扑的反作用未知 | IHF 是否影响 plectoneme 位置、拓扑域划分？ | 蛋白结合可能固定 DNA 弯曲位置，从而组织拓扑结构 | 摘要：「the protein pins the position of plectonemes, organizing the topology of the loop」 |
| IHF 对超螺旋符号（正/负）的响应差异未知 | IHF 是否区分正/负超螺旋？ | 不同超螺旋符号导致 DNA 过旋或欠旋，IHF 可能以不同方式响应 | 摘要：「IHF restrains under- or overtwisted DNA depending on whether the complex is formed in negatively or positively supercoiled DNA」 |
| IHF 是否具有「超螺旋缓冲」功能未知 | IHF 能否 dampen 超螺旋变化？ | 通过 DNA 呼吸或复合物解离，IHF 可能缓冲周围超螺旋应力 | 摘要：「enables IHF to become a 'supercoiling buffer'」 |
| IHF 是否介导 DNA 桥接（bridging）未知 | IHF 能否将 DNA 不同区域桥接在一起？ | 桥接可能分割 DNA 为独立拓扑域 | 摘要：「provide evidence of DNA bridging by IHF and reveal that these bridges divide DNA into independent topological domains」 |

---

## 06 核心思想

### 1) 表面方法
- 使用原子级分子动力学（MD）模拟，构建含 IHF 蛋白的 DNA minicircle 体系，分别设置负超螺旋、正超螺旋和（可能）松弛状态，观察 IHF 与 DNA 的互作动态。

### 2) 核心洞察
- **双向互作**：超螺旋 DNA 的曲率增强 IHF 结合与缠绕；反过来，IHF 通过固定 plectoneme 位置、桥接 DNA 区域，主动组织 DNA 的拓扑结构。
- **符号依赖性**：IHF 对正/负超螺旋的响应不同——在负超螺旋中抑制欠旋（undertwist），在正超螺旋中抑制过旋（overtwist），从而发挥「超螺旋缓冲器」作用。
- **拓扑域分割**：IHF 桥接 DNA 后，将 DNA 环分割为独立的拓扑域，这可能对基因调控具有重要意义。

### 3) 可能的普适教训 [Analysis]
- 蛋白-DNA 互作不能脱离 DNA 的拓扑状态来理解：DNA 的形状（曲率、扭转）是蛋白识别的重要信号，而蛋白结合反过来可以改变 DNA 的拓扑组织。
- 对于依赖 DNA 变形的蛋白（如许多转录因子、 architectural proteins），超螺旋状态可能是其功能调控的一个未被充分重视的维度。

---

## 07 方法总览

- **输入**：IHF 蛋白结构（来自晶体结构或同源建模）；DNA minicircle 序列（长度和序列未在摘要中说明）；超螺旋密度 σ（负、正、可能零）。
- **输出**：MD 轨迹；IHF-DNA 结合模式；DNA 曲率、扭转、plectoneme 位置随时间的变化；IHF 桥接事件。
- **模块**：
  1. 体系构建：将 IHF 置于 DNA minicircle 上，设置不同超螺旋密度。
  2. MD 模拟：原子级力场（具体力场未在摘要中说明，推测为 AMBER 或 CHARMM 系列）。
  3. 轨迹分析：DNA 曲率、扭转、plectoneme 位置、IHF-DNA 接触、桥接事件。
- **训练**：不适用（无机器学习成分）。
- **工具**：未提供（推测为 NAMD、GROMACS 或 AMBER 等常用 MD 软件）。
- **反馈回路**：无（非自适应模拟）。
- **文字流程**：构建 IHF-DNA minicircle 复合物 → 在不同超螺旋密度下运行原子级 MD → 分析轨迹中 DNA 的曲率、扭转、plectoneme 动态及 IHF 的结合模式 → 比较不同超螺旋条件下的差异 → 总结双向互作机制。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| DNA minicircle 构建 | 生成环形 DNA 底物，控制超螺旋密度 | 模拟生理性扭转约束 DNA | 输入：序列、σ；输出：初始构象 | 摘要：「atomistic molecular dynamics simulations on DNA minicircles」 | 无法模拟超螺旋条件，回到松弛线性 DNA 的局限 |
| IHF 蛋白建模与放置 | 将 IHF 置于 DNA 上，模拟结合状态 | 研究 IHF 与超螺旋 DNA 的互作 | 输入：IHF 结构、DNA 构象；输出：复合物初始构象 | 摘要：「the case of IHF」 | 无法研究 IHF 在超螺旋 DNA 上的行为 |
| 原子级 MD 模拟 | 生成动态轨迹，观察互作过程 | 捕捉原子尺度的构象变化和互作 | 输入：复合物构象、力场参数；输出：轨迹 | 摘要：「atomistic molecular dynamics simulations」 | 无法获得动态信息 |
| 轨迹分析（曲率、扭转、plectoneme 追踪） | 量化 DNA 构象变化和拓扑组织 | 揭示超螺旋与 IHF 的相互影响 | 输入：轨迹；输出：曲率、扭转、plectoneme 位置 | 摘要：「increased curvature... pins the position of plectonemes」 | 无法定量描述互作 |
| 桥接事件检测 | 识别 IHF 同时结合 DNA 两个位点的行为 | 揭示拓扑域分割机制 | 输入：轨迹；输出：桥接事件列表 | 摘要：「DNA bridging by IHF... divide DNA into independent topological domains」 | 无法解释拓扑域分割 |

> 注：以上「移除后的影响」均为预期效应（非实测消融），因摘要未提供消融实验。

---

## 09 关键公式符号

不适用。摘要中未提供任何公式或符号。本文为 MD 模拟研究，核心分析基于轨迹几何量（曲率、扭转）和拓扑量（超螺旋密度 σ），但具体公式未在摘要中给出。

---

## 10 实验设计与证据链

- **数据集/群体**：DNA minicircle 体系，含 IHF 蛋白；具体序列、长度、超螺旋密度值未在摘要中提供。
- **规模**：未提供（模拟时长、体系原子数等未说明）。
- **指标**：DNA 曲率、扭转、plectoneme 位置、IHF 结合模式、桥接事件。
- **基线**：未明确说明（推测为无 IHF 的裸 DNA minicircle 或松弛 DNA 上的 IHF 结合）。
- **预算**：不适用（计算模拟，但具体算力未提供）。
- **骨干/仪器**：未提供（MD 软件和力场未说明）。
- **oracle 输入**：不适用（无监督学习或 oracle 概念）。
- **评测协议**：未提供（无标准 benchmark）。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|-------------|-------------------|------|
| 超螺旋 DNA 上 IHF 结合模拟 | 超螺旋增强 IHF 缠绕 | 负/正超螺旋 vs 松弛（推测） | 超螺旋 DNA 的曲率增强 IHF 缠绕 | 超螺旋促进 IHF 结合 | 无法定量比较结合亲和力（无自由能计算） | 摘要：「the increased curvature of supercoiled DNA enhances wrapping around IHF」 |
| plectoneme 位置追踪 | IHF 固定 plectoneme 位置 | 有/无 IHF 的 minicircle（推测） | IHF 结合后 plectoneme 位置被固定 | IHF 组织 DNA 拓扑 | 无法确定固定机制（直接接触 vs 间接效应） | 摘要：「the protein pins the position of plectonemes」 |
| 正/负超螺旋对比 | IHF 对超螺旋符号有不同响应 | 负超螺旋 vs 正超螺旋 | 负超螺旋中抑制欠旋，正超螺旋中抑制过旋 | IHF 作为超螺旋缓冲器 | 无法确定缓冲的动力学范围 | 摘要：「IHF restrains under- or overtwisted DNA depending on...」 |
| 桥接事件检测 | IHF 介导 DNA 桥接 | 多轨迹观察（推测） | 观察到 IHF 桥接 DNA 不同区域 | 桥接分割拓扑域 | 无法确定桥接的生理相关性 | 摘要：「DNA bridging by IHF... divide DNA into independent topological domains」 |

---

## 11 结论正确解读

- **任务范围**：本文仅基于原子级 MD 模拟，未涉及实验验证。结论限于模拟体系（DNA minicircle + IHF）中的行为。
- **oracle/真值输入**：不适用（无监督学习）。
- **端到端状态**：非端到端；模拟体系经过简化（minicircle 而非基因组 DNA），且未包含其他蛋白或生理环境因素。
- **算力成本**：未提供。
- **历史数据依赖**：不适用（无历史数据训练）。
- **模型依赖**：结论依赖于 MD 力场的准确性；不同力场可能影响定量结果。
- **最难情形**：正超螺旋下的 IHF 行为可能更复杂，但摘要未提供细节。
- **群体/领域边界**：结论基于 IHF 一个蛋白，推广到其他 DNA 变形蛋白是「anticipated」而非已验证。
- **不确定性**：未提供误差估计或重复实验信息。
- **有边界的复述**：在原子级 MD 模拟的 DNA minicircle 体系中，IHF 与超螺旋 DNA 之间存在双向互作：超螺旋增强 IHF 缠绕，IHF 固定 plectoneme 位置、分割拓扑域，并根据超螺旋符号抑制过旋或欠旋，从而缓冲超螺旋变化。该结论尚未经实验验证，且推广到其他蛋白需谨慎。

---

## 12 作者自认局限

在提供的摘要中，作者未明确列出局限性。但摘要末句提到「We anticipate that the crosstalk detected here... could be common to other DNA-protein complexes」，表明作者意识到推广性尚未验证。

**作者提及的相关约束**（非正式局限）：
- 结论基于模拟，未提供实验验证。
- 推广到其他蛋白是「anticipated」而非已验证。
- 具体模拟参数（力场、时长、体系大小）未在摘要中说明，可能影响结论的普适性。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| 摘要未提供模拟细节（力场、时长、体系大小） | 不同力场可能显著影响 DNA 弯曲和扭转行为；短模拟可能无法捕捉 plectoneme 重排 | MD 结果对力场和采样时间高度敏感 | 查阅全文 Methods 节；或使用不同力场重复模拟 | 摘要仅提及「atomistic molecular dynamics simulations」 |
| 「超螺旋增强 IHF 缠绕」的结论缺乏定量比较 | 未提供结合自由能或接触面积等定量指标 | 无法判断增强的幅度和生理相关性 | 计算结合自由能（如 MM-PBSA）或比较接触面积 | 摘要仅定性描述「enhances wrapping」 |
| 「IHF 固定 plectoneme 位置」的机制不明确 | 可能是 IHF 直接接触 DNA 弯曲位点，也可能是 IHF 改变 DNA 刚性间接影响 plectoneme | 区分直接与间接机制对理解蛋白功能至关重要 | 设计突变体或截短体模拟，观察 plectoneme 行为变化 | 摘要未提供机制细节 |
| 「超螺旋缓冲器」概念缺乏定量边界 | 未说明缓冲的幅度、时间尺度和适用条件 | 缓冲功能是否具有生理意义取决于定量范围 | 系统扫描不同 σ 值，测量 IHF 对扭转波动的抑制程度 | 摘要仅定性描述「dampens changes」 |
| 桥接事件是否具有序列特异性未知 | IHF 已知偏好特定 DNA 序列，但摘要未说明桥接是否依赖序列 | 序列依赖性影响桥接的生理相关性 | 使用不同序列的 minicircle 进行对照模拟 | 摘要未提及序列信息 |
| 模拟体系仅含 IHF 和 DNA，缺乏其他蛋白或离子环境 | 生理环境中存在大量蛋白和离子，可能影响 IHF 结合和 DNA 拓扑 | 简化体系可能高估或低估互作强度 | 逐步增加体系复杂度（如加入离子、其他蛋白） | 摘要未提及环境因素 |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **超螺旋作为蛋白-DNA 互作的调控维度**：本文表明，DNA 超螺旋状态（σ）可以显著影响蛋白结合（IHF 缠绕增强），而蛋白结合反过来可以组织 DNA 拓扑（固定 plectoneme、分割拓扑域）。对于 TF–DNA 结合机制研究，这意味着在建模或实验设计中应考虑 DNA 的拓扑状态，而非仅用松弛线性 DNA。
   - **迁移方法**：在 MD 模拟或对接研究中，使用超螺旋 DNA 底物（如 minicircle）替代线性 DNA，考察 TF 结合是否受 σ 影响。

2. **「超螺旋缓冲」概念**：IHF 通过抑制过旋或欠旋来 dampen 超螺旋波动。这一机制可能普遍存在于 architectural proteins 和某些 TF 中。
   - **迁移方法**：对候选 TF 进行类似模拟，检测其是否具有符号依赖的扭转缓冲行为；可设计实验（如单分子扭转操纵）验证。

3. **桥接与拓扑域分割**：IHF 桥接 DNA 后形成独立拓扑域，这可能影响远距离基因调控（如 enhancer-promoter 通讯）。
   - **迁移方法**：在 Hi-C 或 3C 数据分析中，考虑 TF 桥接对拓扑域边界的影响；或在模拟中检测 TF 是否介导 DNA 环化。

4. **双向互作的研究框架**：本文提供了一个「蛋白 ↔ DNA 拓扑」双向分析框架，适用于其他 DNA 弯曲蛋白（如 HU、H-NS、某些 TF）。
   - **迁移方法**：对目标 TF 建立类似模拟体系，系统扫描 σ，分析结合模式与拓扑组织的共变。

5. **原子级 MD 在蛋白-DNA 互作中的适用性**：本文展示了原子级 MD 在捕捉蛋白-DNA 动态互作（如 plectoneme 固定、桥接）中的能力，可作为结构预测（如 AlphaFold）的补充工具。
   - **迁移方法**：将 AlphaFold 预测的 TF-DNA 复合物结构放入超螺旋 minicircle 中进行 MD 精化，考察其稳定性与拓扑响应。

---

## 15 与已有知识连接

- **IHF 的经典研究**：IHF 是间接读取的经典例子，其与 DNA 的强弯曲（约 160°）已在晶体结构（如 Rice et al., 1996, Cell）中阐明。本文将其扩展到超螺旋 DNA 情境，补充了拓扑维度的理解。
- **DNA 超螺旋的 MD 模拟**：Noy 课题组及其他人此前已用 MD 模拟 DNA minicircle 研究超螺旋结构（如 plectoneme 形成、DNA 呼吸）。本文首次引入蛋白，拓展了该方法的适用范围。
- **Architectural proteins 与拓扑**：HU、H-NS 等蛋白已知可影响 DNA 拓扑和压缩。本文的「超螺旋缓冲」和「桥接」概念与这些蛋白的功能有潜在联系，可对比研究。
- **TF 结合与 DNA 形状**：间接读取（indirect readout）是 TF 识别 DNA 的重要机制之一（如 Rohs et al., 2009, Nature）。本文强调超螺旋改变 DNA 形状（曲率、扭转），可能影响 TF 的间接读取识别。
- **拓扑域与基因调控**：真核生物中 TAD（topologically associating domains）与 CTCF/cohesin 相关；本文在原核体系（IHF）中观察到类似拓扑域分割，可能为原核基因调控提供新视角。

---

## 16 研究想法

> **Agent 生成的研究候选**

1. **候选名称**：TF 超螺旋依赖性结合的全基因组预测
   - **来源局限/观察**：本文仅研究 IHF 一个蛋白；其他 TF 是否具有类似的超螺旋响应未知。
   - **核心假设**：许多 TF 的结合亲和力受 DNA 超螺旋状态（σ）影响，且这种影响可通过 DNA 形状特征（曲率、扭转）预测。
   - **相对本文的增量**：从单蛋白扩展到多 TF，从模拟扩展到预测模型。
   - **初步方法**：对多个 TF 进行 MD 模拟（不同 σ），提取结合自由能与 DNA 形状特征；训练机器学习模型（如随机森林或图神经网络）预测 σ 依赖性；用 ChIP-seq 数据（不同拓扑状态）验证。
   - **验证方式**：交叉验证预测准确率；与实验数据（如拓扑异构酶抑制前后的 ChIP-seq）对比。
   - **创新状态**：unverified（需文献调研确认是否已有类似工作）。

2. **候选名称**：IHF 桥接的序列依赖性及其对拓扑域的影响
   - **来源局限/观察**：摘要未说明桥接是否依赖 DNA 序列；IHF 已知偏好特定序列。
   - **核心假设**：IHF 桥接事件具有序列特异性，且桥接位点的分布决定拓扑域边界。
   - **相对本文的增量**：从单体系模拟到序列-拓扑关系映射。
   - **初步方法**：设计不同序列的 minicircle（含/不含 IHF 共识序列），进行 MD 模拟；比较桥接频率和拓扑域划分；结合 Hi-C 数据（原核）验证。
   - **验证方式**：桥接频率的序列依赖性统计；拓扑域边界与 IHF 结合位点的共定位分析。
   - **创新状态**：unverified。

3. **候选名称**：超螺旋缓冲机制在 architectural proteins 中的普适性
   - **来源局限/观察**：本文提出 IHF 作为「超螺旋缓冲器」，但未验证其他蛋白是否具有类似功能。
   - **核心假设**：HU、H-NS、CTCF 等 architectural proteins 均具有符号依赖的扭转缓冲能力。
   - **相对本文的增量**：从 IHF 推广到多个蛋白家族，建立通用机制模型。
   - **初步方法**：对多个 architectural proteins 进行 MD 模拟（不同 σ），测量扭转波动抑制程度；比较缓冲能力与蛋白结构特征（如 DNA 弯曲角度、结合模式）的相关性。
   - **验证方式**：模拟结果与单分子实验（如磁镊扭转操纵）对比。
   - **创新状态**：unverified。

4. **候选名称**：AlphaFold 预测的 TF-DNA 复合物在超螺旋 DNA 中的稳定性
   - **来源局限/观察**：AlphaFold 等结构预测工具通常基于线性 DNA 或短寡核苷酸，未考虑超螺旋。
   - **核心假设**：AlphaFold 预测的 TF-DNA 复合物结构在超螺旋 DNA 中可能不稳定，需 MD 精化。
   - **相对本文的增量**：将结构预测与拓扑模拟结合，提高预测的生理相关性。
   - **初步方法**：用 AlphaFold 预测多个 TF-DNA 复合物结构；放入超螺旋 minicircle 中进行 MD 模拟；评估结构稳定性（RMSD、接触保留率）。
   - **验证方式**：与实验结构（如晶体结构）对比；统计稳定性与 σ 的关系。
   - **创新状态**：partially checked（AlphaFold 已用于 TF-DNA 预测，但超螺旋 MD 精化未见报道）。

5. **候选名称**：TF 结合诱导的 DNA 拓扑变化对远距离基因调控的影响
   - **来源局限/观察**：本文发现 IHF 桥接可分割拓扑域，但未探讨对基因表达的影响。
   - **核心假设**：TF 结合通过改变 DNA 拓扑（如固定 plectoneme、分割域）影响远距离增强子-启动子通讯。
   - **相对本文的增量**：从结构/拓扑到功能（基因表达）的跨越。
   - **初步方法**：结合 MD 模拟（拓扑域划分）与 3C/Hi-C 数据（染色质互作）；构建模型预测 TF 结合对互作频率的影响；用报告基因实验验证。
   - **验证方式**：模型预测与实验互作数据对比；报告基因表达水平与拓扑域划分的相关性。
   - **创新状态**：unverified。