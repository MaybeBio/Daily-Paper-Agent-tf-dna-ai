## 01 基本信息

- **标题**：EXTRA-seq: a genome-integrated extended massively parallel reporter assay to quantify enhancer-promoter communication
- **作者与单位**：Kribelbauer-Swietek JF; Gardeux V; Llimos-Aubach G; Faltejskova K; Russeil J; Grenningloh N; Levassor L; Steiner C; Vondrasek J; Deplancke B（单位未在摘要中提供，推测为 EPFL，因致谢提及 EPFL 核心设施）
- **期刊/预印本平台**：bioRxiv
- **年份**：2024
- **论文类型**：预印本（方法学 + 机制研究）
- **领域**：基因调控、增强子-启动子互作、MPRA、深度学习模型验证
- **关键词**：enhancer-promoter communication, massively parallel reporter assay (MPRA), genome-integrated assay, TATA-box, deep learning, Enformer, transcription factor binding sites
- **DOI/arXiv 号**：10.1101/2024.12.08.627402
- **代码**：未提供（"Custom code will be deposited to GitHub upon publication"）
- **数据**：未提供（"Raw and processed sequencing data... will be made available upon publication"）
- **阅读日期**：2026-05-13（当前日期）
- **在课题方向中的位置**：本文属于「蛋白质-DNA互作 × 实验方法学」交叉方向，聚焦增强子-启动子（E-P）通讯的定量测量。对 TF–DNA 结合机制课题的关联在于：(1) 提供基因组整合的 MPRA 平台，可在内源位点以单 TFBS 分辨率解析 TF 结合对表达的影响；(2) 系统比较了深度学习模型（Enformer）与实验测量在预测基因表达上的差异与互补性；(3) 揭示了 TATA-box 对增强子强度的动态范围调节作用，为 TF–DNA 互作的下游功能后果提供了定量框架。

---

## 02 一句话总结

本文开发了基因组整合的延伸型 MPRA 技术 EXTRA-seq，在内源 AXIN2 位点以单 TFBS 分辨率定量增强子活性，发现 TATA-box 作为动态范围放大器（抑制弱增强子、放大强增强子），并证明将 Enformer 深度学习预测与实验测量整合可改善基因表达预测。

---

## 03 研究问题

- **具体问题**：增强子如何与远距离（数百 bp 至数百 kb）的启动子通讯？E-P 兼容性由什么决定？现有深度学习模型能否准确捕捉这种通讯？
- **为什么重要**：增强子-启动子通讯是基因表达调控的核心机制，其失调与多种疾病（包括癌症）相关。理解其规则对疾病机制研究和治疗性基因组编辑至关重要。
- **现有方法不足**：
  - 成像研究（超增强子、凝聚体）受限于单一调控架构或单一 TF；
  - 表观遗传协调分析需跨多样基因组背景推断机制，易混淆；
  - 游离型（episomal）MPRA 缺乏内源染色质环境，无法反映真实的 E-P 通讯；
  - 深度学习模型（如 Enformer）虽能预测表达，但缺乏人类可解释的机制洞察，且对特定基因座的预测不可靠。
- **精确研究问题**：Can a genome-integrated MPRA quantify enhancer-promoter communication at single-TFBS resolution in an endogenous context, and can integrating such experimental measures with deep learning predictions improve gene expression forecasting?

---

## 04 背景与发展脉络

*注：此脉络基于本文引用的框架，未经外部系统核验。*

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|---------|
| 单基因座遗传学 | 报告基因、转基因 | 机制清晰 | 低通量、非内源环境 | — |
| 成像方法 | 超增强子、凝聚体、微环境 | 空间信息 | 限于单一架构或 TF | — |
| 表观遗传协调分析 | 跨群体/单细胞变异共变 | 内源背景 | 推断性、混杂因素多 | — |
| 游离型 MPRA | STARR-seq 等 | 高通量、可测 E-P/E-E | 缺乏内源染色质、距离短 | 本文对比对象 |
| 基因组整合 MPRA | 早期整合型 MPRA（<数百 bp） | 内源环境 | 插入片段短、无法测长距离 | 本文扩展至 kb 级 |
| 深度学习预测 | Enformer、Puffin | 全基因组、跨细胞类型 | 黑箱、特定基因座不可靠 | 本文系统比较并整合 |
| **本文** | **EXTRA-seq** | **内源整合 + kb 级距离 + 单 TFBS 分辨率 + 与 DL 整合** | **通量有限（数十至数百片段）** | **核心贡献** |

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|---------------|---------|
| 游离型 MPRA 缺乏内源环境 | STARR-seq 等无法反映真实 E-P 通讯 | 质粒不经历染色质组装，缺乏内源拓扑关联 | Introduction 第 3 段；Results 图 3 中 STARR-seq 与 EXTRA-seq 结果差异 |
| 现有整合型 MPRA 距离受限 | 仅能测试 <数百 bp 的调控元件 | 传统整合方法插入片段短 | Introduction 第 4 段（引用 47-49） |
| 深度学习模型对特定基因座预测不可靠 | Enformer 对 AXIN2 位点的预测随位置编码变化剧烈 | 模型对输入序列的绝对位置编码敏感 | Results 图 S3a；Supplemental Figure 3a |
| 深度学习模型缺乏可解释性 | 无法从预测中提取人类可理解的调控规则 | 模型为黑箱 | Introduction 第 5 段；Discussion |
| 现有方法无法区分 TF 的「激活」与「先锋」功能 | STARR-seq 低估 PU1 等先锋因子活性 | 游离型染色质无需先锋因子即可开放 | Results 图 3b；Discussion |
| 内源基因座存在多个 TSS 导致测量混淆 | AXIN2 有替代 TSS，需确保只测量目标 TSS 的转录 | 多 TSS 使 RNA 测量不特异 | Methods "Library extraction" 段；Supplemental Figure 1a |

---

## 06 核心思想

**1) 表面方法**：
- 利用 CRISPR 在 AXIN2 基因座插入含 loxP/lox2272 位点的「着陆垫」（landing pad），替换内源启动子及上游数 kb 调控区；
- 通过 Cre 重组酶介导的盒式交换（RMCE）将包含不同增强子/启动子变体的文库整合到该位点；
- 每个变体携带随机条形码（BC），通过 RNA/gDNA 比值定量表达活性。

**2) 核心洞察**：
- **内源染色质环境 + kb 级距离**是捕捉真实 E-P 通讯的关键——游离型 MPRA 无法模拟染色质状态和长距离互作；
- **单 TFBS 分辨率**使机制发现成为可能（如 PU1 的先锋活性、TATA-box 的动态范围调节）；
- **实验与计算互补**：Enformer 擅长捕捉局部序列特征（如 TFBS 存在），但无法预测长距离 E-P 通讯；STARR-seq 捕捉「激活型」TF 活性但遗漏「先锋型」TF；整合两者可弥补各自盲区。

**3) 可能的普适教训 [Analysis]**：
- 任何「序列→功能」的预测模型都需要在**内源、长距离**环境中验证，游离型或短距离实验可能系统性地高估/低估某些调控机制；
- TF 的功能分类（激活 vs 先锋）不应仅基于序列基序，而应基于**染色质环境依赖的活性测量**；
- 深度学习模型与实验测量的「分歧」本身即是信息——分歧处往往指向模型未捕捉的生物学机制。

---

## 07 方法总览

- **输入**：AXIN2 基因座（内源染色质环境）+ 合成的增强子/启动子变体文库（含随机条形码）
- **输出**：每个变体的相对表达活性（log2 fold change, RNA/gDNA 比值）
- **核心模块**：
  1. **CRISPR 细胞工程**：双 gRNA 靶向 AXIN2 5'UTR 和增强子上游，插入含 loxP-CMV-GFP-lox2272 的着陆垫
  2. **文库构建**：PCR 扩增含变体 + 条形码的片段，通过 RMCE 整合
  3. **定量测量**：gDNA 和 mRNA 分别提取，条形码计数，计算 RNA/gDNA 比值
  4. **条形码映射**：ONT 长读长测序建立「条形码→变体」映射
  5. **计算比较**：与 STARR-seq、Enformer、Puffin 预测进行系统对比
- **训练**：不适用（非监督学习任务；深度学习模型为预训练模型 Enformer/Puffin）
- **反馈回路**：无（实验测量与计算预测为单向比较）
- **假设**：
  - 着陆垫插入不影响增强子功能（通过对照验证）
  - RNA/gDNA 比值反映转录活性而非 mRNA 稳定性
  - 条形码计数无 PCR 扩增偏差（通过技术重复验证）

**文字流程**：
1. CRISPR 在 AXIN2 位点插入着陆垫 → 2. 构建含变体+条形码的文库质粒 → 3. ONT 测序建立条形码-变体映射 → 4. RMCE 整合到细胞 → 5. 分选 GFP 阴性细胞（成功交换者）→ 6. 提取 gDNA/mRNA → 7. PCR 扩增条形码区域 → 8. 短读长测序计数 → 9. 计算 RNA/gDNA 比值 → 10. 与 STARR-seq/Enformer/Puffin 比较

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|----------------------|
| CRISPR 着陆垫插入 | 在目标基因座创建可交换的整合位点 | 使文库变体能在相同内源染色质环境中测试 | 输入：AXIN2 位点；输出：含 loxP-CMV-GFP-lox2272 的杂合细胞系 | Results 图 1a；Methods "RMCE Cell line establishment" | 无法进行基因组整合测试，退回游离型 MPRA |
| RMCE 文库整合 | 将变体文库单拷贝整合到着陆垫 | 确保每个细胞测试一个变体，避免质粒拷贝数差异 | 输入：文库质粒 + 着陆垫细胞；输出：整合文库的细胞池 | Results 图 1a,b；Methods "Library Cloning" | 无法控制整合位点，引入位置效应 |
| 条形码系统 | 通过随机 BC 追踪每个变体 | 实现混合池的高通量定量 | 输入：变体+BC 片段；输出：BC-变体映射 | Results 图 1b；Methods "Barcode to fragment mapping" | 无法区分变体，需逐个测试 |
| RNA/gDNA 比值定量 | 计算每个变体的相对表达 | 消除细胞数量差异，反映转录活性 | 输入：gDNA/mRNA 条形码计数；输出：log2 fold change | Results 图 1f-h；Methods "Count data analysis" | 无法定量表达，只能定性 |
| mpralm 统计框架 | 估计均值-方差关系，计算变体效应 | MPRA 数据存在过度离散，需专门统计模型 | 输入：条形码计数表；输出：校正后的 logFC 及标准误 | Results 图 1h；Methods "Count data analysis" | 统计功效降低，假阳性增加 |
| 多位置编码平均策略 | 对 Enformer 预测进行多次移位平均 | 消除模型对输入序列绝对位置的敏感性 | 输入：变体序列；输出：平均预测值 | Results 图 S3a；Methods "Enformer predictions" | Enformer 预测不稳定，无法可靠比较 |
| AlphaFold3 结构预测 | 预测 PU1 蛋白与 DNA 的结合构象 | 解释不同 TFBS 构型的活性差异 | 输入：DNA 序列 + PU1 蛋白序列；输出：预测复合物结构 | Results 图 3d；Methods "Alphafold predictions" | 无法从结构角度解释 TFBS 构型效应 |

**消融效应区分**：
- **实测消融**：未提供系统性消融实验（如移除条形码、改变整合位点等）
- **预期效应**：基于方法学原理推断，标注为「预期」

---

## 09 关键公式符号

本文为实验方法学论文，核心定量为 RNA/gDNA 比值，无复杂数学公式。关键符号如下：

| 符号 | 含义 | 用途 | 来源 |
|------|------|------|------|
| logFC | log2 fold change，mRNA/gDNA 条形码计数的比值 | 衡量变体相对表达活性 | Methods "Count data analysis" |
| BC | 条形码（barcode） | 追踪每个变体 | Results 图 1a |
| rho (ρ) | Pearson 相关系数 | 衡量表观遗传标记与表达的相关性 | Results 图 2b |
| p-value | 显著性水平 | 统计检验 | Results 图 1g,h |

*注：本文未使用深度学习训练公式或分子动力学方程，核心定量为比值计算。*

---

## 10 实验设计与证据链

**数据集/群体**：
- 细胞系：MEC1（慢性淋巴细胞白血病，AXIN2 基因座纯合参考基因型）
- 文库规模：约 50 个合成增强子（1-5 个 TFBS）+ 21 个 TFBS 变体 + 内源增强子/启动子变体
- 技术重复：3-5 个生物学重复（每个变体 100+ 条形码）

**指标**：
- 主要指标：log2 fold change（RNA/gDNA）
- 辅助指标：表达条形码比例、技术重复相关性（Pearson rho = 0.98）

**基线/对照**：
- 内源 REF 增强子（参考基因型）
- 增强子完全删除（阴性对照）
- 非增强子序列（阴性对照）
- STARR-seq（游离型 MPRA 对照）
- Enformer/Puffin 预测（计算对照）

**评测协议**：
- 每个变体至少 100 个条形码
- 技术重复间相关性验证（rho = 0.98）
- 与 STARR-seq 和 Enformer 预测进行配对比较

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|------------|-----------|------|------------|----------------|------|
| rs143348853 REF vs ALT | EXTRA-seq 能捕获内源变异效应 | 杂合细胞中比较 REF/ALT 增强子 | ALT 表达显著高于 REF（~1.6 倍） | EXTRA-seq 能定量内源变异效应 | 不能推广到所有内源变异 | Results 图 1f-h |
| 10 个外源增强子 + 5 个非增强子 | EXTRA-seq 能区分增强子与非增强子 | 与 REF 增强子活性比较 | 非增强子无激活；增强子活性差异大 | EXTRA-seq 具有增强子/非增强子判别力 | 样本量有限（n=15） | Results 图 2a |
| 表观遗传标记相关性 | 内源标记可预测 E-P 通讯效率 | H3K27ac、BRD4、H3K4me1、p300 与表达相关性 | 仅 H3K27ac 和 BRD4 显著相关（rho=0.71, 0.76） | 特定共激活因子标记预测 E-P 通讯 | 因果关系未确立 | Results 图 2b |
| 19 个 TFBS 替换 MEF2 位点 | EXTRA-seq 能分辨单 TFBS 效应 | 与 STARR-seq、Enformer 比较 | 三者排名和效应量均有差异 | 不同方法捕获 TF 功能的不同方面 | 无法确定哪种方法「更正确」 | Results 图 3a-c |
| PU1 位点分析 | STARR-seq 低估先锋因子活性 | STARR-seq vs EXTRA-seq 对 PU1 的效应 | STARR-seq 未检测到 PU1 活性，EXTRA-seq 检测到 | 游离型 MPRA 系统性低估先锋因子 | 需要更多先锋因子验证 | Results 图 3b |
| AlphaFold3 结构预测 | TFBS 构型影响蛋白-DNA 互作 | PU1 短间隔 vs 长间隔构型 | 短间隔预测为同侧结合，长间隔为对侧 | 构型差异可能解释活性差异 | 仅为预测，需实验验证 | Results 图 3d |
| Enformer 位置编码敏感性 | Enformer 预测对输入位置敏感 | 移位 1-10bp 的预测变化 | 预测效应量变化达 3 倍 | Enformer 对位置编码敏感，需平均化 | 平均化策略可能掩盖真实效应 | Results 图 S3a |
| 整合 STARR-seq + Enformer | 组合预测优于单一方法 | 单独 vs 组合与 EXTRA-seq 的相关性 | 组合后相关性最高（rho=0.85） | 实验与计算互补 | 仅一个基因座验证 | Results 图 6b |

---

## 11 结论正确解读

- **任务范围**：本文结论仅限于 AXIN2 基因座、MEC1 细胞系、B 细胞相关增强子/转录因子。不能推广到所有基因座或细胞类型。
- **oracle/真值输入**：EXTRA-seq 测量的是「内源染色质环境中的相对转录活性」，这是其真值；但该真值本身受着陆垫插入位置、细胞状态等影响。
- **端到端状态**：EXTRA-seq 是端到端的实验测量系统（从序列到表达），但**不是**端到端的预测系统——它需要实际实验操作。
- **算力成本**：不适用（实验方法）；AlphaFold3 预测为辅助分析。
- **历史数据依赖**：Enformer/Puffin 预测依赖其训练数据（ENCODE 等），可能对 AXIN2 这类基因座存在偏差。
- **模型依赖**：Enformer 对输入序列位置编码敏感（作者发现），需平均化处理；Puffin 对启动子近端序列的预测与 EXTRA-seq 偏差较大。
- **最难情形**：弱增强子（1 个 TFBS）的活性测量噪声较大；长距离（>20kb）E-P 通讯因克隆效率限制无法测试。
- **群体/领域边界**：B 细胞/淋巴细胞背景；AXIN2 是 WNT 通路靶基因，其调控机制可能具有通路特异性。
- **不确定性**：作者未提供重复实验的完整分布数据；AlphaFold3 预测未经过实验验证（如 EMSA、ChIP）。

**有边界的复述**：在 MEC1 细胞 AXIN2 基因座，EXTRA-seq 能以单 TFBS 分辨率定量增强子活性，发现 TATA-box 对弱增强子起抑制作用、对强增强子起放大作用；Enformer 与 STARR-seq 的整合预测优于任一单独方法，但该结论仅基于一个基因座、约 50 个增强子变体。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|---------|-------------------|------|
| 通量有限 | 可测试片段数从数十到数百，远低于游离型 MPRA | 提高 RMCE 效率、优化文库构建 | Discussion 第 4 段 |
| 距离受限 | 增强子-启动子距离受克隆效率限制（<20kb） | 开发更长的整合载体 | Discussion 第 4 段 |
| 细胞类型特异性 | 结果仅来自 MEC1 细胞 | 扩展到更多细胞类型 | Discussion 最后一段 |
| 基因座特异性 | 仅测试 AXIN2 一个基因座 | 建立通用着陆垫系统 | Discussion 最后一段 |
| 重组效率低 | 整合效率 1.5-6%，需要大量细胞 | 优化 CRISPR 和 RMCE 条件 | Methods "Estimating Replacement efficiency" |
| AlphaFold3 预测未验证 | 结构预测仅为计算推断 | 需要实验验证（如结构生物学方法） | Results 图 3d 讨论 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 着陆垫插入本身可能改变染色质环境 | 插入的 CMV-GFP  cassette 可能引入异源调控元件，影响增强子活性测量 | 如果着陆垫有独立增强子活性，所有测量值都会被污染 | 用无增强子的空载体对照测量基线活性；比较插入前后内源基因表达 | Methods "RMCE Cell line establishment" |
| 杂合整合导致等位基因特异性效应 | 只有一条等位基因被修饰，另一条野生型等位基因可能补偿或干扰 | 可能低估真实增强子效应 | 纯合整合对照；等位基因特异性表达分析 | Methods "RMCE Cell line establishment" |
| 增强子活性与 mRNA 稳定性混淆 | RNA/gDNA 比值假设 mRNA 稳定性不变，但增强子可能影响转录延伸或 mRNA 加工 | 可能高估/低估某些变体的转录活性 | 使用代谢标记（如 SLAM-seq）测量转录速率而非稳态 mRNA | Methods "Count data analysis" |
| Enformer 位置敏感性处理可能掩盖真实信号 | 平均化策略可能平滑掉真实的序列位置效应 | 如果位置效应是真实的生物学信号，平均化会丢失信息 | 系统比较不同平均化策略；用实验验证位置效应 | Results 图 S3a |
| 仅用 Pearson 相关性评估模型 | 相关性高不代表预测准确，可能受离群值驱动 | 需要更严格的评估指标（如秩相关、校准度） | 计算 Spearman 相关、Bland-Altman 图、预测区间 | Results 图 6 |
| AlphaFold3 预测的生物学解释可能过度 | 结构预测差异（同侧 vs 对侧结合）可能不直接对应功能差异 | 结构-功能关系需要实验验证 | 用 EMSA、DNase footprinting 或 ChIP 验证不同构型的结合差异 | Results 图 3d |
| 样本量小（~50 增强子） | 统计功效有限，特别是对于交互效应（增强子×启动子） | 可能遗漏真实但微弱的效应 | 扩大文库规模；用贝叶斯方法处理小样本 | Results 图 5 |
| 未报告阴性对照的完整数据 | 非增强子序列的活性分布未充分展示 | 无法评估 EXTRA-seq 的假阳性率 | 提供非增强子对照的完整分布和阈值设定 | Results 图 2a |

---

## 14 学到什么

**Agent 提炼的知识候选**：

1. **内源整合是 TF 功能分类的关键**：游离型 MPRA 无法区分「激活型」与「先锋型」TF——先锋因子（如 PU1）需要染色质环境才能展现活性。迁移到 TF–DNA 结合机制研究：在评估 TF 功能时，应优先考虑内源整合报告系统而非游离型报告系统。

2. **单 TFBS 分辨率需要足够的条形码深度**：每个变体至少 100 个条形码才能可靠检测小效应（~1.6 倍差异）。迁移：设计 TF 结合位点突变扫描时，需保证每个突变体的条形码覆盖度。

3. **深度学习模型的位置敏感性是系统性问题**：Enformer 对输入序列的绝对位置编码敏感，导致同一变体在不同位置预测差异达 3 倍。迁移：使用深度学习预测 TF 结合或表达时，应进行多位置平均并报告方差。

4. **TATA-box 的双重功能（抑制弱增强子/放大强增强子）**：提示 TF–DNA 互作的输出不仅取决于 TF 结合本身，还取决于启动子核心元件的解释逻辑。迁移：研究 TF 结合机制时，应考虑启动子背景的调节作用。

5. **实验与计算的分歧指向机制盲区**：STARR-seq 与 Enformer 各自遗漏不同 TF 功能（激活 vs 先锋），整合后预测改善。迁移：在开发 TF–DNA 结合预测模型时，应使用多种实验测量（游离型 + 整合型）作为训练/验证数据，避免单一测量偏差。

6. **AlphaFold3 可用于生成可检验的构型假设**：预测不同 TFBS 间隔导致蛋白结合几何差异（同侧 vs 对侧），但需实验验证。迁移：在 TF–DNA 结合机制研究中，可用 AlphaFold3 预测不同 DNA 构型的 TF 结合模式，再用实验（如 FRET、EMSA）验证。

7. **统计框架选择影响结论**：使用 mpralm 而非简单比值，可校正均值-方差关系。迁移：在分析 MPRA 或类似高通量报告数据时，应使用专门针对过度离散数据的统计模型。

---

## 15 与已有知识连接

- **MPRA 方法学**：本文扩展了传统 MPRA（如 STARR-seq, Patwardhan et al. 2009; Arnold et al. 2013）至基因组整合 + kb 级距离。与早期整合型 MPRA（如 Maricque et al. 2018）相比，EXTRA-seq 支持更长片段和更复杂文库。
- **增强子-启动子互作模型**：与「接触-延伸」模型（contact-extend model）和「凝聚体」模型（condensate model）相关，本文提供定量平台测试这些模型。
- **深度学习预测**：与 Enformer（Avsec et al. 2021）、Puffin（Toneyan et al. 2022）等序列-表达模型直接对比，揭示其预测局限。
- **TF 功能分类**：与先锋因子（pioneer factor）研究（如 PU1, Heinz et al. 2010）相关，本文提供内源环境下的功能验证。
- **TATA-box 功能**：与核心启动子元件研究（如 Juven-Gershon & Kadonaga 2010）相关，本文提出 TATA-box 作为「动态范围调节器」的新视角。
- **AlphaFold3**：与结构预测方法（Abramson et al. 2024）相关，本文展示了其在 DNA-蛋白复合物预测中的应用。
- **统计方法**：mpralm（Myint et al. 2019）为 MPRA 数据分析的标准工具，本文验证其适用性。

---

## 16 研究想法

**Agent 生成的研究候选**：

### 候选 1：基于 EXTRA-seq 的 TF 结合位点突变扫描 + 深度学习可解释性分析
- **名称**：EXTRA-seq-TFBS-Scan
- **来源局限/观察**：本文仅测试了 19 个 TFBS 变体，且未系统改变 TFBS 间距、方向、拷贝数
- **核心假设**：TFBS 的间距、方向、侧翼序列对 E-P 通讯的贡献可通过深度学习模型的注意力权重预测
- **增量**：将 EXTRA-seq 扩展到数百个 TFBS 变体，结合 Enformer 注意力图分析，建立「序列特征→E-P 通讯效率」的定量模型
- **初步方法**：合成 200+ TFBS 变体（改变间距 0-50bp、方向、侧翼 5bp），EXTRA-seq 测量，与 Enformer 注意力权重回归
- **验证方式**：留一交叉验证；独立位点验证
- **创新状态**：unverified

### 候选 2：TATA-box 动态范围调节的机制解析
- **名称**：TATA-Dynamic-Range
- **来源局限/观察**：本文发现 TATA-box 抑制弱增强子、放大强增强子，但未探索分子机制
- **核心假设**：TATA-box 通过改变 Pol II 暂停/释放动力学来实现动态范围调节
- **增量**：将 EXTRA-seq 与 Pol II ChIP、PRO-seq 结合，测量 TATA-box 变体的暂停指数
- **初步方法**：在 AXIN2 位点插入 TATA-box 突变体，测量 EXTRA-seq 活性 + PRO-seq 暂停指数 + Pol II ChIP
- **验证方式**：比较 TATA-box 变体的暂停指数与增强子强度的关系
- **创新状态**：unverified

### 候选 3：多基因座 EXTRA-seq 平台开发
- **名称**：Multi-Locus-EXTRA-seq
- **来源局限/观察**：本文仅测试 AXIN2 一个基因座，无法区分基因座特异性效应与普遍规律
- **核心假设**：E-P 通讯规则在不同基因座间具有保守性，但受局部染色质环境影响
- **增量**：开发可靶向多个基因座的通用着陆垫系统，比较 5-10 个基因座的 E-P 通讯规则
- **初步方法**：设计通用着陆垫载体，在 5 个不同基因座插入相同增强子文库，比较活性谱
- **验证方式**：跨基因座相关性分析；染色质状态（ATAC、H3K27ac）与活性的回归
- **创新状态**：unverified

### 候选 4：增强子-启动子距离效应的系统测量
- **名称**：Distance-Sweep-EXTRA-seq
- **来源局限/观察**：本文增强子-启动子距离固定为 ~2.5kb，未系统改变距离
- **核心假设**：E-P 通讯效率随距离呈非线性衰减，衰减速率受启动子类型调控
- **增量**：在 AXIN2 位点插入不同距离（1kb、2kb、5kb、10kb）的相同增强子，测量活性
- **初步方法**：构建距离梯度文库，EXTRA-seq 测量，拟合距离-活性曲线
- **验证方式**：与 Hi-C 接触频率数据对比
- **创新状态**：unverified

### 候选 5：基于 EXTRA-seq 数据的生成模型训练
- **名称**：EXTRA-Gen
- **来源局限/观察**：本文仅用 EXTRA-seq 数据评估现有模型，未用其训练新模型
- **核心假设**：EXTRA-seq 数据（内源整合 + kb 级距离）可训练出比游离型 MPRA 数据更准确的序列→表达模型
- **增量**：将 EXTRA-seq 数据作为训练集，微调 Enformer 或训练新模型
- **初步方法**：收集 EXTRA-seq 数据（本文 + 未来扩展），微调 Enformer 的最终层，比较预测精度
- **验证方式**：独立测试集；与游离型 MPRA 训练的模型对比
- **创新状态**：unverified

### 候选 6：TF 协同性的内源环境测量
- **名称**：TF-Cooperativity-EXTRA-seq
- **来源局限/观察**：本文测试了单个 TFBS 替换，但未测试 TFBS 组合的协同效应
- **核心假设**：TFBS 组合的协同效应在游离型 MPRA 中被低估，需要内源染色质环境才能显现
- **增量**：设计 TFBS 组合文库（如 PU1+IRF、PU1+NFkB），比较 EXTRA-seq 与 STARR-seq 的协同性差异
- **初步方法**：合成 TFBS 组合变体，两种平台平行测量，计算协同指数（observed/expected）
- **验证方式**：与 ChIP-seq 共结合数据对比
- **创新状态**：unverified