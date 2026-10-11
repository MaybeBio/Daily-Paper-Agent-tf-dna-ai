## 01 基本信息
- **标题**：Targeting a Leukemia-Relevant Protein-Protein Interface: N-Aryl Anthranilic Acids as Disruptors of the c-Myb-CBP/p300 KIX Interaction
- **作者与单位**：Alfassam, Haifa E; Kamel, Emadeldin M; Othman, Sarah I; Alharbi, Hanan M; Rudayni, Hassan A; Allam, Ahmed A; Lamsabhi, Al Mokhtar（单位未在摘要中提供）
- **期刊/预印本平台**：Chemical Biology & Drug Design
- **年份**：2026-10-08（在线日期）
- **论文类型**：研究论文（计算-实验联合）
- **领域**：药物化学、蛋白质-蛋白质相互作用（PPI）抑制、转录调控、急性髓系白血病（AML）
- **关键词**：c-Myb、KIX、PPI disruptor、N-aryl anthranilic acid、虚拟筛选、MD模拟、MM/PBSA、微尺度热泳（MST）
- **DOI/arXiv 号**：10.1111/cbdd.70415
- **代码**：未提供
- **数据**：未提供（PDB 2AGH 为公开结构）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA互作（聚焦TF–DNA结合机制）× 物理模拟/AI」方向中的**PPI小分子调控**分支。研究对象为转录因子c-Myb与其共激活因子CBP/p300的KIX结构域之间的蛋白-蛋白界面（而非TF直接与DNA的结合），但该界面是c-Myb转录激活功能的关键下游事件。方法上采用虚拟筛选（对接）+ MD模拟 + MM/PBSA + FEL + ADMET的计算流程，并以MST实验验证，属于典型的计算-实验闭环策略，其「结合亲和力≠PPI破坏力」的核心发现对TF-DNA/共激活因子界面的药物设计具有直接借鉴意义。

## 02 一句话总结
本文通过虚拟筛选（对接+MD+MM/PBSA+FEL+ADMET）从3656个N-aryl anthranilic acid衍生物中筛选出4个候选化合物，并用MST实验验证，发现C3（IC₅₀=16.5±0.8 μM）是最强的c-Myb-KIX PPI破坏剂，优于参考抑制剂Naphthol AS-E phosphate（28.8±3.1 μM），同时揭示配体结合亲和力与PPI破坏能力并不直接相关。

## 03 研究问题
- **具体问题**：能否从N-aryl anthranilic acid骨架库中鉴定出能够破坏c-Myb与CBP/p300 KIX结构域之间蛋白-蛋白相互作用的小分子？
- **为什么重要**：c-Myb是造血干细胞增殖和分化的重要转录因子，在AML中高度依赖c-Myb活性；破坏c-Myb-KIX相互作用可抑制AML致癌转化，是治疗AML的潜在策略。
- **现有方法不足**：TF-共激活因子界面通常面积大、平坦、疏水，传统小分子难以有效靶向；已有抑制剂（如Naphthol AS-E phosphate）活性有限，且缺乏系统性的计算-实验联合筛选策略。
- **精确研究问题**：Can structure-based virtual screening combined with MD/MM-PBSA analysis identify N-aryl anthranilic acid derivatives that disrupt the c-Myb-KIX PPI in vitro?

## 04 背景与发展脉络
*注：以下脉络基于本文引用和框架，标注为「仅本文框架」；未做外部文献核验。*

1. **c-Myb生物学发现阶段**：c-Myb被鉴定为造血基因表达的核心调控因子，其转录激活依赖招募共激活因子CBP/p300（Thakur et al. 2014; Ledsaak et al. 2016）。
2. **AML治疗靶点确立阶段**：遗传学证据表明AML细胞高度依赖MYB活性，破坏c-Myb-p300相互作用可抑制AML致癌转化（Pattabiraman et al. 2014; Schmidt and Klempnauer 2022; Yusenko et al. 2021）。
3. **结构解析阶段**：KIX结构域被解析为三螺旋束，c-Myb以弯曲两亲性螺旋结合于α1/α3疏水沟槽，Leu302是关键残基（De Guzman et al. 2006）；三元复合物结构（PDB 2AGH）显示c-Myb和MLL同时结合KIX的两个不同面，为靶向c-Myb面提供了结构基础。
4. **小分子干预概念验证阶段**：Naphthol AS-E phosphate被报道为首个低分子量c-Myb-KIX抑制剂（Uttarkar et al. 2015），后续有肽模拟物（MYBMIM）和双位点配体（MybLL-tide）等（Ramaswamy et al. 2018）。
5. **本文位置**：在概念验证基础上，采用系统化计算-实验联合工作流，从N-aryl anthranilic acid骨架出发，通过多级筛选（理化过滤→对接→MD→MM/PBSA→FEL→ADMET）→MST验证，旨在发现结构新颖、活性更优的PPI破坏剂，并建立「结合≠破坏」的方法学认知。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PPI界面难以成药 | c-Myb-KIX界面面积大（~1500-3000 Å²）、平坦、疏水，传统小分子难以高亲和力结合 | PPI界面缺乏深口袋，结合自由能分散 | Introduction 第3段 |
| 结合亲和力≠功能破坏 | C1结合最强（ΔG_total=-28.18 kcal/mol）却是最弱抑制剂（IC₅₀=99.6 μM）；C3结合最弱（-17.50 kcal/mol）却是最强抑制剂（IC₅₀=16.5 μM） | 配体可能通过稳定而非破坏PPI构象发挥作用；破坏力取决于对界面能量平衡的扰动方式 | Results 表4、图8；Discussion |
| 浅沟槽结合模式难以稳定 | KIX的α1/α3沟槽浅且开放，配体易脱落 | 缺乏深口袋锚定，结合主要依赖疏水堆积和少量极性接触 | Results 图3、图6 |
| 计算预测与实验活性排序不一致 | 对接分数/结合能排序与MST的IC₅₀排序不完全一致 | 静态对接无法捕捉构象重排和动力学效应；MM/PBSA未含熵贡献 | Results 表1、表4、图8 |
| 参考抑制剂活性有限 | Naphthol AS-E phosphate IC₅₀=28.8±3.1 μM | 结构简单、缺乏优化 | Results 图8B |
| 毒性预测风险 | 所有化合物均预测为阳性：DILI、肾毒性、神经毒性、呼吸毒性 | 骨架本身的固有毒性倾向 | Results 表5 |

## 06 核心思想
1. **表面方法**：一个「漏斗式」多级虚拟筛选流程——3656个N-aryl anthranilic acid衍生物 → 理化性质/药物相似性过滤 → AutoDock Vina对接至KIX α1/α3沟槽 → 短MD验证对接姿势稳定性 → 500 ns长MD + MM/PBSA重打分 → FEL分析 → ADMET过滤 → 4个候选 → MST实验验证。

2. **核心洞察**：**PPI破坏剂的效力不取决于配体-蛋白结合亲和力，而取决于配体对蛋白-蛋白界面能量平衡的扰动方式**。C3虽然对KIX的结合最弱（ΔG_total=-17.50 kcal/mol），但通过改变界面构象重排（ΔΔG_PPI=+4.57 kcal/mol）实现了最强的PPI破坏；C1虽然结合最强（-28.18 kcal/mol），却稳定了PPI（ΔΔG_PPI=-6.47 kcal/mol）。这提示在PPI药物筛选中，应关注「界面扰动能力」而非单纯的「结合强度」。

3. **可能的普适教训** [Analysis]：在TF-共激活因子或TF-DNA界面的药物设计中，计算筛选的排序指标不应仅依赖对接分数或结合自由能，而应引入「对界面稳定性的差分效应」（如ΔΔG_PPI）作为关键排序依据。这一思路可迁移到其他转录因子复合物的抑制剂发现中。

## 07 方法总览
- **输入**：3656个N-aryl anthranilic acid衍生物（结构库）；KIX结构域（PDB 2AGH，小鼠来源，与人类序列100%一致）
- **输出**：4个候选化合物（C1-C4）的预测结合模式、PPI扰动效应、ADMET谱，以及MST实验验证的IC₅₀值
- **模块**：
  1. 药物相似性过滤（MW, cLogP/logD, TPSA, HBD/HBA, 可旋转键, PAINS/反应性基团排除）
  2. AutoDock Vina对接（刚性受体，柔性配体，exhaustiveness=16，3次独立运行，聚类分析）
  3. 短MD验证（评估对接姿势稳定性）
  4. 500 ns MD生产模拟（GROMACS 2022.4, CHARMM36m力场, TIP3P水模型, CGenFF配体参数）
  5. MM/PBSA重打分（gmx_MMPBSA v1.6.3，取400-500 ns轨迹）
  6. ΔΔG_PPI分析（配体结合前后c-Myb-KIX界面结合能变化）
  7. FEL分析（PCA + 自由能地形图）
  8. ADMET预测（ADMETlab 3.0）
  9. MST实验验证（eGFP/hc-Myb(241-390) + p300(1-672)）
- **反馈回路**：计算预测（ΔΔG_PPI排序）→ MST实验验证 → 实验与计算交叉确认
- **文字流程**：结构库 → 理化过滤 → 对接 → 短MD → 500ns MD → MM/PBSA + ΔΔG_PPI → FEL → ADMET → 4候选 → MST验证 → C3为最优

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 药物相似性过滤 | 排除不符合成药性的化合物 | PPI抑制剂需满足基本类药性质 | 输入：3656结构；输出：过滤后子集 | Methods "Virtual Screening" | 预期：保留更多结构多样性但增加假阳性率 [预期效应] |
| AutoDock Vina对接 | 预测配体在KIX α1/α3沟槽的结合姿势 | 提供初始结合模式假设 | 输入：配体+受体；输出：打分排序的姿势 | Methods "Molecular Docking"；Results 图3 | 预期：无法区分结合与破坏效应 [预期效应] |
| 500 ns MD模拟 | 评估配体-KIX复合物的动态稳定性 | 静态对接无法捕捉构象适应 | 输入：对接复合物；输出：轨迹 | Methods "Molecular Dynamics Simulations"；Results 图7 | 预期：短MD无法捕捉长时程构象重排 [预期效应] |
| MM/PBSA重打分 | 计算配体-KIX结合自由能 | 提供比对接分数更可靠的亲和力估计 | 输入：MD轨迹；输出：ΔG_bind | Results 表4 | 实测：C1结合最强但抑制最弱，说明单独使用会误导排序 [实测效应] |
| ΔΔG_PPI分析 | 计算配体对c-Myb-KIX界面结合能的差分效应 | 直接量化PPI破坏/稳定效应 | 输入：apo/holo轨迹；输出：ΔΔG_PPI | Results 表1 | 实测：成功区分C3（破坏）与C1（稳定）[实测效应] |
| FEL分析 | 表征配体诱导的构象状态变化 | 揭示配体对界面构象ensemble的影响 | 输入：MD轨迹PCA投影；输出：自由能地形图 | Results 图5、图6 | 预期：提供破坏机制的构象解释 [预期效应] |
| ADMET预测 | 评估候选化合物的成药性和安全性 | 早期排除高风险化合物 | 输入：结构；输出：ADMET谱 | Results 表5 | 预期：无法预测体内实际毒性 [预期效应] |
| MST实验 | 验证化合物对c-Myb-KIX结合的抑制活性 | 提供体外功能验证 | 输入：C1-C4 + 蛋白；输出：IC₅₀ | Results 图8 | 实测：确认C3为最强抑制剂，验证计算排序 [实测效应] |

## 09 关键公式符号
1. **ΔΔG_PPI（PPI界面差分结合能）**：
   ΔΔG_PPI = ΔG_PPI^holo − ΔG_PPI^apo
   - ΔG_PPI^holo：配体存在时c-Myb-KIX界面的结合自由能
   - ΔG_PPI^apo：无配体时c-Myb-KIX界面的结合自由能
   - 正值表示配体使PPI不稳定（破坏），负值表示稳定
   - 来源：Methods "MM/PBSA Free-Energy Calculations"

2. **MM/PBSA标准公式**：
   ΔG_bind = ΔE_MM + ΔG_solv − TΔS
   - ΔE_MM = ΔE_vdw + ΔE_ele（分子力学气相能量）
   - ΔG_solv = ΔG_PB + ΔG_SA（极性+非极性溶剂化）
   - TΔS：熵贡献（本文未包含）
   - 来源：Methods "MM/PBSA Free-Energy Calculations"

3. **FEL自由能重构**：
   G(PC1, PC2) = −k_BT·ln[P(PC1, PC2)]
   - k_B：玻尔兹曼常数
   - T：绝对温度
   - P(PC1, PC2)：主成分投影的概率密度
   - 来源：Methods "Free Energy Landscape (FEL) Analysis"

## 10 实验设计与证据链
- **数据集/群体**：3656个N-aryl anthranilic acid衍生物（虚拟库）；4个候选（C1-C4）进入实验
- **规模**：500 ns MD × 5个体系（apo + 4个配体复合物）；MST实验3次独立重复
- **指标**：对接分数（kcal/mol）、MM/PBSA ΔG_bind（kcal/mol）、ΔΔG_PPI（kcal/mol）、RMSD（nm）、Rg（nm）、SASA（nm²）、IC₅₀（μM）、K_d（μM）
- **基线/参考**：apo c-Myb-KIX复合物（无配体）；Naphthol AS-E phosphate作为参考抑制剂
- **骨干/仪器**：GROMACS 2022.4（MD）；AutoDock Vina v1.2.5（对接）；gmx_MMPBSA v1.6.3（能量计算）；ADMETlab 3.0（ADMET）；Monolith NT.115（MST）
- **oracle输入**：PDB 2AGH（NMR三元复合物结构，c-Myb结合面为对接靶点）
- **评测协议**：计算排序（ΔΔG_PPI）→ MST实验验证IC₅₀ → 计算与实验交叉比对

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| 虚拟筛选漏斗 | 多级过滤可有效缩小候选范围 | 3656→4 | 4个候选进入后续分析 | 漏斗策略可行 | 无法评估筛选富集率（无阳性对照集） | Results 图2 |
| 对接姿势分析 | 4个配体均结合于α1/α3沟槽 | C1-C4 vs Naphthol AS-E phosphate | 所有配体定位于同一沟槽 | 靶点选择性合理 | 对接无法区分破坏/稳定效应 | Results 图3 |
| MM/PBSA配体结合能 | 配体-KIX结合强度排序 | C1-C4 | C1最强(-28.18)，C3最弱(-17.50) | 配体均能结合KIX | 结合强度与抑制活性不相关 | Results 表4 |
| ΔΔG_PPI分析 | 配体对PPI界面的差分效应 | apo vs holo | C3:+4.57, C2:+2.30, C4:+1.40, C1:-6.47 | C3最强破坏，C1稳定PPI | 计算预测需实验验证 | Results 表1 |
| FEL分析 | 配体诱导的构象状态差异 | apo vs 各配体 | C2/C3更宽构象空间，C1/C4更紧凑 | 破坏性配体允许界面重排 | 构象差异与功能破坏的因果链未直接证明 | Results 图5、图6 |
| MST抑制实验 | 化合物在溶液相破坏c-Myb-KIX结合 | C1-C4 vs Naphthol AS-E phosphate | C3 IC₅₀=16.5±0.8 μM，优于参考(28.8±3.1)；C1最弱(99.6±20.5) | C3为最强破坏剂，计算排序基本正确 | 未测细胞活性；IC₅₀为体外生化数据 | Results 图8 |
| ADMET预测 | 候选化合物的成药性 | C1-C4 | 均满足基本类药性；C3平衡最佳 | C3适合进一步优化 | 预测需实验验证 | Results 表5 |

## 11 结论正确解读
- **任务范围**：本文仅验证了化合物在体外（MST）对c-Myb-KIX PPI的破坏活性，**未进行**细胞实验、动物实验或任何功能学验证（如转录活性、白血病细胞增殖抑制）。
- **oracle/真值输入**：计算部分以PDB 2AGH的c-Myb结合面为靶点，该结构为NMR三元复合物，包含c-Myb和MLL同时结合KIX的构象；实验部分使用人源c-Myb(241-390)和p300(1-672)片段。
- **端到端状态**：**非端到端**。计算筛选→实验验证的流程完整，但仅止步于生化活性验证，未进入细胞/动物层面。
- **算力成本**：未报告具体算力消耗；500 ns × 5体系的MD模拟为中等规模。
- **历史数据依赖**：依赖PDB 2AGH结构质量；虚拟库来源未详细说明。
- **模型依赖**：AutoDock Vina和MM/PBSA均为经典方法，精度有限；未使用AI/深度学习打分函数。
- **最难情形**：PPI界面浅而平坦，配体结合模式相似但功能效应差异大（C1 vs C3），静态打分难以区分。
- **群体/领域边界**：结论仅适用于c-Myb-KIX这一特定PPI；N-aryl anthranilic acid骨架的普适性未验证。
- **不确定性**：MM/PBSA未含熵贡献；MD力场参数（CGenFF）对配体的准确性未验证；MST的IC₅₀变异性较大（C2的SD达±22.1 μM）。
- **有边界的复述**：在PDB 2AGH结构指导下，从3656个N-aryl anthranilic acid衍生物中筛选出的C3，在体外MST实验中以16.5±0.8 μM的IC₅₀破坏c-Myb-KIX相互作用，优于参考抑制剂；但该活性尚未在细胞或动物模型中验证，且C3的PPI破坏机制（构象重排假说）仍需结构生物学证据支持。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 仅体外验证 | MST实验仅证明生化活性，未进行细胞/动物实验 | 在AML细胞系中评估C3活性，检测MYB响应基因表达 | Conclusion 末段 |
| 计算精度有限 | MM/PBSA未含熵贡献；对接和打分函数为经典方法 | 未明确提及 | Methods "MM/PBSA" |
| 候选数量少 | 仅4个化合物进入实验，SAR推断有限 | 系统修饰邻位/间位取代基，扩展类似物库 | Discussion "SAR" 段 |
| ADAPS预测未验证 | ADMET均为计算预测，未实验确认 | 未明确提及 | Results 表5 |
| 结合模式未实验确认 | 对接和MD预测的结合姿势未通过共晶结构或突变验证 | 未明确提及 | Results 图3、图6 |
| 选择性未评估 | 未测试化合物对其他KIX结合伴侣（如MLL、p53等）的影响 | 未明确提及 | 全文未涉及 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| ΔΔG_PPI计算与MST结果定性一致但定量关系未报告 | 未给出ΔΔG_PPI与IC₅₀的相关性分析；C2的ΔΔG_PPI(+2.30)与C4(+1.40)差异不大，但IC₅₀差异显著（54.7 vs 27.2 μM） | 若ΔΔG_PPI是核心排序指标，需验证其定量预测能力 | 计算更多类似物的ΔΔG_PPI并与IC₅₀做回归分析 | Results 表1、表4、图8 |
| C1预测稳定PPI（ΔΔG_PPI=-6.47）但MST仍显示弱抑制（IC₅₀=99.6 μM） | 矛盾：稳定PPI的配体为何仍显示抑制？可能是MST检测的荧光信号变化不完全反映PPI解离，或C1存在非特异性效应 | 若C1确实稳定PPI，应增强而非抑制结合；MST的IC₅₀可能受其他因素干扰 | 用独立方法（如ITC、SPR）验证C1对c-Myb-KIX结合的影响 | Results 表1、图8C |
| 对接靶点为c-Myb结合面，但未考虑KIX的构象动态和变构效应 | KIX是动态结构域，配体可能通过变构机制破坏c-Myb结合而非直接竞争 | 变构机制可能解释C3「弱结合强破坏」的现象 | 进行无标记MD模拟（apo KIX + 配体），分析构象ensemble变化 | Methods "MD Simulations"；Results 图5 |
| 仅使用单一NMR结构（2AGH）作为对接靶点 | 未考虑KIX的多种构象状态或诱导拟合效应 | 单一静态结构可能遗漏关键结合姿势 | 使用ensemble docking或多构象对接 | Methods "Molecular Docking" |
| MST实验的蛋白片段为c-Myb(241-390)和p300(1-672)，非全长蛋白 | 截短片段可能改变结合亲和力和构象 | 全长蛋白中的其他结构域可能影响PPI | 使用全长蛋白重复MST实验 | Methods "MST Assay" |
| 未报告阴性对照化合物的MST数据 | 无法排除化合物对荧光信号的非特异性影响 | 非特异性信号可导致假阳性IC₅₀ | 加入结构不相关的阴性对照化合物 | Results 图8 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **「结合≠破坏」的筛选范式**：本文最核心的可迁移概念——在PPI药物筛选中，配体-蛋白结合亲和力（ΔG_bind）与PPI破坏能力（ΔΔG_PPI）是正交维度。C1结合最强却稳定PPI，C3结合最弱却破坏最强。**迁移到TF-DNA/共激活因子界面**：筛选TF-DNA结合抑制剂时，不应仅以DNA结合竞争能力为指标，而应同时评估配体对TF-共激活因子界面或TF构象ensemble的扰动效应。

2. **ΔΔG_PPI作为排序指标**：通过比较apo和holo状态下蛋白-蛋白界面结合能的差分，可有效区分「稳定型」和「破坏型」配体。**迁移方法**：在TF-DNA互作研究中，可计算配体结合前后TF-DNA界面结合能的差分（ΔΔG_TF-DNA），作为功能破坏潜力的预测指标。

3. **FEL分析揭示构象机制**：通过PCA + 自由能地形图，可区分「紧凑稳定型」和「松散重排型」配体结合模式。**迁移方法**：对TF-DNA复合物进行配体结合前后的FEL比较，可预测配体是否诱导TF构象变化从而影响DNA结合。

4. **漏斗式多级筛选策略**：理化过滤→对接→短MD→长MD→能量重打分→ADMET的渐进式筛选，在计算成本可控的前提下有效缩小候选范围。**迁移方法**：对TF-DNA界面抑制剂筛选，可采用类似漏斗，但需在早期阶段引入ΔΔG_PPI或类似的功能指标。

5. **MST作为PPI破坏验证平台**：MST可灵敏检测蛋白-蛋白复合物的解离，适合中等通量的PPI抑制剂验证。**迁移方法**：对TF-共激活因子或TF-DNA界面，MST可同时检测配体对复合物形成的抑制效应。

6. **ADMET早期介入**：在计算阶段即评估DILI、肾毒性等风险，避免后期失败。**迁移方法**：TF-DNA界面抑制剂筛选同样应早期评估ADMET，特别是DNA结合类化合物常见的基因毒性风险。

## 15 与已有知识连接
- **结构基础**：本文使用的PDB 2AGH（KIX:c-Myb:MLL三元复合物）与De Guzman et al. 2006的NMR研究直接相关，该结构揭示了c-Myb和MLL在KIX上的双位点结合模式，是理解KIX作为多伴侣对接平台的关键结构。
- **已知抑制剂**：Naphthol AS-E phosphate（Uttarkar et al. 2015）是首个c-Myb-KIX小分子抑制剂，本文以其为参考基准；后续的MYBMIM（肽模拟物）和MybLL-tide（双位点配体）来自Ramaswamy et al. 2018，本文的N-aryl anthranilic acid骨架与之化学类型不同，属于新骨架探索。
- **PPI成药性理论**：本文引用的PPI界面特征（~1500-3000 Å²、平坦、疏水）与Arkin et al. 2012和Smith & Gestwicki 2012的PPI靶向综述一致，支持「热点口袋」策略。
- **方法学连接**：MM/PBSA方法（Genheden & Ryde 2015综述）和AutoDock Vina（Trott & Olson 2010）均为计算药物发现的标准工具；本文的「结合vs功能」区分与近年来PPI药物发现领域强调的「功能筛选」趋势一致。
- **与TF-DNA互作课题的关联** [Analysis]：c-Myb-KIX界面虽非TF-DNA直接接触面，但KIX是c-Myb转录激活功能的关键共激活因子对接平台。该界面的小分子调控策略（靶向浅沟槽、关注构象扰动）可类比于TF-DNA界面的小分子调控。此外，本文的「弱结合强破坏」现象提示，在TF-DNA界面抑制剂筛选中，应关注配体对TF-DNA复合物整体稳定性的影响，而非仅关注竞争性DNA结合。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF-DNA界面「构象扰动剂」的ΔΔG筛选框架
   - **来源局限/观察**：本文发现配体结合亲和力与PPI破坏力正交（C1 vs C3），但该框架仅用于蛋白-蛋白界面，未推广至TF-DNA界面。
   - **核心假设**：对TF-DNA复合物，配体可通过诱导TF构象变化（而非竞争DNA结合）来破坏DNA结合，且这种效应可通过ΔΔG_TF-DNA（配体结合前后TF-DNA界面结合能差分）预测。
   - **初步方法**：选取已知TF-DNA复合物结构（如p53-DNA、MYC-MAX-DNA），对候选配体库进行对接+MD模拟，计算ΔΔG_TF-DNA，筛选「弱DNA竞争但强构象扰动」的候选，用EMSA和MST验证。
   - **验证方式**：比较ΔΔG_TF-DNA排序与实验IC₅₀的相关性；用HDX-MS或NMR验证配体诱导的TF构象变化。
   - **创新状态**：unverified

2. **候选名称**：KIX双位点协同破坏策略
   - **来源局限/观察**：本文仅靶向c-Myb结合位点，但KIX同时结合MLL（另一位点），且两站点存在协同性（De Guzman et al. 2006）。
   - **核心假设**：同时靶向c-Myb和MLL结合位点的双价配体，可通过空间位阻和构象锁定协同破坏KIX的多伴侣结合能力，效果优于单位点配体。
   - **初步方法**：基于本文C3结构，设计连接C3与已知MLL位点配体的双价分子；用MD模拟验证双位点同时占据；用MST和ITC验证对c-Myb-KIX和MLL-KIX的双重破坏。
   - **验证方式**：比较双价配体与单位点配体的IC₅₀、选择性及对KIX构象ensemble的影响。
   - **创新状态**：unverified

3. **候选名称**：基于FEL的配体功能分类器
   - **来源局限/观察**：本文FEL分析显示C2/C3（破坏型）与C1/C4（稳定/混合型）的构象空间特征不同，但未系统量化。
   - **核心假设**：配体诱导的KIX构象ensemble变化（如PC1/PC2投影面积、自由能盆地深度）可作为PPI破坏/稳定效应的定量预测因子。
   - **初步方法**：对本文5个体系（apo + C1-C4）的MD轨迹提取FEL特征（盆地数量、深度、转移概率），与ΔΔG_PPI和IC₅₀做回归分析；建立分类模型。
   - **验证方式**：用留一法交叉验证；对新的N-aryl anthranilic acid类似物进行盲测。
   - **创新状态**：unverified

4. **候选名称**：c-Myb-KIX抑制剂的AML细胞活性评估
   - **来源局限/观察**：本文仅验证了体外生化活性，未进行细胞实验。
   - **核心假设**：C3在AML细胞系中能抑制MYB依赖性转录和细胞增殖，且其活性与MYB表达水平相关。
   - **初步方法**：在MV4-11、MOLM-13等AML细胞系中处理C3，检测MYB靶基因表达（qPCR）、细胞活力（CCK-8）、凋亡（流式）和集落形成。
   - **验证方式**：与已知MYB抑制剂（如Naphthol AS-E phosphate）对比；用MYB敲低细胞验证靶点特异性。
   - **创新状态**：unverified

5. **候选名称**：N-aryl anthranilic acid骨架的SAR扩展与优化
   - **来源局限/观察**：本文仅测试了4个化合物，SAR推断有限（Discussion末段作者也承认）。
   - **核心假设**：邻位甲基+间位疏水取代的组合可进一步优化C3的PPI破坏活性和选择性。
   - **初步方法**：基于C3结构，系统变化邻位/间位/对位取代基（甲基、卤素、三氟甲基、甲氧基等），合成10-20个类似物；用对接+MD+MM/PBSA预筛，MST验证。
   - **验证方式**：建立IC₅₀与计算特征（ΔΔG_PPI、疏水接触面积）的QSAR模型。
   - **创新状态**：unverified