## 01 基本信息

- **标题**：CBP60-DB: An AlphaFold-predicted plant kingdom-wide database of the CALMODULIN-BINDING PROTEIN 60 protein family with a novel structural clustering algorithm
- **作者与单位**：Amani, Keaun; Shivnauth, Vanessa; Castroverde, Christian Danve M.（Wilfrid Laurier University，加拿大）
- **期刊/预印本平台**：Plant Direct
- **年份**：2023-07-12
- **论文类型**：数据库/资源型论文（含新算法）
- **领域**：植物生物学、蛋白质结构预测、生物信息学
- **关键词**：AlphaFold2、CBP60蛋白家族、钙调素结合蛋白、结构聚类、植物免疫、数据库
- **DOI/arXiv 号**：10.1002/pld3.509
- **代码**：https://github.com/KeaunAmani/cbp60db/；Google Colab notebook: https://colab.research.google.com/drive/1LOZY33CS5O-PdJAdDApyPlfxUu4DHjcW
- **数据**：https://cbp60db.wlu.ca/（含PDB/mmCIF结构文件、pLDDT/PAE/pTM评分、MSA文件、聚类图、系统发育树等）
- **阅读日期**：未提供
- **在「蛋白质-DNA互作(聚焦TF–DNA结合机制) × AI方法/物理模拟」方向中的位置**：本文聚焦CBP60转录因子家族（含CBP60g和SARD1，均为植物免疫关键TF）的全植物界结构预测与聚类分析。虽未直接研究TF-DNA结合机制，但提供了：(1) 利用AlphaFold2/ColabFold对全植物界TF家族进行结构预测的完整流程；(2) 一种基于结构相似性的新聚类算法（TM-Align + UMAP），可用于TF家族功能亚类划分与直系同源物筛选；(3) 为后续TF-DNA对接、结合位点预测等研究提供结构起点。属于「AI结构预测 × TF家族功能基因组学」交叉方向。

---

## 02 一句话总结

本文利用ColabFold（AlphaFold2衍生）对62个植物物种的1052个CBP60基因同源物（2376个转录本、1996个独特蛋白）进行全结构预测，构建了CBP60-DB数据库，并提出一种基于TM-Align/RSMD结构比对特征+UMAP降维的新颖结构聚类算法，用于全植物界CBP60蛋白家族的结构相似性可视化与功能推断。

---

## 03 研究问题

- **具体问题**：CBP60蛋白家族（尤其是免疫关键转录因子CBP60g和SARD1）在拟南芥以外的植物物种中，其结构多样性、功能保守性和进化关系如何？如何高效地跨物种比较和聚类大量蛋白结构以推断功能？
- **为什么重要**：CBP60g/SARD1是植物水杨酸(SA)合成和免疫应答的主调控转录因子，对作物抗病性改良有直接意义。但大多数物种中该家族的功能和结构信息几乎空白，缺乏系统性的结构资源。
- **现有方法不足**：传统序列比对聚类无法捕捉「同功能但序列分歧大」的蛋白关系；传统结构测定（X射线/NMR）成本高、通量低，无法覆盖全植物界规模；AlphaFold2原始版本速度慢、参数不可调。
- **精确的「Can...?」研究问题**：Can AlphaFold2/ColabFold-based structural prediction combined with a novel TM-Align + UMAP clustering algorithm enable kingdom-wide inference of conserved functions and orthology relationships within the CBP60 protein family across 62 plant species?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及方法，标注为「仅本文框架」或「经外部核验」。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|---------|
| 传统结构生物学 | X射线晶体学、NMR | 高精度、实验验证 | 昂贵、耗时、膜蛋白/复合物难结晶 | 被替代 |
| 同源建模 | SWISS-MODEL等 | 基于已知模板 | 依赖模板、对新型折叠无能为力 | 被替代 |
| 深度学习结构预测 | AlphaFold2 (Jumper et al., 2021) | 高精度、无需模板 | 速度慢、内部参数不可调、MSA生成慢 | 基础工具 |
| 加速版AlphaFold2 | ColabFold (Mirdita et al., 2022) | 速度快、参数可调、MMseqs2加速同源搜索 | 精度略低于原始AF2（作者未量化） | **本文采用** |
| 结构聚类 | 传统RMSD聚类、t-SNE | 简单 | 无法处理大规模、非线性关系 | 被替代 |
| 结构聚类（本文） | TM-Align/RMSD特征张量 + UMAP | 可扩展、直观、可配置 | 二次方时间复杂度 | **本文提出** |

**本文主张的位置**：将AlphaFold2/ColabFold的高通量结构预测与UMAP降维结合，首次实现全植物界规模的蛋白家族结构聚类数据库，填补了CBP60家族跨物种结构资源的空白。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 跨物种功能推断困难 | CBP60家族在大多数植物中功能未知 | 缺乏系统性结构资源；序列相似性不足以推断功能 | 引言：「their function, regulation, and diversification in most species remain unclear」 |
| 传统结构测定通量低 | 无法覆盖62物种、1996个蛋白 | X射线/NMR昂贵、耗时、对某些蛋白无效 | 引言：「Traditional methods... are usually very expensive, time-consuming, and can fail」 |
| 序列聚类无法捕捉结构相似性 | 同功能但序列分歧大的蛋白无法聚类 | 序列比对仅反映一级结构信息 | 方法节：「Traditional sequence-based cluster algorithms... have a major drawback with regard to proteins with similar functionality but different sequences」 |
| AlphaFold2原始版效率低 | 大规模预测耗时 | 默认MSA生成慢、内部设置不可调 | 引言：「base AlphaFold2 also suffers from... the default MSA generation algorithms used can be slow」 |
| 结构聚类算法可扩展性差 | 大规模蛋白结构聚类困难 | 现有方法缺乏可配置性和直观可视化 | 方法节：「our algorithm can cluster small datasets... drawback of the algorithm is its quadratic time complexity」 |

---

## 06 核心思想

### 1) 表面方法
- 从Gramene数据库获取62个植物物种的CBP60基因/蛋白序列
- 使用ColabFold（AlphaFold2 + MMseqs2加速）对所有蛋白进行结构预测
- 构建Web数据库（Go语言编写，无第三方依赖），提供结构文件、评分、可视化
- 提出新聚类算法：两两蛋白间计算TM-Align/RMSD等结构比对指标 → 构建n×n×m特征张量 → 展平为n×(n×m)矩阵 → 输入UMAP降维 → 2D可视化聚类

### 2) 核心洞察
- **结构比序列更保守**：对于CBP60这类功能重要但序列可能分歧的TF家族，结构相似性比序列相似性更能反映功能保守性
- **特征张量+UMAP的组合**：将成对结构比对分数（TM-Align/RMSD）作为特征而非直接对坐标降维，使算法可配置、可解释，且能利用UMAP捕捉非线性结构关系
- **数据库设计理念**：静态数据+哈希索引+API，保证可扩展性和可移植性

### 3) 可能的普适教训 [Analysis]
- **对TF-DNA互作研究的启示**：本文的「结构聚类→功能推断」范式可直接迁移到其他TF家族（如WRKY、NAC、bZIP等），用于识别DNA结合域的结构亚型与潜在功能分化
- **特征工程思路**：将成对结构比对分数作为UMAP输入，比直接对原子坐标降维更鲁棒，且计算成本可控——这一思路可用于TF-DNA复合物构象聚类
- **数据库架构**：轻量级、无依赖的Web应用+API设计，适合作为实验室共享结构资源的模板

---

## 07 方法总览

- **输入**：62个植物物种的CBP60基因同源物蛋白序列（来自Gramene数据库）
- **输出**：CBP60-DB数据库（含1996个预测结构、元数据、评分、聚类可视化、系统发育树）
- **主要模块**：
  1. 序列收集与过滤（Gramene）
  2. 结构预测（ColabFold，含MMseqs2 MSA搜索）
  3. 结构比对与特征提取（TM-Align，可选RSMD）
  4. 聚类与降维（UMAP）
  5. Web应用与API（Go语言）
  6. 系统发育分析（MUSCLE比对 + FastTree）
- **训练**：不适用（无监督聚类，无模型训练）
- **工具**：ColabFold、TM-Align、UMAP、MUSCLE、FastTree、Go、PDBe Molstar、plotly.js
- **反馈回路**：无（静态数据库，但架构支持扩展）
- **文字流程**：Gramena获取序列 → ColabFold预测全部蛋白结构 → 计算两两TM-Align分数 → 构建特征张量 → UMAP降维 → 生成聚类可视化 → 整合所有数据至Web应用 → 用户可通过搜索或点击聚类节点浏览蛋白

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|----------------------|
| 序列收集（Gramene） | 获取62物种CBP60同源物 | 提供全植物界覆盖的序列基础 | 输入：物种列表；输出：基因/转录本/蛋白序列 | 方法节「Using the Gramene comparative genomics website」 | 无法实现全植物界覆盖 |
| ColabFold结构预测 | 从序列预测3D结构 | 核心数据生成；比AF2更快、参数可调 | 输入：蛋白序列；输出：PDB/mmCIF结构+pLDDT/PAE/pTM | 引言「ColabFold... able to generate highly accurate predictions comparable, if not superior to those of AlphaFold2」 | 无结构数据，数据库无法建立 |
| TM-Align特征提取 | 计算两两结构相似性 | 提供结构比较的定量指标 | 输入：结构对；输出：TM-score/RSMD | 方法节「TM-Align scores between all proteins」 | 无法量化结构相似性 |
| 特征张量构建 | 将成对分数组织为n×n×m张量 | 为UMAP提供结构化输入 | 输入：成对分数；输出：特征张量 | 方法节「produce a n×n×m feature tensor」 | 聚类算法无法运行 |
| UMAP降维 | 将高维特征映射至2D | 实现直观的可视化聚类 | 输入：展平特征矩阵；输出：2D坐标 | 方法节「UMAP projection can then be used as an intuitive visualization」 | 无法可视化结构关系 |
| Web应用+API | 提供用户访问界面 | 数据库可访问性 | 输入：用户查询；输出：结构/评分/聚类视图 | 方法节「written in the Go programming language」 | 数据库无法被社区使用 |
| 系统发育分析 | 构建进化树 | 补充结构聚类的进化视角 | 输入：蛋白序列；输出：Newick树文件 | 方法节「MUSCLE alignment... FastTree」 | 缺少进化上下文 |

**消融效应说明**：本文未提供模块消融实验。上述「移除后影响」为基于模块功能的逻辑推断，标注为预期效应。

---

## 09 关键公式符号

本文未提供数学公式。核心算法流程可形式化描述为：

- 设蛋白集合 P = {p₁, p₂, ..., pₙ}，n = 1996
- 对每对 (pᵢ, pⱼ) 计算结构比对指标 sᵢⱼ = TM-Align(pᵢ, pⱼ)（可选附加RMSD）
- 构建特征张量 T ∈ ℝ^(n×n×m)，其中 m = 特征数（如TM-score、RMSD等）
- 展平为矩阵 M ∈ ℝ^(n×(n×m))
- 输入UMAP：Y = UMAP(M)，Y ∈ ℝ^(n×2)
- 输出2D聚类可视化

**符号说明**：
- n：蛋白数量
- m：结构比对特征数量
- T：特征张量
- M：展平后的特征矩阵
- Y：UMAP降维后的2D坐标

来源：方法节「Clustering proteins by structural similarity」描述，公式为 [Analysis] 重构。

---

## 10 实验设计与证据链

### 数据集与规模
- **物种数**：62个植物物种（覆盖植物界主要谱系）
- **基因数**：1052个CBP60基因同源物
- **转录本数**：2376个
- **蛋白数**：1996个独特蛋白
- **数据来源**：Gramene数据库

### 指标
- 结构预测置信度：pLDDT、PAE、pTM（AlphaFold2标准指标）
- 结构相似性：TM-Align分数、RMSD

### 评测协议
- 无定量基准测试；通过数据库可用性、聚类可视化直观性、数据完整性作为间接评估
- 与已有CBP60系统发育分析（Zheng et al., 2021）互补

### 实验表格

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|----------------|------|
| 全植物界CBP60序列收集 | 覆盖62物种的CBP60同源物 | 基于Gramena数据库 | 1052基因/2376转录本/1996蛋白 | CBP60家族在植物界广泛保守 | 未验证序列注释的准确性 | 方法节 |
| ColabFold结构预测 | 可高通量预测CBP60家族结构 | 使用ColabFold而非原始AF2 | 1996个结构全部生成 | ColabFold可处理全家族规模预测 | 未与实验结构对比验证精度 | 方法节 |
| TM-Align + UMAP聚类 | 结构相似性可聚类 | 特征张量→UMAP降维 | 生成直观聚类可视化 | 结构聚类可区分功能亚类 | 未验证聚类与功能注释的一致性 | 方法节、图1 |
| 数据库Web应用 | 可访问性和易用性 | Go语言实现+API | 提供搜索、可视化、下载 | 数据库可被社区使用 | 未进行用户测试 | 方法节、图2-4 |
| 系统发育树构建 | 进化关系推断 | MUSCLE + FastTree | 生成Newick树 | 提供进化上下文 | 未与结构聚类整合分析 | 方法节 |

---

## 11 结论正确解读

- **任务范围**：本文是数据库/资源型论文，核心交付物是CBP60-DB数据库和聚类算法，而非生物学功能发现
- **Oracle/真值输入**：无实验验证结构；所有结构为AlphaFold2/ColabFold预测，未与X射线/NMR实验结构对比
- **端到端状态**：从序列到结构到聚类到Web展示的完整pipeline已实现，但「结构→功能」的推断链条未闭环（未做功能实验验证）
- **算力成本**：未报告具体计算资源消耗
- **历史数据依赖**：依赖Gramena数据库的基因注释质量；依赖AlphaFold2训练数据的覆盖度
- **模型依赖**：结构预测依赖ColabFold（AF2变体）；聚类依赖TM-Align和UMAP参数选择
- **最难情形**：低置信度区域（pLDDT低）的结构在聚类中的可靠性未讨论；跨物种直系同源物与旁系同源物的区分未验证
- **群体/领域边界**：仅覆盖62个有公开基因组的植物物种，不代表所有植物；CBP60家族在非植物生物中的同源物未包含
- **不确定性**：聚类结果的生物学解释（功能推断）是推测性的，需实验验证

**有边界的复述**：本文构建了一个包含62个植物物种、1996个CBP60蛋白预测结构的数据库，并提出了一种基于TM-Align+UMAP的结构聚类算法。该数据库可作为CBP60家族（含TF成员CBP60g/SARD1）跨物种结构比较和候选基因筛选的资源，但所有结构均为计算预测，功能推断需进一步实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| 聚类算法时间复杂度高 | 二次方复杂度，难以扩展到更大数据集 | 未明确提及（但暗示算法适用于中小规模） | 方法节「quadratic time complexity」 |
| 数据库覆盖度有限 | 仅62个物种 | 未明确提及 | 方法节（物种列表） |
| 结构预测依赖计算 | 无实验验证结构 | 未明确提及 | 全文（隐含） |
| 功能推断为推测性 | 聚类结果未与功能实验关联 | 未明确提及 | 结论节「infer putative functions」 |

**作者提及的相关约束**（非正式局限）：
- 数据库为静态内容，更新需手动
- 使用ColabFold而非原始AlphaFold2，精度可能有细微差异（作者认为ColabFold「comparable, if not superior」）
- 聚类算法需要预先计算所有成对TM-Align分数，计算成本随蛋白数平方增长

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 未与实验结构对比验证预测精度 | AF2预测可能存在系统性偏差，尤其对钙调素结合域等柔性区域 | 数据库的可靠性取决于结构预测精度 | 选取若干CBP60成员（如拟南芥CBP60g/SARD1）与已有实验结构或AlphaFold DB对比 | 全文未提及实验验证 |
| 聚类算法未与功能注释关联验证 | 聚类结果可能反映结构相似性而非功能相似性 | 数据库的核心价值主张是「功能推断」 | 将聚类结果与已知功能注释（如GO、突变表型）进行富集分析 | 结论节「infer putative functions」 |
| 未报告pLDDT/PAE的分布统计 | 低置信度区域可能影响聚类结果 | 用户需了解哪些结构区域可靠 | 统计全库pLDDT分布，标注低置信度区域 | 数据存档节提及评分但无统计 |
| 物种选择偏差 | 62个物种可能偏向模式植物和作物，覆盖不均 | 影响「植物界-wide」结论的普适性 | 检查物种列表的系统发育覆盖度 | 方法节物种列表 |
| 与Zheng et al. (2021)系统发育分析的关系未明确 | 结构聚类与序列系统发育可能不一致 | 需明确结构聚类的增量价值 | 比较结构聚类与序列系统发育的一致性 | 引言提及Zheng et al. 2021 |
| 算法「新颖性」需更清晰界定 | TM-Align+UMAP的组合可能已有先例 | 需明确与现有结构聚类方法（如FoldSeek、DeepAlign）的差异 | 与现有方法在基准数据集上对比 | 方法节「novel algorithm」 |

---

## 14 Agent 提炼的知识候选

> 面向「蛋白质-DNA互作（聚焦TF–DNA结合机制）× AI/深度学习/物理模拟」课题的可迁移知识：

1. **全家族结构预测pipeline**：本文展示了从Gramena获取序列→ColabFold批量预测→统一存储的完整流程。可直接迁移到其他TF家族（如WRKY、bZIP、NAC）的全基因组结构预测，为后续TF-DNA对接提供结构输入。
   - 迁移方式：替换序列来源为目标TF家族，调整ColabFold参数（如recycling次数）以优化DNA结合域预测精度。

2. **结构聚类→功能推断范式**：TM-Align成对分数+UMAP降维的聚类方法，可用于TF家族DNA结合域的结构亚型分类。对TF-DNA互作研究，可进一步将聚类结果与已知DNA结合特异性（如PWM、ChIP-seq motif）关联，发现「结构亚型→结合偏好」的映射关系。
   - 迁移方式：对目标TF家族的DNA结合域进行结构聚类，然后与cisBP或JASPAR数据库的motif注释做富集分析。

3. **特征张量构建思路**：将成对结构比对分数组织为张量再降维，比直接对坐标或距离矩阵降维更灵活。可扩展到TF-DNA复合物构象聚类：对MD模拟轨迹中的复合物构象计算成对RMSD/TM-score，构建特征张量后UMAP可视化，识别构象状态。
   - 迁移方式：MD轨迹后处理中，以复合物构象为样本，以RMSD/TM-score为特征，UMAP降维后聚类。

4. **数据库+API设计模式**：Go语言无依赖Web应用+静态数据+哈希索引，适合作为实验室结构资源分享模板。对TF-DNA课题，可构建「TF结构-结合motif-突变数据」一体化数据库。
   - 迁移方式：复用其架构，扩展数据模式以包含DNA结合位点、ChIP-seq peaks、突变表型等。

5. **置信度指标（pLDDT/PAE）的利用**：本文存储了pLDDT/PAE/pTM评分，但未深入分析。对TF-DNA研究，可重点分析DNA结合域（DBD）的pLDDT分布，识别低置信度区域（可能为诱导拟合构象变化区域），为MD模拟或对接提供柔性区域线索。
   - 迁移方式：对目标TF的DBD区域pLDDT做统计分析，低置信度区域作为MD模拟的候选柔性位点。

6. **ColabFold参数可配置性**：本文利用ColabFold的可调参数（如recycling次数）优化预测。对TF-DNA复合物预测，可尝试调整参数以改善蛋白-核酸界面预测精度。
   - 迁移方式：对比不同recycling次数下TF-DNA复合物预测的ipTM/pLDDT，选择最优参数。

---

## 15 与已有知识连接

- **AlphaFold2 (Jumper et al., 2021, Nature)**：本文的基础工具。AF2在单体结构预测上的突破使全家族结构预测成为可能。对TF-DNA课题，AF2的后续版本（AF2-3.0/AlphaFold3）已支持蛋白-核酸复合物预测，本文的pipeline可扩展至复合物层面。
- **ColabFold (Mirdita et al., 2022, Nature Methods)**：AF2的加速实现，本文采用。其MMseqs2加速MSA搜索对大规模预测至关重要。
- **TM-Align (Zhang & Skolnick, 2005, Nucleic Acids Research)**：结构比对工具，本文用于成对相似性计算。TM-score是结构相似性的标准度量，广泛用于TF结构比较。
- **UMAP (McInnes et al., 2018)**：降维算法，本文用于聚类可视化。在生物信息学中已广泛用于单细胞数据、蛋白构象空间分析。
- **Zheng et al. (2021)**：CBP60家族的系统发育分析，本文的序列基础。对TF-DNA课题，系统发育与结构聚类的联合分析可揭示DBD的进化轨迹。
- **CBP60g/SARD1功能研究 (Sun et al., 2015; Wang et al., 2011; Zhang et al., 2010)**：本文的生物学背景。这些研究表明CBP60g/SARD1是SA合成和免疫的关键TF，但其DNA结合机制（识别何种cis-element）仍不完全清楚。本文的结构资源可为后续DNA结合机制研究提供起点。
- **植物免疫与SA信号通路 (Rekhter et al., 2019)**：CBP60g/SARD1调控ICS1/EDS5/PBS3的转录，本文的结构数据可辅助理解TF如何识别这些靶基因启动子。
- **FoldSeek (van Kempen et al., 2023)**：新兴的结构比对工具，与本文的TM-Align+UMAP方法形成对比。对TF-DNA课题，可比较不同结构聚类方法在TF家族上的表现。

---

## 16 Agent 生成的研究候选

### 候选1：TF-DNA结合域结构亚型与DNA结合特异性关联分析
- **名称**：Structure-Based Subtyping of TF DNA-Binding Domains Reveals Binding Preference Determinants
- **来源局限/观察**：本文聚类了CBP60家族结构但未与DNA结合特异性关联；TF-DNA结合特异性（motif）与DBD结构亚型的关系在多数家族中未系统研究
- **核心假设**：同一TF家族内，DBD结构聚类亚型与DNA结合motif（PWM）存在显著关联，结构差异可预测结合偏好变化
- **初步方法**：选取3-5个TF家族（如WRKY、bZIP、NAC），用本文的TM-Align+UMAP pipeline聚类DBD结构，与cisBP/JASPAR motif注释做富集分析，用随机森林预测motif类别
- **验证方式**：交叉验证AUC；对预测的亚型-motif关联选取代表成员做EMSA或HT-SELEX验证
- **创新状态**：partially checked（结构聚类方法已有，但TF家族DBD亚型与motif关联的系统分析未见报道）

### 候选2：TF-DNA复合物构象聚类与结合机制解析
- **名称**：Conformational Landscape of TF-DNA Complexes from MD Simulations with UMAP Clustering
- **来源局限/观察**：本文聚类仅针对单体结构；TF-DNA结合是动态过程，单体结构无法揭示诱导拟合、构象选择等机制
- **核心假设**：TF-DNA复合物的MD模拟轨迹经结构聚类可识别功能相关的构象状态（如特异/非特异结合态），且与实验突变数据一致
- **初步方法**：选取CBP60g/SARD1（或拟南芥其他TF）的DBD-DNA复合物，做μs级MD模拟，对轨迹构象计算成对RMSD/TM-score，用本文的特征张量+UMAP方法聚类，识别亚稳态
- **验证方式**：与已知突变体功能数据对比；MM/PBSA计算各构象态的结合自由能
- **创新状态**：unverified（方法组合新颖，但需验证计算成本与生物学可解释性）

### 候选3：低置信度区域引导的TF-DNA结合位点预测
- **名称**：pLDDT-Guided Prediction of TF-DNA Interface Residues
- **来源局限/观察**：本文存储了pLDDT/PAE但未利用；AF2预测中低pLDDT区域常对应功能相关柔性区（如DNA结合环）
- **核心假设**：TF单体结构中DBD区域的低pLDDT残基富集于DNA结合界面，可作为结合位点预测的特征
- **初步方法**：收集已有TF-DNA复合物结构，计算对应单体AF2预测的pLDDT，检验界面残基是否显著低pLDDT；训练分类器（pLDDT+序列特征）预测DNA结合残基
- **验证方式**：与DBSI、DNABindR等现有方法在基准集上对比AUC/PR
- **创新状态**：partially checked（pLDDT与功能位点的关联已有零星报道，但系统验证并用于TF-DNA界面预测未见）

### 候选4：跨物种TF家族结构-功能进化轨迹分析
- **名称**：Structural Phylogenomics of TF Families: Integrating AlphaFold Structures with Functional Divergence
- **来源局限/观察**：本文提供了CBP60家族62物种的结构聚类，但未与功能分化（如SA通路调控差异）关联
- **核心假设**：TF家族的结构聚类分支与功能分化（如靶基因谱变化）相关，结构变异热点对应功能创新位点
- **初步方法**：对CBP60（或其他TF家族）的结构聚类分支，结合已发表的转录组/ChIP-seq数据，检验结构分支是否对应表达调控差异；鉴定分支特异的氨基酸位点
- **验证方式**：系统发育独立对比（PhyloCorrelate）；对候选位点做定点突变验证
- **创新状态**：unverified（需多组学数据整合，工作量较大）

### 候选5：轻量级TF结构数据库框架复用
- **名称**：TF-StructDB: A Reusable AlphaFold-Anchored Database Framework for Transcription Factor Families
- **来源局限/观察**：本文的Go语言无依赖Web应用+API设计简洁高效，但仅针对CBP60家族
- **核心假设**：该数据库框架可快速适配其他TF家族，成为社区共享的TF结构资源平台
- **初步方法**：将本文的代码框架泛化，定义TF家族元数据schema，部署WRKY、NAC等家族的类似数据库
- **验证方式**：用户测试；与InterPro、Pfam等现有资源对比覆盖率和易用性
- **创新状态**：unverified（工程任务，创新性较低但实用价值高）