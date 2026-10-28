## 01 基本信息

- **标题**：CryptoBench: Cryptic protein-ligand binding sites dataset and benchmark
- **作者**：Vít Škrhák; Marian Novotný; Christos P. Feidakis; Radoslav Krivák; David Hoksza
- **单位**：未提供（作者所属机构未在摘要中列出）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2024
- **论文类型**：数据集 + 基准测试（benchmark）论文
- **领域**：蛋白质-配体结合位点预测；隐晦结合位点（cryptic binding sites, CBS）
- **关键词**：cryptic binding sites, apo-holo pairs, binding site prediction, benchmark, protein-ligand interactions
- **DOI/arXiv 号**：10.1101/2024.08.20.608828
- **代码**：未提供（PocketMiner 和 P2Rank 的代码为外部已有工具，本文未提供新代码）
- **数据**：CryptoBench 数据集，Open Science Framework: https://osf.io/pz4a9/
- **阅读日期**：未提供
- **在「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法/物理模拟」方向中的位置**：本文聚焦蛋白质-配体（小分子）结合位点预测，而非蛋白质-DNA 互作。但其核心问题——**apo 与 holo 构象间的结构差异导致结合位点预测困难**——与 TF–DNA 结合机制中「未结合 DNA 的 TF 构象 vs. 结合 DNA 的 TF 构象」问题高度同构。其数据集构建流程（apo-holo 配对、序列聚类防泄漏、RMSD 阈值定义隐晦性）和基准评测协议（序列 vs. 结构方法对比）可直接迁移至 TF–DNA 结合位点预测任务。

---

## 02 一句话总结

本文构建了目前最大的隐晦结合位点（CBS）数据集 CryptoBench（1,107 个结构，含预定义交叉验证划分），以 pocket RMSD > 2 Å 定义隐晦性，并评测了序列方法（pLM-NN，基于 ESM2-3B 嵌入）与结构方法（PocketMiner、P2Rank）的 CBS 残基预测性能，发现纯序列方法在 AUC 和 AUPRC 上匹配或超越结构方法。

---

## 03 研究问题

- **具体问题**：现有 CBS 数据集规模小（CryptoSite 仅 93 个口袋，PocketMiner 仅 39 个），且缺乏统一的评测协议，导致 CBS 预测方法的比较不公平、训练数据不足。
- **为什么重要**：CBS 是药物发现和蛋白质工程的重要靶点，但其在 apo（未结合配体）构象中不可见，预测难度远高于常规结合位点。缺乏大规模基准阻碍了该领域方法的发展。
- **现有方法为何不足**：
  - CryptoSite 数据集：规模小、隐晦性定义依赖其他预测工具（FPocket、ConCavity），可能引入工具偏差。
  - PocketMiner 数据集：规模更小（39 个口袋），且未提供预定义的交叉验证划分，难以公平比较。
  - 缺乏序列方法在 CBS 预测上的系统评测。
- **精确的「Can ... ?」研究问题**：Can a large-scale, RMSD-based cryptic binding site dataset with predefined splits enable fair benchmarking and reveal whether sequence-based methods can match structure-based methods for CBS residue prediction?

---

## 04 背景与发展脉络

**脉络标注**：以下脉络基于本文 Introduction 和 Discussion 的叙述，属于「仅本文框架」，未经外部系统核验。

1. **早期结合位点预测（非 CBS 专门）**：基于结构的结合位点预测方法（如 P2Rank）依赖 holo 构象中的几何/化学特征（如表面突出性），在常规结合位点上表现良好，但在 apo 构象上性能下降。
2. **CBS 专门方法出现**：认识到 apo 构象中结合位点不可见的问题，发展出基于分子动力学（MD）模拟的方法（如 CryptoSite 的 MD 扩展）和基于机器学习的方法（如 PocketMiner）。
3. **数据集瓶颈**：CryptoSite（93 口袋）和 PocketMiner（39 口袋）规模小，且隐晦性定义不一致（CryptoSite 依赖工具检测，PocketMiner 依赖 RMSD 但未提供标准划分）。
4. **本文主张的位置**：CryptoBench 作为目前最大的 CBS 数据集（1,107 结构），采用纯几何定义（pocket RMSD > 2 Å），提供预定义划分，并首次系统比较序列（pLM-NN）与结构（PocketMiner、P2Rank）方法。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 数据集规模不足 | CryptoSite 仅 93 个口袋，PocketMiner 仅 39 个 | 构建 apo-holo 配对需要大量人工筛选和结构比对，成本高 | Introduction 第 2-3 段 |
| 隐晦性定义不一致 | CryptoSite 依赖 FPocket/ConCavity 检测，可能引入工具偏差 | 使用预测工具定义「隐晦」导致标签依赖工具性能 | Introduction 第 2 段 |
| 缺乏标准评测协议 | 不同方法在不同数据集/划分上评测，结果不可比 | 无统一 benchmark 和预定义交叉验证 | CryptoBench benchmark 节 |
| 结构方法在 apo 构象上性能下降 | PocketMiner 在 apo 上 FPR 高、TPR 低 | 结构方法依赖 holo 构象中可见的几何特征，apo 中这些特征消失 | Results 节、图 4 |
| 序列方法未被充分探索 | 此前 CBS 预测以结构方法为主 | 领域惯性认为结构信息必需 | Results 节、表 4 |
| 隐晦性阈值选择困难 | RMSD 阈值过低会纳入非隐晦位点，过高会漏掉真实 CBS | 缺乏 consensus 定义 | Dataset Construction 节、Discussion 节 |

---

## 06 核心思想

### 1) 表面方法
- 基于 AHoJ-DB（大规模 apo-holo 配对数据库）构建 CBS 数据集，以 pocket RMSD > 2 Å 定义隐晦性，经多步过滤（分辨率、TM-score、配体大小、聚类）得到 1,107 个结构。
- 提供预定义的 80:20 train-test 划分和 4-fold 交叉验证。
- 评测三种方法：pLM-NN（序列，ESM2-3B 嵌入 + 小型神经网络）、PocketMiner（结构，预训练）、P2Rank（结构，预训练）。

### 2) 核心洞察
- **pocket RMSD 是有效的隐晦性量化指标**：与 CryptoSite 的工具依赖定义相比，纯几何定义更客观、可复现。
- **序列方法在 CBS 预测上具有竞争力**：pLM-NN 仅用序列嵌入即可匹配或超越结构方法，说明 CBS 的「隐晦性」可能部分编码在序列中（进化保守性、残基共变等）。
- **结构方法在 apo 上的性能瓶颈**：PocketMiner 在 apo 构象上 FPR 高，说明结构特征在 apo 中不可靠。

### 3) 可能的普适教训 [Analysis]
- **数据集构建的「防泄漏」设计**：按序列相似性聚类（40% 和 10% 阈值）防止同源蛋白跨划分泄漏，这是任何蛋白质 AI 基准（包括 TF–DNA 结合预测）都应遵循的原则。
- **「简单基线」的价值**：pLM-NN 作为简单序列基线，其竞争力提示：在引入复杂结构模型前，应先验证序列信息的极限。
- **隐晦性定义的「任务对齐」**：CBS 的定义应与下游任务（药物设计、突变效应预测）对齐，而非追求普适定义。

---

## 07 方法总览

- **输入**：AHoJ-DB 中的 apo-holo 蛋白对（按 UniProtID 关联），每个配对含 apo 结构、holo 结构、配体信息、pocket 残基标注。
- **输出**：CryptoBench 数据集（1,107 个结构，含预定义划分）+ 三种方法的评测指标（AUC、AUPRC、MCC、F1、TPR、FPR、ACC）。
- **模块**：
  1. **数据过滤**：分辨率 ≤ 2.5 Å、pocket 残基数一致、TM-score ≥ 0.5、配体原子数 ≥ 5、排除指定配体组。
  2. **隐晦性标注**：pocket RMSD > 2 Å（基于 holo 与 apo 的 pocket 残基坐标比对）。
  3. **聚类与划分**：40% 序列相似性聚类选代表，10% 相似性聚类划分 train/test（80:20），train 内 4-fold。
  4. **评测方法**：pLM-NN（ESM2-3B 嵌入 + 3 层 MLP）、PocketMiner（预训练）、P2Rank（预训练）。
- **训练**：pLM-NN 使用 4-fold 交叉验证进行超参数搜索（SklearnTuner），最终模型在 train 集上训练，test 集评测。
- **工具**：AHoJ-DB（数据源）、ESM2-3B（嵌入）、PocketMiner（外部工具）、P2Rank（外部工具）、SklearnTuner（超参数搜索）。
- **反馈回路**：无显式反馈回路（非主动学习或迭代优化）。
- **假设**：
  - pocket RMSD > 2 Å 能有效区分隐晦与非隐晦位点。
  - 序列相似性聚类（40%/10%）足以防止信息泄漏。
  - 配体原子数 ≥ 5 排除非药物类小分子。

**文字流程**：
1. 从 AHoJ-DB 提取所有 apo-holo 配对（约 468 万对）。
2. 依次应用分辨率、残基一致性、TM-score、配体大小、配体类型过滤。
3. 计算每个配对的 pocket RMSD，保留 > 2 Å 的配对。
4. 按 40% 序列相似性聚类，每簇选 RMSD 最大的配对为代表。
5. 对代表集按 10% 相似性聚类，划分 train/test（80:20）。
6. 在 train 上训练 pLM-NN（4-fold 超参数搜索），用 test 评测 pLM-NN、PocketMiner、P2Rank。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| AHoJ-DB 数据源 | 提供大规模 apo-holo 配对 | 手工构建配对成本高，AHoJ-DB 已预计算约 522k 个配体结合位点的 apo-holo 映射 | 输入：PDB 结构 + UniProt 映射；输出：apo-holo 配对及 pocket 残基 | Dataset Construction 节 | 无此模块则需从头计算，规模受限 |
| 分辨率过滤（≤ 2.5 Å） | 保证结构质量 | 低分辨率结构坐标误差大，RMSD 计算不可靠 | 输入：apo/holo 结构；输出：通过/过滤 | Dataset Construction 节 | 低质量结构引入噪声，RMSD 阈值失效 |
| TM-score ≥ 0.5 过滤 | 排除全局构象差异过大的配对 | 全局折叠差异（如 domain swap）会使 pocket RMSD 失去意义 | 输入：apo/holo 结构对；输出：通过/过滤 | Dataset Construction 节 | 纳入全局差异大的配对，pocket RMSD 不再反映局部隐晦性 |
| pocket RMSD > 2 Å 标注 | 定义隐晦性 | 提供客观、可复现的隐晦性标准 | 输入：apo/holo pocket 残基坐标；输出：隐晦/非隐晦标签 | Dataset Construction 节、图 1 | 阈值偏移会改变数据集构成；无此模块则依赖工具定义（如 CryptoSite） |
| 40% 序列聚类选代表 | 去冗余，保证多样性 | 同源蛋白的多个配对会主导数据集 | 输入：所有通过过滤的配对；输出：每簇一个代表 | Dataset Construction 节 | 冗余样本导致训练/评测偏向特定蛋白家族 |
| 10% 序列聚类划分 | 防止信息泄漏 | 同源蛋白跨 train/test 会导致虚高性能 | 输入：代表集；输出：train/test 划分 | CryptoBench benchmark 节 | 泄漏导致评测结果不可信 |
| pLM-NN（ESM2-3B + MLP） | 序列基线方法 | 验证序列信息在 CBS 预测中的极限 | 输入：氨基酸序列；输出：每个残基的隐晦结合概率 | Results 节、表 4 | 无此基线则无法判断结构方法的增量价值 |
| PocketMiner / P2Rank | 结构基线方法 | 代表当前 SOTA 结构方法 | 输入：PDB 结构；输出：残基结合概率 | Results 节、表 4 | 无结构基线则无法比较序列 vs. 结构方法 |

---

## 09 关键公式符号

本文未提供显式数学公式。核心概念定义如下：

- **pocket RMSD**：apo 与 holo 状态下，结合位点残基（定义为 holo 构象中距配体 4.5 Å 内的残基）的坐标均方根偏差。计算公式为：
  \[
  \text{RMSD} = \sqrt{\frac{1}{N} \sum_{i=1}^{N} \| \mathbf{x}_i^{\text{apo}} - \mathbf{x}_i^{\text{holo}} \|^2}
  \]
  其中 \( N \) 为 pocket 残基原子数，\( \mathbf{x}_i \) 为第 \( i \) 个原子的坐标。该公式为作者隐含使用的标准 RMSD 定义（文中未显式写出，但为 RMSD 的通用定义）。

- **归一化指标**（图 1 中用于比较不同长度 pocket 的指标）：
  \[
  \text{归一化值} = \frac{\text{apo 值} - \text{holo 值}}{\text{pocket 长度}}
  \]
  其中「值」可为分子表面、SASA 或体积。该公式在 Dataset Construction 节以文字描述给出。

- **评测指标**：AUC（ROC 曲线下面积）、AUPRC（精确率-召回率曲线下面积）、MCC（Matthews 相关系数）、F1、TPR、FPR、ACC。均为标准定义，文中未给出公式。

---

## 10 实验设计与证据链

### 数据集/群体
- **数据源**：AHoJ-DB（截至 2024 年 8 月，含 522,153 个配体结合位点的 apo-holo 映射）。
- **过滤后规模**：1,107 个结构（含多个 pocket 的记录，具体 pocket 数未在摘要中给出）。
- **划分**：80:20 train/test，train 内 4-fold。
- **测试集**：CryptoBench test 集（约 221 个结构，按 10% 序列聚类划分）。

### 指标
- AUC、AUPRC、MCC、F1、TPR、FPR、ACC。

### 基线/对比方法
- **pLM-NN**：本文实现的序列方法（ESM2-3B 嵌入 + 3 层 MLP，dropout 0.3，Adam，lr 1e-4，7 epochs，batch 2048）。
- **PocketMiner**：结构方法，使用作者发布的预训练模型，未重训练。
- **P2Rank**：结构方法，使用官方预训练模型，未重训练。

### 评测协议
- 残基级别二分类：每个残基是否为隐晦结合位点的一部分。
- 阈值：pLM-NN 和 PocketMiner 使用 0.75 概率阈值；P2Rank 使用其内置二分类输出。
- 排除标准：PocketMiner 无法预测的 22 个结构 + 多链结构 38 个，共 60 个结构从 PocketMiner 对比中排除。

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 指标分布分析（图 1） | pocket RMSD 能区分隐晦与非隐晦位点 | AHoJ-DB 子集 vs PocketMiner 测试集 | RMSD 在隐晦数据集中显著更高；分子表面、SASA、体积区分度低 | RMSD 是有效的隐晦性指标 | 未证明 RMSD 是最优指标；未与其他阈值比较 | Dataset Construction 节、图 1 |
| 主评测（表 4） | pLM-NN 匹配或超越结构方法 | pLM-NN vs. PocketMiner vs. P2Rank，同一 test 集 | pLM-NN 在 AUC、AUPRC 上优于 PocketMiner；与 P2Rank 相当或更优 | 序列方法在 CBS 预测上具有竞争力 | 未证明 pLM-NN 在所有子集上均优；PocketMiner 排除 60 个结构可能引入偏差 | Results 节、表 4 |
| PocketMiner 排除分析 | 排除结构不影响结论 | 全 test 集 vs. PocketMiner 可预测子集 | pLM-NN 在两种设置下均优于 PocketMiner | 结论对排除不敏感 | 未提供排除结构的详细特征分析 | Results 节、表 4 脚注 |
| P2Rank apo vs. holo 对比 | 结构方法在 holo 上优于 apo | P2Rank 在 apo 和 holo 结构上的表现 | P2Rank 在 holo 上表现更好 | 结构方法依赖 holo 构象特征 | 未比较其他结构方法 | Results 节、表 4 |
| 隐晦性阈值验证（图 5-6） | RMSD < 2 Å 的位点可能仍为隐晦 | CryptoSite 中 RMSD < 2 Å 的案例 | 部分案例存在显著侧链构象变化 | 2 Å 阈值可能漏掉部分 CBS | 未提供系统性漏检率 | Discussion 节、图 5-6 |

---

## 11 结论正确解读

- **任务范围**：本文仅针对**小分子配体**的结合位点预测，不涉及蛋白质-DNA、蛋白质-蛋白质互作。结论不能直接外推至 TF–DNA 结合位点预测。
- **oracle/真值输入**：pocket 残基标签来自 holo 结构中距配体 4.5 Å 内的残基，通过 UniProt 序列映射到 apo 结构。这依赖 AHoJ-DB 的配体注释质量。
- **端到端状态**：pLM-NN 是端到端训练的（序列 → 残基标签），但 PocketMiner 和 P2Rank 是预训练模型直接应用，未针对 CBS 微调。
- **算力成本**：pLM-NN 使用 ESM2-3B 嵌入（需 GPU 推理），但 MLP 本身轻量；PocketMiner 和 P2Rank 为 CPU 可运行的结构方法。
- **历史数据依赖**：数据集完全来自 PDB 中已有结构，存在实验偏好（如高可溶性、易结晶蛋白过表达）。
- **模型依赖**：pLM-NN 依赖 ESM2-3B 的嵌入质量；PocketMiner 和 P2Rank 依赖其训练数据的分布。
- **最难情形**：多链蛋白（PocketMiner 无法处理）、pocket 残基数不一致的配对、全局构象差异大的蛋白（TM-score < 0.5 被排除）。
- **群体/领域边界**：结论仅适用于 PDB 中已有 apo-holo 配对且满足过滤条件的蛋白。未覆盖无配体结构的蛋白、膜蛋白、 intrinsically disordered proteins。
- **不确定性**：pLM-NN 与 PocketMiner 的对比中，PocketMiner 排除了 60 个结构（约 27% 的 test 集），可能高估 pLM-NN 的相对优势。

**有边界的复述**：在 PDB 中已有 apo-holo 配对、分辨率 ≤ 2.5 Å、全局折叠相似（TM-score ≥ 0.5）、配体为小分子（≥ 5 个重原子）的蛋白上，基于 ESM2-3B 嵌入的序列方法在隐晦结合位点残基预测上匹配或超越了 PocketMiner 和 P2Rank，但该结论不适用于多链蛋白、无 apo 结构的蛋白，且未与其他序列方法（如 ESM2 更小版本、ProtTrans）或更复杂的结构方法（如 AlphaFold 3 结构预测 + 对接）进行比较。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 隐晦性定义可能漏掉部分 CBS | RMSD < 2 Å 的位点可能仍为隐晦（如侧链旋转），作者承认 2 Å 阈值会漏掉部分真实 CBS | 未明确提及，但暗示需要更精细的构象变化度量 | Discussion 节、图 5-6 |
| 数据集规模仍有限 | 1,107 个结构虽为最大 CBS 数据集，但相对 PDB 总量仍小 | 未明确提及 | Dataset Construction 节 |
| 序列方法仅测试了一种架构 | pLM-NN 是单一 MLP 架构，未与其他序列模型比较 | 未明确提及 | CryptoBench benchmark 节 |
| PocketMiner 排除大量结构 | 60 个结构（22 个预测错误 + 38 个多链）被排除，可能引入偏差 | 未明确提及 | Results 节 |
| 未控制训练数据重叠 | PocketMiner 和 P2Rank 的训练集可能与 CryptoBench test 集有重叠，未进行去重分析 | 未明确提及 | CryptoBench benchmark 节 |
| 隐晦性定义依赖配体存在 | 仅考虑已知配体的结合位点，无法覆盖未知的潜在隐晦位点 | 未明确提及 | Dataset Construction 节 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| pLM-NN 与 PocketMiner 的对比不公平 | PocketMiner 被排除 60 个结构，而 pLM-NN 在全 test 集上评测；若排除的结构多为 PocketMiner 难以处理的困难案例，则 pLM-NN 的优势被夸大 | 基准测试的核心目的是公平比较，排除困难案例会扭曲结论 | 在 PocketMiner 可预测的子集上重新计算 pLM-NN 的指标，比较两者在同一子集上的表现 | Results 节、表 4 脚注 |
| 「隐晦性」定义与下游任务脱节 | RMSD > 2 Å 是几何定义，但药物设计关注的是「能否成药」而非「构象变化大小」；部分 RMSD 大的位点可能并不影响配体结合 | 数据集标签应与实际应用对齐，否则训练的模型可能无法解决实际问题 | 用 docking 或 MD 结合自由能计算验证 RMSD > 2 Å 的位点是否真的影响配体结合 | Dataset Construction 节、Discussion 节 |
| 序列方法的成功可能源于数据泄漏 | 虽然按 10% 序列相似性聚类划分，但 ESM2-3B 的预训练数据可能包含 test 集中的蛋白序列，导致嵌入已「见过」这些蛋白 | 预训练模型的数据泄漏是普遍问题，会高估序列方法性能 | 检查 ESM2-3B 训练集是否包含 CryptoBench test 蛋白；或使用未在 ESM2 训练集中出现的蛋白进行验证 | CryptoBench benchmark 节 |
| 未与 AlphaFold 3 等结构预测方法比较 | AlphaFold 3 可预测蛋白-配体复合物结构，可能直接解决 CBS 检测问题；本文未将其纳入基准 | 如果 AF3 在 CBS 检测上表现更好，则本文的基准价值有限 | 在 CryptoBench 上运行 AF3 或类似方法，比较其与 pLM-NN 的性能 | Introduction 节（提及 AF3 但未比较） |
| 数据集构建依赖 AHoJ-DB 的配体注释 | AHoJ-DB 的配体注释可能不完整或有误，导致 pocket 残基标签不准确 | 标签噪声会限制模型性能上限，并影响基准可信度 | 人工验证随机抽样的 pocket 标签；或与 PDB 官方注释交叉比对 | Dataset Construction 节 |
| 未报告置信区间或统计显著性 | 表 4 仅报告点估计，未提供方差或显著性检验 | 小 test 集上性能差异可能不显著 | 使用 bootstrap 或重复采样计算置信区间 | Results 节、表 4 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **数据集构建的「防泄漏」协议**：按序列相似性分层聚类（40% 去冗余 + 10% 划分）是蛋白质 AI 基准的标准做法。迁移至 TF–DNA 结合位点预测时，应按 TF 的 DNA 结合域（DBD）序列相似性聚类，防止同源 TF 跨 train/test 泄漏。

2. **「简单序列基线」的竞争力**：pLM-NN 仅用 ESM2-3B 嵌入 + 3 层 MLP 即匹配或超越结构方法。对 TF–DNA 结合位点预测，可先测试基于 ESM2 或 ProtTrans 嵌入的序列模型，再决定是否需要引入结构信息。

3. **隐晦性定义的「任务对齐」原则**：CBS 的几何定义（RMSD）虽客观，但可能与下游任务脱节。对 TF–DNA 互作，可考虑用「apo TF 是否可预测 DNA 结合位点」或「结合自由能变化」作为更任务对齐的标签。

4. **结构方法的「apo 瓶颈」**：PocketMiner 在 apo 构象上 FPR 高，说明结构特征在未结合状态下不可靠。对 TF–DNA 结合位点预测，若使用 apo TF 结构，需注意类似问题；可考虑 ensemble 多个构象或结合 MD 采样。

5. **基准评测的「排除偏差」**：PocketMiner 排除 60 个结构（27% test 集）可能扭曲比较。设计 TF–DNA 基准时，应明确排除标准并报告排除对结果的影响。

6. **多链处理的缺失**：PocketMiner 无法处理多链结构，而 TF 常以二聚体或多聚体形式结合 DNA。TF–DNA 基准需显式处理多链 TF 结构。

7. **配体过滤的「生物学相关性」**：排除 < 5 个重原子的配体、保留共价配体，确保数据集的药物相关性。对 TF–DNA，可类比为排除非特异性 DNA 序列或短寡核苷酸。

---

## 15 与已有知识连接

- **CryptoSite（Cimermancic et al., 2016）**：本文直接对比的数据集，其 93 个口袋被用于验证 CryptoBench 的规模优势。CryptoSite 的隐晦性定义依赖 FPocket/ConCavity，本文的 RMSD 定义是对其的改进。
- **PocketMiner（Meller et al., 2023）**：本文的主要结构基线，其 39 个口袋数据集被用于对比。PocketMiner 的图神经网络方法代表结构方法的 SOTA。
- **P2Rank（Krivák & Hoksza, 2018）**：通用结合位点预测工具，本文将其作为非 CBS 特化方法的代表。
- **AHoJ（Hoksza et al., 2019）**：本文数据源，提供 apo-holo 配对的自动比对工具。
- **ESM2（Lin et al., 2023）**：本文序列方法使用的蛋白语言模型，其嵌入已被广泛用于各种蛋白质预测任务。
- **AlphaFold 3（Abramson et al., 2024）**：本文在 Introduction 中提及，但未纳入基准；其蛋白-配体复合物预测能力可能对 CBS 检测有潜在价值。
- **TF–DNA 互作方向的可迁移性**：本文的「apo vs. holo 构象差异」问题与 TF 未结合 DNA 与结合 DNA 的构象差异高度类似。Cryo-EM 和 NMR 已揭示许多 TF 在 DNA 结合时发生折叠或构象重排（如 bZIP 家族的 coiled-coil 形成），这与 CBS 的「隐晦」特性同构。本文的 RMSD 定义、数据集构建流程和基准协议可直接迁移至 TF–DNA 结合位点预测。

---

## 16 研究想法

**Agent 生成的研究候选**

1. **TF–DNA 隐晦结合位点数据集（TF-CryptoBench）**
   - **来源局限/观察**：CryptoBench 仅覆盖小分子配体，TF–DNA 结合位点预测缺乏类似基准。
   - **核心假设**：TF 的 DNA 结合位点在 apo 构象中不可见或部分不可见，且这种「隐晦性」可通过 apo-holo（未结合/结合 DNA）结构比对量化。
   - **初步方法**：从 PDB 收集 TF-DNA 复合物结构，用 AHoJ 或类似工具比对同一 TF 的 apo 和 holo 结构，以 DNA 结合残基的 RMSD > 2 Å 定义隐晦 TF 结合位点；按 DBD 序列相似性聚类划分 train/test。
   - **验证方式**：评测序列方法（ESM2 嵌入 + MLP）与结构方法（如 AF3 预测 apo 结构 + 结合位点预测）的性能。
   - **创新状态**：unverified（需验证数据可用性和隐晦性分布）。

2. **序列 vs. 结构信息的「隐晦性分解」**
   - **来源局限/观察**：CryptoBench 显示序列方法匹配结构方法，但未解释原因。
   - **核心假设**：CBS 的隐晦性可分解为「序列可编码部分」（进化保守性、共变信号）和「纯结构部分」（仅从 apo 构象可识别）。
   - **初步方法**：在 CryptoBench 上训练序列模型，分析其预测错误的残基是否对应结构变化最大的区域；对比 pLM-NN 与 PocketMiner 的误差模式。
   - **验证方式**：若序列模型在 RMSD 高的残基上系统性失败，则说明存在「纯结构隐晦性」。
   - **创新状态**：unverified。

3. **TF 二聚化对隐晦结合位点的影响**
   - **来源局限/观察**：CryptoBench 排除多链结构，而 TF 常以二聚体结合 DNA。
   - **核心假设**：TF 二聚化界面附近的 DNA 结合残基在单体 apo 状态下更「隐晦」，需要二聚体结构才能准确预测。
   - **初步方法**：构建 TF 二聚体 apo-holo 配对数据集，比较单体 vs. 二聚体结构的隐晦性分布；评测结构方法在单体 vs. 二聚体输入上的性能差异。
   - **验证方式**：若二聚体输入显著提升预测性能，则支持二聚化对隐晦性的贡献。
   - **创新状态**：unverified。

4. **MD 模拟增强的 TF–DNA 隐晦位点采样**
   - **来源局限/观察**：CryptoBench 仅使用静态 apo-holo 结构对，未考虑构象 ensemble。
   - **核心假设**：MD 模拟可采样 apo TF 的隐晦构象，提高结合位点预测的鲁棒性。
   - **初步方法**：对 CryptoBench 中的 apo 结构进行短 MD 模拟，提取多个构象作为结构方法的输入；比较 ensemble 输入 vs. 单构象输入的性能。
   - **验证方式**：若 ensemble 输入提升 AUC/AUPRC，则支持 MD 增强的价值。
   - **创新状态**：unverified（需计算资源）。

5. **CBS 预测的「任务对齐」标签设计**
   - **来源局限/观察**：CryptoBench 的 RMSD 定义与药物设计脱节。
   - **核心假设**：以「apo 构象中配体是否可对接成功」作为标签，比 RMSD 更贴近实际应用。
   - **初步方法**：对 CryptoBench 中的 apo 结构运行分子对接（如 AutoDock Vina），以对接成功与否重新标注隐晦性；比较两种标签下的模型性能。
   - **验证方式**：若对接标签训练的模型在独立测试集上表现更好，则支持任务对齐标签的价值。
   - **创新状态**：unverified。