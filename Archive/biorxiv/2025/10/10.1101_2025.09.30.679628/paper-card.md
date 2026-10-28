## 01 基本信息

- **标题**：Qimai: a multi-agent framework for zero-shot DNA-protein interaction prediction
- **作者**：Cong Liu; Mina Yao; Wei Wang
- **单位**：Wang Lab, UC San Diego（由致谢与代码仓库推断，原文未提供完整单位列表）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2025
- **论文类型**：方法学/框架论文（含基准评测）
- **领域**：基因组学、蛋白质-DNA互作预测、AI agent、大语言模型
- **关键词**：DNA-protein interaction、zero-shot、multi-agent、LLM、transformer、motif、transcription factor
- **DOI/ID**：10.1101/2025.09.30.679628
- **代码**：https://github.com/Wang-lab-UCSD/DPI-agent
- **数据**：ENCODE ChIP-seq（Encode3and4、ChIP_690）、CisBP、STRING、UniProt、AlphaFold2 embeddings
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文聚焦 TF–DNA 结合机制预测，核心创新在于将深度学习 DPI 预测与生物 motif 证据（直接+间接）通过 LLM 推理进行整合，实现零样本泛化到未见蛋白。与纯端到端深度学习（DeepSEA、Sei、DNABERT）形成对照，属于「AI × 蛋白质-DNA 互作」方向中「多智能体/LLM 推理」分支，强调可解释性与证据整合，而非物理模拟或结构预测。

## 02 一句话总结

本文提出 Qimai——一个由 LLM 驱动的多智能体框架，将 transformer DPI 模型的定量预测与查询蛋白的直接 motif 证据及其互作蛋白的间接 motif 证据整合，通过推理与批判智能体输出可解释的 DNA-蛋白结合预测，在 78 个未见蛋白的零样本基准上较最佳独立模型将 AUC-PR 提升 17.6%、MCC 提升 244%。

## 03 研究问题

- **具体问题**：现有深度学习模型（DeepSEA、Sei、DNABERT 等）在预测 DNA-蛋白互作时，对训练中未出现过的蛋白（unseen/novel proteins）泛化能力差，且无法处理大量通过蛋白-蛋白互作（PPI）被招募到染色质上、本身缺乏 DNA 序列特异性的蛋白（如 cohesin 组分、染色质修饰酶）。
- **为什么重要**：真实基因组中大量关键调控因子（如 RAD21、CBX3、MTA3）并不直接识别 DNA 序列，而是通过与其他 TF 形成复合物被招募。仅依赖序列 motif 的模型对这些蛋白系统性失效，限制了调控机制解析和疾病位点发现。
- **现有方法不足**：端到端黑箱模型缺乏可解释性；训练分布外泛化差；无法利用生物学先验知识（如 PPI 网络、已知 motif 数据库）进行推理。
- **精确研究问题**：Can a multi-agent framework that integrates deep learning predictions with direct and indirect motif evidence via LLM reasoning achieve superior zero-shot generalization to unseen proteins compared to standalone deep learning models?

## 04 背景与发展脉络

> 注：以下脉络基于本文 Introduction 与 Results 的叙述，属「仅本文框架」，未经外部系统核验。

1. **第一代：序列 motif 扫描**（如 CisBP、FIMO）——依赖已知 motif 数据库，对无已知 motif 的蛋白失效。
2. **第二代：深度学习端到端模型**——DeepSEA（CNN）、Sei（改进 CNN）、DNABERT（预训练 DNA 语言模型）等，利用 ChIP-seq 大数据学习序列-结合关系。优点：自动特征提取；缺点：黑箱、不可解释、对未见蛋白泛化差。
3. **第三代（本文主张）：多智能体证据整合**——将深度学习预测视为一种「证据」，与生物知识（直接 motif、间接 PPI motif）并列，由 LLM 作为推理引擎动态加权整合。核心转变：从「单一模型预测」到「多源证据推理」，从「黑箱」到「可解释」。

**本文位置**：处于第三代的开创性工作，主张模块化、可解释、零样本泛化的新范式。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 对未见蛋白泛化差 | 独立模型在 unseen proteins 上性能大幅下降 | 模型仅从训练蛋白的序列特征中学习，无法外推到新蛋白 | Results 图 2A；Supplementary Table 7 |
| 无法处理非序列特异性结合 | 对 RAD21、CBX3 等无已知 motif 的蛋白预测失败 | 这些蛋白通过 PPI 被招募，本身不直接识别 DNA | Results 图 2E-G；Discussion |
| 黑箱不可解释 | 无法理解模型为何做出预测 | 端到端深度学习缺乏中间推理步骤 | Introduction；Discussion |
| 数据偏差导致捷径学习 | DPI-bench 与 DNA-only 模型性能几乎相同，蛋白模块贡献可忽略 | 正负样本 DNA 序列分布差异使模型仅靠 DNA 模式即可分类 | Supplementary Note A；Supplementary Figure 1D |
| 固定权重无法适应上下文 | LightGBM 集成分类器在冲突证据下失败 | 特征权重固定，无法根据蛋白新颖性动态调整证据权重 | Results 图 2C；AP2A 案例（Supplementary Figure S2E） |

## 06 核心思想

### 1) 表面方法
构建四个智能体：**Decision Agent**（transformer DPI 模型，双输入 DNABERT+AlphaFold2 embedding）、**Evidence Retriever**（扫描直接 motif + 间接 PPI motif）、**Reasoning Agent**（LLM 整合证据并推理）、**Critique Agent**（规则化置信度评分）。LLM 接收结构化「证据包」，动态决定各证据权重，输出预测+解释+置信度。

### 2) 核心洞察
- **将预测问题重构为证据推理问题**：深度学习模型输出只是证据之一，而非最终答案。LLM 可以像人类专家一样，在模型预测与生物先验冲突时，根据蛋白新颖性动态调整信任度。
- **间接证据是零样本泛化的关键**：对未见蛋白，其自身 motif 可能未知，但其互作蛋白的 motif 提供了可迁移的生物学线索。这模拟了「招募机制」的真实生物学。
- **模块化设计解耦了「学习」与「推理」**：深度学习负责从数据中学习序列-结合模式，LLM 负责利用外部知识进行情境化推理，两者互补。

### 3) 可能的普适教训 [Analysis]
- 对任何「数据驱动预测 + 领域先验知识」的任务，将先验知识显式编码为证据流，而非隐式注入训练，可同时提升泛化性和可解释性。
- 「模型置信度」与「蛋白新颖性」的交互是零样本泛化的核心杠杆——当模型对 OOD 输入不可靠时，外部知识应获得更高权重。
- 多智能体框架的价值不在于单个智能体的强大，而在于智能体间的分工与制衡（如 Reasoning 与 Critique 分离）。

## 07 方法总览

- **输入**：查询蛋白序列（UniProt ID）+ 查询 DNA 序列（512 bp）
- **输出**：二分类预测（结合/不结合）+ 置信度分数（0-1）+ LLM 文本解释
- **模块**：
  1. **Decision Agent**：transformer DPI 模型，DNA 编码器（DNABERT-6mer，768 维）+ 蛋白编码器（AlphaFold2 embedding，384 维），共享编码器架构，交叉注意力解码器，sigmoid 二分类
  2. **Evidence Retriever**：从 CisBP 获取直接 motif（最多 3 个），从 STRING 获取互作蛋白（score ≥ 700，最多 50 个）并扫描其 motif
  3. **Reasoning Agent**：LLM（默认 Gemini-2.0-flash），接收证据包，动态加权推理
  4. **Critique Agent**：规则化系统，基于 5 条标准调整置信度（证据一致性、motif 显著性、模型置信度等）
- **训练**：PyTorch 1.12.1，NVIDIA A6000 48GB，Adam + LambdaLR，交叉熵损失；DPI-bench 训练 20 小时，DPI 生产模型训练 150 小时
- **流程**：输入蛋白+DNA → DPI 模型输出概率 → Evidence Retriever 扫描直接/间接 motif → 构建证据包 → LLM 推理 → Critique 调整置信度 → 输出三元组（标签、置信度、解释）

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Decision Agent（DPI 模型） | 提供定量互作概率 | 提供数据驱动的基线预测，作为证据之一 | 输入：DNA 序列 + 蛋白序列；输出：概率分数 | Results 图 1C-D；Supplementary Table 5 | 预期：性能大幅下降（实测消融中 DPI 是主要贡献者之一，但具体数值未单独报告） |
| Evidence Retriever（直接 motif） | 扫描查询蛋白自身 motif | 提供序列特异性的直接证据 | 输入：蛋白 ID + DNA 序列；输出：motif 命中列表 | Results 图 2A；Supplementary Table 7 | 实测：移除后 F1 从 0.537 降至 0.368（内部交叉验证），为最大单因素贡献 |
| Evidence Retriever（间接 motif） | 扫描互作蛋白的 motif | 捕获 PPI 介导的招募机制，对非序列特异性蛋白关键 | 输入：蛋白 ID + STRING 互作网络；输出：互作蛋白 motif 命中 | Results 图 2D；RAD21 案例（图 2E-G） | 实测：移除后 F1 降至 0.501（内部交叉验证）；对 novel 蛋白子集影响更大 |
| Reasoning Agent（LLM） | 整合证据、动态推理、生成解释 | 固定权重分类器无法处理冲突证据；LLM 可情境化判断 | 输入：证据包（文本）；输出：预测标签+解释 | Results 图 2C；AP2A 案例 | 预期：替换为 LightGBM 后 MCC 下降 221%（实测对比） |
| Critique Agent | 规则化置信度校准 | 防止 LLM 过度自信或证据误读 | 输入：LLM 输出+证据元数据；输出：校准后置信度 | Supplementary Note B；Supplementary Figure S2B | 预期：移除后置信度校准变差（未单独消融） |

## 09 关键公式符号

本文未提供显式数学公式。核心概念性「公式」为证据整合逻辑：

- **证据包**：E = {D_direct, D_indirect, P_model}，其中 D_direct 为直接 motif 命中描述，D_indirect 为互作蛋白 motif 命中描述，P_model 为 DPI 模型概率
- **LLM 推理**：ŷ = LLM(E; θ_LLM)，输出二值预测
- **置信度校准**：C = f(ŷ, E, R)，其中 R 为规则集（5 条启发式），f 为确定性调整函数
- **零样本条件**：查询蛋白 p ∉ P_train，即 p 未出现在任何训练样本中

## 10 实验设计与证据链

**数据集与评测协议**：
- **训练集**：Encode3and4（1877 ChIP-seq 实验，844 TF），按染色体划分训练/验证/测试，严格非重叠
- **内部交叉验证**：5 次随机划分，每次从 844 TF 中留出 44 个 unseen 蛋白，测试集 1000 个平衡样本
- **外部验证**：ChIP_690（690 实验，158 TF），其中 78 个蛋白未出现在 Encode3and4 训练集中；51/78（65%）为 novel 蛋白（序列同一性 < 30%）；500 个平衡样本，10 次随机种子重复
- **指标**：AUC-PR、AUC-ROC、F1、MCC、Accuracy
- **基线**：DeepSEA、Sei、DNABERT、DPI（独立使用）
- **LLM 对比**：LightGBM 集成分类器（相同 16 维特征）
- **LLM 消融**：Gemini-1.5-flash、Gemini-2.0-flash、Gemma-3-27b-it

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| DPI 模型基准评测 | 新 transformer DPI 优于现有模型 | DPI vs DeepBind/DeepSEA/DNABERT，ChIP_690 | DPI 在多数指标上最优或持平 | 双输入架构+预训练 embedding 有效 | 提升幅度有限，非颠覆性 | Results 图 1C |
| 内部交叉验证 | Qimai 优于独立模型 | Qimai vs DPI/DeepSEA/Sei，5 折，unseen 蛋白 | Qimai F1=0.537，MCC=0.178；最佳独立模型 DPI F1=0.399，MCC=0.158 | 多智能体整合提升泛化 | 提升主要来自直接 motif，间接 motif 贡献较小（F1 0.537→0.501） | Results 图 1D |
| 外部零样本验证 | Qimai 在真正未见蛋白上泛化 | Qimai vs 独立模型，ChIP_690 中 78 unseen 蛋白 | Qimai AUC-PR=0.701，MCC=0.308；DPI AUC-PR=0.596，MCC=0.090；Sei 接近随机（MCC=-0.260） | 零样本泛化能力显著优于独立模型 | 样本量小（78 蛋白），需更大规模验证 | Results 图 2A；Supplementary Table 7 |
| novel 蛋白子集 | Qimai 对 novel 蛋白优势更大 | 51 个 novel 蛋白（<30% 同一性） | Qimai MCC=0.314，DPI=0.122，DeepSEA=0.166，Sei 为负 | 间接证据对 novel 蛋白尤为关键 | 未报告置信区间 | Results 图 2B |
| LLM vs LightGBM | LLM 推理优于固定权重分类器 | 相同特征，5000 样本测试集 | LLM MCC=0.305，LightGBM=0.095（+221% 相对提升） | 上下文感知推理优于静态加权 | 仅对比一个分类器；未测试其他集成方法 | Results 图 2C |
| 消融：移除直接 motif | 直接 motif 的贡献 | Qimai vs Qimai (w/o direct) | F1 0.537→0.368 | 直接 motif 是最大贡献因素 | 未报告分蛋白类型消融 | Results 图 1D |
| 消融：移除间接 motif | 间接 motif 的贡献 | Qimai vs Qimai (w/o indirect) | F1 0.537→0.501 | 间接 motif 提供补充性收益 | 对已知 motif 蛋白影响有限 | Results 图 1D |
| 注意力权重 vs DBD 注释 | 蛋白编码器学到生物学相关区域 | 34 个有 DBD 注释的蛋白，比较注意力高值区与 DBD 重叠 | 32/34 重叠 ≥50% | AlphaFold2 embedding 编码了 DNA 结合域信息 | 相关性非因果；样本量小 | Supplementary Figure 1C |
| 置信度校准 | Qimai 置信度可靠 | 校准曲线 vs 理想对角线 | 4 组参数均接近理想校准 | 置信度可作为可靠预测概率 | 未与独立模型校准对比 | Supplementary Figure S2B |
| 跨 LLM 鲁棒性 | 框架不依赖特定 LLM | Gemini-1.5/2.0-flash、Gemma-3-27b-it | 各 LLM 在 unseen 集上性能相当 | 框架架构驱动性能，非 LLM 特定能力 | 未测试更多 LLM | Supplementary Figure S3B |
| 多模型组合 | 多 Decision Agent 优于单模型 | DPI vs DPI+Sei vs DeepSEA+DPI+Sei | unseen 集上单 DPI 最优 | 对 OOD 场景，单一可靠模型优于多模型混合 | 与直觉相反，需进一步分析 | Supplementary Figure S3C |

## 11 结论正确解读

- **任务范围**：本文解决的是「给定蛋白+DNA 序列，预测是否互作」的二分类问题，基于 ChIP-seq 峰值数据。不涉及结合强度、结合动力学、构象变化或突变效应预测。
- **零样本定义**：unseen 蛋白指未出现在训练集中的蛋白，但测试 DNA 序列也可能与训练序列有重叠区域（染色体划分保证非重叠，但同一 TF 的不同实验可能共享相似序列）。
- **oracle/真值输入**：直接 motif 来自 CisBP 数据库（已知注释），间接 motif 来自 STRING PPI 网络（已知注释）。这些是「外部知识注入」，非模型自主学习。对无注释的蛋白，框架无法提供这些证据。
- **端到端状态**：框架依赖多个外部数据库（CisBP、STRING、UniProt）和预训练模型（DNABERT、AlphaFold2），非端到端训练。LLM 推理部分未微调，使用通用推理能力。
- **算力成本**：训练 DPI 生产模型需 150 小时单卡 A6000；推理时每次预测约 20 秒（含 LLM API 调用）。未报告 LLM API 成本。
- **历史数据依赖**：性能高度依赖 ChIP-seq 数据质量、CisBP motif 数据库覆盖度、STRING PPI 网络完整性。对研究较少的蛋白或非人类物种，性能可能显著下降。
- **边界复述**：Qimai 在 78 个未见蛋白的外部基准上，将 AUC-PR 从 0.596（最佳独立模型 DPI）提升至 0.701，MCC 从 0.090 提升至 0.308；但该提升主要来自直接 motif 证据，间接证据在 novel 蛋白（无已知 motif）场景下才成为决定性因素。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 依赖外部数据库完整性 | 预测精度受 CisBP motif 覆盖度和 STRING PPI 网络完整性限制 | 未明确说明 | Discussion |
| 当前强调序列和 motif 特征 | 未纳入表观遗传数据（如染色质可及性、组蛋白修饰） | 扩展 Evidence Retriever 纳入表观基因组数据（DNA 甲基化、组蛋白修饰、染色质可及性） | Discussion |
| 未考虑蛋白-蛋白互作的结构基础 | 间接证据仅基于 STRING 分数，未评估 PPI 的结构可行性 | 纳入蛋白结构以评估 PPI 可能性 | Discussion |
| 非 TF 蛋白预测受限于注释质量 | 对无已知 motif 或 PPI 注释的蛋白，框架缺乏证据来源 | 未明确说明 | Discussion |
| 依赖 LLM 推理质量 | 框架性能部分取决于 LLM 的推理能力 | 测试更多开源模型（已在 Supplementary Note B 中初步评估） | Supplementary Note B |

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 零样本基准的「unseen」定义可能过于宽松 | 78 个 unseen 蛋白中，部分可能与训练蛋白共享 DNA 结合域（DBD）同源性，即使整体序列同一性 <30% | 若 DBD 高度保守，模型可能通过 DBD 相似性间接「见过」这些蛋白，夸大零样本能力 | 按 DBD 家族分层分析性能；排除与训练蛋白共享 DBD 家族的蛋白 | Methods 中 novel 定义仅基于全序列同一性 |
| 间接 motif 证据的因果性存疑 | STRING 互作蛋白的 motif 命中可能只是共定位而非因果招募 | 若间接证据只是相关性，框架的「招募机制」解释可能过度 | 对预测为正的间接证据案例，验证互作蛋白是否确实在 ChIP-seq 中共同富集 | Results 图 2E-G 仅展示单个案例 |
| LLM 对比实验可能不公平 | LightGBM 使用 16 维手工特征，而 LLM 接收完整文本证据包，信息量不对等 | 若特征工程不足，LLM 的优势可能来自信息量而非推理能力 | 为 LightGBM 提供更丰富的特征（如 motif 位置、PPI 网络拓扑特征） | Results 图 2C |
| 注意力权重与 DBD 重叠的解读 | 高注意力区域与 DBD 重叠可能反映 embedding 的统计相关性，而非功能性 | 若注意力机制未真正编码结合机制，模型的可解释性主张被削弱 | 进行注意力扰动实验：遮蔽高注意力区域观察预测变化 | Supplementary Figure 1C |
| 置信度评分的规则化设计 | Critique Agent 的 5 条规则可能过拟合特定数据集 | 规则化系统在新场景（如不同物种）可能失效 | 在不同物种或细胞类型上验证置信度校准 | Supplementary Note B |
| 未报告负例的构建方式 | 负样本（非结合 DNA-蛋白对）的生成策略直接影响所有指标 | 若负样本过于简单（如随机序列），性能提升可能被高估 | 检查负样本是否来自 ChIP-seq 阴性区域或随机基因组区域 | Methods 数据部分未详细说明负样本构建 |
| 单一 LLM 默认配置 | 主要结果使用 Gemini-2.0-flash，其他 LLM 仅补充验证 | 商业 API 可能更新导致结果不可复现 | 固定 LLM 版本；测试更多开源模型 | Supplementary Note B |

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **证据解耦与再整合**：将预测任务分解为「数据驱动信号」（深度学习）与「知识驱动信号」（数据库 motif），再通过 LLM 动态整合。这一范式可迁移到 TF-DNA 结合机制研究中任何「序列特征 + 先验知识」并存的问题，如突变效应预测（结合已知 DBD 注释）、细胞类型特异性结合预测（结合表观遗传数据）。
2. **间接证据作为零样本泛化的桥梁**：对未见蛋白，直接 motif 缺失时，互作蛋白的 motif 提供了可迁移线索。这提示在 TF-DNA 结合机制建模中，应显式建模「招募/共结合」关系，而非仅关注蛋白自身的 DNA 结合域。
3. **模型置信度与输入新颖性的交互**：LLM 被提示在蛋白为 novel 时降低对模型预测的信任、提高对生物证据的依赖。这一「置信度调制」思想可迁移到任何 OOD 泛化场景——模型应知道自己不知道什么。
4. **可解释性作为设计目标而非事后补充**：Qimai 的模块化结构天然产生可解释输出（每个证据的贡献可见）。在 TF-DNA 结合机制研究中，这种设计有助于区分「直接结合」与「招募结合」两种模式，为湿实验验证提供可检验假设。
5. **数据偏差的显式处理**：Supplementary Note A 揭示了 DNA 序列偏差问题——正负样本分布差异导致模型走捷径。这提醒在构建 TF-DNA 训练数据时，负样本的构建策略（基因组阴性区域 vs 随机序列）直接影响模型学习到的「结合机制」是否真实。
6. **多智能体分工模式**：Decision（定量预测）、Retrieval（证据收集）、Reasoning（整合推理）、Critique（置信度校准）四角色分离，可类比于「预测-验证-解释-校准」的科研流程，适合迁移到其他组学预测任务。

## 15 与已有知识连接

- **深度学习 TF 结合预测**：本文与 DeepSEA（Zhou & Troyanskaya, 2015）、Sei（Chen et al., 2022）、DNABERT（Ji et al., 2021）形成直接对照。本文的 DPI 模型本身是 DNABERT+AlphaFold2 的双输入 transformer，可视为对 DNABERT 的扩展——将蛋白序列信息从「分类标签」升级为「序列 embedding」。
- **LLM 在生物学的应用**：本文属于「LLM as reasoning engine」分支，与 BioBERT、ProtGPT2 等「LLM as feature extractor」不同，更接近 agent-based 方法（如 ChemCrow、BioPlanner）。其创新在于将 LLM 用于「证据整合」而非「知识生成」。
- **TF 招募机制**：本文的间接证据设计呼应了已知生物学——RUNX1-TAL1-GATA 复合物、CTCF-RAD21 cohesin 复合物等。这与 ENCODE 项目中 TF 共结合分析、以及「先锋因子 vs 招募因子」的调控模型一致。
- **零样本/少样本学习**：本文的「unseen protein」设定与蛋白质功能预测中的「新蛋白泛化」问题一致，可对比 AlphaFold 的「新折叠泛化」、ESM 的「接触图零样本预测」。
- **可解释 AI 在基因组学**：本文的注意力权重-DBD 重叠分析（Supplementary Figure 1C）与「可解释深度学习用于 motif 发现」方向（如 DeepExplainer、TF-MoDISco）相关，但本文更强调「模块级可解释性」而非「特征级可解释性」。
- **[Analysis] 候选连接**：本文的「间接证据」思想可类比于图神经网络中的「消息传递」——通过 PPI 网络传播结合信号。未来可探索将 PPI 网络作为图结构显式编码，而非仅通过 LLM 文本推理。

## 16 研究想法

> 标题：Agent 生成的研究候选

**候选 1：结构感知的间接证据增强**
- **来源局限/观察**：本文间接证据仅基于 STRING 分数和 motif 共现，未考虑互作蛋白与查询蛋白之间的物理结合可行性（如 DBD 空间位阻、复合物构象）。
- **核心假设**：结合 AlphaFold2 预测的蛋白-蛋白复合物结构，过滤掉空间上不可能共结合的互作对，可提升间接证据的特异性。
- **增量**：在 Evidence Retriever 中增加结构过滤模块，将 STRING 互作对通过 AlphaFold-Multimer 打分筛选。
- **验证**：在 ChIP_690 unseen 蛋白上对比有无结构过滤的 AUC-PR/MCC。
- **创新状态**：unverified

**候选 2：动态证据权重学习的元学习框架**
- **来源局限/观察**：LLM 的权重调制依赖提示词工程，缺乏可学习的权重机制；LightGBM 权重固定无法适应上下文。
- **核心假设**：用元学习（MAML 或 Reptile）训练一个小型权重网络，根据蛋白新颖性、motif 质量、模型置信度等元特征，动态输出各证据权重，可替代 LLM 推理。
- **增量**：将 LLM 替换为可训练权重网络，提升可复现性并降低推理成本。
- **验证**：与 LLM 版本在相同基准上对比，并测试权重网络的可解释性。
- **创新状态**：unverified

**候选 3：细胞类型特异性的间接证据建模**
- **来源局限/观察**：本文使用静态 PPI 网络（STRING），未考虑细胞类型特异性的互作组。TF 的招募伙伴因细胞类型而异。
- **核心假设**：引入细胞类型特异的共表达网络或组织特异 PPI，可提升对细胞类型特异结合位点的预测。
- **增量**：将 Evidence Retriever 扩展为条件证据检索（给定细胞类型），LLM 推理时纳入细胞类型上下文。
- **验证**：在 ENCODE 多细胞类型数据上评估，对比静态 vs 动态 PPI 证据。
- **创新状态**：unverified

**候选 4：从二分类到结合强度回归**
- **来源局限/观察**：本文仅预测二元互作标签，未利用 ChIP-seq 峰值的信号强度（定量信息）。
- **核心假设**：将 DPI 模型输出改为结合强度回归，LLM 推理时纳入强度证据，可提升对弱结合位点的识别。
- **增量**：修改损失函数为回归损失，证据包中包含峰值信号值。
- **验证**：在保留定量信息的测试集上评估 Spearman 相关。
- **创新状态**：unverified

**候选 5：突变效应的零样本预测**
- **来源局限/观察**：本文框架预测「是否结合」，未涉及「突变如何影响结合」。但 motif 证据天然支持等位基因特异性分析。
- **核心假设**：将查询 DNA 替换为突变体序列，比较 Qimai 对参考/突变体的预测差异，可零样本预测突变对 TF 结合的影响。
- **增量**：无需重新训练，直接利用现有框架进行扰动分析。
- **验证**：在已知 eQTL/等位基因特异性结合数据集上评估。
- **创新状态**：unverified