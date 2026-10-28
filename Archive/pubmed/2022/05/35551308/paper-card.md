## 01 基本信息

- **标题**：Sequence-based modeling of three-dimensional genome architecture from kilobase to chromosome scale
- **作者与单位**：Zhou, Jian（University of Texas Southwestern Medical Center）
- **期刊/预印本平台**：Nature Genetics
- **年份**：2022
- **论文类型**：研究论文（Research Article）
- **领域**：三维基因组学 × 深度学习
- **关键词**：3D genome architecture, deep learning, sequence-based prediction, chromatin compartments, TADs, CTCF, enhancer-promoter interactions, Polycomb, structural variants
- **DOI/arXiv 号**：10.1038/s41588-022-01065-4
- **代码**：https://github.com/jzhoulab/orca
- **数据**：4DNFI9GMP2J8（H1-ESC micro-C）、4DNFI643OYP9（HFF micro-C）、4DNFILP99QJS（HCT116 cohesin-depleted Hi-C）；Zenodo 数据集（见 Data Availability）
- **阅读日期**：未提供
- **在该课题方向中的位置**：本文是「序列 → 3D 基因组结构」端到端深度学习的代表性工作，将预测范围从亚兆碱基（Akita/DeepC 的 ~1 Mb）扩展到全染色体尺度（256 Mb），并系统验证了 CTCF、Polycomb、增强子-启动子等多种互作类型的序列可预测性。对于 TF–DNA 互作课题，本文提供了「序列基序 → 特定类型染色质互作」的可迁移建模框架，尤其是 POU5F1∷SOX2 与 AP-1 基序对细胞类型特异性互作的预测能力。

---

## 02 一句话总结

本文提出多尺度深度学习框架 Orca，以最高 256 Mb 的基因组序列为输入，预测从 4 kb 到全染色体尺度的 Hi-C 类型互作矩阵，并在微 C 数据上达到 0.78–0.85（H1-ESC）与 0.73–0.79（HFF）的 Pearson 相关，且能准确预测多种实验验证的结构变异效应；通过虚拟筛选发现 TSS 序列是染色质 A 区室的驱动因素。

---

## 03 研究问题

- **具体问题**：能否仅从 DNA 序列预测多尺度（kb 到整条染色体）的 3D 基因组结构？具体包括 TAD、A/B 区室、CTCF 介导、Polycomb 介导、增强子-启动子互作等。
- **为什么重要**：3D 基因组结构是基因表达调控、DNA 复制与修复的关键环节；若能直接从序列预测结构，则可解释序列变异（尤其是结构变异）如何通过改变 3D 结构导致疾病表型。
- **现有方法不足**：Akita 和 DeepC 仅能预测 ~1 Mb 以内的互作，无法覆盖区室尺度和染色体尺度；且未系统评估非 CTCF 类型互作的序列可预测性。
- **精确研究问题（Can...?）**：Can a deep learning model trained on genomic sequence alone predict 3D genome interactions from kilobase to whole-chromosome scale, including cell-type-specific non-CTCF interactions, and accurately predict structural variant effects?

---

## 04 背景与发展脉络

> 注：此脉络基于本文 Introduction 与 Discussion 的叙述，属「仅本文框架」，未经外部系统综述核验。

1. **3C/Hi-C 技术成熟期**：Hi-C、micro-C 等高通量染色质构象捕获技术提供了从 kb 到染色体尺度的互作图谱（Dekker et al., 2002; Lieberman-Aiden et al., 2009; Hsieh et al., 2020 等）。
2. **区室与 TAD 的发现**：A/B 区室（~Mb 级）与 TAD（100 kb–1 Mb）被确认为 3D 基因组的基本组织单元；CTCF/cohesin 介导的 loop extrusion 机制解释了 TAD 形成。
3. **序列深度学习的兴起**：DeepSEA、Basenji 等模型证明序列可预测调控元件活性；Akita（2020）与 DeepC（2020）首次实现从序列预测亚 Mb 级互作。
4. **本文位置**：Orca 将预测范围扩展至 256 Mb（超过人类最长染色体），引入多分辨率级联解码器与水平 checkpointing 技术，并首次系统验证非 CTCF 类型互作（Polycomb、增强子-启动子）的序列可预测性，同时提出 TSS 驱动 A 区室的序列模型。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|---|---|---|---|
| 预测范围受限 | 现有模型（Akita、DeepC）仅覆盖 ~1 Mb 以内互作 | 输入序列长度受限于 GPU 内存与模型设计 | Introduction 第 3 段 |
| 缺乏区室尺度预测 | 无法从序列预测 A/B 区室 | 区室形成涉及 >1 Mb 的序列上下文，超出既有模型输入范围 | Introduction 第 3 段；Results 图 1 |
| 非 CTCF 互作不可预测 | 增强子-启动子、Polycomb 互作的序列决定因素未知 | 缺乏能捕捉这些互作的高分辨率训练数据与模型架构 | Introduction 第 2 段；Results 图 3 |
| 结构变异效应预测困难 | 大片段 SV（>1 Mb）无法用现有模型评估 | 输入窗口不足以覆盖 SV 的完整序列上下文 | Introduction 第 3 段；Results 图 2 |
| 训练内存瓶颈 | 长序列输入导致内部表示超出 GPU 内存 | 标准反向传播需存储所有层激活 | Methods "Scaling hierarchical deep learning model training" |
| 序列基序与互作机制关联不明 | 难以从模型归因到具体 TF 基序 | 缺乏系统化的虚拟筛选方法 | Results 图 3c–d |

---

## 06 核心思想

### 1) 表面方法
- 多尺度级联架构：编码器将最长 256 Mb 序列编码为 9 个分辨率（4 kb 至 1,024 kb）的表示；解码器逐级预测互作矩阵，低分辨率预测作为高分辨率预测的上下文输入。
- 三阶段训练：先训练 1 Mb 模块（含辅助染色质特征预测任务），再训练 1–32 Mb 模块，最后训练 32–256 Mb 模块（含染色体间互作）。
- 虚拟筛选工具：多重体内诱变（multiplexed in silico mutagenesis）与序列插入筛选（insertion screen）。

### 2) 核心洞察
- **多尺度级联是扩展预测范围的关键**：通过「缩放」式级联，低分辨率全局上下文引导高分辨率局部预测，使模型能同时捕捉 TAD 级与区室级结构。
- **TSS 是 A 区室的序列驱动因素**：在 cohesin 耗竭模型中，TSS 序列的插入足以在 B 区室环境中建立 A 区室互作模式。
- **细胞类型特异性互作由特定 TF 基序编码**：POU5F1∷SOX2（ESC）与 AP-1（成纤维细胞）基序的破坏分别对各自细胞类型的互作有最大影响。

### 3) 可能的普适教训 [Analysis]
- 对于 TF–DNA 互作建模：**互作的序列决定因素可通过「虚拟筛选 + 基序富集」系统解码**，而不必依赖可解释性方法（如 saliency map）。
- 对于多尺度生物系统：**级联多分辨率架构是处理「局部机制 + 全局上下文」问题的通用设计模式**，可迁移至其他长程互作预测任务。
- 对于结构变异解读：**序列模型的预测能力使「变异 → 3D 结构变化 → 表型」的因果链可在计算机中快速预筛**。

---

## 07 方法总览

- **输入**：DNA 序列（one-hot 编码），最长 256 Mb；多染色体输入支持染色体间互作预测。
- **输出**：多分辨率互作矩阵（250 × 250），覆盖 4 kb（1 Mb 窗口）至 256 Mb（1,024 kb 分辨率）的互作分数，表示为 log fold over distance-based background。
- **编码器**：层次化多分辨率序列编码器，由 1D 残差卷积块与最大池化组成；第一段（至 4 kb 分辨率）架构改编自 Sei。
- **解码器**：级联多尺度解码器，每个分辨率对应一个 2D 残差卷积块；低分辨率预测经上采样后作为高分辨率解码器的输入。
- **辅助任务**：4 kb 分辨率编码同时预测 DNase-seq、CTCF、组蛋白修饰 peak（辅助损失）。
- **训练**：三阶段训练；损失函数为主任务 MSE + 辅助任务 BCE；优化器为 Adam（momentum 0.98）；水平 checkpointing 技术降低内存。
- **推理**：前向与反向互补序列预测取平均；多尺度预测通过逐级 zoom-in 实现。
- **工具**：PyTorch 实现；代码与模型公开于 GitHub；Web 服务器 https://orca.zhoulab.io。

**文字流程**：  
输入序列 → one-hot 编码 → 层次化编码器（逐级池化，生成 4 kb 至 1,024 kb 表示）→ 顶层解码器预测最大尺度互作 → 逐级下采样解码器，结合上一级预测与当前分辨率序列表示 → 输出各尺度互作矩阵 → 后处理（对称化、反向互补平均）。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|---|---|---|---|---|---|
| 层次化序列编码器 | 将原始序列转换为多分辨率表示 | 不同尺度的 3D 结构依赖不同粒度的序列特征 | 输入：one-hot 序列（≤256 Mb）；输出：4 kb–1,024 kb 分辨率表示 | Results 图 1；Methods 架构描述 | 预期：无法捕捉跨尺度序列依赖，长程互作预测失效 [预期] |
| 级联多尺度解码器 | 逐级预测互作矩阵，低分辨率预测引导高分辨率 | 长程结构需要全局上下文约束局部预测 | 输入：当前分辨率序列表示 + 上一级预测；输出：250 × 250 互作矩阵 | Results 图 1a–c；消融见 Supplementary Table 1 | 预期：高分辨率预测失去全局上下文，TAD 边界定位精度下降 [预期] |
| 辅助染色质特征预测头 | 预测 DNase、CTCF、组蛋白修饰 peak | 提供调控特征的监督信号，改善序列表示 | 输入：4 kb 分辨率编码；输出：peak 概率 | Supplementary Tables 1, 2 显示性能提升 | 实测：移除后主任务性能下降（Supplementary Table 1）[实测] |
| 水平 checkpointing | 降低训练内存 | 256 Mb 输入的内部表示远超 GPU 内存 | 输入：层激活；输出：梯度 | Methods "Scaling hierarchical deep learning model training" | 预期：无此技术则无法训练 256 Mb 模型 [预期] |
| 多重体内诱变筛选 | 系统评估每个 10 bp 位点的结构影响 | 识别驱动互作的序列基序 | 输入：1 Mb 窗口序列；输出：每个 10 bp 位点的结构影响分数 | Results 图 3；Extended Data Fig. 7 | 不适用（分析工具，非模型组件） |
| 序列插入筛选 | 评估外源序列在异位点的区室活性 | 测试序列是否足以驱动区室转换 | 输入：插入序列 + 目标位点；输出：32 Mb 结构影响分数 | Results 图 4 | 不适用（分析工具，非模型组件） |

---

## 09 关键公式符号

本文未提供显式数学公式；以下为方法中隐含的关键计算：

1. **主损失（MSE）**：
   \[
   L_{\text{main}} = \frac{1}{N} \| \text{prediction} - \text{target} \|_F^2
   \]
   其中 prediction 和 target 均为 250 × 250 矩阵，N 为矩阵元素数，\(\|\cdot\|_F\) 为 Frobenius 范数。

2. **辅助损失（BCE）**：
   \[
   L_{\text{aux}} = \frac{1}{N} \left[ \text{target}_c \cdot \log(\text{prediction}_c) + (1 - \text{target}_c) \cdot \log(1 - \text{prediction}_c) \right]
   \]
   其中 target_c 为二值染色质特征标签（DNase、CTCF、组蛋白修饰 peak）。

3. **距离背景归一化**：互作分数定义为 log fold over distance-based background，即：
   \[
   \text{score}_{ij} = \log\left( \frac{\text{observed}_{ij}}{\text{expected}_{|i-j|}} \right)
   \]
   其中 expected 为同距离的平均互作强度（distance-decay 曲线）。

4. **结构影响分数（1 Mb）**：平均绝对 log fold 互作变化：
   \[
   \text{Impact}(s) = \frac{1}{N} \sum_{j} | \text{pred}_{\text{mut}}(s, j) - \text{pred}_{\text{wt}}(s, j) |
   \]
   其中 s 为突变位点，j 遍历窗口内所有位点。

5. **32 Mb 结构影响分数**：同理，但互作窗口为 32 Mb，用于区室级效应评估。

---

## 10 实验设计与证据链

### 数据集与评测协议
- **训练数据**：H1-ESC 与 HFF 的 micro-C 数据（4DN 编号 4DNFI9GMP2J8、4DNFI643OYP9）；HCT116 cohesin 耗竭 Hi-C（4DNFILP99QJS）。
- **参考基因组**：GRCh38/hg38。
- **训练/验证/测试划分**：训练集为除 chr8、9、10 外所有染色体；验证集 chr8；测试集 chr9、10。
- **指标**：Pearson 相关（预测 vs 观测互作矩阵）；背景扣除后 Pearson（与 Akita 比较时）。
- **基线**：Akita（仅 1 Mb 尺度比较）。
- **计算资源**：4× NVIDIA Tesla V100 32GB GPU。

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|---|---|---|---|---|---|---|
| 多尺度预测精度 | Orca 能在所有尺度准确预测互作 | 测试集 chr9、10；9 个分辨率 | H1-ESC Pearson 0.78–0.85；HFF 0.73–0.79 | 序列足以预测多尺度 3D 结构 | 未与所有现有模型系统比较 | Results 图 1c；Extended Data Fig. 1 |
| 与 Akita 比较（1 Mb） | Orca 在亚 Mb 尺度不逊于 Akita | 共享测试集；背景扣除 Pearson | Orca 在 H1-ESC 与 HFF 均优于 Akita | Orca 在局部尺度同样具有竞争力 | 比较仅在 1 Mb 尺度 | Supplementary Figs. 4, 5 |
| 转座子插入效应预测 | Orca 能预测 2 kb 插入的 TAD 边界效应 | 14 个插入位点；预测 vs 实验 in situ Hi-C | 余弦相似度 0.89（H1-ESC）、0.76（HFF），P < 1×10⁻⁴ | 模型捕捉了插入序列的局部结构效应 | 样本量有限（14 个位点） | Results 图 2；Extended Data Fig. 5 |
| 大片段 SV 效应预测 | Orca 能预测 Mb 级 SV 的区室与 TAD 变化 | 40.5 Mb 倒位、0.9–1.8 Mb 缺失/重复/倒位 | 预测与实验 4C/Hi-C 一致 | 模型可用于大片段 SV 的结构效应预测 | 未做定量指标，仅定性一致 | Results 图 2；Supplementary Figs. 8–14 |
| 多重体内诱变筛选 | 非 CTCF 基序对局部互作有贡献 | 全基因组 10 bp 位点筛选 | POU5F1∷SOX2 在 H1-ESC 富集，AP-1 在 HFF 富集 | 细胞类型特异性 TF 基序驱动局部互作 | 未验证因果性（仅关联） | Results 图 3c–d；Supplementary Tables 4, 5 |
| 插入序列区室活性筛选 | TSS 序列足以驱动 A 区室 | 12,800 bp 插入序列；32 Mb 预测 | TSS 附近序列显示最强 A 区室活性 | TSS 是 A 区室的序列驱动因素 | 未在体内验证插入效应 | Results 图 4；Extended Data Fig. 8 |
| 序列置换分析 | A 区室活性依赖特定序列特征 | 随机置换 vs 原始序列 | 置换后 A 区室活性显著降低 | 序列信息（而非组成）驱动区室活性 | 未明确具体序列特征 | Results 图 4e |
| 辅助任务消融 | 辅助染色质特征预测提升主任务 | 有/无辅助损失 | 移除辅助任务后性能下降 | 多任务学习有益 | 未报告下降幅度 | Supplementary Tables 1, 2 |

---

## 11 结论正确解读

- **任务范围**：本文预测的是 **Hi-C 类型互作矩阵**（log fold over distance-decay background），而非绝对接触频率；预测对象是 **细胞群体平均结构**，不涉及单细胞 3D 结构。
- **输入限制**：模型仅使用 DNA 序列，不包含 CTCF ChIP-seq、DNase 等实验数据作为输入（仅作为辅助训练标签）。因此预测反映的是「序列编码的潜在结构信息」，而非当前细胞状态。
- **端到端状态**：模型是端到端训练的（序列 → 互作矩阵），但训练数据来自特定细胞类型（H1-ESC、HFF、HCT116），跨细胞类型泛化需重新训练或微调。
- **算力成本**：训练需 4× V100 GPU，三阶段训练总步数约 65 万步；推理时 256 Mb 输入需水平 checkpointing，单次推理成本较高。
- **历史数据依赖**：模型依赖 micro-C/Hi-C 数据质量；低覆盖区域（着丝粒、异染色质）预测不可靠。
- **最难情形**：高度重复区域（如卫星 DNA）无法从 Hi-C 读取中可靠测量，模型预测无法验证；单一位点或罕见变异的效应预测未做系统评估。
- **不确定性**：本文未报告预测的置信区间或不确定性估计；所有预测为点估计。
- **有边界的复述**：在 H1-ESC、HFF 和 HCT116 三种细胞类型中，Orca 能从序列预测 4 kb 至 256 Mb 尺度的互作矩阵，准确率（Pearson 0.73–0.85）足以复现已知 SV 的结构效应，并支持「TSS 驱动 A 区室」的序列模型；但该结论限于训练数据覆盖的细胞类型和基因组区域，不构成对通用 3D 结构预测的证明。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 预测与观测在某些区域存在差异 | 部分区域预测与实验不符，超出技术噪声可解释范围 | 更高分辨率数据与改进模型可能缩小差距 | Discussion 第 1 段 |
| 高度重复区域无法评估 | 卫星 DNA 等区域缺乏可靠的 Hi-C 测量 | 长读长测序与完整基因组组装可能解决 | Discussion 第 1 段；Data Availability |
| 序列模式与机制关联为相关性 | 虚拟筛选识别的基序与结构变化的关联不一定是因果关系 | 需要实验验证（如 CRISPR 编辑） | Discussion 第 2 段 |
| 模型可能无法学习单一位点特异机制 | 机器学习方法捕捉的是全基因组重复出现的模式，单一位点或罕见机制可能无法学习 | 更高分辨率数据与改进模型可能缩小差距 | Discussion 第 2 段 |
| 训练数据细胞类型有限 | 仅训练了 H1-ESC、HFF、HCT116 三种细胞类型 | 更多细胞类型与分化时间序列数据可提升泛化 | Discussion 第 3 段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| 预测指标仅用 Pearson 相关 | Pearson 对全局强度缩放不敏感，可能高估局部结构预测能力 | 若模型仅捕捉距离衰减趋势，Pearson 可能虚高 | 使用尺度无关指标（如 SCC、AUC for loop 检测）或分距离段评估 | Results 图 1c 未报告其他指标 |
| 与 Akita 比较仅在 1 Mb 尺度 | Akita 本身设计为 1 Mb 窗口，跨尺度比较可能不公平 | 需要明确 Orca 在亚 Mb 尺度的增量优势 | 在相同输入/输出设置下进行公平基准测试 | Supplementary Figs. 4, 5 未报告训练数据差异 |
| SV 效应验证为定性比较 | 40.5 Mb 倒位等案例仅展示预测与实验「一致」，无量化指标 | 定性一致可能掩盖定量偏差 | 计算预测与实验互作矩阵的量化相似度（如 Pearson、Jaccard） | Results 图 2 未提供数值 |
| 虚拟筛选的「结构影响分数」阈值未明确 | 0.01 和 0.1 的阈值选择依据未说明 | 不同阈值可能改变基序富集结论 | 进行阈值敏感性分析 | Results 图 3 未报告阈值扫描 |
| TSS 驱动 A 区室的结论基于插入筛选 | 插入序列可能引入非生理的染色质环境 | 需要内源位点敲除/敲入验证 | 在原生位点删除 TSS 后检测区室变化 | Results 图 4 未包含内源验证 |
| 辅助任务仅用 peak 二值标签 | 连续信号（如 DNase 强度）可能包含更多信息 | 二值化可能丢失定量信息 | 尝试回归任务或量化标签 | Methods 未说明为何选择二值标签 |
| 水平 checkpointing 增加训练时间 | 重计算前向传播增加计算开销 | 可能限制模型在资源有限实验室的复现 | 报告训练时间与标准 checkpointing 的对比 | Methods 未提供时间对比 |

---

## 14 学到什么

> 标题：Agent 提炼的知识候选

1. **多尺度级联架构（可迁移）**：对于 TF–DNA 互作预测，若目标是从序列预测「长程调控互作」（如增强子-启动子），可借鉴 Orca 的「低分辨率全局上下文 + 高分辨率局部细化」级联设计，而非单尺度模型。
2. **虚拟筛选作为机制发现工具（可迁移）**：Orca 展示了「大规模体内诱变 + 基序富集」可从黑盒模型中提取可检验的序列机制假设。该策略可直接迁移至 TF–DNA 互作研究：对目标 TF 的结合位点进行系统突变，用模型预测互作变化，再富集受影响基序。
3. **辅助任务多任务学习（可迁移）**：同时预测染色质特征（DNase、CTCF、组蛋白修饰）可提升主任务性能。对于 TF–DNA 互作模型，可考虑将 TF ChIP-seq 或 DNase 足迹作为辅助任务。
4. **cohesin 耗竭作为「消融实验」**：训练 cohesin 耗竭数据以分离 CTCF 依赖与非依赖的序列决定因素，是「机制解耦」的巧妙设计。类似地，可训练 TF 敲除数据以分离特定 TF 的贡献。
5. **序列置换作为对照**：插入筛选中的随机置换对照可区分「序列信息」与「序列组成」的贡献，是虚拟筛选实验设计的必要对照。
6. **结构变异效应预测的工程流程**：通过「参考序列 vs 变异序列」的预测对比来评估 SV 的结构效应，该流程可迁移至 TF 结合位点变异的功能预测。
7. **水平 checkpointing（工程可迁移）**：对于超长序列（如整个基因座）的深度学习模型，水平 checkpointing 是解决 GPU 内存瓶颈的实用技术。

---

## 15 与已有知识连接

- **Akita（Fudenberg et al., 2020, PNAS）**：首个从序列预测 1 Mb 内互作的 CNN 模型。Orca 在架构上扩展了 Akita 的「分箱互作预测」思路，但引入多尺度级联与更大输入窗口。两者共享「distance-decay 背景归一化」策略。
- **DeepC（Schwarzer et al., 2020, NAR）**：同样预测 Hi-C 互作，但限于 1 Mb 窗口。Orca 的 256 Mb 输入是数量级提升。
- **Sei（Chen et al., 2021, Nat. Genet.）**：Orca 编码器第一段改编自 Sei 的架构，Sei 本身是序列 → 染色质特征的模型。这提示「序列 → 调控特征 → 3D 结构」的层级建模思路。
- **CTCF loop extrusion 模型（Fudenberg et al., 2016; Sanborn et al., 2015）**：Orca 对 CTCF 基序的敏感性与此机制一致，可作为机制解释框架。
- **TAD 边界与 housekeeping 基因/TSS 的关联（Dixon et al., 2012; Rao et al., 2014）**：Orca 的「TSS 驱动 A 区室」结论与此类观察一致，但提供了序列层面的可计算模型。
- **相分离与区室化模型（Hnisz et al., 2017）**：Orca 的 TSS 驱动模型与「转录活性区域促进 A 区室」的相分离观点相容，但本文未直接讨论。
- **对 TF–DNA 互作课题的启示**：Orca 证明特定 TF 基序（POU5F1∷SOX2、AP-1）的序列变异可预测性地改变局部互作，这为「TF 结合 → 3D 结构变化」提供了计算框架，可与 ChIP-seq、HiChIP 等实验数据结合验证。

---

## 16 研究想法

> 标题：Agent 生成的研究候选

### 候选 1：TF 基序变异的 3D 结构效应预测
- **名称**：TF-Mut3D：基于 Orca 的 TF 结合位点系统突变筛选
- **来源局限/观察**：Orca 的虚拟筛选显示单基序破坏可改变局部互作，但未系统覆盖所有 TF。
- **核心假设**：对任意细胞类型特异性 TF，其结合基序的系统突变可预测性地改变局部 3D 互作，且效应大小与 TF 的染色质组织功能相关。
- **初步方法**：选取 50–100 个已知 TF（如 OCT4、NANOG、CTCF、AP-1 亚基），对每个 TF 的全基因组结合位点进行 10 bp 破坏突变，用 Orca 预测互作变化，计算每个 TF 的「结构影响谱」。
- **验证方式**：与现有 HiChIP、PLAC-seq 数据比较，检验预测的互作变化是否与实验观察一致。
- **创新状态**：unverified

### 候选 2：cohesin 耗竭与 TF 依赖互作的解耦
- **名称**：Loop-Independent TF Interaction Atlas
- **来源局限/观察**：Orca 的 cohesin 耗竭模型消除了 TAD 但保留区室，可用于分离 CTCF 依赖与非依赖的 TF 互作。
- **核心假设**：存在一类「cohesin 非依赖、TF 依赖」的互作，其序列决定因素可被 cohesin 耗竭模型识别。
- **初步方法**：对比正常与 cohesin 耗竭 Orca 模型的虚拟筛选结果，识别在耗竭模型中仍保持结构影响的 TF 基序；用这些基序构建「非 loop 互作」预测模型。
- **验证方式**：与 cohesin 耗竭前后的 Hi-C 数据比较，检验预测的「非依赖互作」是否在实验中被保留。
- **创新状态**：unverified

### 候选 3：TSS 驱动的 A 区室序列模型
- **名称**：TSS-Compartment Grammar：从序列到区室的生成模型
- **来源局限/观察**：Orca 显示 TSS 是 A 区室驱动因素，但未解析具体序列特征。
- **核心假设**：A 区室活性由 TSS 附近的特定序列组合（如启动子强度、CpG 含量、TF 基序密度）决定，可被可解释模型捕捉。
- **初步方法**：从 Orca 的插入筛选结果中提取高活性与低活性序列，训练一个可解释的分类器（如 logistic regression 或决策树），识别关键序列特征。
- **验证方式**：在独立细胞类型中验证特征的泛化性，并与实验（如 CRISPR 删除 TSS）比较。
- **创新状态**：unverified

### 候选 4：跨物种 3D 结构预测的迁移学习
- **名称**：Cross-Species 3D Genome Transfer
- **来源局限/观察**：Orca 仅训练了人类细胞；小鼠等模式生物的 3D 结构预测尚缺。
- **核心假设**：人类训练的 Orca 模型可通过迁移学习适应小鼠，且迁移后的模型能识别保守的 3D 结构序列特征。
- **初步方法**：用小鼠 micro-C 数据微调 Orca，比较迁移学习与从头训练的性能；分析迁移后模型关注的序列特征是否与人类保守。
- **验证方式**：在小鼠 holdout 染色体上评估预测精度，并与人类模型的跨物种直接预测比较。
- **创新状态**：unverified

### 候选 5：单细胞 3D 结构的序列预测
- **名称**：sc-Orca：从序列到单细胞结构变异的预测
- **来源局限/观察**：Orca 预测的是群体平均结构，无法捕捉细胞间异质性。
- **核心假设**：单细胞 Hi-C 的结构变异部分可由序列编码的「结构倾向性」解释，且该倾向性可被 Orca 类模型捕捉。
- **初步方法**：将单细胞 Hi-C 数据聚合为「结构倾向性分数」，训练 Orca 的变体预测该分数；评估预测的细胞间变异解释率。
- **验证方式**：与单细胞 Hi-C 实验数据比较，检验预测的倾向性是否与观察到的细胞间变异相关。
- **创新状态**：unverified