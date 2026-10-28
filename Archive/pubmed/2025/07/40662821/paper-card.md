## 01 基本信息

- **标题**：Prediction of gene regulatory connections with joint single-cell foundation models and graph-based learning
- **作者**：Kommu, Sindhura; Wang, Yizhi; Wang, Yue; Wang, Xuan
- **单位**：未提供（根据资助信息推测涉及 Virginia Tech、Children's National Hospital 等，但作者单位未在摘要中明确列出）
- **期刊/平台**：Bioinformatics (Oxford, England)
- **年份**：2025
- **论文类型**：方法学（Method）研究
- **领域**：计算生物学 / 单细胞基因组学 / 基因调控网络推断
- **关键词**：scRNA-seq、基因调控网络（GRN）、单细胞基础模型（scFM）、图神经网络（GNN）、链接预测
- **DOI/ID**：10.1093/bioinformatics/btaf217
- **代码**：https://github.com/sindhura-cs/scRegNet
- **数据**：BEELINE 基准数据集（GSE81252、GSE75748、GSE98664、GSE48968、GSE81682）
- **阅读日期**：2026-05-13（基于当前日期）
- **在该课题方向中的位置**：本文聚焦于**TF–DNA 结合机制**的监督学习建模，将 GRN 推断形式化为**基因调控链接预测**任务。其核心创新在于将**单细胞基础模型（scFM）**（scBERT、Geneformer、scFoundation）提取的上下文感知基因表征与**图神经网络（GNN）**编码的网络拓扑信息进行联合，用于预测 TF–靶基因调控关系。该方法属于「AI/深度学习 × TF–DNA 互作」交叉方向，展示了预训练基础模型在调控链接预测中的迁移价值。

---

## 02 一句话总结

本文提出 scRegNet 框架，通过将单细胞基础模型（scBERT/Geneformer/scFoundation）提取的基因级上下文嵌入与 GNN 编码的调控网络拓扑嵌入拼接，以监督学习方式预测 TF–基因调控链接，在 7 个 BEELINE 基准数据集上一致超越 9 个基线方法（AUROC/AUPRC）。

---

## 03 研究问题

- **具体问题**：如何利用 scRNA-seq 数据准确预测基因调控网络中的缺失调控链接（TF–靶基因互作）？
- **为什么重要**：GRN 是理解细胞分化、发育和疾病机制的关键。scRNA-seq 提供了单细胞分辨率的基因表达谱，但数据的高稀疏性、噪声和 dropout 事件严重制约了 GRN 推断的准确性。准确的调控链接预测有助于揭示细胞表型的分子基础。
- **现有方法不足**：
  - 无监督方法（如 GENIE3、GRNBoost2）依赖共表达/相关性假设，在稀疏数据上精度有限，尤其 AUPRC 表现差。
  - 现有监督方法（如 GENELink、GNNLink）虽利用图结构，但未充分利用大规模预训练模型中学到的丰富基因关系语义。
  - 监督方法需要大量实验验证的 TF–DNA 结合数据作为训练标签，而这类数据获取成本高、覆盖有限。
- **精确研究问题**：*Can pre-trained single-cell foundation models, when combined with graph-based learning, improve gene regulatory link prediction accuracy over existing supervised and unsupervised baselines across diverse cell types?*

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及参考文献构建，标注为「经外部核验」的部分来自文中引用的经典工作。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|----------|
| **第一阶段：无监督共表达/回归方法** | GENIE3（Huynh-Thu et al. 2010）、GRNBoost2（Moerman et al. 2019）、PCC | 无需标签数据，计算简单 | 依赖相关性假设，无法捕捉非线性调控；稀疏数据下假阳性高；AUPRC 表现差 | 作为基线对比 |
| **第二阶段：监督深度学习方法** | CNNC（Yuan and Bar-Joseph 2019）、GNE（Kc et al. 2019）、DeepDRIM（Chen et al. 2021） | 利用实验验证的 TF–DNA 结合数据训练，精度显著提升 | 需要大量标签数据；特征工程依赖人工设计；未充分利用大规模无标签数据 | 作为基线对比 |
| **第三阶段：图神经网络方法** | GENELink（Chen and Liu 2022）、GNNLink（Mao et al. 2023） | 显式建模调控网络拓扑结构，捕捉多跳关系 | 节点初始特征仅来自表达数据，缺乏跨细胞类型的语义泛化 | 作为最强基线对比 |
| **第四阶段：基础模型 + 图学习（本文）** | **scRegNet** | 融合 scFM 的上下文感知基因嵌入与 GNN 的网络拓扑嵌入，兼具语义丰富性与结构感知能力 | 依赖预训练模型的表征质量；scFM 参数冻结，无法针对下游任务微调 | **本文主张的位置** |

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| **scRNA-seq 数据高稀疏性** | 大量 dropout 事件导致基因表达矩阵中零值占比极高 | 单细胞测序技术本身的捕获效率有限，低表达基因容易被遗漏 | Introduction 第 1 段（"scRNA-seq data are typically sparse due to high dropout rates"） |
| **无监督方法精度不足** | GENIE3、GRNBoost2、PCC 在 AUPRC 上表现差 | 依赖共表达/相关性假设，无法区分真实调控关系与噪声共现 | Results 表 2、表 3（传统方法 AUPRC 显著低于监督方法） |
| **监督方法依赖大量标签数据** | 需要大量实验验证的 TF–DNA 结合数据作为训练标签 | 实验验证成本高、周期长，难以覆盖所有细胞类型和物种 | Introduction 第 2 段（"requires a large amount of experimentally validated GRNs as labeled training data, which is often experimentally expensive"） |
| **现有监督方法特征表达有限** | GENELink、GNNLink 的节点特征仅来自表达数据，缺乏跨细胞类型的语义泛化 | 未利用大规模预训练模型中蕴含的基因关系知识 | Introduction 第 3 段（"scRegNet harnesses the rich, context-aware gene-level representations learned by large-scale pre-trained models"） |
| **图网络稀疏性** | 调控网络边稀疏，GNN 消息传递信息有限 | 已知调控关系仅覆盖少数 TF–靶基因对 | Results 节 "Impact of GNN architecture"（"sparsity of the networks" 导致不同 GNN 架构性能趋同） |

---

## 06 核心思想

### 1) 表面方法

scRegNet 是一个两阶段框架：
- **第一阶段**：使用预训练的单细胞基础模型（scBERT、Geneformer、scFoundation）从 scRNA-seq 表达矩阵中提取每个基因的上下文感知嵌入（context-aware embedding），然后通过 mean pooling 跨细胞聚合得到每个基因的细胞类型级表征。
- **第二阶段**：将已知的 TF–基因调控关系构建为图，使用 GNN（GCN）编码网络拓扑，得到基因的拓扑嵌入。
- **融合**：将 scFM 嵌入与 GNN 嵌入拼接为联合表征，输入 MLP 链接预测层，输出调控链接存在概率。

### 2) 核心洞察

- **互补性**：scFM 嵌入捕捉"基因在细胞语境中的语义关系"（从数百万单细胞转录组中学到的共调控模式），而 GNN 嵌入捕捉"已知调控网络的局部拓扑结构"。两者互补——前者提供泛化的生物学先验，后者提供细胞类型特异的调控结构。
- **冻结 vs 微调**：scFM 参数在训练中保持冻结，仅训练 GNN 和 MLP 层，大幅降低计算成本，同时验证了预训练表征的迁移价值。
- **简单架构足够**：作者发现简单的 GCN 即可达到与更复杂的 GNN（GAT、GraphSAGE）相当的性能，归因于调控网络的稀疏性。

### 3) 可能的普适教训 [Analysis]

- **基础模型 + 图学习的组合范式**可推广到其他生物网络推断任务（如蛋白质–蛋白质互作、代谢网络重建），核心思路是"预训练语义表征 + 任务特定结构编码"。
- **冻结预训练模型**的策略在标签稀缺的生物场景中尤为实用，避免了微调带来的过拟合风险。
- **稀疏网络下架构选择不重要**的发现提示：在生物网络任务中，应优先关注特征工程和图构建，而非堆叠复杂模型。

---

## 07 方法总览

- **输入**：
  - scRNA-seq 表达矩阵 X ∈ R^(N×T)（N 细胞 × T 基因）
  - 已知 TF–基因调控图 G = {V, E}（来自 ChIP-seq 实验验证数据）
- **输出**：每个 TF–基因对的调控链接存在概率（二分类）
- **模块**：
  1. **scFM 编码器**：三种可选（scBERT、Geneformer、scFoundation），参数冻结，输出基因级嵌入
  2. **Mean Pooling**：跨细胞聚合基因嵌入 → 细胞类型级基因表征
  3. **GNN 编码器**：GCN（默认），在调控图上做消息传递，输出节点拓扑嵌入
  4. **拼接层**：将 scFM 嵌入与 GNN 嵌入拼接
  5. **MLP 链接预测层**：ReLU + Dropout + 全连接分类层 + Softmax
- **训练**：Binary Cross-Entropy (BCE) 损失，端到端反向传播（仅更新 GNN 和 MLP 参数）
- **流程**：
  1. 对每个基因 t，从 scFM 提取嵌入 h_t^(L)，跨 N 个细胞 mean pooling → Z_scFM[t]
  2. 构建调控图 G，初始化节点特征（可能为表达数据或 one-hot），GCN 消息传递 → Z_GNN[t]
  3. 拼接 Z_joint[t] = [Z_scFM[t] ⊕ Z_GNN[t]]
  4. 对候选基因对 (i,j)，拼接 Z_joint[i] ⊕ Z_joint[j] → MLP → Softmax 概率
- **工具**：PyTorch（推测，未明确说明）、Optuna（超参数优化）
- **假设**：
  - 已知调控图（训练标签）可靠且具有代表性
  - scFM 预训练表征可迁移到下游调控预测任务
  - 调控关系可以通过基因嵌入的拼接+MLP 有效建模

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| **scFM 编码器**（scBERT/Geneformer/scFoundation） | 从 scRNA-seq 表达谱提取上下文感知的基因嵌入 | 捕捉跨细胞的基因共调控模式，提供超越单细胞表达值的语义信息 | 输入：表达矩阵；输出：基因级嵌入（200/896/512 维） | Results 表 2、3：所有 scFM 变体均优于无 scFM 的基线 | **实测消融**（图 2）：移除 scFM 嵌入导致性能显著下降，证明预训练表征的关键贡献 |
| **Mean Pooling** | 跨细胞聚合基因嵌入 | 将单细胞级嵌入压缩为细胞类型级表征，降低噪声 | 输入：N 个细胞的基因嵌入；输出：单向量/基因 | 方法节 "Mean pooling" | **预期**：若改为其他聚合（如 attention pooling），可能小幅提升但增加计算成本 |
| **GNN 编码器**（GCN） | 编码调控网络拓扑结构 | 捕捉 TF–基因间的多跳关系，补充 scFM 缺乏的结构信息 | 输入：调控图 + 节点特征；输出：节点拓扑嵌入 | Results 节 "Impact of GNN architecture"：GCN 与 GAT/GraphSAGE 性能相当 | **实测消融**（图 2）：移除 GNN 导致性能下降，但下降幅度小于移除 scFM |
| **拼接层** | 融合 scFM 与 GNN 嵌入 | 实现语义与结构的互补 | 输入：两个嵌入向量；输出：拼接向量 | 方法节 "Unified gene representations" | **预期**：若改为加权求和或 attention 融合，可能进一步提升但需更多调参 |
| **MLP 链接预测层** | 输出基因对调控概率 | 将联合表征映射为二分类概率 | 输入：拼接后的基因对表征；输出：Softmax 概率 | 方法节 "Link prediction layer" | **预期**：若替换为更复杂的解码器（如双线性层），可能小幅提升 |

---

## 09 关键公式符号

| 公式 | 符号含义 | 用途 | 来源 |
|------|----------|------|------|
| X ∈ R^(N×T) | N=细胞数，T=基因数 | 定义输入 scRNA-seq 表达矩阵 | Methods 节 "Gene representations from foundation models" |
| h_t^(0) = emb_gene2vec(g_t) + emb_expr(g_t) | h_t^(0)=基因 t 的初始嵌入；emb_gene2vec=基因身份嵌入；emb_expr=表达水平嵌入 | scBERT 的输入构建 | Methods 节 "scBERT" |
| h_t^(l) = TransformerLayer(h_t^(l-1)) | h_t^(l)=第 l 层 Transformer 输出 | 多层注意力编码 | Methods 节 公式 (1)（文中以 "similar to Equation (1)" 引用） |
| Z_scFM[t] = (1/N) Σ_n h_t^(n)(L) | Z_scFM[t]=基因 t 的 mean-pooled scFM 嵌入；N=细胞数；h_t^(n)(L)=基因 t 在细胞 n 中的最终层嵌入 | 跨细胞聚合 | Methods 节 "Mean pooling" |
| Z_joint[t] = [Z_scFM[t] ⊕ Z_GNN[t]] | ⊕=拼接操作 | 融合语义与拓扑嵌入 | Methods 节 "Unified gene representations" |
| L_BCE = -(1/K) Σ_k [y_k log(p_k) + (1-y_k) log(1-p_k)] | K=训练基因对数，y_k=真实标签，p_k=预测概率 | 训练损失 | Methods 节 "Model training"（文中描述为 BCE loss，公式为推断） |
| R_t = RankValue(g_t) | R_t=基因 t 的 rank 值 token | Geneformer 的输入构建 | Methods 节 "Geneformer" |

---

## 10 实验设计与证据链

### 数据集与评测协议

- **数据集**：7 个 BEELINE 基准 scRNA-seq 数据集
  - 人类：hESC（胚胎干细胞）、hEP（成熟肝细胞）
  - 小鼠：mDC（树突状细胞）、mESC（胚胎干细胞）、mHSC-E（红系造血干细胞）、mHSC-GM（粒-单核系造血干细胞）、mHSC-L（淋巴系造血干细胞）
- **Ground truth**：细胞类型特异的 ChIP-seq 调控网络（来自 ENCODE、ChIP-Atlas、ESCAPE）
- **数据划分**：每个 TF 的正/负样本按 67%/33% 划分训练/测试，另留 10% 训练数据作为验证集；按 TF 划分防止数据泄漏
- **特征基因选择**：分别使用 500 和 1000 个最显著变异基因（含所有 TF）
- **指标**：AUROC、AUPRC
- **基线（9 个）**：GNNLink、GENELink、GNE、CNNC、DeepDRIM、GRN-transformer、PCC、GRNBoost2、GENIE3
- **超参数优化**：Optuna 框架
- **消融**：移除 scFM 嵌入、移除 GNN 编码器
- **GNN 架构对比**：GCN vs. GAT vs. GraphSAGE

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| **主实验（表 2、3）** | scRegNet 优于所有基线 | 7 数据集 × 2 基因数设置（500/1000）× 3 scFM 变体 vs. 9 基线 | scRegNet 全部变体在所有数据集上 AUROC/AUPRC 均最高；Geneformer 变体平均 AUROC 提升 7.4%（vs GNNLink）、6.9%（vs GENELink）；AUPRC 提升 18.6%（vs GNNLink）、4.1%（vs GENELink） | 融合 scFM + GNN 的表征策略有效提升调控链接预测精度 | 无法证明 scRegNet 在未见过的细胞类型/组织中的泛化能力 | Results 表 2、3 |
| **消融实验（图 2）** | scFM 和 GNN 均有贡献 | 完整模型 vs. 移除 GNN vs. 移除 scFM（Geneformer 为 backbone） | 任一组件移除均导致 AUROC/AUPRC 下降 | 两个模块互补，缺一不可 | 未报告各消融变体的具体数值，仅图示 | Results 节 "Ablation study"、图 2 |
| **GNN 架构对比（表 S4）** | GCN 足够，复杂架构无显著优势 | GCN vs. GAT vs. GraphSAGE（均配 Geneformer） | 三者性能接近，仅略有差异 | 稀疏调控网络下简单 GNN 足够 | 无法排除在更稠密网络或更大数据集上复杂架构的优势 | Results 节 "Impact of GNN architecture"、表 S4 |
| **鲁棒性实验（图 3）** | 模型对训练标签噪声鲁棒 | 1%/2%/3%/4% 标签翻转 vs. GENELink | scRegNet 在各噪声水平下均优于 GENELink，且性能下降更平缓 | 模型对噪声先验具有鲁棒性 | 未测试 >4% 噪声水平；未报告方差具体数值 | Results 节 "Robustness study"、图 3 |
| **生物学验证（表 S3）** | 预测的新调控链接具有生物学意义 | hESC 数据集上 Novel 预测 vs. 文献 | NANOG→BMPR1A、JUND→SNAI2、OTX2→CITED2 等预测与已知功能一致 | 模型预测具有生物学可解释性 | 仅 3 个示例，非系统性验证 | Results 节 "Biological relevance"、表 S3 |

---

## 11 结论正确解读

- **任务范围**：本文解决的是**调控链接预测**（给定 TF 和候选靶基因，判断是否存在调控关系），而非从零推断完整 GRN 结构。输出是边存在概率，而非调控方向或强度。
- **Oracle/真值输入**：训练标签来自 ChIP-seq 实验验证的 TF–DNA 结合数据（ENCODE、ChIP-Atlas、ESCAPE），属于实验验证的"金标准"调控关系。这意味着模型性能上限受限于 ChIP-seq 数据的覆盖度和质量。
- **端到端状态**：scFM 参数冻结，仅 GNN + MLP 端到端训练。因此模型并未利用 scFM 的微调潜力，性能可能仍有提升空间。
- **算力成本**：未报告具体训练时间/GPU 资源。由于 scFM 冻结，主要成本在 GNN 和 MLP 训练，预计远低于从头训练 Transformer。
- **历史数据依赖**：scFM 预训练数据来自大规模 scRNA-seq 语料库（具体数据集未在摘要中说明），其表征质量受预训练数据分布影响。
- **模型依赖**：性能高度依赖 scFM 的选择（Geneformer 和 scFoundation 优于 scBERT），以及调控图构建质量。
- **最难场景**：稀疏调控信号的数据集（如 mHSC 系列）上，绝对 AUPRC 仍偏低（具体数值未在摘要中给出），说明低表达基因的调控预测仍是挑战。
- **群体/领域边界**：仅在人类和小鼠的 7 个细胞类型上验证，未覆盖其他物种、疾病状态或非编码调控。
- **不确定性**：未报告置信区间或多次运行的标准差；鲁棒性实验仅覆盖标签噪声，未测试表达数据噪声、图构建误差等。

**有边界的复述**：scRegNet 在 7 个 BEELINE 基准数据集上，以 ChIP-seq 验证的调控关系为标签，通过冻结的 scFM 嵌入 + GNN 拓扑嵌入 + MLP 分类器，实现了优于 9 个基线的调控链接预测精度（AUROC/AUPRC），并对低水平标签噪声具有鲁棒性。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| **依赖实验验证的 TF–DNA 结合数据** | 训练需要 ChIP-seq 等实验数据作为标签，新细胞类型可能缺乏此类数据 | 将现有 TF–DNA 互作图谱知识融入 scFM 预训练阶段，直接基于 scRNA-seq 进行 GRN 推断 | Conclusions 第 1 段 |
| **浅层融合策略** | scFM 和 GNN 表征仅在拼接层融合，交互不充分 | 探索跨模态注意力机制（cross-modal attention），使两种表征在迭代更新中相互增强 | Conclusions 第 2 段 |
| **scFM 参数冻结** | 预训练模型未针对下游任务微调，可能限制任务特定特征提取 | 未明确提及，但隐含在"更深度融合"的未来方向中 | Conclusions 第 2 段（推断） |
| **GNN 架构选择缺乏理论指导** | 不同 GNN 架构性能接近，但未解释原因 | 未明确提及 | Results 节 "Impact of GNN architecture"（推断） |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| **数据划分按 TF 而非按基因** | 虽然防止了同一 TF 的泄漏，但同一靶基因可能出现在多个 TF 的训练/测试中，导致靶基因层面的信息泄漏 | 可能高估模型对新靶基因的泛化能力 | 按靶基因划分训练/测试，或报告按靶基因分组的交叉验证结果 | Methods 节 "Experimental setup" 中描述的数据划分策略 |
| **消融实验仅报告图示结果** | 图 2 未给出具体数值和统计显著性检验，无法判断差异是否显著 | 消融结论的强度无法量化评估 | 补充消融实验的数值表格和统计检验（如配对 t 检验） | Results 节 "Ablation study"、图 2 |
| **鲁棒性实验仅覆盖标签噪声** | 实际应用中表达数据噪声、dropout 率变化、图构建误差等同样重要 | 模型在真实场景中的鲁棒性可能低于实验所示 | 增加对表达数据降采样、dropout 模拟、图边随机删除的鲁棒性测试 | Results 节 "Robustness study" |
| **生物学验证仅 3 个示例** | 样本量过小，无法排除偶然性；且均为已知调控关系的"重新发现" | 模型发现新调控关系的能力未得到验证 | 在更多数据集上系统验证 novel 预测，或与 CRISPR 筛选等扰动实验数据对比 | Results 节 "Biological relevance"、表 S3 |
| **未报告计算成本** | 无法评估方法在大规模数据集上的可扩展性 | 实际应用中计算资源是重要考量 | 报告训练/推理时间、GPU 型号、内存占用 | 全文未提及 |
| **scFM 选择缺乏系统比较** | 仅比较了三种 scFM 作为 backbone，未与"从头训练 Transformer"或"非 Transformer 特征提取器"对比 | 无法判断 scFM 的预训练优势是否可被简单特征工程替代 | 增加"随机初始化 Transformer"和"PCA/autoencoder 特征"作为对照 | Results 表 2、3 |
| **[Analysis] 与 TF–DNA 结合机制的联系较间接** | 模型预测的是"调控链接是否存在"，但未解释 TF 如何通过 DNA 结合 motif、结合位点亲和力等机制实现调控 | 对理解 TF–DNA 结合机制本身的贡献有限 | 分析模型注意力权重或嵌入空间，检查是否编码了 motif 信息 | 全文框架 |

---

## 14 学到什么

> **Agent 提炼的知识候选**

| 可迁移知识 | 描述 | 如何迁移到「TF–DNA 结合机制 × AI/物理模拟」课题 |
|-----------|------|------------------------------------------------|
| **基础模型嵌入 + 图结构联合编码** | 将预训练模型的语义表征与图拓扑编码拼接，实现信息互补 | 可将 AlphaFold/ESM 等蛋白质基础模型的嵌入与 TF–DNA 复合物结构图（或接触图）结合，用于预测结合亲和力或特异性 |
| **冻结预训练模型策略** | 在大规模预训练模型上冻结参数，仅训练轻量任务头，降低计算成本并避免过拟合 | 在 TF–DNA 结合预测中，可冻结蛋白质语言模型（如 ESM-2）编码 TF 序列，仅训练 DNA 结合域预测头 |
| **稀疏网络下简单 GNN 足够** | 在稀疏生物网络中，GCN 与 GAT/GraphSAGE 性能相当 | 在 TF–DNA 互作网络推断中，不必追求复杂 GNN 架构，应优先优化图构建和节点特征 |
| **按 TF 划分数据防泄漏** | 按调控因子（而非靶基因）划分训练/测试集，避免信息泄漏 | 在 TF–DNA 结合预测中，应按 TF 划分训练/测试，确保测试集 TF 在训练中完全未见 |
| **噪声鲁棒性评估** | 通过标签翻转模拟噪声，评估模型鲁棒性 | 在 TF–DNA 结合数据中，ChIP-seq 本身存在噪声，可模拟标签噪声评估模型在实际数据中的可靠性 |
| **生物学验证策略** | 对 novel 预测进行文献验证，展示生物学可解释性 | 对模型预测的新 TF–DNA 结合位点，可通过已知 motif 数据库（如 JASPAR）或文献进行验证 |
| **多 backbone 对比框架** | 系统比较多种预训练模型作为特征提取器的效果 | 在 TF–DNA 结合预测中，可比较 ESM-2、ProtBERT、DNABERT 等不同基础模型作为特征提取器的效果 |
| **[Analysis] 跨模态融合的局限** | 简单拼接融合可能不足以捕捉两种表征间的复杂交互 | 在 TF–DNA 结合预测中，可探索交叉注意力机制，使蛋白质和 DNA 表征在迭代中相互调制 |

---

## 15 与已有知识连接

- **BEELINE 基准**（Pratapa et al. 2020）：本文使用的 7 个数据集来自 BEELINE，该基准是 GRN 推断领域广泛使用的标准评测平台。本文延续了该基准的评测协议（500/1000 变异基因、ChIP-seq ground truth），便于与既往方法直接对比。
- **GENELink**（Chen and Liu 2022）与 **GNNLink**（Mao et al. 2023）：本文的直接前作，均采用 GNN 进行调控链接预测。本文的增量在于引入 scFM 嵌入作为节点特征，而非仅使用表达数据。
- **单细胞基础模型**：scBERT（Yang et al. 2022）、Geneformer（Theodoris et al. 2023）、scFoundation（Hao et al. 2024）均为近期发布的单细胞领域基础模型。本文是较早将其系统应用于 GRN 推断的工作之一。
- **TF–DNA 结合数据资源**：ENCODE（Consortium 2012）、ChIP-Atlas（Okanishi et al. 2021）、ESCAPE（Xu et al. 2015）提供了实验验证的 TF–DNA 结合数据，是本文训练标签的来源。这些资源也是 TF–DNA 结合机制研究中常用的 ground truth。
- **与结构预测/物理模拟的关联** [Analysis]：本文方法完全基于序列表达数据，未涉及 TF–DNA 复合物的三维结构或物理相互作用力。但本文的"预训练嵌入 + 图学习"范式可迁移到结构层面——例如将 AlphaFold 预测的 TF–DNA 复合物结构编码为图，与序列嵌入联合用于结合特异性预测。本文未探索这一方向，但为后续工作提供了方法学参考。
- **与 motif 分析的关联** [Analysis]：本文未使用 TF 结合 motif 信息（如 JASPAR 数据库），而是让模型从数据中隐式学习结合模式。未来工作可探索将 motif 先验作为额外特征注入模型，可能进一步提升可解释性和精度。

---

## 16 研究想法

> **Agent 生成的研究候选**

### 候选 1：结构感知的 TF–DNA 结合预测框架
- **名称**：Structure-Aware TF–DNA Binding Prediction with Protein Language Models and Contact Graphs
- **来源局限/观察**：scRegNet 仅使用序列表达数据，未利用 TF–DNA 复合物的三维结构信息；而 TF 的 DNA 结合域（DBD）结构对结合特异性至关重要
- **核心假设**：将蛋白质语言模型（如 ESM-2）编码的 TF 序列嵌入与 AlphaFold 预测的 TF–DNA 复合物接触图（contact map）结合，可提升结合位点预测精度
- **初步方法**：① 使用 ESM-2 提取 TF 蛋白序列嵌入；② 使用 AlphaFold 预测 TF–DNA 复合物结构，构建 DBD 与 DNA 的接触图；③ 将序列嵌入与接触图拓扑嵌入拼接，输入 GNN 预测结合亲和力/特异性
- **验证方式**：在 ChIP-seq 基准数据集上对比 scRegNet 和纯序列方法；消融实验检验结构信息的增量贡献
- **创新状态**：unverified

### 候选 2：TF–DNA 结合 motif 先验注入
- **名称**：Motif-Guided Attention for Interpretable TF–DNA Binding Prediction
- **来源局限/观察**：scRegNet 的预测缺乏可解释性——无法回答"模型依据什么特征判断调控关系"；而 TF 结合 motif 是已知的、可解释的生物学先验
- **核心假设**：将已知 TF motif（如 JASPAR）作为注意力偏置注入 Transformer，可同时提升预测精度和可解释性
- **初步方法**：① 在 scFM 的注意力层中引入 motif 位置偏置（motif position bias）；② 训练后分析注意力权重，检查是否集中在已知 motif 区域；③ 对比有无 motif 先验的预测精度
- **验证方式**：在 BEELINE 数据集上对比；用 motif 富集分析验证注意力权重的生物学意义
- **创新状态**：unverified

### 候选 3：跨细胞类型的零样本调控预测
- **名称**：Zero-Shot Gene Regulatory Prediction with Cross-Cell-Type Foundation Model Alignment
- **来源局限/观察**：scRegNet 需要每个细胞类型的 ChIP-seq 标签进行训练，而新细胞类型往往缺乏此类数据
- **核心假设**：通过对比学习对齐不同细胞类型的 scFM 嵌入空间，可实现对新细胞类型的零样本调控预测
- **初步方法**：① 在多个细胞类型的 scRNA-seq 上联合训练 scFM，使用对比损失对齐共享基因的嵌入；② 在源细胞类型上训练 GNN 预测器；③ 直接应用于目标细胞类型（零样本）
- **验证方式**：留一细胞类型交叉验证；对比零样本 vs. 有监督性能差距
- **创新状态**：unverified

### 候选 4：物理模拟与深度学习的混合方法
- **名称**：Hybrid MD-Deep Learning Framework for TF–DNA Binding Affinity Prediction
- **来源局限/观察**：scRegNet 完全忽略 TF–DNA 结合的物理化学机制（氢键、静电相互作用、构象变化等）；而分子动力学（MD）模拟可提供这些物理细节但计算成本极高
- **核心假设**：用少量 MD 模拟数据训练一个"物理代理模型"（physics surrogate），将其预测的亲和力作为特征注入深度学习模型，可提升结合预测的物理合理性
- **初步方法**：① 对代表性 TF–DNA 复合物进行 MD 模拟，提取结合自由能等物理特征；② 训练代理模型预测这些特征；③ 将代理模型输出与 scFM 嵌入拼接，输入 GNN 预测结合
- **验证方式**：在实验测定的结合亲和力数据集上对比；检验物理特征注入是否提升预测精度
- **创新状态**：unverified

### 候选 5：调控链接预测中的不确定性量化
- **名称**：Uncertainty-Aware Gene Regulatory Link Prediction with Ensemble scFM Embeddings
- **来源局限/观察**：scRegNet 输出点估计概率，未量化预测不确定性；而 ChIP-seq 标签本身含噪声，高置信度的错误预测可能误导下游实验设计
- **核心假设**：通过集成多种 scFM 嵌入或 Monte Carlo Dropout 量化预测不确定性，可帮助识别需要实验验证的高置信候选
- **初步方法**：① 使用多种 scFM（scBERT、Geneformer、scFoundation）生成嵌入集成；② 计算预测概率的方差作为不确定性估计；③ 分析不确定性-精度关系（calibration）
- **验证方式**：在 BEELINE 数据集上评估 calibration 和 selective prediction 性能
- **创新状态**：unverified