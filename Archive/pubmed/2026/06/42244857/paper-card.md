## 01 基本信息

- **标题**：TSProm: deep learning framework to predict tissue-specific regulatory logic
- **作者与单位**：Surana, Pallavi; Dutta, Pratik; Papineni, Nimisha; Sathian, Rekha; Zhou, Zhihan; Liu, Han; Davuluri, Ramana V.（Davuluri Lab，机构信息未在摘要中提供）
- **期刊/预印本平台**：NAR Genomics and Bioinformatics
- **年份**：2026
- **论文类型**：研究论文（方法学 + 应用验证）
- **领域**：计算基因组学 / 深度学习 / 基因调控
- **关键词**：tissue-specific promoters, DNA foundation models, DNABERT2, transcription factors, explainable AI, SHAP, attention-based motif discovery
- **DOI/arXiv 号**：10.1093/nargab/lqag050
- **代码**：未提供
- **数据**：TransTExdb（人类，访问日期 2024-12-02）；Mouse BodyMap（通过 TransTEx 流程处理）；JASPAR 2024 CORE；TF-Marker；KnockTF 2.0；ENCODE ChIP-seq
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」交叉方向，核心贡献在于：(1) 将 DNA foundation model（DNABERT2）适配到组织特异性启动子分类任务；(2) 通过双模型对比设计（Model A vs Model B）分离通用启动子生物学与组织特异性调控逻辑；(3) 结合注意力机制与 SHAP 的可解释性模块，从启动子序列中识别组织特异性 TF 结合基序。对 TF–DNA 互作课题的可迁移价值在于其「对比模型设计 + 可解释性验证」的框架，可直接用于从序列中解析 TF 结合特异性。

---

## 02 一句话总结

本文提出 TSProm 框架，基于 DNABERT2 微调双模型（Model A 区分启动子与非启动子、Model B 区分组织特异性启动子与其他表达类别），通过注意力引导的基序发现与 SHAP 交叉验证，在脑、肝、睾丸三种组织中识别出组织特异性 TF 结合基序（如脑中的 SP1、MYC、HES6），并发现 C2H2 锌指蛋白是全局组织特异性调控的主导 TF 家族。

---

## 03 研究问题

- **具体问题**：能否从启动子序列（尤其是远端启动子区域）中解码组织特异性（tissue-specific, TSp）的调控逻辑，即识别决定启动子在特定组织中活跃的序列基序和 TF？
- **为什么重要**：组织特异性基因表达是发育和疾病（尤其是癌症）的核心机制。传统差异表达分析只能描述结果，无法揭示隐藏在非编码 DNA 中的"调控语法"。理解 TSp 启动子的序列逻辑有助于解释疾病中组织特异性失调的分子基础。
- **现有方法不足**：(1) 传统方法基于差异表达或标志基因，忽略非编码调控序列；(2) 多数方法聚焦核心/近端启动子，忽略远端调控区域；(3) 传统 motif 发现工具（如 XSTREME）产生大量泛组织 motif，缺乏组织特异性分辨率；(4) 深度模型常被视为"黑箱"，缺乏可解释性验证。
- **精确研究问题（Can...?）**：Can a DNA foundation model fine-tuned with a comparative dual-model design (general promoter vs tissue-specific) identify tissue-specific TF binding motifs in distal promoter regions that are clinically relevant and validated by orthogonal explainability methods (attention + SHAP)?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，标注为「仅本文框架」，未经外部系统验证。

1. **传统转录组学方法**：通过差异表达或组织标志基因定义组织特异性，但无法揭示序列层面的调控逻辑。
2. **核心/近端启动子分析**：早期方法聚焦 TSS 上下游 ±1 kb 区域，忽略远端调控元件。
3. **传统 motif 发现工具**：如 MEME/XSTREME + JASPAR 数据库比对，可识别已知 TF 基序，但产生大量泛组织 motif，缺乏组织特异性分辨率。
4. **DNA foundation models（DFMs）**：DNABERT2、Nucleotide Transformer、Gena-LM 等通过自监督预训练学习基因组序列的通用表征，可微调到下游任务。DNABERT2 采用 BPE tokenization 和 ALiBi 位置编码，支持长序列。
5. **可解释 AI（xAI）在基因组学中的应用**：注意力权重和 SHAP 值被用于解释模型预测，但多数研究仅用单一方法，缺乏交叉验证。
6. **本文主张的位置**：首次将 DFM 微调与「双模型对比设计」结合，通过 Model A（通用启动子生物学）与 Model B（组织特异性调控）的差异，精确分离 TSp 调控逻辑；并首创「注意力 + SHAP」双通道交叉验证的基序发现流程，在脑、肝、睾丸中识别出临床相关的组织特异性 TF。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 传统方法忽略远端启动子调控 | 多数研究聚焦核心/近端启动子（±1 kb），远端调控元件未被系统探索 | 远端区域序列长、信号稀疏，传统方法难以有效建模 | 作者在 Introduction 指出"most methods focus on core and proximal promoters and not distal regions"；方法中测试 −3 kb 至 +1 kb 窗口 |
| 差异表达无法揭示调控语法 | 表达谱分析只能描述哪些基因是 TSp 的，无法解释为什么 | 调控信息编码在非编码 DNA 序列中，需要序列模型解码 | Introduction："traditional expression-based methods often overlook the latent regulatory grammar embedded in non-coding DNA" |
| 传统 motif 发现缺乏组织特异性分辨率 | XSTREME 等工具在 3 kb 脑启动子上识别出 131 个 motif，但仅 7 个与 TSProm 预测重叠 | 传统工具识别泛组织 motif，无法区分组织特异性信号 | Results 节："Traditional motif analysis on 3 kb brain sequences identified 131 significant JASPAR motifs but showed minimal overlap (7 TFs) with TSProm predictions" |
| 深度模型缺乏可解释性 | 深度模型预测准确但难以理解决策依据 | 注意力权重和 SHAP 值各有局限，单一方法不可靠 | 方法中设计「注意力 + SHAP」双通道交叉验证 |
| 组织异质性导致模型泛化困难 | 不同组织可能有不同的调控逻辑，单一模型难以捕捉 | 需要对比设计分离通用与特异性信号 | 双模型设计（Model A vs Model B）即为解决此痛点 |
| 数据冗余导致过拟合 | 启动子序列间存在高度同源性 | 序列相似性高，直接微调易过拟合 | 使用 MMseqs2 以 80% 序列同一性阈值聚类去冗余 |

---

## 06 核心思想

### 1) 表面方法

- 基于 DNABERT2 预训练模型，对每个组织（脑、肝、睾丸）微调两个二分类模型：
  - **Model A**：区分 TSp 启动子 vs 随机非启动子基因组序列（捕捉通用启动子生物学）
  - **Model B**：区分 TSp 启动子 vs 非 TSp 启动子（GC 含量和重复模式匹配，捕捉组织特异性调控）
- 从 Model B 中提取注意力得分高的 token，进行基序发现；用 SHAP 值交叉验证
- 通过 B ∩ Aᶜ（Model B 独有、Model A 不关注的基序）分离组织特异性调控逻辑

### 2) 核心洞察

- **双模型对比设计**：Model A 学习"什么是启动子"，Model B 学习"什么是该组织特有的启动子"。两者的差异（B ∩ Aᶜ）精确对应组织特异性调控逻辑，而非泛启动子特征。
- **注意力 + SHAP 双通道验证**：注意力权重反映模型内部关注，SHAP 反映对预测的边际贡献，两者一致时基序可信度高。
- **远端启动子包含关键 TSp 调控信息**：−3 kb 至 +1 kb 窗口优于更短窗口，说明 TSp 调控信号分布在远端区域。

### 3) 可能的普适教训 [Analysis]

- **对比设计优于单模型**：在解析"特异性"时，训练一个通用模型和一个特异性模型并取差异，比直接训练特异性模型更有效。这一思路可迁移到 TF–DNA 结合特异性预测：训练"通用 DNA 结合模型"与"组织/条件特异性结合模型"并对比。
- **多通道可解释性交叉验证**：单一可解释性方法（仅注意力或仅 SHAP）可能产生假阳性；多方法一致时结论更可靠。在 TF 基序发现中，建议至少使用两种正交归因方法。
- **长序列窗口的价值**：TF 结合不仅发生在核心启动子，远端区域的协同结合对组织特异性至关重要。在 TF–DNA 互作建模中，应系统测试不同序列窗口的影响。

---

## 07 方法总览

- **输入**：启动子序列（人类 hg38 和 小鼠 mm39），窗口为 TSS 上游 1/2/3 kb + 下游 1 kb；组织特异性标签来自 TransTExdb（人类）和 TransTEx 流程处理 Mouse BodyMap（小鼠）
- **输出**：(1) 二分类预测（是否为 TSp 启动子）；(2) 组织特异性 TF 基序列表（含注意力得分和 SHAP 值）
- **模块**：
  1. **数据准备**：TransTEx 表达分组 → 启动子分类（TSp/TEn/Wide/Low/Null）；MMseqs2 去冗余（80% 同一性阈值）
  2. **模型微调**：DNABERT2（主模型）、Gena-LM、Nucleotide Transformer（对比模型），LoRA 微调，学习率 2e-5/1e-5/3e-5/5e-6，batch size 32/64
  3. **Model A 训练**：TSp 启动子 vs 随机非启动子序列
  4. **Model B 训练**：TSp 启动子 vs 非 TSp 启动子（GC 含量和重复模式匹配）
  5. **注意力基序发现**：提取 [CLS] token 对各 token 的注意力权重，按层平均，归一化；选择高注意力 token 作为候选基序
  6. **SHAP 验证**：KernelExplainer，以 mask token 为基线，计算各 token 对分类 logits 的边际贡献
  7. **基序注释**：MEME 进行 de novo motif 发现，TOMTOM 比对 JASPAR 2024 CORE 数据库
  8. **生物学验证**：TF-Marker（组织/细胞类型标志 TF）、KnockTF 2.0（TF 扰动表达谱）、ENCODE ChIP-seq（结合位点富集）
- **训练**：80:10:10 训练/验证/测试划分，正负样本 1:1
- **反馈回路**：注意力基序 → SHAP 验证 → JASPAR 注释 → 生物学数据库验证 → 最终 TF 列表
- **假设**：(1) 组织特异性启动子的序列特征可被 transformer 模型捕捉；(2) 注意力权重和 SHAP 值能反映真实的 TF 结合基序；(3) 双模型对比能有效分离通用与特异性调控逻辑

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| TransTEx 表达分组 | 将启动子按组织表达模式分为 TSp/TEn/Wide/Low/Null | 提供组织特异性标签，是监督学习的金标准 | 输入：转录本表达矩阵；输出：启动子分类标签 | 方法节描述；基于已发表 TransTEx 方法 | 预期影响：无标签则无法训练分类模型 [预期效应] |
| MMseqs2 去冗余 | 以 80% 序列同一性聚类，保留代表性序列 | 减少序列冗余，防止过拟合和评估偏差 | 输入：启动子序列集；输出：非冗余代表序列集 | 方法节 "Tackling data redundancy" | 预期影响：不去冗余会导致训练/测试泄漏，指标虚高 [预期效应] |
| DNABERT2 微调（LoRA） | 将预训练 DNA 语言模型适配到 TSp 分类任务 | 利用预训练知识，LoRA 降低微调成本 | 输入：启动子序列；输出：二分类 logits | Results 图 2A：DNABERT2 优于 Gena-LM 和 NT | 移除后无基础模型，需从头训练，性能显著下降 [预期效应] |
| Model A（通用启动子模型） | 区分 TSp 启动子 vs 随机非启动子 | 建立"什么是启动子"的基线 | 输入：TSp 启动子 + 随机基因组序列；输出：二分类 | Results：F1 = 0.85–0.95 | 移除后无法区分通用 vs 特异性特征 [预期效应] |
| Model B（组织特异性模型） | 区分 TSp 启动子 vs 非 TSp 启动子（匹配 GC/重复） | 捕捉组织特异性调控信号 | 输入：TSp 启动子 + 匹配的非 TSp 启动子；输出：二分类 | Results：F1 ≈ 0.8 | 移除后无法识别组织特异性基序 [预期效应] |
| 注意力基序提取 | 从 [CLS] 注意力权重中识别高关注 token | 定位模型决策依赖的序列区域 | 输入：模型注意力权重；输出：候选基序列表 | 方法节 "Attention-based motif discovery"；Results 图 3A | 移除后无候选基序来源 [预期效应] |
| SHAP 分析 | 计算各 token 对预测的边际贡献 | 交叉验证注意力基序，排除注意力假阳性 | 输入：模型 logits + 背景分布；输出：token 级 SHAP 值 | 方法节 "Validation of motifs: SHAP analysis"；Results 图 3D | 移除后基序缺乏独立验证，可信度降低 [预期效应] |
| MEME + TOMTOM 注释 | de novo motif 发现 + JASPAR 数据库比对 | 将序列基序映射到已知 TF 结合位点 | 输入：候选基序序列；输出：TF 注释 | 方法节；Results：69/82 motif 匹配 JASPAR | 移除后无法将基序关联到具体 TF [预期效应] |
| 生物学数据库验证 | TF-Marker、KnockTF 2.0、ENCODE ChIP-seq 交叉验证 | 确认基序的生物学相关性和临床意义 | 输入：TF 列表；输出：组织特异性/疾病关联证据 | Results：SP1 在胶质瘤中的临床关联；ENCODE ChIP-seq 富集 | 移除后基序仅具计算意义，缺乏实验支持 [预期效应] |

---

## 09 关键公式符号

**1. 注意力权重计算（[CLS] 对 token j 的注意力）**

$$\alpha_j = \frac{\exp(q^* \cdot k_j / \sqrt{d})}{\sum_{i=1}^{J} \exp(q^* \cdot k_i / \sqrt{d})}$$

- $q^*$：[CLS] token 对应的 query 向量
- $k_j$：第 j 个 BPE token 的 key 向量
- $d$：隐藏维度
- $J$：序列中 token 总数
- $\alpha_j$：第 j 个 token 的注意力权重，量化 [CLS] 对 token j 的关注程度

**2. 归一化注意力得分**

$$\hat{s}_j = \frac{\alpha_j}{\max_i \alpha_i}$$

- $\hat{s}_j$：归一化后的注意力得分，范围 [0, 1]

**3. 层特异性得分（z-score）**

$$z_j = \frac{\hat{s}_j - \mu}{\sigma}$$

- $\mu, \sigma$：该层所有 token 注意力得分的均值和标准差
- $z_j$：token j 的层特异性得分，用于识别显著高注意力 token

**4. 超几何检验（motif 富集）**

$$P(X = k) = \frac{\binom{K}{k} \binom{N-K}{n-k}}{\binom{N}{n}}$$

- $N$：总序列数
- $K$：阳性（TSp）序列数
- $n$：含 motif 的序列数
- $k$：阳性序列中含 motif 的序列数
- 用于检验 motif 在阳性 vs 阴性序列中的富集显著性

**5. SHAP 值（Shapley 值）**

$$\phi_j = \sum_{S \subseteq F \setminus \{j\}} \frac{|S|! (|F| - |S| - 1)!}{|F|!} [f(S \cup \{j\}) - f(S)]$$

- $F$：所有特征（token）集合
- $S$：不含 token j 的特征子集
- $f(S)$：模型在特征子集 S 上的预测
- $\phi_j$：token j 对预测的边际贡献

**6. 95% 置信区间**

$$CI = 1.96 \times \frac{\sigma}{\sqrt{n}}$$

- $\sigma$：SHAP 值标准差
- $n$：token 出现次数

---

## 10 实验设计与证据链

### 数据集与设置

| 项目 | 详情 |
|------|------|
| 人类数据 | TransTExdb（访问日期 2024-12-02），hg38 基因组 |
| 小鼠数据 | Mouse BodyMap，mm39 基因组，通过 TransTEx 流程处理 |
| 组织 | 脑、肝、睾丸（基于 TSp 转录本数量选择） |
| 序列窗口 | −3 kb 至 +1 kb、−2 kb 至 +1 kb、−1 kb 至 +1 kb（相对 TSS） |
| 表达分组 | TSp / TEn / Wide / Low / Null（5 类） |
| 正负样本 | 1:1 比例 |
| 数据划分 | 训练:验证:测试 = 80:10:10 |
| 去冗余 | MMseqs2，80% 序列同一性阈值 |
| 模型 | DNABERT2（主）、Gena-LM、Nucleotide Transformer（对比） |
| 微调 | LoRA，学习率 {2e-5, 1e-5, 3e-5, 5e-6}，batch size {32, 64} |
| 硬件 | NVIDIA A40 GPU |
| 对比方法 | iPro-WAEL（集成随机森林 + CNN）、iChrom-deep-focal（序列 CNN） |
| 验证数据库 | JASPAR 2024 CORE、TF-Marker、KnockTF 2.0、ENCODE ChIP-seq（~4000 文件，~700 实验） |
| 传统 motif 工具 | XSTREME + JASPAR2026_CORE_vertebrates_non_redundant |

### 实验表格

| 实验 | 检验的 Claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 模型性能对比 | DFM 微调优于传统深度学习方法 | DNABERT2 vs Gena-LM vs NT vs iPro-WAEL vs iChrom-deep-focal；3 种序列长度 × 3 组织 | DNABERT2 和 Gena-LM 性能相近且最优；NT 最差；传统方法显著低于 DFM | DFM 能有效捕捉启动子序列特征 | 未报告具体数值，无法判断效应量 | Results 图 2A；Appendix D 表 S2、S3 |
| 序列窗口测试 | 更长窗口包含更多 TSp 调控信息 | −1 kb/+1 kb vs −2 kb/+1 kb vs −3 kb/+1 kb | 更长窗口性能更优（F1 约 80%） | 远端启动子区域包含 TSp 调控信号 | 未报告各窗口具体数值差异 | Results 图 2A |
| Model A vs Model B | 对比设计可分离通用与特异性调控 | Model A（TSp vs 随机）F1 = 0.85–0.95；Model B（TSp vs 匹配非 TSp）F1 ≈ 0.8 | Model A 更易分类，Model B 更具挑战性 | Model B 捕捉的是更精细的组织特异性特征 | 未报告各组织的单独性能 | Results 节 |
| 注意力基序发现 | 注意力可识别 TSp 相关基序 | 脑组织 Model B，82 个显著 motif，69 个匹配 JASPAR | 高比例 motif 映射到已知 TF | 注意力机制能有效定位 TF 结合基序 | 未报告 motif 长度分布和具体序列 | Results 节；图 3A |
| SHAP 交叉验证 | SHAP 与注意力一致 | 注意力高得分 token 的 SHAP 值 | 高 SHAP 值集中在已知 TFBS 区域（−1600 至 +500 bp） | 双通道验证增强基序可信度 | 未报告注意力与 SHAP 的一致性系数 | Results 图 3B–D；Appendix F2 |
| 脑组织 TF 识别 | 识别临床相关的脑 TSp TF | SP1、MYC、HES6 等 | SP1 在胶质瘤中有已知临床关联；HES6 与神经母细胞瘤相关 | TSProm 识别的 TF 具有疾病相关性 | 未做因果验证，仅关联性 | Results 节；TF-Marker、KnockTF 2.0 交叉验证 |
| 基序位置分析 | TSp 基序在启动子上的位置偏好 | motif-TSS 距离分布 | 注意力富集在 −1400 至 +500 bp 区域 | TSp 调控信号集中在 TSS 近端及上游远端 | 未报告各组织的具体分布差异 | Results 图 3B–C |
| 全局 TF 家族分析 | C2H2 锌指是主导家族 | 所有组织的显著 motif 按 TF 家族分类 | C2H2 ZNF 占最大比例（20/82 脑组织 motif） | C2H2 ZNF 是 TSp 调控的主导家族 | 未报告各家族的具体比例和统计检验 | Results 节；图 4A |
| ENCODE ChIP-seq 验证 | 预测基序与实验结合位点重叠 | TSProm 预测区域 vs ENCODE ChIP-seq peaks | 显著富集 | 预测基序具有实验支持 | 未报告富集倍数和 P 值 | Results 节；Appendix F4 图 S5 |
| 睾丸组织验证 | 框架可泛化到其他组织 | 睾丸 TSp 启动子，RFX1/2/3、Patz1、SP2、SP5 等 | 识别出睾丸特异 TF（如 RFX2 参与精子发生） | 框架具有跨组织泛化能力 | 未报告睾丸组织的 motif 数量和匹配率 | Results 节；Appendix G 图 S6、表 S7 |

---

## 11 结论正确解读

- **任务范围**：本文解决的是**启动子序列的二分类任务**（是否为组织特异性启动子），而非直接预测 TF 结合位点或结合亲和力。识别的"motif"是模型注意力 + SHAP 推断出的调控元件，并非实验验证的结合位点。
- **Oracle/真值输入**：组织特异性标签来自 TransTExdb（基于 GTEx 表达数据）和 Mouse BodyMap，属于**表达层面的定义**，而非直接的调控实验证据。模型学到的是"与 TSp 表达相关的序列特征"，不一定是因果性的 TF 结合位点。
- **端到端状态**：TSProm 是**端到端可训练的**（序列 → 分类），但 motif 发现是**事后分析**（post-hoc），不参与训练。
- **算力成本**：使用 LoRA 微调降低显存需求，NVIDIA A40 GPU；具体训练时间和资源未报告。
- **历史数据依赖**：依赖 TransTExdb 的表达分组质量；GTEx 是 bulk 组织数据，无法区分细胞类型异质性。
- **模型依赖**：主模型为 DNABERT2；Gena-LM 和 NT 作为对比。结论可能依赖 DNABERT2 的预训练策略（BPE + ALiBi）。
- **最难情形**：Model B（匹配 GC/重复的负样本）F1 仅约 0.8，说明组织特异性信号与背景序列区分难度较高；睾丸和肝的 motif 识别效果未详细报告。
- **群体/领域边界**：仅覆盖人类和小鼠的三种组织（脑、肝、睾丸）；结论外推到其他组织或物种需谨慎。
- **不确定性**：注意力与 SHAP 的交叉验证是计算层面的，缺乏湿实验验证（如报告基因、EMSA、ChIP-qPCR）。作者在 Discussion 中承认需要"future targeted experimental validations to establish direct regulatory causality"。

**有边界的复述**：TSProm 在人类和小鼠的脑、肝、睾丸启动子上，通过 DNABERT2 微调双模型，能以约 80–95% 的 F1 区分组织特异性启动子，并识别出与已知 TF（如 SP1、MYC、HES6、RFX2）一致的候选基序，但这些基序的因果性尚未经实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 缺乏因果验证 | 注意力/SHAP 推断的 TF 基序是关联性的，未建立直接调控因果关系 | 使用报告基因实验、ChIP-seq、靶向突变 + 表达分析验证 | Discussion 节 |
| 组织异质性 | 使用 bulk 组织数据，无法区分细胞类型特异性效应 | 未来可扩展到单细胞分辨率数据 | Discussion 节（隐含） |
| 物种覆盖有限 | 仅人类和小鼠 | 可扩展到更多物种 | Discussion 节："can be extended to more primate species" |
| 数据质量依赖 | 受限于转录组注释的完整性和准确性 | 随更高质量注释数据更新 | Discussion 节（隐含） |
| 关联性而非因果性 | TF 基序与疾病（如胶质瘤）的关联是文献层面的，非直接实验证据 | 需要功能实验验证 | Results 节（SP1 讨论部分） |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 双模型对比的"减法"逻辑 | B ∩ Aᶜ 的基序可能包含 A 模型未学到的**通用**启动子特征（因 A 的负样本是随机基因组，而非非 TSp 启动子），而非真正的 TSp 特征 | 若 A 的负样本设计不当，B ∩ Aᶜ 可能混杂非特异性信号 | 将 A 的负样本改为非 TSp 启动子（如 Wide 组）重新训练，比较基序差异 | 方法节 Model A 定义：负样本为"randomly selected genomic locations outside promoter sequences" |
| 注意力作为可解释性的有效性 | 注意力权重高 ≠ 因果重要性；transformer 的注意力可能受 token 频率、位置等混淆因素影响 | 若注意力基序是伪相关，后续生物学解读将失真 | 用输入扰动（如 in-silico mutagenesis）或集成梯度替代/补充注意力 | 方法节仅用注意力 + SHAP，未用梯度方法 |
| SHAP KernelExplainer 的计算可行性 | KernelExplainer 是精确但计算密集的方法，在长序列（4 kb）上可能近似误差大 | 若 SHAP 估计不准确，交叉验证的可信度降低 | 报告 SHAP 近似的误差界或使用更高效的 DeepExplainer / GradientExplainer | 方法节 "SHAP KernelExplainer" |
| 负样本 GC/重复匹配的充分性 | 仅匹配 GC 含量和重复模式可能不足以控制所有混淆因素（如 CpG 密度、染色质状态） | 若混淆因素未控制，识别的"TSp 基序"可能反映的是序列组成差异而非调控逻辑 | 增加额外匹配标准（如 CpG 密度、k-mer 频率分布） | 方法节 Model B 定义 |
| 三组织选择的代表性 | 脑、肝、睾丸是 TSp 转录本最多的组织，但可能不代表所有 TSp 调控模式 | 结论可能偏向高 TSp 组织的调控逻辑 | 扩展到更多组织（如心脏、肾）验证 | 方法节 "focused on three representative tissues based on the number of TSp transcripts" |
| 与 XSTREME 的比较方式 | 传统工具识别 131 个 motif 而 TSProm 识别 19 个 TF，但未报告召回率（TSProm 是否遗漏了真实 TSp motif） | 若 TSProm 过度筛选，可能丢失重要调控信息 | 用已知 TSp 调控元件（如 ENCODE 组织特异性增强子）作为金标准，计算召回率 | Results 节 "Traditional motif analysis...131 significant...only 7 overlapping" |
| 性能指标未报告具体数值 | 摘要和 Results 仅报告 F1 范围（0.85–0.95 和 ~0.8），未给出精确值、标准差、显著性检验 | 无法评估模型间差异的统计显著性 | 补充各模型的精确指标和置信区间 | Results 图 2A；Appendix D 表 S2、S3 |

---

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质–DNA 互作（聚焦 TF–DNA 结合机制）× AI/物理模拟」课题。

### 可迁移的概念

1. **双模型对比设计（Dual-model contrastive design）**：训练一个"通用"模型（区分目标 vs 随机背景）和一个"特异性"模型（区分目标 vs 匹配对照），取两者差异可精确分离目标特异性特征。**迁移到 TF–DNA 结合**：训练"通用 DNA 结合模型"（结合 vs 随机序列）与"组织/条件特异性结合模型"（该组织结合 vs 其他组织结合），差异基序即为条件特异性结合逻辑。

2. **注意力 + SHAP 双通道交叉验证**：两种正交的可解释性方法一致时，基序可信度显著提高。**迁移**：在预测 TF 结合位点时，可同时使用注意力权重和 SHAP 值筛选候选位点，降低单方法的假阳性率。

3. **长序列窗口的价值**：TSp 调控信号分布在 TSS 上游 3 kb 范围内，远超传统核心启动子区域。**迁移**：TF 结合预测不应局限于核心 motif 区域，应考虑远端协同结合元件。

4. **负样本匹配策略**：Model B 的负样本匹配 GC 含量和重复模式，迫使模型学习真正的调控差异而非序列组成差异。**迁移**：在构建 TF 结合预测训练集时，负样本应匹配正样本的 GC 含量、CpG 密度等混淆因素。

### 可迁移的方法

1. **LoRA 微调 DNA foundation model**：在有限标注数据下高效适配预训练模型，适合小样本 TF 结合数据。
2. **超几何检验筛选 motif 富集**：简单有效的统计检验，可用于评估候选 TF 基序在目标序列集中的富集显著性。
3. **B ∩ Aᶜ 集合运算分离特异性特征**：通过集合运算从两个模型的预测中提取独有特征，适用于任何"特异性"分析任务。

### 可迁移到 TF–DNA 互作课题的具体思路

- **TF 结合特异性预测**：对每个 TF，训练 Model A（该 TF 结合 vs 随机序列）和 Model B（该 TF 结合 vs 其他 TF 结合），B ∩ Aᶜ 基序可揭示该 TF 的独特结合偏好。
- **组织特异性 TF 协同**：TSProm 识别的组织特异性启动子区域可作为候选增强子/启动子互作区域，与 3D 基因组数据（Hi-C）整合，研究组织特异性 TF 协同结合。
- **与物理模拟结合**：TSProm 识别的高置信度 TF 基序可作为 MD 模拟或分子对接的初始结合位点，减少搜索空间。
- **变异效应预测**：TSProm 的 SHAP 值可量化单核苷酸变异对组织特异性启动子分类的影响，用于预测非编码突变对 TF 结合的破坏效应。

---

## 15 与已有知识连接

- **DNABERT2**（Zhou et al., 2023）：TSProm 的基础模型。DNABERT2 采用 BPE tokenization 和 ALiP 位置编码，在 16 个物种的基因组上预训练。TSProm 验证了 DNABERT2 可有效微调到启动子分类任务。
- **Nucleotide Transformer**（Dalla-Torre et al., 2023）：对比模型之一，基于 BERT 架构，在 3200 个人类基因组和 850 个其他物种基因组上预训练。TSProm 发现其在 TSp 启动子分类上略逊于 DNABERT2。
- **Gena-LM**（Fishman et al., 2023）：对比模型之一，基于 BigBird 稀疏注意力，支持超长序列。TSProm 发现其与 DNABERT2 性能相近。
- **TransTEx**（Zhou et al., 2021）：TSProm 的标签来源。TransTEx 基于 GTEx 数据将启动子分为 TSp/TEn/Wide/Low/Null 五类，TSProm 直接复用了该分类体系。
- **JASPAR 2024 CORE**（Rauluseviciute et al., 2024）：TF 结合位点数据库，TSProm 用于 motif 注释。
- **TF-Marker**（Zhang et al., 2020）：组织/细胞类型标志 TF 数据库，TSProm 用于验证 TF 的组织特异性。
- **KnockTF 2.0**（Feng et al., 2024）：TF 敲除/敲低表达谱数据库，TSProm 用于验证 TF 的疾病相关性。
- **ENCODE ChIP-seq**：实验验证 TF 结合位点，TSProm 用于验证预测基序的富集。
- **MEME / XSTREME**（Bailey, 2021）：传统 de novo motif 发现工具，TSProm 用于对比验证。
- **SHAP**（Lundberg & Lee, 2017）：博弈论解释方法，TSProm 用于 token 级归因。

---

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质–DNA 互作（聚焦 TF–DNA 结合机制）× AI/物理模拟」课题。

### 候选 1：TF 特异性双模型对比框架（TF-DualContrast）

- **名称**：TF-DualContrast：基于双模型对比的 TF 结合特异性解析
- **来源局限/观察**：TSProm 的双模型设计（Model A vs Model B）有效分离了通用启动子与组织特异性调控，但仅用于启动子分类，未直接用于 TF 结合位点预测。现有 TF 结合预测模型（如 DeepBind、BPNet）多为单模型，难以区分"通用结合"与"条件特异性结合"。
- **核心假设**：对每个 TF，训练"通用结合模型"（该 TF 结合 vs 随机序列）和"特异性结合模型"（该 TF 结合 vs 其他 TF 结合），B ∩ Aᶜ 基序可揭示该 TF 的独特结合偏好，优于单模型预测。
- **初步方法**：基于 DNABERT2 或 BPNet 架构，对 ENCODE ChIP-seq 数据中每个 TF 训练双模型；提取 B ∩ Aᶜ 基序；用 JASPAR 和 CIS-BP 验证；比较与单模型的 AUC 差异。
- **验证方式**：在独立 ChIP-seq 数据集上评估；用已知 TF 突变实验（如 SELEX）验证基序特异性。
- **创新状态**：unverified

### 候选 2：注意力-SHAP 引导的 TF 结合位点精细定位

- **名称**：AttnSHAP-TF：注意力与 SHAP 双通道引导的 TF 结合位点定位
- **来源局限/观察**：TSProm 用注意力 + SHAP 交叉验证识别启动子中的 TSp motif，但未在单碱基分辨率下评估结合位点边界。现有 TF 结合位点定位方法（如 TF-MoDisco）依赖传统 motif 匹配，未充分利用深度模型的内部表征。
- **核心假设**：注意力权重和 SHAP 值在单碱基分辨率下的一致性可精确定位 TF 结合位点，优于任一单方法。
- **初步方法**：在 TSProm 微调模型上，对每个预测为正类的启动子计算逐 token 的注意力和 SHAP 值；取两者均高的区域为候选结合位点；与 ChIP-seq peak 中心比较；用 MEME 验证基序质量。
- **验证方式**：在 ENCODE ChIP-seq 上计算定位精度（距离 peak 中心的偏差）；与 TF-MoDisco 比较。
- **创新状态**：unverified

### 候选 3：TSProm 基序与 MD 模拟的整合

- **名称**：TSProm-MD：从序列基序到结合动力学的跨尺度解析
- **来源局限/观察**：TSProm 识别的组织特异性 TF 基序是静态序列特征，未提供结合亲和力或动力学信息。MD 模拟可提供 TF–DNA 结合的原子级机制，但计算成本高，难以全基因组扫描。
- **核心假设**：TSProm 识别的高置信度基序可作为 MD 模拟的候选起始位点，显著减少搜索空间，使 MD 模拟聚焦于功能相关的结合事件。
- **初步方法**：从 TSProm 脑组织结果中选取 SP1、MYC、HES6 基序；用 HDOCK 或 HADDOCK 进行 TF–DNA 对接；对高评分复合物进行 100 ns 级 MD 模拟（AMBER 或 GROMACS）；分析结合自由能（MM-PBSA）和关键接触残基。
- **验证方式**：与实验测定的结合亲和力（如 SPR、ITC）比较；检查 MD 预测的接触残基是否与已知突变数据一致。
- **创新状态**：unverified

### 候选 4：跨物种 TSp 调控逻辑迁移

- **名称**：CrossSpecies-TSProm：跨物种组织特异性调控逻辑迁移
- **来源局限/观察**：TSProm 在人类和小鼠上训练，但未测试跨物种迁移能力。TF 结合基序在物种间保守性不一，组织特异性调控逻辑可能部分保守。
- **核心假设**：在人类上训练的 TSp 启动子模型可迁移到小鼠（反之亦然），且迁移性能与序列保守性相关。
- **初步方法**：用人类训练的模型直接测试小鼠 TSp 启动子；用小鼠数据微调后重测；分析跨物种保守基序与不保守基序的贡献差异。
- **验证方式**：跨物种 AUC 比较；保守基序富集分析（PhyloP 或 phastCons）。
- **创新状态**：unverified

### 候选 5：变异效应预测：TSp 启动子中的非编码突变

- **名称**：TSProm-Var：组织特异性启动子中非编码变异的效应预测
- **来源局限/观察**：TSProm 的 SHAP 分析可量化 token 对分类的贡献，但未用于预测非编码变异的效应。现有变异效应预测工具（如 CADD、PrimateAI）缺乏组织特异性分辨率。
- **核心假设**：TSProm 的 SHAP 值变化可预测非编码变异对组织特异性启动子功能的破坏效应，且优于通用变异效应预测工具。
- **初步方法**：对脑、肝、睾丸 TSp 启动子中的已知致病非编码变异（ClinVar、GWAS）计算 SHAP 值变化（ΔSHAP）；比较与中性变异的 ΔSHAP 分布；用报告基因实验验证 top 变异。
- **验证方式**：AUC 比较（致病 vs 中性）；与 CADD、PrimateAI 的预测比较。
- **创新状态**：unverified