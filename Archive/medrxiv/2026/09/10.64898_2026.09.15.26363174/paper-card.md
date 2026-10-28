## 01 基本信息

- **标题**：Genomic foundation model-derived disruption profiling links somatic mutations to cancer biology and clinical outcomes
- **作者与单位**：Nayak A; Lee T; Agarwal V; Georgakopoulos-Soares I（单位未提供，通讯作者 Georgakopoulos-Soares 实验室，GitHub 显示为 Georgakopoulos-Soares-lab）
- **期刊/预印本平台**：medRxiv（预印本）
- **年份**：2026（预印本日期 2026-09-16）
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：癌症基因组学 × 基因组基础模型（sequence-to-function model）
- **关键词**：somatic mutations, cancer genomics, AlphaGenome, AlphaMissense, regulatory disruption, TCGA, survival analysis
- **DOI/arXiv 号**：10.64898/2026.09.15.26363174
- **代码**：https://github.com/Georgakopoulos-Soares-lab/cancer_non_coding
- **数据**：TCGA（dbGaP phs000178.v11.p8）、POG570（https://www.bcgsc.ca/downloads/POG570）、IntOGen、Cancer hotspots v2、TCGA-CDR
- **阅读日期**：2026-09-16
- **该文在课题方向中的位置**：本文使用基因组基础模型 AlphaGenome 对体细胞突变进行调控层面的 disruption 定量，与「TF–DNA 结合机制 × AI」课题的关联在于：其 disruption profiling 框架中显式包含 **transcription factor (TF) ChIP-seq** 这一模态，即用深度学习模型预测突变对 TF 结合的影响；同时其「将突变效应分解为蛋白层面（AlphaMissense）与调控层面（AlphaGenome）两个正交轴」的思路，可直接迁移到 TF–DNA 结合机制研究中区分「编码区突变改变 TF 蛋白本身」与「非编码区突变改变 TF 结合位点」两类效应。

---

## 02 一句话总结

本文使用基因组基础模型 AlphaGenome 对 TCGA 8,800 例患者、33 种癌症类型的体细胞突变进行七种调控模态（RNA-seq、CAGE、ATAC-seq、DNase-seq、组蛋白 ChIP-seq、TF ChIP-seq、剪接位点）的 disruption 定量，发现热点突变富集强蛋白效应而 passenger 突变携带更广泛的调控效应，且 passenger 来源的染色质可及性（ATAC）disruption 与总生存期相关，并在 POG570 治疗队列中显示治疗特异性预后关联。

---

## 03 研究问题

- **具体问题**：体细胞突变能否在单个基因水平上累积产生「部分、连续」的调控 disruption（而非传统的二元 driver/non-driver 分类），并且这种 disruption 是否具有生物学和临床意义？
- **为什么重要**：传统癌症基因组学聚焦于编码区热点突变和总突变负荷（TMB），忽略了非编码调控效应（染色质、转录调控、剪接）以及突变在基因内的累积效应；这些被忽略的效应可能携带独立的预后和治疗反应信息。
- **现有方法不足**：
  - 编码热点分析（Vogelstein 2013; Bailey 2018）只捕捉强蛋白效应，遗漏调控效应；
  - TMB 和突变特征分析（Alexandrov 2013）是聚合度量，无法定位到具体基因和调控模态；
  - 传统非编码注释依赖预定义的调控元件，无法直接量化突变对调控输出的影响。
- **精确的 Can 问题**：Can a genomic foundation model (AlphaGenome)-derived, gene-level regulatory disruption score, aggregated from somatic mutations, capture biological structure (tissue/cancer type/MSI status) and clinical outcomes (overall survival, treatment-specific survival) beyond tumor mutational burden and hotspot mutation status?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论的叙述，标注为「仅本文框架」；未逐一核对外部文献。

1. **阶段一：driver 基因/突变发现**（Vogelstein 2013; Bailey 2018）
   - 代表方法：突变显著性分析、热点检测
   - 优点：识别高置信 driver
   - 局限：二元分类，忽略累积和调控效应

2. **阶段二：聚合突变负荷分析**（Rizvi 2015; Alexandrov 2013; Sha 2020）
   - 代表方法：TMB、突变特征
   - 优点：与免疫治疗反应等临床结局关联
   - 局限：无法定位到基因和机制

3. **阶段三：序列到功能（sequence-to-function）深度学习模型**（Avsec 2021 Enformer; Linder 2025 Borzoi; Avsec 2026 AlphaGenome）
   - 代表方法：直接在 DNA 序列上预测染色质、表达、剪接等多模态调控输出
   - 优点：无需预定义调控元件，可对任意变异打分
   - 局限：此前未系统应用于癌症体细胞突变的基因水平聚合分析

4. **阶段四（本文位置）**：将 sequence-to-function 模型输出聚合为「基因-患者-模态」disruption profile，连接生物学结构（组织/癌症类型/MSI）与临床结局（生存、治疗反应），并系统对比蛋白层面（AlphaMissense）与调控层面（AlphaGenome）两个正交效应轴。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 传统分析忽略非编码调控效应 | 非热点、非编码突变被当作 passenger 丢弃 | 编码热点分析只关注蛋白效应；非编码注释依赖预定义元件 | 引言：Rheinbay 2020 等显示非编码 driver 难以通过传统方法识别 |
| TMB 等聚合度量丢失基因和机制信息 | TMB 无法告诉是哪个基因、哪个调控通路被扰动 | TMB 是基因组范围的计数，不区分基因和功能模态 | 引言：aggregate mutational burden analyses 的局限 |
| 蛋白效应与调控效应混为一谈 | 单一打分无法区分「改变 TF 蛋白」与「改变 TF 结合位点」两类机制 | 缺乏同时覆盖编码与非编码的正交评分框架 | Results 图 2：AlphaMissense 与 AlphaGenome 在热点 vs passenger 上呈现相反模式 |
| 突变累积效应未被量化 | 单个突变效应弱，但多个突变在同一基因内可能累积出功能后果 | 缺乏基因水平的聚合框架 | 引言：cumulative functional effects 未被单突变分析捕捉 |
| 调控 disruption 的临床相关性未知 | 不清楚调控 disruption 是否携带预后或治疗反应信息 | sequence-to-function 模型此前未与临床结局系统关联 | Results 图 5-6：ATAC disruption 与生存相关；POG570 治疗亚组关联 |

---

## 06 核心思想

### 1) 表面方法
- 用 AlphaGenome 对每个体细胞突变计算 7 种调控模态的「突变 vs 参考」差异（Mutated − Wild-type），在基因-患者层面聚合为 disruption profile；
- 用 AlphaMissense 计算蛋白层面致病性；
- 在 TCGA 8,800 例/33 癌型上构建 patient-gene-modality 矩阵，进行 t-SNE 聚类、MSI 分类、Cox 生存分析；
- 在 POG570 独立队列中按治疗类别分层做生存关联。

### 2) 核心洞察
- **热点突变与 passenger 突变在两个评分轴上呈「镜像」分布**：热点突变富集强 AlphaMissense（蛋白）效应，而 passenger 突变携带更大的 AlphaGenome（调控）效应——说明「passenger」并非功能中性，只是其效应落在传统方法盲区（调控层面）。
- **调控 disruption 是模态特异的**：同一基因在不同组织中由不同调控模态主导（ATAC vs RNA-seq vs splice-site vs TF ChIP），提示 disruption 必须按模态分解而非合并为单一分数。
- **passenger 来源的调控 disruption 独立于 TMB 携带预后信号**：ATAC disruption 在无热点突变的患者中仍与生存相关，说明「累积的部分 disruption」具有临床意义。

### 3) 可能的普适教训 [Analysis]
- **对 TF–DNA 结合研究**：本文的「双轴正交评分」（蛋白效应 vs 调控效应）可直接类比为「TF 蛋白本身的突变效应 vs TF 结合位点（motif/cis-element）的突变效应」——两者需要独立量化，不能合并。
- **对 AI 方法设计**：sequence-to-function 模型的输出是多模态的，聚合时应保留模态维度（而非取平均），因为不同模态可能携带正交的生物学信号。
- **对实验验证**：本文的 disruption profile 是纯计算预测，未做湿实验验证（作者在讨论中承认），提示此类框架需要 paired 功能基因组学数据（如同一患者的 ATAC/RNA 数据）来校准。

---

## 07 方法总览

- **输入**：
  - TCGA 体细胞突变（8,800 患者，33 癌型）
  - POG570 全基因组测序 + 治疗注释（570 样本）
  - 癌症基因集（IntOGen）、热点注释（Cancer hotspots v2）
- **输出**：
  - 患者-基因-模态 disruption profile（7 个 AlphaGenome 模态 + AlphaMissense）
  - 聚类结构（t-SNE）、MSI 分类性能（AUPRC/AUROC）、Cox 生存模型 HR
- **核心模块**：
  1. **变异效应打分**：AlphaGenome（7 模态，100 kb 输入窗口，L2_DIFF 分数）+ AlphaMissense（蛋白致病性）
  2. **基因-患者聚合**：按模态取中位数，TMB 调整（除以 log(1+total mutations)），基因长度回归残差化，z-score 标准化
  3. **生物学结构验证**：t-SNE + 伪 F 统计量（组织/癌型/MSI 聚类）
  4. **生存分析**：Cox PH 模型，按基因-模态对，TMB 残差化后中位数分组，年龄/癌型协变量
  5. **治疗亚组分析**：POG570 内按治疗类别分层 Cox
- **训练**：AlphaGenome 和 AlphaMissense 为预训练模型（本文未重新训练）；本文训练的是 logistic 回归分类器（MSI）和 Cox 模型（生存）
- **反馈回路**：无显式迭代反馈；分析流程为单向 pipeline
- **假设**：
  - AlphaGenome 预测的调控输出可近似真实调控状态（未用同一患者 paired 数据验证）
  - 突变效应可加性聚合（中位数汇总）
  - TMB 和基因长度是主要混杂因素（通过残差化控制）
- **文字流程**：体细胞突变 → AlphaGenome/AlphaMissense 打分 → 基因-患者-模态聚合 → TMB/基因长度调整 → 标准化 → t-SNE 聚类 / MSI 分类 / Cox 生存 / 治疗亚组

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| AlphaGenome 变异打分 | 对每个突变计算 7 种调控模态的预测效应 | 捕获非编码/调控层面的 disruption | 输入：突变 + 100 kb 序列窗口；输出：各模态 L2_DIFF | Results 图 1A-B：NRAS/PTEN 案例显示突变序列与参考序列的预测差异 | 移除后无调控 disruption 度量，整个分析框架失效（核心模块） |
| AlphaMissense 蛋白致病性打分 | 量化编码突变的蛋白效应 | 提供与调控效应正交的蛋白效应轴 | 输入：错义突变；输出：致病性分数 | Results 图 2A-B：热点 vs passenger 在 AlphaMissense 上呈显著差异 | 移除后无法对比蛋白 vs 调控效应，图 2 的核心对比消失 |
| 基因-患者聚合（中位数 + TMB/长度调整） | 将变异级分数聚合为基因级 disruption | 单突变效应弱，需累积；控制 TMB 和基因长度混杂 | 输入：变异级分数；输出：patient-gene-modality 矩阵 | Methods 节：TMB 调整、基因长度回归残差化、z-score 标准化 | 移除后无法进行基因级生存分析；不调整 TMB 则 MSI/生存信号可能被混杂（预期效应 [Analysis]） |
| t-SNE 聚类 + 伪 F 统计 | 验证 disruption profile 是否捕获生物学结构 | 证明 disruption 非噪声，携带组织/癌型/MSI 信息 | 输入：patient-level disruption 矩阵；输出：2D 嵌入 + 聚类统计 | Results 图 4A-C：组织/癌型/MSI 分离显著 | 移除后无法建立 disruption 的生物学有效性（预期效应 [Analysis]） |
| MSI 分类（logistic 回归） | 比较 TMB-only vs AlphaGenome vs 残差化特征 | 证明 disruption 携带 TMB 之外的 MSI 信息 | 输入：TMB 和/或 AlphaGenome 特征；输出：AUPRC/AUROC | Results 图 4D：全特征 AUPRC 0.99/0.98/1.00 vs TMB 0.66-0.96 | 移除后无法量化 disruption 相对 TMB 的增量价值 |
| Cox 生存模型（基因-模态对） | 评估 disruption 与总生存的关联 | 建立临床相关性 | 输入：disruption 分组 + 协变量；输出：HR/95%CI/p 值 | Results 图 5A-B：ATAC 24/25 基因高 disruption HR 更高（q=3.1e-6） | 移除后无法支持「passenger disruption 有预后意义」的核心主张 |
| POG570 治疗亚组 Cox | 评估 disruption 在治疗亚组中的预后价值 | 测试治疗特异性关联 | 输入：治疗类别分层 + disruption 分数；输出：HR/p 值 | Results 图 6A-B：RB1/TCF7L2 等基因在特定治疗组中显著 | 移除后无法支持「治疗特异性」主张；样本量小，结果需谨慎（作者标注 exploratory） |

---

## 09 关键公式符号

> 本文为应用型论文，未给出显式数学公式。以下为从 Methods 描述中可重建的隐式公式。

1. **变异级 disruption 分数**（AlphaGenome）：
   \[
   \Delta_{v,m} = \text{L2\_DIFF}_m(\text{seq}_{\text{mut}}, \text{seq}_{\text{ref}})
   \]
   - \(\Delta_{v,m}\)：变异 \(v\) 在模态 \(m\) 的 disruption 分数
   - \(\text{L2\_DIFF}_m\)：AlphaGenome 对模态 \(m\) 的 L2 差异度量
   - \(\text{seq}_{\text{mut}}, \text{seq}_{\text{ref}}\)：突变序列与参考序列（100 kb 窗口）

2. **基因-患者聚合**（中位数）：
   \[
   D_{p,g,m} = \text{median}_{v \in V_{p,g}} \left( \Delta_{v,m} \right)
   \]
   - \(D_{p,g,m}\)：患者 \(p\)、基因 \(g\)、模态 \(m\) 的聚合 disruption
   - \(V_{p,g}\)：患者 \(p\) 在基因 \(g\) 内的体细胞突变集合

3. **TMB 调整**：
   \[
   D^{\text{adj}}_{p,g,m} = \frac{D_{p,g,m}}{\log(1 + \text{total\_mutations}_p)}
   \]

4. **基因长度残差化**（线性回归）：
   \[
   D^{\text{adj}}_{p,g,m} = \alpha + \beta \cdot \log_{10}(\text{gene\_length}_g) + \epsilon
   \]
   - 残差 \(\hat{\epsilon}\) 作为最终调整分数

5. **z-score 标准化**：
   \[
   Z_{p,g,m} = \frac{\hat{\epsilon}_{p,g,m} - \mu_{g,m}}{\sigma_{g,m}}
   \]

6. **Cox 比例风险模型**：
   \[
   h(t \mid X) = h_0(t) \exp(\beta_1 I_{\text{high disruption}} + \sum_j \gamma_j I_{\text{cancer type}_j})
   \]
   - \(I_{\text{high disruption}}\)：高 disruption 组指示变量（中位数分组）
   - 治疗亚组分析中额外包含治疗类别协变量

---

## 10 实验设计与证据链

### 数据集与规模
| 数据集 | 规模 | 用途 |
|---|---|---|
| TCGA | 8,800 患者，33 癌型 | 主分析：disruption profiling、聚类、MSI、生存 |
| POG570 | 570 全基因组肿瘤样本（治疗注释） | 独立验证：治疗特异性生存 |
| 基因集 | IntOGen 癌症基因集；泛癌 31 基因（≥1% 突变率）；癌型特异 top 30 | 基因选择 |
| 热点注释 | Cancer hotspots v2 | 热点 vs passenger 分类 |

### 指标
- 变异水平：AlphaMissense 分数、AlphaGenome 7 模态 L2_DIFF
- 聚类：伪 F 统计量（t-SNE 分组分离度）
- 分类：AUPRC、AUROC（MSI 分类）
- 生存：HR、95% CI、Wald p 值、Benjamini-Hochberg q 值

### 基线/对比
- MSI 分类：TMB-only（M1）vs TMB-残差化 AlphaGenome（M2）vs 全 AlphaGenome（M3）
- 生存：零 disruption 组为参照；高 vs 低 disruption 对比；热点突变患者单独分组

### 评测协议
- 生存分析限定无热点突变患者（确保信号来自 passenger）
- TMB 残差化 + 基因长度调整 + 年龄/癌型协变量
- 治疗亚组：POG570 内按治疗类别分层，仅保留 ≥10 患者、≥3 事件的亚组

### 证据链表格
| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 热点 vs passenger 变异水平对比 | 热点富集蛋白效应，passenger 富集调控效应 | AlphaMissense vs AlphaGenome，按热点状态分组 | 热点 AlphaMissense 显著更高；passenger AlphaGenome 效应更大 | 两类突变在两个评分轴上呈镜像分布 | 未做功能验证，纯计算预测 | Results 图 2A-C |
| t-SNE 聚类 | disruption profile 捕获组织/癌型结构 | 8,800 患者按 disruption 特征嵌入 | 组织/癌型分离显著（伪 F 高，p=0.001） | disruption 携带生物学结构信息 | 聚类可能部分由突变谱驱动，未做置换检验 [Analysis] | Results 图 4A-B |
| MSI 分类 | disruption 携带 TMB 之外的信息 | M1（TMB）vs M2（残差化）vs M3（全特征） | M3 AUPRC 0.99/0.98/1.00（COAD/UCEC/STAD）；M2 在 COAD/UCEC 仍高（0.82/0.93） | disruption 超越 TMB 的判别力 | STAD 中残差化特征判别力下降，提示该癌型中信号与 TMB 耦合 | Results 图 4D |
| 无热点患者生存分析 | passenger disruption 与总生存相关 | 高 vs 低 disruption，零 disruption 为参照 | ATAC 模态 24/25 基因高 disruption HR 更高（q=3.1e-6） | 染色质可及性 disruption 携带预后信号 | 未做多基因联合模型；HR 差异小（mean 0.0996） | Results 图 5A-B |
| POG570 治疗亚组 | disruption 与治疗特异性结局相关 | 按治疗类别分层 Cox | RB1（DNA 损伤剂 HR=1.36；DNA 合成抑制剂 HR=1.46）；TCF7L2（DNA 损伤剂 HR=1.97）等 | 治疗特异性关联存在 | 样本量小，多重比较未充分控制，作者标注 exploratory | Results 图 6A-B |

---

## 11 结论正确解读

- **任务范围**：本文是「关联分析」（association study），不是「因果验证」或「预测模型」。disruption 分数是 AlphaGenome 的计算预测，未用同一患者的 paired 功能数据（如 RNA-seq/ATAC-seq）验证。
- **oracle/真值输入**：AlphaGenome 和 AlphaMissense 均为预训练模型，其输出作为「真值」使用；无湿实验校准。
- **端到端状态**：非端到端。pipeline 为「预训练模型打分 → 统计聚合 → 关联分析」，各环节独立。
- **算力成本**：未报告。AlphaGenome 为 100 kb 窗口推理，8,800 患者 × 31 基因 × 多模态的计算成本未披露。
- **历史数据依赖**：完全依赖 TCGA 和 POG570 的历史数据；无前瞻性验证。
- **模型依赖**：结论强依赖 AlphaGenome 的预测质量。若 AlphaGenome 对非编码调控的预测存在系统性偏差，则所有下游结论受影响。
- **最难情形**：STAD 中 TMB 残差化后 MSI 判别力下降；ChIP-TF 模态生存信号方向反转（低 disruption 组 HR 更高），提示不同模态的生物学含义不同。
- **群体/领域边界**：泛癌分析以 TCGA 为主（欧美人群为主）；POG570 为加拿大队列。治疗亚组仅限乳腺癌和结直肠癌。
- **不确定性**：所有生存关联的 HR 差异较小（mean paired HR difference 0.0996），效应量有限；治疗亚组样本量小，置信区间宽。
- **有边界的复述**：在 TCGA 和 POG570 数据范围内，AlphaGenome 预测的调控 disruption（特别是染色质可及性）在无热点突变的患者中与总生存相关，且该信号在 TMB 残差化后仍存在；但该结论是计算预测层面的关联，未经功能验证，效应量有限，不能推广为临床预测工具。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 缺乏功能验证 | disruption 分数为计算预测，未与同一肿瘤的功能数据（表达、染色质）对照 | 「validating predicted disruption against functional and expression data from the same tumours」 | Discussion 末段 |
| 治疗亚组样本量小 | POG570 中按治疗类别分层后样本有限 | 「extending the treatment-response analysis to larger annotated cohorts」 | Discussion 末段 |
| 关联而非预测 | 未建立正式的预测模型，仅报告关联 | 「testing whether disruption scores add predictive value in formal, prospectively defined survival and response models」 | Discussion 末段 |
| 结果初步 | 作者将治疗相关发现标注为 exploratory | 需在更大队列中验证 | Results 图 6 上下文 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| AlphaGenome 预测未经验证 | 若模型对非编码调控的预测有系统性偏差，所有 disruption 结论可能为模型伪影 | 核心方法依赖未校准的预测 | 用同一患者的 paired ATAC/RNA 数据比较预测 vs 实测 disruption；或与 CRISPR 扰动实验对照 | Methods 节未提及 paired 验证 |
| 「passenger」定义依赖热点数据库 | 非热点突变可能包含未注释的 driver；热点数据库本身不完备 | 若 passenger 组混入 driver，生存信号可能部分由已知 driver 驱动 | 使用功能评分（如 CADD、PrimateAI）分层 passenger；或排除已知 driver 基因重复分析 | Results 图 2 的 passenger 定义 |
| 中位数分组二分法 | 将连续 disruption 分数中位数二分可能丢失剂量-反应信息，且分组阈值依赖样本构成 | 可能高估或低估真实关联强度 | 使用连续分数做限制性立方样条或时变 Cox 模型 | Results 图 5 方法描述 |
| 多重比较未充分控制 | 31 基因 × 4 模态 × 多治疗组的大量 Cox 检验，仅用 BH 校正 | 部分显著结果可能为假阳性 | 报告所有检验总数；使用置换检验或西太平洋 FDR 控制 | Methods 节仅提及 BH 校正 |
| t-SNE 聚类伪 F 统计的稳健性 | t-SNE 对超参数敏感，伪 F 统计非标准聚类验证指标 | 聚类分离可能受嵌入参数影响 | 使用 UMAP 或 PCA 交叉验证；报告不同 perplexity 下的稳定性 | Results 图 4 方法描述 |
| 治疗亚组中 ChIP-TF 方向反转 | 作者未充分解释为何 TF 结合 disruption 与生存方向与其他模态相反 | 可能反映 TF 结合丢失在某些情境下有利（如抑癌 TF 失活），但也可能是混杂 | 按 TF 功能类别（激活/抑制）分层分析；检查与已知通路的一致性 | Results 图 5B 的 ChIP-TF 结果 |
| 效应量小 | mean paired HR difference 0.0996 的临床意义有限 | 统计显著 ≠ 临床相关 | 报告 NNT 或风险差；在独立队列中验证效应量 | Results 图 5A 数值 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **双轴正交评分框架**：将突变效应分解为「蛋白层面（AlphaMissense）」与「调控层面（AlphaGenome）」两个正交轴，可揭示传统单一评分遗漏的结构。**迁移到 TF–DNA 互作**：对 TF 相关突变，应同时量化「TF 蛋白本身的错义效应」与「TF 结合位点（cis-element/motif）的调控效应」，两者可能呈镜像分布。

2. **模态特异性 disruption**：同一基因在不同组织中由不同调控模态主导（ATAC vs RNA-seq vs splice-site vs TF ChIP），聚合时保留模态维度而非合并。**迁移**：研究 TF–DNA 结合时，应分别报告「结合强度（ChIP）」「可及性（ATAC）」「表达（RNA）」三个层次的 disruption，而非单一结合分数。

3. **TMB 残差化是必要的混杂控制**：任何突变衍生的特征都必须先去除与总突变负荷的线性关联，否则观察到的信号可能只是突变负荷的代理。**迁移**：在 TF–DNA 结合预测中，需控制突变负荷和基因长度，避免将「高突变基因」误判为「高 disruption 基因」。

4. **passenger 并非中性**：非热点突变的累积调控效应可携带独立的预后信号。**迁移**：在 TF–DNA 结合机制研究中，不应只关注已知 driver 突变；低频、分散的调控突变可能通过累积效应影响 TF 结合网络。

5. **治疗亚组分析的价值与风险**：按治疗类别分层可发现全人群中被掩盖的信号，但小样本 + 多重比较使结果只能作为假设生成。**迁移**：TF–DNA 结合预测模型在药物反应研究中的应用，应预设治疗分层假设，而非事后挖掘。

6. **可解释性优先于预测性能**：本文未追求预测精度，而是用 disruption profile 做生物学结构验证（聚类、GSEA）和关联分析。**迁移**：TF–DNA 结合 AI 模型应优先输出可解释的模态分解（结合、可及性、表达），而非单一黑盒分数。

---

## 15 与已有知识连接

- **AlphaGenome / AlphaMissense 家族**：本文使用的 AlphaGenome 与 AlphaMissense 同属 DeepMind 系列模型。AlphaMissense（Cheng et al. 2023）为蛋白错义突变致病性预测；AlphaGenome（Avsec et al. 2026）为基因组调控预测。两者联合使用构成「编码 + 非编码」双覆盖，与课题方向中「TF 蛋白 vs TF 结合位点」的二分法直接对应。
- **Enformer / Borzoi 谱系**：AlphaGenome 属于 sequence-to-function 模型谱系（Enformer: Avsec 2021; Borzoi: Linder 2025）。这些模型直接以 DNA 序列预测调控输出，是 TF–DNA 结合机制研究中「motif → 结合 → 表达」链条的计算基础。
- **癌症基因组学经典框架**：driver 发现（Vogelstein 2013; Bailey 2018）、TMB/突变特征（Alexandrov 2013; Rizvi 2015）是本文的对照基线。本文的「连续 disruption」观点与「二元 driver」框架形成张力，可类比 TF–DNA 研究中「强效应 master regulator vs 弱效应多位点协同」的争论。
- **累积效应与部分功能丧失**：本文引用的 Nayak et al. 2026 提出基因内突变累积的连续功能丧失模型，与 TF–DNA 结合中「部分结合位点亲和力下降」的定量观点一致。
- **MSI 与突变负荷**：MSI-H 与 TMB 的已知关联（本文图 4D 验证）是「突变衍生特征必须控制 TMB」的经典案例，可迁移到 TF–DNA 结合预测的混杂控制。
- **生存分析中的 TMB 残差化**：与免疫治疗反应研究中「TMB 之外的突变质量特征」文献一致（如 neoantigen quality 研究），本文将其扩展到调控 disruption 维度。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：TF–DNA 结合 disruption 的双轴正交评分框架
- **名称**：TF-centric dual-axis disruption profiling（TF-DADP）
- **来源局限/观察**：本文对「任意基因」做蛋白 vs 调控双轴评分，但未聚焦 TF 家族；TF 是唯一同时作为「蛋白效应靶点」和「DNA 结合 reader」的基因类别，双轴框架对其尤为关键。
- **核心假设**：TF 基因的体细胞突变可被分解为「改变 TF 蛋白结构/功能」与「改变 TF 结合位点（其自身启动子/增强子）」两个正交轴，且两轴对癌症表型的贡献可分离。
- **初步方法**：对全部 ~1,600 个人类 TF，用 AlphaMissense 计算错义突变蛋白效应；用 AlphaGenome 计算 TF 基因座 cis-regulatory 区域的 disruption；构建 TF 特异双轴 profile，比较两轴与表达改变、下游靶基因网络扰动的关联。
- **验证方式**：TCGA 中 TF 双轴分数与 TF 表达、靶基因集活性的关联；在 POG570 中检验治疗特异性预后。
- **创新状态**：unverified（框架迁移自本文，但聚焦 TF 类别为新增）

### 候选 2：模态特异性 TF 结合 disruption 与 master regulator 识别
- **名称**：Modality-resolved TF binding disruption for master regulator discovery
- **来源局限/观察**：本文发现 ATAC disruption 预后信号最强，但未深入 TF 结合层面；TF–DNA 结合是染色质可及性的上游决定因素。
- **核心假设**：在无热点突变的肿瘤中，分散的调控突变通过累积效应破坏特定 TF 的结合 motif，从而产生「弱化但广泛」的 master regulator 失活。
- **初步方法**：用 AlphaGenome 的 TF ChIP-seq 模态输出，对每个 TF 的 motif 区域计算突变诱导的结合分数变化；聚合为「TF 结合 disruption 分数」；与下游靶基因表达、患者生存关联。
- **验证方式**：与已知 master regulator 数据库（如 ARACNe 推断的 regulon）交叉验证；在细胞系中用 CRISPR 扰动候选 TF 结合位点验证预测。
- **创新状态**：unverified

### 候选 3：TMB 残差化的 TF 结合 disruption 作为免疫治疗反应预测因子
- **名称**：TMB-residualized TF binding disruption for immunotherapy response
- **来源局限/观察**：本文的 TMB 残差化框架成功分离了 disruption 与突变负荷的混杂；但未应用于免疫治疗反应（仅有生存）。
- **核心假设**：TMB 残差化的 TF 结合 disruption 可预测免疫检查点抑制剂反应，且独立于 TMB 和 neoantigen 负荷。
- **初步方法**：在免疫治疗队列（如 Liu 2019、Riaz 2017 等公开数据）中计算 TF 结合 disruption 分数，与 TMB、TIDE、MSI 等已知标志物比较。
- **验证方式**：多队列 ROC/AUC 比较；与肿瘤免疫微环境（CIBERSORT 推断的免疫浸润）关联。
- **创新状态**：unverified（框架迁移自本文，应用场景为新增）

### 候选 4：TF–DNA 结合 disruption 的模态主导性图谱
- **名称**：Pan-cancer TF binding disruption modality dominance atlas
- **来源局限/观察**：本文的 dominant-modality map（图 3C）显示不同基因-组织对由不同模态主导，但未扩展到 TF 结合层面。
- **核心假设**：不同癌症类型中，TF 结合 disruption 的主导模态（可及性 vs 直接结合 vs 剪接）不同，反映组织特异的调控架构。
- **初步方法**：对 TCGA 33 癌型，计算每个 TF 的 4 模态 disruption 主导性；构建「TF × 癌型 × 主导模态」三维图谱；与组织特异的 enhancer 架构、TF 表达水平关联。
- **验证方式**：与 ENCODE 组织特异 TF 结合数据交叉验证；与已知组织特异 master regulator 一致性检验。
- **创新状态**：unverified

### 候选 5：从 disruption profile 到 TF–DNA 结合机制的物理模拟引导
- **名称**：Disruption-guided MD simulation of TF–DNA binding
- **来源局限/观察**：本文的 disruption 分数是纯统计关联，未提供分子机制解释；TF–DNA 结合机制需要物理层面的验证。
- **核心假设**：AlphaGenome 预测的高 disruption 突变在 TF–DNA 复合物的 MD 模拟中显示结合自由能显著变化，且与 disruption 分数相关。
- **初步方法**：选取高 disruption 的 TF 结合位点突变，用 AlphaFold3 或 RoseTTAFold 构建 TF–DNA 复合物结构，用 MD（如 GROMACS/AMBER）计算结合自由能变化（MM-PBSA）；与 AlphaGenome disruption 分数回归。
- **验证方式**：与实验测定的结合亲和力数据（如 SELEX、HT-SELEX）比较；检验 disruption 分数与 ΔΔG 的相关性。
- **创新状态**：unverified（跨 AI 预测与物理模拟的桥接为新增）