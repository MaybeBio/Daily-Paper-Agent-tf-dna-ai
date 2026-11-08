## 01 基本信息
- **标题**: Unsupervised prioritization of gene-regulatory variants with isolation forests
- **作者与单位**: Schmidt AW; Rosendahl J; Laumen H; Ossowski S（单位未在摘要中提供，推测与德国图宾根大学相关，因致谢提及图宾根大学出版基金）
- **期刊/预印本平台**: bioRxiv
- **年份**: 2026（预印本日期 2026-11-03）
- **论文类型**: 预印本（方法学 + 应用研究）
- **领域**: 基因组学 / 基因调控变异优先级排序 / 无监督机器学习
- **关键词**: eQTL、GWAS、Enformer、isolation forest、基因调控变异、TFBS、无监督学习
- **DOI/arXiv 号**: 10.64898/2026.10.29.762447
- **代码**: https://github.com/pancinf/eQIF.git
- **数据**: 预计算评分（Zenodo, DOI = 10.5281/zenodo.23733502）；Enformer PC20 数据（Google Cloud Storage）；GTEx v8 fine-mapping；CAUSALdb2；CADD/LINSIGHT/DVAR/AVI/Seier 预计算评分
- **阅读日期**: 未提供
- **在课题方向中的位置**: 本文属于「TF–DNA 结合机制 × AI 方法」方向中的**调控变异效应预测**子方向。核心创新在于用无监督 isolation forest 整合 Enformer 的 5,313 维输出为单一评分，直接服务于 TF 结合位点（TFBS）内变异的优先级排序，与 TF–DNA 结合机制高度相关（TFBS footprint、motif 信息含量分析）。

## 02 一句话总结
本文提出 eQIF，一种基于 isolation forest 的无监督方法，将 Enformer 对每个常见 SNP 的 5,313 维 delta 预测压缩为单一基因调控评分，在 eQTL、GWAS-eQTL 和 MPRA 数据上优于 CADD、LINSIGHT、DVAR、AVI 和 Sei，且高评分变异富集于进化保守的 TFBS footprint 区域。

## 03 研究问题
- **具体问题**: 如何将 Enformer 产生的高维（5,313 维）基因调控预测整合为单一、可解释、可全基因组预计算的变异优先级评分？
- **为什么重要**: 大多数常见变异位于非编码区，eQTL 和 GWAS 共定位分析常留下多个候选变异，需要功能评分来缩小实验验证范围。现有工具要么是机制不可知的（CADD），要么是监督式且偏重编码区（AVI），要么缺乏远端调控信息（Sei 的 CNN 架构）。
- **现有方法不足**: 
  - CADD/AVI 是机制不可知或偏重全局有害性，对纯调控效应不敏感；
  - LINSIGHT/DVAR 依赖进化保守性，对 lineage-specific 调控元件不敏感；
  - Sei 的 CNN 架构不包含远端增强子-启动子相互作用；
  - Enformer 本身输出维度太高，不便于直接用于变异优先级排序。
- **精确研究问题（Can ... ?）**: Can an unsupervised isolation forest trained on Enformer PC20 features produce a single genome-wide score that outperforms existing tools in prioritizing eQTLs, gene-regulatory GWAS variants, and MPRA-validated regulatory variants?

## 04 背景与发展脉络
（标注：以下脉络为「经外部核验」——基于摘要中引用的文献和领域常识，但具体细节以本文框架为主）
1. **第一代：机制不可知整合评分**（CADD 2014、LINSIGHT 2018、DVAR 2019）——整合进化保守性、注释等特征，监督或半监督训练，但缺乏组织特异性调控信息。
2. **第二代：序列深度学习的调控预测**（DeepSEA 2015、Sei 2021）——CNN 直接学习 DNA 序列到染色质特征的映射，但 CNN 感受野有限，难以捕捉远端相互作用。
3. **第三代：长上下文序列模型**（Enformer 2021）——引入 transformer 架构，可建模 100kb 以上远端调控，但输出维度高（5,313 tracks），不便于直接排序。
4. **本文位置**: 在 Enformer 之上加一层无监督 isolation forest，将高维输出压缩为单一评分，同时保留远端调控信息。与 Sei 的 seqclass_max_absdiff 评分（CNN 版）形成直接对比。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| Enformer 输出维度高 | 每个变异产生 5,313 个 delta 评分，无法直接用于变异排序 | Enformer 预测多种细胞类型/组织的多种染色质特征 | Methods "Training an Enformer-PC-based isolation forest" 节 |
| 现有工具缺乏远端调控信息 | Sei 等 CNN 模型无法建模远端增强子-启动子相互作用 | CNN 感受野有限 | Introduction 末段 |
| 监督式方法存在训练偏差 | CADD/AVI 使用等位基因频率等作为训练信号，可能偏向编码区或全局有害性 | 监督训练需要标注数据，而调控变异的 gold standard 有限 | Discussion 中关于 AVI 的讨论 |
| 变异优先级排序后仍有多候选 | fine-mapping 后 credible set 常含多个变异 | LD 结构导致统计关联无法区分因果变异 | Introduction 第 1 段 |
| 编码区 eQTL 被忽视 | 多数工具聚焦非编码区，编码区调控变异缺乏专门评分 | 编码区变异通常被归为 missense 机制 | Results "eQTL-coding cohort" 分析 |

## 06 核心思想
1. **表面方法**: 用 isolation forest 对 20 个 Enformer PC 做无监督异常检测，将每个 SNP 映射为异常分数（anomaly score），分数越高表示该变异的 Enformer 预测模式越「异常」（即越可能具有调控效应）。
2. **核心洞察**: 大多数变异是中性/无调控效应的，因此它们在 Enformer PC 空间中形成高密度区域；真正有调控效应的变异是「稀有模式」，在 PC 空间中表现为可分离的异常点。Isolation forest 天然适合这种「稀有性 = 功能性」的假设，且无需任何标注数据。
3. **可能的普适教训 [Analysis]**: 对于高维深度模型输出，无监督异常检测可以作为一种「模型蒸馏」手段，将复杂预测压缩为可操作的单一评分，同时避免监督训练带来的标签偏差。这一思路可迁移到任何「高维预测 → 单维决策」的场景。

## 07 方法总览
- **输入**: 
  - 9,421,183 个常见 SNP（gnomAD v3.1.2 非芬兰欧洲人群，AF ≥ 0.5%，PASS 质控，排除 HLA-MHC 区域）
  - 每个 SNP 的 20 个 Enformer PC 值（来自 1000 Genomes 预计算数据，hg19 坐标经 liftOver 转 hg38）
- **输出**: 每个 SNP 的 eQIF 异常分数（连续值，越高越可能具有调控效应）
- **模块**:
  1. 数据预处理：坐标转换、等位基因/链校正、与 gnomAD 变异取交集
  2. Isolation forest 训练（无监督，无标签）
  3. 超参数优化：5 次重复随机 80:20 训练-测试划分，基于 eQTL 分类 AU-ROC 选择最优参数（sample_size ∈ {1,000, 10,000}；ndim ∈ {1, 2}；特征权重：等权 vs 线性递减）
  4. 验证：三个独立 cohort（eQTL、GWAS-eQTL、MPRA）
- **训练**: 无监督，无标签；超参数选择使用 eQTL cohort 作为验证集（注意：这引入了轻微的监督信号，但仅用于参数选择，非模型训练）
- **反馈回路**: 无（静态预计算）
- **文字流程**: 下载 Enformer PC20 → liftOver 到 hg38 → 与 gnomAD 欧洲 SNP 取交集 → 用 isotree 包训练 isolation forest → 对每个 SNP 计算异常分数 → 在三个验证 cohort 中评估 AU-ROC/AU-PRC → 与 CADD/LINSIGHT/DVAR/AVI/Sei 比较 → 生物学特征分析（保守性、TFBS 富集、motif 信息含量）

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Enformer PC20 特征 | 提供高维调控预测 | Enformer 是唯一能建模远端相互作用的开源模型 | 输入：SNP 及侧翼序列；输出：20 个 PC | 引用 Enformer 原始论文 | 预期影响：失去远端调控信息，性能可能降至 Sei 水平 [预期效应] |
| Isolation forest | 无监督异常检测 | 将 20 维 PC 压缩为单一异常分数 | 输入：20 维 PC 矩阵；输出：异常分数 | Results 图 1A-B | 移除后无替代评分机制 [预期效应] |
| 超参数优化 | 选择最优模型配置 | isolation forest 对 sample_size 和 ndim 敏感 | 输入：候选参数组合；输出：最优参数 | Methods "Training" 节；Suppl. Fig 1 | 次优参数可能导致 AU-ROC 下降（但作者称差异很小）[实测消融效应，Suppl. Fig 1] |
| 特征加权 | 按 PC 排名线性递减权重 | PC 解释方差递减，高序 PC 可能含噪声 | 输入：20 个 PC；输出：加权后的特征 | Methods "column_weights" 参数 | 等权模型性能略低 [实测消融效应，Suppl. Fig 1] |
| 验证 cohort 构建 | 评估泛化性能 | 单一 cohort 不足以证明普适性 | 输入：GTEx/CAUSALdb2/MPRA 数据；输出：三个 cohort | Results 图 1-2 | 移除任一 cohort 会降低结论强度 [预期效应] |

## 09 关键公式符号
本文为方法学论文，核心公式为 isolation forest 的异常分数定义（基于 isotree 包实现，作者未在摘要中给出具体公式）。以下为 isolation forest 的标准公式（基于 Liu et al. 2008，作者引用 [24]）：

- **路径长度**：$h(x)$ 表示样本 $x$ 在 isolation tree 中被隔离所需的边数
- **平均路径长度**：$c(n) = 2H(n-1) - \frac{2(n-1)}{n}$，其中 $H(i) = \ln(i) + \gamma$（欧拉常数），$n$ 为样本数
- **异常分数**：$s(x, n) = 2^{-\frac{E[h(x)]}{c(n)}}$，其中 $E[h(x)]$ 为样本 $x$ 在所有树中的平均路径长度
- **用途**：$s$ 越接近 1 表示越异常（越可能具有调控效应），$s$ 接近 0.5 表示正常样本

其他相关公式：
- **AU-ROC / AU-PRC**：标准分类指标，用于评估排序性能（作者用 precrec 包计算）
- **Spearman 相关系数**：$\rho = \frac{\text{cov}(R_X, R_Y)}{\sigma_{R_X} \sigma_{R_Y}}$，用于评估 eQIF 分数与 motif 信息含量的相关性（Results 图 4C-F）

## 10 实验设计与证据链
- **数据集**:
  - 训练/评分集：9,421,183 个常见欧洲 SNP（gnomAD v3.1.2 NFE）
  - eQTL cohort：GTEx v8 fine-mapping（CAVIAR posterior ≥ 0.95 为 case，≤ 0.01 为 control，匹配 AF 和 TSS 距离）
  - GWAS-eQTL cohort：CAUSALdb2 fine-mapping 结果 ∩ GTEx eQTL
  - MPRA cohort：Siraj et al. 2025（221,412 个 fine-mapped 变异 + 86,064 个对照）
  - 位点验证：SORT1（rs12740374）和 MX2（rs398206）
- **指标**: AU-ROC、AU-PRC、DeLong 检验（pairwise ROC 比较）、Spearman 相关
- **基线**: CADD v1.7、LINSIGHT、DVAR、AVI、Sei seqclass_max_absdiff
- **评测协议**: 5 次重复随机 80:20 划分用于超参数选择；最终模型在全量数据上训练并预计算

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|-------------|-------------------|------|
| eQTL 分类 | eQIF 优于现有工具 | eQIF vs CADD/LINSIGHT/DVAR/AVI/Sei | eQIF AU-ROC = 0.77，最高 | eQIF 在 eQTL 预测上最优 | 未报告 AU-PRC 排名（仅 AU-ROC 显著） | Results 图 1A-B |
| 编码区 eQTL | eQIF 在编码区也有效 | eQTL-coding cohort | eQIF AU-ROC = 0.68，AU-PRC = 0.2 | eQIF 对编码区调控变异有预测力 | 未与专门编码区工具比较 | Results 图 1C-D |
| GWAS-eQTL 分类 | eQIF 预测疾病相关调控变异 | GWAS-eQTL cohort | eQIF AU-ROC = 0.86，AU-PRC = 0.23 | eQIF 在疾病相关变异上表现最佳 | AU-PRC 与 AVI 持平 | Results 图 2A-B |
| MPRA 验证 | eQIF 预测体外功能变异 | MPRA cohort | eQIF AU-ROC = 0.67，AU-PRC = 0.27 | eQIF 在体外功能数据上有效 | 略低于 Sei（AU-ROC 0.68） | Suppl. Fig 3 |
| 位点验证 | eQIF 识别已知因果变异 | SORT1 和 MX2 位点 | rs12740374 和 rs398206 均排第 1 | eQIF 可优先排序已知因果变异 | 仅 2 个位点，样本量小 | Results 图 3 |
| 进化保守性 | eQIF 分数与保守性相关 | phyloP 三物种比较 | OR = 1.3-1.39 | eQIF 富集于保守位点 | 相关性不等于因果 | Results 图 4A |
| TFBS 富集 | eQIF 富集于 TFBS footprint | SCREEN + Vierstra footprint | 高 eQIF 分数富集于 footprint | eQIF 与 TF 结合相关 | 未做 TF 特异性分析 | Results 图 4B |
| motif 信息含量 | eQIF 分数与信息含量相关 | CTCF/ETS1 motif | ρ = 0.70/0.67 | eQIF 分数反映 motif 关键位点 | 仅 2 个 TF | Results 图 4C-F |

## 11 结论正确解读
- **任务范围**: eQIF 仅适用于常见 SNP（AF ≥ 0.5%）的调控效应预测，不适用于罕见变异、结构变异或插入缺失。
- **oracle/真值输入**: 验证 cohort 依赖 CAVIAR/SuSiE fine-mapping 概率作为「真值」代理，这些概率本身有误差；MPRA 数据来自体外实验，不能完全代表体内调控。
- **端到端状态**: eQIF 是预计算评分，不是端到端因果推断工具；它不能替代 fine-mapping，而是 fine-mapping 后的辅助排序工具。
- **算力成本**: isolation forest 训练和推理计算成本低（作者称「computationally fast」），但依赖 Enformer 预计算（需 GPU）。
- **历史数据依赖**: 训练基于 1000 Genomes 和 gnomAD 欧洲人群，对其他人群的适用性未验证。
- **模型依赖**: 完全依赖 Enformer 的 PC20 表示，若 Enformer 有系统性偏差，eQIF 会继承。
- **最难情形**: 编码区 eQTL（AU-ROC 降至 0.68）；MPRA 数据（被 Sei 超越）。
- **群体/领域边界**: 仅欧洲人群；仅 SNP；仅调控效应（不预测剪接、mRNA 稳定性等）。
- **不确定性**: 未报告置信区间；AU-PRC 普遍较低（0.13-0.3），说明绝对精度有限，适合排序而非分类。
- **有边界的复述**: eQIF 是一个针对欧洲人群常见 SNP 的、基于 Enformer PC20 的无监督调控效应评分，在 eQTL 和 GWAS-eQTL 排序上优于现有工具，在 MPRA 上接近但略逊于 Sei，且高评分变异富集于保守 TFBS footprint。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 仅覆盖常见变异 | 基于 1000 Genomes 和 gnomAD 欧洲人群，AF ≥ 0.5% | 未明确提及 | Limitations 节 |
| 依赖 Enformer 预计算 | 需要 GPU 密集型 Enformer 推理 | 未明确提及 | Limitations 节 |
| AVI 在 top 变异上表现相当 | AU-PRC 与 AVI 持平 | 可能通过整合 AlphaGenome 注释改进（但许可证禁止） | Limitations 节 |
| 无法覆盖罕见变异 | 当前版本仅限常见 SNP | 未明确提及 | Limitations 节 |
| MPRA 上被 Sei 超越 | AU-ROC 0.67 vs 0.68 | 推测 Enformer 的远端上下文在体外报告基因中不相关 | Discussion 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 超参数选择使用 eQTL cohort 作为验证集 | 引入了轻微的「泄漏」——模型超参数在测试集上优化，可能高估 eQTL 性能 | 影响 eQTL 结果的可信度 | 使用独立 cohort 或嵌套交叉验证重新评估 | Methods "Training" 节 |
| AU-PRC 普遍较低（0.13-0.3） | 绝对精度有限，可能只适合粗排序 | 实际应用中可能仍有大量假阳性 | 报告 top-k 精确率或设置实用阈值 | Results 图 1-2 |
| 仅 2 个位点验证 | SORT1 和 MX2 样本量太小，无法证明普适性 | 位点验证结论强度有限 | 扩展至更多已知因果变异位点 | Results 图 3 |
| 与 Sei 的比较可能不公平 | Sei 的 seqclass_max_absdiff 是单一 score，而 eQIF 使用 20 个 PC（信息量更大） | 需要控制信息量差异 | 用 Sei 的全部输出做 isolation forest 作为对照 | [Analysis] 基于方法描述 |
| 未报告运行时间 | 「computationally fast」缺乏量化 | 影响实际可用性评估 | 报告训练和推理时间 | Methods 节 |
| 未做人群泛化测试 | 仅欧洲人群，其他人群 LD 结构和等位基因频率不同 | 全球应用受限 | 在非欧洲人群 cohort 上验证 | [Analysis] 基于数据描述 |
| 未与最新深度学习方法（如 AlphaGenome）直接比较 | 仅提及 AVI，未比较 AlphaGenome 原始输出 | 无法判断 eQIF 是否优于直接使用 AlphaGenome | 用 AlphaGenome 原始输出做同样评测 | Limitations 节 |

## 14 学到什么
**Agent 提炼的知识候选**（面向 TF–DNA 结合机制 × AI/物理模拟课题）:

1. **无监督异常检测作为高维模型蒸馏器**: isolation forest 可将 Enformer 的 5,313 维输出压缩为单一评分，这一思路可直接迁移到任何高维深度学习模型（如 AlphaFold 的 pLDDT 多通道输出、MD 模拟的多维自由能特征）的决策压缩场景。
2. **「稀有性 = 功能性」假设**: 在 TF–DNA 结合机制中，功能性变异（改变 TF 结合）在序列空间中天然稀有，异常检测框架可能比监督学习更适合捕捉「未知的未知」。
3. **TFBS footprint 作为验证锚点**: 作者用 DNase footprint 和 motif 信息含量验证 eQIF 分数，这为 TF–DNA 结合机制研究提供了「预测分数 → 实验可验证」的闭环范式。
4. **motif 信息含量与分数相关性的检验方法**: 用 Spearman 相关检验预测分数与 position weight matrix 信息含量的关系，是评估「预测分数是否反映 TF 结合特异性」的简洁统计工具。
5. **编码区调控变异的独立分析**: 作者专门构建了编码区 eQTL cohort，提示在 TF–DNA 结合研究中不应忽视编码区内的调控元件（如 exonic enhancer）。
6. **多 cohort 验证设计**: eQTL（体内）、GWAS-eQTL（疾病相关）、MPRA（体外）三层次验证框架，可迁移到 TF 结合变异预测工具的评估设计。

## 15 与已有知识连接
- **Enformer (Avsec et al. 2021)**: 本文直接建立在 Enformer 的预计算输出上，是 Enformer 在变异优先级排序场景的应用延伸。
- **Sei (Chen et al. 2021)**: 本文的主要竞争对手，同为序列深度学习的调控变异评分，但基于 CNN 架构。本文在 eQTL 和 GWAS-eQTL 上超越 Sei，在 MPRA 上略逊。
- **CADD (Rentzsch et al. 2019) / LINSIGHT (Huang et al. 2018) / DVAR (Li et al. 2019)**: 传统变异优先级工具，本文在多个 cohort 上比较并超越。
- **AlphaGenome Variant Impact (AVI)**: 最新的大模型变异评分，本文在 AU-ROC 上超越但 AU-PRC 持平。
- **GTEx eQTL fine-mapping (CAVIAR)**: 验证数据的来源，与 TF–DNA 结合机制直接相关（eQTL 的因果变异常位于 TFBS）。
- **TFBS footprint (Vierstra et al. 2020)**: 本文用 DNase footprint 验证 eQIF 分数，这是 TF–DNA 结合机制的直接实验证据。
- **JASPAR motif 数据库**: 用于 TFBS 富集分析，是 TF–DNA 结合机制研究的标准资源。
- **候选方向 [Analysis]**: 本文的 isolation forest 框架可迁移到「基于 AlphaFold 结构预测的 TF–DNA 结合变异效应评分」或「基于 MD 模拟自由能变化的变异分类」，但需注意特征维度差异（结构特征 vs 序列特征）。

## 16 研究想法
**Agent 生成的研究候选**:

1. **候选名称**: TFBS-IF：基于结构感知特征的 TF–DNA 结合变异无监督优先级排序
   - **来源局限/观察**: eQIF 仅使用序列特征（Enformer PC），未利用 TF–DNA 三维结构信息；AlphaFold 和 MD 模拟可提供结合自由能变化等结构特征。
   - **核心假设**: 结合 Enformer 序列特征 + AlphaFold 结构特征 + MD 结合自由能变化的 isolation forest 能比单一特征源更准确识别功能性 TFBS 变异。
   - **初步方法**: 对已知 TF–DNA 复合物结构中的变异计算结构特征，与 Enformer PC 拼接后训练 isolation forest，在 GTEx eQTL 和 MPRA 数据上评估。
   - **验证方式**: 与 eQIF、Sei、AlphaFold 变异效应评分比较 AU-ROC/AU-PRC。
   - **创新状态**: unverified

2. **候选名称**: 无监督异常检测用于 TF 结合 motif 的「稀有模式」发现
   - **来源局限/观察**: eQIF 的「稀有性 = 功能性」假设可推广到 motif 层面——在已知 TF motif 中，功能性 SNP 可能位于信息含量最高的位置（作者已证明相关性）。
   - **核心假设**: 在 position weight matrix 的每个位置上，功能性变异的 Enformer 异常分数分布与中性变异显著不同，且差异大小与位置信息含量相关。
   - **初步方法**: 对 JASPAR 中所有 TF motif 的 SNP 计算 eQIF 分数，按位置信息含量分层，检验异常分数与信息含量的剂量-反应关系。
   - **验证方式**: 与已知致病 TFBS 变异数据库比较，评估能否作为「motif 位置功能权重」的先验。
   - **创新状态**: partially checked（作者已对 CTCF/ETS1 做了初步分析，但未系统化）

3. **候选名称**: 跨细胞类型的 TF 结合特异性异常检测
   - **来源局限/观察**: eQIF 使用 Enforcer 的 PC20 聚合了所有细胞类型，可能稀释 cell-type-specific TF 结合信号。
   - **核心假设**: 对特定细胞类型的 Enformer 原始输出（而非 PC）做 isolation forest，能更好捕捉该细胞类型中活跃 TF 的结合变异。
   - **初步方法**: 选择 GTEx 中 eQTL 数量最多的组织，用该组织的 Enformer 原始输出训练 isolation forest，与全局 eQIF 比较。
   - **验证方式**: 组织特异性 eQTL 分类 AU-ROC 提升幅度。
   - **创新状态**: unverified

4. **候选名称**: eQIF 分数作为 MD 模拟的起始点选择器
   - **来源局限/观察**: MD 模拟 TF–DNA 结合成本高，无法对所有变异进行模拟；eQIF 可提供候选变异优先级。
   - **核心假设**: eQIF 高分数变异在 MD 模拟中更可能显示结合自由能显著变化。
   - **初步方法**: 选取 eQIF 分数 top 1% 和 bottom 50% 的 TFBS 变异各 100 个，进行 MD 模拟比较结合自由能变化。
   - **验证方式**: 两组变异自由能变化分布的效应量。
   - **创新状态**: unverified