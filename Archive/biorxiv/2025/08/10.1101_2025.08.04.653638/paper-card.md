## 01 基本信息
- **标题**：Interpreting the Effects of DNA Polymerase Variants at the Structural Level Using MAVISp and Molecular Dynamics Simulations
- **作者与单位**：Arnaudi M; Krzesińska K; Beltrame L; Besora PS; Tiberti M; Nilbert M; Rohlin A; Papaleo E（单位未在摘要中提供，Papaleo E 团队受丹麦基础研究基金等资助，推测隶属丹麦技术大学等机构）
- **期刊/预印本平台**：bioRxiv
- **年份**：2025
- **论文类型**：预印本（方法学应用 + 结构-功能注释研究）
- **领域**：结构生物信息学、蛋白质变异功能预测、分子动力学模拟
- **关键词**：MAVISp、POLE、POLD1、DNA聚合酶、错义变异、分子动力学、ΔΔG、ACM/AMP
- **DOI/arXiv 号**：10.1101/2025.08.04.653638
- **代码**：MAVISp 相关 GitHub 仓库（https://github.com/ELELAB/MAVISp_automatization、https://github.com/ELELAB/mavisp_accessory_tools、https://github.com/ELELAB/MAVISp_downstream_analysis）
- **数据**：OSF 仓库（https://osf.io/z8x4j），MAVISp 数据库（https://services.healthtech.dtu.dk/services/MAVISp-1.0/），PolED 数据库（https://poled-db.org）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦 DNA 聚合酶（POLE/POLD1）错义变异的结构解读，核心是蛋白质稳定性（ΔΔG）与蛋白-DNA 结合自由能变化的计算预测，属于「蛋白质-DNA 互作 × 物理模拟（MD + 自由能计算）」方向。对 TF-DNA 课题的可迁移点在于：MAVISp 模块化框架（稳定性、局部互作、PTM、长程通讯）可直接迁移到转录因子变异的功能解读；MD 结合 FoldX/RaSP/Rosetta 的 ensemble 模式策略（χ1 二面角验证构象采样充分性）是评估结合界面残基变异效应的通用方法。

## 02 一句话总结
本文用 MAVISp 框架（FoldX、RaSP、Rosetta 的 ΔΔG 计算 + MD 模拟的 ensemble 模式）对 POLE/POLD1 的 6 万余个错义变异进行结构层面解读，通过 χ1 二面角分析验证构象采样充分性，识别出影响催化位点构象（如 S297F、P436R）和 DNA 结合亲和力（如 N363K、G702S）的变异，并为 ClinVar VUS 提供 ACMG PP3/BP4/PM1 计算证据。

## 03 研究问题
- **具体问题**：DNA 聚合酶 POLE 和 POLD1 的错义变异如何通过改变蛋白质稳定性、催化位点构象、DNA 结合或蛋白-蛋白互作来影响功能？如何系统性地从结构层面解读这些变异？
- **为什么重要**：POLE/POLD1 变异与遗传性癌症综合征（如聚合酶校对相关息肉病 PPAP）和体细胞高突变肿瘤相关，但大量 ClinVar VUS 缺乏功能注释，临床解读困难。
- **现有方法不足**：单一 VEP（如 AlphaMissense）提供致病性概率但缺乏机制解释；单结构静态 ΔΔG 计算忽略蛋白质动态构象；已有研究未系统整合稳定性、结合、PTM、长程通讯等多维度结构证据。
- **精确研究问题**：Can a modular structure-based framework (MAVISp) combined with MD simulations provide mechanistic structural interpretations for missense variants in POLE/POLD1 that are consistent with experimental functional data and enable ACMG-compliant reclassification of VUS?

## 04 背景与发展脉络
（标注：以下脉络为「经外部核验」+「仅本文框架」混合，具体标注于各条目）
1. **早期变异功能预测（经外部核验）**：SIFT、PolyPhen 等序列保守性方法 → 缺乏结构机制。
2. **结构稳定性预测（经外部核验）**：FoldX、Rosetta 等基于力场的 ΔΔG 计算 → 单结构静态近似，忽略构象多样性。
3. **机器学习 VEP（经外部核验）**：AlphaMissense、EVE、REVEL 等 → 高准确率但黑箱，无机制解释。
4. **MAVISp 框架（仅本文框架 + 作者前期工作）**：模块化结构解读，整合稳定性、局部互作、PTM、长程通讯、VEP 多层证据；simple mode 用单结构，ensemble mode 用 MD 构象集合。
5. **本文主张的位置**：将 MAVISp 全面应用于 POLE/POLD1 两个大型聚合酶，首次引入 χ1 二面角分析验证 ensemble 模式构象采样充分性，并开发 DNA 结合自由能变化的能量组分分解流程，将结构预测与 ACMG 临床解读标准对接。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 变异功能注释缺失 | ClinVar 中大量 VUS 无临床解读 | 实验功能检测通量低，难以覆盖所有错义变异 | Results 节：465 个 POLE VUS、518 个 POLD1 VUS 被重新评估 |
| 单一 VEP 缺乏机制 | AlphaMissense 等只给概率不给机制 | 基于序列/进化模式，不直接建模结构效应 | Results 表 1：AlphaMissense 准确率最高但需结构机制补充 |
| 静态结构预测局限 | 单结构 ΔΔG 计算忽略构象多样性 | 蛋白质在溶液中存在多种构象，单结构可能不代表功能相关状态 | Methods 节：ensemble mode 使用 MD 构象集合 |
| 构象采样充分性未验证 | ensemble 模式结果可能依赖采样不足的构象子集 | 仅用少量聚类结构可能遗漏关键构象状态 | Methods 节：χ1 二面角分析，Jensen-Shannon 散度阈值 0.3-0.4 |
| 大蛋白计算成本高 | POLE（2286 残基）和 POLD1（1107 残基）全蛋白 MD 昂贵 | 系统规模大，需平衡采样深度与计算资源 | Methods 节：500 ns MD（POLE 2-2286、POLD1 2-1107），1000 ns 用于 POLE 30-522 变异体 |
| DNA 结合效应难以量化 | 蛋白-DNA 界面变异的功能后果复杂 | 涉及静电、溶剂化、范德华等多种能量组分 | Results 节：N363K、G702S 的 FoldX 能量组分分解 |

## 06 核心思想
1. **表面方法**：用 MAVISp 框架对 POLE/POLD1 全部错义变异进行系统扫描，包括稳定性（FoldX + RaSP + Rosetta）、局部互作（Arpeggio 接触分析）、PTM 位点、长程通讯（AlloSigMA2）、DNA 结合（FoldX 结合自由能）五个维度；用 MD 模拟生成 ensemble 构象；用 χ1 二面角分析验证构象采样充分性；最后将结果映射到 ACMG PP3/BP4/PM1 证据框架。
2. **核心洞察**：变异效应是构象依赖的——同一变异在不同构象状态下可能表现出不同的 ΔΔG 特征（如 S297F 和 P436R 仅在部分 MD 构象中显示强 destabilizing 效应）。因此，仅用单结构预测会遗漏构象特异的致病机制。此外，DNA 结合效应的解读需要分解能量组分（静电 vs 溶剂化 vs 范德华），而非只看总 ΔΔG。
3. **可能的普适教训 [Analysis]**：对于 TF-DNA 互作研究，变异解读不应止步于「是否 destabilizing」，而应追问「在哪个构象状态、通过哪种能量组分、影响哪个功能界面」。MD ensemble + 能量组分分解是回答这些问题的通用范式；χ1 二面角分析可作为验证构象采样充分性的低成本代理指标。

## 07 方法总览
- **输入**：POLE（UniProt 主异构体，残基 2-2286）和 POLD1（残基 2-1107）的 AlphaFold 模型；ClinVar、COSMIC、cBioPortal 变异数据；PolED 实验功能数据
- **输出**：每个变异的机制注释（稳定性/结合/PTM/长程通讯）、ACMG PP3/BP4/PM1 证据分类、候选变异优先级排序
- **模块**：
  1. STRUCTURE_SELECTION：从 AF 数据库和 PDB 选择/评估结构质量
  2. STABILITY：FoldX（MutateX 流程）+ RaSP + Rosetta（cartddg2020）计算 ΔΔG，consensus 分类
  3. LOCAL_INTERACTION：蛋白-蛋白复合物（POLE-PCNA、POLE-POLE2/MCM2/MCM5/CDC45、POLD1-POLD2/POLD4/PCNA/LASP1）结合自由能
  4. 蛋白-DNA 互作：POLE/POLD1 与 DNA 复合物（PDB 6TNY、9B8S、9B8T、9F6I/J/K/L）结合自由能 + Arpeggio 接触分析
  5. PTM：磷酸化位点变异效应
  6. LONG_RANGE：AlloSigMA2 粗粒化模型 + MD 网络分析
  7. EFOLDMINE：早期折叠事件种子位点
  8. 变异筛选：SpliceAI + Pangolin 排除剪接位点变异
- **训练**：无监督（无训练步骤）；RaSP 为预训练 ML 模型
- **反馈回路**：MD 模拟 → 构象聚类 → 选取代表性构象 → 重新计算 ΔΔG → 与 simple mode 结果对比 → 识别构象依赖效应
- **文字流程**：变异收集 → 结构选择 → simple mode 全扫描 → 对候选变异（已知致病 + 高排名 VUS）进行 MD 模拟 → χ1 二面角验证采样充分性 → ensemble mode 重算稳定性/结合 → 能量组分分解 → ACMG 证据整合 → 优先级排序

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| STABILITY (FoldX+RaSP+Rosetta) | 预测错义变异对折叠自由能的影响 | 稳定性改变是变异致病的主要机制之一 | 输入：AF 模型/PDB 结构 + 变异列表；输出：ΔΔG 值及 destabilizing/neutral/stabilizing 分类 | Results 图 2-3：S297F、P436R 的构象依赖 destabilizing 效应 | 预期影响：失去主要机制注释来源；已知影响：consensus 方法减少单一方法偏差 |
| LOCAL_INTERACTION | 预测变异对蛋白-蛋白结合的影响 | POLE/POLD1 功能依赖与复制机器亚基互作 | 输入：复合物结构 + 界面变异；输出：结合 ΔΔG 分类 | Results 图 6：W2276C、I1183N 破坏 POLE-PCNA 互作 | 预期影响：遗漏互作界面变异的功能解读 |
| 蛋白-DNA 结合分析 | 预测变异对 DNA 结合亲和力的影响 | 聚合酶核心功能是 DNA 合成与校对 | 输入：聚合酶-DNA 复合物 + 变异；输出：结合 ΔΔG + 能量组分分解 + Arpeggio 接触变化 | Results 图 5、7：N363K、G702S 的 DNA 结合效应 | 预期影响：无法识别影响 DNA 识别界面的变异 |
| MD 模拟 (ensemble mode) | 生成构象集合，评估构象依赖效应 | 单结构静态预测可能遗漏关键构象状态 | 输入：AF 模型/复合物；输出：轨迹、聚类结构、RMSF | Results 图 3-4：S297F 的 68% 构象 destabilizing | 预期影响：无法捕捉构象依赖的致病机制 |
| χ1 二面角分析 | 验证 ensemble 采样充分性 | 确保 ΔΔG 计算基于代表性构象 | 输入：MD 轨迹；输出：Jensen-Shannon 散度、rotamer 分布 | Methods 节：JSD ≥ 0.3-0.4 阈值 | 预期影响：无法评估构象采样质量，结果可靠性下降 |
| ACMG 证据整合 | 将结构预测映射到临床解读框架 | 连接计算预测与临床决策 | 输入：各模块输出 + ClinVar 注释；输出：PP3/BP4/PM1 分类 | Results 表 2-4：212 个 POLE VUS 获 PP3 证据 | 预期影响：无法直接支持临床变异解读 |

## 09 关键公式符号
- **ΔΔG（折叠自由能变化）**：ΔΔG = ΔG_mutant − ΔG_wildtype。正值表示 destabilizing。由 FoldX 5 和 RaSP 计算，Rosetta cartddg2020 作为补充。用于 STABILITY 模块分类。
- **ΔΔG_binding（结合自由能变化）**：ΔΔG_binding = ΔG_binding,mutant − ΔG_binding,wildtype。正值表示结合减弱。由 FoldX 计算，用于 LOCAL_INTERACTION 和蛋白-DNA 结合分析。
- **Jensen-Shannon 散度（JSD）**：用于比较 MD 轨迹中 χ1 二面角分布与聚类结构子集的差异。JSD ≥ 0.3-0.4 表示构象显著差异，提示采样不足。
- **Z-score（RMSF 标准化）**：Z = (RMSF_residue − mean_RMSF) / SD_RMSF，用于分类残基灵活性（rigid/flexible/partially flexible）。
- **EfoldMine score**：预测残基是否为早期折叠事件种子，阈值 0.169，最小连续长度 3 残基。
- **AlloSigMA2 变构自由能**：基于粗粒化模型的扰动传播计算，用于 LONG_RANGE 模块。
- **PP3/BP4 阈值**：基于 ClinVar 已知致病/良性变异校准，使用 25th 百分位（致病）和 75th 百分位（良性）作为边界，具体数值见补充表 S2。

## 10 实验设计与证据链
- **数据集**：
  - POLE：43,415 个错义变异（饱和突变扫描，残基 2-2286）
  - POLD1：21,014 个错义变异（残基 2-1107）
  - ClinVar 注释：4,291（POLE）+ 2,025（POLD1）个变异有 ClinVar 记录
  - 实验功能数据：PolED 数据库（酵母突变率实验）
  - 结构：AlphaFold 模型 + PDB 实验结构（6TNY、9B8S、9B8T、9F6I/J/K/L、5VBN）
- **指标**：ΔΔG 值、consensus 分类准确率、MCC、平衡准确率、AUC、JSD、RMSF Z-score
- **基线/对比**：AlphaMissense、EVE、REVEL、GEMME 四种 VEP 对比（表 1）；simple mode vs ensemble mode 对比
- **评测协议**：以 ClinVar 致病/良性注释为金标准，计算各 VEP 的 MCC 和平衡准确率；对 VUS 使用校准阈值分配 PP3/BP4

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-------------------|------|
| VEP 性能评估 | AlphaMissense 在 POLE/POLD1 中表现最佳 | 37 个 POLE + 12 个 POLD1 已知变异，对比 4 种 VEP | AlphaMissense 平衡准确率最高，EVE 的 MCC 最高 | AlphaMissense 适合作为 MAVISp 发现流程第一步 | 样本量小（n=49），无法推广到所有变异类型 | Results 表 1 |
| S297F/P436R 构象依赖稳定性 | 变异效应依赖构象状态 | MD 模拟 + FoldX 多构象 ΔΔG vs 单结构 ΔΔG | S297F 在 68% 构象中 destabilizing；P436R 在 44% 构象中 destabilizing | 单结构预测会遗漏构象特异效应 | MD 采样可能未覆盖全部功能相关构象 | Results 图 3-4 |
| N363K DNA 结合效应 | 变异通过改变 DNA 结合影响校对功能 | FoldX 结合自由能 + Arpeggio 接触分析，frayed vs mismatch-excision 状态 | N363K 在 frayed 状态减弱 DNA 结合，在 mismatch-excision 状态增强结合 | 变异效应是状态依赖的，需考虑功能状态 | 未进行实验验证结合亲和力变化 | Results 图 5 |
| G702S DNA 结合效应 | 变异位于 fingers-palm 界面影响 DNA 协调 | 结合自由能 + 接触分析 | G702S 在所有 DNA 结合构象中 destabilizing，主要来自范德华冲突 | G702S 可能通过干扰 DNA 定位降低复制保真度 | 未直接测量复制保真度变化 | Results 图 7 |
| VUS 重新分类 | MAVISp 可为 VUS 提供 ACMG 证据 | 465 个 POLE VUS + 518 个 POLD1 VUS | 212 个 POLE VUS 获 PP3，138 个获 BP4；152 个 POLD1 VUS 获 PP3，185 个获 BP4 | MAVISp 可系统提供 ACMG 计算证据 | PP3/BP4 为计算证据，不等同于临床致病性 | Results 表 2-4 |

## 11 结论正确解读
- **任务范围**：仅覆盖错义变异（单氨基酸替换），不涉及插入/缺失、剪接变异（仅用于排除）、拷贝数变异等。
- **oracle/真值输入**：ClinVar 注释作为 VEP 评估的金标准，但 ClinVar 本身存在注释偏差（研究偏好、报告偏倚）；PolED 实验数据仅覆盖部分变异。
- **端到端状态**：非端到端。MAVISp 是计算框架，输出为机制假设和 ACMG 计算证据，不替代实验验证或临床判断。
- **算力成本**：MD 模拟仅对候选变异（已知致病 + 高排名 VUS）进行，非全扫描；全扫描使用 simple mode（单结构）。
- **历史数据依赖**：变异数据收集于 2023-06-24，ClinVar 注释截至 2025-11-07，后续数据库更新可能改变分类。
- **模型依赖**：RaSP 为预训练 ML 模型，其训练分布可能影响预测；FoldX 力场对溶剂化效应描述有限。
- **最难情况**：位于无序区域（低 pLDDT）的变异、涉及 backbone 重排的变异、需要长时程构象变化的变异。
- **有边界的复述**：在 AlphaFold 模型和现有实验结构基础上，MAVISp 框架能够为 POLE/POLD1 错义变异提供多维度结构机制注释，其中约 40% 的 ClinVar VUS 可获得 PP3 或 BP4 计算证据，但所有预测需实验验证后方可用于临床决策。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 缺乏 POLD1 的 DNA 结合人源结构 | POLD1-DNA 复合物分析受限于结构可用性 | 等待新的实验结构，或使用同源建模 | Results 节（POLD1 DNA 结合分析部分） |
| MD 模拟时间尺度有限 | 500 ns 可能不足以捕捉大尺度构象重排 | 使用增强采样方法（如 metadynamics） | Methods 节（MD 模拟部分） |
| FoldX 方法局限性 | 对 backbone 重排和溶剂化效应描述有限 | 结合更精确的自由能计算方法 | Results 图 3B 讨论 |
| 计算资源限制 | 无法对所有 6 万余变异进行 MD 模拟 | 仅对候选变异进行 ensemble mode 分析 | Methods 节（ensemble mode 策略） |
| 实验验证不足 | 预测的机制假设未经系统实验验证 | 建议对高排名候选进行酵母突变率实验和生化表征 | Conclusions 节 |
| 剪接效应未全面整合 | 仅用 SpliceAI/Pangolin 排除剪接变异，未深入分析 | 未来可整合 RNA 层面的功能数据 | Methods 节（剪接分析部分） |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| VEP 评估样本量极小（n=49） | MCC 和平衡准确率的估计可能不稳定；POLE/POLD1 已知变异数量有限 | 影响 AlphaMissense 作为发现流程第一步的可靠性结论 | 使用更大规模的独立数据集（如 gnomAD 约束数据）进行外部验证 | Results 表 1 |
| 以 ClinVar 注释为金标准存在循环论证风险 | AlphaMissense 等 VEP 的训练数据可能包含 ClinVar 变异 | 高估 VEP 性能 | 检查 VEP 训练集是否包含 POLE/POLD1 变异，使用时间上更早的 ClinVar 版本 | Methods 节（VEP 评估部分） |
| MD 模拟仅用 AF 模型，未用实验结构交叉验证 | AF 模型在功能构象上可能偏离实验结构 | 影响 ensemble mode 结果的可靠性 | 对已有实验结构的区域（如 6TNY）用实验结构重跑 MD 并比较 | Methods 节（结构选择部分） |
| χ1 二面角分析仅作为采样充分性代理指标 | 二面角分布一致不代表构象空间完全采样 | 可能高估 ensemble mode 的可靠性 | 使用更严格的收敛性指标（如 RMSD 聚类、自由能面重叠） | Methods 节（χ1 分析部分） |
| DNA 结合分析仅用 FoldX，未用 MD 自由能计算交叉验证 | FoldX 对蛋白-DNA 界面的力场参数可能不准确 | 影响 DNA 结合相关变异的结论强度 | 对关键候选（如 N363K、G702S）用 MM/PBSA 或 FEP 计算交叉验证 | Results 图 5、7 |
| 排名流程的权重设置主观性 | 特征权重由作者配置，可能引入偏差 | 影响 VUS 优先级的可重复性 | 进行敏感性分析，测试不同权重对排名的影响 | Methods 节（排名流程部分） |
| 未报告 MD 模拟的复制数 | 单次 MD 可能不足以评估变异效应的统计显著性 | 影响构象依赖结论的稳健性 | 对关键变异进行多次独立 MD 模拟并报告变异性 | Methods 节（MD 模拟部分） |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **模块化变异解读框架**：MAVISp 将变异效应分解为稳定性、局部互作、PTM、长程通讯、结合亲和力五个维度。迁移到 TF-DNA 课题：对转录因子变异，可建立「DNA 结合域稳定性 + 特定 DNA 基序结合亲和力 + 二聚化界面 + 磷酸化调控位点」的多层解读框架。
2. **Ensemble mode 策略**：用 MD 生成构象集合，在多个构象上计算 ΔΔG，识别构象依赖效应。迁移：TF 的 DNA 结合域在结合 DNA 前后存在构象变化（induced fit），变异效应应在 apo 和 holo 两种状态下分别评估。
3. **χ1 二面角作为采样充分性代理指标**：低成本验证 MD 采样是否覆盖主要 rotamer 状态。迁移：在 TF-DNA MD 模拟中，可用 χ1 分析快速评估结合界面残基的构象采样是否充分，避免因采样不足导致的假阳性/假阴性。
4. **能量组分分解**：将 ΔΔG_binding 分解为静电、溶剂化、范德华等组分，识别变异的物理化学机制。迁移：TF 的 DNA 结合特异性常由特定残基-碱基氢键和疏水接触决定，组分分解可区分「直接破坏氢键」vs「改变溶剂化」两种机制。
5. **ACMG 证据映射**：将计算预测映射到 PP3/BP4/PM1 证据等级，支持临床解读。迁移：对 TF 变异，可建立类似的计算证据框架，但需注意 TF 变异的功能后果更复杂（剂量敏感、组织特异性）。
6. **剪接位点排除流程**：在结构分析前先用 SpliceAI/Pangolin 排除剪接相关变异，避免将剪接效应误判为蛋白质结构效应。迁移：TF 变异解读应同样先排除剪接效应，特别是外显子-内含子边界附近的变异。

## 15 与已有知识连接
- **MAVISp 原始论文**：本文是 MAVISp 框架的扩展应用，原始框架发表于作者团队前期工作（引用 8），本文新增 χ1 二面角验证和 DNA 结合能量组分分解流程。
- **AlphaMissense**（引用 16）：作为 VEP 基准，其全蛋白质组覆盖能力与本文结构方法互补。
- **PolED 数据库**：实验功能数据来源，连接计算预测与酵母突变率实验。
- **DNA 聚合酶校对机制**：POLE/POLD1 外切酶结构域（exonuclease domain）的校对功能与癌症易感性关联（引用 1-3, 9），本文的 S297F/P436R 分析直接对接该机制。
- **可迁移的外部方向**：
  - TF-DNA 结合特异性预测（如 DeepSEA、DeepBind）：本文的「结构变异解读」可与之结合，为序列预测提供结构解释。
  - 蛋白质-DNA 对接与 MD 模拟（如 HADDOCK、AMBER）：本文的 ensemble 策略可迁移到 TF-DNA 复合物。
  - 临床变异解读标准（ACMG/AMP）：本文的 PP3/BP4 校准流程可推广到其他蛋白质家族。

## 16 研究想法
**Agent 生成的研究候选**：
1. **TF 变异结构解读框架（TF-MAVISp）**：将 MAVISp 模块化框架迁移到转录因子，建立「DNA 结合域稳定性 + 基序结合亲和力 + 二聚化界面 + 磷酸化调控」的多层解读管线。初步方法：选取 50-100 个已知致病/良性 TF 变异（如 p53、MYC），用 FoldX+RaSP 计算 ΔΔG，用 MD 评估构象效应。验证方式：与实验 DNA 结合数据（如 HT-SELEX、PBMs）对比。创新状态：unverified。
2. **TF-DNA 结合变异的构象依赖效应系统分析**：假设 TF 变异效应在 apo 和 DNA-bound 状态下不同。初步方法：对 10-20 个 TF-DNA 复合物（含 apo 结构）进行 MD 模拟，比较两种状态下 ΔΔG_binding 的差异。验证方式：用 SPR 或 EMSA 实验验证关键预测。创新状态：unverified。
3. **DNA 结合自由能组分分解的自动化流程**：开发工具自动分解 FoldX 的 ΔΔG_binding 为静电、范德华、溶剂化组分，并可视化接触变化。初步方法：基于本文的 FoldX-Arpeggio 流程扩展，支持任意蛋白-DNA 复合物。验证方式：在已知变异数据集上测试组分分解的判别力。创新状态：partially checked（本文已用于 POLE/POLD1，需推广到 TF）。
4. **TF 变异剪接-结构联合解读**：对 TF 基因的错义变异，先排除剪接效应再分析结构影响。初步方法：用 SpliceAI+Pangolin 过滤 TF 变异，对比过滤前后结构预测的准确率变化。验证方式：用 RNA-seq 数据验证剪接预测。创新状态：unverified。
5. **TF 变异的 ACMG 计算证据标准化**：为 TF 基因建立 PP3/BP4 校准阈值，类似本文补充表 S2。初步方法：收集 ClinVar 中 TF 基因的致病/良性变异，校准各 VEP 阈值。验证方式：与 ClinGen 专家小组的规范对比。创新状态：unverified。
6. **TF-DNA 结合域的无序区域变异分析**：本文发现低 pLDDT 区域变异需特殊处理。迁移到 TF：许多 TF 含 intrinsically disordered regions（如 activation domains），这些区域的变异可能通过相分离或变构机制影响功能。初步方法：对 TF 无序区域的变异用 MD 和增强采样分析构象 ensemble 变化。验证方式：细胞实验验证转录活性变化。创新状态：unverified。