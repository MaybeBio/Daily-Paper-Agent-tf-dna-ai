## 01 基本信息

- **标题**：The Intervening Domain Is Required For DNA-binding and Functional Identity of Plant MADS Transcription Factors
- **作者与单位**：Xuelei Lai; Rosario Vega-Leon; Veronique Hugouvieux; Romain Blanc-Mathieu; Froukje van der Wal; Jérémy Lucas; Cátia S. Silva; Agnès Jourdain; Jose Muino; Richard Immink; Kerstin Kaufmann; François Parcy; Cezary Smaczniak; Chloe Zubieta（单位未在摘要中提供，推测为法国 CNRS/CEA Grenoble 及荷兰瓦赫宁根大学等，具体未提供）
- **期刊/预印本平台**：bioRxiv
- **年份**：2021
- **论文类型**：预印本（研究论文）
- **领域**：植物分子生物学 / 转录因子结构与功能 / 蛋白质-DNA 互作
- **关键词**：MADS transcription factor, Intervening domain, DNA-binding, protein dimerization, SEPALLATA3, seq-DAP-seq, Arabidopsis
- **DOI/arXiv 号**：10.1101/2021.03.10.434815
- **代码**：未提供
- **数据**：SEP3 MI 晶体结构已存入 PDB（代码 7NB0）；seq-DAP-seq 数据未提供公开访问链接
- **阅读日期**：未提供
- **在该方向中的位置**：本文聚焦植物 MADS 转录因子的 DNA 结合机制，核心发现是 I domain（Intervening domain）是 DNA 结合所必需的，且能改变 DNA 结合特异性与二聚化伴侣选择。该文属于「TF–DNA 结合机制」的结构生物学与生化研究，不涉及 AI/深度学习或 MD 模拟，但为 AI 方法（如结构预测、结合位点预测、蛋白质-蛋白质互作预测）提供了关键的序列-结构-功能关系数据与可迁移的领域知识。

---

## 02 一句话总结

本文通过晶体结构解析、体外 pull-down、EMSA 和 seq-DAP-seq 实验，证明植物 MADS 转录因子的 I domain（Intervening domain）是 DNA 结合所必需的，且能通过改变二聚化伴侣选择和 DNA 结合特异性来影响转录因子的功能身份。

---

## 03 研究问题

- **具体问题**：植物 MADS 转录因子的 I domain 在 DNA 结合和功能身份中扮演什么角色？I domain 是否影响 DNA 结合特异性、二聚化伴侣选择以及体内功能？
- **为什么重要**：MADS 转录因子家族在植物中高度扩张，调控多种发育过程，但其 DNA 结合域（MADS-box domain）高度保守，几乎识别相同的 CArG box 序列。理解 I domain 如何赋予功能特异性，是解释该家族功能多样性的关键。
- **现有方法为何不足**：以往研究主要关注 MADS-box domain 的 DNA 识别机制，而 I domain 的功能长期被忽视。虽然早期 domain-swap 实验提示 I domain 可能影响 DNA 结合特异性，但缺乏结构、生化和基因组水平的系统证据。
- **精确的「Can ... ?」研究问题**：Can the Intervening domain of plant MADS transcription factors modulate DNA-binding specificity and functional identity independently of the MADS-box domain?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 与 Discussion 的叙述，属于「仅本文框架」，未经外部系统核验。

1. **MADS 家族起源与分类**：MADS-box 基因家族在动植物真菌分化前已存在，分为 SRF-like（type I）和 MEF2-like（type II）两个谱系。植物中 type II 进一步分为 MIKC 和 MIKC* 亚类。
2. **DNA 结合域研究**：MADS-box domain（M domain）约 60 个氨基酸，识别 CArG box（CC(A/T)₆GG）。晶体结构显示 M domain 形成二聚体，通过 N 端柔性区域接触 DNA 大沟。
3. **功能特异性之谜**：尽管 M domain 高度保守，MADS 转录因子却调控截然不同的发育过程。早期研究提出 tetramerisation（四聚化）和三元复合物招募是功能特异性的来源。
4. **I domain 的早期线索**：20 多年前的 domain-swap 实验提示 I domain 可能影响 DNA 结合特异性，但机制不清。I domain 在 type II 中位于 M domain 与 K domain 之间，在 type I 中则直接连接 C 端。
5. **本文主张的位置**：本文通过结构、生化和基因组水平证据，将 I domain 确立为 DNA 结合模块的必需组成部分，并提出 I domain 通过稳定二聚体、改变二聚化伴侣选择和调节 DNA 结合特异性来贡献功能身份。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| MADS 转录因子功能特异性来源不明 | 高度保守的 M domain 识别几乎相同的 DNA 序列，却调控不同发育过程 | 作者认为 I domain 是被忽视的关键因素，可能通过稳定二聚体和调节 DNA 结合特异性来贡献功能身份 | Introduction 第 2-3 段；Discussion 第 1 段 |
| M domain 单独不足以实现 DNA 结合 | 体外实验中 M domain 单独无法结合 DNA | I domain 通过稳定二聚体构象，间接支持 DNA 结合 | Results 图 2F、图 3G-H；Discussion 第 2 段 |
| I domain 对 DNA 结合特异性的贡献被低估 | 以往研究聚焦 M domain 的碱基直接读取，忽略 I domain 的间接贡献 | I domain 可能通过改变二聚体几何构型或柔性，影响 DNA 结合位点的选择 | Results 图 4A-E；Discussion 第 3 段 |
| 功能身份与 DNA 结合特异性的关联不清 | 体内功能差异难以用 M domain 序列差异解释 | I domain 通过改变二聚化伴侣选择和 DNA 结合特异性，共同决定功能身份 | Results 图 4G；Discussion 第 4 段 |

---

## 06 核心思想

### 1) 表面方法

- 解析 SEP3 MI domain（M domain + I domain，残基 1-90）的晶体结构（2.1 Å，PDB 7NB0）
- 对 type I（AGL61、AGL80、PHE1）和 type II（SEP3、AP1、AG）MADS 转录因子进行体外 pull-down 和 EMSA 实验
- 构建 AP1/AG 的 I domain 嵌合体（AG IAP1），通过 seq-DAP-seq 比较 DNA 结合谱
- 在 ap1 突变体中进行体内互补实验，评估 I domain 对功能身份的影响

### 2) 核心洞察

- **I domain 是 DNA 结合模块的必需组成部分**：M domain 单独无法结合 DNA，必须与 I domain 协同才能形成稳定的 DNA 结合二聚体
- **I domain 通过稳定二聚体间接影响 DNA 结合**：I domain 形成 α 螺旋，与 M domain 的 β 折叠相互作用，稳定二聚体构象
- **I domain 改变 DNA 结合特异性**：AG IAP1 嵌合体在 seq-DAP-seq 中表现出与 AG 不同的结合位点偏好，包括新的 intersite spacing（25/34 bp vs 47/57 bp）
- **I domain 决定二聚化伴侣选择**：AG IAP1 在酵母双杂交中获得了 AP1 的部分互作伴侣，失去了 AG 的部分互作伴侣
- **I domain 是功能身份的决定因素**：AG IAP1 在 ap1 突变体中能部分互补 AP1 功能，说明 I domain 足以赋予 AP1 样功能身份

### 3) 可能的普适教训 [Analysis]

- **DNA 结合域的功能边界应重新定义**：对于多结构域转录因子，DNA 结合功能可能不局限于经典的 DBD，而应包括邻近的辅助结构域
- **结构域交换是研究功能身份的强有力工具**：将功能差异映射到特定结构域，可以在体内外同时验证
- **体外 DNA 结合谱与体内功能的相关性**：seq-DAP-seq 与 ChIP-seq 的弱相关性提示，体外结合数据需谨慎外推到体内

---

## 07 方法总览

- **输入**：
  - SEP3 MI 重组蛋白（残基 1-90）
  - type I/II MADS 转录因子的 M domain 和 MI domain 构建体
  - AP1/AG 嵌合体（AG IAP1）
  - Arabidopsis 基因组 DNA 文库（seq-DAP-seq）
- **输出**：
  - SEP3 MI 晶体结构（PDB 7NB0）
  - 蛋白-蛋白互作矩阵（酵母双杂交）
  - DNA 结合能力与特异性数据（EMSA、seq-DAP-seq）
  - 体内功能互补表型（ap1 突变体互补实验）
- **模块**：
  1. 结构生物学模块：蛋白表达纯化、结晶、X 射线衍射、结构解析与精修
  2. 生化模块：体外 pull-down、EMSA
  3. 基因组模块：seq-DAP-seq 文库构建、测序、peak calling、motif 分析
  4. 体内功能模块：拟南芥转化、表型分析、SEM 观察
- **训练**：不适用（无监督学习或模型训练）
- **工具**：XDS/XSCALE（衍射数据处理）、MXCube（数据收集）、meme-chip（PWM）、TFFM-framework、KMAC/KSM（GEM 包）、bowtie2（比对）、MACS2（peak calling）、MSPC（peak 整合）、R/ggplot2（可视化）
- **反馈回路**：seq-DAP-seq 的差异结合位点 → motif 分析 → 与 ChIP-seq 比较 → 体内功能验证
- **文字流程**：先解析 SEP3 MI 结构 → 通过 pull-down 和 EMSA 验证 I domain 对二聚化和 DNA 结合的必要性 → 构建 AG IAP1 嵌合体 → seq-DAP-seq 比较结合谱 → 酵母双杂交比较互作伴侣 → 体内互补实验验证功能身份

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| SEP3 MI 晶体结构解析 | 揭示 M domain 与 I domain 的空间关系 | 理解 I domain 如何稳定 M domain 二聚体 | 输入：SEP3 MI 蛋白；输出：2.1 Å 晶体结构（PDB 7NB0） | Results 图 1A-E；Table 1 | 无法从结构上解释 I domain 的稳定作用（实测：结构已解析，未做消融） |
| 体外 pull-down | 检测 M domain 与 MI domain 的二聚化能力 | 区分 M domain 单独是否足以形成稳定二聚体 | 输入：M/MI 构建体；输出：互作有无 | Results 图 2B-E、图 3A-F | 若移除该实验，无法直接证明 I domain 对二聚化的必要性（实测：M domain 单独不互作） |
| EMSA | 检测 DNA 结合能力 | 验证 I domain 是否为 DNA 结合所必需 | 输入：M/MI 蛋白 + CArG box DNA；输出：结合/不结合 | Results 图 2F、图 3G-H；Supplementary Figure 1 | 若移除，无法证明 I domain 对 DNA 结合的必要性（实测：M domain 单独不结合 DNA） |
| seq-DAP-seq | 全基因组水平比较嵌合体与野生型的 DNA 结合谱 | 评估 I domain 对结合特异性的贡献 | 输入：SEP3-AG 与 SEP3-AG IAP1 复合物 + 基因组 DNA；输出：peak 列表、结合强度、motif | Results 图 4A-F；Methods | 若移除，无法证明 I domain 改变结合特异性（实测：AG IAP1 有独特结合位点与 spacing） |
| 酵母双杂交 | 比较 AP1、AG、AG IAP1 的二聚化伴侣 | 评估 I domain 对互作特异性的贡献 | 输入：AP1/AG/AG IAP1 + 全部 MIKC MADS 成员；输出：互作矩阵 | Results 图 4G；Supplementary Figure 4 | 若移除，无法证明 I domain 改变伴侣选择（实测：AG IAP1 获得 AP1 特异性互作） |
| 体内互补实验 | 验证 I domain 对功能身份的影响 | 将体外发现外推到体内功能 | 输入：ap1 突变体 + AP1::AG IAP1 等构建体；输出：花器官表型 | Results 图 5-7；Supplementary Figures 5-8 | 若移除，无法证明 I domain 的功能身份贡献（实测：AG IAP1 部分互补 ap1 表型） |

---

## 09 关键公式符号

不适用。本文为实验生物学研究，未使用数学模型或公式。核心定量指标包括：

- RMSD（结构比对）：SEP3 MI 与 MEF2 结构比对 RMSD = 0.942 Å（Results 图 1A-B）
- AUC（motif 预测性能）：SEP3-AG 为 0.79，SEP3-AG IAP1 为 0.84（Results 图 4D）
- GO 富集：FDR = 4.2 × 10⁻³，carpel development 富集 7.6 倍（Results 图 4F 相关段落）

---

## 10 实验设计与证据链

**数据集/群体**：
- 结构：SEP3 MI 蛋白晶体，衍射至 2.1 Å
- 生化：type I（AGL61、AGL80、PHE1）和 type II（SEP3、AP1、AG）的 M/MI 构建体
- 基因组：seq-DAP-seq（SEP3-AG 与 SEP3-AG IAP1，各 3 个重复）
- 体内：ap1-7（强等位）和 ap1-11（中等）突变体，T1 代 >20 株/构建体

**指标**：
- 蛋白互作：pull-down 有无、酵母双杂交生长
- DNA 结合：EMSA 迁移率、seq-DAP-seq peak 数与强度
- 功能互补：花器官形态、SEM 表皮细胞特征

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| SEP3 MI 晶体结构 | I domain 形成 α 螺旋并与 M domain 相互作用 | 与 MEF2（PDB 1EGW 等）和 SRF（PDB 1HBX）结构比对 | I domain 形成 α 螺旋，与 M domain β 折叠相互作用；RMSD 0.942 Å vs MEF2 | I domain 是 MADS 折叠的组成部分 | 无法从静态结构推断动态机制 | Results 图 1；Table 1 |
| I domain 突变体 EMSA | I domain 对 DNA 结合的必要性 | SEP3 全长 vs SEP3 M domain vs SEP3 MI；R69L、R69P、Y70E 突变 | M domain 单独不结合 DNA；MI 结合；三个突变均消除 DNA 结合 | I domain 是 DNA 结合所必需 | 未测试所有可能的 I domain 突变 | Results 图 3G-H；Supplementary Figure 1 |
| Type I pull-down | I domain 在 type I 中的必要性 | AGL61 M vs AGL61 MI 与 AGL80 MI、PHE1 MI 的互作 | M domain 单独不互作；MI 互作 | I domain 对 type I 二聚化同样必要 | 仅测试了 3 个 type I 成员 | Results 图 2B-E |
| seq-DAP-seq | I domain 改变 DNA 结合特异性 | SEP3-AG vs SEP3-AG IAP1 | 6,347 peaks（SEP3-AG）vs 3,552 peaks（AG IAP1）；数百个位点差异 ≥2 倍 | I domain 改变结合位点选择 | 未做 ChIP-seq 直接验证 | Results 图 4A-F |
| Intersite spacing 分析 | I domain 影响四聚化介导的 spacing 选择 | SEP3-AG 偏好 47/57 bp；AG IAP1 偏好 25/34 bp | spacing 偏好改变 | I domain 影响 tetramer 构象 | 未直接测定 tetramer 结构 | Results 图 4E |
| 酵母双杂交 | I domain 改变二聚化伴侣 | AP1、AG、AG IAP1 vs 全部 MIKC MADS | AG IAP1 获得 AP1 特异性互作（SOC1、AGL24），失去 AG 特异性互作 | I domain 决定伴侣选择 | 未做定量互作分析 | Results 图 4G |
| ap1 互补实验 | I domain 赋予功能身份 | ap1-7 + AP1::AP1、AP1::AG、AP1::AG IAP1 | AG IAP1 恢复 66-82% 花的 4 片花瓣，AG 不能 | I domain 足以赋予 AP1 样功能 | 互补不完全，存在残留 AG 特征 | Results 图 5-7 |

---

## 11 核心结论

- I domain 是植物 MADS 转录因子 DNA 结合所必需的，M domain 单独无法结合 DNA
- I domain 通过形成 α 螺旋稳定 M domain 二聚体，间接支持 DNA 结合
- I domain 改变 DNA 结合特异性（seq-DAP-seq 显示 AG IAP1 有独特结合位点与 spacing 偏好）
- I domain 改变二聚化伴侣选择（酵母双杂交显示 AG IAP1 获得 AP1 样互作谱）
- I domain 是功能身份的决定因素：AG IAP1 在 ap1 突变体中能部分互补 AP1 功能
- 结论边界：结果基于 Arabidopsis 中的 3 个 MADS 转录因子（SEP3、AP1、AG）及 3 个 type I 成员，外推到整个 MADS 家族需谨慎

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 结构缺乏 DNA 结合状态 | SEP3 MI 晶体结构中无 DNA，无法直接观察 I domain 与 DNA 的相互作用 | 需解析 DNA 结合状态的晶体结构或进行 MD 模拟 | Discussion 第 2 段（推断，原文未明确） |
| seq-DAP-seq 与 ChIP-seq 相关性弱 | 体外结合差异与体内 ChIP-seq 仅弱相关 | 需更多体内数据验证 I domain 的贡献 | Results 图 4F 相关段落 |
| 互补不完全 | AG IAP1 在 ap1 突变体中花瓣恢复 66-82%，存在残留 AG 特征 | 需测试更多 I domain 嵌合体组合 | Results 图 6-7 |
| 泛化性未验证 | 结果基于少数 MADS 成员，未覆盖全部 106 个 Arabidopsis MADS 基因 | 需系统测试 type I 和 type II 各亚家族 | Discussion 最后一段 |
| 机制细节未阐明 | I domain 影响 tetramer 构象的分子机制未直接证明 | 需解析 tetramer 结构或进行单分子实验 | Discussion 第 3 段（推断） |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| I domain 突变体（R69L、R69P、Y70E）消除 DNA 结合，但这些残基也参与二聚体界面 | 突变可能通过破坏二聚体稳定性而非特异性机制消除 DNA 结合 | 区分「I domain 直接参与 DNA 结合」与「I domain 仅稳定二聚体」两种模型 | 进行 SEC-MALS 或 AUC 测定突变体的二聚化状态；或设计不破坏二聚体但改变 I domain 构象的突变 | Results 图 1C-D；Supplementary Figure 1 |
| seq-DAP-seq 中 AG IAP1 的 peak 数（3,552）远少于 AG（6,347） | 可能反映 I domain 改变结合特异性，也可能反映嵌合体蛋白稳定性或表达量差异 | 若为后者，则结合谱差异可能来自蛋白量而非特异性 | 检测嵌合体蛋白在体外表达量；进行蛋白定量归一化 | Results 图 4A-B |
| 酵母双杂交中 AG IAP1 获得 SOC1/AGL24 互作 | 酵母体系中的互作可能不反映植物体内真实互作 | 体内互作需 Co-IP 或 BiFC 验证 | 在植物原生质体或稳定转基因系中验证互作 | Results 图 4G |
| ap1 互补实验中 AG IAP1 互补不完全（66-82%） | 可能反映 I domain 部分贡献，也可能反映 AG 的 K/C domain 干扰 AP1 功能 | 需区分 I domain 与 K/C domain 的独立贡献 | 构建更多嵌合体（如 AP1 骨架 + AG 各 domain） | Results 图 6-7 |
| 结构解析的 SEP3 MI 无 DNA，且 N 端 18 个残基无序 | 无序的 N 端可能直接接触 DNA，其构象变化未被捕获 | 若 N 端在 DNA 结合时折叠，I domain 的稳定作用可能通过 N 端间接实现 | 解析 SEP3 MI-DNA 复合物结构或进行 HDX-MS | Results 图 1A |
| 仅用 EMSA 检测 DNA 结合，未做定量亲和力测定 | EMSA 是定性或半定量方法，无法区分亲和力变化与结合动力学变化 | 定量亲和力（Kd）可更精确评估 I domain 的贡献 | 进行荧光各向异性或表面等离子共振（SPR） | Results 图 3G-H |

---

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/深度学习/物理模拟」课题方向。

1. **DNA 结合域的功能边界应包含辅助结构域**：本文证明 I domain 是 DNA 结合所必需的，提示在 AI 预测 TF 的 DNA 结合能力时，不应仅以经典 DBD 序列为特征，而应纳入邻近结构域。可迁移到深度学习模型的输入特征设计：将 M domain + I domain 作为整体编码，而非仅 M domain。

2. **结构域交换 + 全基因组结合谱是研究 TF 特异性的强有力组合**：AG IAP1 嵌合体结合 seq-DAP-seq 揭示了 I domain 对结合特异性的贡献。该方法可迁移到 AI 辅助的 TF 结合位点预测：用嵌合体数据训练模型，可分离不同结构域对结合特异性的贡献。

3. **Intersite spacing 是 TF 复合物结合特异性的重要维度**：本文发现 I domain 改变 preferred spacing（25/34 bp vs 47/57 bp），提示在预测 TF 结合位点时，应考虑多位点协同结合的空间约束。可迁移到 AI 模型：将 spacing 分布作为特征，或生成考虑 spacing 的 synthetic promoter 用于训练。

4. **体外结合数据与体内 ChIP-seq 的相关性有限**：本文观察到体外与体内的弱相关性，提示 AI 模型在利用体外数据（如 PBM、SELEX）时需谨慎外推到体内。可迁移到模型评估：在训练集与测试集之间明确区分体外/体内数据来源。

5. **酵母双杂交可用于快速筛选 I domain 突变对二聚化伴侣选择的影响**：该方法可迁移到 AI 辅助的蛋白质-蛋白质互作预测：用酵母双杂交数据作为训练/验证集，预测 I domain 突变对互作网络的影响。

6. **晶体结构 + 热稳定性实验可评估 I domain 突变对蛋白稳定性的影响**：本文用热位移实验验证结构预测的突变效应。可迁移到 MD 模拟：用结构作为 MD 起点，模拟 I domain 突变对二聚体稳定性的影响，并与热位移数据对照。

7. **I domain 的 α 螺旋特性可用于二级结构预测验证**：本文发现 I domain 形成 α 螺旋，且序列长度约 15 个氨基酸。可迁移到 AI 结构预测：将 I domain 的 α 螺旋倾向作为先验特征，辅助 AlphaFold 等模型的预测结果验证。

---

## 15 与已有知识连接

- **MADS-box 结构域家族**：本文与已发表的 MADS 结构域结构（如 MEF2、SRF）直接相关，可连接 PDB 1EGW、1C7U、1TQE、3KOV（MEF2）和 1HBX（SRF）。这些结构可作为 MD 模拟或 AI 结构预测的参考。
- **SEP3 相关研究**：作者此前发表的 SEP3 tetramer 结构（参考文献 32、33）与本文直接衔接，本文进一步将 I domain 确立为 DNA 结合的必要组件。
- **seq-DAP-seq 方法**：该方法由作者团队此前开发（参考文献 32），本文将其应用于嵌合体比较，可连接 DAP-seq 方法学文献。
- **TF 结合特异性研究**：本文与「TF 结合特异性由 DBD 以外的结构域调控」这一新兴主题相关，可连接其他家族（如 bZIP、Homeodomain）的类似发现。
- **AI 结构预测**：本文的 SEP3 MI 结构（PDB 7NB0）可作为 AlphaFold 预测结果的验证基准，也可用于训练结构-功能关系模型。
- **候选方向（未经外部核验）**：I domain 的 α 螺旋特性与 MEF2 的「铰链区」功能相似，可能反映一种保守的 TF 调控机制，值得在 AI 辅助的跨物种比较中验证。

---

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/深度学习/物理模拟」课题方向。

### 候选 1：基于 I domain 序列的 MADS TF DNA 结合特异性预测模型
- **来源局限/观察**：本文证明 I domain 改变 DNA 结合特异性，但仅测试了少数 MADS 成员
- **核心假设**：I domain 的序列特征（长度、疏水性、电荷）可预测 MADS TF 的 DNA 结合偏好
- **增量**：将 I domain 纳入 TF 结合位点预测模型，超越仅用 M domain 的现有方法
- **初步方法**：收集 Arabidopsis 全部 106 个 MADS TF 的 seq-DAP-seq 数据，用 I domain 序列编码（one-hot + 理化性质）训练 CNN/Transformer 模型，预测结合位点偏好
- **验证方式**：留一法交叉验证；与仅用 M domain 的模型对比 AUC
- **创新状态**：unverified

### 候选 2：I domain 突变对二聚体稳定性的 MD 模拟研究
- **来源局限/观察**：本文用热位移实验验证了 R69L、R69P、Y70E 突变对稳定性的影响，但未做原子级机制分析
- **核心假设**：I domain 突变通过破坏 M domain 二聚体界面的疏水/氢键网络降低稳定性
- **增量**：提供 I domain 稳定二聚体的原子级机制解释
- **初步方法**：以 PDB 7NB0 为起点，构建 R69L、R69P、Y70E 突变体，进行 100 ns 级 MD 模拟（AMBER/CHARMM），分析二聚体界面接触面积、氢键网络、RMSF
- **验证方式**：模拟预测的稳定性变化与热位移实验数据对比
- **创新状态**：unverified

### 候选 3：I domain 介导的 intersite spacing 选择的机械模型
- **来源局限/观察**：本文发现 I domain 改变 preferred spacing（25/34 vs 47/57 bp），但机制不明
- **核心假设**：I domain 通过改变二聚体几何构型（弯曲角、扭转角）影响 tetramer 对 spacing 的选择
- **增量**：将 TF 复合物的几何约束纳入结合位点预测
- **初步方法**：用 AlphaFold 预测 SEP3-AG 与 SEP3-AG IAP1 的 tetramer 结构，比较 DNA 结合域的几何参数；用 MD 模拟 tetramer-DNA 复合物，计算不同 spacing 下的结合自由能
- **验证方式**：模拟预测的 spacing 偏好与 seq-DAP-seq 数据对比
- **创新状态**：unverified

### 候选 4：跨物种 I domain 保守性与功能多样性的比较基因组学
- **来源局限/观察**：本文仅研究 Arabidopsis，未覆盖其他植物
- **核心假设**：I domain 的序列变异与 MADS TF 的功能分化相关
- **增量**：提供 I domain 在植物进化中的功能演化视角
- **初步方法**：收集多个植物物种的 MADS TF 序列，分析 I domain 的保守性、正选择信号；用 AlphaFold 预测代表性物种的 MI domain 结构，比较几何特征
- **验证方式**：系统发育分析与结构预测的一致性
- **创新状态**：unverified

### 候选 5：I domain 作为 TF 功能身份预测的「可解释」特征
- **来源局限/观察**：本文证明 I domain 是功能身份的决定因素，但未量化其贡献
- **核心假设**：I domain 序列特征可解释 MADS TF 的功能类别（如 A/B/C/E 类）
- **增量**：为 TF 功能预测提供可解释的序列特征
- **初步方法**：用 SHAP 或注意力机制分析 I domain 中哪些残基对功能类别预测贡献最大；与本文的突变数据交叉验证
- **验证方式**：预测的功能类别与已知突变表型对比
- **创新状态**：unverified