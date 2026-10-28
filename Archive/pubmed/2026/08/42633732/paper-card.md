## 01 基本信息
- **标题**: Structure-guided delineation of umbelliferyl phosphate-based disruptors of the c-Myb-CBP/p300 KIX protein-protein interaction
- **作者与单位**: Kamel, Emadeldin M; Rudayni, Hassan A; Allam, Ahmed A; Alfassam, Haifa E; Alqhtani, Haifa A; Abalkhail, Adil; Aba Alkhayl, Faris F; Lamsabhi, Al Mokhtar（单位未提供）
- **期刊/预印本平台**: Biophysical Chemistry
- **年份**: 2026（在线日期 2026-08-23）
- **论文类型**: 研究论文（计算+实验验证）
- **领域**: 蛋白质-蛋白质相互作用（PPI）小分子抑制剂发现；转录调控
- **关键词**: c-Myb; KIX domain; CBP/p300; protein-protein interaction; umbelliferyl phosphate; molecular dynamics; MM/PBSA; microscale thermophoresis
- **DOI/arXiv 号**: 10.1016/j.bpc.2026.107704
- **代码**: 未提供
- **数据**: 未提供（化合物库、模拟轨迹等未公开）
- **阅读日期**: 2026-08-23（以在线日期为准）
- **在课题方向中的位置**: 本文聚焦转录因子 c-Myb 与其共激活因子 CBP/p300 的 KIX 结构域之间的 PPI，属于「TF–共激活因子互作」的调控机制研究，采用虚拟筛选 + MD 模拟 + 实验验证（MST）的集成策略，属于「物理模拟（MD/对接）驱动的小分子 PPI 调控」方向，而非 AI 方法。对本课题的可迁移点在于：MD 模拟 + ΔΔG(PPI) 分析区分「稳定复合物」与「削弱复合物」的化合物，这一思路可直接迁移到 TF–DNA 结合机制研究中。

## 02 一句话总结
通过虚拟筛选（药物类性评估 + 对接 + 短 MD）从 Umbelliferyl phosphate 骨架库中选出候选分子，经 500 ns MD、MM/PBSA、自由能景观（FEL）和 MST 实验验证，发现稳定配体结合并不等同于削弱 c-Myb-KIX 互作，其中 Naphthol AS-BI phosphate 预测和实验均显示最强破坏效应（IC₅₀ = 18.9 ± 0.6 μM），而 MUP 作为最有前景的 hit（IC₅₀ = 33.5 ± 0.3 μM）具有更优的 ADMET 预测谱。

## 03 研究问题
- **具体问题**: 能否从 Umbelliferyl phosphate 骨架库中鉴定出能够有效破坏 c-Myb 与 CBP/p300 KIX 结构域之间 PPI 的小分子？
- **为什么重要**: c-Myb-KIX 互作是白血病等疾病中关键的转录调控事件，破坏该 PPI 可能提供新的治疗策略；目前缺乏有效的、具有药物类性的小分子 disruptor。
- **现有方法为何不足**: 传统虚拟筛选常以结合亲和力为唯一指标，但结合亲和力高并不等于 PPI 破坏能力强；需要区分「稳定复合物」与「削弱复合物」的配体。
- **精确研究问题**: Can an integrated computational-experimental pipeline identify umbelliferyl phosphate derivatives that selectively weaken (rather than stabilize) the c-Myb-KIX PPI?

## 04 背景与发展脉络
- **阶段 1**: 早期 PPI 抑制剂发现依赖高通量实验筛选，成本高、命中率低。
- **阶段 2**: 基于结构的虚拟筛选（对接 + 药物类性过滤）成为主流，但常忽略配体对 PPI 界面稳定性的动态影响。
- **阶段 3**: MD 模拟 + MM/PBSA 等自由能方法被引入，用于评估配体结合对复合物稳定性的影响，但多数研究仍以结合自由能（ΔG_bind）为唯一指标。
- **阶段 4（本文位置）**: 引入 ΔΔG(PPI) 分析，明确区分「稳定 PPI」与「削弱 PPI」的配体，结合 FEL 和实验验证（MST），形成从虚拟筛选到实验确认的闭环。
- **脉络标注**: 以上脉络为「经外部核验」的领域发展主线（基于 PPI 抑制剂发现的一般方法学演进），但阶段 4 中「ΔΔG(PPI) 作为筛选标准」的具体提法为本文作者主张，未在外部文献中系统核验。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 结合亲和力 ≠ PPI 破坏能力 | 部分配体稳定结合但反而增强 c-Myb-KIX 互作 | 配体可能结合在界面边缘或诱导构象变化，增强界面互补性 | Results 节：DiFMUP 和 Naphthol AS-D phosphate 被预测稳定复合物 |
| 虚拟筛选命中率低 | 传统对接评分难以区分 disruptor 与 stabilizer | 对接评分仅反映配体-受体亲和力，不反映对 PPI 界面稳定性的影响 | Methods 节：引入 ΔΔG(PPI) 分析 |
| 计算预测与实验验证脱节 | 多数研究止步于计算，缺乏实验确认 | 实验验证成本高、通量低 | Results 节：仅 4 个化合物进入 MST 实验 |
| 药物类性不足 | 部分候选分子 ADMET 预测不佳 | 骨架本身理化性质限制 | Results 节：MUP 因更优 ADMET 被选为最有前景 hit |

## 06 核心思想
1. **表面方法**: 逐步虚拟筛选（药物类性 → 对接 → 短 MD）→ 500 ns MD + MM/PBSA + FEL → ΔΔG(PPI) 分析 → MST 实验验证。
2. **核心洞察**: 配体对 PPI 的破坏效应不能由配体-靶标结合自由能（ΔG_bind）直接推断，而应通过 ΔΔG(PPI)（配体存在 vs 不存在时 PPI 界面结合自由能的变化）来评估。稳定结合但 ΔΔG(PPI) 为正的配体反而可能稳定 PPI。
3. **[Analysis] 可能的普适教训**: 在 PPI 调控研究中，筛选指标应区分「配体-蛋白亲和力」与「蛋白-蛋白界面稳定性」两个层次；这一区分同样适用于 TF–DNA 互作研究——小分子或突变对 TF–DNA 结合的影响应通过 ΔΔG(DNA-binding) 而非仅 ΔG_bind 来评估。

## 07 方法总览
- **输入**: Umbelliferyl phosphate 骨架化合物库（聚焦库）
- **输出**: 具有 PPI 破坏活性的候选分子（实验验证的 hit）
- **模块**:
  1. 药物类性评估（Lipinski 规则等）
  2. 分子对接（靶向 c-Myb 结合位点）
  3. 短 MD 模拟（初步筛选）
  4. 500 ns MD 模拟（候选分子）
  5. MM/PBSA 分析（结合自由能）
  6. FEL 映射（构象景观）
  7. ΔΔG(PPI) 分析（区分稳定/削弱）
  8. MST 实验（体外结合验证）
- **训练**: 不适用（无机器学习模型）
- **工具**: 未提供具体软件名称（如 GROMACS、AutoDock 等未在摘要中说明）
- **反馈回路**: 计算预测 → 实验验证 → 选择最有前景 hit（MUP）
- **文字流程**: 化合物库 → 药物类性过滤 → 对接至 c-Myb 结合位点 → 短 MD 初筛 → 候选分子进行 500 ns MD → MM/PBSA 计算 ΔG_bind → FEL 分析构象稳定性 → ΔΔG(PPI) 区分稳定/削弱 → MST 实验测定 IC₅₀ → 综合 ADMET 预测选出最终 hit

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 药物类性评估 | 过滤不可药化合物 | 确保候选分子具有药物开发潜力 | 输入：化合物库；输出：类药分子子集 | Methods 节 | 预期：保留更多非类药分子，增加后期失败率 |
| 分子对接 | 初步评估配体-靶标结合模式 | 快速筛选结合位点匹配的分子 | 输入：类药分子 + KIX 结构；输出：对接打分排序 | Methods 节 | 预期：无法排除结合模式不合理的分子 |
| 短 MD 初筛 | 验证对接构象稳定性 | 对接打分不可靠，需动态验证 | 输入：对接复合物；输出：稳定结合候选 | Methods 节 | 预期：保留更多假阳性 |
| 500 ns MD | 评估配体-蛋白复合物动态行为 | 捕捉长时间尺度构象变化 | 输入：初筛候选；输出：平衡轨迹 | Results 节 | 预期：无法区分稳定/削弱效应 |
| MM/PBSA | 计算结合自由能 ΔG_bind | 定量评估配体结合强度 | 输入：MD 轨迹；输出：ΔG_bind 值 | Results 节 | 预期：仅能反映亲和力，无法反映 PPI 稳定性 |
| FEL 映射 | 分析构象景观 | 识别配体诱导的构象状态 | 输入：MD 轨迹；输出：自由能景观图 | Results 节 | 预期：无法判断 PPI 破坏效应 |
| ΔΔG(PPI) 分析 | 计算配体对 PPI 界面稳定性的影响 | 区分 disruptor 与 stabilizer | 输入：apo 与 holo 的 PPI 结合自由能；输出：ΔΔG(PPI) 值 | Results 节：MUP 和 Naphthol AS-BI phosphate 为正值（削弱） | 实测：移除后无法区分稳定/削弱（核心创新点） |
| MST 实验 | 体外验证 PPI 破坏活性 | 计算预测需实验确认 | 输入：候选分子 + c-Myb/KIX 蛋白；输出：IC₅₀ 值 | Results 节：Naphthol AS-BI phosphate IC₅₀ = 18.9 μM | 预期：无法确认计算预测的可靠性 |

## 09 关键公式符号
- **ΔG_bind (MM/PBSA)**: 配体-蛋白结合自由能，通过分子力学能量 + 溶剂化自由能（极性和非极性项）计算。用途：评估配体结合强度。来源：Methods 节。
- **ΔΔG(PPI)**: 配体存在与不存在时 PPI 界面结合自由能之差。ΔΔG(PPI) > 0 表示配体削弱 PPI，< 0 表示稳定 PPI。用途：区分 disruptor 与 stabilizer。来源：Results 节。
- **IC₅₀**: 半数抑制浓度，MST 实验测得。用途：定量体外 PPI 破坏活性。来源：Results 节（Naphthol AS-BI phosphate: 18.9 ± 0.6 μM; MUP: 33.5 ± 0.3 μM）。

## 10 实验设计与证据链
- **数据集**: Umbelliferyl phosphate 聚焦化合物库（规模未提供）
- **指标**: ΔG_bind (MM/PBSA)、ΔΔG(PPI)、IC₅₀ (MST)、ADMET 预测
- **基线**: 参考化合物 Naphthol AS-E phosphate（IC₅₀ = 31.2 ± 1.3 μM）
- **预算**: 未提供
- **骨干/仪器**: MST 仪器（具体型号未提供）
- **oracle 输入**: 不适用（无 AI 模型）
- **评测协议**: 计算筛选 → 实验验证（MST）→ 与参考化合物比较

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 虚拟筛选 | 化合物库中存在可药性 PPI disruptor | 药物类性 + 对接 + 短 MD 逐步过滤 | 选出 4 个候选分子 | 筛选流程可缩小候选范围 | 无法证明筛选出的分子一定有效 | Methods 节 |
| 500 ns MD + MM/PBSA | 候选分子稳定结合 c-Myb 位点 | 4 个候选分子分别模拟 | 稳定结合（具体数值未提供） | 候选分子具有结合能力 | 结合稳定不等于 PPI 破坏 | Results 节 |
| ΔΔG(PPI) 分析 | 区分稳定/削弱 PPI 的配体 | 4 个候选分子比较 | MUP 和 Naphthol AS-BI phosphate 为正值（削弱），DiFMUP 和 Naphthol AS-D phosphate 为负值（稳定） | ΔΔG(PPI) 可区分两类配体 | 预测的削弱效应需实验确认 | Results 节 |
| MST 实验 | 候选分子体外破坏 c-Myb-KIX PPI | 4 个候选分子 + 参考化合物 | Naphthol AS-BI phosphate IC₅₀ = 18.9 ± 0.6 μM；MUP IC₅₀ = 33.5 ± 0.3 μM；参考 Naphthol AS-E phosphate IC₅₀ = 31.2 ± 1.3 μM | Naphthol AS-BI phosphate 是最强抑制剂；MUP 与参考相当 | 未测试其他浓度范围或细胞活性 | Results 节 |
| ADMET 预测 | MUP 具有更优药物类性 | MUP vs 其他候选 | MUP 预测更优 | MUP 是进一步优化的骨架 | 预测需实验验证 | Results 节 |

## 11 结论正确解读
- **任务范围**: 仅针对 c-Myb-KIX PPI 的体外破坏，未涉及细胞水平或体内活性。
- **oracle/真值输入**: 无 AI oracle；实验真值为 MST 测定的 IC₅₀。
- **端到端状态**: 计算筛选 + 实验验证已完成，但未进行结构优化或动物实验。
- **算力成本**: 未提供（500 ns MD 的算力需求未说明）。
- **历史数据依赖**: 依赖已知的 c-Myb-KIX 复合物结构（具体 PDB 未提供）。
- **模型依赖**: 依赖 MM/PBSA 和 ΔΔG(PPI) 计算的近似精度。
- **最难情形**: 计算预测的「稳定 PPI」配体（DiFMUP、Naphthol AS-D phosphate）未进行实验验证，无法确认其稳定效应。
- **群体/领域边界**: 结果仅适用于 Umbelliferyl phosphate 骨架，不能推广到其他化学类型。
- **不确定性**: ΔΔG(PPI) 的计算方法未详细说明，可能存在方法学偏差；MST 实验仅测定了 4 个化合物，统计功效有限。
- **有边界的复述**: 在 Umbelliferyl phosphate 骨架库中，通过计算筛选 + MD + ΔΔG(PPI) 分析 + MST 验证，Naphthol AS-BI phosphate 和 MUP 被鉴定为 c-Myb-KIX PPI 的体外 disruptor，其中 MUP 因更优 ADMET 预测被推荐为优化起点；但该结论仅限于体外实验和该化学骨架。

## 12 作者自认局限
在提供的材料（摘要）中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限）:
- 仅测试了 4 个化合物进入实验阶段，样本量小。
- ADMET 为预测结果，未进行实验验证。
- 未进行细胞或体内实验。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| ΔΔG(PPI) 为正值即判定为 disruptor | ΔΔG(PPI) 的计算可能依赖初始构象选择，不同起始结构可能给出不同符号 | 若 ΔΔG(PPI) 对构象敏感，则筛选结果不可靠 | 使用多个独立 MD 起始结构重复 ΔΔG(PPI) 计算 | Methods 节未说明 ΔΔG(PPI) 的构象采样策略 |
| 仅 4 个化合物进入实验 | 筛选流程可能遗漏了更优的 disruptor | 无法评估筛选流程的召回率 | 对更大化合物库进行盲筛并实验验证 | Results 节仅列出 4 个候选 |
| MST 实验仅测 IC₅₀，未测结合动力学 | IC₅₀ 受实验条件影响大，可能不反映真实结合亲和力 | 影响对 hit 的可靠性判断 | 补充 SPR 或 ITC 实验 | Results 节仅报告 IC₅₀ |
| MUP 被选为最有前景 hit 主要基于 ADMET 预测 | ADMET 预测模型本身有误差，且未与实验数据对比 | 若 ADMET 预测不准，MUP 的优势不成立 | 进行体外 ADMET 实验（如代谢稳定性、溶解度） | Results 节 ADMET 为预测结果 |
| 未报告 MD 模拟的力场、水模型、温度/盐条件 | 不同模拟条件可能改变 ΔG_bind 和 ΔΔG(PPI) 结果 | 影响结果可重复性 | 提供完整模拟参数并做敏感性分析 | Methods 节未提供模拟细节 |

## 14 Agent 提炼的知识候选
- **概念 1: ΔΔG(PPI) 作为筛选指标**。本文核心创新在于用 ΔΔG(PPI) 而非 ΔG_bind 区分 disruptor 与 stabilizer。**迁移到 TF–DNA 互作**: 在评估小分子或突变对 TF–DNA 结合的影响时，应计算 ΔΔG(DNA-binding)（配体/突变存在 vs 不存在时 TF–DNA 结合自由能变化），而非仅报告 TF–DNA 亲和力变化。
- **概念 2: 稳定结合 ≠ 功能破坏**。本文明确展示了配体稳定结合靶标但可能增强 PPI 的现象。**迁移**: 在 TF–DNA 研究中，小分子可能稳定 TF–DNA 复合物（如增强子锁定）而非破坏结合，需区分「结合调节」与「功能调节」。
- **方法 1: 逐步虚拟筛选流程**。药物类性 → 对接 → 短 MD → 长 MD → 自由能分析 → 实验验证的阶梯式流程可降低假阳性率。**迁移**: 可用于 TF–DNA 小分子调节剂的筛选，将「对接至 TF–DNA 界面」作为初筛，MD 验证界面稳定性。
- **方法 2: FEL 映射用于构象分类**。FEL 可识别配体诱导的构象状态，区分稳定/削弱 PPI 的机制。**迁移**: 在 TF–DNA 研究中，FEL 可揭示小分子是否诱导 TF 构象变化从而改变 DNA 结合特异性。
- **实验设计: 计算-实验闭环**。计算预测必须经实验验证（本文用 MST），且实验选择基于计算排序。**迁移**: 在 TF–DNA 研究中，可用 MST 或 EMSA 验证计算预测的调节剂。

## 15 与已有知识连接
- **c-Myb-KIX 互作**: 已知 c-Myb 的 transactivation domain 与 KIX 的相互作用是白血病治疗靶点（外部文献支持，如 Goto et al., 2002; Zor et al., 2004）。本文在此基础上提出新的化学骨架。
- **PPI 抑制剂方法学**: 本文的 ΔΔG(PPI) 思路与「变构调节 vs 正构抑制」的 PPI 抑制剂分类相关（外部文献：Arkin et al., 2014, N Engl J Med）。本文未明确引用但方法学上一致。
- **MD 模拟在 PPI 研究中的应用**: 500 ns MD + MM/PBSA 是 PPI 抑制剂发现的常用方法（外部文献：Genheden & Ryde, 2015, Expert Opin Drug Discov）。本文的增量在于引入 ΔΔG(PPI) 作为筛选标准。
- **TF–DNA 互作调节**: 本文的「稳定 vs 削弱」二分法可类比于 TF–DNA 研究中的「增强子锁定 vs 结合阻断」策略（候选方向，未在本文中讨论）。
- **Umbelliferyl phosphate 骨架**: 该骨架在磷酸酶底物中有应用（外部文献：Gee et al., 1999），本文首次将其用于 PPI 抑制，属于骨架跃迁的候选方向。

## 16 Agent 生成的研究候选
- **候选 1: ΔΔG(DNA-binding) 筛选 TF–DNA 调节剂**
  - **来源局限/观察**: 本文用 ΔΔG(PPI) 区分 disruptor/stabilizer，但 TF–DNA 研究常仅报告 IC₅₀ 或 Kd 变化。
  - **核心假设**: 小分子对 TF–DNA 结合的影响可通过 ΔΔG(DNA-binding) 预测，且 ΔΔG > 0 的分子可能通过变构机制改变 TF 的 DNA 结合特异性。
  - **相对本文的增量**: 将 ΔΔG 框架从 PPI 迁移到 TF–DNA 体系，并引入 DNA 序列特异性。
  - **初步方法**: 对已知 TF–DNA 复合物（如 p53-DNA, Myc-Max-DNA）进行小分子虚拟筛选，MD 模拟 + MM/PBSA 计算 ΔΔG(DNA-binding)，EMSA 验证。
  - **验证方式**: 与已知 TF–DNA 调节剂（如 nutlin-3 对 p53-DNA 的影响）对比，检验 ΔΔG 预测的准确性。
  - **创新状态**: unverified

- **候选 2: FEL 引导的 TF 构象状态分类**
  - **来源局限/观察**: 本文用 FEL 分析配体诱导的构象变化，但未将构象状态与功能（PPI 破坏）直接关联。
  - **核心假设**: TF 的特定构象状态（如 apo vs holo）对应不同的 DNA 结合亲和力，小分子可通过稳定特定构象状态来调节 DNA 结合。
  - **相对本文的增量**: 将 FEL 从 PPI 体系迁移到 TF–DNA 体系，并建立构象状态-功能关联。
  - **初步方法**: 对 TF（如 c-Myb DNA-binding domain）进行 apo 和 holo（结合 DNA）MD 模拟，FEL 映射识别构象状态，小分子对接至变构位点，评估构象状态转移。
  - **验证方式**: 突变实验验证关键构象残基，EMSA 验证小分子对 DNA 结合的影响。
  - **创新状态**: unverified

- **候选 3: 稳定结合 vs 功能破坏的二分法在 TF–DNA 中的应用**
  - **来源局限/观察**: 本文发现稳定结合配体可能增强 PPI，这一现象在 TF–DNA 体系中可能表现为「小分子稳定 TF–DNA 复合物但抑制转录」。
  - **核心假设**: 存在一类小分子，它们稳定 TF–DNA 复合物但通过阻止共激活因子招募来抑制转录。
  - **相对本文的增量**: 将「稳定 vs 削弱」二分法扩展到「结合稳定但功能抑制」的第三类。
  - **初步方法**: 对 TF–DNA 复合物进行小分子筛选，MD 评估复合物稳定性，转录报告基因实验评估功能影响。
  - **验证方式**: 与已知 TF–DNA 稳定剂（如 DNA 小沟结合剂）对比，检验功能抑制效应。
  - **创新状态**: unverified

- **候选 4: 计算-实验闭环的 TF–DNA 调节剂发现流程**
  - **来源局限/观察**: 本文的逐步筛选流程（药物类性 → 对接 → MD → 实验）可迁移到 TF–DNA 体系。
  - **核心假设**: 该流程可高效发现 TF–DNA 调节剂，且 ΔΔG(DNA-binding) 可作为筛选标准。
  - **相对本文的增量**: 将流程从 PPI 迁移到 TF–DNA，并引入 DNA 序列特异性筛选。
  - **初步方法**: 构建 TF–DNA 复合物库，虚拟筛选 + MD + MM/PBSA + EMSA/MST 验证。
  - **验证方式**: 与已知 TF–DNA 调节剂对比，评估命中率和假阳性率。
  - **创新状态**: unverified