## 01 基本信息

- **标题**：Mapping the space of protein binding sites with sequence-based protein language models
- **作者与单位**：Tuğçe Oruç; Maria Kadukova; Thomas G. Davies; Marcel Verdonk; Carl Poelking（Astex Pharmaceuticals）
- **期刊/预印本平台**：bioRxiv
- **年份**：2024
- **论文类型**：预印本（方法学/工具类）
- **领域**：蛋白质-配体结合位点表征、蛋白质语言模型、药物发现
- **关键词**：binding site similarity, protein language models, ESM-2, Voronoi tessellation, pocketome, druggability, train-test debiasing
- **DOI/arXiv 号**：10.1101/2024.07.24.604735
- **代码**：https://github.com/tugceoruc/epocs
- **数据**：https://github.com/tugceoruc/epocs/tree/pre-release/data
- **阅读日期**：未提供
- **在「蛋白质-DNA互作(聚焦TF–DNA结合机制) × AI方法/物理模拟」方向中的位置**：本文聚焦蛋白质-配体（小分子）结合位点，而非蛋白质-DNA界面。但其核心方法——将ESM-2蛋白质语言模型嵌入与3D Voronoi镶嵌结合构建结合位点相似性度量——可直接迁移到TF–DNA结合界面表征。其"多尺度相似性度量+层次聚类+去偏train-test split"框架对TF–DNA结合特异性预测、结合位点分类和基准测试设计具有直接借鉴价值。

## 02 一句话总结

本文提出EPoCS（ESM-driven Pocket Cross-Similarity），通过将ESM-2蛋白质语言模型嵌入映射到3D Voronoi镶嵌定义的配体结合位点残基上并做平均池化，构建结合位点相似性度量，证明其能同时捕捉局部结构与全局序列/功能信息，并可用于生成去偏的train-test splits以改进口袋中心机器学习模型的基准测试。

## 03 研究问题

- **具体问题**：如何构建一个既能捕捉结合位点局部结构相似性、又能反映全局序列/功能关系的可迁移、计算高效的结合位点相似性度量？
- **为什么重要**：结合位点相似性度量是药物发现中靶点识别、配体转移、选择性分析和机器学习模型基准测试的基础工具。现有方法要么计算昂贵（如基于对齐的APoc），要么仅捕捉单一尺度信息（如纯序列相似性）。
- **现有方法为何不足**：APoc等结构对齐方法计算成本高，难以扩展到全蛋白质组规模；纯序列方法丢失局部结构信息；现有方法难以在局部结构与全局功能/进化关系之间取得平衡。
- **精确的"Can ... ?"研究问题**：Can a sequence-based protein language model (ESM-2) combined with 3D tessellation produce a binding site similarity metric that simultaneously captures local structural, global sequence, and functional relationships, and can this metric be used to construct debiased train-test splits for pocket-centric ML models?

## 04 背景与发展脉络

*（注：以下脉络基于本文框架，标注为"仅本文框架"）*

1. **早期结合位点比较方法**：基于序列比对的方法（如BLAST）速度快但忽略结构信息；基于结构叠合的方法（如APoc）精度高但计算昂贵，难以大规模应用。
2. **基于指纹/描述符的方法**：如fpocket，用于口袋检测和druggability评估，但缺乏全局上下文信息。
3. **深度学习时代**：PointSite等基于3D CNN的方法用于druggability预测，但训练数据偏差问题严重。
4. **蛋白质语言模型兴起**：ESM-2等PLM通过自监督学习产生富含进化、结构和功能信息的残基嵌入，计算成本低且可扩展。
5. **本文位置**：首次系统性地将PLM嵌入与3D镶嵌技术结合，构建结合位点相似性度量，并展示其在口袋组学（pocketome）组织、可视化和机器学习基准测试去偏中的应用。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 多尺度信息平衡困难 | 现有度量要么偏重局部结构（APoc），要么偏重全局序列（序列同一性），难以同时捕捉两者 | 结构对齐方法天然聚焦局部几何，序列方法天然丢失结构信息 | Section II, Fig. 2a-c：EPoCS与APoc和序列距离的相关性分析 |
| 计算成本高 | APoc等对齐方法在大规模数据集上不可行 | 对齐算法复杂度高，需要逐对比较 | Section III：96k口袋数据集上无法直接应用APoc，仅用3.5k子集验证 |
| 基准测试数据泄漏 | 随机或简单序列同一性cutoff的train-test split导致模型性能被高估 | PDB数据本身有偏（偏向热门靶点），序列相似性不能代表结构/功能相似性 | Section IV, Fig. 5：PoseBusters与PDBbind训练集存在意外重叠 |
| 现有度量缺乏可扩展性 | 无法支持全蛋白质组规模的结合位点搜索和聚类 | 对齐方法计算瓶颈 | Section III：96k口袋的层次聚类和可视化 |
| 嵌入信息与结构信息脱节 | PLM嵌入虽富含信息，但如何将其与3D结构信息有效整合缺乏系统方案 | PLM嵌入是序列级的，需要映射到3D结构上下文 | Section II：Voronoi镶嵌将ESM嵌入映射到配体结合位点残基 |

## 06 核心思想

### 1) 表面方法
使用ESM-2（esm2_t36_3B_UR50D）为蛋白质序列生成残基级嵌入，通过Voronoi镶嵌确定与配体直接接触的结合位点残基，对这些残基的嵌入做平均池化得到口袋级嵌入向量，以欧氏距离作为口袋间相似性度量。

### 2) 核心洞察
PLM嵌入本身已隐式编码了进化、结构和功能信息，通过3D镶嵌将其"锚定"到结合位点上下文，平均池化操作在保留局部结构敏感性的同时，自然整合了全局序列上下文——这使得EPoCS能同时捕捉局部和全局相似性，而无需显式结构对齐。

### 3) 可能的普适教训 [Analysis]
- **嵌入+几何锚定**：将序列级PLM嵌入通过3D几何（如Voronoi、接触图）锚定到功能位点，是一种通用的"多尺度信息融合"策略，可迁移到TF–DNA界面表征。
- **相似性度量作为基础设施**：一个好的相似性度量不仅是检索工具，更是基准测试设计的基础——通过度量驱动的聚类可以系统性地生成去偏的数据划分。
- **层次聚类+可视化**：将高维嵌入空间投影为可交互的"口袋图谱"（Pocket Atlas），为领域专家提供直观的探索工具。

## 07 方法总览

- **输入**：蛋白质序列 + 配体结合的3D结构（PDB格式）
- **输出**：口袋级嵌入向量（2560维），支持欧氏距离相似性计算
- **模块**：
  1. 序列嵌入生成（ESM-2）
  2. 结合位点残基识别（Voronoi镶嵌 + 8Å径向cutoff）
  3. 口袋嵌入池化（平均池化）
  4. 层次聚类（距离阈值t控制）
  5. 2D投影可视化（Mapper算法）
- **训练**：无监督，ESM-2为预训练模型，无需微调
- **工具**：ESM-2, Voronoi镶嵌, SciPy层次聚类, tmap/Mapper, Faerun可视化
- **反馈回路**：无显式反馈回路；方法为前馈式特征提取
- **假设**：ESM-2嵌入能有效编码结合位点功能/结构信息；平均池化能保留关键信息；欧氏距离在嵌入空间中反映生物学相似性

**文字流程**：
1. 从PDB提取蛋白质链序列和配体坐标
2. 用ESM-2生成全序列残基嵌入
3. 用Voronoi镶嵌识别与配体接触的残基（8Å cutoff）
4. 对结合位点残基嵌入做平均池化 → 口袋嵌入
5. 计算口袋间欧氏距离 → 相似性矩阵
6. 层次聚类（阈值t）→ 口袋簇
7. Mapper算法投影 → 2D Pocket Atlas可视化

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ESM-2序列嵌入 | 生成残基级语义嵌入 | PLM嵌入编码进化、结构、功能信息 | 输入：氨基酸序列；输出：L×2560矩阵 | Section II：与APoc和序列距离的相关性分析 | 预期：失去功能/进化信息，退化为纯结构方法 [预期效应] |
| Voronoi镶嵌 | 识别配体结合位点残基 | 将序列嵌入锚定到3D功能位点 | 输入：蛋白质3D结构+配体坐标；输出：结合位点残基集合 | Methods节：8Å径向cutoff定义 | 预期：无法区分结合位点与非结合位点，嵌入失去空间特异性 [预期效应] |
| 平均池化 | 生成口袋级嵌入 | 将残基级信息压缩为口袋级表示 | 输入：结合位点残基嵌入集合；输出：2560维向量 | Section II：与APoc的局部结构相关性 | 预期：可能降低对关键残基的敏感性，但保留整体特征 [预期效应] |
| 层次聚类 | 组织口袋组学 | 生成多尺度口袋簇 | 输入：口袋距离矩阵；输出：层次树 | Section III：96k口袋聚类 | 预期：无法系统定义口袋家族 [预期效应] |
| Mapper投影 | 2D可视化 | 提供可交互的口袋图谱 | 输入：口袋嵌入+距离；输出：2D图 | Section III, Fig. 3-4 | 预期：失去全局结构可视化能力 [预期效应] |
| 去偏split生成 | 构建train-test划分 | 避免数据泄漏，提供可信基准 | 输入：口袋簇/树；输出：train-test划分 | Section IV, Fig. 6：与30%序列同一性split对比 | 预期：基准测试结果不可信 [预期效应] |

## 09 关键公式符号

**不适用**——本文为方法学/工具类论文，未提出新的数学公式。核心操作为：

- 口袋嵌入：$\mathbf{e}_{pocket} = \frac{1}{N_{site}} \sum_{i \in site} \mathbf{e}_i$（平均池化，文中描述但未以公式形式给出）
- 距离度量：$d(a,b) = \|\mathbf{e}_a - \mathbf{e}_b\|_2$（欧氏距离，文中描述）
- APoc距离转换：$d = 1 - s$（相似度转距离，Section II）

## 10 实验设计与证据链

**数据集/群体**：
- PDB-3.5k：~3500个随机口袋，用于EPoCS与APoc、序列距离的相关性分析
- 96k口袋（68,629个PDB条目）：用于Pocket Atlas构建
- PDBbind 2020 "general" set：用于训练ESM-MLP druggability模型
- PoseBusters：用于验证数据泄漏问题
- HOLO4K：用于与PointSite对比

**指标**：
- 相关性（EPoCS vs APoc vs 序列距离）
- 聚类一致性（OT相似度/Jaccard指数）
- AUC（druggability预测）

**基线**：
- APoc（结构对齐方法）
- 序列同一性距离
- fpocket, PointSite（druggability预测）

**预算/骨干/仪器**：未提供

**评测协议**：
- 对PDB-3.5k计算全对距离矩阵，比较三种度量的相关性
- 对96k口袋进行层次聚类，用OT匹配比较EPoCS与APoc聚类一致性
- 用EPoCS生成不同难度的train-test splits，训练ESM-MLP并比较AUC

| 实验 | 检验的claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|------------------|------|
| 距离相关性分析 | EPoCS同时捕捉局部结构与全局序列信息 | EPoCS vs APoc vs 序列距离，PDB-3.5k全对比较 | EPoCS与APoc和序列距离均显著相关（Fig. 2a-b），而APoc与序列距离相关性差（Fig. 2c） | EPoCS是多尺度度量 | 未量化"最优平衡点" | Section II, Fig. 2 |
| 聚类一致性（OT） | EPoCS聚类与APoc聚类高度一致 | EPoCS阈值t=1.6 vs APoc阈值u=0.2，簇数匹配 | OT相似度72%-86%（Table S1） | EPoCS在局部结构层面复现APoc | 未在更大规模上验证 | Section III, Table S1 |
| Pocket Atlas可视化 | EPoCS组织口袋组学有生物学意义 | 96k口袋，EC注释、配体、QED映射 | 功能相关口袋聚集，ATP等配体呈分散热点 | EPoCS捕捉功能关系 | 未做定量功能富集分析 | Section III, Fig. 3-4 |
| 数据泄漏检测 | 序列同一性split导致泄漏 | PoseBusters vs PDBbind训练集 | 存在意外重叠（Fig. 5） | 现有split方法有缺陷 | 未量化泄漏对性能的影响 | Section IV, Fig. 5 |
| druggability split难度 | EPoCS split产生渐进难度 | 随机split vs 序列同一性30% vs EPoCS cluster/tree splits | 训练AUC恒定~0.92，测试AUC随split难度下降（Fig. 6） | EPoCS可生成可控难度的基准 | 未与其他去偏方法对比 | Section IV, Fig. 6 |
| ESM-MLP性能 | ESM-MLP与现有方法可比 | ESM-MLP vs fpocket vs PointSite | ESM-MLP性能相当（Fig. S2-S3） | 简单MLP+ESM嵌入即可达先进水平 | 未在多个数据集上系统对比 | Supplementary, Fig. S2-S3 |

## 11 结论正确解读

- **任务范围**：本文仅针对蛋白质-小分子配体结合位点，未涉及蛋白质-DNA/RNA界面、蛋白质-蛋白质界面。
- **oracle/真值输入**：使用实验解析的PDB结构中的配体坐标作为结合位点定义依据；druggability标签来自PDBbind。
- **端到端状态**：EPoCS为无监督特征提取方法，不涉及端到端训练；ESM-MLP为独立的下游应用示例。
- **算力成本**：ESM-2 3B模型推理成本较高，但远低于结构对齐方法；作者未提供具体基准。
- **历史数据依赖**：依赖PDB中已有的配体-蛋白共晶结构；对无配体结构需人工生长伪配体。
- **模型依赖**：依赖ESM-2嵌入质量；未测试其他PLM（如ProtBERT、ESM-1b）的替代效果。
- **最难情形**：非标准残基、核酸-蛋白复合物、无序区域、隐口袋（cryptic pocket）等。
- **群体/领域边界**：结论仅在小分子结合位点领域验证；迁移到TF–DNA界面需重新验证。
- **不确定性**：未报告嵌入维度的敏感性分析、池化策略（均值vs最大vs注意力）的消融、不同阈值t的稳定性。

**有边界的复述**：EPoCS在PDB小分子结合位点数据集上，能同时捕捉局部结构相似性（与APoc相关）和全局序列/功能关系（与序列距离相关），并可用于生成比序列同一性cutoff更严格的train-test splits，但该结论仅在本文所述数据集和ESM-2模型配置下得到验证。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 结合位点定义依赖配体 | 需已知配体坐标或人工生长伪配体 | 未明确提及 | Section II, Methods |
| 平均池化可能丢失关键残基信息 | 未对池化策略进行消融 | 未明确提及 | Methods节 |
| 阈值t需经验选择 | 聚类粒度依赖t的选取 | 未明确提及 | Section III |
| 未与其他PLM系统比较 | 仅使用ESM-2 | 未明确提及 | 全文 |
| 数据偏差 | PDB本身偏向热门靶点 | 未明确提及 | Section IV（隐含） |

*注：作者在文中未设独立"Limitations"章节，以上为从Methods和Discussion中提取的隐含局限。*

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 平均池化可能稀释关键残基信号 | 结合位点中少数关键残基（如催化残基）可能被大量非关键残基"淹没" | 对TF–DNA界面，少数关键碱基接触残基可能决定结合特异性 | 对比均值池化 vs 最大池化 vs 注意力池化在结合特异性预测任务上的表现 | Methods节：平均池化描述 |
| 与APoc的相关性可能受数据集偏差影响 | PDB-3.5k可能包含大量同源蛋白，导致所有度量都显示高相关 | 需要去冗余数据集验证 | 在30%序列同一性去冗余后的数据集上重新计算相关性 | Section II, Fig. 2 |
| ESM-2嵌入的"结构信息"来源不明 | ESM-2为序列模型，其结构信息来自进化共变，可能对结合位点这种局部结构不敏感 | 影响方法可解释性和迁移性 | 对比ESM-2嵌入 vs 结构模型（如GVP、SchNet）嵌入在相同任务上的表现 | Section II |
| 去偏split的有效性仅通过AUC间接验证 | 未直接证明EPoCS split消除了特定类型的泄漏 | 基准测试可信度依赖此证明 | 在EPoCS split上测试已知过拟合模型的性能下降幅度 | Section IV, Fig. 6 |
| 未与图神经网络或3D CNN方法直接比较 | 仅与fpocket和PointSite比较，且PointSite比较条件不完全一致 | 无法判断EPoCS嵌入是否优于专用结构编码器 | 在相同数据集和协议下与GNN-based口袋编码器对比 | Supplementary, Fig. S2-S3 |
| 伪配体方法未详细验证 | 对无配体结构使用人工生长伪配体，但未报告该方法的可靠性 | 影响方法在无配体结构上的适用性 | 对比伪配体 vs 真实配体生成的嵌入一致性 | Section II（提及但未详述） |

## 14 学到什么

*（Agent 提炼的知识候选）*

1. **多尺度嵌入融合策略**：将PLM序列嵌入通过3D几何锚定到功能位点，是构建结合位点表征的通用范式。对TF–DNA互作，可将ESM-2嵌入锚定到DNA结合域（DBD）的接触残基，或同时锚定蛋白残基和DNA碱基。

2. **Voronoi镶嵌的界面定义**：用Voronoi镶嵌+径向cutoff定义结合位点残基，比固定半径球或序列窗口更几何合理。可迁移到TF–DNA界面：用Voronoi镶嵌定义蛋白-核酸接触残基/碱基对。

3. **层次聚类+OT比较框架**：用最优传输（OT）比较不同度量诱导的聚类结构，是一种度量评估的通用方法。可用于评估TF–DNA结合位点聚类的生物学意义。

4. **去偏split设计**：基于相似性度量的层次聚类生成渐进难度split，是基准测试设计的先进实践。对TF–DNA结合特异性预测模型，可用EPoCS式度量生成去偏的train-test splits，避免同源蛋白泄漏。

5. **Pocket Atlas可视化**：用Mapper算法将高维嵌入投影为可交互图谱，结合EC注释、配体、QED等多层信息，是探索性数据分析的强有力工具。可构建"TF–DNA结合界面图谱"，映射不同TF家族的结合模式。

6. **简单MLP+PLM嵌入的强基线**：ESM-2嵌入+单隐层MLP即可达到与专用方法相当的性能，说明PLM嵌入的信息密度极高。对TF–DNA结合预测，可先建立类似强基线再考虑复杂模型。

7. **数据泄漏的系统性检测**：通过可视化PoseBusters与训练集的重叠，作者展示了如何识别意外泄漏。对TF–DNA数据集（如CIS-BP、JASPAR），应系统检查训练/测试集间的结构相似性。

## 15 与已有知识连接

- **ESM-2**：由Meta AI开发（Lin et al., 2023），是当前最先进的蛋白质语言模型之一，其嵌入已被广泛用于结构预测（ESMFold）、突变效应预测等任务。本文将其扩展到结合位点表征。
- **APoc**：由Zhang课题组开发（Zhang & Grigorov, 2006），是基于局部结构对齐的口袋相似性方法，本文将其作为结构基线的代表。
- **PoseBusters**：由Buttenschoen等提出（2024），系统评估了分子对接基准测试中的数据泄漏问题，本文直接引用其发现来motivate去偏split的必要性。
- **IF-SitePred**：由Carbery等开发（2023），使用ESM嵌入预测蛋白质-配体结合位点，本文的ESM-MLP模型与其高度相关。
- **Binding MOAD**：数据库（Benson et al., 2008），提供基于APoc的口袋家族分类，本文用于交叉验证EPoCS聚类。
- **Mapper算法**：拓扑数据分析方法（Singh et al., 2007），用于高维数据可视化，本文用于构建Pocket Atlas。
- **与TF–DNA互作课题的关联**：本文方法可直接迁移到TF–DNA结合界面表征。类似工作如DeepTF（DNA结合特异性预测）、TFimpute等使用序列或结构特征，但缺乏多尺度统一度量。EPoCS框架为TF–DNA界面提供了新的表征思路。

## 16 研究想法

*（Agent 生成的研究候选）*

### 候选1：TF–DNA界面多尺度相似性度量（EPoCS-TF）
- **名称**：EPoCS-TF: ESM-driven Transcription Factor-DNA Interface Cross-Similarity
- **来源局限/观察**：EPoCS仅针对蛋白-小分子界面；TF–DNA界面涉及蛋白残基和DNA碱基的双侧特征，且结合特异性由少数关键接触决定
- **核心假设**：将ESM-2蛋白嵌入与DNA碱基嵌入（如DNABERT）通过Voronoi镶嵌联合锚定到TF–DNA接触界面，平均池化后可构建同时捕捉蛋白侧和DNA侧信息的界面相似性度量
- **增量**：扩展EPoCS到双分子界面；引入DNA侧嵌入；可能需设计界面特异性池化策略（如接触加权）
- **初步方法**：从PDB收集TF–DNA复合物，用Voronoi镶嵌定义接触残基/碱基，分别用ESM-2和DNABERT生成嵌入，拼接或加权融合后池化
- **验证方式**：与现有TF–DNA界面相似性方法（如基于结构的叠合、基于序列的PWM比较）对比聚类一致性；测试其在TF家族分类、结合特异性预测中的下游性能
- **创新状态**：unverified

### 候选2：TF–DNA结合位点去偏基准测试框架
- **名称**：TF-Bench: Debiased Benchmarking for TF-DNA Binding Prediction Models
- **来源局限/观察**：本文证明EPoCS可生成去偏split用于口袋中心模型；TF–DNA结合预测模型同样面临数据泄漏问题（同源TF、相似DNA基序）
- **核心假设**：基于EPoCS-TF度量的层次聚类可生成比序列同一性cutoff更严格的TF–DNA基准测试split
- **增量**：将去偏split方法论从口袋中心迁移到TF–DNA中心；可能需考虑DNA侧基序相似性
- **初步方法**：构建TF–DNA结合数据集，用EPoCS-TF计算界面相似性，层次聚类后生成渐进难度split；在多个TF–DNA预测模型上比较不同split下的性能差异
- **验证方式**：检测现有模型在EPoCS-TF split下的性能下降幅度；与序列同一性split对比
- **创新状态**：unverified

### 候选3：TF–DNA界面嵌入的消融研究
- **名称**：What Matters in TF-DNA Interface Embeddings? A Systematic Ablation
- **来源局限/观察**：EPoCS未报告池化策略、嵌入维度、cutoff半径的消融；这些超参数对TF–DNA界面可能更敏感
- **核心假设**：对TF–DNA界面，接触加权池化优于平均池化；DNA侧嵌入的加入显著提升特异性捕捉能力
- **增量**：系统评估不同设计选择对TF–DNA界面表征质量的影响
- **初步方法**：在固定数据集上，变化池化策略（均值/最大/注意力/接触加权）、嵌入模型（ESM-2不同层、DNABERT）、cutoff半径，评估下游任务性能
- **验证方式**：下游任务（TF家族分类、结合/不结合预测）的AUC对比；嵌入空间的生物学意义（如已知TF基序的聚类）
- **创新状态**：unverified

### 候选4：结合分子动力学模拟的TF–DNA界面动态嵌入
- **名称**：DynEPoCS: Dynamics-Aware TF-DNA Interface Embeddings via MD-Enhanced Language Models
- **来源局限/观察**：EPoCS使用静态晶体结构；TF–DNA结合是动态过程，诱导拟合和构象变化可能影响结合特异性
- **核心假设**：将MD模拟采样的构象集合纳入嵌入池化，可捕捉静态结构丢失的动态信息，提升界面表征的鲁棒性
- **增量**：将MD采样与PLM嵌入结合，生成"动态感知"的界面表征
- **初步方法**：对代表性TF–DNA复合物运行短MD模拟，对采样构象分别生成EPoCS-TF嵌入，池化或学习聚合为动态嵌入
- **验证方式**：与静态EPoCS-TF对比在结合特异性预测、突变效应预测上的性能
- **创新状态**：unverified

### 候选5：TF–DNA界面图谱（Interface Atlas）
- **名称**：TF-DNA Interface Atlas: Mapping the Space of Transcription Factor Binding Modes
- **来源局限/观察**：EPoCS的Pocket Atlas展示了口袋组的全局组织；TF–DNA结合模式（如不同DBD家族、结合基序类型）的全局图谱尚缺
- **核心假设**：EPoCS-TF嵌入空间的层次聚类可揭示TF–DNA结合模式的组织原则，与已知DBD分类和DNA基序家族一致
- **增量**：构建TF–DNA界面的全局可视化图谱，整合DBD家族、基序、物种、功能等多层注释
- **初步方法**：收集大规模TF–DNA复合物结构，生成EPoCS-TF嵌入，层次聚类+Mapper投影，叠加注释
- **验证方式**：聚类与已知DBD分类的一致性（如Pfam、CATH）；图谱中相邻簇的生物学关联
- **创新状态**：unverified