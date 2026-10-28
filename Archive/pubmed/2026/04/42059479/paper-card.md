## 01 基本信息
- **标题**：CaHoT-GRN: context-aware high-order topology learning for robust single-cell gene regulatory network inference
- **作者与单位**：Yao, Dengju; Zhang, BinBin; Zhan, Xiaojuan; Wang, Wentao; Liang, Ning（单位未提供）
- **期刊/预印本平台**：Briefings in Bioinformatics
- **年份**：2026（在线日期 2026-04-30）
- **论文类型**：方法学（Method）
- **领域**：单细胞基因调控网络（GRN）推断；多模态深度学习；图神经网络
- **关键词**：gene regulatory network inference; single-cell RNA-seq; large language model; high-order topology; attention mechanism
- **DOI/arXiv 号**：10.1093/bib/bbag202
- **代码**：https://github.com/ydkvictory/CaHoT-GRN
- **数据**：BEELINE 基准（7 个 scRNA-seq 数据集，GSE81252、GSE75748、GSE98664、GSE48968、GSE81682）；膀胱癌空间转录组 GSE171351；ground-truth 网络来自 STRING、ChIP-seq（非特异与细胞类型特异）、LOF/GOF（仅 mESC）
- **阅读日期**：未提供
- **在该方向中的位置**：本文属于「蛋白质-DNA 互作（TF–DNA 结合机制）× AI」方向中的 GRN 推断任务。其核心贡献在于将 TF 蛋白序列与靶基因 DNA 序列的语义嵌入（通过 ESM 与 DNABERT 预训练模型）引入 GRN 推断，并利用 PPI 网络构建高阶拓扑，以缓解仅依赖表达数据导致的假阳性连接。与物理模拟（MD/对接）不同，本文不直接建模 TF–DNA 三维结构，而是通过序列语义空间隐式编码结合亲和力，属于「序列语义 + 图拓扑」的深度学习方法。

## 02 一句话总结
针对单细胞 GRN 推断中仅用表达数据导致假阳性高的问题，CaHoT-GRN 融合 TF 蛋白序列与靶基因 DNA 序列的预训练语言模型嵌入、表达谱及 PPI 约束的高阶拓扑，通过相似性共注意力机制融合双图特征，在 BEELINE 基准上取得平均 AUROC 0.846、AUPR 0.420，匹配或优于现有方法。

## 03 研究问题
- **具体问题**：如何从单细胞转录组数据中稳健地推断基因调控网络（GRN），减少假阳性连接？
- **为什么重要**：GRN 是理解细胞命运决定和疾病机制的关键；单细胞测序提供了推断 GRN 的机会，但数据噪声大、样本稀疏，现有方法准确性有限。
- **现有方法不足**：
  - 无监督方法（GENIE3、GRNBoost、PIDC、DigNet 等）主要捕捉统计关联，难以区分直接调控与间接关联/技术噪声。
  - 有监督方法依赖已知调控关系作为先验，但忽略了靶基因 DNA 序列的调控语义（启动子/增强子上下文）与 TF 蛋白的理化/功能特性。
  - 图学习方法（GNN）通常只利用表达谱构建的浅层拓扑，缺乏生物学先验（如 PPI）来约束高阶连接。
- **精确研究问题（Can...?）**：Can integrating TF protein sequence semantics, target gene DNA sequence semantics, and PPI-constrained high-order topology with a similarity co-attention mechanism improve the robustness of single-cell GRN inference over expression-only baselines?

## 04 背景与发展脉络
*（注：以下脉络基于本文框架整理，未逐一外部核验，标记为「仅本文框架」）*

- **阶段一：统计/信息论方法**（GENIE3、GRNBoost、PIDC）——基于表达相关性或互信息推断 GRN。优点：无需先验、计算快；局限：无法区分直接/间接调控，对噪声敏感。
- **阶段二：图学习方法**（GCLink、GATCL、scMGATGRN、GeneLink+ 等）——将 GRN 推断视为图上的链接预测或节点分类，利用 GNN 聚合邻居信息。优点：能捕捉拓扑结构；局限：主要依赖表达谱，忽略序列语义与蛋白理化性质，且多为浅层拓扑。
- **阶段三：多模态/大模型方法**（本文位置）——引入预训练生物大语言模型（DNABERT、ESM）提取序列语义嵌入，结合 PPI 构建高阶拓扑，通过共注意力融合多视图特征。优点：显式引入 TF–DNA 结合亲和力的序列线索与蛋白互作先验；局限：依赖预训练模型质量与 PPI 覆盖度，计算成本高。

## 05 核心痛点
| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| 假阳性连接过多 | 仅用表达数据推断的 GRN 包含大量非直接调控关系 | 表达相关性不等于因果调控；间接关联与技术噪声被误判为调控边 | Introduction 第 2 段："these methods often fail to elucidate true causal regulation, as they struggle to distinguish direct interactions from indirect correlations and technical noise" |
| 忽略序列语义上下文 | 靶基因的启动子/增强子等调控元件信息未被利用 | 现有方法仅依赖表达数据，未编码 DNA 序列中的 TF 结合位点上下文 | Abstract："current GRNs inference methods rely predominantly on expression data alone, overlooking the sequence semantic context of target genes" |
| 忽略 TF 理化性质 | TF 蛋白的结构/功能特性未被建模 | 未利用蛋白序列编码 TF 的 DNA 结合域等理化特征 | Abstract："the intrinsic physicochemical properties of TFs" 被忽略 |
| 拓扑稀疏性 | GRN 中已知边稀少，GNN 难以有效聚合 | 标注数据有限，浅层拓扑信息不足 | 方法部分提出 PPI 约束的高阶邻居构建以"enrich the sparse network structures inherent in current datasets"（Materials and methods, Overview 节） |
| 长程依赖缺失 | GNN 只能聚合局部邻居，难以捕捉远距离协同调控 | 标准 GNN 层数有限，感受野受限 | 相似性共注意力模块被设计用于"capturing long-range associations among genes"（Abstract） |

## 06 核心思想
1. **表面方法**：一个三阶段多模态框架——(1) 用 DNABERT 编码靶基因启动子/调控区 DNA 序列、用 ESM 编码 TF 蛋白序列，得到序列语义嵌入；(2) 基于表达谱构建 GRN 拓扑，同时通过 PPI 网络约束的元路径生成高阶拓扑（HIN）；(3) 用相似性共注意力模块融合 GRN 与 HIN 双视图特征，最终通过 MLP 与点积解码预测 TF–靶基因调控强度。
2. **核心洞察**：GRN 推断不应只依赖表达数据。TF–DNA 结合的亲和力信息编码在序列中（DNA 结合基序、蛋白结构域），而 PPI 提供了「TF 协同调控」的生物学先验。将这三者（表达、序列语义、PPI 高阶拓扑）在统一框架中融合，可以显著减少假阳性边。
3. **可能的普适教训 [Analysis]**：在生物网络推断任务中，「先验知识（如 PPI）+ 序列语义（如预训练模型嵌入）+ 动态数据（如表达谱）」的三元融合比任何单一数据源都更稳健。预训练语言模型（DNABERT/ESM）提供了一种无需显式 motif 扫描即可编码 TF–DNA 结合潜力的方式，这一思路可迁移到其他「序列-功能」映射任务。

## 07 方法总览
- **输入**：
  - 单细胞表达矩阵（基因 × 细胞）
  - 靶基因的 DNA 序列（启动子/调控区）
  - TF 的蛋白序列
  - 先验 GRN（训练用标签）
  - PPI 网络（如 HuRI）
- **输出**：TF–靶基因对的调控概率/强度（即推断的 GRN 边权重）
- **模块**：
  1. **序列特征提取模块**：DNABERT 编码 DNA 序列 → DNA 嵌入；ESM 编码蛋白序列 → 蛋白嵌入。预训练模型参数冻结。
  2. **PPI 高阶邻居构建模块**：通过元路径（meta-path）在 PPI 网络上生成二阶邻居，构建 HIN；用 PPI 过滤 GRN 中的噪声边。
  3. **相似性共注意力模块**：对 GRN 视图与 HIN 视图分别做 GAT 编码，计算视图内与视图间相似性矩阵，作为共注意力权重聚合邻居特征，融合双视图节点表示。
  4. **GRN 重建模块**：融合后的节点表示经 MLP 投影，点积计算 TF–靶基因关联分数，交叉熵损失优化。
- **训练**：有监督，标签来自 ground-truth 网络（STRING、ChIP-seq、LOF/GOF）；10 次独立实验取平均。
- **流程**：表达谱 + 序列 → 特征提取 → GRN 与 HIN 双图构建 → GAT 编码 → 相似性共注意力融合 → MLP + 点积 → 预测边 → 交叉熵损失。

## 08 核心模块拆解
| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 序列特征提取模块（SFE） | 用 DNABERT/ESM 提取 DNA/蛋白序列语义嵌入 | 编码 TF–DNA 结合亲和力的序列线索，弥补表达数据的信息缺失 | 输入：DNA/蛋白序列；输出：序列嵌入 | 消融实验（w/o SFE）显示性能下降（Results, Ablation 节）；Supplementary Table S1 显示单独使用 DNA 或蛋白序列均不如联合使用 | 移除后模型退化为仅依赖表达谱，假阳性增加（实测消融效应） |
| PPI 高阶邻居构建模块（PPI-HON） | 通过元路径生成 PPI 约束的二阶邻居，构建 HIN | 捕捉 TF 协同调控与间接调控的生物学先验，丰富稀疏 GRN 拓扑 | 输入：GRN 邻接矩阵、PPI 网络；输出：HIN 邻接矩阵 | 消融实验（w/o PPI-HON）显示显著性能下降（Results, Ablation 节）；2-hop 优于 1-hop 和 3-hop（Table 4） | 移除后模型失去高阶拓扑信息，长程调控关系难以捕捉（实测消融效应） |
| 相似性共注意力模块（S Co-A） | 计算 GRN 与 HIN 视图内/视图间相似性，作为注意力权重融合双视图特征 | 标准 GNN 只能聚合局部邻居，无法捕捉长程关联；共注意力可自适应选择强关联节点 | 输入：GRN/HIN 节点嵌入；输出：融合后的节点表示 | 消融实验（w/o S Co-A）显示性能下降（Results, Ablation 节）；Supplementary Table S3 显示自适应融合优于简单求和 | 替换为 MLP 后双视图特征无法深度交互，长程依赖丢失（实测消融效应） |
| GRN 重建模块 | MLP 投影 + 点积计算 TF–靶基因关联分数 | 将融合表示解码为边概率 | 输入：融合节点表示；输出：边分数 | 方法部分公式（Methods, GRN reconstruction 节） | 移除后无法输出预测边（预期效应） |

## 09 关键公式符号
*（注：原文公式以 LaTeX 片段形式给出，以下为可辨识的核心公式，符号含义基于上下文推断）*

1. **二阶邻接矩阵**（PPI-HON 构建）：
   \[
   A^{2} = A \cdot A
   \]
   - \( A \)：GRN 邻接矩阵
   - \( A^{2} \)：原始二阶邻近矩阵（经矩阵乘法得到）
   - \( A^{2n} \)：排除一阶连接后的 refined 二阶邻居信息（"obtained by excluding direct first-order connections"）

2. **PPI 过滤后的 HIN**：
   \[
   \text{HIN} = A^{2n} \odot A^{\text{PPI}}
   \]
   - \( A^{\text{PPI}} \)：数据集特异的 PPI 邻接矩阵（来自 HuRI）
   - \( \odot \)：逐元素乘（推断，用于过滤无 PPI 证据的二阶邻居）

3. **GAT 注意力系数**（标准 GAT，推断）：
   \[
   \alpha_{ij} = \frac{\exp(\text{LeakyReLU}(a^T [W h_i \| W h_j]))}{\sum_{k \in N(i)} \exp(\text{LeakyReLU}(a^T [W h_i \| W h_k]))}
   \]
   - \( h_i, h_j \)：节点特征
   - \( W \)：可学习权重矩阵
   - \( a \)：注意力向量
   - \( \| \)：拼接操作（原文明确提到 "the symbol ∥ denotes the feature concatenation operation"）

4. **相似性共注意力**（推断）：
   \[
   \text{sim\_GRN}, \text{sim\_HIN}, \text{sim\_mix}
   \]
   - 分别表示 GRN 视图内、HIN 视图内、跨视图的相似性矩阵（点积计算）
   - 用于生成共注意力权重 \( \text{co\_att}^{(mk)} \)

5. **视图级融合权重**：
   \[
   w_{\text{GRN}i}, w_{\text{HIN}i} = \text{softmax}(q^T [h_{\text{GRN}i} \| h_{\text{HIN}i}] + b)
   \]
   - \( q^T \)：可学习的拓扑级注意力向量
   - \( b \)：偏置项
   - 输出 \( \beta_1, \beta_2 \)（归一化后的 GRN/HIN 权重）

6. **多模态融合**：
   \[
   h_{\text{out}}^{\text{global}} = [h_{\text{out}}^{\text{exp}} \| h_{\text{out}}^{\text{DNA}} \| h_{\text{out}}^{\text{protein}}]
   \]
   - 拼接三种模态的最终表示

7. **边预测**（推断）：
   \[
   \hat{y}_{ij} = \sigma(h_{\text{out}(i)}^{\text{global}} \cdot h_{\text{out}(j)}^{\text{global}})
   \]
   - 点积后经 sigmoid（推断，原文为 "dot product operation"）

8. **损失函数**：
   \[
   \mathcal{L} = -\frac{1}{T} \sum_{i=1}^{T} [y_{\text{true}}^{(i)} \log y_{\text{pred}}^{(i)} + (1 - y_{\text{true}}^{(i)}) \log(1 - y_{\text{pred}}^{(i)})]
   \]
   - 交叉熵损失（原文明确 "cross-entropy loss function"）
   - \( T \)：总标记边数
   - \( y_{\text{true}}^{(i)} \)：第 i 个 TF–基因对的真实标签
   - \( y_{\text{pred}}^{(i)} \)：预测概率

## 10 实验设计与证据链
- **数据集**：BEELINE 基准中的 7 个 scRNA-seq 数据集（hESC、hHEP、mDC、mESC、mHSC-E、mHSC-GM、mHSC-L）；每个数据集对应 3 种 ground-truth 网络（STRING、非特异 ChIP-seq、细胞类型特异 ChIP-seq），mESC 另有 LOF/GOF 网络，共 4 种 ground-truth。
- **规模**：两种基因规模——TFs+500 和 TFs+1000。
- **指标**：AUROC、AUPR。
- **基线**：7 种方法（GeneLink+、scMGATGRN、GCLink、GATCL、GENELink、GNE、DeepRIG）。
- **实验设置**：10 次独立实验取平均；基线使用默认参数。
- **评测协议**：有监督链接预测，训练/测试划分基于 ground-truth 网络。

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|------------|------|-------------|-------------------|------|
| 主实验（Table 1, 2） | CaHoT-GRN 优于现有方法 | 7 个数据集 × 4 种 ground-truth × 2 种规模，对比 7 个基线 | TFs+500 上 AUROC 平均提升 3.4%、3%、2.7%、1.8%、3%、14.9%、28.2%（vs 各基线）；AUPR 提升 4.5%、6.7%、3.5%、2.7%、7.8%、19.7%、18.1% | CaHoT-GRN 在多数设置下匹配或优于基线 | 未报告方差或显著性检验；未在全部 44 个场景中逐一说明是否均最优 | Results, Tables 1-2 |
| 消融实验（Table 3, Fig. 2） | 三个模块各自贡献 | 移除 SFE / PPI-HON / S Co-A，其余设置不变 | 移除任一模块均导致性能下降 | 三个模块均对最终性能有贡献 | 未报告各模块独立贡献的效应量；未做组合消融（如同时移除两个模块） | Results, Ablation 节 |
| 序列模态单独实验（Supplementary Table S1） | DNA 与蛋白序列均有用 | 单独使用 DNA 或蛋白序列 vs 联合使用 | 联合使用优于单独使用 | 两种序列模态互补 | 未报告单独使用时的具体数值 | Supplementary Table S1 |
| PPI 构建方式（Supplementary Table S2） | 交集/并集策略影响性能 | intersection vs union | 未提供具体数值 | 构建方式影响结果 | 未说明哪种更优 | Supplementary Table S2 |
| 融合策略（Supplementary Table S3） | 自适应融合优于简单求和 | adaptive vs sum | 简单求和优于自适应 | 与主实验 claim 矛盾 | 作者未解释原因 | Supplementary Table S3 |
| 案例研究（Fig. 3, 4） | 预测的调控关系有生物学意义 | hHEP 细胞，预测 top-20 靶基因，用 hTFtarget 验证；JUND、FOXA2、ELF1 的靶基因做通路富集 | 预测靶基因富集于谷胱甘肽代谢等肝脏相关通路；JASPAR 找到高置信 motif | 预测结果具有生物学相关性 | 仅 3 个 TF 的案例，非系统性验证 | Results, Case study 节 |
| 膀胱癌空间转录组（Fig. 5） | 模型可迁移到疾病数据 | 膀胱癌空间转录组，用 hTFtarget 作为先验，构建 5 TF + 60 靶基因子网络 | 捕捉到 BRD4-G6PD、ATF3-DDIT4 等已知调控关系 | 模型可泛化到疾病场景 | 未与基线方法对比；未做定量评估 | Results, 膀胱癌分析节 |

## 11 结论正确解读
- **任务范围**：本文解决的是「从 scRNA-seq 表达谱 + 序列 + PPI 推断 TF–靶基因调控边」的有监督链接预测任务，而非因果推断或动态调控建模。
- **Oracle/真值输入**：训练需要 ground-truth 网络（STRING、ChIP-seq、LOF/GOF）作为标签，这些标签本身来自实验或数据库，存在噪声与覆盖偏差。
- **端到端状态**：序列特征提取（DNABERT/ESM）是冻结的预训练模型，不参与端到端微调；可学习的部分为 GAT 编码器、共注意力模块和 MLP 解码器。
- **算力成本**：未报告训练时间、GPU 型号等；预训练模型推理成本较高，但冻结参数降低了训练开销。
- **历史数据依赖**：依赖 BEELINE 基准的 ground-truth 网络，这些网络来自功能互作数据库（STRING）或 ChIP-seq 实验，存在平台特异性和细胞类型特异性偏差。
- **模型依赖**：性能依赖预训练模型（DNABERT/ESM）的质量、PPI 数据库（HuRI）的覆盖度，以及 ground-truth 网络的定义。
- **最难情形**：稀疏网络（如 STRING）中，严格交集操作和矩阵幂运算可能放大误差，产生拓扑伪影（作者在 Discussion 中承认）。
- **有边界的复述**：CaHoT-GRN 在 BEELINE 基准的 7 个数据集、4 种 ground-truth、2 种规模下，平均 AUROC 0.846、AUPR 0.420，匹配或优于 7 个基线；消融实验支持三个模块的贡献；案例研究显示预测结果具有生物学相关性。但未报告方差、显著性检验、计算成本，且融合策略的消融结果（sum 优于 adaptive）与主实验设计存在张力。

## 12 作者自认局限
| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| 融合机制存在信息孤岛风险 | 相似性共注意力虽能过滤噪声，但可能抑制异构但有价值的跨模态特征 | 引入模态感知的动态路由机制，突破单一相似度指标的限制 | Discussion 第 2 段 |
| 拓扑掩码刚性 | 严格交集/并集操作在低置信或稀疏网络中易放大误差，产生拓扑伪影 | 基于图信息熵的自适应软掩码，提升拓扑鲁棒性 | Discussion 第 2 段 |
| 缺乏湿实验闭环验证 | 预测的调控关系仅通过数据库和 motif 匹配间接验证，未在细胞系中实验确认 | 结合 AlphaFold 3 结构预测、R-PNAI-T 体外筛选、活细胞光交联蛋白质组学，构建干湿闭环验证框架 | Discussion 第 3 段 |

## 13 批判性分析
| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|----------------|---------------------|----------|----------|------|
| 主实验未报告方差或显著性检验 | 10 次独立实验的平均值可能掩盖高方差；提升幅度（3-28%）可能不显著 | 无法判断性能提升是否统计可靠 | 要求作者提供标准差、置信区间或配对检验 p 值 | Results, Tables 1-2 仅报告平均值 |
| 消融实验中「sum 优于 adaptive」与主实验设计矛盾 | 作者在 Supplementary Table S3 中报告简单求和优于自适应融合，但主实验仍采用自适应融合 | 说明自适应融合可能不是最优选择，主实验设计存在内部不一致 | 要求作者解释为何主实验不采用消融中更优的 sum 策略 | Supplementary Table S3 vs. Methods 设计 |
| 序列特征提取模块使用冻结的预训练模型 | DNABERT/ESM 的嵌入可能未针对 GRN 任务优化，且未与下游任务联合微调 | 端到端微调可能进一步提升性能，冻结参数可能限制了任务特异性表征 | 对比冻结 vs. 微调预训练模型的性能差异 | Methods, Sequence feature extraction 节 |
| PPI 网络（HuRI）覆盖度有限 | HuRI 主要覆盖人类蛋白互作，对非人类物种或组织特异性互作的覆盖不足 | 限制了模型在非人类或罕见细胞类型上的泛化能力 | 在非人类数据集上测试，或使用组织特异性 PPI 数据库 | Methods, PPI-based module 节 |
| 案例研究仅 3 个 TF，非系统性验证 | 选择 JUND、FOXA2、ELF1 可能存在选择性偏差；未报告失败案例 | 无法评估模型在更广泛 TF 上的预测可靠性 | 在更多 TF 上做系统验证，报告成功/失败率 | Results, Case study 节 |
| 膀胱癌分析未与基线对比 | 仅展示 CaHoT-GRN 的预测网络，未报告定量指标或与现有方法比较 | 无法判断在疾病数据上的相对优势 | 在相同数据上运行基线方法并对比 AUROC/AUPR | Results, 膀胱癌分析节 |
| 未报告计算成本 | 预训练模型（ESM/DNABERT）推理 + GAT 训练的具体时间/内存未给出 | 影响方法在实际场景中的可用性 | 要求补充运行时间、GPU 型号、显存占用 | 全文未提供 |

## 14 学到什么
*（Agent 提炼的知识候选）*

1. **多模态序列语义可编码 TF–DNA 结合潜力**：本文用 DNABERT 编码靶基因启动子序列、ESM 编码 TF 蛋白序列，在隐空间中隐式建模结合亲和力。**可迁移到本课题**：对于 TF–DNA 结合机制研究，可借鉴此思路，用预训练模型提取 TF 的 DNA 结合域（DBD）序列与靶基因的 motif 上下文嵌入，作为结合亲和力预测的输入特征，替代或补充传统的 PSSM/motif 扫描。
2. **PPI 作为高阶拓扑先验可减少假阳性**：本文用 PPI 过滤 GRN 中的二阶邻居，本质上是利用「TF 常以复合物形式协同结合 DNA」的生物学先验。**可迁移到本课题**：在预测 TF–DNA 结合时，可引入「TF–TF 互作 + 共结合」先验，构建高阶上下文特征，例如通过 PPI 网络聚合协同 TF 的序列嵌入，增强对间接结合的判别。
3. **相似性共注意力可融合双图拓扑**：本文提出的相似性共注意力机制，通过视图内/视图间相似性矩阵自适应聚合长程节点关联，突破了 GNN 局部感受野限制。**可迁移到本课题**：在 TF–DNA 结合预测中，可构建「序列相似性图」与「表达共调控图」双视图，用共注意力融合，捕捉远距离但功能相关的调控关系。
4. **消融实验设计需注意内部一致性**：本文 Supplementary Table S3 中 sum 融合优于 adaptive 融合，但主实验仍采用 adaptive，暴露了方法选择与消融证据之间的张力。**可迁移到本课题**：在设计消融实验时，应确保最终模型选择与消融结果一致，或对不一致给出明确解释。
5. **干湿闭环验证框架**：作者在 Discussion 中提出结合 AlphaFold 3 结构预测、体外筛选、活细胞光交联的闭环验证。**可迁移到本课题**：对于 TF–DNA 结合机制研究，可设计「AI 预测 → 结构验证（AF3/分子对接）→ 体外亲和力实验 → 活细胞验证」的闭环流程，提升预测结果的可信度。

## 15 与已有知识连接
- **BEELINE 基准**（Pratapa et al., 2020）：本文使用的数据集与 ground-truth 网络来自 BEELINE，是 GRN 推断领域公认的基准，可与其他方法（如 GENIE3、GRNBoost2、PIDC）直接对比。
- **DNABERT**（Ji et al., 2021）与 **ESM**（Rives et al., 2021）：本文使用的预训练模型，分别用于 DNA 与蛋白序列编码。这两个模型在基因组与蛋白质组学领域已被广泛验证，可迁移到 TF–DNA 结合位点预测任务。
- **图注意力网络（GAT）**（Veličković et al., 2018）：本文 GAT 编码器的基础架构，与 GRN 推断中的图学习方法（如 GCLink、scMGATGRN）一脉相承。
- **元路径（Meta-path）**（Sun et al., 2011）：本文 PPI-HON 构建中使用的概念，源自异质信息网络分析，可用于捕捉多跳生物关系。
- **TF–DNA 结合机制相关方法**：本文的序列语义嵌入思路与 DeepSEA、DeepBind 等基于序列的 TF 结合预测方法互补——前者关注调控网络拓扑，后者关注单一位点结合。可组合使用。
- **AlphaFold 3**（Abramson et al., 2024）：作者在 Discussion 中提及的蛋白-核酸复合物结构预测工具，是 TF–DNA 三维结构验证的候选方法，与本课题的物理模拟方向直接相关。

## 16 研究想法
*（Agent 生成的研究候选）*

1. **候选名称**：TF–DNA 结合亲和力的「序列语义 + 结构先验」多模态预测
   - **来源局限/观察**：CaHoT-GRN 用序列语义隐式编码结合亲和力，但未显式利用 TF 的 DNA 结合域（DBD）三维结构信息；AlphaFold 3 可预测 TF–DNA 复合物结构，但计算成本高，难以全基因组规模应用。
   - **核心假设**：将 ESM 的序列嵌入与 AlphaFold 3 预测的 DBD–DNA 接触图特征结合，可提升 TF–DNA 结合亲和力的预测精度，尤其在序列相似但结构差异大的 TF 家族中。
   - **初步方法**：对一组 TF（如 JUND、FOXA2、ELF1），用 AlphaFold 3 预测其与已知 motif 的复合物结构，提取界面残基接触特征；将 ESM 序列嵌入与接触特征拼接，训练回归模型预测结合亲和力（如来自 HT-SELEX 或 PBMC 数据）。
   - **验证方式**：在独立测试集上对比「仅序列嵌入」vs.「序列+结构特征」的 Pearson 相关系数；在 JASPAR 已知 motif 上做留一 TF 交叉验证。
   - **创新状态**：unverified（需验证结构特征是否带来增量）。

2. **候选名称**：基于 PPI 高阶上下文的 TF 协同结合位点预测
   - **来源局限/观察**：CaHoT-GRN 用 PPI 过滤 GRN 边，但未显式建模「TF 二聚体/复合物协同结合 DNA」的序列模式；已知许多 TF 以异源二聚体形式结合（如 JUND-FOS）。
   - **核心假设**：将 PPI 网络中的 TF–TF 互作关系作为先验，构建「TF 对」的联合序列嵌入（两个 TF 的 ESM 嵌入 + 靶基因 DNA 嵌入），可预测协同结合位点，优于单 TF 预测。
   - **初步方法**：从 PPI 数据库（如 HuRI、STRING）提取 TF–TF 互作对；对每对 TF，用 DNABERT 编码其共有的 ChIP-seq 峰序列，用 ESM 编码两个 TF 的蛋白序列；训练二分类器预测「该 DNA 区域是否被该 TF 对协同结合」。
   - **验证方式**：用 ENCODE 的 ChIP-seq 共结合数据（如 JUND-FOS 共峰）做评估；对比单 TF 模型与 TF 对模型的 AUPRC。
   - **创新状态**：partially checked（TF 协同结合已有生物学证据，但深度学习方法尚未系统利用 PPI 先验）。

3. **候选名称**：基于图熵的自适应软掩码 GRN 推断
   - **来源局限/观察**：作者在 Discussion 中承认严格交集/并集操作在稀疏网络中易产生拓扑伪影，提出未来用图信息熵实现自适应软掩码。
   - **核心假设**：用图信息熵度量局部拓扑的不确定性，对低熵（高置信）区域施加强约束，对高熵（低置信）区域施加软约束，可减少稀疏网络中的误差放大。
   - **初步方法**：在 CaHoT-GRN 的 PPI-HON 模块中，将硬交集替换为基于图熵的软掩码权重；用可微分的熵正则项训练。
   - **验证方式**：在 BEELINE 的 STRING ground-truth 上对比硬掩码与软掩码的 AUPRC；在 TFs+1000 稀疏场景下检验鲁棒性。
   - **创新状态**：unverified（作者提出方向，未实现）。

4. **候选名称**：GRN 推断的干湿闭环验证框架
   - **来源局限/观察**：作者在 Discussion 中提出结合 AlphaFold 3、R-PNAI-T、光交联的闭环验证，但未实施。
   - **核心假设**：将 GRN 推断的预测边按置信度分层，对高置信边用 AlphaFold 3 做结构验证，对中置信边用体外亲和力实验（如 R-PNAI-T）验证，可系统性评估预测的生物学真实性。
   - **初步方法**：在膀胱癌数据上运行 CaHoT-GRN，取 top-k 预测边；对每条边用 AlphaFold 3 预测 TF–DNA 复合物结构，计算界面能量；选取结构支持与不支持的边各若干，用 R-PNAI-T 实验验证。
   - **验证方式**：比较结构验证通过率与实验验证通过率的一致性；评估闭环反馈对模型再训练的增益。
   - **创新状态**：unverified（需湿实验资源，超出纯计算范围）。