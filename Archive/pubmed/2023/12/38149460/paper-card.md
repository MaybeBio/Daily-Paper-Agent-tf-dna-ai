## 01 基本信息

- **标题**：Ascertainment Bias in the Genomic Test of Positive Selection on Regulatory Sequences
- **作者与单位**：Jiang, Daohan; Zhang, Jianzhi（美国密歇根大学，Department of Ecology and Evolutionary Biology）
- **期刊/预印本平台**：Molecular Biology and Evolution
- **年份**：2023-12-27（在线发表）
- **论文类型**：方法学批评/再分析（Methodological critique & reanalysis）
- **领域**：进化基因组学；调控序列正选择检测；TF–DNA 结合亲和力预测
- **关键词**：ascertainment bias, positive selection, transcription factor binding sites, deltaSVM, machine learning, regulatory sequences
- **DOI/arXiv 号**：10.1093/molbev/msad284
- **代码**：https://github.com/RexJiangEvoBio/TFBS
- **数据**：https://github.com/ljljolinq1010/A-robust-method-for-detecting-positive-selection-on-regulatory-sequences（原始数据来自 Liu & Robinson-Rechavi 2020）
- **阅读日期**：未提供
- **在「蛋白质-DNA互作 × AI/物理模拟」方向中的位置**：本文不提出新预测模型，而是对基于机器学习（gkm-SVM）预测 TF 结合亲和力并用于正选择检测的已有方法进行统计批评。核心贡献在于揭示"ascertainment bias"（确定偏倚）如何使基于 ChIP-seq 鉴定 TFBS 的正选择检验产生假阳性，并提出两种校正方法。对 TF–DNA 互作 × AI 方向的关键启示：任何基于实验鉴定（如 ChIP-seq）的 TFBS 数据集，在用于进化推断时都需考虑数据采集过程本身引入的偏倚。

## 02 一句话总结

本文通过理论推导、计算机模拟和人类 3 个 TF（CEBPA、HNF4A、CTCF）的 ChIP-seq 数据再分析，证明基于 gkm-SVM 预测 deltaSVM 的正选择检验因"ascertainment bias"（仅纳入高结合亲和力的已知 TFBS）而系统性高估正选择信号，提出两种校正方法后，先前报道的绝大多数正选择信号消失。

## 03 研究问题

- **具体问题**：Liu & Robinson-Rechavi (2020) 提出的基于 deltaSVM 的 TFBS 正选择检验，其 P 值计算是否因数据集的 ascertainment bias 而产生系统性偏差？
- **为什么重要**：cis-调控序列的适应性进化是进化生物学核心问题。若检测方法存在系统性假阳性，将导致对调控进化中正选择普遍性的错误估计，影响对基因表达进化机制的理解。
- **现有方法为何不足**：现有检验假设"已知 TFBS 数据集"是中性进化下的随机样本，但实际上这些 TFBS 是通过 ChIP-seq 在焦点物种中鉴定出来的，其纳入标准（可检测的结合）与结合亲和力正相关，导致高亲和力（高 deltaSVM）的位点被系统性富集。
- **精确的 "Can ... ?" 问题**：Can the ascertainment bias inherent in ChIP-seq-based TFBS identification inflate the false positive rate of the deltaSVM-based positive selection test, and can this bias be corrected?

## 04 背景与发展脉络

*注：以下脉络基于本文框架及文中引用的文献，经外部核验的部分已标注。*

1. **阶段一：cis-调控进化重要性确立（1975-2008）**：King & Wilson (1975)、Wray (2007)、Carroll (2008) 等提出基因表达调控变化是表型适应的重要来源。局限：缺乏直接检验调控序列正选择的方法。
2. **阶段二：基于比较基因组学的调控序列正选择检验（2005-2015）**：如 Andolfatto (2005) 用多态性-分歧度比较（类似 McDonald-Kreitman 框架）检验调控序列选择。局限：统计功效低，因调控序列功能位点少；依赖中性参考（同义位点或内含子），而突变率差异和近中性进化使解释复杂化。
3. **阶段三：基于机器学习预测 TF 结合亲和力的正选择检验（2020）**：Liu & Robinson-Rechavi (2020) 训练 gkm-SVM 预测任意 DNA 序列的 TF 结合亲和力（deltaSVM），对每个已知 TFBS 生成中性突变邻居的 deltaSVM 零分布，检验观察到的 deltaSVM 是否显著偏高。优点：不依赖中性参考序列，直接检验结合亲和力的进化方向。局限（本文指出）：**ascertainment bias**——已知 TFBS 来自 ChIP-seq 鉴定，其纳入标准与结合亲和力相关，导致零分布和观察值比较的基准被扭曲。
4. **阶段四（本文位置）**：指出阶段三方法的统计缺陷，提出校正方法，并重新评估人类 TFBS 正选择证据。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| Ascertainment bias（确定偏倚） | 已知 TFBS 数据集中，高 deltaSVM 的位点被系统性富集 | ChIP-seq 只能鉴定出结合足够强的位点；在无正选择的中性进化下，高亲和力位点更可能被纳入数据集，导致观察到的 deltaSVM 分布偏向正值 | Results 节 "Interpretation of P-values" 的数学推导：P′ = Prob(Δ>Δobs\|I) < P；Fig. 1 示意 |
| 假阳性率膨胀 | 中性进化下，正选择检验的假阳性率显著高于名义水平（如 1%） | 因 P 值被系统性低估（P′ < P），更多中性位点被误判为正选择 | Results 节 "False Positive Rates"：模拟显示去除 10%-90% 低分 TFBS 后，假阳性率随去除比例增加而升高（Table 1） |
| 零分布基准扭曲 | 零分布基于祖先序列的突变邻居，但观察值（已知 TFBS）本身是条件样本 | 检验的隐含假设是"已知 TFBS 是中性进化的随机结果"，但实际是"已知 TFBS 是 ChIP-seq 可检测的结果" | Results 节 "Interpretation of P-values" 的 P′ 推导 |
| 多重检验校正不足 | 原始研究未考虑缺失 TFBS 的总数 | 正选择检验的多次检验校正应基于所有潜在检验数（含未检测到的 TFBS），而非仅已知 TFBS 数 | Results 节 "Most Positive Selection Signals Disappear"：方法 1 和 2 分别估计缺失 TFBS 数 |

## 06 核心思想

1. **表面方法**：对 Liu & Robinson-Rechavi (2020) 的 deltaSVM 正选择检验进行统计批评，提出两种校正方法（方法 1：以 2 倍正 deltaSVM 数作为总检验数；方法 2：以全基因组潜在 TFBS 数作为总检验数），并重新计算人类 3 个 TF 的调整后 P 值。

2. **核心洞察**：**数据集的纳入标准（ascertainment）本身就是一种选择**。当检验"已知 TFBS 的结合亲和力是否在进化中升高"时，如果这些 TFBS 是因为结合亲和力足够高才被 ChIP-seq 检测到，那么即使没有正选择，观察到的 deltaSVM 也会偏向正值。这类似于 GWAS 中仅分析显著 SNP 会高估效应量（winner's curse）。数学上，P 值应条件于"位点被纳入数据集"这一事件（P′），而非无条件概率（P），且 P′ < P。

3. **可能的普适教训 [Analysis]**：任何基于实验筛选（如 ChIP-seq、ATAC-seq、体外结合实验）获得的"功能元件"数据集，在用于进化推断（正选择、保守性、功能富集）时，都必须显式建模数据采集过程的偏倚。机器学习预测的"分数"（如 deltaSVM）不能替代对数据生成过程的统计建模。这一教训可迁移到 TF–DNA 互作研究中所有基于实验鉴定的数据集。

## 07 方法总览

- **输入**：
  - Liu & Robinson-Rechavi (2020) 提供的 3 个人类 TF（CEBPA、HNF4A、CTCF）的 ChIP-seq 鉴定 TFBS 及其 deltaSVM 值（来自 GitHub 仓库）
  - 人类基因组大小估计（L = 6×10⁹ 核苷酸，考虑双链）
  - TFBS 平均长度（CEBPA: 269 bp; HNF4A: 340 bp; CTCF: 537 bp）
  - ChIP-seq 鉴定的 TFBS 总数（CEBPA: 16,212; HNF4A: 27,782; CTCF: 118,970）
  - 用于正选择检验的 TFBS 数（即至少有 2 个替换的位点，Table 2 第一行）

- **输出**：校正后的调整 P 值（Benjamini-Hochberg 方法），以及正选择信号的重新评估

- **模块**：
  1. **理论推导模块**：证明 P′ < P（条件概率 vs 无条件概率）
  2. **计算机模拟模块**：生成 50,000 个随机 10-mer 祖先序列，引入 2 个随机替换，模拟不同 ascertainment bias 程度（去除 10%-90% 最低 deltaSVM 的位点），计算假阳性率
  3. **再分析模块**：对 3 个 TF 的 ChIP-seq 数据，用 3 种方法（方法 0：不校正；方法 1：2×正 deltaSVM 数；方法 2：全基因组潜在位点数）计算调整 P 值
  4. **稳健性检验模块**：对 ChIP-seq 检测的 TFBS 序列进行核苷酸随机重排（shuffling），检验 deltaSVM 总和分布是否与真实序列有差异

- **训练**：不涉及（本文无模型训练，使用已有 gkm-SVM 权重）

- **反馈回路**：不适用

- **假设**：
  - 中性进化下，deltaSVM 的零分布可通过祖先序列的随机突变邻居近似
  - ChIP-seq 检测概率与结合亲和力正相关
  - 方法 2 中，全基因组所有潜在位点均可作为检验总数（保守估计）

- **文字流程**：
  1. 从 Liu & Robinson-Rechavi 的 GitHub 获取 3 个 TF 的 deltaSVM 数据和 TFBS 列表
  2. 理论推导：证明当数据集纳入与 deltaSVM 相关时，P 值被低估
  3. 计算机模拟：生成中性进化数据，模拟不同 ascertainment bias 程度，量化假阳性率
  4. 对真实数据应用 3 种多重检验校正方法，比较正选择信号的数量
  5. 用 shuffling 实验验证 deltaSVM 总和作为结合亲和力指标的局限性

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 理论推导（P′ vs P） | 证明 ascertainment bias 导致 P 值系统性低估 | 建立 bias 存在的数学基础 | 输入：事件 I（位点被纳入数据集）与 Δ>Δobs 的条件概率关系；输出：P′ < P 的不等式 | Results 节 "Interpretation of P-values" 的推导 | 移除后 bias 的存在仅为猜测，缺乏理论依据 |
| 计算机模拟 | 量化不同 bias 程度下的假阳性率 | 验证理论预测，展示 bias 的实际影响 | 输入：50,000 个随机 10-mer，2 个随机替换，去除 10%-90% 低 deltaSVM 位点；输出：各 bias 程度下的假阳性率 | Table 1：假阳性率随去除比例增加而升高（如 CEBPA 去除 90% 时假阳性率达 11 倍） | 移除后无法证明 bias 的实际影响大小 |
| 多重检验校正（方法 0/1/2） | 重新计算调整 P 值 | 校正 ascertainment bias 和缺失 TFBS 的影响 | 输入：原始 P 值、TFBS 数、估计的缺失 TFBS 数；输出：调整 P 值 | Table 2：方法 1 和 2 下，CEBPA 正选择位点数从 109（方法 0）降至 87 和 0；HNF4A 和 CTCF 均为 0 | 移除后无法评估 bias 对真实数据结论的影响 |
| Shuffling 检验 | 验证 deltaSVM 总和作为结合亲和力指标的可靠性 | 评估 gkm-SVM 预测长序列结合亲和力的有效性 | 输入：真实 TFBS 序列及其 shuffling 版本；输出：deltaSVM 总和分布比较 | Supplementary Fig. S1：shuffled 与未 shuffled 序列的 deltaSVM 总和分布高度重叠 | 移除后无法评估 deltaSVM 对长序列的预测效度 |

## 09 关键公式符号

1. **P 值定义**（Liu & Robinson-Rechavi 的检验）：
   P = Prob(Δ > Δobs)
   - Δ：中性进化下 deltaSVM 的变化量（随机变量）
   - Δobs：观察到的 deltaSVM 变化量

2. **条件 P 值**（本文核心）：
   P′ = Prob(Δ > Δobs | I) = Prob(Δ > Δobs ∩ I) / Prob(I)
   - I：位点被纳入数据集的事件（如 ChIP-seq 可检测）
   - 关键结论：P′ < P，因为 Prob(Δ > Δobs ∩ I) < Prob(Δ > Δobs) × Prob(I)（事件 I 与 Δ > Δobs 负相关）

3. **方法 1 的调整 P 值**（Benjamini-Hochberg）：
   Padjust = min{1, M·Pᵢ/i}
   - M：总检验数（方法 1 中 M = 2 × 正 deltaSVM 数）
   - Pᵢ：第 i 小的原始 P 值
   - i：秩次（并列 P 值取最大秩）

4. **方法 2 的调整 P 值**：
   Padjust = min{1, M·Pᵢ/i}，其中 M = P(n≥2)·L/l
   - L：基因组大小（6×10⁹ 核苷酸，考虑双链）
   - l：TFBS 平均长度（CEBPA: 269; HNF4A: 340; CTCF: 537）
   - P(n≥2)：至少有 2 个替换的概率

5. **模拟中的 deltaSVM 计算**：
   deltaSVM = Σ(所有 10-mer 的 SVM 权重差)，其中 10-mer 权重来自 gkm-SVM 训练

## 10 实验设计与证据链

**数据集/群体**：
- 模拟数据：50,000 个随机 10-mer 序列（每个位点等概率 4 种核苷酸），每个序列引入 2 个随机替换
- 真实数据：Liu & Robinson-Rechavi (2020) 的人类 ChIP-seq 鉴定的 CEBPA、HNF4A、CTCF 结合位点（CEBPA: 16,212; HNF4A: 27,782; CTCF: 118,970）

**指标**：假阳性率（模拟）、正选择位点数量（真实数据，P < 0.01 或 0.05）

**基线**：无 ascertainment bias 的模拟数据（不删除任何位点）

**预算**：不适用（无算力密集型计算）

**骨干/仪器**：不适用

**oracle 输入**：模拟数据中已知无正选择（所有替换为随机）

**评测协议**：对每个模拟数据集，计算 P < 0.01 的位点比例，与名义水平 1% 比较

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 模拟不同 bias 程度 | Ascertainment bias 增加假阳性率 | 去除 0%、10%-90% 最低 deltaSVM 位点，比较假阳性率 | 假阳性率随去除比例增加而升高；去除 90% 时达 11 倍（CEBPA） | Ascertainment bias 确实导致假阳性率膨胀 | 模拟假设（随机 10-mer、无突变偏好）可能简化了真实进化过程 | Table 1 |
| 真实数据再分析（方法 0 vs 1 vs 2） | 校正后正选择信号减少或消失 | 3 种方法计算调整 P 值，比较 P < 0.05 的位点数 | CEBPA: 109→87→0；HNF4A: 0→0→0；CTCF: 161→0→0 | 原始报告的正选择信号大部分是 ascertainment bias 的假象 | 方法 1 和 2 的 M 估计有不确定性；CEBPA 在方法 1 下仍有 87 个位点 | Table 2 |
| Shuffling 检验 | deltaSVM 总和不能可靠反映长序列结合亲和力 | 真实 TFBS 序列 vs 核苷酸重排序列的 deltaSVM 总和分布 | 两分布高度重叠 | 用 deltaSVM 总和作为长序列结合亲和力指标存在局限 | 未直接检验 deltaSVM 总和与实验结合亲和力的相关性 | Supplementary Fig. S1 |

## 11 结论正确解读

- **任务范围**：本文仅针对 Liu & Robinson-Rechavi (2020) 的特定检验框架（基于 gkm-SVM deltaSVM 的单侧检验），不否定所有基于机器学习的 TFBS 正选择检测方法。
- **oracle/真值输入**：模拟数据中所有替换为随机引入，无正选择，因此所有阳性结果均为假阳性。
- **端到端状态**：本文是"再分析"而非"端到端"新方法开发。校正方法（方法 1/2）是概念性框架，未提供完整软件工具。
- **算力成本**：极低（模拟和再分析均轻量）。
- **历史数据依赖**：依赖 Liu & Robinson-Rechavi (2020) 的 deltaSVM 输出和 ChIP-seq 位点列表；这些数据本身可能包含其他偏倚（如 ChIP-seq 抗体特异性、峰 calling 阈值）。
- **模型依赖**：gkm-SVM 的预测准确性直接影响 deltaSVM 的可靠性；本文未独立验证 gkm-SVM 的准确性。
- **最难情形**：当 TFBS 长度较长（如 CTCF 的 537 bp）时，deltaSVM 总和作为结合亲和力指标的效度最差（shuffling 检验显示分布重叠）。
- **群体/领域边界**：结论仅适用于人类（及类似哺乳动物）的 ChIP-seq 鉴定 TFBS；对体外结合实验（如 SELEX、HT-SELEX）或细菌/酵母体系可能不直接适用。
- **不确定性**：方法 1 和 2 对缺失 TFBS 数的估计是近似的；真实 ascertainment bias 程度未知，因此校正可能不足或过度。
- **有边界的复述**：在 Liu & Robinson-Rechavi (2020) 的检验框架下，由于 ChIP-seq 鉴定 TFBS 的 ascertainment bias，人类 CEBPA、HNF4A、CTCF 结合位点的正选择信号大部分（若非全部）可归因于假阳性；校正后仅 CEBPA 在宽松标准下可能保留少量信号。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 模拟简化 | 模拟使用随机 10-mer 和 2 个随机替换，未考虑突变偏好、选择、连锁等真实进化因素 | 未明确提及 | Results 节 "False Positive Rates" |
| 方法 1 估计不完整 | 方法 1 以 2×正 deltaSVM 数估计总检验数，但未恢复低亲和力且在祖先和焦点物种中均不可检测的位点（n4） | 未明确提及 | Discussion 节 |
| 方法 2 的假设 | 方法 2 假设所有基因组区域均可成为 TFBS，可能过度校正 | 若可建模不同区域成为 TFBS 的异质性，方法 2 可提供更准确校正 | Discussion 节 |
| deltaSVM 对长序列的局限 | deltaSVM 总和不能准确反映长 DNA 片段的整体结合亲和力 | 未明确提及 | Discussion 节、Supplementary Fig. S1 |
| 真实 bias 程度未知 | 无法精确估计 ChIP-seq 数据中 ascertainment bias 的实际强度 | 未明确提及 | Discussion 节 |

**作者提及的相关约束（非正式局限）**：
- 原始研究（Liu & Robinson-Rechavi 2020）的验证测试（如 McDonald-Kreitman 式比较）不足以排除 ascertainment bias，因为负选择可能掩盖 bias 效应（Discussion 节）。
- 小鼠和果蝇数据集的 ascertainment bias 较轻，但并非完全不存在（Discussion 节）。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 模拟仅使用 10-mer 序列 | 真实 TFBS 长度远大于 10 bp（本文数据中平均 269-537 bp），10-mer 模拟可能低估或高估 bias 效应 | 若长度影响 bias 强度，模拟结论可能不适用于真实数据 | 使用真实 TFBS 长度分布进行模拟 | Methods 节 "Analysis of Simulated TFBSs" |
| 方法 1 的 M=2×正 deltaSVM 数假设对称性 | 中性进化下 deltaSVM 正负分布可能不对称（受突变偏好、GC 含量等影响），2 倍估计可能不准确 | M 的准确性直接影响调整 P 值的可靠性 | 用真实基因组序列模拟中性进化，检验 deltaSVM 分布对称性 | Results 节 "Methods for Mitigating" |
| 未独立验证 gkm-SVM 预测准确性 | 若 gkm-SVM 本身有系统误差（如对高亲和力序列预测偏高），bias 可能部分来自模型而非数据采集 | 区分"数据采集 bias"和"模型 bias"对设计改进方案至关重要 | 用独立实验数据（如 HT-SELEX 测量的结合亲和力）验证 gkm-SVM 预测 | 未提供 |
| 再分析仅覆盖 3 个 TF | 不同 TF 的 ChIP-seq 质量、结合 motif 长度、基因组分布差异大，3 个 TF 的结论可能不具普适性 | 若 bias 程度因 TF 而异，需要更广泛的验证 | 扩展到更多 TF 和细胞类型 | Table 2 |
| 未讨论替代检验框架 | 作者仅提出校正方法，未讨论是否可能有完全不同的检验设计（如基于多态性-分歧度比率的框架）能天然避免 ascertainment bias | 校正可能只是权宜之计，根本解决方案可能需要重新设计检验 | 比较不同检验框架在相同数据上的表现 | Discussion 节 |
| Shuffling 检验的解读 | shuffled 序列保留了核苷酸组成但破坏了 motif 结构，deltaSVM 总和分布重叠可能反映 gkm-SVM 对组成敏感而非对 motif 敏感 | 若 gkm-SVM 主要捕捉组成效应，deltaSVM 可能不适合用于正选择检验 | 用包含已知 motif 的合成序列验证 gkm-SVM 的敏感性 | Supplementary Fig. S1 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **Ascertainment bias 的数学框架**：当检验统计量（如 deltaSVM）与样本纳入标准（如 ChIP-seq 可检测性）相关时，P 值必须条件于纳入事件。形式化为 P′ = Prob(Δ > Δobs | I) < P。**可迁移到 TF–DNA 互作**：任何基于实验鉴定的 TFBS 数据集（ChIP-seq、HT-SELEX、PBMs）在用于训练或评估 AI 模型时，训练集的"可检测性"偏倚会系统性影响模型学习到的结合偏好。

2. **"Winner's curse" 在基因组检测中的普遍性**：与 GWAS 中仅分析显著 SNP 会高估效应量类似，仅分析"可检测"的 TFBS 会高估结合亲和力的进化变化。**可迁移**：在训练 TF–DNA 结合预测模型时，若训练数据仅包含高亲和力结合位点，模型对低亲和力位点的预测将不可靠。

3. **多重检验校正的"缺失样本"问题**：校正应基于所有潜在检验数（含未检测到的），而非仅观察到的检验数。**可迁移**：在基因组范围扫描 TF 结合位点或预测调控变异时，需考虑未检测位点的数量。

4. **DeltaSVM 对长序列的局限**：deltaSVM 总和（所有 10-mer 权重差之和）不能准确反映长 DNA 片段的整体结合亲和力。**可迁移**：对 TF–DNA 互作的 AI 建模，序列长度超过模型窗口时，简单加和/平均策略可能失效，需考虑位置效应、协同结合等。

5. **模拟验证 bias 的方法论**：通过生成已知无选择的中性数据，模拟不同 bias 程度，量化假阳性率。**可迁移**：在开发新的 TF–DNA 互作预测或正选择检测方法时，应首先在模拟数据上验证方法的假阳性率受数据采集偏倚的影响程度。

6. **"Shuffling" 作为对照**：通过核苷酸重排保留组成但破坏结构，检验模型是否捕捉组成而非 motif 信息。**可迁移**：评估 TF–DNA 结合预测模型时，shuffling 对照可帮助区分模型学到的是序列组成特征还是 motif 特征。

## 15 与已有知识连接

- **Liu & Robinson-Rechavi (2020)**：本文的直接批评对象。该文提出基于 gkm-SVM 的 deltaSVM 正选择检验，报告人类 TFBS 存在正选择。本文通过 ascertainment bias 校正，推翻其大部分结论。**连接**：在引用 Liu & Robinson-Rechavi 的正选择结论时，必须同时引用本文的批评。

- **Ghandi et al. (2014, 2016)**：gkm-SVM 方法的原始开发者。本文不质疑 gkm-SVM 本身，但指出其输出（deltaSVM）在特定检验框架中的误用。**连接**：gkm-SVM 仍可用于 TF 结合预测，但用于进化推断时需注意 bias。

- **McDonald-Kreitman 检验 (1991)**：本文讨论 Liu & Robinson-Rechavi 的验证测试时提到。MK 框架比较种内多态性与种间分歧度，但本文指出其不适用于调控序列的亲和力变化检验。**连接**：MK 检验的局限性在调控序列中更为突出。

- **Andolfatto (2005)**：早期调控序列正选择检测的代表性工作。本文的 bias 批评可能同样适用于基于多态性-分歧度比较的调控序列检验。**连接**：需重新审视早期调控序列正选择证据。

- **He et al. (2011), Lin et al. (2012)**：本文引用的 X 染色体剂量补偿检验中 ascertainment bias 的例子。**连接**：ascertainment bias 是基因组进化分析中的普遍问题，本文提供了一个新的实例。

- **Shrikumar et al. (2019)**：可解释性方法（如 DeepSHAP）用于解释 gkm-SVM 等模型。本文指出 deltaSVM 的解读方法不影响检验的非参数性质。**连接**：可解释性方法的选择对基于模型分数的统计检验影响有限。

- **TF–DNA 互作 × AI 方向**：本文的 bias 批评对基于深度学习（如 DeepBind、DeepSEA）预测 TF 结合并用于进化推断的工作具有警示意义。**连接**：任何使用实验鉴定的 TFBS 训练模型并用于正选择检测的工作，都应考虑 ascertainment bias。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：Ascertainment-bias-aware 的 TF–DNA 结合预测模型训练框架
   - **来源局限/观察**：本文证明 ChIP-seq 鉴定的 TFBS 数据集存在系统性高亲和力偏倚；现有深度学习模型（如 DeepBind、DeepSEA）直接使用这些数据训练，可能学习到偏倚的分布而非真实的结合偏好。
   - **核心假设**：在训练 TF 结合预测模型时，显式建模"可检测性"（如 ChIP-seq 信号强度阈值）可减少偏倚，提高模型对低亲和力位点的预测准确性。
   - **初步方法**：在训练损失函数中加入"可检测性"项，或使用逆概率加权（inverse probability weighting）校正训练样本的纳入概率；使用 HT-SELEX 等体外数据作为无偏验证集。
   - **验证方式**：比较校正前后模型在独立体外数据（如 HT-SELEX、PBMs）上的预测准确性；模拟已知结合位点的进化场景，检验校正后模型的进化推断准确性。
   - **创新状态**：unverified

2. **候选名称**：基于正选择检验的 TFBS 数据集 bias 量化工具
   - **来源局限/观察**：本文的 bias 校正需要估计缺失 TFBS 数，但方法 1 和 2 均为粗略估计；不同 TF 的 bias 程度可能差异巨大。
   - **核心假设**：通过比较 ChIP-seq 检测位点与基因组随机位点的 deltaSVM 分布，可量化每个 TF 的 ascertainment bias 强度，并据此调整正选择检验的阈值。
   - **初步方法**：开发一个 R/Python 包，输入 ChIP-seq 位点、deltaSVM 权重和基因组序列，输出 bias 校正后的正选择检验结果；包含模拟模块用于估计假阳性率。
   - **验证方式**：在多个物种和 TF 上测试，与本文结果对比；用已知正选择位点（如实验验证的适应性突变）作为阳性对照。
   - **创新状态**：unverified

3. **候选名称**：TF 结合亲和力进化的多物种无偏检验
   - **来源局限/观察**：本文的 bias 源于单物种 ChIP-seq 鉴定；多物种比较（如跨物种 ChIP-seq 或保守位点分析）可能天然减少 bias，但现有方法未充分利用。
   - **核心假设**：使用多物种保守的 TFBS 位点（在多个物种中均可检测）进行正选择检验，可减少单物种 ascertainment bias，提高检验的特异性。
   - **初步方法**：整合多物种 ChIP-seq 数据，构建"多物种可检测"位点集；对每个位点计算各物种的 deltaSVM，检验跨物种的亲和力变化方向是否一致。
   - **验证方式**：模拟多物种进化场景，比较单物种与多物种检验的假阳性率和功效；应用于人类-黑猩猩-大猩猩-小鼠的 TFBS 数据。
   - **创新状态**：unverified

4. **候选名称**：深度学习结合亲和力预测器的 bias 校正迁移学习
   - **来源局限/观察**：本文指出 deltaSVM 对长序列的预测局限；深度学习模型（如 Enformer）可预测长序列的调控活性，但同样受训练数据 bias 影响。
   - **核心假设**：通过迁移学习，将体外高-throughput 结合数据（如 HT-SELEX）的知识迁移到 ChIP-seq 训练的模型，可同时减少 ascertainment bias 和长序列预测误差。
   - **初步方法**：使用 HT-SELEX 数据预训练模型，再用 ChIP-seq 数据微调；在微调时加入"可检测性"校正项。
   - **验证方式**：在独立测试集（如 STARR-seq、MPRA）上比较校正前后模型的预测准确性；检验校正后模型对已知适应性调控突变的预测能力。
   - **创新状态**：unverified

5. **候选名称**：调控序列正选择检验的贝叶斯分层框架
   - **来源局限/观察**：本文的校正方法基于频率学派 P 值调整，无法整合先验信息（如 TF 功能重要性、位点保守性）；贝叶斯方法可更灵活地建模 ascertainment bias。
   - **核心假设**：贝叶斯分层模型可同时估计每个位点的正选择概率和数据集 ascertainment bias 强度，提供比 P 值调整更准确的推断。
   - **初步方法**：构建分层贝叶斯模型，将 deltaSVM 观测值建模为"真实亲和力变化 + 检测偏倚"的函数；使用 MCMC 或变分推断估计后验。
   - **验证方式**：模拟数据验证模型的可识别性和准确性；应用于本文的人类 TFBS 数据，比较与频率学派方法的结果差异。
   - **创新状态**：unverified