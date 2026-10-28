## 01 基本信息
- **标题**: Using single cell atlas data to reconstruct regulatory networks
- **作者与单位**: Song, Qi; Ruffalo, Matthew; Bar-Joseph, Ziv (Carnegie Mellon University, 未提供具体单位)
- **期刊/预印本平台**: Nucleic Acids Research
- **年份**: 2023-02-11
- **论文类型**: 方法学（Method）
- **领域**: 计算生物学 / 系统生物学 / 单细胞基因组学
- **关键词**: 基因调控网络、转录因子、RNA velocity、多任务学习、单细胞ATAC-seq、HuBMAP
- **DOI/arXiv 号**: 10.1093/nar/gkad053
- **代码**: https://github.com/alexQiSong/MTLRank
- **数据**: HuBMAP 数据门户 (https://portal.hubmapconsortium.org/)，Cistrome 数据库
- **阅读日期**: 未提供
- **在该课题方向中的位置**: 本文属于「TF–DNA 互作 × 深度学习」方向，核心创新在于将 RNA velocity（而非静态表达量）作为预测目标，并整合 scATAC-seq 衍生的 TF 活性分数，通过多任务学习框架在 HuBMAP 6 组织图谱规模数据上重建组织特异性调控网络。对 TF–DNA 结合机制研究的启示在于：用动态转录速率替代静态表达量可缓解 TF 表达与靶基因表达之间的时间延迟问题，且染色质可及性数据可部分反映 TF 的翻译后激活状态。

## 02 一句话总结
本文提出 MTLRank，一种结合神经网络与多任务学习的框架，以 TF 表达和基于 scATAC-seq 的 TF 活性分数为输入、RNA velocity 为预测目标，在 HuBMAP 6 组织单细胞图谱数据上重建组织特异性 TF–基因调控网络，并通过 TF 组织标记物召回率和扰动数据验证了其优于现有方法。

## 03 研究问题
- **具体问题**: 如何从大规模单细胞图谱数据中准确推断全局、组织特异性的 TF–基因调控网络？
- **为什么重要**: 调控网络重建是系统生物学的长期目标；组织特异性调控网络有助于理解器官功能、发育和疾病机制。
- **现有方法为何不足**:
  1. 多数方法依赖小规模数据集或静态快照数据，无法捕捉调控过程固有的时间动态性；
  2. TF 表达与靶基因表达之间存在时间延迟，静态表达相关性会产生假阳性和假阴性；
  3. 许多 TF 受翻译后修饰调控，mRNA 表达水平不能直接反映其活性；
  4. 现有方法难以整合多种数据类型（表达、染色质可及性、TF 结合位点）。
- **精确的 "Can ... ?" 研究问题**: Can we improve TF–gene regulatory network inference by predicting RNA velocity (rather than static gene expression) using a multi-task deep learning framework that integrates TF expression, TF activity scores from scATAC-seq, and TF binding site information from ChIP-seq, applied to atlas-scale single-cell data?

## 04 背景与发展脉络
- **早期方法（微阵列时代）**: 基于 TF 表达与靶基因表达的统计相关性（如共表达、互信息）推断调控关系。局限：无法处理非线性关系和时间延迟。
- **回归/信息论方法**: LARS、LASSO 等线性回归模型，GENIE3（随机森林）、GRNBoost2（梯度提升树）等非线性方法。局限：主要使用静态表达数据，未利用染色质可及性和 TF 结合位点信息。
- **整合多组学方法**: 部分方法引入 ChIP-seq、ATAC-seq、motif 信息和蛋白质互作数据。局限：仍以预测表达值为目标，未考虑转录动态性。
- **单细胞时代**: 单细胞数据提供了同一细胞内多基因共表达信息，但静态表达问题依然存在。
- **本文主张的位置**: 首次将 RNA velocity 作为预测目标引入调控网络推断，结合多任务学习实现跨基因参数共享，并整合 scATAC-seq 衍生的 TF 活性分数，在 HuBMAP 图谱规模数据上实现组织特异性网络重建。
- **脉络标注**: 以上脉络基于本文 Introduction 的叙述框架，未经外部系统核验。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 时间延迟导致假阳/假阴 | TF 表达与靶基因表达不同步，静态相关性无法反映因果关系 | TF 结合与靶基因转录积累之间存在时间差，快照数据无法捕捉动态过程 | Introduction 第 2 段："expression levels of genes may not correlate with that of their regulating TFs due to the time delay between TF binding and the accumulation of expressions" |
| 翻译后修饰导致表达-活性脱节 | 高表达的 TF 可能不活跃，低表达的 TF 可能高度活跃 | 许多 TF 受翻译后修饰（如磷酸化）调控，mRNA 水平不能代表蛋白活性 | Introduction 第 3 段："many TFs are post-translationally activated... high expression levels may not be directly correlated to activity" |
| 静态表达作为预测目标的局限 | 以表达值作为模型输出无法反映基因当前的调控状态 | 表达值是累积结果，不代表当前转录速率 | Introduction 第 4 段："these methods have also attempted to use the interaction information to predict gene expression which... may not reflect the current activation level of the target gene" |
| 数据规模不足 | 小数据集导致模型泛化差、网络覆盖不全 | 以往研究缺乏大规模、多组织、多供体的单细胞图谱数据 | Introduction 第 5 段："our method integrates much larger single cell data from recent atlas studies (HuBMAP)" |
| 跨组织泛化困难 | 单一组织模型难以迁移到其他组织 | 不同组织具有不同的细胞组成和调控环境 | 多任务学习框架设计（Methods "MTLRank framework" 节） |

## 06 核心思想
1. **表面方法**: 构建多任务深度神经网络，每个靶基因作为一个任务（输出单元），输入为所有 TF 的表达值和 TF 活性分数，预测目标为靶基因的 RNA velocity。训练后通过 deep SHAP 计算每个 TF 对靶基因预测的贡献，据此排序并构建调控网络。
2. **核心洞察**:
   - RNA velocity 比静态表达量更能反映基因的实时转录活性，因此是更好的调控关系预测目标；
   - TF 活性分数（由 scATAC-seq 可及性和 ChIP-seq 结合位点计算）可部分捕捉 TF 的翻译后激活状态，弥补表达数据的不足；
   - 多任务学习通过 trace norm 正则化实现"软共享"，使相关基因的模型参数相互借鉴，减少过拟合并提高泛化。
3. **可能的普适教训** [Analysis]: 在生物序列/调控预测任务中，选择与生物学过程时间尺度匹配的预测目标（如速率而非状态）可能比增加模型复杂度更有效；整合多种数据模态时，应优先选择能反映"活性"而非"丰度"的特征。

## 07 方法总览
- **输入**:
  - TF 表达矩阵 X（scRNA-seq，RPKM，经 log10 和标准化处理）
  - TF 活性分数矩阵 A^(sum) 和 A^(mean)（由 scATAC-seq 峰与 ChIP-seq 结合位点重叠计算）
- **输出**: 每个靶基因的 RNA velocity 预测值
- **模型结构**: 多层神经网络；输入层 → TF 聚合层（每个 TF 一个神经元，融合其表达和活性分数）→ 三个全连接层（64、32、16 神经元）→ 输出层（预测 velocity）
- **多任务学习**: 每个靶基因作为一个任务；通过 trace norm 正则化对 FC1 和 FC2 层进行参数共享（软共享），FC3 和输出层为任务特异
- **损失函数**: 均方误差（MSE）+ L1 正则化 + trace norm 正则化
- **优化器**: Adam（TensorFlow 2.7.0）
- **训练策略**: 按细胞划分训练/测试集（9:1），每个基因独立处理缺失 velocity 的细胞；每个基因簇内共享参数
- **推断**: 训练完成后，用 deep SHAP 对每个靶基因的模型计算各 TF 的贡献值，按贡献排序取 top 50 作为该基因的候选调控因子
- **反馈回路**: 无显式反馈回路；模型为前馈结构
- **文字流程**: 数据预处理（scRNA-seq 定量、velocity 计算、scATAC-seq 峰 calling、TF 活性分数计算）→ 特征标准化 → 基因聚类（约束 k-means，每簇 24-25 基因）→ 每簇训练多任务网络 → deep SHAP 计算 TF 重要性 → 构建调控网络 → 验证

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| TF 活性分数计算 | 将 scATAC-seq 可及性与 ChIP-seq 结合位点整合为 TF 活性度量 | 表达量无法反映 TF 翻译后激活状态，可及性数据提供补充信号 | 输入：scATAC-seq 峰、ChIP-seq 结合位点；输出：A^(sum)、A^(mean) 矩阵 | Methods "TF activity score" 节；Results 图 2A-B 显示加入活性分数后性能提升 | 预期影响：模型性能下降，尤其对翻译后调控显著的 TF（未做单独消融实验） |
| TF 聚合层 | 每个 TF 一个神经元，融合其表达值和活性分数 | 将多模态 TF 特征压缩为单一表示 | 输入：TF 表达 + 活性分数；输出：TF 聚合表示 | Methods "Model architecture" 节 | 预期影响：模型无法整合多模态信息，性能下降 |
| 多任务学习（trace norm 软共享） | 在基因簇内共享 FC1/FC2 层参数 | 相关基因共享调控机制，参数共享可减少过拟合、提高泛化 | 输入：多个靶基因任务；输出：共享层 + 任务特异层 | Methods "Model architecture and loss function" 节；引用 (44) 证明 trace norm 有效性 | 预期影响：模型过拟合风险增加，泛化能力下降（未做单独消融实验） |
| deep SHAP 归因 | 计算每个 TF 对靶基因 velocity 预测的贡献 | 模型本身不直接输出调控关系，需要解释性方法提取 | 输入：训练好的模型 + 输入样本；输出：每个 TF 的 SHAP 值 | Methods "Ranking TFs using deep SHAP" 节 | 预期影响：无法从模型中提取调控关系，网络构建失败 |
| 基因聚类（约束 k-means） | 将基因分为 24-25 个簇，簇内共享参数 | 降低计算复杂度，同时保证簇内基因调控机制相似 | 输入：velocity 矩阵；输出：基因簇 | Methods "Model architecture" 节 | 预期影响：计算开销增大；若聚类不合理，共享参数反而损害性能 |

## 09 关键公式符号
1. **TF 活性分数**:
   - A^(sum)_(i,j) = Σ_k S(p_(TF(i,j,k)), P^(atac)_(i,j,k))
   - A^(mean)_(i,j) = (1/m) Σ_k S(p_(TF(i,j,k)), P^(atac)_(i,j,k))
   - 其中 S 计算 ChIP-seq 结合位点 p 与 scATAC-seq 峰 P 的重叠比例；m 为结合位点数量
   - 用途: 量化 TF i 对基因 j 启动子区域的调控潜力
   - 直觉: 结合位点处染色质开放程度越高，TF 越可能结合并调控该基因

2. **缩放变换**:
   - A^(sum) = log2(A^(sum) + 1)
   - 用途: 压缩动态范围，减少极端值影响

3. **损失函数**:
   - L = (1/T) Σ_i (1/N(i)) Σ_c (Y_(i,c) - f(A^(sum)_(i,·), A^(mean)_(i,·), E_(c,·), θ))² + λ Σ_i Σ_k ||W^[i,k]||₁ + γ Σ_k ||W'^[k]||_*
   - 其中 T 为任务数，N(i) 为任务 i 的样本数，Y 为真实 velocity，f 为网络输出，W 为权重矩阵，||·||₁ 为 L1 范数，||·||_* 为 trace norm（核范数）
   - 用途: 联合优化预测精度、模型稀疏性和跨任务参数共享
   - 直觉: L1 促进稀疏连接，trace norm 鼓励共享层参数矩阵低秩（即任务间共享信息）

4. **trace norm 梯度**:
   - ∂||W'||_* / ∂W' = UV^T
   - 其中 W' = UΣV^T 为奇异值分解
   - 用途: 反向传播中计算 trace norm 的次梯度

## 10 实验设计与证据链
- **数据集**: HuBMAP 6 组织（肝、脾、左肾、右肾、右肺、大肠），29 个供体；scRNA-seq 细胞数 4,656–93,640；scATAC-seq 细胞数 8,368–310,661
- **指标**: R²（预测 velocity 的拟合优度）；TF 组织标记物召回率（recall of tissue-specific TF markers）
- **基线方法**: LASSO 回归、无参数共享的 NN、GENIE3、GRNBoost2、CellOracle
- **验证数据**: TF-Marker 数据库（组织特异性 TF 标记物）；JUN 扰动 scRNA-seq 数据（人类 CAR-T 细胞）
- **评测协议**: 5 折交叉验证（R²）；TF 标记物召回率比较；扰动数据中检查 JUN 靶基因的富集

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| R² 预测性能比较 | MTLRank 预测 velocity 优于预测表达量 | MTLRank (velocity) vs MTLRank (expression) vs LASSO vs NN vs GENIE3 vs GRNBoost2 | MTLRank 在 velocity 预测上 R² 最高；velocity 作为目标优于 expression | 以 RNA velocity 为目标可提高预测精度 | 未与其他 velocity-based 方法比较 | Results 图 2A |
| 活性分数贡献评估 | 加入 TF 活性分数可提高性能 | 有/无活性分数输入的 MTLRank 对比 | 加入活性分数后 R² 提升（尤其 SNARE-seq 数据） | 染色质可及性信息对调控推断有补充价值 | 提升幅度因组织而异，非所有组织均显著 | Results 图 2A-B |
| TF 标记物召回率 | MTLRank 识别的 TF 富集已知组织标记物 | MTLRank vs 随机选择 | MTLRank 召回率显著高于随机；肝、肾、肺显著富集 | 预测的调控网络包含已知组织特异性 TF | 召回率绝对值仍有限，存在大量未验证预测 | Results 图 2C、表 3 |
| JUN 扰动验证 | MTLRank 识别的 JUN 靶基因在扰动后差异表达 | JUN 扰动前后差异表达基因 vs MTLRank 预测的 JUN 靶基因 | 预测靶基因显著富集于扰动响应基因 | 预测的调控关系具有功能相关性 | 仅验证单个 TF，未覆盖全部预测 | Results "Evaluation based on TF perturbation data" 节 |
| 组织特异性网络分析 | 网络富集组织特异功能通路 | 各组织网络的 GSEA 分析 | 肝富集药物代谢、脾富集 Th1/Th2 分化、肾富集钙信号通路 | 网络具有生物学可解释性 | 通路富集基于已知注释，存在循环验证风险 | Results "Tissue-specific networks" 节 |

## 11 结论正确解读
- **任务范围**: 本文解决的是 TF–基因调控关系的推断问题，输出为组织特异性的 TF–靶基因排序列表，而非直接的物理结合事件（如 ChIP-seq 结合峰或结构层面的 TF–DNA 相互作用）。
- **Oracle/真值输入**: 训练阶段使用 scRNA-seq 计算的 RNA velocity 作为监督信号；TF 活性分数由 ChIP-seq 结合位点（Cistrome 数据库）和 scATAC-seq 峰计算，其中 ChIP-seq 数据来自 bulk 实验而非单细胞。
- **端到端状态**: 方法端到端可运行，从原始单细胞数据到网络输出；但依赖外部数据库（Cistrome、TF-Marker）提供先验信息。
- **算力成本**: 未提供具体训练时间或硬件需求；但多任务学习 + deep SHAP 在数千基因 × 数万细胞规模上计算成本较高（作者在 Discussion 中提到大规模训练的挑战）。
- **历史数据依赖**: 依赖 HuBMAP 特定组织/供体的数据；ChIP-seq 数据来自 Cistrome 数据库，可能引入组织不匹配的偏差。
- **模型依赖**: 深度神经网络 + trace norm 多任务学习；性能依赖基因聚类质量、超参数选择。
- **最难情形**: 低表达基因（velocity 信号弱）、翻译后调控为主的 TF（表达与活性脱节）、scATAC-seq 数据质量差的组织。
- **群体/领域边界**: 仅适用于人类组织；未测试其他物种或细胞系；组织特异性网络可能无法泛化到疾病状态。
- **不确定性**: 预测的调控关系缺乏直接实验验证（除 JUN 扰动外）；R² 绝对值未报告（仅相对比较）；TF 标记物召回率受数据库完整性限制。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 训练数据规模受限 | 每个基因的可用细胞数受限于 velocity 计算要求；部分组织细胞数较少 | 随着更多图谱数据发布，可扩展训练数据 | Discussion 第 1 段 |
| 超参数调优困难 | 数千个模型需要分别调参，计算成本高 | 开发更高效的调参策略或自适应方法 | Discussion 第 2 段 |
| 缺乏金标准验证 | 组织特异性调控网络缺乏系统性实验验证 | 结合 CRISPR 筛选或 Perturb-seq 数据进行验证 | Discussion 第 3 段 |
| 活性分数计算依赖 bulk ChIP-seq | scATAC-seq 与 bulk ChIP-seq 数据来自不同实验条件，可能引入偏差 | 使用单细胞 ChIP-seq 或 TF  footprinting 方法改进 | Methods "TF activity score" 节 |
| 未充分利用时间信息 | RNA velocity 仅反映瞬时速率，未建模更长时间尺度的动态 | 整合谱系追踪或多时间点数据 | Discussion 第 4 段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|----------|----------|------|
| R² 仅用于相对比较，未报告绝对值 | R² 绝对值可能很低，模型解释力有限 | 相对提升可能掩盖整体预测精度不足 | 报告 R² 绝对值及与简单基线（如均值预测）的对比 | Results 图 2A 仅显示相对比较 |
| TF 标记物召回率以数据库为金标准 | TF-Marker 数据库本身可能不完整或有偏 | 召回率可能低估或高估模型性能 | 使用独立实验数据（如 CRISPR 扰动）验证 | Results "Evaluation based on recall of marker TFs" 节 |
| 活性分数计算中 ChIP-seq 与 scATAC-seq 数据不匹配 | bulk ChIP-seq 来自不同细胞类型/条件，可能不代表单细胞状态 | 活性分数可能引入系统性偏差 | 使用同一细胞的 multi-omic 数据（如 10x Multiome）验证 | Methods "TF activity score" 节 |
| 多任务学习仅在基因簇内共享参数 | 基因簇划分基于 velocity 相似性，可能不反映真实调控模块 | 不合理的聚类可能损害共享效果 | 比较不同聚类策略对结果的影响 | Methods "Model architecture" 节 |
| deep SHAP 归因的可靠性未验证 | SHAP 值在高度非线性模型中的解释性可能不稳定 | 调控关系排序可能受解释方法偏差影响 | 与置换重要性、梯度等方法对比 | Methods "Ranking TFs using deep SHAP" 节 |
| 未与最新的基于物理/结构的方法比较 | AlphaFold 等结构预测方法可能提供互补信息 | 无法判断深度学习方法的相对优势 | 在相同数据集上比较不同方法 | 全文未提及结构预测方法 |

## 14 学到什么
**Agent 提炼的知识候选**:
1. **预测目标选择**: 在 TF–DNA 调控推断中，用 RNA velocity 替代静态表达量作为监督信号，可缓解 TF 表达与靶基因表达之间的时间延迟问题。迁移到本课题：在构建 TF–DNA 结合预测模型时，可考虑将动态转录速率（而非稳态表达）作为训练标签，以更贴近结合事件的实时性。
2. **活性分数设计**: 将 scATAC-seq 可及性与 ChIP-seq 结合位点整合为 TF 活性分数，可部分捕捉翻译后激活状态。迁移到本课题：在预测 TF–DNA 结合时，可引入染色质可及性作为特征，而非仅依赖序列 motif；对无法从表达量推断活性的 TF（如受磷酸化调控的 TF），可及性数据是重要补充。
3. **多任务学习策略**: 通过 trace norm 正则化实现"软共享"，使相关基因的模型参数相互借鉴。迁移到本课题：在预测多个 TF 或多个靶基因的结合时，可考虑多任务框架共享底层特征（如染色质状态、序列特征），尤其当某些 TF 训练样本稀少时。
4. **归因方法选择**: deep SHAP 可从黑盒模型中提取每个 TF 的贡献值，用于构建调控网络。迁移到本课题：在深度学习模型中，SHAP 类归因方法可用于从预测模型中提取 TF–DNA 结合的关键序列特征或 motif，增强模型可解释性。
5. **验证策略**: 使用组织特异性 TF 标记物召回率和扰动数据验证预测，而非仅依赖拟合优度。迁移到本课题：在验证 TF–DNA 结合预测时，应结合实验扰动数据（如 TF 敲低/过表达后的靶基因变化）和已知结合位点数据库进行多维度验证。

## 15 与已有知识连接
- **相似方法**: 与 GENIE3 (6)、GRNBoost2 (5) 等基于表达相关性的调控网络推断方法同属一个任务家族，但本文创新性地引入 RNA velocity 和多任务深度学习。与 CellOracle (48) 类似，均整合染色质可及性数据，但 CellOracle 使用线性模型，本文使用深度网络。
- **理论基础**: RNA velocity 方法源于 La Manno et al. (2018) 的 spliced/unspliced 比例模型，本文将其作为监督信号，连接了转录动力学与调控推断。
- **可迁移领域**: 多任务学习 + trace norm 正则化可迁移到其他单细胞多组学整合任务（如 scRNA-seq + scATAC-seq 的细胞类型注释）；deep SHAP 归因可迁移到任何需要从深度学习模型提取生物学特征的场景。
- **与结构预测的潜在连接** [Analysis]: 本文未使用 AlphaFold 等结构预测工具，但其预测的 TF–基因调控关系可作为结构生物学研究的候选列表，用于优先选择进行分子动力学模拟或共结晶实验的 TF–DNA 复合物。
- **与分子模拟的潜在连接** [Analysis]: 本文预测的调控网络可提供 TF–靶基因候选对，这些候选对可用于指导分子对接模拟，验证 TF 与靶基因启动子区的物理结合。

## 16 研究想法
**Agent 生成的研究候选**:

1. **候选名称**: 结合 RNA velocity 与结构预测的 TF–DNA 结合亲和力预测
   - **来源局限/观察**: MTLRank 预测调控关系但未提供结合亲和力或物理结合证据；AlphaFold 等结构预测工具可预测 TF 结构但未整合转录动态信息。
   - **核心假设**: 将 RNA velocity 衍生的调控关系作为先验，可提高 TF–DNA 结合亲和力预测的准确性。
   - **初步方法**: 使用 MTLRank 输出的 TF–靶基因排序作为训练权重，结合 AlphaFold 预测的 TF 结构和 DNA 序列特征，训练一个结合亲和力预测模型。
   - **验证方式**: 在已知 TF–DNA 复合物结构数据集（如 PDB）上评估预测精度，并与未使用调控先验的基线模型对比。
   - **创新状态**: unverified

2. **候选名称**: 基于多任务学习的 TF 活性动态建模与结合位点预测
   - **来源局限/观察**: MTLRank 使用静态 TF 活性分数（由 scATAC-seq 和 ChIP-seq 计算），未建模 TF 活性的时间动态；TF 的翻译后修饰状态随时间变化。
   - **核心假设**: 将 TF 活性的时间动态纳入模型可提高结合位点预测的准确性。
   - **初步方法**: 使用时序单细胞数据（如分化时间序列）计算 TF 活性的时间轨迹，作为多任务学习的额外输入，预测 TF 结合位点的动态变化。
   - **验证方式**: 使用 ChIP-seq 时间序列数据验证预测的结合位点是否随时间变化。
   - **创新状态**: unverified

3. **候选名称**: 整合调控网络与分子模拟的 TF–DNA 互作机制解析
   - **来源局限/观察**: MTLRank 预测的调控网络缺乏物理结合机制层面的解释；分子模拟可提供结合自由能但计算成本高，无法全基因组扫描。
   - **核心假设**: 调控网络预测的 TF–靶基因候选对可作为分子模拟的优先列表，提高模拟效率。
   - **初步方法**: 从 MTLRank 预测的网络中提取高置信度 TF–靶基因对，使用分子对接和分子动力学模拟计算结合自由能，验证调控预测的物理基础。
   - **验证方式**: 比较模拟预测的结合亲和力与实验数据（如表面等离子共振）的相关性。
   - **创新状态**: unverified

4. **候选名称**: 跨组织 TF 协同调控的图神经网络建模
   - **来源局限/观察**: MTLRank 分别构建各组织网络，未显式建模 TF 跨组织的协同调控关系。
   - **核心假设**: TF 在不同组织中的协同调控模式可被图神经网络捕获，提高网络推断的准确性。
   - **初步方法**: 将 6 组织网络作为多层图，使用图神经网络学习 TF 的跨组织嵌入表示，联合预测调控关系。
   - **验证方式**: 在留一组织交叉验证中评估预测性能，并与单组织模型对比。
   - **创新状态**: unverified