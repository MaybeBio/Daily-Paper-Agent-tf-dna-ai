## 01 基本信息

- **标题**：Identification of drug responsive enhancers by predicting chromatin accessibility change from perturbed gene expression profiles
- **作者与单位**：Wang, Yongcui（中国科学院昆明植物研究所）；Wang, Yong（中国科学院数学与系统科学研究院/中国科学院大学，推测，原文未明确标注单位全称）
- **期刊/预印本平台**：NPJ Systems Biology and Applications
- **年份**：2024-05-31
- **论文类型**：方法学/计算框架研究
- **领域**：计算基因组学、药物基因组学、基因调控
- **关键词**：enhancer、chromatin accessibility、drug response、gene expression、regulatory element
- **DOI/arXiv 号**：10.1038/s41540-024-00388-8
- **代码**：未提供
- **数据**：ENCODE（167 个细胞系配对 DNase-seq 和 RNA-seq）、ROADMAP（独立验证）、CMAP、CDS-DB、GeneHancer、ENCODE ChIP-seq、GTEx eQTL、PharmGKB
- **阅读日期**：2025-06-10（示例）
- **在「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法/物理模拟」方向中的位置**：本文属于「从基因表达预测染色质可及性」的监督回归任务，核心是 TF–增强子–基因三者的调控网络。与 TF–DNA 结合机制的直接关系在于：模型显式利用 TF 在增强子上的结合（ChIP-seq 定义的 TF-增强子网络）作为预测特征，且下游分析将差异增强子与 TF motif 关联。方法上属于轻量级机器学习（Elastic Net / RF / SVM），不涉及深度学习或物理模拟，但「用表达谱推断调控元件活性」的思路可迁移到 TF–DNA 结合亲和力预测或增强子-启动子互作建模。

---

## 02 一句话总结

本文提出 PERD 框架，用 Elastic Net / RF / SVM 回归模型，以增强子关联的 TF 和下游基因的表达水平为特征，预测增强子染色质可及性（DNase-seq 信号），并将该模型应用于 CMAP 和 CDS-DB 药物扰动表达数据，识别药物响应增强子（diffEnhancers），进而与 eQTL/PGx 变异关联，为药物敏感性相关非编码变异提供候选调控元件解释。

---

## 03 研究问题

- **具体问题**：药物扰动后，哪些增强子的染色质可及性会发生显著变化？由于缺乏大规模药物扰动后的染色质可及性实验数据，能否仅从药物扰动后的基因表达谱推断增强子可及性变化？
- **为什么重要**：大多数药物相关遗传变异位于非编码调控区（如增强子），这些变异可能通过改变 TF 结合或增强子活性影响药物反应。若能系统识别药物响应增强子，可增强药物相关基因变异的因果解释，助力个体化用药。
- **现有方法不足**：直接测量药物扰动后染色质可及性的实验数据（如药物处理后的 DNase-seq/ATAC-seq）严重匮乏；已有计算工作多聚焦于编码区或启动子，缺乏从表达谱推断增强子活性的系统框架。
- **精确研究问题（Can...?）**：Can we predict genome-wide enhancer chromatin accessibility from gene expression profiles of associated genes and binding TFs, and thereby identify enhancers whose accessibility significantly changes upon drug perturbation?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引用与论述，标注为「仅本文框架」；未逐一核验外部文献。

1. **药物基因组学从编码区转向非编码区**：早期药物反应研究聚焦编码区变异（如药物代谢酶 CYP 基因），但 GWAS 显示大量药物相关变异位于非编码调控区（如增强子），提示调控元件在药物反应中的重要性。
2. **调控元件活性测量技术**：DNase-seq、ATAC-seq 可全基因组测量染色质可及性，ChIP-seq 可定位 TF 结合位点，Hi-C 等可揭示增强子-启动子互作。ENCODE、ROADMAP 积累了跨细胞系/组织的配对数据。
3. **从表达谱推断调控活性的计算尝试**：BIRD（Zhou et al.）首次用表达谱预测 DNase 超敏位点活性，但未聚焦增强子，也未与药物扰动结合。
4. **大规模药物扰动表达数据库**：CMAP、CDS-DB 提供了药物处理前后的基因表达谱，但缺乏对应的染色质可及性数据。
5. **本文主张的位置**：在 BIRD 思路上扩展，显式引入 TF-增强子网络先验知识，将预测单元从全基因组 DH 位点聚焦到增强子，并首次将「表达→可及性」预测模型应用于药物扰动场景，输出药物响应增强子并关联 PGx 变异。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 药物扰动后染色质可及性数据匮乏 | 无法直接测量药物处理后的增强子活性变化 | 大规模药物扰动染色质实验成本高、通量低 | Introduction：「perturbed chromatin activity profiles... are seriously inadequate compared to several main large scale perturbed gene expression profile datasets」 |
| 非编码药物相关变异功能解释困难 | GWAS 变异位于增强子但无法解释其如何影响药物反应 | 缺乏药物响应增强子的系统注释 | Introduction：「GWAS has uncovered numerous variants associated with drug sensitivity, with a majority of them situated within non-coding regulatory elements」 |
| 表达谱与染色质可及性的关联建模不足 | 已有方法未充分利用 TF-增强子网络先验 | 简单回归忽略调控层级结构 | Methods：模型显式引入 TF-增强子、增强子-基因网络作为特征约束 |
| 预测精度受增强子特性限制 | 仅约 50% 增强子可被较好预测（cross-cell PCC > 0.5） | 增强子活性受组织特异性、细胞状态等多因素影响 | Results：「only about 50% (26892/54076) enhancers have their across-cell P-T correlation larger than 0.5」 |
| 药物响应增强子与基因变异的关联缺乏验证 | 预测的 diffEnhancer 与 eQTL/PGx 变异关联较弱 | 数据稀疏、样本量有限 | Results：仅少数药物（如 LY-294002）有较多 diffEnhancer 与 PGx 关联 |

---

## 06 核心思想

1. **表面方法**：构建增强子-基因网络（GeneHancer）和 TF-增强子网络（ENCODE ChIP-seq），以增强子关联 TF 和下游基因的表达量为特征，用回归模型（Elastic Net / RF / SVM）预测增强子染色质可及性（DNase-seq 信号最大值）。训练后应用于药物扰动表达数据，比较处理前后预测可及性，识别显著变化的增强子（diffEnhancers），并关联 TF motif 与 PGx 变异。

2. **核心洞察**：增强子的染色质可及性可由其「上游 TF 表达」和「下游靶基因表达」共同推断——TF 表达反映结合活性，靶基因表达反映增强子的调控输出。这一「双向信息」设计比单纯用基因表达或序列特征更有效。此外，将预测单元从全基因组 DH 位点聚焦到增强子，可减少噪声并增强生物学可解释性。

3. **[Analysis] 可能的普适教训**：在数据匮乏的场景下，利用「调控网络先验」将不可观测的中间变量（增强子活性）与可观测的上下游变量（TF 表达、靶基因表达）桥接，是一种可迁移的建模策略。对 TF–DNA 结合研究而言，这意味着：当无法直接测量 TF 结合或染色质状态时，可尝试用 TF 表达 + 靶基因表达作为代理特征，构建「表达→结合/可及性」的预测模型。

---

## 07 方法总览

- **输入**：
  - 增强子-基因关联网络（GeneHancer）
  - TF-增强子关联网络（ENCODE ChIP-seq 定义的 TF 结合位点落在增强子区域）
  - 配对 RNA-seq 表达矩阵和 DNase-seq 可及性矩阵（ENCODE 167 个细胞系）
  - 药物扰动表达数据（CMAP、CDS-DB）
- **输出**：
  - 每个增强子的预测可及性值（连续值）
  - 药物处理后显著变化的增强子列表（diffEnhancers）
  - diffEnhancer 关联的 TF motif、靶基因、eQTL/PGx 变异
- **模块**：
  1. 网络构建模块：从 GeneHancer 提取增强子-基因关联，从 ENCODE ChIP-seq 提取 TF-增强子关联
  2. 特征构建模块：对每个增强子，聚合其关联 TF 和靶基因的表达值作为特征向量
  3. 回归预测模块：Elastic Net（主模型，R glmnet）、RF、SVM 对比
  4. 药物响应分析模块：用训练好的模型预测药物处理前后可及性，计算 fold change 和 p 值（Wilcoxon 秩和检验），筛选 diffEnhancers
  5. 下游关联模块：diffEnhancer 与 TF motif、GTEx eQTL、PharmGKB PGx 变异关联
- **训练**：ENCODE 167 个细胞系配对数据，留一法交叉验证（LOOCV）评估；独立验证用 ROADMAP 数据
- **反馈回路**：无显式反馈回路；模型为单步监督回归
- **假设**：
  - 增强子可及性可由其关联 TF 和靶基因表达线性/非线性组合预测
  - 药物扰动后表达变化可外推到可及性变化（即训练域与药物扰动域的可及性-表达关系一致）
  - GeneHancer 和 ChIP-seq 定义的增强子-基因/TF 关联是可靠的先验

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 增强子-基因网络构建 | 定义每个增强子的下游靶基因集合 | 提供预测可及性的「下游输出」特征 | 输入：GeneHancer 数据库；输出：增强子-基因关联表 | Methods「Construction of enhancer-gene, and TF-enhancer network」 | [预期] 移除后仅剩 TF 表达特征，预测精度下降（作者未做消融，属预期推断） |
| TF-增强子网络构建 | 定义每个增强子的上游 TF 集合 | 提供预测可及性的「上游调控」特征 | 输入：ENCODE ChIP-seq；输出：TF-增强子关联表 | Methods 同节 | [预期] 移除后失去 TF 结合先验，模型退化为纯基因表达预测，精度下降 |
| 回归预测模型（Elastic Net / RF / SVM） | 从表达特征预测增强子可及性 | 核心预测引擎 | 输入：TF+靶基因表达向量；输出：预测可及性值 | Results 图 2：RF 优于 Elastic Net 和 SVM（cross-cell/cross-enhancer PCC 更高） | [实测] 作者比较了三种回归算法，RF 最优；移除 RF 改用 Elastic Net 会降低 PCC |
| 药物响应增强子检测 | 比较药物处理前后预测可及性，筛选显著变化增强子 | 输出最终生物学发现 | 输入：CMAP/CDS-DB 处理前后表达；输出：diffEnhancers 列表 | Results「Revealing the drug responsive enhancers」 | [预期] 移除后无法识别药物响应增强子，框架失去应用价值 |
| TF motif 关联 | 将 diffEnhancers 与 TF motif 匹配 | 解释哪些 TF 可能介导药物响应 | 输入：diffEnhancers 序列；输出：TF motif 富集 | Results「PERD associates genetic variants with drug responsive enhancers」 | [预期] 移除后失去调控机制解释 |
| PGx/eQTL 关联 | 将 diffEnhancers 与已知药物相关变异关联 | 提供遗传变异的功能注释 | 输入：GTEx eQTL、PharmGKB；输出：候选药物响应变异-增强子对 | Results 图 4、图 5 | [预期] 移除后无法将增强子与个体差异关联 |

---

## 09 关键公式符号

**主模型（公式 1）**：

$$\min_{\alpha,\beta} \| O - \alpha_0 - \beta_0 - \gamma_T \sum_{p \in E_T} \alpha_p TF_p - \gamma_G \sum_{q \in E_G} \beta_q TG_q \|_2^2 + \lambda(\|\alpha\|_2^2 + \|\alpha\|_1 + \|\beta\|_2^2 + \|\beta\|_1)$$

- $O$：目标增强子的染色质可及性值（DNase-seq 信号最大值）
- $TF_p$：第 $p$ 个与该增强子结合的 TF 的表达水平
- $TG_q$：第 $q$ 个与该增强子关联的靶基因的表达水平
- $E_T$、$E_G$：该增强子的 TF 集合和靶基因集合
- $\alpha_p$、$\beta_q$：TF 和靶基因的回归系数
- $\gamma_T$、$\gamma_G$：TF 和靶基因的预设权重（作者设 $\gamma_T = \gamma_G$）
- $\lambda$：正则化参数（Elastic Net 混合 L1/L2）
- 用途：将增强子可及性分解为上游 TF 表达和下游靶基因表达的加权组合
- 直觉：增强子活性 = f(结合它的 TF 的表达, 它调控的基因的表达)
- 来源：Methods「Learning enhancer's chromatin accessibility from its associated genes and binding TFs' expression」

**评估指标**：

- 跨细胞系相关（cross-cell correlation）：$\tau_C = cor(O_{.m}, \hat{O}_{.m})$
- 跨增强子相关（cross-enhancer correlation）：$\tau_E = cor(O_{n.}, \hat{O}_{n.})$
- 平方预测误差：$\tau = \frac{\sum_n \sum_m (O_{nm} - \hat{O}_{nm})^2}{\sum_n \sum_m (O_{nm} - \bar{O})^2}$

---

## 10 实验设计与证据链

**数据集/群体**：
- 训练：ENCODE 167 个细胞系配对 RNA-seq + DNase-seq
- 独立验证：ROADMAP 配对数据
- 药物扰动表达：CMAP（MCF7 乳腺癌、PC3 前列腺癌细胞系）、CDS-DB（乳腺癌患者来源细胞）
- 增强子定义：GeneHancer 数据库
- TF 结合：ENCODE ChIP-seq

**指标**：cross-cell PCC、cross-enhancer PCC、平方预测误差

**基线/对比**：Elastic Net vs RF vs SVM；仅用靶基因表达（EopenByTG）vs 同时用 TF+靶基因表达（EopenByTFandTG）

**预算/骨干/仪器**：未提供（计算资源未说明）

**oracle 输入**：无（模型输入为真实表达数据，输出为可及性预测）

**评测协议**：LOOCV（167 细胞系）；独立 ROADMAP 验证；药物扰动场景无金标准可及性数据，仅通过下游关联间接验证

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 回归算法对比 | RF 是否优于 Elastic Net 和 SVM | 三种算法在 ENCODE 167 细胞系 LOOCV 下比较 | RF 获得更高 cross-cell/cross-enhancer PCC 和更小误差 | RF 是更优的回归器 | 未报告统计显著性检验 | Results 图 2a–f |
| 特征消融：TF+靶基因 vs 仅靶基因 | 加入 TF 表达是否提升预测 | EopenByTFandTG vs EopenByTG | EopenByTFandTG 一致优于 EopenByTG | TF 表达信息对预测可及性有增量贡献 | 未报告消融幅度具体数值 | Results 图 2a–f |
| 独立验证 | 模型是否泛化到新数据 | ENCODE 训练 → ROADMAP 测试 | cross-enhancer PCC > 0.5，误差 < 0.4 | 模型具有跨数据集泛化能力 | 未报告跨组织/跨条件的系统评估 | Results「Evaluation of prediction model in an independent dataset」 |
| 药物响应增强子检测 | 能否从药物扰动表达识别显著可及性变化增强子 | CMAP 处理前后预测可及性比较 | 各药物识别出数量不等的 diffEnhancers（如 LY-294002 有 494 个） | 模型可输出候选药物响应增强子 | 无实验验证可及性变化真实性 | Results 图 4、补充图 6 |
| diffEnhancer 与 PGv 关联 | 预测的增强子是否富集药物相关变异 | diffEnhancers 与 GTEx eQTL、PharmDKB 变异重叠 | 部分药物（如 LY-294002）的 diffEnhancers 含 eQTL 变异，且变异关联基因与增强子靶基因一致 | 增强子变异可能介导药物反应 | 样本量小，未做多重检验校正 | Results 图 5、补充表 1 |

---

## 11 结论正确解读

- **任务范围**：本文解决的是「从表达谱预测增强子可及性」的回归任务，而非「从序列预测可及性」或「TF–DNA 结合机制的直接建模」。模型输出的是增强子可及性的预测值，而非实验测量值。
- **oracle/真值输入**：训练阶段使用真实 DNase-seq 信号作为监督标签；药物扰动阶段无真值可及性数据，diffEnhancers 的「显著性」基于预测值的统计比较，而非实验验证。
- **端到端状态**：非端到端。模型分阶段：先训练可及性预测器，再应用于药物扰动表达，最后做下游关联。各阶段误差会累积。
- **算力成本**：未报告。模型为轻量级回归（Elastic Net / RF / SVM），计算成本低，但特征构建依赖大规模 ChIP-seq 和 GeneHancer 数据库。
- **历史数据依赖**：强依赖 ENCODE/ROADMAP 的配对表达-可及性数据；药物扰动表达来自 CMAP/CDS-DB，不同批次、平台间可能存在批次效应。
- **模型依赖**：预测质量依赖增强子-基因和 TF-增强子网络先验的准确性；GeneHancer 和 ChIP-seq 的覆盖度与噪声直接影响特征质量。
- **最难情形**：低表达、低可及性、组织特异性强的增强子预测精度差；药物处理后表达变化小的增强子难以检测；稀有细胞类型或疾病状态缺乏训练数据。
- **群体/领域边界**：模型在 ENCODE/ROADMAP 的细胞系数据上训练，主要适用于癌细胞系和常见组织类型；对原代细胞、罕见组织或疾病特异状态的泛化能力未验证。
- **不确定性**：diffEnhancers 的 p 值基于预测值分布，未考虑预测误差传播；eQTL/PGv 关联未做多重检验校正，存在假阳性风险。
- **有边界的复述**：PERD 能在 ENCODE/ROADMAP 数据上以中等精度（cross-enhancer PCC > 0.5）从表达谱预测增强子可及性，并能从 CMAP/CDS-DB 药物扰动表达中识别候选药物响应增强子，部分增强子与已知药物相关 eQTL 变异重叠，但所有药物响应增强子均未经过实验验证。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 预测精度有限 | 仅约 50% 增强子 cross-cell PCC > 0.5 | 未明确提及改进方向 | Results「Characterization of the well predicted enhancers」 |
| 组织/细胞类型特异性 | 预测效果在不同组织类型间差异显著 | 未来将应用 PERD 于更大规模数据（如 LINCS L1000）以获得更稳定结果 | Discussion |
| 数据覆盖不足 | 药物扰动染色质数据缺乏，无法直接验证 | 未来尝试基于配对单细胞 ATAC-seq 和 RNA-seq 进行研究 | Discussion |
| 仅关注增强子 | 未涵盖启动子、绝缘子等其他调控元件 | 未明确提及 | 全文范围限定于 enhancer |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 模型用表达预测可及性，但可及性与表达存在双向因果 | 可及性变化可能是表达变化的原因而非结果；模型可能学到相关性而非因果性 | 若用于药物响应推断，因果方向错误会导致错误结论 | 使用扰动实验（如 CRISPR 敲除 TF 后同时测表达和可及性）检验因果方向 | 模型公式 1 将可及性作为表达的函数 |
| 增强子-基因网络来自 GeneHancer，可能包含大量假阳性关联 | 特征噪声会直接降低预测精度，且下游靶基因选择偏差影响解释 | 网络先验质量决定模型上限 | 使用不同增强子-基因数据库（如 FOCS、ABC Model）对比预测结果 | Methods「Construction of enhancer-gene... network」 |
| 药物扰动场景无金标准验证 | diffEnhancers 的「显著性」完全基于预测值，无法区分真实信号与预测误差 | 核心应用场景缺乏验证，结论强度有限 | 对部分 diffEnhancers 进行实验验证（如 ATAC-seq 处理前后比较） | Results 图 4、图 5 均为计算预测 |
| 仅用 DNase-seq 最大值代表增强子活性 | 可及性是一个分布而非单值，最大值可能丢失增强子内部结构信息 | 简化可能掩盖增强子亚区域的功能差异 | 使用可及性峰的形状特征或分位数作为替代标签 | Methods：O 定义为「maximum DH signal along this enhancer region」 |
| 未报告特征重要性或可解释性分析 | 哪些 TF 对预测贡献最大？模型是否学到已知的调控逻辑？ | 可解释性对生物学发现至关重要 | 计算特征重要性（如 RF 的 Gini importance）并与已知 TF-增强子调控关系对比 | 全文未提供特征重要性分析 |
| 样本量有限（167 细胞系）且以癌细胞系为主 | 模型可能过拟合癌细胞系的调控特征，泛化到正常组织或原代细胞存疑 | 药物反应个体差异涉及正常组织，泛化性影响应用价值 | 在 GTEx 正常组织配对数据上评估预测性能 | 数据集描述仅提及 ENCODE/ROADMAP 细胞系 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **「表达→可及性」的代理建模策略**：当直接测量染色质可及性（DNase-seq/ATAC-seq）的数据稀缺时，可用配对表达数据训练回归模型，将表达谱映射到可及性。对 TF–DNA 结合研究而言，这意味着：TF 结合位点的活性可能可由 TF 表达 + 靶基因表达推断，无需 ChIP-seq 实验。
2. **调控网络先验作为特征约束**：将增强子-基因（GeneHancer）和 TF-增强子（ChIP-seq）网络作为先验，将特征空间从全基因组压缩到每个增强子的局部调控邻居，既降维又增强生物学可解释性。可迁移到 TF–DNA 结合预测：用 TF 的已知靶基因集合和共表达网络作为特征，而非仅用序列。
3. **双向信息设计**：同时使用「上游 TF 表达」和「下游靶基因表达」预测增强子活性，比单用任一方向更有效。对 TF–DNA 结合机制研究，这提示：结合活性可能同时受 TF 丰度（上游）和靶基因反馈（下游）调控，建模时应同时考虑。
4. **跨数据集验证的必要性**：ENCODE 训练 → ROADMAP 验证的设计值得借鉴。在 TF–DNA 结合预测中，应使用不同实验技术（ChIP-seq vs CUT&Tag vs HT-SELEX）或不同物种数据进行交叉验证。
5. **药物扰动场景的「计算增强子」概念**：将预测模型应用于药物处理前后表达差异，识别响应增强子，再关联 eQTL/PGv 变异。这一「表达差异→调控元件差异→遗传变异」的级联分析框架，可迁移到 TF–DNA 结合研究：用药物处理前后的 TF 结合预测变化来识别药物响应的结合位点。
6. **轻量级模型的实用性**：Elastic Net / RF 等传统模型在中等规模数据上即可获得可用预测，并非所有任务都需要深度学习。对 TF–DNA 结合预测，当特征维度适中且先验网络可用时，简单模型可能更稳健、更易解释。

---

## 15 与已有知识连接

- **BIRD（Zhou et al.）**：本文直接受 BIRD 启发，BIRD 首次用表达谱预测全基因组 DH 位点活性。本文的改进在于聚焦增强子、引入 TF-增强子网络先验、并应用于药物扰动场景。可连接至 TF–DNA 结合预测中的「表达特征」方法。
- **GeneHancer（Fishilevich et al.）**：增强子-基因关联数据库，本文用于构建靶基因特征。该数据库也可用于 TF–DNA 结合研究中的增强子-靶基因功能验证。
- **ENCODE / ROADMAP 配对数据**：本文训练和验证的基础数据。这些数据同样可用于训练 TF–DNA 结合预测模型（如用 ChIP-seq 定义结合位点，用 DNase-seq 定义可及性）。
- **CMAP / CDS-DB 药物扰动表达数据库**：本文应用场景的数据来源。这些数据库可与 TF–DNA 结合预测结合，用于识别药物扰动的 TF 结合变化。
- **Elastic Net（Zou & Hastie）**：本文主模型，L1+L2 正则化适合高维稀疏特征。在 TF–DNA 结合预测中，Elastic Net 常用于序列特征（k-mer）回归。
- **GTEx eQTL / PharmGKB**：本文下游验证资源。eQTL 变异与增强子重叠分析可迁移至 TF–DNA 结合研究：结合 QTL 变异是否影响 TF 结合（等位基因特异性结合）。
- **[Analysis] 可连接但未引用的方向**：深度学习序列模型（如 DeepSEA、Basenji）可预测可及性，但需要序列输入而非表达输入；本文的表达→可及性方向与序列→可及性方向互补，未来可融合。此外，AlphaFold 等结构预测方法不适用于增强子可及性任务，但可用于预测 TF 突变对结合的影响，与本文的「变异→增强子」分析互补。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

**候选 1：融合序列与表达特征的 TF–DNA 结合预测模型**
- **来源局限/观察**：本文仅用表达特征预测可及性，未利用增强子序列信息；而序列模型（如 DeepSEA）仅用序列，未利用表达上下文。
- **核心假设**：TF–DNA 结合强度同时受序列基序（静态）和细胞状态（动态，由表达反映）调控，融合两者可提升预测精度。
- **初步方法**：对每个增强子，提取序列 k-mer 特征 + 关联 TF 表达 + 靶基因表达，训练多模态回归/分类模型（如梯度提升或浅层 MLP），预测 ChIP-seq 峰强度或可及性。
- **验证方式**：ENCODE 多细胞系交叉验证；比较单模态 vs 融合模型的 AUC/PCC。
- **创新状态**：unverified

**候选 2：药物扰动下的 TF 结合变化预测（TF–drug response）**
- **来源局限/观察**：本文预测增强子可及性变化，但未直接预测 TF 结合变化；TF 是药物响应的直接介导者。
- **核心假设**：药物处理导致的表达变化可映射到特定 TF 的结合活性变化，且这些 TF 结合变化可解释药物敏感性差异。
- **初步方法**：用本文的回归框架，将输出从增强子可及性改为 TF 结合强度（用 ChIP-seq 数据训练），应用于 CMAP 药物处理表达，预测每个 TF 的结合变化，再与药物敏感性 QTL 关联。
- **验证方式**：对已知药物靶点通路中的 TF，检查预测结合变化是否与实验 ChIP-seq（如有）一致；与 PharmGKB 变异关联。
- **创新状态**：unverified

**候选 3：增强子-启动子互作作为中间变量的三层调控模型**
- **来源局限/观察**：本文假设增强子可及性直接由 TF 和靶基因表达决定，但实际存在增强子-启动子互作（3D 结构）这一中间层。
- **核心假设**：引入增强子-启动子互作强度（如 Hi-C 数据）作为中间变量，可提升可及性预测精度，并解释组织特异性。
- **初步方法**：构建三层模型：TF 表达 → 增强子-启动子互作 → 靶基因表达 → 可及性；用结构方程模型或深度生成模型建模。
- **验证方式**：在具有 Hi-C 和 DNase-seq 配对数据的细胞系上评估；比较有无互作中间层的预测性能。
- **创新状态**：unverified

**候选 4：等位基因特异性增强子可及性预测（variant effect on TF binding）**
- **来源局限/观察**：本文关联 eQTL 变异与增强子，但未预测变异对可及性的影响；TF–DNA 结合的核心问题是变异如何改变结合。
- **核心假设**：增强子内的遗传变异通过改变 TF 结合基序影响可及性，且这种影响可通过表达特征增强预测。
- **初步方法**：对每个 eQTL 变异，计算参考/替代等位基因的基序匹配分数差异，结合本文的表达特征，预测变异对可及性的影响（delta-DNase）。
- **验证方式**：用已发表的 allele-specific DNase-seq 或 ChIP-seq 数据验证；比较有/无表达特征的预测精度。
- **创新状态**：unverified

**候选 5：从药物响应增强子到 TF–DNA 结合机制的反向推断**
- **来源局限/观察**：本文输出 diffEnhancers 但未解释其分子机制；TF–DNA 结合研究需要机制层面的解释。
- **核心假设**：diffEnhancers 中富集的 TF motif 可揭示药物作用的转录调控通路，且这些 TF 的结合变化是药物反应的关键驱动。
- **初步方法**：对 diffEnhancers 做 TF motif 富集分析，构建药物-TF-增强子-基因调控网络，用网络传播算法识别关键 TF 节点。
- **验证方式**：与已知药物机制文献对比；用 siRNA 敲低预测的关键 TF 后检测药物敏感性变化。
- **创新状态**：unverified