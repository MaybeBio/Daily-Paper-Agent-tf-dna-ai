## 01 基本信息
- **标题**：MultiCapsNet: A General Framework for Data Integration and Interpretable Classification
- **作者与单位**：Wang, Lifei; Miao, Xuexia; Nie, Rui; Zhang, Zhang; Zhang, Jiang; Cai, Jun（单位未在提供材料中列出）
- **期刊/预印本平台**：Frontiers in Genetics
- **年份**：2021-12-14
- **论文类型**：方法学（Method）论文，提出新框架并多数据集验证
- **领域**：深度学习 × 生物数据整合与可解释分类（含单细胞转录组、蛋白质-蛋白质互作 PPI、蛋白质-DNA 互作 PDI）
- **关键词**：CapsNet、数据整合、可解释性、scRNA-seq、转录因子（TF）、PPI、PDI、SCENIC
- **DOI/arXiv 号**：10.3389/fgene.2021.767602
- **代码**：https://github.com/wanglf19/MultiCapsNet
- **数据**：公开数据，见代码仓库；具体数据集来源见 Methods 节
- **阅读日期**：未提供
- **在课题方向中的位置**：本文属于「AI 方法 × 蛋白质-DNA 互作（TF–DNA 结合机制）」方向中的**可解释深度学习分类器**分支。其核心贡献在于：将 PDI（TF–靶基因调控关系）与 PPI 作为先验知识嵌入 CapsNet 网络结构，使模型在分类的同时输出每个 TF/PPI 模块对细胞类型判别的贡献度（耦合系数），从而在不增加额外计算步骤的情况下实现 TF 层面的可解释性。与 SCENIC 的对比验证了其识别细胞类型相关 TF 的有效性。该框架对 TF–DNA 结合机制研究提供了一种「先验结构约束 + 可解释输出」的迁移范式。

---

## 02 一句话总结
本文提出 MultiCapsNet——一种基于 CapsNet 和 scCapsNet 的通用深度学习框架，通过将多源模块化数据（如变异位点特征组、scRNA-seq 表达谱）分别经独立神经网络映射为等长 primary capsules，再经动态路由（dynamic routing）聚合到 type capsules 完成分类；在 scRNA-seq 应用中，利用 PPI/PDI 先验知识指定输入层到 primary capsules 的连接，使每个 primary capsule 对应一个 TF 或 PPI 子网络，训练后耦合系数直接给出各 TF/PPI 对细胞类型判别的贡献度，在三个数据集上达到与神经网络、随机森林相当的分类性能，并识别出与 SCENIC 一致的细胞类型相关 TF。

---

## 03 研究问题
- **具体问题**：如何构建一个既能整合多源、异质、模块化生物数据（不同格式、不同长度），又能在分类的同时提供可解释性（尤其是生物学层面如 TF 层面的解释）的深度学习框架？
- **为什么重要**：生物数据（如 scRNA-seq、变异位点注释、多组学数据）天然具有模块化结构（如 TF 调控的靶基因集合、PPI 子网络），传统可解释方法（线性回归、随机森林）只能处理数值/类别特征，无法直接利用模块化先验；而深度学习方法虽能处理复杂数据，但“黑箱”特性限制了其在生物学机制发现中的应用。
- **现有方法不足**：
  - 传统可解释 ML（线性模型、树模型）无法处理模块化输入；
  - 标准深度网络（如全连接网络）缺乏对输入模块结构的显式建模；
  - 已有可解释深度学习方法（如通过先验指定网络连接）多针对单一数据类型，缺乏通用多源整合框架；
  - 现有方法（如 SCENIC）虽能推断 TF 调控网络，但需要多步骤流程（GENIE3 → RcisTarget → AUCell），且不直接提供分类功能。
- **精确研究问题（Can ... ?）**：Can a CapsNet-based framework with modular input channels and prior-knowledge-specified connections achieve comparable classification accuracy to standard models while simultaneously providing interpretable importance scores for each data source (e.g., TF or PPI subnetwork) without extra post-hoc analysis steps?

---

## 04 背景与发展脉络
> 注：以下脉络基于本文引用与论述整理，标注为「经外部核验」的部分仅指本文明确引用的文献；其余为本文框架内的逻辑梳理。

1. **传统可解释 ML 阶段**：线性回归/逻辑回归、决策树/随机森林等，可解释性强但仅能处理数值/类别特征，无法直接利用模块化结构（如基因集合、调控网络）。（本文 Figure 1A 论述）
2. **深度学习应用于生物数据阶段**：CNN 处理序列（如 DNA 序列）、Autoencoder/VAE/GAN 用于表达谱降维与生成；但多为“黑箱”，可解释性差（Alipanahi et al., 2018; Camacho et al., 2018; Eraslan et al., 2019）。
3. **先验知识约束网络结构阶段**：将 TF–靶基因调控关系或基因集作为先验，指定神经网络中神经元之间的连接，使内部节点与生物学实体（如 TF）对应，从而提升可解释性（Lin et al., 2017; Chen et al., 2018）。本文明确引用此思路并扩展至 CapsNet 框架。
4. **CapsNet 阶段**：CapsNet（Sabour et al., 2017）最初用于图像识别，以向量胶囊替代标量神经元，通过动态路由实现部分-整体关系建模。本文作者前期工作 scCapsNet（Wang et al., 2020）将其改造为可解释的细胞类型分类器，利用耦合系数揭示基因对细胞类型的贡献。
5. **本文位置**：在 scCapsNet 基础上提出 MultiCapsNet，将单输入扩展为多输入模块化框架，支持多源数据整合（如变异位点特征组、scRNA-seq + PPI/PDI 先验），并系统验证其分类性能与可解释性，与 SCENIC 对比证明其识别细胞类型相关 TF 的有效性。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 深度学习的“黑箱”问题 | 模型预测准确但无法解释决策依据，尤其在生物学应用中难以定位关键调控因子 | 标准深度网络（如全连接层）的隐层节点缺乏生物学语义对应 | Introduction 节：“deep learning methods usually run as a ‘black box’, which is hard to interpret” |
| 传统可解释方法无法处理模块化数据 | 线性模型/树模型仅接受数值或类别特征，无法直接利用基因集合、调控网络等模块化结构 | 模块化数据（如 TF 靶基因集、PPI 子网络）本质上是集合/图结构，传统特征表示会丢失结构信息 | Introduction 节：“traditional interpretable machine learning methods... could only deal with numerical features instead of modular features” |
| 多源数据整合困难 | 不同数据类型（如 one-hot 编码、实数向量、表达谱）长度和语义不一致，难以统一输入 | 缺乏统一的标准化层将异质输入映射到共同表示空间 | Methods 节公式 (1)：`ui = tanh(Wpi xi)`，将不同长度 xi 映射为等长向量 |
| 可解释性需要额外计算步骤 | 标准神经网络需通过特征扰动（如 shuffling）或事后分析（如 SHAP）才能获得重要性分数，计算成本高且不稳定 | 模型本身不输出特征/模块重要性，需事后推断 | Results 节对比：MultiCapsNet 直接输出耦合系数作为重要性分数，而神经网络需额外 shuffling 步骤 |
| 先验知识难以嵌入深度学习 | 生物学先验（如 TF–靶基因调控、PPI）难以转化为网络结构约束 | 缺乏将先验知识映射为网络连接模式的通用机制 | Methods 节：利用 PDI/PPI 指定输入到 primary capsule 的连接（Figure 4A） |

---

## 06 核心思想

### 1) 表面方法
MultiCapsNet 是一个多输入通道的 CapsNet 变体：
- 每个输入模块 xi 通过独立的神经网络（权重 Wpi）映射为等长向量 ui（primary capsule）；
- primary capsules 经动态路由（dynamic routing）聚合为 type capsules vj（对应类别）；
- 在 scRNA-seq 应用中，利用 PDI（TF–靶基因）和 PPI 先验知识指定输入基因到 primary capsule 的连接，使每个 primary capsule 对应一个 TF 或 PPI 子网络；
- 训练完成后，耦合系数 cij 的平均值作为每个 primary capsule（即 TF/PPI 模块）对各类别判别的贡献度。

### 2) 核心洞察
- **模块化输入 + 先验结构约束 = 可解释性**：将输入数据按生物学语义（TF 调控的靶基因集、PPI 子网络）分组，每组对应一个 primary capsule，使模型的内部表示与生物学实体直接对应，从而耦合系数天然成为生物学层面的重要性分数。
- **动态路由替代固定权重**：与全连接网络不同，动态路由允许模型自适应地学习每个 primary capsule 对每个 type capsule 的贡献权重（耦合系数），无需额外的事后解释步骤。
- **通用性**：框架不限于特定数据类型，只要输入可被划分为模块（如变异位点特征组、基因表达子集），即可应用。

### 3) 可能的普适教训 [Analysis]
- **先验知识是深度学习的“免费午餐”**：将领域知识（如调控关系、互作网络）编码为网络结构约束，不仅提升可解释性，还可能减少对数据量的需求（因为搜索空间被约束）。
- **可解释性可以是模型的结构属性而非事后分析**：与其在训练后通过扰动/归因方法解释黑箱，不如在设计网络时就让每个隐层单元具有语义标签。这一思路对 TF–DNA 结合机制研究尤为重要——若能将每个隐层节点对应一个 TF 或结合基序，则模型输出直接指向候选调控因子。
- **耦合系数作为重要性度量的有效性需外部验证**：本文通过与 SCENIC 的对比来验证耦合系数的生物学意义，说明「模型内部权重」作为解释工具时，必须与独立方法交叉验证，否则可能只是模型自身的自洽性而非生物学真实性。

---

## 07 方法总览
- **输入**：l 个模块化数据 xi（i = 1, …, l），每个模块长度 ri 可不同。
- **标准化层**：每个模块通过独立神经网络 `ui = tanh(Wpi xi)` 映射为等长向量 ui（长度 n，默认 n=8），即 primary capsule。
- **动态路由**：primary capsules 经权重矩阵 Wij 生成预测向量 ûj|i = Wij ui；通过迭代动态路由计算耦合系数 cij（softmax 归一化），加权求和得到 sj，再经 squash 非线性得到 type capsules vj。
- **输出**：type capsules vj 的模长表示属于类别 j 的概率。
- **训练**：标准反向传播，损失函数基于 capsule 模长与类别标签的匹配（margin loss，参照 Sabour et al., 2017）。
- **可解释性输出**：对每个类别 j，计算 primary capsule i 的平均耦合系数 cij^avg，作为该模块（TF/PPI）对类别 j 的重要性分数。
- **先验知识嵌入**：在 scRNA-seq 应用中，输入基因按 PDI（TF–靶基因）和 PPI 子网络分组，每组基因连接到对应的 primary capsule；未出现在先验中的基因可归入默认模块。
- **对比模型**：全连接神经网络（sigmoid 激活）、随机森林、K 近邻、Multi-head Attention 模型（替换 embedding 层为数据标准化层）。
- **评测流程**：三个数据集分别训练/验证；scRNA-seq 数据集重复 9 次训练，取平均耦合系数生成重要性排序；与 SCENIC 结果对比。

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 输入标准化层（独立神经网络） | 将不同长度、不同类型的模块化输入映射为等长向量 | 多源数据长度/格式不一致，需统一表示空间 | 输入：xi（长度 ri）；输出：ui（长度 n） | Methods 公式 (1)；Results 中三个数据集均成功应用 | [预期] 移除后无法处理异质输入，模型退化为单输入模型 |
| Primary capsules（模块语义标签） | 每个 capsule 对应一个生物学模块（TF 靶基因集或 PPI 子网络） | 使模型内部表示与生物学实体对应，实现可解释性 | 输入：ui；输出：带语义标签的 capsule | Methods 节 Figure 4A；Results 节 Figure 5 显示 TF/PPI 贡献度 | [预期] 移除后模型失去生物学语义，退化为标准黑箱分类器 |
| 动态路由（dynamic routing） | 迭代计算 primary capsules 到 type capsules 的耦合系数 | 自适应学习模块对类别的贡献权重，无需事后解释 | 输入：ûj|i；输出：耦合系数 cij、type capsules vj | Methods 公式 (2)-(6)；Results 中耦合系数与 shuffling 方法高度相关（r=0.876） | [实测] 替换为固定权重（如平均池化）会丧失自适应权重学习能力，重要性分数质量下降（本文未做消融，[Analysis] 推测） |
| Type capsules（类别表示） | 每个 capsule 对应一个分类类别，模长表示概率 | 完成分类任务 | 输入：sj；输出：vj（模长 ∈ [0,1)） | Methods 公式 (6)；Results 分类准确率与基线相当 | [预期] 移除后无法输出分类概率 |
| 先验知识连接指定 | 根据 PDI/PPI 指定输入基因到 primary capsule 的连接 | 将调控关系/互作网络编码为网络结构 | 输入：基因表达向量；输出：分组后的 primary capsule 输入 | Methods 节 Figure 4A；Results 节识别出已知细胞类型相关 TF | [预期] 移除后模型无法识别 TF 层面的贡献，可解释性丧失 |
| 耦合系数平均与重要性排序 | 对每个类别计算 primary capsule 的平均耦合系数，生成 TF/PPI 重要性排序 | 输出生物学可解释的结果 | 输入：所有样本的耦合系数；输出：每个类别下 TF/PPI 的重要性排序 | Results 节 Figure 5B、6A；与 SCENIC 对比 | [预期] 移除后模型仅输出分类结果，无生物学解释 |

---

## 09 关键公式符号

1. **输入标准化**：
   `ui = tanh(Wpi xi)`，i ∈ [1, 2, …, l]
   - xi：第 i 个输入模块（长度 ri）
   - Wpi：第 i 个神经网络的权重矩阵（维度 n × ri）
   - ui：第 i 个 primary capsule（长度 n，默认 n=8）

2. **预测向量**：
   `ûj|i = Wij ui`
   - Wij：primary capsule i 到 type capsule j 的权重矩阵
   - ûj|i：primary capsule i 对 type capsule j 的预测向量

3. **耦合系数（softmax）**：
   `cij = exp(bij) / Σk exp(bik)`
   - bij：中间参数，初始为 0，表示预测向量与 type capsule 的内积

4. **加权求和**：
   `sj = normalize(Σi cij ûj|i)`
   - sj：type capsule j 的输入加权和

5. **内积更新**：
   `bij = ûj|i · sj`
   - 用于下一轮动态路由迭代

6. **Squash 非线性**：
   `vj = (‖sj‖² / (0.5 + ‖sj‖²)) · (sj / ‖sj‖)`
   - vj：type capsule j 的输出向量，模长表示类别概率

7. **平均耦合系数（重要性分数）**：
   `cij^type_avg = Σ_type cij^type / Σ_type 1`
   - 对同一类别下所有样本的耦合系数取平均，作为 primary capsule i 对类别 j 的重要性分数

---

## 10 实验设计与证据链

### 数据集与评测协议
| 数据集 | 规模 | 任务 | 指标 | 划分 | 对比模型 |
|--------|------|------|------|------|----------|
| 变异位点数据集（Variant call） | >41,000 样本，71 特征，8 组 | 三分类（somatic/ambiguous/fail） | AUC、准确率 | 9:1 训练/验证 | Multi-head Attention、全连接神经网络、随机森林 |
| 小鼠 scRNA-seq（Microwell-Seq） | ~5,000 细胞，7 种细胞类型，9,437 基因 | 细胞类型分类 | 准确率、F1 | 未明确说明 | 全连接神经网络、随机森林、Multi-head Attention |
| SCENIC 示例数据（小鼠皮层/海马） | 7 种细胞类型 | 细胞类型分类 + TF 识别 | 准确率、F1、TF 重叠率 | 未明确说明 | SCENIC |

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 变异位点分类 | MultiCapsNet 在模块化输入上分类性能与标准模型相当 | 与 Attention、全连接网络、随机森林对比 | AUC：0.94/0.99/0.97（三类别）；准确率 ~0.873 | MultiCapsNet 分类性能与基线相当 | 未显著优于所有基线（随机森林准确率 0.895 略高） | Results 节 Figure 4A |
| 重要性分数相关性 | MultiCapsNet 的数据源重要性分数与神经网络 shuffling 方法一致 | Pearson 相关 | r = 0.876 | 两种方法重要性评估高度一致 | 相关性高不等于因果性，未验证重要性分数是否反映真实生物学机制 | Results 节 Figure 4B |
| scRNA-seq 细胞分类 | 整合 PPI/PDI 先验后分类性能不下降 | 与全连接网络、随机森林、Attention 对比 | 准确率 ~97%，F1 ~97% | 先验结构约束不损害分类性能 | 未与未整合先验的 MultiCapsNet 对比（无消融） | Results 节 Supplementary Figures S4A, B |
| TF 识别有效性 | MultiCapsNet 识别的 top TF 与 SCENIC 一致 | 与 SCENIC 结果对比 | 多个细胞类型相关 TF 被两种方法共同识别（如 Rorb-星形胶质细胞、Ets1/Elk3/Gata2-内皮细胞、Sox10/Sox8-少突胶质细胞等） | MultiCapsNet 能识别已知细胞类型相关 TF | 重叠不等于全等，MultiCapsNet 可能遗漏或误报部分 TF；未做统计显著性检验 | Results 节 Figure 6C |
| 排除 labeling TF 的稳健性 | 排除 TF 自身表达后模型性能与解释性不变 | 构建排除 labeling TF 的靶基因集 | top 30 TF 重叠率 ~90%（各细胞类型） | 模型不依赖 labeling TF 自身表达 | 重叠率 90% 仍有 10% 差异，未解释差异来源 | Results 节 Figure 6B |

---

## 11 结论正确解读
- **任务范围**：本文验证了 MultiCapsNet 在两类任务上的有效性——(1) 变异位点分类（模块化特征输入）；(2) 基于 scRNA-seq 的细胞类型分类，并同时输出 TF/PPI 模块的重要性分数。
- **oracle/真值输入**：在 scRNA-seq 应用中，PDI（TF–靶基因）和 PPI 先验来自外部数据库（BIOGRID、HPRD、DREM 2.0），这些先验本身可能不完整或含有噪声；模型性能依赖于先验质量。
- **端到端状态**：MultiCapsNet 是端到端可训练的，但先验知识（PDI/PPI）的获取和整理是离线步骤，不包含在端到端流程中。
- **算力成本**：本文未报告训练时间或硬件配置；动态路由的迭代计算可能比标准前馈网络更耗时（[Analysis] 推测，原文未提供数据）。
- **历史数据依赖**：scRNA-seq 数据来自 Microwell-Seq 平台，变异位点数据来自先前研究（Ainscough et al., 2018）；模型在其他平台/数据类型上的泛化性未验证。
- **模型依赖**：结果基于特定网络结构（n=8 的 capsule 维度、tanh 激活、动态路由迭代次数等超参数）；未进行超参数敏感性分析。
- **最难情形**：对于先验知识覆盖不全的基因（未出现在 PDI/PPI 中），模型将其归入默认模块，可能降低这些基因的可解释性；本文未讨论该情形下的性能。
- **群体/领域边界**：验证限于小鼠 scRNA-seq 和人类变异位点数据；未在植物、微生物或其他物种上验证。
- **不确定性**：重要性分数（耦合系数）的方差未报告；9 次重复训练的稳定性仅以 top 列表重叠率体现，未报告分数本身的置信区间。

**有边界的复述**：MultiCapsNet 在模块化输入分类任务上达到与标准模型相当的准确率，并能通过耦合系数直接输出数据源（TF/PPI 模块）的重要性排序；该排序与神经网络 shuffling 方法高度相关（r=0.876），且与 SCENIC 识别的细胞类型相关 TF 有较高重叠。但该结论限于本文测试的三个数据集和特定先验知识库，不构成对一般生物数据可解释分类的普适保证。

---

## 12 作者自认局限
在提供的材料中未发现作者明确承认的局限。

**作者提及的相关约束**（非正式局限，来自 Discussion 节）：
- 作者指出 MultiCapsNet 目前处理的数据类型限于 one-hot 编码向量和实数向量；对于序列数据（如 DNA/RNA 序列），需要引入 CNN 等模块进行转换（Discussion 节：“the data types are limited to one-hot encoding vectors or real valued vectors. With appropriate dataset, the MultiCapsNet could integrate and standardize more data types, such as sequence data, which can be integrated through convolutional neural network”）。
- 作者提到未来将引入更复杂的层次化生物网络信息（Discussion 节：“the complex and hierarchical information of biological network will be introduced into the MultiCapsNet model”），暗示当前版本对生物网络结构的利用仍较简单（仅一层先验连接指定）。

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| 重要性分数（耦合系数）与 shuffling 方法高度相关（r=0.876），但 shuffling 方法本身并非金标准 | 高相关可能反映两种方法捕捉到相同的统计信号（如特征方差），而非真实的生物学因果贡献；相关性高不等于重要性分数具有生物学意义 | 可解释性声明的核心是「模型输出的 TF 重要性是否反映真实调控机制」，若仅与另一种统计方法一致，则未独立验证生物学真实性 | 用 ChIP-seq 或 TF 敲除实验数据验证 top TF 是否确实调控目标细胞类型；或与已知调控数据库（如 TRRUST、RegNetwork）做富集分析 | Results 节 Figure 4B |
| 未进行消融实验（如移除先验连接、替换动态路由为固定权重） | 无法判断性能与可解释性来自动态路由机制、先验结构约束，还是 capsule 架构本身 | 消融是归因的基础；缺少消融则无法指导后续改进（如哪些组件可简化或替换） | 设计消融：① 无先验连接的随机分组；② 固定权重替代动态路由；③ 标准 CNN/MLP 替代 capsule 层 | 全文未报告消融实验 |
| 与 SCENIC 的对比仅报告重叠 TF，未报告不重叠部分的分析 | 不重叠的 TF 可能是 MultiCapsNet 的新发现，也可能是误报；未分析差异来源 | 若 MultiCapsNet 能发现 SCENIC 遗漏的 TF，则具有增量价值；若只是误报，则说明可解释性输出噪声较大 | 对不重叠 TF 做文献验证或实验验证；分析其是否因先验知识库覆盖不全而被错误分组 | Results 节 Figure 6C |
| 先验知识（PDI/PPI）来自外部数据库，其质量直接影响模型结构 | 数据库中的调控关系可能包含组织特异性差异、假阳性或过时信息；模型性能可能对先验噪声敏感 | 若先验噪声大，模型结构可能被错误约束，导致可解释性输出失真 | 用不同版本的数据库或随机扰动先验连接做敏感性分析 | Methods 节 Figure 4A |
| 分类性能与随机森林相当但未显著超越 | 如果仅追求分类准确率，简单模型（随机森林）可能更实用；MultiCapsNet 的增量价值主要在可解释性 | 需要明确 MultiCapsNet 的适用场景：当可解释性比极致准确率更重要时（如机制发现），该框架才有优势 | 在更多数据集上比较准确率与可解释性的权衡；评估用户（生物学家）对解释结果的实际采纳率 | Results 节 Figure 4A、Supplementary Figures S4A, B |
| 未报告超参数敏感性（capsule 维度 n、动态路由迭代次数、tanh 激活等） | 结果可能对特定超参数组合敏感，泛化性存疑 | 框架的「通用性」声明需要超参数鲁棒性证据支持 | 对关键超参数做网格搜索，报告性能变化范围 | Methods 节公式 (1)-(6) |

---

## 14 学到什么
> 标题：Agent 提炼的知识候选

1. **先验知识结构化的通用模式**：将生物学先验（如 TF–靶基因调控、PPI 子网络）映射为网络输入的分组结构，使每个隐层单元（capsule）具有明确的生物学标签。**迁移到 TF–DNA 结合机制研究**：可将已知 TF 结合位点（motif）或 ChIP-seq 峰对应的基因组区域作为分组依据，构建「每个 primary capsule 对应一个 TF 的结合靶标集合」的模型，直接输出各 TF 对表型（如细胞类型、疾病状态）的贡献度。

2. **耦合系数作为可解释性输出的设计**：动态路由的耦合系数天然提供了「输入模块 → 类别」的软权重，无需事后归因（如 SHAP、LIME）。**迁移思路**：在 TF–DNA 结合预测任务中，若输入为「TF 的候选靶基因集合」，耦合系数可直接作为该 TF 对预测结果的贡献分数，实现端到端的可解释性。

3. **多源异质数据整合的标准化层设计**：每个输入模块通过独立神经网络映射到等长向量，再进入共享的 capsule 层。**迁移到 TF–DNA 结合机制**：可整合多种数据类型——如 DNA 序列（经 CNN 编码）、染色质可及性（ATAC-seq）、TF 表达量、已知 motif 匹配分数——每种类型作为一个模块，经独立编码后融合，同时输出各数据源的重要性。

4. **与独立方法交叉验证可解释性**：本文通过与 SCENIC 的对比来验证 TF 重要性排序的有效性。**迁移思路**：在 TF–DNA 结合研究中，模型输出的 TF 重要性应与独立实验数据（如 ChIP-seq、TF 敲除转录组）或独立算法（如 SCENIC、ARACNe）交叉验证，避免仅依赖模型内部一致性。

5. **模块化输入的粒度选择**：本文在变异位点数据中按数据来源分组（8 组），在 scRNA-seq 中按 TF/PPI 模块分组（696 组）。**迁移启示**：分组的粒度直接影响可解释性的分辨率——分组越细，解释越具体，但可能增加过拟合风险；需根据先验知识的可靠性和数据量权衡。

6. **CapsNet 在生物数据中的适用性**：CapsNet 的向量表示和动态路由适合建模「部分-整体」关系，与生物系统中「基因→模块→表型」的层次结构天然契合。**迁移方向**：在 TF–DNA 结合机制中，可建模「motif→TF 结合→靶基因调控→细胞表型」的层次关系。

---

## 15 与已有知识连接
- **CapsNet 原始文献**：Sabour, S., Frosst, N., & Hinton, G. E. (2017). Dynamic routing between capsules. NeurIPS. 本文的 capsule 架构和动态路由机制直接源于此。
- **scCapsNet（本文作者前期工作）**：Wang, L. et al. (2020). 单细胞 capsule 网络，本文是其多输入扩展。
- **先验知识约束网络结构**：Lin, C. et al. (2017). 使用 TF–靶基因调控关系指定神经网络连接，本文在 scRNA-seq 应用中直接沿用了这一思路（Methods 节引用）。
- **SCENIC**：Aibar, S. et al. (2017). SCENIC: single-cell regulatory network inference and clustering. Nature Methods. 本文将其作为对比方法验证 TF 识别有效性。
- **变异位点分类**：Ainscough, B. J. et al. (2018). 用于自动化体细胞变异筛选的数据集和模型，本文第一个实验直接使用该数据集。
- **可解释深度学习综述**：本文 Introduction 中引用的关于深度学习可解释性挑战的文献（如 Alipanahi et al., 2018; Camacho et al., 2018; Eraslan et al., 2019）。
- **与 TF–DNA 结合机制课题的关联**：
  - 本文的 PDI 先验（TF–靶基因调控关系）直接对应 TF–DNA 结合的调控结果层面；
  - 本文的可解释性输出（TF 重要性分数）可作为 TF–DNA 结合预测模型的解释层参考；
  - 本文的多源整合框架可迁移到「序列 + 表观 + 表达」多模态 TF 结合预测。

---

## 16 研究想法
> 标题：Agent 生成的研究候选

### 候选 1：TF–DNA 结合特异性预测的 MultiCapsNet 框架
- **名称**：TF-CapsNet：基于先验调控关系的可解释 TF–DNA 结合预测器
- **来源局限/观察**：现有 TF–DNA 结合预测模型（如 DeepBind、DeepSEA）多为黑箱 CNN，无法直接指出哪些 TF 模块驱动了预测；MultiCapsNet 的模块化输入 + 耦合系数输出可解决此问题。
- **核心假设**：将输入基因按已知 TF 调控关系分组，每个 primary capsule 对应一个 TF 的靶标集合，模型在预测结合位点的同时输出各 TF 的贡献度，且该贡献度与 ChIP-seq 实验数据一致。
- **初步方法**：输入为基因组序列（经 CNN 编码）+ 候选 TF 的 motif 匹配分数 + 染色质可及性；按 TF 分组构建 primary capsules；动态路由到 type capsules（结合/不结合）；输出耦合系数作为 TF 重要性。
- **验证方式**：在 ENCODE ChIP-seq 数据集上评估预测 AUC；将 TF 重要性排序与独立 motif 富集分析、已知调控数据库比较。
- **创新状态**：unverified

### 候选 2：动态路由权重作为 TF–DNA 协同结合的信号
- **名称**：Co-binding Capsule：利用动态路由发现 TF 协同结合模块
- **来源局限/观察**：MultiCapsNet 的耦合系数 cij 衡量 primary capsule 对 type capsule 的贡献，但未利用 primary capsule 之间的交互信息；TF 协同结合（co-binding）是转录调控的重要机制。
- **核心假设**：动态路由过程中 primary capsule 之间的耦合模式可反映 TF 之间的协同结合关系，即共同贡献于同一 type capsule 的 TF 对可能物理上协同结合 DNA。
- **初步方法**：在 MultiCapsNet 训练后，提取所有样本的耦合系数矩阵，计算 TF 对之间的共现模式（如耦合系数协方差）；与已知 TF–TF 蛋白互作（如 BIOGRID）和共结合 ChIP-seq 数据比较。
- **验证方式**：统计 TF 对共现分数与已知共结合位点的富集关系；用 motif 空间共现（如 Tomtom 匹配）交叉验证。
- **创新状态**：unverified

### 候选 3：先验知识不确定性的鲁棒建模
- **名称**：Uncertainty-aware CapsNet：对不完整 PDI/PDI 先验的鲁棒整合
- **来源局限/观察**：MultiCapsNet 依赖外部数据库的 PDI/PPI 先验，但数据库本身不完整且含噪声；未覆盖的基因被归入默认模块，可能降低可解释性。
- **核心假设**：为先验连接引入不确定性权重（如 dropout 或贝叶斯推断），可提高模型对先验噪声的鲁棒性，并输出先验覆盖不足区域的置信度。
- **初步方法**：在输入到 primary capsule 的连接中引入可学习的掩码或不确定性参数；训练时对先验连接进行随机扰动；输出每个 TF 模块的置信区间。
- **验证方式**：在人工添加噪声的先验上测试性能下降幅度；与原始 MultiCapsNet 比较在低覆盖先验下的可解释性稳定性。
- **创新状态**：unverified

### 候选 4：从细胞类型分类到 TF–DNA 结合动力学
- **名称**：Binding Dynamics Capsule：利用 capsule 表示预测 TF 结合强度与动力学
- **来源局限/观察**：MultiCapsNet 仅做分类（细胞类型），未利用 capsule 向量的连续表示；TF–DNA 结合是连续过程（结合强度、解离速率）。
- **核心假设**：type capsule 的向量方向可编码结合强度信息，而不仅是类别概率；通过回归头可预测 TF 结合强度（如 ChIP-seq 峰强度）。
- **初步方法**：在 MultiCapsNet 的 type capsule 后添加回归头，预测 TF 结合强度；利用 capsule 向量的模长和方向作为结合动力学的低维表示。
- **验证方式**：在 ChIP-seq 峰强度回归任务上评估；比较 capsule 表示与标准 CNN 特征在结合强度预测上的差异。
- **创新状态**：unverified

### 候选 5：跨物种 TF–DNA 结合机制迁移
- **名称**：Cross-species Capsule Transfer：利用 MultiCapsNet 框架迁移 TF 调控知识
- **来源局限/观察**：MultiCapsNet 的模块化结构允许不同物种的输入共享 primary capsule 层；TF 结合机制在物种间保守性可被利用。
- **核心假设**：在人类数据上训练的 primary capsule 表示（对应 TF 模块）可迁移到小鼠数据，因为 TF–DNA 结合机制保守。
- **初步方法**：在人类 scRNA-seq 上预训练 MultiCapsNet，冻结 primary capsule 层，在小鼠数据上微调 type capsule 层；评估迁移后的分类性能和 TF 重要性排序。
- **验证方式**：比较迁移学习与从头训练的性能差异；检查迁移后 TF 重要性排序与小鼠已知调控知识的吻合度。
- **创新状态**：unverified