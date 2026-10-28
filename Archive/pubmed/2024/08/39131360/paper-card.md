## 01 基本信息
- **标题**：moPPIt: De Novo Generation of Motif-Specific Binders with Protein Language Models
- **作者**：Chen, Tong; Zhang, Yinuo; Chatterjee, Pranam
- **单位**：未提供（根据 NIH 基金号 R35GM155282 推测为美国研究机构，具体单位未在材料中提供）
- **期刊/平台**：bioRxiv（预印本服务器）
- **年份**：2024（预印本发布于 2024-07-31，PubMed 收录日期 2024-08-12）
- **论文类型**：预印本（方法学 + 计算验证）
- **领域**：蛋白质设计、蛋白质-肽相互作用预测、蛋白质语言模型
- **关键词**：motif-specific binder design、protein language models、peptide binder、binding site prediction、de novo design
- **DOI/arXiv 号**：10.1101/2024.07.31.606098
- **代码**：https://huggingface.co/ChatterjeeLab/moPPIt（需签署非商业学术许可）
- **数据**：训练数据来自 PPIRef、PepNN、BioLip2 数据库；基准测试蛋白及 PDB ID 见补充表格
- **阅读日期**：2025-01-15（示例）
- **在课题方向中的位置**：本文属于「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI 方法」方向的**相邻领域**——蛋白质-肽互作。其核心方法（BindEvaluator 结合位点预测 + PepMLM 肽生成 + 遗传算法优化）虽针对蛋白质-肽体系，但其「序列-only 的 motif 靶向」思路可直接迁移到 TF–DNA 结合 motif 的靶向设计问题。本文明确提及转录因子（如 EWS::FLI1 融合蛋白）作为目标，且其处理 intrinsically disordered regions（IDRs）的能力对 TF 的固有无序区域研究具有直接参考价值。

## 02 一句话总结
本文提出 moPPIt 算法，仅从目标蛋白序列出发，通过 BindEvaluator（基于 ESM-2 嵌入的 transformer 模型）预测结合位点，结合 PepMLM 肽生成器和遗传算法优化，生成靶向用户指定 motif 的肽段，并在 15 个已知结合肽的蛋白及多个无已知结合肽的结构化/无序蛋白上通过 AlphaFold2-Multimer 和 PeptiDeride 计算验证其结合能力与特异性。

## 03 研究问题
- **具体问题**：如何仅从目标蛋白的氨基酸序列出发，设计出能够特异性结合用户指定 motif（表位）的肽段，而无需依赖目标蛋白的三维结构信息？
- **为什么重要**：许多疾病相关蛋白（如病毒蛋白上的保守表位、转录因子中的固有无序区域、融合癌蛋白的断点连接处）缺乏稳定的三维结构或明确的结合口袋，传统结构-based 设计方法（如 RFDiffusion）难以适用。能够靶向特定 motif 的序列-only 方法将极大扩展可成药靶点的范围。
- **现有方法不足**：结构-based 方法（AlphaFold、RFDiffusion）依赖稳定的三级结构，对 intrinsically disordered proteins（IDPs）和 IDRs 不适用；现有 pLM-based 方法（如 PepMLM 本身）虽能生成结合肽，但未聚焦于「用户指定 motif」的特异性靶向。
- **精确研究问题**：Can a protein language model-based pipeline, trained on sequence pairs alone, generate peptide binders that specifically target user-defined motifs on both structured and disordered protein targets?

## 04 背景与发展脉络
> 注：以下脉络为「经外部核验」的领域发展概述，结合本文引用与领域常识。

1. **结构-based 蛋白设计时代**：AlphaFold [Jumper et al., 2021; Abramson et al., 2024] 实现高精度结构预测；RFDiffusion [Watson et al., 2023] 等扩散模型实现 motif-specific binder 设计。**优点**：高精度、可解释。**局限**：依赖稳定三维结构，对 IDPs/IDRs 失效，且计算成本高。
2. **序列-based 蛋白语言模型兴起**：ESM-2 [Lin et al., 2023]、ProtT5 [Elnaggar et al., 2022]、ESM3 [Hayes et al., 2024] 等在大规模序列上预训练，隐式编码结构-功能关系。**优点**：无需结构、可处理无序区域。**局限**：早期工作未聚焦 motif 特异性。
3. **pLM-based 肽段设计**：PepMLM [Chen et al., 2023b] 等利用 pLM 生成靶向特定蛋白的肽段。**优点**：序列-only、高效。**局限**：缺乏对「用户指定 motif」的精确控制。
4. **本文位置**：moPPIt 填补了「pLM-based 设计」与「motif 特异性」之间的空白，通过 BindEvaluator 提供结合位点预测的监督信号，引导 PepMLM 生成靶向指定 motif 的肽段。其创新在于将「结合位点预测」作为可微分的优化目标，而非仅依赖生成模型的隐式学习。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 结构-based 方法无法处理无序蛋白 | RFDiffusion 等对 IDPs/IDRs 无法生成可靠 binder | 训练数据为稳定结构，无序区域无明确构象 | 引言：IDPs "were not present in their training sets" |
| 现有 pLM-based 方法缺乏 motif 特异性 | PepMLM 等生成肽段但不保证靶向用户指定区域 | 生成过程无结合位点监督信号 | 引言："existing pLM-based methods have not yet focused on targeting specific motifs" |
| 结合位点预测精度不足 | 通用 PPI 结合位点预测器对肽-蛋白体系效果差 | 肽段结合模式与全长蛋白互作不同 | 作者训练 BindEvaluator 专门针对肽-蛋白体系（Results 节） |
| 缺乏序列-only 的 motif 靶向工具 | 无已知 binder 的蛋白难以设计特异性肽段 | 现有方法依赖已知 binder 或结构信息 | 作者在无已知 binder 的蛋白上测试（Results 节） |

## 06 核心思想
1. **表面方法**：三阶段流水线——(1) BindEvaluator 预测目标蛋白上肽段结合位点；(2) PepMLM 生成候选肽段；(3) 遗传算法迭代优化，以 BindEvaluator 预测的位点与用户指定 motif 的重叠度为惩罚项，同时考虑 PepMLM 困惑度。
2. **核心洞察**：将「结合位点预测」作为可微分的优化信号，使生成过程能够被引导至用户指定的 motif。BindEvaluator 的注意力机制天然关注局部 motif 特征（通过 dilated CNN 提取），使得「指定区域」与「预测结合位点」的对齐成为可优化的目标。
3. **可能的普适教训** [Analysis]：在生成任务中，与其依赖端到端的隐式学习，不如显式引入一个「可微分的评估器」作为优化信号。这种「生成器-评估器」的对抗/协同框架，可以迁移到其他生物分子设计任务（如 TF–DNA 结合 motif 的 DNA 适配体设计），其中评估器可以是 DNA 结合位点预测模型。

## 07 方法总览
- **输入**：目标蛋白氨基酸序列 + 用户指定的 motif 残基索引
- **输出**：靶向指定 motif 的肽段序列（可指定长度）
- **模块**：
  1. **BindEvaluator**：基于 ESM-2-650M 嵌入的 transformer，含 dilated CNN 模块，预测目标蛋白上每个残基是否为结合位点
  2. **PepMLM**：ESM-2-based 条件生成模型，生成靶向目标蛋白的肽段
  3. **遗传算法**：迭代优化肽段池，以 BindEvaluator 预测位点与指定 motif 的重叠度（惩罚分）+ PepMLM 困惑度为适应度
- **训练**：BindEvaluator 先在 PPIRef（510,804 个 PPI 三元组）上训练，再在 PepNN + BioLip2（12,273 个肽-蛋白对）上微调；ESM-2 权重固定
- **推理流程**：
  1. PepMLM 生成初始肽段池（50 个候选）
  2. BindEvaluator 预测每个候选肽段与目标蛋白的结合位点
  3. 计算惩罚分（指定 motif 中未被预测为结合位点的残基数 + 预测位点中不在 motif 内的残基数 × 0.5）
  4. 遗传算法（选择、交叉、变异）迭代优化，直至收敛
  5. 输出 top 肽段，用 AlphaFold2-Multimer 验证结合
- **验证工具**：AlphaFold2-Multimer（结构预测 + ipTM/pTM 评分）、PeptiDerive（Rosetta-based 残基能量贡献分析）
- **假设**：pLM 嵌入隐式编码了足够的结构信息，使得仅从序列即可预测结合位点；肽段结合模式可从 PPI 数据迁移学习

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| BindEvaluator（含 dilated CNN） | 预测目标蛋白上的肽段结合位点 | 提供 motif 特异性的监督信号，引导生成 | 输入：ESM-2 嵌入的 binder-target 序列对；输出：每个目标残基的结合概率 | Results 图 1B：测试 AUC > 0.94（PPI），微调后 > 0.96（肽-蛋白） | 预期影响 [Analysis]：移除后生成过程无方向性，退化为普通 PepMLM，无法保证 motif 特异性 |
| Dilated CNN 模块 | 提取局部序列特征 | 结合位点通常为连续短序列（≤23 残基），CNN 可高效捕获 | 输入：ESM-2 嵌入；输出：局部特征增强的嵌入 | Results 图 1B：含 CNN 版本性能更优 | 预期影响 [Analysis]：移除后可能降低对短 motif 的识别精度，但全局注意力仍可部分补偿 |
| PepMLM 生成器 | 生成候选肽段 | 提供初始候选池，利用 pLM 的序列-功能知识 | 输入：目标蛋白序列；输出：肽段序列 | 引用 [Chen et al., 2023b] | 预期影响 [Analysis]：移除后需从头采样，效率大幅降低 |
| 遗传算法优化 | 迭代改进肽段池 | 结合 BindEvaluator 的惩罚分和 PepMLM 困惑度，多目标优化 | 输入：初始肽段池 + 评估分数；输出：优化后肽段池 | Methods 节描述 | 预期影响 [Analysis]：移除后仅靠单轮生成，特异性可能不足 |
| AlphaFold2-Multimer 验证 | 计算结合结构置信度 | 提供 ipTM/pTM 作为结合能力的代理指标 | 输入：肽段-蛋白序列对；输出：ipTM/pTM 分数 | Results 表 S1-S3 | 实测消融：非 moPPIt 核心模块，但为验证必需 |

## 09 关键公式符号
1. **损失函数**（BindEvaluator 训练）：
   L(y, ŷ) = -Σᵢ[yᵢ log(ŷᵢ) + (1-yᵢ) log(1-ŷᵢ)] + λ Σᵢ yᵢ log(yᵢ/ŷᵢ)
   - yᵢ：真实结合标签（0/1）
   - ŷᵢ：预测结合概率
   - λ：平衡 BCE 和 KL 散度的超参数（训练时 0.1，微调时 1.0）

2. **互注意力机制**（BindEvaluator 核心）：
   Attention_target(Q, K, V_binder) = softmax(QKᵀ/√d_k) V_binder
   Attention_binder(Q, K, V_target) = softmax(KQᵀ/√d_k) V_target
   - Q、K、V：查询、键、值矩阵
   - d_k：模型维度

3. **困惑度**（PepMLM 评估）：
   PPL = exp(-(1/L) Σᵢ log P(aᵢ | T, a<ᵢ))
   - L：肽段长度
   - aᵢ：肽段第 i 个氨基酸
   - T：目标蛋白序列
   - a<ᵢ：肽段前 i-1 个氨基酸

4. **惩罚分**（遗传算法适应度）：
   penalty = Σ_{r∈motif} 1[r ∉ predicted_sites] + 0.5 × Σ_{r∈predicted_sites} 1[r ∉ motif]
   - 即：指定 motif 中未被预测为结合位点的残基每个 +1 分，预测位点中不在 motif 内的残基每个 +0.5 分

## 10 实验设计与证据链
**数据集与评测协议**：
- **BindEvaluator 训练**：PPIRef（510,804 个 PPI 三元组，含反向增强），60/20/20 划分
- **BindEvaluator 微调**：PepNN（3,022）+ BioLip2（9,251）肽-蛋白对，80/10/10 划分
- **基准测试 1**：15 个有已知结合肽的结构化蛋白（PDB 来源），比较 moPPIt 设计肽 vs 已知肽的 ipTM/pTM
- **基准测试 2**：3 个无已知结合肽的酶（CLK1、PPP5、MINDY1），评估结合位点特异性
- **基准测试 3**：3 个含 IDR 的蛋白（UCHL5、4E-BP2、EWS::FLI1），评估无序区域靶向能力
- **指标**：AUC、准确率、F1、MCC（BindEvaluator）；ipTM、pTM（AlphaFold2-Multimer）；相对界面分数 RIS（PeptiDerive）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| BindEvaluator PPI 训练测试 | 模型能预测 PPI 结合位点 | 含/不含 dilated CNN 对比 | AUC > 0.93，含 CNN 版本更优 | 架构有效，CNN 增强局部特征 | 未与 SOTA 位点预测器对比 | Results 图 1B |
| BindEvaluator 肽-蛋白微调 | 模型能泛化到肽段结合预测 | 微调前后对比 | AUC > 0.96 | 肽段结合模式可迁移学习 | 未报告精确率/召回率 | Results 图 1B |
| 15 个已知 binder 蛋白基准 | moPPIt 设计肽与已知肽相当 | moPPIt 肽 vs 已知肽的 ipTM/pTM | 14/15 达到或超过已知肽的 ipTM 阈值 | moPPIt 能生成高置信结合肽 | 未做湿实验验证 | Results 表 S1 |
| 3 个无 binder 酶基准 | moPPIt 能靶向新蛋白 | 无对比，仅评估位点特异性 | 高 RIS 残基位于指定 motif | 能设计无已知 binder 蛋白的肽 | 样本量小（n=3） | Results 图 4、表 S2 |
| 3 个 IDR 蛋白基准 | moPPIt 能处理无序区域 | 无对比，仅评估结合置信度 | 高 ipTM 分数 | pLM 方法可靶向 IDR | AlphaFold2 对 IDR 预测可靠性存疑 | Results 表 S3 |

## 11 结论正确解读
- **任务范围**：本文是**计算验证**，无任何湿实验（体外/体内结合实验）。所有结论基于 AlphaFold2-Multimer 的 ipTM/pTM 和 PeptiDerive 的 RIS 预测。
- **oracle/真值输入**：基准测试 1 使用已知肽-蛋白复合物作为「真值」参考；基准测试 2/3 无真值，仅依赖计算指标。
- **端到端状态**：moPPIt 是端到端的序列输入→肽段输出流水线，但验证环节依赖第三方结构预测工具。
- **算力成本**：BindEvaluator 训练需 6×A6000 GPU（48GB VRAM），30 epochs；推理成本未报告。
- **历史数据依赖**：BindEvaluator 训练数据来自 PPIRef（PPI 数据库），微调数据来自 PepNN/BioLip2（肽-蛋白数据库），存在数据库偏差风险。
- **模型依赖**：强依赖 ESM-2-650M 的嵌入质量；AlphaFold2-Multimer 对肽段-蛋白复合物的预测可靠性是验证链的关键假设。
- **最难情形**：IDR 靶向（作者承认 AlphaFold2 对无序区域预测可能不可靠）；无已知 binder 的新靶点（缺乏真值验证）。
- **有边界的复述**：moPPIt 在计算层面展示了从序列生成 motif 特异性肽段的能力，其有效性限于计算指标（ipTM/pTM/RIS），未经实验验证；对 IDR 靶点的结论尤其需要谨慎。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| 缺乏实验验证 | 所有结论基于计算预测 | "our next steps will include a comprehensive experimental validation" | Discussion 节 |
| IDR 验证可靠性 | AlphaFold2-Multimer 和 PeptiDerive 对无序区域可能不可靠 | 未明确提及，但暗示需要实验确认 | Results 表 S3 讨论 |
| 训练数据偏差 | 训练数据来自已知结构/结合数据库 | 未明确提及 | 未提供 |
| 泛化性未验证 | 仅在有限蛋白集上测试 | 计划与 RFDiffusion 等结构方法对比 | Discussion 节 |

**作者提及的相关约束**（非正式局限）：
- 蛋白质长度限制（>500 aa 被移除）
- 肽段长度限制（>25 aa 被移除）
- 训练数据中 IDR 代表性不足

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 验证完全依赖 AlphaFold2-Multimer | AF2 对肽段-蛋白复合物的预测可能系统性高估结合（训练数据偏差）；ipTM 高并不等于真实结合 | 计算验证的结论可能无法转化为实验成功 | 对部分设计肽做 SPR/ITC 结合实验；或与已知阴性肽对比 | Methods 节：验证工具仅 AF2 + PeptiDerive |
| 基准测试 1 的「已知 binder」可能被 AF2 训练数据覆盖 | 若测试蛋白在 AF2 训练集中，ipTM 高可能是记忆而非泛化 | 高估 moPPIt 的泛化能力 | 检查测试蛋白是否在 AF2 训练集；用新解析结构测试 | Results 表 S1：15 个 PDB 蛋白 |
| 惩罚分设计偏向「覆盖 motif」而非「排除 off-target」 | 惩罚分只惩罚「motif 未被覆盖」和「预测位点偏离 motif」，未显式惩罚「结合到其他区域」 | 可能生成多特异性 binder | 检查设计肽在目标蛋白全序列上的预测结合谱 | Methods 节：penalty score 定义 |
| 遗传算法收敛标准未报告 | 无法判断优化是否充分；可能过早停止 | 影响生成肽质量的可重复性 | 报告收敛曲线和迭代次数 | Methods 节：仅描述终止条件 |
| 与结构方法（RFDiffusion）无直接对比 | 无法判断 pLM 方法相对结构方法的优劣 | 方法选择缺乏依据 | 在相同测试集上对比 moPPIt vs RFDiffusion | Discussion 节：仅提及未来计划 |
| IDR 靶向的「成功」标准模糊 | 对 IDR 靶点，AF2 可能预测出「假阳性复合物」；高 ipTM 不等于真实结合 | IDR 结论可能过度乐观 | 用实验方法（NMR/CLMS）验证 IDR 结合 | Results 表 S3 |

## 14 Agent 提炼的知识候选
> 面向「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI/深度学习/物理模拟」课题的可迁移知识：

1. **「生成器-评估器」协同框架**：moPPIt 的核心架构（生成器 + 可微评估器 + 遗传优化）可直接迁移到 TF–DNA 结合 motif 的 DNA 适配体/调控序列设计。具体而言：用类似 BindEvaluator 的模型预测 TF 的 DNA 结合位点，用 DNA 语言模型（如 Nucleotide Transformer）生成候选序列，以「预测结合位点与目标 motif 重叠度」为优化目标。
2. **Dilated CNN 用于局部 motif 特征提取**：TF–DNA 结合 motif 通常为 6-12 bp 的连续序列，与肽段结合位点（≤23 残基）类似。BindEvaluator 中 dilated CNN 提取局部特征的设计可直接用于 DNA 结合位点预测模型。
3. **互注意力机制用于双序列交互建模**：BindEvaluator 的 reciprocal attention（binder 和 target 互为 Q/K）可迁移到 TF–DNA 对建模，用于预测 TF 对特定 DNA 序列的结合偏好。
4. **序列-only 方法对 IDR 的适用性**：许多 TF 的 DNA 结合域（DBD）具有部分无序性，moPPIt 证明 pLM 嵌入可处理无序区域，这为「无序 TF 的 DNA 结合特异性预测」提供了方法学依据。
5. **惩罚分设计中的「特异性-覆盖度」权衡**：moPPIt 的惩罚分（motif 未覆盖 +1，偏离 motif +0.5）提供了一种可调的「特异性 vs 覆盖度」平衡机制，可迁移到 TF–DNA 结合位点预测的损失函数设计。
6. **计算验证链的局限性警示**：moPPIt 的验证完全依赖 AF2 等计算工具，这对 TF–DNA 体系同样适用——计算预测的「结合」必须经过实验验证（EMSA、ChIP-seq、SELEX 等）才能确认。

## 15 与已有知识连接
- **相似方法**：与 PepNN [Abdin et al., 2022] 和 Pseq2Sites [Seo et al., 2023] 架构相似，均使用 pLM 嵌入 + 注意力机制预测结合位点。在 TF–DNA 领域，类似思路见于 DeepBind [Alipanahi et al., 2015]、DeepSEA [Zhou & Troyanskaya, 2015] 等基于序列的 DNA 结合预测模型。
- **组合方向**：moPPIt 的「pLM + 遗传算法」组合可类比于 TF–DNA 设计中的「生成模型 + 进化优化」策略，如用扩散模型生成 DNA 序列后用结合预测模型筛选。
- **冲突/差异**：与 RFDiffusion 等结构方法形成对比——moPPIt 完全不需要结构信息，这对无结构 TF 的 DNA 结合设计具有独特优势，但也意味着无法利用空间约束。
- **可迁移领域**：moPPIt 的「motif 靶向」概念可直接映射到 TF 的 DNA 结合 motif（如锌指蛋白的 DNA 识别螺旋、homeodomain 的 recognition helix），其「指定残基/碱基」的靶向逻辑在 TF–DNA 体系中对应「指定 DNA 接触碱基」。
- **理论支撑**：pLM（ESM-2）嵌入隐式编码结构-功能关系的观点，与蛋白质语言模型在功能预测中的广泛应用一致 [Lin et al., 2023; Rives et al., 2021]。
- **候选延伸**：将 BindEvaluator 的架构改造为「TF–DNA 结合位点预测器」，输入 TF 序列 + DNA 序列，输出 DNA 上的结合碱基——这是本文方法向 TF–DNA 课题最直接的迁移路径。

## 16 Agent 生成的研究候选
> 以下为基于本文方法、面向「TF–DNA 结合机制 × AI」课题的研究方向提案：

1. **候选名称**：TF-DNA-BindEvaluator：基于 pLM 的转录因子-DNA 结合位点预测与 motif 靶向适配体设计
   - **来源局限/观察**：moPPIt 针对蛋白质-肽体系，但 TF–DNA 结合具有类似的「短 motif 识别」特征；现有 TF–DNA 预测模型（DeepBind 等）多为 CNN 架构，未充分利用 pLM 嵌入
   - **核心假设**：ESM-2 嵌入 + 互注意力机制可有效预测 TF 对 DNA 序列的结合位点，且优于纯 CNN 方法
   - **增量**：将 BindEvaluator 的架构迁移到 DNA 结合预测，输入改为 TF 序列 + DNA 序列，输出 DNA 结合碱基
   - **初步方法**：用 CIS-BP、JASPAR 等数据库训练，对比 DeepBind/DeepSEA 基线
   - **验证方式**：ChIP-seq 数据验证、SELEX 实验
   - **创新状态**：unverified

2. **候选名称**：MoPPIt-DNA：遗传算法优化的 TF 结合 DNA 适配体设计
   - **来源局限/观察**：moPPIt 的「生成器-评估器-遗传优化」框架可迁移到 DNA 适配体设计，但 DNA 语言模型（如 Nucleotide Transformer）与蛋白质语言模型在嵌入空间上存在差异
   - **核心假设**：以 DNA 语言模型为生成器、TF–DNA 结合预测器为评估器，遗传算法可设计出靶向特定 TF 的 DNA 适配体
   - **增量**：首次将 moPPIt 框架应用于 DNA 体系；处理 DNA 的「反向互补」对称性问题
   - **初步方法**：用 Nucleotide Transformer 生成候选 DNA，用 TF-DNA-BindEvaluator 评估，遗传算法优化
   - **验证方式**：EMSA、表面等离子共振（SPR）
   - **创新状态**：unverified

3. **候选名称**：IDR-TF-Binder：靶向无序转录因子区域的肽段设计
   - **来源局限/观察**：moPPIt 展示了 pLM 方法对 IDR 靶点的适用性；许多 TF（如 p53、MYC）的调控区域具有无序性，是药物设计的难点
   - **核心假设**：moPPIt 可直接用于设计靶向无序 TF 区域的肽段，且比结构方法更有效
   - **增量**：将 moPPIt 应用于 TF 靶点（如 EWS::FLI1 融合断点、p53 的 N 端无序区）
   - **初步方法**：选择 3-5 个无序 TF 区域，用 moPPIt 设计肽段，AF2 验证
   - **验证方式**：NMR 或交联质谱验证结合
   - **创新状态**：unverified

4. **候选名称**：Mutant-Specific TF Binder：靶向 TF 点突变位点的选择性肽段设计
   - **来源局限/观察**：moPPIt 的「指定 motif」能力可用于靶向 TF 的突变位点（如癌症相关点突变），实现突变选择性结合
   - **核心假设**：moPPIt 能设计出区分野生型与突变型 TF 的肽段
   - **增量**：将 moPPIt 的 motif 指定从「连续区域」扩展到「包含突变位点的局部区域」
   - **初步方法**：选择已知癌症相关 TF 突变（如 TP53 R175H），用 moPPIt 设计肽段，比较对 WT/突变体的结合预测
   - **验证方式**：等温滴定量热法（ITC）
   - **创新状态**：unverified