## 01 基本信息
- **标题**: An in silico to in vivo approach identifies retinoid-X receptor activating tert-butylphenols used in food contact materials
- **作者与单位**: Mengeling, Brenda J; Ettayapuram Ramaprasad, Azhagiya Singam; Smith, Martyn T; Turkieh, Dania; Kleinstreuer, Nicole C; Mansouri, Kamel; Durkin, Kathleen A; La Merrill, Michele A; Furlow, J David（单位未在摘要中提供）
- **期刊/预印本平台**: Scientific Reports
- **年份**: 2025-07-19
- **论文类型**: 研究论文（in silico 筛选 + in vivo 验证）
- **领域**: 计算毒理学 / 核受体（RXR）内分泌干扰 / 食品接触材料安全性
- **关键词**: RXR（retinoid-X receptor）、tert-butylphenols、food contact materials、molecular docking、machine learning、MM-PBSA、Xenopus laevis、thyroid hormone signaling
- **DOI/arXiv 号**: 10.1038/s41598-025-09244-z
- **代码**: 未提供
- **数据**: 57,277 种化学品的筛选结果、MM-PBSA 能量值、Tox21 HDR 数据（通过 ICE 数据库获取）、Xenopus 实验数据（补充材料）
- **阅读日期**: 2025-07-20
- **在该课题方向中的位置**: 本文属于「蛋白质-配体（小分子）互作 × 机器学习 + 分子对接 + MD/MM-PBSA」的典型计算-实验联合流程，但对象是核受体 RXR 与其小分子配体（而非 TF–DNA 直接结合）。对本课题（TF–DNA 互作 × AI/物理模拟）的可迁移点在于：① 大规模虚拟筛选的流程设计（ML 初筛 → 对接 → MM-PBSA 精筛 → 实验验证）；② 核受体异源二聚化（RXR 作为 TR 的 partner）对 DNA 结合效率的调控——这是 TF–DNA 互作中「辅助因子/二聚化伴侣」的经典案例；③ 体内报告系统（转基因 Xenopus）用于验证配体对 TF 活性的功能影响。

## 02 一句话总结
本文通过机器学习（NR-Toxpred）从 57,277 种化学品中预测出 104 种 RXR 配体，经分子对接和 MM-PBSA 能量计算筛选出 6 种 tert-butylphenol 类食品接触化学品，并在转基因 Xenopus laevis 蝌蚪体内验证其中 3 种（4E-DTBP、4sB-DTBP、TTBP）能在纳摩尔至微摩尔浓度下增强 T3 诱导的 TR-RXR 报告基因活性及形态学变化，表明这些化合物是 RXR 激动剂，可能通过干扰 RXR 信号产生内分泌干扰效应。

## 03 研究问题
- **具体问题**: 食品接触材料中广泛使用的 tert-butylphenol 类化合物是否能够结合并激活核受体 RXR，从而干扰甲状腺激素（TH）信号通路？
- **为什么重要**: RXR 是三分之一的核受体（NR）的异源二聚化伴侣，RXR 信号被环境化学物干扰可能影响代谢、发育和免疫功能。食品接触材料中的化合物可能迁移进入食物链，造成人类暴露。
- **现有方法不足**: 传统毒理学测试通量低、成本高；已有的计算预测模型（如 CoMPARA/CERAPP）主要针对雌激素/雄激素受体，对 RXR 的覆盖不足；且缺乏从计算预测到体内功能验证的完整链条。
- **精确研究问题**: Can machine learning combined with molecular docking and MM-PBSA free energy calculations reliably identify environmental chemicals (tert-butylphenols) that activate RXR and potentiate thyroid hormone signaling in vivo?

## 04 背景与发展脉络
（注：以下脉络基于本文框架，部分经外部核验）

1. **核受体超家族与 RXR 的生物学**（经外部核验）: RXR 是 NR 超家族中关键的异源二聚化伴侣，与 TR、LXR、PPAR 等形成二聚体以有效结合 DNA。经典观点认为 TR-RXR 是"非允许性"异源二聚体，即 RXR 激动剂单独不能激活转录，但本文及作者前期工作表明这一观点并非绝对。
2. **计算毒理学的发展**（经外部核验）: 从 QSAR 模型（CERAPP, 2016）到集成模型（CoMPARA, 2020），再到本文使用的 NR-Toxpred（2023），机器学习方法逐步提高了核受体活性预测的准确性和覆盖率。
3. **分子对接与自由能计算在核受体-配体研究中的应用**（经外部核验）: 从刚性对接（Glide XP）到考虑蛋白质柔性的 ensemble docking，再到 MM-PBSA/GBSA 结合自由能计算，计算精度逐步提升。
4. **体内验证模型**（本文框架）: 作者前期建立的转基因 Xenopus laevis 早熟变态模型，可定量检测 TH 信号通路的激活/抑制，为计算预测提供体内功能验证。
5. **本文主张的位置**: 首次将 ML 预测 → 对接 → MM-PBSA → 体内验证的完整流程应用于 RXR 配体筛选，并聚焦于食品接触材料中的 tert-butylphenols。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 环境化学品数量庞大，传统毒理学测试无法覆盖 | 人类暴露于数万种化学品，逐一进行体内/体外测试不现实 | 测试成本高、周期长、动物伦理问题 | Introduction: "future hazard identification... will likely require integration of data from diverse sources" |
| 现有计算模型对 RXR 的预测覆盖不足 | CoMPARA/CERAPP 主要针对 ER/AR 等受体，RXR 预测模型缺乏 | RXR 配体结构多样性高，训练数据有限 | Introduction: 使用 NR-Toxpred 作为改进工具 |
| 计算预测缺乏体内功能验证 | 仅靠对接分数或 ML 概率无法确定化合物是否真正干扰信号通路 | 计算预测存在假阳性，需要生物学验证 | 本文核心贡献：in silico → in vivo 完整流程 |
| 构效关系不明确 | 同为 tert-butylphenol 类化合物，活性差异大（如 4E-DTBP 活性强于 BHT） | 取代基大小、位置影响配体-受体互补性 | Results: 图 2-4，C4 位取代基大小与活性正相关 |
| 非允许性异源二聚体的传统观点可能低估 RXR 配体的作用 | TR-RXR 被认为不受 RXR 配体调控，但实验显示 RXR 激动剂可增强 T3 信号 | 细胞/组织特异性共调节因子比例可能影响异源二聚体的允许性 | Discussion: 引用文献 28,54,55 |

## 06 核心思想
1. **表面方法**: 一个三阶段筛选流程——① NR-Toxpred 机器学习模型从 57,277 种化学品中预测 RXR 活性；② 对预测阳性的 104 种化合物进行 ensemble molecular docking（Glide XP）和 MM-PBSA 结合自由能计算；③ 对选出的 6 种 tert-butylphenols 进行 Tox21 体外报告基因数据分析和转基因 Xenopus 体内验证。

2. **核心洞察**: ① 机器学习模型可以高效缩小候选化合物空间（57,277 → 104），但需要 docking 和 MM-PBSA 提供结构层面的支持；② tert-butylphenol 类化合物的 RXR 激动活性与 C4 位取代基大小呈正相关——乙基是活性所需的最小基团，丁基（TTBP、4sB-DTBP）活性最强；③ 体内验证表明这些化合物在纳摩尔至微摩尔浓度即可增强 T3 信号，提示实际暴露水平可能具有生物学意义。

3. **可能的普适教训** [Analysis]: ① 计算毒理学的"漏斗式"筛选策略（ML → docking → 自由能 → 实验）是可行的，但每一层都需要明确的阈值和验证标准；② 配体-受体结合的"体积互补性"（bulky group filling hydrophobic pocket）是预测活性的关键结构特征，这一原则可迁移到 TF–DNA 互作中的"界面互补性"分析；③ 体内报告系统是验证计算预测的"金标准"，但需要选择发育阶段合适、背景干净的模型（如本文的 pre-metamorphic Xenopus）。

## 07 方法总览
- **输入**: 57,277 种化学品的 SMILES 结构（来自 CoMPARA 扩展列表 + 加州 OEHHA + Food Contact Chemicals Database）
- **输出**: 6 种 tert-butylphenols 的 RXR 激动活性判定（3 种阳性：4E-DTBP、4sB-DTBP、TTBP；3 种阴性/弱阳性：BHT、2,6-DTBP、E703）
- **模块**:
  1. **NR-Toxpred ML 预测**: Morgan fingerprints + SuperLearner 算法，输出 RXR 活性概率
  2. **Ensemble molecular docking**: 10 个 RXR 晶体结构（PDB），Glide XP 算法，输出 docking score
  3. **MM-PBSA 自由能计算**: AMBER 18，AM1-BCC 电荷，FF14SB 力场，TIP3P 水盒子，单点计算
  4. **MD 模拟**: 100 ns × 3 次重复，NPT 系综，300 K，PME 静电
  5. **Tox21 体外数据**: 从 ICE 数据库获取 RXR 报告基因数据
  6. **Xenopus 体内验证**: 转基因 TH 报告基因蝌蚪 + 形态学测量
- **训练**: NR-Toxpred 模型此前已训练（引用文献 18），本文未重新训练
- **反馈回路**: 体内结果与计算预测的一致性验证（3/5 阳性预测得到体内确认，1 个阴性预测得到确认）
- **假设**: ① ML 预测的活性化合物在结构上能对接入 RXR LBD；② MM-PBSA 能量与实验活性相关；③ Xenopus 模型能反映人类 RXR 信号

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| NR-Toxpred ML 筛选 | 从 57,277 种化合物中预测 RXR 活性 | 缩小候选空间，降低计算成本 | 输入: SMILES; 输出: 104 种预测阳性 | Results: "predicted 109 chemicals to be active"（其中 104 种在适用域内） | 移除后需对全部 57,277 种化合物进行对接，计算成本极高 [预期] |
| Ensemble molecular docking | 确定配体在 RXR LBD 中的结合构象 | 提供结构层面的结合证据 | 输入: 104 种化合物 + 10 个 RXR 结构; 输出: docking score（-16.44 至 -4.18） | Results: 图 1a | 移除后无法获得结合构象，MM-PBSA 无法计算 [预期] |
| MM-PBSA 自由能计算 | 评估结合亲和力 | 比 docking score 更准确的能量估计 | 输入: docked complex; 输出: ΔGbind（-77.15 至 -32.03） | Results: 图 1b，表 2 | 移除后仅靠 docking score 可能产生更多假阳性 [预期] |
| MD 模拟（100 ns × 3） | 评估复合物稳定性 | 捕捉动态相互作用 | 输入: docked complex; 输出: 能量组分（ΔEvdW, ΔEelec 等） | Results: 表 2，图 5 | 移除后无法评估结合稳定性 [预期] |
| Tox21 体外数据 | 验证 ML 预测的体外活性 | 提供独立于计算的实验证据 | 输入: 6 种化合物; 输出: AC-50/ACC 值 | Results: 图 2b,c | 移除后体内实验缺乏体外参考 [预期] |
| Xenopus 体内验证 | 验证功能活性 | 提供整体动物水平的证据 | 输入: 6 种化合物 + T3; 输出: 报告基因活性 + 形态学数据 | Results: 图 3, 4 | 移除后无法确认计算预测的生物学意义 [预期] |

## 09 关键公式符号
本文未提供明确的数学公式。MM-PBSA 方法的标准公式（来自文献，非本文原创）：
- ΔG_bind = ΔE_vdW + ΔE_elec + ΔG_PB + ΔG_SA − TΔS
  - ΔE_vdW: van der Waals 相互作用能
  - ΔE_elec: 静电相互作用能
  - ΔG_PB: Poisson-Boltzmann 溶剂化能
  - ΔG_SA: 非极性溶剂化能（基于溶剂可及表面积）
  - −TΔS: 熵贡献（本文未计算，表 2 中未列出）

## 10 实验设计与证据链
- **数据集/群体**: 
  - 计算筛选: 57,277 种化学品（CoMPARA 扩展 + OEHCA + FCCDB）
  - 体外: Tox21 数据库中 6 种 tert-butylphenols 的 RXR 报告基因数据
  - 体内: 转基因 Xenopus laevis 蝌蚪（1 周龄，NF 48 期）
- **规模**: 104 种 ML 预测阳性 → 102 种完成对接和 MM-PBSA → 6 种进入实验验证
- **指标**: docking score, ΔG_bind, AC-50, ACC, 报告基因活性倍数变化, 形态学参数（头面积、脑宽、下颌角）
- **基线/对照**: 已知 RXR 激动剂 bexarotene（阳性对照）；T3-only 处理（阴性对照）；2,6-DTBP（ML 预测阴性对照）
- **预算/资源**: 未提供
- **骨干/仪器**: 未提供（计算使用 Schrodinger Suite、AMBER 18；实验使用 Xenopus 蝌蚪）
- **评测协议**: 统计显著性用 ***p<0.001, ****p<0.0001（具体检验方法在 Methods 中，但摘要未详述）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-------------------|------|
| ML 预测 + 对接 + MM-PBSA | 57,277 种化学品中可预测出 RXR 活性化合物 | 104 种预测阳性，docking score 范围 -16.44 至 -4.18 | 预测出 104 种潜在 RXR 配体 | ML + 对接可有效缩小候选空间 | 计算预测不等于实验活性 | Results 图 1 |
| Tox21 体外报告基因 | 6 种 tert-butylphenols 是否激活 RXR | 与已知激动剂 bexarotene 比较 | 4sB-DTBP 和 TTBP 有纳摩尔级 AC-50 | 部分 tert-butylphenols 是 RXR 激动剂 | 体外活性不等于体内效应 | Results 图 2 |
| Xenopus 体内报告基因 | tert-butylphenols 是否增强 T3 信号 | 25 nM T3 ± 化合物 | 4E-DTBP、4sB-DTBP、TTBP 增强报告基因活性 | 这些化合物在体内增强 TR-RXR 信号 | 未测试是否影响内源基因表达 | Results 图 3 |
| Xenopus 形态学 | 化合物是否增强 T3 诱导的形态变化 | 10 nM T3 ± 化合物，5 天 | 3 种活性化合物增强头面积减小、脑宽增加、下颌角变化 | 功能水平验证 RXR 激动活性 | 未评估长期健康影响 | Results 图 4 |
| MD 模拟 + MM-PBSA | 活性化合物的结合模式 | 6 种化合物与 RXRα 复合物 | 活性化合物有更有利的 ΔG_bind 和 ΔE_vdW | 体积大的 C4 取代基增强疏水相互作用 | 模拟不能完全代表体内动态 | Results 表 2, 图 5 |

## 11 结论正确解读
- **任务范围**: 本文仅针对 RXR 配体识别，未涉及 RXR 与 DNA 的直接结合或 RXR-TR 异源二聚体与 DNA 的共结合。
- **Oracle/真值输入**: 计算阶段使用已知 RXR 配体结构（PDB）作为对接模板；实验阶段使用转基因报告基因作为功能读出。
- **端到端状态**: 是端到端的（in silico → in vitro → in vivo），但 in vivo 仅验证了 6 种化合物中的 3 种阳性，未验证全部预测。
- **算力成本**: 未提供。
- **历史数据依赖**: ML 模型依赖历史训练数据（NR-Toxpred），其覆盖范围可能影响预测准确性。
- **模型依赖**: 依赖 Glide XP 对接和 MM-PBSA 近似，这些方法有已知的局限性（如熵贡献未计算）。
- **最难情形**: 对弱结合或诱导契合型配体的预测可能不准确；对 RXRβ 与 RXRα 的选择性未充分探讨。
- **群体/领域边界**: 结论仅适用于 tert-butylphenol 类化合物和 RXR 信号通路，不能外推到其他核受体或其他化学类别。
- **不确定性**: MM-PBSA 的 ΔG_bind 标准差较大（表 2 中 ±3-8 kcal/mol），部分化合物的预测置信度有限。

**有边界的复述**: 在 57,277 种化学品中，NR-Toxpred ML 模型预测 104 种为 RXR 配体；其中 6 种 tert-butylphenols 经 docking 和 MM-PBSA 筛选后，3 种（4E-DTBP、4sB-DTBP、TTBP）在转基因 Xenopus 蝌蚪体内证实能增强 T3 诱导的 TR-RXR 信号，且活性与 C4 位取代基大小正相关。该结论仅适用于所测试的化合物和模型系统。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 计算模型基于人 RXRα 结构 | 未考虑 RXRβ/γ 亚型差异 | 未明确提及 | Methods: "human RXRα" |
| 未进行共结晶验证 | 结合模式基于 docking 和 MD 模拟 | 作者建议通过共结晶研究确定 definitive binding mode | Discussion: "would best be determined through co-crystallization studies" |
| 未评估这些化合物的实际人体暴露水平 | 虽在食品接触材料中检测到，但未测量人体内浓度 | 未明确提及 | Discussion: 提到检测到 dust、sludge 等环境样本 |
| 未测试这些化合物对其他 RXR 异源二聚体伙伴（如 PPAR、LXR）的影响 | 仅关注 TR-RXR 信号 | 未明确提及 | Discussion: 引用文献 22 讨论 2,4-DTBP 的 PPAR 效应 |
| 体内实验仅使用单一物种（Xenopus） | 未在哺乳动物模型中验证 | 未明确提及 | Methods: Xenopus laevis |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| ML 预测的 104 种化合物中仅测试了 6 种 | 可能存在大量假阳性或假阴性 | 无法评估 ML 模型的整体预测精度 | 对更多预测阳性/阴性化合物进行实验验证 | Results: 仅 6 种进入实验 |
| MM-PBSA 的 ΔG_bind 标准差较大（±3-8 kcal/mol） | 部分化合物的能量差异可能不显著 | 影响计算筛选的可靠性 | 使用更精确的自由能方法（如 FEP）或增加采样 | 表 2 |
| 体内实验浓度（30-1000 nM）可能远高于实际人体暴露水平 | 环境相关浓度下的效应未知 | 影响风险评估的结论 | 进行环境相关浓度的剂量-反应研究 | Results: 图 3-4 |
| 未检测这些化合物是否影响 RXR 的 DNA 结合能力 | 仅检测了转录激活，未区分 DNA 结合 vs 共调节因子招募 | 对 TF-DNA 互作机制的理解不完整 | 使用 EMSA 或 ChIP 检测 RXR-TR 与 DNA 的结合 | Discussion: 引用文献 28,54,55 |
| 未测试这些化合物是否影响 RXR 与 DNA 的结合选择性 | 可能改变 RXR 对特定 DNA 响应元件的偏好 | 影响对下游基因调控的理解 | 进行基因组范围的结合位点分析 | 未提供 |
| 计算筛选仅使用人 RXRα 结构 | 其他物种或亚型的结合可能不同 | 影响跨物种外推 | 使用多物种/多亚型结构进行对接 | Methods: "human RXRα" |

## 14 学到什么
**Agent 提炼的知识候选**:

1. **漏斗式虚拟筛选流程**（可迁移性: 高）: ML 初筛（57,277 → 104）→ ensemble docking → MM-PBSA 精筛 → 实验验证。此流程可直接迁移到 TF–DNA 互作研究：用 ML 预测 TF 突变体或候选小分子对 DNA 结合的影响，再用 docking/MD 验证，最后用实验（如 EMSA、SELEX）确认。

2. **体积互补性作为结合亲和力的关键预测因子**（可迁移性: 高）: 本文发现 C4 位取代基大小与 RXR 激动活性正相关，提示疏水口袋填充是配体结合的关键。在 TF–DNA 互作中，类似原则可应用于预测 TF 突变对 DNA 结合界面的影响——氨基酸侧链体积变化如何影响界面互补性。

3. **体内报告系统作为计算预测的验证工具**（可迁移性: 中）: 转基因 Xenopus 模型提供了整体动物水平的验证。在 TF–DNA 研究中，类似的报告系统（如转基因斑马鱼、小鼠）可用于验证计算预测的 TF 突变或小分子干扰剂的功能影响。

4. **非允许性异源二聚体的重新审视**（可迁移性: 中）: 本文挑战了 TR-RXR 非允许性的传统观点，提示 RXR 配体可增强 T3 信号。在 TF–DNA 互作研究中，这提醒我们：辅助因子（如二聚化伴侣）的配体可能间接调控 TF 的 DNA 结合活性，即使该 TF 本身不被认为受该配体直接调控。

5. **多证据链整合**（可迁移性: 高）: 计算（docking score, ΔG_bind）+ 体外（Tox21）+ 体内（Xenopus）三层证据链的设计，为 TF-DNA 互作研究提供了范式：计算预测 → 体外生化验证 → 体内功能验证。

6. **构效关系（SAR）的建立**（可迁移性: 高）: 通过系统改变取代基大小（H < methyl < ethyl < butyl）建立活性梯度，是解析结合机制的有效策略。在 TF-DNA 研究中，可通过系统突变 DNA 结合域的关键残基（如改变侧链大小、疏水性）来建立类似的 SAR。

## 15 与已有知识连接
- **核受体超家族与 RXR 异源二聚化**（可验证）: Evans & Mangelsdorf (2014) 的经典综述描述了 RXR 作为核受体二聚化伴侣的核心作用。本文的发现（RXR 配体增强 TR-RXR 信号）与这一框架一致，但挑战了"非允许性"的绝对化。
- **CoMPARA/CERAPP 项目**（可验证）: 本文扩展了 CoMPARA 的化合物列表（55,450 → 57,277），并首次将 NR-Toxpred 应用于 RXR 配体筛选。与 Mansouri et al. (2020) 的 CoMPARA 论文直接相关。
- **Tox21 数据库**（可验证）: 本文使用的体外数据来自 Tox21 项目，该数据库包含大量核受体活性数据，可用于验证计算预测。
- **Xenopus 早熟变态模型**（可验证）: 作者前期工作（引用文献 10,11,16,26）建立了该模型，用于检测 TH 信号干扰。
- **MM-PBSA 方法**（可验证）: 该方法广泛用于配体-受体结合自由能计算，本文使用单点计算（非 MD 平均），与更精确的 MD-MM/PBSA 方法有差异。
- **与 TF-DNA 互作课题的关联**（[Analysis] 候选方向）: ① RXR 作为 DNA 结合辅助因子——可类比于其他 TF 的二聚化伴侣（如 AP-1 的 Fos/Jun）；② 小分子配体调控 TF 活性的机制——可类比于核受体的配体结合域调控 DNA 结合域；③ 计算筛选流程可迁移到 TF-小分子干扰剂筛选。

## 16 研究想法
**Agent 生成的研究候选**:

1. **名称**: TF-DNA 结合界面的"体积互补性"预测模型
   - **来源局限/观察**: 本文发现配体 C4 位取代基大小与 RXR 活性正相关，提示疏水口袋填充是关键。类似原则可能适用于 TF 的 DNA 结合界面。
   - **核心假设**: TF 的 DNA 结合域中，关键残基的侧链体积与 DNA 碱基的接触互补性可预测结合亲和力。
   - **初步方法**: 对已知 TF-DNA 复合物结构进行系统突变（改变侧链体积），用 MD 模拟 + MM-PBSA 计算结合自由能变化，与实验数据（如 SELEX、EMSA）对比。
   - **验证方式**: 与 ProTherm 或 ProBind 数据库中的突变数据对比。
   - **创新状态**: unverified

2. **名称**: 基于 ML + 对接的 TF 小分子干扰剂虚拟筛选流程
   - **来源局限/观察**: 本文的漏斗式筛选流程（ML → docking → MM-PBSA → 实验）可迁移到 TF-小分子干扰剂筛选。
   - **核心假设**: 针对 TF 的 DNA 结合域或蛋白-蛋白互作界面，ML 初筛 + 对接 + 自由能计算可有效识别干扰剂。
   - **初步方法**: 以 p53、MYC 等致癌 TF 为靶点，用 NR-Toxpred 类似框架（但重新训练）预测小分子结合，再用 ensemble docking 和 MD/MM-PBSA 精筛，最后用报告基因实验验证。
   - **验证方式**: 与已知 TF 抑制剂（如 nutlin-3 对 p53-MDM2）对比。
   - **创新状态**: partially checked（类似方法已用于核受体，但 TF 靶点较少）

3. **名称**: 异源二聚化伴侣配体对 TF-DNA 结合的间接调控机制研究
   - **来源局限/观察**: 本文挑战了 TR-RXR 非允许性观点，提示 RXR 配体可增强 TR 信号。类似机制可能存在于其他 TF 二聚化系统。
   - **核心假设**: 某些 TF 的二聚化伴侣的配体可间接调控 TF 的 DNA 结合活性，即使该 TF 本身不直接结合该配体。
   - **初步方法**: 选择 AP-1（Fos/Jun）、NF-κB（p50/p65）等系统，用 MD 模拟研究伴侣配体结合对二聚体构象和 DNA 结合的影响，用 ChIP-seq 验证。
   - **验证方式**: 与已知的 TF 活性调控数据对比。
   - **创新状态**: unverified

4. **名称**: 计算-实验联合的 TF-DNA 结合特异性预测平台
   - **来源局限/观察**: 本文展示了计算预测与体内验证的完整闭环，但 TF-DNA 互作领域缺乏类似的高通量验证平台。
   - **核心假设**: 将 ML 预测的 TF 结合位点与 docking/MD 模拟结合，可提高结合特异性预测的准确性。
   - **初步方法**: 整合 ChIP-seq 数据训练的 ML 模型与结构模拟，开发统一的预测平台，用 CRISPR 突变验证。
   - **验证方式**: 与 ENCODE 数据库中的 TF 结合数据对比。
   - **创新状态**: unverified

5. **名称**: 食品接触化学品对核受体信号通路的系统筛查
   - **来源局限/观察**: 本文仅关注 RXR，但食品接触材料中大量化学品可能影响其他核受体。
   - **核心假设**: 本文的筛选流程可扩展到所有核受体，建立食品接触化学品的核受体活性数据库。
   - **初步方法**: 对 Food Contact Chemicals Database 中的化学品进行全核受体 ML 预测 + 对接筛选，建立公开数据库。
   - **验证方式**: 与 Tox21/ToxCast 数据库中的核受体活性数据交叉验证。
   - **创新状态**: partially checked（Tox21 已有部分数据，但未系统覆盖食品接触化学品）