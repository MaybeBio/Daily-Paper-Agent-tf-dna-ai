## 01 基本信息

- **标题**：Ascertainment bias in the genomic test of positive selection on regulatory sequences
- **作者与单位**：Jiang D; Zhang J（美国密歇根大学，University of Michigan）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2023
- **论文类型**：方法学批评/再分析（Methodological critique & re-analysis）
- **领域**：群体遗传学、调控序列进化、正选择检测
- **关键词**：ascertainment bias, positive selection, transcription factor binding sites (TFBS), cis-regulatory evolution, deltaSVM, gkm-SVM
- **DOI/arXiv 号**：10.1101/2023.08.20.554030
- **代码**：未提供（但使用了 Liu & Robinson-Rechavi 的公开数据，见 GitHub 链接）
- **数据**：Liu & Robinson-Rechavi (2020) 公开的人类 CEBPA、HNF4A、CTCF 结合位点数据及 SVM 权重文件（GitHub 链接见 Methods）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文不直接开发新的 AI 预测模型，而是对「基于机器学习预测 TF–DNA 结合亲和力（gkm-SVM/deltaSVM）来检测调控序列正选择」这一新兴方法进行统计偏差审计。对「TF–DNA 结合机制 × AI」方向的核心贡献在于：揭示了「以实验鉴定到的 TFBS 为分析对象」这一普遍做法会引入系统性 ascertainment bias，导致正选择检测的假阳性率膨胀。该结论对任何使用 ChIP-seq 鉴定 TFBS 后做进化或功能分析的 AI 方法均有警示意义。

## 02 一句话总结

本文通过计算机模拟证明：基于 gkm-SVM 预测的 deltaSVM 正选择检测方法，因仅分析实验可检测到的 TFBS（ascertainment bias），在无选择中性进化下也会产生显著高于预期水平的假阳性；应用三种校正方法后，此前报道的人类三个 TF（CEBPA、HNF4A、CTCF）结合位点的正选择信号几乎全部消失。

## 03 研究问题

- **具体问题**：Liu & Robinson-Rechavi (2020) 提出的基于 deltaSVM 的 TFBS 正选择检测方法，其统计推断是否因「仅分析实验鉴定的 TFBS」这一取样偏差而产生系统性假阳性？
- **为什么重要**：cis-调控序列进化被认为是适应性表型变化的重要来源，但检测调控序列正选择在统计上极为困难。若新方法因 ascertainment bias 产生大量假阳性，将误导对调控进化普遍性的认识。
- **现有方法为何不足**：传统方法（如同义/非同义位点比较、种间保守性分析）难以应用于非编码调控序列，因为缺乏明确的中性参照。deltaSVM 方法通过机器学习预测结合亲和力来构建中性零分布，看似解决了参照问题，但忽略了「TFBS 如何被纳入分析数据集」这一非随机过程。
- **精确研究问题**：Can the genomic test of positive selection on TFBSs based on deltaSVM produce unbiased false positive rates when the analyzed TFBSs are ascertained by experimental detection (e.g., ChIP-seq) in the focal species?

## 04 背景与发展脉络

*注：以下脉络为「经外部核验」的领域发展概述，结合本文引用与课题常识。*

1. **阶段一：编码序列正选择检测（1980s–2000s）**。以 dN/dS（Ka/Ks）比值为核心，以同义替换为中性参照。代表方法：PAML 系列（Yang 1997）。优点：统计框架成熟；局限：不适用于非编码调控序列。
2. **阶段二：调控序列正选择检测的早期尝试（2000s–2010s）**。方法包括：种间保守性缺失（如 conserved noncoding sequence 的加速进化）、群体遗传学检验（如 Tajima's D、MK 检验扩展）。代表：Pollard et al. (2010) phyloP/phastCons。优点：可检测保守区域加速进化；局限：对功能方向性（增强/减弱）不敏感，统计功效低。
3. **阶段三：机器学习预测结合亲和力用于进化推断（2015–2020）**。核心突破：用 gkm-SVM（Ghandi et al. 2014; Lee et al. 2015）从 ChIP-seq 数据学习 TF 结合特异性的序列特征，可对任意 DNA 序列预测结合亲和力（deltaSVM 分数）。Liu & Robinson-Rechavi (2020) 首次将该工具用于正选择检测：对每个已知 TFBS，以祖先序列为参照，生成大量突变邻居的 deltaSVM 分布作为零分布，检验真实衍生序列的 deltaSVM 是否显著偏高。
4. **本文位置（2023）**：对阶段三的方法进行统计审计，指出其忽略了 ascertainment bias——即「已知 TFBS」本身是实验检测的产物，其结合亲和力分布已被截断，导致零分布构建有偏。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| Ascertainment bias（确定偏倚） | 已知 TFBS 的结合亲和力系统性偏高，导致中性零分布被低估 | 实验鉴定（ChIP-seq）只能捕获结合亲和力足够高的位点；低亲和力位点无法被检测，因此不会进入分析数据集 | Results 节 "Interpretation of P-values" 的数学推导；Fig. 1 示意 |
| 假阳性率膨胀 | 中性模拟数据中，正选择检测的假阳性率显著高于名义水平（1%） | 因 P'（条件概率）被误当作 P（无条件概率）计算，P 值被系统性低估 | Results 表 1：无 ascertainment bias 时假阳性率≈1%，有 bias 时随 bias 程度升高至 11 倍 |
| 统计推断的无效性 | 无法从「显著位点比例 > 1%」推断正选择存在 | 因零分布本身有偏，比例检验的参照基准失效 | Results 节 "Most positive selection signals disappear" 的再分析结果 |
| 多检验校正的基准错误 | 校正后仍可能保留假阳性 | 校正所需的总检验数（M）被低估，因为未计入未检测到的 TFBS | Methods 节 "Reanalysis of human TFBSs" 中四种 M 估计方法的对比 |

## 06 核心思想

**1) 表面方法**：
- 对 Liu & Robinson-Rechavi (2020) 的 deltaSVM 正选择检测方法进行数学分析，指出其 P 值计算忽略了「TFBS 被纳入数据集」这一条件事件。
- 通过计算机模拟（50,000 个随机 10-mer 祖先序列，各引入 2 个随机替换）验证 ascertainment bias 对假阳性率的影响。
- 提出三种校正方法（方法 1：以 2×正 deltaSVM 位点数估计总检验数；方法 2：利用模拟数据中 bias 程度与正 deltaSVM 比例的经验关系；方法 3：以全基因组潜在结合位点数估计总检验数），重新分析三个人类 TF 的数据。

**2) 核心洞察**：
- 正选择检测的零分布必须基于「所有可能进入数据集的序列」构建，而非「实际进入数据集的序列」。实验检测阈值（ChIP-seq 可检测性）截断了低亲和力位点，使得「已知 TFBS」的 deltaSVM 分布天然右偏——即使完全中性进化，也容易落入右尾。
- 类比：若只考察期末考试成绩优秀的学生，会发现他们期中成绩「显著提高」——这是回归到均值（regression to the mean）的统计假象，而非真实进步。

**3) 可能的普适教训 [Analysis]**：
- 任何使用「实验鉴定的功能元件」作为分析对象的进化/功能研究，都必须考虑鉴定过程本身的非随机性。这一教训不仅适用于 TFBS，也适用于增强子、启动子、eQTL 等一切通过实验筛选得到的调控元件。
- 对 AI 预测模型而言，训练数据（ChIP-seq 阳性位点 + 阴性对照）本身已包含 ascertainment bias，模型学到的「结合特异性」可能高估真实亲和力分布的上尾。下游进化推断需显式建模这一偏差。

## 07 方法总览

- **输入**：
  - 模拟数据：50,000 个随机 10-mer 祖先序列；每个序列随机引入 2 个替换生成衍生序列。
  - 真实数据：Liu & Robinson-Rechavi (2020) 公开的人类 CEBPA（5,807 个 TFBS）、HNF4A、CTCF 结合位点及对应的 deltaSVM 值、P 值。
  - SVM 权重文件：三个 TF 的 10-mer 权重（来自 Liu & Robinson-Rechavi 的 GitHub 仓库）。
- **输出**：校正后的正选择位点比例、校正后的假阳性率估计、校正后的显著位点数量。
- **模块**：
  1. **数学推导模块**：证明 P'（条件概率）< P（无条件概率），即 ascertainment bias 导致 P 值被低估。
  2. **模拟模块**：生成中性进化数据，模拟不同强度 ascertainment bias（移除最低 10%–90% deltaSVM 位点），计算假阳性率。
  3. **校正模块**：三种方法估计总检验数 M，计算 Benjamini-Hochberg 校正后的 adjusted P 值。
  4. **再分析模块**：对三个 TF 的真实数据应用四种方法（方法 0–3）计算 adjusted P 值，比较显著位点数量。
- **训练**：无模型训练；使用已训练的 gkm-SVM 模型（Liu & Robinson-Rechavi 提供）进行预测。
- **反馈回路**：无（静态分析）。
- **假设**：
  - 模拟中替换为完全随机（无突变偏好、无选择）。
  - 缺失的 TFBS 不太可能具有小 P 值（即不太可能显示正选择信号）。
  - 人类基因组大小设为 6×10⁹（二倍体，双链）。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 数学推导（P' vs P） | 证明 ascertainment bias 导致 P 值系统性低估 | 建立理论框架，说明偏差的必然性 | 输入：事件 I（TFBS 被纳入数据集）与事件 Δ>Δ_obs 的条件概率关系；输出：不等式 P' < P | Results 节 "Interpretation of P-values" 的推导 | 无此模块则无法从理论上说明偏差的普遍性 |
| 中性模拟 | 量化 ascertainment bias 对假阳性率的影响 | 验证理论预测，提供 bias 程度与假阳性率的定量关系 | 输入：50,000 随机 10-mer + 2 替换；输出：不同 bias 水平下的假阳性率 | 表 1：无 bias 时假阳性率≈1%；90% bias 时达 11 倍 | 无此模块则无法估计偏差的实际幅度 |
| 方法 1 校正（2×正 deltaSVM） | 估计总检验数 M | 因缺失位点未计入，M 被低估 | 输入：正 deltaSVM 位点数；输出：M = 2×正 deltaSVM 数 | 表 2：CEBPA 校正后比例从 7.51% 降至 6.03% | 校正不充分，仍可能低估 M |
| 方法 2 校正（模拟回归） | 利用模拟中 bias 与正 deltaSVM 比例的关系估计 M | 方法 1 可能低估，需更精确估计 | 输入：模拟数据中 F_removed 与 F+ 的线性关系；输出：M = N/(1-F_removed) | 表 S3、图 S1 | 依赖模拟模型的准确性；若真实缺失机制不同则校正有偏 |
| 方法 3 校正（全基因组潜在位点） | 以全基因组所有可能成为 TFBS 的位点数为 M | 提供最保守的校正 | 输入：基因组大小 L、TFBS 平均长度 l、P(n≥2)；输出：M = LP(n≥2)/l | 表 2：CEBPA 校正后比例降至 0.0401% | 可能过度校正（overcorrection），因并非所有潜在位点都有功能 |
| 真实数据再分析 | 评估校正后正选择信号是否仍存在 | 回答核心问题：原始结论是否稳健 | 输入：三个 TF 的 deltaSVM 数据；输出：校正后显著位点数量 | 表 2、表 3：方法 3 下三个 TF 均无 adjusted P < 0.01 的位点 | 无此模块则无法直接挑战原始结论 |

## 09 关键公式符号

**1. P 值定义（原始方法）**：
- P = Prob(Δ > Δ_obs)，其中 Δ = deltaSVM 在中性进化下的变化量，Δ_obs = 观察到的 deltaSVM 变化。
- 零分布：由祖先序列的所有 2 步突变邻居的 deltaSVM 构成。

**2. 条件概率（实际计算的量）**：
- P' = Prob(Δ > Δ_obs | I)，其中 I = 该 TFBS 被纳入数据集（即被实验检测到）的事件。
- 关键不等式：Prob(Δ > Δ_obs ∩ I) < Prob(Δ > Δ_obs)·Prob(I)，因此 P' < P。
- 含义：因高 deltaSVM 位点更可能被检测到（Prob(I) 与 Δ_obs 正相关），条件化后 P' 系统性低于真实 P。

**3. Benjamini-Hochberg 校正**：
- adjusted P_(i) = P_(i) × M / i，其中 P_(i) 为第 i 小的原始 P 值，M 为总检验数。
- 方法 0：M = 数据集中 TFBS 数。
- 方法 1：M = 2 × (正 deltaSVM 的 TFBS 数)。
- 方法 2：M = N / (1 - F_removed)，其中 F_removed 由模拟回归 F_removed = kF+ + b 估计。
- 方法 3：M = L × P(n≥2) / l，其中 L = 6×10⁹（人类基因组大小），l = 平均 TFBS 长度（CEBPA: 269, HNF4A: 340, CTCF: 537），P(n≥2) = 数据集中有 ≥2 个替换的 TFBS 比例。

**4. 模拟设计**：
- 50,000 个随机 10-mer，每个引入 2 个随机替换（无偏好、无选择）。
- 移除最低 10%–90% deltaSVM 位点模拟 ascertainment bias。

## 10 实验设计与证据链

**数据集/群体**：
- 模拟数据：50,000 个随机 10-mer 序列（中性进化，2 个替换）。
- 真实数据：人类 CEBPA（5,807 TFBS）、HNF4A、CTCF 结合位点（来自 Liu & Robinson-Rechavi 2020 的公开数据）。

**指标**：
- 假阳性率（false positive rate）：模拟数据中 P < 0.01 的位点比例。
- 正选择位点比例：真实数据中 P < 0.01 的位点比例。
- Adjusted P 值：Benjamini-Hochberg 校正后仍显著的位点数。

**基线/对照**：
- 无 ascertainment bias 的模拟数据（不移除任何位点）作为基线。
- 方法 0（不校正）作为对照。

**评测协议**：
- 模拟：比较不同 bias 水平（移除 10%–90% 低位点）下的假阳性率。
- 真实数据：比较四种方法（0–3）下的显著位点数量。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-------------|-------------------|------|
| 模拟：无 bias vs. 有 bias | Ascertainment bias 是否导致假阳性率升高 | 50,000 中性位点；移除 0% vs. 10%–90% 低位点 | 无 bias 时假阳性率≈1%；有 bias 时显著升高，90% bias 时达 11 倍 | Ascertainment bias 确实导致假阳性率膨胀 | 模拟条件（随机 10-mer、2 替换）可能不完全反映真实 TFBS 进化 | 表 1 |
| 模拟：三个 TF 的重复 | 结论是否对 TF 类型稳健 | CEBPA、HNF4A、CTCF 分别模拟 | 三个 TF 结果高度相似 | 偏差是方法学固有的，不依赖特定 TF | 三个 TF 均为人类 TF，未覆盖其他物种 | 表 S1–S2 |
| 真实数据：方法 0 vs. 方法 1–3 | 原始正选择信号是否稳健 | 对三个 TF 的 5,807–16,212 个位点应用四种校正 | 方法 0 下 CEBPA 有 7.51% 位点显著；方法 3 下降至 0.0401% | 原始信号大部分是 ascertainment bias 的假象 | 方法 3 可能过度校正；不能完全排除少数真实正选择位点 | 表 2 |
| 真实数据：adjusted P 值 | 校正后是否有个体位点仍显著 | 方法 0–3 的 adjusted P < 0.01 或 0.05 位点数 | 方法 3 下三个 TF 均无 adjusted P < 0.01 位点；CEBPA 在方法 1 下有 80 个 adjusted P < 0.05 位点 | 几乎没有可靠的个体正选择位点 | 方法 1 和 2 校正不充分，可能仍保留假阳性 | 表 3 |

## 11 结论正确解读

- **任务范围**：本文仅针对 Liu & Robinson-Rechavi (2020) 的 deltaSVM 正选择检测方法进行审计，不涉及其他正选择检测方法（如 dN/dS、MK 检验等）。
- **Oracle/真值输入**：模拟数据中，所有进化均为中性（无正选择），因此所有「显著」结果均为假阳性——这是评估 bias 的黄金标准。
- **端到端状态**：本文是完整的端到端分析（理论推导 + 模拟验证 + 真实数据再分析），但未提供新的检测方法替代方案。
- **算力成本**：极低（模拟 50,000 个 10-mer 的 deltaSVM 计算，常规 CPU 即可）。
- **历史数据依赖**：依赖 Liu & Robinson-Rechavi 公开的 SVM 权重和 deltaSVM 数据；不依赖新的实验数据。
- **模型依赖**：依赖 gkm-SVM 预测的准确性；若 gkm-SVM 本身有偏差，本文结论的定量部分可能受影响，但定性结论（ascertainment bias 存在）不依赖具体模型。
- **最难情形**：方法 3 的校正依赖对「全基因组潜在 TFBS 数」的估计，该估计高度依赖 TFBS 长度和基因组大小假设，不确定性大。
- **群体/领域边界**：结论适用于以 ChIP-seq 鉴定 TFBS 为分析对象的进化研究；不适用于以随机突变扫描或合成生物学方式获得的位点。
- **不确定性**：作者承认方法 1 和 2 校正不充分，方法 3 可能过度校正；真实的正选择比例可能在 0% 到 0.04% 之间。
- **有边界的复述**：在 gkm-SVM 预测准确、模拟条件（随机 10-mer、2 替换）合理的假设下，基于 ChIP-seq 鉴定的人类 TFBS 的 deltaSVM 正选择检测，其报告的显著信号大部分可归因于 ascertainment bias；校正后几乎没有位点达到 adjusted P < 0.01 的显著性。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 方法 1 校正不充分 | 仅以 2×正 deltaSVM 位点数估计 M，仍低估总检验数 | 无明确建议 | Results 节 "Most positive selection signals disappear" |
| 方法 2 可能不准确 | 依赖模拟数据中 bias 与正 deltaSVM 比例的线性关系；真实缺失机制可能不同 | 无明确建议 | Discussion 节 |
| 方法 3 可能过度校正 | 假设所有基因组区域都有潜力成为 TFBS，可能高估 M | 若可建模不同区域成为 TFBS 的异质性概率，方法 3 可改进 | Discussion 节 |
| 模拟条件简化 | 模拟仅考虑随机 10-mer 和 2 个替换，未考虑突变偏好、选择、插入缺失等 | 无明确建议 | Methods 节 "Analysis of simulated TFBSs" |
| 未覆盖非人类数据 | 真实数据仅来自人类三个 TF | 无明确建议 | 全文 |

**作者提及的相关约束（非正式局限）**：
- 作者指出，即使校正后 CEBPA 仍有少量 adjusted P < 0.05 的位点（方法 1 下 80 个），但这些位点可能是「幸存者偏差」——即真实正选择位点更可能被 ChIP-seq 检测到，因此校正可能过度惩罚了真实信号。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 模拟仅使用随机 10-mer 作为祖先序列 | 真实 TFBS 的祖先序列可能具有特定的碱基组成或 motif 结构，影响 deltaSVM 分布 | 若真实祖先序列的 deltaSVM 分布与随机序列不同，bias 的定量估计可能不准 | 使用真实祖先重建序列（如从多种哺乳动物基因组推断）重复模拟 | Methods 节 "Analysis of simulated TFBSs" |
| 方法 3 假设所有基因组区域可成为 TFBS | 染色质可及性、核小体定位、DNA 甲基化等会限制潜在 TFBS 位点 | 若实际潜在位点远少于全基因组估计，方法 3 会过度校正，掩盖真实信号 | 使用染色质可及性数据（如 DNase-seq/ATAC-seq）限定潜在位点集合 | Discussion 节 |
| 作者未提供替代的正选择检测方法 | 批评现有方法但未给出改进方案，读者无法直接应用 | 课题方向需要可操作的替代方案 | 开发考虑 ascertainment bias 的贝叶斯或似然比检验框架 | 全文 |
| 对 gkm-SVM 模型本身的偏差未讨论 | gkm-SVM 的训练数据（ChIP-seq 阳性 + 阴性）可能已包含 bias，影响所有下游预测 | 若模型本身有偏，即使校正 ascertainment bias 也无法恢复无偏推断 | 使用独立验证集（如 SELEX、MITOMI 等体外结合数据）评估 gkm-SVM 预测的准确性 | 未提供 |
| 作者假设「缺失 TFBS 不太可能有小 P 值」 | 若某些真实正选择位点因结合亲和力过高而饱和（超出 ChIP-seq 动态范围），可能被错误排除 | 饱和效应可能导致高亲和力位点被遗漏，而非低亲和力位点 | 检查 ChIP-seq 信号强度与 deltaSVM 的关系，评估是否存在饱和 | Results 节 "Most positive selection signals disappear" 的假设 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **Ascertainment bias 的数学框架**：当分析对象是「实验可检测到的功能元件」时，P 值计算必须条件化于检测事件 I。本文的 P' < P 不等式提供了一个通用框架，可迁移到任何基于实验筛选数据的进化推断。**迁移到本课题**：在使用 ChIP-seq 数据训练 TF–DNA 结合预测模型时，训练集只包含高亲和力位点，模型对低亲和力位点的预测能力未知；下游进化分析（如正选择检测）需显式建模这一截断。

2. **模拟验证 bias 的方法论**：通过中性模拟（随机序列 + 随机突变）建立假阳性率基线，再模拟不同 bias 强度（移除低位点）观察假阳性率变化。**迁移到本课题**：评估任何新的 TF–DNA 结合预测模型时，可先在中性模拟数据上验证统计推断的校准性（calibration），再应用于真实数据。

3. **三种 bias 校正策略**：
   - 方法 1（简单倍数估计）：M = 2×正 deltaSVM 数，适用于 bias 机制简单的情形。
   - 方法 2（模拟回归）：利用模拟数据建立 bias 强度与可观测量的关系，外推真实数据的 bias 程度。
   - 方法 3（全基因组潜在位点）：以所有可能的功能位点数为总检验数，最保守但可能过度校正。
   **迁移到本课题**：在评估 TF–DNA 结合预测模型的进化推断时，可类似地考虑「模型预测的高置信位点」与「实验验证位点」之间的偏差。

4. **「回归到均值」的类比**：高亲和力 TFBS 的 deltaSVM 变化天然右偏，即使中性进化也易被误判为正选择。**迁移到本课题**：在解释 TF–DNA 结合预测模型的输出时，需注意「高结合分数」位点的进化变化可能受天花板效应（ceiling effect）影响，不能直接解读为选择信号。

5. **多方法交叉验证的必要性**：作者强调应结合多种方法（系统发育采样、MK 检验、实验验证）来确认正选择信号。**迁移到本课题**：AI 预测的 TF–DNA 结合变化应结合群体遗传学检验（如选择性清除扫描）和实验验证（如报告基因分析）来确认。

## 15 与已有知识连接

- **Liu & Robinson-Rechavi (2020)**：本文直接挑战其结论。该文首次将 gkm-SVM/deltaSVM 应用于正选择检测，报告了人类 TFBS 的广泛正选择信号。本文通过 ascertainment bias 校正后，这些信号基本消失。**连接**：本课题读者应谨慎引用 Liu & Robinson-Rechavi 的正选择结论，或至少注明本文的校正结果。
- **Ghandi et al. (2014); Lee et al. (2015)**：gkm-SVM 方法的原始文献。本文不质疑 gkm-SVM 的预测能力，而是质疑其下游统计推断。**连接**：gkm-SVM 作为 TF–DNA 结合预测工具仍可用于其他目的（如变异效应预测），但进化推断需额外校正。
- **Prabhakar et al. (2006); Gittelman et al. (2015)**：早期基于序列保守性和生化实验的正选择检测方法。本文的方法论批评同样适用于这些方法中「仅分析已知功能位点」的做法。
- **Benjamini & Hochberg (1995)**：多重检验校正的标准方法。本文展示了校正的 M 值选择对结论的极端敏感性。
- **Ohno's hypothesis 检验（He et al. 2011; Lin et al. 2012）**：作者在 Discussion 中类比了 X 染色体剂量补偿检验中的类似 ascertainment bias，说明该问题在基因组进化分析中的普遍性。
- **候选方向（未验证）**：本文的 bias 校正框架可推广到其他「实验鉴定的功能元件」的进化分析，如增强子、启动子、eQTL、GWAS 位点等。**连接**：本课题若涉及这些元件的 TF–DNA 结合分析，可参考本文的校正策略。

## 16 研究想法

**Agent 生成的研究候选**：

1. **名称**：Ascertainment-bias-aware TF–DNA binding prediction framework
   - **来源局限/观察**：本文证明 gkm-SVM 的 deltaSVM 正选择检测有 bias，但未提供替代预测框架。现有 TF–DNA 结合预测模型（如 DeepBind、DeepSEA）均以 ChIP-seq 数据训练，天然包含 ascertainment bias。
   - **核心假设**：在训练 TF–DNA 结合预测模型时，显式建模 ChIP-seq 检测阈值（截断）可提高模型对低亲和力位点的预测准确性，并改善下游进化推断。
   - **初步方法**：使用 Tobit 回归或截断高斯过程替代标准分类/回归损失；在训练目标中加入「检测概率」项；使用 SELEX/MITOMI 等无偏体外数据作为验证集。
   - **验证方式**：在模拟数据上比较标准模型与 bias-aware 模型的校准性；在真实 TFBS 数据上比较正选择检测的假阳性率。
   - **创新状态**：unverified（需文献调研确认是否已有类似框架）。

2. **名称**：Phylogenetic ascertainment-bias correction for regulatory element evolution
   - **来源局限/观察**：本文方法 3 以全基因组潜在位点数为 M，但未考虑系统发育关系。不同谱系的 TFBS 丢失/获得速率不同，可能影响 bias 程度。
   - **核心假设**：将系统发育信息纳入 ascertainment bias 校正，可更准确估计正选择位点比例。
   - **初步方法**：构建系统发育隐马尔可夫模型（phyloHMM），将「TFBS 可检测性」作为隐状态；在分支上同时估计替换速率和检测概率。
   - **验证方式**：模拟不同系统发育场景下的 bias 校正效果；应用于多物种 ChIP-seq 数据（如 ENCODE 跨物种数据）。
   - **创新状态**：unverified。

3. **名称**：Benchmarking TF–DNA binding predictors under ascertainment bias
   - **来源局限/观察**：本文仅测试了 gkm-SVM 一种预测器。深度学习方法（如 CNN、Transformer）的 bias 特性可能不同。
   - **核心假设**：不同架构的 TF–DNA 结合预测器对 ascertainment bias 的敏感性不同，某些架构可能天然更鲁棒。
   - **初步方法**：在本文的模拟框架下，比较 gkm-SVM、DeepBind、DeepSEA、BPNet 等模型的假阳性率；分析模型输出的校准曲线（calibration curve）。
   - **验证方式**：模拟数据 + 真实 ChIP-seq 数据（如 ENCODE 的 CEBPA、HNF4A、CTCF 数据）。
   - **创新状态**：unverified。

4. **名称**：Experimental validation of predicted positive-selection TFBSs
   - **来源局限/观察**：本文校正后仍有少量 CEBPA 位点显示弱正选择信号（adjusted P < 0.05），但作者未进行实验验证。
   - **核心假设**：这些「幸存」位点中，至少一部分是真实的正选择靶点。
   - **初步方法**：选择校正后仍显著的 CEBPA 位点，使用报告基因分析（luciferase assay）或 CRISPR 编辑比较祖先/衍生等位基因的转录活性差异；结合群体遗传学数据（如 1000 Genomes）检测选择性清除信号。
   - **验证方式**：实验数据 + 群体遗传学检验。
   - **创新状态**：unverified。

5. **名称**：Transfer learning for cross-species TF–DNA binding prediction without ascertainment bias
   - **来源局限/观察**：本文指出多物种数据（如小鼠、果蝇）的 bias 程度不同。跨物种迁移学习可能放大或缩小 bias。
   - **核心假设**：使用无偏体外数据（如 SELEX）作为源域，迁移到 ChIP-seq 目标域，可减少 ascertainment bias 的传播。
   - **初步方法**：域适应（domain adaptation）框架，源域为 SELEX 数据，目标域为 ChIP-seq 数据；在目标域上评估正选择检测的假阳性率。
   - **验证方式**：模拟 + 真实数据（如人类、小鼠的同一 TF 的 ChIP-seq 和 SELEX 数据）。
   - **创新状态**：unverified。