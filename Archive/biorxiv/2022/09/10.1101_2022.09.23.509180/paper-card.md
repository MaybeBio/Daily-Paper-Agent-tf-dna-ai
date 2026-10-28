## 01 基本信息

- **标题**：Statistical learning quantifies transposable element-mediated cis-regulation
- **作者与单位**：Pulver C; Grün D; Duc J; Sheppard S; Planet E; de Fondeville R; Pontis J; Trono D（EPFL，瑞士洛桑联邦理工学院）
- **期刊/预印本平台**：bioRxiv
- **年份**：2022-09-23
- **论文类型**：预印本（方法学 + 应用研究）
- **领域**：计算基因组学 / 统计学习 / 转座子调控
- **关键词**：transposable elements (TEs), cis-regulatory elements (CREs), gene regulatory networks (GRNs), statistical learning, RNA-seq, transcription factors (TFs)
- **DOI/arXiv 号**：10.1101/2022.09.23.509180
- **代码**：https://renkulab.io/gitlab/crates
- **数据**：GEO GSE117395, GSE136763, GSE208403；DDBJ DRA006296；ZENODO 10.5281/zenodo.6707955, 10.5281/zenodo.6769794, 10.5281/zenodo.6816370
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文提出一种统计学习模型 craTEs，从 RNA-seq 数据中估计 TE 亚家族对邻近基因的顺式调控活性，属于「TF–DNA 互作 × 统计学习」交叉方向。其核心假设是 TE 亚家族作为 TF 结合平台（TF  docking platforms）调控邻近基因表达，与 TF–DNA 结合机制直接相关，但方法本身不涉及物理模拟或结构预测，而是基于序列计数和线性回归的统计推断。

---

## 02 一句话总结

本文提出 craTEs 模型，将基因表达差异建模为邻近 TE 亚家族拷贝数的线性组合，仅用 RNA-seq 数据即可估计 TE 亚家族的顺式调控活性，并证明该模型能识别已知的 TE 调控事件（如 LTR5-Hs/SVA 在 naïve hESC 中的增强子活性），且比基于差异表达基因富集的方法更灵敏。

---

## 03 研究问题

- **具体问题**：能否仅从蛋白质编码基因的表达变化中，定量推断哪些 TE 亚家族在顺式调控这些基因？TE 亚家族的调控活性有多大、是否显著？
- **为什么重要**：TE 占人类基因组一半以上，许多 TE 序列充当增强子/启动子等 CRE，但传统方法依赖表观基因组学（如 ChIP-seq、ATAC-seq）来鉴定 TE 调控元件，成本高且难以大规模应用。若能仅从 RNA-seq 推断 TE 调控活性，将极大促进 TE 调控研究。
- **现有方法不足**：基于差异表达基因富集的方法（如 Fisher 精确检验）需要预先设定 DE 阈值，丢失了效应量信息，统计功效低；且无法区分同一亚家族内功能性与非功能性拷贝。
- **精确的 Can 问题**：Can a linear model of gene expression as a function of nearby TE subfamily copy numbers accurately identify TE subfamilies with genuine cis-regulatory activity from RNA-seq data alone?

---

## 04 背景与发展脉络

**脉络标注**：以下脉络基于本文 Introduction 和 Discussion 的叙述，属于「仅本文框架」，未经外部系统核验。

1. **阶段一：TE 作为 CRE 的个案研究**（~2000s–2010s）
   - 代表性方法：报告基因实验、ChIP-seq 鉴定 TE 上的增强子标记（如 H3K27ac）
   - 优点：提供因果证据
   - 局限：个案化、低通量、无法全基因组评估

2. **阶段二：表观基因组富集分析**（~2010s–2020s）
   - 代表性方法：在 TE 亚家族上统计增强子标记的富集（如 H3K27ac ChIP-seq 峰与 TE 重叠）
   - 优点：全基因组覆盖
   - 局限：需要额外的表观基因组实验；富集≠功能；无法定量调控强度

3. **阶段三：基于表达数据的统计推断**（本文位置）
   - 代表性方法：craTEs（本文），借鉴 TF 基序活性分析（如 MARA, motif activity response analysis）的思路
   - 优点：仅需 RNA-seq；直接估计效应量；可区分功能性与非功能性 TE 拷贝
   - 局限：线性近似；无法区分直接与间接调控；需要大量扰动实验

**本文主张的位置**：craTEs 是第一个将 MARA 类模型应用于 TE 亚家族层面的方法，将 TE 视为「调控黑箱」，从基因表达差异中反推 TE 亚家族的调控活性。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| TE 调控活性难以定量 | 现有方法只能定性判断 TE 是否与增强子标记重叠，无法给出调控强度 | 表观基因组标记是生化活性的代理，不等于对基因表达的因果影响 | Introduction: "identification of TE-embedded CREs currently relies on the genome-wide profiling of epigenomic hallmarks" |
| 基于 DE 富集的方法统计功效低 | 需要预先设定 DE 阈值，丢失连续效应量信息；多重检验校正后功效不足 | DE 分析对每个基因独立检验，未利用 TE 亚家族作为共享特征的先验结构 | Results: craTEs 识别出 SVA C 而 DE 富集方法未检出（fig. 1B vs 1C） |
| TE 亚家族内功能异质性 | 同一亚家族内仅部分拷贝有调控活性，整体分析会稀释信号 | TE 拷贝在基因组中散布，受局部染色质环境影响 | Results 图 4: 按表观状态拆分后，功能性拷贝的活性显著高于非功能性拷贝 |
| 需要额外实验成本 | 表观基因组学（ChIP-seq/ATAC-seq）增加实验成本与样本量需求 | 这些实验需要大量细胞、抗体、测序深度 | Introduction: "performing them in pair with RNA-seq significantly increases experimental costs" |
| 单样本无法推断调控 | 单个 RNA-seq 样本只能反映稳态表达，无法区分调控来源 | 需要扰动（如 TF 过表达、CRISPRi）来产生表达差异 | Methods: 模型基于 control vs treatment 的成对比较 |

---

## 06 核心思想

### 1) 表面方法

craTEs 是一个线性回归模型：对每个基因 p，将其表达变化 ΔE_p 建模为邻近 TE 亚家族拷贝数的线性组合，回归系数即该 TE 亚家族的「顺式调控活性」。模型基于成对样本（control vs treatment），通过最小二乘估计系数，并用 t 检验判断系数是否显著非零。

### 2) 核心洞察

**TE 亚家族作为「调控黑箱」**：同一亚家族的 TE 拷贝因序列相似，倾向于结合相似的 TF 集合，因此可视为具有一致调控倾向的单元。通过聚合大量基因的信息，即使每个 TE 拷贝对单个基因的效应微弱，也能在亚家族水平检测到显著信号。这类似于 MARA 模型从表达谱推断 TF 基序活性的思路，但将「基序」替换为「TE 亚家族」。

### 3) 可能的普适教训 [Analysis]

- **聚合策略**：将大量弱信号聚合到共享特征（如 TE 亚家族）上，可以显著提升检测功效，这一思路可迁移到其他重复序列元件（如卫星 DNA、rDNA）的调控分析。
- **表达数据的信息量**：本文证明 RNA-seq 中蕴含的顺式调控信息比通常认为的更多，即使不依赖表观基因组数据也能推断调控事件。
- **线性近似的边界**：模型假设 TE 效应是线性和可加的，忽略了非线性互作（如 TF 协同、染色质构象），这既是简化也是局限。

---

## 07 方法总览

- **输入**：
  - RNA-seq 基因表达计数矩阵（蛋白质编码基因）
  - TE 基因组注释（RepeatMasker，hg19）
  - 实验设计：成对条件（control vs treatment），如 CRISPRi、TF 过表达
- **输出**：
  - 每个 TE 亚家族的估计调控活性（回归系数 β）
  - 显著性检验 p 值（BH 校正）
  - 调控活性矩阵（TE 亚家族 × 实验条件）
- **模块**：
  1. TE 注释预处理：合并碎片化 TE 拷贝（同一亚家族、同链、间距 <1kb 合并）
  2. 基因-TE 关联：计算每个基因启动子 ±50kb 窗口内的 TE 亚家族拷贝数
  3. 表达矩阵处理：log2(TPM+伪计数)，行/列中心化
  4. 线性回归：ΔE = N·ΔA + 噪声，最小二乘估计
  5. 显著性检验：t 检验 + BH 多重检验校正
  6. 距离加权扩展：用高斯核（带宽 L）对 TE 拷贝按距离加权
  7. 交叉验证：5-fold CV 选择最优带宽 L
- **流程**：TE 注释 → 构建基因-TE 邻接矩阵 N → 处理表达矩阵 E → 对每对条件计算 ΔE → 回归估计 ΔA → 显著性检验 → 输出显著 TE 亚家族列表

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| TE 拷贝合并 | 将碎片化 TE 注释合并为完整拷贝 | RepeatMasker 常将单个 TE 拆分为多段，导致拷贝数虚增 | 输入：RepeatMasker 注释；输出：合并后 TE 拷贝 | Methods: "merged TE fragments of the same subfamily into single integrants" | 预期：拷贝数高估，回归系数被稀释，检测功效下降 [Analysis] |
| 基因-TE 邻接矩阵构建 | 计算每个基因邻近的 TE 亚家族拷贝数 | 定义「顺式」范围，将基因组结构转化为回归特征 | 输入：基因坐标、TE 坐标；输出：矩阵 N (P×M) | Methods: "counted the number of integrants of subfamily m falling within cis-regulatory distance" | 预期：窗口过小遗漏远距离调控，过大引入噪声 [Analysis] |
| 表达矩阵中心化 | 去除基因和样本的基线效应 | 使模型聚焦于条件间的差异而非绝对表达 | 输入：log2(TPM) 矩阵；输出：中心化矩阵 | Methods: "Column-centering E sets d_s to zero... Row-centering E sets c_p to zero" | 预期：未中心化会导致基线表达差异被误归为 TE 效应 [Analysis] |
| 线性回归估计 | 估计 TE 亚家族调控活性 | 核心推断步骤，从表达差异中反推调控活性 | 输入：ΔE, N；输出：β, SE, t, p | Results 图 1C: 正确识别 CRISPRi 靶向的 TE 亚家族 | 预期：移除后无替代推断方法 |
| 距离加权（高斯核） | 按距离衰减 TE 对基因的调控影响 | 硬阈值（50kb）可能不准确，加权可自适应 | 输入：TE-基因距离；输出：加权矩阵 N | Results 图 2B: CV 选择 L=100kb 或 500kb 最优 | 预期：硬阈值可能遗漏 50–200kb 范围的调控 [Analysis] |
| 功能/非功能拆分 | 按表观状态将 TE 亚家族拆分为功能性和非功能性拷贝 | 同一亚家族内拷贝异质性会稀释信号 | 输入：ATAC-seq/H3K9me3 峰；输出：拆分后矩阵 | Results 图 4B: 功能性拷贝活性显著更高 | 预期：不拆分则信号被稀释，效应量被低估 |

---

## 09 关键公式符号

**模型 1（硬阈值版本）**：

ΔE_p = Σ_m N_pm · ΔA_m + ε_p

- ΔE_p：基因 p 在条件 2 vs 条件 1 的 log2 表达变化
- N_pm：基因 p 启动子 ±50kb 窗口内 TE 亚家族 m 的拷贝数（调控易感性）
- ΔA_m：TE 亚家族 m 的调控活性差异（待估参数）
- ε_p：高斯噪声

**模型 2（距离加权版本）**：

N_pm = Σ_k w(d_pk)

其中 w(d) = exp(-d² / 2L²)（高斯核）

- d_pk：TE 拷贝 k 中心到基因 p 最近启动子的距离（bp）
- L：高斯核带宽（标准差），通过 5-fold CV 选择

**中心化处理**：

- 列中心化（每基因）：E'_ps = E_ps - mean_s(E_ps)，消除样本效应 d_s
- 行中心化（每样本）：E''_ps = E'_ps - mean_p(E'_ps)，消除基因基线 c_p

**显著性检验**：

- H₀: ΔA_m = 0
- t 统计量 = β̂_m / SE(β̂_m)，服从 t 分布
- p 值经 Benjamini-Hochberg 校正

---

## 10 实验设计与证据链

**数据集**：
1. **naïve hESC + CRISPRi 靶向 LTR5-Hs/SVA**（GSE117395）：CRISPRi 表观沉默 LTR5-Hs 和 SVA 亚家族，RNA-seq 测量基因表达变化
2. **primed hESC + KLF4 过表达**（GSE117395）：KLF4 是核心多能性 TF，已知结合 LTR5-Hs/SVA
3. **naïve hESC + ZNF611 过表达**（GSE117395）：ZNF611 是 SVA 结合 KRAB-ZNF 抑制因子
4. **primed hESC + 441 个 TF 过表达**（DRA006296）：大规模扰动库
5. **K562 + CRISPRi 靶向 LTR2B**（GSE136763）：独立细胞系验证

**指标**：
- 回归系数 β（调控活性估计）
- t 检验 p 值（BH 校正）
- 5-fold CV 均方误差（选择带宽 L）
- 与 ChIP-seq 峰重叠的富集（验证功能/非功能拆分）

**评测协议**：
- 对每个实验，将 treatment vs control 的 ΔE 与 N 矩阵回归
- 比较 craTEs 与 DE 富集方法（Fisher 精确检验 + 超几何检验）的检出能力
- 用已知生物学知识（如 KLF4 结合 LTR5-Hs）作为 ground truth

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| CRISPRi 靶向 LTR5-Hs/SVA（naïve hESC） | craTEs 能识别被沉默的 TE 亚家族 | craTEs vs DE 富集方法 | craTEs 识别出 LTR5-Hs、SVA B/C/D 活性显著下降；DE 富集仅检出 SVA D | craTEs 比 DE 富集更灵敏 | 未证明 craTEs 能识别所有真实调控 TE | Results 图 1C |
| KLF4 过表达（primed hESC） | craTEs 能识别 KLF4 激活的 TE 亚家族 | 与已知 KLF4 结合位点比较 | LTR7、LTR5-Hs、SVA D 活性显著上升 | craTEs 能复现已知 KLF4-TE 调控关系 | 未证明因果关系（KLF4 可能间接调控） | Results 图 1C |
| ZNF611 过表达（naïve hESC） | craTEs 能识别 ZNF611 抑制的 TE 亚家族 | 与已知 ZNF611 靶点比较 | SVA 亚家族活性显著下降 | craTEs 能检测抑制性调控 | 未区分直接/间接抑制 | Results 图 1C |
| 441 TF 过表达筛选 | craTEs 能在大规模扰动中识别 TE-TF 调控网络 | 聚类分析 | TF 家族聚类与 TE 亚家族活性模式对应 | craTEs 可扩展至大规模筛选 | 未验证所有 441 个 TF 的调控关系 | Results 图 3 |
| 距离加权（L 选择） | TE 调控范围约 200kb | 5-fold CV 比较不同 L | L=100kb 或 500kb 最优 | TE 调控范围与已知增强子-启动子距离一致 | 未排除更远距离的调控 | Results 图 2B |
| 功能/非功能拆分（图 4） | 表观状态能区分功能性 TE 拷贝 | 按 ATAC-seq/H3K9me3 拆分 | 功能性拷贝活性显著高于非功能性 | TE 亚家族内存在功能异质性 | 未证明表观标记是功能性的充分条件 | Results 图 4B |

---

## 11 结论正确解读

- **任务范围**：本文方法仅适用于有扰动实验（treatment vs control）的 RNA-seq 数据，不适用于静态表达谱；仅推断 TE 亚家族层面的调控活性，不定位单个功能性 TE 拷贝。
- **oracle/真值输入**：CRISPRi 靶向的 TE 亚家族（LTR5-Hs/SVA、LTR2B）作为已知 ground truth；KLF4/ZNF611 的 ChIP-seq 结合位点作为辅助验证。
- **端到端状态**：方法端到端可用（输入 RNA-seq 计数 + TE 注释 → 输出 TE 亚家族活性列表），但未提供独立验证的因果实验（如单拷贝敲除）。
- **算力成本**：线性回归 + 交叉验证，计算成本极低，普通工作站可运行。
- **历史数据依赖**：依赖 RepeatMasker 注释质量；TE 亚家族分类基于序列相似性，可能掩盖功能异质性。
- **模型依赖**：线性可加假设可能遗漏非线性互作；高斯核带宽选择依赖 CV，可能过拟合特定数据集。
- **最难情形**：低表达基因、TE 拷贝数极少的亚家族、间接调控效应（TF 级联）可能难以检测。
- **群体/领域边界**：结论基于 hESC 和 K562 细胞系，不一定推广到其他细胞类型或物种；TE 调控活性是条件依赖的（细胞类型、发育阶段）。
- **不确定性**：回归系数估计有标准误，但未提供置信区间；多重比较校正后仍可能有假阳性。

**有边界的复述**：在 hESC 和 K562 的扰动实验中，craTEs 能从 RNA-seq 数据中识别已知的 TE 亚家族调控事件，其检测能力优于 DE 富集方法，且能估计 TE 调控的大致范围（~200kb），但该方法不提供单拷贝分辨率的调控定位，也不适用于无扰动的静态数据。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 线性模型近似 | 模型假设 TE 效应线性可加，真实调控可能非线性 | 未明确提及 | Discussion: "the true function underlying the regulatory mechanism is most likely non-linear" |
| 低解释方差 | craTEs 仅解释基因表达变异的 3–10% | 未明确提及 | Discussion: "craTEs explains a fraction of the variation in gene expression ranging from approx. 3% to 10%" |
| 亚家族层面分辨率 | 无法定位单个功能性 TE 拷贝 | 未明确提及 | 隐含于方法设计（亚家族聚合） |
| 条件依赖性 | 调控活性随细胞类型和状态变化 | 未明确提及 | 隐含于实验设计（不同细胞系） |
| 间接效应混淆 | 无法区分 TE 直接调控与通过其他基因的间接效应 | 未明确提及 | 隐含于模型结构（无中介变量） |

**作者提及的相关约束**（非正式局限）：
- TE 注释依赖 RepeatMasker，碎片化拷贝需合并（Methods）
- 排除与基因外显子重叠的 TE，可能遗漏部分调控元件（Methods: "we excluded TEs overlapping exons"）
- 需要至少一对 treatment/control 样本，无法用于单样本推断

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 线性模型假设 TE 拷贝数对基因表达有可加效应 | 真实调控可能涉及协同、拮抗或阈值效应；拷贝数≠活性（部分拷贝可能沉默） | 若假设不成立，估计的 β 可能偏差 | 在已知调控的 TE 亚家族上比较线性 vs 非线性模型预测 | Methods: 模型为纯线性 |
| 距离加权核的选择依赖 CV | CV 可能过拟合特定数据集；L=100kb 或 500kb 在不同细胞类型可能不同 | 影响所有下游推断 | 在不同细胞类型和扰动类型中重复 CV 选择 | Results 图 2B |
| 功能/非功能拆分依赖表观标记 | ATAC-seq/H3K9me3 是相关标记而非因果证据；标记状态可能动态变化 | 拆分可能引入分类错误 | 用独立功能实验（如 CRISPR 敲除单拷贝）验证 | Results 图 4 |
| 未控制共线性的 TE 亚家族 | 不同 TE 亚家族在基因组中可能共定位，导致回归系数不稳定 | 可能产生假阳性/假阴性 | 检查 N 矩阵的条件数，用正则化回归（如 ridge/LASSO）对比 | Methods: 使用普通最小二乘 |
| 441 TF 过表达实验的解读 | TF 过表达可能产生非生理浓度，导致非特异性结合 | 可能高估 TF-TE 调控关系 | 与内源表达水平校正，或使用 degron 系统验证 | Results 图 3 |
| 与 DE 富集方法的比较 | 比较可能受 DE 阈值选择影响；craTEs 的优越性可能仅在特定阈值下成立 | 影响方法推荐 | 在不同 DE 阈值下系统比较 | Results 图 1B vs 1C |
| 未提供效应量的置信区间 | 仅报告 p 值，未报告 β 的不确定性范围 | 影响效应量解读 | 计算并报告 bootstrap 或 profile likelihood 置信区间 | Results: 仅报告 SE 和 p 值 |

---

## 14 学到什么

**Agent 提炼的知识候选**：

1. **从表达数据反推调控活性的统计框架**：craTEs 的核心思想——将基因表达变化回归到邻近调控元件的拷贝数上——可直接迁移到 TF–DNA 结合研究。例如，可将「TE 亚家族拷贝数」替换为「预测的 TF 结合位点密度」或「ChIP-seq 峰强度」，估计特定 TF 在给定细胞类型中的调控活性。

2. **聚合策略提升检测功效**：将单个弱效应聚合到共享特征（亚家族/基序）上，可显著提升统计功效。在 TF–DNA 结合研究中，可对同一 TF 家族的所有结合位点聚合分析，而非逐个位点检验。

3. **距离加权核的普适性**：高斯核加权 TE 对基因的调控影响，可迁移到 TF 结合位点-靶基因关联分析中，替代硬阈值窗口，更灵活地建模增强子-启动子距离效应。

4. **功能/非功能拆分的验证策略**：用表观标记（ATAC-seq、H3K9me3）拆分 TE 拷贝后验证活性差异，这一策略可迁移到 TF 结合位点分析中——用染色质可及性、组蛋白修饰等标记区分功能性 vs 非功能性 TF 结合位点。

5. **大规模扰动筛选的设计**：441 个 TF 过表达 + craTEs 分析的模式，可迁移到 TF–DNA 互作研究中，系统性地绘制 TF→TE→基因的调控网络。

6. **RNA-seq-only 的推断优势**：本文证明无需表观基因组数据即可推断调控事件，这对难以获得 ChIP-seq 的样本（如稀有细胞类型、临床样本）尤为重要。

7. **线性模型的解释性**：回归系数 β 可直接解释为「插入一个 TE 拷贝对邻近基因表达的预期影响」，这种可解释性在生物信息学工具中具有实用价值。

---

## 15 与已有知识连接

- **MARA (Motif Activity Response Analysis)**：craTEs 直接改编自 MARA 模型（Sussex et al.），将「TF 基序」替换为「TE 亚家族」。MARA 是 TF–DNA 结合研究中常用的从表达谱推断 TF 活性的方法，本文是其向重复序列元件的推广。
- **TE 作为增强子的研究**：与 Chuong et al. (2017) 关于 TE 提供增强子序列的综述一致；本文提供了定量框架。
- **CRISPRi 表观沉默 TE**：与 Fuentes et al. (2018) 和 Pontis et al. (2019) 的实验方法一致，本文使用其数据作为验证。
- **增强子-启动子距离**：与 Gasperini et al. (2019) 和 Fulco et al. (2019) 的 CRISPR 干扰增强子筛选结果一致——增强子通常在 100–200kb 范围内影响靶基因。
- **TF 结合位点密度模型**：与 Foat et al. (2006) 的 Bayesian 模型类似，均使用线性回归框架从表达数据推断调控元件活性。
- **候选方向**：本文方法可与 AlphaFold 等结构预测工具结合——预测 TF 对 TE 序列的结合亲和力，作为 N 矩阵的加权因子，可能提升预测精度。

---

## 16 研究想法

**Agent 生成的研究候选**：

### 候选 1：TF 结合位点密度模型（TFBS-density model）
- **名称**：TFBS-craTEs：从 RNA-seq 推断 TF 对靶基因的调控活性
- **来源局限/观察**：craTEs 将 TE 亚家族视为调控单元，但未利用 TF 结合位点信息；TF–DNA 结合是 TE 调控的分子基础
- **核心假设**：基因表达变化可回归到邻近区域预测的 TF 结合位点密度上，估计每个 TF 的调控活性
- **增量**：将 TE 亚家族替换为 TF 基序/结合位点，可直接比较不同 TF 的调控强度；可整合 ChIP-seq 数据作为先验
- **初步方法**：用 FIMO/DeepBind 扫描基因组预测 TF 结合位点，构建 TF×基因 的 N 矩阵，回归估计 TF 活性
- **验证方式**：在已知 TF 扰动数据（如 KnockTF2.0）上验证；与 ChIP-seq 峰密度比较
- **创新状态**：unverified

### 候选 2：结构感知的 TE 调控活性预测
- **名称**：Structure-aware TE regulation：整合 AlphaFold 预测的 TF-TE 结合亲和力
- **来源局限/观察**：craTEs 假设同一 TE 亚家族内所有拷贝调控活性相同，但序列变异（SNP/插入缺失）可能改变 TF 结合亲和力
- **核心假设**：TE 拷贝的调控活性与其编码的 TF 结合位点质量（预测结合亲和力）成正比
- **增量**：用 AlphaFold3/DeepMind 预测 TF 与 TE 序列的复合物结构，估计结合亲和力，作为 N 矩阵的加权因子
- **初步方法**：选取核心 TF（如 OCT4、KLF4）与代表性 TE 亚家族序列，结构预测结合亲和力；与 craTEs 估计的活性比较
- **验证方式**：在 CRISPRi 数据上比较加权 vs 未加权模型的预测精度
- **创新状态**：unverified

### 候选 3：单细胞 RNA-seq 的 TE 调控推断
- **名称**：sc-craTEs：从单细胞转录组推断细胞类型特异的 TE 调控活性
- **来源局限/观察**：craTEs 需要成对 bulk 样本，无法解析细胞类型特异的调控
- **核心假设**：单细胞 RNA-seq 中，同一 TE 亚家族邻近基因的共表达模式可推断 TE 调控活性
- **增量**：将 craTEs 扩展到单细胞数据，利用细胞类型作为天然扰动
- **初步方法**：对每个细胞类型，回归基因表达到 TE 拷贝数，估计细胞类型特异的 TE 活性
- **验证方式**：与已知细胞类型特异的 TE 表达（如 LTR5-Hs 在 naïve 多能性中）比较
- **创新状态**：unverified

### 候选 4：TE 调控的进化比较分析
- **名称**：Evolutionary dynamics of TE-mediated cis-regulation
- **来源局限/观察**：craTEs 仅分析人类数据，未利用跨物种比较
- **核心假设**：TE 亚家族的调控活性与其进化年龄和物种分布相关
- **增量**：将 craTEs 应用于多物种（人、小鼠、斑马鱼）RNA-seq 数据，比较 TE 调控网络的保守性
- **初步方法**：构建各物种的 TE×基因 N 矩阵，估计 TE 活性，比较同源 TE 亚家族的活性差异
- **验证方式**：与已知保守增强子（如 VISTA enhancer）比较
- **创新状态**：unverified

### 候选 5：TE 调控与疾病关联的孟德尔随机化
- **名称**：Mendelian randomization for TE-mediated disease risk
- **来源局限/观察**：craTEs 未连接遗传变异与疾病
- **核心假设**：TE 拷贝数变异（CNV）通过改变顺式调控影响疾病风险
- **增量**：将 craTEs 估计的 TE 活性与 GWAS 数据整合，用孟德尔随机化推断因果效应
- **初步方法**：用 craTEs 估计 eQTL 数据中的 TE 活性，与 GWAS 汇总统计进行 MR 分析
- **验证方式**：在已知 TE 相关疾病（如自身免疫病）中验证
- **创新状态**：unverified