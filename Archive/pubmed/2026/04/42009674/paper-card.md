## 01 基本信息

- **标题**：Prediction and functional interpretation of inter-chromosomal genome architecture from DNA sequence with TwinC
- **作者**：Jha, Anupama; Hristov, Borislav; Wang, Xiao; Wang, Sheng; Greenleaf, William J; Kundaje, Anshul; Aiden, Erez Lieberman; Bertero, Alessandro; Noble, William Stafford
- **单位**：未提供（作者信息中未列出具体单位）
- **期刊/平台**：Nature Communications
- **年份**：2026
- **论文类型**：研究论文（Research Article）
- **领域**：三维基因组学、计算生物学、深度学习
- **关键词**：inter-chromosomal architecture, trans contacts, convolutional neural network, Hi-C, DNA sequence prediction
- **DOI/arXiv 号**：10.1038/s41467-026-72031-5
- **代码**：https://github.com/Noble-Lab/twinc
- **数据**：ENCODE 心脏左/右心室 Hi-C 数据（10 个供体/心室）、4D Nucleome in situ Hi-C 数据、DNA SPRITE 数据（GM12878）、micro-C 数据（H1ESC，来自 Zenodo）、GTEx 心脏左心室 RNA-seq 数据、G4-seq 数据（GSE63874、GSM3003539、GSM3003540）
- **阅读日期**：未提供
- **在课题方向中的位置**：本文聚焦于**跨染色体（trans）染色质互作**的序列预测，与 TF–DNA 结合机制课题的关联在于：(1) 其可解释性分析（Integrated Gradients + TF motif）直接识别了参与 trans 互作的 TF 及其 motif，为 TF–DNA 结合如何介导三维基因组互作提供了序列层面的证据；(2) 其 paired-sequence 架构思路可迁移至 TF–DNA 结合预测（如双序列输入建模 TF 与 DNA 的互作）；(3) 其分类框架（基于重复观测的 contact/no-contact 标签）可借鉴用于处理 TF 结合位点预测中的稀疏标签问题。

---

## 02 一句话总结

TwinC 是一个双序列输入的卷积神经网络，将 trans 染色质互作预测建模为二分类任务（contact vs. no-contact），利用多供体 Hi-C 重复实验提取稳健标签，在心脏组织达到 AUROC≈0.80，并通过 Integrated Gradients 识别出 112 个与 trans 互作相关的 TF motif，揭示了染色质可及性、A/B compartment 与 G-四链体在跨染色体互作中的作用。

---

## 03 研究问题

- **具体问题**：能否仅从 DNA 序列预测两个跨染色体位点之间是否发生稳健的物理接触？如果可以，哪些序列特征（如 TF motif、G4 结构）驱动了这些 trans 互作？
- **为什么重要**：三维基因组结构对基因调控至关重要，但现有预测模型几乎全部聚焦于 cis 互作（如 TAD、loop），trans 互作在基因调控（如增强子-启动子跨染色体互作、转录工厂）中同样关键，却缺乏序列层面的预测模型。
- **现有方法不足**：(1) 现有模型（Akita、DeepC）仅预测 cis 互作，无法处理跨染色体位点对；(2) Orca 虽可预测 trans，但需要 256 mbp 的超长输入和巨大的计算资源（20 天训练），且预测分辨率受限；(3) trans 互作数据极度稀疏，直接回归建模困难。
- **精确研究问题**：Can a paired-sequence convolutional neural network accurately predict reproducible inter-chromosomal contacts from DNA sequence alone, and can interpretability analysis reveal sequence determinants (TF motifs, G4s) of trans genome architecture?

---

## 04 背景与发展脉络

> 注：以下脉络基于本文框架整理，部分代表性方法为作者引用，标注「仅本文框架」或「经外部核验」。

| 阶段 | 代表性方法 | 优点 | 局限 | 本文位置 |
|------|-----------|------|------|----------|
| 实验测量 | Hi-C、micro-C、SPRITE、GAM | 全基因组互作图谱 | trans 信号稀疏、噪声大、成本高 | 本文使用多种实验数据作为标签来源 |
| 第一代序列预测模型 | Akita（CNN，1 mbp 输入） | 从序列预测 cis 互作 | 仅限 cis、窗口受限（≤1 mbp） | 本文借鉴其 encoder 架构 |
| 第二代序列预测模型 | DeepC、Orca | 多分辨率、trans 预测能力 | Orca 计算开销巨大、trans 分辨率粗 | 本文提出更轻量的 paired-sequence 方案 |
| 可解释性方法 | Integrated Gradients、TF-MoDISco | 识别序列 motif 贡献 | 需结合 motif 数据库进行功能注释 | 本文用 IG + JASPAR/ChromBPNet motif 识别 trans 相关 TF |
| 表观基因组整合模型 | Epiphany、C.Origami | 结合 ATAC/DNase 等表观数据 | 依赖额外实验数据，无法纯序列预测 | 本文纯序列输入，但用 ATAC-seq 做验证和功能解释 |

**本文主张的位置**：首个专门针对 trans 互作的轻量级、可解释、纯序列输入的 CNN 模型，在保持与 Orca 相当预测性能的同时，训练效率提升 26 倍，并提供 TF 层面的功能解释。

---

## 05 核心痛点

| 痛点 | 表现 | 成因或作者解释 | 文中证据 |
|------|------|----------------|----------|
| trans 互作数据极度稀疏 | trans 接触仅占全部 read pairs 的 20-30%，且分布广泛 | 染色体占据独立核区域（chromosome territories），跨染色体互作天然低频 | Results 引言段、Fig. 1A |
| 单次实验噪声大 | 单供体 Hi-C 中 trans 信号不可靠 | 技术噪声 + 生物学变异 | Methods "Hi-C labels" 节：使用多供体重复提取稳健标签 |
| 现有模型无法处理 trans | Akita/DeepC 仅预测 cis；Orca 计算开销巨大 | 模型设计基于单序列输入，trans 需要双位点联合建模 | Results 引言段、Discussion 段 |
| trans 互作缺乏序列可解释性 | 不知道哪些序列特征驱动 trans 互作 | 缺乏针对 trans 的可解释性分析框架 | 本文用 IG + TF motif 填补此空白 |
| 标签定义困难 | 何为"接触"、何为"无接触"难以界定 | trans 信号稀疏，需要跨重复实验的一致性判断 | Methods "Hi-C labels" 节：多阈值参数优化 |

---

## 06 核心思想

### 1) 表面方法
- 双序列输入 CNN：两个 100 kbp 的 DNA 序列分别通过共享权重的 1D 卷积 encoder，生成嵌入后通过 outer addition 融合，再经 2D 卷积 decoder 输出 contact score（0-1 之间的标量）。
- 分类框架：将 trans 互作预测建模为二分类（contact vs. no-contact），标签来自多供体 Hi-C 重复实验的稳健一致性判断。
- 可解释性：用 Integrated Gradients 计算每个碱基对预测的贡献，结合 TF motif 数据库（JASPAR + ChromBPNet）识别富集的 TF。

### 2) 核心洞察
- **双序列独立编码 + 交互融合**：两个位点的序列特征先独立提取（如各自包含的 TF motif、染色质状态相关序列），再通过 outer addition 建模两者之间的组合效应——这类似于 TF–DNA 结合中"TF 序列特征 × DNA 序列特征"的交互建模。
- **分类优于回归**：trans 互作信号稀疏且动态范围大，直接回归预测 read count 困难；转为二分类（是否稳健互作）后，问题变得可解，且标签来自多重复实验的稳健性判断，天然去噪。
- **可解释性连接序列与功能**：通过 IG 识别出的 TF 不仅是统计关联，还通过表达量验证（GTEx）显示这些 TF 在心脏中高表达，暗示功能相关性。

### 3) 可能的普适教训 [Analysis]
- 对于稀疏互作预测问题（如 TF–DNA 结合、蛋白质-蛋白质互作），将回归问题转化为基于重复实验稳健性的分类问题，可显著降低学习难度。
- 双序列/双实体独立编码后融合的架构，比单序列拼接输入更高效、更可解释，且天然支持任意距离的互作预测。
- 可解释性分析不应止步于"哪些位置重要"，而应进一步与生物学功能数据库（motif、表达、结构）对接，形成"序列→互作→功能"的完整链条。

---

## 07 方法总览

- **输入**：两个 100 kbp 的 one-hot 编码 DNA 序列（来自不同染色体）
- **输出**：contact score（0-1 标量），表示两个位点是否形成稳健 trans 接触
- **模块**：
  1. 共享权重的 1D 卷积 encoder（10 个非线性 + 10 个线性 block，含 batch norm、max pooling、ReLU）
  2. Outer addition 融合层（将两个 embedding 组合为 2D 张量）
  3. 2D 卷积 decoder（19 个非线性 + 19 个线性 block，含 dilated convolution）
  4. 输出层：sigmoid 产生 contact score
- **训练**：二分类交叉熵损失，Adam 优化器，初始学习率 1×10⁻²，batch size 16，最多 10 epochs，early stopping 基于验证集 average precision
- **标签生成**：多供体 Hi-C 重复实验，通过阈值参数 (i, m, j, n) 定义稳健 contact/no-contact
- **数据划分**：5-fold 交叉验证，按染色体划分（19 train / 2 validation / 2 test），避免信息泄漏
- **可解释性**：Integrated Gradients 计算每碱基重要性，FIMO 扫描 TF motif，Mann-Whitney U 检验识别富集 TF
- **验证**：跨实验技术验证（in situ Hi-C → DNA SPRITE）、跨组织验证（心脏 → GM12878）、与 Orca 对比

**文字流程**：
1. 从多供体 Hi-C 数据中提取稳健 trans contact/no-contact 标签
2. 将两个候选位点的 100 kbp 序列 one-hot 编码
3. 双序列分别通过共享 encoder 提取 embedding
4. Outer addition 融合两个 embedding → 2D 张量
5. 2D 卷积 decoder 处理融合张量 → sigmoid 输出 contact score
6. 训练完成后，用 Integrated Gradients 对测试集高置信度预测计算重要性分数
7. 用 FIMO 扫描 motif 出现，统计富集 TF，结合 GTEx 表达数据验证功能相关性

---

## 08 核心模块拆解

| 模块 | 功能 | 为何需要 | 输入输出 | 支撑证据 | 移除后的已知或预期影响 |
|------|------|----------|----------|----------|------------------------|
| 1D 卷积 encoder（共享权重） | 从每个 100 kbp 序列提取局部序列特征（motif-like patterns） | 两个输入序列需要独立编码，共享权重保证特征提取一致性 | 输入：100 kbp × 4 one-hot；输出：embedding 向量 | Methods "TwinC architecture" 节；架构源自 Akita/Orca | [预期] 移除后模型无法提取序列特征，预测退化为随机 |
| Outer addition 融合层 | 将两个 embedding 组合为 2D 交互张量 | 建模两个位点之间的组合效应（非独立贡献） | 输入：两个 embedding；输出：2D 张量 | Methods "TwinC architecture" 节 | [预期] 替换为 concatenation 可能降低交互建模能力；[Analysis] 未提供消融实验 |
| 2D 卷积 decoder | 从融合张量中提取交互模式，输出 contact score | 需要建模两个位点之间的空间交互模式 | 输入：融合 2D 张量；输出：标量 contact score | Methods "TwinC architecture" 节 | [预期] 移除后无法从融合特征映射到接触概率 |
| 分类输出层（sigmoid + BCE loss） | 将特征映射为二分类概率 | trans 互作预测被建模为分类问题 | 输入：decoder 输出；输出：0-1 概率 | Methods "TwinC training" 节 | [预期] 改为回归后训练不稳定（稀疏标签问题） |
| 标签生成流程（多供体阈值） | 从多供体 Hi-C 中提取稳健 contact/no-contact 标签 | trans 信号稀疏，单实验不可靠 | 输入：多供体 Hi-C 矩阵；输出：二值标签 | Methods "Hi-C labels" 节；Fig. 1B | [预期] 移除后标签噪声增大，预测性能下降 |
| Integrated Gradients 可解释性模块 | 计算每碱基对预测的贡献 | 识别驱动 trans 互作的序列特征 | 输入：模型 + 序列对；输出：重要性分数 | Results "TwinC finds transcription factors" 节；Fig. 5 | [预期] 移除后模型仍可预测，但失去功能解释能力 |

---

## 09 关键公式符号

**1. 二分类交叉熵损失**（Methods "TwinC training" 节）：

$$\ell(Y, \hat{Y}) = -\frac{1}{n} \sum_{i=1}^{n} \left[ y_i \cdot \log \hat{y}_i + (1 - y_i) \cdot \log(1 - \hat{y}_i) \right]$$

- $Y = \{y_1, y_2, \ldots, y_n\}$：真实标签向量，$y_i \in \{0, 1\}$
- $\hat{Y} = \{\hat{y}_1, \hat{y}_2, \ldots, \hat{y}_n\}$：模型预测概率，$\hat{y}_i = g(x_i^1, x_i^2)$
- $x_i^1, x_i^2$：两个输入序列的 one-hot 编码矩阵（100,000 × 4）
- $g$：TwinC 神经网络函数

**2. 回归损失**（Methods "TwinC regression training" 节）：

$$\ell(T, \hat{T}) = \frac{1}{n} \sum_{i=1}^{n} (t_i - \hat{t}_i)^2$$

- $T = \{t_1, t_2, \ldots, t_n\}$：目标矩阵，$t_i$ 为 5 × 5 的 log-normalized observed-over-expected trans contact map
- $\hat{T}$：模型预测，$\hat{t}_i = h(r_i^1, r_i^2)$
- $r_i^1, r_i^2$：640 kbp 输入序列

**3. Outer addition 融合**（Methods "TwinC architecture" 节，隐含）：

$$Z = \text{outer\_add}(E_1, E_2)$$

- $E_1, E_2$：两个序列的 embedding 向量
- $Z$：融合后的 2D 张量，$Z_{jk} = E_1[j] + E_2[k]$

---

## 10 实验设计与证据链

### 数据集与设置
- **训练数据**：人类心脏左心室和右心室 Hi-C 数据，各 10 个供体（ENCODE）
- **验证数据**：心脏左心室 in situ Hi-C（4D Nucleome，4 个样本）
- **跨实验验证**：GM12878 细胞系 in situ Hi-C + DNA SPRITE
- **对比数据**：H1ESC 细胞系 micro-C 数据（Orca 训练数据）
- **分辨率**：100 kbp（分类模型）、128 kbp（回归对比模型）
- **指标**：AUROC、Average Precision、Spearman 相关系数
- **基线**：GC 含量、Orca 模型
- **计算资源**：单张 NVIDIA L40 40GB GPU，训练 18 小时

### 实验表格

| 实验 | 检验的 claim | 对比与条件 | 结果 | 支持的结论 | 不支持更强的结论 | 来源 |
|------|-------------|-----------|------|------------|------------------|------|
| 心脏 trans 互作预测 | TwinC 能从序列预测 trans contacts | 测试集染色体（chr9, chr10），对比 GC 基线 | AUROC = 0.7956（左心室）、0.7984（右心室），显著优于 GC 基线 | 序列中包含 trans 互作的可预测信号 | 未证明因果性，仅相关性 | Results 图 1E-F |
| 跨实验技术验证 | TwinC 预测泛化到不同实验技术 | GM12878 训练于 in situ Hi-C，用 DNA SPRITE 验证 | AUROC = 0.9336（TwinC vs SPRITE），接近实验间一致性上限 0.9611 | 预测具有跨技术稳健性 | 未在更多细胞类型/组织验证 | Results 图 2B |
| 与 Orca 对比 | TwinC 与 Orca 性能相当 | H1ESC micro-C 数据，回归任务，128 kbp 分辨率 | 两者 Spearman 相关性相当（具体数值未在摘要中提供） | TwinC 以更简单架构达到可比性能 | 未提供详细统计显著性 | Results 图 3 |
| ATAC-seq 插入实验 | 可及性序列驱动 trans 互作 | 将高分组位点的 ATAC-seq peak 序列插入低分组位点 | 98.16% 的插入导致 contact score 增加，平均增加 0.0855 | 可及性序列是 trans 互作的重要驱动因素 | 未测试插入长度/位置效应 | Results 图 4B |
| 反向替换实验 | 移除可及性序列降低互作 | 从高分组位点移除 ATAC-seq peak 序列 | contact score 显著下降 | 可及性序列对 trans 互作必要 | 未测试部分移除的剂量效应 | Results 图 4C |
| Compartment 分层分析 | A/B compartment 影响可预测性 | 按 AA/AB/BB 分层计算 AUROC | AA: 0.76, AB/BA: 0.65, BB: 0.56 | A compartment 互作更具序列特异性 | 未解释 BB 互作的机制 | Results 图 4E |
| TF motif 富集分析 | 特定 TF 参与 trans 互作 | IG 重要性 + JASPAR/ChromBPNet motif，Mann-Whitney U 检验 | 识别 112 个富集 TF，包括 CTCF、ATF、TBX、RUNX、GATA、KLF/SP、ETS、IRF、STAT 家族 | 这些 TF 的 motif 是 trans 互作的序列决定因素 | 未验证这些 TF 是否物理结合这些位点 | Results 图 5B |
| TF 表达验证 | 富集 TF 在心脏中高表达 | GTEx 心脏左心室 RNA-seq | 富集 TF 表达显著高于非富集 TF（p = 0.0001） | 这些 TF 在心脏中具有功能相关性 | 表达不等于功能，需敲除验证 | Results 图 5C |
| G4 富集分析 | G4 结构参与 trans 互作 | 计算/实验 G4 坐标与 contact 位点重叠 | contact 组 G4 显著富集（p < 10⁻³⁰⁸） | G4 是 trans 互作的潜在结构介导因素 | 未直接证明 G4 结构形成 | Results 图 5D |

---

## 11 结论正确解读

- **任务范围**：TwinC 预测的是**跨染色体位点对之间是否形成稳健互作**（二分类），而非互作强度或频率。预测分辨率限于 100 kbp bin 级别。
- **输入限制**：仅使用 DNA 序列，不包含表观遗传修饰、蛋白质丰度、细胞状态等信息。因此预测的是"序列编码的互作倾向"，而非实际互作状态。
- **性能边界**：AUROC ≈ 0.80 意味着序列信息能解释大部分但非全部 trans 互作变异。BB compartment 互作预测仅 AUROC = 0.56，接近随机，说明异染色质互作可能由非序列因素主导。
- **可解释性边界**：IG 识别的是"模型认为重要的序列特征"，与 TF  motif 的统计富集是相关性证据，不证明这些 TF 直接介导互作。G4 富集同理。
- **泛化边界**：训练于心脏组织，验证于 GM12878 细胞系和 H1ESC，但未覆盖更多组织/物种。跨物种泛化未测试。
- **与 TF–DNA 结合课题的关联**：TwinC 的 paired-sequence 架构和 IG 可解释性流程可直接迁移至 TF–DNA 结合预测——将"TF 序列"和"DNA 序列"作为双输入，预测结合与否，并用 IG 识别关键碱基。其分类框架（基于重复实验稳健性）也适用于 ChIP-seq 等稀疏标签场景。

---

## 12 作者自认局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|------|----------|---------------------|------|
| trans 互作数据稀疏性 | 100 kbp 分辨率下 trans 信号仍稀疏，限制了更细粒度建模 | 更高覆盖度 Hi-C 实验、更细分辨率建模 | Discussion 段 |
| 预测分辨率有限 | 模型在 100 kbp bin 级别预测，无法解析单碱基或 nucleosome 级别互作 | 结合更高分辨率数据（如 Micro-C、SPRITE） | Discussion 段 |
| 可解释性为相关性 | IG 识别的 TF 未经过实验验证其直接参与 trans 互作 | 未来需结合 CRISPR 干扰等实验验证 | Discussion 段 |
| 组织/细胞类型覆盖有限 | 主要训练于心脏组织，泛化性未充分验证 | 扩展至更多组织、细胞类型和物种 | Discussion 段 |
| 未联合建模 cis 与 trans | 模型仅处理 trans 互作，未与 cis 互作联合建模 | 未来可扩展为 cis-trans 联合模型 | Discussion 段 |

---

## 13 批判性分析

| [Analysis] 观察 | 潜在问题或替代解释 | 为何重要 | 如何检验 | 依据 |
|-----------------|---------------------|----------|----------|------|
| AUROC 0.80 的"实际增益"未充分量化 | 未报告相对于简单基线（如距离、GC、基因密度）的绝对增益大小 | 若大部分预测能力来自 trivial 特征，模型价值有限 | 报告与更多基线的对比（如随机森林、线性模型） | Results 图 1E-F 仅对比 GC |
| 标签提取阈值参数 (i, m, j, n) 的选择可能影响结果 | 不同阈值组合可能产生不同标签集，影响模型学习和评估 | 标签定义是分类任务的核心，阈值敏感性未充分讨论 | 对阈值进行敏感性分析，报告 AUROC 随阈值变化 | Methods "Hi-C labels" 节 |
| 与 Orca 的对比可能不公平 | TwinC 分类 vs Orca 回归，任务形式不同；且 Orca 训练于不同数据（micro-C vs Hi-C） | 公平对比需统一任务和数据 | 在相同数据上对比分类版 Orca 与 TwinC | Results 图 3 |
| ATAC-seq 插入实验的因果解释过强 | 插入 ATAC-seq 序列同时改变了序列组成、长度和潜在 motif 组成，不能单独归因于"可及性" | 可及性本身是表观遗传状态，不是序列属性；序列插入改变的是 motif 组成 | 使用 motif 突变对照、随机序列插入对照 | Results 图 4B-C |
| IG 重要性 + motif 富集的统计框架可能产生假阳性 | 大量 motif 同时检验，Mann-Whitney U 的独立性假设可能不成立（motif 间相关） | 假阳性 TF 列表会误导后续实验 | 使用置换检验、控制 motif 间相关性 | Results 图 5B |
| G4 富集分析未控制序列组成偏差 | G4 motif 富含 G，而 GC 含量本身与互作相关；未控制 GC 混淆 | G4 可能是 GC 含量的代理变量 | 在匹配 GC 含量的对照中重新分析 | Results 图 5D |
| 未报告模型在"困难"位点对上的表现 | 如基因沙漠区、着丝粒/端粒附近、重复序列富集区 | 这些区域可能代表不同的生物学机制 | 分层分析不同基因组特征区域的预测表现 | 未提供 |

---

## 14 学到什么

> 以下为 Agent 提炼的知识候选，面向「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI/物理模拟」课题。

1. **双序列独立编码 + 交互融合架构**：TwinC 的 paired-sequence 设计（共享 encoder → outer addition → 2D decoder）可直接迁移至 TF–DNA 结合预测。将 TF 氨基酸序列（或 DNA 结合域序列）与靶 DNA 序列作为双输入，独立编码后融合，可建模"TF 特征 × DNA 特征"的交互效应，比单序列拼接更高效、更可解释。

2. **分类框架处理稀疏标签**：TF–DNA 结合数据（如 ChIP-seq、HT-SELEX）同样存在稀疏性和噪声问题。TwinC 的"基于重复实验稳健性提取二分类标签"策略，可迁移至 TF 结合位点预测——将连续结合强度转为稳健的"结合/不结合"标签，降低学习难度。

3. **可解释性分析流程**：IG → motif 扫描 → 统计富集 → 表达验证的完整流程，可直接用于 TF–DNA 结合模型。识别模型依赖的关键碱基，与已知 TF motif 比对，可发现新的结合模式或协同结合 motif。

4. **Compartment 分层分析**：TwinC 发现 A/B compartment 对可预测性有显著影响（AA > AB > BB），提示在 TF–DNA 结合预测中，也应考虑染色质环境（如 A/B compartment、染色质状态）对结合的影响，或作为分层分析维度。

5. **G4 作为互作介导因素**：G4 富集于 trans contact 位点，提示在 TF–DNA 结合研究中，G4 结构可能影响 TF 的可及性或结合特异性。可探索 TF 是否倾向于结合 G4 邻近区域。

6. **跨实验技术验证策略**：用 in situ Hi-C 训练、DNA SPRITE 验证的策略，可迁移至 TF–DNA 结合——用 ChIP-seq 训练、用独立技术（如 Bind-n-seq、SMF）验证，增强结论稳健性。

7. **训练效率设计**：TwinC 以 6.5M 参数、18 小时训练达到与 Orca 相当性能，说明在序列预测任务中，架构简洁性和数据效率可以兼顾。TF–DNA 结合模型同样应追求轻量化设计，便于大规模 motif 扫描。

---

## 15 与已有知识连接

- **Akita (Fudenberg et al., 2020)**：TwinC 的 encoder 架构直接继承自 Akita，但 Akita 仅预测 cis 互作。TwinC 通过双序列输入和 outer addition 扩展至 trans，这一改动对 TF–DNA 结合建模有直接启发——类似地，TF–DNA 结合需要双序列（TF + DNA）而非单序列输入。
- **Orca (Zhou, 2022)**：目前唯一可预测 trans 的序列模型，TwinC 与之对比验证了 paired-sequence 方案的效率优势。Orca 的 256 mbp 输入设计对 TF–DNA 结合不适用，TwinC 的 100 kbp 双输入更接近 TF 结合位点预测的尺度。
- **DeepC (Schwarzer et al., 2020)**：基于 Akita 架构的 Hi-C 预测模型，同样仅限 cis。TwinC 的分类框架（而非回归）是对这类模型的创新，可迁移至 TF 结合预测。
- **Integrated Gradients (Sundararajan et al., 2017)**：标准可解释性方法，TwinC 将其应用于 trans 互作模型，结合 motif 数据库进行功能注释。这一流程在 TF–DNA 结合模型（如 DeepBind、DeepSEA）中已有应用，TwinC 的贡献在于将其扩展到双序列交互场景。
- **TF motif 数据库 (JASPAR, ChromBPNet/TF-MoDISco)**：TwinC 使用的 motif 来源，与 TF–DNA 结合课题直接共享。其 112 个 trans 相关 TF 列表可作为候选 TF 列表用于结合预测模型的训练或验证。
- **G4 研究 (e.g., Hänsel-Hertsch et al., 2017)**：G4 在转录调控中的作用已有广泛研究，TwinC 将其与 trans 互作关联，为 TF–DNA 结合研究提供了新的序列特征维度。
- **POSSUMM (Hristov et al., 2024)**：A/B compartment 注释工具，TwinC 用于分层分析。TF–DNA 结合研究可借鉴此工具将基因组分为不同 compartment 进行分层建模。

---

## 16 研究想法

> 以下为 Agent 生成的研究候选，面向「蛋白质-DNA 互作（聚焦 TF–DNA 结合机制）× AI/物理模拟」课题。

### 候选 1：TF–DNA 结合的双序列交互预测模型
- **名称**：TwinBind——基于 paired-sequence CNN 的 TF–DNA 结合预测
- **来源局限/观察**：现有 TF–DNA 结合预测模型（DeepBind、DeepSEA）通常将 DNA 序列作为唯一输入，TF 信息仅作为条件或忽略；TwinC 的双序列交互架构证明"两个实体独立编码+融合"可有效建模跨实体互作。
- **核心假设**：将 TF 序列（或 DNA 结合域序列）与靶 DNA 序列作为双输入，通过共享 encoder + 交互融合，可捕捉 TF 序列特征与 DNA 序列特征之间的组合效应，提升结合预测精度。
- **初步方法**：构建 paired-sequence CNN，输入为 TF 蛋白序列（one-hot 编码）和 200-500 bp DNA 序列；encoder 分别提取特征后通过 outer addition 或 cross-attention 融合；在 ChIP-seq、HT-SELEX 等数据集上训练二分类模型。
- **验证方式**：与单序列基线（仅 DNA 输入）对比 AUPRC；在未见过的 TF 上进行 zero-shot 泛化测试；用 IG 识别关键碱基，与已知 motif 比对。
- **创新状态**：unverified

### 候选 2：基于重复实验稳健性的 TF 结合标签提取
- **名称**：RobustBind——利用多重复 ChIP-seq 提取稳健 TF 结合标签
- **来源局限/观察**：TwinC 通过多供体 Hi-C 重复实验提取稳健 contact/no-contact 标签，显著优于单实验标签；TF 结合数据同样存在重复间不一致问题。
- **核心假设**：在多重复 ChIP-seq 中一致出现的 peak 比单次出现的 peak 更可能是真实结合事件，用一致性标签训练可提升模型泛化性。
- **初步方法**：对 ENCODE 多重复 ChIP-seq 数据，设定一致性阈值（如 ≥2/3 重复出现）提取正标签；负标签从背景区域采样；训练 CNN 分类器。
- **验证方式**：与单重复标签训练的模型对比在独立数据集上的表现；用 CRISPR 验证位点作为 gold standard。
- **创新状态**：unverified

### 候选 3：TF–DNA 结合中的 G4 结构特征整合
- **名称**：G4Bind——将 G4 结构预测整合进 TF–DNA 结合模型
- **来源局限/观察**：TwinC 发现 G4 在 trans contact 位点显著富集，且 G4 已知可影响 TF 结合；现有 TF 结合模型未显式建模 G4 结构。
- **核心假设**：在 DNA 序列特征之外加入 G4 结构预测分数（如来自 Quadparser 或 G4-seq），可提升 TF 结合预测精度，特别是对 G4 结合型 TF。
- **初步方法**：在 TwinBind 的 DNA 编码器中加入 G4 分数通道；或在特征融合层拼接 G4 预测分数；在已知 G4 相关 TF（如 SP1、MYC）的结合数据上测试。
- **验证方式**：对比有无 G4 特征的模型性能；分析 G4 特征对预测的贡献权重。
- **创新状态**：unverified

### 候选 4：TF–DNA 结合与三维基因组的联合建模
- **名称**：TF-3D——联合预测 TF 结合与 trans 互作的多任务模型
- **来源局限/观察**：TwinC 识别出 112 个 trans 相关 TF，暗示 TF 结合与三维基因组互作紧密关联；现有模型分别处理这两个任务，未利用其共享信息。
- **核心假设**：TF 结合位点和 trans 互作共享序列特征（如 motif 密度、染色质状态），多任务学习可提升两个任务的预测性能。
- **初步方法**：构建多任务 CNN，共享 encoder 提取序列特征，分别输出 TF 结合概率和 trans contact 概率；在心脏 Hi-C + 心脏 TF ChIP-seq 数据上联合训练。
- **验证方式**：对比单任务模型的性能；分析共享特征是否对应已知的染色质调控元件。
- **创新状态**：unverified

### 候选 5：TF–DNA 结合预测中的 A/B compartment 分层分析
- **名称**：CompBind——基于染色质 compartment 的 TF 结合预测
- **来源局限/观察**：TwinC 发现 A/B compartment 对 trans 互作可预测性有显著影响（AA > AB > BB），提示不同染色质环境下的 TF 结合机制可能不同。
- **核心假设**：在 A 和 B compartment 中，TF 结合的序列决定因素不同，分层建模可提升整体预测精度。
- **初步方法**：用 POSSUMM 注释基因组 compartment，分别在 A/B compartment 中训练 TF 结合预测模型；比较两模型的序列特征重要性差异。
- **验证方式**：对比分层模型与全局模型的 AUPRC；分析两模型识别的 motif 差异。
- **创新状态**：unverified