## 01 基本信息

- **标题**：Integrated Framework for Probing Multimodal Protein Foundation Models with Structure-Functional Interpretability Analysis in Detection of Allosteric Binding Sites
- **作者与单位**：Alina Bazarova（Helmholtz AI 等）；Gennady M. Verkhivker（Chapman University, Schmid College of Science and Technology）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2026（预印本日期 2026-07-07）
- **论文类型**：方法学研究 + 系统性基准评测
- **领域**：蛋白质-配体结合位点预测；变构位点检测；多模态蛋白质基础模型；可解释性分析
- **关键词**：allosteric binding site；multimodal protein foundation models；OneProt；embedding ablation；variance decomposition；structure-functional interpretability
- **DOI/arXiv 号**：10.64898/2026.07.02.736203
- **代码**：https://github.com/oneprot-models/oneprot-embeddings
- **数据**：https://doi.org/10.5281/zenodo.20997998（含 HDF5 口袋结构、数据划分、模型 checkpoint）
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文聚焦**变构 vs 正构结合位点的判别**（而非 TF–DNA 结合），但其核心问题——**多模态基础模型（序列、结构、功能文本、动力学）中哪些模态对位点功能类别判别有贡献、何时有效**——与 TF–DNA 结合机制研究中"哪些生物信号（序列保守性、结构几何、动力学柔性、功能注释）决定结合特异性"高度同构。其**双层次消融框架（encoder 级 + embedding 级）+ 方差分解**的方法论可直接迁移到 TF–DNA 互作研究中，用于剖析不同模态对 TF 结合位点（如 TFBS vs 非结合位点、直接读码 vs 间接读码）判别能力的贡献。

---

## 02 一句话总结

本文构建了一个统一分析框架，通过在四个数据集（PPI-Site、KinSite、Dual-Site、AlloDiverse）上对 OneProt 多模态蛋白质基础模型进行 encoder 架构消融与 embedding 组合消融，结合方差分解和结构-功能可解释性分析，发现**数据集内在属性（而非模型架构）主导变构/正构位点判别性能**（数据集身份解释 63.7% 可解释方差），且模态贡献高度依赖数据集的生物学分离度。

---

## 03 研究问题

- **具体问题**：多模态蛋白质基础模型（整合序列、结构、功能文本、动力学）在区分变构与正构结合位点时，其性能究竟由什么决定？不同生物模态（序列保守性、结构几何、功能注释、动力学柔性）在何种数据集条件下贡献最大？
- **为什么重要**：变构位点识别是药物设计的关键瓶颈。现有方法多聚焦于预测精度提升，但缺乏对"什么信号在什么条件下有效"的系统理解，导致模型选择与数据构建缺乏理论指导。
- **现有方法不足**：
  - 多数研究仅报告单一基准上的精度，未系统分离数据集属性与模型架构的贡献；
  - 缺乏对模态贡献的定量归因（哪些模态真正提供判别信号）；
  - 未将预测成功/失败与底层生物学组织（结构域、功能注释、进化保守性）关联。
- **精确研究问题（Can...?）**：Can systematic ablation of encoder architectures and embedding combinations across datasets of varying biological separability reveal whether dataset intrinsic properties or model architectural choices dominate allosteric vs orthosteric binding site discrimination, and can structure-functional interpretability link prediction success to underlying biological organization?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 的叙述框架，标注为「仅本文框架」；未逐一外部核验。

1. **几何/能量方法时代**：Fpocket、SiteHound、MetaPocket 2.0 等基于几何与能量打分，依赖静态结构，难以捕捉变构位点的构象柔性特征。
2. **机器学习方法**：P2Rank 等利用局部化学环境打分，精度提升但依赖手工特征，对变构位点的异质性（缺乏保守几何模板）鲁棒性不足。
3. **深度学习方法**：DeepSite、FRSite、BiteNet 等引入 voxel、目标检测、动力学感知架构，在正构位点上表现优异，但在变构位点上性能下降——因为变构位点缺乏序列保守性和明确几何边界。
4. **蛋白质基础模型**：PLM（ESM2 等）从序列中学习进化约束；结构模型（ProNet、Foldseek token）捕捉几何组织；多模态模型（OneProt）进一步整合功能文本与动力学。但**多模态是否必然优于单模态、何时优于单模态**缺乏系统验证。
5. **本文主张的位置**：在"基础模型 + 下游任务"范式中，插入一个**诊断层**——通过系统消融 + 方差分解 + 结构-功能可解释性，回答"什么信号在什么条件下有效"，而非仅追求更高精度。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 变构位点判别精度低 | PPI-Site 上所有模型 AUC 仅 0.55–0.60，接近随机 | 变构与正构位点共享结构/序列上下文，类别标签由空间关系（相对 PPI 界面）而非内在化学差异定义 | Results 图 2A；Discussion 对 PPI-Site 的阐述 |
| 模态贡献不明确 | 不同数据集上最优 embedding 组合不同，无普适最优 | 模态贡献取决于数据集内在分离度：低分离度下额外模态引入噪声，高分离度下多模态收敛 | Results 图 5；Table 3 |
| 类不平衡严重 | KinSite 中 ρ ≈ 51.1，PR-AUC 远低于 ROC-AUC（0.05–0.16） | 变构位点在结构数据库中稀疏，正类样本极少 | Results 图 2B；Supporting Table S2 |
| 架构选择缺乏指导 | 架构贡献仅 3.4% 方差，远低于数据集身份（63.7%） | 架构差异在强信号下被淹没，在弱信号下无法补偿数据内在不可分性 | Results 图 4；Discussion |
| 预测成功缺乏生物学解释 | 仅报告精度无法回答"为什么对/错" | 缺乏将预测结果与结构域、功能注释、进化保守性关联的分析层 | Results 图 8–9；Structure-Functional Interpretability 节 |

---

## 06 核心思想

**1) 表面方法**：
- 采用 OneProt 多模态基础模型（序列 ESM2、结构 Foldseek token、结构图 ProNet、动力学 MDGen、文本 BiomedBERT），冻结 encoder，仅训练轻量 MLP 分类器。
- 双层次消融：(a) **encoder 级**——7 种架构（Pocket+Text 基线、±ST、±SG、±MD 的组合）；(b) **embedding 级**——4 种下游特征组合（Pocket、Pocket+Text、Pocket+Sequence、Pocket+Sequence+Text）。
- 在 4 个数据集上执行 28 种 encoder–embedding 组合 × 10 随机种子 = 1,120 次独立实验。
- 全局与分数据集方差分解（factorial ANOVA）量化数据集、embedding、架构及其交互的方差贡献。
- 对最佳配置的 TP/TN 预测进行结构-功能可解释性分析（结构域、配体类型、构象状态、序列保守性）。

**2) 核心洞察**：
- **数据集身份主导性能**（63.7% 可解释方差），而非架构或 embedding 选择；
- **模态贡献是 regime-dependent 的**：低分离度（PPI-Site）下，额外模态（序列、文本）不仅无益反而有害；中分离度（KinSite）下，文本模态提供关键功能上下文；高分离度（AlloDiverse）下，几乎所有架构收敛到近天花板性能；
- **预测成功反映生物学组织**：TP/TN 的分布与结构域家族、配体类型、构象状态系统关联，而非随机。

**3) 可能的普适教训 [Analysis]**：
- 在生物医学 ML 中，**数据的内在可分离性应先于模型架构被诊断**。当类别由空间/关系定义而非内在化学差异定义时（如 PPI-Site 的变构/正构、TF–DNA 中的间接读码 vs 直接读码），任何模态组合都无法补偿缺失的判别信号。
- **多模态不是免费的**：在低分离度下，额外模态引入与判别无关的方差，稀释有效信号。模态选择应基于对目标生物学问题的先验理解，而非"越多越好"。
- **方差分解 + 消融是比单一精度更信息密集的评估协议**，可区分"数据问题"与"模型问题"。

---

## 07 方法总览

- **输入**：蛋白质序列 S、3D 结构 X（口袋区域 100 残基）、UniProt 功能文本注释 T、可选 MD 轨迹 M。
- **特征提取**：冻结的 OneProt 预训练 encoder，分别生成 pocket、sequence、text、structure-token、structure-graph、MD 模态的 embedding（维度 1024 共享空间）。
- **下游分类器**：轻量 MLP（2 隐藏层），sigmoid 输出，二元交叉熵损失，AdamW 优化，最多 50 epochs，early stopping（patience=20）。
- **消融设计**：
  - Encoder 级：7 种架构（是否包含 ST、SG、MD encoder 于预训练阶段）。
  - Embedding 级：4 种特征组合（Pocket / +Text / +Sequence / +Sequence+Text）。
- **统计框架**：全局 factorial ANOVA + 分数据集 ANOVA，方差分量归一化为百分比。
- **可解释性分析**：对最佳配置的 TP/TN 预测，按结构域家族、配体类型、构象状态（如 DFG-in/out）、序列保守性进行分层统计。
- **数据划分**：MMseqs2 以 30% 序列同一性聚类后划分，防止同源泄漏；ASD 继承原始划分并随机拆分验证/测试。

**文字流程**：
1. 从 PPI-Site、KinSite、ASD 原始资源重建固定大小（100 残基）口袋；
2. 对每个口袋提取 5 种模态 embedding（由 7 种 encoder 架构之一生成）；
3. 按 4 种 embedding 组合拼接特征，训练 MLP 分类器；
4. 在验证集选最优 checkpoint，报告测试集 ROC-AUC / PR-AUC；
5. 对全部 1,120 次运行执行 ANOVA 分解；
6. 对最佳配置的预测结果进行结构-功能分层分析。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| **OneProt 多模态 encoder 集合** | 将序列、结构、文本、动力学映射到共享 1024 维空间 | 提供跨模态统一表征，使下游可比较不同模态贡献 | 输入：S / X / T / M；输出：z_pocket, z_seq, z_text, z_ST, z_SG, z_MD | Methods "Multimodal Backbone Architecture"；原 OneProt 论文 [48] | 移除任一 encoder 改变预训练阶段模态对齐，影响共享空间结构（作者通过 7 架构消融验证） |
| **Encoder 级消融（7 架构）** | 控制预训练阶段哪些模态参与对齐 | 区分"模态信息是否在预训练中塑造了表征" | 输入：模态子集；输出：不同架构的 embedding 空间 | Table 1；Results 图 6 | 预期影响：移除 ST/SG/MD 改变 latent space 组织，但下游影响因数据集而异（实测：架构贡献仅 3.4% 方差） |
| **Embedding 级消融（4 组合）** | 控制下游分类器可见的特征 | 区分"哪些模态特征对判别有直接贡献" | 输入：z 的子集拼接；输出：分类概率 | Table 2；Results 图 5 | 实测：低分离度下添加序列/文本降低性能；中分离度下文本提升；高分离度下差异缩小 |
| **MLP 下游分类器** | 从 embedding 组合学习变构/正构判别 | 轻量分类器确保性能差异归因于表征而非分类器容量 | 输入：拼接 embedding；输出：ŷ ∈ [0,1] | Methods "Downstream Allostery Classification" | 预期影响：更复杂分类器可能小幅提升，但不会改变数据集主导性结论 [Analysis] |
| **Factorial ANOVA 方差分解** | 量化数据集、embedding、架构及其交互的方差贡献 | 提供超越精度比较的归因框架 | 输入：全部 1,120 次运行的 ROC-AUC；输出：各因子方差百分比 | Results 图 4；Methods "Variance Decomposition Analysis" | 移除后无法区分数据与模型贡献，结论退化为"某配置在某数据集上更好" |
| **结构-功能可解释性分析** | 将 TP/TN 预测与结构域、配体类型、构象状态关联 | 解释"为什么对/错"，连接预测与生物学 | 输入：TP/TN 集合 + 结构注释；输出：分层统计 | Results 图 8–9；Structure-Functional Interpretability 节 | 移除后仅剩精度报告，无法回答"预测成功反映什么生物学信号" |

---

## 09 关键公式符号

1. **任务形式化**：
   - 蛋白质 P：序列 S ∈ A^L（A 为氨基酸字母表，L 为长度）；结构 X ∈ R^{N×3}（N 原子）；MD 轨迹 M ∈ R^{N×3×τ}（τ 帧）。
   - 口袋 R_B = {r₁, r₂, …, r_K}，K = 100 残基。
   - 标签：y = 1（变构），y = 0（正构）。
   - 编码器输出：z_k ∈ R^d（d = 1024），k ∈ {pocket, seq, text, ST, SG, MD}。
   - 下游特征：z ∈ R^{k·d}（k = 所选 embedding 数）。
   - 分类器：f : R^{k·d} → [0,1]，ŷ = P(y=1|z)。

2. **损失函数**（二元交叉熵）：
   - L = −[y log ŷ + (1−y) log(1−ŷ)]

3. **全局 ANOVA 模型**：
   - ROC_ijkl = μ + α_i(Dataset) + β_j(Embedding) + γ_k(Architecture) + δ_l(Random Seed) + (交互项) + ε_ijkl
   - ε_ijkl ~ N(0, σ²)
   - 方差分量：%Var(factor) = SS_factor / SS_total × 100%

4. **口袋构建**（PPI-Site）：
   - 口袋中心 = 配体原子几何中心；残基按 Cα 到中心距离排序，取前 K=100。
   - 残基重叠：Jaccard 相似系数；原子坐标重叠：KD-tree 最近邻，4 Å 截断。

---

## 10 实验设计与证据链

**数据集/群体**：
- **PPI-Site**：1,845 正构（PLOC）+ 1,689 变构（PLA）位点，1,278 条独特蛋白链，847 个 CATH 家族。低分离度 regime。
- **KinSite**：3,363 正构 + 172 变构（ρ ≈ 51.1），246 种激酶。中分离度 regime，极端类不平衡。
- **Dual-Site**：PPI-Site + KinSite 合并，5,203 正构 + 1,861 变构（ρ = 2.79）。中间-协同 regime。
- **AlloDiverse**：ASD 衍生的 15,904 变构 + 5,203 正构（ρ = 0.33），1,842 种蛋白，247 CATH / 531 Pfam 家族。高分离度 regime。

**指标**：ROC-AUC（主要）、PR-AUC（类不平衡补充）。

**基线/对比**：
- 无外部基线模型；内部对比为 7 encoder 架构 × 4 embedding 组合的完整交叉。
- 随机种子 ×10 提供分布而非点估计。

**关键实验与结果**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 全局性能层次 | 数据集内在分离度决定性能 | 4 数据集 × 全部配置 | PPI-Site AUC ≈ 0.55–0.60；KinSite ≈ 0.70–0.75；Dual-Site ≈ 0.80–0.85；AlloDiverse ≈ 0.95–0.98 | 数据集身份是性能首要决定因素 | 不能归因于单一生物学特征（结构域、配体类型等共同作用） | Results 图 2–3 |
| 全局 ANOVA | 数据集 > embedding > 架构 | 1,120 runs 全因子 | 数据集 63.7%，embedding 1.4%，架构 3.4%，交互项显著 | 数据属性主导，架构与模态选择是二阶因素 | 交互项的具体生物学解释需进一步分解 | Results 图 4 |
| Embedding 消融（PPI-Site） | 额外模态在低分离度下有害 | Pocket vs +Text vs +Sequence vs +Full | Pocket-only 最优（AUC ≈ 0.59）；Full 最差（0.51） | 共享结构/序列上下文下，全局模态引入噪声 | 不能确定噪声来源（是模态本身还是拼接方式） | Results 图 5A |
| Embedding 消融（KinSite） | 文本模态提供关键功能上下文 | 同上 | Pocket+Text（0.59）> Pocket+Sequence（0.50）；Full 最优（0.66） | 功能注释编码激酶特异性调控机制 | 文本模态的哪些语义特征最有效未解析 | Results 图 5B |
| Embedding 消融（Dual-Site） | 结构多样性 + 进化信号协同 | 同上 | Pocket+Sequence 最优（0.78），优于 Full（0.74） | 序列模态在跨家族场景中提供泛化信号；文本在此引入噪声 | 协同机制的具体形式未建模 | Results 图 5C |
| Embedding 消融（AlloDiverse） | 高分离度下多模态收敛 | 同上 | 所有组合 AUC ≥ 0.94；Pocket+Sequence 最优（0.95） | 强信号下模态选择不敏感 | 无法区分"模态冗余"与"模态互补但饱和" | Results 图 5D |
| Encoder 架构消融 | 预训练模态影响下游 | 7 架构 × 固定 Full embedding | 含 ST+SG 的架构在 Dual-Site/AlloDiverse 中稳定最优；MD 增益有限 | 结构 token 与图编码提供互补几何信息 | MD 的有限增益可能因静态口袋表征未充分利用轨迹信息 | Results 图 6 |
| 结构-功能可解释性（PPI-Site） | TP/TN 反映生物学组织 | 最佳配置 TP/TN vs 结构域/配体注释 | 甲基转移酶/SAM 依赖酶占 TP/TN 约 1/3；共享 Rossmann 折叠 | 低分离度源于共享结构上下文，非模型缺陷 | 未量化"构象差异"对判别失败的具体贡献 | Results 图 8 |
| 结构-功能可解释性（KinSite） | 可检测位点类型层次 | TP/TN vs 抑制剂类型 | Type III 可检测；Type IV 不可检测 | 检测能力与位点结构定义和进化保守性相关 | Type IV 的失败是否可通过动力学模态改善未验证 | Results 图 9 |

---

## 11 结论正确解读

- **任务范围**：本文**不预测变构位点的位置**，而是**在已知结合位点位置的前提下，判别其功能类别（变构 vs 正构）**。这是一个简化设定——实际药物发现中位点位置未知，因此本文结论不能直接外推到"变构位点发现"。
- **模型范围**：仅评估 OneProt 架构；结论不必然推广到其他多模态基础模型（如 ESM3、RhoFold+ 等）。
- **数据集范围**：PPI-Site 的变构标签由空间关系（相对 PPI 界面）定义，而非独立实验验证的变构机制；KinSite 的 Type III/IV 分类依赖激酶抑制剂领域知识，不同标注协议可能改变结果。
- **"数据集主导"的边界**：63.7% 方差归因于数据集身份，但这是在**固定模型家族（OneProt）**内的结论。跨模型家族比较可能改变方差分配。
- **模态贡献的边界**：模态贡献是 regime-dependent 的，但 regime 的划分（低/中/高分离度）是事后归纳，缺乏先验的可操作定义。实际应用中如何预判新数据集的 regime 仍开放。
- **有边界的复述**：在 OneProt 框架内、对已知位点的变构/正构判别任务，数据集内在生物学分离度是性能的首要决定因素（63.7% 可解释方差）；模态贡献高度依赖分离度——低分离度下额外模态有害，中分离度下文本模态关键，高分离度下多模态收敛；结构-功能分析表明预测成功反映底层生物学组织而非随机。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 变构位点定义依赖空间关系 | PPI-Site 的变构标签由相对 PPI 界面的空间位置定义，而非独立实验验证的变构机制 | 需整合实验验证的变构机制注释 | Discussion 对 PPI-Site 的阐述 |
| Type IV 位点不可检测 | 即使合并数据集，Type IV 激酶抑制剂位点仍无法可靠恢复 | 需动力学感知表征（如 ensemble 或多构象输入） | Results 图 9M-O；Discussion |
| 模态贡献的 regime 依赖缺乏先验预测 | 低/中/高分离度是事后归纳，无法先验判断新数据集属于哪一 regime | 开发数据集的先验可分离性诊断指标 | Discussion |
| 静态结构表征限制 | MD encoder 增益有限，可能因下游仅用静态口袋而非轨迹 | 探索轨迹级或 ensemble 级表征 | Results 图 6；Discussion |
| 单一模型家族 | 仅评估 OneProt，结论不必然推广到其他多模态基础模型 | 跨模型家族的系统比较 | Discussion |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| "数据集主导"可能部分源于任务难度差异而非生物学信号 | PPI-Site 的 AUC 接近随机可能因为标签本身噪声大（空间关系定义），而非"低分离度"是内在属性 | 若标签噪声是主因，则"数据集主导"结论对真实变构位点发现的指导意义有限 | 在 PPI-Site 上使用实验验证的变构位点子集重跑；或对标签进行噪声注入模拟 | Results 图 2A；Discussion |
| 模态消融未控制 embedding 维度/信息量差异 | 不同模态 embedding 的维度相同（1024），但有效信息密度可能不同；拼接方式（concat）可能引入维度偏差 | 若某模态有效信息密度低，其"有害"效果可能来自维度稀释而非语义噪声 | 尝试加权拼接、注意力融合、或对单模态 embedding 做 PCA 降维后比较 | Methods "Embedding-Level Ablations" |
| ANOVA 的交互项解释不足 | 数据集 × embedding 交互显著（8.3%），但作者未分解哪些具体数据集-模态组合驱动交互 | 交互项可能揭示可操作的模态选择规则，但未充分挖掘 | 对交互项进行事后对比（post-hoc contrasts），识别显著驱动组合 | Results 图 4 |
| 结构-功能可解释性分析为事后描述，非预测性 | TP/TN 分布与结构域/配体类型关联是描述性的，未建立可预测"哪些新位点可被检测"的规则 | 若无法前瞻性预测，则解释性分析对实际药物发现的增量有限 | 在 held-out 结构域家族上测试基于 TP/TN 特征训练的元分类器 | Results 图 8–9 |
| 类不平衡处理仅靠采样，未报告代价敏感学习 | KinSite ρ ≈ 51.1，PR-AUC 极低（0.05–0.16），但未尝试代价敏感损失或阈值优化 | 实际应用中变构位点召回率可能比 AUC 更重要 | 报告不同阈值下的召回率-精确率权衡；尝试 focal loss 等 | Results 图 2B；Supporting Table S2 |
| 未与专门变构位点预测方法对比 | 无 Fpocket、Allosite、DeepAllo 等专用方法基线 | 无法判断 OneProt 多模态方法是否优于专用几何/能量方法 | 在相同数据集上运行专用方法并对比 | 未提供 |

---

## 14 学到什么

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题的可迁移知识。

**Agent 提炼的知识候选**：

1. **双层次消融框架（encoder 级 + embedding 级）**：本文最核心的方法论贡献。在 TF–DNA 研究中，可类比设计：(a) encoder 级——不同预训练模型（ESM2 序列 vs 结构模型 vs DNA 语言模型如 Nucleotide Transformer）；(b) embedding 级——序列保守性（PhyloP/PhastCons）、结构几何（DNA 形状特征如 minor groove width）、功能注释（TF 家族、GO terms）、动力学（MD 导出的 flexibility）。这能回答"TF–DNA 结合特异性主要由序列、结构还是动力学决定"。

2. **方差分解作为模型评估的一等公民**：当数据集包含多种 TF 家族、多种结合模式（直接读码 vs 间接读码）时，ANOVA 可量化"哪个因素（TF 家族身份、结合模式、模态选择）真正驱动性能"，避免仅报告平均精度。

3. **"低分离度 regime"的识别与应对**：PPI-Site 的教训——当正负类别共享结构/序列上下文时（类比：同一 TF 的 consensus 与非 consensus 结合位点），额外模态不仅无益反而有害。TF–DNA 研究中，若任务定义为"同一 TF 的强 vs 弱结合位点"，应预期低分离度，优先使用局部几何特征而非全局序列/功能特征。

4. **模态贡献的 regime-dependence 是特征而非 bug**：本文最有力的实证结论——没有普适最优模态组合。TF–DNA 研究应避免"多模态一定更好"的默认假设，而应基于目标 TF 家族的生物学特性（保守性、结合模式、构象变化程度）选择模态。

5. **结构-功能可解释性作为验证层**：将 TP/TN 预测映射回结构域、配体类型、构象状态，可区分"模型学到了生物学信号"与"模型利用了伪相关"。在 TF–DNA 中，可检验预测成功的位点是否富集特定 DNA 形状特征（如 narrow minor groove）或特定 TF 结构域（如 homeodomain vs zinc finger）。

6. **类不平衡的极端影响**：KinSite 的 ρ ≈ 51.1 导致 PR-AUC 极低，提示在 TF–DNA 数据集中（如少数 TF 的变构/协同结合位点），应优先报告 PR-AUC 而非仅 ROC-AUC，并考虑采样策略的影响。

7. **"数据集身份主导"对基准设计的启示**：如果数据内在分离度是性能首要决定因素，那么 TF–DNA 领域的基准应明确报告数据集的"分离度特征"（如序列保守性差异、结构多样性、类不平衡比），而非仅报告样本量。

---

## 15 与已有知识连接

- **可核验外部文献**：
  - OneProt 原始论文 [48]：多模态蛋白质基础模型的架构与预训练目标（本文所有实验基于该模型）。
  - ESM2 [43]：序列 encoder 的 Transformer 架构。
  - ProNet [50]：蛋白质结构图神经网络。
  - Foldseek [49]：结构 token 化方法。
  - MDGen [52]：MD 轨迹的 Transformer encoder。
  - BiomedBERT [51]：生物医学文本语言模型。
  - 作者前期工作 [31]：PLM + 能量景观/挫折分析用于激酶结合位点预测——本文是其多模态扩展。
  - 变构位点预测方法：Allosite [40]、AlloPred [39]、DeepAllo [41,42]——本文未直接对比，但属于同一任务家族。

- **与 TF–DNA 课题的关联**：
  - **相似性**：TF–DNA 结合特异性研究同样面临"多模态整合"问题——序列 motif（PWM）、结构（DNA 形状、蛋白-DNA 接触）、进化保守性、功能上下文（共因子、染色质状态）。本文的消融框架可直接迁移。
  - **组合性**：本文的"数据集分离度决定模态贡献"结论，与 TF–DNA 领域已知的"直接读码 vs 间接读码"二分法高度吻合——直接读码（如 zinc finger）依赖序列特征，间接读码（如 p53 响应元件）依赖结构/动力学特征。本文提供了验证这一假说的定量框架。
  - **可迁移方法**：ANOVA 方差分解、双层次消融、TP/TN 结构-功能分层分析，均为模型无关方法，可直接应用于 TF–DNA 基础模型（如 AlphaFold3 的蛋白-DNA 复合物预测、DNA 语言模型 embedding）。
  - **冲突点**：本文的"额外模态在低分离度下有害"结论，与 TF–DNA 领域"整合多组学信号提升预测"的常见预期存在张力。需在 TF–DNA 数据上验证是否同样成立。

- **候选方向（未验证）**：将本文的"分离度 regime"概念形式化为可计算的指标（如类间 embedding 距离/类内方差的比值），作为 TF–DNA 数据集构建前的诊断工具。

---

## 16 研究想法

> 以下为面向「蛋白质-DNA 互作（TF–DNA 结合机制）× AI/物理模拟」课题的研究候选。

**候选 1：TF–DNA 结合位点功能类别的多模态消融研究**
- **来源局限/观察**：本文在蛋白-配体上发现模态贡献高度依赖数据集分离度；TF–DNA 领域缺乏类似系统消融。
- **核心假设**：TF–DNA 结合位点的"直接读码 vs 间接读码"分类可通过模态消融区分——直接读码位点由序列 embedding 主导，间接读码位点由结构/动力学 embedding 主导。
- **初步方法**：构建包含多种 TF 家族（zinc finger、homeodomain、bHLH、p53 等）的已知结合位点数据集，提取序列（ESM2/DNA-LLM）、结构（DNA 形状、蛋白-DNA 接触图）、功能（TF 家族、GO）embedding，执行与本文相同的双层次消融 + ANOVA。
- **验证方式**：检验"直接读码 TF 的最优模态 = 序列"、"间接读码 TF 的最优模态 = 结构/动力学"的交互效应是否显著。
- **创新状态**：unverified

**候选 2：TF–DNA 结合位点"分离度 regime"的量化指标**
- **来源局限/观察**：本文事后归纳了低/中/高分离度 regime，但缺乏先验可计算的分离度指标。
- **核心假设**：类间/类内 embedding 距离比（silhouette score 或 Fisher discriminant ratio）可先验预测模态消融结果。
- **初步方法**：在本文 4 数据集上计算多种分离度指标，回归预测各模态组合的 AUC；在 TF–DNA 数据集上验证指标的可迁移性。
- **验证方式**：指标预测的模态排序与实际消融结果的一致性（rank correlation）。
- **创新状态**：unverified

**候选 3：变构 TF 结合（协同/别构调控）的动力学感知表征**
- **来源局限/观察**：本文发现 MD encoder 增益有限，归因于静态口袋表征；TF–DNA 的别构调控（如协同结合、诱导拟合）本质上依赖构象动力学。
- **核心假设**：MD 导出的 ensemble 特征（如残基波动、构象态分布）能捕捉 TF 别构结合位点，而静态结构不能。
- **初步方法**：对已知别构 TF（如 p53、GR）的 DNA 结合域运行 MD，提取 ensemble embedding，与静态结构 embedding 对比。
- **验证方式**：别构 vs 非别构位点分类的 AUC 提升；MD 特征与实验突变数据的相关性。
- **创新状态**：unverified

**候选 4：跨物种 TF–DNA 结合特异性的模态迁移**
- **来源局限/观察**：本文 Dual-Site 显示合并数据集产生协同效应；TF–DNA 结合特异性在不同物种间保守性不同。
- **核心假设**：序列模态在近缘物种间迁移良好，结构模态在远缘物种间更稳健。
- **初步方法**：构建多物种 TF–DNA 结合数据集，按物种距离分层，测试不同模态组合的跨物种泛化。
- **验证方式**：跨物种 zero-shot 或 few-shot 迁移的 AUC。
- **创新状态**：unverified

**候选 5：物理模拟（MD/对接）与多模态 embedding 的混合模型**
- **来源局限/观察**：本文纯数据驱动，未整合物理模拟；TF–DNA 结合自由能计算（如 MM/PBSA）可提供正交信号。
- **核心假设**：物理模拟导出的能量特征与 embedding 特征互补，尤其在低分离度 regime 下提供 embedding 缺失的判别信号。
- **初步方法**：对 TF–DNA 复合物运行 MD/对接，提取结合自由能、接触面积、氢键数等物理特征，与 embedding 拼接或作为正则化项。
- **验证方式**：与纯 embedding 模型对比的 AUC 提升；物理特征在低分离度数据集上的边际贡献。
- **创新状态**：unverified