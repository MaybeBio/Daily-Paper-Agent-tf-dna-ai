## 01 基本信息

- **标题**：Functional motif detection via in silico ablation using AlphaGenome
- **作者**：Liang, Yuxuan; Dziadowicz, Sebastian A; Wang, Lei; Hu, Gangqing; Yan, Pingkun; Wang, Ge
- **单位**：未提供（根据作者信息推测为美国高校/研究机构，具体单位未在摘要中列出）
- **期刊/平台**：Briefings in Bioinformatics
- **年份**：2026（在线发表日期 2026-08-06）
- **论文类型**：方法学/工具类研究论文（含案例验证）
- **领域**：计算基因组学；转录因子–DNA 互作；深度学习序列-功能预测模型
- **关键词**：转录因子（TF）、motif 功能检测、in silico ablation、AlphaGenome、C/EBPβ、H3K27ac、CUT&RUN、多发性骨髓瘤
- **DOI/arXiv 号**：10.1093/bib/bbag422
- **代码**：https://github.com/liangyuxuan1/Motif-Detection
- **数据**：GEO accession # GSE312300（CEBPB knockout CUT&RUN H3K27ac 数据）
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」交叉方向，提出一种不依赖 TF 特异性 ChIP-seq 的 motif 功能推断框架，利用大型序列-功能基础模型 AlphaGenome 进行 in silico motif 删除扰动，并以 C/EBPβ–TSC22D3 增强子为案例，与 CUT&RUN 实验数据对照验证。该方法可迁移至其他 TF–DNA 互作的功能性 motif 鉴定任务。

---

## 02 一句话总结

本文提出一个基于 AlphaGenome 的虚拟 motif 删除框架，通过计算删除候选 C/EBPβ motif 前后预测染色质活性（H3K27ac）的变化，并以 sham 删除构建零分布来统计推断 motif 的功能贡献，在多发性骨髓瘤 TSC22D3 增强子案例中与 CEBPB knockout 的 CUT&RUN 数据部分一致。

---

## 03 研究问题

- **具体问题**：如何仅从 DNA 序列出发，无需 TF 特异性 ChIP-seq 或大规模实验扰动，即可推断哪些 TF motif 实例对增强子活性具有功能必要性（激活或抑制）？
- **为什么重要**：TF 结合 motif 的鉴定（如 FIMO 扫描）只能给出序列匹配，无法区分功能性结合与偶然匹配。实验验证（ChIP-seq、knockout、报告基因）成本高、通量低，难以规模化。若能直接从序列预测 motif 的功能贡献，将极大加速调控基因组注释和疾病非编码变异解读。
- **现有方法不足**：
  - 传统 PWM 扫描（FIMO 等）仅给出序列相似性，无法估计功能影响；
  - 监督式深度学习模型（DeepBind、DeepSEA、BPNet 等）依赖 ChIP-seq 标签，受限于抗体质量、细胞类型覆盖和训练数据规模；
  - 已有 in silico 扰动研究多聚焦于单碱基变异（如 saturation mutagenesis），而非 motif 级别的删除扰动，且缺乏系统的统计显著性评估。
- **精确研究问题（Can 问题）**：Can a large sequence-to-function model (AlphaGenome) with in silico motif ablation, coupled with a sham-deletion null distribution, identify functionally required TF motif instances from DNA sequence alone, as validated by directional concordance with CEBPB knockout CUT&RUN H3K27ac data?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论的叙述，属于「仅本文框架」，未经外部系统综述核验。

1. **第一代：基于序列统计的 motif 发现**
   - 代表方法：PWM 扫描（FIMO、TRANSFAC Match）、k-mer 模型
   - 优点：计算快、可解释、无需实验数据
   - 局限：仅给出序列匹配分数，无法判断功能必要性；阈值选择主观，假阳性/假阴性难以平衡

2. **第二代：基于 ChIP-seq 标签的深度学习预测**
   - 代表方法：DeepBind、DeepSEA、BPNet、Basenji2、Enformer
   - 优点：可从序列直接预测 TF 结合或染色质状态；BPNet 等可解析 motif 语法（间距、协同性）
   - 局限：依赖高质量 ChIP-seq 标签；跨细胞类型/物种泛化有限；预测结合 ≠ 功能必要性

3. **第三代：序列-功能基础模型 + in silico 扰动**
   - 代表方法：AlphaGenome（>7000 个人类和小鼠功能基因组 track 训练，1 Mb 窗口）
   - 本文主张的位置：将「motif 删除」作为扰动算子，以 sham 删除零分布做统计推断，将预测从「结合」推进到「功能贡献」，且无需 TF 特异性 ChIP-seq
   - 与已有 in silico 扰动（saturation mutagenesis、单碱基编辑）的区别：以 motif 实例为基本单位，直接评估删除后果

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 功能性 motif 鉴定依赖实验 | ChIP-seq 需高质量抗体和大量细胞；knockout/报告基因实验通量低 | TF 结合 ≠ 功能必要；实验成本高、难以规模化 | 引言第 1 段 |
| PWM 扫描假阳性高 | 宽松阈值捕获弱/假匹配，严格阈值漏掉低亲和但功能重要的位点 | 序列匹配分数不编码功能信息；阈值选择依赖背景模型假设 | 引言第 2 段 |
| 监督式深度学习受限于标签 | DeepBind/DeepSEA 等依赖 ChIP-seq 标签，跨条件泛化差 | 标签覆盖有限；结合标签无法区分功能与非功能结合 | 引言第 2 段 |
| 已有 in silico 扰动缺乏统计框架 | 单碱基变异分析未系统评估显著性；motif 级删除缺乏零分布 | 缺乏匹配的 sham 删除对照来刻画背景扰动分布 | Methods Step 2 |
| 模型预测与实验扰动尺度不匹配 | 模型预测单碱基/短片段效应，实验 knockout 是全局 TF 去除 | 两种扰动在生物学尺度上不同，直接比较需谨慎 | Discussion「Contextualizing model–experiment discrepancies」 |

---

## 06 核心思想

### 1) 表面方法
- 三步流水线：① 在染色质活性区域（H3K27ac peak）内用 FIMO 以宽松阈值（P ≤ 1×10⁻³）扫描 C/EBPβ motif；② 对每个候选 motif，在 AlphaGenome 的 1 Mb 输入窗口中精确删除该 motif 序列，比较删除前后预测 H3K27ac 信号的 log2 fold change（LFC）；③ 以长度匹配的 sham 删除（随机位置删除等长片段）构建经验零分布，用双侧 95% 分位数判定 motif 是否功能显著。

### 2) 核心洞察
- **删除而非突变**：完整删除 motif 避免部分序列残留带来的模型伪影，且与「该 motif 是否必要」的生物学问题直接对应。
- **sham 删除零分布**：模型对任意局部删除都有背景响应，必须用等长随机删除刻画这一背景，才能区分 motif 特异性效应与一般删除噪声。
- **方向性解读**：LFC 显著为负 → 激活型 motif；显著为正 → 抑制型 motif；不显著 → 中性。将预测从「结合」推进到「功能贡献」。
- **多 track 联合视角**：AlphaGenome 同时预测多种染色质修饰，单一 H3K27ac 可能遗漏某些 motif 的功能，需跨 track 综合判断。

### 3) 可能的普适教训 [Analysis]
- 对任何「序列-功能」深度学习模型，**匹配的扰动零分布**是区分真实效应与模型背景噪声的关键，这一思想可推广到其他基础模型（如 Enformer、Borzoi）的 in silico 分析。
- **扰动算子的选择**应直接对应生物学问题：删除对应「必要性」，替换对应「等位基因效应」，插入对应「获得功能」。
- 模型预测与实验 knockout 的尺度差异（单 motif vs 全 TF）是系统性偏差来源，比较时应聚焦方向一致性而非数值等价。

---

## 07 方法总览

- **输入**：目标基因组区域（本文为 TSC22D3 位点 60 kb 窗口）；目标 TF 的 PWM（C/EBPβ，JASPAR MA0466.3）；目标细胞类型的染色质活性信号（H3K27ac peak 定义搜索空间）；AlphaGenome 模型权重
- **输出**：每个候选 motif 的功能分类（激活/抑制/中性）及统计显著性（LFC + 95% 零分布区间）
- **模块**：
  1. **染色质活性区域定义**：基于 H3K27ac 信号的经验分布阈值（reservoir sampling，75 分位数，最小 500 bp）
  2. **Motif 提名**：FIMO 扫描，P ≤ 1×10⁻³（宽松阈值以保召回）
  3. **In silico ablation**：在 1 Mb 窗口中删除 motif，AlphaGenome 预测删除前后 H3K27ac 信号
  4. **效应量化**：局部窗口 U（宽度 1152 bp）内 LFC 计算
  5. **统计推断**：K=3000 次 sham 删除构建零分布，双侧 95% 分位数判定
  6. **实验验证**：CEBPB knockout CUT&RUN H3K27ac（RPMI 8226 细胞，DMSO/DEX 两条件）
- **训练**：AlphaGenome 为预训练模型，本文不进行微调；无新模型训练
- **反馈回路**：无在线学习；实验验证仅用于事后评估，不反馈至模型
- **文字流程**：H3K27ac peak 定义搜索空间 → FIMO 扫描提名 11 个候选 motif → 对每个 motif 构建 1 Mb 参考序列和删除序列 → AlphaGenome 分别预测 → 计算局部 LFC → 与 sham 零分布比较 → 输出功能分类 → 与 CEBPB knockout 实验数据比较方向一致性

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 染色质活性区域定义 | 限定 motif 搜索空间至推定增强子区域 | 全基因组扫描计算量大且假阳性高；聚焦活性区域提高先验概率 | 输入：H3K27ac 信号；输出：peak 区间 | Methods Step 1；Results「Motif nomination」 | 预期影响：移除后候选 motif 数量剧增，信噪比下降 [预期效应] |
| Motif 提名（FIMO 宽松阈值） | 高召回率提名候选 motif | 标准阈值（1×10⁻⁴）会漏掉弱但功能重要的位点 | 输入：peak 区间 + PWM；输出：11 个候选 motif | Results「Motif nomination」；Table 1 | 预期影响：改用严格阈值将漏掉 10/11 的弱匹配位点 [预期效应，基于作者对阈值选择的论述] |
| In silico ablation（删除 + AlphaGenome 预测） | 估计 motif 对预测活性的因果贡献 | 模型对序列编辑敏感，删除可隔离 motif 独立效应 | 输入：1 Mb 参考/删除序列；输出：预测 H3K27ac profile | Methods Step 2；Fig. 2B,C | 实测消融不可行（无消融实验）；预期影响：改用点突变可能引入部分序列残留伪影 [预期效应] |
| LFC 量化（局部窗口 U） | 将预测 profile 差异压缩为标量效应量 | 全窗口比较稀释局部效应；motif 作用具有局部性 | 输入：参考/删除预测 profile；输出：LFC 值 | Methods Step 2 公式 | 预期影响：窗口过大会稀释信号，过小会增加噪声 [预期效应] |
| Sham 删除零分布 | 刻画模型对任意等长删除的背景响应 | 模型对删除有非特异性响应，需对照才能判定显著性 | 输入：K=3000 随机位置删除的 LFC；输出：95% 分位数区间 | Methods Step 2；Supplementary | 实测消融不可行；预期影响：移除后无法区分真实效应与背景噪声 [预期效应] |
| 实验验证（CUT&RUN 比较） | 评估预测的方向一致性 | 计算预测需生物学锚点 | 输入：CEBPB KO vs 对照 H3K27ac；输出：方向一致性判断 | Results「Comparison with experimental CEBPB knockout」；Fig. 3 | 预期影响：移除后仅剩计算预测，无法评估生物学有效性 [预期效应] |

---

## 09 关键公式符号

本文核心公式为 LFC 计算（Methods Step 2）：

$$\mathrm{LFC}^{(m)} = \log_2\left(\frac{\sum_{x \in U} H_{\mathrm{ref}}(x) + \epsilon}{\sum_{x \in U} H_{\mathrm{abl}}(x) + \epsilon}\right)$$

- $m$：候选 motif 索引
- $U$：以 motif 为中心的局部评估窗口（宽度 1152 bp）
- $H_{\mathrm{ref}}(x)$：参考（未删除）序列在位置 $x$ 的 AlphaGenome 预测 H3K27ac 信号
- $H_{\mathrm{abl}}(x)$：删除 motif 后序列在位置 $x$ 的预测信号
- $\epsilon$：避免数值不稳定的极小常数

**统计判定**：$\mathrm{LFC}^{(m)}$ 与 K=3000 次 sham 删除所得 LFC 分布比较，若低于 2.5 分位数 → 激活；高于 97.5 分位数 → 抑制；否则中性。

**Motif 提名阈值**：FIMO P ≤ 1×10⁻³（宽松于常规 1×10⁻⁴）。

**Peak 定义**：reservoir sampling（采样率 0.01）估计全基因组阈值，取 75 分位数为活性 cutoff，最小 peak 长度 500 bp。

---

## 10 实验设计与证据链

### 数据集与资源
- **计算分析对象**：TSC22D3 位点 60 kb 窗口（chrX:107,670,000–107,730,000），MM.1S 细胞
- **Motif 扫描**：FIMO + CEBPB PWM（JASPAR MA0466.3），P ≤ 1×10⁻³
- **候选 motif 数**：11 个
- **AlphaGenome 预测**：H3K27ac track，1 Mb 输入窗口
- **Sham 零分布**：K=3000 次长度匹配随机删除
- **实验验证数据**：CEBPB knockout CUT&RUN H3K27ac，RPMI 8226 细胞（DMSO 和 DEX 两条件），GEO # GSE312300
- **评估指标**：方向一致性（in silico 激活/抑制 vs 实验 H3K27ac 增减）
- **超参数**：评估窗口 U = 1152 bp；peak 阈值 = 75 分位数；最小 peak 长度 = 500 bp

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| Motif 提名 | 宽松阈值可捕获标准阈值遗漏的候选 | FIMO P≤1×10⁻³ vs 常规 1×10⁻⁴ | 11 个候选中 10 个 P > 1×10⁻⁴ | 标准阈值会漏掉大多数候选 | 被捕获的弱匹配位点是否功能相关仍需验证 | Results「Motif nomination」；Table 1 |
| In silico ablation 效应分类 | 删除 motif 可产生可检测的预测信号变化 | 11 个 motif 逐一删除 vs sham 零分布 | 2 个激活（5, 7），1 个抑制（3），8 个中性 | 模型可区分 motif 特异性效应与背景噪声 | 分类的生物学准确性需实验验证 | Results「In silico motif-effect inference」；Fig. 2B,C；Table 1 |
| 多 track 一致性 | 强效应 motif 在多个染色质修饰上协调变化 | 9 个组蛋白修饰 track 的 LFC 模式 | motif 3, 5, 7 在多个 track 上显示协调效应 | 多 track 联合可增强功能推断置信度 | 未提供定量一致性指标 | Results「In silico motif-effect inference」；Fig. 2E |
| CUT&RUN 验证（DMSO） | in silico 激活 motif 在 knockout 后实验 H3K27ac 下降 | 5 个可比较 motif（DMSO peak 内）vs CEBPB KO CUT&RUN | motif 5 激活一致；motif 8 中性一致 | 部分 motif 预测与实验方向一致 | 样本量小（5 个），无法统计检验 | Results「Comparison with experimental CEBPB knockout」；Fig. 3 |
| CUT&RUN 验证（DEX） | DEX 条件下所有 motif 可比较 | 11 个 motif 均在 DEX peak 内 vs CEBPB KO CUT&RUN | motif 5, 7 激活一致；其余从预测中性/抑制变为实验激活 | DEX 诱导的全局激活掩盖 motif 特异性效应 | 无法区分 motif 内在贡献与全局 TF 去除效应 | Results「Comparison with experimental CEBPB knockout」；Fig. 3 |
| 补充案例（PPARG 位点） | 方法可推广至其他 TF/细胞类型 | 人间充质干细胞成脂分化，CEBPB ChIP-exo + H3K27ac | 5 个 ChIP-exo 支持 motif 中 1 个高置信 H3K27ac 效应；多 track 联合显示全部 5 个有更广效应 | 方法可迁移至其他位点；多 track 可恢复 ChIP-exo 支持信号 | 仅 1 个位点；非完全匹配的扰动实验 | Supplementary Section 2.1 |

---

## 11 结论正确解读

- **任务范围**：本文方法旨在**优先排序**候选 TF motif 的功能可能性，而非对所有 motif 给出确定性功能注释。输出为「激活/抑制/中性」三分类，基于统计显著性而非效应量阈值。
- **Oracle/真值输入**：AlphaGenome 为预训练模型，其预测本身是模拟信号而非实验测量。实验验证（CUT&RUN）仅用于事后方向一致性评估，不参与模型训练或阈值选择。
- **端到端状态**：方法端到端可运行（序列 → 功能分类），但验证仅覆盖 1 个主案例位点（TSC22D3）+ 1 个补充位点（PPARG），非系统性基准。
- **算力成本**：每 motif 需 2 次 AlphaGenome 前向预测（参考 + 删除），加 K=3000 次 sham 删除预测；1 Mb 窗口的 Transformer 推理成本较高，但作者未报告具体耗时。
- **历史数据依赖**：AlphaGenome 训练数据覆盖 >7000 个人类和小鼠功能基因组 track；对训练数据中未充分代表的细胞类型或物种，预测可靠性未知。
- **最难情形**：弱 motif、冗余 motif（多个 motif 功能重叠时单删除效应被缓冲）、以及位于复杂调控元件中的 motif，其单删除效应可能低于检测阈值。
- **群体/领域边界**：验证限于多发性骨髓瘤细胞系（MM.1S 预测 / RPMI 8226 验证）和人间充质干细胞；对非造血谱系、非 H3K27ac 读出、非 C/EBP 家族 TF 的推广性未验证。
- **不确定性**：模型预测与实验之间的方向不一致（如 motif 3）被归因于扰动尺度差异（单 motif 删除 vs 全 TF knockout），但作者未提供定量分解。

**有边界的复述**：在 TSC22D3 增强子案例中，AlphaGenome in silico motif 删除可识别出与 CEBPB knockout 实验方向一致的激活 motif（motif 5），但存在方向反转的案例（motif 3），且多数候选在单一 H3K27ac 读出上被分类为中性；方法作为假设生成工具的价值大于作为确定性功能注释工具的价值。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 单一位点验证 | 主案例仅 TSC22D3 一个位点，补充案例为 PPARG 位点 | 扩展到更多 TF、位点、细胞类型 | Discussion「Methodological considerations and limitations」 |
| 模型预测与实验条件不完全匹配 | MM.1S 预测 vs RPMI 8226 实验；DMSO/DEX 条件差异 | 在完全匹配的细胞系和条件下验证 | Discussion「Contextualizing model–experiment discrepancies」 |
| 单删除仅测边际贡献 | 增强子中 motif 可能功能冗余，单删除效应被缓冲 | 组合删除、多位点共删除分析 | Discussion「Methodological considerations and limitations」 |
| AlphaGenome 预测可能不准确 | 特定基因组上下文中模型误差难以检测和归因 | 开发模型不确定性估计方法 | Discussion「Methodological considerations and limitations」 |
| 验证范围有限 | 仅 H3K27ac 一种读出；未覆盖转录输出、染色质构象等 | 整合更多功能读出（RNA、3D 基因组） | Discussion「Methodological considerations and limitations」 |

**作者提及的相关约束**（非正式局限）：AlphaGenome 目前仅支持有限的造血谱系背景，不包含 RPMI 8226；MM.1S 的 TF ChIP-seq 数据未纳入模型训练，确保评估独立性，但也意味着模型可能缺乏该细胞类型的特定调控知识。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 验证样本量极小（5 个可比较 motif，DMSO 条件） | 方向一致性可能由偶然驱动；无法计算统计功效 | 核心 claim（in silico ablation 可复现实验方向）的证据强度不足 | 在更多位点、更多 motif 上系统评估方向一致性率，并与随机基线比较 | Results「Comparison with experimental CEBPB knockout」；Fig. 3 |
| 模型预测与实验在不同细胞系（MM.1S vs RPMI 8226） | 观察到的差异可能来自细胞系间调控差异而非方法误差 | 无法区分方法误差与生物学差异 | 在 AlphaGenome 支持的同一细胞系中重复 knockout 实验 | Discussion「Contextualizing model–experiment discrepancies」 |
| 11 个候选中 8 个被分类为中性 | 可能是真阴性，也可能是模型灵敏度不足或删除效应被缓冲 | 中性分类的生物学解释不明确 | 对中性 motif 进行组合删除或在不同条件下测试 | Table 1；Fig. 2 |
| 未报告 AlphaGenome 预测的校准质量 | 模型预测的绝对信号值可能系统性偏移 | LFC 的绝对值依赖模型校准 | 在已知功能/非功能 motif 基准集上评估预测校准 | Methods Step 2（未提供校准分析） |
| 未与现有方法（如 deltaSVM、DeepSEA 变异效应）直接比较 | 无法判断该框架相对已有工具的增量优势 | 方法定位需要基准比较 | 在同一数据集上运行现有工具并比较 AUC/方向一致性 | 全文未提供比较实验 |
| 补充案例（PPARG）中「多 track 联合」标准不明确 | 如何从 9 个 track 的 LFC 模式判定「更广效应」缺乏形式化定义 | 可重复性受影响 | 明确多 track 联合判定的算法或统计标准 | Supplementary Section 2.1 |
| 未讨论 AlphaGenome 的 1 Mb 窗口对删除的边界效应 | 靠近窗口边界的 motif 删除可能受 padding 影响 | 影响 LFC 估计的可靠性 | 对窗口内不同位置的 motif 进行敏感性分析 | Methods Step 2（未提供边界分析） |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **扰动零分布是序列-功能模型推断的必备组件**：任何基于深度学习模型的 in silico 扰动分析，都应构建匹配的零分布（如 sham 删除、随机突变），而非仅报告原始效应量。此思想可直接迁移至 TF–DNA 结合预测模型的 motif 功能注释任务。

2. **删除优于点突变作为 motif 必要性探针**：完整删除 motif 避免了部分序列残留的模型伪影，且与「必要性」的生物学问题直接对应。在 MD/对接模拟中，类似逻辑可应用于「删除侧链/删除接触残基」的 alanine scanning 设计。

3. **宽松阈值提名 + 统计过滤的两阶段策略**：FIMO 用 P≤1×10⁻³ 保召回，再用 in silico 效应 + 零分布过滤，比单一阈值更合理。可迁移至 TF–DNA 结合位点发现流程：先宽松扫描，再用功能预测或物理模拟（如 MD 结合自由能）做二级过滤。

4. **方向一致性而非数值等价作为验证标准**：模型扰动与实验 knockout 尺度不同，比较时应聚焦方向（激活/抑制/中性）而非效应量。对 TF–DNA 互作研究，这意味着 in silico 预测应作为假设排序工具，而非定量替代实验。

5. **多 track 联合可恢复单 track 遗漏的信号**：某些 motif 在 H3K27ac 上中性，但在其他组蛋白修饰上有效应。对 TF–DNA 研究，提示应综合多种功能读出（H3K27ac、H3K4me1、ATAC、RNA）而非依赖单一标记。

6. **模型训练数据覆盖决定可推广性边界**：AlphaGenome 仅支持有限造血谱系，跨细胞类型预测需谨慎。对 TF–DNA 结合模型，训练数据的细胞类型/物种覆盖应作为方法适用性的明确边界条件。

7. **生物学可解释的差异分析框架**：作者将 motif 3 的方向反转归因于 HDAC1 共抑制复合物，说明 in silico 扰动与实验的差异可转化为生物学假说。对 TF–DNA 研究，模型-实验差异可作为发现新调控机制的起点。

---

## 15 与已有知识连接

- **AlphaGenome**：本文使用的序列-功能基础模型，训练于 >7000 个人类和小鼠功能基因组 track，1 Mb 窗口。与 Enformer、Basenji2 同属大窗口序列-功能预测模型家族。本文将其从「变异效应预测」扩展至「motif 删除效应推断」。
- **FIMO / MEME Suite**：经典 motif 扫描工具，本文用其宽松阈值提名候选。与 PWM 扫描的局限（无法判断功能）形成对比，本文的 in silico ablation 正是为弥补此局限而设计。
- **CUT&RUN**：低细胞量染色质 profiling 技术，本文用于验证 H3K27ac 变化。与 ChIP-seq 相比，CUT&RUN 信噪比更高、所需细胞更少，适合 knockout 验证实验。
- **C/EBPβ 与 TSC22D3（GILZ）**：C/EBPβ 是亮氨酸拉链家族转录因子，在免疫和炎症中发挥重要作用；TSC22D3 编码糖皮质激素诱导的亮氨酸拉链蛋白（GILZ），是多发性骨髓瘤中糖皮质激素反应的关键靶基因。本文的案例位点连接了 TF–DNA 结合与疾病相关基因调控。
- **HDAC1 共抑制**：作者用 HDAC1 富集解释 motif 3 的预测-实验差异，连接了 TF–DNA 结合与染色质修饰酶招募的已知互作网络。
- **可迁移方向**：本文的「删除 + 零分布」框架可迁移至其他序列-功能模型（Enformer、Borzoi）的 motif 分析；「宽松提名 + 统计过滤」策略可迁移至 TF–DNA 结合位点发现；「方向一致性」验证标准可迁移至 MD 模拟与实验的对照设计。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：多模型集成 in silico motif ablation 框架
- **名称**：Cross-model ensemble ablation for TF motif functional annotation
- **来源局限/观察**：本文仅依赖 AlphaGenome 单一模型，未与其他序列-功能模型（Enformer、Borzoi）比较或集成；模型特定偏差可能影响 motif 分类
- **核心假设**：多个独立训练的序列-功能模型对同一 motif 删除的效应预测若一致，则功能注释的置信度显著高于单模型
- **初步方法**：在相同 motif 删除实验上运行 Enformer、Borzoi、AlphaGenome，比较 LFC 方向一致性；构建集成评分（如投票或平均秩）
- **验证方式**：在多个已实验验证的 TF–enhancer 位点上评估集成 vs 单模型的 AUC
- **创新状态**：unverified

### 候选 2：组合删除解析增强子内 motif 协同性
- **名称**：Combinatorial in silico ablation for motif synergy detection
- **来源局限/观察**：本文仅做单 motif 删除，作者明确承认单删除无法捕捉冗余/协同效应
- **核心假设**：增强子内多个 motif 的联合删除效应不等于单删除效应之和，非线性交互可揭示 motif 语法（间距、方向、协同）
- **初步方法**：对同一增强子内所有 motif 对进行双删除，计算交互项（LFC_double − LFC_single1 − LFC_single2）；聚类分析交互模式
- **验证方式**：与已知的 motif 协同实验（如 STARR-seq 突变扫描）对照
- **创新状态**：unverified

### 候选 3：in silico ablation 与 MD 模拟的交叉验证
- **名称**：Cross-validation of deep learning ablation with molecular dynamics binding free energy
- **来源局限/观察**：深度学习模型预测的是染色质活性变化，不直接提供 TF–DNA 结合的物理机制；MD 模拟可提供结合自由能变化但计算成本高
- **核心假设**：深度学习预测的「功能重要 motif」应与其删除后 TF–DNA 结合自由能变化（ΔΔG）显著相关
- **初步方法**：对本文 11 个 C/EBPβ motif 进行 MD 模拟（如 GROMACS + C/EBPβ–DNA 复合物结构），计算删除后 ΔΔG；与 AlphaGenome LFC 做相关分析
- **验证方式**：若相关性显著，则两种正交方法可互相校准；若不显著，则揭示深度学习预测的「功能」与「结合亲和力」的解耦
- **创新状态**：unverified

### 候选 4：跨细胞类型的 motif 功能可迁移性预测
- **名称**：Cell-type transferability of in silico motif ablation effects
- **来源局限/观察**：本文在 MM.1S 预测、RPMI 8226 验证，但未系统评估跨细胞类型的预测一致性
- **核心假设**：同一 motif 在不同细胞类型中的功能贡献可能不同，AlphaGenome 的预测可捕捉这种上下文依赖性
- **初步方法**：在 AlphaGenome 支持的所有细胞类型中运行同一组 motif 删除，构建 motif × cell type 效应矩阵；聚类分析 motif 功能的细胞类型特异性
- **验证方式**：与 ENCODE 的 TF knockout 或 CRISPR 干扰数据对照
- **创新状态**：unverified

### 候选 5：变异效应优先级的 motif-aware 策略
- **名称**：Motif-aware variant prioritization via ablation-derived functional weights
- **来源局限/观察**：本文框架可识别功能性 motif，但未延伸至疾病相关非编码变异的优先级排序
- **核心假设**：位于「功能性 motif」内的非编码变异，其调控影响显著大于位于中性 motif 内的变异
- **初步方法**：将本文的 motif 功能分类作为先验权重，整合到现有非编码变异优先级工具（如 CADD、FunSeq2）中
- **验证方式**：在 GWAS 或 ClinVar 非编码变异数据集上评估排序提升
- **创新状态**：unverified