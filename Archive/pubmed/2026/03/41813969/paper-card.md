## 01 基本信息
- **标题**：De novo design of functional nucleic acids of aptamers
- **作者**：Zhang, Zhiming; Jiang, Meng; He, Axin; Zhu, Youyuan; Wang, Ercheng; Wan, Liqi; Qiu, Jiezhong; Guo, Pei; Chen, Guangyong; Han, Da
- **单位**：未提供（据基金信息推测含杭州医学研究所（HIM），中国科学院）
- **期刊/平台**：Nature Computational Science
- **年份**：2026
- **论文类型**：方法学（framework）论文，含实验验证
- **领域**：功能核酸（FNA）设计；核酸大语言模型（NA-LLM）；适配体（aptamer）；转录因子结合DNA
- **关键词**：functional nucleic acids, aptamers, large language models, HT-SELEX, Bayesian optimization, de novo design
- **DOI/arXiv 号**：10.1038/s43588-026-00965-3
- **代码**：未提供
- **数据**：HT-SELEX 数据（TF 数据集来自 ENA 数据库，accession ERP001824；LOX1/CXCL5 适配体数据为本研究产生，未提供 accession）
- **阅读日期**：2026-05-13
- **在课题方向中的位置**：本文属于「AI/深度学习 × 蛋白质-DNA 互作」交叉方向，聚焦于**转录因子（TF）结合 DNA 序列的生成**与**蛋白结合适配体（aptamer）的从头设计**。其核心贡献在于：不依赖 3D 结构信息，仅用 NA-LLM + HT-SELEX 数据 + 贝叶斯优化（BO）在连续潜空间中进行功能引导的序列进化。对 TF–DNA 结合机制研究而言，本文提供了一条「序列→功能」的生成式路径，可与结构预测（如 AlphaFold3）和 MD 模拟互补。

## 02 一句话总结
本文提出 InstructNA 框架，利用核酸大语言模型（NA-LLM）对 HT-SELEX 数据进行持续预训练，结合新开发的 HC-HEBO（hill climbing–heteroscedastic and evolutionary Bayesian optimization）算法在潜空间中进行功能引导的序列优化，在不依赖 3D 结构信息的条件下，为两个蛋白靶标（LOX1、CXCL5）生成了比原始 HT-SELEX 候选更多的高亲和力适配体（KD ≤ 100 nM），且生成序列与原始候选的序列相似性可低至 38%。

## 03 研究问题
- **具体问题**：如何在不依赖 3D 结构信息的前提下，对功能核酸（FNA，包括 TF 结合 DNA 和蛋白结合适配体）进行高效的从头（de novo）设计？
- **为什么重要**：FNA（适配体、调控元件、DNAzyme/ribozyme）是分子工具的核心组件，但核酸的 3D 结构数据稀缺，导致无法像蛋白质设计那样依赖结构-功能关系。传统 SELEX 实验成本高、成功率低、初始文库序列空间覆盖不全。
- **现有方法不足**：
  - 传统 SELEX：高成本、低成功率、PCR 偏好性导致功能序列丢失。
  - 计算设计方法（如 RaptGen、AptaDiff）：仅在小规模、靶标特异的 SELEX 数据上训练，缺乏跨靶标的语义泛化能力。
  - 结构预测方法（如 AlphaFold3、RoseTTAFoldNA）：依赖核酸 3D 结构，而核酸结构数据稀缺。
- **精确的 "Can ... ?" 问题**：Can a nucleic acid large language model, when continually pretrained on HT-SELEX data and guided by a hill-climbing Bayesian optimization algorithm in latent space, generate functional nucleic acid sequences (TF-binding DNA and protein-binding aptamers) with enhanced binding affinity/specificity and high sequence diversity, without relying on 3D structural information?

## 04 背景与发展脉络
*注：此脉络基于本文框架及引用文献，部分经外部核验。*

| 阶段 | 代表方法 | 优点 | 局限 | 本文位置 |
|------|----------|------|------|----------|
| 实验筛选 | SELEX (Tuerk & Gold 1990; Ellington & Szostak 1990) | 体外进化真实功能序列 | 高成本、低成功率、文库覆盖不全、PCR 偏好 | 本文用 HT-SELEX 数据作为训练/种子来源 |
| 计算设计（早期） | 基于结构的设计、分子对接 | 可解释 | 依赖 3D 结构，核酸结构数据稀缺 | 本文明确不依赖结构 |
| 深度学习生成（蛋白质） | ESM、AlphaFold、ProteinMPNN | 蛋白质设计成功 | 核酸领域缺乏类似的结构-功能数据 | 本文借鉴 LLM 思路但用于核酸 |
| 深度学习生成（核酸） | RaptGen (2022)、AptaDiff (2024) | 无需 3D 结构，潜空间生成 | 仅在小规模靶标特异 SELEX 数据上训练，缺乏跨靶标泛化 | 本文以 RaptGen 为主要基线 |
| 核酸大语言模型 | DNABERT (2021)、Evo1 (2024)、Nucleotide Transformer (2023) | 在大规模基因组数据上预训练，捕获序列语义 | 生成能力未被充分开发 | 本文核心：持续预训练 + 解码器 + BO |
| 本文 | InstructNA = NA-LLM + HT-SELEX 持续预训练 + HC-HEBO | 跨靶标泛化、无需结构、序列多样性高 | 需要 HT-SELEX 数据；未验证其他 FNA 类型 | — |

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 核酸 3D 结构数据稀缺 | 无法像蛋白质设计那样依赖结构-功能关系 | 核酸柔性高、结晶困难 | Introduction 第 2 段 |
| 传统 SELEX 效率低 | 高成本、低成功率、初始文库覆盖不全 | PCR 偏好性、文库复杂度有限 | Introduction 第 1 段 |
| 现有深度生成模型泛化差 | RaptGen/AptaDiff 仅在小规模靶标特异数据上训练 | 无法学习跨靶标的丰富序列-功能语义 | Introduction 第 3 段 |
| NA-LLM 生成能力未被开发 | 现有 NA-LLM 主要用于表示学习/预测，而非生成 | 缺乏生成-评估闭环框架 | Discussion 第 1 段 |
| 潜空间优化易陷入局部最优 | 标准 BO 在潜空间中全局搜索导致序列多样性差或功能差 | BO 倾向于全局优化，忽略局部邻域 | Extended Data Fig. 2b, Supplementary Fig. 8 |
| 生成序列与原始候选相似度过高 | 生成序列缺乏新颖性 | 解码器可能过度拟合训练数据 | Fig. 1c（生成序列相似性可低至 38%） |

## 06 核心思想

### 1) 表面方法
InstructNA 是一个五步框架：(1) 从 HT-SELEX 实验收集 FNA 序列；(2) 用这些序列对现有 NA-LLM（如 DNABERT）进行持续预训练，得到领域适配的 FNA-LLM 编码器；(3) 在编码器之上训练一个轻量级解码器，将潜空间嵌入映射回序列；(4) 使用新开发的 HC-HEBO 算法在潜空间中对种子序列的嵌入进行局部优化，以功能指标（如结合特异性/亲和力）为目标；(5) 实验验证生成序列并迭代优化。

### 2) 核心洞察
- **洞察一**：NA-LLM 在大规模基因组数据上预训练后，其潜空间已经隐含了丰富的序列语义；用 HT-SELEX 数据持续预训练可以进一步将潜空间「拉向」功能相关区域，使潜空间中的局部邻域对应功能相似的序列。
- **洞察二**：标准 BO 在潜空间中做全局搜索容易跳出功能相关区域；HC-HEBO 通过 hill climbing 将搜索限制在种子序列嵌入的局部邻域，同时利用 HEBO 的异方差建模处理功能评估中的噪声，实现「局部但有方向」的进化。
- **洞察三**：编码器-解码器架构将「序列空间」映射到「连续潜空间」，使得 BO 这类连续优化算法可以直接作用于序列生成，绕过了离散序列的组合爆炸问题。

### 3) 可能的普适教训 [Analysis]
- **教训一**：在数据稀缺的生物序列设计场景中，「大规模预训练 + 小规模领域适配 + 潜空间优化」的范式可能比「从零训练靶标特异模型」更有效。这与蛋白质设计中的 ESM 思路一致，但本文证明该思路在核酸领域同样可行。
- **教训二**：优化算法的选择应与潜空间的结构相匹配。如果潜空间中功能相关区域是「局部岛状」分布，全局优化器可能失效，局部搜索（hill climbing）反而更有效。这对 TF–DNA 结合 motif 的潜空间探索有直接启示。
- **教训三**：功能评估（如结合亲和力）往往有噪声且昂贵，BO 的异方差建模（heteroscedastic）可以显式处理这种噪声，这一思想可迁移到任何「生成-评估」闭环中。

## 07 方法总览

- **输入**：HT-SELEX 实验得到的 FNA 序列（TF 结合 DNA 或蛋白结合适配体）；功能评估信号（结合特异性分数或 KD 值）
- **输出**：新的 FNA 序列（具有增强功能、高序列多样性）
- **模块**：
  1. **编码器（FNA-LLM）**：基于 DNABERT（3-mer tokenization），用 HT-SELEX 序列持续预训练，输出每个 token 的嵌入（降维至 8 维）
  2. **解码器**：6 层 transformer block，将嵌入序列映射回 token 序列（序列重建任务）
  3. **HC-HEBO 优化器**：在潜空间中对种子嵌入进行局部搜索，目标函数为功能指标（结合特异性/亲和力）
- **训练**：
  - 阶段一：持续预训练（masked language modeling，15% token 被 mask）
  - 阶段二：冻结编码器，训练解码器（序列重建损失）
- **反馈回路**：生成序列 → 实验评估（SPR 测 KD）→ 功能指标反馈给 BO → 下一轮优化
- **假设**：
  - 潜空间中的局部邻域对应功能相似的序列
  - HT-SELEX 数据足以将 NA-LLM 的潜空间「拉向」功能相关区域
  - 功能指标（结合特异性/亲和力）可以作为 BO 的连续目标函数
- **文字流程**：HT-SELEX 序列 → 持续预训练 DNABERT → 得到 FNA-LLM 编码器 → 训练解码器 → 从种子序列（如 top-frequency 序列）出发，在潜空间中用 HC-HEBO 搜索 → 解码生成新序列 → 实验验证（SPR）→ 反馈给 BO → 迭代

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 持续预训练（FNA-LLM） | 将 NA-LLM 适配到 HT-SELEX 功能序列域 | 通用 NA-LLM 的潜空间未针对功能序列优化 | 输入：HT-SELEX 序列；输出：领域适配的编码器 | Extended Data Fig. 1a（与 RaptGen 相比，潜空间-序列相关性更高） | 预期：潜空间语义变差，BO 搜索效率下降 [预期效应] |
| 降维层（8 维嵌入） | 将高维 token 嵌入压缩至低维连续空间 | 使 BO 在低维空间中可行 | 输入：token 嵌入；输出：8 维向量 | Methods 节 | 预期：维度太高时 BO 样本效率下降 [预期效应] |
| 解码器（6 层 transformer） | 将潜空间嵌入映射回序列 | 实现「嵌入→序列」的生成 | 输入：嵌入序列；输出：token logits | Methods 节 | 预期：无法生成有效序列 [预期效应] |
| HC-HEBO | 在潜空间中进行局部功能引导优化 | 标准 BO 全局搜索导致功能差；HC 限制局部邻域 | 输入：种子嵌入、功能评估函数；输出：优化后的嵌入 | Extended Data Fig. 2b, Supplementary Fig. 8（HC-HEBO 优于 HEBO） | 实测：HEBO 生成序列功能差、多样性高；HC-HEBO 功能好 [实测消融效应] |
| 种子序列选择（S1+S2+S3） | 提供多样化的初始嵌入 | 单一来源种子可能陷入局部最优 | 输入：top-frequency 序列、cluster centers、高功能序列近邻；输出：初始嵌入集合 | Extended Data Fig. 2c | 预期：单一来源种子时生成多样性下降 [预期效应] |
| 迭代验证（SPR） | 实验评估生成序列功能 | 计算功能指标（结合特异性）与实验亲和力不完全一致 | 输入：生成序列；输出：KD 值 | Fig. 2b–e | 预期：无实验反馈时 BO 目标函数失真 [预期效应] |

## 09 关键公式符号

1. **结合特异性分数**（8mer_sum 算法）：
   $$S_{\text{total}} = \sum_{i=1}^{n} S_{8\text{mer}}^i$$
   - $S_{\text{total}}$：全长 DNA 序列的结合特异性分数
   - $S_{8\text{mer}}^i$：第 $i$ 个 8-mer motif 的蛋白结合微阵列荧光强度
   - $n$：全长序列中 8-mer motif 的总数（滑动窗口，窗口大小 8，步长 1）

2. **相对结合特异性归一化**：
   $$S_{\text{norm}} = \frac{S - S_{\min}}{S_{\max} - S_{\min}} \times 100$$
   - $S_{\text{norm}}$：归一化后的相对结合特异性（范围 0–100）
   - $S_{\min}$、$S_{\max}$：数据集中的最小/最大结合特异性分数

3. **序列重建损失**（解码器训练）：
   $$L_{\text{recon}} = -\sum \log P(x_i | \mathbf{e}_i)$$
   - $x_i$：第 $i$ 个位置的 ground-truth token
   - $\mathbf{e}_i$：第 $i$ 个位置的嵌入向量
   - $P(x_i | \mathbf{e}_i)$：softmax 后给定嵌入条件下 token 的概率

4. **HC-HEBO 搜索空间**：
   $$S_0 = \{\mathbf{e} \mid \|\mathbf{e} - E_0\| \le \Delta R_0\}$$
   - $E_0$：初始解（种子嵌入）
   - $\Delta R_0$：初始搜索半径（默认 5）
   - 迭代中半径减半，最小阈值 $\Delta R_{\min} = 1.25$

5. **HC-HEBO 贪心选择**：
   $$\mathbf{E}_{i,t} = \arg\max_{\mathbf{e} \in G_{t,i}} f(\mathbf{e})$$
   - $G_{t,i}$：第 $t$ 次迭代第 $i$ 组的候选嵌入集合
   - $f(\mathbf{e})$：功能评估函数（结合特异性/亲和力）

## 10 实验设计与证据链

**数据集与规模**：
- TF 结合 DNA：10 个转录因子（Ar, Atf4, Dbp, Egr3, Foxg1, Klf12, Mlx, Nr2e1, Sox10, Srebf1）的 HT-SELEX 数据，来自 ENA 数据库（accession ERP001824）。每个数据集的 cleaned unique 序列数从 1,695（Atf4）到 205,472（Srebf1）不等（Supplementary Fig. 1）
- 适配体：LOX1 和 CXCL5 两个蛋白靶标，HT-SELEX 实验为本研究新做（Supplementary Note 9, Table 2）

**指标**：
- 结合特异性分数（8mer_sum）
- 相对结合特异性（归一化到 0–100）
- KD 值（SPR 实验，强结合 ≤ 100 nM）
- 序列相似性（与 top-frequency 原始序列的最大相似性）
- 潜空间-序列相关性（Pearson 相关系数）

**基线**：
- RaptGen（生成模型）
- DNABERT（编码器基线）
- HEBO（无 hill climbing 的 BO）
- 原始 HT-SELEX top-frequency 序列

**评测协议**：
- 对每个 TF 数据集生成 30 条序列，比较结合特异性分数与 top-10 原始序列
- 对 LOX1/CXCL5 生成 10 条序列，SPR 测 KD
- 潜空间质量：随机采样 1,000 条序列，计算嵌入余弦相似度与序列比对相似度的 Pearson 相关

**关键实验表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 潜空间-序列相关性 | InstructNA 编码器捕获序列语义 | InstructNA vs RaptGen vs DNABERT，10 个 TF 数据集 | InstructNA 在全部 10 个数据集上 Pearson 相关高于 RaptGen；在 8/10 数据集上高于 DNABERT | 持续预训练提升潜空间语义质量 | 未证明语义质量与生成功能直接因果 | Extended Data Fig. 1a |
| 结合特异性分类 | InstructNA 表示捕获序列-功能关系 | 线性探针，二分类（高/低结合特异性） | InstructNA 在 AUROC/F1/accuracy/recall 上优于 RaptGen（全部 10 数据集），优于 DNABERT（≥7/10 数据集） | 持续预训练增强功能相关表示 | 分类性能不等于生成能力 | Extended Data Fig. 1b,c, Supplementary Fig. 6 |
| KDE 扰动鲁棒性 | 解码器对嵌入扰动鲁棒 | 从 KDE 拟合分布采样 2,000 嵌入，解码后比较 k-mer 频率与 G/C 含量 | InstructNA 在 k-mer（3–6）频率上几乎全部优于 RaptGen；G/C 含量更接近真实分布 | InstructNA 解码器更鲁棒 | 未测试扰动幅度对功能的非线性影响 | Extended Data Fig. 1, Supplementary Fig. 7 |
| HC-HEBO vs HEBO | hill climbing 提升功能优化 | 相同种子，HC-HEBO vs HEBO，TF 数据集 | HC-HEBO 生成序列结合特异性更高，多样性略低 | hill climbing 限制局部搜索有助于功能优化 | 未系统扫描搜索半径超参数 | Extended Data Fig. 2b, Supplementary Fig. 8 |
| 种子来源多样性 | 多源种子提升性能 | S1（top-frequency）、S2（cluster centers）、S3（高功能近邻）单独 vs 组合 | 组合种子优于单一来源 | 多源种子提供更丰富的初始嵌入 | 未分析各来源的独立贡献 | Extended Data Fig. 2c |
| 迭代轮数 | 多轮优化提升功能 | 1 vs 2 轮 HC-HEBO | 2 轮优于 1 轮 | 迭代优化有效 | 未测试 3 轮以上 | Extended Data Fig. 2d |
| TF 结合 DNA 生成 | InstructNA 生成高结合特异性序列 | InstructNA vs RaptGen，各生成 30 条，3 个 TF | Ar: 87% vs 83% 优于 top-10；Dbp: 13% vs 3%；Srebf1: 13% vs 0% | InstructNA 在 Srebf1 上显著优于 RaptGen | Ar 数据集两者差异不显著；未做实验验证结合 | Fig. 1b,c, Supplementary Fig. 10 |
| 适配体生成（LOX1） | InstructNA 生成高亲和力适配体 | 10 条生成序列 vs 10 条 HT-SELEX top-frequency，SPR 测 KD | 4 条生成序列为强结合（KD ≤ 100 nM），HT-SELEX 仅 2 条；G1L KD=12.9 nM vs T1L KD=23.1 nM | InstructNA 生成适配体亲和力优于 HT-SELEX | 样本量小（n=10）；未做功能验证（如细胞实验） | Fig. 2b,d, Supplementary Fig. 13 |
| 适配体生成（CXCL5） | InstructNA 生成高亲和力适配体 | 同上 | 3 条生成序列为强结合，HT-SELEX 仅 1 条；G1C KD=6.6 nM vs T1C KD=18.3 nM | InstructNA 生成适配体亲和力优于 HT-SELEX | 同上 | Fig. 2c,e, Supplementary Fig. 14 |
| 结构分析 | 生成序列形成不同结构 | G1L vs T1L 的 AlphaFold3 预测结构 + MD 模拟 | G1L 形成更复杂的环区结构，与 LOX1 不同结构域结合 | 生成序列可能采用不同结合模式 | 未做突变实验验证关键残基 | Extended Data Fig. 3, Supplementary Note 11 |

## 11 结论正确解读

- **任务范围**：本文的「de novo design」指在给定 HT-SELEX 训练数据的前提下，生成新的、功能增强的 FNA 序列。并非从零（无任何实验数据）设计，而是「数据驱动的序列优化」。
- **oracle/真值输入**：TF 结合 DNA 的功能指标是计算得到的结合特异性分数（8mer_sum），非实验结合数据；适配体的功能指标是 SPR 实验测得的 KD 值（实验真值）。
- **端到端状态**：InstructNA 的「生成-评估」闭环中，TF 部分评估是计算模拟（8mer_sum），适配体部分评估是实验（SPR）。尚未实现「全自动闭环」——实验步骤仍需人工介入。
- **算力成本**：未报告训练/推理的具体算力需求。
- **历史数据依赖**：模型依赖 HT-SELEX 数据质量；TF 数据来自公开数据库，适配体数据为本研究产生。
- **模型依赖**：编码器基于 DNABERT（3-mer），未测试其他 NA-LLM 架构的差异。
- **最难情形**：Srebf1 数据集（205,472 条序列，最大）上 RaptGen 完全失败（0% 优于 top-10），InstructNA 仅 13% 优于 top-10，说明高复杂度数据集上生成仍具挑战。
- **边界**：仅验证了 TF 结合 DNA 和蛋白结合适配体两类 FNA；未验证 DNAzyme、核酶等功能类型。仅测试了 DNA（非 RNA）适配体。
- **有边界的复述**：在 HT-SELEX 数据可获取且功能可量化的前提下，InstructNA 能够生成与原始候选序列差异显著（相似性低至 38%）但功能相当或更优的 FNA 序列，其效果在蛋白结合适配体上优于传统 HT-SELEX 筛选。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 需要 HT-SELEX 数据 | 模型训练和种子选择依赖 HT-SELEX 实验数据 | 探索无实验数据条件下的生成（如纯 LLM 生成） | Discussion 第 2 段 |
| 仅验证部分 FNA 类型 | 只测试了 TF 结合 DNA 和蛋白结合适配体 | 扩展到 DNAzyme、功能 RNA 等其他 FNA 类型 | Discussion 第 2 段 |
| 未整合 3D 结构信息 | 当前框架不利用结构信息 | 整合 AlphaFold3、RoseTTAFoldNA 和 MD 模拟作为额外评估标准 | Discussion 第 3 段 |
| 功能评估依赖单一指标 | TF 部分用计算结合特异性分数，适配体用 KD | 引入更多功能维度（如特异性、热稳定性、细胞活性） | Discussion 第 3 段 |
| 迭代优化轮数有限 | 仅测试 2 轮 HC-HEBO | 探索更多轮次的长期优化行为 | Extended Data Fig. 2d |
| 未报告算力成本 | 未提供训练/推理的算力需求 | 未提供 | 未提供 |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| TF 结合 DNA 的功能评估用计算分数（8mer_sum）而非实验验证 | 计算分数可能无法完全反映真实 TF-DNA 结合；生成序列的「增强」可能只是计算指标上的增强 | 若计算分数与实验结合不一致，则「功能增强」结论不成立 | 对生成序列做 EMSA、ChIP-seq 或 HT-SELEX 验证 | Methods 节 |
| 适配体验证样本量小（n=10/蛋白） | 10 条序列的统计功效有限，4/10 和 3/10 的「强结合」比例可能受抽样波动影响 | 小样本可能高估 InstructNA 的优势 | 增加生成序列数量，重复 SPR 实验 | Fig. 2b,c |
| 与 RaptGen 的比较公平性存疑 | RaptGen 是否在相同条件下训练/调参？InstructNA 使用了持续预训练 + BO，RaptGen 是否使用了其最优配置？ | 若基线未调优，则比较结果可能偏向 InstructNA | 检查 RaptGen 的超参数是否与原文一致；做多随机种子比较 | Methods 节 |
| 未报告生成序列的批次效应 | 不同轮次生成的序列是否在功能上有系统性差异？ | 若存在批次效应，可能影响结论的稳健性 | 按生成轮次分层分析功能指标 | 未提供 |
| 结构分析（AlphaFold3 + MD）仅展示单个例子 | G1L vs T1L 的结构差异是否具有普遍性？ | 单个案例不足以支持「生成序列采用不同结合模式」的结论 | 对多个生成序列做结构预测和 MD 模拟 | Extended Data Fig. 3 |
| 未讨论生成序列的脱靶效应 | 高亲和力适配体可能非特异结合其他蛋白 | 适配体的实用性取决于特异性 | 做交叉结合实验（如对无关蛋白的 SPR） | 未提供 |
| 「de novo」定义模糊 | 生成序列与训练数据相似性低（38%）但并非完全「从零设计」 | 若生成序列实质上是训练序列的重组，则「de novo」程度有限 | 分析生成序列与训练集的 k-mer 重叠度、motif 富集 | Fig. 1c |

## 14 学到什么
*标题：Agent 提炼的知识候选*

1. **潜空间局部搜索优于全局搜索**：在生物序列生成中，功能相关区域在潜空间中可能呈「局部岛状」分布。HC-HEBO 的 hill climbing 策略（限制搜索半径 + 逐步缩小）比全局 BO 更有效。**可迁移到 TF–DNA 结合 motif 的潜空间探索**：在蛋白质语言模型的潜空间中，已知 TF 结合位点可能聚集在特定区域，局部搜索可高效发现新 motif 变体。

2. **持续预训练是「领域适配」的关键**：仅用通用 DNA LLM（如 DNABERT）不足以捕获 FNA 的功能语义；用 HT-SELEX 数据持续预训练可以显著提升潜空间质量。**对 TF–DNA 互作研究**：若目标是生成特定 TF 的结合位点，应使用该 TF 的 ChIP-seq/HT-SELEX 数据对基础 DNA LLM 进行持续预训练，而非从零训练。

3. **编码器-解码器架构解耦「表示」与「生成」**：编码器负责将序列映射到有意义的潜空间，解码器负责将嵌入还原为序列。这种解耦使得优化算法可以独立于序列离散性进行设计。**可迁移思路**：在 TF–DNA 结合预测中，可先训练一个编码器捕获 DNA 序列的 TF 结合语义，再训练一个解码器用于 motif 生成或序列优化。

4. **多源种子策略提升生成多样性**：从 top-frequency 序列、cluster centers、高功能序列近邻三个来源取种子，比单一来源更优。**对 TF–DNA 研究**：在设计 TF 结合位点文库时，可同时从已知高亲和位点、motif 聚类中心和计算预测的高功能序列出发，扩大搜索覆盖。

5. **计算分数 + 实验验证的两阶段评估**：TF 部分用计算分数（8mer_sum）做快速筛选，适配体部分用 SPR 做精确验证。这种「粗筛 + 精验」策略在计算成本与实验成本之间取得平衡。**可迁移到 TF–DNA 研究**：先用 PBM/HT-SELEX 计算分数或深度学习预测分数做大规模筛选，再用 EMSA/SPR 验证少量候选。

6. **KD 值作为连续优化目标**：将 KD 值（而非二分类结合/不结合）作为 BO 的目标函数，使得优化过程可以区分「弱结合」和「强结合」，实现渐进式优化。**对 TF–DNA 研究**：若目标是增强 TF-DNA 结合亲和力，应使用连续亲和力指标（如 KD、IC50）而非二分类标签作为优化目标。

7. **结构信息可作为后验验证而非先验约束**：本文先用 AlphaFold3 预测结构、再用 MD 模拟验证，而非将结构信息作为生成约束。**可迁移思路**：在 TF–DNA 结合设计中，可先生成序列，再用结构预测和 MD 模拟筛选，避免结构预测的误差在生成过程中被放大。

## 15 与已有知识连接

- **DNABERT (Ji et al., 2021)**：本文的基础编码器。DNABERT 是首个针对 DNA 的 BERT 模型，使用 k-mer tokenization。本文将其从「表示学习」扩展到「生成」场景，通过持续预训练 + 解码器实现。**连接点**：DNABERT 的潜空间质量直接影响 InstructNA 的生成效果。

- **Raptogen (Iwano et al., 2022)**：本文的主要基线。Raptogen 是首个用于适配体生成的生成模型，基于 VAE。本文指出 Raptogen 的局限在于仅在小规模靶标特异数据上训练，缺乏跨靶标泛化。**连接点**：InstructNA 的持续预训练策略是对 Raptogen 范式的直接改进。

- **HEBO (Cowen-Rivers et al., 2022)**：本文 BO 算法的基础。HEBO 是异方差贝叶斯优化框架，本文在其上引入 hill climbing 限制搜索空间。**连接点**：HC-HEBO 的「局部搜索」思想可推广到其他生物序列优化任务。

- **AlphaFold3 (Abramson et al., 2024)**：本文用于预测 DNA-蛋白复合物结构。AlphaFold3 支持核酸-蛋白复合物预测，本文将其作为后验验证工具。**连接点**：在 TF–DNA 互作研究中，AlphaFold3 可作为生成序列的结构验证工具。

- **RoseTTAFoldNA (Baek et al., 2024)**：Discussion 中提到的核酸结构预测工具，与 AlphaFold3 互补。**连接点**：可作为 InstructNA 生成序列的替代结构验证工具。

- **SELEX/HT-SELEX (Tuerk & Gold, 1990; Ellington & Szostak, 1990)**：本文的数据来源和实验验证方法。**连接点**：HT-SELEX 数据质量直接影响 InstructNA 的训练效果。

- **8mer_sum 算法**：本文用于计算 TF 结合特异性分数的方法，源自蛋白结合微阵列（PBM）数据分析。**连接点**：该算法可作为 TF–DNA 结合强度的快速计算指标。

- **[Analysis] 候选方向**：与蛋白质设计中的 ESM + 扩散模型（如 Chroma、RFdiffusion）范式类比，InstructNA 可视为「DNA 版」的潜空间优化生成框架。但核酸的构象柔性远高于蛋白质，如何将结构信息更紧密地耦合到生成过程中仍是开放问题。

## 16 研究想法
*标题：Agent 生成的研究候选*

### 候选 1：TF–DNA 结合 motif 的潜空间定向进化
- **名称**：TF-Motif-Evolve
- **来源局限/观察**：InstructNA 证明了 NA-LLM + BO 可生成功能增强的 TF 结合 DNA，但未系统分析生成序列中的 motif 结构。TF–DNA 结合的核心是序列 motif（如锌指蛋白的 3-bp 识别位点），潜空间优化是否隐式地保留了 motif 结构尚不清楚。
- **核心假设**：在潜空间中进行局部搜索时，如果种子序列包含已知 TF 结合 motif，优化过程会倾向于在保持 motif 核心的同时优化侧翼序列，从而增强结合特异性。
- **初步方法**：使用 InstructNA 框架，以已知 TF 结合 motif 为种子，在潜空间中做 HC-HEBO 优化；对生成序列做 motif 扫描（如 MEME、HOMER），分析 motif 保守性和侧翼序列变化。
- **验证方式**：对生成序列做 HT-SELEX 或 EMSA 实验，比较 motif 保守序列与优化序列的结合亲和力。
- **创新状态**：unverified

### 候选 2：结构感知的 FNA 生成评估器
- **名称**：StructFNA-Score
- **来源局限/观察**：InstructNA 明确不依赖 3D 结构信息，但 Discussion 中提出整合 AlphaFold3 和 MD 作为未来方向。当前框架的评估函数（8mer_sum 或 KD）是序列层面的，未利用结构信息。
- **核心假设**：将 AlphaFold3 预测的复合物结构质量（如 pLDDT、ipTM）或 MD 模拟的结合自由能作为 BO 的辅助评估信号，可以进一步提升生成序列的功能。
- **初步方法**：在 InstructNA 的评估环节中，对候选序列做 AlphaFold3 结构预测，将结构质量分数与序列层面的结合分数融合为多目标评估函数；对 top 候选做 MD 模拟验证。
- **验证方式**：比较「序列-only」与「序列+结构」两种评估策略下生成序列的实验结合亲和力。
- **创新状态**：unverified

### 候选 3：跨物种 TF 结合特异性迁移
- **名称**：TF-Bind-Transfer
- **来源局限/观察**：InstructNA 在 10 个 TF 数据集上训练，但未测试跨 TF 的迁移能力。不同 TF 的 DNA 结合域（DBD）类型不同（锌指、bZIP、homeodomain 等），其结合 motif 的潜空间分布可能不同。
- **核心假设**：NA-LLM 的持续预训练可以学习到 TF 结合 DNA 的通用语义，使得在一个 TF 上训练的优化策略可以迁移到另一个 TF（尤其是同一 DBD 家族的 TF）。
- **初步方法**：在 5 个 TF 上训练 InstructNA，在另外 5 个 TF 上测试生成性能（零样本迁移）；分析同一 DBD 家族内外的迁移效果差异。
- **验证方式**：比较迁移场景与直接训练场景下生成序列的结合分数分布。
- **创新状态**：unverified

### 候选 4：RNA 适配体的 InstructNA 扩展
- **名称**：InstructRNA
- **来源局限/观察**：InstructNA 仅处理 DNA 适配体，但 RNA 适配体（如 SELEX 筛选的 RNA 适配体）在治疗诊断中同样重要。RNA 的二级结构（茎环、假结）对适配体功能至关重要，而 DNA LLM 的 tokenization 和预训练策略可能不直接适用于 RNA。
- **核心假设**：将 InstructNA 框架迁移到 RNA 适配体设计时，需要在 tokenization 中引入 RNA 二级结构信息（如结构感知的 token），而非仅使用序列 token。
- **初步方法**：使用 RNA 专用 LLM（如 RNA-FM、RNABERT）作为基础模型，在 RNA 适配体 HT-SELEX 数据上持续预训练；在潜空间中用 HC-HEBO 优化，评估函数用 RNA 适配体的结合亲和力。
- **验证方式**：对生成 RNA 适配体做体外转录和结合实验，比较与 DNA 适配体生成的效果差异。
- **创新状态**：unverified

### 候选 5：TF–DNA 结合特异性的可解释潜空间分析
- **名称**：TF-Latent-Interp
- **来源局限/观察**：InstructNA 的潜空间是黑盒，未分析潜空间维度与 TF 结合特异性之间的对应关系。理解潜空间的语义结构有助于设计更可控的生成策略。
- **核心假设**：InstructNA 的潜空间中存在与 TF 结合特异性高度相关的低维子空间，且该子空间的方向与已知 motif 序列变异方向一致。
- **初步方法**：对 InstructNA 编码器输出的嵌入做 PCA/UMAP 降维，分析嵌入方向与 TF 结合特异性分数的相关性；用探针向量（如 motif 序列的嵌入差）解释潜空间中的功能方向。
- **验证方式**：在潜空间中沿功能方向做插值，验证插值序列的结合分数单调变化。
- **创新状态**：unverified