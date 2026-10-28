## 01 基本信息

- **标题**：Predicting Transcription Factor Binding Sites using Transformer based Capsule Network
- **作者**：Nimisha Ghosh; Daniele Santoni; Indrajit Saha; Giovanni Felici
- **单位**：未提供（通讯作者邮箱：ghosh.nimisha@gmail.com）
- **期刊/平台**：arXiv 预印本
- **年份**：2023-10-23（v2）
- **论文类型**：方法学（Method）论文
- **领域**：生物信息学 / 深度学习 / 转录因子结合位点预测
- **关键词**：Transcription Factor Binding Sites (TFBS)、DNABERT、Capsule Network、ChIP-seq、Deep Learning
- **DOI/arXiv 号**：arXiv:2310.15202v2
- **代码**：https://github.com/NimishaGhosh/DNABERT-Cap/tree/main
- **数据**：ENCODE 数据库中五个细胞系（A549, GM12878, Hep-G2, H1-hESC, Hela）的 ChIP-seq 数据集
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」方向，具体为基于预训练 DNA 语言模型（DNABERT）结合胶囊网络（Capsule Network）进行 TFBS 序列级二分类预测。其核心贡献在于将 Transformer 架构与胶囊网络结合，利用胶囊层的 part-whole 关系编码能力提升 TFBS 预测性能，属于序列特征提取与分类方法创新，而非物理模拟或结构预测类工作。

## 02 一句话总结

本文提出 DNABERT-Cap 模型，将预训练 DNABERT（6-mer tokenization）作为序列编码器，依次连接卷积层、BiLSTM 层和胶囊层，在 ENCODE 五个细胞系的 ChIP-seq 基准数据上实现 TFBS 二分类预测，平均 AUC 超过 0.91，优于 DeepARC、DeepTF、CNN-Zeng 和 DeepBind 等现有方法。

## 03 研究问题

- **具体问题**：如何利用深度学习模型从 DNA 序列中准确预测转录因子结合位点（TFBS）？
- **为什么重要**：TFBS 的准确预测对于理解基因表达调控机制、疾病相关变异的功能注释以及治疗靶点的发现至关重要。实验方法（如 ChIP-seq）成本高、耗时久，计算预测方法可大规模补充实验数据。
- **现有方法不足**：
  - 传统机器学习（如 kmerHMM、gkm-SVM）依赖手工特征提取，难以处理大规模数据。
  - 现有深度学习方法（如 DeepBind、DeepSEA、DeepARC）虽表现良好，但 DeepARC 在编码策略上存在不足；多数方法未充分利用序列的 part-whole 层次关系。
  - Transformer 在 TFBS 预测中的应用有限，且现有方法未将胶囊网络的动态路由机制引入该任务。
- **精确研究问题**：Can a transformer-based capsule network (DNABERT-Cap) outperform existing deep learning predictors in identifying TFBSs from ChIP-seq derived DNA sequences across multiple cell lines?

## 04 背景与发展脉络

> 注：以下脉络基于本文引言及参考文献构建，标注为「经外部核验」的部分来自文中引用的文献信息，其余为本文框架。

1. **传统机器学习阶段**（经外部核验）：
   - kmerHMM（Wong et al. 2013）：基于 HMM 的 motif 建模。
   - gkm-SVM（Ghandi et al. 2014）：基于 k-mer 核函数的 SVM。
   - 局限：依赖手工特征，难以处理大规模数据。

2. **深度学习早期阶段**（经外部核验）：
   - DeepBind（Alipanahi et al. 2015）：首个大规模深度学习 TFBS 预测器，CNN 架构。
   - DeepSEA（Zeng et al. 2016b）：多任务 CNN，预测染色质特征。
   - DanQ（Quang and Xie 2016）：CNN + BiLSTM 混合架构。
   - 局限：CNN 池化操作丢失位置信息，难以建模长程依赖。

3. **混合架构与编码优化阶段**（经外部核验）：
   - DeeperBind（Hassanzadeh and Wang 2016）：LSTM 增强的 CNN。
   - DeepSite（Zhang et al. 2020）：CNN + BiLSTM 捕获长程依赖。
   - DeepARC（Cao et al. 2022）：CNN + RNN，结合 OneHot 与 DNA2Vec 编码。
   - 局限：编码策略不完善，未充分利用预训练模型。

4. **Transformer 与胶囊网络阶段**（本文位置）：
   - DNABERT（Ji et al. 2021）：预训练 DNA 语言模型，6-mer 表现最佳。
   - 胶囊网络（Sabour et al. 2017；Hinton et al. 2018）：动态路由保留 part-whole 关系。
   - 本文主张：将 DNABERT 与胶囊网络结合，通过联合优化实现更优的 TFBS 预测。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 传统机器学习特征工程瓶颈 | kmerHMM、gkm-SVM 等依赖手工特征，处理大规模数据困难 | 手工特征无法充分捕获序列的复杂模式 | Introduction 第 1 段 |
| CNN 池化丢失位置信息 | 传统 CNN 在池化过程中丢失特征的空间位置关系 | 池化操作只保留最显著特征，忽略 part-whole 关系 | Section 2.2 胶囊网络部分 |
| 现有深度学习方法编码策略不足 | DeepARC 等模型在序列编码上存在局限 | 未采用预训练模型，编码方式单一 | Introduction 最后一段 |
| Transformer 在 TFBS 预测中应用有限 | 基于 Transformer 的 TFBS 预测工作较少 | 领域内尚未充分探索预训练 DNA 语言模型的潜力 | Introduction 整体论述 |
| 长程依赖捕获不足 | 单一 CNN 难以建模序列中远距离 k-mer 间的关系 | CNN 感受野有限，无法捕获全局上下文 | Section 2.3 BiLSTM 层描述 |

## 06 核心思想

### 1) 表面方法

构建一个端到端的深度学习流水线：DNA 序列 → 6-mer tokenization → DNABERT 预训练编码器 → 卷积层（CL）→ BiLSTM 层 → 胶囊层（Primary Capsule + Dynamic Routing + TFBS Capsule）→ 二分类输出（有/无 TFBS）。

### 2) 核心洞察

- **预训练 DNA 语言模型提供丰富的上下文表示**：DNABERT 通过多头自注意力机制捕获 k-mer 的双向上下文依赖，比 OneHot 或 DNA2Vec 等静态编码更丰富。
- **胶囊网络保留 part-whole 层次关系**：传统 CNN 的池化操作丢失位置信息，而胶囊网络通过动态路由机制显式建模低层特征与高层特征之间的 part-whole 关系，这对 TFBS 这种由多个 motif 组合决定的序列特征尤为重要。
- **联合优化多层特征**：卷积层提取局部空间特征，BiLSTM 捕获长程依赖，胶囊层整合这些特征并输出类别概率，各层互补。

### 3) 可能的普适教训 [Analysis]

- 将预训练语言模型（如 DNABERT）作为通用序列编码器，再叠加任务特定的结构（如胶囊层），是提升生物序列预测性能的有效范式。
- 胶囊网络的动态路由机制在序列任务中可能比传统池化更有效地保留特征的空间/顺序关系，值得在 TF–DNA 结合机制研究中进一步探索。
- 多细胞系联合评估（而非单细胞系）是验证 TFBS 预测模型泛化能力的重要实验设计。

## 07 方法总览

- **输入**：长度为 101 bp 的 DNA 序列（正样本为 ChIP-seq 峰中心序列，负样本为保持二核苷酸频率的正样本重排序列）
- **输出**：二分类概率（该序列是否包含 TFBS）
- **主要模块**：
  1. Tokenization：6-mer 切分
  2. DNABERT 编码器：12 层 Transformer，768 hidden units，12 注意力头
  3. 卷积层（CL）：64 个滤波器，kernel size 2，提取局部空间特征
  4. BiLSTM 层：64 个隐藏单元，捕获双向长程依赖
  5. Primary Capsule 层：将 BiLSTM 输出转换为胶囊向量
  6. Dynamic Routing（3 次迭代）：在胶囊间建立 part-whole 连接
  7. TFBS Capsule 层：2 个类别胶囊（有/无 TFBS）
- **损失函数**：Separate margin loss（Sabour et al. 2017），m⁺=0.9，m⁻=0.1，λ 调节缺失类权重
- **优化器**：Adam
- **训练/验证/测试划分**：70% / 10% / 20%
- **数据规模**：每个细胞系 500,000 条序列
- **硬件**：NVIDIA GA100 GPU
- **流程**：序列 → 6-mer 切分 → DNABERT 嵌入 → 卷积 → BiLSTM → 胶囊层 → 动态路由 → 类别胶囊 → 分类输出

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| DNABERT 编码器 | 生成 k-mer 的双向上下文嵌入 | 提供比静态编码更丰富的序列表示 | 输入：6-mer token 序列；输出：d×l 嵌入矩阵 | 文中称 DNABERT 6-mer 表现最佳（引用 Ji et al. 2021） | 预期显著降低表示质量（未做消融） |
| 卷积层（CL） | 提取局部空间特征图 | 捕获 k-mer 间的局部模式 | 输入：DNABERT 嵌入；输出：η 通道特征图 | Baseline-3 移除 BiLSTM 保留 CL，性能低于完整模型 | 预期丢失局部模式提取能力（未做单独消融） |
| BiLSTM 层 | 捕获序列双向长程依赖 | 建模 k-mer 间的远距离上下文关系 | 输入：卷积特征图；输出：t×2dim 隐藏状态矩阵 | Baseline-3 移除 BiLSTM 后性能下降，作者归因于 BiLSTM 的贡献 | 实测：移除后性能下降（Baseline-3 对比） |
| Primary Capsule 层 | 将特征向量转换为胶囊向量 | 保留特征的空间/顺序信息 | 输入：BiLSTM 隐藏状态；输出：胶囊序列 | 文中描述胶囊网络优势 | 预期丢失 part-whole 编码能力（未做单独消融） |
| Dynamic Routing | 迭代确定低层到高层的连接权重 | 替代池化，保留 part-whole 关系 | 输入：primary capsules；输出：路由权重 | 文中引用 Sabour et al. 2017 | 预期降低胶囊层效果（未做单独消融） |
| TFBS Capsule 层 | 输出两个类别胶囊 | 最终分类决策 | 输入：路由后的胶囊；输出：2 个类别向量 | 文中描述 | 预期无法输出分类结果（未做消融） |
| Margin Loss | 计算分类损失 | 训练模型区分正负样本 | 输入：类别胶囊长度；输出：损失值 | 文中引用 Sabour et al. 2017 | 预期训练不稳定（未做消融） |

> 注：文中仅通过 Baseline-2（移除胶囊层）和 Baseline-3（移除 BiLSTM）进行了部分消融，未对每个模块单独消融。

## 09 关键公式符号

**1. DNABERT 多头自注意力机制**（Section 2.2，公式 1-2）：

Attention(Q, K, V) = softmax(QK^T / √d_k) V

- Q, K, V：查询、键、值矩阵
- d_k：键向量的维度
- 多头注意力并行执行 T 次（T = Transformer 层数 = 12）

**2. 卷积层特征提取**（Section 2.3，公式 3-4）：

α_i = pool(σ(W_i * X + b_i))

- α_i：第 i 个输出特征图
- W_i：第 i 个卷积核
- b_i：偏置
- σ：激活函数
- pool(·)：池化操作
- *：卷积操作

**3. 胶囊网络 Squash 函数**（Section 2.3，公式 10）：

v_y = (‖s_y‖² / (1 + ‖s_y‖²)) · (s_y / ‖s_y‖)

- v_y：胶囊 y 的输出向量
- s_y：胶囊 y 的总输入

**4. 动态路由耦合系数**（Section 2.3，公式 11-13）：

s_y = Σ_x c_xy · û_{y|x}

c_xy = softmax(b_xy)

b_xy ← b_xy + v_y · û_{y|x}

- û_{y|x}：低层胶囊 x 对高层胶囊 y 的预测向量
- c_xy：耦合系数
- b_xy：对数先验概率
- v_y · û_{y|x}：一致性度量（标量积）

**5. Margin Loss**（Section 2.3，公式 14）：

L_b = T_b · max(0, m⁺ - ‖v_b‖)² + λ(1 - T_b) · max(0, ‖v_b‖ - m⁻)²

- T_b：类别 b 的 ground truth 指示符（1 或 0）
- m⁺ = 0.9，m⁻ = 0.1
- λ：缺失类权重调节参数

## 10 实验设计与证据链

**数据集**：
- 来源：ENCODE 数据库 ChIP-seq 数据
- 细胞系：A549, GM12878, Hep-G2, H1-hESC, Hela（共 5 个）
- 样本量：每个细胞系 500,000 条序列（正负各半，负样本为保持二核苷酸频率的重排序列）
- 序列长度：101 bp
- 划分：70% 训练 / 10% 验证 / 20% 测试

**指标**：Accuracy, Recall, Specificity, MCC, AUC

**基线**：
- Baseline-1：微调 DNABERT + 分类层
- Baseline-2：DNABERT + CL + BiLSTM + 交叉熵损失（无胶囊层）
- Baseline-3：DNABERT + CL + 胶囊层（无 BiLSTM）

**对比方法**：DeepARC, DeepTF, CNN-Zeng, DeepBind

**实验表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 与基线对比 | 胶囊层和 BiLSTM 的贡献 | DNABERT-Cap vs Baseline-1/2/3，5 细胞系 | DNABERT-Cap 在 Accuracy, Specificity, MCC, AUC 上优于所有基线；Baseline-3 在 Recall 上略优 | 胶囊层 + BiLSTM 联合提升整体性能 | 无法分离胶囊层和 BiLSTM 各自的独立贡献 | Table 1, Section 3.2 |
| 与 SOTA 对比 | DNABERT-Cap 优于现有方法 | vs DeepARC, DeepTF, CNN-Zeng, DeepBind，5 细胞系平均 | DNABERT-Cap 在 Accuracy, Specificity, MCC, AUC 上最优；DeepARC 在 Recall 上最优 | DNABERT-Cap 综合性能最佳 | 未报告统计显著性检验 | Table 2, Section 3.3 |
| AUC 曲线可视化 | 模型判别能力 | 5 细胞系各一次运行的 ROC 曲线 | A549: 0.925, GM12878: 0.913, Hep-G2: 0.930, H1-hESC: 0.914, Hela: 0.917 | 各细胞系 AUC 均 > 0.91 | 单次运行，非多次平均 | Supplementary Figure S1, Section 3.2 |

**关键数值**：
- 平均 Accuracy > 83%（Conclusion 提及）
- 平均 AUC > 0.91（所有 5 个细胞系）
- 与 DeepARC 相比：Accuracy 提升 1.11%，Specificity 提升 0.01%，MCC 提升 2.2%，AUC 提升 1.10%（Section 3.3）

## 11 结论正确解读

- **任务范围**：本文解决的是**序列级二分类**问题——判断一条 101 bp DNA 序列是否包含 TFBS，而非**核苷酸级定位**或**基序发现**。
- **数据边界**：模型仅在 5 个特定细胞系的 ChIP-seq 数据上评估，未覆盖全部细胞类型或全部 TF。
- **性能声明**：平均 AUC > 0.91 和 Accuracy > 83% 是在该特定数据集划分下的结果，未报告跨数据集外部验证。
- **对比范围**：与 DeepARC、DeepTF、CNN-Zeng、DeepBind 相比综合最优，但未与最新的 Transformer 类方法（如 Enformer、Borzoi）对比。
- **机制解释**：作者将性能提升归因于 DNABERT 的上下文表示 + 胶囊层的 part-whole 编码 + BiLSTM 的长程依赖捕获，但未提供注意力可视化或胶囊路由分析等直接证据。
- **端到端状态**：模型是端到端训练的（DNABERT 微调 + 下游层联合优化），但 DNABERT 本身是预训练模型。
- **不确定性**：未报告置信区间、方差或多次运行的统计检验。

## 12 作者自认局限

在提供的材料中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限）：
- 数据选择：仅基于资源可用性随机选择 500,000 条序列（Section 2.1），可能引入采样偏差。
- 计算资源：实验在 NVIDIA GA100 GPU 上进行（Acknowledgments），未讨论推理效率或资源需求。
- 未来方向：作者提及可考虑将其他特征（如 DNA shape）纳入模型（Discussion 隐含），但未明确展开。

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|-------------------|----------|----------|------|
| 未报告统计显著性检验 | 性能差异可能不显著，尤其是与 DeepARC 的差距较小（Accuracy 仅 1.11%） | 影响结论可靠性 | 进行配对检验（如 McNemar 检验）或报告多次运行的均值和标准差 | Table 2 数据 |
| 负样本生成方式可能引入偏差 | 保持二核苷酸频率的重排序列可能过于简单，导致模型学习到序列组成而非真实 TFBS 特征 | 高估模型在真实基因组上的性能 | 使用真实非结合位点序列作为负样本进行验证 | Section 2.1 |
| 未与最新 Transformer 方法对比 | Enformer、Borzoi 等模型可能表现更优 | 无法确定 DNABERT-Cap 在当前 SOTA 中的位置 | 补充与这些方法的对比实验 | Section 3.3 对比列表 |
| 缺乏注意力/路由机制分析 | 作者声称胶囊层编码 part-whole 关系，但未提供可视化或定量证据 | 机制解释缺乏直接支持 | 可视化路由权重、注意力模式，或进行扰动实验 | Section 4 Discussion |
| 单次运行报告 AUC 曲线 | Supplementary Figure S1 为单次运行结果，可能不代表平均性能 | 影响结果可重复性 | 报告多次运行的 AUC 分布 | Section 3.2 |
| 未报告模型参数量和推理时间 | 实际部署时计算成本未知 | 影响实用性评估 | 补充模型复杂度分析 | 全文未提及 |
| 5 个细胞系的选择依据不明确 | 可能偏向于易于预测的细胞系 | 影响泛化性结论 | 在更多样化的细胞系和 TF 上验证 | Section 2.1 |

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **预训练 DNA 语言模型 + 任务特定头的范式**：DNABERT 作为通用序列编码器，叠加 CL + BiLSTM + Capsule 的混合架构，为 TF–DNA 结合预测提供了「预训练 + 微调」的可行路径。可迁移到本课题：使用更先进的基因组基础模型（如 Nucleotide Transformer、Enformer）替换 DNABERT，评估不同预训练模型对 TFBS 预测的影响。

2. **胶囊网络在序列任务中的潜力**：动态路由机制替代池化操作，保留 part-whole 关系，这对 TFBS 这种由多个 motif 协同决定的序列特征可能特别有效。可迁移到本课题：探索胶囊网络在 motif 发现、结合位点定位（而非仅序列分类）中的应用。

3. **多细胞系联合评估设计**：在 5 个不同细胞系上评估模型，可检验跨细胞类型的泛化能力。可迁移到本课题：设计跨细胞系、跨 TF 的评估协议，避免单细胞系过拟合。

4. **消融实验的层次化设计**：通过 Baseline-1/2/3 逐步移除组件（分类头、胶囊层、BiLSTM），可定位各模块贡献。可迁移到本课题：在 TF–DNA 结合预测中系统消融各组件，明确哪些模块对性能提升最关键。

5. **负样本生成策略**：保持二核苷酸频率的重排序列作为负样本，可控制序列组成偏差。可迁移到本课题：在训练 TF–DNA 结合模型时，采用更严格的负样本控制（如匹配 GC 含量、重复序列含量）以避免混淆因素。

6. **性能指标选择**：使用 Accuracy、Recall、Specificity、MCC、AUC 多指标联合评估，MCC 对类别不平衡更稳健。可迁移到本课题：在 TFBS 预测中优先报告 MCC 和 AUC，而非仅 Accuracy。

7. **代码和数据公开**：提供 GitHub 仓库和 ENCODE 数据来源，便于复现和扩展。可迁移到本课题：建立标准化的基准数据集和评估协议，促进领域内方法比较。

## 15 与已有知识连接

1. **DNABERT（Ji et al. 2021）**：本文直接构建于 DNABERT 之上，使用其 6-mer 预训练模型。DNABERT 本身是基于 BERT 架构的 DNA 语言模型，在多种基因组任务上表现优异。本课题可参考其预训练策略和 tokenization 选择。

2. **Capsule Network（Sabour et al. 2017；Hinton et al. 2018）**：胶囊网络最初用于图像分类，本文将其引入生物序列分析。动态路由机制的核心思想——用向量替代标量、用路由替代池化——可迁移到 TF–DNA 结合的结构建模中。

3. **DeepBind（Alipanahi et al. 2015）**：深度学习预测 TFBS 的开创性工作，本文将其作为主要对比基线。DeepBind 的 CNN 架构和序列特异性建模思路是本课题的基础参考。

4. **DeepARC（Cao et al. 2022）**：结合 CNN + RNN 和 DNA2Vec 编码的近期工作，本文直接对比并指出其在编码策略上的不足。本课题可参考其混合架构设计。

5. **ENCODE 项目（enc 2012）**：数据来源，ChIP-seq 是 TF–DNA 结合实验的金标准。本课题可扩展使用 ENCODE 的其他细胞系和 TF 数据。

6. **DanQ（Quang and Xie 2016）**：CNN + BiLSTM 的混合架构，本文的 BiLSTM 层设计与之相关。本课题可参考其多任务学习框架。

7. **DeepSEA（Zeng et al. 2016b）**：多任务 CNN 预测染色质特征，本文的数据预处理（正负样本生成）沿用其策略。本课题可参考其数据增强和负样本控制方法。

8. **[Analysis] 与物理模拟方法的潜在连接**：本文纯序列方法未涉及结构信息。本课题若结合 AlphaFold 预测的 TF 结构或 MD 模拟的 TF–DNA 结合构象，可将序列特征与结构特征融合，可能进一步提升预测精度。

## 16 研究想法

> 标题：Agent 生成的研究候选

**候选 1：基于 DNABERT-Cap 的核苷酸级 TFBS 定位**
- **来源局限/观察**：本文仅做序列级二分类，未定位具体结合位点。
- **核心假设**：胶囊层的 part-whole 编码能力可迁移到核苷酸级标注任务，精确定位 TFBS 边界。
- **初步方法**：将 DNABERT-Cap 的胶囊输出层改为序列标注头（如 CRF 或逐位置分类），在 ENCODE 的 peak 边界数据上训练。
- **验证方式**：与 DeepSNR、DeepFinder 等核苷酸级方法对比，使用 AUC、F1 和定位精度指标。
- **创新状态**：unverified

**候选 2：融合 DNA shape 特征的 TF–DNA 结合预测**
- **来源局限/观察**：本文仅使用序列信息，未考虑 DNA 三维结构特征（如 minor groove width、roll、helix twist）。
- **核心假设**：DNA shape 特征与序列特征互补，可提升 TFBS 预测精度，尤其对结合特异性弱的 TF。
- **初步方法**：使用 DNAshape 工具计算 101 bp 序列的 shape 特征，与 DNABERT 嵌入拼接后输入胶囊网络。
- **验证方式**：与本文结果对比，检验 Accuracy、AUC 提升；在已知 shape 敏感的 TF（如 bHLH 家族）上重点评估。
- **创新状态**：unverified

**候选 3：跨细胞系 TFBS 预测的迁移学习框架**
- **来源局限/观察**：本文在 5 个细胞系上独立训练，未利用跨细胞系共享信息。
- **核心假设**：不同细胞系的 TFBS 模式存在共享和特异部分，迁移学习可提升低资源细胞系的预测性能。
- **初步方法**：在多个细胞系上预训练 DNABERT-Cap，然后在目标细胞系上微调；或使用多任务学习同时预测多个细胞系。
- **验证方式**：在样本量较少的细胞系上评估，对比独立训练与迁移学习的性能差异。
- **创新状态**：unverified

**候选 4：结合 TF 蛋白序列信息的跨 TF 泛化**
- **来源局限/观察**：本文模型针对特定细胞系训练，未利用 TF 蛋白本身的序列或结构信息。
- **核心假设**：将 TF 蛋白的嵌入（如 ESM-2 或 ProtBERT 表示）与 DNA 序列嵌入联合建模，可实现对新 TF 的零样本或少样本预测。
- **初步方法**：设计双编码器架构，DNA 序列经 DNABERT 编码，TF 蛋白序列经蛋白语言模型编码，融合后输入胶囊层分类。
- **验证方式**：在训练中未见的 TF 上测试，评估零样本泛化能力。
- **创新状态**：unverified

**候选 5：胶囊路由权重作为 motif 可解释性指标**
- **来源局限/观察**：本文未分析胶囊层学到的特征是否对应已知 motif。
- **核心假设**：动态路由的耦合系数可揭示对分类贡献最大的 k-mer 组合，对应已知或新 motif。
- **初步方法**：提取路由权重，与 JASPAR 数据库的已知 motif 比对；可视化高权重 k-mer 的序列 logo。
- **验证方式**：与 MEME 等 motif 发现工具的结果对比，检验发现的 motif 是否与实验验证的一致。
- **创新状态**：unverified

**候选 6：DNABERT-Cap 与 MD 模拟的混合框架**
- **来源局限/观察**：本文纯序列方法无法捕获 TF–DNA 结合的三维构象变化。
- **核心假设**：序列预测结果可作为 MD 模拟的候选筛选器，减少模拟成本；MD 模拟的结构特征可反馈提升序列模型。
- **初步方法**：先用 DNABERT-Cap 筛选高置信度候选序列，对 top 候选进行 TF–DNA 对接和 MD 模拟，验证结合稳定性；将模拟得到的结合自由能作为额外特征训练排序模型。
- **验证方式**：对比纯序列预测与混合框架的预测精度；检验 MD 模拟是否发现序列模型无法区分的结合差异。
- **创新状态**：unverified