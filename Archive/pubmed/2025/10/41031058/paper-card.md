## 01 基本信息

- **标题**：DeepEPI: CNN-transformer-based model for extracting TF interactions through predicting enhancer-promoter interactions
- **作者**：Tabatabaei, Seyedeh Fatemeh; Akbari Roknabadi, Saeedeh; Koohi, Somayyeh
- **单位**：未提供（根据作者信息推测为伊朗学术机构，具体未在文中说明）
- **期刊/平台**：Bioinformatics Advances
- **年份**：2025-10-01
- **论文类型**：方法学（深度学习模型开发与验证）
- **领域**：基因组学 / 调控基因组学 / 深度学习
- **关键词**：enhancer-promoter interactions (EPIs)、CNN、Transformer、multihead attention、transcription factor (TF) interactions、OneHot encoding、DNA2Vec
- **DOI/arXiv 号**：10.1093/bioadv/vbaf221
- **代码**：https://github.com/nazanintbtb/DeepEPI.git
- **数据**：TargetFinder EPI 数据集（6 种人类细胞系）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 深度学习」方向，聚焦于**顺式调控元件（增强子-启动子）之间的互作预测**，并从中**提取转录因子（TF）及其互作**。与课题「TF–DNA 结合机制」的关联在于：本文通过注意力权重定位关键序列基序并映射到 TF，从而间接推断 TF 与 DNA 的结合位点及 TF-TF 协同关系。方法上属于**序列驱动的监督学习**，而非物理模拟或结构预测。

---

## 02 一句话总结

本文提出 DeepEPI——一个结合 CNN 与 Transformer 的深度学习框架，仅从增强子和启动子 DNA 序列预测增强子-启动子互作（EPI），并通过 multihead attention 的注意力权重提取 TF 基序及 TF-TF 互作，在 6 种人类细胞系上优于现有方法（如 EPIVAN、EPI-Trans），同时以 OneHot 嵌入层降低存储开销并保持可解释性。

---

## 03 研究问题

- **具体问题**：能否仅从增强子和启动子的 DNA 序列（无需额外表观遗传特征）准确预测增强子-启动子互作，并同时提取参与互作的转录因子及其互作关系？
- **为什么重要**：EPI 是基因表达调控的核心机制，异常 EPI 与多种人类疾病相关。识别 EPI 及其中的 TF 互作有助于理解疾病机制、药物开发。传统实验方法（Hi-C、ChIA-PET）昂贵且耗时，计算预测可大幅缩小实验验证范围。
- **现有方法不足**：
  - 依赖额外基因组特征（如 TargetFinder 使用 DNase-seq、ChIP-seq、组蛋白修饰等）的方法受限于数据可用性和特征选择知识。
  - 纯序列方法（如 SPEID、EPIVAN）虽有效，但多数缺乏 TF 及 TF-TF 互作提取能力；仅 EPIANN 支持 TF 互作提取，但性能有限。
  - Transformer 模型（如 EPI-Trans）虽有精度提升，但缺乏可解释性。
- **精确研究问题（Can...?）**：Can a CNN-Transformer hybrid model, trained solely on enhancer and promoter sequences, predict EPIs with higher accuracy than existing methods while simultaneously extracting biologically valid TF–TF interactions via multihead attention?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 的叙述，标注为「仅本文框架」，未经外部系统核验。

| 阶段 | 代表方法 | 优点 | 局限 |
|------|----------|------|------|
| 早期计算预测 | TargetFinder (Whalen et al. 2016) | 多组学特征整合，精度较高 | 依赖多种实验数据，数据缺失时不可用 |
| 纯序列方法 | Yang et al. (2017) — word embedding + boosted tree | 无需额外组学数据 | 特征工程依赖，模型容量有限 |
| 神经网络方法 | EPIANN (Mao et al. 2017) | 引入注意力机制，支持 TF 互作提取 | 精度有限 |
| 深度序列模型 | SPEID (Singh et al. 2019) — CNN+LSTM | 提取序列基序（PFM） | 不支持 TF 互作提取 |
| 简化深度模型 | SIMCNN (Zhuang et al. 2019) — CNN+迁移学习 | 计算高效 | 精度有限 |
| RNN+注意力 | EPIVAN (Hong et al. 2020) — CNN+GRU+attention，DNA2Vec | 精度较高 | 可解释性有限 |
| 纯 Transformer | EPI-Trans (Ahmed et al. 2024) — DNA2Vec | 精度略有提升 | 缺乏可解释性 |
| **本文** | **DeepEPI — CNN+Transformer+multihead attention，embed-OneHot** | **精度高、可解释、存储高效、支持 TF 及 TF-TF 互作提取** | **OneHot 编码缺乏特征间依赖** |

**本文主张的位置**：在纯序列 EPI 预测方法中，DeepEPI 首次将 CNN 与 Transformer 结合，在保持高精度的同时通过 multihead attention 实现 TF 与 TF-TF 互作的可解释提取，填补了「高精度 + 可解释 + TF 互作提取」的空白。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有方法缺乏 TF 互作提取能力 | 多数纯序列 EPI 预测模型仅输出互作概率，无法识别参与互作的 TF 及其互作关系 | 模型架构未设计可解释的注意力机制，或未将注意力权重映射回序列基序 | Introduction: "only PEPWORD, TF-EPI, SPEID, and EPIANN support the identification of TFs, and among them, EPIANN is the only one that identifies TF interactions" |
| OneHot 编码存储开销大 | 传统 OneHot 编码需存储大规模稀疏矩阵，GPU 内存消耗高 | 每个核苷酸用 4 维二进制向量表示，长序列（3000+2000 bp）导致高维稀疏输入 | Results 3.3: "Embed-OneHot encoding required ∼1.9 GB of GPU memory, representing a reduction of nearly 3 GB compared to traditional OneHot encoding" |
| OneHot 编码缺乏特征间依赖 | OneHot 编码无法捕获核苷酸之间的语义关系 | OneHot 是离散独立表示，不包含序列上下文信息 | Introduction: "OneHot encoding... faces challenges such as lack of inter-feature dependencies" |
| 类别不平衡影响训练 | 正负样本比例 1:20，模型偏向预测负类 | 数据天然不平衡，EPI 在基因组中稀疏 | Methods 2.1: "20 negative samples were selected for every positive sample, maintaining a consistent 1:20 ratio" |
| 数据增强与损失函数加权效果差异 | 类加权损失函数效果显著低于数据增强 | 类加权损失未能增加训练数据多样性，模型仍缺乏对正类变异的泛化能力 | Results 3.1: 类加权损失 AUC 0.888/AUPR 0.452 vs 数据增强（50 bp）AUC 0.935/AUPR 0.705 |
| 可解释性与精度难以兼得 | 高精度 Transformer 模型（EPI-Trans）缺乏可解释性 | 纯 Transformer 架构未设计基序提取机制 | Introduction: EPI-Trans "lacks interpretability features" |

---

## 06 核心思想

### 1) 表面方法

DeepEPI 是一个端到端的深度学习流水线：
- **输入**：增强子（3000 bp）和启动子（2000 bp）的 DNA 序列
- **编码**：OneHot 编码（通过嵌入层实现，即 embed-OneHot）或 DNA2Vec 词嵌入
- **特征提取**：CNN 卷积层分别处理增强子和启动子序列，提取局部基序特征
- **序列建模**：Transformer block 捕获长程依赖和跨区域互作
- **注意力池化**：multihead attention 层替代全连接层，对 Transformer 输出进行加权聚合
- **输出**：EPI 互作概率（二分类）

### 2) 核心洞察

- **CNN 负责局部基序识别，Transformer 负责全局依赖建模**：增强子-启动子互作既依赖局部 TF 结合基序（CNN 擅长），也依赖远距离调控关系（Transformer 擅长），两者互补。
- **Multihead attention 的注意力权重可直接映射回序列位置**：通过将注意力分数最高的序列片段提取为 PWM 矩阵，再用 TOMTOM 比对到已知 TF 基序数据库，即可实现「预测即解释」——无需额外解释工具。
- **Embed-OneHot 编码在保持 OneHot 可解释性的同时解决存储问题**：通过嵌入层动态生成 OneHot 表示，避免显式存储大规模稀疏矩阵，兼顾可解释性与资源效率。

### 3) 可能的普适教训 [Analysis]

- **注意力权重作为可解释性接口**：本文展示了注意力机制不仅是性能组件，还可作为「可解释性出口」——将注意力分数映射回输入空间即可获得生物学上有意义的基序。这一思路可迁移到其他 TF–DNA 结合预测任务（如 ChIP-seq 峰内基序发现）。
- **混合架构的分工原则**：CNN 提取局部模式 + Transformer 建模全局依赖的组合，在序列类生物学任务中具有通用性，尤其适合「局部基序 + 远程调控」的调控基因组学问题。
- **编码方式的选择应同时考虑性能与可解释性**：DNA2Vec 精度更高但不可解释，OneHot 可解释但存储大——本文的 embed-OneHot 是「折中方案」，提示在模型设计时应将下游解释需求纳入编码选择考量。

---

## 07 方法总览

- **输入**：增强子序列（3000 bp）+ 启动子序列（2000 bp），来自 TargetFinder 数据集，6 种人类细胞系（具体细胞系名称见原文 Table 2，此处未提供）
- **输出**：EPI 互作概率（二分类）；以及从 multihead attention 中提取的 TF 基序和 TF-TF 互作
- **模块**：
  1. 嵌入层（embed-OneHot 或 DNA2Vec）
  2. CNN 特征提取（增强子和启动子分别处理）
  3. 合并层（增强子+启动子特征融合）
  4. Transformer block（含 multihead attention、前馈网络、层归一化）
  5. 注意力层（替代全连接层，用于最终分类）
  6. 分类输出层
- **训练**：
  - 损失函数：交叉熵
  - 优化器：Adam
  - Batch size：64
  - 类别不平衡处理：数据增强（序列平移 10/25/50 bp）或类加权损失（两种策略分别评估）
  - 训练策略：先在 6 个细胞系合并数据上训练（"best" 模型），再对每个细胞系单独微调
- **工具**：TensorFlow；TOMTOM（基序比对）；HOCOMOCO Human v11（TF 基序数据库）；BioGRID（TF-TF 互作验证）
- **反馈回路**：无显式主动学习回路；TF 提取结果通过 TOMTOM/BioGRID 事后验证
- **假设**：
  - 增强子和启动子序列包含足够信息预测 EPI（无需额外表观遗传特征）
  - Multihead attention 的注意力权重能反映功能性 TF 结合位点
  - 跨细胞系共享的调控语法可通过联合训练捕获

**文字流程**：
1. 增强子和启动子序列分别经嵌入层编码
2. CNN 卷积+池化提取局部基序特征
3. 增强子和启动子特征向量合并
4. 合并特征输入 Transformer block，捕获长程依赖
5. Transformer 输出经 multihead attention 层加权聚合
6. 聚合向量经全连接层输出 EPI 概率
7. 训练完成后，从 multihead attention 权重中提取高注意力序列片段 → 构建 PWM → TOMTOM 比对 → 识别 TF → BioGRID 验证 TF-TF 互作

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 嵌入层（embed-OneHot） | 将 DNA 序列映射为稠密向量表示 | 降低 OneHot 存储开销，同时保持可解释性 | 输入：DNA 序列（one-hot 索引）；输出：嵌入向量 | Results 3.3: 相比传统 OneHot 减少 ~3 GB GPU 内存 | 预期影响：若移除并改用传统 OneHot，存储开销显著增加，可能限制 batch size 或序列长度 [Analysis] |
| CNN 特征提取 | 提取局部序列基序（TF 结合位点样模式） | 增强子/启动子功能依赖短 motif，CNN 擅长局部模式识别 | 输入：嵌入向量；输出：局部特征图 | Results 3.2: 三步消融实验显示 CNN 贡献显著 | 实测消融：三步消融中移除 CNN 组件后性能下降（具体数值见原文 Fig. 2，此处未提供） |
| Transformer block | 建模增强子-启动子间的长程依赖和全局互作 | EPI 涉及远距离调控，需捕获非局部特征关系 | 输入：CNN 合并特征；输出：上下文增强的特征表示 | Results 3.2: 引入 Transformer 后性能优于纯 CNN 基线 | 实测消融：三步消融中移除 Transformer 后性能下降（具体数值见原文 Fig. 2） |
| Multihead attention 层 | 替代全连接层，加权聚合特征并输出注意力权重 | 提供可解释性——注意力权重可映射回序列基序 | 输入：Transformer 输出 H；输出：加权和 S + 注意力权重 | Results 3.5: 从注意力头中提取 158 个启动子 TF 和 154 个增强子 TF | 预期影响：若替换为全连接层，模型可能仍保持精度但丧失 TF 提取能力 [Analysis] |
| 数据增强（序列平移） | 生成正类样本的变异版本 | 缓解 1:20 类别不平衡 | 输入：正样本序列；输出：平移 10/25/50 bp 的序列变体 | Results 3.1: 50 bp 平移获得最佳 AUC 0.935/AUPR 0.705 | 实测消融：类加权损失（AUC 0.888/AUPR 0.452）显著低于数据增强，说明数据多样性比损失加权更有效 |
| 类加权损失 | 在损失函数中提高正类权重 | 替代数据增强的另一种不平衡处理策略 | 输入：预测 logits + 标签；输出：加权交叉熵损失 | Results 3.1: 效果显著低于数据增强 | 实测消融：AUC 0.888 vs 数据增强 0.935，说明仅调整损失权重不足以弥补数据多样性缺失 |

---

## 09 关键公式符号

文中明确给出的公式较少，以下为可提取的核心公式：

**公式 (1)-(3)：CNN 特征提取**
- 增强子特征：E₀ = f_CNN(E)，其中 E 为增强子嵌入向量
- 启动子特征：P₀ = f_CNN(P)，其中 P 为启动子嵌入向量
- 合并特征：M = [E₀; P₀]（拼接操作）

**公式 (4)：Transformer block 输出**
- H = Transformer(M)，H 为上下文增强的合并特征表示

**公式 (5)：注意力层**
- S = Σᵢ αᵢ hᵢ
- 其中 αᵢ = softmax(u_cᵀ tanh(W_h hᵢ + b_h))
- hᵢ 为 H 的第 i 行（第 i 个位置的上下文特征）
- W_h 为可学习权重矩阵，b_h 为偏置，u_c 为可训练的上下文向量

**符号说明**：
- E：增强子序列嵌入（3000 bp）
- P：启动子序列嵌入（2000 bp）
- E₀, P₀：CNN 提取的增强子/启动子特征
- M：合并特征
- H：Transformer 输出
- S：注意力加权后的最终表示（用于分类）
- αᵢ：第 i 个位置的注意力权重

**用途**：
- 公式 (1)-(3) 描述特征提取与融合流程
- 公式 (4) 描述 Transformer 的序列建模
- 公式 (5) 描述注意力池化机制，其权重 αᵢ 是后续 TF 提取的关键——高 αᵢ 对应的序列位置被用于构建 PWM

---

## 10 实验设计与证据链

### 数据集与评测协议

- **数据集**：TargetFinder EPI 数据集，6 种人类细胞系（具体名称见原文 Table 2，此处未提供）
- **正负样本**：正负比 1:20，负样本与正样本具有相似的增强子-启动子距离分布
- **数据划分**：训练集 90%，测试集 10%；从训练集中再留出 5% 作为验证集
- **指标**：AUROC（area under the ROC curve）和 AUPR（area under the precision-recall curve）
- **基线/对比方法**：EPIVAN、EPI-Trans、PEPWORD、SPEID、EPIANN（均为已发表的 EPI 预测工具）
- **硬件**：NVIDIA GPU 8 GB 内存（具体型号未提供）
- **实现**：TensorFlow

### 实验列表

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 数据增强 vs 类加权损失 | 数据增强比类加权损失更有效 | HUVEC 细胞系；10/25/50 bp 平移 vs 类加权损失 | 50 bp 平移：AUC 0.935/AUPR 0.705；类加权：AUC 0.888/AUPR 0.452 | 数据增强显著优于类加权损失 | 仅在一个细胞系上验证，未在所有 6 个细胞系上比较 | Results 3.1 |
| 三步消融（baseline → +Transformer → +Attention） | 每个组件对性能的贡献 | 逐步添加 Transformer 和 Attention 层 | 每步均有提升（具体数值见原文 Fig. 2，此处未提供） | Transformer 和 Attention 层均贡献性能提升 | 未报告各步的统计显著性检验 | Results 3.2, Fig. 2 |
| 编码方式比较（OneHot vs embed-OneHot vs DNA2Vec） | embed-OneHot 在性能与资源间取得平衡 | 相同模型结构，不同编码 | DNA2Vec 精度最高；embed-OneHot 接近且内存减少 ~3 GB | embed-OneHot 是资源高效且性能接近的选择 | 未报告各编码方式的详细统计比较 | Results 3.3, Fig. 3 |
| 与现有工具比较 | DeepEPI 优于现有方法 | 6 个细胞系；对比 EPIVAN、EPI-Trans、PEPWORD、SPEED、EPIANN | DeepEPI_best_DNA2Vec 平均 AUROC 最优；DeepEPI_best_onehot 在 AUPR 上超过多数方法 | DeepEPI 在精度上具有竞争力 | 各工具在不同细胞系上表现有波动，非所有细胞系均最优 | Results 3.4, Fig. 4 |
| TF 提取与验证 | 注意力权重能识别真实 TF 结合位点 | 从注意力头提取 PWM → TOMTOM 比对 → ENCODE 验证 | 提取 158 个启动子 TF、154 个增强子 TF；75.6% 的 TF-TF 互作在 BioGRID 中有物理互作支持 | 注意力权重具有生物学意义 | ENCODE 验证仅覆盖部分细胞系；TF-TF 互作验证依赖 BioGRID 的覆盖度 | Results 3.5, 3.6 |
| CTCF-CTCF 互作分析 | 模型能捕获已知的染色质组织相关互作 | 全注意力头搜索 CTCF-CTCF | 在 4 个细胞系中检测到 CTCF-CTCF 互作 | 模型能恢复已知的调控互作 | 未与其他方法提取的 CTCF-CTCF 做定量比较 | Results 3.5 |

---

## 11 结论正确解读

- **任务范围**：本文解决的是**增强子-启动子互作（EPI）的二分类预测**，输入仅为 DNA 序列（增强子+启动子），不涉及 3D 基因组结构、表观遗传修饰或染色质状态等额外信息。
- **Oracle/真值输入**：训练标签来自 TargetFinder 数据集的 Hi-C 实验注释，属于实验衍生的监督信号。
- **端到端状态**：模型是端到端训练的（序列→互作概率），但 TF 提取是**事后分析**（post-hoc），不参与训练损失。
- **算力成本**：embed-OneHot 编码将 GPU 内存从 ~4.9 GB 降至 ~1.9 GB，但具体训练时间未报告。
- **历史数据依赖**：模型依赖 TargetFinder 数据集的细胞系注释质量；不同细胞系的 Hi-C 数据分辨率可能影响标签质量。
- **模型依赖**：性能高度依赖 Transformer 的 multihead attention 配置（16 头）；TF 提取质量依赖 TOMTOM 比对阈值和 HOCOMOCO 数据库覆盖度。
- **最难情形**：模型在 GM78 和 NHEK 细胞系上表现相对较弱（原文 Fig. 4 中可见波动）；TF-TF 互作提取在注意力权重分散时可能失效。
- **群体/领域边界**：模型仅在 6 个人类细胞系上验证，未测试其他物种或疾病相关细胞类型；TF 提取依赖已知基序数据库，无法发现全新 TF。
- **不确定性**：未报告置信区间或多次运行的方差；TF-TF 互作的 75.6% BioGRID 支持率基于数据库现有注释，可能高估（未注释的互作被计为不支持）。

**有边界的复述**：DeepEPI 在 6 个人类细胞系的 EPI 预测任务上，以纯序列输入取得了优于现有方法的 AUROC/AUPR，并能通过注意力权重提取已知 TF 基序和 TF-TF 互作，其中约 3/4 的互作有 BioGRID 实验支持。该结论仅适用于所测试的细胞系和数据库覆盖范围，不构成对全基因组调控机制的普适性声明。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 直接验证 TF-TF 互作困难 | 缺乏实验资源直接验证增强子-启动子区域的 TF 互作 | 未来工作将进行实验验证 | Results 3.7: "direct comparison of our TF-TF interaction results remains challenging" |
| 依赖现有数据库 | TF 识别依赖 HOCOMOCO 数据库，TF-TF 验证依赖 BioGRID | 未明确提及 | Results 3.5, 3.6 |
| 编码方式权衡 | OneHot 编码缺乏特征间依赖，DNA2Vec 不可解释 | 探索其他编码方式，如 2LK encoding | Conclusion: "adopting 2LK encoding could prove advantageous in subsequent studies" |
| 细胞系特异性 | 不同细胞系表现有差异 | 未明确提及 | Results 3.4, Fig. 4 |

> 注：作者在文中未系统列出「Limitations」章节，以上为从 Results 和 Conclusion 中提取的明确表述。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| TF 提取依赖事后注意力分析，而非端到端学习 | 注意力权重高并不必然等于功能性 TF 结合位点；可能是序列统计偏差而非生物学信号 | 若注意力权重与真实 TF 结合位点相关性弱，则「可解释性」声明不成立 | 将注意力权重与 ChIP-seq 实验测得的 TF 结合位点做定量比较（如 AUC 或相关性） | Results 3.5 仅用 TOMTOM 比对和 BioGRID 验证，缺乏与 ChIP-seq 的直接对比 |
| 数据增强（序列平移）可能引入伪影 | 平移 50 bp 可能破坏真实的增强子-启动子空间关系，产生不自然的正样本 | 若增强样本不反映真实生物学变异，模型可能学习到平移伪影而非调控逻辑 | 在保持原始距离分布的独立测试集上评估增强模型的泛化性能 | Methods 2.1 未说明平移后序列的生物学合理性验证 |
| 与现有工具的比较可能不公平 | 不同工具使用不同的训练数据划分、编码方式和超参数，直接比较 AUROC/AUPR 可能受实现细节影响 | 若比较不公平，则「优于现有方法」的结论可能不稳健 | 使用统一的交叉验证协议和相同的超参数搜索空间重新实现所有基线 | Results 3.4 未报告各工具的复现细节 |
| 未报告统计显著性 | 各实验间的性能差异未给出置信区间或显著性检验 | 若无统计检验，微小的性能提升可能不具实际意义 | 在多次随机种子下重复实验并报告均值±标准差及显著性检验 | 全文未提及统计检验方法 |
| 6 种细胞系的选择可能偏向易预测的细胞类型 | 未说明细胞系选择标准；某些细胞系的 Hi-C 数据质量可能更高 | 若细胞系选择有偏，结论的泛化性受限 | 在更多样化的细胞系（包括疾病相关）上验证 | Methods 2.1 未提供细胞系选择理由 |
| TF-TF 互作验证依赖 BioGRID 的「物理互作」注释 | BioGRID 注释可能不完整，未注释的互作被误判为「不支持」 | 75.6% 的支持率可能低估真实互作比例 | 使用多个互作数据库（如 STRING、ENCODE）交叉验证 | Results 3.5 仅使用 BioGRID |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

| 知识候选 | 类型 | 可迁移性说明（面向 TF–DNA 结合机制 × AI/物理模拟） |
|----------|------|-----------------------------------------------------|
| **CNN+Transformer 的分工架构**：CNN 提取局部基序，Transformer 建模长程依赖 | 架构设计 | 可直接迁移到 TF–DNA 结合位点预测：CNN 识别结合基序，Transformer 捕获基序间的协同/距离关系 |
| **Multihead attention 作为可解释性出口**：注意力权重映射回序列位置 → PWM → TF 识别 | 可解释性方法 | 可用于任何序列-based TF 结合预测模型，将「黑盒预测」转化为「可验证的基序发现」 |
| **Embed-OneHot 编码**：嵌入层动态生成 OneHot 表示，兼顾可解释性与存储效率 | 编码策略 | 在需要可解释性（如基序可视化）且序列较长的 TF 结合预测任务中，可替代传统 OneHot 或词嵌入 |
| **事后 TF 提取流程**：训练后从注意力头提取 PWM → TOMTOM 比对 → 数据库验证 | 分析流程 | 可作为通用 pipeline 迁移到其他调控元件预测任务（如 ChIP-seq 峰内基序发现） |
| **数据增强 vs 损失加权的实证比较**：数据多样性比损失重加权更有效 | 训练策略 | 在 TF–DNA 结合数据不平衡时，优先考虑序列增强（如突变/平移）而非仅调整损失权重 |
| **跨细胞系联合训练 + 单细胞系微调**：先在合并数据上训练，再单独微调 | 训练策略 | 适用于多细胞系 TF 结合预测：共享调控语法 + 细胞系特异性微调 |
| **TF-TF 互作从注意力权重推断**：高注意力得分的 TF 对视为候选互作 | 生物学发现方法 | 可迁移到 TF 协同结合研究：从模型注意力中提取 TF 对共现模式，生成可实验验证的假设 |
| **验证流程：数据库交叉验证**：用 BioGRID 等数据库验证预测的 TF-TF 互作 | 验证策略 | 任何计算预测的 TF 互作都应通过多数据库交叉验证，避免单一数据库的注释偏差 |

---

## 15 与已有知识连接

- **TargetFinder (Whalen et al. 2016)**：本文的数据集来源。TargetFinder 首次系统比较了多种特征（DNase、ChIP-seq、组蛋白修饰等）对 EPI 预测的贡献，本文将其简化为纯序列输入，验证了序列信息本身的充分性。
- **EPIVAN (Hong et al. 2020)**：本文的主要对比基线。EPIVAN 使用 CNN+GRU+attention 和 DNA2Vec 编码，本文用 Transformer 替代 GRU，并引入 embed-OneHot 编码，在 AUPR 上提升 2.4%（DNA2Vec 条件下）。
- **EPI-Trans (Ahmed et al. 2024)**：纯 Transformer 的 EPI 预测模型。本文与之对比，显示 CNN+Transformer 混合架构在 AUROC 上略有优势（0.7%），且本文额外提供 TF 提取能力。
- **EPIANN (Mao et al. 2017)**：首个支持 TF 互作提取的 EPI 模型。本文在 TF 提取能力上与之对齐，但通过 Transformer 的 multihead attention 替代了 EPIANN 的注意力机制，提升了精度。
- **SPEED (Singh et al. 2019)**：CNN+LSTM 架构，从卷积核提取 PWM。本文的 TF 提取思路（从注意力权重构建 PWM）与 SPEED 的卷积核 PWM 提取互补，可视为两种不同的基序发现路径。
- **DanQ (Quang & Xie, 2016)**：CNN+LSTM 的经典调控基因组学模型。本文的 CNN+Transformer 可视为 DanQ 架构的现代升级，用 Transformer 替代 LSTM 捕获更长距离依赖。
- **Enformer (Avsec et al., 2021)**：基于 Transformer 的基因表达预测模型。本文与 Enformer 共享 Transformer 核心思想，但 Enformer 预测表达量而本文预测 EPI 二元互作，任务粒度不同。
- **TF–DNA 结合机制方向**：本文的 TF 提取方法（注意力权重 → PWM → TOMTOM）与传统的 ChIP-seq 基序发现（如 MEME-ChIP）形成互补——前者是模型驱动的无监督发现，后者是统计富集分析。两者可交叉验证。
- **物理模拟方向**：本文未涉及 MD 或对接，但其预测的 TF-TF 互作对可作为物理模拟（如蛋白-蛋白对接、MD 模拟）的候选体系，缩小模拟搜索空间。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：注意力引导的 TF–DNA 结合位点精细定位
- **名称**：Attention-Guided TFBS Refinement
- **来源局限/观察**：DeepEPI 从 5000 bp 序列中提取 TF，但注意力权重只能定位到约 246 个片段（每个约 20 bp），分辨率不足以精确到单个碱基对
- **核心假设**：通过更高分辨率的注意力图（如逐碱基注意力）或与 CNN 卷积核的 PWM 结合，可将 TF 结合位点定位到碱基对级别
- **增量**：将 DeepEPI 的「片段级」TF 提取升级为「碱基级」结合位点预测，直接对接 ChIP-seq 峰内基序发现
- **初步方法**：在 DeepEPI 的 Transformer 层后添加逐碱基注意力头，或用积分梯度（Integrated Gradients）替代注意力权重
- **验证方式**：与 ENCODE ChIP-seq 峰中心比较，计算预测位点与实验峰中心的距离分布
- **创新状态**：unverified

### 候选 2：TF-TF 互作预测的物理模拟验证
- **名称**：Computational Validation of TF-TF Interactions via Docking
- **来源局限/观察**：DeepEPI 预测的 172 个 TF-TF 互作中 75.6% 有 BioGRID 支持，但剩余 24.4% 可能是新互作或假阳性
- **核心假设**：未被 BioGRID 注释的 TF-TF 互作对中，有一部分可通过蛋白-蛋白对接（如 HADDOCK、ClusPro）获得结构支持
- **增量**：将深度学习预测与物理模拟结合，为预测的 TF-TF 互作提供结构层面的验证
- **初步方法**：选取 DeepEPI 预测的高置信度 TF-TF 对，提取蛋白结构（PDB 或 AlphaFold 预测），进行蛋白-蛋白对接，评估结合界面能量
- **验证方式**：对接得分与 BioGRID 注释的互作对比较；若未注释对的对接得分显著高于随机对，则支持其真实性
- **创新状态**：unverified

### 候选 3：跨细胞系 TF 结合特异性建模
- **名称**：Cell-Type-Specific TF Binding via Conditional Transformer
- **来源局限/观察**：DeepEPI 的 "best" 模型在合并数据上训练，但不同细胞系的 TF 结合谱不同（如 GATA1 在 K562 中富集）
- **核心假设**：通过细胞系条件编码（如 cell-type embedding），模型可学习细胞系特异的 TF 结合偏好
- **增量**：从「通用 EPI 预测」升级为「细胞系特异 TF 结合预测」，更贴近实际调控机制
- **初步方法**：在 DeepEPI 的输入中加入细胞系 one-hot 编码或可学习的 cell-type embedding，与序列特征融合
- **验证方式**：比较条件模型与通用模型在单细胞系测试集上的 AUPR；检查细胞系特异注意力权重是否对应已知的细胞系特异 TF
- **创新状态**：unverified

### 候选 4：从 EPI 预测到 TF–DNA 结合亲和力预测
- **名称**：EPI-to-Binding Affinity Transfer Learning
- **来源局限/观察**：DeepEPI 预测的是二元 EPI 互作，但 TF–DNA 结合本质上是连续亲和力（如 Kd 值）
- **核心假设**：EPI 预测任务中学到的序列特征可迁移到 TF–DNA 结合亲和力预测，通过迁移学习减少对实验亲和力数据的依赖
- **增量**：将 DeepEPI 的预训练权重迁移到小样本的 TF 结合亲和力数据集（如 SELEX、HT-SELEX），实现少样本亲和力预测
- **初步方法**：冻结 DeepEPI 的 CNN+Transformer 层，替换输出层为回归头，在亲和力数据上微调
- **验证方式**：预测 Kd 值与实验值的相关系数；与从头训练的模型比较样本效率
- **创新状态**：unverified

### 候选 5：注意力权重的可解释性基准测试
- **名称**：Attention Faithfulness Benchmark for TFBS Discovery
- **来源局限/观察**：DeepEPI 声称注意力权重能提取 TF，但未系统验证注意力权重与真实 TF 结合位点的定量关系
- **核心假设**：注意力权重与 TF 结合位点的重叠度可通过标准化指标（如 AUPRC over genomic positions）量化
- **增量**：为「注意力即解释」提供定量基准，推动该领域从定性展示走向可验证的评估
- **初步方法**：在多个细胞系上，将 DeepEPI 的注意力权重与 ENCODE ChIP-seq 峰比较，计算逐位置 AUPRC；与随机注意力、梯度归因等方法对比
- **验证方式**：注意力 AUPRC 是否显著高于随机基线；是否与模型预测性能相关
- **创新状态**：unverified