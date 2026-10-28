## 01 基本信息
- **标题**：The EN-TEx resource of multi-tissue personal epigenomes & variant-impact models
- **作者与单位**：Rozowsky, Joel; Gao, Jiahao; Borsari, Beatrice; Yang, Yucheng T; Galeev, Timur; Gursoy, Gamze; et al. 通讯作者 Mark Gerstein（耶鲁大学）；合作单位包括冷泉港实验室、加州大学等（多中心合作）
- **期刊/预印本平台**：Cell
- **年份**：2023
- **论文类型**：资源型（Resource）论文，含多组学数据整合与预测建模
- **领域**：功能基因组学、表观基因组学、遗传变异效应预测
- **关键词**：EN-TEx、个人表观基因组、等位基因特异性（allele-specific）、二倍体比对、变异效应预测、深度学习、Transformer、eQTL转移
- **DOI/arXiv 号**：10.1016/j.cell.2023.02.018
- **代码**：https://github.com/gersteinlab/transferQTL（transferQTL模型）；其余代码与数据见 EN-TEx portal（entex.encodeproject.org）
- **数据**：1635 个开放获取数据集，来自 4 个供体 × ~30 组织 × ~15 种实验（ChIP-seq、ATAC-seq、DNase-seq、WGBS、Hi-C、RNA-seq、eCLIP、质谱蛋白质组等）；数据通过 EN-TEx portal 与 ENCODE portal 公开
- **阅读日期**：2026-05-13（按当前日期）
- **在课题方向中的位置**：本文是「蛋白质-DNA互作 × AI/深度学习」交叉方向的代表性资源型工作。其核心贡献在于：(1) 提供大规模、多组织、二倍体（等位基因特异性）的 TF–DNA 结合数据（CTCF、POLR2A 等 ChIP-seq）；(2) 构建基于 DNA 序列上下文的深度学习模型（DNABERT/Transformer）预测变异对 TF 结合（ASB）的影响，直接面向 TF–DNA 结合机制；(3) 通过随机森林模型（transferQTL）将染色质状态与 eQTL 关联，为 TF 结合变异的功能解读提供可迁移框架。

## 02 一句话总结
本文构建了 4 个个体 × ~30 组织 × ~15 种实验的 EN-TEx 多组织个人表观基因组资源，通过二倍体比对识别出超过 100 万个等位基因特异性（AS）位点，并利用 DNABERT Transformer 模型证明仅凭局部 DNA 序列上下文即可高精度预测变异对 TF 结合（如 CTCF）的等位基因特异性影响，同时开发随机森林模型（transferQTL）将已知 eQTL 从易获取组织转移到难获取组织。

## 03 研究问题
- **具体问题**：如何系统性地评估遗传变异（特别是杂合 SNP）对分子表型（基因表达、TF 结合、染色质状态、DNA 甲基化、蛋白质丰度）的影响？如何利用个人二倍体基因组替代单一参考基因组，实现更精确的变异效应量化？
- **为什么重要**：绝大多数 GWAS 变异位于非编码区，其功能机制不明。传统方法依赖单一参考基因组，无法区分两个等位基因的差异效应。等位基因特异性分析提供了一种无需扰动实验即可直接观察变异效应的自然实验范式，对理解 TF–DNA 结合机制、变异致病机制和精准医学至关重要。
- **现有方法不足**：(1) 已有 AS 研究规模小、组织覆盖有限；(2) 缺乏统一的、跨多种实验类型的 AS 分析流程；(3) 缺乏将 AS 数据与深度学习模型结合、从序列直接预测变异效应的系统尝试；(4) eQTL 研究受限于组织获取难度，难以覆盖难以活检的组织。
- **精确的「Can ... ?」研究问题**：Can a Transformer-based deep learning model predict allele-specific TF binding (e.g., CTCF) from local DNA sequence context alone, without any tissue-specific epigenetic information?

## 04 背景与发展脉络
- **阶段一：参考基因组时代的变异-表型关联**。代表性方法：GWAS、eQTL 分析（GTEx 项目）。优点：大规模、统计功效高。局限：依赖单一参考基因组，无法区分等位基因差异效应；非编码变异功能解读困难。
- **阶段二：等位基因特异性（AS）分析兴起**。代表性方法：AS 表达（ASE）、等位基因特异性结合（ASB）、等位基因特异性甲基化（ASM）。优点：直接比较同一细胞内两个等位基因的差异，天然控制反式环境。局限：早期研究规模小、组织覆盖有限、缺乏统一流程。
- **阶段三：个人二倍体基因组与长读长测序**。代表性方法：长读长测序（PacBio、ONT）进行变异分型（phasing），构建个人二倍体基因组。优点：可区分单倍型，实现真正的等位基因特异性定量。局限：成本高、样本量有限。
- **阶段四：深度学习在调控基因组学中的应用**。代表性方法：DNABERT、Enformer、Basenji 等。优点：可从序列直接预测功能。局限：多数模型基于参考基因组，未充分利用等位基因特异性信息。
- **本文位置**：本文处于阶段三与阶段四的交汇点——利用长读长测序构建个人二倍体基因组，系统识别 AS 位点，并首次将 DNABERT Transformer 模型应用于 AS 预测，同时开发 transferQTL 随机森林模型实现跨组织 eQTL 转移。在「TF–DNA 结合 × AI」方向上，本文提供了「序列上下文 → TF 结合变异效应」的直接建模范式。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 参考基因组比对丢失等位基因信息 | 传统比对仅使用单一参考序列，杂合位点的两个等位基因无法区分，导致 AS 信号被平均化或丢失 | 参考基因组是单倍型，无法代表个体二倍体状态 | Results 图 1C；Methods "Personal Genome" 节 |
| AS 检测统计功效不足 | 单组织、单个体中 AS 位点检出率低，难以构建大规模 AS 目录 | 测序深度有限、等位基因特异性 reads 计数少 | Results 图 1C；Methods "AS Calling" 节 |
| 跨组织 AS 异质性难以刻画 | 不同组织中 AS 效应可能不同，但缺乏统一的多组织 AS 数据集 | 多组织、多实验的系统性数据采集成本极高 | Results 图 3；Methods "Decoration Process" 节 |
| 变异效应预测缺乏序列级模型 | 已有模型多基于注释或保守性特征，难以捕捉局部序列上下文对 TF 结合的影响 | 缺乏大规模 AS 数据作为训练标签 | Results 图 7；Methods "Transformer Model" 节 |
| eQTL 难以在难获取组织中检测 | 心脏、脑等组织活检困难，eQTL 目录覆盖不全 | 组织获取的伦理和 logistics 限制 | Results 图 5；Methods "transferQTL Model" 节 |
| 等位基因特异性与 eQTL 的关联不明确 | AS 事件与 eQTL 之间的因果关系缺乏直接证据 | 缺乏同时具有基因型、表观基因组和表达数据的匹配样本 | Results 图 4；Methods "Compatibility" 节 |

## 06 核心思想
### 1) 表面方法
- 构建 4 个个体的二倍体个人基因组（长读长测序 + 变异分型）
- 将 ~15 种功能基因组学实验（ChIP-seq、ATAC-seq、DNase-seq、WGBS、Hi-C、RNA-seq 等）的 reads 分别比对到两个单倍型，系统识别等位基因特异性（AS）事件
- 整合 AS 事件构建跨组织、跨实验的 AS 目录（>100 万 AS SNP）
- 开发三个应用：(a) 用 AS 数据"装饰"ENCODE cCRE 调控元件；(b) 用随机森林模型（transferQTL）跨组织转移 eQTL；(c) 用 DNABERT Transformer 模型从序列预测 AS 效应

### 2) 核心洞察
- **二倍体比对是 AS 检测的基础**：通过将 reads 比对到个人单倍型而非参考基因组，可以消除参考等位基因偏好（reference allele bias），实现更精确的等位基因特异性定量。
- **AS 事件是变异效应的天然读出**：AS 不需要扰动实验，直接比较同一细胞内两个等位基因的差异，天然控制反式环境，是评估变异对 TF 结合影响的理想范式。
- **局部序列上下文足以预测 AS 效应**：DNABERT Transformer 模型仅使用 250 bp 窗口内的序列信息即可达到 0.69-0.80 的 AUROC，说明 TF 结合变异效应主要由局部序列决定，而非远端调控或染色质环境。
- **AS 信息可增强 eQTL 转移**：染色质状态（特别是 H3K36me3 等）在目标组织中的存在与否，能有效预测 eQTL 是否在目标组织中活跃，实现跨组织 eQTL 注释。

### 3) 可能的普适教训 [Analysis]
- **匹配的基因型-表观基因组-表达数据是功能基因组学的黄金标准**：本文展示了当基因型、表观基因组和表达数据来自同一批个体时，可以构建比任何单一数据源都更强大的预测模型。
- **序列模型的可解释性可转化为生物学发现**：DNABERT 的注意力机制不仅用于预测，还可用于"重新发现"已知的 TF 结合基序（如 CTCF），说明深度学习模型可以用于基序发现。
- **"装饰"策略是整合异构数据的有效手段**：将 AS 信息映射到已有的调控元件注释上，可以显著提升注释的功能分辨率，这一策略可迁移到其他基因组注释任务。

## 07 方法总览
- **输入**：
  - 4 个个体的全基因组测序数据（Illumina 短读长 + 10x Genomics 链接读长 + PacBio/ONT 长读长）
  - ~30 组织的功能基因组学数据（ChIP-seq、ATAC-seq、DNase-seq、WGBS、Hi-C、RNA-seq、eCLIP、质谱蛋白质组）
- **输出**：
  - 4 个二倍体个人基因组
  - AS 目录（>100 万 AS SNP，涵盖 ASE、ASB、ASM、AS-chromatin 等）
  - 装饰后的 ENCODE cCRE 注释
  - transferQTL 模型预测的跨组织 eQTL
  - DNABERT Transformer 模型预测的 AS 效应
- **模块**：
  1. 个人基因组构建（变异检测、分型、单倍型组装）
  2. 二倍体比对与 AS 检测（等位基因特异性 reads 计数、统计检验）
  3. AS 目录整合与注释
  4. cCRE 装饰流程
  5. transferQTL 随机森林模型
  6. DNABERT Transformer 模型
- **训练**：
  - transferQTL：随机森林，使用染色质特征（组蛋白修饰、TF 结合、染色质可及性）预测 eQTL 转移
  - DNABERT：使用预训练的 DNABERT 权重初始化，在 AS 数据集上微调，输入为 250 bp 序列窗口
- **工具**：CrossStitch（基因组组装）、HapCUT2（分型）、STAR（RNA-seq 比对）、BWA（DNA 比对）、FastaAlternateReferenceMaker（构建个人参考）、DNABERT（深度学习）、randomForest（R 包）
- **反馈回路**：AS 检测结果用于训练预测模型，模型预测又可用于优先排序新的候选 AS 位点，形成"检测-预测-验证"的闭环
- **假设**：
  - 等位基因特异性 reads 计数服从二项分布（或 beta-binomial）
  - 局部序列上下文（250 bp）足以捕捉 TF 结合变异效应
  - 染色质状态在组织间的差异可用于预测 eQTL 的组织特异性

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 个人基因组构建 | 为每个个体生成二倍体参考序列，包含两个单倍型 | 传统参考基因组无法区分等位基因，导致 AS 信号丢失 | 输入：全基因组测序 reads；输出：分型后的二倍体基因组（VCF + 单倍型序列） | Methods "Personal Genome" 节；Results 图 1B | 移除后无法进行等位基因特异性分析，AS 目录无法构建 |
| 二倍体比对与 AS 检测 | 将功能基因组学 reads 分别比对到两个单倍型，统计等位基因特异性 reads | 精确量化两个等位基因的差异活性 | 输入：功能基因组学 reads + 二倍体基因组；输出：AS SNP 列表（含统计显著性） | Methods "AS Calling" 节；Results 图 1C | 移除后无法识别 AS 位点，后续所有应用（装饰、预测模型）均无法实现 |
| AS 目录整合 | 跨组织、跨实验整合 AS 事件 | 单组织 AS 检出率低，需要整合提高统计功效 | 输入：各组织 AS 检测结果；输出：统一 AS 目录（>100 万 SNP） | Results 图 1C；Methods "AS Catalog" 节 | 移除后 AS 位点数量大幅减少，无法支撑下游模型训练 |
| cCRE 装饰 | 将 AS 信息映射到 ENCODE cCRE 上，标注其等位基因特异性活性 | 增强现有调控元件注释的功能分辨率 | 输入：AS 目录 + ENCODE cCRE 列表；输出：装饰后的 cCRE 注释 | Results 图 3；Methods "Decoration Process" 节 | 移除后 cCRE 注释缺乏等位基因特异性信息，无法识别 AS 调控元件 |
| transferQTL 模型 | 随机森林模型，将 eQTL 从供体组织转移到目标组织 | 难获取组织缺乏 eQTL 数据 | 输入：供体组织 eQTL + 目标组织染色质特征；输出：目标组织 eQTL 预测 | Results 图 5；Methods "transferQTL Model" 节 | 移除后无法扩展 eQTL 目录到难获取组织 |
| DNABERT Transformer 模型 | 从 250 bp 序列窗口预测 SNP 是否导致 AS 效应 | 验证"序列上下文决定 TF 结合变异效应"假说 | 输入：SNP 周围 250 bp 序列；输出：AS 概率（AUROC 0.69-0.80） | Results 图 7；Methods "Transformer Model" 节 | 移除后无法从序列直接预测变异效应，需依赖实验数据 |
| 外部验证流程 | 在 NA12878、Roadmap ST2/ST3 等外部数据上验证模型 | 确保模型泛化性 | 输入：外部 AS 数据集；输出：模型性能指标 | Results 图 7B；Methods "External Validation" 节 | 移除后模型泛化性无法评估 |

## 09 关键公式符号
本文核心统计模型为等位基因特异性检测和预测模型，涉及以下关键公式：

1. **等位基因特异性检验（beta-binomial 检验）**：
   - 对每个杂合 SNP，假设参考等位基因 reads 数 $X$ 服从 beta-binomial 分布：$X \sim \text{BetaBinomial}(n, \alpha, \beta)$，其中 $n$ 为总 reads 数，$\alpha, \beta$ 为 beta 分布参数
   - 零假设为无等位基因偏好：$P(X = k) = \binom{n}{k} 0.5^n$
   - 备择假设允许偏离 0.5 的等位基因比例

2. **AS 富集的比值比（Odds Ratio, OR）**：
   - $\text{OR} = \frac{a/b}{c/d}$
   - 其中 $a$ 为 AS SNP 在 motif 中的数量，$b$ 为非 AS SNP 在 motif 中的数量，$c$ 为 AS SNP 不在 motif 中的数量，$d$ 为非 AS SNP 不在 motif 中的数量
   - 用于衡量 TF motif 中 AS SNP 的富集程度（Results 图 6A）

3. **DNABERT 模型**：
   - 输入：250 bp 序列窗口（128 bp 上游 + SNP + 128 bp 下游）
   - 输出：$P(\text{AS})$，即 SNP 导致等位基因特异性结合的概率
   - 损失函数：二元交叉熵 $\mathcal{L} = -\frac{1}{N}\sum_{i=1}^{N}[y_i \log(p_i) + (1-y_i)\log(1-p_i)]$
   - 评估指标：AUROC（受试者工作特征曲线下面积）

4. **transferQTL 随机森林模型**：
   - 特征：目标组织中 SNP 附近的染色质状态（组蛋白修饰、TF 结合、染色质可及性）
   - 响应变量：SNP 是否为目标组织中的 eQTL
   - 性能指标：平衡准确率（balanced accuracy）= 0.86

5. **GWAS 富集分析（超几何检验）**：
   - $P(X = k) = \frac{\binom{K}{k}\binom{N-K}{n-k}}{\binom{N}{n}}$
   - 其中 $N$ 为基因组中 cCRE 总数，$K$ 为携带 GWAS SNP 的 cCRE 数，$n$ 为特定组织 cCRE 数，$k$ 为特定组织中携带 GWAS SNP 的 cCRE 数

## 10 实验设计与证据链
- **数据集**：
  - 4 个供体（2 男 2 女，年龄 37-54 岁），~30 组织，~15 种实验，共 1635 个数据集
  - 外部验证：NA12878（CEPH 个体）、Roadmap 个体 STL002/STL003
  - 外部 eQTL 目录：GTEx v8、eQTLGen 等
- **指标**：
  - AS 检测：等位基因特异性 reads 比例、统计显著性（FDR < 0.1）
  - 模型性能：AUROC、平衡准确率
  - 富集分析：比值比（OR）、超几何检验 p 值
- **基线/对照**：
  - DNABERT 模型对照：logistic 回归、随机森林（基于序列嵌入）、仅 motif 匹配的简单模型
  - transferQTL 对照：仅使用供体组织信息的模型、随机猜测
  - AS 富集对照：非 AS SNP 作为背景
- **关键实验**：
  1. **AS 目录构建**：4 个个体 × ~30 组织 × 12 种实验，识别 >100 万 AS SNP（Results 图 1C）
  2. **cCRE 装饰**：将 AS 信息映射到 ENCODE cCRE，发现 AS cCRE 在组织特异性调控中富集（Results 图 3）
  3. **TF motif 敏感性分析**：对 660 个 TF motif 进行 AS SNP 富集分析，识别出 195 个"AS 敏感"motif，其中 C2H2 锌指家族显著富集（Results 图 6A-B）
  4. **DNABERT 预测**：训练 Transformer 模型预测 CTCF 等 TF 的 AS 结合，AUROC = 0.69-0.80，显著优于基线模型（Results 图 7B）
  5. **transferQTL 跨组织转移**：从皮肤等易获取组织转移 eQTL 到心脏等难获取组织，平衡准确率 0.86（Results 图 5B）
  6. **外部验证**：在 NA12878 和 Roadmap 个体上验证 AS 预测模型，AUROC 0.74（Results 图 7B）
- **证据链逻辑**：从数据资源构建（AS 目录）→ 生物学发现（TF motif 敏感性、AS 与保守性关系）→ 预测模型（DNABERT、transferQTL）→ 外部验证，形成完整的"资源-发现-建模-验证"链条。

## 11 结论正确解读
- **任务范围**：本文的 AS 预测模型（DNABERT）预测的是"SNP 是否在至少一个组织中导致等位基因特异性结合/染色质状态"，而非组织特异性预测。模型是组织无关的（tissue-independent）。
- **oracle/真值输入**：AS 标签来自 EN-TEx 自身的 ChIP-seq/ATAC-seq 等实验数据，通过二倍体比对和统计检验获得。外部验证使用 NA12878 和 Roadmap 数据。
- **端到端状态**：DNABERT 模型是端到端训练的（序列 → AS 概率），但 transferQTL 模型依赖中间特征（染色质状态），不是端到端。
- **算力成本**：DNABERT 微调需要 GPU 资源，但具体算力未在文中详述。
- **历史数据依赖**：模型训练依赖 EN-TEx 4 个个体的数据，AS 标签的全面性受限于测序深度和组织覆盖。
- **模型依赖**：DNABERT 预测依赖预训练权重（来自人类基因组），transferQTL 依赖 ENCODE/GTEx 注释。
- **最难情形**：模型在低频变异、稀有变异上的表现可能较差，因为训练数据中稀有变异的 AS 信号不足。
- **群体/领域边界**：EN-TEx 仅包含 4 个欧洲裔个体，AS 目录对非欧洲人群的覆盖有限；模型预测可能在其他群体中表现下降。
- **不确定性**：AS 检测的统计功效受测序深度影响，低深度组织的 AS 位点可能被漏检；模型预测的 AS 效应需要实验验证。
- **有边界的复述**：本文证明，在 EN-TEx 的 4 个欧洲裔个体中，基于 250 bp 局部序列上下文的 DNABERT Transformer 模型能够以 AUROC 0.69-0.80 的准确率预测 SNP 对 TF 结合（特别是 CTCF）的等位基因特异性影响，且该预测能力主要来自序列上下文而非组织特异性信息。这一结论的适用范围限于常见变异和已覆盖的组织类型。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 供体数量有限 | 仅 4 个个体，统计功效不足以进行个体间比较 | 扩展到更大队列 | Discussion "Limitations of the Study" |
| 缺乏技术重复 | 多数实验无技术重复，影响 AS 检测的可靠性 | 增加重复实验 | Discussion "Limitations of the Study" |
| 组织覆盖不完整 | 部分组织仅来自部分个体，无法进行完整的跨个体比较 | 补充更多组织-个体组合 | Discussion "Limitations of the Study" |
| 罕见变异覆盖不足 | AS 目录主要覆盖常见变异，罕见变异的 AS 信号不足 | 结合更大规模测序数据 | Discussion "Limitations of the Study" |
| 模型为组织无关预测 | DNABERT 模型不区分组织，无法捕捉组织特异性调控 | 开发组织特异性模型 | Discussion "Limitations of the Study" |
| 缺乏实验验证 | 预测的 AS 效应未通过 CRISPR 等实验验证 | 结合高通量实验验证 | Discussion "Limitations of the Study" |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| DNABERT 模型仅使用 250 bp 序列窗口 | 远端增强子-启动子互作可能对 TF 结合变异效应有贡献，但模型未纳入 | 若远端调控重要，模型可能高估局部序列的作用 | 在模型中纳入 Hi-C 互作信息，比较性能变化 | Results 图 7；Methods "Transformer Model" 节 |
| AS 检测依赖二倍体比对，但仅覆盖杂合 SNP | 纯合变异和结构变异（SV）的效应无法通过 AS 分析检测 | SV 可能对 TF 结合有更大效应，但被系统遗漏 | 结合 SV 的等位基因特异性分析 | Methods "AS Calling" 节 |
| 4 个供体均为欧洲裔 | 非欧洲人群的 AS 模式和 TF 结合变异效应可能不同 | 模型可能在其他群体中表现下降，限制普适性 | 在非欧洲人群数据上验证模型 | Methods "Sample Selection" 节 |
| transferQTL 模型依赖染色质特征，但染色质数据本身可能受变异影响 | 存在循环论证风险：用受变异影响的染色质预测变异效应 | 可能高估模型性能 | 使用独立于染色质的特征（如序列保守性）进行对照 | Methods "transferQTL Model" 节 |
| DNABERT 注意力分析"重新发现"已知 motif | 这可能是模型记忆训练数据的结果，而非真正的基序发现能力 | 需要验证模型是否能发现新 motif | 在 held-out 数据上测试新 motif 发现能力 | Results 图 7D-F |
| AS 目录中 95% 的变异仅由非 RNA 实验检测 | 非 RNA 实验（如 ChIP-seq）的 AS 信号可能与 RNA 表达不一致 | 需要整合多组学 AS 信号以全面评估变异效应 | 比较不同实验类型 AS 信号的一致性 | Results 图 1C；Data S8B-C |

## 14 个人收获与启示
- **二倍体比对是 AS 分析的基础设施**：本文展示了将功能基因组学数据比对到个人二倍体基因组而非参考基因组的巨大优势。对于 TF–DNA 结合研究，这一策略可以直接量化变异对结合的影响，无需扰动实验。
- **序列上下文是 TF 结合变异效应的主导因素**：DNABERT 模型仅用 250 bp 序列即可达到 0.69-0.80 AUROC，说明局部序列特征（motif 破坏/创建、间距、侧翼序列）是决定变异效应的主要因素。这为基于序列的 TF 结合预测提供了强有力支持。
- **AS 敏感 motif 的概念**：本文识别出 195 个对变异特别敏感的 TF motif（主要是 C2H2 锌指），这一概念可直接迁移到 TF–DNA 结合机制研究中——某些 TF 的结合位点对序列变异特别脆弱，可能是疾病相关变异的富集位点。
- **"装饰"策略的通用性**：将 AS 信息映射到已有调控元件注释上，可以显著提升注释的功能分辨率。这一策略可迁移到其他基因组注释任务（如增强子、绝缘子、启动子注释）。
- **Transformer 注意力可用于基序发现**：DNABERT 的注意力机制可以"重新发现"已知 TF 基序，说明注意力权重可以用于识别对结合关键的序列位置。这一方法可迁移到 TF–DNA 结合机制研究中，用于发现新的结合模式或关键核苷酸位置。
- **跨组织 eQTL 转移的可行性**：通过染色质状态特征，可以将 eQTL 从易获取组织转移到难获取组织，这对难以活检的组织（如心脏、脑）的功能基因组学研究具有重要价值。

## 15 与已有知识连接
- **ENCODE 项目**：本文是 ENCODE 项目的延伸，使用 ENCODE 标准化的实验流程和数据处理管线，其 cCRE 装饰直接基于 ENCODE 的调控元件注释（Methods "Decoration Process" 节）。与 ENCODE 3 的 cCRE 定义一致。
- **GTEx 项目**：EN-TEx 的 4 个供体来自 GTEx 队列，eQTL 分析使用 GTEx v8 目录。本文的 transferQTL 模型直接扩展了 GTEx eQTL 的应用范围。
- **DNABERT**：本文使用 DNABERT 作为预训练模型进行微调，DNABERT 是 BERT 架构在 DNA 序列上的应用（Ji et al., 2021）。本文展示了 DNABERT 在变异效应预测中的新应用。
- **等位基因特异性表达（ASE）研究**：本文的 AS 分析框架与早期 ASE 研究（如 AlleleDB、GEUVADIS）一致，但扩展到了染色质层面（组蛋白修饰、TF 结合、染色质可及性）。
- **TF motif 数据库**：本文使用 CIS-BP 数据库的 660 个人类 TF motif 进行富集分析，与 JASPAR、TRANSFAC 等数据库互补。
- **深度学习在调控基因组学中的应用**：与 Enformer（Avsec et al., 2021）、Basenji（Kelley et al., 2018）等模型相比，本文的 DNABERT 模型更专注于变异效应预测，且利用了等位基因特异性标签。
- **3D 基因组**：本文的 Hi-C 数据分析与 3D 基因组研究（如 TAD、A/B compartment）相关，但主要作为 AS 分析的一个维度，未深入探讨 3D 结构对 TF 结合变异效应的影响。

## 16 研究想法
### 候选 1：基于 DNABERT 的 TF 结合变异效应预测模型优化
- **名称**：TF-BindVar：基于 Transformer 的 TF 结合变异效应预测
- **来源局限/观察**：本文的 DNABERT 模型是组织无关的，且仅使用 250 bp 序列窗口。对于 TF–DNA 结合机制研究，需要组织特异性预测和更长的序列上下文。
- **核心假设**：将组织特异性染色质状态（如 ATAC-seq、H3K27ac）作为额外输入特征，可以提升 TF 结合变异效应的预测精度，特别是在组织特异性调控区域。
- **初步方法**：在 DNABERT 基础上，将组织特异性染色质特征（如峰值强度、染色质状态注释）编码为额外 token 或特征向量，与序列 embedding 拼接后输入 Transformer。在 EN-TEx 数据上训练和验证。
- **验证方式**：使用 EN-TEx 的 ASB 数据作为标签，比较加入染色质特征前后的 AUROC 变化；在外部数据集（如 Roadmap）上验证泛化性。
- **创新状态**：unverified

### 候选 2：AS 敏感 TF motif 的系统性鉴定与机制解析
- **名称**：SensitiveMotif Atlas：人类 TF 结合位点变异敏感性的系统图谱
- **来源局限/观察**：本文识别了 195 个 AS 敏感 motif，但仅基于 EN-TEx 4 个个体。不同 TF 的 DNA 结合域结构差异可能导致不同的变异敏感性模式。
- **核心假设**：TF 的 DNA 结合域结构（如锌指数目、接触残基）与其 motif 的变异敏感性相关，可以通过结构特征预测 TF 的变异敏感性。
- **初步方法**：整合 EN-TEx ASB 数据、CIS-BP motif 数据库、AlphaFold 预测的 TF 结构，计算每个 TF 的变异敏感性得分，并与结构特征（如结合域长度、接触残基数、motif 信息含量）进行关联分析。
- **验证方式**：使用外部 ASB 数据集（如个人基因组计划）验证敏感性得分的可重复性；通过 EMSA 或 HT-SELEX 实验验证预测的高敏感 TF。
- **创新状态**：unverified

### 候选 3：基于物理模拟的 TF–DNA 结合变异效应预测
- **名称**：PhysTF：结合分子动力学模拟与深度学习的 TF–DNA 结合变异效应预测
- **来源局限/观察**：本文的 DNABERT 模型是纯数据驱动的，缺乏物理约束。对于 TF–DNA 结合机制，物理模拟可以提供结合自由能的定量估计。
- **核心假设**：将分子动力学模拟计算的 TF–DNA 结合自由能变化（ΔΔG）作为先验特征，可以提升变异效应预测的准确性和可解释性。
- **初步方法**：选取 10-20 个代表性 TF（如 CTCF、FOXO3、ZNF460），对每个 TF 的野生型和突变型 DNA 结合进行分子动力学模拟，计算 ΔΔG。将 ΔΔG 作为特征加入 DNABERT 模型，比较性能变化。
- **验证方式**：使用 EN-TEx ASB 数据作为标签，比较加入 ΔΔG 特征前后的 AUROC 变化；通过表面等离子体共振（SPR）实验验证预测的 ΔΔG 值。
- **创新状态**：unverified

### 候选 4：跨组织 eQTL 转移的深度学习模型
- **名称**：DeepTransfer-eQTL：基于深度学习的跨组织 eQTL 转移预测
- **来源局限/观察**：本文的 transferQTL 模型使用随机森林，特征主要是染色质状态。深度学习模型可能捕捉更复杂的特征交互。
- **核心假设**：深度学习模型（如图神经网络或 Transformer）可以更好地利用 EN-TEx 的多组织染色质数据，实现更准确的跨组织 eQTL 转移。
- **初步方法**：将 EN-TEx 的多组织染色质特征构建为图结构（节点为组织，边为组织间相似性），使用图神经网络预测 eQTL 在目标组织中的活性。与随机森林基线比较。
- **验证方式**：使用 GTEx 的 eQTL 数据作为标签，比较图神经网络与随机森林的平衡准确率；在独立数据集上验证。
- **创新状态**：unverified

### 候选 5：AS 变异与疾病关联的整合分析
- **名称**：AS-Disease：等位基因特异性变异在疾病中的富集分析框架
- **来源局限/观察**：本文发现 AS 变异与 GWAS 位点显著共定位，但未系统分析 AS 变异在疾病中的富集模式。
- **核心假设**：AS 变异在疾病相关调控区域中显著富集，且不同疾病类型富集的 TF 类别不同。
- **初步方法**：将 EN-TEx AS 目录与 GWAS Catalog、ClinVar 等数据库整合，计算 AS 变异在疾病相关区域中的富集程度，并分析富集的 TF 类别与疾病类型的关联。
- **验证方式**：使用置换检验评估富集显著性；在独立数据集中验证。
- **创新状态**：unverified