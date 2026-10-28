## 01 基本信息

- **标题**：Integrative scATAC-seq and mtDNA mutation analysis reveals disease-driven regulatory aberrations in AML
- **作者与单位**：Tian, Chen; Dong, Yijun; Sun, Xin; Xu, Longchen; Ma, Xiaoli; Tao, Yuwei; Wang, Fang; Zhang, Haohang; Li, Jie; Li, Kun; Chen, Yasong; Liu, Hongxing; Lan, Xun（单位未提供）
- **期刊/预印本平台**：Science Bulletin
- **年份**：2025
- **论文类型**：研究论文（Research Article）
- **领域**：单细胞表观基因组学、急性髓系白血病（AML）、基因调控网络、线粒体DNA谱系追踪
- **关键词**：AML、mtscATAC-seq、cis-regulatory elements、WT1、CEBPB、GATA4、线粒体DNA追踪、基因调控网络
- **DOI/arXiv 号**：10.1016/j.scib.2025.07.009
- **代码**：未提供（cisGRN 算法为 in-house 开发，未提供公开代码链接）
- **数据**：未提供（原始测序数据未提供存取号）
- **阅读日期**：2025-08-09（基于 URL 访问日期推断）
- **该文在「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法/物理模拟」方向中的位置**：本文聚焦于转录因子（TF）与 cis-regulatory elements（CREs）结合的表观遗传调控，核心发现包括 WT1 锌指结构域突变导致其靶基因调控区染色质可及性下降和超甲基化，以及一个 CRE 突变引入 CEBPB 新结合基序从而激活增强子。该文属于「TF–DNA 结合机制 × 基因组变异/表观遗传」交叉方向，使用 cisGRN 算法（基于 motif 扫描和染色质可及性共变的 GRN 推断）而非深度学习或物理模拟方法，但其 TF 结合基序变异→结合改变→基因表达变化的因果链条验证范式（luciferase + prime editing）对本课题有直接借鉴价值。

## 02 一句话总结

本文通过 mtscATAC-seq 结合单细胞 RNA-seq 和自研 cisGRN 算法，在 AML 中鉴定出 WT1 锌指结构域突变（R467Q/R467L/R467W/H470Y/H470R）通过降低靶基因调控区染色质可及性和增加甲基化导致基因下调，以及一个早期出现的 CRE 突变通过引入 CEBPB 新结合基序激活 GATA4 表达促进 AML 增殖，并利用线粒体 DNA 追踪和机器学习识别出可预测耐药和复发风险的 LSC 样克隆。

## 03 研究问题

- **具体问题**：AML 中转录调控异常如何驱动疾病进展？哪些 cis-regulatory elements（CREs）的染色质可及性改变与 AML 分化异常相关？特定 TF 结合位点的突变如何影响基因调控？哪些克隆亚群与复发和耐药相关？
- **为什么重要**：AML 复发风险高，理解其进展机制和识别预后生物标志物对改善治疗结局至关重要。
- **现有方法为何不足**：传统 bulk 测序无法解析细胞异质性；单独 scATAC-seq 缺乏谱系追踪能力；现有 GRN 推断方法未充分利用 CRE 动态变化与 TF 结合基序变异之间的关联。
- **精确的「Can ... ?」研究问题**：Can integrative mtscATAC-seq with mtDNA lineage tracing and cisGRN analysis uncover disease-driven regulatory aberrations and track relapse-prone AML clones?

## 04 背景与发展脉络

> 注：以下脉络基于本文引言和讨论的叙述框架，标注为「仅本文框架」，未经外部系统核验。

1. **阶段一：bulk 表观基因组学**（如 bulk ATAC-seq、ChIP-seq）
   - 代表性方法：bulk ATAC-seq 鉴定开放染色质区域
   - 优点：可鉴定 CREs 和 TF 结合位点
   - 局限：丢失细胞异质性信息，无法关联克隆动态
2. **阶段二：单细胞表观基因组学**（scATAC-seq）
   - 代表性方法：scATAC-seq、sci-ATAC-seq
   - 优点：解析细胞类型特异性的染色质可及性
   - 局限：缺乏谱系追踪能力，难以关联克隆演化
3. **阶段三：线粒体单细胞多组学**（mtscATAC-seq）
   - 代表性方法：mtscATAC-seq（本文采用）
   - 优点：同时获得染色质可及性和 mtDNA 突变信息，实现克隆谱系追踪
   - 局限：mtDNA 突变覆盖度有限，需要补充 scRNA-seq
4. **阶段四：GRN 推断与功能验证**（本文主张的位置）
   - 代表性方法：cisGRN（本文自研）、SCENIC 等
   - 优点：将 CRE 动态与 TF 结合基序变异关联，结合功能实验（luciferase、prime editing）验证因果性
   - 局限：依赖 motif 扫描精度，对非经典结合模式覆盖有限

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| AML 复发风险高 | 即使治疗后缓解，仍存在高复发率 | 存在 LSC 样克隆亚群，对治疗具有耐药性 | 摘要：Given the high relapse risk of AML |
| 转录调控异常难以定位 | 造血分化过程中调控紊乱导致白血病发生 | 需要单细胞水平的染色质可及性分析才能解析 | 摘要：Disturbances in transcriptional regulation during hematopoiesis can lead to aberrant hematopoietic differentiation |
| 现有方法无法同时获得表观信息和谱系 | 单独 scATAC-seq 缺乏克隆追踪能力 | mtDNA 突变可作为内源条形码，但需与染色质可及性同时检测 | 摘要：applied mtscATAC-seq, supplemented with scRNA-seq |
| TF 结合位点突变的功能影响难以评估 | WT1 锌指突变导致靶基因下调，但机制不清 | 突变降低染色质可及性并增加甲基化，作者通过 cisGRN 和功能实验验证 | 摘要：mutations in the zinc finger domain of WT1 are associated with decreased chromatin accessibility and hypermethylation |
| CRE 突变如何影响 TF 结合难以预测 | 一个 CRE 突变引入 CEBPB 新结合基序 | 突变创造新 motif，增强 CEBPB 结合，激活增强子活性 | 摘要：introducing a new binding motif for CEBPB, which facilitates its binding to the enhancer |
| 耐药和复发预测不准确 | 现有标志物预测能力有限 | LSC 样克隆中的 marker genes 可更准确预测耐药和复发 | 摘要：identified marker genes in the clones that more accurately predict drug resistance and relapse risk |

## 06 核心思想

1. **表面方法**：对 AML 患者样本进行 mtscATAC-seq（同时捕获染色质可及性和 mtDNA 突变），辅以 scRNA-seq；构建单细胞造血参考图谱将肿瘤细胞映射到分化轨迹；使用自研 cisGRN 算法分析 CRE 动态与 TF 结合；通过 luciferase 报告实验和 prime editing 验证功能；用 mtDNA 追踪和机器学习预测复发风险。

2. **核心洞察**：
   - TF 结合位点（尤其是锌指结构域）的突变不仅改变蛋白质-DNA 直接互作，还通过影响染色质可及性和 DNA 甲基化状态间接重塑调控环境，形成「突变→可及性↓→甲基化↑→基因↓」的级联效应。
   - CRE 中的非编码突变可以通过引入新的 TF 结合基序（如 CEBPB motif）来「劫持」增强子活性，这是一种顺式调控层面的功能获得机制。
   - mtDNA 突变作为内源谱系条形码，可以将表观状态与克隆演化历史关联，从而识别具有 LSC 特征的复发倾向克隆。

3. **可能的普适教训** [Analysis]：
   - TF–DNA 互作的扰动不仅来自 TF 自身的突变，也来自其结合位点（CRE）的顺式突变；研究疾病相关调控异常时需同时考虑这两个层面。
   - 单细胞多组学（表观 + 谱系）的整合比单一组学更能揭示「谁在何时何地发生了调控改变」。
   - 功能验证（如 prime editing 精确引入/修复突变）是将关联性发现转化为因果性结论的关键步骤。

## 07 方法总览

- **输入**：AML 患者骨髓/外周血样本（具体样本量未提供），进行 mtscATAC-seq 和 scRNA-seq
- **输出**：AML 细胞的分化状态图谱、CRE 可及性变化、WT1 靶基因调控异常、CEBPB-GATA4 调控轴、复发相关克隆及其 marker genes
- **模块**：
  1. 单细胞造血参考图谱构建（将肿瘤细胞映射到正常造血分化轨迹）
  2. cisGRN 算法（分析 CRE 动态与 TF 结合基序的关联）
  3. WT1 突变功能验证（luciferase、prime editing）
  4. CRE 突变功能验证（luciferase 增强子活性、prime editing）
  5. mtDNA 谱系追踪 + 机器学习模型（识别复发相关克隆）
- **训练**：机器学习模型用于预测耐药和复发风险（具体算法和训练细节未提供）
- **工具**：mtscATAC-seq、scRNA-seq、cisGRN（自研）、luciferase reporter assay、prime editing
- **反馈回路**：cisGRN 预测 → 功能实验验证 → 修正调控模型
- **假设**：mtDNA 突变可作为可靠的克隆谱系条形码；染色质可及性变化反映调控活性变化；CRE 突变可通过改变 TF 结合影响基因表达

**文字流程**：
1. 收集 AML 患者样本，进行 mtscATAC-seq 和 scRNA-seq
2. 构建单细胞造血参考图谱，将肿瘤细胞映射到分化轨迹上，鉴定 AML 分化相关的 CRE 可及性改变
3. 使用 cisGRN 算法分析 CRE 动态，发现 WT1 锌指突变与靶基因调控区可及性下降和甲基化增加相关
4. 对 5 个 WT1 锌指突变（R467Q/R467L/R467W/H470Y/H470R）进行功能验证，确认其致病效应
5. 鉴定一个 CRE 突变，该突变引入 CEBPB 新结合基序，通过 luciferase 和 prime editing 验证其激活增强子、促进 GATA4 表达和 AML 增殖
6. 利用 mtDNA 追踪和机器学习，识别 LSC 样复发相关克隆及其 marker genes

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 单细胞造血参考图谱 | 将肿瘤细胞映射到正常分化轨迹 | 确定 AML 细胞的分化状态和异常 | 输入：正常造血 scATAC-seq 数据；输出：分化轨迹和 AML 细胞映射位置 | 摘要：constructing a single-cell hematopoiesis reference and mapping tumor cells to it | 预期影响：无法定位 AML 分化异常的具体阶段 [Analysis] |
| cisGRN 算法 | 分析 CRE 动态与 TF 结合基序的关联 | 从染色质可及性数据推断调控关系 | 输入：scATAC-seq 染色质可及性矩阵、motif 注释；输出：TF-CRE-靶基因调控网络 | 摘要：identified significant alterations in chromatin accessibility of CREs associated with AML differentiation | 预期影响：无法系统发现 WT1 靶基因调控异常 [Analysis] |
| WT1 突变功能验证 | 确认 5 个锌指突变的致病效应 | 将关联性发现转化为因果性结论 | 输入：WT1 突变体；输出：靶基因表达和染色质状态变化 | 摘要：Functional validation confirmed the pathogenic effects of five WT1 zinc finger mutations | 实测消融效应：未提供（未做 WT1 突变验证的消融对照） |
| CRE 突变功能验证（luciferase + prime editing） | 验证 CRE 突变引入 CEBPB motif 并激活增强子 | 证明非编码突变的功能获得机制 | 输入：野生型和突变型 CRE 报告构建体；输出：增强子活性和 GATA4 表达变化 | 摘要：These effects were validated through luciferase reporter assays and prime editing experiments | 实测消融效应：未提供（未做 CEBPB 敲低/结合位点突变的对照） |
| mtDNA 谱系追踪 + 机器学习 | 识别复发相关克隆及其 marker genes | 将表观状态与克隆演化关联，预测复发风险 | 输入：mtDNA 突变谱、克隆表观特征；输出：复发风险预测模型和 marker genes | 摘要：identified marker genes in the clones that more accurately predict drug resistance and relapse risk | 预期影响：无法追踪复发倾向克隆 [Analysis] |

## 09 关键公式符号

不适用。本文为实验生物学研究，未提供数学模型或公式。cisGRN 算法的具体数学框架未在摘要中披露。

## 10 实验设计与证据链

- **数据集/群体**：AML 患者样本（具体数量未提供），进行 mtscATAC-seq 和 scRNA-seq
- **规模**：未提供
- **指标**：染色质可及性变化、基因表达变化、增强子活性（luciferase）、细胞增殖
- **基线**：正常造血细胞参考图谱
- **预算**：未提供
- **骨干/仪器**：mtscATAC-seq、scRNA-seq 平台（具体型号未提供）
- **oracle 输入**：正常造血 scATAC-seq 数据用于构建参考图谱
- **评测协议**：未提供（无交叉验证、独立队列验证等描述）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| AML 细胞映射到造血参考图谱 | AML 存在分化相关的 CRE 可及性改变 | AML vs 正常造血细胞 | 鉴定出显著 CRE 可及性改变 | AML 分化伴随调控异常 | 无法确定这些改变是驱动因素还是伴随现象 | 摘要 |
| cisGRN 分析 WT1 靶基因 | WT1 锌指突变与靶基因调控区可及性下降和甲基化增加相关 | 突变型 vs 野生型 WT1 | 突变与可及性下降、超甲基化、基因下调相关 | WT1 突变通过表观机制导致基因下调 | 未证明直接因果性（缺乏 ChIP-seq 或体外结合实验） | 摘要 |
| 5 个 WT1 突变功能验证 | 这些突变具有致病效应 | 突变体 vs 野生型 | 确认致病效应 | WT1 锌指突变是功能性致病突变 | 未提供具体效应大小和表型细节 | 摘要 |
| CRE 突变 luciferase 验证 | 突变引入 CEBPB motif 并激活增强子 | 突变型 vs 野生型 CRE | 增强子活性增加 | CRE 突变通过 CEBPB 结合激活增强子 | 未排除其他 TF 的贡献 | 摘要 |
| Prime editing 实验 | 修复 CRE 突变可逆转表型 | 修复 vs 未修复 | 验证了 CRE 突变的功能 | CRE 突变是 AML 增殖的驱动因素 | 未提供体内实验证据 | 摘要 |
| mtDNA 追踪 + 机器学习 | 可识别复发相关克隆 | 复发 vs 非复发克隆 | 鉴定出 LSC 样克隆和 marker genes | 可预测耐药和复发风险 | 未提供独立验证队列的预测性能 | 摘要 |

## 11 结论正确解读

- **任务范围**：本文覆盖 AML 的转录调控异常鉴定、TF 突变功能验证、CRE 突变功能验证、复发克隆识别四个层面。未涉及治疗干预或临床试验。
- **oracle/真值输入**：正常造血参考图谱作为「正常状态」的基准；mtDNA 突变作为克隆谱系的真值标记。
- **端到端状态**：从患者样本到复发风险预测的完整流程已展示，但预测模型的独立验证未在摘要中描述。
- **算力成本**：未提供。
- **历史数据依赖**：依赖正常造血参考图谱的构建质量；mtDNA 突变追踪依赖突变覆盖度。
- **模型依赖**：cisGRN 算法依赖 motif 扫描精度；机器学习模型的具体算法和特征未披露。
- **最难情形**：低 mtDNA 突变覆盖度的样本可能无法可靠追踪克隆；WT1 突变效应可能受遗传背景影响。
- **群体/领域边界**：结论基于 AML 患者样本，是否适用于其他白血病类型或实体瘤未知。
- **不确定性**：WT1 突变与靶基因调控异常的关联强度、CEBPB 结合的直接证据（如 ChIP-seq）未在摘要中提供。

**有边界的复述**：在本文分析的 AML 患者样本中，WT1 锌指结构域突变与靶基因调控区染色质可及性下降和超甲基化相关，一个特定 CRE 突变可引入 CEBPB 结合基序并激活增强子促进 GATA4 表达，且基于 mtDNA 追踪和机器学习的克隆分析可识别与耐药和复发相关的 LSC 样克隆。这些结论限于所分析的样本集和实验条件。

## 12 作者自认局限

在提供的材料（摘要）中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限）：
- 摘要中提及「supplemented with scRNA-seq」，暗示 mtscATAC-seq 单独可能不足以全面解析表达调控，需要多组学补充。
- 机器学习模型的预测能力描述为「more accurately predict」，暗示与现有方法相比有改进但非绝对准确。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| WT1 突变与靶基因可及性下降的关联基于 cisGRN 推断 | cisGRN 可能将间接关联误判为直接调控；可及性下降可能是分化状态改变的结果而非原因 | 决定 WT1 突变是否直接驱动调控异常 | 使用 ChIP-seq 验证 WT1 在靶位点的直接结合；在 isogenic 细胞系中引入/修复突变观察染色质变化 | 摘要：cisGRN 分析发现关联，但未提及 ChIP-seq 验证 |
| CRE 突变引入 CEBPB motif 的结论基于序列分析 | 其他 TF 也可能结合该区域；CEBPB 结合可能是伴随现象 | 影响对 AML 增殖驱动机制的理解 | 进行 CEBPB 特异性 ChIP-seq；突变 CEBPB 结合位点后观察增强子活性变化 | 摘要：validated through luciferase reporter assays and prime editing experiments，但未提及 CEBPB 直接结合证据 |
| mtDNA 追踪依赖突变覆盖度 | 低覆盖度样本可能产生假阴性克隆鉴定 | 影响复发预测的可靠性 | 报告 mtDNA 突变覆盖度统计和克隆鉴定的置信度阈值 | 摘要：未提供覆盖度信息 |
| 机器学习模型预测复发风险 | 未描述训练集/验证集划分、特征选择、模型类型 | 无法评估过拟合风险和泛化能力 | 提供模型细节和独立验证队列结果 | 摘要：未提供模型细节 |
| 样本量未披露 | 小样本可能导致结论不可靠 | 影响所有结论的普适性 | 报告样本量和统计功效分析 | 摘要：未提供样本量 |

## 14 Agent 提炼的知识候选

**可迁移的概念**：
1. **TF 突变 → 染色质可及性 → 甲基化 → 基因表达的级联模型**：本课题研究 TF–DNA 结合机制时，可借鉴此框架，将 TF 突变的影响从「直接结合改变」扩展到「表观状态重塑」的多层效应。
2. **CRE 突变引入新 TF motif 的「结合位点劫持」机制**：在预测 TF–DNA 互作时，需考虑非编码突变可能创造新结合位点，而非仅破坏现有位点。
3. **单细胞多组学整合策略**：将表观状态（ATAC）与谱系追踪（mtDNA）结合，可同时解析「调控状态」和「克隆演化」，适用于研究 TF 结合异常的克隆动态。

**可迁移的方法**：
1. **cisGRN 算法思路**：基于 CRE 可及性动态与 TF motif 共变推断调控网络，可迁移到其他 TF–DNA 互作研究中，尤其适用于 scATAC-seq 数据。
2. **功能验证组合拳**：luciferase reporter assay（验证增强子活性）+ prime editing（精确引入/修复突变）的组合，是验证 TF 结合位点突变因果性的金标准流程。
3. **参考图谱映射策略**：构建正常状态参考图谱并将疾病细胞映射到其上，可系统鉴定调控异常，适用于任何分化相关疾病。

**可迁移到本课题的具体方式**：
- 若本课题关注 TF–DNA 结合机制，可借鉴「突变→可及性→甲基化→表达」的级联分析框架，将 TF 结合预测从静态 motif 匹配扩展到动态表观状态。
- 可参考 cisGRN 的「CRE 动态 + motif 共变」思路，开发或改进 TF 结合位点预测算法。
- 可借鉴「CRE 突变引入新 motif」的发现模式，在基因组变异分析中主动搜索「获得功能」型 TF 结合位点突变。

## 15 与已有知识连接

- **相似工作**：与 SCENIC（Aibar et al., 2017, Nature Methods）等 GRN 推断工具类似，cisGRN 也基于 motif 和共表达/共可及性推断调控网络，但 cisGRN 更强调 CRE 动态变化。
- **TF 突变与疾病**：WT1 在 AML 中的突变已有广泛研究（如 Owen et al., 2016, Blood），本文的新颖之处在于将锌指突变与染色质可及性和甲基化状态直接关联。
- **非编码突变与 TF 结合**：与「非编码突变通过改变 TF 结合影响疾病」的文献一致（如 Khurana et al., 2016, Nature Reviews Genetics），本文提供了 AML 中的具体案例。
- **线粒体 DNA 追踪**：与 Ludwig et al. (2019, Nature) 等利用 mtDNA 突变追踪克隆演化的方法一致，本文将其与表观组学结合。
- **候选方向** [Analysis]：本文的「CRE 突变引入新 motif」机制可连接到「TF 结合位点变异的功能预测」这一计算生物学方向，但该连接为本文未明确提及的推断。

## 16 Agent 生成的研究候选

**候选 1：基于深度学习的 TF 结合位点突变效应预测模型**
- **名称**：TF-BindMut：预测 TF 结合位点突变对结合亲和力和染色质状态的影响
- **来源局限/观察**：本文发现 WT1 锌指突变和 CRE 突变均影响 TF–DNA 互作，但缺乏系统性的计算预测工具；现有工具（如 DeepSEA、Basenji）主要预测染色质状态而非 TF 结合亲和力变化
- **核心假设**：结合 DNA 序列特征、TF motif 信息、染色质可及性数据，深度学习模型可准确预测单核苷酸变异对 TF 结合的影响
- **相对本文的增量**：将本文的个案发现（WT1 突变、CEBPB motif 引入）推广为可泛化的预测模型
- **初步方法**：使用 scATAC-seq 数据训练 CNN/Transformer 模型，输入为 TF 结合位点序列 + 变异信息，输出为结合亲和力变化和染色质可及性变化；用本文的 WT1 和 CEBPB 案例作为验证集
- **验证方式**：与 ChIP-seq 数据对比；在 isogenic 细胞系中验证预测的突变效应
- **创新状态**：unverified

**候选 2：TF 突变与 CRE 突变的协同效应分析框架**
- **名称**：TF-CRE CoMut：分析 TF 自身突变与其结合位点突变的协同调控异常
- **来源局限/观察**：本文分别研究了 WT1 突变（TF 侧）和 CRE 突变（顺式侧），但未系统分析两者在同一患者中的协同效应
- **核心假设**：在 AML 中，TF 突变和其靶基因 CRE 突变可能协同作用，放大调控异常
- **相对本文的增量**：将本文的「TF 侧」和「顺式侧」发现整合为统一分析框架
- **初步方法**：对 AML 患者进行配对分析，检测 WT1 突变状态与靶基因 CRE 突变/甲基化状态的关联；使用 cisGRN 扩展分析
- **验证方式**：独立 AML 队列验证；功能实验验证协同效应
- **创新状态**：unverified

**候选 3：基于物理模拟的 TF 突变结合自由能变化预测**
- **名称**：TF-MutΔΔG：使用分子动力学模拟预测 TF 锌指突变对 DNA 结合自由能的影响
- **来源局限/观察**：本文的 WT1 锌指突变（R467Q 等）位于 DNA 结合界面，但未进行原子层面的结合机制分析；现有 MD 模拟方法可预测突变对蛋白-DNA 结合的影响
- **核心假设**：MD 模拟可准确预测 WT1 锌指突变的结合自由能变化，并与染色质可及性数据关联
- **相对本文的增量**：为本文的表观遗传观察提供物理化学机制解释
- **初步方法**：构建 WT1 锌指-DNA 复合物结构（基于同源建模或 AlphaFold），对 5 个突变进行 MD 模拟和 MM/PBSA 结合自由能计算
- **验证方式**：与本文的功能验证结果对比；预测新的致病突变
- **创新状态**：unverified