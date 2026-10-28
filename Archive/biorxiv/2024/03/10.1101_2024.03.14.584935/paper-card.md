## 01 基本信息

- **标题**：ProAffinity-GNN: A Novel Approach to Structure-based Protein-Protein Binding Affinity Prediction via a Curated Dataset and Graph Neural Networks
- **作者**：Zhiyuan Zhou; Yueming Yin; Hao Han; Yiping Jia; Jun Hong Koh; Adams Wai-Kin Kong; Yuguang Mu
- **单位**：Nanyang Technological University (NTU), Singapore（据通讯邮箱推断，具体单位列表未提供）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2024
- **论文类型**：方法学 + 数据集构建（含基准评测）
- **领域**：蛋白质-蛋白质相互作用（PPI）结合亲和力预测；结构生物学 × 深度学习
- **关键词**：protein-protein interaction, binding affinity, graph neural network, protein language model, PDBbind, structure-based prediction
- **DOI/arXiv 号**：10.1101/2024.03.14.584935
- **代码**：未提供
- **数据**：基于 PDBbind (v2020) 手工标注的 2,285 对 PPI 配对数据集（未提供直接下载链接）
- **阅读日期**：2026-05-13（按当前日期）
- **在该课题方向中的位置**：本文聚焦 **蛋白质-蛋白质** 结合亲和力预测，而非 TF–DNA 互作。但其核心方法——**ESM-2 蛋白语言模型节点嵌入 + 残基级图神经网络（AttentiveFP）+ 分子内/分子间双图融合**——对 TF–DNA 结合亲和力预测具有高度可迁移性。其数据集构建策略（从 PDBbind 中手工标注配对互作链）也为构建 TF–DNA 互作数据集提供了方法论参考。

---

## 02 一句话总结

本文通过手工标注 PDBbind 中 2,285 对蛋白质-蛋白质互作配对构建了迄今最大的结构基 PPI 结合亲和力数据集，并提出 ProAffinity-GNN——一种融合 ESM-2 蛋白语言模型嵌入与 AttentiveFP 图注意力网络的深度学习框架，在多个基准集上以 MAE=1.62 kcal/mol、R=0.629 的交叉验证性能超越现有方法，并在外部 SKEMPI 突变数据集上展现出泛化能力。

---

## 03 研究问题

- **具体问题**：如何利用已知 3D 结构准确预测蛋白质-蛋白质复合物的结合亲和力（以 pKₐ/ΔG 为指标）？
- **为什么重要**：PPI 是几乎所有生物过程的核心，结合亲和力的准确预测对药物发现、蛋白质工程和疾病机制解析至关重要。实验方法（如 ITC、SPR）耗时耗力，计算方法可提供高通量替代方案。
- **现有方法不足**：
  - 传统方法（PRODIGY 线性模型、PPI-Affinity SVM）依赖手工设计的物理化学特征（如接触残基、埋藏表面积），特征工程繁琐且难以捕捉复杂互作模式。
  - 数据稀缺：PDBbind 中 2,852 个复合物仅 590 个为简单双链，多数含多链，难以直接用于配对分析；现有 benchmark 仅 144 对，规模过小。
  - 已有深度学习方法多聚焦蛋白质-配体（小分子）而非蛋白质-蛋白质，且未充分利用序列信息。
- **精确研究问题（Can 形式）**：Can a graph neural network with protein language model embeddings, trained on a manually curated pairwise PPI dataset, achieve higher accuracy and better generalization than existing feature-based methods for structure-based protein-protein binding affinity prediction?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 与 References 构建，属「仅本文框架」，未经外部系统核验。

| 阶段 | 代表方法 | 优点 | 局限 |
|------|----------|------|------|
| 实验方法 | ITC、SPR、NMR | 准确 | 耗时、昂贵、通量低 |
| 物理模拟 | 分子动力学（MD）、MM-PBSA | 物理可解释 | 计算成本高、精度受力场限制 |
| 经验/线性模型 | PRODIGY（接触残基+埋藏面积） | 简单、快速 | 特征有限、泛化差 |
| 传统 ML | PPI-Affinity（SVM + 分子描述符） | 比线性模型灵活 | 依赖手工特征、数据规模小 |
| 深度图学习（本文） | ProAffinity-GNN（ESM-2 + AttentiveFP + 双图） | 端到端、自动特征学习、融合序列+结构 | 数据依赖、可解释性弱 |

**本文主张的位置**：首次将蛋白语言模型（ESM-2）与图注意力网络（AttentiveFP）结合用于 PPI 结合亲和力预测，并配套构建了最大规模的手工标注配对数据集，填补了该方向「数据不足 + 方法单一」的双重空白。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 数据稀缺 | PDBbind 2,852 个复合物中仅 590 个为简单双链；benchmark 仅 144 对 | 多数复合物含多链，需人工判断实际互作配对；现有数据库未提供配对标注 | Introduction 第 3 段 |
| 数据标注困难 | 多链复合物中需确定哪两条链/两组蛋白直接互作 | 结构特征不足以判断时需查阅原始文献 | Materials and methods, Dataset creation 节；图 2 |
| 特征工程繁琐 | 传统方法需手工计算接触残基、埋藏面积、分子描述符 | 物理化学特征难以全面刻画互作复杂性 | Introduction 第 2 段（PRODIGY、PPI-Affinity 描述） |
| 模型泛化差 | 现有方法在跨数据集测试时性能显著下降 | 训练数据规模小、特征针对性过强 | Results, Comparative analysis 节（表 1 中 PRODIGY 在 test set 2 上表现不佳） |
| 序列信息未充分利用 | 多数结构基方法仅用 3D 坐标，忽略序列进化信息 | 缺乏将序列嵌入与结构图融合的有效框架 | Materials and methods, Graph construction 节（ESM-2 引入动机） |

---

## 06 核心思想

### 1) 表面方法
- 构建手工标注的 PPI 配对数据集（2,285 对，过滤后 2,133 对用于训练）。
- 将每个蛋白质复合物表示为残基级图：节点 = 残基（ESM-2 嵌入），边 = 分子内/分子间距离阈值内的残基对。
- 使用 AttentiveFP（GAT + GRU）分别处理分子内图与分子间图，融合后经全连接层回归预测 pKₐ。

### 2) 核心洞察
- **双图分离优于单图**：将分子内（蛋白质内部）与分子间（互作界面）图分开处理，使模型能分别学习蛋白质折叠特征与界面互作特征，消融实验证实双图组合效果最佳。
- **语言模型嵌入替代手工特征**：ESM-2 的 1280 维残基嵌入蕴含丰富的进化与结构信息，无需手工计算物理化学描述符，简化流程且提升泛化。
- **数据质量优先于数量**：手工标注配对互作链（而非简单取双链）显著提升了数据可用性，使多链复合物也能被纳入训练。

### 3) 可能的普适教训 [Analysis]
- 对 TF–DNA 互作预测：**「分子内 + 分子间」双图分离**的设计可直接迁移——蛋白质内部图 + 蛋白质-DNA 界面图分别建模，可能优于单图混合。
- **语言模型嵌入的通用性**：ESM-2 对蛋白质有效，DNA 侧可考虑使用 DNABERT 或核苷酸语言模型嵌入，形成「蛋白语言模型 + DNA 语言模型」双通道。
- **数据标注策略**：手工标注互作配对（而非依赖自动工具）虽耗时，但对模型性能提升显著，值得在 TF–DNA 数据集构建中借鉴。

---

## 07 方法总览

- **输入**：蛋白质复合物 3D 结构（PDB 格式）+ 对应 FASTA 序列
- **输出**：结合亲和力预测值（pKₐ，可线性转换为 ΔG kcal/mol）
- **模块**：
  1. 数据过滤与配对标注（手工）
  2. PDB → PDBQT 转换（AutoDockFR，添加极性氢）
  3. 残基级图构建（节点 = 残基，边 = 距离阈值）
  4. ESM-2 (t33 650M UR50D) 生成节点嵌入（1280 维）
  5. AttentiveFP 图神经网络（GAT 层 + GRU 更新）
  6. 三图融合（1 分子间 + 2 分子内）→ 全连接层 → 回归输出
- **训练**：Adam 优化器，lr=0.0005，weight decay=0.001，batch size=16，dropout=0.5，最大 25 epochs，early stopping，MSE loss，NVIDIA RTX A6000 GPU
- **评测**：5-fold 交叉验证 + 两个外部 benchmark 集 + SKEMPI 突变数据集
- **流程**：PDB 结构 → 配对标注 → PDBQT 转换 → 残基图构建 → ESM-2 嵌入 → AttentiveFP 三图并行处理 → 特征拼接 → 全连接回归 → pKₐ/ΔG 输出

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 手工配对标注 | 确定多链复合物中实际互作的链/链组 | 多链复合物无法直接用于配对分析；错误配对会引入噪声 | 输入：PDB 复合物；输出：标注的互作配对 | Materials and methods, Dataset creation 节；图 2 | 预期：数据质量下降，模型性能降低 [Analysis] |
| ESM-2 节点嵌入 | 为每个残基生成 1280 维语义向量 | 替代手工物理化学特征，捕捉序列进化信息 | 输入：FASTA 序列；输出：残基级嵌入 | Materials and methods, Graph construction 节 | 预期：模型失去序列信息，性能显著下降 [Analysis] |
| 分子内图（×2） | 分别建模两个蛋白质内部残基互作 | 捕捉蛋白质折叠结构与内部稳定性 | 输入：单链残基坐标 + 嵌入；输出：图嵌入 | 消融实验 Variant C 仍表现良好 | 实测：仅保留分子间图（Variant B）性能下降 |
| 分子间图 | 建模两蛋白界面残基互作 | 直接刻画结合界面特征 | 输入：跨链残基对（距离 ≤15Å）；输出：图嵌入 | 消融实验 Variant B | 实测：仅保留分子间图性能不如三图组合 |
| AttentiveFP（GAT+GRU） | 图级特征学习与节点更新 | GAT 自适应加权邻居，GRU 增强时序/迭代更新 | 输入：图结构 + 节点特征；输出：更新后的节点特征 | 消融实验 Variant A（纯 GAT）性能下降 | 实测：替换为纯 GAT 后性能下降 |
| 三图特征融合 + 全连接回归 | 整合分子内/分子间信息并映射到亲和力值 | 单一图信息不完整；回归头将高维特征映射到标量 | 输入：三图拼接特征；输出：pKₐ 预测值 | Results 表 1、表 3 | 预期：移除任一图分支均导致性能下降 [Analysis] |

---

## 09 关键公式符号

| 公式 | 符号含义 | 用途 | 来源 |
|------|----------|------|------|
| pKₐ = −log₁₀(K) | K = K_d, K_i, 或 IC₅₀ (mol/L) | 统一不同亲和力指标为对数尺度 | Materials and methods, Data preparation 节 |
| ΔG = RT·ln(K) | R = 1.987×10⁻³ kcal/(mol·K)，T = 298 K | 将 pKₐ 转换为 ΔG (kcal/mol) 以与基准比较 | Materials and methods, Evaluation metrics 节 |
| α_ij = softmax(LeakyReLU(aᵀ[Wh_i ‖ Wh_j])) | h_i, h_j = 节点特征；W = 权重矩阵；a = 注意力向量 | GAT 中计算邻居 j 对节点 i 的注意力系数 | Materials and methods, Network 节（GAT 描述） |
| h_i' = σ(Σ_α_ij·W·h_j) | σ = 非线性激活（ReLU） | 更新节点特征 | 同上 |
| r_t = σ(W_r·[h_{t−1}, x_t] + b_r) | r_t = 重置门；h_{t−1} = 上一隐藏态；x_t = 当前输入 | GRU 重置门控制遗忘程度 | Materials and methods, Network 节（GRU 描述） |
| z_t = σ(W_z·[h_{t−1}, x_t] + b_z) | z_t = 更新门 | GRU 更新门控制新旧信息混合 | 同上 |
| h̃_t = tanh(W·[r_t ∗ h_{t−1}, x_t] + b) | ∗ = 逐元素乘法 | 候选隐藏状态 | 同上 |
| h_t = (1 − z_t) ∗ h_{t−1} + z_t ∗ h̃_t | — | 最终隐藏状态 | 同上 |
| MAE = (1/N)·Σ|ŷ_i − y_i| | ŷ_i = 预测值，y_i = 真实值 | 评估指标 | Materials and methods, Evaluation metrics 节 |
| R = Σ(ŷ_i − ȳ)(y_i − ȳ) / √[Σ(ŷ_i − ȳ)²·Σ(y_i − ȳ)²] | ȳ = 均值 | Pearson 相关系数 | 同上 |

---

## 10 实验设计与证据链

**数据集与评测设置：**
- 训练集：2,133 对 PPI（从 2,285 对中过滤，排除含 DNA/RNA 的条目）
- 5-fold 交叉验证：训练集内部划分
- Benchmark 测试集 1：79 个数据点，来自结构基 PPI 结合亲和力 benchmark 数据库
- Benchmark 测试集 2：90 个数据点，来自 PPI-Affinity 项目（PDBbind 来源，含 1 个同源二聚体）
- 外部数据集：SKEMPI 2.0 子集（26 个野生型 + 140 个突变体结构，用 EvoEF2 生成突变体结构）
- 指标：MAE (kcal/mol)、Pearson R
- 硬件：NVIDIA RTX A6000 GPU

**实验表格：**

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 5-fold 交叉验证 | 模型在训练分布上的泛化能力 | 训练集 2,133 对，5 折 | R = 0.629 ± 0.056，MAE = 1.62 ± 0.08 kcal/mol | 模型在训练分布上表现稳定 | 未与同设置下其他方法直接对比 | Results, Performance 节 |
| Benchmark 测试集 1（79 对） | 与现有方法在标准 benchmark 上的对比 | 对比 PRODIGY、PPI-Affinity | ProAffinity-GNN 与 PRODIGY 相当，优于 PPI-Affinity | 模型在标准 benchmark 上具有竞争力 | 样本量小，差异可能不显著 | Results 表 1 |
| Benchmark 测试集 2（90 对） | 在更困难的双链子集上的表现 | 对比 PRODIGY、PPI-Affinity | ProAffinity-GNN 显著优于两者 | 模型在双链 PPI 上泛化更强 | 未报告置信区间 | Results 表 1 |
| 合并测试集（169 对） | 综合泛化能力 | 对比 PRODIGY、PPI-Affinity | ProAffinity-GNN 综合最优 | 模型整体泛化能力最强 | 未做统计显著性检验 | Results 表 1 |
| SKEMPI 外部验证 | 对突变体结构的泛化能力 | 26 野生型 + 140 突变体，对比 PPI-Affinity | ProAffinity-GNN 优于 PPI-Affinity | 模型对未见突变体具有泛化能力 | 突变体结构由 EvoEF2 生成，非实验结构 | Results 表 2 |
| 消融实验 | 各组件贡献 | Variant A（纯 GAT）、Variant B（仅分子间图）、Variant C（仅分子内图） | 完整模型最优；Variant C 优于 Variant B；Variant A 最差 | AttentiveFP 优于纯 GAT；双图组合优于单图 | 未报告各变体的具体数值 | Results 表 3、图 6 |

---

## 11 结论正确解读

- **任务范围**：仅针对蛋白质-蛋白质结合亲和力预测，不涉及蛋白质-DNA/RNA 互作（作者明确排除了含 DNA/RNA 的条目）。
- **oracle/真值输入**：训练标签来自 PDBbind 中实验测定的 K_d、K_i、IC₅₀ 值，经手工标注配对后使用。这些实验值本身存在测量误差，且不同实验条件可能影响一致性。
- **端到端状态**：模型端到端运行，输入 PDB 结构 + FASTA 序列，直接输出 pKₐ 预测值，无需中间手工特征计算。
- **算力成本**：单张 NVIDIA RTX A6000 GPU 即可训练，最大 25 epochs，成本可控。
- **历史数据依赖**：训练数据全部来自 PDBbind v2020，存在结构数据库的固有偏差（如易结晶蛋白过表达、膜蛋白缺失）。
- **模型依赖**：依赖 ESM-2 预训练嵌入质量；若目标蛋白与 ESM-2 训练分布差异大，嵌入质量可能下降。
- **最难情形**：突变体结构（需 EvoEF2 生成，非实验结构）；多链复合物中配对标注依赖人工判断。
- **群体/领域边界**：仅适用于蛋白质-蛋白质互作；对蛋白质-核酸互作、翻译后修饰等场景未验证。
- **不确定性**：未报告预测的置信区间或不确定性估计；SKEMPI 测试中突变体结构为计算生成，可能引入额外误差。

**有边界的复述**：ProAffinity-GNN 在 PDBbind 来源的 PPI 结构数据上，以 ESM-2 嵌入 + AttentiveFP 双图架构实现了优于现有方法的预测精度（交叉验证 R≈0.63，MAE≈1.62 kcal/mol），并在外部 benchmark 和 SKEMPI 突变数据集上展现出泛化能力。该结论仅适用于蛋白质-蛋白质互作场景，且受限于 PDBbind 数据分布和 ESM-2 嵌入质量。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 数据规模有限 | 训练集仅 2,133 对，远小于蛋白质-配体数据集 | 未明确提及 | Conclusion 节（隐含） |
| 缺乏统一评测基准 | 作者指出「absence of a universally accepted evaluation dataset」 | 呼吁领域建立统一评测标准 | Conclusion 节 |
| 突变体结构依赖计算生成 | SKEMPI 测试中突变体结构由 EvoFF2 生成，非实验测定 | 未明确提及 | Results, SKEMPI 节（隐含） |
| 未覆盖蛋白质-核酸互作 | 数据过滤排除了含 DNA/RNA 的条目 | 未明确提及 | Materials and methods, Data preparation 节（隐含） |

> 注：作者在 Conclusion 中明确承认「a pressing issue remains the absence of a universally accepted evaluation dataset」，其余局限为 [Analysis] 从方法描述中推断，非作者直接声明。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 训练集与测试集可能分布重叠 | Benchmark 测试集 2 来自 PDBbind，而训练集也基于 PDBbind，可能存在复合物重叠 | 若重叠，则测试性能被高估 | 检查训练集与测试集的 PDB ID 重叠情况 | Materials and methods, Data preparation 节 |
| 手工标注的主观性 | 配对标注依赖人工判断和文献查阅，不同标注者可能给出不同结果 | 标注不一致会引入标签噪声 | 计算标注者间一致性（如 Cohen's κ） | Materials and methods, Dataset creation 节 |
| ESM-2 嵌入的领域偏移 | ESM-2 主要在序列数据库上预训练，对结构变异（如突变）的嵌入可能不敏感 | 影响突变体预测的可靠性 | 对比 ESM-2 嵌入在野生型 vs 突变体上的差异 | Materials and methods, Graph construction 节 |
| 消融实验未报告数值 | 表 3 仅定性描述，未给出各变体的具体 MAE/R 值 | 无法评估差异的统计显著性 | 补充各变体的数值结果和置信区间 | Results 表 3 |
| 未与最新深度学习方法对比 | 仅对比 PRODIGY（线性模型）和 PPI-Affinity（SVM），未对比其他 GNN/Transformer 方法 | 无法确认方法在深度学习基线中的相对位置 | 增加与近期方法的对比实验 | Results 表 1 |
| 距离阈值选择的敏感性 | 分子内 3.5Å、分子间 15Å 的阈值未做敏感性分析 | 阈值选择可能显著影响图结构和性能 | 对不同阈值组合进行网格搜索 | Materials and methods, Graph construction 节 |
| 未报告推理时间 | 未提及模型推理速度，影响实际应用评估 | 实际部署需考虑计算效率 | 补充推理时间基准测试 | 全文未提及 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

| 可迁移知识 | 类型 | 如何迁移到 TF–DNA 互作课题 |
|------------|------|------------------------------|
| **双图分离架构**（分子内 + 分子间） | 方法设计 | 对 TF–DNA 复合物，可构建「蛋白质内部图」+「DNA 内部图」+「蛋白质-DNA 界面图」三图并行处理，分别捕捉折叠结构、DNA 构象与界面互作 |
| **ESM-2 语言模型嵌入** | 特征工程 | 蛋白质侧直接复用 ESM-2 嵌入；DNA 侧可尝试 DNABERT 或 Nucleotide Transformer 嵌入，形成双语言模型通道 |
| **手工标注配对策略** | 数据构建 | TF–DNA 复合物同样面临多链/多域问题，可参照其「最小互作单元」标注策略，结合文献判断实际结合的 TF 亚基与 DNA 片段 |
| **距离阈值建图** | 图构建 | 分子间 15Å 阈值可作初始参考；TF–DNA 界面通常涉及更短距离（氢键、范德华），建议对 5-10Å 范围做敏感性分析 |
| **pKₐ 统一指标** | 评测设计 | TF–DNA 结合数据同样存在 K_d、K_i、IC₅₀ 混用问题，可统一转换为 pKₐ 或 ΔG 以利比较 |
| **消融实验设计** | 实验方法 | 对 TF–DNA 模型，可设计「仅蛋白图 / 仅 DNA 图 / 仅界面图 / 全图组合」的消融，定位信息主要来源 |
| **外部数据集验证** | 评测策略 | 除训练分布外，用 SKEMPI 类突变数据库（如 ProTherm 或 TF 突变数据库）验证泛化能力 |
| **AttentiveFP 的 GRU 迭代更新** | 网络结构 | 对 TF–DNA 结合位点协同性建模可能有帮助——GRU 的迭代更新可模拟多轮构象调整 |

---

## 15 与已有知识连接

- **PDBbind 数据库**：本文数据基础，与蛋白质-配体结合亲和力预测领域（如 DeepDTA、OnionNet）直接相关。本文将其扩展至 PPI 场景。
- **ESM-2 (Lin et al., 2023)**：Meta AI 的蛋白语言模型，本文证明其嵌入可用于结构基亲和力预测。该模型在 TF–DNA 课题中同样可作为蛋白质侧特征提取器。
- **AttentiveFP (Xiong et al., 2019)**：原用于分子性质预测的图注意力框架，本文首次将其迁移至 PPI 亲和力预测。其「虚拟超节点」聚合策略对 TF–DNA 界面建模有参考价值。
- **PRODIGY (Vangone & Bonvin, 2015)**：基于接触残基的线性模型，本文将其作为基准。该方法的接触特征思想可迁移至 TF–DNA 界面接触分析。
- **PPI-Affinity (Romero-Molina et al., 2022)**：SVM + 分子描述符方法，本文直接对比对象。其描述符选择策略对 TF–DNA 特征工程有参考。
- **SKEMPI 2.0 (Jankauskaitė et al., 2019)**：突变体结合数据数据库，本文用于外部验证。TF–DNA 领域可类比使用 ProTherm 或 CIS-BP 突变数据。
- **OnionNet (Zheng et al., 2019)**：蛋白质-配体亲和力预测的层状距离分类方法，本文的边特征设计受其启发。该「洋葱层」思想可迁移至 TF–DNA 界面距离分层。
- **候选方向 [Analysis]**：本文方法可扩展至 TF–DNA 场景——将「蛋白质-蛋白质界面图」替换为「蛋白质-DNA 界面图」，DNA 残基（核苷酸）节点嵌入可尝试 DNABERT 或 one-hot + 位置编码。此外，本文数据集构建策略可启发构建 TF–DNA 结构-亲和力配对数据集（如基于 PDB 中 TF-DNA 复合物 + 文献亲和力数据）。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：ProAffinity-GNN 迁移至 TF–DNA 结合亲和力预测
- **名称**：TF-DNA-GNN：基于双语言模型嵌入与三图架构的转录因子-DNA 结合亲和力预测
- **来源局限/观察**：本文方法在 PPI 上有效，但 TF–DNA 互作具有不同物理化学特征（静电主导、碱基特异性、小沟/大沟识别），需适配
- **核心假设**：蛋白质语言模型（ESM-2）+ DNA 语言模型（DNABERT）嵌入 + 「蛋白内部图 + DNA 内部图 + 蛋白-DNA 界面图」三图架构可准确预测 TF–DNA 结合亲和力
- **增量**：将 PPI 方法扩展至蛋白-核酸互作；引入 DNA 侧语言模型嵌入；界面图边特征需适配 DNA 碱基对类型
- **初步方法**：构建 TF-DNA 结构数据集（PDB 中 TF-DNA 复合物 + 实验 K_d）；ESM-2 编码蛋白残基，DNABERT 编码核苷酸；三图并行 GAT+GRU；回归预测 pKₐ
- **验证方式**：与现有 TF-DNA 亲和力预测工具（如 DeepTF、TFBind）对比；在独立测试集上评估 MAE/R
- **创新状态**：unverified

### 候选 2：TF–DNA 配对数据集构建（仿照本文手工标注策略）
- **名称**：TF-DNA-Pair：基于 PDB 结构的手工标注 TF–DNA 互作配对数据集
- **来源局限/观察**：本文指出 PPI 领域数据稀缺，TF–DNA 领域更甚——现有数据库（如 TRANSFAC、JASPAR）多为序列基，缺乏结构-亲和力配对数据
- **核心假设**：通过手工标注 PDB 中 TF-DNA 复合物的实际结合亚基与 DNA 片段，可构建高质量结构-亲和力数据集
- **增量**：首个大规模 TF-DNA 结构-亲和力配对数据集；标注规则可复用本文「最小互作单元」策略
- **初步方法**：从 PDB 筛选 TF-DNA 复合物；结合文献与结构分析标注互作链/片段；关联实验亲和力数据（K_d/IC₅₀）；统一为 pKₐ
- **验证方式**：数据集统计报告 + 基线模型评测
- **创新状态**：unverified

### 候选 3：界面图边特征增强——引入 DNA 碱基类型与氢键模式
- **名称**：Base-Aware Edge Encoding for TF-DNA Interface Graphs
- **来源局限/观察**：本文边特征仅基于原子对距离分类（OnionNet 风格），未考虑 DNA 碱基类型特异性（A-T vs G-C 氢键模式不同）
- **核心假设**：在界面图边特征中编码碱基对类型（A/T/G/C）与氢键供体/受体模式，可提升 TF-DNA 结合特异性预测
- **增量**：将 DNA 序列信息显式注入图边，而非仅依赖节点嵌入
- **初步方法**：在本文图构建基础上，为界面边增加碱基类型 one-hot 编码与氢键模式特征；对比有无该特征的消融
- **验证方式**：在 TF-DNA 数据集上对比 MAE/R；分析注意力权重与已知 TF 结合基序的对应关系
- **创新状态**：unverified

### 候选 4：突变敏感性预测——从 PPI 到 TF-DNA 的迁移学习
- **名称**：TF-DNA-Mut：基于预训练 PPI 模型的 TF-DNA 突变效应预测
- **来源局限/观察**：本文在 SKEMPI 突变数据上表现良好，说明模型对突变有一定泛化能力；TF-DNA 突变数据（如 DNase  footprints 或 SELEX 突变实验）同样丰富
- **核心假设**：在 PPI 上预训练的图神经网络可通过迁移学习适应 TF-DNA 突变效应预测
- **增量**：利用 PPI 大模型作为 TF-DNA 小样本任务的预训练；减少 TF-DNA 数据稀缺的影响
- **初步方法**：在本文模型上预训练 PPI 任务，然后在 TF-DNA 突变数据集上微调；对比随机初始化与预训练初始化的性能
- **验证方式**：在 TF-DNA 突变数据集上评估 MAE/R；与直接训练对比
- **创新状态**：unverified