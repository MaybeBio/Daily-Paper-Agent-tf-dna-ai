## 01 基本信息
- **标题**：Targeting the c-Myb-CBP/p300 KIX protein-protein interaction with quinone-methide triterpenes: In silico mechanistic insights and MST biochemical validation
- **作者与单位**：Kamel, Emadeldin M; Rudayni, Hassan A; Allam, Ahmed A; Alfassam, Haifa E; Abalkhail, Adil; Aba Alkhayl, Faris F; Lamsabhi, Al Mokhtar（单位未提供）
- **期刊/预印本平台**：Journal of Molecular Graphics & Modelling
- **年份**：2026（在线日期 2026-08-28）
- **论文类型**：研究论文（计算 + 实验验证）
- **领域**：蛋白质-蛋白质相互作用（PPI）抑制；转录因子 c-Myb 与 CBP/p300 KIX 结构域互作；药物发现
- **关键词**：c-Myb；KIX；PPI 抑制剂；quinone-methide triterpenes；分子动力学；微尺度热泳（MST）
- **DOI/arXiv 号**：10.1016/j.jmgm.2026.109553
- **代码**：未提供
- **数据**：PDB:2AGH 作为结构模板；457 个 quinone-methide triterpenes 化合物库（来源未提供）
- **阅读日期**：未提供
- **在该方向中的位置**：本文属于「TF–DNA 互作调控」的上游——通过小分子破坏转录因子 c-Myb 与其共激活因子 CBP/p300 KIX 结构域的 PPI，从而间接影响 c-Myb 驱动的转录程序。方法上结合 funnel-based virtual screening、500 ns MD 模拟、ΔΔG(PPI) 与自由能景观（FEL）分析，并以 MST 实验验证。对 TF–DNA 互作课题的可迁移点在于：PPI 界面扰动分析流程、ΔΔG(PPI) 分解方法、FEL 用于评估配体诱导的构象异质性，以及计算-实验闭环验证策略。

## 02 一句话总结
本文通过 funnel-based virtual screening 从 457 个 quinone-methide triterpenes 中筛选出候选分子，结合 500 ns MD 模拟与 ΔΔG(PPI)/FEL 分析预测 tingenone 能最有效地削弱 c-Myb-KIX 相互作用（+2.31 kcal/mol），并用 MST 实验验证 tingenone 的 IC₅₀ = 23.6 ± 3.0 μM，优于参考抑制剂 Naphthol-AS-E-phosphate（IC₅₀ = 29.0 ± 1.6 μM）。

## 03 研究问题
- **具体问题**：能否从 quinone-methide triterpenes 中发现能够有效破坏 c-Myb-CBP/p300 KIX PPI 的小分子抑制剂？
- **为什么重要**：c-Myb-KIX 互作是急性髓系白血病等血液恶性肿瘤转录程序的关键调控事件，靶向该 PPI 可能提供新的治疗策略。
- **现有方法为何不足**：c-Myb-KIX 界面较大且平坦，传统小分子药物设计难以直接靶向；已有抑制剂（如 Naphthol-AS-E-phosphate）效力有限，且缺乏系统的构象动态学评估。
- **精确研究问题**：Can quinone-methide triterpenes bind to the c-Myb-bound KIX interface and induce conformational changes that weaken the c-Myb-KIX PPI, as predicted by MD-based ΔΔG(PPI) analysis and validated by MST?

## 04 背景与发展脉络
- **阶段一：c-Myb-KIX 结构解析**。PDB:2AGH 提供了 c-Myb 结合 KIX 的复合物结构，为后续 PPI 靶向研究奠定基础。
- **阶段二：PPI 抑制剂设计**。传统上 PPI 被认为是"不可成药"靶点，但近年来通过 hotspot 识别、片段筛选、虚拟筛选等方法逐步突破。代表方法包括基于结构的虚拟筛选、MD 模拟、MM-PBSA/MM-GBSA 等结合自由能计算。
- **阶段三：本工作位置**。本文在已有结构基础上，采用 funnel-based virtual screening（一种对结合位点进行预定位的筛选策略），结合长时间 MD 模拟（500 ns）和 ΔΔG(PPI) 分析，不仅评估结合亲和力，还关注配体对界面稳定性和构象动态的影响，最后用 MST 实验验证。
- **脉络标注**：以上脉络为「仅本文框架」——作者未在摘要中系统回顾 PPI 抑制剂发展史，此脉络基于本文方法选择推断。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| c-Myb-KIX PPI 难以用小分子靶向 | 界面大而平坦，传统药物设计困难 | 作者未在摘要中明确解释，但 PPI 界面缺乏深口袋是公认挑战 | 未提供（摘要未展开） |
| 已有抑制剂效力有限 | Naphthol-AS-E-phosphate 作为参考抑制剂 IC₅₀ 仅 29.0 μM | 作者未明确解释 | Results（MST 数据） |
| 仅结合亲和力不足以预测 PPI 破坏效果 | isoiguesterin 结合最有利但反而稳定界面 | 作者通过 ΔΔG(PPI) 和 FEL 分析揭示配体对界面稳定性的不同影响 | Results（ΔΔG(PPI) 与 FEL 分析） |
| 计算预测与实验验证脱节 | 许多虚拟筛选结果缺乏生化验证 | 作者采用 MST 实验验证关键预测 | Methods/Results（MST 验证） |

## 06 核心思想
1. **表面方法**：对 457 个 quinone-methide triterpenes 进行 funnel-based virtual screening，选出 3 个候选（isoiguesterin、pristimerin、tingenone），进行 500 ns MD 模拟，计算 ΔΔG(PPI) 和 FEL，最后用 MST 验证。
2. **核心洞察**：PPI 破坏效果不能仅由配体-靶标结合亲和力决定。isoiguesterin 结合最有利（ΔΔG = -5.18 kcal/mol）但反而稳定界面；tingenone 结合并非最有利（+2.31 kcal/mol）却产生最明显的界面削弱信号。关键在于配体如何影响界面残基的构象动态和整体自由能景观——tingenone 诱导更异质的构象集合（多个低能盆地），而 isoiguesterin 使体系趋于受限的低能态。
3. **可能的普适教训** [Analysis]：在 PPI 抑制剂筛选中，应同时评估"结合亲和力"与"界面稳定性/构象动态"两个维度。一个配体即使结合强，若它"锁住"了复合物的稳定构象，反而可能成为 PPI 的稳定剂而非破坏剂。这提示 ΔΔG(PPI) 与 FEL 分析应作为 PPI 抑制剂筛选的标准配套工具。

## 07 方法总览
- **输入**：PDB:2AGH 的 c-Myb-bound KIX 构象；457 个 quinone-methide triterpenes 化合物库
- **输出**：候选抑制剂的排名、ΔΔG(PPI) 值、FEL 特征、MST 实验 IC₅₀
- **模块**：
  1. Funnel-based virtual screening（预定位筛选）
  2. 500 ns MD 模拟（每个候选配体-蛋白复合物）
  3. ΔΔG(PPI) 分析（预测配体对 PPI 稳定性的影响）
  4. FEL 分析（评估构象异质性）
  5. MST 实验验证（测量 Kd 和 IC₅₀）
- **训练**：不适用（无机器学习模型）
- **工具**：未提供具体软件名称
- **反馈回路**：计算预测（ΔΔG(PPI)）→ 实验验证（MST）→ 确认或修正预测
- **文字流程**：从 PDB:2AGH 提取 c-Myb-bound KIX 构象 → 对 457 个化合物进行 funnel-based virtual screening → 选出 3 个优先候选 → 分别进行 500 ns MD 模拟 → 计算 ΔΔG(PPI) 评估界面稳定性变化 → 进行 FEL 分析评估构象异质性 → 用 MST 实验验证 c-Myb-KIX 直接互作（Kd = 28.49 μM）及候选化合物的抑制效力（IC₅₀）→ 综合计算与实验数据确定 tingenone 为最有前景的候选。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Funnel-based virtual screening | 从 457 个化合物中优先排序候选 | 降低 MD 模拟的计算成本，聚焦最有希望的分子 | 输入：化合物库 + 受体结构；输出：3 个优先候选 | 摘要明确说明该流程"prioritized isoiguesterin, pristimerin, and tingenone" | 预期影响：可能遗漏其他有效候选（未做全库 MD）[Analysis] |
| 500 ns MD 模拟 | 评估配体对界面稳定性和构象动态的影响 | 静态对接无法捕捉诱导拟合和动态效应 | 输入：3 个配体-蛋白复合物；输出：轨迹数据 | 摘要明确提及"500ns MD simulations revealed distinct ligand-dependent effects" | 预期影响：无法评估更长时尺度的构象变化 |
| ΔΔG(PPI) 分析 | 定量预测配体对 PPI 稳定性的影响 | 直接衡量 PPI 削弱/增强的倾向 | 输入：MD 轨迹；输出：ΔΔG 值（tingenone +2.31，pristimerin +0.28，isoiguesterin -5.18 kcal/mol） | 摘要给出具体数值 | 实测消融：未做；预期影响：失去定量排序依据 |
| FEL 分析 | 评估配体诱导的构象异质性 | 构象多样性可能与 PPI 破坏相关 | 输入：MD 轨迹；输出：自由能景观图 | 摘要描述 tingenone 诱导"most heterogeneous conformational ensemble" | 实测消融：未做；预期影响：失去对构象动态的直观理解 |
| MST 实验 | 验证直接互作和抑制效力 | 计算预测需实验确认 | 输入：纯化蛋白 + 化合物；输出：Kd = 28.49 μM，IC₅₀ 值 | 摘要给出具体数值 | 实测消融：未做；预期影响：无法确认计算预测的生物学相关性 |

## 09 关键公式符号
- **ΔΔG(PPI)**：配体存在与不存在时 PPI 结合自由能之差。正值表示配体削弱 PPI，负值表示稳定 PPI。用途：定量预测配体对 PPI 的影响。来源：Results 节（摘要提及具体数值）。
- **Kd（解离常数）**：MST 实验中 c-Myb-KIX 直接互作的解离常数，Kd = 28.49 ± 2.32 μM。用途：验证直接互作。来源：Results 节（MST 数据）。
- **IC₅₀（半数抑制浓度）**：MST 实验中配体抑制 PPI 的半数有效浓度。用途：定量比较候选化合物效力。来源：Results 节（MST 数据）。
- 其他公式：未提供（摘要未展开 MD 分析的具体公式，如 MM-PBSA 等）。

## 10 实验设计与证据链
- **数据集/群体**：457 个 quinone-methide triterpenes（虚拟筛选库）；3 个候选进入 MD 和 MST
- **规模**：MD 模拟 500 ns/体系；MST 实验验证 3 个候选 + 参考抑制剂
- **指标**：ΔΔG(PPI)（计算）；Kd、IC₅₀（实验）
- **基线**：参考抑制剂 Naphthol-AS-E-phosphate（IC₅₀ = 29.0 ± 1.6 μM）
- **预算**：未提供
- **骨干/仪器**：MST 仪器（具体型号未提供）
- **Oracle 输入**：PDB:2AGH 的 c-Myb-bound KIX 构象
- **评测协议**：计算预测（ΔΔG(PPI) 排序）→ 实验验证（MST 测量 IC₅₀）→ 比较计算预测与实验结果的吻合度

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| Funnel-based virtual screening | 能从化合物库中优先排序有效候选 | 457 化合物 → 3 候选 | 选出 isoiguesterin、pristimerin、tingenone | 筛选流程能缩小候选范围 | 无法证明未选中的化合物无效 | 摘要 |
| 500 ns MD + ΔΔG(PPI) | 配体能削弱或稳定 c-Myb-KIX PPI | 3 候选 + 无配体对照 | tingenone +2.31，pristimerin +0.28，isoiguesterin -5.18 kcal/mol | tingenone 预测最强削弱，isoiguesterin 反而稳定 | ΔΔG 预测未经实验直接验证（实验测的是 IC₅₀ 而非 ΔΔG） | Results |
| FEL 分析 | 配体诱导不同构象异质性 | 3 候选对比 | tingenone 多低能盆地，isoiguesterin 受限低能态 | tingenone 诱导更异质构象集合 | FEL 异质性与 PPI 破坏的因果关系未直接证明 | Results |
| MST 实验 | 候选化合物能抑制 c-Myb-KIX 互作 | 3 候选 + 参考抑制剂 | tingenone IC₅₀ = 23.6 ± 3.0 μM，优于参考（29.0 ± 1.6 μM） | tingenone 是有效抑制剂 | 未测其他未筛选化合物；未做细胞水平功能验证 | Results |

## 11 结论正确解读
- **任务范围**：本研究仅针对 c-Myb-KIX PPI 的体外生化抑制，未涉及细胞水平或动物模型的转录调控功能验证。
- **Oracle/真值输入**：PDB:2AGH 的 c-Myb-bound KIX 构象作为唯一结构模板，未考虑 KIX 的其他结合构象或 c-Myb 的替代结合模式。
- **端到端状态**：计算筛选 → MD 预测 → MST 验证的流程已闭环，但未达到药物开发阶段（无 ADMET、体内实验）。
- **算力成本**：未提供具体算力信息。
- **历史数据依赖**：依赖 PDB:2AGH 结构质量；化合物库来源未说明。
- **模型依赖**：ΔΔG(PPI) 计算方法未说明（如 MM-PBSA、MM-GBSA 或其他），不同方法结果可能有差异。
- **最难情形**：isoiguesterin 结合最有利但稳定界面，说明"结合强"不等于"抑制有效"，这是 PPI 抑制剂设计的核心难点。
- **群体/领域边界**：结论仅适用于 quinone-methide triterpenes 这一类化合物；仅针对 c-Myb-KIX 这一对 PPI。
- **不确定性**：ΔΔG(PPI) 预测与 IC₅₀ 实验之间的定量关系未建立；FEL 异质性与抑制机制之间的因果链未直接验证。
- **有边界的复述**：在 PDB:2AGH 结构基础上，通过 funnel-based virtual screening 和 500 ns MD 模拟，tingenone 被预测为能最有效削弱 c-Myb-KIX 相互作用的 quinone-methide triterpene（ΔΔG = +2.31 kcal/mol），MST 实验确认其 IC₅₀ = 23.6 ± 3.0 μM，优于参考抑制剂 Naphthol-AS-E-phosphate（29.0 ± 1.6 μM）。该结论限于体外生化层面，未涉及细胞或体内功能验证。

## 12 作者自认局限
在提供的摘要材料中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限，基于摘要推断）：
- 仅测试了 3 个候选化合物的 MST 验证，未对全部 457 个化合物进行实验筛选。
- 未提供细胞水平或体内功能验证。
- ΔΔG(PPI) 计算方法未在摘要中说明，可能影响结果可重复性。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| ΔΔG(PPI) 预测与 IC₅₀ 实验之间的定量关系未建立 | tingenone 的 ΔΔG 最大（+2.31）且 IC₅₀ 最低，但 pristimerin 的 ΔΔG 仅 +0.28 却未被实验排除；isoiguesterin 的 ΔΔG 为负（-5.18）但未报告其 IC₅₀ 是否无法测量 | 若 ΔΔG 与 IC₅₀ 无单调关系，则 ΔΔG 作为筛选指标的有效性存疑 | 对所有 3 个候选报告 IC₅₀ 并与 ΔΔG 排序比较 | Results 节 |
| FEL 异质性与 PPI 破坏的因果关系未直接证明 | tingenone 诱导多低能盆地可能反映配体诱导的构象重排，但也可能只是配体结合后的非功能性波动 | 若 FEL 异质性不是 PPI 破坏的机制，则其作为筛选指标的依据不足 | 设计突变实验：破坏 tingenone 诱导的特定构象态，观察 PPI 稳定性是否恢复 | Results（FEL 分析） |
| 仅使用单一结构模板（PDB:2AGH） | KIX 结构域可能具有多种构象态，c-Myb 也可能以不同模式结合；单一模板可能遗漏配体诱导的替代结合位点 | 若存在 cryptic pocket，则筛选可能遗漏更优候选 | 使用多构象集合（如 MD 集合、ensemble docking）重复筛选 | Methods（结构模板选择） |
| 化合物库来源和多样性未说明 | 457 个 quinone-methide triterpenes 的化学多样性未知，可能限制结构-活性关系分析 | 影响结论的泛化性 | 提供化合物库的化学空间分析 | 未提供 |
| MST 实验仅验证了直接结合抑制，未验证功能后果 | IC₅₀ 反映的是 PPI 抑制，但未证明该抑制能阻断 c-Myb 驱动的转录程序 | 若抑制 PPI 不足以改变转录输出，则治疗意义有限 | 增加报告基因实验或转录组分析 | Results（MST 数据） |

## 14 学到什么
**Agent 提炼的知识候选**

1. **ΔΔG(PPI) 作为 PPI 扰动指标**：本文用 ΔΔG(PPI) 区分配体对 PPI 的稳定/削弱效应。可迁移到 TF–DNA 互作课题：对于预测 TF 突变或小分子对 TF–DNA 结合的影响，可计算 ΔΔG(binding) 来评估突变/配体对 TF–DNA 复合物稳定性的影响，而非仅看单个结合亲和力。

2. **FEL 分析用于评估配体诱导的构象异质性**：本文用 FEL 区分配体诱导的构象状态分布差异。可迁移到 TF–DNA 互作：TF 结合 DNA 时往往经历构象选择或诱导拟合，FEL 可帮助区分不同 TF 突变体或不同 DNA 序列下 TF 的构象景观差异，从而理解结合特异性机制。

3. **"结合强 ≠ 抑制有效"的教训**：isoiguesterin 结合最有利但稳定界面，提示在 TF–DNA 互作研究中，评估 TF 突变或小分子效应时，不能只看结合亲和力变化，还要看是否影响复合物的动态稳定性。例如，一个 TF 突变可能增强 DNA 结合但"锁死"了 TF 的活性构象，反而降低转录活性。

4. **计算-实验闭环验证策略**：虚拟筛选 → MD 预测 → 实验验证（MST）的流程可迁移到 TF–DNA 互作研究：对 TF–DNA 复合物进行虚拟筛选（如针对 TF 的 DNA 结合域寻找小分子），用 MD 预测结合模式，再用实验（如 EMSA、ITC、MST）验证。

5. **funnel-based virtual screening 方法**：该方法对结合位点进行预定位，提高筛选效率。可迁移到 TF–DNA 互作：对 TF 的 DNA 结合域进行 funnel-based 筛选，寻找可能干扰 DNA 结合的小分子或肽段。

6. **MST 作为 PPI/蛋白-核酸互作验证工具**：MST 可测量溶液中蛋白-蛋白或蛋白-核酸相互作用的 Kd 和竞争抑制 IC₅₀。可迁移到 TF–DNA 互作：用 MST 测量 TF-DNA 结合亲和力及候选抑制剂对 TF-DNA 结合的竞争效应。

## 15 与已有知识连接
- **PDB:2AGH**：c-Myb 与 KIX 结构域的复合物结构，是研究 TF-共激活因子互作的代表性结构。可连接到其他 TF-共激活因子复合物结构（如 p53-MDM2、p53-CBP/p300）进行比较分析。
- **c-Myb 在白血病中的角色**：c-Myb 是造血系统关键转录因子，其异常表达与急性髓系白血病相关。可连接到已有关于 c-Myb DNA 结合域（R2R3）与 DNA 互作的研究，以及针对 c-Myb DNA 结合的小分子抑制剂研究。
- **KIX 结构域的多配体结合特性**：KIX 结构域可同时结合多个转录因子（如 c-Myb、MLL、p53），是研究转录因子竞争性结合共激活因子的模型系统。可连接到关于转录凝聚体（transcriptional condensates）和协同转录调控的研究。
- **quinone-methide triterpenes**：这类天然产物（如 celastrol、pristimerin）已知具有抗炎、抗肿瘤活性，部分通过共价修饰蛋白半胱氨酸残基发挥作用。可连接到关于天然产物作为 TF 活性调节剂的研究。
- **MST 技术**：微尺度热泳是测量分子间相互作用的常用方法，可连接到 ITC、SPR、EMSA 等互补技术，用于交叉验证蛋白-蛋白或蛋白-核酸互作数据。
- **ΔΔG 计算方法**：本文的 ΔΔG(PPI) 分析可连接到 MM-PBSA/MM-GBSA、FEP 等自由能计算方法，以及这些方法在预测突变效应（如 ΔΔG 用于预测 TF 突变对 DNA 结合的影响）中的应用。

## 16 研究想法
**Agent 生成的研究候选**

1. **候选名称**：TF–DNA 结合小分子干扰物的 ΔΔG 引导筛选
   - **来源局限/观察**：本文用 ΔΔG(PPI) 评估 PPI 扰动，但未扩展到 TF–DNA 互作；TF–DNA 界面同样平坦，传统筛选困难。
   - **核心假设**：ΔΔG(binding) 能有效预测小分子对 TF–DNA 复合物稳定性的影响，且与实验测得的 DNA 结合抑制效力相关。
   - **初步方法**：选取一个 TF–DNA 复合物（如 c-Myb R2R3-DNA），对化合物库进行 funnel-based virtual screening，对 top 候选进行 MD 模拟并计算 ΔΔG(binding)，用 MST 或 EMSA 验证。
   - **验证方式**：比较 ΔΔG 预测排序与实验 IC₅₀ 排序的一致性；设置已知 DNA 结合抑制剂作为阳性对照。
   - **创新状态**：unverified

2. **候选名称**：TF 突变体对 DNA 结合特异性的 FEL 分析
   - **来源局限/观察**：本文用 FEL 区分配体诱导的构象异质性，但未用于 TF 突变体分析；TF 突变常导致 DNA 结合特异性改变，机制未明。
   - **核心假设**：TF 突变体在结合 DNA 时的 FEL 差异能解释其 DNA 结合特异性变化，且 FEL 特征（盆地数量、深度）与实验测得的结合亲和力/特异性相关。
   - **初步方法**：对一系列 TF 突变体（如 p53 DNA 结合域突变体）进行 MD 模拟，计算 FEL，比较突变体与野生型的构象景观差异，结合实验数据（如蛋白微阵列、SELEX）验证。
   - **验证方式**：FEL 预测的特异性变化与实验测得的 DNA 结合谱比较；突变体 FEL 特征与临床突变致病性关联分析。
   - **创新状态**：unverified

3. **候选名称**：TF–DNA 互作 vs TF–共激活因子互作的竞争性调控
   - **来源局限/观察**：本文研究 TF-共激活因子 PPI 抑制，但未考虑 TF 同时结合 DNA 和共激活因子的竞争关系；TF 可能通过构象变化在 DNA 结合和共激活因子结合之间切换。
   - **核心假设**：小分子或翻译后修饰通过改变 TF 的构象景观，同时影响 TF–DNA 和 TF–共激活因子互作，且这种双重调控可通过 FEL 分析预测。
   - **初步方法**：以 c-Myb 为模型，构建 c-Myb-DNA-KIX 三元复合物模型，用 MD 模拟研究 DNA 结合对 c-Myb-KIX 互作的影响，以及小分子（如 tingenone）对三元复合物稳定性的影响。
   - **验证方式**：用 MST 或 ITC 测量三元复合物中各组分的结合亲和力变化；用细胞实验验证转录输出变化。
   - **创新状态**：unverified

4. **候选名称**：基于 FEL 的 TF–DNA 结合小分子抑制剂分类器
   - **来源局限/观察**：本文仅测试了 3 个候选，未建立 FEL 特征与抑制效力之间的定量关系。
   - **核心假设**：FEL 特征（如盆地数量、能量屏障高度、构象熵）可作为 TF–DNA 或 TF–PPI 小分子抑制剂的预测性生物标志物。
   - **初步方法**：对更多化合物进行 MD + FEL 分析，提取 FEL 特征，与实验 IC₅₀ 建立回归模型（如随机森林、高斯过程）。
   - **验证方式**：留一法交叉验证；对未参与训练的化合物进行前瞻性预测并实验验证。
   - **创新状态**：unverified

5. **候选名称**：c-Myb 的 DNA 结合域与 KIX 结合域的构象耦合
   - **来源局限/观察**：本文聚焦 c-Myb-KIX 互作，但 c-Myb 的 DNA 结合域（R2R3）与转录激活域（含 KIX 结合基序）之间的构象耦合未被研究。
   - **核心假设**：c-Myb 的 DNA 结合状态影响其 KIX 结合域的构象可及性，从而影响共激活因子招募；小分子可通过改变这种构象耦合来调控转录输出。
   - **初步方法**：构建 c-Myb 全长或截短体的 MD 模型，模拟 DNA 结合与未结合状态，比较 KIX 结合域的构象动态；用 HDX-MS 或 FRET 实验验证。
   - **验证方式**：比较 DNA 结合前后 KIX 结合域的构象变化；测试小分子对构象耦合的影响。
   - **创新状态**：unverified