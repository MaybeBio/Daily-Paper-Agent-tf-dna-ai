## 01 基本信息

- **标题**：ODesign: A World Model for Biomolecular Interaction Design
- **作者与单位**：Odin Zhang 等（Lingang Laboratory, Shanghai Jiao Tong University, Zhejiang University, The Chinese University of Hong Kong, Shanghai Artificial Intelligence Laboratory, McGill University, MIT, Harvard University, University of Washington 等）
- **期刊/预印本平台**：arXiv 预印本
- **年份**：2025
- **论文类型**：方法学（生成式基础模型）
- **领域**：AI for Science；生物分子相互作用设计；生成式建模
- **关键词**：world model, biomolecular interaction design, all-to-all generation, diffusion model, inverse folding, protein binder design, aptamer design, small molecule design
- **DOI/arXiv 号**：arXiv:2510.22304v2
- **代码**：未提供（提供在线服务 https://odesign.lglab.ac.cn）
- **数据**：RCSB PDB（X-ray 晶体结构，2021-09-30 前发布）+ AlphaFold2/OpenFold 蒸馏数据集
- **阅读日期**：2026-05-13
- **在本课题方向中的位置**：本文提出一个统一的、基于 AlphaFold3 架构的全原子生成式世界模型，支持跨模态（蛋白质、核酸、小分子）的"all-to-all"相互作用设计。对于 TF–DNA 结合机制研究，本文提供了：(1) 将结构预测模型（AF3）的预训练权重迁移到生成任务的范式；(2) 统一的 token 化方案（将蛋白质残基、核酸核苷酸、小分子原子统一为生成单元）；(3) 表位/热点残基条件化生成机制，可直接迁移到 TF–DNA 结合界面设计；(4) 蛋白质结合 DNA/RNA 的零样本设计能力，为 TF–DNA 复合物设计提供了直接工具。

---

## 02 一句话总结

ODesign 基于 AlphaFold3 架构，将蛋白质、核酸和小分子的化学单元统一为生成 token，通过两阶段（骨架扩散生成 + 序列逆折叠）策略，在单一框架内实现跨模态的"all-to-all"生物分子相互作用设计，在蛋白质-蛋白质、蛋白质-配体、蛋白质-核酸、核酸-配体等任务上超越或匹敌模态专用模型，并实现 2–4 个数量级的吞吐量提升。

---

## 03 研究问题

- **具体问题**：现有生成模型（如 RFdiffusion、ResGen、RhoDesign）均为模态专用，无法在单一框架内实现跨模态（蛋白质、核酸、小分子）的相互作用设计，且缺乏对相互作用界面的细粒度控制（如指定表位/热点残基）。
- **为什么重要**：生物功能由多模态分子协同实现（信号转导、基因调控、代谢等），跨模态设计能力是编程新生物功能的前提。对于 TF–DNA 互作研究，能够同时设计蛋白质（TF）和核酸（DNA）及其结合界面，是设计人工转录因子和基因调控元件的关键。
- **现有方法为何不足**：(1) 模态专用模型无法处理跨模态相互作用；(2) 结构预测模型（AF3）只做预测不做生成；(3) 现有生成模型缺乏多粒度控制（分子、基序、原子级）；(4) 生成吞吐量低，难以满足高通量筛选需求。
- **精确研究问题**：Can a single generative framework, built upon structure prediction architectures, achieve all-to-all biomolecular interaction design across proteins, nucleic acids, and small molecules with fine-grained control and high throughput?

---

## 04 背景与发展脉络

*注：以下脉络基于本文框架整理，标注「仅本文框架」或「经外部核验」。*

1. **阶段一：模态专用生成模型**（经外部核验）
   - 蛋白质：RFDiffusion（扩散模型）、Proteina、FrameFlow、Genie2、Chroma
   - 蛋白质-小分子：ResGen、TargetDiff、Pocket2Mol、SurfGen、D3FG
   - RNA：RhoDesign、gRNAde、RNAFrameFlow
   - 局限：各自为政，无法跨模态；缺乏统一的条件控制机制

2. **阶段二：结构预测作为预训练**（仅本文框架）
   - AlphaFold3 实现了蛋白质、核酸、小分子、修饰的统一表示
   - 本文主张：结构预测模型隐式学习了跨模态相互作用的基本物理化学原理，可作为生成模型的预训练基础
   - 关键假设：预测任务学到的表征可迁移到生成任务

3. **阶段三：统一生成式世界模型**（本文位置）
   - ODesign：将 AF3 架构改造为生成模型，通过掩码策略实现多粒度条件控制
   - 核心创新：统一 token 空间 + 任务导向掩码 + 两阶段生成（骨架→序列）
   - 覆盖任务：蛋白质单体生成、蛋白质-蛋白质结合子设计、蛋白质-配体结合蛋白设计、基序支架、RNA 单体生成、蛋白质结合 RNA/DNA 适配体设计、DNA/RNA 结合小分子设计

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 模态隔离 | 蛋白质、核酸、小分子各有专用模型，无法统一设计 | 不同模态的化学组成和结构规律差异大，现有模型各自为政 | Introduction 第 2-3 段 |
| 缺乏细粒度控制 | 现有模型只能控制实体级（如"设计一个结合蛋白"），无法控制基序级或原子级 | 生成单元粒度过粗，缺乏统一的 token 化方案 | Introduction 第 3 段；Appendix A 掩码策略 |
| 吞吐量瓶颈 | 单 GPU 单日仅能生成少量候选分子，不足以填满 96 孔板 | 扩散模型迭代步数多，且需要多次采样 | Results 图 2a；Appendix C 吞吐量计算 |
| 跨模态泛化缺失 | 无法处理"蛋白质结合 RNA"、"DNA 结合小分子"等跨模态任务 | 训练数据和模型架构均局限于单一模态 | Introduction 第 2 段；Results 图 3c-d |
| 表位/热点指定困难 | 设计结合子时无法指定目标上的特定结合位点 | 缺乏热点残基编码机制 | Appendix A 表 S1（is_hotspot 特征） |
| 数据稀疏（核酸模态） | RNA/DNA 结构数据远少于蛋白质，模型性能下降 | 训练数据中核酸结构占比低 | Results 图 3a-b；作者在 DNA 适配体设计中的性能下降讨论 |

---

## 06 核心思想

### 1) 表面方法
- 基于 AlphaFold3 架构，将蛋白质、核酸、小分子统一为 token 序列
- 两阶段生成：先通过条件扩散模型生成骨架坐标，再通过逆折叠模块（OInvFold）分配序列
- 四种掩码粒度（All/Entity/Token/Atom）实现多层级条件控制
- 在 PDB + AF2/OpenFold 蒸馏数据上训练，继承 AF3 预训练权重

### 2) 核心洞察
- **结构预测作为生成预训练**：AF3 在预测任务中学到的跨模态相互作用知识可直接迁移到生成任务，无需从零训练
- **统一 token 空间**：将不同模态的化学单元（氨基酸残基、核苷酸、原子）统一为生成 token，使跨模态设计成为可能
- **任务导向掩码**：通过不同粒度的掩码策略，将"设计"任务转化为"条件补全"任务，实现从实体级到原子级的连续控制
- **两阶段解耦**：骨架生成与序列设计分离，降低任务复杂度，同时允许分别优化

### 3) 可能的普适教训 [Analysis]
- 对于 TF–DNA 互作研究：结构预测模型（如 AF3）的预训练权重是生成模型的优质初始化，这一范式可迁移到 TF–DNA 结合界面设计
- 统一 token 化是跨模态建模的关键：将不同化学实体映射到同一表示空间，使模型能够学习跨模态的相互作用规律
- 掩码策略提供了一种灵活的条件控制机制：从"设计整个结合子"到"仅设计特定原子"的连续控制，适用于不同精度的设计需求

---

## 07 方法总览

- **输入**：JSON 格式任务描述，包含参考结构文件（.pdb/.cif）、条件链信息（序列、长度、MSA）、热点残基/原子指定、设计链长度范围等
- **输出**：全原子三维结构（骨架坐标 + 序列），支持蛋白质、核酸、小分子三种模态
- **核心模块**：
  1. **Embedding 模块**：初始元素表示，融合序列、结构、MSA 特征；新增 is_hotspot 和 is_masked 特征
  2. **条件模块**：编码目标的三维结构，通过距离约束（distogram）注入结构信息
  3. **Pairformer 模块**：48 层，三角乘法更新 + 三角注意力，建模 token 间相互作用
  4. **条件扩散模块**：EDM 调度，从噪声中解码全原子坐标
  5. **OInvFold 模块**：统一逆折叠，为生成的骨架分配序列（蛋白质/核酸的残基类型、小分子的原子类型）
- **训练**：PDB（2021-09-30 前）+ AF2/OpenFold 蒸馏数据；掩码策略按任务类型采样（All/Entity/Token/Atom 四种粒度）；损失函数包含 distogram、MSE、bond、smooth-LDDT、reconstruction 五个分量
- **推理**：支持刚性/柔性目标模式；四种初始化方法（热点中心、全局中心、用户指定中心、用户指定残基中心）；支持部分扩散（partial diffusion）用于优化已有结合子
- **反馈回路**：生成 → AF3/Chai-1 结构预测验证 → 过滤 → 输出候选

**文字流程**：
1. 解析 JSON 任务描述，确定条件链、设计链、热点残基
2. 构建统一 token 序列，嵌入序列/结构/MSA 特征
3. 通过条件模块注入目标三维结构信息（distogram）
4. Pairformer 迭代更新 token 表示，建模分子间相互作用
5. 条件扩散模块从噪声中生成设计链的骨架坐标
6. OInvFold 模块为骨架分配序列（残基类型或原子类型）
7. 输出候选结构，供下游 AF3/Chai-1 验证

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| Embedding 模块 | 将不同模态的化学单元映射到统一表示空间 | 跨模态统一表示的基础 | 输入：token 序列、结构坐标、MSA；输出：初始嵌入 | Appendix A 表 S1 | 预期：跨模态设计能力丧失 [预期效应] |
| 条件模块（距离约束） | 将目标三维结构信息注入生成过程 | 使生成的结构与目标形成正确相互作用 | 输入：目标结构坐标；输出：distogram 特征 | Appendix A 算法 S10 | 预期：生成结构无法与目标形成正确界面 [预期效应] |
| Pairformer 模块 | 建模 token 间（分子内和分子间）相互作用 | 捕获跨模态相互作用的基本物理化学规律 | 输入：嵌入特征；输出：更新后的 token 表示 | Appendix A 算法 S11；Results 图 2 | 预期：生成结构质量显著下降 [预期效应] |
| 条件扩散模块 | 从噪声中生成全原子坐标 | 实现三维结构生成 | 输入：噪声坐标 + Pairformer 条件；输出：去噪后的坐标 | Appendix A 算法 S12；Results 图 2 | 预期：无法生成有效结构 [预期效应] |
| OInvFold 模块 | 为生成的骨架分配序列 | 完成从结构到序列的映射 | 输入：骨架坐标 + Pairformer 特征；输出：残基/原子类型 | Results 图 2；Appendix A | 预期：序列设计质量下降 [预期效应] |
| 掩码策略（All/Entity/Token/Atom） | 控制生成任务的粒度和范围 | 实现从实体级到原子级的连续控制 | 输入：任务类型；输出：掩码矩阵 | Appendix A 算法 S2-S5 | 预期：丧失多粒度控制能力 [预期效应] |
| 部分扩散（partial diffusion） | 在现有结合子基础上进行局部优化 | 支持对已有分子的改造和优化 | 输入：现有结构 + 噪声水平；输出：优化后的结构 | Appendix B | 预期：无法进行结合子优化 [预期效应] |

---

## 09 关键公式符号

**1. 损失函数（Appendix A）**：
L = L_distogram + L_MSE + L_bond + L_smooth_lddt + L_reconstruction

- L_distogram：token 间距离分布预测与真实值的交叉熵
- L_MSE：预测坐标与真实坐标的均方误差
- L_bond：键长预测的 RMSE
- L_smooth_lddt：局部距离差异测试（LDDT）损失
- L_reconstruction：配体键重建的交叉熵

**2. 吞吐量计算（Appendix C, 公式 4）**：
N_pass = (24 × 3600) / (T_sample + T_refold)

- N_pass：24 小时内通过过滤的候选数
- T_sample：单次采样时间
- T_refold：单次重折叠验证时间

**3. 部分扩散噪声添加（Appendix B）**：
x_t = √(1-σ²) · x₀ + σ · ε, ε ~ N(0, I)

- x₀：原始结构坐标
- σ：噪声水平，由 SNR(t) 决定
- x_t：加噪后的坐标

**4. SNR 定义（Appendix B）**：
SNR(t) = 1/σ²(t)

- 用于控制部分扩散中噪声的添加量

---

## 10 实验设计与证据链

**数据集**：
- 训练：PDB 全部单体/复合物结构（2021-09-30 前）+ AF2/OpenFold 蒸馏数据
- 蛋白质-蛋白质：CaoData 11 个靶标（EGFR、CD3d 等）
- 蛋白质-配体：RFDiffusion-AA 的 4 个配体（IAI、OQO、FAD、SAM）
- 基序支架：MotifBench 30 个靶标
- RNA 单体：与 RNAFrameFlow 对比
- 蛋白质结合 RNA/DNA：10 个蛋白质-RNA 复合物、4 个蛋白质-DNA 复合物（2023-01-13 后发布）
- DNA/RNA 结合小分子：3 个 DNA-配体、3 个 RNA-配体复合物（2023-01-13 后发布）

**指标**：
- 蛋白质-蛋白质：iPAE < 10.85, ipTM > 0.5, pLDDT > 80, complex RMSD < 2.5Å
- 蛋白质-配体：iPAE < 10, pLDDT > 70
- 基序支架：基序 RMSD < 1.0Å, 整体 RMSD < 2.0Å
- RNA/DNA 单体：RMSD < 5Å 或 TM-score > 0.45
- 蛋白质结合核酸：Cα 对齐的磷酸原子 RMSD < 5Å
- 小分子设计：AF3 预测的 iPAE、iPTM、配体 PTM、RMSD

**基线**：
- 蛋白质-蛋白质：RFDiffusion、BoltzDesign1、BindCraft
- 蛋白质-配体：RFDiffusion-AA、BoltzDesign1
- 基序支架：RFDiffusion、RFDiffusion-AA、Proteina
- RNA 单体：RNAFrameFlow
- 小分子设计：TargetDiff、D3FG、Pocket2Mol、SurfGen、ResGen

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 蛋白质-蛋白质结合子设计 | ODesign 在实体级设计任务上优于专用模型 | 11 靶标，800 候选/靶标，24h 吞吐量 | ODesign 平均 2672 通过，RFDiffusion 555，BindCraft 22，BoltzDesign1 61 | ODesign 吞吐量超专用模型 1-2 个数量级 | 未报告结合亲和力的实验验证 | Results 图 2a |
| 蛋白质-配体结合蛋白设计 | ODesign 在配体结合蛋白设计上优于专用模型 | 4 配体，800 候选/配体 | ODesign 12.1 倍于 RFDiffusion-AA，57.8 倍于 BoltzDesign1 | ODesign 在配体结合蛋白设计上显著领先 | 未报告实验验证的结合亲和力 | Results 图 2b |
| 基序支架 | ODesign 在基序支架任务上达到最优 | MotifBench 30 靶标 | ODesign 成功率 18.4%，RFDiffusion-AA 14.3% | ODesign 在基序支架上优于最强基线 | 未报告多样性/新颖性指标的详细对比 | Results 图 2c |
| RNA 单体生成 | ODesign 在 RNA 单体生成上匹敌 RNA 专用模型 | 长度 10-150 nt | ODesign 成功率约为 RNAFrameFlow 的 2 倍 | ODesign 在 RNA 生成上不弱于专用模型 | 未报告 RNA 功能验证 | Results 图 3a |
| 蛋白质结合 RNA 适配体设计 | ODesign 能零样本设计蛋白质结合 RNA | 10 个蛋白质-RNA 复合物 | 77.95% 成功率（Cα 对齐磷酸 RMSD < 5Å） | ODesign 具备跨模态（蛋白质→RNA）设计能力 | 未报告实验验证的 RNA 适配体功能 | Results 图 3c |
| 蛋白质结合 DNA 适配体设计 | ODesign 能零样本设计蛋白质结合 DNA | 4 个蛋白质-DNA 复合物 | 报告了成功案例 | ODesign 具备蛋白质→DNA 设计能力 | 样本量小，未报告统计显著性 | Results 图 3d |
| DNA 单体生成 | ODesign 能生成 DNA 骨架 | 长度 10-150 nt | 报告了成功率随长度变化 | ODesign 具备 DNA 生成能力 | 未与 DNA 专用模型对比 | Results 图 3b |
| DNA/RNA 结合小分子设计 | ODesign 能设计结合核酸的小分子 | 3 DNA-配体、3 RNA-配体复合物 | AF3 预测 iPAE 低、iPTM 高 | ODesign 具备核酸→小分子设计能力 | 未报告化学合成或实验验证 | Results 图 4b-c |
| 全局 vs 部分对齐 | 部分对齐策略优于全局对齐 | 预训练 checkpoint 上对比 | 全局对齐损失更低 | 全局对齐在预训练场景更优 | 未报告生成任务上的对比 | Appendix A 图 S1 |
| 消融：掩码策略 | 不同掩码粒度影响生成质量 | 各任务类型 | 未提供详细消融数据 | 掩码策略设计合理 | 未提供消融实验的定量结果 | Appendix A 表 S3 |

---

## 11 结论正确解读

- **任务范围**：本文覆盖蛋白质单体、蛋白质-蛋白质、蛋白质-配体、基序支架、RNA 单体、蛋白质结合 RNA/DNA、DNA/RNA 结合小分子共 7 类设计任务。**不包含**：TF–DNA 特异性结合机制分析、结合亲和力预测、突变效应预测。
- **Oracle/真值输入**：所有评估均使用 AF3/Chai-1 结构预测作为"真值"代理，**没有湿实验验证**。这意味着"成功"定义的是"可被结构预测模型折叠/识别"，而非"具有生物学功能"。
- **端到端状态**：ODesign 是生成模型，输出候选结构；下游验证（AF3/Chai-1）是独立步骤，**不是端到端训练**。
- **算力成本**：训练使用大规模 GPU 集群（8×H100 用于推理基准测试），具体训练算力未披露。
- **历史数据依赖**：训练数据为 PDB 中 2021-09-30 前发布的结构 + AF2/OpenFold 蒸馏数据。**测试集**（2023-01-13 后发布）与训练集无重叠，但蒸馏数据可能引入偏差。
- **模型依赖**：性能高度依赖 AF3 架构和预训练权重。若 AF3 的预测偏差存在，ODesign 的生成结果也会继承该偏差。
- **最难情形**：DNA 适配体设计（性能随长度下降最快）、RNA 小分子设计（数据最稀疏）。
- **群体/领域边界**：结果适用于 PDB 中已观测到的分子类型和相互作用模式；对于新型化学修饰、非天然氨基酸、非常规核酸结构等，泛化能力未知。
- **不确定性**：未报告生成结果的置信区间、多样性度量或失败案例分析。

**有边界的复述**：ODesign 是一个基于 AF3 架构的统一生成模型，在计算模拟层面（以 AF3/Chai-1 为评估器）实现了跨模态的"all-to-all"生物分子相互作用设计，在吞吐量上显著优于现有专用模型，但其生物学功能未经实验验证，且对 TF–DNA 特异性结合机制的建模能力尚未被专门评估。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 核酸模态数据稀疏 | DNA 适配体设计性能随长度下降最快；RNA 数据量不足 | 未明确提及 | Results 图 3b；Appendix A 训练数据描述 |
| 缺乏细粒度语义控制 | 无法控制蛋白质二级结构组成、小分子芳香性等属性 | 引入更丰富的条件控制机制 | Conclusion 段 |
| 部分扩散策略未充分探索 | 仅初步验证了部分扩散在配体优化中的应用 | 进一步探索部分扩散在更广泛任务中的应用 | Appendix B |
| 全局对齐 vs 部分对齐的权衡 | 全局对齐在预训练中更优，但部分对齐在生成中可能更优 | 未明确提及 | Appendix A 图 S1 |
| 蒸馏数据偏差 | AF2/OpenFold 蒸馏数据可能引入预测模型的系统性偏差 | 未明确提及 | Appendix A 训练数据描述 |
| 未进行湿实验验证 | 所有评估基于计算模拟 | 与实验团队合作验证设计分子 | Conclusion 段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 评估完全依赖 AF3/Chai-1 作为真值 | AF3 的预测偏差会被 ODesign 继承；"成功"可能只是"AF3 认为成功" | 生成模型的质量上限受限于评估器的质量 | 使用多种结构预测模型交叉验证；对部分设计进行湿实验验证 | Results 各节评估协议 |
| 吞吐量比较可能不公平 | ODesign 使用 AF3 架构和预训练权重，而 RFdiffusion 等从零训练；计算资源投入不同 | 吞吐量优势可能部分来自架构和预训练而非方法本身 | 控制计算资源后重新比较；报告训练成本 | Results 图 2a-b |
| 未报告生成结构的多样性 | 高吞吐量可能以牺牲多样性为代价 | 多样性是设计筛选的关键指标 | 计算生成结构的 pairwise RMSD 分布、聚类数 | Results 各节 |
| 未报告失败案例分析 | 无法了解模型在哪些情况下失效 | 失败模式分析对实际应用至关重要 | 系统分析未通过过滤的生成结构特征 | 未提供 |
| 蒸馏数据可能引入循环偏差 | 训练数据包含 AF2/OpenFold 预测结构，评估又用 AF3/Chai-1，可能形成"自我验证"循环 | 模型可能只是学会了"欺骗"结构预测器 | 使用实验解析结构（非预测）作为评估集 | Appendix A 训练数据描述 |
| 未与 AlphaProteo 等最新方法直接比较 | 文中提到 AlphaProteo 的评估标准，但未将其作为基线 | 无法判断 ODesign 是否代表当前最优 | 在相同评估协议下与 AlphaProteo 等比较 | Results 图 2a |
| 对 TF–DNA 特异性结合机制的建模能力未评估 | 本文未专门测试 TF–DNA 结合界面设计或序列特异性 | 对课题方向（TF–DNA 互作）的直接适用性未知 | 设计 TF–DNA 结合界面实验，评估序列特异性恢复 | 全文未涉及 |
| 小分子生成的质量评估不足 | 仅报告了 AF3 预测的 iPAE/iPTM，未报告化学有效性、合成可及性 | 化学有效性是药物设计的基本要求 | 使用 RDKit 计算化学有效性、SA score 等 | Results 图 4 |

---

## 14 学到什么

**Agent 提炼的知识候选**

1. **结构预测权重 → 生成模型迁移**：将 AF3 这类结构预测模型的预训练权重作为生成模型的初始化，可显著加速收敛并提升性能。迁移到 TF–DNA 课题：可尝试将 AF3 权重迁移到 TF–DNA 结合界面生成模型，利用其已学习的蛋白质-核酸相互作用知识。

2. **统一 token 空间设计**：将蛋白质残基、核苷酸、小分子原子统一为生成 token，配合模态特定后缀（-P/-N/-L），实现跨模态生成。迁移到 TF–DNA 课题：可设计统一的 TF–DNA 联合 token 空间，同时生成 TF 序列和 DNA 结合位点。

3. **任务导向掩码策略**：通过不同粒度的掩码（All/Entity/Token/Atom），将设计任务转化为条件补全任务，实现从实体级到原子级的连续控制。迁移到 TF–DNA 课题：可用 Token 级掩码设计 TF 的特定 DNA 结合结构域（如锌指、亮氨酸拉链），用 Atom 级掩码设计关键接触残基。

4. **两阶段生成范式**：先扩散生成骨架，再逆折叠分配序列，降低任务复杂度。迁移到 TF–DNA 课题：可先生成 TF–DNA 复合物骨架，再分别设计 TF 序列和 DNA 序列，避免联合优化的复杂性。

5. **表位/热点残基条件化**：通过 is_hotspot 特征指定目标上的关键结合残基，引导生成。迁移到 TF–DNA 课题：可指定 DNA 上的关键碱基或 TF 上的关键残基作为热点，实现结合界面定向设计。

6. **吞吐量作为评估指标**：将"单 GPU 24 小时有效设计数"作为核心指标，强调实际可用性。迁移到 TF–DNA 课题：在评估 TF–DNA 设计方法时，应同时报告吞吐量，而非仅报告成功率。

7. **零样本泛化评估**：使用训练集时间截点之后发布的 PDB 结构作为测试集，评估零样本泛化能力。迁移到 TF–DNA 课题：可构建时间截点后的 TF–DNA 复合物测试集，评估模型的泛化能力。

8. **部分扩散用于局部优化**：通过控制 SNR 对现有结合子进行局部扰动和优化。迁移到 TF–DNA 课题：可用于优化已有 TF–DNA 结合界面，在保持整体结构的同时微调关键接触。

---

## 15 与已有知识连接

- **AlphaFold3 (Abramson et al., 2024)**：ODesign 直接基于 AF3 架构和预训练权重。AF3 的 Pairformer 和扩散模块被改造为生成模型。连接点：AF3 的蛋白质-核酸-小分子统一表示是跨模态建模的基础。
- **RFDiffusion (Watson et al., 2023)**：ODesign 的主要基线之一，蛋白质-蛋白质结合子设计的 SOTA。ODesign 在吞吐量上超越 RFdiffusion 约 5 倍。
- **RFDiffusion-AA (Krishna et al., 2024)**：全原子蛋白质-配体设计基线。ODesign 在配体结合蛋白设计上实现 12.1 倍吞吐量提升。
- **RFDiffusion2 (Goverde et al., 2025)**：原子级基序支架基线。ODesign 在 AME 基准上超越 RFDiffusion2。
- **BoltzDesign (Wohlwend et al., 2024)**：基于 Boltz-1 的幻觉设计方法。ODesign 在吞吐量上大幅超越。
- **BindCraft (Pacesa et al., 2024)**：AF2 幻觉结合子设计。ODesign 在吞吐量上超越约 2 个数量级。
- **PocketGen (Zhang et al., 2024)**：口袋设计基线。ODesign 在口袋 RMSD 和 iPAE 上均优于 PocketGen。
- **MotifBench (Wang et al., 2024)**：基序支架基准。ODesign 在 30 个靶标中 27 个获得成功设计。
- **RNAFrameFlow (Ren et al., 2024)**：RNA 生成基线。ODesign 在 RNA 单体生成上超越约 2 倍。
- **AlphaProteo (Zambaldi et al., 2024)**：DeepMind 的蛋白质结合子设计系统。ODesign 采用了其评估标准（iPAE/ipTM/pLDDT 阈值）。
- **CaoData (Cao et al., 2022)**：蛋白质-蛋白质设计基准数据集，ODesign 从中选取 11 个靶标。
- **PoseBusters V2 (Buttenschoen et al., 2024)**：蛋白质-配体结构验证基准，用于 ODesign 的验证集。
- **ESM3 (Hayes et al., 2024)**：生成式蛋白质语言模型，作为 ODesign 的基线之一（未在图中展示详细对比）。

---

## 16 研究想法

**Agent 生成的研究候选**

1. **TF–DNA 结合界面定向生成**
   - 名称：TF-DNA Interface Designer
   - 来源局限/观察：ODesign 支持蛋白质→DNA 设计，但未专门优化 TF–DNA 结合界面的序列特异性
   - 核心假设：在 ODesign 框架中加入 TF–DNA 结合基序（如锌指、bZIP、homeodomain）的结构先验，可提升结合特异性
   - 初步方法：在 ODesign 的 token 空间中引入 TF 家族特定的 motif token；在训练数据中增加 TF–DNA 复合物的权重；在损失函数中加入结合界面残基-碱基接触的约束项
   - 验证方式：设计已知 TF 的 DNA 结合序列，与实验测定的结合位点（如 JASPAR、CIS-BP）比对；使用 AF3 预测复合物结构验证界面几何
   - 创新状态：unverified

2. **TF–DNA 共折叠生成**
   - 名称：Co-folding TF-DNA Generator
   - 来源局限/观察：ODesign 采用两阶段策略（先骨架后序列），可能无法充分捕捉 TF 和 DNA 的共折叠协同效应
   - 核心假设：联合生成 TF 和 DNA 的骨架与序列，可更好地捕捉结合诱导的构象变化
   - 初步方法：将 ODesign 的掩码策略扩展为"双链联合掩码"，同时掩蔽 TF 和 DNA 的部分 token；在扩散过程中引入 TF-DNA 界面距离约束
   - 验证方式：与 ODesign 的独立生成结果对比，评估复合物结构的界面质量（iPAE、界面接触数）
   - 创新状态：unverified

3. **TF–DNA 结合特异性预测器**
   - 名称：TF-DNA Specificity Predictor
   - 来源局限/观察：ODesign 是生成模型，不直接输出结合特异性评分；TF–DNA 结合特异性预测是独立任务
   - 核心假设：ODesign 的 Pairformer 表示可迁移到结合特异性预测任务
   - 初步方法：冻结 ODesign 的 Pairformer 权重，在 TF–DNA 结合数据上微调一个分类头；输入 TF 序列 + DNA 序列，输出结合概率
   - 验证方式：在标准 TF–DNA 结合数据集（如 ChIP-seq、SELEX）上评估 AUC
   - 创新状态：unverified

4. **TF–DNA 结合界面突变效应预测**
   - 名称：TF-DNA Mutation Effect Predictor
   - 来源局限/观察：ODesign 生成的结构可用于计算突变效应，但未提供直接工具
   - 核心假设：ODesign 生成的结构对突变的敏感性可预测实验测定的结合亲和力变化
   - 初步方法：对生成的 TF–DNA 复合物进行 in silico 突变扫描，计算结构变化分数；与实验测定的 ΔΔG 或 Kd 变化关联
   - 验证方式：使用 ProTherm、dbMPIKT 等数据库中的 TF–DNA 突变数据
   - 创新状态：unverified

5. **TF–DNA 共进化信息注入**
   - 名称：Co-evolution Enhanced TF-DNA Design
   - 来源局限/观察：ODesign 的训练数据主要是静态结构，未利用序列共进化信息
   - 核心假设：将 TF–DNA 共进化信息（如 EVcouplings、GREMLIN）作为额外特征，可提升设计序列的天然性
   - 初步方法：在 Embedding 模块中加入共进化特征；或在训练损失中加入共进化一致性约束
   - 验证方式：设计序列与天然 TF–DNA 序列的相似性；AF3 预测结构的质量
   - 创新状态：unverified

6. **TF–DNA 结合动力学的生成式建模**
   - 名称：Dynamic TF-DNA World Model
   - 来源局限/观察：ODesign 是静态结构生成模型，不捕捉结合动力学
   - 核心假设：在 ODesign 框架中加入时间维度（如噪声调度中引入时间条件），可生成结合路径上的中间构象
   - 初步方法：将 ODesign 的扩散过程扩展为时间条件扩散；在训练数据中加入分子动力学模拟的 TF–DNA 轨迹
   - 验证方式：生成构象与 MD 模拟轨迹的相似性；结合路径的物理合理性
   - 创新状态：unverified