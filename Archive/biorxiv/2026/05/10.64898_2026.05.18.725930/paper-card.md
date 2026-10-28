## 01 基本信息

- **标题**：Prediction of Transcription Factor DNA Binding Affinity with High-Throughput *K*<sub>d</sub> Measurements and Deep Learning
- **作者**：Zhi Wang; Di Wang; Ke Shen; Junchen Luo; Xinyao Wang; Nan Wu; Yunzhi Lang; Xiangyu Wang; Jun Ren; Wenyang Dong; Lu Pan; Yitong Lyu; Gang Li; Dubai Li; Chen Xie; Zhen Zhang; Shijun Yu; Liuying Shan; Nannan Zhang; Jian Yan; Mingchen Chen; Xiaoliang Sunney Xie
- **单位**：未提供（bioRxiv 预印本未列出完整单位信息）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2026
- **论文类型**：预印本（研究论文）
- **领域**：蛋白质-DNA 互作（TF–DNA 结合亲和力）× 深度学习
- **关键词**：Transcription factor, DNA binding affinity, K<sub>d</sub>, deaminase, deep learning, Seq2K<sub>d</sub>, ivt FOODIE, eQTL, ENTIRE
- **DOI/ID**：10.64898/2026.05.18.725930
- **代码**：未提供
- **数据**：ivt FOODIE 数据集（46 个 TF，13 个 DBD 家族）；JASPAR 预训练数据；ENTIRE 网络门户（集成模型与数据）
- **阅读日期**：2026-05-20（预印本发布日）
- **在该方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」交叉方向，核心贡献为：(1) 开发高通量 *in vitro* 亲和力测量方法 ivt FOODIE，直接测量基因组尺度 K<sub>d</sub>；(2) 构建 Seq2K<sub>d</sub> 深度学习模型，从序列预测绝对结合亲和力；(3) 将预测亲和力变化与 eQTL 效应关联，实现 TF 功能分层（activator-like vs. repressor-like）。该文填补了「序列→亲和力」定量预测的空白，区别于传统 motif 定性描述。

---

## 02 一句话总结

本文通过开发 deaminase 介导的 *in vitro* 足迹实验（ivt FOODIE）高通量测量 46 个人类 TF 的基因组尺度 K<sub>d</sub>，并用 JASPAR 预训练 + ivt FOODIE 微调的深度学习模型 Seq2K<sub>d</sub> 实现从 DNA 序列预测绝对结合亲和力，进而揭示遗传变异对基因表达和疾病易感性的影响。

---

## 03 研究问题

- **具体问题**：如何从 DNA 序列定量预测转录因子（TF）的绝对结合亲和力（K<sub>d</sub>），而非仅依赖定性的 motif 匹配？
- **为什么重要**：TF–DNA 结合亲和力是基因调控的物理基础。现有公共数据库（如 JASPAR）仅提供 motif 序列偏好，缺乏定量 K<sub>d</sub> 信息，限制了对调控机制的热力学理解及变异效应的精确评估。
- **现有方法不足**：(1) 传统实验方法（如 EMSA、SELEX）通量低，难以覆盖基因组规模；(2) 现有预测模型多为定性分类（结合/不结合），缺乏绝对亲和力输出；(3) 缺乏大规模 K<sub>d</sub> 训练数据，限制了深度学习模型的监督训练。
- **精确研究问题**：Can a deep learning model trained on high-throughput *in vitro* K<sub>d</sub> measurements predict absolute TF–DNA binding affinity across diverse DNA-binding domains, and can these predictions reveal functional consequences of genetic variation?

---

## 04 背景与发展脉络

*注：以下脉络基于本文框架，未经外部系统核验，标注为「仅本文框架」。*

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|---------|
| 1. 定性 motif 描述 | JASPAR, TRANSFAC, SELEX | 提供序列偏好，易于使用 | 无定量亲和力，无法区分强弱结合 | 本文用 JASPAR 做预训练 |
| 2. 定量亲和力实验 | EMSA, MITOMI, HT-SELEX | 可测 K<sub>d</sub> | 通量低，覆盖有限 | ivt FOODIE 突破通量瓶颈 |
| 3. 计算预测（定性） | DeepBind, DeepSEA, BPNet | 可预测结合/不结合 | 输出非绝对 K<sub>d</sub>，缺乏物理意义 | Seq2K<sub>d</sub> 输出绝对亲和力 |
| 4. 计算预测（定量） | 少量基于 PBM 数据的模型 | 可预测相对亲和力 | 数据规模小，泛化差 | 本文用 46 TF × 基因组尺度数据训练 |

**本文主张的位置**：在「高通量实验测量 + 深度学习预测」交叉点，首次实现基因组尺度绝对 K<sub>d</sub> 预测，并连接至功能基因组学（eQTL、疾病变异）。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|---------|
| 缺乏基因组尺度 K<sub>d</sub> 数据 | 现有数据库仅提供 motif，无定量亲和力 | 传统实验方法通量低，难以覆盖全基因组 | 引言部分（未提供具体节号） |
| 预测模型缺乏监督训练数据 | 深度学习模型多为无监督或弱监督 | 缺少大规模配对（序列，K<sub>d</sub>）数据 | 方法部分描述预训练+微调策略 |
| 绝对亲和力 vs. 相对亲和力 | 现有模型输出相对分数，无法比较不同 TF | 缺乏统一物理尺度 | Seq2K<sub>d</sub> 设计为输出绝对 K<sub>d</sub> |
| 变异效应评估不精确 | 现有方法难以量化变异对结合亲和力的影响 | 缺乏高精度定量模型 | 通过预测 K<sub>d</sub> 变化分析致病/良性变异 |

---

## 06 核心思想

### 1) 表面方法
- 实验端：ivt FOODIE 利用 deaminase 介导的 C-to-U 转换，在 *in vitro* 条件下对 TF 结合的基因组区域进行足迹分析，高通量测量 K<sub>d</sub>。
- 计算端：Seq2K<sub>d</sub> 深度学习模型，先在 JASPAR 结合位点上预训练，再用 ivt FOODIE 的 46 TF K<sub>d</sub> 数据微调，实现序列→绝对亲和力预测。

### 2) 核心洞察
- **实验与计算协同**：高通量实验数据为深度学习提供监督信号，使模型能学习「序列→物理亲和力」的映射，而非仅学习「序列→结合/不结合」的分类边界。
- **跨 DBD 泛化**：46 个 TF 覆盖 13 个 DBD 家族，使模型能泛化到未表征的 TF（约 500 个新 motif 发现）。
- **亲和力变化作为功能读out**：预测的 K<sub>d</sub> 变化与 eQTL 效应符号/大小相关，将物理量（亲和力）与功能量（基因表达）直接桥接。

### 3) 可能的普适教训 [Analysis]
- 将「物理量测量」与「深度学习预测」结合，可突破纯计算模型的性能天花板——高质量实验数据是模型能力的上限。
- 预训练+微调策略在生物序列任务中有效：先用公共数据（JASPAR）学通用表征，再用任务特定数据（ivt FOODIE）微调。
- 亲和力变化（ΔK<sub>d</sub>）比绝对 K<sub>d</sub> 更具功能解释力，可用于变异效应分层。

---

## 07 方法总览

- **输入**：DNA 序列（基因组区域或任意序列）；TF 身份（或 DBD 类型）
- **输出**：绝对 K<sub>d</sub> 值（预测）
- **模块**：
  1. ivt FOODIE 实验模块：体外转录 + deaminase 足迹 → 高通量 K<sub>d</sub> 测量
  2. Seq2K<sub>d</sub> 模型：序列编码器（深度学习）→ 亲和力回归头
  3. 预训练模块：JASPAR 结合位点 → 学习序列表征
  4. 微调模块：ivt FOODIE K<sub>d</sub> 数据 → 学习绝对亲和力映射
  5. 下游分析模块：motif 发现、eQTL 关联、变异效应分析
- **训练**：两阶段（预训练 + 微调）；损失函数为回归损失（如 MSE，具体未提供）
- **反馈回路**：预测结果 → 新 TF 实验验证 → 数据扩充 → 模型迭代（文中未明确描述，[Analysis] 推断）
- **文字流程**：从基因组提取候选区域 → ivt FOODIE 实验测量 K<sub>d</sub> → 构建训练集（序列，K<sub>d</sub>）→ JASPAR 预训练 Seq2K<sub>d</sub> → ivt FOODIE 微调 → 预测任意序列的 K<sub>d</sub> → 下游功能分析（motif、eQTL、变异）

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|---------|---------|---------|----------------------|
| ivt FOODIE 实验 | 高通量测量 TF 的基因组尺度 K<sub>d</sub> | 提供监督训练数据，是模型性能上限 | 输入：TF + 基因组 DNA；输出：K<sub>d</sub> 图谱 | 方法部分描述；46 TF 数据 | 无训练数据，Seq2K<sub>d</sub> 无法监督学习（预期） |
| JASPAR 预训练 | 学习 TF 结合位点的序列表征 | 利用公共数据初始化模型，缓解小样本问题 | 输入：JASPAR motif 序列；输出：预训练权重 | 方法部分描述 | 预训练移除后，微调可能过拟合（预期） |
| Seq2K<sub>d</sub> 回归头 | 从序列特征映射到绝对 K<sub>d</sub> | 输出物理量而非分类标签 | 输入：序列嵌入；输出：K<sub>d</sub> 标量 | 模型设计部分 | 无回归头则无法输出绝对亲和力（预期） |
| eQTL 关联分析 | 将预测 ΔK<sub>d</sub> 与基因表达效应关联 | 验证预测的功能相关性，实现 TF 分层 | 输入：预测 ΔK<sub>d</sub> + eQTL 数据；输出：TF 分层（activator/repressor） | Results 部分（未提供具体图号） | 移除后无法建立「亲和力→表达」桥梁（预期） |
| 变异效应分析 | 比较致病/良性变异的 ΔK<sub>d</sub> 分布 | 展示临床应用价值 | 输入：ClinVar 变异 + 预测 ΔK<sub>d</sub>；输出：统计显著性 | Results 部分（未提供具体图号） | 移除后失去疾病相关性证据（预期） |

*注：文中未提供消融实验，以上「预期影响」均为 [Analysis] 推断，非实测。*

---

## 09 关键公式符号

本文为预印本，摘要中未提供具体公式。基于方法描述，核心关系可表示为：

- **结合亲和力定义**：K<sub>d</sub> = [TF][DNA] / [TF-DNA]（解离常数，文中未显式给出，[Analysis] 推断）
- **预测目标**：K<sub>d</sub><sup>pred</sup> = f<sub>θ</sub>(sequence)，其中 f<sub>θ</sub> 为 Seq2K<sub>d</sub> 模型参数
- **变异效应**：ΔK<sub>d</sub> = K<sub>d</sub><sup>mut</sup> - K<sub>d</sub><sup>ref</sup>（文中未显式给出，[Analysis] 推断）

*注：具体损失函数、网络架构公式未在摘要中提供。*

---

## 10 实验设计与证据链

- **数据集**：
  - ivt FOODIE 数据：46 个人类 TF，覆盖 13 个 DBD 家族，基因组尺度 K<sub>d</sub> 测量
  - JASPAR：预训练用 TF 结合位点
  - eQTL 数据：用于功能关联分析（具体来源未提供）
  - ClinVar：致病/良性变异分析
- **规模**：46 TF；约 500 个新 motif 发现
- **指标**：K<sub>d</sub> 预测精度（具体指标如 R²、Pearson r 未提供）；eQTL 关联显著性；变异 ΔK<sub>d</sub> 分布差异
- **基线**：未明确提及（可能为 motif 匹配方法或现有预测模型，未提供）
- **评测协议**：未详细描述（预印本摘要限制）

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|----------------|------|
| ivt FOODIE 测量 | 高通量 K<sub>d</sub> 测量的可行性 | 46 TF × 基因组区域 | 成功获得 K<sub>d</sub> 图谱 | 方法可行 | 未与其他方法直接对比 | 方法部分 |
| Seq2K<sub>d</sub> 预测 | 序列→绝对 K<sub>d</sub> 预测能力 | 训练集内评估 | 预测成功（具体数值未提供） | 模型有效 | 未提供独立测试集结果 | Results |
| de novo motif 发现 | 泛化到未表征 TF | 约 500 个 TF | 发现新 motif | 模型可泛化 | 未实验验证这些 motif | Results |
| eQTL 关联 | 预测 ΔK<sub>d</sub> 与表达效应相关 | activator vs. repressor 分层 | 显著相关 | 亲和力变化有功能意义 | 因果关系未证明 | Results |
| 变异分析 | 致病变异 ΔK<sub>d</sub> 更大 | 致病 vs. 良性 | 显著差异 | 可用于疾病解读 | 未做前瞻性验证 | Results |

---

## 11 结论正确解读

- **任务范围**：本文解决的是「给定 TF 和 DNA 序列，预测绝对 K<sub>d</sub>」的回归任务，而非分类任务。
- **oracle/真值输入**：K<sub>d</sub> 真值来自 ivt FOODIE 实验测量，该测量本身可能有系统误差（未讨论）。
- **端到端状态**：实验→训练→预测→功能分析全流程已打通，但预测精度上限受限于实验数据质量。
- **算力成本**：未提供。
- **历史数据依赖**：预训练依赖 JASPAR，微调依赖 ivt FOODIE；两者覆盖的 TF 和序列空间有限。
- **模型依赖**：Seq2K<sub>d</sub> 架构细节未在摘要中提供，无法评估其可复现性。
- **最难情形**：未讨论（如低亲和力结合、非经典 motif、染色质背景效应）。
- **群体/领域边界**：仅人类 TF；仅 *in vitro* 测量，未考虑体内染色质可及性、竞争性结合等。
- **不确定性**：预测 K<sub>d</sub> 的置信区间未提供；eQTL 关联为相关性，非因果。

**有边界的复述**：本文证明，在 46 个人类 TF（13 个 DBD 家族）范围内，结合高通量 *in vitro* K<sub>d</sub> 测量和深度学习，可以预测 DNA 序列的绝对结合亲和力，且预测的亲和力变化与 eQTL 效应和疾病变异相关。该结论不适用于未覆盖的 TF 或体内复杂环境。

---

## 12 作者自认局限

在提供的摘要中，作者未明确列出局限性。以下为作者提及的相关约束（非正式局限）：

- 测量范围限于「accessible genomic regions from human cells」（摘要原文），暗示未覆盖全部基因组。
- 预训练数据来自 JASPAR，可能引入已知 motif 偏好偏差。
- 未提供模型在非人类物种或非标准条件下的验证。

*注：完整局限性可能在正文中，但摘要未提供。*

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|-------------------|---------|---------|------|
| 46 TF 覆盖 13 DBD，但人类有约 1600 个 TF | 模型可能对未覆盖的 DBD 家族泛化差 | 影响「约 500 个新 TF」的可靠性 | 在独立 DBD 家族上测试 | 摘要中 TF 数量 |
| eQTL 关联为相关性 | 可能是连锁不平衡或混杂因素导致 | 影响「TF 分层」的因果解释 | 孟德尔随机化或 CRISPR 验证 | Results 描述 |
| 未提供与现有方法的定量对比 | 无法判断 Seq2K<sub>d</sub> 是否优于 PBM 或 HT-SELEX 模型 | 影响方法贡献的评估 | 在公共基准上对比 | 摘要未提及基线 |
| 致病/良性变异 ΔK<sub>d</sub> 差异 | 可能受变异类型（如截断突变）驱动，而非亲和力变化 | 影响「疾病机制」结论 | 分层分析（错义 vs. 截断） | Results 描述 |
| 未讨论 *in vitro* 到 *in vivo* 的差距 | 体内有染色质、竞争、辅因子等 | 影响生物学解释 | 与 ChIP-seq 数据对比 | 摘要未提及 |

---

## 14 Agent 提炼的知识候选

### 可迁移概念与方法

1. **高通量 K<sub>d</sub> 测量实验设计（ivt FOODIE）**
   - 核心：deaminase 介导的 C-to-U 转换 + 体外足迹 → 高通量亲和力测量
   - 迁移到本课题：可用于其他 DNA 结合蛋白（如染色质重塑因子、修复蛋白）的亲和力测量；也可适配为 RNA-蛋白互作测量

2. **预训练 + 微调策略**
   - 核心：JASPAR（公共 motif 数据）预训练 → 任务特定数据微调
   - 迁移到本课题：可用公共 ChIP-seq 或 HT-SELEX 数据预训练，再用少量高精度 K<sub>d</sub> 数据微调，降低实验成本

3. **绝对亲和力输出 vs. 分类输出**
   - 核心：回归到 K<sub>d</sub> 而非二分类
   - 迁移到本课题：对 TF–DNA 机制研究，绝对亲和力可区分「强/弱结合」的连续谱，优于「结合/不结合」的定性描述

4. **ΔK<sub>d</sub> 作为功能读out**
   - 核心：亲和力变化与 eQTL 效应关联，实现 TF 功能分层
   - 迁移到本课题：可用于预测非编码变异对 TF 结合的影响，并关联到疾病

5. **跨 DBD 泛化**
   - 核心：46 TF × 13 DBD 训练，实现跨家族泛化
   - 迁移到本课题：设计训练集时覆盖多个 DBD 家族，可提升模型对新 TF 的预测能力

### 可迁移公式/框架
- 序列→K<sub>d</sub> 的回归框架可直接用于其他 DNA 结合蛋白
- 预训练+微调的两阶段训练范式可复用于其他生物序列任务

---

## 15 与已有知识连接

- **JASPAR**：本文用 JASPAR 做预训练，JASPAR 是 TF 结合 motif 的权威数据库（Sandelin et al., 2004; Fornes et al., 2020）。连接点：motif 定性信息 → 定量 K<sub>d</sub> 的升级。
- **DeepBind (Alipanahi et al., 2015)**：早期用深度学习预测 TF 结合，但输出为结合分数而非绝对 K<sub>d</sub>。本文的 ΔK<sub>d</sub> 输出是重要差异。
- **HT-SELEX (Jolma et al., 2010)**：高通量测量 TF 结合特异性的经典方法，但通常给出相对偏好而非绝对 K<sub>d</sub>。ivt FOODIE 的绝对定量是改进。
- **MITOMI (Maerkl & Quake, 2007)**：微流控测量 K<sub>d</sub> 的早期方法，通量低。ivt FOODIE 的基因组尺度覆盖是突破。
- **eQTL 分析 (GTEx Consortium)**：本文用 eQTL 验证预测的功能相关性，GTEx 是标准参考。
- **ClinVar (Landrum et al., 2018)**：用于致病/良性变异分析，连接预测到临床。
- **候选方向**：与 AlphaFold 类结构预测结合，探索「序列→结构→亲和力」的端到端预测；与分子动力学模拟结合，验证预测的 K<sub>d</sub> 是否与物理模拟一致。

---

## 16 Agent 生成的研究候选

### 候选 1：跨物种 TF–DNA 亲和力预测迁移
- **名称**：Cross-species TF–DNA affinity transfer learning
- **来源局限/观察**：本文仅人类 TF；不同物种 TF 同源但结合偏好可能分化
- **核心假设**：预训练在人类数据上的 Seq2K<sub>d</sub> 可迁移到其他物种，且迁移性能与 DBD 保守性相关
- **初步方法**：用人类数据训练，在模式生物（小鼠、果蝇、酵母）的 K<sub>d</sub> 数据上微调或零样本测试
- **验证方式**：与各物种实验 K<sub>d</sub> 对比，计算 Pearson r / R²
- **创新状态**：unverified

### 候选 2：结合染色质可及性的体内亲和力预测
- **名称**：Integrating chromatin accessibility into K<sub>d</sub> prediction
- **来源局限/观察**：本文为 *in vitro* 测量，未考虑体内染色质状态
- **核心假设**：将 ATAC-seq 可及性作为额外输入，可提高体内结合预测准确性
- **初步方法**：在 Seq2K<sub>d</sub> 基础上增加可及性特征通道，用 ChIP-seq 数据验证
- **验证方式**：预测的体内结合与 ChIP-seq peak 重叠率
- **创新状态**：unverified

### 候选 3：ΔK<sub>d</sub> 驱动的非编码变异致病性预测
- **名称**：ΔK<sub>d</sub>-based pathogenicity scoring for non-coding variants
- **来源局限/观察**：本文显示致病变异 ΔK<sub>d</sub> 更大，但未构建预测工具
- **核心假设**：ΔK<sub>d</sub> 可作为非编码变异致病性的量化特征，优于现有保守性评分
- **初步方法**：用 Seq2K<sub>d</sub> 计算所有 ClinVar 非编码变异的 ΔK<sub>d</sub>，训练分类器区分致病/良性
- **验证方式**：AUC 对比现有工具（CADD, Eigen, etc.）
- **创新状态**：unverified

### 候选 4：TF 结合亲和力与 DNA 结构特征的关联
- **名称**：Linking K<sub>d</sub> to DNA structural features
- **来源局限/观察**：本文纯序列模型，未利用 DNA 结构信息
- **核心假设**：DNA 结构特征（弯曲性、螺旋参数）可提高 K<sub>d</sub> 预测精度，尤其在非 B-DNA 区域
- **初步方法**：用 DNAShape 或 MD 模拟生成结构特征，与序列特征融合输入模型
- **验证方式**：对比有无结构特征的预测精度
- **创新状态**：unverified

### 候选 5：TF 突变对 DNA 结合亲和力的影响预测
- **名称**：Predicting K<sub>d</sub> changes upon TF protein mutations
- **来源局限/观察**：本文预测 DNA 序列变异的影响，未涉及 TF 蛋白突变
- **核心假设**：TF 蛋白序列/结构变化导致的 K<sub>d</sub> 变化可被学习
- **初步方法**：扩展 Seq2K<sub>d</sub> 输入为 (TF 序列, DNA 序列) 对，用突变体 K<sub>d</sub> 数据训练
- **验证方式**：与饱和突变实验数据对比
- **创新状态**：unverified

### 候选 6：与分子动力学模拟的交叉验证
- **名称**：Cross-validating Seq2K<sub>d</sub> with MD-simulated binding free energies
- **来源局限/观察**：深度学习预测缺乏物理可解释性
- **核心假设**：MD 模拟计算的结合自由能与 Seq2K<sub>d</sub> 预测一致，可互相验证
- **初步方法**：选取代表性 TF–DNA 复合物，用 MD/MM-PBSA 计算 ΔG，与模型预测 K<sub>d</sub> 转换的 ΔG 对比
- **验证方式**：相关性分析；不一致案例用于改进模型
- **创新状态**：unverified