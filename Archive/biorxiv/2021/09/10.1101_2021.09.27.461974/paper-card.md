## 01 基本信息

- **标题**：Protein-protein interaction-Gaussian accelerated molecular dynamics (PPI-GaMD): Characterization of protein binding thermodynamics and kinetics
- **作者**：Jinan Wang; Yinglong Miao
- **单位**：未提供（根据作者信息推测为美国北卡罗来纳大学教堂山分校计算医学中心，但原文未明确标注，故标注为未提供）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2021
- **论文类型**：方法学论文（方法开发 + 案例验证）
- **领域**：计算生物物理 / 分子动力学模拟 / 蛋白质-蛋白质相互作用
- **关键词**：Gaussian accelerated molecular dynamics (GaMD)、protein-protein interactions (PPIs)、binding free energy、binding kinetics、barnase-barstar
- **DOI/arXiv 号**：10.1101/2021.09.27.461974
- **代码**：未提供
- **数据**：未提供（模拟轨迹数据未公开）
- **阅读日期**：2026-05-13（按当前日期填写）
- **在该课题方向中的位置**：本文属于「物理模拟（MD）」分支，聚焦于通过增强采样 MD 方法（GaMD 的扩展）同时计算蛋白质-蛋白质结合的热力学（自由能）与动力学（速率常数）。对于 TF–DNA 互作课题，本文提供了一种可迁移的增强采样策略——选择性加速互作界面势能以捕获重复结合/解离事件，从而同时获得热力学与动力学信息。该方法不依赖 AI，但与 AI 方法（如预测结合位点或自由能面）可互补。

---

## 02 一句话总结

本文开发了 PPI-GaMD 方法，通过对蛋白质-蛋白质互作界面势能施加选择性 boost 来加速解离、同时对体系其余势能施加 boost 以保留柔性，在 barnase-barstar 模型体系上通过 6 条独立的 2 μs 模拟捕获了重复的结合/解离事件，从而同时计算了结合自由能与动力学速率常数，结果与实验吻合。

---

## 03 研究问题

- **具体问题**：如何通过全原子 MD 模拟高效地捕获蛋白质-蛋白质相互作用的重复结合与解离事件，从而同时计算结合自由能（热力学）与结合/解离速率常数（动力学）？
- **为什么重要**：PPIs 在细胞信号传导、免疫应答等基本生物过程中起关键作用。TF–DNA 互作同样属于此类问题——转录因子与 DNA 的结合/解离动力学直接决定基因调控的时间响应。然而，由于生物时间尺度长（毫秒至秒级）且蛋白质构象复杂，常规 MD 无法在可行算力内采样到足够的结合/解离事件。
- **现有方法为何不足**：常规 MD 受限于微秒级模拟，难以观察到 PPI 的重复结合/解离；增强采样方法（如 metadynamics、replica exchange）虽能加速，但往往只优化热力学采样，难以同时获得可靠的动力学信息（因 boost 会扭曲时间尺度）。
- **精确研究问题**：Can a selectively boosted GaMD approach capture repetitive protein association/dissociation events in all-atom simulations, thereby enabling simultaneous calculation of binding free energies and kinetic rate constants that agree with experimental data?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及作者引用的文献，属于「经外部核验」的领域共识，但具体分期为本文框架。

| 阶段 | 代表性方法 | 优点 | 局限 |
|------|-----------|------|------|
| 常规 MD | 经典全原子 MD | 物理上精确、无需先验知识 | 时间尺度受限（μs 级），难以采样 PPI 结合/解离 |
| 增强采样（自由能） | Umbrella sampling、metadynamics、replica exchange | 可计算结合自由能 | 动力学信息丢失或扭曲；计算成本高 |
| 加速 MD (aMD) | aMD 对势能面施加 boost | 可加速构象采样 | boost 选择不当会引入偏差；对 PPI 解离加速不足 |
| GaMD | 高斯加速 MD（Miao et al., 2015） | 通过高斯分布匹配的 boost 减少偏差，可同时获得热力学与动力学 | 对 PPI 的慢解离过程仍不够高效 |
| **本文位置** | **PPI-GaMD** | **选择性 boost 互作界面势能 + 全局 boost，同时捕获结合/解离** | **仅在单一模型体系（barnase-barstar）验证；需更多体系测试** |

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PPI 结合/解离时间尺度远超 MD 可达范围 | 常规 MD 无法在 μs 级模拟中观察到重复结合/解离 | 蛋白质结合/解离涉及毫秒至秒级时间尺度，且伴随大尺度构象变化 | 引言部分（未提供具体图/表编号） |
| 现有增强采样方法难以同时获得热力学与动力学 | 多数方法只优化自由能采样，动力学信息被 boost 扭曲 | boost 势能改变了体系的时间演化，导致速率常数无法直接恢复 | 引言部分（未提供具体图/表编号） |
| GaMD 对 PPI 解离加速不足 | 标准 GaMD 的 boost 作用于整个体系，对互作界面的慢解离过程加速有限 | 解离需要克服的能垒主要位于互作界面，需针对性 boost | 引言部分（未提供具体图/表编号） |
| 选择性 boost 可能引入偏差 | 若只 boost 互作界面，可能扭曲界面附近的构象分布 | 需通过 GaMD 的高斯匹配框架保证 boost 引入的偏差可被准确恢复 | Methods 节（未提供具体图/表编号） |

---

## 06 核心思想

### 1) 表面方法
PPI-GaMD 在标准 GaMD 基础上，将 boost 势能分解为两部分：
- **互作界面 boost**：仅对蛋白质-蛋白质之间的非键相互作用势能（范德华 + 静电）施加 boost，以加速解离。
- **全局 boost**：对体系其余势能施加标准 GaMD boost，以保留蛋白质内部柔性并促进 rebinding。

### 2) 核心洞察
[Analysis] 本文的关键洞察在于：PPI 解离的瓶颈是互作界面的非键相互作用能垒，而非蛋白质内部构象变化。因此，**选择性 boost 互作界面势能**可以在不扭曲蛋白质内部动力学的前提下，大幅加速解离过程。同时，保留全局 boost 可以维持蛋白质的构象柔性，使 rebinding 事件也能被有效采样。这种「双 boost」策略使得热力学（自由能）与动力学（速率常数）可以同时从同一组模拟中提取。

### 3) 可能的普适教训 [Analysis]
对于 TF–DNA 互作课题，本文的普适教训是：**当目标过程（如 TF 从 DNA 上解离）的能垒集中在特定相互作用界面时，针对该界面的选择性 boost 比全局 boost 更高效**。这一策略可迁移到 TF–DNA 体系——选择性加速 TF 与 DNA 之间的非键相互作用，同时保留 TF 和 DNA 的内部柔性，有望在可行算力内捕获重复的结合/解离事件。

---

## 07 方法总览

- **输入**：蛋白质-蛋白质复合物的全原子结构（本文为 barnase-barstar 复合物，PDB 结构未在摘要中给出具体编号）
- **输出**：结合自由能（ΔG）、结合速率常数（k_on）、解离速率常数（k_off）、结合/解离轨迹
- **模块**：
  1. 体系构建（溶剂化、加盐、平衡）
  2. GaMD boost 计算（互作界面 boost + 全局 boost）
  3. 增强采样 MD 模拟（多条独立轨迹）
  4. 轨迹分析（结合/解离事件检测、自由能计算、速率常数计算）
- **训练**：不适用（无机器学习训练；GaMD 的 boost 参数通过迭代计算确定）
- **工具**：未提供具体软件名称（推测为 AMBER 或 NAMD，但原文未明确）
- **反馈回路**：无显式反馈回路；boost 参数在模拟前确定，模拟中固定
- **文字流程**：
  1. 构建 barnase-barstar 复合物体系，进行能量最小化和平衡。
  2. 计算体系势能分布，确定 GaMD boost 参数（包括互作界面 boost 和全局 boost 的阈值与上限）。
  3. 运行 6 条独立的 2 μs PPI-GaMD 模拟。
  4. 从轨迹中检测 barstar 的解离与 rebinding 事件。
  5. 基于事件统计计算结合自由能（通过 Boltzmann 重新加权）与 k_on、k_off（通过事件时间统计）。
  6. 与实验数据对比验证。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 互作界面 boost | 选择性加速蛋白质-蛋白质间非键相互作用 | 解离能垒主要位于互作界面，需针对性加速 | 输入：界面非键势能；输出：boost 势能 | 摘要中明确说明「selectively boosts interaction potential energy between protein partners to facilitate their slow dissociation」 | 预期影响：解离事件无法在 2 μs 内被采样（预期效应，未实测） |
| 全局 boost | 加速蛋白质内部构象变化 | 保留蛋白质柔性以促进 rebinding | 输入：体系其余势能；输出：boost 势能 | 摘要中「another boost potential is applied to the remaining potential energy of the entire system to effectively model the protein's flexibility and rebinding」 | 预期影响：蛋白质柔性降低，rebinding 事件减少（预期效应，未实测） |
| 多轨迹模拟 | 6 条独立 2 μs 模拟 | 提高统计采样，捕获重复事件 | 输入：同一复合物不同初始速度；输出：6 条轨迹 | 摘要中「Six independent 2 μs PPI-GaMD simulations」 | 预期影响：统计不确定性增大，事件数不足（预期效应，未实测） |
| 事件检测与统计 | 从轨迹中识别结合/解离事件 | 计算速率常数需要事件时间统计 | 输入：轨迹坐标；输出：事件时间序列 | 摘要中「captured repetitive barstar dissociation and rebinding events」 | 预期影响：无法计算 k_on/k_off（预期效应，未实测） |
| 自由能计算 | 通过重新加权计算结合自由能 | 从增强采样轨迹恢复 unbiased 自由能 | 输入：boost 轨迹；输出：ΔG | 摘要中「calculated binding free energies ... agree well with the experimental data」 | 预期影响：ΔG 偏差增大（预期效应，未实测） |

> 注：本文为方法学论文，摘要中未提供消融实验数据，故所有「移除后影响」均为预期效应，非实测。

---

## 09 关键公式符号

> 本文为预印本，摘要中未给出具体公式。以下基于 GaMD 方法的通用框架（Miao et al., 2015）列出核心公式，但**不声称这些公式出现在本文中**。

| 公式 | 符号含义 | 用途 | 直觉 | 来源指针 |
|------|----------|------|------|----------|
| ΔV(r) = ½ k₀ (E - V(r))² 当 V(r) < E | ΔV(r)：boost 势能；k₀：谐波力常数；E：boost 阈值；V(r)：体系势能 | 标准 GaMD 的 boost 形式 | 当势能低于阈值时施加谐波 boost，使势能面变平 | GaMD 原始文献（Miao et al., 2015），本文摘要未给出 |
| ΔV_PPI(r) = ½ k_PPI (E_PPI - V_PPI(r))² | ΔV_PPI：互作界面 boost；V_PPI：蛋白质-蛋白质间非键势能 | 选择性加速界面解离 | 仅对界面势能施加 boost，不影响内部构象 | 本文方法描述（摘要中未给出公式） |
| ΔG = -k_B T ln⟨e^{βΔV}⟩_boost | ΔG：自由能；k_B：Boltzmann 常数；T：温度；β = 1/k_B T；⟨·⟩_boost：增强采样系综平均 | 从 boost 轨迹恢复 unbiased 自由能 | 通过指数重新加权消除 boost 偏差 | GaMD 标准框架，本文摘要未给出 |

> 注：以上公式为 GaMD 通用框架，本文摘要未提供具体公式，故标注为「基于 GaMD 通用框架，非本文直接给出」。

---

## 10 实验设计与证据链

- **数据集/体系**：barnase-ribonuclease 与 barstar-inhibitor 复合物（模型体系）
- **规模**：6 条独立的 2 μs 全原子 MD 模拟（总模拟时间 12 μs）
- **指标**：结合自由能（ΔG）、结合速率常数（k_on）、解离速率常数（k_off）
- **基线**：实验测得的 ΔG、k_on、k_off 值（具体数值未在摘要中给出）
- **预算**：未提供（未说明计算资源）
- **骨干/仪器**：未提供（未说明 GPU/CPU 集群）
- **oracle 输入**：不适用（无机器学习 oracle）
- **评测协议**：将 PPI-GaMD 计算的 ΔG、k_on、k_off 与实验数据对比

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 6×2 μs PPI-GaMD 模拟 | PPI-GaMD 能捕获重复结合/解离事件 | 与实验数据对比 | 捕获了重复的 barstar 解离与 rebinding 事件 | PPI-GaMD 能有效采样 PPI 结合/解离 | 未证明该方法对所有 PPI 体系均有效 | 摘要（未提供具体图/表编号） |
| 结合自由能计算 | PPI-GaMD 能准确计算 ΔG | 与实验 ΔG 对比 | 计算值与实验值吻合 | PPI-GaMD 可准确计算结合热力学 | 未提供误差范围或统计显著性 | 摘要（未提供具体数值） |
| 动力学速率常数计算 | PPI-GaMD 能准确计算 k_on/k_off | 与实验 k_on/k_off 对比 | 计算值与实验值吻合 | PPI-GaMD 可准确计算结合/解离动力学 | 未提供速率常数的置信区间 | 摘要（未提供具体数值） |
| 机制分析 | PPI-GaMD 能提供结合机制见解 | 与既往实验/计算发现对比 | 发现长程静电相互作用和多条结合路径 | 机制见解与既往发现一致 | 未提供定量比较 | 摘要（未提供具体图/表编号） |

---

## 11 结论正确解读

- **任务范围**：本文仅在一个模型体系（barnase-barstar）上验证了 PPI-GaMD 方法。该方法声称适用于一般 PPI 体系，但仅在单一体系上演示。
- **oracle/真值输入**：实验测得的 ΔG、k_on、k_off 作为真值；模拟输入为复合物结构（PDB 未给出编号）。
- **端到端状态**：方法端到端可用（从结构到热力学/动力学），但未提供自动化流程或软件包。
- **算力成本**：6×2 μs 全原子模拟，具体算力未披露；对于更大体系（如 TF–DNA 复合物），成本可能显著增加。
- **历史数据依赖**：不依赖历史数据（无机器学习训练）；但依赖初始复合物结构。
- **模型依赖**：依赖 GaMD 的 boost 参数选择；对力场选择敏感（未讨论）。
- **最难情形**：结合/解离极慢的 PPI 体系（如高亲和力复合物）可能需要更长模拟或更强 boost。
- **群体/领域边界**：仅适用于蛋白质-蛋白质体系；对蛋白质-DNA 体系需重新验证（DNA 的带电性质与蛋白质不同，boost 策略可能需要调整）。
- **不确定性**：未提供误差棒、重复性分析或统计显著性检验。
- **有边界的复述**：PPI-GaMD 在 barnase-barstar 体系上，通过 6×2 μs 模拟成功捕获了重复结合/解离事件，计算的 ΔG、k_on、k_off 与实验吻合，并提供了结合机制见解；但该方法在更多 PPI 体系及非蛋白体系（如 TF–DNA）上的普适性尚未验证。

---

## 12 作者自认局限

> 在提供的摘要中，作者未明确列出局限性。以下为摘要中隐含的约束，标注为「作者提及的相关约束」而非正式局限。

**作者提及的相关约束**（非正式局限）：
- 仅在单一模型体系（barnase-barstar）上演示（摘要中「demonstrated on a model system」）。
- 模拟时长为 2 μs/条，对于更慢的 PPI 体系可能需要更长模拟（摘要中未明确讨论，但「long biological timescales」作为动机暗示此约束）。
- 未提供方法对非蛋白体系（如蛋白-DNA）的适用性讨论。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 仅在单一体系（barnase-barstar）上验证 | 该方法可能对该体系特有性质（如强静电驱动结合）过拟合；对其他 PPI 或 TF–DNA 体系可能失效 | 方法普适性是核心 claim，单一体系不足以支撑 | 在多个不同亲和力、不同结合机制的 PPI 体系上测试；在 TF–DNA 体系上测试 | 摘要中「demonstrated on a model system」 |
| 未提供 boost 参数选择的敏感性分析 | 结果可能对 boost 阈值和力常数敏感；不同体系需重新调参 | 若参数敏感，方法「easy-to-use」的 claim 受质疑 | 对同一体系使用不同 boost 参数重复模拟，比较结果稳定性 | 摘要中「easy-to-use」claim，但未提供参数敏感性数据 |
| 未提供与实验数据的定量误差分析 | 「agree well with experimental data」缺乏量化标准（如误差百分比、置信区间） | 无法判断计算精度是否满足实际应用需求 | 提供 ΔG、k_on、k_off 的计算值与实验值的具体数值及误差 | 摘要中「agree well」但无数值 |
| 未讨论 boost 对动力学时间尺度的扭曲程度 | GaMD 的 boost 会加速动力学，但时间尺度重标因子（time rescaling factor）未讨论 | 若时间重标不准确，k_on/k_off 的绝对值可能不可靠 | 与已知动力学数据的体系对比，验证时间重标因子的准确性 | 摘要中未提及时间重标 |
| 未提供与标准 GaMD 的对比 | 无法判断 PPI-GaMD 相对标准 GaMD 的增量优势 | 若标准 GaMD 也能达到类似效果，PPI-GaMD 的「selective boost」策略必要性存疑 | 在同一体系上运行标准 GaMD 与 PPI-GaMD，对比采样效率与结果精度 | 摘要中未提供对比实验 |

---

## 14 学到什么

> **Agent 提炼的知识候选**

| 可迁移知识 | 类型 | 如何迁移到 TF–DNA 互作课题 |
|-----------|------|---------------------------|
| **选择性 boost 互作界面势能** | 方法策略 | 对 TF–DNA 体系，可选择性加速 TF 与 DNA 之间的非键相互作用（特别是静电和氢键），以加速 TF 从 DNA 上的解离，同时保留 TF 和 DNA 内部柔性以促进 rebinding |
| **双 boost 策略（界面 + 全局）** | 方法设计 | 在 TF–DNA 模拟中，界面 boost 加速解离，全局 boost 保留 TF 的构象变化（如 DNA 结合域的开合），两者结合可同时采样结合与解离 |
| **从增强采样轨迹恢复 unbiased 自由能** | 理论框架 | GaMD 的 Boltzmann 重新加权框架可直接迁移到 TF–DNA 体系，用于计算 TF–DNA 结合自由能 |
| **多轨迹独立模拟提高事件采样** | 实验设计 | 对 TF–DNA 体系，可运行多条独立短轨迹（而非单条长轨迹）以捕获更多结合/解离事件，提高统计可靠性 |
| **动力学速率常数从事件统计中提取** | 分析方法 | 通过检测 TF–DNA 结合/解离事件的时间序列，可计算 k_on/k_off，为基因调控动力学提供计算预测 |
| **长程静电相互作用驱动结合** | 机制洞察 | 本文发现长程静电在 barnase-barstar 结合中起关键作用；TF–DNA 结合同样由静电主导（DNA 带负电），此机制洞察可指导增强采样 boost 的设计（优先 boost 静电项） |

---

## 15 与已有知识连接

- **GaMD 原始方法**：Miao et al., *J. Chem. Theory Comput.* 2015, 11, 3584–3595。本文是 GaMD 在 PPI 体系上的扩展，核心框架（高斯 boost、重新加权）继承自该工作。
- **aMD 系列方法**：Hamelberg et al., *J. Chem. Phys.* 2004, 120, 11919–11929。加速 MD 的早期工作，GaMD 是其改进版本。
- **PPI 结合/解离模拟的挑战**：与 Pan et al., *J. Phys. Chem. B* 2017 等关于 PPI 增强采样的工作相关；本文的「选择性 boost」策略是对「体系特定 boost」思路的推进。
- **TF–DNA 互作模拟**：与蛋白质-DNA 对接和 MD 模拟文献（如 Zhang et al., *Nucleic Acids Res.* 2020 等）相关；本文方法可迁移到 TF–DNA 体系，但需注意 DNA 的带电性和柔性差异。
- **动力学与热力学同时计算**：与 milestoning、Markov state models 等方法互补；本文提供了一种更简单的替代方案（直接增强采样 + 事件统计）。
- **[Analysis] 候选方向**：本文方法可与 AI 方法结合——例如用机器学习预测 TF–DNA 结合位点或识别关键界面残基，再用 PPI-GaMD 验证动力学；或用量子化学/MM-PBSA 方法验证 PPI-GaMD 计算的自由能。

---

## 16 研究想法

> **Agent 生成的研究候选**

### 候选 1：TF–DNA 互作的 PPI-GaMD 迁移验证
- **名称**：TF-DNA-GaMD：选择性加速转录因子-DNA 结合/解离的增强采样方法
- **来源局限/观察**：PPI-GaMD 仅在蛋白质-蛋白质体系上验证；TF–DNA 体系具有不同的物理化学特征（DNA 高度带电、柔性大、结合界面大），方法迁移需重新验证
- **核心假设**：选择性 boost TF-DNA 界面非键势能（特别是静电项）可有效加速 TF 从 DNA 上的解离，同时保留 TF 和 DNA 的构象柔性以促进 rebinding
- **初步方法**：选取一个已知动力学数据的 TF–DNA 体系（如 p53-DNA 或 LacI-DNA），构建全原子体系，应用 PPI-GaMD 的双 boost 策略（界面 boost + 全局 boost），运行多条独立微秒级模拟，检测结合/解离事件，计算 ΔG、k_on、k_off
- **验证方式**：与实验测得的结合亲和力和动力学数据对比；与标准 MD 和标准 GaMD 对比采样效率
- **可能的失败模式**：DNA 的强负电性可能导致界面 boost 过大，扭曲构象分布；TF-DNA 结合界面大，boost 区域选择困难；DNA 的柔性可能导致 rebinding 路径复杂，事件检测困难
- **创新状态**：unverified（方法迁移到新体系，需实验验证）

### 候选 2：PPI-GaMD 与机器学习结合预测 TF 结合动力学
- **名称**：ML-guided PPI-GaMD：用机器学习预测关键界面残基以指导选择性 boost
- **来源局限/观察**：PPI-GaMD 的界面 boost 需要预先定义「互作界面」，但界面残基的选择可能影响采样效率；机器学习可自动识别关键界面残基
- **核心假设**：用机器学习（如图神经网络）从静态结构预测 TF-DNA 结合的关键界面残基，将其作为 PPI-GaMD 的 boost 区域，可提高采样效率
- **初步方法**：训练一个 GNN 模型预测 TF-DNA 结合界面残基（基于已知复合物结构），将预测结果作为 PPI-GaMD 的 boost 区域定义，在多个 TF-DNA 体系上测试
- **验证方式**：对比 ML-guided boost 与人工定义界面的采样效率（事件数/μs）和计算精度（ΔG、k_on/k_off 与实验对比）
- **可能的失败模式**：ML 预测的界面残基不准确；boost 区域过大导致计算成本增加；ML 预测与 MD 模拟的误差叠加
- **创新状态**：unverified（跨学科组合，需验证可行性）

### 候选 3：TF–DNA 结合动力学的多路径分析
- **名称**：Pathway analysis of TF-DNA binding from PPI-GaMD trajectories
- **来源局限/观察**：PPI-GaMD 在 barnase-barstar 上发现了多条结合路径；TF-DNA 结合可能同样存在多条路径（如 sliding、hopping、direct binding），但缺乏原子级描述
- **核心假设**：PPI-GaMD 轨迹可揭示 TF-DNA 结合的多条微观路径，且不同路径的贡献与 TF 的 DNA 结合域结构相关
- **初步方法**：对 TF-DNA 体系运行 PPI-GaMD，用路径集合分析（transition path sampling 或 Markov state model）从轨迹中提取结合路径，聚类分析不同路径的构象特征
- **验证方式**：与单分子实验（如 FRET、optical tweezers）观察到的结合动力学对比；与已知 TF 结合机制文献对比
- **可能的失败模式**：PPI-GaMD 的 boost 可能扭曲路径分布；路径聚类的主观性；轨迹长度不足以覆盖所有路径
- **创新状态**：unverified（需在 TF-DNA 体系上验证）

### 候选 4：PPI-GaMD 与 AI 自由能预测的交叉验证
- **名称**：Cross-validation of PPI-GaMD free energies with AI-based binding affinity predictors
- **来源局限/观察**：PPI-GaMD 计算的 ΔG 与实验吻合，但未与 AI 预测工具（如 AlphaFold 的 pLDDT、RoseTTAFold 的 confidence score、或基于深度学习的 binding affinity 预测器）对比
- **核心假设**：PPI-GaMD 计算的 ΔG 与 AI 预测的 binding affinity 具有相关性，但 AI 预测无法提供动力学信息，两者互补
- **初步方法**：在多个 PPI 体系（包括 TF-DNA）上，分别用 PPI-GaMD 计算 ΔG 和用 AI 工具预测 binding affinity，对比两者的相关性和差异
- **验证方式**：与实验数据对比，评估两种方法的互补性；分析 AI 预测误差与 PPI-GaMD 模拟时间的关系
- **可能的失败模式**：AI 预测工具对 PPI 的准确性有限；PPI-GaMD 的计算成本高，难以覆盖大体系；两种方法的误差来源不同，难以直接对比
- **创新状态**：unverified（需系统性对比研究）