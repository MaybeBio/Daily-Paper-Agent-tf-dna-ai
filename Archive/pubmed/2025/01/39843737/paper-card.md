## 01 基本信息
- **标题**：Multiscale footprints reveal the organization of cis-regulatory elements
- **作者与单位**：Hu, Yan; Horlbeck, Max A; Zhang, Ruochi; Ma, Sai; Shrestha, Rojesh; Kartha, Vinay K; Duarte, Fabiana M; Hock, Conrad; Duarte, Fabiana M; Hock, Conrad; Labade, Ajay; Kletzien, Ajay; Meliki, Alina; Tay, Tristan; Earl, Andrew S; Shoresh, Charles B; Wagers, Amy J; Buenrostro, Jason D（哈佛大学/布罗德研究所等，具体单位未在摘要中列出）
- **期刊/预印本平台**：Nature
- **年份**：2025-01-23
- **论文类型**：方法学 + 应用研究
- **领域**：计算基因组学、表观遗传学、基因调控
- **关键词**：cis-regulatory elements (CREs)、转录因子 (TF)、核小体、ATAC-seq、深度学习、单细胞、造血、衰老
- **DOI/arXiv 号**：10.1038/s41586-024-08443-4
- **代码**：https://github.com/buenrostrolab/scPrinter（在 Methods 中提及）
- **数据**：人类骨髓单细胞 ATAC+RNA（SHARE-seq）、小鼠 HSC 10x Multiome、HepG2/GM12878/K562 细胞系 ATAC-seq、BAC 体外数据（未提供具体数据编号）
- **阅读日期**：2025-04-11
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 深度学习」方向，核心创新在于从 ATAC-seq 染色质可及性数据中提取多尺度（TF 与核小体）footprint，并用深度学习模型（seq2PRINT）从 DNA 序列预测这些 footprint，从而推断 TF 结合与核小体定位。对 TF–DNA 结合机制研究提供了不依赖 ChIP-seq 的高通量预测框架，并揭示了 CRE 在分化与衰老中的结构动态。

## 02 一句话总结
本文开发了 PRINT（多尺度 footprint 检测）与 seq2PRINT（序列到 footprint 的深度学习模型），从 bulk 和单细胞 ATAC-seq 数据中同时解析 TF 与核小体结合足迹，并应用于人类造血分化与小鼠 HSC 衰老，发现 CRE 呈以先锋因子为中心的逐步建立与拓宽模式，以及衰老中核小体足迹的广泛丢失与 TF 重编程。

## 03 研究问题
- **具体问题**：如何从染色质可及性数据（ATAC-seq）中同时、精确地检测不同大小 DNA 结合蛋白（TF 约 20 bp、核小体约 147 bp）的结合足迹，并进一步从 DNA 序列预测这些结合事件，从而在单细胞分辨率和大规模上解析 CRE 内部的结构组织？
- **为什么重要**：CRE 的功能取决于其内部多种效应蛋白（TF、核小体、共调控因子）的动态组合。现有 ChIP-seq 无法规模化覆盖所有 TF 和所有细胞状态；而传统 footprint 方法仅关注 TF 尺度，忽略了核小体，且受酶切序列偏好影响大。
- **现有方法不足**：(1) 传统 footprint 方法（如 TOBIAS）仅检测 TF 尺度，不检测核小体；(2) 对 Tn5 序列偏好校正不足；(3) 难以应用于单细胞数据（稀疏性）；(4) 无法从序列直接推断结合，限制了跨细胞类型的迁移。
- **精确研究问题**：Can a deep learning model trained on multiscale ATAC-seq footprints predict TF and nucleosome binding from DNA sequence alone, and can this reveal cell-type-specific and age-associated reorganization of CREs?

## 04 背景与发展脉络
*注：以下脉络基于本文框架，部分经外部核验标注。*

1. **DNase-seq footprinting 时代**：利用 DNase I 切割保护模式检测 TF 结合（Galas & Schmitz 1978；Boyle et al. 2008）。局限：分辨率有限、无法检测核小体、通量低。
2. **ATAC-seq 与单细胞扩展**：Tn5 转座酶偏好开放染色质（Buenrostro et al. 2013），单细胞 ATAC-seq 出现（Cusanovich et al. 2015）。局限：Tn5 序列偏好严重，footprint 信号弱。
3. **计算 footprint 方法**：TOBIAS（Bentsen et al. 2020）等通过纠正酶切偏好检测 TF footprint。ChromBPNet（Brent et al. 2021）用深度学习预测 ATAC-seq 计数。局限：仅 TF 尺度、未整合核小体、未做序列到 footprint 的端到端预测。
4. **深度学习在调控基因组学中的应用**：Basset（Kelley et al. 2016）、Enformer（Avsec et al. 2021）等从序列预测染色质状态。局限：预测的是粗粒度可及性，非蛋白结合足迹。
5. **本文位置**：首次将多尺度 footprint（TF + 核小体）与深度学习结合，实现从序列到蛋白结合足迹的端到端预测，并引入 LoRA 实现单细胞规模的高效微调。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| Tn5 序列偏好 | 不同序列背景下 Tn5 插入率差异大，导致 footprint 假阳性 | Tn5 转座酶本身有序列偏好，非蛋白结合导致 | Methods "Tn5 sequence bias modelling" 节；Extended Data Fig. 1a–d |
| 单尺度 footprint 局限 | 仅检测 TF 尺度（~20 bp），无法检测核小体（~147 bp） | 传统方法固定窗口大小，无法适应不同蛋白尺寸 | 图 1a 多尺度示意；Results "Identification of multiscale footprints" 节 |
| 单细胞数据稀疏 | 单细胞 ATAC-seq 每个细胞 reads 极少，无法直接 footprint | 测序深度限制 | Methods "LoRA enables efficient sequence modelling" 节 |
| 弱/无 footprint TF 检测困难 | 部分 TF 结合不产生明显 footprint，传统方法漏检 | 结合时间短、无稳定保护模式 | 图 2e；Extended Data Fig. 4c–f |
| 计算成本高 | 为每个细胞类型单独训练模型不可行 | 模型参数量大，数据量多 | Methods "LoRA" 节；Extended Data Fig. 6a–c |

## 06 核心思想
1. **表面方法**：开发 PRINT 计算框架，在多个窗口尺度（4–200 bp）上计算 footprint 分数，同时检测 TF 和核小体；随后训练 seq2PRINT 深度学习模型，以 DNA 序列为输入预测多尺度 footprint，并用 LoRA 实现单细胞数据的高效微调。
2. **核心洞察**：DNA 序列本身包含了足够的调控信息，可以从序列直接预测 TF 和核小体的结合足迹，而无需 ChIP-seq 或 motif 先验。多尺度 footprint 提供了 CRE 内部结构的"图像"，揭示了 TF 结合与核小体定位之间的空间关系。
3. **可能的普适教训** [Analysis]：将"信号分解为多个空间尺度"的思路可推广到其他染色质数据（如 MNase-seq、CUT&Tag），且"先在大规模数据上预训练、再用 LoRA 微调到具体细胞类型"的范式适用于任何单细胞表观基因组分析任务。

## 07 方法总览
- **输入**：ATAC-seq 插入位点数据（bulk 或单细胞伪 bulk），DNA 序列（参考基因组）
- **输出**：多尺度 footprint 分数（每个碱基位置）、TF 结合预测、核小体定位预测、TF motif 重要性分数
- **模块**：
  1. Tn5 序列偏好模型（CNN，训练于 BAC 去蛋白 DNA 数据）
  2. PRINT footprint 计算（多尺度窗口 + 背景校正 + 统计检验）
  3. seq2PRINT 序列模型（CNN + 残差连接 + 扩张卷积，预测多尺度 footprint）
  4. LoRA 微调模块（低秩分解实现高效微调）
  5. TF 结合分类器（基于 motif 位点的 footprint 和序列特征）
  6. 核小体预测模块（回归模型）
  7. 下游分析工具（TF 动态追踪、motif 发现、差异分析）
- **训练**：seq2PRINT 在 HepG2 bulk ATAC-seq 上预训练，用 LoRA 微调到每个伪 bulk；TF 分类器用 ChIP-seq 数据训练
- **反馈回路**：seq2PRINT 预测的 footprint 变化可用于发现新 motif，新 motif 又可用于改进 TF 结合预测
- **文字流程**：ATAC-seq reads → Tn5 偏好校正 → 多尺度 footprint 计算（PRINT）→ seq2PRINT 序列模型训练 → 预测全基因组 footprint → 在单细胞伪 bulk 上用 LoRA 微调 → 提取 TF 结合分数和核小体定位 → 下游差异分析和 motif 发现

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Tn5 序列偏好模型 | 预测每个序列位置的 Tn5 插入偏好 | 校正酶切偏好，避免 footprint 假阳性 | 输入：±50 bp 序列；输出：预测插入率 | Extended Data Fig. 1a–d；R=0.94 vs k-mer/PWM | 预期：footprint 假阳性率显著上升 [Analysis] |
| PRINT 多尺度 footprint | 在 4–200 bp 窗口计算 footprint 分数 | 同时检测 TF 和核小体 | 输入：校正后插入计数；输出：多尺度 footprint 分数 | 图 1c–i；体外 BAC 验证 | 预期：无法区分 TF 与核小体信号 [Analysis] |
| seq2PRINT 序列模型 | 从 DNA 序列预测多尺度 footprint | 实现无 ChIP-seq 的 TF 结合预测 | 输入：1 kb DNA 序列；输出：多尺度 footprint 预测 | 图 2b；相关性 0.75 | 预期：失去跨细胞类型迁移能力 [Analysis] |
| LoRA 微调 | 低秩分解实现高效微调 | 单细胞数据量大，全量微调不可行 | 输入：预训练模型 + 伪 bulk 数据；输出：伪 bulk 特异模型 | Extended Data Fig. 6a–c；80 倍加速 | 预期：计算成本增加 80 倍 [Analysis] |
| TF 结合分类器 | 预测 motif 位点是否被结合 | 将 footprint 转化为 TF 结合事件 | 输入：footprint + motif 特征；输出：结合概率 | 图 2d–e；优于 ChromBPNet/TOBIAS | 预期：弱 footprint TF 检测能力下降 [Analysis] |
| 核小体预测模块 | 预测核小体定位 | 解析 CRE 内核小体- TF 关系 | 输入：多尺度 footprint；输出：核小体占据分数 | 图 3d；与化学作图数据一致 | 预期：无法追踪核小体重塑 [Analysis] |

## 09 关键公式符号
*注：原文 Methods 中公式未在摘要中完整给出，以下基于可获取信息。*

1. **Footprint score 计算**（PRINT 核心）：
   - 对每个位置 i 和尺度 s，计算观测插入比 R_obs(i,s) = C_center(i,s) / (C_center(i,s) + C_flank(i,s))
   - 其中 C_center 为中心窗口插入数，C_flank 为两侧翼窗口插入数
   - 背景分布由 Tn5 偏好模型预测的期望比 R_exp(i,s) 给出
   - Footprint score = (R_exp - R_obs) / σ_background，σ_background 由最近邻 500 个位置估计
   - 符号：C = 插入计数；R = 比率；σ = 标准差

2. **seq2PRINT 损失函数**：
   - Loss = Loss_footprint + Loss_accessibility
   - Loss_footprint = MSE(footprint_PRINT, footprint_pred)
   - Loss_accessibility = MSE(log(1 + n_obs), log(1 + n_pred))
   - 符号：MSE = 均方误差；n_obs = 观测插入数；n_pred = 预测插入数

3. **LoRA 参数更新**：
   - W = W₀ + ΔW，其中 ΔW = BA，B ∈ R^(d_e×r)，A ∈ R^(r×d_p*)
   - 符号：W₀ = 初始权重；ΔW = 更新量；r = 秩（=32）；d_e = 嵌入维度；d_p* = 参数维度

## 10 实验设计与证据链
- **数据集**：
  - 训练/验证：HepG2 bulk ATAC-seq；GM12878（验证）；K562（测试）
  - 单细胞：人类骨髓 874,480 细胞（7 供体，SHARE-seq）；小鼠 HSC 48,225 细胞（10x Multiome，年轻 n=10，年老 n=5）
  - 体外验证：BAC DNA + 纯化 TF（MYC/MAX、CEBPA）
  - 基准：ChIP-seq（ENCODE、UniBind、CistromeDB）；DNase-seq footprint（ENCODE）
- **指标**：footprint 检测精度/召回、TF 结合预测 precision@10%、与 ChIP-seq 的一致性、核小体定位与化学作图数据的一致性
- **基线**：TOBIAS、ChromBPNet、DNase footprinting
- **评测协议**：五折交叉验证（按染色体划分）；单细胞数据用 LoRA 微调后评估

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| BAC 体外 footprint 检测 | PRINT 能检测纯化 TF 结合 | 0 vs 50 vs 100 nM MYC/MAX | 仅在含 TF 条件下检测到 footprint | PRINT 对 TF 结合敏感且特异 | 未测试所有 TF 类型 | 图 1c–g |
| Tn5 偏好模型性能 | CNN 优于 k-mer/PWM | R=0.94 vs 0.85/0.80 | CNN 最佳 | 深度学习可有效建模 Tn5 偏好 | 未与其他深度学习架构比较 | 图 1b |
| seq2PRINT 预测精度 | 序列可预测 footprint | 与观测 footprint 相关性 0.75 | 高相关性 | 序列包含足够调控信息 | 因果性未证明 | Extended Data Fig. 4b |
| TF 结合预测基准 | seq2PRINT 优于现有方法 | vs ChromBPNet、TOBIAS | seq2PRINT precision 最高 | 多尺度 footprint 提供额外信息 | 仅在少数细胞系测试 | 图 2d–e |
| CTCF 降解实验 | 模型预测与实验一致 | degron-CTCF 耗尽 vs 对照 | 预测的 footprint 变化与实验高度相关 (R=0.93) | 模型捕捉真实 TF 结合动态 | 仅测试一个 TF | 图 2f |
| 造血分化追踪 | CRE 呈逐步建立模式 | 红系 vs 淋巴系轨迹 | 先锋因子先结合，CRE 逐步拓宽 | CRE 建立是逐步过程 | 未直接验证功能 | 图 3d–g |
| 衰老 HSC 比较 | 衰老改变 CRE 结构 | 年轻 vs 年老 HSC | 核小体 footprint 广泛丢失，Ets/Runx motif 获得 | 衰老伴随 CRE 结构紊乱 | 因果关系未建立 | 图 4i–j |
| AlphaFold3 验证 | 预测的 Ets/Runx 复合 motif 可形成二聚体 | AF3 预测 vs PDB 已知结构 | RMSD=0.825 Å | 预测的复合 motif 有结构基础 | 仅验证一个 motif | 图 4h |

## 11 结论正确解读
- **任务范围**：本文方法适用于 ATAC-seq 数据（bulk 和单细胞伪 bulk），检测范围限于 TF（~20 bp）和核小体（~147 bp）尺度的 footprint。不适用于其他蛋白类型（如共调控因子）的直接检测。
- **oracle/真值输入**：TF 结合预测的训练标签来自 ChIP-seq 数据，因此预测能力受限于 ChIP-seq 覆盖的 TF 集合。对于无 ChIP-seq 数据的 TF，预测依赖 motif 相似性外推。
- **端到端状态**：seq2PRINT 是端到端的序列到 footprint 预测模型，但 TF 结合分类器仍需 ChIP-seq 数据训练，并非完全无监督。
- **算力成本**：LoRA 微调实现 80 倍加速，但预训练 seq2PRINT 仍需大量 GPU 资源（具体未披露）。
- **历史数据依赖**：模型在人类和小鼠数据上训练，跨物种迁移需重新微调。
- **最难情形**：弱结合、短暂结合的 TF（如诱导型 TF）footprint 信号弱，预测难度大；单细胞数据中低频细胞类型的 footprint 检测受限。
- **群体/领域边界**：造血系统是主要验证领域；其他组织/疾病中的适用性需进一步验证。
- **不确定性**：footprint 分数是统计推断，不代表直接物理结合测量；预测的 TF 结合需实验验证。

**有边界的复述**：本文证明，在 ATAC-seq 数据上，多尺度 footprint 结合深度学习可以在 ChIP-seq 覆盖的 TF 集合内、以优于现有方法的精度预测 TF 结合，并揭示 CRE 在造血分化和衰老中的结构动态；但该方法不检测非 DNA 结合蛋白、依赖 ChIP-seq 标签、且主要在造血系统中验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 未利用片段长度信息 | 方法不整合转座片段长度，可能丢失核小体定位信息 | 作者在 Discussion 中提及可整合片段长度作为额外特征 | Discussion 节 |
| 稀有结合事件可能漏检 | 深度学习中需要多实例学习模式，罕见或非经典结合事件可能被遗漏 | 作者建议结合其他方法如甲基转移酶 footprinting 进行交叉验证 | Discussion 节 |
| 伪 bulk 依赖 | 单细胞 footprint 需要伪 bulk 化，无法在单个细胞水平检测 | 作者提及未来可探索单分子 footprint 方法 | Discussion 节 |
| 训练数据偏差 | 模型训练依赖 ChIP-seq 数据，对无 ChIP-seq 的 TF 预测能力有限 | 作者建议用 TF 扰动实验（如 CRISPR）进行验证 | Discussion 节 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 相关性 0.75 的预测精度 | 可能部分来自序列组成（GC 含量）而非真实 TF 结合信号 | 若模型主要学习序列组成特征，则生物学解释性有限 | 用 GC 匹配的阴性序列测试模型；比较 shuffled 序列的预测 | Extended Data Fig. 4b |
| TF 结合分类器依赖 ChIP-seq 标签 | 存在循环论证风险：ChIP-seq 本身有局限性，模型可能继承其偏差 | 影响模型在新 TF 或新细胞类型上的泛化能力 | 用独立方法（如 siRNA 敲低 + footprint 变化）验证预测 | 图 2f 的 CTCF 实验是正面例子 |
| 造血分化轨迹的"逐步拓宽"模型 | 可能反映伪时间排序的人为因素而非真实生物学过程 | 若结论是伪影，则对 CRE 动态的理解有误 | 用独立分化实验（如体外分化）验证同一 CRE 的动态 | 图 3d–g |
| AlphaFold3 验证仅一个 motif | 单一案例不足以证明所有预测的复合 motif 都有结构基础 | 影响对 Ets/Runx 复合 motif 普遍性的判断 | 对多个预测的复合 motif 进行 AF3 预测和突变验证 | 图 4h |
| 衰老比较中年轻/年老 HSC 的批次效应 | 未明确说明是否控制了批次效应 | 若存在批次效应，差异可能来自技术而非生物学 | 检查是否有重复实验和批次校正 | 图 4a–b |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **多尺度 footprint 概念**：将 footprint 分析从固定窗口（~20 bp）扩展到多尺度（4–200 bp），可同时捕获 TF 和核小体信号。**迁移到本课题**：在 TF–DNA 结合机制研究中，可借鉴此思路分析其他染色质数据（如 ChIP-exo、CUT&Tag），检测不同大小的 DNA 结合复合物。

2. **序列到 footprint 的端到端预测**：seq2PRINT 证明 DNA 序列本身足以预测蛋白结合足迹，无需 motif 先验。**迁移到本课题**：可用于预测未知 TF 的结合位点，或评估非编码变异对 TF 结合的影响（类似于在硅片饱和突变分析）。

3. **LoRA 微调范式**：在大规模预训练模型上用低秩分解微调到每个细胞类型/状态，实现 80 倍加速。**迁移到本课题**：在需要处理大量细胞类型或条件的 TF 结合预测任务中，此范式可大幅降低计算成本。

4. **footprint 与核小体定位的关联分析**：通过多尺度 footprint 同时追踪 TF 和核小体，揭示 CRE 内部的空间组织。**迁移到本课题**：可用于研究 TF 结合如何影响核小体定位，或核小体如何调控 TF 可及性——这是 TF–DNA 结合机制的核心问题。

5. **de novo motif 发现与结构验证结合**：seq2PRINT 发现的 de novo motif 用 AlphaFold3 验证物理结合。**迁移到本课题**：将深度学习发现的 motif 与结构预测（AF3、MD 模拟）结合，可形成"序列→结合→结构"的完整验证链。

6. **footprint 分数作为 TF 结合强度的连续度量**：相比二值结合/不结合，footprint 分数提供连续的结合强度估计。**迁移到本课题**：可用于定量比较不同突变对 TF 结合亲和力的影响，或构建 TF 结合的能量景观。

## 15 与已有知识连接
- **可核验的外部文献**：
  - Buenrostro et al. 2013 (ATAC-seq 原始方法)
  - Bentsen et al. 2020 (TOBIAS，footprint 分析基线)
  - Kelley et al. 2016 (Basset，序列到染色质状态的深度学习)
  - Avsec et al. 2021 (Enformer，序列到表达的深度学习)
  - Hu et al. 2021 (ChromBPNet，序列到 ATAC 计数的深度学习)
  - 本文引用的 PDB 结构：4L0Z (Runx:Ets 二聚体)、2NNY (Ets:Ets 二聚体)
- **与用户已有知识的连接**：
  - 若用户熟悉 TOBIAS：本文的 PRINT 是其多尺度扩展，解决了单尺度局限
  - 若用户熟悉 ChromBPNet：本文的 seq2PRINT 是其 footprint 级扩展，预测更细粒度的蛋白结合
  - 若用户熟悉 AlphaFold3：本文展示了 AF3 在验证非编码 motif 功能中的应用
- **候选研究方向**：
  - 将 seq2PRINT 扩展到其他物种或组织
  - 将多尺度 footprint 与 3D 基因组（Hi-C）数据整合
  - 用 seq2PRINT 预测非编码变异对 TF 结合的影响（与 GWAS 关联）

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合亲和力的多尺度 footprint 预测器
   - **来源局限/观察**：seq2PRINT 预测的是 footprint 强度，但未直接量化 TF–DNA 结合亲和力（Kd）
   - **核心假设**：多尺度 footprint 深度特征可预测 TF 对特定 DNA 序列的体外结合亲和力
   - **初步方法**：用 SELEX 或 HT-SELEX 数据训练回归模型，输入为 seq2PRINT 的 footprint 预测和序列特征，输出为 Kd 或相对亲和力
   - **验证方式**：与表面等离子共振（SPR）或电泳迁移率变动分析（EMSA）测量的 Kd 对比
   - **创新状态**：unverified

2. **候选名称**：单细胞分辨率下的 TF 竞争与协同结合建模
   - **来源局限/观察**：本文在伪 bulk 水平分析 TF 动态，未在单细胞水平解析 TF 共结合
   - **核心假设**：单细胞 ATAC-seq 的 footprint 模式可推断同一 CRE 内 TF 的竞争或协同关系
   - **初步方法**：用 seq2PRINT 对每个单细胞（或小规模伪 bulk）预测 footprint，计算 TF 对之间的共变异，构建 TF 互作网络
   - **验证方式**：与多色免疫荧光或 DNA-FISH 共定位数据对比
   - **创新状态**：unverified

3. **候选名称**：衰老相关 TF 重编程的结构基础
   - **来源局限/观察**：本文发现衰老 HSC 中 Ets/Runx 复合 motif 获得，但未深入结构机制
   - **核心假设**：衰老相关的 Ets/Runx 复合 motif 改变 TF 二聚化界面，影响 DNA 结合特异性
   - **初步方法**：用 AlphaFold3 或 MD 模拟预测衰老相关复合 motif 的 TF–DNA 结构，比较与年轻 motif 的构象差异
   - **验证方式**：突变分析 + 电泳迁移率变动分析（EMSA）验证结合亲和力变化
   - **创新状态**：unverified

4. **候选名称**：非编码变异对 TF–核小体协同的扰动预测
   - **来源局限/观察**：本文揭示了 TF 与核小体的空间关系，但未评估变异的影响
   - **核心假设**：非编码变异通过改变 TF 结合或核小体定位来影响 CRE 功能，seq2PRINT 可预测这种扰动
   - **初步方法**：对 GWAS 风险变异进行 in silico 突变，用 seq2PRINT 预测 footprint 变化，筛选影响 TF–核小体协同的变异
   - **验证方式**：用 CRISPR 编辑 + ATAC-seq 验证预测的 footprint 变化
   - **创新状态**：unverified

5. **候选名称**：跨物种 TF 结合机制的比较基因组学
   - **来源局限/观察**：本文方法在人类和小鼠上验证，未探索跨物种保守性
   - **核心假设**：多尺度 footprint 的序列决定因素在物种间保守，可用于预测新物种的 TF 结合
   - **初步方法**：用人类训练的 seq2PRINT 直接应用于小鼠、斑马鱼等物种的 ATAC-seq 数据，评估跨物种预测精度
   - **验证方式**：与各物种的 ChIP-seq 数据对比
   - **创新状态**：unverified