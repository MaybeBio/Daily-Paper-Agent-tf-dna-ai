## 01 基本信息

- **标题**：Non-coding genetic variants underlying higher prostate cancer risk in men of African ancestry
- **作者**：Hannenhalli, Sridhar; Li, Shan; Fatema, Kaniz; Nidharshan, Sundarraj; Singh, Arashdeep; Rajagopal, Padma Sheila; Notani, Dimple; Takeda, David
- **单位**：未提供（据 NIH 基金号推断含美国国家癌症研究所 NCI 成员）
- **期刊/平台**：Research Square（预印本）
- **年份**：2024
- **论文类型**：预印本（研究论文）
- **领域**：前列腺癌遗传学；非编码调控变异；群体基因组学；深度学习
- **关键词**：prostate cancer, African ancestry, non-coding variants, enhancer, deep learning, transcription factor, polygenic risk score
- **DOI/ID**：10.21203/rs.3.rs-5485172/v1
- **代码**：未提供
- **数据**：LNCaP H3K27ac ChIP-seq（GEO: GSM1249448）、DHT 处理 DHS（GSM822388）、5 例欧裔 PrCa 患者 H3K27ac bam（来自文献 7）、胎儿前列腺表达（GSM614545）、FOXA1 ChIP-seq（GSE276748，本文产生）、PEGASUS 与 Ghana 队列基因型（dbGaP）、TCGA PrCa 临床与表达数据
- **阅读日期**：2025-01-15（示例）
- **在本课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」方向，核心贡献是将序列深度卷积网络（enhancer 模型）与滑动窗口策略结合，系统评估非编码 SNP 对增强子活性的影响，并进一步解析其通过干扰 FOXA1 等前列腺关键转录因子结合而影响 PrCa 风险的机制。对 TF–DNA 互作课题的可迁移点在于：单核苷酸分辨率的功能预测框架、TF 结合破坏的鉴定流程、以及跨群体等位基因频率差异与 TF 结合改变之间的关联分析范式。

## 02 一句话总结

本文开发了 ProSNP-DL——一个基于深度卷积网络的前列腺增强子活性预测模型，结合滑动窗口策略，在 491K 高 Fst SNP 中鉴定出约 2,000 个在非洲裔美国人中频率更高的增强子 SNP（eSNP），这些 eSNP 通过增强或减弱增强子活性、破坏 FOXA1/AR/HOX 等前列腺关键转录因子结合，以前列腺组织特异的方式影响 PrCa 风险，且可构建补充现有 GWAS 风险评分的多基因风险评分。

## 03 研究问题

- **具体问题**：非洲裔美国男性前列腺癌发病率和死亡率显著高于欧裔，但现有 GWAS 衍生的多基因风险评分（PRS）在跨群体中预测效果不佳，且 GWAS 变异本身不直接指向机制。本文要解决的核心问题是：**非编码调控 SNP（特别是增强子区域的 SNP）是否以及如何通过影响增强子活性和转录因子结合，导致非洲裔男性更高的 PrCa 风险？**
- **为什么重要**：PrCa 在非洲裔男性中发病率约为欧裔的 1.75 倍、亚裔的 3.18 倍，死亡率最高。理解群体间风险差异的分子机制，有助于开发更公平的跨群体风险预测工具，并揭示 PrCa 的调控机制。
- **现有方法不足**：GWAS 变异不直接指向机制；现有 PRS 跨群体迁移性差；对非编码调控变异在群体间差异中的作用缺乏系统评估。
- **精确研究问题**：Can a sequence-based deep learning model of prostate enhancers, combined with a sliding window strategy, identify non-coding SNPs with higher alternate allele frequency in African ancestry that functionally impact enhancer activity and disrupt key prostate transcription factor binding, thereby contributing to elevated PrCa risk?

## 04 背景与发展脉络

**注：以下脉络基于本文框架及引用文献，部分经外部核验（标注）。**

1. **GWAS 与 PRS 阶段**：大规模 GWAS 已鉴定数百个 PrCa 风险位点，并构建多祖先 PRS（如文献 8 的 PGS-545）。局限：变异不指向机制；跨群体预测精度下降（本文 Introduction）。
2. **单变异功能解析阶段**：如 8q24 位点 rs72725854（A>G/T），非洲裔特异变异通过引入 SPDEF 转录因子结合位点增强增强子活性，响应雄激素刺激上调 PCAT1、PVT1、c-Myc 表达（文献 17）。局限：逐个变异解析效率低，无法全基因组系统评估。
3. **深度学习增强子模型阶段**：序列深度模型（如本文引用的文献 18、41、42）可学习增强子序列编码，具有单核苷酸分辨率，能预测 SNP 对增强子活性的影响。局限：单 SNP 效应评估需考虑其在增强子中的位置。
4. **本文位置**：将深度学习增强子模型与滑动窗口策略结合（ProSNP-DL），实现全基因组规模、位置感知的非编码调控 SNP 功能预测，并进一步与群体遗传学（Fst 分层）、TF 结合 motif 分析、实验验证（ChIP-seq）整合，形成「预测→机制→验证→风险评分」的完整框架。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| GWAS 变异不指向机制 | 风险变异无法直接解释如何影响疾病 | GWAS 仅提供统计关联，不包含功能信息 | Introduction: "variants discovered via GWAS do not directly point to underlying mechanisms" |
| PRS 跨群体迁移性差 | 基于欧裔的 PRS 在非洲裔中预测效果不佳 | 群体间等位基因频率和连锁不平衡模式不同 | Introduction: "polygenic risk scores... do not address population-specific genetic mechanisms" |
| 非编码调控变异在群体差异中的作用未被系统评估 | 缺乏对增强子区域 SNP 的系统功能预测 | 缺乏单核苷酸分辨率的增强子模型与群体遗传学整合框架 | Introduction: "the role of non-coding regulatory polymorphisms in driving inter-ancestry variation in PrCa has not been sufficiently explored" |
| 单 SNP 效应依赖其在增强子中的位置 | 同一 SNP 在不同增强子位置效应不同 | 增强子活性对序列上下文敏感 | Results 图 2C 展示 rs72725854 效应随窗口位置变化；Methods "Effect size of a SNP" 滑动窗口策略 |
| 预测需要实验验证 | 计算预测的 TF 结合破坏需 ChIP-seq 验证 | 计算预测可能存在假阳性 | Results 图 5D-F 展示 FOXA1 ChIP-seq 验证 |

## 06 核心思想

### 1) 表面方法
ProSNP-DL 是一个两阶段框架：首先，用 LNCaP 细胞 H3K27ac ChIP-seq 峰（作为增强子代理）训练深度卷积网络，学习前列腺增强子的序列编码；然后，对每个候选 SNP，在以其为中心的 ±200bp 区域内以 20bp 步长滑动 2KB 窗口，计算每个窗口中参考/替代等位基因的模型分数差异（delta score），统计替代等位基因将中性序列转化为活性增强子（或反之）的窗口数，定义为 essential window number（EWN），以 EWN ≥ 5 作为 eSNP 的判定标准。

### 2) 核心洞察
- **位置感知的 SNP 效应评估**：SNP 对增强子活性的影响高度依赖其在增强子中的位置，滑动窗口策略能捕捉这种位置效应，避免单窗口评估的偏差。
- **群体分层与功能预测的整合**：通过 Fst 分层优先筛选群体间频率差异最大的 SNP，再以功能预测聚焦真正可能影响表型的位点，提高信噪比。
- **增强/减弱双向机制**：eSNP 分为"gained"（增强活性）和"lost"（减弱活性）两类，它们通过互补的机制（激活致癌通路 vs. 抑制肿瘤抑制通路）共同促进致癌。
- **TF 结合破坏作为核心中介机制**：eSNP 主要通过破坏 FOXA1、AR、HOX 等前列腺关键 TF 的结合来影响增强子活性，且 FOX 家族 TF 是核心中介。

### 3) 可能的普适教训 [Analysis]
- 深度学习模型的功能预测价值不仅在于预测精度，更在于其可解释性——通过 delta score 和 EWN 将黑箱输出转化为可操作的生物学假设。
- 群体遗传学（Fst）与功能基因组学（enhancer 模型）的整合，是解析群体间疾病风险差异的有效范式，可迁移到其他具有群体差异的复杂疾病。
- "gained/lost"双向分类框架为理解调控变异的异质性效应提供了简洁而有力的概念工具。

## 07 方法总览

- **输入**：
  - 训练数据：67,064 个 LNCaP H3K27ac 峰（阳性），10 折交叉验证的泛细胞类型 DHS 区域（阴性，不重叠 LNCaP H3K27ac 峰）
  - 候选 SNP：全基因组 84,802,133 个 SNP → 过滤为 10,171,946 个非编码常见 SNP（MAF ≥ 5% 在 EA 或 AA）→ 进一步筛选 top 5% Fst 的 491K SNP
- **输出**：2,407 个 AA-dominant eSNP（1,296 gained + 1,111 lost），及其对增强子活性的预测效应、受影响的 TF、靶基因和生物学通路
- **核心模块**：
  1. 深度卷积网络增强子模型（5 层卷积 + 全连接层，3,631,401 参数）
  2. 滑动窗口 SNP 效应评估（EWN 计算）
  3. Fst 群体分层筛选
  4. TF motif 富集分析（FIMO 扫描 JASPAR、CIS-BP、SwissRegulon、HOCOMOCO、UniPROBE）
  5. GREAT 功能富集分析
  6. CancerSEA 癌症功能状态富集分析
  7. 生存分析（TCGA Cox 回归）
  8. PRS 构建与验证（10 折交叉验证 EA 队列，独立 AA 队列验证）
- **反馈回路**：ChIP-seq 实验（FOXA1，LNCaP 与 MDA PCa 2B）验证预测的 TF 结合破坏
- **文字流程**：全基因组 SNP → 非编码常见 SNP 过滤 → Fst top 5% 筛选 → 对每个 SNP 滑动窗口计算 delta score → EWN ≥ 5 判定为 eSNP → 分为 gained/lost → TF motif 富集分析 → GREAT 通路富集 → CancerSEA 功能状态 → 靶基因生存分析 → PRS 构建与跨群体验证 → FOXA1 ChIP-seq 实验验证

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 深度卷积网络增强子模型 | 从序列预测增强子活性 | 提供单核苷酸分辨率的增强子功能预测 | 输入：1kb DNA 序列；输出：增强子活性分数 | 图 2B auROC=0.91；文献 18 同架构模型可预测 raQTL 等位基因效应 | 移除后无法进行全基因组规模的 SNP 功能预测 [预期] |
| 滑动窗口策略（EWN） | 评估 SNP 在不同增强子位置的效果 | SNP 效应依赖位置，单窗口评估有偏差 | 输入：SNP 及 ±200bp 区域；输出：EWN（0-21） | 图 2C 展示 rs72725854 位置依赖效应；Methods "Effect size of a SNP" | 移除后可能遗漏位置依赖的 SNP 效应 [预期] |
| Fst 群体分层筛选 | 优先选择群体间频率差异最大的 SNP | 聚焦可能解释群体风险差异的位点 | 输入：全基因组 SNP；输出：top 5% Fst 的 491K SNP | 图 S1A | 移除后候选 SNP 数量过大，信噪比降低 [预期] |
| TF motif 富集分析 | 鉴定 eSNP 破坏的 TF 结合位点 | 揭示 eSNP 影响增强子活性的分子机制 | 输入：eSNP 周围 100bp 序列；输出：富集的 TF motif | 图 5AB，FOX/HOX 家族富集；表 S1-4 | 移除后无法将 eSNP 与具体 TF 关联 [预期] |
| GREAT 功能富集 | 将 eSNP 关联到生物学通路 | 理解 eSNP 靶基因的功能意义 | 输入：eSNP 位置；输出：富集的 GO 术语 | 图 4AB | 移除后无法理解 eSNP 的生物学后果 [预期] |
| CancerSEA 富集 | 评估 eSNP 靶基因在癌症功能状态中的角色 | 连接 eSNP 到具体的致癌/抑癌过程 | 输入：靶基因列表；输出：14 种功能状态的富集分数 | 图 4C-E | 移除后无法区分 gained/lost eSNP 的功能差异 [预期] |
| FOXA1 ChIP-seq 验证 | 实验验证预测的 TF 结合破坏 | 提供预测的直接实验证据 | 输入：LNCaP 与 MDA PCa 2B 细胞；输出：FOXA1 结合峰 | 图 5D-F；rs10095018 案例 | 移除后预测缺乏实验支持 [预期] |
| PRS 构建与验证 | 评估 eSNP 的临床预测价值 | 将功能变异转化为风险预测工具 | 输入：eSNP 基因型；输出：PrCa 风险评分 | 图 6A-C | 移除后无法评估 eSNP 的临床应用价值 [预期] |

## 09 关键公式符号

**1. EWN（Essential Window Number）**

EWN = 窗口数{窗口 w ∈ W : (score_alt(w) − score_ref(w) 方向一致) 且 (score_alt(w) 或 score_ref(w) 跨越活性阈值)}

其中 W 为以 SNP 为中心的 ±200bp 区域内、步长 20bp 的 21 个 2kb 窗口。具体判定标准：
- gained eSNP：替代等位基因在 ≥85% 窗口中产生正 delta score，且至少在 5 个窗口中将中性序列（FPR < 0.01）转化为活性增强子
- lost eSNP：替代等位基因在 ≥85% 窗口中产生负 delta score，且至少在 5 个窗口中将活性增强子转化为中性序列

**2. Delta score**

Δ(w) = score_model(seq_alt, w) − score_model(seq_ref, w)

其中 score_model 为深度卷积网络的增强子活性预测分数。

**3. PRS（Polygenic Risk Score）**

PRS_i = Σ_j β_j × genotype_ij

其中 β_j 为多变量线性回归中 SNP j 的系数，genotype_ij 为个体 i 在 SNP j 的替代等位基因数（0, 1, 2）。

**4. Cox 回归（生存分析）**

h(t|X) = h₀(t) × exp(β₁×gene_expression + β₂×age)

用于评估 eSNP 靶基因表达与 PrCa 患者总生存期的关联。

## 10 实验设计与证据链

**数据集与资源**：
- 训练集：67,064 LNCaP H3K27ac 峰（阳性）；泛细胞类型 DHS 非重叠区域（阴性）
- 候选 SNP：全基因组 84,802,133 → 非编码常见 10,171,946 → top 5% Fst 491K
- 验证队列：PEGASUS（EA，4,599 例 + 2,841 对照）；Ghana（AA，474 例 + 458 对照）
- 实验数据：LNCaP（欧裔来源）与 MDA PCa 2B（非裔来源）细胞系 FOXA1 ChIP-seq（本文产生，GSE276748）
- 外部数据：5 例 EA PrCa 患者 H3K27ac bam（文献 7）、胎儿前列腺表达（GSM614545）、TCGA PrCa 临床与表达

**指标**：auROC（模型性能）、EWN（SNP 效应量）、富集 p 值（GREAT/CancerSEA）、AUC（PRS 区分度）、HR（生存分析）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 增强子模型训练与评估 | 模型能准确区分前列腺增强子与非增强子 | 10 折交叉验证，阳性 vs 阴性 | auROC = 0.91 | 模型具有高区分度，可用于 SNP 效应预测 | 模型性能不代表 SNP 效应预测的准确性 | 图 2B |
| rs72725854 案例分析 | 模型能复现已知 PrCa 风险 SNP 的增强子效应 | 参考 A vs 替代 T 等位基因 | 替代等位基因在多个窗口中增强增强子活性（EWN=5） | 模型能捕捉已知功能变异 | 单个案例不足以证明全基因组适用性 | 图 2C |
| eSNP 鉴定 | 高 Fst SNP 中存在影响增强子活性的功能性位点 | 491K 高 Fst SNP 经 ProSNP-DL 筛选 | 2,407 AA-dominant eSNP（1,296 gained + 1,111 lost） | 群体间频率差异 SNP 富含功能性增强子变异 | 预测的功能效应需实验验证 | 图 S1B |
| H3K27ac 等位基因不平衡 | eSNP 预测的增强子活性差异在实验数据中可检测 | eSNP 位点 vs 非 eSNP 位点，5 例 EA PrCa 患者 H3K27ac 数据 | eSNP 显示显著等位基因不平衡 | eSNP 预测与实验增强子活性一致 | 样本量小（5 例） | 图 3AB |
| GWAS 关联富集 | eSNP 富集于 PrCa GWAS 关联位点 | eSNP vs 非 eSNP 与 GWAS 信号的共定位 | AA-dominant eSNP 显著富集 PrCa GWAS 信号 | eSNP 与 PrCa 风险相关 | 富集不等于因果 | 图 3C |
| GREAT 功能富集 | gained/lost eSNP 靶基因富集于不同生物学通路 | gained vs lost vs 非 eSNP | gained：免疫抑制、端粒延长；lost：分化、凋亡 | eSNP 通过互补机制促进致癌 | 通路富集基于注释，需功能验证 | 图 4AB |
| TF motif 富集 | eSNP 破坏特定 TF 家族结合 | eSNP vs 非 eSNP 的 motif 频率 | FOX、HOX、AR 家族显著富集 | eSNP 通过破坏关键 TF 结合影响增强子活性 | motif 富集不等于实际 TF 结合改变 | 图 5AB，表 S1-4 |
| FOXA1 ChIP-seq 验证 | 预测的 FOXA1 结合破坏在实验中可检测 | LNCaP（EA）vs MDA PCa 2B（AA） | MDA PCa 2B 在 lost eSNP 处 FOXA1 结合降低；rs10095018 案例验证 | 预测的 TF 结合破坏得到实验支持 | 仅验证 FOXA1，其他 TF 未验证 | 图 5D-F |
| 生存分析 | eSNP 靶基因表达与 PrCa 患者生存相关 | 高表达 vs 低表达，Cox 回归控制年龄 | gained eSNP 靶基因高表达与更差生存相关 | eSNP 靶基因具有临床相关性 | 相关性不等于因果 | 图 3E |
| PRS 构建与验证 | eSNP 可构建有效 PrCa 风险评分 | eSNP-PRS vs 随机 SNP-PRS vs PGS-545 | eSNP-PRS 优于随机 SNP，与 PGS-545 互补 | eSNP 提供独立于 GWAS 的风险信息 | 需更大样本验证 | 图 6A-C |

## 11 结论正确解读

- **任务范围**：本文聚焦于**非编码 SNP 对前列腺增强子活性的影响**，不涉及编码变异、剪接变异或其他调控元件（如启动子、绝缘子）的系统评估。
- **oracle/真值输入**：增强子模型以 LNCaP H3K27ac ChIP-seq 峰为训练标签，这是增强子的代理标记而非直接功能测定；等位基因不平衡分析基于 5 例 EA 患者，样本量有限。
- **端到端状态**：从 SNP 预测到 TF 结合破坏的链条中，仅 FOXA1 得到 ChIP-seq 实验验证；AR、HOX 等 TF 的预测未直接验证。
- **算力成本**：未提供训练时间、GPU 配置等细节。
- **历史数据依赖**：模型依赖 LNCaP 细胞系（单一前列腺癌细胞系）的增强子注释，可能无法完全代表正常前列腺组织或其他遗传背景下的增强子景观。
- **模型依赖**：深度卷积网络架构与文献 18 相同，未与其他架构（如 Transformer、扩张卷积）比较。
- **最难情形**：模型对远离训练分布的区域（如非 DHS 区域、重复序列区域）的预测可靠性未知；对罕见变异（MAF < 5%）未评估。
- **群体边界**：eSNP 定义基于 AA vs EA 频率差异，不适用于其他祖先群体；PRS 验证仅在 EA 和 AA 队列中进行。
- **有边界的复述**：本文开发了一个前列腺增强子活性预测模型，在 Fst 筛选的 SNP 中鉴定出约 2,000 个 AA-dominant eSNP，这些 SNP 预测影响增强子活性、破坏 FOXA1 等关键 TF 结合，靶基因涉及免疫抑制和去分化等致癌通路，且可构建补充现有 GWAS 的 PRS。该结论受限于单一细胞系训练数据、有限的实验验证（仅 FOXA1）和特定的群体比较框架。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 预测需实验验证 | 计算预测的 eSNP 效应和 TF 结合破坏需进一步实验确认 | 未明确说明 | Discussion: "must be rigorously tested experimentally to establish their causality" |
| 模型可扩展性 | 方法可应用于其他癌症类型，但需相应组织的增强子数据 | 扩展到其他具有显著遗传基础的癌症类型 | Discussion: "this study can be extended to other cancer types with substantial hereditary basis, provided availability of the active enhancer data in appropriate cell or tissue type" |
| 非增强子调控变异未覆盖 | 方法聚焦增强子，未涉及剪接等其他非编码调控机制 | 可应用于其他非编码 SNP 类别（如剪接相关） | Discussion: "such an approach can be applied to other classes of non-coding SNPs, such as those affecting splicing" |
| 前列腺其他疾病 | eSNP 可能影响前列腺其他疾病 | 探索 eSNP 在前列腺其他疾病中的作用 | Discussion: "our deep learning model is trained on prostate enhancers, which can affect not just malignant transformation, i.e., PrCa, but other maladies of the prostate, which should be explored in a follow up study" |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 增强子模型以 H3K27ac 为标签 | H3K27ac 是增强子活性的相关标记而非直接功能读数；LNCaP 为雄激素依赖性细胞系，经 DHT 处理后的增强子景观可能不代表所有前列腺状态 | 模型学到的"增强子"可能偏向特定细胞状态和信号环境 | 用 STARR-seq 或 MPRA 等直接功能读数验证模型预测；在多个前列腺细胞系/类器官中测试模型泛化性 | Methods "Data Processing"；图 2B |
| Fst top 5% 筛选可能引入选择偏差 | 高 Fst SNP 可能富集于选择信号区域，而非 PrCa 相关区域；可能遗漏频率差异中等但功能重要的 SNP | 影响 eSNP 的全面性和代表性 | 使用不同 Fst 阈值进行敏感性分析；与全 SNP 扫描结果比较 | Methods "Data Processing"；图 S1A |
| 靶基因分配采用"近端基因"代理 | 增强子可通过三维基因组结构调控远距离基因，近端分配可能错误归因 | 影响通路富集和功能解释的准确性 | 使用 Hi-C 数据（本文已获取 LNCaP Hi-C）进行增强子-启动子配对验证 | Methods "Data Processing" 提及 Hi-C 数据 |
| FOXA1 ChIP-seq 验证仅两个细胞系 | LNCaP（EA）与 MDA PCa 2B（AA）的遗传背景差异可能混淆 eSNP 效应与细胞系固有差异 | 无法区分 eSNP 效应是群体特异还是细胞系特异 | 在多个 AA/EA 来源的细胞系中重复 ChIP-seq；使用等位基因特异性 ChIP-seq 分析 | 图 5D-F |
| PRS 提升幅度有限 | eSNP-PRS 仅"略微提升"（原文 "slightly improved"）PGS-545 的性能 | 临床实用性存疑 | 在更大、更多样化的队列中验证；评估 PRS 在不同年龄、临床分期亚组中的表现 | 图 6B |
| 生存分析基于 TCGA 数据 | TCGA PrCa 患者主要为局限性/中危患者，生存事件较少；基因表达与种系 SNP 的关联可能受肿瘤异质性影响 | 生存关联的稳健性存疑 | 在独立队列中重复生存分析；使用 SNP-表达 eQTL 共定位分析 | 图 3E |

## 14 学到什么

**Agent 提炼的知识候选**

1. **位置感知的 SNP 效应评估框架**：滑动窗口策略（EWN）解决了单 SNP 效应依赖其在增强子中位置的问题。可迁移到 TF–DNA 互作课题：评估 TF 结合位点内 SNP 时，可类似地滑动窗口计算不同位置对 TF 结合亲和力的影响，而非仅看 SNP 是否位于 motif 中心。

2. **"gained/lost"双向分类范式**：将调控变异分为增强/减弱两类，并分别关联到互补的生物学通路（激活致癌 vs. 抑制抑癌）。可迁移到 TF–DNA 互作：TF 结合 SNP 可分为"创建/增强结合"与"破坏/减弱结合"两类，它们可能通过不同的下游机制影响基因表达。

3. **群体分层（Fst）与功能预测的整合策略**：先以群体遗传学指标筛选候选，再以功能模型聚焦，提高信噪比。可迁移到 TF–DNA 互作：研究跨群体 TF 结合差异时，可先筛选 Fst 高 SNP，再预测其对 TF 结合的影响，最后用 ChIP-seq 验证。

4. **TF motif 富集分析流程**：用 FIMO 扫描多数据库 motif，比较 eSNP vs 非 eSNP 的 TF 家族富集。可迁移到 TF–DNA 互作：鉴定影响特定 TF 结合的 SNP 集合后，可用此流程系统鉴定受影响的 TF 家族。

5. **多层级验证策略**：计算预测 → 等位基因不平衡（H3K27ac）→ 细胞系 ChIP-seq → 生存分析 → PRS。可迁移到 TF–DNA 互作：TF 结合 SNP 的验证可从计算预测出发，经 ChIP-seq 验证结合差异，再关联到靶基因表达和临床结局。

6. **增强子模型的可解释性应用**：深度模型不仅用于预测，更通过 delta score 提供可解释的 SNP 效应量。可迁移到 TF–DNA 互作：基于深度学习的 TF 结合预测模型（如 DeepBind、BPNet）可类似地用于量化 SNP 对 TF 结合的影响。

7. **跨群体 TF 结合差异的机制假设**：同一 TF 在不同群体中可能因 SNP 频率差异而结合不同靶位点，导致基因调控差异。这是 TF–DNA 互作 × 群体基因组学交叉方向的重要假设。

## 15 与已有知识连接

- **深度增强子模型**：本文模型架构与作者前期工作（文献 18）相同，该工作已证明同架构模型在 HepG2 中可预测 raQTL 的等位基因效应。可连接至 DeepSEA、Basenji 等序列深度模型文献，比较不同模型在增强子预测上的表现。
- **rs72725854 案例**：连接至文献 15-17 对 8q24 位点非洲裔特异变异的系列研究，本文将其作为模型验证案例，展示了从单变异解析到全基因组扫描的扩展。
- **TF 破坏与癌症**：FOXA1 作为前列腺先锋因子、AR 共调节因子的作用已有大量文献（如文献 30、35），本文的 eSNP-TF 关联分析为这些已知 TF 在群体差异风险中的作用提供了新证据。
- **PRS 跨群体问题**：连接至多祖先 PRS 文献（如文献 8、14），本文提出了一种基于功能注释而非仅统计关联的 SNP 权重方案，是对现有 PRS 方法的补充。
- **等位基因不平衡分析**：连接至 ASChIP-seq、WASP 等方法学文献，本文用 BaalChIP 进行等位基因不平衡分析，是该方法在增强子 SNP 验证中的应用。
- **可迁移方向**：本文的「群体分层 → 功能预测 → TF 机制 → 风险评分」框架可迁移至其他具有群体差异的癌症类型（如三阴性乳腺癌在非裔女性中高发），以及 TF–DNA 互作的其他场景（如等位基因特异性结合、TF 协同结合）。

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：跨群体 TF 结合 SNP 的系统鉴定与功能验证
   - **来源局限/观察**：本文仅验证了 FOXA1 一个 TF 的结合破坏；AR、HOX 家族等预测未实验验证
   - **核心假设**：AA 群体中高频率的 eSNP 通过破坏多个前列腺关键 TF（不仅是 FOXA1）的协同结合，导致增强子活性改变
   - **初步方法**：对本文鉴定的 2,407 个 eSNP 进行多 TF ChIP-seq（AR、HOXB13、FOXA1 共结合位点）；用 MPRA 或 STARR-seq 验证增强子活性差异；分析 TF 协同结合 motif 的间距和方向性
   - **验证方式**：在多个 AA/EA 来源的前列腺细胞系中重复 ChIP-seq；比较 TF 结合差异与增强子活性差异的一致性
   - **创新状态**：unverified

2. **候选名称**：基于深度学习的 TF 结合 SNP 效应预测模型优化
   - **来源局限/观察**：本文增强子模型是通用的（预测增强子活性），非 TF 特异；对 TF 结合破坏的预测是间接的（通过 motif 富集）
   - **核心假设**：TF 特异的深度模型（如 BPNet 风格）能更准确预测 SNP 对 TF 结合的影响，优于通用增强子模型 + motif 分析的间接方法
   - **初步方法**：用 ChIP-nexus 或 ChIP-exo 数据训练 TF 特异结合模型；比较 TF 特异模型与通用增强子模型在预测 eSNP 效应上的性能；整合 TF 协同结合信息
   - **验证方式**：在独立 ChIP-seq 数据上评估预测的等位基因特异性结合；与本文 eSNP 集合比较重叠率
   - **创新状态**：unverified

3. **候选名称**：eSNP 对 TF 结合三维基因组结构的影响
   - **来源局限/观察**：本文使用 Hi-C 数据但仅用于靶基因分配；未分析 eSNP 对三维基因组结构的影响
   - **核心假设**：eSNP 不仅影响 TF 结合亲和力，还可能通过改变增强子-启动子相互作用频率来影响基因表达
   - **初步方法**：在 LNCaP 和 MDA PCa 2B 中进行 Hi-C 或 HiChIP；比较 eSNP 位点的染色质环锚定差异；整合 eSNP、TF 结合和染色质环数据构建调控网络
   - **验证方式**：CRISPR 干扰或碱基编辑验证 eSNP 对增强子-启动子相互作用和靶基因表达的影响
   - **创新状态**：unverified

4. **候选名称**：eSNP 在前列腺正常发育与癌变中的差异作用
   - **来源局限/观察**：本文聚焦 PrCa 风险，但 eSNP 可能在前列腺正常发育中也有作用；胎儿 vs 成人表达差异分析提示发育相关
   - **核心假设**：部分 eSNP 在前列腺发育中起正常调控作用，其风险效应仅在癌变过程中显现
   - **初步方法**：分析 eSNP 在胎儿 vs 成人前列腺组织中的增强子活性差异；比较 eSNP 靶基因在正常发育和癌变中的表达模式；用类器官模型验证
   - **验证方式**：在胎儿和成人前列腺类器官中进行 CRISPR 编辑和增强子活性检测
   - **创新状态**：unverified

5. **候选名称**：基于 eSNP 的跨群体 PrCa 风险预测模型
   - **来源局限/观察**：本文 eSNP-PRS 仅"略微提升"现有 PRS 性能，但 eSNP 具有功能注释优势
   - **核心假设**：将功能注释（eSNP 状态、TF 结合破坏、靶基因通路）整合到 PRS 构建中，可提高跨群体预测性能
   - **初步方法**：在更大多祖先队列中评估 eSNP-PRS；比较不同 PRS 构建策略（LDpred2、PRS-CS 等）在加入 eSNP 权重后的表现；评估 eSNP-PRS 在临床决策中的增量价值
   - **验证方式**：在独立 AA 和 EA 队列中验证；与现有临床风险因素（PSA、家族史）联合评估
   - **创新状态**：unverified