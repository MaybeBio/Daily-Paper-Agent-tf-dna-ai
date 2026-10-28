## 01 基本信息
- **标题**：Screening of peptide inhibitors targeting YAP-TEAD4 interaction: affinity evaluation and anti-AML cell activity
- **作者**：Yang, Xiaotian; Yang, Shudan; Lin, Guoqiang; Chen, Shutong; Jiang, Huiran; Wang, Yuting; Zhang, Yanming; Zhang, Xingxia
- **单位**：未提供（PubMed 记录未列出单位信息）
- **期刊/平台**：Journal of Enzyme Inhibition and Medicinal Chemistry
- **年份**：2026（在线发表日期 2026-03-09）
- **论文类型**：实验研究（虚拟筛选 + 体外实验验证）
- **领域**：药物发现 / 蛋白质-蛋白质相互作用（PPI）抑制 / 急性髓系白血病（AML）
- **关键词**：YAP-TEAD4；肽抑制剂；药效团建模；分子对接；分子动力学模拟；AML
- **DOI/arXiv 号**：10.1080/14756366.2026.2633822
- **代码**：未提供
- **数据**：数据可向通讯作者索取（Data availability statement）
- **阅读日期**：2026-05-13（基于当前日期）
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × AI/物理模拟」方向中的**间接相关**工作——研究对象为 YAP-TEAD4 转录因子复合物（TEAD4 为 DNA 结合转录因子，YAP 为共激活因子），但靶向的是**蛋白-蛋白界面**而非蛋白-DNA 界面。方法上采用**药效团建模 + 分子对接 + MD 模拟**的物理模拟流程，对 TF-DNA 互作研究中的**界面分析、虚拟筛选、结合自由能计算**具有直接可迁移性。

## 02 一句话总结
通过药效团建模、分子对接和 MD 模拟从 59,319 条十肽库中筛选出靶向 YAP-TEAD4 界面 3 的候选肽，其中 peptide-4 以 5.08 nM 的 Kd 结合 TEAD4，并在 AML-193 细胞中显示 0.65 μM 的抗增殖活性及下游基因（CTGF/CYR61）下调。

## 03 研究问题
- **具体问题**：能否从肽库中筛选出高亲和力、可破坏 YAP-TEAD4 互作的肽抑制剂，并在 AML 细胞模型中验证其活性？
- **为什么重要**：YAP-TEAD4 的异常激活驱动肿瘤发生、进展和化疗耐药。YAP 无酶活口袋，难以用小分子靶向；TEAD4 的小分子抑制剂存在特异性差、亲和力低的问题。肽类抑制剂更适合覆盖大而平坦的 PPI 界面。
- **现有方法不足**：已有 TEAD 靶向小分子（flufenamic acid、niflumic acid、vinylsulfonamide、MGH-CP1）特异性差、亲和力低；YAP 来源的 Ω-loop 肽虽具微摩尔亲和力但不足以成药；Stapled 肽（如 stapled sYAPm1）亲和力仍仅达微摩尔级别（Kd = 37.0 ± 5.4 μM）。
- **精确研究问题**：Can structure-based virtual screening (pharmacophore + docking) identify peptide inhibitors with nanomolar affinity for TEAD4 and measurable anti-AML activity in cell models?

## 04 背景与发展脉络
*注：以下脉络基于本文引文及正文描述，属「经外部核验」的领域发展框架。*

1. **阶段一：小分子 TEAD 抑制剂**（2015-2021）
   - 代表：flufenamic acid、niflumic acid、vinylsulfonamide、MGH-CP1
   - 优点：可口服、代谢稳定
   - 局限：特异性差、亲和力低（微摩尔级别）
   - 代表进展：IAG933 进入 I 期临床（2021，间皮瘤），但后续结果未更新

2. **阶段二：YAP 来源肽段**（2015-2020）
   - 代表：YAP84-100 来源的 peptide 17（经二硫键构象优化，Kd = 15 nM 对 TEAD1）
   - 优点：天然界面序列、特异性较好
   - 局限：对 TEAD4 的亲和力不足；细胞渗透性差

3. **阶段三：stapled 肽**（2020-2023）
   - 代表：stapled sYAPm1（Ω-loop 序列环化，Kd = 37.0 ± 5.4 μM）
   - 优点：构象预组织增强亲和力
   - 局限：仍为微摩尔级别，未达成药阈值

4. **阶段四：结构导向虚拟筛选**（本文位置，2024-2026）
   - 方法：药效团建模 + 分子对接 + MD 模拟 + MM/PBSA
   - 优势：可系统搜索序列空间、成本低、可解释性强
   - 本文贡献：从 59,319 条肽库中筛出 Kd = 5.08 nM 的 peptide-4，显著优于已有肽类抑制剂

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| YAP 难以直接靶向 | YAP 无酶活口袋、无深结合位点 | YAP 是转录共激活因子，缺乏经典药物结合位点 | Introduction 第 2 段 |
| TEAD 小分子抑制剂亲和力低 | 已报道 TEAD 抑制剂特异性差、亲和力低 | 小分子难以覆盖大而平坦的 PPI 界面 | Introduction 第 2 段 |
| 已有肽抑制剂亲和力不足 | YAP 来源 Ω-loop 肽仅微摩尔亲和力 | 线性肽缺乏构象约束，熵代价高 | Introduction 第 3 段（stapled sYAPm1 Kd = 37.0 ± 5.4 μM） |
| 界面 3 缺乏深口袋 | 大而平坦的表面无深结合位点 | 界面 3 以 Ω-loop 介导，接触面积大但缺乏经典口袋 | Introduction 第 3 段；Results 图 1 |
| 肽的细胞渗透性差 | 肽类药物普遍存在膜穿透问题 | 肽的极性和分子量限制 | Discussion 中 physicochemical properties 预测（pI = 12.01 正电荷增强渗透） |

## 06 核心思想

### 1) 表面方法
基于 YAP-TEAD4 复合物晶体结构（PDB: 3KYS），在 MOE 中构建药效团模型（含氢键受体、供体、疏水中心），对 59,319 条十肽库进行虚拟筛选，经分子对接打分排序后取 top 4 进行体外验证，并对最优肽进行 50 ns MD 模拟和 MM/PBSA 结合自由能计算。

### 2) 核心洞察
YAP 的 Ω-loop 序列（残基 85-95）虽为关键结合元件，但线性肽亲和力不足。通过**药效团特征编码界面关键相互作用**（Phe85 的氢键受体、Lys90 的氢键供体、疏水核心），可在不依赖精确对接打分的情况下快速富集高亲和力候选肽。peptide-4 的序列（MRSRKLPNSF）与天然 YAP 序列（PMRLRKLPDSFFKPP）相比，在保持关键接触残基的同时优化了疏水/静电互补。

### 3) 可能的普适教训 [Analysis]
- **药效团优先于对接打分**：对于大而平坦的 PPI 界面，精确对接打分往往不可靠，而基于关键残基相互作用的药效团筛选更具鲁棒性。这一策略可迁移到 TF-DNA 界面——识别 DNA 结合域的关键碱基接触残基，构建药效团筛选 DNA 模拟肽或小分子。
- **MD 验证作为二级筛选**：本文用 50 ns MD 验证 docking pose 的稳定性，而非直接依赖 docking score，这一「docking 初筛 + MD 确认」的两级策略对 TF-DNA 体系同样适用。
- **正电荷肽增强渗透**：peptide-4 的高 pI（12.01）被作者解释为增强膜渗透的设计特征，这对核内靶点（如转录因子）的肽类药物设计有参考价值。

## 07 方法总览

- **输入**：YAP-TEAD4 复合物晶体结构（PDB: 3KYS）；59,319 条十肽组合库（由三肽+三肽+四肽片段组合生成）
- **输出**：4 条候选肽（peptide 1-4），其中 peptide-4 为最优候选
- **模块**：
  1. 药效团建模（MOE）：基于界面 3 关键残基相互作用构建
  2. 药效团验证：500 分子测试集（含 7 个已知活性肽），计算 Enrichment Factor 和 GH score
  3. 虚拟筛选：药效团匹配 + 分子对接（MOE Dock，Triangle Matcher + London dG 初筛，GBVI/WSA dG 精打分）
  4. 体外验证：MST 亲和力测定（Kd）、MTT 细胞活力（IC50）、RT-qPCR（CTGF/CYR61 表达）
  5. MD 模拟：50 ns，GROMACS 2021.5，AMBER99SB-ILDN 力场，SPC 水模型
  6. MM/PBSA 计算：单轨迹法，分解为静电、范德华、极性和非极性溶剂化能
- **训练**：无监督/无训练过程（基于物理/知识驱动方法）
- **反馈回路**：docking score → 体外 Kd 验证 → MD 稳定性确认 → 功能实验（MTT/RT-qPCR）
- **工具**：MOE（药效团、对接）、GROMACS（MD）、GraphPad Prism（绘图）、Expasy ProtParam（理化性质预测）
- **假设**：① 3KYS 晶体结构可代表溶液中的 YAP-TEAD4 构象；② 药效团特征可编码界面关键相互作用；③ docking score 与实验亲和力正相关；④ 肽的细胞活性与其 TEAD4 亲和力相关

**文字流程**：从 PDB 获取 3KYS → MOE 中预处理结构 → 分析界面 3 相互作用 → 构建药效团模型 → 用 500 分子测试集验证药效团 → 对 59,319 肽库进行药效团筛选 → 命中 126 条 → 分子对接打分排序 → 取 top 4 → 合成肽段 → MST 测 Kd → 选出 peptide-4 → 50 ns MD 验证稳定性 → MM/PBSA 计算结合自由能 → MTT 测 IC50 → RT-qPCR 测下游基因表达 → 预测理化性质

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 药效团建模 | 编码界面 3 关键相互作用（HBA、HBD、疏水中心） | 大而平坦的 PPI 界面无法直接对接筛选，需先降维 | 输入：3KYS 界面残基；输出：4 特征药效团模型 | 500 分子测试集：EF = 63，GH = 0.9，0 假阴性 | [预期] 移除后筛选将无导向，59,319 条肽库无法有效富集 |
| 药效团验证 | 评估模型区分活性/非活性肽的能力 | 确保模型有预测力而非过拟合 | 输入：500 分子测试集；输出：EF、GH 分数 | Table S3：活性分子率 88%，活性比 100% | [预期] 无验证则模型可靠性未知，后续筛选结果不可信 |
| 虚拟筛选（药效团匹配 + 对接） | 从 59,319 条肽中富集候选 | 实验验证成本高，需计算预筛 | 输入：肽库 + 药效团 + TEAD4 结构；输出：top 4 候选肽 | 126 条命中 → 对接打分 → top 4 | [预期] 移除后需实验筛选全部 59,319 条肽，不现实 |
| 分子对接打分 | 排序候选肽的结合亲和力 | 药效团匹配后需精细排序 | 输入：126 条命中肽 + TEAD4；输出：docking score 排序 | 图 3：peptide 1-4 打分均优于 peptide 10 | [预期] 移除后无法从 126 条中选出 top 4 |
| MST 亲和力测定 | 实验验证候选肽与 TEAD4 的结合 | 计算预测需实验确认 | 输入：peptide 1-4 + TEAD4 蛋白；输出：Kd 值 | Table 2：peptide-4 Kd = 5.08 ± 0.42 nM | [实测] 无此模块则所有计算预测无实验支撑 |
| MD 模拟（50 ns） | 验证 peptide-4-TEAD4 复合物稳定性 | 静态 docking pose 可能不稳定 | 输入：docking 最优复合物；输出：RMSD/RMSF/Rg/氢键轨迹 | 图 5：RMSD 稳定于 0.45 nm，6 个稳定氢键 | [预期] 移除后无法确认 docking pose 的动力学稳定性 |
| MM/PBSA 计算 | 定量计算结合自由能 | 评估结合强度及驱动力 | 输入：MD 轨迹；输出：ΔG = −35.89 ± 0.43 kJ/mol | Results 图 5(F,G)：范德华和静电为主要驱动力 | [预期] 移除后无法从能量学角度解释结合机制 |
| MTT 细胞活力 | 评估肽对 AML-193 的抗增殖活性 | 亲和力不等于细胞活性 | 输入：peptide 1-4 + AML-193 细胞；输出：IC50 | peptide-4 IC50 = 0.65 ± 0.04 μM | [实测] 无此模块则无法确认功能活性 |
| RT-qPCR | 检测下游靶基因 CTGF/CYR61 表达 | 确认通路抑制的特异性 | 输入：peptide-4 处理细胞；输出：mRNA 相对表达量 | 图 7：浓度依赖性下调 | [实测] 无此模块则无法确认机制相关性 |

## 09 关键公式符号

**MM/PBSA 结合自由能**（Methods 节）：
$$\Delta G = \Delta H - T \times \Delta S$$

$$\Delta H = \Delta E_{ele} + \Delta E_{vdW} + \Delta G_{PB} + \Delta G_{SA}$$

| 符号 | 含义 | 用途 |
|------|------|------|
| ΔG | 结合自由能变化 | 评估 peptide-4 与 TEAD4 结合的热力学稳定性 |
| ΔH | 焓变 | 结合过程的热效应 |
| T | 热力学温度 | 熵项的温度系数 |
| ΔS | 熵变 | 构象和溶剂熵的变化 |
| ΔE_ele | 静电相互作用能 | 评估静电贡献（本文中为主要驱动力之一） |
| ΔE_vdW | 范德华相互作用能 | 评估疏水接触贡献（本文中为主要驱动力之一） |
| ΔG_PB | 极性溶剂化自由能 | 评估去溶剂化代价（本文中不利于结合） |
| ΔG_SA | 非极性溶剂化自由能 | 评估疏水效应贡献 |

**药效团验证指标**（Methods 节）：
- Enrichment Factor (EF)：活性分子富集倍数
- Goodness of Hit Score (GH)：命中质量综合评分

**IC50 计算**：MTT 实验数据经非线性回归拟合剂量-反应曲线获得（具体公式未在文中给出）

## 10 实验设计与证据链

### 数据集/群体/规模
- **结构数据**：YAP-TEAD4 复合物晶体结构（PDB: 3KYS，分辨率 2.8 Å）
- **肽库**：59,319 条十肽（组合库，由三肽+三肽+四肽片段拼接）
- **药效团验证集**：500 分子（含 7 个已知活性肽）
- **候选肽**：peptide 1-4 + 阳性对照 peptide 10
- **细胞系**：AML-193（人急性髓系白血病细胞系，ATCC CRL-9589）
- **蛋白**：重组人 TEAD4 蛋白（Abcam, ab238222）

### 指标
- 药效团模型：EF、GH score、假阴性/假阳性率
- 亲和力：Kd（MST 测定）
- 细胞活性：IC50（MTT 测定，72h）
- 结构稳定性：RMSD、RMSF、Rg、氢键数（MD 轨迹）
- 结合自由能：ΔG（MM/PBSA）
- 通路抑制：CTGF/CYR61 mRNA 相对表达量（RT-qPCR，2^-ΔΔCt 法）

### 预算/资源
- MD 模拟：50 ns，GROMACS 2021.5，AMBER99SB-ILDN 力场，SPC 水模型，通过 BeiKun Cloud 平台计算
- 实验重复：MTT 和 RT-qPCR 至少三次独立重复（Methods 节）

### 评测协议
- 药效团验证：500 分子测试集，计算 EF 和 GH
- 亲和力排序：MST 测定 Kd，peptide-4 最低（5.08 nM）
- 功能验证：MTT 测 IC50，peptide-4 最低（0.65 μM）
- 机制验证：RT-qPCR 检测 CTGF/CYR61 下调

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|-----------------|------|
| 药效团模型验证 | 模型能区分活性/非活性肽 | 500 分子测试集，7 个已知活性肽 | EF = 63，GH = 0.9，0 假阴性 | 模型有强预测能力 | 测试集规模小，可能过拟合 | Table S3 |
| 虚拟筛选 | 药效团 + docking 能富集高亲和力肽 | 59,319 条肽库 → 126 命中 → top 4 | 4 条候选肽进入实验 | 筛选流程有效 | 未报告命中率与随机筛选的对比 | Results 图 2-3 |
| MST 亲和力 | 候选肽与 TEAD4 有高亲和力 | peptide 1-4 vs peptide 10 | peptide-4 Kd = 5.08 ± 0.42 nM，优于 peptide 10（12.16 ± 0.93 nM） | peptide-4 为高亲和力 TEAD4 结合肽 | 未测其他已知 TEAD4 抑制剂作对照 | Table 2 |
| MD 模拟 | peptide-4-TEAD4 复合物稳定 | 50 ns，AMBER99SB-ILDN | RMSD 稳定于 0.45 nm，6 个稳定氢键 | docking pose 在动力学上稳定 | 仅 50 ns，未做重复或更长模拟 | 图 5(A-E) |
| MM/PBSA | 结合自由能热力学稳定 | 单轨迹法 | ΔG = −35.89 ± 0.43 kJ/mol | 结合为自发过程 | 未做熵分解或突变分析验证残基贡献 | 图 5(F-G) |
| MTT 细胞活力 | peptide-4 抑制 AML-193 增殖 | peptide 1-4 vs peptide 10，72h | peptide-4 IC50 = 0.65 ± 0.04 μM，最低 | peptide-4 有抗 AML 活性 | 未测正常细胞毒性，未做凋亡/周期分析 | Results 图 S2 |
| RT-qPCR | peptide-4 抑制 Hippo 下游靶基因 | 0.2 和 5 μM 处理 | CTGF/CYR61 浓度依赖性下调 | peptide-4 功能上抑制 YAP-TEAD4 转录活性 | 未检测蛋白水平变化，未做 ChIP 验证直接结合 | 图 7 |

## 11 结论正确解读

- **任务范围**：本文仅覆盖**体外**亲和力（MST）和**细胞水平**活性（MTT/RT-qPCR），未进行动物实验、药代动力学或毒性研究。
- **Oracle/真值输入**：MST 测定的 Kd 值作为亲和力金标准；MTT 的 IC50 作为细胞活性指标；RT-qPCR 的 mRNA 水平作为通路抑制指标。这些均为实验测量值，非计算预测。
- **端到端状态**：**非端到端**。虚拟筛选仅提供候选，最终验证依赖实验。计算与实验之间存在明显断层——docking score 与 Kd 的定量关系未建立。
- **算力成本**：MD 仅 50 ns，计算成本较低；未报告具体 GPU 时数。
- **历史数据依赖**：依赖 3KYS 晶体结构（2009 年发表），未考虑 TEAD4 的构象动态或多聚体状态。
- **模型依赖**：药效团模型基于单一晶体结构界面 3 的静态相互作用，未考虑诱导拟合。
- **最难情形**：未测试 peptide-4 对其他 TEAD 家族成员（TEAD1/2/3）或 YAP 同源物（YAP1/TAZ）的选择性；未在耐药细胞株或原代 AML 细胞中验证。
- **群体/领域边界**：结论仅适用于 AML-193 细胞系和体外 TEAD4 结合；不能外推至体内抗白血病效果或其他癌症类型。
- **不确定性**：Kd 和 IC50 均报告为 mean ± SEM，但未报告重复次数和变异系数；MD 模拟仅一次运行，无系综重复。

**有边界的复述**：在 3KYS 结构指导下，通过药效团建模和分子对接从 59,319 条十肽库中筛选出的 peptide-4，在体外以 5.08 nM 的 Kd 结合 TEAD4，在 AML-193 细胞中 72h 处理显示 0.65 μM 的 IC50，并在 0.2-5 μM 浓度下显著下调 CTGF/CYR61 mRNA 表达。这些数据支持 peptide-4 作为 YAP-TEAD4 互作抑制剂的候选分子，但其体内抗白血病活性和选择性尚未验证。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 缺乏体内验证 | 未进行动物模型实验 | "In vivo evaluations of peptide-4 will be conducted, encompassing anti-AML efficacy assays, toxicity studies, and pharmacokinetic experiments" | Conclusions 末段 |
| 理化性质仅为预测 | 未实验测定肽的稳定性、渗透性等 | "in vitro experiments will be conducted to further validate these properties" | Conclusions 末段 |
| 未报告临床转化数据 | 无药代动力学、毒性数据 | 同上 | Conclusions 末段 |

*注：作者在正文中未系统列出局限性，以上为 Conclusions 中明确提及的未来工作方向，属「作者提及的相关约束」而非正式局限声明。*

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 药效团验证集仅 500 分子，其中仅 7 个活性肽 | EF = 63 可能因活性分子比例极低而虚高；GH = 0.9 在如此小的活性集上统计功效不足 | 模型泛化能力存疑，可能过拟合特定化学空间 | 在更大、更多样化的数据集上验证；报告 ROC-AUC 或随机基线对比 | Methods 节 |
| 未报告 docking 与实验 Kd 的相关性 | 4 条肽的 docking 排序与 MST 测定的 Kd 排序是否一致未说明 | 若 docking score 与实验亲和力无定量关系，筛选流程的可推广性受限 | 计算 4 条肽 docking score 与 Kd 的 Spearman 相关 | Results 图 3 vs Table 2 |
| MD 仅 50 ns 且单次运行 | 肽-蛋白结合可能未充分采样；未做重复实验评估方差 | 动力学稳定性结论可能不可靠 | 延长至 200+ ns，3 次重复，报告标准差 | Methods 节 |
| 未做突变实验验证关键残基 | 文中声称 Gln246、Asp249、Lys250、Lys274、Tyr406 为核心残基，但无 alanine scanning 或突变体 Kd 数据 | 残基贡献缺乏直接实验证据 | 对 peptide-4 或 TEAD4 进行定点突变，测 Kd 变化 | Results 图 5(F,G) |
| 未测试对 TEAD1/2/3 的选择性 | YAP 可与所有 TEAD 家族成员结合，peptide-4 可能无选择性 | 选择性是药物开发的关键参数 | 对 TEAD1/2/3 分别测 Kd | 未提供 |
| 细胞实验仅一个细胞系 | AML-193 单一细胞系不足以支持"anti-AML"结论 | 不同 AML 亚型的 YAP-TEAD4 依赖性可能不同 | 在多个 AML 细胞系及原代细胞中验证 | Results 图 S2 |
| 未检测蛋白水平变化 | RT-qPCR 仅测 mRNA，未验证 CTGF/CYR61 蛋白水平或下游通路（如增殖标志物） | mRNA 变化不一定反映功能蛋白变化 | Western blot 检测 CTGF/CYR61 蛋白 | 图 7 |
| 未做 ChIP 或报告基因实验 | 未直接证明 peptide-4 在细胞内阻断 YAP-TEAD4 在 DNA 上的转录复合物 | 机制推断（抑制 YAP-TEAD4 互作）缺乏直接证据 | 荧光素酶报告基因实验或 ChIP-qPCR | 未提供 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **药效团优先筛选策略**（可迁移性：高）
   - 概念：对平坦 PPI 界面，先构建基于关键残基相互作用的药效团模型，再用 docking 精筛
   - 迁移到 TF-DNA：对 TF 的 DNA 结合域（DBD），识别与 DNA 碱基形成特异性接触的关键残基（如螺旋-转角-螺旋 motif 的第 3 螺旋），构建药效团筛选 DNA 模拟肽或小分子
   - 操作：在 MOE 或 Pharmit 中基于 TF-DNA 共晶结构构建药效团 → 筛选肽库/DNA 模拟物库 → docking 验证

2. **两级验证流程：docking 初筛 + MD 确认**（可迁移性：高）
   - 概念：docking score 排序后，用 MD 模拟验证 top 候选的结合稳定性，而非直接信任 docking pose
   - 迁移到 TF-DNA：对候选 TF 抑制剂或突变体，先 docking 到 DBD-DNA 界面，再用 50-100 ns MD 验证复合物稳定性，以 RMSD/RMSF/氢键数为指标
   - 注意：本文 MD 仅 50 ns，对 TF-DNA 体系建议延长至 200+ ns 并做重复

3. **MM/PBSA 能量分解识别驱动残基**（可迁移性：高）
   - 概念：将结合自由能分解为静电、范德华、极性/非极性溶剂化能，识别主要驱动力
   - 迁移到 TF-DNA：对 TF-DNA 复合物做 MM/PBSA 或 MM/GBSA 分解，识别对 DNA 结合贡献最大的残基，指导突变设计或抑制剂设计
   - 本文结果：范德华和静电为主要驱动力，极性溶剂化不利——TF-DNA 结合通常也以静电和范德华为主

4. **正电荷肽设计增强膜渗透**（可迁移性：中）
   - 概念：peptide-4 的 pI = 12.01，作者认为正电荷增强膜渗透
   - 迁移到 TF-DNA：设计靶向 TF 的细胞穿透肽时，可通过富集 Lys/Arg 残基提高正电荷，但需平衡 DNA 结合界面的电荷互补
   - 注意：此为作者推测，无直接实验证据

5. **下游靶基因作为功能读出**（可迁移性：高）
   - 概念：用 RT-qPCR 检测通路下游靶基因（CTGF/CYR61）表达作为抑制效果的机制验证
   - 迁移到 TF-DNA：对 TF 抑制剂，检测该 TF 已知靶基因的表达变化，作为转录抑制的功能证据
   - 注意：需结合 ChIP 或报告基因实验确认直接机制

## 15 与已有知识连接

1. **YAP-TEAD 互作界面研究**（可验证外部文献）
   - 本文基于 3KYS 结构分析界面 3，与已有 YAP-TEAD 结构生物学研究一致（如 Li et al., 2010, Genes & Development 报道的 YAP-TEAD 复合物结构）
   - 界面 3 的 Ω-loop 结合模式与已有报道吻合

2. **TEAD 抑制剂开发现状**（可验证外部文献）
   - 本文引用的 IAG933（Novartis）进入 I 期临床，与公开数据库（ClinicalTrials.gov）信息一致
   - 已有小分子抑制剂（flufenamic acid 等）的局限性在本文中准确描述

3. **肽类 PPI 抑制剂设计策略**（可验证外部文献）
   - Stapled 肽策略（stapled sYAPm1）与已有文献一致（如 Zhang et al., 2020, JACS 报道的 YAP 来源 stapled 肽）
   - 本文 peptide-4 的 Kd（5.08 nM）优于已报道的 stapled sYAPm1（37 μM），但需注意实验条件差异

4. **MM/PBSA 方法学**（可验证外部文献）
   - 本文使用单轨迹 MM/PBSA 方法，与标准流程一致（如 Kollman et al., 2000, Acc Chem Res）
   - 能量分解策略与文献中 PPI 体系分析一致

5. **与 TF-DNA 互作研究的关联**（[Analysis] 候选方向）
   - YAP 本身是转录共激活因子，其与 TEAD4 的互作是转录调控的关键步骤
   - TEAD4 的 DNA 结合域（TEA 结构域）与 YAP 结合域在空间上分离，但 YAP 结合可增强 TEAD4 的 DNA 结合亲和力——这一「共激活因子增强 DBD 结合」的机制可迁移到其他 TF 体系
   - 本文的肽筛选策略可反向应用于筛选增强或阻断 TF-DNA 结合的肽

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF-DBD 药效团筛选平台（TF-DBD Pharmacophore Screening Platform）
   - **来源局限/观察**：本文药效团方法针对 PPI 界面，但 TF-DNA 界面具有不同的化学特征（磷酸二酯骨架、碱基特异性氢键）
   - **核心假设**：基于 TF-DBD 关键碱基接触残基构建的药效团模型，可从肽库中筛选出阻断 TF-DNA 结合的肽
   - **增量**：将本文的 PPI 药效团流程适配到蛋白-DNA 界面，需处理 DNA 的特异性（碱基序列）和非特异性（骨架）接触
   - **初步方法**：选一个 TF（如 p53、MYC），从共晶结构提取 DBD-DNA 接触残基 → 构建药效团（碱基特异性 H-bond、疏水堆积）→ 筛选肽库 → MST/ITC 验证 → MD 确认
   - **验证方式**：EMSA 或荧光各向异性检测肽对 TF-DNA 结合的抑制；ChIP 检测细胞内靶基因结合变化
   - **创新状态**：unverified

2. **候选名称**：TF-DNA 结合自由能分解图谱（TF-DNA Binding Free Energy Decomposition Atlas）
   - **来源局限/观察**：本文 MM/PBSA 仅报告总 ΔG，未做残基级分解；对 TF-DNA 体系，识别「热点残基」对设计抑制剂至关重要
   - **核心假设**：对多个 TF-DNA 复合物做 MM/PBSA 残基分解，可识别通用的 DNA 结合热点残基模式
   - **增量**：系统性地跨 TF 家族比较能量分解图谱，而非单案例
   - **初步方法**：收集 20-50 个 TF-DNA 共晶结构 → 短 MD（50-100 ns）→ MM/PBSA 残基分解 → 聚类分析热点残基模式
   - **验证方式**：对预测的热点残基做 alanine scanning 突变，测 DNA 结合亲和力变化
   - **创新状态**：unverified

3. **候选名称**：共激活因子增强 DBD-DNA 结合的分子机制研究（Coactivator-Enhanced DBD-DNA Binding Mechanism）
   - **来源局限/观察**：本文研究 YAP-TEAD4 互作，但未探讨 YAP 结合如何影响 TEAD4 的 DNA 结合；已有文献提示共激活因子可增强 TF 的 DNA 结合
   - **核心假设**：YAP 结合 TEAD4 诱导 DBD 构象变化，增强其 DNA 结合亲和力或改变序列选择性
   - **增量**：将 PPI 抑制与 DNA 结合调控联系起来，提供双重干预策略
   - **初步方法**：MD 模拟 TEAD4-DBD 单独 vs TEAD4-DBD+YAP 肽复合物的 DNA 结合自由能；比较构象系综
   - **验证方式**：EMSA 比较有无 YAP 肽时 TEAD4 的 DNA 结合亲和力；SMF（单分子荧光）检测结合动力学
   - **创新状态**：unverified

4. **候选名称**：正电荷肽的核内递送效率系统评估（Systematic Evaluation of Cationic Peptide Nuclear Delivery）
   - **来源局限/观察**：本文推测 peptide-4 的高 pI 增强膜渗透，但无实验证据；TF 抑制肽需进入核内才能发挥作用
   - **核心假设**：正电荷密度与核内递送效率存在非线性关系，过高正电荷可能导致内体滞留
   - **增量**：系统比较不同 pI/电荷分布的肽的核内递送效率，为 TF 靶向肽设计提供参数
   - **初步方法**：合成一系列 pI 7-13 的肽 → 共聚焦显微镜定量核内分布 → 关联 pI 与核内浓度
   - **验证方式**：核内荧光定量 + 功能性读出（靶基因表达抑制）
   - **创新状态**：unverified

5. **候选名称**：TF 界面肽库的机器学习增强筛选（ML-Enhanced Peptide Library Screening for TF Interfaces）
   - **来源局限/观察**：本文用 59,319 条肽库 + 药效团筛选，但未用 ML；对更大的组合空间，ML 可提升筛选效率
   - **核心假设**：基于已知 TF 界面肽的活性数据训练 ML 模型，可预测新肽的亲和力，减少 docking 计算量
   - **增量**：将本文的物理筛选流程与 ML 结合，形成混合筛选管线
   - **初步方法**：用本文 4 条肽 + 文献中 TF 界面肽数据训练 GBDT/图神经网络 → 预测 10^6 级肽库 → top 100 做 docking + MD → 实验验证 top 10
   - **验证方式**：MST 测 Kd，比较 ML 预测排名与实验排名的一致性
   - **创新状态**：unverified