## 01 基本信息

- **标题**：Refining sequence-to-activity models by increasing model resolution
- **作者**：Chandra, Nuria Alina; Hu, Yan; Buenrostro, Jason D; Mostafavi, Sara; Sasse, Alexander
- **单位**：未提供（根据作者信息推测涉及哈佛大学/华盛顿大学等，但原文未明确列出）
- **期刊/平台**：Bioinformatics advances
- **年份**：2026-08-02（在线发表日期）
- **论文类型**：方法学/应用研究
- **领域**：计算基因组学、深度学习、染色质可及性建模
- **关键词**：sequence-to-activity model, ATAC-seq, base-pair resolution, multi-task learning, transcription factor motifs, cis-regulatory syntax
- **DOI/arXiv 号**：10.1093/bioadv/vbag122
- **代码**：https://github.com/nuriachandra/bpAITAC
- **数据**：GSE100738（Yoshida et al. 2019，ImmGen ATAC-seq 数据，90 种小鼠免疫细胞类型）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作 × 深度学习」方向，聚焦于通过提高序列-活性模型的输入分辨率（从区域级到碱基对级）来改进染色质可及性预测，从而更精细地解码 TF 结合位点（TF footprints）和顺式调控语法。与 TF–DNA 结合机制直接相关，因为碱基对分辨率的 ATAC-seq 信号直接反映 TF 占据（footprints），模型通过学习这些信号来推断 TF 结合强度与位置。

## 02 一句话总结

本文提出 bpAI-TAC，一个多任务卷积神经网络，通过同时预测 90 种免疫细胞类型的 ATAC-seq 总可及性和碱基对分辨率的 Tn5 插入分布，利用 profile 信息提升差异染色质可及性预测精度，并发现 AI-TAC 遗漏的 TF 基序及其细胞类型特异性效应大小。

## 03 研究问题

- **具体问题**：在序列-活性（S2A）模型中，将训练目标从区域级 ATAC-seq 可及性提升到碱基对分辨率的 Tn5 插入 profile，是否能改善模型对细胞类型特异性染色质可及性差异的预测能力，并揭示更精细的 TF 结合语法？
- **为什么重要**：细胞类型特异性基因表达由 TF 结合调控，而 TF 结合位点通常位于开放染色质区域内的特定位置。区域级可及性聚合信号丢失了 TF footprints 的位置和强度信息，限制了模型对 cis-regulatory syntax 的学习。提高分辨率有望捕获这些精细信号。
- **现有方法不足**：AI-TAC 等模型仅预测区域级可及性，无法区分 Tn5 插入的局部分布；ChromBPnet 虽使用 bp 分辨率，但为单任务模型，无法直接比较跨细胞类型的差异活性，且需要显式 Tn5 偏置建模。
- **精确研究问题**：Can a multi-task sequence-to-activity model trained on base-pair resolution ATAC-seq profiles improve predictions of differential chromatin accessibility across immune cell types and uncover TF motifs missed by region-level models?

## 04 背景与发展脉络

（注：以下脉络基于本文引用和讨论，部分经外部核验，标注如下）

1. **区域级 S2A 模型**（如 AI-TAC，Maslova et al. 2020）：预测 OCR 总可及性，成功识别细胞类型特异性基序，但无法解析 TF 结合位置和强度。
2. **碱基对分辨率模型**（如 BPnet，Avsec et al. 2021；ChromBPnet，Pampari et al. 2024）：预测 Tn5 插入 profile，可生成 TF footprints，但为单任务模型，训练成本高，且需显式 Tn5 偏置校正。
3. **TF footprint 生物学**（Bentsen et al. 2020；Schultheis et al. 2024；Hu et al. 2025）：Tn5 插入的局部分布反映 TF 占据，footprint 深度与 TF 结合强度相关。
4. **本文位置**：将多任务学习与 bp 分辨率结合，在 90 种免疫细胞类型上同时预测可及性和 profile，无需显式偏置分解即可获得性能提升，并系统比较了损失函数、架构和分辨率的影响。

（此脉络基于本文引言和讨论，部分引用外部文献，标注为「经外部核验」）

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 区域级可及性丢失 TF 位置信息 | AI-TAC 无法区分 Tn5 插入的局部分布，难以精确定位 TF 结合位点 | 信号在数百 bp 窗口内聚合，footprint 细节被平均化 | 引言：信号通常聚合数百 bp，难以 pinpoint 驱动可及性变化的碱基 |
| 单任务模型无法比较跨细胞类型差异 | ChromBPnet 每细胞类型训练一个模型，预测不一致，难以直接比较 | 缺乏共享表示，训练成本高 | 引言：bpAI-TAC 使用单一多任务模型以支持跨细胞类型直接比较 |
| 显式 Tn5 偏置建模复杂 | ChromBPnet 需要单独训练偏置模型并校正 | Tn5 酶有序列偏好，扭曲 footprint 信号 | 讨论：bpAI-TAC 无需显式偏置分解即可获得性能提升 |
| 碱基对分辨率数据量大 | 多任务 bp 分辨率训练内存需求高 | 每个碱基一个输出，数据量随序列长度线性增长 | 结果 2.2：内存需求是主要瓶颈之一 |
| 粗分辨率丢失 footprint 细节 | 5/10/20 bp 分箱模型性能下降 | 分箱可能截断 footprint 或合并不同 TF 信号 | 结果 2.2 图 2c：粗分辨率模型一致低于 bp 模型 |

## 06 核心思想

1. **表面方法**：构建多任务 CNN，输入 1 kb DNA 序列，双输出头分别预测 250 bp 窗口内每个碱基的 Tn5 插入概率（profile head）和总插入数（accessibility head），在 90 种免疫细胞类型上联合训练。

2. **核心洞察**：碱基对分辨率的 profile 信号包含 TF footprints 信息，这些信息不仅改善 footprint 解释，还通过多任务学习反向增强可及性预测——模型被迫学习 TF 结合位置和强度，从而更准确地推断哪些基序在哪些细胞类型中驱动开放。多任务共享表示使模型能够从 profile 任务中提取的精细语法迁移到可及性预测任务。

3. **可能的普适教训** [Analysis]：在序列-功能建模中，提高输出分辨率（即使最终任务只需要聚合值）可以作为一种隐式的数据增强或表示学习正则化，迫使模型学习更细粒度的特征。类似思路可能适用于其他基因组学任务（如 ChIP-seq peak 调用 + footprint 分析、RNA-seq 表达 + 剪接位点预测）。

## 07 方法总览

- **输入**：1 kb（998 bp）DNA 序列，one-hot 编码，以 ATAC-seq peak 为中心
- **输出**：
  - Profile head：250 bp 窗口内每个碱基的 Tn5 插入概率分布（softmax 后）
  - Accessibility head：250 bp 窗口内总 Tn5 插入数（标量）
- **模型架构**：CNN 主体，起始卷积核宽 25，后接 9 层扩张卷积（核宽 3，扩张率从 2 开始逐层加倍），带残差连接，每层 300 个滤波器，ReLU 激活。分支为两个头：profile head 为单卷积（宽 25，90 个滤波器），accessibility head 为 3 次最大池化（宽 5）+ 卷积（宽 3，300 滤波器）+ 全连接层。
- **训练**：Adam 优化器，学习率 1e-3，1000 步线性 warmup，batch size 20，训练至收敛。
- **损失函数**：比较了多种损失，包括：
  - 正则损失：直接比较预测与观测的每碱基 Tn5 计数（PNLL 或 MSE）
  - 复合损失：λ 加权 profile 损失（MNLL 或 CE）与 accessibility 损失（MSE of log counts）
- **Tn5 偏置处理**：训练了三种偏置模型（蛋白-free DNA、closed OCR 聚合、浅层架构），在推理时可将偏置设为 0 以提取纯 TF footprint 信号。
- **流程**：输入序列 → CNN 编码 → 双头输出 → 训练时联合优化 → 推理时结合偏置模型生成 footprint 或直接输出可及性预测。

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 扩张卷积残差主体 | 学习长程序列特征和基序组合语法 | 捕获 1 kb 窗口内的调控语法，包括基序间距和方向 | 输入：1 kb one-hot 序列；输出：隐表示 | 结果 2.1：bpAI-TAC 优于 AI-TAC | [预期] 移除后模型无法学习长程相互作用，性能下降 |
| Profile head | 预测每碱基 Tn5 插入概率 | 提供 TF footprint 级别的监督信号 | 输入：隐表示；输出：250 bp 概率分布 | 结果 2.3：bpAI-TAC 识别出 AI-TAC 遗漏的基序 | [实测] 仅训练 accessibility head（λ=0）时性能下降（图 2b） |
| Accessibility head | 预测总 Tn5 插入数 | 提供区域级可及性预测 | 输入：隐表示；输出：标量 | 结果 2.1：可及性预测准确 | [预期] 移除后模型无法输出可及性，但 profile 任务可能仍提供部分信息 |
| Tn5 偏置模型 | 建模 Tn5 酶的序列偏好 | 分离技术偏置与生物学信号，提取干净 footprint | 输入：DNA 序列；输出：偏置 profile | 结果 2.3 图 S7：偏置校正后 footprint 更清晰 | [预期] 移除后 footprint 被 Tn5 偏置污染，基序效应估计偏差 |
| 多任务联合训练 | 同时优化 profile 和 accessibility | 共享表示，提升跨细胞类型泛化 | 输入：多任务损失；输出：共享权重 | 结果 2.2 图 2f：多任务优于单任务集成 | [实测] 单任务模型性能显著下降（图 2f） |

## 09 关键公式符号

1. **复合损失函数**（Methods 4.4.3）：
   L = λ · L_profile + (1-λ) · L_accessibility
   - L_profile：profile 损失（MNLL 或 CE）
   - L_accessibility：accessibility 损失（MSE of log counts）
   - λ ∈ [0,1]：profile 损失权重

2. **Poisson 负对数似然（PNLL）**（Methods 4.4.3）：
   L_PNLL = Σ_i [y_i · log(λ_i) - λ_i - log(y_i!)]
   其中 y_i 为观测 Tn5 计数，λ_i 为预测均值

3. **预测 Tn5 计数重构**（Methods 4.2）：
   predicted_count_i = profile_probability_i × predicted_total_count
   - 将 profile 概率与 accessibility 标量相乘得到每碱基预测计数

4. **偏置校正**（Methods 4.3）：
   logit_corrected = logit_predicted - logit_bias
   - 推理时从预测 logit 中减去偏置模型 logit，得到纯 TF footprint 信号

## 10 实验设计与证据链

**数据集与评测协议**：
- 数据：ImmGen ATAC-seq，90 种小鼠免疫细胞类型，5,18,845 个 OCR（Yoshida et al. 2019）
- 划分：染色体 12、15 用于验证，11、16 用于测试
- 指标：Pearson 相关系数 R（预测 vs 观测可及性）
- 基线：AI-TAC（区域级多任务模型，无 profile 任务）
- 对比条件：不同损失函数（PNLL, MSE, MNLL+CE, MNLL+MSE）、不同架构（浅层、深层）、不同分辨率（1/5/10/20 bp）、不同偏置模型

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 主实验：bpAI-TAC vs AI-TAC | profile 信息提升可及性预测 | 相同架构，有无 profile 任务 | bpAI-TAC 平均 R=0.70，AI-TAC 平均 R=0.51（细胞类型特异性 OCR 上） | profile 任务提供额外监督信号 | 未证明 profile 任务对所有 OCR 类型均有益 | 结果 2.1 图 1b-d |
| 差异可及性预测 | bpAI-TAC 更好预测细胞类型间差异 | 4,005 对细胞类型组合 | 平均 R 从 0.46 提升至 0.58 | profile 信息增强差异可及性建模 | 未报告显著性检验 | 结果 2.1 图 S2 |
| 损失函数比较 | PNLL 优于复合损失 | PNLL vs MNLL+CE vs MNLL+MSE | PNLL 最佳 | PNLL 更符合 Tn5 计数分布 | 未测试所有可能损失组合 | 结果 2.2 图 2a |
| 分辨率消融 | 1 bp 优于 5/10/20 bp | 不同分箱大小 | 1 bp 最佳，粗分箱性能下降 | 碱基对分辨率是关键 | 未测试 2 bp 等中间值 | 结果 2.2 图 2c |
| 偏置模型比较 | 偏置校正不影响可及性预测 | 三种偏置模型 vs 无偏置 | 可及性预测相似 | 偏置主要影响 footprint 解释而非可及性 | 未评估偏置对基序发现的影响 | 结果 2.2 图 2e |
| 基序发现 | bpAI-TAC 发现 AI-TAC 遗漏的基序 | 比较两模型 attribution | 23 个基序簇在 bpAI-TAC 中显著富集，包括 RUNX、SPIB、REL、POU2F、ERF 等 | profile 信息揭示更全面的 TF 语法 | 未验证这些基序的功能重要性 | 结果 2.3 图 3c |
| 基序效应大小 | bpAI-TAC 更准确估计细胞类型特异性效应 | 基序插入实验 | bpAI-TAC 预测的效应大小与细胞类型更一致 | 模型学到更精细的上下文依赖 | 未与 ChIP-seq 直接验证 | 结果 2.3 图 3d |

## 11 结论正确解读

- **任务范围**：本文仅针对 ATAC-seq 可及性预测和 TF motif 发现，不涉及 TF 结合亲和力的直接测量或 3D 结构预测。
- **Oracle/真值输入**：训练和测试均使用真实 ATAC-seq 数据（GSE100738），无模拟数据或 oracle 输入。
- **端到端状态**：模型端到端训练，从 DNA 序列直接预测可及性和 profile，无需中间特征工程。
- **算力成本**：未报告具体训练时间或 GPU 需求，仅提及内存是主要瓶颈。
- **历史数据依赖**：模型仅依赖 DNA 序列，不依赖进化保守性等外部特征。
- **模型依赖**：结果依赖于 CNN 架构选择、损失函数和数据划分；不同架构可能产生不同结果。
- **最难情形**：细胞类型特异性 OCR（仅在少数细胞类型中开放）预测难度最高，但 bpAI-TAC 在此类区域提升最大。
- **群体/领域边界**：仅限小鼠免疫细胞；人类或其他物种的泛化性未验证。
- **不确定性**：未报告预测置信区间或不确定性估计。
- **有边界的复述**：在 90 种小鼠免疫细胞类型的 ATAC-seq 数据上，将多任务 CNN 的输出分辨率从区域级提升到碱基对级，可将差异可及性预测的 Pearson R 从 0.46 提升至 0.58，并识别出 23 个 AI-TAC 遗漏的 TF 基序簇；该结论仅适用于该数据集的测试染色体划分，且依赖特定架构和损失函数选择。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| footprint 深度不如 ChromBPnet 明显 | 多任务架构下 footprint 信号较弱 | 改进偏置校正或架构设计 | 讨论：deep footprints 不如 ChromBPnet 明显 |
| 测序深度有限 | 平均 1500 万 reads/细胞类型，可能限制 footprint 检测 | 使用更深测序数据 | 讨论：测序深度可能影响 footprint 质量 |
| 未验证功能重要性 | 新发现的基序未通过实验验证 | 后续实验验证 | 讨论：需要实验验证新基序的功能 |
| 泛化性未测试 | 仅限小鼠免疫细胞 | 扩展到其他物种和组织 | 讨论：未提及，但隐含 |

**作者提及的相关约束**（非正式局限）：
- 内存需求限制了批量大小和序列长度
- 偏置模型的选择对 footprint 解释有影响，但对可及性预测影响不大
- 多任务学习在 lineage 水平上优于单任务集成，但未测试所有可能的集成策略

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 性能提升可能部分来自模型容量增加而非分辨率本身 | bpAI-TAC 有额外输出头，参数量大于 AI-TAC | 若提升仅来自容量，则「分辨率」论点被削弱 | 控制参数量，比较同容量有无 profile 任务 | 结果 2.1：未报告参数量控制实验 |
| 基序效应大小比较缺乏 ground truth | 基序插入实验的「真实」效应大小未知 | 无法确认 bpAI-TAC 的估计更准确 | 使用 ChIP-seq 或 MPRA 数据验证 | 结果 2.3：仅比较两模型相对差异 |
| 偏置模型选择对可及性预测无影响，但可能影响基序发现 | 三种偏置模型产生相似可及性预测，但基序发现可能不同 | 基序发现的稳健性未测试 | 用不同偏置模型重复基序分析 | 结果 2.2 图 2e：仅报告可及性预测 |
| 90 种细胞类型共享权重可能稀释细胞类型特异性信号 | 多任务学习可能偏向共享特征，牺牲极端特异性 | 某些细胞类型的特异性基序可能被忽略 | 比较每细胞类型单独模型 vs 多任务模型 | 结果 2.2 图 2f：仅报告 lineage 水平 |
| 1 kb 窗口可能不足以捕获长程调控 | 增强子-启动子互作可跨越数十 kb | 模型可能遗漏远程调控信息 | 测试更长输入窗口 | 方法：固定 1 kb 输入 |
| 未报告跨物种泛化 | 小鼠模型可能不适用于人类 | 人类疾病相关调控变异可能无法建模 | 在人类 ATAC-seq 数据上测试 | 讨论：未提及 |

## 14 学到什么

**Agent 提炼的知识候选**：

1. **多任务分辨率提升策略**：在 TF–DNA 互作建模中，同时预测聚合信号（如可及性）和细粒度信号（如 Tn5 footprint）可作为一种自监督/多任务正则化，提升聚合任务性能。可迁移到 TF 结合强度预测：同时预测 ChIP-seq peak 强度和 footprint 深度。

2. **无需显式偏置分解**：bpAI-TAC 表明，在双头架构下，模型可隐式学习 Tn5 偏置，无需像 ChromBPnet 那样显式建模。这提示在 TF–DNA 结合预测中，可通过架构设计（如分离 profile 和 count 预测）隐式处理技术偏置。

3. **分辨率消融实验设计**：通过 1/5/10/20 bp 分箱比较，系统评估分辨率对性能的影响。类似实验设计可迁移到其他 footprint 分析工具的参数选择。

4. **基序效应大小比较方法**：将基序插入随机背景序列，比较模型预测的 footprint 深度和可及性变化，可量化基序的细胞类型特异性效应。可迁移到 TF 结合特异性预测模型的解释。

5. **多任务 vs 单任务集成的比较**：多任务模型优于单任务集成，且更高效。在 TF–DNA 互作建模中，多细胞类型联合训练可能比逐细胞类型训练更有效。

6. **偏置模型训练策略**：使用蛋白-free DNA 或 closed OCR 聚合数据训练偏置模型，可分离技术偏置。可迁移到其他测序技术（如 ChIP-seq 的 input 对照）的偏置建模。

7. **模型解释的基序发现流程**：DeepSHAP → seqlet 提取 → 聚类 → Tomtom 注释 → 与已知基序比较，是系统的 TF motif 发现流程，可迁移到其他序列-功能模型。

## 15 与已有知识连接

- **与 ChromBPnet（Pampari et al. 2024）**：bpAI-TAC 直接继承 ChromBPnet 的架构思想（双头输出、偏置建模），但改为多任务框架，并发现无需显式偏置分解。两者比较显示，多任务学习可替代单任务 + 显式偏置校正。
- **与 BPnet（Avsec et al. 2021）**：bpAI-TAC 的 profile 头设计源自 BPnet，但 BPnet 为单任务，bpAI-TAC 扩展为多任务。
- **与 AI-TAC（Maslova et al. 2020）**：bpAI-TAC 是 AI-TAC 的直接升级，通过增加 profile 任务提升可及性预测。
- **与 TF footprint 分析工具（如 HINT-ATAC，Li et al. 2019）**：bpAI-TAC 的 footprint 生成能力可与专用 footprint 工具互补，但模型生成的 footprint 是预测性的，而非直接从数据中调用。
- **与 DeepSEA（Zhou & Troyanskaya 2015）**：同为序列-功能模型，但 DeepSEA 预测多种功能基因组学信号，bpAI-TAC 专注于 ATAC-seq 且分辨率更高。
- **与 Enformer（Avsec et al. 2021）**：Enformer 预测长程调控，bpAI-TAC 聚焦局部（1 kb），两者可互补。
- **与 TF–DNA 结合机制**：bpAI-TAC 的 footprint 预测直接反映 TF 占据，可用于推断 TF 结合强度，与结构预测（如 AlphaFold 3）和分子动力学模拟互补——序列模型提供全基因组范围的结合预测，结构方法提供原子级机制。

## 16 研究想法

**Agent 生成的研究候选**：

1. **候选名称**：TF–DNA 结合亲和力的多分辨率预测框架
   - **来源局限/观察**：bpAI-TAC 仅预测 ATAC-seq 可及性，未直接预测 TF 结合亲和力；且 footprint 深度与结合强度的定量关系未验证。
   - **核心假设**：将 ChIP-seq 的 TF 结合强度（peak 高度）与 ATAC-seq footprint 深度联合建模，可提升结合亲和力预测精度。
   - **增量**：在 bpAI-TAC 架构上增加 TF 结合强度输出头，使用多任务学习同时预测可及性、footprint 和 ChIP-seq 信号。
   - **初步方法**：使用 ENCODE 或 Cistrome 的 ChIP-seq 数据，对同一细胞类型同时训练三个输出头，比较联合 vs 独立训练的性能。
   - **验证方式**：在 held-out 染色体上比较 Pearson R；用已知 TF 基序突变实验验证预测的亲和力变化。
   - **创新状态**：unverified

2. **候选名称**：基于深度学习的 TF footprint 到结合构象的映射
   - **来源局限/观察**：bpAI-TAC 的 footprint 预测是序列层面的，未与 TF 的 3D 结合构象关联。
   - **核心假设**：footprint 的深度和形状与 TF 的结合构象（如结合角度、接触残基）相关，可通过深度学习建立映射。
   - **增量**：将 bpAI-TAC 的 footprint 预测与 AlphaFold 3 或 MD 模拟的 TF–DNA 复合物结构结合，建立序列-footprint-结构的三级映射。
   - **初步方法**：对已知结构的 TF–DNA 复合物，计算其预测 footprint 与结构特征（如接触残基、结合角度）的相关性；训练一个编码器将 footprint 映射到结构空间。
   - **验证方式**：在已知结构的 TF 上测试映射精度；用突变实验验证预测的结构变化。
   - **创新状态**：unverified

3. **候选名称**：多任务 S2A 模型中的 Tn5 偏置解耦与可迁移性
   - **来源局限/观察**：bpAI-TAC 未显式建模 Tn5 偏置，但偏置可能在不同细胞类型或实验条件下变化。
   - **核心假设**：显式解耦 Tn5 偏置（如通过对抗训练或独立偏置模块）可提升模型在不同数据集间的迁移能力。
   - **增量**：在 bpAI-TAC 中加入偏置解耦模块，使用域适应技术（如 DANN）使模型对实验批次不敏感。
   - **初步方法**：在多个独立 ATAC-seq 数据集（不同实验室、不同 Tn5 批次）上训练，比较有无偏置解耦的迁移性能。
   - **验证方式**：跨数据集预测精度；footprint 一致性分析。
   - **创新状态**：unverified

4. **候选名称**：碱基对分辨率下的 TF 协同结合语法解码
   - **来源局限/观察**：bpAI-TAC 识别了 23 个新基序，但未分析基序间的协同或拮抗关系。
   - **核心假设**：碱基对分辨率的模型可揭示 TF 结合位点间的精确间距和方向偏好，从而解码协同结合语法。
   - **增量**：利用 bpAI-TAC 的 attribution map 分析基序对共现模式，与已知的 TF 协同结合（如 pioneer factor 和 settling factor）比较。
   - **初步方法**：对 attribution map 进行基序对共现分析，统计显著富集的间距和方向；用 DNA 突变实验验证预测的协同效应。
   - **验证方式**：与 ChIP-seq 共结合数据比较；电泳迁移实验（EMSA）验证。
   - **创新状态**：unverified

5. **候选名称**：从 ATAC-seq footprint 到 TF 结合自由能的预测模型
   - **来源局限/观察**：bpAI-TAC 的 footprint 是定性信号，未定量化为结合自由能。
   - **核心假设**：footprint 深度与 TF 结合自由能（ΔG）存在定量关系，可通过校准学习预测 ΔG。
   - **增量**：将 bpAI-TAC 的 footprint 预测与已知 TF–DNA 结合自由能数据（如 PBMs、HT-SELEX）联合训练，输出 ΔG 估计。
   - **初步方法**：使用 PBMs 或 HT-SELEX 的定量结合数据作为监督信号，微调 bpAI-TAC 的 profile 头，输出每碱基的 ΔG 贡献。
   - **验证方式**：在 held-out 的 TF 上比较预测 ΔG 与实验值；用表面等离子体共振（SPR）验证。
   - **创新状态**：unverified