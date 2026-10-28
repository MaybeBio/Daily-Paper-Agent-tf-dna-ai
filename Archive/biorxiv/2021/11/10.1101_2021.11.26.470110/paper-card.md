## 01 基本信息
- **标题**：AlphaFill: enriching the AlphaFold models with ligands and co-factors
- **作者**：Hekkelman ML; de Vries I; Joosten RP; Perrakis A
- **单位**：荷兰癌症研究所（Netherlands Cancer Institute）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2021
- **论文类型**：方法学/资源型论文（算法 + 数据库资源）
- **领域**：结构生物信息学；蛋白质结构预测后处理；配体/辅因子注释
- **关键词**：AlphaFold、配体移植、辅因子、PDB-REDO、结构注释
- **DOI/ID**：10.1101/2021.11.26.470110
- **代码**：https://github.com/PDB-REDO（AlphaFill、libcif++、libpdb-redo）
- **数据**：https://alphafill.eu（数据库 + rsync下载）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文不直接预测TF–DNA互作，但提供了一种基于同源结构"移植"小分子/离子到AlphaFold模型的方法。对TF–DNA课题的可迁移价值在于：①为AlphaFold预测的TF结构补充金属离子（如锌指结构域的Zn²⁺）和辅因子，这些对DNA结合构象和稳定性至关重要；②其"同源结构→局部结构比对→移植配体"的流程可类比迁移到"同源TF–DNA复合物→移植DNA片段"的尝试；③其关于移植后模型精度边界（定性可用、定量不可用）的讨论对使用AI预测结构做分子模拟（MD）的初始化具有直接参考意义。

## 02 一句话总结
本文提出AlphaFill算法，通过将AlphaFold预测模型与PDB-REDO实验结构中同源蛋白的序列和结构比对，将常见辅因子、金属离子和小分子配体"移植"到预测模型上，构建了包含21,899个"填充"模型的AlphaFill数据库，并明确这些模型仅适用于定性分析而非定量互作测量。

## 03 研究问题
- **具体问题**：AlphaFold预测的蛋白质结构仅包含氨基酸残基坐标，缺少对蛋白质折叠稳定性和功能至关重要的辅因子、金属离子和小分子配体。如何系统性地为AlphaFold模型补充这些化学实体？
- **为什么重要**：许多蛋白质（如血红蛋白、锌指蛋白、激酶）在没有辅因子/离子时无法正确折叠或执行功能。缺少这些化学实体的模型会误导功能解读和实验设计，尤其对金属依赖性DNA结合蛋白（如锌指TF）影响显著。
- **现有方法不足**：AlphaFold数据库本身仅提供到PDBe-Knowledge Base的链接，指向同一蛋白的实验结构，但未系统地将同源蛋白中的配体信息迁移到预测模型上；且不覆盖无实验结构的同源场景。
- **精确研究问题**："Can we reliably transplant biologically relevant small molecules and ions from homologous experimental structures to AlphaFold-predicted protein models based on sequence and structure similarity?"

## 04 背景与发展脉络
*（注：以下脉络为「经外部核验」+「本文框架」混合，已分别标注）*

1. **AlphaFold时代之前**：结构生物学依赖实验方法（X-ray、NMR、Cryo-EM）获取蛋白结构，配体/辅因子在实验结构中天然存在。同源建模（如SWISS-MODEL）虽可预测结构，但配体处理通常需手动或依赖专门工具。
2. **AlphaFold/AlphaFold2（2020-2021）**：AI结构预测实现高精度单链结构预测，但输出仅含氨基酸坐标，不含配体、离子、核酸等非蛋白实体。AlphaFold数据库（2021年11月，365,198个模型）大规模发布，加剧了"有结构无配体"的问题。
3. **AlphaFold Multimer/RoseTTAFold（2021）**：扩展至多聚体预测，但仍不处理小分子配体。
4. **本文位置（2021）**：首次提出系统性的配体"移植"（transplantation）策略，利用PDB-REDO优化后的实验结构作为配体来源，通过序列同源性和局部结构比对将配体放入预测模型。属于AlphaFold后处理/注释方向的开创性工作。
5. **后续方向（本文展望）**：作者明确指出未来应发展基于结构相似性（而非仅序列相似性）的配体移植方法，并提及深度学习可能在此发挥作用——这与当前"结构比对+深度学习配体定位"的研究趋势一致。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| AlphaFold模型缺少辅因子/离子 | 血红蛋白无血红素、锌指无Zn²⁺、激酶无ATP/ADP | AlphaFold仅以氨基酸序列为输入，不预测非蛋白化学实体 | Abstract："all these structures lack cofactors essential for their structural integrity and molecular function" |
| 缺少配体导致功能解读困难 | 无法判断蛋白是否处于活性构象、无法设计突变/药物实验 | 配体对蛋白折叠稳定性和催化/结合功能至关重要 | Introduction："Cofactors, ligands, and ions help to understand both the function and structural integrity of proteins" |
| 同源配体信息未系统利用 | AlphaFold数据库仅链接同一蛋白的实验结构，不覆盖同源场景 | 数据库设计未包含跨物种/跨同源物的配体迁移 | Introduction："we do not limit the mapping to identical sequences, but we extend it to homologues" |
| 移植配体的可靠性难以评估 | 用户无法判断移植的配体位置是否可信 | 缺乏系统的质量指标（全局/局部RMSD） | Results："The RMSD of this local alignment is stored in the AlphaFill metadata" |
| 配体来源选择标准模糊 | 同源蛋白可能含多种配体，需人工筛选生物学相关者 | 需人工构建"可移植化合物列表" | Methods："The selection of biological relevant molecules...based on the number of occurrences in the PDB" |

## 06 核心思想

### 1) 表面方法
AlphaFill是一个基于序列同源性和结构比对的配体移植算法：将AlphaFold模型序列BLAST到PDB-REDO序列数据库，筛选同源实验结构，对每个候选配体进行局部结构比对（基于Cα原子），若局部RMSD足够低则将配体坐标直接"复制"到预测模型中。

### 2) 核心洞察
- **同源结构是配体位置的可靠先验**：蛋白质的配体结合位点在进化中高度保守，同源蛋白中配体的结合位置可以迁移到预测结构上，前提是局部结构足够相似。
- **"移植"而非"对接"**：作者选择直接坐标移植而非分子对接，因为对接需要精确的侧链构象和能量函数，而AlphaFold模型的侧链精度不足以支撑可靠对接；移植则绕开了能量计算，直接利用实验结构的配体坐标。
- **全局RMSD与局部RMSD的双重质量控制**：全局RMSD反映整体折叠一致性，局部RMSD反映配体周围环境的可靠性，两者结合可区分"可信移植"与"低置信度移植"。

### 3) 可能的普适教训 [Analysis]
- **对AI预测结构，后处理注释与预测本身同等重要**：AlphaFold解决了主链折叠问题，但功能注释（配体、离子、互作伙伴）需要额外的同源信息迁移策略。
- **"局部质量"比"全局质量"更关键**：对于配体/离子结合位点，局部结构精度（配体周围6Å内的残基）决定了移植的可靠性，而非整体折叠精度。
- **定性与定量的边界必须明确**：作者反复强调AlphaFill模型仅适用于定性分析，不适用于定量测量（如精确的金属-配体距离），这种"能力边界声明"对任何基于AI预测结构的衍生资源都至关重要。

## 07 方法总览

- **输入**：AlphaFold模型（蛋白质坐标文件，仅含氨基酸残基）；PDB-REDO实验结构数据库（配体来源）；人工构建的"可移植化合物列表"（400种常见辅因子/离子/配体）
- **输出**：AlphaFill模型（AlphaFold坐标 + 移植的配体/离子坐标）；JSON格式元数据（记录每个移植配体的来源、全局/局部RMSD、序列一致性等）
- **核心模块**：
  1. **序列检索**：BLAST将AlphaFold模型序列比对到PDB-REDO序列数据库
  2. **同源筛选**：过滤序列一致性≥70%、比对长度≥85残基的同源结构
  3. **结构比对**：基于Cα原子进行全局结构比对（使用PDB-REDO的比对工具）
  4. **配体扫描**：检查同源结构中的可移植化合物，对每个配体提取周围6Å内的骨架原子进行局部比对
  5. **坐标移植**：将配体坐标（含交替构象）直接复制到AlphaFold模型中
  6. **元数据生成**：记录每个移植的详细信息（来源PDB条目、链、RMSD、序列一致性等）
- **训练**：无监督/无训练——算法基于几何比对而非机器学习
- **反馈回路**：无（一次性处理，无迭代优化）
- **假设**：①同源蛋白的配体结合位点结构保守；②局部结构比对RMSD可反映移植可靠性；③70%序列一致性阈值足以保证配体结合位点保守性

**文字流程**：AlphaFold模型 → BLAST到PDB-REDO序列库 → 筛选同源结构（≥70%一致性，≥85残基） → 全局Cα结构比对 → 扫描可移植化合物 → 对每个配体提取周围6Å骨架原子做局部比对 → 若局部RMSD可接受则移植坐标 → 生成mmCIF + JSON元数据 → 存入AlphaFill数据库

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 序列检索（BLAST） | 找到与AlphaFold模型同源的实验结构 | 同源结构是配体移植的信息来源 | 输入：AlphaFold序列；输出：候选同源结构列表 | Methods："The sequence of the AlphaFold model is BLASTed against the sequence file of the LAHMA webserver" | 无此模块则无法找到配体来源；预期影响：完全失效 [预期] |
| 同源筛选（≥70%一致性，≥85残基） | 过滤低质量同源匹配 | 低一致性同源物的配体结合位点可能不保守 | 输入：BLAST结果；输出：过滤后的同源结构 | Methods："the sequence identity cutoff is currently 70% over an aligned sequence of at least 85 residues" | 降低阈值可增加覆盖率但引入假阳性移植 [预期]；提高阈值则减少覆盖率 |
| 全局结构比对（Cα） | 评估整体折叠一致性 | 全局RMSD是移植可靠性的第一层指标 | 输入：AlphaFold模型+同源结构；输出：全局RMSD | Results："The root-mean-square deviation (RMSD) of this global alignment is stored in the AlphaFill metadata" | 无此模块则无法提供全局质量指标 [预期] |
| 局部结构比对（配体周围6Å） | 评估配体结合位点的局部结构一致性 | 配体移植的可靠性取决于局部而非全局结构相似性 | 输入：配体周围6Å骨架原子；输出：局部RMSD | Results："All backbone atoms within 6Å are then used for a local structural alignment" | 无此模块则无法区分"整体相似但局部不相似"的案例 [预期] |
| 配体坐标移植 | 将配体从实验结构复制到预测模型 | 直接移植避免了对接的不确定性 | 输入：同源结构中的配体坐标；输出：AlphaFill模型中的配体坐标 | Results："Compounds are then integrated into the AlphaFold model" | 无此模块则整个方法不成立 [预期] |
| 去重/冲突检测 | 避免同一配体重复移植（3.5Å距离阈值） | 多个同源结构可能含相同配体 | 输入：候选移植列表；输出：去重后的移植结果 | Results："unless the same compound is already placed within 3.5Å of the centroid" | 无此模块则产生冗余配体 [预期] |
| 元数据生成 | 记录每个移植的来源和质量指标 | 用户需要评估移植的可靠性 | 输入：移植过程信息；输出：JSON元数据 | Results："a JSON-formatted metadata file describing the provenance" | 无此模块则用户无法判断移植质量 [预期] |

## 09 关键公式符号

本文为算法/资源型论文，未使用数学公式。核心的量化指标为：

- **序列一致性（Sequence Identity）**：BLAST比对中相同残基比例，阈值≥70%
- **比对长度（Alignment Length）**：有效比对残基数，阈值≥85残基
- **全局RMSD**：Cα原子全局结构比对的均方根偏差，存储于元数据
- **局部RMSD**：配体周围6Å内骨架原子的局部比对的均方根偏差，存储于元数据
- **距离阈值**：3.5Å（判断配体是否已存在）、6Å（定义配体周围区域）

## 10 实验设计与证据链

### 数据集与规模
- **输入数据**：AlphaFold数据库全部模型（2021年11月版本，365,198个模型）
- **配体来源**：PDB-REDO数据库（本地副本，2021年11月1日版本）
- **化合物列表**：400种（基于PDB出现频率≥1600次 + CoFactor数据库辅因子）
- **计算资源**：48线程Intel Xeon E5-2697 CPU，总耗时10天14.5小时
- **平均运行时间**：每模型约2分钟（单线程）

### 评测协议
- **无定量基准测试**：本文未提供与金标准（如实验结构中的真实配体位置）的系统性定量比较
- **定性验证**：通过视觉检查（Coot、CCP4mg）和案例展示验证移植合理性
- **案例选择**：肌红蛋白（血红素）、锌指蛋白（Zn²⁺）、激酶（ATP/ADP）、ENPP家族（双金属锌位点）

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| 全数据库运行 | AlphaFill可规模化应用于所有AlphaFold模型 | 365,198个模型，48线程 | 21,899个模型获得至少一个移植配体；共移植108,997个化合物 | 方法可规模化，约6%模型有可移植配体 | 未评估移植配体的位置精度 | Results："21,899 models that had at least one transplanted compound" |
| 肌红蛋白案例 | 血红素可移植到预测结构 | AlphaFold模型AF-P02144 vs 实验结构 | 血红素成功移植，配体结合腔清晰可见 | 定性分析可行 | 未提供定量距离/相互作用能验证 | Results："has a heme shaped cavity that can readily be supplemented" |
| 锌指蛋白案例 | 结构Zn²⁺可移植 | 锌指基序的Cys/His配位 | Zn²⁺移植到预测的配位位点 | 结构金属离子可移植 | 配位几何有偏差（作者承认） | Results："tetrahedral zinc binding site looks proper, but the atomic distances...deviate substantially" |
| ENPP家族案例 | 双金属催化位点可移植 | ENPP1-7家族比对 | 两个Zn²⁺均移植成功 | 多金属位点可同时移植 | 未验证催化活性 | Results："zinc atoms and the residues that coordinate them occupy highly similar positions" |
| 激酶案例（ABL1） | ATP/ADP可区分激酶状态 | ABL1模型AF-P00519，ATP vs ADP移植 | 全局/局部RMSD可区分ATP结合态更优 | RMSD可作为状态指示器 | 仅单一案例，非系统验证 | Results："suggesting that the structure is more representative to the ATP-bound state" |

## 11 结论正确解读

- **任务范围**：本文解决的是"为AlphaFold预测模型补充常见辅因子/离子/小分子"的注释问题，不涉及配体诱导的构象变化预测，也不涉及全新配体结合位点发现。
- **Oracle/真值输入**：配体坐标直接来自实验结构（PDB-REDO），非预测或对接产生；"真值"即实验结构中配体的实验坐标。
- **端到端状态**：AlphaFill是端到端的自动化流程（输入序列/模型→输出带配体模型），但配体列表是人工构建的封闭集合（400种），非开放发现。
- **算力成本**：平均2分钟/模型（单线程），全库运行约10天（48线程），成本可控。
- **历史数据依赖**：依赖PDB-REDO数据库的覆盖度；对无同源实验结构（<70%一致性）的蛋白无效。
- **模型依赖**：依赖AlphaFold模型质量；对低pLDDT区域（柔性环、结构域间连接区）的配体移植不可靠。
- **最难情形**：①配体结合位点位于低置信度区域；②同源物中配体结合模式不同（如不同构象状态）；③多亚基界面处的配体（AlphaFold单体模型无法处理）。
- **不确定性**：作者明确声明模型仅适用于定性分析，不适用于定量测量（如精确的金属-配体距离、氢键几何）；移植配体的精确位置可能有显著偏差。
- **边界复述**：AlphaFill为AlphaFold模型提供了基于同源实验结构的配体/辅因子注释，覆盖约6%的AlphaFold模型，其输出适合作为功能解读和实验设计的定性参考，不适合作为定量结构分析的输入。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 配位几何不精确 | 锌指蛋白中Zn²⁺与配体原子距离偏离目标值 | 建议用户对移植位点进行进一步优化/精修 | Results："the atomic distances between the zinc atom and its ligands deviate substantially from previously established target values" |
| 仅限序列同源移植 | 依赖BLAST序列同源性，无法处理无同源实验结构的情况 | 应发展基于结构相似性的移植方法 | Discussion："AlphaFill by definition depends on homology as the first and major criterion" |
| 化合物列表有限 | 仅400种常见化合物，不覆盖所有可能配体 | 列表可扩展，文件格式支持更新 | Methods："stored as a cif-formatted file separate from the AlphaFill program to allow easy extension" |
| 不处理构象状态 | 无法区分同一蛋白的不同功能构象状态 | 提及深度学习可能解决 | Discussion："future work should aim to increase the accuracy" |
| 非定量精度 | 模型不适合精确测量互作 | 建议结合分子动力学模拟等进一步精修 | Discussion："not meant or suitable for precise quantification of interactions" |
| 多聚体界面配体缺失 | AlphaFold单体模型无法处理亚基界面配体 | 未明确提及 | Discussion（隐含） |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 70%序列一致性阈值缺乏系统优化 | 可能过高（漏掉远同源但结构保守的配体位点）或过低（引入假阳性） | 阈值直接影响覆盖率和精度平衡 | 对不同阈值（如30%、50%、70%）进行系统评测，比较移植配体与实验结构的距离误差 | Methods："the sequence identity cutoff is currently 70%" |
| 局部RMSD作为质量指标可能不足 | 局部RMSD低不代表配体-蛋白互作模式正确（如侧链取向、氢键网络） | 用户可能过度信任低RMSD的移植 | 对移植配体进行分子动力学模拟或对接验证，比较互作能量 | Results："The RMSD of this local alignment is stored in the AlphaFill metadata" |
| 未提供定量验证基准 | 无与实验结构的系统性比较（如配体重原子RMSD分布） | 无法客观评估方法精度 | 构建测试集：对已知实验结构的蛋白，删除配体后用AlphaFold预测并移植，比较配体位置误差 | 全文未提供定量基准 |
| 案例选择偏向"成功案例" | 肌红蛋白、锌指、激酶均为配体结合位点高度保守的经典体系 | 可能高估方法在困难案例上的表现 | 在随机/困难案例（如配体诱导构象变化大的蛋白）上测试 | Results案例部分 |
| 未讨论配体移植对下游计算的影响 | 移植配体是否适合作为MD模拟起点？是否需要先做能量最小化？ | 对使用AlphaFill做MD初始化的用户至关重要 | 对移植模型做MD模拟，比较与实验结构的稳定性差异 | Discussion："not meant or suitable for precise quantification" |
| 化合物列表构建标准不透明 | 基于PDB频率和CoFactor数据库，但具体筛选标准未详述 | 影响可重复性和扩展性 | 检查列表构建代码/标准 | Methods："based on the number of occurrences in the PDB" |

## 14 学到什么
*（Agent 提炼的知识候选）*

1. **同源结构信息迁移是AI预测结构功能注释的有效策略**：当预测模型缺少功能关键的非蛋白组分时，利用同源实验结构进行"移植"比从头预测或对接更可靠。可迁移到TF–DNA课题：尝试从同源TF–DNA复合物实验结构中移植DNA片段到AlphaFold预测的TF结构上，作为后续MD模拟的起点。
2. **"局部质量"指标比"全局质量"更适用于配体/互作位点评估**：AlphaFill使用配体周围6Å的局部RMSD作为移植可靠性指标，而非全局RMSD。对TF–DNA课题的启示：评估预测TF结构时，应重点关注DNA结合结构域（DBD）的局部结构质量（如pLDDT、局部RMSD），而非整体模型质量。
3. **明确"定性可用、定量不可用"的能力边界**：AlphaFill明确声明其输出仅适用于定性分析，不适用于定量互作测量。对TF–DNA课题的启示：任何基于AI预测结构的互作分析（如预测TF–DNA结合亲和力）都应明确声明精度边界，避免过度解读。
4. **人工构建的化合物列表是可控的初始方案**：AlphaFill通过人工筛选400种常见化合物，避免了开放集合的复杂性。对TF–DNA课题的启示：可先构建"TF–DNA互作相关辅因子/离子"的封闭列表（如Zn²⁺、Mg²⁺、Ca²⁺、血红素等），聚焦常见体系。
5. **元数据记录移植来源是资源可信度的关键**：AlphaFill为每个移植配体记录来源PDB条目、RMSD、序列一致性等，使用户可追溯。对TF–DNA课题的启示：构建任何AI预测结构的衍生资源时，应保留完整的来源和置信度元数据。
6. **结构比对中的"局部环境"检查可避免错误移植**：AlphaFill的案例中，MSH2的额外ADP移植被识别为错误（来自链间交叉），说明需要检查配体周围环境的合理性。对TF–DNA课题的启示：移植DNA片段时需检查DNA结合残基的取向和静电环境是否与实验结构一致。

## 15 与已有知识连接

- **AlphaFold2（Jumper et al., Nature 2021）**：本文直接基于AlphaFold数据库输出，解决其"无配体"的固有局限。TF–DNA课题中，AlphaFold2对TF单体结构预测精度高，但无法预测DNA结合状态，AlphaFill的思路可部分弥补。
- **PDB-REDO（Joosten et al., Acta Cryst D 2014）**：本文的配体来源，提供优化后的实验结构，比原始PDB条目更适合作为配体移植模板。TF–DNA课题中，使用PDB-REDO优化的TF–DNA复合物结构作为模板更可靠。
- **AlphaFold Multimer（Evans et al., 2021）**：可预测蛋白-蛋白复合物，但不处理蛋白-核酸互作。AlphaFill与AlphaFold Multimer互补，分别处理"配体/离子"和"蛋白互作伙伴"。
- **分子动力学模拟（MD）**：AlphaFill模型可作为MD模拟的初始结构，但作者明确警告需要进一步精修。TF–DNA课题中，AlphaFill移植的金属离子（如锌指Zn²⁺）可作为MD模拟的起点，但需先做能量最小化和平衡。
- **DNA对接工具（如HADDOCK、ZDOCK）**：AlphaFill的"移植"策略与对接方法互补——移植依赖同源结构，对接不依赖同源但计算成本高。TF–DNA课题中，可先用AlphaFill思路移植DNA获得初始复合物，再用对接工具优化。
- **候选方向（未验证）**：作者提及"基于深度学习的结构比对配体移植"是未来方向——这与当前"几何深度学习用于配体定位"的研究趋势一致，可关注后续工作。

## 16 研究想法
*（Agent 生成的研究候选）*

### 候选1：AlphaFill-TF——面向转录因子DNA结合结构域的辅因子与DNA片段移植工具
- **来源局限/观察**：AlphaFill仅移植小分子/离子，不处理DNA/RNA等大分子配体；且其70%序列一致性阈值对TF家族（如C2H2锌指、homeodomain）可能过严。
- **核心假设**：TF的DBD结构在家族内高度保守，DNA结合模式（如锌指- DNA识别）可跨物种移植。
- **增量**：扩展AlphaFill策略到DNA片段移植，针对TF家族优化同源性阈值和局部比对策略。
- **初步方法**：收集TF–DNA复合物实验结构，对AlphaFold预测的TF结构进行DBD局部比对，移植DNA片段并评估界面残基兼容性。
- **验证方式**：与实验复合物结构比较DNA位置RMSD；用MD模拟评估复合物稳定性。
- **创新状态**：unverified

### 候选2：基于pLDDT加权的配体移植置信度评分
- **来源局限/观察**：AlphaFill使用全局/局部RMSD作为质量指标，但未利用AlphaFold自身的pLDDT置信度信息。
- **核心假设**：配体结合位点所在区域的pLDDT值可预测移植可靠性——高pLDDT区域的移植更可信。
- **增量**：将pLDDT加权整合到AlphaFill的移植决策中，提供更精细的置信度分层。
- **初步方法**：对AlphaFill移植结果按配体周围残基的平均pLDDT分层，与实验结构比较验证相关性。
- **验证方式**：统计pLDDT与移植配体位置误差的相关性；构建ROC曲线评估pLDDT作为过滤器的效果。
- **创新状态**：unverified

### 候选3：TF–DNA复合物中金属离子介导的DNA结合构象分析
- **来源局限/观察**：AlphaFill案例显示锌指Zn²⁺移植后配位几何有偏差，但未深入分析金属离子对DNA结合构象的影响。
- **核心假设**：结构锌离子（如锌指）的精确配位几何影响DBD的DNA结合面取向，AlphaFold预测的apo结构可能无法准确呈现holo构象。
- **增量**：系统比较AlphaFold预测的锌指TF结构与实验holo结构的DBD构象差异，量化Zn²⁺对构象的影响。
- **初步方法**：收集含锌指TF的AlphaFold模型与实验复合物结构，比对DBD区域并分析Zn²⁺配位残基的构象差异。
- **验证方式**：统计DBD Cα RMSD与Zn²⁺存在与否的相关性；MD模拟验证Zn²⁺对构象稳定性的贡献。
- **创新状态**：unverified

### 候选4：AlphaFill移植配体作为MD模拟初始结构的系统评估
- **来源局限/观察**：作者声明AlphaFill模型"不适合定量分析"，但未系统评估其作为MD模拟起点的可行性。
- **核心假设**：经过适当能量最小化和平衡，AlphaFill移植的配体/离子可以作为MD模拟的有效起点，且优于无配体的apo结构。
- **增量**：为TF–DNA课题提供"AlphaFill模型→MD模拟"的标准工作流和评估基准。
- **初步方法**：选取多个TF–DNA体系，分别从AlphaFill模型和apo结构启动MD模拟，比较模拟轨迹中配体/离子稳定性。
- **验证方式**：配体RMSD随时间演化；配位键长分布与实验值比较；蛋白-配体相互作用能。
- **创新状态**：unverified

### 候选5：基于结构比对的TF–DNA复合物"移植"与对接方法的系统比较
- **来源局限/观察**：AlphaFill的移植策略与分子对接（如HADDOCK）在原理上互补，但无系统比较。
- **核心假设**：对高同源性的TF–DNA体系，移植策略优于对接；对低同源性体系，对接更可靠。
- **增量**：为TF–DNA复合物建模提供方法选择指南。
- **初步方法**：构建TF–DNA测试集，分别用AlphaFill式移植和HADDOCK对接建模，与实验结构比较。
- **验证方式**：DNA位置RMSD、界面接触残基恢复率、结合能预测精度。
- **创新状态**：unverified