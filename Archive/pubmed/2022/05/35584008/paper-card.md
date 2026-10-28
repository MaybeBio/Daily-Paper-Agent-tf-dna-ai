## 01 基本信息

- **标题**：RegulonDB 11.0: Comprehensive high-throughput datasets on transcriptional regulation in Escherichia coli K-12
- **作者与单位**：Tierrafria, Victor H; Rioualen, Claire; Salgado, Heladia; Lara, Paloma; Gama-Castro, Socorro; Lally, Patrick; Gomez-Romero, Laura; Pena-Loredo, Pablo; Lopez-Almazo, Andres G; Alarcon-Carranza, Gabriel; Betancourt-Figueroa, Felipe; Polanco-Morelos, J Enrique; Garcia-Sotelo, Jair; Gaytan-Nunez, Estefani; Mendez-Cruz, Carlos-Francisco; Muniz, Luis J; Bonavides-Martinez, Cesar; Moreno-Hagelsieb, Gabriel; Galagan, James E; Wade, Joseph T; Collado-Vides, Julio（单位未在摘要中提供，主要来自 UNAM，墨西哥国立自治大学）
- **期刊/预印本平台**：Microbial genomics
- **年份**：2022
- **论文类型**：数据库/资源描述论文
- **领域**：微生物基因组学、转录调控、生物信息学数据库
- **关键词**：RegulonDB、E. coli K-12、转录调控、ChIP-seq、gSELEX、DAP-seq、RNA-seq、TSS、TTS、转录单元
- **DOI/arXiv 号**：10.1099/mgen.0.000833
- **代码**：https://github.com/regulondbunam/；https://github.com/PGC-CCG/RegulonDB-HT；https://github.com/PGC-CCG/SnakeChunks；https://github.com/PGC-CCG/EcoliGenes
- **数据**：https://regulondb.ccg.unam.mx/；Docker 容器：https://doi.org/10.5281/zenodo.6376425
- **阅读日期**：未提供
- **在课题方向中的位置**：本文是转录调控领域的基础数据资源论文，为 TF–DNA 互作研究提供大规模、多技术（ChIP-seq、ChIP-exo、gSELEX、DAP-seq）的 TF 结合位点数据，以及 TSS、TTS、TU 和 RNA-seq 表达数据。对于 AI/深度学习或物理模拟方法研究 TF–DNA 结合机制，本文提供的是训练数据、验证基准和生物学先验知识来源，而非方法本身。

## 02 一句话总结

本文描述 RegulonDB 11.0 数据库的升级，将 E. coli K-12 转录调控相关的高通量数据（TF 结合位点、TSS、TTS、TU、RNA-seq 表达谱）从 99 个数据集扩展到 2000+ 个，通过统一处理、标准化和元数据注释（含 NLP 辅助的生长条件提取），为研究者提供可比较、可追溯的转录调控数据资源。

## 03 研究问题

- **具体问题**：如何将分散在公共数据库（GEO、SRA、ArrayExpress 等）中的 E. coli K-12 转录调控高通量数据整合到一个统一、可搜索、可比较的资源中？
- **为什么重要**：高通量技术（ChIP-seq、RNA-seq 等）产生了海量转录调控数据，但这些数据分散在不同来源、使用不同基因组版本、不同处理流程，研究者难以直接比较和复用。对于 TF–DNA 互作研究，缺乏统一的数据资源会阻碍系统性分析和模型构建。
- **现有方法为何不足**：已有数据库（如 COLOMBOS、TEC、proChIPdb）各自覆盖单一数据类型或单一技术，没有提供跨技术的整合视图；且缺乏统一的标准化处理和详细的生长条件元数据，限制了数据的可比性和可复用性。
- **精确的 Can 问题**：Can a single integrated resource provide standardized, comparable, and searchable high-throughput datasets on transcriptional regulation in E. coli K-12, covering TF binding, transcription initiation, termination, and gene expression?

## 04 背景与发展脉络

> 注：此脉络基于本文框架，未经外部核验。

1. **早期阶段（~2000s）**：RegulonDB 以手工文献 curation 为主，收集经典低通量（LT）实验数据，如单个 TF 结合位点、启动子、转录单元等。代表方法：手工 curation + 文献检索。优点：高精度、生物学验证充分；局限：覆盖度有限、更新慢。
2. **高通量数据初步整合（~2009-2012）**：RegulonDB 8.0 开始收集 TSS 数据，9.0 加入 ChIP-seq 和 gSELEX 数据。优点：开始覆盖基因组规模数据；局限：数据集数量有限（99 个），处理流程不统一。
3. **专门数据库出现（~2016-2021）**：TEC（gSELEX 数据）、proChIPdb（ChIP-seq/ChIP-exo 数据）、COLOMBOS（表达数据）等专门数据库出现。优点：各自领域内数据丰富；局限：数据类型单一、格式不统一、缺乏跨技术整合。
4. **RegulonDB 11.0（本文，2022）**：大规模整合 2000+ 数据集，覆盖 TF 结合（ChIP-seq、ChIP-exo、gSELEX、DAP-seq）、TSS、TTS、TU、RNA-seq 表达谱。引入统一处理流程（SnakeChunks）、标准化（基因组版本更新、DEseq 归一化）、NLP 辅助元数据提取、MCO 本体映射。优点：一站式资源、可比性强、可追溯；局限：数据质量参差、部分数据集缺乏完整元数据。

**本文主张的位置**：RegulonDB 11.0 是当前最全面的 E. coli K-12 转录调控高通量数据整合资源，填补了跨技术、跨数据类型整合的空白。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 数据分散 | 转录调控数据分布在 GEO、SRA、ArrayExpress、TEC、proChIPdb 等多个来源 | 不同研究组使用不同数据库存储数据，缺乏统一整合 | Introduction 节："no resource currently exists that offers all available high and low-throughput data" |
| 格式不统一 | 不同来源的数据使用不同基因组版本、不同文件格式 | 各研究组独立处理数据，缺乏统一标准 | Methods 节 "Normalization and uniformization"；Results 节 "Data as reported by authors frequently vary in reference genome used and/or format" |
| 元数据缺失 | 生长条件等关键实验条件信息不完整 | 文献中缺乏详细实验条件描述，作者未提供完整元数据 | Discussion 节："found none that described the growth rate, and less than 100 provided the pH" |
| 可比性差 | 不同数据集的处理流程不同，难以直接比较 | 缺乏统一的数据处理流程和归一化方法 | Methods 节 "DEseq-normalization"；Results 节 "enhancing their comparability" |
| 数据可发现性低 | 研究者难以找到特定条件下的转录调控数据 | 缺乏基于元数据的搜索功能 | Results 节 "Browsing the data" 描述的搜索界面 |
| 经典数据与高通量数据脱节 | LT 经典数据与 HT 数据缺乏系统比较 | 未建立 HT 数据到 LT 数据的映射 | Methods 节 "Mapping and integration"；Results 节 "pre-processed column" |

## 06 核心思想

### 1) 表面方法

构建一个大型数据库（RegulonDB 11.0），系统收集、标准化、注释和展示 E. coli K-12 转录调控的高通量数据，包括 TF 结合位点（ChIP-seq、ChIP-exo、gSELEX、DAP-seq）、TSS、TTS、TU 和 RNA-seq 表达谱。提供 Web 界面、搜索工具和基因组浏览器供用户访问。

### 2) 核心洞察

- **数据整合的关键不是收集，而是标准化和可追溯性**：作者强调不仅提供原始数据，还提供统一处理的版本（uniformized files），并保留作者原始版本，让用户自行选择。
- **元数据是数据可复用的前提**：作者投入大量精力（NLP + 人工审核）提取生长条件等元数据，并映射到 MCO 本体，使数据可被语义化搜索和比较。
- **HT 数据需要与 LT 经典数据建立映射**：通过将 HT 数据映射到 RegulonDB 中经过经典实验验证的 TFRS，用户可以直接评估 HT 数据的可靠性。

### 3) 可能的普适教训 [Analysis]

- 对于 TF–DNA 互作研究，数据质量评估应优先于数据量：本文提供的 HT 数据与 LT 经典数据的映射机制，为 AI 模型训练时的数据标注可靠性提供了参考框架。
- 统一处理流程（如 SnakeChunks）的设计思路可迁移到其他组学数据整合场景，确保不同来源数据的可比性。
- NLP 辅助 curation 的策略表明，在生物数据整合中，自动化工具 + 人工审核的混合模式是处理大规模元数据提取的有效路径。

## 07 方法总览

- **输入**：来自公共数据库（GEO、SRA、ArrayExpress）和文献的原始高通量数据，包括 ChIP-seq、ChIP-exo、gSELEX、DAP-seq 的原始/处理后数据，RNA-seq 原始数据，以及文献中报道的 TSS、TTS、TU 数据。
- **输出**：标准化的数据集集合（RegulonDB-HT），包含统一格式的数据文件、元数据表、生长条件注释、MOC 映射、基因组浏览器可视化。
- **模块**：
  1. 数据收集（Data gathering）：从 GEO、SRA、ArrayExpress、TEC、proChIPdb 等来源收集数据
  2. 人工 curation 和注释（Curation and annotation）：从文献中提取数据特征、元数据
  3. 标准化/统一处理（Normalization and uniformization）：ChIP-seq 用 SnakeChunks 统一处理；RNA-seq 用 DEseq 归一化；坐标更新到最新基因组版本
  4. 映射和整合（Mapping and integration）：HT 数据映射到 LT 经典数据
  5. NLP 辅助元数据提取：CRF 模型自动提取生长条件
  6. Web 界面和搜索工具
- **训练**：NLP 模型（CRF）使用 228 个手工标注的 GEO SOFT 文件训练（70% 训练 + 交叉验证，30% 测试）
- **工具**：SnakeChunks（基于 snakemake 的 ChIP-seq 分析流程）、cutadapt、Bowtie 2、Macs 3、RSAT matrix-scan、RSAT peak-motifs、RSAT convert-matrix、GEOquery、fuzzywuzzy、Beautiful Soup
- **反馈回路**：NLP 提取的生长条件经人工审核后回填到数据库，提高后续提取准确性
- **假设**：不同来源的数据在统一处理后具有可比性；LT 经典数据可作为 HT 数据的验证基准

**文字流程**：从公共数据库和文献收集原始数据 → 人工 curation 提取元数据和特征 → 对 ChIP-seq 原始数据用 SnakeChunks 统一处理（比对、peak calling、motif 识别）→ RNA-seq 数据用 DEseq 归一化 → 所有坐标更新到 NC_000913.3 基因组版本 → HT 数据映射到 LT 经典数据 → NLP 提取生长条件并映射到 MCO → 存入 MongoDB → 通过 Web 界面和搜索工具展示。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 数据收集（Data gathering） | 从 GEO、SRA、ArrayExpress、TEC、proCHIPdb 等来源系统收集转录调控 HT 数据 | 数据分散在多个来源，需要统一收集 | 输入：公共数据库中的原始数据；输出：数据集清单和原始文件 | Methods 节 "Data gathering" | 预期影响：数据覆盖度大幅降低，无法提供全面资源 [预期效应] |
| 人工 curation 和注释 | 从文献中提取数据特征、元数据、实验条件 | 文献中的信息需要人工判断和提取 | 输入：原始文献；输出：结构化元数据表 | Methods 节 "Curation and annotation" | 预期影响：元数据质量下降，数据可搜索性降低 [预期效应] |
| ChIP-seq 统一处理（SnakeChunks） | 用统一流程处理 ChIP-seq 原始数据，确保可比性 | 不同来源的 ChIP-seq 数据处理流程不同，影响比较 | 输入：ChIP-seq 原始 fastq 文件；输出：peak 坐标、TFBS 序列、motif | Methods 节 "Uniformization"；Results 节 "26 datasets associated with ten TFs are provided with two tables" | 实测影响：未提供消融实验；预期影响：数据可比性显著下降 [预期效应] |
| RNA-seq 归一化（DEseq） | 对 RNA-seq 表达数据进行 DEseq 归一化 | 不同实验的测序深度、文库大小不同，需要归一化才能比较 | 输入：RNA-seq 原始计数；输出：归一化表达值（counts, RPKM/FPKM, TPM） | Methods 节 "Normalization" | 预期影响：跨数据集比较不可靠 [预期效应] |
| 坐标更新 | 将数据坐标从旧基因组版本更新到 NC_000913.3 | 不同来源使用不同基因组版本，需要统一 | 输入：旧版本坐标；输出：NC_000913.3 坐标 | Methods 节 "Uniformization" | 预期影响：数据无法在统一基因组浏览器中展示 [预期效应] |
| NLP 生长条件提取（CRF） | 自动从 SOFT 文件中提取生长条件元数据 | 手工 curation 大规模元数据成本高 | 输入：SOFT 文件文本；输出：标注的生长条件术语 | Methods 节 "NLP method"；Results 节 "F1-score 0.81-0.83" | 预期影响：生长条件覆盖率大幅降低 [预期效应] |
| MOC 映射 | 将生长条件术语映射到 MOC 本体 | 统一术语便于语义化搜索 | 输入：提取的生长条件术语；输出：MOC ID | Methods 节 "Mapping to MCO"；Results 节 "~83% of terms mapped" | 预期影响：跨数据集条件比较困难 [预期效应] |
| Web 界面和搜索工具 | 提供数据浏览、搜索和可视化 | 数据需要可访问和可搜索 | 输入：用户查询；输出：数据集列表、基因组浏览器视图 | Results 节 "Browsing the data" | 预期影响：数据可访问性降低 [预期效应] |

## 09 关键公式符号

本文为数据库资源论文，不涉及核心数学模型或公式。以下为方法中涉及的少量量化指标：

- **F1-score**：F1 = 2 × (precision × recall) / (precision + recall)，用于评估 NLP 模型（CRF）提取生长条件的性能。precision = TP / (TP + FP)，recall = TP / (TP + FN)。文中报告 F1 = 0.81（五折交叉验证）和 0.83（测试集）。
- **DEseq 归一化**：未给出具体公式，标准 DEseq 方法基于几何均值计算缩放因子。文中描述为 "created a 'pseudo-reference' sample, where we obtained the geometric mean of each gene's expression"。
- **CRF 条件概率**：P(y|x)，给定观测序列 x 下标签序列 y 的条件概率，用于序列标注任务。

## 10 实验设计与证据链

**数据集/群体**：
- 228 个 GEO SOFT 文件（来自 27 个 GEO series），用于 NLP 模型训练和测试
- 2000+ 个高通量数据集，涵盖 TF 结合（ChIP-seq、ChIP-exo、gSELEX、DAP-seq）、TSS、TTS、TU、RNA-seq 表达谱
- 具体数据量：29 个 ChIP-seq 数据集（12 个 TF）、94 个 ChIP-exo 数据集（73 个 TF）、164 个 gSELEX 数据集（121 个 TF）、215 个 DAP-seq 数据集（211 个 TF）、16 个 TSS 数据集（68049 个 TSS）、5 个 TU 数据集（12347 个 TU）、5 个 TTS 数据集（5326 个 TTS）、1864 个 RNA-seq 样本

**指标**：
- NLP 模型：F1-score（0.81 交叉验证，0.83 测试）
- 数据映射率：~83% 的生长条件术语映射到 MCO ID（15% 精确匹配，~68% 字符串相似度）
- RNA-seq 数据质量：648/1864 样本标记为 "PASS"（>500 万 reads，>90% 比对率，>90% 基因非零覆盖）

**评测协议**：
- NLP 模型：五折交叉验证 + 独立测试集（30%）
- 数据质量评估：基于比对率、reads 数、基因覆盖度等指标

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|-----------------|------|
| NLP 模型训练与测试 | CRF 能有效提取生长条件 | 228 个 SOFT 文件，70% 训练/30% 测试，五折交叉验证 | F1 = 0.81（CV），0.83（测试） | CRF 可自动提取生长条件 | 未与其他 NLP 方法（如 BERT、LSTM）对比；未报告 precision/recall 单独值 | Methods 节 "NLP method"；Results 节 "F1-score" |
| 生长条件 MCO 映射 | 提取的术语可映射到 MCO 本体 | 精确匹配 vs 字符串相似度（fuzzywuzzy） | ~83% 映射成功（15% 精确 + 68% 相似度） | 大部分生长条件可标准化 | 17% 未映射术语的处理方式未说明 | Results 节 "Mapping to MCO" |
| ChIP-seq 统一处理 | 统一流程可识别 TFBS | 28 个数据集，11 个 TF，SnakeChunks 流程 | 26 个数据集同时提供作者版和统一版 | 统一处理可行 | 未与作者原始结果做系统性比较 | Results 节 "TF binding datasets" |
| RNA-seq 质量评估 | 可筛选高质量样本 | 1864 个样本，基于比对率等指标 | 648 个样本标记为 PASS | 可提供质量分层 | PASS/非 PASS 的生物学意义未验证 | Results 节 "Gene expression datasets" |
| HT 与 LT 数据比较 | HT 数据可恢复经典知识 | 各 HT 数据集与 RegulonDB LT 数据比较 | 恢复率因数据集而异（图 5b） | HT 数据与 LT 数据存在重叠 | 恢复率低的数据集的原因未深入分析 | Results 节 "Fig. 5b" |

## 11 关键结论

- RegulonDB 11.0 提供了 2000+ 个 E. coli K-12 转录调控高通量数据集，涵盖 TF 结合（ChIP-seq、ChIP-exo、gSELEX、DAP-seq）、TSS、TTS、TU 和 RNA-seq 表达谱，是目前最全面的整合资源。
- 通过统一处理流程（SnakeChunks for ChIP-seq、DEseq for RNA-seq），提高了不同来源数据的可比性。
- NLP 辅助 curation 策略（CRF 模型）成功从 SOFT 文件中自动提取生长条件，F1-score 达 0.83，显著降低了人工 curation 成本。
- 提供了 HT 数据与 LT 经典数据的映射，使用户可以评估 HT 数据的可靠性。
- 所有数据、代码和文档均公开可用，支持可重复性。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未更新 ChIP-chip 和 microarray 数据 | 这些旧技术数据未包含在本次升级中 | 未明确说明 | Discussion 节："We did not however update our ChIP-chip nor microarray datasets" |
| 未包含 Hi-C 数据 | 3D 基因组结构数据不在本次范围内 | 未明确说明 | Discussion 节："we did not include any Hi-C data" |
| 生长条件元数据不完整 | 大量样本缺乏 pH、生长速率等关键条件信息 | 正在改进 NLP 预测模型 | Discussion 节："found none that described the growth rate, and less than 100 provided the pH" |
| NLP 提取的术语需要人工审核 | 自动提取的生长条件需人工验证后才能入库 | 改进模型以减少人工审核需求 | Methods 节 "assisted curation strategy" |
| 部分数据集缺乏原始数据 | 某些数据集无法获取原始 fastq 文件 | 未明确说明 | Results 节："one dataset does not come with raw data" |

## 12.5 作者提及的相关约束（非正式局限）

- 数据质量参差不齐：不同来源的数据质量差异大，作者通过 "PASS" 标记提供质量分层，但未对低质量数据的处理策略做详细说明。
- 数据可比性仍有局限：虽然提供了统一处理版本，但作者承认 "The diversity of information and formats provided by authors makes it difficult to compare in a comprehensive way the results of our in-house processing with those provided originally"（Discussion 节）。
- 未来计划中未包含跨 HT 数据集的系统比较，仅提到 "In a future version we will add comparisons between them"。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| NLP 模型仅使用 CRF，未与深度学习方法对比 | 现代 NLP 方法（如 transformer-based 模型）可能在生长条件提取上表现更好 | 影响元数据提取效率的上限评估 | 在相同数据集上对比 CRF vs BERT/BioBERT 等模型 | Methods 节 "NLP method" |
| HT 与 LT 数据映射的"恢复率"指标定义不明确 | 恢复率的计算方式（如是否考虑 peak 宽度、阈值）未详细说明 | 影响用户对 HT 数据质量的判断 | 查阅补充材料或联系作者获取详细计算方式 | Results 节 "Fig. 5b" |
| ChIP-seq 统一处理仅覆盖 11 个 TF | 样本量小，可能无法代表所有 TF 的结合特性 | 影响统一处理流程的泛化性评估 | 扩展到更多 TF 验证流程稳定性 | Results 节 "TF binding datasets" |
| RNA-seq "PASS" 标准可能过于宽松或严格 | >90% 比对率、>90% 基因覆盖度的阈值依据未说明 | 影响数据筛选的合理性 | 对比不同阈值下的下游分析结果 | Results 节 "Gene expression datasets" |
| 未提供 HT 数据之间的交叉比较 | 不同技术（ChIP-seq vs gSELEX vs DAP-seq）对同一 TF 的结合位点一致性未评估 | 影响用户对跨技术数据整合的信心 | 对同一 TF 的多技术数据做 Venn 图或相关性分析 | Discussion 节 "In a future version we will add comparisons between them" |
| 数据库更新频率未明确 | 未说明后续数据更新的时间表和机制 | 影响数据库的长期可用性 | 关注 RegulonDB 后续版本发布 | 未提供 |

## 14 学到什么

> Agent 提炼的知识候选

1. **数据标准化流程设计**：本文展示了如何为多来源、多技术的高通量数据设计统一的处理流程（SnakeChunks for ChIP-seq、DEseq for RNA-seq）。对于 TF–DNA 互作研究，可借鉴此思路构建统一的 ChIP-seq 处理 pipeline，减少批次效应，提高 AI 模型训练数据的质量。

2. **HT-LT 数据映射策略**：将高通量数据映射到经典低通量验证数据（LT）的方法，为 AI 模型训练时的标签可靠性评估提供了参考。在 TF–DNA 结合位点预测中，可用此策略筛选高置信度训练样本。

3. **NLP 辅助 curation 模式**：CRF + 人工审核的混合 curation 策略，可迁移到其他生物数据整合场景。对于 TF–DNA 互作文献的自动信息提取（如结合位点、调控关系、实验条件），此模式可大幅提高效率。

4. **MOC 本体映射**：将实验条件映射到标准本体的做法，为 AI 模型训练时的条件特征编码提供了标准化方案。在构建 TF–DNA 结合预测模型时，标准化的实验条件描述有助于模型泛化。

5. **数据质量分层标记**：通过 "PASS" 标记对数据质量进行分层，而非简单丢弃低质量数据。在 AI 训练中，可借鉴此策略进行样本加权或分层采样。

6. **TFBS vs TFRS 概念区分**：本文明确区分了 TFBS（结合位点）和 TFRS（有调控功能的结合位点），这一概念区分对 AI 模型的任务定义（结合预测 vs 功能预测）有重要指导意义。

## 15 与已有知识连接

- **RegulonDB 历史版本**：本文是 RegulonDB 系列数据库的持续更新，早期版本（8.0、9.0、10.5）已在 [3, 10, 23] 中描述。本文的 HT 数据收集始于 2009 年（TSS），2012 年加入 ChIP-seq 和 gSELEX。
- **EcoCyc**：另一个 E. coli 数据库，与 RegulonDB 共享数据，本文提到 TFRS 数据同时上传至 EcoCyc [4]。
- **TEC 数据库**：提供 gSELEX 数据，本文的 gSELEX 子集来源于此 [26]。
- **proChIPdb**：提供 ChIP-seq 和 ChIP-exo 数据，本文的 ChIP-exo 子集来源于此 [27]。
- **COLOMBOS**：表达数据数据库，与本文的 RNA-seq 数据互补 [25]。
- **MCO（Microbial Conditions Ontology）**：本文使用 MCO 作为生长条件标准化的框架 [28]。
- **SnakeChunks**：本文开发的 ChIP-seq 分析流程，基于 snakemake [1, 29]。
- **RSAT 工具套件**：用于 motif 识别和 TFBS 预测，本文使用 RSAT matrix-scan 和 peak-motifs [43-45]。
- **候选方向**：本文的 HT 数据可作为 AI 模型（如 DeepBind、DeepSEA 类模型）在细菌 TF–DNA 结合预测上的训练/验证数据；ChIP-seq 统一处理流程可结合 ATAC-seq 等数据用于开放染色质区域分析。

## 16 研究想法

> Agent 生成的研究候选

1. **名称**：基于 RegulonDB HT 数据的 E. coli TF–DNA 结合预测模型基准测试
   - **来源局限/观察**：RegulonDB 11.0 提供了多技术（ChIP-seq、gSELEX、DAP-seq）的 TF 结合数据，但缺乏统一的基准测试集来评估不同预测模型的性能。
   - **核心假设**：利用 RegulonDB 的 HT-LT 映射数据构建高质量基准集，可系统评估现有 TF–DNA 结合预测模型在细菌上的表现。
   - **初步方法**：从 RegulonDB 提取多技术覆盖的 TF 结合数据，构建正负样本集；评估 DeepBind、DeepSEA、BPNet 等模型；比较不同技术来源数据的预测难度。
   - **验证方式**：交叉验证 AUC/PRC；与 DNase-seq  footprints 等独立数据验证。
   - **创新状态**：unverified

2. **名称**：跨技术 TF 结合位点一致性分析与集成学习框架
   - **来源局限/观察**：同一 TF 在不同技术（ChIP-seq vs gSELEX vs DAP-seq）下的结合位点存在差异，但缺乏系统性比较。
   - **核心假设**：不同技术的结合位点差异包含生物学信息（如体内 vs 体外、依赖辅助因子 vs 不依赖），可被利用来改进预测。
   - **初步方法**：对多技术覆盖的 TF（如 H-NS、Fur、Fis）进行 Venn 分析、motif 富集比较；构建多视图学习模型（multi-view learning）整合不同技术数据。
   - **验证方式**：在独立 ChIP-exo 数据上验证集成模型性能；比较单技术 vs 多技术训练的性能差异。
   - **创新状态**：unverified

3. **名称**：基于 RegulonDB 生长条件元数据的 TF 结合环境依赖性分析
   - **来源局限/观察**：RegulonDB 11.0 通过 NLP 提取了生长条件元数据，但尚未被用于分析 TF 结合的环境依赖性。
   - **核心假设**：TF 的结合位点在不同生长条件下显著不同，生长条件信息可提高结合预测的准确性。
   - **初步方法**：利用 RegulonDB 的 RNA-seq 数据（含生长条件注释）分析不同条件下的基因表达差异；将生长条件作为条件变量输入条件生成模型（conditional GAN 或 VAE）预测 TF 结合。
   - **验证方式**：在已知的应激响应 TF（如 OxyR、SoxR）上验证条件依赖性；比较有无条件信息的模型性能。
   - **创新状态**：unverified

4. **名称**：TFBS-TFRS 功能分类的深度学习模型
   - **来源局限/观察**：RegulonDB 明确区分 TFBS（仅结合）和 TFRS（结合且调控），但现有预测模型大多不区分这两类。
   - **核心假设**：TFBS 和 TFRS 在序列特征、染色质环境、进化保守性上存在可学习的差异。
   - **初步方法**：构建多任务学习模型，同时预测结合和调控功能；利用 RegulonDB 的 TFRS 标注作为调控功能标签；整合序列、结构（DNA shape）、进化保守性特征。
   - **验证方式**：在 RegulonDB 保留集上评估；与随机突变实验数据比较。
   - **创新状态**：unverified

5. **名称**：基于 RegulonDB 数据的 E. coli 转录调控网络嵌入表示学习
   - **来源局限/观察**：RegulonDB 包含丰富的调控关系数据（TF-TF、TF-基因），但尚未被用于学习调控网络的嵌入表示。
   - **核心假设**：调控网络的嵌入表示可捕获 TF 的功能相似性和调控机制差异，有助于预测未知的调控关系。
   - **初步方法**：从 RegulonDB 提取 TF-TF 和 TF-基因调控网络；使用图神经网络（GNN）或 node2vec 学习嵌入；结合序列特征进行调控关系预测。
   - **验证方式**：在已知调控关系上评估链接预测性能；与随机网络对比。
   - **创新状态**：unverified