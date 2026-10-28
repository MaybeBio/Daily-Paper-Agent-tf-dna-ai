## 01 基本信息
- **标题**：Deep learning the dynamic regulatory sequence code of cardiac organoid differentiation
- **作者**：Metzl-Raz, Eyal; Zhao, Ryan; Deshpande, Salil; Powell, Jackson; Porter, Elizabeth G; Zouaghi, Yassine; Liu, Betty B; Kim, Samuel H; Abdi, Immanuel; Evergreen, Ivy; Agarwal, Megha; Sheth, Maya U; Miyamoto, Matthew; Sanchez, Julie M; Engreitz, Jesse M; Kundaje, Anshul; Greenleaf, William J; Gifford, Casey A
- **单位**：未提供（推测为 Stanford University 相关实验室，如 Greenleaf Lab、Gifford Lab、Kundaje Lab、Engreitz Lab，但原文未明确列出单位列表）
- **期刊/平台**：bioRxiv : the preprint server for biology
- **年份**：2025（预印本日期 2025-11-24）
- **论文类型**：预印本（preprint）
- **领域**：发育生物学 × 计算基因组学 × 深度学习
- **关键词**：cardiac organoid, single-cell multi-omics, chromatin accessibility, deep learning, ChromBPNet, TF–DNA binding, cis-regulatory grammar, congenital heart disease
- **DOI/arXiv 号**：10.1101/2025.10.15.680997
- **代码**：https://github.com/GreenleafLab/Cardioid（分析脚本）；https://github.com/GreenleafLab/shareseq-pipeline（预处理流程）
- **数据**：未提供（文中提到数据可通过作者获取，但未给出具体 accession 号）
- **阅读日期**：2026-05-13（假设）
- **在课题方向中的位置**：本文是「TF–DNA 结合机制 × 深度学习」方向的代表性工作，利用 ChromBPNet 从 DNA 序列预测染色质可及性，进而解码细胞状态特异的 TF motif 语法（motif syntax），并整合单细胞多组学数据揭示心脏类器官分化过程中的动态调控规则。与课题直接相关：核心方法（ChromBPNet + DeepLIFT + TF-MODISCO）可迁移至任意 TF–DNA 互作研究。

## 02 一句话总结
本文通过整合人 iPSC 来源心脏类器官的时间分辨单细胞多组学图谱（约 12 万细胞、6 个时间点）与 ChromBPNet 深度学习模型，从 DNA 序列预测染色质可及性，解码了心脏分化过程中细胞状态特异的 TF motif 组合语法（如 TEAD、HAND、TBX 的上下文依赖活性），并通过 MYOCD 敲低实验验证了模型预测的 ventricular 心肌细胞命运决定因子。

## 03 研究问题
- **具体问题**：如何从 DNA 序列中解码心脏类器官分化过程中驱动染色质可及性动态变化的转录因子（TF）调控语法（regulatory syntax）？具体包括：哪些 TF motif 组合在特定细胞状态中贡献可及性？TF 之间的协同/拮抗关系如何随分化时间变化？非编码变异如何通过破坏这些语法导致先天性心脏病（CHD）？
- **为什么重要**：CHD 是最常见的先天性缺陷（影响高达 3% 活产儿），但大量病例的遗传病因未明，尤其是非编码变异的作用。理解早期心脏发育（post-gastrulation 阶段）的顺式调控逻辑是解释这些变异致病机制的关键。
- **现有方法不足**：传统 motif 扫描无法解析密集排列的 TF 结合位点的组合效应；ChIP-seq 难以规模化覆盖所有 TF 和细胞状态；标准 ATAC-seq 分析缺乏单碱基分辨率来区分复杂调控语法；胎儿图谱多聚焦后期心脏状态，缺乏早期谱系特化阶段的调控分辨率。
- **精确研究问题（Can 问题）**：Can a base-pair-resolution deep learning model trained on single-cell chromatin accessibility data from cardiac organoids accurately predict cell-state-specific TF motif grammar, and can this grammar be experimentally validated to reveal essential regulators of cardiac lineage commitment?

## 04 背景与发展脉络
**脉络标注**：以下脉络基于本文引言与讨论的框架，结合领域常识，标注为「经外部核验」的部分仅指领域公认方法。

1. **阶段一：传统 motif 发现与 ChIP-seq（2010s 前）**：基于位置权重矩阵（PWM）扫描基因组，依赖已知 TF 结合偏好，无法发现新 motif 或解析组合语法。ChIP-seq 可鉴定 TF 占据，但难以规模化且需先验知识。
2. **阶段二：单细胞 ATAC-seq 与可及性分析（2015-2020）**：scATAC-seq 提供细胞类型特异的调控区域图谱，但分析多停留在 peak 水平，缺乏单碱基分辨率的调控逻辑解析。
3. **阶段三：深度学习预测染色质可及性（2018-2023）**：Basenji、BpNet、ChromBPNet 等模型从序列预测可及性/表达，可学习 motif 及其语法。局限：多用于 bulk 或细胞系，缺乏发育时间动态与细胞状态分辨率。
4. **阶段四：单细胞多组学 × 深度学习的整合（本文，2025）**：将时间分辨的 scRNA/ATAC 多组学图谱与 ChromBPNet 结合，实现细胞状态特异的 motif 语法解码，并链接到疾病变异。本文主张的位置：在此脉络中首次将 ChromBPNet 应用于心脏类器官分化轨迹，并整合 TF 表达与 motif 活性来解析上下文依赖调控。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 传统 motif 扫描无法解析组合语法 | 每个 peak 平均注释到 90 个 motif 实例，无法区分功能性结合 | 密集排列的 TF 结合位点导致 PWM 扫描特异性低；缺乏定量贡献评估 | Results 节（图 S3D 相关描述） |
| 标准 ATAC-seq 分析缺乏单碱基分辨率 | 无法区分同一 peak 内不同 TF 的贡献 | peak 水平聚合丢失了碱基级别的调控信息 | Results 节（图 3B 相关描述） |
| ChIP-seq 难以规模化覆盖所有 TF 和细胞状态 | 需要每个 TF 的特异性抗体，无法在多个时间点和细胞类型中系统开展 | 技术通量限制与先验知识需求 | Introduction 节 |
| 胎儿图谱缺乏早期发育阶段分辨率 | 现有 in vivo 图谱多聚焦后期心脏状态，无法捕捉 post-gastrulation 的谱系特化事件 | 早期人类胚胎组织难以获取 | Discussion 节 |
| 非编码变异功能解读困难 | 大量 CHD 相关非编码变异无法定位到具体细胞状态和调控机制 | 缺乏早期发育阶段的调控图谱和预测模型 | Discussion 节 |
| 表达与活性脱节 | TF 表达不等于功能活性，如 MEF2 在 vCM 和 AE 均表达但仅 vCM 有可及性贡献 | 需要整合表达与序列预测来解析上下文依赖活性 | Results 节（图 3F 相关描述） |

## 06 核心思想
**1) 表面方法**：
- 生成时间分辨的心脏类器官单细胞多组学图谱（scRNA + scATAC，6 个时间点，约 12 万细胞）
- 对每个细胞状态训练 ChromBPNet 模型，从 DNA 序列预测染色质可及性
- 用 DeepLIFT 计算每个碱基的贡献分数，用 TF-MODISCO 发现 de novo motif
- 通过 in silico marginalization 量化每个 motif 对可及性的边际贡献
- 整合 TF 表达数据，将 motif 活性与候选 TF 表达关联
- 用 CRISPRi 敲低 MYOCD 验证模型预测

**2) 核心洞察**：
- 染色质可及性的调控语法是细胞状态特异的：同一 motif（如 TEAD）在不同细胞类型中与不同 partner motif 组合，产生不同的可及性贡献
- 表达与活性可分离：TF 表达不等于功能活性，需要序列层面的预测来解析真正的调控贡献
- 通过 marginalization 可以量化 motif 的边际效应，从而区分「存在」与「功能」
- 模型预测的 motif 语法可以直接链接到疾病变异，解释非编码变异的细胞状态特异效应

**3) 可能的普适教训 [Analysis]**：
- 深度学习模型不仅是预测工具，更是「可解释的调控语法解码器」——通过贡献分数和 marginalization，可以将黑盒预测转化为可检验的生物学假设
- 单细胞多组学与深度学习的整合是解析发育调控逻辑的通用框架，可迁移至其他器官系统
- 表达与活性的解耦是发育生物学的普遍现象，序列预测模型提供了一种系统解析这种解耦的方法

## 07 方法总览
- **输入**：DNA 序列（hg38 参考基因组，2114 bp 窗口）；每个细胞状态的聚合 ATAC-seq 片段
- **输出**：碱基分辨率可及性预测；每个碱基的贡献分数；de novo motif 及其边际贡献分数
- **模块**：
  1. 数据生成：SHARE-seq 单细胞多组学（scRNA + scATAC）
  2. 细胞状态注释：聚类 + marker gene 鉴定
  3. Peak calling：每个细胞状态的聚合 ATAC 数据
  4. ChromBPNet 训练：5-fold 交叉验证，每细胞状态一个模型
  5. DeepLIFT 贡献分数计算
  6. TF-MODISCO motif 发现与聚类（MotifCompendium）
  7. In silico marginalization：motif 插入/缺失实验
  8. 基因链接：scE2G 预测 enhancer-gene 连接
  9. 变异效应预测：variant scoring
- **训练**：每个细胞状态独立训练 ChromBPNet，5-fold 交叉验证；Tn5 bias 模型在 vCM 状态的 background regions 上训练
- **反馈回路**：模型预测 → 实验验证（CRISPRi MYOCD KD）→ 验证模型解释力
- **文字流程**：从类器官分化取样 → SHARE-seq 建库测序 → 单细胞多组学数据处理与聚类 → 每细胞状态聚合 ATAC → 训练 ChromBPNet → DeepLIFT 贡献分数 → TF-MODISCO 发现 motif → marginalization 量化 motif 效应 → scE2G 链接基因 → 变异预测 → 实验验证

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| SHARE-seq 单细胞多组学 | 同时获取同一细胞的转录组和染色质可及性 | 需要将 TF 表达与 motif 活性关联，解析上下文依赖调控 | 输入：类器官细胞；输出：配对 scRNA/scATAC 数据 | Results 节（图 1B-D） | 无法关联表达与活性，失去上下文依赖解析能力 |
| ChromBPNet 模型 | 从序列预测碱基分辨率可及性 | 学习 motif 及其语法，超越传统 PWM 扫描 | 输入：2114 bp 序列；输出：可及性预测 + 贡献分数 | Results 节（图 3A-B）；Methods 节 | 无法解析 motif 语法，退回传统 motif 扫描 |
| DeepLIFT 贡献分数 | 计算每个碱基对预测的贡献 | 定位功能性碱基，发现 de novo motif | 输入：训练好的模型 + 序列；输出：碱基贡献分数 | Methods 节 | 无法定位功能性 motif 实例 |
| TF-MODISCO + MotifCompenium | 从贡献分数中发现 motif 并聚类 | 获得非冗余 motif 集合，避免冗余 | 输入：贡献分数；输出：418 个 motif，172 组，106 家族 | Results 节；Methods 节 | motif 集合冗余，下游分析噪声大 |
| In silico marginalization | 量化 motif 的边际可及性贡献 | 区分「存在」与「功能」，解析 motif 组合效应 | 输入：motif 序列 + 背景序列；输出：边际效应分数 | Results 节（图 3F-H） | 无法区分功能性 motif 与被动存在 motif |
| scE2G 基因链接 | 将调控元件链接到目标基因 | 从 motif 语法到基因调控网络 | 输入：peak + 基因表达；输出：enhancer-gene 连接 | Results 节（图 4A-B） | 无法将 motif 活性转化为基因调控网络 |
| CRISPRi 功能验证 | 敲低模型预测的关键 TF | 验证模型预测的因果性 | 输入：MYOCD sgRNA；输出：细胞命运变化 | Results 节（图 5A-G） | 模型预测停留在相关性，缺乏因果证据 |

## 09 关键公式符号
本文未提供明确的数学公式。核心方法涉及的概念性「公式」如下：

1. **ChromBPNet 预测目标**：
   - 输入序列 x（长度 2114 bp），输出预测可及性 ŷ = f(x)
   - 训练目标：最小化预测与观测可及性之间的损失（具体损失函数未在文中详述）

2. **DeepLIFT 贡献分数**：
   - 对每个碱基 i，计算贡献分数 c_i，表示该碱基对预测 ŷ 的贡献
   - 满足加和性质：Σ c_i ≈ ŷ - y_ref（y_ref 为参考值）

3. **In silico marginalization 效应量**：
   - 对 motif m，计算效应量 = log2(预测可及性_with_motif / 预测可及性_without_motif)
   - 在 1000 个背景序列上平均，得到 motif 的边际效应分数

4. **距离加权贡献分数**（gene-motif linking）：
   - 对 motif hit 距 TSS 距离 d，权重 w(d) = e^(-d/5000) + 1/e
   - motif 对基因 g 的贡献 = Σ_hits w(d) × 贡献分数

## 10 实验设计与证据链
**数据集与资源**：
- 人 iPSC 来源心脏类器官，6 个时间点（Day 0, 1, 2, 3, 5, 10）
- 约 12 万细胞（60,000 用于 scRNA/scATAC 配对分析）
- 20 个细胞状态（聚类注释）
- 628,378 共识 peak（9,643,338 总细胞状态特异 peak）
- 59 个细胞状态（含对照 + MYOCD KD）
- 参考图谱：人原肠胚（gastrula）图谱、小鼠胚胎心脏发育图谱（E8-P0）

**指标**：
- ChromBPNet 预测准确度：Pearson 相关系数（0.78-0.88，中位数 0.85）
- 可及性预测 profile 质量：Jensen-Shannon Divergence（JSD，中位数 0.47-0.73）
- motif 边际效应：log2 fold change
- 变异效应：预测可及性变化 + 经验 p 值

**实验表格**：
| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 时间序列类器官分化图谱 | 类器官重现体内心脏发育轨迹 | 与人类原肠胚图谱比对 | 早期时间点映射到原肠胚状态，后期出现心脏谱系 | 类器官是研究早期心脏发育的有效模型 | 不能完全替代 in vivo 验证 | Results 图 1-2 |
| ChromBPNet 训练与评估 | 模型能从序列预测细胞状态特异可及性 | 每细胞状态 5-fold CV | Pearson 0.78-0.88，JSD 0.47-0.73 | 模型准确预测可及性 | 预测准确度不直接等于调控机制正确 | Results 图 3A-B |
| Motif 语法分析（TEAD 案例） | TEAD 活性由 partner motif 决定 | 不同细胞状态中 TEAD 的边际效应 | TEAD 与 SRF 组合在 vCM 中活性高，与 GRHL 组合在 ectoderm 中活性高 | 上下文依赖的 motif 语法 | 未直接验证蛋白-蛋白互作 | Results 图 3H |
| MEF2 活性分析 | 表达不等于活性 | vCM vs AE 中 MEF2 表达与边际效应 | MEF2 在两者均表达，但仅 vCM 有可及性贡献 | 需要序列预测解析功能活性 | 未解释 MEF2 活性差异的分子机制 | Results 图 3F |
| MYOCD CRISPRi 敲低 | MYOCD 是 vCM 命运决定因子 | 对照 vs MYOCD KD，多时间点 | vCM 减少，出现替代细胞状态；AE 改变 | MYOCD 对 vCM 特化必需 | 未证明 MYOCD 直接结合所有靶位点 | Results 图 5A-G |
| 非编码变异效应预测 | 模型能预测 CHD 相关变异的细胞状态特异效应 | 对 CHD 相关变异进行 in silico 突变 | 变异在特定细胞状态中显著改变可及性 | 模型可用于变异功能解读 | 未进行实验验证变异效应 | Results 图 6E-G |

## 11 结论正确解读
- **任务范围**：本文聚焦于心脏类器官分化过程中的染色质可及性调控，而非直接测量 TF 结合或基因表达调控。模型预测的是「可及性」，TF 活性是通过 motif 贡献推断的。
- **oracle/真值输入**：模型训练使用观测的 ATAC-seq 可及性作为真值；TF 活性推断依赖 motif 序列匹配，未使用 ChIP-seq 验证。
- **端到端状态**：从序列到可及性预测是端到端的；但从序列到「TF 功能」是间接推断，需要实验验证。
- **算力成本**：未提供具体训练时间或硬件需求。
- **历史数据依赖**：模型仅基于类器官分化数据训练，泛化到其他组织或物种需重新训练或微调。
- **模型依赖**：结果依赖 ChromBPNet 架构和训练策略；不同模型可能产生不同 motif 发现。
- **最难情形**：模型对低可及性区域、罕见细胞状态、以及非经典 motif 的预测可能不准确。
- **群体/领域边界**：结论基于 iPSC 来源类器官，可能不完全反映 in vivo 人类心脏发育；CHD 变异分析限于已知 CHD 基因附近区域。
- **不确定性**：marginalization 效应量是预测值，未提供置信区间；变异效应预测未经过实验验证。

**有边界的复述**：本文证明，在心脏类器官分化系统中，基于 DNA 序列的深度学习模型能够以较高准确度（Pearson 中位数 0.85）预测细胞状态特异的染色质可及性，并从中解码出上下文依赖的 TF motif 语法；其中 MYOCD-SRF 网络被预测并实验验证为 vCM 特化的关键调控模块。这些结论限于类器官系统，外推到 in vivo 需谨慎。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 类器官模型缺乏关键支持细胞类型 | 缺少神经嵴细胞等 in vivo 重要细胞类型，限制后期发育和疾病建模 | 引入更多细胞类型和微环境因素 | Discussion 节 |
| 缺乏血流动力学和机械力 | 类器官缺乏血流剪切力等机械信号，可能影响心脏成熟 | 结合生物反应器或微流控系统 | Discussion 节 |
| 细胞类型组成限制 | 现有类器官系统无法完全模拟复杂器官结构 | 开发更复杂的类器官系统 | Discussion 节 |
| 模型预测需要实验验证 | 计算预测的 TF 活性需要功能实验确认 | 结合 CRISPR 筛选和报告基因实验 | Discussion 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| ChromBPNet 预测准确度（Pearson 0.85）可能高估模型生物学理解 | 高相关可能部分来自序列组成偏差（如 GC 含量）而非真实调控语法 | 影响 motif 发现的可靠性 | 与随机序列对照比较；检查预测是否依赖序列组成而非 motif 组合 | Results 图 3A-B |
| TF-MODISCO 发现的 motif 可能包含大量假阳性 | 贡献分数高不代表 TF 真实结合，可能反映间接效应或序列伪影 | 影响下游功能注释 | 用 ChIP-seq 或 CRISPR 验证部分 motif 预测 | Methods 节 |
| in silico marginalization 使用合成背景序列 | 背景序列的选取可能影响效应量估计，且未考虑内源染色质状态 | 影响 motif 效应量的可靠性 | 使用内源基因组背景重复 marginalization | Methods 节 |
| MYOCD KD 实验验证了相关性而非因果性 | KD 可能通过间接效应影响 vCM 命运，而非直接通过 MYOCD-SRF 调控 | 影响对机制的理解 | 进行 MYOCD 回补实验或位点特异性突变 | Results 图 5 |
| 变异效应预测缺乏实验验证 | 预测的 CHD 相关变异效应可能不反映真实功能影响 | 影响临床解释 | 用报告基因实验验证预测的变异效应 | Results 图 6 |
| 类器官与 in vivo 的差异未充分讨论 | 类器官可能缺乏关键的细胞互作信号，导致调控语法与 in vivo 不同 | 影响结论外推 | 与人类胎儿心脏数据直接比较 | Discussion 节 |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **ChromBPNet 作为 TF–DNA 互作解码器的范式**：本文展示了如何将深度学习模型从「预测工具」转化为「机制发现工具」。核心流程：训练序列→可及性模型 → DeepLIFT 贡献分数 → TF-MODISCO de novo motif 发现 → marginalization 量化 motif 效应。**可迁移性**：直接适用于任何 TF–DNA 互作研究，只需将「可及性」替换为感兴趣的 ChIP-seq、MPRA 或甲基化数据。

2. **上下文依赖的 motif 语法分析**：本文核心创新在于揭示同一 TF motif 在不同细胞状态中与不同 partner 组合产生不同效应。方法：对每个细胞状态独立训练模型，比较 motif 的 marginalization 效应量。**可迁移性**：可用于解析 TF 在不同细胞类型、发育阶段或疾病状态中的功能切换。

3. **表达-活性解耦的分析框架**：通过整合 scRNA 表达与 motif 活性预测，本文区分了「TF 存在」与「TF 功能」。**可迁移性**：在 TF–DNA 互作研究中，应同时考虑 TF 表达和序列层面的活性预测，避免仅凭表达推断功能。

4. **in silico marginalization 作为定量扰动实验**：通过在背景序列中插入/删除 motif，计算边际效应，实现了「计算扰动」实验。**可迁移性**：可用于预测 TF 结合位点突变的功能效应，为变异解读提供先验。

5. **单细胞多组学与深度学习的整合策略**：scRNA 提供细胞状态注释，scATAC 提供调控图谱，深度学习提供序列→调控的映射。**可迁移性**：这种「多组学定义状态 + 深度学习解析机制」的框架可推广至其他器官系统。

6. **从模型预测到功能验证的闭环**：本文通过 CRISPRi 验证了 MYOCD 的预测功能，展示了计算预测与实验验证结合的范式。**可迁移性**：在 TF–DNA 研究中，应优先验证模型预测的高置信度、高效应量靶点。

## 15 与已有知识连接
- **ChromBPNet 原始论文**：本文使用的模型架构源自 ChromBPNet（Kundaje lab），该模型已在 ENCODE 数据上验证可准确预测可及性并发现 motif。本文将其扩展到单细胞类器官系统。
- **TF-MODISCO**：motif 发现方法源自 TF-MODISCO 工具，本文将其应用于深度学习贡献分数而非传统 ChIP-seq 数据。
- **scE2G**：enhancer-gene 链接方法源自 Engreitz lab 的 scE2G 工具，本文将其与 motif 活性预测整合。
- **心脏发育调控网络**：本文识别的 TF（TEAD、HAND、TBX、MEF2、SRF）与已知心脏发育文献一致，验证了方法的生物学相关性。
- **先天性心脏病遗传学**：本文的变异解读框架与 CHD 队列研究（如 410 个 CHD 基因）相连接，为理解非编码变异提供了新视角。
- **类器官模型**：与既往心脏类器官工作（如 44,45 引用的分化方案）相比，本文增加了多组学时间分辨率和深度学习解析。
- **可迁移领域**：本文方法可迁移至其他器官类器官（脑、肝、肾）的发育调控研究，以及疾病相关的 TF 互作异常研究。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：跨细胞类型的 TF–DNA 互作语法图谱（TF Grammar Atlas）
   - **来源局限/观察**：本文仅覆盖心脏类器官，TF 语法是否具有普适性未知
   - **核心假设**：不同谱系共享核心 TF 语法，但 lineage-specific TF 通过 partner 组合实现特异性
   - **增量**：将 ChromBPNet 流程扩展到多个类器官系统或组织，构建跨谱系的 TF 语法图谱
   - **初步方法**：对脑、肝、肾类器官生成类似多组学数据，训练统一或分状态的 ChromBPNet 模型，比较 motif 语法
   - **验证方式**：跨系统比较 motif 效应量，识别保守与特异的语法规则
   - **创新状态**：unverified

2. **候选名称**：TF 协同作用的可解释深度学习模型（Interpretable TF Synergy Model）
   - **来源局限/观察**：本文通过 marginalization 间接推断 TF 协同，未直接建模 motif 间相互作用
   - **核心假设**：显式建模 motif-motif 交互可提高预测准确度并揭示协同规则
   - **增量**：在 ChromBPNet 架构中引入注意力机制或显式交互项，直接学习 motif 组合效应
   - **初步方法**：修改 ChromBPNet 架构，在贡献分数计算中引入 pairwise 交互项；用合成数据验证
   - **验证方式**：与标准 ChromBPNet 比较预测准确度；用 CRISPR 多基因扰动验证预测的协同效应
   - **创新状态**：unverified

3. **候选名称**：TF 结合亲和力的单碱基分辨率预测（Single-Base TF Binding Affinity Prediction）
   - **来源局限/观察**：本文贡献分数反映对可及性的贡献，非直接结合亲和力
   - **核心假设**：深度学习贡献分数可校准为结合亲和力的代理指标
   - **增量**：将贡献分数与体外结合实验（PBM、SELEX）数据整合，建立序列→亲和力的预测模型
   - **初步方法**：收集公开 TF 结合亲和力数据，训练校准模型，将 ChromBPNet 贡献分数映射为亲和力
   - **验证方式**：与实验测量的亲和力比较；预测已知致病突变的亲和力变化
   - **创新状态**：unverified

4. **候选名称**：非编码变异的功能效应预测平台（Noncoding Variant Effect Predictor for Cardiac Development）
   - **来源局限/观察**：本文仅分析了少数 CHD 相关变异，缺乏系统评估
   - **核心假设**：基于类器官训练的模型可预测 CHD 相关非编码变异的功能效应
   - **增量**：构建包含所有已知 CHD 相关变异的预测平台，提供细胞状态特异的效应评分
   - **初步方法**：扩展 variant scoring 到所有 CHD 相关变异，建立公开数据库和可视化工具
   - **验证方式**：与报告基因实验和患者数据比较；评估预测的细胞状态特异性
   - **创新状态**：unverified

5. **候选名称**：TF 语法与 3D 基因组的整合模型（Integrating TF Grammar with 3D Genome Architecture）
   - **来源局限/观察**：本文仅使用序列信息，未考虑 3D 基因组结构对 TF 互作的影响
   - **核心假设**：3D 基因组结构调节 TF 语法效应，整合可提高预测准确度
   - **增量**：将 Hi-C 数据和 CTCF/cohesin 结合位点信息整合到 ChromBPNet 框架
   - **初步方法**：在模型输入中加入 3D 结构特征，或在 marginalization 中考虑染色质环
   - **验证方式**：与仅序列模型比较；用 3D 结构扰动实验验证
   - **创新状态**：unverified

6. **候选名称**：TF 语法进化的比较基因组学分析（Evolutionary Analysis of TF Grammar）
   - **来源局限/观察**：本文仅研究人类，TF 语法的进化保守性未知
   - **核心假设**：核心 TF 语法在脊椎动物中保守，但 lineage-specific 语法是新近演化的
   - **增量**：将模型应用于小鼠、斑马鱼等模式生物的心脏发育数据，比较 motif 语法
   - **初步方法**：跨物种训练或迁移学习，比较 motif 效应量和语法规则
   - **验证方式**：与已知跨物种保守增强子比较；用进化保守性评分验证
   - **创新状态**：unverified