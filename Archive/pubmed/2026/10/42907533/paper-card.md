## 01 基本信息

- **标题**：Deep dynamical models of single-cell multiomic velocities predict loss-of-function and rescue perturbations in B cells
- **作者**：Karbalayghareh, Alireza; Pelzer, Benedikt; Chin, Christopher R; Melnick, Ari; Barisic, Darko; Leslie, Christina S
- **单位**：未提供（根据作者信息推测为 Memorial Sloan Kettering Cancer Center 等，但原文未明确列出，故标注未提供）
- **期刊/平台**：Nature Biotechnology
- **年份**：2026（在线日期 2026-10-22）
- **论文类型**：研究论文（含计算方法 + 湿实验验证）
- **领域**：单细胞多组学 × 生成式深度学习 × 基因调控网络 × B 细胞分化
- **关键词**：neural ODE, single-cell multiome, transcription factor motif activity, gene regulatory network, in silico perturbation, germinal center B cells
- **DOI/arXiv 号**：10.1038/s41586-026-03348-1（注意：原文 DOI 前缀为 s41587，但用户提供为 s41586，此处按用户提供记录，实际以出版社为准）
- **代码**：未提供
- **数据**：未提供（文中提及小鼠 GC B 细胞 multiome 数据，但未给出数据可用性链接）
- **阅读日期**：2026-10-22（按用户提供日期）
- **该文在「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法/物理模拟」方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」交叉方向，核心创新在于将 TF motif activity 作为隐变量纳入神经 ODE 动力学建模，实现 TF–DNA 结合活性的动态推断与 in silico 扰动预测。与物理模拟（MD/对接）不同，本文采用数据驱动的生成式建模，但 TF motif 的引入使其直接关联 TF–DNA 结合机制，可作为该课题中「TF 结合活性动态建模」的参考范式。

---

## 02 一句话总结

本文提出 DynaVelo，一个生成式神经 ODE 模型，从单细胞 multiome 数据联合学习基因表达与 TF motif 活性的动力学，通过 in silico 扰动预测 Arid1a 杂合缺失 B 细胞中的 rescue 靶点（Ctcf、Stat3、Bcl6），并经双杂合小鼠实验验证了 rescue 效果。

---

## 03 研究问题

- **具体问题**：如何从单细胞 multiome 数据（同时测量基因表达与染色质可及性）中学习基因调控的动态过程，并预测基因扰动（如 TF 缺失）对细胞状态的影响，进而识别可逆转病理表型的 rescue 靶点？
- **为什么重要**：理解 TF–DNA 结合如何驱动细胞命运决定（如 GC B 细胞分化）是发育生物学和疾病机制的核心；能够预测扰动后果并设计 rescue 策略，对精准医学和合成生物学有直接价值。
- **现有方法为何不足**：传统 scRNA-seq velocity 方法（如 scVelo）假设 RNA 剪接动力学，不包含调控信息；多组学整合方法（如 MOFA+）是静态的，无法建模时间演化；现有 GRN 推断方法（如 SCENIC）多为静态相关，不能预测扰动后的动态响应。
- **精确研究问题**：Can a generative neural ODE model, trained on single-cell multiome data, learn the joint dynamics of gene expression and TF motif activity such that in silico perturbation of TF activity predicts loss-of-function phenotypes and identifies rescue targets that are validated in vivo?

---

## 04 背景与发展脉络

（注：以下脉络基于本文框架及作者引用的代表性方法，标注「经外部核验」的部分为领域公认事实，其余为本文框架。）

1. **单细胞 velocity 方法**（如 scVelo, RNA velocity）：利用剪接动力学推断细胞状态转移方向。局限：仅基于 RNA 剪接，不含调控信息，无法建模 TF 效应。— 经外部核验
2. **多组学整合方法**（如 MOFA+, WNN）：联合 RNA 和 ATAC 降维，但为静态表征，不建模动态。— 经外部核验
3. **GRN 推断方法**（如 SCENIC, GRNBoost2）：从表达和 motif 信息推断 TF–target 边，但为静态相关，不预测扰动响应。— 经外部核验
4. **神经 ODE 在单细胞中的应用**（如 Latent ODE, Neural ODE）：可建模连续时间动态，但多用于插值或生成，未结合 TF motif 活性。— 本文框架
5. **本文主张的位置**：首次将 TF motif activity 作为可学习的隐变量纳入神经 ODE 的向量场，使模型可被 in silico 扰动，从而预测扰动后果和 rescue 靶点。— 本文框架

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 静态 GRN 无法反映动态调控 | 现有 GRN 推断仅给出静态边，无法解释细胞状态转移中 TF 活性的变化 | 作者认为 GRN 是动态且细胞状态特异的，静态方法忽略了时间维度 | 摘要中「yields dynamic and cell-state-specific GRNs」 |
| 现有 velocity 方法缺乏调控信息 | RNA velocity 仅基于剪接动力学，无法解释为何细胞走向特定命运 | 作者指出需要联合表达与染色质可及性才能捕捉 TF 效应 | 摘要中「learns the joint dynamics of gene expression and TF motif activity」 |
| 无法预测扰动后果 | 现有模型不能回答「如果敲除某 TF，细胞会怎样」 | 作者认为需要可被扰动的生成式模型，而非仅用于轨迹推断 | 摘要中「the model can be perturbed in silico」 |
| 缺乏 wet-lab 验证的计算预测 | 多数计算预测停留在 in silico，未经过实验检验 | 作者强调需要体内验证来确认预测的可靠性 | 摘要中「In vivo experiments in double-heterozygous mice confirmed rescue」 |

---

## 06 核心思想

1. **表面方法**：DynaVelo 是一个生成式神经 ODE，输入单细胞 multiome 数据（基因表达 + 染色质可及性），输出每个细胞的基因表达和 TF motif 活性的联合轨迹。模型学习一个向量场函数 f(x, t)，其中 x 包含基因表达和 TF motif 活性，通过 ODE 积分生成轨迹。关键设计是 TF motif activity 作为可学习的隐变量，且向量场显式依赖 TF 活性，因此可以通过修改 TF 活性进行 in silico 扰动。

2. **核心洞察**：TF motif activity 是连接基因表达和染色质可及性的「调控桥梁」。通过将 TF 活性作为隐变量纳入动力学方程，模型不仅拟合了表达动态，还隐式学习了 TF–DNA 结合的调控逻辑。这使得模型能够回答「如果 TF 活性改变，表达动态如何变化」的因果性问题，而不仅仅是描述性轨迹。

3. **可能的普适教训** [Analysis]：将「调控因子活性」作为显式隐变量纳入生成式动力学模型，是连接观测数据（表达/可及性）与因果扰动预测的关键设计。这一思路可迁移到任何「调控因子–靶标」系统（如 TF–DNA、miRNA–mRNA、激酶–底物），只要调控因子活性可从数据中推断或近似。

---

## 07 方法总览

- **输入**：单细胞 multiome 数据，每个细胞同时测量基因表达（RNA）和染色质可及性（ATAC）。
- **输出**：每个细胞的基因表达和 TF motif 活性的联合动态轨迹；in silico 扰动后的预测轨迹；动态 GRN。
- **模块**：
  1. 数据预处理：RNA 和 ATAC 的联合降维/整合（具体方法未在摘要中详述）。
  2. TF motif activity 推断：从 ATAC 可及性推断每个细胞的 TF motif 活性（可能基于 motif 扫描和可及性加权）。
  3. 神经 ODE 编码器：将细胞状态（表达 + TF 活性）映射到隐空间，学习向量场 f(x, t)。
  4. 解码器：从隐空间映射回基因表达空间，用于重构和轨迹生成。
  5. 扰动模块：通过修改 TF 活性向量进行 in silico 扰动，重新积分 ODE 得到预测轨迹。
- **训练**：生成式训练，目标为重构基因表达和 TF 活性，同时可能包含 velocity 一致性损失（具体损失函数未在摘要中详述）。
- **反馈回路**：模型预测的轨迹可用于推断动态 GRN，GRN 又可用于解释扰动效应，形成闭环。
- **文字流程**：输入 multiome 数据 → 推断 TF motif 活性 → 编码到隐空间 → 学习 ODE 向量场 → 解码生成轨迹 → 通过修改 TF 活性进行 in silico 扰动 → 预测扰动后轨迹 → 从轨迹推断动态 GRN → 选择 rescue 靶点 → 湿实验验证。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| TF motif activity 推断 | 从 ATAC 可及性推断每个细胞的 TF 结合活性 | 提供调控信息，连接表达与可及性 | 输入：ATAC 峰 × motif 矩阵；输出：细胞 × TF 活性矩阵 | 摘要中「learns the joint dynamics of gene expression and TF motif activity」 | 预期影响 [Analysis]：移除后模型退化为纯表达动力学，失去调控解释力，无法进行有意义的 TF 扰动 |
| 神经 ODE 向量场 | 学习表达和 TF 活性的联合时间演化 | 核心动力学模型，支持连续时间积分和扰动 | 输入：当前状态 x(t)；输出：导数 dx/dt | 摘要中「generative neural ordinary differential equation model」 | 预期影响 [Analysis]：移除后无法生成轨迹，模型退化为静态表征 |
| 扰动模块 | 修改 TF 活性并重新积分 ODE | 实现 in silico 扰动预测 | 输入：原始状态 + 扰动 TF 列表；输出：扰动后轨迹 | 摘要中「the model can be perturbed in silico」 | 预期影响 [Analysis]：移除后模型仅能描述，不能预测扰动后果 |
| 动态 GRN 推断 | 从轨迹中提取 TF–target 边 | 提供可解释的调控网络 | 输入：轨迹；输出：动态 GRN | 摘要中「yields dynamic and cell-state-specific GRNs」 | 预期影响 [Analysis]：移除后失去可解释性，无法定位具体调控边 |

注：以上「预期影响」均为 [Analysis] 推断，原文未提供消融实验数据。

---

## 09 关键公式符号

（注：摘要中未给出具体公式，以下基于神经 ODE 标准形式推断，标注为 [Analysis] 推断。）

1. **神经 ODE 状态演化**：
   \[
   \frac{d\mathbf{x}(t)}{dt} = f_\theta(\mathbf{x}(t), t)
   \]
   - \(\mathbf{x}(t)\)：t 时刻的细胞状态向量，包含基因表达和 TF motif 活性
   - \(f_\theta\)：参数为 θ 的神经网络，学习向量场
   - 用途：定义连续时间动力学，通过 ODE 积分生成轨迹
   - 来源：标准神经 ODE 形式（Chen et al., 2018），本文采用此框架 [Analysis]

2. **TF motif 活性推断**（推测形式）：
   \[
   A_{c,tf} = \sum_{p \in peaks} w_{p,tf} \cdot acc_{c,p}
   \]
   - \(A_{c,tf}\)：细胞 c 中 TF tf 的 motif 活性
   - \(w_{p,tf}\)：峰 p 中 TF tf 的 motif 权重（如 motif 匹配分数）
   - \(acc_{c,p}\)：细胞 c 中峰 p 的可及性
   - 用途：从 ATAC 数据推断 TF 活性
   - 来源：基于常见 motif 活性推断方法（如 chromVAR）的推测 [Analysis]

3. **扰动操作**（推测形式）：
   \[
   \mathbf{x}_{\text{pert}}(0) = \mathbf{x}(0) + \delta_{tf}
   \]
   - \(\delta_{tf}\)：对 TF 活性维度的扰动向量（如将某 TF 活性设为零）
   - 用途：模拟 TF 敲除或过表达
   - 来源：基于摘要中「perturbed in silico」的推断 [Analysis]

---

## 10 实验设计与证据链

- **数据集**：小鼠野生型（WT）和 Arid1a 杂合缺失（Arid1aHet）的 germinal center (GC) B 细胞单细胞 multiome 数据（RNA + ATAC）。
- **规模**：未提供具体细胞数。
- **指标**：未在摘要中明确列出（推测包括轨迹重构误差、GRN 边恢复率、扰动预测与实验一致性等）。
- **基线**：未在摘要中明确列出（推测包括 scVelo、SCENIC 等）。
- **预算/资源**：未提供。
- **骨干/仪器**：10x Genomics Multiome 或类似平台（推测，未明确）。
- **oracle 输入**：未提供（推测包括已知的 TF 结合 motif 数据库）。
- **评测协议**：未在摘要中详述。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| WT GC B 细胞轨迹恢复 | DynaVelo 能恢复 WT 的分叉动态 | 与 WT 数据拟合，观察轨迹结构 | 恢复出分叉动态 | 模型能捕捉正常分化过程 | 未与定量指标对比，无法判断精度 | 摘要「recovers the bifurcating in vivo dynamics of wild-type」 |
| Arid1aHet 动态变化 | DynaVelo 能揭示杂合缺失下的动态改变 | WT vs Arid1aHet 轨迹对比 | 显示动态改变 | 模型能捕捉基因型效应 | 未说明改变的幅度和方向 | 摘要「reveals how these dynamics change under heterozygous loss」 |
| GRN 边恢复 | 动态 GRN 能恢复已知 TF–gene 边 | 与已知 WT GC GRN 对比 | 恢复已知边 | 模型能学习真实调控关系 | 未给出精确率/召回率 | 摘要「recover known TF-to-gene edges」 |
| 扰动预测 | 预测 Arid1aHet 中 rescue 靶点 | 对 Arid1aHet 进行 in silico 扰动，筛选 rescue 靶点 | 预测 Ctcf、Stat3、Bcl6 | 模型能识别潜在 rescue 靶点 | 未说明筛选标准 | 摘要「identified Ctcf, Stat3 and Bcl6 as rescue targets」 |
| 湿实验验证 | 双杂合小鼠能 rescue Arid1aHet 表型 | Arid1aHet;CtcfHet、Arid1aHet;Stat3Het、Arid1aHet;Bcl6Het vs Arid1aHet | 三种均 rescue 暗区表型 | 预测靶点具有体内有效性 | 未说明 rescue 的定量程度 | 摘要「confirmed rescue of the Arid1aHet dark-zone phenotype in all three cases」 |
| multiome 验证 | Arid1aHet;CtcfHet 向 WT 动态偏移 | Arid1aHet;CtcfHet multiome 数据 vs 预测 | 验证了向 WT 的偏移 | 模型预测具有可验证性 | 未说明偏移的统计显著性 | 摘要「validated the predicted shift toward wild-type dynamics」 |

---

## 11 结论正确解读

- **任务范围**：本文聚焦于 GC B 细胞分化过程中的基因表达与 TF 活性联合动力学建模，以及单基因杂合缺失（Arid1a）下的扰动预测。
- **oracle/真值输入**：模型依赖 ATAC 数据推断 TF motif 活性，因此 TF 活性的准确性受限于 motif 数据库质量和 ATAC 分辨率。
- **端到端状态**：模型是端到端可训练的（从 multiome 到轨迹），但 TF motif 活性推断可能依赖外部 motif 数据库，并非完全端到端。
- **算力成本**：未提供，但神经 ODE 训练通常计算成本较高 [Analysis]。
- **历史数据依赖**：模型需要 multiome 数据（RNA + ATAC），且需要足够的细胞覆盖轨迹各阶段。
- **模型依赖**：结果依赖于神经 ODE 的架构选择、训练策略和 TF motif 活性推断方法。
- **最难情形**：预测多个 TF 同时扰动的组合效应、非编码突变对 TF 结合的影响、以及超出训练分布的新细胞状态。
- **群体/领域边界**：结论在 B 细胞系统中验证，推广到其他细胞类型或组织需重新训练和验证。
- **不确定性**：摘要未提供置信区间或不确定性量化；湿实验验证了三个靶点，但未说明 rescue 的完整性和长期稳定性。

**有边界的复述**：DynaVelo 在 WT 和 Arid1aHet 小鼠 GC B 细胞 multiome 数据上，能够学习基因表达与 TF motif 活性的联合动力学，通过 in silico 扰动预测 Ctcf、Stat3、Bcl6 为 Arid1a 缺失的 rescue 靶点，并在双杂合小鼠中验证了这三种靶点对暗区表型的 rescue 效果，以及 Arid1aHet;CtcfHet 的 multiome 动态向 WT 偏移。

---

## 12 作者自认局限

在提供的摘要中，作者未明确列出局限性。以下为作者提及的相关约束（非正式局限）：

- 摘要中未出现「limitation」「caveat」「future work」等字样。
- 作者仅报告了成功验证的案例，未提及失败案例或模型失效场景。

**作者提及的相关约束**（非正式局限）：
- 模型需要 multiome 数据（RNA + ATAC），对数据质量要求较高（推断自摘要中「single-cell multiome data」的表述）。
- 湿实验验证仅覆盖三个靶点，未覆盖所有预测结果（推断自摘要中「in all three cases」的表述）。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| TF motif 活性推断依赖 ATAC 数据 | ATAC 可及性不等于 TF 实际结合，可能引入假阳性/假阴性 | TF 活性是模型的核心隐变量，其准确性直接影响扰动预测 | 与 ChIP-seq 或 CUT&Tag 数据对比验证 TF 活性推断 | 摘要中「TF motif activity」的表述 |
| 湿实验验证仅三个靶点 | 可能只报告了成功的案例，存在选择性报告偏差 | 无法评估模型的整体预测准确率 | 要求作者提供所有预测靶点及验证结果 | 摘要中「in all three cases」的表述 |
| 未提供与基线方法的定量对比 | 无法判断 DynaVelo 相对现有方法（如 scVelo + SCENIC）的优势 | 需要定量指标（如 GRN 边恢复的 AUROC、轨迹一致性） | 要求补充与基线的定量对比实验 | 摘要中未提及基线对比 |
| 神经 ODE 的可扩展性 | 大规模数据（数十万细胞）下训练可能不稳定或耗时 | 影响方法在更大数据集上的实用性 | 测试不同数据规模下的训练时间和稳定性 | 神经 ODE 的已知计算成本 [Analysis] |
| 扰动预测的因果性 | 模型学习的是相关性，in silico 扰动可能不等于真实遗传扰动 | 因果推断需要额外的干预实验或因果模型 | 与 CRISPR 干扰实验对比，检验预测的因果性 | 摘要中「perturbed in silico」的表述 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **TF motif activity 作为隐变量的建模范式**：将 TF 结合活性（从 ATAC 推断）作为显式隐变量纳入神经 ODE，使模型可被扰动。可迁移到 TF–DNA 结合机制研究：在 MD 模拟或对接中，TF 活性可作为偏置项或约束条件，引导模拟朝向特定结合构象。
2. **动态 GRN 推断**：从轨迹中提取随时间变化的 TF–target 边，而非静态网络。可迁移到 TF–DNA 结合机制：结合分子动力学轨迹，推断 TF 结合位点的动态占据率，构建时间分辨的调控网络。
3. **In silico 扰动作为假设生成工具**：通过修改 TF 活性预测表型变化，生成可实验验证的假设。可迁移到 TF–DNA 结合机制：预测 TF 点突变对结合亲和力的影响，指导湿实验验证。
4. **生成式模型 + 湿实验闭环**：计算预测与体内验证的闭环设计，是计算生物学研究的可复制范式。可迁移到任何 TF–DNA 结合机制研究，强调预测必须经过实验检验。
5. **多组学联合建模**：RNA + ATAC 的联合建模比单模态更丰富。可迁移到 TF–DNA 结合机制：结合 ChIP-seq、ATAC-seq、RNA-seq 多模态数据，构建更完整的调控图景。

---

## 15 与已有知识连接

- **相似方法**：与 RNA velocity（La Manno et al., 2018; Bergen et al., 2020）同属单细胞动力学建模，但 DynaVelo 增加了 TF motif 活性维度。与 Latent ODE（Rubanova et al., 2019）同属神经 ODE 在生物数据中的应用。
- **组合方向**：与 AlphaFold 等结构预测方法组合，可预测 TF 突变对 DNA 结合的结构影响，再输入 DynaVelo 预测细胞动态变化。
- **冲突观点**：与静态 GRN 推断方法（如 SCENIC）相比，DynaVelo 主张 GRN 是动态的，可能引发关于「静态 GRN 是否足够」的讨论。
- **可迁移领域**：TF–DNA 结合机制研究中，DynaVelo 的「TF 活性作为隐变量」思想可迁移到分子模拟中，将 TF 活性作为集体变量（collective variable）引导增强采样。
- **候选方向**：将 DynaVelo 的框架扩展到蛋白质–DNA 结合自由能预测，将 TF 活性与结合自由能关联，建立从序列/结构到细胞动态的多尺度模型。

---

## 16 研究想法

**Agent 生成的研究候选**

1. **候选名称**：TF–DNA 结合自由能的动态推断框架（DynaBind）
   - **来源局限/观察**：DynaVelo 的 TF 活性是数据驱动的隐变量，未直接关联物理结合自由能；MD 模拟可计算结合自由能但无法覆盖细胞群体动态。
   - **核心假设**：TF motif 活性与 TF–DNA 结合自由能之间存在可学习映射，通过该映射可将细胞动态与分子物理连接。
   - **相对本文的增量**：将 DynaVelo 的宏观动态与 MD 的微观物理结合，建立多尺度模型。
   - **初步方法**：在 DynaVelo 框架中增加结合自由能预测头，用 MD 模拟的 TF–DNA 复合物数据训练，实现从序列到细胞动态的端到端预测。
   - **验证方式**：对已知 TF 突变体，比较预测的细胞动态变化与实验表型。
   - **创新状态**：unverified

2. **候选名称**：TF 点突变扰动预测的 in silico 筛选平台
   - **来源局限/观察**：DynaVelo 仅验证了杂合缺失（loss-of-function），未覆盖点突变（missense）对 TF 结合的影响。
   - **核心假设**：TF 点突变对 motif 活性的影响可通过序列特征预测，进而通过 DynaVelo 预测细胞表型。
   - **相对本文的增量**：扩展扰动类型从缺失到点突变，增加临床相关性。
   - **初步方法**：用突变效应预测器（如 AlphaMissense）预处理 TF 突变，将预测的活性变化输入 DynaVelo 进行扰动模拟。
   - **验证方式**：对已知致病 TF 突变，比较预测的细胞状态偏移与患者数据。
   - **创新状态**：unverified

3. **候选名称**：动态 GRN 与 TF 结合位点共变分析
   - **来源局限/观察**：DynaVelo 输出动态 GRN，但未与基因组上的 TF 结合位点（如 ChIP-seq peaks）直接关联。
   - **核心假设**：动态 GRN 中的边变化与 TF 结合位点的染色质状态变化（ATAC 峰动态）一致。
   - **相对本文的增量**：将 GRN 动态与基因组位点动态对齐，提供更精细的调控机制解释。
   - **初步方法**：在 DynaVelo 轨迹上提取 ATAC 峰动态，与 GRN 边变化做关联分析，识别「先导」结合位点。
   - **验证方式**：用 CRISPR 干扰特定结合位点，检验 GRN 边是否如预测消失。
   - **创新状态**：unverified

4. **候选名称**：TF–DNA 结合机制的增强采样引导神经 ODE
   - **来源局限/观察**：DynaVelo 的向量场是纯数据驱动的，未利用物理先验；MD 模拟的增强采样可探索稀有结合构象。
   - **核心假设**：将 MD 增强采样得到的结合自由能面作为正则项，可提高神经 ODE 在稀有状态下的预测准确性。
   - **相对本文的增量**：引入物理先验，提高数据稀疏区域的泛化能力。
   - **初步方法**：用 metadynamics 或 umbrella sampling 计算 TF–DNA 自由能面，将其梯度作为正则项加入神经 ODE 损失。
   - **验证方式**：在数据稀疏的细胞类型上测试预测准确性。
   - **创新状态**：unverified

5. **候选名称**：跨物种 TF 结合动态的迁移学习
   - **来源局限/观察**：DynaVelo 在小鼠 B 细胞上训练，未测试跨物种泛化。
   - **核心假设**：TF 结合机制在哺乳动物中保守，模型可迁移到人类 B 细胞。
   - **相对本文的增量**：扩展模型适用性，增加临床转化价值。
   - **初步方法**：用小鼠数据预训练，用少量人类数据微调，测试人类 GC B 细胞动态预测。
   - **验证方式**：与人类 GC B 细胞 multiome 数据对比。
   - **创新状态**：unverified