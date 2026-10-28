## 01 基本信息

- **标题**：A base-resolution panorama of the *in vivo* impact of cytosine methylation on transcription factor binding
- **作者与单位**：Aldo Hernandez-Corchado; Hamed S. Najafabadi（麦吉尔大学，加拿大）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2021
- **论文类型**：方法学 + 系统生物学分析（计算建模 + 大规模组学数据整合）
- **领域**：计算生物学 / 表观基因组学 / 转录调控
- **关键词**：转录因子（TF）、CpG 甲基化、ChIP-seq、广义线性模型、甲基化偏好、C2H2-ZF
- **DOI/arXiv 号**：10.1101/2021.08.27.457995
- **代码**：https://github.com/csglab/JAMS
- **数据**：Zenodo（DOI: 10.5281/zenodo.5573261）
- **阅读日期**：未提供
- **该文在「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法/物理模拟」方向中的位置**：本文属于**统计建模/机器学习方法**分支，而非物理模拟（MD/对接）或深度学习方法。其核心贡献在于提出一个广义线性模型（GLM）框架 JAMS，将 ChIP-seq 信号分解为背景信号与 TF 特异性信号，从而在**碱基分辨率**下从体内数据中解耦出 CpG 甲基化对 TF 结合的独立效应。该方法可视为一种**可解释的浅层机器学习模型**，与深度学习黑箱模型形成互补，为 TF–DNA 结合机制研究提供了可迁移的统计去混淆框架。

---

## 02 一句话总结

本文提出 JAMS（Joint Accessibility-Methylation-Sequence）广义线性模型，将 ChIP-seq 的 pull-down 与 control 读段计数联合建模为 DNA 可及性、区域甲基化、序列和碱基分辨率 CpG 甲基化的函数，从而在体内条件下定量推断 260 个 TF 的甲基化结合偏好，发现 45% 的 TF 被甲基化抑制、6% 偏好甲基化，且多数体外甲基化偏好信号在体内被 MBD 蛋白竞争所掩盖。

---

## 03 研究问题

- **具体问题**：在体内（in vivo）条件下，单个 CpG 位点的甲基化状态如何影响转录因子（TF）与其结合位点（TFBS）的结合强度？哪些 TF 偏好甲基化 DNA，哪些被甲基化抑制？
- **为什么重要**：DNA 甲基化是经典的表观遗传抑制标记，但近年体外实验（如 methyl-SELEX）表明超过三分之一的 TF 可能偏好甲基化序列。然而体内环境存在 DNA 可及性、区域甲基化水平、MBD 蛋白竞争等混杂因素，使得碱基分辨率的甲基化效应难以从 ChIP-seq 数据中直接观测。
- **现有方法不足**：
  - 体外方法（methyl-SELEX、bisulfite-SELEX、PBM）无法反映体内染色质环境与竞争性蛋白结合。
  - 已有体内分析方法（如比较甲基化/非甲基化位点的 ChIP-seq 信号）未同时控制 DNA 可及性和区域甲基化水平，导致效应被混淆。
  - 现有工具（如 BaMM、MOODS）仅建模序列，不整合甲基化与可及性信息。
- **精确的「Can ... ?」研究问题**：Can a joint statistical model of accessibility, regional methylation, sequence, and base-resolution CpG methylation quantitatively explain in vivo TF binding strength (as measured by ChIP-seq) and recover known TF methylation preferences?

---

## 04 背景与发展脉络

> 注：此脉络基于本文引言与讨论，结合外部文献，标记为「经外部核验」与「仅本文框架」混合。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|----------|
| **早期体外生化** | EMSA、footprinting | 直接测量 TF–DNA 亲和力 | 无法反映体内染色质环境 | 背景 |
| **高通量体外** | methyl-SELEX / bisulfite-SELEX（Yin et al. 2017） | 系统测量 TF 对甲基化 CpG 的偏好 | 体外条件，无染色质与竞争蛋白 | 本文的对照基准 |
| **体内 ChIP-seq 分析** | 比较甲基化/非甲基化位点信号 | 反映体内真实结合 | 未控制可及性与区域甲基化混淆 | 本文改进对象 |
| **序列建模** | PWM、BaMM、DeepBind | 预测 TF 结合序列偏好 | 不含甲基化信息 | 本文的序列模块基础 |
| **统计去混淆** | **JAMS（本文）** | 联合建模可及性、区域甲基化、序列、碱基分辨率甲基化，分离背景与 TF 信号 | 依赖 ChIP-seq 数据质量与已知 motif | **本文核心贡献** |

**本文主张的位置**：JAMS 是首个在碱基分辨率下、从体内 ChIP-seq 数据中系统推断 TF 甲基化偏好并同时控制可及性与区域甲基化混淆的统计框架。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| **体内甲基化效应被混淆** | 无法从 ChIP-seq 信号中直接分离单个 CpG 甲基化的效应 | DNA 可及性、区域甲基化水平、序列偏好同时影响 ChIP-seq 信号 | Results 节 "Modeling the joint effect..." 第一段 |
| **体外与体内结果不一致** | 体外 methyl-SELEX 显示大量 TF 偏好甲基化，但体内难以复现 | MBD 蛋白与 TF 竞争结合甲基化 CpG，掩盖了 TF 的固有偏好 | Discussion 节；Results 图 4D |
| **现有方法缺乏碱基分辨率** | 已有体内分析只能区分高/低甲基化区域，无法定位到单个 CpG | ChIP-seq 信号是多个位点的平均，且 motif 内多个 CpG 效应叠加 | Results 节 "JAMS models reveal..." 第一段 |
| **背景信号干扰** | ChIP-seq 的 pull-down 信号包含非特异性背景，掩盖 TF 特异性信号 | 染色质可及性影响 sonication 效率，导致背景信号与 TF 信号混淆 | Results 图 1F；Methods "Implementation of JAMS" |
| **motif 选择偏差** | 使用已知 motif 对齐位点可能引入偏差 | 不同 motif 来源（SELEX vs PBM）质量不一 | Methods "Formatting and preprocessing" 节 |

---

## 06 核心思想

### 1) 表面方法
构建一个广义线性模型（GLM），对每个 ChIP-seq 实验的 peak 区域，将 pull-down 和 control 的读段计数联合建模为以下特征的线性函数：
- **序列**：TFBS 内每个位置的 one-hot 编码
- **可及性**：DNase-seq 信号（分 bin）
- **区域甲基化**：TFBS 侧翼区域的平均甲基化水平
- **碱基分辨率甲基化**：TFBS 内每个 CpG 位点的甲基化比例

模型同时拟合背景信号（control）和 TF 特异性信号（pull-down 减去背景），通过似然比检验判断每个 CpG 位点的甲基化效应是否显著。

### 2) 核心洞察
- **分离背景与 TF 信号**：ChIP-seq 的 pull-down 信号 = 背景信号 + TF 特异性信号。通过同时建模 control 实验，可以将背景信号（受可及性影响）与 TF 信号（受序列和甲基化影响）解耦，从而避免可及性对甲基化效应的混淆。
- **碱基分辨率是关键**：motif 内不同 CpG 位点的甲基化效应可能方向相反（一个位点促进、另一个抑制），只有碱基分辨率建模才能捕捉这种异质性。
- **体内 vs 体外的差异源于竞争**：体外实验中 TF 单独与 DNA 结合，偏好甲基化；体内存在 MBD 蛋白竞争，导致净效应偏向甲基化抑制或中性。

### 3) 可能的普适教训 [Analysis]
- **统计去混淆优于实验控制**：当实验无法完全控制混杂因素时，联合建模多个协变量可以从观测数据中分离因果效应。这一思路可迁移到其他组学数据整合问题。
- **体外结果需体内验证**：体外高通量实验（SELEX、PBM）测的是 TF 的固有生化偏好，但体内净效应取决于竞争环境。对 TF–DNA 互作研究而言，体外与体内结果应视为互补而非替代。
- **可解释模型的价值**：在深度学习主导的时代，GLM 等可解释模型在需要推断具体生物学机制（如某个 CpG 位点的效应方向）时仍有不可替代的价值。

---

## 07 方法总览

- **输入**：
  - ChIP-seq/ChIP-exo pull-down 与 control 的 BAM 文件（2209 个实验，604 个 TF，6 个细胞系）
  - 对应细胞系的 WGBS 甲基化数据（碱基分辨率）
  - 对应细胞系的 DNase-seq 可及性数据
  - TF 的已知 motif（PFM，来自 CIS-BP，优先 SELEX 来源）
- **输出**：
  - 每个 TF 的 JAMS 模型（系数向量 β_f 和 β_b）
  - 每个 TF 的甲基化偏好分类（methyl-minus / methyl-plus / mixed-effect / no-effect）
  - 每个 CpG 位点的甲基化效应方向与显著性
- **模块**：
  1. **数据预处理**：peak calling（MACS，p<0.01）、去除重复区域、motif 匹配（AffiMx）、提取序列/甲基化/可及性特征
  2. **特征构建**：序列 one-hot、甲基化比例（每个 CpG 位点）、可及性（分 bin 对数）、区域甲基化（侧翼平均）
  3. **模型拟合**：负二项 GLM，联合建模 control 与 pull-down 计数，公式 `n ~ XX + t + XX:t`
  4. **显著性检验**：似然比检验（比较全模型与去除甲基化特征的简化模型）
  5. **TF 分类**：基于显著正/负甲基化效应的存在与否
- **训练**：每个 ChIP-seq 实验独立拟合一个 GLM，无跨实验共享参数；使用 R 的 `glm.nb` 函数
- **工具**：bowtie2、samtools、MACS、bismark、bedtools、bwtool、AffiMx、RCADE2、R（glm.nb）
- **反馈回路**：无显式反馈回路；模型为单次拟合，无迭代优化
- **假设**：
  - ChIP-seq 读段计数服从负二项分布
  - 背景信号与 TF 信号可加性分解
  - 已知 motif 能正确对齐 TFBS 位置
  - 甲基化效应在位点间独立（无交互项）

**文字流程**：
1. 从 ENCODE/GEO 收集 ChIP-seq、WGBS、DNase-seq 数据
2. 对每个 ChIP-seq 实验进行 peak calling，并生成负 peak 集（control 交换）
3. 去除重复区域，用已知 motif 在 peak summit ±100bp 内定位最佳 TFBS
4. 提取每个 peak 的序列、TFBS 内每个 CpG 的甲基化比例、侧翼区域平均甲基化、可及性分 bin 信号
5. 构建负二项 GLM，同时拟合 control 与 pull-down 计数
6. 通过似然比检验评估每个 CpG 位点甲基化效应的显著性
7. 对每个 TF 汇总显著效应，分类为 methyl-minus / methyl-plus / mixed-effect / no-effect
8. 与体外 SELEX 数据比较，分析体内外一致性

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| **Peak calling 与负 peak 集** | 识别 ChIP-seq 富集区域，并生成背景对照 | 需要覆盖宽范围信号强度的 peak 以拟合背景模型 | 输入：BAM 文件；输出：peak 列表（正/负） | Methods "ChIP-seq data processing" 节 | 移除负 peak 将无法估计背景信号，导致甲基化效应与可及性混淆 [预期] |
| **Motif 匹配与 TFBS 定位** | 在 peak summit 附近定位最可能的 TFBS | 需要对齐多个 peak 的序列和甲基化特征 | 输入：PFM、peak 序列；输出：TFBS 位置 | Methods "Formatting and preprocessing" 节；Results 图 1H（序列模型与已知 motif 相关 r=0.86） | 移除将导致序列特征无法对齐，甲基化位点定位失效 [预期] |
| **特征提取** | 构建序列 one-hot、甲基化比例、可及性、区域甲基化特征 | 将原始数据转换为 GLM 可用的预测变量 | 输入：BAM/WGBS/DNase 文件、TFBS 坐标；输出：特征矩阵 X | Methods "Formatting and preprocessing" 节 | 移除可及性特征将导致甲基化效应被可及性混淆 [预期] |
| **负二项 GLM 联合建模** | 同时拟合 control 与 pull-down 计数，分离背景与 TF 信号 | 核心创新：将背景信号作为显式模型组件，避免混淆 | 输入：特征矩阵 X、计数向量 n；输出：系数 β_f、β_b | Results 图 1E（预测与观测相关 r=0.69）；Methods "Implementation of JAMS" | 移除联合建模将退化为仅建模 pull-down，无法分离背景 [实测：作者在 CTCF 模型中验证了背景信号的可预测性] |
| **似然比检验** | 评估每个 CpG 位点甲基化效应的显著性 | 需要判断哪些位点的甲基化效应是统计上可靠的 | 输入：全模型与简化模型；输出：p 值、FDR | Results 图 2A（CTCF 的 dot plot logo 显示显著位点） | 移除将无法区分真实效应与噪声 [预期] |
| **TF 分类** | 基于显著效应方向将 TF 分为 methyl-minus / plus / mixed / no-effect | 系统层面总结甲基化偏好 | 输入：各 TF 的显著 CpG 效应；输出：分类标签 | Results 图 4B（45% methyl-minus, 6% methyl-plus） | 移除将无法进行系统比较 [预期] |
| **RCADE2 motif 增强** | 为 C2H2-ZF 蛋白推断更准确的 PFM | CIS-BP 对锌指蛋白的 motif 覆盖不足 | 输入：蛋白序列、ChIP-seq peak 序列；输出：优化 PFM | Methods "Inference of PFMs for C2H2-ZF proteins" 节 | 移除将导致锌指蛋白的 TFBS 定位不准，甲基化效应估计偏差 [预期] |

---

## 09 关键公式符号

**1. JAMS 核心模型**（Methods "Implementation of JAMS" 节）：

$$\log(\mu_f) = X \beta_f$$

- $\mu_f$：k×1 向量，k 个 peak 的 TF 特异性结合强度
- $X$：k×m 特征矩阵（序列 one-hot、甲基化、可及性等）
- $\beta_f$：m×1 系数向量，表示各特征对 TF 结合强度的效应

**2. 背景信号模型**：

$$\log(\mu_b) = X \beta_b$$

- $\mu_b$：k×1 向量，k 个 peak 的背景信号强度
- $\beta_b$：m×1 系数向量，表示各特征对背景信号的效应

**3. Control 读段计数**：

$$\log(\lambda_c) = \log(\mu_b) + s_c$$

- $\lambda_c$：k×1 向量，control 实验的期望读段计数
- $s_c$：control 文库的 size factor（对数尺度）

**4. Pull-down 读段计数**：

$$\log(\lambda_p) = \log(\mu_b + \mu_f) + s_p$$

- $\lambda_p$：k×1 向量，pull-down 实验的期望读段计数
- $s_p$：pull-down 文库的 size factor（对数尺度）

**5. 负二项观测模型**：

$$n_c \sim NB(\lambda_c, \phi), \quad n_p \sim NB(\lambda_p, \phi)$$

- $n_c, n_p$：观测到的 control 和 pull-down 读段计数
- $\phi$：共享的离散参数

**6. 实际拟合形式**（R 公式）：

$$n \sim XX + t + XX:t$$

- $n$：2k×1 向量，拼接 control 和 pull-down 计数
- $XX$：2k×m 矩阵，$XX = \text{rbind}(X, X)$
- $t$：2k×1 二元向量，0 表示 control，1 表示 pull-down
- $XX$ 的系数对应 $\beta_b$，$XX:t$ 的系数对应 $\beta_f$

**用途**：通过将背景信号（$\beta_b$）与 TF 特异性信号（$\beta_f$）分离，使得 $\beta_f$ 中甲基化特征的系数可以直接解释为甲基化对 TF 结合的独立效应，不受可及性和区域甲基化的混淆。

---

## 10 实验设计与证据链

### 数据集与资源
- **ChIP-seq/ChIP-exo**：2209 个实验，604 个 TF，6 个细胞系（HEK293, GM12878, HeLa-S3, HepG2, K562, H1），来源包括 ENCODE、Najafabadi et al.、Schmitges et al.、Imbeault et al.
- **WGBS**：6 个细胞系的碱基分辨率甲基化数据
- **DNase-seq**：6 个细胞系的可及性数据
- **体外对照**：Yin et al. 2017 的 methyl-SELEX / bisulfite-SELEX 数据（260 个 TF 中有 76 个有体外数据）
- **指标**：Pearson 相关系数（预测 vs 观测信号）、FDR（甲基化效应显著性）、分类精度（与 SELEX 比较）
- **预算/资源**：未提供具体计算资源信息
- **评测协议**：10 折交叉验证（CTCF 模型）；与 SELEX 数据的一致性比较

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-----------|-----------------|------|
| **CTCF JAMS 模型（HEK293）** | 可及性+甲基化+序列可定量预测 ChIP-seq 信号 | 10 折交叉验证，预测 vs 观测 pull-down/control 比 | Pearson r=0.69 | JAMS 能解释大部分 TF 结合信号变异 | 不能证明因果性；可能存在未建模的混杂因素 | Results 图 1E |
| **CTCF 甲基化效应验证** | 甲基化对 CTCF 结合有负效应 | 与已知 CTCF 甲基化敏感性比较 | 检测到 C2pG3 和 C12pG13 的显著负效应 | JAMS 能恢复已知的 CTCF 甲基化敏感性 | 未与突变实验直接比较 | Results 图 2A-B；Supplementary Fig. 2 |
| **跨细胞系可转移性** | JAMS 模型可预测其他细胞系的结合 | HEK293 训练的模型预测 GM12878, HeLa-S3 等 | 预测与观测显著相关 | 模型捕捉了细胞不变的 TF 内在偏好 | 不能排除细胞系特异性因子 | Results 表 1 |
| **差异结合预测** | 甲基化差异可解释跨细胞系差异结合 | GM12878 vs HeLa-S3 差异 peak，仅用甲基化特征预测 | 预测 logFC 与观测 logFC 相关 r=0.40（全部 peak），r=0.84（显著 peak） | 甲基化变化是差异结合的重要驱动因素 | 相关性不等于因果性；可及性变化可能共变 | Results 图 3C-E |
| **260 TF 系统分类** | 体内甲基化偏好可系统推断 | 2209 个实验，604 个 TF，筛选后 260 个高质量模型 | 45% methyl-minus, 6% methyl-plus, 1.5% mixed, 26% no-effect | 体内大多数 TF 被甲基化抑制，少数偏好 | 分类依赖 motif 质量与 ChIP-seq 数据质量 | Results 图 4B；Table 2 |
| **与 SELEX 体外数据比较** | 体内外甲基化偏好一致性 | 76 个 TF 有体外数据 | 82% 的体内 methyl-minus 与体外一致；但 20 个体外 methyl-plus 中仅 5 个在体内也呈 methyl-plus | 体外 methyl-plus 效应在体内多被掩盖 | 样本量小；SELEX 与体内条件差异大 | Results 图 4D；Discussion |
| **KRAB-ZF 富集分析** | methyl-plus TF 富集于 KRAB-ZF 家族 | 与所有 TF 比较 | 24% KRAB-ZF 为 methyl-plus vs 12% 非 KRAB（Fisher p<0.009） | KRAB-ZF 可能通过甲基化识别转座子 | 功能验证未做 | Results 表 2；Supplementary Table 4 |

---

## 11 结论正确解读

- **任务范围**：本文仅针对**体内 ChIP-seq 可观测的 TF 结合强度**，不涉及 TF 结合的功能后果（如基因表达变化）、不涉及非 CpG 甲基化（如 m6A）、不涉及组蛋白修饰的联合效应。
- **oracle/真值输入**：模型使用已知 motif（PFM）定位 TFBS，这是关键的 oracle 输入。若 motif 不准确，甲基化效应估计会偏差。作者用 RCADE2 增强锌指蛋白 motif，但其他家族仍依赖 CIS-BP。
- **端到端状态**：**非端到端**。JAMS 是统计模型而非深度学习；需要预先的 peak calling、motif 匹配、甲基化调用等步骤。模型输出的是系数而非直接预测结合位点。
- **算力成本**：未报告。GLM 拟合在计算上轻量，但 2209 个实验的预处理（比对、peak calling）需要中等规模计算资源。
- **历史数据依赖**：依赖已发表的 ChIP-seq、WGBS、DNase-seq 数据，数据质量参差不齐；作者用统一流程重新处理以缓解批次效应。
- **模型依赖**：依赖 CIS-BP motif 数据库和 RCADE2 预测；不同 motif 来源可能影响结果。
- **最难情形**：低可及性区域的 TF 结合信号弱，甲基化效应难以估计；motif 内无 CpG 的 TF 无法分类；ChIP-seq 抗体质量差的实验被过滤。
- **群体/领域边界**：仅人类细胞系（HEK293, GM12878, HeLa-S3, HepG2, K562, H1），不涵盖小鼠、其他物种或原代细胞；仅 CpG 甲基化，不涵盖 CHG/CHH 甲基化。
- **不确定性**：作者未提供置信区间或效应量分布；分类阈值（FDR<1×10⁻⁵）较严格，可能漏掉弱效应。

**有边界的复述**：在人类 6 个细胞系中，基于 2209 个 ChIP-seq 实验和碱基分辨率 WGBS 数据，JAMS 模型能以约 0.69 的相关性预测 CTCF 结合强度，并识别出 45% 的 TF 在体内被 CpG 甲基化抑制、6% 偏好甲基化；体外 methyl-SELEX 观察到的甲基化偏好信号在体内大多被 MBD 蛋白竞争所掩盖。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| **无法区分直接与间接效应** | JAMS 的甲基化系数可能反映 MBD 蛋白竞争或染色质状态改变的间接效应，而非 TF 与甲基化 DNA 的直接亲和力差异 | 需要结合体外实验验证直接相互作用 | Discussion 节 |
| **motif 质量依赖** | 使用已知 motif 定位 TFBS，motif 不准确会导致甲基化效应估计偏差 | 使用更全面的 motif 数据库或实验验证 motif | Methods "Formatting and preprocessing" 节 |
| **重复区域排除** | 排除了重复元件区域，可能遗漏转座子相关 TF 结合事件 | 未来可针对重复区域开发专门方法 | Methods "Formatting and preprocessing" 节 |
| **细胞系覆盖有限** | 仅 6 个细胞系，且以癌细胞系为主 | 扩展到更多正常组织与细胞类型 | Discussion 节 |
| **无法捕捉协同效应** | 模型假设各 CpG 位点效应独立，未建模位点间交互或 TF 协同结合 | 引入交互项或高阶模型 | Methods "Implementation of JAMS" 节（隐含） |
| **体内外差异的机制解释有限** | 观察到体外 methyl-plus 在体内多呈中性，但无法直接证明 MBD 竞争是唯一原因 | 需要设计实验直接操纵 MBD 水平 | Discussion 节 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| **JAMS 的甲基化系数可能被可及性中介** | 甲基化可能通过影响染色质可及性间接影响 TF 结合，而非直接改变 TF–DNA 亲和力。模型将可及性和甲基化作为独立变量，但二者高度相关 | 若中介效应存在，甲基化系数的解释将偏离"直接效应" | 使用孟德尔随机化或中介分析；或在体外系统中控制可及性 | Results 图 1F 显示可及性对信号有强效应 |
| **peak calling 的 circularity** | 使用 MACS 的 p<0.01 宽阈值可能纳入大量假阳性 peak，而 JAMS 对这些 peak 的拟合可能引入噪声 | 假阳性 peak 可能稀释真实甲基化效应 | 用更严格阈值或独立 peak caller 重复分析 | Methods "ChIP-seq data processing" 节 |
| **motif 匹配的 oracle 依赖** | 使用已知 motif 定位 TFBS 意味着无法发现新 motif 或非经典结合模式；对锌指蛋白用 RCADE2 增强，但其他家族未增强 | 若 motif 不完整，甲基化效应可能被错误归因 | 用无偏的 k-mer 或深度学习 motif 发现方法交叉验证 | Methods "Formatting and preprocessing" 节 |
| **负二项 GLM 的线性假设** | 甲基化效应可能非线性（如阈值效应），GLM 无法捕捉 | 非线性效应可能导致系数低估或方向误判 | 使用样条或树模型对比 | Methods "Implementation of JAMS" 节 |
| **体内外比较的样本量小** | 仅 76 个 TF 有体外数据，其中 methyl-plus 仅 20 个，统计功效有限 | 体内外差异的结论可能受小样本影响 | 扩大体外数据集或使用 meta 分析 | Results 图 4D |
| **未报告交叉验证的稳定性** | 仅报告了 CTCF 的 10 折交叉验证，未报告 260 个 TF 模型的稳定性或过拟合风险 | 部分 TF 的模型可能过拟合，导致甲基化分类不可靠 | 对每个 TF 报告交叉验证指标或 bootstrap 置信区间 | Results 图 1E；Methods 节 |
| **MBD 竞争解释缺乏直接证据** | 作者将体内外差异归因于 MBD 竞争，但未提供 MBD 敲低/过表达实验 | 竞争假说若错误，将影响对 methyl-plus TF 生物学意义的理解 | 在 MBD 敲低细胞中重复 JAMS 分析 | Discussion 节 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

| 知识候选 | 类型 | 可迁移性说明（面向 TF–DNA 互作 × AI/物理模拟） |
|----------|------|------------------------------------------------|
| **联合建模多个混杂因素以分离因果效应** | 方法论 | 在 TF–DNA 结合预测中，可及性、甲基化、序列高度相关。JAMS 的"同时建模背景+信号"策略可迁移到深度学习架构：在输出层同时预测 control 和 pull-down 信号，让网络自动学习去混淆表示 |
| **碱基分辨率优于区域平均** | 方法论 | 甲基化效应在位点间异质（一个 CpG 促进、另一个抑制）。对 AI 模型，输入应保留碱基分辨率甲基化而非区域平均；对 MD 模拟，应分别对每个甲基化 CpG 进行突变分析 |
| **体内外差异的竞争解释框架** | 生物学机制 | 体外测得的 TF 甲基化偏好（如 SELEX）不能直接外推至体内。对物理模拟，需在体系中加入竞争蛋白（如 MBD）才能复现体内行为；对 AI 模型，训练数据应优先使用体内数据或加入竞争特征 |
| **可解释模型的诊断价值** | 方法论 | GLM 系数可直接解释为"该 CpG 甲基化对结合的效应方向"。深度学习模型可借鉴此思路：用注意力权重或积分梯度提取每个 CpG 位点的效应，并与 JAMS 系数交叉验证 |
| **motif 质量对下游分析的影响** | 工程实践 | 对锌指蛋白等 motif 不明确的 TF，使用 RCADE2 等蛋白序列引导的 motif 预测可显著提升 peak 对齐质量。对 AI 模型，motif 对齐步骤可替换为端到端的序列编码，但需注意可解释性损失 |
| **负二项分布处理 ChIP-seq 计数** | 统计建模 | ChIP-seq 计数存在过离散，负二项优于泊松。对深度学习模型，损失函数可选用负二项似然而非 MSE，以更好匹配计数数据分布 |
| **大规模组学数据统一重处理** | 工程实践 | 2209 个实验来自多个来源，统一重处理（同一比对参数、同一 peak caller）显著提升可比性。对 AI 模型，训练数据的统一预处理管线是模型泛化的前提 |

---

## 15 与已有知识连接

| 连接对象 | 类型 | 关系说明 |
|----------|------|----------|
| **Yin et al. 2017 (methyl-SELEX)** | 直接对比 | 本文的体外对照基准。Yin 等发现 >1/3 TF 偏好甲基化 DNA；本文发现体内仅 6% 呈 methyl-plus，差异归因于 MBD 竞争。两者互补：体外测固有偏好，体内测净效应 |
| **CTCF 甲基化敏感性研究（如 Wang et al. 2012）** | 验证 | 本文 CTCF 模型中 C2pG3 的负效应与已知 CTCF 甲基化敏感性一致，验证了 JAMS 方法的有效性 |
| **CEBPB 甲基化偏好（Mann et al. 2013）** | 验证 | 本文 JAMS 检测到 CEBPB 的 methyl-plus 效应，与体外 PBM 结果一致，说明 JAMS 能捕捉真实偏好 |
| **MBD 蛋白家族（如 MeCP2、MBD1-4）** | 机制解释 | 本文用 MBD 竞争解释体内外差异。MBD 蛋白特异性结合甲基化 CpG，可能阻断 TF 结合或改变染色质状态 |
| **ENCODE 项目** | 数据来源 | 本文使用 ENCODE 的 ChIP-seq、DNase-seq、WGBS 数据，体现了公共组学数据在计算建模中的价值 |
| **RCADE2（Najafabadi et al. 2015）** | 方法依赖 | 本文用 RCADE2 推断锌指蛋白 motif，说明蛋白序列引导的 motif 预测可补充实验 motif 数据库的不足 |
| **广义线性模型在 ChIP-seq 分析中的应用（如 DESeq2）** | 方法相似 | 本文的 GLM 框架与 DESeq2 的负二项模型一脉相承，但扩展为联合建模 control 与 pull-down，并整合多类特征 |
| **深度学习 TF 结合预测（如 DeepBind、DeepSEA）** | 方法对比 | 本文的 GLM 可解释性强但表达力有限；深度学习可捕捉复杂非线性，但缺乏显式混杂控制。两者可互补：深度学习做特征发现，GLM 做因果验证 |

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：基于 JAMS 系数的深度学习正则化
- **名称**：JAMS-informed neural network regularization for TF binding prediction
- **来源局限/观察**：JAMS 是线性模型，无法捕捉序列-甲基化-可及性的非线性交互；深度学习可捕捉非线性但缺乏可解释性和混杂控制
- **核心假设**：将 JAMS 系数作为先验知识注入深度学习模型（如作为正则化项或辅助损失），可提升模型在低数据场景下的泛化能力，同时保持可解释性
- **初步方法**：训练一个 CNN 或 Transformer 预测 ChIP-seq 信号，在损失函数中加入 JAMS 系数一致性惩罚项（模型对特定 CpG 位点的梯度方向应与 JAMS 系数一致）
- **验证方式**：在本文 260 个 TF 的 JAMS 模型上训练，比较有无正则化的预测精度和甲基化效应恢复能力
- **创新状态**：unverified

### 候选 2：MBD 竞争的显式建模
- **名称**：Explicit MBD competition model for in vivo TF–DNA binding
- **来源局限/观察**：本文归因体内外差异于 MBD 竞争，但未直接建模。MBD 蛋白浓度和结合动力学可能在不同细胞类型中差异显著
- **核心假设**：在 JAMS 框架中加入 MBD 丰度作为调节变量，可以解释更多跨细胞系的差异结合
- **初步方法**：收集各细胞系的 MBD 蛋白表达量（RNA-seq/蛋白质组），在 JAMS 中加入 MBD 丰度 × 甲基化的交互项；或构建一个竞争结合模型（TF vs MBD 对同一 CpG 的竞争）
- **验证方式**：比较含/不含 MBD 交互项的模型在跨细胞系预测中的表现
- **创新状态**：unverified

### 候选 3：碱基分辨率甲基化效应的 MD 模拟验证
- **名称**：Molecular dynamics validation of base-resolution methylation effects on TF–DNA binding
- **来源局限/观察**：JAMS 提供统计关联，但缺乏物理机制解释。MD 模拟可验证特定 CpG 甲基化如何改变 TF–DNA 相互作用
- **核心假设**：JAMS 识别的高效应 CpG 位点在 MD 模拟中应显示显著的结合自由能变化
- **初步方法**：选取 5-10 个 JAMS 识别的高效应 TF–CpG 组合，进行 MD 模拟（如 GROMACS/AMBER），比较甲基化/非甲基化 DNA 与 TF 的结合自由能（MM-PBSA/MM-GBSA）
- **验证方式**：MD 预测的效应方向与 JAMS 系数是否一致
- **创新状态**：unverified

### 候选 4：JAMS 框架扩展到其他表观修饰
- **名称**：Extending JAMS to hydroxymethylation and other base modifications
- **来源局限/观察**：JAMS 仅处理 5mC；5hmC、5fC 等氧化衍生物也可能影响 TF 结合，且其分布与 5mC 不同
- **核心假设**：将 5hmC 等修饰纳入 JAMS 特征矩阵，可解释 5mC 无法解释的 TF 结合变异
- **初步方法**：使用 TAB-seq / oxBS-seq 数据获取 5hmC 信号，将其作为额外特征加入 JAMS 模型
- **验证方式**：比较含/不含 5hmC 特征的模型拟合优度
- **创新状态**：unverified

### 候选 5：JAMS 与 AlphaFold 结构预测的整合
- **名称**：Integrating JAMS methylation effects with AlphaFold-predicted TF–DNA complex structures
- **来源局限/观察**：JAMS 提供统计效应，AlphaFold 提供结构预测，但两者未整合。甲基化效应可能通过结构机制（如甲基基团与氨基酸残基的疏水接触）实现
- **核心假设**：JAMS 识别的高效应 CpG 位点在 AlphaFold 预测的 TF–DNA 复合物中应位于关键接触界面
- **初步方法**：用 AlphaFold3 预测 TF–DNA 复合物结构，将 JAMS 的甲基化效应映射到结构上，分析高效应位点的空间分布
- **验证方式**：高效应位点是否显著富集在 TF–DNA 接触界面
- **创新状态**：unverified