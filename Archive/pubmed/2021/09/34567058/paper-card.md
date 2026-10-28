## 01 基本信息

- **标题**：Systematic Evaluation of DNA Sequence Variations on in vivo Transcription Factor Binding Affinity
- **作者与单位**：Jin, Yutong; Jiang, Jiahui; Wang, Ruixuan; Qin, Zhaohui S（Emory University，Rollins School of Public Health）
- **期刊/预印本平台**：Frontiers in Genetics
- **年份**：2021-09-28
- **论文类型**：方法评估/系统性调查研究（Method evaluation / Survey）
- **领域**：非编码变异功能注释；TF–DNA 结合亲和力预测；调控基因组学
- **关键词**：SNV、转录因子结合、PWM、gkm-SVM、deltaSVM、ChIP-seq、GWAS
- **DOI/arXiv 号**：10.3389/fgene.2021.667866
- **代码**：https://github.com/YutongJ/TFBS
- **数据**：ENCODE ChIP-seq 数据（18 个 TF，GM12878 细胞系为主）、JASPAR/Factorbook PWM、dbSNP153 Common SNPs
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「TF–DNA 结合机制 × 序列变异功能预测」方向，核心贡献在于系统比较 PWM 与 gkm-SVM/deltaSVM 两种方法在量化 SNV 对体内 TF 结合亲和力影响时的一致性，并指出仅约 20% 位于推定结合位点内的 SNV 具有显著功能影响。对课题的启示在于：PWM 作为经典结合模型存在位点独立性假设缺陷，而基于 ChIP-seq 的序列学习方法（gkm-SVM）可作为互补或替代方案，尤其适用于 motif 边界模糊或较短弱 motif 的 TF。

---

## 02 一句话总结

本文用 gkm-SVM（基于 ChIP-seq 训练的序列核方法）计算 deltaSVM 分数，系统评估 18 个 TF 的推定结合位点内 SNV 对体内结合亲和力的影响，发现仅约 20% 的此类 SNV 具有显著影响，且 deltaSVM 与 PWM 分数在单个位点层面一致性有限。

---

## 03 研究问题

- **具体问题**：位于推定 TF 结合位点内的 SNV 是否真的会影响体内 TF 结合？PWM 分数变化与基于 ChIP-seq 的 deltaSVM 分数变化是否一致？
- **为什么重要**：GWAS 发现的大多数变异位于非编码区，常见注释策略是将落在 PWM 扫描出的推定结合位点内的 SNV 直接标记为"功能性"。若该策略高估了 SNV 的功能影响，将导致大量假阳性注释，误导下游功能实验与疾病机制研究。
- **现有方法为何不足**：PWM 假设各位置独立（零阶马尔可夫模型），无法捕捉位置间依赖；且 PWM 仅反映序列偏好，不直接度量体内结合（受染色质可及性、竞争性结合、辅因子等影响）。传统注释方法（如 RegulomeDB）仅判断 SNV 是否落在 PWM 位点内，不量化影响程度。
- **精确研究问题**：Can deltaSVM scores (derived from ChIP-seq-trained gkm-SVM) provide a more reliable quantification of SNV impact on in vivo TF binding than PWM-based probability differences, and to what extent do the two methods agree?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引用与论述整理，属「经外部核验」的领域发展脉络，但阶段划分与评价框架为本文作者视角。

| 阶段 | 代表性方法 | 优点 | 局限 |
|------|-----------|------|------|
| 经典 motif 建模 | PWM（Stormo et al., 1982）；MEME、HOMER 等 motif 发现工具 | 简单、可解释、计算高效 | 假设位置独立；无法捕捉高阶依赖；仅反映序列偏好而非体内结合 |
| 数据库资源 | TRANSFAC、JASPAR、Factorbook、HOCOMOCO、CIS-BP | 提供大量 curated motif | 设计目标是表征 motif 模式，而非量化变异影响 |
| 变异功能预测 | RegulomeDB、CADD、FunSeq 等 | 整合多源注释 | 对 TF 结合位点内变异的判断多为二元（有/无影响），缺乏定量 |
| 序列核方法 | gkm-SVM（Ghandi et al., 2014）；deltaSVM（Lee et al., 2015） | 捕捉序列上下文依赖；直接基于 ChIP-seq 体内数据训练；可量化变异影响 | 依赖 ChIP-seq 数据质量与细胞系特异性；黑箱性质较强 |
| 深度学习（后续发展） | DeepBind、DeepSEA、Basenji 等 | 可捕捉更长程依赖与复杂模式 | 本文未涉及，但同属"序列→功能"预测范式 |

**本文主张的位置**：在 PWM 与 gkm-SVM 之间进行系统比较，检验两者在 SNV 功能影响评估上的一致性，并建议将 deltaSVM 作为 PWM 的补充工具用于非编码变异注释。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| PWM 位点内 SNV 被过度注释为功能性 | 传统方法将所有落在推定结合位点内的 SNV 视为影响 TF 结合 | PWM 仅反映序列偏好，不度量体内结合；许多位点位置保守性低 | Results 节：仅约 20% SNV 具有显著 deltaSVM 影响 |
| PWM 与体内结合度量不一致 | 高 PWM 分数的 10-mer 不一定有高 SVM 权重，反之亦然 | PWM 假设位置独立；motif 边界模糊；ChIP-seq 反映体内竞争性结合 | Results 节图 1、Supplementary Figure 2：相关性范围 −0.081 至 0.787 |
| 短/弱 motif 的 PWM 评估不可靠 | JUND、MAX、POU5F1、USF1 等高 SVM 权重 10-mer 的 PWM 分数不突出 | motif 长度短、信息含量低，PWM 难以准确评分 | Results 节：Supplementary Figure 2 讨论 |
| 缺乏统一的变异影响量化标准 | 不同方法给出不同结论，难以判断 SNV 是否"功能性" | 缺乏体内结合亲和力的直接实验数据作为金标准 | Discussion 节：作者承认无实验数据验证 |
| 细胞系特异性问题 | SVM 权重在不同细胞系间有差异 | TF 结合具有细胞类型特异性 | Methods 节：作者仅用 GM12878 训练，但验证了 CTCF 在三种细胞系间约 80% 重叠 |

---

## 06 核心思想

### 1) 表面方法
- 对 18 个 TF，使用 ENCODE ChIP-seq 数据（GM12878 细胞系）训练 gkm-SVM，获得所有可能 10-mer 的 SVM 权重。
- 对每个推定 PWM 结合位点内的 SNV，计算 deltaSVM 分数（变异前后 10-mer SVM 权重差异之和）与 delta-PWM 分数（变异前后 PWM 概率差异）。
- 以随机非位点序列的 deltaSVM 分布建立经验阈值（2.5% 与 97.5% 分位），判断 SNV 是否"显著影响"结合。
- 对 11 种疾病的 GWAS 关联变异，统计落在推定位点内但 deltaSVM 不显著的"不一致 SNV"比例。

### 2) 核心洞察
- **PWM 与 SVM 度量的不一致性是系统性的**：两者相关性从 −0.081 到 0.787 不等，说明对某些 TF（如 BCL11A、STAT1）PWM 分数几乎无法预测体内结合强度。
- **大多数位点内 SNV 影响有限**：约 80% 的位点内 SNV 的 deltaSVM 分数未超过经验阈值，说明"落在 motif 内"不等于"影响结合"。
- **序列上下文比单点保守性更重要**：gkm-SVM 通过 gapped k-mer 捕捉位置间依赖，能识别 PWM 无法反映的上下文效应。

### 3) 可能的普适教训 [Analysis]
- **单一序列特征不足以刻画 TF–DNA 结合**：PWM 的独立性假设在体内场景下过于简化，任何基于 PWM 的变异注释都应谨慎解读。
- **数据驱动的序列表示（如 gkm-SVM 的 k-mer 特征）可作为 motif 模型的补充**：尤其对短 motif、弱保守位点、或结合受上下文调控的 TF。
- **"显著性"需要经验零分布**：本文用随机序列建立 deltaSVM 阈值，这种置换/零分布思路可迁移到其他变异效应预测任务中。

---

## 07 方法总览

- **输入**：
  - 18 个 TF 的 ENCODE ChIP-seq peak 区域（正集）与基因组随机区域（负集，由 genNullSeqs 生成，匹配 GC 含量、重复比例、长度）
  - 对应 TF 的 PWM（来自 JASPAR/Factorbook）
  - dbSNP153 Common SNPs（用于疾病关联变异分析）
- **输出**：
  - 每个 10-mer 的 SVM 权重
  - 每个位点内 SNV 的 deltaSVM 分数与 delta-PWM 分数
  - SNV 是否"显著影响"结合的二元判断
- **核心模块**：
  1. gkm-SVM 训练（正负集构建、核计算、权重估计）
  2. PWM 扫描与位点识别
  3. deltaSVM 与 delta-PWM 计算
  4. 经验阈值建立（随机序列零分布）
  5. 疾病关联变异注释与不一致性统计
- **训练**：gkm-SVM 使用 R 包 gkmSVM，默认参数（未提供具体超参数细节）
- **反馈回路**：无显式迭代优化；方法为一次性训练+评估
- **假设**：
  - ChIP-seq peak 区域代表体内 TF 结合位点
  - 10-mer 窗口足以捕捉 TF 结合的决定性序列特征
  - 随机序列的 deltaSVM 分布可作为显著性零分布

**文字流程**：
1. 从 ENCODE 获取 18 个 TF 的 ChIP-seq peak 区域 → 作为正集
2. 用 genNullSeqs 生成匹配的负集序列 → 训练 gkm-SVM → 获得所有 10-mer 的 SVM 权重
3. 用 PWM 扫描基因组 → 识别推定结合位点 → 对位点内每个 SNV 计算 delta-PWM 与 deltaSVM
4. 从非位点随机序列计算 deltaSVM 经验分布 → 确定显著性阈值
5. 对 11 种疾病的 GWAS 变异 → 统计落在位点内但 deltaSVM 不显著的"不一致 SNV"比例

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| gkm-SVM 训练 | 从 ChIP-seq 数据学习序列→结合潜力映射 | 提供不依赖 PWM 的体内结合度量 | 输入：peak/非 peak 序列；输出：10-mer SVM 权重 | Methods 节；Results 节相关性分析 | 无法计算 deltaSVM，整个变异影响评估框架失效 |
| PWM 扫描与位点识别 | 识别推定 TF 结合位点 | 定义 SNV 的"位点内"归属 | 输入：基因组序列 + PWM；输出：位点坐标与分数 | Methods 节 | 无法界定分析范围；但作者已证明该范围本身可能不可靠 |
| deltaSVM 计算 | 量化 SNV 对结合潜力的影响 | 核心创新：将变异效应转化为 SVM 权重差 | 输入：参考/变异 10-mer 权重；输出：deltaSVM 分数 | Methods 节；Results 节图 1 | 无法判断 SNV 是否显著影响结合 |
| 经验阈值建立 | 定义"显著影响"的零分布 | 避免任意 cutoff | 输入：随机序列 deltaSVM；输出：2.5%/97.5% 分位阈值 | Methods 节 | 无法区分真实影响与随机波动 |
| 疾病关联变异注释 | 评估 GWAS 变异的功能影响 | 将方法应用于实际问题 | 输入：疾病 SNV 列表 + 位点注释；输出：不一致 SNV 比例 | Results 节图 2、Supplementary Table S5 | 无法评估方法在真实疾病变异中的表现 |

**消融效应区分**：本文未做模块消融实验。上述"移除后影响"为 [Analysis] 基于方法逻辑的推断，非作者实测。

---

## 09 关键公式符号

**1. PWM 分数（相对熵形式）**：

$$D(a_1, a_2, \ldots, a_L) = \sum_{i=1}^{L} \sum_{j \in \{A,C,G,T\}} P_{i,j} \log_2 \frac{P_{i,j}}{P_j}$$

- $a_i$：第 i 个位置的核苷酸（A/C/G/T）
- $L$：motif 长度
- $P_{i,j}$：位置 i 处核苷酸 j 的概率（来自 PWM）
- $P_j$：背景概率（本文固定为 0.25）
- 用途：衡量序列与 PWM 的匹配程度；值越大表示越符合 motif 模型
- 直觉：相对熵度量了 PWM 分布与背景分布的差异，反映该位点序列的信息量

**2. deltaSVM 分数**（引用自 Lee et al., 2015，本文使用）：

$$\text{deltaSVM} = \sum_{k \in K} w_k \cdot [I(k \in S_{alt}) - I(k \in S_{ref})]$$

- $K$：所有可能的 gapped k-mer 集合
- $w_k$：k-mer k 的 SVM 权重
- $S_{ref}$ / $S_{alt}$：参考/变异等位基因所在 10-mer 覆盖的 k-mer 集合
- 用途：量化 SNV 对序列结合潜力的影响
- 直觉：将变异效应分解为所有受影响的 k-mer 权重变化之和

**3. delta-PWM 分数**（本文定义）：

$$\text{delta-PWM} = D(\text{ref motif}) - D(\text{alt motif})$$

- 用途：PWM 框架下的变异影响度量
- 直觉：变异前后 motif 匹配度的差异

---

## 10 实验设计与证据链

### 数据集与资源
- **TF 数量**：18 个（BCL11A, CTCF, EGR1, GABPA, JUN, JUND, MAX, NANOG, POU5F1, RAD21, RFX5, SIX5, SRF, STAT1, TCF12, USF1, USF2, YY1）
- **ChIP-seq 数据**：ENCODE 联盟，GM12878 细胞系（训练 SVM）；K562 细胞系（用于 CTCF/JUND 验证）
- **PWM 来源**：JASPAR 和 Factorbook
- **变异数据**：dbSNP153 Common SNPs
- **疾病数据**：PheGenI 门户，11 种疾病（AD、哮喘、乳腺癌、心血管疾病、儿童发育障碍、结直肠癌、克罗恩病、肺癌、肥胖、银屑病、2型糖尿病），p 值阈值 10⁻⁶
- **代码**：GitHub (https://github.com/YutongJ/TFBS)

### 评测协议
- **相关性分析**：对每个 TF，取 top 1,000 PWM 分数最高的 10-mer，计算其 SVM 权重与 PWM 分数的相关性（Pearson）
- **跨细胞系验证**：CTCF 在 GM12878、K562、H1 三种细胞系的 SVM 权重 top 1,000/500 重叠率
- **显著性阈值**：从随机非位点序列计算 deltaSVM 经验分布，取 2.5%/97.5% 分位
- **不一致 SNV 定义**：落在 PWM 推定位点内但 deltaSVM 不显著的 SNV

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| PWM vs SVM 相关性 | 两种度量在 top 10-mer 上的一致性 | 18 个 TF，各取 top 1,000 10-mer | 相关性范围 −0.081 至 0.787，多数为中等正相关 | 两种方法部分一致，但存在显著分歧 | 不能断言哪种方法更准确（无实验金标准） | Results 节图 1、Supplementary Figure 1 |
| 跨细胞系 SVM 权重稳定性 | SVM 权重是否细胞系特异 | CTCF 在 GM12878、K562、H1 的 top 1,000/500 重叠 | top 1,000 约 80% 重叠，top 500 约 84% | CTCF 的 SVM 权重在三种细胞系间较稳定 | 不能推广到所有 TF 或所有细胞系 | Methods 节 |
| 位点内 SNV 显著性比例 | PWM 位点内 SNV 是否大多影响结合 | 18 个 TF 全部推定位点内常见 SNV | 仅约 20% SNV 的 deltaSVM 超过显著性阈值 | 大多数位点内 SNV 对结合影响有限 | 不能排除阈值选择或 10-mer 窗口的影响 | Results 节 |
| 疾病关联 SNV 不一致率 | PWM 注释与 deltaSVM 的一致性 | 11 种疾病 GWAS 变异 | 平均约 80% 不一致率 | PWM 单独使用可能高估 SNV 功能影响 | 不一致 SNV 可能仍通过其他机制（如染色质）影响功能 | Results 节图 2、Supplementary Table S5 |

---

## 11 结论正确解读

- **任务范围**：仅评估 SNV 对 TF 结合亲和力的影响，不涉及基因表达、表型或疾病因果性。
- **oracle/真值输入**：ChIP-seq peak 作为体内结合的代理标签；无体外结合亲和力实验数据作为直接验证。
- **端到端状态**：非端到端流程；gkm-SVM 训练与变异效应评估为两阶段独立过程。
- **算力成本**：未报告具体训练时间或计算资源。
- **历史数据依赖**：依赖 ENCODE ChIP-seq 数据质量与 peak calling 结果；依赖 dbSNP 的变异频率注释。
- **模型依赖**：gkm-SVM 的 k-mer 长度、gap 参数等超参数未报告；PWM 来源（JASPAR vs Factorbook）可能影响结果。
- **最难情形**：短 motif（如 JUND、MAX）、弱保守位点、以及结合受染色质状态调控的 TF。
- **群体/领域边界**：仅限 18 个 TF、GM12878 细胞系、常见 SNV（dbSNP）；不覆盖罕见变异、其他细胞类型、其他物种。
- **不确定性**：无置信区间或重复实验报告；经验阈值基于随机序列，但随机序列的生成参数可能影响阈值。

**有边界的复述**：在 18 个 TF、GM12878 细胞系、dbSNP 常见变异的范围内，基于 ChIP-seq 训练的 gkm-SVM 所计算的 deltaSVM 分数显示，约 80% 位于 PWM 推定结合位点内的 SNV 对体内结合无显著影响，且 PWM 与 SVM 两种度量在单个位点层面的一致性有限（相关性 −0.081 至 0.787）。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 缺乏实验验证 | 无体外或体内结合亲和力实验数据来验证 SVM 预测 | 考虑利用染色质可及性数据或 DNA 甲基化数据评估预测准确性 | Discussion 节 |
| 细胞系特异性 | SVM 权重基于 GM12878 训练，可能不适用于其他细胞类型 | 未明确提及，但暗示需在更多细胞系中验证 | Methods 节 |
| 仅考虑序列信息 | 未纳入染色质状态、DNA 甲基化、辅因子等表观遗传因素 | 建议整合表观基因组数据以提高预测准确性 | Discussion 节 |
| 10-mer 窗口限制 | 固定 10-mer 窗口可能无法捕捉更长距离的调控上下文 | 未明确提及 | Methods 节（隐含） |

**作者提及的相关约束**（非正式局限）：作者明确表示"不认为 SVM 权重是金标准"，且 PWM 与 SVM 的不一致可能源于两者度量不同层面的结合特性。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 仅用 top 1,000 10-mer 计算相关性 | 可能高估或低估真实相关性；top 选择引入选择偏差 | 相关性结论依赖采样策略 | 用全部 10-mer 或随机采样计算相关性 | Results 节方法描述 |
| 经验阈值基于随机序列 | 随机序列的 GC 含量、重复比例匹配可能不充分；未报告 genNullSeqs 参数 | 显著性判断依赖零分布质量 | 用不同随机序列生成策略重复阈值估计 | Methods 节 |
| 未报告 gkm-SVM 超参数 | k-mer 长度、gap 数、C 值等影响模型性能 | 结果可复现性存疑 | 检查 GitHub 代码或联系作者 | Methods 节 |
| "不一致 SNV"可能反映真实生物学 | PWM 位点内但 deltaSVM 不显著的 SNV 可能通过影响辅因子招募、染色质构象等机制发挥作用 | 不能简单将不一致解释为 PWM 的失败 | 用 ATAC-seq、Hi-C 等多组学数据交叉验证 | Results 节讨论 |
| 疾病关联 SNV 分析中 LD 扩展可能引入噪声 | 5kb 窗口内的 LD 伙伴可能并非真正的功能变异 | 可能稀释真实信号 | 用 fine-mapping 或 eQTL 共定位方法精确定位 | Methods 节 |
| 未比较其他深度学习方法 | 仅与 PWM 比较，未与 DeepBind、DeepSEA 等比较 | 无法判断 gkm-SVM 在当代方法中的相对位置 | 在相同数据集上运行多种方法比较 | 全文未提及 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **PWM 位点内变异的"功能性"需重新审视**：本文证据表明约 80% 的位点内 SNV 对体内结合无显著影响。在 TF–DNA 互作研究中，不应仅凭 PWM 位点重叠来注释变异功能，应结合 ChIP-seq 衍生的序列模型或实验验证。

2. **gkm-SVM/deltaSVM 作为 PWM 的互补工具**：gkm-SVM 通过 gapped k-mer 捕捉位置间依赖，对短 motif 或弱保守位点的评估可能优于 PWM。可迁移到课题中：对目标 TF，若 PWM 预测与 ChIP-seq 数据不一致，可训练 gkm-SVM 作为替代评分函数。

3. **经验零分布建立显著性阈值**：本文用随机非位点序列的 deltaSVM 分布确定 2.5%/97.5% 分位阈值。此思路可迁移到任何变异效应预测任务中，避免任意 cutoff 带来的偏差。

4. **跨细胞系验证的必要性**：CTCF 在三种细胞系间约 80% 的 top 10-mer 重叠，说明部分 TF 的结合序列偏好具有细胞类型稳定性，但作者也警告不能推广。在课题中，若使用特定细胞系的 ChIP-seq 数据训练模型，需评估其泛化性。

5. **PWM 与序列学习方法的低相关性本身是信息**：对某些 TF（如 BCL11A、STAT1），PWM 分数几乎无法预测 SVM 权重，提示这些 TF 的结合可能高度依赖上下文或辅因子。在课题中，可据此筛选出"PWM 不适用"的 TF，优先使用更复杂的模型。

6. **方法选择应基于 motif 特性**：短 motif（如 JUND、MAX）的 PWM 评估不可靠，而 gkm-SVM 表现更好。在课题中，可根据 motif 长度、信息含量选择评分方法。

---

## 15 与已有知识连接

- **PWM 模型**：本文直接基于 Stormo et al. (1982) 的 PWM 框架，并指出其零阶马尔可夫假设的局限。与课题中常用的 motif 扫描工具（FIMO、HOMER）直接相关。
- **gkm-SVM**：Ghandi et al. (2014) 提出，Lee et al. (2015) 扩展为 deltaSVM。本文是该方法在 TF 结合变异评估中的系统应用。与课题中基于 k-mer 或 gapped k-mer 的序列表示方法（如 kmer-SVM、gkm-filter）直接相关。
- **ENCODE 资源**：本文使用的 ChIP-seq 数据来自 ENCODE 联盟，与课题中常用的 ENCODE TF ChIP-seq 数据集一致。
- **非编码变异功能预测**：本文与 RegulomeDB (Boyle et al., 2012)、CADD (Kircher et al., 2014) 等方法形成对比，强调定量评估而非二元注释。与课题中变异效应预测任务（如用 DeepSEA、Basenji 预测变异对染色质状态的影响）互补。
- **可迁移方向**：本文的"不一致 SNV"分析框架可迁移到课题中，用于评估不同模型（PWM vs 深度学习 vs 物理模拟）在变异效应预测上的一致性；其经验阈值方法也可用于 MD 模拟或对接打分中判断"显著"结构变化。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

**候选 1：基于深度学习的 TF 结合变异效应预测与 PWM 的系统比较**
- **来源局限/观察**：本文仅比较了 gkm-SVM 与 PWM，未涉及深度学习模型（如 DeepBind、DeepSEA、Basenji）。
- **核心假设**：深度学习模型在预测 SNV 对 TF 结合影响上优于 gkm-SVM 和 PWM，尤其在长程依赖和复杂上下文场景。
- **初步方法**：对 18 个 TF（或扩展至更多 TF），用 ENCODE ChIP-seq 数据训练 DeepBind/DeepSEA 类模型，计算变异前后的预测分数变化，与 deltaSVM 和 delta-PWM 比较；用体外结合实验（如 HT-SELEX、PBMs）数据作为验证集。
- **验证方式**：AUC/PRC 比较；在已知功能性变异（如 eQTL、fine-mapped GWAS 变异）上的富集分析。
- **创新状态**：partially checked（深度学习在 TF 结合预测上已有大量工作，但与 gkm-SVM/PWM 的系统比较在 2021 年后有部分工作，需查新）。

**候选 2：整合染色质可及性数据的 TF 结合变异效应预测**
- **来源局限/观察**：作者明确承认未纳入表观遗传因素，并建议未来整合。
- **核心假设**：将 ATAC-seq/DNase-seq 可及性数据作为特征，可显著提高 SNV 对体内 TF 结合影响预测的准确性。
- **初步方法**：在 gkm-SVM 或深度学习框架中，将序列特征与细胞类型特异的可及性特征（如 ATAC-seq 信号、核小体定位）融合；在多种细胞类型中验证。
- **验证方式**：与本文的 deltaSVM 结果比较；用 CRISPR 扰动或报告基因实验验证 top 预测。
- **创新状态**：unverified（已有部分工作将可及性纳入预测，但针对变异效应的系统评估较少）。

**候选 3：用 MD 模拟验证 deltaSVM 预测的高影响 SNV**
- **来源局限/观察**：本文的 deltaSVM 预测缺乏实验验证，且未涉及结构层面的机制解释。
- **核心假设**：deltaSVM 分数高的 SNV 在 MD 模拟中表现出更大的结合自由能变化或构象扰动。
- **初步方法**：选取 deltaSVM 预测为"显著影响"和"无影响"的 SNV 各若干，对含 SNV 的 TF–DNA 复合物进行 MD 模拟（如 100-500 ns），计算结合自由能差（MM-PBSA/MM-GBSA）和关键接触变化。
- **验证方式**：deltaSVM 分数与 MD 自由能变化的相关性；高影响 SNV 是否更可能位于蛋白-DNA 直接接触界面。
- **创新状态**：unverified（MD 与序列预测方法的结合在 TF–DNA 领域有探索，但针对本文具体框架的系统验证未见报道）。

**候选 4：TF 结合位点内 SNV 的"功能层级"注释框架**
- **来源局限/观察**：本文仅用二元阈值判断 SNV 是否显著，未区分影响程度或机制类型。
- **核心假设**：SNV 对 TF 结合的影响可分为"核心接触破坏"、"辅助接触微调"、"不影响结合但影响辅因子招募"等层级，需要多方法联合注释。
- **初步方法**：整合 PWM 分数变化、deltaSVM 分数、结构信息（如 PDB 中 TF–DNA 复合物的接触残基）、表观遗传数据，构建多层级注释框架；在已知疾病变异上验证。
- **验证方式**：与实验数据（如 CRISPR 筛选、报告基因）比较；层级间的生物学功能差异分析。
- **创新状态**：unverified（类似框架在部分工具中已有雏形，但针对 TF 结合变异的系统层级化注释较少）。