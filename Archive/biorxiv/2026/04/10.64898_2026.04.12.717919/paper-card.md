## 01 基本信息

- **标题**：A Hybrid Physics-Deep Learning Framework for Combinatorial De Novo Design of Small-Molecule Binding Proteins
- **作者与单位**：Connor V Galvin; Amy B Guo; Maple N Chen; Isabella L Alfonso; Dominic Grisingher; Simon Kretschmer; Divya Kranthi; Mark JS Kelly; Tanja Kortemme（加州大学旧金山分校，Kortemme 实验室）
- **期刊/预印本平台**：bioRxiv
- **年份**：2026
- **论文类型**：预印本（方法学 + 实验验证）
- **领域**：蛋白质设计（小分子结合蛋白的 de novo 设计）
- **关键词**：de novo protein design, small-molecule binding, motif scaffolding, combinatorial assembly, physics-based refinement, deep learning, alpha-beta architecture
- **DOI/arXiv 号**：10.64898/2026.04.12.717919
- **代码**：https://github.com/cvgalvin/CLAIRE
- **数据**：https://doi.org/10.5061/dryad.7pvmcvf8c（补充数据）；NMR 结构将存入 PDB（代码 11EZ）
- **阅读日期**：未提供
- **在该方向中的位置**：本文属于「蛋白质-配体（小分子）互作」的 de novo 设计，而非 TF–DNA 互作。但其核心问题——如何在原子精度上满足预定义的互作几何（氢键网络）——与 TF–DNA 结合机制高度同构。其「组合式 motif 筛选 + 物理/深度学习混合优化」的框架，对 TF–DNA 结合特异性设计具有直接的方法论迁移价值。

---

## 02 一句话总结

本文提出 CLAIRE 框架，通过将小分子结合 motif（BSFF 生成）组合式嫁接到数千个几何微调的 alpha-beta 骨架（LUCS 生成）中，再经 Rosetta 物理能量优化与 ProteinMPNN 序列设计迭代，以 4/26 的实验结合成功率（15% 结合率，其中 2 个 NMR 结构验证）实现了对孕酮和雌三醇的 de novo 结合蛋白设计，无需高通量筛选。

---

## 03 研究问题

- **具体问题**：如何以高于 1% 的成功率、无需高通量筛选地 de novo 设计结合特定小分子的蛋白质？
- **为什么重要**：小分子结合蛋白在生物传感、药物递送、催化等领域有广泛应用；现有生成模型（如扩散模型）难以在原子精度上满足配体互作的严格几何约束，导致成功率极低（<0.1%）。
- **现有方法不足**：
  - 端到端生成模型（如 RFdiffusion all-atom）虽能生成整体结构，但对氢键等极性互作的几何精度不足，导致大量设计失败。
  - 基于 motif 的螺旋束设计（helical bundle scaffolding）虽成功率高，但局限于螺旋束拓扑，无法覆盖 alpha-beta 折叠等更广泛的天然小分子结合蛋白拓扑。
  - 物理能量函数（Rosetta）单独使用难以搜索巨大的序列-结构空间。
- **精确研究问题**：Can a combinatorial assembly of pre-defined binding motifs into geometrically diverse alpha-beta scaffolds, followed by hybrid physics-deep learning refinement, achieve experimental binding success rates above 1% without high-throughput screening?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及引用，属于「经外部核验」的领域共识，但具体分期为本文框架。

| 阶段 | 代表性方法 | 优点 | 局限 |
|------|-----------|------|------|
| 早期计算设计 | Rosetta 序列设计 + 能量最小化 | 可设计稳定蛋白 | 小分子互作精度不足，成功率极低 |
| 生成式深度学习 | RFdiffusion、Chroma 等扩散模型 | 可生成多样骨架 | 对配体极性互作的原子级几何建模不足，成功率 <0.1% |
| Motif 脚手架设计 | 螺旋束参数化设计（helical bundle scaffolding） | 预定义互作可高保真保留 | 仅限螺旋束拓扑，无法推广到 alpha-beta 等拓扑 |
| 组合式骨架筛选 | 本文 CLAIRE（BSFF + LUCS + 混合优化） | 推广到 alpha-beta 拓扑，成功率显著提升 | 依赖 motif 库质量与骨架库多样性 |

**本文主张的位置**：将「预定义互作 motif」策略从螺旋束推广到 alpha-beta 拓扑，并通过「组合式大规模筛选 + 物理/深度学习混合优化」弥补单一方法的不足。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 生成模型对配体互作精度不足 | RFdiffusion 等生成的设计难以满足氢键几何约束 | 扩散模型在生成时未显式优化配体极性互作；氢键对几何偏差极为敏感 | Results 图 2A-B：RFdiffusion 设计在氢键数量与几何满意度上显著低于 CLAIRE |
| 极性原子去溶剂化代价高 | 配体极性原子埋入蛋白内部需形成完整氢键网络，否则能量惩罚大 | 埋藏极性原子的去溶剂化能需由新形成的氢键补偿，Rosetta 能量函数难以精确建模 | Discussion：氢键网络是设计失败主因之一 |
| 物理能量函数与观测频率不一致 | Rosetta 能量评分与天然互作频率不相关 | 能量函数未充分捕捉 pi-stacking、cation-pi 等非共价互作的几何偏好 | Results 图 1D：pi-stacking 在能量上无显著偏好，但统计上高度富集 |
| 骨架-配体几何匹配概率低 | 随机骨架与给定 motif 的匹配率极低（~10⁻⁴） | 多残基 motif 的几何约束严格，随机搜索空间巨大 | Introduction：motif-scaffold 匹配概率约 10⁻⁴ |
| 螺旋束拓扑限制 | 现有 motif 脚手架方法仅适用于螺旋束 | 螺旋束中心腔几何有限，无法容纳多样配体 | Introduction：需推广到 alpha-beta 拓扑 |
| 高通量筛选依赖 | 现有方法需筛选数千至数万设计才能获得少量 hits | 设计精度不足导致 hit rate 极低 | Discussion：CLAIRE 无需高通量筛选即可获得功能 binder |

---

## 06 核心思想

### 1) 表面方法

CLAIRE 框架分三步：
1. **Motif 生成**（BSFF）：将目标小分子分解为化学亚结构，从 PDB 中挖掘与这些亚结构互作的氨基酸残基组合，聚类为离散的互作模式（motif），每个 motif 含 3-4 个残基，定义精确的氢键/堆积几何。
2. **骨架生成**（LUCS）：以天然 NTF2 折叠为模板，系统变化螺旋-环-螺旋单元的几何参数（长度、角度、方向），生成 1,816 个几何微调的 alpha-beta 骨架。
3. **组合式嫁接与优化**：将 motif 通过 Rosetta Match 嫁接到骨架库中，筛选高保真匹配；随后经 Rosetta FastDesign（结合位点）、HBRefine（氢键网络修复）、ProteinMPNN（非结合位点序列设计）、Rosetta FastRelax（结构松弛）迭代优化，最终以 AlphaFold2 验证结构一致性。

### 2) 核心洞察

- **「先定义互作，再找骨架」优于「先生成骨架，再设计互作」**：将原子级互作几何作为硬约束，通过大规模组合筛选找到能高保真容纳该几何的骨架，而非依赖生成模型隐式学习互作。
- **统计偏好可弥补能量函数缺陷**：BSFF 的聚类分析揭示了 Rosetta 能量函数未充分捕捉的互作偏好（如 pi-stacking），用统计富集替代能量评分可提高 motif 质量。
- **物理与深度学习互补**：物理方法（Rosetta）负责显式互作与能量优化，深度学习方法（ProteinMPNN、AlphaFold2）负责序列设计与结构验证，各取所长。

### 3) 可能的普适教训 [Analysis]

- 对 TF–DNA 互作设计：DNA 碱基的氢键供体/受体模式比小分子更规则，BSFF 式「从 PDB 挖掘互作模式 + 组合式骨架筛选」的策略可直接迁移——先定义 TF 与 DNA 碱基的氢键/堆积 motif，再在骨架库中搜索能高保真呈现这些 motif 的折叠。
- 「统计偏好 > 能量评分」的发现对 TF–DNA 同样适用：Rosetta 等物理函数对 DNA 互作的极性/堆积项建模同样不完善，从 PDB 统计中提取碱基-氨基酸互作偏好可能更可靠。
- 「组合式筛选 + 混合优化」的框架可推广为通用范式：任何「预定义互作 + 骨架搜索」的问题都可借鉴。

---

## 07 方法总览

- **输入**：目标小分子（孕酮/雌三醇）的化学结构；天然 NTF2 蛋白结构（PDB 5TPJ）
- **输出**：设计的小分子结合蛋白序列及预测结构
- **模块**：
  1. BSFF motif 生成（统计聚类互作模式）
  2. LUCS 骨架库生成（几何参数化采样）
  3. Rosetta Match（motif 嫁接与筛选）
  4. Rosetta FastDesign（结合位点序列设计）
  5. HBRefine（氢键网络修复，自定义算法）
  6. ProteinMPNN（非结合位点序列设计）
  7. Rosetta FastRelax（结构松弛与能量过滤）
  8. AlphaFold2/ColabFold（结构验证与过滤）
- **训练**：无端到端训练；BSFF 和 LUCS 为数据驱动方法，ProteinMPNN 和 AlphaFold2 为预训练模型
- **反馈回路**：AlphaFold2 预测结构 → 与设计模型比对（RMSD）→ 过滤低一致性设计；HBRefine 识别未满足氢键 → 引入突变 → 重新评估
- **文字流程**：小分子 → BSFF 分解为亚结构 → 挖掘 PDB 互作残基 → 聚类为 motif 库 → LUCS 生成骨架库 → Rosetta Match 将 motif 嫁接到骨架 → 筛选埋藏良好、无冲突的匹配 → FastDesign 设计结合位点序列 → HBRefine 修复氢键网络 → ProteinMPNN 设计外围序列 → FastRelax 松弛 → AlphaFold2 验证 → 实验表征

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| BSFF motif 生成 | 从 PDB 挖掘小分子亚结构-氨基酸互作模式并聚类 | 提供原子级精确的预定义互作几何，避免生成模型隐式学习的精度不足 | 输入：小分子结构；输出：3-4 残基 motif 库 | Results 图 1A、1D：统计富集的 pi-stacking 等互作模式 | 预期影响：失去高保真互作模板，设计精度大幅下降 [预期效应] |
| LUCS 骨架库生成 | 系统变化 NTF2 折叠的螺旋-环-螺旋几何，生成 1,816 个骨架 | 提供几何多样化的 alpha-beta 骨架，增加与 motif 匹配的概率 | 输入：NTF2 模板；输出：骨架库 | Results 图 1B、1E：匹配成功率 >160 matches/motif | 预期影响：骨架多样性不足，匹配率下降 [预期效应] |
| Rosetta Match | 将 motif 嫁接到骨架并筛选高保真匹配 | 组合式搜索 motif-骨架兼容性，解决低匹配概率问题 | 输入：motif 库 + 骨架库；输出：嫁接结构 | Results 图 1E：所有 5 种小分子均获得 >10,000 嫁接结构 | 实测：无此步则无法获得初始设计 [作者逻辑推断] |
| HBRefine | 识别并修复结合位点未满足氢键 | 氢键网络是设计成功的关键瓶颈，通用优化难以满足 | 输入：FastDesign 后结构；输出：氢键优化后结构 | Results 图 1F、1G：加入后 in silico 成功率提升至 6.8% | 实测：移除后 in silico 成功率显著下降（图 1G） |
| ProteinMPNN | 重新设计结合位点外序列 | 稳定整体折叠，提高序列-结构兼容性 | 输入：结合位点固定结构；输出：全序列 | Results 图 1G：加入后成功率进一步提升 | 实测：移除后成功率下降（图 1G） |
| AlphaFold2 过滤 | 预测结构并与设计模型比对 | 验证设计的可折叠性与结构保真度 | 输入：设计序列；输出：预测结构 + 置信度 | Methods：pLDDT ≥ 88.0 且 Ca RMSD ≤ 1.5 Å 过滤 | 预期影响：无法过滤错误折叠设计 [预期效应] |

---

## 09 关键公式符号

本文为方法学论文，无核心数学公式。关键量化指标如下：

- **motif-scaffold 匹配概率**：~10⁻⁴（Introduction，3 残基 motif）
- **in silico 成功率**：CLAIRE 6.8%（雌三醇）、5.2%（孕酮）；RFdiffusion 0.09%（孕酮）（Results 图 2A）
- **实验结合成功率**：4/26 设计结合靶标（雌三醇 1/13，孕酮 3/13）（Results 图 3B）
- **结构验证**：NMR 结构与设计模型 Ca RMSD 1.57 Å（A1E apo）、1.46 Å（D2P holo）（Results 图 4）
- **HBRefine 提升倍数**：in silico 成功率提升约 7 倍（Results 图 1G）
- **Rosetta 能量项**：fa_atr、fa_rep、hbond_sc、hbond_bb_sc、fa_elec（权重 1, 0.55, 1, 1, 1）
- **过滤阈值**：配体埋藏 ≥ 70%（dsasa）、结合位点 rotamer Boltzmann 概率 ≥ 0.3、PackStat ≥ 0.6、疏水 SASA ≤ 1200 Å²、空腔体积 ≤ 120 Å³

---

## 10 实验设计与证据链

**数据集/群体**：
- 靶标分子：孕酮（progesterone）、雌三醇（estriol）；泛化测试：咖啡酸、3-氰基-7-羟基香豆素、DFHBI
- 骨架库：1,816 个 LUCS 生成的 NTF2 骨架（初始 1,709 个经 3 轮 ProteinMPNN/ColabFold 筛选）
- 对比方法：RFdiffusion all-atom（约 30,000 个扩散设计/靶标）
- 实验表征：26 个设计（每靶标 13 个）进行表达、SEC、NMR 结合筛选

**指标**：
- in silico：氢键数量、配体埋藏、形状互补性、结合位点预组织、AlphaFold2 一致性
- 实验：SEC 单聚体、¹⁵N-HSQC 化学位移扰动、NMR 结构解析

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| BSFF 互作模式统计 | 特定互作模式在 PDB 中统计富集 | 聚类 vs. 随机期望 | pi-stacking 等模式显著富集 | 统计偏好可指导 motif 设计 | 统计富集 ≠ 能量有利 | Results 图 1D |
| Motif 嫁接筛选 | 组合式筛选可找到高保真匹配 | 5 种小分子 × 1,816 骨架 | 所有分子均获 >10,000 嫁接结构 | 组合式策略可克服低匹配概率 | 未直接验证结合活性 | Results 图 1E |
| CLAIRE vs RFdiffusion in silico | CLAIRE 设计质量更高 | 相同过滤标准 | 成功率 6.8%/5.2% vs 0.09% | 预定义互作优于隐式生成 | in silico ≠ 实验结合 | Results 图 2A-B |
| HBrefine 消融 | 氢键优化提升成功率 | 有/无 HBrefine | 成功率提升约 7 倍 | 氢键网络是关键瓶颈 | 未单独验证各氢键贡献 | Results 图 1G |
| 实验结合筛选 | 设计能结合靶标 | 26 设计 vs 靶标 | 4/26 结合（15%） | 无需高通量筛选即可获得 binder | 亲和力未定量（仅 NMR 扰动） | Results 图 3B |
| NMR 结构验证 | 设计结构与模型一致 | A1E apo、D2P holo | Ca RMSD 1.57/1.46 Å | 设计模型准确 | 仅 2 个结构验证 | Results 图 4 |
| 点突变验证 | 设计的氢键残基关键 | 5 个突变体 | 结合信号显著减弱 | 设计的互作模式真实 | 未做丙氨酸扫描全覆盖 | Results 图 5 |

---

## 11 结论正确解读

- **任务范围**：本文解决的是「小分子结合蛋白」的 de novo 设计，而非 TF–DNA 互作。其结论边界为：对分子量 180-314 Da 的疏水性小分子（甾体类），通过预定义互作 + 组合式骨架筛选可实现 15% 的实验结合成功率。
- **oracle/真值输入**：BSFF 依赖 PDB 中天然蛋白-配体复合物的互作数据；AlphaFold2 作为结构验证 oracle。这些输入的质量直接影响设计成功率。
- **端到端状态**：非端到端生成。设计流程为「模块化流水线」，各步骤独立优化，最终由实验验证。
- **算力成本**：未明确报告总计算量；但 1,816 骨架 × 数百 motif × 多轮优化，估计为中等规模（数万 CPU 小时级）。
- **历史数据依赖**：BSFF 依赖 PDB 中已有的蛋白-配体复合物；对全新化学空间的小分子，motif 库可能不足。
- **最难情形**：极性高、柔性大的小分子（如糖类、多磷酸盐）可能难以设计，因为氢键网络更复杂、去溶剂化代价更高。
- **不确定性**：4/26 的成功率基于 NMR 化学位移扰动判断，未报告定量 Kd；亲和力可能为弱-中等（μM 级）。
- **有边界的复述**：CLAIRE 通过「预定义互作 + 组合式骨架筛选 + 物理/深度学习混合优化」，在甾体类小分子上实现了 15% 的实验结合成功率，显著优于 RFdiffusion 的 <0.1%，但该结论仅适用于与训练数据化学空间相似的小分子，且未定量亲和力。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 结合亲和力未定量 | NMR 化学位移扰动仅定性判断结合，未报告 Kd | 未来需进行定量亲和力测量（ITC、SPR） | Discussion |
| 设计成功率仍有提升空间 | 4/26 结合，但仅 2 个结构验证 | 扩大骨架库多样性、改进 motif 库质量 | Discussion |
| 对极性/柔性小分子的适用性未知 | 仅测试了疏水性甾体类分子 | 需在更广泛化学空间验证 | Discussion |
| 计算成本较高 | 需数千骨架 × 数百 motif 的组合筛选 | 开发更高效的筛选算法 | Discussion |
| 依赖 PDB 互作数据 | BSFF 的 motif 库受限于已知复合物结构 | 结合生成模型扩展 motif 空间 | Discussion |
| 与天然蛋白的互作模式差异 | 设计的氢键网络与天然蛋白不同 | 需进一步优化氢键几何 | Discussion |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 4/26 成功率基于 NMR 化学位移扰动 | 化学位移扰动可能来自非特异性结合或构象变化，而非特异性结合 | 成功率可能被高估 | 进行 ITC 或 SPR 定量亲和力测量 | Results 图 3B |
| 与 RFdiffusion 的比较条件可能不公 | RFdiffusion 未经过同等程度的迭代优化和过滤 | 比较结论可能偏向 CLAIRE | 对 RFdiffusion 设计施加相同优化流程后比较 | Results 图 2A |
| BSFF 的统计富集分析可能受 PDB 冗余影响 | 高同源性蛋白可能重复贡献相同互作模式 | 统计偏好可能被放大 | 使用非冗余数据集重新分析 | Methods：已按 70% 序列同一性去冗余 |
| HBrefine 的 7 倍提升可能依赖特定过滤阈值 | 阈值选择可能人为放大差异 | 提升幅度可能不具普适性 | 在多个阈值下进行敏感性分析 | Results 图 1G |
| 仅测试了 2 个化学相似靶标 | 孕酮和雌三醇结构高度相似，可能无法代表一般性 | 方法的泛化性未充分验证 | 在更多样化的小分子上测试 | Results 图 3 |
| 未报告阴性对照（如随机序列） | 无法排除非特异性结合 | 结合信号可能来自非特异性相互作用 | 加入随机序列或 scrambled 序列作为阴性对照 | 未提供 |
| 设计成功率可能依赖 NTF2 折叠的天然小分子结合倾向 | NTF2 天然结合疏水性配体，可能使设计更容易 | 方法在其他折叠上的适用性未知 | 在非配体结合折叠上测试 | Introduction：NTF2 天然结合小分子 |

---

## 14 学到什么

> 以下为面向「TF–DNA 互作 × AI/物理模拟」课题方向的可迁移知识。

### Agent 提炼的知识候选

1. **「先定义互作，再找骨架」的逆向设计范式**：CLAIRE 的核心不是生成模型，而是「预定义互作 motif + 大规模骨架筛选」。对 TF–DNA 设计，可先定义 TF 与 DNA 碱基的氢键/堆积 motif（如锌指与碱基的序列特异性氢键模式），再在骨架库中搜索能高保真容纳这些 motif 的折叠。这比端到端生成更可控。

2. **统计偏好 > 能量评分的 motif 筛选策略**：BSFF 发现 Rosetta 能量函数未捕捉 pi-stacking 等互作偏好，改用 PDB 统计富集。对 TF–DNA，Rosetta 等物理函数对 DNA 碱基互作的极性/堆积项建模同样不完善，从 PDB 中统计提取「氨基酸-碱基」互作偏好（如精氨酸-鸟嘌呤的 bidentate 氢键）可能更可靠。

3. **组合式筛选克服低概率匹配**：motif-scaffold 匹配概率仅 ~10⁻⁴，但通过组合式大规模筛选（1,816 骨架 × 数百 motif）可获得足够候选。对 TF–DNA，若预定义 3-4 残基的 DNA 结合 motif，同样需要大规模骨架库筛选，而非依赖单一折叠。

4. **物理-深度学习混合优化流水线**：CLAIRE 的「Rosetta 物理优化（互作）+ ProteinMPNN（序列）+ AlphaFold2（验证）」迭代流程，可迁移到 TF–DNA 设计：Rosetta 负责 DNA 互作几何优化，ProteinMPNN 负责蛋白序列设计，AlphaFold2 验证折叠与互作。

5. **氢键网络是设计成败的关键瓶颈**：CLAIRE 专门开发 HBRefine 修复氢键网络，因为这是主要失败原因。对 TF–DNA，碱基特异性识别几乎完全依赖氢键网络，HBRefine 的思路（识别未满足氢键 → 定向突变 → 重新评估）可直接迁移。

6. **统计互作模式可弥补物理能量函数缺陷**：BSFF 的聚类分析揭示了物理能量函数未建模的互作模式。对 TF–DNA，可类似地从 PDB 中挖掘「氨基酸-碱基」互作模式库，用于指导 motif 设计。

7. **实验验证策略**：CLAIRE 使用 NMR 化学位移扰动筛选结合，并用 NMR 结构验证设计准确性。对 TF–DNA 设计，类似的 NMR 滴定（¹⁵N-HSQC 化学位移扰动）可直接用于验证 TF 与 DNA 的结合。

---

## 15 与已有知识连接

- **AlphaFold2 (Jumper et al., 2021)**：本文使用 AlphaFold2 作为结构验证工具，验证设计序列的可折叠性。对 TF–DNA 课题，AlphaFold2 同样可用于验证 TF 结构预测，但其对蛋白-核酸复合物的预测能力有限，需结合专门工具。
- **RFdiffusion (Watson et al., 2023)**：本文以 RFdiffusion all-atom 作为对比基线，指出其在配体互作精度上的不足。对 TF–DNA，RFdiffusion 的蛋白-DNA 复合物生成能力仍在发展中，本文的对比结论提示其可能同样面临互作精度问题。
- **ProteinMPNN (Dauparas et al., 2022)**：本文使用 ProteinMPNN 进行序列设计，其逆折叠能力对 TF–DNA 设计同样适用，但需注意 DNA 结合界面的序列约束。
- **Rosetta Match (Zanghellini et al., 2006)**：本文使用 Rosetta Match 进行 motif 嫁接，该方法同样可用于将 DNA 结合 motif 嫁接到骨架。
- **Motif scaffolding 策略 (e.g., Polizzi & DeGrado, 2020)**：本文将该策略从螺旋束推广到 alpha-beta 拓扑，对 TF–DNA 设计有直接启示——DNA 结合结构域（如锌指、螺旋-转角-螺旋）的 scaffolding 可借鉴此思路。
- **统计互作偏好分析 (e.g., 蛋白质-配体互作数据库)**：BSFF 的聚类方法可迁移到蛋白质-DNA 互作数据库（如 PDB 中的 TF-DNA 复合物），挖掘碱基-氨基酸互作偏好。
- **NMR 化学位移扰动筛选**：本文的实验验证方法在 TF–DNA 研究中已有广泛应用（如转录因子与 DNA 的滴定实验），两者方法学一致。

---

## 16 研究想法

> 以下为面向「TF–DNA 互作 × AI/物理模拟」课题方向的研究候选。

### Agent 生成的研究候选

1. **名称**：TF-DNA-Motif：基于统计互作偏好的转录因子-DNA 结合 motif 挖掘与设计框架
   - **来源局限/观察**：CLAIRE 的 BSFF 方法证明「从 PDB 挖掘互作模式 + 组合式筛选」可有效设计小分子结合蛋白；TF–DNA 互作同样有大量 PDB 数据，但缺乏类似的系统化 motif 挖掘。
   - **核心假设**：从 TF-DNA 复合物结构中挖掘的「氨基酸-碱基」互作模式（氢键、堆积、疏水）可构成高保真 motif 库，用于 de novo TF 设计。
   - **初步方法**：类似 BSFF，将 DNA 碱基分解为化学亚结构，从 PDB 中提取互作氨基酸，聚类为离散互作模式；用 Rosetta Match 将 motif 嫁接到 alpha-beta 骨架库；用 Rosetta + ProteinMPNN + AlphaFold2 优化。
   - **验证方式**：设计针对特定 DNA 序列的 TF，用 EMSA 或 NMR 滴定验证结合；与 RFdiffusion 生成的 TF 对比成功率。
   - **创新状态**：unverified（方法迁移自小分子结合蛋白设计，未在 TF-DNA 上验证）

2. **名称**：HB-Refine-DNA：面向蛋白-DNA 界面的氢键网络优化算法
   - **来源局限/观察**：CLAIRE 的 HBRefine 显著提升设计成功率，证明氢键网络是设计瓶颈；TF-DNA 识别的核心同样是氢键网络（碱基特异性），但现有设计工具缺乏针对 DNA 互作的氢键优化。
   - **核心假设**：针对 DNA 碱基的氢键供体/受体模式定制优化算法，可提升 TF-DNA 设计的成功率。
   - **初步方法**：扩展 HBRefine，加入 DNA 碱基的氢键几何约束（如 Watson-Crick 边缘的供体/受体模式），在 Rosetta 能量函数中增加 DNA 互作项。
   - **验证方式**：在已知 TF-DNA 复合物上测试优化后结构的氢键满意度；在 de novo 设计上比较有无 HB-Refine-DNA 的成功率。
   - **创新状态**：unverified（HBRefine 为本文原创，DNA 扩展为候选方向）

3. **名称**：Combi-TF：组合式 TF 骨架筛选框架
   - **来源局限/观察**：CLAIRE 通过组合式筛选 1,816 个骨架克服了低匹配概率；TF-DNA 设计同样面临「预定义 DNA 结合 motif 与骨架匹配率低」的问题。
   - **核心假设**：对 DNA 结合 motif 进行组合式骨架筛选，可找到高保真匹配的 alpha-beta 骨架，优于端到端生成。
   - **初步方法**：构建 TF 相关骨架库（如螺旋-转角-螺旋、锌指、winged helix 等），用 Rosetta Match 将 DNA 结合 motif 嫁接到骨架库，筛选高保真匹配。
   - **验证方式**：对 5-10 种不同 DNA 序列设计 TF，比较组合式筛选与 RFdiffusion 的成功率。
   - **创新状态**：unverified（方法迁移自本文，TF 骨架库构建为候选方向）

4. **名称**：Stat-vs-Energy：TF-DNA 互作中统计偏好与能量评分的系统比较
   - **来源局限/观察**：本文发现 Rosetta 能量与统计频率不相关（pi-stacking），提示物理能量函数对某些互作建模不足；TF-DNA 互作中可能同样存在此类偏差。
   - **核心假设**：TF-DNA 互作中，统计富集的互作模式（如精氨酸-鸟嘌呤）与 Rosetta 能量评分存在系统性偏差，统计偏好可指导更优的 motif 设计。
   - **初步方法**：从 PDB 中提取 TF-DNA 互作数据，比较 Rosetta 能量评分与统计频率的相关性；识别能量函数未捕捉的互作模式。
   - **验证方式**：对识别出的偏差模式，设计突变实验验证其功能重要性。
   - **创新状态**：unverified（本文在小分子上发现此现象，TF-DNA 上未验证）

5. **名称**：NMR-TF-Screen：基于化学位移扰动的 TF 设计快速筛选流程
   - **来源局限/观察**：本文使用 NMR 化学位移扰动筛选 26 个设计，无需高通量筛选；TF-DNA 设计同样需要低通量、高信息量的筛选方法。
   - **核心假设**：¹⁵N-HSQC 化学位移扰动可有效筛选 TF-DNA 结合，且能提供结合位点信息。
   - **初步方法**：将本文的 NMR 筛选流程（表达、纯化、HSQC、配体滴定）迁移到 TF-DNA 系统，优化 DNA 浓度梯度和缓冲条件。
   - **验证方式**：在已知 TF-DNA 系统上验证筛选流程的灵敏度和特异性。
   - **创新状态**：partially checked（NMR 滴定在 TF-DNA 研究中已有应用，本文的流程优化为增量贡献）