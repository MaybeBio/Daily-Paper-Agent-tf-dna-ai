## 01 基本信息

- **标题**：Improving interpretability of transcription factor binding models with DNA shape features
- **作者与单位**：Keivanfar RL; Yang F; Pollard KS; Ioannidis NM（Gladstone Institutes；UC Berkeley；Chan Zuckerberg Biohub San Francisco 等，具体单位对应关系原文未逐一列出）
- **期刊/预印本平台**：bioRxiv（预印本）
- **年份**：2025（2025-04-03 发布）
- **论文类型**：方法学/预印本（深度学习模型开发 + 可解释性分析）
- **领域**：基因组学 × 深度学习 × 蛋白质-DNA 互作（转录因子结合预测）
- **关键词**：DNA shape、transcription factor binding、deep learning、interpretability、DeepLIFT、TF-MoDISco、ChIP-seq
- **DOI/arXiv 号**：10.1101/2025.04.01.646034
- **代码**：https://github.com/ni-lab/DeepShape
- **数据**：DNA shape 输入数据 Zenodo DOI 10.5281/zenodo.13334119；模型权重 Zenodo 及 https://huggingface.co/ryankeivanfar/DeepShape
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文属于「TF–DNA 结合机制 × 深度学习」交叉方向，核心贡献在于将 DNA 结构特征（shape）显式作为深度学习模型的输入通道，与经典 one-hot 序列编码并行处理，从而在保持预测性能的同时提供额外的可解释性维度。该工作直接回应了「序列基序不足以完全解释 TF 结合特异性」这一领域痛点，属于可解释 AI 与结构生物学交叉的前沿尝试。

## 02 一句话总结

本文开发了 DeepShape——一个双分支卷积神经网络，将 one-hot 序列编码与五种 DNA shape 特征（MGW、HelT、ProT、Roll、EP）并行输入，在 919 个基因组靶标（含 690 个 TF ChIP-seq 靶标）上达到与序列-only 模型相当或略优的性能（AUROC 0.929 vs 0.925），并通过 DeepLIFT 和 TF-MoDISco 证明 shape 特征提供了序列之外的可解释性信息，尤其在非经典基序和侧翼区域对 TF 结合起调节作用。

## 03 研究问题

- **具体问题**：深度学习模型能否通过显式引入 DNA shape 特征，在预测 TF 结合的同时提供超越序列基序的可解释性洞察？
- **为什么重要**：TF–DNA 识别不仅依赖序列基序，还涉及 shape readout 机制（即 TF 通过 DNA 局部三维结构识别结合位点）。现有深度学习模型（如 DeepSEA、DeeperDeepSEA）仅使用 one-hot 序列输入，虽能捕捉序列基序，但无法显式建模结构信息，且「黑箱」特性限制了机制性解读。
- **现有方法为何不足**：传统 shape 分析（如 DNAShapeR 的富集检验）只能描述统计富集，无法与深度学习模型的预测能力结合；而纯序列深度学习模型无法区分序列效应与结构效应，也难以解释非经典基序结合事件。
- **精确的「Can ... ?」研究问题**：Can a deep learning model that explicitly incorporates DNA shape features alongside sequence achieve comparable predictive performance while providing additional interpretable insights into TF–DNA binding mechanisms beyond what sequence-only models can offer?

## 04 背景与发展脉络

> 注：以下脉络基于本文引用与论述，标注为「仅本文框架」——未经外部系统核验。

1. **第一代：序列基序发现工具**（如 MEME）——基于位置权重矩阵（PWM）识别保守基序。局限：无法捕捉基序间的协同/竞争关系，忽略结构信息。
2. **第二代：基因组深度学习模型**（DeepSEA → DeeperDeepSEA / Basenji 等）——以 one-hot 序列为输入，端到端预测多种分子表型。优势：自动学习复杂调控语法；局限：黑箱性质，难以提取机制性知识，且完全忽略 DNA 三维结构。
3. **第三代：可解释性方法**（DeepLIFT、TF-MoDISco、Puffin 等）——通过特征归因或设计可解释架构来解读模型学到的序列特征。局限：仍局限于序列维度，无法回答「结构如何影响结合」。
4. **并行脉络：DNA shape 分析**（DNAShapeR 等）——从序列预测局部结构特征（MGW、HelT、ProT、Roll、EP），通过富集检验发现 shape 在 TF 结合中的作用。局限：统计方法无法与预测模型整合，难以刻画复杂非线性关系。
5. **本文位置**：DeepShape 首次将 DNA shape 特征作为显式输入通道与序列并行嵌入深度学习架构，在保持预测性能的同时，通过归因分析将 shape 信息转化为可解释的生物学洞察——填补了「深度学习 × 结构可解释性」的空白。

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 序列基序不足以完全解释 TF 结合特异性 | 同一基序在不同基因组位置结合强度差异大；存在非经典基序结合事件 | TF 结合受 DNA 局部结构（shape readout）调节，序列 alone 无法捕捉结构效应 | Introduction 引用 [13,14,15]；Myc-Max 案例中 E-box 基序不足以解释结合特异性（Results 图 3） |
| 深度学习模型缺乏机制可解释性 | 模型预测准确但无法回答「为什么这个位置被结合」 | 黑箱神经网络的特征难以映射到生物学机制 | Introduction 引用 [10,11,12]；本文动机 |
| 现有 shape 分析方法与预测模型脱节 | 富集检验只能描述统计关联，无法与深度学习预测能力整合 | 统计方法与深度学习分属不同方法论范式 | Introduction 对 [16] 的讨论 |
| 模型超参数影响 shape 特征利用率 | 默认超参数下 shape 分支贡献较低 | 原始 DeeperDeepSEA 超参数未针对多模态输入优化 | Results 图 1b 与 Supp. fig. 2 对比；Supp. fig. 1 超参数搜索 |
| shape 特征归因难以可视化 | 连续值 shape 特征无法直接用于 TF-MoDISco 等基序发现工具 | TF-MoDISco 设计用于离散序列特征 | Methods 中 shape 特征四分位数离散化处理 |

## 06 核心思想

**1) 表面方法**：构建双分支卷积神经网络 DeepShape——序列分支处理 one-hot 编码，shape 分支处理五种 DNA 结构特征（MGW、HelT、ProT、Roll、EP），两分支各经两层卷积后拼接，再经四层卷积、池化、批归一化、dropout 和全连接层输出 919 个靶标的二分类预测。训练后使用 DeepLIFT 计算特征归因，并将 shape 归因离散化为四分位数后输入 TF-MoDISco 发现 shape 基序。

**2) 核心洞察**：
- 将 DNA shape 作为显式输入而非隐式学习，使模型必须「使用」结构信息，从而在归因分析中可直接解读结构贡献。
- 序列与 shape 分支的分离设计使得可以分别考察两类特征的贡献，实现「双通道可解释性」。
- 关键发现：shape 归因与序列归因呈稳定比例关系（shape ≈ 0.269 × sequence），提示模型以一致方式整合结构信息；但个别 TF（如 MafK）显著偏离此趋势，暗示其结合机制更依赖 shape readout。
- 对 Myc-Max 的分析揭示 shape 分支激活分布弥散于基序侧翼而非集中于 E-box 本身，与「shape 调节结合亲和力」的机制假说一致。

**3) 可能的普适教训** [Analysis]：
- 在生物序列深度学习中，显式引入物理/结构先验（如 DNA shape）比纯数据驱动隐式学习更有利于机制解读——「可解释性应设计进架构而非事后附加」。
- 双分支架构 + 归因比例分析是一种可迁移的通用范式：通过比较不同输入模态的归因相对贡献，可量化不同生物学机制在预测中的权重。
- 将连续值特征离散化后适配现有基序发现工具（TF-MoDISco）是一种低成本高收益的工具复用策略。

## 07 方法总览

- **输入**：
  - 序列分支：1000-bp one-hot 编码 DNA 序列（4 通道）
  - shape 分支：1000-bp × 5 种 shape 特征（MGW、HelT、ProT、Roll、EP），由 DNAShapeR 从 hg19 参考基因组预计算
- **输出**：919 个基因组靶标的二分类预测（结合/不结合），包括 690 个 TF ChIP-seq、125 个 DNase、104 个组蛋白修饰靶标
- **模型架构**：双分支 CNN——各分支 2 层卷积 → 拼接 → 4 层卷积 → 2 层最大池化 → 3 层批归一化 → 2 层 dropout → 展平 → 2 层全连接 → sigmoid 输出。每层 450 个卷积核，滤波器长度 4（经超参数搜索确定）
- **训练**：二值交叉熵损失；训练参数（步数、batch size 等）与 DeepSEA/DeeperDeepSEA 原始设置一致；6 个染色体划分的交叉验证（reciprocal validation/test splits）
- **标签生成**：基因组按 200-bp bin 划分，bin 与 ChIP-seq peak 重叠超过 50% 即为正样本
- **可解释性分析**：
  - DeepLIFT 归因：计算每个输入特征对预测的贡献，满足求和-到-增量性质
  - TF-MoDISco：将 shape 归因值按四分位数离散化为 4 维 one-hot 编码，输入 TF-MoDISco 聚类发现 shape 基序
  - 序列-形状归因比例分析：拟合 shape 归因与序列归因的线性关系
  - 置换检验：随机置换 shape 特征评估其对预测的贡献
- **下游验证**：用 TF-MoDISco 发现的基序对数据集重新特征化，训练逻辑回归和梯度提升模型预测 TF 结合，评估基序的相对重要性

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 序列分支（2 层卷积） | 从 one-hot 序列提取序列基序特征 | 捕捉经典 PWM 类基序信息 | 输入：1000×4 one-hot；输出：卷积特征图 | 模型整体性能与 DeeperDeepSEA 相当（Results 图 1b） | 预期：模型退化为纯 shape 模型，性能大幅下降 [预期效应] |
| shape 分支（2 层卷积） | 从 5 种 shape 特征提取结构模式 | 显式建模 DNA 局部结构对结合的贡献 | 输入：1000×5 shape 值；输出：卷积特征图 | 置换 shape 特征导致性能下降（Results 图 1c）；MafK 案例中 shape 基序有独立贡献（Results 图 4） | 实测：置换后 AUROC 贡献比 0.228，AUPRC 贡献比 0.348（Results 图 1c）[实测消融效应] |
| 特征拼接 + 后续卷积层 | 整合序列与结构信息，学习二者交互 | 序列与 shape 可能协同决定结合特异性 | 输入：两分支特征图拼接；输出：高层抽象特征 | 模型整体性能（Results 图 1b） | 预期：移除后无法建模序列-shape 交互 [预期效应] |
| 超参数搜索 | 确定滤波器长度 4、450 kernels/层 | 原始 DeeperDeepSEA 超参数未针对双输入优化 | 输入：候选超参数集；输出：最优配置 | Supp. fig. 1；优化后 shape 贡献比提升（Supp. fig. 2 对比） | 预期：使用默认超参数时 shape 分支利用率降低 [预期效应] |
| DeepLIFT 归因 | 计算每个输入特征对预测的贡献 | 实现输入级可解释性 | 输入：训练好的模型 + 输入样本；输出：逐特征归因分数 | Methods DeepLIFT 节；Results 图 2-4 | 预期：移除后无法定位关键序列/结构位置 [预期效应] |
| shape 归因离散化 + TF-MoDISco | 将连续 shape 归因转化为可聚类的离散模式 | 适配现有基序发现工具 | 输入：shape 归因分数；输出：shape 基序 | Results 图 4b-f；MafK ProT 基序的发现 | 预期：移除后无法发现 shape 基序模式 [预期效应] |
| 置换检验 | 随机打乱 shape 特征评估其贡献 | 量化 shape 信息的独立预测价值 | 输入：模型 + 置换后的 shape 输入；输出：性能下降量 | Results 图 1c | 实测：AUROC 贡献比 0.228，AUPRC 贡献比 0.348 [实测消融效应] |
| 基序特征化 + 下游分类器 | 用发现的基序重新特征化数据，训练简单模型 | 验证基序的独立预测能力 | 输入：基序匹配分数；输出：TF 结合预测 | Results 图 5a-c | 预期：移除后无法评估基序相对重要性 [预期效应] |

## 09 关键公式符号

**1) DeepLIFT 求和-到-增量性质**（Methods DeepLIFT 节）：

$$\hat{y}_{input} - \hat{y}_{ref} = \sum_{f} Att_f$$

- $\hat{y}_{input}$：模型对给定输入序列的预测输出
- $\hat{y}_{ref}$：模型对参考序列的预测输出
- $Att_f$：特征 $f$ 的归因分数
- **用途**：保证所有特征归因之和等于预测差异，使归因可解释为「每个特征的贡献量」
- **直觉**：将模型的预测变化「分配」到每个输入特征上，类似沙普利值分解
- **来源**：Methods DeepLIFT 节

**2) 置换检验贡献比**（Results 图 1c 描述）：

$$\text{Contribution Ratio} = \frac{\text{Performance}_{\text{original}} - \text{Performance}_{\text{permuted}}}{\text{Performance}_{\text{original}}}$$

- **用途**：量化 shape 或序列特征对模型性能的相对贡献
- **直觉**：打乱某类特征后性能下降的比例越大，说明该类特征越重要
- **来源**：Results 图 1c 描述（公式为 [Analysis] 重构，原文未给出显式公式）

**3) 序列-形状归因比例**（Results 图 4a 描述）：

$$\text{Shape Attribution} \approx 0.269 \times \text{Sequence Attribution}$$

- **用途**：描述跨 TF 的 shape 与序列归因的平均比例关系
- **直觉**：模型整体上赋予序列约 3.7 倍于 shape 的归因权重，但个别 TF 偏离此趋势
- **来源**：Results 图 4a（数值 0.269 来自原文）

## 10 实验设计与证据链

**数据集与评测设置**：
- **训练/评测数据**：ENCODE 和 Roadmap Epigenomics 统一处理的 919 个基因组靶标（690 TF ChIP-seq、125 DNase、104 组蛋白修饰），覆盖 148 个细胞类型、34 个处理条件
- **标签策略**：200-bp 基因组 bin，与 peak 区域重叠 >50% 为正样本
- **数据划分**：6 个染色体划分的 reciprocal validation/test splits（染色体 6/7、8/9、9、10/11/12、14/15、15/16）
- **基准模型**：作者训练的 DeeperDeepSEA（序列-only，含原始超参数和优化后超参数两种版本）
- **评估指标**：AUROC、AUPRC
- **超参数搜索**：11 个 TF 靶标用于超参数调优（基于强 shape 或序列偏好选择）
- **可解释性分析**：DeepLIFT 归因 + TF-MoDISco 基序发现 + 置换检验 + 下游分类器验证

**实验表格**：

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| 全靶标性能基准 | DeepShape 性能不劣于序列-only 模型 | DeepShape vs 作者训练的 DeeperDeepSEA（6 个划分） | 平均 AUROC 0.929 vs 0.925；平均 AUPRC 0.379 vs 0.367 | 加入 shape 特征不损害预测性能，略有提升 | 性能提升幅度小，未报告显著性检验 | Results 图 1b |
| 置换检验 | shape 特征对预测有独立贡献 | 置换 shape 特征 vs 置换序列特征 | shape 贡献比 AUROC 0.228、AUPRC 0.348 | shape 信息对预测有实质贡献 | 贡献比数值依赖置换策略，未报告方差 | Results 图 1c |
| 超参数对比 | 优化超参数提升 shape 利用率 | 优化后超参数 vs 原始 DeeperDeepSEA 超参数 | 优化后 shape 贡献比更高（Supp. fig. 2：AUROC 0.101 → 0.228） | 超参数搜索对多模态输入至关重要 | 未系统分析超参数-贡献比关系 | Results 图 1c vs Supp. fig. 2 |
| 结合位点 shape 分布 | shape 特征在结合位点有系统性偏移 | 结合位点 vs 背景序列的 shape 值分布 | 各 shape 特征在结合位点呈现显著偏移（KS 检验） | shape 特征在 TF 结合位点具有信息量 | KS 统计量未报告具体数值 | Results 图 2a-b |
| Myc-Max 分支激活分析 | shape 分支捕捉基序侧翼结构信息 | 序列分支 vs shape 分支的激活分布 | 序列分支激活集中于 E-box；shape 分支激活弥散于侧翼 | shape 提供基序之外的补充信息 | 仅分析单一 TF 二聚体，推广性有限 | Results 图 3 |
| MafK shape 基序发现 | shape 基序可解释 MafK 结合特异性 | TF-MoDISco 发现的 ProT 基序 vs 序列基序 | 发现 ProT shape 基序，与序列基序共现于侧翼区；共现位点 ChIP-seq 信号显著更高 | shape 基序调节 MafK 结合亲和力 | 仅单一 TF 案例，需更多验证 | Results 图 4b-f |
| 基序消融验证 | shape 基序有独立预测价值 | 含 vs 不含 ProT 基序的位点 | 共现位点结合信号更高（Supp. table 2） | shape 基序对结合有正向调节作用 | 相关性非因果性，未做扰动实验 | Results 图 4e |

## 11 结论正确解读

- **任务范围**：本文结论仅适用于「从 DNA 序列预测 TF 结合」这一任务设定，不涉及 TF 结合后的下游功能（如转录调控、染色质状态变化）。
- **Oracle/真值输入**：训练标签来自 ENCODE/Roadmap 的 ChIP-seq peak 调用，本质上是实验观测而非 ground truth 结合亲和力；peak 调用阈值、细胞类型特异性等会影响标签质量。
- **端到端状态**：DeepShape 是端到端训练的预测模型，但 shape 特征由 DNAShapeR 预计算（非可微），因此 shape 分支学到的表征受限于 DNAShapeR 的预测精度。
- **算力成本**：原文未报告训练时间、GPU 数量等计算资源信息（Not assessable）。
- **历史数据依赖**：模型基于 hg19 参考基因组训练，shape 特征来自参考序列而非样本特异性结构（如 ChIP-exo 或 cryo-EM 实测结构），因此无法捕捉体内动态构象。
- **模型依赖**：结论基于特定架构（双分支 CNN）和特定解释工具（DeepLIFT + TF-MoDISco），不同架构或归因方法可能产生不同结果。
- **最难情形**：作者未系统分析模型在哪些情况下失败（如低置信度 peak、非经典基序、间接结合等）。
- **群体/领域边界**：训练数据来自 ENCODE/Roadmap 的细胞系，主要覆盖常见癌细胞系和少数原代细胞；对罕见细胞类型或非人类物种的泛化能力未验证。
- **不确定性**：性能提升幅度小（AUROC +0.004），未报告置信区间或显著性检验；置换检验的贡献比未报告方差。

**有边界的复述**：在 ENCODE/Roadmap 的 919 个靶标上，将五种 DNA shape 特征作为显式输入与序列并行训练的 DeepShape 模型，其预测性能与序列-only 的 DeeperDeepSEA 相当（AUROC 0.929 vs 0.925），且通过归因分析可提取 shape 层面的可解释模式，其中 MafK 案例显示侧翼 ProT shape 基序与序列基序共现时结合信号增强。这些发现支持 shape 特征在 TF 结合预测中具有补充价值，但性能增益有限，且结论局限于参考基因组静态 shape 预测和 ChIP-seq 标签定义。

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|-------------------|------|
| shape 特征的静态性 | 使用的 shape 特征代表 DNA 的固有/偏好构象，未考虑动态结构变化 | 未明确提及 | Discussion 末段 |
| 缺乏大规模结构特征 | 未考虑拓扑关联结构域（TADs）等更大尺度特征 | 未明确提及 | Discussion 末段 |
| 未考虑 DNA 修饰 | 未纳入甲基化等 DNA 修饰对 shape 的影响 | 未明确提及 | Discussion 末段 |
| 连续值 shape 输入导致归因分散 | 连续值输入可能贡献了观察到的弥散归因模式 | 可测试将输入转换为二值/极端分位数形式 | Discussion 末段 |
| 归因模式的验证有限 | 仅对 MafK 进行了深入的 shape 基序验证 | 未明确提及 | Discussion 末段 |

> 注：作者在 Discussion 末段集中讨论了这些局限，但未逐一提出具体未来方向。原文表述为「The DNA shape features used represent a static, localized view of DNA structure, neglecting its dynamic nature and larger-scale features... Additionally the use of continuous values for shape inputs may contribute to the observed diffuse attribution patterns. This could be tested by converting input features to a binary form...」

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 性能提升幅度极小（AUROC +0.004） | 可能不具实际意义；shape 分支可能主要学习了与序列冗余的信息 | 若 shape 无独立预测价值，则「可解释性增益」可能是伪命题 | 报告置信区间；在序列信息被遮蔽（如仅用 shape 输入）条件下测试性能 | Results 图 1b 数值 |
| 置换检验的贡献比（0.228/0.348）与整体性能提升（+0.004 AUROC）之间存在张力 | 置换检验可能高估了 shape 的贡献，因为置换破坏了输入分布的一致性 | 贡献比是本文核心证据之一，若不可靠则削弱 shape 价值论证 | 使用更保守的消融方法（如将 shape 分支置零而非置换） | Results 图 1c |
| MafK 案例的选择偏差 | 作者可能预先知道 MafK 有强 shape 偏好才选择分析；未报告系统扫描多少 TF 后发现此案例 | 单案例不能支持「shape 基序普遍调节 TF 结合」的结论 | 对所有 690 个 TF 靶标系统运行 shape 基序发现，报告发现率 | Results 图 4 |
| shape 特征由 DNase 预计算，非模型学习 | 模型学到的「shape 表征」受限于 DNAShapeR 的近似精度；真实体内结构可能不同 | 若 DNAShapeR 预测不准，则 shape 分支学到的模式可能是伪影 | 使用分子动力学模拟或实验结构数据交叉验证 shape 基序 | Methods Shape inputs 节 |
| 未与现有 shape-aware 模型（如 CNN 直接以 shape 为输入的先前工作）对比 | 基线仅对比序列-only 模型，未对比其他 shape 整合策略 | 无法判断双分支架构是否优于更简单的 shape 整合方法 | 增加基线：单分支 shape-only、序列+shape 拼接单分支等 | Results 图 1b |
| 归因比例分析（0.269）的生物学解释模糊 | 作者将稳定比例解释为「模型一致利用 shape」，但也可解释为 shape 分支学到的是序列分支的线性变换 | 若 shape 分支只是序列的线性函数，则「独立可解释性」不成立 | 检查 shape 分支与序列分支表征的相关性/互信息 | Results 图 4a |
| 未报告超参数搜索的具体空间和计算成本 | 无法评估该方法的可复现性和资源需求 | 影响方法实用性评估 | 补充超参数搜索细节和计算资源报告 | Supp. fig. 1 |

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **双分支输入设计作为可解释性工具**：将生物学先验特征（如 DNA shape）作为独立输入通道而非让模型隐式学习，使得归因分析可以直接回答「结构如何贡献于预测」。迁移到 TF–DNA 互作课题：可尝试将其他结构特征（如 DNA 弯曲度、柔韧性、静电势）或表观遗传特征（甲基化、核小体占位）作为额外输入通道，实现多维度可解释性。

2. **归因比例分析（shape:sequence ≈ 0.269）**：通过比较不同输入模态的归因总量，可量化不同生物学机制在预测中的相对权重，并识别偏离总体趋势的异常 TF（可能具有独特结合机制）。迁移：对 TF 家族进行系统归因比例分析，可发现结构依赖型 vs 序列依赖型 TF 的分类学。

3. **连续特征离散化适配现有工具**：将连续 shape 归因值转换为四分位数 one-hot 编码后输入 TF-MoDISco，成功将专为序列设计的基序发现工具扩展到结构特征。迁移：其他连续特征（如 ChIP 信号强度、进化保守性分数）也可用此策略适配现有基序发现工具。

4. **置换检验作为特征重要性评估**：通过跨样本置换 shape 特征评估其独立贡献，是一种简单有效的特征重要性评估方法。迁移：在 TF–DNA 结合预测中，可对不同类型的结构特征分别做置换检验，建立特征重要性排序。

5. **超参数搜索对多模态输入的关键性**：原始单模态超参数（滤波器长度 4、450 kernels）经搜索后显著提升 shape 分支利用率（贡献比 0.101 → 0.228）。迁移：多模态模型需要针对每个输入模态单独调优，不能直接沿用单模态最优配置。

6. **shape 基序与序列基序的共现分析**：通过检查 shape 基序与序列基序的相对位置（如 MafK 中 ProT 基序位于序列基序侧翼），可揭示结构特征如何调节序列基序的结合亲和力。迁移：对任意 TF，可系统分析其 shape 基序与序列基序的空间关系，建立「结构-序列协同」模型。

7. **激活分布的空间分析**：对比序列分支与 shape 分支激活在基因组位置上的分布（如 Myc-Max 中序列分支集中于 E-box、shape 分支弥散于侧翼），可揭示不同特征在结合位点中的功能分工。迁移：此方法可推广到其他 TF 二聚体或复合物，分析各亚基的序列/结构贡献。

## 15 与已有知识连接

- **DeepSEA / DeeperDeepSEA**：本文模型架构直接基于 DeeperDeepSEA 扩展，属于同一技术谱系。DeepSEA 首次将 CNN 应用于基因组调控预测，DeeperDeepSEA 加深了网络结构。本文的贡献在于输入模态的扩展而非架构创新。
- **DNAShapeR / DNAShape 数据库**：本文使用的五种 shape 特征（MGW、HelT、ProT、Roll、EP）来自 DNAShapeR 工具，该工具基于五核苷酸滑动窗口的蒙特卡洛模拟预测 DNA 结构。此前研究（如 Samee et al. 2019）已用统计方法发现 shape 基序在 TF 结合中的富集，本文将其整合进深度学习框架。
- **TF-MoDISco**：由 Shrikumar et al. 开发的基序发现工具，原设计用于从深度学习模型的序列归因中提取基序。本文的创新在于将其适配到 shape 归因，扩展了该工具的应用范围。
- **Myc-Max 结合机制研究**：Guo et al. (2014) 和 Allevato et al. (2017) 的研究表明 Myc-Max 结合受染色质环境和侧翼序列影响，本文的 shape 分支激活分析为这一观点提供了计算模型层面的支持。
- **Shape readout 概念**：由 Rohs et al. 等提出的 TF-DNA 识别模型，认为 TF 通过识别 DNA 局部结构特征（而非仅碱基序列）实现结合特异性。本文是该概念在深度学习框架中的直接实现。
- **可解释性方法谱系**：本文属于「设计可解释模型」路线（与「事后解释」相对），与 Puffin 等使用生物学约束核的模型思路一致，但本文通过输入模态分离实现可解释性，而非通过核设计。

## 16 研究想法

> 标题：Agent 生成的研究候选

**候选 1：TF 家族级别的 shape 依赖度系统分析**
- **来源局限/观察**：本文发现 MafK 偏离 shape:sequence 归因比例总体趋势，但未系统分析所有 TF。
- **核心假设**：不同 TF 家族（如 bZIP、C2H2、homeodomain）对 shape 特征的依赖程度存在系统性差异，且与 TF 的 DNA 结合结构域类型相关。
- **增量**：对 690 个 TF 靶标计算 shape:sequence 归因比例，按 TF 家族聚类，建立「结构域类型 → shape 依赖度」的映射。
- **初步方法**：使用 DeepShape 预训练模型，对每个 TF 靶标计算归因比例；用 TF 结构域注释（如 Pfam、CIS-BP）进行关联分析。
- **验证方式**：与已知结构生物学数据（如 PDB 中 TF-DNA 复合物结构）交叉验证；对预测为高 shape 依赖的 TF 进行实验验证（如 EMSA 突变分析）。
- **创新状态**：unverified

**候选 2：动态 shape 特征替代静态预测**
- **来源局限/观察**：作者承认使用静态 shape 预测是局限，未考虑 DNA 动态构象。
- **核心假设**：使用分子动力学（MD）模拟生成的 ensemble shape 特征（而非单一静态预测）可提升模型对 shape 敏感型 TF 的预测性能。
- **增量**：将 MD 模拟纳入 shape 特征生成流程，比较静态 vs. ensemble shape 特征对预测性能和可解释性的影响。
- **初步方法**：对代表性 TF 结合位点运行短时 MD 模拟，提取 shape 特征分布（均值、方差）；将 ensemble 特征作为输入训练 DeepShape 变体。
- **验证方式**：在保留测试集上比较 AUROC/AUPRC；检查 ensemble 特征是否产生更清晰的 shape 基序。
- **创新状态**：unverified

**候选 3：shape 基序的跨细胞类型保守性分析**
- **来源局限/观察**：本文在多个细胞类型上训练模型，但未分析 shape 基序的细胞类型特异性。
- **核心假设**：某些 shape 基序在多个细胞类型中保守（反映 TF 的内在结构偏好），而另一些具有细胞类型特异性（反映染色质环境差异）。
- **增量**：对每个 TF 靶标在不同细胞类型中提取 shape 基序，计算基序相似度矩阵，识别保守 vs 特异的 shape 基序。
- **初步方法**：使用 DeepShape 对同一 TF 在不同细胞类型的靶标进行归因分析，用 TF-MoDISco 提取 shape 基序，计算基序间相似度。
- **验证方式**：保守 shape 基序是否对应已知的结构生物学特征（如窄小沟区域）；细胞类型特异 shape 基序是否与染色质可及性数据相关。
- **创新状态**：unverified

**候选 4：shape 特征作为序列基序的「上下文调制器」的显式建模**
- **来源局限/观察**：本文的模型将序列和 shape 并行处理，但未显式建模二者的交互（如 shape 如何调制序列基序的识别）。
- **核心假设**：在序列基序附近特定位置（如 ±2 bp 侧翼）的 shape 特征对结合亲和力的调制作用可被显式参数化，且这种调制具有方向性（如特定 shape 特征增强/抑制结合）。
- **增量**：设计一个注意力机制或门控单元，使序列基序的表示被局部 shape 特征调制，而非简单拼接。
- **初步方法**：在 DeepShape 的拼接层引入门控注意力，学习 shape 特征对序列特征的调制权重；分析学习到的调制模式。
- **验证方式**：与标准拼接模型对比性能；检查调制权重是否与已知的 shape-readout 机制一致（如 MEF2A 的小沟识别）。
- **创新状态**：unverified

**候选 5：shape 感知的变异效应预测**
- **来源局限/观察**：本文聚焦于结合预测和可解释性，未涉及变异效应预测。
- **核心假设**：在序列变异效应预测中引入 shape 特征变化（而非仅序列变化）可提升对致病性非编码变异的预测能力，特别是对 shape 敏感型 TF。
- **增量**：将 DeepShape 扩展到变异效应预测，比较「仅序列变化」vs.「序列+shape 变化」对预测的影响。
- **初步方法**：对 eQTL/GWAS 变异位点计算参考和变异等位基因的序列和 shape 特征，输入 DeepShape 比较预测变化；评估与实验数据（如 MPRA、STARR-seq）的一致性。
- **验证方式**：在已知功能变异数据集上评估 AUC；检查 shape 特征变化是否在功能变异中显著更大。
- **创新状态**：unverified