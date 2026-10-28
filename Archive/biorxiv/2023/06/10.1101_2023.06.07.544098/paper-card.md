## 01 基本信息

- **标题**：Calling Cards: a customizable platform to longitudinally record protein-DNA interactions over time in cells and tissues
- **作者**：Allen Yen; Chase Mateusiak; Simona Sarafinovska; Mariam A. Gachechiladze; Juanru Guo; Xuhua Chen; Arnav Moudgil; Alexander J. Cammack; Jessica Hoisington-Lopez; MariaLynn Crosby; Michael R. Brent; Robi D. Mitra; Joseph D. Dougherty
- **单位**：Washington University in Saint Louis（圣路易斯华盛顿大学，遗传学系等；具体单位列表未提供）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2023-06-09
- **论文类型**：方法学/实验方案（Protocol）论文，含方法验证与示例数据
- **领域**：基因组学、蛋白质-DNA互作、表观遗传学、基因调控
- **关键词**：Calling Cards、piggyBac转座酶、蛋白-DNA互作、长期记录、TF结合、增强子、BRD4、下一代测序
- **DOI/ID**：10.1101/544098（bioRxiv ID：2023.06.07.544098）
- **代码**：nf-core/callingcards（https://nf-co.re/callingcards）；pycallingcards（https://github.com/The-Mitra-Lab/pycallingcards）
- **数据**：GEO GSE223926（https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE223926）
- **阅读日期**：未提供
- **在该方向中的位置**：本文属于「蛋白质-DNA互作（聚焦TF–DNA结合机制）× 实验方法」方向，提供了一种不依赖抗体的、基于转座酶的、可累积记录TF–DNA结合事件的平台技术。与AI/深度学习或物理模拟（MD/对接/结构预测）无直接关联，但其产生的长期累积结合数据可作为AI模型（如TF结合位点预测、增强子-启动子互作建模）的训练或验证数据来源，也可为物理模拟提供时间维度的结合动态参考。

---

## 02 一句话总结

本文提出并详细描述了Calling Cards平台——利用piggyBac转座酶在TF结合位点附近插入自我报告转座子（SRT），通过RNA测序恢复插入位点，从而在细胞和组织中累积记录一段时间内的蛋白-DNA互作事件，并提供了从实验设计到数据分析的完整操作流程。

---

## 03 研究问题

- **具体问题**：如何在不依赖抗体、不需要破坏细胞的情况下，在特定细胞类型中长时间记录瞬时的蛋白-DNA互作事件，并将这些历史分子事件与最终的细胞状态或表型关联起来？
- **为什么重要**：现有的蛋白-DNA互作检测方法（如ChIP-seq、CUT&RUN、CUT&Tag）只能提供取样时刻的静态快照，无法记录时间维度上的累积结合历史。而发育、衰老和疾病中的基因调控变化往往是动态的、累积的，需要一种能够记录历史事件的方法来理解因果关系。
- **现有方法不足**：
  - ChIP-seq需要高质量抗体，且需要大量起始材料，难以用于稀有细胞类型。
  - CUT&RUN/CUT&Tag虽然降低了起始材料需求，但仍依赖抗体，且仍是快照式测量。
  - 时间序列实验需要多个时间点取样，成本高且无法在同一细胞中追踪历史。
  - 现有方法无法将历史分子事件与最终表型在同一细胞中直接关联。
- **精确研究问题**：Can a genetically encoded, transposase-based system record cumulative protein-DNA interaction events over time in specific cell types, without antibodies, and enable correlation of historical molecular states with eventual cellular outcomes?

---

## 04 背景与发展脉络

**注：以下脉络基于本文框架整理，未经外部系统核验。**

1. **早期阶段：酵母中的Calling Cards（~2008）**
   - 方法：使用Ty5整合酶和TF-Sir4蛋白融合体在酵母中记录TF结合。
   - 优点：首次证明了转座子/整合酶系统可用于记录蛋白-DNA互作。
   - 局限：Ty5系统在哺乳动物中效率低，不适用。

2. **过渡阶段：转向piggyBac转座酶系统（~2012-2020）**
   - 方法：利用piggyBac转座酶的高活性跨物种特性，开发hyPB（hyperactive piggyBac）系统。
   - 优点：piggyBac在哺乳动物细胞中高效，且偏好插入基因组中开放的染色质区域。
   - 关键改进：开发SRT（self-reporting transposon），使插入事件可通过RNA-seq检测，大幅提高灵敏度。

3. **当前阶段：哺乳动物体内应用与平台化（2020-2023）**
   - 方法：Cre依赖的FrontFlip-hyPB系统，实现细胞类型特异性记录；引入条形码SRT，支持多重化。
   - 优点：可在复杂组织（如脑）中记录特定细胞类型的增强子使用和TF结合；与RNA-seq兼容，可同时测量转录组。
   - 局限：无法解析时间顺序；插入事件数相对较低；需要遗传递送。

4. **本文位置**：本文是Calling Cards技术的综合实验方案（Protocol），整合了此前分散的方法学进展，提供了标准化的五步流程（试剂递送→样本采集→RNA提取→文库制备→测序分析），并配套发布了nf-core/callingcards计算流程，使该技术对更广泛的研究者开放。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有方法无法记录时间维度 | ChIP-seq/CUT&RUN只能提供取样时刻的快照，无法追溯历史结合事件 | 这些方法在取样时破坏细胞，只能反映当下状态 | Introduction: "ChIP-seq...only provides a snapshot of states at the time of harvest" |
| 抗体依赖性 | ChIP-seq/CUT&RUN需要高质量特异性抗体，许多TF缺乏可靠抗体 | 抗体质量参差不齐，且难以针对所有TF开发 | Introduction: "ChIP-seq requires high quality antibodies" |
| 起始材料需求大 | ChIP-seq需要大量细胞，难以用于稀有细胞类型或小组织样本 | 免疫沉淀步骤需要足够的染色质输入 | Introduction: "relatively large amounts of starting material" |
| 无法在特定细胞类型中记录 | 复杂组织中难以分离特定细胞类型进行检测 | 组织异质性导致信号稀释 | Introduction: "not easily adaptable to query targeted cell populations" |
| 无法关联历史与结局 | 无法将早期分子事件与最终表型在同一细胞中关联 | 快照式测量无法提供时间因果信息 | Introduction: "enables correlation of historical molecular states to eventual outcomes or phenotypes" |
| 转座子插入的潜在毒性 | 转座子插入可能破坏基因功能 | 转座酶活性可能导致基因组不稳定 | Limitations节: "the readout...is unable to resolve the temporal order of insertions"（间接提及插入的随机性） |

---

## 06 核心思想

### 1) 表面方法
Calling Cards平台利用piggyBac转座酶（hyPB）与目标TF融合（或利用天然BRD4结合），当TF结合DNA时，hyPB将SRT转座子插入附近基因组位点。SRT包含EF1α启动子驱动的tdTomato报告基因（无polyA信号），插入后可从插入位点向侧翼基因组转录，产生包含插入位点信息的嵌合转录本。通过RNA-seq捕获这些转录本，即可定位插入位点，从而推断TF的结合位置。由于转座事件是永久性的，插入会随细胞分裂保留，因此可以累积记录整个实验期间的结合事件。

### 2) 核心洞察
- **将瞬时事件转化为永久记录**：转座酶将瞬时的蛋白-DNA结合事件转化为基因组中的永久标记，使得"历史"可以被"读取"。
- **RNA作为读取介质**：通过SRT的转录产生嵌合RNA，使插入位点可通过RNA-seq检测，与转录组分析天然兼容。
- **无需抗体**：利用TF-转座酶融合蛋白或天然蛋白-蛋白互作（如BRD4-hyPB），绕过了抗体依赖。
- **细胞类型特异性**：通过Cre依赖的FrontFlip-hyPB或细胞类型特异性启动子，实现特定细胞类型的记录。

### 3) 可能的普适教训 [Analysis]
- **"写入-读取"分离的架构**：将分子事件的记录（写入）与检测（读取）分离，是设计时间维度分子记录系统的通用原则。类似思路也见于CRISPR-Cas9介导的基因组编辑记录系统。
- **利用内源机制**：piggyBac转座酶偏好插入开放染色质区域，这一特性天然富集了调控区域，提高了信噪比。
- **条形码化实现多重化**：通过引入条形码，可以在同一实验中同时追踪多个TF或样本，这是高通量实验设计的通用策略。

---

## 07 方法总览

- **输入**：
  - 目标细胞/组织（体外培养细胞或体内小鼠组织）
  - Calling Cards试剂：TF-hyPB融合蛋白表达质粒（或hyPB）+ SRT供体质粒/AAV病毒
  - （可选）Cre重组酶表达系统（用于细胞类型特异性）
- **输出**：
  - qBED文件：包含每个SRT插入的基因组坐标、链方向、测序深度、SRT条形码
  - 峰值（peaks）：插入富集区域，代表TF结合位点或增强子区域
  - 差异插入区域：不同条件/时间点之间的差异结合
- **模块**：
  1. 试剂制备与递送（Basic Protocol 1）：质粒扩增、AAV包装、体外转染或体内注射
  2. 样本采集（Basic Protocol 2）：RNA提取（TRIzol法）
  3. 文库制备（Basic Protocol 3）：逆转录、SRT特异性扩增、tagmentation、indexing
  4. 测序（Basic Protocol 4）：Illumina平台，建议PE150
  5. 数据分析（Basic Protocol 5）：nf-core/callingcards流程
- **训练**：不适用（非机器学习方法）
- **工具**：
  - nf-core/callingcards（Nextflow流程）
  - pycallingcards（Python包，含CCcaller和Blockify峰值调用器）
  - UMItools（条形码处理）、trimmomatic（接头修剪）、FastQC（质控）
  - BEDtools（基因组区间操作）
- **反馈回路**：文库密度qPCR（Basic Protocol 3中的可选步骤）用于评估SRT丰度，决定是否继续文库制备
- **假设**：
  - TF-hyPB融合蛋白保留TF的DNA结合特异性
  - 转座酶插入位点与TF结合位点在基因组上邻近（~1kb内）
  - SRT插入是随机的，且不偏向特定序列（除TTAA位点偏好）
  - RNA-seq能有效捕获SRT嵌合转录本

**文字流程**：
1. 构建TF-hyPB融合蛋白表达载体和SRT供体载体（含条形码）
2. 体外转染细胞或包装AAV后体内注射（如脑室注射）
3. 等待足够时间让转座事件累积（数天至数周）
4. 收获组织/细胞，提取总RNA
5. 逆转录合成cDNA，用SRT特异性引物扩增插入位点侧翼序列
6. 通过tagmentation和indexing构建测序文库
7. Illumina测序（PE150）
8. 运行nf-core/callingcards流程：过滤、比对、提取插入位点、生成qBED
9. 峰值调用（CCcaller或Blockify）、差异分析、基序富集等下游分析

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| TF-hyPB融合蛋白 | 将转座酶活性导向特定TF结合位点 | 使转座插入事件与TF结合位置相关联 | 输入：TF cDNA + hyPB；输出：功能性融合蛋白 | 文中列出多种已验证TF（SP1, FOXA2, ASCL1, MYOD1, NEUROD2, NGN1等） | 预期：无法靶向特定TF，只能记录BRD4增强子（使用未融合hyPB） |
| SRT（自我报告转座子） | 在插入位点产生可检测的嵌合转录本 | 使插入事件可通过RNA-seq检测，无需DNA测序 | 输入：转座子供体质粒；输出：含tdTomato的插入序列 | "SRT...transcribing RNA from within the transposon" | 预期：无法从RNA恢复插入位点，需改用DNA方法，灵敏度大幅降低 |
| 条形码系统 | 区分独立插入事件 | 解决同一基因座多次插入的计数问题 | 输入：含随机条形码的SRT；输出：带唯一标识的插入 | "introducing transcribed barcodes into the SRT" | 预期：无法区分同一基因座的多次独立插入，定量能力下降 |
| Cre依赖的FrontFlip-hyPB | 实现细胞类型特异性记录 | 在复杂组织中只记录目标细胞类型 | 输入：floxed-hyPB + Cre；输出：仅在Cre+细胞中表达的hyPB | "Cre-dependent hyPB transpose systems" | 预期：记录信号被非目标细胞稀释，无法解析细胞类型特异性 |
| 文库密度qPCR | 评估SRT丰度，决定是否继续 | 避免低质量样本浪费试剂和时间 | 输入：cDNA样本；输出：tdTomato/B-actin比值 | Figure 7 | 预期：低质量样本进入后续步骤，浪费试剂和测序资源 |
| nf-core/callingcards流程 | 从原始测序数据生成qBED | 标准化数据处理，降低分析门槛 | 输入：FASTQ + 参考基因组；输出：qBED + 峰值 | "nextflow Calling Cards bioinformatic pipeline" | 预期：分析结果不可重复，难以比较不同实验 |
| CCcaller/Blockify峰值调用 | 识别插入富集区域 | 从离散插入点推断结合区域 | 输入：qBED；输出：峰值列表 | "CCcaller is the default peak caller" | 预期：无法区分真实结合信号与背景噪声 |

---

## 09 关键公式符号

**不适用**。本文为实验方案论文，未涉及数学公式或统计模型。峰值调用和差异分析使用的统计方法（Poisson检验、Fisher精确检验、二项检验）在CCcaller和pycallingcards中实现，但文中未给出具体公式。

---

## 10 实验设计与证据链

### 数据集/群体/指标
- **验证数据**：文中提及使用小鼠脑组织（发育中的皮层）作为示例，数据已上传至GEO（GSE223926）
- **细胞系**：HEK293、N2A（用于体外验证）
- **关键指标**：
  - 插入位点数量（总插入数）
  - 峰值数量（富集区域）
  - 与ChIP-seq的重叠率
  - 基序富集（TF结合基序在峰值区域的富集程度）
  - 测序饱和度（~90%）
  - 重复性（生物学重复间相关性）

### 实验列表

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|----------------|------|
| BrokenHeart体外功能验证 | TF-hyPB融合蛋白具有转座酶活性 | 共转染TF-hyPB + BrokenHeart报告质粒 vs. 阴性对照 | tdTomato表达阳性 | 融合蛋白功能正常 | 未验证体内特异性 | Basic Protocol 1, Figure S1 |
| 体内AAV递送（脑室注射） | AAV可有效递送Calling Cards试剂至脑组织 | P0-P2小鼠脑室注射，2天至数周后取材 | 检测到插入事件 | 体内递送可行 | 未系统比较不同AAV血清型效率 | Basic Protocol 1, Figure 5 |
| 与ChIP-seq比较 | Calling Cards识别的结合位点与ChIP-seq一致 | Calling Cards vs. 同一TF的ChIP-seq数据 | 显著重叠 | 方法学有效性 | 未在所有TF中验证 | Introduction: "concordant with ChIP-seq data" |
| 测序饱和度分析 | 10-25M reads可达到~90%饱和度 | 不同测序深度下插入恢复率 | 10-25M reads达到~90% | 推荐测序深度合理 | 未对不同组织类型系统优化 | Basic Protocol 4, Figure 10 |
| 重复性分析 | 生物学重复间高度相关 | 同一条件下多个生物学重复 | 高相关性 | 方法可重复 | 未报告具体相关系数 | Supplemental Figure 4 |

---

## 11 结论正确解读

- **任务范围**：本文是实验方案（Protocol），其"结论"是方法学的可行性和操作流程的标准化，而非新的生物学发现。
- **Oracle/真值输入**：方法验证依赖与ChIP-seq数据的比较作为"真值"参考，但ChIP-seq本身也有局限性（抗体质量、分辨率等）。
- **端到端状态**：Calling Cards已从酵母扩展到哺乳动物体外和体内，但尚未在人类组织或疾病样本中广泛验证。
- **算力成本**：数据分析需要Linux HPC环境，但计算量低于单细胞RNA-seq，属于中等规模。
- **历史数据依赖**：方法依赖转座事件的累积，因此需要足够的表达时间（数天至数周），无法记录极早期事件。
- **模型依赖**：不依赖机器学习模型；峰值调用使用统计检验（Poisson）。
- **最难情形**：低表达TF、稀有细胞类型、需要高时间分辨率的研究。
- **群体/领域边界**：目前主要在小鼠脑组织中验证；其他组织、物种、疾病模型需要重新优化递送和表达条件。
- **不确定性**：插入位点与TF结合位点的精确距离关系尚未系统量化；转座酶插入偏好（TTAA位点）可能引入系统性偏差。

**有边界的复述**：Calling Cards能够在遗传靶向的细胞类型中，通过转座酶介导的永久标记，累积记录数天至数周内的蛋白-DNA互作事件，其数据与ChIP-seq具有一致性，但无法解析事件的时间顺序，且需要遗传递送系统。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 无法解析时间顺序 | "the readout of the method provides a cumulative history...is unable to resolve the temporal order of insertions" | 通过时间序列取样+计算减法（如Cammack et al. 2020） | Limitations节 |
| 连续记录而非门控记录 | "current Calling Card reagents record continuously from delivery...until sacrifice" | 开发药物诱导型转座酶 | Limitations节 |
| 插入数较低 | 单细胞中插入数<100 | 优化转座酶活性、增加SRT拷贝数 | Limitations节 |
| 稀有细胞类型挑战 | 极稀有细胞类型可能无法获得足够插入数 | FACS富集tdTomato阳性细胞 | Limitations节 |
| 单细胞版本需要专门方案 | 单细胞Calling Cards需要独立protocol | 参考Moudgil et al. 2020b | Limitations节 |
| 递送效率依赖组织类型 | 不同组织/物种需要优化递送方法 | 开发更多AAV血清型和启动子 | Limitations节 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 插入位点与TF结合位点的距离关系未系统量化 | 转座酶可能在TF离开后仍插入，或插入到远端区域 | 影响峰值调用的分辨率和对结合位点的推断精度 | 使用已知TF结合位点（如ChIP-seq）系统评估插入位点距离分布 | 文中仅称"near TF binding sites" |
| 与ChIP-seq的一致性仅在有限TF中验证 | 不同TF的染色质环境、结合动力学可能影响转座效率 | 方法普适性存疑 | 在更多TF、更多细胞类型中系统比较 | Introduction: "in test cases examined so far" |
| 转座酶插入偏好（TTAA）可能引入系统性偏差 | 某些TF结合位点附近可能缺乏TTAA位点 | 可能导致假阴性 | 分析插入位点序列偏好，与随机模型比较 | 文中承认TTAA偏好 |
| 累积信号可能掩盖动态变化 | 早期和晚期事件在最终读数中不可区分 | 对研究动态调控过程（如发育）构成根本限制 | 时间序列取样+计算减法 | Limitations节 |
| 过表达TF-hyPB可能改变细胞状态 | 融合蛋白过表达可能产生显性负效应或毒性 | 可能影响内源TF功能 | 比较过表达与敲入系统的插入谱 | 文中提及"overexpression is a concern" |
| 未报告假阳性率 | 转座酶可能非特异性插入 | 影响数据可信度 | 使用阴性对照（无TF-hyPB）评估背景插入率 | 未提供 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **时间维度分子记录的设计范式**：Calling Cards展示了"事件→永久标记→可读取"的三步设计。对于TF-DNA互作研究，这种范式可迁移到其他DNA结合蛋白（如组蛋白修饰酶、染色质重塑复合物）的长期记录。

2. **RNA作为互作读出介质的优势**：通过SRT转录产生嵌合RNA，使蛋白-DNA互作数据与转录组数据天然可比对。这一设计对AI模型训练特别有价值——同一批细胞可同时获得"结合历史"和"表达状态"，为构建"结合→表达"的预测模型提供配对数据。

3. **条形码化多重检测策略**：通过SRT条形码区分不同TF或不同样本，这一思路可迁移到多重TF同时检测的实验设计，为AI模型提供更丰富的训练数据维度。

4. **无抗体检测的可行性**：对于缺乏高质量抗体的TF，转座酶融合策略提供了一种替代方案。这对TF-DNA结合机制研究中的"暗物质"TF（未表征TF）尤为重要。

5. **累积信号与时间分辨率的权衡**：累积记录的优势是灵敏度高，代价是时间信息丢失。对于AI/物理模拟，这意味着Calling Cards数据适合训练"稳态结合谱"预测模型，但不适合训练"结合动力学"模型。

6. **计算流程的模块化设计**：nf-core/callingcards采用Nextflow容器化流程，这种模块化、可复现的计算架构值得在AI模型训练pipeline中借鉴。

7. **与ChIP-seq的互补验证策略**：Calling Cards与ChIP-seq的一致性验证思路，可迁移到AI模型预测结果的实验验证设计——用正交方法交叉验证模型预测。

---

## 15 与已有知识连接

- **ChIP-seq / CUT&RUN / CUT&Tag**：Calling Cards与这些方法互补——前者提供累积历史，后者提供快照。文中明确比较了Calling Cards与ChIP-seq的一致性（Introduction），并讨论了CUT&RUN/CUT&Tag的低起始量优势。对于TF-DNA互作研究，联合使用快照方法和记录方法可获得"当前状态+历史轨迹"的完整图景。

- **DamID**：文中提到DamID是另一种累积记录蛋白-DNA互作的方法（Introduction）。DamID利用DNA甲基转移酶融合蛋白，在结合位点附近产生甲基化标记。与Calling Cards相比，DamID不依赖转座，但需要甲基化敏感酶切或甲基化DNA免疫沉淀。两种方法的比较为选择合适记录系统提供了参考。

- **ATAC-seq / H3K27ac / H3K4me1 ChIP-seq**：文中建议将Calling Cards增强子数据与这些染色质状态标记联合分析（Commentary节），以建立增强子-基因调控互作。这与TF-DNA互作研究中的"增强子-启动子互作"课题直接相关。

- **单细胞RNA-seq**：Calling Cards与单细胞平台兼容（Moudgil et al. 2020b），可在同一细胞中同时获得结合历史和转录组。这一连接对AI模型（如基于结合谱预测细胞状态）具有直接价值。

- **CRISPR-Cas9记录系统**：[Analysis] Calling Cards的"写入-读取"架构与CRISPR-Cas9介导的基因组记录系统（如CAMERA、MEMOIR）在概念上相似，但记录的是蛋白-DNA互作而非基因表达事件。这种概念连接可能启发新的混合记录系统。

- **TF-DNA结合预测的AI模型**：[Analysis] Calling Cards产生的长期累积结合数据可作为DeepBind、DeepSEA、BPNet等TF结合预测模型的训练或验证数据，特别是对于缺乏ChIP-seq数据的TF或细胞类型。

---

## 16 研究想法

**Agent 生成的研究候选**

### 候选1：基于Calling Cards数据的TF结合位点预测模型
- **名称**：CC2Seq——利用Calling Cards累积结合数据训练TF-DNA结合预测模型
- **来源局限/观察**：Calling Cards数据与ChIP-seq一致但覆盖更长时间窗口，且不依赖抗体；现有AI模型（如BPNet）主要基于ChIP-seq训练，受限于抗体质量和快照性质
- **核心假设**：Calling Cards累积结合数据比ChIP-seq快照数据包含更完整的TF结合事件，可训练出泛化性更好的结合预测模型
- **初步方法**：使用pycallingcards输出的qBED峰值作为训练标签，DNA序列作为输入特征，采用CNN或Transformer架构（类似BPNet），在多个TF上训练并评估
- **验证方式**：与ChIP-seq训练的模型比较AUROC/AUPRC；在独立细胞类型中交叉验证；基序发现与已知TF基序比对
- **创新状态**：unverified

### 候选2：结合历史与细胞命运的因果推断框架
- **名称**：Hist2Fate——利用Calling Cards记录早期增强子使用并预测最终细胞命运
- **来源局限/观察**：Calling Cards可记录早期发育中的增强子使用，但无法直接追踪同一细胞的命运；现有分析方法缺乏将历史结合事件与最终状态关联的统计框架
- **核心假设**：早期增强子使用的累积模式可预测最终细胞类型/状态，且比单时间点测量更准确
- **初步方法**：利用Calling Cards数据（如发育中皮层不同时间点）构建"增强子使用轨迹"，结合单细胞RNA-seq数据，使用轨迹推断或最优传输方法关联历史与终态
- **验证方式**：在已知发育轨迹（如皮层神经元分化）中验证预测准确性；与单时间点ChIP-seq预测比较
- **创新状态**：unverified

### 候选3：TF-转座酶融合蛋白结合特异性的物理模拟验证
- **名称**：FusionBind——用MD模拟验证TF-hyPB融合蛋白的DNA结合特异性
- **来源局限/观察**：TF-hyPB融合蛋白可能改变TF的DNA结合构象或动力学；现有结构预测工具（如AlphaFold）未针对融合蛋白优化
- **核心假设**：TF-hyPB融合蛋白的DNA结合域构象与天然TF基本一致，但转座酶结构域可能引入空间位阻
- **初步方法**：对已发表的TF-hyPB融合蛋白（如SP1-hyPB）进行MD模拟，比较融合蛋白与天然TF的DNA结合自由能谱和构象变化；使用AlphaFold2预测融合蛋白结构作为起点
- **验证方式**：模拟预测的DNA结合基序与Calling Cards实验数据比对；与已知TF-DNA共晶结构比较
- **创新状态**：unverified

### 候选4：多TF并行Calling Cards的基序协同分析
- **名称**：MultiCC——利用条形码化Calling Cards数据解析多TF协同结合
- **来源局限/观察**：Calling Cards支持条形码化多重检测，但现有分析工具缺乏多TF协同结合的模式识别方法
- **核心假设**：不同TF的累积结合事件在基因组上呈现协同或排斥模式，这些模式可预测增强子功能和基因表达
- **初步方法**：使用条形码化Calling Cards数据（多个TF在同一细胞中），构建TF-TF共插入矩阵，使用非负矩阵分解或主题模型识别协同结合模块
- **验证方式**：与已知TF协同互作数据库（如ENCODE）比较；预测的协同模块与基因表达变化的相关性
- **创新状态**：unverified

### 候选5：Calling Cards数据与染色质状态整合的增强子活性预测
- **名称**：EnhancerCC——整合Calling Cards增强子记录与染色质状态预测增强子活性
- **来源局限/观察**：Calling Cards可记录BRD4结合的增强子，但增强子活性还受染色质状态（H3K27ac、H3K4me1）调控；现有增强子预测模型（如REPTILE）未利用时间累积信息
- **核心假设**：Calling Cards记录的累积增强子使用与染色质状态标记的整合可提高增强子活性预测准确性
- **初步方法**：将Calling Cards插入密度、H3K27ac、H3K4me1、ATAC-seq等特征输入梯度提升机或深度学习模型，预测增强子-基因靶向关系
- **验证方式**：与CRISPR干扰验证的增强子活性比较；在不同细胞类型中交叉验证
- **创新状态**：unverified