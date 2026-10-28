## 01 基本信息
- **标题**：Co-component signal transduction systems: Fast-evolving virulence regulation cassettes discovered in enteric bacteria
- **作者与单位**：Kinch, Lisa N; Cong, Qian; Jaishankar, Jananee; Orth, Kim（德克萨斯大学西南医学中心，K.O. 实验室）
- **期刊/预印本平台**：Proceedings of the National Academy of Sciences of the United States of America (PNAS)
- **年份**：2022-06-02
- **论文类型**：研究论文（含计算方法与实验验证）
- **领域**：细菌信号转导、毒力调控、结构预测（AlphaFold）、蛋白质进化
- **关键词**：co-component signal transduction、VtrA/VtrC、ToxR/ToxS、lipocalin、AlphaFold、毒力调控
- **DOI/arXiv 号**：10.1073/pnas.2203176119
- **代码**：未提供（ColabFold/AlphaFold 为外部工具）
- **数据**：SI Appendix（表 S1–S3、图 S1–S3）；结构模型未公开提供
- **阅读日期**：2026-05-13
- **在课题方向中的位置**：本文聚焦细菌双组分/共组分信号转导系统中转录因子（TF）的跨膜感知与调控机制，核心对象为 VtrA/VtrC 与 ToxR/ToxS 等膜结合转录因子。其方法学核心——利用 AlphaFold/ColabFold 结构预测识别序列已高度分化的同源蛋白——对「TF–DNA 互作 × AI 结构预测」方向具有直接可迁移性：展示了当序列比对失效时，结构预测可作为同源检测与功能推断的替代工具。但本文不涉及 TF–DNA 结合机制本身（DNA 结合域仅作为输出域提及），也不涉及分子动力学模拟。

## 02 一句话总结
本文通过 AlphaFold/ColabFold 结构预测，发现肠杆菌中 VtrA/VtrC 样共组分信号转导系统（含 ToxR/ToxS、PsaE/PsaF 等）的周质感知组件共享脂质运载蛋白（lipocalin）折叠，支持其从共同祖先分化而来，并提示脂质感应可能调控肠道致病菌毒力。

## 03 研究问题
- **具体问题**：VtrA/VtrC 共组分信号转导系统（感知胆汁酸、调控 T3SS2 毒力分泌装置）在肠杆菌中是否存在同源系统？这些系统的周质感知组件是否共享共同折叠与功能机制？
- **为什么重要**：VtrA/VtrC 是已知的毒力调控系统，但其周质感知组件的序列高度分化，传统序列比对无法识别同源关系。若能通过结构预测发现更广泛的同源家族，将揭示肠杆菌中一种普遍的毒力调控范式，并可能为抗菌干预提供新靶点。
- **现有方法为何不足**：VtrA 与 ToxR 的周质结构域序列相似性已低于敏感序列检测方法的置信阈值（SI Appendix, Table S1），传统 PSI-BLAST/HHsearch 无法跨家族识别同源关系。
- **精确的「Can ... ?」研究问题**：Can AlphaFold/ColabFold 结构预测识别序列已高度分化的 VtrA/VtrC 样共组分信号转导系统，并揭示其共享的脂质运载蛋白折叠？

## 04 背景与发展脉络
- **阶段一：序列同源检测**（PSI-BLAST、HHsearch）。可识别保守同源家族，但对快速进化的周质感知域失效（VtrA vs ToxR 跨家族检测失败）。
- **阶段二：实验结构解析**。VtrA/VtrC 复合物结构（5kew）揭示异源二聚体与胆汁酸结合机制；ToxR 周质域结构（6uue）已知，但 ToxS 结构未知。
- **阶段三：AI 结构预测**（AlphaFold/ColabFold）。本文利用 AlphaFold2 对 ToxS 及候选共组分进行结构建模，识别出 lipocalin 折叠，突破了序列检测的局限。
- **本文主张的位置**：在序列方法失效处，结构预测可作为同源检测的替代工具，并支持「共组分信号转导系统从共同祖先分化」的进化假说。
- **脉络核验状态**：仅本文框架（作者未系统综述该领域全部方法；本文的进化假说为作者主张，需外部验证）。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 序列同源检测失效 | VtrA 与 ToxR 周质域序列无法跨家族识别 | 周质感知域快速进化，序列分歧超过敏感检测阈值 | SI Appendix, Table S1；Results 节「evolved beyond confident sequence recognition」 |
| ToxS 结构未知 | 无法通过序列方法确认 ToxS 与 VtrC 的同源关系 | ToxS 序列与 VtrC 无显著相似性 | Results 节「sensitive sequence detection methods fail to identify a relationship between ToxS and VtrC」 |
| 候选共组分系统难以发现 | 传统方法仅能识别 HTH 输出域，无法识别周质输入组件 | 输入域序列高度分化，且部分基因未正确注释 | Results 节「Genome Neighborhoods Facilitate Discovery」；BZ17_3565 注释错误案例 |
| 进化关系无法评估 | CadC 与 VtrA 周质域序列相似性低，无法进行系统发育分析 | 序列分歧过大，无法可靠比对 | Results 节「precludes sequence-based clustering or traditional phylogenetic analysis」 |

## 06 核心思想
1. **表面方法**：以 VtrA/VtrC 序列为起点，用 PSI-BLAST 搜索细菌参考基因组；对候选序列进行跨膜螺旋预测、基因邻域分析；对候选共组分蛋白用 AlphaFold2/ColabFold 进行单体及复合物结构预测；用 DaliLite 进行结构比对与聚类。
2. **核心洞察**：尽管序列已高度分化，VtrA/VtrC 样共组分系统的周质感知组件（VtrC、ToxS、PsaF 等）共享 lipocalin 折叠，且该折叠在结构上可被 AI 方法稳定识别。这一「结构保守、序列分化」的模式提示共组分系统从共同祖先通过基因复制与快速进化分化而来，并可能普遍以脂质/胆汁酸为配体。
3. **可能的普适教训** [Analysis]：当序列同源检测失效时，AI 结构预测可作为「结构同源检测」的替代工具，尤其适用于快速进化的蛋白家族。这一思路可迁移到 TF–DNA 互作领域：对于 DNA 结合域序列高度分化的转录因子，结构预测可能帮助识别共享的 DNA 结合折叠或辅助域。

## 07 方法总览
- **输入**：V. parahaemolyticus VtrA/VtrC 序列；18 个高质量肠杆菌基因组（SI Appendix, Table S2）；NCBI 参考基因组数据库。
- **输出**：28 个跨膜锚定转录因子候选；多个候选共组分基因对；ToxS、FidL 等结构模型；共组分系统进化关系推断。
- **模块**：
  1. 序列搜索（PSI-BLAST，5 轮迭代，E-value 0.001）
  2. 跨膜螺旋预测（Phobius）
  3. 基因邻域分析（寻找共转录操纵子结构）
  4. 同源序列收集（HMMER 迭代搜索，E-value 递减 10⁻¹²→10⁻³）
  5. 结构预测（AlphaFold2/ColabFold，单体及复合物）
  6. 结构比对与聚类（DaliLite）
  7. 保守性映射（Al2Co，映射至 VtrC 结构 5kew）
- **训练**：无（使用预训练 AlphaFold2/ColabFold）。
- **反馈回路**：结构预测结果用于验证序列搜索候选；保守性分析用于推断功能位点。
- **文字流程**：VtrA/VtrC 序列 → PSI-BLAST 搜索 → 跨膜预测过滤 → 基因邻域筛选 → 候选共组分对 → HMMER 收集同源序列 → AlphaFold2 结构建模 → DaliLite 结构比对 → 保守性映射 → 进化与功能推断。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| PSI-BLAST 序列搜索 | 从参考基因组中识别 VtrA 同源序列 | 起始候选发现 | 输入：VtrA/ToxR 序列；输出：252 条候选 | Results 节「identified numerous CadC-like HTH-containing proteins」 | 移除后无法获得初始候选集（必需步骤） |
| Phobius 跨膜预测 | 过滤含跨膜螺旋的转录因子 | 筛选膜锚定 TF | 输入：候选序列；输出：28 个跨膜 TF | Results 节「filtered using TMH prediction, resulting in 28」 | 移除后可能纳入非膜蛋白，降低特异性（预期影响） |
| 基因邻域分析 | 识别共转录操纵子中的下游共组分 | 发现共组分基因对 | 输入：TF 基因位点；输出：候选共组分基因 | Results 节「inspected their gene neighborhood」；BZ17_3565 注释修正案例 | 移除后无法区分共组分与无关邻基因（必需步骤） |
| HMMER 迭代搜索 | 收集每个共组分的同源序列 | 构建多序列比对用于结构预测 | 输入：候选共组分序列；输出：同源序列集 | Methods 节「six rounds of iterative HMMER search」 | 移除后 MSA 深度不足，AlphaFold 预测精度下降（预期影响） |
| AlphaFold2/ColabFold 结构预测 | 预测共组分蛋白三维结构 | 识别共享折叠，突破序列检测局限 | 输入：MSA；输出：结构模型 | Results 节「ToxS model adopts a lipocalin-like fold」；图 2D、3A | 移除后无法确认 ToxS 与 VtrC 的结构同源性（核心贡献） |
| DaliLite 结构比对 | 量化结构相似性，生成距离矩阵 | 评估进化关系 | 输入：结构模型；输出：Z-score 距离矩阵 | Results 节「Dali Z-score 5.6」；图 5F | 移除后无法定量支持同源假说（预期影响） |
| Al2Co 保守性映射 | 将序列保守性映射至结构 | 识别功能位点 | 输入：MSA + 结构；输出：保守性着色结构 | Results 节「conserved disulfide」；图 3A、4D | 移除后无法推断功能重要性（预期影响） |

## 09 关键公式符号
- **DaliLite 距离转换**：\( D = -\ln(Z_{AB} / \min(Z_{AA}, Z_{BB})) \)
  - \( Z_{AB} \)：结构 A 与 B 的比对 Z-score
  - \( Z_{AA}, Z_{BB} \)：各自自身比对 Z-score
  - 用途：将结构相似性转换为距离，用于热图聚类（图 5F）
  - 来源：Methods 节「VtrA-Like Periplasmic Domain Heat Map」
- 其余公式：不适用（本文无其他数学公式）。

## 10 实验设计与证据链
- **数据集**：18 个肠杆菌参考基因组（SI Appendix, Table S2）；NCBI RefSeq 数据库；候选共组分序列来自 V. parahaemolyticus、V. cholerae、Y. pseudotuberculosis、S. typhimurium、E. coli、S. flexneri、B. pseudomallei 等。
- **指标**：结构预测置信度（pLDDT，文中未给具体数值）；DaliLite Z-score；HHsearch 概率（SI Appendix, Table S3）。
- **基线**：无显式基线（本文为发现性研究，非基准测试）。
- **预算**：未提供。
- **骨干/仪器**：AlphaFold2（ColabFold 实现）；DaliLite；CLANS；Phobius；HMMER。
- **oracle 输入**：VtrA/VtrC 实验结构（5kew）作为结构比对参照；VtrC 结构（5kew chain D）作为保守性映射模板。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|--------------|------------|------|--------------|-------------------|------|
| PSI-BLAST 搜索 + 跨膜过滤 | 肠杆菌中存在 VtrA 样跨膜 TF | 18 基因组，252 条候选 → 28 条跨膜 TF | 28 个候选跨膜 TF | 共组分系统在肠杆菌中广泛存在 | 未验证这些 TF 是否均参与毒力调控 | Results 节；表 1 |
| ToxS 结构预测 | ToxS 采用 lipocalin 折叠 | AlphaFold2 模型 vs VtrC 实验结构 | ToxS 模型呈 lipocalin 折叠，核心残基高置信 | ToxS 与 VtrC 结构同源 | 模型非实验结构，动态行为未知 | Results 节；图 2D |
| 候选共组分结构预测 | 各候选共享 lipocalin 折叠 | 8 个候选模型 vs VtrC | 除 SF3507、TcpH 外均呈 lipocalin 折叠 | 共组分系统共享折叠祖先 | 低置信模型（SF3507、TcpH）不能排除折叠差异 | Results 节；图 3A |
| 保守二硫键分析 | 二硫键为家族保守特征 | 序列比对 + 结构映射 | FidL、YqeJ、STM0342、STM0345、SF3507 均含保守二硫键 | 二硫键可能为功能必需 | 未做突变验证 | Results 节；图 3A |
| GrvA/FidL 复合物预测 | 复合物互作模式与 VtrA/VtrC 相似 | AlphaFold2 复合物模型 vs VtrA/VtrC 实验结构 | 预测接触面与 VtrA/VtrC 周质互作面一致 | 共组分互作模式保守 | 复合物模型未实验验证 | Results 节；图 4A |
| PsaE/PsaF、YqeI/YqeJ 共表达实验 | 候选共组分形成异源二聚体 | 共表达 + 纯化 | 形成二聚体复合物 | 共组分互作可实验验证 | 未测结合亲和力或功能 | Results 节；SI Appendix Methods |
| DaliLite 结构聚类 | 结构距离反映进化关系 | 全对全结构比对 | 距离热图显示亚家族聚类 | 结构支持共同祖先假说 | 距离阈值未明确定义 | Results 节；图 5F |

## 11 结论正确解读
- **任务范围**：本文仅覆盖肠杆菌（含 Vibrio、Yersinia、Salmonella、E. coli、Shigella、Burkholderia），不涉及其他细菌门类；仅关注共组分信号转导系统，不涵盖经典双组分系统（如 His-Asp 磷酸转移）。
- **oracle/真值输入**：VtrA/VtrC 实验结构（5kew）作为结构比对与保守性映射的参照；VtrC 的胆汁酸结合实验数据（外部文献）作为功能推断依据。
- **端到端状态**：非端到端。结构预测为计算模型，未经实验验证（除 PsaE/PsaF、YqeI/YqeJ 的共表达实验外）；ToxS 的脂质结合功能为推断，未做直接结合实验。
- **算力成本**：未提供。
- **历史数据依赖**：依赖 RefSeq 基因组注释质量；BZ17_3565 注释错误案例表明注释质量影响候选发现。
- **模型依赖**：AlphaFold2 预测置信度不均一（SF3507、TcpH 低置信）；复合物预测方法为修改版 AlphaFold，未与标准 AlphaFold-Multimer 对比。
- **最难情形**：序列高度分化且无实验结构的蛋白（如 TcpH）；预测置信度低的区域无法可靠推断功能。
- **群体/领域边界**：结论限于肠杆菌共组分系统；对 TF–DNA 结合机制本身无直接贡献。
- **不确定性**：进化关系推断基于结构相似性，但 DaliLite Z-score 处于「灰色地带」（如 CadC vs VtrA，Z=5.6），不能排除趋同进化；脂质感应功能为推断，缺乏直接配体结合证据。
- **有边界的复述**：在肠杆菌中，VtrA/VtrC 样共组分系统的周质感知组件共享 lipocalin 折叠，且该折叠可被 AlphaFold 稳定预测；这些系统可能从共同祖先分化，并可能以脂质/胆汁酸为配体调控毒力基因表达，但具体配体与激活机制尚未直接验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 结构预测置信度不均一 | SF3507、TcpH 模型低置信，无法可靠推断折叠 | 未明确提及 | Results 节「less-confident predictions」 |
| 进化关系推断处于灰色地带 | CadC 与 VtrA 结构相似性 Z-score 5.6，低于明确同源阈值 | 未明确提及 | Results 节「gray area of homology」 |
| 功能推断缺乏直接证据 | 脂质感应功能基于结构推断，未做配体结合实验 | 未明确提及 | Discussion 节「suggest that they may also function as lipid sensors」 |
| 复合物预测方法为修改版 | 修改版 AlphaFold 未与标准方法对比 | 未明确提及 | Methods 节「local adaptation of AlphaFold」 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|------------------|----------------------|----------|----------|------|
| AlphaFold 预测的 lipocalin 折叠可能为假阳性 | AlphaFold 对 β-桶状折叠有偏好，可能将非相关序列也预测为 lipocalin 折叠；低置信模型（SF3507、TcpH）尤其可疑 | 若折叠预测不可靠，则「共同祖先」假说失去结构基础 | 对候选蛋白做实验结构解析（X-ray/Cryo-EM）；或使用多种独立结构预测工具交叉验证 | Results 节「less-confident predictions」；[Analysis] 基于 AlphaFold 已知的折叠偏好 |
| 「共同祖先」假说缺乏系统发育支持 | 作者明确承认无法进行序列系统发育分析，结构相似性可能来自趋同进化（如脂质结合压力） | 若为趋同进化，则「共组分系统」可能不是单系群，功能推断需谨慎 | 收集更多中间序列，尝试结构引导的比对与系统发育；或比较不同肠杆菌中该系统的基因组邻域保守性 | Results 节「precludes sequence-based phylogenetic analysis」 |
| 功能推断（脂质感应）缺乏直接实验证据 | 保守二硫键和 lipocalin 折叠仅提示脂质结合可能，但未做配体筛选或结合实验 | 若功能推断错误，则「脂质调控毒力」的结论不成立 | 对 VtrC 同源蛋白做脂质阵列筛选、等温滴定量热（ITC）或表面等离子共振（SPR） | Discussion 节「suggest that they may also function as lipid sensors」；[Analysis] 推断语气 |
| 候选共组分系统的「功能」未验证 | 除 PsaE/PsaF、YqeI/YqeJ 的共表达实验外，未做转录激活或毒力表型实验 | 若这些系统不参与毒力调控，则「毒力调控 cassette」的命名过度推广 | 对候选系统做基因敲除 + 毒力表型分析；或做报告基因转录激活实验 | Results 节「form dimers when expressed together」；[Analysis] 功能验证缺失 |
| 复合物预测方法未与标准方法对比 | 修改版 AlphaFold 的准确性未知，GrvA/FidL 互作界面预测可能不可靠 | 若互作界面预测错误，则「互作模式保守」的结论不成立 | 用 AlphaFold-Multimer 或 RoseTTAFold 重新预测；或做交联质谱验证 | Methods 节「local adaptation of AlphaFold」；[Analysis] 方法未基准化 |

## 14 学到什么
**Agent 提炼的知识候选**
1. **结构同源检测策略**：当序列同源检测失效时，AI 结构预测（AlphaFold/ColabFold）可作为替代工具。迁移到 TF–DNA 互作：对于 DNA 结合域序列高度分化的转录因子（如某些细菌 TF），可先预测结构，再与已知 TF 结构比对，识别共享折叠。
2. **基因邻域 + 结构预测联合策略**：利用操纵子结构（共转录、基因重叠）辅助发现功能关联蛋白。迁移：在真核生物中可类比为共表达或共调控基因模块，辅助识别 TF 的辅助因子。
3. **保守二硫键作为功能标记**：在快速进化蛋白中，二硫键位置可能比序列更保守，可作为功能位点标记。迁移：在 TF 中可关注保守的半胱氨酸残基，可能参与氧化还原调控或结构稳定。
4. **结构比对距离矩阵**：DaliLite Z-score 转换距离矩阵用于聚类，可量化结构相似性。迁移：可用于 TF 家族的结构分类，识别序列不相似但结构相似的 DNA 结合域。
5. **「灰色地带」同源判断**：Z-score 处于临界值（如 5.6）时，作者谨慎处理，不强行下结论。迁移：在 TF 同源判断中，应明确区分「确定同源」「灰色地带」「趋同进化」三种情况。
6. **复合物预测的链间处理**：通过修改 AlphaFold 位置编码（加 200 表示链间断）实现复合物建模。迁移：可用于预测 TF 二聚化界面或 TF–辅助因子互作界面。

## 15 与已有知识连接
- **VtrA/VtrC 原始发现**：Kinch 等此前报道 VtrA/VtrC 感知胆汁酸并调控 V. parahaemolyticus T3SS2（PNAS 2022 本文为扩展；原始结构见 5kew，PDB）。
- **ToxR/ToxS 经典系统**：ToxR 是霍乱弧菌毒力调控主开关，ToxS 为其周质辅助蛋白（Miller et al., Science 1987；本文将其归入同一超家族）。
- **CadC 系统**：大肠杆菌 CadC 是赖氨酸脱羧酶途径的调控因子，含周质感知域（本文将其与 VtrA 结构比较，Z-score 5.6）。
- **AlphaFold 方法**：Jumper et al., Nature 2021；本文使用 ColabFold（Mirdita et al., Nat Methods 2022）实现。
- **lipocalin 折叠**：经典脂质运载蛋白家族（如 retinol-binding protein），本文将其扩展到细菌信号转导。
- **与 TF–DNA 互作课题的关联**：本文的 TF（VtrA、ToxR）含 HTH DNA 结合域，但其 DNA 结合机制未研究。可迁移的是「结构预测辅助同源检测」的方法论，而非具体的 DNA 结合机制。候选方向：用类似策略寻找其他细菌中序列分化的 TF–DNA 结合域。

## 16 研究想法
**Agent 生成的研究候选**
1. **候选名称**：TF–DNA 结合域的结构同源普查
   - **来源局限/观察**：本文展示了序列检测失效时结构预测可识别同源蛋白；TF 的 DNA 结合域同样存在序列快速进化的情况。
   - **核心假设**：细菌中大量未注释的 HTH 蛋白与已知 TF 共享 DNA 结合折叠，但序列相似性低于检测阈值。
   - **增量**：将本文的「结构同源检测」策略系统应用于 TF–DNA 结合域，构建结构引导的 TF 家族分类。
   - **初步方法**：收集所有含 HTH 域的细菌蛋白 → AlphaFold 批量预测 → 与已知 TF–DNA 复合物结构比对 → 聚类。
   - **验证方式**：对预测的新家族成员做 EMSA 或 SELEX 验证 DNA 结合活性。
   - **创新状态**：unverified（需验证 AlphaFold 对 DNA 结合域的预测精度）。

2. **候选名称**：共组分系统的配体筛选
   - **来源局限/观察**：本文推断脂质感应但未做配体实验。
   - **核心假设**：新发现的 VtrC 样蛋白（FidL、YqeJ 等）结合特定脂质或胆汁酸，且配体特异性决定下游 TF 激活。
   - **增量**：将结构预测与配体筛选结合，建立「结构-配体-功能」映射。
   - **初步方法**：表达候选 VtrC 样蛋白 → 脂质阵列筛选 → ITC 验证 → 突变关键残基 → 报告基因实验。
   - **验证方式**：配体结合与转录激活的相关性。
   - **创新状态**：unverified。

3. **候选名称**：TF 周质感知域的构象变化模拟
   - **来源局限/观察**：本文仅做静态结构预测，未研究配体结合后的构象变化。
   - **核心假设**：VtrC 样 lipocalin 结合配体后发生构象变化，通过跨膜螺旋传递至胞内 HTH 域。
   - **增量**：将 MD 模拟引入共组分系统，研究信号转导的动态机制。
   - **初步方法**：以 VtrC 结构为起点 → 配体对接 → MD 模拟（μs 级）→ 分析周质域与跨膜域的相对运动。
   - **验证方式**：MD 预测的构象变化与突变实验对比。
   - **创新状态**：unverified（需先获得可靠的 VtrC 配体结合态结构）。

4. **候选名称**：TF–DNA 结合域与感知域的共进化分析
   - **来源局限/观察**：本文发现输出域（HTH）保守而输入域（周质感知）快速进化。
   - **核心假设**：在共组分系统中，DNA 结合域与感知域的进化速率差异反映功能约束差异；感知域进化快可能对应配体多样性。
   - **增量**：将进化分析从单个蛋白扩展到双基因 cassette。
   - **初步方法**：对本文发现的 cassette 做共进化分析（dN/dS、协变分析）→ 与结构预测结合 → 识别共进化残基对。
   - **验证方式**：共进化残基对是否位于互作界面。
   - **创新状态**：unverified。

5. **候选名称**：AI 结构预测在 TF 同源检测中的基准测试
   - **来源局限/观察**：本文未系统评估 AlphaFold 在「序列分歧大但结构保守」场景下的检测灵敏度。
   - **核心假设**：AlphaFold 的 pLDDT 和 PAE 可作为同源检测的定量指标，优于序列比对。
   - **增量**：建立基准数据集，量化结构预测在同源检测中的灵敏度/特异性。
   - **初步方法**：收集已知同源但序列分歧大的 TF 对 → AlphaFold 预测 → 比较 pLDDT/结构比对 Z-score 与序列一致性的关系。
   - **验证方式**：与实验结构比对，计算结构同源性判定的准确率。
   - **创新状态**：unverified（需构建基准数据集）。