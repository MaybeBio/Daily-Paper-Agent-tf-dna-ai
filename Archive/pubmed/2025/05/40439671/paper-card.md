## 01 基本信息
- **标题**：PLM-DBPs: enhancing plant DNA-binding protein prediction by integrating sequence-based and structure-aware protein language models
- **作者与单位**：Pokharel, Suresh; Barasa, Kepha; Pratyush, Pawel; Kc, Dukka B（单位未在摘要中提供，据基金信息推测涉及 Michigan Technological University 与 Rochester Institute of Technology）
- **期刊/预印本平台**：Briefings in Bioinformatics
- **年份**：2025
- **论文类型**：方法学（深度学习框架开发与基准评测）
- **领域**：生物信息学 / 蛋白质功能预测 / DNA 结合蛋白（DBP）预测
- **关键词**：DNA-binding proteins; plant; protein language models; structure-aware; deep learning; ProtT5; SaProt
- **DOI/arXiv 号**：10.1093/bib/bbaf245
- **代码**：https://github.com/suresh-pokharel/PLM-DBPs
- **数据**：训练/测试集来自 PlDBPred（UniProt，2021-06-14 访问）；独立测试集为作者新构建（GO:0003677，taxonomy ID:33090，2021-06-14 至 2025-03-22 间新增的 reviewed 蛋白）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「蛋白质–DNA 互作（TF–DNA 结合机制）× AI 方法」方向中的**序列/结构表征学习**子类。它不直接建模 TF–DNA 结合的物理机制或残基级接触，而是聚焦于**植物 DBP 的蛋白级二分类预测**，核心贡献在于验证了「序列 PLM + 结构感知 PLM 的分数级融合」对植物 DBP 预测的有效性。对本课题的可迁移点在于：结构感知表征（3Di 序列）与序列表征的互补性验证、轻量级 ANN 头部的设计、以及跨物种泛化（植物 vs 通用）的评测思路。

## 02 一句话总结
本文提出 PLM-DBPs，一个将序列 PLM（ProtT5）与结构感知 PLM（SaProt）的蛋白级表征分别训练 ANN 分类头、再以等权分数级融合的深度学习框架，在植物 DBP 预测任务上优于现有方法，并证明结构信息可进一步提升仅用序列表征的预测精度。

## 03 研究问题
- **具体问题**：如何利用序列与结构两种模态的 PLM 表征，提升**植物** DNA 结合蛋白（DBP）的预测准确性？
- **为什么重要**：植物 DBP 在基因调控、发育、环境响应中起核心作用；实验方法耗时耗力，计算预测可加速功能注释。现有通用 DBP 预测器在植物上精度不足，而植物专用工具（如 PlDBPred）仅用序列特征（PSSM），未利用结构信息。
- **现有方法不足**：(1) 多数方法依赖手工特征（PSSM、理化性质），特征工程成本高；(2) 已有 PLM 方法（如 ESM-DBP）仅用序列模态，忽略结构信息；(3) 植物 DBP 与通用 DBP 存在物种特异性差异，通用模型泛化不佳。
- **精确研究问题**：Can integrating structure-aware PLM representations with sequence-based PLM representations improve plant DBP prediction over sequence-only models?

## 04 背景与发展脉络
> 注：以下脉络基于本文引言与相关工作，属于「仅本文框架」——本文未提供系统性综述，以下为作者叙述的演进逻辑。

1. **传统机器学习阶段**：IDRBP-PPCT（RF + PSSM/PSFM/PPCT）、StackDPPred（SVM/LR/KNN 集成 + PSSM/EDT/RPT）、PlDBPred（SVM + PSSM，植物专用）。局限：依赖手工特征，特征工程繁琐。
2. **深度学习 + 进化特征阶段**：iDRBP_MMC（CNN + PSSM，多标签）、DeepDRBP-2L（CNN + biLSTM + PSSM）、PDBP-Fusion（CNN + biLSTM + one-hot）、Wu et al. 的层次/多类 CNN-LSTM。局限：仍以 PSSM 为主，未利用大规模预训练。
3. **序列 PLM 阶段**：PreDBP-PLMs（CNN + PLM 表征 + PSSM）、ESM-DBP（微调 ESM-2）。优势：利用大规模无监督预训练，表征丰富；局限：仅序列模态，忽略结构。
4. **结构感知 PLM 阶段（本文位置）**：随着 AlphaFold 使结构可及，结构感知 PLM（如 SaProt）出现。本文首次（据作者主张）将序列 PLM 与结构感知 PLM 结合用于**植物** DBP 预测，验证结构信息的互补价值。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 植物 DBP 预测精度不足 | 通用 DBP 预测器在植物数据上表现不佳 | 植物蛋白具有独特的结构与功能特性，通用模型难以泛化 | Introduction 第 2 段（"general DNA-binding predictor often struggle to accurately generalize the plant-specific DBPs"） |
| 现有方法忽略结构信息 | 多数方法仅用序列特征（PSSM、PLM 表征） | 结构数据获取困难，或未意识到结构表征的互补价值 | Introduction 第 3-4 段（"existing methods predominantly rely on sequence-based representations and handcrafted features"） |
| 手工特征工程成本高 | 需设计 PSSM、理化性质等多类特征 | 传统方法依赖领域知识进行特征设计 | Introduction 第 2 段（对 IDRBP-PPCT、StackDPPred 等的描述） |
| 结构信息获取的计算瓶颈 | 生成 3D 结构或 3Di 序列需要额外计算 | 运行 AlphaFold 或 Foldseek 成本高 | Methods "Getting 3Di sequence" 节（作者因计算资源限制改用 ProstT5 预测 3Di） |
| 融合策略选择困难 | 不同融合方式（early/cross-attention/late）效果差异大 | 特征维度增加与模型复杂度可能导致过拟合或欠拟合 | Results "Ablation study on fusion strategies"（feature-level 与 cross-attention 效果不佳） |

## 06 核心思想
1. **表面方法**：提取蛋白序列的 ProtT5 表征（1024 维）与结构感知的 SaProt 表征（1280 维），分别训练独立的 ANN 分类头，最后以等权（w₁=w₂=0.5）分数级融合（late fusion）得到最终预测概率，阈值 0.5 分类。
2. **核心洞察**：序列与结构两种模态的 PLM 表征携带**互补**信息——序列 PLM 捕捉进化与序列上下文，结构感知 PLM 捕捉局部几何相互作用（3Di 编码）。分数级融合避免了特征拼接带来的维度灾难与过拟合，是简单而有效的整合方式。
3. **可能的普适教训 [Analysis]**：对于蛋白功能预测任务，当两种表征各自已很强时，**late fusion 优于 early fusion** 可能是一个普遍规律——因为 early fusion 迫使模型在高维空间中学习跨模态交互，需要更多数据；而 late fusion 保留了各模态独立决策的稳健性。此外，**结构信息不一定要精确的原子坐标**，3Di 这类粗粒化结构编码在资源受限时是可行的替代。

## 07 方法总览
- **输入**：蛋白氨基酸序列（长度 ≥ 50，无非标准氨基酸）
- **输出**：二分类概率（DBP vs non-DBP）
- **模块**：
  1. 序列表征提取：ProtT5（T5 架构，编码器最后一层隐藏状态，平均池化 → 1024 维）
  2. 结构表征提取：SaProt（输入为 AA+3Di 联合 token，平均池化 → 1280 维）
  3. 分类头：两个独立 ANN（结构见表 3，具体层数/神经元数未在摘要中给出）
  4. 融合：分数级加权平均（w₁=w₂=0.5）
- **训练**：五折交叉验证；网格搜索 + KerasTuner 超参数优化；对比分类器包括 SVM、RF、ANN、CNN-1D
- **工具**：未明确列出（推测为 PyTorch/TensorFlow + HuggingFace transformers）
- **反馈回路**：无（静态监督学习，无主动学习或迭代优化）
- **文字流程**：蛋白序列 → 并行输入 ProtT5（序列）与 SaProt（序列+3Di）→ 分别平均池化得到 1024 维与 1280 维表征 → 各自经 ANN 分类头得到概率 p₁、p₂ → p = 0.5·p₁ + 0.5·p₂ → 阈值 0.5 判定 DBP/non-DBP

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| ProtT5 序列表征 | 提取蛋白序列的上下文嵌入 | 序列 PLM 捕捉进化与序列模式，是 DBP 预测的强基线 | 输入：AA 序列；输出：1024 维蛋白级向量 | Table 4（ProtT5-ANN 在五折 CV 中表现优异） | 预期显著下降（序列信息是 DBP 预测的主要信号）[预期效应，未做单模态消融] |
| SaProt 结构表征 | 提取结构感知嵌入（3Di 编码） | 结构信息补充序列无法捕捉的几何特征 | 输入：AA+3Di 联合序列；输出：1280 维蛋白级向量 | Table 4（结构表征单独使用即接近序列表征性能）；Table 5（融合后提升） | 单独移除后性能下降但幅度小于移除 ProtT5 [预期效应，基于 Table 4 中两者单独性能接近] |
| ANN 分类头 | 将 PLM 表征映射为二分类概率 | 简单 MLP 足以利用高质量表征，避免复杂模型过拟合 | 输入：1024/1280 维向量；输出：概率标量 | Table 4（ANN 与 CNN-1D 性能相当，选 ANN 因简洁） | 替换为更复杂模型（CNN-1D）性能无显著提升 [实测，Table 4] |
| 分数级融合 | 等权平均两个分类头的概率 | 融合序列与结构决策，互补信息提升鲁棒性 | 输入：p₁, p₂；输出：p = 0.5p₁ + 0.5p₂ | Table 5（late fusion 优于 early fusion 与 cross-attention） | 替换为 early fusion 或 cross-attention 后性能下降 [实测，Table 5] |
| 3Di 序列生成（ProstT5 预测） | 从序列预测 3Di 结构编码 | 避免运行 AlphaFold/Foldseek 的高计算成本 | 输入：AA 序列；输出：3Di 序列 | Methods "Getting 3Di sequence" 节（作者对比后选 ProstT5） | 若用 Foldseek 真实验证 3Di 可能略有提升，但作者称差异可忽略 [作者主张，未提供量化数据] |

## 09 关键公式符号
- **融合概率**：p = w₁·p₁ + w₂·p₂，其中 w₁ = w₂ = 0.5，p₁ 为 ProtT5-ANN 输出概率，p₂ 为 SaProt-ANN 输出概率。用途：最终分类决策。直觉：等权平均两个独立模型的置信度，简单且稳健。
- **分类阈值**：p_θ = 0.5，p ≥ 0.5 判为 DBP，否则 non-DBP。
- **评估指标**：Sensitivity = TP/(TP+FN)；Specificity = TN/(TN+FP)；Accuracy = (TP+TN)/(TP+TN+FP+FN)；Precision = TP/(TP+FP)；F1 = 2·Precision·Recall/(Precision+Recall)；MCC = (TP·TN − FP·FN)/√((TP+FP)(TP+FN)(TN+FP)(TN+FN))。用途：模型评估。直觉：MCC 对类别不平衡更稳健。
- **注**：本文未提供损失函数、池化公式等细节（摘要中未给出），以上为文中明确出现的公式。

## 10 实验设计与证据链
**数据集与评测设置**：
- 训练/主测试集：PlDBPred 数据集（UniProt，2021-06-14 访问），含 849 DBP（正）与 1848 non-DBP（负），负类随机平衡后训练；独立测试集 997 条（500 non-DBP，497 DBP）
- 独立新测试集：作者自建，GO:000077（应为 GO:0003677）注释、taxonomy ID:33090、reviewed、2021-06-14 至 2025-03-22 间新增，20 条 DBP
- 通用验证集：Wu & Guo 的四分类数据集（RBP/SSB/DSB/NABP），用于验证通用 DBP 预测能力
- 指标：Sensitivity、Specificity、Accuracy、Precision、F1、MCC、AUROC、AUPR
- 硬件：单张 A100 80GB（训练）；推理在 Intel Xeon W-2145 CPU
- 对比基线：DNAbinder、DPP_PseAAC、iDRBP_MMC、IDRBP-PPCT、PDBP-fusion、DeepDRBP、StackDPPred、PlDBPred、ESM-DBP

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 单表征消融（Table 4） | 不同 PLM 表征 + 不同分类头的性能 | 5 种序列 PLM（Ankh、ESM-2 三版本、ProtT5）× 4 种分类头（SVM、RF、ANN、CNN-1D）；另测 SaProt 表征 | ProtT5-ANN 综合最优；SaProt-ANN 与 ProtT5-ANN 性能接近 | 序列与结构表征均携带强预测信号 | 无法判断哪种表征对特定 TF 亚类更优（未做亚类分析） | Results "Ablation study on individual PLM representation" |
| 融合策略对比（Table 5, Fig. 4） | late fusion 优于 early fusion 与 cross-attention | 同一 ProtT5+SaProt 表征，三种融合方式，五折 CV | late fusion 在多数指标上最优或持平 | 分数级融合是简单有效的整合方式 | 未证明 late fusion 在所有数据集上显著优于其他方式（"on par or outperforms"） | Results "Ablation study on fusion strategies" |
| 与现有工具对比（Table 6） | PLM-DBPs 优于已有 DBP 预测器 | 在 PlDBPred 独立测试集上与 9 个工具对比 | PLM-DBPs 在多数指标上最优 | 整合结构信息可提升植物 DBP 预测 | 未报告统计显著性检验 | Results "Comparison with existing tools" |
| 时间泛化测试 | 模型对新增数据的泛化能力 | 20 条 2021 年后新增的植物 DBP | MCC 85.9%，优于 PlDBPred（识别出额外 2 条 DBP） | 模型具有时间泛化能力 | 样本量极小（20 条），结论有限 | Results "Comparison with PlDBPred" |
| 通用 DBP 验证 | 方法不限于植物 | Wu & Guo 四分类数据集 | 表现良好（具体数值未在摘要中给出） | 方法可迁移至通用 DBP 预测 | 四分类任务与二分类任务不可直接比较 | Supplementary Section S2 |

## 11 结论正确解读
- **任务范围**：本文解决的是**蛋白级二分类**（是否为 DBP），而非残基级 DNA 结合位点预测，更非 TF–DNA 结合机制（如结合亲和力、结合构象）的建模。
- **Oracle/真值输入**：训练标签来自 GO 注释（GO:0003677），本质是功能注释而非实验验证的结合活性；负样本为无该注释的蛋白，可能存在注释缺失导致的噪声。
- **端到端状态**：模型是「表征提取（冻结 PLM）+ 浅层分类头」的流水线，并非端到端微调 PLM；PLM 权重未针对 DBP 任务优化。
- **算力成本**：训练仅需单张 A100；但推理需先运行 ProtT5 与 SaProt 两个模型，且 SaProt 需要 3Di 序列（由 ProstT5 预测），实际部署成本高于单序列模型。
- **历史数据依赖**：训练数据截至 2021-06-14，独立测试集为 2021-2025 新增数据，验证了时间泛化，但 20 条样本量极小。
- **模型依赖**：性能高度依赖 PLM 表征质量；若 PLM 更新（如 ESM-3），需重新评测。
- **最难情形**：未分析——模型对短序列、低复杂度序列、或与已知 DBP 同源性极低的新型结合蛋白的表现未知。
- **群体/领域边界**：仅覆盖植物（35 个物种）；通用 DBP 验证在四分类数据集上进行，但未报告逐类指标。
- **有边界的复述**：在 PlDBPred 数据集（截至 2021 年的植物蛋白）上，等权分数级融合 ProtT5 与 SaProt 表征的 ANN 模型，在独立测试集上优于 9 个现有工具，并在 20 条 2021 年后新增的植物 DBP 上达到 MCC 85.9%；结构信息的增益在融合后体现，但单独使用 SaProt 并不显著优于单独使用 ProtT5。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 结构信息利用有限 | 仅通过 3Di 序列（粗粒化结构编码）间接利用结构，未使用完整 3D 坐标 | 探索更有效的结构信息整合技术 | Conclusion（"current approach leverages only limited structural knowledge through 3Di sequences"） |
| 融合策略简单 | 等权固定权重，未动态调整 | 动态权重分配，基于各模态对决策的贡献 | Conclusion（"dynamically assigning their weights based on their contributions"） |
| 未探索最新 PLM | 未评测 ESM-3、xTrimoPGLM 等更新模型 | 基准测试更先进的序列 PLM | Conclusion（"benchmarking advanced sequence-based PLMs such as ESM3, xTrimoPGLM"） |
| 结构数据库覆盖有限 | 仅依赖 AlphaFold/PDB 可及的结构 | 整合更多样化的结构数据库 | Conclusion（"incorporate diverse structural databases"） |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 独立测试集仅 20 条 | MCC 85.9% 的置信区间极宽，可能不具统计显著性 | 时间泛化结论可能被小样本夸大 | 扩大独立测试集，或报告置信区间/置换检验 | Results "Comparison with PlDBPred"（20 条样本） |
| 负样本定义依赖 GO 注释缺失 | 无 GO:0003677 注释的蛋白可能仍是 DBP（注释不全），导致负样本污染 | 模型可能学习的是「注释完整性」而非「结合能力」 | 用实验验证的非 DBP 子集重测，或检查预测为 DBP 的负样本是否近期被新注释 | Methods "Dataset"（负样本来自无 GO 注释的蛋白） |
| 未报告统计显著性检验 | Table 6 的对比未说明差异是否显著 | 性能提升可能是噪声 | 对主要指标做 DeLong 检验（AUROC）或 bootstrap 置信区间 | Results "Comparison with existing tools"（未提及显著性） |
| 3Di 预测误差的级联效应 | 使用 ProstT5 预测 3Di 而非真实结构，预测误差可能影响 SaProt 表征 | 若 3Di 预测不准，结构增益可能被低估或高估 | 对比真实结构（PDB/AlphaFold）与预测 3Di 的性能差异 | Methods "Getting 3Di sequence"（作者仅在小规模实验中对比，未系统量化） |
| 未做残基级评估 | 模型只输出蛋白级标签，无法定位 DNA 结合残基 | 对机制研究价值有限，无法指导突变实验 | 在残基级数据集（如预测结合残基）上评测表征质量 | 全文未涉及残基级分析 |
| 等权融合可能非最优 | 不同蛋白可能更依赖某一模态，固定权重缺乏适应性 | 动态融合可能进一步提升性能 | 实现基于注意力或置信度的动态加权并对比 | Conclusion（作者自认未来方向） |

## 14 学到什么
> 标题：Agent 提炼的知识候选

1. **结构感知表征的「轻量」获取路径**：本文展示了用 ProstT5 预测 3Di 序列替代昂贵结构计算（AlphaFold/FoldScan）的可行性，且性能差异可忽略。**迁移到 TF–DNA 课题**：在缺乏实验结构的大规模 TF 筛选中，可用 3Di 预测作为结构模态的代理，避免对每个 TF 运行 AlphaFold。
2. **Late fusion 作为多模态整合的稳健基线**：在特征维度高、数据量有限时，分数级融合（等权平均）优于特征拼接（early fusion）与注意力融合。**迁移到 TF–DNA 课题**：当同时使用序列 PLM（如 ESM-2）与结构表征（如 AlphaFold 结构编码）预测 TF 结合特异性时，可先尝试 late fusion 作为基线，再探索更复杂的融合。
3. **物种特异性建模的必要性**：通用 DBP 预测器在植物上表现不佳，说明训练数据的物种分布对泛化影响显著。**迁移到 TF–DNA 课题**：TF–DNA 结合机制在不同物种（如人 vs 植物 vs 细菌）中存在差异，构建物种特化模型或引入物种信息作为条件输入可能优于单一通用模型。
4. **简单分类头 + 强表征的充分性**：ANN 与 CNN-1D 性能相当，说明 PLM 表征已高度线性可分。**迁移到 TF–DNA 课题**：在 TF 结合位点预测中，可先验证简单分类头（逻辑回归/浅层 MLP）在强表征上的表现，避免不必要的模型复杂度。
5. **时间切分的独立测试集设计**：作者构建了训练期之后新增蛋白的测试集，验证时间泛化。**迁移到 TF–DNA 课题**：在评估 TF–DNA 预测模型时，应按时间切分数据（如训练集用 2020 年前的结构/序列，测试集用 2020 年后新增的），避免因数据库更新导致的泄漏。
6. **多模态互补性的验证范式**：先分别评测各模态单独性能，再评测融合性能，以证明互补性而非冗余性。**迁移到 TF–DNA 课题**：在结合序列与结构信息时，应报告各模态单独与融合的完整对比，而非只报告融合结果。

## 15 与已有知识连接
- **PlDBPred（SVM + PSSM，植物 DBP 预测）**：本文的直接前作与主要对比基线。本文用 PLM 表征替代手工 PSSM 特征，并引入结构模态，验证了表征学习的优势。**连接**：在 TF–DNA 课题中，可参考 PlDBPred 的植物 DBP 数据集构建思路，但用 PLM 表征替代传统特征。
- **ESM-DBP（微调 ESM-2 做 DBP 预测）**：本文对比的 PLM 基线之一。本文未微调 PLM，而是冻结表征 + 训练分类头，说明冻结表征在数据量有限时已足够。**连接**：在 TF 结合特异性预测中，可对比「冻结 PLM + 分类头」与「微调 PLM」的性价比。
- **SaProt（结构感知 PLM，AA+3Di 联合 token）**：本文采用的结构模态模型。SaProt 的 3Di 编码源自 FoldSeek，将结构信息序列化。**连接**：在 TF–DNA 课题中，SaProt 或类似结构感知 PLM 可用于编码 TF 的结构特征，与 DNA 序列编码器结合。
- **Wu & Guo 的四分类 DBP 数据集（RBP/SSB/DSB/NABP）**：本文用于验证通用性的数据集。**连接**：该数据集区分单链/双链 DNA 结合蛋白，对 TF–DNA 课题有参考价值——TF 通常结合双链 DNA，可在此数据集上检验模型是否偏好 DSB 类。
- **AlphaFold 与结构预测的普及**：本文的背景前提。AlphaFold 使结构信息可及，推动了结构感知 PLM 的发展。**连接**：在 TF–DNA 课题中，AlphaFold 预测的 TF 结构可作为结构模态输入，但需注意预测结构在 apo 状态与 DNA 结合构象间的差异。
- **[Analysis] 候选方向**：本文未涉及残基级结合位点预测，也未分析 TF 家族（如 bZIP、MYB、WRKY 等）的亚类性能差异。这两个方向是 TF–DNA 课题中自然延伸，可基于本文框架扩展。

## 16 研究想法
> 标题：Agent 生成的研究候选

1. **TF 家族特化的多模态融合模型**
   - 来源局限/观察：本文仅做 DBP 二分类，未区分 TF 家族；不同 TF 家族（如锌指、bZIP、homeodomain）的 DNA 结合机制差异显著。
   - 核心假设：TF 家族信息可作为条件输入，提升结合特异性预测的精度。
   - 增量：在本文的 ProtT5+SaProt 融合框架上，加入 TF 家族分类头或家族条件嵌入。
   - 初步方法：在植物 TF 数据集上，按 Pfam 家族分组训练/评测；对比「全局模型」与「家族条件模型」。
   - 验证方式：五折交叉验证 + 独立测试集；按家族分层报告 MCC/AUPR。
   - 创新状态：unverified

2. **残基级 DNA 结合位点预测的序列-结构融合**
   - 来源局限/观察：本文仅输出蛋白级标签，无法定位结合残基；TF–DNA 机制研究需要残基级信息。
   - 核心假设：序列 PLM 与结构感知 PLM 的 token 级表征融合，可提升结合残基预测的精度。
   - 增量：将本文的蛋白级池化改为 token 级预测头，输出每个残基的结合概率。
   - 初步方法：在植物 TF 数据集上标注已知 DNA 结合残基（如来自 PDB 结构或 UniProt 注释）；对比「序列-only」「结构-only」「融合」三种 token 级模型。
   - 验证方式：残基级 Precision/Recall、AUPRC；与现有结合位点预测工具对比。
   - 创新状态：unverified

3. **动态权重融合：基于置信度的自适应多模态整合**
   - 来源局限/观察：本文使用固定等权融合，未考虑不同蛋白对序列/结构模态的依赖差异。
   - 核心假设：对序列保守性高但结构预测置信度低的蛋白，应加大序列模态权重，反之亦然。
   - 增量：在融合层加入一个元分类器，根据输入蛋白的序列熵、3Di 预测置信度等特征动态分配权重。
   - 初步方法：在本文框架上，将固定 w₁=w₂=0.5 替换为可学习的权重网络；对比固定权重与动态权重的性能。
   - 验证方式：五折交叉验证 + 独立测试集；分析动态权重与蛋白特征的相关性。
   - 创新状态：unverified

4. **跨物种 TF–DNA 结合机制的可迁移性分析**
   - 来源局限/观察：本文聚焦植物，但 TF–DNA 结合机制在真核生物中保守；通用 DBP 模型在植物上表现不佳。
   - 核心假设：植物 TF 与动物 TF 的 DNA 结合域在结构上保守，但在侧翼序列上存在物种特异性差异。
   - 增量：在本文框架上，用多物种数据训练，并分析模型在植物/动物/真菌上的迁移表现。
   - 初步方法：收集植物、动物、真菌的 TF 数据集；训练多物种模型，按物种分组评测；分析错误预测的序列特征。
   - 验证方式：跨物种迁移测试；UMAP 可视化表征分布。
   - 创新状态：unverified

5. **结合亲和力预测的连续值回归扩展**
   - 来源局限/观察：本文是二分类，但 TF–DNA 结合是连续亲和力；分类模型丢失了强度信息。
   - 核心假设：序列+结构融合表征可预测 TF–DNA 结合亲和力的相对强弱。
   - 增量：将分类头替换为回归头，输出结合亲和力分数。
   - 初步方法：使用 SELEX 或 HT-SELEX 数据构建连续标签；在本文框架上训练回归模型。
   - 验证方式：Pearson/Spearman 相关系数；与现有亲和力预测工具对比。
   - 创新状态：unverified