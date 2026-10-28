## 01 基本信息

- **标题**：DNA-binding domain-aware classification enables systematic annotation of the regulatory genome
- **作者**：Christian Ickes; Cigdem Hazal Timucin; Bendix Christian Harms; Umut Akgül; Íñigo Vicente-Hernández; Ivan Bogeski; Tim Beißbarth; Martin Haubrock
- **单位**：University of Göttingen（哥廷根大学，德国）
- **期刊/平台**：bioRxiv（预印本）
- **年份**：2024
- **论文类型**：方法学 + 应用研究（预印本）
- **领域**：调控基因组学、转录因子结合位点预测、深度学习
- **关键词**：TF–DNA 互作、DNA-binding domain (DBD)、DNABERT、多分类、调控基因组注释、TFBS 预测
- **DOI/ID**：10.1101/2024.12.20.629625
- **代码**：https://gitlab.gwdg.de/MedBioinf/generegulation/tfclasspredict（另有 PyPI 发布）
- **数据**：https://doi.org/10.5281/zenodo.21278466（含预编译基因组轨道）
- **阅读日期**：未提供
- **在本课题方向中的位置**：本文聚焦 TF–DNA 结合机制，提出以 DBD-class 为分类单元的深度学习框架（DNABERT 微调），将 TFBS 预测从单 TF 二分类重构为跨 23 个 DBD-class 的多分类问题，直接回应了共享 DBD 结构导致结合特异性重叠的生物学问题，属于「TF–DNA 互作 × 深度学习」方向，且其 DBD-class 抽象层对物理模拟（如 MD/对接）中如何定义结合特异性层级具有参考价值。

---

## 02 一句话总结

本文提出 TFClassPredict——一个基于 DNABERT 的多分类框架，将 TFBS 预测重构为 23 个 DBD-class 的判别任务，利用 DBD–DNA 共进化关系，在 21bp 序列上实现 DBD-class 级分类（Accuracy 87.3%，F1_macro 78.1%），并证明其可增强 PWM 流程、改善 3D 基因组互作预测，以及从 ATAC-seq 数据中恢复已知的免疫细胞谱系决定程序。

---

## 03 研究问题

- **具体问题**：给定一段 DNA 序列，能否可靠地判断哪个 DBD-class（而非具体哪个 TF）在该位点具有主导结合潜力？
- **为什么重要**：调控基因组注释的核心挑战是将顺式调控序列与正确的反式因子关联。由于大量 TF 共享 DBD 结构，其结合基序高度相似，单 TF 级别的分配在序列层面本质上是不确定的。DBD-class 级分类提供了一个生物学上有意义且统计上可处理的抽象层级。
- **现有方法不足**：
  - PWM 方法假设位置独立，无法建模高阶序列依赖和侧翼序列上下文；
  - 深度学习方法（CNN/RNN/Transformer）虽性能更优，但通常仍以单 TF 的 bound/unbound 二分类为框架，回避了竞争性结合问题；
  - 现有方法未显式利用 DBD 结构相似性作为分类层级。
- **精确研究问题（Can 问题）**：Can a DNABERT-based multi-class classifier, trained on high-confidence directly bound TFBSs and structured by DBD-class labels, reliably discriminate among 23 DBD-classes from 21bp DNA sequence alone, and does this DBD-class abstraction improve downstream regulatory genomics tasks?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文引言与讨论的叙述，属于「仅本文框架」，未经外部系统核验。

1. **PWM 时代（经典方法）**：以位置独立权重矩阵表示 TF 结合偏好，代表工具如 HOMER、FIMO。优点：可解释、计算快；局限：无法建模位置间依赖、侧翼序列效应、竞争性结合。
2. **深度学习时代（CNN/RNN）**：如 DeepBind、DanQ 等，从数据中学习非线性序列特征，性能优于 PWM。局限：通常以单 TF 为预测单元，忽略 DBD 共享导致的类别重叠；需要大量 per-TF 训练数据。
3. **基因组语言模型（Transformer）**：DNABERT 等基于 k-mer tokenization 的预训练模型，通过自注意力学习上下文表征，在多种调控任务上达到 SOTA。局限：直接用于 TFBS 预测时仍多沿用二分类范式。
4. **DBD 结构分类学（生物学基础）**：TFClass 数据库按 DBD 结构层级组织 TF，反映 DBD–DNA 共进化关系。已有研究表明 DBD 结构相似性可预测结合特异性相似性。
5. **本文主张的位置**：将 TFClass 的 DBD-class 层级引入深度学习分类框架，以 DBD-class 为标签空间，利用 DBD–DNA 共进化信号，实现「结构感知」的 TFBS 分类，并证明该抽象层在多种下游任务中的实用性。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 单 TF 级别 TFBS 分配本质模糊 | 同一序列可被多个 TF 的 PWM 匹配；ChIP-seq 峰中 motif 归属不确定 | 共享 DBD 结构的 TF 结合基序高度相似，序列信息不足以区分 | Introduction 第 1 段；Results 图 2b（FIMO 分类准确率低） |
| PWM 位置独立假设限制性能 | FIMO 在 DBD-class 分类任务上准确率低 | PWM 无法建模位置间依赖和上下文效应 | Results 图 2b；Discussion 第 1 段 |
| 二分类范式回避竞争性结合 | 现有深度学习方法仅回答「某 TF 是否结合」，不回答「哪个 TF 主导」 | 缺乏以 DBD 结构为层级的标签体系 | Introduction 第 2 段 |
| 低数据 TF 预测困难 | 部分 TF 的 ChIP-seq 数据稀少，per-TF 模型性能差 | 数据稀疏性在单 TF 粒度上无法克服 | Results 图 3c-d（DBD-class 池化缓解数据稀疏） |
| 下游分析噪声累积 | PWM 假阳性传播到 3D 基因组和 ATAC-seq 分析 | 单 TF 级预测的不确定性未在流程中显式处理 | Results 图 4a-b（过滤后准确率提升） |

---

## 06 核心思想

### 1) 表面方法
- 使用 DNABERT（6-mer tokenization）作为骨干模型，在 21bp 的 TFBS 序列上进行微调，输出 23 个 DBD-class 的多分类概率分布。
- 训练数据来自 UniBind 数据库的高置信直接结合 TFBS，按 TFClass 层级标注 DBD-class。
- 训练后应用于：(a) 对 PWM 预测结果进行后过滤；(b) 预测 3D 基因组互作；(c) 从 ATAC-seq 峰中推断 DBD-class 结合潜力。

### 2) 核心洞察
- **DBD-class 是序列与功能之间的「自然抽象层级」**：DBD 结构决定 DNA 识别特异性，且 DBD–DNA 共进化使得同一 DBD-class 内的 TF 共享可学习的序列语法。将分类目标从「哪个 TF」提升到「哪个 DBD-class」，既保留了生物学意义，又规避了单 TF 级别不可判定的问题。
- **多分类优于二分类**：将「结合 vs 不结合」重构为「属于哪个 DBD-class」的判别问题，迫使模型学习类间区分性特征，而非仅学习单类正例模式。
- **池化效应缓解数据稀疏**：将多个 TF 的 TFBS 按 DBD-class 合并，等效于数据增强，使低资源 TF 也能受益于同类其他 TF 的训练信号。

### 3) 可能的普适教训 [Analysis]
- 在生物序列分类中，标签体系的选择本身就是一种先验知识注入。选择一个与生物学机制对齐的抽象层级（如 DBD-class），可能比单纯增加模型容量更有效。
- 「竞争性判别」框架（discriminate each class against all others）比「独立二分类」更符合生物系统中多个因子竞争同一结合位点的真实图景。
- 对物理模拟（MD/对接）的启示：DBD-class 层级可作为定义结合特异性先验的合理粒度，减少因 TF 家族内细微差异导致的模拟目标模糊。

---

## 07 方法总览

- **输入**：21bp DNA 序列（来自 UniBind 高置信 TFBS，扩展至 21bp 窗口）
- **输出**：23 个 DBD-class 的概率分布（softmax）
- **骨干模型**：DNABERT（12 层 Transformer，自注意力，k-mer tokenization；k=6 为最优）
- **训练**：多分类交叉熵损失，Adam 优化器，最多 60 epochs，early stopping（验证损失 3 epochs 无改善则停止）；每类独立优化分类阈值（最大化类内 F1）
- **数据划分**：染色体分层随机划分，训练:验证:测试 = 80:10:10（据 Methods 4.1 推断，具体比例文中未明确给出，标注为推断）
- **对比模型**：HOMER（PWM 富集）、FIMO（PWM 扫描）、DanQ（CNN+BLSTM）、NN-6mer（相同 tokenization 的简单神经网络）、NN-onehot（one-hot 编码的简单神经网络）、随机基线（按类先验概率抽样）
- **下游应用**：
  1. PWM 后过滤：FIMO 预测 → TFClassPredict 验证 → 保留一致预测
  2. 3D 基因组互作预测：从 ATAC-seq 峰提取序列 → TFClassPredict 计算 DBD-class 结合潜力 → 作为 Random Forest 特征预测 Micro-C 互作计数
  3. 免疫细胞 ATAC-seq：对 25 种免疫细胞类型的 ATAC-seq 峰计算 DBD-class 结合潜力 → 比较谱系间差异
- **基因组规模扫描**：预编译 21bp 窗口预测轨道（hg38），存储于 LMDB 数据库
- **工具链**：Python、TensorFlow 2.13、HuggingFace Transformers、scikit-learn、HOMER、MEME Suite、Juicer、edgeR、limma

**文字流程**：
1. 从 UniBind 获取高置信直接结合 TFBS → 过滤重叠位点 → 扩展至 21bp → 按 TFClass 标注 DBD-class
2. 将序列 tokenize 为 6-mer → 输入 DNABERT → 微调多分类头
3. 在测试集上评估分类性能（accuracy、F1_macro、per-class F1）
4. 将训练好的模型应用于下游任务（PWM 过滤、3D 互作预测、ATAC-seq 分析）

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| UniBind 数据过滤与 DBD-class 标注 | 构建训练/测试集 | 确保训练数据为直接结合事件，减少间接结合噪声；DBD-class 标签提供分类目标 | 输入：UniBind TFBS；输出：21bp 序列 + DBD-class 标签 | Methods 4.1；Results 图 1d | 移除后模型将基于噪声标签训练，分类性能显著下降（预期） |
| DNABERT 骨干（6-mer） | 学习序列上下文表征 | Transformer 自注意力可建模长程依赖和上下文效应，优于 PWM 的位置独立假设 | 输入：6-mer token 序列；输出：序列嵌入 | Results 图 3a（DNABERT 优于所有基线）；Supplementary Table A2 | 替换为简单 NN 后 accuracy 下降约 10-15%（实测，图 3a） |
| 多分类头（23 类 softmax） | 输出 DBD-class 概率分布 | 将预测从二分类重构为竞争性多分类，直接建模类间区分 | 输入：DNABERT 嵌入；输出：23 维概率向量 | Results 图 3a；Methods 4.5 | 改为二分类（per-class one-vs-rest）将丢失类间竞争信息，预期 F1 下降（预期） |
| 每类独立阈值优化 | 将概率转为硬分类 | 类别不平衡下全局阈值不最优 | 输入：验证集概率；输出：每类最优 F1 阈值 | Methods 4.5 | 移除后低资源类 F1 下降（预期） |
| 1bp 滑动窗口扫描 | 处理任意长度序列 | 模型输入固定为 21bp，需扩展到基因组尺度 | 输入：任意长度 DNA；输出：逐窗口 DBD-class 概率 | Methods 4.6；Results 图 5a | 移除后无法进行基因组尺度注释（预期） |
| PWM 后过滤流程 | 结合 TFClassPredict 与 FIMO | 保留单 TF 分辨率的同时降低 FIMO 假阳性 | 输入：FIMO 预测 + TFClassPredict 预测；输出：过滤后预测 | Results 图 4a-b | 移除后 FIMO 假阳性率升高，per-TF 准确率下降（实测，图 4a） |
| Random Forest 互作预测 | 用 DBD-class 结合潜力预测 3D 互作 | 验证 DBD-class 级特征在复杂调控任务中的有效性 | 输入：ATAC-seq 峰内 DBD-class 结合潜力计数；输出：互作计数 | Results 图 4c-e | 替换为 HOMER 特征后性能下降（实测，图 4d） |

---

## 09 关键公式符号

本文为深度学习分类框架，核心公式为多分类交叉熵损失：

**交叉熵损失**：
\[
\mathcal{L} = -\frac{1}{N} \sum_{i=1}^{N} \sum_{c=1}^{C} y_{i,c} \log(\hat{y}_{i,c})
\]

- \( N \)：训练样本数
- \( C = 23 \)：DBD-class 数量
- \( y_{i,c} \)：样本 \( i \) 的真实标签（one-hot，属于类 \( c \) 则为 1）
- \( \hat{y}_{i,c} \)：模型预测的样本 \( i \) 属于类 \( c \) 的概率（softmax 输出）

**TFBPD（Transcription Factor Binding Potential Deviation）**：
\[
\text{TFBPD}_{g,d} = \frac{x_{g,d} - e(x_{g,d})}{\sqrt{e(x_{g,d})}}
\]

- \( x_{g,d} \)：基因组区域 \( g \) 中 DBD-class \( d \) 的 TFBP 计数
- \( e(x_{g,d}) \)：在保持区域和 DBD-class 边缘分布下的期望计数（基于列联表独立性假设）
- 灵感来源：ChromVAR 的 accessibility deviations

**分类评估指标**：
- Accuracy：\( \frac{TP + TN}{TP + TN + FP + FN} \)
- Macro F1：各类 F1 的算术平均，\( F1_c = \frac{2 \cdot P_c \cdot R_c}{P_c + R_c} \)

---

## 10 实验设计与证据链

### 数据集与设置

| 项目 | 详情 |
|------|------|
| 训练数据 | UniBind DAMO 集合，268 个人类 TF 的高置信直接结合 TFBS，过滤后 265 个 TF 有 TFClass 注释 |
| 序列长度 | 21bp（统一扩展/裁剪） |
| DBD-class 数 | 23 |
| 数据量 | 5,567,690 条 TFBS 序列（过滤后） |
| 划分方式 | 染色体分层随机划分，80:20 训练/测试，训练集再分验证集 |
| 基因组 | hg38 |
| 骨干模型 | DNABERT（6-mer 最优） |
| 对比模型 | HOMER、FIMO、DanQ、NN-6mer、NN-onehot、随机基线 |
| 下游数据 | Micro-C（HFFc6、H1-hESC）、ATAC-seq（GSE118189，25 种免疫细胞类型，97 样本） |
| 评估指标 | Accuracy、Macro F1、Per-class F1、Pearson 相关系数 |

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|------------|-------------------|------|
| PWM 基线评估 | PWM 方法在 DBD-class 分类上能力有限 | HOMER 富集 + FIMO 扫描，映射到 DBD-class | FIMO 分类准确率显著低于 TFClassPredict | PWM 位置独立假设不足以区分 DBD-class | 未提供具体数值 | Results 图 2b |
| 架构比较 | DNABERT 优于其他深度架构 | DNABERT vs DanQ vs NN-6mer vs NN-onehot vs 随机 | DNABERT Accuracy 87.3%，F1_macro 78.1%，优于所有基线 | Transformer + k-mer 预训练对 DBD-class 分类最有效 | 未提供各模型完整数值表 | Results 图 3a；Supplementary Table A2 |
| 数据量-性能关系 | DBD-class 池化缓解数据稀疏 | 按 TF 数量分层分析 per-TF accuracy | 低数据 TF 在 DBD-class 框架下仍保持较高准确率 | 池化效应有效 | 未提供具体相关系数 | Results 图 3c-d |
| PWM 后过滤 | TFClassPredict 可降低 PWM 假阳性 | FIMO 预测 → TFClassPredict 过滤 → 比较过滤前后 | 过滤后 per-TF 分类准确率显著提升 | TFClassPredict 可作为 PWM 流程的有效补充 | 未提供提升幅度数值 | Results 图 4a-b |
| 3D 基因组互作预测 | DBD-class 结合潜力可预测染色质互作 | Random Forest：TFClassPredict 特征 vs HOMER 特征 | TFClassPredict 特征获得更高 Pearson 相关系数 | DBD-class 级特征优于 PWM 级特征 | 未提供具体 r 值 | Results 图 4c-e；Supplementary Table A3 |
| 免疫细胞 ATAC-seq | TFClassPredict 可恢复已知谱系决定程序 | 25 种免疫细胞类型，比较 DBD-class 结合潜力差异 | 恢复已知 B 细胞、NK 细胞、T 细胞谱系决定 TF 程序 | DBD-class 级注释具有生物学有效性 | 未提供统计显著性数值 | Results 图 6a-d；Supplementary Table A5 |
| 基因组规模注释 | TFClassPredict 可生成全基因组 DBD-class 注释 | 预编译 21bp 窗口预测轨道 | 生成全基因组注释轨道 | 可扩展至全基因组规模 | 未提供轨道统计摘要 | Results 图 5a-c |

---

## 11 结论正确解读

- **任务范围**：本文解决的是 DBD-class 级别的分类，而非单 TF 级别的结合预测。结论仅适用于「判断序列属于哪个 DBD-class 的结合偏好」，不能直接推广到「判断具体哪个 TF 结合」。
- **输入限制**：模型仅使用 21bp 核心序列，不包含染色质可及性、共因子、表观遗传修饰等上下文信息。因此，其预测的是「序列内在的 DBD-class 结合潜力」，而非「细胞环境中的实际结合事件」。
- **oracle/真值**：训练标签来自 UniBind 的 ChIP-seq 直接结合事件，经 motif 过滤。这意味着标签本身受 ChIP-seq 实验质量和 motif 注释完整性影响。
- **端到端状态**：TFClassPredict 是分类器，不是端到端的调控预测流水线。下游应用（3D 互作、ATAC-seq）需要额外整合其他数据。
- **性能边界**：Accuracy 87.3% 是在 23 类不平衡数据上的宏观指标，不代表所有 DBD-class 都同样可区分。部分类（如 DBD-class 2.9）仍具挑战性。
- **生物学解释**：模型在 DBD-class 层面的成功支持「DBD 结构决定结合特异性」的进化保守假说，但不证明 DBD-class 是唯一决定因素。
- **可推广性**：模型基于人类基因组训练，直接迁移到其他物种需验证。21bp 窗口可能不足以捕获某些 TF 的长程结合模式。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 单 TF 分辨率不足 | DBD-class 级分类不识别具体哪个 TF 结合 | 结合 PWM 过滤或整合表达数据实现单 TF 推断 | Discussion 第 2 段 |
| 21bp 窗口限制 | 无法建模长程序列上下文、增强子-启动子环等 | 扩展窗口或整合多尺度信息 | Discussion 第 3 段 |
| 间接结合污染 | 训练数据可能含间接结合事件 | 更严格的实验验证或整合蛋白-DNA 构象数据 | Discussion 第 4 段 |
| 覆盖范围有限 | 仅覆盖 23 个 DBD-class，未包含全部 TF 家族 | 扩展至更多 DBD-class 和物种 | Discussion 第 5 段 |
| 序列信息不足 | 无法区分某些共享核心基序的 DBD-class | 整合 DNA 形状特征或结构信息 | Discussion 第 3 段 |
| 预测为潜力而非实际结合 | 未考虑细胞环境、共因子、染色质状态 | 整合细胞类型特异性的染色质数据 | Discussion 第 4 段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 训练/测试划分基于染色体分层随机，但未明确是否按 TF 划分 | 同一 TF 的多个结合位点可能同时出现在训练和测试集，导致数据泄漏 | 若泄漏存在，分类性能被高估 | 按 TF 分组划分训练/测试集，比较性能差异 | Methods 4.1 未明确说明 |
| 21bp 窗口的选择依据未充分论证 | 不同 DBD-class 的 DNA 足迹长度差异大，固定窗口可能截断关键接触位点 | 窗口大小直接影响模型可学习的序列特征 | 对不同窗口大小（如 11bp、31bp）进行消融实验 | Methods 4.1 仅说明「与最大结合位点一致」 |
| 与 DanQ 的对比可能不公平 | DanQ 原始设计针对 1000bp 序列，本文将其适配到 21bp 可能未充分调参 | 若基线未充分优化，DNABERT 的优势可能被夸大 | 对 DanQ 进行超参数搜索后重新对比 | Methods 4.5 仅提及 kernel size 调整 |
| TFBPD 的期望值模型假设区域间独立 | 基因组区域存在结构相关性（如 TAD 边界），可能违反独立性假设 | 若假设不成立，TFBPD 的标准化可能引入偏差 | 使用置换检验或空间自相关分析验证 | Methods 4.7 未讨论此假设 |
| 免疫细胞分析仅验证了已知谱系因子 | 恢复已知程序是必要但非充分验证，可能遗漏新的生物学发现 | 模型的实际价值在于发现未知调控逻辑 | 在未注释的细胞类型或疾病样本中验证预测的新颖性 | Results 图 6 仅展示已知因子 |
| 3D 互作预测中 RF 特征仅用 DBD-class 结合潜力，未与序列特征基线对比 | 无法判断提升来自 DBD-class 分类质量还是特征工程本身 | 若简单序列特征也能达到类似效果，则 DBD-class 抽象的价值存疑 | 增加 k-mer 频率、GC 含量等简单序列特征作为 RF 基线 | Results 图 4c-e 未提供此对比 |
| 未报告推理时间与计算成本 | 基因组尺度扫描的计算开销可能限制实际应用 | 实用性评估需要知道运行成本 | 报告 GPU 类型、推理速度、内存占用 | 全文未提及 |

---

## 14 个人收获与启发

### 对「TF–DNA 互作 × AI/物理模拟」课题的可迁移收获

1. **标签体系设计是核心创新点**：本文最重要的贡献不是新模型架构，而是将分类目标从「TF 身份」重构为「DBD-class」。这提示我们：在 TF–DNA 互作建模中，选择与生物学机制对齐的标签层级可能比追求更复杂的模型更有效。对物理模拟而言，DBD-class 可作为定义模拟系统边界（如哪些残基参与识别）的合理先验。

2. **「竞争性判别」框架的普适性**：将「结合 vs 不结合」的二分类改为「哪个 DBD-class 主导」的多分类，迫使模型学习类间区分性特征。这一思路可迁移到其他生物序列分类问题，如 RNA 结合蛋白特异性预测、染色质修饰酶靶点预测。

3. **数据池化策略**：将同一 DBD-class 下多个 TF 的结合位点合并训练，等效于数据增强，有效缓解了低资源 TF 的数据稀疏问题。这对物理模拟中的力场参数化或对接打分函数训练具有直接参考价值——按结构家族分组训练可能比逐蛋白训练更稳健。

4. **PWM + 深度学习的混合流程**：TFClassPredict 不是替代 PWM，而是作为 PWM 的过滤层，保留单 TF 分辨率的同时降低假阳性。这种「粗筛 + 精排」的级联策略在计算成本受限的场景（如全基因组扫描）中非常实用。

5. **TFBPD 标准化方法**：基于列联表期望值的偏差评分（灵感来自 ChromVAR）为比较不同 DBD-class 在不同基因组区域的富集程度提供了无偏度量。这一方法可直接迁移到任何「区域 × 类别」计数矩阵的分析中。

6. **预编译基因组轨道**：将模型预测预计算为全基因组轨道并公开，大幅降低了后续研究的计算门槛。这种「一次计算、多次复用」的发布模式值得在结构预测（如 AlphaFold 全蛋白质组）之外的领域推广。

---

## 15 与已有知识连接

- **TFClass 数据库**：本文使用 TFClass 的层级分类系统（2018 release）作为 DBD-class 标签来源。TFClass 按结构域进化关系组织 TF，是本文标签体系的基础。可进一步参考 TFClass 的更新版本以扩展分类覆盖。
- **UniBind 数据库**：训练数据来自 UniBind 的 DAMO 集合，该数据库使用 ChIP-eat 流程统一处理 ChIP-seq 数据，提供高置信直接结合位点。与 ENCODE 的 ChIP-seq 数据互补。
- **DNABERT**：本文基于 DNABERT 微调，DNABERT 是首个针对基因组 DNA 的 BERT 模型，通过 k-mer tokenization 和掩码语言建模预训练。后续的 DNABERT-2、Nucleotide Transformer 等模型可作为更强的骨干替代。
- **DanQ**：本文对比的深度架构之一，CNN+BLSTM 混合模型，最初用于预测 DNase I 超敏感位点等功能基因组注释。
- **ChromVAR**：TFBPD 评分的灵感来源。ChromVAR 用于从 ATAC-seq 数据中推断 TF 活性偏差，本文将其思想扩展到 DBD-class 级别的结合潜力分析。
- **HOMER / FIMO / MEME Suite**：经典 PWM 工具，本文用于基线对比和下游过滤流程。
- **3D 基因组（Micro-C）**：本文使用 Micro-C 数据验证 TFClassPredict 在染色质互作预测中的价值。Micro-C 是 Hi-C 的高分辨率变体，可捕捉更精细的染色质结构。
- **免疫细胞分化**：本文使用 Calderon et al. 的免疫细胞 ATAC-seq 数据（GSE118189），该数据集覆盖 25 种免疫细胞类型，是研究免疫分化调控的重要资源。
- **TF–DNA 共进化**：本文的核心假设（DBD 结构相似 → 结合特异性相似）与蛋白质-DNA 共进化研究一致，可参考 Nitta et al. (2015) 关于 Homeodomain 家族结合特异性的系统研究。

---

## 16 研究想法

### 候选 1：DBD-class 约束的 TF–DNA 对接打分函数
- **来源局限/观察**：本文证明 DBD-class 是序列分类的有效层级，但未涉及 3D 结构。物理模拟（如 MD/对接）中，TF 家族内不同成员的 DNA 识别模式高度相似，逐蛋白打分函数训练数据稀疏。
- **核心假设**：以 DBD-class 为分组单位训练结构-序列打分函数，可提高低资源 TF 的对接预测精度。
- **初步方法**：收集 PDB 中已知 TF–DNA 复合物，按 DBD-class 分组；对每组训练结构-序列匹配打分模型（如基于几何深度学习或能量函数微调）；在 DBD-class 内交叉验证。
- **验证方式**：与逐蛋白打分函数对比，在 DBD-class 内留一 TF 交叉验证；用实验突变数据（如 SELEX 或 HT-SELEX）验证预测特异性。
- **创新状态**：unverified

### 候选 2：基于 DBD-class 先验的 TF 结合位点竞争性预测
- **来源局限/观察**：TFClassPredict 是静态分类器，未建模多个 DBD-class 在同一基因组位点的竞争关系。
- **核心假设**：在同一增强子/启动子区域，多个 DBD-class 的结合潜力存在竞争性，联合建模可提高预测精度。
- **初步方法**：将 TFClassPredict 扩展为条件随机场（CRF）或图神经网络，以区域为单位联合预测多个 DBD-class 的结合潜力；损失函数引入类间互斥约束。
- **验证方式**：在 ENCODE 共结合数据集上评估；与逐位点独立预测对比。
- **创新状态**：unverified

### 候选 3：TFClassPredict 与 AlphaFold 结构先验的融合
- **来源局限/观察**：TFClassPredict 仅用序列信息，未利用蛋白质结构。AlphaFold 等结构预测工具可提供 DBD 结构信息，可能增强分类。
- **核心假设**：将 DBD 结构特征（如表面静电势、DNA 接触残基）编码为条件信息，可提高 DBD-class 分类的准确性和可解释性。
- **初步方法**：对每个 DBD-class 的代表性结构提取结构指纹；将结构指纹作为辅助特征注入 TFClassPredict 的分类头；或使用双塔架构分别编码序列和结构。
- **验证方式**：与纯序列模型对比；在结构已知的 TF 上评估分类置信度与结构相似性的相关性。
- **创新状态**：unverified

### 候选 4：跨物种 DBD-class 分类迁移
- **来源局限/观察**：TFClassPredict 基于人类数据训练，跨物种泛化能力未验证。
- **核心假设**：DBD-class 的 DNA 识别语法在进化上保守，人类训练的模型可迁移至模式生物。
- **初步方法**：用小鼠、果蝇、酵母的 ChIP-seq 数据评估 TFClassPredict 的零样本迁移性能；对低性能类进行领域自适应微调。
- **验证方式**：跨物种分类准确率对比；与各物种独立训练模型对比。
- **创新状态**：unverified

### 候选 5：单细胞 ATAC-seq 的 DBD-class 调控动态推断
- **来源局限/观察**：本文在 bulk ATAC-seq 上验证了 DBD-class 结合潜力的生物学有效性，但未涉及单细胞分辨率。
- **核心假设**：单细胞 ATAC-seq 峰中 DBD-class 结合潜力的异质性可反映细胞状态转变中的调控逻辑。
- **初步方法**：将 TFClassPredict 应用于单细胞 ATAC-seq 数据，计算每个细胞的 DBD-class 结合潜力谱；使用流形学习或轨迹推断分析分化过程中的 DBD-class 动态。
- **验证方式**：与已知分化轨迹的 TF 表达数据对比；在 CRISPR 扰动数据中验证预测的调控关系。
- **创新状态**：unverified

### 候选 6：DBD-class 结合潜力与 3D 基因组结构的联合建模
- **来源局限/观察**：本文将 DBD-class 结合潜力作为 RF 特征预测 Micro-C 互作，但未与结构模型深度整合。
- **核心假设**：DBD-class 结合潜力的空间共定位可预测增强子-启动子互作强度，且优于单一位点特征。
- **初步方法**：将 TFClassPredict 预测的 DBD-class 结合潜力映射到 3D 基因组图谱，计算 DBD-class 对在空间上的共富集；使用图神经网络建模互作强度。
- **验证方式**：与 Micro-C/Hi-C 数据对比；在 CRISPR 干扰增强子实验数据中验证。
- **创新状态**：unverified