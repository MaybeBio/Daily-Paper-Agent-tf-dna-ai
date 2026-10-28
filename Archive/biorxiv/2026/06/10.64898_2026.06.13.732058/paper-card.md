## 01 基本信息

- **标题**：ProtAff: Protein Binding Affinity Prediction via LoRA-Finetuned ESM-2
- **作者**：Lee-Shin Chu; Jeff Vogt; Michael Chungyoun; Jeffrey J. Gray
- **单位**：Johns Hopkins University（Gray Lab，据 GitHub 仓库 Graylab/ProtAff 推断；原文未明确列出单位列表）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（方法学 + 实证评估）
- **领域**：蛋白质-蛋白质结合亲和力预测；蛋白质语言模型；低秩适应（LoRA）；交叉注意力
- **关键词**：binding affinity prediction, ESM-2, LoRA, cross-attention, margin ranking loss, protein-protein interaction, AlphaFold3, Boltz-2
- **DOI/arXiv 号**：10.64898/2026.06.13.732058
- **代码**：https://github.com/Graylab/ProtAff（推理代码、模型权重、测试集）
- **数据**：训练集 362,567 条亲和力测量数据，整合自 AbRank、ASD、PPB-Affinity 三个聚合数据库（覆盖 20 个原始数据源）；测试集为 AdaptyvBio EGFR benchmark（N=55）及 AdaptyvBio Nipah 病毒设计竞赛数据
- **阅读日期**：未提供
- **在「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法/物理模拟」方向中的位置**：本文研究对象为蛋白质-蛋白质相互作用（PPI）的亲和力预测，而非蛋白质-DNA 互作。但其方法框架——基于 ESM-2 蛋白质语言模型的 LoRA 微调 + 交叉注意力 + 排序损失——可直接迁移到 TF–DNA 结合亲和力预测任务。本文的核心发现（结构置信度分数不能反映结合亲和力；序列模型在目标内排序有效但跨目标判别不足；模型可能依赖 binder 组成特征而非靶标条件化互作建模）对 TF–DNA 结合机制研究具有重要警示意义：类似地，结构预测置信度（如 AF3 的 ipTM）可能无法替代结合亲和力排序，且序列模型可能学到 DNA 结合结构域（DBD）的组成性偏差而非真正的靶标序列特异性。

---

## 02 一句话总结

本文提出 ProtAff——一个基于 ESM-2（650M）LoRA 微调 + 交叉注意力 + 边际排序损失的序列-only 亲和力预测模型，在 AdaptyvBio EGFR 基准（N=55）上 Spearman ρ=0.413，显著优于结构置信度分数（最佳 AF3 指标 ρ=0.054）和现有 ML 方法（MINT ρ=0.242，CrossAffinity ρ=0.216），并在 Nipah 病毒 binder 设计竞赛中产出 KD=0.132 nM 的候选（较竞赛冠军强 2.8 倍）；但跨目标判别（91 个 VHH–抗原晶体结构）中仅 2/91 命中，且靶标替换实验表明其排序主要依赖 binder 组成特征而非靶标条件化互作建模。

---

## 03 研究问题

- **具体问题**：能否仅从蛋白质序列预测蛋白质-蛋白质结合亲和力（KD），并在未见过的靶标上实现可靠的亲和力排序？
- **为什么重要**：结合亲和力是理解生物机制和工程化治疗性蛋白（如抗体）的核心量值。结构预测模型（AF3、Boltz-2）的置信度分数虽能评估结构质量，但不能反映结合强弱；传统物理方法（Rosetta flex ddG、FoldX）和统计模型（PRODIGY）依赖实验或预测的复合物结构，限制了在无结构新序列上的应用。
- **现有方法不足**：(1) 结构置信度分数（ipTM、ipSAE、pLDDT）在 AdaptyvBio EGFR 基准上与实验亲和力相关性接近零或为负；(2) 现有 ML 方法（MINT、CrossAffinity）性能有限；(3) 多数方法在随机划分上评估，存在训练-测试序列高相似性问题（如 AbRank benchmark 中测试集与训练集高度重叠）；(4) 跨靶标泛化能力未得到充分检验。
- **精确的「Can ... ?」研究问题**：Can a sequence-only model, trained on heterogeneous affinity data with rigorous train-test separation, rank binding affinity among confirmed binders for a novel target better than structural confidence scores and existing ML-based affinity predictors?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引文与论述整理，标注为「经外部核验」的部分仅指本文引用的外部文献结论，未逐一独立验证。

**阶段一：物理/统计方法**
- 代表：Rosetta flex ddG [8]、FoldX [9]（基于能量函数）；PRODIGY [10]（基于接触统计）。
- 优点：可解释、有物理基础。
- 局限：需要实验或预测的复合物结构；对无结构新序列不适用；计算成本高。

**阶段二：结构预测模型作为代理**
- 代表：AlphaFold3 [1]、Boltz-2 [2]、Chai-1 [3]。
- 优点：结构预测精度高；置信度分数（ipTM、ipSAE）可作筛选工具。
- 局限：Smorodina et al. [5] 显示 AF3 ipTM 与对接质量（DockQ）强相关（r=0.938），但 Overath et al. [6] 的 meta 分析确认这些分数对 binder/non-binder 分类有效，却不能排序结合亲和力。本文在 EGFR 基准上证实所有结构置信度分数与实验亲和力相关性≈0或为负。

**阶段三：序列-based ML 方法**
- 代表：PLM-interact [16]、AntiBinder [17]、PPLM [18]（二分类互作预测）；AlphaBind [19]（大规模预训练亲和力优化）；MINT [22]（STRING 预训练 + 亲和力微调）；CrossAffinity [23]（交叉注意力架构）。
- 优点：无需结构；可扩展至新序列。
- 局限：多数聚焦二分类而非连续亲和力排序；训练-测试划分不严格（AbRank 分析显示高序列相似性泄漏）；跨靶标泛化未验证。

**本文主张的位置**：ProtAff 是首个将 LoRA 微调 + 交叉注意力 + 边际排序损失统一到大规模异构亲和力数据上的序列-only 框架，并系统评估了目标内排序、跨目标判别、靶标依赖性和组成性混淆。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 结构置信度分数不能反映结合亲和力 | AF3/Boltz-2 的 ipTM、ipSAE、pDockQ 等与实验 KD 的 Spearman 相关性≈0或为负 | 置信度分数反映结构可折叠性/对接合理性，而非结合自由能；所有候选都能产生合理构象时无法区分强弱 | Results 节 4.1，Table 1，Supplementary Table S3 |
| 异构数据尺度不兼容 | 训练数据涵盖 KD、IC50、escape ratio 等 20 个数据源，量纲差异大 | 不同实验测定方法报告值不可直接比较，绝对回归损失会受尺度主导 | Methods 节 2.1、2.3 |
| 训练数据靶标严重不均衡 | 5 个靶标占 28 万+样本（77%），大多数靶标样本 <100 | 生物数据库天然偏向少数热点靶标（SARS-CoV-2、PD-1、TIGIT 等） | Methods 节 2.1，Figure 1B |
| 序列模型跨目标判别能力弱 | 91 个 VHH–抗原靶标中仅 2/91 将真配体排到第 1 位 | 序列模型学到 binder 组成特征而非靶标条件化互作；跨靶标时这些特征不具判别力 | Results 节 4.3，Figure 7 |
| 模型对靶标序列不敏感 | 替换为无关靶标序列后排序性能不降反升 | 交叉注意力在靶标侧分布均匀，未聚焦界面残基；模型主要依赖 binder 侧特征 | Results 节 4.4，Figure 8、9 |
| 组成性混淆 | 预测分数与序列长度、疏水性等 binder 组成特征强相关 | 训练集以抗体/设计蛋白为主，这些蛋白的组成特征与亲和力存在虚假相关 | Results 节 4.5，Figure 10 |

---

## 06 核心思想

**1) 表面方法**：
- 用共享的 ESM-2（650M）编码 binder 和 target 序列，对最后 4 层 transformer 的 Q/K/V 投影施加 LoRA 低秩适配（rank=16, α=32）。
- 将 per-residue embedding 投影到 256 维，binder 作为 query、target 作为 key/value 输入两层交叉注意力（8 heads）。
- 交叉注意力输出经注意力池化 + 两层 MLP 头，输出标量亲和力分数。
- 训练目标为边际排序损失（margin ranking loss, m=0.1），仅要求序数正确性，规避异构数据尺度问题。
- 可选加权变体：按样本对间亲和力差值的对数尺度加权。

**2) 核心洞察**：
- **排序优于回归**：异构数据源无法统一到绝对 KD 尺度，但序数关系（哪个 binder 更强）是跨数据源可迁移的监督信号。
- **LoRA 保留预训练知识**：冻结 ESM-2 主干、仅微调低秩适配器，在保留通用蛋白质表征的同时实现任务适应，避免灾难性遗忘。
- **交叉注意力的非对称设计**：binder→target 的单向注意力反映设计任务的不对称性（固定靶标、排序 binder），而非对称的互作建模。
- **严格的数据隔离**：训练集中移除与测试靶标（EGFR）序列相似度 >50% 的样本，避免泄漏。

**3) 可能的普适教训 [Analysis]**：
- 结构置信度 ≠ 结合亲和力：在 TF–DNA 互作中，类似地，结构预测分数（如 AF3 的 ipTM 或 DNA 结合域的 docking score）可能无法排序不同 TF 对同一 DNA 基序的亲和力差异。
- 序列模型容易学到「binder 组成」而非「互作特异性」：在 TF–DNA 场景中，这对应模型可能依赖 TF 的 DBD 类型或 DNA 的 GC 含量等组成特征，而非真正的基序识别。需要靶标替换实验（如将 DNA 序列打乱或替换为无关序列）来检验模型是否真的利用了 DNA 信息。
- 排序损失是处理异构实验数据的通用策略：TF–DNA 结合数据同样来自多种实验（SELEX、HT-SELEX、PBM、ChIP-seq 等），量纲和尺度差异大，排序损失天然适配。

---

## 07 方法总览

**输入**：
- Binder 氨基酸序列（≤1024 残基）
- Target 氨基酸序列（≤1024 残基）

**输出**：
- 标量亲和力分数（相对值，用于排序）

**模块**：
1. **ESM-2 编码器（共享权重）**：分别编码 binder 和 target，输出 per-residue embedding（1280 维）
2. **LoRA 适配器**：仅作用于最后 4 层的 Q/K/V 投影，rank=16, α=32
3. **投影层**：线性层 + LayerNorm，1280→256 维
4. **交叉注意力模块**：2 层、8 heads，binder embedding 作为 query，target embedding 作为 key/value
5. **注意力池化**：单头注意力计算 per-residue 重要性权重，输出固定长度表示
6. **MLP 头**：2 层，输出标量

**训练**：
- 损失：边际排序损失（margin=0.1），可选加权变体
- 优化器：AdamW，线性 warmup（前 10% steps），梯度裁剪 1.0，bf16 混合精度
- 对：intra-target（同靶标不同 binder）和 inter-target（不同靶标）配对
- 采样：cluster-balanced pair sampling（靶标 90% 序列同一性聚类，按几何均值加权，p=0.25）

**数据流**：
```
binder_seq → ESM-2+LoRA → [B, L_b, 1280] → proj → [B, L_b, 256]
target_seq → ESM-2+LoRA → [B, L_t, 1280] → proj → [B, L_t, 256]
                                          ↓
              cross-attn(query=binder, kv=target) → [B, L_b, 256]
                                          ↓
                              attention pooling → [B, 256]
                                          ↓
                                    MLP head → [B, 1]  (affinity score)
```

**验证协议**：
- 验证集：group-based split，验证靶标完全不在训练聚类中
- 测试：AdaptyvBio EGFR benchmark（N=55，EGFR 与训练集 <50% 相似度）

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| ESM-2（650M）共享编码器 | 从序列提取蛋白质表征 | 序列-only 输入；预训练语言模型编码丰富的进化/结构信息 | 输入：binder/target 序列；输出：per-residue embedding [L, 1280] | 预训练模型在蛋白质任务中的通用有效性（引用 [45]） | 预期：无预训练则性能大幅下降 [Analysis]；但本文未做此消融 |
| LoRA 适配器（最后 4 层 Q/K/V） | 参数高效微调 | 避免全量微调的计算成本与灾难性遗忘；保留预训练知识 | 输入：冻结的 Q/K/V 权重；输出：低秩更新后的投影 | Table 1：LoRA 变体 ρ=0.413 vs 冻结 ESM-2 变体 ρ=0.257 | 实测：移除 LoRA（冻结 ESM-2）ρ 从 0.413 降至 0.257（Table 1） |
| 交叉注意力（2 层, 8 heads） | 建模 binder-target 互作 | 使 binder 表征条件化于靶标序列；非对称设计反映设计任务 | 输入：binder proj [L_b, 256] 作为 query，target proj [L_t, 256] 作为 key/value；输出：[L_b, 256] | 交叉注意力优于 naive concatenation（引用 [49]） | 预期：移除后模型退化为 binder-only 打分，跨靶标判别进一步恶化 [Analysis]；本文未做此消融 |
| 注意力池化 | 将变长残基表征压缩为固定长度 | 处理不同长度序列；学习残基重要性权重 | 输入：[L_b, 256]；输出：[256] | Results 节 4.4：binder 侧池化权重富集于界面残基（median enrichment=1.63） | 预期：移除后需用平均池化，可能降低对关键残基的敏感性 [Analysis] |
| 边际排序损失 | 训练序数正确性 | 异构数据源尺度不兼容，绝对回归不可行 | 输入：两个样本对的预测分数与真实序数关系 | Table 1：margin ranking loss 变体 ρ=0.413 vs MSE 回归变体 ρ=0.163 | 实测：替换为 MSE 损失 ρ 从 0.413 降至 0.163（Table 1） |
| Cluster-balanced 采样 | 缓解靶标不均衡 | 5 个靶标占 77% 样本，不校正则模型偏向高频靶标 | 输入：靶标聚类大小；输出：pair 采样权重 | Methods 节 2.4，Supplementary Table S2 | 预期：移除后模型对低频靶标泛化更差 [Analysis]；本文未做此消融 |

---

## 09 关键公式符号

**1) LoRA 前向传播**（Methods 节 2.2）：
\[
h = W_0 x + BAx
\]
- \( W_0 \in \mathbb{R}^{d \times d} \)：冻结的预训练权重矩阵
- \( A \in \mathbb{R}^{r \times d} \)，\( B \in \mathbb{R}^{d \times r} \)：低秩分解矩阵，rank \( r = 16 \)
- \( x \)：输入激活；\( h \)：输出激活
- 初始化：\( A \sim \mathcal{N}(0, \sigma^2) \)，\( B = 0 \)（训练开始时适配器输出为零，不扰动预训练权重）

**2) 边际排序损失**（Methods 节 2.3）：
\[
\mathcal{L} = \max(0, m - (s(x_1) - s(x_2)) \cdot y)
\]
- \( s(x_1), s(x_2) \)：两个 binder-target 对的预测分数
- \( y \in \{-1, +1\} \)：真实序数关系（+1 表示 x₁ 比 x₂ 更强结合）
- \( m = 0.1 \)：边际超参数

**3) 加权变体**（Methods 节 2.3）：
\[
\mathcal{L}_{weighted} = w \cdot \max(0, m - (s(x_1) - s(x_2)) \cdot y)
\]
- \( w = \text{clamp}(|\delta|, 0.1, 5.0) \)
- \( \delta \)：两个 binder 在转换后 log₁₀(KD[nM]) 的绝对差
- 目的：对亲和力差异大的样本对赋予更高权重

**4) Cluster-balanced 采样权重**（Methods 节 2.4）：
\[
w_{pair} = (n_{c_1} \cdot n_{c_2})^{-p}
\]
- \( n_{c_1}, n_{c_2} \)：两个靶标所在 90% 同一性聚类的样本数
- \( p = 0.25 \)：平衡强度参数

**5) NDCG@K**（Methods 节 3.1）：
\[
\text{NDCG@K} = \frac{\text{DCG@K}}{\text{IDCG@K}}, \quad \text{DCG@K} = \sum_{i=1}^{K} \frac{r_{\pi(i)}}{\log_2(i+1)}
\]
- \( \pi(i) \)：预测排名第 i 位的样本
- \( r_{\pi(i)} \)：该样本的 graded relevance（此处为实验 −log₁₀KD）
- IDCG@K：理想排序下的 DCG@K

---

## 10 实验设计与证据链

**数据集/群体**：
- **训练集**：362,567 条亲和力测量，来自 AbRank [14]、ASD [24]、PPB-Affinity [25] 三个聚合数据库，覆盖 20 个原始数据源；308,854 个唯一 binder，10,949 个唯一 target
- **测试集 1（目标内排序）**：AdaptyvBio EGFR benchmark [7]，N=55 单链蛋白 binder（<250 残基），实验测量 KD 对 EGFR；EGFR 与训练集所有 target 序列相似度 <50%
- **测试集 2（跨目标判别）**：Smorodina et al. [5] 的 91 个 VHH–抗原晶体结构，每个 VHH 对 91 个抗原打分，检查真配体排名

**指标**：
- Spearman 秩相关（ρ）——主要指标
- Pearson 相关（R）
- NDCG@K（K=1 至 50）——top-list 排序质量
- Top-1 hit count（跨目标判别）

**基线**：
- 结构方法：AF3 [1] 的 ipSAE、ipTM、pDockQ [50]、pDockQ2 [51]、LIS [52]（多种聚合方式：min/max/mean/median）
- Boltz-2 [2] 的对应指标
- ML 方法：MINT [22]、CrossAffinity [23]

**评测协议**：
- EGFR benchmark：计算预测分数与实验 −log₁₀KD 的 Spearman/Pearson 相关
- 跨目标判别：对每个 target，将 91 个 VHH 的预测分数排序，记录真配体排名；报告 top-1 命中数
- 消融：替换损失函数（margin ranking → MSE）、冻结 ESM-2（移除 LoRA）

**实验表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| EGFR 目标内排序 | ProtAff 优于结构置信度分数和现有 ML 方法 | ProtAff vs AF3/Boltz-2 全部指标 vs MINT/CrossAffinity | ProtAff ρ=0.413；最佳 AF3 指标 ρ=0.054；MINT ρ=0.242；CrossAffinity ρ=0.216 | 序列-only 模型在目标内排序中显著优于结构置信度分数 | 样本量小（N=55），单一靶标，不能推广至所有靶标类型 | Results 节 4.1，Table 1，Figure 4 |
| 损失函数消融 | margin ranking loss 优于 MSE 回归 | margin ranking（ρ=0.413）vs MSE（ρ=0.163） | margin ranking 显著更优 | 排序损失对异构数据至关重要 | 未测试其他排序损失变体（如 ListNet、LambdaRank） | Table 1 |
| LoRA 消融 | LoRA 微调优于冻结 ESM-2 | LoRA（ρ=0.413）vs 冻结（ρ=0.257） | LoRA 显著更优 | 参数高效微调对任务适应必要 | 未与全量微调对比 | Table 1 |
| Nipah 设计竞赛 | ProtAff 辅助设计产出强 binder | 3 阶段 pipeline（采样→过滤→ProtAff 排序）vs 竞赛官方结果 | Top 设计 KD=0.132 nM，较竞赛冠军（KD=0.37 nM）强 2.8 倍 | ProtAff 在实际设计流程中有实用价值 | 仅 5 个设计被实验测试，样本极小；未与其他排序方法在相同 pipeline 下对比 | Results 节 4.2，Figure 6 |
| 跨目标判别 | 序列模型在跨靶标任务中不如结构方法 | AF3（34/91 top-1）vs ProtAff（2/91）vs MINT（0/91）vs CrossAffinity（1/91） | 结构方法显著优于序列方法 | 序列-only 模型缺乏跨靶标特异性判别能力 | 91 个 VHH 均来自同一支架，不代表所有 binder 类型 | Results 节 4.3，Figure 7 |
| 靶标替换 | ProtAff 对靶标序列不敏感 | 替换为 Scrambled EGFR（ρ=0.432）、Most represented（ρ=0.460）、Similar length（ρ=0.510）、Different family（ρ=0.448）、Sparse（ρ=0.209）vs True EGFR（ρ=0.413） | 4/5 替换不降反升；仅 Sparse 下降 | 模型主要依赖 binder 组成特征而非靶标条件化互作 | 替换靶标均为训练集内或随机序列，未测试真实但无关的靶标 | Results 节 4.4，Figure 9 |
| 组成特征相关 | 预测分数与 binder 组成特征相关 | 预测分数 vs 实验 −log₁₀KD 与序列长度、疏水性、净电荷、等电点的 Spearman 相关 | 长度 ρ=0.46（预测）vs 0.16（实验）；疏水性 ρ=−0.37 vs −0.04；净电荷 ρ=−0.37 vs 0.10 | 模型将 binder 组成特征误用作亲和力线索 | 相关分析未控制多变量混淆；N=55 统计功效有限 | Results 节 4.5，Figure 10 |

---

## 11 结论正确解读

- **任务范围**：本文评估的是「目标内亲和力排序」（给定同一靶标，排序不同 binder 的 KD）和「跨目标判别」（给定 binder，识别其同源靶标）。前者 ProtAff 有效，后者无效。
- **oracle/真值输入**：训练数据来自 20 个异构数据源的实验测量，经近似转换到 log₁₀(KD[nM]) 尺度；转换本身有误差，但排序损失缓解了尺度不兼容问题。测试集 EGFR benchmark 为实验测量的 KD。
- **端到端状态**：ProtAff 是端到端的序列→分数模型，不依赖结构预测或对接。但 Nipah 设计 pipeline 中，结构方法（AF3/Boltz-2）仍用于过滤和结构验证，ProtAff 仅替代亲和力排序步骤。
- **算力成本**：原文未提供训练/推理的具体算力成本。ESM-2 650M 为中等规模 PLM，LoRA 微调参数效率高，推理为单次前向传播，成本远低于结构预测+对接。
- **历史数据依赖**：训练数据偏向抗体/设计蛋白和少数热点靶标（SARS-CoV-2、PD-1、TIGIT 等），这直接导致组成性混淆和跨靶标泛化不足。
- **模型依赖**：性能依赖 ESM-2 预训练质量；LoRA 微调优于冻结，但未与全量微调对比。
- **最难情况**：跨靶标判别（91 VHH 对 91 抗原）中序列模型几乎失效；Sparse 靶标（训练样本极少）替换导致性能下降，说明数据覆盖对靶标条件化至关重要。
- **群体/领域边界**：结论仅适用于蛋白质-蛋白质相互作用中的抗体/设计蛋白类 binder。对酶-抑制剂、受体-配体等其它 PPI 类别，以及蛋白质-DNA/RNA 互作，未经验证。
- **不确定性**：EGFR benchmark N=55，统计功效有限；Nipah 设计仅 5 个候选被实验测试；组成性相关分析未做多变量控制。

**有边界的复述**：ProtAff 在「同一靶标内排序候选 binder 亲和力」这一任务上，以序列-only 输入超越了结构置信度分数和现有 ML 基线（ρ=0.413 vs 最佳基线 0.242），并在实际设计流程中产出 KD=0.132 nM 的 binder；但该模型不适用于「跨靶标识别同源互作对」任务（2/91 top-1），且其排序信号主要来自 binder 组成特征而非靶标特异性互作建模，因此其预测不能解释为结合机制层面的理解。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 跨目标判别能力不足 | 91 个 VHH–抗原靶标中仅 2/91 将真配体排到第 1 位，远低于结构方法（AF3 34/91） | 纳入非结合对作为负样本训练；引入对比学习损失显式建模靶标特异性 | Results 节 4.3，Discussion 节 5.4 |
| 靶标条件化不足 | 靶标替换实验显示模型对靶标序列不敏感；交叉注意力在靶标侧分布均匀 | 设计显式强制靶标条件化的训练目标，如靶标打乱负样本 | Results 节 4.4，Discussion 节 5.5 |
| 组成性混淆 | 预测分数与序列长度、疏水性、净电荷等 binder 组成特征强相关 | 在训练数据中平衡 binder 支架多样性；引入去偏技术 | Results 节 4.5，Discussion 节 5.5 |
| 训练数据偏差 | 数据以抗体/设计蛋白为主，5 个靶标占 77% 样本 | 扩展更多靶标家族和 binder 支架类型 | Methods 节 2.1，Discussion 节 5.5 |
| 评估规模有限 | EGFR benchmark 仅 N=55，单一靶标；Nipah 设计仅 5 个候选被实验测试 | 在更多靶标和更大候选集上验证 | Discussion 节 5.3、5.6 |
| 超参数未系统优化 | 未系统变化交叉注意力层数、LoRA rank、LoRA 深度等 | 未来进行系统超参数搜索 | Discussion 节 5.6 |
| 未建模蛋白质表达性和稳定性 | Nipah 设计中 3/5 候选未表达，ProtAff 无法预测此风险 | 集成表达性预测模型 | Discussion 节 5.3 |
| 注意力分析使用 AF3 预测结构而非实验结构 | 界面残基定义依赖 AF3 预测，可能引入偏差 | 使用实验结构验证注意力富集分析 | Discussion 节 5.6 |

---

## 12 作者自认局限（续）

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 异构数据转换近似 | IC50 和 escape ratio 到 KD 的转换是近似的，残余尺度差异仍存在 | 更精细的测定类型建模或元数据利用 | Methods 节 2.1，Discussion 节 5.2 |
| 未验证其它 PPI 类别 | 仅验证了抗体/设计蛋白类 binder，酶-抑制剂、受体-配体等未测试 | 扩展至更多 PPI 类别 | Discussion 节 5.6 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| EGFR benchmark 仅 N=55，单一靶标 | ρ=0.413 的置信区间可能很宽；单一靶标的结果不能代表一般化能力 | 核心结论（优于结构方法）建立在极小样本上 | 在多个靶标（如 HER2、PD-L1、TNF-α）上重复评估；报告 bootstrap 置信区间 | Results 节 4.1 |
| 靶标替换实验中「不降反升」可能反映的是噪声而非鲁棒性 | 替换靶标后 ρ 从 0.413 升至 0.432-0.510，但差异可能不显著；N=55 下 ρ 的标准误约 0.13 | 作者将此解读为「模型不依赖靶标」，但更可能是统计噪声 | 报告替换实验的置信区间；增加 N 或使用置换检验 | Results 节 4.4，Figure 9 |
| 组成特征相关分析未控制多重共线性 | 序列长度、疏水性、净电荷、等电点之间高度相关；单变量相关不能识别独立贡献 | 无法确定哪个组成特征真正驱动预测 | 多元回归或偏相关分析；在控制其他变量后检验各特征的独立贡献 | Results 节 4.5，Figure 10 |
| 与 MINT/CrossAffinity 的对比可能不公平 | 这些基线可能未在相同数据上重新训练或调优；MINT 的预训练数据分布与 ProtAff 训练集不同 | 基线性能差异可能来自训练数据而非架构 | 在相同训练/测试划分下重新训练所有基线；报告每个基线的调优过程 | Results 节 4.1，Table 1 |
| 未报告训练/推理成本 | 无法评估 ProtAff 的实用性与可扩展性 | 实际应用需考虑计算成本 | 报告参数量、训练时间、推理延迟 | 未提供 |
| 注意力富集分析使用 AF3 预测结构 | AF3 预测误差可能系统性影响界面残基定义；且 AF3 本身在 EGFR 亲和力排序上失败，其结构可能不反映结合构象 | 注意力富集结论可能建立在不可靠的结构基础上 | 使用实验结构（如 PDB 中的 EGFR-抗体复合物）重复分析 | Discussion 节 5.6 |
| 排序损失消除了绝对 KD 预测能力 | 模型输出是相对分数，不能直接用于预测 KD 值 | 许多应用场景需要绝对 KD 估计 | 在输出层添加校准头或使用混合损失 | Methods 节 2.3 |
| 训练数据中 5 个靶标占 77% 样本，cluster-balanced 采样仅缓解 pair 层面而非 binder 组成层面偏差 | 即使 pair 采样平衡，binder 支架多样性仍可能不足 | 组成性混淆的根源可能是 binder 序列空间覆盖不足 | 分析训练集中 binder 支架分布；在更均匀的 binder 空间上重新训练 | Methods 节 2.4 |
| 未与全量微调 ESM-2 对比 | LoRA 的优势可能仅在于参数效率，而非性能；全量微调可能更优 | 无法判断 LoRA 是否是性能关键因素 | 增加全量微调基线 | Table 1 |

---

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI/物理模拟」课题方向。

**1. 排序损失是处理异构实验数据的通用策略**
- 来源：Methods 节 2.3，Table 1（margin ranking vs MSE，ρ=0.413 vs 0.163）
- 迁移：TF–DNA 结合数据同样来自多种实验（HT-SELEX、PBM、ChIP-seq、SPR），量纲和尺度差异大。训练 TF–DNA 结合模型时，优先使用排序损失而非回归损失，可规避跨实验的绝对 KD 不可比问题。

**2. LoRA 微调 PLM 是序列-only 亲和力预测的高效范式**
- 来源：Methods 节 2.2，Table 1（LoRA vs 冻结，ρ=0.413 vs 0.257）
- 迁移：对 TF–DNA 结合预测，可用 ESM-2（或 DNA 语言模型如 Nucleotide Transformer）编码 TF 和 DNA 序列，LoRA 微调 + 交叉注意力。DNA 侧可考虑用 k-mer tokenization 或字符级编码，交叉注意力的非对称设计（TF→DNA）可反映 TF 识别 DNA 基序的方向性。

**3. 交叉注意力优于 naive concatenation，但需验证靶标侧注意力是否真正聚焦**
- 来源：Results 节 4.4，Figure 8（靶标侧注意力分布均匀，未聚焦界面）
- 迁移：在 TF–DNA 模型中，应显式检查交叉注意力是否聚焦于 DNA 结合基序（motif）区域。若注意力在 DNA 侧分布均匀，说明模型可能未学到真正的序列特异性识别，需要引入 motif 先验或对比学习约束。

**4. 靶标替换实验是检验「靶标条件化」的关键诊断工具**
- 来源：Results 节 4.4，Figure 9
- 迁移：对 TF–DNA 模型，将 DNA 序列替换为随机序列、打乱序列或无关 TF 的已知基序，观察预测分数是否变化。若排序不随 DNA 序列改变而改变，说明模型退化为 TF-only 打分器，未利用 DNA 信息。

**5. 组成性混淆是序列-only 模型的系统性风险**
- 来源：Results 节 4.5，Figure 10
- 迁移：TF–DNA 训练数据中，不同 TF 家族（如 C2H2、bZIP、homeodomain）的 DNA 结合域长度、电荷、疏水性差异显著，模型可能学到「TF 家族类型」而非「TF-DNA 匹配」。应在训练集中平衡 TF 家族分布，并报告按 TF 家族分层的性能。

**6. 结构置信度分数不能替代亲和力排序**
- 来源：Results 节 4.1，Table 1（AF3/Boltz-2 全部指标 ρ≈0 或负）
- 迁移：在 TF–DNA 场景中，AF3 等结构预测模型的置信度分数（ipTM、pLDDT）可能无法排序不同 TF 对同一 DNA 基序的亲和力。结构方法适合筛选「能否结合」，序列模型适合排序「结合多强」，两者应互补而非替代。

**7. 严格的数据去重（序列相似度截断）是评估泛化能力的必要条件**
- 来源：Methods 节 2.1，Supplementary Figure S1（AbRank 数据泄漏分析）
- 迁移：TF–DNA 数据中，同一 TF 家族的 DNA 结合域高度相似，若不做序列同一性截断，测试集性能会被高估。建议按 TF 序列 50% 同一性聚类划分训练/测试，并报告「新 TF 家族」上的性能。

**8. 跨目标判别任务需要结构信息或显式负样本训练**
- 来源：Results 节 4.3，Figure 7（序列模型 2/91 vs AF3 34/91）
- 迁移：若 TF–DNA 任务需要「给定 TF，从多个 DNA 序列中识别其靶标」，序列-only 模型可能不足。可考虑：(a) 加入非靶标 DNA 作为负样本训练；(b) 结合结构预测或 docking 分数作为辅助特征；(c) 使用对比学习显式拉近同源 TF-DNA 对。

**9. 注意力池化权重可解释模型关注的残基区域**
- 来源：Results 节 4.4，Figure 8（binder 侧池化富集于界面残基）
- 迁移：在 TF–DNA 模型中，可分析池化权重在 TF 序列上的分布，检查是否富集于已知 DNA 结合域（如锌指、螺旋-转角-螺旋基序）。这为模型提供了一种无需结构即可定位关键残基的可解释性工具。

**10. 实际设计 pipeline 中，序列模型与结构过滤互补**
- 来源：Results 节 4.2，Figure 6（ProtAff 排序 + 结构过滤产出 KD=0.132 nM）
- 迁移：TF 工程或合成转录因子设计中，可用序列模型（如 ProtAff 架构）对大量候选进行亲和力排序，再用结构预测（AF3/Docking）过滤不可折叠或无法对接的候选，最后用实验验证少量 top 候选。

---

## 15 与已有知识连接

- **ESM-2 与蛋白质语言模型**：ESM-2 [45] 是当前广泛使用的蛋白质 PLM，本文验证了其在亲和力预测任务中经 LoRA 微调的有效性。与 ESM-1b、ProtTrans 等模型相比，ESM-2 的 per-residue embedding 可直接用于交叉注意力，无需额外结构信息。在 TF–DNA 任务中，可类比使用 ESM-2 编码 TF，DNA 侧可考虑 Nucleotide Transformer、DNABERT-2 等 DNA 语言模型。

- **LoRA 参数高效微调**：LoRA [47] 最初用于大语言模型的高效微调，本文将其应用于蛋白质亲和力预测，验证了低秩适配在保留预训练知识的同时实现任务适应的有效性。与全量微调相比，LoRA 参数量小、训练快，适合资源受限的实验室环境。

- **AlphaFold3 / Boltz-2 结构置信度与亲和力的关系**：Smorodina et al. [5] 和 Overath et al. [6] 分别验证了 AF3 置信度与对接质量和 binder 分类的关系。本文进一步证明这些分数不能排序亲和力，与 King et al. [59] 的独立结论一致。这提示在 TF–DNA 领域，AF3 的 DNA-蛋白复合物置信度分数同样可能无法反映结合强度，需要专门的亲和力模型。

- **边际排序损失**：排序损失在信息检索（RankNet、LambdaRank）和对比学习（InfoNCE）中有广泛应用。AbRank [14] 首次将其用于抗体亲和力预测，本文扩展了其适用性并验证了加权变体的效果。在 TF–DNA 数据中，排序损失可天然适配 SELEX 富集比、PBM 荧光强度等相对量。

- **交叉注意力在 PPI 预测中的应用**：CrossAttention [48] 在蛋白质-蛋白质相互作用预测中已有应用，本文验证了其在亲和力排序中的有效性，并发现其靶标侧注意力分布均匀的问题。在 TF–DNA 中，可参考 DNA-蛋白质交叉注意力模型（如 CBPBind、DeepZF）的设计，但需注意 DNA 序列的 k-mer 编码和反向互补链处理。

- **组成性混淆与数据偏差**：本文发现的 binder 组成特征混淆问题，与机器学习中「shortcut learning」和「dataset bias」文献一致。在 TF–DNA 数据中，类似风险存在于 TF 家族不平衡（C2H2 占多数）和 DNA 基序 GC 含量偏差。可参考去偏技术（如 reweighting、adversarial debiasing）进行缓解。

- **靶标替换实验**：本文的靶标替换实验设计（scrambled、most represented、similar length、different family、sparse）是一种系统性的「靶标条件化」检验方法，可类比于 NLP 中的「敏感性分析」和「对抗扰动」。在 TF–DNA 模型中，可设计 DNA 序列替换实验（随机 DNA、打乱基序、替换为无关 TF 基序）来检验模型是否真正利用了 DNA 信息。

- **设计竞赛验证**：AdaptyvBio 竞赛平台提供了标准化的实验验证环境，本文的 Nipah binder 设计案例展示了「序列模型排序 + 实验验证」的闭环流程。在 TF 工程领域，类似的可参考平台包括合成启动子设计竞赛和 CRISPR 筛选平台。

---

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI/物理模拟」课题方向。

**候选 1：TF-DNA 亲和力排序模型（ProtAff-TF）**
- **名称**：ProtAff-TF：基于 LoRA 微调 ESM-2 + DNA 编码器的 TF-DNA 结合亲和力排序模型
- **来源局限/观察**：ProtAff 在蛋白质-蛋白质亲和力排序中有效，但跨靶标判别不足；TF-DNA 数据同样异构（SELEX、PBM、ChIP-seq），且 DNA 侧编码需要特殊处理
- **核心假设**：将 ProtAff 的「binder→target 交叉注意力」框架迁移为「TF→DNA 交叉注意力」，配合排序损失，可在 TF-DNA 目标内排序任务中超越现有方法
- **初步方法**：TF 序列用 ESM-2+LoRA 编码，DNA 序列用 k-mer tokenization + DNA 语言模型（如 Nucleotide Transformer）编码；交叉注意力以 TF 为 query、DNA 为 key/value；训练目标为边际排序损失；在 SELEX 富集比和 PBM 荧光强度数据上评估
- **验证方式**：与现有 TF-DNA 亲和力预测器（如 DeepSELEX、FactorNet）对比；在多个 TF 家族上分层报告 Spearman ρ；靶标替换实验检验 DNA 条件化
- **创新状态**：unverified

**候选 2：靶标条件化诊断协议**
- **名称**：TF-DNA 模型的靶标条件化诊断协议（Target-Conditioning Probe）
- **来源局限/观察**：ProtAff 的靶标替换实验揭示了模型对靶标不敏感的问题；TF-DNA 模型可能同样存在「TF 家族 shortcut」
- **核心假设**：通过系统性的 DNA 替换实验（随机 DNA、打乱基序、替换为无关 TF 基序、同长度 GC 匹配对照），可以量化 TF-DNA 模型对 DNA 序列信息的真实依赖程度
- **初步方法**：设计标准化的 DNA 替换协议，计算「条件化分数」（真实 DNA 排序 vs 替换 DNA 排序的 Spearman 差异）；在多个公开 TF-DNA 模型上运行，建立基准
- **验证方式**：条件化分数与模型在独立测试集上的泛化能力之间的相关性；与 motif 富集分析结果对比
- **创新状态**：unverified

**候选 3：结构-序列混合亲和力模型**
- **名称**：结构感知的 TF-DNA 亲和力排序（Structure-Aware TF-DNA Affinity Ranking）
- **来源局限/观察**：ProtAff 证明序列模型在目标内排序中优于结构置信度分数，但跨靶标判别不足；结构方法（AF3）在跨靶标中占优但无法排序亲和力
- **核心假设**：将序列模型的亲和力排序能力与结构模型的特异性识别能力结合，可同时提升目标内排序和跨靶标判别
- **初步方法**：双塔架构——序列塔（ESM-2+LoRA+交叉注意力）输出亲和力分数，结构塔（AF3 或 Boltz-2 的 ipTM/界面残基特征）输出特异性分数；融合层学习两者权重；在 TF-DNA 数据集上联合训练
- **验证方式**：与纯序列模型和纯结构方法对比；在跨 TF 家族和跨 DNA 基序上分层评估
- **创新状态**：unverified

**候选 4：DNA 侧注意力可解释性分析**
- **名称**：TF-DNA 交叉注意力的基序定位能力分析
- **来源局限/观察**：ProtAff 的 binder 侧注意力池化富集于界面残基，但靶标侧注意力分布均匀；TF-DNA 模型中 DNA 侧注意力是否聚焦于已知基序是模型质量的关键指标
- **核心假设**：若 TF-DNA 交叉注意力在 DNA 侧聚焦于已知结合基序（如 JASPAR 注释的 motif），则模型学到了真正的序列特异性识别；否则需要引入 motif 先验
- **初步方法**：在训练好的 TF-DNA 模型上，对每个测试 DNA 序列计算注意力权重分布；与已知 motif 位置计算富集分数（如 AUC 或 Jensen-Shannon 散度）；对比随机初始化和有监督训练的模型
- **验证方式**：注意力富集分数与模型排序性能的相关性；motif 置换实验（将 motif 替换为随机序列后预测分数变化）
- **创新状态**：unverified

**候选 5：TF 家族平衡训练策略**
- **名称**：去偏 TF-DNA 训练：缓解 TF 家族不平衡导致的组成性混淆
- **来源局限/观察**：ProtAff 的组成性混淆源于训练数据中抗体/设计蛋白占主导；TF-DNA 数据中 C2H2 锌指家族占多数，可能导致模型学到「TF 家族类型」而非「TF-DNA 匹配」
- **核心假设**：通过 TF 家族平衡采样和去偏正则化，可减少组成性混淆，提升跨家族泛化
- **初步方法**：按 TF 家族分层采样；在损失函数中加入对抗性去偏项（预测 TF 家族并惩罚其与亲和力分数的互信息）；在保留的 TF 家族上评估
- **验证方式**：与基线模型在「新 TF 家族」上的性能对比；组成特征与预测分数的偏相关分析
- **创新状态**：unverified

**候选 6：DNA 语言模型 vs 传统编码的消融**
- **名称**：DNA 编码方式对 TF-DNA 亲和力预测的影响
- **来源局限/观察**：ProtAff 仅处理蛋白质序列；TF-DNA 任务需要同时编码 DNA，DNA 的编码方式（one-hot、k-mer、DNA 语言模型）可能显著影响性能
- **核心假设**：DNA 语言模型（如 Nucleotide Transformer）的预训练表示优于传统 one-hot 或 k-mer 编码，尤其在数据稀疏的 TF 家族上
- **初步方法**：固定 TF 编码（ESM-2+LoRA）和训练目标（排序损失），仅变化 DNA 编码方式；在相同数据划分下对比 Spearman ρ 和跨靶标判别
- **验证方式**：多组随机种子下的性能差异显著性检验；在低数据 TF 家族上的分层表现
- **创新状态**：unverified

**候选 7：TF-DNA 设计 pipeline 验证**
- **名称**：基于序列亲和力排序的合成转录因子设计 pipeline
- **来源局限/观察**：ProtAff 在 Nipah binder 设计中产出 KD=0.132 nM 的 binder，验证了「序列排序 + 实验验证」的闭环；类似策略可迁移至 TF 工程
- **核心假设**：用 TF-DNA 亲和力排序模型筛选合成 TF 变体库，可显著提高实验验证命中率
- **初步方法**：从已知 TF（如锌指阵列）出发，生成突变库 → 用 TF-DNA 模型排序 → top-K 用 SPR/EMSA 验证 KD → 与随机筛选对比命中率
- **验证方式**：命中率提升的统计显著性；模型排序与实验 KD 的 Spearman 相关性
- **创新状态**：unverified