## 01 基本信息

- **标题**：Structure-primed embedding on the transcription factor manifold enables transparent model architectures for gene regulatory network and latent activity inference
- **作者**：Tjarnberg, Andreas; Beheler-Amass, Maggie; Jackson, Christopher; Christiaen, Lionel A; Gresham, David; Bonneau, Richard
- **单位**：纽约大学（NYU）等（原文未完整列出所有单位，部分作者单位未提供）
- **期刊/平台**：Genome Biology
- **年份**：2024
- **论文类型**：方法学（Method）论文，提出新型深度学习框架
- **领域**：基因调控网络（GRN）推断、转录因子活性（TFA）推断、深度学习可解释性
- **关键词**：Gene regulatory network (GRN)、Transcription factor activity (TFA)、Deep learning、Autoencoder、Explainable AI、Single-cell genomics
- **DOI/arXiv 号**：10.1186/s13059-023-03134-1
- **代码**：未提供（原文未给出代码仓库链接）
- **数据**：公开数据（B. subtilis bulk RNA、S. cerevisiae bulk/single-cell RNA、PBMC multi-ome ATAC+RNA、COVID-19 PBMC 数据）；新测序数据已存入 NCBI GEO（GSE218089）
- **阅读日期**：2026-05-13（按当前日期填写）
- **在课题方向中的位置**：本文属于「AI/深度学习 × 蛋白质-DNA 互作（TF–DNA 结合机制）」方向，聚焦于利用已知 TF–DNA 结合先验（prior）约束神经网络结构，实现可解释的 GRN 推断与 TFA 估计。与物理模拟（MD/对接）无直接关联，但为 TF–DNA 结合机制研究提供了从表达数据推断 TF 活性的计算框架，可与结构预测方法互补。

## 02 一句话总结

本文提出 SupirFactor——一种基于自编码器的知识先验（structure-primed）深度学习框架，通过将已知 TF–DNA 调控先验嵌入网络结构，在多个物种和数据类型上实现了优于现有方法的 GRN 推断，并利用新提出的 explained relative variance（ERV）指标实现可解释的 TFA 推断和通路分析。

## 03 研究问题

- **具体问题**：如何从基因表达数据中同时推断基因调控网络（GRN）结构和转录因子活性（TFA），并保证模型的可解释性？
- **为什么重要**：GRN 推断受限于缺乏全基因组 TFA 的直接测量，导致难以区分协变关系和真正的调控互作。TFA 是理解细胞状态、发育和疾病的关键，但实验测量困难。
- **现有方法不足**：
  - 传统方法（如 NCA）使用静态先验，无法捕捉上下文依赖的调控关系；
  - 深度学习方法虽能建模复杂非线性关系，但缺乏可解释性，难以提取生物学意义；
  - 现有可解释性方法（如特征移除）需要目标值，无法用于无监督的 GRN 推断场景。
- **精确研究问题（Can...?）**：Can a structure-primed autoencoder architecture, combined with a variance-based interpretability metric (ERV), enable transparent and accurate GRN inference and TFA estimation from gene expression data across species and data modalities?

## 04 背景与发展脉络

> 注：此脉络基于本文框架整理，未经外部系统核验，标注为「仅本文框架」。

- **阶段一：统计/信息论方法（如 CLR、ARACNE）**：基于互信息或相关性推断共表达网络。优点：计算简单；局限：无法区分直接与间接调控，缺乏因果性。
- **阶段二：回归/基于模型的 GRN 推断（如 GENIE3、GRNBoost2）**：基于树模型或回归，利用表达协变推断调控关系。优点：可处理非线性；局限：不使用先验知识，推断结果难以解释为 TF 活性。
- **阶段三：网络组件分析（NCA）及变体**：利用先验调控结构（P）分解表达矩阵为 TFA 和调控强度。优点：显式估计 TFA；局限：先验静态、线性假设强、无法建模 TF-TF 互作。
- **阶段四：深度学习 GRN 推断**：利用 DNN 建模复杂非线性调控。优点：表达能力强；局限：黑箱、不可解释、难以提取 GRN 结构。
- **本文主张的位置**：在阶段三的先验约束思想与阶段四的深度学习能力之间架桥——用先验约束网络结构（而非仅作为正则项），同时提出 ERV 指标使模型完全透明可解释，实现 GRN 推断与 TFA 估计的统一框架。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| TFA 无法直接测量 | 缺乏全基因组 TF 活性的实验数据，GRN 推断难以区分协变与因果调控 | TF 活性受翻译后修饰、核定位、配体结合等多层调控，mRNA 表达不能代表活性 | Background 节："lack of direct measurements of genome-wide transcription factor activity (TFA) making it difficult to separate covariance and regulatory interactions" |
| 显式 TFA 推断与 GRN 推断脱节 | 现有方法要么只推断 GRN 不估计 TFA，要么估计 TFA 但使用静态先验 | 显式估计 TFA 的方法（如 NCA）将 GRN 推断和 TFA 估计分为两步，无法联合优化 | Background 节："Estimating TFA explicitly is problematic as it disconnects GRN inference and TFA estimation" |
| 深度学习模型不可解释 | DNN 能建模复杂关系但无法提供生物学可解释的 GRN 和潜在活性 | 深度模型过参数化，缺乏有效的特征重要性评估方法 | Background 节："Deep learning offers a potential solution... although does not provide interpretable models and latent features" |
| 现有可解释性方法不适用 | 特征移除方法（如 SHAP、LIME）需要目标值，无法用于无监督 GRN 推断 | GRN 推断是自监督任务，缺乏分类/回归目标 | Methods 节 ERV 定义部分："These techniques cannot be used for model selection" |
| 先验知识利用不足 | 已知的 TF–DNA 结合证据未被有效整合到深度模型中 | 多数深度 GRN 方法仅将先验作为正则项或后处理过滤，而非嵌入架构 | "The SupirFactor regulation model" 节：先验 P 直接约束 W 的结构 |

## 06 核心思想

### 1) 表面方法

SupirFactor 是一个自编码器框架，包含两种变体：
- **Shallow SupirFactor**：单隐层，输入基因表达 → TF 活性层（latent φ）→ 重建基因表达。编码器权重 W ∈ P（先验约束），解码器权重 Θ 即 GRN。
- **Hierarchical SupirFactor**：在 TF 层与输出之间增加 meta-TF（mTF）层，建模 TF-TF 互作和高阶调控通路。

训练目标为最小化重建误差（MSE），使用 Adam 优化器。关键创新是**先验 P 直接约束编码器权重的稀疏结构**（而非仅作为惩罚项），使 latent 层可解释为 TF 活性。

### 2) 核心洞察

- **先验即架构**：将已知 TF–DNA 结合证据（P）作为编码器权重的结构约束，使 latent 变量天然对应 TF 活性，无需事后解释。
- **ERV 作为统一解释指标**：通过扰动 latent 特征并测量输出方差变化，ERV 可量化任意层特征对输出的贡献，无需目标值，适用于无监督 GRN 推断。
- **TFA ≠ TF 表达**：模型学到的 latent 活性与 TF mRNA 表达不同，能捕捉翻译后调控等表达无法反映的活性变化（如细胞周期中 TFA 峰值滞后于表达峰值）。

### 3) 可能的普适教训 [Analysis]

- **知识先验嵌入架构优于后处理约束**：将生物学先验直接编码为网络结构（而非 loss 惩罚项），可同时提升可解释性和泛化能力。这一思路可迁移到 TF–DNA 结合机制研究中，例如将已知的 DNA 结合域（DBD）结构信息或 ChIP-seq 峰作为先验约束。
- **方差分解作为通用可解释性工具**：ERV 不依赖目标值，可推广到其他无监督生物学推断任务（如通路活性推断、细胞状态表征）。
- **活性推断需与结构推断联合优化**：TFA 和 GRN 是相互依赖的隐变量，联合推断优于两步法。

## 07 方法总览

- **输入**：基因表达矩阵 X（n 基因 × s 样本），先验矩阵 P（TF × 基因，二值或连续权重）
- **输出**：GRN 矩阵 Θ（TF × 基因，调控强度）、TFA 矩阵 φ（TF × 样本，latent 活性）、mTF 活性矩阵 φ̂（mTF × 样本）
- **模块**：
  1. 编码器 f：X → φ，权重 W ∈ P（先验约束）
  2. （Hierarchical）mTF 层 s：φ → φ̂，权重 Π
  3. 解码器 g：φ（或 φ̂）→ X̂，权重 Θ（GRN）
- **训练**：Adam 优化器，MSE loss，权重衰减（L2），dropout 正则化
- **解释模块**：ERV 计算（扰动 latent 特征，测量输出方差变化）
- **流程**：输入表达数据 → 先验约束编码器映射到 TF 活性 → （可选）mTF 层聚合 TF 互作 → 解码器重建表达 → 通过 ERV 评估各连接的预测重要性 → 提取 GRN 和 TFA

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 先验约束编码器（W ∈ P） | 将基因表达映射到 TF 活性 latent 空间，权重结构由先验 P 限定 | 确保 latent 特征可解释为 TF 活性，减少参数空间，防止过拟合 | 输入：基因表达 x；输出：TF 活性 φ | Results 图 2A：使用先验约束的模型 GRN 恢复显著优于无先验模型 | 移除后 latent 特征失去生物学对应，可解释性大幅下降（预期影响） |
| mTF 层（Hierarchical） | 建模 TF-TF 互作，将 TF 聚合为通路级 latent 特征 | 捕捉 TF 协同调控、竞争结合等高阶互作，实现通路分析 | 输入：TF 活性 φ；输出：mTF 活性 φ̂ | Results 图 4：mTF 富集到 KEGG 代谢通路 | 移除后退化为 shallow 模型，无法建模 TF-TF 互作（预期影响） |
| 解码器（Θ） | 从 TF/mTF 活性重建基因表达，Θ 即 GRN | 通过重建任务学习调控权重，Θ 可直接解释为 GRN | 输入：φ/φ̂；输出：重建表达 X̂ | Results 图 2C：GRN 恢复优于 GENIE3、GRNBoost2 | 移除后无法提取 GRN（预期影响） |
| ERV 解释模块 | 量化每个 latent 特征对每个输出基因的方差贡献 | 提供无目标值的特征重要性评估，支持模型选择和剪枝 | 输入：训练好的模型 + 数据；输出：ERV 矩阵 | Results 图 2A：ERV 优于模型权重直接解释；Methods 节 ERV 定义 | 移除后模型不可解释，无法进行剪枝（预期影响） |
| 剪枝/模型选择 | 迭代移除 ERV ≤ 0 的权重，重拟合模型 | 消除过参数化，提高泛化和可解释性 | 输入：完整模型 + ERV；输出：稀疏模型 | Methods 节 "Stable architecture"：剪枝后模型保持预测性能 | 移除后模型过参数化，GRN 解释困难（预期影响） |

## 09 关键公式符号

| 公式 | 符号含义 | 用途 | 直觉 | 来源 |
|------|----------|------|------|------|
| $\hat{\mathbf{x}} = h(\mathbf{x}) = (g \circ f)(\mathbf{x})$ | x：基因表达向量；f：编码器；g：解码器；h：整个自编码器 | 定义自编码器整体映射 | 表达数据经编码-解码重建，latent 即 TF 活性 | Methods "Shallow SupirFactor" 节，式(1) |
| $\boldsymbol{\phi} = f(\mathbf{x}) = \sigma(\mathbf{W}\mathbf{x})$ | φ：TF 活性；W：编码器权重（∈P）；σ：激活函数 | 编码器映射 | 基因表达经先验约束权重线性组合后非线性激活，得到 TF 活性 | Methods 节，式(2) |
| $\hat{\mathbf{x}} = g(\boldsymbol{\phi}) = \sigma(\boldsymbol{\Theta}\boldsymbol{\phi})$ | Θ：解码器权重（GRN） | 解码器映射 | TF 活性经 GRN 权重线性组合重建基因表达 | Methods 节，式(3) |
| $\hat{\mathbf{x}} = h(\mathbf{x}) = (g \circ s \circ f)(\mathbf{x})$ | s：mTF 层映射 | Hierarchical 模型整体映射 | 增加 mTF 中间层建模 TF-TF 互作 | Methods "Hierarchical SupirFactor" 节，式(4) |
| $\hat{\boldsymbol{\phi}} = s(\boldsymbol{\phi}) = \sigma(\boldsymbol{\Pi}\boldsymbol{\phi})$ | Π：TF→mTF 权重矩阵 | mTF 层映射 | TF 活性经互作权重聚合为通路级活性 | Methods 节，式(5) |
| $\hat{\mathbf{x}} = g(\hat{\boldsymbol{\phi}}) = \sigma(\boldsymbol{\Theta}\hat{\boldsymbol{\phi}})$ | Θ：mTF→基因权重 | Hierarchical 解码器 | mTF 活性重建基因表达 | Methods 节，式(6) |
| $\hat{\mathbf{x}}_C = (g \circ s \circ f_C)(\mathbf{x}_C)$ | C：生物学上下文；f_C：上下文特异的编码器 | JRL 多任务学习 | 不同上下文共享 mTF 层和解码器，但编码器权重上下文特异 | Methods "JRL" 节，式(7) |
| $\text{MSE} = \frac{1}{N}\sum_i \|\mathbf{x}_i - h(\mathbf{x}_i)\|^2$ | N：样本数 | 训练目标 | 最小化重建误差 | Methods 节，式(8) |
| $\xi^2_{i,k} = 1 - \frac{\text{MSE}_i(\bar{h}(\mathbf{x})_{\phi})}{\text{MSE}_i(\bar{h}(\mathbf{x})_{\phi_{K \neq k}})}$ | ξ²：ERV；i：基因；k：TF | 计算 TF k 对基因 i 的解释方差比例 | 移除 TF k 后误差增加越多，说明 k 对 i 越重要 | Methods "ERV" 节，式(10) |
| $\xi^2_{m,k,\Pi} \equiv 1 - \frac{\sum_{i \in k \cap m}\text{MSE}_i(\bar{h}(\mathbf{x})_{\phi})}{\sum_{i \in k \cap m}\text{MSE}_{i,k,L}(\bar{h}(\mathbf{x})_{\phi_{K \neq k}})}$ | m：mTF；k∩m：TF k 与 mTF m 共同靶向的基因集 | 计算 mTF 层权重的 ERV | 通过交集基因集评估 TF→mTF→基因的间接贡献 | Methods 节，式(11) |
| $\hat{\boldsymbol{\phi}} = \arg\min_{\phi} \|\mathbf{Y} - \boldsymbol{\phi}\mathbf{P}\|$ | Y：表达矩阵；P：先验矩阵 | NCA 基线方法 | 用静态先验最小二乘估计 TFA | Methods "NCA" 节，式(14) |
| $\dot{x}_{i,s} = x_{i,s} \cdot 1 \text{ if } a_{p,s} \in A_i \text{ else } 0$ | a_{p,s}：ATAC 峰；A_i：基因 i 相关峰集合 | ATAC 掩码 | 仅保留染色质可及区域的表达信号 | Methods "Epigenetic masking" 节，式(16) |

## 10 实验设计与证据链

### 数据集与规模
- **B. subtilis bulk RNA**：B1、B2 两个数据集，先验网络含 154 个 TF、4218 个报告基因
- **S. cerevisiae bulk RNA**：S1、S2 两个数据集，先验网络含 150 个 TF、5578 个报告基因
- **S. cerevisiae single-cell RNA**：scY 训练集（15 种生长条件）；4 个新测序测试集（YPD 1/2、MMD 1/2，n=1531/1428/492/463）
- **PBMC multi-ome**：10x 公开数据，10,411 细胞、21,601 基因、75,111 ATAC 峰；COVID-19 数据集来自 [58]

### 指标
- GRN 恢复：AUPR（area under precision-recall curve），针对先验中留出的边
- 预测精度：R²（重建表达的解释方差）
- TFA 验证：与已知生物学功能/文献注释的一致性

### 基线方法
- Inferiorator（含 AMuSR 多任务变体）
- GENIE3、GRNBoost2（不使用先验的方法）

### 关键实验与结果

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 基准测试（shallow Supirator） | 先验约束自编码器优于现有 GRN 推断方法 | 5 个数据集（B1/B2/S1/S2/scY），对比 Inferelator、GENIE3、GRNBoost2 | SupirFactor 在所有数据集上 AUPR 显著更高 | 先验约束 + 深度学习的组合有效提升 GRN 恢复 | 未证明在所有可能的 GRN 推断场景中均最优 | Results 图 2C |
| ERV vs 模型权重解释 | ERV 比直接使用权重更能反映生物学重要性 | 同一模型，比较 ERV 排序与权重排序的 AUPR | ERV 排序的 AUPR 显著高于权重排序 | ERV 是更优的连接重要性指标 | 未与其他可解释性方法（如 SHAP）系统比较 | Results 图 2A |
| 剪枝实验 | 移除 ERV ≤ 0 的权重不损失预测性能 | 剪枝前后 R² 和 AUPR 对比 | 剪枝后参数减少约 50%，R² 保持，AUPR 提升 | ERV 支持有效的模型剪枝 | 未测试不同剪枝阈值的影响 | Methods "Stable architecture" 节 |
| 细胞周期 TFA 分析 | TFA 能捕捉表达无法反映的 TF 活性变化 | scY 数据，比较 TFA 与 TF 表达的细胞周期相位 | TFA 峰值滞后于表达峰值，与已知调控逻辑一致 | TFA 是独立于表达的活性度量 | 未与蛋白水平实验测量直接验证 | Results 图 3A-B |
| mTF 通路富集 | mTF 层能聚合功能相关的 TF 模块 | scY 数据，KEGG 富集分析 | 42/148 个 mTF 富集到代谢通路 | mTF 层具有通路生物学意义 | 未在哺乳动物数据上验证 mTF 功能 | Results 图 4 |
| PBMC 多组学验证 | 模型可扩展到哺乳动物复杂系统 | PBMC multi-ome，ATAC 掩码整合 | 恢复已知细胞类型特异 TF（如 PAX5 于 B 细胞） | 框架可推广到人类数据 | 未与 PBMC 的 ChIP-seq 直接比较 | Results 图 5 |
| COVID-19 迁移分析 | 训练好的模型可迁移到新数据发现疾病相关 TF | 健康 vs COVID PBMC，比较 TFA | 识别出炎症相关 TF（FosB、JUN）活性上调 | 模型可用于条件特异 TFA 分析 | 未进行因果验证 | Results "COVID-19" 节 |

## 11 结论正确解读

- **任务范围**：本文解决的是 GRN 推断和 TFA 推断，而非 TF–DNA 结合机制的直接建模。模型输出的是调控权重和 latent 活性，不是物理结合亲和力或结构信息。
- **先验的作用**：先验 P 是已知的 TF–DNA 调控证据（来自文献/ChIP-seq），模型不预测新的 TF–DNA 结合，而是在给定先验下估计调控强度和 TF 活性。
- **TFA 的边界**：TFA 是模型推断的 latent 变量，与实验测量的蛋白活性（如 ELISA、western blot）未直接验证，仅在已知生物学功能的层面间接验证。
- **端到端状态**：模型是端到端训练的（输入表达 → 输出 GRN + TFA），但依赖外部先验 P 作为输入约束，不是完全无先验的端到端推断。
- **算力成本**：原文未提供详细算力/训练时间信息（Not assessable）。
- **历史数据依赖**：模型依赖先验 P 的质量，先验中的假阳性/假阴性会直接影响推断结果。
- **最难场景**：模型在稀疏先验或缺乏先验的物种上表现未知；PBMC 结果主要验证已知 TF，对新 TF 发现能力有限。
- **不确定性**：原文未提供置信区间或不确定性量化（Not assessable）。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 先验质量依赖 | 模型性能受限于先验 P 的完整性和准确性 | 未明确提及（隐含：改进先验构建方法） | Discussion 节（隐含） |
| 模型稳定性 | 非线性深度模型存在训练稳定性问题 | 未明确提及 | Discussion 节："challenges still exist, like model stability and model selection" |
| 模型选择挑战 | 剪枝阈值和超参数选择需要进一步优化 | 未明确提及 | Discussion 节 |
| 哺乳动物验证有限 | PBMC 分析主要验证已知 TF，新调控关系发现有限 | 未明确提及 | Results 图 5 相关讨论 |
| 未与蛋白活性实验直接验证 | TFA 推断未与实验测量的蛋白活性对比 | 未明确提及 | 全文（隐含） |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 先验 P 与 gold standard 重叠 | 基准测试中先验 P 与 gold standard 共享大量边，留出验证可能高估性能 | 若先验已包含大部分 gold standard 边，AUPR 高可能反映先验质量而非模型能力 | 使用完全独立的 gold standard（如不同数据库来源）进行验证 | Methods 节：先验与 gold standard 均来自文献数据库 |
| ERV 与因果性 | ERV 衡量的是预测贡献，不等于因果调控关系 | 高 ERV 连接可能是间接调控或共变关系 | 用扰动实验（如 TF 敲除）验证高 ERV 连接的因果性 | Methods 节 ERV 定义 |
| TFA 可解释性验证 | TFA 与已知生物学功能的一致性可能受选择偏差影响（只检查已知 TF） | 需要系统评估 TFA 对未知 TF 的推断准确性 | 对未注释 TF 的 TFA 进行实验验证 | Results 图 3-5 |
| 与物理模拟的脱节 | 模型完全基于表达数据，未利用 TF–DNA 结合的结构信息（如 DBD 序列偏好、3D 结构） | 结合结构先验可能提升低表达/稀疏数据下的推断 | 将 P 替换为基于结构预测的 TF–DNA 结合评分 | 全文（未涉及结构信息） |
| 基线方法选择 | 仅与 Inferelator、GENIE3、GRNBoost2 比较，未与最新深度 GRN 方法（如 GraphTF、DeepSEM）比较 | 无法判断 SupirFactor 在深度学习 GRN 方法中的相对位置 | 增加与更多深度 GRN 方法的基准比较 | Results 图 2C |
| 单细胞数据稀疏性 | 未明确讨论模型在极端稀疏/低深度单细胞数据上的表现 | 实际应用中单细胞数据噪声大、dropout 率高 | 在低深度/稀疏数据上进行鲁棒性测试 | 未提供 |

## 14 学到什么

**Agent 提炼的知识候选**

1. **先验即架构（Prior-as-Architecture）**：将生物学先验直接编码为网络连接结构（而非 loss 惩罚），可同时提升可解释性和泛化能力。迁移到 TF–DNA 结合机制研究：可将已知的 TF 结合位点（motif）或 ChIP-seq 峰作为编码器结构约束，推断细胞类型特异的 TF 活性。

2. **ERV 作为无监督可解释性指标**：通过扰动 latent 特征并测量输出方差变化，无需目标值即可评估特征重要性。迁移：在 TF–DNA 结合预测中，可用类似方法评估每个序列特征（如 motif 位置、结构域）对结合预测的贡献，无需标签。

3. **TFA 与表达解耦**：模型证明 latent 活性与 TF mRNA 表达不同，能捕捉翻译后调控。迁移：在 TF–DNA 结合机制研究中，TFA 可作为比表达量更准确的调控活性度量，用于关联 DNA 结合事件。

4. **层级通路建模（mTF）**：通过中间层将 TF 聚合为通路级 latent 特征，实现可解释的通路分析。迁移：可将此思想用于建模 TF 协同结合（co-binding）或增强子-启动子互作中的 TF 组合效应。

5. **ATAC 掩码整合多组学**：用染色质可及性掩码输入特征，整合表观基因组信息。迁移：在 TF–DNA 结合预测中，可将 ATAC-seq 可及性作为输入掩码或特征权重，提升结合位点预测精度。

6. **剪枝作为模型选择**：基于 ERV 迭代剪枝非预测权重，在保持预测性能的同时大幅简化模型。迁移：在深度 TF–DNA 结合模型中，可用类似方法剪除非关键序列特征，提升可解释性。

## 15 与已有知识连接

- **NCA（Network Component Analysis）**：本文直接与 NCA 对比（Methods "NCA" 节），SupirFactor 是对 NCA 的深度学习扩展，解决了 NCA 静态先验和线性假设的局限。NCA 是 TF–DNA 调控推断的经典方法（Liao et al., 2003）。
- **Inferelator**：本文使用 Inferelator 作为主要基线（含 AMuSR 多任务变体），Inferelator 是 GRN 推断的经典回归方法（Bonneau et al., 2006；Greenfield et al., 2017）。
- **GENIE3 / GRNBoost2**：基于树模型的 GRN 推断方法，本文作为无先验基线对比（Huynh-Thu et al., 2010；Moerman et al., 2019）。
- **自编码器在 GRN 推断中的应用**：本文与 D-GEX（Chen et al., 2016）等自编码器表达建模方法相关，但创新在于先验约束结构和 ERV 解释。
- **TF 活性推断**：与 Footprint（Neph et al., 2012）、VIPER（Alvarez et al., 2016）等方法相关，本文提供深度学习的替代方案。
- **可解释 AI 在基因组学**：与 SHAP（Lundberg & Lee, 2017）等通用可解释方法相比，ERV 专为无监督 GRN 推断设计。
- **单细胞多组学整合**：与 MOFA+（Argelaguet et al., 2020）、scAI（Jin et al., 2020）等多组学整合方法相关，本文的 ATAC 掩码是一种轻量级整合策略。

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：Structure-Primed TF–DNA Binding Affinity Prediction
   - **来源局限/观察**：SupirFactor 使用表达数据推断 TFA，但未利用 TF–DNA 结合的结构信息（如 DBD 序列偏好、3D 结构）
   - **核心假设**：将 TF–DNA 结合的结构先验（如 PDB 结构、motif PWM）嵌入自编码器结构，可提升 TFA 推断精度，尤其在先验稀疏的物种中
   - **初步方法**：将 TF 的 DNA 结合域序列嵌入（如 ESM 或 ProtTrans）作为编码器权重的初始化或约束，结合 ChIP-seq 峰作为先验 P
   - **验证方式**：在多个物种（酵母、人类细胞系）上比较加入结构先验前后的 TFA 推断精度和 GRN 恢复 AUPR
   - **创新状态**：unverified

2. **候选名称**：ERV-Guided Active Learning for TF–DNA Binding Assay Design
   - **来源局限/观察**：ERV 可识别预测性最强的 TF–基因连接，但未用于指导实验设计
   - **核心假设**：ERV 高的不确定连接是实验验证的最佳候选，可最大化信息增益
   - **初步方法**：在 SupirFactor 框架中计算 ERV 的不确定性（如通过多次初始化或 dropout），选择高 ERV 方差/低 ERV 的连接进行 ChIP-seq 或报告基因实验验证
   - **验证方式**：模拟实验设计（用已有 ChIP-seq 数据模拟"待验证"连接），比较 ERV 引导选择与随机选择的验证效率
   - **创新状态**：unverified

3. **候选名称**：Multi-Modal Structure-Aware GRN Inference with AlphaFold TF Complexes
   - **来源局限/观察**：SupirFactor 的 mTF 层建模 TF-TF 互作，但未利用 TF 复合物的结构信息
   - **核心假设**：AlphaFold 预测的 TF-TF 复合物结构可作为 mTF 层权重的先验，提升通路推断精度
   - **初步方法**：使用 AlphaFold-Multimer 预测 TF-TF 互作结构，将预测界面残基的保守性编码为 Π 矩阵的初始化
   - **验证方式**：在酵母和人类数据上比较结构先验 mTF 层与随机初始化的通路富集精度
   - **创新状态**：unverified

4. **候选名称**：TFA-Guided Molecular Dynamics Sampling of TF–DNA Binding
   - **来源局限/观察**：SupirFactor 推断的 TFA 是统计 latent 变量，未与物理结合动力学关联
   - **核心假设**：高 TFA 的 TF 在 DNA 上的结合构象更稳定（更低自由能），TFA 可作为 MD 模拟的增强采样权重
   - **初步方法**：对高 TFA 的 TF–DNA 复合物进行加权 MD 模拟（如 metadynamics），比较不同 TFA 水平下的结合自由能
   - **验证方式**：对已知结构 TF–DNA 复合物（如 p53、GCN4）计算 TFA，与 MD 模拟的结合自由能关联分析
   - **创新状态**：unverified

5. **候选名称**：Cross-Species Transfer Learning with Structure-Primed GRN Priors
   - **来源局限/观察**：SupirFactor 在单一物种上训练，未利用跨物种保守的调控信息
   - **核心假设**：跨物种保守的 TF–DNA 结合 motif 可作为迁移学习的桥梁，提升低资源物种的 GRN 推断
   - **初步方法**：在模式物种（酵母、人类）上预训练 SupirFactor，将编码器权重映射到目标物种（如非模式植物、微生物），利用保守 motif 初始化先验 P
   - **验证方式**：在多个非模式物种的公开数据上比较迁移学习与从头训练的 GRN 恢复 AUPR
   - **创新状态**：unverified