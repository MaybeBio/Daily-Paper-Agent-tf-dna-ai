## 01 基本信息
- **标题**: Impact of Persistent Endocrine-Disrupting Chemicals on Human Nuclear Receptors: Insights from In Silico and Experimental Characterization
- **作者与单位**: Ganesh, Harrish; Moran, James; Roy, Saptarshi; Mathew, Joshua; Ackah-Blay, Jehosheba; Costello, Ellen; Shan, Priya; Dakshanamurthy, Sivanesan（单位未在摘要中提供，推测为 Georgetown University Medical Center，因致谢提及 Lombardi Comprehensive Cancer Center）
- **期刊/预印本平台**: International Journal of Molecular Sciences (IJMS)
- **年份**: 2025
- **论文类型**: 研究论文（in silico + in vitro 结合）
- **领域**: 环境毒理学 / 内分泌干扰化学物（EDCs）× 核受体（NRs）× 分子对接
- **关键词**: 未提供（摘要中未列出）
- **DOI/arXiv 号**: 10.3390/ijms26072879
- **代码**: 提供了 Python 3.12.4 程序（Supplementary Code S1–S11），用于氨基酸残基相互作用分析、功能基团影响分析、SMILES 转换等
- **数据**: 16,892 个 EDCs 数据集（14,735 PFAS 来自 EPA CompTox；1,927 塑料化学品来自 Wagner et al. 数据库；209 PBDEs、58 bisphenols、38 PFAS pesticides、6 phthalates 来自 PubChem）
- **阅读日期**: 2025-04-18
- **在课题方向中的位置**: 本文属于「小分子（环境污染物）× 核受体（NRs）」的分子对接 + 体外实验验证研究。与「TF–DNA 结合机制 × AI/物理模拟」课题的关联在于：(1) 核受体（NRs）本身是配体激活型转录因子，其配体结合域（LBD）的疏水相互作用机制与 TF–DNA 结合域（DBD）的相互作用机制在「疏水互补、形状匹配、极性/氢键贡献」层面有可迁移的物理化学原理；(2) 分子对接流程（Autodock Vina 验证、grid box 设置、RMSD 验证）可直接迁移到 TF–DNA 对接或 TF–小分子共价/非共价修饰的模拟；(3) 氨基酸残基频率分析（Python 自动化）可迁移到 TF–DNA 结合界面残基偏好分析。

---

## 02 一句话总结
本文通过 Autodock Vina 分子对接模拟 16,829 个持久性 EDCs（PFAS、塑料化学品、PBDEs、双酚类、邻苯二甲酸酯、PFAS 农药）与 7 个人类核受体（PXR、CAR、PPARα/γ/δ、AR、RORγt）的结合，结合 HepG2 细胞体外 NR 激活和转录因子通路实验，发现 PFAS 和塑料化学品通过疏水氨基酸（亮氨酸、异亮氨酸、苯丙氨酸、甲硫氨酸）和极性残基（组氨酸、天冬酰胺）的互补作用优先结合大 LBD 核受体（PXR、PPARs），且 DCHP 和 DEHP 在体外实验中激活 PXR 和 PPARγ。

---

## 03 研究问题
- **具体问题**: 持久性 EDCs（PFAS、塑料化学品、PBDEs、双酚类、邻苯二甲酸酯、PFAS 农药）如何与 7 个人类核受体（PXR、CAR、PPARα、PPARγ、PPARδ、AR、RORγt）结合？哪些结构特征（碳链长度、功能基团、环状结构、疏水性）决定结合强度？
- **为什么重要**: EDCs 具有持久性、生物累积性，与癌症相关；核受体是 EDCs 的主要靶点，激活或拮抗 NRs 会导致内分泌紊乱、代谢疾病和致癌效应。但此前缺乏跨 EDC 类别、跨多个 NRs 的系统性比较。
- **现有方法不足**: 以往研究多聚焦单一 EDC 类别（如仅 PFAS 或仅双酚类）或单一受体，缺乏跨类别、跨受体的系统比较；且多数研究仅做计算模拟，缺乏体外实验验证。
- **精确的 Can 问题**: Can persistent EDCs from six chemical classes bind to seven human nuclear receptors with sufficient affinity (docking score) to warrant concern for endocrine disruption, and can specific structural features (fluorinated chain length, functional groups, cyclic structure) predict binding strength across receptors?

---

## 04 背景与发展脉络
（注：以下脉络基于本文引言和讨论，属于「仅本文框架」，未经外部系统核验）

1. **阶段一：EDC 单类别-单受体研究**（早期）
   - 代表：PFAS 激活 PPARα 的研究（引用 [16,17]）；PFAS 对 CAR 的间接激活（引用 [18,19]）
   - 优点：建立了 EDC–NR 相互作用的基本概念
   - 局限：缺乏跨类别比较，无法识别通用结合规则

2. **阶段二：多类别-多受体计算筛选**（近期）
   - 代表：Azhagiya Singam et al. 的 EDC–NR 对接分类框架（引用 [37]）
   - 优点：建立了 docking score 分类标准（强/中/弱结合）
   - 局限：多为纯计算，缺乏体外验证；未系统分析氨基酸残基偏好

3. **阶段三：计算 + 实验验证 + 结构-活性关系分析**（本文位置）
   - 本文主张：首次对 6 类 EDCs × 7 个 NRs 进行系统对接，结合 Python 自动化残基/功能基团分析，并用 HepG2 体外实验验证关键化合物（DCHP、DEHP）
   - 创新点：16,892 EDC 数据集规模；跨类别比较；残基频率与功能基团贡献的定量分析

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| EDC 研究碎片化 | 各研究聚焦单一化合物类别或单一受体，缺乏系统比较 | 数据获取困难、计算资源限制、各领域研究传统不同 | Introduction: "comprehensive studies on these persistent EDC interactions and their impacts on hNRs remain limited" |
| 计算模拟缺乏实验验证 | 多数对接研究无体外数据支持 | 实验成本高、化合物数量大 | 本文通过 HepG2 实验验证 DCHP/DEHP（Results 2.8） |
| 结合机制理解不足 | 不清楚哪些氨基酸残基和功能基团驱动结合 | 缺乏自动化残基分析工具 | 作者开发 Python 程序（Supplementary Code S7–S9） |
| 结构-活性关系不明确 | 碳链长度、功能基团对结合强度的影响缺乏定量分析 | 数据量大、手工分析不可行 | 碳链长度与 docking score 相关性分析（Results 2.4, 图 7） |
| 生物累积性无法在对接中体现 | 分子对接只反映瞬时结合，不反映体内累积效应 | 对接是热力学静态快照 | Discussion: "bioaccumulation, a factor that cannot be accounted for in molecular simulations" |

---

## 06 核心思想

### 1) 表面方法
- 大规模分子对接：16,829 EDCs（PFAS、塑料化学品、PBDEs、双酚类、邻苯二甲酸酯、PFAS 农药）对 7 个 NRs（PXR、CAR、PPARα/γ/δ、AR、RORγt）的 LBD 进行 Autodock Vina 对接
- 对接协议验证：参考配体 RMSD < 2.5 Å；docking score 与已知 IC50/EC50 比较（标准误差 0.25–1.44）
- Python 自动化分析：残基相互作用频率、功能基团分类、碳链长度计算
- 体外验证：HepG2 细胞 NR 激活实验（trans-FACTORIAL™）和转录因子通路实验（cis-FACTORIAL™）

### 2) 核心洞察
- **疏水互补是主导驱动力**：所有 EDC 类别中，强结合均依赖 LBD 中疏水残基（亮氨酸、异亮氨酸、苯丙氨酸、甲硫氨酸）的富集；极性残基（组氨酸、天冬酰胺）提供辅助稳定
- **LBD 大小决定结合谱**：大 LBD 受体（PXR、PPARs）能容纳长链 PFAS 和环状塑料化学品，小 LBD 受体（AR、CAR）结合受限
- **功能基团调节而非决定**：磺酸、尿素、氨基甲酸酯等极性基团增强特定受体结合，但疏水骨架是必要条件
- **碳链长度存在最优区间**：PFAS 碳链长度与结合强度呈非线性关系，过长碳链因构象熵损失反而降低结合

### 3) 可能的普适教训 [Analysis]
- 对 TF–DNA 互作研究：**残基频率分析**（本文 Python 自动化方法）可直接迁移到 TF–DNA 结合界面——统计 DBD 中与 DNA 接触的残基类型偏好，识别「热点残基」
- **LBD 大小与配体尺寸匹配**的概念可类比为「DBD 构象柔性 vs DNA 结合位点形状」——TF 的 DBD 柔性区域可能决定其能结合的 DNA 基序范围
- **功能基团调节而非决定**的结论提示：TF–DNA 互作中，DNA 碱基的化学修饰（如甲基化）可能类似「功能基团」，调节而非决定结合特异性

---

## 07 方法总览
- **输入**：
  - 受体结构：7 个 NRs 的 LBD 晶体结构（PDB），经 ChimeraX 1.8 清理（去水、去非标准残基、去配体）
  - 配体结构：16,829 EDCs 的 SMILES 表示（PFAS 来自 EPA CompTox；塑料化学品来自 Wagner et al. 数据库；其余来自 PubChem）
- **处理流程**：
  1. SMILES → 3D 结构（OpenBabel 2.3.3，GAFF 力场能量最小化）
  2. Autodock 4.2 Tools 准备受体（加氢、Kollman 电荷、pdbqt 格式）
  3. Autodock Vina 对接（grid box 覆盖 LBD 正构位点）
  4. Python 脚本分析：残基相互作用频率（5 Å 截断）、功能基团分类、碳链长度计算
  5. 分类标准：docking score 与参考配体均值比较，分为强/中/弱结合
- **输出**：每个 EDC–NR 对的 docking score、相互作用残基列表、功能基团贡献、碳链长度-结合强度关系
- **反馈回路**：对接结果指导体外实验选择（DCHP、DEHP 因高结合力和生物累积性被选中）
- **体外验证**：HepG2 细胞 trans-FACTORIAL™（50 个 NRs）和 cis-FACTORIAL™（52 个 TFs），10 mM 处理 16 小时

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 受体准备（ChimeraX + Autodock Tools） | 清理晶体结构、加氢、分配电荷 | 确保对接网格准确覆盖 LBD | 输入：PDB 结构；输出：pdbqt 格式受体 | RMSD 验证 < 2.5 Å（Results 2.1） | 预期：grid box 偏移导致 docking score 系统性偏差 [预期效应] |
| 配体准备（OpenBabel + GAFF） | SMILES → 3D 结构、能量最小化 | 确保配体构象合理 | 输入：SMILES；输出：pdbqt 格式配体 | 未提供单独验证 | 预期：构象生成错误导致 docking score 低估 [预期效应] |
| Autodock Vina 对接 | 预测结合构象和亲和力 | 核心计算模块 | 输入：受体+配体 pdbqt；输出：docking score + 构象 | 与 IC50/EC50 比较，标准误差 0.25–1.44（Results 2.1） | 实测：移除后无计算预测能力 |
| 残基相互作用频率分析（Python） | 统计 5 Å 内接触残基 | 识别结合热点残基 | 输入：对接构象；输出：残基频率表 | 图 5A–G 显示疏水残基主导 | 预期：无法识别结合机制 [预期效应] |
| 功能基团分类分析 | 按官能团分组比较 docking score | 识别功能基团对结合的贡献 | 输入：SMILES + docking score；输出：功能基团-亲和力表 | 表 3 显示磺酸、尿素强结合 | 预期：无法解释化学多样性 [预期效应] |
| 碳链长度计算 | 最长氟化碳链长度 | 验证链长-亲和力关系 | 输入：SMILES；输出：碳链长度 | 图 7 显示 R² = 0.74–0.91 | 预期：无法解释链长效应 [预期效应] |
| 体外 NR 激活实验（trans-FACTORIAL™） | 验证 DCHP/DEHP 对 50 个 NRs 的激活 | 计算预测的实验验证 | 输入：化合物处理；输出：fold induction | 图 8 显示 PXR 和 PPARγ 强激活 | 实测：移除后无法确认功能效应 |
| 体外 TF 通路实验（cis-FACTORIAL™） | 验证 DCHP/DEHP 对 52 个 TFs 的调控 | 评估下游通路影响 | 输入：化合物处理；输出：TF 活性变化 | 图 8B 显示 VDRE 和 PXR 正调控 | 实测：移除后无法评估下游效应 |

---

## 09 关键公式符号
本文未提供明确的数学公式。核心定量关系为：

- **Docking score 分类标准**（作者采用 Azhagiya Singam et al. 的方法）：
  - 强结合：docking score < 参考配体均值
  - 中等结合：docking score 在参考配体均值 ±10% 范围内
  - 弱结合：docking score > 参考配体均值 +10%
  
- **碳链长度-结合强度相关性**：R² 值（PPARα: 0.838, PPARδ: 0.908, PXR: 0.867, PPARγ: 0.74）用于量化线性相关程度

- **RMSD 验证阈值**：< 2.5 Å 视为对接协议有效

---

## 10 实验设计与证据链

**数据集与规模**：
- 配体：16,829 EDCs（14,591 PFAS + 1,927 塑料化学品 + 209 PBDEs + 58 双酚类 + 38 PFAS 农药 + 6 邻苯二甲酸酯）
- 受体：7 个人类 NRs（PXR、CAR、PPARα、PPARγ、PPARδ、AR、RORγt）
- 体外实验：HepG2 细胞，DCHP 和 DEHP（10 mM，16 h）

**指标**：
- 计算：docking score（kcal/mol）、RMSD（Å）、残基接触频率、LogP、碳链长度
- 实验：fold induction（NR 激活倍数）

**基线/参考**：
- 参考配体：各 NR 的已知内源/合成配体（如 PXR 的 SJB7、CAR 的 ATE、PPARα 的棕榈酸等）
- 分类阈值：参考配体 docking score 均值

**验证协议**：
- 对接协议验证：参考配体重新对接，RMSD < 2.5 Å
- 计算-实验交叉验证：DCHP/DEHP 的 docking score 与体外激活结果比较

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-----------------|------|
| 对接协议验证 | Autodock Vina 能准确预测结合构象 | 7 个 NRs 的参考配体重新对接 vs 共晶结构 | RMSD 0.353–2.416 Å，均 < 2.5 Å | 对接协议可靠 | 不能证明对所有 EDCs 均准确 | Results 2.1, 图 1 |
| PFAS 结合谱分析 | PFAS 优先结合特定 NRs | 14,591 PFAS vs 7 NRs | PXR 和 PPARγ 强结合比例最高 | PFAS 主要靶向 PXR/PPARs | 不能确定功能激活 vs 拮抗 | Results 2.2, 表 1 |
| 碳链长度分析 | 长链 PFAS 结合更强 | 碳链长度 vs docking score | R² = 0.74–0.91（PPARs, PXR） | 链长是重要预测因子 | 非线性关系，非严格单调 | Results 2.4, 图 7 |
| 功能基团分析 | 磺酸/尿素基团增强结合 | 含/不含功能基团的 PFAS 比较 | 磺酸、尿素平均 docking score 更负 | 极性基团贡献结合 | 样本量不均，需谨慎 | Results 2.6, 表 3 |
| 残基频率分析 | 疏水残基主导结合 | 各 EDC 类别的接触残基频率 | 亮氨酸、异亮氨酸、苯丙氨酸频率最高 | 疏水互补是通用机制 | 不能区分特异性 vs 非特异性结合 | Results 2.3, 图 5 |
| DCHP/DEHP 体外 NR 激活 | 计算预测的强结合转化为功能激活 | 50 个 NRs 的 trans-FACTORIAL™ | PXR 和 PPARγ 强激活 | DCHP/DEHP 是 PXR/PPARγ 激动剂 | 未测试所有 7 个 NRs 的激活 | Results 2.8, 图 8 |
| DCHP/DEHP 体外 TF 通路 | 激活 NRs 导致下游 TF 变化 | 52 个 TFs 的 cis-FACTORIAL™ | VDRE 和 PXR 正调控 | 影响维生素 D 信号和药物代谢 | 未做剂量-反应曲线 | Results 2.8, 图 8 |

---

## 11 结论正确解读
- **任务范围**: 本文只覆盖了 7 个 NRs 的 LBD 正构位点对接，未涉及 DBD、未涉及 DNA 共结合、未涉及共调节因子招募。结论仅适用于「配体–LBD 结合亲和力」层面。
- **oracle/真值输入**: 体外实验使用了 HepG2 细胞系，该细胞系内源表达部分 NRs，但并非所有 7 个 NRs 都有功能验证。DCHP/DEHP 的激活实验覆盖了 50 个 NRs，但未逐一对应 7 个对接靶点。
- **端到端状态**: 计算（对接）→ 体外（激活）的流程是「部分端到端」——只有 DCHP/DEHP 两个化合物走完了全流程，其余 16,827 个 EDCs 仅有计算预测。
- **算力成本**: 未报告具体算力消耗。大规模对接（16,829 × 7 ≈ 118,000 次对接）在标准工作站上可行，但未提供时间数据。
- **历史数据依赖**: 依赖 EPA CompTox 和 Wagner et al. 数据库的化合物清单，这些数据库本身可能不完整或有偏。
- **模型依赖**: 结果依赖 Autodock Vina 的评分函数精度；Vina 对疏水相互作用的描述较好，但对极化效应、水介导氢键的描述有限。
- **最难情形**: 对 AR 的结合预测最弱（AR 的 LBD 较小且刚性），对长链 PFAS 的构象采样可能不充分。
- **群体/领域边界**: 结论仅适用于人类 NRs，不适用于其他物种；仅适用于所列 6 类 EDCs，不涵盖所有环境污染物。
- **不确定性**: docking score 是热力学近似，不反映动力学稳定性；体外实验仅测试了单一浓度（10 mM）和单一时间点（16 h）。

**有边界的复述**: 在 Autodock Vina 评分函数和 HepG2 细胞实验条件下，持久性 EDCs 中 PFAS 和塑料化学品对 PXR、PPARγ 等大 LBD 核受体表现出强结合预测，且 DCHP/DEHP 在体外确实激活 PXR 和 PPARγ；但该结论不能外推到其他 NRs、其他 EDCs 类别或其他实验条件。

---

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 缺乏全蛋白柔性 | 仅考虑 LBD 局部柔性，未进行全蛋白 MD 模拟 | 未来应纳入 MM-GBSA 或 MM-PBSA 模拟 | Conclusions: "future work should incorporate the full flexibility of top EDC-binding complexes, which could be achieved by incorporating MM-GBSA or MM-PBSA simulations" |
| 缺乏特异性结合实验 | 未做 SPR/ITC 等定量结合实验 | 需要更精确的结合亲和力测量 | Conclusions: "it requires a specific binding assay" |
| 体外验证范围有限 | 仅验证了 DCHP 和 DEHP 两个化合物 | 应扩展至其他强结合 EDCs | Conclusions: "additional in vitro binding studies should target PFAS and plastic-associated chemicals" |
| 未测试变构位点 | 仅关注正构位点 | 变构位点可能作为次级激活域 | Conclusions: "Allosteric sites have been studied for NRs like VDR, PPARγ, and PXR, but only with PFAS. Future research should explore allosteric sites in other NRs" |
| 生物累积性未纳入 | 对接无法反映体内累积效应 | 需要结合毒代动力学模型 | Results 2.8: "bioaccumulation, a factor that cannot be accounted for in molecular simulations" |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 对接分类标准依赖参考配体均值 | 不同 NRs 的参考配体亲和力范围差异大，均值分类可能不公平 | 跨受体比较时可能产生系统性偏差 | 使用绝对 docking score 阈值或归一化处理 | Results 2.2 分类方法 |
| 残基频率分析仅基于 top 15 binders | 小样本可能不具代表性，且未区分特异性 vs 非特异性接触 | 可能高估某些残基的重要性 | 扩大至 top 50 或全部结合子，并设置随机对照 | Results 2.3, 图 5 |
| 碳链长度-亲和力相关性基于平均 docking score | 平均值掩盖了同一链长内的巨大变异 | 可能过度简化结构-活性关系 | 展示散点图分布，报告置信区间 | Results 2.4, 图 7 |
| 体外实验仅测试 10 mM 单一浓度 | 未做剂量-反应曲线，无法判断生理相关性 | 高浓度可能产生非特异性效应 | 补充多浓度梯度实验 | Results 2.8 方法 |
| HepG2 细胞是肝癌细胞系 | 内源 NR 表达谱与正常组织不同 | 可能影响 NR 激活结果的普适性 | 使用原代细胞或多细胞系验证 | Results 2.8 方法 |
| 未报告对接的构象聚类分析 | 单一最优构象可能不代表主要结合模式 | 可能遗漏重要的替代结合模式 | 进行构象聚类，报告代表性构象 | Methods 3.8 |
| 功能基团分析未控制分子量/链长混杂 | 含磺酸基团的 PFAS 可能同时更长 | 功能基团效应可能与链长效应混淆 | 多元回归控制混杂变量 | Results 2.6, 表 3 |

---

## 14 个人收获与启发
- **方法可迁移**: 本文的「大规模对接 + Python 自动化残基频率分析」流程可直接迁移到 TF–DNA 互作研究——对 TF 突变体库或 TF 家族成员进行 DNA 基序对接，统计接触残基频率，识别 DNA 结合热点残基。
- **分类框架可借鉴**: 「强/中/弱结合」的三分类框架（基于参考配体均值）可用于 TF–DNA 结合强度的标准化比较，尤其适合跨 TF 家族的系统比较。
- **计算-实验闭环设计**: 本文「计算筛选 → 选择代表性化合物 → 体外验证」的流程是计算驱动实验的典范。在 TF–DNA 研究中，可先对 TF 突变体进行 DNA 对接筛选，再选择 top 突变体做 EMSA/SELEX 验证。
- **疏水互补的普适性**: 本文发现疏水残基主导 EDC–NR 结合，这与 TF–DNA 相互作用中疏水残基在 DBD 折叠核心中的作用类似，但 TF–DNA 特异性主要由极性/氢键网络决定——这一差异提示：小分子–蛋白互作与蛋白–核酸互作的「特异性来源」不同。
- **LBD 大小与配体尺寸匹配**: 这一概念可类比为「DBD 构象柔性决定 DNA 基序识别范围」——柔性 DBD 可能识别更多变异的基序，刚性 DBD 则更特异。
- **功能基团调节而非决定**: 对 TF–DNA 研究，DNA 甲基化/羟甲基化等修饰可能类似「功能基团」，调节而非决定 TF 结合——这为研究表观遗传修饰对 TF 结合的影响提供了框架。

---

## 15 与已有知识连接
- **Autodock Vina 在蛋白-配体对接中的验证**: 本文 RMSD < 2.5 Å 的验证标准与 Trott & Olson (2010) 的原始验证一致，说明 Vina 在 NR-LBD 体系中的可靠性。
- **NR 配体混杂性**: 本文发现 EDCs 可结合多个 NRs，这与 McGovern & Shoichet 关于「promiscuous binding」的讨论相关——但本文的疏水互补机制提示这可能是「合理混杂」而非「非特异性」。
- **PPARγ 作为环境传感器**: 本文 PPARγ 的高结合率与 Grün & Blumberg 的「obesogen」假说一致，支持 PPARγ 是环境化学物质的关键靶点。
- **与 TF–DNA 对接的差异**: 蛋白-DNA 对接（如 HADDOCK、ZDOCK）与蛋白-小分子对接（Vina）的评分函数不同——DNA 的带电磷酸骨架和碱基堆积需要静电和 π-π 相互作用的显式处理，而本文的疏水主导机制不完全适用于 TF–DNA。
- **可迁移的残基频率方法**: 本文的残基频率分析类似于 DNA 结合蛋白中的「consensus motif」分析——可类比为「结合界面残基偏好」的定量描述。
- **体外验证的局限性**: 本文的 HepG2 实验与 Attagene 平台（引用 [83-87]）是 NR 活性检测的标准方法，但仅覆盖转录激活，未覆盖翻译后修饰等调控层面。

---

## 16 研究想法

### 候选 1: TF–DNA 结合界面的「疏水热点」系统分析
- **来源局限/观察**: 本文发现 EDCs 与 NR 的结合由疏水残基主导，但 TF–DNA 互作研究多聚焦极性/氢键网络，疏水贡献常被忽视。
- **核心假设**: TF–DNA 结合界面中存在保守的「疏水热点」残基，其突变对结合亲和力的影响与极性残基同等重要。
- **初步方法**: 收集 TF–DNA 共晶结构（PDB），计算界面残基的疏水接触面积（如 Shrake-Rupley 算法），与已知突变数据（如 ProTherm 或文献）关联。
- **验证方式**: 对 top 疏水热点残基做丙氨酸扫描突变 + EMSA 验证。
- **创新状态**: unverified

### 候选 2: 基于 EDC 结合模式的 NR 交叉反应性预测模型
- **来源局限/观察**: 本文仅做了 7 个 NRs 的对接，但人类有 48 个 NRs，EDC 可能结合未测试的 NRs。
- **核心假设**: EDC 的 docking score 谱（7 个 NRs 的向量）可作为特征，预测其对其他 NRs 的结合。
- **初步方法**: 用本文 7-NR docking score 作为特征向量，训练分类器（如随机森林）预测 EDC 是否激活/拮抗其他 NRs（使用 ToxCast 数据作为标签）。
- **验证方式**: 留一法交叉验证 + 对预测的 top 候选做体外实验。
- **创新状态**: partially checked（ToxCast 已有部分数据，但本文特征尚未被用于此目的）

### 候选 3: 将「功能基团调节」概念迁移到 TF–DNA 修饰识别
- **来源局限/观察**: 本文发现功能基团（磺酸、尿素）调节而非决定 NR 结合；类似地，DNA 修饰（甲基化、氧化）可能调节而非决定 TF 结合。
- **核心假设**: TF 对修饰 DNA 的结合亲和力变化可由修饰基团的化学性质（极性、体积、氢键供体/受体）预测。
- **初步方法**: 对已知 TF（如 p53、SP1）的 DNA 结合位点进行系统修饰（5mC、5hmC、8-oxoG），用分子对接或 MD 模拟预测结合变化，与文献数据比较。
- **验证方式**: 对预测变化最大的修饰做表面等离子共振（SPR）或荧光各向异性实验。
- **创新状态**: unverified

### 候选 4: 大 LBD vs 小 LBD 的「结合谱宽度」与 TF 的「基序谱宽度」类比
- **来源局限/观察**: 本文发现大 LBD 受体（PXR、PPARs）能容纳更多样化的配体，小 LBD 受体（AR）则受限。
- **核心假设**: TF 的 DBD 结构域大小/柔性与其识别的 DNA 基序多样性呈正相关。
- **初步方法**: 收集 TF 家族成员的 DBD 结构（体积、柔性指标如 B-factor），与其已知的 DNA 基序矩阵（JASPAR）的熵（信息含量）做相关性分析。
- **验证方式**: 对相关性最强的 TF 做突变实验（增大/减小 DBD 柔性），检测基序谱变化。
- **创新状态**: unverified

### 候选 5: 结合本文数据构建 EDC–NR 结合数据库
- **来源局限/观察**: 本文产生了 16,829 × 7 的 docking score 矩阵，但未公开为可查询数据库。
- **核心假设**: 该矩阵可作为训练数据，用于预测新 EDC 的 NR 结合谱。
- **初步方法**: 将 docking score 矩阵与 EDC 的分子描述符（RDKit 计算）关联，训练图神经网络或梯度提升模型。
- **验证方式**: 对模型预测的 top 新 EDC 做体外实验验证。
- **创新状态**: unverified（数据已产生，但未用于建模）