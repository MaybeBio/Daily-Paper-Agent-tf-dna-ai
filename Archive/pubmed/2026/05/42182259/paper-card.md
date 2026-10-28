## 01 基本信息
- **标题**：Using Deep Learning Models of Gene Regulation to Guide Drug Prioritization
- **作者**：Huang, Xiaoqin; Ovcharenko, Ivan
- **单位**：未提供（推测为 NIH 相关机构，依据致谢中的 Intramural Research Program of NIH）
- **期刊/平台**：bioRxiv (preprint server for biology)
- **年份**：2026
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：基因调控深度学习 × 药物重定位
- **关键词**：deep learning, enhancer, allele-specific, transcription factor, drug repurposing, GWAS, FOXA1, breast cancer
- **DOI/arXiv**：10.64898/2026.05.11.724354
- **代码**：未提供（TREDNet 预训练模型已存放于 Zenodo: https://doi.org/10.5281/zenodo.8161621）
- **数据**：ENCODE、LINCS L1000 (GSE70138, GSE92742)、KnockTF 2.0、TCGA-BRCA、GWAS Catalog (GCST004988)、DGIdb 5.0、DrugCentral、ChEMBL
- **阅读日期**：2026-06-01（估计）
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作（TF–DNA 结合机制）× 深度学习」方向中的**调控基因组学应用**分支。核心贡献在于将 enhancer 预测模型（TF–DNA 结合的直接体现）与 TF 敲低转录组、药物诱导转录组连接，形成从非编码变异→TF 结合→基因表达→药物候选的完整链路。对 TF–DNA 结合机制研究者的可迁移价值在于：展示了如何用 allele-specific enhancer 预测 + attribution-based motif discovery 推断疾病相关 TF 结合偏好，以及如何用 TF 敲低转录组作为 TF 结合功能后果的代理。

## 02 一句话总结
本文开发了一个整合深度学习框架，通过 cell type-specific enhancer 预测模型（TREDNet）评估 GWAS 变异的 allele-specific 效应，结合 attribution-based motif discovery 推断疾病相关 TF（乳腺癌中为 FOXA1），再通过 FOXA1 敲低转录组与 LINCS 药物诱导转录组的 directional concordance 打分，从 6,605 个化合物中优先排序出 63 个候选药物（含 18 个已批准药物），其中 8 个经 drug-gene interaction 数据进一步精炼。

## 03 研究问题
- **具体问题**：如何将非编码 GWAS 变异（占复杂疾病风险变异 90% 以上）转化为可操作的药物重定位假设？
- **为什么重要**：现有药物重定位方法主要基于编码变异或转录组 anti-correlation，缺乏对非编码调控变异的显式建模，导致疾病遗传机制与治疗假设之间的连接断裂。
- **现有方法不足**：(1) 多数方法依赖基因 proximity 或统计关联，不建模 allele-specific 调控效应；(2) 缺乏 cell type-specific 的调控上下文；(3) 未将 TF 结合偏好与药物转录效应系统整合。
- **精确研究问题**：Can allele-specific enhancer prediction combined with TF-centered transcriptional concordance scoring prioritize drug candidates that are directionally anti-correlated with disease-associated pathway activity?

## 04 背景与发展脉络
*注：以下脉络基于本文框架及引用文献，部分经外部核验，标注如下。*

1. **药物重定位的计算方法**（经外部核验）
   - 基因表达 signature matching（如 Connectivity Map, CMap）：通过药物诱导转录组与疾病转录组的 anti-correlation 识别候选药物。局限：不建模上游调控变异。
   - 网络-based inference：利用蛋白互作或基因调控网络传播疾病信号。局限：缺乏 allele-specific 分辨率。
   - 结构-based docking：适用于编码靶点，不适用于非编码调控变异。

2. **调控基因组学的深度学习方法**（经外部核验）
   - 早期：Encode/DNase-seq 特征 + 传统 ML（如 gkm-SVM）
   - 深度卷积网络：DeepSEA、Basenji 等直接从序列预测调控活性
   - 本框架采用 TREDNet（两阶段：预训练 + 微调），在 4,560 个 ENCODE 图谱上预训练，再对每个 cell type 微调

3. **Allele-specific 调控效应建模**（经外部核验）
   - 早期：deltaSVM 等基于 k-mer 的 allele-specific 打分
   - 深度学习方法：DeepSEA 的 allele-specific 输出、Enformer 的 in silico mutagenesis
   - 本文：Δscore = P(risk) − P(protective)，结合 DeepLIFT + TF-MoDISco 归因

4. **TF 敲低转录组资源**（经外部核验）
   - KnockTF 2.0：456 TFs × 357 cell lines 的敲低/敲除转录组
   - 本文将其与 LINCS L1000 药物转录组整合，形成 TF-centered 药物打分

5. **本文主张的位置**：首次将 allele-specific enhancer 预测 → TF motif 归因 → TF 敲低转录组 → 药物转录组 concordance 串成完整链路，实现「从非编码变异到药物候选」的端到端计算框架。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 非编码变异难以解释 | >90% GWAS 风险变异位于非编码区，但多数药物重定位方法忽略 | 缺乏对 enhancer 调控效应的显式建模 | Background 第 1-2 段 |
| 缺乏 cell type 特异性 | 同一变异在不同细胞类型中调控效应不同 | 增强子活性高度 cell type-specific | Results "Deep learning enhancer modeling" 节；7 个 cell lines 分别训练模型 |
| TF 结合偏好难以从序列推断 | 需要从 allele-specific 效应中识别关键 TF | 单变异效应微弱，需要 attribution 方法聚合信号 | Results "Allele-specific TF convergence" 节；DeepLIFT + TF-MoDISco |
| 药物转录组与疾病机制脱节 | 传统 anti-correlation 缺乏上游调控上下文 | 未将 TF 敲低转录组作为中间表型 | Results "Drug candidate prioritization" 节；FOXA1 敲低作为桥梁 |
| 统计功效不足 | 单变异 allele-specific 效应小 | 需要聚合多个变异信号 | 1,537 个候选变异（top 10% |Δscore|）用于 motif discovery |
| 药物-基因互作数据不完整 | 数据库非 cell type 特异性 | DGIdb 5.0 聚合多来源但缺乏细胞上下文 | Discussion 局限性第 3 点 |

## 06 核心思想

### 1) 表面方法
一个四阶段流水线：(a) 用 TREDNet 训练 7 个 cell type-specific enhancer 预测模型；(b) 对 GWAS 变异计算 Δscore 并筛选候选调控变异；(c) 用 DeepLIFT + TF-MoDISco 做 attribution-based motif discovery 推断关键 TF；(d) 用 TF 敲低转录组与 LINKS 药物转录组的 concordance 打分排序药物。

### 2) 核心洞察
**TF 是连接非编码变异与药物响应的「枢纽」**。非编码变异通过改变 TF 结合亲和力影响 enhancer 活性，而 TF 敲低转录组捕捉了该 TF 功能丧失的全局转录后果；药物诱导转录组若与 TF 敲低方向一致，则药物可能模拟或拮抗该 TF 的调控网络效应。这一洞察将「变异→TF 结合」的静态序列分析，扩展为「变异→TF 结合→转录网络→药物响应」的动态功能链路。

### 3) 可能的普适教训 [Analysis]
- **中间表型设计**：在「基因型→表型」的长链路中，引入 TF 敲低转录组作为中间表型，可显著提高统计功效和机制可解释性。这对 TF–DNA 互作研究者的启示是：TF 结合预测（静态）应与 TF 扰动转录组（动态）联合建模。
- **Attribution 聚合策略**：单变异效应微弱时，用 attribution 方法（DeepLIFT）在多个候选变异上聚合 motif 信号，比单变异分析更稳健。可迁移到其他 TF 结合机制研究。
- **Cell type 特异性是核心**：7 个 cell lines 分别训练模型而非共享模型，说明 enhancer 预测的 cell type 特异性不可忽略。对 TF–DNA 互作研究意味着：TF 结合 motif 的解读必须放在特定细胞上下文中。

## 07 方法总览

- **输入**：(1) 7 个 cell lines 的 ATAC-seq/DNase-seq + H3K27ac 峰；(2) GWAS 汇总统计（135 studies, 42 traits）；(3) LINCS L1000 药物诱导转录组（6,605 compounds in MCF7）；(4) KnockTF 2.0 TF 敲低转录组；(5) DGIdb 5.0 drug-gene 互作数据
- **输出**：63 个候选化合物（含 18 个已批准药物），进一步精炼为 8 个具有 drug-gene 互作证据的候选
- **模块**：
  1. TREDNet enhancer 预测（两阶段：ENCODE v4 预训练 + cell type 微调）
  2. Allele-specific 打分（Δscore = P(risk) − P(protective)）
  3. DeepLIFT + TF-MoDISco motif discovery
  4. TF 敲低 concordance 打分（KD_concordance = Mean(z_up) − Mean(z_down)）
  5. Pathway anti-correlation 分析（TCGA-BRCA DEGs + hallmark GSEA）
  6. DGIdb drug-gene 互作精炼
- **训练**：5-fold cross-validation，chromosome-level holdout 防泄漏；负样本 1:10 采样
- **反馈回路**：无显式迭代反馈；各阶段为流水线式串联
- **文字流程**：先训练 enhancer 模型 → 对 GWAS 变异计算 Δscore 并筛选（top 10% |Δscore| + 至少一个 allele 超过 FPR<10% 阈值）→ DeepLIFT 归因 + TF-MoDISco 聚类 motif → 在 MCF7 中计算每个药物的 FOXA1 敲低 concordance 得分 → 筛选 top 10% 得分的化合物 → 对候选化合物进行 8 条 hallmark pathway 的 anti-correlation 验证 → 用 DGIdb 互作数据精炼最终候选列表

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| TREDNet enhancer 预测 | 从序列预测 cell type-specific enhancer 活性 | 提供 allele-specific 打分的底层模型 | 输入：2kb 序列；输出：enhancer 概率 | AUROC 0.91–0.98, AUPRC 0.58–0.86（7 cell lines）；MCF7: AUROC 0.91, AUPRC 0.65 | 预期影响：无此模块则无法计算 Δscore，整个框架失效 [预期] |
| Allele-specific 打分（Δscore） | 量化风险/保护 allele 的 enhancer 预测差异 | 识别候选调控变异 | 输入：risk/protective allele 序列；输出：Δscore | 1,537 个变异（7.5%）通过筛选 | 预期影响：无此模块则无法连接 GWAS 变异与调控效应 [预期] |
| DeepLIFT + TF-MoDISco | 从 attribution 信号中识别 TF motif | 推断疾病相关 TF | 输入：allele-specific 序列 + 模型梯度；输出：motif 富集 | FOXA1: 40 vs 0 seqlets (risk vs protective, p=4.9×10⁻¹²)；FOXD2: 35 vs 0 | 预期影响：无此模块则无法确定中心 TF（FOXA1）[预期] |
| TF 敲低 concordance 打分 | 量化药物转录组与 TF 敲低转录组的 directional 一致性 | 将 TF 机制转化为药物排序 | 输入：LINCS 药物 z-score + KnockTF 敲低 DEGs；输出：KD_concordance 得分 | 63 个候选化合物得分显著高于背景（permutation p<2.0×10⁻⁴） | 预期影响：无此模块则无法从 TF 机制生成药物候选 [预期] |
| Pathway anti-correlation 分析 | 验证候选药物转录效应与疾病通路方向相反 | 提供疾病相关性的独立验证 | 输入：TCGA-BRCA DEGs + hallmark 通路；输出：8 条通路的 anti-correlation 得分 | 54% 候选化合物在全部 8 条通路中 anti-correlated（vs 5.3% 非候选） | 预期影响：无此模块则缺乏疾病相关性的功能验证 [预期] |
| DGIdb drug-gene 互作精炼 | 用已知药物-靶点互作过滤候选 | 提供独立于转录组的证据 | 输入：63 个候选 + DGIdb 5.0；输出：8 个最终候选 | 13 个化合物有与 FOXA1 调控基因的已知互作 | 预期影响：无此模块则最终候选列表缺乏靶点层面的支持 [预期] |

*注：所有消融效应均为预期（作者未做模块移除实验），标注为 [预期]。*

## 09 关键公式符号

1. **Allele-specific enhancer 差异得分**：
   Δscore = P(risk allele) − P(protective allele)
   - P：TREDNet 预测的 enhancer 概率（0-1）
   - 用途：量化单变异对 enhancer 活性的影响方向与大小
   - 直觉：正值表示风险 allele 增强 enhancer 活性，负值表示减弱

2. **TF 敲低 concordance 得分**：
   KD_concordance = Mean(z_up) − Mean(z_down)
   - z_up：TF 敲低后上调基因在药物处理中的 z-score
   - z_down：TF 敲低后下调基因在药物处理中的 z-score
   - 用途：衡量药物转录组与 TF 敲低转录组的 directional 一致性
   - 直觉：正值表示药物诱导的基因表达变化与 TF 敲低方向一致（药物模拟 TF 功能丧失）

3. **富集分析**（LDSC）：
   - 基于回归的 partitioned heritability，估计 enhancer annotation 对 trait heritability 的贡献
   - 统计量：回归系数（enrichment），z-test 检验显著性

4. **Fisher's exact test**：
   - 用于 TF motif 富集（risk vs protective seqlets）和 drug-gene 互作重叠
   - 单侧检验，p < 0.05 显著

5. **Permutation test**：
   - 5,000 次随机基因集置换生成 null 分布
   - 用于评估 KD_concordance 得分的统计显著性

## 10 实验设计与证据链

**数据集/群体**：
- 7 个 cell lines：A673, HCT116, HepG2, IMR90, K562, MCF7, PC3（ENCODE 表观基因组）
- GWAS：135 studies, 42 traits（GWAS Catalog）
- 药物转录组：LINCS L1000, 6,605 compounds in MCF7
- TF 敲低转录组：KnockTF 2.0（456 TFs × 357 cell lines）
- 乳腺癌表达：TCGA-BRCA 肿瘤 vs 正常组织

**指标**：
- Enhancer 预测：AUROC, AUPRC
- 富集：LDSC enrichment, fold-enrichment, p-value
- 药物打分：KD_concordance 得分分布，permutation p-value
- 通路验证：8 条 hallmark 通路的 anti-correlation 阳性率

**评测协议**：
- Enhancer 模型：5-fold cross-validation，chromosome-level holdout
- 候选变异筛选：FPR < 10% 阈值 + top 10% |Δscore|
- 药物筛选：top 10% KD_concordance 得分
- 通路验证：Fisher's exact test 比较候选 vs 非候选化合物

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|-------------------|------|
| Enhancer 模型性能 | TREDNet 能准确区分 enhancer vs 非 enhancer | 7 cell lines, chromosome holdout | AUROC 0.91–0.98, AUPRC 0.58–0.86 | 模型可用于 allele-specific 打分 | 未与最新 SOTA（如 Enformer）对比 | Results 图 S1A-B |
| Heritability 富集 | MCF7 enhancer 富集乳腺癌 heritability | MCF7 vs 其他 cell lines, 42 traits | 乳腺癌 heritability 显著富集于 MCF7 enhancer（10.5-fold, p=4.1×10⁻⁶） | MCF7 是乳腺癌的正确细胞上下文 | 未做共定位或 fine-mapping 验证 | Results 图 S1C |
| Allele-specific 变异筛选 | 存在 allele-dependent enhancer 效应 | 20,619 个 GWAS 变异 | 1,537 个（7.5%）通过筛选 | 非编码变异具有可检测的调控效应 | 未用实验（如 MPRA）验证 | Results 图 S2C |
| FOXA1 motif 富集 | 风险 allele 富集 FOXA1 motif | risk vs protective allele attribution | FOXA1: 40 vs 0 seqlets (p=4.9×10⁻¹²) | FOXA1 是乳腺癌关键调控因子 | 未验证 FOXA1 结合差异（如 ChIP-seq） | Results 图 S2A, 表 S1 |
| 药物 concordance 打分 | 候选药物转录组与 FOXA1 敲低一致 | 63 候选 vs 6,542 非候选 | 候选得分显著更高（permutation p<2.0×10⁻⁴） | 打分能富集 FOXA1 相关药物 | 未做体外/体内验证 | Results 图 3A |
| Pathway anti-correlation | 候选药物抑制乳腺癌通路 | 8 条 hallmark 通路 | 54% 候选在全部 8 条通路 anti-correlated（vs 5.3% 非候选） | 候选药物具有疾病相关性 | 未验证通路蛋白水平变化 | Results 图 4B-C |
| Drug-gene 互作验证 | 候选药物靶点与 FOXA1 调控基因重叠 | DGIdb 5.0 互作数据 | 13/63 有已知互作，8 个最终候选 | 独立证据支持候选 | 互作数据不完整且非 cell type 特异 | Results 图 5, 表 1 |

## 11 核心结论

1. **MCF7 enhancer 显著富集乳腺癌 heritability**（10.5-fold, p=4.1×10⁻⁶），支持 cell type-specific enhancer 建模作为连接非编码变异与疾病的桥梁。
2. **乳腺癌风险 allele 显著富集 FOXA1 motif**（40 vs 0 seqlets, p=4.9×10⁻¹²），且 FOXA1 在肿瘤中上调（log2FC=2.18），提示 FOXA1 是乳腺癌非编码风险变异的汇聚点。
3. **FOXA1 敲低 concordance 打分能有效富集候选药物**：63 个候选化合物（含 18 个已批准药物）的 concordance 得分显著高于背景。
4. **54% 的候选药物在全部 8 条乳腺癌 hallmark 通路中显示 anti-correlated 转录效应**（vs 5.3% 非候选），支持候选药物的疾病相关性。
5. **8 个最终候选化合物**具有 drug-gene 互作证据，包括 proteasome inhibitors（ixazomib, bortezomib, carfilzomib）等。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 计算预测需实验验证 | 候选变异和药物均为计算推断，未做实验确认 | 需要实验验证调控效应和治疗效果 | Discussion 局限性第 1 点 |
| 数据覆盖有限 | 仅 7 个 cell lines 有完整表观基因组数据 | 扩展至更多 cell types 和 tissues | Discussion 局限性第 2 点 |
| drug-gene 数据库不完整 | DGIdb 5.0 非 cell type 特异且可能遗漏 | 整合更全面的 cell type-specific 互作数据 | Discussion 局限性第 3 点 |
| 癌症细胞系局限 | 使用 cancer-derived cell lines 引入体细胞变异 | 使用非转化细胞或 patient-derived 模型 | Discussion 局限性第 4 点 |
| enhancer 模型预测的是概率而非直接活性 | Δscore 反映模型预测差异，非实验测量的 enhancer 活性 | 结合 STARR-seq 或 MPRA 等高通量实验验证 | Discussion 局限性第 5 点 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| FOXA1 motif 富集基于模型 attribution，而非实验结合数据 | Attribution 方法可能反映模型偏差而非真实 TF 结合；40 vs 0 的极端比例可能源于模型对 FOXA1 motif 的过度敏感 | 若 attribution 有偏，则整个 TF 推断环节可能指向错误 TF | 用独立 ChIP-seq 数据验证 FOXA1 在候选变异位点的等位基因差异结合；或用 MPRA 实验验证 allele-specific enhancer 活性 | Results 图 S2A；Discussion 局限性第 5 点 |
| 药物 concordance 打分仅用 FOXA1 一个 TF | 乳腺癌风险变异可能通过多个 TF 共同作用，单一 TF 可能过度简化 | 可能遗漏通过其他 TF 起作用的候选药物 | 扩展至多个 TF 敲低谱的联合打分 | Results "Drug candidate prioritization" 节 |
| 54% anti-correlation 的基准未明确 | 未报告随机药物在该指标下的分布宽度，54% 的效应量可能受选择阈值影响 | 若随机药物也有较高比例，则区分度有限 | 报告随机药物的 anti-correlation 分布，计算效应量（如 Cohen's d） | Results 图 4B-C |
| 未与现有药物重定位方法直接比较 | 未报告与 CMap 或其它 signature matching 方法的性能对比 | 无法判断该框架的增量价值 | 在相同数据集上运行 CMap 等基线方法，比较候选药物重叠率和富集度 | 未提供 |
| 8 个最终候选的「支持证据」强度不一 | 部分候选仅有 drug-gene 互作，缺乏转录组层面的独立验证 | 最终列表可能包含假阳性 | 对 8 个候选逐一报告 concordance 得分、anti-correlation 通路数和 drug-gene 证据类型 | 表 1 |
| 训练数据中 MCF7 的 enhancer 定义依赖 H3K27ac 峰 | H3K27ac 是 enhancer 的间接标记，可能遗漏不依赖 H3K27ac 的 enhancer | 可能影响 Δscore 计算的完整性 | 整合更多 enhancer 标记（如 H3K4me1, ATAC-seq 足迹） | Methods "Cell type-specific enhancer modeling" 节 |

## 12 结论正确解读

- **任务范围**：本文是**计算框架**，输出的是「候选药物列表」而非「临床可用治疗方案」。所有结论均为「computationally supported」而非「experimentally validated」。
- **Oracle/真值输入**：GWAS 汇总统计来自公开数据库，TF 敲低转录组来自 KnockTF 2.0（数据库注释），药物转录组来自 LINCS L1000。这些均为第三方数据，未做独立实验验证。
- **端到端状态**：框架是端到端的（从变异到药物），但每个环节的误差会累积。Δscore 的准确性依赖 enhancer 模型质量；TF 推断依赖 attribution 方法可靠性；药物打分依赖 LINCS 数据质量。
- **算力成本**：未报告具体训练时间或硬件需求。TREDNet 两阶段训练（4,560 图谱预训练 + 7 cell lines 微调）预计需要 GPU 集群，但具体成本未披露。
- **历史数据依赖**：GWAS 汇总统计、LINCS、KnockTF 均为历史积累数据，存在 cohort 偏差、平台效应等。
- **最难情形**：非编码变异效应微弱时（低 Δscore），筛选阈值可能遗漏真实调控变异；TF 敲低数据缺失的 cell type 无法分析。
- **群体/领域边界**：仅适用于有 matched 表观基因组、TF 敲低、药物转录组数据的 cell type-disease 对。目前仅 7 个 cell lines 满足条件。
- **不确定性**：所有 p 值均来自计算检验（Fisher's exact, permutation），不代表实验验证。FOXA1 与乳腺癌的关联有文献支持，但具体候选变异的调控效应未做实验确认。

**有边界的复述**：本文展示了一个在 MCF7 乳腺癌上下文中，从非编码 GWAS 变异出发，通过 enhancer 预测和 TF motif 归因推断 FOXA1 为关键调控因子，再通过 FOXA1 敲低转录组与药物转录组的 concordance 打分，从 6,605 个化合物中筛选出 63 个候选（含 18 个已批准药物），其中 8 个具有 drug-gene 互作证据。该框架的计算预测需实验验证，且适用范围受限于数据可及性。

## 13 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 计算预测需实验验证 | 候选变异和药物均为计算推断，未做实验确认 | 需要实验验证调控效应和治疗效果 | Discussion 局限性第 1 点 |
| 数据覆盖有限 | 仅 7 个 cell lines 有完整表观基因组数据 | 扩展至更多 cell types 和 tissues | Discussion 局限性第 2 点 |
| drug-gene 数据库不完整 | DGIdb 5.0 非 cell type 特异且可能遗漏 | 整合更全面的 cell type-specific 互作数据 | Discussion 局限性第 3 点 |
| 癌症细胞系局限 | 使用 cancer-derived cell lines 引入体细胞变异 | 使用非转化细胞或 patient-derived 模型 | Discussion 局限性第 4 点 |
| enhancer 模型预测的是概率而非直接活性 | Δscore 反映模型预测差异，非实验测量的 enhancer 活性 | 结合 STARR-seq 或 MPRA 等高通量实验验证 | Discussion 局限性第 5 点 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **TF 作为「变异-药物」枢纽的建模范式**：将 TF 敲低转录组作为中间表型，连接非编码变异与药物响应。可迁移到本课题：在 TF–DNA 结合机制研究中，可将 TF 结合预测（静态）与 TF 扰动转录组（动态）联合，构建「结合→功能」的完整模型。

2. **Allele-specific Δscore 的阈值策略**：同时要求「至少一个 allele 超过 FPR<10% 阈值」和「|Δscore| 在 top 10%」，兼顾绝对效应和相对效应。可迁移到 TF–DNA 结合研究：在筛选功能性 SNP 时，不应只看效应大小，还要看是否超过模型可靠预测的绝对阈值。

3. **Attribution-based motif discovery 的聚合策略**：在多个候选变异上聚合 DeepLIFT 信号，而非单变异分析。可迁移到本课题：当单个变异对 TF 结合的影响微弱时，在风险位点集合上聚合 attribution 信号可提高统计功效。

4. **Concordance 打分的 directional 设计**：KD_concordance = Mean(z_up) − Mean(z_down) 同时考虑上调和下调基因，比单一方向更稳健。可迁移到 TF–DNA 研究：评估 TF 靶基因集在药物处理中的变化时，应同时考虑双向变化而非仅看重叠。

5. **Cell type 特异性是硬约束**：7 个 cell lines 分别训练模型，而非共享模型。可迁移到本课题：TF–DNA 结合模型必须考虑 cell type 上下文，同一 TF 在不同细胞类型中的 motif 偏好可能不同。

6. **多源数据交叉验证**：转录组打分（CMap 风格）+ 通路 anti-correlation + drug-gene 互作三重验证。可迁移到本课题：TF–DNA 结合预测结果应通过 ChIP-seq、MPRA、敲低转录组等多层次数据交叉验证。

## 15 与已有知识连接

- **CMap/Connectivity Map 框架**：本文的 concordance 打分直接继承 CMap 的 signature matching 思想，但增加了 TF 敲低作为中间层。可连接：Subramanian et al. 2017 (LINCS L1000)。
- **DeepSEA/Enformer 等调控预测模型**：TREDNet 属于同一技术谱系，但采用两阶段训练策略。可连接：Zhou & Troyanskaya 2015; Avsec et al. 2021。
- **LDSC partitioned heritability**：本文使用标准 LDSC 流程，与 Finucane et al. 2015 一致。
- **FOXA1 在乳腺癌中的先锋因子功能**：本文的 FOXA1 发现与已知文献一致（Carroll et al. 2005; Hurtado et al. 2011），可作为外部验证。
- **TF 敲低数据库**：KnockTF 2.0 是较新的资源，可连接：Feng et al. 2020 (KnockTF v1)。
- **药物重定位的调控基因组学方法**：本文属于新兴方向，可连接：Chen et al. 2022 (regulatory variant-guided drug repurposing) 等早期尝试。
- **[Analysis] 候选连接**：本文框架可扩展到其他 TF–DNA 互作研究场景，如将 allele-specific 结合预测与 CRISPR 筛选或 MPRA 数据结合，验证 TF 结合变异的因果效应。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合特异性的多细胞类型迁移学习框架
   - **来源局限/观察**：本文 7 个 cell lines 分别训练模型，未利用跨细胞类型共享的 TF 结合规律
   - **核心假设**：TF 结合 motif 存在共享的序列偏好和细胞类型特异性的染色质上下文，迁移学习可提升低资源细胞类型的预测性能
   - **增量**：在 TREDNet 基础上引入 multi-task learning 或 meta-learning，共享 TF 结合先验
   - **初步方法**：用 ENCODE 多细胞类型数据预训练共享表示，对目标细胞类型微调；评估 Δscore 精度提升
   - **验证方式**：与本文 7 个 cell lines 的 AUROC/AUPRC 对比；用独立 ChIP-seq 验证 allele-specific 预测
   - **创新状态**：unverified

2. **候选名称**：TF 结合变异的因果效应验证——MPRA 与深度学习 Δscore 的系统比较
   - **来源局限/观察**：本文 Δscore 为纯计算预测，未用实验验证
   - **核心假设**：深度学习 Δscore 与 MPRA 测量的等位基因增强子活性差异显著相关
   - **增量**：建立计算预测与实验测量的定量映射，校准 Δscore 的生物学意义
   - **初步方法**：选取乳腺癌 GWAS 候选变异，设计 MPRA 文库，比较风险/保护 allele 的增强子活性；回归分析 Δscore 与实验效应的相关性
   - **验证方式**：相关系数、ROC-AUC；识别 Δscore 高但实验无效应的「假阳性」模式
   - **创新状态**：unverified

3. **候选名称**：多 TF 协同结合的 allele-specific 建模
   - **来源局限/观察**：本文聚焦单一 TF（FOXA1），但增强子功能由多 TF 协同决定
   - **核心假设**：风险变异通过改变多个 TF 的协同结合（而非单一 TF）影响增强子活性
   - **增量**：将 Δscore 分解为多 TF 贡献，识别协同结合的 TF 组合
   - **初步方法**：用 TF-MoDISco 输出的多 motif 共现模式，构建 TF-TF 协同评分；比较风险/保护 allele 的协同差异
   - **验证方式**：与 ChIP-seq 共结合数据比较；敲低协同 TF 后验证增强子活性变化
   - **创新状态**：unverified

4. **候选名称**：从 TF 结合到药物响应的生成式模型
   - **来源局限/观察**：本文用 concordance 打分排序药物，但未建模 TF 结合变化如何传播到药物响应
   - **核心假设**：TF 结合变异的调控效应可通过基因调控网络传播，生成式模型可预测药物响应的方向与幅度
   - **增量**：将 Δscore 与 TF 敲低转录组、药物转录组联合建模，学习「变异→网络→药物」的端到端映射
   - **初步方法**：用图神经网络或变分自编码器建模调控网络，以 Δscore 为输入预测药物转录响应
   - **验证方式**：与本文 63 个候选对比；用独立药物响应数据（如 GDSC）验证
   - **创新状态**：unverified

5. **候选名称**：非编码变异到 TF 结合特异性的物理模拟增强
   - **来源局限/观察**：本文纯深度学习，未利用物理模拟（MD/对接）的 TF–DNA 结合机制信息
   - **核心假设**：MD 模拟的 TF–DNA 结合自由能变化可增强深度学习的 allele-specific 预测
   - **增量**：将 MD 计算的结合自由能差异作为深度学习模型的辅助特征或约束
   - **初步方法**：对候选变异进行 TF–DNA 复合物的 MD 模拟，提取结合自由能特征；与 Δscore 联合训练
   - **验证方式**：与纯深度学习 Δscore 对比；用实验结合数据（如 HT-SELEX）验证
   - **创新状态**：unverified