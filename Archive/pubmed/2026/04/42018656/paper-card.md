## 01 基本信息

- **标题**：FOSL2 regulates endothelial cell state and chromatin accessibility in systemic sclerosis pulmonary vascular remodeling
- **作者与单位**：Behera, Rithika; Zhou, Yuechen; Gerges, Peter H; Fan, Jingyu; Tabib, Tracy; Gaydosik, Alyxzandria M; Huang, Mengqi; Das, Jishnu; Pachera, Elena; Hukara, Amela; Tang, Ying; Renoux, Florian; Tai, Miranda; Distler, Oliver; Kania, Gabriela; Chan, Stephen Y; Singh, Harinder; Valenzi, Eleanor; Lafyatis, Robert（单位未在摘要中提供，第一作者单位推测为匹兹堡大学，依据 Methods 中 IRB 信息）
- **期刊/预印本平台**：JCI insight
- **年份**：2026-04-22
- **论文类型**：研究论文（Research Article）
- **领域**：系统硬化症（SSc）肺血管重塑；内皮细胞（EC）状态；转录因子 FOSL2；染色质可及性；单细胞多组学
- **关键词**：FOSL2, AP-1, 内皮细胞, 系统性硬化症, 肺动脉高压, 染色质可及性, ChromBPNet, 单细胞多组学
- **DOI/arXiv 号**：10.1172/jci.insight.189107
- **代码**：未提供
- **数据**：GEO GSE302151（人类多组学数据）、GEO GSE314055（小鼠 scRNA-Seq 数据）
- **阅读日期**：2026-05-14
- **在该课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」交叉方向。核心贡献在于：① 利用单细胞多组学（RNA + ATAC）数据，通过 motif 富集（chromVAR）和 SCENIC+ 推断 FOSL2 调控网络；② 使用深度学习模型 ChromBPNet 在碱基对分辨率下预测 AP-1 结合位点的染色质可及性变化；③ 结合转基因小鼠模型（Fosl2tg）验证 FOSL2 在肺血管重塑中的因果作用。对 TF–DNA 互作课题的可迁移点：ChromBPNet 的碱基对分辨率结合贡献度分析流程、SCENIC+ 的 eRegulon 推断方法、以及「多组学 + 深度学习 + 动物模型」三线验证范式。

---

## 02 一句话总结

通过单细胞多组学（RNA + ATAC）分析 SSc-ILD-PH 患者肺组织，结合 chromVAR、SCENIC+ 和深度学习模型 ChromBPNet，鉴定出转录因子 FOSL2 在疾病内皮细胞中调控 AP-1 结合位点的染色质可及性，并在 Fosl2 转基因小鼠中验证了 FOSL2 过表达足以驱动类似人类 SSc-PH 的血管重塑表型。

---

## 03 研究问题

- **具体问题**：在 SSc-ILD-PH 的肺血管重塑中，哪些转录因子驱动内皮细胞状态转变？FOSL2 是否通过改变染色质可及性来调控下游基因表达？
- **为什么重要**：SSc-PH 是 SSc 患者的主要死因之一，但血管病变的分子机制尚不清楚。理解驱动 EC 状态转变的关键 TF 及其 DNA 结合机制，可为治疗提供新靶点。
- **现有方法为何不足**：传统 bulk 转录组无法解析细胞异质性；仅凭差异表达基因难以区分「因」与「果」；缺乏碱基对分辨率的 TF 结合位点解析，难以精确定位顺式调控元件。
- **精确的「Can ... ?」问题**：Can FOSL2 overexpression in endothelial cells drive the chromatin accessibility changes and gene expression programs observed in SSc-ILD-PH pulmonary vascular remodeling?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 和 Discussion 的引用框架，标注为「仅本文框架」，未经外部系统核验。

1. **SSc 血管病变的病理认识**：微血管 EC 损伤 → 血流减少 → 组织缺血 → 血管重塑（Raynaud、指端溃疡、PH）。EC 凋亡和功能障碍被认为是起始事件（引用 1, 2）。
2. **SSc-PH 的临床分型**：Group 1 PAH（与 ILD 无关）vs Group 3 PH（与 ILD/缺氧相关），但两者血管病变重叠，机制不明（引用 3–9）。
3. **Fosl2 转基因小鼠模型**：Maurer et al.（引用 10）建立 Fosl2tg 小鼠，显示肺血管重塑（内膜增厚、中膜肥厚、血管周围炎症），与人类 SSc-PH 相似。FOSL2 属于 AP-1 家族（Fos 蛋白），已知在 SSc 纤维化肺中过表达（引用 11–13）。
4. **单细胞多组学技术**：同时测量单细胞转录组和染色质可及性（10x Multiome），可同时解析细胞状态和调控元件活性。
5. **TF 调控网络推断工具**：chromVAR（引用 19）用于 motif 富集；SCENIC+（引用 20）用于 eRegulon 推断；CellOracle（引用 21）用于 in silico 扰动。
6. **深度学习在 ATAC-Seq 中的应用**：ChromBPNet（引用 34）可校正 Tn5 酶切偏好，并在碱基对分辨率下预测染色质可及性，结合 TF-MoDISco（引用 35）鉴定 motif。
7. **本文主张的位置**：首次将单细胞多组学 + ChromBPNet 深度学习 + 转基因小鼠验证三者结合，系统性地将 FOSL2 确立为 SSc-ILD-PH 中 EC 状态转变的关键驱动因子，并区分了缺氧依赖与非依赖通路。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| SSc-PH 分子机制不清 | 血管病变与纤维化、炎症的因果关系不明 | EC 损伤被认为是起始事件，但具体驱动因子未知 | Introduction 第 1–2 段 |
| 传统转录组无法解析细胞异质性 | bulk RNA-Seq 掩盖 EC 亚型特异性变化 | 肺组织包含多种细胞类型，EC 亚型（动脉、静脉、毛细血管）功能不同 | Results 图 1A–E |
| 差异表达基因无法区分因果 | 仅凭表达变化难以确定哪个 TF 是驱动者 | TF 表达与活性不完全相关，需结合染色质可及性和 motif 分析 | Results 图 1F–I |
| 碱基对分辨率下 TF 结合位点不明 | 无法精确定位 AP-1 在增强子/启动子上的结合变化 | 传统 peak 水平分析分辨率不足，受 Tn5 酶切偏好影响 | Results 图 8–9；Methods ChromBPNet 部分 |
| 缺氧 vs 非缺氧通路难以区分 | SSc-ILD-PH 患者常伴缺氧，但 Fosl2tg 小鼠早期无纤维化 | 需要比较 Fosl2tg 与单纯缺氧处理小鼠的 EC 基因表达 | Results 图 7；Supplemental Table 16–17 |
| 免疫细胞可能混淆 EC 表型 | T 细胞、B 细胞可能间接影响 EC 状态 | 需要 Rag2 敲除背景下的 Fosl2tg 小鼠来排除适应性免疫贡献 | Results 图 6B；Fosl2tgrag2ko 实验 |

---

## 06 核心思想

**1) 表面方法**：
- 对 SSc-ILD-PH 患者（n=9）和健康对照（n=6）的肺组织进行单细胞多组学测序（RNA + ATAC），鉴定 EC 亚型。
- 使用 chromVAR 进行 motif 富集分析，识别疾病相关 TF。
- 使用 SCENIC+ 构建 eRegulons，推断 TF→靶基因调控网络。
- 使用 CellOracle 进行 in silico FOSL2 敲除/过表达模拟。
- 在 Fosl2tg 转基因小鼠中进行 scRNA-Seq 验证。
- 在体外原代 EC 中过表达 FOSL2，进行 ATAC-Seq，并用 ChromBPNet + TF-MoDISco 在碱基对分辨率下分析 AP-1 结合变化。

**2) 核心洞察**：
- FOSL2 不仅是疾病中表达上调的 TF，更是 EC 状态转变的**驱动因子**（而非伴随现象）。
- FOSL2 通过结合 AP-1 基序（TGAGTCA）改变染色质可及性，激活血管重塑相关基因（如 ETS1、BMP4、TFEB、ITGA2）。
- FOSL2 调控的基因程序部分独立于缺氧通路，提示其是 SSc-PH 的独立驱动因素。
- FOSL2 可能通过下调 BMPR2（通过 AP-1 位点结合）参与 PAH 遗传易感性。

**3) 可能的普适教训 [Analysis]**：
- 单细胞多组学 + 深度学习基序解析的组合，可以系统性地从「相关」走向「因果」：先鉴定候选 TF，再通过转基因/过表达验证，最后用碱基对分辨率模型精确定位结合位点。
- ChromBPNet 的贡献度分析（contribution scores）提供了一种不依赖 motif 数据库的先验、直接从数据中学习 TF 结合特征的方法，这对研究非经典基序或未知 TF 尤为重要。
- 「多模型交叉验证」（chromVAR + SCENIC+ + CellOracle + ChromBPNet）比单一方法更可靠，因为每种方法有不同的偏差。

---

## 07 方法总览

- **输入**：
  - 人类：SSc-ILD-PH 患者（n=9）和健康对照（n=6）肺组织单细胞多组学（RNA + ATAC）
  - 小鼠：Fosl2tg（n=3）vs WT（n=3）肺组织 scRNA-Seq；Fosl2tgrag2ko（n=2）vs rag2ko（n=1）vs WT（n=2）肺组织 scRNA-Seq（FLEX 技术，石蜡包埋样本）
  - 体外：健康人肺原代 EC，AdV-FOSL2 感染 vs 对照，bulk ATAC-Seq
- **输出**：
  - EC 亚型注释和疾病相关细胞状态变化
  - FOSL2 eRegulon 及其靶基因/靶区域列表
  - FOSL2 过表达后染色质可及性变化的碱基对分辨率图谱
  - AP-1 基序结合变化的聚类分析（贡献度分数聚类）
- **模块**：
  1. 单细胞多组学数据处理（Cell Ranger → Seurat → Harmony 批次校正 → 聚类 → 细胞类型注释）
  2. chromVAR motif 富集分析
  3. SCENIC+ eRegulon 推断
  4. CellOracle in silico 扰动
  5. 小鼠 scRNA-Seq 差异表达和通路富集（GSEA Hallmark）
  6. 体外 ATAC-Seq + ChromBPNet 模型训练（Tn5 偏差校正 + 碱基对分辨率贡献度）
  7. TF-MoDISco 基序鉴定
  8. 贡献度分数聚类和基因组注释
- **反馈回路**：体外 FOSL2 过表达 ATAC-Seq 的 ChromBPNet 结果与人类 SSc-ILD-PH 单细胞 ATAC 数据交叉验证，确认 FOSL2 结合位点在疾病中的可及性变化。
- **文字流程**：人类多组学数据 → 鉴定 EC 亚型和 FOSL2 富集 → SCENIC+ 构建调控网络 → CellOracle 模拟扰动 → 小鼠模型验证 → 体外过表达 + ATAC-Seq → ChromBPNet 碱基对分辨率分析 → 与人类数据比对 → 结论。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 单细胞多组学聚类与 EC 亚型注释 | 解析肺组织细胞异质性，区分 EC 亚型 | 不同 EC 亚型在疾病中变化不同，bulk 分析会掩盖亚型特异性信号 | 输入：79,125 细胞多组学数据；输出：6 个 EC 亚型 | Results 图 1A–E；Supplemental Figure 2 | 无法区分动脉/静脉/毛细血管 EC 的差异响应，可能遗漏亚型特异性 FOSL2 靶基因 |
| chromVAR motif 富集 | 在 EC 亚型中鉴定差异富集的 TF 基序 | 从全基因组范围筛选候选疾病相关 TF | 输入：ATAC peak × 细胞矩阵；输出：motif 活性分数 | Results 图 1F–G；Supplemental Table 5 | 无法确定候选 TF 的因果作用，仅提供相关性 |
| SCENIC+ eRegulon 推断 | 构建 TF→增强子→基因调控网络 | 将 motif 富集转化为可检验的调控关系 | 输入：RNA + ATAC 矩阵；输出：161 个 eRegulons，含 FOSL2 eRegulon（862 区域，201 靶基因） | Results 图 2A–G；Supplemental Figure 3 | 无法区分直接与间接调控，可能包含大量假阳性靶基因 |
| CellOracle in silico 扰动 | 模拟 FOSL2 敲除/过表达对 EC 状态的影响 | 在计算层面预测 FOSL2 的因果作用 | 输入：GRN + 表达矩阵；输出：状态转移向量 | Results 图 3A–C | 预测依赖 GRN 质量，可能无法捕捉非线性效应 |
| Fosl2tg 小鼠 scRNA-Seq | 在体内验证 FOSL2 过表达对 EC 转录组的影响 | 提供因果证据 | 输入：WT vs Fosl2tg 肺 scRNA-Seq；输出：差异表达基因列表 | Results 图 4–5；Supplemental Table 9 | 无法区分 FOSL2 对 EC 的直接 vs 间接效应（通过其他细胞类型） |
| Fosl2tgrag2ko 小鼠 | 排除 T/B 细胞对 EC 表型的间接贡献 | 确认 FOSL2 对 EC 的作用不依赖适应性免疫 | 输入：Fosl2tgrag2ko vs rag2ko vs WT scRNA-Seq；输出：EC 差异表达基因 | Results 图 6B | 无法排除先天免疫细胞（如巨噬细胞）的贡献 |
| 体外 AdV-FOSL2 感染 + ATAC-Seq | 在受控系统中检测 FOSL2 过表达对染色质可及性的直接影响 | 排除体内复杂微环境的混杂因素 | 输入：原代 EC ± FOSL2 过表达；输出：bulk ATAC-Seq | Results 图 8–9 | 体外系统无法完全模拟体内微环境（如缺氧、剪切力） |
| ChromBPNet 碱基对分辨率分析 | 预测 Tn5 偏差校正后的染色质可及性，提取贡献度分数 | 在单碱基分辨率下定位 TF 结合位点 | 输入：ATAC-Seq BAM + peak；输出：贡献度分数 bigwig | Results 图 8–9；Methods ChromBPNet 部分 | 移除后只能做 peak 水平分析，无法区分同一 peak 内不同 TF 结合位点的贡献 |
| TF-MoDISco 基序鉴定 | 从贡献度分数中从头鉴定 TF 基序 | 不依赖 motif 数据库，发现未知结合位点 | 输入：贡献度分数；输出：FOS:JUN(AP-1) 基序 | Results 图 8A–B | 移除后只能依赖已知 motif 数据库，可能遗漏非经典基序 |
| 贡献度分数聚类 | 将 AP-1 结合位点按贡献度变化模式分组 | 区分疾病特异性和 FOSL2 特异性结合变化 | 输入：贡献度分数矩阵；输出：4 个聚类 | Results 图 8C | 聚类数选择可能影响生物学解释 |

---

## 09 关键公式符号

本文为实验生物学 + 计算分析论文，未提供形式化数学模型。以下列出隐含在方法中的关键计算概念：

1. **chromVAR motif 偏差校正**（隐含）：
   - 对每个细胞/peak，计算 motif 的期望可及性（基于 GC 含量、Tn5 偏差等），与实际可及性比较得到偏差分数（deviation score）。
   - 符号：`Z`（偏差分数），`E[accessibility]`（期望可及性），`observed accessibility`（实际可及性）。
   - 用途：识别在疾病 EC 中 motif 活性显著变化的 TF。
   - 来源：Methods 中引用 chromVAR（19）。

2. **SCENIC+ eRegulon 相关性**（隐含）：
   - 使用梯度提升机（Gradient Boosting Machines）评估 TF→region→gene 关系。
   - 符号：`corr(TF, region)` 和 `corr(region, gene)`，阈值 > 0.5 或 < –0.5。
   - 用途：构建 FOSL2 调控网络。
   - 来源：Methods SCENIC+ 部分。

3. **ChromBPNet 贡献度分数**（隐含）：
   - 模型：`P(accessibility | sequence) = f(sequence)`，其中 f 为深度神经网络。
   - 贡献度分数：`contribution_score(i) = ∂P / ∂x_i`（对第 i 个碱基的梯度），或使用 DeepLIFT/SHAP 类方法。
   - 用途：在碱基对分辨率下定位 AP-1 结合位点。
   - 来源：Methods ChromBPNet 部分。

4. **超几何检验**（隐含，用于 peak 与基因关联）：
   - `P(X ≥ k) = Σ (C(K,k) C(N-K, n-k)) / C(N,n)`
   - 用途：判断 peak 与基因启动子/增强子的关联是否显著。
   - 来源：未在摘要中明确，但为 SCENIC+ 标准流程。

---

## 10 实验设计与证据链

**数据集/群体**：
- 人类：SSc-ILD-PH 患者肺组织（n=9）vs 健康对照（n=6），单细胞多组学（RNA + ATAC）
- 人类验证：独立 scRNA-Seq 数据集（n=16 SSc-ILD-PH vs n=15 对照，引用 28）
- 小鼠：Fosl2tg（n=3）vs WT（n=3）scRNA-Seq；Fosl2tgrag2ko（n=2）vs rag2ko（n=1）vs WT（n=2）FLEX scRNA-Seq
- 体外：健康人肺原代 EC（n=2），AdV-FOSL2 vs 对照，bulk ATAC-Seq
- 临床：患者平均肺动脉压（mPAP）数据用于相关性分析

**指标**：
- 差异基因表达（log2FC ≥ 0.25–0.32，Padj < 0.05）
- motif 活性差异（chromVAR deviation score）
- eRegulon 活性（SCENIC+ AUC 分数）
- 染色质可及性差异（ATAC peak 强度）
- 碱基对分辨率贡献度分数差异
- 基因集富集（GSEA Hallmark，Padj < 0.05）
- 超几何重叠检验（P < 0.05）

**评测协议**：
- 人类多组学：Harmony 批次校正 → 聚类 → 亚型注释 → 疾病 vs 对照差异分析
- 小鼠验证：WT vs Fosl2tg 差异表达 → 与人类 SSc-ILD-PH 差异基因重叠分析
- 体外验证：AdV-FOSL2 vs 对照 ATAC-Seq → ChromBPNet 训练 → 贡献度分数比较
- 交叉验证：体外 FOSL2 过表达引起的染色质可及性变化与人类疾病 EC 的变化重叠

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-------------|-------------------|------|
| 单细胞多组学聚类 | SSc-ILD-PH 肺组织中存在可区分的 EC 亚型 | SSc（n=9）vs 对照（n=6） | 鉴定出 6 个 EC 亚型，静脉 EC 比例增加，动脉 EC 比例减少 | 疾病状态下 EC 亚型组成改变 | 无法确定亚型变化是原因还是结果 | Results 图 1A–E |
| chromVAR motif 富集 | AP-1 家族基序在 SSc EC 中富集 | SSc vs 对照 EC | FOS、FOSL2 基序活性显著升高 | AP-1 家族 TF 与疾病相关 | 无法区分 FOS vs FOSL2 的相对贡献 | Results 图 1F–G |
| SCENIC+ eRegulon | FOSL2 调控特定靶基因网络 | SSc vs 对照 | FOSL2 eRegulon 含 862 区域、201 靶基因，380 区域在 SSc 中更可及 | FOSL2 是疾病 EC 状态的关键调控因子 | eRegulon 为推断结果，需实验验证 | Results 图 2A–G |
| CellOracle in silico KO/过表达 | FOSL2 扰动可改变 EC 状态 | KO vs 过表达 vs 对照 | KO 使 EC 向健康状态转移，过表达向疾病状态转移 | FOSL2 是 EC 状态转变的驱动因子 | 计算预测，需体内验证 | Results 图 3A–C |
| Fosl2tg 小鼠 scRNA-Seq | FOSL2 过表达在体内驱动 EC 基因表达变化 | Fosl2tg（n=3）vs WT（n=3） | 295 基因上调，与人类 SSc-ILD-PH 差异基因显著重叠 | FOSL2 过表达足以驱动疾病相关 EC 程序 | 小鼠模型不能完全模拟人类疾病 | Results 图 4–5 |
| Fosl2tgrag2ko 小鼠 | FOSL2 对 EC 的作用不依赖 T/B 细胞 | Fosl2tgrag2ko vs rag2ko vs WT | EC 基因表达变化在无 T/B 细胞时仍存在 | FOSL2 对 EC 的作用是细胞自主的 | 不能排除巨噬细胞等先天免疫细胞贡献 | Results 图 6B |
| 体外 AdV-FOSL2 + ATAC-Seq | FOSL2 过表达直接改变染色质可及性 | AdV-FOSL2 vs 对照 | AP-1 基序处可及性增加 | FOSL2 直接结合并开放染色质 | 体外系统无法完全模拟体内微环境 | Results 图 8–9 |
| ChromBPNet + TF-MoDISco | 碱基对分辨率下 AP-1 结合位点变化 | SSc vs 对照；FOSL2-OE vs 对照 | FOS:JUN 基序（TGAGTCA）贡献度增加 | AP-1 结合位点在疾病中更活跃 | 贡献度为预测值，需 ChIP-seq 验证 | Results 图 8A–C |
| 基因-表型关联 | FOSL2 靶基因与 mPAP 相关 | 靶基因表达 vs 临床 mPAP | 部分靶基因（如 EDN1）与 mPAP 正相关 | FOSL2 靶基因与疾病严重程度相关 | 相关性不等于因果，样本量小 | Results 图 9；Supplemental Table 15 |

---

## 11 结论正确解读

- **任务范围**：本文聚焦于 SSc-ILD-PH 肺血管重塑中 EC 的转录调控机制，不涉及其他细胞类型（如平滑肌、成纤维细胞）的深入分析，也不涉及 SSc 其他器官（皮肤、肾）的病变。
- **oracle/真值输入**：FOSL2 作为候选 TF 的鉴定依赖于 chromVAR 和 SCENIC+ 的推断，并非直接测量 FOSL2 的 DNA 结合（无 ChIP-seq 数据）。ChromBPNet 的贡献度分数是模型预测，需实验验证。
- **端到端状态**：本文完成了「人类疾病数据 → 候选 TF 鉴定 → 小鼠模型验证 → 体外机制研究」的完整链条，但未进行 FOSL2 的 ChIP-seq 或 CRISPR 敲除/敲入的功能验证。
- **算力成本**：未提供具体算力信息。ChromBPNet 训练通常需要 GPU 资源，但本文未报告训练时间或硬件配置。
- **历史数据依赖**：依赖公开的 motif 数据库（如 JASPAR）和参考基因组（hg38, mm10），以及先前发表的 SSc scRNA-Seq 数据集（引用 28）。
- **模型依赖**：结论依赖于 chromVAR、SCENIC+、CellOracle、ChromBPNet 四种计算方法的准确性，每种方法均有各自的假设和偏差。
- **最难情形**：区分 FOSL2 与其他 AP-1 家族成员（FOS、FOSB、FRA-1）的贡献；区分 FOSL2 的直接 vs 间接靶基因；区分缺氧依赖 vs 非依赖通路。
- **群体/领域边界**：结论基于 SSc-ILD-PH 患者（n=9）和健康对照（n=6），样本量有限；未涵盖特发性 PAH（IPAH）或其他结缔组织病相关 PAH。
- **不确定性**：FOSL2 在 EC 中的下游靶基因是否直接介导血管重塑表型尚不明确；FOSL2 与其他 AP-1 成员的协同/拮抗关系未探索。

**有边界的复述**：在 SSc-ILD-PH 患者肺 EC 中，FOSL2 表达上调且其预测的靶基因网络被激活；Fosl2 转基因小鼠中 EC 的转录变化与人类疾病显著重叠；体外 FOSL2 过表达可增加 AP-1 基序处的染色质可及性。这些数据支持 FOSL2 是 SSc-ILD-PH 中 EC 状态转变的驱动因子，但未证明 FOSL2 单独足以引发疾病，也未排除其他 AP-1 家族成员的贡献。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 样本量有限 | 人类多组学数据仅 9 例 SSc-ILD-PH vs 6 例对照 | 未明确提及，但暗示需要更大规模验证 | Results 图 1；Supplemental Table 1 |
| 无法区分 FOS 与 FOSL2 的贡献 | chromVAR 显示 FOS 和 FOSL2 基序均富集，但无法区分 | 未明确提及 | Results 图 1F–G |
| FOSL2 靶基因的直接性未验证 | SCENIC+ 推断的靶基因未经 ChIP-seq 验证 | 未明确提及 | Results 图 2 |
| 小鼠模型与人类疾病的差异 | Fosl2tg 小鼠不能完全模拟人类 SSc-ILD-PH 的复杂性 | 未明确提及 | Results 图 4–5 |
| T 细胞/B 细胞非依赖结论的边界 | Rag2 敲除仅排除适应性免疫，不排除先天免疫 | 未明确提及 | Results 图 6B |
| 体外系统的局限性 | 原代 EC 培养无法模拟体内微环境（剪切力、缺氧、免疫细胞互作） | 未明确提及 | Results 图 8–9 |
| ChromBPNet 预测需实验验证 | 贡献度分数为模型预测，非直接结合测量 | 未明确提及 | Methods ChromBPNet 部分 |
| 缺氧 vs 非缺氧通路区分不完整 | 仅通过比较 Fosl2tg 与缺氧处理小鼠的基因表达，未直接操纵缺氧通路 | 未明确提及 | Results 图 7；Supplemental Table 16–17 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| FOSL2 基序富集不等于 FOSL2 结合 | chromVAR 检测的是基序活性，FOS、FOSB、FRA-1 等均可结合相同基序 | 若其他 AP-1 成员是实际效应因子，靶向 FOSL2 可能无效 | 进行 FOSL2 特异性 ChIP-seq 或 CUT&Tag | Results 图 1F–G |
| Fosl2tg 小鼠中 FOSL2 过表达是全局性的 | MHC1 启动子驱动的过表达不限于 EC，可能通过其他细胞类型间接影响 EC | 削弱了「FOSL2 在 EC 中直接驱动病变」的结论 | 构建 EC 特异性 FOSL2 过表达/敲除小鼠 | Methods 小鼠模型部分 |
| 体外 AdV-FOSL2 感染效率未报告 | 未提供感染效率和 FOSL2 表达水平的定量数据 | 若感染效率低，染色质可及性变化可能被低估 | 报告 MOI 验证、FOSL2 蛋白/RNA 水平 | Methods 腺病毒感染部分 |
| ChromBPNet 训练数据未详细说明 | 未报告训练集、验证集划分和模型性能指标 | 模型性能影响贡献度分数的可靠性 | 提供模型性能指标（AUROC/AUPRC） | Methods ChromBPNet 部分 |
| 未进行 FOSL2 敲低/敲除实验 | 仅有过表达实验，缺乏功能缺失实验 | 过表达可能产生非生理性效应 | 在 EC 中敲低 FOSL2 并检测染色质可及性和基因表达 | 全文未提及 |
| 与 mPAP 的相关性分析样本量小 | n=9 的相关性分析统计功效有限 | 临床相关性结论需谨慎 | 在独立队列中验证 | Results 图 9 |
| 未探索 FOSL2 的翻译后修饰 | FOSL2 活性可能受磷酸化等修饰调控 | 修饰状态可能影响 DNA 结合亲和力 | 进行磷酸化位点突变实验 | 未提及 |
| 未比较 FOSL2 与 FOS 的差异靶基因 | 两者可能调控不同的基因子集 | 若 FOS 调控不同靶基因，治疗策略需调整 | 分别进行 FOS 和 FOSL2 的 ChIP-seq 比较 | Results 图 1F–G |

---

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题方向。

1. **多组学交叉验证范式**：本文展示了「RNA + ATAC 单细胞多组学 → motif 富集 → eRegulon 推断 → in silico 扰动 → 动物模型 → 体外验证」的完整流程。对于 TF–DNA 互作研究，这种「从相关到因果」的多层验证策略可迁移到其他 TF 和疾病场景。

2. **ChromBPNet 的碱基对分辨率贡献度分析**：这是本文最值得借鉴的方法。ChromBPNet 通过深度学习模型学习序列→可及性的映射，并利用贡献度分数（类似梯度/注意力）在碱基对分辨率下定位 TF 结合位点。相比传统 peak 水平分析，该方法可以：
   - 区分同一 peak 内多个 TF 的结合位点；
   - 发现非经典基序；
   - 校正 Tn5 酶切偏好。
   对于 TF–DNA 互作课题，可迁移到任何有 ATAC-seq 数据的场景，用于精确定位 TF 结合位点。

3. **TF 结合位点的贡献度聚类**：本文将 AP-1 基序的贡献度分数进行聚类，区分了疾病特异性和 FOSL2 特异性的结合变化。这种「结合位点分型」思路可迁移到其他 TF 研究，用于区分不同细胞状态或疾病亚型中的 TF 结合模式。

4. **FOSL2 与 BMPR2 的调控关系**：本文发现 FOSL2 可能通过 AP-1 位点下调 BMPR2（遗传性 PAH 的致病基因），提示 TF 调控网络与遗传易感位点的交叉。对于 TF–DNA 互作研究，这种「TF 结合位点与疾病相关 SNP/突变重叠」的分析思路值得借鉴。

5. **缺氧依赖 vs 非依赖通路的区分策略**：通过比较 Fosl2tg 与单纯缺氧处理小鼠的基因表达，本文区分了 FOSL2 调控的缺氧依赖和非依赖通路。这种「模型间比较」策略可迁移到其他 TF 研究，用于解析 TF 在不同微环境条件下的调控差异。

6. **深度学习模型的可解释性**：ChromBPNet + TF-MoDISco 的组合展示了「深度学习预测 + 可解释性分析」的范式。对于 AI 驱动的 TF–DNA 互作研究，这种「黑盒预测 + 白盒解释」的流程是值得推广的。

7. **体外-体内一致性验证**：本文通过比较体外 FOSL2 过表达和体内疾病状态的染色质可及性变化，验证了体外模型的可靠性。这种「体外-体内交叉验证」策略可迁移到其他 TF 功能研究。

---

## 15 与已有知识连接

1. **AP-1 转录因子家族**：FOSL2（Fra-2）属于 AP-1 家族，与 FOS、FOSB、FRA-1 等形成异源二聚体。已有文献表明 AP-1 在纤维化（包括 SSc 皮肤和肺纤维化）中起关键作用（引用 11–13）。本文将其扩展到肺血管 EC 重塑。

2. **Fosl2 转基因小鼠模型**：Maurer et al.（引用 10）建立的 Fosl2tg 小鼠是 SSc 研究的经典模型，本文在此基础上进行了单细胞水平的深入分析。

3. **单细胞多组学技术**：10x Multiome 同时测量 RNA 和 ATAC，是近年兴起的核心技术。本文与先前发表的 SSc 皮肤 scRNA-seq 研究（引用 37）形成互补。

4. **ChromBPNet**：由 ENCODE 项目开发（引用 34），已在多种细胞类型中用于预测染色质可及性。本文将其应用于疾病 EC 和 FOSL2 过表达场景，扩展了其应用范围。

5. **BMPR2 与 PAH**：BMPR2 是家族性 PAH 的主要致病基因，已有大量研究关注其表达调控。本文发现 FOSL2 可能通过 AP-1 位点调控 BMPR2，为 PAH 的转录调控提供了新线索。

6. **SCENIC+ 和 CellOracle**：这两个工具分别用于 eRegulon 推断和 in silico 扰动预测，是近年单细胞调控网络分析的主流方法。本文展示了它们在疾病研究中的应用。

7. **TGF-β 信号通路**：本文 GO 分析显示 FOSL2 靶基因富集于 TGF-β 响应通路，与 SSc 纤维化中 TGF-β 的核心作用一致。

8. **缺氧与 AP-1**：已有研究表明缺氧可诱导 AP-1 活性，本文通过比较 Fosl2tg 与缺氧处理小鼠，区分了缺氧依赖和非依赖的 FOSL2 调控通路。

---

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题方向。

### 候选 1：基于 ChromBPNet 的 TF 结合位点精细定位与突变效应预测
- **名称**：TF-BindNet：碱基对分辨率下的 TF 结合位点突变效应预测
- **来源局限/观察**：本文使用 ChromBPNet 在碱基对分辨率下定位 AP-1 结合位点，但未系统评估 SNP/突变对结合亲和力的影响。已有研究表明，非编码 SNP 通过改变 TF 结合影响疾病风险。
- **核心假设**：ChromBPNet 的贡献度分数可以预测 SNP 对 TF 结合的影响，且预测结果与实验测量（如电泳迁移率变动分析 EMSA、报告基因）一致。
- **初步方法**：在本文的 ATAC-seq 数据上训练 ChromBPNet，对 FOSL2 结合位点内的所有 SNP 进行 in silico 突变，计算贡献度分数变化；与 GWAS 中 SSc/PAH 相关 SNP 重叠分析；用 EMSA 或荧光素酶报告基因验证 top 候选。
- **验证方式**：比较预测的突变效应与实验测量的结合亲和力变化；检查预测的致病 SNP 是否在 SSc/PAH 患者中富集。
- **创新状态**：unverified（需验证 ChromBPNet 在突变预测上的准确性）

### 候选 2：FOSL2 与 BMPR2 的分子动力学模拟
- **名称**：FOSL2–DNA 结合与 BMPR2 调控的分子动力学研究
- **来源局限/观察**：本文发现 FOSL2 可能通过 AP-1 位点调控 BMPR2，但未提供分子层面的结合机制。BMPR2 下调是 PAH 的关键事件。
- **核心假设**：FOSL2 与 BMPR2 内含子/启动子区域的 AP-1 位点结合，且该结合受 DNA 甲基化或染色质状态调控。
- **初步方法**：使用 AlphaFold 预测 FOSL2–JUN 异源二聚体结构，与 BMPR2 调控区域的 AP-1 基序进行分子对接；用分子动力学模拟评估结合稳定性；比较 FOSL2 与 FOS 对同一基序的结合差异。
- **验证方式**：MD 模拟预测的结合亲和力与表面等离子体共振（SPR）或等温滴定量热（ITC）实验比较。
- **创新状态**：unverified（需先确认 FOSL2 直接结合 BMPR2 调控区域）

### 候选 3：TF 结合位点的「状态转换」模型
- **名称**：EC-State-TF：基于单细胞多组学的 TF 结合状态转换建模
- **来源局限/观察**：本文发现 SSc EC 中 AP-1 结合位点的可及性增加，但未建模 TF 结合与细胞状态转换的动态关系。
- **核心假设**：TF 结合位点的可及性变化先于基因表达变化，可作为细胞状态转换的早期标志。
- **初步方法**：使用本文的单细胞多组学数据，构建 TF 结合位点可及性→基因表达的时序模型（如 RNA velocity + 染色质可及性）；用 CellOracle 模拟 FOSL2 扰动后的状态转换轨迹；与本文的 Fosl2tg 小鼠数据验证。
- **验证方式**：模型预测的状态转换轨迹与实验数据（Fosl2tg 小鼠不同时间点）比较。
- **创新状态**：unverified（需更多时间序列数据）

### 候选 4：AP-1 家族成员的差异化 DNA 结合特异性
- **名称**：AP-1 亚型特异性结合位点的深度学习识别
- **来源局限/观察**：本文无法区分 FOS 与 FOSL2 在相同基序上的结合差异。AP-1 家族成员可能具有不同的 DNA 结合偏好。
- **核心假设**：FOSL2 与 FOS 虽共享 AP-1 基序，但存在亚型特异的结合位点（如不同的侧翼序列或基序变体）。
- **初步方法**：使用本文的 ATAC-seq 数据，对 FOSL2 过表达 vs 对照的贡献度分数进行差异分析；用 TF-MoDISco 鉴定 FOSL2 特异的基序变体；用 ChIP-seq 验证 FOSL2 结合位点。
- **验证方式**：FOSL2 ChIP-seq 与预测的 FOSL2 特异位点重叠率。
- **创新状态**：unverified（需 ChIP-seq 数据）

### 候选 5：深度学习预测 TF 结合的物理化学可解释性
- **名称**：从 ChromBPNet 到物理化学：TF–DNA 结合的能量景观解析
- **来源局限/观察**：ChromBPNet 是黑盒模型，其预测的贡献度分数缺乏物理化学解释。
- **核心假设**：ChromBPNet 的贡献度分数与 TF–DNA 结合的自由能变化相关，可用于构建能量景观。
- **初步方法**：将 ChromBPNet 的贡献度分数与已知的 TF–DNA 结合自由能数据（如 Protein-DNA 结合数据库）进行关联分析；用分子动力学模拟验证 top 位点的结合自由能；构建「序列→能量→可及性」的端到端模型。
- **验证方式**：预测的自由能变化与实验测量的结合亲和力比较。
- **创新状态**：unverified（需跨学科验证）

### 候选 6：FOSL2 靶基因的增强子-启动子互作预测
- **名称**：FOSL2 介导的染色质环与增强子-启动子互作预测
- **来源局限/观察**：本文分析了 FOSL2 对染色质可及性的影响，但未涉及三维基因组结构（如增强子-启动子互作）。
- **核心假设**：FOSL2 通过改变增强子可及性来调控远距离基因表达，且这些互作在 SSc 中异常。
- **初步方法**：使用本文的单细胞多组学数据，结合 Hi-C 数据（如来自 ENCODE）预测 FOSL2 相关增强子-启动子互作；用 CRISPR 干扰（CRISPRi）验证关键互作。
- **验证方式**：CRISPRi 实验验证预测的增强子-启动子互作对基因表达的影响。
- **创新状态**：unverified（需 Hi-C 数据）