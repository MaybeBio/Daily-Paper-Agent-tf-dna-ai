## 01 基本信息
- **标题**：Regulatory network architecture constrains inflammatory responses in tissue-resident alveolar macrophages
- **作者与单位**：Kruszelnicki, Sonia M; Chakraborty, Sreeparna; Wang, Xinge; Rehman, Jalees; Singh, Harinder; Gottschalk, Rachel A（单位未提供，推测为美国大学/研究所，具体未提供）
- **期刊/预印本平台**：bioRxiv : the preprint server for biology
- **年份**：2026-02-27（预印本发布日期）
- **论文类型**：预印本（研究论文）
- **领域**：免疫学、基因调控网络、巨噬细胞生物学、计算生物学
- **关键词**：alveolar macrophages, gene regulatory networks, transcription factors, PU.1, CEBP/β, chromatin accessibility, single-cell RNA-seq, ATAC-seq, deep learning
- **DOI/arXiv 号**：10.64898/2026.02.16.706134
- **代码**：未提供
- **数据**：scRNA-seq 数据来自 GSE280003；ATAC-seq 数据来自 GSE100738（训练 ChromBPNet）、GSE231217 和 GSE319365（贡献分数计算）
- **阅读日期**：2026-05-13（假设）
- **该文在「蛋白质-DNA 互作(聚焦 TF–DNA 结合机制) × AI 方法/物理模拟」方向中的位置**：该文属于「TF–DNA 结合机制 × 深度学习」交叉方向，利用 ChromBPNet（基于深度学习的染色质可及性建模）和 TF-MoDISco 进行 motif 发现，结合 CellOracle 构建 GRN 并进行 in silico 扰动，研究组织驻留巨噬细胞中 TF 网络架构对炎症反应的约束作用。核心关注 PU.1 和 CEBP/β 两个 TF 的调控机制。

## 02 一句话总结
该文整合 scRNA-seq、ATAC-seq 和深度学习染色质可及性建模（ChromBPNet），构建组织驻留与募集来源肺泡巨噬细胞的 GRN，发现组织驻留 AM 中 PU.1 和 CEBP/β 的高连通性网络架构通过稳定 TF-TF 互作约束炎症反应，使其炎症响应较募集 AM 更为受限。

## 03 研究问题
- **具体问题**：组织驻留肺泡巨噬细胞（tissue-resident alveolar macrophages, AMs）与募集来源的单核细胞衍生 AMs 在炎症应激下，其基因调控网络架构如何不同？这种架构差异如何影响炎症反应的强度？
- **为什么重要**：巨噬细胞在不同组织中表现出功能多样性，同时维持核心先天免疫程序。理解 GRN 架构如何协调组织特异性功能与炎症反应，对揭示组织稳态维持机制和炎症相关疾病（如慢性炎症、纤维化）的病理机制至关重要。
- **现有方法为何不足**：以往研究多聚焦于单个 TF 的功能，或使用体外巨噬细胞系统构建 GRN，未能解决组织特异性 TF 活性与炎症反应调控在体内的交叉问题。缺乏将染色质可及性、TF 结合基序与基因表达程序整合的系统性框架。
- **精确的「Can ... ?」研究问题**：Can tissue-resident alveolar macrophages constrain inflammatory responses through a stabilizing gene regulatory network architecture involving PU.1 and CEBP/β, compared to recruited monocyte-derived macrophages?

## 04 背景与发展脉络
- **阶段一：单 TF 功能研究**：早期研究聚焦于单个 TF（如 PU.1、CEBP/β）在巨噬细胞发育和功能中的作用，如 PU.1 作为谱系决定因子、CEBP/β 在炎症调控中的作用。优点：明确了关键 TF 的功能；局限：无法揭示 TF 间的协同调控关系。
- **阶段二：体外 GRN 构建**：利用体外巨噬细胞系统（如骨髓来源巨噬细胞）构建炎症反应 GRN（如文献 13、14）。优点：可操控性强；局限：无法反映组织特异性微环境对 TF 活性的影响。
- **阶段三：整合多组学与深度学习**：结合 scRNA-seq、ATAC-seq 和深度学习模型（如 ChromBPNet、CellOracle）在体内系统中构建 GRN。优点：可同时考虑染色质可及性、TF 基序和基因表达；局限：计算模型对 TF 协同结合的预测仍需实验验证。
- **本文主张的位置**：本文处于阶段三，通过整合 scRNA-seq、ATAC-seq 和 ChromBPNet 深度学习建模，构建组织驻留与募集 AM 的特异性 GRN，首次系统揭示 GRN 架构差异（TF-TF 连通性）如何约束炎症反应。
- **脉络核验状态**：仅本文框架（基于摘要和正文的叙述，未进行外部文献系统核验）。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 组织特异性 GRN 缺失 | 以往 GRN 多基于体外系统，无法反映体内组织微环境对 TF 活性的影响 | 体外系统缺乏肺泡微环境信号（如 GM-CSF、TGF-β） | Introduction 节：previous studies constructed inflammatory response GRNs using in vitro macrophage systems, such GRNs did not address how tissue-specific TF activity intersects with inflammatory response regulation in vivo |
| TF 协同调控机制不明 | 单个 TF 功能已知，但 TF-TF 互作如何稳定网络架构不清楚 | 缺乏系统性网络分析框架 | Introduction 节：higher-order regulatory interactions that coordinate tissue-resident macrophage identity and inflammatory response regulation remain poorly understood |
| 炎症反应差异的调控基础未知 | 组织驻留与募集 AM 对 LPS 反应不同，但机制不清 | 缺乏将染色质可及性与 GRN 架构关联的分析 | Results 节：tissue-resident AMs were more evenly distributed across timepoints, with cells manifesting low levels of the inflammation topic |
| 深度学习模型的可解释性 | ChromBPNet 可预测染色质可及性，但如何将预测转化为 TF 调控机制需额外分析 | 需要结合 motif 发现和 GRN 推断 | Methods 节：应用 TF-MoDISco 聚类高贡献区域进行 de novo motif 发现 |

## 06 核心思想
1. **表面方法**：整合 scRNA-seq（GSE280003）和 ATAC-seq 数据，使用 ChromBPNet 深度学习模型预测染色质可及性，TF-MoDISco 进行 motif 发现，CellOracle 构建 GRN 并进行系统性 in silico TF 敲除模拟。
2. **核心洞察**：组织驻留 AM 的 GRN 具有更高的 TF-TF 连通性（以特征向量中心性衡量），这种密集的 TF 互作网络提供了调控冗余性和稳定性，使得单个 TF 扰动对网络功能的影响较小，从而约束炎症反应的幅度。相反，募集 AM 的 GRN 连通性较低，TF 扰动更容易导致功能状态的显著偏移。
3. **可能的普适教训 [Analysis]**：GRN 的拓扑架构（而非单个 TF 的活性）可能是决定细胞功能状态稳定性的关键因素。高连通性网络通过冗余机制缓冲外界扰动，这一原理可能适用于其他组织驻留细胞类型，也可为设计合成基因线路或理解疾病状态下的网络失稳提供参考。

## 07 方法总览
- **输入**：
  - scRNA-seq 数据（GSE280003，LPS 处理 0/3/6/15 天的肺泡巨噬细胞）
  - ATAC-seq 数据（GSE100738 用于训练 ChromBPNet；GSE231217、GSE319365 用于计算贡献分数）
- **输出**：
  - 组织驻留 vs 募集 AM 的特异性 GRN
  - TF 扰动对功能状态（topic）的影响分数
  - 高贡献 TF（PU.1、CEBP/β）的鉴定
- **模块**：
  1. 数据预处理：scRNA-seq 过滤、k-means 聚类、伪 bulk 生成；ATAC-seq 比对、peak calling（MACS2）
  2. Topic 建模：非负矩阵分解（fastTopics），鉴定 homeostasis/inflammation/resolution 功能状态
  3. ChromBPNet 训练：5 折交叉验证，预测染色质可及性，计算贡献分数
  4. Motif 发现：TF-MoDISco 进行 de novo motif 聚类，HOMER 进行已知 motif 富集分析
  5. GRN 构建：CellOracle 整合染色质可及性、motif 扫描和基因表达
  6. In silico 扰动：系统性模拟单个 TF 敲除，计算 topic 特异性扰动分数
- **训练**：ChromBPNet 5 折训练，使用自定义 Tn5 偏置模型回归 Tn5 切割偏置
- **反馈回路**：无显式反馈回路（非迭代优化）
- **假设**：TF 结合基序在开放染色质区域的富集可反映功能性 TF 结合；特征向量中心性可衡量 TF 在网络中的调控重要性

**文字流程**：scRNA-seq 数据 → 聚类鉴定细胞类型 → topic 建模定义功能状态 → ATAC-seq 数据 → ChromBPNet 训练并计算贡献分数 → TF-MoDISco motif 发现 → CellOracle 构建 GRN → 系统性 in silico TF 敲除 → 计算扰动分数 → 比较组织驻留 vs 募集 AM 的网络架构差异。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Topic 建模（fastTopics） | 定义巨噬细胞功能状态（homeostasis/inflammation/resolution） | 将连续基因表达谱离散化为可解释的功能程序 | 输入：scRNA-seq 表达矩阵；输出：topic 比例矩阵 | Results 节：KEGG 富集验证 topic 功能注释 | 预期影响：无法区分功能状态，后续扰动分析缺乏参照 [预期效应] |
| ChromBPNet | 预测染色质可及性并计算贡献分数 | 识别调控染色质可及性的序列特征 | 输入：ATAC-seq 数据；输出：贡献分数 bigwig | Methods 节：5 折训练，Tn5 偏置校正 | 预期影响：无法定位高贡献 TF 结合区域，GRN 构建失去染色质依据 [预期效应] |
| TF-MoDISco | de novo motif 发现 | 识别高贡献区域中的 TF 结合基序 | 输入：贡献分数；输出：motif 聚类 | Results 图 2D：ETS 和 CEBP 家族 motif 最丰富 | 预期影响：无法鉴定关键 TF 家族 [预期效应] |
| CellOracle GRN 构建 | 推断 TF-靶基因调控关系 | 将染色质可及性与基因表达关联 | 输入：ATAC-seq peak、motif 扫描、scRNA-seq 表达；输出：GRN | Methods 节：使用 Tn5 校正的开放染色质区域 | 预期影响：无法进行网络级分析 [预期效应] |
| In silico 扰动 | 模拟 TF 敲除对功能状态的影响 | 评估单个 TF 对网络稳定性的贡献 | 输入：GRN、topic 梯度；输出：扰动分数 | Results 图 2C：募集 AM 扰动向量幅度更大 | 预期影响：无法量化网络稳定性差异 [预期效应] |

## 09 关键公式符号
- **特征向量中心性（Eigenvector centrality）**：用于衡量 TF 在 GRN 中的调控重要性。定义：对于邻接矩阵 A，特征向量中心性 x 满足 Ax = λx，其中 λ 为最大特征值。用途：比较组织驻留 vs 募集 AM 中 TF 的中心性分布。直觉：一个 TF 的中心性不仅取决于其直接连接数，还取决于其邻居的中心性，反映其在网络中的全局影响力。来源：Results 图 2A 描述。
- **Topic 模型（非负矩阵分解）**：X ≈ W H，其中 X 为基因×细胞表达矩阵，W 为基因×topic 载荷，H 为 topic×细胞比例。用途：定义功能状态。直觉：将高维表达数据分解为可解释的共表达程序。来源：Methods 节 Topic Modeling。
- **扰动分数（Perturbation score）**：通过计算 in silico 敲除后 topic 梯度的点积变化得到。公式未在文中显式给出，但描述为「dot products reflecting the magnitude of alteration of these gradients」。用途：量化 TF 对功能状态维持的贡献。来源：Results 图 2B 描述。

## 10 实验设计与证据链
- **数据集**：
  - scRNA-seq：GSE280003（C57BL/6 小鼠，LPS 气管内给药，0/3/6/15 天，肺泡巨噬细胞分选）
  - ATAC-seq 训练：GSE100738（肺泡巨噬细胞）
  - ATAC-seq 测试：GSE231217、GSE319365（naïve 和 LPS 3 天）
- **样本量**：未提供具体细胞数/小鼠数
- **指标**：特征向量中心性、扰动分数（点积）、motif 富集分数
- **基线**：募集单核细胞衍生 AM vs 组织驻留 AM
- **评测协议**：5 折交叉验证训练 ChromBPNet；topic 模型选择基于最大似然和残差最小化
- **关键实验**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| Topic 建模 + 细胞注释 | 组织驻留与募集 AM 在 LPS 后功能状态不同 | 0/3/6/15 天时间点，k-means 聚类 | 募集 AM 在炎症期富集，组织驻留 AM 维持 homeostasis topic | 两类细胞对 LPS 反应不同 | 未直接证明因果性 | Results 图 1D,E |
| 特征向量中心性比较 | 组织驻留 AM 的 GRN 具有更高 TF-TF 连通性 | 组织驻留 vs 募集 AM GRN | 组织驻留 AM 的 TF 平均中心性更高 | 网络架构差异存在 | 未证明中心性差异是炎症反应差异的原因 | Results 图 2A |
| In silico 扰动 | 募集 AM 对单 TF 扰动更敏感 | 系统性敲除每个 TF，比较扰动分数 | 募集 AM 的扰动向量幅度更大 | 募集 AM 网络稳定性较低 | 未进行实验验证（如实际敲除） | Results 图 2C |
| Motif 分析 | PU.1 和 CEBP/β 是高贡献 TF | TF-MoDISco + HOMER 富集 | ETS 和 CEBP 家族 motif 最丰富，Spi1/Cebpb 高表达 | 这两个 TF 是网络关键节点 | 未直接证明其结合位点的功能重要性 | Results 图 2D,E |
| 靶向扰动 | CEBP/β 和 PU.1 敲除导致向炎症状态转变 | 组织驻留 AM 中敲除 Cebpb/Spi1 vs 其他 TF | 敲除这两个 TF 产生大扰动向量 | 这两个 TF 维持 homeostasis 并约束炎症 | 未进行实验敲除验证 | Results 图 2F |

## 11 结论正确解读
- **任务范围**：该研究仅针对小鼠肺泡巨噬细胞对 LPS 诱导的急性炎症反应，不涵盖其他组织巨噬细胞类型或其他炎症刺激。
- **oracle/真值输入**：细胞类型注释基于已知 marker 基因（未提供具体 marker 列表）；topic 功能注释基于 KEGG 富集，依赖数据库注释的准确性。
- **端到端状态**：非端到端。分析流程为模块化：scRNA-seq 聚类 → topic 建模 → ATAC-seq → ChromBPNet → GRN → 扰动。各模块独立运行，未进行整体误差传播分析。
- **算力成本**：未提供具体计算资源需求。
- **历史数据依赖**：依赖公开数据集 GSE280003、GSE100738 等，数据质量直接影响结果。
- **模型依赖**：ChromBPNet 预测准确性依赖训练数据质量；CellOracle GRN 推断依赖 motif 扫描阈值和基因表达相关性假设。
- **最难情形**：LPS 后 15 天（恢复期）的细胞状态可能难以准确注释；募集 AM 与组织驻留 AM 的边界可能模糊。
- **群体/领域边界**：仅限小鼠肺泡巨噬细胞，人类巨噬细胞或其他组织驻留巨噬细胞（如小胶质细胞、库普弗细胞）的 GRN 架构可能不同。
- **不确定性**：in silico 扰动未进行实验验证；特征向量中心性与功能稳定性的因果关系未直接证明。
- **有边界的复述**：在小鼠 LPS 诱导的急性肺炎模型中，组织驻留肺泡巨噬细胞通过 PU.1 和 CEBP/β 介导的高连通性 GRN 架构，在计算模拟层面表现出对单 TF 扰动的抵抗性，从而约束炎症反应幅度；这一结论基于计算预测，尚未经实验敲除验证。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 计算预测未经实验验证 | in silico 敲除结果未进行实际基因敲除实验 | 未明确提及，但暗示需要实验验证 | Results 节：We speculate that their stabilizing influence is supported by TF cooperation at the chromatin level |
| 推测性机制解释 | TF 协同结合于染色质水平的机制为推测 | 未明确提及 | Results 节：we speculate that their stabilizing influence is supported by TF cooperation at the chromatin level |
| 数据来源单一 | 仅使用小鼠模型和 LPS 刺激 | 未明确提及 | 未提供 |

**作者提及的相关约束**（非正式局限）：研究仅关注肺泡巨噬细胞，未涵盖其他组织驻留巨噬细胞类型；未进行跨物种验证。

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 特征向量中心性差异可能受细胞数量或测序深度影响 | 募集 AM 在炎症期数量增加，可能影响 GRN 推断的稳定性 | 中心性差异可能是技术伪影而非生物学差异 | 进行 downsampling 分析或使用伪 bulk 重复验证 | Results 图 2A 未提供统计检验细节 |
| in silico 敲除仅模拟表达量归零，未考虑 TF 的剂量效应或翻译后修饰 | 实际敲除可能产生更复杂的效果 | 模拟可能高估或低估 TF 的真实影响 | 与实验敲除数据（如 CRISPR）对比 | Methods 节未描述敲除模拟的具体实现 |
| Topic 建模选择 k=7 的依据未充分说明 | 不同 k 值可能改变功能状态注释和后续分析 | 结果可能对模型选择敏感 | 进行 k 值敏感性分析 | Methods 节仅提及「selected a model with k=7 total topics for best model performance」 |
| ChromBPNet 训练数据来自 GSE100738，但测试数据来自不同数据集 | 批次效应可能影响贡献分数计算 | 跨数据集泛化性未验证 | 使用同一数据集的留出集进行验证 | Methods 节描述的训练/测试数据来源不同 |
| PU.1 和 CEBP/β 的「高贡献」基于 motif 富集，但未验证其结合位点的功能重要性 | motif 存在不等于功能性结合 | 可能高估这两个 TF 的调控作用 | 进行 ChIP-seq 或 CRISPR 干扰验证 | Results 图 2D,E 仅显示 motif 富集 |

## 14 学到什么
**Agent 提炼的知识候选**：
1. **可迁移概念：GRN 拓扑稳定性与功能约束的关系**。该文提出高 TF-TF 连通性（特征向量中心性）赋予网络稳定性，约束炎症反应。可迁移到 TF–DNA 结合机制研究：在分析 TF 结合位点网络时，不仅关注单个 TF 的结合强度，还应考虑 TF 间的互作密度和网络拓扑对下游基因表达稳定性的影响。
2. **可迁移方法：Topic 建模 + GRN 推断的整合框架**。使用 fastTopics 定义功能状态，再通过 CellOracle 将染色质可及性、motif 和表达关联。可迁移到其他组织或细胞类型：先定义功能状态，再构建状态特异性 GRN，避免全细胞平均化掩盖异质性。
3. **可迁移方法：ChromBPNet + TF-MoDISco 的深度学习 motif 发现流程**。利用深度学习模型计算贡献分数，再通过 motif 聚类识别关键 TF。可迁移到 TF–DNA 结合机制研究：用于预测 TF 结合位点的序列特征，特别是当 ChIP-seq 数据稀缺时。
4. **可迁移概念：in silico 扰动作为网络稳定性量化工具**。系统性模拟 TF 敲除并计算功能状态偏移，可迁移到预测 TF 组合扰动效果，为实验设计提供优先级。
5. **可迁移设计：组织驻留 vs 募集细胞的对比策略**。利用同一组织微环境下两种细胞类型的自然对比，揭示网络架构差异。可迁移到其他组织驻留免疫细胞（如小胶质细胞、库普弗细胞）研究。

## 15 与已有知识连接
- **相似工作**：CellOracle 原始论文（Kamimoto et al., 2023）开发了基于染色质可及性的 GRN 推断和 in silico 扰动框架；ChromBPNet（Bentsen et al., 2020）是广泛使用的染色质可及性深度学习模型。本文是这些方法的整合应用。
- **TF 功能知识**：PU.1（Spi1）是巨噬细胞谱系决定因子，CEBP/β 参与炎症和脂质代谢调控，两者在肺泡巨噬细胞稳态中的协同作用已有报道（如文献 24-27 提及的 pioneer factor 和协同结合）。
- **可迁移领域**：该框架可迁移到其他组织驻留巨噬细胞（如小胶质细胞、库普弗细胞）或树突状细胞亚群，研究组织特异性 GRN 如何塑造免疫反应。
- **候选方向 [Analysis]**：该文未进行实验验证，未来可结合 CRISPR 敲除或 dCas9 表观编辑验证 PU.1/CEBP/β 的因果作用；也可将 GRN 架构特征（如中心性、模块性）与疾病状态（如慢性炎症、纤维化）关联。

## 16 研究想法
**Agent 生成的研究候选**：

1. **候选名称**：TF 协同结合位点的深度学习预测与实验验证
   - **来源局限/观察**：该文通过 motif 富集推断 PU.1/CEBP/β 的重要性，但未验证其结合位点的功能。
   - **核心假设**：PU.1 和 CEBP/β 在染色质上的协同结合位点（共定位 motif）比单独结合位点更能预测炎症基因的调控。
   - **增量**：使用 ChromBPNet 贡献分数 + 共定位分析，预测协同结合位点，并用 CRISPR 干扰验证。
   - **初步方法**：从 ATAC-seq 数据中提取高贡献区域，用 TF-MoDISco 识别共定位 motif，比较共定位 vs 单独 motif 区域的靶基因表达差异；设计 dCas9-KRAB 干扰实验。
   - **验证方式**：qPCR/RNA-seq 检测靶基因表达变化；ATAC-seq 检测染色质可及性变化。
   - **创新状态**：unverified

2. **候选名称**：GRN 拓扑稳定性指标作为炎症反应强度的预测因子
   - **来源局限/观察**：该文仅比较了两种细胞类型，未建立定量预测模型。
   - **核心假设**：GRN 的特征向量中心性分布（如基尼系数或模块度）可定量预测细胞对炎症刺激的反应幅度。
   - **增量**：将 GRN 拓扑指标与炎症反应强度（如 TNF-α 产量）关联，建立预测模型。
   - **初步方法**：收集多种组织驻留巨噬细胞的 scRNA-seq/ATAC-seq 数据，构建 GRN，计算拓扑指标，与 LPS 刺激后的炎症基因表达变化进行回归分析。
   - **验证方式**：交叉验证预测准确性；用独立数据集验证。
   - **创新状态**：unverified

3. **候选名称**：TF 网络冗余性与炎症疾病易感性的关联分析
   - **来源局限/观察**：该文提出高连通性网络约束炎症，但未探讨疾病状态下的网络失稳。
   - **核心假设**：慢性炎症或纤维化疾病中，肺泡巨噬细胞的 GRN 连通性下降，导致炎症反应失控。
   - **增量**：将 GRN 架构分析应用于疾病模型（如肺纤维化小鼠）。
   - **初步方法**：分析疾病模型和正常小鼠的 AM scRNA-seq/ATAC-seq，比较 GRN 拓扑差异，鉴定关键失稳 TF。
   - **验证方式**：与临床样本数据对比；药物干预恢复网络稳定性后观察表型变化。
   - **创新状态**：unverified

4. **候选名称**：跨物种 GRN 架构保守性分析
   - **来源局限/观察**：该文仅使用小鼠数据，未验证人类保守性。
   - **核心假设**：PU.1/CEBP/β 介导的 GRN 稳定架构在人类肺泡巨噬细胞中保守。
   - **增量**：使用人类 AM 数据（如公开 scRNA-seq/ATAC-seq）验证网络架构特征。
   - **初步方法**：从人类 AM 数据构建 GRN，比较中心性分布和关键 TF 模块与小鼠的相似性。
   - **验证方式**：跨物种模块保守性统计检验。
   - **创新状态**：unverified