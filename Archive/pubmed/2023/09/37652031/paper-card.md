## 01 基本信息

- **标题**：Updated Phylogeny and Protein Structure Predictions Revise the Hypothesis on the Origin of MADS-box Transcription Factors in Land Plants
- **作者与单位**：Qiu, Yichun; Li, Zhen; Walther, Dirk; Kohler, Claudia（单位未在摘要中提供，推测为 Max Planck Society 相关研究所）
- **期刊/预印本平台**：Molecular Biology and Evolution
- **年份**：2023-09-01
- **论文类型**：研究论文（系统发育学 + 蛋白质结构预测）
- **领域**：进化生物学、植物发育、转录因子家族演化
- **关键词**：MADS-box、转录因子、系统发育、AlphaFold2、OmegaFold、蛋白质结构预测、陆生植物起源
- **DOI/arXiv 号**：10.1093/molbev/msad194
- **代码**：未提供
- **数据**：所有数据包含在文章及在线补充材料中（Data Availability 声明）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦 MADS-box 转录因子（TF）家族的进化起源，利用系统发育分析和 AlphaFold2/OmegaFold 蛋白质结构预测，修正了陆生植物 Type I/II MADS-box TF 的起源假说。与「TF–DNA 互作 × AI 方法」课题的关联在于：(1) 展示了 AlphaFold2/OmegaFold 结构预测在区分 TF 亚家族（SRF-type vs. MEF2-type）中的判别力；(2) 结构预测与系统发育互为验证的方法论可迁移至其他 TF 家族的功能演化研究；(3) 为理解 TF 结构域（MADS、I、K 域）与 DNA 结合功能的关系提供了进化框架。

## 02 一句话总结

利用 175 个真核物种的 MADS-box 基因序列进行系统发育分析，并结合 AlphaFold2/OmegaFold 蛋白质结构预测，证明陆生植物 Type I 和 Type II MADS-box TF 均起源于 MEF2-type 祖先基因（而非传统认为的 SRF-type 与 MEF2-type 分别对应），该结论通过结构相似性评分和拓扑检验（AU test）获得支持。

## 03 研究问题

- **具体问题**：陆生植物 MADS-box 转录因子的 Type I（M-type）和 Type II（MIKC-type）亚家族分别起源于真核生物中哪个祖先类型（SRF-type 还是 MEF2-type）？
- **为什么重要**：MADS-box TF 是陆生植物发育（尤其是花器官形成）的核心调控因子，其起源假说影响对植物陆地适应、体型复杂度演化以及 TF 家族功能分化的理解。传统模型（Alvarez-Buylla et al. 2000）认为 Type I 对应 SRF-type、Type II 对应 MEF2-type，但该模型基于少量序列且支持度不足。
- **现有方法为何不足**：早期系统发育分析受限于可用序列数量（仅少数拟南芥、动物、真菌序列），长枝吸引（long-branch attraction）可能导致 Type I 高替换率序列错误聚类到 SRF 分支；缺乏独立证据（如结构信息）验证系统发育推断。
- **精确研究问题**：Can the combination of expanded taxonomic sampling and protein structure prediction (AlphaFold2/OmegaFold) resolve whether land plant Type I and II MADS-box TFs both derive from a MEF2-type ancestor?

## 04 背景与发展脉络

**注：以下脉络基于本文框架，未经外部系统核验。**

1. **奠基阶段（1990s–2000s）**：MADS-box 基因家族命名（MCM1、AGAMOUS、DEFICIENS、SRF）；动物中 SRF/MEF2 两类被区分；植物中 Type I/II 被发现。Alvarez-Buylla et al. (2000) 提出 Type I↔SRF、Type II↔MEF2 的对应模型，基于少量序列。
2. **扩展阶段（2000s–2010s）**：更多植物基因组（拟南芥、水稻等）揭示 Type I/II 在植物中大量扩增；Type I 高替换率、内含子丢失等特征被描述；但早期模型未被严格检验。De Bodt et al. (2003) 和 Kaufmann et al. (2005) 曾提出质疑，但未引起重视。
3. **基因组时代（2010s–2020s）**：轮藻（Charophytes）基因组（如 Klebsormidium flaccidum、Chara braunii）揭示其仅含 MEF2-type（Type II）MADS-box 基因；绿藻、红藻中亦无 SRF-type 基因。这些发现与旧模型矛盾。
4. **结构预测时代（2021–）**：AlphaFold2 (Jumper et al. 2021) 和 OmegaFold (Wu et al. 2022) 使基于序列的蛋白质结构预测成为可能，为系统发育推断提供独立验证手段。本文在此阶段提出修正模型。

**本文主张的位置**：在系统发育采样广度（175 物种）和证据类型（序列 + 结构）上均超越前人，提出「Type I 和 II 均源自 MEF2-type」的新模型，并建议术语「SRF-type/MEF2-type」用于真核生物层面、「M-type/MIKC-type」仅用于植物结构域描述。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 早期系统发育支持度不足 | Type I 与 SRF 的聚类关系在原始研究中支持度低 | 可用序列数量有限（仅少数拟南芥、动物、真菌序列），长枝吸引效应 | Introduction 节：作者引用 Alvarez-Buylla et al. (2000) 原文自述聚类"not well supported" |
| 长枝吸引导致错误聚类 | Type I 高替换率可能使其人为靠近 SRF 分支 | Type I 基因进化速率快，长枝吸引是系统发育推断的已知陷阱 | Results 节：作者指出 Type I 长分支特征；Discussion 节提及长枝吸引 |
| 轮藻/绿藻/红藻中无 SRF-type 基因 | 若旧模型成立，SRF-type 应在这些藻类中存在，但从未被发现 | 可能是多次独立丢失（旧模型解释），或 SRF-type 从未存在于该谱系（新模型解释） | Results 节：175 物种调查中 Archaeplastida 无 SRF-type；Discussion 节：parsimony 论证 |
| 结构证据缺失 | 旧模型缺乏蛋白质结构层面的独立验证 | 此前无高精度结构预测工具，晶体结构仅覆盖少数 MADS-box 蛋白 | Methods 节：使用 AlphaFold2/OmegaFold 进行结构预测 |
| 术语混淆 | "Type I/II" 与 "SRF/MEF2" 在不同文献中混用 | 早期分类基于植物内部结构域差异，未与真核生物整体进化对应 | Discussion 节：作者提出术语使用建议 |

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 早期系统发育支持度不足 | Type I 与 SRF 的聚类关系在原始研究中支持度低 | 可用序列数量有限（仅少数拟南芥、动物、真菌序列），长枝吸引效应 | Introduction 节：作者引用 Alvarez-Buylla et al. (2000) 原文自述聚类"not well supported" |
| 长枝吸引导致错误聚类 | Type I 高替换率可能使其人为靠近 SRF 分支 | Type I 基因进化速率快，长枝吸引是系统发育推断的已知陷阱 | Results 节：作者指出 Type I 长分支特征；Discussion 节提及长枝吸引 |
| 轮藻/绿藻/红藻中无 SRF-type 基因 | 若旧模型成立，SRF-type 应在这些藻类中存在，但从未被发现 | 可能是多次独立丢失（旧模型解释），或 SRF-type 从未存在于该谱系（新模型解释） | Results 节：175 物种调查中 Archaeplastida 无 SRF-type；Discussion 节：parsimony 论证 |
| 结构证据缺失 | 旧模型缺乏蛋白质结构层面的独立验证 | 此前无高精度结构预测工具，晶体结构仅覆盖少数 MADS-box 蛋白 | Methods 节：使用 AlphaFold2/OmegaFold 进行结构预测 |
| 术语混淆 | "Type I/II" 与 "SRF/MEF2" 在不同文献中混用 | 早期分类基于植物内部结构域差异，未与真核生物整体进化对应 | Discussion 节：作者提出术语使用建议 |

## 06 核心思想

1. **表面方法**：扩大物种采样（175 个真核生物基因组），提取 MADS 结构域序列进行多方法系统发育分析（ML + Bayesian + NJ），并用 AlphaFold2/OmegaFold 预测代表性 MADS-box 蛋白结构，与已知晶体结构（HsSRF、HsMEF2A、AtSEP3）进行结构相似性比较。

2. **核心洞察**：系统发育和结构预测两个独立证据源一致表明——陆生植物 Type I 和 Type II MADS-box TF 均属于 MEF2-type 谱系，而非传统认为的 Type I↔SRF、Type II↔MEF2 对应关系。SRF-type 基因在 Archaeplastida 祖先中已丢失，Type I/II 的分化是 MEF2-type 祖先在陆生植物祖先中经历一次额外复制后的产物。

3. **可能的普适教训** [Analysis]：
   - 结构预测可作为系统发育推断的独立验证手段，尤其当序列进化速率不均（如 Type I 高替换率）时，结构相似性不易受序列饱和影响。
   - 扩大分类群采样（尤其是关键过渡类群如轮藻）能有效打破长枝，修正早期基于有限数据的假说。
   - 术语体系应反映进化关系而非仅结构域特征，避免因命名导致的概念固化。

## 07 方法总览

- **输入**：175 个真核物种的基因组/蛋白组序列；已知 MADS-box 蛋白序列（拟南芥、人、酵母）作为查询；已知晶体结构（HsSRF 1HBX、HsMEF2A 1EGW、AtSEP3 7NB0）。
- **输出**：MADS-box 基因家族的系统发育树（ML/Bayesian/NJ）；代表性蛋白的预测结构及结构相似性评分。
- **模块**：
  1. 序列检索与注释：BLASTP + CD-Search 提取 MADS 结构域；HMMER + Pfam PF00319 扫描未注释基因。
  2. 多序列比对：MUSCLE（默认参数）；T-coffee 和 MAFFT 用于交叉验证。
  3. 系统发育推断：IQ-TREE 1.6.7（ML，ModelFinder 选 LG 模型，1000 次 ultrafast bootstrap）；Phylobayes v3.2（Bayesian，CAT+GTR，双链收敛）；MEGA11（NJ，P-distance，1000 bootstrap）。
  4. 拓扑检验：AU test（Shimodaira 2002）比较新模型 vs 旧模型约束树。
  5. 结构预测：ColabFold（AlphaFold2）预测代表性序列；OmegaFold 基于单序列预测；maxcluster 计算 TM-score 与已知结构比较。
- **训练**：无监督训练（AlphaFold2/OmegaFold 为预训练模型，本文直接使用）。
- **反馈回路**：系统发育结果与结构预测结果相互印证；AU test 提供统计检验。
- **文字流程**：收集序列 → 提取 MADS 域 → 多方法建树 → 拓扑检验 → 结构预测 → 结构相似性比较 → 综合推断进化模型。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 序列检索与注释（BLASTP + CD-Search + HMMER） | 全面鉴定 175 物种中的 MADS-box 基因 | 避免遗漏未注释基因，确保采样完整性 | 输入：基因组/蛋白组；输出：MADS 结构域序列集 | Methods 节；补充表 S1 | 预期影响：可能遗漏部分 MADS-box 基因，导致系统发育采样偏差 [预期效应] |
| 多方法系统发育推断（ML/Bayesian/NJ） | 构建 MADS-box 基因家族进化树 | 不同方法交叉验证，减少单一方法偏差 | 输入：MADS 域比对；输出：系统发育树 | Results 图 3、4；补充图 S1、S2 | 预期影响：单一方法可能得出不同拓扑 [预期效应] |
| 拓扑检验（AU test） | 统计比较新旧模型 | 提供定量证据拒绝旧假说 | 输入：两种约束树；输出：p 值 | Results 节；补充图 S4 | 预期影响：无法定量评估模型优劣 [预期效应] |
| AlphaFold2 结构预测（ColabFold） | 预测 MADS 域三维结构 | 提供独立于序列的系统发育证据 | 输入：氨基酸序列；输出：预测结构（PDB 格式） | Results 图 2b–d；补充表 S2 | 预期影响：失去结构层面的独立验证 [预期效应] |
| OmegaFold 结构预测 | 基于单序列预测结构 | 排除 MSA 依赖性，验证 AlphaFold2 结果 | 输入：单条序列；输出：预测结构 | Results 图 2e–g；补充表 S3 | 预期影响：无法排除 MSA 偏差 [预期效应] |
| 结构相似性比较（maxcluster/TM-score） | 量化预测结构与已知晶体结构的相似度 | 判断蛋白属于 SRF 还是 MEF2 结构类型 | 输入：预测结构 + 参考结构；输出：TM-score | Results 图 2；补充图 S5 | 预期影响：失去结构分类依据 [预期效应] |

## 09 关键公式符号

本文未使用数学公式。核心定量工具为：

- **TM-score**（Template Modeling score）：用于结构相似性比较，由 Zhang & Skolnick (2005) 提出，范围 [0,1]，>0.5 通常表示相同折叠。本文用 maxcluster 程序计算。
- **AU test**（Approximately Unbiased test）：Shimodaira (2002) 提出的系统发育拓扑检验，基于多尺度 bootstrap 重采样计算 p 值，用于比较竞争拓扑的统计支持度。
- **Ultrafast bootstrap**（UFBoot）：Hoang et al. (2018) 提出的快速 bootstrap 方法，用于 ML 树的节点支持度估计，本文使用 1000 次重复。

## 10 实验设计与证据链

**数据集与群体**：
- 175 个真核物种基因组（覆盖 Archaeplastida、Amorphea、SAR、Cryptista、Haptista、Discoba、Metamonada 等主要真核类群）
- 代表性植物：拟南芥（被子植物）、苏铁、银杏、买麻藤（裸子植物）、蕨类、苔藓植物等
- 结构预测集合：代表性 MADS-box TF 序列（数量未在摘要中明确）

**指标**：
- 系统发育树支持度（UFBoot、Bayesian posterior probability、NJ bootstrap）
- AU test p 值
- TM-score（结构相似性）

**基线/对比**：
- 旧模型（Alvarez-Buylla et al. 2000）：Type I↔SRF、Type II↔MEF2
- 新模型：Type I 和 II 均源自 MEF2-type

**评测协议**：
- 三种系统发育方法（ML/Bayesian/NJ）交叉验证
- 两种结构预测工具（AlphaFold2/OmegaFold）交叉验证
- 拓扑检验（AU test）定量比较

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 175 物种系统发育分析 | SRF/MEF2 古老复制事件 | 三种方法（ML/Bayesian/NJ） | 所有方法均支持 SRF/MEF2 两大分支 | 古老复制事件在真核生物祖先中发生 | 无法确定复制事件的确切时间点 | Results 图 3、4 |
| 植物 Type I/II 聚类位置 | Type I 是否属于 SRF 分支 | 新模型 vs 旧模型约束树 | Type I 和 II 均聚类在 MEF2 分支 | 旧模型被拒绝 | 无法排除极端的趋同进化 | Results 节；补充图 S4 |
| AU test | 新模型是否显著优于旧模型 | 两种拓扑的似然比较 | 旧拓扑被显著拒绝 | 新模型统计支持 | p 值具体数值未在摘要中提供 | 补充图 S4 |
| AlphaFold2 结构预测 | MADS 域结构类型 | 预测结构 vs HsSRF/HsMEF2A 晶体结构 | 植物 Type I/II 均更接近 HsMEF2A | 结构证据支持 MEF2 起源 | 预测结构非实验验证 | Results 图 2b–d |
| OmegaFold 结构预测 | 排除 MSA 依赖 | 单序列预测 vs AlphaFold2 结果 | 与 AlphaFold2 结果一致 | 结构结论稳健 | OmegaFold 精度可能低于 AlphaFold2 | Results 图 2e–g |
| HMM 扫描（PF00319） | 排除注释遗漏 | 基因组扫描 vs 已有注释 | 未发现 Archaeplastida 中 SRF-type 基因 | SRF-type 缺失非注释假象 | HMM 可能漏检高度分化序列 | Methods 节；补充表 S1 |

## 11 结论正确解读

- **任务范围**：本文仅针对 MADS-box TF 家族的进化起源，不涉及 TF–DNA 结合的具体分子机制或结合位点特异性。
- **oracle/真值输入**：系统发育分析依赖序列比对质量；结构预测依赖 AlphaFold2/OmegaFold 的模型精度，无实验解析结构作为金标准。
- **端到端状态**：非端到端。系统发育与结构预测为两个独立模块，结论为两者综合推断。
- **算力成本**：未提供具体算力信息。AlphaFold2 预测通过 ColabFold 在线服务完成。
- **历史数据依赖**：依赖 175 个物种的基因组注释质量；早期分化谱系（如轮藻）的基因组覆盖仍有限。
- **模型依赖**：系统发育结果依赖替换模型选择（LG 为最佳模型）；结构预测依赖 AlphaFold2/OmegaFold 的算法假设。
- **最难情形**：Type I 基因的高替换率导致长枝，是系统发育推断的主要挑战；结构预测对短序列或低复杂度区域可能不可靠。
- **群体/领域边界**：结论适用于绿色植物（Archaeplastida）谱系，外推至其他真核类群需谨慎。
- **不确定性**：作者承认结构预测不能完全排除 SRF 起源的趋同进化可能性（Discussion 节）；AU test 的 p 值具体数值未在摘要中提供。
- **有边界的复述**：在 175 个真核物种的采样范围内，基于多方法系统发育分析和两种结构预测工具的交叉验证，陆生植物 Type I 和 Type II MADS-box TF 最可能均起源于 MEF2-type 祖先基因，SRF-type 基因在 Archaeplastida 祖先中丢失。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 结构预测不能完全排除趋同进化 | 预测的 MEF2 结构可能由 SRF 祖先趋同进化而来 | 需要更多实验解析的 MADS-box 蛋白结构 | Discussion 节 |
| 系统发育分析受限于可用基因组 | 部分关键谱系（如轮藻）基因组覆盖有限 | 更多轮藻和早期分化植物基因组的测序 | Discussion 节 |
| Type I 基因高替换率 | 长枝影响系统发育推断的准确性 | 增加中间谱系采样以打破长枝 | Discussion 节 |
| 术语混淆风险 | "Type I/II" 与 "SRF/MEF2" 混用可能造成误解 | 建议在植物学文献中保留 Type I/II 术语，但明确其 MEF2 起源 | Discussion 节 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 结构预测仅比较 MADS 域，未包含全长蛋白 | 全长蛋白中其他结构域可能影响 MADS 域构象 | MADS 域是 DNA 结合核心，但全长构象可能影响功能 | 对代表性 Type I/II 蛋白进行全长结构预测与比较 | Methods 节：仅提取 MADS 域进行结构预测 |
| 系统发育分析依赖单一 MADS 域比对 | 不同结构域可能提供不同进化信号 | 单一区域可能受选择压力影响产生偏差 | 使用全长蛋白或不同结构域组合进行敏感性分析 | Methods 节：仅使用 MADS 域序列 |
| AU test 结果未提供具体 p 值 | 无法评估拒绝旧模型的强度 | 统计显著性程度影响结论可信度 | 查阅补充材料获取具体 p 值 | 补充图 S4（摘要未提供数值） |
| 175 物种中 Archaeplastida 采样可能偏向模式物种 | 采样偏差可能影响 SRF-type 缺失的推断 | 若未采样的藻类中存在 SRF-type，结论需修正 | 扩展采样至更多红藻、灰藻等早期分化谱系 | 补充表 S1（具体物种列表未在摘要中提供） |
| OmegaFold 精度低于 AlphaFold2 | 两者结果一致可能反映共同偏差而非真实信号 | 独立验证需要不同方法学原理的工具 | 使用 ESMFold 等第三种预测工具交叉验证 | Results 节：作者未讨论工具间精度差异 |
| 未讨论 MADS-box TF 的 DNA 结合特异性差异 | Type I/II 可能识别不同 DNA 基序，影响功能分化 | DNA 结合特异性是 TF 功能的核心 | 结合已知 DNA 结合基序数据进行分析 | 全文未涉及 DNA 结合位点分析 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **结构预测作为系统发育的独立验证**：AlphaFold2/OmegaFold 预测的 MADS 域结构可区分 SRF-type（含 kink）与 MEF2-type（无 kink）的构象差异。此方法可迁移至其他 TF 家族（如 bHLH、WRKY、NAC）的亚家族分类验证，尤其当序列分歧大、系统发育信号弱时。

2. **扩大采样打破长枝**：本文通过纳入轮藻等关键过渡类群，有效修正了早期基于有限采样的错误结论。在 TF–DNA 互作研究中，跨物种采样（尤其是早期分化谱系）有助于识别保守的 DNA 结合机制与衍生变化。

3. **结构域架构与进化起源的区分**：作者建议将「Type I/II」（进化起源）与「M-type/MIKC-type」（结构域架构）术语分离。类似地，在研究 TF 家族时，应区分「系统发育关系」与「功能分类」，避免将结构相似性误认为进化同源性。

4. **MADS 域延伸定义**：作者提出将 MADS 域扩展至包含第二螺旋（I/MEF2 域），因为该螺旋是 DNA 结合功能单元的一部分。对 TF 结构域边界的精确定义直接影响系统发育分析和功能预测的准确性。

5. **结构预测的判别力**：MADS 域中 kink 的有无（SRF vs MEF2）是结构层面的关键判别特征。类似地，其他 TF 家族可能存在结构层面的亚家族特异性特征（如螺旋转角、loop 长度），可用于功能预测。

6. **进化框架指导功能研究**：Type I 从 MEF2-type 祖先通过 K 域丢失演化而来，提示 K 域可能对 DNA 结合特异性或蛋白互作有重要贡献。此思路可迁移至其他 TF 家族：结构域获得/丢失事件可作为功能分化的进化标记。

## 15 与已有知识连接

- **Alvarez-Buylla et al. (2000)**：本文直接挑战并修正其「Type I↔SRF、Type II↔MEF2」模型，是领域内的核心旧假说。
- **Jumper et al. (2021) AlphaFold2**：本文使用 ColabFold 实现，展示了 AlphaFold2 在进化生物学中的应用场景。
- **Wu et al. (2022) OmegaFold**：作为无需 MSA 的替代方法，用于交叉验证结构预测结果。
- **Lai et al. (2021) AtSEP3 晶体结构**：提供了植物 MADS-box 蛋白的实验结构参考（PDB: 7NB0），本文将其作为结构比较的基准之一。
- **Tanabe et al. (2005)**：提供了轮藻 MADS-box 序列，是本文采样扩展的基础。
- **Shimodaira (2002) AU test**：系统发育拓扑检验的标准方法。
- **Zhang & Skolnick (2005) TM-score**：结构相似性比较的常用指标。
- **与 TF–DNA 互作课题的关联**：MADS-box TF 的 DNA 结合特异性（CArG-box）已有较多研究（如 Shore & Sharrocks 1995），本文的进化框架可为理解不同 MADS-box 亚家族（如 MIKC^C 与 MIKC^*）的 DNA 结合差异提供进化背景。未来可将结构预测与 DNA 结合基序分析（如 ChIP-seq、SELEX）结合，探索结构差异如何转化为结合特异性差异。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：MADS-box TF 亚家族 DNA 结合特异性的结构决定因素分析
   - **来源局限/观察**：本文证明 Type I/II 均属 MEF2-type，但两者 DNA 结合特异性差异（如 MIKC^C 与 MIKC^* 识别不同 CArG-box 变体）的分子基础尚不清楚。
   - **核心假设**：Type I 中 I-like 域与 Type II 中 I 域的微小结构差异（由 K 域丢失引起）导致 DNA 结合特异性分化。
   - **初步方法**：对代表性 Type I/II 蛋白进行 AlphaFold2 全长预测，结合分子对接（如 HDOCK、HADDOCK）模拟与不同 CArG-box 变体的结合；用现有 ChIP-seq 数据验证预测的结合基序。
   - **验证方式**：比较预测的 DNA 结合界面残基与实验数据（如突变体表型、EMSA 数据）。
   - **创新状态**：unverified

2. **候选名称**：基于结构预测的 TF 亚家族分类新框架——以植物 TF 家族为测试集
   - **来源局限/观察**：本文展示了结构预测可区分 SRF/MEF2 亚家族，但该方法尚未系统应用于其他植物 TF 家族（如 bHLH、MYB、NAC）。
   - **核心假设**：结构相似性（TM-score）可作为序列相似性的补充，用于 TF 亚家族分类，尤其当序列分歧大时。
   - **初步方法**：选取 5-10 个植物 TF 家族，对每个家族的代表性成员进行 AlphaFold2 预测，计算结构相似性矩阵，与基于序列的系统发育树比较。
   - **验证方式**：检查结构分类是否与已知功能分组（如 DNA 结合基序、蛋白互作伙伴）一致。
   - **创新状态**：unverified

3. **候选名称**：轮藻 MADS-box TF 的 DNA 结合机制——从单基因到家族扩张的进化过渡
   - **来源局限/观察**：轮藻仅有 1-3 个 MADS-box 基因，而陆生植物有 50-100+，家族扩张与 DNA 结合功能分化的关系未知。
   - **核心假设**：轮藻 MADS-box TF 的 DNA 结合特异性较广（低特异性），家族扩张后通过二聚化多样化实现特异性分化。
   - **初步方法**：对轮藻（如 Klebsormidium、Chara）MADS-box 蛋白进行结构预测和 DNA 结合模拟；比较其与陆生植物 Type I/II 的结合界面差异。
   - **验证方式**：如可能，进行体外 DNA 结合实验（EMSA、SELEX）。
   - **创新状态**：unverified

4. **候选名称**：TF 结构域边界定义对系统发育推断的影响——以 MADS-box 为案例
   - **来源局限/观察**：本文提出扩展 MADS 域定义（含第二螺旋），但不同结构域边界定义对系统发育结果的影响未系统评估。
   - **核心假设**：结构域边界选择显著影响系统发育树的拓扑和亚家族分类。
   - **初步方法**：使用不同 MADS 域边界（仅第一螺旋 vs. 含第二螺旋 vs. 全长）分别建树，比较拓扑差异和支持度。
   - **验证方式**：检查不同边界下关键节点的支持度变化，评估结论稳健性。
   - **创新状态**：unverified

5. **候选名称**：TF 结构预测与 DNA 结合基序共进化分析——MADS-box 案例研究
   - **来源局限/观察**：本文未分析 MADS-box TF 的 DNA 结合基序（CArG-box）与结构进化是否协同。
   - **核心假设**：MADS 域结构变化（如 kink 有无）与 DNA 结合基序的进化速率相关。
   - **初步方法**：收集已知 MADS-box TF 的 DNA 结合基序数据（CisBP、JASPAR），与结构预测结果联合分析，检测共进化信号。
   - **验证方式**：统计检验结构特征与基序变异的关联性。
   - **创新状态**：unverified