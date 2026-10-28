## 01 基本信息
- **标题**：Cross-modal contrastive learning decodes developmental regulatory features through chromatin potential analysis
- **作者与单位**：Yang, Yueyuxiao; Xie, Chenxi; He, Qiushun; Yang Meng（单位未提供）
- **期刊/预印本平台**：GigaScience
- **年份**：2025
- **论文类型**：方法学（Method）+ 应用研究
- **领域**：单细胞多组学整合、计算调控基因组学、深度学习
- **关键词**：cross-modal contrastive learning, chromatin accessibility, gene expression, regulatory interaction, chromatin potential, single-cell multiomics
- **DOI/arXiv 号**：10.1093/gigascience/giaf053
- **代码**：https://github.com/melobio/Attune
- **数据**：10x Multiome (PBMC10k)、SHARE-seq (mouse skin, GSE140203)、NeurIPS 2021 (GSE194122)、Greenleaf 2021 (GSE162170)
- **阅读日期**：未提供
- **在该方向中的位置**：本文属于「单细胞多组学 × 对比学习」方向，核心是整合 scRNA-seq 与 scATAC-seq 两种模态，通过跨模态对比学习对齐基因表达与染色质可及性，并利用 Transformer 交叉注意力推断基因-峰（gene–peak）调控互作。与 TF–DNA 结合机制的直接关系在于：其推断的 peak–gene 调控关系可视为 TF 结合位点（peak）与靶基因表达之间的关联性建模，为从染色质可及性数据中推断 TF 调控网络提供了可迁移的深度学习框架。

## 02 一句话总结
本文提出 Attune，一种基于跨模态对比学习的框架，将同一细胞的 scRNA-seq 与 scATAC-seq 数据在共享嵌入空间中对齐，并通过 Transformer 交叉注意力推断基因-峰调控互作，在毛囊成熟数据集中揭示了转录因子 Gli3 的染色质电位（chromatin potential）及其在谱系特化中的调控作用。

## 03 研究问题
- **具体问题**：如何从配对单细胞多组学数据（同一细胞的染色质可及性与基因表达）中整合信息，并进一步推断基因表达与染色质调控元件之间的调控关系？
- **为什么重要**：基因表达受染色质可及性调控，TF 结合开放染色质区域（peaks）以启动或抑制转录。配对多组学数据提供了在同一细胞中同时观察"调控输入"（染色质）与"调控输出"（转录）的机会，但现有方法多聚焦于整合或预测，缺乏对调控机制的深入解析。
- **现有方法不足**：已有整合方法（如 Seurat V4、MultiVI、BABEL）主要关注嵌入对齐或跨模态预测，但未充分利用细粒度特征（单个基因、单个 peak）之间的对应关系；GLUE 虽引入调控图先验，但依赖外部注释且难以发现新调控关系。
- **精确研究问题**：Can a cross-modal contrastive learning framework with Transformer-based cross-attention align paired scRNA-seq and scATAC-seq data while simultaneously inferring gene–peak regulatory interactions that reflect developmental regulatory features?

## 04 背景与发展脉络
- **阶段一：单模态分析**。scRNA-seq 与 scATAC-seq 分别独立分析，通过相关性或共定位推断调控关系。局限：无法在同一细胞中直接关联两种模态。
- **阶段二：多组学整合**。Seurat V4、MultiVI、BABEL 等方法将多模态数据映射到共享嵌入空间，实现细胞对齐与跨模态预测。局限：主要面向整合与预测，缺乏调控关系推断能力。
- **阶段三：调控关系建模**。GLUE 引入 guidance graph 显式建模 cis-regulatory 关系；Cicero 利用共可及性推断 peak–gene 连接。局限：依赖先验注释或仅捕捉共变异，难以发现动态调控变化。
- **本文位置**：提出 Attune，将对比学习预训练与 Transformer 交叉注意力结合，在整合多模态数据的同时，通过注意力权重直接推断 gene–peak 调控关系，并利用残差（residual）定义"染色质电位"以捕捉调控延迟。
- **脉络核验**：以上脉络基于本文引言与讨论部分，属「仅本文框架」，未经外部系统核验。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 多模态整合与调控推断分离 | 现有方法要么只做整合（Seurat V4、MultiVI），要么只做预测（BABEL），缺乏统一框架 | 整合方法未利用细粒度特征对应关系，预测方法未建模调控机制 | 引言：现有方法"predominantly focused on integration or prediction tasks" |
| 调控关系推断依赖先验 | GLUE 需 guidance graph 先验，Cicero 仅捕捉共可及性 | 先验注释不完整，共变异无法区分直接与间接调控 | 引言：GLUE "explicitly model cis-regulatory interactions"，Cicero 基于共可及性 |
| 染色质可及性与转录存在时间延迟 | 同一细胞中染色质开放与基因表达不完全同步，导致直接比较失真 | 染色质开放先于转录，存在调控延迟 | 讨论：提出 residual 作为"chromatin potential"以捕捉延迟 |
| 细粒度调控关系难以从嵌入中提取 | 细胞级嵌入保留整体信息，但丢失基因-峰级别的对应关系 | 嵌入维度有限，无法保留所有特征级关系 | 方法：引入 Transformer 交叉注意力在特征级建模 gene–peak 关系 |

## 06 核心思想
1. **表面方法**：Attune 采用双塔结构，分别编码 scRNA-seq 与 scATAC-seq 数据，通过跨模态对比学习（NT-Xent loss）将同一细胞的两种模态表示在共享嵌入空间中对齐。预训练后，通过 Transformer 解码器对基因嵌入和 peak 嵌入进行交叉注意力计算，得到 gene–peak 注意力权重作为调控关系强度。此外，通过计算预测表达与实际表达的残差定义"染色质电位"。
2. **核心洞察**：对比学习不仅实现模态对齐，还通过教师-学生网络（teacher–student）的异步设计捕捉模态间的信息差异；Transformer 交叉注意力天然适合建模基因与 peak 之间的成对关系，注意力权重可直接解释为调控强度；残差（预测 vs 实际表达）反映了染色质已开放但转录尚未完成的"电位"状态。
3. **可能的普适教训** [Analysis]：将对比学习从"对齐"升级为"关系推断"的关键在于在特征级别（而非仅细胞级别）建立跨模态对应；注意力机制的可解释性使其成为从深度学习模型中提取生物学关系的有效工具；"残差"作为一种简单但有效的策略，可捕捉时间延迟或状态转换信号。

## 07 方法总览
- **输入**：配对的 scRNA-seq 基因表达矩阵（基因 × 细胞）与 scATAC-seq peak 计数矩阵（peak × 细胞），同一细胞两种模态配对。
- **输出**：① 对齐的细胞嵌入（用于整合与可视化）；② gene–peak 注意力权重矩阵（用于调控关系推断）；③ 每个基因的染色质电位（残差）。
- **模块**：
  1. 预处理：基因/peak 过滤（<5% 细胞表达/可及）、归一化、HVG 选择（2,000 基因）
  2. 教师-学生网络：RNA 教师网络（层次注意力）与 ATAC 教师网络，分别编码两种模态
  3. 对比学习：NT-Xent loss，拉近同一细胞两种模态的嵌入，推远不同细胞
  4. Transformer 解码器：对基因嵌入和 peak 嵌入进行自注意力和交叉注意力，输出 gene–peak 注意力权重
  5. 模态预测网络：MLP 从 ATAC 嵌入预测基因表达
- **训练**：对比预训练 20 epochs（Adam，lr 1e-4 至 1e-6）；Transformer 5 epochs；预测网络 40 epochs；温度系数 0.1，batch size 32，嵌入维度 128
- **反馈回路**：对比学习损失 → 更新教师-学生网络；预测损失 → 更新 MLP；Transformer 注意力权重 → 下游调控推断
- **文字流程**：输入配对矩阵 → 教师-学生网络分别编码 → 对比学习对齐嵌入 → 预训练完成 → 冻结编码器 → Transformer 解码器接收基因/peak 嵌入 → 交叉注意力计算 gene–peak 权重 → 注意力权重用于调控关系评估 → 同时 MLP 从 ATAC 预测表达 → 残差 = 预测 − 实际 → 残差作为染色质电位

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 教师-学生网络（RNA/ATAC） | 分别编码两种模态，生成细胞级嵌入 | 将高维稀疏的基因/peak 计数压缩为低维稠密表示，便于对比对齐 | 输入：基因计数/peak 计数；输出：128 维嵌入 | 对比学习对齐效果优于其他方法（Fig. 2A-B） | 预期：失去模态特异性特征提取能力，对齐质量下降 [预期效应] |
| 跨模态对比学习（NT-Xent） | 拉近同一细胞两种模态嵌入，推远不同细胞 | 建立跨模态对应关系，使嵌入空间具有生物学意义 | 输入：RNA/ATAC 嵌入对；输出：对比损失 | 消融实验显示对比对象设计影响整合效果（Supplementary Table S7） | 实测：对比对象改变导致整合性能下降（Supplementary Table S7） |
| Transformer 交叉注意力 | 建模 gene–peak 成对关系，输出注意力权重 | 在特征级别建立跨模态对应，推断调控关系 | 输入：基因嵌入序列 + peak 嵌入序列；输出：注意力权重矩阵 | 注意力权重可反映 promoter 互作（Fig. 3B，AUC 评估） | 预期：失去调控关系推断能力，仅剩整合功能 [预期效应] |
| 模态预测网络（MLP） | 从 ATAC 嵌入预测基因表达 | 实现跨模态预测，并产生残差用于染色质电位分析 | 输入：ATAC 嵌入；输出：预测表达值 | 预测性能优于 BABEL 等（Fig. 2F-G） | 预期：无法进行表达预测，残差分析不可行 [预期效应] |
| 残差计算（染色质电位） | 预测表达 − 实际表达 | 捕捉染色质已开放但转录未完成的延迟状态 | 输入：预测/实际表达；输出：残差向量 | Gli3 残差在毛囊分化中呈现显著模式（Fig. 3G-H） | 预期：失去对调控延迟的检测能力 [预期效应] |

## 09 关键公式符号
- **NT-Xent loss**（对比学习核心）：
  \[
  \ell(m, m^+) = -\log \frac{\exp(\text{sim}(z_m^{RNA}, z_{m^+}^{ATAC})/\tau)}{\sum_{k=1}^{2N} \mathbb{1}_{[k \neq m]} \exp(\text{sim}(z_m^{RNA}, z_k^{ATAC})/\tau)}
  \]
  - \( z_m^{RNA} \)：细胞 m 的 RNA 嵌入（教师网络输出）
  - \( z_{m^+}^{ATAC} \)：同一细胞 m 的 ATAC 嵌入（正样本）
  - \( \text{sim}(\cdot, \cdot) \)：余弦相似度
  - \( \tau \)：温度系数（默认 0.1）
  - \( N \)：batch 内细胞数；\( 2N \) 为总样本数（两种模态各 N）
  - 用途：最大化同一细胞两种模态嵌入的一致性，最小化不同细胞间的相似度
  - 直觉：将"同一细胞"作为跨模态正样本对，迫使网络学习模态无关的细胞身份表示

- **总预训练目标**：
  \[
  \mathcal{L}_{\text{total}} = \mathcal{L}_{\text{NT-Xent}}^{\text{teacher}} + \mathcal{L}_{\text{NT-Xent}}^{\text{student}}
  \]
  - 教师与学生对分别计算对比损失，共同优化

- **Transformer 交叉注意力**：
  \[
  \text{CrossAttention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right) V
  \]
  - \( Q = \text{self\_gene\_hidden}_i \)（基因侧查询）
  - \( K, V = \text{peak\_hidden}_j \)（peak 侧键值）
  - \( d_k \)：注意力维度
  - 用途：计算每个基因对每个 peak 的注意力权重，作为调控关系强度
  - 直觉：基因作为查询，关注其周围（1.2 Mb 内）的 peak，注意力权重反映调控可能性

- **残差（染色质电位）**：
  \[
  \text{Residual}_g = \text{Predicted\_Expression}_g - \text{Measured\_Expression}_g
  \]
  - 预测表达来自 MLP（输入 ATAC 嵌入），实际表达来自 scRNA-seq
  - 用途：正值表示染色质已开放但转录未跟上（电位高），负值表示转录已发生但染色质关闭
  - 直觉：捕捉染色质可及性与转录之间的时间延迟

## 10 实验设计与证据链
- **数据集**：
  - 10x Multiome PBMC10k（n = 11,909 细胞，人外周血单个核细胞）
  - SHARE-seq 小鼠皮肤（late anagen 期，GSE140203）
  - NeurIPS 2021 竞赛数据（人骨髓，GSE194122）
  - Greenleaf 2021 人脑皮层（GSE162170）
- **指标**：整合：MAP、细胞类型 ASW、NC、SAS、Batch ASW、GC、总体整合分数、FOSCTTM；预测：基因-wise Pearson/Spearman 相关系数、RMSE；调控推断：AUC（基于 PCHi-C 真值）
- **基线**：Seurat V4、MultiVI、BABEL、GLUE、Cicero、Polarbear、uniPort、Cobolt、MinNet、scJoint、sciCAN
- **评测协议**：80% 细胞训练参考嵌入，20% 查询细胞映射；交叉预测 5 次 bootstrap；调控推断使用 PCHi-C 互作作为真值

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| 多组学整合基准 | Attune 整合性能优于现有方法 | 10x Multiome 与 SHARE-seq，对比 7 种方法 | Attune 总体整合分数最高（10x Multiome: 0.806；SHARE-seq: 0.829） | Attune 在整合任务上具有优势 | 未提供统计显著性检验 | Fig. 2A-B, Supplementary Tables S2-S3 |
| 嵌入质量评估 | Attune 嵌入具有更好的对齐性与均匀性 | 对比其他方法嵌入 | Attune 对齐性最佳（最低对齐分数） | 嵌入质量优于基线 | 未报告均匀性具体数值 | Fig. 2C, Supplementary Table S4 |
| 交叉预测 | Attune 预测表达优于 BABEL 与 Polarbear | 10x Multiome，5 次 bootstrap | Attune 最高 Spearman 0.243，Pearson 0.271，最低 RMSE 0.528 | Attune 在交叉预测任务上表现最佳 | 未报告预测基因子集差异 | Fig. 2F-G, Supplementary Table S8 |
| 预训练消融 | 预训练提升交叉预测性能 | MLP+预训练 vs MLP 无预训练 vs LASSO | 预训练显著提升预测性能 | 预训练对下游任务有益 | 未报告消融幅度 | Supplementary Table S10 |
| 对比对象消融 | 教师-教师对比设计最优 | 3 种对比方案 | 方案 1（教师-教师）最优 | 架构设计对性能有实质影响 | 未报告效应量 | Supplementary Table S7 |
| 调控推断 | Transformer 注意力可反映 PCHi-C 互作 | 10x Multiome，AUC 评估 | Attune+Transformer AUC 优于 Cicero、LASSO、GLUE | 注意力权重可捕捉真实调控关系 | 未报告 AUC 具体数值 | Fig. 3B |
| Gli3 染色质电位 | Gli3 残差反映毛囊谱系特化 | SHARE-seq 毛囊数据集 | Gli3 残差在谱系转变前升高，peak 聚类呈协调变化 | 染色质电位可揭示谱系 priming | 未做功能验证 | Fig. 3G-I, Fig. 4A-E |

## 11 结论正确解读
- **任务范围**：本文方法适用于配对 scRNA-seq + scATAC-seq 数据（同一细胞两种模态），不适用于非配对数据或仅单模态数据。
- **Oracle/真值输入**：调控推断评估使用 PCHi-C 互作作为真值，该数据来自人造血细胞，与 10x Multiome PBMC 存在细胞类型差异；PCHi-C 检测的是启动子-其他区域互作，不等同于 TF 直接结合。
- **端到端状态**：Attune 预训练 + 下游微调是端到端可训练的，但调控推断依赖 Transformer 注意力权重的解释，未经过湿实验验证。
- **算力成本**：模型轻量（嵌入维度 128，batch 32），但未报告训练时间或硬件需求。
- **历史数据依赖**：方法依赖 HVG 选择（2,000 基因），可能丢失低表达但重要的调控基因。
- **模型依赖**：注意力权重作为调控强度的解释依赖 Transformer 架构，不同初始化或训练可能产生不同权重分布。
- **最难情形**：低表达基因、稀疏 peak 区域、异质性高的细胞群。
- **群体/领域边界**：验证限于 PBMC、小鼠皮肤、人脑皮层三个数据集；未在疾病样本或更多物种中验证。
- **不确定性**：未报告置信区间或统计显著性；残差分析基于相关性而非因果性。
- **有边界的复述**：Attune 在配对单细胞多组学数据上实现了优于现有方法的整合与交叉预测性能，其 Transformer 注意力权重可部分反映 PCHi-C 验证的启动子-峰互作，并通过对 Gli3 的残差分析揭示了毛囊分化中的染色质电位模式；但该方法的调控推断能力尚未经湿实验验证，且评估局限于少数数据集。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 数据量有限 | 性能验证仅在少量数据集上 | 在更多数据集上验证模型鲁棒性 | Discussion 末段 |
| 调控推断未湿实验验证 | 注意力权重推断的调控关系未经实验证实 | 结合实验验证调控关系 | Discussion 末段 |
| 模型泛化性 | 未在更多物种/组织类型中测试 | 扩展至更多物种与组织 | Discussion 末段 |
| 计算资源 | 未报告大规模数据上的可扩展性 | 优化模型以支持百万级细胞 | Discussion 末段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 调控推断评估仅用 PCHi-C 真值 | PCHi-C 检测的是染色质构象互作，不等同于 TF 直接结合；且 PCHi-C 数据来自不同细胞类型 | 可能高估注意力权重的调控推断能力 | 使用 ChIP-seq 或 CRISPR 干扰实验验证特定 gene–peak 对 | Methods "Evaluation on inference of regulatory interaction" |
| 残差分析缺乏因果证据 | Gli3 残差与谱系转变的关联可能是伴随而非因果 | 染色质电位概念需要因果验证 | 在 Gli3 敲除/敲低模型中检测残差变化 | Fig. 3G-H, Fig. 4A-E |
| 对比学习依赖配对数据 | 实际应用中配对多组学数据获取成本高、噪声大 | 限制了方法在非配对数据上的适用性 | 测试在非配对数据上的迁移能力 | Methods "Input data and preprocessing" |
| 注意力权重解释性未系统验证 | 注意力权重高不一定意味着调控关系强，可能反映共变异而非因果 | 影响调控网络推断的可靠性 | 与随机权重基线比较 AUC，或使用注意力归因方法 | Fig. 3B |
| 未报告统计显著性 | 整合与预测性能差异未提供置信区间或 p 值 | 无法判断性能优势是否显著 | 补充统计检验 | Fig. 2A-B, F-G |
| 超参数敏感性 | 温度系数、嵌入维度、HVG 数量等超参数选择可能影响结果 | 影响方法可复现性 | 进行超参数敏感性分析 | Methods "Hyperparameter tuning" |

## 14 学到什么
**Agent 提炼的知识候选**：

1. **跨模态对比学习用于调控关系推断**：Attune 的核心思路——先用对比学习对齐两种模态的细胞级表示，再在特征级（基因-峰）用交叉注意力建模关系——可直接迁移到 TF–DNA 结合预测。具体而言，可将 TF 的 ChIP-seq 峰（或 motif 匹配位点）视为"peak 模态"，将 TF 靶基因表达视为"基因模态"，用对比学习预训练对齐，再用注意力推断 TF–靶基因关系。

2. **残差作为"调控延迟"指标**：预测表达与实际表达的残差被定义为"染色质电位"，捕捉染色质已开放但转录未完成的中间状态。这一概念可迁移到 TF–DNA 结合研究：当 TF 结合位点已开放（ATAC 信号高）但靶基因尚未上调时，残差可识别"已 priming 但未激活"的调控事件，有助于发现早期谱系特化中的 TF 功能。

3. **教师-学生网络设计**：不对称的教师-学生网络（教师更复杂、学生更简单）在对比学习中可稳定训练并提升表征质量。在 TF–DNA 结合预测中，可考虑用教师网络编码序列特征（DNA 序列 embedding）、学生网络编码染色质状态特征，通过对比学习对齐，提升跨模态预测性能。

4. **注意力权重作为可解释调控强度**：Transformer 交叉注意力权重直接作为 gene–peak 关系强度，避免了黑箱预测。在 TF–DNA 结合研究中，可用注意力权重替代传统的 motif 匹配分数或 DNase 足迹深度，作为 TF 结合位点功能重要性的排序依据。

5. **1.2 Mb 窗口的调控范围假设**：作者将基因-峰关联限制在 1.2 Mb 内，基于 PCHi-C 距离统计。这一窗口大小可作为 TF–靶基因关联分析的默认参数，但需注意不同细胞类型和 TF 的调控范围可能不同。

6. **对比学习对象的选择影响性能**：消融实验显示，教师-教师对比优于其他组合，说明对比对象的设计（而非简单增加对比对）是性能关键。在 TF–DNA 结合预测中，对比对象的选择（如正样本对定义）可能比模型架构更重要。

## 15 与已有知识连接
- **对比学习在单细胞多组学中的应用**：与 GLUE（图引导对比）、MultiVI（VAE 框架）、BABEL（跨模态预测）等方法形成对比。Attune 的独特之处在于将对比学习与 Transformer 注意力结合，同时实现整合与调控推断。可对比的方法：scVI、totalVI、Cobolt、Polarbear。
- **调控关系推断方法**：与 Cicero（共可及性）、PECA（peak–gene 关联）、SCENT（调控电位）等方法互补。Attune 的注意力权重提供了一种新的 gene–peak 关联度量，可与共可及性、相关性等方法比较。
- **染色质电位概念**：与 SCENIC 的 regulon 活性、CytoTRACE 的分化电位等概念相关。Attune 的残差定义提供了一种基于深度学习预测的电位度量，可与基于 motif 的 regulon 分析互补。
- **Transformer 在基因组学中的应用**：与 Enformer、Borzoi 等序列模型不同，Attune 的 Transformer 作用于单细胞嵌入而非原始序列，更接近跨模态注意力（如 CLIP 的跨模态注意力）的应用。
- **TF–DNA 结合预测**：与 DeepSEA、DeepBind、BPNet 等序列-based 预测方法互补。Attune 提供了一种从染色质状态（而非序列）出发的 TF 调控推断路径，可整合序列特征与染色质状态特征。
- **候选方向** [Analysis]：将 Attune 的框架扩展到 TF 特异性调控推断——将 TF 的 ChIP-seq 峰作为第三种模态，或利用注意力权重识别 TF 结合的 peak 子集，与 motif 分析结合验证。

## 16 研究想法
**Agent 生成的研究候选**：

1. **TF–DNA 结合预测的跨模态对比学习框架**
   - **名称**：TF-BindAlign
   - **来源局限/观察**：现有 TF 结合预测多基于序列（DNA motif）或染色质状态（DNase/ATAC）单一模态，未充分利用同一细胞中两种模态的对应关系。
   - **核心假设**：通过对比学习对齐 TF 的序列特征（motif/embedding）与染色质可及性特征（ATAC 信号），可提升 TF 结合位点的预测精度，尤其在无 ChIP-seq 数据的细胞类型中。
   - **相对本文的增量**：将 Attune 的跨模态对比学习从"基因表达-染色质可及性"迁移到"TF 序列特征-染色质可及性"，并引入 TF 特异性编码器。
   - **初步方法**：构建双塔网络，一塔编码 DNA 序列（k-mer embedding 或预训练 DNA 模型），另一塔编码 ATAC 信号（peak 计数），用对比学习对齐同一 TF 结合位点的两种表示；下游用交叉注意力预测 TF 结合强度。
   - **验证方式**：在 ENCODE 的 ChIP-seq 数据上评估 AUC/AUPRC，与 DeepSEA、BPNet 比较；在无 ChIP-seq 的细胞类型中验证迁移能力。
   - **创新状态**：unverified

2. **基于染色质电位的 TF 调控动态分析**
   - **名称**：TF-Potential
   - **来源局限/观察**：Attune 的残差（染色质电位）在 Gli3 中揭示了谱系 priming，但未系统分析 TF 的电位特征。
   - **核心假设**：不同 TF 的染色质电位模式（残差的时间动态）可区分"先锋因子"（pioneer factor，先开放染色质）与"沉降因子"（settler factor，依赖已开放染色质）。
   - **相对本文的增量**：将残差分析从单个基因扩展到全基因组 TF 靶基因集，并建立 TF 电位谱。
   - **初步方法**：对多个 TF 的靶基因集计算残差，沿分化轨迹分析残差峰值时间；聚类 TF 的电位动态模式；与已知先锋因子列表比较验证。
   - **验证方式**：在小鼠皮肤、胚胎干细胞分化等数据集上验证；与 ATAC-seq 时间序列数据交叉验证。
   - **创新状态**：unverified

3. **注意力权重与 motif 分析结合的调控网络构建**
   - **名称**：AttnRegNet
   - **来源局限/观察**：Attune 的注意力权重提供了 gene–peak 关联，但未与 TF motif 信息结合，无法确定具体 TF。
   - **核心假设**：将注意力权重高的 peak 进行 motif 富集分析，可识别驱动调控变化的 TF，并构建 TF–gene 调控网络。
   - **相对本文的增量**：在 Attune 的 gene–peak 关联基础上，加入 motif 注释层，实现"peak→TF→gene"的三层调控推断。
   - **初步方法**：提取注意力权重 top 10% 的 peak，用 HOMER/STREME 进行 motif 富集；将富集 TF 与 peak 关联的基因连接，构建调控网络；用 SCENIC 比较 regulon 一致性。
   - **验证方式**：在毛囊和皮层数据集中验证网络中的已知调控关系（如 Gli3 靶基因）；用 CRISPR 干扰验证 top 预测。
   - **创新状态**：unverified

4. **多模态对比学习扩展到三模态（ATAC + RNA + TF 结合）**
   - **名称**：TriAttune
   - **来源局限/观察**：Attune 仅处理两种模态，但同一细胞可同时测量更多模态（如蛋白质、甲基化）。
   - **核心假设**：引入第三种模态（如 TF 结合预测分数）可进一步提升调控推断精度。
   - **相对本文的增量**：将对比学习从双模态扩展到多模态，并设计模态间注意力机制。
   - **初步方法**：在 Attune 基础上增加 TF 结合分数模态（来自 ChIP-seq 或预测模型），用多模态对比学习对齐；用 Transformer 交叉注意力建模三模态关系。
   - **验证方式**：在同时具有 ATAC + RNA + ChIP-seq 的数据集上评估调控推断 AUC。
   - **创新状态**：unverified

5. **染色质电位作为分化轨迹的调控时钟**
   - **名称**：ChromoClock
   - **来源局限/观察**：Attune 的残差在毛囊分化中呈现时间动态，但未系统评估其作为分化进程指标的潜力。
   - **核心假设**：全基因组残差的主成分可构成"调控时钟"，比转录组或染色质状态单独更准确地反映分化进程。
   - **相对本文的增量**：将残差从单基因扩展到全基因组，并建立分化轨迹的调控时间轴。
   - **初步方法**：计算全基因组残差矩阵，用 PCA 提取主成分；沿分化轨迹拟合残差动态；比较残差时钟与基于表达或染色质的伪时间。
   - **验证方式**：在多个分化数据集上验证残差时钟与已知分化时间点的一致性。
   - **创新状态**：unverified