## 01 基本信息

- **标题**：E(3) equivariant graph neural networks for robust and accurate protein–protein interaction site prediction
- **作者与单位**：Rahmatullah Roche; Bernard Moussad; Md Hossain Shuvo; Debswapna Bhattacharya（美国密苏里大学，Bhattacharya Lab）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2022-12-16
- **论文类型**：方法学（Method）论文，提出新模型 EquiPPIS
- **领域**：结构生物信息学 × 深度学习（几何图神经网络）
- **关键词**：E(3) equivariant graph neural network; protein–protein interaction (PPI) site prediction; AlphaFold2; symmetry-aware deep learning
- **DOI/arXiv 号**：10.1101/2022.12.14.520476
- **代码**：https://github.com/Bhattacharya-Lab/EquiPPIS （GNU GPL v3）
- **数据**：Dset_186、Dset_72、Dset_164（合并去冗余后 Train_335 / Test_60 / Validation_42），原始数据来自 https://github.com/biomed-AI/GraphPPIS
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文聚焦 **蛋白质–蛋白质互作（PPI）位点预测**，而非 TF–DNA 互作。但其核心方法——**E(3) 等变图神经网络（EGCL）** 直接利用 3D 坐标（Cα 原子）进行等变消息传递，并验证了**用 AlphaFold2 预测结构替代实验结构**的可行性——这两点对 TF–DNA 结合位点预测（尤其是基于预测结构的 DNA 结合残基识别）具有高度可迁移性。本文属于「几何深度学习 × 互作位点预测」方向，是 TF–DNA 互作 × AI 方法可借鉴的邻近领域工作。

---

## 02 一句话总结

本文提出 EquiPPIS——一个基于 E(3) 等变图神经网络（EGCL）的 partner-independent PPI 位点预测模型，直接以 Cα 坐标作为等变输入，在实验结构上显著超越现有方法，且使用 AlphaFold2 预测结构时仍优于现有方法使用实验结构的精度，证明了等变架构对互作位点预测的鲁棒性和可扩展性。

---

## 03 研究问题

- **具体问题**：在 partner-independent 设定下（仅给定单个蛋白结构，无伴侣/复合物信息），如何准确预测蛋白质表面的互作界面残基（PPI sites）？
- **为什么重要**：PPI 是几乎所有生物过程的核心，但实验表征昂贵且耗时；计算预测可高通量补充实验，且 partner-independent 预测不依赖伴侣结构，适用范围更广。
- **现有方法不足**：
  - 多数现有方法依赖实验解析结构，无法扩展到无实验结构的蛋白；
  - 基于图卷积的方法（如 GraphPPIS）只利用残基对距离（distance maps），**忽略 3D 空间中的对称性**（旋转、平移、反射），即不具备等变性；
  - 非等变模型需要大量数据增强来近似学习对称性，效率低且泛化差。
- **精确研究问题（Can ... ?）**：Can an E(3) equivariant graph neural network that directly consumes 3D coordinates achieve state-of-the-art partner-independent PPI site prediction accuracy, and can it generalize to AlphaFold2-predicted structures without significant performance loss?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 与 References 的叙述，属于「仅本文框架」，未经外部独立核验。

1. **早期机器学习时代**：基于手工特征工程 + 传统分类器（如 PSIVER 用 Naïve Bayes + 核密度估计）。
2. **深度学习序列方法**：利用序列信息（如 PSSM、进化信息）的神经网络方法（如 DLPred 用 LSTM、DELPHI 用 CNN+RNN 集成），但精度有限。
3. **结构感知方法**：引入实验结构信息，如 DeepPPISP（CNN）、SPPIDER（SVM+NN+LD）、MaSIF-site（几何深度学习）、GraphPPIS（图卷积网络，利用 distance maps）。
4. **AlphaFold2 突破（CASP14）**：高精度单链结构预测成为可能，引发「用预测结构替代实验结构」的下游任务迁移问题。
5. **等变图神经网络兴起**：E(n) 等变图神经网络（EGCL, Satorras et al. 2021）和 SE(3) 等变网络（Fuchs et al. 2020）在分子建模中展现优势，但尚未被用于 PPI 位点预测。
6. **本文位置**：首次将 E(3) 等变图神经网络引入 partner-independent PPI 位点预测，并系统验证等变性带来的精度增益和对预测结构的鲁棒性。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 现有方法依赖实验结构 | 无法扩展到无实验结构的蛋白；预测结构输入时精度显著下降 | 模型在实验结构上训练，未见过预测结构的噪声/误差分布 | Results 表 2：GraphPPIS 用 AlphaFold2 结构时 PR-AUC 从 0.429 降至 0.399 |
| 图卷积忽略 3D 对称性 | 需要大量数据增强近似学习旋转/平移不变性，效率低 | 标准 GCN/GAT 只做 permutation equivariance，不保证 E(3) 等变 | Results 图 3a-3d：GCN/GAT 基线精度远低于 EquiPPIS |
| 距离图（distance maps）信息不足 | 只编码残基对距离，丢失方向、取向等几何信息 | GraphPPIS 仅用 Cα 距离作为空间信息 | Results 图 3：EquiPPIS 直接使用 Cα 坐标，优于 GraphPPIS |
| 互作位点预测对构象变化敏感 | 结合前后（bound/unbound）结构差异导致精度下降 | 蛋白结合伴随 induced fit / conformational selection 构象变化 | Results 图 3e-3f：UBtest_31 上 MaSIF-site 和 GraphPPIS 分别有 35% 和 14.6% 的 MCC 下降 |
| 等变性带来的精度增益未被验证 | 缺乏对等变架构 vs 非等变架构的系统对比 | 尚无工作将 E(3) 等变 GNN 用于 PPI 位点预测 | Results「Analyzing the importance of equivariance」节 |

---

## 06 核心思想

### 1) 表面方法
构建一个端到端的 E(3) 等变图神经网络（EquiPPIS），输入为单链蛋白的 Cα 坐标 + 序列/结构特征，输出为每个残基的 PPI 位点概率。网络堆叠 10 层 EGCL，每层同时更新节点嵌入和坐标嵌入，最后通过线性层 + sigmoid 做二分类。

### 2) 核心洞察
- **等变性是 3D 分子数据的先验知识**：蛋白的互作位点预测应与整体旋转、平移、反射无关。EGCL 通过设计等变的消息传递和坐标更新，**从几何第一性原理出发**编码这种对称性，无需数据增强。
- **坐标本身是特征**：与 GraphPPIS 只使用距离图不同，EquiPPIS 直接消费 Cα 坐标，让网络在等变约束下自由学习方向、取向等几何关系，信息量更大。
- **等变模型对预测结构更鲁棒**：因为等变架构对坐标噪声/误差的响应更「结构化」（保持对称性），所以对 AlphaFold2 预测结构的误差更不敏感。

### 3) 可能的普适教训 [Analysis]
- 对 TF–DNA 互作位点预测：DNA 结合残基的识别同样具有 3D 旋转/平移对称性，E(3) 等变架构天然适配；且 AlphaFold2 预测的 TF 结构可作为输入，避免对实验结构的依赖。
- 「用预测结构做下游任务」时，模型对结构误差的鲁棒性应作为核心设计指标，而非仅追求实验结构上的精度。
- 等变模型不仅提升精度，还减少数据增强需求，这对数据稀缺的 TF–DNA 互作数据集尤为重要。

---

## 07 方法总览

- **输入**：单链蛋白结构（Cα 坐标）+ 序列特征（one-hot 氨基酸类型、PSSM、ESM2 嵌入）+ 结构特征（SS、RSA、局部几何、取向、接触数、相对位置、虚拟表面积）
- **输出**：每个残基的 PPI 位点概率（0-1）
- **图构建**：残基为节点，Cα 距离 ≤ 14Å 且序列间隔 ≥ 6 的残基对为边
- **核心模块**：
  1. 图构建与特征工程模块
  2. 10 层 EGCL 堆叠的等变图神经网络（每层含等变消息传递 + 坐标更新 + 注意力聚合）
  3. 输出层（线性变换 + sigmoid）
- **训练**：二元交叉熵损失，Adam 优化器（lr=1e-4，weight decay=1e-16），余弦退火调度，最多 50 epochs，NVIDIA A40 GPU
- **框架**：PyTorch 1.12.0 + Deep Graph Library (DGL) 0.9.0
- **文字流程**：输入蛋白结构 → 提取 Cα 坐标和序列/结构特征 → 按距离阈值构建图 → 将节点特征、边特征、坐标输入 EGCL 堆叠 → 每层更新节点嵌入和坐标嵌入（等变约束下）→ 最后一层节点嵌入经线性变换 + sigmoid → 得到每个残基的 PPI 位点概率

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 图构建模块 | 将蛋白结构转为图（节点=残基，边=空间邻近残基对） | 图神经网络需要图结构输入；距离阈值 14Å 和序列间隔 ≥6 过滤短程冗余 | 输入：Cα 坐标；输出：图 G=(V,E) | Methods「Graph representation and featurization」节 | 预期影响：阈值过小丢失长程互作信息，过大引入噪声边 [Analysis] |
| 序列特征编码 | one-hot 氨基酸类型、PSSM、ESM2 嵌入 | 提供进化保守性和序列上下文信息，PSSM 和 ESM2 是互作位点预测的强特征 | 输入：序列；输出：L×73 特征矩阵 | Methods 节；Results 图 4a 消融实验 | 实测：移除 PSSM 或 ESM2 均导致精度下降（图 4a） |
| 结构特征编码 | SS（3/8-state）、RSA（2/8-state）、局部几何、取向、接触数、相对位置、虚拟表面积 | 提供局部构象和残基环境信息，补充序列特征 | 输入：结构；输出：L×45 特征矩阵 | Methods 节；Results 图 4a 消融实验 | 实测：移除结构特征导致精度下降（图 4a） |
| EGCL 等变卷积层（×10） | 等变消息传递 + 坐标更新 + 注意力聚合 | 核心创新：保证 E(3) 等变性，直接消费 3D 坐标 | 输入：节点嵌入、边特征、坐标；输出：更新后的节点嵌入和坐标 | Results「Analyzing the importance of equivariance」节 | 实测：关闭坐标更新（EquiPPIS invariant）后 ROC-AUC 降至 0.8 以下（图 3a-3d） |
| 注意力机制 | 在等变消息传递中加权聚合邻居信息 | 提升表达力，区分不同邻居的重要性 | 输入：聚合消息嵌入；输出：注意力加权嵌入 | Methods 节；EquiPPIS w/o attention 基线 | 实测：关闭注意力后精度下降（图 3a-3d） |
| 输出层 | 线性变换 + sigmoid | 将节点嵌入映射为 PPI 位点概率 | 输入：最后一层节点嵌入；输出：每个残基的概率 | Methods 节 | 预期影响：无此层无法完成二分类任务 [Analysis] |

---

## 09 关键公式符号

**EGCL 层更新规则**（来自 Satorras et al. 2021，本文采用）：

1. **边消息**：
   $$m_{ij} = \phi_e(h_i^l, h_j^l, \|x_i^l - x_j^l\|^2, a_{ij})$$
   - $h_i^l$：节点 $i$ 在第 $l$ 层的嵌入
   - $x_i^l$：节点 $i$ 在第 $l$ 层的坐标
   - $a_{ij}$：边特征
   - $\phi_e$：边 MLP

2. **坐标更新**：
   $$x_i^{l+1} = x_i^l + C \sum_{j \neq i} (x_i^l - x_j^l) \phi_x(m_{ij})$$
   - $C = 1/(M-1)$，$M$ 为节点数
   - $\phi_x$：坐标 MLP
   - 该更新保证等变性：坐标差 $(x_i - x_j)$ 在旋转/平移/反射下以相同方式变换

3. **注意力聚合**：
   $$m_i = \sum_{j \neq i} m_{ij} \cdot \phi_a(m_{ij})$$
   - $\phi_a$：注意力操作（线性变换 + sigmoid）

4. **节点嵌入更新**：
   $$h_i^{l+1} = \phi_h(h_i^l, m_i)$$
   - $\phi_h$：节点 MLP

5. **边特征**（本文自定义）：
   $$a_{ij} = \frac{\log(|i - j|)}{d_{ij}}$$
   - $|i-j|$：序列间隔
   - $d_{ij}$：Cα 欧氏距离
   - 分子捕捉序列分离度，分母捕捉空间距离

6. **预测**：
   $$p_i = \sigma(\phi_0(h_i^L))$$
   - $\sigma$：sigmoid 函数
   - $\phi_0$：输出线性层

---

## 10 实验设计与证据链

**数据集与规模**：
- 训练集 Train_335：335 个蛋白，10,374 个互作残基，55,992 个非互作残基
- 测试集 Test_60：60 个蛋白，2,075 个互作残基，11,069 个非互作残基
- 独立验证集 Validation_42：42 个蛋白（来自 GraphPPIS 的 Test_315，过滤 >25% 序列同一性）
- 非冗余测试集 UBtest_31：31 个蛋白（Test_60 子集，有已知非结合态结构）

**指标**：Accuracy、Precision、Recall、F1-score、MCC、ROC-AUC、PR-AUC

**基线方法**：PSIVER（Naïve Bayes）、ProNA2020（神经网络）、SCRIBER（逻辑回归）、DLPred（LSTM）、DELPHI（CNN+RNN 集成）、DeepPPISP（CNN）、SPPIDER（SVM+NN+LD）、MaSIF-site（几何深度学习）、GraphPPIS（图卷积网络）

**评测协议**：与 GraphPPIS 相同的 train/test split；所有基线使用相同输入特征和超参数（除 GCN/GAT 对比实验外）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| Test_60 主实验 | EquiPPIS 优于现有方法 | 与 9 种基线对比，相同输入 | EquiPPIS 是唯一 ROC-AUC > 0.8 的方法，PR-AUC 显著领先 | 等变架构带来精度提升 | 未做统计显著性检验 | Results 表 1 |
| 等变性消融 | 等变性是精度提升的关键 | EquiPPIS vs EquiPPIS invariant vs EquiPPIS w/o attention vs GCN vs GAT | 完整版最优；invariant 版 ROC-AUC < 0.8；GCN/GAT 远低于 GraphPPIS | 等变性和注意力均贡献精度 | 未报告各消融的完整指标矩阵 | Results 图 3a-3d |
| UBtest_31 非结合态测试 | EquiPPIS 对构象变化鲁棒 | 使用非结合态结构输入 | EquiPPIS 精度下降最小（MCC 降 4.6%），MaSIF-site 降 35%，GraphPPIS 降 14.6% | 等变模型对构象变化更鲁棒 | 样本量小（31 个） | Results 图 3e-3f |
| AlphaFold2 预测结构测试 | EquiPPIS 可用预测结构 | Test_60 用 AF2 预测结构 vs 实验结构 | EquiPPIS 用 AF2 结构 PR-AUC=0.451，优于 GraphPPIS 用实验结构（0.429） | 预测结构可替代实验结构 | 仅对比 GraphPPIS，未对比其他方法 | Results 表 2 |
| 特征消融 | 各特征组贡献 | 在 Validation_42 上逐一移除特征 | 所有特征组移除均导致精度下降；PSSM 和 ESM2 贡献最大 | 序列和结构特征互补 | 未报告具体数值 | Results 图 4a |
| 超参数选择 | 层数和隐藏维度 | Validation_42 上网格搜索 | 10 层、256 隐藏单元最优 | 深度和宽度需平衡 | 未报告完整搜索空间 | Results 图 4b-4g |

---

## 11 结论正确解读

- **任务范围**：本文解决的是 **partner-independent PPI 位点预测**——即仅给定单个蛋白结构，预测其表面哪些残基参与互作。**不涉及**复合物结构预测、结合亲和力预测或伴侣识别。
- **oracle/真值输入**：训练和测试均使用实验解析结构（来自 PDB 复合物中提取的单链），互作位点标签由复合物中链间接触残基定义。UBtest_31 使用非结合态实验结构，AF2 测试使用 AlphaFold2 预测结构。
- **端到端状态**：完整端到端模型，从结构直接预测位点，无需中间步骤。
- **算力成本**：训练最多 50 epochs，单张 NVIDIA A40 GPU，未报告具体训练时间。
- **历史数据依赖**：依赖 PDB 中已知复合物结构，存在数据库覆盖偏差（偏向已解析复合物的蛋白类型）。
- **模型依赖**：依赖 E(3) 等变图神经网络架构（EGCL），特征工程包含大量手工设计特征。
- **最难情形**：非结合态结构（构象变化大）、预测结构（含模型误差）、低序列同源性的蛋白。
- **不确定性**：未报告预测的置信度校准或不确定性估计；未做跨数据集泛化测试（如独立于训练分布的测试集）。
- **有边界的复述**：在 PDB 来源的 benchmark 上，E(3) 等变图神经网络相比非等变图网络和传统方法，能更准确地预测 partner-independent PPI 位点，且对非结合态和 AlphaFold2 预测结构输入具有更好的鲁棒性。该结论限于 benchmark 数据分布，未验证真实生物学场景中的泛化能力。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 可解释性不足 | 深度学习模型的潜在表示缺乏生物学解释 | 系统探索预测位点的进化/功能意义 | Discussion 节 |
| 未使用 MSA 信息 | 模型是 MSA-free 的，未利用多序列比对信息 | 显式纳入 MSA 信息可能进一步提升精度 | Discussion 节 |
| 未扩展到其他分子 | 仅针对蛋白质-蛋白质互作 | 可扩展到 DNA、RNA、小分子配体结合位点预测 | Discussion 节（最后一段） |
| 依赖 AlphaFold2 预测质量 | AF2 预测结构质量影响下游精度 | 未提供具体缓解方案 | Results 表 2 讨论 |

> 注：作者在 Discussion 中明确提到的局限仅以上 4 点。其他潜在局限（如 benchmark 偏差、未做统计显著性检验）未在原文中明确承认。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| 仅与 GraphPPIS 对比 AF2 结构实验 | 未与其他方法在 AF2 输入下对比，可能高估 EquiPPIS 的鲁棒性优势 | 「用预测结构超越实验结构」是核心卖点，需更全面对比 | 在 AF2 输入下对比所有基线方法 | Results 表 2 |
| 消融实验未报告完整指标 | 仅报告 ROC-AUC 和 PR-AUC 的变化，未报告 Precision/Recall/MCC 的消融影响 | 不同指标可能对特征移除的敏感度不同 | 补充完整指标矩阵的消融表 | Results 图 3、图 4 |
| 未做统计显著性检验 | 性能差异可能是随机波动，尤其测试集仅 60 个蛋白 | 结论的可靠性依赖差异的显著性 | 多次随机种子重复实验 + 配对检验 | Results 表 1 |
| 特征工程复杂，可迁移性存疑 | 45 维结构特征 + 3 种序列特征，特征设计依赖领域知识 | 对 TF–DNA 场景迁移时，特征需重新设计 | 在 TF–DNA 数据集上测试特征迁移效果 | Methods 节 |
| 等变性 vs 数据增强的公平对比 | 未与「非等变模型 + 数据增强」对比，无法分离等变架构和模型容量的贡献 | 等变性的优势可能部分来自模型容量或训练效率 | 控制模型容量，对比等变 vs 非等变+增强 | Results「Analyzing the importance of equivariance」节 |
| UBtest_31 样本量小 | 31 个蛋白的鲁棒性结论外推有限 | 鲁棒性声明需要更大规模验证 | 扩展非结合态测试集 | Results 图 3e-3f |
| 未讨论类别不平衡处理 | 互作位点通常远少于非互作位点，但未说明是否采用类别权重或采样策略 | 类别不平衡可能影响 Precision-Recall 指标的解释 | 检查训练损失函数和采样策略 | Methods 节 |

---

## 14 学到什么

> **Agent 提炼的知识候选**

1. **E(3) 等变图神经网络可直接迁移到 TF–DNA 结合位点预测**：DNA 结合残基的识别同样具有旋转/平移/反射对称性。可将 EquiPPIS 的 EGCL 架构直接用于 TF 结构（Cα 或全原子坐标），预测 DNA 结合残基。关键改动：图构建的边定义（距离阈值、序列间隔）需针对 TF–DNA 界面重新调优。

2. **「预测结构作为输入」的鲁棒性设计原则**：本文证明等变架构对 AF2 预测结构的误差更鲁棒。对 TF–DNA 场景，大量 TF 无实验结构，依赖 AF2 预测，因此选择等变架构而非普通 GNN 是合理的设计决策。

3. **特征工程的层次化设计**：本文融合序列特征（one-hot、PSSM、ESM2）和结构特征（SS、RSA、局部几何、取向、接触数、相对位置、虚拟表面积），并逐一消融验证贡献。对 TF–DNA 场景，可借鉴此思路：DNA 结合残基的已知强特征（如电正性、进化保守性）可类似地系统消融。

4. **等变性消融实验设计**：通过「关闭坐标更新」构造等变 vs 不变对照，直接验证等变性的贡献。这是可迁移的实验设计模板——在 TF–DNA 模型中也应做类似的架构消融。

5. **边特征设计**：本文使用 log(序列间隔)/距离 作为边特征，同时编码序列和空间信息。对 TF–DNA，可考虑加入 DNA 结合 motif 位置权重或保守性分数作为边特征。

6. **MSA-free 的权衡**：本文明确讨论 MSA-free 的优缺点（广泛适用 vs 信息缺失）。TF–DNA 场景中，TF 家族保守性高，MSA 信息可能更有价值，值得作为扩展方向。

7. **跨分子泛化声明**：作者在 Discussion 中提出方法可扩展到 DNA/RNA/小分子结合位点预测——这为 TF–DNA 场景提供了直接的方法学依据，但需注意 DNA 结合残基的物理化学特征与 PPI 残基不同（如 DNA 磷酸骨架的负电性 vs 蛋白表面的疏水 patch）。

---

## 15 与已有知识连接

- **Satorras et al. (2021), E(n) Equivariant Graph Neural Networks**：本文的 EGCL 层直接来自此工作。该架构已在分子性质预测、动力学模拟等任务中验证，本文将其首次用于 PPI 位点预测。→ 对 TF–DNA 场景，可参考此原始架构的数学性质（等变性证明、复杂度分析）。

- **GraphPPIS (2022)**：本文的直接前作和主要对比基线。GraphPPIS 使用标准 GCN + distance maps，本文通过等变架构超越之。→ 对 TF–DNA 场景，GraphPPIS 的 benchmark 设计（数据集构建、评估协议）可复用。

- **AlphaFold2 (Jumper et al., 2021)**：本文利用 AF2 预测结构作为输入，验证了「预测结构 → 下游任务」的可行性。→ 对 TF–DNA 场景，AF2 预测的 TF 结构质量（尤其是 DNA 结合域）需单独评估，因为 AF2 对 apo 结构的预测精度可能低于 holo 结构。

- **MaSift-Site (Gainza et al., 2020)**：基于几何深度学习的 PPI 位点预测方法，本文对比对象之一。其「指纹」思想（局部几何编码）与本文的局部几何特征有相似之处。→ 对 TF–DNA 场景，可借鉴其几何指纹方法编码 DNA 结合表面的形状互补性。

- **ESM2 (Lin et al., 2022)**：本文使用 ESM2 作为序列特征来源。→ 对 TF–DNA 场景，ESM2 或 ESM-1b 的嵌入已证明包含进化信息，可用于 DNA 结合残基预测。

- **候选方向（未验证）**：将本文的等变架构与 DNA 特异性特征（如 DNA 形状、静电势）结合，构建 TF–DNA 结合位点预测模型——这是本文方法在课题方向上的直接延伸，但需新数据集和特征工程。

---

## 16 研究想法

> **Agent 生成的研究候选**

1. **名称**：E(3)-TFDNA——基于等变图神经网络的转录因子 DNA 结合残基预测
   - **来源局限/观察**：EquiPPIS 证明 E(3) 等变架构对蛋白互作位点预测有效，且对 AF2 预测结构鲁棒；TF–DNA 结合残基预测尚无等变方法。
   - **核心假设**：E(3) 等变图神经网络能比非等变 GNN 更准确地预测 TF 的 DNA 结合残基，且对 AF2 预测的 TF 结构具有鲁棒性。
   - **增量**：将 EGCL 架构迁移到 TF–DNA 场景；引入 DNA 特异性特征（电正性、保守性、DNA 结合 motif 位置）；构建 TF–DNA 专用 benchmark。
   - **初步方法**：以 TF 单链结构（实验或 AF2 预测）为输入，Cα 坐标 + 序列/结构特征，EGCL 堆叠，输出 DNA 结合残基概率。与 GraphPPIS、DeepPPISP 等对比。
   - **验证方式**：在 PDB 中 TF–DNA 复合物数据集上评估；对比实验结构 vs AF2 预测结构的精度差异。
   - **创新状态**：unverified（方法迁移 + 场景适配，未见已发表工作）

2. **名称**：等变架构对预测结构误差的鲁棒性分析——以 TF–DNA 为例
   - **来源局限/观察**：EquiPPIS 在 PPI 上展示了等变模型对 AF2 预测结构的鲁棒性，但未分析鲁棒性的来源（是等变性本身还是模型容量）。
   - **核心假设**：等变架构的鲁棒性来自其对坐标扰动的「结构化」响应，而非简单的正则化效应。
   - **增量**：系统比较等变 vs 非等变模型在不同噪声水平（AF2 pLDDT 分层、人为坐标扰动）下的性能衰减曲线。
   - **初步方法**：在 TF–DNA 数据集上，对输入结构施加受控扰动（旋转、平移、高斯噪声），测量模型输出的稳定性。
   - **验证方式**：绘制噪声-性能曲线，比较等变和非等变模型的衰减率。
   - **创新状态**：unverified（分析性工作，方法成熟但结论新颖）

3. **名称**：TF–DNA 结合位点预测的等变图神经网络——结合 DNA 形状特征的 multimodal 方法
   - **来源局限/观察**：EquiPPIS 仅使用蛋白结构信息；TF–DNA 结合特异性受 DNA 形状（minor groove width、electrostatic potential）影响。
   - **核心假设**：将 DNA 形状特征作为边/节点特征注入等变图网络，可提升 DNA 结合残基预测精度。
   - **增量**：在 EGCL 框架中引入 DNA 形状特征通道；设计蛋白-DNA 联合图表示。
   - **初步方法**：蛋白残基为节点，DNA 形状特征（如 DNAshape 计算的 minor groove width）作为全局或局部特征注入。
   - **验证方式**：与仅用蛋白特征的等变模型对比，检验 DNA 形状特征的增量贡献。
   - **创新状态**：unverified（特征工程创新，架构复用）

4. **名称**：TF–DNA 结合位点预测的等变图神经网络——结合 DNA 形状特征的 multimodal 方法
   - **来源局限/观察**：EquiPPIS 仅使用蛋白结构信息；TF–DNA 结合特异性受 DNA 形状（minor groove width、electrostatic potential）影响。
   - **核心假设**：将 DNA 形状特征作为边/节点特征注入等变图网络，可提升 DNA 结合残基预测精度。
   - **增量**：在 EGCL 框架中引入 DNA 形状特征通道；设计蛋白-DNA 联合图表示。
   - **初步方法**：蛋白残基为节点，DNA 形状特征（如 DNAshape 计算的 minor groove width）作为全局或局部特征注入。
   - **验证方式**：与仅用蛋白特征的等变模型对比，检验 DNA 形状特征的增量贡献。
   - **创新状态**：unverified（特征工程创新，架构复用）

5. **名称**：TF–DNA 结合位点预测的等变图神经网络——结合 DNA 形状特征的 multimodal 方法
   - **来源局限/观察**：EquiPPIS 仅使用蛋白结构信息；TF–DNA 结合特异性受 DNA 形状（minor groove width、electrostatic potential）影响。
   - **核心假设**：将 DNA 形状特征作为边/节点特征注入等变图网络，可提升 DNA 结合残基预测精度。
   - **增量**：在 EGCL 框架中引入 DNA 形状特征通道；设计蛋白-DNA 联合图表示。
   - **初步方法**：蛋白残基为节点，DNA 形状特征（如 DNAshape 计算的 minor groove width）作为全局或局部特征注入。
   - **验证方式**：与仅用蛋白特征的等变模型对比，检验 DNA 形状特征的增量贡献。
   - **创新状态**：unverified（特征工程创新，架构复用）